---
title: If 陳述式的完整說明
description: 就像許多其他語言一樣，PowerShell 提供的陳述式也可讓您在指令碼中按條件執行程式碼。
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: b6bafb99bfb8ecd0152bae841e5c58d4c27ccd3e
ms.sourcegitcommit: 0afff6edbe560e88372dd5f1cdf51d77f9349972
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2020
ms.locfileid: "86469747"
---
# <a name="everything-you-wanted-to-know-about-the-if-statement"></a><span data-ttu-id="aaaaa-103">`if` 陳述式的完整說明</span><span class="sxs-lookup"><span data-stu-id="aaaaa-103">Everything you wanted to know about the `if` statement</span></span>

<span data-ttu-id="aaaaa-104">就像許多其他語言一樣，PowerShell 提供的陳述式也可讓您在指令碼中按條件執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-104">Like many other languages, PowerShell has statements for conditionally executing code in your scripts.</span></span> <span data-ttu-id="aaaaa-105">其中一個陳述式就是 [If][] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-105">One of those statements is the [If][] statement.</span></span> <span data-ttu-id="aaaaa-106">今天，我們將深入探討 PowerShell 其中一個最基本的命令。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-106">Today we will take a deep dive into one of the most fundamental commands in PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="aaaaa-107">[原文][]出自 [@KevinMarquette][] 所撰寫的部落格。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-107">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="aaaaa-108">PowerShell 小組感謝 Kevin 分享此內容。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-108">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="aaaaa-109">請前往 [PowerShellExplained.com][] 瀏覽他的部落格。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-109">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="conditional-execution"></a><span data-ttu-id="aaaaa-110">條件式執行</span><span class="sxs-lookup"><span data-stu-id="aaaaa-110">Conditional execution</span></span>

<span data-ttu-id="aaaaa-111">您的指令碼經常必須做出決策，並根據這些決策執行不同的邏輯。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-111">Your scripts often need to make decisions and perform different logic based on those decisions.</span></span>
<span data-ttu-id="aaaaa-112">這就是我所謂的條件式執行。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-112">This is what I mean by conditional execution.</span></span> <span data-ttu-id="aaaaa-113">您可以使用一個陳述式或值來進行評估，然後根據該評估結果執行不同的程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-113">You have one statement or value to evaluate, then execute a different section of code based on that evaluation.</span></span> <span data-ttu-id="aaaaa-114">這就是 `if` 陳述式的功能所在。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-114">This is exactly what the `if` statement does.</span></span>

## <a name="the-if-statement"></a><span data-ttu-id="aaaaa-115">`if` 陳述式</span><span class="sxs-lookup"><span data-stu-id="aaaaa-115">The `if` statement</span></span>

<span data-ttu-id="aaaaa-116">以下是 `if` 陳述式的基本範例：</span><span class="sxs-lookup"><span data-stu-id="aaaaa-116">Here is a basic example of the `if` statement:</span></span>

```powershell
$condition = $true
if ( $condition )
{
    Write-Output "The condition was true"
}
```

<span data-ttu-id="aaaaa-117">`if` 陳述式會先評估括弧中的運算式。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-117">The first thing the `if` statement does is evaluate the expression in parentheses.</span></span> <span data-ttu-id="aaaaa-118">若評估為 `$true`，就會執行大括弧中的 `scriptblock`。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-118">If it evaluates to `$true`, then it executes the `scriptblock` in the braces.</span></span> <span data-ttu-id="aaaaa-119">若值為 `$false`，就會略過該指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-119">If the value was `$false`, then it would skip over that scriptblock.</span></span>

<span data-ttu-id="aaaaa-120">在上述範例中，`if` 陳述式只評估 `$condition` 變數。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-120">In the previous example, the `if` statement was just evaluating the `$condition` variable.</span></span> <span data-ttu-id="aaaaa-121">結果是 `$true`，因此會在指令碼區塊內執行 `Write-Output` 命令。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-121">It was `$true` and would have executed the `Write-Output` command inside the scriptblock.</span></span>

<span data-ttu-id="aaaaa-122">在某些語言中，您可以將任何一行程式碼置於 `if` 陳述式後方，就會執行該程式碼。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-122">In some languages, you can place a single line of code after the `if` statement and it gets executed.</span></span> <span data-ttu-id="aaaaa-123">但 PowerShell 的情況並非如此。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-123">That isn't the case in PowerShell.</span></span> <span data-ttu-id="aaaaa-124">您必須提供完整的 `scriptblock` 並加上大括弧，才能正確運作。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-124">You must provide a full `scriptblock` with braces for it to work correctly.</span></span>

## <a name="comparison-operators"></a><span data-ttu-id="aaaaa-125">比較運算子</span><span class="sxs-lookup"><span data-stu-id="aaaaa-125">Comparison operators</span></span>

<span data-ttu-id="aaaaa-126">`if` 陳述式最常見的用法是用來將兩個項目互相比較。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-126">The most common use of the `if` statement for is comparing two items with each other.</span></span> <span data-ttu-id="aaaaa-127">PowerShell 提供特殊運算子以用於不同的比較案例。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-127">PowerShell has special operators for different comparison scenarios.</span></span> <span data-ttu-id="aaaaa-128">當您使用比較運算子時，其會比較左側的值和右側的值。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-128">When you use a comparison operator, the value on the left-hand side is compared to the value on the right-hand side.</span></span>

### <a name="-eq-for-equality"></a><span data-ttu-id="aaaaa-129">-eq 表示相等</span><span class="sxs-lookup"><span data-stu-id="aaaaa-129">-eq for equality</span></span>

<span data-ttu-id="aaaaa-130">`-eq` 會對兩個值進行相等檢查，以確保兩者相等。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-130">The `-eq` does an equality check between two values to make sure they're equal to each other.</span></span>

```powershell
$value = Get-MysteryValue
if ( 5 -eq $value )
{
    # do something
}
```

<span data-ttu-id="aaaaa-131">在這個範例中，我用已知的 `5` 值來比較我的 `$value`，以查看兩者是否相符。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-131">In this example, I'm taking a known value of `5` and comparing it to my `$value` to see if they match.</span></span>

<span data-ttu-id="aaaaa-132">其中一個可能的使用案例是先檢查值的狀態，然後再對其採取動作。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-132">One possible use case is to check the status of a value before you take an action on it.</span></span> <span data-ttu-id="aaaaa-133">您可以取得某個服務，並確認其為執行狀態，然後呼叫 `Restart-Service`。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-133">You could get a service and check that the status was running before you called `Restart-Service` on it.</span></span>

<span data-ttu-id="aaaaa-134">C# 等其他語言常會使用 `==` 來表示相等 (例如 `5 == $value`)，但 PowerShell 不適用此方法。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-134">It's common in other languages like C# to use `==` for equality (ex: `5 == $value`) but that doesn't work with PowerShell.</span></span> <span data-ttu-id="aaaaa-135">另一個常見的錯誤是使用專門用來指派值給變數的等號 (例如 `5 = $value`)。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-135">Another common mistake that people make is to use the equals sign (ex: `5 = $value`) that is reserved for assigning values to variables.</span></span> <span data-ttu-id="aaaaa-136">此外，將已知值放在左側，這會造成更可怕的錯誤。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-136">By placing your known value on the left, it makes that mistake more awkward to make.</span></span>

<span data-ttu-id="aaaaa-137">這個運算子 (和其他運算子) 有一些變化。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-137">This operator (and others) has a few variations.</span></span>

