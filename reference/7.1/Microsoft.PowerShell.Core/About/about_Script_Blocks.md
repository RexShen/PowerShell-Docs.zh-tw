---
description: 定義腳本區塊是什麼，並說明如何使用 PowerShell 程式設計語言的腳本區塊。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_script_blocks?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Script_Blocks
ms.openlocfilehash: 28bc5377e1787ddb646480eacc219c5bbb63dc37
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208239"
---
# <a name="about-script-blocks"></a><span data-ttu-id="5bb0c-104">關於腳本區塊</span><span class="sxs-lookup"><span data-stu-id="5bb0c-104">About Script Blocks</span></span>

## <a name="short-description"></a><span data-ttu-id="5bb0c-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="5bb0c-105">Short description</span></span>

<span data-ttu-id="5bb0c-106">定義腳本區塊是什麼，並說明如何使用 PowerShell 程式設計語言的腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="5bb0c-106">Defines what a script block is and explains how to use script blocks in the PowerShell programming language.</span></span>

## <a name="long-description"></a><span data-ttu-id="5bb0c-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="5bb0c-107">Long description</span></span>

<span data-ttu-id="5bb0c-108">在 PowerShell 程式設計語言中，腳本區塊是可當做單一單位使用的語句或運算式集合。</span><span class="sxs-lookup"><span data-stu-id="5bb0c-108">In the PowerShell programming language, a script block is a collection of statements or expressions that can be used as a single unit.</span></span>
<span data-ttu-id="5bb0c-109">指令碼區塊可以接受引數和傳回值。</span><span class="sxs-lookup"><span data-stu-id="5bb0c-109">A script block can accept arguments and return values.</span></span>

<span data-ttu-id="5bb0c-110">在語法上，腳本區塊是以大括弧括住的語句清單，如下列語法所示：</span><span class="sxs-lookup"><span data-stu-id="5bb0c-110">Syntactically, a script block is a statement list in braces, as shown in the following syntax:</span></span>

```
{<statement list>}
```

<span data-ttu-id="5bb0c-111">腳本區塊會傳回腳本區塊中所有命令的輸出，可以是單一物件或陣列。</span><span class="sxs-lookup"><span data-stu-id="5bb0c-111">A script block returns the output of all the commands in the script block, either as a single object or as an array.</span></span>

<span data-ttu-id="5bb0c-112">您也可以使用關鍵字來指定傳回值 `return` 。</span><span class="sxs-lookup"><span data-stu-id="5bb0c-112">You can also specify a return value using the `return` keyword.</span></span> <span data-ttu-id="5bb0c-113">`return`關鍵字不會影響或隱藏從腳本區塊傳回的其他輸出。</span><span class="sxs-lookup"><span data-stu-id="5bb0c-113">The `return` keyword does not affect or suppress other output returned from your script block.</span></span> <span data-ttu-id="5bb0c-114">不過， `return` 關鍵字會結束該行的腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="5bb0c-114">However, the `return` keyword exits the script block at that line.</span></span> <span data-ttu-id="5bb0c-115">如需詳細資訊，請參閱 [about_Return](about_Return.md)。</span><span class="sxs-lookup"><span data-stu-id="5bb0c-115">For more information, see [about_Return](about_Return.md).</span></span>

<span data-ttu-id="5bb0c-116">就像函式一樣，腳本區塊也可以包含參數。</span><span class="sxs-lookup"><span data-stu-id="5bb0c-116">Like functions, a script block can include parameters.</span></span> <span data-ttu-id="5bb0c-117">使用 Param 關鍵字指派具名引數，如下列語法所示：</span><span class="sxs-lookup"><span data-stu-id="5bb0c-117">Use the Param keyword to assign named parameters, as shown in the following syntax:</span></span>

```
{
Param([type]$Parameter1 [,[type]$Parameter2])
<statement list>
}
```

> [!NOTE]
> <span data-ttu-id="5bb0c-118">在腳本區塊中，與函式不同的是，您不能在大括弧之外指定參數。</span><span class="sxs-lookup"><span data-stu-id="5bb0c-118">In a script block, unlike a function, you cannot specify parameters outside the braces.</span></span>

<span data-ttu-id="5bb0c-119">如同函式，腳本區塊可以包含 `DynamicParam` 、 `Begin` 、 `Process` 和 `End` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="5bb0c-119">Like functions, script blocks can include the `DynamicParam`, `Begin`, `Process`, and `End` keywords.</span></span> <span data-ttu-id="5bb0c-120">如需詳細資訊，請參閱 [about_Functions](about_Functions.md) 和 [about_Functions_Advanced](about_Functions_Advanced.md)。</span><span class="sxs-lookup"><span data-stu-id="5bb0c-120">For more information, see [about_Functions](about_Functions.md) and [about_Functions_Advanced](about_Functions_Advanced.md).</span></span>

