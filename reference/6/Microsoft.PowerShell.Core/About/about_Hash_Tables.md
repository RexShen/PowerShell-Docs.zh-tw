---
description: 描述如何在 PowerShell 中建立、使用和排序雜湊表。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/28/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_hash_tables?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Hash_Tables
ms.openlocfilehash: ecc4cbb02522766b04414c30c65d4d6acde3bb8a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207072"
---
# <a name="about-hash-tables"></a><span data-ttu-id="751a6-104">關於雜湊表</span><span class="sxs-lookup"><span data-stu-id="751a6-104">About Hash Tables</span></span>

## <a name="short-description"></a><span data-ttu-id="751a6-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="751a6-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="751a6-106">描述如何在 PowerShell 中建立、使用和排序雜湊表。</span><span class="sxs-lookup"><span data-stu-id="751a6-106">Describes how to create, use, and sort hash tables in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="751a6-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="751a6-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="751a6-108">雜湊表（又稱為字典或關聯陣列）是一種精簡的資料結構，它會儲存一或多個索引鍵/值組。</span><span class="sxs-lookup"><span data-stu-id="751a6-108">A hash table, also known as a dictionary or associative array, is a compact data structure that stores one or more key/value pairs.</span></span> <span data-ttu-id="751a6-109">例如，雜湊表可能包含一連串的 IP 位址和電腦名稱稱，其中 IP 位址是金鑰，而電腦名稱稱則是值，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="751a6-109">For example, a hash table might contain a series of IP addresses and computer names, where the IP addresses are the keys and the computer names are the values, or vice versa.</span></span>

<span data-ttu-id="751a6-110">在 PowerShell 中，每個雜湊表都是雜湊表 (System.object) 物件。</span><span class="sxs-lookup"><span data-stu-id="751a6-110">In PowerShell, each hash table is a Hashtable (System.Collections.Hashtable) object.</span></span> <span data-ttu-id="751a6-111">您可以在 PowerShell 中使用雜湊表物件的屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="751a6-111">You can use the properties and methods of Hashtable objects in PowerShell.</span></span>

<span data-ttu-id="751a6-112">從 PowerShell 3.0 開始，您可以使用 [已排序] 屬性，在 PowerShell 中 (OrderedDictionary) 建立已排序的字典。</span><span class="sxs-lookup"><span data-stu-id="751a6-112">Beginning in PowerShell 3.0, you can use the [ordered] attribute to create an ordered dictionary (System.Collections.Specialized.OrderedDictionary) in PowerShell.</span></span>

<span data-ttu-id="751a6-113">排序的字典與雜湊表不同之處在于，索引鍵一律會依列出的順序出現。</span><span class="sxs-lookup"><span data-stu-id="751a6-113">Ordered dictionaries differ from hash tables in that the keys always appear in the order in which you list them.</span></span> <span data-ttu-id="751a6-114">未判斷雜湊表中的索引鍵順序。</span><span class="sxs-lookup"><span data-stu-id="751a6-114">The order of keys in a hash table is not determined.</span></span>

<span data-ttu-id="751a6-115">雜湊表中的索引鍵和值也是 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="751a6-115">The keys and value in hash tables are also .NET objects.</span></span> <span data-ttu-id="751a6-116">它們最常是字串或整數，但可以有任何物件類型。</span><span class="sxs-lookup"><span data-stu-id="751a6-116">They are most often strings or integers, but they can have any object type.</span></span> <span data-ttu-id="751a6-117">您也可以建立嵌套雜湊表，其中索引鍵的值是另一個雜湊表。</span><span class="sxs-lookup"><span data-stu-id="751a6-117">You can also create nested hash tables, in which the value of a key is another hash table.</span></span>

<span data-ttu-id="751a6-118">雜湊資料表經常會使用，因為它們對於尋找和取出資料非常有效率。</span><span class="sxs-lookup"><span data-stu-id="751a6-118">Hash tables are frequently used because they are very efficient for finding and retrieving data.</span></span> <span data-ttu-id="751a6-119">您可以使用雜湊表來儲存清單，並在 PowerShell 中建立計算屬性。</span><span class="sxs-lookup"><span data-stu-id="751a6-119">You can use hash tables to store lists and to create calculated properties in PowerShell.</span></span> <span data-ttu-id="751a6-120">而且，PowerShell 有一個 Cmdlet Convertfrom-string-至 convertfrom-stringdata，可將字串轉換成雜湊表。</span><span class="sxs-lookup"><span data-stu-id="751a6-120">And, PowerShell has a cmdlet, ConvertFrom-StringData, that converts strings to a hash table.</span></span>

