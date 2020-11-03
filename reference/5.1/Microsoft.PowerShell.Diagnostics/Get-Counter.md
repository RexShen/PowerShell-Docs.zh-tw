---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 10/30/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/get-counter?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Counter
ms.openlocfilehash: 7c1ab665fc7ffddc54ec936f80b76b4329291a3b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202628"
---
# Get-Counter

## 概要
從本機電腦和遠端電腦取得效能計數器資料。

## SYNTAX

### GetCounterSet (預設值)

```
Get-Counter [[-Counter] <String[]>] [-SampleInterval <Int32>] [-MaxSamples <Int64>] [-Continuous]
 [-ComputerName <String[]>] [<CommonParameters>]
```

### ListSetSet

```
Get-Counter [-ListSet] <String[]> [-ComputerName <String[]>] [<CommonParameters>]
```

## DESCRIPTION

指令程式會 `Get-Counter` 直接從 Windows 系列作業系統的效能監視檢測中取得效能計數器資料。 `Get-Counter` 從本機電腦或遠端電腦取得效能資料。

您可以使用 `Get-Counter` 參數來指定一或多部電腦、列出效能計數器集合，以及它們所包含的實例、設定取樣間隔，以及指定最大樣本數。 如果沒有參數，會 `Get-Counter` 取得一組系統計數器的效能計數器資料。

許多計數器集合受 (ACL) 的存取控制清單保護。 若要查看所有計數器集合，請使用 [以 **系統管理員身分執行** ] 選項開啟 PowerShell。

## 範例

### 範例1：取得計數器集合清單

這個範例會取得本機電腦的計數器集合清單。

```powershell
Get-Counter -ListSet *
```

```Output
CounterSetName     : Processor
MachineName        : .
CounterSetType     : MultiInstance
Description        : The Processor performance object consists of counters that measure aspects ...
                     computer that performs arithmetic and logical computations, initiates ...
                     computer can have multiple processors.  The processor object represents ...
Paths              : {\Processor(*)\% Processor Time, \Processor(*)\% User Time, ...
PathsWithInstances : {\Processor(0)\% Processor Time, \Processor(1)\% Processor Time, ...
Counter            : {\Processor(*)\% Processor Time, \Processor(*)\% User Time, ...
```

