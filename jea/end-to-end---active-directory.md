---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "端對端   Active Directory"
ms.technology: powershell
ms.openlocfilehash: 3108f5dad96ef54feb3cf559fae38812ed46849c
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: zh-TW
---
# <a name="end-to-end---active-directory"></a><span data-ttu-id="fe8d5-103">端對端 - Active Directory</span><span class="sxs-lookup"><span data-stu-id="fe8d5-103">End to End - Active Directory</span></span>
<span data-ttu-id="fe8d5-104">假設您的程式範圍已增加。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-104">Imagine the scope of your program has increased.</span></span>
<span data-ttu-id="fe8d5-105">您現在有責任將 JEA 加入網域控制站，以執行 Active Directory 動作。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-105">You are now responsible for adding JEA to Domain Controllers to perform Active Directory actions.</span></span>
<span data-ttu-id="fe8d5-106">技術支援人員將使用 JEA 解除鎖定帳戶、重設密碼，以及執行其他類似動作。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-106">The help desk people are going to use JEA to unlock accounts, reset passwords, and do other similar actions.</span></span>

<span data-ttu-id="fe8d5-107">您必須將一組全新的命令公開給一組不同的人員。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-107">You need to expose a completely new set of commands to a different group of people.</span></span>
<span data-ttu-id="fe8d5-108">除此之外，您還必須公開許多現有的 Active Directory 指令碼。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-108">On top of that, you have a bunch of existing Active Directory scripts you need to expose.</span></span>
<span data-ttu-id="fe8d5-109">本節將逐步引導您撰寫這項工作所需的工作階段設定和角色功能。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-109">This section will walk through authoring a Session Configuration and Role Capability for this task.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fe8d5-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="fe8d5-110">Prerequisites</span></span>
<span data-ttu-id="fe8d5-111">為了逐步進行本節，您必須在網域控制站上執行。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-111">To follow this section step-by-step, you'll need to be operating on a domain controller.</span></span>
<span data-ttu-id="fe8d5-112">如果您無權存取網域控制站，別擔心。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-112">If you don't have access to your domain controller, don't worry.</span></span>
<span data-ttu-id="fe8d5-113">請針對您熟悉的一些其他案例或角色執行，並嘗試跟著做。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-113">Try to follow along with by working against some other scenario or role with which you are familiar.</span></span>
<span data-ttu-id="fe8d5-114">若要快速地設定新的網域控制站，請參閱[建立網域控制站附錄](.\creating-a-domain-controller.md)。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-114">If you want to quickly set up a new domain controller, check out the [Creating a Domain Controller appendix](.\creating-a-domain-controller.md).</span></span>

## <a name="steps-to-make-a-new-role-capability-and-session-configuration"></a><span data-ttu-id="fe8d5-115">建立新的角色功能和工作階段設定的步驟</span><span class="sxs-lookup"><span data-stu-id="fe8d5-115">Steps to Make a new Role Capability and Session Configuration</span></span>

<span data-ttu-id="fe8d5-116">建立新的角色功能乍看之下可能令人卻步，但這項作業可以分成幾個相當簡單的步驟︰</span><span class="sxs-lookup"><span data-stu-id="fe8d5-116">Making a new role capability can seem daunting at first, but it can be broken into fairly simple steps:</span></span>

1.  <span data-ttu-id="fe8d5-117">識別您必須啟用的工作</span><span class="sxs-lookup"><span data-stu-id="fe8d5-117">Identify the tasks you need to enable</span></span>
2.  <span data-ttu-id="fe8d5-118">視需要限制這些工作</span><span class="sxs-lookup"><span data-stu-id="fe8d5-118">Restrict those tasks as necessary</span></span>
3.  <span data-ttu-id="fe8d5-119">確認這些工作適用於 JEA</span><span class="sxs-lookup"><span data-stu-id="fe8d5-119">Confirm they work with JEA</span></span>
4.  <span data-ttu-id="fe8d5-120">將這些工作放在角色功能檔案中</span><span class="sxs-lookup"><span data-stu-id="fe8d5-120">Put them in a Role Capability file</span></span>
5.  <span data-ttu-id="fe8d5-121">登錄公開該角色功能的工作階段設定</span><span class="sxs-lookup"><span data-stu-id="fe8d5-121">Register a Session Configuration that exposes that Role Capability</span></span>

