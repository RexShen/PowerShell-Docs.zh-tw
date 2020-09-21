---
title: 如何在字串中替代變數
description: 在字串中使用變數來建立格式化文字的方法很多。
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 786526fb98dbf1b3ec7c5c6c985ac95b85a96259
ms.sourcegitcommit: 4bb44f183dcbfa8dced57f075812e02d3b45fd70
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86301313"
---
# <a name="everything-you-wanted-to-know-about-variable-substitution-in-strings"></a><span data-ttu-id="b71b9-103">如何在字串中替代變數</span><span class="sxs-lookup"><span data-stu-id="b71b9-103">Everything you wanted to know about variable substitution in strings</span></span>

<span data-ttu-id="b71b9-104">在字串中使用變數的方法很多。</span><span class="sxs-lookup"><span data-stu-id="b71b9-104">There are many ways to use variables in strings.</span></span> <span data-ttu-id="b71b9-105">這裡所謂的「替代變數」，其實是指將字串格式化以包含變數值的任何情況。</span><span class="sxs-lookup"><span data-stu-id="b71b9-105">I'm calling this variable substitution but I'm referring to any time you want to format a string to include values from variables.</span></span> <span data-ttu-id="b71b9-106">這是指令碼撰寫新手要注意的部分。</span><span class="sxs-lookup"><span data-stu-id="b71b9-106">This is something that I often find myself explaining to new scripters.</span></span>

> [!NOTE]
> <span data-ttu-id="b71b9-107">此[原文][]出自 [@KevinMarquette][] 所撰寫的部落格。</span><span class="sxs-lookup"><span data-stu-id="b71b9-107">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="b71b9-108">PowerShell 小組感謝 Kevin 分享此內容。</span><span class="sxs-lookup"><span data-stu-id="b71b9-108">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="b71b9-109">請前往 [PowerShellExplained.com][] 瀏覽他的部落格。</span><span class="sxs-lookup"><span data-stu-id="b71b9-109">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="concatenation"></a><span data-ttu-id="b71b9-110">串連</span><span class="sxs-lookup"><span data-stu-id="b71b9-110">Concatenation</span></span>

<span data-ttu-id="b71b9-111">第一種方法可稱為串連。</span><span class="sxs-lookup"><span data-stu-id="b71b9-111">The first class of methods can be referred to as concatenation.</span></span> <span data-ttu-id="b71b9-112">基本上，這種方法就是把好幾個字串聯結在一起。</span><span class="sxs-lookup"><span data-stu-id="b71b9-112">It's basically taking several strings and joining them together.</span></span> <span data-ttu-id="b71b9-113">使用串連來建置格式化字串是一個已經行之有年的方法。</span><span class="sxs-lookup"><span data-stu-id="b71b9-113">There's a long history of using concatenation to build formatted strings.</span></span>

```powershell
$name = 'Kevin Marquette'
$message = 'Hello, ' + $name
```

<span data-ttu-id="b71b9-114">若只有要新增幾個值，串連不會有什麼大問題。</span><span class="sxs-lookup"><span data-stu-id="b71b9-114">Concatenation works out OK when there are only a few values to add.</span></span> <span data-ttu-id="b71b9-115">但通常很快就會變得複雜。</span><span class="sxs-lookup"><span data-stu-id="b71b9-115">But this can get complicated quickly.</span></span>

```powershell
$first = 'Kevin'
$last = 'Marquette'
```

```powershell
$message = 'Hello, ' + $first + ' ' + $last + '.'
```

<span data-ttu-id="b71b9-116">這個簡單的範例已經沒那麼一目了然。</span><span class="sxs-lookup"><span data-stu-id="b71b9-116">This simple example is already getting harder to read.</span></span>

## <a name="variable-substitution"></a><span data-ttu-id="b71b9-117">變數替代</span><span class="sxs-lookup"><span data-stu-id="b71b9-117">Variable substitution</span></span>

<span data-ttu-id="b71b9-118">PowerShell 提供另一種更輕鬆的選項。</span><span class="sxs-lookup"><span data-stu-id="b71b9-118">PowerShell has another option that is easier.</span></span> <span data-ttu-id="b71b9-119">您可以直接在字串中指定變數。</span><span class="sxs-lookup"><span data-stu-id="b71b9-119">You can specify your variables directly in the strings.</span></span>

```powershell
$message = "Hello, $first $last."
```

