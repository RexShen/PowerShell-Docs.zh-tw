---
title: 您想知道有關於 Switch 陳述式的一切
description: PowerShell 中的 Switch 陳述式提供了在其他語言中無法找到的功能。
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: ebf6191d56374273465ae6bee49ef82a02cc1580
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149421"
---
# <a name="everything-you-ever-wanted-to-know-about-the-switch-statement"></a><span data-ttu-id="4361a-103">您想知道有關於 Switch 陳述式的一切</span><span class="sxs-lookup"><span data-stu-id="4361a-103">Everything you ever wanted to know about the switch statement</span></span>

<span data-ttu-id="4361a-104">與其他語言相似，PowerShell 具備在您指令碼中控制執行流程的命令。</span><span class="sxs-lookup"><span data-stu-id="4361a-104">Like many other languages, PowerShell has commands for controlling the flow of execution within your scripts.</span></span> <span data-ttu-id="4361a-105">其中一個這類陳述式便是 [switch][] 陳述式，其在 PowerShell 中提供了在其他語言中無法找到的功能。</span><span class="sxs-lookup"><span data-stu-id="4361a-105">One of those statements is the [switch][] statement and in PowerShell, it offers features that aren't found in other languages.</span></span> <span data-ttu-id="4361a-106">今天，我們會深入探討使用 PowerShell 的 `switch`。</span><span class="sxs-lookup"><span data-stu-id="4361a-106">Today, we take a deep dive into working with the PowerShell `switch`.</span></span>

> [!NOTE]
> <span data-ttu-id="4361a-107">此[原文][]出自 [@KevinMarquette][] 所撰寫的部落格。</span><span class="sxs-lookup"><span data-stu-id="4361a-107">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="4361a-108">PowerShell 小組感謝 Kevin 分享此內容。</span><span class="sxs-lookup"><span data-stu-id="4361a-108">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="4361a-109">請前往 [PowerShellExplained.com][] 瀏覽 Kevin 的部落格。</span><span class="sxs-lookup"><span data-stu-id="4361a-109">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="if-statement"></a><span data-ttu-id="4361a-110">If 陳述式</span><span class="sxs-lookup"><span data-stu-id="4361a-110">If statement</span></span>

<span data-ttu-id="4361a-111">您所學到的一個陳述式是 `if` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="4361a-111">One of the first statements that you learn is the `if` statement.</span></span> <span data-ttu-id="4361a-112">其可以讓您在陳述式為 `$true` 時執行指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="4361a-112">It lets you execute a script block if a statement is `$true`.</span></span>

``` powershell
if ( Test-Path $Path )
{
    Remove-Item $Path
}
```

<span data-ttu-id="4361a-113">您可以透過使用 `elseif` 和 `else` 陳述式來擁有更複雜的邏輯。</span><span class="sxs-lookup"><span data-stu-id="4361a-113">You can have much more complicated logic by using `elseif` and `else` statements.</span></span> <span data-ttu-id="4361a-114">在以下範例，我擁有一個代表星期幾的數值，並且我希望將該名稱作為字串取得。</span><span class="sxs-lookup"><span data-stu-id="4361a-114">Here is an example where I have a numeric value for day of the week and I want to get the name as a string.</span></span>

``` powershell
$day = 3

if ( $day -eq 0 ) { $result = 'Sunday'        }
elseif ( $day -eq 1 ) { $result = 'Monday'    }
elseif ( $day -eq 2 ) { $result = 'Tuesday'   }
elseif ( $day -eq 3 ) { $result = 'Wednesday' }
elseif ( $day -eq 4 ) { $result = 'Thursday'  }
elseif ( $day -eq 5 ) { $result = 'Friday'    }
elseif ( $day -eq 6 ) { $result = 'Saturday'  }

$result
```

```Output
Wednesday
```

<span data-ttu-id="4361a-115">事實證明這是一個相當常見的模式，且有許多方式可以處理這種模式。</span><span class="sxs-lookup"><span data-stu-id="4361a-115">It turns out that this is a common pattern and there are many ways to deal with this.</span></span> <span data-ttu-id="4361a-116">其中一個便是使用 `switch`。</span><span class="sxs-lookup"><span data-stu-id="4361a-116">One of them is with a `switch`.</span></span>

## <a name="switch-statement"></a><span data-ttu-id="4361a-117">Switch 陳述式</span><span class="sxs-lookup"><span data-stu-id="4361a-117">Switch statement</span></span>

<span data-ttu-id="4361a-118">`switch` 陳述式可以讓您提供一個變數及可能值的清單。</span><span class="sxs-lookup"><span data-stu-id="4361a-118">The `switch` statement allows you to provide a variable and a list of possible values.</span></span> <span data-ttu-id="4361a-119">若該值與變數相符，便會執行其 ScriptBlock。</span><span class="sxs-lookup"><span data-stu-id="4361a-119">If the value matches the variable, then its scriptblock is executed.</span></span>

``` powershell
$day = 3

switch ( $day )
{
    0 { $result = 'Sunday'    }
    1 { $result = 'Monday'    }
    2 { $result = 'Tuesday'   }
    3 { $result = 'Wednesday' }
    4 { $result = 'Thursday'  }
    5 { $result = 'Friday'    }
    6 { $result = 'Saturday'  }
}

$result
```

```Output
'Wednesday'
```

