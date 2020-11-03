---
description: 變數
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_variable_provider?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 變數提供者
ms.openlocfilehash: c58ec641db0902088bf931d8bf4a48f5f7fa2ab8
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206815"
---
# <a name="variable-provider"></a><span data-ttu-id="d43c6-104">變數提供者</span><span class="sxs-lookup"><span data-stu-id="d43c6-104">Variable provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="d43c6-105">提供者名稱</span><span class="sxs-lookup"><span data-stu-id="d43c6-105">Provider name</span></span>
<span data-ttu-id="d43c6-106">變數</span><span class="sxs-lookup"><span data-stu-id="d43c6-106">Variable</span></span>

## <a name="drives"></a><span data-ttu-id="d43c6-107">磁碟機</span><span class="sxs-lookup"><span data-stu-id="d43c6-107">Drives</span></span>

`Variable:`

## <a name="capabilities"></a><span data-ttu-id="d43c6-108">功能</span><span class="sxs-lookup"><span data-stu-id="d43c6-108">Capabilities</span></span>

<span data-ttu-id="d43c6-109">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="d43c6-109">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="d43c6-110">簡短描述</span><span class="sxs-lookup"><span data-stu-id="d43c6-110">Short description</span></span>

<span data-ttu-id="d43c6-111">提供對 PowerShell 變數和其值的存取。</span><span class="sxs-lookup"><span data-stu-id="d43c6-111">Provides access to the PowerShell variables and to their values.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="d43c6-112">詳細描述</span><span class="sxs-lookup"><span data-stu-id="d43c6-112">Detailed description</span></span>

<span data-ttu-id="d43c6-113">PowerShell **變數** 提供者可讓您取得、新增、變更、清除及刪除目前主控台中的 PowerShell 變數。</span><span class="sxs-lookup"><span data-stu-id="d43c6-113">The PowerShell **Variable** provider lets you get, add, change, clear, and delete PowerShell variables in the current console.</span></span>

<span data-ttu-id="d43c6-114">PowerShell **變數** 提供者支援 powershell 所建立的變數，包括自動變數、喜好設定變數，以及您所建立的變數。</span><span class="sxs-lookup"><span data-stu-id="d43c6-114">The PowerShell **Variable** provider supports the variables that PowerShell creates, including the automatic variables, the preference variables, and the variables that you create.</span></span>

<span data-ttu-id="d43c6-115">**變數** 磁片磁碟機是只包含變數物件的一般命名空間。</span><span class="sxs-lookup"><span data-stu-id="d43c6-115">The **Variable** drive is a flat namespace that contains only the variable objects.</span></span> <span data-ttu-id="d43c6-116">變數沒有任何子項目。</span><span class="sxs-lookup"><span data-stu-id="d43c6-116">The variables have no child items.</span></span>

<span data-ttu-id="d43c6-117">**變數** 提供者支援下列 Cmdlet，這些 Cmdlet 將在本文中討論。</span><span class="sxs-lookup"><span data-stu-id="d43c6-117">The **Variable** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="d43c6-118">Get-Location</span><span class="sxs-lookup"><span data-stu-id="d43c6-118">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="d43c6-119">Set-Location</span><span class="sxs-lookup"><span data-stu-id="d43c6-119">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="d43c6-120">Get-Item</span><span class="sxs-lookup"><span data-stu-id="d43c6-120">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="d43c6-121">New-Item</span><span class="sxs-lookup"><span data-stu-id="d43c6-121">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="d43c6-122">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="d43c6-122">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="d43c6-123">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="d43c6-123">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)

<span data-ttu-id="d43c6-124">PowerShell 也包含一組特別設計來查看和變更變數的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d43c6-124">PowerShell also includes a set of cmdlets designed especially to view and to change variables.</span></span> <span data-ttu-id="d43c6-125">當您使用 **變數** Cmdlet 時，不需要 `Variable:` 在名稱中指定磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="d43c6-125">When you use **Variable** cmdlets, you do not need to specify the `Variable:` drive in the name.</span></span> <span data-ttu-id="d43c6-126">本文未涵蓋使用 **變數** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d43c6-126">This article does not cover working with **Variable** cmdlets.</span></span>

