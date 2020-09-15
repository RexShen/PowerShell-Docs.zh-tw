---
title: 您想知道有關於 $null 的一切
description: PowerShell $null 常常看起來很簡單，但其實有很多細微差異。 讓我們仔細看一下 $null，您就會知道當您意外遇到 Null 值時，會發生什麼事。
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: e0553a5e17450d8044f548792649369e99903850
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149471"
---
# <a name="everything-you-wanted-to-know-about-null"></a><span data-ttu-id="f0d78-104">您想知道有關於 $null 的一切</span><span class="sxs-lookup"><span data-stu-id="f0d78-104">Everything you wanted to know about $null</span></span>

<span data-ttu-id="f0d78-105">PowerShell `$null` 常常看起來很簡單，但其實有很多細微差異。</span><span class="sxs-lookup"><span data-stu-id="f0d78-105">The PowerShell `$null` often appears to be simple but it has a lot of nuances.</span></span> <span data-ttu-id="f0d78-106">讓我們仔細看一下 `$null`，您就會知道當您意外遇到 `$null` 值時，會發生什麼事。</span><span class="sxs-lookup"><span data-stu-id="f0d78-106">Let's take a close look at `$null` so you know what happens when you unexpectedly run into a `$null` value.</span></span>

> [!NOTE]
> <span data-ttu-id="f0d78-107">此文章的[原始版本][]出現在 [@KevinMarquette][] 所撰寫的部落格中。</span><span class="sxs-lookup"><span data-stu-id="f0d78-107">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="f0d78-108">PowerShell 小組感謝 Kevin 與我們分享此內容。</span><span class="sxs-lookup"><span data-stu-id="f0d78-108">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="f0d78-109">請前往 [PowerShellExplained.com][] 瀏覽他的部落格。</span><span class="sxs-lookup"><span data-stu-id="f0d78-109">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="what-is-null"></a><span data-ttu-id="f0d78-110">什麼是 NULL？</span><span class="sxs-lookup"><span data-stu-id="f0d78-110">What is NULL?</span></span>

<span data-ttu-id="f0d78-111">您可以將 NULL 想成是未知或空白的值。</span><span class="sxs-lookup"><span data-stu-id="f0d78-111">You can think of NULL as an unknown or empty value.</span></span> <span data-ttu-id="f0d78-112">在指派值或物件給變數之前，變數就會是 NULL。</span><span class="sxs-lookup"><span data-stu-id="f0d78-112">A variable is NULL until you assign a value or an object to it.</span></span> <span data-ttu-id="f0d78-113">這可能很重要，因為有一些命令需要值，而且如果值為 NULL，就會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="f0d78-113">This can be important because there are some commands that require a value and generate errors if the value is NULL.</span></span>

### <a name="powershell-null"></a><span data-ttu-id="f0d78-114">PowerShell $null</span><span class="sxs-lookup"><span data-stu-id="f0d78-114">PowerShell $null</span></span>

<span data-ttu-id="f0d78-115">`$null` 是 PowerShell 中用來代表 NULL 的自動變數。</span><span class="sxs-lookup"><span data-stu-id="f0d78-115">`$null` is an automatic variable in PowerShell used to represent NULL.</span></span> <span data-ttu-id="f0d78-116">您可以將其指派給變數、將其用於比較，以及在集合中將其作為 NULL 的預留位置使用。</span><span class="sxs-lookup"><span data-stu-id="f0d78-116">You can assign it to variables, use it in comparisons and use it as a place holder for NULL in a collection.</span></span>

<span data-ttu-id="f0d78-117">PowerShell 會將 `$null` 視為具有 NULL 值的物件。</span><span class="sxs-lookup"><span data-stu-id="f0d78-117">PowerShell treats `$null` as an object with a value of NULL.</span></span> <span data-ttu-id="f0d78-118">如果您之前使用另一種語言，這可能會和您預期的不同。</span><span class="sxs-lookup"><span data-stu-id="f0d78-118">This is different than what you may expect if you come from another language.</span></span>

## <a name="examples-of-null"></a><span data-ttu-id="f0d78-119">$null 的範例</span><span class="sxs-lookup"><span data-stu-id="f0d78-119">Examples of $null</span></span>

<span data-ttu-id="f0d78-120">每當您嘗試使用尚未初始化的變數時，值就會是 `$null`。</span><span class="sxs-lookup"><span data-stu-id="f0d78-120">Anytime you try to use a variable that you have not initialized, the value is `$null`.</span></span> <span data-ttu-id="f0d78-121">這是 `$null` 值潛入到您的程式碼中時，其中一種最常見的潛入方式。</span><span class="sxs-lookup"><span data-stu-id="f0d78-121">This is one of the most common ways that `$null` values sneak into your code.</span></span>

```powershell
PS> $null -eq $undefinedVariable
True
```

<span data-ttu-id="f0d78-122">如果您輸入錯誤的變數名稱，PowerShell 會將其視為不同的變數，而值會是 `$null`。</span><span class="sxs-lookup"><span data-stu-id="f0d78-122">If you happen to mistype a variable name then PowerShell sees it as a different variable and the value is `$null`.</span></span>

<span data-ttu-id="f0d78-123">另一種尋找 `$null` 值的方式是，當它們來自不提供任何結果的其他命令時。</span><span class="sxs-lookup"><span data-stu-id="f0d78-123">The other way you find `$null` values is when they come from other commands that don't give you any results.</span></span>

```powershell
PS> function Get-Nothing {}
PS> $value = Get-Nothing
PS> $null -eq $value
True
```

## <a name="impact-of-null"></a><span data-ttu-id="f0d78-124">$null 的影響</span><span class="sxs-lookup"><span data-stu-id="f0d78-124">Impact of $null</span></span>

<span data-ttu-id="f0d78-125">`$null` 值會依據其顯示的位置，對您的程式碼產生不同的影響。</span><span class="sxs-lookup"><span data-stu-id="f0d78-125">`$null` values impact your code differently depending on where they show up.</span></span>

### <a name="in-strings"></a><span data-ttu-id="f0d78-126">在字串中</span><span class="sxs-lookup"><span data-stu-id="f0d78-126">In strings</span></span>

<span data-ttu-id="f0d78-127">如果您在字串中使用 `$null`，其就是空白值 (或空字串)。</span><span class="sxs-lookup"><span data-stu-id="f0d78-127">If you use `$null` in a string, then it's a blank value (or empty string).</span></span>

```powershell
PS> $value = $null
PS> Write-Output "The value is $value"
The value is
```

<span data-ttu-id="f0d78-128">這是我在記錄檔訊息中使用變數時，偏好用括弧括住變數的其中一個原因。</span><span class="sxs-lookup"><span data-stu-id="f0d78-128">This is one of the reasons that I like to place brackets around variables when using them in log messages.</span></span> <span data-ttu-id="f0d78-129">當值位於字串的結尾時，識別變數值的邊緣甚至會變得更加重要。</span><span class="sxs-lookup"><span data-stu-id="f0d78-129">It's even more important to identify the edges of your variable values when the value is at the end of the string.</span></span>

