# 在 PowerShell 4.0 使用設定識別碼設定提取用戶端

>適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

必須告知每個目標節點使用提取模式和指定的 URL，其中它可連絡提取伺服器以取得設定。 若要這樣做，您必須使用必要的資訊來設定本機設定管理員 (LCM)。 若要設定 LCM，您可以建立一種特殊的設定，稱為「中繼設定」。 如需設定 LCM 的詳細資訊，請參閱 [Windows PowerShell 4.0 預期狀態設定本機設定管理員](metaConfig4.md)

下列指令碼會設定 LCM 從名為 "PullServer" 的伺服器提取設定：

```powershell
Configuration SimpleMetaConfigurationForPull 
{ 
    LocalConfigurationManager 
    { 
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "WebDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 15;
        ConfigurationModeFrequencyMins = 30; 
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = “TRUE”}
    } 
} 
SimpleMetaConfigurationForPull -Output "."
```

在此指令碼中，**DownloadManagerCustomData** 會傳遞提取伺服器的 URL，並 (適用於此範例) 允許不安全的連線。 

執行這個指令碼之後，它會建立新的輸出資料夾，稱為 **SimpleMetaConfigurationForPull**，並在該處放入中繼設定 MOF 檔案。

若要套用此設定，請以 **ComputerName** (使用 "localhost") 和 **Path** (目標節點的 localhost.meta.mof 檔案位置路徑) 參數使用 **Set-DscLocalConfigurationManager**。 例如： 
```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path . –Verbose.
```

## 設定識別碼
此指令碼將 LCM 的 **ConfigurationID** 屬性設為先前針對這個用途建立的 GUID (可透過 **New-Guid** Cmdlet 建立 GUID)。 **ConfigurationID** 供 LCM 用來在提取伺服器上尋找適當設定。 提取伺服器上的設定 MOF 檔案必須命名為 `ConfigurationID.mof`，其中 *ConfigurationID* 是目標節點 LCM 的 **ConfigurationID** 屬性值。

## 從 SMB 伺服器提取

如果將提取伺服器設定為 SMB 檔案共用，而不是 Web 服務，您會指定 **DscFileDownloadManager**，而不是 **WebDownLoadManager**。
**DscFileDownloadManager** 採用 **SourcePath** 屬性而非 **ServerUrl**。 下列指令碼會設定 LCM 從
伺服器 "CONTOSO-SERVER" 上名為 "SmbDscShare" 的 SMB 共用提取設定：

```powershell
Configuration SimpleMetaConfigurationForPull 
{ 
    LocalConfigurationManager 
    { 
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "DscFileDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 15;
        ConfigurationModeFrequencyMins = 30; 
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "\\CONTOSO-SERVER\SmbDscShare"}
    } 
} 
SimpleMetaConfigurationForPull -Output "."
```

## 另請參閱

- [設定 DSC Web 提取伺服器](pullServer.md)
- [設定 DSC SMB 提取伺服器](pullServerSMB.md)

<!--HONumber=Mar16_HO2-->


