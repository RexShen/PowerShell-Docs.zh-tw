---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/disable-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-JobTrigger
ms.openlocfilehash: 236e6b7e6e450bd1f3f868f889a19cf796890127
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203032"
---
# <span data-ttu-id="693eb-103">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="693eb-103">Disable-JobTrigger</span></span>

## <span data-ttu-id="693eb-104">概要</span><span class="sxs-lookup"><span data-stu-id="693eb-104">SYNOPSIS</span></span>
<span data-ttu-id="693eb-105">停用排程工作的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="693eb-105">Disables the job triggers of scheduled jobs.</span></span>

## <span data-ttu-id="693eb-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="693eb-106">SYNTAX</span></span>

```
Disable-JobTrigger [-InputObject] <ScheduledJobTrigger[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="693eb-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="693eb-107">DESCRIPTION</span></span>
<span data-ttu-id="693eb-108">**Disable-JobTrigger** Cmdlet 會暫時停用排程工作的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="693eb-108">The **Disable-JobTrigger** cmdlet temporarily disables the job triggers of scheduled jobs.</span></span>
<span data-ttu-id="693eb-109">停用會保留所有工作觸發程序屬性，但不會防止工作觸發程序啟動排程工作。</span><span class="sxs-lookup"><span data-stu-id="693eb-109">Disabling preserves all job trigger properties, but it prevents the job trigger from starting the scheduled job.</span></span>

<span data-ttu-id="693eb-110">若要使用此 Cmdlet，請使用 Get-JobTrigger Cmdlet 來取得工作觸發程式。</span><span class="sxs-lookup"><span data-stu-id="693eb-110">To use this cmdlet, use the Get-JobTrigger cmdlet to get the job triggers.</span></span>
<span data-ttu-id="693eb-111">接著，使用管線傳送工作觸發程序至 **Disable-JobTrigger** 或使用其 *InputObject* 參數。</span><span class="sxs-lookup"><span data-stu-id="693eb-111">Then pipe the job triggers to **Disable-JobTrigger** or use its *InputObject* parameter.</span></span>

<span data-ttu-id="693eb-112">若要停用工作觸發 **程式，enable-jobtrigger** Cmdlet 會將工作觸發程式的 Enabled 屬性設定為 $False。</span><span class="sxs-lookup"><span data-stu-id="693eb-112">To disable a job trigger, the **Disable-JobTrigger** cmdlet sets the Enabled property of the job trigger to $False.</span></span>
<span data-ttu-id="693eb-113">若要重新啟用工作觸發程式，請使用 Enable-JobTrigger Cmdlet，此 Cmdlet 會將工作觸發程式的 **Enabled** 屬性設定為 $True。</span><span class="sxs-lookup"><span data-stu-id="693eb-113">To re-enable the job trigger, use the Enable-JobTrigger cmdlet, which sets the **Enabled** property of the job trigger to $True.</span></span>
<span data-ttu-id="693eb-114">停用工作觸發程序不會停用排程的工作 (例如 Disable-ScheduledJob Cmdlet 的作用)，但若您停用所有工作觸發程序，則效果等同於停用排程的工作。</span><span class="sxs-lookup"><span data-stu-id="693eb-114">Disabling a job trigger does not disable the scheduled job, such as is done by the Disable-ScheduledJob cmdlet, but if you disable all job triggers, the effect is the same as disabling the scheduled job.</span></span>

<span data-ttu-id="693eb-115">若停用排程工作或停用排程工作的所有工作觸發程序，您仍然可以使用 Start-Job Cmdlet 或使用停用的排程工作做為範本來啟動工作。</span><span class="sxs-lookup"><span data-stu-id="693eb-115">If you disable a scheduled job or disable all job triggers of a scheduled job, you can still start the job by using the Start-Job cmdlet or use the disabled scheduled job as a template.</span></span>

<span data-ttu-id="693eb-116">**Disable-ScheduledJob** 為 Windows PowerShell 內含之 **PSScheduledJob** 模組中的其中一個工作排程 Cmdlet 集合。</span><span class="sxs-lookup"><span data-stu-id="693eb-116">**Disable-ScheduledJob** is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="693eb-117">如需排程工作的詳細資訊，請參閱 PSScheduledJob 模組中的「關於」主題。</span><span class="sxs-lookup"><span data-stu-id="693eb-117">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="693eb-118">匯入 PSScheduledJob 模組，然後輸入：`Get-Help about_Scheduled*`，或參閱 about_Scheduled_Jobs。</span><span class="sxs-lookup"><span data-stu-id="693eb-118">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="693eb-119">此 Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="693eb-119">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="693eb-120">範例</span><span class="sxs-lookup"><span data-stu-id="693eb-120">EXAMPLES</span></span>

### <span data-ttu-id="693eb-121">範例 1：停用工作觸發程序</span><span class="sxs-lookup"><span data-stu-id="693eb-121">Example 1: Disable a job trigger</span></span>

```
PS C:\> Get-JobTrigger -Name "Backup-Archives" -TriggerID 1 | Disable-JobTrigger
```

<span data-ttu-id="693eb-122">此命令會停用本機電腦上 Backup-Archives 排程工作的第一個觸發程序 (識別碼=1)。</span><span class="sxs-lookup"><span data-stu-id="693eb-122">This command disables the first trigger (ID=1) of the Backup-Archives scheduled job on the local computer.</span></span>

<span data-ttu-id="693eb-123">此命令會使用 Get-JobTrigger Cmdlet 來取得工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="693eb-123">The command uses the Get-JobTrigger cmdlet to get the job trigger.</span></span>
<span data-ttu-id="693eb-124">管線運算子會傳送工作觸發程序至 **Disable-JobTrigger** Cmdlet，此 Cmdlet 會將它停用。</span><span class="sxs-lookup"><span data-stu-id="693eb-124">A pipeline operator sends the job trigger to the **Disable-JobTrigger** cmdlet, which disables it.</span></span>

### <span data-ttu-id="693eb-125">範例 2：停用所有工作觸發程序</span><span class="sxs-lookup"><span data-stu-id="693eb-125">Example 2: Disable all job triggers</span></span>

```
The first command uses the Get-ScheduledJob cmdlet to get the Backup-Archives and Inventory scheduled jobs. A pipeline operator (|) sends the scheduled jobs to the Get-JobTrigger cmdlet, which gets all job triggers of the scheduled jobs. Another pipeline operator sends the job triggers to the **Disable-JobTrigger** cmdlet, which disables them.The first command uses the **Get-ScheduledJob** cmdlet to get the jobs, because its *Name* parameter takes multiple names.
PS C:\> Get-ScheduledJob -Name "Backup-Archives,Inventory" | Get-JobTrigger | Disable-JobTrigger

