---
ms.date: 07/10/2019
keywords: jea,powershell,安全性
title: JEA 角色功能
ms.openlocfilehash: 5b5b5977d4fec1ed850f1146fe7c09463908651b
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "79402395"
---
# <a name="jea-role-capabilities"></a><span data-ttu-id="219ca-103">JEA 角色功能</span><span class="sxs-lookup"><span data-stu-id="219ca-103">JEA Role Capabilities</span></span>

<span data-ttu-id="219ca-104">建立 JEA 端點時，您必須定義一或多個角色功能，描述某人可以在 JEA 工作階段中做什麼。</span><span class="sxs-lookup"><span data-stu-id="219ca-104">When creating a JEA endpoint, you need to define one or more role capabilities that describe what someone can do in a JEA session.</span></span> <span data-ttu-id="219ca-105">角色功能是具有 `.psrc` 副檔名的 PowerShell 資料檔案，列出可供連線使用者使用的所有 Cmdlet、函式、提供者，以及外部程式。</span><span class="sxs-lookup"><span data-stu-id="219ca-105">A role capability is a PowerShell data file with the `.psrc` extension that lists all the cmdlets, functions, providers, and external programs that are made available to connecting users.</span></span>

## <a name="determine-which-commands-to-allow"></a><span data-ttu-id="219ca-106">決定允許哪些命令</span><span class="sxs-lookup"><span data-stu-id="219ca-106">Determine which commands to allow</span></span>

<span data-ttu-id="219ca-107">建立角色功能檔案的第一步是考慮使用者需要存取什麼。</span><span class="sxs-lookup"><span data-stu-id="219ca-107">The first step in creating a role capability file is to consider what the users need access to.</span></span> <span data-ttu-id="219ca-108">這項需求收集程序可能需要一段時間，但這是很重要的程序。</span><span class="sxs-lookup"><span data-stu-id="219ca-108">The requirements gathering process can take a while, but it's an important process.</span></span> <span data-ttu-id="219ca-109">提供使用者太少 Cmdlet 和函式的存取權，可能會使他們無法完成工作。</span><span class="sxs-lookup"><span data-stu-id="219ca-109">Giving users access to too few cmdlets and functions can prevent them from getting their job done.</span></span> <span data-ttu-id="219ca-110">允許太多 Cmdlet 和函式的存取權，可能會讓使用者執行超出您預期的項目，並降低您的安全性立場。</span><span class="sxs-lookup"><span data-stu-id="219ca-110">Allowing access to too many cmdlets and functions can allow users to do more than you intended and weaken your security stance.</span></span>

<span data-ttu-id="219ca-111">您進行此處理程序的方式，取決於您的組織和目標。</span><span class="sxs-lookup"><span data-stu-id="219ca-111">How you go about this process depends on your organization and goals.</span></span> <span data-ttu-id="219ca-112">下列祕訣可協助確保您採用正確的方法。</span><span class="sxs-lookup"><span data-stu-id="219ca-112">The following tips can help ensure you're on the right path.</span></span>

1. <span data-ttu-id="219ca-113">**識別**使用者用來完成工作的命令。</span><span class="sxs-lookup"><span data-stu-id="219ca-113">**Identify** the commands users are using to get their jobs done.</span></span> <span data-ttu-id="219ca-114">這可能需要調查 IT 人員、檢查自動化指令碼，或分析 PowerShell 工作階段文字記錄和記錄檔。</span><span class="sxs-lookup"><span data-stu-id="219ca-114">This may involve surveying IT staff, checking automation scripts, or analyzing PowerShell session transcripts and logs.</span></span>
2. <span data-ttu-id="219ca-115">可能的話，將命令列工具的使用**更新**為 PowerShell 對等用法，以得到最佳的稽核和 JEA 自訂體驗。</span><span class="sxs-lookup"><span data-stu-id="219ca-115">**Update** use of command-line tools to PowerShell equivalents, where possible, for the best auditing and JEA customization experience.</span></span> <span data-ttu-id="219ca-116">外部程式無法像原生 PowerShell Cmdlet 和 JEA 函式那樣精細地限制。</span><span class="sxs-lookup"><span data-stu-id="219ca-116">External programs can't be constrained as granularly as native PowerShell cmdlets and functions in JEA.</span></span>
3. <span data-ttu-id="219ca-117">**限制** Cmdlet 的範圍，只允許特定的參數或參數值。</span><span class="sxs-lookup"><span data-stu-id="219ca-117">**Restrict** the scope of the cmdlets to only allow specific parameters or parameter values.</span></span> <span data-ttu-id="219ca-118">如果使用者只應管理部分系統，則這點特別重要。</span><span class="sxs-lookup"><span data-stu-id="219ca-118">This is especially important if users should manage only part of a system.</span></span>
4. <span data-ttu-id="219ca-119">**建立**自訂函式來取代複雜命令或 JEA 中難以限制的命令。</span><span class="sxs-lookup"><span data-stu-id="219ca-119">**Create** custom functions to replace complex commands or commands that are difficult to constrain in JEA.</span></span> <span data-ttu-id="219ca-120">包裝複雜命令或套用額外驗證邏輯的簡單函式，可以提供系統管理員更多的控制，以及使用者的簡便性。</span><span class="sxs-lookup"><span data-stu-id="219ca-120">A simple function that wraps a complex command or applies additional validation logic can offer additional control for admins and end-user simplicity.</span></span>
5. <span data-ttu-id="219ca-121">**測試**使用者或自動化服務可允許命令的範圍清單，並視需要調整。</span><span class="sxs-lookup"><span data-stu-id="219ca-121">**Test** the scoped list of allowable commands with your users or automation services, and adjust as necessary.</span></span>