<span data-ttu-id="b71b9-120">也可以使用不同引號類型括住字串，達到不同作用。</span><span class="sxs-lookup"><span data-stu-id="b71b9-120">The type of quotes you use around the string makes a difference.</span></span> <span data-ttu-id="b71b9-121">使用雙引號括住的字串可進行替代，但用單引號的字串則否。</span><span class="sxs-lookup"><span data-stu-id="b71b9-121">A double quoted string allows the substitution but a single quoted string doesn't.</span></span> <span data-ttu-id="b71b9-122">您可以自行選擇要使用哪一種。</span><span class="sxs-lookup"><span data-stu-id="b71b9-122">There are times you want one or the other so you have an option.</span></span>

## <a name="command-substitution"></a><span data-ttu-id="b71b9-123">常見替代</span><span class="sxs-lookup"><span data-stu-id="b71b9-123">Command substitution</span></span>

<span data-ttu-id="b71b9-124">當您開始嘗試將屬性的值放入字串時，就會遇到一點麻煩了。</span><span class="sxs-lookup"><span data-stu-id="b71b9-124">Things get a little tricky when you start trying to get the values of properties into a string.</span></span> <span data-ttu-id="b71b9-125">很多新手都是卡在這一關。</span><span class="sxs-lookup"><span data-stu-id="b71b9-125">This is where many new people get tripped up.</span></span> <span data-ttu-id="b71b9-126">首先我會示範一般新手認為可以運作的內容 (而且乍看之下，這樣的值也應該沒有問題)。</span><span class="sxs-lookup"><span data-stu-id="b71b9-126">First let me show you what they think should work (and at face value almost looks like it should).</span></span>

```powershell
$directory = Get-Item 'c:\windows'
$message = "Time: $directory.CreationTime"
```

<span data-ttu-id="b71b9-127">您以為可以得到 `$directory` 的 `CreationTime`，但卻得到 `Time: c:\windows.CreationTime` 值。</span><span class="sxs-lookup"><span data-stu-id="b71b9-127">You would be expecting to get the `CreationTime` off of the `$directory`, but instead you get this `Time: c:\windows.CreationTime` as your value.</span></span> <span data-ttu-id="b71b9-128">主要是因為這種類型的替代只會使用基底變數。</span><span class="sxs-lookup"><span data-stu-id="b71b9-128">The reason is that this type of substitution only sees the base variable.</span></span> <span data-ttu-id="b71b9-129">其會將句點視為字串的一部分，所以不會更深入地解析值。</span><span class="sxs-lookup"><span data-stu-id="b71b9-129">It considers the period as part of the string so it stops resolving the value any deeper.</span></span>

<span data-ttu-id="b71b9-130">所以當您將這個物件放入字串時，會提供字串作為預設值。</span><span class="sxs-lookup"><span data-stu-id="b71b9-130">It just so happens that this object gives a string as a default value when placed into a string.</span></span>
<span data-ttu-id="b71b9-131">反之，有些物件會提供類型名稱，例如 `System.Collections.Hashtable`。</span><span class="sxs-lookup"><span data-stu-id="b71b9-131">Some objects give you the type name instead like `System.Collections.Hashtable`.</span></span> <span data-ttu-id="b71b9-132">這都是您要小心的地方。</span><span class="sxs-lookup"><span data-stu-id="b71b9-132">Just something to watch for.</span></span>

<span data-ttu-id="b71b9-133">PowerShell 可讓您使用特殊語法在字串內執行命令。</span><span class="sxs-lookup"><span data-stu-id="b71b9-133">PowerShell allows you to do command execution inside the string with a special syntax.</span></span> <span data-ttu-id="b71b9-134">這可讓我們取得這些物件的屬性，並執行任何其他命令來取得值。</span><span class="sxs-lookup"><span data-stu-id="b71b9-134">This allows us to get the properties of these objects and run any other command to get a value.</span></span>

```powershell
$message = "Time: $($directory.CreationTime)"
```

<span data-ttu-id="b71b9-135">有些情況很適合這麼做，但即使只有幾個變數，也可能像串連一樣越變越複雜。</span><span class="sxs-lookup"><span data-stu-id="b71b9-135">This works great for some situations but it can get just as crazy as concatenation if you have just a few variables.</span></span>

### <a name="command-execution"></a><span data-ttu-id="b71b9-136">命令執行</span><span class="sxs-lookup"><span data-stu-id="b71b9-136">Command execution</span></span>

