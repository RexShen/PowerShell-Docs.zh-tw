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
# Import-Counter

## 概要
匯入效能計數器記錄檔，並建立代表記錄檔中每個計數器樣本的物件。

## SYNTAX

### GetCounterSet (預設值)

```
Import-Counter [-Path] <String[]> [-StartTime <DateTime>] [-EndTime <DateTime>] [-Counter <String[]>]
 [-MaxSamples <Int64>] [<CommonParameters>]
```

### ListSetSet

```
Import-Counter [-Path] <String[]> -ListSet <String[]> [<CommonParameters>]
```

### SummarySet

```
Import-Counter [-Path] <String[]> [-Summary] [<CommonParameters>]
```

## DESCRIPTION

**Import-module** Cmdlet 會從效能計數器記錄檔匯入效能計數器資料，並為檔案中的每個計數器樣本建立物件。
它所建立的 **PerformanceCounterSampleSet** 物件與在收集效能計數器資料 **時，會傳回的物件** 完全相同。

您可以從逗點分隔值 (.csv)、Tab 分隔值 (.tsv) 與二進位效能記錄檔 (.blg) 效能記錄檔匯入資料。
如果您使用的是 .blg 檔案，您可以在每個命令中匯入多達32的檔案。
您可以使用 [匯 **入-計數器** ] 的參數來篩選您匯入的資料。

除了 Get-Counter 和 Export-Counter Cmdlet 之外，此功能還可讓您收集、匯出、匯入、合併、篩選、操作及重新匯出 Windows PowerShell 內的效能計數器資料。

## 範例

### 範例1：從檔案匯入所有計數器資料

```powershell
$Data = Import-Counter -Path ProcessorData.csv
```

此命令會將 ProcessorData.csv 檔案中的所有計數器資料匯入 $Data 變數中。

### 範例2：從檔案匯入特定計數器資料

```
PS C:\> $I = Import-Counter -Path "ProcessorData.blg" -Counter "\\SERVER01\Processor(_Total)\Interrupts/sec"
```

此命令只會將 Processordata.blg .blg 檔案中的「 **處理器 (_total) \ 中斷數/秒** 」計數器資料匯入 $I 變數中。

### 範例3：從效能計數器選取資料，然後將它匯出至檔案

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

此範例顯示如何從效能計數器記錄檔 (.blg) 中選取資料，然後將選取的資料匯出至 .csv 檔案。
前四個命令會從檔案取得計數器路徑，並將其儲存在名為 $Data 的變數中。
最後兩個命令匯入選取的資料，然後只匯出選取的資料。

### 範例4：顯示已匯入的計數器集合群組中的所有計數器路徑

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

此範例示範如何顯示匯入的計數器集合群組中的所有的計數器路徑。

### 範例5：從某個時間戳記範圍匯入計數器資料

```
The first command lists in a table the time stamps of all of the data in the ProcessorData.blg file.
PS C:\> Import-Counter -Path ".\disk.blg" | Format-Table -Property Timestamp

The second command saves particular time stamps in the $Start and $End variables. The strings are cast to **DateTime** objects.
PS C:\> $Start = [datetime]"7/9/2008 3:47:00 PM"; $End = [datetime]"7/9/2008 3:47:59 PM"

The third command uses the **Import-Counter** cmdlet to get only counter data that has a time stamp between the start and end times (inclusive). The command uses the *StartTime* and *EndTime* parameters of **Import-Counter** to specify the range.
PS C:\> Import-Counter -Path Disk.blg -StartTime $start -EndTime $end
```

此範例只會匯入時間戳記是在命令指定的開始與結束範圍之間的計數器資料。

### 範例6：從效能計數器記錄檔匯入指定數目的最舊樣本

```
The first command uses the **Import-Counter** cmdlet to import the first (oldest) five samples from the Disk.blg file. The command uses the *MaxSamples* parameter to limit the import to five counter samples.
PS C:\> Import-Counter -Path "Disk.blg" -MaxSamples 5

The second command uses array notation and the Windows PowerShell range operator (..) to get the last five counter samples from the file. These are the five newest samples.
PS C:\> (Import-Counter -Path Disk.blg)[-1 .. -5]
```

此範例顯示如何從效能計數器記錄檔匯入五個最舊和五個最新的樣本。

### 範例7：從檔案取得計數器資料的摘要

```
PS C:\> Import-Counter "D:\Samples\Memory.blg" -Summary

OldestRecord            NewestRecord            SampleCount
------------            ------------            -----------
7/10/2008 2:59:18 PM    7/10/2008 3:00:27 PM    1000
```

此命令使用 *Import-Counter* Cmdlet 的 **Summary** 參數，取得 Memory.blg 檔案中計數器資料的摘要。

