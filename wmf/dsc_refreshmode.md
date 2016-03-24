# RefreshMode 屬性的額外值

此版本導入新的 `RefreshMode` 值 - **Disabled**。 當設定為此模式時，LCM 不會執行文件管理。 當使用協力廠商的設定管理工具而不是 DSC 時，請使用此模式，同時依然能以 `Invoke-DscResource` Cmdlet 來運用 DSC 的資源，又或著您只是因故需要停止 DSC 處理時，也可以使用此模式。

```powershell
Configuration LCMSettings
{
    Node localhost
    {
        LocalConfigurationManager
        {
           RefreshMode = 'Disabled'
        }
    }
}

LCMSettings -OutputPath .\LCMSettings
Set-DscLocalConfigurationManager -Path .\LCMSettings -Verbose -ComputerName localhost
```
<!--HONumber=Mar16_HO2-->