### <a name="syntax"></a><span data-ttu-id="751a6-121">Syntax</span><span class="sxs-lookup"><span data-stu-id="751a6-121">Syntax</span></span>

<span data-ttu-id="751a6-122">雜湊表的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="751a6-122">The syntax of a hash table is as follows:</span></span>

```powershell
@{ <name> = <value>; [<name> = <value> ] ...}
```

<span data-ttu-id="751a6-123">已排序字典的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="751a6-123">The syntax of an ordered dictionary is as follows:</span></span>

```powershell
[ordered]@{ <name> = <value>; [<name> = <value> ] ...}
```

<span data-ttu-id="751a6-124">[已排序] 屬性是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="751a6-124">The [ordered] attribute was introduced in PowerShell 3.0.</span></span>

### <a name="creating-hash-tables"></a><span data-ttu-id="751a6-125">建立雜湊表</span><span class="sxs-lookup"><span data-stu-id="751a6-125">Creating Hash Tables</span></span>

<span data-ttu-id="751a6-126">若要建立雜湊表，請遵循下列指導方針：</span><span class="sxs-lookup"><span data-stu-id="751a6-126">To create a hash table, follow these guidelines:</span></span>

- <span data-ttu-id="751a6-127">使用 at sign ( @ ) 來開始雜湊表。</span><span class="sxs-lookup"><span data-stu-id="751a6-127">Begin the hash table with an at sign (@).</span></span>
- <span data-ttu-id="751a6-128">以大括弧括住雜湊表 ({}) 。</span><span class="sxs-lookup"><span data-stu-id="751a6-128">Enclose the hash table in braces ({}).</span></span>
- <span data-ttu-id="751a6-129">針對雜湊表的內容輸入一或多個索引鍵/值組。</span><span class="sxs-lookup"><span data-stu-id="751a6-129">Enter one or more key/value pairs for the content of the hash table.</span></span>
- <span data-ttu-id="751a6-130">使用等號 (=) ，將每個索引鍵與其值分隔開來。</span><span class="sxs-lookup"><span data-stu-id="751a6-130">Use an equal sign (=) to separate each key from its value.</span></span>
- <span data-ttu-id="751a6-131">使用分號 (; ) 或分行符號來分隔索引鍵/值組。</span><span class="sxs-lookup"><span data-stu-id="751a6-131">Use a semicolon (;) or a line break to separate the key/value pairs.</span></span>
- <span data-ttu-id="751a6-132">包含空格的索引鍵必須以引號括住。</span><span class="sxs-lookup"><span data-stu-id="751a6-132">Key that contains spaces must be enclosed in quotation marks.</span></span> <span data-ttu-id="751a6-133">值必須是有效的 PowerShell 運算式。</span><span class="sxs-lookup"><span data-stu-id="751a6-133">Values must be valid PowerShell expressions.</span></span> <span data-ttu-id="751a6-134">字串必須以引號出現，即使它們不包含空格。</span><span class="sxs-lookup"><span data-stu-id="751a6-134">Strings must appear in quotation marks, even if they do not include spaces.</span></span>
- <span data-ttu-id="751a6-135">若要管理雜湊表，請將它儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="751a6-135">To manage the hash table, save it in a variable.</span></span>
- <span data-ttu-id="751a6-136">將已排序的雜湊表指派給變數時，請將 [已排序] 屬性放在 "@" 符號前面。</span><span class="sxs-lookup"><span data-stu-id="751a6-136">When assigning an ordered hash table to a variable, place the [ordered] attribute before the "@" symbol.</span></span> <span data-ttu-id="751a6-137">如果您將它放在變數名稱之前，命令就會失敗。</span><span class="sxs-lookup"><span data-stu-id="751a6-137">If you place it before the variable name, the command fails.</span></span>

