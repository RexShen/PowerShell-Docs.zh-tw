---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: PowerShell 預期狀態設定部分設定
description: DSC 可讓設定以片段形式傳送及從多個來源傳送。 目標節點上的 LCM 會先將片段結合，再以單一設定的形式加以套用。
ms.openlocfilehash: 3afe5d684cabec9c8ab528347610b6dd00c5d4e9
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661613"
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a>PowerShell 預期狀態設定部分設定

> 適用於︰Windows PowerShell 5.0 及更新版本。

在 PowerShell 5.0 中，預期狀態設定 (DSC) 可讓設定以片段形式和從多個來源傳送。 目標節點上本機設定管理員 (LCM) 先將片段放在一起，再當成單一設定套用。 這項功能可讓團隊或個人之間共用設定控制權。 例如，如果兩個或多個開發人員小組在一項服務共同作業，便有可能每個人都想要建立設定來管理服務的一部分。 每一種設定可能提取自不同提取伺服器，因此無法將它們加入開發的不同階段。 部分設定也可讓不同的個人或小組控制設定節點的不同層面，而不需要協調單一設定文件的編輯。 例如，一個小組可能會負責部署 VM 和作業系統，而另一個小組負責在該 VM 上部署其他應用程式和服務。 藉由部分設定，每個小組都可以建立自己的設定，而不會讓任一組的設定不必要地複雜。

您可以藉由推送模式、提取模式或兩者組合來使用部分設定。

## <a name="partial-configurations-in-push-mode"></a>推送模式中的部分設定

若要在推送模式下使用部分設定，您可以設定目標節點上的 LCM 接收部分設定。 每個部分設定都必須使用 `Publish-DSCConfiguration` Cmdlet 推送至目標。 目標節點接著將部分設定結合至單一設定中，您也可以呼叫 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) Cmdlet 來套用設定。

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a>設定推送模式部分設定的 LCM

若要設定推送模式中部分設定的 LCM，請對每個部分設定建立 **DSCLocalConfigurationManager** 設定與一個 **PartialConfiguration** 區塊。 如需設定 LCM 的詳細資訊，請參閱 [Windows 設定本機設定管理員](../managing-nodes/metaConfig.md)。 下列範例顯示預期會有兩個部分設定的 LCM 設定，其中一個部署作業系統，另一個部署及設定 SharePoint。

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {

        PartialConfiguration ServiceAccountConfig
        {
            Description = 'Configuration to add the SharePoint service account to the Administrators group.'
            RefreshMode = 'Push'
        }
           PartialConfiguration SharePointConfig
        {
            Description = 'Configuration for the SharePoint server'
            RefreshMode = 'Push'
        }
    }
}

PartialConfigDemo
```

每個部分設定的 **RefreshMode** 均設為 "Push"。 **PartialConfiguration** 區塊的名稱 (在此情況下為 "ServiceAccountConfig" 和 "SharePointConfig") 必須完全符合推送至目標節點的設定名稱。

> [!Note]
> 每個 **PartialConfiguration** 區塊的名稱都必須符合設定在設定指令碼中指定的實際名稱，而不是應為目標節點或 `localhost` 名稱的 MOF 檔案名稱。

### <a name="publishing-and-starting-push-mode-partial-configurations"></a>發佈和啟動推送模式部分設定

然後您可對每個設定呼叫 [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)，傳遞包含設定文件的資料夾作為 **Path** 參數。 `Publish-DSCConfiguration` 將設定 MOF 檔案放至目標節點。 發佈這兩種設定之後，您可以在目標節點上呼叫 `Start-DSCConfiguration –UseExisting`。

例如，如果您編譯了撰寫節點上的下列設定 MOF 文件︰

```powershell
Get-ChildItem -Recurse
```

```output
    Directory: C:\PartialConfigTest

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        8/11/2016   1:55 PM                ServiceAccountConfig
d-----       11/17/2016   4:14 PM                SharePointConfig

    Directory: C:\PartialConfigTest\ServiceAccountConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        8/11/2016   2:02 PM           2034 TestVM.mof

    Directory: C:\PartialConfigTest\SharePointConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       11/17/2016   4:14 PM           1930 TestVM.mof
