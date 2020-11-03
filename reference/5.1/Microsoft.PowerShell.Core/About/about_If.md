---
description: 描述您可以用來根據一或多個條件式測試結果執行語句清單的語言命令。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_If
ms.openlocfilehash: 8b1be96167dab47e7e15e3e5b89c46126f117541
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208011"
---
# <a name="about-if"></a><span data-ttu-id="68fd8-104">關於</span><span class="sxs-lookup"><span data-stu-id="68fd8-104">About If</span></span>

## <a name="short-description"></a><span data-ttu-id="68fd8-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="68fd8-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="68fd8-106">描述您可以用來根據一或多個條件式測試結果執行語句清單的語言命令。</span><span class="sxs-lookup"><span data-stu-id="68fd8-106">Describes a language command you can use to run statement lists based on the results of one or more conditional tests.</span></span>

## <a name="long-description"></a><span data-ttu-id="68fd8-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="68fd8-107">LONG DESCRIPTION</span></span>
<span data-ttu-id="68fd8-108">`If`如果指定的條件式測試評估為 true，您可以使用語句來執行程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="68fd8-108">You can use the `If` statement to run code blocks if a specified conditional test evaluates to true.</span></span> <span data-ttu-id="68fd8-109">如果所有先前的測試都評估為 false，您也可以指定要執行的一或多個其他條件式測試。</span><span class="sxs-lookup"><span data-stu-id="68fd8-109">You can also specify one or more additional conditional tests to run if all the prior tests evaluate to false.</span></span> <span data-ttu-id="68fd8-110">最後，如果沒有其他先前的條件式測試評估為 true，您可以指定另一個執行的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="68fd8-110">Finally, you can specify an additional code block that is run if no other prior conditional test evaluates to true.</span></span>

### <a name="syntax"></a><span data-ttu-id="68fd8-111">Syntax</span><span class="sxs-lookup"><span data-stu-id="68fd8-111">Syntax</span></span>

<span data-ttu-id="68fd8-112">下列範例顯示 `If` 語句語法：</span><span class="sxs-lookup"><span data-stu-id="68fd8-112">The following example shows the `If` statement syntax:</span></span>

```powershell
if (<test1>)
    {<statement list 1>}
[elseif (<test2>)
    {<statement list 2>}]
[else
    {<statement list 3>}]
```

<span data-ttu-id="68fd8-113">當您執行 `If` 語句時，PowerShell 會將 `<test1>` 條件運算式評估為 true 或 false。</span><span class="sxs-lookup"><span data-stu-id="68fd8-113">When you run an `If` statement, PowerShell evaluates the `<test1>` conditional expression as true or false.</span></span> <span data-ttu-id="68fd8-114">如果 `<test1>` 是 true，則會 `<statement list 1>` 執行，且 PowerShell 會結束 `If` 語句。</span><span class="sxs-lookup"><span data-stu-id="68fd8-114">If `<test1>` is true, `<statement list 1>` runs, and PowerShell exits the `If` statement.</span></span> <span data-ttu-id="68fd8-115">如果 `<test1>` 為 false，則 PowerShell 會評估條件陳述式所指定的條件 `<test2>` 。</span><span class="sxs-lookup"><span data-stu-id="68fd8-115">If `<test1>` is false, PowerShell evaluates the condition specified by the `<test2>` conditional statement.</span></span>

<span data-ttu-id="68fd8-116">如果 `<test2>` 是 true，則會 `<statement list 2>` 執行，且 PowerShell 會結束 `If` 語句。</span><span class="sxs-lookup"><span data-stu-id="68fd8-116">If `<test2>` is true, `<statement list 2>` runs, and PowerShell exits the `If` statement.</span></span> <span data-ttu-id="68fd8-117">如果 `<test1>` 和都 `<test2>` 評估為 false， `<statement list 3`> 程式碼區塊會執行，且 PowerShell 會結束 If 語句。</span><span class="sxs-lookup"><span data-stu-id="68fd8-117">If both `<test1>` and `<test2>` evaluate to false, the `<statement list 3`> code block runs, and PowerShell exits the If statement.</span></span>

<span data-ttu-id="68fd8-118">您可以使用多個 Elseif 語句來串連一系列的條件式測試。</span><span class="sxs-lookup"><span data-stu-id="68fd8-118">You can use multiple Elseif statements to chain a series of conditional tests.</span></span> <span data-ttu-id="68fd8-119">因此，只有在所有先前的測試都為 false 時，才會執行每個測試。</span><span class="sxs-lookup"><span data-stu-id="68fd8-119">So, that each test is run only if all the previous tests are false.</span></span>
<span data-ttu-id="68fd8-120">如果您需要建立 `If` 包含許多 Elseif 語句的語句，請考慮改為使用 Switch 語句。</span><span class="sxs-lookup"><span data-stu-id="68fd8-120">If you need to create an `If` statement that contains many Elseif statements, consider using a Switch statement instead.</span></span>

<span data-ttu-id="68fd8-121">範例：</span><span class="sxs-lookup"><span data-stu-id="68fd8-121">Examples:</span></span>

<span data-ttu-id="68fd8-122">最簡單的 `If` 語句包含單一命令，且不包含任何 Elseif 語句或任何 Else 語句。</span><span class="sxs-lookup"><span data-stu-id="68fd8-122">The simplest `If` statement contains a single command and does not contain any Elseif statements or any Else statements.</span></span> <span data-ttu-id="68fd8-123">下列範例顯示語句的最簡單形式 `If` ：</span><span class="sxs-lookup"><span data-stu-id="68fd8-123">The following example shows the simplest form of the `If` statement:</span></span>

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
```

<span data-ttu-id="68fd8-124">在此範例中，如果 $a 變數大於2，條件就會評估為 true，而且會執行語句清單。</span><span class="sxs-lookup"><span data-stu-id="68fd8-124">In this example, if the $a variable is greater than 2, the condition evaluates to true, and the statement list runs.</span></span> <span data-ttu-id="68fd8-125">但是，如果 $a 小於或等於2，或不是現有的變數，語句就不 `If` 會顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="68fd8-125">However, if $a is less than or equal to 2 or is not an existing variable, the `If` statement does not display a message.</span></span>

<span data-ttu-id="68fd8-126">藉由加入 Else 語句，當 $a 小於或等於2時，就會顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="68fd8-126">By adding an Else statement, a message is displayed when $a is less than or equal to 2.</span></span> <span data-ttu-id="68fd8-127">如下一個範例所示：</span><span class="sxs-lookup"><span data-stu-id="68fd8-127">As the next example shows:</span></span>

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
else {
    Write-Host ("The value $a is less than or equal to 2," +
        " is not created or is not initialized.")
}
```

<span data-ttu-id="68fd8-128">若要進一步精簡此範例，您可以使用 Elseif 語句，在 $a 的值等於2時顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="68fd8-128">To further refine this example, you can use the Elseif statement to display a message when the value of $a is equal to 2.</span></span> <span data-ttu-id="68fd8-129">如下一個範例所示：</span><span class="sxs-lookup"><span data-stu-id="68fd8-129">As the next example shows:</span></span>

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
elseif ($a -eq 2) {
    Write-Host "The value $a is equal to 2."
}
else {
    Write-Host ("The value $a is less than 2 or" +
        " was not created or initialized.")
}
```

## <a name="see-also"></a><span data-ttu-id="68fd8-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68fd8-130">SEE ALSO</span></span>

[<span data-ttu-id="68fd8-131">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="68fd8-131">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="68fd8-132">about_Switch</span><span class="sxs-lookup"><span data-stu-id="68fd8-132">about_Switch</span></span>](about_Switch.md)