```powershell
PS> $value = $null
PS> Write-Output "The value is [$value]"
The value is []
```

<span data-ttu-id="f0d78-130">這可讓您易於找出空字串與 `$null` 值。</span><span class="sxs-lookup"><span data-stu-id="f0d78-130">This makes empty strings and `$null` values easy to spot.</span></span>

### <a name="in-numeric-equation"></a><span data-ttu-id="f0d78-131">在數值方程式中</span><span class="sxs-lookup"><span data-stu-id="f0d78-131">In numeric equation</span></span>

<span data-ttu-id="f0d78-132">在數值方程式中使用 `$null` 值時，如果結果不會提供錯誤，那結果就會是無效的。</span><span class="sxs-lookup"><span data-stu-id="f0d78-132">When a `$null` value is used in a numeric equation then your results are invalid if they don't give an error.</span></span> <span data-ttu-id="f0d78-133">有時候 `$null` 會評估為 `0`，而其他時候則會讓整個結果為 `$null`。</span><span class="sxs-lookup"><span data-stu-id="f0d78-133">Sometimes the `$null` evaluates to `0` and other times it makes the whole result `$null`.</span></span>
<span data-ttu-id="f0d78-134">以下是根據值的順序，給出 0 或 `$null` 的乘法範例。</span><span class="sxs-lookup"><span data-stu-id="f0d78-134">Here is an example with multiplication that gives 0 or `$null` depending on the order of the values.</span></span>

```powershell
PS> $null * 5
PS> $null -eq ( $null * 5 )
True

PS> 5 * $null
0
PS> $null -eq ( 5 * $null )
False
```

### <a name="in-place-of-a-collection"></a><span data-ttu-id="f0d78-135">代替集合</span><span class="sxs-lookup"><span data-stu-id="f0d78-135">In place of a collection</span></span>

<span data-ttu-id="f0d78-136">集合可讓您使用索引來存取值。</span><span class="sxs-lookup"><span data-stu-id="f0d78-136">A collection allow you use an index to access values.</span></span> <span data-ttu-id="f0d78-137">如果您嘗試在實際為 `null` 的集合中編製索引，會收到此錯誤：`Cannot index into a null array`。</span><span class="sxs-lookup"><span data-stu-id="f0d78-137">If you try to index into a collection that is actually `null`, you get this error: `Cannot index into a null array`.</span></span>

```powershell
PS> $value = $null
PS> $value[10]
Cannot index into a null array.
At line:1 char:1
+ $value[10]
+ ~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [], RuntimeException
    + FullyQualifiedErrorId : NullArray
```

<span data-ttu-id="f0d78-138">如果您有集合，但嘗試存取不在集合中的元素時，會得到 `$null` 結果。</span><span class="sxs-lookup"><span data-stu-id="f0d78-138">If you have a collection but try to access an element that is not in the collection, you get a `$null` result.</span></span>

```powershell
$array = @( 'one','two','three' )
$null -eq $array[100]
True
```

### <a name="in-place-of-an-object"></a><span data-ttu-id="f0d78-139">代替物件</span><span class="sxs-lookup"><span data-stu-id="f0d78-139">In place of an object</span></span>

<span data-ttu-id="f0d78-140">如果您嘗試存取物件的屬性或子屬性，但物件並沒有您指定的屬性，會取得 `$null` 值，就像針對未定義的變數所取得的結果一樣。</span><span class="sxs-lookup"><span data-stu-id="f0d78-140">If you try to access a property or sub property of an object that doesn't have the specified property, you get a `$null` value like you would for an undefined variable.</span></span> <span data-ttu-id="f0d78-141">在此情況下，變數為 `$null` 或實際物件並不重要。</span><span class="sxs-lookup"><span data-stu-id="f0d78-141">It doesn't matter if the variable is `$null` or an actual object in this case.</span></span>

```powershell
PS> $null -eq $undefined.some.fake.property
True

PS> $date = Get-Date
PS> $null -eq $date.some.fake.property
True
```

### <a name="method-on-a-null-valued-expression"></a><span data-ttu-id="f0d78-142">Null 值運算式上的方法</span><span class="sxs-lookup"><span data-stu-id="f0d78-142">Method on a null-valued expression</span></span>

<span data-ttu-id="f0d78-143">呼叫 `$null` 物件上的方法會擲回 `RuntimeException`。</span><span class="sxs-lookup"><span data-stu-id="f0d78-143">Calling a method on a `$null` object throws a `RuntimeException`.</span></span>

```powershell
PS> $value = $null
PS> $value.toString()
You cannot call a method on a null-valued expression.
At line:1 char:1
+ $value.tostring()
+ ~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [], RuntimeException
    + FullyQualifiedErrorId : InvokeMethodOnNull
```

<span data-ttu-id="f0d78-144">每當我看到片語 `You cannot call a method on a null-valued expression` 時，我首先要尋找的項目就是在變數上呼叫方法，而不需要先檢查值是否為 `$null` 的地方。</span><span class="sxs-lookup"><span data-stu-id="f0d78-144">Whenever I see the phrase `You cannot call a method on a null-valued expression` then the first thing I look for are places where I am calling a method on a variable without first checking it for `$null`.</span></span>

## <a name="checking-for-null"></a><span data-ttu-id="f0d78-145">檢查 $null</span><span class="sxs-lookup"><span data-stu-id="f0d78-145">Checking for $null</span></span>

<span data-ttu-id="f0d78-146">您可能已經注意到，在我的範例中檢查 `$null` 時，我一律會將 `$null` 放在左側。</span><span class="sxs-lookup"><span data-stu-id="f0d78-146">You may have noticed that I always place the `$null` on the left when checking for `$null` in my examples.</span></span> <span data-ttu-id="f0d78-147">這是刻意的，而且已被視為 PowerShell 最佳做法。</span><span class="sxs-lookup"><span data-stu-id="f0d78-147">This is intentional and accepted as a PowerShell best practice.</span></span> <span data-ttu-id="f0d78-148">在某些情況下，將其放在右側並不會提供您預期的結果。</span><span class="sxs-lookup"><span data-stu-id="f0d78-148">There are some scenarios where placing it on the right doesn't give you the expected result.</span></span>

<span data-ttu-id="f0d78-149">請看看下一個範例並嘗試預測結果：</span><span class="sxs-lookup"><span data-stu-id="f0d78-149">Look at this next example and try to predict the results:</span></span>

```powershell
if ( $value -eq $null )
{
    'The array is $null'
}
if ( $value -ne $null )
{
    'The array is not $null'
}
```