<span data-ttu-id="4361a-120">針對此範例，`$day` 的值與其中一個數值相符，接著便會將正確的名稱指派給 `$result`。</span><span class="sxs-lookup"><span data-stu-id="4361a-120">For this example, the value of `$day` matches one of the numeric values, then the correct name is assigned to `$result`.</span></span> <span data-ttu-id="4361a-121">我們在此範例中只會執行變數指派，但在這些指令碼區塊中可以執行任何 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="4361a-121">We are only doing a variable assignment in this example, but any PowerShell can be executed in those script blocks.</span></span>

### <a name="assign-to-a-variable"></a><span data-ttu-id="4361a-122">指派給變數</span><span class="sxs-lookup"><span data-stu-id="4361a-122">Assign to a variable</span></span>

<span data-ttu-id="4361a-123">我們可以透過另外一種方式撰寫上一個範例。</span><span class="sxs-lookup"><span data-stu-id="4361a-123">We can write that last example in another way.</span></span>

``` powershell
$result = switch ( $day )
{
    0 { 'Sunday'    }
    1 { 'Monday'    }
    2 { 'Tuesday'   }
    3 { 'Wednesday' }
    4 { 'Thursday'  }
    5 { 'Friday'    }
    6 { 'Saturday'  }
}
```

<span data-ttu-id="4361a-124">我們可以將值置於 PowerShell 管線上，然後將其指派給 `$result`。</span><span class="sxs-lookup"><span data-stu-id="4361a-124">We are placing the value on the PowerShell pipeline and assigning it to the `$result`.</span></span> <span data-ttu-id="4361a-125">您可以使用 `if` 和 `foreach` 陳述式執行相同的操作。</span><span class="sxs-lookup"><span data-stu-id="4361a-125">You can do this same thing with the `if` and `foreach` statements.</span></span>

### <a name="default"></a><span data-ttu-id="4361a-126">預設</span><span class="sxs-lookup"><span data-stu-id="4361a-126">Default</span></span>

<span data-ttu-id="4361a-127">我們可以使用 `default` 關鍵字來辨別在沒有相符項目時會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="4361a-127">We can use the `default` keyword to identify the what should happen if there is no match.</span></span>

``` powershell
$result = switch ( $day )
{
    0 { 'Sunday' }
    # ...
    6 { 'Saturday' }
    default { 'Unknown' }
}
```

<span data-ttu-id="4361a-128">在此處我們會在預設案例中傳回 `Unknown` 值。</span><span class="sxs-lookup"><span data-stu-id="4361a-128">Here we return the value `Unknown` in the default case.</span></span>

### <a name="strings"></a><span data-ttu-id="4361a-129">字串</span><span class="sxs-lookup"><span data-stu-id="4361a-129">Strings</span></span>

<span data-ttu-id="4361a-130">我在最後幾個範例中比對了數字，但您也可以比對字串。</span><span class="sxs-lookup"><span data-stu-id="4361a-130">I was matching numbers in those last examples, but you can also match strings.</span></span>

``` powershell
$item = 'Role'

switch ( $item )
{
    Component
    {
        'is a component'
    }
    Role
    {
        'is a role'
    }
    Location
    {
        'is a location'
    }
}
```

```Output
is a role
```

<span data-ttu-id="4361a-131">我決定不把 `Component`、`Role` 和 `Location` 比對括在引號中，以表示這些是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="4361a-131">I decided not to wrap the `Component`,`Role` and `Location` matches in quotes here to highlight that they're optional.</span></span> <span data-ttu-id="4361a-132">`switch` 在大多數的案例中會將這些項目作為字串處理。</span><span class="sxs-lookup"><span data-stu-id="4361a-132">The `switch` treats those as a string in most cases.</span></span>

## <a name="arrays"></a><span data-ttu-id="4361a-133">陣列</span><span class="sxs-lookup"><span data-stu-id="4361a-133">Arrays</span></span>

<span data-ttu-id="4361a-134">PowerShell `switch` 其中一項很酷的功能就是其處理陣列的方式。</span><span class="sxs-lookup"><span data-stu-id="4361a-134">One of the cool features of the PowerShell `switch` is the way it handles arrays.</span></span> <span data-ttu-id="4361a-135">若您將一個陣列提供給 `switch`，其便會處理該集合中的每個項目。</span><span class="sxs-lookup"><span data-stu-id="4361a-135">If you give a `switch` an array, it processes each element in that collection.</span></span>

``` powershell
$roles = @('WEB','Database')

switch ( $roles ) {
    'Database'   { 'Configure SQL' }
    'WEB'        { 'Configure IIS' }
    'FileServer' { 'Configure Share' }
}
```

```Output
Configure IIS
Configure SQL
```

<span data-ttu-id="4361a-136">若陣列中包含重複的項目，會將其在適當的區段中多次比對。</span><span class="sxs-lookup"><span data-stu-id="4361a-136">If you have repeated items in your array, then they're matched multiple times by the appropriate section.</span></span>

### <a name="psitem"></a><span data-ttu-id="4361a-137">PSItem</span><span class="sxs-lookup"><span data-stu-id="4361a-137">PSItem</span></span>

<span data-ttu-id="4361a-138">您可以使用 `$PSItem` 或 `$_` 來參考目前的處理項目。</span><span class="sxs-lookup"><span data-stu-id="4361a-138">You can use the `$PSItem` or `$_` to reference the current item that was processed.</span></span> <span data-ttu-id="4361a-139">當我們進行簡單的比對時，`$PSItem` 便是我們正在比對的值。</span><span class="sxs-lookup"><span data-stu-id="4361a-139">When we do a simple match, `$PSItem` is the value that we are matching.</span></span> <span data-ttu-id="4361a-140">我會在下一節進行一些進階比對，並且在這些進階比對中使用此變數。</span><span class="sxs-lookup"><span data-stu-id="4361a-140">I'll be performing some advanced matches in the next section where this variable is used.</span></span>

