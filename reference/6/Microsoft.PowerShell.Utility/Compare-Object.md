---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/compare-object?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Compare-Object
ms.openlocfilehash: c72cde8e626993726ae1a52206c88e20c3a7c588
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "93208879"
---
# <span data-ttu-id="4da1b-103">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="4da1b-103">Compare-Object</span></span>

## <span data-ttu-id="4da1b-104">概要</span><span class="sxs-lookup"><span data-stu-id="4da1b-104">Synopsis</span></span>
<span data-ttu-id="4da1b-105">比較兩個物件集。</span><span class="sxs-lookup"><span data-stu-id="4da1b-105">Compares two sets of objects.</span></span>

## <span data-ttu-id="4da1b-106">語法</span><span class="sxs-lookup"><span data-stu-id="4da1b-106">Syntax</span></span>

```
Compare-Object [-ReferenceObject] <PSObject[]> [-DifferenceObject] <PSObject[]>
 [-SyncWindow <Int32>] [-Property <Object[]>] [-ExcludeDifferent] [-IncludeEqual] [-PassThru]
 [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

## <span data-ttu-id="4da1b-107">描述</span><span class="sxs-lookup"><span data-stu-id="4da1b-107">Description</span></span>

<span data-ttu-id="4da1b-108">此 `Compare-Object` Cmdlet 會比較兩組物件。</span><span class="sxs-lookup"><span data-stu-id="4da1b-108">The `Compare-Object` cmdlet compares two sets of objects.</span></span> <span data-ttu-id="4da1b-109">其中一組物件是 **參考** ，而另一組物件則是 **差異** 。</span><span class="sxs-lookup"><span data-stu-id="4da1b-109">One set of objects is the **reference** , and the other set of objects is the **difference**.</span></span>

<span data-ttu-id="4da1b-110">`Compare-Object` 檢查是否有比較整個物件的可用方法。</span><span class="sxs-lookup"><span data-stu-id="4da1b-110">`Compare-Object` checks for available methods of comparing a whole object.</span></span> <span data-ttu-id="4da1b-111">如果找不到合適的方法，它會呼叫 **ToString ( # B1** 方法的輸入物件，並比較字串結果。</span><span class="sxs-lookup"><span data-stu-id="4da1b-111">If it can't find a suitable method, it calls the **ToString()** methods of the input objects and compares the string results.</span></span> <span data-ttu-id="4da1b-112">您可以提供要用於比較的一或多個屬性。</span><span class="sxs-lookup"><span data-stu-id="4da1b-112">You can provide one or more properties to be used for comparison.</span></span> <span data-ttu-id="4da1b-113">當提供屬性時，此 Cmdlet 只會比較這些屬性的值。</span><span class="sxs-lookup"><span data-stu-id="4da1b-113">When properties are provided, the cmdlet compares the values of those properties only.</span></span>

<span data-ttu-id="4da1b-114">比較的結果會指出屬性值是否只出現在 **參考** 物件中 () ， `<=` 或只出現在 () 的 **差異** 物件中 `=>` 。</span><span class="sxs-lookup"><span data-stu-id="4da1b-114">The result of the comparison indicates whether a property value appeared only in the **reference** object (`<=`) or only in the **difference** object (`=>`).</span></span> <span data-ttu-id="4da1b-115">如果使用 **IncludeEqual** 參數， (`==`) 表示值是在這兩個物件中。</span><span class="sxs-lookup"><span data-stu-id="4da1b-115">If the **IncludeEqual** parameter is used, (`==`) indicates the value is in both objects.</span></span>

<span data-ttu-id="4da1b-116">如果 **參考** 或 **差異** 物件 () 為 null，則會 `$null` `Compare-Object` 產生終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="4da1b-116">If the **reference** or the **difference** objects are null (`$null`), `Compare-Object` generates a terminating error.</span></span>

<span data-ttu-id="4da1b-117">某些範例會使用展開來減少程式碼範例的行長度。</span><span class="sxs-lookup"><span data-stu-id="4da1b-117">Some examples use splatting to reduce the line length of the code samples.</span></span> <span data-ttu-id="4da1b-118">如需詳細資訊，請參閱 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)。</span><span class="sxs-lookup"><span data-stu-id="4da1b-118">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

## <span data-ttu-id="4da1b-119">範例</span><span class="sxs-lookup"><span data-stu-id="4da1b-119">Examples</span></span>

### <span data-ttu-id="4da1b-120">範例 1-比較兩個文字檔的內容</span><span class="sxs-lookup"><span data-stu-id="4da1b-120">Example 1 - Compare the content of two text files</span></span>

<span data-ttu-id="4da1b-121">此範例會比較兩個文字檔的內容。</span><span class="sxs-lookup"><span data-stu-id="4da1b-121">This example compares the contents of two text files.</span></span> <span data-ttu-id="4da1b-122">此範例會使用下列兩個文字檔，其中每個值都在個別行上。</span><span class="sxs-lookup"><span data-stu-id="4da1b-122">The example uses the following two text files, with each value on a separate line.</span></span>

- <span data-ttu-id="4da1b-123">`Testfile1.txt` 包含值：狗、squirrel 和鳥。</span><span class="sxs-lookup"><span data-stu-id="4da1b-123">`Testfile1.txt` contains the values: dog, squirrel, and bird.</span></span>
- <span data-ttu-id="4da1b-124">`Testfile2.txt` 包含下列值：貓、鳥和 racoon。</span><span class="sxs-lookup"><span data-stu-id="4da1b-124">`Testfile2.txt` contains the values: cat, bird, and racoon.</span></span>

<span data-ttu-id="4da1b-125">輸出只會顯示檔案之間不同的行。</span><span class="sxs-lookup"><span data-stu-id="4da1b-125">The output displays only the lines that are different between the files.</span></span> <span data-ttu-id="4da1b-126">`Testfile1.txt` 這是 () 的 **參考** 物件 `<=` ，而 `Testfile2.txt` () 的 **差異** 物件 `=>` 。</span><span class="sxs-lookup"><span data-stu-id="4da1b-126">`Testfile1.txt` is the **reference** object (`<=`) and `Testfile2.txt`is the **difference** object (`=>`).</span></span> <span data-ttu-id="4da1b-127">不會顯示同時出現在這兩個檔案中的內容行。</span><span class="sxs-lookup"><span data-stu-id="4da1b-127">Lines with content that appear in both files aren't displayed.</span></span>

```powershell
Compare-Object -ReferenceObject (Get-Content -Path C:\Test\Testfile1.txt) -DifferenceObject (Get-Content -Path C:\Test\Testfile2.txt)
```

```Output
InputObject SideIndicator
----------- -------------
cat         =>
racoon      =>
dog         <=
squirrel    <=
```

### <span data-ttu-id="4da1b-128">範例 2-比較每一行內容並排除差異</span><span class="sxs-lookup"><span data-stu-id="4da1b-128">Example 2 - Compare each line of content and exclude the differences</span></span>

<span data-ttu-id="4da1b-129">這個範例會使用 **IncludeEqual** 和 **ExcludeDifferent** 參數，來比較兩個文字檔中每一行的內容。</span><span class="sxs-lookup"><span data-stu-id="4da1b-129">This example uses the **IncludeEqual** and **ExcludeDifferent** parameters to compare each line of content in two text files.</span></span>

<span data-ttu-id="4da1b-130">因為此命令使用 **ExcludeDifferent** 參數，所以輸出只會包含兩個檔案中包含的行，如 **SideIndicator** () 所示 `==` 。</span><span class="sxs-lookup"><span data-stu-id="4da1b-130">Because the command uses the **ExcludeDifferent** parameter, the output only contains lines contained in both files, as shown by the **SideIndicator** (`==`).</span></span>

```powershell
$objects = @{
  ReferenceObject = (Get-Content -Path C:\Test\Testfile1.txt)
  DifferenceObject = (Get-Content -Path C:\Test\Testfile2.txt)
}
Compare-Object @objects -IncludeEqual -ExcludeDifferent
```

```Output
InputObject SideIndicator
----------- -------------
bird        ==
```

<a id="ex3" />

### <span data-ttu-id="4da1b-131">範例 3-使用 PassThru 參數顯示差異</span><span class="sxs-lookup"><span data-stu-id="4da1b-131">Example 3 - Show the difference when using the PassThru parameter</span></span>

<span data-ttu-id="4da1b-132">通常會傳回 `Compare-Object` 具有下列屬性的 **PSCustomObject** 類型：</span><span class="sxs-lookup"><span data-stu-id="4da1b-132">Normally, `Compare-Object` returns a **PSCustomObject** type with the following properties:</span></span>

- <span data-ttu-id="4da1b-133">要比較的 **InputObject**</span><span class="sxs-lookup"><span data-stu-id="4da1b-133">The **InputObject** being compared</span></span>
- <span data-ttu-id="4da1b-134">**SideIndicator** 屬性，顯示輸出所屬的輸入物件</span><span class="sxs-lookup"><span data-stu-id="4da1b-134">The **SideIndicator** property showing which input object the output belongs to</span></span>

<span data-ttu-id="4da1b-135">當您使用 **PassThru** 參數時，物件的 **型** 別不會變更，但所傳回物件的實例會有一個名為 **SideIndicator** 的新增 **NoteProperty** 。</span><span class="sxs-lookup"><span data-stu-id="4da1b-135">When you use the **PassThru** parameter, the **Type** of the object is not changed but the instance of the object returned has an added **NoteProperty** named **SideIndicator**.</span></span> <span data-ttu-id="4da1b-136">**SideIndicator** 會顯示輸出所屬的輸入物件。</span><span class="sxs-lookup"><span data-stu-id="4da1b-136">**SideIndicator** shows which input object the output belongs to.</span></span>

<span data-ttu-id="4da1b-137">下列範例顯示不同的輸出類型。</span><span class="sxs-lookup"><span data-stu-id="4da1b-137">The following examples shows the different output types.</span></span>

```powershell
$a = $True
Compare-Object -IncludeEqual $a $a
(Compare-Object -IncludeEqual $a $a) | Get-Member
```

```Output
InputObject SideIndicator
----------- -------------
       True ==

   TypeName: System.Management.Automation.PSCustomObject