`Get-Counter` 使用 **ListSet** 參數搭配星號 (`*`) 來取得計數器集合的清單。
`.` **MachineName** 資料行中)  (的點代表本機電腦。

### 範例2：指定 SampleInterval 和 MaxSamples

此範例會取得本機電腦上所有處理器的計數器資料。 資料會以兩秒的間隔收集，直到有三個樣本為止。

```powershell
Get-Counter -Counter "\Processor(_Total)\% Processor Time" -SampleInterval 2 -MaxSamples 3
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/18/2019 14:39:56        \\Computer01\processor(_total)\% processor time :
                          20.7144271584086

6/18/2019 14:39:58        \\Computer01\processor(_total)\% processor time :
                          10.4391790575511

6/18/2019 14:40:01        \\Computer01\processor(_total)\% processor time :
                          37.5968799396998
```

`Get-Counter` 使用 **counter** 參數來指定計數器路徑 `\Processor(_Total)\% Processor Time` 。 **SampleInterval** 參數會設定兩秒間隔以檢查計數器。 **MaxSamples** 會判斷三個是檢查計數器的最大次數。

### 範例3：取得計數器的連續範例

此範例會每秒取得計數器的連續範例。 若要停止命令，請按下<kbd>CTRL</kbd> + <kbd>C</kbd>。 若要指定樣本之間較長的間隔，請使用 **SampleInterval** 參數。

```powershell
Get-Counter -Counter "\Processor(_Total)\% Processor Time" -Continuous
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/19/2019 15:35:03        \\Computer01\processor(_total)\% processor time :
                          43.8522842937022

6/19/2019 15:35:04        \\Computer01\processor(_total)\% processor time :
                          29.7896844697383

6/19/2019 15:35:05        \\Computer01\processor(_total)\% processor time :
                          29.4962645638135

6/19/2019 15:35:06        \\Computer01\processor(_total)\% processor time :
                          25.5901500127408
```

`Get-Counter` 使用 **counter** 參數來指定 `\Processor\% Processor Time` 計數器。
**連續** 參數指定每秒取得範例，直到命令以 <kbd>CTRL</kbd> + <kbd>C</kbd>停止為止。

### 範例4：依字母順序排列的計數器集合清單

此範例會使用管線來取得計數器清單集，然後依字母順序排序清單。

```powershell
Get-Counter -ListSet * | Sort-Object -Property CounterSetName | Format-Table -AutoSize
```

```Output
CounterSetName                        MachineName CounterSetType  Description
--------------                        ----------- --------------  -----------
.NET CLR Data                         .           SingleInstance  .Net CLR Data
.NET Data Provider for SqlServer      .           SingleInstance  Counters for System.Data.SqlClient
AppV Client Streamed Data Percentage  .           SingleInstance  Size of data streamed to disk ...
Authorization Manager Applications    .           SingleInstance  The set of Counters for ...
BitLocker                             .           MultiInstance   BitLocker Drive Encryption ...
Bluetooth Device                      .           SingleInstance  Counters related to a remote ...
Cache                                 .           SingleInstance  The Cache performance object ...
Client Side Caching                   .           SingleInstance  Performance counters for SMB ...
```

`Get-Counter` 使用 **ListSet** 參數搭配星號 (`*`) 來取得計數器集合的完整清單。 **CounterSet** 物件會沿著管線向下傳送。 `Sort-Object` 使用 **Property** 參數來指定依 **CounterSetName** 排序物件。 物件會向下傳送到管線 `Format-Table` 。 **AutoSize** 參數會調整資料行寬度，以將截斷降至最低。

`.` **MachineName** 資料行中)  (的點代表本機電腦。

### 範例5：執行背景工作以取得計數器資料

在此範例中，會在 `Start-Job` `Get-Counter` 本機電腦上以背景工作方式執行命令。
若要查看作業的效能計數器輸出，請使用 `Receive-Job` Cmdlet。

```powershell
Start-Job -ScriptBlock {Get-Counter -Counter "\LogicalDisk(_Total)\% Free Space" -MaxSamples 1000}
```

```Output
Id     Name  PSJobTypeName   State    HasMoreData  Location   Command
--     ----  -------------   -----    -----------  --------   -------
1      Job1  BackgroundJob   Running  True         localhost  Get-Counter -Counter
```

`Start-Job` 使用 **ScriptBlock** 參數來執行 `Get-Counter` 命令。 `Get-Counter` 使用 **counter** 參數來指定計數器路徑 `\LogicalDisk(_Total)\% Free Space` 。 **MaxSamples** 參數會指定取得計數器的1000樣本。

### 範例6：從多部電腦取得計數器資料

此範例會使用變數，從兩部電腦取得效能計數器資料。

```powershell
$DiskReads = "\LogicalDisk(C:)\Disk Reads/sec"
$DiskReads | Get-Counter -ComputerName Server01, Server02 -MaxSamples 10
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/21/2019 10:51:04        \\Server01\logicaldisk(c:)\disk reads/sec :
                          0

                          \\Server02\logicaldisk(c:)\disk reads/sec :
                          0.983050344269146
```

`$DiskReads`變數會儲存 `\LogicalDisk(C:)\Disk Reads/sec` 計數器路徑。 `$DiskReads`變數會沿著管線向下傳送至 `Get-Counter` 。 **計數器** 是第一個位置參數，並接受中儲存的路徑 `$DiskReads` 。 **ComputerName** 指定兩部電腦和 **MaxSamples** 指定要從每部電腦取得10個樣本。

### 範例7：從多部隨機電腦取得計數器的實例值

此範例會取得企業中50隨機遠端電腦的效能計數器值。 **ComputerName** 參數會使用儲存在變數中的隨機電腦名稱稱。 若要更新變數中的電腦名稱稱，請重新建立變數。

**ComputerName** 參數中伺服器名稱的替代方案是使用文字檔。 例如：

`-ComputerName (Get-Random (Get-Content -Path C:\Servers.txt) -Count 50)`

計數器路徑在 `*` 實例名稱中包含星號 () ，以取得每個遠端電腦處理器的資料。

```powershell
$Servers = Get-Random (Get-Content -Path C:\Servers.txt) -Count 50
$Counter = "\Processor(*)\% Processor Time"
Get-Counter -Counter $Counter -ComputerName $Servers
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/20/2019 12:20:35        \\Server01\processor(0)\% processor time :
                          6.52610319637854

                          \\Server01\processor(1)\% processor time :
                          3.41030663625782

                          \\Server01\processor(2)\% processor time :
                          9.64189975649925

                          \\Server01\processor(3)\% processor time :
                          1.85240835619747

                          \\Server01\processor(_total)\% processor time :
                          5.35768447160776
```

此 `Get-Random` Cmdlet 會使用 `Get-Content` 從檔案選取50隨機電腦名稱稱 `Servers.txt` 。 遠端電腦名稱稱會儲存在變數中 `$Servers` 。 `\Processor(*)\% Processor Time`計數器的路徑會儲存在變數中 `$Counter` 。 `Get-Counter` 使用 **Counter** 參數來指定變數中的計數器 `$Counter` 。 **ComputerName** 參數會指定變數中的電腦名稱稱 `$Servers` 。

### 範例8：使用 Path 屬性來取得格式化的路徑名稱

此範例會使用計數器集合的 **path** 屬性來尋找效能計數器的格式化路徑名稱。

管線會與 Cmdlet 搭配使用 `Where-Object` ，以尋找路徑名稱的子集。 若要尋找計數器集合計數器路徑的完整清單，請 (`|`) 和命令移除管線 `Where-Object` 。

`$_`是管線中目前物件的自動變數。
如需詳細資訊，請參閱 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)。

