---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-Object
ms.openlocfilehash: 5c27421180131562c6a2a1fe24d1a8203f4a9828
ms.sourcegitcommit: f9ae48d026d65833b9c8ca881058dda0bbd067b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2020
ms.locfileid: "93206332"
---
# <span data-ttu-id="28b70-103">Select-Object</span><span class="sxs-lookup"><span data-stu-id="28b70-103">Select-Object</span></span>

## <span data-ttu-id="28b70-104">概要</span><span class="sxs-lookup"><span data-stu-id="28b70-104">SYNOPSIS</span></span>
<span data-ttu-id="28b70-105">選取物件或物件屬性。</span><span class="sxs-lookup"><span data-stu-id="28b70-105">Selects objects or object properties.</span></span>

## <span data-ttu-id="28b70-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="28b70-106">SYNTAX</span></span>

### <span data-ttu-id="28b70-107">DefaultParameter (預設) </span><span class="sxs-lookup"><span data-stu-id="28b70-107">DefaultParameter (Default)</span></span>

```
Select-Object [-InputObject <PSObject>] [[-Property] <Object[]>] [-ExcludeProperty <String[]>]
 [-ExpandProperty <String>] [-Unique] [-Last <Int32>] [-First <Int32>] [-Skip <Int32>] [-Wait]
 [<CommonParameters>]
```

### <span data-ttu-id="28b70-108">SkipLastParameter</span><span class="sxs-lookup"><span data-stu-id="28b70-108">SkipLastParameter</span></span>

