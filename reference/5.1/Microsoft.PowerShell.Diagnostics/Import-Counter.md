---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/import-counter?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Counter
ms.openlocfilehash: 837f6b4b3b2869c6f74b3b02904dd43b73f6bcd5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202623"
---
# <span data-ttu-id="c82e6-103">Import-Counter</span><span class="sxs-lookup"><span data-stu-id="c82e6-103">Import-Counter</span></span>

## <span data-ttu-id="c82e6-104">概要</span><span class="sxs-lookup"><span data-stu-id="c82e6-104">SYNOPSIS</span></span>
<span data-ttu-id="c82e6-105">匯入效能計數器記錄檔，並建立代表記錄檔中每個計數器樣本的物件。</span><span class="sxs-lookup"><span data-stu-id="c82e6-105">Imports performance counter log files and creates the objects that represent each counter sample in the log.</span></span>

## <span data-ttu-id="c82e6-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c82e6-106">SYNTAX</span></span>

### <span data-ttu-id="c82e6-107">GetCounterSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="c82e6-107">GetCounterSet (Default)</span></span>

```
Import-Counter [-Path] <String[]> [-StartTime <DateTime>] [-EndTime <DateTime>] [-Counter <String[]>]
 [-MaxSamples <Int64>] [<CommonParameters>]
```

### <span data-ttu-id="c82e6-108">ListSetSet</span><span class="sxs-lookup"><span data-stu-id="c82e6-108">ListSetSet</span></span>

```
Import-Counter [-Path] <String[]> -ListSet <String[]> [<CommonParameters>]
```

### <span data-ttu-id="c82e6-109">SummarySet</span><span class="sxs-lookup"><span data-stu-id="c82e6-109">SummarySet</span></span>

```
Import-Counter [-Path] <String[]> [-Summary] [<CommonParameters>]
```

## <span data-ttu-id="c82e6-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="c82e6-110">DESCRIPTION</span></span>

<span data-ttu-id="c82e6-111">**Import-module** Cmdlet 會從效能計數器記錄檔匯入效能計數器資料，並為檔案中的每個計數器樣本建立物件。</span><span class="sxs-lookup"><span data-stu-id="c82e6-111">The **Import-Counter** cmdlet imports performance counter data from performance counter log files and creates objects for each counter sample in the file.</span></span>
<span data-ttu-id="c82e6-112">它所建立的 **PerformanceCounterSampleSet** 物件與在收集效能計數器資料 **時，會傳回的物件** 完全相同。</span><span class="sxs-lookup"><span data-stu-id="c82e6-112">The **PerformanceCounterSampleSet** objects that it creates are identical to the objects that **Get-Counter** returns when it collects performance counter data.</span></span>

<span data-ttu-id="c82e6-113">您可以從逗點分隔值 (.csv)、Tab 分隔值 (.tsv) 與二進位效能記錄檔 (.blg) 效能記錄檔匯入資料。</span><span class="sxs-lookup"><span data-stu-id="c82e6-113">You can import data from comma-separated value (.csv), tab-separated value ( .tsv), and binary performance log (.blg) performance log files.</span></span>
<span data-ttu-id="c82e6-114">如果您使用的是 .blg 檔案，您可以在每個命令中匯入多達32的檔案。</span><span class="sxs-lookup"><span data-stu-id="c82e6-114">If you are using .blg files, you can import up to 32 files in each command.</span></span>
<span data-ttu-id="c82e6-115">您可以使用 [匯 **入-計數器** ] 的參數來篩選您匯入的資料。</span><span class="sxs-lookup"><span data-stu-id="c82e6-115">You can use the parameters of **Import-Counter** to filter the data that you import.</span></span>

<span data-ttu-id="c82e6-116">除了 Get-Counter 和 Export-Counter Cmdlet 之外，此功能還可讓您收集、匯出、匯入、合併、篩選、操作及重新匯出 Windows PowerShell 內的效能計數器資料。</span><span class="sxs-lookup"><span data-stu-id="c82e6-116">Along with the Get-Counter and Export-Counter cmdlets, this feature lets you collect, export, import, combine, filter, manipulate, and re-export performance counter data within Windows PowerShell.</span></span>

