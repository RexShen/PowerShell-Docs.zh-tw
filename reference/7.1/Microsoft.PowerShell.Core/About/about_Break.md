---
description: 描述您可以用來立即結束、、 `foreach` 、 `for` `while` `do` 、 `switch` 或 `trap` 語句的語句。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_break?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Break
ms.openlocfilehash: cd83a9487deaca0cdff1fe1af569cf4b22a36eaa
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208364"
---
# <a name="about-break"></a><span data-ttu-id="094c5-104">關於 Break</span><span class="sxs-lookup"><span data-stu-id="094c5-104">About Break</span></span>

## <a name="short-description"></a><span data-ttu-id="094c5-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="094c5-105">Short description</span></span>

<span data-ttu-id="094c5-106">描述您可以用來立即結束、、 `foreach` 、 `for` `while` `do` 、 `switch` 或 `trap` 語句的語句。</span><span class="sxs-lookup"><span data-stu-id="094c5-106">Describes a statement you can use to immediately exit `foreach`, `for`, `while`, `do`, `switch`, or `trap` statements.</span></span>

## <a name="long-description"></a><span data-ttu-id="094c5-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="094c5-107">Long description</span></span>

<span data-ttu-id="094c5-108">`break`語句提供結束目前控制區塊的方法。</span><span class="sxs-lookup"><span data-stu-id="094c5-108">The `break` statement provides a way to exit the current control block.</span></span>
<span data-ttu-id="094c5-109">執行會在控制區塊之後的下一個語句繼續執行。</span><span class="sxs-lookup"><span data-stu-id="094c5-109">Execution continues at the next statement after the control block.</span></span> <span data-ttu-id="094c5-110">語句支援標籤。</span><span class="sxs-lookup"><span data-stu-id="094c5-110">The statement supports labels.</span></span> <span data-ttu-id="094c5-111">標籤是您在腳本中指派給語句的名稱。</span><span class="sxs-lookup"><span data-stu-id="094c5-111">A label is a name you assign to a statement in a script.</span></span>

## <a name="using-break-in-loops"></a><span data-ttu-id="094c5-112">在迴圈中使用 break</span><span class="sxs-lookup"><span data-stu-id="094c5-112">Using break in loops</span></span>

<span data-ttu-id="094c5-113">當 `break` 語句出現在迴圈中（例如，、、 `foreach` `for` 或迴圈）時 `do` `while` ，PowerShell 會立即結束迴圈。</span><span class="sxs-lookup"><span data-stu-id="094c5-113">When a `break` statement appears in a loop, such as a `foreach`, `for`, `do`, or `while` loop, PowerShell immediately exits the loop.</span></span>

<span data-ttu-id="094c5-114">`break`語句可以包含一個可讓您結束內嵌迴圈的標籤。</span><span class="sxs-lookup"><span data-stu-id="094c5-114">A `break` statement can include a label that lets you exit embedded loops.</span></span> <span data-ttu-id="094c5-115">標籤可以在腳本中指定 any loop 關鍵字，例如 `foreach` 、 `for` 或 `while` 。</span><span class="sxs-lookup"><span data-stu-id="094c5-115">A label can specify any loop keyword, such as `foreach`, `for`, or `while`, in a script.</span></span>

<span data-ttu-id="094c5-116">下列範例顯示如何使用 `break` 語句來結束 `for` 語句：</span><span class="sxs-lookup"><span data-stu-id="094c5-116">The following example shows how to use a `break` statement to exit a `for` statement:</span></span>

```powershell
for($i=1; $i -le 10; $i++) {
   Write-Host $i
   break
}
```

