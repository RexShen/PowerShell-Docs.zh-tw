---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-object?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-Object
ms.openlocfilehash: 59cbba88e3c21d740b774d95e7c0e734cd8e3fdc
ms.sourcegitcommit: f9ae48d026d65833b9c8ca881058dda0bbd067b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2020
ms.locfileid: "93206336"
---
# <span data-ttu-id="3de46-103">Select-Object</span><span class="sxs-lookup"><span data-stu-id="3de46-103">Select-Object</span></span>

## <span data-ttu-id="3de46-104">概要</span><span class="sxs-lookup"><span data-stu-id="3de46-104">SYNOPSIS</span></span>
<span data-ttu-id="3de46-105">選取物件或物件屬性。</span><span class="sxs-lookup"><span data-stu-id="3de46-105">Selects objects or object properties.</span></span>

## <span data-ttu-id="3de46-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3de46-106">SYNTAX</span></span>

### <span data-ttu-id="3de46-107">DefaultParameter (預設) </span><span class="sxs-lookup"><span data-stu-id="3de46-107">DefaultParameter (Default)</span></span>

```
Select-Object [-InputObject <PSObject>] [[-Property] <Object[]>] [-ExcludeProperty <String[]>]
 [-ExpandProperty <String>] [-Unique] [-Last <Int32>] [-First <Int32>] [-Skip <Int32>] [-Wait]
 [<CommonParameters>]
```

### <span data-ttu-id="3de46-108">SkipLastParameter</span><span class="sxs-lookup"><span data-stu-id="3de46-108">SkipLastParameter</span></span>