### 範例8：更新效能計數器記錄檔

```
The first command uses the *ListSet* parameter of **Import-Counter** to get the counters in OldData.blg, an existing counter log file. The command uses a pipeline operator (|) to send the data to a ForEach-Object command that gets only the values of the **PathsWithInstances** property of each object
PS C:\> $Counters = Import-Counter OldData.blg -ListSet * | ForEach-Object {$_.PathsWithInstances}

The second command gets updated data for the counters in the $Counters variable. It uses the Get-Counter cmdlet to get a current sample, and then export the results to the NewData.blg file.
PS C:\> Get-Counter -Counter $Counters -MaxSamples 20 | Export-Counter C:\Logs\NewData.blg
```

此範例會更新效能計數器記錄檔。

### 範例9：從多個檔案匯入效能記錄資料，然後加以儲存

```
PS C:\> $Counters = "D:\test\pdata.blg", "D:\samples\netlog.blg" | Import-Counter
```

此命令從兩個記錄檔匯入效能記錄資料，並將資料儲存在 $Counters 變數中。
命令使用管線運算子將效能記錄檔路徑傳送至 Import-Counter，此 Cmdlet 會從指定的路徑匯入資料。

請注意，每個路徑都以引號括住，而且路徑之間會以逗號分隔彼此。

## PARAMETERS

### -Counter

將效能計數器指定為字串陣列。
依預設， **import-module** 會匯入輸入檔案中所有計數器的所有資料。
輸入一或多個計數器路徑。
路徑中的執行個體部分允許萬用字元。

每個計數器路徑都具有下列格式。
路徑中必須要有 ComputerName 值。
例如：

- `\\<ComputerName>\<CounterSet>(<Instance>)\<CounterName>`

例如：

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

### -EndTime

指定此 Cmdlet 在 *StartTime* 和 this 參數時間戳記之間匯入計數器資料的結束日期和時間。
輸入 **DateTime** 物件，例如 Get-Date Cmdlet 所建立的物件。
依預設， **import-module** 會匯入 *Path* 參數所指定之檔案中的所有計數器資料。

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

### -ListSet

指定匯出檔案中代表的效能計數器集合。
具有此參數的命令不會匯入任何資料。

輸入一或多個計數器集合名稱。
允許使用萬用字元。
若要取得檔案中的所有計數器集合，請輸入 `Import-Counter -ListSet *` 。

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

### -MaxSamples

指定每個計數器要匯入樣本的最大數目。
依預設， **Get 計數器** 會匯入 *Path* 參數所指定之檔案中的所有資料。

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

### -Path

指定要匯入之檔案的檔案路徑。
這是必要參數。

輸入您使用 **Export-Counter** Cmdlet 匯出之 .csv,,. tsv 或 .blg 檔案的路徑和檔案名。
您只可以指定一個 .csv 或 .tsv 檔案，但是您可以在每個命令中指定多個 (最多 32 個) .blg 檔案。
您也可以透過管線將檔案路徑字串 (在) 匯 **入-計數器** 的引號中。

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

### -StartTime

指定此 Cmdlet 取得計數器資料的開始日期和時間。
輸入 **DateTime** 物件，例如「 **取得日期** 」 Cmdlet 所建立的物件。
依預設， **import-module** 會匯入 *Path* 參數所指定之檔案中的所有計數器資料。

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

### -Summary

指出此 Cmdlet 會取得匯入資料的摘要，而不是取得個別計數器資料範例。

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

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

您可以透過管線將效能計數器記錄檔路徑傳送至此 Cmdlet。

## 輸出

### Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet、Microsoft.PowerShell.Commands.GetCounter.CounterSet、Microsoft.PowerShell.Commands.GetCounter.CounterFileInfo

這個 Cmdlet 會傳回 **會傳回 microsoft.powershell.commands.getcounter.counterset. PerformanceCounterSampleSet** 。
如果您使用 *ListSet* 參數，這個 Cmdlet 會傳回 **會傳回 microsoft.powershell.commands.getcounter.counterset** 物件。
如果您使用 *Summary* 參數，這個 Cmdlet 會傳回 **會傳回 microsoft.powershell.commands.getcounter.counterset. microsoft.powershell.commands.getcounter.counterfileinfo** 物件。

## 注意

* 此 Cmdlet 沒有 *ComputerName* 參數。 但是，如果電腦設定為 Windows PowerShell 遠端處理，您可以使用 Invoke-Command Cmdlet 在遠端電腦上執行 [匯 **入-計數器** ] 命令。

## 相關連結

[Export-Counter](Export-Counter.md)

[Get-Counter](Get-Counter.md)
