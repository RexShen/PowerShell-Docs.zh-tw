---
title: 您想知道有關雜湊表的一切
description: 雜湊表在 PowerShell 中是極其重要的，因此務必加以充分了解。
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 1539cf6444cab718c1108384c640193d66c85daf
ms.sourcegitcommit: 0c31814bed14ff715dc7d4aace07cbdc6df2438e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2020
ms.locfileid: "93354417"
---
# <a name="everything-you-wanted-to-know-about-hashtables"></a><span data-ttu-id="04fca-103">您想知道有關雜湊表的一切</span><span class="sxs-lookup"><span data-stu-id="04fca-103">Everything you wanted to know about hashtables</span></span>

<span data-ttu-id="04fca-104">我想要回頭討論[雜湊表][]。</span><span class="sxs-lookup"><span data-stu-id="04fca-104">I want to take a step back and talk about [hashtables][].</span></span> <span data-ttu-id="04fca-105">現在我隨時都會使用雜湊表。</span><span class="sxs-lookup"><span data-stu-id="04fca-105">I use them all the time now.</span></span> <span data-ttu-id="04fca-106">昨晚當使用者群組會議結束後，我正在教導某人有關雜湊表的資訊，我意識到自己和對方一樣對雜湊表感到困惑。</span><span class="sxs-lookup"><span data-stu-id="04fca-106">I was teaching someone about them after our user group meeting last night and I realized I had the same confusion about them as he had.</span></span> <span data-ttu-id="04fca-107">雜湊表在 PowerShell 中是極其重要的，因此務必加以充分了解。</span><span class="sxs-lookup"><span data-stu-id="04fca-107">Hashtables are really important in PowerShell so it's good to have a solid understanding of them.</span></span>

> [!NOTE]
> <span data-ttu-id="04fca-108">本文的[原始版本][]出現在 [@KevinMarquette][] 所撰寫的部落格中。</span><span class="sxs-lookup"><span data-stu-id="04fca-108">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="04fca-109">PowerShell 小組感謝 Kevin 與我們分享此內容。</span><span class="sxs-lookup"><span data-stu-id="04fca-109">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="04fca-110">請在 [PowerShellExplained.com][] 查看他的部落格。</span><span class="sxs-lookup"><span data-stu-id="04fca-110">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="hashtable-as-a-collection-of-things"></a><span data-ttu-id="04fca-111">雜湊表即事件集合</span><span class="sxs-lookup"><span data-stu-id="04fca-111">Hashtable as a collection of things</span></span>

<span data-ttu-id="04fca-112">我想要您先將 **雜湊表** 看成雜湊表傳統定義中的集合。</span><span class="sxs-lookup"><span data-stu-id="04fca-112">I want you to first see a **Hashtable** as a collection in the traditional definition of a hashtable.</span></span> <span data-ttu-id="04fca-113">此定義可讓您在稍後將其用於更進階的內容時，對其運作方式有基本的了解。</span><span class="sxs-lookup"><span data-stu-id="04fca-113">This definition gives you a fundamental understanding of how they work when they get used for more advanced stuff later.</span></span> <span data-ttu-id="04fca-114">略過這項了解通常是造成困惑的來源。</span><span class="sxs-lookup"><span data-stu-id="04fca-114">Skipping this understanding is often a source of confusion.</span></span>

## <a name="what-is-an-array"></a><span data-ttu-id="04fca-115">什麼是陣列？</span><span class="sxs-lookup"><span data-stu-id="04fca-115">What is an array?</span></span>

<span data-ttu-id="04fca-116">在跳到什麼是 **雜湊表** 之前，我必須先提到 [陣列][]。</span><span class="sxs-lookup"><span data-stu-id="04fca-116">Before I jump into what a **Hashtable** is, I need to mention [arrays][] first.</span></span> <span data-ttu-id="04fca-117">基於此討論的目的，陣列是值或物件的清單或集合。</span><span class="sxs-lookup"><span data-stu-id="04fca-117">For the purpose of this discussion, an array is a list or collection of values or objects.</span></span>

```powershell
$array = @(1,2,3,5,7,11)
```

<span data-ttu-id="04fca-118">一旦您將項目放入陣列後，就可以使用 `foreach` 來逐一查看清單，或使用索引來存取陣列中的個別元素。</span><span class="sxs-lookup"><span data-stu-id="04fca-118">Once you have your items into an array, you can either use `foreach` to iterate over the list or use an index to access individual elements in the array.</span></span>

```powershell
foreach($item in $array)
{
    Write-Output $item
}

Write-Output $array[3]
```

<span data-ttu-id="04fca-119">您也可以採用相同的方式，使用索引來更新值。</span><span class="sxs-lookup"><span data-stu-id="04fca-119">You can also update values using an index in the same way.</span></span>

```powershell
$array[2] = 13
```

<span data-ttu-id="04fca-120">我只是稍微示範一下陣列，但是當我移到雜湊表時，應該將其放至正確的內容中。</span><span class="sxs-lookup"><span data-stu-id="04fca-120">I just scratched the surface on arrays but that should put them into the right context as I move onto hashtables.</span></span>

## <a name="what-is-a-hashtable"></a><span data-ttu-id="04fca-121">什麼是雜湊表？</span><span class="sxs-lookup"><span data-stu-id="04fca-121">What is a hashtable?</span></span>

<span data-ttu-id="04fca-122">我將先從基本的技術層面說明雜湊表是什麼，然後再轉移到 PowerShell 使用雜湊表的其他方法。</span><span class="sxs-lookup"><span data-stu-id="04fca-122">I'm going to start with a basic technical description of what hashtables are, in the general sense, before I shift into the other ways PowerShell uses them.</span></span>

<span data-ttu-id="04fca-123">雜湊表是一種資料結構，與陣列非常相似，不同之處在於您會使用索引鍵來儲存每個值 (物件)。</span><span class="sxs-lookup"><span data-stu-id="04fca-123">A hashtable is a data structure, much like an array, except you store each value (object) using a key.</span></span> <span data-ttu-id="04fca-124">其是基本的索引鍵/值存放區。</span><span class="sxs-lookup"><span data-stu-id="04fca-124">It's a basic key/value store.</span></span> <span data-ttu-id="04fca-125">首先，我們會建立空的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="04fca-125">First, we create an empty hashtable.</span></span>

```powershell
$ageList = @{}
```

<span data-ttu-id="04fca-126">請注意，大括號 (而不是括號) 是用來定義雜湊表。</span><span class="sxs-lookup"><span data-stu-id="04fca-126">Notice that braces, instead of parentheses, are used to define a hashtable.</span></span> <span data-ttu-id="04fca-127">然後，我們會使用如下的索引鍵來新增項目：</span><span class="sxs-lookup"><span data-stu-id="04fca-127">Then we add an item using a key like this:</span></span>

```powershell
$key = 'Kevin'
$value = 36
$ageList.add( $key, $value )

$ageList.add( 'Alex', 9 )
```

<span data-ttu-id="04fca-128">人員的名稱是索引鍵，而其年齡是我想要儲存的值。</span><span class="sxs-lookup"><span data-stu-id="04fca-128">The person's name is the key and their age is the value that I want to save.</span></span>

## <a name="using-the-brackets-for-access"></a><span data-ttu-id="04fca-129">使用大括號進行存取</span><span class="sxs-lookup"><span data-stu-id="04fca-129">Using the brackets for access</span></span>

<span data-ttu-id="04fca-130">一旦將您的值新增至雜湊表後，就可以使用該相同的索引鍵 (而不是使用數字索引鍵，如您對陣列所做的一般) 將其取回。</span><span class="sxs-lookup"><span data-stu-id="04fca-130">Once you add your values to the hashtable, you can pull them back out using that same key (instead of using a numeric index like you would have for an array).</span></span>

```powershell
$ageList['Kevin']
$ageList['Alex']
```

<span data-ttu-id="04fca-131">當我想要 Kevin 的年齡時，可以使用他的名稱來進行存取。</span><span class="sxs-lookup"><span data-stu-id="04fca-131">When I want Kevin's age, I use his name to access it.</span></span> <span data-ttu-id="04fca-132">我們也可以使用這種方法，在雜湊表中新增或更新值。</span><span class="sxs-lookup"><span data-stu-id="04fca-132">We can use this approach to add or update values into the hashtable too.</span></span> <span data-ttu-id="04fca-133">這就像是使用上述的 `add()` 函式一樣。</span><span class="sxs-lookup"><span data-stu-id="04fca-133">This is just like using the `add()` function above.</span></span>

```powershell
$ageList = @{}

$key = 'Kevin'
$value = 36
$ageList[$key] = $value

$ageList['Alex'] = 9
```

<span data-ttu-id="04fca-134">還有另一種語法，您可以用來存取及更新我在稍後章節中會討論到的值。</span><span class="sxs-lookup"><span data-stu-id="04fca-134">There's another syntax you can use for accessing and updating values that I'll cover in a later section.</span></span> <span data-ttu-id="04fca-135">如果您是從另一種語言來到 PowerShell，這些範例應該符合您之前使用雜湊表的方式。</span><span class="sxs-lookup"><span data-stu-id="04fca-135">If you're coming to PowerShell from another language, these examples should fit in with how you may have used hashtables before.</span></span>

### <a name="creating-hashtables-with-values"></a><span data-ttu-id="04fca-136">使用一些值建立雜湊表</span><span class="sxs-lookup"><span data-stu-id="04fca-136">Creating hashtables with values</span></span>

<span data-ttu-id="04fca-137">到目前為止，我已經為這些範例建立了一個空的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="04fca-137">So far I've created an empty hashtable for these examples.</span></span> <span data-ttu-id="04fca-138">在建立索引鍵和值時，您可以預先將其填入。</span><span class="sxs-lookup"><span data-stu-id="04fca-138">You can pre-populate the keys and values when you create them.</span></span>

```powershell
$ageList = @{
    Kevin = 36
    Alex  = 9
}
```

### <a name="as-a-lookup-table"></a><span data-ttu-id="04fca-139">做為查閱資料表</span><span class="sxs-lookup"><span data-stu-id="04fca-139">As a lookup table</span></span>

<span data-ttu-id="04fca-140">此雜湊表類型的實際值是您可以使用其做為查閱資料表的值。</span><span class="sxs-lookup"><span data-stu-id="04fca-140">The real value of this type of a hashtable is that you can use them as a lookup table.</span></span> <span data-ttu-id="04fca-141">以下是一個簡單範例。</span><span class="sxs-lookup"><span data-stu-id="04fca-141">Here is a simple example.</span></span>

```powershell
$environments = @{
    Prod = 'SrvProd05'
    QA   = 'SrvQA02'
    Dev  = 'SrvDev12'
}

$server = $environments[$env]
```

