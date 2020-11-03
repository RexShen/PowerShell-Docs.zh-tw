---
description: 描述語句如何 `continue` 立即將程式流程傳回至程式迴圈、 `switch` 語句或語句的頂端 `trap` 。
keywords: powershell,cmdlet
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_continue?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Continue
ms.openlocfilehash: 51dfd85044d240f1d1429580d6eeb98c662d62c4
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208076"
---
# <a name="about-continue"></a><span data-ttu-id="a79e0-104">關於繼續</span><span class="sxs-lookup"><span data-stu-id="a79e0-104">About Continue</span></span>

## <a name="short-description"></a><span data-ttu-id="a79e0-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="a79e0-105">Short description</span></span>

<span data-ttu-id="a79e0-106">描述語句如何 `continue` 立即將程式流程傳回至程式迴圈、 `switch` 語句或語句的頂端 `trap` 。</span><span class="sxs-lookup"><span data-stu-id="a79e0-106">Describes how the `continue` statement immediately returns the program flow to the top of a program loop, a `switch` statement, or a `trap` statement.</span></span>

## <a name="long-description"></a><span data-ttu-id="a79e0-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="a79e0-107">Long description</span></span>

<span data-ttu-id="a79e0-108">`continue`語句會提供一種方式來結束目前的控制區塊，但會繼續執行，而不是完全結束。</span><span class="sxs-lookup"><span data-stu-id="a79e0-108">The `continue` statement provides a way to exit the current control block but continue execution, rather than exit completely.</span></span> <span data-ttu-id="a79e0-109">語句支援標籤。</span><span class="sxs-lookup"><span data-stu-id="a79e0-109">The statement supports labels.</span></span>
<span data-ttu-id="a79e0-110">標籤是您在腳本中指派給語句的名稱。</span><span class="sxs-lookup"><span data-stu-id="a79e0-110">A label is a name you assign to a statement in a script.</span></span>

## <a name="using-continue-in-loops"></a><span data-ttu-id="a79e0-111">在迴圈中使用 continue</span><span class="sxs-lookup"><span data-stu-id="a79e0-111">Using continue in loops</span></span>

<span data-ttu-id="a79e0-112">未標記的 `continue` 語句會立即將程式流程傳回至由 `for` 、 `foreach` 、 `do` 或語句所控制之最內層迴圈的頂端 `while` 。</span><span class="sxs-lookup"><span data-stu-id="a79e0-112">An unlabeled `continue` statement immediately returns the program flow to the top of the innermost loop that is controlled by a `for`, `foreach`, `do`, or `while` statement.</span></span> <span data-ttu-id="a79e0-113">迴圈的目前反覆運算會終止，而迴圈會繼續進行下一個反復專案。</span><span class="sxs-lookup"><span data-stu-id="a79e0-113">The current iteration of the loop is terminated and the loop continues with the next iteration.</span></span>

<span data-ttu-id="a79e0-114">在下列範例中， `while` 如果變數等於5，程式流程會返回迴圈的頂端 `$ctr` 。</span><span class="sxs-lookup"><span data-stu-id="a79e0-114">In the following example, program flow returns to the top of the `while` loop if the `$ctr` variable is equal to 5.</span></span> <span data-ttu-id="a79e0-115">因此，會顯示1到10之間的所有數位，但5：</span><span class="sxs-lookup"><span data-stu-id="a79e0-115">As a result, all the numbers between 1 and 10 are displayed except for 5:</span></span>

```powershell
while ($ctr -lt 10)
{
    $ctr += 1
    if ($ctr -eq 5)
    {
        continue
    }

    Write-Host -Object $ctr
}
```

<span data-ttu-id="a79e0-116">使用迴圈時 `for` ，會在 `<Repeat>` 語句之後繼續執行，然後進行 `<Condition>` 測試。</span><span class="sxs-lookup"><span data-stu-id="a79e0-116">When using a `for` loop, execution continues at the `<Repeat>` statement, followed by the `<Condition>` test.</span></span> <span data-ttu-id="a79e0-117">在下列範例中，不會發生無限迴圈，因為遞減 `$i` 會出現在關鍵字之後 `continue` 。</span><span class="sxs-lookup"><span data-stu-id="a79e0-117">In the example below, an infinite loop will not occur because the decrement of `$i` occurs after the `continue` keyword.</span></span>

```powershell
#   <Init>  <Condition> <Repeat>
for ($i = 0; $i -lt 10; $i++)
{
    Write-Host -Object $i
    if ($i -eq 5)
    {
        continue
        # Will not result in an infinite loop.
        $i--
    }
}
```

### <a name="using-a-labeled-continue-in-a-loop"></a><span data-ttu-id="a79e0-118">在迴圈中使用加上標籤的 continue</span><span class="sxs-lookup"><span data-stu-id="a79e0-118">Using a labeled continue in a loop</span></span>

<span data-ttu-id="a79e0-119">加上標籤的 `continue` 語句會終止反覆運算的執行，並將控制權轉移至目標的封入反復專案或 `switch` 語句標籤。</span><span class="sxs-lookup"><span data-stu-id="a79e0-119">A labeled `continue` statement terminates execution of the iteration and transfers control to the targeted enclosing iteration or `switch` statement label.</span></span>

<span data-ttu-id="a79e0-120">在下列範例中， `for` 當是 True 時，最內層會終止， `$condition` 而反復專案會在第二個 **True** `for` 迴圈中繼續 `labelB` 。</span><span class="sxs-lookup"><span data-stu-id="a79e0-120">In the following example, the innermost `for` is terminated when `$condition` is **True** and iteration continues with the second `for` loop at `labelB`.</span></span>