<span data-ttu-id="f0d78-150">如果我沒有定義 `$value`，第一個就會評估為 `$true`，而且我們的訊息為 `The array is $null`。</span><span class="sxs-lookup"><span data-stu-id="f0d78-150">If I do not define `$value`, the first one evaluates to `$true` and our message is `The array is $null`.</span></span> <span data-ttu-id="f0d78-151">這裡的陷阱是可以建立 `$value`，來允許它們兩個都可以是 `$false`</span><span class="sxs-lookup"><span data-stu-id="f0d78-151">The trap here is that it's possible to create a `$value` that allows both of them to be `$false`</span></span>

```powershell
$value = @( $null )
```

<span data-ttu-id="f0d78-152">在此情況下，`$value` 是包含 `$null` 的陣列。</span><span class="sxs-lookup"><span data-stu-id="f0d78-152">In this case, the `$value` is an array that contains a `$null`.</span></span> <span data-ttu-id="f0d78-153">`-eq` 會檢查陣列中的每個值，並傳回符合的 `$null`。</span><span class="sxs-lookup"><span data-stu-id="f0d78-153">The `-eq` checks every value in the array and returns the `$null` that is matched.</span></span> <span data-ttu-id="f0d78-154">這會評估為 `$false`。</span><span class="sxs-lookup"><span data-stu-id="f0d78-154">This evaluates to `$false`.</span></span> <span data-ttu-id="f0d78-155">`-ne` 會傳回不符合 `$null` 的所有項目，而且在此案例中並沒有任何結果 (這也會評估為 `$false`)。</span><span class="sxs-lookup"><span data-stu-id="f0d78-155">The `-ne` returns everything that doesn't match `$null` and in this case there are no results (This also evaluates to `$false`).</span></span> <span data-ttu-id="f0d78-156">兩個情況都不是 `$true`，即使它們其中一個看起來應該要是。</span><span class="sxs-lookup"><span data-stu-id="f0d78-156">Neither one is `$true` even though it looks like one of them should be.</span></span>

<span data-ttu-id="f0d78-157">我們不僅可以建立一個會讓這兩種情況都評估為 `$false` 的值，也可以建立一個會讓兩個情況都評估為 `$true` 的值。</span><span class="sxs-lookup"><span data-stu-id="f0d78-157">Not only can we create a value that makes both of them evaluate to `$false`, it's possible to create a value where they both evaluate to `$true`.</span></span> <span data-ttu-id="f0d78-158">Mathias Jessen (@IISResetMe) 有一篇深入說明該案例的[絕佳貼文][]。</span><span class="sxs-lookup"><span data-stu-id="f0d78-158">Mathias Jessen (@IISResetMe) has a [good post][] that dives into that scenario.</span></span>

### <a name="psscriptanalyzer-and-vscode"></a><span data-ttu-id="f0d78-159">PSScriptAnalyzer 與 VSCode</span><span class="sxs-lookup"><span data-stu-id="f0d78-159">PSScriptAnalyzer and VSCode</span></span>

<span data-ttu-id="f0d78-160">[PSScriptAnalyzer][] 模組有一個會檢查是否有此問題的規則，名為 `PSPossibleIncorrectComparisonWithNull`。</span><span class="sxs-lookup"><span data-stu-id="f0d78-160">The [PSScriptAnalyzer][] module has a rule that checks for this issue called `PSPossibleIncorrectComparisonWithNull`.</span></span>

```powershell
PS> Invoke-ScriptAnalyzer ./myscript.ps1

RuleName                              Message
--------                              -------
PSPossibleIncorrectComparisonWithNull $null should be on the left side of equality comparisons.
```

<span data-ttu-id="f0d78-161">因為 VS Code 也會使用 PSScriptAnalyser 規則，所以其也會在您的指令碼中將此情況以反白方式顯示，或將其識別為問題。</span><span class="sxs-lookup"><span data-stu-id="f0d78-161">Because VS Code uses the PSScriptAnalyser rules too, it also highlights or identifies this as a problem in your script.</span></span>

### <a name="simple-if-check"></a><span data-ttu-id="f0d78-162">簡單的 if 檢查</span><span class="sxs-lookup"><span data-stu-id="f0d78-162">Simple if check</span></span>

<span data-ttu-id="f0d78-163">人們檢查非 $null 值的一種常見方式是使用簡單的 `if()` 陳述式，而不進行比較。</span><span class="sxs-lookup"><span data-stu-id="f0d78-163">A common way that people check for a non-$null value is to use a simple `if()` statement without the comparison.</span></span>

```powershell
if ( $value )
{
    Do-Something
}
```

<span data-ttu-id="f0d78-164">如果值是 `$null`，這會評估為 `$false`。</span><span class="sxs-lookup"><span data-stu-id="f0d78-164">If the value is `$null`, this evaluates to `$false`.</span></span> <span data-ttu-id="f0d78-165">這很容易閱讀，但請小心，因為其會尋找您預期其尋找的項目。</span><span class="sxs-lookup"><span data-stu-id="f0d78-165">This is easy to read, but be careful that it's looking for exactly what you're expecting it to look for.</span></span> <span data-ttu-id="f0d78-166">我將該程式碼讀為：</span><span class="sxs-lookup"><span data-stu-id="f0d78-166">I read that line of code as:</span></span>

> <span data-ttu-id="f0d78-167">如果 `$value` 有值。</span><span class="sxs-lookup"><span data-stu-id="f0d78-167">If `$value` has a value.</span></span>

<span data-ttu-id="f0d78-168">但這並不完整。</span><span class="sxs-lookup"><span data-stu-id="f0d78-168">But that's not the whole story.</span></span> <span data-ttu-id="f0d78-169">那一行的真正意思應該是：</span><span class="sxs-lookup"><span data-stu-id="f0d78-169">That line is actually saying:</span></span>

> <span data-ttu-id="f0d78-170">如果 `$value` 不是 `$null`、`0`、`$false` 或 `empty string`</span><span class="sxs-lookup"><span data-stu-id="f0d78-170">If `$value` is not `$null` or `0` or `$false` or an `empty string`</span></span>

<span data-ttu-id="f0d78-171">以下是該陳述式的更完整範例。</span><span class="sxs-lookup"><span data-stu-id="f0d78-171">Here is a more complete sample of that statement.</span></span>

```powershell
if ( $null -ne $value -and
        $value -ne 0 -and
        $value -ne '' -and
        $value -ne $false )
{
    Do-Something
}
```

<span data-ttu-id="f0d78-172">只要您記得其他的值會視為 `$false`，而不是只會視為變數具有值，那就可以使用基本的 `if` 檢查。</span><span class="sxs-lookup"><span data-stu-id="f0d78-172">It's perfectly OK to use a basic `if` check as long as you remember those other values count as `$false` and not just that a variable has a value.</span></span>

<span data-ttu-id="f0d78-173">我在幾天前重構一些程式碼時遇到了這個問題。</span><span class="sxs-lookup"><span data-stu-id="f0d78-173">I ran into this issue when refactoring some code a few days ago.</span></span> <span data-ttu-id="f0d78-174">其有一個像這樣的基本屬性檢查。</span><span class="sxs-lookup"><span data-stu-id="f0d78-174">It had a basic property check like this.</span></span>

