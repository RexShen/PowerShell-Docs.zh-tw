---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 使用 DSC 來建置持續整合和持續部署管線
ms.openlocfilehash: 2d049cd640f0df9b018a88ad106e59dbeed7bcee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954235"
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a><span data-ttu-id="4ce9e-103">使用 DSC 來建置持續整合和持續部署管線</span><span class="sxs-lookup"><span data-stu-id="4ce9e-103">Building a Continuous Integration and Continuous Deployment pipeline with DSC</span></span>

<span data-ttu-id="4ce9e-104">此範例示範如何使用 PowerShell、DSC、Pester 及 Visual Studio Team Foundation Server (TFS) 來建置「持續整合/持續部署」(CI/CD) 管線。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-104">This example demonstrates how to build a Continuous Integration/Continuous Deployment (CI/CD) pipeline by using PowerShell, DSC, Pester, and Visual Studio Team Foundation Server (TFS).</span></span>

<span data-ttu-id="4ce9e-105">建置並設定管線之後，您便可以使用它來完整部署、設定及測試 DNS 伺服器和相關的主機記錄。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-105">After the pipeline is built and configured, you can use it to fully deploy, configure and test a DNS server and associated host records.</span></span>
<span data-ttu-id="4ce9e-106">此程序會模擬將在開發環境中使用之管線的第一個部分。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-106">This process simulates the first part of a pipeline that would be used in a development environment.</span></span>

<span data-ttu-id="4ce9e-107">自動化的 CI/CD 管線可協助您以更快且更可靠的方式更新軟體，確保所有程式碼都經過測試，並且您程式碼的最新組建隨時可供使用。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-107">An automated CI/CD pipeline helps you update software faster and more reliably, ensuring that all code is tested, and that a current build of your code is available at all times.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4ce9e-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="4ce9e-108">Prerequisites</span></span>

<span data-ttu-id="4ce9e-109">若要使用此範例，您應該熟悉下列各項知識：</span><span class="sxs-lookup"><span data-stu-id="4ce9e-109">To use this example, you should be familiar with the following:</span></span>

