---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "重現示範端點"
ms.technology: powershell
ms.openlocfilehash: 4a56272b6f995500d443d441f5e03db85dac6f96
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: zh-TW
---
# <a name="remake-the-demo-endpoint"></a><span data-ttu-id="c2c1c-103">重現示範端點</span><span class="sxs-lookup"><span data-stu-id="c2c1c-103">Remake the Demo Endpoint</span></span>
<span data-ttu-id="c2c1c-104">在本節中，您將了解如何產生您在上一節中所使用之示範端點的相同複本。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-104">In this section, you will learn how to generate an exact replica of the demo endpoint you used in the above section.</span></span>
<span data-ttu-id="c2c1c-105">本節將介紹了解 JEA 所需的核心概念，包括 PowerShell 工作階段設定和角色功能。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-105">This will introduce core concepts that are necessary to understand JEA, including PowerShell Session Configurations and Role Capabilities.</span></span>

## <a name="powershell-session-configurations"></a><span data-ttu-id="c2c1c-106">PowerShell 工作階段設定</span><span class="sxs-lookup"><span data-stu-id="c2c1c-106">PowerShell Session Configurations</span></span>
<span data-ttu-id="c2c1c-107">當您在上一節中使用 JEA 時，首先會執行下列命令︰</span><span class="sxs-lookup"><span data-stu-id="c2c1c-107">When you used JEA in the above section, you started by running the following command:</span></span>

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEA_Demo -Credential $NonAdminCred
```

<span data-ttu-id="c2c1c-108">其中大部分參數一目了然，但 *ConfigurationName* 參數乍看之下可能令人混淆。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-108">While most of the parameters are self-explanatory, the *ConfigurationName* parameter may seem confusing at first.</span></span>
<span data-ttu-id="c2c1c-109">該參數指定您要連線的 PowerShell 工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-109">That parameter specified the PowerShell Session Configuration to which you were connecting.</span></span>

<span data-ttu-id="c2c1c-110">*PowerShell 工作階段設定*是 PowerShell 端點的複雜說法。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-110">*PowerShell Session Configuration* is a fancy term for a PowerShell endpoint.</span></span>
<span data-ttu-id="c2c1c-111">這是使用者連線並存取 PowerShell 功能的象徵性「位置」。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-111">It is the figurative "place" where users connect and get access to PowerShell functionality.</span></span>
<span data-ttu-id="c2c1c-112">根據您設定工作階段設定的方式，它可提供不同的功能給連線使用者。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-112">Based on how you set up a Session Configuration, it can provide different functionality to connecting users.</span></span>
<span data-ttu-id="c2c1c-113">針對 JEA，我們使用工作階段設定將 PowerShell 限制在一組有限的功能，並以特殊權限虛擬帳戶身分執行。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-113">For JEA, we use Session Configurations to restrict PowerShell to a limited set of functionality and to run as a privileged virtual account.</span></span>

<span data-ttu-id="c2c1c-114">您的電腦上已經登錄數個 PowerShell 工作階段設定，每個設定的設定方式稍有不同。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-114">You already have several registered PowerShell Session Configurations on your machine, each set up slightly differently.</span></span>
<span data-ttu-id="c2c1c-115">這些設定大部分隨附於 Windows，但 "JEA_Demo" 工作階段設定則是在[必要條件](prerequisites.md)一節中所設定。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-115">Most of them come with Windows, but the "JEA_Demo" Session Configuration was set up in the [prerequisites](prerequisites.md) section.</span></span>
<span data-ttu-id="c2c1c-116">您可以在系統管理員的 PowerShell 提示字元中執行下列命令，來查看所有登錄的工作階段設定︰</span><span class="sxs-lookup"><span data-stu-id="c2c1c-116">You can see all registered Session Configurations by running the following command in an Administrator PowerShell prompt:</span></span>

```PowerShell
Get-PSSessionConfiguration
```

## <a name="powershell-session-configuration-files"></a><span data-ttu-id="c2c1c-117">PowerShell 工作階段設定檔</span><span class="sxs-lookup"><span data-stu-id="c2c1c-117">PowerShell Session Configuration Files</span></span>
<span data-ttu-id="c2c1c-118">您可以登錄新的 *PowerShell 工作階段設定檔*，來建立新的工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-118">You can make new Session Configurations by registering new *PowerShell Session Configuration Files*.</span></span>
<span data-ttu-id="c2c1c-119">工作階段設定檔的副檔名為 ".pssc"。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-119">Session Configuration Files have ".pssc" file extensions.</span></span>
<span data-ttu-id="c2c1c-120">您可以使用 New-PSSessionConfigurationFile Cmdlet 產生工作階段設定檔。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-120">You can generate Session Configuration Files with the New-PSSessionConfigurationFile cmdlet.</span></span>

<span data-ttu-id="c2c1c-121">接下來，您將為 JEA 建立並登錄新的工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-121">Next, you are going to create and register a new Session Configuration for JEA.</span></span>

## <a name="generate-and-modify-your-powershell-session-configuration"></a><span data-ttu-id="c2c1c-122">產生及修改您的 PowerShell 工作階段設定</span><span class="sxs-lookup"><span data-stu-id="c2c1c-122">Generate and Modify your PowerShell Session Configuration</span></span>
<span data-ttu-id="c2c1c-123">執行下列命令，產生 PowerShell 工作階段設定「基本架構」檔案。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-123">Run the following command to generate a PowerShell Session Configuration "skeleton" file.</span></span>

```PowerShell
New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

