---
description: 描述陣列，這些是設計用來儲存專案集合的資料結構。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/26/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_arrays?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Arrays
ms.openlocfilehash: 2283c36d899c3ea743f6c379dc686ec583d7a36c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206784"
---
# <a name="about-arrays"></a><span data-ttu-id="50084-104">關於陣列</span><span class="sxs-lookup"><span data-stu-id="50084-104">About Arrays</span></span>

## <a name="short-description"></a><span data-ttu-id="50084-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="50084-105">Short Description</span></span>
<span data-ttu-id="50084-106">描述陣列，這些是設計用來儲存專案集合的資料結構。</span><span class="sxs-lookup"><span data-stu-id="50084-106">Describes arrays, which are data structures designed to store collections of items.</span></span>

## <a name="long-description"></a><span data-ttu-id="50084-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="50084-107">Long Description</span></span>

<span data-ttu-id="50084-108">陣列是設計用來儲存專案集合的資料結構。</span><span class="sxs-lookup"><span data-stu-id="50084-108">An array is a data structure that is designed to store a collection of items.</span></span>
<span data-ttu-id="50084-109">專案可以是相同類型或不同類型。</span><span class="sxs-lookup"><span data-stu-id="50084-109">The items can be the same type or different types.</span></span>

<span data-ttu-id="50084-110">從 Windows PowerShell 3.0 開始，零或一個物件的集合會有陣列的某些屬性。</span><span class="sxs-lookup"><span data-stu-id="50084-110">Beginning in Windows PowerShell 3.0, a collection of zero or one object has some properties of arrays.</span></span>

## <a name="creating-and-initializing-an-array"></a><span data-ttu-id="50084-111">建立和初始化陣列</span><span class="sxs-lookup"><span data-stu-id="50084-111">Creating and initializing an array</span></span>

<span data-ttu-id="50084-112">若要建立及初始化陣列，請將多個值指派給變數。</span><span class="sxs-lookup"><span data-stu-id="50084-112">To create and initialize an array, assign multiple values to a variable.</span></span> <span data-ttu-id="50084-113">儲存在陣列中的值會以逗號分隔，並以指派運算子 () 分隔引數名稱 `=` 。</span><span class="sxs-lookup"><span data-stu-id="50084-113">The values stored in the array are delimited with a comma and separated from the variable name by the assignment operator (`=`).</span></span>

<span data-ttu-id="50084-114">例如，若要建立名為 `$A` 的陣列，其中包含七個數值 (int) 值22、5、10、8、12、9和80，請輸入：</span><span class="sxs-lookup"><span data-stu-id="50084-114">For example, to create an array named `$A` that contains the seven numeric (int) values of 22, 5, 10, 8, 12, 9, and 80, type:</span></span>

```powershell
$A = 22,5,10,8,12,9,80
```

<span data-ttu-id="50084-115">您也可以將逗號放在單一專案之前，以使用逗號初始化單一專案陣列。</span><span class="sxs-lookup"><span data-stu-id="50084-115">The comma can also be used to initialize a single item array by placing the comma before the single item.</span></span>

<span data-ttu-id="50084-116">例如，若要建立名為的單一專案陣列 `$B` ，其中包含單一值7，請輸入：</span><span class="sxs-lookup"><span data-stu-id="50084-116">For example, to create a single item array named `$B` containing the single value of 7, type:</span></span>

```powershell
$B = ,7
```

<span data-ttu-id="50084-117">您也可以使用範圍運算子 () 來建立和初始化陣列 `..` 。</span><span class="sxs-lookup"><span data-stu-id="50084-117">You can also create and initialize an array by using the range operator (`..`).</span></span>
<span data-ttu-id="50084-118">下列範例會建立包含值5到8的陣列。</span><span class="sxs-lookup"><span data-stu-id="50084-118">The following example creates an array containing the values 5 through 8.</span></span>

```powershell
$C = 5..8
```

<span data-ttu-id="50084-119">因此， `$C` 包含四個值：5、6、7和8。</span><span class="sxs-lookup"><span data-stu-id="50084-119">As a result, `$C` contains four values: 5, 6, 7, and 8.</span></span>

