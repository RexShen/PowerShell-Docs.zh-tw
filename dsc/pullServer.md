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
# <a name="desired-state-configuration-pull-service"></a><span data-ttu-id="95e04-103">Desired State Configuration 提取服務</span><span class="sxs-lookup"><span data-stu-id="95e04-103">Desired State Configuration Pull Service</span></span>

> <span data-ttu-id="95e04-104">適用於：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="95e04-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="95e04-105">提取服務解決方案可集中管理本機設定管理員。</span><span class="sxs-lookup"><span data-stu-id="95e04-105">Local Configuration Manager can be centrally managed by a Pull Service solution.</span></span>
<span data-ttu-id="95e04-106">使用這個方法時，受控節點會向服務註冊，然後得到 LCM 設定中的組態指派。</span><span class="sxs-lookup"><span data-stu-id="95e04-106">When using this approach, the node that is being managed is registered with a service and assigned a configuration in LCM settings.</span></span>
<span data-ttu-id="95e04-107">組態及需要當成組態相依性的所有 DSC 資源都會下載到電腦，供 LCM 用來管理組態。</span><span class="sxs-lookup"><span data-stu-id="95e04-107">The configuration and all DSC resources needed as dependencies for the configuration are downloaded to the machine and used by LCM to manage the configuration.</span></span>
<span data-ttu-id="95e04-108">受控電腦的狀態相關資訊會上傳到服務以供回報。</span><span class="sxs-lookup"><span data-stu-id="95e04-108">Information about the state of the machine being managed is uploaded to the service for reporting.</span></span>
<span data-ttu-id="95e04-109">這個概念就是「提取服務」。</span><span class="sxs-lookup"><span data-stu-id="95e04-109">This concept is referred to as "pull service".</span></span>

<span data-ttu-id="95e04-110">目前針對提取服務的選項包括：</span><span class="sxs-lookup"><span data-stu-id="95e04-110">The current options for pull service include:</span></span>

- <span data-ttu-id="95e04-111">Azure 自動化 Desired State Configuration 服務</span><span class="sxs-lookup"><span data-stu-id="95e04-111">Azure Automation Desired State Configuration service</span></span>
- <span data-ttu-id="95e04-112">在 Windows Server 上執行的提取服務</span><span class="sxs-lookup"><span data-stu-id="95e04-112">A pull service running on Windows Server</span></span>
- <span data-ttu-id="95e04-113">社群維護的開放原始碼解決方案</span><span class="sxs-lookup"><span data-stu-id="95e04-113">Community maintained open source solutions</span></span>
- <span data-ttu-id="95e04-114">SMB 共用</span><span class="sxs-lookup"><span data-stu-id="95e04-114">An SMB share</span></span>

