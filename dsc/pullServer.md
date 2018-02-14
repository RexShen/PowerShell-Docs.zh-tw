---
ms.date: 2018-02-02
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "DSC 提取服務"
ms.openlocfilehash: d5e24dcc093c73d8ebbaa618517193dacc4f2aaf
ms.sourcegitcommit: 755d7bc0740573d73613cedcf79981ca3dc81c5e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="desired-state-configuration-pull-service"></a>Desired State Configuration 提取服務

> 適用於：Windows PowerShell 5.0

提取服務解決方案可集中管理本機設定管理員。
使用這個方法時，受控節點會向服務註冊，然後得到 LCM 設定中的組態指派。
組態及需要當成組態相依性的所有 DSC 資源都會下載到電腦，供 LCM 用來管理組態。
受控電腦的狀態相關資訊會上傳到服務以供回報。
這個概念就是「提取服務」。

目前針對提取服務的選項包括：

- Azure 自動化 Desired State Configuration 服務
- 在 Windows Server 上執行的提取服務
- 社群維護的開放原始碼解決方案
- SMB 共用

**建議的解決方案** (也是具有最多可用功能的選項) 是 [Azure 自動化 DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-getting-started)。

Azure 服務可以管理私人資料中心內部部署的節點，或是如 Azure 和 AWS 等公用雲端中的節點。
針對伺服器無法直接連線至網際網路的私人環境，請考慮將輸出流量限制在發佈的 Azure IP 範圍內 (請參閱 [Azure 資料中心 IP 範圍](https://www.microsoft.com/en-us/download/details.aspx?id=41653) \(英文\))。

目前無法在 Windows Server 上的提取服務中使用的線上服務功能包括：
- 系統會在傳輸和靜止期間加密所有資料
- 系統會自動建立和管理用戶端憑證
- 用於集中管理[密碼/認證](https://docs.microsoft.com/en-us/azure/automation/automation-credentials)，或是如伺服器名稱或連接字串等[變數](https://docs.microsoft.com/en-us/azure/automation/automation-variables)的祕密存放區
- 集中管理節點 [LCM 設定](metaConfig.md#basic-settings)
- 集中將設定指派給用戶端節點
- 在設定變更抵達生產環境之前，先將它發行至「金絲雀群組」以進行測試
- 圖形化報告
  - 以 DSC 資源細微度層級提供的狀態詳細資料
  - 來自用戶端電腦的詳細資訊錯誤訊息以供進行疑難排解
- [與 Azure Log Analytics 整合](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-diagnostics)以取得警示功能、自動化工作、針對報告及警示的 Android/iOS 應用程式

## <a name="dsc-pull-service-in-windows-server"></a>Windows Server 中的 DSC 提取服務

您可以設定提取服務，使其在 Windows Server 上執行。
請注意，Windows Server 中的提取服務解決方案僅含有儲存組態/模組以供下載，以及將報表資料擷取到資料庫的功能。
有許多 Azure 服務提供的功能並未包含在內，因此不是適合評估服務使用方式的工具。

Windows Server 中提供的提取服務是 IIS 中的一種 Web 服務，在目標節點要求 DSC 組態檔時，會使用 OData 介面讓這些節點能夠使用這些組態檔。

使用提取伺服器的需求：

- 伺服器需執行：
  - WMF/PowerShell 5.0 或更新版本
  - IIS 伺服器角色
  - DSC 服務
- 在理想情況下，某些用來保護憑證的憑證產生方式，可傳遞到在目標節點的本機設定管理員 (LCM)。

設定 Windows Server 使其裝載提取服務的最佳方法，是使用 DSC 組態。
下方提供一段範例指令碼。

### <a name="using-the-xdscwebservice-resource"></a>使用 xDSCWebService 資源

設定 Web 提取伺服器的最簡單方式，是使用包含在 xPSDesiredStateConfiguration 模組的 xWebService 資源。
下列步驟說明如何使用設定 Web 服務之設定中的資源。

1. 呼叫 [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) Cmdlet 以安裝 **xPSDesiredStateConfiguration** 模組。 **注意**：**Install-Module** 已納入 **PowerShellGet** 模組，其隨附於 PowerShell 5.0。 您可以在 [PackageManagement PowerShell 模組預覽](https://www.microsoft.com/en-us/download/details.aspx?id=49186)下載 PowerShell 3.0 和 4.0 的 **PowerShellGet** 模組。 
1. 在組織或公開授權單位中，從信任的憑證授權單位取得 DSC 提取伺服器的 SSL 憑證。 從授權單位收到的憑證通常為 PFX 格式。 在即將成為預設位置 (應為 CERT:\LocalMachine\My) 中 DSC 提取伺服器的節點上安裝憑證。 記下憑證指紋。
1. 選取要作為註冊金鑰使用的 GUID。 若要使用 PowerShell 產生一個 GUID，請在 PS 命令提示字元中輸入下列命令，然後按 Enter 鍵：'``` [guid]::newGuid()```' 或 '```New-Guid```'。 用戶端節點會使用此金鑰作為共用金鑰，以在註冊期間進行驗證。 如需詳細資訊，請參閱下面的＜註冊金鑰＞一節。
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
         Import-DSCResource –ModuleName PSDesiredStateConfiguration

         Node $NodeName
         {
             WindowsFeature DSCServiceFeature
             {
                 Ensure = 'Present'
                 Name   = 'DSC-Service'
             }

             xDscWebService PSDSCPullServer
             {
                 Ensure                   = 'Present'
                 EndpointName             = 'PSDSCPullServer'
                 Port                     = 8080
                 PhysicalPath             = "$env:SystemDrive\inetpub\PSDSCPullServer"
                 CertificateThumbPrint    = $certificateThumbPrint
                 ModulePath               = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
                 ConfigurationPath        = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
                 State                    = 'Started'
                 DependsOn                = '[WindowsFeature]DSCServiceFeature'
                 UseSecurityBestPractices = $false
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
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store 
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDSCPullServer -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose

```

#### <a name="registration-key"></a>註冊金鑰

若要讓用戶端向伺服器註冊，使其可以使用設定名稱，而非設定識別碼，上述設定所建立的註冊金鑰會儲存在 `C:\Program Files\WindowsPowerShell\DscService` 中名為 `RegistrationKeys.txt` 的檔案。 註冊金鑰會當作共用密碼，在用戶端向提取伺服器初始註冊期間使用。 用戶端會產生自我簽署的憑證，以在成功完成註冊之後，用來向提取伺服器進行唯一驗證。 此憑證的指紋會儲存在本機，並與提取伺服器的 URL 相關聯。
> **注意**：PowerShell 4.0 中不支援註冊金鑰。 

若要設定節點向提取伺服器進行驗證，對於要向此提取伺服器註冊的任何目標節點，其中繼設定內都必須要有註冊金鑰。 請注意，成功註冊目標電腦之後，會移除下面中繼設定內的 **RegistrationKey**，而且值 '140a952b-b9d6-406b-b416-e0f759c9c0e4' 必須符合儲存在提取伺服器之 RegistrationKeys.txt 檔案中的值。 請務必保護註冊金鑰值，因為知道此值可向提取伺服器註冊任何目標電腦。

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

中繼設定檔內缺乏 **ConfigurationID** 屬性即隱含表示提取伺服器支援提取伺服器通訊協定 V2 版，因此需要初始註冊。
相反地，出現 **ConfigurationID** 則表示會使用提取伺服器通訊協定 V1 版，而且不會處理註冊。

>**注意**︰在 PUSH 案例中，目前版本有 Bug，必須針對尚未向提取伺服器註冊的節點，於中繼設定檔內定義 ConfigurationID 屬性。 這會強制執行 V1 提取伺服器通訊協定，並避免出現註冊失敗訊息。

## <a name="placing-configurations-and-resources"></a>放置設定和資源

提取伺服器設定完成之後，提取伺服器設定中 **ConfigurationPath** 和 **ModulePath** 屬性所定義的資料夾會是您放置模組和設定，以供目標節點提取的位置。
這些檔案必須使用特定格式，提取伺服器才能正確地加以處理。

### <a name="dsc-resource-module-package-format"></a>DSC 資源模組封裝格式

每個資源模組都必須根據下列模式進行壓縮及命名：`{Module Name}_{Module Version}.zip`。
例如，名為 xWebAdminstration 且模組版本為 3.1.2.0 的模組會命名為 'xWebAdministration_3.2.1.0.zip'。
一個壓縮檔必須包含一個模組版本。
因為每個壓縮檔中只會有一個資源版本，所以不支援在 WMF 5.0 中新增可支援單一目錄中有多個模組版本的模組格式。
這表示在封裝 DSC 資源模組以搭配提取伺服器使用之前，您必須對目錄結構進行小幅變更。
在 WMF 5.0 中包含 DSC 資源的模組預設格式為 '{模組資料夾}\{模組版本}\DscResources\{DSC 資源資料夾}\'。
在為提取伺服器進行封裝前，只要移除 **{模組版本}** 資料夾，路徑就會變成 '{模組資料夾}\DscResources\{DSC 資源資料夾}\'。
完成這項變更之後，如上所述壓縮資料夾，並將這些壓縮檔放在 **ModulePath** 資料夾中。

使用 `new-dscchecksum {module zip file}` 為新增的模組建立總和檢查碼檔案。

### <a name="configuration-mof-format"></a>設定 MOF 格式

設定 MOF 檔案需要與總和檢查碼檔案配對，以便目標節點上的 LCM 可驗證設定。
若要建立總和檢查碼，請呼叫 [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) Cmdlet。
此 Cmdlet 會使用 **Path** 參數，指定設定 MOF 所在的資料夾。
此 Cmdlet 會建立名為 `ConfigurationMOFName.mof.checksum` 的總和檢查碼檔案，其中 `ConfigurationMOFName` 是設定 MOF 檔案的名稱。
如果在指定的資料夾中有多個設定 MOF 檔案，就會在每個設定資料夾中各建立一個總和檢查碼。
將 MOF 檔案及其相關總和檢查碼檔案置於 **ConfigurationPath** 資料夾。

>**注意**：如果您以任何方式變更設定 MOF 檔案，也必須重新建立總和檢查碼檔案。

### <a name="tooling"></a>工具

為了讓您更輕鬆地設定、驗證和管理提取伺服器，下列工具將納入作為最新版 xPSDesiredStateConfiguration 模組中的範例︰

1. 有助於封裝 DSC 資源模組和設定檔以供提取伺服器使用的模組。 [PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1)。 範例如下：

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @("xWebAdministration", "xPhp") 
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList 

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. 驗證提取伺服器是否正確設定的指令碼。 [PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1)。

## <a name="community-solutions-for-pull-service"></a>適用於提取服務的社群解決方案

DSC 社群撰寫了多個解決方案來實作提取服務通訊協定。
對於內部部署環境，這些解決方案提供了提取服務功能，而且有機會以累加的功能改進回饋給社群。

- [Tug](https://github.com/powershellorg/tug)
- [DSC-TRÆK](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a>提取用戶端設定

下列主題將詳細描述如何設定提取用戶端：

- [使用設定識別碼設定 DSC 提取用戶端](pullClientConfigID.md)
- [使用設定名稱設定 DSC 提取用戶端](pullClientConfigNames.md)
- [部分設定](partialConfigs.md)

## <a name="see-also"></a>另請參閱

- [Windows PowerShell 預期狀態設定概觀](overview.md)
- [制定組態](enactingConfigurations.md)
- [使用 DSC 報表伺服器](reportServer.md)