```powershell
(Get-Counter -ListSet Memory).Paths | Where-Object { $_ -like "*Cache*" }
```

```Output
\Memory\Cache Faults/sec
\Memory\Cache Bytes
\Memory\Cache Bytes Peak
\Memory\System Cache Resident Bytes
\Memory\Standby Cache Reserve Bytes
\Memory\Standby Cache Normal Priority Bytes
\Memory\Standby Cache Core Bytes
\Memory\Long-Term Average Standby Cache Lifetime (s)
```

`Get-Counter` 使用 **ListSet** 參數來指定 **記憶體** 計數器集合。 此命令會以括弧括住，讓 [ **路徑** ] 屬性以字串形式傳回每個路徑。 物件會向下傳送到管線 `Where-Object` 。 `Where-Object` 使用變數 `$_` 來處理每個物件，並使用 `-like` 運算子來尋找字串的相符專案 `*Cache*` 。 星號 (`*`) 是任何字元的萬用字元。

### 範例9：使用 PathsWithInstances 屬性來取得格式化的路徑名稱

這個範例會取得格式化的路徑名稱，其中包含 **PhysicalDisk** 效能計數器的實例。

```powershell
(Get-Counter -ListSet PhysicalDisk).PathsWithInstances
```

```Output
\PhysicalDisk(0 C:)\Current Disk Queue Length
\PhysicalDisk(_Total)\Current Disk Queue Length
\PhysicalDisk(0 C:)\% Disk Time
\PhysicalDisk(_Total)\% Disk Time
\PhysicalDisk(0 C:)\Avg. Disk Queue Length
\PhysicalDisk(_Total)\Avg. Disk Queue Length
\PhysicalDisk(0 C:)\% Disk Read Time
\PhysicalDisk(_Total)\% Disk Read Time
```

`Get-Counter` 使用 **ListSet** 參數來指定 **PhysicalDisk** 計數器集合。 此命令會以括弧括住，讓 **PathsWithInstances** 屬性以字串形式傳回每個路徑實例。

### 範例10：為計數器集合中的每個計數器取得單一值

在此範例中，會針對本機電腦的 **Memory** 計數器集合中的每個效能計數器傳回單一值。

```powershell
$MemCounters = (Get-Counter -ListSet Memory).Paths
Get-Counter -Counter $MemCounters
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/19/2019 12:05:00        \\Computer01\memory\page faults/sec :
                          868.772077545597

                          \\Computer01\memory\available bytes :
                          9031176192

                          \\Computer01\memory\committed bytes :
                          8242982912

                          \\Computer01\memory\commit limit :
                          19603333120
```

`Get-Counter` 使用 **ListSet** 參數來指定 **記憶體** 計數器集合。 此命令會以括弧括住，讓 [ **路徑** ] 屬性以字串形式傳回每個路徑。 路徑會儲存在變數中 `$MemCounters` 。 `Get-Counter` 使用 **counter** 參數來指定變數中的計數器路徑 `$MemCounters` 。

### 範例11：顯示物件的屬性值

**PerformanceCounterSample** 物件中的屬性值代表每個資料範例。 在此範例中，我們使用 **CounterSamples** 物件的屬性來檢查、選取、排序及分組資料。

```powershell
$Counter = "\\Server01\Process(Idle)\% Processor Time"
$Data = Get-Counter $Counter
$Data.CounterSamples | Format-List -Property *
```

```Output
Path             : \\Server01\process(idle)\% processor time
InstanceName     : idle
CookedValue      : 198.467899571389
RawValue         : 14329160321003
SecondValue      : 128606459528326201
MultipleCount    : 1
CounterType      : Timer100Ns
Timestamp        : 6/19/2019 12:20:49
Timestamp100NSec : 128606207528320000
Status           : 0
DefaultScale     : 0
TimeBase         : 10000000
```