## <span data-ttu-id="c82e6-117">範例</span><span class="sxs-lookup"><span data-stu-id="c82e6-117">EXAMPLES</span></span>

### <span data-ttu-id="c82e6-118">範例1：從檔案匯入所有計數器資料</span><span class="sxs-lookup"><span data-stu-id="c82e6-118">Example 1: Import all counter data from a file</span></span>

```powershell
$Data = Import-Counter -Path ProcessorData.csv
```

<span data-ttu-id="c82e6-119">此命令會將 ProcessorData.csv 檔案中的所有計數器資料匯入 $Data 變數中。</span><span class="sxs-lookup"><span data-stu-id="c82e6-119">This command imports all counter data from the ProcessorData.csv file into the $Data variable.</span></span>

### <span data-ttu-id="c82e6-120">範例2：從檔案匯入特定計數器資料</span><span class="sxs-lookup"><span data-stu-id="c82e6-120">Example 2: Import specific counter data from a file</span></span>

```
PS C:\> $I = Import-Counter -Path "ProcessorData.blg" -Counter "\\SERVER01\Processor(_Total)\Interrupts/sec"
```

<span data-ttu-id="c82e6-121">此命令只會將 Processordata.blg .blg 檔案中的「 **處理器 (_total) \ 中斷數/秒** 」計數器資料匯入 $I 變數中。</span><span class="sxs-lookup"><span data-stu-id="c82e6-121">This command imports only the **"Processor(_total)\Interrupts/sec"** counter data from the ProcessorData.blg file into the $I variable.</span></span>

### <span data-ttu-id="c82e6-122">範例3：從效能計數器選取資料，然後將它匯出至檔案</span><span class="sxs-lookup"><span data-stu-id="c82e6-122">Example 3: Select data from a performance counter then export it to a file</span></span>

```
The first command uses **Import-Counter** to import all of the performance counter data from the ProcessorData.blg files. The command saves the data in the $Data variable.
PS C:\> $Data = Import-Counter .\ProcessorData.blg

The second command displays the counter paths in the $Data variable. To get the display shown in the command output, the example uses the Format-Table cmdlet to format as a table the counter paths of the first counter in the $Data variable.
PS C:\> $Data[0].CounterSamples | Format-Table -Property Path

Path
----
\\SERVER01\Processor(_Total)\DPC Rate
\\SERVER01\Processor(1)\DPC Rate
\\SERVER01\Processor(0)\DPC Rate
\\SERVER01\Processor(_Total)\% Idle Time
\\SERVER01\Processor(1)\% Idle Time
\\SERVER01\Processor(0)\% Idle Time
\\SERVER01\Processor(_Total)\% C3 Time
\\SERVER01\Processor(1)\% C3 Time

The third command gets the counter paths that end in "Interrupts/sec" and saves the paths in the $IntCtrs variable. It uses the Where-Object cmdlet to filter the counter paths and the ForEach-Object cmdlet to get only the value of the **Path** property of each selected path object.
PS C:\> $IntCtrs = $Data[0].Countersamples | Where-Object {$_.Path -like "*Interrupts/sec"} | ForEach-Object {$_.Path}

The fourth command displays the selected counter paths in the $IntCtrs variable.
PS C:\> $IntCtrs

\\SERVER01\Processor(_Total)\Interrupts/sec
\\SERVER01\Processor(1)\Interrupts/sec
\\SERVER01\Processor(0)\Interrupts/sec

The fifth command uses the **Import-Counter** cmdlet to import the data. It uses the $IntCtrs variable as the value of the *Counter* parameter to import only data for the counter paths in $IntCtrs.
PS C:\> $I = Import-Counter -Path .\ProcessorData.blg -Counter $intCtrs

The sixth command uses the Export-Counter cmdlet to export the data to the Interrupts.csv file.
PS C:\> $I | Export-Counter -Path .\Interrupts.csv -Format CSV
```