- [<span data-ttu-id="d43c6-127">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="d43c6-127">Get-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Get-Variable)
- [<span data-ttu-id="d43c6-128">New-Variable</span><span class="sxs-lookup"><span data-stu-id="d43c6-128">New-Variable</span></span>](xref:Microsoft.PowerShell.Utility.New-Variable)
- [<span data-ttu-id="d43c6-129">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="d43c6-129">Set-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Set-Variable)
- [<span data-ttu-id="d43c6-130">Remove-Variable</span><span class="sxs-lookup"><span data-stu-id="d43c6-130">Remove-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Remove-Variable)
- [<span data-ttu-id="d43c6-131">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="d43c6-131">Clear-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Clear-Variable)

> [!NOTE]
> <span data-ttu-id="d43c6-132">您也可以使用 PowerShell 運算式剖析器來建立、查看和變更變數的值，而不需要使用 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d43c6-132">You can also use the PowerShell expression parser to create, view, and change the values of variables without using the cmdlets.</span></span> <span data-ttu-id="d43c6-133">直接使用變數時，請使用貨幣符號 (`$`) 將名稱識別為變數，並使用指派運算子 (`=`) 建立和變更其值。</span><span class="sxs-lookup"><span data-stu-id="d43c6-133">When working with variables directly, use a dollar sign (`$`) to identify the name as a variable and the assignment operator (`=`)to establish and change its value.</span></span> <span data-ttu-id="d43c6-134">例如， `$p = Get-Process` `p` 會建立變數，並將命令的結果儲存 `Get-Process` 在其中。</span><span class="sxs-lookup"><span data-stu-id="d43c6-134">For example, `$p = Get-Process` creates the `p` variable and stores the results of a `Get-Process` command in it.</span></span>

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="d43c6-135">此提供者公開的類型</span><span class="sxs-lookup"><span data-stu-id="d43c6-135">Types exposed by this provider</span></span>

<span data-ttu-id="d43c6-136">變數可以是數種不同類型的其中一種。</span><span class="sxs-lookup"><span data-stu-id="d43c6-136">Variables can be one of several different types.</span></span> <span data-ttu-id="d43c6-137">大部分的變數都是類別的實例 `PSVariable` 。</span><span class="sxs-lookup"><span data-stu-id="d43c6-137">Most variables will be instances of the `PSVariable` class.</span></span> <span data-ttu-id="d43c6-138">以下列出其他變數和其類型。</span><span class="sxs-lookup"><span data-stu-id="d43c6-138">Other variables and their types are listed below.</span></span>

- <span data-ttu-id="d43c6-139">`?`變數是類別的實例 `QuestionMarkVariable` 。</span><span class="sxs-lookup"><span data-stu-id="d43c6-139">The `?` variable is an instance of the `QuestionMarkVariable` class.</span></span>
- <span data-ttu-id="d43c6-140">`null`變數是類別的實例 `NullVariable` 。</span><span class="sxs-lookup"><span data-stu-id="d43c6-140">The `null` variable is an instance of the `NullVariable` class.</span></span>
- <span data-ttu-id="d43c6-141">最大計數變數是類別的實例 `SessionStateCapacityVariable` 。</span><span class="sxs-lookup"><span data-stu-id="d43c6-141">The maximum count variables are instances of the `SessionStateCapacityVariable` class.</span></span>
- <span data-ttu-id="d43c6-142">`LocalVariable` 實例包含目前執行的相關資訊，例如：</span><span class="sxs-lookup"><span data-stu-id="d43c6-142">`LocalVariable` instances contain information about current execution, such as:</span></span>
  - `MyInvocation`
  - `PSCommandPath`
  - `PSScriptRoot`
  - `PSBoundParameters`
  - `args`
  - `input`

## <a name="navigating-the-variable-drives"></a><span data-ttu-id="d43c6-143">流覽變數磁片磁碟機</span><span class="sxs-lookup"><span data-stu-id="d43c6-143">Navigating the Variable drives</span></span>

