---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 設定本機設定管理員
description: 本機設定管理員 (LCM) 是 DSC 的引擎，其負責剖析及套用傳送至節點的設定。
ms.openlocfilehash: 73711536d419cd0305d541e3be23195ae6b91782
ms.sourcegitcommit: 61765d08321623743dc5db5367160f6982fe7857
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2020
ms.locfileid: "97352683"
---
# <a name="configuring-the-local-configuration-manager"></a>設定本機設定管理員

> 適用於：Windows PowerShell 5.0

本機設定管理員 (LCM) 是 Desired State Configuration (DSC) 的引擎。 LCM 在每個目標節點上執行，而且會負責剖析和制定傳送至節點的設定。 它也會負責多個 DSC 的其他層面，包括下列層面。

- 決定重新整理模式 (發送或提取)。
- 指定節點提取的頻率，並制定設定。
- 將節點與提取服務產生關聯。
- 指定部分設定。

您可以使用一種特殊的設定來設定 LCM，以指定這些行為。 下列章節說明如何設定 LCM。

Windows PowerShell 5.0 推出了用於管理本機設定管理員的新設定。 如需在 Windows PowerShell 4.0 中設定 LCM 的資訊，請參閱[在舊版 Windows PowerShell 中設定本機設定管理員](metaconfig4.md)。

## <a name="writing-and-enacting-an-lcm-configuration"></a>撰寫和制定 LCM 設定

若要設定 LCM，您可以建立並執行會套用 LCM 設定的特殊設定。
若要指定 LCM 設定，您可以使用 DscLocalConfigurationManager 屬性。 下圖顯示簡單的設定，可將 LCM 設定為推入模式。

```powershell
[DSCLocalConfigurationManager()]
configuration LCMConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
        }
    }
}
```

套用設定至 LCM 的程序和套用 DSC 設定類似。 您將會建立 LCM 設定，將它編譯成 MOF 檔案，然後將它套用至節點。 和 DSC 設定不同的是，您不會藉由呼叫 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) \(英文\) Cmdlet 來制定 LCM 設定。 相反地，您會呼叫 [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) \(英文\)，將 LCM 設定 MOF 的路徑作為參數提供。 制定 LCM 設定之後，您可以藉由呼叫 [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) \(英文\) Cmdlet 來查看 LCM 屬性。

LCM 設定可以包含一組僅限於有限資源的區塊。 在上述範例中，唯一呼叫的資源是 **Settings**。 其他可用的資源包括：

- **ConfigurationRepositoryWeb**：指定設定的 HTTP 提取服務。
- **ConfigurationRepositoryShare**：指定設定的 SMB 共用。
- **ResourceRepositoryWeb**：指定模組的 HTTP 提取服務。
- **ResourceRepositoryShare**：指定模組的 SMB 共用。
- **ReportServerWeb**：指定傳送報表的目標 HTTP 提取服務。
- **PartialConfiguration**：提供資料以啟用部分設定。

## <a name="basic-settings"></a>基本設定

除了指定提取服務端點/路徑及部分設定之外，所有的 LCM 屬性都會在 **Settings** 區塊中設定。 下列屬性可用於 **Settings** 區塊。

