---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 10/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/export-counter?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Counter
ms.openlocfilehash: 54498eb504a1d13a5b96a2583b5e5d6e4c08735e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206675"
---
# <span data-ttu-id="68468-103">Export-Counter</span><span class="sxs-lookup"><span data-stu-id="68468-103">Export-Counter</span></span>

## <span data-ttu-id="68468-104">概要</span><span class="sxs-lookup"><span data-stu-id="68468-104">SYNOPSIS</span></span>
<span data-ttu-id="68468-105">將效能計數器資料匯出至記錄檔。</span><span class="sxs-lookup"><span data-stu-id="68468-105">Exports performance counter data to log files.</span></span>

## <span data-ttu-id="68468-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="68468-106">SYNTAX</span></span>

```
Export-Counter [-Path] <String> [-FileFormat <String>] [-MaxSize <UInt32>]
 -InputObject <PerformanceCounterSampleSet[]> [-Force] [-Circular] [<CommonParameters>]
```

## <span data-ttu-id="68468-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="68468-107">DESCRIPTION</span></span>

<span data-ttu-id="68468-108">此 `Export-Counter` Cmdlet 會將效能計數器資料匯出 (PerformanceCounterSampleSet 物件) 至二進位效能記錄檔中的記錄檔 ( .blg) 、逗點分隔值 ( .csv) 或定位字元分隔值 ( tsv) 格式。</span><span class="sxs-lookup"><span data-stu-id="68468-108">The `Export-Counter` cmdlet exports performance counter data (PerformanceCounterSampleSet objects) to log files in binary performance log (.blg), comma-separated value (.csv), or tab-separated value (.tsv) format.</span></span> <span data-ttu-id="68468-109">您可以使用這個 Cmdlet 來記錄效能計數器資料。</span><span class="sxs-lookup"><span data-stu-id="68468-109">You use this cmdlet to log performance counter data.</span></span>

<span data-ttu-id="68468-110">此 `Export-Counter` Cmdlet 是設計用來匯出和 Cmdlet 所傳回的 `Get-Counter` 資料 `Import-Counter` 。</span><span class="sxs-lookup"><span data-stu-id="68468-110">The `Export-Counter` cmdlet is designed to export data that is returned by the `Get-Counter` and `Import-Counter` cmdlets.</span></span>

<span data-ttu-id="68468-111">此 Cmdlet 只能在 Windows 7、Windows Server 2008 R2 及更新版本的 Windows 上執行。</span><span class="sxs-lookup"><span data-stu-id="68468-111">This cmdlet runs only on Windows 7, Windows Server 2008 R2, and later versions of Windows.</span></span>

## <span data-ttu-id="68468-112">範例</span><span class="sxs-lookup"><span data-stu-id="68468-112">EXAMPLES</span></span>

### <span data-ttu-id="68468-113">範例1：將計數器資料匯出至檔案</span><span class="sxs-lookup"><span data-stu-id="68468-113">EXAMPLE 1: Export counter data to a file</span></span>

<span data-ttu-id="68468-114">此範例會將計數器資料匯出至 .BLG 檔案。</span><span class="sxs-lookup"><span data-stu-id="68468-114">This example exports counter data to a BLG file.</span></span>

```powershell
Get-Counter "\Processor(*)\% Processor Time" | Export-Counter -Path $home\Counters.blg
```

<span data-ttu-id="68468-115">此命令會使用 `Get-Counter` Cmdlet 來收集處理器時間資料。</span><span class="sxs-lookup"><span data-stu-id="68468-115">The command uses the `Get-Counter` cmdlet to collect processor time data.</span></span> <span data-ttu-id="68468-116">它使用管線運算子 (|) 將資料傳送至 `Export-Counter` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="68468-116">It uses a pipeline operator (|) to send the data to the `Export-Counter` cmdlet.</span></span> <span data-ttu-id="68468-117">此 `Export-Counter` 命令會使用 **Path** 變數來指定輸出檔。</span><span class="sxs-lookup"><span data-stu-id="68468-117">The `Export-Counter` command uses the **Path** variable to specify the output file.</span></span>

