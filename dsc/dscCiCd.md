---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 使用 DSC 來建置持續整合和持續部署管線
ms.openlocfilehash: ce0f2ed79f5f96a1c38e0beaf32529aba7538963
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190548"
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a><span data-ttu-id="a2310-103">使用 DSC 來建置持續整合和持續部署管線</span><span class="sxs-lookup"><span data-stu-id="a2310-103">Building a Continuous Integration and Continuous Deployment pipeline with DSC</span></span>

<span data-ttu-id="a2310-104">此範例示範如何使用 PowerShell、DSC、Pester 及 Visual Studio Team Foundation Server (TFS) 來建置「持續整合/持續部署」(CI/CD) 管線。</span><span class="sxs-lookup"><span data-stu-id="a2310-104">This example demonstrates how to build a Continuous Integration/Continuous Deployment (CI/CD) pipeline by using PowerShell, DSC, Pester, and Visual Studio Team Foundation Server (TFS).</span></span>

<span data-ttu-id="a2310-105">建置並設定管線之後，您便可以使用它來完整部署、設定及測試 DNS 伺服器和相關的主機記錄。</span><span class="sxs-lookup"><span data-stu-id="a2310-105">After the pipeline is built and configured, you can use it to fully deploy, configure and test a DNS server and associated host records.</span></span>
<span data-ttu-id="a2310-106">此程序會模擬將在開發環境中使用之管線的第一個部分。</span><span class="sxs-lookup"><span data-stu-id="a2310-106">This process simulates the first part of a pipeline that would be used in a development environment.</span></span>

<span data-ttu-id="a2310-107">自動化的 CI/CD 管線可協助您以更快且更可靠的方式更新軟體，確保所有程式碼都經過測試，並且您程式碼的最新組建隨時可供使用。</span><span class="sxs-lookup"><span data-stu-id="a2310-107">An automated CI/CD pipeline helps you update software faster and more reliably, ensuring that all code is tested, and that a current build of your code is available at all times.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a2310-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="a2310-108">Prerequisites</span></span>

<span data-ttu-id="a2310-109">若要使用此範例，您應該熟悉下列各項知識：</span><span class="sxs-lookup"><span data-stu-id="a2310-109">To use this example, you should be familiar with the following:</span></span>