<span data-ttu-id="094c5-117">在此範例中， `break` `for` 當變數等於1時，語句會結束迴圈 `$i` 。</span><span class="sxs-lookup"><span data-stu-id="094c5-117">In this example, the `break` statement exits the `for` loop when the `$i` variable equals 1.</span></span> <span data-ttu-id="094c5-118">即使在 `for` 大於10的情況下，語句會評估為 **True** ，但在 `$i` 第一次執行迴圈時，PowerShell 會到達 break 語句 `for` 。</span><span class="sxs-lookup"><span data-stu-id="094c5-118">Even though the `for` statement evaluates to **True** until `$i` is greater than 10, PowerShell reaches the break statement the first time the `for` loop is run.</span></span>

<span data-ttu-id="094c5-119">`break`在必須符合內部條件的迴圈中使用語句較為常見。</span><span class="sxs-lookup"><span data-stu-id="094c5-119">It is more common to use the `break` statement in a loop where an inner condition must be met.</span></span> <span data-ttu-id="094c5-120">請考慮下列 `foreach` 語句範例：</span><span class="sxs-lookup"><span data-stu-id="094c5-120">Consider the following `foreach` statement example:</span></span>

```powershell
$i=0
$varB = 10,20,30,40
foreach ($val in $varB) {
  if ($val -eq 30) {
    break
  }
  $i++
}
Write-Host "30 was found in array index $i"
```

<span data-ttu-id="094c5-121">在此範例中，語句會逐一查看 `foreach` `$varB` 陣列。</span><span class="sxs-lookup"><span data-stu-id="094c5-121">In this example, the `foreach` statement iterates the `$varB` array.</span></span> <span data-ttu-id="094c5-122">`if`語句會評估為 False，這是迴圈執行的前兩倍，而變數 `$i` 會遞增1。</span><span class="sxs-lookup"><span data-stu-id="094c5-122">The `if` statement evaluates to False the first two times the loop is run and the variable `$i` is incremented by 1.</span></span> <span data-ttu-id="094c5-123">第三次執行迴圈時， `$i` 等於2， `$val` 變數等於30。</span><span class="sxs-lookup"><span data-stu-id="094c5-123">The third time the loop is run, `$i` equals 2, and the `$val` variable equals 30.</span></span> <span data-ttu-id="094c5-124">此時， `break` 語句會執行，而且迴圈會結束 `foreach` 。</span><span class="sxs-lookup"><span data-stu-id="094c5-124">At this point, the `break` statement runs, and the `foreach` loop exits.</span></span>

### <a name="using-a-labeled-break-in-a-loop"></a><span data-ttu-id="094c5-125">在迴圈中使用加上標籤的 break</span><span class="sxs-lookup"><span data-stu-id="094c5-125">Using a labeled break in a loop</span></span>

<span data-ttu-id="094c5-126">`break`語句可以包含標籤。</span><span class="sxs-lookup"><span data-stu-id="094c5-126">A `break` statement can include a label.</span></span> <span data-ttu-id="094c5-127">如果您使用 `break` 關鍵字搭配標籤，則 PowerShell 會離開標示的迴圈，而不會結束目前的迴圈。</span><span class="sxs-lookup"><span data-stu-id="094c5-127">If you use the `break` keyword with a label, PowerShell exits the labeled loop instead of exiting the current loop.</span></span>
<span data-ttu-id="094c5-128">標籤是冒號，後面接著您指派的名稱。</span><span class="sxs-lookup"><span data-stu-id="094c5-128">The label is a colon followed by a name that you assign.</span></span> <span data-ttu-id="094c5-129">標籤必須是語句中的第一個 token，其後必須接著迴圈關鍵字（例如） `while` 。</span><span class="sxs-lookup"><span data-stu-id="094c5-129">The label must be the first token in a statement, and it must be followed by the looping keyword, such as `while`.</span></span>

