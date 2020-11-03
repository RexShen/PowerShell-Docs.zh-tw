---
description: 描述您可以用來根據條件式測試執行語句的語言命令。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 3/4/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_for?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_For
ms.openlocfilehash: 5f4fc025ee36e99de7d2ad7a00b1c1dca9c5ce3f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207104"
---
# <a name="about-for"></a><span data-ttu-id="6e0fb-104">關於</span><span class="sxs-lookup"><span data-stu-id="6e0fb-104">About For</span></span>

## <a name="short-description"></a><span data-ttu-id="6e0fb-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="6e0fb-105">Short description</span></span>
<span data-ttu-id="6e0fb-106">描述您可以用來根據條件式測試執行語句的語言命令。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-106">Describes a language command you can use to run statements based on a conditional test.</span></span>

## <a name="long-description"></a><span data-ttu-id="6e0fb-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="6e0fb-107">Long description</span></span>

<span data-ttu-id="6e0fb-108">`For`語句 (也稱為 `For` 迴圈) 是一種語言結構，可讓您在指定的條件評估為時，用來建立在命令區塊中執行命令的迴圈 `$true` 。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-108">The `For` statement (also known as a `For` loop) is a language construct you can use to create a loop that runs commands in a command block while a specified condition evaluates to `$true`.</span></span>

<span data-ttu-id="6e0fb-109">迴圈的一般用法 `For` 是反覆運算值的陣列，並在這些值的子集上運作。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-109">A typical use of the `For` loop is to iterate an array of values and to operate on a subset of these values.</span></span> <span data-ttu-id="6e0fb-110">在大部分的情況下，如果您想要逐一查看陣列中的所有值，請考慮使用 `Foreach` 語句。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-110">In most cases, if you want to iterate all the values in an array, consider using a `Foreach` statement.</span></span>

### <a name="syntax"></a><span data-ttu-id="6e0fb-111">Syntax</span><span class="sxs-lookup"><span data-stu-id="6e0fb-111">Syntax</span></span>

<span data-ttu-id="6e0fb-112">以下顯示 `For` 語句語法。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-112">The following shows the `For` statement syntax.</span></span>

```
for (<Init>; <Condition>; <Repeat>)
{
    <Statement list>
}
```

<span data-ttu-id="6e0fb-113">**Init** 預留位置代表在迴圈開始之前執行的一或多個命令。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-113">The **Init** placeholder represents one or more commands that are run before the loop begins.</span></span> <span data-ttu-id="6e0fb-114">您通常會使用語句的 **Init** 部分來建立和初始化具有起始值的變數。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-114">You typically use the **Init** portion of the statement to create and initialize a variable with a starting value.</span></span>

<span data-ttu-id="6e0fb-115">然後，這個變數會是在語句下一個部分中測試條件的基礎 `For` 。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-115">This variable will then be the basis for the condition to be tested in the next portion of the `For` statement.</span></span>

<span data-ttu-id="6e0fb-116">**條件** 預留位置代表 `For` 解析為 `$true` 或 `$false` **布林** 值之語句的部分。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-116">The **Condition** placeholder represents the portion of the `For` statement that resolves to a `$true` or `$false` **Boolean** value.</span></span> <span data-ttu-id="6e0fb-117">PowerShell 會在每次執行迴圈時評估條件 `For` 。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-117">PowerShell evaluates the condition each time the `For` loop runs.</span></span> <span data-ttu-id="6e0fb-118">如果語句是 `$true` ，則會執行命令區塊中的命令，並再次評估語句。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-118">If the statement is `$true`, the commands in the command block run, and the statement is evaluated again.</span></span> <span data-ttu-id="6e0fb-119">如果條件仍然是 `$true` ，則 **語句清單** 中的命令會再次執行。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-119">If the condition is still `$true`, the commands in the **Statement list** run again.</span></span> <span data-ttu-id="6e0fb-120">迴圈會重複，直到條件變成為止 `$false` 。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-120">The loop is repeated until the condition becomes `$false`.</span></span>

<span data-ttu-id="6e0fb-121">**重複** 的預留位置代表一個或多個命令（以逗號分隔），這些命令會在每次迴圈重複時執行。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-121">The **Repeat** placeholder represents one or more commands, separated by commas, that are executed each time the loop repeats.</span></span> <span data-ttu-id="6e0fb-122">一般來說，這是用來修改在語句的 **條件** 部分內測試的變數。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-122">Typically, this is used to modify a variable that is tested inside the **Condition** part of the statement.</span></span>