## <a name="parameters"></a><span data-ttu-id="4361a-141">參數</span><span class="sxs-lookup"><span data-stu-id="4361a-141">Parameters</span></span>

<span data-ttu-id="4361a-142">PowerShell `switch` 的獨特功能便是其具備許多 [switch 參數][]，可以變更其執行的方式。</span><span class="sxs-lookup"><span data-stu-id="4361a-142">A unique feature of the PowerShell `switch` is that it has a number of [switch parameters][] that change how it performs.</span></span>

### <a name="-casesensitive"></a><span data-ttu-id="4361a-143">-CaseSensitive</span><span class="sxs-lookup"><span data-stu-id="4361a-143">-CaseSensitive</span></span>

<span data-ttu-id="4361a-144">根據預設，相符的項目不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="4361a-144">The matches aren't case-sensitive by default.</span></span> <span data-ttu-id="4361a-145">若您需要區分大小寫，可以使用 `-CaseSensitive`。</span><span class="sxs-lookup"><span data-stu-id="4361a-145">If you need to be case-sensitive, you can use `-CaseSensitive`.</span></span> <span data-ttu-id="4361a-146">其可以與其他 switch 參數一起使用。</span><span class="sxs-lookup"><span data-stu-id="4361a-146">This can be used in combination with the other switch parameters.</span></span>

### <a name="-wildcard"></a><span data-ttu-id="4361a-147">-Wildcard</span><span class="sxs-lookup"><span data-stu-id="4361a-147">-Wildcard</span></span>

<span data-ttu-id="4361a-148">我們可以使用 `-wildcard` switch 來啟用萬用字元支援。</span><span class="sxs-lookup"><span data-stu-id="4361a-148">We can enable wildcard support with the `-wildcard` switch.</span></span> <span data-ttu-id="4361a-149">其會使用與 `-like` 運算子相同的萬用字元邏輯來進行每個比對。</span><span class="sxs-lookup"><span data-stu-id="4361a-149">This uses the same wildcard logic as the `-like` operator to do each match.</span></span>

``` powershell
$Message = 'Warning, out of disk space'

switch -Wildcard ( $message )
{
    'Error*'
    {
        Write-Error -Message $Message
    }
    'Warning*'
    {
        Write-Warning -Message $Message
    }
    default
    {
        Write-Information $message
    }
}
```

```Output
WARNING: Warning, out of disk space
```

<span data-ttu-id="4361a-150">我們會在此處處理訊息，然後根據訊息的內容將其輸出到不同的串流上。</span><span class="sxs-lookup"><span data-stu-id="4361a-150">Here we are processing a message and then outputting it on different streams based on the contents.</span></span>

### <a name="-regex"></a><span data-ttu-id="4361a-151">-Regex</span><span class="sxs-lookup"><span data-stu-id="4361a-151">-Regex</span></span>

<span data-ttu-id="4361a-152">switch 陳述式支援 RegEx 比對，就跟其支援萬用字元一樣。</span><span class="sxs-lookup"><span data-stu-id="4361a-152">The switch statement supports regex matches just like it does wildcards.</span></span>

``` powershell
switch -Regex ( $message )
{
    '^Error'
    {
        Write-Error -Message $Message
    }
    '^Warning'
    {
        Write-Warning -Message $Message
    }
    default
    {
        Write-Information $message
    }
}
```

<span data-ttu-id="4361a-153">我在我寫的另外一篇文章中包含了更多使用 RegEx 的範例：[使用 RegEx 的許多方式][]。</span><span class="sxs-lookup"><span data-stu-id="4361a-153">I have more examples of using regex in another article I wrote: [The many ways to use regex][].</span></span>

### <a name="-file"></a><span data-ttu-id="4361a-154">-File</span><span class="sxs-lookup"><span data-stu-id="4361a-154">-File</span></span>

<span data-ttu-id="4361a-155">Switch 陳述式少為人知的功能是可以透過 `-File` 參數來處理檔案。</span><span class="sxs-lookup"><span data-stu-id="4361a-155">A little known feature of the switch statement is that it can process a file with the `-File` parameter.</span></span> <span data-ttu-id="4361a-156">您可以搭配檔案的路徑使用 `-file`，而非為其提供變數運算式。</span><span class="sxs-lookup"><span data-stu-id="4361a-156">You use `-file` with a path to a file instead of giving it a variable expression.</span></span>

``` powershell
switch -Wildcard -File $path
{
    'Error*'
    {
        Write-Error -Message $PSItem
    }
    'Warning*'
    {
        Write-Warning -Message $PSItem
    }
    default
    {
        Write-Output $PSItem
    }
}
```

<span data-ttu-id="4361a-157">其運作方式跟處理陣列類似。</span><span class="sxs-lookup"><span data-stu-id="4361a-157">It works just like processing an array.</span></span> <span data-ttu-id="4361a-158">在此範例中，我會將其與萬用字元比對組合，並使用 `$PSItem`。</span><span class="sxs-lookup"><span data-stu-id="4361a-158">In this example, I combine it with wildcard matching and make use of the `$PSItem`.</span></span> <span data-ttu-id="4361a-159">這會處理記錄檔，並根據 RegEx 比對項目將其轉換成警告和錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="4361a-159">This would process a log file and convert it to warning and error messages depending on the regex matches.</span></span>

