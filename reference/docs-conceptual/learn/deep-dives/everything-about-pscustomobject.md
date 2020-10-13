---
title: 您想知道有關 PSCustomObject 的一切
description: PSCustomObject 可讓您用簡單的方法來建立結構化資料。
ms.date: 10/05/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: ccbdcdae5ad38f555233dffbed7e8a6ec2b0726b
ms.sourcegitcommit: 1695df0d241c0390cac71a7401e61198fc6ff756
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2020
ms.locfileid: "91772315"
---
# <a name="everything-you-wanted-to-know-about-pscustomobject"></a><span data-ttu-id="99675-103">您想知道有關 PSCustomObject 的一切</span><span class="sxs-lookup"><span data-stu-id="99675-103">Everything you wanted to know about PSCustomObject</span></span>

<span data-ttu-id="99675-104">`PSCustomObject` 是可以加入您 PowerShell 工具組中的一項優秀工具。</span><span class="sxs-lookup"><span data-stu-id="99675-104">`PSCustomObject`s are a great tool to add into your PowerShell tool belt.</span></span> <span data-ttu-id="99675-105">讓我們從基本概念開始，再循序漸進說明進階功能。</span><span class="sxs-lookup"><span data-stu-id="99675-105">Let's start with the basics and work our way into the more advanced features.</span></span> <span data-ttu-id="99675-106">`PSCustomObject` 旨在使用簡單的方法建立結構化資料。</span><span class="sxs-lookup"><span data-stu-id="99675-106">The idea behind using a `PSCustomObject` is to have a simple way to create structured data.</span></span> <span data-ttu-id="99675-107">請見第一個範例，您便能更清楚地了解這句話的意思。</span><span class="sxs-lookup"><span data-stu-id="99675-107">Take a look at the first example and you'll have a better idea of what that means.</span></span>

> [!NOTE]
> <span data-ttu-id="99675-108">本文的[原始版本][]出現在 [@KevinMarquette][] 所撰寫的部落格中。</span><span class="sxs-lookup"><span data-stu-id="99675-108">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="99675-109">PowerShell 小組感謝 Kevin 與我們分享此內容。</span><span class="sxs-lookup"><span data-stu-id="99675-109">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="99675-110">請前往 [PowerShellExplained.com][] 瀏覽 Kevin 的部落格。</span><span class="sxs-lookup"><span data-stu-id="99675-110">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="creating-a-pscustomobject"></a><span data-ttu-id="99675-111">建立 PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="99675-111">Creating a PSCustomObject</span></span>

<span data-ttu-id="99675-112">我非常喜歡在 PowerShell 中使用 `[PSCustomObject]`。</span><span class="sxs-lookup"><span data-stu-id="99675-112">I love using `[PSCustomObject]` in PowerShell.</span></span> <span data-ttu-id="99675-113">建立可用的物件從未如此簡單。</span><span class="sxs-lookup"><span data-stu-id="99675-113">Creating a usable object has never been easier.</span></span>
<span data-ttu-id="99675-114">因此，我將跳過使用其他方法來建立物件，請注意其中大部分的範例均需使用 PowerShell v3.0 及更新版本。</span><span class="sxs-lookup"><span data-stu-id="99675-114">Because of that, I'm going to skip over all the other ways you can create an object but I need to mention that most of these examples are PowerShell v3.0 and newer.</span></span>

```powershell
$myObject = [PSCustomObject]@{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}
```

<span data-ttu-id="99675-115">這個方法相當適合我，因為我幾乎將雜湊表用於任何項目。</span><span class="sxs-lookup"><span data-stu-id="99675-115">This method works well for me because I use hashtables for just about everything.</span></span> <span data-ttu-id="99675-116">但有時候我會希望 PowerShell 能將雜湊表視為物件處理。</span><span class="sxs-lookup"><span data-stu-id="99675-116">But there are times when I would like PowerShell to treat hashtables more like an object.</span></span> <span data-ttu-id="99675-117">您會注意到的一個差異處便是當您想要使用 `Format-Table` 或 `Export-CSV` 時，卻發現雜湊表只不過是索引鍵/值組的集合。</span><span class="sxs-lookup"><span data-stu-id="99675-117">The first place you notice the difference is when you want to use `Format-Table` or `Export-CSV` and you realize that a hashtable is just a collection of key/value pairs.</span></span>

