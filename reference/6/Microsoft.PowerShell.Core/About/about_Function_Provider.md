---
description: 函式
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_function_provider?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 函式提供者
ms.openlocfilehash: 0323433d5ab9114dd1bb21afc47b7fa7db3d6f8f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207095"
---
# <a name="function-provider"></a><span data-ttu-id="7a6b9-104">函數提供者</span><span class="sxs-lookup"><span data-stu-id="7a6b9-104">Function provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="7a6b9-105">提供者名稱</span><span class="sxs-lookup"><span data-stu-id="7a6b9-105">Provider name</span></span>
<span data-ttu-id="7a6b9-106">函式</span><span class="sxs-lookup"><span data-stu-id="7a6b9-106">Function</span></span>

## <a name="drives"></a><span data-ttu-id="7a6b9-107">磁碟機</span><span class="sxs-lookup"><span data-stu-id="7a6b9-107">Drives</span></span>

`Function:`

## <a name="capabilities"></a><span data-ttu-id="7a6b9-108">功能</span><span class="sxs-lookup"><span data-stu-id="7a6b9-108">Capabilities</span></span>

<span data-ttu-id="7a6b9-109">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="7a6b9-109">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="7a6b9-110">簡短描述</span><span class="sxs-lookup"><span data-stu-id="7a6b9-110">Short description</span></span>

<span data-ttu-id="7a6b9-111">提供 PowerShell 中定義之函式的存取權。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-111">Provides access to the functions defined in PowerShell.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="7a6b9-112">詳細描述</span><span class="sxs-lookup"><span data-stu-id="7a6b9-112">Detailed description</span></span>

<span data-ttu-id="7a6b9-113">PowerShell 函 **式提供者** 可讓您在 powershell 中取得、新增、變更、清除和刪除函式和篩選器。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-113">The PowerShell **Function** provider lets you get, add, change, clear, and delete the functions and filters in PowerShell.</span></span>

<span data-ttu-id="7a6b9-114">函式是可執行動作的具名程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-114">A function is a named block of code that performs an action.</span></span> <span data-ttu-id="7a6b9-115">當您輸入函式名稱時，函式中的程式碼就會執行。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-115">When you type the function name, the code in the function runs.</span></span> <span data-ttu-id="7a6b9-116">篩選條件是可建立執行動作條件的具名程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-116">A filter is a named block of code that establishes conditions for an action.</span></span> <span data-ttu-id="7a6b9-117">您可以輸入篩選器的名稱來取代條件，例如在 `Where-Object` 命令中。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-117">You can type the name of the filter in place of the condition, such as in a `Where-Object` command.</span></span>

<span data-ttu-id="7a6b9-118">函 **式磁片磁碟機** 是只包含函式和篩選物件的一般命名空間。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-118">The **Function** drive is a flat namespace that contains only the function and filter objects.</span></span> <span data-ttu-id="7a6b9-119">函式和篩選條件都沒有子項目。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-119">Neither functions nor filters have child items.</span></span>

<span data-ttu-id="7a6b9-120">函 **式提供者** 支援下列 Cmdlet，這些 Cmdlet 將在本文中討論。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-120">The **Function** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="7a6b9-121">Get-Location</span><span class="sxs-lookup"><span data-stu-id="7a6b9-121">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="7a6b9-122">Set-Location</span><span class="sxs-lookup"><span data-stu-id="7a6b9-122">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="7a6b9-123">Get-Item</span><span class="sxs-lookup"><span data-stu-id="7a6b9-123">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="7a6b9-124">New-Item</span><span class="sxs-lookup"><span data-stu-id="7a6b9-124">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="7a6b9-125">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="7a6b9-125">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="7a6b9-126">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="7a6b9-126">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="7a6b9-127">此提供者公開的類型</span><span class="sxs-lookup"><span data-stu-id="7a6b9-127">Types exposed by this provider</span></span>