<span data-ttu-id="68468-118">因為資料集可能非常大，所以此範例會透過管線將資料傳送至 `Export-Counter` 。</span><span class="sxs-lookup"><span data-stu-id="68468-118">Because the data set might be very large, this example sends the data to `Export-Counter` through the pipeline.</span></span> <span data-ttu-id="68468-119">如果資料儲存在變數中，您可能會使用不相稱的記憶體量。</span><span class="sxs-lookup"><span data-stu-id="68468-119">If the data were saved in a variable, you might use a disproportionate amount of memory.</span></span>

### <span data-ttu-id="68468-120">範例 2︰將檔案匯出至計數器檔案格式</span><span class="sxs-lookup"><span data-stu-id="68468-120">Example 2: Export a file to a counter file format</span></span>

<span data-ttu-id="68468-121">此範例會將 CSV 檔案轉換成計數器資料的 .BLG 格式。</span><span class="sxs-lookup"><span data-stu-id="68468-121">This example converts a CSV file to a counter data BLG format.</span></span>

<span data-ttu-id="68468-122">此 `Import-Counter` Cmdlet 會從檔案匯入效能計數器資料 `Threads.csv` 。</span><span class="sxs-lookup"><span data-stu-id="68468-122">The `Import-Counter` cmdlet imports performance counter data from the `Threads.csv` file.</span></span> <span data-ttu-id="68468-123">此範例假設先前使用指令程式匯出此檔案 `Export-Counter` 。</span><span class="sxs-lookup"><span data-stu-id="68468-123">The example presumes that this file was previously exported by using the `Export-Counter` cmdlet.</span></span> <span data-ttu-id="68468-124">管線運算子 (`|`) 將匯入的資料傳送至 `Export-Counter` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="68468-124">A pipeline operator (`|`) sends the imported data to the `Export-Counter` cmdlet.</span></span> <span data-ttu-id="68468-125">命令使用 **Path** 參數指定輸出檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="68468-125">The command uses the **Path** parameter to specify the location of the output file.</span></span> <span data-ttu-id="68468-126">它會使用 **迴圈** 和 **MaxSize** 參數，指示 `Export-Counter` CMDLET 建立包裝在 1 GB 的迴圈記錄檔。</span><span class="sxs-lookup"><span data-stu-id="68468-126">It uses the **Circular** and **MaxSize** parameters to direct the `Export-Counter` cmdlet to create a circular log that wraps at 1 GB.</span></span> <span data-ttu-id="68468-127">**MaxSize** 參數以 mb 表示。</span><span class="sxs-lookup"><span data-stu-id="68468-127">The **MaxSize** parameter is expressed in megabytes.</span></span>

```powershell
$1GBInMB = 1024 # 1GB = 1024MB
Import-Counter Threads.csv | Export-Counter -Path ThreadTest.blg -Circular -MaxSize $1GBInMB
```

### <span data-ttu-id="68468-128">範例 3︰從遠端電腦取得計數器資料，並將資料儲存至檔案</span><span class="sxs-lookup"><span data-stu-id="68468-128">Example 3: Get counter data from a remote computer and save the data to a file</span></span>

<span data-ttu-id="68468-129">此範例說明如何從遠端電腦取得效能計數器資料，並將資料儲存在遠端電腦上的檔案中。</span><span class="sxs-lookup"><span data-stu-id="68468-129">This example shows how to get performance counter data from a remote computer and save the data in a file on the remote computer.</span></span>

<span data-ttu-id="68468-130">第一個命令會使用 `Get-Counter` Cmdlet 從遠端電腦的 Server01 收集工作集計數器資料。</span><span class="sxs-lookup"><span data-stu-id="68468-130">The first command uses the `Get-Counter` cmdlet to collect working set counter data from Server01, a remote computer.</span></span> <span data-ttu-id="68468-131">此命令會將資料儲存在 `$C` 變數中。</span><span class="sxs-lookup"><span data-stu-id="68468-131">The command saves the data in the `$C` variable.</span></span>