<span data-ttu-id="04fca-142">在此範例中，您指定 `$env` 變數的環境，而且其會挑選正確的伺服器。</span><span class="sxs-lookup"><span data-stu-id="04fca-142">In this example, you specify an environment for the `$env` variable and it will pick the correct server.</span></span> <span data-ttu-id="04fca-143">您可以將 `switch($env){...}` 用於像這樣的選擇，但雜湊表是不錯的選項。</span><span class="sxs-lookup"><span data-stu-id="04fca-143">You could use a `switch($env){...}` for a selection like this but a hashtable is a nice option.</span></span>

<span data-ttu-id="04fca-144">當您以動態方式建置查閱資料表以供稍後使用時，這樣做的效果更好。</span><span class="sxs-lookup"><span data-stu-id="04fca-144">This gets even better when you dynamically build the lookup table to use it later.</span></span> <span data-ttu-id="04fca-145">因此，當您需要交叉參考時，請考慮使用這種方法。</span><span class="sxs-lookup"><span data-stu-id="04fca-145">So think about using this approach when you need to cross reference something.</span></span> <span data-ttu-id="04fca-146">我認為，如果 PowerShell 在管道上使用 `Where-Object` 進行篩選並不理想，我們將看到更多這種方法。</span><span class="sxs-lookup"><span data-stu-id="04fca-146">I think we would see this even more if PowerShell wasn't so good at filtering on the pipe with `Where-Object`.</span></span> <span data-ttu-id="04fca-147">若在效能至上的情況下，就必須考慮這種方法。</span><span class="sxs-lookup"><span data-stu-id="04fca-147">If you're ever in a situation where performance matters, this approach needs to be considered.</span></span>

<span data-ttu-id="04fca-148">我並未說其速度更快，但其符合[若效能至上，請將其進行測試][]的規則。</span><span class="sxs-lookup"><span data-stu-id="04fca-148">I won't say that it's faster, but it does fit into the rule of [If performance matters, test it][].</span></span>

#### <a name="multiselection"></a><span data-ttu-id="04fca-149">多重選擇</span><span class="sxs-lookup"><span data-stu-id="04fca-149">Multiselection</span></span>

<span data-ttu-id="04fca-150">一般來說，您會將雜湊表視為索引鍵/值組，其中您可以提供一個索引鍵並取得一個值。</span><span class="sxs-lookup"><span data-stu-id="04fca-150">Generally, you think of a hashtable as a key/value pair, where you provide one key and get one value.</span></span> <span data-ttu-id="04fca-151">PowerShell 可讓您提供索引鍵陣列，以取得多個值。</span><span class="sxs-lookup"><span data-stu-id="04fca-151">PowerShell allows you to provide an array of keys to get multiple values.</span></span>

```powershell
$environments[@('QA','DEV')]
$environments[('QA','DEV')]
$environments['QA','DEV']
```

<span data-ttu-id="04fca-152">在此範例中，我使用上述的相同查閱雜湊表，並提供三種不同的陣列樣式來取得相符項目。</span><span class="sxs-lookup"><span data-stu-id="04fca-152">In this example, I use the same lookup hashtable from above and provide three different array styles to get the matches.</span></span> <span data-ttu-id="04fca-153">這是 PowerShell 中大部分人都不知道的隱藏功能。</span><span class="sxs-lookup"><span data-stu-id="04fca-153">This is a hidden gem in PowerShell that most people aren't aware of.</span></span>

## <a name="iterating-hashtables"></a><span data-ttu-id="04fca-154">逐一查看雜湊表</span><span class="sxs-lookup"><span data-stu-id="04fca-154">Iterating hashtables</span></span>

<span data-ttu-id="04fca-155">因為雜湊表是索引鍵/值組的集合，所以您會以不同於陣列或一般項目清單所用的方式，逐一查看此雜湊表。</span><span class="sxs-lookup"><span data-stu-id="04fca-155">Because a hashtable is a collection of key/value pairs, you iterate over it differently than you do for an array or a normal list of items.</span></span>

<span data-ttu-id="04fca-156">首先要注意的是，如果您透過管道處理雜湊表，則管道會將其視為一個物件。</span><span class="sxs-lookup"><span data-stu-id="04fca-156">The first thing to notice is that if you pipe your hashtable, the pipe treats it like one object.</span></span>

```powershell
PS> $ageList | Measure-Object
count : 1
```

<span data-ttu-id="04fca-157">即使 `.count` 屬性會告訴您其包含多少個值，也一樣。</span><span class="sxs-lookup"><span data-stu-id="04fca-157">Even though the `.count` property tells you how many values it contains.</span></span>

```powershell
PS> $ageList.count
2
```

<span data-ttu-id="04fca-158">如果您只需要值，則可以使用 `.values` 屬性來解決此問題。</span><span class="sxs-lookup"><span data-stu-id="04fca-158">You get around this issue by using the `.values` property if all you need is just the values.</span></span>

```powershell
PS> $ageList.values | Measure-Object -Average
Count   : 2
Average : 22.5
```

<span data-ttu-id="04fca-159">列舉索引鍵並使用索引鍵來存取值通常更有用。</span><span class="sxs-lookup"><span data-stu-id="04fca-159">It's often more useful to enumerate the keys and use them to access the values.</span></span>

```powershell
PS> $ageList.keys | ForEach-Object{
    $message = '{0} is {1} years old!' -f $_, $ageList[$_]
    Write-Output $message
}
Kevin is 36 years old
Alex is 9 years old
```

<span data-ttu-id="04fca-160">以下是搭配 `foreach(){...}` 迴圈的相同範例。</span><span class="sxs-lookup"><span data-stu-id="04fca-160">Here is the same example with a `foreach(){...}` loop.</span></span>

```powershell
foreach($key in $ageList.keys)
{
    $message = '{0} is {1} years old' -f $key, $ageList[$key]
    Write-Output $message
}
```

<span data-ttu-id="04fca-161">我們正在瀏覽雜湊表中的每個索引鍵，然後使用其來存取值。</span><span class="sxs-lookup"><span data-stu-id="04fca-161">We are walking each key in the hashtable and then using it to access the value.</span></span> <span data-ttu-id="04fca-162">當您使用雜湊表做為集合時，這是常見的模式。</span><span class="sxs-lookup"><span data-stu-id="04fca-162">This is a common pattern when working with hashtables as a collection.</span></span>

### <a name="getenumerator"></a><span data-ttu-id="04fca-163">GetEnumerator()</span><span class="sxs-lookup"><span data-stu-id="04fca-163">GetEnumerator()</span></span>

<span data-ttu-id="04fca-164">這會將我們帶至 `GetEnumerator()` 以逐一查看我們的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="04fca-164">That brings us to `GetEnumerator()` for iterating over our hashtable.</span></span>

```powershell
$ageList.GetEnumerator() | ForEach-Object{
    $message = '{0} is {1} years old!' -f $_.key, $_.value
    Write-Output $message
}
```