Name          MemberType   Definition
----          ----------   ----------
Equals        Method       bool Equals(System.Object obj)
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
ToString      Method       string ToString()
InputObject   NoteProperty System.Boolean InputObject=True
SideIndicator NoteProperty string SideIndicator===
```

```powershell
Compare-Object -IncludeEqual $a $a -PassThru
(Compare-Object -IncludeEqual $a $a -PassThru) | Get-Member
```

```Output
True

   TypeName: System.Boolean
Name          MemberType   Definition
----          ----------   ----------
CompareTo     Method       int CompareTo(System.Object obj), int CompareTo(bool value), int IComparable.CompareTo(Syst
Equals        Method       bool Equals(System.Object obj), bool Equals(bool obj), bool IEquatable[bool].Equals(bool ot
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
GetTypeCode   Method       System.TypeCode GetTypeCode(), System.TypeCode IConvertible.GetTypeCode()
ToBoolean     Method       bool IConvertible.ToBoolean(System.IFormatProvider provider)
ToByte        Method       byte IConvertible.ToByte(System.IFormatProvider provider)
ToChar        Method       char IConvertible.ToChar(System.IFormatProvider provider)
ToDateTime    Method       datetime IConvertible.ToDateTime(System.IFormatProvider provider)
ToDecimal     Method       decimal IConvertible.ToDecimal(System.IFormatProvider provider)
ToDouble      Method       double IConvertible.ToDouble(System.IFormatProvider provider)
ToInt16       Method       short IConvertible.ToInt16(System.IFormatProvider provider)
ToInt32       Method       int IConvertible.ToInt32(System.IFormatProvider provider)
ToInt64       Method       long IConvertible.ToInt64(System.IFormatProvider provider)
ToSByte       Method       sbyte IConvertible.ToSByte(System.IFormatProvider provider)
ToSingle      Method       float IConvertible.ToSingle(System.IFormatProvider provider)
ToString      Method       string ToString(), string ToString(System.IFormatProvider provider), string IConvertible.To
ToType        Method       System.Object IConvertible.ToType(type conversionType, System.IFormatProvider provider)
ToUInt16      Method       ushort IConvertible.ToUInt16(System.IFormatProvider provider)
ToUInt32      Method       uint IConvertible.ToUInt32(System.IFormatProvider provider)
ToUInt64      Method       ulong IConvertible.ToUInt64(System.IFormatProvider provider)
TryFormat     Method       bool TryFormat(System.Span[char] destination, [ref] int charsWritten)
SideIndicator NoteProperty string SideIndicator===
```

<span data-ttu-id="4da1b-138">使用 **PassThru** 時， **系統** 會傳回 (system.string) 的原始物件類型。</span><span class="sxs-lookup"><span data-stu-id="4da1b-138">When using **PassThru** , the original object type ( **System.Boolean** ) is returned.</span></span> <span data-ttu-id="4da1b-139">請注意，[system.string **] 物件的** 預設格式所顯示的輸出未顯示 [ **SideIndicator** ] 屬性。</span><span class="sxs-lookup"><span data-stu-id="4da1b-139">Note how the output displayed by the default format for **System.Boolean** objects didn't display the **SideIndicator** property.</span></span> <span data-ttu-id="4da1b-140">不過 **，傳回的** system.string 物件具有加入的 **NoteProperty** 。</span><span class="sxs-lookup"><span data-stu-id="4da1b-140">However, the returned **System.Boolean** object has the added **NoteProperty**.</span></span>

### <span data-ttu-id="4da1b-141">範例 4-使用屬性比較兩個簡單的物件</span><span class="sxs-lookup"><span data-stu-id="4da1b-141">Example 4 - Compare two simple objects using properties</span></span>

<span data-ttu-id="4da1b-142">在此範例中，我們會比較兩個具有相同長度的不同字串。</span><span class="sxs-lookup"><span data-stu-id="4da1b-142">In this example, we compare two different string that have the same length.</span></span>

```powershell
Compare-Object -ReferenceObject 'abc' -DifferenceObject 'xyz' -Property Length -IncludeEqual
```

```Output
Length SideIndicator
------ -------------
     3 ==
```

### <span data-ttu-id="4da1b-143">範例 5-使用屬性比較複雜物件</span><span class="sxs-lookup"><span data-stu-id="4da1b-143">Example 5 - Comparing complex objects using properties</span></span>

<span data-ttu-id="4da1b-144">此範例顯示比較複雜物件時的行為。</span><span class="sxs-lookup"><span data-stu-id="4da1b-144">This example shows the behavior when comparing complex objects.</span></span> <span data-ttu-id="4da1b-145">在此範例中，我們會針對不同的 PowerShell 實例儲存兩個不同的處理常式物件。</span><span class="sxs-lookup"><span data-stu-id="4da1b-145">In this example we store two different process objects for different instances of PowerShell.</span></span> <span data-ttu-id="4da1b-146">這兩個變數都包含具有相同名稱的處理常式物件。</span><span class="sxs-lookup"><span data-stu-id="4da1b-146">Both variables contain process objects with the same name.</span></span> <span data-ttu-id="4da1b-147">當比較物件但未指定 **Property** 參數時，此 Cmdlet 會將物件視為相等。</span><span class="sxs-lookup"><span data-stu-id="4da1b-147">When the objects are compared without specifying the **Property** parameter, the cmdlet considers the objects to be equal.</span></span> <span data-ttu-id="4da1b-148">請注意， **InputObject** 的值與 **ToString ( # B1** 方法的結果相同。</span><span class="sxs-lookup"><span data-stu-id="4da1b-148">Notice that the value of the **InputObject** is the same as the result of the **ToString()** method.</span></span> <span data-ttu-id="4da1b-149">由於 **system.object** 沒有 **IComparable** 介面，因此 Cmdlet 會將物件轉換成字串，然後比較結果。</span><span class="sxs-lookup"><span data-stu-id="4da1b-149">Since the **System.Diagnostics.Process** class does not have the **IComparable** interface, the cmdlet converts the objects to strings then compares the results.</span></span>

```powershell
PS> Get-Process pwsh

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    101   123.32     139.10      35.81   11168   1 pwsh
     89   107.55      66.97      11.44   17600   1 pwsh

PS> $a = Get-Process -Id 11168
PS> $b = Get-Process -Id 17600
PS> $a.ToString()
System.Diagnostics.Process (pwsh)
PS> $b.ToString()
System.Diagnostics.Process (pwsh)
PS> Compare-Object $a $b -IncludeEqual

InputObject                       SideIndicator
-----------                       -------------
System.Diagnostics.Process (pwsh) ==

PS> Compare-Object $a $b -Property ProcessName, Id, CPU

ProcessName    Id       CPU SideIndicator
-----------    --       --- -------------
pwsh        17600   11.4375 =>
pwsh        11168 36.203125 <=
```

<span data-ttu-id="4da1b-150">當您指定要比較的屬性時，此 Cmdlet 會顯示差異。</span><span class="sxs-lookup"><span data-stu-id="4da1b-150">When you specify properties to be compared, the cmdlet shows the differences.</span></span>

### <span data-ttu-id="4da1b-151">範例 6-比較執行 IComparable 的複雜物件</span><span class="sxs-lookup"><span data-stu-id="4da1b-151">Example 6 - Comparing complex objects that implement IComparable</span></span>

<span data-ttu-id="4da1b-152">如果物件實作為 **IComparable** ，此 Cmdlet 會搜尋比較物件的方式。如果物件是不同的類型，則會將 **差異** 物件轉換成 **ReferenceObject** 的類型，然後再進行比較。</span><span class="sxs-lookup"><span data-stu-id="4da1b-152">If the object implements **IComparable** , the cmdlet searches for ways to compare the objects.If the objects are different types, the **Difference** object is converted to the type of the **ReferenceObject** then compared.</span></span>

<span data-ttu-id="4da1b-153">在此範例中，我們會比較字串與 **TimeSpan** 物件。</span><span class="sxs-lookup"><span data-stu-id="4da1b-153">In this example, we are comparing a string to a **TimeSpan** object.</span></span> <span data-ttu-id="4da1b-154">在第一種情況下，字串會轉換成 **TimeSpan** ，因此物件相等。</span><span class="sxs-lookup"><span data-stu-id="4da1b-154">In the first case, the string is converted to a **TimeSpan** so the objects are equal.</span></span>

```powershell
Compare-Object ([TimeSpan]"0:0:1") "0:0:1" -IncludeEqual
```

```Output
InputObject SideIndicator
----------- -------------
00:00:01    ==
```

```powershell
Compare-Object "0:0:1" ([TimeSpan]"0:0:1")
```

```Output
InputObject SideIndicator
----------- -------------
00:00:01    =>
0:0:1       <=
```

<span data-ttu-id="4da1b-155">在第二個案例中， **TimeSpan** 會轉換成字串，因此物件是不同的。</span><span class="sxs-lookup"><span data-stu-id="4da1b-155">In the second case, the **TimeSpan** is converted to a string so the object are different.</span></span>

## <span data-ttu-id="4da1b-156">參數</span><span class="sxs-lookup"><span data-stu-id="4da1b-156">Parameters</span></span>

### <span data-ttu-id="4da1b-157">-CaseSensitive</span><span class="sxs-lookup"><span data-stu-id="4da1b-157">-CaseSensitive</span></span>

<span data-ttu-id="4da1b-158">指出比較應區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="4da1b-158">Indicates that comparisons should be case-sensitive.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4da1b-159">-Culture</span><span class="sxs-lookup"><span data-stu-id="4da1b-159">-Culture</span></span>

<span data-ttu-id="4da1b-160">指定要用於比較的文化特性。</span><span class="sxs-lookup"><span data-stu-id="4da1b-160">Specifies the culture to use for comparisons.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4da1b-161">-DifferenceObject</span><span class="sxs-lookup"><span data-stu-id="4da1b-161">-DifferenceObject</span></span>

<span data-ttu-id="4da1b-162">指定與 **參考** 物件比較的物件。</span><span class="sxs-lookup"><span data-stu-id="4da1b-162">Specifies the objects that are compared to the **reference** objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4da1b-163">-ExcludeDifferent</span><span class="sxs-lookup"><span data-stu-id="4da1b-163">-ExcludeDifferent</span></span>

<span data-ttu-id="4da1b-164">指出這個 Cmdlet 只會顯示相同物件的比較特性。</span><span class="sxs-lookup"><span data-stu-id="4da1b-164">Indicates that this cmdlet displays only the characteristics of compared objects that are equal.</span></span> <span data-ttu-id="4da1b-165">捨棄物件之間的差異。</span><span class="sxs-lookup"><span data-stu-id="4da1b-165">The differences between the objects are discarded.</span></span>

<span data-ttu-id="4da1b-166">使用 **ExcludeDifferent** 搭配 **IncludeEqual** ，只顯示 **參考** 和 **差異** 物件之間相符的行。</span><span class="sxs-lookup"><span data-stu-id="4da1b-166">Use **ExcludeDifferent** with **IncludeEqual** to display only the lines that match between the **reference** and **difference** objects.</span></span>

<span data-ttu-id="4da1b-167">如果指定了 **ExcludeDifferent** 但沒有 **IncludeEqual** ，就不會有輸出。</span><span class="sxs-lookup"><span data-stu-id="4da1b-167">If **ExcludeDifferent** is specified without **IncludeEqual** , there's no output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4da1b-168">-IncludeEqual</span><span class="sxs-lookup"><span data-stu-id="4da1b-168">-IncludeEqual</span></span>

<span data-ttu-id="4da1b-169">**IncludeEqual** 會顯示 **參考** 和 **差異** 物件之間的相符專案。</span><span class="sxs-lookup"><span data-stu-id="4da1b-169">**IncludeEqual** displays the matches between the **reference** and **difference** objects.</span></span>

<span data-ttu-id="4da1b-170">根據預設，輸出也會包含 **參考** 和 **差異** 物件之間的差異。</span><span class="sxs-lookup"><span data-stu-id="4da1b-170">By default, the output also includes the differences between the **reference** and **difference** objects.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4da1b-171">-PassThru</span><span class="sxs-lookup"><span data-stu-id="4da1b-171">-PassThru</span></span>

<span data-ttu-id="4da1b-172">當您使用 **PassThru** 參數時，會 `Compare-Object` 省略比較物件周圍的 **PSCustomObject** 包裝函式，並傳回不同的物件（不變）。</span><span class="sxs-lookup"><span data-stu-id="4da1b-172">When you use the **PassThru** parameter, `Compare-Object` omits the **PSCustomObject** wrapper around the compared objects and returns the differing objects, unchanged.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4da1b-173">-Property</span><span class="sxs-lookup"><span data-stu-id="4da1b-173">-Property</span></span>

<span data-ttu-id="4da1b-174">指定要比較之 **參考** 和 **差異** 物件的屬性陣列。</span><span class="sxs-lookup"><span data-stu-id="4da1b-174">Specifies an array of properties of the **reference** and **difference** objects to compare.</span></span>

<span data-ttu-id="4da1b-175">**Property** 參數的值可以是新的計算屬性。</span><span class="sxs-lookup"><span data-stu-id="4da1b-175">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="4da1b-176">計算的屬性可以是腳本區塊或雜湊表。</span><span class="sxs-lookup"><span data-stu-id="4da1b-176">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="4da1b-177">有效的索引鍵/值組為：</span><span class="sxs-lookup"><span data-stu-id="4da1b-177">Valid key-value pairs are:</span></span>

- <span data-ttu-id="4da1b-178">運算式 `<string>` 或 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="4da1b-178">Expression - `<string>` or `<script block>`</span></span>

<span data-ttu-id="4da1b-179">如需詳細資訊，請參閱 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。</span><span class="sxs-lookup"><span data-stu-id="4da1b-179">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4da1b-180">-ReferenceObject</span><span class="sxs-lookup"><span data-stu-id="4da1b-180">-ReferenceObject</span></span>

<span data-ttu-id="4da1b-181">指定用來做為比較參考的物件陣列。</span><span class="sxs-lookup"><span data-stu-id="4da1b-181">Specifies an array of objects used as a reference for comparison.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4da1b-182">-SyncWindow</span><span class="sxs-lookup"><span data-stu-id="4da1b-182">-SyncWindow</span></span>

<span data-ttu-id="4da1b-183">指定 `Compare-Object` 在物件集合中尋找相符項時檢查的相鄰物件數目。</span><span class="sxs-lookup"><span data-stu-id="4da1b-183">Specifies the number of adjacent objects that `Compare-Object` inspects while looking for a match in a collection of objects.</span></span> <span data-ttu-id="4da1b-184">`Compare-Object` 當在集合中找不到相同位置的物件時，檢查連續的物件。</span><span class="sxs-lookup"><span data-stu-id="4da1b-184">`Compare-Object` examines adjacent objects when it doesn't find the object in the same position in a collection.</span></span> <span data-ttu-id="4da1b-185">預設值是 `[Int32]::MaxValue` ，這表示會 `Compare-Object` 檢查整個物件集合。</span><span class="sxs-lookup"><span data-stu-id="4da1b-185">The default value is `[Int32]::MaxValue`, which means that `Compare-Object` examines the entire object collection.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: [Int32]::MaxValue
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4da1b-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4da1b-186">CommonParameters</span></span>

<span data-ttu-id="4da1b-187">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="4da1b-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4da1b-188">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="4da1b-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4da1b-189">輸入</span><span class="sxs-lookup"><span data-stu-id="4da1b-189">Inputs</span></span>

### <span data-ttu-id="4da1b-190">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="4da1b-190">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="4da1b-191">您可以將物件沿著管線向下傳送至 **DifferenceObject** 參數。</span><span class="sxs-lookup"><span data-stu-id="4da1b-191">You can send an object down the pipeline to the **DifferenceObject** parameter.</span></span>

## <span data-ttu-id="4da1b-192">輸出</span><span class="sxs-lookup"><span data-stu-id="4da1b-192">Outputs</span></span>

### <span data-ttu-id="4da1b-193">無</span><span class="sxs-lookup"><span data-stu-id="4da1b-193">None</span></span>

<span data-ttu-id="4da1b-194">如果 **參考** 物件和 **差異** 物件相同，除非您使用 **IncludeEqual** 參數，否則不會有輸出。</span><span class="sxs-lookup"><span data-stu-id="4da1b-194">If the **reference** object and the **difference** object are the same, there's no output, unless you use the **IncludeEqual** parameter.</span></span>

### <span data-ttu-id="4da1b-195">System.Management.Automation.PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="4da1b-195">System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="4da1b-196">如果物件不同，請將不同的 `Compare-Object` 物件包裝在 `PSCustomObject` 具有 **SideIndicator** 屬性的包裝函式中，以參考差異。</span><span class="sxs-lookup"><span data-stu-id="4da1b-196">If the objects are different, `Compare-Object` wraps the differing objects in a `PSCustomObject` wrapper with a **SideIndicator** property to reference the differences.</span></span>

<span data-ttu-id="4da1b-197">當您使用 **PassThru** 參數時，物件的 **型** 別不會變更，但所傳回物件的實例會有一個名為 **SideIndicator** 的新增 **NoteProperty** 。</span><span class="sxs-lookup"><span data-stu-id="4da1b-197">When you use the **PassThru** parameter, the **Type** of the object is not changed but the instance of the object returned has an added **NoteProperty** named **SideIndicator**.</span></span> <span data-ttu-id="4da1b-198">**SideIndicator** 會顯示輸出所屬的輸入物件。</span><span class="sxs-lookup"><span data-stu-id="4da1b-198">**SideIndicator** shows which input object the output belongs to.</span></span>

## <span data-ttu-id="4da1b-199">備忘稿</span><span class="sxs-lookup"><span data-stu-id="4da1b-199">Notes</span></span>

<span data-ttu-id="4da1b-200">使用 **PassThru** 參數時，主控台中顯示的輸出可能不會包含 **SideIndicator** 屬性。</span><span class="sxs-lookup"><span data-stu-id="4da1b-200">When using the **PassThru** parameter, the output displayed in the console may not include the **SideIndicator** property.</span></span> <span data-ttu-id="4da1b-201">的物件類型輸出的預設格式視圖 `Compare-Object` 不包含 **SideIndicator** 屬性。</span><span class="sxs-lookup"><span data-stu-id="4da1b-201">The default format view of the for the object type output by `Compare-Object` does not include the **SideIndicator** property.</span></span> <span data-ttu-id="4da1b-202">如需詳細資訊，請參閱本文中的 [範例 3](#ex3) 。</span><span class="sxs-lookup"><span data-stu-id="4da1b-202">For more information see [Example 3](#ex3) in this article.</span></span>

## <span data-ttu-id="4da1b-203">相關連結</span><span class="sxs-lookup"><span data-stu-id="4da1b-203">Related links</span></span>

[<span data-ttu-id="4da1b-204">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="4da1b-204">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="4da1b-205">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="4da1b-205">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="4da1b-206">Group-Object</span><span class="sxs-lookup"><span data-stu-id="4da1b-206">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="4da1b-207">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="4da1b-207">Measure-Object</span></span>](Measure-Object.md)

[<span data-ttu-id="4da1b-208">New-Object</span><span class="sxs-lookup"><span data-stu-id="4da1b-208">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="4da1b-209">Select-Object</span><span class="sxs-lookup"><span data-stu-id="4da1b-209">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="4da1b-210">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="4da1b-210">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="4da1b-211">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="4da1b-211">Tee-Object</span></span>](Tee-Object.md)

[<span data-ttu-id="4da1b-212">Where-Object</span><span class="sxs-lookup"><span data-stu-id="4da1b-212">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)

[<span data-ttu-id="4da1b-213">Get-Process</span><span class="sxs-lookup"><span data-stu-id="4da1b-213">Get-Process</span></span>](../Microsoft.PowerShell.Management/Get-Process.md)