```

您會發行並執行設定，如下所示︰

```powershell
Publish-DscConfiguration .\ServiceAccountConfig -ComputerName 'TestVM'
Publish-DscConfiguration .\SharePointConfig -ComputerName 'TestVM'
Start-DscConfiguration -UseExisting -ComputerName 'TestVM'
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
17     Job17           Configuratio... Running       True            TestVM            Start-DscConfiguration...
```

> [!Note]
> 執行 [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) Cmdlet 的使用者必須在目標節點上具備系統管理員權限。

## <a name="partial-configurations-in-pull-mode"></a>提取模式中的部分設定

部分設定可從一或多個提取伺服器提取 (如需提取伺服器的詳細資訊，請參閱 [Windows PowerShell 期望狀態設定提取伺服器](pullServer.md))。 若要這樣做，您必須在目標節點上設定 LCM，以提取部分設定，並在提取伺服器上適當地命名和放置設定文件。

### <a name="configuring-the-lcm-for-pull-node-configurations"></a>設定提取節點設定 LCM

若要設定 LCM 從提取伺服器提取部分設定，您必須在 **ConfigurationRepositoryWeb** (適用於 HTTP 提取伺服器) 或 **ConfigurationRepositoryShare** (適用於 SMB 提取伺服器) 區塊定義提取伺服器。 接著建立 **PartialConfiguration** 區塊，該區塊可使用 **ConfigurationSource** 屬性參考提取伺服器。 您也需要建立 **Settings** 區塊以指定 LCM 使用提取模式，並指定提取伺服器與目標節點用來識別設定的 **ConfigurationNames** 或 **ConfigurationID** 。 下列中繼設定會定義名為 CONTOSO-PullSrv 的 HTTP 提取伺服器，和使用該提取伺服器的兩個部分設定。

如需使用 **ConfigurationNames** 設定 LCM 的詳細資訊，請參閱 [使用設定名稱設定提取用戶端](pullClientConfigNames.md)。 如需使用 **ConfigurationID** 設定 LCM 的相關資訊，請參閱 [使用設定識別碼設定提取用戶端](pullClientConfigID.md)。

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a>使用設定名稱設定提取節點設定的 LCM

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               ="ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
        }
}
```

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a>使用 ConfigurationID 設定提取節點設定的 LCM

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemoConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode                     = 'Pull'
            ConfigurationID                 = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins            = 30
            RebootNodeIfNeeded              = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description                     = 'Configuration for the Base OS'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode                     = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description                     = 'Configuration for the Sharepoint Server'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Pull'
        }
    }
}
PartialConfigDemo
```

您可以從一部以上的提取伺服器提取部分設定，只需要定義每部提取伺服器，然後在每個 **PartialConfiguration** 區塊中參考適當的提取伺服器即可。

建立中繼設定之後，您必須執行此設定來建立設定文件 (MOF 檔案)，然後呼叫 [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) 以設定 LCM。

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a>在提取伺服器上放置設定文件並為其命名 (ConfigurationNames)

部分設定文件必須位於提取伺服器的 `web.config` 檔案 (通常為 `C:\Program
Files\WindowsPowerShell\DscService\Configuration`) 內指定為 **ConfigurationPath** 的資料夾中。

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a>PowerShell 5.1 中命名提取伺服器上的命名設定文件

如果您僅從個別提取伺服器提取單一部分設定，設定文件可以使用任何名稱。 如果您從提取伺服器提取多個部分設定，設定文件可以命名為 `<ConfigurationName>.mof` (其中 *ConfigurationName* 是部分設定的名稱) 或是 `<ConfigurationName>.<NodeName>.mof` (其中 *ConfigurationName* 是部分設定的名稱，而 *NodeName* 是目標節點的名稱)。 這可讓您從 Azure 自動化 DSC 提取伺服器提取設定。

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a>PowerShell 5.0 中命名提取伺服器上的命名設定文件

設定文件必須命名如下：`ConfigurationName.mof`，其中 *ConfigurationName* 是部分設定的名稱。 在此範例中，設定文件應該命名如下：

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a>在提取伺服器上放置設定文件並為其命名 (ConfigurationID)

部分設定文件必須位於提取伺服器的 `web.config` 檔案 (通常為 `C:\Program Files\WindowsPowerShell\DscService\Configuration`) 內指定為 **ConfigurationPath** 的資料夾中。 設定文件必須命名如下：`<ConfigurationName>.<ConfigurationID>.mof`，其中 _ConfigurationName_ 是部分設定的名稱，而 _ConfigurationID_ 是目標節點上 LCM 中所定義的設定識別碼。 在此範例中，設定文件應該命名如下：

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```