<span data-ttu-id="04fca-165">列舉程式會逐一為您提供每個索引鍵/值組。</span><span class="sxs-lookup"><span data-stu-id="04fca-165">The enumerator gives you each key/value pair one after another.</span></span> <span data-ttu-id="04fca-166">其是專為此使用案例所設計的。</span><span class="sxs-lookup"><span data-stu-id="04fca-166">It was designed specifically for this use case.</span></span> <span data-ttu-id="04fca-167">感謝您光臨 [Mark Kraus](https://get-PowerShellblog.blogspot.com) 提醒我這個問題。</span><span class="sxs-lookup"><span data-stu-id="04fca-167">Thank you to [Mark Kraus](https://get-PowerShellblog.blogspot.com) for reminding me of this one.</span></span>

### <a name="badenumeration"></a><span data-ttu-id="04fca-168">BadEnumeration</span><span class="sxs-lookup"><span data-stu-id="04fca-168">BadEnumeration</span></span>

<span data-ttu-id="04fca-169">其中一個重要的細節是，您無法在列舉雜湊表時對其進行修改。</span><span class="sxs-lookup"><span data-stu-id="04fca-169">One important detail is that you can't modify a hashtable while it's being enumerated.</span></span> <span data-ttu-id="04fca-170">如果我們從基本 `$environments` 範例開始：</span><span class="sxs-lookup"><span data-stu-id="04fca-170">If we start with our basic `$environments` example:</span></span>

```powershell
$environments = @{
    Prod = 'SrvProd05'
    QA   = 'SrvQA02'
    Dev  = 'SrvDev12'
}
```

<span data-ttu-id="04fca-171">嘗試將每個索引鍵設定為相同的伺服器值則會失敗。</span><span class="sxs-lookup"><span data-stu-id="04fca-171">And trying to set every key to the same server value fails.</span></span>

```powershell
$environments.Keys | ForEach-Object {
    $environments[$_] = 'SrvDev03'
}

An error occurred while enumerating through a collection: Collection was modified; enumeration operation may not execute.
+ CategoryInfo          : InvalidOperation: tableEnumerator:HashtableEnumerator) [], RuntimeException
+ FullyQualifiedErrorId : BadEnumeration
```

<span data-ttu-id="04fca-172">即使看起來應該很好，也會失敗：</span><span class="sxs-lookup"><span data-stu-id="04fca-172">This will also fail even though it looks like it should also be fine:</span></span>

```powershell
foreach($key in $environments.keys) {
    $environments[$key] = 'SrvDev03'
}

Collection was modified; enumeration operation may not execute.
    + CategoryInfo          : OperationStopped: (:) [], InvalidOperationException
    + FullyQualifiedErrorId : System.InvalidOperationException
```

<span data-ttu-id="04fca-173">解決這種情況的訣竅是在執行列舉之前，先複製金鑰。</span><span class="sxs-lookup"><span data-stu-id="04fca-173">The trick to this situation is to clone the keys before doing the enumeration.</span></span>

```powershell
$environments.Keys.Clone() | ForEach-Object {
    $environments[$_] = 'SrvDev03'
}
```

## <a name="hashtable-as-a-collection-of-properties"></a><span data-ttu-id="04fca-174">雜湊表即屬性集合</span><span class="sxs-lookup"><span data-stu-id="04fca-174">Hashtable as a collection of properties</span></span>

<span data-ttu-id="04fca-175">到目前為止，我們放在雜湊表中的物件類型都是相同類型的物件。</span><span class="sxs-lookup"><span data-stu-id="04fca-175">So far the type of objects we placed in our hashtable were all the same type of object.</span></span> <span data-ttu-id="04fca-176">我已在所有這些範例中使用了年齡，而索引鍵是該人員的名稱。</span><span class="sxs-lookup"><span data-stu-id="04fca-176">I used ages in all those examples and the key was the person's name.</span></span> <span data-ttu-id="04fca-177">當您的物件集合各有一個名稱時，這是一種很好的查看方法。</span><span class="sxs-lookup"><span data-stu-id="04fca-177">This is a great way to look at it when your collection of objects each have a name.</span></span> <span data-ttu-id="04fca-178">在 PowerShell 中使用雜湊表的另一個常見方式是保留屬性的集合，其中索引鍵是屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="04fca-178">Another common way to use hashtables in PowerShell is to hold a collection of properties where the key is the name of the property.</span></span> <span data-ttu-id="04fca-179">在下一個範例中，我將逐步解說該概念。</span><span class="sxs-lookup"><span data-stu-id="04fca-179">I'll step into that idea in this next example.</span></span>

### <a name="property-based-access"></a><span data-ttu-id="04fca-180">屬性型存取</span><span class="sxs-lookup"><span data-stu-id="04fca-180">Property-based access</span></span>

<span data-ttu-id="04fca-181">使用屬性型存取可變更雜湊表的動態，以及在 PowerShell 中使用雜湊表的方式。</span><span class="sxs-lookup"><span data-stu-id="04fca-181">The use of property-based access changes the dynamics of hashtables and how you can use them in PowerShell.</span></span> <span data-ttu-id="04fca-182">以下是上述的一般範例，其會將索引鍵視為屬性。</span><span class="sxs-lookup"><span data-stu-id="04fca-182">Here is our usual example from above treating the keys as properties.</span></span>

```powershell
$ageList = @{}
$ageList.Kevin = 35
$ageList.Alex = 9
```

<span data-ttu-id="04fca-183">就像上述範例，此範例會新增這些索引鍵 (如果其尚未存在於雜湊表中)。</span><span class="sxs-lookup"><span data-stu-id="04fca-183">Just like the examples above, this example adds those keys if they don't exist in the hashtable already.</span></span> <span data-ttu-id="04fca-184">根據您定義金鑰的方式和您的值，這可能有點奇怪或完美符合。</span><span class="sxs-lookup"><span data-stu-id="04fca-184">Depending on how you defined your keys and what your values are, this is either a little strange or a perfect fit.</span></span> <span data-ttu-id="04fca-185">到目前為止，年齡清單範例一直非常有用。</span><span class="sxs-lookup"><span data-stu-id="04fca-185">The age list example has worked great up until this point.</span></span> <span data-ttu-id="04fca-186">我們需要新的範例，以方便您繼續進行。</span><span class="sxs-lookup"><span data-stu-id="04fca-186">We need a new example for this to feel right going forward.</span></span>

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}
```

<span data-ttu-id="04fca-187">此外，我們也可以在 `$person` 上新增和存取屬性，如下所示。</span><span class="sxs-lookup"><span data-stu-id="04fca-187">And we can add and access attributes on the `$person` like this.</span></span>

```powershell
$person.city = 'Austin'
$person.state = 'TX'
```

<span data-ttu-id="04fca-188">突然間，此雜湊表就像物件一樣地感覺和運作。</span><span class="sxs-lookup"><span data-stu-id="04fca-188">All of a sudden this hashtable starts to feel and act like an object.</span></span> <span data-ttu-id="04fca-189">雜湊表仍然是項目的集合，因此上述所有範例仍然適用。</span><span class="sxs-lookup"><span data-stu-id="04fca-189">It's still a collection of things, so all the examples above still apply.</span></span> <span data-ttu-id="04fca-190">我們只是從另一個觀點接近雜湊表。</span><span class="sxs-lookup"><span data-stu-id="04fca-190">We just approach it from a different point of view.</span></span>

### <a name="checking-for-keys-and-values"></a><span data-ttu-id="04fca-191">檢查索引鍵和值</span><span class="sxs-lookup"><span data-stu-id="04fca-191">Checking for keys and values</span></span>

<span data-ttu-id="04fca-192">在大部分的情況下，您可以只測試值，如下所示：</span><span class="sxs-lookup"><span data-stu-id="04fca-192">In most cases, you can just test for the value with something like this:</span></span>

```powershell
if( $person.age ){...}
```

<span data-ttu-id="04fca-193">這很簡單，但對我而言卻是許多錯誤 (bug) 的來源，因為我在邏輯中輕忽了一個重要的細節。</span><span class="sxs-lookup"><span data-stu-id="04fca-193">It's simple but has been the source of many bugs for me because I was overlooking one important detail in my logic.</span></span> <span data-ttu-id="04fca-194">我開始使用測試值來測試索引鍵是否存在。</span><span class="sxs-lookup"><span data-stu-id="04fca-194">I started to use it to test if a key was present.</span></span> <span data-ttu-id="04fca-195">當值為 `$false` 或零時，該陳述式會意外傳回 `$false`。</span><span class="sxs-lookup"><span data-stu-id="04fca-195">When the value was `$false` or zero, that statement would return `$false` unexpectedly.</span></span>

```powershell
if( $person.age -ne $null ){...}
```

<span data-ttu-id="04fca-196">這解決了零值的問題，但未解決 $null 與不存在索引鍵的問題。</span><span class="sxs-lookup"><span data-stu-id="04fca-196">This works around that issue for zero values but not $null vs non-existent keys.</span></span> <span data-ttu-id="04fca-197">在大部分的時間裡，您不需要進行這項區別，但有一些功能可在這時供您執行。</span><span class="sxs-lookup"><span data-stu-id="04fca-197">Most of the time you don't need to make that distinction but there are functions for when you do.</span></span>

```powershell
if( $person.ContainsKey('age') ){...}
```

<span data-ttu-id="04fca-198">如果您需要在不知道索引鍵或逐一查看整個集合的情況下測試值，我們也會有 `ContainsValue()` 因應此情況。</span><span class="sxs-lookup"><span data-stu-id="04fca-198">We also have a `ContainsValue()` for the situation where you need to test for a value without knowing the key or iterating the whole collection.</span></span>

### <a name="removing-and-clearing-keys"></a><span data-ttu-id="04fca-199">移除和清除索引鍵</span><span class="sxs-lookup"><span data-stu-id="04fca-199">Removing and clearing keys</span></span>

<span data-ttu-id="04fca-200">您可以使用 `.Remove()` 函式來移除索引鍵。</span><span class="sxs-lookup"><span data-stu-id="04fca-200">You can remove keys with the `.Remove()` function.</span></span>

```powershell
$person.remove('age')
```

<span data-ttu-id="04fca-201">為其指派 `$null` 值，只是讓您擁有一個具有 `$null` 值的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="04fca-201">Assigning them a `$null` value just leaves you with a key that has a `$null` value.</span></span>

<span data-ttu-id="04fca-202">清除雜湊表的常見方式就是將其初始化為空的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="04fca-202">A common way to clear a hashtable is to just initialize it to an empty hashtable.</span></span>

```powershell
$person = @{}
```

<span data-ttu-id="04fca-203">儘管可以如此運作，但請嘗試改用 `clear()` 函式。</span><span class="sxs-lookup"><span data-stu-id="04fca-203">While that does work, try to use the `clear()` function instead.</span></span>

```powershell
$person.clear()
```

<span data-ttu-id="04fca-204">這是使用函式建立自我記錄程式碼的其中一個執行個體，而且其會讓程式碼的意圖非常簡潔。</span><span class="sxs-lookup"><span data-stu-id="04fca-204">This is one of those instances where using the function creates self-documenting code and it makes the intentions of the code very clean.</span></span>

## <a name="all-the-fun-stuff"></a><span data-ttu-id="04fca-205">所有有趣的事物</span><span class="sxs-lookup"><span data-stu-id="04fca-205">All the fun stuff</span></span>

### <a name="ordered-hashtables"></a><span data-ttu-id="04fca-206">排序的雜湊表</span><span class="sxs-lookup"><span data-stu-id="04fca-206">Ordered hashtables</span></span>

<span data-ttu-id="04fca-207">根據預設，雜湊表不會排序 (或已排序)。</span><span class="sxs-lookup"><span data-stu-id="04fca-207">By default, hashtables aren't ordered (or sorted).</span></span> <span data-ttu-id="04fca-208">在傳統內容中，一律使用索引鍵存取值時，順序並不重要。</span><span class="sxs-lookup"><span data-stu-id="04fca-208">In the traditional context, the order doesn't matter when you always use a key to access values.</span></span> <span data-ttu-id="04fca-209">建議您讓屬性保持您所定義的順序。</span><span class="sxs-lookup"><span data-stu-id="04fca-209">You may find that you want the properties to stay in the order that you define them.</span></span> <span data-ttu-id="04fca-210">幸好，有一種方法可以使用 `ordered` 關鍵字來執行此動作。</span><span class="sxs-lookup"><span data-stu-id="04fca-210">Thankfully, there's a way to do that with the `ordered` keyword.</span></span>

```powershell
$person = [ordered]@{
    name = 'Kevin'
    age  = 36
}
```

<span data-ttu-id="04fca-211">現在，當您列舉索引鍵和值時，其會保持該順序。</span><span class="sxs-lookup"><span data-stu-id="04fca-211">Now when you enumerate the keys and values, they stay in that order.</span></span>

### <a name="inline-hashtables"></a><span data-ttu-id="04fca-212">內嵌雜湊表</span><span class="sxs-lookup"><span data-stu-id="04fca-212">Inline hashtables</span></span>

<span data-ttu-id="04fca-213">在一行上定義雜湊表時，可以用分號區隔索引鍵/值組。</span><span class="sxs-lookup"><span data-stu-id="04fca-213">When you're defining a hashtable on one line, you can separate the key/value pairs with a semicolon.</span></span>

```powershell
$person = @{ name = 'kevin'; age = 36; }
```

<span data-ttu-id="04fca-214">如果您是在管道上建立它們，這會非常方便。</span><span class="sxs-lookup"><span data-stu-id="04fca-214">This will come in handy if you're creating them on the pipe.</span></span>

### <a name="custom-expressions-in-common-pipeline-commands"></a><span data-ttu-id="04fca-215">一般管道命令中的自訂運算式</span><span class="sxs-lookup"><span data-stu-id="04fca-215">Custom expressions in common pipeline commands</span></span>

<span data-ttu-id="04fca-216">有幾個 Cmdlet 可支援使用雜湊表來建立自訂或計算屬性。</span><span class="sxs-lookup"><span data-stu-id="04fca-216">There are a few cmdlets that support the use of hashtables to create custom or calculated properties.</span></span> <span data-ttu-id="04fca-217">您通常會看到此屬性搭配 `Select-Object` 和 `Format-Table`。</span><span class="sxs-lookup"><span data-stu-id="04fca-217">You commonly see this with `Select-Object` and `Format-Table`.</span></span> <span data-ttu-id="04fca-218">雜湊表具有特殊語法，在完全展開時看起來就像這樣。</span><span class="sxs-lookup"><span data-stu-id="04fca-218">The hashtables have a special syntax that looks like this when fully expanded.</span></span>

```powershell
$property = @{
    name = 'totalSpaceGB'
    expression = { ($_.used + $_.free) / 1GB }
}
```

<span data-ttu-id="04fca-219">`name` 就是讓 Cmdlet 標示該資料行。</span><span class="sxs-lookup"><span data-stu-id="04fca-219">The `name` is what the cmdlet would label that column.</span></span> <span data-ttu-id="04fca-220">`expression` 是執行的指令碼區塊，其中 `$_` 是管道上物件的值。</span><span class="sxs-lookup"><span data-stu-id="04fca-220">The `expression` is a script block that is executed where `$_` is the value of the object on the pipe.</span></span> <span data-ttu-id="04fca-221">以下是該指令碼的運作方式：</span><span class="sxs-lookup"><span data-stu-id="04fca-221">Here is that script in action:</span></span>

```powershell
$drives = Get-PSDrive | Where Used
$drives | Select-Object -Properties name, $property

