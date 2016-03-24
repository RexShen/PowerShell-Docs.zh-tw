# 使用新的中繼設定屬性設定 DSC LCM

`DscLocalConfigurationManager` 屬性將設定區塊指定為中繼設定，用於設定 DSC 本機設定管理員。 此屬性會限制住設定，讓它只包含設定 DSC 本機設定管理員的項目。 在處理期間，此設定會產生 `*.meta.mof` 檔案，然後會使用 `Set-DscLocalConfigurationManager` Cmdlet 將此檔案傳送至適當的目標節點。

```powershell
[DscLocalConfigurationManager()]
configuration meta
{
    Node localhost
    {
        Settings
        {
            ConfigurationMode = "ApplyAndAutocorrect"
            ConfigurationID = "5603f952-d6c6-4971-88c4-948636bf5c3f"
            RefreshMode = "Pull"
        }
        ConfigurationRepositoryWeb PullServer
        {
            ServerURL = "https://corp.contoso.com/PSDSCPullServer/PSDSCPullServer.svc"
        }
    }
}
```

上述範例中將 LCM 的重新整理模式設定為使用 Pull 模式、將設定模式變更為 ApplyAndAutocorrect，並定義提取伺服器的類型和位置。

這個新的設定屬性會取代並延伸 PowerShell 4.0 的 LocalConfigurationManager 資源功能。 設定中仍然支援此 LocalConfigurationManager ，但沒有回溯相容性的屬性。

中繼資源︰

| **資源名稱**            | **描述**                                |
|------------------------------|------------------------------------------------|
| LocalConfigurationManager    | DSC 引擎執行的多項設定      |
| PartialConfiguration         | 部分設定的設定                 |
| ConfigurationRepositoryWeb   | 網頁導向的設定存放庫             |
| ConfigurationRepositoryShare | 以檔案共用為基礎的設定存放庫      |
| ResourceRepositoryWeb        | 網頁導向的資源存放庫                  |
| ResourceRepositoryShare      | 以檔案為基礎的資源存放庫                 |
| ReportServerWeb              | 提取狀況的網頁導向報告端點 |
<!--HONumber=Mar16_HO2-->