<span data-ttu-id="094c5-130">`break` 將執行移出已加上標籤的迴圈。</span><span class="sxs-lookup"><span data-stu-id="094c5-130">`break` moves execution out of the labeled loop.</span></span> <span data-ttu-id="094c5-131">在內嵌迴圈中，它本身所使用的結果與 `break` 關鍵字不同。</span><span class="sxs-lookup"><span data-stu-id="094c5-131">In embedded loops, this has a different result than the `break` keyword has when it is used by itself.</span></span> <span data-ttu-id="094c5-132">此範例中有語句 `while` 與 `for` 語句：</span><span class="sxs-lookup"><span data-stu-id="094c5-132">This example has a `while` statement with a `for` statement:</span></span>

```powershell
:myLabel while (<condition 1>) {
  for ($item in $items) {
    if (<condition 2>) {
      break myLabel
    }
    $item = $x   # A statement inside the For-loop
  }
}
$a = $c  # A statement after the labeled While-loop
```

<span data-ttu-id="094c5-133">如果條件2評估為 **True** ，則腳本的執行會跳至標記迴圈之後的語句。</span><span class="sxs-lookup"><span data-stu-id="094c5-133">If condition 2 evaluates to **True** , the execution of the script skips down to the statement after the labeled loop.</span></span> <span data-ttu-id="094c5-134">在此範例中，會使用語句再次開始執行 `$a = $c` 。</span><span class="sxs-lookup"><span data-stu-id="094c5-134">In the example, execution starts again with the statement `$a = $c`.</span></span>

<span data-ttu-id="094c5-135">您可以嵌套許多標示的迴圈，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="094c5-135">You can nest many labeled loops, as shown in the following example.</span></span>

```powershell
:red while (<condition1>) {
  :yellow while (<condition2>) {
    while (<condition3>) {
      if ($a) {break}
      if ($b) {break red}
      if ($c) {break yellow}
    }
    Write-Host "After innermost loop"
  }
  Write-Host "After yellow loop"
}
Write-Host "After red loop"
```

<span data-ttu-id="094c5-136">如果 `$b` 變數評估為 True，就會在標記為 "red" 的迴圈之後繼續執行腳本。</span><span class="sxs-lookup"><span data-stu-id="094c5-136">If the `$b` variable evaluates to True, execution of the script resumes after the loop that is labeled "red".</span></span> <span data-ttu-id="094c5-137">如果 `$c` 變數評估為 True，腳本控制項的執行會在標示為 "黃色" 的迴圈之後繼續執行。</span><span class="sxs-lookup"><span data-stu-id="094c5-137">If the `$c` variable evaluates to True, execution of the script control resumes after the loop that is labeled "yellow".</span></span>

<span data-ttu-id="094c5-138">如果 `$a` 變數評估為 True，則會在最內層迴圈之後繼續執行。</span><span class="sxs-lookup"><span data-stu-id="094c5-138">If the `$a` variable evaluates to True, execution resumes after the innermost loop.</span></span> <span data-ttu-id="094c5-139">不需要標籤。</span><span class="sxs-lookup"><span data-stu-id="094c5-139">No label is needed.</span></span>

<span data-ttu-id="094c5-140">PowerShell 不會限制標籤可以繼續執行的程度。</span><span class="sxs-lookup"><span data-stu-id="094c5-140">PowerShell does not limit how far labels can resume execution.</span></span> <span data-ttu-id="094c5-141">標籤甚至可以跨腳本和函式呼叫界限傳遞控制。</span><span class="sxs-lookup"><span data-stu-id="094c5-141">The label can even pass control across script and function call boundaries.</span></span>

## <a name="using-break-in-a-switch-statement"></a><span data-ttu-id="094c5-142">在 switch 語句中使用 break</span><span class="sxs-lookup"><span data-stu-id="094c5-142">Using break in a switch statement</span></span>

<span data-ttu-id="094c5-143">在 `switch` 結構中， `break` 會導致 PowerShell 結束程式 `switch` 代碼區塊。</span><span class="sxs-lookup"><span data-stu-id="094c5-143">In a `switch`construct, `break` causes PowerShell to exit the `switch` code block.</span></span>

