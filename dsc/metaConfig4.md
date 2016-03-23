# Windows PowerShell 4.0 預期狀態設定本機設定管理員 (LCM)

>適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

本機設定管理員是 Windows PowerShell 預期狀態設定 (DSC) 引擎， 會在所有目標節點上執行，負責呼叫包含在 DSC 設定指令碼中的設定資源。 本主題列出本機設定管理員屬性，並說明如何修改目標節點上的本機設定管理員設定。

## 本機設定管理員屬性
以下列出您可以設定或擷取的本機設定管理員屬性。
 
* **AllowModuleOverwrite**：控制是否允許從設定伺服器下載新設定，以覆寫目標節點上舊的設定。 可能的值為 True 和 False。
* **CertificateID**：GUID 憑證，用來保護存取設定的憑證。 如需詳細資訊，請參閱 [Want to secure credentials in Windows PowerShell Desired State Configuration (需要保護 Windows PowerShell 預期狀態設定的憑證嗎？)](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx)。
* **ConfigurationID**：指出用來從設定為「提取」伺服器取得特定設定檔的 GUID。 此 GUID 可確保存取正確的設定檔。
* **ConfigurationMode**：指定本機設定管理員實際上如何將設定套用至目標節點。 它可以接受下列值：
    - **ApplyOnly**：若設定此選項，藉由直接將新設定傳送到目標節點 (“push”)，或如果已設定「提取」伺服器，而且當 DSC 檢查「提取」伺服器時探索到新的設定時，DSC 會套用此設定，除非偵測的新設定，否則不執行進一步動作。 如果目標節點的設定偏離，就不採取任何動作。
    - **ApplyAndMonitor**：若設定此選項 (此為預設值)，藉由直接將新設定傳送到目標節點，或在「提取」伺服器探索，DSC 會套用任何新的設定。 之後，如果目標節點的設定偏離設定檔，DSC 就會報告記錄檔中的差異。 如需 DSC 記錄的資訊，請參閱 [Using Event Logs to Diagnose Errors in Desired State Configuration (在預期狀態設定中使用事件記錄檔診斷錯誤)](http://blogs.msdn.com/b/powershell/archive/2014/01/03/using-event-logs-to-diagnose-errors-in-desired-state-configuration.aspx)。
    - **ApplyAndAutoCorrect**：若設定此選項，藉由直接將新設定傳送到目標節點，或在「提取」伺服器探索，DSC 會套用任何新的設定。 之後，如果目標節點的設定偏離設定檔，DSC 就會報告記錄檔中的差異，然後嘗試調整目標節點設定，以符合設定檔。
* **ConfigurationModeFrequencyMins**代表 DSC 的背景應用程式嘗試實作目標節點上目前設定的頻率 (以分鐘為單位)。 預設值為 15。 這個值可以搭配 RefreshMode 設定。 當 RefreshMode 設定為 PULL 時，目標節點會連絡設定伺服器，頻率為 RefreshFrequencyMins 所設定的間隔，並下載目前的設定。 不論 RefreshMode 值為何，在 ConfigurationModeFrequencyMins 所設定的間隔中，一致性引擎會套用已下載至目標節點的最新設定。 RefreshFrequencyMins 應為 ConfigurationModeFrequencyMins 的整數倍數。
* **Credential**：表示存取遠端資源所需的認證 (如同 Get-Credential)，例如連絡設定伺服器。
* **DownloadManagerCustomData**：代表陣列，其中包含下載管理員特有的自訂資料。
* **DownloadManagerName**：指出設定和模組下載管理員的名稱。
* **RebootNodeIfNeeded**：目標節點上的某些設定變更可能需要重新啟動才能套用變更。 如果該值為 **True**，這個屬性將會在設定已完全套用時立即重新啟動節點，而無進一步警告。 如果為 **False** (預設值)，將會完成設定，但節點必須手動重新啟動，變更才會生效。
* **RefreshFrequencyMins**：當您設定「提取」伺服器時使用。 代表的本機設定管理員連絡「提取」伺服器來下載目前設定的頻率 (以分鐘為單位)。 這個值可以搭配 ConfigurationModeFrequencyMins 設定。 當 RefreshMode 設定為 PULL 時，目標節點會連絡「提取」伺服器，頻率為 RefreshFrequencyMins 所設定的間隔，並下載目前的設定。 在 ConfigurationModeFrequencyMins 所設定的間隔中，一致性引擎接著會套用已下載至目標節點的最新設定。 如果 RefreshFrequencyMins 未設定為 ConfigurationModeFrequencyMins 的整數倍數，則系統會無條件進位。 預設值為 30。
* **RefreshMode**：可能的值為 **Push** (預設值) 和 **Pull**。 在 “push” 設定中，您必須使用任何用戶端電腦，在每個目標節點上放置設定檔。 在 “pull” 模式中，您必須設定 「提取」伺服器，供本機設定管理員來連絡及存取設定檔。

### 更新本機設定管理員設定的範例

您可以更新目標節點的本機設定管理員設定，方法是在設定指令碼中節點區塊內加入 **LocalConfigurationManager** 區塊，如下列範例所示。

```powershell
Configuration ExampleConfig
{
    Node “Server001”
    {
        LocalConfigurationManager
        {
            ConfigurationID = "646e48cb-3082-4a12-9fd9-f71b9a562d4e"
            ConfigurationModeFrequencyMins = 45
            ConfigurationMode = "ApplyAndAutocorrect"
            RefreshMode = "Pull"
            RefreshFrequencyMins = 90
            DownloadManagerName = "WebDownloadManager"
            DownloadManagerCustomData = (@{ServerUrl="https://$PullServer/psdscpullserver.svc"})
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

執行上述範例中的指令碼會產生 MOF 檔案，該檔案指定並儲存所需的設定。 若要套用設定，您可以使用 **Set-DscLocalConfigurationManager** Cmdlet，如下列範例所示。

```powershell
Set-DscLocalConfigurationManager -Path "c:\users\public\dsc"
```

> **注意**：針對 **Path** 參數，當您叫用前一個範例中的設定時，您指定的路徑必須與您為 **OutputPath** 參數所指定的路徑相同。

若要查看目前本機設定管理員設定，您可以使用 **Get-DscLocalConfigurationManager** Cmdlet。 如果您叫用的這個 Cmdlet 不含任何參數，依預設會取得您用來執行此 Cmdlet 之節點的本機設定管理員設定。 若要指定另一個節點，請使用這項 Cmdlet 的 **CimSession** 參數。<!--HONumber=Feb16_HO4-->