<span data-ttu-id="50084-120">未指定任何資料類型時，PowerShell 會將每個陣列建立為物件陣列 ( **system.object []** ) 。</span><span class="sxs-lookup"><span data-stu-id="50084-120">When no data type is specified, PowerShell creates each array as an object array ( **System.Object[]** ).</span></span> <span data-ttu-id="50084-121">若要判斷陣列的資料類型，請使用 **GetType ( # B1** 方法。</span><span class="sxs-lookup"><span data-stu-id="50084-121">To determine the data type of an array, use the **GetType()** method.</span></span> <span data-ttu-id="50084-122">例如，若要判斷陣列的資料類型 `$A` ，請輸入：</span><span class="sxs-lookup"><span data-stu-id="50084-122">For example, to determine the data type of the `$A` array, type:</span></span>

```powershell
$A.GetType()
```

<span data-ttu-id="50084-123">若要建立強型別陣列，也就是只能包含特定類型之值的陣列，請將變數轉換為數組類型，例如 **string []** 、 **long []** 或 **int32 []** 。</span><span class="sxs-lookup"><span data-stu-id="50084-123">To create a strongly typed array, that is, an array that can contain only values of a particular type, cast the variable as an array type, such as **string[]** , **long[]** , or **int32[]** .</span></span> <span data-ttu-id="50084-124">若要轉換陣列，請在變數名稱之前加上括弧括住的陣列類型。</span><span class="sxs-lookup"><span data-stu-id="50084-124">To cast an array, precede the variable name with an array type enclosed in brackets.</span></span> <span data-ttu-id="50084-125">例如，若要建立名為的32位整數陣列 `$ia` ，其中包含四個整數 (1500、2230、3350和 4000) ，請輸入：</span><span class="sxs-lookup"><span data-stu-id="50084-125">For example, to create a 32-bit integer array named `$ia` containing four integers (1500, 2230, 3350, and 4000), type:</span></span>

```powershell
[int32[]]$ia = 1500,2230,3350,4000
```

<span data-ttu-id="50084-126">因此， `$ia` 陣列只能包含整數。</span><span class="sxs-lookup"><span data-stu-id="50084-126">As a result, the `$ia` array can contain only integers.</span></span>

<span data-ttu-id="50084-127">您可以建立在 Microsoft .NET Framework 中轉換成任何支援類型的陣列。</span><span class="sxs-lookup"><span data-stu-id="50084-127">You can create arrays that are cast to any supported type in the Microsoft .NET Framework.</span></span> <span data-ttu-id="50084-128">例如，用 `Get-Process` 來表示處理 **程式** 的物件是由系統的 ... 處理型別。</span><span class="sxs-lookup"><span data-stu-id="50084-128">For example, the objects that `Get-Process` retrieves to represent processes are of the **System.Diagnostics.Process** type.</span></span> <span data-ttu-id="50084-129">若要建立處理常式物件的強型別陣列，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="50084-129">To create a strongly typed array of process objects, enter the following command:</span></span>

```powershell
[Diagnostics.Process[]]$zz = Get-Process
```

## <a name="the-array-sub-expression-operator"></a><span data-ttu-id="50084-130">陣列子運算式運算子</span><span class="sxs-lookup"><span data-stu-id="50084-130">The array sub-expression operator</span></span>

<span data-ttu-id="50084-131">陣列子運算式運算子會從它內部的語句建立陣列。</span><span class="sxs-lookup"><span data-stu-id="50084-131">The array sub-expression operator creates an array from the statements inside it.</span></span> <span data-ttu-id="50084-132">無論運算子內的語句產生什麼，運算子都會將它放置在陣列中。</span><span class="sxs-lookup"><span data-stu-id="50084-132">Whatever the statement inside the operator produces, the operator will place it in an array.</span></span> <span data-ttu-id="50084-133">即使有零個或一個物件。</span><span class="sxs-lookup"><span data-stu-id="50084-133">Even if there is zero or one object.</span></span>

<span data-ttu-id="50084-134">陣列運算子的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="50084-134">The syntax of the array operator is as follows:</span></span>

```syntax
@( ... )
```

<span data-ttu-id="50084-135">您可以使用 array 運算子來建立零或一個物件的陣列。</span><span class="sxs-lookup"><span data-stu-id="50084-135">You can use the array operator to create an array of zero or one object.</span></span> <span data-ttu-id="50084-136">例如：</span><span class="sxs-lookup"><span data-stu-id="50084-136">For example:</span></span>

```powershell
$a = @("Hello World")
$a.Count
```

```Output
1
```

```powershell
$b = @()
$b.Count
```

```Output
0
```

<span data-ttu-id="50084-137">當您取得物件時，array 運算子在腳本中很有用，但不知道您取得的物件數目。</span><span class="sxs-lookup"><span data-stu-id="50084-137">The array operator is useful in scripts when you are getting objects, but do not know how many objects you get.</span></span> <span data-ttu-id="50084-138">例如：</span><span class="sxs-lookup"><span data-stu-id="50084-138">For example:</span></span>

```powershell
$p = @(Get-Process Notepad)
```

<span data-ttu-id="50084-139">如需有關陣列子運算式運算子的詳細資訊，請參閱 [about_Operators](about_Operators.md)。</span><span class="sxs-lookup"><span data-stu-id="50084-139">For more information about the array sub-expression operator, see [about_Operators](about_Operators.md).</span></span>

## <a name="accessing-and-using-array-elements"></a><span data-ttu-id="50084-140">存取和使用陣列元素</span><span class="sxs-lookup"><span data-stu-id="50084-140">Accessing and using array elements</span></span>

### <a name="reading-an-array"></a><span data-ttu-id="50084-141">讀取陣列</span><span class="sxs-lookup"><span data-stu-id="50084-141">Reading an array</span></span>

<span data-ttu-id="50084-142">您可以使用變數名稱來參考陣列。</span><span class="sxs-lookup"><span data-stu-id="50084-142">You can refer to an array by using its variable name.</span></span> <span data-ttu-id="50084-143">若要顯示陣列中的所有元素，請輸入陣列名稱稱。</span><span class="sxs-lookup"><span data-stu-id="50084-143">To display all the elements in the array, type the array name.</span></span> <span data-ttu-id="50084-144">例如，假設 `$a` 是一個陣列，其中包含0、1、2到9的整數; 輸入：</span><span class="sxs-lookup"><span data-stu-id="50084-144">For example, assuming `$a` is an array containing integers 0, 1, 2, until 9; typing:</span></span>

```powershell
$a
```

```Output
0
1
2
3
4
5
6
7
8
9
```

<span data-ttu-id="50084-145">您可以使用索引（從位置0開始）來參考陣列中的元素。</span><span class="sxs-lookup"><span data-stu-id="50084-145">You can refer to the elements in an array by using an index, beginning at position 0.</span></span> <span data-ttu-id="50084-146">以括弧括住索引編號。</span><span class="sxs-lookup"><span data-stu-id="50084-146">Enclose the index number in brackets.</span></span> <span data-ttu-id="50084-147">例如，若要顯示陣列中的第一個元素 `$a` ，請輸入：</span><span class="sxs-lookup"><span data-stu-id="50084-147">For example, to display the first element in the `$a` array, type:</span></span>

```powershell
$a[0]
```

```Output
0
```

<span data-ttu-id="50084-148">若要顯示陣列中的第三個元素 `$a` ，請輸入：</span><span class="sxs-lookup"><span data-stu-id="50084-148">To display the third element in the `$a` array, type:</span></span>

```powershell
$a[2]
```

```Output
2
```

<span data-ttu-id="50084-149">您可以使用索引的範圍運算子來取得陣列的一部分。</span><span class="sxs-lookup"><span data-stu-id="50084-149">You can retrieve part of the array using a range operator for the index.</span></span> <span data-ttu-id="50084-150">例如，若要取出陣列的第二到第五個元素，您可以輸入：</span><span class="sxs-lookup"><span data-stu-id="50084-150">For example, to retrieve the second to fifth elements of the array, you would type:</span></span>

```powershell
$a[1..4]
```

```Output
1
2
3
4
```

<span data-ttu-id="50084-151">從陣列結尾算算的負數。</span><span class="sxs-lookup"><span data-stu-id="50084-151">Negative numbers count from the end of the array.</span></span> <span data-ttu-id="50084-152">例如，"-1" 是指陣列的最後一個元素。</span><span class="sxs-lookup"><span data-stu-id="50084-152">For example, "-1" refers to the last element of the array.</span></span> <span data-ttu-id="50084-153">若要顯示陣列的最後三個元素，請在 [索引遞增順序] 中輸入：</span><span class="sxs-lookup"><span data-stu-id="50084-153">To display the last three elements of the array, in index ascending order, type:</span></span>

```powershell
$a = 0 .. 9
$a[-3..-1]
```

```Output
7
8
9
```

<span data-ttu-id="50084-154">如果您以遞減順序輸入負索引，則輸出會變更。</span><span class="sxs-lookup"><span data-stu-id="50084-154">If you type negative indexes in descending order, your output changes.</span></span>

```powershell
$a = 0 .. 9
$a[-1..-3]
```

```Output
9
8
7
```

<span data-ttu-id="50084-155">不過，使用此標記法時請務必小心。</span><span class="sxs-lookup"><span data-stu-id="50084-155">However, be cautious when using this notation.</span></span> <span data-ttu-id="50084-156">標記法從結束界限到陣列開頭的迴圈。</span><span class="sxs-lookup"><span data-stu-id="50084-156">The notation cycles from the end boundary to the beginning of the array.</span></span>

```powershell
$a = 0 .. 9
$a[2..-2]
```

```Output
2
1
0
9
8
```

<span data-ttu-id="50084-157">此外，另一個常見的錯誤是假設 `$a[0..-2]` 是參考陣列的所有元素，但最後一個除外。</span><span class="sxs-lookup"><span data-stu-id="50084-157">Also, one common mistake is to assume `$a[0..-2]` refers to all the elements of the array, except for the last one.</span></span> <span data-ttu-id="50084-158">它會參考陣列中的第一個、最後一個和第二個元素。</span><span class="sxs-lookup"><span data-stu-id="50084-158">It refers to the first, last, and second-to-last elements in the array.</span></span>

<span data-ttu-id="50084-159">您可以使用加號運算子 (`+`) ，將範圍與陣列中的元素清單結合。</span><span class="sxs-lookup"><span data-stu-id="50084-159">You can use the plus operator (`+`) to combine a ranges with a list of elements in an array.</span></span> <span data-ttu-id="50084-160">例如，若要顯示索引位置0、2和4到6的元素，請輸入：</span><span class="sxs-lookup"><span data-stu-id="50084-160">For example, to display the elements at index positions 0, 2, and 4 through 6, type:</span></span>

```powershell
$a = 0 .. 9
$a[0,2+4..6]
```

```Output
0
2
4
5
6
```

<span data-ttu-id="50084-161">此外，若要列出多個範圍和個別元素，您可以使用加號運算子。</span><span class="sxs-lookup"><span data-stu-id="50084-161">Also, to list multiple ranges and individual elements you can use the plus operator.</span></span> <span data-ttu-id="50084-162">例如，將專案從零到二、四到6，以及在第八個位置型別上的元素列出：</span><span class="sxs-lookup"><span data-stu-id="50084-162">For example, to list elements zero to two, four to six, and the element at eighth positional type:</span></span>

```powershell
$a = 0..9
$a[+0..2+4..6+8]
```

```Output
0
1
2
4
5
6
8
```

### <a name="iterations-over-array-elements"></a><span data-ttu-id="50084-163">反覆運算陣列元素</span><span class="sxs-lookup"><span data-stu-id="50084-163">Iterations over array elements</span></span>

<span data-ttu-id="50084-164">您也可以使用迴圈結構（例如 ForEach、For 和 While 迴圈）來參考陣列中的元素。</span><span class="sxs-lookup"><span data-stu-id="50084-164">You can also use looping constructs, such as ForEach, For, and While loops, to refer to the elements in an array.</span></span> <span data-ttu-id="50084-165">例如，若要使用 ForEach 迴圈來顯示陣列中的元素 `$a` ，請輸入：</span><span class="sxs-lookup"><span data-stu-id="50084-165">For example, to use a ForEach loop to display the elements in the `$a` array, type:</span></span>

```powershell
$a = 0..9
foreach ($element in $a) {
  $element
}
```

```Output
0
1
2
3
4
5
6
7
8
9
```

<span data-ttu-id="50084-166">Foreach 迴圈會逐一查看陣列，並傳回陣列中的每個值，直到到達陣列的結尾為止。</span><span class="sxs-lookup"><span data-stu-id="50084-166">The Foreach loop iterates through the array and returns each value in the array until reaching the end of the array.</span></span>

<span data-ttu-id="50084-167">當您在檢查陣列中的元素時，當您要遞增計數器時，For 迴圈會很有用。</span><span class="sxs-lookup"><span data-stu-id="50084-167">The For loop is useful when you are incrementing counters while examining the elements in an array.</span></span> <span data-ttu-id="50084-168">例如，若要使用 For 迴圈來傳回陣列中的每個其他值，請輸入：</span><span class="sxs-lookup"><span data-stu-id="50084-168">For example, to use a For loop to return every other value in an array, type:</span></span>

```powershell
$a = 0..9
for ($i = 0; $i -le ($a.length - 1); $i += 2) {
  $a[$i]
}
```

```Output
0
2
4
6
8
```

<span data-ttu-id="50084-169">您可以使用 While 迴圈來顯示陣列中的元素，直到定義的條件不再為 true 為止。</span><span class="sxs-lookup"><span data-stu-id="50084-169">You can use a While loop to display the elements in an array until a defined condition is no longer true.</span></span> <span data-ttu-id="50084-170">例如，若要在 `$a` 陣列索引小於4時顯示陣列中的元素，請輸入：</span><span class="sxs-lookup"><span data-stu-id="50084-170">For example, to display the elements in the `$a` array while the array index is less than 4, type:</span></span>

```powershell
$a = 0..9
$i=0
while($i -lt 4) {
  $a[$i];
  $i++
}
```

```Output
0
1
2
3
```

## <a name="properties-of-arrays"></a><span data-ttu-id="50084-171">陣列的屬性</span><span class="sxs-lookup"><span data-stu-id="50084-171">Properties of arrays</span></span>

### <a name="count-or-length-or-longlength"></a><span data-ttu-id="50084-172">Count 或 Length 或 LongLength</span><span class="sxs-lookup"><span data-stu-id="50084-172">Count or Length or LongLength</span></span>

<span data-ttu-id="50084-173">若要判斷陣列中有多少個專案，請使用 `Length` 屬性或其 `Count` 別名。</span><span class="sxs-lookup"><span data-stu-id="50084-173">To determine how many items are in an array, use the `Length` property or its `Count` alias.</span></span> <span data-ttu-id="50084-174">`Longlength` 如果陣列包含2147483647以上的元素，則會很有用。</span><span class="sxs-lookup"><span data-stu-id="50084-174">`Longlength` is useful if the array contains more than 2,147,483,647 elements.</span></span>

```powershell
$a = 0..9
$a.Count
$a.Length
```

```Output
10
10
```

### <a name="rank"></a><span data-ttu-id="50084-175">排名</span><span class="sxs-lookup"><span data-stu-id="50084-175">Rank</span></span>

<span data-ttu-id="50084-176">傳回陣列中的維度數目。</span><span class="sxs-lookup"><span data-stu-id="50084-176">Returns the number of dimensions in the array.</span></span> <span data-ttu-id="50084-177">PowerShell 中大部分的陣列只有一個維度。</span><span class="sxs-lookup"><span data-stu-id="50084-177">Most arrays in PowerShell have one dimension, only.</span></span> <span data-ttu-id="50084-178">即使您想要建立多維度陣列;如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="50084-178">Even when you think you are building a multidimensional array; like the following example:</span></span>

```powershell
$a = @(
  @(0,1),
  @("b", "c"),
  @(Get-Process)
)

[int]$r = $a.Rank
"`$a rank: $r"
```

```Output
$a rank: 1
```

<span data-ttu-id="50084-179">下列範例示範如何使用 .Net Framework 建立真正的多維陣列。</span><span class="sxs-lookup"><span data-stu-id="50084-179">The following example shows how to create a truly multidimensional array using the .Net Framework.</span></span>

```powershell
[int[,]]$rank2 = [int[,]]::new(5,5)
$rank2.rank
```

```Output
2
```

## <a name="methods-of-arrays"></a><span data-ttu-id="50084-180">陣列的方法</span><span class="sxs-lookup"><span data-stu-id="50084-180">Methods of arrays</span></span>

### <a name="clear"></a><span data-ttu-id="50084-181">Clear</span><span class="sxs-lookup"><span data-stu-id="50084-181">Clear</span></span>

<span data-ttu-id="50084-182">將所有元素值設定為數組專案類型的 _預設值_ 。</span><span class="sxs-lookup"><span data-stu-id="50084-182">Sets all element values to the _default value_ of the array's element type.</span></span>
<span data-ttu-id="50084-183">Clear ( # A1 方法不會重設陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="50084-183">The Clear() method does not reset the size of the array.</span></span>

<span data-ttu-id="50084-184">在下列範例中 `$a` ，是物件的陣列。</span><span class="sxs-lookup"><span data-stu-id="50084-184">In the following example `$a` is an array of objects.</span></span>

```powershell
$a = 1, 2, 3
$a.Clear()
$a | % { $null -eq $_ }
```

```Output
True
True
True
```

<span data-ttu-id="50084-185">在此範例中， `$intA` 明確類型為包含整數。</span><span class="sxs-lookup"><span data-stu-id="50084-185">In this example, `$intA` is explicitly typed to contain integers.</span></span>

```powershell
[int[]] $intA = 1, 2, 3
$intA.Clear()
$intA
```

```Output
0
0
0
```

### <a name="foreach"></a><span data-ttu-id="50084-186">ForEach</span><span class="sxs-lookup"><span data-stu-id="50084-186">ForEach</span></span>

<span data-ttu-id="50084-187">允許逐一查看陣列中的所有元素，並針對陣列的每個元素執行指定的作業。</span><span class="sxs-lookup"><span data-stu-id="50084-187">Allows to iterate over all elements in the array and perform a given operation for each element of the array.</span></span>

<span data-ttu-id="50084-188">ForEach 方法有數個多載，可執行不同的作業。</span><span class="sxs-lookup"><span data-stu-id="50084-188">The ForEach method has several overloads that perform different operations.</span></span>

```
ForEach(scriptblock expression)
ForEach(scriptblock expression, object[] arguments)
ForEach(type convertToType)
ForEach(string propertyName)
ForEach(string propertyName, object[] newValue)
ForEach(string methodName)
ForEach(string methodName, object[] arguments)
```

#### <a name="foreachscriptblock-expression"></a><span data-ttu-id="50084-189">ForEach (scriptblock 運算式) </span><span class="sxs-lookup"><span data-stu-id="50084-189">ForEach(scriptblock expression)</span></span>

#### <a name="foreachscriptblock-expression-object-arguments"></a><span data-ttu-id="50084-190">ForEach (scriptblock 運算式，object [] 引數) </span><span class="sxs-lookup"><span data-stu-id="50084-190">ForEach(scriptblock expression, object[] arguments)</span></span>

<span data-ttu-id="50084-191">此方法已新增至 PowerShell v4。</span><span class="sxs-lookup"><span data-stu-id="50084-191">This method was added in PowerShell v4.</span></span>

> [!NOTE]
> <span data-ttu-id="50084-192">語法需要使用腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="50084-192">The syntax requires the usage of a script block.</span></span> <span data-ttu-id="50084-193">如果 scriptblock 是唯一的參數，則括弧是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="50084-193">Parentheses are optional if the scriptblock is the only parameter.</span></span> <span data-ttu-id="50084-194">此外，方法和左括弧或大括弧之間不得有空格。</span><span class="sxs-lookup"><span data-stu-id="50084-194">Also, there must not be a space between the method and the opening parenthesis or brace.</span></span>

<span data-ttu-id="50084-195">下列範例顯示如何使用 foreach 方法。</span><span class="sxs-lookup"><span data-stu-id="50084-195">The following example shows how use the foreach method.</span></span> <span data-ttu-id="50084-196">在此情況下，目的是要產生陣列中元素的平方值。</span><span class="sxs-lookup"><span data-stu-id="50084-196">In this case the intent is to generate the square value of the elements in the array.</span></span>

```powershell
$a = @(0 .. 3)
$a.ForEach({ $_ * $_})
```

```Output
0
1
4
9
```

<span data-ttu-id="50084-197">如同的 `-ArgumentList` 參數 `ForEach-Object` ， `arguments` 參數允許將引數陣列傳遞至設定為接受這些引數的腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="50084-197">Just like the `-ArgumentList` parameter of `ForEach-Object`, the `arguments` parameter allows the passing of an array of arguments to a script block configured to accept them.</span></span>

<span data-ttu-id="50084-198">如需有關 **ArgumentList** 行為的詳細資訊，請參閱 [about_Splatting](about_Splatting.md#splatting-with-arrays)。</span><span class="sxs-lookup"><span data-stu-id="50084-198">For more information about the behavior of **ArgumentList** , see [about_Splatting](about_Splatting.md#splatting-with-arrays).</span></span>

#### <a name="foreachtype-converttotype"></a><span data-ttu-id="50084-199">ForEach (類型 convertToType) </span><span class="sxs-lookup"><span data-stu-id="50084-199">ForEach(type convertToType)</span></span>

<span data-ttu-id="50084-200">`ForEach`方法可以用來將專案轉換成不同的類型; 下列範例會示範如何將字串日期清單轉換成 `[DateTime]` 型別。</span><span class="sxs-lookup"><span data-stu-id="50084-200">The `ForEach` method can be used to swiftly cast the elements to a different type; the following example shows how to convert a list of string dates to `[DateTime]` type.</span></span>

```powershell
@("1/1/2017", "2/1/2017", "3/1/2017").ForEach([datetime])
```

```Output

Sunday, January 1, 2017 12:00:00 AM
Wednesday, February 1, 2017 12:00:00 AM
Wednesday, March 1, 2017 12:00:00 AM
```

#### <a name="foreachstring-propertyname"></a><span data-ttu-id="50084-201">ForEach (字串屬性名稱) </span><span class="sxs-lookup"><span data-stu-id="50084-201">ForEach(string propertyName)</span></span>

#### <a name="foreachstring-propertyname-object-newvalue"></a><span data-ttu-id="50084-202">ForEach (string propertyName，object [] newValue) </span><span class="sxs-lookup"><span data-stu-id="50084-202">ForEach(string propertyName, object[] newValue)</span></span>

<span data-ttu-id="50084-203">`ForEach`方法也可以用來快速取得或設定集合中每個專案的屬性值。</span><span class="sxs-lookup"><span data-stu-id="50084-203">The `ForEach` method can also be used to quickly retrieve, or set property values for every item in the collection.</span></span>

```powershell
# Set all LastAccessTime properties of files to the current date.
(dir 'C:\Temp').ForEach('LastAccessTime', (Get-Date))
# View the newly set LastAccessTime of all items, and find Unique entries.
(dir 'C:\Temp').ForEach('LastAccessTime') | Get-Unique
```

```Output
Wednesday, June 20, 2018 9:21:57 AM
```

#### <a name="foreachstring-methodname"></a><span data-ttu-id="50084-204">ForEach (字串方法名稱) </span><span class="sxs-lookup"><span data-stu-id="50084-204">ForEach(string methodName)</span></span>

#### <a name="foreachstring-methodname-object-arguments"></a><span data-ttu-id="50084-205">ForEach (字串方法名稱，object [] 引數) </span><span class="sxs-lookup"><span data-stu-id="50084-205">ForEach(string methodName, object[] arguments)</span></span>

<span data-ttu-id="50084-206">最後， `ForEach` 方法可以用來在集合中的每個專案上執行方法。</span><span class="sxs-lookup"><span data-stu-id="50084-206">Lastly, `ForEach` methods can be used to execute a method on every item in the collection.</span></span>

```powershell
("one", "two", "three").ForEach("ToUpper")
```

```Output
ONE
TWO
THREE
```

<span data-ttu-id="50084-207">如同的 `-ArgumentList` 參數 `ForEach-Object` ， `arguments` 參數允許將引數陣列傳遞至設定為接受這些引數的腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="50084-207">Just like the `-ArgumentList` parameter of `ForEach-Object`, the `arguments` parameter allows the passing of an array of arguments to a script block configured to accept them.</span></span>

> [!NOTE]
> <span data-ttu-id="50084-208">從 Windows PowerShell 3.0 開始，也可以使用「純量物件和集合的方法」來完成集合中每個專案的屬性和執行方法，您可以在這裡閱讀更多相關資訊 [about_methods](about_methods.md)。</span><span class="sxs-lookup"><span data-stu-id="50084-208">Starting in Windows PowerShell 3.0 retrieving properties and executing methods for each item in a collection can also be accomplished using "Methods of scalar objects and collections" You can read more about that here [about_methods](about_methods.md).</span></span>

### <a name="where"></a><span data-ttu-id="50084-209">Where</span><span class="sxs-lookup"><span data-stu-id="50084-209">Where</span></span>

<span data-ttu-id="50084-210">允許篩選或選取陣列的元素。</span><span class="sxs-lookup"><span data-stu-id="50084-210">Allows to filter or select the elements of the array.</span></span> <span data-ttu-id="50084-211">腳本必須評估為與下列專案不同的專案：零 (0) 、空字串， `$false` 或專案 `$null` 要顯示在 `Where`</span><span class="sxs-lookup"><span data-stu-id="50084-211">The script must evaluate to anything different than: zero (0), empty string, `$false` or `$null` for the element to show after the `Where`</span></span>

<span data-ttu-id="50084-212">方法有一個定義 `Where` 。</span><span class="sxs-lookup"><span data-stu-id="50084-212">There is one definition for the `Where` method.</span></span>

```
Where(scriptblock expression[, WhereOperatorSelectionMode mode
                            [, int numberToReturn]])
```

> [!NOTE]
> <span data-ttu-id="50084-213">語法需要使用腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="50084-213">The syntax requires the usage of a script block.</span></span> <span data-ttu-id="50084-214">如果 scriptblock 是唯一的參數，則括弧是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="50084-214">Parentheses are optional if the scriptblock is the only parameter.</span></span> <span data-ttu-id="50084-215">此外，方法和左括弧或大括弧之間不得有空格。</span><span class="sxs-lookup"><span data-stu-id="50084-215">Also, there must not be a space between the method and the opening parenthesis or brace.</span></span>

<span data-ttu-id="50084-216">`Expression`是篩選所需的 scriptblock， `mode` 選擇性引數允許其他選取功能，而 `numberToReturn` 選擇性引數可讓您限制從篩選傳回的專案數目。</span><span class="sxs-lookup"><span data-stu-id="50084-216">The `Expression` is scriptblock that is required for filtering, the `mode` optional argument allows additional selection capabilities, and the `numberToReturn` optional argument allows the ability to limit how many items are returned from the filter.</span></span>

<span data-ttu-id="50084-217">的可接受值為 `mode` ：</span><span class="sxs-lookup"><span data-stu-id="50084-217">The acceptable values for `mode` are:</span></span>

- <span data-ttu-id="50084-218">預設 (0) -傳回所有專案</span><span class="sxs-lookup"><span data-stu-id="50084-218">Default (0) - Return all items</span></span>
- <span data-ttu-id="50084-219">第一個 (1) -傳回第一個專案</span><span class="sxs-lookup"><span data-stu-id="50084-219">First (1) - Return the first item</span></span>
- <span data-ttu-id="50084-220">最後 (2) -傳回最後一個專案</span><span class="sxs-lookup"><span data-stu-id="50084-220">Last (2) - Return the last item</span></span>
- <span data-ttu-id="50084-221">SkipUntil (3) -略過專案直到條件為 true，傳回剩餘的專案</span><span class="sxs-lookup"><span data-stu-id="50084-221">SkipUntil (3) - Skip items until condition is true, the return the remaining items</span></span>
- <span data-ttu-id="50084-222">直到 (4) -傳回所有專案，直到條件為 true</span><span class="sxs-lookup"><span data-stu-id="50084-222">Until (4) - Return all items until condition is true</span></span>
- <span data-ttu-id="50084-223">分割 (5) -傳回兩個元素的陣列</span><span class="sxs-lookup"><span data-stu-id="50084-223">Split (5) - Return an array of two elements</span></span>
  - <span data-ttu-id="50084-224">第一個元素包含相符的專案</span><span class="sxs-lookup"><span data-stu-id="50084-224">The first element contains matching items</span></span>
  - <span data-ttu-id="50084-225">第二個元素包含其餘專案</span><span class="sxs-lookup"><span data-stu-id="50084-225">The second element contains the remaining items</span></span>

<span data-ttu-id="50084-226">下列範例顯示如何從陣列中選取所有奇數。</span><span class="sxs-lookup"><span data-stu-id="50084-226">The following example shows how to select all odd numbers from the array.</span></span>

```powershell
(0..9).Where{ $_ % 2 }
```

```Output
1
3
5
7
9
```

<span data-ttu-id="50084-227">這個範例會示範如何選取非空白的字串。</span><span class="sxs-lookup"><span data-stu-id="50084-227">This example show how to select the strings that are not empty.</span></span>

```powershell
('hi', '', 'there').Where({$_.Length})
```

```Output
hi
there
```

#### <a name="default"></a><span data-ttu-id="50084-228">預設</span><span class="sxs-lookup"><span data-stu-id="50084-228">Default</span></span>

<span data-ttu-id="50084-229">此 `Default` 模式會使用 scriptblock 篩選項目 `Expression` 。</span><span class="sxs-lookup"><span data-stu-id="50084-229">The `Default` mode filters items using the `Expression` scriptblock.</span></span>

<span data-ttu-id="50084-230">如果 `numberToReturn` 已提供，它會指定要傳回的專案數目上限。</span><span class="sxs-lookup"><span data-stu-id="50084-230">If a `numberToReturn` is provided, it specifies the maximum number of items to return.</span></span>

```powershell
# Get the zip files in the current users profile, sorted by LastAccessTime.
$Zips = dir $env:userprofile -Recurse '*.zip' | Sort-Object LastAccessTime
# Get the least accessed file over 100MB
$Zips.Where({$_.Length -gt 100MB}, 'Default', 1)
```

> [!NOTE]
> <span data-ttu-id="50084-231">`Default`模式和模式都會傳回 `First` 第一個 (`numberToReturn`) 專案，而且可以交換使用。</span><span class="sxs-lookup"><span data-stu-id="50084-231">Both the `Default` mode and `First` mode return the first (`numberToReturn`) items, and can be used interchangeably.</span></span>

#### <a name="last"></a><span data-ttu-id="50084-232">最後一個</span><span class="sxs-lookup"><span data-stu-id="50084-232">Last</span></span>

```powershell
$h = (Get-Date).AddHours(-1)
$logs = dir 'C:\' -Recurse '*.log' | Sort-Object CreationTime
# Find the last 5 log files created in the past hour.
$logs.Where({$_.CreationTime -gt $h}, 'Last', 5)
```

#### <a name="skipuntil"></a><span data-ttu-id="50084-233">SkipUntil</span><span class="sxs-lookup"><span data-stu-id="50084-233">SkipUntil</span></span>

<span data-ttu-id="50084-234">`SkipUntil`模式會略過集合中的所有物件，直到物件通過腳本區塊運算式篩選。</span><span class="sxs-lookup"><span data-stu-id="50084-234">The `SkipUntil` mode skips all objects in a collection until an object passes the script block expression filter.</span></span> <span data-ttu-id="50084-235">然後，它會傳回 **所有** 其餘的收集項，而不進行測試。</span><span class="sxs-lookup"><span data-stu-id="50084-235">It then returns **ALL** remaining collection items without testing them.</span></span> <span data-ttu-id="50084-236">_只測試一個傳遞專案_ 。</span><span class="sxs-lookup"><span data-stu-id="50084-236">_Only one passing item is tested_ .</span></span>

<span data-ttu-id="50084-237">這表示傳回的集合包含未經過測試的 _傳遞_ 和 _未傳遞_ 專案。</span><span class="sxs-lookup"><span data-stu-id="50084-237">This means the returned collection contains both _passing_ and _non-passing_ items that have NOT been tested.</span></span>

<span data-ttu-id="50084-238">傳回的專案數可透過傳遞值給 `numberToReturn` 引數來限制。</span><span class="sxs-lookup"><span data-stu-id="50084-238">The number of items returned can be limited by passing a value to the `numberToReturn` argument.</span></span>

```powershell
$computers = "Server01", "Server02", "Server03", "localhost", "Server04"
# Find the first available online server.
$computers.Where({ Test-Connection $_ }, 'SkipUntil', 1)
```

```Output
localhost
```

#### <a name="until"></a><span data-ttu-id="50084-239">直到</span><span class="sxs-lookup"><span data-stu-id="50084-239">Until</span></span>

<span data-ttu-id="50084-240">`Until`模式會反轉 `SkipUntil` 模式。</span><span class="sxs-lookup"><span data-stu-id="50084-240">The `Until` mode inverts the `SkipUntil` mode.</span></span>  <span data-ttu-id="50084-241">它會傳回集合中的 **所有** 專案，直到專案通過腳本區塊運算式為止。</span><span class="sxs-lookup"><span data-stu-id="50084-241">It returns **ALL** items in a collection until an item passes the script block expression.</span></span> <span data-ttu-id="50084-242">一旦專案 _通過_ scriptblock 運算式，方法就會 `Where` 停止處理專案。</span><span class="sxs-lookup"><span data-stu-id="50084-242">Once an item _passes_ the scriptblock expression, the `Where` method stops processing items.</span></span>

<span data-ttu-id="50084-243">這表示您會收到來自方法的第一組 _非傳遞_ 專案 `Where` 。</span><span class="sxs-lookup"><span data-stu-id="50084-243">This means that you receive the first set of _non-passing_ items from the `Where` method.</span></span> <span data-ttu-id="50084-244">一個專案通過 _後_ ，就不會測試或傳回其餘部分。</span><span class="sxs-lookup"><span data-stu-id="50084-244">_After_ one item passes, the rest are NOT tested or returned.</span></span>

<span data-ttu-id="50084-245">傳回的專案數可透過傳遞值給 `numberToReturn` 引數來限制。</span><span class="sxs-lookup"><span data-stu-id="50084-245">The number of items returned can be limited by passing a value to the `numberToReturn` argument.</span></span>

```powershell
# Retrieve the first set of numbers less than or equal to 10.
(1..50).Where({$_ -gt 10}, 'Until')
# This would perform the same operation.
(1..50).Where({$_ -le 10})
```

```Output
1
2
3
4
5
6
7
8
9
10
```

> [!NOTE]
> <span data-ttu-id="50084-246">`Until`和都 `SkipUntil` 是在不測試一批專案的前提下運作。</span><span class="sxs-lookup"><span data-stu-id="50084-246">Both `Until` and `SkipUntil` operate under the premise of NOT testing a batch of items.</span></span>
>
> <span data-ttu-id="50084-247">`Until`_傳回_ 第一次行程 **之前** 的專案。</span><span class="sxs-lookup"><span data-stu-id="50084-247">`Until` returns the items **BEFORE** the first _pass_ .</span></span>
>
> <span data-ttu-id="50084-248">`SkipUntil`傳回第一次 _傳遞_**之後** 的所有專案，包括第一個傳遞專案。</span><span class="sxs-lookup"><span data-stu-id="50084-248">`SkipUntil` returns all the items **AFTER** the first _pass_ , including the first passing item.</span></span>

#### <a name="split"></a><span data-ttu-id="50084-249">分割</span><span class="sxs-lookup"><span data-stu-id="50084-249">Split</span></span>

<span data-ttu-id="50084-250">`Split`模式會分割，或將集合專案分組為兩個不同的集合。</span><span class="sxs-lookup"><span data-stu-id="50084-250">The `Split` mode splits, or groups collection items into two separate collections.</span></span> <span data-ttu-id="50084-251">傳遞 scriptblock 運算式的那些運算式，以及不會傳遞的運算式。</span><span class="sxs-lookup"><span data-stu-id="50084-251">Those that pass the scriptblock expression, and those that do not.</span></span>

<span data-ttu-id="50084-252">如果 `numberToReturn` 指定了，則第一個集合會包含 _傳遞_ 的專案，而不會超過指定的值。</span><span class="sxs-lookup"><span data-stu-id="50084-252">If a `numberToReturn` is specified, the first collection, contains the _passing_ items, not to exceed the value specified.</span></span>

<span data-ttu-id="50084-253">其餘的物件（甚至是 **通過** 運算式篩選的物件）會在第二個集合中傳回。</span><span class="sxs-lookup"><span data-stu-id="50084-253">The remaining objects, even those that **PASS** the expression filter, are returned in the second collection.</span></span>

```powershell
$running, $stopped = (Get-Service).Where({$_.Status -eq 'Running'}, 'Split')
$running
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  Appinfo            Application Information
Running  AudioEndpointBu... Windows Audio Endpoint Builder
Running  Audiosrv           Windows Audio
...
```

```powershell
$stopped
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
...
```

## <a name="get-the-members-of-an-array"></a><span data-ttu-id="50084-254">取得陣列的成員</span><span class="sxs-lookup"><span data-stu-id="50084-254">Get the members of an array</span></span>

<span data-ttu-id="50084-255">若要取得陣列的屬性和方法（例如 Length 屬性和 **SetValue** 方法），請使用 Cmdlet 的 **InputObject** 參數 `Get-Member` 。</span><span class="sxs-lookup"><span data-stu-id="50084-255">To get the properties and methods of an array, such as the Length property and the **SetValue** method, use the **InputObject** parameter of the `Get-Member` cmdlet.</span></span>

<span data-ttu-id="50084-256">當您使用管線將陣列傳送至時 `Get-Member` ，PowerShell 會一次傳送一個專案，並傳回 `Get-Member` 陣列中每個專案的類型 (忽略重複專案) 。</span><span class="sxs-lookup"><span data-stu-id="50084-256">When you pipe an array to `Get-Member`, PowerShell sends the items one at a time and `Get-Member` returns the type of each item in the array (ignoring duplicates).</span></span>

<span data-ttu-id="50084-257">當您使用 **InputObject** 參數時，會傳回 `Get-Member` 陣列的成員。</span><span class="sxs-lookup"><span data-stu-id="50084-257">When you use the **InputObject** parameter, `Get-Member` returns the members of the array.</span></span>

<span data-ttu-id="50084-258">例如，下列命令會取得 `$a` 陣列變數的成員。</span><span class="sxs-lookup"><span data-stu-id="50084-258">For example, the following command gets the members of the `$a` array variable.</span></span>

```powershell
Get-Member -InputObject $a
```

<span data-ttu-id="50084-259">您也可以在傳送至 Cmdlet 的值之前輸入逗號 ( ) ，以取得陣列的成員 `Get-Member` 。</span><span class="sxs-lookup"><span data-stu-id="50084-259">You can also get the members of an array by typing a comma (,) before the value that is piped to the `Get-Member` cmdlet.</span></span> <span data-ttu-id="50084-260">逗號會讓陣列成為陣列陣列中的第二個專案。</span><span class="sxs-lookup"><span data-stu-id="50084-260">The comma makes the array the second item in an array of arrays.</span></span> <span data-ttu-id="50084-261">PowerShell 會一次將一個陣列輸送，並傳回 `Get-Member` 陣列的成員。</span><span class="sxs-lookup"><span data-stu-id="50084-261">PowerShell pipes the arrays one at a time and `Get-Member` returns the members of the array.</span></span> <span data-ttu-id="50084-262">如同接下來的兩個範例。</span><span class="sxs-lookup"><span data-stu-id="50084-262">Like the next two examples.</span></span>

```powershell
,$a | Get-Member

,(1,2,3) | Get-Member
```

## <a name="manipulating-an-array"></a><span data-ttu-id="50084-263">運算元組</span><span class="sxs-lookup"><span data-stu-id="50084-263">Manipulating an array</span></span>

<span data-ttu-id="50084-264">您可以變更陣列中的元素、將專案加入至陣列，以及將兩個數組的值結合成第三個數組。</span><span class="sxs-lookup"><span data-stu-id="50084-264">You can change the elements in an array, add an element to an array, and combine the values from two arrays into a third array.</span></span>

<span data-ttu-id="50084-265">若要變更陣列中特定專案的值，請指定您要變更的陣列名稱稱和元素的索引，然後使用指派運算子 (`=`) 來指定專案的新值。</span><span class="sxs-lookup"><span data-stu-id="50084-265">To change the value of a particular element in an array, specify the array name and the index of the element that you want to change, and then use the assignment operator (`=`) to specify a new value for the element.</span></span> <span data-ttu-id="50084-266">例如，若要將陣列中第二個專案的值 `$a` (索引位置 1) 變更為10，請輸入：</span><span class="sxs-lookup"><span data-stu-id="50084-266">For example, to change the value of the second item in the `$a` array (index position 1) to 10, type:</span></span>

```powershell
$a[1] = 10
```

<span data-ttu-id="50084-267">您也可以使用陣列的 **SetValue** 方法來變更值。</span><span class="sxs-lookup"><span data-stu-id="50084-267">You can also use the **SetValue** method of an array to change a value.</span></span> <span data-ttu-id="50084-268">下列範例會將陣列 (索引位置 1) 的第二個值變更 `$a` 為500：</span><span class="sxs-lookup"><span data-stu-id="50084-268">The following example changes the second value (index position 1) of the `$a` array to 500:</span></span>

```powershell
$a.SetValue(500,1)
```

<span data-ttu-id="50084-269">您可以使用 `+=` 運算子將元素加入至陣列。</span><span class="sxs-lookup"><span data-stu-id="50084-269">You can use the `+=` operator to add an element to an array.</span></span> <span data-ttu-id="50084-270">下列範例顯示如何將元素加入至 `$a` 陣列。</span><span class="sxs-lookup"><span data-stu-id="50084-270">The following example shows how to add an element to the `$a` array.</span></span>

```powershell
$a = @(0..4)
$a += 5
```

> [!NOTE]
> <span data-ttu-id="50084-271">當您使用 `+=` 運算子時，PowerShell 實際上會建立新的陣列，其中包含原始陣列的值和新增的值。</span><span class="sxs-lookup"><span data-stu-id="50084-271">When you use the `+=` operator, PowerShell actually creates a new array with the values of the original array and the added value.</span></span> <span data-ttu-id="50084-272">如果作業重複數次，或陣列的大小太大，這可能會導致效能問題。</span><span class="sxs-lookup"><span data-stu-id="50084-272">This might cause performance issues if the operation is repeated several times or the size of the array is too big.</span></span>

<span data-ttu-id="50084-273">從陣列中刪除元素並不容易，但您可以建立新的陣列，其中只包含現有陣列的選取專案。</span><span class="sxs-lookup"><span data-stu-id="50084-273">It is not easy to delete elements from an array, but you can create a new array that contains only selected elements of an existing array.</span></span> <span data-ttu-id="50084-274">例如，若要 `$t` 使用陣列中的所有元素（ `$a` 位於索引位置2的值除外）來建立陣列，請輸入：</span><span class="sxs-lookup"><span data-stu-id="50084-274">For example, to create the `$t` array with all the elements in the `$a` array except for the value at index position 2, type:</span></span>

```powershell
$t = $a[0,1 + 3..($a.length - 1)]
```

<span data-ttu-id="50084-275">若要將兩個數組合並為單一陣列，請使用加號運算子 (`+`) 。</span><span class="sxs-lookup"><span data-stu-id="50084-275">To combine two arrays into a single array, use the plus operator (`+`).</span></span> <span data-ttu-id="50084-276">下列範例會建立兩個數組、將它們合併，然後顯示產生的組合陣列。</span><span class="sxs-lookup"><span data-stu-id="50084-276">The following example creates two arrays, combines them, and then displays the resulting combined array.</span></span>

```powershell
$x = 1,3
$y = 5,9
$z = $x + $y
```

<span data-ttu-id="50084-277">如此一來， `$z` 陣列會包含1、3、5和9。</span><span class="sxs-lookup"><span data-stu-id="50084-277">As a result, the `$z` array contains 1, 3, 5, and 9.</span></span>

<span data-ttu-id="50084-278">若要刪除陣列，請將的值指派 `$null` 給陣列。</span><span class="sxs-lookup"><span data-stu-id="50084-278">To delete an array, assign a value of `$null` to the array.</span></span> <span data-ttu-id="50084-279">下列命令會刪除變數中的陣列 `$a` 。</span><span class="sxs-lookup"><span data-stu-id="50084-279">The following command deletes the array in the `$a` variable.</span></span>

`$a = $null`

<span data-ttu-id="50084-280">您也可以使用指令 `Remove-Item` 程式，但指派的值 `$null` 更快，尤其是大型陣列。</span><span class="sxs-lookup"><span data-stu-id="50084-280">You can also use the `Remove-Item` cmdlet, but assigning a value of `$null` is faster, especially for large arrays.</span></span>

## <a name="arrays-of-zero-or-one"></a><span data-ttu-id="50084-281">零或一的陣列</span><span class="sxs-lookup"><span data-stu-id="50084-281">Arrays of zero or one</span></span>

<span data-ttu-id="50084-282">從 Windows PowerShell 3.0 開始，零或一個物件的集合會有 Count 和 Length 屬性。</span><span class="sxs-lookup"><span data-stu-id="50084-282">Beginning in Windows PowerShell 3.0, a collection of zero or one object has the Count and Length property.</span></span> <span data-ttu-id="50084-283">此外，您也可以為一個物件的陣列編制索引。</span><span class="sxs-lookup"><span data-stu-id="50084-283">Also, you can index into an array of one object.</span></span> <span data-ttu-id="50084-284">這項功能可協助您避免在預期集合的命令到達兩個專案時所發生的腳本錯誤。</span><span class="sxs-lookup"><span data-stu-id="50084-284">This feature helps you to avoid scripting errors that occur when a command that expects a collection gets fewer than two items.</span></span>

<span data-ttu-id="50084-285">下列範例示範這項功能。</span><span class="sxs-lookup"><span data-stu-id="50084-285">The following examples demonstrate this feature.</span></span>

### <a name="zero-objects"></a><span data-ttu-id="50084-286">零物件</span><span class="sxs-lookup"><span data-stu-id="50084-286">Zero objects</span></span>

```powershell
$a = $null
$a.Count
$a.Length
```

```Output
0
0
```

### <a name="one-object"></a><span data-ttu-id="50084-287">一個物件</span><span class="sxs-lookup"><span data-stu-id="50084-287">One object</span></span>

```powershell
$a = 4
$a.Count
$a.Length
$a[0]
$a[-1]
```

```Output
1
1
4
4
```

## <a name="indexing-support-for-systemtuple-objects"></a><span data-ttu-id="50084-288">系統元組物件的索引支援</span><span class="sxs-lookup"><span data-stu-id="50084-288">Indexing support for System.Tuple objects</span></span>

<span data-ttu-id="50084-289">PowerShell 6.1 新增了 **元組** 物件的索引存取支援，類似于陣列。</span><span class="sxs-lookup"><span data-stu-id="50084-289">PowerShell 6.1 added the support for indexed access of **Tuple** objects, similar to arrays.</span></span>
<span data-ttu-id="50084-290">例如：</span><span class="sxs-lookup"><span data-stu-id="50084-290">For example:</span></span>

```powershell
PS> $tuple = [Tuple]::Create(1, 'test')
PS> $tuple[0]
1
PS> $tuple[1]
test
PS> $tuple[0..1]
1
test
PS> $tuple[-1]
test
```

<span data-ttu-id="50084-291">與陣列和其他集合物件不同的是，當透過管線或支持對象陣列的參數傳遞元組物件時，會將 **元組** 物件視為單一物件。</span><span class="sxs-lookup"><span data-stu-id="50084-291">Unlike arrays and other collection objects, **Tuple** objects are treated as a single object when passed through the pipeline or by parameters that support arrays of objects.</span></span>

<span data-ttu-id="50084-292">如需詳細資訊，請參閱 [系統元組](/dotnet/api/system.tuple)。</span><span class="sxs-lookup"><span data-stu-id="50084-292">For more information, see [System.Tuple](/dotnet/api/system.tuple).</span></span>

## <a name="see-also"></a><span data-ttu-id="50084-293">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50084-293">See also</span></span>

- [<span data-ttu-id="50084-294">about_Assignment_Operators</span><span class="sxs-lookup"><span data-stu-id="50084-294">about_Assignment_Operators</span></span>](about_Assignment_Operators.md)
- [<span data-ttu-id="50084-295">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="50084-295">about_Hash_Tables</span></span>](about_Hash_Tables.md)
- [<span data-ttu-id="50084-296">about_Operators</span><span class="sxs-lookup"><span data-stu-id="50084-296">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="50084-297">about_For</span><span class="sxs-lookup"><span data-stu-id="50084-297">about_For</span></span>](about_For.md)
- [<span data-ttu-id="50084-298">about_Foreach</span><span class="sxs-lookup"><span data-stu-id="50084-298">about_Foreach</span></span>](about_Foreach.md)
- [<span data-ttu-id="50084-299">about_While</span><span class="sxs-lookup"><span data-stu-id="50084-299">about_While</span></span>](about_While.md)
