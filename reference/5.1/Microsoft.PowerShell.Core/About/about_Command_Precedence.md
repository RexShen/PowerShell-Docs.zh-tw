---
description: 描述 PowerShell 如何決定要執行哪個命令。
keywords: powershell,cmdlet
ms.date: 02/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_command_precedence?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Command_Precedence
ms.openlocfilehash: 288c01af2d66aca786cf1b97ad844dd91cac45ca
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207691"
---
# <a name="about-command-precedence"></a><span data-ttu-id="6233a-104">關於命令優先順序</span><span class="sxs-lookup"><span data-stu-id="6233a-104">About Command Precedence</span></span>

## <a name="short-description"></a><span data-ttu-id="6233a-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="6233a-105">Short description</span></span>
<span data-ttu-id="6233a-106">描述 PowerShell 如何決定要執行哪個命令。</span><span class="sxs-lookup"><span data-stu-id="6233a-106">Describes how PowerShell determines which command to run.</span></span>

## <a name="long-description"></a><span data-ttu-id="6233a-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="6233a-107">Long description</span></span>

<span data-ttu-id="6233a-108">命令優先順序描述當會話包含一個以上具有相同名稱的命令時，PowerShell 如何決定要執行哪個命令。</span><span class="sxs-lookup"><span data-stu-id="6233a-108">Command precedence describes how PowerShell determines which command to run when a session contains more than one command with the same name.</span></span> <span data-ttu-id="6233a-109">使用相同名稱的命令可以隱藏或取代會話中的命令。</span><span class="sxs-lookup"><span data-stu-id="6233a-109">Commands within a session can be hidden or replaced by commands with the same name.</span></span> <span data-ttu-id="6233a-110">本文說明如何執行隱藏的命令，以及如何避免命令名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="6233a-110">This article shows you how to run hidden commands and how to avoid command-name conflicts.</span></span>

## <a name="command-precedence"></a><span data-ttu-id="6233a-111">命令優先順序</span><span class="sxs-lookup"><span data-stu-id="6233a-111">Command precedence</span></span>

<span data-ttu-id="6233a-112">當 PowerShell 會話包含一個以上具有相同名稱的命令時，PowerShell 會使用下列規則來決定要執行的命令。</span><span class="sxs-lookup"><span data-stu-id="6233a-112">When a PowerShell session includes more than one command that has the same name, PowerShell determines which command to run by using the following rules.</span></span>

<span data-ttu-id="6233a-113">如果您指定命令的路徑，PowerShell 會在路徑指定的位置執行命令。</span><span class="sxs-lookup"><span data-stu-id="6233a-113">If you specify the path to a command, PowerShell runs the command at the location specified by the path.</span></span>

<span data-ttu-id="6233a-114">例如，下列命令會執行 "C： TechDocs" 目錄中的 FindDocs.ps1 腳本 \\ ：</span><span class="sxs-lookup"><span data-stu-id="6233a-114">For example, the following command runs the FindDocs.ps1 script in the "C:\\TechDocs" directory:</span></span>

```
C:\TechDocs\FindDocs.ps1
```

<span data-ttu-id="6233a-115">除了命令位於 Path 環境變數中所列的路徑中， `$env:path` 或除非您指定腳本檔案的路徑，powershell 仍不會以安全性功能 (原生) 命令執行可執行檔（包括 PowerShell 腳本）。</span><span class="sxs-lookup"><span data-stu-id="6233a-115">As a security feature, PowerShell does not run executable (native) commands, including PowerShell scripts, unless the command is located in a path that is listed in the Path environment variable `$env:path` or unless you specify the path to the script file.</span></span>