<span data-ttu-id="c82e6-123">此範例顯示如何從效能計數器記錄檔 (.blg) 中選取資料，然後將選取的資料匯出至 .csv 檔案。</span><span class="sxs-lookup"><span data-stu-id="c82e6-123">This example shows how to select data from a performance counter log file (.blg) and then export the selected data to a .csv file.</span></span>
<span data-ttu-id="c82e6-124">前四個命令會從檔案取得計數器路徑，並將其儲存在名為 $Data 的變數中。</span><span class="sxs-lookup"><span data-stu-id="c82e6-124">The first four commands get the counter paths from the file and save them in the variable named $Data.</span></span>
<span data-ttu-id="c82e6-125">最後兩個命令匯入選取的資料，然後只匯出選取的資料。</span><span class="sxs-lookup"><span data-stu-id="c82e6-125">The last two commands import selected data and then export only the selected data.</span></span>

### <span data-ttu-id="c82e6-126">範例4：顯示已匯入的計數器集合群組中的所有計數器路徑</span><span class="sxs-lookup"><span data-stu-id="c82e6-126">Example 4: Display all counter paths in a group of imported counter sets</span></span>

```
The first command uses the *ListSet* parameter of the **Import-Counter** cmdlet to get all of the counter sets that are represented in a counter data file.
PS C:\> Import-Counter -Path ProcessorData.csv -ListSet *

CounterSetName     : Processor
MachineName        : \\SERVER01
CounterSetType     : MultiInstance
Description        :
Paths              : {\\SERVER01\Processor(*)\DPC Rate, \\SERVER01\Processor(*)\% Idle Time, \\SERVER01
\Processor(*)\% C3 Time, \\SERVER01\Processor(*)\% Interrupt Time...}
PathsWithInstances : {\\SERVER01\Processor(_Total)\DPC Rate, \\SERVER01\Processor(1)\DPC Rate, \\SERVER01
\Processor(0)\DPC Rate, \\SERVER01\Processor(_Total)\% Idle Time...}
Counter            : {\\SERVER01\Processor(*)\DPC Rate, \\SERVER01\Processor(*)\% Idle Time, \\SERVER01
\Processor(*)\% C3 Time, \\SERVER01\Processor(*)\% Interrupt Time...}

The second command gets all of the counter paths from the list set.
PS C:\> Import-Counter -Path ProcessorData.csv -ListSet * | ForEach-Object {$_.Paths}

\\SERVER01\Processor(*)\DPC Rate
\\SERVER01\Processor(*)\% Idle Time
\\SERVER01\Processor(*)\% C3 Time
\\SERVER01\Processor(*)\% Interrupt Time
\\SERVER01\Processor(*)\% C2 Time
\\SERVER01\Processor(*)\% User Time
\\SERVER01\Processor(*)\% C1 Time
\\SERVER01\Processor(*)\% Processor Time
\\SERVER01\Processor(*)\C1 Transitions/sec
\\SERVER01\Processor(*)\% DPC Time
\\SERVER01\Processor(*)\C2 Transitions/sec
\\SERVER01\Processor(*)\% Privileged Time
\\SERVER01\Processor(*)\C3 Transitions/sec
\\SERVER01\Processor(*)\DPCs Queued/sec
\\SERVER01\Processor(*)\Interrupts/sec
```

<span data-ttu-id="c82e6-127">此範例示範如何顯示匯入的計數器集合群組中的所有的計數器路徑。</span><span class="sxs-lookup"><span data-stu-id="c82e6-127">This example shows how to display all the counter paths in a group of imported counter sets.</span></span>

### <span data-ttu-id="c82e6-128">範例5：從某個時間戳記範圍匯入計數器資料</span><span class="sxs-lookup"><span data-stu-id="c82e6-128">Example 5: Import counter data from a range of time stamps</span></span>

```
The first command lists in a table the time stamps of all of the data in the ProcessorData.blg file.
PS C:\> Import-Counter -Path ".\disk.blg" | Format-Table -Property Timestamp

The second command saves particular time stamps in the $Start and $End variables. The strings are cast to **DateTime** objects.
PS C:\> $Start = [datetime]"7/9/2008 3:47:00 PM"; $End = [datetime]"7/9/2008 3:47:59 PM"

The third command uses the **Import-Counter** cmdlet to get only counter data that has a time stamp between the start and end times (inclusive). The command uses the *StartTime* and *EndTime* parameters of **Import-Counter** to specify the range.
PS C:\> Import-Counter -Path Disk.blg -StartTime $start -EndTime $end
```