<span data-ttu-id="094c5-144">`break`關鍵字是用來離開 `switch` 結構。</span><span class="sxs-lookup"><span data-stu-id="094c5-144">The `break` keyword is used to leave the `switch` construct.</span></span> <span data-ttu-id="094c5-145">例如，下列語句會 `switch` 使用 `break` 語句來測試最特定的條件：</span><span class="sxs-lookup"><span data-stu-id="094c5-145">For example, the following `switch` statement uses `break` statements to test for the most specific condition:</span></span>

```powershell
$var = "word2"
switch -regex ($var) {
    "word2" {
      Write-Host "Exact" $_
      break
    }

    "word.*" {
      Write-Host "Match on the prefix" $_
      break
    }

    "w.*" {
      Write-Host "Match on at least the first letter" $_
      break
    }

    default {
      Write-Host "No match" $_
      break
    }
}
```

<span data-ttu-id="094c5-146">在此範例中， `$var` 會建立變數，並將其初始化為的字串值 `word2` 。</span><span class="sxs-lookup"><span data-stu-id="094c5-146">In this example, the `$var` variable is created and initialized to a string value of `word2`.</span></span> <span data-ttu-id="094c5-147">`switch`語句會使用 **Regex** 類別，先將變數值與詞彙比對 `word2` 。</span><span class="sxs-lookup"><span data-stu-id="094c5-147">The `switch` statement uses the **Regex** class to match the variable value first with the term `word2`.</span></span> <span data-ttu-id="094c5-148">因為變數值和語句中的第一個測試 `switch` 相符，所以語句中的第一個程式碼區塊會 `switch` 執行。</span><span class="sxs-lookup"><span data-stu-id="094c5-148">Because the variable value and the first test in the `switch` statement match, the first code block in the `switch` statement runs.</span></span>

<span data-ttu-id="094c5-149">當 PowerShell 到達第一個 `break` 語句時，語句便會結束 `switch` 。</span><span class="sxs-lookup"><span data-stu-id="094c5-149">When PowerShell reaches the first `break` statement, the `switch` statement exits.</span></span> <span data-ttu-id="094c5-150">如果 `break` 從範例移除四個語句，則會符合全部四個條件。</span><span class="sxs-lookup"><span data-stu-id="094c5-150">If the four `break` statements are removed from the example, all four conditions are met.</span></span> <span data-ttu-id="094c5-151">`break`當符合最特定條件時，此範例會使用語句來顯示結果。</span><span class="sxs-lookup"><span data-stu-id="094c5-151">This example uses the `break` statement to display results when the most specific condition is met.</span></span>

## <a name="using-break-in-a-trap-statement"></a><span data-ttu-id="094c5-152">在 trap 語句中使用 break</span><span class="sxs-lookup"><span data-stu-id="094c5-152">Using break in a trap statement</span></span>

<span data-ttu-id="094c5-153">如果在語句主體中執行的最後一個語句 `trap` 是 `break` ，則會隱藏 error 物件，並重新擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="094c5-153">If the final statement executed in the body of a `trap` statement is `break`, the error object is suppressed and the exception is re-thrown.</span></span>

<span data-ttu-id="094c5-154">下列範例會建立使用語句所捕捉的 **DivideByZeroException** 例外狀況 `trap` 。</span><span class="sxs-lookup"><span data-stu-id="094c5-154">The following example create a **DivideByZeroException** exception that is trapped using the `trap` statement.</span></span>

```powershell
function test {
  trap [DivideByZeroException] {
    Write-Host 'divide by zero trapped'
    break
  }

  $i = 3
  'Before loop'
  while ($true) {
     "1 / $i = " + (1 / $i--)
  }
  'After loop'
}
test
```

請注意，執行會在例外狀況時停止。 <span data-ttu-id="094c5-156">`After loop`永遠不會到達。</span><span class="sxs-lookup"><span data-stu-id="094c5-156">The `After loop` is never reached.</span></span>
<span data-ttu-id="094c5-157">執行之後，就會重新擲回例外狀況 `trap` 。</span><span class="sxs-lookup"><span data-stu-id="094c5-157">The exception is re-thrown after the `trap` executes.</span></span>

