# 隔離設定、資源及報表的存放庫

在此版本中我們讓您擁有所需的彈性，以對一個或多個 DSC 提取伺服器進行提取和報告。 每個端點可以分開定義，所以您可以從一個位置提取設定、從另一個位置提取資源，再從另一個位置提取報告。 下列中繼設定就是在執行這項動作。

```PowerShell
[DscLocalConfigurationManager()]
Configuration SampleMetaConfig
{
    Settings
    {
        RefreshMode = "PULL";
        AllowModuleOverwrite = $true;
        RebootNodeIfNeeded = $true;
    }

    ConfigurationRepositoryWeb Configurations
    {
        ServerURL = “https://PullServerMachine:8080/psdscpullserver.svc”
        RegistrationKey = "140a952b-b9d6-406b-b416-e0f759c9c0e4"
    }

    ResourceRepositoryWeb Resources
    {
        ServerURL = “https://ResourceServer:8080/psdscpullserver.svc”
        RegistrationKey = "aaaf952b-b9d6-406b-b416-e0f759c6e000"
    }

    ReportServerWeb Reports
    {
        ServerURL = “https://ReportServer:8080/psdscpullserver.svc”
        RegistrationKey = "fefe592b-b9d6-046b-b146-e0f759c0c0c0"
    }
}
```

此外，您還可以使用上述的任何組合。 下列中繼設定會設定在 Push 模式中的目標節點，但節點將會提取沒有從「DSC 提取伺服器」安裝的資源，而且會將其狀態報告到另一部「DSC 提取伺服器」。


```PowerShell
[DscLocalConfigurationManager()]
Configuration SampleMetaConfig
{
    Settings
    {
        RefreshMode = "Push";
        RebootNodeIfNeeded = $true;
    }

    ResourceRepositoryWeb Resources
    {
        ServerURL = “https://ResourceServer:8080/psdscpullserver.svc”
        RegistrationKey = "aaaf952b-b9d6-406b-b416-e0f759c6e000"
    }

    ReportServerWeb Reports
    {
        ServerURL = “https://ReportServer:8080/psdscpullserver.svc”
        RegistrationKey = "fefe592b-b9d6-046b-b146-e0f759c0c0c0"
    }
}
```<!--HONumber=Mar16_HO2-->