<span data-ttu-id="c82e6-129">此範例只會匯入時間戳記是在命令指定的開始與結束範圍之間的計數器資料。</span><span class="sxs-lookup"><span data-stu-id="c82e6-129">This example imports only the counter data that has a time stamp between the starting an ending ranges specified in the command.</span></span>

### <span data-ttu-id="c82e6-130">範例6：從效能計數器記錄檔匯入指定數目的最舊樣本</span><span class="sxs-lookup"><span data-stu-id="c82e6-130">Example 6: Import a specified number of the oldest samples from a performance counter log file</span></span>

```
The first command uses the **Import-Counter** cmdlet to import the first (oldest) five samples from the Disk.blg file. The command uses the *MaxSamples* parameter to limit the import to five counter samples.
PS C:\> Import-Counter -Path "Disk.blg" -MaxSamples 5

The second command uses array notation and the Windows PowerShell range operator (..) to get the last five counter samples from the file. These are the five newest samples.
PS C:\> (Import-Counter -Path Disk.blg)[-1 .. -5]
```

<span data-ttu-id="c82e6-131">此範例顯示如何從效能計數器記錄檔匯入五個最舊和五個最新的樣本。</span><span class="sxs-lookup"><span data-stu-id="c82e6-131">This example shows how to import the five oldest and five newest samples from a performance counter log file.</span></span>

### <span data-ttu-id="c82e6-132">範例7：從檔案取得計數器資料的摘要</span><span class="sxs-lookup"><span data-stu-id="c82e6-132">Example 7: Get a summary of counter data from a file</span></span>

```
PS C:\> Import-Counter "D:\Samples\Memory.blg" -Summary

OldestRecord            NewestRecord            SampleCount
------------            ------------            -----------
7/10/2008 2:59:18 PM    7/10/2008 3:00:27 PM    1000
```

<span data-ttu-id="c82e6-133">此命令使用 *Import-Counter* Cmdlet 的 **Summary** 參數，取得 Memory.blg 檔案中計數器資料的摘要。</span><span class="sxs-lookup"><span data-stu-id="c82e6-133">This command uses the *Summary* parameter of the **Import-Counter** cmdlet to get a summary of the counter data in the Memory.blg file.</span></span>

### <span data-ttu-id="c82e6-134">範例8：更新效能計數器記錄檔</span><span class="sxs-lookup"><span data-stu-id="c82e6-134">Example 8: Update a performance counter log file</span></span>

```
The first command uses the *ListSet* parameter of **Import-Counter** to get the counters in OldData.blg, an existing counter log file. The command uses a pipeline operator (|) to send the data to a ForEach-Object command that gets only the values of the **PathsWithInstances** property of each object
PS C:\> $Counters = Import-Counter OldData.blg -ListSet * | ForEach-Object {$_.PathsWithInstances}

The second command gets updated data for the counters in the $Counters variable. It uses the Get-Counter cmdlet to get a current sample, and then export the results to the NewData.blg file.
PS C:\> Get-Counter -Counter $Counters -MaxSamples 20 | Export-Counter C:\Logs\NewData.blg
```

<span data-ttu-id="c82e6-135">此範例會更新效能計數器記錄檔。</span><span class="sxs-lookup"><span data-stu-id="c82e6-135">This example updates a performance counter log file.</span></span>

### <span data-ttu-id="c82e6-136">範例9：從多個檔案匯入效能記錄資料，然後加以儲存</span><span class="sxs-lookup"><span data-stu-id="c82e6-136">Example 9: Import performance log data from multiple files and then save it</span></span>

```
PS C:\> $Counters = "D:\test\pdata.blg", "D:\samples\netlog.blg" | Import-Counter
```