```powershell
if ( $object.property )
{
    $object.property = $value
}
```

<span data-ttu-id="f0d78-175">我想要指派一個值給物件屬性，如果它存在的話。</span><span class="sxs-lookup"><span data-stu-id="f0d78-175">I wanted to assign a value to the object property only if it existed.</span></span> <span data-ttu-id="f0d78-176">在大部分情況下，原始物件會有一個在 `if` 陳述式中評估為 `$true` 的值。</span><span class="sxs-lookup"><span data-stu-id="f0d78-176">In most cases, the original object had a value that would evaluate to `$true` in the `if` statement.</span></span> <span data-ttu-id="f0d78-177">但我遇到一個偶爾未設定值的問題。</span><span class="sxs-lookup"><span data-stu-id="f0d78-177">But I ran into an issue where the value was occasionally not getting set.</span></span> <span data-ttu-id="f0d78-178">我已對程式碼進行偵錯並發現物件具有屬性，但其為空的字串值。</span><span class="sxs-lookup"><span data-stu-id="f0d78-178">I debugged the code and found that the object had the property but it was a blank string value.</span></span> <span data-ttu-id="f0d78-179">這會讓其無法使用先前的邏輯來更新。</span><span class="sxs-lookup"><span data-stu-id="f0d78-179">This prevented it from ever getting updated with the previous logic.</span></span> <span data-ttu-id="f0d78-180">所以我新增了適當的 `$null` 檢查，然後一切就能正常運作了。</span><span class="sxs-lookup"><span data-stu-id="f0d78-180">So I added a proper `$null` check and everything worked.</span></span>

```powershell
if ( $null -ne $object.property )
{
    $object.property = $value
}
```

<span data-ttu-id="f0d78-181">這是一個和這些錯誤一樣難以找到的小錯誤 (Bug)，因此導致我積極地檢查 `$null` 值。</span><span class="sxs-lookup"><span data-stu-id="f0d78-181">It's little bugs like these that are hard to spot and make me aggressively check values for `$null`.</span></span>

## <a name="nullcount"></a><span data-ttu-id="f0d78-182">$null.Count</span><span class="sxs-lookup"><span data-stu-id="f0d78-182">$null.Count</span></span>

<span data-ttu-id="f0d78-183">如果您嘗試存取 `$null` 值上的屬性，該屬性也會是 `$null`。</span><span class="sxs-lookup"><span data-stu-id="f0d78-183">If you try to access a property on a `$null` value, that the property is also `$null`.</span></span> <span data-ttu-id="f0d78-184">`count` 屬性是此規則的例外。</span><span class="sxs-lookup"><span data-stu-id="f0d78-184">The `count` property is the exception to this rule.</span></span>

```powershell
PS> $value = $null
PS> $value.count
0
```

<span data-ttu-id="f0d78-185">當您有 `$null` 值時，`count` 就會是 `0`。</span><span class="sxs-lookup"><span data-stu-id="f0d78-185">When you have a `$null` value, then the `count` is `0`.</span></span> <span data-ttu-id="f0d78-186">此特殊屬性是由 PowerShell 所新增的。</span><span class="sxs-lookup"><span data-stu-id="f0d78-186">This special property is added by PowerShell.</span></span>

### <a name="pscustomobject-count"></a><span data-ttu-id="f0d78-187">[PSCustomObject] 計數</span><span class="sxs-lookup"><span data-stu-id="f0d78-187">[PSCustomObject] Count</span></span>

<span data-ttu-id="f0d78-188">PowerShell 中幾乎所有物件都有該 count 屬性。</span><span class="sxs-lookup"><span data-stu-id="f0d78-188">Almost all objects in PowerShell have that count property.</span></span> <span data-ttu-id="f0d78-189">Windows PowerShell 5.1 中一個重要的例外是 `[PSCustomObject]` (PowerShell 6.0 中已修正此問題)。</span><span class="sxs-lookup"><span data-stu-id="f0d78-189">One important exception is the `[PSCustomObject]` in Windows PowerShell 5.1 (This is fixed in PowerShell 6.0).</span></span> <span data-ttu-id="f0d78-190">其沒有 count 屬性，因此如果您嘗試加以使用，就會得到 `$null` 值。</span><span class="sxs-lookup"><span data-stu-id="f0d78-190">It doesn't have a count property so you get a `$null` value if you try to use it.</span></span> <span data-ttu-id="f0d78-191">我在這裡說明這件事是要讓您不要嘗試使用 `.Count`，而不執行 `$null` 檢查。</span><span class="sxs-lookup"><span data-stu-id="f0d78-191">I call this out here so that you don't try to use `.Count` instead of a `$null` check.</span></span>

<span data-ttu-id="f0d78-192">在 Windows PowerShell 5.1 與 PowerShell 6.0 上執行此範例會提供不同的結果。</span><span class="sxs-lookup"><span data-stu-id="f0d78-192">Running this example on Windows PowerShell 5.1 and PowerShell 6.0 gives you different results.</span></span>

```powershell
$value = [PSCustomObject]@{Name='MyObject'}
if ( $value.count -eq 1 )
{
    "We have a value"
}
```

## <a name="empty-null"></a><span data-ttu-id="f0d78-193">空白 Null</span><span class="sxs-lookup"><span data-stu-id="f0d78-193">Empty null</span></span>

<span data-ttu-id="f0d78-194">有一種特殊類型的 `$null`，其作用與其他類型不同。</span><span class="sxs-lookup"><span data-stu-id="f0d78-194">There is one special type of `$null` that acts differently than the others.</span></span> <span data-ttu-id="f0d78-195">我要將其命名為空白 `$null`，但它其實是 [System.Management.Automation.Internal.AutomationNull][]。</span><span class="sxs-lookup"><span data-stu-id="f0d78-195">I am going to call it the empty `$null` but it's really a [System.Management.Automation.Internal.AutomationNull][].</span></span> <span data-ttu-id="f0d78-196">這個空的 `$null` 是函式或指令碼區塊未傳回任何內容的結果 (不正確的結果)。</span><span class="sxs-lookup"><span data-stu-id="f0d78-196">This empty `$null` is the one you get as the result of a function or script block that returns nothing (a void result).</span></span>

```powershell
PS> function Get-Nothing {}
PS> $nothing = Get-Nothing
PS> $null -eq $nothing
True
```

<span data-ttu-id="f0d78-197">如果您將其與 `$null` 比較，就會得到 `$null` 值。</span><span class="sxs-lookup"><span data-stu-id="f0d78-197">If you compare it with `$null`, you get a `$null` value.</span></span> <span data-ttu-id="f0d78-198">在需要值的評估中使用時，值一律會是 `$null`。</span><span class="sxs-lookup"><span data-stu-id="f0d78-198">When used in an evaluation where a value is required, the value is always `$null`.</span></span> <span data-ttu-id="f0d78-199">但如果您將其放在陣列中，其就會被視為空陣列。</span><span class="sxs-lookup"><span data-stu-id="f0d78-199">But if you place it inside an array, it's treated the same as an empty array.</span></span>