## <a name="advanced-details"></a><span data-ttu-id="4361a-160">進階詳細資料</span><span class="sxs-lookup"><span data-stu-id="4361a-160">Advanced details</span></span>

<span data-ttu-id="4361a-161">現在您已了解所記載的所有功能，我們便可以在更進階處理的內容中使用這些功能。</span><span class="sxs-lookup"><span data-stu-id="4361a-161">Now that you're aware of all these documented features, we can use them in the context of more advanced processing.</span></span>

### <a name="expressions"></a><span data-ttu-id="4361a-162">運算式</span><span class="sxs-lookup"><span data-stu-id="4361a-162">Expressions</span></span>

<span data-ttu-id="4361a-163">`switch` 可以改為在運算式上使用，而非變數。</span><span class="sxs-lookup"><span data-stu-id="4361a-163">The `switch` can be on an expression instead of a variable.</span></span>

``` powershell
switch ( ( Get-Service | Where status -eq 'running' ).name ) {...}
```

<span data-ttu-id="4361a-164">運算式所要評估的值會是用於該比對的值。</span><span class="sxs-lookup"><span data-stu-id="4361a-164">Whatever the expression evaluates to is the value used for the match.</span></span>

### <a name="multiple-matches"></a><span data-ttu-id="4361a-165">多個比對項目</span><span class="sxs-lookup"><span data-stu-id="4361a-165">Multiple matches</span></span>

<span data-ttu-id="4361a-166">您可能已經使用過這項功能，但 `switch` 可以比對多個條件。</span><span class="sxs-lookup"><span data-stu-id="4361a-166">You may have already picked up on this, but a `switch` can match to multiple conditions.</span></span> <span data-ttu-id="4361a-167">這在使用 `-wildcard` 或 `-regex` 進行比對時更是如此。</span><span class="sxs-lookup"><span data-stu-id="4361a-167">This is especially true when using `-wildcard` or `-regex` matches.</span></span> <span data-ttu-id="4361a-168">您可以多次新增相同的條件，這些條件都會觸發。</span><span class="sxs-lookup"><span data-stu-id="4361a-168">You can add the same condition multiple times and all of them are triggered.</span></span>

``` powershell
switch ( 'Word' )
{
    'word' { 'lower case word match' }
    'Word' { 'mixed case word match' }
    'WORD' { 'upper case word match' }
}
```

```Output
lower case word match
mixed case word match
upper case word match
```

<span data-ttu-id="4361a-169">這三個陳述式全部都會觸發。</span><span class="sxs-lookup"><span data-stu-id="4361a-169">All three of these statements are fired.</span></span> <span data-ttu-id="4361a-170">這代表每個條件都會進行檢查 (按照順序)。</span><span class="sxs-lookup"><span data-stu-id="4361a-170">This shows that every condition is checked (in order).</span></span> <span data-ttu-id="4361a-171">這在處理陣列時也是如此，陣列中的每個項目會檢查每個條件。</span><span class="sxs-lookup"><span data-stu-id="4361a-171">This holds true for processing arrays where each item checks each condition.</span></span>

### <a name="continue"></a><span data-ttu-id="4361a-172">Continue</span><span class="sxs-lookup"><span data-stu-id="4361a-172">Continue</span></span>

<span data-ttu-id="4361a-173">一般而言，我會在此處介紹 `break` 陳述式，但先了解如何使用 `continue` 會更好。</span><span class="sxs-lookup"><span data-stu-id="4361a-173">Normally, this is where I would introduce the `break` statement, but it's better that we learn how to use `continue` first.</span></span> <span data-ttu-id="4361a-174">就像 `foreach` 迴圈一樣，`continue` 會繼續執行集合中的下一個項目，或是在沒有其他項目時結束 `switch`。</span><span class="sxs-lookup"><span data-stu-id="4361a-174">Just like with a `foreach` loop, `continue` continues onto the next item in the collection or exits the `switch` if there are no more items.</span></span> <span data-ttu-id="4361a-175">我們可以使用 continue 陳述式重新撰寫上一個範例，使其只執行一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="4361a-175">We can rewrite that last example with continue statements so that only one statement executes.</span></span>

``` powershell
switch ( 'Word' )
{
    'word'
    {
        'lower case word match'
        continue
    }
    'Word'
    {
        'mixed case word match'
        continue
    }
    'WORD'
    {
        'upper case word match'
        continue
    }
}
```

```Output
lower case word match
```

<span data-ttu-id="4361a-176">switch 會比對第一個項目，然後便會繼續執行下一個值，而非比對全部的三個項目。</span><span class="sxs-lookup"><span data-stu-id="4361a-176">Instead of matching all three items, the first one is matched and the switch continues to the next value.</span></span> <span data-ttu-id="4361a-177">因為沒有任何要處理的值，所以 switch 會結束。</span><span class="sxs-lookup"><span data-stu-id="4361a-177">Because there are no values left to process, the switch exits.</span></span> <span data-ttu-id="4361a-178">下一個範例顯示了萬用字元比對多個項目的方式。</span><span class="sxs-lookup"><span data-stu-id="4361a-178">This next example is showing how a wildcard could match multiple items.</span></span>

``` powershell
switch -Wildcard -File $path
{
    '*Error*'
    {
        Write-Error -Message $PSItem
        continue
    }
    '*Warning*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    default
    {
        Write-Output $PSItem
    }
}
```

