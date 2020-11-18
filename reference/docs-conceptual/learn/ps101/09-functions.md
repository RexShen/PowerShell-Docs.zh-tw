---
title: 函式
description: PowerShell 函式可讓您建立可在指令碼中重複使用的工具。
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 9554c0b4d3932b7371201f7b08c8b9d26a567f5e
ms.sourcegitcommit: e85e56d6614cbd30e01965a5cf03fb3f5ca78103
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2020
ms.locfileid: "94589121"
---
# <a name="chapter-9---functions"></a><span data-ttu-id="10075-103">第 9 章 - 函式</span><span class="sxs-lookup"><span data-stu-id="10075-103">Chapter 9 - Functions</span></span>

<span data-ttu-id="10075-104">如果您要撰寫 PowerShell 一行程式碼或指令碼，而且發現您經常需要針對不同的案例進行修改，將它轉換成可重複使用的函式應很合適。</span><span class="sxs-lookup"><span data-stu-id="10075-104">If you're writing PowerShell one-liners or scripts and find yourself often having to modify them for different scenarios, there's a good chance that it's a good candidate to be turned into a function that can be reused.</span></span>

<span data-ttu-id="10075-105">如果可能，我偏好撰寫函式，因為它們更具工具導向。</span><span class="sxs-lookup"><span data-stu-id="10075-105">Whenever possible, I prefer to write functions because they are more tool oriented.</span></span> <span data-ttu-id="10075-106">我可以將函式放在指令碼模組中，將該模組放在 `$env:PSModulePath` 中並呼叫函式，而不需要實際找出其儲存位置。</span><span class="sxs-lookup"><span data-stu-id="10075-106">I can put the functions in a script module, put that module in the `$env:PSModulePath`, and call the functions without needing to physically locate where they're saved.</span></span> <span data-ttu-id="10075-107">使用 PowerShellGet 模組，要在 NuGet 存放庫中共用這些模組非常容易。</span><span class="sxs-lookup"><span data-stu-id="10075-107">Using the PowerShellGet module, it's easy to share those modules in a NuGet repository.</span></span> <span data-ttu-id="10075-108">PowerShellGet 隨附 PowerShell 5.0 版和更新版本。</span><span class="sxs-lookup"><span data-stu-id="10075-108">PowerShellGet ships with PowerShell version 5.0 and higher.</span></span> <span data-ttu-id="10075-109">其以 PowerShell 3.0 版和更新版本的個別下載形式提供。</span><span class="sxs-lookup"><span data-stu-id="10075-109">It is available as a separate download for PowerShell version 3.0 and higher.</span></span>

<span data-ttu-id="10075-110">不要太過複雜。</span><span class="sxs-lookup"><span data-stu-id="10075-110">Don't over complicate things.</span></span> <span data-ttu-id="10075-111">將它保持簡單，並使用最直接的方式來完成工作。</span><span class="sxs-lookup"><span data-stu-id="10075-111">Keep it simple and use the most straight forward way to accomplish a task.</span></span> <span data-ttu-id="10075-112">避免在您重複使用的任何程式碼中使用別名和位置參數。</span><span class="sxs-lookup"><span data-stu-id="10075-112">Avoid aliases and positional parameters in any code that you reuse.</span></span> <span data-ttu-id="10075-113">將您的程式碼格式化，以易於閱讀。</span><span class="sxs-lookup"><span data-stu-id="10075-113">Format your code for readability.</span></span> <span data-ttu-id="10075-114">不要將值硬式編碼；使用參數和變數。</span><span class="sxs-lookup"><span data-stu-id="10075-114">Don't hardcode values; use parameters and variables.</span></span> <span data-ttu-id="10075-115">請勿撰寫不必要的程式碼，即使它不會損及任何項目。</span><span class="sxs-lookup"><span data-stu-id="10075-115">Don't write unnecessary code even if it doesn't hurt anything.</span></span> <span data-ttu-id="10075-116">這會增加不必要的複雜度。</span><span class="sxs-lookup"><span data-stu-id="10075-116">It adds unnecessary complexity.</span></span> <span data-ttu-id="10075-117">注意細節對撰寫任何 PowerShell 程式碼很有幫助。</span><span class="sxs-lookup"><span data-stu-id="10075-117">Attention to detail goes a long way when writing any PowerShell code.</span></span>

## <a name="naming"></a><span data-ttu-id="10075-118">命名</span><span class="sxs-lookup"><span data-stu-id="10075-118">Naming</span></span>

<span data-ttu-id="10075-119">在 PowerShell 中為您的函式命名時，請使用 [Pascal 命名法的大小寫][] 名稱搭配已核准的動詞和單數名詞。</span><span class="sxs-lookup"><span data-stu-id="10075-119">When naming your functions in PowerShell, use a [Pascal case][] name with an approved verb and a singular noun.</span></span> <span data-ttu-id="10075-120">我也建議為名詞加上前置詞。</span><span class="sxs-lookup"><span data-stu-id="10075-120">I also recommend prefixing the noun.</span></span> <span data-ttu-id="10075-121">例如： `<ApprovedVerb>-<Prefix><SingularNoun>` 。</span><span class="sxs-lookup"><span data-stu-id="10075-121">For example: `<ApprovedVerb>-<Prefix><SingularNoun>`.</span></span>

<span data-ttu-id="10075-122">在 PowerShell 中，您可以藉由執行 `Get-Verb` 來取得已核准的特定動詞清單。</span><span class="sxs-lookup"><span data-stu-id="10075-122">In PowerShell, there's a specific list of approved verbs that can be obtained by running `Get-Verb`.</span></span>

```powershell
Get-Verb | Sort-Object -Property Verb
```