<span data-ttu-id="99675-118">您接著可以存取和使用值，其方式與使用一般物件相同。</span><span class="sxs-lookup"><span data-stu-id="99675-118">You can then access and use the values like you would a normal object.</span></span>

```powershell
$myObject.Name
```

### <a name="converting-a-hashtable"></a><span data-ttu-id="99675-119">轉換雜湊表</span><span class="sxs-lookup"><span data-stu-id="99675-119">Converting a hashtable</span></span>

<span data-ttu-id="99675-120">在討論這個主題的同時，您知道可以這樣做嗎：</span><span class="sxs-lookup"><span data-stu-id="99675-120">While I am on the topic, did you know you could do this:</span></span>

```powershell
$myHashtable = @{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}
$myObject = [pscustomobject]$myHashtable
```

<span data-ttu-id="99675-121">我偏好從一開始就建立物件，但有時候您可能需要先使用雜湊表。</span><span class="sxs-lookup"><span data-stu-id="99675-121">I do prefer to create the object from the start but there are times you have to work with a hashtable first.</span></span> <span data-ttu-id="99675-122">因為建構函式會取得物件屬性的雜湊表，所以此範例可以正常運作。</span><span class="sxs-lookup"><span data-stu-id="99675-122">This example works because the constructor takes a hashtable for the object properties.</span></span> <span data-ttu-id="99675-123">有一點相當重要，雖然此方法可以正常運作，但並非完全相等的項目。</span><span class="sxs-lookup"><span data-stu-id="99675-123">One important note is that while this method works, it isn't an exact equivalent.</span></span> <span data-ttu-id="99675-124">最大差異在於屬性的順序並未獲得保留。</span><span class="sxs-lookup"><span data-stu-id="99675-124">The biggest difference is that the order of the properties isn't preserved.</span></span>

### <a name="legacy-approach"></a><span data-ttu-id="99675-125">舊版方法</span><span class="sxs-lookup"><span data-stu-id="99675-125">Legacy approach</span></span>

<span data-ttu-id="99675-126">您可能曾看過有人使用 `New-Object` 來建立自訂物件。</span><span class="sxs-lookup"><span data-stu-id="99675-126">You may have seen people use `New-Object` to create custom objects.</span></span>

```powershell
$myHashtable = @{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}

$myObject = New-Object -TypeName PSObject -Property $myHashtable
```

<span data-ttu-id="99675-127">這種方法的效率較低，但在舊版 PowerShell 中這可能是最好的選項了。</span><span class="sxs-lookup"><span data-stu-id="99675-127">This way is quite a bit slower but it may be your best option on early versions of PowerShell.</span></span>

### <a name="saving-to-a-file"></a><span data-ttu-id="99675-128">儲存至檔案</span><span class="sxs-lookup"><span data-stu-id="99675-128">Saving to a file</span></span>

<span data-ttu-id="99675-129">我發現將雜湊表儲存至檔案的最佳方式是將其儲存為 JSON。</span><span class="sxs-lookup"><span data-stu-id="99675-129">I find the best way to save a hashtable to a file is to save it as JSON.</span></span> <span data-ttu-id="99675-130">您可以將其匯入回 `[PSCustomObject]`</span><span class="sxs-lookup"><span data-stu-id="99675-130">You can import it back into a `[PSCustomObject]`</span></span>

```powershell
$myObject | ConvertTo-Json -depth 1- | Set-Content -Path $Path
$myObject = Get-Content -Path $Path | ConvertFrom-Json
```

<span data-ttu-id="99675-131">我在[讀取和寫入檔案的許多方式][]一文中談及更多將物件儲存到檔案的方式。</span><span class="sxs-lookup"><span data-stu-id="99675-131">I cover more ways to save objects to a file in my article on [The many ways to read and write to files][].</span></span>

## <a name="working-with-properties"></a><span data-ttu-id="99675-132">使用屬性</span><span class="sxs-lookup"><span data-stu-id="99675-132">Working with properties</span></span>

### <a name="adding-properties"></a><span data-ttu-id="99675-133">新增屬性</span><span class="sxs-lookup"><span data-stu-id="99675-133">Adding properties</span></span>

<span data-ttu-id="99675-134">您仍然可以使用 `Add-Member` 將新的屬性新增到 `PSCustomObject`。</span><span class="sxs-lookup"><span data-stu-id="99675-134">You can still add new properties to your `PSCustomObject` with `Add-Member`.</span></span>

```powershell
$myObject | Add-Member -MemberType NoteProperty -Name `ID` -Value 'KevinMarquette'

$myObject.ID
```