Name     totalSpaceGB
----     ------------
C    238.472652435303
```

<span data-ttu-id="04fca-222">我已將其放在變數中，但其可以輕鬆地以內嵌方式定義，而且您可以將 `name` 縮短為 `n`，以及將 `expression` 縮短為 `e` (當您位於其中時)。</span><span class="sxs-lookup"><span data-stu-id="04fca-222">I placed that in a variable but it could easily be defined inline and you can shorten `name` to `n` and `expression` to `e` while you're at it.</span></span>

```powershell
$drives | Select-Object -properties name, @{n='totalSpaceGB';e={($_.used + $_.free) / 1GB}}
```

<span data-ttu-id="04fca-223">我個人不喜歡製作長命令，而且其通常會促成一些我不想陷入的不良行為。</span><span class="sxs-lookup"><span data-stu-id="04fca-223">I personally don't like how long that makes commands and it often promotes some bad behaviors that I won't get into.</span></span> <span data-ttu-id="04fca-224">我更願意建立新的雜湊表或 `pscustomobject`，其中包含我想要的所有欄位和屬性，而不是在指令碼中使用這個方法。</span><span class="sxs-lookup"><span data-stu-id="04fca-224">I'm more likely to create a new hashtable or `pscustomobject` with all the fields and properties that I want instead of using this approach in scripts.</span></span> <span data-ttu-id="04fca-225">但有很多程式碼會這麼做，因此我希望您注意此情況。</span><span class="sxs-lookup"><span data-stu-id="04fca-225">But there's a lot of code out there that does this so I wanted you to be aware of it.</span></span> <span data-ttu-id="04fca-226">我稍後會談論如何建立 `pscustomobject`。</span><span class="sxs-lookup"><span data-stu-id="04fca-226">I talk about creating a `pscustomobject` later on.</span></span>

### <a name="custom-sort-expression"></a><span data-ttu-id="04fca-227">自訂排序運算式</span><span class="sxs-lookup"><span data-stu-id="04fca-227">Custom sort expression</span></span>

<span data-ttu-id="04fca-228">如果物件具有您想要依其排序的資料，就可以輕鬆排序集合。</span><span class="sxs-lookup"><span data-stu-id="04fca-228">It's easy to sort a collection if the objects have the data that you want to sort on.</span></span> <span data-ttu-id="04fca-229">您可以先將資料新增至物件，然後再排序，或針對 `Sort-Object` 建立自訂運算式。</span><span class="sxs-lookup"><span data-stu-id="04fca-229">You can either add the data to the object before you sort it or create a custom expression for `Sort-Object`.</span></span>

```powershell
Get-ADUser | Sort-Object -Parameter @{ e={ Get-TotalSales $_.Name } }
```

<span data-ttu-id="04fca-230">在此範例中，我會取得使用者清單，並使用一些自訂 Cmdlet 來取得只針對排序的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="04fca-230">In this example I'm taking a list of users and using some custom cmdlet to get additional information just for the sort.</span></span>

#### <a name="sort-a-list-of-hashtables"></a><span data-ttu-id="04fca-231">排序雜湊表清單</span><span class="sxs-lookup"><span data-stu-id="04fca-231">Sort a list of Hashtables</span></span>

<span data-ttu-id="04fca-232">如果您有想要排序的雜湊表清單，則會發現 `Sort-Object` 不會將您的索引鍵視為屬性。</span><span class="sxs-lookup"><span data-stu-id="04fca-232">If you have a list of hashtables that you want to sort, you'll find that the `Sort-Object` doesn't treat your keys as properties.</span></span> <span data-ttu-id="04fca-233">我們可以使用自訂排序運算式進行一回。</span><span class="sxs-lookup"><span data-stu-id="04fca-233">We can get a round that by using a custom sort expression.</span></span>

```powershell
$data = @(
    @{name='a'}
    @{name='c'}
    @{name='e'}
    @{name='f'}
    @{name='d'}
    @{name='b'}
)

$data | Sort-Object -Property @{e={$_.name}}
```

## <a name="splatting-hashtables-at-cmdlets"></a><span data-ttu-id="04fca-234">在 Cmdlet 展開雜湊表</span><span class="sxs-lookup"><span data-stu-id="04fca-234">Splatting hashtables at cmdlets</span></span>

<span data-ttu-id="04fca-235">這是有關雜湊表其中一件我最愛的事，許多人早期並未發現。</span><span class="sxs-lookup"><span data-stu-id="04fca-235">This is one of my favorite things about hashtables that many people don't discover early on.</span></span>
<span data-ttu-id="04fca-236">其概念為不是在一行上將所有屬性提供給 Cmdlet，而是先將其封裝成雜湊表。</span><span class="sxs-lookup"><span data-stu-id="04fca-236">The idea is that instead of providing all the properties to a cmdlet on one line, you can instead pack them into a hashtable first.</span></span> <span data-ttu-id="04fca-237">接著，您可以使用特殊方式將雜湊表提供給函式。</span><span class="sxs-lookup"><span data-stu-id="04fca-237">Then you can give the hashtable to the function in a special way.</span></span>
<span data-ttu-id="04fca-238">以下是以一般方式建立 DHCP 範圍的範例。</span><span class="sxs-lookup"><span data-stu-id="04fca-238">Here is an example of creating a DHCP scope the normal way.</span></span>

```powershell
Add-DhcpServerv4Scope -Name 'TestNetwork' -StartRange'10.0.0.2' -EndRange '10.0.0.254' -SubnetMask '255.255.255.0' -Description 'Network for testlab A' -LeaseDuration (New-TimeSpan -Days 8) -Type "Both"
```

<span data-ttu-id="04fca-239">不使用[展開][]，所有這些項目都必須定義在同一行上。</span><span class="sxs-lookup"><span data-stu-id="04fca-239">Without using [splatting][], all those things need to be defined on a single line.</span></span> <span data-ttu-id="04fca-240">其會滾出畫面或換行，視其表現而定。</span><span class="sxs-lookup"><span data-stu-id="04fca-240">It either scrolls off the screen or will wrap where ever it feels like.</span></span> <span data-ttu-id="04fca-241">現在請將其與使用展開的命令進行比較。</span><span class="sxs-lookup"><span data-stu-id="04fca-241">Now compare that to a command that uses splatting.</span></span>

```powershell
$DHCPScope = @{
    Name        = 'TestNetwork'
    StartRange  = '10.0.0.2'
    EndRange    = '10.0.0.254'
    SubnetMask  = '255.255.255.0'
    Description = 'Network for testlab A'
    LeaseDuration = (New-TimeSpan -Days 8)
    Type = "Both"
}
Add-DhcpServerv4Scope @DHCPScope
```

<span data-ttu-id="04fca-242">使用 `@` 符號，而不是 `$` 時，會叫用展開作業。</span><span class="sxs-lookup"><span data-stu-id="04fca-242">The use of the `@` sign instead of the `$` is what invokes the splat operation.</span></span>

<span data-ttu-id="04fca-243">只需片刻就會理解閱讀該範例有多容易。</span><span class="sxs-lookup"><span data-stu-id="04fca-243">Just take a moment to appreciate how easy that example is to read.</span></span> <span data-ttu-id="04fca-244">這是完全相同的命令，具有所有相同的值。</span><span class="sxs-lookup"><span data-stu-id="04fca-244">They are the exact same command with all the same values.</span></span> <span data-ttu-id="04fca-245">第二個更容易了解和繼續進行。</span><span class="sxs-lookup"><span data-stu-id="04fca-245">The second one is easier to understand and maintain going forward.</span></span>

<span data-ttu-id="04fca-246">每當命令太長時，我就會使用展開。</span><span class="sxs-lookup"><span data-stu-id="04fca-246">I use splatting anytime the command gets too long.</span></span> <span data-ttu-id="04fca-247">我定義了太長的命令，導致我的視窗向右滾動。</span><span class="sxs-lookup"><span data-stu-id="04fca-247">I define too long as causing my window to scroll right.</span></span> <span data-ttu-id="04fca-248">如果我點擊函式的三個屬性，很可能會使用展開的雜湊表來重寫該函式。</span><span class="sxs-lookup"><span data-stu-id="04fca-248">If I hit three properties for a function, odds are that I'll rewrite it using a splatted hashtable.</span></span>

### <a name="splatting-for-optional-parameters"></a><span data-ttu-id="04fca-249">針對選擇性參數進行展開</span><span class="sxs-lookup"><span data-stu-id="04fca-249">Splatting for optional parameters</span></span>

<span data-ttu-id="04fca-250">我使用展開的其中一種最常見方式，就是處理來自我指令碼中其他位置的選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="04fca-250">One of the most common ways I use splatting is to deal with optional parameters that come from some place else in my script.</span></span> <span data-ttu-id="04fca-251">假設我有一個函式，包裝了 `Get-CIMInstance` 呼叫，其中具有選擇性 `$Credential` 引數。</span><span class="sxs-lookup"><span data-stu-id="04fca-251">Let's say I have a function that wraps a `Get-CIMInstance` call that has an optional `$Credential` argument.</span></span>

```powershell
$CIMParams = @{
    ClassName = 'Win32_Bios'
    ComputerName = $ComputerName
}

if($Credential)
{
    $CIMParams.Credential = $Credential
}