```Output
Verb        Group
----        -----
Add         Common
Approve     Lifecycle
Assert      Lifecycle
Backup      Data
Block       Security
Checkpoint  Data
Clear       Common
Close       Common
Compare     Data
Complete    Lifecycle
Compress    Data
Confirm     Lifecycle
Connect     Communications
Convert     Data
ConvertFrom Data
ConvertTo   Data
Copy        Common
Debug       Diagnostic
Deny        Lifecycle
Disable     Lifecycle
Disconnect  Communications
Dismount    Data
Edit        Data
Enable      Lifecycle
Enter       Common
Exit        Common
Expand      Data
Export      Data
Find        Common
Format      Common
Get         Common
Grant       Security
Group       Data
Hide        Common
Import      Data
Initialize  Data
Install     Lifecycle
Invoke      Lifecycle
Join        Common
Limit       Data
Lock        Common
Measure     Diagnostic
Merge       Data
Mount       Data
Move        Common
New         Common
Open        Common
Optimize    Common
Out         Data
Ping        Diagnostic
Pop         Common
Protect     Security
Publish     Data
Push        Common
Read        Communications
Receive     Communications
Redo        Common
Register    Lifecycle
Remove      Common
Rename      Common
Repair      Diagnostic
Request     Lifecycle
Reset       Common
Resize      Common
Resolve     Diagnostic
Restart     Lifecycle
Restore     Data
Resume      Lifecycle
Revoke      Security
Save        Data
Search      Common
Select      Common
Send        Communications
Set         Common
Show        Common
Skip        Common
Split       Common
Start       Lifecycle
Step        Common
Stop        Lifecycle
Submit      Lifecycle
Suspend     Lifecycle
Switch      Common
Sync        Data
Test        Diagnostic
Trace       Diagnostic
Unblock     Security
Undo        Common
Uninstall   Lifecycle
Unlock      Common
Unprotect   Security
Unpublish   Data
Unregister  Lifecycle
Update      Data
Use         Other
Wait        Lifecycle
Watch       Common
Write       Communications
```

<span data-ttu-id="10075-123">在上述範例中，我已依照 **動詞** 資料行排序結果。</span><span class="sxs-lookup"><span data-stu-id="10075-123">In the previous example, I've sorted the results by the **Verb** column.</span></span> <span data-ttu-id="10075-124">**群組** 資料行可讓您對於如何使用這些動詞有些概念。</span><span class="sxs-lookup"><span data-stu-id="10075-124">The **Group** column gives you an idea of how these verbs are used.</span></span> <span data-ttu-id="10075-125">將函式新增至模組時，請務必在 PowerShell 中選擇已核准的動詞。</span><span class="sxs-lookup"><span data-stu-id="10075-125">It's important to choose an approved verb in PowerShell when functions are added to a module.</span></span> <span data-ttu-id="10075-126">如果您選擇未核准的動詞，模組會在載入時產生警告訊息。</span><span class="sxs-lookup"><span data-stu-id="10075-126">The module generates a warning message at load time if you choose an unapproved verb.</span></span> <span data-ttu-id="10075-127">該警告訊息會讓您的函式看起來不專業。</span><span class="sxs-lookup"><span data-stu-id="10075-127">That warning message makes your functions look unprofessional.</span></span> <span data-ttu-id="10075-128">未核准的動詞也會限制函式的可探索性。</span><span class="sxs-lookup"><span data-stu-id="10075-128">Unapproved verbs also limit the discoverability of your functions.</span></span>

## <a name="a-simple-function"></a><span data-ttu-id="10075-129">簡單函式</span><span class="sxs-lookup"><span data-stu-id="10075-129">A simple function</span></span>

<span data-ttu-id="10075-130">PowerShell 中的函式會使用 function 關鍵字來宣告，後面接著函式名稱，然後是左和右大括弧。</span><span class="sxs-lookup"><span data-stu-id="10075-130">A function in PowerShell is declared with the function keyword followed by the function name and then an open and closing curly brace.</span></span> <span data-ttu-id="10075-131">函式將執行的程式碼會包含在這些大括弧內。</span><span class="sxs-lookup"><span data-stu-id="10075-131">The code that the function will execute is contained within those curly braces.</span></span>

```powershell
function Get-Version {
    $PSVersionTable.PSVersion
}
```

<span data-ttu-id="10075-132">顯示的函式是一個會傳回 PowerShell 版本的簡單範例。</span><span class="sxs-lookup"><span data-stu-id="10075-132">The function shown is a simple example that returns the version of PowerShell.</span></span>

```powershell
Get-Version
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

<span data-ttu-id="10075-133">名稱很可能會與名為 `Get-Version` 之類的函式和 PowerShell 中的預設命令，或其他人可能寫入的命令發生衝突。</span><span class="sxs-lookup"><span data-stu-id="10075-133">There's a good chance of name conflict with functions named something like `Get-Version` and default commands in PowerShell or commands that others may write.</span></span> <span data-ttu-id="10075-134">這就是為什麼我建議您在函式的名詞部分前面加上前置詞，以協助避免命名衝突。</span><span class="sxs-lookup"><span data-stu-id="10075-134">This is why I recommend prefixing the noun portion of your functions to help prevent naming conflicts.</span></span> <span data-ttu-id="10075-135">在下列範例中，我將使用前置詞 "PS"。</span><span class="sxs-lookup"><span data-stu-id="10075-135">In the following example, I'll use the prefix "PS".</span></span>

```powershell
function Get-PSVersion {
    $PSVersionTable.PSVersion
}
```

<span data-ttu-id="10075-136">除了名稱之外，此函式與上一個函式完全相同。</span><span class="sxs-lookup"><span data-stu-id="10075-136">Other than the name, this function is identical to the previous one.</span></span>

```powershell
Get-PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

<span data-ttu-id="10075-137">即使是在名詞前面加上 PS 之類項目，還是有可能發生名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="10075-137">Even when prefixing the noun with something like PS, there's still a good chance of having a name conflict.</span></span> <span data-ttu-id="10075-138">我通常會在我的函式名詞前面加上我的姓名縮寫。</span><span class="sxs-lookup"><span data-stu-id="10075-138">I typically prefix my function nouns with my initials.</span></span> <span data-ttu-id="10075-139">發展一個標準並持續使用它。</span><span class="sxs-lookup"><span data-stu-id="10075-139">Develop a standard and stick to it.</span></span>

```powershell
function Get-MrPSVersion {
    $PSVersionTable.PSVersion
}
```

<span data-ttu-id="10075-140">除了使用更合理的名稱來嘗試避免與其他 PowerShell 命令的命名衝突以外，此函式與前兩個函式沒有不同。</span><span class="sxs-lookup"><span data-stu-id="10075-140">This function is no different than the previous two other than using a more sensible name to try to prevent naming conflicts with other PowerShell commands.</span></span>