### <a name="running-partial-configurations-from-a-pull-server"></a>從提取伺服器中執行部分設定

在已設定目標節點上的 LCM 後，並已在提取伺服器上建立設定文件並正確加以命名後，目標節點將會提取部分設定、結合部分設定，並依據 LCM 屬性 **RefreshFrequencyMins** 所指定的固定間隔套用所產生的設定。 如果您想要強制重新整理，可以呼叫 [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) Cmdlet 以提取設定，然後呼叫 `Start-DSCConfiguration –UseExisting` 加以套用。

## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a>混合推送和提取模式中的部分設定

您也可以混和部分設定的推送和提取模式。 也就是說，推送另一個部分設定時，您可能會有一個從提取伺服器提取的部分設定。 指定每個部分設定的重新整理模式，如同先前小節中所述。 例如，下列中繼設定描述相同的範例，其中 `ServiceAccountConfig` 部分設定處於 Pull 模式，而 `SharePointConfig` 部分設定則處於 Push 模式。

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a>使用 ConfigurationNames 的混合推送和提取模式

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               = "ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            RefreshMode                     = 'Pull'
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Push'
        }

}
```

### <a name="mixed-push-and-pull-modes-using-configurationid"></a>使用 ConfigurationID 的混合推送和提取模式

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {
        Settings
        {
            RefreshMode             = 'Pull'
            ConfigurationID         = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins    = 30
            RebootNodeIfNeeded      = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL               = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description             = 'Configuration for the Base OS'
            ConfigurationSource     = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode             = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description             = 'Configuration for the Sharepoint Server'
            DependsOn               = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode             = 'Push'
        }
    }
}
PartialConfigDemo
```

請注意，在 Settings 區塊中指定的 **RefreshMode** 為 "Pull"，但 `SharePointConfig` 部分設定的 **RefreshMode** 則是 "Push"。

如上面所述，對其各自的重新整理模式命名和放置設定 MOF 檔案。
呼叫 `Publish-DSCConfiguration` 來發佈 `SharePointConfig` 部分設定，然後等待 `ServiceAccountConfig` 設定從提取伺服器上提取，或藉由呼叫 [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) 強制重新整理。

## <a name="example-serviceaccountconfig-partial-configuration"></a>ServiceAccountConfig 部分設定範例

```powershell
Configuration ServiceAccountConfig
{
    Param (
        [Parameter(Mandatory,
                   HelpMessage="Domain credentials required to add domain\sharepoint_svc to the local Administrators group.")]
        [ValidateNotNullOrEmpty()]
        [pscredential]$Credential
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Group LocalAdmins
        {
            GroupName           = 'Administrators'
            MembersToInclude    = 'domain\sharepoint_svc',
                                  'admins@example.domain'
            Ensure              = 'Present'
            Credential          = $Credential
        }

        WindowsFeature Telnet
        {
            Name                = 'Telnet-Server'
            Ensure              = 'Absent'
        }
    }
}
ServiceAccountConfig
```

## <a name="example-sharepointconfig-partial-configuration"></a>SharePointConfig 部分設定範例

```powershell
Configuration SharePointConfig
{
    Param (
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [pscredential]$ProductKey
    )

    Import-DscResource -ModuleName xSharePoint

    Node localhost
    {
        xSPInstall SharePointDefault
        {
            Ensure      = 'Present'
            BinaryDir   = '\\FileServer\Installers\Sharepoint\'
            ProductKey  = $ProductKey
        }
    }
}
SharePointConfig
```

## <a name="see-also"></a>另請參閱

[Windows PowerShell 預期狀態設定提取伺服器](pullServer.md)

[Windows 設定本機設定管理員](../managing-nodes/metaConfig.md)