```powershell
:labelA for ($i = 1; $i -le 10; $i++) {
    :labelB for ($j = 1; $j -le 10; $j++) {
        :labelC for ($k = 1; $k -le 10; $k++) {
            if ($condition) {
                continue labelB
            } else {
                $condition = Update-Condition
            }
        }
    }
}
```

## <a name="using-continue-in-a-switch-statement"></a><span data-ttu-id="a79e0-121">在 switch 語句中使用 continue</span><span class="sxs-lookup"><span data-stu-id="a79e0-121">Using continue in a switch statement</span></span>

<span data-ttu-id="a79e0-122">中未標記的 `continue` 語句會 `switch` 終止目前反覆運算的 `switch` 執行，並將控制權轉移至的頂端， `switch` 以取得下一個輸入專案。</span><span class="sxs-lookup"><span data-stu-id="a79e0-122">An unlabeled `continue` statement within a `switch` terminates execution of the current `switch` iteration and transfers control to the top of the `switch` to get the next input item.</span></span>

<span data-ttu-id="a79e0-123">當有單一輸入專案結束 `continue` 整個 `switch` 語句時。</span><span class="sxs-lookup"><span data-stu-id="a79e0-123">When there is a single input item `continue` exits the entire `switch` statement.</span></span>
<span data-ttu-id="a79e0-124">當 `switch` 輸入為集合時，會 `switch` 測試集合中的每個元素。</span><span class="sxs-lookup"><span data-stu-id="a79e0-124">When the `switch` input is a collection, the `switch` tests each element of the collection.</span></span> <span data-ttu-id="a79e0-125">會結束 `continue` 目前的反復專案，並 `switch` 繼續下一個元素。</span><span class="sxs-lookup"><span data-stu-id="a79e0-125">The `continue` exits the current iteration and the `switch` continues with the next element.</span></span>

```powershell
switch (1,2,3) {
  2 { continue }  # moves on to the next element, 3
  default { $_ }
}
```

```Output
1
3
```

## <a name="using-continue-in-a-trap-statement"></a><span data-ttu-id="a79e0-126">在 trap 語句中使用 continue</span><span class="sxs-lookup"><span data-stu-id="a79e0-126">Using continue in a trap statement</span></span>

<span data-ttu-id="a79e0-127">如果在主體中執行的最後一個語句 `trap` 是 `continue` ，則會以無訊息方式忽略陷阱的錯誤，並繼續執行緊接在引發的語句後面的語句 `trap` 。</span><span class="sxs-lookup"><span data-stu-id="a79e0-127">If the final statement executed in the body a `trap` statement is `continue`, the trapped error is silently ignored and execution continues with the statement immediately following the one that caused `trap` to occur.</span></span>

## <a name="do-not-use-continue-outside-of-a-loop-switch-or-trap"></a><span data-ttu-id="a79e0-128">請勿在迴圈、切換或陷阱之外使用 continue</span><span class="sxs-lookup"><span data-stu-id="a79e0-128">Do not use continue outside of a loop, switch, or trap</span></span>

<span data-ttu-id="a79e0-129">當在 `continue` 直接支援 (迴圈、) 的結構之外使用時， `switch` `trap` PowerShell 會查閱封閉結構 _的呼叫堆疊_ 。</span><span class="sxs-lookup"><span data-stu-id="a79e0-129">When `continue` is used outside of a construct that directly supports it (loops, `switch`, `trap`), PowerShell looks _up the call stack_ for an enclosing construct.</span></span> <span data-ttu-id="a79e0-130">如果找不到封閉結構，則目前的運行空間會以安靜方式終止。</span><span class="sxs-lookup"><span data-stu-id="a79e0-130">If it can't find an enclosing construct, the current runspace is quietly terminated.</span></span>

<span data-ttu-id="a79e0-131">這表示不慎在封閉結構之外使用的函式和腳本 `continue` ，可能會不慎終止其 _呼叫_ 端。</span><span class="sxs-lookup"><span data-stu-id="a79e0-131">This means that functions and scripts that inadvertently use a `continue` outside of an enclosing construct that supports it, can inadvertently terminate their _callers_ .</span></span>

<span data-ttu-id="a79e0-132">在管線中使用（ `continue` 例如 `ForEach-Object` 腳本區塊），不只會結束管線，tt 可能會終止整個運行空間。</span><span class="sxs-lookup"><span data-stu-id="a79e0-132">Using `continue` inside a pipeline, such as a `ForEach-Object` script block, not only exits the pipeline, tt potentially terminates the entire runspace.</span></span>

## <a name="see-also"></a><span data-ttu-id="a79e0-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a79e0-133">See also</span></span>

[<span data-ttu-id="a79e0-134">about_Break</span><span class="sxs-lookup"><span data-stu-id="a79e0-134">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="a79e0-135">about_For</span><span class="sxs-lookup"><span data-stu-id="a79e0-135">about_For</span></span>](about_For.md)

[<span data-ttu-id="a79e0-136">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="a79e0-136">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="a79e0-137">about_Throw</span><span class="sxs-lookup"><span data-stu-id="a79e0-137">about_Throw</span></span>](about_Throw.md)

[<span data-ttu-id="a79e0-138">about_Trap</span><span class="sxs-lookup"><span data-stu-id="a79e0-138">about_Trap</span></span>](about_Trap.md)

[<span data-ttu-id="a79e0-139">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="a79e0-139">about_Try_Catch_Finally</span></span>](about_Try_Catch_Finally.md)
