---
title:   設定本機設定管理員
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# 設定本機設定管理員

> 適用於：Windows PowerShell 5.0

本機設定管理員 (LCM) 是 Windows PowerShell 預期狀態設定 (DSC) 的引擎。 LCM 在每個目標節點上執行，而且會負責剖析和制定傳送至節點的設定。 它也會負責多個 DSC 的其他層面，包括下列層面。

* 決定重新整理模式 (發送或提取)。
* 指定節點提取的頻率，並制定設定。
* 將節點與提取伺服器產生關聯。
* 指定部分設定。

您可以使用一種特殊的設定來設定 LCM，以指定這些行為。 下列章節說明如何設定 LCM。

> **注意**：本主題適用於 Windows PowerShell 5.0 中導入的 LCM。 如需在 Windows PowerShell 4.0 中設定 LCM 的資訊，請參閱 [Windows PowerShell 4.0 預期狀態設定本機設定管理員](metaconfig4.md)。

## 撰寫和制定 LCM 設定

若要設定 LCM，您可以建立並執行一種特殊的設定。 若要指定 LCM 設定，您可以使用 DscLocalConfigurationManager 屬性。 下圖顯示簡單的設定，可將 LCM 設定為推入模式。

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

您可以呼叫並執行設定，以建立 MOF 設定，就如同一般設定 (如需建立 MOF 設定的資訊，請參閱[編譯設定](configurations.md#compiling-the-configuration))。 不同於一般設定，您不必藉由呼叫 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) Cmdlet 來制定 LCM 設定。 相反地，您呼叫 [Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx) Cmdlet，將 MOF 設定的路徑作為參數提供。 制定設定之後，您可以藉由呼叫 [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) Cmdlet 來查看 LCM 屬性。

LCM 設定可以包含一組僅限於有限資源的區塊。 在上述範例中，唯一呼叫的資源是 **Settings**。 其他可用的資源包括：

* **ConfigurationRepositoryWeb**：指定設定的 HTTP 提取伺服器。 
* **ConfigurationRepositoryShare**：指定設定的 SMB 提取伺服器。
* **ResourceRepositoryWeb**：指定模組的 HTTP 提取伺服器。
* **ResourceRepositoryShare**：指定模組的 SMB 提取伺服器。
* **ReportServerWeb**：指定傳送報表的目標 HTTP 提取伺服器。
* **PartialConfiguration**：指定部分設定。

## 基本設定

除了指定提取伺服器與部分設定之外，所有的 LCM 屬性都在 **Settings** 區塊中設定。 下列屬性可用於 **Settings** 區塊。

|  屬性  |  類型  |  描述   | 
|----------- |------- |--------------- | 
| ConfigurationModeFrequencyMins| UInt32| 檢查並套用目前設定的頻率 (以分鐘為單位)。 如果 ConfigurationMode 屬性設定為 ApplyOnly，就會忽略這個屬性。 預設值為 15。 <br> __注意__：這個屬性的值必須是 __RefreshFrequencyMins__ 屬性值的倍數，或者 __RefreshFrequencyMins__ 屬性值必須是這個屬性值的倍數。| 
| RebootNodeIfNeeded| bool| 在套用需要重新開機的設定之後，請將此設為 __$true__ 以自動重新啟動節點。 否則，您將必須手動重新啟動任何設定所需的節點。 預設值為 __$false__。| 
| ConfigurationMode| 字串 | 指定 LCM 實際上如何將設定套用至目標節點。 可能的值為 __"ApplyOnly"__、__"ApplyandMonitior"(預設)__ 和 __"ApplyandAutoCorrect"__。 <ul><li>__ApplyOnly__：DSC 會套用此設定，並且不執行任何進一步的動作，除非新的設定已推送至目標節點，或從伺服器提取新的設定。 第一次套用新設定之後，DSC 不會檢查與先前設定狀態的偏離。</li><li> __ApplyAndMonitor__：這是預設值。 LCM 適用於任何新的設定。 第一次套用新設定之後，如果目標節點偏離預期狀態，則 DSC 會回報記錄中的差異。</li><li>__ApplyAndAutoCorrect__：DSC 會套用任何新的設定。 第一次套用新設定之後，如果目標節點偏離預期狀態，則 DSC 會報告記錄檔中的差異，然後重新套用目前設定。</li></ul>| 
| ActionAfterReboot| 字串| 指定套用設定期間在重新開機後的動作。 可能的值為 __"ContinueConfiguration(default)"__ 和 __"StopConfiguration"__。 <ul><li> __ContinueConfiguration__︰機器重新開機後繼續套用目前的設定。</li><li>__StopConfiguration__：機器重新開機後停止目前的設定。</li></ul>| 
| RefreshMode| 字串| 指定 LCM 取得設定的方式。 可能的值為 __"Disabled"__、__"Push(default)"__ 和 __"Pull"__。 <ul><li>__Disabled__：會為此節點停用 DSC 設定。</li><li> __Push__：藉由呼叫 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) Cmdlet 啟動設定。 設定會立即套用至節點。 這是預設值。</li><li>__Pull__：節點設定為定期檢查提取伺服器的設定。 如果這個屬性設為 __Pull__，您就必須在 __ConfigurationRepositoryWeb__ 或 __ConfigurationRepositoryShare__ 區塊指定提取伺服器。 如需提取伺服器的詳細資訊，請參閱[設定 DSC 提取伺服器](pullServer.md)。</li></ul>| 
| CertificateID| 字串| GUID 會指定憑證，用來保護存取設定的憑證。 如需詳細資訊，請參閱 [Want to secure credentials in Windows PowerShell Desired State Configuration (需要保護 Windows PowerShell 預期狀態設定的憑證嗎？)](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx)。| 
| ConfigurationID| 字串| GUID，識別要在提取模式中從提取伺服器取得的設定檔。 如果設定 MOF 的名稱為 ConfigurationID.mof，此節點將在提取伺服器提取設定。<br> __注意__：如果您使用 __RegistrationKey__ 向提取伺服器註冊節點，進而設定這個屬性，會無法運作。 如需詳細資訊，請參閱[使用設定名稱設定提取用戶端](pullClientConfigNames.md)。| 
| RefreshFrequencyMins| Uint32| LCM 檢查提取伺服器以取得更新設定的時間間隔 (以分鐘為單位)。 如果 LCM 未在提取模式下設定，就會忽略此值。 預設值為 30。<br> __注意__：這個屬性的值必須是 __ConfigurationModeFrequencyMins__ 屬性值的倍數，或者 __ConfigurationModeFrequencyMins__ 屬性值必須是這個屬性值的倍數。| 
| AllowModuleOverwrite| bool| 若允許從設定伺服器下載新設定，以覆寫目標節點上的舊設定，即為 __$TRUE__。 否則為 $FALSE。| 
| DebugMode| 字串| 可能的值為 __None (預設)__、__ForceModuleImport__ 和 __All__。 <ul><li>設為 __None__ 會使用快取資源。 這是預設，而且應該用於實際執行的案例。</li><li>設為 __ForceModuleImport__，會導致 LCM 重新載入任何 DSC 資源模組，即使先前已載入這些模組並已快取。 這會影響 DSC 作業的效能，因為每個模組會在使用時重新載入。 通常會在為資源偵錯時使用此值</li><li>在這一版本中，__All__ 與 __ForceModuleImport__ 相同</li></ul> |
| ConfigurationDownloadManagers| CimInstance[]| 已過時。 使用 __ConfigurationRepositoryWeb__ 和 __ConfigurationRepositoryShare__ 區塊來定義設定提取伺服器。| 
| ResourceModuleManagers| CimInstance[]| 已過時。 使用 __ResourceRepositoryWeb__ 和 __ResourceRepositoryShare__ 區塊來定義資源提取伺服器。| 
| ReportManagers| CimInstance[]| 已過時。 使用 __ReportServerWeb__ 區塊來定義報表提取伺服器。| 
| PartialConfigurations| CimInstance| 未實作。 請勿使用。| 
| StatusRetentionTimeInDays | UInt32| LCM 會保留目前設定狀態的天數。| 

## 提取伺服器

提取伺服器是作為 DSC 檔案中央位置使用的 OData Web 服務或 SMB 共用。 LCM 設定支援定義下列提取伺服器類型：

* **設定伺服器**：DSC 設定的儲存機制。 使用 **ConfigurationRepositoryWeb** (適用於 Web 伺服器) 和 **ConfigurationRepositoryShare** (適用於 SMB 伺服器) 區塊來定義設定伺服器。
* 資源伺服器 — 封裝成 PowerShell 模組的 DSC 資源的儲存機制。 使用 **ResourceRepositoryWeb** (適用於 Web 伺服器) 和 **ResourceRepositoryShare** (適用於 SMB 伺服器) 區塊來定義資源伺服器。
* 報表伺服器 — DSC 傳送報表資料的目標服務。 使用 **ReportServerWeb** 區塊來定義報表伺服器。 報表伺服器必須是 Web 服務。

如需設定和使用提取伺服器的相關資訊，請參閱[設定 DSC 提取伺服器](pullServer.md)。

## 設定伺服器區塊

若要定義 Web 設定伺服器，請建立 **ConfigurationRepositoryWeb** 區塊。 **ConfigurationRepositoryWeb** 定義下列屬性。

|屬性|類型|描述|
|---|---|---| 
|AllowUnsecureConnection|bool|設為 **$TRUE** 即允許從節點到伺服器的未經驗證連線。 設為 **$FALSE** 表示需要驗證。|
|CertificateID|字串|表示用來向伺服器驗證憑證的 GUID。|
|ConfigurationNames|String[]|要由目標節點提取之設定名稱的陣列。 僅有在使用 **RegistrationKey** 向提取伺服器註冊此節點時，才會使用這些設定。 如需詳細資訊，請參閱[使用設定名稱設定提取用戶端](pullClientConfigNames.md)。|
|RegistrationKey|字串|向提取伺服器註冊節點的 GUID。 如需詳細資訊，請參閱[使用設定名稱設定提取用戶端](pullClientConfigNames.md)。|
|ServerURL|字串|設定伺服器的 URL。|

若要定義 SMB 設定伺服器，請建立 **ConfigurationRepositoryShare** 區塊。 **ConfigurationRepositoryShare** 定義下列屬性。

|屬性|類型|描述|
|---|---|---|
|認證|MSFT_Credential|用來向 SMB 驗證的認證。|
|SourcePath|字串|SMB 共用的路徑。|

## 資源伺服器區塊

若要定義 Web 資源伺服器，請建立 **ResourceRepositoryWeb** 區塊。 **ResourceRepositoryWeb** 定義下列屬性。

|屬性|類型|描述|
|---|---|---|
|AllowUnsecureConnection|bool|設為 **$TRUE** 即允許從節點到伺服器的未經驗證連線。 設為 **$FALSE** 表示需要驗證。|
|CertificateID|字串|表示用來向伺服器驗證憑證的 GUID。|
|RegistrationKey|字串|GUID，識別提取伺服器的節點。 如需詳細資訊，請參閱＜如何向 DSC 提取伺服器註冊節點＞。|
|ServerURL|字串|設定伺服器的 URL。|
 
若要定義 SMB 資源伺服器，請建立 **ResourceRepositoryShare** 區塊。 **ResourceRepositoryShare** 定義下列屬性。

|屬性|類型|描述|
|---|---|---|
|認證|MSFT_Credential|用來向 SMB 驗證的認證。|
|SourcePath|字串|SMB 共用的路徑。|

## 報表伺服器區塊

報表伺服器必須是 OData Web 服務。 若要定義報表伺服器，請建立 **ReportServerWeb** 區塊。 **ReportServerWeb** 定義下列屬性。

|屬性|類型|描述|
|---|---|---| 
|AllowUnsecureConnection|bool|設為 **$TRUE** 即允許從節點到伺服器的未經驗證連線。 設為 **$FALSE** 表示需要驗證。|
|CertificateID|字串|表示用來向伺服器驗證憑證的 GUID。|
|RegistrationKey|字串|GUID，識別提取伺服器的節點。 如需詳細資訊，請參閱＜如何向 DSC 提取伺服器註冊節點＞。|
|ServerURL|字串|設定伺服器的 URL。|

## 部分設定

若要定義部分設定，請建立 **PartialConfiguration** 區塊。 如需部分設定的詳細資訊，請參閱 [DSC 部分設定](partialConfigs.md)。 **PartialConfiguration** 定義下列屬性。

|屬性|類型|描述|
|---|---|---| 
|ConfigurationSource|string[]|**ConfiguratoinRepositoryWeb** 和 **ConfigurationRepositoryShare** 區塊中預先定義的設定伺服器名稱陣列，部分設定會從中提取。|
|DependsOn|string{}|必須在套用部分設定之前先完成的其他設定名稱清單。|
|描述|字串|用來描述部分設定的文字。|
|ExclusiveResources|string[]|這個部分設定專用的資源陣列。|
|RefreshMode|字串|指定 LCM 如何取得這個部分設定。 可能的值為 __"Disabled"__、__"Push(default)"__ 和 __"Pull"__。 <ul><li>__Disabled__：停用此部分設定。</li><li> __Push__：藉由呼叫 [Publish-DscConfiguration](https://technet.microsoft.com/en-us/library/mt517875.aspx) Cmdlet 將部分設定推送到節點。 節點的所有部分設定從伺服器發送或提取之後，就可以藉由呼叫 `Start-DscConfiguration –UseExisting` 來啟動。 這是預設值。</li><li>__Pull__：節點設定為定期檢查提取伺服器的部分設定。 如果這個屬性設為 __Pull__，您就必須在 __ConfigurationSource__ 屬性中指定提取伺服器。 如需提取伺服器的詳細資訊，請參閱[設定 DSC 提取伺服器](pullServer.md)。</li></ul>|
|ResourceModuleSource|string[]|要從中下載此部分設定所需資源的資源伺服器名稱陣列。 這些名稱必須參考 **ResourceRepositoryWeb** 和 **ResourceRepositoryShare** 區塊中預先定義的資源伺服器。|

## 另請參閱 

### 概念
[Windows PowerShell 預期狀態設定概觀](overview.md)
 
[設定 DSC 提取伺服器](pullServer.md) 

[Windows PowerShell 4.0 預期狀態設定本機設定管理員](metaConfig4.md) 

### 其他資源
[Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx) 

[使用設定名稱設定提取用戶端](pullClientConfigNames.md) 



<!--HONumber=Jun16_HO3-->