```powershell
PS> $containempty = @( @() )
PS> $containnothing = @($nothing)
PS> $containnull = @($null)

PS> $containempty.count
0
PS> $containnothing.count
0
PS> $containnull.count
1
```

<span data-ttu-id="f0d78-200">您可以有一個包含一個 `$null` 值，而其 `count` 為 `1` 的陣列。</span><span class="sxs-lookup"><span data-stu-id="f0d78-200">You can have an array that contains one `$null` value and its `count` is `1`.</span></span> <span data-ttu-id="f0d78-201">但是，如果您將空的結果放在陣列中，其就不會被視為項目。</span><span class="sxs-lookup"><span data-stu-id="f0d78-201">But if you place an empty result inside an array then it's not counted as an item.</span></span> <span data-ttu-id="f0d78-202">計數為 `0`。</span><span class="sxs-lookup"><span data-stu-id="f0d78-202">The count is `0`.</span></span>

<span data-ttu-id="f0d78-203">如果您將空 `$null` 視為集合，那其就會是空的。</span><span class="sxs-lookup"><span data-stu-id="f0d78-203">If you treat the empty `$null` like a collection, then it's empty.</span></span>

### <a name="pipeline"></a><span data-ttu-id="f0d78-204">管線</span><span class="sxs-lookup"><span data-stu-id="f0d78-204">Pipeline</span></span>

<span data-ttu-id="f0d78-205">您會看到差異的主要位置是在使用管線時。</span><span class="sxs-lookup"><span data-stu-id="f0d78-205">The primary place you see the difference is when using the pipeline.</span></span> <span data-ttu-id="f0d78-206">您可以使用管線傳送 `$null` 值，但不能傳送空 `$null` 值。</span><span class="sxs-lookup"><span data-stu-id="f0d78-206">You can pipe a `$null` value but not an empty `$null` value.</span></span>

```powershell
PS> $null | ForEach-Object{ Write-Output 'NULL Value' }
'NULL Value'
PS> $nothing | ForEach-Object{ Write-Output 'No Value' }
```

<span data-ttu-id="f0d78-207">視程式碼而定，您應該在邏輯中說明 `$null`。</span><span class="sxs-lookup"><span data-stu-id="f0d78-207">Depending on your code, you should account for the `$null` in your logic.</span></span>

<span data-ttu-id="f0d78-208">請先檢查 `$null`</span><span class="sxs-lookup"><span data-stu-id="f0d78-208">Either check for `$null` first</span></span>

- <span data-ttu-id="f0d78-209">在管線上篩選出 Null (`... | Where {$null -ne $_} | ...`)</span><span class="sxs-lookup"><span data-stu-id="f0d78-209">Filter out null on the pipeline (`... | Where {$null -ne $_} | ...`)</span></span>
- <span data-ttu-id="f0d78-210">在管線函式中加以處理</span><span class="sxs-lookup"><span data-stu-id="f0d78-210">Handle it in the pipeline function</span></span>

## <a name="foreach"></a><span data-ttu-id="f0d78-211">foreach</span><span class="sxs-lookup"><span data-stu-id="f0d78-211">foreach</span></span>

<span data-ttu-id="f0d78-212">`foreach` 的功能之中，我最愛的其中之一就是其不會列舉 `$null` 集合。</span><span class="sxs-lookup"><span data-stu-id="f0d78-212">One of my favorite features of `foreach` is that it doesn't enumerate over a `$null` collection.</span></span>

```powershell
foreach ( $node in $null )
{
    #skipped
}
```

<span data-ttu-id="f0d78-213">這讓我不需要先針對集合進行 `$null` 檢查，再列舉集合。</span><span class="sxs-lookup"><span data-stu-id="f0d78-213">This saves me from having to `$null` check the collection before I enumerate it.</span></span> <span data-ttu-id="f0d78-214">如果您有 `$null` 值的集合，`$node` 仍然可以是 `$null`。</span><span class="sxs-lookup"><span data-stu-id="f0d78-214">If you have a collection of `$null` values, the `$node` can still be `$null`.</span></span>

<span data-ttu-id="f0d78-215">foreach 在 PowerShell 3.0 中已開始以這種方式運作。</span><span class="sxs-lookup"><span data-stu-id="f0d78-215">The foreach started working this way with PowerShell 3.0.</span></span> <span data-ttu-id="f0d78-216">如果您使用的是較舊的版本，就不是這種情況。</span><span class="sxs-lookup"><span data-stu-id="f0d78-216">If you happen to be on an older version, then this is not the case.</span></span> <span data-ttu-id="f0d78-217">這是為了與 2.0 版相容而向後移植程式碼時，必須注意的其中一個重要變更。</span><span class="sxs-lookup"><span data-stu-id="f0d78-217">This is one of the important changes to be aware of when back-porting code for 2.0 compatibility.</span></span>

## <a name="value-types"></a><span data-ttu-id="f0d78-218">實值型別</span><span class="sxs-lookup"><span data-stu-id="f0d78-218">Value types</span></span>

<span data-ttu-id="f0d78-219">就技術而言，只有參考型別可以是 `$null`。</span><span class="sxs-lookup"><span data-stu-id="f0d78-219">Technically, only reference types can be `$null`.</span></span> <span data-ttu-id="f0d78-220">但是 PowerShell 很大方，因此允許任何類型的變數。</span><span class="sxs-lookup"><span data-stu-id="f0d78-220">But PowerShell is very generous and allows for variables to be any type.</span></span> <span data-ttu-id="f0d78-221">如果您決定為實值型別進行強型別處理，那其就不能是 `$null`。</span><span class="sxs-lookup"><span data-stu-id="f0d78-221">If you decide to strongly type a value type, it cannot be `$null`.</span></span>
<span data-ttu-id="f0d78-222">PowerShell 會將 `$null` 轉換成許多型別適用的預設值。</span><span class="sxs-lookup"><span data-stu-id="f0d78-222">PowerShell converts `$null` to a default value for many types.</span></span>

```powershell
PS> [int]$number = $null
PS> $number
0

PS> [bool]$boolean = $null
PS> $boolean
False

PS> [string]$string = $null
PS> $string -eq ''
True
```

<span data-ttu-id="f0d78-223">有些型別並沒有從 `$null` 轉換而來的有效轉換。</span><span class="sxs-lookup"><span data-stu-id="f0d78-223">There are some types that do not have a valid conversion from `$null`.</span></span> <span data-ttu-id="f0d78-224">這些型別會產生 `Cannot convert null to type` 錯誤。</span><span class="sxs-lookup"><span data-stu-id="f0d78-224">These types generate a `Cannot convert null to type` error.</span></span>

```powershell
PS> [datetime]$date = $null
Cannot convert null to type "System.DateTime".
At line:1 char:1
+ [datetime]$date = $null
+ ~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : MetadataError: (:) [], ArgumentTransformationMetadataException
    + FullyQualifiedErrorId : RuntimeException
```