```
Select-Object [-InputObject <PSObject>] [[-Property] <Object[]>] [-ExcludeProperty <String[]>]
 [-ExpandProperty <String>] [-Unique] [-SkipLast <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="3de46-109">IndexParameter</span><span class="sxs-lookup"><span data-stu-id="3de46-109">IndexParameter</span></span>

```
Select-Object [-InputObject <PSObject>] [-Unique] [-Wait] [-Index <Int32[]>] [<CommonParameters>]
```

## <span data-ttu-id="3de46-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3de46-110">DESCRIPTION</span></span>

<span data-ttu-id="3de46-111">`Select-Object`Cmdlet 會選取物件或物件集合的指定屬性。</span><span class="sxs-lookup"><span data-stu-id="3de46-111">The `Select-Object` cmdlet selects specified properties of an object or set of objects.</span></span> <span data-ttu-id="3de46-112">它也可以選取唯一物件、指定數目的物件，或位於陣列中指定位置的物件。</span><span class="sxs-lookup"><span data-stu-id="3de46-112">It can also select unique objects, a specified number of objects, or objects in a specified position in an array.</span></span>

<span data-ttu-id="3de46-113">若要從集合選取物件，請使用 **First** 、 **Last** 、 **Unique** 、 **Skip** 及 **Index** 參數。</span><span class="sxs-lookup"><span data-stu-id="3de46-113">To select objects from a collection, use the **First** , **Last** , **Unique** , **Skip** , and **Index** parameters.</span></span> <span data-ttu-id="3de46-114">若要選取物件屬性，請使用 **Property** 參數。</span><span class="sxs-lookup"><span data-stu-id="3de46-114">To select object properties, use the **Property** parameter.</span></span> <span data-ttu-id="3de46-115">當您選取 [屬性] 時，會傳回 `Select-Object` 只具有指定屬性的新物件。</span><span class="sxs-lookup"><span data-stu-id="3de46-115">When you select properties, `Select-Object` returns new objects that have only the specified properties.</span></span>

<span data-ttu-id="3de46-116">從 Windows PowerShell 3.0 開始， `Select-Object` 包含優化功能，可防止命令建立及處理未使用的物件。</span><span class="sxs-lookup"><span data-stu-id="3de46-116">Beginning in Windows PowerShell 3.0, `Select-Object` includes an optimization feature that prevents commands from creating and processing objects that are not used.</span></span>

<span data-ttu-id="3de46-117">當您 `Select-Object` 在命令管線中包含具有 **First** 或 **Index** 參數的命令時，PowerShell 會在所選物件數目產生時立即停止產生物件的命令，即使在管線的命令之前出現產生物件的命令 `Select-Object` 。</span><span class="sxs-lookup"><span data-stu-id="3de46-117">When you include a `Select-Object` command with the **First** or **Index** parameters in a command pipeline, PowerShell stops the command that generates the objects as soon as the selected number of objects is generated, even when the command that generates the objects appears before the `Select-Object` command in the pipeline.</span></span> <span data-ttu-id="3de46-118">若要關閉此最佳化行為，請使用 **Wait** 參數。</span><span class="sxs-lookup"><span data-stu-id="3de46-118">To turn off this optimizing behavior, use the **Wait** parameter.</span></span>

## <span data-ttu-id="3de46-119">範例</span><span class="sxs-lookup"><span data-stu-id="3de46-119">EXAMPLES</span></span>

### <span data-ttu-id="3de46-120">範例1：依屬性選取物件</span><span class="sxs-lookup"><span data-stu-id="3de46-120">Example 1: Select objects by property</span></span>

<span data-ttu-id="3de46-121">這個範例會建立物件，而這些物件的 **名稱** 、 **識別碼** 及工作集 ( **WS** ) 處理常式物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="3de46-121">This example creates objects that have the **Name** , **ID** , and working set ( **WS** ) properties of process objects.</span></span>

```powershell
Get-Process | Select-Object -Property ProcessName, Id, WS
```

### <span data-ttu-id="3de46-122">範例2：依屬性選取物件並設定結果格式</span><span class="sxs-lookup"><span data-stu-id="3de46-122">Example 2: Select objects by property and format the results</span></span>

<span data-ttu-id="3de46-123">此範例會取得電腦上處理常式所使用之模組的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3de46-123">This example gets information about the modules used by the processes on the computer.</span></span> <span data-ttu-id="3de46-124">它會使用 `Get-Process` Cmdlet 來取得電腦上的處理常式。</span><span class="sxs-lookup"><span data-stu-id="3de46-124">It uses `Get-Process` cmdlet to get the process on the computer.</span></span>

<span data-ttu-id="3de46-125">它會使用 `Select-Object` Cmdlet 來輸出實例的陣列， `[System.Diagnostics.ProcessModule]` 如每個實例輸出的 **模組** 屬性中所包含 `System.Diagnostics.Process` `Get-Process` 。</span><span class="sxs-lookup"><span data-stu-id="3de46-125">It uses the `Select-Object` cmdlet to output an array of `[System.Diagnostics.ProcessModule]` instances as contained in the **Modules** property of each `System.Diagnostics.Process` instance output by `Get-Process`.</span></span>

<span data-ttu-id="3de46-126">Cmdlet 的 **Property** 參數會 `Select-Object` 選取處理常式名稱。</span><span class="sxs-lookup"><span data-stu-id="3de46-126">The **Property** parameter of the `Select-Object` cmdlet selects the process names.</span></span> <span data-ttu-id="3de46-127">這會將 `ProcessName` **NoteProperty** 加入至每個 `[System.Diagnostics.ProcessModule]` 實例，並在其中填入目前進程的 **ProcessName** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="3de46-127">This adds a `ProcessName` **NoteProperty** to every `[System.Diagnostics.ProcessModule]` instance and populates it with the value of current process's **ProcessName** property.</span></span>

<span data-ttu-id="3de46-128">最後， `Format-List` Cmdlet 會用來顯示清單中每個處理常式的名稱和模組。</span><span class="sxs-lookup"><span data-stu-id="3de46-128">Finally, `Format-List` cmdlet is used to display the name and modules of each process in a list.</span></span>

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

### <span data-ttu-id="3de46-129">範例3：使用最多記憶體選取進程</span><span class="sxs-lookup"><span data-stu-id="3de46-129">Example 3: Select processes using the most memory</span></span>

<span data-ttu-id="3de46-130">這個範例會取得使用最多記憶體的五個處理常式。</span><span class="sxs-lookup"><span data-stu-id="3de46-130">This example gets the five processes that are using the most memory.</span></span> <span data-ttu-id="3de46-131">`Get-Process`Cmdlet 會取得電腦上的處理常式。</span><span class="sxs-lookup"><span data-stu-id="3de46-131">The `Get-Process` cmdlet gets the processes on the computer.</span></span> <span data-ttu-id="3de46-132">指令程式會 `Sort-Object` 根據記憶體 (工作集) 使用方式來排序處理常式，而此 `Select-Object` Cmdlet 只會選取產生之物件陣列的最後五個成員。</span><span class="sxs-lookup"><span data-stu-id="3de46-132">The `Sort-Object` cmdlet sorts the processes according to memory (working set) usage, and the `Select-Object` cmdlet selects only the last five members of the resulting array of objects.</span></span>

<span data-ttu-id="3de46-133">包含 Cmdlet 的命令中不需要 **Wait** 參數， `Sort-Object` 因為會 `Sort-Object` 處理所有物件，然後傳回集合。</span><span class="sxs-lookup"><span data-stu-id="3de46-133">The **Wait** parameter is not required in commands that include the `Sort-Object` cmdlet because `Sort-Object` processes all objects and then returns a collection.</span></span> <span data-ttu-id="3de46-134">`Select-Object`優化只適用于在處理時個別傳回物件的命令。</span><span class="sxs-lookup"><span data-stu-id="3de46-134">The `Select-Object` optimization is available only for commands that return objects individually as they are processed.</span></span>

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

### <span data-ttu-id="3de46-135">範例4：選取陣列中的唯一字元</span><span class="sxs-lookup"><span data-stu-id="3de46-135">Example 4: Select unique characters from an array</span></span>

<span data-ttu-id="3de46-136">這個範例使用的 **unique** 參數 `Select-Object` ，從字元陣列取得唯一字元。</span><span class="sxs-lookup"><span data-stu-id="3de46-136">This example uses the **Unique** parameter of `Select-Object` to get unique characters from an array of characters.</span></span>

```powershell
"a","b","c","a","a","a" | Select-Object -Unique
```

```Output
a
b
c
```

### <span data-ttu-id="3de46-137">範例5：在事件記錄檔中選取最新和最舊的事件</span><span class="sxs-lookup"><span data-stu-id="3de46-137">Example 5: Select newest and oldest events in the event log</span></span>

<span data-ttu-id="3de46-138">此範例會取得 Windows PowerShell 事件記錄檔中的第一個 (最新) 和最後 (最舊的) 事件。</span><span class="sxs-lookup"><span data-stu-id="3de46-138">This example gets the first (newest) and last (oldest) events in the Windows PowerShell event log.</span></span>

<span data-ttu-id="3de46-139">`Get-EventLog` 取得 Windows PowerShell 記錄檔中的所有事件，並將它們儲存在 `$a` 變數中。</span><span class="sxs-lookup"><span data-stu-id="3de46-139">`Get-EventLog` gets all events in the Windows PowerShell log and saves them in the `$a` variable.</span></span>
<span data-ttu-id="3de46-140">然後， `$a` 會透過管道傳送至 `Select-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3de46-140">Then, `$a` is piped to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="3de46-141">此 `Select-Object` 命令會使用 **Index** 參數，從變數中的事件陣列選取事件 `$a` 。</span><span class="sxs-lookup"><span data-stu-id="3de46-141">The `Select-Object` command uses the **Index** parameter to select events from the array of events in the `$a` variable.</span></span> <span data-ttu-id="3de46-142">第一個事件的索引為 0。</span><span class="sxs-lookup"><span data-stu-id="3de46-142">The index of the first event is 0.</span></span> <span data-ttu-id="3de46-143">最後一個事件的索引是減1的專案數目 `$a` 。</span><span class="sxs-lookup"><span data-stu-id="3de46-143">The index of the last event is the number of items in `$a` minus 1.</span></span>

