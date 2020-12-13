---
title: 您想知道有關於陣列的一切
description: 陣列是大部分程式設計語言的基礎語言功能。
ms.date: 10/08/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: b26aa11aadbeea1984b2754cfcad061c7fa3ff1e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "91852556"
---
# <a name="everything-you-wanted-to-know-about-arrays"></a><span data-ttu-id="b9585-103">您想知道有關於陣列的一切</span><span class="sxs-lookup"><span data-stu-id="b9585-103">Everything you wanted to know about arrays</span></span>

<span data-ttu-id="b9585-104">[陣列][]是大部分程式設計語言的基礎語言功能。</span><span class="sxs-lookup"><span data-stu-id="b9585-104">[Arrays][] are a fundamental language feature of most programming languages.</span></span> <span data-ttu-id="b9585-105">陣列是不容易規避的值或物件的集合。</span><span class="sxs-lookup"><span data-stu-id="b9585-105">They're a collection of values or objects that are difficult to avoid.</span></span> <span data-ttu-id="b9585-106">讓我們詳細檢視陣列及其所提供的一切功能。</span><span class="sxs-lookup"><span data-stu-id="b9585-106">Let's take a close look at arrays and everything they have to offer.</span></span>

> [!NOTE]
> <span data-ttu-id="b9585-107">本文的[原始版本][]出自 [@KevinMarquette][] 所撰寫的部落格。</span><span class="sxs-lookup"><span data-stu-id="b9585-107">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="b9585-108">PowerShell 小組感謝 Kevin 分享的內容。</span><span class="sxs-lookup"><span data-stu-id="b9585-108">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="b9585-109">請前往 [PowerShellExplained.com][] 瀏覽他的部落格。</span><span class="sxs-lookup"><span data-stu-id="b9585-109">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="what-is-an-array"></a><span data-ttu-id="b9585-110">什麼是陣列？</span><span class="sxs-lookup"><span data-stu-id="b9585-110">What is an array?</span></span>

<span data-ttu-id="b9585-111">我要先從基本的技術描述開始，藉此說明陣列是什麼，以及大部分的程式設計語言如何使用這些陣列，再導入 PowerShell 使用陣列的其他方式的主題。</span><span class="sxs-lookup"><span data-stu-id="b9585-111">I'm going to start with a basic technical description of what arrays are and how they are used by most programming languages before I shift into the other ways PowerShell makes use of them.</span></span>

<span data-ttu-id="b9585-112">陣列是一種資料結構，可做為多個項目的集合。</span><span class="sxs-lookup"><span data-stu-id="b9585-112">An array is a data structure that serves as a collection of multiple items.</span></span> <span data-ttu-id="b9585-113">您可以逐一查看陣列，或使用索引來存取個別的項目。</span><span class="sxs-lookup"><span data-stu-id="b9585-113">You can iterate over the array or access individual items using an index.</span></span> <span data-ttu-id="b9585-114">系統會以連續的記憶體區塊建立陣列，其中每個值都會儲存於彼此相鄰的位置。</span><span class="sxs-lookup"><span data-stu-id="b9585-114">The array is created as a sequential chunk of memory where each value is stored right next to the other.</span></span>

<span data-ttu-id="b9585-115">隨著文章內容的敘述，我將處及相關的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="b9585-115">I'll touch on each of those details as we go.</span></span>

## <a name="basic-usage"></a><span data-ttu-id="b9585-116">基本使用方式</span><span class="sxs-lookup"><span data-stu-id="b9585-116">Basic usage</span></span>

<span data-ttu-id="b9585-117">因為陣列是 PowerShell 的基本功能，所以在 PowerShell 中使用陣列有一種簡單的語法。</span><span class="sxs-lookup"><span data-stu-id="b9585-117">Because arrays are such a basic feature of PowerShell, there is a simple syntax for working with them in PowerShell.</span></span>

### <a name="create-an-array"></a><span data-ttu-id="b9585-118">建立陣列</span><span class="sxs-lookup"><span data-stu-id="b9585-118">Create an array</span></span>

<span data-ttu-id="b9585-119">您可以使用 `@()` 來建立空的陣列</span><span class="sxs-lookup"><span data-stu-id="b9585-119">An empty array can be created by using `@()`</span></span>

```powershell
PS> $data = @()
PS> $data.count
0
```

<span data-ttu-id="b9585-120">我們可以建立陣列，並將值放在 `@()` 括弧中，藉此將其植入。</span><span class="sxs-lookup"><span data-stu-id="b9585-120">We can create an array and seed it with values just by placing them in the `@()` parentheses.</span></span>

```powershell
PS> $data = @('Zero','One','Two','Three')
PS> $data.count
4

PS> $data
Zero
One
Two
Three
```

<span data-ttu-id="b9585-121">此陣列有 4 個項目。</span><span class="sxs-lookup"><span data-stu-id="b9585-121">This array has 4 items.</span></span> <span data-ttu-id="b9585-122">當我們呼叫 `$data` 變數時，我們會看到項目的清單。</span><span class="sxs-lookup"><span data-stu-id="b9585-122">When we call the `$data` variable, we see the list of our items.</span></span> <span data-ttu-id="b9585-123">如果是字串陣列，則會為每個字串各取得一行。</span><span class="sxs-lookup"><span data-stu-id="b9585-123">If it's an array of strings, then we get one line per string.</span></span>

<span data-ttu-id="b9585-124">我們可以在多行宣告陣列。</span><span class="sxs-lookup"><span data-stu-id="b9585-124">We can declare an array on multiple lines.</span></span> <span data-ttu-id="b9585-125">在此情況下，逗號是選擇性使用的，而且通常會省略。</span><span class="sxs-lookup"><span data-stu-id="b9585-125">The comma is optional in this case and generally left out.</span></span>

```powershell
$data = @(
    'Zero'
    'One'
    'Two'
    'Three'
)
```

<span data-ttu-id="b9585-126">我習慣將陣列宣告為多行，就像這樣。</span><span class="sxs-lookup"><span data-stu-id="b9585-126">I prefer to declare my arrays on multiple lines like that.</span></span> <span data-ttu-id="b9585-127">當您有多個項目時，這樣不僅方便閱讀，同時也可讓您在使用原始程式碼控制時更容易與舊版進行比較。</span><span class="sxs-lookup"><span data-stu-id="b9585-127">Not only does it get easier to read when you have multiple items, it also makes it easier to compare to previous versions when using source control.</span></span>

#### <a name="other-syntax"></a><span data-ttu-id="b9585-128">其他語法</span><span class="sxs-lookup"><span data-stu-id="b9585-128">Other syntax</span></span>

<span data-ttu-id="b9585-129">眾所周知，`@()` 是用來建立陣列的語法，不過在大多數情況下，以逗號分隔的清單就能勝任。</span><span class="sxs-lookup"><span data-stu-id="b9585-129">It's commonly understood that `@()` is the syntax for creating an array, but comma-separated lists work most of the time.</span></span>

```powershell
$data = 'Zero','One','Two','Three'
```

#### <a name="write-output-to-create-arrays"></a><span data-ttu-id="b9585-130">Write-Output 建立陣列</span><span class="sxs-lookup"><span data-stu-id="b9585-130">Write-Output to create arrays</span></span>

<span data-ttu-id="b9585-131">值得一提的小技巧，就是您可以使用 `Write-Output` 在主控台快速地建立字串。</span><span class="sxs-lookup"><span data-stu-id="b9585-131">One cool little trick worth mentioning is that you can use `Write-Output` to quickly create strings at the console.</span></span>

```powershell
$data = Write-Output Zero One Two Three
```

<span data-ttu-id="b9585-132">這種方式很便利，因為當參數接受字串時，您不需要在字串前後加上引號。</span><span class="sxs-lookup"><span data-stu-id="b9585-132">This is handy because you don't have to put quotes around the strings when the parameter accepts strings.</span></span> <span data-ttu-id="b9585-133">我不會在指令碼中執行這項操作，不過這種作法在主控台中是很好下手的方式。</span><span class="sxs-lookup"><span data-stu-id="b9585-133">I would never do this in a script but it's fair game in the console.</span></span>

### <a name="accessing-items"></a><span data-ttu-id="b9585-134">存取項目</span><span class="sxs-lookup"><span data-stu-id="b9585-134">Accessing items</span></span>

<span data-ttu-id="b9585-135">現在您已經有一個具有項目的陣列，您可能會想要存取和更新這些項目。</span><span class="sxs-lookup"><span data-stu-id="b9585-135">Now that you have an array with items in it, you may want to access and update those items.</span></span>

#### <a name="offset"></a><span data-ttu-id="b9585-136">Offset</span><span class="sxs-lookup"><span data-stu-id="b9585-136">Offset</span></span>

<span data-ttu-id="b9585-137">若要存取個別的項目，我們將括弧 `[]` 用於從 0 開始的位移值。</span><span class="sxs-lookup"><span data-stu-id="b9585-137">To access individual items, we use the brackets `[]` with an offset value starting at 0.</span></span> <span data-ttu-id="b9585-138">這就是我們取得陣列中第一個項目的方式：</span><span class="sxs-lookup"><span data-stu-id="b9585-138">This is how we get the first item in our array:</span></span>

```powershell
PS> $data = 'Zero','One','Two','Three'
PS> $data[0]
Zero
```

<span data-ttu-id="b9585-139">我們在這裡使用零的原因，在於第一個項目位於清單的開頭，所以我們使用 0 個項目的位移來取得該項目。</span><span class="sxs-lookup"><span data-stu-id="b9585-139">The reason why we use zero here is because the first item is at the beginning of the list so we use an offset of 0 items to get to it.</span></span> <span data-ttu-id="b9585-140">若要取得第二個項目，我們必須藉由位移 1 來略過第一個項目。</span><span class="sxs-lookup"><span data-stu-id="b9585-140">To get to the second item, we would need to use an offset of 1 to skip the first item.</span></span>

```powershell
PS> $data[1]
One
```

<span data-ttu-id="b9585-141">這表示最後一個項目是在位移 3。</span><span class="sxs-lookup"><span data-stu-id="b9585-141">This would mean that the last item is at offset 3.</span></span>

```powershell
PS> $data[3]
Three
```

#### <a name="index"></a><span data-ttu-id="b9585-142">索引</span><span class="sxs-lookup"><span data-stu-id="b9585-142">Index</span></span>

<span data-ttu-id="b9585-143">現在您可以瞭解我在此範例中挑選那些值的原因所在。</span><span class="sxs-lookup"><span data-stu-id="b9585-143">Now you can see why I picked the values that I did for this example.</span></span> <span data-ttu-id="b9585-144">我將此視為位移，因為這就是它真正的本質所在，但此位移較常稱為索引。</span><span class="sxs-lookup"><span data-stu-id="b9585-144">I introduced this as an offset because that is what it really is, but this offset is more commonly referred to as an index.</span></span> <span data-ttu-id="b9585-145">從 `0` 開始的索引。</span><span class="sxs-lookup"><span data-stu-id="b9585-145">An index that starts at `0`.</span></span> <span data-ttu-id="b9585-146">在本文的其餘部分，我將會將該位移稱為索引。</span><span class="sxs-lookup"><span data-stu-id="b9585-146">For the rest of this article I will call the offset an index.</span></span>