## <a name="step-1-identify-what-needs-to-be-exposed"></a><span data-ttu-id="fe8d5-122">步驟 1︰識別必須公開的內容</span><span class="sxs-lookup"><span data-stu-id="fe8d5-122">Step 1: Identify What Needs to Be Exposed</span></span>
<span data-ttu-id="fe8d5-123">建立新的角色功能或工作階段設定之前，您必須識別使用者需要透過 JEA 端點執行的所有工作，以及如何透過 PowerShell 來執行這些工作。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-123">Before you make a new Role Capability or Session Configuration, you need to identify all of the things users will need to do through the JEA endpoint, as well as how to do them through PowerShell.</span></span>
<span data-ttu-id="fe8d5-124">這涉及相當大量的需求收集和研究。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-124">This will involve a fair amount of requirement gathering and research.</span></span>
<span data-ttu-id="fe8d5-125">您進行此處理程序的方式將取決於您的組織和目標。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-125">How you go about this process will depend on your organization and goals.</span></span>
<span data-ttu-id="fe8d5-126">請注意，需求收集和研究在真實世界的處理程序中是不可或缺的一部分。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-126">It is important to call out requirement gathering and research as a critical part of the real world process.</span></span>
<span data-ttu-id="fe8d5-127">這可能是採用 JEA 的過程中最困難的步驟。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-127">This may be the most difficult step in the process of adopting JEA.</span></span>

