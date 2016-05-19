# 設定 DSC Web 提取伺服器

> 適用於：Windows PowerShell 5.0

DSC Web 提取伺服器是一種 Web 服務，在目標節點請求 DSC 設定檔時，可使用 OData 介面將 DSC 設定檔提供給這些目標節點。

使用提取伺服器的需求：

* 伺服器需執行：
  - WMF/PowerShell 5.0 或更新版本
  - IIS 伺服器角色
  - DSC 服務
* 在理想情況下，某些用來保護憑證的憑證產生方式，可傳遞到在目標節點的本機設定管理員 (LCM)。

您可以使用 [伺服器管理員] 中的 [新增角色及功能精靈]，或使用 PowerShell 新增 IIS 伺服器角色與 DSC 服務。 本主題中所包含的範例指令碼也將為您處理這兩個步驟。

## 使用 xWebService 資源
設定 Web 提取伺服器的最簡單方式，是使用包含在 xPSDesiredStateConfiguration 模組的 xWebService 資源。 下列步驟說明如何使用設定 Web 服務之設定中的資源。

1. 呼叫 [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) Cmdlet 以安裝 **xPSDesiredStateConfiguration** 模組。 **注意**：**Install-Module** 已納入 **PowerShellGet** 模組，其隨附於 PowerShell 5.0。 您可以在 [PackageManagement PowerShell 模組預覽](https://www.microsoft.com/en-us/download/details.aspx?id=49186)中下載 PowerShell 3.0 和 4.0 的 **PowerShellGet** 模組. 
1. 從您組織或公開授權單位內受信任的憑證授權單位，取得 DSC 提取伺服器的 SSL 憑證。 從授權單位收到的憑證通常使用 PFX 格式。 在即將成為預設位置 (應為 CERT:\LocalMachine\My) 中 DSC 提取伺服器的節點上安裝憑證。 記下憑證指紋。
1. 選取要作為註冊金鑰使用的 GUID。 若要使用 PowerShell 產生一個 GUID，請在 PS 命令提示字元中輸入下列命令，然後按 Enter 鍵：'``` [guid]::newGuid()```'。 用戶端節點會使用此金鑰作為共用金鑰，以在註冊期間進行驗證。 如需詳細資訊，請參閱下面的[註冊金鑰](#RegKey)一節。
1. 在 PowerShell ISE 中，啟動 (F5) 下列設定指令碼 (包含於 **xPSDesiredStateConfiguration** 模組的 Example 資料夾的 Sample_xDscWebService.ps1)。 此指令碼會設定提取伺服器。
  
```powershell
configuration Sample_xDscPullServer
{ 
    param  
    ( 
            [string[]]$NodeName = 'localhost', 
            
            [ValidateNotNullOrEmpty()] 
            [string] $certificateThumbPrint,
            
            [Parameter(Mandatory)]
            [ValidateNotNullOrEmpty()]
            [string] $RegistrationKey 
     ) 
 
 
     Import-DSCResource -ModuleName xPSDesiredStateConfiguration 

     Node $NodeName 
     { 
         WindowsFeature DSCServiceFeature 
         { 
             Ensure = 'Present'
             Name   = 'DSC-Service'             
         } 
 
         xDscWebService PSDSCPullServer 
         { 
             Ensure                  = 'Present' 
             EndpointName            = 'PSDSCPullServer' 
             Port                    = 8080 
             PhysicalPath            = "$env:SystemDrive\inetpub\PSDSCPullServer" 
             CertificateThumbPrint   = $certificateThumbPrint          
             ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules" 
             ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration" 
             State                   = 'Started'
             DependsOn               = '[WindowsFeature]DSCServiceFeature'                         
         } 

        File RegistrationKeyFile
        {
            Ensure          = 'Present'
            Type            = 'File'
            DestinationPath = "$env:ProgramFiles\WindowsPowerShell\DscService\RegistrationKeys.txt"
            Contents        = $RegistrationKey
        }
    }
}

```

1. 執行設定，傳遞 SSL 憑證的指紋作為 **certificateThumbPrint** 參數，以及 GUID 註冊金鑰作為 **RegistrationKey** 參數：

```powershell
# To find the Thumbprint for an installed SSL certificate for use with the pull server list all certifcates in your local store 
# and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
dir Cert:\LocalMachine\my

# Then include this thumbprint when running the configuration
Sample_xDSCPullServer -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutpuPath c:\Configs\PullServer

# Run the compiled configuration to make the target node a DSC Pull Server
Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
```

## 註冊金鑰
若要讓用戶端向伺服器註冊，使其可以使用設定名稱，而非設定識別碼，上述設定所建立的註冊金鑰會儲存在 `C:\Program Files\WindowsPowerShell\DscService` 中名為 `RegistrationKeys.txt` 的檔案。 註冊金鑰會當作共用密碼，在用戶端向提取伺服器初始註冊期間使用。 用戶端會產生自我簽署的憑證，以在成功完成註冊之後，用來向提取伺服器進行唯一驗證。 此憑證的指紋會儲存在本機，並與提取伺服器的 URL 相關聯。
> **注意**：PowerShell 4.0 中不支援註冊金鑰。 

若要設定節點向提取伺服器進行驗證，要向此提取伺服器註冊之任何目標節點的中繼設定內都必須有此註冊金鑰。 請注意，成功註冊目標電腦之後，會移除下面中繼設定內的 **RegistrationKey**，而且值 '140a952b-b9d6-406b-b416-e0f759c9c0e4' 必須符合儲存在提取伺服器之 RegistrationKeys.txt 檔案中的值。 請務必保護註冊金鑰值，因為知道此值可向提取伺服器註冊任何目標電腦。

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode          = 'Pull'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded   = $true
        }
        
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey    = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }   
        
        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
        }
    }
}