<span data-ttu-id="7a6b9-128">每個函數都是 [FunctionInfo](/dotnet/api/system.management.automation.functioninfo) 類別的實例。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-128">Each function is an instance of the [System.Management.Automation.FunctionInfo](/dotnet/api/system.management.automation.functioninfo) class.</span></span> <span data-ttu-id="7a6b9-129">每個篩選器都是 [都是 system.management.automation.filterinfo](/dotnet/api/system.management.automation.filterinfo) 類別的實例。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-129">Each filter is an instance of the [System.Management.Automation.FilterInfo](/dotnet/api/system.management.automation.filterinfo) class.</span></span>

## <a name="navigating-the-function-drive"></a><span data-ttu-id="7a6b9-130">導覽函式磁片磁碟機</span><span class="sxs-lookup"><span data-stu-id="7a6b9-130">Navigating the Function drive</span></span>

<span data-ttu-id="7a6b9-131">函 **式提供者會在** 磁片磁碟機中公開它的資料存放區 `Function:` 。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-131">The **Function** provider exposes its data store in the `Function:` drive.</span></span> <span data-ttu-id="7a6b9-132">若要使用函式，您可以將位置變更為 `Function:` 磁片磁碟機 (`Set-Location Function:`) 。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-132">To work with functions, you can change your location to the `Function:` drive (`Set-Location Function:`).</span></span> <span data-ttu-id="7a6b9-133">或者，您可以從另一個 PowerShell 磁片磁碟機工作。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-133">Or, you can work from another PowerShell drive.</span></span> <span data-ttu-id="7a6b9-134">若要從另一個位置參考函式，請使用路徑中 () 的磁片磁碟機名稱 `Function:` 。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-134">To reference a function from another location, use the drive name (`Function:`) in the path.</span></span>

```powershell
Set-Location Function:
```

<span data-ttu-id="7a6b9-135">若要返回檔案系統磁碟機，請輸入磁碟機名稱。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-135">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="7a6b9-136">例如，輸入：</span><span class="sxs-lookup"><span data-stu-id="7a6b9-136">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="7a6b9-137">您也可以從任何其他 PowerShell 磁片磁碟機使用 **函數** 提供者。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-137">You can also work with the **Function** provider from any other PowerShell drive.</span></span> <span data-ttu-id="7a6b9-138">若要從另一個位置參考函式，請使用路徑中的磁片磁碟機名稱 `Function:` 。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-138">To reference an function from another location, use the drive name `Function:` in the path.</span></span>

> [!NOTE]
> <span data-ttu-id="7a6b9-139">PowerShell 會使用別名，讓您有熟悉的方式來處理提供者路徑。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-139">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="7a6b9-140">和等命令 `dir` `ls` 現在是 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)的別名， `cd` 它是 [設定位置](xref:Microsoft.PowerShell.Management.Set-Location)的別名。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-140">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="7a6b9-141">和 `pwd` 是 [取得位置](xref:Microsoft.PowerShell.Management.Get-Location)的別名。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-141">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="getting-functions"></a><span data-ttu-id="7a6b9-142">取得函式</span><span class="sxs-lookup"><span data-stu-id="7a6b9-142">Getting functions</span></span>

<span data-ttu-id="7a6b9-143">此命令會取得目前工作階段中的所有函式清單。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-143">This command gets the list of all the functions in the current session.</span></span> <span data-ttu-id="7a6b9-144">您可以從任何 PowerShell 磁片磁碟機使用此命令。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-144">You can use this command from any PowerShell drive.</span></span>

```powershell
Get-ChildItem -Path Function:
```

<span data-ttu-id="7a6b9-145">函式提供者沒有任何容器，因此在搭配使用時，上述命令具有相同的效果 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-145">The Function provider has no containers, so the above command has the same effect when used with `Get-ChildItem`.</span></span>

```powershell
Get-ChildItem -Path Function:
```

<span data-ttu-id="7a6b9-146">您可以藉由存取 **定義** 屬性來取出函數的定義，如下所示。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-146">You can retrieve a function's definition by accessing the **Definition** property, as shown below.</span></span>