- <span data-ttu-id="aaaaa-138">`-eq` 等於 (不區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-138">`-eq` case-insensitive equality</span></span>
- <span data-ttu-id="aaaaa-139">`-ieq` 等於 (不區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-139">`-ieq` case-insensitive equality</span></span>
- <span data-ttu-id="aaaaa-140">`-ceq` 等於 (區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-140">`-ceq` case-sensitive equality</span></span>

### <a name="-ne-not-equal"></a><span data-ttu-id="aaaaa-141">-ne 不等於</span><span class="sxs-lookup"><span data-stu-id="aaaaa-141">-ne not equal</span></span>

<span data-ttu-id="aaaaa-142">許多運算子都有作用相反 (檢查相反結果) 的相關運算子。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-142">Many operators have a related operator that is checking for the opposite result.</span></span> <span data-ttu-id="aaaaa-143">`-ne` 可確認值不相等。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-143">`-ne` verifies that the values don't equal each other.</span></span>

```powershell
if ( 5 -ne $value )
{
    # do something
}
```

<span data-ttu-id="aaaaa-144">您可以使用此項目來確保只有當值不是 `5` 時才會執行動作。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-144">Use this to make sure that the action only executes if the value isn't `5`.</span></span> <span data-ttu-id="aaaaa-145">良好的使用案例是在您嘗試啟動服務之前，先檢查其是否處於執行中狀態。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-145">A good use-cases where would be to check if a service was in the running state before you try to start it.</span></span>

<span data-ttu-id="aaaaa-146">**變化：**</span><span class="sxs-lookup"><span data-stu-id="aaaaa-146">**Variations:**</span></span>

- <span data-ttu-id="aaaaa-147">`-ne` 不等於 (不區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-147">`-ne` case-insensitive not equal</span></span>
- <span data-ttu-id="aaaaa-148">`-ine` 不等於 (不區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-148">`-ine` case-insensitive not equal</span></span>
- <span data-ttu-id="aaaaa-149">`-cne` 不等於 (區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-149">`-cne` case-sensitive not equal</span></span>

<span data-ttu-id="aaaaa-150">這些是 `-eq` 的反向變化。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-150">These are inverse variations of `-eq`.</span></span> <span data-ttu-id="aaaaa-151">當我列出其他運算子的變化時，會將這些類型整理在一起。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-151">I'll group these types together when I list variations for other operators.</span></span>

### <a name="-gt--ge--lt--le-for-greater-than-or-less-than"></a><span data-ttu-id="aaaaa-152">-gt -ge -lt -le 表示大於或小於</span><span class="sxs-lookup"><span data-stu-id="aaaaa-152">-gt -ge -lt -le for greater than or less than</span></span>

<span data-ttu-id="aaaaa-153">這些運算子可用來檢查值是否大於或小於另一個值。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-153">These operators are used when checking to see if a value is larger or smaller than another value.</span></span>
<span data-ttu-id="aaaaa-154">`-gt -ge -lt -le` 代表 GreaterThan、GreaterThanOrEqual、LessThan 和 LessThanOrEqual。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-154">The `-gt -ge -lt -le` stand for GreaterThan, GreaterThanOrEqual, LessThan, and LessThanOrEqual.</span></span>

```powershell
if ( $value -gt 5 )
{
    # do something
}
```

<span data-ttu-id="aaaaa-155">**變化：**</span><span class="sxs-lookup"><span data-stu-id="aaaaa-155">**Variations:**</span></span>

- <span data-ttu-id="aaaaa-156">`-gt` 大於</span><span class="sxs-lookup"><span data-stu-id="aaaaa-156">`-gt` greater than</span></span>
- <span data-ttu-id="aaaaa-157">`-igt` 大於 (不區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-157">`-igt` greater than, case-insensitive</span></span>
- <span data-ttu-id="aaaaa-158">`-cgt` 大於 (區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-158">`-cgt` greater than, case-sensitive</span></span>
- <span data-ttu-id="aaaaa-159">`-ge` 大於或等於</span><span class="sxs-lookup"><span data-stu-id="aaaaa-159">`-ge` greater than or equal</span></span>
- <span data-ttu-id="aaaaa-160">`-ige` 大於或等於 (不區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-160">`-ige` greater than or equal, case-insensitive</span></span>
- <span data-ttu-id="aaaaa-161">`-cge` 大於或等於 (區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-161">`-cge` greater than or equal, case-sensitive</span></span>
- <span data-ttu-id="aaaaa-162">`-lt` 小於</span><span class="sxs-lookup"><span data-stu-id="aaaaa-162">`-lt` less than</span></span>
- <span data-ttu-id="aaaaa-163">`-ilt` 小於 (不區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-163">`-ilt` less than, case-insensitive</span></span>
- <span data-ttu-id="aaaaa-164">`-clt` 小於 (區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-164">`-clt` less than, case-sensitive</span></span>
- <span data-ttu-id="aaaaa-165">`-le` 小於或等於</span><span class="sxs-lookup"><span data-stu-id="aaaaa-165">`-le` less than or equal</span></span>
- <span data-ttu-id="aaaaa-166">`-ile` 小於或等於 (不區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-166">`-ile` less than or equal, case-insensitive</span></span>
- <span data-ttu-id="aaaaa-167">`-cle` 小於或等於 (區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-167">`-cle` less than or equal, case-sensitive</span></span>

<span data-ttu-id="aaaaa-168">我不知道這些運算子為何要有區分大小寫和不區分大小寫的選項。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-168">I don't know why you would use case-sensitive and insensitive options for these operators.</span></span>

### <a name="-like-wildcard-matches"></a><span data-ttu-id="aaaaa-169">-like 萬用字元比對</span><span class="sxs-lookup"><span data-stu-id="aaaaa-169">-like wildcard matches</span></span>

<span data-ttu-id="aaaaa-170">PowerShell 有自己的萬用字元模式比對語法，可讓您搭配 `-like` 運算子使用。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-170">PowerShell has its own wildcard-based pattern matching syntax and you can use it with the `-like` operator.</span></span> <span data-ttu-id="aaaaa-171">這些萬用字元模式都很基本。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-171">These wildcard patterns are fairly basic.</span></span>

- <span data-ttu-id="aaaaa-172">`?` 比對任何單一字元</span><span class="sxs-lookup"><span data-stu-id="aaaaa-172">`?` matches any single character</span></span>
- <span data-ttu-id="aaaaa-173">`*` 比對任何字元數</span><span class="sxs-lookup"><span data-stu-id="aaaaa-173">`*` matches any number of characters</span></span>

```powershell
$value = 'S-ATX-SQL01'
if ( $value -like 'S-*-SQL??')
{
    # do something
}
```

<span data-ttu-id="aaaaa-174">請務必注意，模式會比對整個字串。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-174">It's important to point out that the pattern matches the whole string.</span></span> <span data-ttu-id="aaaaa-175">若您要比對字串中的某個項目，則必須將 `*` 放在字串的兩端。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-175">If you need to match something in the middle of the string, you need to place the `*` on both ends of the string.</span></span>

```powershell
$value = 'S-ATX-SQL02'
if ( $value -like '*SQL*')
{
    # do something
}
```

<span data-ttu-id="aaaaa-176">**變化：**</span><span class="sxs-lookup"><span data-stu-id="aaaaa-176">**Variations:**</span></span>

- <span data-ttu-id="aaaaa-177">`-like` 萬用字元 (不區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-177">`-like` case-insensitive wildcard</span></span>
- <span data-ttu-id="aaaaa-178">`-ilike` 萬用字元 (不區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-178">`-ilike` case-insensitive wildcard</span></span>
- <span data-ttu-id="aaaaa-179">`-clike` 萬用字元 (區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-179">`-clike` case-sensitive wildcard</span></span>
- <span data-ttu-id="aaaaa-180">`-notlike` 萬用字元不相符 (不區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-180">`-notlike` case-insensitive wildcard not matched</span></span>
- <span data-ttu-id="aaaaa-181">`-inotlike` 萬用字元不相符 (不區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-181">`-inotlike` case-insensitive wildcard not matched</span></span>
- <span data-ttu-id="aaaaa-182">`-cnotlike` 萬用字元不相符 (區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-182">`-cnotlike` case-sensitive wildcard not matched</span></span>

### <a name="-match-regular-expression"></a><span data-ttu-id="aaaaa-183">-match 規則運算式</span><span class="sxs-lookup"><span data-stu-id="aaaaa-183">-match regular expression</span></span>

<span data-ttu-id="aaaaa-184">`-match` 運算子可讓您檢查字串以進行規則運算式比對。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-184">The `-match` operator allows you to check a string for a regular-expression-based match.</span></span> <span data-ttu-id="aaaaa-185">若萬用字元模式不夠靈活時，您就可以使用這個運算子。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-185">Use this when the wildcard patterns aren't flexible enough for you.</span></span>

```powershell
$value = 'S-ATX-SQL01'
if ( $value -match 'S-\w\w\w-SQL\d\d')
{
    # do something
}
```

<span data-ttu-id="aaaaa-186">Regex 模式預設會比對字串中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-186">A regex pattern matches anywhere in the string by default.</span></span> <span data-ttu-id="aaaaa-187">因此，您可以指定要比對的子字串，如下所示：</span><span class="sxs-lookup"><span data-stu-id="aaaaa-187">So you can specify a substring that you want matched like this:</span></span>

```powershell
$value = 'S-ATX-SQL01'
if ( $value -match 'SQL')
{
    # do something
}
```

<span data-ttu-id="aaaaa-188">Regex 是一種複雜的語言，很值得進一步了解。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-188">Regex is a complex language of its own and worth looking into.</span></span> <span data-ttu-id="aaaaa-189">我在另一篇文章有詳細說明 `-match` 以及 [使用 RegEx 的許多方式][]。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-189">I talk more about `-match` and [the many ways to use regex][] in another article.</span></span>

<span data-ttu-id="aaaaa-190">**變化：**</span><span class="sxs-lookup"><span data-stu-id="aaaaa-190">**Variations:**</span></span>

- <span data-ttu-id="aaaaa-191">`-match` Regex (不區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-191">`-match` case-insensitive regex</span></span>
- <span data-ttu-id="aaaaa-192">`-imatch` Regex (不區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-192">`-imatch` case-insensitive regex</span></span>
- <span data-ttu-id="aaaaa-193">`-cmatch` Regex (區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-193">`-cmatch` case-sensitive regex</span></span>
- <span data-ttu-id="aaaaa-194">`-notmatch` Regex 不相符 (不區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-194">`-notmatch` case-insensitive regex not matched</span></span>
- <span data-ttu-id="aaaaa-195">`-inotmatch` Regex 不相符 (不區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-195">`-inotmatch` case-insensitive regex not matched</span></span>
- <span data-ttu-id="aaaaa-196">`-cnotmatch` Regex 不相符 (區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-196">`-cnotmatch` case-sensitive regex not matched</span></span>

### <a name="-is-of-type"></a><span data-ttu-id="aaaaa-197">-is 類型</span><span class="sxs-lookup"><span data-stu-id="aaaaa-197">-is of type</span></span>

<span data-ttu-id="aaaaa-198">您可以使用 `-is` 運算子來檢查值的類型。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-198">You can check a value's type with the `-is` operator.</span></span>

```powershell
if ( $value -is [string] )
{
    # do something
}
```

<span data-ttu-id="aaaaa-199">若您使用類別或透過管線接受各種物件，則可以使用這個運算子。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-199">You may use this if you're working with classes or accepting various objects over the pipeline.</span></span> <span data-ttu-id="aaaaa-200">您可以輸入服務或服務名稱，</span><span class="sxs-lookup"><span data-stu-id="aaaaa-200">You could have either a service or a service name as your input.</span></span> <span data-ttu-id="aaaaa-201">然後檢查您是否有服務；若您只有名稱，請擷取服務。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-201">Then check to see if you have a service and fetch the service if you only have the name.</span></span>

```powershell
if ( $Service -isnot [System.ServiceProcess.ServiceController] )
{
    $Service = Get-Service -Name $Service
}
```

<span data-ttu-id="aaaaa-202">**變化：**</span><span class="sxs-lookup"><span data-stu-id="aaaaa-202">**Variations:**</span></span>

- <span data-ttu-id="aaaaa-203">`-is` 某種類型</span><span class="sxs-lookup"><span data-stu-id="aaaaa-203">`-is` of type</span></span>
- <span data-ttu-id="aaaaa-204">`-isnot` 非某種類型</span><span class="sxs-lookup"><span data-stu-id="aaaaa-204">`-isnot` not of type</span></span>

## <a name="collection-operators"></a><span data-ttu-id="aaaaa-205">集合運算子</span><span class="sxs-lookup"><span data-stu-id="aaaaa-205">Collection operators</span></span>

<span data-ttu-id="aaaaa-206">當您使用先前的運算子搭配單一值時，結果會是 `$true` 或 `$false`。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-206">When you use the previous operators with a single value, the result is `$true` or `$false`.</span></span> <span data-ttu-id="aaaaa-207">使用集合時的處理方式稍有不同。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-207">This is handled slightly differently when working with a collection.</span></span> <span data-ttu-id="aaaaa-208">運算子會評估集合中的每個項目，並傳回評估為 `$true` 的每一個值。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-208">Each item in the collection gets evaluated and the operator returns every value that evaluates to `$true`.</span></span>

```powershell
PS> 1,2,3,4 -eq 3
3
```

<span data-ttu-id="aaaaa-209">這仍可在 `if` 陳述式中正常運作。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-209">This still works correctly in a `if` statement.</span></span> <span data-ttu-id="aaaaa-210">因此，運算子會傳回值，而整個陳述式為 `$true`。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-210">So a value is returned by your operator, then the whole statement is `$true`.</span></span>

```powershell
$array = 1..6
if ( $array -gt 3 )
{
    # do something
}
```

<span data-ttu-id="aaaaa-211">但這裡有個魔鬼藏在細節中，我必須明確指出來。以這種方式使用 `-ne` 運算子時，很容易不小心回溯檢查邏輯。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-211">There's one small trap hiding in the details here that I need to point out. When using the `-ne` operator this way, it's easy to mistakenly look at the logic backwards.</span></span> <span data-ttu-id="aaaaa-212">若集合中的任何項目不符合您的值，則搭配使用 `-ne` 與集合時會傳回 `$true`。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-212">Using `-ne` with a collection returns `$true` if any item in the collection doesn't match your value.</span></span>

```powershell
PS> 1,2,3 -ne 4
1
2
3
```

<span data-ttu-id="aaaaa-213">這很容易讓人中招，所以我們可以使用 `-contains` 和 `-in` 運算子更有效率地處理這種情況。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-213">This may look like a clever trick, but we have operators `-contains` and `-in` that handle this more efficiently.</span></span> <span data-ttu-id="aaaaa-214">而且 `-notcontains` 會如您預期般執行。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-214">And `-notcontains` does what you expect.</span></span>

### <a name="-contains"></a><span data-ttu-id="aaaaa-215">-contains</span><span class="sxs-lookup"><span data-stu-id="aaaaa-215">-contains</span></span>

<span data-ttu-id="aaaaa-216">`-contains` 運算子會檢查集合中的值。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-216">The `-contains` operator checks the collection for your value.</span></span> <span data-ttu-id="aaaaa-217">一旦找到相符的結果，就會傳回 `$true`。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-217">As soon as it finds a match, it returns `$true`.</span></span>

```powershell
$array = 1..6
if ( $array -contains 3 )
{
    # do something
}
```

<span data-ttu-id="aaaaa-218">這個慣用方法可查看集合是否包含您的值。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-218">This is the preferred way to see if a collection contains your value.</span></span> <span data-ttu-id="aaaaa-219">若您使用 `Where-Object` (或 `-eq`)，則每次都會跑完整份清單，速度會明顯變慢。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-219">Using `Where-Object` (or `-eq`) walks the entire list every time and is significantly slower.</span></span>

<span data-ttu-id="aaaaa-220">**變化：**</span><span class="sxs-lookup"><span data-stu-id="aaaaa-220">**Variations:**</span></span>

- <span data-ttu-id="aaaaa-221">`-contains` 相符 (不區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-221">`-contains` case-insensitive match</span></span>
- <span data-ttu-id="aaaaa-222">`-icontains` 相符 (不區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-222">`-icontains` case-insensitive match</span></span>
- <span data-ttu-id="aaaaa-223">`-ccontains` 相符 (區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-223">`-ccontains` case-sensitive match</span></span>
- <span data-ttu-id="aaaaa-224">`-notcontains` 不相符 (不區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-224">`-notcontains` case-insensitive not matched</span></span>
- <span data-ttu-id="aaaaa-225">`-inotcontains` 不相符 (不區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-225">`-inotcontains` case-insensitive not matched</span></span>
- <span data-ttu-id="aaaaa-226">`-cnotcontains` 不相符 (區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-226">`-cnotcontains` case-sensitive not matched</span></span>

### <a name="-in"></a><span data-ttu-id="aaaaa-227">-in</span><span class="sxs-lookup"><span data-stu-id="aaaaa-227">-in</span></span>

<span data-ttu-id="aaaaa-228">`-in` 運算子跟 `-contains` 運算子一樣，差別是其集合在右側。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-228">The `-in` operator is just like the `-contains` operator except the collection is on the right-hand side.</span></span>

```powershell
$array = 1..6
if ( 3 -in $array )
{
    # do something
}
```

<span data-ttu-id="aaaaa-229">**變化：**</span><span class="sxs-lookup"><span data-stu-id="aaaaa-229">**Variations:**</span></span>

- <span data-ttu-id="aaaaa-230">`-in` 相符 (不區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-230">`-in` case-insensitive match</span></span>
- <span data-ttu-id="aaaaa-231">`-iin` 相符 (不區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-231">`-iin` case-insensitive match</span></span>
- <span data-ttu-id="aaaaa-232">`-cin` 相符 (區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-232">`-cin` case-sensitive match</span></span>
- <span data-ttu-id="aaaaa-233">`-notin` 不相符 (不區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-233">`-notin` case-insensitive not matched</span></span>
- <span data-ttu-id="aaaaa-234">`-inotin` 不相符 (不區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-234">`-inotin` case-insensitive not matched</span></span>
- <span data-ttu-id="aaaaa-235">`-cnotin` 不相符 (區分大小寫)</span><span class="sxs-lookup"><span data-stu-id="aaaaa-235">`-cnotin` case-sensitive not matched</span></span>

## <a name="logical-operators"></a><span data-ttu-id="aaaaa-236">邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="aaaaa-236">Logical operators</span></span>

<span data-ttu-id="aaaaa-237">邏輯運算子可用來反轉或結合其他運算式。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-237">Logical operators are used to invert or combine other expressions.</span></span>

### <a name="-not"></a><span data-ttu-id="aaaaa-238">-not</span><span class="sxs-lookup"><span data-stu-id="aaaaa-238">-not</span></span>

<span data-ttu-id="aaaaa-239">`-not` 運算子會將運算式從 `$false` 翻轉為 `$true`，或從 `$true` 翻轉為 `$false`。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-239">The `-not` operator flips an expression from `$false` to `$true` or from `$true` to `$false`.</span></span> <span data-ttu-id="aaaaa-240">下列是我們想要在 `Test-Path` 為 `$false` 時執行動作的範例。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-240">Here is an example where we want to perform an action when `Test-Path` is `$false`.</span></span>

```powershell
if ( -not ( Test-Path -Path $path ) )
```

<span data-ttu-id="aaaaa-241">我們剛提到的大部分運算子都有變化，因此您不需要使用 `-not` 運算子，</span><span class="sxs-lookup"><span data-stu-id="aaaaa-241">Most of the operators we talked about do have a variation where you do not need to use the `-not` operator.</span></span> <span data-ttu-id="aaaaa-242">但這個運算子仍有派上用場的時候。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-242">But there are still times it is useful.</span></span>

### <a name="-operator"></a><span data-ttu-id="aaaaa-243">!</span><span class="sxs-lookup"><span data-stu-id="aaaaa-243">!</span></span> <span data-ttu-id="aaaaa-244">! 運算子之後</span><span class="sxs-lookup"><span data-stu-id="aaaaa-244">operator</span></span>

<span data-ttu-id="aaaaa-245">您可以使用 `!` 作為 `-not` 的別名。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-245">You can use `!` as an alias for `-not`.</span></span>

```powershell
if ( -not $value ){}
if ( !$value ){}
```

<span data-ttu-id="aaaaa-246">慣用 C# 等其他語言的使用者較常使用 `!`。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-246">You may see `!` used more by people that come from another languages like C#.</span></span> <span data-ttu-id="aaaaa-247">我偏好把整個運算子打出來，不然我在快速查看指令碼時很容易漏看。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-247">I prefer to type it out because I find it hard to see when quickly looking at my scripts.</span></span>

### <a name="-and"></a><span data-ttu-id="aaaaa-248">-and</span><span class="sxs-lookup"><span data-stu-id="aaaaa-248">-and</span></span>

<span data-ttu-id="aaaaa-249">您可以將運算式與 `-and` 運算子結合。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-249">You can combine expressions with the `-and` operator.</span></span> <span data-ttu-id="aaaaa-250">當您這麼做時，兩側都必須為 `$true`，整個運算式才能為 `$true`。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-250">When you do that, both sides need to be `$true` for the whole expression to be `$true`.</span></span>

```powershell
if ( ($age -gt 13) -and ($age -lt 55) )
```

<span data-ttu-id="aaaaa-251">在該範例中，`$age` 左側必須大於等於 13 歲，右側則小於 55 歲。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-251">In that example, `$age` must be 13 or older for the left side and less than 55 for the right side.</span></span> <span data-ttu-id="aaaaa-252">為了讓這個範例更一目了然，我新增了額外的括弧；只要運算式很精簡，您就可以自行選擇是否使用這些括弧。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-252">I added extra parentheses to make it clearer in that example but they're optional as long as the expression is simple.</span></span> <span data-ttu-id="aaaaa-253">以下是不使用括弧的相同範例。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-253">Here is the same example without them.</span></span>

```powershell
if ( $age -gt 13 -and $age -lt 55 )
```

<span data-ttu-id="aaaaa-254">評估會由左至右進行。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-254">Evaluation happens from left to right.</span></span> <span data-ttu-id="aaaaa-255">若第一個項目評估為 `$false`，運算式就會提早結束，而無法執行正確的比較。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-255">If the first item evaluates to `$false`, it exits early and doesn't perform the right comparison.</span></span> <span data-ttu-id="aaaaa-256">當您需要先確定值存在，然後再使用該值時，這會很方便。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-256">This is handy when you need to make sure a value exists before you use it.</span></span> <span data-ttu-id="aaaaa-257">例如，若您提供 `$null` 路徑給 `Test-Path`，就會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-257">For example, `Test-Path` throws an error if you give it a `$null` path.</span></span>

```powershell
if ( $null -ne $path -and (Test-Path -Path $path) )
```

### <a name="-or"></a><span data-ttu-id="aaaaa-258">-or</span><span class="sxs-lookup"><span data-stu-id="aaaaa-258">-or</span></span>

<span data-ttu-id="aaaaa-259">`-or` 可讓您指定兩個運算式，並在其中一個是 `$true` 時傳回 `$true`。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-259">The `-or` allows for you to specify two expressions and returns `$true` if either one of them is `$true`.</span></span>

```powershell
if ( $age -le 13 -or $age -ge 55 )
```

<span data-ttu-id="aaaaa-260">如同使用 `-and` 運算子一樣，評估會由左至右進行。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-260">Just like with the `-and` operator, the evaluation happens from left to right.</span></span> <span data-ttu-id="aaaaa-261">差異在於，若第一個部分為 `$true`，整個陳述式就是 `$true`；運算式的其餘部分都不會再處理。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-261">Except that if the first part is `$true`, then the whole statement is `$true` and it doesn't process the rest of the expression.</span></span>

<span data-ttu-id="aaaaa-262">另請注意這些運算子的語法運作方式：</span><span class="sxs-lookup"><span data-stu-id="aaaaa-262">Also make note of how the syntax works for these operators.</span></span> <span data-ttu-id="aaaaa-263">您需要兩個不同的運算式。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-263">You need two separate expressions.</span></span> <span data-ttu-id="aaaaa-264">我看過有些使用者寫出類似 `$value -eq 5 -or 6` 的運算式，而沒發現自己犯了錯。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-264">I have seen users try to do something like this `$value -eq 5 -or 6` without realizing their mistake.</span></span>

### <a name="-xor-exclusive-or"></a><span data-ttu-id="aaaaa-265">-xor 互斥 or</span><span class="sxs-lookup"><span data-stu-id="aaaaa-265">-xor exclusive or</span></span>

<span data-ttu-id="aaaaa-266">這個運算子比較不一樣。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-266">This one is a little unusual.</span></span> <span data-ttu-id="aaaaa-267">`-xor` 只允許一個運算式評估為 `$true`。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-267">`-xor` allows only one expression to evaluate to `$true`.</span></span> <span data-ttu-id="aaaaa-268">因此，若這兩個項目都是 `$false`，或這兩個項目都是 `$true`，則整個運算式都是 `$false`。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-268">So if both items are `$false` or both items are `$true`, then the whole expression is `$false`.</span></span> <span data-ttu-id="aaaaa-269">換句話說，只有當運算式的結果不同時，運算式才是 `$true`。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-269">Another way to look at this is the expression is only `$true` when the results of the expression are different.</span></span>

<span data-ttu-id="aaaaa-270">大概沒什麼人會想用這個邏輯運算子，連我都想不出有什麼好的使用範例可以分享。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-270">It's rare that anyone would ever use this logical operator and I can't think up a good example as to why I would ever use it.</span></span>

## <a name="bitwise-operators"></a><span data-ttu-id="aaaaa-271">位元運算子</span><span class="sxs-lookup"><span data-stu-id="aaaaa-271">Bitwise operators</span></span>

<span data-ttu-id="aaaaa-272">位元運算子會在值當中的位元上執行計算，並產生新的值作為結果。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-272">Bitwise operators perform calculations on the bits within the values and produce a new value as the result.</span></span> <span data-ttu-id="aaaaa-273">這篇文章不會教大家[位元運算子][]，但以下為清單。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-273">Teaching [bitwise operators][] is beyond the scope of this article, but here is the list the them.</span></span>

- <span data-ttu-id="aaaaa-274">`-band` 二進位 AND</span><span class="sxs-lookup"><span data-stu-id="aaaaa-274">`-band` binary AND</span></span>
- <span data-ttu-id="aaaaa-275">`-bor` 二進位 OR</span><span class="sxs-lookup"><span data-stu-id="aaaaa-275">`-bor` binary OR</span></span>
- <span data-ttu-id="aaaaa-276">`-bxor` 二進位互斥 OR</span><span class="sxs-lookup"><span data-stu-id="aaaaa-276">`-bxor` binary exclusive OR</span></span>
- <span data-ttu-id="aaaaa-277">`-bnot` 二進位 NOT</span><span class="sxs-lookup"><span data-stu-id="aaaaa-277">`-bnot` binary NOT</span></span>
- <span data-ttu-id="aaaaa-278">`-shl` 左移</span><span class="sxs-lookup"><span data-stu-id="aaaaa-278">`-shl` shift left</span></span>
- <span data-ttu-id="aaaaa-279">`-shr` 右移</span><span class="sxs-lookup"><span data-stu-id="aaaaa-279">`-shr` shift right</span></span>

## <a name="powershell-expressions"></a><span data-ttu-id="aaaaa-280">PowerShell 運算式</span><span class="sxs-lookup"><span data-stu-id="aaaaa-280">PowerShell expressions</span></span>

<span data-ttu-id="aaaaa-281">我們可以在條件陳述式中使用一般 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-281">We can use normal PowerShell inside the condition statement.</span></span>

```powershell
if ( Test-Path -Path $Path )
```

<span data-ttu-id="aaaaa-282">`Test-Path` 會在執行時傳回 `$true` 或 `$false`。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-282">`Test-Path` returns `$true` or `$false` when it executes.</span></span> <span data-ttu-id="aaaaa-283">這也適用於會傳回其他值的命令。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-283">This also applies to commands that return other values.</span></span>

```powershell
if ( Get-Process Notepad* )
```

<span data-ttu-id="aaaaa-284">若有傳回處理序，運算式會評估為 `$true`；若什麼都沒有，則為 `$false`。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-284">It evaluates to `$true` if there's a returned process and `$false` if there'sn'thing.</span></span> <span data-ttu-id="aaaaa-285">使用管線運算式或其他 PowerShell 陳述式也完全有效，如下所示：</span><span class="sxs-lookup"><span data-stu-id="aaaaa-285">It's perfectly valid to use pipeline expressions or other PowerShell statements like this:</span></span>

```powershell
if ( Get-Process | Where Name -eq Notepad )
```

<span data-ttu-id="aaaaa-286">這些運算式可以使用 `-and` 和 `-or` 運算子彼此結合，但您可能必須使用括弧將其分割成子運算式。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-286">These expressions can be combined with each other with the `-and` and `-or` operators, but you may have to use parenthesis to break them into subexpressions.</span></span>

```powershell
if ( (Get-Process) -and (Get-Service) )
```

### <a name="checking-for-null"></a><span data-ttu-id="aaaaa-287">檢查 $null</span><span class="sxs-lookup"><span data-stu-id="aaaaa-287">Checking for $null</span></span>

<span data-ttu-id="aaaaa-288">`if` 陳述式會將無結果或 `$null` 值評估為 `$false`。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-288">Having a no result or a `$null` value evaluates to `$false` in the `if` statement.</span></span> <span data-ttu-id="aaaaa-289">如要特別檢查 `$null`，最佳做法是將 `$null` 放在左側。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-289">When checking specifically for `$null`, it's a best practice to place the `$null` on the left-hand side.</span></span>

```powershell
if ( $null -eq $value )
```

<span data-ttu-id="aaaaa-290">在 PowerShell 中處理 `$null` 值時，有幾個細微的差異。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-290">There are quite a few nuances when dealing with `$null` values in PowerShell.</span></span> <span data-ttu-id="aaaaa-291">若您想深入了解，可以參閱我寫的 [$null 的完整說明][]一文。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-291">If you're interested in diving deeper, I have an article about [everything you wanted to know about $null][].</span></span>

### <a name="variable-assignment"></a><span data-ttu-id="aaaaa-292">變數指派</span><span class="sxs-lookup"><span data-stu-id="aaaaa-292">Variable assignment</span></span>

<span data-ttu-id="aaaaa-293">我差點忘了要納入這個項目，幸好 [Prasoon Karunan V][] 提醒我。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-293">I almost forgot to add this one until [Prasoon Karunan V][] reminded me of it.</span></span>

```powershell
if ($process=Get-Process notepad -ErrorAction ignore) {$process} else {$false}
```

<span data-ttu-id="aaaaa-294">一般來說，當您指派值給變數時，並不會將值傳遞給管線或主控台。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-294">Normally when you assign a value to a variable, the value isn't passed onto the pipeline or console.</span></span> <span data-ttu-id="aaaaa-295">但當您在子運算式中指派變數時，變數卻會傳遞給管線。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-295">When you do a variable assignment in a sub expression, it does get passed on to the pipeline.</span></span>

```powershell
PS> $first = 1
PS> ($second = 2)
2
```

<span data-ttu-id="aaaaa-296">您知道為什麼 `$first` 指派沒有輸出，而 `$second` 指派卻有嗎？</span><span class="sxs-lookup"><span data-stu-id="aaaaa-296">See how the `$first` assignment has no output and the `$second` assignment does?</span></span> <span data-ttu-id="aaaaa-297">在 `if` 陳述式中進行指派時，其執行方式就如同上述的 `$second` 指派。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-297">When an assignment is done in an `if` statement, it executes just like the `$second` assignment above.</span></span> <span data-ttu-id="aaaaa-298">以下是簡潔的使用範例：</span><span class="sxs-lookup"><span data-stu-id="aaaaa-298">Here is a clean example on how you could use it:</span></span>

```powershell
if ( $process = Get-Process Notepad* )
{
    $process | Stop-Process
}
```

<span data-ttu-id="aaaaa-299">若將值指派給 `$process`，陳述式為 `$true`，且 `$process` 會停止。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-299">If `$process` gets assigned a value, then the statement is `$true` and `$process` gets stopped.</span></span>

<span data-ttu-id="aaaaa-300">請注意不要將這個項目與 `-eq` 混淆，因為這不是相等檢查。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-300">Make sure you don't confuse this with `-eq` because this isn't an equality check.</span></span> <span data-ttu-id="aaaaa-301">這項功能比較含糊不清，因此大多數人都做不到。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-301">This is a more obscure feature that most people don't realize works this way.</span></span>

## <a name="alternate-execution-path"></a><span data-ttu-id="aaaaa-302">替代執行路徑</span><span class="sxs-lookup"><span data-stu-id="aaaaa-302">Alternate execution path</span></span>

<span data-ttu-id="aaaaa-303">`if` 陳述式不只可讓您指定陳述式為 `$true` 時的動作，也可讓您指定陳述式為 `$false` 時的動作。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-303">The `if` statement allows you to specify an action for not only when the statement is `$true`, but also for when it's `$false`.</span></span> <span data-ttu-id="aaaaa-304">這時，`else` 陳述式就派上用場了。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-304">This is where the `else` statement comes into play.</span></span>

### <a name="else"></a><span data-ttu-id="aaaaa-305">else</span><span class="sxs-lookup"><span data-stu-id="aaaaa-305">else</span></span>

<span data-ttu-id="aaaaa-306">使用 `else` 陳述式時，其一律是 `if` 陳述式的最後一部分。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-306">The `else` statement is always the last part of the `if` statement when used.</span></span>

```powershell
if ( Test-Path -Path $Path -PathType Leaf )
{
    Move-Item -Path $Path -Destination $archivePath
}
else
{
    Write-Warning "$path doesn't exist or isn't a file."
}
```

<span data-ttu-id="aaaaa-307">在此範例中，我們要檢查 `$path` 以確定其為一個檔案。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-307">In this example, we check the `$path` to make sure it's a file.</span></span> <span data-ttu-id="aaaaa-308">若找到檔案，我們就將其移動位置。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-308">If we find the file, we move it.</span></span> <span data-ttu-id="aaaaa-309">若找不到，我們就撰寫一則警告。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-309">If not, we write a warning.</span></span> <span data-ttu-id="aaaaa-310">這種類型的分支邏輯相當普遍。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-310">This type of branching logic is very common.</span></span>

### <a name="nested-if"></a><span data-ttu-id="aaaaa-311">巢狀 if</span><span class="sxs-lookup"><span data-stu-id="aaaaa-311">Nested if</span></span>

<span data-ttu-id="aaaaa-312">`if` 和 `else` 陳述式接受指令碼區塊，因此我們可以將任何 PowerShell 命令放在其中，包括其他 `if` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-312">The `if` and `else` statements take a script block, so we can place any PowerShell command inside them, including another `if` statement.</span></span> <span data-ttu-id="aaaaa-313">這可讓您使用更複雜的邏輯。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-313">This allows you to make use of much more complicated logic.</span></span>

```powershell
if ( Test-Path -Path $Path -PathType Leaf )
{
    Move-Item -Path $Path -Destination $archivePath
}
else
{
    if ( Test-Path -Path $Path )
    {
        Write-Warning "A file was required but a directory was found instead."
    }
    else
    {
        Write-Warning "$path could not be found."
    }
}
```

<span data-ttu-id="aaaaa-314">在此範例中，我們會先測試理想路徑，然後對其採取動作。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-314">In this example, we test the happy path first and then take action on it.</span></span> <span data-ttu-id="aaaaa-315">若失敗，我們會進行其他檢查，並提供詳細資訊給使用者。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-315">If that fails, we do another check and to provide more detailed information to the user.</span></span>

### <a name="elseif"></a><span data-ttu-id="aaaaa-316">elseif</span><span class="sxs-lookup"><span data-stu-id="aaaaa-316">elseif</span></span>

<span data-ttu-id="aaaaa-317">我們的作業並不限於單一條件式檢查，</span><span class="sxs-lookup"><span data-stu-id="aaaaa-317">We aren't limited to just a single conditional check.</span></span> <span data-ttu-id="aaaaa-318">因此我們可以將 `if` 和 `else` 陳述式鏈結在一起，而不使用 `elseif` 陳述式來進行巢狀。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-318">We can chain `if` and `else` statements together instead of nesting them by using the `elseif` statement.</span></span>

```powershell
if ( Test-Path -Path $Path -PathType Leaf )
{
    Move-Item -Path $Path -Destination $archivePath
}
elseif ( Test-Path -Path $Path )
{
    Write-Warning "A file was required but a directory was found instead."
}
else
{
    Write-Warning "$path could not be found."
}
```

<span data-ttu-id="aaaaa-319">執行順序是由上到下。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-319">The execution happens from the top to the bottom.</span></span> <span data-ttu-id="aaaaa-320">因此會評估最上面的 `if` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-320">The top `if` statement is evaluated first.</span></span> <span data-ttu-id="aaaaa-321">若是 `$false`，則會向下移動到清單的下一個 `elseif` 或 `else`。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-321">If that is `$false`, then it moves down to the next `elseif` or `else` in the list.</span></span> <span data-ttu-id="aaaaa-322">若沒有其他陳述式傳回 `$true`，最後一個 `else` 就是會採取的預設動作。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-322">That last `else` is the default action to take if none of the others return `$true`.</span></span>

### <a name="switch"></a><span data-ttu-id="aaaaa-323">參數</span><span class="sxs-lookup"><span data-stu-id="aaaaa-323">switch</span></span>

<span data-ttu-id="aaaaa-324">現在，我要來說明 `switch` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-324">At this point, I need to mention the `switch` statement.</span></span> <span data-ttu-id="aaaaa-325">此陳述式提供的替代語法可多次比較某個值。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-325">It provides an alternate syntax for doing multiple comparisons with a value.</span></span> <span data-ttu-id="aaaaa-326">使用 `switch` 時，您可以指定運算式，而結果會與數個不同的值進行比較。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-326">With the `switch`, you specify an expression and that result gets compared with several different values.</span></span> <span data-ttu-id="aaaaa-327">若其中一個值相符，則會執行相符的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-327">If one of those values match, the matching code block is executed.</span></span> <span data-ttu-id="aaaaa-328">請看一下這個範例：</span><span class="sxs-lookup"><span data-stu-id="aaaaa-328">Take a look at this example:</span></span>

```powershell
$itemType = 'Role'
switch ( $itemType )
{
    'Component'
    {
        'is a component'
    }
    'Role'
    {
        'is a role'
    }
    'Location'
    {
        'is a location'
    }
}
```

<span data-ttu-id="aaaaa-329">有三個可能的值符合 `$itemType`。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-329">There three possible values that can match the `$itemType`.</span></span> <span data-ttu-id="aaaaa-330">在此情況下，其會與 `Role` 進行比對。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-330">In this case, it matches with `Role`.</span></span> <span data-ttu-id="aaaaa-331">這只是一個簡單的範例，讓您看一下 `switch` 運算子的用法。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-331">I used a simple example just to give you some exposure to the `switch` operator.</span></span> <span data-ttu-id="aaaaa-332">我在另一篇 [Switch 陳述式的完整說明][]文章中會專門介紹。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-332">I talk more about [everything you ever wanted to know about the switch statement][] in another article.</span></span>

## <a name="pipeline"></a><span data-ttu-id="aaaaa-333">管線</span><span class="sxs-lookup"><span data-stu-id="aaaaa-333">Pipeline</span></span>

<span data-ttu-id="aaaaa-334">管線是 PowerShell 的獨特重要功能。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-334">The pipeline is a unique and important feature of PowerShell.</span></span> <span data-ttu-id="aaaaa-335">未隱藏或未指派給變數的任何值都會放在管線中。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-335">Any value that isn't suppressed or assigned to a variable gets placed in the pipeline.</span></span> <span data-ttu-id="aaaaa-336">`if` 提供的方法，可讓我們透過較隱密的方式利用管線。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-336">The `if` provides us a way to take advantage of the pipeline in a way that isn't always obvious.</span></span>

```powershell
$discount = if ( $age -ge 55 )
{
    Get-SeniorDiscount
}
elseif ( $age -le 13 )
{
    Get-ChildDiscount
}
else
{
    0.00
}
```

<span data-ttu-id="aaaaa-337">每個指令碼區塊都會將結果、命令或值放入管線中，</span><span class="sxs-lookup"><span data-stu-id="aaaaa-337">Each script block is placing the results the commands or the value into the pipeline.</span></span> <span data-ttu-id="aaaaa-338">然後再將 `if` 陳述式的結果指派給 `$discount` 變數。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-338">Then we assign the result of the `if` statement to the `$discount` variable.</span></span> <span data-ttu-id="aaaaa-339">此範例可以輕鬆地將這些值直接指派給每個指令碼區塊中的 `$discount` 變數。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-339">That example could have just as easily assigned those values to the `$discount` variable directly in each scriptblock.</span></span> <span data-ttu-id="aaaaa-340">說實話，我不常這樣搭配使用 `if` 陳述式，但我最近確實有這麼一個使用範例。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-340">I can't say that I use this with the `if` statement often, but I do have an example where I used this recently.</span></span>

### <a name="array-inline"></a><span data-ttu-id="aaaaa-341">陣列內嵌</span><span class="sxs-lookup"><span data-stu-id="aaaaa-341">Array inline</span></span>

<span data-ttu-id="aaaaa-342">假設我有個名為 [Invoke-SnowSql][] 的函式，其會使用數個命令列引數來啟動可執行檔。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-342">I have a function called [Invoke-SnowSql][] that launches an executable with several command-line arguments.</span></span> <span data-ttu-id="aaaaa-343">以下是該函式的片段，其中我會建置引數陣列。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-343">Here is a clip from that function where I build the array of arguments.</span></span>

```powershell
$snowSqlParam = @(
    '--accountname', $Endpoint
    '--username', $Credential.UserName
    '--option', 'exit_on_error=true'
    '--option', 'output_format=csv'
    '--option', 'friendly=false'
    '--option', 'timing=false'
    if ($Debug)
    {
        '--option', 'log_level=DEBUG'
    }
    if ($Path)
    {
        '--filename', $Path
    }
    else
    {
        '--query', $singleLineQuery
    }
)
```

<span data-ttu-id="aaaaa-344">`$Debug` 和 `$Path` 變數是終端使用者提供的函式參數。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-344">The `$Debug` and `$Path` variables are parameters on the function that are provided by the end user.</span></span>
<span data-ttu-id="aaaaa-345">在陣列的初始化中，我以內嵌方式評估這些項目。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-345">I evaluate them inline inside the initialization of my array.</span></span> <span data-ttu-id="aaaaa-346">若 `$Debug` 為 true，則這些值會落在正確位置的 `$snowSqlParam` 中。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-346">If `$Debug` is true, then those values fall into the `$snowSqlParam` in the correct place.</span></span> <span data-ttu-id="aaaaa-347">`$Path` 變數也是如此。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-347">Same holds true for the `$Path` variable.</span></span>

## <a name="simplify-complex-operations"></a><span data-ttu-id="aaaaa-348">簡化複雜的作業</span><span class="sxs-lookup"><span data-stu-id="aaaaa-348">Simplify complex operations</span></span>

<span data-ttu-id="aaaaa-349">有時候，當要檢查的比較項目太多時，`If` 陳述式會從畫面右側一路跑到底。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-349">It's inevitable that you run into a situation that has way too many comparisons to check and your `If` statement scrolls way off the right side of the screen.</span></span>

```powershell
$user = Get-ADUser -Identity $UserName
if ( $null -ne $user -and $user.Department -eq 'Finance' -and $user.Title -match 'Senior' -and $user.HomeDrive -notlike '\\server\*' )
{
    # Do Something
}
```

<span data-ttu-id="aaaaa-350">這會導致難以閱讀，您也更容易犯錯。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-350">They can be hard to read and that make you more prone to make mistakes.</span></span> <span data-ttu-id="aaaaa-351">我們可以用幾個方法來改善情況。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-351">There are a few things we can do about that.</span></span>

### <a name="line-continuation"></a><span data-ttu-id="aaaaa-352">行接續</span><span class="sxs-lookup"><span data-stu-id="aaaaa-352">Line continuation</span></span>

<span data-ttu-id="aaaaa-353">PowerShell 中有一些運算子可讓您將命令換行。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-353">There some operators in PowerShell that let you wrap you command to the next line.</span></span> <span data-ttu-id="aaaaa-354">若您想要將運算式分成多行，就非常適合使用 `-and` 和 `-or` 邏輯運算子。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-354">The logical operators `-and` and `-or` are good operators to use if you want to break your expression into multiple lines.</span></span>

```powershell
if ($null -ne $user -and
    $user.Department -eq 'Finance' -and
    $user.Title -match 'Senior' -and
    $user.HomeDrive -notlike '\\server\*'
)
{
    # Do Something
}
```

<span data-ttu-id="aaaaa-355">雖然要看的東西還是很多，但將每個項目分開獨立一行，視覺感完全不一樣。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-355">There's still a lot going on there, but placing each piece on its own line makes a big difference.</span></span>
<span data-ttu-id="aaaaa-356">一般來說，當我進行兩個以上的項目比較時，或必須向右捲動才能讀取任何邏輯時，我都會使用這個方法。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-356">I generally use this when I get more than two comparisons or if I have to scroll to the right to read any of the logic.</span></span>

### <a name="pre-calculating-results"></a><span data-ttu-id="aaaaa-357">預先計算結果</span><span class="sxs-lookup"><span data-stu-id="aaaaa-357">Pre-calculating results</span></span>

<span data-ttu-id="aaaaa-358">我們可將上面的陳述式從 `if` 陳述式中獨立出來，並只檢查結果。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-358">We can take that statement out of the `if` statement and only check the result.</span></span>

```powershell
$needsSecureHomeDrive = $null -ne $user -and
    $user.Department -eq 'Finance' -and
    $user.Title -match 'Senior' -and
    $user.HomeDrive -notlike '\\server\*'

if ( $needsSecureHomeDrive )
{
    # Do Something
}
```

<span data-ttu-id="aaaaa-359">這種方式比上一個範例更加一目了然。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-359">This just feels much cleaner than the previous example.</span></span> <span data-ttu-id="aaaaa-360">您也可以使用變數名稱來明確說明要檢查的內容。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-360">You also are given an opportunity to use a variable name that explains what it's that you're really checking.</span></span> <span data-ttu-id="aaaaa-361">這也是一個用來儲存非必要註解的自編程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-361">This is also and example of self-documenting code that saves unnecessary comments.</span></span>

### <a name="multiple-if-statements"></a><span data-ttu-id="aaaaa-362">多個 if 陳述式</span><span class="sxs-lookup"><span data-stu-id="aaaaa-362">Multiple if statements</span></span>

<span data-ttu-id="aaaaa-363">我們可以範例分成多個陳述式，並逐一檢查。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-363">We can break this up into multiple statements and check them one at a time.</span></span> <span data-ttu-id="aaaaa-364">在這個案例中，我們會使用旗標或追蹤變數來合併結果。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-364">In this case, we use a flag or a tracking variable to combine the results.</span></span>

```powershell

$skipUser = $false

if( $null -eq $user )
{
    $skipUser = $true
}

if( $user.Department -ne 'Finance' )
{
    Write-Verbose "isn't in Finance department"
    $skipUser = $true
}

if( $user.Title -match 'Senior' )
{
    Write-Verbose "Doesn't have Senior title"
    $skipUser = $true
}

if( $user.HomeDrive -like '\\server\*' )
{
    Write-Verbose "Home drive already configured"
    $skipUser = $true
}

if ( -not $skipUser )
{
    # do something
}
```

<span data-ttu-id="aaaaa-365">我必須反轉邏輯，讓旗標邏輯能夠正確運作。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-365">I did have to invert the logic to make the flag logic work correctly.</span></span> <span data-ttu-id="aaaaa-366">每項評估都是個別的 `if` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-366">Each evaluation is an individual `if` statement.</span></span> <span data-ttu-id="aaaaa-367">這麼做的優點是您可以在偵錯時明確看出邏輯的運作方式。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-367">The advantage of this is that when you're debugging, you can tell exactly what the logic is doing.</span></span> <span data-ttu-id="aaaaa-368">我也可以同時提升詳細程度。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-368">I was able to add much better verbosity at the same time.</span></span>

<span data-ttu-id="aaaaa-369">這種做法有個明顯的缺點，就是要寫的程式碼太多了。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-369">The obvious downside is that it's so much more code to write.</span></span> <span data-ttu-id="aaaaa-370">若您把程式碼用逐行邏輯呈現，並分解成 25 行或更多行，看起來就比較複雜。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-370">The code is more complex to look at as it takes a single line of logic and explodes it into 25 or more lines.</span></span>

### <a name="using-functions"></a><span data-ttu-id="aaaaa-371">使用函式</span><span class="sxs-lookup"><span data-stu-id="aaaaa-371">Using functions</span></span>

<span data-ttu-id="aaaaa-372">我們也可以將所有驗證邏輯移至函式中。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-372">We can also move all that validation logic into a function.</span></span> <span data-ttu-id="aaaaa-373">這樣看起來就清爽多了。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-373">Look at how clean this looks at a glance.</span></span>

```powershell
if ( Test-SecureDriveConfiguration -ADUser $user )
{
    # do something
}
```

<span data-ttu-id="aaaaa-374">雖然您仍必須建立函式來進行驗證，但這麼做讓這段程式碼更易於使用，</span><span class="sxs-lookup"><span data-stu-id="aaaaa-374">You still have to create the function to do the validation, but it makes this code much easier to work with.</span></span> <span data-ttu-id="aaaaa-375">您也可以更輕鬆測試這段程式碼。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-375">It makes this code easier to test.</span></span> <span data-ttu-id="aaaaa-376">在測試中，您可以模擬對 `Test-ADDriveConfiguration` 的呼叫，並只需要對此函式進行兩項測試。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-376">In your tests, you can mock the call to `Test-ADDriveConfiguration` and you only need two tests for this function.</span></span> <span data-ttu-id="aaaaa-377">其中一個會傳回 `$true`，另一個則傳回 `$false`。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-377">One where it returns `$true` and one where it returns `$false`.</span></span> <span data-ttu-id="aaaaa-378">另一個函式很小，因此更容易測試。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-378">Testing the other function is simpler because it's so small.</span></span>

<span data-ttu-id="aaaaa-379">該函式的主體仍可以是我們一開始使用的一行程式碼，或是我們在上一節中使用的分解邏輯。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-379">The body of that function could still be that one-liner we started with or the exploded logic that we used in the last section.</span></span> <span data-ttu-id="aaaaa-380">兩種案例都適用於這種做法，並可讓您稍後更輕鬆地變更該實作。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-380">This works well for both scenarios and allows you to easily change that implementation later.</span></span>

## <a name="error-handling"></a><span data-ttu-id="aaaaa-381">錯誤處理</span><span class="sxs-lookup"><span data-stu-id="aaaaa-381">Error handling</span></span>

<span data-ttu-id="aaaaa-382">`if` 陳述式的其中一個重要用法是在發生錯誤之前，先檢查是否有錯誤條件。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-382">One important use of the `if` statement is to check for error conditions before you run into errors.</span></span> <span data-ttu-id="aaaaa-383">舉例來說，我們可以在嘗試建立資料夾之前，先檢查資料夾是否已經存在。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-383">A good example is to check if a folder already exists before you try to create it.</span></span>

```powershell
if ( -not (Test-Path -Path $folder) )
{
    New-Item -Type Directory -Path $folder
}
```

<span data-ttu-id="aaaaa-384">我必須提醒一點，如果例外狀況是您能預期得到的，就不是真正的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-384">I like to say that if you expect an exception to happen, then it's not really an exception.</span></span> <span data-ttu-id="aaaaa-385">因此，請檢查您的值，並盡量驗證條件。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-385">So check your values and validate your conditions where you can.</span></span>

<span data-ttu-id="aaaaa-386">若您想要深入了解實際的例外狀況處理方式，可以參閱我寫的[例外狀況的完整說明][]一文。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-386">If you want to dive a little more into actual exception handling, I have an article on [everything you ever wanted to know about exceptions][].</span></span>

## <a name="final-words"></a><span data-ttu-id="aaaaa-387">結論</span><span class="sxs-lookup"><span data-stu-id="aaaaa-387">Final words</span></span>

<span data-ttu-id="aaaaa-388">`if` 陳述式是非常簡單的陳述式，但卻是 PowerShell 的基礎。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-388">The `if` statement is such a simple statement but is a fundamental piece of PowerShell.</span></span> <span data-ttu-id="aaaaa-389">幾乎在您撰寫的每個指令碼中，都會多次使用這個陳述式。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-389">You will find yourself using this multiple times in almost every script you write.</span></span> <span data-ttu-id="aaaaa-390">希望您對相關內容有更清楚的了解。</span><span class="sxs-lookup"><span data-stu-id="aaaaa-390">I hope you have a better understanding than you had before.</span></span>

<!-- link references -->
[原文]: https://powershellexplained.com/2019-08-11-Powershell-if-then-else-equals-operator/
[original version]: https://powershellexplained.com/2019-08-11-Powershell-if-then-else-equals-operator/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[if]: /powershell/module/microsoft.powershell.core/about/about_if
[位元運算子]: /powershell/module/microsoft.powershell.core/about/about_arithmetic_operators#bitwise-operators
[bitwise operators]: /powershell/module/microsoft.powershell.core/about/about_arithmetic_operators#bitwise-operators
[使用 RegEx 的許多方式]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/
[the many ways to use regex]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/
[例外狀況的完整說明]: everything-about-exceptions.md
[everything you ever wanted to know about exceptions]: everything-about-exceptions.md
[$null 的完整說明]: everything-about-null.md
[everything you wanted to know about $null]: everything-about-null.md
[Prasoon Karunan V]: https://twitter.com/prasoonkarunan
[Switch 陳述式的完整說明]: everything-about-switch.md
[everything you ever wanted to know about the switch statement]: everything-about-switch.md
[Invoke-SnowSql]: https://github.com/loanDepot/SnowSQL/blob/a3731b52e4ab4ecb503fb81e2d8cb131e8f90410/SnowSQL/public/Invoke-SnowSql.ps1#L90