PullClientConfigID -OutputPath c:\Configs\TargetNodes
```
> **注意**：**ReportServerWeb** 區段允許將報告資料傳送至提取伺服器。 

中繼設定檔內缺乏 **ConfigurationID** 屬性即隱含表示提取伺服器支援提取伺服器通訊協定 V2 版，因此需要初始註冊。 相反地，出現 **ConfigurationID** 則表示會使用提取伺服器通訊協定 V1 版，而且不會處理註冊。

>**注意**︰在 PUSH 案例中，目前版本有 Bug，必須針對尚未向提取伺服器註冊的節點，於中繼設定檔內定義 ConfigurationID 屬性。 這會強制執行 V1 提取伺服器通訊協定，並避免出現註冊失敗訊息。

## 放置設定和資源
提取伺服器設定完成之後，提取伺服器設定中 **ConfigurationPath** 和 **ModulePath** 屬性所定義的資料夾會是您放置模組和設定，以供目標節點提取的位置。 這些檔案必須使用特定格式，提取伺服器才能正確地加以處理。 

### DSC 資源模組封裝格式
每個資源模組都必須根據下列模式 **{模組名稱}_{模組版本}.zip** 進行壓縮及命名。 例如，名為 xWebAdminstration 且模組版本為 3.1.2.0 的模組會命名為 'xWebAdministration_3.2.1.0.zip'。 一個壓縮檔必須包含一個模組版本。 因為每個壓縮檔中只會有一個資源版本，所以不支援在 WMF 5.0 中新增可支援單一目錄中有多個模組版本的模組格式。 這表示在封裝 DSC 資源模組以搭配提取伺服器使用之前，您必須對目錄結構進行小幅變更。 在 WMF 5.0 中包含 DSC 資源之模組的預設格式為「{模組資料夾}\{模組版本}\DscResources\{DSC 資源資料夾}\」。 在針對提取伺服器封裝之前，只移除 **{模組版本}** 資料夾，讓路徑成為「{模組資料夾}\DscResources\{DSC 資源資料夾}\」。 完成這項變更之後，如上所述壓縮資料夾，並將這些壓縮檔放在 **ModulePath** 資料夾中。

### 設定 MOF 格式 
設定 MOF 檔案需要與總和檢查碼檔案配對，以便目標節點上的 LCM 可驗證設定。 若要建立總和檢查碼，請呼叫 [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) Cmdlet。 此 Cmdlet 會使用 **Path** 參數，指定設定 MOF 所在的資料夾。 此 Cmdlet 會建立名為 `ConfigurationMOFName.mof.checksum` 的總和檢查碼檔案，其中 `ConfigurationMOFName` 是設定 MOF 檔案的名稱。 如果在指定的資料夾中有多個設定 MOF 檔案，就會在每個設定資料夾中各建立一個總和檢查碼。 將 MOF 檔案及其相關聯的總和檢查碼檔案放在 **ConfigurationPath** 資料夾中。

>**注意**：如果您以任何方式變更設定 MOF 檔案，也必須重新建立總和檢查碼檔案。

## 工具
為了讓您更輕鬆地設定、驗證和管理提取伺服器，下列工具將納入作為最新版 xPSDesiredStateConfiguration 模組中的範例︰
1. 有助於封裝 DSC 資源模組和設定檔以供提取伺服器使用的模組。 [PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1)。 範例如下：

```powershell
    # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
     $moduleList = @("xWebAdministration", "xPhp") 
     Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList 
     
     # Example 2 - Package modules and mof documents from c:\LocalDepot
     Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
```

1. 驗證提取伺服器是否正確設定的指令碼。 [PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/Examples/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).


## 提取用戶端設定 
下列主題將詳細描述如何設定提取用戶端：

* [使用設定識別碼設定 DSC 提取用戶端](pullClientConfigID.md)
* [使用設定名稱設定 DSC 提取用戶端](pullClientConfigNames.md)
* [部分設定](partialConfigs.md)


## 另請參閱
* [Windows PowerShell 預期狀態設定概觀](overview.md)
* [施行設定](enactingConfigurations.md)
* [使用 DSC 報表伺服器](reportServer.md)


<!--HONumber=May16_HO1-->


