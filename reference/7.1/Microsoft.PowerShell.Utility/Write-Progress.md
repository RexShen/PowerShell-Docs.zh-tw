---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-progress?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Progress
ms.openlocfilehash: 9e7aa9efce77e4c4c917658aeb2ecaabcd67e1e6
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208532"
---
# <span data-ttu-id="287e9-103">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="287e9-103">Write-Progress</span></span>

## <span data-ttu-id="287e9-104">概要</span><span class="sxs-lookup"><span data-stu-id="287e9-104">SYNOPSIS</span></span>
<span data-ttu-id="287e9-105">在 PowerShell 命令視窗中顯示進度列。</span><span class="sxs-lookup"><span data-stu-id="287e9-105">Displays a progress bar within a PowerShell command window.</span></span>

## <span data-ttu-id="287e9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="287e9-106">SYNTAX</span></span>

```
Write-Progress [-Activity] <String> [[-Status] <String>] [[-Id] <Int32>] [-PercentComplete <Int32>]
 [-SecondsRemaining <Int32>] [-CurrentOperation <String>] [-ParentId <Int32>] [-Completed] [-SourceId <Int32>]
 [<CommonParameters>]
```

## <span data-ttu-id="287e9-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="287e9-107">DESCRIPTION</span></span>

<span data-ttu-id="287e9-108">此 `Write-Progress` Cmdlet 會在 PowerShell 命令視窗中顯示進度列，以描述執行中命令或腳本的狀態。</span><span class="sxs-lookup"><span data-stu-id="287e9-108">The `Write-Progress` cmdlet displays a progress bar in a PowerShell command window that depicts the status of a running command or script.</span></span> <span data-ttu-id="287e9-109">您可以選擇進度列反映的指示器及進度列上下方顯示的文字。</span><span class="sxs-lookup"><span data-stu-id="287e9-109">You can select the indicators that the bar reflects and the text that appears above and below the progress bar.</span></span>

## <span data-ttu-id="287e9-110">範例</span><span class="sxs-lookup"><span data-stu-id="287e9-110">EXAMPLES</span></span>

### <span data-ttu-id="287e9-111">範例1：顯示 For 迴圈的進度</span><span class="sxs-lookup"><span data-stu-id="287e9-111">Example 1: Display the progress of a For loop</span></span>

```powershell
for ($i = 1; $i -le 100; $i++ )
{
    Write-Progress -Activity "Search in Progress" -Status "$i% Complete:" -PercentComplete $i;
}
```

<span data-ttu-id="287e9-112">此命令會顯示 For 迴圈從 1 計算至 100 的進度。</span><span class="sxs-lookup"><span data-stu-id="287e9-112">This command displays the progress of a For loop that counts from 1 to 100.</span></span>

<span data-ttu-id="287e9-113">此 `Write-Progress` Cmdlet 包含狀態列標題 `Activity` 、狀態行和變數 `$i` (「For 迴圈」中的計數器) ，指出工作的相對完整性。</span><span class="sxs-lookup"><span data-stu-id="287e9-113">The `Write-Progress` cmdlet includes a status bar heading `Activity`, a status line, and the variable `$i` (the counter in the For loop), which indicates the relative completeness of the task.</span></span>

### <span data-ttu-id="287e9-114">範例2：顯示 nested For 迴圈的進度</span><span class="sxs-lookup"><span data-stu-id="287e9-114">Example 2: Display the progress of nested For loops</span></span>

```powershell
for($I = 1; $I -lt 101; $I++ )
{
    Write-Progress -Activity Updating -Status 'Progress->' -PercentComplete $I -CurrentOperation OuterLoop
    for($j = 1; $j -lt 101; $j++ )
    {
        Write-Progress -Id 1 -Activity Updating -Status 'Progress' -PercentComplete $j -CurrentOperation InnerLoop
    }
}
```

```Output
Updating
Progress ->
 [ooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo]
OuterLoop
Updating
Progress
 [oooooooooooooooooo                                                   ]
InnerLoop
```

<span data-ttu-id="287e9-115">此範例會顯示兩個巢狀 For 迴圈的進度，每個迴圈都會以進度列表示。</span><span class="sxs-lookup"><span data-stu-id="287e9-115">This example displays the progress of two nested For loops, each of which is represented by a progress bar.</span></span>