### <a name="remove-properties"></a><span data-ttu-id="99675-135">移除屬性</span><span class="sxs-lookup"><span data-stu-id="99675-135">Remove properties</span></span>

<span data-ttu-id="99675-136">您也可以刪除物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="99675-136">You can also remove properties off of an object.</span></span>

```powershell
$myObject.psobject.properties.remove('ID')
```

<span data-ttu-id="99675-137">`psobject` 是一種隱藏屬性，可以讓您存取基底物件的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="99675-137">The `psobject` is a hidden property that gives you access to base object metadata.</span></span>

### <a name="enumerating-property-names"></a><span data-ttu-id="99675-138">列舉屬性名稱</span><span class="sxs-lookup"><span data-stu-id="99675-138">Enumerating property names</span></span>

<span data-ttu-id="99675-139">有時候，您需要物件上所有屬性名稱的清單。</span><span class="sxs-lookup"><span data-stu-id="99675-139">Sometimes you need a list of all the property names on an object.</span></span>

```powershell
$myObject | Get-Member -MemberType NoteProperty | Select -ExpandProperty Name
```

<span data-ttu-id="99675-140">我們也可以從 `psobject` 屬性取得相同的清單。</span><span class="sxs-lookup"><span data-stu-id="99675-140">We can get this same list off of the `psobject` property too.</span></span>

```powershell
$myobject.psobject.properties.name
```

### <a name="dynamically-accessing-properties"></a><span data-ttu-id="99675-141">動態存取屬性</span><span class="sxs-lookup"><span data-stu-id="99675-141">Dynamically accessing properties</span></span>

<span data-ttu-id="99675-142">我已經提到您可以直接存取屬性值。</span><span class="sxs-lookup"><span data-stu-id="99675-142">I already mentioned that you can access property values directly.</span></span>

```powershell
$myObject.Name
```

<span data-ttu-id="99675-143">您可以使用字串作為屬性名稱，其仍會正常運作。</span><span class="sxs-lookup"><span data-stu-id="99675-143">You can use a string for the property name and it will still work.</span></span>

```powershell
$myObject.'Name'
```

<span data-ttu-id="99675-144">我們可以更進一步地進行這項操作，使用變數作為屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="99675-144">We can take this one more step and use a variable for the property name.</span></span>

```powershell
$property = 'Name'
$myObject.$property
```

<span data-ttu-id="99675-145">我知道這看起來很奇怪，但這會正常運作。</span><span class="sxs-lookup"><span data-stu-id="99675-145">I know that looks strange, but it works.</span></span>

### <a name="convert-pscustomobject-into-a-hashtable"></a><span data-ttu-id="99675-146">將 PSCustomObject 轉換成雜湊表</span><span class="sxs-lookup"><span data-stu-id="99675-146">Convert PSCustomObject into a hashtable</span></span>

<span data-ttu-id="99675-147">若要繼續上一節的內容，您可以以動態方式逐步存取屬性，並從中建立雜湊表。</span><span class="sxs-lookup"><span data-stu-id="99675-147">To continue on from the last section, you can dynamically walk the properties and create a hashtable from them.</span></span>

```powershell
$hashtable = @{}
foreach( $property in $myobject.psobject.properties.name )
{
    $hashtable[$property] = $myObject.$property
}
```

### <a name="testing-for-properties"></a><span data-ttu-id="99675-148">測試屬性</span><span class="sxs-lookup"><span data-stu-id="99675-148">Testing for properties</span></span>

<span data-ttu-id="99675-149">若您需要了解一個屬性是否存在，您可以直接檢查該屬性是否具備值。</span><span class="sxs-lookup"><span data-stu-id="99675-149">If you need to know if a property exists, you could just check for that property to have a value.</span></span>

```powershell
if( $null -ne $myObject.ID )
```

<span data-ttu-id="99675-150">但是，如果該值可能為 `$null`，則可檢查 `psobject.properties` 以確定該值是否存在。</span><span class="sxs-lookup"><span data-stu-id="99675-150">But if the value could be `$null` you can check to see if it exists by checking the `psobject.properties` for it.</span></span>

```powershell
if( $myobject.psobject.properties.match('ID').Count )
```

## <a name="adding-object-methods"></a><span data-ttu-id="99675-151">新增物件方法</span><span class="sxs-lookup"><span data-stu-id="99675-151">Adding object methods</span></span>