### <a name="examples-of-potentially-dangerous-commands"></a><span data-ttu-id="219ca-122">有潛在危險的命令範例</span><span class="sxs-lookup"><span data-stu-id="219ca-122">Examples of potentially dangerous commands</span></span>

<span data-ttu-id="219ca-123">謹慎地選取命令，對於確定 JEA 端點不會允許使用者提升其權限而言很重要。</span><span class="sxs-lookup"><span data-stu-id="219ca-123">Careful selection of commands is important to ensure the JEA endpoint doesn't allow the user to elevate their permissions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="219ca-124">協助使用者成功所需的基本資訊。JEA 工作階段通常會以提高的權限執行。</span><span class="sxs-lookup"><span data-stu-id="219ca-124">Essential information required for user successCommands in a JEA session are often run with elevated privileges.</span></span>

<span data-ttu-id="219ca-125">下表包含一些命令範例，如果允許其為未受限制的狀態，將可能惡意地使用它們。</span><span class="sxs-lookup"><span data-stu-id="219ca-125">The following table contains examples of commands that can be used maliciously if allowed in an unconstrained state.</span></span> <span data-ttu-id="219ca-126">這不是詳盡的清單，應該僅作為警告的起點。</span><span class="sxs-lookup"><span data-stu-id="219ca-126">This isn't an exhaustive list and should only be used as a cautionary starting point.</span></span>

|                                            <span data-ttu-id="219ca-127">風險</span><span class="sxs-lookup"><span data-stu-id="219ca-127">Risk</span></span>                                            |                                <span data-ttu-id="219ca-128">範例</span><span class="sxs-lookup"><span data-stu-id="219ca-128">Example</span></span>                                |                                                                              <span data-ttu-id="219ca-129">相關的命令</span><span class="sxs-lookup"><span data-stu-id="219ca-129">Related commands</span></span>                                                                              |
| ------------------------------------------------------------------------------------------ | --------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="219ca-130">授與連線使用者系統管理員權限以略過 JEA</span><span class="sxs-lookup"><span data-stu-id="219ca-130">Granting the connecting user admin privileges to bypass JEA</span></span>                                | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | <span data-ttu-id="219ca-131">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span><span class="sxs-lookup"><span data-stu-id="219ca-131">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span></span>                                                                                                        |
| <span data-ttu-id="219ca-132">執行任意程式碼，例如惡意程式碼、入侵或自訂指令碼來略過防護</span><span class="sxs-lookup"><span data-stu-id="219ca-132">Running arbitrary code, such as malware, exploits, or custom scripts to bypass protections</span></span> | `Start-Process -FilePath '\\san\share\malware.exe'`                   | <span data-ttu-id="219ca-133">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span><span class="sxs-lookup"><span data-stu-id="219ca-133">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span></span> |

## <a name="create-a-role-capability-file"></a><span data-ttu-id="219ca-134">建立角色功能檔案</span><span class="sxs-lookup"><span data-stu-id="219ca-134">Create a role capability file</span></span>

<span data-ttu-id="219ca-135">您可以使用 [New-PSRoleCapabilityFile](/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile?view=powershell-6) Cmdlet 建立新的 PowerShell 角色功能檔案。</span><span class="sxs-lookup"><span data-stu-id="219ca-135">You can create a new PowerShell role capability file with the [New-PSRoleCapabilityFile](/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile?view=powershell-6) cmdlet.</span></span>

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

<span data-ttu-id="219ca-136">您應編輯產生的角色功能檔案，以允許角色所需的命令。</span><span class="sxs-lookup"><span data-stu-id="219ca-136">The resulting role capability file should be edited to allow the commands required for the role.</span></span> <span data-ttu-id="219ca-137">PowerShell 說明文件包含數個檔案設定方式的範例。</span><span class="sxs-lookup"><span data-stu-id="219ca-137">The PowerShell help documentation contains several examples of how you can configure the file.</span></span>

### <a name="allowing-powershell-cmdlets-and-functions"></a><span data-ttu-id="219ca-138">允許 PowerShell Cmdlet 和函式</span><span class="sxs-lookup"><span data-stu-id="219ca-138">Allowing PowerShell cmdlets and functions</span></span>

<span data-ttu-id="219ca-139">若要授權使用者執行 PowerShell Cmdlet 或函式，請將 Cmdlet 或函式名稱新增至 VisibleCmdlets 或 VisibleFunctions 欄位。</span><span class="sxs-lookup"><span data-stu-id="219ca-139">To authorize users to run PowerShell cmdlets or functions, add the cmdlet or function name to the VisibleCmdlets or VisibleFunctions fields.</span></span> <span data-ttu-id="219ca-140">如果不確定命令是 Cmdlet 或函式，您可以執行 `Get-Command <name>` 並檢查輸出中的 **CommandType** 屬性。</span><span class="sxs-lookup"><span data-stu-id="219ca-140">If you aren't sure whether a command is a cmdlet or function, you can run `Get-Command <name>` and check the **CommandType** property in the output.</span></span>

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