#### <a name="special-index-tricks"></a><span data-ttu-id="b9585-147">特殊索引訣竅</span><span class="sxs-lookup"><span data-stu-id="b9585-147">Special index tricks</span></span>

<span data-ttu-id="b9585-148">在大部分的程式設計語言中，您只能指定單一數字做為索引，並傳回單一項目。</span><span class="sxs-lookup"><span data-stu-id="b9585-148">In most languages, you can only specify a single number as the index and you get a single item back.</span></span>
<span data-ttu-id="b9585-149">PowerShell 更加靈活。</span><span class="sxs-lookup"><span data-stu-id="b9585-149">PowerShell is much more flexible.</span></span> <span data-ttu-id="b9585-150">您可以同時使用多個索引。</span><span class="sxs-lookup"><span data-stu-id="b9585-150">You can use multiple indexes at once.</span></span> <span data-ttu-id="b9585-151">藉由提供索引清單，我們可以選取多個項目。</span><span class="sxs-lookup"><span data-stu-id="b9585-151">By providing a list of indexes, we can select several items.</span></span>

```powershell
PS> $data[0,2,3]
Zero
Two
Three
```

<span data-ttu-id="b9585-152">系統會根據所提供的索引順序傳回項目。</span><span class="sxs-lookup"><span data-stu-id="b9585-152">The items are returned based on the order of the indexes provided.</span></span> <span data-ttu-id="b9585-153">如果複製索引，則您會同時取得該項目。</span><span class="sxs-lookup"><span data-stu-id="b9585-153">If you duplicate an index, you get that item both times.</span></span>

```powershell
PS> $data[3,0,3]
Three
Zero
Three
```

<span data-ttu-id="b9585-154">我們可以藉由內建的 `..` 運算子來指定數字序列。</span><span class="sxs-lookup"><span data-stu-id="b9585-154">We can specify a sequence of numbers with the built-in `..` operator.</span></span>

```powershell
PS> $data[1..3]
One
Two
Three
```

<span data-ttu-id="b9585-155">反向也適用。</span><span class="sxs-lookup"><span data-stu-id="b9585-155">This works in reverse too.</span></span>

```powershell
PS> $data[3..1]
Three
Two
One
```

<span data-ttu-id="b9585-156">您可以使用負索引值從尾端進行位移。</span><span class="sxs-lookup"><span data-stu-id="b9585-156">You can use negative index values to offset from the end.</span></span> <span data-ttu-id="b9585-157">因此，如果需要清單中的最後一個項目，您可以使用 `-1`。</span><span class="sxs-lookup"><span data-stu-id="b9585-157">So if you need the last item in the list, you can use `-1`.</span></span>

```powershell
PS> $data[-1]
Three
```

<span data-ttu-id="b9585-158">在這裡使用 `..` 運算子時，請務必小心謹慎。</span><span class="sxs-lookup"><span data-stu-id="b9585-158">One word of caution here with the `..` operator.</span></span> <span data-ttu-id="b9585-159">序列 `0..-1` 和 `-1..0` 會針對 `0,-1` 和 `-1,0` 的值進行評估。</span><span class="sxs-lookup"><span data-stu-id="b9585-159">The sequence `0..-1` and `-1..0` evaluate to the values `0,-1` and `-1,0`.</span></span> <span data-ttu-id="b9585-160">如果您忘記此詳細資料，很容易就能看到 `$data[0..-1]`，並聯想到它會列舉所有的項目。</span><span class="sxs-lookup"><span data-stu-id="b9585-160">It's easy to see `$data[0..-1]` and think it would enumerate all items if you forget this detail.</span></span> <span data-ttu-id="b9585-161">`$data[0..-1]` 藉由提供陣列中的第一個和最後一個項目 (並且不含任何其他值)，為您提供與 `$data[0,-1]` 相同的值。</span><span class="sxs-lookup"><span data-stu-id="b9585-161">`$data[0..-1]` gives you the same value as `$data[0,-1]` by giving you the first and last item in the array (and none of the other values).</span></span>

#### <a name="out-of-bounds"></a><span data-ttu-id="b9585-162">超出範圍</span><span class="sxs-lookup"><span data-stu-id="b9585-162">Out of bounds</span></span>

<span data-ttu-id="b9585-163">在大部分的程式設計語言中，如果嘗試存取超出陣列結尾的項目索引，則您會收到某種類型的錯誤或例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b9585-163">In most languages, if you try to access an index of an item that is past the end of the array, you would get some type of error or an exception.</span></span> <span data-ttu-id="b9585-164">PowerShell 不會無訊息地傳回任何內容。</span><span class="sxs-lookup"><span data-stu-id="b9585-164">PowerShell silently returns nothing.</span></span>

```powershell
PS> $null -eq $data[9000]
True
```

#### <a name="cannot-index-into-a-null-array"></a><span data-ttu-id="b9585-165">無法為 null 陣列編製索引</span><span class="sxs-lookup"><span data-stu-id="b9585-165">Cannot index into a null array</span></span>

<span data-ttu-id="b9585-166">如果您的變數是 `$null`，而您嘗試將其編製為數組之類的索引，則會收到顯示訊息 `Cannot index into a null array` 的 `System.Management.Automation.RuntimeException` 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b9585-166">If your variable is `$null` and you try to index it like an array, you get a `System.Management.Automation.RuntimeException` exception with the message `Cannot index into a null array`.</span></span>

```powershell
PS> $empty = $null
SP> $empty[0]
Error: Cannot index into a null array.
```

<span data-ttu-id="b9585-167">因此，在您嘗試存取其中的元素之前，請確認您的陣列並非 `$null`。</span><span class="sxs-lookup"><span data-stu-id="b9585-167">So make sure your arrays are not `$null` before you try to access elements inside them.</span></span>

#### <a name="count"></a><span data-ttu-id="b9585-168">Count</span><span class="sxs-lookup"><span data-stu-id="b9585-168">Count</span></span>

<span data-ttu-id="b9585-169">陣列和其他集合具有 count 屬性，可告訴您陣列中有多少個項目。</span><span class="sxs-lookup"><span data-stu-id="b9585-169">Arrays and other collections have a count property that tells you how many items are in the array.</span></span>

```powershell
PS> $data.count
4
```

<span data-ttu-id="b9585-170">PowerShell 3.0 已將 count 屬性新增至大部分的物件。</span><span class="sxs-lookup"><span data-stu-id="b9585-170">PowerShell 3.0 added a count property to most objects.</span></span> <span data-ttu-id="b9585-171">您可以擁有單一物件，而且物件應該會提供您 `1` 的計數。</span><span class="sxs-lookup"><span data-stu-id="b9585-171">you can have a single object and it should give you a count of `1`.</span></span>

```powershell
PS> $date = Get-Date
PS> $date.count
1
```

<span data-ttu-id="b9585-172">即使 `$null` 具有 count 屬性，它還是會傳回 `0`。</span><span class="sxs-lookup"><span data-stu-id="b9585-172">Even `$null` has a count property except it returns `0`.</span></span>

```powershell
PS> $null.count
0
```

<span data-ttu-id="b9585-173">這裡有一些陷阱，我會在本文稍後探討 `$null` 或空白陣列的檢查時，再回顧一下。</span><span class="sxs-lookup"><span data-stu-id="b9585-173">There are some traps here that I will revisit when I cover checking for `$null` or empty arrays later on in this article.</span></span>

#### <a name="off-by-one-errors"></a><span data-ttu-id="b9585-174">差一錯誤</span><span class="sxs-lookup"><span data-stu-id="b9585-174">Off-by-one errors</span></span>

<span data-ttu-id="b9585-175">會建立常見的程式設計錯誤的原因，在於陣列是從索引 0 開始。</span><span class="sxs-lookup"><span data-stu-id="b9585-175">A common programming error is created because arrays start at index 0.</span></span> <span data-ttu-id="b9585-176">有兩種方式可以導入差一錯誤。</span><span class="sxs-lookup"><span data-stu-id="b9585-176">Off-by-one errors can be introduced in two ways.</span></span>

<span data-ttu-id="b9585-177">第一種是心裡想著您想要第二個項目，並使用 `2` 的索引，然後實際上去取得第三個項目。</span><span class="sxs-lookup"><span data-stu-id="b9585-177">The first is by mentally thinking you want the second item and using an index of `2` and really getting the third item.</span></span> <span data-ttu-id="b9585-178">或者，假設您有四個項目，而您想要上一個項目，所以您可以使用此計數來取用最後一個項目。</span><span class="sxs-lookup"><span data-stu-id="b9585-178">Or by thinking that you have four items and you want last item, so you use the count to access the last item.</span></span>

```powershell
$data[ $data.count ]
```

<span data-ttu-id="b9585-179">PowerShell 很樂意讓您這麼做，並為您提供索引 4的確切項目： `$null`。</span><span class="sxs-lookup"><span data-stu-id="b9585-179">PowerShell is perfectly happy to let you do that and give you exactly what item exists at index 4: `$null`.</span></span> <span data-ttu-id="b9585-180">您應該使用 `$data.count - 1` 或我們所學習的 `-1`。</span><span class="sxs-lookup"><span data-stu-id="b9585-180">You should be using `$data.count - 1` or the `-1` that we learned about above.</span></span>

```powershell
PS> $data[ $data.count - 1 ]
Three
```

<span data-ttu-id="b9585-181">這是您可以使用 `-1` 索引來取得最後一項元素的最後機會。</span><span class="sxs-lookup"><span data-stu-id="b9585-181">This is where you can use the `-1` index to get the last element.</span></span>

```powershell
PS> $data[ -1 ]
Three
```

<span data-ttu-id="b9585-182">Lee Dailey 也會向我指出，我們可以使用 `$data.GetUpperBound(0)` 來取得最大的索引編號。</span><span class="sxs-lookup"><span data-stu-id="b9585-182">Lee Dailey also pointed out to me that we can use `$data.GetUpperBound(0)` to get the max index number.</span></span>

```powershell
PS> $data.GetUpperBound(0)
3
PS> $data[ $data.GetUpperBound(0) ]
Three
```

<span data-ttu-id="b9585-183">第二個最常見的方式是在反覆查看清單，而不是在合適的時間停止。</span><span class="sxs-lookup"><span data-stu-id="b9585-183">The second most common way is when iterating the list and not stopping at the right time.</span></span> <span data-ttu-id="b9585-184">當我們談到如何使用 `for` 迴圈時，我會重新回顧此資訊。</span><span class="sxs-lookup"><span data-stu-id="b9585-184">I'll revisit this when we talk about using the `for` loop.</span></span>

### <a name="updating-items"></a><span data-ttu-id="b9585-185">正在更新項目</span><span class="sxs-lookup"><span data-stu-id="b9585-185">Updating items</span></span>

<span data-ttu-id="b9585-186">我們可以使用相同的索引來更新陣列中的現有項目。</span><span class="sxs-lookup"><span data-stu-id="b9585-186">We can use the same index to update existing items in the array.</span></span> <span data-ttu-id="b9585-187">這可讓我們直接存取以更新個別項目。</span><span class="sxs-lookup"><span data-stu-id="b9585-187">This gives us direct access to update individual items.</span></span>

```powershell
$data[2] = 'dos'
$data[3] = 'tres'
```