<span data-ttu-id="99675-152">若您需要將指令碼方法新增到物件，您可以使用 `Add-Member` 和 `ScriptBlock` 進行這項操作。</span><span class="sxs-lookup"><span data-stu-id="99675-152">If you need to add a script method to an object, you can do it with `Add-Member` and a `ScriptBlock`.</span></span> <span data-ttu-id="99675-153">您必須使用 `this` 自動變數來參考目前的物件。</span><span class="sxs-lookup"><span data-stu-id="99675-153">You have to use the `this` automatic variable reference the current object.</span></span> <span data-ttu-id="99675-154">以下是將物件轉換成雜湊表的 `scriptblock`。</span><span class="sxs-lookup"><span data-stu-id="99675-154">Here is a `scriptblock` to turn an object into a hashtable.</span></span> <span data-ttu-id="99675-155">(與上一個範例相同的程式碼)</span><span class="sxs-lookup"><span data-stu-id="99675-155">(same code form the last example)</span></span>

```powershell
$ScriptBlock = {
    $hashtable = @{}
    foreach( $property in $this.psobject.properties.name )
    {
        $hashtable[$property] = $this.$property
    }
    return $hashtable
}
```

<span data-ttu-id="99675-156">然後，我們將其作為指令碼屬性新增到物件。</span><span class="sxs-lookup"><span data-stu-id="99675-156">Then we add it to our object as a script property.</span></span>

```powershell
$memberParam = @{
    MemberType = "ScriptMethod"
    InputObject = $myobject
    Name = "ToHashtable"
    Value = $scriptBlock
}
Add-Member @memberParam
```

<span data-ttu-id="99675-157">接著呼叫函數 (如下所示)：</span><span class="sxs-lookup"><span data-stu-id="99675-157">Then we can call our function like this:</span></span>

```powershell
$myObject.ToHashtable()
```

### <a name="objects-vs-value-types"></a><span data-ttu-id="99675-158">物件與實值型別</span><span class="sxs-lookup"><span data-stu-id="99675-158">Objects vs Value types</span></span>

<span data-ttu-id="99675-159">物件與實值型別處理變數指派的方式不同。</span><span class="sxs-lookup"><span data-stu-id="99675-159">Objects and value types don't handle variable assignments the same way.</span></span> <span data-ttu-id="99675-160">若您將實值型別互相指派，只是把值複製到新的變數。</span><span class="sxs-lookup"><span data-stu-id="99675-160">If you assign value types to each other, only the value get copied to the new variable.</span></span>

```powershell
$first = 1
$second = $first
$second = 2
```

<span data-ttu-id="99675-161">在此情況下，`$first` 為 1，`$second` 為 2。</span><span class="sxs-lookup"><span data-stu-id="99675-161">In this case, `$first` is 1 and `$second` is 2.</span></span>

<span data-ttu-id="99675-162">物件變數會保存實際物件的參考。</span><span class="sxs-lookup"><span data-stu-id="99675-162">Object variables hold a reference to the actual object.</span></span> <span data-ttu-id="99675-163">當您將一個物件指派給新的變數時，其仍會參考相同的物件。</span><span class="sxs-lookup"><span data-stu-id="99675-163">When you assign one object to a new variable, they still reference the same object.</span></span>

```powershell
$third = [PSCustomObject]@{Key=3}
$fourth = $third
$fourth.Key = 4
```

<span data-ttu-id="99675-164">因為 `$third` 與 `$fourth` 會參考物件的相同執行個體，所以 `$third.key` 與 `$fourth.Key` 皆為 4。</span><span class="sxs-lookup"><span data-stu-id="99675-164">Because `$third` and `$fourth` reference the same instance of an object, both `$third.key` and `$fourth.Key` are 4.</span></span>

### <a name="psobjectcopy"></a><span data-ttu-id="99675-165">psobject.copy()</span><span class="sxs-lookup"><span data-stu-id="99675-165">psobject.copy()</span></span>

<span data-ttu-id="99675-166">如果您需要物件的真正複本，您可以進行複製。</span><span class="sxs-lookup"><span data-stu-id="99675-166">If you need a true copy of an object, you can clone it.</span></span>

```powershell
$third = [PSCustomObject]@{Key=3}
$fourth = $third.psobject.copy()
$fourth.Key = 4
```