> <span data-ttu-id="c2c1c-124">**提示**︰此基本架構檔案預設只會包含最常見的組態設定。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-124">**TIP:** Only the most common configuration settings are included in the skeleton file by default.</span></span>
> <span data-ttu-id="c2c1c-125">使用 `-Full` 參數可將所有適用的設定加入產生的 PSSC。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-125">Use the `-Full` parameter to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="c2c1c-126">在 PowerShell ISE 或您偏好的文字編輯器中開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-126">Open the file in PowerShell ISE, or your favorite text editor.</span></span>

```PowerShell
ise "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

<span data-ttu-id="c2c1c-127">將檔案中的下列欄位更新為底下的值 (記得在您自己的非系統管理員安全性群組中進行取代)︰</span><span class="sxs-lookup"><span data-stu-id="c2c1c-127">Update the following fields in the file with the values below (remember to substitute in your own non-administrator security group):</span></span>

```PowerShell
# OLD: SessionType = 'Default'
SessionType = 'RestrictedRemoteServer'

# OLD: TranscriptDirectory = 'C:\Transcripts\'
TranscriptDirectory = "C:\ProgramData\JEAConfiguration\Transcripts"

# OLD: # RunAsVirtualAccount = $true
RunAsVirtualAccount = $true

# OLD: RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }
RoleDefinitions = @{'CONTOSO\JEA_NonAdmin_Operator' = @{ RoleCapabilities =  'Maintenance' }}
```

<span data-ttu-id="c2c1c-128">以下是每個項目所代表的意義︰</span><span class="sxs-lookup"><span data-stu-id="c2c1c-128">Here is what each of those entries mean:</span></span>

1.  <span data-ttu-id="c2c1c-129">*SessionType* 欄位定義預設要用於此端點的預設值。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-129">The *SessionType* field defines preset default settings to use with this endpoint.</span></span>
<span data-ttu-id="c2c1c-130">*RestrictedRemoteServer* 定義遠端管理所需的最低設定。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-130">*RestrictedRemoteServer* defines the minimal settings necessary for remote management.</span></span>
<span data-ttu-id="c2c1c-131">根據預設，*RestrictedRemoteServer* 端點會公開 Get-Command、Get-FormatData、Select-Object、Get-Help、Measure-Object、Exit-PSSession、Clear-Host 和 Out-Default。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-131">By default, a *RestrictedRemoteServer* endpoint will expose Get-Command, Get-FormatData, Select-Object, Get-Help, Measure-Object, Exit-PSSession, Clear-Host, and Out-Default.</span></span>
<span data-ttu-id="c2c1c-132">它會將 *ExecutionPolicy* 設定為 *RemoteSigned*，並將 *LanguageMode* 設定為 *NoLanguage*。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-132">It will set the *ExecutionPolicy* to *RemoteSigned*, and the *LanguageMode* to *NoLanguage*.</span></span>
<span data-ttu-id="c2c1c-133">這些設定的唯一作用是提供安全且最基本的起點，以便設定您的端點。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-133">The net effect of these settings is a secure and minimal starting point for configuring your endpoint.</span></span>

2.  <span data-ttu-id="c2c1c-134">*RoleDefinitions* 欄位將角色功能指派給特定群組。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-134">The *RoleDefinitions* field assigns Role Capabilities to specific groups.</span></span>
<span data-ttu-id="c2c1c-135">它會定義誰可以特殊權限帳戶身分執行什麼工作。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-135">It defines who can do what as a privileged account.</span></span>
<span data-ttu-id="c2c1c-136">您可以使用此欄位，根據群組成員資格指定任何連線使用者可以使用的功能。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-136">With this field, you can specify the functionality available to any connecting user based on group membership.</span></span>
<span data-ttu-id="c2c1c-137">這是 JEA RBAC 功能的核心。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-137">This is the core of JEA's RBAC functionality.</span></span>
<span data-ttu-id="c2c1c-138">在此範例中，您將對 "Contoso\JEA_NonAdmin_Operator" 群組的成員公開預製的「維護」RoleCapability。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-138">In this example, you are exposing the pre-made "Maintenance" RoleCapability to members of the "Contoso\JEA_NonAdmin_Operator" group.</span></span>

3.  <span data-ttu-id="c2c1c-139">*RunAsVirtualAccount* 欄位指出 PowerShell 應該以此端點的虛擬帳戶身分執行。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-139">The *RunAsVirtualAccount* field indicates that PowerShell should "run as" a Virtual Account at this endpoint.</span></span>
<span data-ttu-id="c2c1c-140">根據預設，虛擬帳戶是內建 Administrator 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-140">By default, the Virtual Account is a member of the built in Administrators group.</span></span>
<span data-ttu-id="c2c1c-141">在網域控制站上，它預設也是 Domain Administrators 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-141">On a domain controller, it is also a member of the Domain Administrators group by default.</span></span>
<span data-ttu-id="c2c1c-142">稍後在本指南中，您將了解如何自訂虛擬帳戶的權限。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-142">Later in this guide, you will learn how to customize the privileges of the Virtual Account.</span></span>

4.  <span data-ttu-id="c2c1c-143">*TranscriptDirectory* 欄位定義 "Over-The-Shoulder" PowerShell 文字記錄在每個遠端工作階段之後的儲存位置。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-143">The *TranscriptDirectory* field defines where "over-the-shoulder" PowerShell transcripts are saved after each remote session.</span></span>
<span data-ttu-id="c2c1c-144">這些文字記錄讓您能夠以容易閱讀的方式，來查看在每個工作階段中執行的動作。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-144">These transcripts allow you to inspect the actions taken in each session in a readable way.</span></span>
<span data-ttu-id="c2c1c-145">如需 PowerShell 文字記錄的詳細資訊，請參閱這篇[部落格文章](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx)。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-145">For more information about PowerShell transcripts, check out this [blog post](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).</span></span>
<span data-ttu-id="c2c1c-146">注意︰定期的 Windows Eventing 也會擷取每位使用者使用 PowerShell 執行的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-146">Note: regular Windows Eventing also captures information about what each user ran with PowerShell.</span></span>
<span data-ttu-id="c2c1c-147">只不過文字記錄稍微更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-147">Transcripts are just a bit more readable.</span></span>

<span data-ttu-id="c2c1c-148">最後，將變更儲存至 *JEADemo2.pssc*。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-148">Finally, save your changes to *JEADemo2.pssc*.</span></span>

## <a name="apply-the-powershell-session-configuration"></a><span data-ttu-id="c2c1c-149">套用 PowerShell 工作階段設定</span><span class="sxs-lookup"><span data-stu-id="c2c1c-149">Apply the PowerShell Session Configuration</span></span>

<span data-ttu-id="c2c1c-150">若要從工作階段設定檔建立端點，您必須登錄該檔案。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-150">To create an endpoint from a Session Configuration file, you need to register the file.</span></span>
<span data-ttu-id="c2c1c-151">這需要幾項資訊︰</span><span class="sxs-lookup"><span data-stu-id="c2c1c-151">This requires a few pieces of information:</span></span>

1. <span data-ttu-id="c2c1c-152">工作階段設定檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-152">The path to the Session Configuration file.</span></span>
2. <span data-ttu-id="c2c1c-153">登錄的工作階段設定名稱。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-153">The name of your registered Session Configuration.</span></span> <span data-ttu-id="c2c1c-154">這是使用者使用 `Enter-PSSession` 或 `New-PSSession` 連線到您的端點時，提供給 "ConfigurationName" 參數的相同名稱。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-154">This is the same name users provide to the "ConfigurationName" parameter when they connect to your endpoint with `Enter-PSSession` or `New-PSSession`.</span></span>

<span data-ttu-id="c2c1c-155">若要登錄本機電腦上的工作階段設定，請執行下列命令︰</span><span class="sxs-lookup"><span data-stu-id="c2c1c-155">To register the Session Configuration on your local machine, run the following command:</span></span>

```PowerShell
Register-PSSessionConfiguration -Name 'JEADemo2' -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