<span data-ttu-id="b9585-188">如果我們嘗試更新最後一項元素之外的項目，就會出現 `Index was outside the bounds of the array.` 錯誤。</span><span class="sxs-lookup"><span data-stu-id="b9585-188">If we try to update an item that is past the last element, then we get an `Index was outside the bounds of the array.` error.</span></span>

```powershell
PS> $data[4] = 'four'
Index was outside the bounds of the array.
At line:1 char:1
+ $data[4] = 'four'
+ ~~~~~~~~~~~~~
+ CategoryInfo          : OperationStopped: (:) [], IndexOutOfRangeException
+ FullyQualifiedErrorId : System.IndexOutOfRangeException
```

<span data-ttu-id="b9585-189">稍後當我談到如何擴大陣列時，我會重新回顧這種情況。</span><span class="sxs-lookup"><span data-stu-id="b9585-189">I'll revisit this later when I talk about how to make an array larger.</span></span>

### <a name="iteration"></a><span data-ttu-id="b9585-190">反覆運算</span><span class="sxs-lookup"><span data-stu-id="b9585-190">Iteration</span></span>

<span data-ttu-id="b9585-191">在某些時候，您可能需要針對陣列中的每個項目，逐一執行或逐一查看整個清單並執行動作。</span><span class="sxs-lookup"><span data-stu-id="b9585-191">At some point, you might need to walk or iterate the entire list and perform some action for each item in the array.</span></span>

#### <a name="pipeline"></a><span data-ttu-id="b9585-192">管線</span><span class="sxs-lookup"><span data-stu-id="b9585-192">Pipeline</span></span>

<span data-ttu-id="b9585-193">陣列和 PowerShell 管道皆彼此適用。</span><span class="sxs-lookup"><span data-stu-id="b9585-193">Arrays and the PowerShell pipeline are meant for each other.</span></span> <span data-ttu-id="b9585-194">這是處理這些值最簡單的方式之一。</span><span class="sxs-lookup"><span data-stu-id="b9585-194">This is one of the simplest ways to process over those values.</span></span> <span data-ttu-id="b9585-195">當您將陣列傳遞至管道時，陣列中的每個項目都會進行個別處理。</span><span class="sxs-lookup"><span data-stu-id="b9585-195">When you pass an array to a pipeline, each item inside the array is processed individually.</span></span>

```powershell
PS> $data = 'Zero','One','Two','Three'
PS> $data | ForEach-Object {"Item: [$PSItem]"}
Item: [Zero]
Item: [One]
Item: [Two]
Item: [Three]
```

<span data-ttu-id="b9585-196">如果您之前看不到 `$PSItem`，只需要知道它與 `$_` 的內容相同即可。</span><span class="sxs-lookup"><span data-stu-id="b9585-196">If you have not seen `$PSItem` before, just know that it's the same thing as `$_`.</span></span> <span data-ttu-id="b9585-197">您可以使用其中一種，因為兩者都代表管道中的目前物件。</span><span class="sxs-lookup"><span data-stu-id="b9585-197">You can use either one because they both represent the current object in the pipeline.</span></span>

#### <a name="foreach-loop"></a><span data-ttu-id="b9585-198">ForEach 迴圈</span><span class="sxs-lookup"><span data-stu-id="b9585-198">ForEach loop</span></span>

<span data-ttu-id="b9585-199">`ForEach` 迴圈適用於集合。</span><span class="sxs-lookup"><span data-stu-id="b9585-199">The `ForEach` loop works well with collections.</span></span> <span data-ttu-id="b9585-200">使用語法： `foreach ( <variable> in <collection> )`</span><span class="sxs-lookup"><span data-stu-id="b9585-200">Using the syntax: `foreach ( <variable> in <collection> )`</span></span>

```powershell
foreach ( $node in $data )
{
    "Item: [$node]"
}
```

#### <a name="foreach-method"></a><span data-ttu-id="b9585-201">ForEach 方法</span><span class="sxs-lookup"><span data-stu-id="b9585-201">ForEach method</span></span>

<span data-ttu-id="b9585-202">我往往會忘了這項功能，但它很適合用於簡單的作業。</span><span class="sxs-lookup"><span data-stu-id="b9585-202">I tend to forget about this one but it works well for simple operations.</span></span> <span data-ttu-id="b9585-203">PowerShell 可讓您在集合上呼叫 `.ForEach()`。</span><span class="sxs-lookup"><span data-stu-id="b9585-203">PowerShell allows you to call `.ForEach()` on a collection.</span></span>

```powershell
PS> $data.foreach({"Item [$PSItem]"})
Item [Zero]
Item [One]
Item [Two]
Item [Three]
```

<span data-ttu-id="b9585-204">`.foreach()` 接受屬於指令碼區塊的參數。</span><span class="sxs-lookup"><span data-stu-id="b9585-204">The `.foreach()` takes a parameter that is a script block.</span></span> <span data-ttu-id="b9585-205">您可以置放括號，並僅提供指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="b9585-205">You can drop the parentheses and just provide the script block.</span></span>

```powershell
$data.foreach{"Item [$PSItem]"}
```

<span data-ttu-id="b9585-206">這是鮮為人知的語法，但其運作方式完全相同。</span><span class="sxs-lookup"><span data-stu-id="b9585-206">This is a lesser known syntax but it works just the same.</span></span> <span data-ttu-id="b9585-207">此 `foreach` 方法已在 PowerShell 4.0 中新增。</span><span class="sxs-lookup"><span data-stu-id="b9585-207">This `foreach` method was added in PowerShell 4.0.</span></span>

#### <a name="for-loop"></a><span data-ttu-id="b9585-208">For 迴圈</span><span class="sxs-lookup"><span data-stu-id="b9585-208">For loop</span></span>

<span data-ttu-id="b9585-209">在大部分其他程式設計語言中，皆使用 `for` 迴圈，不過在 PowerShell 中並不多見。</span><span class="sxs-lookup"><span data-stu-id="b9585-209">The `for` loop is used heavily in most other languages but you don't see it much in PowerShell.</span></span> <span data-ttu-id="b9585-210">當您看到該迴圈時，通常是在逐一執行陣列的內容中。</span><span class="sxs-lookup"><span data-stu-id="b9585-210">When you do see it, it's often in the context of walking an array.</span></span>

```powershell
for ( $index = 0; $index -lt $data.count; $index++)
{
    "Item: [{0}]" -f $data[$index]
}
```

<span data-ttu-id="b9585-211">我們首先該做的，就是將 `$index` 初始化為 `0`。</span><span class="sxs-lookup"><span data-stu-id="b9585-211">The first thing we do is initialize an `$index` to `0`.</span></span> <span data-ttu-id="b9585-212">然後，我們會新增 `$index` 必須小於 `$data.count` 的條件。</span><span class="sxs-lookup"><span data-stu-id="b9585-212">Then we add the condition that `$index` must be less than `$data.count`.</span></span> <span data-ttu-id="b9585-213">最後，我們會指定每次迴圈時，我都必須藉由 `1` 來增加索引。</span><span class="sxs-lookup"><span data-stu-id="b9585-213">Finally, we specify that every time we loop that me must increase the index by `1`.</span></span> <span data-ttu-id="b9585-214">在此情況下，`$index++` 為 `$index = $index + 1` 縮短形。</span><span class="sxs-lookup"><span data-stu-id="b9585-214">In this case `$index++` is short for `$index = $index + 1`.</span></span>

<span data-ttu-id="b9585-215">當您使用 `for` 迴圈時，請特別注意該條件。</span><span class="sxs-lookup"><span data-stu-id="b9585-215">Whenever you're using a `for` loop, pay special attention to the condition.</span></span> <span data-ttu-id="b9585-216">我在這裡使用 `$index -lt $data.count`。</span><span class="sxs-lookup"><span data-stu-id="b9585-216">I used `$index -lt $data.count` here.</span></span> <span data-ttu-id="b9585-217">您可以稍微讓條件出現錯誤，藉此在您的邏輯中取得差一錯誤。</span><span class="sxs-lookup"><span data-stu-id="b9585-217">It's easy to get the condition slightly wrong to get an off-by-one error in your logic.</span></span> <span data-ttu-id="b9585-218">使用 `$index -le $data.count` 或 `$index -lt ($data.count - 1)` 總是略有些許錯誤。</span><span class="sxs-lookup"><span data-stu-id="b9585-218">Using `$index -le $data.count` or `$index -lt ($data.count - 1)` are ever so slightly wrong.</span></span> <span data-ttu-id="b9585-219">這會導致您的結果處理的項目過多或太少。</span><span class="sxs-lookup"><span data-stu-id="b9585-219">That would cause your result to process too many or too few items.</span></span> <span data-ttu-id="b9585-220">這是傳統的差一錯誤。</span><span class="sxs-lookup"><span data-stu-id="b9585-220">This is the classic off-by-one error.</span></span>

#### <a name="switch-loop"></a><span data-ttu-id="b9585-221">Switch 迴圈</span><span class="sxs-lookup"><span data-stu-id="b9585-221">Switch loop</span></span>

<span data-ttu-id="b9585-222">這是很容易忽略的一種。</span><span class="sxs-lookup"><span data-stu-id="b9585-222">This is one that is easy to overlook.</span></span> <span data-ttu-id="b9585-223">如果您將陣列提供給 [switch 陳述式][]，則陳述式會檢查陣列中的每個項目。</span><span class="sxs-lookup"><span data-stu-id="b9585-223">If you provide an array to a [switch statement][], it checks each item in the array.</span></span>

```powershell
$data = 'Zero','One','Two','Three'
switch( $data )
{
    'One'
    {
        'Tock'
    }
    'Three'
    {
        'Tock'
    }
    Default
    {
        'Tick'
    }
}
```

```Output
Tick
Tock
Tick
Tock
```

<span data-ttu-id="b9585-224">我們可以使用 switch 陳述式來做很多很酷的事。</span><span class="sxs-lookup"><span data-stu-id="b9585-224">There are a lot of cool things that we can do with the switch statement.</span></span> <span data-ttu-id="b9585-225">我有另一篇專文介紹這個。</span><span class="sxs-lookup"><span data-stu-id="b9585-225">I have another article dedicated to this.</span></span>

- <span data-ttu-id="b9585-226">[您想知道有關於 [Switch 陳述式]的一切] (英文)</span><span class="sxs-lookup"><span data-stu-id="b9585-226">[Everything you ever wanted to know about the switch statement][switch statement]</span></span>

#### <a name="updating-values"></a><span data-ttu-id="b9585-227">更新值</span><span class="sxs-lookup"><span data-stu-id="b9585-227">Updating values</span></span>

<span data-ttu-id="b9585-228">當陣列是字串或整數 (實值型別) 的集合時，您有時可能會在進行迴圈處理時，想要新陣列中的值。</span><span class="sxs-lookup"><span data-stu-id="b9585-228">When your array is a collection of string or integers (value types), sometimes you may want to update the values in the array as you loop over them.</span></span> <span data-ttu-id="b9585-229">以上大部分的迴圈會使用迴圈中的變數來保存值的複本。</span><span class="sxs-lookup"><span data-stu-id="b9585-229">Most of the loops above use a variable in the loop that holds a copy of the value.</span></span> <span data-ttu-id="b9585-230">如果您更新該變數，陣列中的原始值不會更新。</span><span class="sxs-lookup"><span data-stu-id="b9585-230">If you update that variable, the original value in the array is not updated.</span></span>