<span data-ttu-id="b71b9-137">您可以在字串內執行命令。</span><span class="sxs-lookup"><span data-stu-id="b71b9-137">You can run commands inside a string.</span></span> <span data-ttu-id="b71b9-138">不過，即使有這個選項，我也不想用。</span><span class="sxs-lookup"><span data-stu-id="b71b9-138">Even though I have this option, I don't like it.</span></span> <span data-ttu-id="b71b9-139">因為內容很快就會變得雜亂無章，很難偵錯。</span><span class="sxs-lookup"><span data-stu-id="b71b9-139">It gets cluttered quickly and hard to debug.</span></span> <span data-ttu-id="b71b9-140">我會執行命令並儲存至變數，或使用格式字串。</span><span class="sxs-lookup"><span data-stu-id="b71b9-140">I either run the command and save to a variable or use a format string.</span></span>

```powershell
$message = "Date: $(Get-Date)"
```

## <a name="format-string"></a><span data-ttu-id="b71b9-141">格式字串</span><span class="sxs-lookup"><span data-stu-id="b71b9-141">Format string</span></span>

<span data-ttu-id="b71b9-142">.NET 的格式化字串方法，我認為滿好用的。</span><span class="sxs-lookup"><span data-stu-id="b71b9-142">.NET has a way to format strings that I find fairly easy to work with.</span></span> <span data-ttu-id="b71b9-143">首先，我會示範靜態方法，接著再示範如何使用 PowerShell 快捷方式來執行相同的動作。</span><span class="sxs-lookup"><span data-stu-id="b71b9-143">First let me show you the static method for it before I show you the PowerShell shortcut to do the same thing.</span></span>

```powershell
# .NET string format string
[string]::Format('Hello, {0} {1}.',$first,$last)

# PowerShell format string
'Hello, {0} {1}.' -f $first, $last
```

<span data-ttu-id="b71b9-144">在這個範例中，系統會剖析字串以尋找 `{0}` 和 `{1}` 權杖，然後使用該數字從提供的值中挑選。</span><span class="sxs-lookup"><span data-stu-id="b71b9-144">What is happening here is that the string is parsed for the tokens `{0}` and `{1}`, then it uses that number to pick from the values provided.</span></span> <span data-ttu-id="b71b9-145">若您想要在字串中重複某位置的一個值，您可以重複使用該值數字。</span><span class="sxs-lookup"><span data-stu-id="b71b9-145">If you want to repeat one value some place in the string, you can reuse that values number.</span></span>

<span data-ttu-id="b71b9-146">字串越複雜，使用這個方法就有越顯著的優勢。</span><span class="sxs-lookup"><span data-stu-id="b71b9-146">The more complicated the string gets, the more value you get out of this approach.</span></span>

### <a name="format-values-as-arrays"></a><span data-ttu-id="b71b9-147">將值格式化為陣列</span><span class="sxs-lookup"><span data-stu-id="b71b9-147">Format values as arrays</span></span>

<span data-ttu-id="b71b9-148">若您的格式行太長，您可以先將值放入陣列中。</span><span class="sxs-lookup"><span data-stu-id="b71b9-148">If your format line gets too long, you can place your values into an array first.</span></span>

```powershell
$values = @(
    "Kevin"
    "Marquette"
)
'Hello, {0} {1}.' -f $values
```

<span data-ttu-id="b71b9-149">這個範例不是展開，因為我要將整個陣列傳入，但概念很類似。</span><span class="sxs-lookup"><span data-stu-id="b71b9-149">This is not splatting because I'm passing the whole array in, but the idea is similar.</span></span>

## <a name="advanced-formatting"></a><span data-ttu-id="b71b9-150">進階格式</span><span class="sxs-lookup"><span data-stu-id="b71b9-150">Advanced formatting</span></span>

<span data-ttu-id="b71b9-151">我必須強調這些功能都是來自 .NET，因為其中許多格式設定選項都已有相當完整的[記載說明][]，</span><span class="sxs-lookup"><span data-stu-id="b71b9-151">I intentionally called these out as coming from .NET because there are lots of formatting options already well [documented][] on it.</span></span> <span data-ttu-id="b71b9-152">也有內建的方法可以格式化各種資料類型。</span><span class="sxs-lookup"><span data-stu-id="b71b9-152">There are built in ways to format various data types.</span></span>