### <a name="function-parameters"></a><span data-ttu-id="f0d78-225">函數參數</span><span class="sxs-lookup"><span data-stu-id="f0d78-225">Function parameters</span></span>

<span data-ttu-id="f0d78-226">在函式參數中使用強型別值是很常見的。</span><span class="sxs-lookup"><span data-stu-id="f0d78-226">Using a strongly typed values in function parameters is very common.</span></span> <span data-ttu-id="f0d78-227">我們通常會學習定義參數的型別，即使我們習慣不在指令碼中定義其他變數的型別也一樣。</span><span class="sxs-lookup"><span data-stu-id="f0d78-227">We generally learn to define the types of our parameters even if we tend not to define the types of other variables in our scripts.</span></span> <span data-ttu-id="f0d78-228">您的函式中可能已經有一些強型別變數，但您甚至沒有意識到。</span><span class="sxs-lookup"><span data-stu-id="f0d78-228">You may already have some strongly typed variables in your functions and not even realize it.</span></span>

```powershell
function Do-Something
{
    param(
        [String] $Value
    )
}
```

<span data-ttu-id="f0d78-229">一旦您將參數的型別設定為 `string`，值就永遠不會是 `$null`。</span><span class="sxs-lookup"><span data-stu-id="f0d78-229">As soon as you set the type of the parameter as a `string`, the value can never be `$null`.</span></span> <span data-ttu-id="f0d78-230">我們經常會檢查某個值是否是 `$null`，以查看使用者是否已提供值。</span><span class="sxs-lookup"><span data-stu-id="f0d78-230">It's common to check if a value is `$null` to see if the user provided a value or not.</span></span>

```powershell
if ( $null -ne $Value ){...}
```

<span data-ttu-id="f0d78-231">如果沒有提供任何值，`$Value` 就會是一個空字串 `''`。</span><span class="sxs-lookup"><span data-stu-id="f0d78-231">`$Value` is an empty string `''` when no value is provided.</span></span> <span data-ttu-id="f0d78-232">請改為使用自動變數 `$PSBoundParameters.Value`。</span><span class="sxs-lookup"><span data-stu-id="f0d78-232">Use the automatic variable `$PSBoundParameters.Value` instead.</span></span>

```powershell
if ( $null -ne $PSBoundParameters.Value ){...}
```

<span data-ttu-id="f0d78-233">`$PSBoundParameters` 只會包含呼叫函式時所指定的參數。</span><span class="sxs-lookup"><span data-stu-id="f0d78-233">`$PSBoundParameters` only contains the parameters that were specified when the function was called.</span></span>
<span data-ttu-id="f0d78-234">您也可以使用 `ContainsKey` 方法來檢查屬性。</span><span class="sxs-lookup"><span data-stu-id="f0d78-234">You can also use the `ContainsKey` method to check for the property.</span></span>

```powershell
if ( $PSBoundParameters.ContainsKey('Value') ){...}
```

### <a name="isnotnullorempty"></a><span data-ttu-id="f0d78-235">IsNotNullOrEmpty</span><span class="sxs-lookup"><span data-stu-id="f0d78-235">IsNotNullOrEmpty</span></span>

<span data-ttu-id="f0d78-236">如果值是字串，您可以使用靜態字串函式來同時檢查值是否為 `$null` 或空字串。</span><span class="sxs-lookup"><span data-stu-id="f0d78-236">If the value is a string, you can use a static string function to check if the value is `$null` or an empty string at the same time.</span></span>

```powershell
if ( -not [string]::IsNullOrEmpty( $value ) ){...}
```

<span data-ttu-id="f0d78-237">當我知道實值型別應該是字串時，才發現我經常會用到。</span><span class="sxs-lookup"><span data-stu-id="f0d78-237">I find myself using this often when I know the value type should be a string.</span></span>

## <a name="when-i-null-check"></a><span data-ttu-id="f0d78-238">當我進行 $null 檢查時</span><span class="sxs-lookup"><span data-stu-id="f0d78-238">When I $null check</span></span>

<span data-ttu-id="f0d78-239">我是一個防禦性高的指令碼作者。</span><span class="sxs-lookup"><span data-stu-id="f0d78-239">I am a defensive scripter.</span></span> <span data-ttu-id="f0d78-240">每當我呼叫函式並將其指派給變數時，都會檢查其是否是 `$null`。</span><span class="sxs-lookup"><span data-stu-id="f0d78-240">Anytime I call a function and assign it to a variable, I check it for `$null`.</span></span>

```powershell
$userList = Get-ADUser kevmar
if ($null -ne $userList){...}
```

<span data-ttu-id="f0d78-241">相較於 `try/catch`，我更喜歡使用 `if` 或 `foreach`。</span><span class="sxs-lookup"><span data-stu-id="f0d78-241">I much prefer using `if` or `foreach` over using `try/catch`.</span></span> <span data-ttu-id="f0d78-242">別誤會我的意思，我還是很常使用 `try/catch` 的。</span><span class="sxs-lookup"><span data-stu-id="f0d78-242">Don't get me wrong, I still use `try/catch` a lot.</span></span> <span data-ttu-id="f0d78-243">但是，如果我可以測試錯誤條件或空的結果集，我可以讓例外狀況處理作業成為處理真正例外狀況的作業。</span><span class="sxs-lookup"><span data-stu-id="f0d78-243">But if I can test for an error condition or an empty set of results, I can allow my exception handling be for true exceptions.</span></span>

<span data-ttu-id="f0d78-244">我也習慣先檢查是否有 `$null`，然後才在物件為值編製索引或呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="f0d78-244">I also tend to check for `$null` before I index into a value or call methods on an object.</span></span> <span data-ttu-id="f0d78-245">這兩個動作會因為 `$null` 物件而失敗，所以我發現先驗證它們是很重要的。</span><span class="sxs-lookup"><span data-stu-id="f0d78-245">These two actions fail for a `$null` object so I find it important to validate them first.</span></span> <span data-ttu-id="f0d78-246">我先前已經在這篇文章中討論過那些案例。</span><span class="sxs-lookup"><span data-stu-id="f0d78-246">I already covered those scenarios earlier in this post.</span></span>

### <a name="no-results-scenario"></a><span data-ttu-id="f0d78-247">無結果案例</span><span class="sxs-lookup"><span data-stu-id="f0d78-247">No results scenario</span></span>

<span data-ttu-id="f0d78-248">請務必了解一點，那就是不同的函式與命令會以不同的方式處理無結果案例。</span><span class="sxs-lookup"><span data-stu-id="f0d78-248">It's important to know that different functions and commands handle the no results scenario differently.</span></span> <span data-ttu-id="f0d78-249">許多 PowerShell 命令都會在錯誤資料流中傳回空的 `$null` 與錯誤。</span><span class="sxs-lookup"><span data-stu-id="f0d78-249">Many PowerShell commands return the empty `$null` and an error in the error stream.</span></span> <span data-ttu-id="f0d78-250">但其他則會擲回例外狀況，或提供狀態物件。</span><span class="sxs-lookup"><span data-stu-id="f0d78-250">But others throw exceptions or give you a status object.</span></span> <span data-ttu-id="f0d78-251">您仍然需要知道自己使用的命令會如何處理無結果與錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="f0d78-251">It's still up to you to know how the commands you use deal with the no results and error scenarios.</span></span>

