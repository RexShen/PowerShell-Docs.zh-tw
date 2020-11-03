---
description: 描述可搭配 Microsoft .NET 類型使用的運算子。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/15/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_type_operators?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Type_Operators
ms.openlocfilehash: 6ea2ef2f61636d67a8bacf69ff577f477712a165
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208443"
---
# <a name="about-type-operators"></a><span data-ttu-id="8116b-104">關於類型運算子</span><span class="sxs-lookup"><span data-stu-id="8116b-104">About Type Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="8116b-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="8116b-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="8116b-106">描述可搭配 Microsoft .NET 類型使用的運算子。</span><span class="sxs-lookup"><span data-stu-id="8116b-106">Describes the operators that work with Microsoft .NET types.</span></span>

## <a name="long-description"></a><span data-ttu-id="8116b-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="8116b-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="8116b-108">布林型別運算子 `-is` 會 (， `-isNot`) 判斷物件是否為指定之 .net 型別的實例。</span><span class="sxs-lookup"><span data-stu-id="8116b-108">The Boolean type operators (`-is` and `-isNot`) tell whether an object is an instance of a specified .NET type.</span></span> <span data-ttu-id="8116b-109">`-is`如果類型相符，運算子會傳回 **TRUE** 值，否則會傳回 **FALSE** 值。</span><span class="sxs-lookup"><span data-stu-id="8116b-109">The `-is` operator returns a value of **TRUE** if the type matches and a value of **FALSE** otherwise.</span></span> <span data-ttu-id="8116b-110">`-isNot`如果類型相符，運算子會傳回 **FALSE** 的值，否則會傳回 **TRUE** 值。</span><span class="sxs-lookup"><span data-stu-id="8116b-110">The `-isNot` operator returns a value of **FALSE** if the type matches and a value of **TRUE** otherwise.</span></span>

<span data-ttu-id="8116b-111">`-as`運算子會嘗試將輸入物件轉換成指定的 .net 型別。</span><span class="sxs-lookup"><span data-stu-id="8116b-111">The `-as` operator tries to convert the input object to the specified .NET type.</span></span> <span data-ttu-id="8116b-112">如果成功，它會傳回已轉換的物件。</span><span class="sxs-lookup"><span data-stu-id="8116b-112">If it succeeds, it returns the converted object.</span></span> <span data-ttu-id="8116b-113">如果失敗，則會傳回 `$null`。</span><span class="sxs-lookup"><span data-stu-id="8116b-113">If it fails, it returns `$null`.</span></span> <span data-ttu-id="8116b-114">它不會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="8116b-114">It does not return an error.</span></span>

<span data-ttu-id="8116b-115">下表列出 PowerShell 中的型別運算子。</span><span class="sxs-lookup"><span data-stu-id="8116b-115">The following table lists the type operators in PowerShell.</span></span>

|<span data-ttu-id="8116b-116">運算子</span><span class="sxs-lookup"><span data-stu-id="8116b-116">Operator</span></span>|<span data-ttu-id="8116b-117">描述</span><span class="sxs-lookup"><span data-stu-id="8116b-117">Description</span></span>                |<span data-ttu-id="8116b-118">範例</span><span class="sxs-lookup"><span data-stu-id="8116b-118">Example</span></span>                          |
|--------|---------------------------|---------------------------------|
|`-is`   |<span data-ttu-id="8116b-119">當輸入時傳回 TRUE</span><span class="sxs-lookup"><span data-stu-id="8116b-119">Returns TRUE when the input</span></span>|`(get-date) -is [DateTime]`      |
|        |<span data-ttu-id="8116b-120">是的實例。</span><span class="sxs-lookup"><span data-stu-id="8116b-120">is an instance of the</span></span>      |`True`                           |
|        |<span data-ttu-id="8116b-121">指定的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="8116b-121">specified .NET type.</span></span>       |                                 |
|`-isNot`|<span data-ttu-id="8116b-122">當輸入時傳回 TRUE</span><span class="sxs-lookup"><span data-stu-id="8116b-122">Returns TRUE when the input</span></span>|`(get-date) -isNot [DateTime]`   |
|        |<span data-ttu-id="8116b-123">不是的實例。</span><span class="sxs-lookup"><span data-stu-id="8116b-123">not an instance of the</span></span>     |`False`                          |
|        |<span data-ttu-id="8116b-124">specified.NET 類型。</span><span class="sxs-lookup"><span data-stu-id="8116b-124">specified.NET type.</span></span>        |                                 |
|`-as`   |<span data-ttu-id="8116b-125">將輸入轉換為</span><span class="sxs-lookup"><span data-stu-id="8116b-125">Converts the input to the</span></span>  |`"5/7/07" -as [DateTime]`        |
|        |<span data-ttu-id="8116b-126">指定的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="8116b-126">specified .NET type.</span></span>       |`Monday, May 7, 2007 12:00:00 AM`|