<span data-ttu-id="c82e6-137">此命令從兩個記錄檔匯入效能記錄資料，並將資料儲存在 $Counters 變數中。</span><span class="sxs-lookup"><span data-stu-id="c82e6-137">This command imports performance log data from two logs and saves the data in the $Counters variable.</span></span>
<span data-ttu-id="c82e6-138">命令使用管線運算子將效能記錄檔路徑傳送至 Import-Counter，此 Cmdlet 會從指定的路徑匯入資料。</span><span class="sxs-lookup"><span data-stu-id="c82e6-138">The command uses a pipeline operator to send the performance log paths to Import-Counter, which imports the data from the specified paths.</span></span>

<span data-ttu-id="c82e6-139">請注意，每個路徑都以引號括住，而且路徑之間會以逗號分隔彼此。</span><span class="sxs-lookup"><span data-stu-id="c82e6-139">Notice that each path is enclosed in quotation marks and that the paths are separated from each other by a comma.</span></span>

## <span data-ttu-id="c82e6-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c82e6-140">PARAMETERS</span></span>

### <span data-ttu-id="c82e6-141">-Counter</span><span class="sxs-lookup"><span data-stu-id="c82e6-141">-Counter</span></span>

<span data-ttu-id="c82e6-142">將效能計數器指定為字串陣列。</span><span class="sxs-lookup"><span data-stu-id="c82e6-142">Specifies, as a string array, the performance counters.</span></span>
<span data-ttu-id="c82e6-143">依預設， **import-module** 會匯入輸入檔案中所有計數器的所有資料。</span><span class="sxs-lookup"><span data-stu-id="c82e6-143">By default, **Import-Counter** imports all data from all counters in the input files.</span></span>
<span data-ttu-id="c82e6-144">輸入一或多個計數器路徑。</span><span class="sxs-lookup"><span data-stu-id="c82e6-144">Enter one or more counter paths.</span></span>
<span data-ttu-id="c82e6-145">路徑中的執行個體部分允許萬用字元。</span><span class="sxs-lookup"><span data-stu-id="c82e6-145">Wildcards are permitted in the Instance part of the path.</span></span>

<span data-ttu-id="c82e6-146">每個計數器路徑都具有下列格式。</span><span class="sxs-lookup"><span data-stu-id="c82e6-146">Each counter path has the following format.</span></span>
<span data-ttu-id="c82e6-147">路徑中必須要有 ComputerName 值。</span><span class="sxs-lookup"><span data-stu-id="c82e6-147">The ComputerName value is required in the path.</span></span>
<span data-ttu-id="c82e6-148">例如：</span><span class="sxs-lookup"><span data-stu-id="c82e6-148">For instance:</span></span>

- `\\<ComputerName>\<CounterSet>(<Instance>)\<CounterName>`

<span data-ttu-id="c82e6-149">例如：</span><span class="sxs-lookup"><span data-stu-id="c82e6-149">For example:</span></span>

- `\\Server01\Processor(2)\% User Time`
- `\\Server01\Processor(*)\% Processor Time`