```powershell
$a = Get-EventLog -LogName "Windows PowerShell"
$a | Select-Object -Index 0, ($A.count - 1)
```

### <span data-ttu-id="3de46-144">範例6：選取第一個物件以外的所有物件</span><span class="sxs-lookup"><span data-stu-id="3de46-144">Example 6: Select all but the first object</span></span>

<span data-ttu-id="3de46-145">這個範例會在 Servers.txt 檔案中列出的每一部電腦上建立新的 PSSession，除了第一部電腦之外。</span><span class="sxs-lookup"><span data-stu-id="3de46-145">This example creates a new PSSession on each of the computers listed in the Servers.txt files, except for the first one.</span></span>

<span data-ttu-id="3de46-146">`Select-Object` 選取電腦名稱稱清單中的所有電腦，但不選取第一部電腦。</span><span class="sxs-lookup"><span data-stu-id="3de46-146">`Select-Object` selects all but the first computer in a list of computer names.</span></span> <span data-ttu-id="3de46-147">產生的電腦清單會設定為 Cmdlet 的 **ComputerName** 參數值 `New-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="3de46-147">The resulting list of computers is set as the value of the **ComputerName** parameter of the `New-PSSession` cmdlet.</span></span>

```powershell
New-PSSession -ComputerName (Get-Content Servers.txt | Select-Object -Skip 1)
```

### <span data-ttu-id="3de46-148">範例7：重新命名檔案，然後選取多個以進行審核</span><span class="sxs-lookup"><span data-stu-id="3de46-148">Example 7: Rename files and select several to review</span></span>

<span data-ttu-id="3de46-149">此範例會將 "-ro" 尾碼新增至具有唯讀屬性之文字檔的基底名稱，然後顯示前五個檔案，讓使用者可以看到效果的範例。</span><span class="sxs-lookup"><span data-stu-id="3de46-149">This example adds a "-ro" suffix to the base names of text files that have the read-only attribute and then displays the first five files so the user can see a sample of the effect.</span></span>

<span data-ttu-id="3de46-150">`Get-ChildItem` 使用 **ReadOnly** 動態參數來取得唯讀檔案。</span><span class="sxs-lookup"><span data-stu-id="3de46-150">`Get-ChildItem` uses the **ReadOnly** dynamic parameter to get read-only files.</span></span> <span data-ttu-id="3de46-151">產生的檔案會以管道傳送至 `Rename-Item` Cmdlet，以重新命名檔案。</span><span class="sxs-lookup"><span data-stu-id="3de46-151">The resulting files are piped to the `Rename-Item` cmdlet, which renames the file.</span></span> <span data-ttu-id="3de46-152">它使用的 **Passthru** 參數將重新 `Rename-Item` 命名的檔案傳送至 `Select-Object` Cmdlet，此 Cmdlet 會選取前5個來顯示。</span><span class="sxs-lookup"><span data-stu-id="3de46-152">It uses the **Passthru** parameter of `Rename-Item` to send the renamed files to the `Select-Object` cmdlet, which selects the first 5 for display.</span></span>

<span data-ttu-id="3de46-153">的 **Wait** 參數 `Select-Object` 會防止 PowerShell 在 `Get-ChildItem` 取得前五個唯讀文字檔之後停止 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3de46-153">The **Wait** parameter of `Select-Object` prevents PowerShell from stopping the `Get-ChildItem` cmdlet after it gets the first five read-only text files.</span></span> <span data-ttu-id="3de46-154">在沒有此參數的情況下，只會重新命名前五個唯讀檔案。</span><span class="sxs-lookup"><span data-stu-id="3de46-154">Without this parameter, only the first five read-only files would be renamed.</span></span>

```powershell
Get-ChildItem *.txt -ReadOnly |
    Rename-Item -NewName {$_.BaseName + "-ro.txt"} -PassThru |
    Select-Object -First 5 -Wait