<span data-ttu-id="219ca-141">有時候特定 Cmdlet 或函式的範圍對於您使用者的需求而言過於廣泛。</span><span class="sxs-lookup"><span data-stu-id="219ca-141">Sometimes the scope of a specific cmdlet or function is too broad for your users' needs.</span></span> <span data-ttu-id="219ca-142">例如，DNS 系統管理員可能只需要重新啟動 DNS 服務的存取權。</span><span class="sxs-lookup"><span data-stu-id="219ca-142">A DNS admin, for example, probably only needs access to restart the DNS service.</span></span> <span data-ttu-id="219ca-143">在多租用戶環境中，租用戶可以存取自助式管理工具。</span><span class="sxs-lookup"><span data-stu-id="219ca-143">In multi-tenant environments, tenants have access to self-service management tools.</span></span> <span data-ttu-id="219ca-144">租用戶應受限於僅可管理自己的資源。</span><span class="sxs-lookup"><span data-stu-id="219ca-144">Tenants should be limited to managing their own resources.</span></span> <span data-ttu-id="219ca-145">在這些情況下，您可以限制從 Cmdlet 或函式公開哪些參數。</span><span class="sxs-lookup"><span data-stu-id="219ca-145">For these cases, you can restrict which parameters are exposed from the cmdlet or function.</span></span>

```powershell
VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}
```

<span data-ttu-id="219ca-146">在進階情況中，您可能也需要限制使用者可以透過這些參數使用的值。</span><span class="sxs-lookup"><span data-stu-id="219ca-146">In more advanced scenarios, you may also need to restrict the values a user may use with these parameters.</span></span> <span data-ttu-id="219ca-147">角色功能可讓您定義一組值，或定義決定是否允許輸入的規則運算式模式。</span><span class="sxs-lookup"><span data-stu-id="219ca-147">Role capabilities let you define a set of values or a regular expression pattern that determine what input is allowed.</span></span>

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> <span data-ttu-id="219ca-148">一律會允許[一般的 PowerShell 參數](/powershell/module/microsoft.powershell.core/about/about_commonparameters)，即使是您限制了可用的參數。</span><span class="sxs-lookup"><span data-stu-id="219ca-148">The [common PowerShell parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters) are always allowed, even if you restrict the available parameters.</span></span>
> <span data-ttu-id="219ca-149">您不應該將其明確列在 Parameters 欄位中。</span><span class="sxs-lookup"><span data-stu-id="219ca-149">You should not explicitly list them in the Parameters field.</span></span>

<span data-ttu-id="219ca-150">下表說明您可以自訂可見 Cmdlet 或函式的各種方式。</span><span class="sxs-lookup"><span data-stu-id="219ca-150">The table below describes the various ways you can customize a visible cmdlet or function.</span></span>
<span data-ttu-id="219ca-151">您可以在 **VisibleCmdlets** 欄位中混搭下列任何項目。</span><span class="sxs-lookup"><span data-stu-id="219ca-151">You can mix and match any of the below in the **VisibleCmdlets** field.</span></span>

