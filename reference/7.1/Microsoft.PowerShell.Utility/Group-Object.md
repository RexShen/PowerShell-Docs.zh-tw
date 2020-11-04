---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/group-object?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Group-Object
ms.openlocfilehash: 962380192a188ec51ee3861c2623d3143a182ef3
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2020
ms.locfileid: "93205952"
---
# <span data-ttu-id="e1821-103">Group-Object</span><span class="sxs-lookup"><span data-stu-id="e1821-103">Group-Object</span></span>

## <span data-ttu-id="e1821-104">概要</span><span class="sxs-lookup"><span data-stu-id="e1821-104">SYNOPSIS</span></span>
<span data-ttu-id="e1821-105">將包含指定屬性之相同值的物件分組。</span><span class="sxs-lookup"><span data-stu-id="e1821-105">Groups objects that contain the same value for specified properties.</span></span>

## <span data-ttu-id="e1821-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e1821-106">SYNTAX</span></span>

### <span data-ttu-id="e1821-107">雜湊表</span><span class="sxs-lookup"><span data-stu-id="e1821-107">HashTable</span></span>

```
Group-Object [-NoElement] [-AsHashTable] [-AsString] [-InputObject <PSObject>]
 [[-Property] <Object[]>] [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

## <span data-ttu-id="e1821-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e1821-108">DESCRIPTION</span></span>

<span data-ttu-id="e1821-109">此 `Group-Object` Cmdlet 會根據指定屬性的值，在群組中顯示物件。</span><span class="sxs-lookup"><span data-stu-id="e1821-109">The `Group-Object` cmdlet displays objects in groups based on the value of a specified property.</span></span>
<span data-ttu-id="e1821-110">`Group-Object` 傳回資料表，其中每個屬性值都有一個資料列，以及顯示具有該值之專案數目的資料行。</span><span class="sxs-lookup"><span data-stu-id="e1821-110">`Group-Object` returns a table with one row for each property value and a column that displays the number of items with that value.</span></span>

<span data-ttu-id="e1821-111">如果您指定一個以上的屬性，請 `Group-Object` 先依第一個屬性的值將它們分組，然後在每個屬性群組內，依下一個屬性的值分組。</span><span class="sxs-lookup"><span data-stu-id="e1821-111">If you specify more than one property, `Group-Object` first groups them by the values of the first property, and then, within each property group, it groups by the value of the next property.</span></span>

<span data-ttu-id="e1821-112">從 PowerShell 7 開始， `Group-Object` 可以結合 **CaseSensitive** 和 **AsHashtable** 參數來建立區分大小寫的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="e1821-112">Beginning in PowerShell 7, `Group-Object` can combine the **CaseSensitive** and **AsHashtable** parameters to create a case-sensitive hash table.</span></span> <span data-ttu-id="e1821-113">雜湊表索引鍵會使用區分大小寫的比較，並輸出 **system.string 物件。**</span><span class="sxs-lookup"><span data-stu-id="e1821-113">The hash table keys use case-sensitive comparisons and output a **System.Collections.Hashtable** object.</span></span>

## <span data-ttu-id="e1821-114">範例</span><span class="sxs-lookup"><span data-stu-id="e1821-114">EXAMPLES</span></span>

### <span data-ttu-id="e1821-115">範例1：依副檔名群組檔案</span><span class="sxs-lookup"><span data-stu-id="e1821-115">Example 1: Group files by extension</span></span>

<span data-ttu-id="e1821-116">此範例會以遞迴方式取得中的檔案 `$PSHOME` ，並依副檔名將它們分組。</span><span class="sxs-lookup"><span data-stu-id="e1821-116">This example recursively gets the files under `$PSHOME` and groups them by file name extension.</span></span> <span data-ttu-id="e1821-117">輸出會傳送至 `Sort-Object` Cmdlet，以針對指定的延伸模組找到的計數檔案進行排序。</span><span class="sxs-lookup"><span data-stu-id="e1821-117">The output is sent to the `Sort-Object` cmdlet, which sorts them by the count files found for the given extension.</span></span> <span data-ttu-id="e1821-118">空白 **名稱** 代表目錄。</span><span class="sxs-lookup"><span data-stu-id="e1821-118">The empty **Name** represents directories.</span></span>

<span data-ttu-id="e1821-119">此範例使用 **NoElement** 參數來省略群組的成員。</span><span class="sxs-lookup"><span data-stu-id="e1821-119">This example uses the **NoElement** parameter to omit the members of the group.</span></span>

```powershell
$files = Get-ChildItem -Path $PSHOME -Recurse
$files | Group-Object -Property extension -NoElement | Sort-Object -Property Count -Descending
```

```Output
Count Name
----- ----
  365 .xml
  231 .cdxml
  197
  169 .ps1xml
  142 .txt
  114 .psd1
   63 .psm1
   49 .xsd
   36 .dll
   15 .mfl
   15 .mof