|  屬性  |  類型  |  描述   |
|----------- |------- |--------------- |
| ActionAfterReboot| 字串| 指定套用設定期間在重新開機後的動作。 可能的值為 __"ContinueConfiguration"__ 和 __"StopConfiguration"__ 。 <ul><li> __ContinueConfiguration__：機器重新開機後繼續套用目前的設定。 這是預設值。</li><li>__StopConfiguration__：機器重新開機後停止目前的設定。</li></ul>|
| AllowModuleOverwrite| bool| 若允許以自提取服務下載的新設定覆寫目標節點上的舊設定，即為 __$TRUE__。 否則為 $FALSE。|
| CertificateID| 字串| 憑證指紋，用來保護在設定中傳遞的憑證。 如需詳細資訊，請參閱 [Want to secure credentials in Windows PowerShell Desired State Configuration (需要保護 Windows PowerShell 預期狀態設定的憑證嗎？)](https://devblogs.microsoft.com/powershell/want-to-secure-credentials-in-windows-powershell-desired-state-configuration/)。 <br> __注意：__ 若使用 Azure 自動化 DSC 提取服務，系統會自動管理此設定。|
| ConfigurationDownloadManagers| CimInstance[]| 已過時。 使用 __ConfigurationRepositoryWeb__ 和 __ConfigurationRepositoryShare__ 區塊來定義設定提取服務端點。|
| ConfigurationID| 字串| 用於與較舊提取服務版本之間的回溯相容性。 識別要從提取服務取得之設定檔的 GUID。 如果設定 MOF 的名稱為 ConfigurationID.mof，節點將會在提取服務上提取設定。<br> __注意：__ 如果您設定這個屬性，將無法使用 __RegistrationKey__ 向提取服務註冊節點。 如需詳細資訊，請參閱[以設定名稱設定提取用戶端](../pull-server/pullClientConfigNames.md)。|
| ConfigurationMode| 字串 | 指定 LCM 實際上如何將設定套用至目標節點。 可能的值為 __"ApplyOnly"__ 、 __"ApplyAndMonitor"__ 和 __"ApplyAndAutoCorrect"__ 。 <ul><li>__ApplyOnly__：除非將新設定推送至目標節點，或是從服務提取新設定時，否則，DSC 會套用設定且不執行任何進一步的動作。 初始套用新的設定之後，DSC 不會檢查先前設定的狀態是否漂移。 請注意，在 __ApplyOnly__ 生效之前，DSC 不斷嘗試套用此組態，直到成功為止 。 </li><li> __ApplyAndMonitor__：這是預設值。 LCM 會套用任何新的設定。 初始套用新設定之後，如果目標節點從所需狀態漂移，DSC 會在記錄中報告差異。 請注意，在 __ApplyAndMonitor__ 生效之前，DSC 不斷嘗試套用此組態，直到成功為止 。</li><li>__ApplyAndAutoCorrect__：DSC 會套用任何新設定。 第一次套用新設定之後，如果目標節點偏離預期狀態，則 DSC 會報告記錄檔中的差異，然後重新套用目前設定。</li></ul>|
| ConfigurationModeFrequencyMins| UInt32| 檢查並套用目前設定的頻率 (以分鐘為單位)。 如果 ConfigurationMode 屬性設定為 ApplyOnly，就會忽略這個屬性。 預設值為 15。|
| DebugMode| 字串| 可能的值為 __None__、__ForceModuleImport__ 和 __All__。 <ul><li>設為 __None__ 會使用快取資源。 這是預設，而且應該用於實際執行的案例。</li><li>設為 __ForceModuleImport__，會導致 LCM 重新載入任何 DSC 資源模組，即使先前已載入這些模組並已快取。 這會影響 DSC 作業的效能，因為每個模組會在使用時重新載入。 通常會在為資源偵錯時使用此值</li><li>在這一版本中，__All__ 與 __ForceModuleImport__ 相同</li></ul> |
| RebootNodeIfNeeded| bool| 將此設為 `$true`，以允許資源使用 `$global:DSCMachineStatus` 旗標來重新啟動節點。 否則，您將必須手動重新啟動任何設定所需的節點。 預設值是 `$false`。 若要在重新啟動條件是由 DSC 以外項目 (例如 Windows Installer) 所制定的情況下使用此設定，請將此設定與 [ComputerManagementDsc](https://github.com/PowerShell/ComputerManagementDsc) 中的 __PendingReboot__ 模組結合。|
| RefreshMode| 字串| 指定 LCM 取得設定的方式。 可能的值為 __"Disabled"__ 、 __"Push"__ 和 __"Pull"__ 。 <ul><li>__Disabled__：為此節點停用 DSC 設定。</li><li> __Push__：藉由呼叫 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) Cmdlet 來初始設定。 設定會立即套用至節點。 這是預設值。</li><li>__Pull__：將節點設定為定期檢查來自提取服務或 SMB 路徑的設定。 如果這個屬性設為 __Pull__，您必須在 __ConfigurationRepositoryWeb__ 或 __ConfigurationRepositoryShare__ 區塊中指定 HTTP (服務) 或 SMB (共用) 路徑。</li></ul>|
| RefreshFrequencyMins| Uint32| LCM 檢查提取服務以取得更新設定並針對漂移檢查本機設定的時間間隔 (以分鐘為單位)。 無論是否已下載更新，都會套用設定。 如果 LCM 未在提取模式下設定，就會忽略此值。 預設值是 30。|
| ReportManagers| CimInstance[]| 已過時。 使用 __ReportServerWeb__ 區塊來定義傳送報表資料至提取服務的端點。|
| ResourceModuleManagers| CimInstance[]| 已過時。 使用 __ResourceRepositoryWeb__ 和 __ResourceRepositoryShare__ 區塊來個別定義提取服務 HTTP 端點或 SMB 路徑。|
| PartialConfigurations| CimInstance| 未實作。 請勿使用。|
| StatusRetentionTimeInDays | UInt32| LCM 會保留目前設定狀態的天數。|

> [!NOTE]
> LCM 會根據以下項目，啟動 **ConfigurationModeFrequencyMins**：
>
> - 已使用 `Set-DscLocalConfigurationManager` 套用變更為 **ConfigurationModeFrequencyMins** 的新中繼設定
> - 電腦重新啟動
>
> 針對任何計時器處理序發生當機的狀況，會在 30 秒內偵測該狀況，並重新啟動循環。 若此作業的期間超過所設定循環頻率，則下一個計時器便不會啟動，並可能使同時作業延遲啟動循環。 例如，中繼設定已設定為 15 分鐘的提取頻率，而提取動作則在 T1 發生。 節點沒有在 16 分鐘內完成工作。 這樣便會忽略第一個 15 分鐘循環，而下一個提取則會在 T1+15+15 時發生。
>
> 提取案例中的原始意圖是 `RefreshFrequencyMins` 已設定為比 `ConfigurationModeFrequencyMins` 更長的時間。 本機設定主要會由 `ConfigurationModeFrequencyMins` 管理以避免設定漂移，而且會使用 `RefreshFrequencyMins` 來追蹤系統管理員所做的實際設定變更。

## <a name="pull-service"></a>提取服務

LCM 設定支援定義下列提取服務端點類型：

- **設定伺服器**：適用於 DSC 設定的存放庫。 使用 **ConfigurationRepositoryWeb** (適用於 Web 伺服器) 和 **ConfigurationRepositoryShare** (適用於 SMB 伺服器) 區塊來定義設定伺服器。
- **資源伺服器**：封裝成 PowerShell 模組的 DSC 資源存放庫。 使用 **ResourceRepositoryWeb** (適用於 Web 伺服器) 和 **ResourceRepositoryShare** (適用於 SMB 伺服器) 區塊來定義資源伺服器。
- **報表伺服器**：DSC 傳送報表資料的目標服務。 使用 **ReportServerWeb** 區塊來定義報表伺服器。 報表伺服器必須是 Web 服務。

如需提取服務的詳細資訊，請參閱 [Desired State Configuration 提取服務](../pull-server/pullServer.md)。

## <a name="configuration-server-blocks"></a>設定伺服器區塊

若要定義 Web 設定伺服器，請建立 **ConfigurationRepositoryWeb** 區塊。 **ConfigurationRepositoryWeb** 定義下列屬性。

|屬性|類型|描述|
|---|---|---|
|AllowUnsecureConnection|bool|設為 **$TRUE** 即允許從節點到伺服器的未經驗證連線。 設為 **$FALSE** 表示需要驗證。|
|CertificateID|字串|用來向伺服器驗證的憑證指紋。|
|ConfigurationNames|String[]|要由目標節點提取之設定名稱的陣列。 僅有在使用 **RegistrationKey** 向提取服務註冊節點時，才會使用這些設定。 如需詳細資訊，請參閱[以設定名稱設定提取用戶端](../pull-server/pullClientConfigNames.md)。|
|RegistrationKey|字串|向提取服務註冊節點的 GUID。 如需詳細資訊，請參閱[以設定名稱設定提取用戶端](../pull-server/pullClientConfigNames.md)。|
|ServerURL|字串|設定服務的 URL。|
|ProxyURL*|字串|與設定服務通訊時要使用的 HTTP Proxy URL。|
|ProxyCredential*|pscredential|要用於 HTTP Proxy 的認證。|

> [!NOTE]
> Windows 1809 版與更新版本中支援。

如需能簡化針對內部部署節點設定 ConfigurationRepositoryWeb 值的範例指令碼，請參閱[產生 DSC 中繼設定](/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

若要定義 SMB 設定伺服器，請建立 **ConfigurationRepositoryShare** 區塊。 **ConfigurationRepositoryShare** 定義下列屬性。

|  屬性  |      類型       |                      描述                      |
| ---------- | --------------- | ----------------------------------------------------- |
| 認證 | MSFT_Credential | 用來向 SMB 驗證的認證。 |
| SourcePath | 字串          | SMB 共用的路徑。                            |

## <a name="resource-server-blocks"></a>資源伺服器區塊

若要定義 Web 資源伺服器，請建立 **ResourceRepositoryWeb** 區塊。
**ResourceRepositoryWeb** 定義下列屬性。

|        屬性         |     類型     |                                                              描述                                                               |
| ----------------------- | ------------ | -------------------------------------------------------------------------------------------------------------------------------------- |
| AllowUnsecureConnection | bool         | 設為 **$TRUE** 即允許從節點到伺服器的未經驗證連線。 設為 **$FALSE** 表示需要驗證。 |
| CertificateID           | 字串       | 用來向伺服器驗證的憑證指紋。                                                                    |
| RegistrationKey         | 字串       | 向提取服務識別節點的 GUID。                                                                                   |
| ServerURL               | 字串       | 設定伺服器的 URL。                                                                                                   |
| ProxyURL*               | 字串       | 與設定服務通訊時要使用的 HTTP Proxy URL。                                                    |
| ProxyCredential*        | pscredential | 要用於 HTTP Proxy 的認證。                                                                                                  |

> [!NOTE]
> Windows 1809 版與更新版本中支援。

如需能簡化針對內部部署節點設定 ResourceRepositoryWeb 值的範例指令碼，請參閱[產生 DSC 中繼設定](/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

若要定義 SMB 資源伺服器，請建立 **ResourceRepositoryShare** 區塊。
**ResourceRepositoryShare** 定義下列屬性。

|屬性|類型|描述|
|---|---|---|
|認證|MSFT_Credential|用來向 SMB 驗證的認證。 如需傳遞認證的範例，請參閱[設定 SMB DSC 提取伺服器](../pull-server/pullServerSMB.md)|
|SourcePath|字串|SMB 共用的路徑。|

## <a name="report-server-blocks"></a>報表伺服器區塊

若要定義報表伺服器，請建立 **ReportServerWeb** 區塊。 報表伺服器角色並不相容於以 SMB 為基礎的提取服務。 **ReportServerWeb** 定義下列屬性。

|        屬性         |     類型     |                                                              描述                                                               |
| ----------------------- | ------------ | -------------------------------------------------------------------------------------------------------------------------------------- |
| AllowUnsecureConnection | bool         | 設為 **$TRUE** 即允許從節點到伺服器的未經驗證連線。 設為 **$FALSE** 表示需要驗證。 |
| CertificateID           | 字串       | 用來向伺服器驗證的憑證指紋。                                                                    |
| RegistrationKey         | 字串       | 向提取服務識別節點的 GUID。                                                                                   |
| ServerURL               | 字串       | 設定伺服器的 URL。                                                                                                   |
| ProxyURL*               | 字串       | 與設定服務通訊時要使用的 HTTP Proxy URL。                                                    |
| ProxyCredential*        | pscredential | 要用於 HTTP Proxy 的認證。                                                                                                  |

> [!NOTE]
> Windows 1809 版與更新版本中支援。

如需能簡化針對內部部署節點設定 ReportServerWeb 值的範例指令碼，請參閱[產生 DSC 中繼設定](/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

## <a name="partial-configurations"></a>部分設定

若要定義部分設定，請建立 **PartialConfiguration** 區塊。 如需部分設定的詳細資訊，請參閱 [DSC 部分設定](../pull-server/partialConfigs.md)。
**PartialConfiguration** 定義下列屬性。

|屬性|類型|描述|
|---|---|---|
|ConfigurationSource|string[]|先前在 **ConfigurationRepositoryWeb** 和 **ConfigurationRepositoryShare** 區塊中定義的設定伺服器名稱陣列，部分設定會從中提取。|
|DependsOn|string{}|必須在套用部分設定之前先完成的其他設定名稱清單。|
|描述|字串|用來描述部分設定的文字。|
|ExclusiveResources|string[]|這個部分設定專用的資源陣列。|
|RefreshMode|字串|指定 LCM 如何取得這個部分設定。 可能的值為 __"Disabled"__ 、 __"Push"__ 和 __"Pull"__ 。 <ul><li>__Disabled__：停用此部分設定。</li><li> __Push__：藉由呼叫 [Publish-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) Cmdlet 來將部分設定推送到節點。 節點的所有部分設定從服務推送或提取之後，就可以藉由呼叫 `Start-DscConfiguration –UseExisting` 來啟動設定。 這是預設值。</li><li>__Pull__：將節點設定為定期檢查來自提取服務的部分設定。 如果這個屬性設為 __Pull__，您必須在 __ConfigurationSource__ 屬性中指定提取服務。 如需 Azure 自動化提取服務的詳細資訊，請參閱 [Azure 自動化 DSC 概觀](/azure/automation/automation-dsc-overview)。</li></ul>|
|ResourceModuleSource|string[]|要從中下載此部分設定所需資源的資源伺服器名稱陣列。 這些名稱必須參考先前在 **ResourceRepositoryWeb** 和 **ResourceRepositoryShare** 區塊中定義的服務端點。|

> [!NOTE]
> 雖然 Azure 自動化 DSC 支援部分組態，但每個節點的每個自動化帳戶中只能提取一個組態。

## <a name="see-also"></a>另請參閱

### <a name="concepts"></a>概念

[Desired State Configuration 概觀](../overview/overview.md)

[開始使用 Azure 自動化 DSC](/azure/automation/automation-dsc-getting-started)

### <a name="other-resources"></a>其他資源

[Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)

[以設定名稱設定提取用戶端](../pull-server/pullClientConfigNames.md)
