---
ms.date: 06/12/2017
author: rpsqrd
ms.topic: conceptual
keywords: jea,powershell,安全性
title: JEA 角色功能
ms.openlocfilehash: bd6d61443faf30e4056930a010103e6807c015c9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="jea-role-capabilities"></a><span data-ttu-id="4f271-103">JEA 角色功能</span><span class="sxs-lookup"><span data-stu-id="4f271-103">JEA Role Capabilities</span></span>

> <span data-ttu-id="4f271-104">適用對象：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4f271-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="4f271-105">建立 JEA 端點時，您必須定義一或多個「角色功能」，描述某人可以在 JEA 工作階段中做「什麼」。</span><span class="sxs-lookup"><span data-stu-id="4f271-105">When creating a JEA endpoint, you will need to define one or more "role capabilities" which describe *what* someone can do in a JEA session.</span></span>
<span data-ttu-id="4f271-106">角色功能是具有 .psrc 副檔名的 PowerShell 資料檔案，列出應該供連線使用者使用的所有 Cmdlet、函式、提供者，以及外部程式。</span><span class="sxs-lookup"><span data-stu-id="4f271-106">A role capability is a PowerShell data file with the .psrc extension that lists all the cmdlets, functions, providers, and external programs that should be made available to connecting users.</span></span>

<span data-ttu-id="4f271-107">本主題說明如何建立 JEA 使用者的 PowerShell 角色功能檔案。</span><span class="sxs-lookup"><span data-stu-id="4f271-107">This topic describes how to create a PowerShell role capability file for your JEA users.</span></span>

## <a name="determine-which-commands-to-allow"></a><span data-ttu-id="4f271-108">決定允許哪些命令</span><span class="sxs-lookup"><span data-stu-id="4f271-108">Determine which commands to allow</span></span>

<span data-ttu-id="4f271-109">建立角色功能檔案時的第一步是考慮被指派該角色的使用者將需要存取什麼。</span><span class="sxs-lookup"><span data-stu-id="4f271-109">The first step when creating a role capability file is to consider what the users who are assigned the role will need access to.</span></span>
<span data-ttu-id="4f271-110">這項需求收集程序可能需要一段時間，但這是非常重要的程序。</span><span class="sxs-lookup"><span data-stu-id="4f271-110">This requirements gathering process can take a while, but it is a very important process.</span></span>
<span data-ttu-id="4f271-111">提供使用者太少 Cmdlet 和函式的存取權，可能會使他們無法完成工作。</span><span class="sxs-lookup"><span data-stu-id="4f271-111">Giving users access to too few cmdlets and functions can prevent them from getting their job done.</span></span>
<span data-ttu-id="4f271-112">允許存取太多 Cmdlet 和函式則可能會導致使用者執行比您想要其隱含系統管理員權限更多的事情，削弱您的安全性立場。</span><span class="sxs-lookup"><span data-stu-id="4f271-112">Allowing access to too many cmdlets and functions can lead to users doing more than you intended with their implicit admin privileges, weakening your security stance.</span></span>

<span data-ttu-id="4f271-113">您如何執行此程序將取決於您的組織和目標，但下列秘訣可以協助確保您的路徑正確。</span><span class="sxs-lookup"><span data-stu-id="4f271-113">How you go about this process will depend on your organization and goals, however the following tips can help ensure you're on the right path.</span></span>

1. <span data-ttu-id="4f271-114">**識別**使用者用來完成工作的命令。</span><span class="sxs-lookup"><span data-stu-id="4f271-114">**Identify** the commands users are using to get their jobs done.</span></span> <span data-ttu-id="4f271-115">這可能需要調查 IT 人員、檢查自動化指令碼，或分析 PowerShell 工作階段文字記錄或記錄檔。</span><span class="sxs-lookup"><span data-stu-id="4f271-115">This may involve surveying IT staff, checking automation scripts, or analyzing PowerShell session transcripts or logs.</span></span>
2. <span data-ttu-id="4f271-116">可能的話，將命令列工具的使用**更新**為 PowerShell 對等用法，以得到最佳的稽核和 JEA 自訂體驗。</span><span class="sxs-lookup"><span data-stu-id="4f271-116">**Update** use of command line tools to PowerShell equivalents, where possible, for the best auditing and JEA customization experience.</span></span> <span data-ttu-id="4f271-117">外部程式無法像原生 PowerShell Cmdlet 和 JEA 函式那樣精細地限制。</span><span class="sxs-lookup"><span data-stu-id="4f271-117">External programs cannot be constrained as granularly as native PowerShell cmdlets and functions in JEA.</span></span>
3. <span data-ttu-id="4f271-118">視需要**限制** Cmdlet 的範圍，只允許特定的參數或參數值。</span><span class="sxs-lookup"><span data-stu-id="4f271-118">**Restrict** the scope of the cmdlets if necessary to only allow specific parameters or parameter values.</span></span> <span data-ttu-id="4f271-119">如果使用者應該只能管理系統的一部分，這點尤其重要。</span><span class="sxs-lookup"><span data-stu-id="4f271-119">This is particularly important if users should only be able to manage part of a system.</span></span>
4. <span data-ttu-id="4f271-120">**建立**自訂函式，取代複雜命令或 JEA 中難以限制的命令。</span><span class="sxs-lookup"><span data-stu-id="4f271-120">**Create** custom functions to replace complex commands or commands which are difficult to constrain in JEA.</span></span> <span data-ttu-id="4f271-121">包裝複雜命令或套用額外驗證邏輯的簡單函式，可以提供系統管理員更多的控制，以及使用者的簡便性。</span><span class="sxs-lookup"><span data-stu-id="4f271-121">A simple function that wraps a complex command or applies additional validation logic can offer additional control for admins and end-user simplicity.</span></span>
5. <span data-ttu-id="4f271-122">**測試**使用者和/或自動化服務允許命令的範圍清單，並視需要調整。</span><span class="sxs-lookup"><span data-stu-id="4f271-122">**Test** the scoped list of allowable commands with your users and/or automation services and adjust as necessary.</span></span>