<span data-ttu-id="751a6-138">若要在 $hash 的值中建立空白雜湊表，請輸入：</span><span class="sxs-lookup"><span data-stu-id="751a6-138">To create an empty hash table in the value of $hash, type:</span></span>

```powershell
$hash = @{}
```

<span data-ttu-id="751a6-139">您也可以在建立索引鍵和值時，將索引鍵和值加入至雜湊表。</span><span class="sxs-lookup"><span data-stu-id="751a6-139">You can also add keys and values to a hash table when you create it.</span></span> <span data-ttu-id="751a6-140">例如，下列語句會建立含有三個索引鍵的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="751a6-140">For example, the following statement creates a hash table with three keys.</span></span>

```powershell
$hash = @{ Number = 1; Shape = "Square"; Color = "Blue"}
```

### <a name="creating-ordered-dictionaries"></a><span data-ttu-id="751a6-141">建立已排序的字典</span><span class="sxs-lookup"><span data-stu-id="751a6-141">Creating Ordered Dictionaries</span></span>

<span data-ttu-id="751a6-142">您可以藉由加入 OrderedDictionary 類型的物件來建立已排序的字典，但建立已排序字典最簡單的方式是使用 [已排序] 屬性。</span><span class="sxs-lookup"><span data-stu-id="751a6-142">You can create an ordered dictionary by adding an object of the OrderedDictionary type, but the easiest way to create an ordered dictionary is use the [Ordered] attribute.</span></span>

<span data-ttu-id="751a6-143">[已排序] 屬性是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="751a6-143">The [ordered] attribute is introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="751a6-144">將屬性緊接在 "@" 符號前面。</span><span class="sxs-lookup"><span data-stu-id="751a6-144">Place the attribute immediately before the "@" symbol.</span></span>

```powershell
$hash = [ordered]@{ Number = 1; Shape = "Square"; Color = "Blue"}
```

<span data-ttu-id="751a6-145">您可以使用與雜湊資料表相同的方式來使用已排序的字典。</span><span class="sxs-lookup"><span data-stu-id="751a6-145">You can use ordered dictionaries in the same way that you use hash tables.</span></span>
<span data-ttu-id="751a6-146">這兩種類型都可以當做參數值使用，這些參數會採用雜湊表或字典 (iDictionary) 。</span><span class="sxs-lookup"><span data-stu-id="751a6-146">Either type can be used as the value of parameters that take a hash table or dictionary (iDictionary).</span></span>

<span data-ttu-id="751a6-147">您無法使用 [已排序] 屬性來轉換或轉換雜湊表。</span><span class="sxs-lookup"><span data-stu-id="751a6-147">You cannot use the [ordered] attribute to convert or cast a hash table.</span></span> <span data-ttu-id="751a6-148">如果您將已排序的屬性放在變數名稱之前，命令會失敗並出現下列錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="751a6-148">If you place the ordered attribute before the variable name, the command fails with the following error message.</span></span>

```powershell
PS C:\> [ordered]$hash = @{}
At line:1 char:1
+ [ordered]$hash = @{}
+ [!INCLUDE[]()]
The ordered attribute can be specified only on a hash literal node.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordExc
eption
+ FullyQualifiedErrorId : OrderedAttributeOnlyOnHashLiteralNode
```

<span data-ttu-id="751a6-149">若要更正運算式，請移動 [已排序] 屬性。</span><span class="sxs-lookup"><span data-stu-id="751a6-149">To correct the expression, move the [ordered] attribute.</span></span>

```powershell
PS C:\> $hash = [ordered]@{}
```

<span data-ttu-id="751a6-150">您可以將已排序的字典轉換成雜湊表，但是即使您清除變數並輸入新值，也無法復原已排序的屬性。</span><span class="sxs-lookup"><span data-stu-id="751a6-150">You can cast an ordered dictionary to a hash table, but you cannot recover the ordered attribute, even if you clear the variable and enter new values.</span></span> <span data-ttu-id="751a6-151">若要重新建立順序，您必須移除並重新建立變數。</span><span class="sxs-lookup"><span data-stu-id="751a6-151">To re-establish the order, you must remove and recreate the variable.</span></span>

```
PS C:\> [hashtable]$hash = [ordered]@{
>> Number = 1; Shape = "Square"; Color = "Blue"}
PS C:\> $hash

Name                           Value
----                           -----
Color                          Blue
Shape                          Square
Number                         1
```