<span data-ttu-id="287e9-116">`Write-Progress`第二個進度列的命令包含用來區分它與第一個進度列的 **識別碼** 參數。</span><span class="sxs-lookup"><span data-stu-id="287e9-116">The `Write-Progress` command for the second progress bar includes the **Id** parameter that distinguishes it from the first progress bar.</span></span>

<span data-ttu-id="287e9-117">如果沒有 **Id** 參數，進度列就會彼此重迭，而不是顯示在另一個。</span><span class="sxs-lookup"><span data-stu-id="287e9-117">Without the **Id** parameter, the progress bars would be superimposed on each other instead of being displayed one below the other.</span></span>

### <span data-ttu-id="287e9-118">範例3：在搜尋字串時顯示進度</span><span class="sxs-lookup"><span data-stu-id="287e9-118">Example 3: Display the progress while searching for a string</span></span>

```powershell
# Use Get-EventLog to get the events in the System log and store them in the $Events variable.
$Events = Get-EventLog -LogName system
# Pipe the events to the ForEach-Object cmdlet.
$Events | ForEach-Object -Begin {
    # In the Begin block, use Clear-Host to clear the screen.
    Clear-Host
    # Set the $i counter variable to zero.
    $i = 0
    # Set the $out variable to a empty string.
    $out = ""
} -Process {
    # In the Process script block search the message property of each incoming object for "bios".
    if($_.message -like "*bios*")
    {
        # Append the matching message to the out variable.
        $out=$out + $_.Message
    }
    # Increment the $i counter variable which is used to create the progress bar.
    $i = $i+1
    # Use Write-Progress to output a progress bar.
    # The Activity and Status parameters create the first and second lines of the progress bar heading, respectively.
    Write-Progress -Activity "Searching Events" -Status "Progress:" -PercentComplete ($i/$Events.count*100)
} -End {
    # Display the matching messages using the out variable.
    $out
}
```

<span data-ttu-id="287e9-119">此命令會顯示在「系統」記錄檔中尋找 "bios" 字串之命令的進度。</span><span class="sxs-lookup"><span data-stu-id="287e9-119">This command displays the progress of a command to find the string "bios" in the System event log.</span></span>

<span data-ttu-id="287e9-120">值 **的計算** 方式是將已處理的事件總數所處理的事件數目除以， `$I` 然後將 `$Events.count` 該結果乘以100。</span><span class="sxs-lookup"><span data-stu-id="287e9-120">The **PercentComplete** parameter value is calculated by dividing the number of events that have been processed `$I` by the total number of events retrieved `$Events.count` and then multiplying that result by 100.</span></span>

### <span data-ttu-id="287e9-121">範例4：顯示每個嵌套進程層級的進度</span><span class="sxs-lookup"><span data-stu-id="287e9-121">Example 4: Display progress for each level of a nested process</span></span>

```powershell
foreach ( $i in 1..10 ) {
  Write-Progress -Id 0 "Step $i"
  foreach ( $j in 1..10 ) {
    Write-Progress -Id 1 -ParentId 0 "Step $i - Substep $j"
    foreach ( $k in 1..10 ) {
      Write-Progress -Id 2  -ParentId 1 "Step $i - Substep $j - iteration $k"; start-sleep -m 150
    }
  }
}
```

```Output
Step 1
     Processing
    Step 1 - Substep 2
         Processing
        Step 1 - Substep 2 - Iteration 3
             Processing
```

<span data-ttu-id="287e9-122">在此範例中，您可以使用 **ParentId** 參數將輸出縮排，以顯示每個步驟進度中的父/子關聯性。</span><span class="sxs-lookup"><span data-stu-id="287e9-122">In this example you can use the **ParentId** parameter to have indented output to show parent/child relationships in the progress of each step.</span></span>

## <span data-ttu-id="287e9-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="287e9-123">PARAMETERS</span></span>

### <span data-ttu-id="287e9-124">-Activity</span><span class="sxs-lookup"><span data-stu-id="287e9-124">-Activity</span></span>

