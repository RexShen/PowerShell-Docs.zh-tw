---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 11/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/get-counter?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Counter
ms.openlocfilehash: b8b78c0a2dec0c3e51c91df522cc5b026952a222
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205096"
---
# <span data-ttu-id="d94e8-103">Get-Counter</span><span class="sxs-lookup"><span data-stu-id="d94e8-103">Get-Counter</span></span>

## <span data-ttu-id="d94e8-104">概要</span><span class="sxs-lookup"><span data-stu-id="d94e8-104">SYNOPSIS</span></span>
<span data-ttu-id="d94e8-105">從本機電腦和遠端電腦取得效能計數器資料。</span><span class="sxs-lookup"><span data-stu-id="d94e8-105">Gets performance counter data from local and remote computers.</span></span>

## <span data-ttu-id="d94e8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d94e8-106">SYNTAX</span></span>

### <span data-ttu-id="d94e8-107">GetCounterSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="d94e8-107">GetCounterSet (Default)</span></span>

```
Get-Counter [[-Counter] <String[]>] [-SampleInterval <Int32>] [-MaxSamples <Int64>] [-Continuous]
 [-ComputerName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="d94e8-108">ListSetSet</span><span class="sxs-lookup"><span data-stu-id="d94e8-108">ListSetSet</span></span>

```
Get-Counter [-ListSet] <String[]> [-ComputerName <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="d94e8-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="d94e8-109">DESCRIPTION</span></span>

<span data-ttu-id="d94e8-110">指令程式會 `Get-Counter` 直接從 Windows 系列作業系統的效能監視檢測中取得效能計數器資料。</span><span class="sxs-lookup"><span data-stu-id="d94e8-110">The `Get-Counter` cmdlet gets performance counter data directly from the performance monitoring instrumentation in the Windows family of operating systems.</span></span> <span data-ttu-id="d94e8-111">`Get-Counter` 從本機電腦或遠端電腦取得效能資料。</span><span class="sxs-lookup"><span data-stu-id="d94e8-111">`Get-Counter` gets performance data from a local computer or remote computers.</span></span>

<span data-ttu-id="d94e8-112">您可以使用 `Get-Counter` 參數來指定一或多部電腦、列出效能計數器集合，以及它們所包含的實例、設定取樣間隔，以及指定最大樣本數。</span><span class="sxs-lookup"><span data-stu-id="d94e8-112">You can use the `Get-Counter` parameters to specify one or more computers, list the performance counter sets and the instances they contain, set the sample intervals, and specify the maximum number of samples.</span></span> <span data-ttu-id="d94e8-113">如果沒有參數，會 `Get-Counter` 取得一組系統計數器的效能計數器資料。</span><span class="sxs-lookup"><span data-stu-id="d94e8-113">Without parameters, `Get-Counter` gets performance counter data for a set of system counters.</span></span>

<span data-ttu-id="d94e8-114">許多計數器集合受 (ACL) 的存取控制清單保護。</span><span class="sxs-lookup"><span data-stu-id="d94e8-114">Many counter sets are protected by access control lists (ACL).</span></span> <span data-ttu-id="d94e8-115">若要查看所有計數器集合，請使用 [以 **系統管理員身分執行** ] 選項開啟 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d94e8-115">To see all counter sets, open PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="d94e8-116">PowerShell 7 中已重新引入此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d94e8-116">This cmdlet was reintroduced in PowerShell 7.</span></span>

## <span data-ttu-id="d94e8-117">範例</span><span class="sxs-lookup"><span data-stu-id="d94e8-117">EXAMPLES</span></span>

### <span data-ttu-id="d94e8-118">範例1：取得計數器集合清單</span><span class="sxs-lookup"><span data-stu-id="d94e8-118">Example 1: Get the counter set list</span></span>

<span data-ttu-id="d94e8-119">這個範例會取得本機電腦的計數器集合清單。</span><span class="sxs-lookup"><span data-stu-id="d94e8-119">This example gets the local computer's list of counter sets.</span></span>

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

<span data-ttu-id="d94e8-120">`Get-Counter` 使用 **ListSet** 參數搭配星號 (`*`) 來取得計數器集合的清單。</span><span class="sxs-lookup"><span data-stu-id="d94e8-120">`Get-Counter` uses the **ListSet** parameter with an asterisk (`*`) to get the list of counter sets.</span></span>
<span data-ttu-id="d94e8-121">`.` **MachineName** 資料行中)  (的點代表本機電腦。</span><span class="sxs-lookup"><span data-stu-id="d94e8-121">The dot (`.`) in the **MachineName** column represents the local computer.</span></span>

### <span data-ttu-id="d94e8-122">範例2：指定 SampleInterval 和 MaxSamples</span><span class="sxs-lookup"><span data-stu-id="d94e8-122">Example 2: Specify the SampleInterval and MaxSamples</span></span>

<span data-ttu-id="d94e8-123">此範例會取得本機電腦上所有處理器的計數器資料。</span><span class="sxs-lookup"><span data-stu-id="d94e8-123">This examples gets the counter data for all processors on the local computer.</span></span> <span data-ttu-id="d94e8-124">資料會以兩秒的間隔收集，直到有三個樣本為止。</span><span class="sxs-lookup"><span data-stu-id="d94e8-124">Data is collected at two-second intervals until there are three samples.</span></span>

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

<span data-ttu-id="d94e8-125">`Get-Counter` 使用 **counter** 參數來指定計數器路徑 `\Processor(_Total)\% Processor Time` 。</span><span class="sxs-lookup"><span data-stu-id="d94e8-125">`Get-Counter` uses the **Counter** parameter to specify the counter path `\Processor(_Total)\% Processor Time`.</span></span> <span data-ttu-id="d94e8-126">**SampleInterval** 參數會設定兩秒間隔以檢查計數器。</span><span class="sxs-lookup"><span data-stu-id="d94e8-126">The **SampleInterval** parameter sets a two-second interval to check the counter.</span></span> <span data-ttu-id="d94e8-127">**MaxSamples** 會判斷三個是檢查計數器的最大次數。</span><span class="sxs-lookup"><span data-stu-id="d94e8-127">**MaxSamples** determines that three is the maximum number of times to check the counter.</span></span>

### <span data-ttu-id="d94e8-128">範例3：取得計數器的連續範例</span><span class="sxs-lookup"><span data-stu-id="d94e8-128">Example 3: Get continuous samples of a counter</span></span>

<span data-ttu-id="d94e8-129">此範例會每秒取得計數器的連續範例。</span><span class="sxs-lookup"><span data-stu-id="d94e8-129">This examples gets continuous samples for a counter every second.</span></span> <span data-ttu-id="d94e8-130">若要停止命令，請按下<kbd>CTRL</kbd> + <kbd>C</kbd>。</span><span class="sxs-lookup"><span data-stu-id="d94e8-130">To stop the command, press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span> <span data-ttu-id="d94e8-131">若要指定樣本之間較長的間隔，請使用 **SampleInterval** 參數。</span><span class="sxs-lookup"><span data-stu-id="d94e8-131">To specify a longer interval between samples, use the **SampleInterval** parameter.</span></span>

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

<span data-ttu-id="d94e8-132">`Get-Counter` 使用 **counter** 參數來指定 `\Processor\% Processor Time` 計數器。</span><span class="sxs-lookup"><span data-stu-id="d94e8-132">`Get-Counter` uses the **Counter** parameter to specify the `\Processor\% Processor Time` counter.</span></span>
<span data-ttu-id="d94e8-133">**連續** 參數指定每秒取得範例，直到命令以 <kbd>CTRL</kbd> + <kbd>C</kbd>停止為止。</span><span class="sxs-lookup"><span data-stu-id="d94e8-133">The **Continuous** parameter specifies to get samples every second until the command is stopped with <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

### <span data-ttu-id="d94e8-134">範例4：依字母順序排列的計數器集合清單</span><span class="sxs-lookup"><span data-stu-id="d94e8-134">Example 4: Alphabetical list of counter sets</span></span>

<span data-ttu-id="d94e8-135">此範例會使用管線來取得計數器清單集，然後依字母順序排序清單。</span><span class="sxs-lookup"><span data-stu-id="d94e8-135">This example uses the pipeline to get the counter list set and then sort the list in alphabetical order.</span></span>

```powershell
Get-Counter -ListSet * |
  Sort-Object -Property CounterSetName |
    Format-Table CounterSetName, CounterSetType -AutoSize
```

```Output
CounterSetName                        CounterSetType
--------------                        --------------
.NET CLR Data                         SingleInstance
.NET Data Provider for SqlServer      SingleInstance
AppV Client Streamed Data Percentage  SingleInstance
Authorization Manager Applications    SingleInstance
BitLocker                             MultiInstance
Bluetooth Device                      SingleInstance
Cache                                 SingleInstance
Client Side Caching                   SingleInstance
```

<span data-ttu-id="d94e8-136">`Get-Counter` 使用 **ListSet** 參數搭配星號 (`*`) 來取得計數器集合的完整清單。</span><span class="sxs-lookup"><span data-stu-id="d94e8-136">`Get-Counter` uses the **ListSet** parameter with an asterisk (`*`) to get a complete list of counter sets.</span></span> <span data-ttu-id="d94e8-137">**CounterSet** 物件會沿著管線向下傳送。</span><span class="sxs-lookup"><span data-stu-id="d94e8-137">The **CounterSet** objects are sent down the pipeline.</span></span> <span data-ttu-id="d94e8-138">`Sort-Object` 使用 **Property** 參數來指定依 **CounterSetName** 排序物件。</span><span class="sxs-lookup"><span data-stu-id="d94e8-138">`Sort-Object` uses the **Property** parameter to specify that the objects are sorted by **CounterSetName** .</span></span> <span data-ttu-id="d94e8-139">物件會向下傳送到管線 `Format-Table` 。</span><span class="sxs-lookup"><span data-stu-id="d94e8-139">The objects are sent down the pipeline to `Format-Table`.</span></span> <span data-ttu-id="d94e8-140">**AutoSize** 參數會調整資料行寬度，以將截斷降至最低。</span><span class="sxs-lookup"><span data-stu-id="d94e8-140">The **AutoSize** parameter adjusts the column widths to minimize truncation.</span></span>

<span data-ttu-id="d94e8-141">`.` **MachineName** 資料行中)  (的點代表本機電腦。</span><span class="sxs-lookup"><span data-stu-id="d94e8-141">The dot (`.`) in the **MachineName** column represents the local computer.</span></span>

### <span data-ttu-id="d94e8-142">範例5：執行背景工作以取得計數器資料</span><span class="sxs-lookup"><span data-stu-id="d94e8-142">Example 5: Run a background job to get counter data</span></span>

<span data-ttu-id="d94e8-143">在此範例中，會在 `Start-Job` `Get-Counter` 本機電腦上以背景工作方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="d94e8-143">In this example, `Start-Job` runs a `Get-Counter` command as a background job on the local computer.</span></span>
<span data-ttu-id="d94e8-144">若要查看作業的效能計數器輸出，請使用 `Receive-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d94e8-144">To view the performance counter output from the job, use the `Receive-Job` cmdlet.</span></span>

```powershell
Start-Job -ScriptBlock {Get-Counter -Counter "\LogicalDisk(_Total)\% Free Space" -MaxSamples 1000}
```

```Output
Id     Name  PSJobTypeName   State    HasMoreData  Location   Command
--     ----  -------------   -----    -----------  --------   -------
1      Job1  BackgroundJob   Running  True         localhost  Get-Counter -Counter
```

<span data-ttu-id="d94e8-145">`Start-Job` 使用 **ScriptBlock** 參數來執行 `Get-Counter` 命令。</span><span class="sxs-lookup"><span data-stu-id="d94e8-145">`Start-Job` uses the **ScriptBlock** parameter to run a `Get-Counter` command.</span></span> <span data-ttu-id="d94e8-146">`Get-Counter` 使用 **counter** 參數來指定計數器路徑 `\LogicalDisk(_Total)\% Free Space` 。</span><span class="sxs-lookup"><span data-stu-id="d94e8-146">`Get-Counter` uses the **Counter** parameter to specify the counter path `\LogicalDisk(_Total)\% Free Space`.</span></span> <span data-ttu-id="d94e8-147">**MaxSamples** 參數會指定取得計數器的1000樣本。</span><span class="sxs-lookup"><span data-stu-id="d94e8-147">The **MaxSamples** parameter specifies to get 1000 samples of the counter.</span></span>

### <span data-ttu-id="d94e8-148">範例6：從多部電腦取得計數器資料</span><span class="sxs-lookup"><span data-stu-id="d94e8-148">Example 6: Get counter data from multiple computers</span></span>

<span data-ttu-id="d94e8-149">此範例會使用變數，從兩部電腦取得效能計數器資料。</span><span class="sxs-lookup"><span data-stu-id="d94e8-149">This example uses a variable to get performance counter data from two computers.</span></span>

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

<span data-ttu-id="d94e8-150">`$DiskReads`變數會儲存 `\LogicalDisk(C:)\Disk Reads/sec` 計數器路徑。</span><span class="sxs-lookup"><span data-stu-id="d94e8-150">The `$DiskReads` variable stores the `\LogicalDisk(C:)\Disk Reads/sec` counter path.</span></span> <span data-ttu-id="d94e8-151">`$DiskReads`變數會沿著管線向下傳送至 `Get-Counter` 。</span><span class="sxs-lookup"><span data-stu-id="d94e8-151">The `$DiskReads` variable is sent down the pipeline to `Get-Counter`.</span></span> <span data-ttu-id="d94e8-152">**計數器** 是第一個位置參數，並接受中儲存的路徑 `$DiskReads` 。</span><span class="sxs-lookup"><span data-stu-id="d94e8-152">**Counter** is the first position parameter and accepts the path stored in `$DiskReads`.</span></span> <span data-ttu-id="d94e8-153">**ComputerName** 指定兩部電腦和 **MaxSamples** 指定要從每部電腦取得10個樣本。</span><span class="sxs-lookup"><span data-stu-id="d94e8-153">**ComputerName** specifies the two computers and **MaxSamples** specifies to get 10 samples from each computer.</span></span>

### <span data-ttu-id="d94e8-154">範例7：從多部隨機電腦取得計數器的實例值</span><span class="sxs-lookup"><span data-stu-id="d94e8-154">Example 7: Get a counter's instance values from multiple random computers</span></span>

<span data-ttu-id="d94e8-155">此範例會取得企業中50隨機遠端電腦的效能計數器值。</span><span class="sxs-lookup"><span data-stu-id="d94e8-155">This example gets the value of a performance counter on 50 random, remote computers in the enterprise.</span></span> <span data-ttu-id="d94e8-156">**ComputerName** 參數會使用儲存在變數中的隨機電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="d94e8-156">The **ComputerName** parameter uses random computer names stored in a variable.</span></span> <span data-ttu-id="d94e8-157">若要更新變數中的電腦名稱稱，請重新建立變數。</span><span class="sxs-lookup"><span data-stu-id="d94e8-157">To update the computer names in the variable, recreate the variable.</span></span>

<span data-ttu-id="d94e8-158">**ComputerName** 參數中伺服器名稱的替代方案是使用文字檔。</span><span class="sxs-lookup"><span data-stu-id="d94e8-158">An alternative for the server names in the **ComputerName** parameter is to use a text file.</span></span> <span data-ttu-id="d94e8-159">例如：</span><span class="sxs-lookup"><span data-stu-id="d94e8-159">For example:</span></span>

`-ComputerName (Get-Random (Get-Content -Path C:\Servers.txt) -Count 50)`

<span data-ttu-id="d94e8-160">計數器路徑在 `*` 實例名稱中包含星號 () ，以取得每個遠端電腦處理器的資料。</span><span class="sxs-lookup"><span data-stu-id="d94e8-160">The counter path includes an asterisk (`*`) in the instance name to get the data for each of the remote computer's processors.</span></span>

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

<span data-ttu-id="d94e8-161">此 `Get-Random` Cmdlet 會使用 `Get-Content` 從檔案選取50隨機電腦名稱稱 `Servers.txt` 。</span><span class="sxs-lookup"><span data-stu-id="d94e8-161">The `Get-Random` cmdlet uses `Get-Content` to select 50 random computer names from the `Servers.txt` file.</span></span> <span data-ttu-id="d94e8-162">遠端電腦名稱稱會儲存在變數中 `$Servers` 。</span><span class="sxs-lookup"><span data-stu-id="d94e8-162">The remote computer names are stored in the `$Servers` variable.</span></span> <span data-ttu-id="d94e8-163">`\Processor(*)\% Processor Time`計數器的路徑會儲存在變數中 `$Counter` 。</span><span class="sxs-lookup"><span data-stu-id="d94e8-163">The `\Processor(*)\% Processor Time` counter's path is stored in the `$Counter` variable.</span></span> <span data-ttu-id="d94e8-164">`Get-Counter` 使用 **Counter** 參數來指定變數中的計數器 `$Counter` 。</span><span class="sxs-lookup"><span data-stu-id="d94e8-164">`Get-Counter` uses the **Counter** parameter to specify the counters in the `$Counter` variable.</span></span> <span data-ttu-id="d94e8-165">**ComputerName** 參數會指定變數中的電腦名稱稱 `$Servers` 。</span><span class="sxs-lookup"><span data-stu-id="d94e8-165">The **ComputerName** parameter specifies the computer names in the `$Servers` variable.</span></span>

### <span data-ttu-id="d94e8-166">範例8：使用 Path 屬性來取得格式化的路徑名稱</span><span class="sxs-lookup"><span data-stu-id="d94e8-166">Example 8: Use the Path property to get formatted path names</span></span>

<span data-ttu-id="d94e8-167">此範例會使用計數器集合的 **path** 屬性來尋找效能計數器的格式化路徑名稱。</span><span class="sxs-lookup"><span data-stu-id="d94e8-167">This example uses the **Path** property of a counter set to find the formatted path names for the performance counters.</span></span>

<span data-ttu-id="d94e8-168">管線會與 Cmdlet 搭配使用 `Where-Object` ，以尋找路徑名稱的子集。</span><span class="sxs-lookup"><span data-stu-id="d94e8-168">The pipeline is used with the `Where-Object` cmdlet to find a subset of the path names.</span></span> <span data-ttu-id="d94e8-169">若要尋找計數器集合計數器路徑的完整清單，請 (`|`) 和命令移除管線 `Where-Object` 。</span><span class="sxs-lookup"><span data-stu-id="d94e8-169">To find a counter sets complete list of counter paths, remove the pipeline (`|`) and `Where-Object` command.</span></span>

<span data-ttu-id="d94e8-170">`$_`是管線中目前物件的自動變數。</span><span class="sxs-lookup"><span data-stu-id="d94e8-170">The `$_` is an automatic variable for the current object in the pipeline.</span></span>
<span data-ttu-id="d94e8-171">如需詳細資訊，請參閱 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="d94e8-171">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

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

<span data-ttu-id="d94e8-172">`Get-Counter` 使用 **ListSet** 參數來指定 **記憶體** 計數器集合。</span><span class="sxs-lookup"><span data-stu-id="d94e8-172">`Get-Counter` uses the **ListSet** parameter to specify the **Memory** counter set.</span></span> <span data-ttu-id="d94e8-173">此命令會以括弧括住，讓 [ **路徑** ] 屬性以字串形式傳回每個路徑。</span><span class="sxs-lookup"><span data-stu-id="d94e8-173">The command is enclosed in parentheses so that the **Paths** property returns each path as a string.</span></span> <span data-ttu-id="d94e8-174">物件會向下傳送到管線 `Where-Object` 。</span><span class="sxs-lookup"><span data-stu-id="d94e8-174">The objects are sent down the pipeline to `Where-Object`.</span></span> <span data-ttu-id="d94e8-175">`Where-Object` 使用變數 `$_` 來處理每個物件，並使用 `-like` 運算子來尋找字串的相符專案 `*Cache*` 。</span><span class="sxs-lookup"><span data-stu-id="d94e8-175">`Where-Object` uses the variable `$_` to process each object and uses the `-like` operator to find matches for the string `*Cache*`.</span></span> <span data-ttu-id="d94e8-176">星號 (`*`) 是任何字元的萬用字元。</span><span class="sxs-lookup"><span data-stu-id="d94e8-176">The asterisks (`*`) are wildcards for any characters.</span></span>

### <span data-ttu-id="d94e8-177">範例9：使用 PathsWithInstances 屬性來取得格式化的路徑名稱</span><span class="sxs-lookup"><span data-stu-id="d94e8-177">Example 9: Use the PathsWithInstances property to get formatted path names</span></span>

<span data-ttu-id="d94e8-178">這個範例會取得格式化的路徑名稱，其中包含 **PhysicalDisk** 效能計數器的實例。</span><span class="sxs-lookup"><span data-stu-id="d94e8-178">This example gets the formatted path names that include the instances for the **PhysicalDisk** performance counters.</span></span>

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

<span data-ttu-id="d94e8-179">`Get-Counter` 使用 **ListSet** 參數來指定 **PhysicalDisk** 計數器集合。</span><span class="sxs-lookup"><span data-stu-id="d94e8-179">`Get-Counter` uses the **ListSet** parameter to specify the **PhysicalDisk** counter set.</span></span> <span data-ttu-id="d94e8-180">此命令會以括弧括住，讓 **PathsWithInstances** 屬性以字串形式傳回每個路徑實例。</span><span class="sxs-lookup"><span data-stu-id="d94e8-180">The command is enclosed in parentheses so that the **PathsWithInstances** property returns each path instance as a string.</span></span>

### <span data-ttu-id="d94e8-181">範例10：為計數器集合中的每個計數器取得單一值</span><span class="sxs-lookup"><span data-stu-id="d94e8-181">Example 10: Get a single value for each counter in a counter set</span></span>

<span data-ttu-id="d94e8-182">在此範例中，會針對本機電腦的 **Memory** 計數器集合中的每個效能計數器傳回單一值。</span><span class="sxs-lookup"><span data-stu-id="d94e8-182">In this example, a single value is returned for each performance counter in the local computer's **Memory** counter set.</span></span>

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

<span data-ttu-id="d94e8-183">`Get-Counter` 使用 **ListSet** 參數來指定 **記憶體** 計數器集合。</span><span class="sxs-lookup"><span data-stu-id="d94e8-183">`Get-Counter` uses the **ListSet** parameter to specify the **Memory** counter set.</span></span> <span data-ttu-id="d94e8-184">此命令會以括弧括住，讓 [ **路徑** ] 屬性以字串形式傳回每個路徑。</span><span class="sxs-lookup"><span data-stu-id="d94e8-184">The command is enclosed in parentheses so that the **Paths** property returns each path as a string.</span></span> <span data-ttu-id="d94e8-185">路徑會儲存在變數中 `$MemCounters` 。</span><span class="sxs-lookup"><span data-stu-id="d94e8-185">The paths are stored in the `$MemCounters` variable.</span></span> <span data-ttu-id="d94e8-186">`Get-Counter` 使用 **counter** 參數來指定變數中的計數器路徑 `$MemCounters` 。</span><span class="sxs-lookup"><span data-stu-id="d94e8-186">`Get-Counter` uses the **Counter** parameter to specify the counter paths in the `$MemCounters` variable.</span></span>

### <span data-ttu-id="d94e8-187">範例11：顯示物件的屬性值</span><span class="sxs-lookup"><span data-stu-id="d94e8-187">Example 11: Display an object's property values</span></span>

<span data-ttu-id="d94e8-188">**PerformanceCounterSample** 物件中的屬性值代表每個資料範例。</span><span class="sxs-lookup"><span data-stu-id="d94e8-188">The property values in the **PerformanceCounterSample** object represent each data sample.</span></span> <span data-ttu-id="d94e8-189">在此範例中，我們使用 **CounterSamples** 物件的屬性來檢查、選取、排序及分組資料。</span><span class="sxs-lookup"><span data-stu-id="d94e8-189">In this example we use the properties of the **CounterSamples** object to examine, select, sort, and group the data.</span></span>

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

<span data-ttu-id="d94e8-190">計數器路徑儲存在 `$Counter` 變數中。</span><span class="sxs-lookup"><span data-stu-id="d94e8-190">The counter path is stored in the `$Counter` variable.</span></span> <span data-ttu-id="d94e8-191">`Get-Counter` 取得計數器值的一個樣本，並將結果儲存在 `$Data` 變數中。</span><span class="sxs-lookup"><span data-stu-id="d94e8-191">`Get-Counter` gets one sample of the counter values and stores the results in the `$Data` variable.</span></span> <span data-ttu-id="d94e8-192">`$Data`變數使用 **CounterSamples** 屬性來取得物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="d94e8-192">The `$Data` variable uses the **CounterSamples** property to get the object's properties.</span></span> <span data-ttu-id="d94e8-193">物件會向下傳送到管線 `Format-List` 。</span><span class="sxs-lookup"><span data-stu-id="d94e8-193">The object is sent down the pipeline to `Format-List`.</span></span> <span data-ttu-id="d94e8-194">**Property** 參數使用星號 (`*`) 萬用字元來選取所有屬性。</span><span class="sxs-lookup"><span data-stu-id="d94e8-194">The **Property** parameter uses an asterisk (`*`) wildcard to select all the properties.</span></span>

### <span data-ttu-id="d94e8-195">範例12：效能計數器陣列值</span><span class="sxs-lookup"><span data-stu-id="d94e8-195">Example 12: Performance counter array values</span></span>

<span data-ttu-id="d94e8-196">在此範例中，變數會儲存每個效能計數器。</span><span class="sxs-lookup"><span data-stu-id="d94e8-196">In this example, a variable stores each performance counter.</span></span> <span data-ttu-id="d94e8-197">**CounterSamples** 屬性是可以顯示特定計數器值的陣列。</span><span class="sxs-lookup"><span data-stu-id="d94e8-197">The **CounterSamples** property is an array that can display specific counter values.</span></span>

<span data-ttu-id="d94e8-198">若要顯示每個計數器範例，請使用 `$Counter.CounterSamples` 。</span><span class="sxs-lookup"><span data-stu-id="d94e8-198">To display each counter sample, use `$Counter.CounterSamples`.</span></span>

```powershell
$Counter = Get-Counter -Counter "\Processor(*)\% Processor Time"
$Counter.CounterSamples[0]
```

```Output
Path                                         InstanceName        CookedValue
----                                         ------------        -----------
\\Computer01\processor(0)\% processor time   0              1.33997091699662
```

<span data-ttu-id="d94e8-199">`Get-Counter` 使用 **counter** 參數來指定計數器 `\Processor(*)\% Processor Time` 。</span><span class="sxs-lookup"><span data-stu-id="d94e8-199">`Get-Counter` uses the **Counter** parameter to specify the counter `\Processor(*)\% Processor Time`.</span></span> <span data-ttu-id="d94e8-200">這些值會儲存在 `$Counter` 變數中。</span><span class="sxs-lookup"><span data-stu-id="d94e8-200">The values are stored in the `$Counter` variable.</span></span>
<span data-ttu-id="d94e8-201">`$Counter.CounterSamples[0]` 顯示第一個計數器值的陣列值。</span><span class="sxs-lookup"><span data-stu-id="d94e8-201">`$Counter.CounterSamples[0]` displays the array value for the first counter value.</span></span>

### <span data-ttu-id="d94e8-202">範例13：比較效能計數器值</span><span class="sxs-lookup"><span data-stu-id="d94e8-202">Example 13: Compare performance counter values</span></span>

<span data-ttu-id="d94e8-203">此範例會尋找本機電腦上每個處理器所使用的處理器時間量。</span><span class="sxs-lookup"><span data-stu-id="d94e8-203">This example finds the amount of processor time used by each processor on the local computer.</span></span> <span data-ttu-id="d94e8-204">**CounterSamples** 屬性是用來比較計數器資料與指定的值。</span><span class="sxs-lookup"><span data-stu-id="d94e8-204">The **CounterSamples** property is used to compare the counter data against a specified value.</span></span>

<span data-ttu-id="d94e8-205">若要顯示每個計數器範例，請使用 `$Counter.CounterSamples` 。</span><span class="sxs-lookup"><span data-stu-id="d94e8-205">To display each counter sample, use `$Counter.CounterSamples`.</span></span>

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

<span data-ttu-id="d94e8-206">`Get-Counter` 使用 **counter** 參數來指定計數器 `\Processor(*)\% Processor Time` 。</span><span class="sxs-lookup"><span data-stu-id="d94e8-206">`Get-Counter` uses the **Counter** parameter to specify the counter `\Processor(*)\% Processor Time`.</span></span> <span data-ttu-id="d94e8-207">這些值會儲存在 `$Counter` 變數中。</span><span class="sxs-lookup"><span data-stu-id="d94e8-207">The values are stored in the `$Counter` variable.</span></span> <span data-ttu-id="d94e8-208">中儲存的物件 `$Counter.CounterSamples` 會向下傳送到管線。</span><span class="sxs-lookup"><span data-stu-id="d94e8-208">The objects stored in `$Counter.CounterSamples` are sent down the pipeline.</span></span> <span data-ttu-id="d94e8-209">`Where-Object` 使用腳本區塊，將每個物件的值與指定的20值進行比較。</span><span class="sxs-lookup"><span data-stu-id="d94e8-209">`Where-Object` uses a script block to compare each objects value against a specified value of 20.</span></span> <span data-ttu-id="d94e8-210">`$_.CookedValue`是管線中目前物件的變數。</span><span class="sxs-lookup"><span data-stu-id="d94e8-210">The `$_.CookedValue` is a variable for the current object in the pipeline.</span></span> <span data-ttu-id="d94e8-211">**CookedValue** 小於20的計數器隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="d94e8-211">Counters with a **CookedValue** that is less than 20 are displayed.</span></span>

### <span data-ttu-id="d94e8-212">範例14：排序效能計數器資料</span><span class="sxs-lookup"><span data-stu-id="d94e8-212">Example 14: Sort performance counter data</span></span>

<span data-ttu-id="d94e8-213">此範例顯示如何排序效能計數器資料。</span><span class="sxs-lookup"><span data-stu-id="d94e8-213">This example shows how to sort performance counter data.</span></span> <span data-ttu-id="d94e8-214">此範例會尋找電腦上，在取樣期間使用最多處理器時間的處理常式。</span><span class="sxs-lookup"><span data-stu-id="d94e8-214">The example finds the processes on the computer that are using the most processor time during the sample.</span></span>

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

<span data-ttu-id="d94e8-215">`Get-Counter` 使用 **counter** 參數來指定 `\Process(*)\% Processor Time` 本機電腦上所有處理常式的計數器。</span><span class="sxs-lookup"><span data-stu-id="d94e8-215">`Get-Counter` uses the **Counter** parameter to specify the `\Process(*)\% Processor Time` counter for all the processes on the local computer.</span></span> <span data-ttu-id="d94e8-216">結果會儲存在變數中 `$Procs` 。</span><span class="sxs-lookup"><span data-stu-id="d94e8-216">The result is stored in the `$Procs` variable.</span></span> <span data-ttu-id="d94e8-217">`$Procs`具有 **CounterSamples** 屬性的變數會將 **PerformanceCounterSample** 物件沿著管線向下傳送。</span><span class="sxs-lookup"><span data-stu-id="d94e8-217">The `$Procs` variable with the **CounterSamples** property sends the **PerformanceCounterSample** objects down the pipeline.</span></span> <span data-ttu-id="d94e8-218">`Sort-Object` 使用 **Property** 參數，依 **CookedValue** 以 **遞減** 順序排序物件。</span><span class="sxs-lookup"><span data-stu-id="d94e8-218">`Sort-Object` uses the **Property** parameter to sort the objects by **CookedValue** in **Descending** order.</span></span> <span data-ttu-id="d94e8-219">`Format-Table` 使用 **Property** 參數來選取輸出的資料行。</span><span class="sxs-lookup"><span data-stu-id="d94e8-219">`Format-Table` uses the **Property** parameter to select the columns for the output.</span></span> <span data-ttu-id="d94e8-220">**AutoSize** 參數會調整資料行寬度，以將截斷降至最低。</span><span class="sxs-lookup"><span data-stu-id="d94e8-220">The **AutoSize** parameter adjusts the column widths to minimize truncation.</span></span>

## <span data-ttu-id="d94e8-221">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d94e8-221">PARAMETERS</span></span>

### <span data-ttu-id="d94e8-222">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="d94e8-222">-ComputerName</span></span>

<span data-ttu-id="d94e8-223">指定一或多個電腦名稱稱，或一組以逗號分隔的 **遠端** 電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="d94e8-223">Specifies one computer name or a comma-separated array of **remote** computer names.</span></span> <span data-ttu-id="d94e8-224">使用 NetBIOS 名稱、IP 位址或電腦的完整功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="d94e8-224">Use the NetBIOS name, an IP address, or the computer's fully qualified domain name.</span></span>

<span data-ttu-id="d94e8-225">若要從 **本機** 電腦取得效能計數器資料，請排除 **ComputerName** 參數。</span><span class="sxs-lookup"><span data-stu-id="d94e8-225">To get performance counter data from the **local** computer, exclude the **ComputerName** parameter.</span></span>
<span data-ttu-id="d94e8-226">針對包含 **MachineName** 資料行之 **ListSet** 的輸出， `.`) 表示本機電腦的點 (。</span><span class="sxs-lookup"><span data-stu-id="d94e8-226">For output such as a **ListSet** that contains the **MachineName** column, a dot (`.`) indicates the local computer.</span></span>

<span data-ttu-id="d94e8-227">`Get-Counter` 不依賴 PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="d94e8-227">`Get-Counter` doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="d94e8-228">即使您的電腦未設定為執行遠端命令，您也可以使用 **ComputerName** 參數。</span><span class="sxs-lookup"><span data-stu-id="d94e8-228">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

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

### <span data-ttu-id="d94e8-229">-Continuous</span><span class="sxs-lookup"><span data-stu-id="d94e8-229">-Continuous</span></span>

<span data-ttu-id="d94e8-230">指定 **連續** 時，會 `Get-Counter` 取得範例，直到您按下 <kbd>CTRL</kbd> + <kbd>C</kbd>。</span><span class="sxs-lookup"><span data-stu-id="d94e8-230">When the **Continuous** is specified, `Get-Counter` gets samples until you press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span> <span data-ttu-id="d94e8-231">每秒都會針對每個指定的效能計數器取得範例。</span><span class="sxs-lookup"><span data-stu-id="d94e8-231">Samples are obtained every second for each specified performance counter.</span></span> <span data-ttu-id="d94e8-232">使用 **SampleInterval** 參數可增加連續範例之間的間隔。</span><span class="sxs-lookup"><span data-stu-id="d94e8-232">Use the **SampleInterval** parameter to increase the interval between continuous samples.</span></span>

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

### <span data-ttu-id="d94e8-233">-Counter</span><span class="sxs-lookup"><span data-stu-id="d94e8-233">-Counter</span></span>

<span data-ttu-id="d94e8-234">指定一或多個計數器路徑的路徑。</span><span class="sxs-lookup"><span data-stu-id="d94e8-234">Specifies the path to one or more counter paths.</span></span> <span data-ttu-id="d94e8-235">路徑會輸入為以逗號分隔的陣列、變數或文字檔中的值。</span><span class="sxs-lookup"><span data-stu-id="d94e8-235">Paths are input as a comma-separated array, a variable, or values from a text file.</span></span> <span data-ttu-id="d94e8-236">您可以向下傳送管線的計數器路徑字串至 `Get-Counter` 。</span><span class="sxs-lookup"><span data-stu-id="d94e8-236">You can send counter path strings down the pipeline to `Get-Counter`.</span></span>

<span data-ttu-id="d94e8-237">計數器路徑使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="d94e8-237">Counter paths use the following syntax:</span></span>

`\\ComputerName\CounterSet(Instance)\CounterName`

`\CounterSet(Instance)\CounterName`

<span data-ttu-id="d94e8-238">例如：</span><span class="sxs-lookup"><span data-stu-id="d94e8-238">For example:</span></span>

`\\Server01\Processor(*)\% User Time`

`\Processor(*)\% User Time`

<span data-ttu-id="d94e8-239">在 `\\ComputerName` 效能計數器路徑中是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="d94e8-239">The `\\ComputerName` is optional in a performance counter path.</span></span> <span data-ttu-id="d94e8-240">如果計數器路徑未包含電腦名稱稱，則會 `Get-Counter` 使用本機電腦。</span><span class="sxs-lookup"><span data-stu-id="d94e8-240">If the counter path doesn't include the computer name, `Get-Counter` uses the local computer.</span></span>

<span data-ttu-id="d94e8-241">實例中的星號 (`*`) 是取得計數器所有實例的萬用字元。</span><span class="sxs-lookup"><span data-stu-id="d94e8-241">An asterisk (`*`) in the instance is a wildcard character to get all instances of the counter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="d94e8-242">-ListSet</span><span class="sxs-lookup"><span data-stu-id="d94e8-242">-ListSet</span></span>

<span data-ttu-id="d94e8-243">列出電腦上的效能計數器集合。</span><span class="sxs-lookup"><span data-stu-id="d94e8-243">Lists the performance counter sets on the computers.</span></span> <span data-ttu-id="d94e8-244">使用星號 (`*`) 來指定所有計數器集合。</span><span class="sxs-lookup"><span data-stu-id="d94e8-244">Use an asterisk (`*`) to specify all counter sets.</span></span> <span data-ttu-id="d94e8-245">輸入一個名稱或以逗號分隔的計數器集合名稱字串。</span><span class="sxs-lookup"><span data-stu-id="d94e8-245">Enter one name or a comma-separated string of counter set names.</span></span> <span data-ttu-id="d94e8-246">您可以將計數器集合名稱向下傳送到管線。</span><span class="sxs-lookup"><span data-stu-id="d94e8-246">You can send counter set names down the pipeline.</span></span>

<span data-ttu-id="d94e8-247">若要取得計數器集合格式化的計數器路徑，請使用 **ListSet** 參數。</span><span class="sxs-lookup"><span data-stu-id="d94e8-247">To get a counter sets formatted counter paths, use the **ListSet** parameter.</span></span> <span data-ttu-id="d94e8-248">每個計數器集合的 **路徑** 和 **PathsWithInstances** 屬性包含格式為字串的個別計數器路徑。</span><span class="sxs-lookup"><span data-stu-id="d94e8-248">The **Paths** and **PathsWithInstances** properties of each counter set contain the individual counter paths formatted as a string.</span></span>

<span data-ttu-id="d94e8-249">您可以將計數器路徑字串儲存在變數中，或使用管線將字串傳送至另一個 `Get-Counter` 命令。</span><span class="sxs-lookup"><span data-stu-id="d94e8-249">You can save the counter path strings in a variable or use the pipeline to send the string to another `Get-Counter` command.</span></span>

<span data-ttu-id="d94e8-250">例如，將每個 **處理器** 計數器路徑傳送至 `Get-Counter` ：</span><span class="sxs-lookup"><span data-stu-id="d94e8-250">For example to send each **Processor** counter path to `Get-Counter`:</span></span>

`Get-Counter -ListSet Processor | Get-Counter`

> [!NOTE]
> <span data-ttu-id="d94e8-251">在 PowerShell 7 中， `Get-Counter` 無法取出計數器集合的 **Description** 屬性。</span><span class="sxs-lookup"><span data-stu-id="d94e8-251">In PowerShell 7, `Get-Counter` can't retrieve the **Description** property of the counter set.</span></span> <span data-ttu-id="d94e8-252">**描述** 設定為 `$null` 。</span><span class="sxs-lookup"><span data-stu-id="d94e8-252">The **Description** is set to `$null`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ListSetSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="d94e8-253">-MaxSamples</span><span class="sxs-lookup"><span data-stu-id="d94e8-253">-MaxSamples</span></span>

<span data-ttu-id="d94e8-254">指定要從每個指定效能計數器取得的樣本數目。</span><span class="sxs-lookup"><span data-stu-id="d94e8-254">Specifies the number of samples to get from each specified performance counter.</span></span> <span data-ttu-id="d94e8-255">若要取得範例的常數資料流程，請使用 **連續** 參數。</span><span class="sxs-lookup"><span data-stu-id="d94e8-255">To get a constant stream of samples, use the **Continuous** parameter.</span></span>

<span data-ttu-id="d94e8-256">如果未指定 **MaxSamples** 參數，則 `Get-Counter` 只會針對每個指定的計數器取得一個樣本。</span><span class="sxs-lookup"><span data-stu-id="d94e8-256">If the **MaxSamples** parameter isn't specified, `Get-Counter` only gets one sample for each specified counter.</span></span>

<span data-ttu-id="d94e8-257">若要收集大型資料集，請以 `Get-Counter` PowerShell 背景工作的形式執行。</span><span class="sxs-lookup"><span data-stu-id="d94e8-257">To collect a large data set, run `Get-Counter` as a PowerShell background job.</span></span> <span data-ttu-id="d94e8-258">如需詳細資訊，請參閱 [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="d94e8-258">For more information, see [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md).</span></span>

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

### <span data-ttu-id="d94e8-259">-SampleInterval</span><span class="sxs-lookup"><span data-stu-id="d94e8-259">-SampleInterval</span></span>

<span data-ttu-id="d94e8-260">指定每個指定效能計數器樣本之間的秒數。</span><span class="sxs-lookup"><span data-stu-id="d94e8-260">Specifies the number of seconds between samples for each specified performance counter.</span></span> <span data-ttu-id="d94e8-261">如果未指定 **SampleInterval** 參數，則會 `Get-Counter` 使用一秒的間隔。</span><span class="sxs-lookup"><span data-stu-id="d94e8-261">If the **SampleInterval** parameter isn't specified, `Get-Counter` uses a one-second interval.</span></span>

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

### <span data-ttu-id="d94e8-262">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d94e8-262">CommonParameters</span></span>

<span data-ttu-id="d94e8-263">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="d94e8-263">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d94e8-264">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="d94e8-264">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d94e8-265">輸入</span><span class="sxs-lookup"><span data-stu-id="d94e8-265">INPUTS</span></span>

### <span data-ttu-id="d94e8-266">System.String[]</span><span class="sxs-lookup"><span data-stu-id="d94e8-266">System.String[]</span></span>

<span data-ttu-id="d94e8-267">`Get-Counter` 接受計數器路徑和計數器集合名稱的管線輸入。</span><span class="sxs-lookup"><span data-stu-id="d94e8-267">`Get-Counter` accepts pipeline input for counter paths and counter set names.</span></span>

## <span data-ttu-id="d94e8-268">輸出</span><span class="sxs-lookup"><span data-stu-id="d94e8-268">OUTPUTS</span></span>

### <span data-ttu-id="d94e8-269">會傳回 microsoft.powershell.commands.getcounter.counterset，會傳回 microsoft.powershell.commands.getcounter.counterset. PerformanceCounterSampleSet，.，，會傳回 microsoft.powershell.commands.getcounter.counterset. PerformanceCounterSample <。</span><span class="sxs-lookup"><span data-stu-id="d94e8-269">Microsoft.PowerShell.Commands.GetCounter.CounterSet, Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet, Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSample</span></span>

<span data-ttu-id="d94e8-270">若要查看物件的屬性，請向下傳送管線的輸出 `Get-Member` 。</span><span class="sxs-lookup"><span data-stu-id="d94e8-270">To view an object's properties, send the output down the pipeline to `Get-Member`.</span></span> <span data-ttu-id="d94e8-271">輸出的物件類型如下所示：</span><span class="sxs-lookup"><span data-stu-id="d94e8-271">The object types that are output are as follows:</span></span>

<span data-ttu-id="d94e8-272">**ListSet** 參數： **會傳回 microsoft.powershell.commands.getcounter.counterset 的命令**</span><span class="sxs-lookup"><span data-stu-id="d94e8-272">**ListSet** parameter: **Microsoft.PowerShell.Commands.GetCounter.CounterSet**</span></span>

<span data-ttu-id="d94e8-273">**Counter** 參數： **會傳回 microsoft.powershell.commands.getcounter.counterset. PerformanceCounterSampleSet**</span><span class="sxs-lookup"><span data-stu-id="d94e8-273">**Counter** parameter: **Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet**</span></span>

<span data-ttu-id="d94e8-274">**CounterSamples** 屬性： **會傳回 microsoft.powershell.commands.getcounter.counterset. PerformanceCounterSample**</span><span class="sxs-lookup"><span data-stu-id="d94e8-274">**CounterSamples** property: **Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSample**</span></span>

## <span data-ttu-id="d94e8-275">注意</span><span class="sxs-lookup"><span data-stu-id="d94e8-275">NOTES</span></span>

<span data-ttu-id="d94e8-276">如果未指定任何參數，則會 `Get-Counter` 為每個指定的效能計數器取得一個樣本。</span><span class="sxs-lookup"><span data-stu-id="d94e8-276">If no parameters are specified, `Get-Counter` gets one sample for each specified performance counter.</span></span> <span data-ttu-id="d94e8-277">使用 **MaxSamples** 和 **連續** 參數來取得更多範例。</span><span class="sxs-lookup"><span data-stu-id="d94e8-277">Use the **MaxSamples** and **Continuous** parameters to get more samples.</span></span>

<span data-ttu-id="d94e8-278">`Get-Counter` 使用樣本之間的一秒間隔。</span><span class="sxs-lookup"><span data-stu-id="d94e8-278">`Get-Counter` uses a one-second interval between samples.</span></span> <span data-ttu-id="d94e8-279">使用 **SampleInterval** 參數來增加間隔。</span><span class="sxs-lookup"><span data-stu-id="d94e8-279">Use the **SampleInterval** parameter to increase the interval.</span></span>

<span data-ttu-id="d94e8-280">**MaxSamples** 和 **SampleInterval** 值適用于命令中每部電腦上的所有計數器。</span><span class="sxs-lookup"><span data-stu-id="d94e8-280">The **MaxSamples** and **SampleInterval** values apply to all the counters on each computer in the command.</span></span> <span data-ttu-id="d94e8-281">若要為不同的計數器設定不同的值，請輸入不同的 `Get-Counter` 命令。</span><span class="sxs-lookup"><span data-stu-id="d94e8-281">To set different values for different counters, enter separate `Get-Counter` commands.</span></span>

<span data-ttu-id="d94e8-282">在 PowerShell 7 中，使用 **ListSet** 參數時， `Get-Counter` 無法取出計數器集合的 **Description** 屬性。</span><span class="sxs-lookup"><span data-stu-id="d94e8-282">In PowerShell 7, when using the **ListSet** parameter, `Get-Counter` can't retrieve the **Description** property of the counter set.</span></span> <span data-ttu-id="d94e8-283">**描述** 設定為 `$null` 。</span><span class="sxs-lookup"><span data-stu-id="d94e8-283">The **Description** is set to `$null`.</span></span>

## <span data-ttu-id="d94e8-284">相關連結</span><span class="sxs-lookup"><span data-stu-id="d94e8-284">RELATED LINKS</span></span>

[<span data-ttu-id="d94e8-285">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="d94e8-285">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="d94e8-286">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="d94e8-286">about_Jobs</span></span>](../Microsoft.PowerShell.Core/About/about_Jobs.md)

[<span data-ttu-id="d94e8-287">Format-List</span><span class="sxs-lookup"><span data-stu-id="d94e8-287">Format-List</span></span>](../Microsoft.PowerShell.Utility/Format-List.md)

[<span data-ttu-id="d94e8-288">Format-Table</span><span class="sxs-lookup"><span data-stu-id="d94e8-288">Format-Table</span></span>](../Microsoft.PowerShell.Utility/Format-Table.md)

[<span data-ttu-id="d94e8-289">Get-Member</span><span class="sxs-lookup"><span data-stu-id="d94e8-289">Get-Member</span></span>](../Microsoft.PowerShell.Utility/Get-Member.md)

[<span data-ttu-id="d94e8-290">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="d94e8-290">Receive-Job</span></span>](../Microsoft.PowerShell.Core/Receive-Job.md)

[<span data-ttu-id="d94e8-291">Start-Job</span><span class="sxs-lookup"><span data-stu-id="d94e8-291">Start-Job</span></span>](../Microsoft.PowerShell.Core/Start-Job.md)

[<span data-ttu-id="d94e8-292">Where-Object</span><span class="sxs-lookup"><span data-stu-id="d94e8-292">Where-Object</span></span>](..//Microsoft.PowerShell.Core/Where-Object.md)