<span data-ttu-id="b9585-231">該陳述式的例外狀況是 `for` 迴圈。</span><span class="sxs-lookup"><span data-stu-id="b9585-231">The exception to that statement is the `for` loop.</span></span> <span data-ttu-id="b9585-232">如果您想要逐一執行陣列並更新其中的值，則 `for` 迴圈就是您要尋找的工具。</span><span class="sxs-lookup"><span data-stu-id="b9585-232">If you want to walk an array and update values inside it, then the `for` loop is what you're looking for.</span></span>

```powershell
for ( $index = 0; $index -lt $data.count; $index++ )
{
    $data[$index] = "Item: [{0}]" -f $data[$index]
}
```

<span data-ttu-id="b9585-233">此範例會依索引採用值，進行一些變更，然後使用該相同的索引將其指派回去。</span><span class="sxs-lookup"><span data-stu-id="b9585-233">This example takes a value by index, makes a few changes, and then uses that same index to assign it back.</span></span>

## <a name="arrays-of-objects"></a><span data-ttu-id="b9585-234">物件陣列</span><span class="sxs-lookup"><span data-stu-id="b9585-234">Arrays of Objects</span></span>

<span data-ttu-id="b9585-235">到目前為止，我們放入陣列中的唯一東西就是實值型別，不過陣列也可以包含物件。</span><span class="sxs-lookup"><span data-stu-id="b9585-235">So far, the only thing we've placed in an array is a value type, but arrays can also contain objects.</span></span>

```powershell
$data = @(
    [pscustomobject]@{FirstName='Kevin';LastName='Marquette'}
    [pscustomobject]@{FirstName='John'; LastName='Doe'}
)
```

<span data-ttu-id="b9585-236">當您將物件的集合指派給變數時，許多 Cmdlet 都會以陣列的形式將其傳回。</span><span class="sxs-lookup"><span data-stu-id="b9585-236">Many cmdlets return collections of objects as arrays when you assign them to a variable.</span></span>

```powershell
$processList = Get-Process
```

<span data-ttu-id="b9585-237">我們已討論過的所有基本功能，仍適用於物件陣列，其中有一些值得加以說明的細節。</span><span class="sxs-lookup"><span data-stu-id="b9585-237">All of the basic features we already talked about still apply to arrays of objects with a few details worth pointing out.</span></span>

### <a name="accessing-properties"></a><span data-ttu-id="b9585-238">存取屬性</span><span class="sxs-lookup"><span data-stu-id="b9585-238">Accessing properties</span></span>

<span data-ttu-id="b9585-239">我們可以使用索引來存取集合中的個別項目，就像使用實值型別一樣。</span><span class="sxs-lookup"><span data-stu-id="b9585-239">We can use an index to access an individual item in a collection just like with value types.</span></span>

```powershell
PS> $data[0]

FirstName LastName
-----     ----
Kevin     Marquette
```

<span data-ttu-id="b9585-240">我們可以直接存取和更新屬性。</span><span class="sxs-lookup"><span data-stu-id="b9585-240">We can access and update properties directly.</span></span>

```powershell
PS> $data[0].FirstName

Kevin

PS> $data[0].FirstName = 'Jay'
PS> $data[0]

FirstName LastName
-----     ----
Jay       Marquette
```

#### <a name="array-properties"></a><span data-ttu-id="b9585-241">陣列屬性</span><span class="sxs-lookup"><span data-stu-id="b9585-241">Array properties</span></span>

<span data-ttu-id="b9585-242">通常您必須列舉這類的完整清單，才能存取所有屬性：</span><span class="sxs-lookup"><span data-stu-id="b9585-242">Normally you would have to enumerate the whole list like this to access all the properties:</span></span>

```powershell
PS> $data | ForEach-Object {$_.LastName}

Marquette
Doe
```

<span data-ttu-id="b9585-243">或藉由使用 `Select-Object -ExpandProperty` Cmdlet 達到目的。</span><span class="sxs-lookup"><span data-stu-id="b9585-243">Or by using the `Select-Object -ExpandProperty` cmdlet.</span></span>

```powershell
PS> $data | Select-Object -ExpandProperty LastName

Marquette
Doe
```

<span data-ttu-id="b9585-244">不過，PowerShell 讓我們能夠直接要求 `LastName`。</span><span class="sxs-lookup"><span data-stu-id="b9585-244">But PowerShell offers us the ability to request `LastName` directly.</span></span> <span data-ttu-id="b9585-245">PowerShell 會為我們列舉所有清單，並傳回一份清除清單。</span><span class="sxs-lookup"><span data-stu-id="b9585-245">PowerShell enumerates them all for us and returns a clean list.</span></span>

```powershell
PS> $data.LastName

Marquette
Doe
```

<span data-ttu-id="b9585-246">列舉仍然會發生，但我們無法瞭解其背後的複雜性。</span><span class="sxs-lookup"><span data-stu-id="b9585-246">The enumeration still happens but we don't see the complexity behind it.</span></span>

### <a name="where-object-filtering"></a><span data-ttu-id="b9585-247">Where-Object 篩選</span><span class="sxs-lookup"><span data-stu-id="b9585-247">Where-Object filtering</span></span>

<span data-ttu-id="b9585-248">這就是 `Where-Object` 的進入位置，因此我們可以根據物件的屬性，篩選並選取我們想要的陣列內容。</span><span class="sxs-lookup"><span data-stu-id="b9585-248">This is where `Where-Object` comes in so we can filter and select what we want out of the array based on the properties of the object.</span></span>

```powershell
PS> $data | Where-Object {$_.FirstName -eq 'Kevin'}

FirstName LastName
-----     ----
Kevin     Marquette
```

<span data-ttu-id="b9585-249">我們可以撰寫相同的查詢，以取得我們所要尋找的 `FirstName`。</span><span class="sxs-lookup"><span data-stu-id="b9585-249">We can write that same query to get the `FirstName` we are looking for.</span></span>

```powershell
$data | Where FirstName -eq Kevin
```

#### <a name="where"></a><span data-ttu-id="b9585-250">Where()</span><span class="sxs-lookup"><span data-stu-id="b9585-250">Where()</span></span>

<span data-ttu-id="b9585-251">陣列具有 `Where()` 的方法，可讓您指定篩選條件的 `scriptblock`。</span><span class="sxs-lookup"><span data-stu-id="b9585-251">Arrays have a `Where()` method on them that allows you to specify a `scriptblock` for the filter.</span></span>

```powershell
$data.Where({$_.FirstName -eq 'Kevin'})
```

<span data-ttu-id="b9585-252">此功能已在 PowerShell 4.0 中新增。</span><span class="sxs-lookup"><span data-stu-id="b9585-252">This feature was added in PowerShell 4.0.</span></span>

### <a name="updating-objects-in-loops"></a><span data-ttu-id="b9585-253">更新迴圈中的物件</span><span class="sxs-lookup"><span data-stu-id="b9585-253">Updating objects in loops</span></span>

<span data-ttu-id="b9585-254">採用實值型別時，更新陣列的唯一方式是使用 for 迴圈，因為我們需要知道索引以取代值。</span><span class="sxs-lookup"><span data-stu-id="b9585-254">With value types, the only way to update the array is to use a for loop because we need to know the index to replace the value.</span></span> <span data-ttu-id="b9585-255">我們有更多選項可使用物件，因為它們是參考型別。</span><span class="sxs-lookup"><span data-stu-id="b9585-255">We have more options with objects because they are reference types.</span></span> <span data-ttu-id="b9585-256">以下是一個簡短的範例：</span><span class="sxs-lookup"><span data-stu-id="b9585-256">Here is a quick example:</span></span>

```powershell
foreach($person in $data)
{
    $person.FirstName = 'Kevin'
}
```

<span data-ttu-id="b9585-257">這個迴圈會逐一執行 `$data` 陣列中的每個物件。</span><span class="sxs-lookup"><span data-stu-id="b9585-257">This loop is walking every object in the `$data` array.</span></span> <span data-ttu-id="b9585-258">由於物件屬於參考型別，因此 `$person` 變數會參考陣列中完全相同的物件。</span><span class="sxs-lookup"><span data-stu-id="b9585-258">Because objects are reference types, the `$person` variable references the exact same object that is in the array.</span></span> <span data-ttu-id="b9585-259">因此，更新其屬性會更新原始物件。</span><span class="sxs-lookup"><span data-stu-id="b9585-259">So updates to its properties do update the original.</span></span>

<span data-ttu-id="b9585-260">您仍然無法以這種方式來取代整個物件。</span><span class="sxs-lookup"><span data-stu-id="b9585-260">You still can't replace the whole object this way.</span></span> <span data-ttu-id="b9585-261">如果您嘗試將新物件指派給 `$person` 變數，則會將變數參考更新為不會再指向陣列中原始物件的其他物件。</span><span class="sxs-lookup"><span data-stu-id="b9585-261">If you try to assign a new object to the `$person` variable, you're updating the variable reference to something else that no longer points to the original object in the array.</span></span> <span data-ttu-id="b9585-262">這種運作方式與您的預期不同：</span><span class="sxs-lookup"><span data-stu-id="b9585-262">This doesn't work like you would expect:</span></span>

```powershell
foreach($person in $data)
{
    $person = [pscustomobject]@{
        FirstName='Kevin'
        LastName='Marquette'
    }
}
```

## <a name="operators"></a><span data-ttu-id="b9585-263">操作員</span><span class="sxs-lookup"><span data-stu-id="b9585-263">Operators</span></span>

<span data-ttu-id="b9585-264">PowerShell 中的運算子也適用陣列。</span><span class="sxs-lookup"><span data-stu-id="b9585-264">The operators in PowerShell also work on arrays.</span></span> <span data-ttu-id="b9585-265">其中一些工作的執行方式稍有不同。</span><span class="sxs-lookup"><span data-stu-id="b9585-265">Some of them work slightly differently.</span></span>

### <a name="-join"></a><span data-ttu-id="b9585-266">-join</span><span class="sxs-lookup"><span data-stu-id="b9585-266">-join</span></span>

<span data-ttu-id="b9585-267">`-join` 運算子最明顯，因此讓我們先瞭解一下。</span><span class="sxs-lookup"><span data-stu-id="b9585-267">The `-join` operator is the most obvious one so let's look at it first.</span></span> <span data-ttu-id="b9585-268">我喜歡 `-join` 運算子並經常使用。</span><span class="sxs-lookup"><span data-stu-id="b9585-268">I like the `-join` operator and use it often.</span></span> <span data-ttu-id="b9585-269">它會將陣列中的所有元素與您指定的字元或字串聯結在一起。</span><span class="sxs-lookup"><span data-stu-id="b9585-269">It joins all elements in the array with the character or string that you specify.</span></span>

```powershell
PS> $data = @(1,2,3,4)
PS> $data -join '-'
1-2-3-4
PS> $data -join ','
1,2,3,4
```

<span data-ttu-id="b9585-270">我喜歡 `-join` 運算子的其中一項功能，就是它會處理單一項目。</span><span class="sxs-lookup"><span data-stu-id="b9585-270">One of the features that I like about the `-join` operator is that it handles single items.</span></span>

```powershell
PS> 1 -join '-'
1
```

<span data-ttu-id="b9585-271">我在記錄和詳細資訊訊息中使用此功能。</span><span class="sxs-lookup"><span data-stu-id="b9585-271">I use this inside logging and verbose messages.</span></span>