```powershell
Get-MrPSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

<span data-ttu-id="10075-141">載入記憶體之後，您可以在 **Function** PSDrive 上查看函式。</span><span class="sxs-lookup"><span data-stu-id="10075-141">Once loaded into memory, you can see functions on the **Function** PSDrive.</span></span>

```powershell
Get-ChildItem -Path Function:\Get-*Version
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-Version
Function        Get-PSVersion
Function        Get-MrPSVersion
```

<span data-ttu-id="10075-142">如果您想要從目前的工作階段移除這些函式，您必須從 **Function** PSDrive 中移除它們，或關閉並重新開啟 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="10075-142">If you want to remove these functions from your current session, you'll have to remove them from the **Function** PSDrive or close and reopen PowerShell.</span></span>

```powershell
Get-ChildItem -Path Function:\Get-*Version | Remove-Item
```

<span data-ttu-id="10075-143">確認已確實移除這些函式。</span><span class="sxs-lookup"><span data-stu-id="10075-143">Verify that the functions were indeed removed.</span></span>

```powershell
Get-ChildItem -Path Function:\Get-*Version
```

<span data-ttu-id="10075-144">如果函式已載入為模組的一部分，則可以卸載模組以將其移除。</span><span class="sxs-lookup"><span data-stu-id="10075-144">If the functions were loaded as part of a module, the module can be unloaded to remove them.</span></span>

```powershell
Remove-Module -Name <ModuleName>
```

<span data-ttu-id="10075-145">`Remove-Module` Cmdlet 會從您目前的 PowerShell 工作階段的記憶體移中除模組，而不會從您的系統或磁碟中移除它們。</span><span class="sxs-lookup"><span data-stu-id="10075-145">The `Remove-Module` cmdlet removes modules from memory in your current PowerShell session, it doesn't remove them from your system or from disk.</span></span>

## <a name="parameters"></a><span data-ttu-id="10075-146">參數</span><span class="sxs-lookup"><span data-stu-id="10075-146">Parameters</span></span>

<span data-ttu-id="10075-147">不要以靜態方式指派值！</span><span class="sxs-lookup"><span data-stu-id="10075-147">Don't statically assign values!</span></span> <span data-ttu-id="10075-148">使用參數和變數。</span><span class="sxs-lookup"><span data-stu-id="10075-148">Use parameters and variables.</span></span> <span data-ttu-id="10075-149">為參數命名時，請盡可能使用相同名稱做為參數名稱的預設 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="10075-149">When it comes to naming your parameters, use the same name as the default cmdlets for your parameter names whenever possible.</span></span>

```powershell
function Test-MrParameter {

    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="10075-150">為什麼我使用 **ComputerName** 而不是 **Computer**、**ServerName** 或 **Host** 做為參數名稱？</span><span class="sxs-lookup"><span data-stu-id="10075-150">Why did I use **ComputerName** and not **Computer**, **ServerName**, or **Host** for my parameter name?</span></span> <span data-ttu-id="10075-151">這是因為我希望將我的函式如同預設 Cmdlet 般標準化。</span><span class="sxs-lookup"><span data-stu-id="10075-151">It's because I wanted my function standardized like the default cmdlets.</span></span>

<span data-ttu-id="10075-152">我要建立一個函式來查詢系統上的所有命令，並傳回具有特定參數名稱的函式數目。</span><span class="sxs-lookup"><span data-stu-id="10075-152">I'll create a function to query all of the commands on a system and return the number of them that have specific parameter names.</span></span>

```powershell
function Get-MrParameterCount {
    param (
        [string[]]$ParameterName
    )

    foreach ($Parameter in $ParameterName) {
        $Results = Get-Command -ParameterName $Parameter -ErrorAction SilentlyContinue

        [pscustomobject]@{
            ParameterName = $Parameter
            NumberOfCmdlets = $Results.Count
        }
    }
}
```

<span data-ttu-id="10075-153">如您在下面所示的結果中所見，有 39 個命令具有 **ComputerName** 參數。</span><span class="sxs-lookup"><span data-stu-id="10075-153">As you can see in the results shown below, 39 commands that have a **ComputerName** parameter.</span></span> <span data-ttu-id="10075-154">沒有任何 Cmdlet 具有參數 (例如 **Computer**、**ServerName**、**Host** 或 **Machine**)。</span><span class="sxs-lookup"><span data-stu-id="10075-154">There aren't any cmdlets that have parameters such as **Computer**, **ServerName**, **Host**, or **Machine**.</span></span>

```powershell
Get-MrParameterCount -ParameterName ComputerName, Computer, ServerName, Host, Machine
```

```Output
ParameterName NumberOfCmdlets
------------- ---------------
ComputerName               39
Computer                    0
ServerName                  0
Host                        0
Machine                     0
```

<span data-ttu-id="10075-155">我也建議對您的參數名稱使用相同的大小寫做為預設 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="10075-155">I also recommend using the same case for your parameter names as the default cmdlets.</span></span> <span data-ttu-id="10075-156">使用 `ComputerName`，而不是 `computername`。</span><span class="sxs-lookup"><span data-stu-id="10075-156">Use `ComputerName`, not `computername`.</span></span> <span data-ttu-id="10075-157">這會讓您的函式看起來像是預設 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="10075-157">This makes your functions look and feel like the default cmdlets.</span></span> <span data-ttu-id="10075-158">已熟悉 PowerShell 的人員就會覺得再習慣不過。</span><span class="sxs-lookup"><span data-stu-id="10075-158">People who are already familiar with PowerShell will feel right at home.</span></span>

## <a name="advanced-functions"></a><span data-ttu-id="10075-159">進階函式</span><span class="sxs-lookup"><span data-stu-id="10075-159">Advanced Functions</span></span>

<span data-ttu-id="10075-160">將 PowerShell 中的函式轉換成進階函式真的很簡單。</span><span class="sxs-lookup"><span data-stu-id="10075-160">Turning a function in PowerShell into an advanced function is really simple.</span></span> <span data-ttu-id="10075-161">函式與進階函式之間的其中一項差異是，進階函式具有許多會自動新增至函式的一般參數。</span><span class="sxs-lookup"><span data-stu-id="10075-161">One of the differences between a function and an advanced function is that advanced functions have a number of common parameters that are added to the function automatically.</span></span> <span data-ttu-id="10075-162">這些一般參數包括 **Verbose** 和 **Debug** 之類的參數。</span><span class="sxs-lookup"><span data-stu-id="10075-162">These common parameters include parameters such as **Verbose** and **Debug**.</span></span>

<span data-ttu-id="10075-163">我將從上一節中使用的 `Test-MrParameter` 函式開始。</span><span class="sxs-lookup"><span data-stu-id="10075-163">I'll start out with the `Test-MrParameter` function that was used in the previous section.</span></span>

```powershell
function Test-MrParameter {

    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="10075-164">我想要您注意的是，`Test-MrParameter` 函式沒有任何一般參數。</span><span class="sxs-lookup"><span data-stu-id="10075-164">What I want you to notice is that the `Test-MrParameter` function doesn't have any common parameters.</span></span> <span data-ttu-id="10075-165">要查看一般參數有幾個不同的方式。</span><span class="sxs-lookup"><span data-stu-id="10075-165">There are a couple of different ways to see the common parameters.</span></span> <span data-ttu-id="10075-166">其中一個是使用 `Get-Command` 來檢視語法。</span><span class="sxs-lookup"><span data-stu-id="10075-166">One is by viewing the syntax using `Get-Command`.</span></span>

```powershell
Get-Command -Name Test-MrParameter -Syntax
```

```Output
Test-MrParameter [[-ComputerName] <Object>]
```

<span data-ttu-id="10075-167">另一個是使用 `Get-Command` 向下切入參數。</span><span class="sxs-lookup"><span data-stu-id="10075-167">Another is to drill down into the parameters with `Get-Command`.</span></span>

```powershell
(Get-Command -Name Test-MrParameter).Parameters.Keys
```

```Output
ComputerName
```

<span data-ttu-id="10075-168">新增 `CmdletBinding` 以將函式轉換為進階函式。</span><span class="sxs-lookup"><span data-stu-id="10075-168">Add `CmdletBinding` to turn the function into an advanced function.</span></span>

```powershell
function Test-MrCmdletBinding {

    [CmdletBinding()] #<<-- This turns a regular function into an advanced function
    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="10075-169">新增 `CmdletBinding` 會自動新增一般參數。</span><span class="sxs-lookup"><span data-stu-id="10075-169">Adding `CmdletBinding` adds the common parameters automatically.</span></span> <span data-ttu-id="10075-170">`CmdletBinding` 需要 `param` 區塊，但 `param` 區塊可以是空的。</span><span class="sxs-lookup"><span data-stu-id="10075-170">`CmdletBinding` requires a `param` block, but the `param` block can be empty.</span></span>

```powershell
Get-Command -Name Test-MrCmdletBinding -Syntax
```

```Output
Test-MrCmdletBinding [[-ComputerName] <Object>] [<CommonParameters>]
```

<span data-ttu-id="10075-171">向下切入具有 `Get-Command` 的參數，會顯示實際參數名稱，包括一般參數名稱。</span><span class="sxs-lookup"><span data-stu-id="10075-171">Drilling down into the parameters with `Get-Command` shows the actual parameter names including the common ones.</span></span>

```powershell
(Get-Command -Name Test-MrCmdletBinding).Parameters.Keys
```

```Output
ComputerName
Verbose
Debug
ErrorAction
WarningAction
InformationAction
ErrorVariable
WarningVariable
InformationVariable
OutVariable
OutBuffer
PipelineVariable
```

## <a name="supportsshouldprocess"></a><span data-ttu-id="10075-172">SupportsShouldProcess</span><span class="sxs-lookup"><span data-stu-id="10075-172">SupportsShouldProcess</span></span>

<span data-ttu-id="10075-173">`SupportsShouldProcess` 新增 **WhatIf** 和 **Confirm** 參數。</span><span class="sxs-lookup"><span data-stu-id="10075-173">`SupportsShouldProcess` adds **WhatIf** and **Confirm** parameters.</span></span> <span data-ttu-id="10075-174">只有會進行變更的命令才需要這些。</span><span class="sxs-lookup"><span data-stu-id="10075-174">These are only needed for commands that make changes.</span></span>

```powershell
function Test-MrSupportsShouldProcess {

    [CmdletBinding(SupportsShouldProcess)]
    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="10075-175">請注意，現在已有 **WhatIf** 和 **Confirm** 參數。</span><span class="sxs-lookup"><span data-stu-id="10075-175">Notice that there are now **WhatIf** and **Confirm** parameters.</span></span>

```powershell
Get-Command -Name Test-MrSupportsShouldProcess -Syntax
```

```Output
Test-MrSupportsShouldProcess [[-ComputerName] <Object>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

<span data-ttu-id="10075-176">同樣地，您也可以使用 `Get-Command` 來傳回包含實際參數名稱的清單，包括一般參數與 WhatIf 和 Confirm。</span><span class="sxs-lookup"><span data-stu-id="10075-176">Once again, you can also use `Get-Command` to return a list of the actual parameter names including the common ones along with WhatIf and Confirm.</span></span>

```powershell
(Get-Command -Name Test-MrSupportsShouldProcess).Parameters.Keys
```

```Output
ComputerName
Verbose
Debug
ErrorAction
WarningAction
InformationAction
ErrorVariable
WarningVariable
InformationVariable
OutVariable
OutBuffer
PipelineVariable
WhatIf
Confirm
```

## <a name="parameter-validation"></a><span data-ttu-id="10075-177">參數驗證</span><span class="sxs-lookup"><span data-stu-id="10075-177">Parameter Validation</span></span>

<span data-ttu-id="10075-178">及早驗證輸入。</span><span class="sxs-lookup"><span data-stu-id="10075-178">Validate input early on.</span></span> <span data-ttu-id="10075-179">當程式碼在沒有有效輸入的情況下無法執行時，為什麼要讓程式碼繼續在某路徑上執行？</span><span class="sxs-lookup"><span data-stu-id="10075-179">Why allow your code to continue on a path when it's not possible to run without valid input?</span></span>

<span data-ttu-id="10075-180">一律輸入要用於參數的變數 (指定資料類型)。</span><span class="sxs-lookup"><span data-stu-id="10075-180">Always type the variables that are being used for your parameters (specify a datatype).</span></span>

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [string]$ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="10075-181">在上述範例中，我指定 **String** 做為 **ComputerName** 參數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="10075-181">In the previous example, I've specified **String** as the datatype for the **ComputerName** parameter.</span></span> <span data-ttu-id="10075-182">這會使得它只允許指定單一電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="10075-182">This causes it to allow only a single computer name to be specified.</span></span> <span data-ttu-id="10075-183">如果透過逗號分隔清單指定多個電腦名稱，則會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="10075-183">If more than one computer name is specified via a comma-separated list, an error is generated.</span></span>

```powershell
Test-MrParameterValidation -ComputerName Server01, Server02
```

```Output
Test-MrParameterValidation : Cannot process argument transformation on parameter
'ComputerName'. Cannot convert value to type System.String.
At line:1 char:42
+ Test-MrParameterValidation -ComputerName Server01, Server02
+
    + CategoryInfo          : InvalidData: (:) [Test-MrParameterValidation], ParameterBindingArg
     umentTransformationException
    + FullyQualifiedErrorId : ParameterArgumentTransformationError,Test-MrParameterValidation
```

<span data-ttu-id="10075-184">目前的定義有個問題，就是省略 **ComputerName** 參數的值是有效的，但需要值，函式才能成功完成。</span><span class="sxs-lookup"><span data-stu-id="10075-184">The problem with the current definition is that it's valid to omit the value of the **ComputerName** parameter, but a value is required for the function to complete successfully.</span></span> <span data-ttu-id="10075-185">這就是 `Mandatory` 參數屬性派上用場的地方。</span><span class="sxs-lookup"><span data-stu-id="10075-185">This is where the `Mandatory` parameter attribute comes in handy.</span></span>

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory)]
        [string]$ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="10075-186">上一個範例中使用的語法可與 PowerShell 3.0 版和更新版本相容。</span><span class="sxs-lookup"><span data-stu-id="10075-186">The syntax used in the previous example is PowerShell version 3.0 and higher compatible.</span></span>
<span data-ttu-id="10075-187">您可以改為指定 `[Parameter(Mandatory=$true)]`，使函式與 PowerShell 2.0 版和更新版本相容。</span><span class="sxs-lookup"><span data-stu-id="10075-187">`[Parameter(Mandatory=$true)]` could be specified instead to make the function compatible with PowerShell version 2.0 and higher.</span></span> <span data-ttu-id="10075-188">既然現在需要 **ComputerName** (如果未指定)，則函式會提示您輸入一個。</span><span class="sxs-lookup"><span data-stu-id="10075-188">Now that the **ComputerName** is required, if one isn't specified, the function will prompt for one.</span></span>

```powershell
Test-MrParameterValidation
```

```Output
cmdlet Test-MrParameterValidation at command pipeline position 1
Supply values for the following parameters:
ComputerName:
```

<span data-ttu-id="10075-189">如果您想要允許 **ComputerName** 參數有多個值，請使用 **String** 資料類型，但在資料類型中加入左方括弧和右方括弧，以允許字串陣列。</span><span class="sxs-lookup"><span data-stu-id="10075-189">If you want to allow for more than one value for the **ComputerName** parameter, use the **String** datatype but add open and closed square brackets to the datatype to allow for an array of strings.</span></span>

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory)]
        [string[]]$ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="10075-190">您可能想要為 **ComputerName** 參數指定預設值 (如果未指定的話)。</span><span class="sxs-lookup"><span data-stu-id="10075-190">Maybe you want to specify a default value for the **ComputerName** parameter if one isn't specified.</span></span>