```powershell
"{0:yyyyMMdd}" -f (Get-Date)
"Population {0:N0}" -f  8175133
```

<span data-ttu-id="b71b9-153">我並不打算詳細說明這些方式，只是想讓您知道，這是一款非常強大的格式化引擎。</span><span class="sxs-lookup"><span data-stu-id="b71b9-153">I'm not going to go into them but I just wanted to let you know that this is a very powerful formatting engine if you need it.</span></span>

## <a name="joining-strings"></a><span data-ttu-id="b71b9-154">聯結字串</span><span class="sxs-lookup"><span data-stu-id="b71b9-154">Joining strings</span></span>

<span data-ttu-id="b71b9-155">有時候您會想要將值清單串連在一起。</span><span class="sxs-lookup"><span data-stu-id="b71b9-155">Sometimes you actually do want to concatenate a list of values together.</span></span> <span data-ttu-id="b71b9-156">您可以使用 `-join` 運算子執行這個動作。</span><span class="sxs-lookup"><span data-stu-id="b71b9-156">There's a `-join` operator that can do that for you.</span></span> <span data-ttu-id="b71b9-157">該運算子甚至可讓您指定要在字串之間聯結的字元。</span><span class="sxs-lookup"><span data-stu-id="b71b9-157">It even lets you specify a character to join between the strings.</span></span>

```powershell
$servers = @(
    'server1'
    'server2'
    'server3'
)

$servers  -join ','
```

<span data-ttu-id="b71b9-158">若要 `-join` 一些字串而不含分隔符號，您必須指定空字串 `''`。</span><span class="sxs-lookup"><span data-stu-id="b71b9-158">If you want to `-join` some strings without a separator, you need to specify an empty string `''`.</span></span>
<span data-ttu-id="b71b9-159">但如果您只要做到這樣就夠了，還有更快的方法。</span><span class="sxs-lookup"><span data-stu-id="b71b9-159">But if that is all you need, there's a faster option.</span></span>

```powershell
[string]::Concat('server1','server2','server3')
[string]::Concat($servers)
```

<span data-ttu-id="b71b9-160">順帶一提，您也可以將字串 `-split`。</span><span class="sxs-lookup"><span data-stu-id="b71b9-160">It's also worth pointing out that you can also `-split` strings too.</span></span>

## <a name="join-path"></a><span data-ttu-id="b71b9-161">Join-Path</span><span class="sxs-lookup"><span data-stu-id="b71b9-161">Join-Path</span></span>

<span data-ttu-id="b71b9-162">大家很容易忽略這個建置檔案路徑的絕佳 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b71b9-162">This is often overlooked but a great cmdlet for building a file path.</span></span>

```powershell
$folder = 'Temp'
Join-Path -Path 'c:\windows' -ChildPath $folder
```

<span data-ttu-id="b71b9-163">這個 Cmdlet 的最大優點是可以正確處理多個值當中的反斜線。</span><span class="sxs-lookup"><span data-stu-id="b71b9-163">The great thing about this is it works out the backslashes correctly when it puts the values together.</span></span> <span data-ttu-id="b71b9-164">若您要從使用者或設定檔取得值，這就特別重要。</span><span class="sxs-lookup"><span data-stu-id="b71b9-164">This is especially important if you are taking values from users or config files.</span></span>

<span data-ttu-id="b71b9-165">這也適用於 `Split-Path` 和 `Test-Path`。</span><span class="sxs-lookup"><span data-stu-id="b71b9-165">This also goes well with `Split-Path` and `Test-Path`.</span></span> <span data-ttu-id="b71b9-166">我在[讀取和儲存至檔案][]文章中也會說明這些內容。</span><span class="sxs-lookup"><span data-stu-id="b71b9-166">I also cover these in my post about [reading and saving to files][].</span></span>

## <a name="strings-are-arrays"></a><span data-ttu-id="b71b9-167">字串為陣列</span><span class="sxs-lookup"><span data-stu-id="b71b9-167">Strings are arrays</span></span>

<span data-ttu-id="b71b9-168">在繼續之前，我必須先說明一下何謂新增字串。</span><span class="sxs-lookup"><span data-stu-id="b71b9-168">I do need to mention adding strings here before I go on.</span></span> <span data-ttu-id="b71b9-169">其實字串就是一個字元陣列。</span><span class="sxs-lookup"><span data-stu-id="b71b9-169">Remember that a string is just an array of characters.</span></span> <span data-ttu-id="b71b9-170">當您新增多個字串時，每次都會建立新的陣列。</span><span class="sxs-lookup"><span data-stu-id="b71b9-170">When you add multiple strings together, a new array is created each time.</span></span>