<span data-ttu-id="287e9-125">指定狀態列上方標題中文字的第一行。</span><span class="sxs-lookup"><span data-stu-id="287e9-125">Specifies the first line of text in the heading above the status bar.</span></span>
<span data-ttu-id="287e9-126">此文字說明正在報告其進度的活動。</span><span class="sxs-lookup"><span data-stu-id="287e9-126">This text describes the activity whose progress is being reported.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="287e9-127">-Completed</span><span class="sxs-lookup"><span data-stu-id="287e9-127">-Completed</span></span>

<span data-ttu-id="287e9-128">指示是否顯示進度列。</span><span class="sxs-lookup"><span data-stu-id="287e9-128">Indicates whether the progress bar is visible.</span></span>
<span data-ttu-id="287e9-129">如果省略此參數，則會 `Write-Progress` 顯示進度資訊。</span><span class="sxs-lookup"><span data-stu-id="287e9-129">If this parameter is omitted, `Write-Progress` displays progress information.</span></span>

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

### <span data-ttu-id="287e9-130">-CurrentOperation</span><span class="sxs-lookup"><span data-stu-id="287e9-130">-CurrentOperation</span></span>

<span data-ttu-id="287e9-131">指定進度列下方的文字行。</span><span class="sxs-lookup"><span data-stu-id="287e9-131">Specifies the line of text below the progress bar.</span></span>
<span data-ttu-id="287e9-132">此文字說明目前執行的操作。</span><span class="sxs-lookup"><span data-stu-id="287e9-132">This text describes the operation that is currently taking place.</span></span>

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

### <span data-ttu-id="287e9-133">-Id</span><span class="sxs-lookup"><span data-stu-id="287e9-133">-Id</span></span>

<span data-ttu-id="287e9-134">指定區別每個進度列的識別碼。</span><span class="sxs-lookup"><span data-stu-id="287e9-134">Specifies an ID that distinguishes each progress bar from the others.</span></span> <span data-ttu-id="287e9-135">在單一命令中建立超過一個進度列時，請使用此參數。</span><span class="sxs-lookup"><span data-stu-id="287e9-135">Use this parameter when you are creating more than one progress bar in a single command.</span></span> <span data-ttu-id="287e9-136">如果進度列沒有不同的識別碼，它們會重疊，而不會以序列方式顯示。</span><span class="sxs-lookup"><span data-stu-id="287e9-136">If the progress bars do not have different IDs, they are superimposed instead of being displayed in a series.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="287e9-137">-ParentId</span><span class="sxs-lookup"><span data-stu-id="287e9-137">-ParentId</span></span>

<span data-ttu-id="287e9-138">指定目前活動的父活動。</span><span class="sxs-lookup"><span data-stu-id="287e9-138">Specifies the parent activity of the current activity.</span></span>
<span data-ttu-id="287e9-139">如果目前活動沒有父系活動，請使用 -1 作為值。</span><span class="sxs-lookup"><span data-stu-id="287e9-139">Use the value -1 if the current activity has no parent activity.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="287e9-140">-PercentComplete</span><span class="sxs-lookup"><span data-stu-id="287e9-140">-PercentComplete</span></span>

<span data-ttu-id="287e9-141">指定完成之活動的百分比。</span><span class="sxs-lookup"><span data-stu-id="287e9-141">Specifies the percentage of the activity that is completed.</span></span>
<span data-ttu-id="287e9-142">如果完成的百分比不明或不適用，請使用 -1 作為值。</span><span class="sxs-lookup"><span data-stu-id="287e9-142">Use the value -1 if the percentage complete is unknown or not applicable.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="287e9-143">-SecondsRemaining</span><span class="sxs-lookup"><span data-stu-id="287e9-143">-SecondsRemaining</span></span>

<span data-ttu-id="287e9-144">指定活動完成之前預計的剩餘秒數。</span><span class="sxs-lookup"><span data-stu-id="287e9-144">Specifies the projected number of seconds remaining until the activity is completed.</span></span>
<span data-ttu-id="287e9-145">如果剩餘秒數不明或不適用，請使用 -1 作為值。</span><span class="sxs-lookup"><span data-stu-id="287e9-145">Use the value -1 if the number of seconds remaining is unknown or not applicable.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="287e9-146">-SourceId</span><span class="sxs-lookup"><span data-stu-id="287e9-146">-SourceId</span></span>