<span data-ttu-id="4361a-179">因為輸入檔中的行可能會同時包含 `Error` 和 `Warning` 字詞，我們只希望執行第一個字詞，然後繼續處理檔案。</span><span class="sxs-lookup"><span data-stu-id="4361a-179">Because a line in the input file could contain both the word `Error` and `Warning`, we only want the first one to execute and then continue processing the file.</span></span>

### <a name="break"></a><span data-ttu-id="4361a-180">中斷</span><span class="sxs-lookup"><span data-stu-id="4361a-180">Break</span></span>

<span data-ttu-id="4361a-181">`break` 陳述式會結束 switch。</span><span class="sxs-lookup"><span data-stu-id="4361a-181">A `break` statement exits the switch.</span></span> <span data-ttu-id="4361a-182">這與 `continue` 針對單一值所呈現的行為相同。</span><span class="sxs-lookup"><span data-stu-id="4361a-182">This is the same behavior that `continue` presents for single values.</span></span> <span data-ttu-id="4361a-183">其差異會在處理陣列時顯示。</span><span class="sxs-lookup"><span data-stu-id="4361a-183">The difference is shown when processing an array.</span></span> <span data-ttu-id="4361a-184">`break` 會停止 switch 中的所有處理，`continue` 則會移動到下一個項目。</span><span class="sxs-lookup"><span data-stu-id="4361a-184">`break` stops all processing in the switch and `continue` moves onto the next item.</span></span>

``` powershell
$Messages = @(
    'Downloading update'
    'Ran into errors downloading file'
    'Error: out of disk space'
    'Sending email'
    '...'
)

switch -Wildcard ($Messages)
{
    'Error*'
    {
        Write-Error -Message $PSItem
        break
    }
    '*Error*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    '*Warning*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    default
    {
        Write-Output $PSItem
    }
}
```

```Output
Downloading update
WARNING: Ran into errors downloading file
write-error -message $PSItem : Error: out of disk space
+ CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
+ FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException
```

<span data-ttu-id="4361a-185">在此案例中，若我們遇到任何開頭為 `Error` 的行，便會出現錯誤，然後 switch 會停止。</span><span class="sxs-lookup"><span data-stu-id="4361a-185">In this case, if we hit any lines that start with `Error` then we get an error and the switch stops.</span></span>
<span data-ttu-id="4361a-186">這就是 `break` 陳述式為我們執行的操作。</span><span class="sxs-lookup"><span data-stu-id="4361a-186">This is what that `break` statement is doing for us.</span></span> <span data-ttu-id="4361a-187">若我們在字串中發現 `Error`，而非只在開頭，便會將其作為警告寫入。</span><span class="sxs-lookup"><span data-stu-id="4361a-187">If we find `Error` inside the string and not just at the beginning, we write it as a warning.</span></span> <span data-ttu-id="4361a-188">我們會對 `Warning` 執行相同的操作。</span><span class="sxs-lookup"><span data-stu-id="4361a-188">We do the same thing for `Warning`.</span></span> <span data-ttu-id="4361a-189">一行可能會同時包含 `Error` 和 `Warning` 字詞，但我們只需要其中一個就可執行。</span><span class="sxs-lookup"><span data-stu-id="4361a-189">It's possible that a line could have both the word `Error` and `Warning`, but we only need one to process.</span></span> <span data-ttu-id="4361a-190">這便是 `continue` 為我們執行的操作。</span><span class="sxs-lookup"><span data-stu-id="4361a-190">This is what the `continue` statement is doing for us.</span></span>

### <a name="break-labels"></a><span data-ttu-id="4361a-191">中斷標籤</span><span class="sxs-lookup"><span data-stu-id="4361a-191">Break labels</span></span>

<span data-ttu-id="4361a-192">`switch` 陳述式支援 `break/continue` 標籤，如同 `foreach` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="4361a-192">The `switch` statement supports `break/continue` labels just like `foreach`.</span></span>

``` powershell
:filelist foreach($path in $logs)
{
    :logFile switch -Wildcard -File $path
    {
        'Error*'
        {
            Write-Error -Message $PSItem
            break filelist
        }
        'Warning*'
        {
            Write-Error -Message $PSItem
            break logFile
        }
        default
        {
            Write-Output $PSItem
        }
    }
}
```

<span data-ttu-id="4361a-193">我個人不喜歡使用中斷標籤，但我還是想要提及，因為若您先前從未看過這些標籤，可能會覺得相當困惑。</span><span class="sxs-lookup"><span data-stu-id="4361a-193">I personally don't like the use of break labels but I wanted to point them out because they're confusing if you've never seen them before.</span></span> <span data-ttu-id="4361a-194">當您有多個呈現巢狀的 `switch` 或 `foreach` 陳述式時，建議您中斷最內部以外的項目。</span><span class="sxs-lookup"><span data-stu-id="4361a-194">When you have multiple `switch` or `foreach` statements that are nested, you may want to break out of more than the inner most item.</span></span> <span data-ttu-id="4361a-195">您可以將標籤置於 `switch` 上，其可以作為 `break` 的目標。</span><span class="sxs-lookup"><span data-stu-id="4361a-195">You can place a label on a `switch` that can be the target of your `break`.</span></span>

### <a name="enum"></a><span data-ttu-id="4361a-196">例舉</span><span class="sxs-lookup"><span data-stu-id="4361a-196">Enum</span></span>

<span data-ttu-id="4361a-197">PowerShell 5.0 提供了列舉，讓我們可在 switch 中使用。</span><span class="sxs-lookup"><span data-stu-id="4361a-197">PowerShell 5.0 gave us enums and we can use them in a switch.</span></span>