<span data-ttu-id="b71b9-171">請看一下這個範例：</span><span class="sxs-lookup"><span data-stu-id="b71b9-171">Look at this example:</span></span>

```powershell
$message = "Numbers: "
foreach($number in 1..10000)
{
    $message += " $number"
}
```

<span data-ttu-id="b71b9-172">這看似很基本，但您不知道的是，每將一個字串新增到 `$message` 時，就會建立一整個新的字串。</span><span class="sxs-lookup"><span data-stu-id="b71b9-172">It looks very basic but what you don't see is that each time a string is added to `$message` that a whole new string is created.</span></span> <span data-ttu-id="b71b9-173">系統會配置記憶體、複製資料，並將舊的字串捨棄。</span><span class="sxs-lookup"><span data-stu-id="b71b9-173">Memory gets allocated, data gets copied and the old one is discarded.</span></span>
<span data-ttu-id="b71b9-174">若只要重複幾次倒沒什麼問題，但這樣的迴圈仍可能爆出問題。</span><span class="sxs-lookup"><span data-stu-id="b71b9-174">Not a big deal when it's only done a few times, but a loop like this would really expose the issue.</span></span>

### <a name="stringbuilder"></a><span data-ttu-id="b71b9-175">StringBuilder</span><span class="sxs-lookup"><span data-stu-id="b71b9-175">StringBuilder</span></span>

<span data-ttu-id="b71b9-176">當您要從許多較小的字串建立大型字串時，StringBuilder 也是非常熱門的選擇。</span><span class="sxs-lookup"><span data-stu-id="b71b9-176">StringBuilder is also very popular for building large strings from lots of smaller strings.</span></span> <span data-ttu-id="b71b9-177">因為 StringBuilder 只會收集您新增至其中的所有字串，並在您最後要擷取值時，才會將字串全部串連起來。</span><span class="sxs-lookup"><span data-stu-id="b71b9-177">The reason why is because it just collects all the strings you add to it and only concatenates all of them at the end when you retrieve the value.</span></span>

```powershell
$stringBuilder = New-Object -TypeName "System.Text.StringBuilder"

[void]$stringBuilder.Append("Numbers: ")
foreach($number in 1..10000)
{
    [void]$stringBuilder.Append(" $number")
}
$message = $stringBuilder.ToString()
```

<span data-ttu-id="b71b9-178">同樣地，這也是我特別推薦的 .NET 功能。</span><span class="sxs-lookup"><span data-stu-id="b71b9-178">Again, this is something that I'm reaching out to .NET for.</span></span> <span data-ttu-id="b71b9-179">雖然我並不常用，但知道有這個功能也挺不錯的。</span><span class="sxs-lookup"><span data-stu-id="b71b9-179">I don't use it often anymore but it's good to know it's there.</span></span>

## <a name="delineation-with-braces"></a><span data-ttu-id="b71b9-180">以大括弧區隔</span><span class="sxs-lookup"><span data-stu-id="b71b9-180">Delineation with braces</span></span>

<span data-ttu-id="b71b9-181">這種做法主要用於字串內的尾碼串連。</span><span class="sxs-lookup"><span data-stu-id="b71b9-181">This is used for suffix concatenation within the string.</span></span> <span data-ttu-id="b71b9-182">因為變數的字邊界有時候不太明確。</span><span class="sxs-lookup"><span data-stu-id="b71b9-182">Sometimes your variable doesn't have a clean word boundary.</span></span>

```powershell
$test = "Bet"
$tester = "Better"
Write-Host "$test $tester ${test}ter"
```

<span data-ttu-id="b71b9-183">感謝 [/u/real_parbold][] 提供範例。</span><span class="sxs-lookup"><span data-stu-id="b71b9-183">Thank you [/u/real_parbold][] for that one.</span></span>

<span data-ttu-id="b71b9-184">以下是這種方法的替代方式：</span><span class="sxs-lookup"><span data-stu-id="b71b9-184">Here is an alternate to this approach:</span></span>

```powershell
Write-Host "$test $tester $($test)ter"
Write-Host "{0} {1} {0}ter" -f $test, $tester
```

