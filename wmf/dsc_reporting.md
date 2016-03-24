# 將設定狀態回報到中央位置

DSC 設定狀態的詳細資訊可以傳送到執行 DSC 服務的伺服器。 由 Get-DscConfigurationStatus Cmdlet 傳回的相同資訊會傳送至 DSC 服務。 藉由定義中繼設定中的報表伺服器，當發生錯誤或設定成功完成時，此狀態會傳送到伺服器。 在 Pull 或 Push 模式中設定節點時，會傳送這項資訊。 狀態資訊儲存於 DSC 服務資料庫中。

## 報告狀態的範例中繼設定
```PowerShell
[DscLocalConfigurationManager()]
Configuration ReportingClientMetaConfig
{
    Settings
        {
            RefreshFrequencyMins = 30
            RefreshMode = "PUSH"
            ConfigurationModeFrequencyMins = 15
            AllowModuleOverwrite = $true
        }

        ReportServerWeb ReportManager
        {
            ServerUrL = "http://localhost:8080/PSDSCPullServer/PSDSCPullserver.svc"
            AllowUnsecureConnection  = $true
        }           
}
```
使用 DSC 服務建立的新 OData 端點會公開此狀態資訊。 藉由傳遞設定識別碼或代理程式識別碼 {$guid} 至端點，可以收集並剖析節點的所有狀態。

## 範例網路要求收集設定狀態 
```PowerShell
$statusReports = Invoke-WebRequest -Uri "[http://localhost:8080/PSDSCPullserver/PSDSCPullserver.svc/Node(ConfigurationId='$guid')/StatusReport](http://localhost:8080/PSDSCPullserver/psdscpullserver.svc/Node(ConfigurationId='$guid')/StatusReport)s" -UseBasicParsing -UseDefaultCredentials -ContentType "application/json;odata=minimalmetadata;streaming=true;charset=utf-8" -Headers @{Accept = "application/json"; ProtocolVersion = “1.1”}
```<!--HONumber=Mar16_HO2-->