The second command displays the results. The command repeats the **Get-ScheduledJob** and **Get-JobTrigger** command. A pipeline operator sends the job triggers to the Format-Table cmdlet, which displays the job triggers in a table. The **Format-Table** command adds a JobName property that displays the value of the Name property of the scheduled job in the JobDefinition property of the job trigger object.
PS C:\> Get-ScheduledJob -Name "Backup-Archives,Inventory" | Get-JobTrigger | Format-Table -Property ID, Frequency, At, DaysOfWeek, Enabled, @{Label="JobName";Expression={$_.JobDefinition.Name}} -AutoSize
Id Frequency At                     DaysOfWeek Enabled JobName
-- --------- --                     ---------- ------- -------
1  Weekly    9/28/2011 3:00:00 AM   {Monday}   False   Backup-Archive
2  Daily     9/29/2011 1:00:00 AM              False   Backup-Archive
1  Weekly    10/20/2011 11:00:00 PM {Friday}   False   Inventory
1  Weekly    11/2/2011 2:00:00 PM   {Monday}   False   Inventory
```

<span data-ttu-id="693eb-126">這些命令會停用兩個排程工作上的所有工作觸發程序，並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="693eb-126">These commands disable all job triggers on two scheduled jobs and display the results.</span></span>

### <span data-ttu-id="693eb-127">範例3：停用遠端電腦上排程工作的工作觸發程式</span><span class="sxs-lookup"><span data-stu-id="693eb-127">Example 3: Disable job trigger of a scheduled job on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName Server01 {Get-JobTrigger -Name DeployPackage | Where-Object {$_.Frequency -eq "Daily"} | Disable-JobTrigger}
```

<span data-ttu-id="693eb-128">此命令會停用 Server01 遠端電腦上 DeployPackage 排程工作的每日工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="693eb-128">This command disables the daily job triggers on the DeployPackage scheduled job on the Server01 remote computer.</span></span>

<span data-ttu-id="693eb-129">此命令會使用 Invoke-Command Cmdlet，在 Server01 電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="693eb-129">The command uses the Invoke-Command cmdlet to run the commands on the Server01 computer.</span></span>
<span data-ttu-id="693eb-130">遠端命令會使用 Get-JobTrigger Cmdlet 來取得 DeployPackage 排程工作的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="693eb-130">The remote command uses the Get-JobTrigger cmdlet to get the job triggers of the DeployPackage scheduled job.</span></span>
<span data-ttu-id="693eb-131">管線運算子會將工作觸發程式傳送至 Where-Object Cmdlet，此 Cmdlet 只會傳回每日工作觸發程式。</span><span class="sxs-lookup"><span data-stu-id="693eb-131">A pipeline operator sends the job triggers to the Where-Object cmdlet, which returns only daily job triggers.</span></span>
<span data-ttu-id="693eb-132">管線運算子會將每日工作觸發程式傳送至 **enable-jobtrigger** Cmdlet，以停用它們。</span><span class="sxs-lookup"><span data-stu-id="693eb-132">A pipeline operator sends the daily job triggers to the **Disable-JobTrigger** cmdlet, which disables them.</span></span>