<span data-ttu-id="10075-191">問題在於，預設值無法與強制參數搭配使用。</span><span class="sxs-lookup"><span data-stu-id="10075-191">The problem is that default values can't be used with mandatory parameters.</span></span> <span data-ttu-id="10075-192">相反地，您必須使用 `ValidateNotNullOrEmpty` 參數驗證屬性搭配預設值。</span><span class="sxs-lookup"><span data-stu-id="10075-192">Instead, you'll need to use the `ValidateNotNullOrEmpty` parameter validation attribute with a default value.</span></span>

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="10075-193">即使是設定預設值，也請嘗試不要使用靜態值。</span><span class="sxs-lookup"><span data-stu-id="10075-193">Even when setting a default value, try not to use static values.</span></span> <span data-ttu-id="10075-194">在上述範例中，使用 `$env:COMPUTERNAME` 做為預設值，如果未提供值，則會自動轉譯為本機電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="10075-194">In the previous example, `$env:COMPUTERNAME` is used as the default value, which is automatically translated into the local computer name if a value is not provided.</span></span>

## <a name="verbose-output"></a><span data-ttu-id="10075-195">詳細資訊輸出</span><span class="sxs-lookup"><span data-stu-id="10075-195">Verbose Output</span></span>

<span data-ttu-id="10075-196">雖然內嵌註解很實用，特別是當您撰寫一些複雜的程式碼時，使用者永遠不會看到這些註解，除非使用者查看程式碼本身。</span><span class="sxs-lookup"><span data-stu-id="10075-196">While inline comments are useful, especially if you're writing some complex code, they never get seen by users unless they look into the code itself.</span></span>