<span data-ttu-id="287e9-147">指定記錄的來源。</span><span class="sxs-lookup"><span data-stu-id="287e9-147">Specifies the source of the record.</span></span> <span data-ttu-id="287e9-148">您可以使用此取代 **識別碼** ，但不能搭配其他參數（例如 **ParentId** ）使用。</span><span class="sxs-lookup"><span data-stu-id="287e9-148">You can use this in place of **Id** but cannot be used with other parameters like **ParentId** .</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="287e9-149">-Status</span><span class="sxs-lookup"><span data-stu-id="287e9-149">-Status</span></span>

<span data-ttu-id="287e9-150">指定狀態列上方標題中文字的第二行。</span><span class="sxs-lookup"><span data-stu-id="287e9-150">Specifies the second line of text in the heading above the status bar.</span></span>
<span data-ttu-id="287e9-151">此文字說明活動的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="287e9-151">This text describes current state of the activity.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="287e9-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="287e9-152">CommonParameters</span></span>

<span data-ttu-id="287e9-153">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="287e9-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="287e9-154">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="287e9-154">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="287e9-155">輸入</span><span class="sxs-lookup"><span data-stu-id="287e9-155">INPUTS</span></span>

### <span data-ttu-id="287e9-156">無</span><span class="sxs-lookup"><span data-stu-id="287e9-156">None</span></span>

<span data-ttu-id="287e9-157">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="287e9-157">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="287e9-158">輸出</span><span class="sxs-lookup"><span data-stu-id="287e9-158">OUTPUTS</span></span>

### <span data-ttu-id="287e9-159">無</span><span class="sxs-lookup"><span data-stu-id="287e9-159">None</span></span>

<span data-ttu-id="287e9-160">`Write-Progress` 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="287e9-160">`Write-Progress` does not generate any output.</span></span>

## <span data-ttu-id="287e9-161">注意</span><span class="sxs-lookup"><span data-stu-id="287e9-161">NOTES</span></span>

<span data-ttu-id="287e9-162">如果沒有顯示進度列，請檢查變數的值 `$ProgressPreference` 。</span><span class="sxs-lookup"><span data-stu-id="287e9-162">If the progress bar does not appear, check the value of the `$ProgressPreference` variable.</span></span> <span data-ttu-id="287e9-163">如果值是設為 SilentlyContinue，就不會顯示進度列。</span><span class="sxs-lookup"><span data-stu-id="287e9-163">If the value is set to SilentlyContinue, the progress bar is not displayed.</span></span> <span data-ttu-id="287e9-164">如需 PowerShell 喜好設定的詳細資訊，請參閱 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="287e9-164">For more information about PowerShell preferences, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="287e9-165">指令程式的參數會對應至 **ProgressRecord** 類別的屬性。</span><span class="sxs-lookup"><span data-stu-id="287e9-165">The parameters of the cmdlet correspond to the properties of the **System.Management.Automation.ProgressRecord** class.</span></span> <span data-ttu-id="287e9-166">如需詳細資訊，請參閱 [ProgressRecord 類別](/dotnet/api/system.management.automation.progressrecord)。</span><span class="sxs-lookup"><span data-stu-id="287e9-166">For more information, see [ProgressRecord Class](/dotnet/api/system.management.automation.progressrecord).</span></span>

## <span data-ttu-id="287e9-167">相關連結</span><span class="sxs-lookup"><span data-stu-id="287e9-167">RELATED LINKS</span></span>

[<span data-ttu-id="287e9-168">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="287e9-168">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="287e9-169">Write-Error</span><span class="sxs-lookup"><span data-stu-id="287e9-169">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="287e9-170">Write-Host</span><span class="sxs-lookup"><span data-stu-id="287e9-170">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="287e9-171">Write-Output</span><span class="sxs-lookup"><span data-stu-id="287e9-171">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="287e9-172">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="287e9-172">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="287e9-173">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="287e9-173">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="287e9-174">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="287e9-174">Write-Warning</span></span>](Write-Warning.md)