```yaml
Type: System.String[]
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: All counter
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="c82e6-150">-EndTime</span><span class="sxs-lookup"><span data-stu-id="c82e6-150">-EndTime</span></span>

<span data-ttu-id="c82e6-151">指定此 Cmdlet 在 *StartTime* 和 this 參數時間戳記之間匯入計數器資料的結束日期和時間。</span><span class="sxs-lookup"><span data-stu-id="c82e6-151">Specifies an end date and time that this cmdlet imports counter data between the *StartTime* and this parameter timestamps.</span></span>
<span data-ttu-id="c82e6-152">輸入 **DateTime** 物件，例如 Get-Date Cmdlet 所建立的物件。</span><span class="sxs-lookup"><span data-stu-id="c82e6-152">Enter a **DateTime** object, such as one created by the Get-Date cmdlet.</span></span>
<span data-ttu-id="c82e6-153">依預設， **import-module** 會匯入 *Path* 參數所指定之檔案中的所有計數器資料。</span><span class="sxs-lookup"><span data-stu-id="c82e6-153">By default, **Import-Counter** imports all counter data in the files specified by the *Path* parameter.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: No end time
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c82e6-154">-ListSet</span><span class="sxs-lookup"><span data-stu-id="c82e6-154">-ListSet</span></span>

<span data-ttu-id="c82e6-155">指定匯出檔案中代表的效能計數器集合。</span><span class="sxs-lookup"><span data-stu-id="c82e6-155">Specifies the performance counter sets that are represented in the exported files.</span></span>
<span data-ttu-id="c82e6-156">具有此參數的命令不會匯入任何資料。</span><span class="sxs-lookup"><span data-stu-id="c82e6-156">Commands with this parameter do not import any data.</span></span>

<span data-ttu-id="c82e6-157">輸入一或多個計數器集合名稱。</span><span class="sxs-lookup"><span data-stu-id="c82e6-157">Enter one or more counter set names.</span></span>
<span data-ttu-id="c82e6-158">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="c82e6-158">Wildcards are permitted.</span></span>
<span data-ttu-id="c82e6-159">若要取得檔案中的所有計數器集合，請輸入 `Import-Counter -ListSet *` 。</span><span class="sxs-lookup"><span data-stu-id="c82e6-159">To get all counter sets in the file, type `Import-Counter -ListSet *`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ListSetSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="c82e6-160">-MaxSamples</span><span class="sxs-lookup"><span data-stu-id="c82e6-160">-MaxSamples</span></span>

<span data-ttu-id="c82e6-161">指定每個計數器要匯入樣本的最大數目。</span><span class="sxs-lookup"><span data-stu-id="c82e6-161">Specifies the maximum number of samples of each counter to import.</span></span>
<span data-ttu-id="c82e6-162">依預設， **Get 計數器** 會匯入 *Path* 參數所指定之檔案中的所有資料。</span><span class="sxs-lookup"><span data-stu-id="c82e6-162">By default, **Get-Counter** imports all of the data in the files specified by the *Path* parameter.</span></span>

```yaml
Type: System.Int64
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: No maximum
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c82e6-163">-Path</span><span class="sxs-lookup"><span data-stu-id="c82e6-163">-Path</span></span>

<span data-ttu-id="c82e6-164">指定要匯入之檔案的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="c82e6-164">Specifies the file paths of the files to be imported.</span></span>
<span data-ttu-id="c82e6-165">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="c82e6-165">This parameter is required.</span></span>

<span data-ttu-id="c82e6-166">輸入您使用 **Export-Counter** Cmdlet 匯出之 .csv,,. tsv 或 .blg 檔案的路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="c82e6-166">Enter the path and file name of a, .csv,, .tsv, or .blg file that you exported by using the **Export-Counter** cmdlet.</span></span>
<span data-ttu-id="c82e6-167">您只可以指定一個 .csv 或 .tsv 檔案，但是您可以在每個命令中指定多個 (最多 32 個) .blg 檔案。</span><span class="sxs-lookup"><span data-stu-id="c82e6-167">You can specify only one .csv or .tsv file, but you can specify multiple .blg files (up to 32) in each command.</span></span>
<span data-ttu-id="c82e6-168">您也可以透過管線將檔案路徑字串 (在) 匯 **入-計數器** 的引號中。</span><span class="sxs-lookup"><span data-stu-id="c82e6-168">You can also pipe file path strings (in quotation marks) to **Import-Counter** .</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSPath

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="c82e6-169">-StartTime</span><span class="sxs-lookup"><span data-stu-id="c82e6-169">-StartTime</span></span>

<span data-ttu-id="c82e6-170">指定此 Cmdlet 取得計數器資料的開始日期和時間。</span><span class="sxs-lookup"><span data-stu-id="c82e6-170">Specifies the start date and time in which this cmdlet gets counter data.</span></span>
<span data-ttu-id="c82e6-171">輸入 **DateTime** 物件，例如「 **取得日期** 」 Cmdlet 所建立的物件。</span><span class="sxs-lookup"><span data-stu-id="c82e6-171">Enter a **DateTime** object, such as one created by the **Get-Date** cmdlet.</span></span>
<span data-ttu-id="c82e6-172">依預設， **import-module** 會匯入 *Path* 參數所指定之檔案中的所有計數器資料。</span><span class="sxs-lookup"><span data-stu-id="c82e6-172">By default, **Import-Counter** imports all counter data in the files specified by the *Path* parameter.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: No start time
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c82e6-173">-Summary</span><span class="sxs-lookup"><span data-stu-id="c82e6-173">-Summary</span></span>