<span data-ttu-id="d43c6-144">**變數** 提供者會在磁片磁碟機中公開它的資料存放區 `Variable:` 。</span><span class="sxs-lookup"><span data-stu-id="d43c6-144">The **Variable** provider exposes its data store in the `Variable:` drive.</span></span> <span data-ttu-id="d43c6-145">若要使用變數，您可以將位置變更為 `Variable:` 磁片磁碟機 (`Set-Location Variable:`) ，也可以從任何其他的 PowerShell 磁片磁碟機工作。</span><span class="sxs-lookup"><span data-stu-id="d43c6-145">To work with variables, you can change your location to the `Variable:` drive (`Set-Location Variable:`), or you can work from any other PowerShell drive.</span></span> <span data-ttu-id="d43c6-146">若要從另一個位置參考變數，請在路徑中使用磁片磁碟機名稱 (`Variable:`) 。</span><span class="sxs-lookup"><span data-stu-id="d43c6-146">To reference a variable from another location, use the drive name (`Variable:`) in the path.</span></span>

```powershell
Set-Location Variable:
```

<span data-ttu-id="d43c6-147">若要返回檔案系統磁碟機，請輸入磁碟機名稱。</span><span class="sxs-lookup"><span data-stu-id="d43c6-147">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="d43c6-148">例如，輸入：</span><span class="sxs-lookup"><span data-stu-id="d43c6-148">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="d43c6-149">您也可以從任何其他 PowerShell 磁片磁碟機使用 **變數** 提供者。</span><span class="sxs-lookup"><span data-stu-id="d43c6-149">You can also work with the **Variable** provider from any other PowerShell drive.</span></span> <span data-ttu-id="d43c6-150">若要從另一個位置參考變數，請在路徑中使用磁片磁碟機名稱 `Variable:` 。</span><span class="sxs-lookup"><span data-stu-id="d43c6-150">To reference an variable from another location, use the drive name `Variable:` in the path.</span></span>

> [!NOTE]
> <span data-ttu-id="d43c6-151">PowerShell 會使用別名，讓您有熟悉的方式來處理提供者路徑。</span><span class="sxs-lookup"><span data-stu-id="d43c6-151">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="d43c6-152">和等命令 `dir` `ls` 現在是 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)的別名， `cd` 它是 [設定位置](xref:Microsoft.PowerShell.Management.Set-Location)的別名。</span><span class="sxs-lookup"><span data-stu-id="d43c6-152">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="d43c6-153">和 `pwd` 是 [取得位置](xref:Microsoft.PowerShell.Management.Get-Location)的別名。</span><span class="sxs-lookup"><span data-stu-id="d43c6-153">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="displaying-the-value-of-variables"></a><span data-ttu-id="d43c6-154">顯示變數的值</span><span class="sxs-lookup"><span data-stu-id="d43c6-154">Displaying the value of variables</span></span>

### <a name="get-all-variables-in-the-current-session"></a><span data-ttu-id="d43c6-155">取得目前會話中的所有變數</span><span class="sxs-lookup"><span data-stu-id="d43c6-155">Get all variables in the current session</span></span>

<span data-ttu-id="d43c6-156">此命令會取得目前工作階段中所有變數及其值的清單。</span><span class="sxs-lookup"><span data-stu-id="d43c6-156">This command gets the list of all the variables and their values in the current session.</span></span> <span data-ttu-id="d43c6-157">您可以從任何 PowerShell 磁片磁碟機使用此命令。</span><span class="sxs-lookup"><span data-stu-id="d43c6-157">You can use this command from any PowerShell drive.</span></span>

```powershell
Get-ChildItem -Path Variable:
```

### <a name="get-a-variable-using-its-provider-path"></a><span data-ttu-id="d43c6-158">使用其提供者路徑取得變數</span><span class="sxs-lookup"><span data-stu-id="d43c6-158">Get a variable using its provider path</span></span>

<span data-ttu-id="d43c6-159">此命令會使用前面加上貨幣符號 () 的提供者路徑來抓取變數值 `$` 。</span><span class="sxs-lookup"><span data-stu-id="d43c6-159">This command retrieves a variables value using its provider path prefixed by the dollar sign (`$`).</span></span> <span data-ttu-id="d43c6-160">這與在變數名稱前面加上貨幣符號 () 的效果相同 `$` 。</span><span class="sxs-lookup"><span data-stu-id="d43c6-160">This has the same effect as prefixing the variables name with the dollar sign (`$`).</span></span>