...
```

### <span data-ttu-id="e1821-120">範例2：依機率和 evens 分組整數</span><span class="sxs-lookup"><span data-stu-id="e1821-120">Example 2: Group integers by odds and evens</span></span>

<span data-ttu-id="e1821-121">此範例顯示如何使用腳本區塊做為 **Property** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="e1821-121">This example shows how to use script blocks as the value of the **Property** parameter.</span></span> <span data-ttu-id="e1821-122">此命令會顯示從1到20的整數，並依機率和甚至來分組。</span><span class="sxs-lookup"><span data-stu-id="e1821-122">This command displays the integers from 1 to 20, grouped by odds and even.</span></span>

```powershell
1..20 | Group-Object -Property {$_ % 2}
```

```Output
Count Name                      Group
----- ----                      -----
   10 0                         {2, 4, 6, 8...}
   10 1                         {1, 3, 5, 7...}
```

### <span data-ttu-id="e1821-123">範例3：依 >entrytype 分組事件記錄檔事件</span><span class="sxs-lookup"><span data-stu-id="e1821-123">Example 3: Group event log events by EntryType</span></span>

<span data-ttu-id="e1821-124">此範例會在系統事件記錄檔中顯示1000最新的專案，並依 **>entrytype** 分組。</span><span class="sxs-lookup"><span data-stu-id="e1821-124">This example displays the 1,000 most recent entries in the System event log, grouped by **EntryType** .</span></span>

<span data-ttu-id="e1821-125">在輸出中， **Count** 資料行代表每個群組中的專案數。</span><span class="sxs-lookup"><span data-stu-id="e1821-125">In the output, the **Count** column represents the number of entries in each group.</span></span> <span data-ttu-id="e1821-126">[ **名稱** ] 資料行代表定義群組的 **事件** 類型值。</span><span class="sxs-lookup"><span data-stu-id="e1821-126">The **Name** column represents the **EventType** values that define a group.</span></span> <span data-ttu-id="e1821-127">**群組** 資料行代表每個群組中的物件。</span><span class="sxs-lookup"><span data-stu-id="e1821-127">The **Group** column represents the objects in each group.</span></span>

```powershell
Get-WinEvent -LogName System -MaxEvents 1000 | Group-Object -Property LevelDisplayName
```

```Output
Count Name          Group
----- ----          -----
  153 Error         {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics...}
  722 Information   {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics...}
  125 Warning       {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics...}