```powershell
PS> $data = @(1,2,3,4)
PS> "Data is $($data -join ',')."
Data is 1,2,3,4.
```

#### <a name="-join-array"></a><span data-ttu-id="b9585-272">-join $array</span><span class="sxs-lookup"><span data-stu-id="b9585-272">-join $array</span></span>

<span data-ttu-id="b9585-273">Lee Dailey 在這裡向我傳授一個聰明的技巧。</span><span class="sxs-lookup"><span data-stu-id="b9585-273">Here is a clever trick that Lee Dailey pointed out to me.</span></span> <span data-ttu-id="b9585-274">如果您想要加入任何不含分隔符號的內容，您可以改用以下方式：</span><span class="sxs-lookup"><span data-stu-id="b9585-274">If you ever want to join everything without a delimiter, instead of doing this:</span></span>

```powershell
PS> $data = @(1,2,3,4)
PS> $data -join $null
1234
```

<span data-ttu-id="b9585-275">您可以使用 `-join` 搭配陣列做為參數，而不使用前置詞。</span><span class="sxs-lookup"><span data-stu-id="b9585-275">You can use `-join` with the array as the parameter with no prefix.</span></span> <span data-ttu-id="b9585-276">請檢視此範例，瞭解我所說的內容。</span><span class="sxs-lookup"><span data-stu-id="b9585-276">Take a look at this example to see that I'm talking about.</span></span>

```powershell
PS> $data = @(1,2,3,4)
PS> -join $data
1234
```

### <a name="-replace-and--split"></a><span data-ttu-id="b9585-277">-replace 與 -split</span><span class="sxs-lookup"><span data-stu-id="b9585-277">-replace and -split</span></span>

<span data-ttu-id="b9585-278">`-replace` 和 `-split` 等其他運算子會在陣列中的每個項目上執行。</span><span class="sxs-lookup"><span data-stu-id="b9585-278">The other operators like `-replace` and `-split` execute on each item in the array.</span></span> <span data-ttu-id="b9585-279">我不能說我曾用過這種方式，但這裡有一個範例。</span><span class="sxs-lookup"><span data-stu-id="b9585-279">I can't say that I have ever used them this way but here is an example.</span></span>

```powershell
PS> $data = @('ATX-SQL-01','ATX-SQL-02','ATX-SQL-03')
PS> $data -replace 'ATX','LAX'
LAX-SQL-01
LAX-SQL-02
LAX-SQL-03
```

### <a name="-contains"></a><span data-ttu-id="b9585-280">-contains</span><span class="sxs-lookup"><span data-stu-id="b9585-280">-contains</span></span>

<span data-ttu-id="b9585-281">`-contains` 運算子可讓您檢查值的陣列，以查看其是否包含指定的值。</span><span class="sxs-lookup"><span data-stu-id="b9585-281">The `-contains` operator allows you to check an array of values to see if it contains a specified value.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $data -contains 'green'
True
```

### <a name="-in"></a><span data-ttu-id="b9585-282">-in</span><span class="sxs-lookup"><span data-stu-id="b9585-282">-in</span></span>

<span data-ttu-id="b9585-283">當您有想要驗證的單一值符合數個值的其中之一時，您可以使用 `-in` 運算子。</span><span class="sxs-lookup"><span data-stu-id="b9585-283">When you have a single value that you would like to verify matches one of several values, you can use the `-in` operator.</span></span> <span data-ttu-id="b9585-284">這個值會在左邊，而陣列位於運算子右側。</span><span class="sxs-lookup"><span data-stu-id="b9585-284">The value would be on the left and the array on the right-hand side of the operator.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> 'green' -in $data
True
```

<span data-ttu-id="b9585-285">如果清單很大，這可能會產生昂貴的費用。</span><span class="sxs-lookup"><span data-stu-id="b9585-285">This can get expensive if the list is large.</span></span> <span data-ttu-id="b9585-286">如果我檢查的值不是少數幾個，我通常會使用 RegEx 模式。</span><span class="sxs-lookup"><span data-stu-id="b9585-286">I often use a regex pattern if I'm checking more than a few values.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $pattern = "^({0})$" -f ($data -join '|')
PS> $pattern
^(red|green|blue)$

PS> 'green' -match $pattern
True
```

### <a name="-eq-and--ne"></a><span data-ttu-id="b9585-287">-eq 和-ne</span><span class="sxs-lookup"><span data-stu-id="b9585-287">-eq and -ne</span></span>

<span data-ttu-id="b9585-288">等式和陣列可能會變得複雜。</span><span class="sxs-lookup"><span data-stu-id="b9585-288">Equality and arrays can get complicated.</span></span> <span data-ttu-id="b9585-289">當陣列位於左側時，會比較每個項目。</span><span class="sxs-lookup"><span data-stu-id="b9585-289">When the array is on the left side, every item gets compared.</span></span> <span data-ttu-id="b9585-290">這樣並不會傳回 `True`，而是會傳回符合的物件。</span><span class="sxs-lookup"><span data-stu-id="b9585-290">Instead of returning `True`, it returns the object that matches.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $data -eq 'green'
green
```

<span data-ttu-id="b9585-291">當您使用 `-ne` 運算子時，我們會取得所有與我們值不相等的值。</span><span class="sxs-lookup"><span data-stu-id="b9585-291">When you use the `-ne` operator, we get all the values that are not equal to our value.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $data -ne 'green'
red
blue
```

<span data-ttu-id="b9585-292">當您在 `if()` 陳述式中使用這種方式時，傳回的值就是 `True` 值。</span><span class="sxs-lookup"><span data-stu-id="b9585-292">When you use this in an `if()` statement, a value that is returned is a `True` value.</span></span> <span data-ttu-id="b9585-293">如果未傳回任何值，則為 `False` 值。</span><span class="sxs-lookup"><span data-stu-id="b9585-293">If no value is returned, then it's a `False` value.</span></span> <span data-ttu-id="b9585-294">這兩個後續陳述式都會評估為 `True`。</span><span class="sxs-lookup"><span data-stu-id="b9585-294">Both of these next statements evaluate to `True`.</span></span>

```powershell
$data = @('red','green','blue')
if ( $data -eq 'green' )
{
    'Green was found'
}
if ( $data -ne 'green' )
{
    'And green was not found'
}
```

<span data-ttu-id="b9585-295">我稍後會回顧一下我們談到的 `$null` 的測試。</span><span class="sxs-lookup"><span data-stu-id="b9585-295">I'll revisit this in a moment when we talk about testing for `$null`.</span></span>

### <a name="-match"></a><span data-ttu-id="b9585-296">-match</span><span class="sxs-lookup"><span data-stu-id="b9585-296">-match</span></span>

<span data-ttu-id="b9585-297">`-match` 運算子會嘗試比對集合中的每個項目。</span><span class="sxs-lookup"><span data-stu-id="b9585-297">The `-match` operator tries to match each item in the collection.</span></span>

```powershell
PS> $servers = @(
    'LAX-SQL-01'
    'LAX-API-01'
    'ATX-SQL-01'
    'ATX-API-01'
)
PS> $servers -match 'SQL'
LAX-SQL-01
ATX-SQL-01
```

<span data-ttu-id="b9585-298">當您使用具有單一值的 `-match` 時，會以符合的資訊填入一個特殊的變數 `$Matches`。</span><span class="sxs-lookup"><span data-stu-id="b9585-298">When you use `-match` with a single value, a special variable `$Matches` gets populated with match info.</span></span> <span data-ttu-id="b9585-299">若以這種方式處理陣列，就不會出現這種情況。</span><span class="sxs-lookup"><span data-stu-id="b9585-299">This isn't the case when an array is processed this way.</span></span>

<span data-ttu-id="b9585-300">我們可以採用與 `Select-String` 相同的方法。</span><span class="sxs-lookup"><span data-stu-id="b9585-300">We can take the same approach with `Select-String`.</span></span>

```powershell
$servers | Select-String SQL
```

<span data-ttu-id="b9585-301">我會進一步檢視 `Select-String`、`-match` 和另一篇文章 ([使用 RegEx 的許多方式][] (英文)) 中的 `$matches` 變數。</span><span class="sxs-lookup"><span data-stu-id="b9585-301">I take a closer look at `Select-String`,`-match` and the `$matches` variable in another post called [The many ways to use regex][].</span></span>

### <a name="null-or-empty"></a><span data-ttu-id="b9585-302">$null 或 empty</span><span class="sxs-lookup"><span data-stu-id="b9585-302">$null or empty</span></span>

<span data-ttu-id="b9585-303">測試 `$null` 或空陣列可能會很棘手。</span><span class="sxs-lookup"><span data-stu-id="b9585-303">Testing for `$null` or empty arrays can be tricky.</span></span> <span data-ttu-id="b9585-304">以下是陣列的常見陷阱。</span><span class="sxs-lookup"><span data-stu-id="b9585-304">Here are the common traps with arrays.</span></span>

<span data-ttu-id="b9585-305">乍看之下，這個陳述式看起來應該可以運作。</span><span class="sxs-lookup"><span data-stu-id="b9585-305">At a glance, this statement looks like it should work.</span></span>

```powershell
if ( $array -eq $null)
{
    'Array is $null'
}
```

<span data-ttu-id="b9585-306">但是我只是在 `-eq` 檢查陣列中的每個項目。</span><span class="sxs-lookup"><span data-stu-id="b9585-306">But I just went over how `-eq` checks each item in the array.</span></span> <span data-ttu-id="b9585-307">因此，我們可以擁有數個項目的陣列，其中包含單一 $null 值，而且該值會評估為 `$true`</span><span class="sxs-lookup"><span data-stu-id="b9585-307">So we can have an array of several items with a single $null value and it would evaluate to `$true`</span></span>

```powershell
$array = @('one',$null,'three')
if ( $array -eq $null)
{
    'I think Array is $null, but I would be wrong'
}
```

<span data-ttu-id="b9585-308">這就是將 `$null` 放在運算子左邊是最佳做法的理由所在。</span><span class="sxs-lookup"><span data-stu-id="b9585-308">This is why it's a best practice to place the `$null` on the left side of the operator.</span></span> <span data-ttu-id="b9585-309">這會讓此情況成為不會發生的問題。</span><span class="sxs-lookup"><span data-stu-id="b9585-309">This makes this scenario a non-issue.</span></span>

```powershell
if ( $null -eq $array )
{
    'Array actually is $null'
}
```

<span data-ttu-id="b9585-310">`$null` 陣列與空陣列屬於不同的陣列。</span><span class="sxs-lookup"><span data-stu-id="b9585-310">A `$null` array isn't the same thing as an empty array.</span></span> <span data-ttu-id="b9585-311">若您知道自己有陣列，請檢查其中的物件計數。</span><span class="sxs-lookup"><span data-stu-id="b9585-311">If you know you have an array, check the count of objects in it.</span></span> <span data-ttu-id="b9585-312">如果陣列為 `$null`，則計數為 `0`。</span><span class="sxs-lookup"><span data-stu-id="b9585-312">If the array is `$null`, the count is `0`.</span></span>

```powershell
if ( $array.count -gt 0 )
{
    "Array isn't empty"
}
```

<span data-ttu-id="b9585-313">這裡還有另一個要注意的陷阱。</span><span class="sxs-lookup"><span data-stu-id="b9585-313">There is one more trap to watch out for here.</span></span> <span data-ttu-id="b9585-314">即使您有單一物件，您仍然可以使用 `count`，除非該物件是 `PSCustomObject`。</span><span class="sxs-lookup"><span data-stu-id="b9585-314">You can use the `count` even if you have a single object, unless that object is a `PSCustomObject`.</span></span> <span data-ttu-id="b9585-315">這是 PowerShell 6.1 中所修正的錯誤。</span><span class="sxs-lookup"><span data-stu-id="b9585-315">This is a bug that is fixed in PowerShell 6.1.</span></span>
<span data-ttu-id="b9585-316">這是好消息，但有很多人仍在使用 5.1，而且需要留意。</span><span class="sxs-lookup"><span data-stu-id="b9585-316">That's good news, but a lot of people are still on 5.1 and need to watch out for it.</span></span>

```powershell
PS> $object = [PSCustomObject]@{Name='TestObject'}
PS> $object.count
$null
```

<span data-ttu-id="b9585-317">如果您仍在使用 PowerShell 5.1，您可以先將物件包裝在陣列中，再檢查計數以取得精確的計數。</span><span class="sxs-lookup"><span data-stu-id="b9585-317">If you're still on PowerShell 5.1, you can wrap the object in an array before checking the count to get an accurate count.</span></span>

```powershell
if ( @($array).count -gt 0 )
{
    "Array isn't empty"
}
```

<span data-ttu-id="b9585-318">為了充分確保安全起見，請檢查 `$null`，然後檢查計數。</span><span class="sxs-lookup"><span data-stu-id="b9585-318">To fully play it safe, check for `$null`, then check the count.</span></span>

```powershell
if ( $null -ne $array -and @($array).count -gt 0 )
{
    "Array isn't empty"
}
```

### <a name="all--eq"></a><span data-ttu-id="b9585-319">全部 -eq</span><span class="sxs-lookup"><span data-stu-id="b9585-319">All -eq</span></span>

<span data-ttu-id="b9585-320">我最近看到有人詢問 [如何驗證陣列中的每個值是否符合指定的值][]。</span><span class="sxs-lookup"><span data-stu-id="b9585-320">I recently saw someone ask [how to verify that every value in an array matches a given value][].</span></span>
<span data-ttu-id="b9585-321">Reddit 使用者 **/u/bis** 享有這項聰明的 [解決方案][]，可檢查是否有任何不正確的值，然後將結果翻轉。</span><span class="sxs-lookup"><span data-stu-id="b9585-321">Reddit user **/u/bis** had this clever [solution][] that checks for any incorrect values and then flips the result.</span></span>

```powershell
$results = Test-Something
if ( -not ( $results -ne 'Passed') )
{
    'All results a Passed'
}
```

## <a name="adding-to-arrays"></a><span data-ttu-id="b9585-322">新增至陣列</span><span class="sxs-lookup"><span data-stu-id="b9585-322">Adding to arrays</span></span>

<span data-ttu-id="b9585-323">此時，您會開始對如何將項目新增至陣列感到懷疑。</span><span class="sxs-lookup"><span data-stu-id="b9585-323">At this point, you're starting to wonder how to add items to an array.</span></span> <span data-ttu-id="b9585-324">簡單明瞭的答案就是您無法將項目新增至陣列。</span><span class="sxs-lookup"><span data-stu-id="b9585-324">The quick answer is that you can't.</span></span> <span data-ttu-id="b9585-325">陣列在記憶體中的大小是固定的。</span><span class="sxs-lookup"><span data-stu-id="b9585-325">An array is a fixed size in memory.</span></span> <span data-ttu-id="b9585-326">如果您需要擴充陣列或在其中加入單一項目，則需要建立新的陣列，並將所有的值複製到舊陣列。</span><span class="sxs-lookup"><span data-stu-id="b9585-326">If you need to grow it or add a single item to it, then you need to create a new array and copy all the values over from the old array.</span></span> <span data-ttu-id="b9585-327">就跟很多工作一樣，這聽起來十分費工；不過，PowerShell 會隱藏建立新陣列的複雜性。</span><span class="sxs-lookup"><span data-stu-id="b9585-327">This sounds like a lot of work, however, PowerShell hides the complexity of creating the new array.</span></span> <span data-ttu-id="b9585-328">PowerShell 會為陣列實作新增運算子 (`+`)。</span><span class="sxs-lookup"><span data-stu-id="b9585-328">PowerShell implements the addition operator (`+`) for arrays.</span></span>

> [!NOTE]
> <span data-ttu-id="b9585-329">PowerShell 不會實作減法運算。</span><span class="sxs-lookup"><span data-stu-id="b9585-329">PowerShell does not implement a subtraction operation.</span></span> <span data-ttu-id="b9585-330">如果您想要有彈性的陣列替代方案，則必須使用[泛型`List`](#generic-list)物件。</span><span class="sxs-lookup"><span data-stu-id="b9585-330">If you want a flexible alternative to an array, you need to use a [generic `List`](#generic-list) object.</span></span>

### <a name="array-addition"></a><span data-ttu-id="b9585-331">新增陣列</span><span class="sxs-lookup"><span data-stu-id="b9585-331">Array addition</span></span>

<span data-ttu-id="b9585-332">我們可以搭配使用新增運算子與陣列來建立新的陣列。</span><span class="sxs-lookup"><span data-stu-id="b9585-332">We can use the addition operator with arrays to create a new array.</span></span> <span data-ttu-id="b9585-333">因此，假設有這兩個陣列：</span><span class="sxs-lookup"><span data-stu-id="b9585-333">So given these two arrays:</span></span>

```powershell
$first = @(
    'Zero'
    'One'
)
$second = @(
    'Two'
    'Three'
)
```

<span data-ttu-id="b9585-334">我們可以將其合併以取得新的陣列。</span><span class="sxs-lookup"><span data-stu-id="b9585-334">We can add them together to get a new array.</span></span>

```powershell
PS> $first + $second