計數器路徑儲存在 `$Counter` 變數中。 `Get-Counter` 取得計數器值的一個樣本，並將結果儲存在 `$Data` 變數中。 `$Data`變數使用 **CounterSamples** 屬性來取得物件的屬性。 物件會向下傳送到管線 `Format-List` 。 **Property** 參數使用星號 (`*`) 萬用字元來選取所有屬性。

### 範例12：效能計數器陣列值

在此範例中，變數會儲存每個效能計數器。 **CounterSamples** 屬性是可以顯示特定計數器值的陣列。

若要顯示每個計數器範例，請使用 `$Counter.CounterSamples` 。

```powershell
$Counter = Get-Counter -Counter "\Processor(*)\% Processor Time"
$Counter.CounterSamples[0]
```

```Output
Path                                         InstanceName        CookedValue
----                                         ------------        -----------
\\Computer01\processor(0)\% processor time   0              1.33997091699662
```

`Get-Counter` 使用 **counter** 參數來指定計數器 `\Processor(*)\% Processor Time` 。 這些值會儲存在 `$Counter` 變數中。
`$Counter.CounterSamples[0]` 顯示第一個計數器值的陣列值。

### 範例13：比較效能計數器值

此範例會尋找本機電腦上每個處理器所使用的處理器時間量。 **CounterSamples** 屬性是用來比較計數器資料與指定的值。

若要顯示每個計數器範例，請使用 `$Counter.CounterSamples` 。

```powershell
$Counter = Get-Counter -Counter "\Processor(*)\% Processor Time"
$Counter.CounterSamples | Where-Object { $_.CookedValue -lt "20" }
```

```Output
Path                                         InstanceName        CookedValue
----                                         ------------        -----------
\\Computer01\processor(0)\% processor time   0              12.6398025240208
\\Computer01\processor(1)\% processor time   1              15.7598095767344
```

`Get-Counter` 使用 **counter** 參數來指定計數器 `\Processor(*)\% Processor Time` 。 這些值會儲存在 `$Counter` 變數中。 中儲存的物件 `$Counter.CounterSamples` 會向下傳送到管線。 `Where-Object` 使用腳本區塊，將每個物件的值與指定的20值進行比較。 `$_.CookedValue`是管線中目前物件的變數。 **CookedValue** 小於20的計數器隨即顯示。

### 範例14：排序效能計數器資料

此範例顯示如何排序效能計數器資料。 此範例會尋找電腦上，在取樣期間使用最多處理器時間的處理常式。

```powershell
$Procs = Get-Counter -Counter "\Process(*)\% Processor Time"
$Procs.CounterSamples | Sort-Object -Property CookedValue -Descending |
   Format-Table -Property Path, InstanceName, CookedValue -AutoSize
```

```Output
Path                                                         InstanceName             CookedValue
----                                                         ------------             -----------
\\Computer01\process(_total)\% processor time                _total              395.464129650573
\\Computer01\process(idle)\% processor time                  idle                389.356575524695
\\Computer01\process(mssense)\% processor time               mssense             3.05377706293879
\\Computer01\process(csrss#1)\% processor time               csrss               1.52688853146939
\\Computer01\process(microsoftedgecp#10)\% processor time    microsoftedgecp     1.52688853146939
\\Computer01\process(runtimebroker#5)\% processor time       runtimebroker                      0
\\Computer01\process(settingsynchost)\% processor time       settingsynchost                    0
\\Computer01\process(microsoftedgecp#16)\% processor time    microsoftedgecp                    0
```

`Get-Counter` 使用 **counter** 參數來指定 `\Process(*)\% Processor Time` 本機電腦上所有處理常式的計數器。 結果會儲存在變數中 `$Procs` 。 `$Procs`具有 **CounterSamples** 屬性的變數會將 **PerformanceCounterSample** 物件沿著管線向下傳送。 `Sort-Object` 使用 **Property** 參數，依 **CookedValue** 以 **遞減** 順序排序物件。 `Format-Table` 使用 **Property** 參數來選取輸出的資料行。 **AutoSize** 參數會調整資料行寬度，以將截斷降至最低。

## PARAMETERS

### -ComputerName

指定一或多個電腦名稱稱，或一組以逗號分隔的 **遠端** 電腦名稱稱。 使用 NetBIOS 名稱、IP 位址或電腦的完整功能變數名稱。