<span data-ttu-id="68468-132">第二個命令會使用管線運算子 (`|`) 將資料傳送 `$C` 至 Cmdlet，以將它儲存 `Export-Counter` 在 `Workingset.blg` Server01 電腦的效能共用中的檔案。</span><span class="sxs-lookup"><span data-stu-id="68468-132">The second command uses a pipeline operator (`|`) to send the data in `$C` to the `Export-Counter` cmdlet, which saves it in the `Workingset.blg` file in the Perf share of the Server01 computer.</span></span>

```powershell
$C = Get-Counter -ComputerName Server01 -Counter "\Process(*)\Working Set - Private" -MaxSamples $C | Export-Counter -Path \\Server01\Perf\WorkingSet.blg
```

```Output
20
```

### <span data-ttu-id="68468-133">範例 4︰重新記錄現有的資料</span><span class="sxs-lookup"><span data-stu-id="68468-133">Example 4: Re-log existing data</span></span>

<span data-ttu-id="68468-134">此範例示範如何使用 `Import-Counter` 和 `Export-Counter` Cmdlet 重新記錄現有的資料。</span><span class="sxs-lookup"><span data-stu-id="68468-134">This example shows how to use the `Import-Counter` and `Export-Counter` cmdlets to re-log existing data.</span></span>

<span data-ttu-id="68468-135">第一個命令會使用 `Import-Counter` Cmdlet，從磁碟空間 .blg 記錄檔匯入效能計數器資料。</span><span class="sxs-lookup"><span data-stu-id="68468-135">The first command uses the `Import-Counter` cmdlet to import performance counter data from the DiskSpace.blg log.</span></span> <span data-ttu-id="68468-136">它會將資料儲存在 `$All` 變數中。</span><span class="sxs-lookup"><span data-stu-id="68468-136">It saves the data in the `$All` variable.</span></span> <span data-ttu-id="68468-137">此檔案包含 \% 企業中超過200部遠端電腦上的「LogicalDisk 可用空間」計數器範例。</span><span class="sxs-lookup"><span data-stu-id="68468-137">This file contains samples of the "LogicalDisk\% Free Space" counter on more than 200 remote computers in the enterprise.</span></span>

<span data-ttu-id="68468-138">第二個命令會使用 `Where-Object` Cmdlet 來選取 **CookedValue** 小於 15 (%) 的物件。</span><span class="sxs-lookup"><span data-stu-id="68468-138">The second command uses the `Where-Object` cmdlet to select objects with **CookedValue** of less than 15 (percent).</span></span> <span data-ttu-id="68468-139">命令會將結果儲存在 `$LowSpace` 變數中。</span><span class="sxs-lookup"><span data-stu-id="68468-139">The command saves the results in the `$LowSpace` variable.</span></span>

<span data-ttu-id="68468-140">第三個命令會使用管線運算子 (`|`) 將變數中的資料傳送 `$LowSpace` 至 `Export-Counter` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="68468-140">The third command uses a pipeline operator (`|`) to send the data in the `$LowSpace` variable to the `Export-Counter` cmdlet.</span></span> <span data-ttu-id="68468-141">命令使用 **Path** 參數，指示選取的資料應記錄到 LowDiskSpace.blg 檔案中。</span><span class="sxs-lookup"><span data-stu-id="68468-141">The command uses the **Path** parameter to indicate that the selected data should be logged in the LowDiskSpace.blg file.</span></span>

```powershell
$All = Import-Counter DiskSpace.blg
$LowSpace = $All | Where-Object {$_.CounterSamples.CookedValue -lt 15}
$LowSpace | Export-Counter -Path LowDiskSpace.blg
```

## <span data-ttu-id="68468-142">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="68468-142">PARAMETERS</span></span>

### <span data-ttu-id="68468-143">-Circular</span><span class="sxs-lookup"><span data-stu-id="68468-143">-Circular</span></span>

<span data-ttu-id="68468-144">指出輸出檔為先進先出 (FIFO) 格式的循環記錄檔。</span><span class="sxs-lookup"><span data-stu-id="68468-144">Indicates that the output file is a circular log with first in, first out (FIFO) format.</span></span>
<span data-ttu-id="68468-145">當您包括此參數時， **MaxSize** 是必要參數。</span><span class="sxs-lookup"><span data-stu-id="68468-145">When you include this parameter, the **MaxSize** parameter is required.</span></span>

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