``` powershell
enum Context {
    Component
    Role
    Location
}

$item = [Context]::Role

switch ( $item )
{
    Component
    {
        'is a component'
    }
    Role
    {
        'is a role'
    }
    Location
    {
        'is a location'
    }
}
```

```Output
is a role
```

<span data-ttu-id="4361a-198">若您希望保持所有項目為強型別列舉，可以將這些項目放在括弧中。</span><span class="sxs-lookup"><span data-stu-id="4361a-198">If you want to keep everything as strongly typed enums, then you can place them in parentheses.</span></span>

``` powershell
switch ($item )
{
    ([Context]::Component)
    {
        'is a component'
    }
    ([Context]::Role)
    {
        'is a role'
    }
    ([Context]::Location)
    {
        'is a location'
    }
}
```

<span data-ttu-id="4361a-199">此處需要括弧，以避免 switch 將 `[Context]::Location` 值視為常值字串處理。</span><span class="sxs-lookup"><span data-stu-id="4361a-199">The parentheses are needed here so that the switch doesn't treat the value `[Context]::Location` as a literal string.</span></span>

### <a name="scriptblock"></a><span data-ttu-id="4361a-200">ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="4361a-200">ScriptBlock</span></span>

<span data-ttu-id="4361a-201">我們可以視需要使用 ScriptBlock 為比對執行評估。</span><span class="sxs-lookup"><span data-stu-id="4361a-201">We can use a scriptblock to perform the evaluation for a match if needed.</span></span>

``` powershell
$age = 37

switch ( $age )
{
    {$PSItem -le 18}
    {
        'child'
    }
    {$PSItem -gt 18}
    {
        'adult'
    }
}
```

```Output
'adult'
```

<span data-ttu-id="4361a-202">這會增加複雜度，並且可能會讓您的 `switch` 難以閱讀。</span><span class="sxs-lookup"><span data-stu-id="4361a-202">This adds complexity and can make your `switch` hard to read.</span></span> <span data-ttu-id="4361a-203">在大多數您想要使用這類項目的案例中，建議使用 `if` 和 `elseif` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="4361a-203">In most cases where you would use something like this it would be better to use `if` and `elseif` statements.</span></span> <span data-ttu-id="4361a-204">若我已經擁有大型的 switch，且需要兩個項目叫用相同的評估區塊，便會考慮使用此項目。</span><span class="sxs-lookup"><span data-stu-id="4361a-204">I would consider using this if I already had a large switch in place and I needed two items to hit the same evaluation block.</span></span>

<span data-ttu-id="4361a-205">有一個我認為可以提升易讀性的方法，便是將 ScriptBlock 放在括弧中。</span><span class="sxs-lookup"><span data-stu-id="4361a-205">One thing that I think helps with legibility is to place the scriptblock in parentheses.</span></span>

``` powershell
switch ( $age )
{
    ({$PSItem -le 18})
    {
        'child'
    }
    ({$PSItem -gt 18})
    {
        'adult'
    }
}
```

<span data-ttu-id="4361a-206">其仍會以相同的方式執行，並且可以在快速查看時有更好的視覺體驗。</span><span class="sxs-lookup"><span data-stu-id="4361a-206">It still executes the same way and gives a better visual break when quickly looking at it.</span></span>

### <a name="regex-matches"></a><span data-ttu-id="4361a-207">RegEx $matches</span><span class="sxs-lookup"><span data-stu-id="4361a-207">Regex $matches</span></span>

<span data-ttu-id="4361a-208">我們必須回到 RegEx 接觸一些不會讓人立即察覺的項目。</span><span class="sxs-lookup"><span data-stu-id="4361a-208">We need to revisit regex to touch on something that isn't immediately obvious.</span></span> <span data-ttu-id="4361a-209">使用 RegEx 會填入 `$matches` 變數。</span><span class="sxs-lookup"><span data-stu-id="4361a-209">The use of regex populates the `$matches` variable.</span></span> <span data-ttu-id="4361a-210">當我談到[使用 RegEx 的許多方式][]時，我更常談的是如何使用 `$matches`。</span><span class="sxs-lookup"><span data-stu-id="4361a-210">I do go into the use of `$matches` more when I talk about [The many ways to use regex][].</span></span> <span data-ttu-id="4361a-211">以下是示範其搭配具名比對項目運作方式的快速範例。</span><span class="sxs-lookup"><span data-stu-id="4361a-211">Here is a quick sample to show it in action with named matches.</span></span>

``` powershell
$message = 'my ssn is 123-23-3456 and credit card: 1234-5678-1234-5678'

switch -regex ($message)
{
    '(?<SSN>\d\d\d-\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a SSN: $($matches.SSN)"
    }
    '(?<CC>\d\d\d\d-\d\d\d\d-\d\d\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a credit card number: $($matches.CC)"
    }
    '(?<Phone>\d\d\d-\d\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a phone number: $($matches.Phone)"
    }
}
```

```Output
WARNING: message may contain a SSN: 123-23-3456
WARNING: message may contain a credit card number: 1234-5678-1234-5678
```

### <a name="null"></a><span data-ttu-id="4361a-212">$null</span><span class="sxs-lookup"><span data-stu-id="4361a-212">$null</span></span>

<span data-ttu-id="4361a-213">您可以比對不一定要是預設的 `$null` 值。</span><span class="sxs-lookup"><span data-stu-id="4361a-213">You can match a `$null` value that doesn't have to be the default.</span></span>