Get-CIMInstance @CIMParams
```

<span data-ttu-id="04fca-252">首先使用常見的參數建立我的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="04fca-252">I start by creating my hashtable with common parameters.</span></span> <span data-ttu-id="04fca-253">接著新增 `$Credential`，如果存在的話。</span><span class="sxs-lookup"><span data-stu-id="04fca-253">Then I add the `$Credential` if it exists.</span></span>
<span data-ttu-id="04fca-254">因為我在這裡使用展開，所以我只需要在程式碼中呼叫 `Get-CIMInstance` 一次。</span><span class="sxs-lookup"><span data-stu-id="04fca-254">Because I'm using splatting here, I only need to have the call to `Get-CIMInstance` in my code once.</span></span> <span data-ttu-id="04fca-255">這種設計模式非常簡潔，而且可以輕鬆地處理許多選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="04fca-255">This design pattern is very clean and can handle lots of optional parameters easily.</span></span>

<span data-ttu-id="04fca-256">為求公平，您可以撰寫命令，以允許參數的 `$null` 值。</span><span class="sxs-lookup"><span data-stu-id="04fca-256">To be fair, you could write your commands to allow `$null` values for parameters.</span></span> <span data-ttu-id="04fca-257">只是您不一定能控制您所呼叫的其他命令。</span><span class="sxs-lookup"><span data-stu-id="04fca-257">You just don't always have control over the other commands you're calling.</span></span>

### <a name="multiple-splats"></a><span data-ttu-id="04fca-258">多個展開</span><span class="sxs-lookup"><span data-stu-id="04fca-258">Multiple splats</span></span>

<span data-ttu-id="04fca-259">您可以將多個雜湊表展開至相同的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="04fca-259">You can splat multiple hashtables to the same cmdlet.</span></span> <span data-ttu-id="04fca-260">如果我們回顧原始展開範例：</span><span class="sxs-lookup"><span data-stu-id="04fca-260">If we revisit our original splatting example:</span></span>

```powershell
$Common = @{
    SubnetMask  = '255.255.255.0'
    LeaseDuration = (New-TimeSpan -Days 8)
    Type = "Both"
}

$DHCPScope = @{
    Name        = 'TestNetwork'
    StartRange  = '10.0.0.2'
    EndRange    = '10.0.0.254'
    Description = 'Network for testlab A'
}

Add-DhcpServerv4Scope @DHCPScope @Common
```

<span data-ttu-id="04fca-261">當我有一組常用的參數傳遞至許多命令時，我會使用這種方法。</span><span class="sxs-lookup"><span data-stu-id="04fca-261">I'll use this method when I have a common set of parameters that I'm passing to lots of commands.</span></span>

### <a name="splatting-for-clean-code"></a><span data-ttu-id="04fca-262">針對全新程式碼進行展開</span><span class="sxs-lookup"><span data-stu-id="04fca-262">Splatting for clean code</span></span>

<span data-ttu-id="04fca-263">如果讓您的程式碼更簡潔，展開單一參數就不會有任何問題。</span><span class="sxs-lookup"><span data-stu-id="04fca-263">There's nothing wrong with splatting a single parameter if makes you code cleaner.</span></span>

```powershell
$log = @{Path = '.\logfile.log'}
Add-Content "logging this command" @log
```

### <a name="splatting-executables"></a><span data-ttu-id="04fca-264">展開可執行檔</span><span class="sxs-lookup"><span data-stu-id="04fca-264">Splatting executables</span></span>

<span data-ttu-id="04fca-265">展開也可以在使用 `/param:value` 語法的一些可執行檔上運作。</span><span class="sxs-lookup"><span data-stu-id="04fca-265">Splatting also works on some executables that use a `/param:value` syntax.</span></span> <span data-ttu-id="04fca-266">例如，`Robocopy.exe` 具有一些如下的參數。</span><span class="sxs-lookup"><span data-stu-id="04fca-266">`Robocopy.exe`, for example, has some parameters like this.</span></span>

```powershell
$robo = @{R=1;W=1;MT=8}
robocopy source destination @robo
```

<span data-ttu-id="04fca-267">我不知道這一切是否有用，但是我發現其很有趣。</span><span class="sxs-lookup"><span data-stu-id="04fca-267">I don't know that this is all that useful, but I found it interesting.</span></span>

## <a name="adding-hashtables"></a><span data-ttu-id="04fca-268">新增雜湊表</span><span class="sxs-lookup"><span data-stu-id="04fca-268">Adding hashtables</span></span>

<span data-ttu-id="04fca-269">雜湊表支援新增運算子以結合兩個雜湊表。</span><span class="sxs-lookup"><span data-stu-id="04fca-269">Hashtables support the addition operator to combine two hashtables.</span></span>

```powershell
$person += @{Zip = '78701'}
```

<span data-ttu-id="04fca-270">這只適用於兩個雜湊表不共用索引鍵的情況。</span><span class="sxs-lookup"><span data-stu-id="04fca-270">This only works if the two hashtables don't share a key.</span></span>

## <a name="nested-hashtables"></a><span data-ttu-id="04fca-271">巢狀雜湊表</span><span class="sxs-lookup"><span data-stu-id="04fca-271">Nested hashtables</span></span>

<span data-ttu-id="04fca-272">我們可以使用雜湊表做為雜湊表內的值。</span><span class="sxs-lookup"><span data-stu-id="04fca-272">We can use hashtables as values inside a hashtable.</span></span>

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}
$person.location = @{}
$person.location.city = 'Austin'
$person.location.state = 'TX'
```

<span data-ttu-id="04fca-273">我一開始使用包含兩個索引鍵的基本雜湊表。</span><span class="sxs-lookup"><span data-stu-id="04fca-273">I started with a basic hashtable containing two keys.</span></span> <span data-ttu-id="04fca-274">已新增名為 `location` 的索引鍵搭配空的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="04fca-274">I added a key called `location` with an empty hashtable.</span></span> <span data-ttu-id="04fca-275">然後，將最後兩個項目新增至該 `location` 雜湊表。</span><span class="sxs-lookup"><span data-stu-id="04fca-275">Then I added the last two items to that `location` hashtable.</span></span> <span data-ttu-id="04fca-276">我們也可以全都以內嵌方式執行此動作。</span><span class="sxs-lookup"><span data-stu-id="04fca-276">We can do this all inline too.</span></span>

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
    location = @{
        city  = 'Austin'
        state = 'TX'
    }
}
```

<span data-ttu-id="04fca-277">這會建立我們在上面看到的同一個雜湊表，並且可以使用相同的方式來存取屬性。</span><span class="sxs-lookup"><span data-stu-id="04fca-277">This creates the same hashtable that we saw above and can access the properties the same way.</span></span>

```powershell
$person.location.city
Austin
```

<span data-ttu-id="04fca-278">有許多方式可以處理您物件的結構。</span><span class="sxs-lookup"><span data-stu-id="04fca-278">There are many ways to approach the structure of your objects.</span></span> <span data-ttu-id="04fca-279">這裡是查看巢狀雜湊表的第二種方式。</span><span class="sxs-lookup"><span data-stu-id="04fca-279">Here is a second way to look at a nested hashtable.</span></span>

```powershell
$people = @{
    Kevin = @{
        age  = 36
        city = 'Austin'
    }
    Alex = @{
        age  = 9
        city = 'Austin'
    }
}
```

<span data-ttu-id="04fca-280">這會混合使用雜湊表做為物件集合和屬性集合的概念。</span><span class="sxs-lookup"><span data-stu-id="04fca-280">This mixes the concept of using hashtables as a collection of objects and a collection of properties.</span></span> <span data-ttu-id="04fca-281">即使用了您偏好的任何方法使這些值形成巢狀，仍然很容易加以存取。</span><span class="sxs-lookup"><span data-stu-id="04fca-281">The values are still easy to access even when they're nested using whatever approach you prefer.</span></span>

```powershell
PS> $people.kevin.age
36
PS> $people.kevin['city']
Austin
PS> $people['Alex'].age
9
PS> $people['Alex']['City']
Austin
```

<span data-ttu-id="04fca-282">我通常會在將其視為屬性時使用點屬性。</span><span class="sxs-lookup"><span data-stu-id="04fca-282">I tend to use the dot property when I'm treating it like a property.</span></span> <span data-ttu-id="04fca-283">這些一般都是我在程式碼中以靜態方式定義的項目，而且我非常了解這些項目。</span><span class="sxs-lookup"><span data-stu-id="04fca-283">Those are generally things I've defined statically in my code and I know them off the top of my head.</span></span> <span data-ttu-id="04fca-284">如果我需要逐步執行清單或以程式設計方式存取索引鍵，則會使用括弧來提供索引鍵名稱。</span><span class="sxs-lookup"><span data-stu-id="04fca-284">If I need to walk the list or programmatically access the keys, I use the brackets to provide the key name.</span></span>

```powershell
foreach($name in $people.keys)
{
    $person = $people[$name]
    '{0}, age {1}, is in {2}' -f $name, $person.age, $person.city
}
```

<span data-ttu-id="04fca-285">能夠讓雜湊表形成巢狀，可提供您許多彈性和選項。</span><span class="sxs-lookup"><span data-stu-id="04fca-285">Having the ability to nest hashtables gives you a lot of flexibility and options.</span></span>

### <a name="looking-at-nested-hashtables"></a><span data-ttu-id="04fca-286">查看巢狀雜湊表</span><span class="sxs-lookup"><span data-stu-id="04fca-286">Looking at nested hashtables</span></span>

<span data-ttu-id="04fca-287">一旦您開始讓雜湊表形成巢狀，就需要一個簡易的方法，從主控台進行查看。</span><span class="sxs-lookup"><span data-stu-id="04fca-287">As soon as you start nesting hashtables, you're going to need an easy way to look at them from the console.</span></span> <span data-ttu-id="04fca-288">如果我採用最後一個雜湊表，就會得到如下所示的輸出，而且其只會如此的深：</span><span class="sxs-lookup"><span data-stu-id="04fca-288">If I take that last hashtable, I get an output that looks like this and it only goes so deep:</span></span>

```powershell
PS> $people
Name                           Value
----                           -----
Kevin                          {age, city}
Alex                           {age, city}
```

<span data-ttu-id="04fca-289">我用於查看這些項目的移至命令是 `ConvertTo-JSON`，因為其非常簡潔，而且我經常在其他項目上使用 JSON。</span><span class="sxs-lookup"><span data-stu-id="04fca-289">My go to command for looking at these things is `ConvertTo-JSON` because it's very clean and I frequently use JSON on other things.</span></span>

```powershell
PS> $people | ConvertTo-Json
{
    "Kevin":  {
                "age":  36,
                "city":  "Austin"
            },
    "Alex":  {
                "age":  9,
                "city":  "Austin"
            }
}
```

<span data-ttu-id="04fca-290">即使您不知道 JSON，還是應該能夠看到您要尋找的內容。</span><span class="sxs-lookup"><span data-stu-id="04fca-290">Even if you don't know JSON, you should be able to see what you're looking for.</span></span> <span data-ttu-id="04fca-291">這類結構化資料有一個 `Format-Custom` 命令，但我仍然更喜歡使用 JSON 檢視。</span><span class="sxs-lookup"><span data-stu-id="04fca-291">There's a `Format-Custom` command for structured data like this but I still like the JSON view better.</span></span>

## <a name="creating-objects"></a><span data-ttu-id="04fca-292">建立物件</span><span class="sxs-lookup"><span data-stu-id="04fca-292">Creating objects</span></span>

<span data-ttu-id="04fca-293">有時候，您只需要擁有物件，而且使用雜湊表來保留屬性，並不只是讓工作完成而已。</span><span class="sxs-lookup"><span data-stu-id="04fca-293">Sometimes you just need to have an object and using a hashtable to hold properties just isn't getting the job done.</span></span> <span data-ttu-id="04fca-294">最常見的情況是，您想要將索引鍵視為資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="04fca-294">Most commonly you want to see the keys as column names.</span></span> <span data-ttu-id="04fca-295">`pscustomobject` 讓這件事變得很簡單。</span><span class="sxs-lookup"><span data-stu-id="04fca-295">A `pscustomobject` makes that easy.</span></span>

```powershell
$person = [pscustomobject]@{
    name = 'Kevin'
    age  = 36
}