### <a name="displaying-hash-tables"></a><span data-ttu-id="751a6-152">顯示雜湊表</span><span class="sxs-lookup"><span data-stu-id="751a6-152">Displaying Hash Tables</span></span>

<span data-ttu-id="751a6-153">若要顯示儲存在變數中的雜湊表，請輸入變數名稱。</span><span class="sxs-lookup"><span data-stu-id="751a6-153">To display a hash table that is saved in a variable, type the variable name.</span></span>
<span data-ttu-id="751a6-154">依預設，雜湊資料表會顯示為具有一個索引鍵資料行的資料表，以及一個值的資料行。</span><span class="sxs-lookup"><span data-stu-id="751a6-154">By default, a hash tables is displayed as a table with one column for keys and one for values.</span></span>

```powershell
C:\PS> $hash

Name                           Value
----                           -----
Shape                          Square
Color                          Blue
Number                         1
```

<span data-ttu-id="751a6-155">雜湊資料表有索引鍵和值屬性。</span><span class="sxs-lookup"><span data-stu-id="751a6-155">Hash tables have Keys and Values properties.</span></span> <span data-ttu-id="751a6-156">您可以使用點標記法來顯示所有的索引鍵或所有的值。</span><span class="sxs-lookup"><span data-stu-id="751a6-156">Use dot notation to display all of the keys or all of the values.</span></span>

```powershell
C:\PS> $hash.keys
Number
Shape
Color

C:\PS> $hash.values
1
Square
Blue
```

<span data-ttu-id="751a6-157">每個索引鍵名稱也是雜湊表的屬性，其值是索引鍵名稱屬性的值。</span><span class="sxs-lookup"><span data-stu-id="751a6-157">Each key name is also a property of the hash table, and its value is the value of the key-name property.</span></span> <span data-ttu-id="751a6-158">使用下列格式來顯示內容值。</span><span class="sxs-lookup"><span data-stu-id="751a6-158">Use the following format to display the property values.</span></span>

```powershell
$hashtable.<key>
<value>
```

<span data-ttu-id="751a6-159">例如：</span><span class="sxs-lookup"><span data-stu-id="751a6-159">For example:</span></span>

```powershell
C:\PS> $hash.Number
1

C:\PS> $hash.Color
Blue
```

<span data-ttu-id="751a6-160">如果索引鍵名稱與雜湊表類型的其中一個屬性名稱衝突，您就可以使用 `PSBase` 來存取這些屬性。</span><span class="sxs-lookup"><span data-stu-id="751a6-160">If the key name collides with one of the property names of the HashTable type, you can use `PSBase` to access those properties.</span></span> <span data-ttu-id="751a6-161">例如，如果索引鍵名稱是， `keys` 而您想要傳回索引鍵的集合，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="751a6-161">For example, if the key name is `keys` and you want to return the collection of Keys, use this syntax:</span></span>

```powershell
$hashtable.PSBase.Keys
```

<span data-ttu-id="751a6-162">雜湊資料表有一個 Count 屬性，表示雜湊表中的索引鍵/值組數目。</span><span class="sxs-lookup"><span data-stu-id="751a6-162">Hash tables have a Count property that indicates the number of key-value pairs in the hash table.</span></span>

```powershell
C:\PS> $hash.count
3
```

<span data-ttu-id="751a6-163">雜湊資料表資料表不是陣列，因此您不能使用整數做為雜湊表的索引，但您可以使用索引鍵名稱來編制雜湊表的索引。</span><span class="sxs-lookup"><span data-stu-id="751a6-163">Hash table tables are not arrays, so you cannot use an integer as an index into the hash table, but you can use a key name to index into the hash table.</span></span>
<span data-ttu-id="751a6-164">如果索引鍵是字串值，請用引號括住索引鍵名稱。</span><span class="sxs-lookup"><span data-stu-id="751a6-164">If the key is a string value, enclose the key name in quotation marks.</span></span>

<span data-ttu-id="751a6-165">例如：</span><span class="sxs-lookup"><span data-stu-id="751a6-165">For example:</span></span>

```powershell
C:\PS> $hash["Number"]
1
```