<span data-ttu-id="10075-197">下列範例中所示的函式在 `foreach` 迴圈中具有內嵌註解。</span><span class="sxs-lookup"><span data-stu-id="10075-197">The function shown in the following example has an inline comment in the `foreach` loop.</span></span> <span data-ttu-id="10075-198">雖然這個特定的註解可能不太難找到，但想像一下若函式包含數百行程式碼。</span><span class="sxs-lookup"><span data-stu-id="10075-198">While this particular comment may not be that difficult to locate, imagine if the function included hundreds of lines of code.</span></span>

```powershell
function Test-MrVerboseOutput {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    foreach ($Computer in $ComputerName) {
        #Attempting to perform some action on $Computer <<-- Don't use
        #inline comments like this, use write verbose instead.
        Write-Output $Computer
    }

}
```

<span data-ttu-id="10075-199">較好的選項是使用 `Write-Verbose`，而不是內嵌註解。</span><span class="sxs-lookup"><span data-stu-id="10075-199">A better option is to use `Write-Verbose` instead of inline comments.</span></span>

```powershell
function Test-MrVerboseOutput {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    foreach ($Computer in $ComputerName) {
        Write-Verbose -Message "Attempting to perform some action on $Computer"
        Write-Output $Computer
    }

}
```

<span data-ttu-id="10075-200">呼叫函式而未使用 **Verbose** 參數時，將不會顯示詳細資訊輸出。</span><span class="sxs-lookup"><span data-stu-id="10075-200">When the function is called without the **Verbose** parameter, the verbose output won't be displayed.</span></span>