```powershell
(Get-Item -Path function:more).Definition
```

<span data-ttu-id="7a6b9-147">您也可以使用前面加上貨幣符號 () 的提供者路徑來取得函式的定義 `$` 。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-147">You can also retrieve a function's definition using its provider path prefixed by the dollar sign (`$`).</span></span>

```powershell
$function:more
```

### <a name="getting-selected-functions"></a><span data-ttu-id="7a6b9-148">取得選取的函式</span><span class="sxs-lookup"><span data-stu-id="7a6b9-148">Getting selected functions</span></span>

<span data-ttu-id="7a6b9-149">此命令會 `man` 從 `Function:` 磁片磁碟機取得函數。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-149">This command gets the `man` function from the `Function:` drive.</span></span> <span data-ttu-id="7a6b9-150">它會使用 `Get-Item` Cmdlet 來取得函數。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-150">It uses the `Get-Item` cmdlet to get the function.</span></span> <span data-ttu-id="7a6b9-151">管線運算子 (`|`) 將結果傳送至 `Format-Table` 。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-151">The pipeline operator (`|`) sends the result to `Format-Table`.</span></span> <span data-ttu-id="7a6b9-152">`-Wrap`參數會將不符合該行的文字導向到下一行。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-152">The `-Wrap` parameter directs text that does not fit on the line onto the next line.</span></span> <span data-ttu-id="7a6b9-153">`-Autosize`參數會調整資料表資料行的大小來容納文字。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-153">The `-Autosize` parameter resizes the table columns to accommodate the text.</span></span>

```powershell
Get-Item -Path man | Format-Table -Wrap -Autosize
```

### <a name="working-with-function-provider-paths"></a><span data-ttu-id="7a6b9-154">使用函數提供者路徑</span><span class="sxs-lookup"><span data-stu-id="7a6b9-154">Working with Function provider paths</span></span>

<span data-ttu-id="7a6b9-155">這些命令都會取得名為的函式 `c:` 。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-155">These commands both get the function named `c:`.</span></span> <span data-ttu-id="7a6b9-156">第一個命令適用於任何磁碟機。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-156">The first command can be used in any drive.</span></span> <span data-ttu-id="7a6b9-157">第二個命令用於 `Function:` 磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-157">The second command is used in the `Function:` drive.</span></span> <span data-ttu-id="7a6b9-158">由於名稱結尾是冒號 (此為磁碟機的語法)，因此，您必須使用磁碟機名稱來限定路徑。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-158">Because the name ends in a colon, which is the syntax for a drive, you must qualify the path with the drive name.</span></span> <span data-ttu-id="7a6b9-159">在 `Function:` 磁片磁碟機中，您可以使用任一種格式。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-159">Within the `Function:` drive, you can use either format.</span></span> <span data-ttu-id="7a6b9-160">在第二個命令中， (`.`) 的點代表目前的位置。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-160">In the second command, the dot (`.`) represents the current location.</span></span>

```
PS C:\> Get-Item -Path Function:c:
PS Function:\> Get-Item -Path .\c:
```

## <a name="creating-a-function"></a><span data-ttu-id="7a6b9-161">建立函式</span><span class="sxs-lookup"><span data-stu-id="7a6b9-161">Creating a function</span></span>

<span data-ttu-id="7a6b9-162">此命令會使用 `New-Item` Cmdlet 來建立名為的函式 `Win32:` 。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-162">This command uses the `New-Item` cmdlet to create a function called `Win32:`.</span></span>
<span data-ttu-id="7a6b9-163">使用括號括起來的運算式是函式名稱所代表的指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-163">The expression in braces is the script block that is represented by the function name.</span></span>

```powershell
New-Item -Path Function:Win32: -Value {Set-Location C:\Windows\System32}
```