- <span data-ttu-id="4ce9e-110">CI-CD 概念。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-110">CI-CD concepts.</span></span> <span data-ttu-id="4ce9e-111">如需詳細的參考資料，請參閱[發行管線模型](https://aka.ms/thereleasepipelinemodelpdf) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-111">A good reference can be found at [The Release Pipeline Model](https://aka.ms/thereleasepipelinemodelpdf).</span></span>
- <span data-ttu-id="4ce9e-112">[Git](https://git-scm.com/) 原始檔控制</span><span class="sxs-lookup"><span data-stu-id="4ce9e-112">[Git](https://git-scm.com/) source control</span></span>
- <span data-ttu-id="4ce9e-113">[Pester](https://github.com/pester/Pester) 測試架構</span><span class="sxs-lookup"><span data-stu-id="4ce9e-113">The [Pester](https://github.com/pester/Pester) testing framework</span></span>
- [<span data-ttu-id="4ce9e-114">Team Foundation Server</span><span class="sxs-lookup"><span data-stu-id="4ce9e-114">Team Foundation Server</span></span>](https://visualstudio.microsoft.com/tfs/)

## <a name="what-you-will-need"></a><span data-ttu-id="4ce9e-115">您將需要</span><span class="sxs-lookup"><span data-stu-id="4ce9e-115">What you will need</span></span>

<span data-ttu-id="4ce9e-116">若要建置和執行此範例，您將需要一個有數台電腦和/或虛擬機器的環境。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-116">To build and run this example, you will need an environment with several computers and/or virtual machines.</span></span>

### <a name="client"></a><span data-ttu-id="4ce9e-117">Client</span><span class="sxs-lookup"><span data-stu-id="4ce9e-117">Client</span></span>

<span data-ttu-id="4ce9e-118">這是您將進行所有設定和執行範例之工作的電腦。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-118">This is the computer where you'll do all of the work setting up and running the example.</span></span>

<span data-ttu-id="4ce9e-119">用戶端電腦必須是已安裝下列各項的 Windows 電腦：</span><span class="sxs-lookup"><span data-stu-id="4ce9e-119">The client computer must be a Windows computer with the following installed:</span></span>

- [<span data-ttu-id="4ce9e-120">Git</span><span class="sxs-lookup"><span data-stu-id="4ce9e-120">Git</span></span>](https://git-scm.com/)
- <span data-ttu-id="4ce9e-121">從 https://github.com/PowerShell/Demo_CI 複製的本機 Git 儲存機制</span><span class="sxs-lookup"><span data-stu-id="4ce9e-121">a local git repo cloned from https://github.com/PowerShell/Demo_CI</span></span>
- <span data-ttu-id="4ce9e-122">文字編輯器，例如 [Visual Studio Code](https://code.visualstudio.com/)</span><span class="sxs-lookup"><span data-stu-id="4ce9e-122">a text editor, such as [Visual Studio Code](https://code.visualstudio.com/)</span></span>

### <a name="tfssrv1"></a><span data-ttu-id="4ce9e-123">TFSSrv1</span><span class="sxs-lookup"><span data-stu-id="4ce9e-123">TFSSrv1</span></span>

<span data-ttu-id="4ce9e-124">裝載 TFS 伺服器且您將定義組建和版本的電腦。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-124">The computer that hosts the TFS server where you will define your build and release.</span></span>
<span data-ttu-id="4ce9e-125">此電腦上必須安裝 [Team Foundation Server 2017](https://visualstudio.microsoft.com/tfs/)。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-125">This computer must have [Team Foundation Server 2017](https://visualstudio.microsoft.com/tfs/) installed.</span></span>

### <a name="buildagent"></a><span data-ttu-id="4ce9e-126">BuildAgent</span><span class="sxs-lookup"><span data-stu-id="4ce9e-126">BuildAgent</span></span>

<span data-ttu-id="4ce9e-127">執行建置專案之 Windows 組建代理程式的電腦。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-127">The computer that runs the Windows build agent that builds the project.</span></span>
<span data-ttu-id="4ce9e-128">此電腦上必須安裝及執行 Windows 組建代理程式。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-128">This computer must have a Windows build agent installed and running.</span></span>
<span data-ttu-id="4ce9e-129">如需有關如何安裝及執行 Windows 組建代理程式的指示，請參閱[在 Windows 上部署代理程式](/azure/devops/pipelines/agents/v2-windows) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-129">See [Deploy an agent on Windows](/azure/devops/pipelines/agents/v2-windows) for instructions on how to install and run a Windows build agent.</span></span>

<span data-ttu-id="4ce9e-130">您還必須在此電腦上安裝 `xDnsServer` 和 `xNetworking` DSC 模組。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-130">You also need to install both the `xDnsServer` and `xNetworking` DSC modules on this computer.</span></span>

### <a name="testagent1"></a><span data-ttu-id="4ce9e-131">TestAgent1</span><span class="sxs-lookup"><span data-stu-id="4ce9e-131">TestAgent1</span></span>

<span data-ttu-id="4ce9e-132">這是此範例中的 DSC 設定所設定為 DNS 伺服器的電腦。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-132">This is the computer that is configured as a DNS server by the DSC configuration in this example.</span></span>
<span data-ttu-id="4ce9e-133">此電腦必須執行 [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016)。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-133">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>

### <a name="testagent2"></a><span data-ttu-id="4ce9e-134">TestAgent2</span><span class="sxs-lookup"><span data-stu-id="4ce9e-134">TestAgent2</span></span>

<span data-ttu-id="4ce9e-135">這是裝載此範例所設定之網站的電腦。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-135">This is the computer that hosts the website this example configures.</span></span>
<span data-ttu-id="4ce9e-136">此電腦必須執行 [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016)。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-136">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>

## <a name="add-the-code-to-tfs"></a><span data-ttu-id="4ce9e-137">將程式碼新增至 TFS</span><span class="sxs-lookup"><span data-stu-id="4ce9e-137">Add the code to TFS</span></span>

<span data-ttu-id="4ce9e-138">我們一開始會在 TFS 中建立 Git 儲存機制，並從您在用戶端電腦上的本機儲存機制匯入程式碼。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-138">We'll start out by creating a Git repository in TFS, and importing the code from your local repository on the client computer.</span></span>
<span data-ttu-id="4ce9e-139">如果您尚未將 Demo_CI 儲存機制複製到您的用戶端電腦上，請立即執行下列 Git 命令來執行此操作：</span><span class="sxs-lookup"><span data-stu-id="4ce9e-139">If you have not already cloned the Demo_CI repository to your client computer, do so now by running the following git command:</span></span>

`git clone https://github.com/PowerShell/Demo_CI`

1. <span data-ttu-id="4ce9e-140">在您的用戶端電腦上，於網頁瀏覽器中瀏覽至您的 TFS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-140">On your client computer, navigate to your TFS server in a web browser.</span></span>
1. <span data-ttu-id="4ce9e-141">在 TFS 中，[建立一個新的小組專案](/azure/devops/organizations/projects/create-project)並命名為 Demo_CI。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-141">In TFS, [Create a new team project](/azure/devops/organizations/projects/create-project) named Demo_CI.</span></span>

   <span data-ttu-id="4ce9e-142">請確定將 [版本控制]  設定為 [Git]  。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-142">Make sure that **Version control** is set to **Git**.</span></span>
1. <span data-ttu-id="4ce9e-143">在您的用戶端電腦上，使用下列命令為您剛在 TFS 中建立的儲存機制新增遠端：</span><span class="sxs-lookup"><span data-stu-id="4ce9e-143">On your client computer, add a remote to the repository you just created in TFS with the following command:</span></span>

   `git remote add tfs <YourTFSRepoURL>`

   <span data-ttu-id="4ce9e-144">其中 `<YourTFSRepoURL>` 是您在上一個步驟中所建立之 TFS 儲存機制的複製 URL。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-144">Where `<YourTFSRepoURL>` is the clone URL to the TFS repository you created in the previous step.</span></span>

   <span data-ttu-id="4ce9e-145">如果您不知道哪裡可以找到此 URL，請參閱[複製現有的 Git 儲存機制](/azure/devops/repos/git/clone) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-145">If you don't know where to find this URL, see [Clone an existing Git repo](/azure/devops/repos/git/clone).</span></span>
1. <span data-ttu-id="4ce9e-146">使用下列命令將程式碼從您的本機儲存機制推送到 TFS 儲存機制：</span><span class="sxs-lookup"><span data-stu-id="4ce9e-146">Push the code from your local repository to your TFS repository with the following command:</span></span>

   `git push tfs --all`
1. <span data-ttu-id="4ce9e-147">將會在 TFS 儲存機制中填入 Demo_CI 程式碼。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-147">The TFS repository will be populated with the Demo_CI code.</span></span>

> [!NOTE]
> <span data-ttu-id="4ce9e-148">本範例使用 Git 存放庫之 `ci-cd-example` 分支中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-148">This example uses the code in the `ci-cd-example` branch of the Git repo.</span></span>
> <span data-ttu-id="4ce9e-149">請務必指定此分支作為您 TFS 專案中及您所建立之 CI/CD 觸發程序的預設分支。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-149">Be sure to specify this branch as the default branch in your TFS project, and for the CI/CD triggers you create.</span></span>

## <a name="understanding-the-code"></a><span data-ttu-id="4ce9e-150">了解程式碼</span><span class="sxs-lookup"><span data-stu-id="4ce9e-150">Understanding the code</span></span>

<span data-ttu-id="4ce9e-151">在建立這些組建與部署管線之前，讓我們先來看看部分程式碼以了解情況。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-151">Before we create the build and deployment pipelines, let's look at some of the code to understand what is going on.</span></span>
<span data-ttu-id="4ce9e-152">在您的用戶端電腦上，開啟您慣用的文字編輯器，然後瀏覽至 Demo_CI Git 儲存機制的根目錄。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-152">On your client computer, open your favorite text editor and navigate to the root of your Demo_CI Git repository.</span></span>

### <a name="the-dsc-configuration"></a><span data-ttu-id="4ce9e-153">DSC 設定</span><span class="sxs-lookup"><span data-stu-id="4ce9e-153">The DSC configuration</span></span>

<span data-ttu-id="4ce9e-154">開啟檔案 `DNSServer.ps1` (從本機 Demo_CI 儲存機制的根目錄路徑為 `./InfraDNS/Configs/DNSServer.ps1`)。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-154">Open the file `DNSServer.ps1` (from the root of the local Demo_CI repository, `./InfraDNS/Configs/DNSServer.ps1`).</span></span>

<span data-ttu-id="4ce9e-155">此檔案包含設定 DNS 伺服器的 DSC 設定。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-155">This file contains the DSC configuration that sets up the DNS server.</span></span> <span data-ttu-id="4ce9e-156">以下是其全部：</span><span class="sxs-lookup"><span data-stu-id="4ce9e-156">Here it is in its entirety:</span></span>

```powershell
configuration DNSServer
{
    Import-DscResource -module 'xDnsServer','xNetworking', 'PSDesiredStateConfiguration'

    Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
    {
        WindowsFeature DNS
        {
            Ensure  = 'Present'
            Name    = 'DNS'
        }

        xDnsServerPrimaryZone $Node.zone
        {
            Ensure    = 'Present'
            Name      = $Node.Zone
            DependsOn = '[WindowsFeature]DNS'
        }

        foreach ($ARec in $Node.ARecords.keys) {
            xDnsRecord $ARec
            {
                Ensure    = 'Present'
                Name      = $ARec
                Zone      = $Node.Zone
                Type      = 'ARecord'
                Target    = $Node.ARecords[$ARec]
                DependsOn = '[WindowsFeature]DNS'
            }
        }

        foreach ($CName in $Node.CNameRecords.keys) {
            xDnsRecord $CName
            {
                Ensure    = 'Present'
                Name      = $CName
                Zone      = $Node.Zone
                Type      = 'CName'
                Target    = $Node.CNameRecords[$CName]
                DependsOn = '[WindowsFeature]DNS'
            }
        }
    }
}
```

<span data-ttu-id="4ce9e-157">請注意 `Node` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="4ce9e-157">Notice the `Node` statement:</span></span>

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

<span data-ttu-id="4ce9e-158">這會尋找[設定資料](../configurations/configData.md) (由 `DevEnv.ps1` 指令碼所建立) 中所有已定義為具備 `DNSServer` 角色的節點。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-158">This finds any nodes that were defined as having a role of `DNSServer` in the [configuration data](../configurations/configData.md), which is created by the `DevEnv.ps1` script.</span></span>

<span data-ttu-id="4ce9e-159">您可以在 [about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays) 中深入閱讀 `Where` 方法</span><span class="sxs-lookup"><span data-stu-id="4ce9e-159">You can read more about the `Where` method in [about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays)</span></span>

<span data-ttu-id="4ce9e-160">進行 CI 時，使用設定資料來定義節點相當重要，因為節點資訊在環境之間可能會有所變更，而使用設定資料則可讓您不須變更設定程式碼，即可輕鬆對節點資訊進行變更。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-160">Using configuration data to define nodes is important when doing CI because node information will likely change between environments, and using configuration data allows you to easily make changes to node information without changing the configuration code.</span></span>

<span data-ttu-id="4ce9e-161">在第一個資源區塊中，此設定會呼叫 **WindowsFeature** 以確保啟用 DNS 功能。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-161">In the first resource block, the configuration calls the **WindowsFeature** to ensure that the DNS feature is enabled.</span></span>
<span data-ttu-id="4ce9e-162">接下來的資源區塊會從 [xDnsServer](https://github.com/PowerShell/xDnsServer) 模組呼叫資源，以設定主要區域和 DNS 記錄。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-162">The resource blocks that follow call resources from the [xDnsServer](https://github.com/PowerShell/xDnsServer) module to configure the primary zone and DNS records.</span></span>

<span data-ttu-id="4ce9e-163">請注意，兩個 `xDnsRecord` 區塊皆包裝在 `foreach` 迴圈中，這些迴圈會逐一查看設定資料中的陣列。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-163">Notice that the two `xDnsRecord` blocks are wrapped in `foreach` loops that iterate through arrays in the configuration data.</span></span>
<span data-ttu-id="4ce9e-164">此設定資料同樣也是 `DevEnv.ps1` 指令碼所建立的，接下來將會探討此設定資料。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-164">Again, the configuration data is created by the `DevEnv.ps1` script, which we'll look at next.</span></span>

### <a name="configuration-data"></a><span data-ttu-id="4ce9e-165">設定資料</span><span class="sxs-lookup"><span data-stu-id="4ce9e-165">Configuration data</span></span>

<span data-ttu-id="4ce9e-166">`DevEnv.ps1` 檔案 (從本機 Demo_CI 儲存機制的根目錄路徑為 `./InfraDNS/DevEnv.ps1`) 會在雜湊表中指定環境特定設定資料，然後將該雜湊表傳遞給對 `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`) 中定義之 `New-DscConfigurationDataDocument` 函式的呼叫。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-166">The `DevEnv.ps1` file (from the root of the local Demo_CI repository, `./InfraDNS/DevEnv.ps1`) specifies the environment-specific configuration data in a hashtable, and then passes that hashtable to a call to the `New-DscConfigurationDataDocument` function, which is defined in `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).</span></span>

<span data-ttu-id="4ce9e-167">`DevEnv.ps1` 檔案：</span><span class="sxs-lookup"><span data-stu-id="4ce9e-167">The `DevEnv.ps1` file:</span></span>

```powershell
param(
    [parameter(Mandatory=$true)]
    [string]
    $OutputPath
)

Import-Module $PSScriptRoot\..\Assets\DscPipelineTools\DscPipelineTools.psd1 -Force

# Define Unit Test Environment
$DevEnvironment = @{
    Name                        = 'DevEnv';
    Roles = @(
        @{  Role                = 'DNSServer';
            VMName              = 'TestAgent1';
            Zone                = 'Contoso.com';
            ARecords            = @{'TFSSrv1'= '10.0.0.10';'Client'='10.0.0.15';'BuildAgent'='10.0.0.30';'TestAgent1'='10.0.0.40';'TestAgent2'='10.0.0.50'};
            CNameRecords        = @{'DNS' = 'TestAgent1.contoso.com'};
        }
    )
}

Return New-DscConfigurationDataDocument -RawEnvData $DevEnvironment -OutputPath $OutputPath
```

<span data-ttu-id="4ce9e-168">`New-DscConfigurationDataDocument` 函式 (定義於 `\Assets\DscPipelineTools\DscPipelineTools.psm1`) 會以程式設計方式，從以 `RawEnvData` 和 `OtherEnvData` 參數的形式傳遞的雜湊表 (節點資料) 和陣列 (非節點資料) 建立設定資料文件。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-168">The `New-DscConfigurationDataDocument` function (defined in `\Assets\DscPipelineTools\DscPipelineTools.psm1`) programmatically creates a configuration data document from the hashtable (node data) and array (non-node data) that are passed as the `RawEnvData` and `OtherEnvData` parameters.</span></span>

<span data-ttu-id="4ce9e-169">在我們的案例中，只使用 `RawEnvData` 參數。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-169">In our case, only the `RawEnvData` parameter is used.</span></span>

### <a name="the-psake-build-script"></a><span data-ttu-id="4ce9e-170">psake 建置指令碼</span><span class="sxs-lookup"><span data-stu-id="4ce9e-170">The psake build script</span></span>

<span data-ttu-id="4ce9e-171">`Build.ps1` (從 Demo_CI 儲存機制的根目錄路徑為 `./InfraDNS/Build.ps1`) 中定義的 [psake](https://github.com/psake/psake) 建置指令碼會定義組建所含的工作。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-171">The [psake](https://github.com/psake/psake) build script defined in `Build.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Build.ps1`) defines tasks that are part of the build.</span></span>
<span data-ttu-id="4ce9e-172">它也定義每個工作所依存的其他工作。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-172">It also defines which other tasks each task depends on.</span></span>
<span data-ttu-id="4ce9e-173">當叫用 psake 指令碼時，它會確保指定的工作 (如果未指定任何工作，則是名為 `Default` 的工作) 執行，並且所有相依項目也一併執行 (這是遞迴的，因此相依項目的相依項目也會執行，依此類推)。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-173">When invoked, the psake script ensures that the specified task (or the task named `Default` if none is specified) runs, and that all dependencies also run (this is recursive, so that dependencies of dependencies run, and so on).</span></span>

<span data-ttu-id="4ce9e-174">在此範例中，`Default` 是定義為：</span><span class="sxs-lookup"><span data-stu-id="4ce9e-174">In this example, the `Default` task is defined as:</span></span>

```powershell
Task Default -depends UnitTests
```

<span data-ttu-id="4ce9e-175">`Default` 工作本身沒有任何實作，但依存於 `CompileConfigs` 工作。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-175">The `Default` task has no implementation itself, but has a dependency on the `CompileConfigs` task.</span></span>
<span data-ttu-id="4ce9e-176">產生的工作相依性鏈結會確保執行建置指令碼中的所有工作。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-176">The resulting chain of task dependencies ensures that all tasks in the build script are run.</span></span>

<span data-ttu-id="4ce9e-177">在此範例中，是透過呼叫 `Initiate.ps1` 檔案 (位於 Demo_CI 儲存機制的根目錄) 中的 `Invoke-PSake` 來叫用 psake 指令碼：</span><span class="sxs-lookup"><span data-stu-id="4ce9e-177">In this example, the psake script is invoked by a call to `Invoke-PSake` in the `Initiate.ps1` file (located at the root of the Demo_CI repository):</span></span>

```powershell
param(
    [parameter()]
    [ValidateSet('Build','Deploy')]
    [string]
    $fileName
)

#$Error.Clear()

Invoke-PSake $PSScriptRoot\InfraDNS\$fileName.ps1

<#if($Error.count)
{
    Throw "$fileName script failed. Check logs for failure details."
}
#>
```

<span data-ttu-id="4ce9e-178">當我們在 TFS 中為範例建立組建定義時，將會提供 psake 指令碼檔作為此指令碼的 `fileName` 參數。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-178">When we create the build definition for our example in TFS, we will supply our psake script file as the `fileName` parameter for this script.</span></span>

<span data-ttu-id="4ce9e-179">建置指令碼會定義下列工作：</span><span class="sxs-lookup"><span data-stu-id="4ce9e-179">The build script defines the following tasks:</span></span>

#### <a name="generateenvironmentfiles"></a><span data-ttu-id="4ce9e-180">GenerateEnvironmentFiles</span><span class="sxs-lookup"><span data-stu-id="4ce9e-180">GenerateEnvironmentFiles</span></span>

<span data-ttu-id="4ce9e-181">會執行 `DevEnv.ps1` 以產生設定資料檔。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-181">Runs `DevEnv.ps1`, which generates the configuration data file.</span></span>

#### <a name="installmodules"></a><span data-ttu-id="4ce9e-182">InstallModules</span><span class="sxs-lookup"><span data-stu-id="4ce9e-182">InstallModules</span></span>

<span data-ttu-id="4ce9e-183">會安裝設定 `DNSServer.ps1` 所需的模組。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-183">Installs the modules required by the configuration `DNSServer.ps1`.</span></span>

#### <a name="scriptanalysis"></a><span data-ttu-id="4ce9e-184">ScriptAnalysis</span><span class="sxs-lookup"><span data-stu-id="4ce9e-184">ScriptAnalysis</span></span>

<span data-ttu-id="4ce9e-185">會呼叫 [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer)。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-185">Calls the [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).</span></span>

#### <a name="unittests"></a><span data-ttu-id="4ce9e-186">UnitTests</span><span class="sxs-lookup"><span data-stu-id="4ce9e-186">UnitTests</span></span>

<span data-ttu-id="4ce9e-187">會執行 [Pester](https://github.com/pester/Pester/wiki) 單元測試。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-187">Runs the [Pester](https://github.com/pester/Pester/wiki) unit tests.</span></span>

#### <a name="compileconfigs"></a><span data-ttu-id="4ce9e-188">CompileConfigs</span><span class="sxs-lookup"><span data-stu-id="4ce9e-188">CompileConfigs</span></span>

<span data-ttu-id="4ce9e-189">會使用 `GenerateEnvironmentFiles` 工作所產生的設定資料，將設定 (`DNSServer.ps1`) 編譯成 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-189">Compiles the configuration (`DNSServer.ps1`) into a MOF file, using the configuration data generated by the `GenerateEnvironmentFiles` task.</span></span>

#### <a name="clean"></a><span data-ttu-id="4ce9e-190">Clean</span><span class="sxs-lookup"><span data-stu-id="4ce9e-190">Clean</span></span>

<span data-ttu-id="4ce9e-191">會建立用於範例的資料夾，並移除來自先前回合的所有測試結果、設定資料檔及模組。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-191">Creates the folders used for the example, and removes any test results, configuration data files, and modules from previous runs.</span></span>

### <a name="the-psake-deploy-script"></a><span data-ttu-id="4ce9e-192">psake 部署指令碼</span><span class="sxs-lookup"><span data-stu-id="4ce9e-192">The psake deploy script</span></span>

<span data-ttu-id="4ce9e-193">`Deploy.ps1` (從 Demo_CI 儲存機制的根目錄路徑為 `./InfraDNS/Deploy.ps1`) 中定義的 [psake](https://github.com/psake/psake) 部署指令碼會定義部署和執行設定的工作。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-193">The [psake](https://github.com/psake/psake) deployment script defined in `Deploy.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Deploy.ps1`) defines tasks that deploy and run the configuration.</span></span>

<span data-ttu-id="4ce9e-194">`Deploy.ps1` 會定義下列工作：</span><span class="sxs-lookup"><span data-stu-id="4ce9e-194">`Deploy.ps1` defines the following tasks:</span></span>

#### <a name="deploymodules"></a><span data-ttu-id="4ce9e-195">DeployModules</span><span class="sxs-lookup"><span data-stu-id="4ce9e-195">DeployModules</span></span>

<span data-ttu-id="4ce9e-196">會在 `TestAgent1` 上啟動 PowerShell 工作階段，並安裝包含設定所需 DSC 資源的模組。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-196">Starts a PowerShell session on `TestAgent1` and installs the modules containing the DSC resources required for the configuration.</span></span>

#### <a name="deployconfigs"></a><span data-ttu-id="4ce9e-197">DeployConfigs</span><span class="sxs-lookup"><span data-stu-id="4ce9e-197">DeployConfigs</span></span>

<span data-ttu-id="4ce9e-198">會呼叫 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) Cmdlet 以在 `TestAgent1` 上執行設定。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-198">Calls the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet to run the configuration on `TestAgent1`.</span></span>

#### <a name="integrationtests"></a><span data-ttu-id="4ce9e-199">IntegrationTests</span><span class="sxs-lookup"><span data-stu-id="4ce9e-199">IntegrationTests</span></span>

<span data-ttu-id="4ce9e-200">會執行 [Pester](https://github.com/pester/Pester/wiki) 整合測試。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-200">Runs the [Pester](https://github.com/pester/Pester/wiki) integration tests.</span></span>

#### <a name="acceptancetests"></a><span data-ttu-id="4ce9e-201">AcceptanceTests</span><span class="sxs-lookup"><span data-stu-id="4ce9e-201">AcceptanceTests</span></span>

<span data-ttu-id="4ce9e-202">會執行 [Pester](https://github.com/pester/Pester/wiki) 接受度測試。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-202">Runs the [Pester](https://github.com/pester/Pester/wiki) acceptance tests.</span></span>

#### <a name="clean"></a><span data-ttu-id="4ce9e-203">Clean</span><span class="sxs-lookup"><span data-stu-id="4ce9e-203">Clean</span></span>

<span data-ttu-id="4ce9e-204">會移除在先前回合中安裝的所有模組，並確保測試結果資料夾存在。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-204">Removes any modules installed in previous runs, and ensures that the test result folder exists.</span></span>

### <a name="test-scripts"></a><span data-ttu-id="4ce9e-205">測試指令碼</span><span class="sxs-lookup"><span data-stu-id="4ce9e-205">Test scripts</span></span>

<span data-ttu-id="4ce9e-206">接受度、整合及單元測試是在 `Tests` 資料夾 (從 Demo_CI 儲存機制的根目錄路徑為 `./InfraDNS/Tests`) 內的指令碼中定義的，各分別在其個別資料夾內名為 `DNSServer.tests.ps1` 的檔案中。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-206">Acceptance, Integration, and Unit tests are defined in scripts in the `Tests` folder (from the root of the Demo_CI repository, `./InfraDNS/Tests`), each in files named `DNSServer.tests.ps1` in their respective folders.</span></span>

<span data-ttu-id="4ce9e-207">測試指令碼會使用 [Pester](https://github.com/pester/Pester/wiki) 和 [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) 語法。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-207">The test scripts use [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="unit-tests"></a><span data-ttu-id="4ce9e-208">單元測試</span><span class="sxs-lookup"><span data-stu-id="4ce9e-208">Unit tests</span></span>

<span data-ttu-id="4ce9e-209">單元測試會測試 DSC 設定本身，以確保設定在執行時會執行預期執行的工作。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-209">The unit tests test the DSC configurations themselves to ensure that the configurations will do what is expected when they run.</span></span>
<span data-ttu-id="4ce9e-210">單元測試指令碼會使用 [Pester](https://github.com/pester/Pester/wiki)。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-210">The unit test script uses [Pester](https://github.com/pester/Pester/wiki).</span></span>

#### <a name="integration-tests"></a><span data-ttu-id="4ce9e-211">整合測試</span><span class="sxs-lookup"><span data-stu-id="4ce9e-211">Integration tests</span></span>

<span data-ttu-id="4ce9e-212">整合測試會測試系統的設定，以確保當與其他元件整合時，會依照預期的方式設定系統。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-212">The integration tests test the configuration of the system to ensure that when integrated with other components, the system is configured as expected.</span></span> <span data-ttu-id="4ce9e-213">使用 DSC 來設定這些測試之後，這些測試就會在目標節點上執行。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-213">These tests run on the target node after it has been configured with DSC.</span></span>
<span data-ttu-id="4ce9e-214">整合測試指令碼會混合使用 [Pester](https://github.com/pester/Pester/wiki) 和 [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) 語法。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-214">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="acceptance-tests"></a><span data-ttu-id="4ce9e-215">接受度測試</span><span class="sxs-lookup"><span data-stu-id="4ce9e-215">Acceptance tests</span></span>

<span data-ttu-id="4ce9e-216">接受度測試會測試系統，以確保系統依照預期的方式運作。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-216">Acceptance tests test the system to ensure that it behaves as expected.</span></span>
<span data-ttu-id="4ce9e-217">例如，它會測試來確保在查詢時，網頁會傳回正確的資訊。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-217">For example, it tests to ensure a web page returns the right information when queried.</span></span>
<span data-ttu-id="4ce9e-218">這些測試會從目標節點的遠端執行，以測試真實世界案例。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-218">These tests run remotely from the target node in order to test real world scenarios.</span></span>
<span data-ttu-id="4ce9e-219">整合測試指令碼會混合使用 [Pester](https://github.com/pester/Pester/wiki) 和 [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) 語法。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-219">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

## <a name="define-the-build"></a><span data-ttu-id="4ce9e-220">定義組建</span><span class="sxs-lookup"><span data-stu-id="4ce9e-220">Define the build</span></span>

<span data-ttu-id="4ce9e-221">既然我們已將程式碼上傳到 TFS 並查看其功能，現在即可開始定義組建。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-221">Now that we've uploaded our code to TFS and looked at what it does, let's define our build.</span></span>

<span data-ttu-id="4ce9e-222">在這裡，我們將只涵蓋您將新增到組建中的建置步驟。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-222">Here, we'll cover only the build steps that you'll add to the build.</span></span> <span data-ttu-id="4ce9e-223">如需有關如何在 TFS 中建立組建定義的指示，請參閱[建立組建定義並將其排入佇列](/azure/devops/pipelines/create-first-pipeline) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-223">For instructions on how to create a build definition in TFS, see [Create and queue a build definition](/azure/devops/pipelines/create-first-pipeline).</span></span>

<span data-ttu-id="4ce9e-224">請建立一個名為 "InfraDNS" 的新組建定義 (選取 [空白]  範本)。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-224">Create a new build definition (select the **Empty** template) named "InfraDNS".</span></span>
<span data-ttu-id="4ce9e-225">將下列步驟新增到您的組建定義中：</span><span class="sxs-lookup"><span data-stu-id="4ce9e-225">Add the following steps to you build definition:</span></span>

- <span data-ttu-id="4ce9e-226">PowerShell 指令碼</span><span class="sxs-lookup"><span data-stu-id="4ce9e-226">PowerShell Script</span></span>
- <span data-ttu-id="4ce9e-227">發行測試結果</span><span class="sxs-lookup"><span data-stu-id="4ce9e-227">Publish Test Results</span></span>
- <span data-ttu-id="4ce9e-228">複製檔案</span><span class="sxs-lookup"><span data-stu-id="4ce9e-228">Copy Files</span></span>
- <span data-ttu-id="4ce9e-229">發行成品</span><span class="sxs-lookup"><span data-stu-id="4ce9e-229">Publish Artifact</span></span>

<span data-ttu-id="4ce9e-230">新增這些建置步驟之後，請依下列方式編輯每個步驟的屬性：</span><span class="sxs-lookup"><span data-stu-id="4ce9e-230">After adding these build steps, edit the properties of each step as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="4ce9e-231">PowerShell 指令碼</span><span class="sxs-lookup"><span data-stu-id="4ce9e-231">PowerShell Script</span></span>

1. <span data-ttu-id="4ce9e-232">將 [類型]  屬性設定為 `File Path`。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-232">Set the **Type** property to `File Path`.</span></span>
1. <span data-ttu-id="4ce9e-233">將 [指令碼路徑]  屬性設定為 `initiate.ps1`。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-233">Set the **Script Path** property to `initiate.ps1`.</span></span>
1. <span data-ttu-id="4ce9e-234">將 `-fileName build` 新增到 [引數]  屬性。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-234">Add `-fileName build` to the **Arguments** property.</span></span>

<span data-ttu-id="4ce9e-235">此建置步驟會執行 `initiate.ps1` 檔案以呼叫 psake 建置指令碼。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-235">This build step runs the `initiate.ps1` file, which calls the psake build script.</span></span>

### <a name="publish-test-results"></a><span data-ttu-id="4ce9e-236">發行測試結果</span><span class="sxs-lookup"><span data-stu-id="4ce9e-236">Publish Test Results</span></span>

1. <span data-ttu-id="4ce9e-237">將 [測試結果格式]  設定為 `NUnit`</span><span class="sxs-lookup"><span data-stu-id="4ce9e-237">Set **Test Result Format** to `NUnit`</span></span>
1. <span data-ttu-id="4ce9e-238">將 [測試結果檔案]  設定為 `InfraDNS/Tests/Results/*.xml`</span><span class="sxs-lookup"><span data-stu-id="4ce9e-238">Set **Test Results Files** to `InfraDNS/Tests/Results/*.xml`</span></span>
1. <span data-ttu-id="4ce9e-239">將 [測試回合標題]  設定為 `Unit`。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-239">Set **Test Run Title** to `Unit`.</span></span>
1. <span data-ttu-id="4ce9e-240">確定已選取 [啟用]  和 [永遠執行]  這兩個 [控制選項]  。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-240">Make sure **Control Options** **Enabled** and **Always run** are both selected.</span></span>

<span data-ttu-id="4ce9e-241">此建置步驟會執行我們先前查看之 Pester 指令碼中的單元測試，然後將結果儲存在 `InfraDNS/Tests/Results/*.xml` 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-241">This build step runs the unit tests in the Pester script we looked at earlier, and stores the results in the `InfraDNS/Tests/Results/*.xml` folder.</span></span>

### <a name="copy-files"></a><span data-ttu-id="4ce9e-242">複製檔案</span><span class="sxs-lookup"><span data-stu-id="4ce9e-242">Copy Files</span></span>

1. <span data-ttu-id="4ce9e-243">將下列每一行新增到 [內容]  中：</span><span class="sxs-lookup"><span data-stu-id="4ce9e-243">Add each of the following lines to **Contents**:</span></span>

   ```
   initiate.ps1
   **\deploy.ps1
   **\Acceptance\**
   **\Integration\**
   ```

1. <span data-ttu-id="4ce9e-244">將 [目標資料夾]  設定為 `$(Build.ArtifactStagingDirectory)\`</span><span class="sxs-lookup"><span data-stu-id="4ce9e-244">Set **TargetFolder** to `$(Build.ArtifactStagingDirectory)\`</span></span>

<span data-ttu-id="4ce9e-245">此步驟會將建置和測試指令碼複製到暫存目錄中，以便供下一個步驟發行成組建成品。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-245">This step copies the build and test scripts to the staging directory so that the can be published as build artifacts by the next step.</span></span>

### <a name="publish-artifact"></a><span data-ttu-id="4ce9e-246">發行成品</span><span class="sxs-lookup"><span data-stu-id="4ce9e-246">Publish Artifact</span></span>

1. <span data-ttu-id="4ce9e-247">將 [要發行的路徑]  設定為 `$(Build.ArtifactStagingDirectory)\`</span><span class="sxs-lookup"><span data-stu-id="4ce9e-247">Set **Path to Publish** to `$(Build.ArtifactStagingDirectory)\`</span></span>
1. <span data-ttu-id="4ce9e-248">將 [成品名稱]  設定為 `Deploy`</span><span class="sxs-lookup"><span data-stu-id="4ce9e-248">Set **Artifact Name** to `Deploy`</span></span>
1. <span data-ttu-id="4ce9e-249">將 [成品類型]  設定為 `Server`</span><span class="sxs-lookup"><span data-stu-id="4ce9e-249">Set **Artifact Type** to `Server`</span></span>
1. <span data-ttu-id="4ce9e-250">在 [控制選項]  中選取 [`Enabled`]</span><span class="sxs-lookup"><span data-stu-id="4ce9e-250">Select `Enabled` in **Control Options**</span></span>

## <a name="enable-continuous-integration"></a><span data-ttu-id="4ce9e-251">啟用持續整合</span><span class="sxs-lookup"><span data-stu-id="4ce9e-251">Enable continuous integration</span></span>

<span data-ttu-id="4ce9e-252">現在我們將設定一個觸發程序，此觸發程序會在每當有任何變更簽入 Git 儲存機制的 `ci-cd-example` 分支中時，便促使專案進行建置。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-252">Now we'll set up a trigger that causes the project to build any time a change is checked in to the `ci-cd-example` branch of the git repository.</span></span>

1. <span data-ttu-id="4ce9e-253">在 TFS 中，按一下 [建置及發行]  索引標籤</span><span class="sxs-lookup"><span data-stu-id="4ce9e-253">In TFS, click the **Build & Release** tab</span></span>
1. <span data-ttu-id="4ce9e-254">選取 `DNS Infra` 組建定義，然後按一下 [編輯] </span><span class="sxs-lookup"><span data-stu-id="4ce9e-254">Select the `DNS Infra` build definition, and click **Edit**</span></span>
1. <span data-ttu-id="4ce9e-255">按一下 [觸發程序]  索引標籤</span><span class="sxs-lookup"><span data-stu-id="4ce9e-255">Click the **Triggers** tab</span></span>
1. <span data-ttu-id="4ce9e-256">選取 [持續整合 (CI)]  ，然後從分支下拉式清單中選取 `refs/heads/ci-cd-example`</span><span class="sxs-lookup"><span data-stu-id="4ce9e-256">Select **Continuous integration (CI)**, and select `refs/heads/ci-cd-example` in the branch drop-down list</span></span>
1. <span data-ttu-id="4ce9e-257">按一下 [儲存]  ，然後按一下 [確定] </span><span class="sxs-lookup"><span data-stu-id="4ce9e-257">Click **Save** and then **OK**</span></span>

<span data-ttu-id="4ce9e-258">現在 TFS Git 儲存機制中的任何變更都會觸發自動化建置。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-258">Now any change in the TFS git repository triggers an automated build.</span></span>

## <a name="create-the-release-definition"></a><span data-ttu-id="4ce9e-259">建立發行定義</span><span class="sxs-lookup"><span data-stu-id="4ce9e-259">Create the release definition</span></span>

<span data-ttu-id="4ce9e-260">讓我們來建立一個發行定義，以便在每次簽入程式碼時，都將專案部署到開發環境。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-260">Let's create a release definition so that the project is deployed to the development environment with every code check-in.</span></span>

<span data-ttu-id="4ce9e-261">若要這樣做，請新增一個與您先前建立之 `InfraDNS` 組建定義關聯的新發行定義。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-261">To do this, add a new release definition associated with the `InfraDNS` build definition you created previously.</span></span>
<span data-ttu-id="4ce9e-262">請務必選取 [持續部署]  ，以便在每次完成新組建時便觸發新的發行。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-262">Be sure to select **Continuous deployment** so that a new release will be triggered any time a new build is completed.</span></span>
<span data-ttu-id="4ce9e-263">([什麼是發行管線？](/azure/devops/pipelines/release/))，並設定它，如下所示：</span><span class="sxs-lookup"><span data-stu-id="4ce9e-263">([What are release pipelines?](/azure/devops/pipelines/release/)) and configure it as follows:</span></span>

<span data-ttu-id="4ce9e-264">將下列步驟新增到發行定義中：</span><span class="sxs-lookup"><span data-stu-id="4ce9e-264">Add the following steps to the release definition:</span></span>

- <span data-ttu-id="4ce9e-265">PowerShell 指令碼</span><span class="sxs-lookup"><span data-stu-id="4ce9e-265">PowerShell Script</span></span>
- <span data-ttu-id="4ce9e-266">發行測試結果</span><span class="sxs-lookup"><span data-stu-id="4ce9e-266">Publish Test Results</span></span>
- <span data-ttu-id="4ce9e-267">發行測試結果</span><span class="sxs-lookup"><span data-stu-id="4ce9e-267">Publish Test Results</span></span>

<span data-ttu-id="4ce9e-268">依下列方式編輯步驟：</span><span class="sxs-lookup"><span data-stu-id="4ce9e-268">Edit the steps as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="4ce9e-269">PowerShell 指令碼</span><span class="sxs-lookup"><span data-stu-id="4ce9e-269">PowerShell Script</span></span>

1. <span data-ttu-id="4ce9e-270">將 [指令碼路徑]  欄位設定為 `$(Build.DefinitionName)\Deploy\initiate.ps1"`</span><span class="sxs-lookup"><span data-stu-id="4ce9e-270">Set the **Script Path** field to `$(Build.DefinitionName)\Deploy\initiate.ps1"`</span></span>
1. <span data-ttu-id="4ce9e-271">將 [引數]  欄位設定為 `-fileName Deploy`</span><span class="sxs-lookup"><span data-stu-id="4ce9e-271">Set the **Arguments** field to `-fileName Deploy`</span></span>

### <a name="first-publish-test-results"></a><span data-ttu-id="4ce9e-272">第一個發行測試結果</span><span class="sxs-lookup"><span data-stu-id="4ce9e-272">First Publish Test Results</span></span>

1. <span data-ttu-id="4ce9e-273">為 [測試結果格式]  欄位選取 [`NUnit`]</span><span class="sxs-lookup"><span data-stu-id="4ce9e-273">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="4ce9e-274">將 [測試結果檔案]  欄位設定為 `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span><span class="sxs-lookup"><span data-stu-id="4ce9e-274">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span></span>
1. <span data-ttu-id="4ce9e-275">將 [測試回合標題]  設定為 `Integration`</span><span class="sxs-lookup"><span data-stu-id="4ce9e-275">Set the **Test Run Title** to `Integration`</span></span>
1. <span data-ttu-id="4ce9e-276">在 [控制選項]  底下，選取 [永遠執行] </span><span class="sxs-lookup"><span data-stu-id="4ce9e-276">Under **Control Options**, check **Always run**</span></span>

### <a name="second-publish-test-results"></a><span data-ttu-id="4ce9e-277">第二個發行測試結果</span><span class="sxs-lookup"><span data-stu-id="4ce9e-277">Second Publish Test Results</span></span>

1. <span data-ttu-id="4ce9e-278">為 [測試結果格式]  欄位選取 [`NUnit`]</span><span class="sxs-lookup"><span data-stu-id="4ce9e-278">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="4ce9e-279">將 [測試結果檔案]  欄位設定為 `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span><span class="sxs-lookup"><span data-stu-id="4ce9e-279">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span></span>
1. <span data-ttu-id="4ce9e-280">將 [測試回合標題]  設定為 `Acceptance`</span><span class="sxs-lookup"><span data-stu-id="4ce9e-280">Set the **Test Run Title** to `Acceptance`</span></span>
1. <span data-ttu-id="4ce9e-281">在 [控制選項]  底下，選取 [永遠執行] </span><span class="sxs-lookup"><span data-stu-id="4ce9e-281">Under **Control Options**, check **Always run**</span></span>

## <a name="verify-your-results"></a><span data-ttu-id="4ce9e-282">驗證您的結果</span><span class="sxs-lookup"><span data-stu-id="4ce9e-282">Verify your results</span></span>

<span data-ttu-id="4ce9e-283">現在，每當您將 `ci-cd-example` 分支中的變更推送到 TFS 時，就會開始一個新的組建。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-283">Now, any time you push changes in the `ci-cd-example` branch to TFS, a new build will start.</span></span>
<span data-ttu-id="4ce9e-284">如果組建順利完成，就會觸發新的部署。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-284">If the build completes successfully, a new deployment is triggered.</span></span>

<span data-ttu-id="4ce9e-285">您可以在用戶端電腦上開啟瀏覽器並瀏覽至 `www.contoso.com`，來檢查部署結果。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-285">You can check the result of the deployment by opening a browser on the client machine and navigating to `www.contoso.com`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4ce9e-286">接下來的步驟</span><span class="sxs-lookup"><span data-stu-id="4ce9e-286">Next steps</span></span>

<span data-ttu-id="4ce9e-287">此範例會設定 DNS 伺服器 `TestAgent1`，讓 URL `www.contoso.com` 解析成 `TestAgent2`，但它並不會實際部署網站。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-287">This example configures the DNS server `TestAgent1` so that the URL `www.contoso.com` resolves to `TestAgent2`, but it does not actually deploy a website.</span></span>
<span data-ttu-id="4ce9e-288">儲存機制的 `WebApp` 資料夾底下有提供此做法的基本架構。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-288">The skeleton for doing so is provided in the repo under the `WebApp` folder.</span></span>
<span data-ttu-id="4ce9e-289">您可以使用提供的 Stub 來建立 psake 指令碼、Pester 測試及 DSC 設定，以部署您自己的網站。</span><span class="sxs-lookup"><span data-stu-id="4ce9e-289">You can use the stubs provided to create psake scripts, Pester tests, and DSC configurations to deploy your own website.</span></span>