## <a name="using-script-blocks"></a><span data-ttu-id="5bb0c-121">使用腳本區塊</span><span class="sxs-lookup"><span data-stu-id="5bb0c-121">Using Script Blocks</span></span>

<span data-ttu-id="5bb0c-122">腳本區塊是 Microsoft .NET Framework 類型的實例 `System.Management.Automation.ScriptBlock` 。</span><span class="sxs-lookup"><span data-stu-id="5bb0c-122">A script block is an instance of a Microsoft .NET Framework type `System.Management.Automation.ScriptBlock`.</span></span> <span data-ttu-id="5bb0c-123">命令可以有腳本區塊參數值。</span><span class="sxs-lookup"><span data-stu-id="5bb0c-123">Commands can have script block parameter values.</span></span> <span data-ttu-id="5bb0c-124">例如， `Invoke-Command` Cmdlet 具有 `ScriptBlock` 接受腳本區塊值的參數，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="5bb0c-124">For example, the `Invoke-Command` cmdlet has a `ScriptBlock` parameter that takes a script block value, as shown in this example:</span></span>

```powershell
Invoke-Command -ScriptBlock { Get-Process }
```

```Output
Handles  NPM(K)    PM(K)     WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----     ----- -----   ------     -- -----------
999          28    39100     45020   262    15.88   1844 communicator
721          28    32696     36536   222    20.84   4028 explorer
...
```

<span data-ttu-id="5bb0c-125">`Invoke-Command` 也可以執行具有參數區塊的腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="5bb0c-125">`Invoke-Command` can also execute script blocks that have parameter blocks.</span></span>
<span data-ttu-id="5bb0c-126">參數是透過使用 **ArgumentList** 參數的位置來指派。</span><span class="sxs-lookup"><span data-stu-id="5bb0c-126">Parameters are assigned by position using the **ArgumentList** parameter.</span></span>

```powershell
Invoke-Command -ScriptBlock { param($p1, $p2)
"p1: $p1"
"p2: $p2"
} -ArgumentList "First", "Second"
```

```Output
p1: First
p2: Second
```

<span data-ttu-id="5bb0c-127">上述範例中的腳本區塊會使用 `param` 關鍵字來建立參數 `$p1` 和 `$p2` 。</span><span class="sxs-lookup"><span data-stu-id="5bb0c-127">The script block in the preceding example uses the `param` keyword to create a parameters `$p1` and `$p2`.</span></span> <span data-ttu-id="5bb0c-128">字串 "First" 系結至第一個參數 (`$p1`) ，而 "Second" 系結至 (`$p2`) 。</span><span class="sxs-lookup"><span data-stu-id="5bb0c-128">The string "First" is bound to the first parameter (`$p1`) and "Second" is bound to (`$p2`).</span></span>