```powershell
$variable:home
```

### <a name="get-variables-using-wildcards"></a><span data-ttu-id="d43c6-161">使用萬用字元取得變數</span><span class="sxs-lookup"><span data-stu-id="d43c6-161">Get variables using wildcards</span></span>

<span data-ttu-id="d43c6-162">此命令會取得名稱以 "max" 開頭的變數。</span><span class="sxs-lookup"><span data-stu-id="d43c6-162">This command gets the variables with names that begin with "max".</span></span> <span data-ttu-id="d43c6-163">您可以從任何 PowerShell 磁片磁碟機使用此命令。</span><span class="sxs-lookup"><span data-stu-id="d43c6-163">You can use this command from any PowerShell drive.</span></span>

```powershell
Get-ChildItem -Path Variable:max*
```

### <a name="get-the-value-of-the--variable"></a><span data-ttu-id="d43c6-164">取得的值？</span><span class="sxs-lookup"><span data-stu-id="d43c6-164">Get the value of the ?</span></span> <span data-ttu-id="d43c6-165">變動</span><span class="sxs-lookup"><span data-stu-id="d43c6-165">variable</span></span>

<span data-ttu-id="d43c6-166">此命令會使用 `-LiteralPath` [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem) 的參數， `?` 從磁片磁碟機中取得變數的值 `Variable:` 。</span><span class="sxs-lookup"><span data-stu-id="d43c6-166">This command uses the `-LiteralPath` parameter of [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) to get the value of the `?` variable from within the `Variable:` drive.</span></span> <span data-ttu-id="d43c6-167">在 `?` 路徑中是萬用字元，但不 `Get-ChildItem` 會嘗試解析參數值中的任何萬用字元 `-LiteralPath` 。</span><span class="sxs-lookup"><span data-stu-id="d43c6-167">The `?` is a wildcard in paths, but `Get-ChildItem` does not attempt to resolve any wildcards in the values of the `-LiteralPath` parameter.</span></span>

```powershell
Get-ChildItem -Literalpath ?
```

### <a name="get-readonly-and-constant-variables"></a><span data-ttu-id="d43c6-168">取得 ReadOnly 和常數變數</span><span class="sxs-lookup"><span data-stu-id="d43c6-168">Get ReadOnly and Constant variables</span></span>

<span data-ttu-id="d43c6-169">此命令會取得 `ReadOnly` `Constant` 其 **Options** 屬性的值為或的變數。</span><span class="sxs-lookup"><span data-stu-id="d43c6-169">This command gets the variables that have the values of `ReadOnly` or `Constant` for their **Options** property.</span></span>

```powershell
Get-ChildItem -Path Variable: | Where-Object {
   $_.options -Match "Constant" `
   -or $_.options -Match "ReadOnly"
 } | Format-List -Property name, value, options