若要從 **本機** 電腦取得效能計數器資料，請排除 **ComputerName** 參數。
針對包含 **MachineName** 資料行之 **ListSet** 的輸出， `.`) 表示本機電腦的點 (。

`Get-Counter` 不依賴 PowerShell 遠端功能。 即使您的電腦未設定為執行遠端命令，您也可以使用 **ComputerName** 參數。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Continuous

指定 **連續** 時，會 `Get-Counter` 取得範例，直到您按下 <kbd>CTRL</kbd> + <kbd>C</kbd>。 每秒都會針對每個指定的效能計數器取得範例。 使用 **SampleInterval** 參數可增加連續範例之間的間隔。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Counter

指定一或多個計數器路徑的路徑。 路徑會輸入為以逗號分隔的陣列、變數或文字檔中的值。 您可以向下傳送管線的計數器路徑字串至 `Get-Counter` 。

計數器路徑使用下列語法：

`\\ComputerName\CounterSet(Instance)\CounterName`

`\CounterSet(Instance)\CounterName`

例如：

`\\Server01\Processor(*)\% User Time`

`\Processor(*)\% User Time`

在 `\\ComputerName` 效能計數器路徑中是選擇性的。 如果計數器路徑未包含電腦名稱稱，則會 `Get-Counter` 使用本機電腦。

實例中的星號 (`*`) 是取得計數器所有實例的萬用字元。

```yaml
Type: System.String[]
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -ListSet

列出電腦上的效能計數器集合。 使用星號 (`*`) 來指定所有計數器集合。 輸入一個名稱或以逗號分隔的計數器集合名稱字串。 您可以將計數器集合名稱向下傳送到管線。

若要取得計數器集合格式化的計數器路徑，請使用 **ListSet** 參數。 每個計數器集合的 **路徑** 和 **PathsWithInstances** 屬性包含格式為字串的個別計數器路徑。

您可以將計數器路徑字串儲存在變數中，或使用管線將字串傳送至另一個 `Get-Counter` 命令。

例如，將每個 **處理器** 計數器路徑傳送至 `Get-Counter` ：

`Get-Counter -ListSet Processor | Get-Counter`

```yaml
Type: System.String[]
Parameter Sets: ListSetSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### -MaxSamples

指定要從每個指定效能計數器取得的樣本數目。 若要取得範例的常數資料流程，請使用 **連續** 參數。

如果未指定 **MaxSamples** 參數，則 `Get-Counter` 只會針對每個指定的計數器取得一個樣本。

若要收集大型資料集，請以 `Get-Counter` PowerShell 背景工作的形式執行。 如需詳細資訊，請參閱 [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md)。

```yaml
Type: System.Int64
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SampleInterval

指定每個指定效能計數器樣本之間的秒數。 如果未指定 **SampleInterval** 參數，則會 `Get-Counter` 使用一秒的間隔。

```yaml
Type: System.Int32
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String[]

`Get-Counter` 接受計數器路徑和計數器集合名稱的管線輸入。

## 輸出

### 會傳回 microsoft.powershell.commands.getcounter.counterset，會傳回 microsoft.powershell.commands.getcounter.counterset. PerformanceCounterSampleSet，.，，會傳回 microsoft.powershell.commands.getcounter.counterset. PerformanceCounterSample <。

若要查看物件的屬性，請向下傳送管線的輸出 `Get-Member` 。 輸出的物件類型如下所示：

**ListSet** 參數： **會傳回 microsoft.powershell.commands.getcounter.counterset 的命令**

**Counter** 參數： **會傳回 microsoft.powershell.commands.getcounter.counterset. PerformanceCounterSampleSet**

**CounterSamples** 屬性： **會傳回 microsoft.powershell.commands.getcounter.counterset. PerformanceCounterSample**

## 注意

如果未指定任何參數，則會 `Get-Counter` 為每個指定的效能計數器取得一個樣本。 使用 **MaxSamples** 和 **連續** 參數來取得更多範例。

`Get-Counter` 使用樣本之間的一秒間隔。 使用 **SampleInterval** 參數來增加間隔。

**MaxSamples** 和 **SampleInterval** 值適用于命令中每部電腦上的所有計數器。 若要為不同的計數器設定不同的值，請輸入不同的 `Get-Counter` 命令。

## 相關連結

[about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md)

[Format-List](../Microsoft.PowerShell.Utility/Format-List.md)

[Format-Table](../Microsoft.PowerShell.Utility/Format-Table.md)

[Get-Member](../Microsoft.PowerShell.Utility/Get-Member.md)

[Receive-Job](../Microsoft.PowerShell.Core/Receive-Job.md)

[Start-Job](../Microsoft.PowerShell.Core/Start-Job.md)

[Where-Object](..//Microsoft.PowerShell.Core/Where-Object.md)