```
Select-Object [-InputObject <PSObject>] [[-Property] <Object[]>] [-ExcludeProperty <String[]>]
 [-ExpandProperty <String>] [-Unique] [-SkipLast <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="28b70-109">IndexParameter</span><span class="sxs-lookup"><span data-stu-id="28b70-109">IndexParameter</span></span>

```
Select-Object [-InputObject <PSObject>] [-Unique] [-Wait] [-Index <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="28b70-110">SkipIndexParameter</span><span class="sxs-lookup"><span data-stu-id="28b70-110">SkipIndexParameter</span></span>

```
Select-Object [-InputObject <PSObject>] [-Unique] [-SkipIndex <Int32[]>] [<CommonParameters>]
```

## <span data-ttu-id="28b70-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="28b70-111">DESCRIPTION</span></span>

<span data-ttu-id="28b70-112">`Select-Object`Cmdlet 會選取物件或物件集合的指定屬性。</span><span class="sxs-lookup"><span data-stu-id="28b70-112">The `Select-Object` cmdlet selects specified properties of an object or set of objects.</span></span> <span data-ttu-id="28b70-113">它也可以選取唯一物件、指定數目的物件，或位於陣列中指定位置的物件。</span><span class="sxs-lookup"><span data-stu-id="28b70-113">It can also select unique objects, a specified number of objects, or objects in a specified position in an array.</span></span>

<span data-ttu-id="28b70-114">若要從集合選取物件，請使用 **First** 、 **Last** 、 **Unique** 、 **Skip** 及 **Index** 參數。</span><span class="sxs-lookup"><span data-stu-id="28b70-114">To select objects from a collection, use the **First** , **Last** , **Unique** , **Skip** , and **Index** parameters.</span></span> <span data-ttu-id="28b70-115">若要選取物件屬性，請使用 **Property** 參數。</span><span class="sxs-lookup"><span data-stu-id="28b70-115">To select object properties, use the **Property** parameter.</span></span> <span data-ttu-id="28b70-116">當您選取 [屬性] 時，會傳回 `Select-Object` 只具有指定屬性的新物件。</span><span class="sxs-lookup"><span data-stu-id="28b70-116">When you select properties, `Select-Object` returns new objects that have only the specified properties.</span></span>

<span data-ttu-id="28b70-117">從 Windows PowerShell 3.0 開始， `Select-Object` 包含優化功能，可防止命令建立及處理未使用的物件。</span><span class="sxs-lookup"><span data-stu-id="28b70-117">Beginning in Windows PowerShell 3.0, `Select-Object` includes an optimization feature that prevents commands from creating and processing objects that are not used.</span></span>

<span data-ttu-id="28b70-118">當您 `Select-Object` 在命令管線中包含具有 **First** 或 **Index** 參數的命令時，PowerShell 會在所選物件數目產生時立即停止產生物件的命令，即使在管線的命令之前出現產生物件的命令 `Select-Object` 。</span><span class="sxs-lookup"><span data-stu-id="28b70-118">When you include a `Select-Object` command with the **First** or **Index** parameters in a command pipeline, PowerShell stops the command that generates the objects as soon as the selected number of objects is generated, even when the command that generates the objects appears before the `Select-Object` command in the pipeline.</span></span> <span data-ttu-id="28b70-119">若要關閉此最佳化行為，請使用 **Wait** 參數。</span><span class="sxs-lookup"><span data-stu-id="28b70-119">To turn off this optimizing behavior, use the **Wait** parameter.</span></span>

## <span data-ttu-id="28b70-120">範例</span><span class="sxs-lookup"><span data-stu-id="28b70-120">EXAMPLES</span></span>

### <span data-ttu-id="28b70-121">範例1：依屬性選取物件</span><span class="sxs-lookup"><span data-stu-id="28b70-121">Example 1: Select objects by property</span></span>

<span data-ttu-id="28b70-122">這個範例會建立物件，而這些物件的 **名稱** 、 **識別碼** 及工作集 ( **WS** ) 處理常式物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="28b70-122">This example creates objects that have the **Name** , **ID** , and working set ( **WS** ) properties of process objects.</span></span>

```powershell
Get-Process | Select-Object -Property ProcessName, Id, WS
```

### <span data-ttu-id="28b70-123">範例2：依屬性選取物件並設定結果格式</span><span class="sxs-lookup"><span data-stu-id="28b70-123">Example 2: Select objects by property and format the results</span></span>

<span data-ttu-id="28b70-124">此範例會取得電腦上處理常式所使用之模組的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="28b70-124">This example gets information about the modules used by the processes on the computer.</span></span> <span data-ttu-id="28b70-125">它會使用 `Get-Process` Cmdlet 來取得電腦上的處理常式。</span><span class="sxs-lookup"><span data-stu-id="28b70-125">It uses `Get-Process` cmdlet to get the process on the computer.</span></span>

<span data-ttu-id="28b70-126">它會使用 `Select-Object` Cmdlet 來輸出實例的陣列， `[System.Diagnostics.ProcessModule]` 如每個實例輸出的 **模組** 屬性中所包含 `System.Diagnostics.Process` `Get-Process` 。</span><span class="sxs-lookup"><span data-stu-id="28b70-126">It uses the `Select-Object` cmdlet to output an array of `[System.Diagnostics.ProcessModule]` instances as contained in the **Modules** property of each `System.Diagnostics.Process` instance output by `Get-Process`.</span></span>

<span data-ttu-id="28b70-127">Cmdlet 的 **Property** 參數會 `Select-Object` 選取處理常式名稱。</span><span class="sxs-lookup"><span data-stu-id="28b70-127">The **Property** parameter of the `Select-Object` cmdlet selects the process names.</span></span> <span data-ttu-id="28b70-128">這會將 `ProcessName` **NoteProperty** 加入至每個 `[System.Diagnostics.ProcessModule]` 實例，並在其中填入目前進程的 **ProcessName** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="28b70-128">This adds a `ProcessName` **NoteProperty** to every `[System.Diagnostics.ProcessModule]` instance and populates it with the value of current process's **ProcessName** property.</span></span>

<span data-ttu-id="28b70-129">最後， `Format-List` Cmdlet 會用來顯示清單中每個處理常式的名稱和模組。</span><span class="sxs-lookup"><span data-stu-id="28b70-129">Finally, `Format-List` cmdlet is used to display the name and modules of each process in a list.</span></span>

```powershell
Get-Process Explorer | Select-Object -Property ProcessName -ExpandProperty Modules | Format-List
```

```Output
ProcessName       : explorer
ModuleName        : explorer.exe
FileName          : C:\WINDOWS\explorer.exe
BaseAddress       : 140697278152704
ModuleMemorySize  : 3919872
EntryPointAddress : 140697278841168
FileVersionInfo   : File:             C:\WINDOWS\explorer.exe
                    InternalName:     explorer
                    OriginalFilename: EXPLORER.EXE.MUI
                    FileVersion:      10.0.17134.1 (WinBuild.160101.0800)
                    FileDescription:  Windows Explorer
                    Product:          Microsoft Windows Operating System
                    ProductVersion:   10.0.17134.1
...
```

### <span data-ttu-id="28b70-130">範例3：使用最多記憶體選取進程</span><span class="sxs-lookup"><span data-stu-id="28b70-130">Example 3: Select processes using the most memory</span></span>

<span data-ttu-id="28b70-131">這個範例會取得使用最多記憶體的五個處理常式。</span><span class="sxs-lookup"><span data-stu-id="28b70-131">This example gets the five processes that are using the most memory.</span></span> <span data-ttu-id="28b70-132">`Get-Process`Cmdlet 會取得電腦上的處理常式。</span><span class="sxs-lookup"><span data-stu-id="28b70-132">The `Get-Process` cmdlet gets the processes on the computer.</span></span> <span data-ttu-id="28b70-133">指令程式會 `Sort-Object` 根據記憶體 (工作集) 使用方式來排序處理常式，而此 `Select-Object` Cmdlet 只會選取產生之物件陣列的最後五個成員。</span><span class="sxs-lookup"><span data-stu-id="28b70-133">The `Sort-Object` cmdlet sorts the processes according to memory (working set) usage, and the `Select-Object` cmdlet selects only the last five members of the resulting array of objects.</span></span>

<span data-ttu-id="28b70-134">包含 Cmdlet 的命令中不需要 **Wait** 參數， `Sort-Object` 因為會 `Sort-Object` 處理所有物件，然後傳回集合。</span><span class="sxs-lookup"><span data-stu-id="28b70-134">The **Wait** parameter is not required in commands that include the `Sort-Object` cmdlet because `Sort-Object` processes all objects and then returns a collection.</span></span> <span data-ttu-id="28b70-135">`Select-Object`優化只適用于在處理時個別傳回物件的命令。</span><span class="sxs-lookup"><span data-stu-id="28b70-135">The `Select-Object` optimization is available only for commands that return objects individually as they are processed.</span></span>

```powershell
Get-Process | Sort-Object -Property WS | Select-Object -Last 5
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VS(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
2866     320       33432      45764   203   222.41   1292 svchost
577      17        23676      50516   265    50.58   4388 WINWORD
826      11        75448      76712   188    19.77   3780 Ps
1367     14        73152      88736   216    61.69    676 Ps
1612     44        66080      92780   380   900.59   6132 INFOPATH
```

### <span data-ttu-id="28b70-136">範例4：選取陣列中的唯一字元</span><span class="sxs-lookup"><span data-stu-id="28b70-136">Example 4: Select unique characters from an array</span></span>

<span data-ttu-id="28b70-137">這個範例使用的 **unique** 參數 `Select-Object` ，從字元陣列取得唯一字元。</span><span class="sxs-lookup"><span data-stu-id="28b70-137">This example uses the **Unique** parameter of `Select-Object` to get unique characters from an array of characters.</span></span>

```powershell
"a","b","c","a","a","a" | Select-Object -Unique
```

```Output
a
b
c
```

### <span data-ttu-id="28b70-138">範例5：在事件記錄檔中選取最新和最舊的事件</span><span class="sxs-lookup"><span data-stu-id="28b70-138">Example 5: Select newest and oldest events in the event log</span></span>

<span data-ttu-id="28b70-139">此範例會取得 Windows PowerShell 事件記錄檔中的第一個 (最新) 和最後 (最舊的) 事件。</span><span class="sxs-lookup"><span data-stu-id="28b70-139">This example gets the first (newest) and last (oldest) events in the Windows PowerShell event log.</span></span>

<span data-ttu-id="28b70-140">`Get-EventLog` 取得 Windows PowerShell 記錄檔中的所有事件，並將它們儲存在 `$a` 變數中。</span><span class="sxs-lookup"><span data-stu-id="28b70-140">`Get-EventLog` gets all events in the Windows PowerShell log and saves them in the `$a` variable.</span></span>
<span data-ttu-id="28b70-141">然後， `$a` 會透過管道傳送至 `Select-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="28b70-141">Then, `$a` is piped to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="28b70-142">此 `Select-Object` 命令會使用 **Index** 參數，從變數中的事件陣列選取事件 `$a` 。</span><span class="sxs-lookup"><span data-stu-id="28b70-142">The `Select-Object` command uses the **Index** parameter to select events from the array of events in the `$a` variable.</span></span> <span data-ttu-id="28b70-143">第一個事件的索引為 0。</span><span class="sxs-lookup"><span data-stu-id="28b70-143">The index of the first event is 0.</span></span> <span data-ttu-id="28b70-144">最後一個事件的索引是減1的專案數目 `$a` 。</span><span class="sxs-lookup"><span data-stu-id="28b70-144">The index of the last event is the number of items in `$a` minus 1.</span></span>

```powershell
$a = Get-EventLog -LogName "Windows PowerShell"
$a | Select-Object -Index 0, ($A.count - 1)
```

### <span data-ttu-id="28b70-145">範例6：選取第一個物件以外的所有物件</span><span class="sxs-lookup"><span data-stu-id="28b70-145">Example 6: Select all but the first object</span></span>

<span data-ttu-id="28b70-146">這個範例會在 Servers.txt 檔案中列出的每一部電腦上建立新的 PSSession，除了第一部電腦之外。</span><span class="sxs-lookup"><span data-stu-id="28b70-146">This example creates a new PSSession on each of the computers listed in the Servers.txt files, except for the first one.</span></span>

<span data-ttu-id="28b70-147">`Select-Object` 選取電腦名稱稱清單中的所有電腦，但不選取第一部電腦。</span><span class="sxs-lookup"><span data-stu-id="28b70-147">`Select-Object` selects all but the first computer in a list of computer names.</span></span> <span data-ttu-id="28b70-148">產生的電腦清單會設定為 Cmdlet 的 **ComputerName** 參數值 `New-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="28b70-148">The resulting list of computers is set as the value of the **ComputerName** parameter of the `New-PSSession` cmdlet.</span></span>

```powershell
New-PSSession -ComputerName (Get-Content Servers.txt | Select-Object -Skip 1)
```

### <span data-ttu-id="28b70-149">範例7：重新命名檔案，然後選取多個以進行審核</span><span class="sxs-lookup"><span data-stu-id="28b70-149">Example 7: Rename files and select several to review</span></span>

<span data-ttu-id="28b70-150">此範例會將 "-ro" 尾碼新增至具有唯讀屬性之文字檔的基底名稱，然後顯示前五個檔案，讓使用者可以看到效果的範例。</span><span class="sxs-lookup"><span data-stu-id="28b70-150">This example adds a "-ro" suffix to the base names of text files that have the read-only attribute and then displays the first five files so the user can see a sample of the effect.</span></span>

<span data-ttu-id="28b70-151">`Get-ChildItem` 使用 **ReadOnly** 動態參數來取得唯讀檔案。</span><span class="sxs-lookup"><span data-stu-id="28b70-151">`Get-ChildItem` uses the **ReadOnly** dynamic parameter to get read-only files.</span></span> <span data-ttu-id="28b70-152">產生的檔案會以管道傳送至 `Rename-Item` Cmdlet，以重新命名檔案。</span><span class="sxs-lookup"><span data-stu-id="28b70-152">The resulting files are piped to the `Rename-Item` cmdlet, which renames the file.</span></span> <span data-ttu-id="28b70-153">它使用的 **Passthru** 參數將重新 `Rename-Item` 命名的檔案傳送至 `Select-Object` Cmdlet，此 Cmdlet 會選取前5個來顯示。</span><span class="sxs-lookup"><span data-stu-id="28b70-153">It uses the **Passthru** parameter of `Rename-Item` to send the renamed files to the `Select-Object` cmdlet, which selects the first 5 for display.</span></span>

<span data-ttu-id="28b70-154">的 **Wait** 參數 `Select-Object` 會防止 PowerShell 在 `Get-ChildItem` 取得前五個唯讀文字檔之後停止 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="28b70-154">The **Wait** parameter of `Select-Object` prevents PowerShell from stopping the `Get-ChildItem` cmdlet after it gets the first five read-only text files.</span></span> <span data-ttu-id="28b70-155">在沒有此參數的情況下，只會重新命名前五個唯讀檔案。</span><span class="sxs-lookup"><span data-stu-id="28b70-155">Without this parameter, only the first five read-only files would be renamed.</span></span>

```powershell
Get-ChildItem *.txt -ReadOnly |
    Rename-Item -NewName {$_.BaseName + "-ro.txt"} -PassThru |
    Select-Object -First 5 -Wait
```

### <span data-ttu-id="28b70-156">範例8：示範-ExpandProperty 參數的複雜</span><span class="sxs-lookup"><span data-stu-id="28b70-156">Example 8: Demonstrate the intricacies of the -ExpandProperty parameter</span></span>

<span data-ttu-id="28b70-157">此範例示範 **ExpandProperty** 參數的複雜。</span><span class="sxs-lookup"><span data-stu-id="28b70-157">This example demonstrates the intricacies of the **ExpandProperty** parameter.</span></span>

<span data-ttu-id="28b70-158">請注意，產生的輸出是實例的陣列 `[System.Int32]` 。</span><span class="sxs-lookup"><span data-stu-id="28b70-158">Note that the output generated was an array of `[System.Int32]` instances.</span></span> <span data-ttu-id="28b70-159">實例符合 **輸出視圖** 的標準格式化規則。</span><span class="sxs-lookup"><span data-stu-id="28b70-159">The instances conform to standard formatting rules of the **Output View** .</span></span> <span data-ttu-id="28b70-160">這適用于任何 *展開* 的屬性。</span><span class="sxs-lookup"><span data-stu-id="28b70-160">This is true for any *Expanded* properties.</span></span> <span data-ttu-id="28b70-161">如果輸出的物件具有特定的標準格式，則可能不會顯示展開的屬性。</span><span class="sxs-lookup"><span data-stu-id="28b70-161">If the outputted objects have a specific standard format, the expanded property might not be visible.</span></span>

```powershell
# Create a custom object to use for the Select-Object example.
$object = [pscustomobject]@{Name="CustomObject";Expand=@(1,2,3,4,5)}
# Use the ExpandProperty parameter to Expand the property.
$object | Select-Object -ExpandProperty Expand -Property Name
```

```Output
1
2
3
4
5
```

```powershell
# The output did not contain the Name property, but it was added successfully.
# Use Get-Member to confirm the Name property was added and populated.
$object | Select-Object -ExpandProperty Expand -Property Name | Get-Member
```

```Output
   TypeName: System.Int32

Name        MemberType   Definition
----        ----------   ----------
CompareTo   Method       int CompareTo(System.Object value), int CompareTo(int value), int IComparable.CompareTo(System.Object obj)...
Equals      Method       bool Equals(System.Object obj), bool Equals(int obj), bool IEquatable[int].Equals(int other)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
GetTypeCode Method       System.TypeCode GetTypeCode(), System.TypeCode IConvertible.GetTypeCode()
ToBoolean   Method       bool IConvertible.ToBoolean(System.IFormatProvider provider)
ToByte      Method       byte IConvertible.ToByte(System.IFormatProvider provider)
ToChar      Method       char IConvertible.ToChar(System.IFormatProvider provider)
ToDateTime  Method       datetime IConvertible.ToDateTime(System.IFormatProvider provider)
ToDecimal   Method       decimal IConvertible.ToDecimal(System.IFormatProvider provider)
ToDouble    Method       double IConvertible.ToDouble(System.IFormatProvider provider)
ToInt16     Method       int16 IConvertible.ToInt16(System.IFormatProvider provider)
ToInt32     Method       int IConvertible.ToInt32(System.IFormatProvider provider)
ToInt64     Method       long IConvertible.ToInt64(System.IFormatProvider provider)
ToSByte     Method       sbyte IConvertible.ToSByte(System.IFormatProvider provider)
ToSingle    Method       float IConvertible.ToSingle(System.IFormatProvider provider)
ToString    Method       string ToString(), string ToString(string format), string ToString(System.IFormatProvider provider)...
ToType      Method       System.Object IConvertible.ToType(type conversionType, System.IFormatProvider provider)
ToUInt16    Method       uint16 IConvertible.ToUInt16(System.IFormatProvider provider)
ToUInt32    Method       uint32 IConvertible.ToUInt32(System.IFormatProvider provider)
ToUInt64    Method       uint64 IConvertible.ToUInt64(System.IFormatProvider provider)
Name        NoteProperty string Name=CustomObject
```

### <span data-ttu-id="28b70-162">範例9：在物件上建立自訂屬性</span><span class="sxs-lookup"><span data-stu-id="28b70-162">Example 9: Create custom properties on objects</span></span>

<span data-ttu-id="28b70-163">下列範例示範如何使用將 `Select-Object` 自訂屬性加入至任何物件。</span><span class="sxs-lookup"><span data-stu-id="28b70-163">The following example demonstrates using `Select-Object` to add a custom property to any object.</span></span>
<span data-ttu-id="28b70-164">當您指定不存在的屬性名稱時，會 `Select-Object` 將該屬性建立為每個傳遞之物件上的 **NoteProperty** 。</span><span class="sxs-lookup"><span data-stu-id="28b70-164">When you specify a property name that does not exist, `Select-Object` creates that property as a **NoteProperty** on each object passed.</span></span>

```powershell
$customObject = 1 | Select-Object -Property MyCustomProperty
$customObject.MyCustomProperty = "New Custom Property"
$customObject
```

```Output
MyCustomProperty
----------------
New Custom Property
```

### <span data-ttu-id="28b70-165">範例10：為每個 InputObject 建立計算屬性</span><span class="sxs-lookup"><span data-stu-id="28b70-165">Example 10: Create calculated properties for each InputObject</span></span>

<span data-ttu-id="28b70-166">這個範例示範 `Select-Object` 如何使用，將計算屬性加入至您的輸入。</span><span class="sxs-lookup"><span data-stu-id="28b70-166">This example demonstrates using `Select-Object` to add calculated properties to your input.</span></span> <span data-ttu-id="28b70-167">將 **ScriptBlock** 傳遞給 **Property** 參數會導致 `Select-Object` 在每個傳遞的物件上評估運算式，並將結果新增至輸出。</span><span class="sxs-lookup"><span data-stu-id="28b70-167">Passing a **ScriptBlock** to the **Property** parameter causes `Select-Object` to evaluate the expression on each object passed and add the results to the output.</span></span> <span data-ttu-id="28b70-168">在 **ScriptBlock** 內，您可以使用 `$_` 變數來參考管線中的目前物件。</span><span class="sxs-lookup"><span data-stu-id="28b70-168">Within the **ScriptBlock** , you can use the `$_` variable to reference the current object in the pipeline.</span></span>

<span data-ttu-id="28b70-169">依預設， `Select-Object` 會使用 **ScriptBlock** 字串做為屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="28b70-169">By default, `Select-Object` will use the **ScriptBlock** string as the name of the property.</span></span> <span data-ttu-id="28b70-170">使用 **雜湊表** ，您可以將 **ScriptBlock** 的輸出標記為新增至每個物件的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="28b70-170">Using a **Hashtable** , you can label the output of your **ScriptBlock** as a custom property added to each object.</span></span> <span data-ttu-id="28b70-171">您可以將多個計算屬性加入至傳遞給的每個物件 `Select-Object` 。</span><span class="sxs-lookup"><span data-stu-id="28b70-171">You can add multiple calculated properties to each object passed to `Select-Object`.</span></span>

```powershell
# Create a calculated property called $_.StartTime.DayOfWeek
Get-Process | Select-Object -Property ProcessName,{$_.StartTime.DayOfWeek}
```

```Output
ProcessName  $_.StartTime.DayOfWeek
----         ----------------------
alg                       Wednesday
ati2evxx                  Wednesday
ati2evxx                   Thursday
...
```

```powershell
# Add a custom property to calculate the size in KiloBytes of each FileInfo object you pass in.
# Use the pipeline variable to divide each file's length by 1 KiloBytes
$size = @{label="Size(KB)";expression={$_.length/1KB}}
# Create an additional calculated property with the number of Days since the file was last accessed.
# You can also shorten the key names to be 'l', and 'e', or use Name instead of Label.
$days = @{l="Days";e={((Get-Date) - $_.LastAccessTime).Days}}
# You can also shorten the name of your label key to 'l' and your expression key to 'e'.
Get-ChildItem $PSHOME -File | Select-Object Name, $size, $days
```

```Output
Name                        Size(KB)        Days
----                        --------        ----
Certificate.format.ps1xml   12.5244140625   223
Diagnostics.Format.ps1xml   4.955078125     223
DotNetTypes.format.ps1xml   134.9833984375  223
```

## <span data-ttu-id="28b70-172">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="28b70-172">PARAMETERS</span></span>

### <span data-ttu-id="28b70-173">-ExcludeProperty</span><span class="sxs-lookup"><span data-stu-id="28b70-173">-ExcludeProperty</span></span>

<span data-ttu-id="28b70-174">指定此 Cmdlet 從作業中排除的屬性。</span><span class="sxs-lookup"><span data-stu-id="28b70-174">Specifies the properties that this cmdlet excludes from the operation.</span></span> <span data-ttu-id="28b70-175">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="28b70-175">Wildcards are permitted.</span></span>

<span data-ttu-id="28b70-176">從 PowerShell 6 開始，不再需要包含 **Property** 參數， **ExcludeProperty** 才能運作。</span><span class="sxs-lookup"><span data-stu-id="28b70-176">Beginning in PowerShell 6, it is no longer required to include the **Property** parameter for **ExcludeProperty** to work.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="28b70-177">-ExpandProperty</span><span class="sxs-lookup"><span data-stu-id="28b70-177">-ExpandProperty</span></span>

<span data-ttu-id="28b70-178">請指定要選取的屬性，並指示應嘗試延伸該屬性。</span><span class="sxs-lookup"><span data-stu-id="28b70-178">Specifies a property to select, and indicates that an attempt should be made to expand that property.</span></span>

- <span data-ttu-id="28b70-179">如果指定的屬性是陣列，則陣列的每個值都會包含在輸出中。</span><span class="sxs-lookup"><span data-stu-id="28b70-179">If the specified property is an array, each value of the array is included in the output.</span></span>
- <span data-ttu-id="28b70-180">如果指定的屬性是物件，則會針對每個 **InputObject** 展開物件屬性</span><span class="sxs-lookup"><span data-stu-id="28b70-180">If the specified property is an object, the objects properties are expanded for every **InputObject**</span></span>

<span data-ttu-id="28b70-181">無論是哪一種情況，輸出物件的 **類型** 都將符合展開屬性的 **類型** 。</span><span class="sxs-lookup"><span data-stu-id="28b70-181">In either case, the **Type** of objects output will match the **Type** of the expanded property.</span></span>

<span data-ttu-id="28b70-182">如果指定了 **Property** 參數， `Select-Object` 將會嘗試將每個選取的屬性新增為每個輸出物件的 **NoteProperty** 。</span><span class="sxs-lookup"><span data-stu-id="28b70-182">If the **Property** parameter is specified, `Select-Object` will attempt to add each selected property as a **NoteProperty** to every outputted object.</span></span>

> [!WARNING]
> <span data-ttu-id="28b70-183">如果您收到錯誤：因為屬性已存在，所以無法處理 Select： Property `<PropertyName>` ，請考慮下列事項。</span><span class="sxs-lookup"><span data-stu-id="28b70-183">If you receive the error: Select : Property cannot be processed because property `<PropertyName>` already exists, consider the following.</span></span>
> <span data-ttu-id="28b70-184">請注意，使用時 `-ExpandProperty` ， `Select-Object` 不能取代現有的屬性。</span><span class="sxs-lookup"><span data-stu-id="28b70-184">Note that when using `-ExpandProperty`, `Select-Object` can not replace an existing property.</span></span>
> <span data-ttu-id="28b70-185">這表示：</span><span class="sxs-lookup"><span data-stu-id="28b70-185">This means:</span></span>
>
> - <span data-ttu-id="28b70-186">如果展開的物件具有相同名稱的屬性，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="28b70-186">If the expanded object has a property of the same name, an error will occur.</span></span>
> - <span data-ttu-id="28b70-187">如果 *選取* 的物件具有與 *展開* 物件屬性相同名稱的屬性，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="28b70-187">If the *Selected* object has a property of the same name as an *Expanded* objects property, an error will occur.</span></span>

```yaml
Type: System.String
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="28b70-188">-First</span><span class="sxs-lookup"><span data-stu-id="28b70-188">-First</span></span>

<span data-ttu-id="28b70-189">指定要從輸入物件陣列開始位置選取的物件數。</span><span class="sxs-lookup"><span data-stu-id="28b70-189">Specifies the number of objects to select from the beginning of an array of input objects.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="28b70-190">-Index</span><span class="sxs-lookup"><span data-stu-id="28b70-190">-Index</span></span>

<span data-ttu-id="28b70-191">依據物件的索引值從陣列選取物件。</span><span class="sxs-lookup"><span data-stu-id="28b70-191">Selects objects from an array based on their index values.</span></span> <span data-ttu-id="28b70-192">在使用逗號區隔的清單中輸入索引。</span><span class="sxs-lookup"><span data-stu-id="28b70-192">Enter the indexes in a comma-separated list.</span></span> <span data-ttu-id="28b70-193">陣列中的索引是以 0 開始，其中 0 代表第一個值，(n-1) 則代表最後一個值。</span><span class="sxs-lookup"><span data-stu-id="28b70-193">Indexes in an array begin with 0, where 0 represents the first value and (n-1) represents the last value.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: IndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="28b70-194">-InputObject</span><span class="sxs-lookup"><span data-stu-id="28b70-194">-InputObject</span></span>

<span data-ttu-id="28b70-195">指定要透過管線傳送給 Cmdlet 的物件。</span><span class="sxs-lookup"><span data-stu-id="28b70-195">Specifies objects to send to the cmdlet through the pipeline.</span></span> <span data-ttu-id="28b70-196">此參數可讓您將物件輸送至 `Select-Object` 。</span><span class="sxs-lookup"><span data-stu-id="28b70-196">This parameter enables you to pipe objects to `Select-Object`.</span></span>

<span data-ttu-id="28b70-197">當您將物件傳遞給 **inputobject** 參數時（而不是使用管線）， `Select-Object` 會將 **InputObject** 視為單一物件（即使值是集合）。</span><span class="sxs-lookup"><span data-stu-id="28b70-197">When you pass objects to the **InputObject** parameter, instead of using the pipeline, `Select-Object` treats the **InputObject** as a single object, even if the value is a collection.</span></span> <span data-ttu-id="28b70-198">建議您在將集合傳遞至時，使用管線 `Select-Object` 。</span><span class="sxs-lookup"><span data-stu-id="28b70-198">It is recommended that you use the pipeline when passing collections to `Select-Object`.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="28b70-199">-Last</span><span class="sxs-lookup"><span data-stu-id="28b70-199">-Last</span></span>

<span data-ttu-id="28b70-200">指定要從輸入物件陣列結束位置選取的物件數。</span><span class="sxs-lookup"><span data-stu-id="28b70-200">Specifies the number of objects to select from the end of an array of input objects.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="28b70-201">-Property</span><span class="sxs-lookup"><span data-stu-id="28b70-201">-Property</span></span>

<span data-ttu-id="28b70-202">指定要選取的屬性。</span><span class="sxs-lookup"><span data-stu-id="28b70-202">Specifies the properties to select.</span></span> <span data-ttu-id="28b70-203">這些屬性會以 **NoteProperty** 成員的形式新增至輸出物件。</span><span class="sxs-lookup"><span data-stu-id="28b70-203">These properties are added as **NoteProperty** members to the output objects.</span></span> <span data-ttu-id="28b70-204">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="28b70-204">Wildcards are permitted.</span></span>

<span data-ttu-id="28b70-205">**Property** 參數的值可以是新的計算屬性。</span><span class="sxs-lookup"><span data-stu-id="28b70-205">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="28b70-206">若要建立計算的屬性，請使用雜湊表。</span><span class="sxs-lookup"><span data-stu-id="28b70-206">To create a calculated, property, use a hash table.</span></span>

<span data-ttu-id="28b70-207">有效索引鍵為：</span><span class="sxs-lookup"><span data-stu-id="28b70-207">Valid keys are:</span></span>

- <span data-ttu-id="28b70-208">名稱 (或標籤) - `<string>`</span><span class="sxs-lookup"><span data-stu-id="28b70-208">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="28b70-209">運算式 `<string>` 或 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="28b70-209">Expression - `<string>` or `<script block>`</span></span>

<span data-ttu-id="28b70-210">如需詳細資訊，請參閱 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。</span><span class="sxs-lookup"><span data-stu-id="28b70-210">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="28b70-211">-Skip</span><span class="sxs-lookup"><span data-stu-id="28b70-211">-Skip</span></span>

<span data-ttu-id="28b70-212">略過 (不選取) 指定的項目數。</span><span class="sxs-lookup"><span data-stu-id="28b70-212">Skips (does not select) the specified number of items.</span></span> <span data-ttu-id="28b70-213">根據預設， **Skip** 參數會從物件陣列或清單的開頭開始計算，但是如果命令使用 **最後一個** 參數，就會從清單或陣列的結尾算起。</span><span class="sxs-lookup"><span data-stu-id="28b70-213">By default, the **Skip** parameter counts from the beginning of the array or list of objects, but if the command uses the **Last** parameter, it counts from the end of the list or array.</span></span>

<span data-ttu-id="28b70-214">與從 0 位置開始計算的 **Index** 參數不同， **Skip** 參數會從 1 開始。</span><span class="sxs-lookup"><span data-stu-id="28b70-214">Unlike the **Index** parameter, which starts counting at 0, the **Skip** parameter begins at 1.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="28b70-215">-SkipLast</span><span class="sxs-lookup"><span data-stu-id="28b70-215">-SkipLast</span></span>

<span data-ttu-id="28b70-216">略過 (不會從清單或陣列的結尾選取) 指定數目的專案。</span><span class="sxs-lookup"><span data-stu-id="28b70-216">Skips (does not select) the specified number of items from the end of the list or array.</span></span> <span data-ttu-id="28b70-217">的運作方式與使用 **Skip** 搭配 **Last** 參數的方式相同。</span><span class="sxs-lookup"><span data-stu-id="28b70-217">Works in the same way as using **Skip** together with **Last** parameter.</span></span>

<span data-ttu-id="28b70-218">不同于從0開始計算的 **Index** 參數， **SkipLast** 參數會從1開始。</span><span class="sxs-lookup"><span data-stu-id="28b70-218">Unlike the **Index** parameter, which starts counting at 0, the **SkipLast** parameter begins at 1.</span></span>

```yaml
Type: System.Int32
Parameter Sets: SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="28b70-219">-Unique</span><span class="sxs-lookup"><span data-stu-id="28b70-219">-Unique</span></span>

<span data-ttu-id="28b70-220">指定當輸入物件的子集具有完全相同的屬性與值，將只會選取子集的一個成員。</span><span class="sxs-lookup"><span data-stu-id="28b70-220">Specifies that if a subset of the input objects has identical properties and values, only a single member of the subset will be selected.</span></span>

<span data-ttu-id="28b70-221">此參數區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="28b70-221">This parameter is case-sensitive.</span></span> <span data-ttu-id="28b70-222">因此，只有字元大小寫不同的字串會被視為唯一的字串。</span><span class="sxs-lookup"><span data-stu-id="28b70-222">As a result, strings that differ only in character casing are considered to be unique.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="28b70-223">-Wait</span><span class="sxs-lookup"><span data-stu-id="28b70-223">-Wait</span></span>

<span data-ttu-id="28b70-224">指出此 Cmdlet 會關閉優化。</span><span class="sxs-lookup"><span data-stu-id="28b70-224">Indicates that the cmdlet turns off optimization.</span></span> <span data-ttu-id="28b70-225">PowerShell 會以命令在命令管線中出現的循序執行命令，並讓它們產生所有物件。</span><span class="sxs-lookup"><span data-stu-id="28b70-225">PowerShell runs commands in the order that they appear in the command pipeline and lets them generate all objects.</span></span> <span data-ttu-id="28b70-226">根據預設，如果您 `Select-Object` 在命令管線中包含具有 **First** 或 **Index** 參數的命令，則 PowerShell 會在產生選取的物件數目時，停止產生物件的命令。</span><span class="sxs-lookup"><span data-stu-id="28b70-226">By default, if you include a `Select-Object` command with the **First** or **Index** parameters in a command pipeline, PowerShell stops the command that generates the objects as soon as the selected number of objects is generated.</span></span>

<span data-ttu-id="28b70-227">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="28b70-227">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DefaultParameter, IndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="28b70-228">-SkipIndex</span><span class="sxs-lookup"><span data-stu-id="28b70-228">-SkipIndex</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: SkipIndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="28b70-229">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="28b70-229">CommonParameters</span></span>

<span data-ttu-id="28b70-230">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="28b70-230">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="28b70-231">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="28b70-231">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="28b70-232">輸入</span><span class="sxs-lookup"><span data-stu-id="28b70-232">INPUTS</span></span>

### <span data-ttu-id="28b70-233">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="28b70-233">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="28b70-234">您可以透過管線將任何物件傳送至 `Select-Object` 。</span><span class="sxs-lookup"><span data-stu-id="28b70-234">You can pipe any object to `Select-Object`.</span></span>

## <span data-ttu-id="28b70-235">輸出</span><span class="sxs-lookup"><span data-stu-id="28b70-235">OUTPUTS</span></span>

### <span data-ttu-id="28b70-236">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="28b70-236">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="28b70-237">注意</span><span class="sxs-lookup"><span data-stu-id="28b70-237">NOTES</span></span>

- <span data-ttu-id="28b70-238">您也可以 `Select-Object` 使用它的內建別名來參考 Cmdlet `select` 。</span><span class="sxs-lookup"><span data-stu-id="28b70-238">You can also refer to the `Select-Object` cmdlet by its built-in alias, `select`.</span></span> <span data-ttu-id="28b70-239">如需詳細資訊，請參閱 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="28b70-239">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

- <span data-ttu-id="28b70-240">的優化功能 `Select-Object` 僅適用于在處理管線時將物件寫入至管線的命令。</span><span class="sxs-lookup"><span data-stu-id="28b70-240">The optimization feature of `Select-Object` is available only for commands that write objects to the pipeline as they are processed.</span></span> <span data-ttu-id="28b70-241">它對緩衝已處理之物件的命令沒有效果，並且會將它們以集合的方式寫入。</span><span class="sxs-lookup"><span data-stu-id="28b70-241">It has no effect on commands that buffer processed objects and write them as a collection.</span></span> <span data-ttu-id="28b70-242">立即寫入物件是 Cmdlet 設計最佳做法。</span><span class="sxs-lookup"><span data-stu-id="28b70-242">Writing objects immediately is a cmdlet design best practice.</span></span> <span data-ttu-id="28b70-243">如需詳細資訊，請參閱以 [強烈建議的開發指導方針](/powershell/scripting/developer/windows-powershell)，將 _單一記錄寫入管線_ 。</span><span class="sxs-lookup"><span data-stu-id="28b70-243">For more information, see _Write Single Records to the Pipeline_ in [Strongly Encouraged Development Guidelines](/powershell/scripting/developer/windows-powershell).</span></span>

## <span data-ttu-id="28b70-244">相關連結</span><span class="sxs-lookup"><span data-stu-id="28b70-244">RELATED LINKS</span></span>

[<span data-ttu-id="28b70-245">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="28b70-245">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="28b70-246">Group-Object</span><span class="sxs-lookup"><span data-stu-id="28b70-246">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="28b70-247">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="28b70-247">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="28b70-248">Where-Object</span><span class="sxs-lookup"><span data-stu-id="28b70-248">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