Zero
One
Two
Three
```

### <a name="plus-equals-"></a><span data-ttu-id="b9585-335">Plus equals +=</span><span class="sxs-lookup"><span data-stu-id="b9585-335">Plus equals +=</span></span>

<span data-ttu-id="b9585-336">我們可以就地建立新的陣列，並在其中新增項目，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b9585-336">We can create a new array in place and add an item to it like this:</span></span>

```powershell
$data = @(
    'Zero'
    'One'
    'Two'
    'Three'
)
$data += 'four'
```

<span data-ttu-id="b9585-337">請記住，您每次使用 `+=` 時，都會複製並建立新的陣列。</span><span class="sxs-lookup"><span data-stu-id="b9585-337">Just remember that every time you use `+=` that you're duplicating and creating a new array.</span></span> <span data-ttu-id="b9585-338">這不是小型資料集的問題，而是以極不理想的方式進行規模調整。</span><span class="sxs-lookup"><span data-stu-id="b9585-338">This is a not an issue for small datasets but it scales extremely poorly.</span></span>

### <a name="pipeline-assignment"></a><span data-ttu-id="b9585-339">管道指派</span><span class="sxs-lookup"><span data-stu-id="b9585-339">Pipeline assignment</span></span>

<span data-ttu-id="b9585-340">您可以將任何管道的結果指派至變數中。</span><span class="sxs-lookup"><span data-stu-id="b9585-340">You can assign the results of any pipeline into a variable.</span></span> <span data-ttu-id="b9585-341">如果其中包含多個項目，則為陣列。</span><span class="sxs-lookup"><span data-stu-id="b9585-341">It's an array if it contains multiple items.</span></span>

```powershell
$array = 1..5 | ForEach-Object {
    "ATX-SQL-$PSItem"
}
```

<span data-ttu-id="b9585-342">通常當我們想要使用管道時，我們會考慮使用一般的 PowerShell 一行程式碼。</span><span class="sxs-lookup"><span data-stu-id="b9585-342">Normally when we think of using the pipeline, we think of the typical PowerShell one-liners.</span></span> <span data-ttu-id="b9585-343">我們可以利用管道搭配 `foreach()` 陳述式和其他迴圈。</span><span class="sxs-lookup"><span data-stu-id="b9585-343">We can leverage the pipeline with `foreach()` statements and other loops.</span></span> <span data-ttu-id="b9585-344">因此，我們不會將項目新增至迴圈中的陣列，而是可以將項目放置在管道上。</span><span class="sxs-lookup"><span data-stu-id="b9585-344">So instead of adding items to an array in a loop, we can drop items onto the pipeline.</span></span>

```powershell
$array = foreach ( $node in (1..5))
{
    "ATX-SQL-$node"
}
```

## <a name="array-types"></a><span data-ttu-id="b9585-345">陣列類型</span><span class="sxs-lookup"><span data-stu-id="b9585-345">Array Types</span></span>

<span data-ttu-id="b9585-346">根據預設，系統建立 PowerShell 中的陣列做為 `[PSObject[]]` 類型。</span><span class="sxs-lookup"><span data-stu-id="b9585-346">By default, an array in PowerShell is created as a `[PSObject[]]` type.</span></span> <span data-ttu-id="b9585-347">如此可使其包含任何類型的物件或值。</span><span class="sxs-lookup"><span data-stu-id="b9585-347">This allows it to contain any type of object or value.</span></span> <span data-ttu-id="b9585-348">這種方式有效，是因為所有項目都是從 `PSObject` 類型繼承而來。</span><span class="sxs-lookup"><span data-stu-id="b9585-348">This works because everything is inherited from the `PSObject` type.</span></span>

### <a name="strongly-typed-arrays"></a><span data-ttu-id="b9585-349">強類型陣列</span><span class="sxs-lookup"><span data-stu-id="b9585-349">Strongly typed arrays</span></span>

<span data-ttu-id="b9585-350">您可以使用類似的語法來建立任何類型的陣列。</span><span class="sxs-lookup"><span data-stu-id="b9585-350">You can create an array of any type using a similar syntax.</span></span> <span data-ttu-id="b9585-351">當您建立強類型陣列時，它只能包含指定類型的值或物件。</span><span class="sxs-lookup"><span data-stu-id="b9585-351">When you create a strongly typed array, it can only contain values or objects the specified type.</span></span>

```powershell
PS> [int[]] $numbers = 1,2,3
PS> [int[]] $numbers2 = 'one','two','three'
ERROR: Cannot convert value "one" to type "System.Int32". Input string was not in a correct format."