<span data-ttu-id="99675-167">複製會建立物件的淺層複製 (Shallow Copy)。</span><span class="sxs-lookup"><span data-stu-id="99675-167">Clone creates a shallow copy of the object.</span></span> <span data-ttu-id="99675-168">其現在擁有不同的執行個體，且在此範例中，`$third.key` 為 3，`$fourth.Key` 則為 4。</span><span class="sxs-lookup"><span data-stu-id="99675-168">They have different instances now and `$third.key` is 3 and `$fourth.Key` is 4 in this example.</span></span>

<span data-ttu-id="99675-169">我將這稱為淺層複製 (Shallow Copy)，因為若您擁有巢狀物件。</span><span class="sxs-lookup"><span data-stu-id="99675-169">I call this a shallow copy because if you have nested objects.</span></span> <span data-ttu-id="99675-170">(其中屬性會包含其他物件)。</span><span class="sxs-lookup"><span data-stu-id="99675-170">(where the properties contain other objects).</span></span> <span data-ttu-id="99675-171">只會複製最上層的值。</span><span class="sxs-lookup"><span data-stu-id="99675-171">Only the top-level values are copied.</span></span> <span data-ttu-id="99675-172">子物件仍會互相參考。</span><span class="sxs-lookup"><span data-stu-id="99675-172">The child objects will reference each other.</span></span>

### <a name="pstypename-for-custom-object-types"></a><span data-ttu-id="99675-173">自訂物件類型的 PSTypeName</span><span class="sxs-lookup"><span data-stu-id="99675-173">PSTypeName for custom object types</span></span>

<span data-ttu-id="99675-174">有了物件以後，我們可以對其進行幾項可能不是那麼明顯的操作。</span><span class="sxs-lookup"><span data-stu-id="99675-174">Now that we have an object, there are a few more things we can do with it that may not be nearly as obvious.</span></span> <span data-ttu-id="99675-175">首先需要為其提供一個 `PSTypeName`。</span><span class="sxs-lookup"><span data-stu-id="99675-175">First thing we need to do is give it a `PSTypeName`.</span></span> <span data-ttu-id="99675-176">這是我觀察到人們普遍採用的方法：</span><span class="sxs-lookup"><span data-stu-id="99675-176">This is the most common way I see people do it:</span></span>

```powershell
$myObject.PSObject.TypeNames.Insert(0,"My.Object")
```

<span data-ttu-id="99675-177">我最近從這篇 [post by /u/markekraus][]文章中發現到另外一種進行此操作的方法。</span><span class="sxs-lookup"><span data-stu-id="99675-177">I recently discovered another way to do this from this [post by /u/markekraus][].</span></span> <span data-ttu-id="99675-178">我進行了一些研究並閱讀了更多來自 [Adam Bertram][] 和 [Mike Shepard][] 與此概念有關的文章，其中討論到這種方法可以讓您以內嵌的方式進行定義。</span><span class="sxs-lookup"><span data-stu-id="99675-178">I did a little digging and more posts about the idea from [Adam Bertram][] and [Mike Shepard][] where they talk about this approach that allows you to define it inline.</span></span>

```powershell
$myObject = [PSCustomObject]@{
    PSTypeName = 'My.Object'
    Name       = 'Kevin'
    Language   = 'PowerShell'
    State      = 'Texas'
}
```

<span data-ttu-id="99675-179">我非常喜歡這種方法，因為這相當適用於程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="99675-179">I love how nicely this just fits into the language.</span></span> <span data-ttu-id="99675-180">現在我們有了具備適當類型名稱的物件，可以進行更多操作。</span><span class="sxs-lookup"><span data-stu-id="99675-180">Now that we have an object with a proper type name, we can do some more things.</span></span>

> [!NOTE]
> <span data-ttu-id="99675-181">您也可使用 PowerShell 類別建立自訂的 PowerShell 類型。</span><span class="sxs-lookup"><span data-stu-id="99675-181">You can also create custom PowerShell types using PowerShell classes.</span></span> <span data-ttu-id="99675-182">如需詳細資訊，請參閱 [PowerShell 類別概觀](/powershell/module/Microsoft.PowerShell.Core/About/about_Classes)。</span><span class="sxs-lookup"><span data-stu-id="99675-182">For more information, see [PowerShell Class Overview](/powershell/module/Microsoft.PowerShell.Core/About/about_Classes).</span></span>

## <a name="using-defaultpropertyset-the-long-way"></a><span data-ttu-id="99675-183">使用 DefaultPropertySet (較慢的方式)</span><span class="sxs-lookup"><span data-stu-id="99675-183">Using DefaultPropertySet (the long way)</span></span>