$person

name  age
----  ---
Kevin  36
```

<span data-ttu-id="04fca-296">即使您一開始並未將其建立為 `pscustomobject`，稍後也可以視需要將其轉換。</span><span class="sxs-lookup"><span data-stu-id="04fca-296">Even if you don't create it as a `pscustomobject` initially, you can always cast it later when needed.</span></span>

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}

[pscustomobject]$person

name  age
----  ---
Kevin  36
```

<span data-ttu-id="04fca-297">我已經為了 [pscustomobject][] 撰寫詳細的文章，您應該在此之後閱讀。</span><span class="sxs-lookup"><span data-stu-id="04fca-297">I already have detailed write-up for [pscustomobject][] that you should go read after this one.</span></span> <span data-ttu-id="04fca-298">其係根據這裡所學到的許多東西建置的。</span><span class="sxs-lookup"><span data-stu-id="04fca-298">It builds on a lot of the things learned here.</span></span>

## <a name="reading-and-writing-hashtables-to-file"></a><span data-ttu-id="04fca-299">讀取和寫入雜湊表至檔案</span><span class="sxs-lookup"><span data-stu-id="04fca-299">Reading and writing hashtables to file</span></span>

### <a name="saving-to-csv"></a><span data-ttu-id="04fca-300">儲存至 CSV</span><span class="sxs-lookup"><span data-stu-id="04fca-300">Saving to CSV</span></span>

<span data-ttu-id="04fca-301">努力將雜湊表儲存至 CSV，是我在上面提到的其中一個困難之處。</span><span class="sxs-lookup"><span data-stu-id="04fca-301">Struggling with getting a hashtable to save to a CSV is one of the difficulties that I was referring to above.</span></span> <span data-ttu-id="04fca-302">將您的雜湊表轉換成 `pscustomobject`，然後其就會正確地儲存至 CSV。</span><span class="sxs-lookup"><span data-stu-id="04fca-302">Convert your hashtable to a `pscustomobject` and it will save correctly to CSV.</span></span> <span data-ttu-id="04fca-303">如果您從 `pscustomobject` 開始，很有幫助，因為資料行順序會保留下來。</span><span class="sxs-lookup"><span data-stu-id="04fca-303">It helps if you start with a `pscustomobject` so the column order is preserved.</span></span> <span data-ttu-id="04fca-304">但您可以視需要將其轉換成 `pscustomobject` 內嵌。</span><span class="sxs-lookup"><span data-stu-id="04fca-304">But you can cast it to a `pscustomobject` inline if needed.</span></span>

```powershell
$person | ForEach-Object{ [pscustomobject]$_ } | Export-CSV -Path $path
```

<span data-ttu-id="04fca-305">可以再次參閱我針對如何使用 [pscustomobject][] 撰寫的文章。</span><span class="sxs-lookup"><span data-stu-id="04fca-305">Again, check out my write-up on using a [pscustomobject][].</span></span>

### <a name="saving-a-nested-hashtable-to-file"></a><span data-ttu-id="04fca-306">將巢狀雜湊表儲存至檔案</span><span class="sxs-lookup"><span data-stu-id="04fca-306">Saving a nested hashtable to file</span></span>

<span data-ttu-id="04fca-307">如果我需要將巢狀雜湊表儲存至檔案，然後再次將其讀回，則會使用 JSON Cmdlet 來執行此動作。</span><span class="sxs-lookup"><span data-stu-id="04fca-307">If I need to save a nested hashtable to a file and then read it back in again, I use the JSON cmdlets to do it.</span></span>

```powershell
$people | ConvertTo-JSON | Set-Content -Path $path
$people = Get-Content -Path $path -Raw | ConvertFrom-JSON
```

<span data-ttu-id="04fca-308">這個方法有兩個重點。</span><span class="sxs-lookup"><span data-stu-id="04fca-308">There are two important points about this method.</span></span> <span data-ttu-id="04fca-309">第一個重點是 JSON 會寫出多行，因此我需要使用 `-Raw` 選項，將其讀回成單一字串。</span><span class="sxs-lookup"><span data-stu-id="04fca-309">First is that the JSON is written out multiline so I need to use the `-Raw` option to read it back into a single string.</span></span> <span data-ttu-id="04fca-310">第二個重點是匯入的物件不再是 `[hashtable]`。</span><span class="sxs-lookup"><span data-stu-id="04fca-310">The Second is that the imported object is no longer a `[hashtable]`.</span></span> <span data-ttu-id="04fca-311">現在是 `[pscustomobject]`，而且如果不是您所預期的，可能會造成問題。</span><span class="sxs-lookup"><span data-stu-id="04fca-311">It's now a `[pscustomobject]` and that can cause issues if you don't expect it.</span></span>

<span data-ttu-id="04fca-312">注意深層巢狀雜湊表。</span><span class="sxs-lookup"><span data-stu-id="04fca-312">Watch for deeply-nested hashtables.</span></span> <span data-ttu-id="04fca-313">當您將其轉換為 JSON 時，可能不會得到您預期的結果。</span><span class="sxs-lookup"><span data-stu-id="04fca-313">When you convert it to JSON you might not get the results you expect.</span></span>

```powershell
@{ a = @{ b = @{ c = @{ d = "e" }}}} | ConvertTo-Json

{
  "a": {
    "b": {
      "c": "System.Collections.Hashtable"
    }
  }
}
```

<span data-ttu-id="04fca-314">使用 **Depth** 參數以確保您已展開所有的巢狀雜湊表。</span><span class="sxs-lookup"><span data-stu-id="04fca-314">Use **Depth** parameter to ensure that you have expanded all the nested hashtables.</span></span>

```powershell
@{ a = @{ b = @{ c = @{ d = "e" }}}} | ConvertTo-Json -Depth 3

{
  "a": {
    "b": {
      "c": {
        "d": "e"
      }
    }
  }
}
```

<span data-ttu-id="04fca-315">如果您需要其在匯入時成為 `[hashtable]`，則必須使用 `Export-CliXml` 和 `Import-CliXml` 命令。</span><span class="sxs-lookup"><span data-stu-id="04fca-315">If you need it to be a `[hashtable]` on import, then you need to use the `Export-CliXml` and `Import-CliXml` commands.</span></span>

### <a name="converting-json-to-hashtable"></a><span data-ttu-id="04fca-316">將 JSON 轉換成雜湊表</span><span class="sxs-lookup"><span data-stu-id="04fca-316">Converting JSON to Hashtable</span></span>

<span data-ttu-id="04fca-317">如果您需要將 JSON 轉換成 `[hashtable]`，我知道有一種方法，可以利用 .NET 中的 [JavaScriptSerializer][] 來執行此動作。</span><span class="sxs-lookup"><span data-stu-id="04fca-317">If you need to convert JSON to a `[hashtable]`, there's one way that I know of to do it with the [JavaScriptSerializer][] in .NET.</span></span>

```powershell
[Reflection.Assembly]::LoadWithPartialName("System.Web.Script.Serialization")
$JSSerializer = [System.Web.Script.Serialization.JavaScriptSerializer]::new()
$JSSerializer.Deserialize($json,'Hashtable')
```

<span data-ttu-id="04fca-318">從 PowerShell v6 開始，JSON 支援會使用 NewtonSoft JSON.NET 並加入雜湊表支援。</span><span class="sxs-lookup"><span data-stu-id="04fca-318">Beginning in PowerShell v6, JSON support uses the NewtonSoft JSON.NET and adds hashtable support.</span></span>

```powershell
'{ "a": "b" }' | ConvertFrom-Json -AsHashtable

Name      Value
----      -----
a         b
```

<span data-ttu-id="04fca-319">PowerShell 6.2 已將 **Depth** 參數新增至 `ConvertFrom-Json`。</span><span class="sxs-lookup"><span data-stu-id="04fca-319">PowerShell 6.2 added the **Depth** parameter to `ConvertFrom-Json`.</span></span> <span data-ttu-id="04fca-320">預設 **Depth** 為1024。</span><span class="sxs-lookup"><span data-stu-id="04fca-320">The default **Depth** is 1024.</span></span>

### <a name="reading-directly-from-a-file"></a><span data-ttu-id="04fca-321">直接從檔案讀取</span><span class="sxs-lookup"><span data-stu-id="04fca-321">Reading directly from a file</span></span>

<span data-ttu-id="04fca-322">如果您有一個檔案包含一個使用 PowerShell 語法的雜湊表，則有一種可以直接將其匯入的方式。</span><span class="sxs-lookup"><span data-stu-id="04fca-322">If you have a file that contains a hashtable using PowerShell syntax, there's a way to import it directly.</span></span>

```powershell
$content = Get-Content -Path $Path -Raw -ErrorAction Stop
$scriptBlock = [scriptblock]::Create( $content )
$scriptBlock.CheckRestrictedLanguage( $allowedCommands, $allowedVariables, $true )
$hashtable = ( & $scriptBlock )
```

<span data-ttu-id="04fca-323">其會將檔案的內容匯入至 `scriptblock`，然後在執行其之前，檢查以確定其中沒有任何其他 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="04fca-323">It imports the contents of the file into a `scriptblock`, then checks to make sure it doesn't have any other PowerShell commands in it before it executes it.</span></span>

<span data-ttu-id="04fca-324">關於這一點，您知道模組資訊清單 (.psd1 檔案) 只是雜湊表嗎？</span><span class="sxs-lookup"><span data-stu-id="04fca-324">On that note, did you know that a module manifest (the psd1 file) is just a hashtable?</span></span>