<span data-ttu-id="8116b-127">型別運算子的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="8116b-127">The syntax of the type operators is as follows:</span></span>

```powershell
<input> <operator> [.NET type]
```

<span data-ttu-id="8116b-128">您也可以使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="8116b-128">You can also use the following syntax:</span></span>

```powershell
<input> <operator> ".NET type"
```

<span data-ttu-id="8116b-129">.NET 類型可以用方括弧或字串的形式（例如或 system.string）撰寫為類型名稱 `[DateTime]` `"DateTime"` 。 **System.DateTime**</span><span class="sxs-lookup"><span data-stu-id="8116b-129">The .NET type can be written as a type name in brackets or a string, such as `[DateTime]` or `"DateTime"` for **System.DateTime** .</span></span> <span data-ttu-id="8116b-130">如果類型不在 system 命名空間的根目錄中，請指定物件類型的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="8116b-130">If the type is not at the root of the system namespace, specify the full name of the object type.</span></span> <span data-ttu-id="8116b-131">您可以省略 "System."。</span><span class="sxs-lookup"><span data-stu-id="8116b-131">You can omit "System.".</span></span> <span data-ttu-id="8116b-132">例如，若要指定 **system.object** ，請輸入 `[System.Diagnostics.Process]` 、 `[Diagnostics.Process]` 或 `"Diagnostics.Process"` 。</span><span class="sxs-lookup"><span data-stu-id="8116b-132">For example, to specify **System.Diagnostics.Process** , enter `[System.Diagnostics.Process]`, `[Diagnostics.Process]`, or `"Diagnostics.Process"`.</span></span>

<span data-ttu-id="8116b-133">型別運算子一律會以整體的形式在輸入物件上運作。</span><span class="sxs-lookup"><span data-stu-id="8116b-133">The type operators always operate on the input object as a whole.</span></span> <span data-ttu-id="8116b-134">也就是說，如果輸入物件是集合，它就是經過測試的 _集合_ 型別，而不是集合的 _元素_ 類型。</span><span class="sxs-lookup"><span data-stu-id="8116b-134">That is, if the input object is a collection, it is the _collection_ type that is tested, not the types of the collection's _elements_ .</span></span>

### <a name="-isisnot-operators"></a><span data-ttu-id="8116b-135">-是/isNot 運算子</span><span class="sxs-lookup"><span data-stu-id="8116b-135">-is/isNot operators</span></span>

<span data-ttu-id="8116b-136">**布林** 型別運算子 (`-is` 和 `-isNot`) 一律會傳回 **布林** 值，即使輸入是物件的集合也一樣。</span><span class="sxs-lookup"><span data-stu-id="8116b-136">The **Boolean** type operators (`-is` and `-isNot`) always return a **Boolean** value, even if the input is a collection of objects.</span></span>

<span data-ttu-id="8116b-137">如果的型別與 `<input>` 或 _衍生_ 自 .net 型別，則運算子會傳回 `-is` `$True` 。</span><span class="sxs-lookup"><span data-stu-id="8116b-137">If `<input>` is a type that is the same as or is _derived_ from the .NET Type, the `-is` operator returns `$True`.</span></span>

<span data-ttu-id="8116b-138">例如， **DirectoryInfo** 型別衍生自 **FileSystemInfo** 型別。</span><span class="sxs-lookup"><span data-stu-id="8116b-138">For example, the **DirectoryInfo** type is derived from the **FileSystemInfo** type.</span></span> <span data-ttu-id="8116b-139">因此，這兩個範例都會傳回 **True** 。</span><span class="sxs-lookup"><span data-stu-id="8116b-139">Therefore, both of these examples return **True** .</span></span>

