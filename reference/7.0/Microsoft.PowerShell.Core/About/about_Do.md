---
description: 執行一個或多個語句清單，受限於 While 或 Until 條件。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_do?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Do
ms.openlocfilehash: ee4d7fbb53c5d1e9dd72243385f7eca0f4665623
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208231"
---
# <a name="about-do"></a><span data-ttu-id="0dff2-104">關於</span><span class="sxs-lookup"><span data-stu-id="0dff2-104">About Do</span></span>

## <a name="short-description"></a><span data-ttu-id="0dff2-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="0dff2-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="0dff2-106">執行一個或多個語句清單，受限於 While 或 Until 條件。</span><span class="sxs-lookup"><span data-stu-id="0dff2-106">Runs a statement list one or more times, subject to a While or Until condition.</span></span>

## <a name="long-description"></a><span data-ttu-id="0dff2-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="0dff2-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="0dff2-108">Do 關鍵字適用于 While 關鍵字或 Until 關鍵字，以執行腳本區塊中的語句，受限於條件。</span><span class="sxs-lookup"><span data-stu-id="0dff2-108">The Do keyword works with the While keyword or the Until keyword to run the statements in a script block, subject to a condition.</span></span> <span data-ttu-id="0dff2-109">與相關 While 迴圈不同的是，Do 迴圈中的腳本區塊一律會至少執行一次。</span><span class="sxs-lookup"><span data-stu-id="0dff2-109">Unlike the related While loop, the script block in a Do loop always runs at least once.</span></span>

<span data-ttu-id="0dff2-110">While **迴圈是** 各種 While 迴圈。</span><span class="sxs-lookup"><span data-stu-id="0dff2-110">A **Do-While** loop is a variety of the While loop.</span></span> <span data-ttu-id="0dff2-111">在 **Do While** 迴圈中，此條件會在腳本區塊執行之後評估。</span><span class="sxs-lookup"><span data-stu-id="0dff2-111">In a **Do-While** loop, the condition is evaluated after the script block has run.</span></span> <span data-ttu-id="0dff2-112">如同 While 迴圈一樣，只要條件評估為 true，就會重複執行腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="0dff2-112">As in a While loop, the script block is repeated as long as the condition evaluates to true.</span></span>

<span data-ttu-id="0dff2-113">就像 **While** 迴圈一樣，在評估條件之前， **Do Until** 迴圈一律會至少執行一次。</span><span class="sxs-lookup"><span data-stu-id="0dff2-113">Like a **Do-While** loop, a **Do-Until** loop always runs at least once before the condition is evaluated.</span></span> <span data-ttu-id="0dff2-114">不過，腳本區塊只會在條件為 false 時執行。</span><span class="sxs-lookup"><span data-stu-id="0dff2-114">However, the script block runs only while the condition is false.</span></span>

<span data-ttu-id="0dff2-115">*Continue* 和 *Break* 流程式控制制關鍵字可用於 **do While** 迴圈中，或在 **do Until** 迴圈中使用。</span><span class="sxs-lookup"><span data-stu-id="0dff2-115">The *Continue* and *Break* flow control keywords can be used in a **Do-While** loop or in a **Do-Until** loop.</span></span>

### <a name="syntax"></a><span data-ttu-id="0dff2-116">Syntax</span><span class="sxs-lookup"><span data-stu-id="0dff2-116">Syntax</span></span>

<span data-ttu-id="0dff2-117">以下顯示 **Do While** 語句的語法：</span><span class="sxs-lookup"><span data-stu-id="0dff2-117">The following shows the syntax of the **Do-While** statement:</span></span>

```powershell
do {<statement list>} while (<condition>)
```

<span data-ttu-id="0dff2-118">以下顯示 **Do Until** 語句的語法：</span><span class="sxs-lookup"><span data-stu-id="0dff2-118">The following shows the syntax of the **Do-Until** statement:</span></span>

```powershell
do {<statement list>} until (<condition>)
```

<span data-ttu-id="0dff2-119">語句清單包含一或多個在每次輸入或重複迴圈時執行的語句。</span><span class="sxs-lookup"><span data-stu-id="0dff2-119">The statement list contains one or more statements that run each time the loop is entered or repeated.</span></span>

<span data-ttu-id="0dff2-120">語句的條件部分會解析為 true 或 false。</span><span class="sxs-lookup"><span data-stu-id="0dff2-120">The condition portion of the statement resolves to true or false.</span></span>

### <a name="example"></a><span data-ttu-id="0dff2-121">範例</span><span class="sxs-lookup"><span data-stu-id="0dff2-121">Example</span></span>

<span data-ttu-id="0dff2-122">下列 Do 語句範例會計算陣列中的專案，直到到達值為0的專案為止。</span><span class="sxs-lookup"><span data-stu-id="0dff2-122">The following example of a Do statement counts the items in an array until it reaches an item with a value of 0.</span></span>

```powershell
C:\PS> $x = 1,2,78,0
C:\PS> do { $count++; $a++; } while ($x[$a] -ne 0)
C:\PS> $count
3
```

<span data-ttu-id="0dff2-123">下列範例會使用 Until 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="0dff2-123">The following example uses the Until keyword.</span></span> <span data-ttu-id="0dff2-124">請注意，不等於運算子 (`-ne`) 會取代為等於運算子 (`-eq`) 。</span><span class="sxs-lookup"><span data-stu-id="0dff2-124">Notice that the not equal to operator (`-ne`) is replaced by the equal to operator (`-eq`).</span></span>

```powershell
C:\PS> $x = 1,2,78,0
C:\PS> do { $count++; $a++; } until ($x[$a] -eq 0)
C:\PS> $count
3
```

<span data-ttu-id="0dff2-125">下列範例會寫入陣列的所有值，並略過任何小於零的值。</span><span class="sxs-lookup"><span data-stu-id="0dff2-125">The following example writes all the values of an array, skipping any value that is less than zero.</span></span>

```powershell
do {
  if ($x[$a] -lt 0) { continue }
  Write-Host $x[$a]
}
while (++$a -lt 10)
```

## <a name="see-also"></a><span data-ttu-id="0dff2-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0dff2-126">SEE ALSO</span></span>

[<span data-ttu-id="0dff2-127">about_While</span><span class="sxs-lookup"><span data-stu-id="0dff2-127">about_While</span></span>](about_While.md)

[<span data-ttu-id="0dff2-128">about_Operators</span><span class="sxs-lookup"><span data-stu-id="0dff2-128">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="0dff2-129">about_Assignment_Operators</span><span class="sxs-lookup"><span data-stu-id="0dff2-129">about_Assignment_Operators</span></span>](about_Assignment_Operators.md)

[<span data-ttu-id="0dff2-130">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="0dff2-130">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="0dff2-131">about_Break</span><span class="sxs-lookup"><span data-stu-id="0dff2-131">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="0dff2-132">about_Continue</span><span class="sxs-lookup"><span data-stu-id="0dff2-132">about_Continue</span></span>](about_Continue.md)