<span data-ttu-id="99675-184">根據預設，PowerShell 會為我們決定要顯示哪些屬性。</span><span class="sxs-lookup"><span data-stu-id="99675-184">PowerShell decides for us what properties to display by default.</span></span> <span data-ttu-id="99675-185">許多原生命令都包含了 `.ps1xml` [格式化檔案][]，可執行所有繁重的工作。</span><span class="sxs-lookup"><span data-stu-id="99675-185">A lot of the native commands have a `.ps1xml` [formatting file][] that does all the heavy lifting.</span></span> <span data-ttu-id="99675-186">從這篇 [Boe Prox 的文章][]中，有另外一種方式可以只使用 PowerShell 在自訂物件上進行此操作。</span><span class="sxs-lookup"><span data-stu-id="99675-186">From this [post by Boe Prox][], there's another way for us to do this on our custom object using just PowerShell.</span></span> <span data-ttu-id="99675-187">我們可以為其提供 `MemberSet` 以供其使用。</span><span class="sxs-lookup"><span data-stu-id="99675-187">We can give it a `MemberSet` for it to use.</span></span>

```powershell
$defaultDisplaySet = 'Name','Language'
$defaultDisplayPropertySet = New-Object System.Management.Automation.PSPropertySet('DefaultDisplayPropertySet',[string[]]$defaultDisplaySet)
$PSStandardMembers = [System.Management.Automation.PSMemberInfo[]]@($defaultDisplayPropertySet)
$MyObject | Add-Member MemberSet PSStandardMembers $PSStandardMembers
```

<span data-ttu-id="99675-188">現在當物件進入殼層中時，根據預設只會顯示這些屬性。</span><span class="sxs-lookup"><span data-stu-id="99675-188">Now when my object just falls to the shell, it will only show those properties by default.</span></span>

### <a name="update-typedata-with-defaultpropertyset"></a><span data-ttu-id="99675-189">搭配 DefaultPropertySet 使用 Update-TypeData</span><span class="sxs-lookup"><span data-stu-id="99675-189">Update-TypeData with DefaultPropertySet</span></span>

<span data-ttu-id="99675-190">這很不錯，但是我最近在觀看 [PowerShell unplugged 2016 with Jeffrey Snover & Don Jones][psunplugged] (Jeffrey Snover 和 Don Jones 的 PowerShell 不插電 2016) 時，發現還有更好的方式。</span><span class="sxs-lookup"><span data-stu-id="99675-190">This is nice but I recently saw a better way when watching [PowerShell unplugged 2016 with Jeffrey Snover & Don Jones][psunplugged].</span></span> <span data-ttu-id="99675-191">Jeffrey 使用 [Update-TypeData][] 來指定預設屬性。</span><span class="sxs-lookup"><span data-stu-id="99675-191">Jeffrey was using [Update-TypeData][] to specify the default properties.</span></span>

```powershell
$TypeData = @{
    TypeName = 'My.Object'
    DefaultDisplayPropertySet = 'Name','Language'
}
Update-TypeData @TypeData
```

<span data-ttu-id="99675-192">這相當簡單，甚至如果我沒有這篇文章作為快速參考，我幾乎仍然可以記得。</span><span class="sxs-lookup"><span data-stu-id="99675-192">That is simple enough that I could almost remember it if I didn't have this post as a quick reference.</span></span> <span data-ttu-id="99675-193">現在我可以輕鬆地建立包含許多屬性的物件，並讓其在殼層中以相當簡潔的方式提供檢視。</span><span class="sxs-lookup"><span data-stu-id="99675-193">Now I can easily create objects with lots of properties and still give it a nice clean view when looking at it from the shell.</span></span> <span data-ttu-id="99675-194">若我需要存取或查看其他屬性，這些屬性仍會在其位置。</span><span class="sxs-lookup"><span data-stu-id="99675-194">If I need to access or see those other properties, they're still there.</span></span>

```powershell
$myObject | Format-List *
```

### <a name="update-typedata-with-scriptproperty"></a><span data-ttu-id="99675-195">搭配 ScriptProperty 使用 Update-TypeData</span><span class="sxs-lookup"><span data-stu-id="99675-195">Update-TypeData with ScriptProperty</span></span>