```powershell
Test-MrVerboseOutput -ComputerName Server01, Server02
```

<span data-ttu-id="10075-201">使用 **Verbose** 參數呼叫時，將會顯示詳細資訊輸出。</span><span class="sxs-lookup"><span data-stu-id="10075-201">When it's called with the **Verbose** parameter, the verbose output will be displayed.</span></span>

```powershell
Test-MrVerboseOutput -ComputerName Server01, Server02 -Verbose
```

## <a name="pipeline-input"></a><span data-ttu-id="10075-202">管線輸入</span><span class="sxs-lookup"><span data-stu-id="10075-202">Pipeline Input</span></span>

<span data-ttu-id="10075-203">想要函式接受管線輸入時，需要一些額外的程式碼。</span><span class="sxs-lookup"><span data-stu-id="10075-203">When you want your function to accept pipeline input, some additional coding is necessary.</span></span> <span data-ttu-id="10075-204">如本書稍早所述，命令可以接受管線輸入 **by value** (by type)，或 **by property name**。</span><span class="sxs-lookup"><span data-stu-id="10075-204">As mentioned earlier in this book, commands can accept pipeline input **by value** (by type) or **by property name**.</span></span> <span data-ttu-id="10075-205">您可以撰寫函式，就像原生命令一樣，使得它們會接受這兩個類型中的一或兩個輸入。</span><span class="sxs-lookup"><span data-stu-id="10075-205">You can write your functions just like the native commands so that they accept either one or both of these types of input.</span></span>

<span data-ttu-id="10075-206">若要接受輸入 **by value**，請為該特定參數指定 `ValueFromPipeline` 參數屬性。</span><span class="sxs-lookup"><span data-stu-id="10075-206">To accept pipeline input **by value**, specified the `ValueFromPipeline` parameter attribute for that particular parameter.</span></span> <span data-ttu-id="10075-207">請記住，您只能透過每個資料類型中的一個來接受管線輸入 **by value**。</span><span class="sxs-lookup"><span data-stu-id="10075-207">Keep in mind that you can only accept pipeline input **by value** from one of each datatype.</span></span> <span data-ttu-id="10075-208">例如，如果您有會接受字串輸入的兩個參數，則其中只有一個可接受管線輸入 **by value**，因為如果您同時為這兩個字串參數指定它，則管線輸入不會知道要繫結的是哪一個。</span><span class="sxs-lookup"><span data-stu-id="10075-208">For example, if you have two parameters that accept string input, only one of those can accept pipeline input **by value** because if you specified it for both of the string parameters, the pipeline input wouldn't know which one to bind to.</span></span> <span data-ttu-id="10075-209">這是我將這種管線輸入稱為 _by type_ 而非 **by value** 的另一個原因。</span><span class="sxs-lookup"><span data-stu-id="10075-209">This is another reason I call this type of pipeline input _by type_ instead of **by value**.</span></span>

<span data-ttu-id="10075-210">管線輸入一次會出現在一個項目中，與 `foreach` 迴圈中處理項目的方式類似。</span><span class="sxs-lookup"><span data-stu-id="10075-210">Pipeline input comes in one item at a time similar to the way items are handled in a `foreach` loop.</span></span>
<span data-ttu-id="10075-211">如果您接受陣列做為輸入，則至少需要 `process` 區塊來處理每個項目。</span><span class="sxs-lookup"><span data-stu-id="10075-211">At a minimum, a `process` block is required to process each of these items if you're accepting an array as input.</span></span> <span data-ttu-id="10075-212">如果您只接受單一值做為輸入，則不需要 `process` 區塊，但仍建議您為了一致性而指定它。</span><span class="sxs-lookup"><span data-stu-id="10075-212">If you're only accepting a single value as input, a `process` block isn't necessary, but I still recommend specifying it for consistency.</span></span>

```powershell
function Test-MrPipelineInput {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline)]
        [string[]]$ComputerName
    )

    PROCESS {
        Write-Output $ComputerName
    }

}
```

<span data-ttu-id="10075-213">接受管線輸入 **by property name** 也是類似的，但它是使用 `ValueFromPipelineByPropertyName` 參數屬性指定，且不論資料類型為何，都可以為任何數目的參數指定。</span><span class="sxs-lookup"><span data-stu-id="10075-213">Accepting pipeline input **by property name** is similar except it's specified with the `ValueFromPipelineByPropertyName` parameter attribute and it can be specified for any number of parameters regardless of datatype.</span></span> <span data-ttu-id="10075-214">關鍵在於要以管線送入的命令輸出必須具有符合參數名稱的屬性名稱，或您函式的參數別名。</span><span class="sxs-lookup"><span data-stu-id="10075-214">The key is that the output of the command that's being piped in has to have a property name that matches the name of the parameter or a parameter alias of your function.</span></span>

```powershell
function Test-MrPipelineInput {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
            Write-Output $ComputerName
    }

}
```