<span data-ttu-id="6e0fb-123">**語句清單** 預留位置代表一組一或多個在每次輸入或重複迴圈時都會執行的命令。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-123">The **Statement list** placeholder represents a set of one or more commands that are run each time the loop is entered or repeated.</span></span> <span data-ttu-id="6e0fb-124">**語句清單** 的內容會以大括弧括住。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-124">The contents of the **Statement list** are surrounded by braces.</span></span>

### <a name="support-for-multiple-operations"></a><span data-ttu-id="6e0fb-125">支援多項作業</span><span class="sxs-lookup"><span data-stu-id="6e0fb-125">Support for multiple operations</span></span>

<span data-ttu-id="6e0fb-126">**Init** 語句中的多個指派作業支援下列語法：</span><span class="sxs-lookup"><span data-stu-id="6e0fb-126">The following syntaxes are supported for multiple assignment operations in the **Init** statement:</span></span>

```powershell
# Comma separated assignment expressions enclosed in parenthesis.
for (($i = 0), ($j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}

# Sub-expression using the semicolon to separate statements.
for ($($i = 0;$j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}
```

<span data-ttu-id="6e0fb-127">在 **重複** 語句中，有多個指派作業支援下列語法：</span><span class="sxs-lookup"><span data-stu-id="6e0fb-127">The following syntaxes are supported for multiple assignment operations in the **Repeat** statement:</span></span>

```powershell
# Comma separated assignment expressions.
for (($i = 0), ($j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}

# Comma separated assignment expressions enclosed in parenthesis.
for (($i = 0), ($j = 0); $i -lt 10; ($i++), ($j++))
{
    "`$i:$i"
    "`$j:$j"
}