### <a name="adding-and-removing-keys-and-values"></a><span data-ttu-id="751a6-166">新增和移除索引鍵和值</span><span class="sxs-lookup"><span data-stu-id="751a6-166">Adding and Removing Keys and Values</span></span>

<span data-ttu-id="751a6-167">若要將索引鍵和值新增至雜湊表，請使用下列命令格式。</span><span class="sxs-lookup"><span data-stu-id="751a6-167">To add keys and values to a hash table, use the following command format.</span></span>

```powershell
$hash["<key>"] = "<value>"
```

<span data-ttu-id="751a6-168">例如，若要將值為 "Now" 的 "Time" 索引鍵新增至雜湊表，請使用下列語句格式。</span><span class="sxs-lookup"><span data-stu-id="751a6-168">For example, to add a "Time" key with a value of "Now" to the hash table, use the following statement format.</span></span>

```powershell
$hash["Time"] = "Now"
```

<span data-ttu-id="751a6-169">您也可以使用 system.string 物件的 Add 方法，將索引鍵和值加入至雜湊表。</span><span class="sxs-lookup"><span data-stu-id="751a6-169">You can also add keys and values to a hash table by using the Add method of the System.Collections.Hashtable object.</span></span> <span data-ttu-id="751a6-170">Add 方法具有下列語法：</span><span class="sxs-lookup"><span data-stu-id="751a6-170">The Add method has the following syntax:</span></span>

```powershell
Add(Key, Value)
```

<span data-ttu-id="751a6-171">例如，若要將值為 "Now" 的 "Time" 索引鍵新增至雜湊表，請使用下列語句格式。</span><span class="sxs-lookup"><span data-stu-id="751a6-171">For example, to add a "Time" key with a value of "Now" to the hash table, use the following statement format.</span></span>

```powershell
$hash.Add("Time", "Now")
```

<span data-ttu-id="751a6-172">而且，您可以使用加法運算子 (+) 將索引鍵和值加入至雜湊表，以將雜湊資料表加入至現有的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="751a6-172">And, you can add keys and values to a hash table by using the addition operator (+) to add a hash table to an existing hash table.</span></span> <span data-ttu-id="751a6-173">例如，下列語句會將值為 "Now" 的 "Time" 索引鍵新增至 $hash 變數中的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="751a6-173">For example, the following statement adds a "Time" key with a value of "Now" to the hash table in the $hash variable.</span></span>

```powershell
$hash = $hash + @{Time="Now"}
```

<span data-ttu-id="751a6-174">您也可以加入儲存在變數中的值。</span><span class="sxs-lookup"><span data-stu-id="751a6-174">You can also add values that are stored in variables.</span></span>

```powershell
$t = "Today"
$now = (Get-Date)

$hash.Add($t, $now)
```

<span data-ttu-id="751a6-175">您無法使用減法運算子來移除雜湊表中的索引鍵/值組，但您可以使用 Hashtable 物件的 Remove 方法。</span><span class="sxs-lookup"><span data-stu-id="751a6-175">You cannot use a subtraction operator to remove a key/value pair from a hash table, but you can use the Remove method of the Hashtable object.</span></span> <span data-ttu-id="751a6-176">Remove 方法會將索引鍵做為其值。</span><span class="sxs-lookup"><span data-stu-id="751a6-176">The Remove method takes the key as its value.</span></span>

<span data-ttu-id="751a6-177">Remove 方法具有下列語法：</span><span class="sxs-lookup"><span data-stu-id="751a6-177">The Remove method has the following syntax:</span></span>

```
Remove(Key)
```

<span data-ttu-id="751a6-178">例如，若要從 $hash 變數值中的雜湊表移除時間 = 現在的索引鍵/值組，請輸入：</span><span class="sxs-lookup"><span data-stu-id="751a6-178">For example, to remove the Time=Now key/value pair from the hash table in the value of the $hash variable, type:</span></span>

```powershell
$hash.Remove("Time")
```