|                                           <span data-ttu-id="219ca-152">範例</span><span class="sxs-lookup"><span data-stu-id="219ca-152">Example</span></span>                                           |                                                             <span data-ttu-id="219ca-153">使用案例</span><span class="sxs-lookup"><span data-stu-id="219ca-153">Use case</span></span>                                                              |
| ------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="219ca-154">`'My-Func'` 或 `@{ Name = 'My-Func' }`</span><span class="sxs-lookup"><span data-stu-id="219ca-154">`'My-Func'` or `@{ Name = 'My-Func' }`</span></span>                                                      | <span data-ttu-id="219ca-155">允許使用者執行 `My-Func` 而無任何參數限制。</span><span class="sxs-lookup"><span data-stu-id="219ca-155">Allows the user to run `My-Func` without any restrictions on the parameters.</span></span>                                                      |
| `'MyModule\My-Func'`                                                                        | <span data-ttu-id="219ca-156">允許使用者從模組 `My-Func` 執行 `MyModule` 而無任何參數限制。</span><span class="sxs-lookup"><span data-stu-id="219ca-156">Allows the user to run `My-Func` from the module `MyModule` without any restrictions on the parameters.</span></span>                           |
| `'My-*'`                                                                                    | <span data-ttu-id="219ca-157">允許使用者使用動詞 `My` 執行任何 Cmdlet 或函式。</span><span class="sxs-lookup"><span data-stu-id="219ca-157">Allows the user to run any cmdlet or function with the verb `My`.</span></span>                                                                 |
| `'*-Func'`                                                                                  | <span data-ttu-id="219ca-158">允許使用者使用名詞 `Func` 執行任何 Cmdlet 或函式。</span><span class="sxs-lookup"><span data-stu-id="219ca-158">Allows the user to run any cmdlet or function with the noun `Func`.</span></span>                                                               |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`              | <span data-ttu-id="219ca-159">允許使用者搭配 `My-Func` 和 `Param1` 參數來執行 `Param2`。</span><span class="sxs-lookup"><span data-stu-id="219ca-159">Allows the user to run `My-Func` with the `Param1` and `Param2` parameters.</span></span> <span data-ttu-id="219ca-160">可以提供任何值給參數。</span><span class="sxs-lookup"><span data-stu-id="219ca-160">Any value can be supplied to the parameters.</span></span>          |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}` | <span data-ttu-id="219ca-161">允許使用者執行 `My-Func` 搭配 `Param1` 參數。</span><span class="sxs-lookup"><span data-stu-id="219ca-161">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="219ca-162">只能提供 "Value1" 和 "Value2" 給參數。</span><span class="sxs-lookup"><span data-stu-id="219ca-162">Only "Value1" and "Value2" can be supplied to the parameter.</span></span>        |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`    | <span data-ttu-id="219ca-163">允許使用者執行 `My-Func` 搭配 `Param1` 參數。</span><span class="sxs-lookup"><span data-stu-id="219ca-163">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="219ca-164">可以提供開頭為 "contoso" 的任何值給參數。</span><span class="sxs-lookup"><span data-stu-id="219ca-164">Any value starting with "contoso" can be supplied to the parameter.</span></span> |

> [!WARNING]
> <span data-ttu-id="219ca-165">關於最佳安全性做法，不建議在定義可見 Cmdlet 或函式時使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="219ca-165">For best security practices, it is not recommended to use wildcards when defining visible cmdlets or functions.</span></span> <span data-ttu-id="219ca-166">相反地，您應該明確列出每個受信任的命令，以確保沒有其他共用相同命名配置的命令意外地獲得授權。</span><span class="sxs-lookup"><span data-stu-id="219ca-166">Instead, you should explicitly list each trusted command to ensure no other commands that share the same naming scheme are unintentionally authorized.</span></span>

<span data-ttu-id="219ca-167">您無法將 **ValidatePattern** 和 **ValidateSet** 同時套用至相同的 Cmdlet 或函式。</span><span class="sxs-lookup"><span data-stu-id="219ca-167">You can't apply both a **ValidatePattern** and **ValidateSet** to the same cmdlet or function.</span></span>

<span data-ttu-id="219ca-168">如果您這樣做，**ValidatePattern** 會覆寫 **ValidateSet**。</span><span class="sxs-lookup"><span data-stu-id="219ca-168">If you do, the **ValidatePattern** overrides the **ValidateSet**.</span></span>

<span data-ttu-id="219ca-169">如需 **ValidatePattern** 的詳細資訊，請參閱[這篇 *Hey, Scripting Guy!* 文章](https://devblogs.microsoft.com/scripting/validate-powershell-parameters-before-running-the-script/)和 [PowerShell 規則運算式](/powershell/module/microsoft.powershell.core/about/about_regular_expressions)參考內容。</span><span class="sxs-lookup"><span data-stu-id="219ca-169">For more information about **ValidatePattern**, check out [this *Hey, Scripting Guy!* post](https://devblogs.microsoft.com/scripting/validate-powershell-parameters-before-running-the-script/) and the [PowerShell Regular Expressions](/powershell/module/microsoft.powershell.core/about/about_regular_expressions) reference content.</span></span>

### <a name="allowing-external-commands-and-powershell-scripts"></a><span data-ttu-id="219ca-170">允許外部命令及 PowerShell 指令碼</span><span class="sxs-lookup"><span data-stu-id="219ca-170">Allowing external commands and PowerShell scripts</span></span>

<span data-ttu-id="219ca-171">若要允許使用者在 JEA 工作階段中執行可執行檔和 PowerShell 指令碼 (.ps1)，您必須在 **VisibleExternalCommands** 欄位中新增每個程式的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="219ca-171">To allow users to run executables and PowerShell scripts (.ps1) in a JEA session, you have to add the full path to each program in the **VisibleExternalCommands** field.</span></span>

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

<span data-ttu-id="219ca-172">在可能的情況下，請使用任何外部可執行檔的對等 PowerShell Cmdlet 或函式，因為您可以控制 PowerShell Cmdlet 和函式允許哪些參數。</span><span class="sxs-lookup"><span data-stu-id="219ca-172">Where possible, to use PowerShell cmdlet or function equivalents for any external executables you authorize since you have control over the parameters allowed with PowerShell cmdlets and functions.</span></span>

<span data-ttu-id="219ca-173">許多可執行檔允許您讀取目前的狀態，然後提供不同參數來變更。</span><span class="sxs-lookup"><span data-stu-id="219ca-173">Many executables allow you to read the current state and then change it by providing different parameters.</span></span>

<span data-ttu-id="219ca-174">例如，考慮裝載於管理系統上的網路共用檔案伺服器管理員角色。</span><span class="sxs-lookup"><span data-stu-id="219ca-174">For example, consider the role of a file server admin that manages network shares hosted on a system.</span></span> <span data-ttu-id="219ca-175">管理共用的其中一種方法是使用 `net share`。</span><span class="sxs-lookup"><span data-stu-id="219ca-175">One way of managing shares is to use `net share`.</span></span> <span data-ttu-id="219ca-176">不過，允許 **net.exe** 很危險，因為使用者可以透過 `net group Administrators unprivilegedjeauser /add` 使用命令取得管理員權限。</span><span class="sxs-lookup"><span data-stu-id="219ca-176">However, allowing **net.exe** is dangerous because the user could use the command to gain admin privileges with `net group Administrators unprivilegedjeauser /add`.</span></span> <span data-ttu-id="219ca-177">較安全的選項是允許 [Get-SmbShare](/powershell/module/smbshare/get-smbshare)，這可達到相同結果但具有非常多的範圍限制。</span><span class="sxs-lookup"><span data-stu-id="219ca-177">A more secure option is to allow [Get-SmbShare](/powershell/module/smbshare/get-smbshare), which achieves the same result but has a much more limited scope.</span></span>

<span data-ttu-id="219ca-178">在 JEA 工作階段中將外部命令提供給使用者時，請一律指定可執行檔的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="219ca-178">When making external commands available to users in a JEA session, always specify the complete path to the executable.</span></span> <span data-ttu-id="219ca-179">這可防止名稱類似和潛在惡意程式在系統上的其他位置執行。</span><span class="sxs-lookup"><span data-stu-id="219ca-179">This prevents the execution of similarly named and potentially malicious programs located elsewhere on the system.</span></span>

### <a name="allowing-access-to-powershell-providers"></a><span data-ttu-id="219ca-180">允許存取 PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="219ca-180">Allowing access to PowerShell providers</span></span>

<span data-ttu-id="219ca-181">根據預設，在 JEA 工作階段中不能使用 PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="219ca-181">By default, no PowerShell providers are available in JEA sessions.</span></span> <span data-ttu-id="219ca-182">這是為了降低將敏感性資訊和組態設定公開給連線使用者的風險。</span><span class="sxs-lookup"><span data-stu-id="219ca-182">This reduces the risk of sensitive information and configuration settings being disclosed to the connecting user.</span></span>

<span data-ttu-id="219ca-183">如有必要，您可以使用 `VisibleProviders` 命令允許存取 PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="219ca-183">When necessary, you can allow access to the PowerShell providers using the `VisibleProviders` command.</span></span> <span data-ttu-id="219ca-184">如需完整的提供者清單，請執行 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="219ca-184">For a full list of providers, run `Get-PSProvider`.</span></span>

```powershell
VisibleProviders = 'Registry'
```

<span data-ttu-id="219ca-185">針對需要存取檔案系統、登錄、憑證存放區或其他敏感性提供者的簡單工作，請考慮撰寫代表使用者與提供者合作的自訂函式。</span><span class="sxs-lookup"><span data-stu-id="219ca-185">For simple tasks that require access to the file system, registry, certificate store, or other sensitive providers, consider writing a custom function that works with the provider on the user's behalf.</span></span> <span data-ttu-id="219ca-186">函式、Cmdlet 和 JEA 工作階段中可用外部程式不受限於與 JEA 相同的條件約束。</span><span class="sxs-lookup"><span data-stu-id="219ca-186">The functions, cmdlets, and external programs available in a JEA session aren't subject to the same constraints as JEA.</span></span> <span data-ttu-id="219ca-187">根據預設，它們可以存取任何提供者。</span><span class="sxs-lookup"><span data-stu-id="219ca-187">They can access any provider by default.</span></span> <span data-ttu-id="219ca-188">另外也請考慮當需要在與 JEA 端點之間複製檔案時使用[使用者磁碟機](session-configurations.md#user-drive)。</span><span class="sxs-lookup"><span data-stu-id="219ca-188">Also consider using the [user drive](session-configurations.md#user-drive) when copying files to or from a JEA endpoint is required.</span></span>

### <a name="creating-custom-functions"></a><span data-ttu-id="219ca-189">建立自訂函式</span><span class="sxs-lookup"><span data-stu-id="219ca-189">Creating custom functions</span></span>

<span data-ttu-id="219ca-190">您可以在角色功能檔案中撰寫自訂函式，簡化一般使用者的複雜工作。</span><span class="sxs-lookup"><span data-stu-id="219ca-190">You can author custom functions in a role capability file to simplify complex tasks for your end users.</span></span> <span data-ttu-id="219ca-191">當您需要 Cmdlet 參數值的進階驗證邏輯時，自訂函式也十分有用。</span><span class="sxs-lookup"><span data-stu-id="219ca-191">Custom functions are also useful when you require advanced validation logic for cmdlet parameter values.</span></span> <span data-ttu-id="219ca-192">您可以在 **FunctionDefinitions** 欄位中撰寫簡單的函式︰</span><span class="sxs-lookup"><span data-stu-id="219ca-192">You can write simple functions in the **FunctionDefinitions** field:</span></span>

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending |
            Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> <span data-ttu-id="219ca-193">別忘了將您的自訂函式名稱新增至 **VisibleFunctions** 欄位，以便 JEA 使用者可以執行它們。</span><span class="sxs-lookup"><span data-stu-id="219ca-193">Don't forget to add the name of your custom functions to the **VisibleFunctions** field so they can be run by the JEA users.</span></span>

<span data-ttu-id="219ca-194">自訂函式主體 (指令碼區塊) 會以系統的預設語言模式執行，且不受限於 JEA 的語言條件約束。</span><span class="sxs-lookup"><span data-stu-id="219ca-194">The body (script block) of custom functions runs in the default language mode for the system and isn't subject to JEA's language constraints.</span></span> <span data-ttu-id="219ca-195">這表示函式可以存取檔案系統和登錄，並執行角色功能檔案中未設為可見的命令。</span><span class="sxs-lookup"><span data-stu-id="219ca-195">This means that functions can access the file system and registry, and run commands that weren't made visible in the role capability file.</span></span> <span data-ttu-id="219ca-196">請在使用參數時小心避免執行任意程式碼。</span><span class="sxs-lookup"><span data-stu-id="219ca-196">Take care to avoid running arbitrary code when using parameters.</span></span> <span data-ttu-id="219ca-197">避免直接將使用者輸入用於 `Invoke-Expression` 之類的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="219ca-197">Avoid piping user input directly into cmdlets like `Invoke-Expression`.</span></span>

<span data-ttu-id="219ca-198">請注意，上述範例使用了完整的模組名稱 (FQMN) `Microsoft.PowerShell.Utility\Select-Object`，而不是使用速記的 `Select-Object`。</span><span class="sxs-lookup"><span data-stu-id="219ca-198">In the above example, notice that the fully qualified module name (FQMN) `Microsoft.PowerShell.Utility\Select-Object` was used instead of the shorthand `Select-Object`.</span></span>
<span data-ttu-id="219ca-199">角色功能檔案中定義的函式仍受限於 JEA 工作階段的範圍，包括 JEA 建立來限制現有命令的 Proxy 函式。</span><span class="sxs-lookup"><span data-stu-id="219ca-199">Functions defined in role capability files are still subject to the scope of JEA sessions, which includes the proxy functions JEA creates to constrain existing commands.</span></span>

<span data-ttu-id="219ca-200">根據預設，`Select-Object` 是所有 JEA 工作階段中受限制的預設 Cmdlet，不允許您選取物件上的任意屬性。</span><span class="sxs-lookup"><span data-stu-id="219ca-200">By default, `Select-Object` is a constrained cmdlet in all JEA sessions that doesn't allow the selection of arbitrary properties on objects.</span></span> <span data-ttu-id="219ca-201">若要在函式中使用未受限制的 `Select-Object`，您必須使用 FQMN 明確地要求完整實作。</span><span class="sxs-lookup"><span data-stu-id="219ca-201">To use the unconstrained `Select-Object` in functions, you must explicitly request the full implementation using the FQMN.</span></span> <span data-ttu-id="219ca-202">從函式叫用時，JEA 工作階段中任何受約束的 Cmdlet 都具有相同條件約束。</span><span class="sxs-lookup"><span data-stu-id="219ca-202">Any constrained cmdlet in a JEA session has the same constraints when invoked from a function.</span></span> <span data-ttu-id="219ca-203">如需詳細資訊，請參閱 [about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence)。</span><span class="sxs-lookup"><span data-stu-id="219ca-203">For more information, see [about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence).</span></span>

<span data-ttu-id="219ca-204">如果您要撰寫數個自訂函式，將它們放在 PowerShell 指令碼模組可能會比較方便。</span><span class="sxs-lookup"><span data-stu-id="219ca-204">If you're writing several custom functions, it's more convenient to put them in a PowerShell script module.</span></span> <span data-ttu-id="219ca-205">您可以使用 **VisibleFunctions** 欄位將那些函式設為在 JEA 工作階段中可見，就像是使用內建和協力廠商模組一樣。</span><span class="sxs-lookup"><span data-stu-id="219ca-205">You make those functions visible in the JEA session using the **VisibleFunctions** field like you would with built-in and third-party modules.</span></span>

<span data-ttu-id="219ca-206">您必須將內建函式 `tabexpansion2` 納入 **VisibleFunctions** 清單，Tab 鍵完成才能在 JEA 工作階段中正常運作。</span><span class="sxs-lookup"><span data-stu-id="219ca-206">For tab completion to work properly in JEA sessions you must include the built-in function `tabexpansion2` in the **VisibleFunctions** list.</span></span>

## <a name="make-the-role-capabilities-available-to-a-configuration"></a><span data-ttu-id="219ca-207">將角色功能提供給設定</span><span class="sxs-lookup"><span data-stu-id="219ca-207">Make the role capabilities available to a configuration</span></span>

<span data-ttu-id="219ca-208">在 PowerShell 6 之前，為了讓 PowerShell 尋找角色功能檔案，其必須儲存在 PowerShell 模組的 **RoleCapabilitie** 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="219ca-208">Prior to PowerShell 6, for PowerShell to find a role capability file it must be stored in a **RoleCapabilities** folder in a PowerShell module.</span></span> <span data-ttu-id="219ca-209">模組可以儲存在 `$env:PSModulePath` 環境變數包含的任何資料夾中，但您不應該將其放在 `$env:SystemRoot\System32` 資料夾中 ，或是未受信任連線使用者可以修改其中檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="219ca-209">The module can be stored in any folder included in the `$env:PSModulePath` environment variable, however you shouldn't place it in `$env:SystemRoot\System32` or a folder where untrusted users could modify the files.</span></span>

<span data-ttu-id="219ca-210">下列範例會在用來裝載角色功能檔案的 **路徑中，建立名為**ContosoJEA`$env:ProgramFiles` 的 PowerShell 指令碼模組。</span><span class="sxs-lookup"><span data-stu-id="219ca-210">The following example creates a PowerShell script module called **ContosoJEA** in the `$env:ProgramFiles` path to host the role capabilities file.</span></span>

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest.
# At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

<span data-ttu-id="219ca-211">如需 PowerShell 模組的詳細資訊，請參閱[了解 PowerShell 模組](/powershell/scripting/developer/windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="219ca-211">For more information about PowerShell modules, see [Understanding a PowerShell Module](/powershell/scripting/developer/windows-powershell).</span></span>

<span data-ttu-id="219ca-212">從 PowerShell 6 開始，**RoleDefinitions** 屬性已新增至工作階段設定檔。</span><span class="sxs-lookup"><span data-stu-id="219ca-212">Starting in PowerShell 6, the **RoleDefinitions** property was added to the session configuration file.</span></span> <span data-ttu-id="219ca-213">此屬性可讓您為角色定義指定角色設定檔的位置。</span><span class="sxs-lookup"><span data-stu-id="219ca-213">This property lets you specify the location of a role configuration file for your role definition.</span></span> <span data-ttu-id="219ca-214">請查看 [New-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/new-pssessionconfigurationfile) 中的範例。</span><span class="sxs-lookup"><span data-stu-id="219ca-214">See the examples in [New-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/new-pssessionconfigurationfile).</span></span>

## <a name="updating-role-capabilities"></a><span data-ttu-id="219ca-215">更新角色功能</span><span class="sxs-lookup"><span data-stu-id="219ca-215">Updating role capabilities</span></span>

<span data-ttu-id="219ca-216">您可以編輯角色功能檔案以隨時更新設定。</span><span class="sxs-lookup"><span data-stu-id="219ca-216">You can edit a role capability file to update the settings at any time.</span></span> <span data-ttu-id="219ca-217">更新角色功能之後啟動的任何新 JEA 工作階段都會反映出修改過的功能。</span><span class="sxs-lookup"><span data-stu-id="219ca-217">Any new JEA sessions started after the role capability has been updated will reflect the revised capabilities.</span></span>

<span data-ttu-id="219ca-218">這就是為什麼控制角色功能資料夾的存取權如此重要。</span><span class="sxs-lookup"><span data-stu-id="219ca-218">This is why controlling access to the role capabilities folder is so important.</span></span> <span data-ttu-id="219ca-219">應該只有受高度信任的系統管理員才允許變更角色功能檔案。</span><span class="sxs-lookup"><span data-stu-id="219ca-219">Only highly trusted administrators should be allowed to change role capability files.</span></span> <span data-ttu-id="219ca-220">如果未受信任的使用者可以變更角色功能檔案，他們便可以輕鬆地讓自己能存取 Cmdlet，使其可提高權限。</span><span class="sxs-lookup"><span data-stu-id="219ca-220">If an untrusted user can change role capability files, they can easily give themselves access to cmdlets that allow them to elevate their privileges.</span></span>

<span data-ttu-id="219ca-221">針對想要鎖定角色功能存取權的系統管理員，請確定本機系統對於角色功能檔案和包含的模組具有讀取存取權。</span><span class="sxs-lookup"><span data-stu-id="219ca-221">For administrators looking to lock down access to the role capabilities, ensure Local System has read access to the role capability files and containing modules.</span></span>

## <a name="how-role-capabilities-are-merged"></a><span data-ttu-id="219ca-222">如何合併角色功能</span><span class="sxs-lookup"><span data-stu-id="219ca-222">How role capabilities are merged</span></span>

<span data-ttu-id="219ca-223">當使用者進入 JEA 工作階段時，即可存取[工作階段設定檔](session-configurations.md)中所有相符的角色功能。</span><span class="sxs-lookup"><span data-stu-id="219ca-223">Users are granted access to all matching role capabilities in the [session configuration file](session-configurations.md) when they enter a JEA session.</span></span> <span data-ttu-id="219ca-224">JEA 會嘗試授與使用者任何角色所允許的最寬鬆命令集。</span><span class="sxs-lookup"><span data-stu-id="219ca-224">JEA tries to give the user the most permissive set of commands allowed by any of the roles.</span></span>

### <a name="visiblecmdlets-and-visiblefunctions"></a><span data-ttu-id="219ca-225">VisibleCmdlet 和 VisibleFunction</span><span class="sxs-lookup"><span data-stu-id="219ca-225">VisibleCmdlets and VisibleFunctions</span></span>

<span data-ttu-id="219ca-226">最複雜的合併邏輯會影響 Cmdlet 和函式，它們的參數和參數值可能會在 JEA 中受到限制。</span><span class="sxs-lookup"><span data-stu-id="219ca-226">The most complex merge logic affects cmdlets and functions, which can have their parameters and parameter values limited in JEA.</span></span>

<span data-ttu-id="219ca-227">規則如下︰</span><span class="sxs-lookup"><span data-stu-id="219ca-227">The rules are as follows:</span></span>

1. <span data-ttu-id="219ca-228">如果 Cmdlet 只在一個角色中設為可見，則具有任何適用參數條件約束的使用者將可看見。</span><span class="sxs-lookup"><span data-stu-id="219ca-228">If a cmdlet is only made visible in one role, it is visible to the user with any applicable parameter constraints.</span></span>
2. <span data-ttu-id="219ca-229">如果 Cmdlet 在多個角色中設為可見，且每個角色都對 Cmdlet 具有相同的條件約束，則具有這些條件約束的使用者將可看見該 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="219ca-229">If a cmdlet is made visible in more than one role, and each role has the same constraints on the cmdlet, the cmdlet is visible to the user with those constraints.</span></span>
3. <span data-ttu-id="219ca-230">如果 Cmdlet 在多個角色中設為可見，且每個角色允許不同的參數集，則使用者將可看見該 Cmdlet 及在每個角色定義的所有參數。</span><span class="sxs-lookup"><span data-stu-id="219ca-230">If a cmdlet is made visible in more than one role, and each role allows a different set of parameters, the cmdlet and all the parameters defined across every role are visible to the user.</span></span>
   <span data-ttu-id="219ca-231">如果一個角色對參數沒有條件約束，則將允許所有參數。</span><span class="sxs-lookup"><span data-stu-id="219ca-231">If one role doesn't have constraints on the parameters, all parameters are allowed.</span></span>
4. <span data-ttu-id="219ca-232">如果一個角色針對 Cmdlet 參數定義驗證集或驗證模式，而另一個角色允許該參數但未限制參數值，則會忽略驗證集或模式。</span><span class="sxs-lookup"><span data-stu-id="219ca-232">If one role defines a validate set or validate pattern for a cmdlet parameter, and the other role allows the parameter but does not constrain the parameter values, the validate set or pattern is ignored.</span></span>
5. <span data-ttu-id="219ca-233">如果在多個角色中針對相同的 Cmdlet 參數定義驗證集，將允許所有驗證字元集中的所有值。</span><span class="sxs-lookup"><span data-stu-id="219ca-233">If a validate set is defined for the same cmdlet parameter in more than one role, all values from all validate sets are allowed.</span></span>
6. <span data-ttu-id="219ca-234">如果在多個角色中針對相同的 Cmdlet 參數定義驗證模式，將允許符合任何模式的任何值。</span><span class="sxs-lookup"><span data-stu-id="219ca-234">If a validate pattern is defined for the same cmdlet parameter in more than one role, any values that match any of the patterns are allowed.</span></span>
7. <span data-ttu-id="219ca-235">如果在一或多個角色中定義驗證集，並且在另一個角色中針對相同 Cmdlet 參數定義驗證模式，將會忽略驗證集，並套用規則 (6) 至其餘的驗證模式。</span><span class="sxs-lookup"><span data-stu-id="219ca-235">If a validate set is defined in one or more roles, and a validate pattern is defined in another role for the same cmdlet parameter, the validate set is ignored and rule (6) applies to the remaining validate patterns.</span></span>

<span data-ttu-id="219ca-236">以下是角色如何根據這些規則合併的範例：</span><span class="sxs-lookup"><span data-stu-id="219ca-236">Below is an example of how roles are merged according to these rules:</span></span>

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permissions for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service
#   is ignored because of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use
#   ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```