## <span data-ttu-id="693eb-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="693eb-133">PARAMETERS</span></span>

### <span data-ttu-id="693eb-134">-InputObject</span><span class="sxs-lookup"><span data-stu-id="693eb-134">-InputObject</span></span>
<span data-ttu-id="693eb-135">指定要停用的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="693eb-135">Specifies the job trigger to be disabled.</span></span>
<span data-ttu-id="693eb-136">輸入變數，其中包含 **ScheduledJobTrigger** 物件，或輸入命令或運算式取得 **ScheduledJobTrigger** 物件，例如 Get-JobTrigger 命令。</span><span class="sxs-lookup"><span data-stu-id="693eb-136">Enter a variable that contains  **ScheduledJobTrigger** objects or type a command or expression that gets **ScheduledJobTrigger** objects, such as a Get-JobTrigger command.</span></span>
<span data-ttu-id="693eb-137">您也可以使用管線將 **ScheduledJobTrigger** 物件傳遞給 **Disable-JobTrigger** 。</span><span class="sxs-lookup"><span data-stu-id="693eb-137">You can also pipe a **ScheduledJobTrigger** object to **Disable-JobTrigger** .</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="693eb-138">-PassThru</span><span class="sxs-lookup"><span data-stu-id="693eb-138">-PassThru</span></span>
<span data-ttu-id="693eb-139">傳回代表您正在使用之項目的物件。</span><span class="sxs-lookup"><span data-stu-id="693eb-139">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="693eb-140">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="693eb-140">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="693eb-141">-Confirm</span><span class="sxs-lookup"><span data-stu-id="693eb-141">-Confirm</span></span>
<span data-ttu-id="693eb-142">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="693eb-142">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="693eb-143">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="693eb-143">-WhatIf</span></span>
<span data-ttu-id="693eb-144">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="693eb-144">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="693eb-145">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="693eb-145">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="693eb-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="693eb-146">CommonParameters</span></span>
<span data-ttu-id="693eb-147">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="693eb-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="693eb-148">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="693eb-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="693eb-149">輸入</span><span class="sxs-lookup"><span data-stu-id="693eb-149">INPUTS</span></span>

### <span data-ttu-id="693eb-150">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span><span class="sxs-lookup"><span data-stu-id="693eb-150">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span></span>
<span data-ttu-id="693eb-151">您可以使用管線傳送工作觸發程序至 **Disable-JobTrigger** 。</span><span class="sxs-lookup"><span data-stu-id="693eb-151">You can pipe job triggers to **Disable-JobTrigger** .</span></span>

## <span data-ttu-id="693eb-152">輸出</span><span class="sxs-lookup"><span data-stu-id="693eb-152">OUTPUTS</span></span>

### <span data-ttu-id="693eb-153">無</span><span class="sxs-lookup"><span data-stu-id="693eb-153">None</span></span>
<span data-ttu-id="693eb-154">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="693eb-154">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="693eb-155">注意</span><span class="sxs-lookup"><span data-stu-id="693eb-155">NOTES</span></span>

* <span data-ttu-id="693eb-156">**Disable-JobTrigger** 不會產生錯誤或警告 (若您停用已停用的工作觸發程序)。</span><span class="sxs-lookup"><span data-stu-id="693eb-156">**Disable-JobTrigger** does not generate errors or warnings if you disable a job trigger that is already disabled.</span></span>

## <span data-ttu-id="693eb-157">相關連結</span><span class="sxs-lookup"><span data-stu-id="693eb-157">RELATED LINKS</span></span>

[<span data-ttu-id="693eb-158">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="693eb-158">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="693eb-159">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="693eb-159">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="693eb-160">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="693eb-160">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="693eb-161">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="693eb-161">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="693eb-162">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="693eb-162">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="693eb-163">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="693eb-163">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="693eb-164">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="693eb-164">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="693eb-165">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="693eb-165">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="693eb-166">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="693eb-166">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="693eb-167">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="693eb-167">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="693eb-168">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="693eb-168">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="693eb-169">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="693eb-169">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="693eb-170">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="693eb-170">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="693eb-171">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="693eb-171">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="693eb-172">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="693eb-172">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="693eb-173">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="693eb-173">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