## <a name="keys-can-be-any-object"></a><span data-ttu-id="04fca-325">索引鍵可以是任何物件</span><span class="sxs-lookup"><span data-stu-id="04fca-325">Keys can be any object</span></span>

<span data-ttu-id="04fca-326">在大部分的時候，索引鍵只是字串。</span><span class="sxs-lookup"><span data-stu-id="04fca-326">Most of the time, the keys are just strings.</span></span> <span data-ttu-id="04fca-327">因此，我們可以在任何項目前後加上引號，使其成為索引鍵。</span><span class="sxs-lookup"><span data-stu-id="04fca-327">So we can put quotes around anything and make it a key.</span></span>

```powershell
$person = @{
    'full name' = 'Kevin Marquette'
    '#' = 3978
}
$person['full name']
```

<span data-ttu-id="04fca-328">您可以做到一些可能沒有意識到可以做到的事情。</span><span class="sxs-lookup"><span data-stu-id="04fca-328">You can do some odd things that you may not have realized you could do.</span></span>

```powershell
$person.'full name'

$key = 'full name'
$person.$key
```

<span data-ttu-id="04fca-329">這是因為您可以做到一些事情，這並不表示您應該這麼做。</span><span class="sxs-lookup"><span data-stu-id="04fca-329">Just because you can do something, it doesn't mean that you should.</span></span> <span data-ttu-id="04fca-330">最後一個看起來就像是等待發生的錯誤 (bug)，這讓讀取您程式碼的任何人很容易產生誤解。</span><span class="sxs-lookup"><span data-stu-id="04fca-330">That last one just looks like a bug waiting to happen and would be easily misunderstood by anyone reading your code.</span></span>

<span data-ttu-id="04fca-331">從技術上來說，您的索引鍵不一定是字串，但如果您只使用字串，就比較容易思考。</span><span class="sxs-lookup"><span data-stu-id="04fca-331">Technically your key doesn't have to be a string but they're easier to think about if you only use strings.</span></span> <span data-ttu-id="04fca-332">不過，索引編製並不適用於複雜索引鍵。</span><span class="sxs-lookup"><span data-stu-id="04fca-332">However, indexing doesn't work well with the complex keys.</span></span>

```powershell
$ht = @{ @(1,2,3) = "a" }
$ht

Name                           Value
----                           -----
{1, 2, 3}                      a
```

<span data-ttu-id="04fca-333">依索引鍵存取雜湊表中的值不一定會有作用。</span><span class="sxs-lookup"><span data-stu-id="04fca-333">Accessing a value in the hashtable by its key doesn't always work.</span></span> <span data-ttu-id="04fca-334">例如：</span><span class="sxs-lookup"><span data-stu-id="04fca-334">For example:</span></span>

```powershell
$key = $ht.keys[0]
$ht.$($key)
a
$ht[$key]
a
```

<span data-ttu-id="04fca-335">當索引鍵是陣列時，即必須將 `$key` 變數包裝在子運算式中，使其可與成員存取 (`.`) 標記法搭配使用。</span><span class="sxs-lookup"><span data-stu-id="04fca-335">When the key is an array, you must wrap the `$key` variable in a subexpression so that it can be used with member access (`.`) notation.</span></span> <span data-ttu-id="04fca-336">或者，您也可使用陣列索引 (`[]`) 標記法。</span><span class="sxs-lookup"><span data-stu-id="04fca-336">Or, you can use array index (`[]`) notation.</span></span>

## <a name="use-in-automatic-variables"></a><span data-ttu-id="04fca-337">用於自動變數</span><span class="sxs-lookup"><span data-stu-id="04fca-337">Use in automatic variables</span></span>

### <a name="psboundparameters"></a><span data-ttu-id="04fca-338">$PSBoundParameters</span><span class="sxs-lookup"><span data-stu-id="04fca-338">$PSBoundParameters</span></span>

<span data-ttu-id="04fca-339">[$PSBoundParameters][] 是只存在於函式內容中的自動變數。</span><span class="sxs-lookup"><span data-stu-id="04fca-339">[$PSBoundParameters][] is an automatic variable that only exists inside the context of a function.</span></span>
<span data-ttu-id="04fca-340">其包含呼叫函數時搭配的所有參數。</span><span class="sxs-lookup"><span data-stu-id="04fca-340">It contains all the parameters that the function was called with.</span></span> <span data-ttu-id="04fca-341">這不是真正的雜湊表，但是足以讓您將其等同視之。</span><span class="sxs-lookup"><span data-stu-id="04fca-341">This isn't exactly a hashtable but close enough that you can treat it like one.</span></span>

<span data-ttu-id="04fca-342">其中包括移除索引鍵，並將其展開至其他函式。</span><span class="sxs-lookup"><span data-stu-id="04fca-342">That includes removing keys and splatting it to other functions.</span></span> <span data-ttu-id="04fca-343">如果您發現自己撰寫的是 Proxy 函式，請仔細查看一下。</span><span class="sxs-lookup"><span data-stu-id="04fca-343">If you find yourself writing proxy functions, take a closer look at this one.</span></span>

<span data-ttu-id="04fca-344">如需其他詳細資料，請參閱 [about_Automatic_Variables][]。</span><span class="sxs-lookup"><span data-stu-id="04fca-344">See [about_Automatic_Variables][] for more details.</span></span>

### <a name="psboundparameters-gotcha"></a><span data-ttu-id="04fca-345">PSBoundParameters 陷阱</span><span class="sxs-lookup"><span data-stu-id="04fca-345">PSBoundParameters gotcha</span></span>

<span data-ttu-id="04fca-346">要記住的一個重點是，這只包含當做參數傳入的值。</span><span class="sxs-lookup"><span data-stu-id="04fca-346">One important thing to remember is that this only includes the values that are passed in as parameters.</span></span> <span data-ttu-id="04fca-347">如果您也有具有預設值的參數，但呼叫者未將其傳入，則 `$PSBoundParameters` 不會包含這些值。</span><span class="sxs-lookup"><span data-stu-id="04fca-347">If you also have parameters with default values but aren't passed in by the caller, `$PSBoundParameters` doesn't contain those values.</span></span> <span data-ttu-id="04fca-348">這通常會被輕忽掉。</span><span class="sxs-lookup"><span data-stu-id="04fca-348">This is commonly overlooked.</span></span>

### <a name="psdefaultparametervalues"></a><span data-ttu-id="04fca-349">$PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="04fca-349">$PSDefaultParameterValues</span></span>

<span data-ttu-id="04fca-350">這個自動變數可讓您將預設值指派給任何 Cmdlet，而無需變更 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="04fca-350">This automatic variable lets you assign default values to any cmdlet without changing the cmdlet.</span></span>
<span data-ttu-id="04fca-351">請看一下這個範例。</span><span class="sxs-lookup"><span data-stu-id="04fca-351">Take a look at this example.</span></span>

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "UTF8"
```

<span data-ttu-id="04fca-352">這會新增一個項目至 `$PSDefaultParameterValues` 雜湊表，將 `UTF8` 設定為 `Out-File -Encoding` 參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="04fca-352">This adds an entry to the `$PSDefaultParameterValues` hashtable that sets `UTF8` as the default value for the `Out-File -Encoding` parameter.</span></span> <span data-ttu-id="04fca-353">這是工作階段特有的，因此應該將其置於您的 `$profile` 中。</span><span class="sxs-lookup"><span data-stu-id="04fca-353">This is session-specific so you should place it in your `$profile`.</span></span>

<span data-ttu-id="04fca-354">我經常使用這個來預先指派我經常輸入的值。</span><span class="sxs-lookup"><span data-stu-id="04fca-354">I use this often to pre-assign values that I type quite often.</span></span>

```powershell
$PSDefaultParameterValues[ "Connect-VIServer:Server" ] = 'VCENTER01.contoso.local'
```

<span data-ttu-id="04fca-355">這也會接受萬用字元，讓您可以大量設定這些值。</span><span class="sxs-lookup"><span data-stu-id="04fca-355">This also accepts wildcards so you can set values in bulk.</span></span> <span data-ttu-id="04fca-356">以下是一些您可以使用的方法：</span><span class="sxs-lookup"><span data-stu-id="04fca-356">Here are some ways you can use that:</span></span>

```powershell
$PSDefaultParameterValues[ "Get-*:Verbose" ] = $true
$PSDefaultParameterValues[ "*:Credential" ] = Get-Credential
```

<span data-ttu-id="04fca-357">如需更深入的明細，請參閱由 [Michael Sorens][] 撰寫的[自動預設值][]，這是一篇絕佳的文章。</span><span class="sxs-lookup"><span data-stu-id="04fca-357">For a more in-depth breakdown, see this great article on [Automatic Defaults][] by [Michael Sorens][].</span></span>

## <a name="regex-matches"></a><span data-ttu-id="04fca-358">Regex $Matches</span><span class="sxs-lookup"><span data-stu-id="04fca-358">Regex $Matches</span></span>

<span data-ttu-id="04fca-359">使用 `-match` 運算子時，會使用比對的結果來建立稱為 `$matches` 的自動變數。</span><span class="sxs-lookup"><span data-stu-id="04fca-359">When you use the `-match` operator, an automatic variable called `$matches` is created with the results of the match.</span></span> <span data-ttu-id="04fca-360">如果您的規則運算式中有任何子運算式，也會列出那些子比對。</span><span class="sxs-lookup"><span data-stu-id="04fca-360">If you have any sub expressions in your regex, those sub matches are also listed.</span></span>

```powershell
$message = 'My SSN is 123-45-6789.'

$message -match 'My SSN is (.+)\.'
$Matches[0]
$Matches[1]
```

### <a name="named-matches"></a><span data-ttu-id="04fca-361">具名比對</span><span class="sxs-lookup"><span data-stu-id="04fca-361">Named matches</span></span>

<span data-ttu-id="04fca-362">這是我最愛的其中一項功能，大部分人都不知道。</span><span class="sxs-lookup"><span data-stu-id="04fca-362">This is one of my favorite features that most people don't know about.</span></span> <span data-ttu-id="04fca-363">如果您使用具名規則運算式比對，則可以依據比對上的名稱來存取該比對。</span><span class="sxs-lookup"><span data-stu-id="04fca-363">If you use a named regex match, then you can access that match by name on the matches.</span></span>

```powershell
$message = 'My Name is Kevin and my SSN is 123-45-6789.'