<span data-ttu-id="751a6-179">您可以在 PowerShell 中使用雜湊表物件的所有屬性和方法，包括 Contains、Clear、Clone 和 CopyTo。</span><span class="sxs-lookup"><span data-stu-id="751a6-179">You can use all of the properties and methods of Hashtable objects in PowerShell, including Contains, Clear, Clone, and CopyTo.</span></span> <span data-ttu-id="751a6-180">如需雜湊表物件的詳細資訊，請參閱 MSDN 上的 "system.string"。</span><span class="sxs-lookup"><span data-stu-id="751a6-180">For more information about Hashtable objects, see "System.Collections.Hashtable" on MSDN.</span></span>

### <a name="object-types-in-hashtables"></a><span data-ttu-id="751a6-181">雜湊表中的物件類型</span><span class="sxs-lookup"><span data-stu-id="751a6-181">Object Types in HashTables</span></span>

<span data-ttu-id="751a6-182">雜湊表中的索引鍵和值可以具有任何 .NET 物件類型，而單一雜湊資料表可以有多個類型的索引鍵和值。</span><span class="sxs-lookup"><span data-stu-id="751a6-182">The keys and values in a hash table can have any .NET object type, and a single hash table can have keys and values of multiple types.</span></span>

<span data-ttu-id="751a6-183">下列語句會建立進程名稱字串和處理物件值的雜湊表，並將它儲存在 \$ p 變數中。</span><span class="sxs-lookup"><span data-stu-id="751a6-183">The following statement creates a hash table of process name strings and process object values and saves it in the \$p variable.</span></span>

```powershell
$p = @{"PowerShell" = (Get-Process PowerShell);
"Notepad" = (Get-Process notepad)}
```

<span data-ttu-id="751a6-184">您可以在 p 中顯示雜湊表 \$ ，並使用索引鍵名稱屬性來顯示這些值。</span><span class="sxs-lookup"><span data-stu-id="751a6-184">You can display the hash table in \$p and use the key-name properties to display the values.</span></span>

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)

C:\PS> $p.PowerShell

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    441      24    54196      54012   571     5.10   1788 PowerShell

C:\PS> $p.keys | foreach {$p.$_.handles}
441
251
```

<span data-ttu-id="751a6-185">雜湊表中的索引鍵也可以是任何 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="751a6-185">The keys in a hash table can also be any .NET type.</span></span> <span data-ttu-id="751a6-186">下列語句會將索引鍵/值組加入至 p 變數中的雜湊表 \$ 。</span><span class="sxs-lookup"><span data-stu-id="751a6-186">The following statement adds a key/value pair to the hash table in the \$p variable.</span></span> <span data-ttu-id="751a6-187">金鑰是代表 WinRM 服務的服務物件，而值則是服務的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="751a6-187">The key is a Service object that represents the WinRM service, and the value is the current status of the service.</span></span>

```powershell
C:\PS> $p = $p + @{(Get-Service WinRM) = ((Get-Service WinRM).Status)}
```

<span data-ttu-id="751a6-188">您可以使用在雜湊表中用於其他配對的相同方法，來顯示和存取新的索引鍵/值組。</span><span class="sxs-lookup"><span data-stu-id="751a6-188">You can display and access the new key/value pair by using the same methods that you use for other pairs in the hash table.</span></span>

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running

C:\PS> $p.keys
PowerShell
Notepad

Status   Name               DisplayName
------   ----               -----------
Running  winrm              Windows Remote Management (WS-Manag...

C:\PS> $p.keys | foreach {$_.name}
winrm
```

<span data-ttu-id="751a6-189">雜湊表中的索引鍵和值也可以是雜湊表物件。</span><span class="sxs-lookup"><span data-stu-id="751a6-189">The keys and values in a hash table can also be Hashtable objects.</span></span> <span data-ttu-id="751a6-190">下列語句會將索引鍵/值組加入至 p 變數中的雜湊表 \$ ，其中索引鍵是字串、Hash2，而值是具有三個索引鍵/值組的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="751a6-190">The following statement adds key/value pair to the hash table in the \$p variable in which the key is a string, Hash2, and the value is a hash table with three key/value pairs.</span></span>

```powershell
C:\PS> $p = $p + @{"Hash2"= @{a=1; b=2; c=3}}
```

<span data-ttu-id="751a6-191">您可以使用相同的方法來顯示及存取新的值。</span><span class="sxs-lookup"><span data-stu-id="751a6-191">You can display and access the new values by using the same methods.</span></span>

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running
Hash2                          {a, b, c}

C:\PS> $p.Hash2