PS> [string[]] $strings = 'one','two','three'
```

### <a name="arraylist"></a><span data-ttu-id="b9585-352">ArrayList</span><span class="sxs-lookup"><span data-stu-id="b9585-352">ArrayList</span></span>

<span data-ttu-id="b9585-353">將項目新增至陣列是其最大的限制之一，但還有一些其他集合可供我們使用，從而解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="b9585-353">Adding items to an array is one of its biggest limitations, but there are a few other collections that we can turn to that solve this problem.</span></span>

<span data-ttu-id="b9585-354">當我們需要更快速使用的陣列時，`ArrayList` 通常是我們想到的第一個辦法。</span><span class="sxs-lookup"><span data-stu-id="b9585-354">The `ArrayList` is commonly one of the first things that we think of when we need an array that is faster to work with.</span></span> <span data-ttu-id="b9585-355">它的作用就像是物件陣列，我們在任何場合都需要它，但它會快速地處理新增項目。</span><span class="sxs-lookup"><span data-stu-id="b9585-355">It acts like an object array every place that we need it, but it handles adding items quickly.</span></span>

<span data-ttu-id="b9585-356">以下是我們建立 `ArrayList` 並在其中新增項目的方式。</span><span class="sxs-lookup"><span data-stu-id="b9585-356">Here is how we create an `ArrayList` and add items to it.</span></span>

```powershell
$myarray = [System.Collections.ArrayList]::new()
[void]$myArray.Add('Value')
```

<span data-ttu-id="b9585-357">我們會呼叫 .NET 來取得這種類型。</span><span class="sxs-lookup"><span data-stu-id="b9585-357">We are calling into .NET to get this type.</span></span> <span data-ttu-id="b9585-358">在此情況下，我們會使用預設的建構函式來建立它。</span><span class="sxs-lookup"><span data-stu-id="b9585-358">In this case, we are using the default constructor to create it.</span></span> <span data-ttu-id="b9585-359">然後，我們會呼叫 `Add` 方法，並將項目新增至其中。</span><span class="sxs-lookup"><span data-stu-id="b9585-359">Then we call the `Add` method to add an item to it.</span></span>

<span data-ttu-id="b9585-360">我在行首使用 `[void]` 的原因，是要隱藏傳回程式碼。</span><span class="sxs-lookup"><span data-stu-id="b9585-360">The reason I'm using `[void]` at the beginning of the line is to suppress the return code.</span></span> <span data-ttu-id="b9585-361">有些 .NET 呼叫會執行此動作，而且可能會產生非預期的輸出。</span><span class="sxs-lookup"><span data-stu-id="b9585-361">Some .NET calls do this and can create unexpected output.</span></span>

<span data-ttu-id="b9585-362">如果您在陣列中的唯一資料是字串，則也請瞭解 [StringBuilder][] 的使用方式。</span><span class="sxs-lookup"><span data-stu-id="b9585-362">If the only data that you have in your array is strings, then also take a look at using [StringBuilder][].</span></span> <span data-ttu-id="b9585-363">這幾乎是相同的東西，但有一些僅供處理字串的方法。</span><span class="sxs-lookup"><span data-stu-id="b9585-363">It's almost the same thing but has some methods that are just for dealing with strings.</span></span> <span data-ttu-id="b9585-364">`StringBuilder` 是專為效能而特別設計的。</span><span class="sxs-lookup"><span data-stu-id="b9585-364">The `StringBuilder` is specially designed for performance.</span></span>

<span data-ttu-id="b9585-365">人們從陣列移至 `ArrayList` 的情況很常見。</span><span class="sxs-lookup"><span data-stu-id="b9585-365">It's common to see people move to `ArrayList` from arrays.</span></span> <span data-ttu-id="b9585-366">但這種情況發生在 C# 並未提供泛型支援的時代。</span><span class="sxs-lookup"><span data-stu-id="b9585-366">But it comes from a time where C# didn't have generic support.</span></span> <span data-ttu-id="b9585-367">`ArrayList` 在泛型的 `List[]` 支援中已淘汰</span><span class="sxs-lookup"><span data-stu-id="b9585-367">The `ArrayList` is deprecated in support for the generic `List[]`</span></span>

### <a name="generic-list"></a><span data-ttu-id="b9585-368">泛型清單</span><span class="sxs-lookup"><span data-stu-id="b9585-368">Generic List</span></span>

<span data-ttu-id="b9585-369">泛型型別是中的特殊類型 C# ，可定義一般化類別，而使用者會指定它在建立時所使用的資料類型。</span><span class="sxs-lookup"><span data-stu-id="b9585-369">A generic type is a special type in C# that defines a generalized class and the user specifies the data types it uses when created.</span></span> <span data-ttu-id="b9585-370">因此，如果您需要數字或字串的清單，您可以定義想要 `int` 或 `string` 類型的清單。</span><span class="sxs-lookup"><span data-stu-id="b9585-370">So if you want a list of numbers or strings, you would define that you want list of `int` or `string` types.</span></span>

<span data-ttu-id="b9585-371">以下是建立字串清單的方式。</span><span class="sxs-lookup"><span data-stu-id="b9585-371">Here is how you create a List for strings.</span></span>

```powershell
$mylist = [System.Collections.Generic.List[string]]::new()
```

<span data-ttu-id="b9585-372">或者您也可以數字的清單。</span><span class="sxs-lookup"><span data-stu-id="b9585-372">Or a list for numbers.</span></span>

```powershell
$mylist = [System.Collections.Generic.List[int]]::new()
```

<span data-ttu-id="b9585-373">我們可以將現有的陣列轉換成類似如下的清單，而且不需要先建立物件：</span><span class="sxs-lookup"><span data-stu-id="b9585-373">We can cast an existing array to a list like this without creating the object first:</span></span>

```powershell
$mylist = [System.Collections.Generic.List[int]]@(1,2,3)
```

<span data-ttu-id="b9585-374">我們可以使用 PowerShell 5 和更新版本中的 `using namespace` 陳述式來縮短語法。</span><span class="sxs-lookup"><span data-stu-id="b9585-374">We can shorten the syntax with the `using namespace` statement in PowerShell 5 and newer.</span></span> <span data-ttu-id="b9585-375">`using` 陳述式必須是指令碼的第一行。</span><span class="sxs-lookup"><span data-stu-id="b9585-375">The `using` statement needs to be the first line of your script.</span></span> <span data-ttu-id="b9585-376">藉由宣告命名空間，PowerShell 可讓您在參考資料類型時，將其剔除。</span><span class="sxs-lookup"><span data-stu-id="b9585-376">By declaring a namespace, PowerShell lets you leave it off of the data types when you reference them.</span></span>

```powershell
using namespace System.Collections.Generic
$myList = [List[int]]@(1,2,3)
```

<span data-ttu-id="b9585-377">這可讓 `List` 變得更容易使用。</span><span class="sxs-lookup"><span data-stu-id="b9585-377">This makes the `List` much more usable.</span></span>

<span data-ttu-id="b9585-378">您可以使用類似 `Add` 的方法。</span><span class="sxs-lookup"><span data-stu-id="b9585-378">You have a similar `Add` method available to you.</span></span> <span data-ttu-id="b9585-379">有別於 ArrayList，`Add` 方法沒有傳回值，因此我們不需要 `void` 它。</span><span class="sxs-lookup"><span data-stu-id="b9585-379">Unlike the ArrayList, there is no return value on the `Add` method so we don't have to `void` it.</span></span>

```powershell
$myList.Add(10)
```

<span data-ttu-id="b9585-380">我們仍然可以存取其他陣列之類的元素。</span><span class="sxs-lookup"><span data-stu-id="b9585-380">And we can still access the elements like other arrays.</span></span>

```powershell
PS> $myList[-1]
10
```

#### <a name="listpsobject"></a><span data-ttu-id="b9585-381">List[PSObject]</span><span class="sxs-lookup"><span data-stu-id="b9585-381">List[PSObject]</span></span>

<span data-ttu-id="b9585-382">您可擁有任何類型的清單，但在不知道物件類型時，可使用 `[List[PSObject]]` 加以包含。</span><span class="sxs-lookup"><span data-stu-id="b9585-382">You can have a list of any type, but when you don't know the type of objects, you can use `[List[PSObject]]` to contain them.</span></span>

```powershell
$list = [List[PSObject]]::new()
```

#### <a name="remove"></a><span data-ttu-id="b9585-383">Remove()</span><span class="sxs-lookup"><span data-stu-id="b9585-383">Remove()</span></span>

<span data-ttu-id="b9585-384">`ArrayList` 和泛型 `List[]` 都支援從集合中移除項目。</span><span class="sxs-lookup"><span data-stu-id="b9585-384">The `ArrayList` and the generic `List[]` both support removing items from the collection.</span></span>

```powershell
using namespace System.Collections.Generic
$myList = [List[string]]@('Zero','One','Two','Three')
[void]$myList.Remove("Two")
Zero
One
Three
```

<span data-ttu-id="b9585-385">使用實值型別時，它會從清單中移除第一個項目。</span><span class="sxs-lookup"><span data-stu-id="b9585-385">When working with value types, it removes the first one from the list.</span></span> <span data-ttu-id="b9585-386">您可以再次呼叫它，以便繼續移除該值。</span><span class="sxs-lookup"><span data-stu-id="b9585-386">You can call it over and over again to keep removing that value.</span></span> <span data-ttu-id="b9585-387">如果您有參考型別，則您必須提供要移除的物件。</span><span class="sxs-lookup"><span data-stu-id="b9585-387">If you have reference types, you have to provide the object that you want removed.</span></span>

```powershell
[list[System.Management.Automation.PSDriveInfo]]$drives = Get-PSDrive
$drives.remove($drives[2])
```

```powershell
$delete = $drives[2]
$drives.remove($delete)
```

<span data-ttu-id="b9585-388">如果可以從集合中尋找並移除項目，則 remove 方法會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="b9585-388">The remove method returns `true` if it was able to find and remove the item from the collection.</span></span>

### <a name="more-collections"></a><span data-ttu-id="b9585-389">更多集合</span><span class="sxs-lookup"><span data-stu-id="b9585-389">More collections</span></span>

<span data-ttu-id="b9585-390">還有許多其他可以使用的集合，但是有良好的泛型陣列替代品。</span><span class="sxs-lookup"><span data-stu-id="b9585-390">There are many other collections that can be used but these are the good generic array replacements.</span></span>
<span data-ttu-id="b9585-391">如果您想要深入瞭解更多選項，請查看此 [Gist](https://gist.github.com/kevinblumenfeld/4a698dbc90272a336ed9367b11d91f1c)，那是由 [Mark Kraus](https://get-powershellblog.blogspot.com/2016/11/about-mark-kraus.html) 合併在一起的。</span><span class="sxs-lookup"><span data-stu-id="b9585-391">If you're interested in learning about more of these options, take a look at this [Gist](https://gist.github.com/kevinblumenfeld/4a698dbc90272a336ed9367b11d91f1c) that [Mark Kraus](https://get-powershellblog.blogspot.com/2016/11/about-mark-kraus.html) put together.</span></span>

## <a name="other-nuances"></a><span data-ttu-id="b9585-392">其他細微差異</span><span class="sxs-lookup"><span data-stu-id="b9585-392">Other nuances</span></span>

<span data-ttu-id="b9585-393">現在我已經討論過所有的主要功能，接下來我要提到幾件事，再進行總結。</span><span class="sxs-lookup"><span data-stu-id="b9585-393">Now that I have covered all the major functionality, here are a few more things that I wanted to mention before I wrap this up.</span></span>

### <a name="pre-sized-arrays"></a><span data-ttu-id="b9585-394">預先調整大小的陣列</span><span class="sxs-lookup"><span data-stu-id="b9585-394">Pre-sized arrays</span></span>

<span data-ttu-id="b9585-395">我說過，一旦建立陣列之後，您就無法變更它的大小。</span><span class="sxs-lookup"><span data-stu-id="b9585-395">I mentioned that you can't change the size of an array once it's created.</span></span> <span data-ttu-id="b9585-396">我們可以使用 `new($size)` 建構函式來呼叫它，以建立預先決定大小的陣列。</span><span class="sxs-lookup"><span data-stu-id="b9585-396">We can create an array of a pre-determined size by calling it with the `new($size)` constructor.</span></span>

```powershell
$data = [Object[]]::new(4)
$data.count
4
```

### <a name="multiplying-arrays"></a><span data-ttu-id="b9585-397">相乘陣列</span><span class="sxs-lookup"><span data-stu-id="b9585-397">Multiplying arrays</span></span>

<span data-ttu-id="b9585-398">有趣的小技巧是，您可以將陣列乘以一個整數。</span><span class="sxs-lookup"><span data-stu-id="b9585-398">An interesting little trick is that you can multiply an array by an integer.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $data * 3
red
green
blue
red
green
blue
red
green
blue
```