``` powershell
$value = $null

switch ( $value )
{
    $null
    {
        'Value is null'
    }
    default
    {
        'value is not null'
    }
}

```Output
Value is null
```

<span data-ttu-id="4361a-214">這也適用於空字串。</span><span class="sxs-lookup"><span data-stu-id="4361a-214">Same goes for an empty string.</span></span>

``` powershell
switch ( '' )
{
    ''
    {
        'Value is empty'
    }
    default
    {
        'value is a empty string'
    }
}

```Output
Value is empty
```

### <a name="constant-expression"></a><span data-ttu-id="4361a-215">常數運算式</span><span class="sxs-lookup"><span data-stu-id="4361a-215">Constant expression</span></span>

<span data-ttu-id="4361a-216">Lee Dailey 指出我們可以使用常數 `$true` 運算式來評估 `[bool]` 項目。</span><span class="sxs-lookup"><span data-stu-id="4361a-216">Lee Dailey pointed out that we can use a constant `$true` expression to evaluate `[bool]` items.</span></span>
<span data-ttu-id="4361a-217">假設我們有幾個需要進行的布林值檢查。</span><span class="sxs-lookup"><span data-stu-id="4361a-217">Imagine if we have several boolean checks that need to happen.</span></span>

``` powershell
$isVisible = $false
$isEnabled = $true
$isSecure = $true

switch ( $true )
{
    $isEnabled
    {
        'Do-Action'
    }
    $isVisible
    {
        'Show-Animation'
    }
    $isSecure
    {
        'Enable-AdminMenu'
    }
}
```

```Output
Do-Action
Enabled-AdminMenu
```

<span data-ttu-id="4361a-218">這是進行評估及針對數個布林值欄位狀態採取動作的最簡潔方式。</span><span class="sxs-lookup"><span data-stu-id="4361a-218">This is a clean way to evaluate and take action on the status of several boolean fields.</span></span> <span data-ttu-id="4361a-219">最棒的是，您可以讓其中一個比對項目翻轉尚未評估的值的狀態。</span><span class="sxs-lookup"><span data-stu-id="4361a-219">The cool thing about this is that you can have one match flip the status of a value that hasn't been evaluated yet.</span></span>

``` powershell
$isVisible = $false
$isEnabled = $true
$isAdmin = $false

switch ( $true )
{
    $isEnabled
    {
        'Do-Action'
        $isVisible = $true
    }
    $isVisible
    {
        'Show-Animation'
    }
    $isAdmin
    {
        'Enable-AdminMenu'
    }
}
```

```Output
Do-Action
Show-Animation
```

<span data-ttu-id="4361a-220">在此範例中將 `$isEnabled` 設為 `$true` 可以確保 `$isVisible` 也會設為 `$true`。</span><span class="sxs-lookup"><span data-stu-id="4361a-220">Setting `$isEnabled` to `$true` in this example makes sure that `$isVisible` is also set to `$true`.</span></span> <span data-ttu-id="4361a-221">然後，當評估 `$isVisible` 時，便會呼叫其 ScriptBlock。</span><span class="sxs-lookup"><span data-stu-id="4361a-221">Then when `$isVisible` gets evaluated, its scriptblock is invoked.</span></span> <span data-ttu-id="4361a-222">這雖然有點不直覺，但是卻是使用該機制的聰明方式。</span><span class="sxs-lookup"><span data-stu-id="4361a-222">This is a bit counter-intuitive but is a clever use of the mechanics.</span></span>

### <a name="switch-automatic-variable"></a><span data-ttu-id="4361a-223">$switch 自動變數</span><span class="sxs-lookup"><span data-stu-id="4361a-223">$switch automatic variable</span></span>

<span data-ttu-id="4361a-224">當 `switch` 處理其值時，其會建立列舉程式並呼叫其為 `$switch`。</span><span class="sxs-lookup"><span data-stu-id="4361a-224">When the `switch` is processing its values, it creates an enumerator and calls it `$switch`.</span></span> <span data-ttu-id="4361a-225">這是由 PowerShell 所建立的自動變數，其可以讓您直接操作。</span><span class="sxs-lookup"><span data-stu-id="4361a-225">This is an automatic variable created by PowerShell and you can manipulate it directly.</span></span>