### <a name="visibleexternalcommands-visiblealiases-visibleproviders-scriptstoprocess"></a><span data-ttu-id="219ca-237">VisibleExternalCommand, VisibleAliase, VisibleProvider, ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="219ca-237">VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess</span></span>

<span data-ttu-id="219ca-238">角色功能檔案中所有其他欄位會新增至可允許之外部命令、別名、提供者和啟動指令碼的累計集。</span><span class="sxs-lookup"><span data-stu-id="219ca-238">All other fields in the role capability file are added to a cumulative set of allowable external commands, aliases, providers, and startup scripts.</span></span> <span data-ttu-id="219ca-239">JEA 使用者將可以使用一個角色功能中的任何命令、別名、提供者或指令碼。</span><span class="sxs-lookup"><span data-stu-id="219ca-239">Any command, alias, provider, or script available in one role capability is available to the JEA user.</span></span>

<span data-ttu-id="219ca-240">請小心確保來自一個角色功能之提供者組合集和來自另一個角色功能的 Cmdlet/函式/命令不會允許使用者意外存取系統資源。</span><span class="sxs-lookup"><span data-stu-id="219ca-240">Be careful to ensure that the combined set of providers from one role capability and cmdlets/functions/commands from another don't allow users unintentional access to system resources.</span></span>
<span data-ttu-id="219ca-241">例如，如果一個角色允許 `Remove-Item` Cmdlet，另一個允許 `FileSystem` 提供者，便會有 JEA 使用者刪除您電腦上任意檔案的風險。</span><span class="sxs-lookup"><span data-stu-id="219ca-241">For example, if one role allows the `Remove-Item` cmdlet and another allows the `FileSystem` provider, you are at risk of a JEA user deleting arbitrary files on your computer.</span></span> <span data-ttu-id="219ca-242">如需識別使用者有效權限的詳細資訊，請參閱[稽核 JEA](audit-and-report.md) 一文。</span><span class="sxs-lookup"><span data-stu-id="219ca-242">Additional information about identifying users' effective permissions can be found in the [auditing JEA](audit-and-report.md) article.</span></span>

## <a name="next-steps"></a><span data-ttu-id="219ca-243">後續步驟</span><span class="sxs-lookup"><span data-stu-id="219ca-243">Next steps</span></span>

[<span data-ttu-id="219ca-244">建立工作階段設定檔</span><span class="sxs-lookup"><span data-stu-id="219ca-244">Create a session configuration file</span></span>](session-configurations.md)