<span data-ttu-id="99675-196">我從該影片得知的另外一件事是為物件建立指令碼屬性。</span><span class="sxs-lookup"><span data-stu-id="99675-196">Something else I got out of that video was creating script properties for your objects.</span></span> <span data-ttu-id="99675-197">這也是指出這項操作適用於現有物件的良好時機。</span><span class="sxs-lookup"><span data-stu-id="99675-197">This would be a good time to point out that this works for existing objects too.</span></span>

```powershell
$TypeData = @{
    TypeName = 'My.Object'
    MemberType = 'ScriptProperty'
    MemberName = 'UpperCaseName'
    Value = {$this.Name.toUpper()}
}
Update-TypeData @TypeData
```

<span data-ttu-id="99675-198">您可以在建立物件前，或是建立物件之後進行這項操作，而其仍然會正常運作。</span><span class="sxs-lookup"><span data-stu-id="99675-198">You can do this before your object is created or after and it will still work.</span></span> <span data-ttu-id="99675-199">這正是與前述搭配指令碼屬性使用 `Add-Member` 的不同之處。</span><span class="sxs-lookup"><span data-stu-id="99675-199">This is what makes this different then using `Add-Member` with a script property.</span></span> <span data-ttu-id="99675-200">當您按照我先前參考的方式使用 `Add-Member`，其只會存在於物件的特定執行個體。</span><span class="sxs-lookup"><span data-stu-id="99675-200">When you use `Add-Member` the way I referenced earlier, it only exists on that specific instance of the object.</span></span> <span data-ttu-id="99675-201">但這項操作適用於所有使用此 `TypeName` 的物件。</span><span class="sxs-lookup"><span data-stu-id="99675-201">This one applies to all objects with this `TypeName`.</span></span>

## <a name="function-parameters"></a><span data-ttu-id="99675-202">函數參數</span><span class="sxs-lookup"><span data-stu-id="99675-202">Function parameters</span></span>

<span data-ttu-id="99675-203">您現在可以在函數和指令碼中使用這些參數的自訂類型。</span><span class="sxs-lookup"><span data-stu-id="99675-203">You can now use these custom types for parameters in your functions and scripts.</span></span> <span data-ttu-id="99675-204">您可以讓其中一個函數建立這些自訂物件，然後將這些物件傳遞至其他函數。</span><span class="sxs-lookup"><span data-stu-id="99675-204">You can have one function create these custom objects and then pass them into other functions.</span></span>

```powershell
param( [PSTypeName('My.Object')]$Data )
```

<span data-ttu-id="99675-205">PowerShell 會要求物件必須是您所指定的類型。</span><span class="sxs-lookup"><span data-stu-id="99675-205">PowerShell requires that the object is the type you specified.</span></span> <span data-ttu-id="99675-206">當類型無法自動比對時，便會擲回驗證錯誤，為您省下在程式碼中對其進行測試的步驟。</span><span class="sxs-lookup"><span data-stu-id="99675-206">It throws a validation error if the type doesn't match automatically to save you the step of testing for it in your code.</span></span> <span data-ttu-id="99675-207">讓 PowerShell 達到最佳效果的絕佳範例。</span><span class="sxs-lookup"><span data-stu-id="99675-207">A great example of letting PowerShell do what it does best.</span></span>

### <a name="function-outputtype"></a><span data-ttu-id="99675-208">函數 OutputType</span><span class="sxs-lookup"><span data-stu-id="99675-208">Function OutputType</span></span>

<span data-ttu-id="99675-209">您也可以為進階函數定義 `OutputType`。</span><span class="sxs-lookup"><span data-stu-id="99675-209">You can also define an `OutputType` for your advanced functions.</span></span>

```powershell
function Get-MyObject
{
    [OutputType('My.Object')]
    [CmdletBinding()]
        param
        (
            ...
```

<span data-ttu-id="99675-210">**OutputType** 屬性值只是文件備註。</span><span class="sxs-lookup"><span data-stu-id="99675-210">The **OutputType** attribute value is only a documentation note.</span></span> <span data-ttu-id="99675-211">其並非衍生自函數程式碼或與實際的函數輸出比較。</span><span class="sxs-lookup"><span data-stu-id="99675-211">It isn't derived from the function code or compared to the actual function output.</span></span>