```powershell
PS> (Get-Item /) -is [System.IO.DirectoryInfo]
True
PS> (Get-Item /) -is [System.IO.FileSystemInfo]
True
```

<span data-ttu-id="8116b-140">`-is`如果在比較中實作為介面，運算子也可以符合介面 `<input>` 。</span><span class="sxs-lookup"><span data-stu-id="8116b-140">The `-is` operator can also match interfaces if the `<input>` implements the interface in the comparison.</span></span> <span data-ttu-id="8116b-141">在此範例中，輸入是陣列。</span><span class="sxs-lookup"><span data-stu-id="8116b-141">In this example, the input is an array.</span></span> <span data-ttu-id="8116b-142">陣列會執行 **system.object** 介面。</span><span class="sxs-lookup"><span data-stu-id="8116b-142">Arrays implement the **System.Collections.IList** interface.</span></span>

```powershell
PS> 1, 2 -is [System.Collections.IList]
True
```

### <a name="-as-operator"></a><span data-ttu-id="8116b-143">-as 運算子</span><span class="sxs-lookup"><span data-stu-id="8116b-143">-as operator</span></span>

<span data-ttu-id="8116b-144">`-as`運算子會嘗試將輸入物件轉換成指定的 .net 型別。</span><span class="sxs-lookup"><span data-stu-id="8116b-144">The `-as` operator tries to convert the input object to the specified .NET type.</span></span> <span data-ttu-id="8116b-145">如果成功，它會傳回已轉換的物件。</span><span class="sxs-lookup"><span data-stu-id="8116b-145">If it succeeds, it returns the converted object.</span></span> <span data-ttu-id="8116b-146">如果失敗，則會傳回 `$null` 。</span><span class="sxs-lookup"><span data-stu-id="8116b-146">It if fails, it returns `$null`.</span></span> <span data-ttu-id="8116b-147">它不會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="8116b-147">It does not return an error.</span></span>

<span data-ttu-id="8116b-148">如果 `<input>` 是 _衍生_ 自 .net 型別的型別，則會 `-as` _傳回_ 未變更的輸入物件。</span><span class="sxs-lookup"><span data-stu-id="8116b-148">If the `<input>` is a type that is _derived_ from the .NET Type `-as` _passes through_ returns input object unchanged.</span></span> <span data-ttu-id="8116b-149">例如， **DirectoryInfo** 型別衍生自 **FileSystemInfo** 型別。</span><span class="sxs-lookup"><span data-stu-id="8116b-149">For example, the **DirectoryInfo** type is derived from the **FileSystemInfo** type.</span></span> <span data-ttu-id="8116b-150">因此，在下列範例中，物件類型會保持不變：</span><span class="sxs-lookup"><span data-stu-id="8116b-150">Therefore, the object type is unchanged in the following example:</span></span>

```powershell
PS> $fsroot = (Get-Item /) -as [System.IO.FileSystemInfo]
PS> $fsroot.GetType().FullName
System.IO.DirectoryInfo
```

#### <a name="converting-the-datetime-type-is-culture-sensitive"></a><span data-ttu-id="8116b-151">轉換 DateTime 類型會區分文化特性</span><span class="sxs-lookup"><span data-stu-id="8116b-151">Converting the DateTime type is culture-sensitive</span></span>

<span data-ttu-id="8116b-152">不同于型別轉換， `[DateTime]` 使用運算子轉換成型別 `-as` 只適用于根據目前文化特性的規則格式化的字串。</span><span class="sxs-lookup"><span data-stu-id="8116b-152">Unlike type casting, converting to `[DateTime]` type using the `-as` operator only works with strings that are formatted according to the rules of the current culture.</span></span>

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr-FR'
PS> '13/5/20' -as [datetime]

mercredi 13 mai 2020 00:00:00

PS> '05/13/20' -as [datetime]
PS> [datetime]'05/13/20'

mercredi 13 mai 2020 00:00:00