### <a name="initialize-with-0"></a><span data-ttu-id="b9585-399">以 0 初始化</span><span class="sxs-lookup"><span data-stu-id="b9585-399">Initialize with 0</span></span>

<span data-ttu-id="b9585-400">常見的情況是您想要建立全部為零的陣列。</span><span class="sxs-lookup"><span data-stu-id="b9585-400">A common scenario is that you want to create an array with all zeros.</span></span> <span data-ttu-id="b9585-401">如果您只會有整數，則強型別的整數陣列會預設為全部為零。</span><span class="sxs-lookup"><span data-stu-id="b9585-401">If you're only going to have integers, a strongly typed array of integers defaults to all zeros.</span></span>

```powershell
PS> [int[]]::new(4)
0
0
0
0
```

<span data-ttu-id="b9585-402">我們也可以使用相乘的技巧來執行此動作。</span><span class="sxs-lookup"><span data-stu-id="b9585-402">We can use the multiplying trick to do this too.</span></span>

```powershell
PS> $data = @(0) * 4
PS> $data
0
0
0
0
```

<span data-ttu-id="b9585-403">「相乘」技巧的好處是您可以使用任何值。</span><span class="sxs-lookup"><span data-stu-id="b9585-403">The nice thing about the multiplying trick is that you can use any value.</span></span> <span data-ttu-id="b9585-404">因此，如果您想要以 `255` 做為預設值，這會是很好的方式。</span><span class="sxs-lookup"><span data-stu-id="b9585-404">So if you would rather have `255` as your default value, this would be a good way to do it.</span></span>

```powershell
PS> $data = @(255) * 4
PS> $data
255
255
255
255
```

### <a name="nested-arrays"></a><span data-ttu-id="b9585-405">嵌套陣列</span><span class="sxs-lookup"><span data-stu-id="b9585-405">Nested arrays</span></span>

<span data-ttu-id="b9585-406">陣列中的陣列稱為「嵌套陣列」。</span><span class="sxs-lookup"><span data-stu-id="b9585-406">An array inside an array is called a nested array.</span></span> <span data-ttu-id="b9585-407">我不會在 PowerShell 中使用這些功能，但我在其他程式設計語言中使用了這些功能。</span><span class="sxs-lookup"><span data-stu-id="b9585-407">I don't use these much in PowerShell but I have used them more in other languages.</span></span> <span data-ttu-id="b9585-408">當您的資料符合資料格 (如模式) 時，請考慮在各陣列中使用一個陣列。</span><span class="sxs-lookup"><span data-stu-id="b9585-408">Consider using an array of arrays when your data fits in a grid like pattern.</span></span>

<span data-ttu-id="b9585-409">這裡提供兩種方式可以建立二維陣列。</span><span class="sxs-lookup"><span data-stu-id="b9585-409">Here are two ways we can create a two-dimensional array.</span></span>

```powershell
$data = @(@(1,2,3),@(4,5,6),@(7,8,9))

$data2 = @(
    @(1,2,3),
    @(4,5,6),
    @(7,8,9)
)
```

<span data-ttu-id="b9585-410">在這些範例中，逗點非常重要。</span><span class="sxs-lookup"><span data-stu-id="b9585-410">The comma is very important in those examples.</span></span> <span data-ttu-id="b9585-411">我先前針對多行提供了一個一般陣列的範例，其中逗號是選擇性使用的。</span><span class="sxs-lookup"><span data-stu-id="b9585-411">I gave an earlier example of a normal array on multiple lines where the comma was optional.</span></span> <span data-ttu-id="b9585-412">多維陣列則不會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="b9585-412">That isn't the case with a multi-dimensional array.</span></span>

<span data-ttu-id="b9585-413">我們使用索引標記法的方式現在有了些許變更，因為我們已經有了嵌套陣列。</span><span class="sxs-lookup"><span data-stu-id="b9585-413">The way we use the index notation changes slightly now that we've a nested array.</span></span> <span data-ttu-id="b9585-414">使用上述 `$data`，這就是我們存取值 3 的方式。</span><span class="sxs-lookup"><span data-stu-id="b9585-414">Using the `$data` above, this is how we would access the value 3.</span></span>

```powershell
PS> $outside = 0
PS> $inside = 2
PS> $data[$outside][$inside]
3
```

<span data-ttu-id="b9585-415">為每個陣列嵌套層級新增一組括弧。</span><span class="sxs-lookup"><span data-stu-id="b9585-415">Add a set of bracket for each level of array nesting.</span></span> <span data-ttu-id="b9585-416">第一組括弧是針對最外部的陣列，然後以您的方式從該處開始作業。</span><span class="sxs-lookup"><span data-stu-id="b9585-416">The first set of brackets is for the outer most array and then you work your way in from there.</span></span>

### <a name="write-output--noenumerate"></a><span data-ttu-id="b9585-417">Write-Output -NoEnumerate</span><span class="sxs-lookup"><span data-stu-id="b9585-417">Write-Output -NoEnumerate</span></span>

<span data-ttu-id="b9585-418">PowerShell 習慣取消換行或列舉陣列。</span><span class="sxs-lookup"><span data-stu-id="b9585-418">PowerShell likes to unwrap or enumerate arrays.</span></span> <span data-ttu-id="b9585-419">這是 PowerShell 使用管道的核心層面，但有時您不希望出現這種情況。</span><span class="sxs-lookup"><span data-stu-id="b9585-419">This is a core aspect of the way PowerShell uses the pipeline but there are times that you don't want that to happen.</span></span>

<span data-ttu-id="b9585-420">我通常會將物件輸送至 `Get-Member` 以便進行深入瞭解。</span><span class="sxs-lookup"><span data-stu-id="b9585-420">I commonly pipe objects to `Get-Member` to learn more about them.</span></span> <span data-ttu-id="b9585-421">當我使用管道將陣列輸送給它時，它會取消換行，而 Get-Member 會看到陣列的成員，而不是實際的陣列。</span><span class="sxs-lookup"><span data-stu-id="b9585-421">When I pipe an array to it, it gets unwrapped and Get-Member sees the members of the array and not the actual array.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $data | Get-Member
TypeName: System.String
...
```

<span data-ttu-id="b9585-422">若要避免陣列取消換行，您可以使用 `Write-Object -NoEnumerate`。</span><span class="sxs-lookup"><span data-stu-id="b9585-422">To prevent that unwrap of the array, you can use `Write-Object -NoEnumerate`.</span></span>

```powershell
PS> Write-Output -NoEnumerate $data | Get-Member
TypeName: System.Object[]
...
```

<span data-ttu-id="b9585-423">我還有第二種方式，也就是駭客入侵的手法 (而且我試著避免這類的駭客入侵守法)。</span><span class="sxs-lookup"><span data-stu-id="b9585-423">I have a second way that's more of a hack (and I try to avoid hacks like this).</span></span> <span data-ttu-id="b9585-424">您可以將逗號放在陣列前方，然後再使用管道輸送。</span><span class="sxs-lookup"><span data-stu-id="b9585-424">You can place a comma in front of the array before you pipe it.</span></span>

```powershell
PS> ,$data | Get-Member
TypeName: System.Object[]
...
```

### <a name="return-an-array"></a><span data-ttu-id="b9585-425">傳回陣列</span><span class="sxs-lookup"><span data-stu-id="b9585-425">Return an array</span></span>

<span data-ttu-id="b9585-426">當您從函式輸出或傳回值時，也會發生此陣列取消換行的情況。</span><span class="sxs-lookup"><span data-stu-id="b9585-426">This unwrapping of arrays also happens when you output or return values from a function.</span></span> <span data-ttu-id="b9585-427">如果您將輸出指派給變數，但這通常不是問題，您仍然可以取得陣列。</span><span class="sxs-lookup"><span data-stu-id="b9585-427">You can still get an array if you assign the output to a variable so this isn't commonly an issue.</span></span>

<span data-ttu-id="b9585-428">Catch 是您有新的陣列。</span><span class="sxs-lookup"><span data-stu-id="b9585-428">The catch is that you have a new array.</span></span> <span data-ttu-id="b9585-429">如果這樣造成困擾，您可以使用 `Write-Output -NoEnumerate $array` 或 `return ,$array` 來解決問題。</span><span class="sxs-lookup"><span data-stu-id="b9585-429">If that is ever a problem, you can use `Write-Output -NoEnumerate $array` or `return ,$array` to work around it.</span></span>

## <a name="anything-else"></a><span data-ttu-id="b9585-430">還想知道什麼嗎？</span><span class="sxs-lookup"><span data-stu-id="b9585-430">Anything else?</span></span>

<span data-ttu-id="b9585-431">我知道這裡有很多內容需要吸收消化。</span><span class="sxs-lookup"><span data-stu-id="b9585-431">I know this is all a lot to take in.</span></span> <span data-ttu-id="b9585-432">我希望您每次閱讀本文時，都學到一些東西，而且本文將會是您未來漫長歲月中的絕佳參考資料。</span><span class="sxs-lookup"><span data-stu-id="b9585-432">My hope is that you learn something from this article every time you read it and that it turns out to be a good reference for you for a long time to come.</span></span> <span data-ttu-id="b9585-433">若您認為本文內容實用，請與您認為可能會從中獲得價值的其他人分享。</span><span class="sxs-lookup"><span data-stu-id="b9585-433">If you found this to be helpful, please share it with others you think may get value out of it.</span></span>

<span data-ttu-id="b9585-434">從這裡開始，我會建議您查看我所寫的關於[雜湊表][]的類似文章。</span><span class="sxs-lookup"><span data-stu-id="b9585-434">From here, I would recommend you check out a similar post that I wrote about [hashtables][].</span></span>

<!-- link references -->
[原始版本]: https://powershellexplained.com/2018-10-15-Powershell-arrays-Everything-you-wanted-to-know/
[original version]: https://powershellexplained.com/2018-10-15-Powershell-arrays-Everything-you-wanted-to-know/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[陣列]: /powershell/module/microsoft.powershell.core/about/about_arrays
[Arrays]: /powershell/module/microsoft.powershell.core/about/about_arrays
[switch 陳述式]: everything-about-switch.md
[switch statement]: everything-about-switch.md
[雜湊表]: everything-about-hashtable.md
[hashtables]: everything-about-hashtable.md
[使用 RegEx 的許多方式]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/
[The many ways to use regex]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/
[如何驗證陣列中的每個值是否符合指定的值]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition
[how to verify that every value in an array matches a given value]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition
[解決方案]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition/e7iizca
[solution]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition/e7iizca
[StringBuilder]: https://powershellexplained.com/2017-11-20-Powershell-StringBuilder/