<span data-ttu-id="c2c1c-156">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="c2c1c-156">Congratulations!</span></span> <span data-ttu-id="c2c1c-157">您已設定 JEA 端點。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-157">You have set up your JEA endpoint.</span></span>

## <a name="test-out-your-endpoint"></a><span data-ttu-id="c2c1c-158">測試您的端點</span><span class="sxs-lookup"><span data-stu-id="c2c1c-158">Test Out Your Endpoint</span></span>
<span data-ttu-id="c2c1c-159">對您的新端點重新執行[使用 JEA](using-jea.md)一節中所列的步驟，確認端點如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-159">Re-run the steps listed in the [Using JEA](using-jea.md) section against your new endpoint to confirm it is operating as intended.</span></span>
<span data-ttu-id="c2c1c-160">將設定名稱提供給 `Enter-PSSession` 時，請務必使用新的端點名稱 (JEADemo2)。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-160">Be sure to use the new endpoint name (JEADemo2) when providing the configuration name to `Enter-PSSession`.</span></span>

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEADemo2 -Credential $NonAdminCred
```

## <a name="key-concepts"></a><span data-ttu-id="c2c1c-161">重要概念</span><span class="sxs-lookup"><span data-stu-id="c2c1c-161">Key Concepts</span></span>
<span data-ttu-id="c2c1c-162">**PowerShell 工作階段設定**︰有時稱為 *PowerShell 端點*，這是使用者連線並存取 PowerShell 功能的象徵性「位置」。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-162">**PowerShell Session Configuration**: Sometimes referred to as *PowerShell Endpoint*, this is the figurative "place" where users connect and get access to PowerShell functionality.</span></span>
<span data-ttu-id="c2c1c-163">您可以執行 `Get-PSSessionConfiguration`，列出系統上已登錄的工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-163">You can list the registered Session Configurations on your system by running `Get-PSSessionConfiguration`.</span></span>
<span data-ttu-id="c2c1c-164">以特定方式設定時，PowerShell 工作階段設定可稱為 *JEA 端點*。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-164">When configured in a specific way, a PowerShell Session Configuration can be called a *JEA Endpoint*.</span></span>

<span data-ttu-id="c2c1c-165">**PowerShell 工作階段設定檔 (.pssc)**︰此檔案經登錄後，可定義 PowerShell 工作階段設定的設定。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-165">**PowerShell Session Configuration File (.pssc)**: A file that, when registered, defines settings for a PowerShell Session Configuration.</span></span>
<span data-ttu-id="c2c1c-166">它會包含可連線到端點的使用者角色、「執行身分」虛擬帳戶等規格。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-166">It contains specifications for user roles that can connect to the endpoint, the "run as" Virtual Account, and more.</span></span>     

<span data-ttu-id="c2c1c-167">**角色定義**︰工作階段設定檔中的欄位，定義授與連線使用者的角色功能。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-167">**Role Definitions**: The field in a Session Configuration File that defines the Role Capabilities granted to connecting users.</span></span>
<span data-ttu-id="c2c1c-168">它會定義*誰*可以特殊權限帳戶身分執行*什麼*工作。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-168">It defines *who* can do *what* as a privileged account.</span></span>
<span data-ttu-id="c2c1c-169">這是 JEA RBAC 功能的核心。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-169">This is the core of JEA's RBAC capabilities.</span></span>

<span data-ttu-id="c2c1c-170">**SessionType**：工作階段設定檔中的欄位，表示工作階段設定的預設值。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-170">**SessionType**: A field in a Session Configuration File that represents default settings for a Session Configuration.</span></span>
<span data-ttu-id="c2c1c-171">針對 JEA 端點，這必須設定為 RestrictedRemoteServer。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-171">For JEA endpoints, this must be set to RestrictedRemoteServer.</span></span>

<span data-ttu-id="c2c1c-172">**PowerShell 文字記錄**︰包含 PowerShell 工作階段之 "Over-The-Shoulder" 檢視的檔案。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-172">**PowerShell Transcript**: A file containing an "over-the-shoulder" view of a PowerShell session.</span></span>
<span data-ttu-id="c2c1c-173">您可以將 PowerShell 設定為使用 TranscriptDirectory 欄位來產生 JEA 工作階段的文字記錄。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-173">You can set PowerShell to generate transcripts for JEA sessions using the TranscriptDirectory field.</span></span>
<span data-ttu-id="c2c1c-174">如需文字記錄的詳細資訊，請參閱這篇[部落格文章](https://technet.microsoft.com/en-us/magazine/ff687007.aspx)。</span><span class="sxs-lookup"><span data-stu-id="c2c1c-174">For more information on transcripts, check out this [blog post](https://technet.microsoft.com/en-us/magazine/ff687007.aspx).</span></span>