```

### <span data-ttu-id="e1821-128">範例4：依優先權類別分組進程</span><span class="sxs-lookup"><span data-stu-id="e1821-128">Example 4: Group processes by priority class</span></span>

<span data-ttu-id="e1821-129">此範例示範 **NoElement** 參數的效果。</span><span class="sxs-lookup"><span data-stu-id="e1821-129">This example demonstrates the effect of the **NoElement** parameter.</span></span> <span data-ttu-id="e1821-130">這些命令會依優先順序類別將電腦上的處理程序分組。</span><span class="sxs-lookup"><span data-stu-id="e1821-130">These commands group the processes on the computer by priority class.</span></span>

<span data-ttu-id="e1821-131">第一個命令會使用 `Get-Process` Cmdlet 取得電腦上的處理常式，並將物件沿著管線向下傳送。</span><span class="sxs-lookup"><span data-stu-id="e1821-131">The first command uses the `Get-Process` cmdlet to get the processes on the computer and sends the objects down the pipeline.</span></span> <span data-ttu-id="e1821-132">`Group-Object`依進程的 **PriorityClass** 屬性值將物件分組。</span><span class="sxs-lookup"><span data-stu-id="e1821-132">`Group-Object`groups the objects by the value of the **PriorityClass** property of the process.</span></span>

<span data-ttu-id="e1821-133">第二個範例會使用 **NoElement** 參數來消除輸出中群組的成員。</span><span class="sxs-lookup"><span data-stu-id="e1821-133">The second example uses the **NoElement** parameter to eliminate the members of the group from the output.</span></span> <span data-ttu-id="e1821-134">結果是只有 **Count** 和 **Name** 屬性值的資料表。</span><span class="sxs-lookup"><span data-stu-id="e1821-134">The result is a table with only the **Count** and **Name** property value.</span></span>

<span data-ttu-id="e1821-135">結果顯示在下列範例輸出中。</span><span class="sxs-lookup"><span data-stu-id="e1821-135">The results are shown in the following sample output.</span></span>

```powershell
Get-Process | Group-Object -Property PriorityClass
```

```Output
Count Name         Group
----- ----         -----
   55 Normal       {System.Diagnostics.Process (AdtAgent), System.Diagnosti...
    1              {System.Diagnostics.Process (Idle)}
    3 High         {System.Diagnostics.Process (Newproc), System.Diagnostic...
    2 BelowNormal  {System.Diagnostics.Process (winperf),
```

```powershell
Get-Process | Group-Object -Property PriorityClass -NoElement
```

```Output
Count Name
----- ----
   55 Normal
    1
    3 High
    2 BelowNormal
```

### <span data-ttu-id="e1821-136">範例5：依名稱分組進程</span><span class="sxs-lookup"><span data-stu-id="e1821-136">Example 5: Group processes by name</span></span>

<span data-ttu-id="e1821-137">下列範例會使用 `Group-Object` 來群組在本機電腦上執行的多個處理常式實例。</span><span class="sxs-lookup"><span data-stu-id="e1821-137">The following example uses `Group-Object` to group multiple instances of processes running on the local computer.</span></span> <span data-ttu-id="e1821-138">`Where-Object` 顯示具有一個以上實例的進程。</span><span class="sxs-lookup"><span data-stu-id="e1821-138">`Where-Object` displays processes with more than one instance.</span></span>

```powershell
Get-Process | Group-Object -Property Name -NoElement | Where-Object {$_.Count -gt 1}
```

```Output
Count Name
----- ----
2     csrss
5     svchost
2     winlogon
2     wmiprvse
```

### <span data-ttu-id="e1821-139">範例6：雜湊表中的群組物件</span><span class="sxs-lookup"><span data-stu-id="e1821-139">Example 6: Group objects in a hash table</span></span>

<span data-ttu-id="e1821-140">這個範例會使用 **AsHashTable** 和 **AsString** 參數，以索引鍵/值組的集合傳回雜湊表中的群組。</span><span class="sxs-lookup"><span data-stu-id="e1821-140">This example uses the **AsHashTable** and **AsString** parameters to return the groups in a hash table, as a collection of key-value pairs.</span></span>

<span data-ttu-id="e1821-141">在產生的雜湊表中，每個屬性值為索引鍵，而群組元素為值。</span><span class="sxs-lookup"><span data-stu-id="e1821-141">In the resulting hash table, each property value is a key, and the group elements are the values.</span></span>
<span data-ttu-id="e1821-142">因為每個索引鍵是雜湊表物件的屬性，您可以使用點標記法來顯示值。</span><span class="sxs-lookup"><span data-stu-id="e1821-142">Because each key is a property of the hash table object, you can use dot notation to display the values.</span></span>

<span data-ttu-id="e1821-143">第一個命令會取得 `Get` `Set` 會話中的和 Cmdlet、依動詞將這些指令程式分組、以雜湊表傳回群組，然後將雜湊表儲存在 `$A` 變數中。</span><span class="sxs-lookup"><span data-stu-id="e1821-143">The first command gets the `Get` and `Set` cmdlets in the session, groups them by verb, returns the groups as a hash table, and saves the hash table in the `$A` variable.</span></span>

<span data-ttu-id="e1821-144">第二個命令會顯示中的雜湊表 `$A` 。</span><span class="sxs-lookup"><span data-stu-id="e1821-144">The second command displays the hash table in `$A`.</span></span> <span data-ttu-id="e1821-145">有兩個索引鍵/值組，一個用於 `Get` Cmdlet，另一個用於 `Set` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e1821-145">There are two key-value pairs, one for the `Get` cmdlets and one for the `Set` cmdlets.</span></span>

<span data-ttu-id="e1821-146">第三個命令使用點標記法， `$A.Get` 在中顯示 **Get** 索引鍵的值 `$A` 。</span><span class="sxs-lookup"><span data-stu-id="e1821-146">The third command uses dot notation, `$A.Get` to display the values of the **Get** key in `$A`.</span></span> <span data-ttu-id="e1821-147">這些值為 **CmdletInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="e1821-147">The values are **CmdletInfo** object.</span></span> <span data-ttu-id="e1821-148">**AsString** 參數不會將群組中的物件轉換成字串。</span><span class="sxs-lookup"><span data-stu-id="e1821-148">The **AsString** parameter doesn't convert the objects in the groups to strings.</span></span>

```powershell
$A = Get-Command Get-*, Set-* -CommandType cmdlet | Group-Object -Property Verb -AsHashTable -AsString
$A
```

```Output
Name     Value
----     -----
Get      {Get-Acl, Get-Alias, Get-AppLockerFileInformation, Get-AppLockerPolicy...}
Set      {Set-Acl, Set-Alias, Set-AppBackgroundTaskResourcePolicy, Set-AppLockerPolicy...}
```

```powershell
$A.Get
```

```Output
CommandType     Name                                Version    Source
-----------     ----                                -------    ------
Cmdlet          Get-Acl                             7.0.0.0    Microsoft.PowerShell.Security
Cmdlet          Get-Alias                           7.0.0.0    Microsoft.PowerShell.Utility
Cmdlet          Get-AppLockerFileInformation        2.0.0.0    AppLocker
Cmdlet          Get-AppLockerPolicy                 2.0.0.0    AppLocker
...
```

### <span data-ttu-id="e1821-149">範例7：建立區分大小寫的雜湊表</span><span class="sxs-lookup"><span data-stu-id="e1821-149">Example 7: Create a case-sensitive hash table</span></span>

<span data-ttu-id="e1821-150">此範例結合了 **CaseSensitive** 和 **AsHashTable** 參數來建立區分大小寫的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="e1821-150">This example combines the **CaseSensitive** and **AsHashTable** parameters to create a case-sensitive hash table.</span></span> <span data-ttu-id="e1821-151">範例中的檔案具有和的副檔名 `.txt` `.TXT` 。</span><span class="sxs-lookup"><span data-stu-id="e1821-151">The files in the example have extensions of `.txt` and `.TXT`.</span></span>

```powershell
$hash = Get-ChildItem -Path C:\Files | Group-Object -Property Extension -CaseSensitive -AsHashTable
$hash
```

```Output
Name           Value
----           -----
.TXT           {C:\Files\File7.TXT, C:\Files\File8.TXT, C:\Files\File9.TXT}
.txt           {C:\Files\file1.txt, C:\Files\file2.txt, C:\Files\file3.txt}
```

<span data-ttu-id="e1821-152">`$hash`變數會儲存 **system.object** 物件。</span><span class="sxs-lookup"><span data-stu-id="e1821-152">The `$hash` variable stores the **System.Collections.Hashtable** object.</span></span> <span data-ttu-id="e1821-153">`Get-ChildItem` 從目錄中取得檔案名 `C:\Files` ，然後將 **FileInfo** 物件傳送至管線。</span><span class="sxs-lookup"><span data-stu-id="e1821-153">`Get-ChildItem` gets the file names from the `C:\Files` directory and sends the **System.IO.FileInfo** objects down the pipeline.</span></span> <span data-ttu-id="e1821-154">`Group-Object` 使用 **屬性** 值 **延伸** 來將物件分組。</span><span class="sxs-lookup"><span data-stu-id="e1821-154">`Group-Object` groups the objects using the **Property** value **Extension** .</span></span> <span data-ttu-id="e1821-155">**CaseSensitive** 和 **AsHashTable** 參數會建立雜湊表，而且索引鍵會使用區分大小寫的索引鍵和來分組 `.txt` `.TXT` 。</span><span class="sxs-lookup"><span data-stu-id="e1821-155">The **CaseSensitive** and **AsHashTable** parameters create the hash table and the keys are grouped using the case-sensitive keys `.txt` and `.TXT`.</span></span>

## <span data-ttu-id="e1821-156">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e1821-156">PARAMETERS</span></span>

### <span data-ttu-id="e1821-157">-AsHashTable</span><span class="sxs-lookup"><span data-stu-id="e1821-157">-AsHashTable</span></span>

<span data-ttu-id="e1821-158">指出此 Cmdlet 會以雜湊表傳回群組。</span><span class="sxs-lookup"><span data-stu-id="e1821-158">Indicates that this cmdlet returns the group as a hash table.</span></span> <span data-ttu-id="e1821-159">雜湊表的索引鍵為屬性值，會以其為依據進行物件分組。</span><span class="sxs-lookup"><span data-stu-id="e1821-159">The keys of the hash table are the property values by which the objects are grouped.</span></span> <span data-ttu-id="e1821-160">雜湊表的值是具有該屬性值的物件。</span><span class="sxs-lookup"><span data-stu-id="e1821-160">The values of the hash table are the objects that have that property value.</span></span>

<span data-ttu-id="e1821-161">**AsHashTable** 參數本身會傳回每一個雜湊表，其中每個索引鍵都是群組物件的實例。</span><span class="sxs-lookup"><span data-stu-id="e1821-161">By itself, the **AsHashTable** parameter returns each hash table in which each key is an instance of the grouped object.</span></span> <span data-ttu-id="e1821-162">搭配 **AsString** 參數使用時，雜湊表中的索引鍵為字串。</span><span class="sxs-lookup"><span data-stu-id="e1821-162">When used with the **AsString** parameter, the keys in the hash table are strings.</span></span>

<span data-ttu-id="e1821-163">從 PowerShell 7 開始，若要建立區分大小寫的雜湊表，請在命令中包含 **CaseSensitive** 和 **AsHashtable** 。</span><span class="sxs-lookup"><span data-stu-id="e1821-163">Beginning in PowerShell 7, to create case-sensitive hash tables, include **CaseSensitive** and **AsHashtable** in your command.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: AHT

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1821-164">-AsString</span><span class="sxs-lookup"><span data-stu-id="e1821-164">-AsString</span></span>

<span data-ttu-id="e1821-165">指出此 Cmdlet 會將雜湊表索引鍵轉換成字串。</span><span class="sxs-lookup"><span data-stu-id="e1821-165">Indicates that this cmdlet converts the hash table keys to strings.</span></span> <span data-ttu-id="e1821-166">依預設，雜湊表索引鍵是群組物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e1821-166">By default, the hash table keys are instances of the grouped object.</span></span> <span data-ttu-id="e1821-167">只有搭配 **AsHashTable** 參數使用時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="e1821-167">This parameter is valid only when used with the **AsHashTable** parameter.</span></span>

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

### <span data-ttu-id="e1821-168">-CaseSensitive</span><span class="sxs-lookup"><span data-stu-id="e1821-168">-CaseSensitive</span></span>

<span data-ttu-id="e1821-169">指出此 Cmdlet 會讓群組區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="e1821-169">Indicates that this cmdlet makes the grouping case-sensitive.</span></span> <span data-ttu-id="e1821-170">如果沒有這個參數，群組中物件的屬性值可能大小寫會有不同。</span><span class="sxs-lookup"><span data-stu-id="e1821-170">Without this parameter, the property values of objects in a group might have different cases.</span></span>

<span data-ttu-id="e1821-171">從 PowerShell 7 開始，若要建立區分大小寫的雜湊表，請在命令中包含 **CaseSensitive** 和 **AsHashtable** 。</span><span class="sxs-lookup"><span data-stu-id="e1821-171">Beginning in PowerShell 7, to create case-sensitive hash tables, include **CaseSensitive** and **AsHashtable** in your command.</span></span>

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

### <span data-ttu-id="e1821-172">-Culture</span><span class="sxs-lookup"><span data-stu-id="e1821-172">-Culture</span></span>

<span data-ttu-id="e1821-173">指定比較字串時要使用的文化特性。</span><span class="sxs-lookup"><span data-stu-id="e1821-173">Specifies the culture to use when comparing strings.</span></span>

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

### <span data-ttu-id="e1821-174">-InputObject</span><span class="sxs-lookup"><span data-stu-id="e1821-174">-InputObject</span></span>

<span data-ttu-id="e1821-175">指定要分組的物件。</span><span class="sxs-lookup"><span data-stu-id="e1821-175">Specifies the objects to group.</span></span> <span data-ttu-id="e1821-176">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="e1821-176">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="e1821-177">當您使用 **InputObject** 參數將物件集合提交至時，會 `Group-Object` `Group-Object` 收到一個代表集合的物件。</span><span class="sxs-lookup"><span data-stu-id="e1821-177">When you use the **InputObject** parameter to submit a collection of objects to `Group-Object`, `Group-Object` receives one object that represents the collection.</span></span> <span data-ttu-id="e1821-178">如此一來，它會建立該物件做為其成員的單一群組。</span><span class="sxs-lookup"><span data-stu-id="e1821-178">As a result, it creates a single group with that object as its member.</span></span>

<span data-ttu-id="e1821-179">若要將集合中的物件分組，請使用管線將物件傳送至 `Group-Object` 。</span><span class="sxs-lookup"><span data-stu-id="e1821-179">To group the objects in a collection, pipe the objects to `Group-Object`.</span></span>

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

### <span data-ttu-id="e1821-180">-NoElement</span><span class="sxs-lookup"><span data-stu-id="e1821-180">-NoElement</span></span>

<span data-ttu-id="e1821-181">指出此 Cmdlet 會從結果中省略群組的成員。</span><span class="sxs-lookup"><span data-stu-id="e1821-181">Indicates that this cmdlet omits the members of a group from the results.</span></span>

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

### <span data-ttu-id="e1821-182">-Property</span><span class="sxs-lookup"><span data-stu-id="e1821-182">-Property</span></span>

<span data-ttu-id="e1821-183">指定要分組的屬性。</span><span class="sxs-lookup"><span data-stu-id="e1821-183">Specifies the properties for grouping.</span></span> <span data-ttu-id="e1821-184">物件會依據指定屬性的值進行分組。</span><span class="sxs-lookup"><span data-stu-id="e1821-184">The objects are arranged into groups based on the value of the specified property.</span></span>

<span data-ttu-id="e1821-185">**Property** 參數的值可以是新的計算屬性。</span><span class="sxs-lookup"><span data-stu-id="e1821-185">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="e1821-186">計算的屬性可以是腳本區塊或雜湊表。</span><span class="sxs-lookup"><span data-stu-id="e1821-186">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="e1821-187">有效的索引鍵/值組為：</span><span class="sxs-lookup"><span data-stu-id="e1821-187">Valid key-value pairs are:</span></span>

- <span data-ttu-id="e1821-188">運算式 `<string>` 或 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="e1821-188">Expression - `<string>` or `<script block>`</span></span>

<span data-ttu-id="e1821-189">如需詳細資訊，請參閱 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。</span><span class="sxs-lookup"><span data-stu-id="e1821-189">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1821-190">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e1821-190">CommonParameters</span></span>

<span data-ttu-id="e1821-191">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="e1821-191">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e1821-192">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="e1821-192">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e1821-193">輸入</span><span class="sxs-lookup"><span data-stu-id="e1821-193">INPUTS</span></span>

### <span data-ttu-id="e1821-194">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="e1821-194">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="e1821-195">您可以透過管線將任何物件傳送至 `Group-Object` 。</span><span class="sxs-lookup"><span data-stu-id="e1821-195">You can pipe any object to `Group-Object`.</span></span>

## <span data-ttu-id="e1821-196">輸出</span><span class="sxs-lookup"><span data-stu-id="e1821-196">OUTPUTS</span></span>

### <span data-ttu-id="e1821-197">Microsoft.PowerShell.Commands.GroupInfo 或 System.Collections.Hashtable</span><span class="sxs-lookup"><span data-stu-id="e1821-197">Microsoft.PowerShell.Commands.GroupInfo or System.Collections.Hashtable</span></span>

<span data-ttu-id="e1821-198">當您使用 **AsHashTable** 參數時，會傳回 `Group-Object` **Hashtable** 物件。</span><span class="sxs-lookup"><span data-stu-id="e1821-198">When you use the **AsHashTable** parameter, `Group-Object` returns a **Hashtable** object.</span></span>
<span data-ttu-id="e1821-199">否則，它會傳回 **GroupInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="e1821-199">Otherwise, it returns a **GroupInfo** object.</span></span>

## <span data-ttu-id="e1821-200">注意</span><span class="sxs-lookup"><span data-stu-id="e1821-200">NOTES</span></span>

<span data-ttu-id="e1821-201">您可以使用格式化 Cmdlet （例如和）的 **GroupBy** 參數 `Format-Table` `Format-List` 來群組物件。</span><span class="sxs-lookup"><span data-stu-id="e1821-201">You can use the **GroupBy** parameter of the formatting cmdlets, such as `Format-Table` and `Format-List`, to group objects.</span></span> <span data-ttu-id="e1821-202">與不同的是，它會建立每個屬性值各有 `Group-Object` 一個資料列的單一資料表，而 **GroupBy** 參數會為每個屬性值建立一個資料表，其中每個具有屬性值的專案都會有一個資料列。</span><span class="sxs-lookup"><span data-stu-id="e1821-202">Unlike `Group-Object`, which creates a single table with a row for each property value, the **GroupBy** parameters create a table for each property value with a row for each item that has the property value.</span></span>

<span data-ttu-id="e1821-203">`Group-Object` 不需要分組的物件為相同的 Microsoft .NET Core 類型。</span><span class="sxs-lookup"><span data-stu-id="e1821-203">`Group-Object` doesn't require that the objects being grouped are of the same Microsoft .NET Core type.</span></span> <span data-ttu-id="e1821-204">將不同 .NET Core 類型的物件分組時，會 `Group-Object` 使用下列規則：</span><span class="sxs-lookup"><span data-stu-id="e1821-204">When grouping objects of different .NET Core types, `Group-Object` uses the following rules:</span></span>

- <span data-ttu-id="e1821-205">相同的屬性名稱和類型。</span><span class="sxs-lookup"><span data-stu-id="e1821-205">Same Property Names and Types.</span></span>

  <span data-ttu-id="e1821-206">如果物件具有具有指定名稱的屬性，且屬性值有相同的 .NET Core 類型，則會使用相同類型之物件所使用的相同規則將屬性值分組。</span><span class="sxs-lookup"><span data-stu-id="e1821-206">If the objects have a property with the specified name, and the property values have the same .NET Core type, the property values are grouped by using the same rules that would be used for objects of the same type.</span></span>

- <span data-ttu-id="e1821-207">相同的屬性名稱，不同的類型。</span><span class="sxs-lookup"><span data-stu-id="e1821-207">Same Property Names, Different Types.</span></span>

  <span data-ttu-id="e1821-208">如果物件具有具有指定名稱的屬性，但是屬性值在不同的物件中有不同的 .NET Core 型別，則 `Group-Object` 會使用第一次出現之屬性的 .Net core 型別做為該屬性群組的 .Net core 型別。</span><span class="sxs-lookup"><span data-stu-id="e1821-208">If the objects have a property with the specified name, but the property values have a different .NET Core type in different objects, `Group-Object` uses the .NET Core type of the first occurrence of the property as the .NET Core type for that property group.</span></span> <span data-ttu-id="e1821-209">當物件具有含不同類型的屬性時，屬性值會轉換為該群組的類型。</span><span class="sxs-lookup"><span data-stu-id="e1821-209">When an object has a property with a different type, the property value is converted to the type for that group.</span></span> <span data-ttu-id="e1821-210">如果類型轉換失敗，則物件不會包含在群組中。</span><span class="sxs-lookup"><span data-stu-id="e1821-210">If the type conversion fails, the object isn't included in the group.</span></span>

- <span data-ttu-id="e1821-211">遺漏屬性。</span><span class="sxs-lookup"><span data-stu-id="e1821-211">Missing Properties.</span></span>

  <span data-ttu-id="e1821-212">沒有指定屬性的物件無法群組。</span><span class="sxs-lookup"><span data-stu-id="e1821-212">Objects that don't have a specified property can't be grouped.</span></span> <span data-ttu-id="e1821-213">未分組的物件會顯示在名為的群組中的最後一個 **GroupInfo** 物件輸出中 `AutomationNull.Value` 。</span><span class="sxs-lookup"><span data-stu-id="e1821-213">Objects that aren't grouped appear in the final **GroupInfo** object output in a group named `AutomationNull.Value`.</span></span>

## <span data-ttu-id="e1821-214">相關連結</span><span class="sxs-lookup"><span data-stu-id="e1821-214">RELATED LINKS</span></span>

[<span data-ttu-id="e1821-215">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="e1821-215">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="e1821-216">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="e1821-216">about_Hash_Tables</span></span>](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[<span data-ttu-id="e1821-217">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="e1821-217">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="e1821-218">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="e1821-218">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="e1821-219">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="e1821-219">Measure-Object</span></span>](Measure-Object.md)

[<span data-ttu-id="e1821-220">New-Object</span><span class="sxs-lookup"><span data-stu-id="e1821-220">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="e1821-221">Select-Object</span><span class="sxs-lookup"><span data-stu-id="e1821-221">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="e1821-222">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="e1821-222">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="e1821-223">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="e1821-223">Tee-Object</span></span>](Tee-Object.md)

[<span data-ttu-id="e1821-224">Where-Object</span><span class="sxs-lookup"><span data-stu-id="e1821-224">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)