## <a name="initializing-to-null"></a><span data-ttu-id="f0d78-252">初始化為 $null</span><span class="sxs-lookup"><span data-stu-id="f0d78-252">Initializing to $null</span></span>

<span data-ttu-id="f0d78-253">我養成了一個習慣，那就是先將所有的變數初始化，然後再使用。</span><span class="sxs-lookup"><span data-stu-id="f0d78-253">One habit that I have picked up is initializing all my variables before I use them.</span></span> <span data-ttu-id="f0d78-254">您必須以其他語言執行此動作。</span><span class="sxs-lookup"><span data-stu-id="f0d78-254">You are required to do this in other languages.</span></span> <span data-ttu-id="f0d78-255">在我的函式的最前面，或當我輸入 foreach 迴圈時，我會定義我使用的所有值。</span><span class="sxs-lookup"><span data-stu-id="f0d78-255">At the top of my function or as I enter a foreach loop, I define all the values that I'm using.</span></span>

<span data-ttu-id="f0d78-256">以下是我想要讓您仔細看看的狀況。</span><span class="sxs-lookup"><span data-stu-id="f0d78-256">Here is a scenario that I want you to take a close look at.</span></span> <span data-ttu-id="f0d78-257">這是我之前必須追查的一個錯誤 (Bug) 的範例。</span><span class="sxs-lookup"><span data-stu-id="f0d78-257">It's an example of a bug I had to chase down before.</span></span>

```powershell
function Do-Something
{
    foreach ( $node in 1..6 )
    {
        try
        {
            $result = Get-Something -ID $node
        }
        catch
        {
            Write-Verbose "[$result] not valid"
        }

        if ( $null -ne $result )
        {
            Update-Something $result
        }
    }
}
```

<span data-ttu-id="f0d78-258">這裡預期的是 `Get-Something` 會傳回結果或空 `$null`。</span><span class="sxs-lookup"><span data-stu-id="f0d78-258">The expectation here is that `Get-Something` returns either a result or an empty `$null`.</span></span> <span data-ttu-id="f0d78-259">如果發生錯誤，我們會將其記錄下來。</span><span class="sxs-lookup"><span data-stu-id="f0d78-259">If there is an error, we log it.</span></span> <span data-ttu-id="f0d78-260">然後，我們會先檢查以確定我們已經取得有效結果，然後再加以處理。</span><span class="sxs-lookup"><span data-stu-id="f0d78-260">Then we check to make sure we got a valid result before processing it.</span></span>

<span data-ttu-id="f0d78-261">此程式碼中隱藏的錯誤 (Bug) 是 `Get-Something` 擲回例外狀況，而且未指派值給 `$result`。</span><span class="sxs-lookup"><span data-stu-id="f0d78-261">The bug hiding in this code is when `Get-Something` throws an exception and doesn't assign a value to `$result`.</span></span> <span data-ttu-id="f0d78-262">其會在指派之前失敗，因此甚至不會將 `$null` 指派給 `$result` 變數。</span><span class="sxs-lookup"><span data-stu-id="f0d78-262">It fails before the assignment so we don't even assign `$null` to the `$result` variable.</span></span> <span data-ttu-id="f0d78-263">`$result` 仍然包含先前來自其他反覆項目的有效 `$result`。</span><span class="sxs-lookup"><span data-stu-id="f0d78-263">`$result` still contains the previous valid `$result` from other iterations.</span></span>
<span data-ttu-id="f0d78-264">在此範例中，會 `Update-Something` 以在同一物件上執行多次。</span><span class="sxs-lookup"><span data-stu-id="f0d78-264">`Update-Something` to execute multiple times on the same object in this example.</span></span>

<span data-ttu-id="f0d78-265">我先直接在 foreach 迴圈內部把 `$result` 設定為 `$null`，然後再加以使用來緩解這個問題。</span><span class="sxs-lookup"><span data-stu-id="f0d78-265">I set `$result` to `$null` right inside the foreach loop before I use it to mitigate this issue.</span></span>

```powershell
foreach ( $node in 1..6 )
{
    $result = $null
    try
    {
        ...
```

### <a name="scope-issues"></a><span data-ttu-id="f0d78-266">範圍問題</span><span class="sxs-lookup"><span data-stu-id="f0d78-266">Scope issues</span></span>

<span data-ttu-id="f0d78-267">這也有助於緩解範圍設定問題。</span><span class="sxs-lookup"><span data-stu-id="f0d78-267">This also helps mitigate scoping issues.</span></span> <span data-ttu-id="f0d78-268">在該範例中，我們會在迴圈中不斷重複指派值給 `$result`。</span><span class="sxs-lookup"><span data-stu-id="f0d78-268">In that example, we assign values to `$result` over and over in a loop.</span></span> <span data-ttu-id="f0d78-269">但是，由於 PowerShell 允許來自函式外部的變數值進入目前函式的範圍，因此在函式內將它們初始化可以緩解可能透過該方式引入的錯誤 (Bug)。</span><span class="sxs-lookup"><span data-stu-id="f0d78-269">But because PowerShell allows variable values from outside the function to bleed into the scope of the current function, initializing them inside your function mitigates bugs that can be introduced that way.</span></span>

<span data-ttu-id="f0d78-270">如果函式中未初始化的變數設定為父代範圍中個某個值，該變數就不會是 `$null`。</span><span class="sxs-lookup"><span data-stu-id="f0d78-270">An uninitialized variable in your function is not `$null` if it's set to a value in a parent scope.</span></span>
<span data-ttu-id="f0d78-271">父代範圍可能是另一個函式，其會呼叫您的函式並使用相同的變數名稱。</span><span class="sxs-lookup"><span data-stu-id="f0d78-271">The parent scope could be another function that calls your function and uses the same variable names.</span></span>

<span data-ttu-id="f0d78-272">如果我採用相同的 `Do-something` 範例，並移除迴圈，最後會得到看起來像此範例的結果：</span><span class="sxs-lookup"><span data-stu-id="f0d78-272">If I take that same `Do-something` example and remove the loop, I would end up with something that looks like this example:</span></span>

```powershell
function Invoke-Something
{
    $result = 'ParentScope'
    Do-Something
}

function Do-Something
{
    try
    {
        $result = Get-Something -ID $node
    }
    catch
    {
        Write-Verbose "[$result] not valid"
    }

    if ( $null -ne $result )
    {
        Update-Something $result
    }
}
```