<span data-ttu-id="10075-215">`BEGIN` 和 `END` 區塊是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="10075-215">`BEGIN` and `END` blocks are optional.</span></span> <span data-ttu-id="10075-216">`BEGIN` 會在 `PROCESS` 區塊之前指定，並在從管線收到項目之前，用來執行任何初始工作。</span><span class="sxs-lookup"><span data-stu-id="10075-216">`BEGIN` would be specified before the `PROCESS` block and is used to perform any initial work prior to the items being received from the pipeline.</span></span> <span data-ttu-id="10075-217">務必了解這點。</span><span class="sxs-lookup"><span data-stu-id="10075-217">This is important to understand.</span></span> <span data-ttu-id="10075-218">以管線送入的值無法在 `BEGIN` 區塊中存取。</span><span class="sxs-lookup"><span data-stu-id="10075-218">Values that are piped in are not accessible in the `BEGIN` block.</span></span> <span data-ttu-id="10075-219">`END` 區塊會在 `PROCESS` 區塊之後指定，且會在以管線送入的所有項目都經過處理之後用於清除。</span><span class="sxs-lookup"><span data-stu-id="10075-219">The `END` block would be specified after the `PROCESS` block and is used for cleanup once all of the items that are piped in have been processed.</span></span>

## <a name="error-handling"></a><span data-ttu-id="10075-220">錯誤處理</span><span class="sxs-lookup"><span data-stu-id="10075-220">Error Handling</span></span>

<span data-ttu-id="10075-221">下列範例中所顯示的函式會在無法連絡電腦時產生未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="10075-221">The function shown in the following example generates an unhandled exception when a computer can't be contacted.</span></span>

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            Test-WSMan -ComputerName $Computer
        }
    }

}
```

<span data-ttu-id="10075-222">有幾種不同的方式可以處理 PowerShell 中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="10075-222">There are a couple of different ways to handle errors in PowerShell.</span></span> <span data-ttu-id="10075-223">`Try/Catch` 是處理錯誤的更現代化方式。</span><span class="sxs-lookup"><span data-stu-id="10075-223">`Try/Catch` is the more modern way to handle errors.</span></span>

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            try {
                Test-WSMan -ComputerName $Computer
            }
            catch {
                Write-Warning -Message "Unable to connect to Computer: $Computer"
            }
        }
    }

}
```