PS> [datetime]'13/05/20'
InvalidArgument: Cannot convert value "13/05/20" to type "System.DateTime".
Error: "String '13/05/20' was not recognized as a valid DateTime."
```

<span data-ttu-id="8116b-153">若要尋找物件的 .NET 類型，請使用 `Get-Member` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8116b-153">To find the .NET type of an object, use the `Get-Member` cmdlet.</span></span> <span data-ttu-id="8116b-154">或者，將所有物件的 **GetType** 方法與這個方法的 **FullName** 屬性一起使用。</span><span class="sxs-lookup"><span data-stu-id="8116b-154">Or, use the **GetType** method of all the objects together with the **FullName** property of this method.</span></span> <span data-ttu-id="8116b-155">例如，下列語句會取得命令的傳回數值型別 `Get-Culture` ：</span><span class="sxs-lookup"><span data-stu-id="8116b-155">For example, the following statement gets the type of the return value of a `Get-Culture` command:</span></span>

```powershell
PS> (Get-Culture).GetType().FullName
System.Globalization.CultureInfo
```

## <a name="examples"></a><span data-ttu-id="8116b-156">範例</span><span class="sxs-lookup"><span data-stu-id="8116b-156">EXAMPLES</span></span>

<span data-ttu-id="8116b-157">下列範例示範型別運算子的一些用法：</span><span class="sxs-lookup"><span data-stu-id="8116b-157">The following examples show some uses of the Type operators:</span></span>

```powershell
PS> 32 -is [Float]
False

PS> 32 -is "int"
True

PS> (get-date) -is [DateTime]
True

PS> "12/31/2007" -is [DateTime]
False

PS> "12/31/2007" -is [String]
True

PS> (get-process PowerShell)[0] -is [System.Diagnostics.Process]
True

PS> (get-command get-member) -is [System.Management.Automation.CmdletInfo]
True
```

<span data-ttu-id="8116b-158">下列範例顯示當輸入是物件的集合時，相符的型別是集合的 .NET 型別，而不是集合中個別物件的型別。</span><span class="sxs-lookup"><span data-stu-id="8116b-158">The following example shows that when the input is a collection of objects, the matching type is the .NET type of the collection, not the type of the individual objects in the collection.</span></span>

<span data-ttu-id="8116b-159">在此範例中，雖然和 Cmdlet 都會傳回 system.string `Get-Culture` `Get-UICulture` 物件，但這些物件的集合是 system.object 陣列。 **System.Globalization.CultureInfo**</span><span class="sxs-lookup"><span data-stu-id="8116b-159">In this example, although both the `Get-Culture` and `Get-UICulture` cmdlets return **System.Globalization.CultureInfo** objects, a collection of these objects is a System.Object array.</span></span>

```powershell
PS> (get-culture) -is [System.Globalization.CultureInfo]
True

PS> (get-uiculture) -is [System.Globalization.CultureInfo]
True

PS> (get-culture), (get-uiculture) -is [System.Globalization.CultureInfo]
False

PS> (get-culture), (get-uiculture) -is [Array]
True

PS> (get-culture), (get-uiculture) | foreach {
  $_ -is [System.Globalization.CultureInfo])
}
True
True

PS> (get-culture), (get-uiculture) -is [Object]
True
```

<span data-ttu-id="8116b-160">下列範例示範如何使用 `-as` 運算子。</span><span class="sxs-lookup"><span data-stu-id="8116b-160">The following examples show how to use the `-as` operator.</span></span>

```powershell
PS> "12/31/07" -is [DateTime]
False

PS> "12/31/07" -as [DateTime]
Monday, December 31, 2007 12:00:00 AM

PS> $date = "12/31/07" -as [DateTime]

C:\PS>$a -is [DateTime]
True

PS> 1031 -as [System.Globalization.CultureInfo]

LCID      Name      DisplayName
----      ----      -----------
1031      de-DE     German (Germany)
```

<span data-ttu-id="8116b-161">下列範例顯示當 `-as` 運算子無法將輸入物件轉換成 .net 型別時，它會傳回 `$null` 。</span><span class="sxs-lookup"><span data-stu-id="8116b-161">The following example shows that when the `-as` operator cannot convert the input object to the .NET type, it returns `$null`.</span></span>

```powershell
PS> 1031 -as [System.Diagnostics.Process]
PS>
```

## <a name="see-also"></a><span data-ttu-id="8116b-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8116b-162">SEE ALSO</span></span>

[<span data-ttu-id="8116b-163">about_Operators</span><span class="sxs-lookup"><span data-stu-id="8116b-163">about_Operators</span></span>](about_Operators.md)