<span data-ttu-id="4f271-123">請務必記得，JEA 工作階段中的命令通常會使用系統管理員 (或以其他方式提高權限) 的權限來執行。</span><span class="sxs-lookup"><span data-stu-id="4f271-123">It is important to remember that commands in a JEA session are often run with admin (or otherwise elevated) privileges.</span></span>
<span data-ttu-id="4f271-124">謹慎地選取可用的命令，對於確定 JEA 端點不會允許連線使用者提升其權限而言很重要。</span><span class="sxs-lookup"><span data-stu-id="4f271-124">Careful selection of available commands is important to ensure the JEA endpoint does not allow the connecting user to elevate their permissions.</span></span>
<span data-ttu-id="4f271-125">以下是一些命令範例，如果允許其為未受限制的狀態，將可能惡意地使用它們。</span><span class="sxs-lookup"><span data-stu-id="4f271-125">Below are some examples of commands that can be used maliciously if allowed in an unconstrained state.</span></span>
<span data-ttu-id="4f271-126">請注意，這不是詳盡的清單，應該僅作為警告的起點。</span><span class="sxs-lookup"><span data-stu-id="4f271-126">Note that this is not an exhaustive list and should only be used as a cautionary starting point.</span></span>

### <a name="examples-of-potentially-dangerous-commands"></a><span data-ttu-id="4f271-127">有潛在危險的命令範例</span><span class="sxs-lookup"><span data-stu-id="4f271-127">Examples of potentially dangerous commands</span></span>

<span data-ttu-id="4f271-128">風險</span><span class="sxs-lookup"><span data-stu-id="4f271-128">Risk</span></span> | <span data-ttu-id="4f271-129">範例</span><span class="sxs-lookup"><span data-stu-id="4f271-129">Example</span></span> | <span data-ttu-id="4f271-130">相關的命令</span><span class="sxs-lookup"><span data-stu-id="4f271-130">Related commands</span></span>
-----|---------|-----------------
<span data-ttu-id="4f271-131">授與連線使用者系統管理員權限以略過 JEA</span><span class="sxs-lookup"><span data-stu-id="4f271-131">Granting the connecting user admin privileges to bypass JEA</span></span> | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | <span data-ttu-id="4f271-132">`Add-ADGroupMember`、`Add-LocalGroupMember`、`net.exe`、`dsadd.exe`</span><span class="sxs-lookup"><span data-stu-id="4f271-132">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span></span>
<span data-ttu-id="4f271-133">執行任意程式碼，例如惡意程式碼、入侵或自訂指令碼來略過防護</span><span class="sxs-lookup"><span data-stu-id="4f271-133">Running arbitrary code, such as malware, exploits, or custom scripts to bypass protections</span></span> | `Start-Process -FilePath '\\san\share\malware.exe'` | <span data-ttu-id="4f271-134">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span><span class="sxs-lookup"><span data-stu-id="4f271-134">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span></span>

## <a name="create-a-role-capability-file"></a><span data-ttu-id="4f271-135">建立角色功能檔案</span><span class="sxs-lookup"><span data-stu-id="4f271-135">Create a role capability file</span></span>