<span data-ttu-id="99675-212">使用輸出類型旨在讓函數的中繼資訊反映您的意圖。</span><span class="sxs-lookup"><span data-stu-id="99675-212">The main reason you would use an output type is so that meta information about your function reflects your intentions.</span></span> <span data-ttu-id="99675-213">像是 `Get-Command` 和 `Get-Help` 等可供您開發環境利用的項目。</span><span class="sxs-lookup"><span data-stu-id="99675-213">Things like `Get-Command` and `Get-Help` that your development environment can take advantage of.</span></span> <span data-ttu-id="99675-214">如需詳細資訊，請查看其說明：[about_Functions_OutputTypeAttribute][]。</span><span class="sxs-lookup"><span data-stu-id="99675-214">If you want more information, then take a look at the help for it: [about_Functions_OutputTypeAttribute][].</span></span>

<span data-ttu-id="99675-215">換句話說，若您使用 Pester 對函數進行單元測試，確保輸出物件與您的 **OutputType** 相符便是個不錯的做法。</span><span class="sxs-lookup"><span data-stu-id="99675-215">With that said, if you're using Pester to unit test your functions then it would be a good idea to validate the output objects match your **OutputType**.</span></span> <span data-ttu-id="99675-216">這可以擷取不應進入管道卻進入管道的變數。</span><span class="sxs-lookup"><span data-stu-id="99675-216">This could catch variables that just fall to the pipe when they shouldn't.</span></span>

## <a name="closing-thoughts"></a><span data-ttu-id="99675-217">結論</span><span class="sxs-lookup"><span data-stu-id="99675-217">Closing thoughts</span></span>

<span data-ttu-id="99675-218">本文的內容主要與 `[PSCustomObject]` 有關，但其中許多資訊都適用於一般的物件。</span><span class="sxs-lookup"><span data-stu-id="99675-218">The context of this was all about `[PSCustomObject]`, but a lot of this information applies to objects in general.</span></span>

<span data-ttu-id="99675-219">我以前曾經看過這些大部分的功能，但從未見過將這些資訊集中以展示 `PSCustomObject` 的功能。</span><span class="sxs-lookup"><span data-stu-id="99675-219">I have seen most of these features in passing before but never saw them presented as a collection of information on `PSCustomObject`.</span></span> <span data-ttu-id="99675-220">就在上一週我偶然發現另外一種做法，而我相當驚訝先前從未見過這種做法。</span><span class="sxs-lookup"><span data-stu-id="99675-220">Just this last week I stumbled upon another one and was surprised that I had not seen it before.</span></span> <span data-ttu-id="99675-221">我想要將這些概念集中在一起，讓您有機會以更宏觀的方式來檢視，並在您有機會使用這些功能時知道這些功能存在。</span><span class="sxs-lookup"><span data-stu-id="99675-221">I wanted to pull all these ideas together so you can hopefully see the bigger picture and be aware of them when you have an opportunity to use them.</span></span> <span data-ttu-id="99675-222">我希望您可以了解到一些資訊，並找到將這些資訊融入您指令碼的方式。</span><span class="sxs-lookup"><span data-stu-id="99675-222">I hope you learned something and can find a way to work this into your scripts.</span></span>

<!-- link references -->
[原始版本]: https://powershellexplained.com/2016-10-28-powershell-everything-you-wanted-to-know-about-pscustomobject/
[original version]: https://powershellexplained.com/2016-10-28-powershell-everything-you-wanted-to-know-about-pscustomobject/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Boe Prox 的文章]: https://learn-PowerShell.net/2013/08/03/quick-hits-set-the-default-property-display-in-PowerShell-on-custom-objects/
[post by Boe Prox]: https://learn-PowerShell.net/2013/08/03/quick-hits-set-the-default-property-display-in-PowerShell-on-custom-objects/
[格式化檔案]: https://mcpmag.com/articles/2014/05/13/PowerShell-properties-part-3.aspx
[formatting file]: https://mcpmag.com/articles/2014/05/13/PowerShell-properties-part-3.aspx
[about_Functions_OutputTypeAttribute]: /powershell/module/microsoft.powershell.core/about/about_functions_outputtypeattribute
[讀取和寫入檔案的許多方式]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files
[The many ways to read and write to files]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files
[post by /u/markekraus]: https://www.reddit.com/r/PowerShell/comments/590awc/is_it_possible_to_initialize_a_pscustoobject_with/
[Adam Bertram]: http://www.adamtheautomator.com/building-custom-object-types-PowerShell-pstypename/
[Mike Shepard]: https://powershellstation.com/2016/05/22/custom-objects-and-pstypename/
[psunplugged]: https://www.youtube.com/watch?v=Ab46gHXNm8Q
[Update-TypeData]: /powershell/module/microsoft.powershell.utility/update-typedata