```Output
Before loop
1 / 3 = 0.333333333333333
1 / 2 = 0.5
1 / 1 = 1
divide by zero trapped
ParentContainsErrorRecordException:
Line |
  10 |       "1 / $i = " + (1 / $i--)
     |       ~~~~~~~~~~~~~~~~~~~~~~~~
     | Attempted to divide by zero.
```

## <a name="do-not-use-break-outside-of-a-loop-switch-or-trap"></a><span data-ttu-id="094c5-158">請勿在迴圈、切換或陷阱之外使用 break</span><span class="sxs-lookup"><span data-stu-id="094c5-158">Do not use break outside of a loop, switch, or trap</span></span>

<span data-ttu-id="094c5-159">當在 `break` 直接支援 (迴圈、) 的結構之外使用時， `switch` `trap` PowerShell 會查閱封閉結構 _的呼叫堆疊_ 。</span><span class="sxs-lookup"><span data-stu-id="094c5-159">When `break` is used outside of a construct that directly supports it (loops, `switch`, `trap`), PowerShell looks _up the call stack_ for an enclosing construct.</span></span> <span data-ttu-id="094c5-160">如果找不到封閉結構，則目前的運行空間會以安靜方式終止。</span><span class="sxs-lookup"><span data-stu-id="094c5-160">If it can't find an enclosing construct, the current runspace is quietly terminated.</span></span>

<span data-ttu-id="094c5-161">這表示不慎在封閉結構之外使用的函式和腳本， `break` 可能會不慎終止其 _呼叫_ 端。</span><span class="sxs-lookup"><span data-stu-id="094c5-161">This means that functions and scripts that inadvertently use a `break` outside of an enclosing construct that supports it can inadvertently terminate their _callers_ .</span></span>

<span data-ttu-id="094c5-162">在管線中使用（ `break` `break` 例如 `ForEach-Object` 腳本區塊），不只會結束管線，它可能會終止整個運行空間。</span><span class="sxs-lookup"><span data-stu-id="094c5-162">Using `break` inside a pipeline `break`, such as a `ForEach-Object` script block, not only exits the pipeline, it potentially terminates the entire runspace.</span></span>

## <a name="see-also"></a><span data-ttu-id="094c5-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="094c5-163">See also</span></span>

[<span data-ttu-id="094c5-164">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="094c5-164">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="094c5-165">about_Continue</span><span class="sxs-lookup"><span data-stu-id="094c5-165">about_Continue</span></span>](about_Continue.md)

[<span data-ttu-id="094c5-166">about_For</span><span class="sxs-lookup"><span data-stu-id="094c5-166">about_For</span></span>](about_For.md)

[<span data-ttu-id="094c5-167">about_Foreach</span><span class="sxs-lookup"><span data-stu-id="094c5-167">about_Foreach</span></span>](about_Foreach.md)

[<span data-ttu-id="094c5-168">about_Switch</span><span class="sxs-lookup"><span data-stu-id="094c5-168">about_Switch</span></span>](about_Switch.md)

[<span data-ttu-id="094c5-169">about_Throw</span><span class="sxs-lookup"><span data-stu-id="094c5-169">about_Throw</span></span>](about_Throw.md)

[<span data-ttu-id="094c5-170">about_Trap</span><span class="sxs-lookup"><span data-stu-id="094c5-170">about_Trap</span></span>](about_Trap.md)

[<span data-ttu-id="094c5-171">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="094c5-171">about_Try_Catch_Finally</span></span>](about_Try_Catch_Finally.md)

[<span data-ttu-id="094c5-172">about_While</span><span class="sxs-lookup"><span data-stu-id="094c5-172">about_While</span></span>](about_While.md)