# Sub-expression using the semicolon to separate statements.
for ($($i = 0;$j = 0); $i -lt 10; $($i++;$j++))
{
    "`$i:$i"
    "`$j:$j"
}
```

> [!NOTE]
> <span data-ttu-id="6e0fb-128">前置或後置遞增以外的作業可能無法用於所有語法。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-128">Operations other than pre or post increment may not work with all syntaxes.</span></span>

<span data-ttu-id="6e0fb-129">針對多個 **條件** ，請使用邏輯運算子，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-129">For multiple **Conditions** use logical operators as demonstrated by the following example.</span></span>

```powershell
for (($i = 0), ($j = 0); $i -lt 10 -and $j -lt 10; $i++,$j++)
{
    "`$i:$i"
    "`$j:$j"
}
```

<span data-ttu-id="6e0fb-130">如需詳細資訊，請參閱 [about_Logical_Operators](about_Logical_Operators.md)。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-130">For more information, see [about_Logical_Operators](about_Logical_Operators.md).</span></span>

### <a name="examples"></a><span data-ttu-id="6e0fb-131">範例</span><span class="sxs-lookup"><span data-stu-id="6e0fb-131">Examples</span></span>

<span data-ttu-id="6e0fb-132">`For`語句至少需要圍繞 **Init** 、 **Condition** 和 **Repeat** 部分的括弧，以及語句的 **語句清單** 部分中以大括弧括住的命令。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-132">At a minimum, a `For` statement requires the parenthesis surrounding the **Init** , **Condition** , and **Repeat** part of the statement and a command surrounded by braces in the **Statement list** part of the statement.</span></span>

<span data-ttu-id="6e0fb-133">請注意，即將推出的範例會刻意顯示語句之外的程式碼 `For` 。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-133">Note that the upcoming examples intentionally show code outside the `For` statement.</span></span> <span data-ttu-id="6e0fb-134">在稍後的範例中，程式碼會整合到 `For` 語句中。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-134">In later examples, code is integrated into the `For` statement.</span></span>

<span data-ttu-id="6e0fb-135">例如，下列 `For` 語句會持續顯示變數的值， `$i` 直到您按下 CTRL + C 以手動方式中斷命令為止。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-135">For example, the following `For` statement continually displays the value of the `$i` variable until you manually break out of the command by pressing CTRL+C.</span></span>

```powershell
$i = 1
for (;;)
{
    Write-Host $i
}
```

<span data-ttu-id="6e0fb-136">您可以將其他命令加入至語句清單，讓的值在 `$i` 每次執行迴圈時遞增1，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-136">You can add additional commands to the statement list so that the value of `$i` is incremented by 1 each time the loop is run, as the following example shows.</span></span>

```powershell
for (;;)
{
    $i++; Write-Host $i
}
```

<span data-ttu-id="6e0fb-137">在您按下 CTRL + C 來中斷命令之前，此語句會持續顯示變數的值， `$i` 因為每次執行迴圈時，它會遞增1。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-137">Until you break out of the command by pressing CTRL+C, this statement will continually display the value of the `$i` variable as it is incremented by 1 each time the loop is run.</span></span>

<span data-ttu-id="6e0fb-138">`For`您可以改為使用語句的 **重複** 部分，而不是變更語句的語句清單部分中的變數值，如下所示 `For` 。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-138">Rather than change the value of the variable in the statement list part of the `For` statement, you can use the **Repeat** portion of the `For` statement instead, as follows.</span></span>

```powershell
$i=1
for (;;$i++)
{
    Write-Host $i
}
```

<span data-ttu-id="6e0fb-139">除非您按下 CTRL + C，否則這個語句仍會無限期地重複執行，直到您中斷命令為止。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-139">This statement will still repeat indefinitely until you break out of the command by pressing CTRL+C.</span></span>

<span data-ttu-id="6e0fb-140">您可以 `For` 使用 *條件* 來結束迴圈。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-140">You can terminate the `For` loop using a *condition* .</span></span> <span data-ttu-id="6e0fb-141">您可以使用語句的 **條件** 部分來放置條件 `For` 。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-141">You can place a condition using the **Condition** portion of the `For` statement.</span></span> <span data-ttu-id="6e0fb-142">`For`當條件評估為時，迴圈就會終止 `$false` 。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-142">The `For` loop terminates when the condition evaluates to `$false`.</span></span>

<span data-ttu-id="6e0fb-143">在下列範例中， `For` 迴圈會在的值 `$i` 小於或等於10時執行。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-143">In the following example, the `For` loop runs while the value of `$i` is less than or equal to 10.</span></span>

```powershell
$i=1
for(;$i -le 10;$i++)
{
    Write-Host $i
}
```

<span data-ttu-id="6e0fb-144">`For`您可以 `For` 使用語句的 **Init** 部分，在迴圈內執行這項工作，而不是在語句之外建立和初始化變數 `For` 。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-144">Instead of creating and initializing the variable outside the `For` statement, you can perform this task inside the `For` loop by using the **Init** portion of the `For` statement.</span></span>

```powershell
for($i=1; $i -le 10; $i++){Write-Host $i}
```

<span data-ttu-id="6e0fb-145">您可以使用換行字元（而不是分號）來分隔語句的 **Init** 、 **Condition** 和 **Repeat** 部分 `For` 。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-145">You can use carriage returns instead of semicolons to delimit the **Init** , **Condition** , and **Repeat** portions of the `For` statement.</span></span> <span data-ttu-id="6e0fb-146">下列範例顯示 `For` 使用這個替代語法的。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-146">The following example shows a `For` that uses this alternative syntax.</span></span>

```powershell
for ($i = 0
  $i -lt 10
  $i++){
  $i
}
```

<span data-ttu-id="6e0fb-147">這種替代形式的 `For` 語句適用于 powershell 腳本檔案和 powershell 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-147">This alternative form of the `For` statement works in PowerShell script files and at the PowerShell command prompt.</span></span> <span data-ttu-id="6e0fb-148">但是， `For` 當您在命令提示字元中輸入互動式命令時，以分號使用語句語法會比較容易。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-148">However, it is easier to use the `For` statement syntax with semicolons when you enter interactive commands at the command prompt.</span></span>

<span data-ttu-id="6e0fb-149">`For`迴圈比迴圈更有彈性， `Foreach` 因為它可讓您使用模式來遞增陣列或集合中的值。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-149">The `For` loop is more flexible than the `Foreach` loop because it allows you to increment values in an array or collection by using patterns.</span></span> <span data-ttu-id="6e0fb-150">在下列範例中， `$i` 變數會在語句的 **重複** 部分中遞增 2 `For` 。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-150">In the following example, the `$i` variable is incremented by 2 in the **Repeat** portion of the `For` statement.</span></span>

```powershell
for ($i = 0; $i -le 20; $i += 2)
{
    Write-Host $i
}
```

<span data-ttu-id="6e0fb-151">`For`迴圈也可以撰寫在一行，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="6e0fb-151">The `For` loop can also be written on one line as in the following example.</span></span>

```powershell
for ($i = 0; $i -lt 10; $i++) { Write-Host $i }
```

## <a name="see-also"></a><span data-ttu-id="6e0fb-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e0fb-152">SEE ALSO</span></span>

[<span data-ttu-id="6e0fb-153">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="6e0fb-153">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="6e0fb-154">about_Foreach</span><span class="sxs-lookup"><span data-stu-id="6e0fb-154">about_Foreach</span></span>](about_Foreach.md)
