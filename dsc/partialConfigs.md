# PowerShell 預期狀態設定部分設定

>適用於：Windows PowerShell 5.0

在 PowerShell 5.0 中，預期狀態設定 (DSC) 可讓設定以片段形式和從多個來源傳送。 目標節點上本機設定管理員 (LCM) 先將片段放在一起，再當成單一設定套用。 這項功能可讓團隊或個人之間共用設定控制權。 例如，如果兩個或多個開發人員小組在一項服務共同作業，便有可能每個人都想要建立設定來管理服務的一部分。 每一種設定可能提取自不同提取伺服器，因此無法將它們加入開發的不同階段。 部分設定也可讓不同的個人或小組控制設定節點的不同層面，而不需要協調單一設定文件的編輯。 例如，一個小組可能會負責部署 VM 和作業系統，而另一個小組負責在該 VM 上部署其他應用程式和服務。 藉由部分設定，每個小組都可以建立自己的設定，而不會讓任一組的設定不必要地複雜。

您可以藉由推送模式、提取模式或兩者組合來使用部分設定。

## 推送模式中的部分設定
若要在推送模式下使用部分設定，您可以設定目標節點上的 LCM 接收部分設定。 每個部分設定都必須使用 Publish-DSCConfiguration Cmdlet 推送至目標。 目標節點接著將部分設定結合至單一設定中，您也可以呼叫 [Start-DscConfigurationxt](https://technet.microsoft.com/en-us/library/dn521623.aspx) Cmdlet 來套用設定。

### 設定推送模式部分設定的 LCM
若要設定推送模式中部分設定的 LCM，請對每個部分設定建立 **DSCLocalConfigurationManager** 設定與一個 **PartialConfiguration** 區塊。 如需設定 LCM 的詳細資訊，請參閱 [Windows Configuring the Local Configuration Manager (Windows 設定本機設定管理員)](https://technet.microsoft.com/en-us/library/mt421188.aspx)。 下列範例顯示預期會有兩個部分設定的 LCM 設定，其中一個部署作業系統，另一個部署及設定 SharePoint。

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {
        
           PartialConfiguration OSInstall
        {
            Description = 'Configuration for the Base OS'
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

每個部分設定的 **RefreshMode** 設為 "Push"。 **PartialConfiguration** 區塊的名稱 (在此情況下為 "OSInstall" 和 "SharePointConfig") 必須完全符合推送至目標節點的設定名稱。

### 發佈和啟動推送模式部分設定
![PartialConfig 資料夾結構](./images/PartialConfig1.jpg)

然後您可對每個設定呼叫 **Publish-DSCConfiguration**，傳遞包含設定文件的資料夾作為 Path 參數。 發佈這兩種設定之後，您可以在目標節點上呼叫 `Start-DSCConfiguration –UseExisting`。

## 提取模式中的部分設定

部分設定可從一或多個提取伺服器提取 (如需提取伺服器的詳細資訊，請參閱 [Windows PowerShell 期望狀態設定提取伺服器](pullServer.md)。 若要這樣做，您必須在目標節點上設定 LCM，以提取部分設定，並在提取伺服器上適當地命名和放置設定文件。

### 設定提取節點設定 LCM

若要設定 LCM 從提取伺服器提取部分設定，您必須在 **ConfigurationRepositoryWeb** (適用於 HTTP 提取伺服器) 或 **ConfigurationRepositoryShare** (適用於 SMB 提取伺服器) 區塊定義提取伺服器。 接著建立 **PartialConfiguration** 區塊，該區塊可使用 **ConfigurationSource** 屬性參考提取伺服器。 您也需要建立 Settings 區塊以指定 LCM 使用提取模式，並指定提取伺服器與目標節點用來識別設定的 ConfigurationID。 下列中繼設定會定義名為 CONTOSO-PullSrv 的 HTTP 提取伺服器，和使用該提取伺服器的兩個部分設定。

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            
        }
        
           PartialConfiguration OSInstall
        {
            Description = 'Configuration for the Base OS'
            ConfigurationSource = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description = 'Configuration for the Sharepoint Server'
            ConfigurationSource = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            DependsOn = [PartialConfiguration]OSInstall
            RefreshMode = 'Pull'
        }
    }
}
PartialConfigDemo 
```

您可以從一部以上的提取伺服器提取部分設定，您只需要定義每部提取伺服器，並在每個 PartialConfiguration 區塊中參考適當的提取伺服器。

建立中繼設定之後，您必須執行此設定來建立設定文件 (MOF 檔案)，然後呼叫 [Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621(v=wps.630).aspx) 以設定 LCM。

### 在提取伺服器上命名和放置設定文件

部分設定文件必須位於提取伺服器的 `web.config` 檔案 (通常為 `C:\Program Files\WindowsPowerShell\DscService\Configuration`) 內指定為 **ConfigurationPath** 的資料夾中。 設定文件名稱必須如下命名：_ConfigurationName_。 _ConfigurationID_`.mof`，其中 _ConfigurationName_ 是部分設定的名稱，而 _ConfigurationID_ 是目標節點上 LCM 中所定義的設定識別碼。 在此範例中，設定文件名稱應該如下。
![在提取伺服器上的 PartialConfig 名稱](images/PartialConfigPullServer.jpg)

### 從提取伺服器中執行部分設定

已在目標節點上設定 LCM 之後，且已在提取伺服器上建立並正確將設定文件命名之後，目標節點將會提取部分設定、結合部分設定，並依據 LCM 屬性 **RefreshFrequencyMins** 所指定的固定間隔套用所產生的設定。 如果您想要強制重新整理，您可以呼叫 Update-DscConfiguration Cmdlet 以提取設定，然後呼叫 `Start-DSCConfiguration –UseExisting` 以套用設定。

## 混合推送和提取模式中的部分設定

您也可以混和部分設定的推送和提取模式。 也就是說，推送另一個部分設定時，您可能會有一個從提取伺服器提取的部分設定。 請根據前一節所述的重新整理模式，像平常一樣處理每個部分設定。 例如，下列中繼設定描述相同的範例，其中作業系統部分設定位在提取模式下，而 SharePoint 部分設定位在推送模式下。

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            
        }
        
           PartialConfiguration OSInstall
        {
            Description = 'Configuration for the Base OS'
            ConfigurationSource = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description = 'Configuration for the Sharepoint Server'
            DependsOn = [PartialConfiguration]OSInstall
            RefreshMode = 'Push'
        }
    }
}
PartialConfigDemo 
```

請注意，在 Settings 區塊中指定的 **RefreshMode** 為 "Pull"，但 OSInstall 部分設定的 **RefreshMode** 會是 "Push"。

您可如上面所述，對其各自的重新整理模式命名和放置設定文件。 您可以呼叫 **Publish-DSCConfiguration** 來發佈 SharePointInstall 部分設定，然後等待 OSInstall 設定從提取伺服器上提取，或藉由呼叫 [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541(v=wps.630).aspx) 強制重新整理。

##另請參閱 

**概念**
[Windows PowerShell 預期狀態設定提取伺服器](pullServer.md)
[Windows 設定本機設定管理員](https://technet.microsoft.com/en-us/library/mt421188.aspx) 
<!--HONumber=Feb16_HO4-->