### <a name="find-resources"></a><span data-ttu-id="fe8d5-128">尋找資源</span><span class="sxs-lookup"><span data-stu-id="fe8d5-128">Find Resources</span></span>
<span data-ttu-id="fe8d5-129">以下是研究如何建立 Active Directory 管理端點時可參閱的一組線上資源︰</span><span class="sxs-lookup"><span data-stu-id="fe8d5-129">Here is a set of online resources that might have come up in your research on creating an Active Directory management endpoint:</span></span>
-   [<span data-ttu-id="fe8d5-130">Active Directory PowerShell Overview</span><span class="sxs-lookup"><span data-stu-id="fe8d5-130">Active Directory PowerShell Overview</span></span>](http://blogs.msdn.com/b/adpowershell/archive/2009/03/05/active-directory-powershell-overview.aspx) (Active Directory PowerShell 概觀)
-   [<span data-ttu-id="fe8d5-131">CMD to PowerShell Guide for Active Directory</span><span class="sxs-lookup"><span data-stu-id="fe8d5-131">CMD to PowerShell Guide for Active Directory</span></span>](http://blogs.technet.com/b/ashleymcglone/archive/2013/01/02/free-download-cmd-to-powershell-guide-for-ad.aspx) (適用於 Active Directory 的 CMD 到 PowerShell 指南)

### <a name="make-a-list"></a><span data-ttu-id="fe8d5-132">建立清單</span><span class="sxs-lookup"><span data-stu-id="fe8d5-132">Make a List</span></span>
<span data-ttu-id="fe8d5-133">以下是您將在本節其餘部分執行的一組十個動作。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-133">Here is a set of ten actions that you will be working from in the remainder of this section.</span></span>
<span data-ttu-id="fe8d5-134">請記住，這只是範例，您的組織需求可能不同︰</span><span class="sxs-lookup"><span data-stu-id="fe8d5-134">Keep in mind this is simply an example, your organizations requirements may be different:</span></span>

|<span data-ttu-id="fe8d5-135">動作</span><span class="sxs-lookup"><span data-stu-id="fe8d5-135">Action</span></span>                                                         |<span data-ttu-id="fe8d5-136">PowerShell 命令</span><span class="sxs-lookup"><span data-stu-id="fe8d5-136">PowerShell Command</span></span>                                             |
|---------------------------------------------------------------|---------------------------------------------------------------|
|<span data-ttu-id="fe8d5-137">解除鎖定帳戶</span><span class="sxs-lookup"><span data-stu-id="fe8d5-137">Account Unlock</span></span>                                                 |`Unlock-ADAccount`                                             |
|<span data-ttu-id="fe8d5-138">密碼重設</span><span class="sxs-lookup"><span data-stu-id="fe8d5-138">Password Reset</span></span>                                                 |<span data-ttu-id="fe8d5-139">`Set-ADAccountPassword` 和 `Set-ADUser -ChangePasswordAtLogon`</span><span class="sxs-lookup"><span data-stu-id="fe8d5-139">`Set-ADAccountPassword` and `Set-ADUser -ChangePasswordAtLogon`</span></span>|
|<span data-ttu-id="fe8d5-140">變更使用者的職稱</span><span class="sxs-lookup"><span data-stu-id="fe8d5-140">Change a User's Title</span></span>                                          |`Set-ADUser -Title`                                            |  
|<span data-ttu-id="fe8d5-141">尋找已鎖定、已停用、非作用中等 AD 帳戶</span><span class="sxs-lookup"><span data-stu-id="fe8d5-141">Find AD Accounts that are locked out, disabled, inactive, etc.</span></span> |`Search-ADAccount`                                             |
|<span data-ttu-id="fe8d5-142">新增使用者至群組</span><span class="sxs-lookup"><span data-stu-id="fe8d5-142">Add User to Group</span></span>                                              |`Add-ADGroupMember -Identity (with whitelist) -Members`        |
|<span data-ttu-id="fe8d5-143">從群組中移除使用者</span><span class="sxs-lookup"><span data-stu-id="fe8d5-143">Remove User from Group</span></span>                                         |`Remove-ADGroupMember -Identity (with whitelist) -Members`     |
|<span data-ttu-id="fe8d5-144">啟用使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="fe8d5-144">Enable a user account</span></span>                                          |`Enable-ADAccount`                                             |
|<span data-ttu-id="fe8d5-145">停用使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="fe8d5-145">Disable a user account</span></span>                                         |`Disable-ADAccount`                                            |

## <a name="step-2-restrict-tasks-as-necessary"></a><span data-ttu-id="fe8d5-146">步驟 2：視需要限制工作</span><span class="sxs-lookup"><span data-stu-id="fe8d5-146">Step 2: Restrict Tasks as Necessary</span></span>

<span data-ttu-id="fe8d5-147">現在您已有動作清單，您必須仔細思考每個命令的功能。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-147">Now that you have your list of actions, you need to think through the capabilities of each command.</span></span>
<span data-ttu-id="fe8d5-148">這樣做有兩個重要原因︰</span><span class="sxs-lookup"><span data-stu-id="fe8d5-148">There are two important reasons to do this:</span></span>

1.  <span data-ttu-id="fe8d5-149">這樣很容易提供使用者超出預計的功能。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-149">It is easy to give users more capabilities than you intend.</span></span>
<span data-ttu-id="fe8d5-150">例如，`Set-ADUser` 是非常強大且彈性的命令。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-150">For example, `Set-ADUser` is an incredibly powerful and flexible command.</span></span>
<span data-ttu-id="fe8d5-151">您可能不想要向技術支援使用者公開它可以執行的所有工作。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-151">You may not want to expose everything it can do to help desk users.</span></span>  

2.  <span data-ttu-id="fe8d5-152">更糟的是，您可能公開允許使用者擺脫 JEA 限制的命令。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-152">Even worse, it's possible to expose commands that allow users to escape JEA's restrictions.</span></span>
<span data-ttu-id="fe8d5-153">如果發生這種情況，JEA 會停止作為安全性界限。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-153">If this happens, JEA ceases to function as a security boundary.</span></span>
<span data-ttu-id="fe8d5-154">請小心選取命令。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-154">Please be careful when selecting commands.</span></span>
<span data-ttu-id="fe8d5-155">例如，Invoke-Expression 可讓使用者執行不受限制的程式碼。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-155">For example, Invoke-Expression will allow users to run unrestricted code.</span></span>
<span data-ttu-id="fe8d5-156">如需本主題的更多討論，請參閱＜限制命令時的考量＞一節。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-156">For more discussion on this topic, check out the Considerations When Restricting Commands section.</span></span>

<span data-ttu-id="fe8d5-157">檢閱每個命令之後，您決定做出下列限制︰</span><span class="sxs-lookup"><span data-stu-id="fe8d5-157">After reviewing each command, you decide to restrict the following:</span></span>

1.  <span data-ttu-id="fe8d5-158">`Set-ADUser` 只能搭配 -Title 參數執行</span><span class="sxs-lookup"><span data-stu-id="fe8d5-158">`Set-ADUser` should only be allowed to run with the -Title parameter</span></span>

2.  <span data-ttu-id="fe8d5-159">`Add-ADGroupMember` 和 `Remove-ADGroupMember` 只能用於特定群組</span><span class="sxs-lookup"><span data-stu-id="fe8d5-159">`Add-ADGroupMember` and `Remove-ADGroupMember` should only work with certain groups</span></span>

### <a name="step-3-confirm-the-tasks-work-with-jea"></a><span data-ttu-id="fe8d5-160">步驟 3：確認這些工作適用於 JEA</span><span class="sxs-lookup"><span data-stu-id="fe8d5-160">Step 3: Confirm the Tasks Work with JEA</span></span>
<span data-ttu-id="fe8d5-161">在限制的 JEA 環境中可能無法直接實際使用這些 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-161">Actually using those cmdlets may not be straightforward in the restricted JEA environment.</span></span>
<span data-ttu-id="fe8d5-162">JEA 會在 *NoLanguage* 模式下執行，以防止使用者使用變數。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-162">JEA runs in *NoLanguage* mode which, among other things, prevents users from using variables.</span></span>
<span data-ttu-id="fe8d5-163">為了確保使用者有流暢的體驗，請務必檢查一些事項。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-163">In order to ensure that end users have a smooth experience, it's important to check for a few things.</span></span>

<span data-ttu-id="fe8d5-164">例如，請考慮 `Set-ADAccountPassword`。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-164">As an example, consider `Set-ADAccountPassword`.</span></span>
<span data-ttu-id="fe8d5-165">-NewPassword 參數需要安全字串。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-165">The -NewPassword parameter requires a secure string.</span></span>
<span data-ttu-id="fe8d5-166">通常，使用者會建立安全字串並傳入作為變數 (如下所示)︰</span><span class="sxs-lookup"><span data-stu-id="fe8d5-166">Often, users create a secure string and pass it in as a variable (as below):</span></span>

```PowerShell
$newPassword = Read-Host -Prompt "Specify a new password" -AsSecureString
Set-ADAccountPassword -Identity mollyd -NewPassword $newPassword -Reset
```

<span data-ttu-id="fe8d5-167">不過，*NoLanguage* 模式會防止使用變數。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-167">However, *NoLanguage* mode prevents the usage of variables.</span></span>
<span data-ttu-id="fe8d5-168">您可以透過兩個方式來解決這項限制︰</span><span class="sxs-lookup"><span data-stu-id="fe8d5-168">You can get around this restriction in two ways:</span></span>

1.  <span data-ttu-id="fe8d5-169">您可以要求使用者執行命令，而不指派變數。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-169">You can require users run the command without assigning variables.</span></span>
<span data-ttu-id="fe8d5-170">這設定起來很容易，但對於使用端點的操作員可能很麻煩。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-170">This is easy to configure, but can be painful for the operators using the endpoint.</span></span>
<span data-ttu-id="fe8d5-171">誰會想要在您每次重設密碼時輸入此命令？</span><span class="sxs-lookup"><span data-stu-id="fe8d5-171">Who wants to type this out every time you reset a password?</span></span>
```PowerShell
Set-ADAccountPassword -Identity mollyd -NewPassword (Read-Host -Prompt "Specify a new password" -AsSecureString) -Reset
```

2.  <span data-ttu-id="fe8d5-172">您可以透過公開給使用者的指令碼或函式來掩飾此複雜性。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-172">You can wrap the complexity in a script or a function that you expose to end users.</span></span>
<span data-ttu-id="fe8d5-173">您公開的指令碼和函式會在不受限制的內容中執行；您可以撰寫函式來使用變數並呼叫其他命令，而不會發生任何問題。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-173">Scripts and functions that you expose run in an unrestricted context; you can write functions that use variables and call other commands without any issue.</span></span>
<span data-ttu-id="fe8d5-174">這種方法簡化了使用者體驗、避免發生錯誤、減少所需的 PowerShell 知識，並降低不小心公開過多功能的情況。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-174">This approach simplifies the end user experience, prevents errors, reduces required PowerShell knowledge, and reduces unintentionally exposing excess functionality.</span></span>
<span data-ttu-id="fe8d5-175">唯一的缺點就是撰寫和維護函式的成本。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-175">The only downside is the cost of authoring and maintaining the function.</span></span>

### <a name="aside-adding-a-function-to-your-module"></a><span data-ttu-id="fe8d5-176">題外話：新增函式至模組</span><span class="sxs-lookup"><span data-stu-id="fe8d5-176">Aside: Adding a Function to your Module</span></span>
<span data-ttu-id="fe8d5-177">您將採取第二個方法，撰寫稱為 `Reset-ContosoUserPassword` 的 PowerShell 函式。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-177">Taking approach #2, you are going to write a PowerShell function called `Reset-ContosoUserPassword`.</span></span>
<span data-ttu-id="fe8d5-178">此函式將會執行重設使用者的密碼時所需進行的所有作業。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-178">This function is going to do everything that needs to happen when you reset a user's password.</span></span>
<span data-ttu-id="fe8d5-179">在您的組織中，這可能涉及執行精密複雜的作業。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-179">In your organization, this may involve doing fancy and complicated things.</span></span>
<span data-ttu-id="fe8d5-180">因為這只是範例，所以您的命令只會重設密碼，並要求使用者在登入時變更密碼。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-180">Because this is just an example, your command will just reset the password and require the user change the password at logon.</span></span>
<span data-ttu-id="fe8d5-181">我們會將它放入您在最後一節中所建立的 Contoso_AD_Module 模組。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-181">We will put it in the Contoso_AD_Module module you made in the last section.</span></span>

1. <span data-ttu-id="fe8d5-182">在 PowerShell ISE 中，開啟 "Contoso_AD_Module.psm1"</span><span class="sxs-lookup"><span data-stu-id="fe8d5-182">In PowerShell ISE, open "Contoso_AD_Module.psm1"</span></span>
```PowerShell
ise 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psm1'
```

2. <span data-ttu-id="fe8d5-183">按 Crtl+J 開啟程式碼片段功能表。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-183">Press Crtl+J to open the snippets menu.</span></span>

3. <span data-ttu-id="fe8d5-184">按向下鍵直到您找到 [函式]，然後按 Enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-184">Key down until you find "function" and press enter.</span></span>
<span data-ttu-id="fe8d5-185">這會為函式建立非常基本的架構。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-185">This puts up a super basic skeleton of a function.</span></span>

4. <span data-ttu-id="fe8d5-186">將函式重新命名為 "Reset-ContosoUserPassword"。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-186">Rename the function "Reset-ContosoUserPassword".</span></span>  

5. <span data-ttu-id="fe8d5-187">將其中一個參數重新命名為 "Identity"，並刪除第二個參數。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-187">Rename one of the parameters "Identity" and delete the second.</span></span>

6. <span data-ttu-id="fe8d5-188">將下列內容複製到函式主體。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-188">Copy the following into the body of the function.</span></span>
```PowerShell
# Get the new password
$NewPassword = Read-Host -Prompt "Enter a new password" -AsSecureString
# Reset the password
Set-ADAccountPassword -Identity $Identity -NewPassword $NewPassword -Reset
# Require the user to reset at next logon
Set-ADUser -Identity $Identity -ChangePasswordAtLogon
```

7. <span data-ttu-id="fe8d5-189">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-189">Save the file.</span></span>
<span data-ttu-id="fe8d5-190">最後的結果應該如下所示︰</span><span class="sxs-lookup"><span data-stu-id="fe8d5-190">You should end up with something that looks like this:</span></span>
```PowerShell
function Reset-ContosoUserPassword ($Identity)
{
# Get the new password
$NewPassword = Read-Host -Prompt "Enter a new password" -AsSecureString
# Reset the password
Set-ADAccountPassword -Identity $Identity -NewPassword $NewPassword -Reset
# Require the user to reset at next logon
Set-ADUser -Identity $Identity -ChangePasswordAtLogon
}
```
<span data-ttu-id="fe8d5-191">現在，您的使用者只要呼叫 `Reset-ContosoUserPassword`，就能建立內嵌安全字串，而不需要記住此語法。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-191">Now, your users can simply call `Reset-ContosoUserPassword` and not have to remember the syntax to create a secure string inline.</span></span>

## <a name="step-4-edit-the-role-capability-file"></a><span data-ttu-id="fe8d5-192">步驟 4：編輯角色功能檔案</span><span class="sxs-lookup"><span data-stu-id="fe8d5-192">Step 4: Edit the Role Capability File</span></span>
<span data-ttu-id="fe8d5-193">在[建立角色功能](./role-capabilities.md#role-capability-creation)一節中，您已建立空白角色功能檔案。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-193">In the [Role Capability Creation](./role-capabilities.md#role-capability-creation) section, you created a blank Role Capability file.</span></span>
<span data-ttu-id="fe8d5-194">在本節中，您將在該檔案中填入值。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-194">In this section, you will fill in the values in that file.</span></span>

<span data-ttu-id="fe8d5-195">首先在 PowerShell ISE 中開啟角色功能檔案。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-195">Start by opening the role capability file in PowerShell ISE.</span></span>
```PowerShell
ise 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities\ADHelpDesk.psrc'
```
<span data-ttu-id="fe8d5-196">以下列變更更新檔案：</span><span class="sxs-lookup"><span data-stu-id="fe8d5-196">Update the file with the following changes:</span></span>
```PowerShell
# OLD: VisibleCmdlets = 'Invoke-Cmdlet1', @{ Name = 'Invoke-Cmdlet2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }
VisibleCmdlets =
    'Unlock-ADAccount',
    'Search-ADAccount',
    'Enable-ADAccount',
    'Disable-ADAccount',
    @{ Name = 'Set-ADUser'; Parameters = @{ Name = 'Title'; ValidateSet = 'Manager', 'Engineer' }},
    @{ Name = 'Add-ADGroupMember'; Parameters =
        @{Name = 'Identity'; ValidateSet = 'TestGroup'},
        @{Name = 'Members'}},
    @{ Name = 'Remove-ADGroupMember'; Parameters =
        @{Name = 'Identity'; ValidateSet = 'TestGroup'},
        @{Name = 'Members'}}

# OLD: VisibleFunctions = 'Invoke-Function1', @{ Name = 'Invoke-Function2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }
VisibleFunctions = 'Reset-ContosoUserPassword'
```

<span data-ttu-id="fe8d5-197">上述變更有一些注意事項︰</span><span class="sxs-lookup"><span data-stu-id="fe8d5-197">There are a few things to note about the above:</span></span>
1.  <span data-ttu-id="fe8d5-198">PowerShell 會嘗試自動載入您的角色功能所需的模組。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-198">PowerShell will attempt to auto-load the modules needed for your Role Capability.</span></span>
<span data-ttu-id="fe8d5-199">如果您注意到模組發生未自動載入的問題，您可能必須在 "ModulesToImport" 欄位中明確地列出模組名稱。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-199">You may need to explicitly list module names in the "ModulesToImport" field if you notice problems with a module not being autoloaded.</span></span>

2.  <span data-ttu-id="fe8d5-200">如果您不確定命令是 Cmdlet 或函式，請執行 `Get-Command` 並查看 "CommandType" 屬性。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-200">If you aren't sure if a command is a cmdlet or a function, run `Get-Command` and look at the "CommandType" property</span></span>

3.  <span data-ttu-id="fe8d5-201">如果定義一組允許的值並不容易，則 ValidatePattern 可讓您使用規則運算式來限制參數引數。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-201">The ValidatePattern allows you to use a regular expression to restrict parameter arguments if it is not easy to define a set of allowable values.</span></span>
<span data-ttu-id="fe8d5-202">您無法對單一參數同時定義 ValidatePattern 和 ValidateSet。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-202">You cannot define both a ValidatePattern and ValidateSet for a single parameter.</span></span>

## <a name="step-5-register-a-new-session-configuration"></a><span data-ttu-id="fe8d5-203">步驟 5：登錄新的工作階段設定</span><span class="sxs-lookup"><span data-stu-id="fe8d5-203">Step 5: Register a new Session Configuration</span></span>
<span data-ttu-id="fe8d5-204">接下來，您將建立新的工作階段設定檔，該檔案會向 "JEA_NonAdmin_HelpDesk" AD 群組的成員公開您的角色功能。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-204">Next, you will create a new session configuration file that will expose your Role Capability to members of the "JEA_NonAdmin_HelpDesk" AD group.</span></span>

<span data-ttu-id="fe8d5-205">首先在 PowerShell ISE 中建立及開啟新的空白工作階段設定檔。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-205">Start by creating and opening a new blank Session Configuration file in PowerShell ISE.</span></span>
```PowerShell
New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
ise "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
```
<span data-ttu-id="fe8d5-206">修改 PSSC 檔案中的下列欄位。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-206">Modify the following fields in the PSSC file.</span></span>
<span data-ttu-id="fe8d5-207">如果您在自己的環境中執行，則應該以您自己的非系統管理員使用者或群組取代 "CONTOSO\JEA_NonAdmins_Helpdesk"。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-207">If you are working in your own environment, you should replace "CONTOSO\JEA_NonAdmins_Helpdesk" with your own non-administrator user or group.</span></span>
```PowerShell
# OLD: Description = ''
Description = 'An endpoint for Active Directory tasks.'

# OLD: SessionType = 'Default'
SessionType = 'RestrictedRemoteServer'

# OLD: TranscriptDirectory = 'C:\Transcripts\'
TranscriptDirectory = "C:\ProgramData\JEAConfiguration\Transcripts"

# OLD: RunAsVirtualAccount = $true
RunAsVirtualAccount = $true

# OLD: RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }
RoleDefinitions = @{ 'CONTOSO\JEA_NonAdmin_HelpDesk' = @{ RoleCapabilities =  'ADHelpDesk' }}
```
<span data-ttu-id="fe8d5-208">儲存並登錄工作階段設定</span><span class="sxs-lookup"><span data-stu-id="fe8d5-208">Save and register the Session Configuration</span></span>
```PowerShell
Register-PSSessionConfiguration -Name ADHelpDesk -Path "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
```
## <a name="test-it-out"></a><span data-ttu-id="fe8d5-209">測試看看！</span><span class="sxs-lookup"><span data-stu-id="fe8d5-209">Test It Out!</span></span>
<span data-ttu-id="fe8d5-210">取得您的非系統管理員使用者認證︰</span><span class="sxs-lookup"><span data-stu-id="fe8d5-210">Get your non-administrator user credentials:</span></span>
```PowerShell
$HelpDeskCred = Get-Credential
```
<span data-ttu-id="fe8d5-211">如果您遵循[設定使用者和群組](creating-a-domain-controller.md#set-up-users-and-groups)一節進行，則認證會是︰</span><span class="sxs-lookup"><span data-stu-id="fe8d5-211">If you followed the [Set Up Users and Groups](creating-a-domain-controller.md#set-up-users-and-groups) section, the credentials will be:</span></span>
-   <span data-ttu-id="fe8d5-212">使用者名稱 = "HelpDeskUser"</span><span class="sxs-lookup"><span data-stu-id="fe8d5-212">Username = "HelpDeskUser"</span></span>
-   <span data-ttu-id="fe8d5-213">密碼 = "pa$$w0rd"</span><span class="sxs-lookup"><span data-stu-id="fe8d5-213">Password = "pa$$w0rd"</span></span>

<span data-ttu-id="fe8d5-214">使用非系統管理員認證從遠端登入 AD 技術支援端點︰</span><span class="sxs-lookup"><span data-stu-id="fe8d5-214">Remote into the ADHelpdesk endpoint using the non-admin credential:</span></span>
```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName ADHelpDesk -Credential $HelpDeskCred
```
<span data-ttu-id="fe8d5-215">使用 Set-ADUser 重設使用者的職稱。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-215">Use Set-ADUser to reset a user's title.</span></span>
```PowerShell
Set-ADUser -Identity OperatorUser -Title Engineer
```
<span data-ttu-id="fe8d5-216">確認標題已變更。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-216">Verify that the title has changed.</span></span>
```PowerShell
Get-ADUser -Identity OperatorUser -Property Title
```
<span data-ttu-id="fe8d5-217">現在，使用 Add-ADGroupMember 將新增使用者至 TestGroup。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-217">Now, use Add-ADGroupMember to add a user to the TestGroup.</span></span>
<span data-ttu-id="fe8d5-218">注意︰請確定您已事先建立 TestGroup。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-218">Note: make sure you've created the TestGroup beforehand.</span></span>
```PowerShell
Add-ADGroupMember TestGroup -Member OperatorUser -Verbose
```
<span data-ttu-id="fe8d5-219">結束工作階段︰</span><span class="sxs-lookup"><span data-stu-id="fe8d5-219">Exit the session:</span></span>
```PowerShell
Exit-PSSession
```
## <a name="key-concepts"></a><span data-ttu-id="fe8d5-220">重要概念</span><span class="sxs-lookup"><span data-stu-id="fe8d5-220">Key Concepts</span></span>
<span data-ttu-id="fe8d5-221">**NoLanguage 模式**：當 PowerShell 在 "NoLanguage" 模式時，使用者只能執行命令，而不能使用任何語言項目。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-221">**NoLanguage Mode**: When PowerShell is in "NoLanguage" mode, users may only run commands; they cannot use any language elements.</span></span>
<span data-ttu-id="fe8d5-222">如需詳細資訊，請執行 `Get-Help about_Language_Modes`。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-222">For more information, run `Get-Help about_Language_Modes`.</span></span>

<span data-ttu-id="fe8d5-223">**PowerShell 函式**：PowerShell 函式是您可以透過名稱呼叫的 PowerShell 程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-223">**PowerShell Functions**: PowerShell functions are bits of PowerShell code that you can call by name.</span></span>
<span data-ttu-id="fe8d5-224">如需詳細資訊，請執行 `Get-Help about_Functions`。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-224">For more information, run `Get-Help about_Functions`.</span></span>

<span data-ttu-id="fe8d5-225">**ValidateSet/ValidatePattern**︰公開命令時，您可以限制特定參數的有效引數。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-225">**ValidateSet/ValidatePattern**: When exposing a command, you can restrict valid arguments for specific parameters.</span></span>
<span data-ttu-id="fe8d5-226">ValidateSet 是有效引數的特定清單。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-226">A ValidateSet is a specific list of valid arguments.</span></span>
<span data-ttu-id="fe8d5-227">ValidatePattern 是該參數引數必須符合的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="fe8d5-227">A ValidatePattern is a regular expression that the arguments for that parameter must match.</span></span>