<span data-ttu-id="4f271-136">您可以使用 [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) Cmdlet 建立新的 PowerShell 角色功能檔案。</span><span class="sxs-lookup"><span data-stu-id="4f271-136">You can create a new PowerShell role capability file with the [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet.</span></span>

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

<span data-ttu-id="4f271-137">所產生的角色功能檔案可以在文字編輯器中開啟並修改，以允許角色所需的命令。</span><span class="sxs-lookup"><span data-stu-id="4f271-137">The resulting role capability file can be opened in a text editor and modified to allow the desired commands for the role.</span></span>
<span data-ttu-id="4f271-138">PowerShell 說明文件包含數個檔案設定方式的範例。</span><span class="sxs-lookup"><span data-stu-id="4f271-138">The PowerShell help documentation contains several examples of how you can configure the file.</span></span>

### <a name="allowing-powershell-cmdlets-and-functions"></a><span data-ttu-id="4f271-139">允許 PowerShell Cmdlet 和函式</span><span class="sxs-lookup"><span data-stu-id="4f271-139">Allowing PowerShell cmdlets and functions</span></span>

<span data-ttu-id="4f271-140">若要授權使用者執行 PowerShell Cmdlet 或函式、新增 Cmdlet 或函式名稱至 VisbibleCmdlets 或 VisibleFunctions 欄位。</span><span class="sxs-lookup"><span data-stu-id="4f271-140">To authorize users to run PowerShell cmdlets or functions, add the cmdlet or function name to the VisbibleCmdlets or VisibleFunctions fields.</span></span>
<span data-ttu-id="4f271-141">如果您不確定命令是 Cmdlet 或函式，可以執行 `Get-Command <name>` 並檢查輸出中的 "CommandType" 屬性。</span><span class="sxs-lookup"><span data-stu-id="4f271-141">If you aren't sure whether a command is a cmdlet or function, you can run `Get-Command <name>` and check the "CommandType" property in the output.</span></span>

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

<span data-ttu-id="4f271-142">有時候特定 Cmdlet 或函式的範圍對於您使用者的需求而言過於廣泛。</span><span class="sxs-lookup"><span data-stu-id="4f271-142">Sometimes the scope of a specific cmdlet or function is too broad for your users' needs.</span></span>
<span data-ttu-id="4f271-143">例如，DNS 系統管理員可能只需要重新啟動 DNS 服務的存取權。</span><span class="sxs-lookup"><span data-stu-id="4f271-143">A DNS admin, for example, probably only needs access to restart the DNS service.</span></span>
<span data-ttu-id="4f271-144">在多租用戶環境中，租用戶被授與自我服務管理工具的存取權，並且應該受限於管理自己的資源。</span><span class="sxs-lookup"><span data-stu-id="4f271-144">In a multi-tenant environment where tenants are granted access to self-service management tools, tenants should be limited to managing with their own resources.</span></span>
<span data-ttu-id="4f271-145">在這些情況下，您可以限制從 Cmdlet 或函式公開哪些參數。</span><span class="sxs-lookup"><span data-stu-id="4f271-145">For these cases, you can restrict which parameters are exposed from the cmdlet or function.</span></span>

```powershell

VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}

```

<span data-ttu-id="4f271-146">在進階情況中，您可能也需要限制某人可以提供給這些參數的值。</span><span class="sxs-lookup"><span data-stu-id="4f271-146">In more advanced scenarios, you may also need to restrict which values someone can supply to these parameters.</span></span>
<span data-ttu-id="4f271-147">角色功能可讓您定義一組允許的值或評估以決定是否允許指定輸入的規則運算式模式。</span><span class="sxs-lookup"><span data-stu-id="4f271-147">Role capabilities let you define a set of allowed values or a regular expression pattern that is evaluated to determine if a given input is allowed.</span></span>

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> <span data-ttu-id="4f271-148">一律會允許[一般的 PowerShell 參數](https://technet.microsoft.com/library/hh847884.aspx)，即使是您限制了可用的參數。</span><span class="sxs-lookup"><span data-stu-id="4f271-148">The [common PowerShell parameters](https://technet.microsoft.com/library/hh847884.aspx) are always allowed, even if you restrict the available parameters.</span></span>
> <span data-ttu-id="4f271-149">您不應該將其明確列在 Parameters 欄位中。</span><span class="sxs-lookup"><span data-stu-id="4f271-149">You should not explicitly list them in the Parameters field.</span></span>

<span data-ttu-id="4f271-150">下表說明您可以自訂可見 Cmdlet 或函式的各種方式。</span><span class="sxs-lookup"><span data-stu-id="4f271-150">The table below describes the various ways you can customize a visible cmdlet or function.</span></span>
<span data-ttu-id="4f271-151">您可以在 VisibleCmdlets 欄位中混搭下列任何項目。</span><span class="sxs-lookup"><span data-stu-id="4f271-151">You can mix and match any of the below in the VisibleCmdlets field.</span></span>

<span data-ttu-id="4f271-152">範例</span><span class="sxs-lookup"><span data-stu-id="4f271-152">Example</span></span>                                                                                      | <span data-ttu-id="4f271-153">使用案例</span><span class="sxs-lookup"><span data-stu-id="4f271-153">Use case</span></span>
---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------
<span data-ttu-id="4f271-154">`'My-Func'` 或 `@{ Name = 'My-Func' }`</span><span class="sxs-lookup"><span data-stu-id="4f271-154">`'My-Func'` or `@{ Name = 'My-Func' }`</span></span>                                                       | <span data-ttu-id="4f271-155">允許使用者執行 `My-Func` 而無任何參數限制。</span><span class="sxs-lookup"><span data-stu-id="4f271-155">Allows the user to run `My-Func` without any restrictions on the parameters.</span></span>
`'MyModule\My-Func'`                                                                         | <span data-ttu-id="4f271-156">允許使用者從模組 `MyModule` 執行 `My-Func` 而無任何參數限制。</span><span class="sxs-lookup"><span data-stu-id="4f271-156">Allows the user to run `My-Func` from the module `MyModule` without any restrictions on the parameters.</span></span>
`'My-*'`                                                                                     | <span data-ttu-id="4f271-157">允許使用者使用動詞 `My` 執行任何 Cmdlet 或函式。</span><span class="sxs-lookup"><span data-stu-id="4f271-157">Allows the user to run any cmdlet or function with the verb `My`.</span></span>
`'*-Func'`                                                                                   | <span data-ttu-id="4f271-158">允許使用者使用名詞 `Func` 執行任何 Cmdlet 或函式。</span><span class="sxs-lookup"><span data-stu-id="4f271-158">Allows the user to run any cmdlet or function with the noun `Func`.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`               | <span data-ttu-id="4f271-159">允許使用者執行 `My-Func` 搭配 `Param1` 和/或 `Param2` 參數。</span><span class="sxs-lookup"><span data-stu-id="4f271-159">Allows the user to run `My-Func` with the `Param1` and/or `Param2` parameters.</span></span> <span data-ttu-id="4f271-160">可以提供任何值給參數。</span><span class="sxs-lookup"><span data-stu-id="4f271-160">Any value can be supplied to the parameters.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}`  | <span data-ttu-id="4f271-161">允許使用者執行 `My-Func` 搭配 `Param1` 參數。</span><span class="sxs-lookup"><span data-stu-id="4f271-161">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="4f271-162">只能提供 "Value1" 和 "Value2" 給參數。</span><span class="sxs-lookup"><span data-stu-id="4f271-162">Only "Value1" and "Value2" can be supplied to the parameter.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`     | <span data-ttu-id="4f271-163">允許使用者執行 `My-Func` 搭配 `Param1` 參數。</span><span class="sxs-lookup"><span data-stu-id="4f271-163">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="4f271-164">可以提供開頭為 "contoso" 的任何值給參數。</span><span class="sxs-lookup"><span data-stu-id="4f271-164">Any value starting with "contoso" can be supplied to the parameter.</span></span>


> [!WARNING]
> <span data-ttu-id="4f271-165">關於最佳安全性做法，不建議在定義可見 Cmdlet 或函式時使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="4f271-165">For best security practices, it is not recommended to use wildcards when defining visible cmdlets or functions.</span></span>
> <span data-ttu-id="4f271-166">相反地，您應該明確列出每個受信任的命令，以確保沒有其他共用相同命名配置的命令意外地獲得授權。</span><span class="sxs-lookup"><span data-stu-id="4f271-166">Instead, you should explicitly list each trusted command to ensure no other commands that share the same naming scheme are unintentionally authorized.</span></span>

<span data-ttu-id="4f271-167">您無法將 ValidatePattern 和 ValidateSet 同時套用至相同的 Cmdlet 或函式。</span><span class="sxs-lookup"><span data-stu-id="4f271-167">You cannot apply both a ValidatePattern and ValidateSet to the same cmdlet or function.</span></span>

<span data-ttu-id="4f271-168">如果您這樣做，ValidatePattern 會覆寫 ValidateSet。</span><span class="sxs-lookup"><span data-stu-id="4f271-168">If you do, the ValidatePattern will override the ValidateSet.</span></span>

<span data-ttu-id="4f271-169">如需 ValidatePattern 的詳細資訊，請參閱[這篇 *Hey, Scripting Guy!* 文章](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/)和 [PowerShell 規則運算式](https://technet.microsoft.com/library/hh847880.aspx)參考內容。</span><span class="sxs-lookup"><span data-stu-id="4f271-169">For more information about ValidatePattern, check out [this *Hey, Scripting Guy!* post](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) and the [PowerShell Regular Expressions](https://technet.microsoft.com/library/hh847880.aspx) reference content.</span></span>

### <a name="allowing-external-commands-and-powershell-scripts"></a><span data-ttu-id="4f271-170">允許外部命令及 PowerShell 指令碼</span><span class="sxs-lookup"><span data-stu-id="4f271-170">Allowing external commands and PowerShell scripts</span></span>

<span data-ttu-id="4f271-171">若要允許使用者在 JEA 工作階段中執行可執行檔和 PowerShell 指令碼 (.ps1)，您必須在 VisibleExternalCommands 欄位中新增每個程式的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="4f271-171">To allow users to run executables and PowerShell scripts (.ps1) in a JEA session, you have to add the full path to each program in the VisibleExternalCommands field.</span></span>

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

<span data-ttu-id="4f271-172">建議您，在可能的情況下，使用任何外部可執行檔的對等 PowerShell Cmdlet/函式，因為您可以控制 PowerShell Cmdlet/函式允許哪些參數。</span><span class="sxs-lookup"><span data-stu-id="4f271-172">It is advised, where possible, to use PowerShell cmdlet/function equivalents of any external executables you authorize since you have control over which parameters are allowed with PowerShell cmdlets/functions.</span></span>

<span data-ttu-id="4f271-173">許多可執行檔允許您讀取目前的狀態，然後提供不同參數來變更它。</span><span class="sxs-lookup"><span data-stu-id="4f271-173">Many executables allow you to both read the current state and then change it just by providing different parameters.</span></span>

<span data-ttu-id="4f271-174">例如，請考慮檔案伺服器系統管理員的角色，系統管理員想要檢查本機電腦裝載哪些網路共用。</span><span class="sxs-lookup"><span data-stu-id="4f271-174">For example, consider the role of a file server admin who wants to check which network shares are hosted by the local machine.</span></span>
<span data-ttu-id="4f271-175">其中一個檢查方式是使用 `net share`。</span><span class="sxs-lookup"><span data-stu-id="4f271-175">One way to check is to use `net share`.</span></span>
<span data-ttu-id="4f271-176">不過，允許 net.exe 非常危險，因為系統管理員可以輕鬆地以 `net group Administrators unprivilegedjeauser /add` 使用命令取得系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="4f271-176">However, allowing net.exe is very dangerous becuase the admin could just as easily use the command to gain admin privileges with `net group Administrators unprivilegedjeauser /add`.</span></span>
<span data-ttu-id="4f271-177">更好的方法是允許 [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx)，這可達到相同的結果，但範圍的限制多了許多。</span><span class="sxs-lookup"><span data-stu-id="4f271-177">A better approach is to allow [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx) which achieves the same result but has a much more limited scope.</span></span>

<span data-ttu-id="4f271-178">當提供外部命令給使用者在 JEA 工作階段中使用時，請一律指定可執行檔的完整路徑，以確保不會改為執行放置在系統上別處、名稱類似 (且可能惡意) 的程式。</span><span class="sxs-lookup"><span data-stu-id="4f271-178">When making external commands available to users in a JEA session, always specify the complete path to the executable to ensure a similarly named (and potentially malicous) program placed elsewhere on the system does not get executed instead.</span></span>

### <a name="allowing-access-to-powershell-providers"></a><span data-ttu-id="4f271-179">允許存取 PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="4f271-179">Allowing access to PowerShell providers</span></span>

<span data-ttu-id="4f271-180">根據預設，在 JEA 工作階段中不能使用 PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="4f271-180">By default, no PowerShell providers are available in JEA sessions.</span></span>

<span data-ttu-id="4f271-181">這主要是為了降低機密資訊和設定被公開給連線使用者的風險。</span><span class="sxs-lookup"><span data-stu-id="4f271-181">This is primarily to reduce the risk of sensitive information and configuration settings being disclosed to the connecting user.</span></span>

<span data-ttu-id="4f271-182">如有必要，您可以使用 `VisibleProviders` 命令允許存取 PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="4f271-182">When necessary, you can allow access to the PowerShell providers using the `VisibleProviders` command.</span></span>
<span data-ttu-id="4f271-183">如需完整的提供者清單，請執行 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="4f271-183">For a full list of providers, run `Get-PSProvider`.</span></span>

```powershell
VisibleProviders = 'Registry'
```

<span data-ttu-id="4f271-184">針對需要存取檔案系統、登錄、憑證存放區或其他機密提供者的簡單工作，您也可以考慮撰寫代表使用者與提供者合作的自訂函式。</span><span class="sxs-lookup"><span data-stu-id="4f271-184">For simple tasks that require access to the file system, registry, certificate store, or other sensitive providers, you can also consider writing a custom function that works with the provider on the user's behalf.</span></span>
<span data-ttu-id="4f271-185">函式、Cmdlet 和 JEA 工作階段中可用的外部程式不受限於與 JEA 相同的條件約束 -- 它們預設可以存取任何提供者。</span><span class="sxs-lookup"><span data-stu-id="4f271-185">Functions, cmdlets, and external programs that are available in a JEA session are not subject to the same constraints as JEA -- they can access any provider by default.</span></span>
<span data-ttu-id="4f271-186">另外也請考慮當需要在與 JEA 端點之間複製檔案時，使用[使用者磁碟機](session-configurations.md#user-drive)。</span><span class="sxs-lookup"><span data-stu-id="4f271-186">Also consider using the [user drive](session-configurations.md#user-drive) when copying files to/from a JEA endpoint is required.</span></span>

### <a name="creating-custom-functions"></a><span data-ttu-id="4f271-187">建立自訂函式</span><span class="sxs-lookup"><span data-stu-id="4f271-187">Creating custom functions</span></span>

<span data-ttu-id="4f271-188">您可以在角色功能檔案中撰寫自訂函式，簡化一般使用者的複雜工作。</span><span class="sxs-lookup"><span data-stu-id="4f271-188">You can author custom functions in a role capability file to simplify complex tasks for your end users.</span></span>
<span data-ttu-id="4f271-189">當您需要 Cmdlet 參數值的進階驗證邏輯時，自訂函式也十分有用。</span><span class="sxs-lookup"><span data-stu-id="4f271-189">Custom functions are also useful when you require advanced validation logic for cmdlet parameter values.</span></span>
<span data-ttu-id="4f271-190">您可以在 **FunctionDefinitions** 欄位中撰寫簡單的函式︰</span><span class="sxs-lookup"><span data-stu-id="4f271-190">You can write simple functions in the **FunctionDefinitions** field:</span></span>

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending | Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> <span data-ttu-id="4f271-191">別忘了將您的自訂函式名稱新增至 **VisibleFunctions** 欄位，以便 JEA 使用者可以執行它們。</span><span class="sxs-lookup"><span data-stu-id="4f271-191">Don't forget to add the name of your custom functions to the **VisibleFunctions** field so they can be run by the JEA users.</span></span>


<span data-ttu-id="4f271-192">自訂函式主體 (指令碼區塊) 會以系統的預設語言模式執行，而且不受限於 JEA 的語言條件約束。</span><span class="sxs-lookup"><span data-stu-id="4f271-192">The body (script block) of custom functions runs in the default language mode for the system and is not subject to JEA's language constraints.</span></span>
<span data-ttu-id="4f271-193">這表示函式可以存取檔案系統和登錄，並執行角色功能檔案中未設為可見的命令。</span><span class="sxs-lookup"><span data-stu-id="4f271-193">This means that functions can access the file system and registry, and run commands that were not made visible in the role capability file.</span></span>
<span data-ttu-id="4f271-194">請小心避免允許在使用參數時執行任意程式碼，並避免直接將使用者輸入以管線送到 Cmdlet，例如 `Invoke-Expression`。</span><span class="sxs-lookup"><span data-stu-id="4f271-194">Take care to avoid allowing arbitrary code to be run when using parameters and avoid piping user input directly into cmdlets like `Invoke-Expression`.</span></span>

<span data-ttu-id="4f271-195">在上述範例中，您會發現，使用了完整的模組名稱 (FQMN) `Microsoft.PowerShell.Utility\Select-Object`，而不是使用速記的 `Select-Object`。</span><span class="sxs-lookup"><span data-stu-id="4f271-195">In the above example, you will notice that the fully qualified module name (FQMN) `Microsoft.PowerShell.Utility\Select-Object` was used instead of the shorthand `Select-Object`.</span></span>
<span data-ttu-id="4f271-196">角色功能檔案中定義的函式仍受限於 JEA 工作階段的範圍，包括 JEA 建立來限制現有命令的 Proxy 函式。</span><span class="sxs-lookup"><span data-stu-id="4f271-196">Functions defined in role capability files are still subject to the scope of JEA sessions, which includes the proxy functions JEA creates to constrain existing commands.</span></span>

<span data-ttu-id="4f271-197">Select-Object 是所有 JEA 工作階段中受限制的預設 Cmdlet，它不允許您選取物件上的任何屬性。</span><span class="sxs-lookup"><span data-stu-id="4f271-197">Select-Object is a default, constrained cmdlet in all JEA sessions that doesn't allow you to select arbitrary properties on objects.</span></span>
<span data-ttu-id="4f271-198">若要使用未受限制的 Select-Object，您必須指定 FQMN，以明確地要求完整實作。</span><span class="sxs-lookup"><span data-stu-id="4f271-198">To use the unconstrained Select-Object in functions, you must explicitly request the full implementation by specifying the FQMN.</span></span>
<span data-ttu-id="4f271-199">JEA 工作階段中的任何受限制 Cmdlet 從函式叫用時會展現相同行為，與 PowerShell 的[命令優先順序](https://msdn.microsoft.com/en-us/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence)一致。</span><span class="sxs-lookup"><span data-stu-id="4f271-199">Any constrained cmdlet in a JEA session will exhibit the same behavior when invoked from a function, in line with PowerShell's [command precedence](https://msdn.microsoft.com/en-us/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).</span></span>

<span data-ttu-id="4f271-200">如果您要撰寫大量自訂函式，將它們放在 [PowerShell 指令碼模組](https://msdn.microsoft.com/en-us/library/dd878340(v=vs.85).aspx)可能會比較輕鬆。</span><span class="sxs-lookup"><span data-stu-id="4f271-200">If you are writing a lot of custom functions, it may be easier to put them in a [PowerShell Script Module](https://msdn.microsoft.com/en-us/library/dd878340(v=vs.85).aspx).</span></span>
<span data-ttu-id="4f271-201">接著您可以使用 VisibleFunctions 欄位將那些函式設為在 JEA 工作階段中可見，就像是使用內建和協力廠商模組一樣。</span><span class="sxs-lookup"><span data-stu-id="4f271-201">You can then make those functions visible in the JEA session using the VisibleFunctions field like you would with built-in and third party modules.</span></span>

## <a name="place-role-capabilities-in-a-module"></a><span data-ttu-id="4f271-202">將角色功能放置在模組中</span><span class="sxs-lookup"><span data-stu-id="4f271-202">Place role capabilities in a module</span></span>

<span data-ttu-id="4f271-203">為了讓 PowerShell 尋找角色功能檔案，它必須儲存在 PowerShell 模組的 "RoleCapabilities" 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="4f271-203">In order for PowerShell to find a role capability file, it must be stored in a "RoleCapabilities" folder in a PowerShell module.</span></span>
<span data-ttu-id="4f271-204">模組可以儲存在 `$env:PSModulePath` 環境變數中包含的任何資料夾中，但您不應該將它放在 System32 資料夾中 (保留給內建模組)，或是不受信任的連線使用者可以修改其中檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="4f271-204">The module can be stored in any folder included in the `$env:PSModulePath` environment variable, however you should not place it in System32 (reserved for built-in modules) or a folder where the untrusted, connecting users could modify the files.</span></span>
<span data-ttu-id="4f271-205">以下範例會在 "Program Files" 路徑中建立基本 PowerShell 指令碼模組，稱為 *ContosoJEA*。</span><span class="sxs-lookup"><span data-stu-id="4f271-205">Below is an example of creating a basic PowerShell script module called *ContosoJEA* in the "Program Files" path.</span></span>

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest. At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

<span data-ttu-id="4f271-206">如需 PowerShell 模組、模組資訊清單和 PSModulePath 環境變數的詳細資訊，請參閱[了解 PowerShell 模組](https://msdn.microsoft.com/en-us/library/dd878324.aspx)。</span><span class="sxs-lookup"><span data-stu-id="4f271-206">See [Understanding a PowerShell Module](https://msdn.microsoft.com/en-us/library/dd878324.aspx) for more information about PowerShell modules, module manifests, and the PSModulePath environment variable.</span></span>

## <a name="updating-role-capabilities"></a><span data-ttu-id="4f271-207">更新角色功能</span><span class="sxs-lookup"><span data-stu-id="4f271-207">Updating role capabilities</span></span>


<span data-ttu-id="4f271-208">您只要儲存對角色功能檔案的變更，即可隨時更新角色功能檔案。</span><span class="sxs-lookup"><span data-stu-id="4f271-208">You can update a role capability file at any time by simply saving changes to the role capability file.</span></span>
<span data-ttu-id="4f271-209">更新角色功能之後啟動的任何新 JEA 工作階段都會反映出修改過的功能。</span><span class="sxs-lookup"><span data-stu-id="4f271-209">Any new JEA sessions started after the role capability has been updated will reflect the revised capabilities.</span></span>

<span data-ttu-id="4f271-210">這就是為什麼控制角色功能資料夾的存取權如此重要。</span><span class="sxs-lookup"><span data-stu-id="4f271-210">This is why controlling access to the role capabilities folder is so important.</span></span>
<span data-ttu-id="4f271-211">應該只有受高度信任的系統管理員才能夠變更角色功能檔案。</span><span class="sxs-lookup"><span data-stu-id="4f271-211">Only highly trusted administrators should be able to change role capability files.</span></span>
<span data-ttu-id="4f271-212">如果不受信任的使用者可以變更角色功能檔案，他們便可以輕鬆地讓自己能存取 Cmdlet，使其可提高權限。</span><span class="sxs-lookup"><span data-stu-id="4f271-212">If an untrusted user can change role capability files, they can easily give themselves access to cmdlets which allow them to elevate their privileges.</span></span>


<span data-ttu-id="4f271-213">針對想要鎖定角色功能存取權的系統管理員，請確定本機系統對於角色功能檔案和包含的模組具有讀取存取權。</span><span class="sxs-lookup"><span data-stu-id="4f271-213">For administrators looking to lock down access to the role capabilities, ensure Local System has read access to the role capability files and containing modules.</span></span>

## <a name="how-role-capabilities-are-merged"></a><span data-ttu-id="4f271-214">如何合併角色功能</span><span class="sxs-lookup"><span data-stu-id="4f271-214">How role capabilities are merged</span></span>

<span data-ttu-id="4f271-215">可以根據[工作階段設定檔](session-configurations.md)中的角色對應，在使用者進入 JEA 工作階段時授與使用者對多個角色功能的存取權。</span><span class="sxs-lookup"><span data-stu-id="4f271-215">Users can be granted access to multiple role capabilities when they enter a JEA session depending on the role mappings in the [session configuration file](session-configurations.md).</span></span>
<span data-ttu-id="4f271-216">發生這種情況時，JEA 會嘗試授與使用者任何角色所允許的*最寬鬆*的命令集。</span><span class="sxs-lookup"><span data-stu-id="4f271-216">When this happens, JEA tries to give the user the *most permissive* set of commands allowed by any of the roles.</span></span>

<span data-ttu-id="4f271-217">**VisibleCmdlets 和 VisibleFunctions**</span><span class="sxs-lookup"><span data-stu-id="4f271-217">**VisibleCmdlets and VisibleFunctions**</span></span>

<span data-ttu-id="4f271-218">最複雜的合併邏輯會影響 Cmdlet 和函式，它們的參數和參數值可能會在 JEA 中受到限制。</span><span class="sxs-lookup"><span data-stu-id="4f271-218">The most complex merge logic affects cmdlets and functions, which can have their parameters and parameter values limited in JEA.</span></span>

<span data-ttu-id="4f271-219">規則如下︰</span><span class="sxs-lookup"><span data-stu-id="4f271-219">The rules are as follows:</span></span>

1. <span data-ttu-id="4f271-220">如果 Cmdlet 只在一個角色中設為可見，具有任何適用的參數條件約束的使用者將可看見它。</span><span class="sxs-lookup"><span data-stu-id="4f271-220">If a cmdlet is only made visible in one role, it will be visible to the user with any applicable parameter constraints.</span></span>
2. <span data-ttu-id="4f271-221">如果 Cmdlet 在多個角色中設為可見，而且每個角色都對 Cmdlet 具有相同的條件約束，則具有這些條件約束的使用者將可看見該 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4f271-221">If a cmdlet is made visible in more than one role, and each role has the same constraints on the cmdlet, the cmdlet will be visible to the user with those constraints.</span></span>
3. <span data-ttu-id="4f271-222">如果 Cmdlet 在多個角色中設為可見，而且每個角色允許不同的參數集，則使用者將可看見該 Cmdlet 及在每個角色定義的所有參數。</span><span class="sxs-lookup"><span data-stu-id="4f271-222">If a cmdlet is made visible in more than one role, and each role allows a different set of parameters, the cmdlet and all of the parameters defined across every role will be visible to the user.</span></span> <span data-ttu-id="4f271-223">如果一個角色對參數沒有條件約束，將允許所有參數。</span><span class="sxs-lookup"><span data-stu-id="4f271-223">If one role doesn't have constraints on the parameters, all parameters will be allowed.</span></span>
4. <span data-ttu-id="4f271-224">如果一個角色針對 Cmdlet 參數定義驗證集或驗證模式，而另一個角色允許該參數，但未限制參數的值，則會忽略驗證集或模式。</span><span class="sxs-lookup"><span data-stu-id="4f271-224">If one role defines a validate set or validate pattern for a cmdlet parameter, and the other role allows the parameter but does not constrain the parameter values, the validate set or pattern will be ignored.</span></span>
5. <span data-ttu-id="4f271-225">如果在多個角色中針對相同的 Cmdlet 參數定義驗證集，將允許所有驗證字元集中的所有值。</span><span class="sxs-lookup"><span data-stu-id="4f271-225">If a validate set is defined for the same cmdlet parameter in more than one role, all values from all validate sets will be allowed.</span></span>
6. <span data-ttu-id="4f271-226">如果在多個角色中針對相同的 Cmdlet 參數定義驗證模式，將允許符合任何模式的任何值。</span><span class="sxs-lookup"><span data-stu-id="4f271-226">If a validate pattern is defined for the same cmdlet parameter in more than one role, any values that match any of the patterns will be allowed.</span></span>
7. <span data-ttu-id="4f271-227">如果在一或多個角色中定義驗證集，並且在另一個角色中針對相同 Cmdlet 參數定義驗證模式，將會忽略驗證集，並套用規則 (6) 至其餘的驗證模式。</span><span class="sxs-lookup"><span data-stu-id="4f271-227">If a validate set is defined in one or more roles, and a validate pattern is defined in another role for the same cmdlet parameter, the validate set is ignored and rule (6) applies to the remaining validate patterns.</span></span>

<span data-ttu-id="4f271-228">以下是角色如何根據這些規則合併的範例：</span><span class="sxs-lookup"><span data-stu-id="4f271-228">Below is an example of how roles are merged according to these rules:</span></span>

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permisisons for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service is ignored becuase of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```



<span data-ttu-id="4f271-229">**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**</span><span class="sxs-lookup"><span data-stu-id="4f271-229">**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**</span></span>

<span data-ttu-id="4f271-230">角色功能檔案中的所有其他欄位只會新增至可允許之外部命令、別名、提供者和啟動指令碼的累計集。</span><span class="sxs-lookup"><span data-stu-id="4f271-230">All other fields in the role capability file are simply added to a cumulative set of allowable external commands, aliases, providers, and startup scripts.</span></span>
<span data-ttu-id="4f271-231">JEA 使用者將可以使用一個角色功能中的任何命令、別名、提供者或指令碼。</span><span class="sxs-lookup"><span data-stu-id="4f271-231">Any command, alias, provider, or script available in one role capability will be available to the JEA user.</span></span>

<span data-ttu-id="4f271-232">請小心確保來自一個角色功能的提供者組合集，和來自另一個角色功能的 Cmdlet/函式/命令，不會允許連線使用者意外存取系統資源。</span><span class="sxs-lookup"><span data-stu-id="4f271-232">Be careful to ensure that the combined set of providers from one role capability and cmdlets/functions/commands from another do not allow connecting users unintentional access to system resources.</span></span>
<span data-ttu-id="4f271-233">例如，如果一個角色允許 `Remove-Item` Cmdlet，另一個允許 `FileSystem` 提供者，便會有 JEA 使用者刪除您電腦上任意檔案的風險。</span><span class="sxs-lookup"><span data-stu-id="4f271-233">For example, if one role allows the `Remove-Item` cmdlet and another allows the `FileSystem` provider, you are at risk of a JEA user deleting arbitrary files on your computer.</span></span>
<span data-ttu-id="4f271-234">如需識別使用者有效權限的詳細資訊，請參閱[稽核 JEA 主題](audit-and-report.md)。</span><span class="sxs-lookup"><span data-stu-id="4f271-234">Additional information about identifying users' effective permissions can be found in the [auditing JEA topic](audit-and-report.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="4f271-235">接下來的步驟</span><span class="sxs-lookup"><span data-stu-id="4f271-235">Next steps</span></span>

- [<span data-ttu-id="4f271-236">建立工作階段設定檔</span><span class="sxs-lookup"><span data-stu-id="4f271-236">Create a session configuration file</span></span>](session-configurations.md)