```

## <a name="creating-variables"></a><span data-ttu-id="d43c6-170">建立變數</span><span class="sxs-lookup"><span data-stu-id="d43c6-170">Creating variables</span></span>

### <a name="create-a-new-variable"></a><span data-ttu-id="d43c6-171">建立新的變數</span><span class="sxs-lookup"><span data-stu-id="d43c6-171">Create a new variable</span></span>

<span data-ttu-id="d43c6-172">此命令會建立 `services` 變數，並將命令的結果儲存 `Get-Service` 在其中。</span><span class="sxs-lookup"><span data-stu-id="d43c6-172">This command creates the `services` variable and stores the results of a `Get-Service` command in it.</span></span> <span data-ttu-id="d43c6-173">因為目前的位置是在 `Variable:` 磁片磁碟機中，所以參數的值 `-Path` 為點 (`.`) ，代表目前的位置。</span><span class="sxs-lookup"><span data-stu-id="d43c6-173">Because the current location is in the `Variable:` drive, the value of the `-Path` parameter is a dot (`.`), which represents the current location.</span></span>

<span data-ttu-id="d43c6-174">命令周圍的括弧 `Get-Service` 可確保在建立變數之前執行此命令。</span><span class="sxs-lookup"><span data-stu-id="d43c6-174">The parentheses around the `Get-Service` command ensure that the command is executed before the variable is created.</span></span> <span data-ttu-id="d43c6-175">如果沒有括號，新變數的值就是 "Get-Service" 字串。</span><span class="sxs-lookup"><span data-stu-id="d43c6-175">Without the parentheses, the value of the new variable is a "Get-Service" string.</span></span>

```powershell
New-Item -Path . -Name services -Value (Get-Service)
```

### <a name="create-a-variable-using-an-absolute-path"></a><span data-ttu-id="d43c6-176">使用絕對路徑建立變數</span><span class="sxs-lookup"><span data-stu-id="d43c6-176">Create a variable using an absolute path</span></span>

<span data-ttu-id="d43c6-177">此命令會建立 `services` 變數，並將命令的結果儲存 `Get-Service` 在其中。</span><span class="sxs-lookup"><span data-stu-id="d43c6-177">This command creates a `services` variable and stores the result of a `Get-Service` command in it.</span></span>

```powershell
New-Item -Path Variable:services -Value Get-Service
```

 <span data-ttu-id="d43c6-178">若要建立不含值的變數，請省略指派運算子。</span><span class="sxs-lookup"><span data-stu-id="d43c6-178">To create a variable without a value, omit the assignment operator.</span></span>

## <a name="changing-variables"></a><span data-ttu-id="d43c6-179">變更變數</span><span class="sxs-lookup"><span data-stu-id="d43c6-179">Changing variables</span></span>

### <a name="rename-a-variable"></a><span data-ttu-id="d43c6-180">重新命名變數</span><span class="sxs-lookup"><span data-stu-id="d43c6-180">Rename a variable</span></span>

<span data-ttu-id="d43c6-181">此命令會使用 `Rename-Item` Cmdlet 將變數名稱變更 `a` 為 `processes` 。</span><span class="sxs-lookup"><span data-stu-id="d43c6-181">This command uses the `Rename-Item` cmdlet to change the name of the `a` variable to `processes`.</span></span>

```powershell
Rename-Item -Path Variable:a -NewName processes
```

### <a name="change-the-value-of-a-variable"></a><span data-ttu-id="d43c6-182">變更變數的值</span><span class="sxs-lookup"><span data-stu-id="d43c6-182">Change the value of a variable</span></span>

<span data-ttu-id="d43c6-183">此命令會使用 `Set-Item` Cmdlet 將變數的值變更 `ErrorActionPreference` 為 "Stop"。</span><span class="sxs-lookup"><span data-stu-id="d43c6-183">This command uses the `Set-Item` cmdlet to change the value of the `ErrorActionPreference` variable to "Stop".</span></span>

```powershell
Set-Item -Path Variable:ErrorActionPreference -Value Stop
```

## <a name="copy-a-variable"></a><span data-ttu-id="d43c6-184">複製變數</span><span class="sxs-lookup"><span data-stu-id="d43c6-184">Copy a variable</span></span>

<span data-ttu-id="d43c6-185">此命令會使用 `Copy-Item` Cmdlet 將變數複製 `processes` 到 `old_processes` 。</span><span class="sxs-lookup"><span data-stu-id="d43c6-185">This command uses the `Copy-Item` cmdlet to copy the `processes` variable to `old_processes`.</span></span> <span data-ttu-id="d43c6-186">這會建立名為的新變數 `old_processes` ，其值與 `processes` 變數相同。</span><span class="sxs-lookup"><span data-stu-id="d43c6-186">This creates a new variable named `old_processes` that has the same value as the `processes` variable.</span></span>

```powershell
Copy-Item -Path Variable:processes -Destination Variable:old_processes
```

## <a name="delete-a-variable"></a><span data-ttu-id="d43c6-187">刪除變數</span><span class="sxs-lookup"><span data-stu-id="d43c6-187">Delete a variable</span></span>

<span data-ttu-id="d43c6-188">此命令會 `serv` 從目前的會話刪除變數。</span><span class="sxs-lookup"><span data-stu-id="d43c6-188">This command deletes the `serv` variable from the current session.</span></span> <span data-ttu-id="d43c6-189">您可以在任何 PowerShell 磁片磁碟機中使用此命令。</span><span class="sxs-lookup"><span data-stu-id="d43c6-189">You can use this command in any PowerShell drive.</span></span>

```powershell
Remove-Variable -Path Variable:serv
```

### <a name="delete-variables-using-the--force-parameter"></a><span data-ttu-id="d43c6-190">使用-Force 參數刪除變數</span><span class="sxs-lookup"><span data-stu-id="d43c6-190">Delete variables using the -Force parameter</span></span>

<span data-ttu-id="d43c6-191">此命令會從目前的會話刪除所有變數，但 **Options** 屬性具有值的變數除外 `Constant` 。</span><span class="sxs-lookup"><span data-stu-id="d43c6-191">This command deletes all variables from the current session except for the variables whose **Options** property has a value of `Constant`.</span></span> <span data-ttu-id="d43c6-192">如果沒有 `-Force` 參數，命令就不會刪除 **Options** 屬性具有值的變數 `ReadOnly` 。</span><span class="sxs-lookup"><span data-stu-id="d43c6-192">Without the `-Force` parameter, the command does not delete variables whose **Options** property has a value of `ReadOnly`.</span></span>

```powershell
Remove-Item Variable:* -Force
```

## <a name="setting-the-value-of-a-variable-to-null"></a><span data-ttu-id="d43c6-193">將變數的值設定為 Null</span><span class="sxs-lookup"><span data-stu-id="d43c6-193">Setting the value of a variable to NULL</span></span>

<span data-ttu-id="d43c6-194">此命令會使用 `Clear-Item` Cmdlet 將變數的值變更 `processes` 為 Null。</span><span class="sxs-lookup"><span data-stu-id="d43c6-194">This command uses the `Clear-Item` cmdlet to change the value of the `processes` variable to NULL.</span></span>

```powershell
Clear-Item -Path Variable:processes
```

## <a name="using-the-pipeline"></a><span data-ttu-id="d43c6-195">使用管線</span><span class="sxs-lookup"><span data-stu-id="d43c6-195">Using the pipeline</span></span>

<span data-ttu-id="d43c6-196">提供者 Cmdlet 接受管線輸入。</span><span class="sxs-lookup"><span data-stu-id="d43c6-196">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="d43c6-197">您可以使用管線將提供者資料從一個 Cmdlet 傳送到另一個提供者 Cmdlet，以簡化工作。</span><span class="sxs-lookup"><span data-stu-id="d43c6-197">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="d43c6-198">若要深入瞭解如何搭配使用管線與提供者 Cmdlet，請參閱本文中提供的 Cmdlet 參考。</span><span class="sxs-lookup"><span data-stu-id="d43c6-198">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="d43c6-199">取得說明</span><span class="sxs-lookup"><span data-stu-id="d43c6-199">Getting help</span></span>

<span data-ttu-id="d43c6-200">從 Windows PowerShell 3.0 開始，您可以取得提供者 Cmdlet 的自訂說明主題，這些主題說明這些 Cmdlet 在檔案系統磁碟機中的行為方式。</span><span class="sxs-lookup"><span data-stu-id="d43c6-200">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="d43c6-201">若要取得針對檔案系統磁片磁碟機自訂的說明主題，請在檔案系統磁片磁碟機中執行 [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 命令，或使用 `-Path` [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 的參數來指定檔案系統磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="d43c6-201">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path variable:
```

## <a name="see-also"></a><span data-ttu-id="d43c6-202">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d43c6-202">See also</span></span>

[<span data-ttu-id="d43c6-203">about_Variables</span><span class="sxs-lookup"><span data-stu-id="d43c6-203">about_Variables</span></span>](../About/about_Variables.md)

[<span data-ttu-id="d43c6-204">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="d43c6-204">about_Automatic_Variables</span></span>](../About/about_Automatic_Variables.md)

[<span data-ttu-id="d43c6-205">about_Providers</span><span class="sxs-lookup"><span data-stu-id="d43c6-205">about_Providers</span></span>](../About/about_Providers.md)