<span data-ttu-id="f0d78-273">如果對 `Get-Something` 的呼叫擲回例外狀況，我執行的 `$null` 檢查就會從 `Invoke-Something` 尋找 `$result`。</span><span class="sxs-lookup"><span data-stu-id="f0d78-273">If the call to `Get-Something` throws an exception, then my `$null` check finds the `$result` from `Invoke-Something`.</span></span> <span data-ttu-id="f0d78-274">將函式內部的值初始化可緩解這個問題。</span><span class="sxs-lookup"><span data-stu-id="f0d78-274">Initializing the value inside your function mitigates this issue.</span></span>

<span data-ttu-id="f0d78-275">為變數命名並不容易，而且通常都會在多個函式中使用相同的變數名稱。</span><span class="sxs-lookup"><span data-stu-id="f0d78-275">Naming variables is hard and it's common for an author to use the same variable names in multiple functions.</span></span> <span data-ttu-id="f0d78-276">我知道我總是使用 `$node`、`$result` 與 `$data`。</span><span class="sxs-lookup"><span data-stu-id="f0d78-276">I know I use `$node`,`$result`,`$data` all the time.</span></span> <span data-ttu-id="f0d78-277">因此，這會使來自其他範圍的變數非常容易出現在不應該出現的位置。</span><span class="sxs-lookup"><span data-stu-id="f0d78-277">So it would be very easy for values from different scopes to show up in places where they should not be.</span></span>

## <a name="redirect-output-to-null"></a><span data-ttu-id="f0d78-278">將輸出重新導向至 $null</span><span class="sxs-lookup"><span data-stu-id="f0d78-278">Redirect output to $null</span></span>

<span data-ttu-id="f0d78-279">我已經在這整篇文章中討論過很多次 `$null` 值，但如果不說一下將輸出重新導向至 `$null`，那這個主題就不算完整。</span><span class="sxs-lookup"><span data-stu-id="f0d78-279">I have been talking about `$null` values for this entire article but the topic is not complete if I didn't mention redirecting output to `$null`.</span></span> <span data-ttu-id="f0d78-280">有時候，有些命令會輸出您想要隱藏的資訊或物件。</span><span class="sxs-lookup"><span data-stu-id="f0d78-280">There are times when you have commands that output information or objects that you want to suppress.</span></span> <span data-ttu-id="f0d78-281">將輸出重新導向至 `$null` 就可以達到您想要的隱藏效果。</span><span class="sxs-lookup"><span data-stu-id="f0d78-281">Redirecting output to `$null` does that.</span></span>

### <a name="out-null"></a><span data-ttu-id="f0d78-282">Out-Null</span><span class="sxs-lookup"><span data-stu-id="f0d78-282">Out-Null</span></span>

<span data-ttu-id="f0d78-283">Out-Null 命令是內建的方法，可將管線資料重新導向到 `$null`。</span><span class="sxs-lookup"><span data-stu-id="f0d78-283">The Out-Null command is the built-in way to redirect pipeline data to `$null`.</span></span>

```powershell
New-Item -Type Directory -Path $path | Out-Null
```

### <a name="assign-to-null"></a><span data-ttu-id="f0d78-284">指派給 $null</span><span class="sxs-lookup"><span data-stu-id="f0d78-284">Assign to $null</span></span>

<span data-ttu-id="f0d78-285">您可以將命令的結果指派給 `$null`，以獲得與使用 `Out-Null` 相同的效果。</span><span class="sxs-lookup"><span data-stu-id="f0d78-285">You can assign the results of a command to `$null` for the same effect as using `Out-Null`.</span></span>

```powershell
$null = New-Item -Type Directory -Path $path
```

<span data-ttu-id="f0d78-286">因為 `$null` 是個常數值，所以您一律不能加以覆寫。</span><span class="sxs-lookup"><span data-stu-id="f0d78-286">Because `$null` is a constant value, you can never overwrite it.</span></span> <span data-ttu-id="f0d78-287">我不喜歡其在我的程式碼中的樣子，但其執行速度通常比 `Out-Null` 快。</span><span class="sxs-lookup"><span data-stu-id="f0d78-287">I don't like the way it looks in my code but it often performs faster than `Out-Null`.</span></span>

### <a name="redirect-to-null"></a><span data-ttu-id="f0d78-288">重新導向至 $null</span><span class="sxs-lookup"><span data-stu-id="f0d78-288">Redirect to $null</span></span>

<span data-ttu-id="f0d78-289">您也可以使用重新導向運算子將輸出傳送至 `$null`。</span><span class="sxs-lookup"><span data-stu-id="f0d78-289">You can also use the redirection operator to send output to `$null`.</span></span>

```powershell
New-Item -Type Directory -Path $path > $null
```

<span data-ttu-id="f0d78-290">如果您處理的是會在不同的資料流上輸出的命令列可執行檔。</span><span class="sxs-lookup"><span data-stu-id="f0d78-290">If you're dealing with command-line executables that output on the different streams.</span></span> <span data-ttu-id="f0d78-291">您可以將所有輸出資料流重新導向至 `$null`，就像這樣：</span><span class="sxs-lookup"><span data-stu-id="f0d78-291">You can redirect all output streams to `$null` like this:</span></span>

```powershell
git status *> $null
```

## <a name="summary"></a><span data-ttu-id="f0d78-292">摘要</span><span class="sxs-lookup"><span data-stu-id="f0d78-292">Summary</span></span>

<span data-ttu-id="f0d78-293">我已經討論過很多與此項目有關的基礎，而且我知道這篇文章的內容比我大多數的深入探討文章更分散。</span><span class="sxs-lookup"><span data-stu-id="f0d78-293">I covered a lot of ground on this one and I know this article is more fragmented than most of my deep dives.</span></span> <span data-ttu-id="f0d78-294">這是因為 `$null` 值可能會在 PowerShell 中的許多不同位置出現，而且所有細微差異都會是在找到它的位置特定的。</span><span class="sxs-lookup"><span data-stu-id="f0d78-294">That is because `$null` values can pop up in many different places in PowerShell and all the nuances are specific to where you find it.</span></span> <span data-ttu-id="f0d78-295">我希望您能夠進一步了解 `$null`，並知道您可能會遇到更晦澀的狀況，進而擺脫掉這個問題。</span><span class="sxs-lookup"><span data-stu-id="f0d78-295">I hope you walk away from this with a better understanding of `$null` and an awareness of the more obscure scenarios you may run into.</span></span>

<!-- link references -->
[原始版本]: https://powershellexplained.com/2018-12-23-Powershell-null-everything-you-wanted-to-know/
[original version]: https://powershellexplained.com/2018-12-23-Powershell-null-everything-you-wanted-to-know/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[絕佳貼文]: https://blog.iisreset.me/schrodingers-argumentlist
[good post]: https://blog.iisreset.me/schrodingers-argumentlist
[PSScriptAnalyzer]: https://www.powershellgallery.com/packages/PSScriptAnalyzer
[System.Management.Automation.Internal.AutomationNull]: /dotnet/api/system.management.automation.internal.automationnull