<span data-ttu-id="10075-224">雖然上述範例中顯示的函式使用錯誤處理，但它也會產生未處理的例外狀況，因為命令未產生終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="10075-224">Although the function shown in the previous example uses error handling, it also generates an unhandled exception because the command doesn't generate a terminating error.</span></span> <span data-ttu-id="10075-225">也務必了解這點。</span><span class="sxs-lookup"><span data-stu-id="10075-225">This is also important to understand.</span></span> <span data-ttu-id="10075-226">只攔截到終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="10075-226">Only terminating errors are caught.</span></span> <span data-ttu-id="10075-227">指定 **ErrorAction** 參數搭配 **Stop** 做為值，以將非終止錯誤轉換成會終止的錯誤。</span><span class="sxs-lookup"><span data-stu-id="10075-227">Specify the **ErrorAction** parameter with **Stop** as the value to turn a non-terminating error into a terminating one.</span></span>

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            try {
                Test-WSMan -ComputerName $Computer -ErrorAction Stop
            }
            catch {
                Write-Warning -Message "Unable to connect to Computer: $Computer"
            }
        }
    }

}
```

<span data-ttu-id="10075-228">除非絕對必要，否則請勿修改全域 `$ErrorActionPreference` 變數。</span><span class="sxs-lookup"><span data-stu-id="10075-228">Don't modify the global `$ErrorActionPreference` variable unless absolutely necessary.</span></span> <span data-ttu-id="10075-229">如果您直接從 PowerShell 函式內使用類似 .NET 的項目，就無法在命令本身上指定 **ErrorAction**。</span><span class="sxs-lookup"><span data-stu-id="10075-229">If you're using something like .NET directly from within your PowerShell function, you can't specify the **ErrorAction** on the command itself.</span></span> <span data-ttu-id="10075-230">在該情況下，您可能需要變更全域 `$ErrorActionPreference` 變數，但如果您的確變更它，請在嘗試命令之後立即將它變更回來。</span><span class="sxs-lookup"><span data-stu-id="10075-230">In that scenario, you might need to change the global `$ErrorActionPreference` variable, but if you do change it, change it back immediately after trying the command.</span></span>

## <a name="comment-based-help"></a><span data-ttu-id="10075-231">註解型說明</span><span class="sxs-lookup"><span data-stu-id="10075-231">Comment-Based Help</span></span>

<span data-ttu-id="10075-232">將註解型說明新增至您的函式是最佳做法，這能夠讓您所共用的人員知道如何使用內容。</span><span class="sxs-lookup"><span data-stu-id="10075-232">It's considered to be a best practice to add comment based help to your functions so the people you're sharing them with will know how to use them.</span></span>

```powershell
function Get-MrAutoStoppedService {

<#
.SYNOPSIS
    Returns a list of services that are set to start automatically, are not
    currently running, excluding the services that are set to delayed start.

.DESCRIPTION
    Get-MrAutoStoppedService is a function that returns a list of services from
    the specified remote computer(s) that are set to start automatically, are not
    currently running, and it excludes the services that are set to start automatically
    with a delayed startup.

.PARAMETER ComputerName
    The remote computer(s) to check the status of the services on.

.PARAMETER Credential
    Specifies a user account that has permission to perform this action. The default
    is the current user.

.EXAMPLE
     Get-MrAutoStoppedService -ComputerName 'Server1', 'Server2'

.EXAMPLE
     'Server1', 'Server2' | Get-MrAutoStoppedService

.EXAMPLE
     Get-MrAutoStoppedService -ComputerName 'Server1' -Credential (Get-Credential)

.INPUTS
    String

.OUTPUTS
    PSCustomObject

.NOTES
    Author:  Mike F Robbins
    Website: http://mikefrobbins.com
    Twitter: @mikefrobbins
#>

    [CmdletBinding()]
    param (

    )

    #Function Body

}
```

<span data-ttu-id="10075-233">將註解型說明新增至函式時，可以擷取其說明，就像預設的內建命令一樣。</span><span class="sxs-lookup"><span data-stu-id="10075-233">When you add comment based help to your functions, help can be retrieved for them just like the default built-in commands.</span></span>

<span data-ttu-id="10075-234">用於在 PowerShell 中撰寫函式的所有語法，可能顯得過於困難，尤其是對於剛開始的新手來說。</span><span class="sxs-lookup"><span data-stu-id="10075-234">All of the syntax for writing a function in PowerShell can seem overwhelming especially for someone who is just getting started.</span></span> <span data-ttu-id="10075-235">有時候，如果我不記得某個項目的語法，我會在個別監視器上開啟第二個 ISE 複本，並在輸入我的函式的程式碼時，檢視「Cmdlet (進階函式) - 完整」程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="10075-235">Often times if I can't remember the syntax for something, I'll open a second copy of the ISE on a separate monitor and view the "Cmdlet (advanced function) - Complete" snippet while typing in the code for my function.</span></span> <span data-ttu-id="10075-236">您可以使用 <kbd>Ctrl</kbd>+<kbd>J</kbd> 按鍵組合，在 PowerShell ISE 中存取程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="10075-236">Snippets can be accessed in the PowerShell ISE using the <kbd>Ctrl</kbd>+<kbd>J</kbd> key combination.</span></span>

## <a name="summary"></a><span data-ttu-id="10075-237">摘要</span><span class="sxs-lookup"><span data-stu-id="10075-237">Summary</span></span>

<span data-ttu-id="10075-238">在本章中，您已了解在 PowerShell 中撰寫函式的基本概念，包括如何將函式轉換成進階函式，以及在撰寫 PowerShell 函式時應該考慮的一些更重要的元素，例如，參數驗證、詳細資訊輸出、管線輸入、錯誤處理和註解型說明。</span><span class="sxs-lookup"><span data-stu-id="10075-238">In this chapter you've learned the basics of writing functions in PowerShell to include how to turn a function into an advanced function and some of the more important elements that you should consider when writing PowerShell functions such as parameter validation, verbose output, pipeline input, error handling, and comment based help.</span></span>

## <a name="review"></a><span data-ttu-id="10075-239">檢閱</span><span class="sxs-lookup"><span data-stu-id="10075-239">Review</span></span>

1. <span data-ttu-id="10075-240">如何在 PowerShell 中取得核准的動詞清單？</span><span class="sxs-lookup"><span data-stu-id="10075-240">How do you obtain a list of approved verbs in PowerShell?</span></span>
1. <span data-ttu-id="10075-241">如何將 PowerShell 函式轉換成進階函式？</span><span class="sxs-lookup"><span data-stu-id="10075-241">How do you turn a PowerShell function into an advanced function?</span></span>
1. <span data-ttu-id="10075-242">何時應該將 **WhatIf** 和 **Confirm** 參數新增至您的 PowerShell 函式？</span><span class="sxs-lookup"><span data-stu-id="10075-242">When should **WhatIf** and **Confirm** parameters be added to your PowerShell functions?</span></span>
1. <span data-ttu-id="10075-243">如何將非終止錯誤轉變成終止的錯誤？</span><span class="sxs-lookup"><span data-stu-id="10075-243">How do you turn a non-terminating error into a terminating one?</span></span>
1. <span data-ttu-id="10075-244">為什麼您應該在函式中新增註解型說明？</span><span class="sxs-lookup"><span data-stu-id="10075-244">Why should you add comment based help to your functions?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="10075-245">建議閱讀資料</span><span class="sxs-lookup"><span data-stu-id="10075-245">Recommended Reading</span></span>

- <span data-ttu-id="10075-246">[about_Functions][]</span><span class="sxs-lookup"><span data-stu-id="10075-246">[about_Functions][]</span></span>
- <span data-ttu-id="10075-247">[about_Functions_Advanced_Parameters][]</span><span class="sxs-lookup"><span data-stu-id="10075-247">[about_Functions_Advanced_Parameters][]</span></span>
- <span data-ttu-id="10075-248">[about_CommonParameters][]</span><span class="sxs-lookup"><span data-stu-id="10075-248">[about_CommonParameters][]</span></span>
- <span data-ttu-id="10075-249">[about_Functions_CmdletBindingAttribute][]</span><span class="sxs-lookup"><span data-stu-id="10075-249">[about_Functions_CmdletBindingAttribute][]</span></span>
- <span data-ttu-id="10075-250">[about_Functions_Advanced][]</span><span class="sxs-lookup"><span data-stu-id="10075-250">[about_Functions_Advanced][]</span></span>
- <span data-ttu-id="10075-251">[about_Try_Catch_Finally][]</span><span class="sxs-lookup"><span data-stu-id="10075-251">[about_Try_Catch_Finally][]</span></span>
- <span data-ttu-id="10075-252">[about_Comment_Based_Help][]</span><span class="sxs-lookup"><span data-stu-id="10075-252">[about_Comment_Based_Help][]</span></span>
- <span data-ttu-id="10075-253">[影片：使用進階函式和指令碼模組的 PowerShell 工具製作][]</span><span class="sxs-lookup"><span data-stu-id="10075-253">[Video: PowerShell Toolmaking with Advanced Functions and Script Modules][]</span></span>

<!-- link references -->
[about_Functions]: /powershell/module/microsoft.powershell.core/about/about_functions
[about_Functions_Advanced_Parameters]: /powershell/module/microsoft.powershell.core/about/about_functions_advanced_parameters
[about_CommonParameters]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[about_Functions_CmdletBindingAttribute]: /powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute
[about_Functions_Advanced]: /powershell/module/microsoft.powershell.core/about/about_functions_advanced
[about_Try_Catch_Finally]: /powershell/module/microsoft.powershell.core/about/about_try_catch_finally
[about_Comment_Based_Help]: /powershell/module/microsoft.powershell.core/about/about_comment_based_help
[影片：使用進階函式和指令碼模組的 PowerShell 工具製作]: https://mikefrobbins.com/2016/05/26/video-powershell-toolmaking-with-advanced-functions-and-script-modules/
[Video: PowerShell Toolmaking with Advanced Functions and Script Modules]: https://mikefrobbins.com/2016/05/26/video-powershell-toolmaking-with-advanced-functions-and-script-modules/
[Pascal 命名法的大小寫]: /dotnet/standard/design-guidelines/capitalization-conventions
[Pascal case]: /dotnet/standard/design-guidelines/capitalization-conventions