<span data-ttu-id="b71b9-185">我個人會使用格式字串來進行這項工作，但多了解一種做法對您也很有幫助。</span><span class="sxs-lookup"><span data-stu-id="b71b9-185">I personally use format string for this, but this is good to know incase you see it in the wild.</span></span>

## <a name="find-and-replace-tokens"></a><span data-ttu-id="b71b9-186">尋找和取代權杖</span><span class="sxs-lookup"><span data-stu-id="b71b9-186">Find and replace tokens</span></span>

<span data-ttu-id="b71b9-187">雖然這裡提的大部分功能都可讓您盡量不用翻遍解決方案，但有時候您的範本檔案可能很大，而您想要取代其中的字串。</span><span class="sxs-lookup"><span data-stu-id="b71b9-187">While most of these features limit your need to roll your own solution, there are times where you may have large template files where you want to replace strings inside.</span></span>

<span data-ttu-id="b71b9-188">假設您已從含大量文字的檔案中提取範本。</span><span class="sxs-lookup"><span data-stu-id="b71b9-188">Let us assume you pulled in a template from a file that has a lot of text.</span></span>

```powershell
$letter = Get-Content -Path TemplateLetter.txt -RAW
$letter = $letter -replace '#FULL_NAME#', 'Kevin Marquette'
```

<span data-ttu-id="b71b9-189">您可能必須取代一大堆權杖。</span><span class="sxs-lookup"><span data-stu-id="b71b9-189">You may have lots of tokens to replace.</span></span> <span data-ttu-id="b71b9-190">訣竅是使用非常明顯且易於尋找和取代的權杖。</span><span class="sxs-lookup"><span data-stu-id="b71b9-190">The trick is to use a very distinct token that is easy to find and replace.</span></span> <span data-ttu-id="b71b9-191">我通常會在兩端使用特殊字元以利辨別。</span><span class="sxs-lookup"><span data-stu-id="b71b9-191">I tend to use a special character at both ends to help distinguish it.</span></span>

<span data-ttu-id="b71b9-192">不過，我最近發現了一種新的方法。</span><span class="sxs-lookup"><span data-stu-id="b71b9-192">I recently found a new way to approach this.</span></span> <span data-ttu-id="b71b9-193">我就順便在這裡說明一下，因為這是常用的模式。</span><span class="sxs-lookup"><span data-stu-id="b71b9-193">I decided to leave this section in here because this is a pattern that is commonly used.</span></span>

### <a name="replace-multiple-tokens"></a><span data-ttu-id="b71b9-194">取代多個權杖</span><span class="sxs-lookup"><span data-stu-id="b71b9-194">Replace multiple tokens</span></span>

<span data-ttu-id="b71b9-195">當手邊有需要取代的權杖清單時，我會採用一般的方法。</span><span class="sxs-lookup"><span data-stu-id="b71b9-195">When I have a list of tokens that I need to replace, I take a more generic approach.</span></span> <span data-ttu-id="b71b9-196">我會將這些權杖放在雜湊表中，然後逐一查看以進行取代。</span><span class="sxs-lookup"><span data-stu-id="b71b9-196">I would place them in a hashtable and iterate over them to do the replace.</span></span>

```powershell
$tokenList = @{
    Full_Name = 'Kevin Marquette'
    Location = 'Orange County'
    State = 'CA'
}

$letter = Get-Content -Path TemplateLetter.txt -RAW
foreach( $token in $tokenList.GetEnumerator() )
{
    $pattern = '#{0}#' -f $token.key
    $letter = $letter -replace $pattern, $token.Value
}
```

<span data-ttu-id="b71b9-197">您可以視需要從 JSON 或 CSV 載入這些權杖。</span><span class="sxs-lookup"><span data-stu-id="b71b9-197">Those tokens could be loaded from JSON or CSV if needed.</span></span>

### <a name="executioncontext-expandstring"></a><span data-ttu-id="b71b9-198">ExecutionCoNtext ExpandString</span><span class="sxs-lookup"><span data-stu-id="b71b9-198">ExecutionContext ExpandString</span></span>

<span data-ttu-id="b71b9-199">有個妙計是使用單引號來定義替代字串，稍後再展開變數。</span><span class="sxs-lookup"><span data-stu-id="b71b9-199">There's a clever way to define a substitution string with single quotes and expand the variables later.</span></span> <span data-ttu-id="b71b9-200">請看一下這個範例：</span><span class="sxs-lookup"><span data-stu-id="b71b9-200">Look at this example:</span></span>