<span data-ttu-id="5bb0c-129">如需有關 **ArgumentList** 行為的詳細資訊，請參閱 [about_Splatting](about_Splatting.md#splatting-with-arrays)。</span><span class="sxs-lookup"><span data-stu-id="5bb0c-129">For more information about the behavior of **ArgumentList** , see [about_Splatting](about_Splatting.md#splatting-with-arrays).</span></span>

<span data-ttu-id="5bb0c-130">您可以使用變數來儲存和執行腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="5bb0c-130">You can use variables to store and execute script blocks.</span></span> <span data-ttu-id="5bb0c-131">下列範例會將腳本區塊儲存在變數中，並將其傳遞至 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="5bb0c-131">The example below stores a script block in a variable and passes it to `Invoke-Command`.</span></span>

```powershell
$a = { Get-Service BITS }
Invoke-Command -ScriptBlock $a
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  BITS               Background Intelligent Transfer Ser...
```

<span data-ttu-id="5bb0c-132">呼叫運算子是另一種方式，可執行儲存在變數中的腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="5bb0c-132">The call operator is another way to execute script blocks stored in a variable.</span></span>
<span data-ttu-id="5bb0c-133">如同 `Invoke-Command` ，呼叫運算子會在子範圍中執行腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="5bb0c-133">Like `Invoke-Command`, the call operator executes the script block in a child scope.</span></span> <span data-ttu-id="5bb0c-134">呼叫運算子可讓您更輕鬆地使用參數搭配您的腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="5bb0c-134">The call operator can make it easier for you to use parameters with your script blocks.</span></span>

```powershell
$a ={ param($p1, $p2)
"p1: $p1"
"p2: $p2"
}
&$a -p2 "First" -p1 "Second"
```

```Output
p1: Second
p2: First
```

<span data-ttu-id="5bb0c-135">您可以使用指派，將腳本區塊的輸出儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="5bb0c-135">You can store the output from your script blocks in a variable using assignment.</span></span>

```
PS>  $a = { 1 + 1}
PS>  $b = &$a
PS>  $b
2
```

```
PS>  $a = { 1 + 1}
PS>  $b = Invoke-Command $a
PS>  $b
2
```

<span data-ttu-id="5bb0c-136">如需呼叫運算子的詳細資訊，請參閱 [about_Operators](about_Operators.md)。</span><span class="sxs-lookup"><span data-stu-id="5bb0c-136">For more information about the call operator, see [about_Operators](about_Operators.md).</span></span>

## <a name="using-delay-bind-script-blocks-with-parameters"></a><span data-ttu-id="5bb0c-137">使用具有參數的延遲系結腳本區塊</span><span class="sxs-lookup"><span data-stu-id="5bb0c-137">Using delay-bind script blocks with parameters</span></span>

<span data-ttu-id="5bb0c-138">接受管線輸入 (`by Value`) 或 (`by PropertyName`) 可在參數上使用 **延遲** 系結腳本區塊的型別參數。</span><span class="sxs-lookup"><span data-stu-id="5bb0c-138">A typed parameter that accepts pipeline input (`by Value`) or (`by PropertyName`) enables use of **delay-bind** script blocks on the parameter.</span></span>
<span data-ttu-id="5bb0c-139">在 **延遲** 系結腳本區塊內，您可以使用管線變數參考物件中的管道 `$_` 。</span><span class="sxs-lookup"><span data-stu-id="5bb0c-139">Within the **delay-bind** script block, you can reference the piped in object using the pipeline variable `$_`.</span></span>

```powershell
# Renames config.log to old_config.log
dir config.log | Rename-Item -NewName {"old_" + $_.Name}
```

<span data-ttu-id="5bb0c-140">在更複雜的 Cmdlet 中，延遲系結腳本區塊可讓您重複使用物件中的一個管道來填入其他參數。</span><span class="sxs-lookup"><span data-stu-id="5bb0c-140">In more complex cmdlets, delay-bind script blocks allow the reuse of one piped in object to populate other parameters.</span></span>

<span data-ttu-id="5bb0c-141">**延遲** 將腳本區塊系結為參數的注意事項：</span><span class="sxs-lookup"><span data-stu-id="5bb0c-141">Notes on **delay-bind** script blocks as parameters:</span></span>

- <span data-ttu-id="5bb0c-142">您必須明確指定搭配 **延遲** 系結腳本區塊使用的任何參數名稱。</span><span class="sxs-lookup"><span data-stu-id="5bb0c-142">You must explicitly specify any parameter names you use with **delay-bind** script blocks.</span></span>
- <span data-ttu-id="5bb0c-143">參數不可以是不具類型的，且參數的類型不得為 `[scriptblock]` 或 `[object]` 。</span><span class="sxs-lookup"><span data-stu-id="5bb0c-143">The parameter must not be untyped, and the parameter's type cannot be `[scriptblock]` or `[object]`.</span></span>
- <span data-ttu-id="5bb0c-144">如果您在不提供管線輸入的情況下使用 **延遲** 系結腳本區塊，就會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="5bb0c-144">You receive an error if you use a **delay-bind** script block without providing pipeline input.</span></span>

  ```powershell
  Rename-Item -NewName {$_.Name + ".old"}
  ```

  ```Output
  Rename-Item : Cannot evaluate parameter 'NewName' because its argument is
  specified as a script block and there is no input. A script block cannot
  be evaluated without input.
  At line:1 char:23
  +  Rename-Item -NewName {$_.Name + ".old"}
  +                       ~~~~~~~~~~~~~~~~~~
      + CategoryInfo          : MetadataError: (:) [Rename-Item],
        ParameterBindingException
      + FullyQualifiedErrorId : ScriptBlockArgumentNoInput,
        Microsoft.PowerShell.Commands.RenameItemCommand
  ```

## <a name="see-also"></a><span data-ttu-id="5bb0c-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5bb0c-145">See Also</span></span>

[<span data-ttu-id="5bb0c-146">about_Functions</span><span class="sxs-lookup"><span data-stu-id="5bb0c-146">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="5bb0c-147">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="5bb0c-147">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="5bb0c-148">about_Operators</span><span class="sxs-lookup"><span data-stu-id="5bb0c-148">about_Operators</span></span>](about_Operators.md)