<span data-ttu-id="6233a-116">若要執行目前目錄中的腳本，請指定完整路徑，或輸入點 `.\` 以表示目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="6233a-116">To run a script that is in the current directory, specify the full path, or type a dot `.\` to represent the current directory.</span></span>

<span data-ttu-id="6233a-117">例如，若要在目前的目錄中執行 FindDocs.ps1 檔案，請輸入：</span><span class="sxs-lookup"><span data-stu-id="6233a-117">For example, to run the FindDocs.ps1 file in the current directory, type:</span></span>

```
.\FindDocs.ps1
```

### <a name="using-wildcards-in-execution"></a><span data-ttu-id="6233a-118">在執行中使用萬用字元</span><span class="sxs-lookup"><span data-stu-id="6233a-118">Using wildcards in execution</span></span>

<span data-ttu-id="6233a-119">您可以在命令執行中使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="6233a-119">You may use wildcards in command execution.</span></span> <span data-ttu-id="6233a-120">使用萬用字元 *也稱為萬用字元。*</span><span class="sxs-lookup"><span data-stu-id="6233a-120">Using wildcard characters is also known as *globbing* .</span></span>

<span data-ttu-id="6233a-121">PowerShell 會在常值相符之前，執行具有萬用字元比對的檔案。</span><span class="sxs-lookup"><span data-stu-id="6233a-121">PowerShell executes a file that has a wildcard match, before a literal match.</span></span>

<span data-ttu-id="6233a-122">例如，請考慮具有下列檔案的目錄：</span><span class="sxs-lookup"><span data-stu-id="6233a-122">For example, consider a directory with the following files:</span></span>

```
Get-ChildItem C:\temp\test


    Directory: C:\temp\test


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        5/20/2019   2:29 PM             28 a.ps1
-a----        5/20/2019   2:29 PM             28 [a1].ps1
```

<span data-ttu-id="6233a-123">這兩個腳本檔案都具有相同的內容： `$MyInvocation.MyCommand.Path` 。</span><span class="sxs-lookup"><span data-stu-id="6233a-123">Both script files have the same content: `$MyInvocation.MyCommand.Path`.</span></span>
<span data-ttu-id="6233a-124">此命令會顯示所叫用之腳本的名稱。</span><span class="sxs-lookup"><span data-stu-id="6233a-124">This command displays the name of the script that is invoked.</span></span>

<span data-ttu-id="6233a-125">當您執行時 `[a1].ps1` ， `a.ps1` 即使檔案 `[a1].ps1` 是常值相符，也會執行該檔案。</span><span class="sxs-lookup"><span data-stu-id="6233a-125">When you run `[a1].ps1`, the file `a.ps1` is executed even though the file `[a1].ps1` is a literal match.</span></span>

```powershell
C:\temp\test\[a1].ps1
```

```Output
C:\temp\test\a.ps1
```

<span data-ttu-id="6233a-126">現在讓我們刪除檔案 `a.ps1` ，然後嘗試再次執行。</span><span class="sxs-lookup"><span data-stu-id="6233a-126">Now let's delete the `a.ps1` file and attempt to run it again.</span></span>

```powershell
Remove-Item C:\temp\test\a.ps1
C:\temp\test\[a1].ps1
```

```Output
C:\temp\test\[a1].ps1
```

<span data-ttu-id="6233a-127">您可以從執行這次的輸出中看到， `[a1].ps1` 因為常值比對是該萬用字元模式的唯一檔案相符項。</span><span class="sxs-lookup"><span data-stu-id="6233a-127">You can see from the output that `[a1].ps1` runs this time because the literal match is the only file match for that wildcard pattern.</span></span>

<span data-ttu-id="6233a-128">如需 PowerShell 如何使用萬用字元的詳細資訊，請參閱 [about_Wildcards](about_Wildcards.md)。</span><span class="sxs-lookup"><span data-stu-id="6233a-128">For more information about how PowerShell uses wildcards, see [about_Wildcards](about_Wildcards.md).</span></span>

> [!NOTE]
> <span data-ttu-id="6233a-129">若要將搜尋限制為相對路徑，您必須在腳本名稱之前加上 `.\` 路徑。</span><span class="sxs-lookup"><span data-stu-id="6233a-129">To limit the search to a relative path, you must prefix the script name with the `.\` path.</span></span> <span data-ttu-id="6233a-130">這會將命令搜尋限制在相對路徑中的檔案。</span><span class="sxs-lookup"><span data-stu-id="6233a-130">This limits the search for commands to files in that relative path.</span></span> <span data-ttu-id="6233a-131">如果沒有這個前置詞，其他 PowerShell 語法可能會衝突，而且會有一些保證可以找到檔案。</span><span class="sxs-lookup"><span data-stu-id="6233a-131">Without this prefix, other PowerShell syntax may conflict and there are few guarantees that the file will be found.</span></span>

<span data-ttu-id="6233a-132">如果您未指定路徑，則 PowerShell 在針對目前會話中載入的所有專案執行命令時，會使用下列優先順序：</span><span class="sxs-lookup"><span data-stu-id="6233a-132">If you do not specify a path, PowerShell uses the following precedence order when it runs commands for all items loaded in the current session:</span></span>

  1. <span data-ttu-id="6233a-133">Alias</span><span class="sxs-lookup"><span data-stu-id="6233a-133">Alias</span></span>
  2. <span data-ttu-id="6233a-134">函式</span><span class="sxs-lookup"><span data-stu-id="6233a-134">Function</span></span>
  3. <span data-ttu-id="6233a-135">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6233a-135">Cmdlet</span></span>
  4. <span data-ttu-id="6233a-136">外部可執行檔 (程式和非 PowerShell 腳本) </span><span class="sxs-lookup"><span data-stu-id="6233a-136">External executable files (programs and non-PowerShell scripts)</span></span>

<span data-ttu-id="6233a-137">因此，如果您輸入 "help"，PowerShell 會先尋找名為的別名，然後尋找名為的函式， `help` `Help` 最後是名為的 Cmdlet `Help` 。</span><span class="sxs-lookup"><span data-stu-id="6233a-137">Therefore, if you type "help", PowerShell first looks for an alias named `help`, then a function named `Help`, and finally a cmdlet named `Help`.</span></span> <span data-ttu-id="6233a-138">它會執行它所找到的第一個 `help` 專案。</span><span class="sxs-lookup"><span data-stu-id="6233a-138">It runs the first `help` item that it finds.</span></span>

<span data-ttu-id="6233a-139">例如，如果您的會話包含 Cmdlet 和函式，且兩者皆為 `Get-Map` ，當您輸入時，PowerShell 會執行函式 `Get-Map` 。</span><span class="sxs-lookup"><span data-stu-id="6233a-139">For example, if your session contains a cmdlet and a function, both named `Get-Map`, when you type `Get-Map`, PowerShell runs the function.</span></span>

> [!NOTE]
> <span data-ttu-id="6233a-140">這僅適用于已載入的命令。</span><span class="sxs-lookup"><span data-stu-id="6233a-140">This only applies to loaded commands.</span></span> <span data-ttu-id="6233a-141">如果有一個 `build` 可執行檔和名稱為的函式別名 `build` `Invoke-Build` 未載入至目前的會話中，則 PowerShell 會改為執行 `build` 可執行檔。</span><span class="sxs-lookup"><span data-stu-id="6233a-141">If there is a `build` executable and an Alias `build` for a function with the name of `Invoke-Build` inside a module that is not loaded into the current session, PowerShell runs the `build` executable instead.</span></span> <span data-ttu-id="6233a-142">如果在此情況下找不到外部可執行檔，則不會自動載入模組。</span><span class="sxs-lookup"><span data-stu-id="6233a-142">It does not auto-load modules if it finds the external executable in this case.</span></span> <span data-ttu-id="6233a-143">只有在找不到任何外部可執行檔時，才會叫用具有指定名稱的別名、函式或 Cmdlet，進而觸發其模組的自動載入。</span><span class="sxs-lookup"><span data-stu-id="6233a-143">It is only when no external executable is found that an alias, function, or cmdlet with the given name is invoked, thereby triggering auto-loading of its module.</span></span>

<span data-ttu-id="6233a-144">當會話包含具有相同名稱之相同類型的專案時，PowerShell 會執行較新的專案。</span><span class="sxs-lookup"><span data-stu-id="6233a-144">When the session contains items of the same type that have the same name, PowerShell runs the newer item.</span></span>

<span data-ttu-id="6233a-145">例如，如果您從模組匯入另一個 `Get-Date` Cmdlet，當您輸入時 `Get-Date` ，PowerShell 會在原生版本上執行匯入的版本。</span><span class="sxs-lookup"><span data-stu-id="6233a-145">For example, if you import another `Get-Date` cmdlet from a module, when you type `Get-Date`, PowerShell runs the imported version over the native one.</span></span>

## <a name="hidden-and-replaced-items"></a><span data-ttu-id="6233a-146">隱藏和取代的專案</span><span class="sxs-lookup"><span data-stu-id="6233a-146">Hidden and replaced items</span></span>

<span data-ttu-id="6233a-147">由於這些規則的結果，專案可以用相同的名稱取代或隱藏專案。</span><span class="sxs-lookup"><span data-stu-id="6233a-147">As a result of these rules, items can be replaced or hidden by items with the same name.</span></span>

<span data-ttu-id="6233a-148">如果您仍然可以存取原始專案（例如，藉由使用模組或嵌入式管理單元名稱來限定專案名稱），則專案會「隱藏」或「隱藏」。</span><span class="sxs-lookup"><span data-stu-id="6233a-148">Items are "hidden" or "shadowed" if you can still access the original item, such as by qualifying the item name with a module or snap-in name.</span></span>

<span data-ttu-id="6233a-149">例如，如果您匯入的函式名稱與會話中的 Cmdlet 相同，則會隱藏此 Cmdlet (但不會取代) ，因為它是從嵌入式管理單元或模組匯入。</span><span class="sxs-lookup"><span data-stu-id="6233a-149">For example, if you import a function that has the same name as a cmdlet in the session, the cmdlet is hidden (but not replaced) because it was imported from a snap-in or module.</span></span>

<span data-ttu-id="6233a-150">如果您無法再存取原始專案，則會「取代」或「覆寫」專案。</span><span class="sxs-lookup"><span data-stu-id="6233a-150">Items are "replaced" or "overwritten" if you can no longer access the original item.</span></span>

<span data-ttu-id="6233a-151">例如，如果您匯入的變數與會話中的變數具有相同的名稱，則原始變數會被取代，而且無法再存取。</span><span class="sxs-lookup"><span data-stu-id="6233a-151">For example, if you import a variable that has the same name as a variable in the session, the original variable is replaced and is no longer accessible.</span></span>
<span data-ttu-id="6233a-152">您無法使用模組名稱來限定變數。</span><span class="sxs-lookup"><span data-stu-id="6233a-152">You cannot qualify a variable with a module name.</span></span>

<span data-ttu-id="6233a-153">此外，如果您在命令列中輸入函式，然後匯入具有相同名稱的函式，就會取代原始函式，而且無法再存取該函數。</span><span class="sxs-lookup"><span data-stu-id="6233a-153">Also, if you type a function at the command line and then import a function with the same name, the original function is replaced and is no longer accessible.</span></span>

### <a name="finding-hidden-commands"></a><span data-ttu-id="6233a-154">尋找隱藏的命令</span><span class="sxs-lookup"><span data-stu-id="6233a-154">Finding hidden commands</span></span>

<span data-ttu-id="6233a-155">[Get 命令](xref:Microsoft.PowerShell.Core.Get-Command)Cmdlet 的 **all** 參數會取得具有指定名稱的所有命令，即使它們已隱藏或被取代亦同。</span><span class="sxs-lookup"><span data-stu-id="6233a-155">The **All** parameter of the [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command) cmdlet gets all commands with the specified name, even if they are hidden or replaced.</span></span> <span data-ttu-id="6233a-156">從 PowerShell 3.0 開始，根據預設， `Get-Command` 只會取得您輸入命令名稱時所執行的命令。</span><span class="sxs-lookup"><span data-stu-id="6233a-156">Beginning in PowerShell 3.0, by default, `Get-Command` gets only the commands that run when you type the command name.</span></span>

<span data-ttu-id="6233a-157">在下列範例中，會話包含函式 `Get-Date` 和 [取得日期](xref:Microsoft.PowerShell.Utility.Get-Date) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6233a-157">In the following examples, the session includes a `Get-Date` function and a [Get-Date](xref:Microsoft.PowerShell.Utility.Get-Date) cmdlet.</span></span>

<span data-ttu-id="6233a-158">下列命令會取得在 `Get-Date` 您輸入時執行的命令 `Get-Date` 。</span><span class="sxs-lookup"><span data-stu-id="6233a-158">The following command gets the `Get-Date` command that runs when you type `Get-Date`.</span></span>

```powershell
Get-Command Get-Date
```

```output
CommandType     Name                      ModuleName
-----------     ----                      ----------
Function        Get-Date
```

<span data-ttu-id="6233a-159">下列命令使用 **all** 參數來取得所有 `Get-Date` 命令。</span><span class="sxs-lookup"><span data-stu-id="6233a-159">The following command uses the **All** parameter to get all `Get-Date` commands.</span></span>

```powershell
Get-Command Get-Date -All
```

```output
CommandType     Name                      ModuleName
-----------     ----                      ----------
Function        Get-Date
Cmdlet          Get-Date                  Microsoft.PowerShell.Utility
```

### <a name="running-hidden-commands"></a><span data-ttu-id="6233a-160">執行隱藏的命令</span><span class="sxs-lookup"><span data-stu-id="6233a-160">Running hidden commands</span></span>

<span data-ttu-id="6233a-161">您可以指定專案屬性來區別命令與可能有相同名稱的其他命令，以執行特定命令。</span><span class="sxs-lookup"><span data-stu-id="6233a-161">You can run particular commands by specifying item properties that distinguish the command from other commands that might have the same name.</span></span> <span data-ttu-id="6233a-162">您可以使用這個方法來執行任何命令，但它特別適用于執行隱藏的命令。</span><span class="sxs-lookup"><span data-stu-id="6233a-162">You can use this method to run any command, but it is especially useful for running hidden commands.</span></span>

#### <a name="qualified-names"></a><span data-ttu-id="6233a-163">限定名稱</span><span class="sxs-lookup"><span data-stu-id="6233a-163">Qualified names</span></span>

<span data-ttu-id="6233a-164">使用 Cmdlet 的模組限定名稱，可讓您執行具有相同名稱的專案所隱藏的命令。</span><span class="sxs-lookup"><span data-stu-id="6233a-164">Using the module-qualified name of a cmdlet allows you to run commands hidden by an item with the same name.</span></span> <span data-ttu-id="6233a-165">例如，您可以藉 `Get-Date` 由使用其模組名稱（如其模組名稱 **Microsoft.PowerShell.Utility** ）來執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6233a-165">For example, you can run the `Get-Date` cmdlet by qualifying it with its module name **Microsoft.PowerShell.Utility** .</span></span>

<span data-ttu-id="6233a-166">撰寫您要散發的腳本時，請使用這個慣用的方法。</span><span class="sxs-lookup"><span data-stu-id="6233a-166">Use this preferred method when writing scripts that you intend to distribute.</span></span> <span data-ttu-id="6233a-167">您無法預測腳本執行所在的會話中可能存在哪些命令。</span><span class="sxs-lookup"><span data-stu-id="6233a-167">You cannot predict which commands might be present in the session in which the script runs.</span></span>

```powershell
New-Alias -Name "Get-Date" -Value "Get-ChildItem"
Microsoft.PowerShell.Utility\Get-Date
```

```output
Tuesday, September 4, 2018 8:17:25 AM
```

<span data-ttu-id="6233a-168">若要執行 `New-Map` 模組所新增的命令 `MapFunctions` ，請使用其模組限定名稱：</span><span class="sxs-lookup"><span data-stu-id="6233a-168">To run a `New-Map` command that was added by the `MapFunctions` module, use its module-qualified name:</span></span>

```powershell
MapFunctions\New-Map
```

<span data-ttu-id="6233a-169">若要尋找從中匯入命令的模組，請使用命令的 **ModuleName** 屬性。</span><span class="sxs-lookup"><span data-stu-id="6233a-169">To find the module from which a command was imported, use the **ModuleName** property of commands.</span></span>

```
(Get-Command <command-name>).ModuleName
```

<span data-ttu-id="6233a-170">例如，若要尋找 Cmdlet 的來源 `Get-Date` ，請輸入：</span><span class="sxs-lookup"><span data-stu-id="6233a-170">For example, to find the source of the `Get-Date` cmdlet, type:</span></span>

```powershell
(Get-Command Get-Date).ModuleName
```

```output
Microsoft.PowerShell.Utility
```

> [!NOTE]
> <span data-ttu-id="6233a-171">您無法限定變數或別名。</span><span class="sxs-lookup"><span data-stu-id="6233a-171">You cannot qualify variables or aliases.</span></span>

#### <a name="call-operator"></a><span data-ttu-id="6233a-172">呼叫運算子</span><span class="sxs-lookup"><span data-stu-id="6233a-172">Call operator</span></span>

<span data-ttu-id="6233a-173">您也可以使用 `Call` 運算子 `&` 來執行隱藏的命令，方法是將它與 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem) 的呼叫結合， (別名是 "Dir" ) `Get-Command` 或 [Get 模組](xref:Microsoft.PowerShell.Core.Get-Module)。</span><span class="sxs-lookup"><span data-stu-id="6233a-173">You can also use the `Call` operator `&` to run hidden commands by combining it with a call to [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) (the alias is "dir"), `Get-Command` or [Get-Module](xref:Microsoft.PowerShell.Core.Get-Module).</span></span>

<span data-ttu-id="6233a-174">呼叫運算子會在子範圍內執行字串和腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="6233a-174">The call operator executes strings and script blocks in a child scope.</span></span> <span data-ttu-id="6233a-175">如需詳細資訊，請參閱 [about_Operators](about_Operators.md)。</span><span class="sxs-lookup"><span data-stu-id="6233a-175">For more information, see [about_Operators](about_Operators.md).</span></span>

<span data-ttu-id="6233a-176">例如，如果您有一個名為 `Map` 的函式，該函式是由名為的別名所隱藏 `Map` ，請使用下列命令來執行函數。</span><span class="sxs-lookup"><span data-stu-id="6233a-176">For example, if you have a function named `Map` that is hidden by an alias named `Map`, use the following command to run the function.</span></span>

```powershell
&(Get-Command -Name Map -CommandType Function)
```

<span data-ttu-id="6233a-177">或</span><span class="sxs-lookup"><span data-stu-id="6233a-177">or</span></span>

```powershell
&(dir Function:\map)
```

<span data-ttu-id="6233a-178">您也可以將隱藏的命令儲存在變數中，讓它更容易執行。</span><span class="sxs-lookup"><span data-stu-id="6233a-178">You can also save your hidden command in a variable to make it easier to run.</span></span>

<span data-ttu-id="6233a-179">例如，下列命令會將函數儲存 `Map` 在變數中 `$myMap` ，然後使用 `Call` 運算子來執行它。</span><span class="sxs-lookup"><span data-stu-id="6233a-179">For example, the following command saves the `Map` function in the `$myMap` variable and then uses the `Call` operator to run it.</span></span>

```powershell
$myMap = (Get-Command -Name map -CommandType function)
&($myMap)
```

### <a name="replaced-items"></a><span data-ttu-id="6233a-180">取代的專案</span><span class="sxs-lookup"><span data-stu-id="6233a-180">Replaced items</span></span>

<span data-ttu-id="6233a-181">「已取代」專案是指無法再存取的專案。</span><span class="sxs-lookup"><span data-stu-id="6233a-181">A "replaced" item is one that you can no longer access.</span></span> <span data-ttu-id="6233a-182">您可以從模組或嵌入式管理單元匯入相同名稱的專案，以取代專案。</span><span class="sxs-lookup"><span data-stu-id="6233a-182">You can replace items by importing items of the same name from a module or snap-in.</span></span>

<span data-ttu-id="6233a-183">例如，如果您 `Get-Map` 在會話中輸入函式，並匯入名為的函式 `Get-Map` ，它會取代原始的函式。</span><span class="sxs-lookup"><span data-stu-id="6233a-183">For example, if you type a `Get-Map` function in your session, and you import a function called `Get-Map`, it replaces the original function.</span></span> <span data-ttu-id="6233a-184">您無法在目前的會話中取得它。</span><span class="sxs-lookup"><span data-stu-id="6233a-184">You cannot retrieve it in the current session.</span></span>

<span data-ttu-id="6233a-185">無法隱藏變數和別名，因為您無法使用呼叫運算子或限定名稱來執行它們。</span><span class="sxs-lookup"><span data-stu-id="6233a-185">Variables and aliases cannot be hidden because you cannot use a call operator or a qualified name to run them.</span></span> <span data-ttu-id="6233a-186">當您從模組或嵌入式管理單元匯入變數和別名時，會以相同的名稱取代會話中的變數。</span><span class="sxs-lookup"><span data-stu-id="6233a-186">When you import variables and aliases from a module or snap-in, they replace variables in the session with the same name.</span></span>

### <a name="avoiding-name-conflicts"></a><span data-ttu-id="6233a-187">避免名稱衝突</span><span class="sxs-lookup"><span data-stu-id="6233a-187">Avoiding name conflicts</span></span>

<span data-ttu-id="6233a-188">管理命令名稱衝突的最佳方式是防止它們。</span><span class="sxs-lookup"><span data-stu-id="6233a-188">The best way to manage command name conflicts is to prevent them.</span></span> <span data-ttu-id="6233a-189">當您為命令命名時，請使用唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="6233a-189">When you name your commands, use a unique name.</span></span> <span data-ttu-id="6233a-190">例如，將您的姓名縮寫或公司名稱縮寫加入命令中的名詞。</span><span class="sxs-lookup"><span data-stu-id="6233a-190">For example, add your initials or company name acronym to the nouns in your commands.</span></span>

<span data-ttu-id="6233a-191">此外，當您從 PowerShell 模組或另一個會話將命令匯入會話時，請使用 `Prefix` [import-module](xref:Microsoft.PowerShell.Core.Import-Module) 的參數或</span><span class="sxs-lookup"><span data-stu-id="6233a-191">Also, when you import commands into your session from a PowerShell module or from another session, use the `Prefix` parameter of the [Import-Module](xref:Microsoft.PowerShell.Core.Import-Module) or</span></span>

<span data-ttu-id="6233a-192">[Import-module](xref:Microsoft.PowerShell.Utility.Import-PSSession) Cmdlet 會將前置詞新增至命令名稱中的名詞。</span><span class="sxs-lookup"><span data-stu-id="6233a-192">[Import-PSSession](xref:Microsoft.PowerShell.Utility.Import-PSSession) cmdlet to add a prefix to the nouns in the names of commands.</span></span>

<span data-ttu-id="6233a-193">例如， `Get-Date` `Set-Date` 當您匯入模組時，下列命令可避免與 PowerShell 隨附的和 Cmdlet 發生衝突 `DateFunctions` 。</span><span class="sxs-lookup"><span data-stu-id="6233a-193">For example, the following command avoids any conflict with the `Get-Date` and `Set-Date` cmdlets that come with PowerShell when you import the `DateFunctions` module.</span></span>

```powershell
Import-Module -Name DateFunctions -Prefix ZZ
```

<span data-ttu-id="6233a-194">如需詳細資訊，請參閱 `Import-Module` 和 `Import-PSSession` 下文。</span><span class="sxs-lookup"><span data-stu-id="6233a-194">For more information, see `Import-Module` and `Import-PSSession` below.</span></span>

## <a name="see-also"></a><span data-ttu-id="6233a-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6233a-195">See also</span></span>

- [<span data-ttu-id="6233a-196">about_Path_Syntax</span><span class="sxs-lookup"><span data-stu-id="6233a-196">about_Path_Syntax</span></span>](about_Path_Syntax.md)
- [<span data-ttu-id="6233a-197">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="6233a-197">about_Aliases</span></span>](about_Aliases.md)
- [<span data-ttu-id="6233a-198">about_Functions</span><span class="sxs-lookup"><span data-stu-id="6233a-198">about_Functions</span></span>](about_Functions.md)
- [<span data-ttu-id="6233a-199">Alias-Provider</span><span class="sxs-lookup"><span data-stu-id="6233a-199">Alias-Provider</span></span>](../../Microsoft.PowerShell.Core/About/about_Alias_Provider.md)
- [<span data-ttu-id="6233a-200">Function-Provider</span><span class="sxs-lookup"><span data-stu-id="6233a-200">Function-Provider</span></span>](../../Microsoft.PowerShell.Core/About/about_Function_Provider.md)
- [<span data-ttu-id="6233a-201">Get-Command</span><span class="sxs-lookup"><span data-stu-id="6233a-201">Get-Command</span></span>](xref:Microsoft.PowerShell.Core.Get-Command)
- [<span data-ttu-id="6233a-202">Import-Module</span><span class="sxs-lookup"><span data-stu-id="6233a-202">Import-Module</span></span>](xref:Microsoft.PowerShell.Core.Import-Module)
- [<span data-ttu-id="6233a-203">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="6233a-203">Import-PSSession</span></span>](xref:Microsoft.PowerShell.Utility.Import-PSSession)