if($message -match 'My Name is (?<Name>.+) and my SSN is (?<SSN>.+)\.')
{
    $Matches.Name
    $Matches.SSN
}
```

<span data-ttu-id="04fca-364">在上述範例中，`(?<Name>.*)` 是具名子運算式。</span><span class="sxs-lookup"><span data-stu-id="04fca-364">In the example above, the `(?<Name>.*)` is a named sub expression.</span></span> <span data-ttu-id="04fca-365">此值接著會放置在 `$Matches.Name` 屬性中。</span><span class="sxs-lookup"><span data-stu-id="04fca-365">This value is then placed in the `$Matches.Name` property.</span></span>

## <a name="group-object--ashashtable"></a><span data-ttu-id="04fca-366">Group-Object -AsHashtable</span><span class="sxs-lookup"><span data-stu-id="04fca-366">Group-Object -AsHashtable</span></span>

<span data-ttu-id="04fca-367">少有人知的 `Group-Object` 功能，其可以為您將某些資料集變成雜湊表。</span><span class="sxs-lookup"><span data-stu-id="04fca-367">One little known feature of `Group-Object` is that it can turn some datasets into a hashtable for you.</span></span>

```powershell
Import-CSV $Path | Group-Object -AsHashtable -Property email
```

<span data-ttu-id="04fca-368">這會將每個資料列加入雜湊表中，並使用指定的屬性做為存取其的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="04fca-368">This will add each row into a hashtable and use the specified property as the key to access it.</span></span>

## <a name="copying-hashtables"></a><span data-ttu-id="04fca-369">複製雜湊表</span><span class="sxs-lookup"><span data-stu-id="04fca-369">Copying Hashtables</span></span>

<span data-ttu-id="04fca-370">要知道的一個重點是，雜湊表是物件。</span><span class="sxs-lookup"><span data-stu-id="04fca-370">One important thing to know is that hashtables are objects.</span></span> <span data-ttu-id="04fca-371">此外，每個變數只是物件的參考。</span><span class="sxs-lookup"><span data-stu-id="04fca-371">And each variable is just a reference to an object.</span></span> <span data-ttu-id="04fca-372">這表示需要更多工作，才能建立雜湊表的有效複本。</span><span class="sxs-lookup"><span data-stu-id="04fca-372">This means that it takes more work to make a valid copy of a hashtable.</span></span>

### <a name="assigning-reference-types"></a><span data-ttu-id="04fca-373">指派參考型別</span><span class="sxs-lookup"><span data-stu-id="04fca-373">Assigning reference types</span></span>

<span data-ttu-id="04fca-374">當您有一個雜湊表並將其指派給第二個變數時，這兩個變數都會指向相同的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="04fca-374">When you have one hashtable and assign it to a second variable, both variables point to the same hashtable.</span></span>

```powershell
PS> $orig = @{name='orig'}
PS> $copy = $orig
PS> $copy.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.name
PS> 'Orig: [{0}]' -f $orig.name

Copy: [copy]
Orig: [copy]
```

<span data-ttu-id="04fca-375">這強調這些雜湊表是相同的，因為變更其中一個變數的值時，也會變更另一個變數中的值。</span><span class="sxs-lookup"><span data-stu-id="04fca-375">This highlights that they're the same because altering the values in one will also alter the values in the other.</span></span> <span data-ttu-id="04fca-376">這也適用於將雜湊表傳遞至其他函式時。</span><span class="sxs-lookup"><span data-stu-id="04fca-376">This also applies when passing hashtables into other functions.</span></span> <span data-ttu-id="04fca-377">如果這些函式對該雜湊表進行變更，您的原始雜湊表也會變更。</span><span class="sxs-lookup"><span data-stu-id="04fca-377">If those functions make changes to that hashtable, your original is also altered.</span></span>

### <a name="shallow-copies-single-level"></a><span data-ttu-id="04fca-378">淺層複製，單層</span><span class="sxs-lookup"><span data-stu-id="04fca-378">Shallow copies, single level</span></span>

<span data-ttu-id="04fca-379">如果我們有像上述範例的簡單雜湊表，則可以使用 `.Clone()` 來進行淺層複製。</span><span class="sxs-lookup"><span data-stu-id="04fca-379">If we have a simple hashtable like our example above, we can use `.Clone()` to make a shallow copy.</span></span>

```powershell
PS> $orig = @{name='orig'}
PS> $copy = $orig.Clone()
PS> $copy.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.name
PS> 'Orig: [{0}]' -f $orig.name

Copy: [copy]
Orig: [orig]
```

<span data-ttu-id="04fca-380">這可讓我們對某個雜湊表進行一些不會影響另一個雜湊表的基本變更。</span><span class="sxs-lookup"><span data-stu-id="04fca-380">This will allow us to make some basic changes to one that don't impact the other.</span></span>

### <a name="shallow-copies-nested"></a><span data-ttu-id="04fca-381">淺層複製，巢狀</span><span class="sxs-lookup"><span data-stu-id="04fca-381">Shallow copies, nested</span></span>

<span data-ttu-id="04fca-382">為何稱為淺層複製的原因是其只會複製基層屬性。</span><span class="sxs-lookup"><span data-stu-id="04fca-382">The reason why it's called a shallow copy is because it only copies the base level properties.</span></span> <span data-ttu-id="04fca-383">如果其中一個屬性是參考型別 (例如另一個雜湊表)，則這些巢狀物件仍會指向彼此。</span><span class="sxs-lookup"><span data-stu-id="04fca-383">If one of those properties is a reference type (like another hashtable), then those nested objects will still point to each other.</span></span>

```powershell
PS> $orig = @{
        person=@{
            name='orig'
        }
    }
PS> $copy = $orig.Clone()
PS> $copy.person.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.person.name
PS> 'Orig: [{0}]' -f $orig.person.name

Copy: [copy]
Orig: [copy]
```

<span data-ttu-id="04fca-384">因此，您可以看到，即使我複製了雜湊表，也不會複製 `person` 的參考。</span><span class="sxs-lookup"><span data-stu-id="04fca-384">So you can see that even though I cloned the hashtable, the reference to `person` wasn't cloned.</span></span> <span data-ttu-id="04fca-385">我們需要進行深層複製，才能真正具有未連結到第一個雜湊表的第二個雜湊表。</span><span class="sxs-lookup"><span data-stu-id="04fca-385">We need to make a deep copy to truly have a second hashtable that isn't linked to the first.</span></span>

### <a name="deep-copies"></a><span data-ttu-id="04fca-386">深層複製</span><span class="sxs-lookup"><span data-stu-id="04fca-386">Deep copies</span></span>

<span data-ttu-id="04fca-387">在撰寫本文時，我並不知道只要深層複製雜湊表 (並將其保留為雜湊表)，是一種聰明的方式。</span><span class="sxs-lookup"><span data-stu-id="04fca-387">At the time of writing this, I'm not aware of any clever ways to just make a deep copy of a hashtable (and keep it as a hashtable).</span></span> <span data-ttu-id="04fca-388">這只是某人需要撰寫的其中一件事。</span><span class="sxs-lookup"><span data-stu-id="04fca-388">That's just one of those things that someone needs to write.</span></span>
<span data-ttu-id="04fca-389">以下是執行此動作的快速方法。</span><span class="sxs-lookup"><span data-stu-id="04fca-389">Here is a quick method to do that.</span></span>

```powershell
function Get-DeepClone
{
    [CmdletBinding()]
    param(
        $InputObject
    )
    process
    {
        if($InputObject -is [hashtable]) {
            $clone = @{}
            foreach($key in $InputObject.keys)
            {
                $clone[$key] = Get-DeepClone $InputObject[$key]
            }
            return $clone
        } else {
            return $InputObject
        }
    }
}
```

<span data-ttu-id="04fca-390">其不會處理任何其他參考型別或陣列，但這是很好的起點。</span><span class="sxs-lookup"><span data-stu-id="04fca-390">It doesn't handle any other reference types or arrays, but it's a good starting point.</span></span>

## <a name="anything-else"></a><span data-ttu-id="04fca-391">任何其他項目？</span><span class="sxs-lookup"><span data-stu-id="04fca-391">Anything else?</span></span>

<span data-ttu-id="04fca-392">我很快涵蓋了許多基礎的東西。</span><span class="sxs-lookup"><span data-stu-id="04fca-392">I covered a lot of ground quickly.</span></span> <span data-ttu-id="04fca-393">我希望您可以走出去學習新的事物，或在每次閱讀時有更深的領悟。</span><span class="sxs-lookup"><span data-stu-id="04fca-393">My hope is that you walk away leaning something new or understanding it better every time you read this.</span></span> <span data-ttu-id="04fca-394">因為我涵蓋了這項功能的完整範疇，所以目前可能會有一些層面不適用於您。</span><span class="sxs-lookup"><span data-stu-id="04fca-394">Because I covered the full spectrum of this feature, there are aspects that just may not apply to you right now.</span></span> <span data-ttu-id="04fca-395">這完全沒問題，而且是預期的情況，視您使用 PowerShell 的程度而定。</span><span class="sxs-lookup"><span data-stu-id="04fca-395">That is perfectly OK and is kind of expected depending on how much you work with PowerShell.</span></span>

<!-- link references -->
[原始版本]: https://powershellexplained.com/2016-11-06-powershell-hashtable-everything-you-wanted-to-know-about/
[original version]: https://powershellexplained.com/2016-11-06-powershell-hashtable-everything-you-wanted-to-know-about/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[雜湊表]: /powershell/module/microsoft.powershell.core/about/about_hash_tables
[hashtables]: /powershell/module/microsoft.powershell.core/about/about_hash_tables
[陣列]: /powershell/module/microsoft.powershell.core/about/about_arrays
[arrays]: /powershell/module/microsoft.powershell.core/about/about_arrays
[若效能至上，請將其進行測試]: https://github.com/PoshCode/PowerShellPracticeAndStyle/blob/master/Best-Practices/Performance.md
[If performance matters, test it]: https://github.com/PoshCode/PowerShellPracticeAndStyle/blob/master/Best-Practices/Performance.md
[展開]: /powershell/module/microsoft.powershell.core/about/about_splatting
[splatting]: /powershell/module/microsoft.powershell.core/about/about_splatting
[pscustomobject]: everything-about-pscustomobject.md
[JavaScriptSerializer]: /dotnet/api/system.web.script.serialization.javascriptserializer?view=netframework-4.8&preserve-view=true
[PSBoundParameters]: https://tommymaynard.com/the-psboundparameters-automatic-variable-2016/
[about_Automatic_Variables]: /powershell/module/microsoft.powershell.core/about/about_automatic_variables
[自動預設值]: https://www.simple-talk.com/sysadmin/PowerShell/PowerShell-time-saver-automatic-defaults/
[Automatic Defaults]: https://www.simple-talk.com/sysadmin/PowerShell/PowerShell-time-saver-automatic-defaults/
[Michael Sorens]: http://cleancode.sourceforge.net/wwwdoc/about.html
