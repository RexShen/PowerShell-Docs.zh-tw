# 以多個設定片段 (部分設定) 來設定節點

WMF 5.0 會協助您在片段中將設定文件傳遞到節點。 如需讓節點接收設定文件的多個片段，則必須設定其本機設定管理員 (LCM)，以指定必須的片段，如此範例所示。

```powershell
[DSCLocalConfigurationManager()]
configuration SQLServerDSCSettings
{
    Node localhost
    {
        Settings
        {
            ConfigurationModeFrequencyMins = 30
        }

        ConfigurationRepositoryWeb OSConfigServer
        {
            ServerURL = "https://corp.contoso.com/OSConfigServer/PSDSCPullServer.svc"
        }

        ConfigurationRepositoryWeb SQLConfigServer
        {
            ServerURL = "https://corp.contoso.com/SQLConfigServer/PSDSCPullServer.svc"
        }

        PartialConfiguration OSConfig
        {
            Description = 'Configuration for the Base OS'
            ExclusiveResources = 'PSDesiredStateConfiguration\*'
            ConfigurationSource = '[ConfigurationRepositoryWeb]OSConfigServer'
        }

        PartialConfiguration SQLConfig
        {
            Description = 'Configuration for the SQL Server'
            ConfigurationSource = '[ConfigurationRepositoryWeb]SQLConfigServer'
            DependsOn = '[PartialConfiguration]OSConfig'
        }
    }
}
```

在部分設定中，設定名稱必須符合 LCM 中定義的名稱。 在上述範例中，設定應該命名為 `OSConfig` 和 `SQLConfig`。

為部分設定進行 LCM 設定可讓設定相互協調，但不提供安全性功能。<!--HONumber=Mar16_HO2-->