- <span data-ttu-id="a2310-110">CI-CD 概念。</span><span class="sxs-lookup"><span data-stu-id="a2310-110">CI-CD concepts.</span></span> <span data-ttu-id="a2310-111">如需詳細的參考資料，請參閱[發行管線模型](http://aka.ms/thereleasepipelinemodelpdf) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="a2310-111">A good reference can be found at [The Release Pipeline Model](http://aka.ms/thereleasepipelinemodelpdf).</span></span>
- <span data-ttu-id="a2310-112">[Git](https://git-scm.com/) 原始檔控制</span><span class="sxs-lookup"><span data-stu-id="a2310-112">[Git](https://git-scm.com/) source control</span></span>
- <span data-ttu-id="a2310-113">[Pester](https://github.com/pester/Pester) 測試架構</span><span class="sxs-lookup"><span data-stu-id="a2310-113">The [Pester](https://github.com/pester/Pester) testing framework</span></span>
- [<span data-ttu-id="a2310-114">Team Foundation Server</span><span class="sxs-lookup"><span data-stu-id="a2310-114">Team Foundation Server</span></span>](https://www.visualstudio.com/tfs/)

## <a name="what-you-will-need"></a><span data-ttu-id="a2310-115">您將需要</span><span class="sxs-lookup"><span data-stu-id="a2310-115">What you will need</span></span>

<span data-ttu-id="a2310-116">若要建置和執行此範例，您將需要一個有數台電腦和/或虛擬機器的環境。</span><span class="sxs-lookup"><span data-stu-id="a2310-116">To build and run this example, you will need an environment with several computers and/or virtual machines.</span></span>

### <a name="client"></a><span data-ttu-id="a2310-117">Client</span><span class="sxs-lookup"><span data-stu-id="a2310-117">Client</span></span>

<span data-ttu-id="a2310-118">這是您將進行所有設定和執行範例之工作的電腦。</span><span class="sxs-lookup"><span data-stu-id="a2310-118">This is the computer where you'll do all of the work setting up and running the example.</span></span>

<span data-ttu-id="a2310-119">用戶端電腦必須是已安裝下列各項的 Windows 電腦：</span><span class="sxs-lookup"><span data-stu-id="a2310-119">The client computer must be a Windows computer with the following installed:</span></span>
- [<span data-ttu-id="a2310-120">Git</span><span class="sxs-lookup"><span data-stu-id="a2310-120">Git</span></span>](https://git-scm.com/)
- <span data-ttu-id="a2310-121">從 https://github.com/PowerShell/Demo_CI 複製的本機 Git 儲存機制</span><span class="sxs-lookup"><span data-stu-id="a2310-121">a local git repo cloned from https://github.com/PowerShell/Demo_CI</span></span>
- <span data-ttu-id="a2310-122">文字編輯器，例如 [Visual Studio Code](https://code.visualstudio.com/)</span><span class="sxs-lookup"><span data-stu-id="a2310-122">a text editor, such as [Visual Studio Code](https://code.visualstudio.com/)</span></span>

### <a name="tfssrv1"></a><span data-ttu-id="a2310-123">TFSSrv1</span><span class="sxs-lookup"><span data-stu-id="a2310-123">TFSSrv1</span></span>

<span data-ttu-id="a2310-124">裝載 TFS 伺服器且您將定義組建和版本的電腦。</span><span class="sxs-lookup"><span data-stu-id="a2310-124">The computer that hosts the TFS server where you will define your build and release.</span></span>
<span data-ttu-id="a2310-125">此電腦上必須安裝 [Team Foundation Server 2017](https://www.visualstudio.com/tfs/)。</span><span class="sxs-lookup"><span data-stu-id="a2310-125">This computer must have [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) installed.</span></span>

### <a name="buildagent"></a><span data-ttu-id="a2310-126">BuildAgent</span><span class="sxs-lookup"><span data-stu-id="a2310-126">BuildAgent</span></span>

<span data-ttu-id="a2310-127">執行建置專案之 Windows 組建代理程式的電腦。</span><span class="sxs-lookup"><span data-stu-id="a2310-127">The computer that runs the Windows build agent that builds the project.</span></span>
<span data-ttu-id="a2310-128">此電腦上必須安裝及執行 Windows 組建代理程式。</span><span class="sxs-lookup"><span data-stu-id="a2310-128">This computer must have a Windows build agent installed and running.</span></span>
<span data-ttu-id="a2310-129">如需有關如何安裝及執行 Windows 組建代理程式的指示，請參閱[在 Windows 上部署代理程式](https://www.visualstudio.com/en-us/docs/build/actions/agents/v2-windows) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="a2310-129">See [Deploy an agent on Windows](https://www.visualstudio.com/en-us/docs/build/actions/agents/v2-windows) for instructions on how to install and run a Windows build agent.</span></span>

<span data-ttu-id="a2310-130">您還必須在此電腦上安裝 `xDnsServer` 和 `xNetworking` DSC 模組。</span><span class="sxs-lookup"><span data-stu-id="a2310-130">You also need to install both the `xDnsServer` and `xNetworking` DSC modules on this computer.</span></span>

### <a name="testagent1"></a><span data-ttu-id="a2310-131">TestAgent1</span><span class="sxs-lookup"><span data-stu-id="a2310-131">TestAgent1</span></span>

<span data-ttu-id="a2310-132">這是此範例中的 DSC 設定所設定為 DNS 伺服器的電腦。</span><span class="sxs-lookup"><span data-stu-id="a2310-132">This is the computer that is configured as a DNS server by the DSC configuration in this example.</span></span>
<span data-ttu-id="a2310-133">此電腦必須執行 [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016)。</span><span class="sxs-lookup"><span data-stu-id="a2310-133">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>

### <a name="testagent2"></a><span data-ttu-id="a2310-134">TestAgent2</span><span class="sxs-lookup"><span data-stu-id="a2310-134">TestAgent2</span></span>

<span data-ttu-id="a2310-135">這是裝載此範例所設定之網站的電腦。</span><span class="sxs-lookup"><span data-stu-id="a2310-135">This is the computer that hosts the website this example configures.</span></span>
<span data-ttu-id="a2310-136">此電腦必須執行 [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016)。</span><span class="sxs-lookup"><span data-stu-id="a2310-136">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>

## <a name="add-the-code-to-tfs"></a><span data-ttu-id="a2310-137">將程式碼新增至 TFS</span><span class="sxs-lookup"><span data-stu-id="a2310-137">Add the code to TFS</span></span>

<span data-ttu-id="a2310-138">我們一開始會在 TFS 中建立 Git 儲存機制，並從您在用戶端電腦上的本機儲存機制匯入程式碼。</span><span class="sxs-lookup"><span data-stu-id="a2310-138">We'll start out by creating a Git repository in TFS, and importing the code from your local repository on the client computer.</span></span>
<span data-ttu-id="a2310-139">如果您尚未將 Demo_CI 儲存機制複製到您的用戶端電腦上，請立即執行下列 Git 命令來執行此操作：</span><span class="sxs-lookup"><span data-stu-id="a2310-139">If you have not already cloned the Demo_CI repository to your client computer, do so now by running the following git command:</span></span>

`git clone https://github.com/PowerShell/Demo_CI`

1. <span data-ttu-id="a2310-140">在您的用戶端電腦上，於網頁瀏覽器中瀏覽至您的 TFS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="a2310-140">On your client computer, navigate to your TFS server in a web browser.</span></span>
1. <span data-ttu-id="a2310-141">在 TFS 中，[建立一個新的小組專案](https://www.visualstudio.com/en-us/docs/setup-admin/create-team-project)並命名為 Demo_CI。</span><span class="sxs-lookup"><span data-stu-id="a2310-141">In TFS, [Create a new team project](https://www.visualstudio.com/en-us/docs/setup-admin/create-team-project) named Demo_CI.</span></span>

    <span data-ttu-id="a2310-142">請確定將 [版本控制] 設定為 [Git]。</span><span class="sxs-lookup"><span data-stu-id="a2310-142">Make sure that **Version control** is set to **Git**.</span></span>
1. <span data-ttu-id="a2310-143">在您的用戶端電腦上，使用下列命令為您剛在 TFS 中建立的儲存機制新增遠端：</span><span class="sxs-lookup"><span data-stu-id="a2310-143">On your client computer, add a remote to the repository you just created in TFS with the following command:</span></span>

    `git remote add tfs <YourTFSRepoURL>`

    <span data-ttu-id="a2310-144">其中 `<YourTFSRepoURL>` 是您在上一個步驟中所建立之 TFS 儲存機制的複製 URL。</span><span class="sxs-lookup"><span data-stu-id="a2310-144">Where `<YourTFSRepoURL>` is the clone URL to the TFS repository you created in the previous step.</span></span>

    <span data-ttu-id="a2310-145">如果您不知道哪裡可以找到此 URL，請參閱[複製現有的 Git 儲存機制](https://www.visualstudio.com/en-us/docs/git/tutorial/clone) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="a2310-145">If you don't know where to find this URL, see [Clone an existing Git repo](https://www.visualstudio.com/en-us/docs/git/tutorial/clone).</span></span>
1. <span data-ttu-id="a2310-146">使用下列命令將程式碼從您的本機儲存機制推送到 TFS 儲存機制：</span><span class="sxs-lookup"><span data-stu-id="a2310-146">Push the code from your local repository to your TFS repository with the following command:</span></span>

    `git push tfs --all`
1. <span data-ttu-id="a2310-147">將會在 TFS 儲存機制中填入 Demo_CI 程式碼。</span><span class="sxs-lookup"><span data-stu-id="a2310-147">The TFS repository will be populated with the Demo_CI code.</span></span>

><span data-ttu-id="a2310-148">**注意：** 此範例會使用 Git 儲存機制之 `ci-cd-example` 分支中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a2310-148">**Note:** This example uses the code in the `ci-cd-example` branch of the Git repo.</span></span>
><span data-ttu-id="a2310-149">請務必指定此分支作為您 TFS 專案中及您所建立之 CI/CD 觸發程序的預設分支。</span><span class="sxs-lookup"><span data-stu-id="a2310-149">Be sure to specify this branch as the default branch in your TFS project, and for the CI/CD triggers you create.</span></span>

## <a name="understanding-the-code"></a><span data-ttu-id="a2310-150">了解程式碼</span><span class="sxs-lookup"><span data-stu-id="a2310-150">Understanding the code</span></span>

<span data-ttu-id="a2310-151">在建立這些組建與部署管線之前，讓我們先來看看部分程式碼以了解情況。</span><span class="sxs-lookup"><span data-stu-id="a2310-151">Before we create the build and deployment pipelines, let's look at some of the code to understand what is going on.</span></span>
<span data-ttu-id="a2310-152">在您的用戶端電腦上，開啟您慣用的文字編輯器，然後瀏覽至 Demo_CI Git 儲存機制的根目錄。</span><span class="sxs-lookup"><span data-stu-id="a2310-152">On your client computer, open your favorite text editor and navigate to the root of your Demo_CI Git repository.</span></span>

### <a name="the-dsc-configuration"></a><span data-ttu-id="a2310-153">DSC 設定</span><span class="sxs-lookup"><span data-stu-id="a2310-153">The DSC configuration</span></span>

<span data-ttu-id="a2310-154">開啟檔案 `DNSServer.ps1` (從本機 Demo_CI 儲存機制的根目錄路徑為 `./InfraDNS/Configs/DNSServer.ps1`)。</span><span class="sxs-lookup"><span data-stu-id="a2310-154">Open the file `DNSServer.ps1` (from the root of the local Demo_CI repository, `./InfraDNS/Configs/DNSServer.ps1`).</span></span>

<span data-ttu-id="a2310-155">此檔案包含設定 DNS 伺服器的 DSC 設定。</span><span class="sxs-lookup"><span data-stu-id="a2310-155">This file contains the DSC configuration that sets up the DNS server.</span></span> <span data-ttu-id="a2310-156">以下是其全部：</span><span class="sxs-lookup"><span data-stu-id="a2310-156">Here it is in its entirety:</span></span>

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

<span data-ttu-id="a2310-157">請注意 `Node` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="a2310-157">Notice the `Node` statement:</span></span>

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

<span data-ttu-id="a2310-158">這會尋找[設定資料](configData.md) (由 `DevEnv.ps1` 指令碼所建立) 中所有已定義為具備 `DNSServer` 角色的節點。</span><span class="sxs-lookup"><span data-stu-id="a2310-158">This finds any nodes that were defined as having a role of `DNSServer` in the [configuration data](configData.md), which is created by the `DevEnv.ps1` script.</span></span>

<span data-ttu-id="a2310-159">進行 CI 時，使用設定資料來定義節點相當重要，因為節點資訊在環境之間可能會有所變更，而使用設定資料則可讓您不須變更設定程式碼，即可輕鬆對節點資訊進行變更。</span><span class="sxs-lookup"><span data-stu-id="a2310-159">Using configuration data to define nodes is important when doing CI because node information will likely change between environments, and using configuration data allows you to easily make changes to node information without changing the configuration code.</span></span>

<span data-ttu-id="a2310-160">在第一個資源區塊中，此設定會呼叫 [WindowsFeature](windowsFeatureResource.md) 以確保啟用 DNS 功能。</span><span class="sxs-lookup"><span data-stu-id="a2310-160">In the first resource block, the configuration calls the [WindowsFeature](windowsFeatureResource.md) to ensure that the DNS feature is enabled.</span></span>
<span data-ttu-id="a2310-161">接下來的資源區塊會從 [xDnsServer](https://github.com/PowerShell/xDnsServer) 模組呼叫資源，以設定主要區域和 DNS 記錄。</span><span class="sxs-lookup"><span data-stu-id="a2310-161">The resource blocks that follow call resources from the [xDnsServer](https://github.com/PowerShell/xDnsServer) module to configure the primary zone and DNS records.</span></span>

<span data-ttu-id="a2310-162">請注意，兩個 `xDnsRecord` 區塊皆包裝在 `foreach` 迴圈中，這些迴圈會逐一查看設定資料中的陣列。</span><span class="sxs-lookup"><span data-stu-id="a2310-162">Notice that the two `xDnsRecord` blocks are wrapped in `foreach` loops that iterate through arrays in the configuration data.</span></span>
<span data-ttu-id="a2310-163">此設定資料同樣也是 `DevEnv.ps1` 指令碼所建立的，接下來將會探討此設定資料。</span><span class="sxs-lookup"><span data-stu-id="a2310-163">Again, the configuration data is created by the `DevEnv.ps1` script, which we'll look at next.</span></span>

### <a name="configuration-data"></a><span data-ttu-id="a2310-164">設定資料</span><span class="sxs-lookup"><span data-stu-id="a2310-164">Configuration data</span></span>

<span data-ttu-id="a2310-165">`DevEnv.ps1` 檔案 (從本機 Demo_CI 儲存機制的根目錄路徑為 `./InfraDNS/DevEnv.ps1`) 會在雜湊表中指定環境特定設定資料，然後將該雜湊表傳遞給對 `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`) 中定義之 `New-DscConfigurationDataDocument` 函式的呼叫。</span><span class="sxs-lookup"><span data-stu-id="a2310-165">The `DevEnv.ps1` file (from the root of the local Demo_CI repository, `./InfraDNS/DevEnv.ps1`) specifies the environment-specific configuration data in a hashtable, and then passes that hashtable to a call to the `New-DscConfigurationDataDocument` function, which is defined in `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).</span></span>

<span data-ttu-id="a2310-166">`DevEnv.ps1` 檔案：</span><span class="sxs-lookup"><span data-stu-id="a2310-166">The `DevEnv.ps1` file:</span></span>

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

<span data-ttu-id="a2310-167">`New-DscConfigurationDataDocument` 函式 (定義於 `\Assets\DscPipelineTools\DscPipelineTools.psm1`) 會以程式設計方式，從以 `RawEnvData` 和 `OtherEnvData` 參數的形式傳遞的雜湊表 (節點資料) 和陣列 (非節點資料) 建立設定資料文件。</span><span class="sxs-lookup"><span data-stu-id="a2310-167">The `New-DscConfigurationDataDocument` function (defined in `\Assets\DscPipelineTools\DscPipelineTools.psm1`) programmatically creates a configuration data document from the hashtable (node data) and array (non-node data) that are passed as the `RawEnvData` and `OtherEnvData` parameters.</span></span>

<span data-ttu-id="a2310-168">在我們的案例中，只使用 `RawEnvData` 參數。</span><span class="sxs-lookup"><span data-stu-id="a2310-168">In our case, only the `RawEnvData` parameter is used.</span></span>

### <a name="the-psake-build-script"></a><span data-ttu-id="a2310-169">psake 建置指令碼</span><span class="sxs-lookup"><span data-stu-id="a2310-169">The psake build script</span></span>

<span data-ttu-id="a2310-170">`Build.ps1` (從 Demo_CI 儲存機制的根目錄路徑為 `./InfraDNS/Build.ps1`) 中定義的 [psake](https://github.com/psake/psake) 建置指令碼會定義組建所含的工作。</span><span class="sxs-lookup"><span data-stu-id="a2310-170">The [psake](https://github.com/psake/psake) build script defined in `Build.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Build.ps1`) defines tasks that are part of the build.</span></span>
<span data-ttu-id="a2310-171">它也定義每個工作所依存的其他工作。</span><span class="sxs-lookup"><span data-stu-id="a2310-171">It also defines which other tasks each task depends on.</span></span>
<span data-ttu-id="a2310-172">當叫用 psake 指令碼時，它會確保指定的工作 (如果未指定任何工作，則是名為 `Default` 的工作) 執行，並且所有相依項目也一併執行 (這是遞迴的，因此相依項目的相依項目也會執行，依此類推)。</span><span class="sxs-lookup"><span data-stu-id="a2310-172">When invoked, the psake script ensures that the specified task (or the task named `Default` if none is specified) runs, and that all dependencies also run (this is recursive, so that dependencies of dependencies run, and so on).</span></span>

<span data-ttu-id="a2310-173">在此範例中，`Default` 是定義為：</span><span class="sxs-lookup"><span data-stu-id="a2310-173">In this example, the `Default` task is defined as:</span></span>

```powershell
Task Default -depends UnitTests
```

<span data-ttu-id="a2310-174">`Default` 工作本身沒有任何實作，但依存於 `CompileConfigs` 工作。</span><span class="sxs-lookup"><span data-stu-id="a2310-174">The `Default` task has no implementation itself, but has a dependency on the `CompileConfigs` task.</span></span>
<span data-ttu-id="a2310-175">產生的工作相依性鏈結會確保執行建置指令碼中的所有工作。</span><span class="sxs-lookup"><span data-stu-id="a2310-175">The resulting chain of task dependencies ensures that all tasks in the build script are run.</span></span>

<span data-ttu-id="a2310-176">在此範例中，是透過呼叫 `Initiate.ps1` 檔案 (位於 Demo_CI 儲存機制的根目錄) 中的 `Invoke-PSake` 來叫用 psake 指令碼：</span><span class="sxs-lookup"><span data-stu-id="a2310-176">In this example, the psake script is invoked by a call to `Invoke-PSake` in the `Initiate.ps1` file (located at the root of the Demo_CI repository):</span></span>

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

<span data-ttu-id="a2310-177">當我們在 TFS 中為範例建立組建定義時，將會提供 psake 指令碼檔作為此指令碼的 `fileName` 參數。</span><span class="sxs-lookup"><span data-stu-id="a2310-177">When we create the build definition for our example in TFS, we will supply our psake script file as the `fileName` parameter for this script.</span></span>

<span data-ttu-id="a2310-178">建置指令碼會定義下列工作：</span><span class="sxs-lookup"><span data-stu-id="a2310-178">The build script defines the following tasks:</span></span>

#### <a name="generateenvironmentfiles"></a><span data-ttu-id="a2310-179">GenerateEnvironmentFiles</span><span class="sxs-lookup"><span data-stu-id="a2310-179">GenerateEnvironmentFiles</span></span>

<span data-ttu-id="a2310-180">會執行 `DevEnv.ps1` 以產生設定資料檔。</span><span class="sxs-lookup"><span data-stu-id="a2310-180">Runs `DevEnv.ps1`, which generates the configuration data file.</span></span>

#### <a name="installmodules"></a><span data-ttu-id="a2310-181">InstallModules</span><span class="sxs-lookup"><span data-stu-id="a2310-181">InstallModules</span></span>

<span data-ttu-id="a2310-182">會安裝設定 `DNSServer.ps1` 所需的模組。</span><span class="sxs-lookup"><span data-stu-id="a2310-182">Installs the modules required by the configuration `DNSServer.ps1`.</span></span>

#### <a name="scriptanalysis"></a><span data-ttu-id="a2310-183">ScriptAnalysis</span><span class="sxs-lookup"><span data-stu-id="a2310-183">ScriptAnalysis</span></span>

<span data-ttu-id="a2310-184">會呼叫 [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer)。</span><span class="sxs-lookup"><span data-stu-id="a2310-184">Calls the [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).</span></span>

#### <a name="unittests"></a><span data-ttu-id="a2310-185">UnitTests</span><span class="sxs-lookup"><span data-stu-id="a2310-185">UnitTests</span></span>

<span data-ttu-id="a2310-186">會執行 [Pester](https://github.com/pester/Pester/wiki) 單元測試。</span><span class="sxs-lookup"><span data-stu-id="a2310-186">Runs the [Pester](https://github.com/pester/Pester/wiki) unit tests.</span></span>

#### <a name="compileconfigs"></a><span data-ttu-id="a2310-187">CompileConfigs</span><span class="sxs-lookup"><span data-stu-id="a2310-187">CompileConfigs</span></span>

<span data-ttu-id="a2310-188">會使用 `GenerateEnvironmentFiles` 工作所產生的設定資料，將設定 (`DNSServer.ps1`) 編譯成 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="a2310-188">Compiles the configuration (`DNSServer.ps1`) into a MOF file, using the configuration data generated by the `GenerateEnvironmentFiles` task.</span></span>

#### <a name="clean"></a><span data-ttu-id="a2310-189">Clean</span><span class="sxs-lookup"><span data-stu-id="a2310-189">Clean</span></span>

<span data-ttu-id="a2310-190">會建立用於範例的資料夾，並移除來自先前回合的所有測試結果、設定資料檔及模組。</span><span class="sxs-lookup"><span data-stu-id="a2310-190">Creates the folders used for the example, and removes any test results, configuration data files, and modules from previous runs.</span></span>

### <a name="the-psake-deploy-script"></a><span data-ttu-id="a2310-191">psake 部署指令碼</span><span class="sxs-lookup"><span data-stu-id="a2310-191">The psake deploy script</span></span>

<span data-ttu-id="a2310-192">`Deploy.ps1` (從 Demo_CI 儲存機制的根目錄路徑為 `./InfraDNS/Deploy.ps1`) 中定義的 [psake](https://github.com/psake/psake) 部署指令碼會定義部署和執行設定的工作。</span><span class="sxs-lookup"><span data-stu-id="a2310-192">The [psake](https://github.com/psake/psake) deployment script defined in `Deploy.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Deploy.ps1`) defines tasks that deploy and run the configuration.</span></span>

<span data-ttu-id="a2310-193">`Deploy.ps1` 會定義下列工作：</span><span class="sxs-lookup"><span data-stu-id="a2310-193">`Deploy.ps1` defines the following tasks:</span></span>

#### <a name="deploymodules"></a><span data-ttu-id="a2310-194">DeployModules</span><span class="sxs-lookup"><span data-stu-id="a2310-194">DeployModules</span></span>

<span data-ttu-id="a2310-195">會在 `TestAgent1` 上啟動 PowerShell 工作階段，並安裝包含設定所需 DSC 資源的模組。</span><span class="sxs-lookup"><span data-stu-id="a2310-195">Starts a PowerShell session on `TestAgent1` and installs the modules containing the DSC resources required for the configuration.</span></span>

#### <a name="deployconfigs"></a><span data-ttu-id="a2310-196">DeployConfigs</span><span class="sxs-lookup"><span data-stu-id="a2310-196">DeployConfigs</span></span>

<span data-ttu-id="a2310-197">會呼叫 [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration.md) Cmdlet 以在 `TestAgent1` 上執行設定。</span><span class="sxs-lookup"><span data-stu-id="a2310-197">Calls the [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration.md) cmdlet to run the configuration on `TestAgent1`.</span></span>

#### <a name="integrationtests"></a><span data-ttu-id="a2310-198">IntegrationTests</span><span class="sxs-lookup"><span data-stu-id="a2310-198">IntegrationTests</span></span>

<span data-ttu-id="a2310-199">會執行 [Pester](https://github.com/pester/Pester/wiki) 整合測試。</span><span class="sxs-lookup"><span data-stu-id="a2310-199">Runs the [Pester](https://github.com/pester/Pester/wiki) integration tests.</span></span>

#### <a name="acceptancetests"></a><span data-ttu-id="a2310-200">AcceptanceTests</span><span class="sxs-lookup"><span data-stu-id="a2310-200">AcceptanceTests</span></span>

<span data-ttu-id="a2310-201">會執行 [Pester](https://github.com/pester/Pester/wiki) 接受度測試。</span><span class="sxs-lookup"><span data-stu-id="a2310-201">Runs the [Pester](https://github.com/pester/Pester/wiki) acceptance tests.</span></span>

#### <a name="clean"></a><span data-ttu-id="a2310-202">Clean</span><span class="sxs-lookup"><span data-stu-id="a2310-202">Clean</span></span>

<span data-ttu-id="a2310-203">會移除在先前回合中安裝的所有模組，並確保測試結果資料夾存在。</span><span class="sxs-lookup"><span data-stu-id="a2310-203">Removes any modules installed in previous runs, and ensures that the test result folder exists.</span></span>

### <a name="test-scripts"></a><span data-ttu-id="a2310-204">測試指令碼</span><span class="sxs-lookup"><span data-stu-id="a2310-204">Test scripts</span></span>

<span data-ttu-id="a2310-205">接受度、整合及單元測試是在 `Tests` 資料夾 (從 Demo_CI 儲存機制的根目錄路徑為 `./InfraDNS/Tests`) 內的指令碼中定義的，各分別在其個別資料夾內名為 `DNSServer.tests.ps1` 的檔案中。</span><span class="sxs-lookup"><span data-stu-id="a2310-205">Acceptance, Integration, and Unit tests are defined in scripts in the `Tests` folder (from the root of the Demo_CI repository, `./InfraDNS/Tests`), each in files named `DNSServer.tests.ps1` in their respective folders.</span></span>

<span data-ttu-id="a2310-206">測試指令碼會使用 [Pester](https://github.com/pester/Pester/wiki) 和 [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) 語法。</span><span class="sxs-lookup"><span data-stu-id="a2310-206">The test scripts use [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="unit-tests"></a><span data-ttu-id="a2310-207">單元測試</span><span class="sxs-lookup"><span data-stu-id="a2310-207">Unit tests</span></span>

<span data-ttu-id="a2310-208">單元測試會測試 DSC 設定本身，以確保設定在執行時會執行預期執行的工作。</span><span class="sxs-lookup"><span data-stu-id="a2310-208">The unit tests test the DSC configurations themselves to ensure that the configurations will do what is expected when they run.</span></span>
<span data-ttu-id="a2310-209">單元測試指令碼會使用 [Pester](https://github.com/pester/Pester/wiki)。</span><span class="sxs-lookup"><span data-stu-id="a2310-209">The unit test script uses [Pester](https://github.com/pester/Pester/wiki).</span></span>

#### <a name="integration-tests"></a><span data-ttu-id="a2310-210">整合測試</span><span class="sxs-lookup"><span data-stu-id="a2310-210">Integration tests</span></span>

<span data-ttu-id="a2310-211">整合測試會測試系統的設定，以確保當與其他元件整合時，會依照預期的方式設定系統。</span><span class="sxs-lookup"><span data-stu-id="a2310-211">The integration tests test the configuration of the system to ensure that when integrated with other components, the system is configured as expected.</span></span> <span data-ttu-id="a2310-212">使用 DSC 來設定這些測試之後，這些測試就會在目標節點上執行。</span><span class="sxs-lookup"><span data-stu-id="a2310-212">These tests run on the target node after it has been configured with DSC.</span></span>
<span data-ttu-id="a2310-213">整合測試指令碼會混合使用 [Pester](https://github.com/pester/Pester/wiki) 和 [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) 語法。</span><span class="sxs-lookup"><span data-stu-id="a2310-213">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="acceptance-tests"></a><span data-ttu-id="a2310-214">接受度測試</span><span class="sxs-lookup"><span data-stu-id="a2310-214">Acceptance tests</span></span>

<span data-ttu-id="a2310-215">接受度測試會測試系統，以確保系統依照預期的方式運作。</span><span class="sxs-lookup"><span data-stu-id="a2310-215">Acceptance tests test the system to ensure that it behaves as expected.</span></span>
<span data-ttu-id="a2310-216">例如，它會測試來確保在查詢時，網頁會傳回正確的資訊。</span><span class="sxs-lookup"><span data-stu-id="a2310-216">For example, it tests to ensure a web page returns the right information when queried.</span></span>
<span data-ttu-id="a2310-217">這些測試會從目標節點的遠端執行，以測試真實世界案例。</span><span class="sxs-lookup"><span data-stu-id="a2310-217">These tests run remotely from the target node in order to test real world scenarios.</span></span>
<span data-ttu-id="a2310-218">整合測試指令碼會混合使用 [Pester](https://github.com/pester/Pester/wiki) 和 [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) 語法。</span><span class="sxs-lookup"><span data-stu-id="a2310-218">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

## <a name="define-the-build"></a><span data-ttu-id="a2310-219">定義組建</span><span class="sxs-lookup"><span data-stu-id="a2310-219">Define the build</span></span>

<span data-ttu-id="a2310-220">既然我們已將程式碼上傳到 TFS 並查看其功能，現在即可開始定義組建。</span><span class="sxs-lookup"><span data-stu-id="a2310-220">Now that we've uploaded our code to TFS and looked at what it does, let's define our build.</span></span>

<span data-ttu-id="a2310-221">在這裡，我們將只涵蓋您將新增到組建中的建置步驟。</span><span class="sxs-lookup"><span data-stu-id="a2310-221">Here, we'll cover only the build steps that you'll add to the build.</span></span> <span data-ttu-id="a2310-222">如需有關如何在 TFS 中建立組建定義的指示，請參閱[建立組建定義並將其排入佇列](https://www.visualstudio.com/en-us/docs/build/define/create) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="a2310-222">For instructions on how to create a build definition in TFS, see [Create and queue a build definition](https://www.visualstudio.com/en-us/docs/build/define/create).</span></span>

<span data-ttu-id="a2310-223">請建立一個名為 "InfraDNS" 的新組建定義 (選取 [空白] 範本)。</span><span class="sxs-lookup"><span data-stu-id="a2310-223">Create a new build definition (select the **Empty** template) named "InfraDNS".</span></span>
<span data-ttu-id="a2310-224">將下列步驟新增到您的組建定義中：</span><span class="sxs-lookup"><span data-stu-id="a2310-224">Add the following steps to you build definition:</span></span>

- <span data-ttu-id="a2310-225">PowerShell 指令碼</span><span class="sxs-lookup"><span data-stu-id="a2310-225">PowerShell Script</span></span>
- <span data-ttu-id="a2310-226">發行測試結果</span><span class="sxs-lookup"><span data-stu-id="a2310-226">Publish Test Results</span></span>
- <span data-ttu-id="a2310-227">複製檔案</span><span class="sxs-lookup"><span data-stu-id="a2310-227">Copy Files</span></span>
- <span data-ttu-id="a2310-228">發行成品</span><span class="sxs-lookup"><span data-stu-id="a2310-228">Publish Artifact</span></span>

<span data-ttu-id="a2310-229">新增這些建置步驟之後，請依下列方式編輯每個步驟的屬性：</span><span class="sxs-lookup"><span data-stu-id="a2310-229">After adding these build steps, edit the properties of each step as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="a2310-230">PowerShell 指令碼</span><span class="sxs-lookup"><span data-stu-id="a2310-230">PowerShell Script</span></span>

1. <span data-ttu-id="a2310-231">將 [類型] 屬性設定為 `File Path`。</span><span class="sxs-lookup"><span data-stu-id="a2310-231">Set the **Type** property to `File Path`.</span></span>
1. <span data-ttu-id="a2310-232">將 [指令碼路徑] 屬性設定為 `initiate.ps1`。</span><span class="sxs-lookup"><span data-stu-id="a2310-232">Set the **Script Path** property to `initiate.ps1`.</span></span>
1. <span data-ttu-id="a2310-233">將 `-fileName build` 新增到 [引數] 屬性。</span><span class="sxs-lookup"><span data-stu-id="a2310-233">Add `-fileName build` to the **Arguments** property.</span></span>

<span data-ttu-id="a2310-234">此建置步驟會執行 `initiate.ps1` 檔案以呼叫 psake 建置指令碼。</span><span class="sxs-lookup"><span data-stu-id="a2310-234">This build step runs the `initiate.ps1` file, which calls the psake build script.</span></span>

### <a name="publish-test-results"></a><span data-ttu-id="a2310-235">發行測試結果</span><span class="sxs-lookup"><span data-stu-id="a2310-235">Publish Test Results</span></span>

1. <span data-ttu-id="a2310-236">將 [測試結果格式] 設定為 `NUnit`</span><span class="sxs-lookup"><span data-stu-id="a2310-236">Set **Test Result Format** to `NUnit`</span></span>
1. <span data-ttu-id="a2310-237">將 [測試結果檔案] 設定為 `InfraDNS/Tests/Results/*.xml`</span><span class="sxs-lookup"><span data-stu-id="a2310-237">Set **Test Results Files** to `InfraDNS/Tests/Results/*.xml`</span></span>
1. <span data-ttu-id="a2310-238">將 [測試回合標題] 設定為 `Unit`。</span><span class="sxs-lookup"><span data-stu-id="a2310-238">Set **Test Run Title** to `Unit`.</span></span>
1. <span data-ttu-id="a2310-239">確定已選取 [啟用] 和 [永遠執行] 這兩個 [控制選項]。</span><span class="sxs-lookup"><span data-stu-id="a2310-239">Make sure **Control Options** **Enabled** and **Always run** are both selected.</span></span>

<span data-ttu-id="a2310-240">此建置步驟會執行我們先前查看之 Pester 指令碼中的單元測試，然後將結果儲存在 `InfraDNS/Tests/Results/*.xml` 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="a2310-240">This build step runs the unit tests in the Pester script we looked at earlier, and stores the results in the `InfraDNS/Tests/Results/*.xml` folder.</span></span>

### <a name="copy-files"></a><span data-ttu-id="a2310-241">複製檔案</span><span class="sxs-lookup"><span data-stu-id="a2310-241">Copy Files</span></span>

1. <span data-ttu-id="a2310-242">將下列每一行新增到 [內容] 中：</span><span class="sxs-lookup"><span data-stu-id="a2310-242">Add each of the following lines to **Contents**:</span></span>

    ```
    initiate.ps1
    **\deploy.ps1
    **\Acceptance\**
    **\Integration\**
    ```

1. <span data-ttu-id="a2310-243">將 [目標資料夾] 設定為 `$(Build.ArtifactStagingDirectory)\`</span><span class="sxs-lookup"><span data-stu-id="a2310-243">Set **TargetFolder** to `$(Build.ArtifactStagingDirectory)\`</span></span>

<span data-ttu-id="a2310-244">此步驟會將建置和測試指令碼複製到暫存目錄中，以便供下一個步驟發行成組建成品。</span><span class="sxs-lookup"><span data-stu-id="a2310-244">This step copies the build and test scripts to the staging directory so that the can be published as build artifacts by the next step.</span></span>

### <a name="publish-artifact"></a><span data-ttu-id="a2310-245">發行成品</span><span class="sxs-lookup"><span data-stu-id="a2310-245">Publish Artifact</span></span>

1. <span data-ttu-id="a2310-246">將 [要發行的路徑] 設定為 `$(Build.ArtifactStagingDirectory)\`</span><span class="sxs-lookup"><span data-stu-id="a2310-246">Set **Path to Publish** to `$(Build.ArtifactStagingDirectory)\`</span></span>
1. <span data-ttu-id="a2310-247">將 [成品名稱] 設定為 `Deploy`</span><span class="sxs-lookup"><span data-stu-id="a2310-247">Set **Artifact Name** to `Deploy`</span></span>
1. <span data-ttu-id="a2310-248">將 [成品類型] 設定為 `Server`</span><span class="sxs-lookup"><span data-stu-id="a2310-248">Set **Artifact Type** to `Server`</span></span>
1. <span data-ttu-id="a2310-249">在 [控制選項] 中選取 [`Enabled`]</span><span class="sxs-lookup"><span data-stu-id="a2310-249">Select `Enabled` in **Control Options**</span></span>

## <a name="enable-continuous-integration"></a><span data-ttu-id="a2310-250">啟用持續整合</span><span class="sxs-lookup"><span data-stu-id="a2310-250">Enable continuous integration</span></span>

<span data-ttu-id="a2310-251">現在我們將設定一個觸發程序，此觸發程序會在每當有任何變更簽入 Git 儲存機制的 `ci-cd-example` 分支中時，便促使專案進行建置。</span><span class="sxs-lookup"><span data-stu-id="a2310-251">Now we'll set up a trigger that causes the project to build any time a change is checked in to the `ci-cd-example` branch of the git repository.</span></span>

1. <span data-ttu-id="a2310-252">在 TFS 中，按一下 [建置及發行] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="a2310-252">In TFS, click the **Build & Release** tab</span></span>
1. <span data-ttu-id="a2310-253">選取 `DNS Infra` 組建定義，然後按一下 [編輯]</span><span class="sxs-lookup"><span data-stu-id="a2310-253">Select the `DNS Infra` build definition, and click **Edit**</span></span>
1. <span data-ttu-id="a2310-254">按一下 [觸發程序] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="a2310-254">Click the **Triggers** tab</span></span>
1. <span data-ttu-id="a2310-255">選取 [持續整合 (CI)]，然後從分支下拉式清單中選取 `refs/heads/ci-cd-example`</span><span class="sxs-lookup"><span data-stu-id="a2310-255">Select **Continuous integration (CI)**, and select `refs/heads/ci-cd-example` in the branch drop-down list</span></span>
1. <span data-ttu-id="a2310-256">按一下 [儲存]，然後按一下 [確定]</span><span class="sxs-lookup"><span data-stu-id="a2310-256">Click **Save** and then **OK**</span></span>

<span data-ttu-id="a2310-257">現在 TFS Git 儲存機制中的任何變更都會觸發自動化建置。</span><span class="sxs-lookup"><span data-stu-id="a2310-257">Now any change in the TFS git repository triggers an automated build.</span></span>

## <a name="create-the-release-definition"></a><span data-ttu-id="a2310-258">建立發行定義</span><span class="sxs-lookup"><span data-stu-id="a2310-258">Create the release definition</span></span>

<span data-ttu-id="a2310-259">讓我們來建立一個發行定義，以便在每次簽入程式碼時，都將專案部署到開發環境。</span><span class="sxs-lookup"><span data-stu-id="a2310-259">Let's create a release definition so that the project is deployed to the development environment with every code check-in.</span></span>

<span data-ttu-id="a2310-260">若要這樣做，請新增一個與您先前建立之 `InfraDNS` 組建定義關聯的新發行定義。</span><span class="sxs-lookup"><span data-stu-id="a2310-260">To do this, add a new release definition associated with the `InfraDNS` build definition you created previously.</span></span>
<span data-ttu-id="a2310-261">請務必選取 [持續部署]，以便在每次完成新組建時便觸發新的發行。</span><span class="sxs-lookup"><span data-stu-id="a2310-261">Be sure to select **Continuous deployment** so that a new release will be triggered any time a new build is completed.</span></span>
<span data-ttu-id="a2310-262">([做法：使用發行定義](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions) \(英文\) 並依下列方式進行設定：</span><span class="sxs-lookup"><span data-stu-id="a2310-262">([How to: Work with release definitions](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions)) and configure it as follows:</span></span>

<span data-ttu-id="a2310-263">將下列步驟新增到發行定義中：</span><span class="sxs-lookup"><span data-stu-id="a2310-263">Add the following steps to the release definition:</span></span>

- <span data-ttu-id="a2310-264">PowerShell 指令碼</span><span class="sxs-lookup"><span data-stu-id="a2310-264">PowerShell Script</span></span>
- <span data-ttu-id="a2310-265">發行測試結果</span><span class="sxs-lookup"><span data-stu-id="a2310-265">Publish Test Results</span></span>
- <span data-ttu-id="a2310-266">發行測試結果</span><span class="sxs-lookup"><span data-stu-id="a2310-266">Publish Test Results</span></span>

<span data-ttu-id="a2310-267">依下列方式編輯步驟：</span><span class="sxs-lookup"><span data-stu-id="a2310-267">Edit the steps as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="a2310-268">PowerShell 指令碼</span><span class="sxs-lookup"><span data-stu-id="a2310-268">PowerShell Script</span></span>

1. <span data-ttu-id="a2310-269">將 [指令碼路徑] 欄位設定為 `$(Build.DefinitionName)\Deploy\initiate.ps1"`</span><span class="sxs-lookup"><span data-stu-id="a2310-269">Set the **Script Path** field to `$(Build.DefinitionName)\Deploy\initiate.ps1"`</span></span>
1. <span data-ttu-id="a2310-270">將 [引數] 欄位設定為 `-fileName Deploy`</span><span class="sxs-lookup"><span data-stu-id="a2310-270">Set the **Arguments** field to `-fileName Deploy`</span></span>

### <a name="first-publish-test-results"></a><span data-ttu-id="a2310-271">第一個發行測試結果</span><span class="sxs-lookup"><span data-stu-id="a2310-271">First Publish Test Results</span></span>

1. <span data-ttu-id="a2310-272">為 [測試結果格式] 欄位選取 [`NUnit`]</span><span class="sxs-lookup"><span data-stu-id="a2310-272">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="a2310-273">將 [測試結果檔案] 欄位設定為 `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span><span class="sxs-lookup"><span data-stu-id="a2310-273">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span></span>
1. <span data-ttu-id="a2310-274">將 [測試回合標題] 設定為 `Integration`</span><span class="sxs-lookup"><span data-stu-id="a2310-274">Set the **Test Run Title** to `Integration`</span></span>
1. <span data-ttu-id="a2310-275">在 [控制選項] 底下，選取 [永遠執行]</span><span class="sxs-lookup"><span data-stu-id="a2310-275">Under **Control Options**, check **Always run**</span></span>

### <a name="second-publish-test-results"></a><span data-ttu-id="a2310-276">第二個發行測試結果</span><span class="sxs-lookup"><span data-stu-id="a2310-276">Second Publish Test Results</span></span>

1. <span data-ttu-id="a2310-277">為 [測試結果格式] 欄位選取 [`NUnit`]</span><span class="sxs-lookup"><span data-stu-id="a2310-277">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="a2310-278">將 [測試結果檔案] 欄位設定為 `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span><span class="sxs-lookup"><span data-stu-id="a2310-278">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span></span>
1. <span data-ttu-id="a2310-279">將 [測試回合標題] 設定為 `Acceptance`</span><span class="sxs-lookup"><span data-stu-id="a2310-279">Set the **Test Run Title** to `Acceptance`</span></span>
1. <span data-ttu-id="a2310-280">在 [控制選項] 底下，選取 [永遠執行]</span><span class="sxs-lookup"><span data-stu-id="a2310-280">Under **Control Options**, check **Always run**</span></span>

## <a name="verify-your-results"></a><span data-ttu-id="a2310-281">驗證您的結果</span><span class="sxs-lookup"><span data-stu-id="a2310-281">Verify your results</span></span>

<span data-ttu-id="a2310-282">現在，每當您將 `ci-cd-example` 分支中的變更推送到 TFS 時，就會開始一個新的組建。</span><span class="sxs-lookup"><span data-stu-id="a2310-282">Now, any time you push changes in the `ci-cd-example` branch to TFS, a new build will start.</span></span>
<span data-ttu-id="a2310-283">如果組建順利完成，就會觸發新的部署。</span><span class="sxs-lookup"><span data-stu-id="a2310-283">If the build completes successfully, a new deployment is triggered.</span></span>

<span data-ttu-id="a2310-284">您可以在用戶端電腦上開啟瀏覽器並瀏覽至 `www.contoso.com`，來檢查部署結果。</span><span class="sxs-lookup"><span data-stu-id="a2310-284">You can check the result of the deployment by opening a browser on the client machine and navigating to `www.contoso.com`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a2310-285">接下來的步驟</span><span class="sxs-lookup"><span data-stu-id="a2310-285">Next steps</span></span>

<span data-ttu-id="a2310-286">此範例會設定 DNS 伺服器 `TestAgent1`，讓 URL `www.contoso.com` 解析成 `TestAgent2`，但它並不會實際部署網站。</span><span class="sxs-lookup"><span data-stu-id="a2310-286">This example configures the DNS server `TestAgent1` so that the URL `www.contoso.com` resolves to `TestAgent2`, but it does not actually deploy a website.</span></span>
<span data-ttu-id="a2310-287">儲存機制的 `WebApp` 資料夾底下有提供此做法的基本架構。</span><span class="sxs-lookup"><span data-stu-id="a2310-287">The skeleton for doing so is provided in the repo under the `WebApp` folder.</span></span>
<span data-ttu-id="a2310-288">您可以使用提供的 Stub 來建立 psake 指令碼、Pester 測試及 DSC 設定，以部署您自己的網站。</span><span class="sxs-lookup"><span data-stu-id="a2310-288">You can use the stubs provided to create psake scripts, Pester tests, and DSC configurations to deploy your own website.</span></span>