<span data-ttu-id="7a6b9-164">您也可以在 PowerShell 命令列中輸入函式來建立函式。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-164">You can also create a function by typing it at the PowerShell command line.</span></span> <span data-ttu-id="7a6b9-165">例如，tpe `Function:Win32: {Set-Location C:\Windows\System32}` 。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-165">For example, tpe `Function:Win32: {Set-Location C:\Windows\System32}`.</span></span> <span data-ttu-id="7a6b9-166">如果您是在 `Function:` 磁片磁碟機中，您可以省略磁片磁碟機名稱。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-166">If you are in the `Function:` drive, you can omit the drive name.</span></span>

## <a name="deleting-a-function"></a><span data-ttu-id="7a6b9-167">刪除函式</span><span class="sxs-lookup"><span data-stu-id="7a6b9-167">Deleting a function</span></span>

<span data-ttu-id="7a6b9-168">此命令會 `more:` 從目前的會話刪除函數。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-168">This command deletes the `more:` function from the current session.</span></span>

```powershell
Remove-Item Function:more:
```

## <a name="changing-a-function"></a><span data-ttu-id="7a6b9-169">變更函數</span><span class="sxs-lookup"><span data-stu-id="7a6b9-169">Changing a function</span></span>

<span data-ttu-id="7a6b9-170">此命令會使用 `Set-Item` Cmdlet 來變更函式， `prompt` 讓它顯示路徑之前的時間。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-170">This command uses the `Set-Item` cmdlet to change the `prompt` function so that it displays the time before the path.</span></span>

```powershell
Set-Item -Path Function:prompt -Value {
  'PS '+ (Get-Date -Format t) + " " + (Get-Location) + '> '
  }
```

### <a name="rename-a-function"></a><span data-ttu-id="7a6b9-171">重新命名函數</span><span class="sxs-lookup"><span data-stu-id="7a6b9-171">Rename a function</span></span>

<span data-ttu-id="7a6b9-172">此命令會使用 `Rename-Item` Cmdlet 將函數的名稱變更 `help` 為 `gh` 。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-172">This command uses the `Rename-Item` cmdlet to change the name of the `help` function to `gh`.</span></span>

```powershell
Rename-Item -Path Function:help -NewName gh
```

## <a name="copying-a-function"></a><span data-ttu-id="7a6b9-173">複製函式</span><span class="sxs-lookup"><span data-stu-id="7a6b9-173">Copying a function</span></span>

<span data-ttu-id="7a6b9-174">此命令會將 `prompt` 函數複製到 `oldPrompt` ，以有效地為與提示函式相關聯的腳本區塊建立新名稱。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-174">This command copies the `prompt` function to `oldPrompt`, effectively creating a new name for the script block that is associated with the prompt function.</span></span>
<span data-ttu-id="7a6b9-175">如果您想要變更它，就可以使用此命令來儲存原始提示函式。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-175">You can use this to save the original prompt function if you plan to change it.</span></span>
<span data-ttu-id="7a6b9-176">新函數的 **Options** 屬性的值為 `None` 。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-176">The **Options** property of the new function has a value of `None`.</span></span> <span data-ttu-id="7a6b9-177">若要變更 **Options** 屬性的值，請使用 `Set-Item` 。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-177">To change the value of the **Options** property, use `Set-Item`.</span></span>

```powershell
Copy-Item -Path Function:prompt -Destination Function:oldPrompt
```

## <a name="dynamic-parameters"></a><span data-ttu-id="7a6b9-178">動態參數</span><span class="sxs-lookup"><span data-stu-id="7a6b9-178">Dynamic parameters</span></span>

<span data-ttu-id="7a6b9-179">動態參數是 PowerShell 提供者新增的 Cmdlet 參數，而且只有在提供者啟用的磁片磁碟機中使用 Cmdlet 時才能使用。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-179">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="options-systemmanagementautomationscopeditemoptions"></a><span data-ttu-id="7a6b9-180">選項 < [ScopedItemOptions] ></span><span class="sxs-lookup"><span data-stu-id="7a6b9-180">Options <[System.Management.Automation.ScopedItemOptions]></span></span>

<span data-ttu-id="7a6b9-181">決定函數的 **Options** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-181">Determines the value of the **Options** property of a function.</span></span>

