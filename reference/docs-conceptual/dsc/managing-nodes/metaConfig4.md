---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 在 PowerShell 4.0 中設定 LCM
ms.openlocfilehash: 4a9dedf67f9fb18fdd7f5adf70dbf1402fb3f918
ms.sourcegitcommit: 4eda0bc902658d4a188159bd7310e64399f6e178
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83271826"
---
# <a name="configuring-the-lcm-in-powershell-40"></a>在 PowerShell 4.0 中設定 LCM

>適用於：Windows PowerShell 4.0

**如需 Windows PowerShell 5.0 及更新版本的相關資訊，請參閱[設定本機設定管理員](metaConfig.md)。**

本機設定管理員是 Windows PowerShell 預期狀態設定 (DSC) 引擎，
會在所有目標節點上執行，負責呼叫包含在 DSC 設定指令碼中的設定資源。
本主題列出本機設定管理員屬性，並說明如何修改目標節點上的本機設定管理員設定。

## <a name="local-configuration-manager-properties"></a>本機設定管理員屬性

以下列出您可以設定或擷取的本機設定管理員屬性。

- **AllowModuleOverwrite**：控制是否允許以從設定服務下載的新設定來覆寫目標節點上的舊設定。 可能的值為 True 和 False。
- **CertificateID**：憑證指紋，用來保護在設定中傳遞的憑證。 如需詳細資訊，請參閱 [Want to secure credentials in Windows PowerShell Desired State Configuration (需要保護 Windows PowerShell 預期狀態設定的憑證嗎？)](https://devblogs.microsoft.com/powershell/want-to-secure-credentials-in-windows-powershell-desired-state-configuration/)。
- **ConfigurationID**：表示用來從提取服務取得特定設定檔的 GUID。 此 GUID 可確保存取正確的設定檔。
- **ConfigurationMode**：指定本機設定管理員實際上如何將設定套用至目標節點。 它可以採用下列值：
  - **ApplyOnly**：若設定此選項，DSC 會套用設定，並且不會執行任何進一步的動作，除非它透過下列兩種方式偵測到新的設定：您直接將新設定傳送至目標節點，或是您連線至提取服務且 DSC 於檢查提取服務時發現新設定。 如果目標節點的設定偏離，就不採取任何動作。
  - **ApplyAndMonitor**：若設定此選項 (此為預設值)，DSC 會套用任何新設定，無論新設定是由您直接傳送至目標節點，或是在提取服務上發現。 之後，如果目標節點的設定偏離設定檔，DSC 就會報告記錄檔中的差異。 如需 DSC 記錄的資訊，請參閱 [Using Event Logs to Diagnose Errors in Desired State Configuration (在預期狀態設定中使用事件記錄檔診斷錯誤)](https://devblogs.microsoft.com/powershell/using-event-logs-to-diagnose-errors-in-desired-state-configuration/)。
  - **ApplyAndAutoCorrect**：若設定此選項，DSC 會套用任何新設定，無論新設定是由您直接傳送至目標節點，或是在提取服務上發現。 之後，如果目標節點的設定偏離設定檔，DSC 就會報告記錄檔中的差異，然後嘗試調整目標節點設定，以符合設定檔。
- **ConfigurationModeFrequencyMins**：代表 DSC 背景應用程式嘗試在目標節點上實作目前設定的頻率 (以分鐘為單位)。 預設值為 15。 這個值可以搭配 RefreshMode 設定。 當 RefreshMode 設定為 PULL 時，目標節點會以由 RefreshFrequencyMins 所設定的間隔連絡設定服務，並下載目前的設定。 不論 RefreshMode 值為何，在 ConfigurationModeFrequencyMins 所設定的間隔中，一致性引擎會套用已下載至目標節點的最新設定。 RefreshFrequencyMins 應為 ConfigurationModeFrequencyMins 的整數倍數。
- **Credential**：表示存取遠端資源所需的認證 (如同 Get-Credential)，例如連絡設定服務。
- **DownloadManagerCustomData**：代表陣列，其中包含下載管理員特定的自訂資料。
- **DownloadManagerName**：指出設定和模組下載管理員的名稱。
- **RebootNodeIfNeeded**：將此設為 `$true`，以允許資源使用 `$global:DSCMachineStatus` 旗標來重新啟動節點。 否則，您將必須手動重新啟動任何設定所需的節點。 預設值是 `$false`。 若要在重新啟動條件是由 DSC 以外的項目 (例如 Windows Installer) 所制定的情況下使用此設定，請將此設定與 [xPendingReboot](https://github.com/powershell/xpendingreboot) \(英文\) 模組結合。
- **RefreshFrequencyMins**：於您設定提取服務時使用。 代表的本機設定管理員連絡提取服務來下載目前設定的頻率 (以分鐘為單位)。 這個值可以搭配 ConfigurationModeFrequencyMins 設定。 當 RefreshMode 設定為 PULL 時，目標節點會以由 RefreshFrequencyMins 所設定的間隔連絡提取服務，並下載目前的設定。 在 ConfigurationModeFrequencyMins 所設定的間隔中，一致性引擎接著會套用已下載至目標節點的最新設定。 如果 RefreshFrequencyMins 未設定為 ConfigurationModeFrequencyMins 的整數倍數，則系統會無條件進位。 預設值是 30。
- **RefreshMode**：可能的值為 **Push** (預設值) 和 **Pull**。 在 [推送] 設定中，您必須使用任何用戶端電腦，在每個目標節點上放置設定檔。 在 [提取] 模式中，您必須設定提取服務，本機設定管理員才能連絡及存取設定檔。

> [!NOTE]
> LCM 會根據以下項目，啟動 **ConfigurationModeFrequencyMins**：
>
> - 新的中繼設定會使用 `Set-DscLocalConfigurationManager` 來套用
> - 電腦重新啟動
>
> 針對任何計時器處理序發生當機的狀況，會在 30 秒內偵測該狀況，並重新啟動循環。
> 若此作業的期間超過所設定循環頻率，則下一個計時器便不會啟動，並可能使同時作業延遲啟動循環。
>
> 例如，中繼設定已設定為 15 分鐘的提取頻率，而提取動作則在 T1 發生。  節點沒有在 16 分鐘內完成工作。  這樣便會忽略第一個 15 分鐘循環，而下一個提取則會在 T1+15+15 時發生。

### <a name="example-of-updating-local-configuration-manager-settings"></a>更新本機設定管理員設定的範例

您可以更新目標節點的本機設定管理員設定，方法是在設定指令碼中節點區塊內加入 **LocalConfigurationManager** 區塊，如下列範例所示。

```powershell
Configuration ExampleConfig
{
    Node "Server001"
    {
        LocalConfigurationManager
        {
            ConfigurationID = "646e48cb-3082-4a12-9fd9-f71b9a562d4e"
            ConfigurationModeFrequencyMins = 45
            ConfigurationMode = "ApplyAndAutocorrect"
            RefreshMode = "Pull"
            RefreshFrequencyMins = 90
            DownloadManagerName = "WebDownloadManager"
            DownloadManagerCustomData = (@{ServerUrl="https://$PullService/psdscpullserver.svc"})
            CertificateID = "71AA68562316FE3F73536F1096B85D66289ED60E"
            Credential = $cred
            RebootNodeIfNeeded = $true
            AllowModuleOverwrite = $false
        }
# One or more resource blocks can be added here
    }
}

# The following line invokes the configuration and creates a file called Server001.meta.mof at the specified path
ExampleConfig -OutputPath "c:\users\public\dsc"
```

執行上述範例中的指令碼會產生 MOF 檔案，該檔案指定並儲存所需的設定。
若要套用設定，您可以使用 **Set-DscLocalConfigurationManager** Cmdlet，如下列範例所示。

```powershell
Set-DscLocalConfigurationManager -Path "c:\users\public\dsc"
```

> [!NOTE]
> 針對 **Path** 參數，當您叫用前一個範例中的設定時，您指定的路徑必須與您為 **OutputPath** 參數所指定的路徑相同。

若要查看目前本機設定管理員設定，您可以使用 **Get-DscLocalConfigurationManager** Cmdlet。
如果您叫用的這個 Cmdlet 不含任何參數，依預設會取得您用來執行此 Cmdlet 之節點的本機設定管理員設定。
若要指定另一個節點，請使用這項 Cmdlet 的 **CimSession** 參數。