### <span data-ttu-id="68468-146">-FileFormat</span><span class="sxs-lookup"><span data-stu-id="68468-146">-FileFormat</span></span>

<span data-ttu-id="68468-147">指定輸出記錄檔的輸出格式。</span><span class="sxs-lookup"><span data-stu-id="68468-147">Specifies the output format of the output log file.</span></span>

<span data-ttu-id="68468-148">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="68468-148">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="68468-149">CSV</span><span class="sxs-lookup"><span data-stu-id="68468-149">CSV</span></span>
- <span data-ttu-id="68468-150">TSV</span><span class="sxs-lookup"><span data-stu-id="68468-150">TSV</span></span>
- <span data-ttu-id="68468-151">BLG</span><span class="sxs-lookup"><span data-stu-id="68468-151">BLG</span></span>

<span data-ttu-id="68468-152">預設值為 BLG。</span><span class="sxs-lookup"><span data-stu-id="68468-152">The default value is BLG.</span></span>

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

### <span data-ttu-id="68468-153">-Force</span><span class="sxs-lookup"><span data-stu-id="68468-153">-Force</span></span>

<span data-ttu-id="68468-154">若 **Path** 參數所指定的位置已有檔案存在，就會覆寫並取代現有檔案。</span><span class="sxs-lookup"><span data-stu-id="68468-154">Overwrites and replaces an existing file if one exists in the location specified by the **Path** parameter.</span></span>

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

### <span data-ttu-id="68468-155">-InputObject</span><span class="sxs-lookup"><span data-stu-id="68468-155">-InputObject</span></span>

<span data-ttu-id="68468-156">以陣列格式指定要匯出的計數器資料。</span><span class="sxs-lookup"><span data-stu-id="68468-156">Specifies, as an array, the counter data to export.</span></span> <span data-ttu-id="68468-157">輸入包含資料的變數，或輸入可取得資料的命令，例如 `Get-Counter` 或 `Import-Counter` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="68468-157">Enter a variable that contains the data or a command that gets the data, such as the `Get-Counter` or `Import-Counter` cmdlet.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet[]
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="68468-158">-MaxSize</span><span class="sxs-lookup"><span data-stu-id="68468-158">-MaxSize</span></span>

<span data-ttu-id="68468-159">指定輸出檔案的大小上限，以 mb (MB) 。</span><span class="sxs-lookup"><span data-stu-id="68468-159">Specifies the maximum size of the output file in megabytes (MB).</span></span>

<span data-ttu-id="68468-160">若指定 **Circular** 參數，則會在記錄檔達到指定的大小上限時，於較新的項目加入時刪除最舊的項目。</span><span class="sxs-lookup"><span data-stu-id="68468-160">If the **Circular** parameter is specified, then when the log file reaches the specified maximum size, the oldest entries are deleted as newer ones are added.</span></span> <span data-ttu-id="68468-161">若未指定 **Circular** 參數，則會在記錄檔達到指定的大小上限時，停止加入任何新資料，且此 Cmdlet 會產生一個非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="68468-161">If the **Circular** parameter is not specified, then when the log file reaches the specified maximum size, no new data is added and the cmdlet generates a non-terminating error.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="68468-162">-Path</span><span class="sxs-lookup"><span data-stu-id="68468-162">-Path</span></span>

<span data-ttu-id="68468-163">指定輸出檔案的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="68468-163">Specifies the path and file name of the output file.</span></span> <span data-ttu-id="68468-164">請在本機電腦上輸入相對或絕對路徑，或在遠端電腦上輸入統一命名慣例 (UNC) 路徑，例如 `\\Computer\Share\file.blg` 。</span><span class="sxs-lookup"><span data-stu-id="68468-164">Enter a relative or absolute path on the local computer, or a Uniform Naming Convention (UNC) path to a remote computer, such as `\\Computer\Share\file.blg`.</span></span> <span data-ttu-id="68468-165">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="68468-165">This parameter is required.</span></span>