```powershell
$message = 'Hello, $Name!'
$name = 'Kevin Marquette'
$string = $ExecutionContext.InvokeCommand.ExpandString($message)
```

<span data-ttu-id="b71b9-201">當您對目前的執行內容呼叫 `.InvokeCommand.ExpandString` 時，系統會使用目前範圍中的變數來進行替代。</span><span class="sxs-lookup"><span data-stu-id="b71b9-201">The call to `.InvokeCommand.ExpandString` on the current execution context uses the variables in the current scope for substitution.</span></span> <span data-ttu-id="b71b9-202">值得注意的是，您甚至可以在變數存在之前就先定義 `$message`。</span><span class="sxs-lookup"><span data-stu-id="b71b9-202">The key thing here is that the `$message` can be defined very early before the variables even exist.</span></span>

<span data-ttu-id="b71b9-203">若再延伸一下，我們可以使用不同的值不斷執行這種替代。</span><span class="sxs-lookup"><span data-stu-id="b71b9-203">If we expand on that just a little bit, we can perform this substitution over and over wih different values.</span></span>

```powershell
$message = 'Hello, $Name!'
$nameList = 'Mark Kraus','Kevin Marquette','Lee Dailey'
foreach($name in $nameList){
    $ExecutionContext.InvokeCommand.ExpandString($message)
}
```

<span data-ttu-id="b71b9-204">若要進一步延伸這個概念，您可以從文字檔匯入大型電子郵件範本來執行此動作。</span><span class="sxs-lookup"><span data-stu-id="b71b9-204">To keep going on this idea; you could be importing a large email template from a text file to do this.</span></span> <span data-ttu-id="b71b9-205">感謝 [Mark Kraus][] 提供這個[建議][]。</span><span class="sxs-lookup"><span data-stu-id="b71b9-205">I have to thank [Mark Kraus][] for this [suggestion][].</span></span>

## <a name="whatever-works-the-best-for-you"></a><span data-ttu-id="b71b9-206">適合的方法最好</span><span class="sxs-lookup"><span data-stu-id="b71b9-206">Whatever works the best for you</span></span>

<span data-ttu-id="b71b9-207">我個人是格式字串方法的粉絲。</span><span class="sxs-lookup"><span data-stu-id="b71b9-207">I'm a fan of the format string approach.</span></span> <span data-ttu-id="b71b9-208">遇到更複雜的字串或多個變數時，我一定會採用這個方法。</span><span class="sxs-lookup"><span data-stu-id="b71b9-208">I definitely do this with the more complicated strings or if there are multiple variables.</span></span> <span data-ttu-id="b71b9-209">不過若要處理的內容很簡短，我就會採用本文提到的任何一種方法。</span><span class="sxs-lookup"><span data-stu-id="b71b9-209">On anything that is very short, I may use any one of these.</span></span>

## <a name="anything-else"></a><span data-ttu-id="b71b9-210">還想知道什麼嗎？</span><span class="sxs-lookup"><span data-stu-id="b71b9-210">Anything else?</span></span>

<span data-ttu-id="b71b9-211">針對這個主題，我快速把重點都講完了。</span><span class="sxs-lookup"><span data-stu-id="b71b9-211">I covered a lot of ground on this one.</span></span> <span data-ttu-id="b71b9-212">希望您有學到一點新東西。</span><span class="sxs-lookup"><span data-stu-id="b71b9-212">My hope is that you walk away learning something new.</span></span>

<!-- link references -->
[原文]: https://powershellexplained.com/2017-01-13-powershell-variable-substitution-in-strings/
[original version]: https://powershellexplained.com/2017-01-13-powershell-variable-substitution-in-strings/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Mark Kraus]: https://get-powershellblog.blogspot.com/
[建議]: https://www.reddit.com/r/PowerShell/comments/5npf8h/kevmar_everything_you_wanted_to_know_about/dcdfia5/
[suggestion]: https://www.reddit.com/r/PowerShell/comments/5npf8h/kevmar_everything_you_wanted_to_know_about/dcdfia5/
[/u/real_parbold]: https://www.reddit.com/r/PowerShell/comments/5npf8h/kevmar_everything_you_wanted_to_know_about/dcdfm6p/
[讀取和儲存至檔案]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files/
[reading and saving to files]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files/
[記載說明]: /dotnet/api/system.string.format#overloads
[documented]: /dotnet/api/system.string.format#overloads