- <span data-ttu-id="7a6b9-182">`None`：沒有選項。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-182">`None`: No options.</span></span> <span data-ttu-id="7a6b9-183">`None` 是預設值。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-183">`None` is the default.</span></span>
- <span data-ttu-id="7a6b9-184">`Constant`：無法刪除函數，而且無法變更其屬性。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-184">`Constant`: The function cannot be deleted, and its properties cannot be changed.</span></span> <span data-ttu-id="7a6b9-185">`Constant` 只有在您建立函式時才能使用。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-185">`Constant` is available only when you are creating a function.</span></span>
  <span data-ttu-id="7a6b9-186">您無法將現有函式的選項變更為 `Constant` 。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-186">You cannot change the option of an existing function to `Constant`.</span></span>
- <span data-ttu-id="7a6b9-187">`Private`：函式只會在目前的範圍中顯示</span><span class="sxs-lookup"><span data-stu-id="7a6b9-187">`Private`: The function is visible only in the current scope</span></span>
- <span data-ttu-id="7a6b9-188"> (不在子範圍) 。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-188">(not in child scopes).</span></span>
- <span data-ttu-id="7a6b9-189">`ReadOnly`：除非使用參數，否則無法變更函數的屬性 `-Force` 。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-189">`ReadOnly`: The properties of the function cannot be changed except by using the `-Force` parameter.</span></span> <span data-ttu-id="7a6b9-190">您可以使用 `Remove-Item` 刪除函數。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-190">You can use `Remove-Item` to delete the function.</span></span>
- <span data-ttu-id="7a6b9-191">`AllScope`：函式會複製到所建立的任何新範圍。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-191">`AllScope`: The function is copied to any new scopes that are created.</span></span>

### <a name="cmdlets-supported"></a><span data-ttu-id="7a6b9-192">支援的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7a6b9-192">Cmdlets supported</span></span>

- [<span data-ttu-id="7a6b9-193">New-Item</span><span class="sxs-lookup"><span data-stu-id="7a6b9-193">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

- [<span data-ttu-id="7a6b9-194">Set-Item</span><span class="sxs-lookup"><span data-stu-id="7a6b9-194">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)

## <a name="using-the-pipeline"></a><span data-ttu-id="7a6b9-195">使用管線</span><span class="sxs-lookup"><span data-stu-id="7a6b9-195">Using the pipeline</span></span>

<span data-ttu-id="7a6b9-196">提供者 Cmdlet 接受管線輸入。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-196">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="7a6b9-197">您可以使用管線將提供者資料從一個 Cmdlet 傳送到另一個提供者 Cmdlet，以簡化工作。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-197">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="7a6b9-198">若要深入瞭解如何搭配使用管線與提供者 Cmdlet，請參閱本文中提供的 Cmdlet 參考。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-198">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="7a6b9-199">取得說明</span><span class="sxs-lookup"><span data-stu-id="7a6b9-199">Getting help</span></span>

<span data-ttu-id="7a6b9-200">從 Windows PowerShell 3.0 開始，您可以取得提供者 Cmdlet 的自訂說明主題，這些主題說明這些 Cmdlet 在檔案系統磁碟機中的行為方式。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-200">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="7a6b9-201">若要取得針對檔案系統磁片磁碟機自訂的說明主題，請在檔案系統磁片磁碟機中執行 [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 命令，或使用 `-Path` [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 的參數來指定檔案系統磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="7a6b9-201">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path function:
```

## <a name="see-also"></a><span data-ttu-id="7a6b9-202">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a6b9-202">See also</span></span>

[<span data-ttu-id="7a6b9-203">about_Functions</span><span class="sxs-lookup"><span data-stu-id="7a6b9-203">about_Functions</span></span>](../About/about_Functions.md)

[<span data-ttu-id="7a6b9-204">about_Providers</span><span class="sxs-lookup"><span data-stu-id="7a6b9-204">about_Providers</span></span>](../About/about_Providers.md)