Name                           Value
----                           -----
a                              1
b                              2
c                              3

C:\PS> $p.Hash2.b
2
```

### <a name="sorting-keys-and-values"></a><span data-ttu-id="751a6-192">排序索引鍵和值</span><span class="sxs-lookup"><span data-stu-id="751a6-192">Sorting Keys and Values</span></span>

<span data-ttu-id="751a6-193">雜湊表中的專案本質上未排序。</span><span class="sxs-lookup"><span data-stu-id="751a6-193">The items in a hash table are intrinsically unordered.</span></span> <span data-ttu-id="751a6-194">每次您顯示索引鍵/值組時，這些索引鍵/值組可能會以不同的順序出現。</span><span class="sxs-lookup"><span data-stu-id="751a6-194">The key/value pairs might appear in a different order each time that you display them.</span></span>

<span data-ttu-id="751a6-195">雖然您無法排序雜湊表，但您可以使用雜湊表的 GetEnumerator 方法來列舉索引鍵和值，然後使用 Sort-Object Cmdlet 來排序要顯示的列舉值。</span><span class="sxs-lookup"><span data-stu-id="751a6-195">Although you cannot sort a hash table, you can use the GetEnumerator method of hash tables to enumerate the keys and values, and then use the Sort-Object cmdlet to sort the enumerated values for display.</span></span>

<span data-ttu-id="751a6-196">例如，下列命令會列舉 p 變數中雜湊表中的索引鍵和值， \$ 然後依字母順序排序索引鍵。</span><span class="sxs-lookup"><span data-stu-id="751a6-196">For example, the following commands enumerate the keys and values in the hash table in the \$p variable and then sort the keys in alphabetical order.</span></span>

```powershell
C:\PS> $p.GetEnumerator() | Sort-Object -Property key