```

### <span data-ttu-id="3de46-155">範例8：示範-ExpandProperty 參數的複雜</span><span class="sxs-lookup"><span data-stu-id="3de46-155">Example 8: Demonstrate the intricacies of the -ExpandProperty parameter</span></span>

<span data-ttu-id="3de46-156">此範例示範 **ExpandProperty** 參數的複雜。</span><span class="sxs-lookup"><span data-stu-id="3de46-156">This example demonstrates the intricacies of the **ExpandProperty** parameter.</span></span>

<span data-ttu-id="3de46-157">請注意，產生的輸出是實例的陣列 `[System.Int32]` 。</span><span class="sxs-lookup"><span data-stu-id="3de46-157">Note that the output generated was an array of `[System.Int32]` instances.</span></span> <span data-ttu-id="3de46-158">實例符合 **輸出視圖** 的標準格式化規則。</span><span class="sxs-lookup"><span data-stu-id="3de46-158">The instances conform to standard formatting rules of the **Output View** .</span></span> <span data-ttu-id="3de46-159">這適用于任何 *展開* 的屬性。</span><span class="sxs-lookup"><span data-stu-id="3de46-159">This is true for any *Expanded* properties.</span></span> <span data-ttu-id="3de46-160">如果輸出的物件具有特定的標準格式，則可能不會顯示展開的屬性。</span><span class="sxs-lookup"><span data-stu-id="3de46-160">If the outputted objects have a specific standard format, the expanded property might not be visible.</span></span>

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

### <span data-ttu-id="3de46-161">範例9：在物件上建立自訂屬性</span><span class="sxs-lookup"><span data-stu-id="3de46-161">Example 9: Create custom properties on objects</span></span>

<span data-ttu-id="3de46-162">下列範例示範如何使用將 `Select-Object` 自訂屬性加入至任何物件。</span><span class="sxs-lookup"><span data-stu-id="3de46-162">The following example demonstrates using `Select-Object` to add a custom property to any object.</span></span>
<span data-ttu-id="3de46-163">當您指定不存在的屬性名稱時，會 `Select-Object` 將該屬性建立為每個傳遞之物件上的 **NoteProperty** 。</span><span class="sxs-lookup"><span data-stu-id="3de46-163">When you specify a property name that does not exist, `Select-Object` creates that property as a **NoteProperty** on each object passed.</span></span>

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

### <span data-ttu-id="3de46-164">範例10：為每個 InputObject 建立計算屬性</span><span class="sxs-lookup"><span data-stu-id="3de46-164">Example 10: Create calculated properties for each InputObject</span></span>

<span data-ttu-id="3de46-165">這個範例示範 `Select-Object` 如何使用，將計算屬性加入至您的輸入。</span><span class="sxs-lookup"><span data-stu-id="3de46-165">This example demonstrates using `Select-Object` to add calculated properties to your input.</span></span> <span data-ttu-id="3de46-166">將 **ScriptBlock** 傳遞給 **Property** 參數會導致 `Select-Object` 在每個傳遞的物件上評估運算式，並將結果新增至輸出。</span><span class="sxs-lookup"><span data-stu-id="3de46-166">Passing a **ScriptBlock** to the **Property** parameter causes `Select-Object` to evaluate the expression on each object passed and add the results to the output.</span></span> <span data-ttu-id="3de46-167">在 **ScriptBlock** 內，您可以使用 `$_` 變數來參考管線中的目前物件。</span><span class="sxs-lookup"><span data-stu-id="3de46-167">Within the **ScriptBlock** , you can use the `$_` variable to reference the current object in the pipeline.</span></span>

<span data-ttu-id="3de46-168">依預設， `Select-Object` 會使用 **ScriptBlock** 字串做為屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="3de46-168">By default, `Select-Object` will use the **ScriptBlock** string as the name of the property.</span></span> <span data-ttu-id="3de46-169">使用 **雜湊表** ，您可以將 **ScriptBlock** 的輸出標記為新增至每個物件的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="3de46-169">Using a **Hashtable** , you can label the output of your **ScriptBlock** as a custom property added to each object.</span></span> <span data-ttu-id="3de46-170">您可以將多個計算屬性加入至傳遞給的每個物件 `Select-Object` 。</span><span class="sxs-lookup"><span data-stu-id="3de46-170">You can add multiple calculated properties to each object passed to `Select-Object`.</span></span>

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

## <span data-ttu-id="3de46-171">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3de46-171">PARAMETERS</span></span>

### <span data-ttu-id="3de46-172">-ExcludeProperty</span><span class="sxs-lookup"><span data-stu-id="3de46-172">-ExcludeProperty</span></span>

<span data-ttu-id="3de46-173">指定此 Cmdlet 從作業中排除的屬性。</span><span class="sxs-lookup"><span data-stu-id="3de46-173">Specifies the properties that this cmdlet excludes from the operation.</span></span> <span data-ttu-id="3de46-174">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="3de46-174">Wildcards are permitted.</span></span> <span data-ttu-id="3de46-175">此參數只有在命令也包括 **Property** 參數時才有效。</span><span class="sxs-lookup"><span data-stu-id="3de46-175">This parameter is effective only when the command also includes the **Property** parameter.</span></span>

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

### <span data-ttu-id="3de46-176">-ExpandProperty</span><span class="sxs-lookup"><span data-stu-id="3de46-176">-ExpandProperty</span></span>

<span data-ttu-id="3de46-177">請指定要選取的屬性，並指示應嘗試延伸該屬性。</span><span class="sxs-lookup"><span data-stu-id="3de46-177">Specifies a property to select, and indicates that an attempt should be made to expand that property.</span></span>

- <span data-ttu-id="3de46-178">如果指定的屬性是陣列，則陣列的每個值都會包含在輸出中。</span><span class="sxs-lookup"><span data-stu-id="3de46-178">If the specified property is an array, each value of the array is included in the output.</span></span>
- <span data-ttu-id="3de46-179">如果指定的屬性是物件，則會針對每個 **InputObject** 展開物件屬性</span><span class="sxs-lookup"><span data-stu-id="3de46-179">If the specified property is an object, the objects properties are expanded for every **InputObject**</span></span>

<span data-ttu-id="3de46-180">無論是哪一種情況，輸出物件的 **類型** 都將符合展開屬性的 **類型** 。</span><span class="sxs-lookup"><span data-stu-id="3de46-180">In either case, the **Type** of objects output will match the **Type** of the expanded property.</span></span>

<span data-ttu-id="3de46-181">如果指定了 **Property** 參數， `Select-Object` 將會嘗試將每個選取的屬性新增為每個輸出物件的 **NoteProperty** 。</span><span class="sxs-lookup"><span data-stu-id="3de46-181">If the **Property** parameter is specified, `Select-Object` will attempt to add each selected property as a **NoteProperty** to every outputted object.</span></span>

> [!WARNING]
> <span data-ttu-id="3de46-182">如果您收到錯誤：因為屬性已存在，所以無法處理 Select： Property `<PropertyName>` ，請考慮下列事項。</span><span class="sxs-lookup"><span data-stu-id="3de46-182">If you receive the error: Select : Property cannot be processed because property `<PropertyName>` already exists, consider the following.</span></span>
> <span data-ttu-id="3de46-183">請注意，使用時 `-ExpandProperty` ， `Select-Object` 不能取代現有的屬性。</span><span class="sxs-lookup"><span data-stu-id="3de46-183">Note that when using `-ExpandProperty`, `Select-Object` can not replace an existing property.</span></span>
> <span data-ttu-id="3de46-184">這表示：</span><span class="sxs-lookup"><span data-stu-id="3de46-184">This means:</span></span>
>
> - <span data-ttu-id="3de46-185">如果展開的物件具有相同名稱的屬性，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="3de46-185">If the expanded object has a property of the same name, an error will occur.</span></span>
> - <span data-ttu-id="3de46-186">如果 *選取* 的物件具有與 *展開* 物件屬性相同名稱的屬性，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="3de46-186">If the *Selected* object has a property of the same name as an *Expanded* objects property, an error will occur.</span></span>

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

### <span data-ttu-id="3de46-187">-First</span><span class="sxs-lookup"><span data-stu-id="3de46-187">-First</span></span>

<span data-ttu-id="3de46-188">指定要從輸入物件陣列開始位置選取的物件數。</span><span class="sxs-lookup"><span data-stu-id="3de46-188">Specifies the number of objects to select from the beginning of an array of input objects.</span></span>

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

### <span data-ttu-id="3de46-189">-Index</span><span class="sxs-lookup"><span data-stu-id="3de46-189">-Index</span></span>

<span data-ttu-id="3de46-190">依據物件的索引值從陣列選取物件。</span><span class="sxs-lookup"><span data-stu-id="3de46-190">Selects objects from an array based on their index values.</span></span> <span data-ttu-id="3de46-191">在使用逗號區隔的清單中輸入索引。</span><span class="sxs-lookup"><span data-stu-id="3de46-191">Enter the indexes in a comma-separated list.</span></span> <span data-ttu-id="3de46-192">陣列中的索引是以 0 開始，其中 0 代表第一個值，(n-1) 則代表最後一個值。</span><span class="sxs-lookup"><span data-stu-id="3de46-192">Indexes in an array begin with 0, where 0 represents the first value and (n-1) represents the last value.</span></span>

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

### <span data-ttu-id="3de46-193">-InputObject</span><span class="sxs-lookup"><span data-stu-id="3de46-193">-InputObject</span></span>

<span data-ttu-id="3de46-194">指定要透過管線傳送給 Cmdlet 的物件。</span><span class="sxs-lookup"><span data-stu-id="3de46-194">Specifies objects to send to the cmdlet through the pipeline.</span></span> <span data-ttu-id="3de46-195">此參數可讓您將物件輸送至 `Select-Object` 。</span><span class="sxs-lookup"><span data-stu-id="3de46-195">This parameter enables you to pipe objects to `Select-Object`.</span></span>

<span data-ttu-id="3de46-196">當您將物件傳遞給 **inputobject** 參數時（而不是使用管線）， `Select-Object` 會將 **InputObject** 視為單一物件（即使值是集合）。</span><span class="sxs-lookup"><span data-stu-id="3de46-196">When you pass objects to the **InputObject** parameter, instead of using the pipeline, `Select-Object` treats the **InputObject** as a single object, even if the value is a collection.</span></span> <span data-ttu-id="3de46-197">建議您在將集合傳遞至時，使用管線 `Select-Object` 。</span><span class="sxs-lookup"><span data-stu-id="3de46-197">It is recommended that you use the pipeline when passing collections to `Select-Object`.</span></span>

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

### <span data-ttu-id="3de46-198">-Last</span><span class="sxs-lookup"><span data-stu-id="3de46-198">-Last</span></span>

<span data-ttu-id="3de46-199">指定要從輸入物件陣列結束位置選取的物件數。</span><span class="sxs-lookup"><span data-stu-id="3de46-199">Specifies the number of objects to select from the end of an array of input objects.</span></span>

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

### <span data-ttu-id="3de46-200">-Property</span><span class="sxs-lookup"><span data-stu-id="3de46-200">-Property</span></span>

<span data-ttu-id="3de46-201">指定要選取的屬性。</span><span class="sxs-lookup"><span data-stu-id="3de46-201">Specifies the properties to select.</span></span> <span data-ttu-id="3de46-202">這些屬性會以 **NoteProperty** 成員的形式新增至輸出物件。</span><span class="sxs-lookup"><span data-stu-id="3de46-202">These properties are added as **NoteProperty** members to the output objects.</span></span> <span data-ttu-id="3de46-203">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="3de46-203">Wildcards are permitted.</span></span>

<span data-ttu-id="3de46-204">**Property** 參數的值可以是新的計算屬性。</span><span class="sxs-lookup"><span data-stu-id="3de46-204">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="3de46-205">若要建立計算的屬性，請使用雜湊表。</span><span class="sxs-lookup"><span data-stu-id="3de46-205">To create a calculated, property, use a hash table.</span></span>

<span data-ttu-id="3de46-206">有效索引鍵為：</span><span class="sxs-lookup"><span data-stu-id="3de46-206">Valid keys are:</span></span>

- <span data-ttu-id="3de46-207">名稱 (或標籤) - `<string>`</span><span class="sxs-lookup"><span data-stu-id="3de46-207">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="3de46-208">運算式 `<string>` 或 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="3de46-208">Expression - `<string>` or `<script block>`</span></span>

<span data-ttu-id="3de46-209">如需詳細資訊，請參閱 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。</span><span class="sxs-lookup"><span data-stu-id="3de46-209">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="3de46-210">-Skip</span><span class="sxs-lookup"><span data-stu-id="3de46-210">-Skip</span></span>

<span data-ttu-id="3de46-211">略過 (不選取) 指定的項目數。</span><span class="sxs-lookup"><span data-stu-id="3de46-211">Skips (does not select) the specified number of items.</span></span> <span data-ttu-id="3de46-212">根據預設， **Skip** 參數會從物件陣列或清單的開頭開始計算，但是如果命令使用 **最後一個** 參數，就會從清單或陣列的結尾算起。</span><span class="sxs-lookup"><span data-stu-id="3de46-212">By default, the **Skip** parameter counts from the beginning of the array or list of objects, but if the command uses the **Last** parameter, it counts from the end of the list or array.</span></span>

<span data-ttu-id="3de46-213">與從 0 位置開始計算的 **Index** 參數不同， **Skip** 參數會從 1 開始。</span><span class="sxs-lookup"><span data-stu-id="3de46-213">Unlike the **Index** parameter, which starts counting at 0, the **Skip** parameter begins at 1.</span></span>

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

### <span data-ttu-id="3de46-214">-SkipLast</span><span class="sxs-lookup"><span data-stu-id="3de46-214">-SkipLast</span></span>

<span data-ttu-id="3de46-215">略過 (不會從清單或陣列的結尾選取) 指定數目的專案。</span><span class="sxs-lookup"><span data-stu-id="3de46-215">Skips (does not select) the specified number of items from the end of the list or array.</span></span> <span data-ttu-id="3de46-216">的運作方式與使用 **Skip** 搭配 **Last** 參數的方式相同。</span><span class="sxs-lookup"><span data-stu-id="3de46-216">Works in the same way as using **Skip** together with **Last** parameter.</span></span>

<span data-ttu-id="3de46-217">不同于從0開始計算的 **Index** 參數， **SkipLast** 參數會從1開始。</span><span class="sxs-lookup"><span data-stu-id="3de46-217">Unlike the **Index** parameter, which starts counting at 0, the **SkipLast** parameter begins at 1.</span></span>

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

### <span data-ttu-id="3de46-218">-Unique</span><span class="sxs-lookup"><span data-stu-id="3de46-218">-Unique</span></span>

<span data-ttu-id="3de46-219">指定當輸入物件的子集具有完全相同的屬性與值，將只會選取子集的一個成員。</span><span class="sxs-lookup"><span data-stu-id="3de46-219">Specifies that if a subset of the input objects has identical properties and values, only a single member of the subset will be selected.</span></span>

<span data-ttu-id="3de46-220">此參數區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="3de46-220">This parameter is case-sensitive.</span></span> <span data-ttu-id="3de46-221">因此，只有字元大小寫不同的字串會被視為唯一的字串。</span><span class="sxs-lookup"><span data-stu-id="3de46-221">As a result, strings that differ only in character casing are considered to be unique.</span></span>

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

### <span data-ttu-id="3de46-222">-Wait</span><span class="sxs-lookup"><span data-stu-id="3de46-222">-Wait</span></span>

<span data-ttu-id="3de46-223">指出此 Cmdlet 會關閉優化。</span><span class="sxs-lookup"><span data-stu-id="3de46-223">Indicates that the cmdlet turns off optimization.</span></span> <span data-ttu-id="3de46-224">PowerShell 會以命令在命令管線中出現的循序執行命令，並讓它們產生所有物件。</span><span class="sxs-lookup"><span data-stu-id="3de46-224">PowerShell runs commands in the order that they appear in the command pipeline and lets them generate all objects.</span></span> <span data-ttu-id="3de46-225">根據預設，如果您 `Select-Object` 在命令管線中包含具有 **First** 或 **Index** 參數的命令，則 PowerShell 會在產生選取的物件數目時，停止產生物件的命令。</span><span class="sxs-lookup"><span data-stu-id="3de46-225">By default, if you include a `Select-Object` command with the **First** or **Index** parameters in a command pipeline, PowerShell stops the command that generates the objects as soon as the selected number of objects is generated.</span></span>

<span data-ttu-id="3de46-226">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="3de46-226">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="3de46-227">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3de46-227">CommonParameters</span></span>

<span data-ttu-id="3de46-228">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="3de46-228">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3de46-229">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="3de46-229">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="3de46-230">輸入</span><span class="sxs-lookup"><span data-stu-id="3de46-230">INPUTS</span></span>

### <span data-ttu-id="3de46-231">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="3de46-231">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="3de46-232">您可以透過管線將任何物件傳送至 `Select-Object` 。</span><span class="sxs-lookup"><span data-stu-id="3de46-232">You can pipe any object to `Select-Object`.</span></span>

## <span data-ttu-id="3de46-233">輸出</span><span class="sxs-lookup"><span data-stu-id="3de46-233">OUTPUTS</span></span>

### <span data-ttu-id="3de46-234">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="3de46-234">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="3de46-235">注意</span><span class="sxs-lookup"><span data-stu-id="3de46-235">NOTES</span></span>

- <span data-ttu-id="3de46-236">您也可以 `Select-Object` 使用它的內建別名來參考 Cmdlet `select` 。</span><span class="sxs-lookup"><span data-stu-id="3de46-236">You can also refer to the `Select-Object` cmdlet by its built-in alias, `select`.</span></span> <span data-ttu-id="3de46-237">如需詳細資訊，請參閱 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="3de46-237">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

- <span data-ttu-id="3de46-238">的優化功能 `Select-Object` 僅適用于在處理管線時將物件寫入至管線的命令。</span><span class="sxs-lookup"><span data-stu-id="3de46-238">The optimization feature of `Select-Object` is available only for commands that write objects to the pipeline as they are processed.</span></span> <span data-ttu-id="3de46-239">它對緩衝已處理之物件的命令沒有效果，並且會將它們以集合的方式寫入。</span><span class="sxs-lookup"><span data-stu-id="3de46-239">It has no effect on commands that buffer processed objects and write them as a collection.</span></span> <span data-ttu-id="3de46-240">立即寫入物件是 Cmdlet 設計最佳做法。</span><span class="sxs-lookup"><span data-stu-id="3de46-240">Writing objects immediately is a cmdlet design best practice.</span></span> <span data-ttu-id="3de46-241">如需詳細資訊，請參閱以 [強烈建議的開發指導方針](/powershell/scripting/developer/windows-powershell)，將 _單一記錄寫入管線_ 。</span><span class="sxs-lookup"><span data-stu-id="3de46-241">For more information, see _Write Single Records to the Pipeline_ in [Strongly Encouraged Development Guidelines](/powershell/scripting/developer/windows-powershell).</span></span>

## <span data-ttu-id="3de46-242">相關連結</span><span class="sxs-lookup"><span data-stu-id="3de46-242">RELATED LINKS</span></span>

[<span data-ttu-id="3de46-243">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="3de46-243">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="3de46-244">Group-Object</span><span class="sxs-lookup"><span data-stu-id="3de46-244">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="3de46-245">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="3de46-245">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="3de46-246">Where-Object</span><span class="sxs-lookup"><span data-stu-id="3de46-246">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