<span data-ttu-id="4361a-226">這是由 [/u/frmadsen](https://www.reddit.com/user/frmadsen) 向我指出的</span><span class="sxs-lookup"><span data-stu-id="4361a-226">This was pointed out to me by [/u/frmadsen](https://www.reddit.com/user/frmadsen)</span></span>

<div class="reddit-embed" data-embed-media="www.redditmedia.com" data-embed-parent="false" data-embed-live="false" data-embed-uuid="8f6edbf1-abc6-4513-971e-ccd1d202889d" data-embed-created="2018-12-25T22:05:33.986Z"><span data-ttu-id="4361a-227">來自<a href="https://www.reddit.com/r/PowerShell/comments/a90rx2/what_should_i_it_student_learn_to_master/">我 (IT 學生) 該如何熟悉運用 PowerShell？</a>(英文) 討論的<a href="https://www.reddit.com/r/PowerShell/comments/a90rx2/what_should_i_it_student_learn_to_master/ecj2kji/">留言</a>。</span><span class="sxs-lookup"><span data-stu-id="4361a-227"><a href="https://www.reddit.com/r/PowerShell/comments/a90rx2/what_should_i_it_student_learn_to_master/ecj2kji/">Comment</a> from discussion <a href="https://www.reddit.com/r/PowerShell/comments/a90rx2/what_should_i_it_student_learn_to_master/">What should I (IT student) learn to master PowerShell?</a>.</span></span></div><script async src="https://www.redditstatic.com/comment-embed.js"></script>

<span data-ttu-id="4361a-228">這可以為您提供以下結果：</span><span class="sxs-lookup"><span data-stu-id="4361a-228">This gives you the results of:</span></span>

```Output
2
4
```

<span data-ttu-id="4361a-229">藉由將列舉程式向前移動，下一個項目將不會由 `switch` 進行處理，但是您可以直接存取該值。</span><span class="sxs-lookup"><span data-stu-id="4361a-229">By moving the enumerator forward, the next item doesn't get processed by the `switch` but you can access that value directly.</span></span> <span data-ttu-id="4361a-230">我認為這種做法相當瘋狂。</span><span class="sxs-lookup"><span data-stu-id="4361a-230">I would call it madness.</span></span>

## <a name="other-patterns"></a><span data-ttu-id="4361a-231">其他模式</span><span class="sxs-lookup"><span data-stu-id="4361a-231">Other patterns</span></span>

### <a name="hashtables"></a><span data-ttu-id="4361a-232">雜湊表</span><span class="sxs-lookup"><span data-stu-id="4361a-232">Hashtables</span></span>

<span data-ttu-id="4361a-233">我其中一個最熱門的貼文是針對[雜湊表][]的貼文。</span><span class="sxs-lookup"><span data-stu-id="4361a-233">One of my most popular posts is the one I did on [hashtables][].</span></span> <span data-ttu-id="4361a-234">其中一個 `hashtable` 的使用案例是作為查閱資料表。</span><span class="sxs-lookup"><span data-stu-id="4361a-234">One of the use cases for a `hashtable` is to be a lookup table.</span></span> <span data-ttu-id="4361a-235">這是除了 `switch` 陳述式所經常處理的常見模式之外，可用的替代方法。</span><span class="sxs-lookup"><span data-stu-id="4361a-235">That is an alternate approach to a common pattern that a `switch` statement is often addressing.</span></span>

``` powershell
$day = 3

$lookup = @{
    0 = 'Sunday'
    1 = 'Monday'
    2 = 'Tuesday'
    3 = 'Wednesday'
    4 = 'Thursday'
    5 = 'Friday'
    6 = 'Saturday'
}

$lookup[$day]
```

```Output
Wednesday
```

<span data-ttu-id="4361a-236">若我只將 `switch` 作為查閱使用，我經常會改為使用 `hashtable`。</span><span class="sxs-lookup"><span data-stu-id="4361a-236">If I'm only using a `switch` as a lookup, I often use a `hashtable` instead.</span></span>

### <a name="enum"></a><span data-ttu-id="4361a-237">例舉</span><span class="sxs-lookup"><span data-stu-id="4361a-237">Enum</span></span>

<span data-ttu-id="4361a-238">PowerShell 5.0 引進了 `Enum`，而這也是此案例中的選項之一。</span><span class="sxs-lookup"><span data-stu-id="4361a-238">PowerShell 5.0 introduced the `Enum` and it's also an option in this case.</span></span>

``` powershell
$day = 3

enum DayOfTheWeek {
    Sunday
    Monday
    Tuesday
    Wednesday
    Thursday
    Friday
    Saturday
}

[DayOfTheWeek]$day
```

```Output
Wednesday
```

<span data-ttu-id="4361a-239">我們可以花上一整天的時間來查看解決此問題的不同方式。</span><span class="sxs-lookup"><span data-stu-id="4361a-239">We could go all day looking at different ways to solve this problem.</span></span> <span data-ttu-id="4361a-240">但我只想確定您知道您可有所選擇。</span><span class="sxs-lookup"><span data-stu-id="4361a-240">I just wanted to make sure you knew you had options.</span></span>

## <a name="final-words"></a><span data-ttu-id="4361a-241">結論</span><span class="sxs-lookup"><span data-stu-id="4361a-241">Final words</span></span>

<span data-ttu-id="4361a-242">switch 陳述式表面上相當簡單，但其提供了一些不為人知的進階功能。</span><span class="sxs-lookup"><span data-stu-id="4361a-242">The switch statement is simple on the surface but it offers some advanced features that most people don't realize are available.</span></span> <span data-ttu-id="4361a-243">將這些功能連結在一起可以讓其提供強大的功能。</span><span class="sxs-lookup"><span data-stu-id="4361a-243">Stringing those features together makes this a powerful feature.</span></span> <span data-ttu-id="4361a-244">我希望您有了解到一些先前並不了解的知識。</span><span class="sxs-lookup"><span data-stu-id="4361a-244">I hope you learned something that you had not realized before.</span></span>

<!-- link references -->
[原文]: https://powershellexplained.com/2018-01-12-Powershell-switch-statement/
[original version]: https://powershellexplained.com/2018-01-12-Powershell-switch-statement/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[switch]: /powershell/module/microsoft.powershell.core/about/about_switch
[switch 參數]: https://www.powershellmagazine.com/2013/12/20/using-powershell-switch-vs-boolean-parameters-in-sma-runbooks/
[switch parameters]: https://www.powershellmagazine.com/2013/12/20/using-powershell-switch-vs-boolean-parameters-in-sma-runbooks/
[使用 RegEx 的許多方式]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression
[The many ways to use regex]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression
[雜湊表]: everything-about-hashtable.md
[hashtables]: everything-about-hashtable.md