<span data-ttu-id="68468-166">檔案格式是由 **FileFormat** 參數的值來決定，而不是由路徑中的副檔名所決定。</span><span class="sxs-lookup"><span data-stu-id="68468-166">The file format is determined by the value of the **FileFormat** parameter, not by the file name extension in the path.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="68468-167">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="68468-167">CommonParameters</span></span>

<span data-ttu-id="68468-168">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="68468-168">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="68468-169">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="68468-169">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="68468-170">輸入</span><span class="sxs-lookup"><span data-stu-id="68468-170">INPUTS</span></span>

### <span data-ttu-id="68468-171">Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet</span><span class="sxs-lookup"><span data-stu-id="68468-171">Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet</span></span>

<span data-ttu-id="68468-172">您可以透過管線將效能計數器資料從 `Get-Counter` 或傳送 `Import-Counter` 至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="68468-172">You can pipe performance counter data from `Get-Counter` or `Import-Counter` to this cmdlet.</span></span>

## <span data-ttu-id="68468-173">輸出</span><span class="sxs-lookup"><span data-stu-id="68468-173">OUTPUTS</span></span>

### <span data-ttu-id="68468-174">無</span><span class="sxs-lookup"><span data-stu-id="68468-174">None</span></span>

## <span data-ttu-id="68468-175">注意</span><span class="sxs-lookup"><span data-stu-id="68468-175">NOTES</span></span>

<span data-ttu-id="68468-176">記錄檔產生器會預期所有輸入物件都具有相同的計數器路徑，並且物件會依時間以遞增順序排列。</span><span class="sxs-lookup"><span data-stu-id="68468-176">The log file generator expects that all input objects have the same counter path and that the objects are arranged in ascending time order.</span></span>

<span data-ttu-id="68468-177">計數器類別和第一個輸入物件的路徑會決定記錄檔中記錄的屬性。</span><span class="sxs-lookup"><span data-stu-id="68468-177">The counter type and path of the first input object determines the properties recorded in the log file.</span></span> <span data-ttu-id="68468-178">若其他輸入物件沒有記錄之屬性的值，屬性欄位就會是空的。</span><span class="sxs-lookup"><span data-stu-id="68468-178">If other input objects do not have a value for a recorded property, the property field is empty.</span></span> <span data-ttu-id="68468-179">若物件具有未記錄的屬性值，則會忽略額外的屬性值。</span><span class="sxs-lookup"><span data-stu-id="68468-179">If the objects have property values that were not recorded, the extra property values are ignored.</span></span>

<span data-ttu-id="68468-180">效能監視器可能無法讀取產生的所有記錄 `Export-Counter` 。</span><span class="sxs-lookup"><span data-stu-id="68468-180">Performance Monitor might not be able to read all logs that `Export-Counter` generates.</span></span> <span data-ttu-id="68468-181">例如，效能監視器要求所有物件都要有相同的路徑，而且所有物件都以相同的時間間隔分隔。</span><span class="sxs-lookup"><span data-stu-id="68468-181">For instance, Performance Monitor requires that all objects have the same path and that all objects are separated by the same time interval.</span></span>

<span data-ttu-id="68468-182">`Import-Counter`Cmdlet 沒有 **ComputerName** 參數。</span><span class="sxs-lookup"><span data-stu-id="68468-182">The `Import-Counter` cmdlet does not have a **ComputerName** parameter.</span></span> <span data-ttu-id="68468-183">但是，如果電腦設定為遠端 Windows PowerShell Windows PowerShell，您可以使用 `Invoke-Command` Cmdlet `Import-Counter` 在遠端電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="68468-183">However, if the computer is configured for remote Windows PowerShell Windows PowerShell, you can use the `Invoke-Command` cmdlet to run an `Import-Counter` command on a remote computer.</span></span>

## <span data-ttu-id="68468-184">相關連結</span><span class="sxs-lookup"><span data-stu-id="68468-184">RELATED LINKS</span></span>

[<span data-ttu-id="68468-185">Get-Counter</span><span class="sxs-lookup"><span data-stu-id="68468-185">Get-Counter</span></span>](Get-Counter.md)

[<span data-ttu-id="68468-186">Import-Counter</span><span class="sxs-lookup"><span data-stu-id="68468-186">Import-Counter</span></span>](Import-Counter.md)