Name                           Value
----                           -----
Notepad                        System.Diagnostics.Process (notepad)
PowerShell                     System.Diagnostics.Process (PowerShell)
System.ServiceProcess.Servi... Running
```

<span data-ttu-id="751a6-197">下列命令會使用相同的程式，以遞減順序排序雜湊值。</span><span class="sxs-lookup"><span data-stu-id="751a6-197">The following command uses the same procedure to sort the hash values in descending order.</span></span>

```powershell
C:\PS> $p.getenumerator() | Sort-Object -Property Value -Descending

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running
```

### <a name="creating-objects-from-hash-tables"></a><span data-ttu-id="751a6-198">從雜湊表建立物件</span><span class="sxs-lookup"><span data-stu-id="751a6-198">Creating Objects from Hash Tables</span></span>

<span data-ttu-id="751a6-199">從 PowerShell 3.0 開始，您可以從屬性和屬性值的雜湊表建立物件。</span><span class="sxs-lookup"><span data-stu-id="751a6-199">Beginning in PowerShell 3.0, you can create an object from a hash table of properties and property values.</span></span>

<span data-ttu-id="751a6-200">語法如下：</span><span class="sxs-lookup"><span data-stu-id="751a6-200">The syntax is as follows:</span></span>

```powershell
[<class-name>]@{
  <property-name>=<property-value>
  <property-name>=<property-value>
}
```

<span data-ttu-id="751a6-201">這個方法只適用於具有 null 建構函式 (也就是沒有參數的建構函式) 的類別。</span><span class="sxs-lookup"><span data-stu-id="751a6-201">This method works only for classes that have a null constructor, that is, a constructor that has no parameters.</span></span> <span data-ttu-id="751a6-202">物件屬性必須是公用而且可設定。</span><span class="sxs-lookup"><span data-stu-id="751a6-202">The object properties must be public and settable.</span></span>

<span data-ttu-id="751a6-203">如需詳細資訊，請參閱 [about_Object_Creation](about_Object_Creation.md)。</span><span class="sxs-lookup"><span data-stu-id="751a6-203">For more information, see [about_Object_Creation](about_Object_Creation.md).</span></span>

### <a name="convertfrom-stringdata"></a><span data-ttu-id="751a6-204">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="751a6-204">ConvertFrom-StringData</span></span>

<span data-ttu-id="751a6-205">`ConvertFrom-StringData`Cmdlet 會將字串或此處的索引鍵/值組字串轉換成雜湊表。</span><span class="sxs-lookup"><span data-stu-id="751a6-205">The `ConvertFrom-StringData` cmdlet converts a string or a here-string of key/value pairs into a hash table.</span></span> <span data-ttu-id="751a6-206">您可以 `ConvertFrom-StringData` 在腳本的 [資料] 區段中安全地使用指令程式，您可以使用它搭配指令 `Import-LocalizedData` 程式，在使用者介面中顯示使用者訊息 (UI) 目前使用者的文化特性。</span><span class="sxs-lookup"><span data-stu-id="751a6-206">You can use the `ConvertFrom-StringData` cmdlet safely in the Data section of a script, and you can use it with the `Import-LocalizedData` cmdlet to display user messages in the user-interface (UI) culture of the current user.</span></span>

<span data-ttu-id="751a6-207">這裡-字串在雜湊表中的值包含引號時特別有用。</span><span class="sxs-lookup"><span data-stu-id="751a6-207">Here-strings are especially useful when the values in the hash table include quotation marks.</span></span> <span data-ttu-id="751a6-208">如需有關此字串的詳細資訊，請參閱 [about_Quoting_Rules](about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="751a6-208">For more information about here-strings, see [about_Quoting_Rules](about_Quoting_Rules.md).</span></span>

<span data-ttu-id="751a6-209">下列範例示範如何在上述範例中建立使用者訊息的這個字串，以及如何使用將 `ConvertFrom-StringData` 它們從字串轉換成雜湊表。</span><span class="sxs-lookup"><span data-stu-id="751a6-209">The following example shows how to create a here-string of the user messages in the previous example and how to use `ConvertFrom-StringData` to convert them from a string into a hash table.</span></span>

<span data-ttu-id="751a6-210">下列命令會建立此索引鍵/值組的字串，然後將它儲存在 \$ 字串變數中。</span><span class="sxs-lookup"><span data-stu-id="751a6-210">The following command creates a here-string of the key/value pairs and then saves it in the \$string variable.</span></span>

```powershell
C:\PS> $string = @"
Msg1 = Type "Windows".
Msg2 = She said, "Hello, World."
Msg3 = Enter an alias (or "nickname").
"@
```

<span data-ttu-id="751a6-211">此命令會使用 ConvertFrom-StringData Cmdlet，將此字串轉換成雜湊表。</span><span class="sxs-lookup"><span data-stu-id="751a6-211">This command uses the ConvertFrom-StringData cmdlet to convert the here-string into a hash table.</span></span>

```powershell
C:\PS> ConvertFrom-StringData $string

Name                           Value
----                           -----
Msg3                           Enter an alias (or "nickname").
Msg2                           She said, "Hello, World."
Msg1                           Type "Windows".
```

<span data-ttu-id="751a6-212">如需有關此字串的詳細資訊，請參閱 [about_Quoting_Rules](about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="751a6-212">For more information about here-strings, see [about_Quoting_Rules](about_Quoting_Rules.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="751a6-213">另請參閱</span><span class="sxs-lookup"><span data-stu-id="751a6-213">SEE ALSO</span></span>

[<span data-ttu-id="751a6-214">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="751a6-214">about_Arrays</span></span>](about_Arrays.md)

[<span data-ttu-id="751a6-215">about_Object_Creation</span><span class="sxs-lookup"><span data-stu-id="751a6-215">about_Object_Creation</span></span>](about_Object_Creation.md)

[<span data-ttu-id="751a6-216">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="751a6-216">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)

[<span data-ttu-id="751a6-217">about_Script_Internationalization</span><span class="sxs-lookup"><span data-stu-id="751a6-217">about_Script_Internationalization</span></span>](about_Script_Internationalization.md)

[<span data-ttu-id="751a6-218">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="751a6-218">ConvertFrom-StringData</span></span>](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)

[<span data-ttu-id="751a6-219">Import-LocalizedData</span><span class="sxs-lookup"><span data-stu-id="751a6-219">Import-LocalizedData</span></span>](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)

[<span data-ttu-id="751a6-220">System.Collections.Hashtable</span><span class="sxs-lookup"><span data-stu-id="751a6-220">System.Collections.Hashtable</span></span>](/dotnet/api/system.collections.hashtable)