<span data-ttu-id="95e04-115">**建議的解決方案** (也是具有最多可用功能的選項) 是 [Azure 自動化 DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="95e04-115">**The recommended solution**, and the option with the most features available, is [Azure Automation DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-getting-started).</span></span>

<span data-ttu-id="95e04-116">Azure 服務可以管理私人資料中心內部部署的節點，或是如 Azure 和 AWS 等公用雲端中的節點。</span><span class="sxs-lookup"><span data-stu-id="95e04-116">The Azure service can manage nodes on-premises in private datacenters, or in public clouds such as Azure and AWS.</span></span>
<span data-ttu-id="95e04-117">針對伺服器無法直接連線至網際網路的私人環境，請考慮將輸出流量限制在發佈的 Azure IP 範圍內 (請參閱 [Azure 資料中心 IP 範圍](https://www.microsoft.com/en-us/download/details.aspx?id=41653) \(英文\))。</span><span class="sxs-lookup"><span data-stu-id="95e04-117">For private environments where servers cannot directly connect to the Internet, consider limiting outbound traffic to only the published Azure IP range (see [Azure Datacenter IP Ranges](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span></span>

<span data-ttu-id="95e04-118">目前無法在 Windows Server 上的提取服務中使用的線上服務功能包括：</span><span class="sxs-lookup"><span data-stu-id="95e04-118">Features of the online service that are not currently available in the pull service on Windows Server include:</span></span>
- <span data-ttu-id="95e04-119">系統會在傳輸和靜止期間加密所有資料</span><span class="sxs-lookup"><span data-stu-id="95e04-119">All data is encrypted in transit and at rest</span></span>
- <span data-ttu-id="95e04-120">系統會自動建立和管理用戶端憑證</span><span class="sxs-lookup"><span data-stu-id="95e04-120">Client certificates are created and managed automatically</span></span>
- <span data-ttu-id="95e04-121">用於集中管理[密碼/認證](https://docs.microsoft.com/en-us/azure/automation/automation-credentials)，或是如伺服器名稱或連接字串等[變數](https://docs.microsoft.com/en-us/azure/automation/automation-variables)的祕密存放區</span><span class="sxs-lookup"><span data-stu-id="95e04-121">Secrets store for centrally managing [passwords/credentials](https://docs.microsoft.com/en-us/azure/automation/automation-credentials), or [variables](https://docs.microsoft.com/en-us/azure/automation/automation-variables) such as server names or connection strings</span></span>
- <span data-ttu-id="95e04-122">集中管理節點 [LCM 設定](metaConfig.md#basic-settings)</span><span class="sxs-lookup"><span data-stu-id="95e04-122">Centrally manage node [LCM configuration](metaConfig.md#basic-settings)</span></span>
- <span data-ttu-id="95e04-123">集中將設定指派給用戶端節點</span><span class="sxs-lookup"><span data-stu-id="95e04-123">Centrally assign configurations to client nodes</span></span>
- <span data-ttu-id="95e04-124">在設定變更抵達生產環境之前，先將它發行至「金絲雀群組」以進行測試</span><span class="sxs-lookup"><span data-stu-id="95e04-124">Release configuration changes to "canary groups" for testing before reaching production</span></span>
- <span data-ttu-id="95e04-125">圖形化報告</span><span class="sxs-lookup"><span data-stu-id="95e04-125">Graphical reporting</span></span>
  - <span data-ttu-id="95e04-126">以 DSC 資源細微度層級提供的狀態詳細資料</span><span class="sxs-lookup"><span data-stu-id="95e04-126">Status detail at the DSC resource level of granularity</span></span>
  - <span data-ttu-id="95e04-127">來自用戶端電腦的詳細資訊錯誤訊息以供進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="95e04-127">Verbose error messages from client machines for troubleshooting</span></span>
- <span data-ttu-id="95e04-128">[與 Azure Log Analytics 整合](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-diagnostics)以取得警示功能、自動化工作、針對報告及警示的 Android/iOS 應用程式</span><span class="sxs-lookup"><span data-stu-id="95e04-128">[Integration with Azure Log Analytics](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-diagnostics) for alerting, automated tasks, Android/iOS app for reporting and alerting</span></span>

## <a name="dsc-pull-service-in-windows-server"></a><span data-ttu-id="95e04-129">Windows Server 中的 DSC 提取服務</span><span class="sxs-lookup"><span data-stu-id="95e04-129">DSC pull service in Windows Server</span></span>

<span data-ttu-id="95e04-130">您可以設定提取服務，使其在 Windows Server 上執行。</span><span class="sxs-lookup"><span data-stu-id="95e04-130">It is possible to configuring a pull service to run on Windows Server.</span></span>
<span data-ttu-id="95e04-131">請注意，Windows Server 中的提取服務解決方案僅含有儲存組態/模組以供下載，以及將報表資料擷取到資料庫的功能。</span><span class="sxs-lookup"><span data-stu-id="95e04-131">Please be advised that the pull service solution included in Windows Server includes only capabilities of storing configurations/modules for download and capturing report data in to database.</span></span>
<span data-ttu-id="95e04-132">有許多 Azure 服務提供的功能並未包含在內，因此不是適合評估服務使用方式的工具。</span><span class="sxs-lookup"><span data-stu-id="95e04-132">It does not include many of the capabilities offered by the service in Azure and so is not a good tool for evaluating how the service would be used.</span></span>

<span data-ttu-id="95e04-133">Windows Server 中提供的提取服務是 IIS 中的一種 Web 服務，在目標節點要求 DSC 組態檔時，會使用 OData 介面讓這些節點能夠使用這些組態檔。</span><span class="sxs-lookup"><span data-stu-id="95e04-133">The pull service offered in Windows Server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="95e04-134">使用提取伺服器的需求：</span><span class="sxs-lookup"><span data-stu-id="95e04-134">Requirements for using a pull server:</span></span>

- <span data-ttu-id="95e04-135">伺服器需執行：</span><span class="sxs-lookup"><span data-stu-id="95e04-135">A server running:</span></span>
  - <span data-ttu-id="95e04-136">WMF/PowerShell 5.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="95e04-136">WMF/PowerShell 5.0 or greater</span></span>
  - <span data-ttu-id="95e04-137">IIS 伺服器角色</span><span class="sxs-lookup"><span data-stu-id="95e04-137">IIS server role</span></span>
  - <span data-ttu-id="95e04-138">DSC 服務</span><span class="sxs-lookup"><span data-stu-id="95e04-138">DSC Service</span></span>
- <span data-ttu-id="95e04-139">在理想情況下，某些用來保護憑證的憑證產生方式，可傳遞到在目標節點的本機設定管理員 (LCM)。</span><span class="sxs-lookup"><span data-stu-id="95e04-139">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="95e04-140">設定 Windows Server 使其裝載提取服務的最佳方法，是使用 DSC 組態。</span><span class="sxs-lookup"><span data-stu-id="95e04-140">The best way to configure Windows Server to host pull service is to use a DSC configuration.</span></span>
<span data-ttu-id="95e04-141">下方提供一段範例指令碼。</span><span class="sxs-lookup"><span data-stu-id="95e04-141">An example script is provided below.</span></span>

### <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="95e04-142">使用 xDSCWebService 資源</span><span class="sxs-lookup"><span data-stu-id="95e04-142">Using the xDSCWebService resource</span></span>

<span data-ttu-id="95e04-143">設定 Web 提取伺服器的最簡單方式，是使用包含在 xPSDesiredStateConfiguration 模組的 xWebService 資源。</span><span class="sxs-lookup"><span data-stu-id="95e04-143">The easiest way to set up a web pull server is to use the xWebService resource, included in the xPSDesiredStateConfiguration module.</span></span>
<span data-ttu-id="95e04-144">下列步驟說明如何使用設定 Web 服務之設定中的資源。</span><span class="sxs-lookup"><span data-stu-id="95e04-144">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="95e04-145">呼叫 [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) Cmdlet 以安裝 **xPSDesiredStateConfiguration** 模組。</span><span class="sxs-lookup"><span data-stu-id="95e04-145">Call the [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span> <span data-ttu-id="95e04-146">**注意**：**Install-Module** 已納入 **PowerShellGet** 模組，其隨附於 PowerShell 5.0。</span><span class="sxs-lookup"><span data-stu-id="95e04-146">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="95e04-147">您可以在 [PackageManagement PowerShell 模組預覽](https://www.microsoft.com/en-us/download/details.aspx?id=49186)下載 PowerShell 3.0 和 4.0 的 **PowerShellGet** 模組。</span><span class="sxs-lookup"><span data-stu-id="95e04-147">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span> 
1. <span data-ttu-id="95e04-148">在組織或公開授權單位中，從信任的憑證授權單位取得 DSC 提取伺服器的 SSL 憑證。</span><span class="sxs-lookup"><span data-stu-id="95e04-148">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="95e04-149">從授權單位收到的憑證通常為 PFX 格式。</span><span class="sxs-lookup"><span data-stu-id="95e04-149">The certificate received from the authority is usually in the PFX format.</span></span> <span data-ttu-id="95e04-150">在即將成為預設位置 (應為 CERT:\LocalMachine\My) 中 DSC 提取伺服器的節點上安裝憑證。</span><span class="sxs-lookup"><span data-stu-id="95e04-150">Install the certificate on the node that will become the DSC Pull server in the default location which should be CERT:\LocalMachine\My.</span></span> <span data-ttu-id="95e04-151">記下憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="95e04-151">Make a note of the certificate thumbprint.</span></span>
1. <span data-ttu-id="95e04-152">選取要作為註冊金鑰使用的 GUID。</span><span class="sxs-lookup"><span data-stu-id="95e04-152">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="95e04-153">若要使用 PowerShell 產生一個 GUID，請在 PS 命令提示字元中輸入下列命令，然後按 Enter 鍵：'``` [guid]::newGuid()```' 或 '```New-Guid```'。</span><span class="sxs-lookup"><span data-stu-id="95e04-153">To generate one using PowerShell enter the following at the PS prompt and press enter: '``` [guid]::newGuid()```' or '```New-Guid```'.</span></span> <span data-ttu-id="95e04-154">用戶端節點會使用此金鑰作為共用金鑰，以在註冊期間進行驗證。</span><span class="sxs-lookup"><span data-stu-id="95e04-154">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="95e04-155">如需詳細資訊，請參閱下面的＜註冊金鑰＞一節。</span><span class="sxs-lookup"><span data-stu-id="95e04-155">For more information see the Registration Key section below.</span></span>
1. <span data-ttu-id="95e04-156">在 PowerShell ISE 中，啟動 (F5) 下列設定指令碼 (包含於 **xPSDesiredStateConfiguration** 模組的 Example 資料夾的 Sample_xDscWebService.ps1)。</span><span class="sxs-lookup"><span data-stu-id="95e04-156">In the PowerShell ISE, start (F5) the following configuration script (included in the Example folder of the  **xPSDesiredStateConfiguration** module as Sample_xDscWebService.ps1).</span></span> <span data-ttu-id="95e04-157">此指令碼會設定提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="95e04-157">This script sets up the pull server.</span></span>

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

1. <span data-ttu-id="95e04-158">執行設定，傳遞 SSL 憑證的指紋作為 **certificateThumbPrint** 參數，以及 GUID 註冊金鑰作為 **RegistrationKey** 參數：</span><span class="sxs-lookup"><span data-stu-id="95e04-158">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store 
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDSCPullServer -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose

```

#### <a name="registration-key"></a><span data-ttu-id="95e04-159">註冊金鑰</span><span class="sxs-lookup"><span data-stu-id="95e04-159">Registration Key</span></span>

<span data-ttu-id="95e04-160">若要讓用戶端向伺服器註冊，使其可以使用設定名稱，而非設定識別碼，上述設定所建立的註冊金鑰會儲存在 `C:\Program Files\WindowsPowerShell\DscService` 中名為 `RegistrationKeys.txt` 的檔案。</span><span class="sxs-lookup"><span data-stu-id="95e04-160">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key which was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="95e04-161">註冊金鑰會當作共用密碼，在用戶端向提取伺服器初始註冊期間使用。</span><span class="sxs-lookup"><span data-stu-id="95e04-161">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="95e04-162">用戶端會產生自我簽署的憑證，以在成功完成註冊之後，用來向提取伺服器進行唯一驗證。</span><span class="sxs-lookup"><span data-stu-id="95e04-162">The client will generate a self-signed certificate which is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="95e04-163">此憑證的指紋會儲存在本機，並與提取伺服器的 URL 相關聯。</span><span class="sxs-lookup"><span data-stu-id="95e04-163">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>
> <span data-ttu-id="95e04-164">**注意**：PowerShell 4.0 中不支援註冊金鑰。</span><span class="sxs-lookup"><span data-stu-id="95e04-164">**Note**: Registration keys are not supported in PowerShell 4.0.</span></span> 

<span data-ttu-id="95e04-165">若要設定節點向提取伺服器進行驗證，對於要向此提取伺服器註冊的任何目標節點，其中繼設定內都必須要有註冊金鑰。</span><span class="sxs-lookup"><span data-stu-id="95e04-165">In order to configure a node to authenticate with the pull server the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="95e04-166">請注意，成功註冊目標電腦之後，會移除下面中繼設定內的 **RegistrationKey**，而且值 '140a952b-b9d6-406b-b416-e0f759c9c0e4' 必須符合儲存在提取伺服器之 RegistrationKeys.txt 檔案中的值。</span><span class="sxs-lookup"><span data-stu-id="95e04-166">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value '140a952b-b9d6-406b-b416-e0f759c9c0e4' must match the value stored in the RegistrationKeys.txt file on the pull server.</span></span> <span data-ttu-id="95e04-167">請務必保護註冊金鑰值，因為知道此值可向提取伺服器註冊任何目標電腦。</span><span class="sxs-lookup"><span data-stu-id="95e04-167">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

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

> <span data-ttu-id="95e04-168">**注意**：**ReportServerWeb** 區段允許將報告資料傳送至提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="95e04-168">**Note**: The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span>

<span data-ttu-id="95e04-169">中繼設定檔內缺乏 **ConfigurationID** 屬性即隱含表示提取伺服器支援提取伺服器通訊協定 V2 版，因此需要初始註冊。</span><span class="sxs-lookup"><span data-stu-id="95e04-169">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span>
<span data-ttu-id="95e04-170">相反地，出現 **ConfigurationID** 則表示會使用提取伺服器通訊協定 V1 版，而且不會處理註冊。</span><span class="sxs-lookup"><span data-stu-id="95e04-170">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

><span data-ttu-id="95e04-171">**注意**︰在 PUSH 案例中，目前版本有 Bug，必須針對尚未向提取伺服器註冊的節點，於中繼設定檔內定義 ConfigurationID 屬性。</span><span class="sxs-lookup"><span data-stu-id="95e04-171">**Note**: In a PUSH scenario, a bug exists in the current relase that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="95e04-172">這會強制執行 V1 提取伺服器通訊協定，並避免出現註冊失敗訊息。</span><span class="sxs-lookup"><span data-stu-id="95e04-172">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="95e04-173">放置設定和資源</span><span class="sxs-lookup"><span data-stu-id="95e04-173">Placing configurations and resources</span></span>

<span data-ttu-id="95e04-174">提取伺服器設定完成之後，提取伺服器設定中 **ConfigurationPath** 和 **ModulePath** 屬性所定義的資料夾會是您放置模組和設定，以供目標節點提取的位置。</span><span class="sxs-lookup"><span data-stu-id="95e04-174">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span>
<span data-ttu-id="95e04-175">這些檔案必須使用特定格式，提取伺服器才能正確地加以處理。</span><span class="sxs-lookup"><span data-stu-id="95e04-175">These files need to be in a specific format in order for the pull server to correctly process them.</span></span>

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="95e04-176">DSC 資源模組封裝格式</span><span class="sxs-lookup"><span data-stu-id="95e04-176">DSC resource module package format</span></span>

<span data-ttu-id="95e04-177">每個資源模組都必須根據下列模式進行壓縮及命名：`{Module Name}_{Module Version}.zip`。</span><span class="sxs-lookup"><span data-stu-id="95e04-177">Each resource module needs to be zipped and named according the following pattern `{Module Name}_{Module Version}.zip`.</span></span>
<span data-ttu-id="95e04-178">例如，名為 xWebAdminstration 且模組版本為 3.1.2.0 的模組會命名為 'xWebAdministration_3.2.1.0.zip'。</span><span class="sxs-lookup"><span data-stu-id="95e04-178">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span>
<span data-ttu-id="95e04-179">一個壓縮檔必須包含一個模組版本。</span><span class="sxs-lookup"><span data-stu-id="95e04-179">Each version of a module must be contained in a single zip file.</span></span>
<span data-ttu-id="95e04-180">因為每個壓縮檔中只會有一個資源版本，所以不支援在 WMF 5.0 中新增可支援單一目錄中有多個模組版本的模組格式。</span><span class="sxs-lookup"><span data-stu-id="95e04-180">Since there is only a single version of a resource in each zip file the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span>
<span data-ttu-id="95e04-181">這表示在封裝 DSC 資源模組以搭配提取伺服器使用之前，您必須對目錄結構進行小幅變更。</span><span class="sxs-lookup"><span data-stu-id="95e04-181">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span>
<span data-ttu-id="95e04-182">在 WMF 5.0 中包含 DSC 資源的模組預設格式為 '{模組資料夾}\{模組版本}\DscResources\{DSC 資源資料夾}\'。</span><span class="sxs-lookup"><span data-stu-id="95e04-182">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span>
<span data-ttu-id="95e04-183">在為提取伺服器進行封裝前，只要移除 **{模組版本}** 資料夾，路徑就會變成 '{模組資料夾}\DscResources\{DSC 資源資料夾}\'。</span><span class="sxs-lookup"><span data-stu-id="95e04-183">Before packaging up for the pull server simply remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span>
<span data-ttu-id="95e04-184">完成這項變更之後，如上所述壓縮資料夾，並將這些壓縮檔放在 **ModulePath** 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="95e04-184">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="95e04-185">使用 `new-dscchecksum {module zip file}` 為新增的模組建立總和檢查碼檔案。</span><span class="sxs-lookup"><span data-stu-id="95e04-185">Use `new-dscchecksum {module zip file}` to create a checksum file for the newly-added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="95e04-186">設定 MOF 格式</span><span class="sxs-lookup"><span data-stu-id="95e04-186">Configuration MOF format</span></span>

<span data-ttu-id="95e04-187">設定 MOF 檔案需要與總和檢查碼檔案配對，以便目標節點上的 LCM 可驗證設定。</span><span class="sxs-lookup"><span data-stu-id="95e04-187">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="95e04-188">若要建立總和檢查碼，請呼叫 [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="95e04-188">To create a checksum, call the [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet.</span></span>
<span data-ttu-id="95e04-189">此 Cmdlet 會使用 **Path** 參數，指定設定 MOF 所在的資料夾。</span><span class="sxs-lookup"><span data-stu-id="95e04-189">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span>
<span data-ttu-id="95e04-190">此 Cmdlet 會建立名為 `ConfigurationMOFName.mof.checksum` 的總和檢查碼檔案，其中 `ConfigurationMOFName` 是設定 MOF 檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="95e04-190">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="95e04-191">如果在指定的資料夾中有多個設定 MOF 檔案，就會在每個設定資料夾中各建立一個總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="95e04-191">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>
<span data-ttu-id="95e04-192">將 MOF 檔案及其相關總和檢查碼檔案置於 **ConfigurationPath** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="95e04-192">Place the MOF files and their associated checksum files in the **ConfigurationPath** folder.</span></span>

><span data-ttu-id="95e04-193">**注意**：如果您以任何方式變更設定 MOF 檔案，也必須重新建立總和檢查碼檔案。</span><span class="sxs-lookup"><span data-stu-id="95e04-193">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

### <a name="tooling"></a><span data-ttu-id="95e04-194">工具</span><span class="sxs-lookup"><span data-stu-id="95e04-194">Tooling</span></span>

<span data-ttu-id="95e04-195">為了讓您更輕鬆地設定、驗證和管理提取伺服器，下列工具將納入作為最新版 xPSDesiredStateConfiguration 模組中的範例︰</span><span class="sxs-lookup"><span data-stu-id="95e04-195">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>

1. <span data-ttu-id="95e04-196">有助於封裝 DSC 資源模組和設定檔以供提取伺服器使用的模組。</span><span class="sxs-lookup"><span data-stu-id="95e04-196">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span> <span data-ttu-id="95e04-197">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1)。</span><span class="sxs-lookup"><span data-stu-id="95e04-197">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span> <span data-ttu-id="95e04-198">範例如下：</span><span class="sxs-lookup"><span data-stu-id="95e04-198">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @("xWebAdministration", "xPhp") 
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList 

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="95e04-199">驗證提取伺服器是否正確設定的指令碼。</span><span class="sxs-lookup"><span data-stu-id="95e04-199">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="95e04-200">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1)。</span><span class="sxs-lookup"><span data-stu-id="95e04-200">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>

## <a name="community-solutions-for-pull-service"></a><span data-ttu-id="95e04-201">適用於提取服務的社群解決方案</span><span class="sxs-lookup"><span data-stu-id="95e04-201">Community Solutions for Pull Service</span></span>

<span data-ttu-id="95e04-202">DSC 社群撰寫了多個解決方案來實作提取服務通訊協定。</span><span class="sxs-lookup"><span data-stu-id="95e04-202">The DSC community has authored multiple solutions to implement the pull service protocol.</span></span>
<span data-ttu-id="95e04-203">對於內部部署環境，這些解決方案提供了提取服務功能，而且有機會以累加的功能改進回饋給社群。</span><span class="sxs-lookup"><span data-stu-id="95e04-203">For on-premises environments these offer pull service capabilities and an opportunity to contribute back to the community with incremental enhancements.</span></span>

- [<span data-ttu-id="95e04-204">Tug</span><span class="sxs-lookup"><span data-stu-id="95e04-204">Tug</span></span>](https://github.com/powershellorg/tug)
- [<span data-ttu-id="95e04-205">DSC-TRÆK</span><span class="sxs-lookup"><span data-stu-id="95e04-205">DSC-TRÆK</span></span>](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a><span data-ttu-id="95e04-206">提取用戶端設定</span><span class="sxs-lookup"><span data-stu-id="95e04-206">Pull client configuration</span></span>

<span data-ttu-id="95e04-207">下列主題將詳細描述如何設定提取用戶端：</span><span class="sxs-lookup"><span data-stu-id="95e04-207">The following topics describe setting up pull clients in detail:</span></span>

- [<span data-ttu-id="95e04-208">使用設定識別碼設定 DSC 提取用戶端</span><span class="sxs-lookup"><span data-stu-id="95e04-208">Setting up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
- [<span data-ttu-id="95e04-209">使用設定名稱設定 DSC 提取用戶端</span><span class="sxs-lookup"><span data-stu-id="95e04-209">Setting up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
- [<span data-ttu-id="95e04-210">部分設定</span><span class="sxs-lookup"><span data-stu-id="95e04-210">Partial configurations</span></span>](partialConfigs.md)

## <a name="see-also"></a><span data-ttu-id="95e04-211">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95e04-211">See also</span></span>

- [<span data-ttu-id="95e04-212">Windows PowerShell 預期狀態設定概觀</span><span class="sxs-lookup"><span data-stu-id="95e04-212">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
- [<span data-ttu-id="95e04-213">制定組態</span><span class="sxs-lookup"><span data-stu-id="95e04-213">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="95e04-214">使用 DSC 報表伺服器</span><span class="sxs-lookup"><span data-stu-id="95e04-214">Using a DSC report server</span></span>](reportServer.md)