<span data-ttu-id="c82e6-174">指出此 Cmdlet 會取得匯入資料的摘要，而不是取得個別計數器資料範例。</span><span class="sxs-lookup"><span data-stu-id="c82e6-174">Indicates that this cmdlet gets a summary of the imported data, instead of getting individual counter data samples.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SummarySet
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c82e6-175">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c82e6-175">CommonParameters</span></span>

<span data-ttu-id="c82e6-176">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="c82e6-176">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c82e6-177">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="c82e6-177">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c82e6-178">輸入</span><span class="sxs-lookup"><span data-stu-id="c82e6-178">INPUTS</span></span>

### <span data-ttu-id="c82e6-179">System.String</span><span class="sxs-lookup"><span data-stu-id="c82e6-179">System.String</span></span>

<span data-ttu-id="c82e6-180">您可以透過管線將效能計數器記錄檔路徑傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c82e6-180">You can pipe performance counter log paths to this cmdlet.</span></span>

## <span data-ttu-id="c82e6-181">輸出</span><span class="sxs-lookup"><span data-stu-id="c82e6-181">OUTPUTS</span></span>

### <span data-ttu-id="c82e6-182">Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet、Microsoft.PowerShell.Commands.GetCounter.CounterSet、Microsoft.PowerShell.Commands.GetCounter.CounterFileInfo</span><span class="sxs-lookup"><span data-stu-id="c82e6-182">Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet, Microsoft.PowerShell.Commands.GetCounter.CounterSet, Microsoft.PowerShell.Commands.GetCounter.CounterFileInfo</span></span>

<span data-ttu-id="c82e6-183">這個 Cmdlet 會傳回 **會傳回 microsoft.powershell.commands.getcounter.counterset. PerformanceCounterSampleSet** 。</span><span class="sxs-lookup"><span data-stu-id="c82e6-183">This cmdlet returns a **Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet** .</span></span>
<span data-ttu-id="c82e6-184">如果您使用 *ListSet* 參數，這個 Cmdlet 會傳回 **會傳回 microsoft.powershell.commands.getcounter.counterset** 物件。</span><span class="sxs-lookup"><span data-stu-id="c82e6-184">If you use the *ListSet* parameter, this cmdlet returns a **Microsoft.PowerShell.Commands.GetCounter.CounterSet** object.</span></span>
<span data-ttu-id="c82e6-185">如果您使用 *Summary* 參數，這個 Cmdlet 會傳回 **會傳回 microsoft.powershell.commands.getcounter.counterset. microsoft.powershell.commands.getcounter.counterfileinfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="c82e6-185">If you use the *Summary* parameter, this cmdlet returns a **Microsoft.PowerShell.Commands.GetCounter.CounterFileInfo** object.</span></span>

## <span data-ttu-id="c82e6-186">注意</span><span class="sxs-lookup"><span data-stu-id="c82e6-186">NOTES</span></span>

* <span data-ttu-id="c82e6-187">此 Cmdlet 沒有 *ComputerName* 參數。</span><span class="sxs-lookup"><span data-stu-id="c82e6-187">This cmdlet does not have a *ComputerName* parameter.</span></span> <span data-ttu-id="c82e6-188">但是，如果電腦設定為 Windows PowerShell 遠端處理，您可以使用 Invoke-Command Cmdlet 在遠端電腦上執行 [匯 **入-計數器** ] 命令。</span><span class="sxs-lookup"><span data-stu-id="c82e6-188">However, if the computer is configured for Windows PowerShell remoting, you can use the Invoke-Command cmdlet to run an **Import-Counter** command on a remote computer.</span></span>

## <span data-ttu-id="c82e6-189">相關連結</span><span class="sxs-lookup"><span data-stu-id="c82e6-189">RELATED LINKS</span></span>

[<span data-ttu-id="c82e6-190">Export-Counter</span><span class="sxs-lookup"><span data-stu-id="c82e6-190">Export-Counter</span></span>](Export-Counter.md)

[<span data-ttu-id="c82e6-191">Get-Counter</span><span class="sxs-lookup"><span data-stu-id="c82e6-191">Get-Counter</span></span>](Get-Counter.md)
