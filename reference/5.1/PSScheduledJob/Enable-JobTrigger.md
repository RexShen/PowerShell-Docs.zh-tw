---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/enable-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-JobTrigger
ms.openlocfilehash: d08b55f4ba78af69608ac74c097fc6851164093b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203008"
---
# <span data-ttu-id="a3779-103">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="a3779-103">Enable-JobTrigger</span></span>

## <span data-ttu-id="a3779-104">概要</span><span class="sxs-lookup"><span data-stu-id="a3779-104">SYNOPSIS</span></span>
<span data-ttu-id="a3779-105">啟用排程工作的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="a3779-105">Enables the job triggers of scheduled jobs.</span></span>

## <span data-ttu-id="a3779-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a3779-106">SYNTAX</span></span>

```
Enable-JobTrigger [-InputObject] <ScheduledJobTrigger[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="a3779-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a3779-107">DESCRIPTION</span></span>
<span data-ttu-id="a3779-108">**Enable-JobTrigger** Cmdlet 會重新啟用排程工作的工作觸發程序，例如使用 Disable-JobTrigger Cmdlet 停用的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="a3779-108">The **Enable-JobTrigger** cmdlet re-enables job triggers of scheduled jobs, such as those that were disabled by using the Disable-JobTrigger cmdlet.</span></span>
<span data-ttu-id="a3779-109">已啟用與已重新啟用的工作觸發程序可立即啟動排程工作；您不需要重新啟動 Windows 或 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="a3779-109">Enabled and re-enabled job triggers can start scheduled jobs immediately; there is no need to restart Windows or Windows PowerShell.</span></span>

<span data-ttu-id="a3779-110">若要使用此 Cmdlet，請使用 Get-JobTrigger Cmdlet 來取得工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="a3779-110">To use this cmdlet, use the  Get-JobTrigger cmdlet to get the job triggers.</span></span>
<span data-ttu-id="a3779-111">接著，使用管線將工作觸發程序傳送至 **Enable-JobTrigger** 或使用其 *InputObject* 參數。</span><span class="sxs-lookup"><span data-stu-id="a3779-111">Then pipe the job triggers to **Enable-JobTrigger** or use its *InputObject* parameter.</span></span>

<span data-ttu-id="a3779-112">為啟用工作觸發程序， **Enable-JobTrigger** Cmdlet 會將工作觸發程序的 Enabled 屬性設為 $True。</span><span class="sxs-lookup"><span data-stu-id="a3779-112">To enable a job trigger, the **Enable-JobTrigger** cmdlet sets the Enabled property of the job trigger to $True.</span></span>

<span data-ttu-id="a3779-113">**Enable-ScheduledJob** 為 Windows PowerShell 內含之 **PSScheduledJob** 模組中的其中一個工作排程 Cmdlet 集合。</span><span class="sxs-lookup"><span data-stu-id="a3779-113">**Enable-ScheduledJob** is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="a3779-114">如需排程工作的詳細資訊，請參閱 PSScheduledJob 模組中的「關於」主題。</span><span class="sxs-lookup"><span data-stu-id="a3779-114">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="a3779-115">匯入 PSScheduledJob 模組，然後輸入：`Get-Help about_Scheduled*`，或參閱 about_Scheduled_Jobs。</span><span class="sxs-lookup"><span data-stu-id="a3779-115">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="a3779-116">此 Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="a3779-116">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="a3779-117">範例</span><span class="sxs-lookup"><span data-stu-id="a3779-117">EXAMPLES</span></span>

### <span data-ttu-id="a3779-118">範例 1︰啟用工作觸發程序</span><span class="sxs-lookup"><span data-stu-id="a3779-118">Example 1: Enable a job trigger</span></span>

```
PS C:\> Get-JobTrigger -Name Backup-Archives -TriggerID 1 | Enable-JobTrigger
```

<span data-ttu-id="a3779-119">此命令會啟用本機電腦上 Backup-Archives 排程工作的第一個觸發程序 (識別碼=1)。</span><span class="sxs-lookup"><span data-stu-id="a3779-119">This command enables the first trigger (ID=1) of the Backup-Archives scheduled job on the local computer.</span></span>

<span data-ttu-id="a3779-120">此命令會使用 Get-JobTrigger Cmdlet 來取得工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="a3779-120">The command uses the Get-JobTrigger cmdlet to get the job trigger.</span></span>
<span data-ttu-id="a3779-121">管線運算子會傳送工作觸發程序至 **Enable-JobTrigger** Cmdlet，此 Cmdlet 會將它啟用。</span><span class="sxs-lookup"><span data-stu-id="a3779-121">A pipeline operator sends the job trigger to the **Enable-JobTrigger** cmdlet, which enables it.</span></span>

### <span data-ttu-id="a3779-122">範例 2︰啟用所有工作觸發程序</span><span class="sxs-lookup"><span data-stu-id="a3779-122">Example 2: Enable all job triggers</span></span>

```
PS C:\> Get-ScheduledJob | Get-JobTrigger | Enable-JobTrigger
```

<span data-ttu-id="a3779-123">此命令會使用 Get-ScheduledJob Cmdlet 來取得本機電腦上排程的工作。</span><span class="sxs-lookup"><span data-stu-id="a3779-123">The command uses the Get-ScheduledJob cmdlet to get  the scheduled jobs on the local computer.</span></span>
<span data-ttu-id="a3779-124">管線運算子 (|) 會將排程工作傳送至 Get-JobTrigger Cmdlet，此 Cmdlet 會取得排程工作的所有工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="a3779-124">A pipeline operator (|) sends the scheduled jobs to the Get-JobTrigger cmdlet, which gets all job triggers of the scheduled jobs.</span></span>
<span data-ttu-id="a3779-125">另一個管線運算子會傳送工作觸發程序至 **Enable-JobTrigger** Cmdlet，此 Cmdlet 會將它們啟用。</span><span class="sxs-lookup"><span data-stu-id="a3779-125">Another pipeline operator sends the job triggers to the **Enable-JobTrigger** cmdlet, which enables them.</span></span>

### <span data-ttu-id="a3779-126">範例 3：啟用遠端電腦上排程工作的工作觸發程序</span><span class="sxs-lookup"><span data-stu-id="a3779-126">Example 3: Enable the job trigger of a scheduled job on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName Server01 {Get-JobTrigger -Name DeployPackage | Where-Object {$_.Frequency -eq "AtLogon"} | Enable-JobTrigger}
```

<span data-ttu-id="a3779-127">此命令會重新啟用 Server01 遠端電腦上 DeployPackage 排程工作的 AtLogon 工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="a3779-127">This command re-enables the AtLogon job triggers on the DeployPackage scheduled job on the Server01 remote computer.</span></span>

<span data-ttu-id="a3779-128">此命令會使用 Invoke-Command Cmdlet，在 Server01 電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="a3779-128">The command uses the Invoke-Command cmdlet to run the commands on the Server01 computer.</span></span>
<span data-ttu-id="a3779-129">遠端命令會使用 Get-JobTrigger Cmdlet 來取得 DeployPackage 排程工作的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="a3779-129">The remote command uses the Get-JobTrigger cmdlet to get the job triggers of the DeployPackage scheduled job.</span></span>
<span data-ttu-id="a3779-130">管線運算子會將工作觸發程序傳送至 Where-Object Cmdlet，這個 Cmdlet 只會傳回 AtLogon 工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="a3779-130">A pipeline operator sends the job triggers to the Where-Object cmdlet which returns only AtLogon job triggers.</span></span>
<span data-ttu-id="a3779-131">管線運算子會將 AtLogon 工作觸發程序傳送至 **Enable-JobTrigger** Cmdlet，此 Cmdlet 會啟用它們。</span><span class="sxs-lookup"><span data-stu-id="a3779-131">A pipeline operator sends the AtLogon job triggers to the **Enable-JobTrigger** cmdlet, which enables them.</span></span>

### <span data-ttu-id="a3779-132">範例 4︰顯示已停用的工作觸發程序</span><span class="sxs-lookup"><span data-stu-id="a3779-132">Example 4: Display disabled job triggers</span></span>

```
PS C:\> Get-ScheduledJob | Get-JobTrigger | where {!$_.Enabled} | Format-Table Id, Frequency, At, DaysOfWeek, Enabled, @{Label="JobName";Expression={$_.JobDefinition.Name}}
Id Frequency At                     DaysOfWeek Enabled JobName
-- --------- --                     ---------- ------- -------
 1    Weekly 9/28/2011 3:00:00 AM   {Monday}   False   Backup-Archive
 2    Daily  9/29/2011 1:00:00 AM              False   Backup-Archive
 1    Weekly 10/20/2011 11:00:00 PM {Friday}   False   Inventory
 1    Weekly 11/2/2011 2:00:00 PM   {Monday}   False   Inventory
```

<span data-ttu-id="a3779-133">此命令會以表格方式顯示所有排程工作的所有已停用工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="a3779-133">This command displays all disabled job triggers of all scheduled jobs in a table.</span></span>
<span data-ttu-id="a3779-134">您可以使用像這樣的命令來探索可能需要重新啟用的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="a3779-134">You can use a command like this one to discover job triggers that might need to be enabled.</span></span>

<span data-ttu-id="a3779-135">此命令會使用 Get-ScheduledJob Cmdlet 來取得本機電腦上的排程工作。</span><span class="sxs-lookup"><span data-stu-id="a3779-135">The command uses the Get-ScheduledJob cmdlet to get the scheduled jobs on the local computer.</span></span>
<span data-ttu-id="a3779-136">管線運算子 (|) 會將排程工作傳送至 Get-JobTrigger Cmdlet，此 Cmdlet 會取得排程工作的所有工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="a3779-136">A pipeline operator (|) sends the scheduled jobs to the Get-JobTrigger cmdlet, which gets all job triggers of the scheduled jobs.</span></span>
<span data-ttu-id="a3779-137">另一個管線運算子會將工作觸發程序傳送至 Where-Object Cmdlet，此 Cmdlet 只會傳回已停用的工作觸發程序，也就是，工作觸發程序的 Enabled 屬性值不是 (!) true。</span><span class="sxs-lookup"><span data-stu-id="a3779-137">Another pipeline operator sends the job triggers to the Where-Object cmdlet, which returns only job triggers that are disabled, that is, where the value of the Enabled property of the job trigger is not (!) true.</span></span>

<span data-ttu-id="a3779-138">另一個管線運算子會將已停用的工作觸發程序傳送至 Format-Table Cmdlet，這個 Cmdlet 會顯示資料表中選取的工作觸發程序屬性。</span><span class="sxs-lookup"><span data-stu-id="a3779-138">Another pipeline operator sends the disabled job triggers to the Format-Table cmdlet, which displays the selected properties of the job triggers in a table.</span></span>
<span data-ttu-id="a3779-139">這些屬性包含新的 JobName 屬性，此屬性會顯示工作觸發程序 JobDefinition 屬性中排程工作的名稱。</span><span class="sxs-lookup"><span data-stu-id="a3779-139">The properties include a new JobName property that displays the name of the scheduled job in the JobDefinition property of the job trigger.</span></span>

## <span data-ttu-id="a3779-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a3779-140">PARAMETERS</span></span>

### <span data-ttu-id="a3779-141">-InputObject</span><span class="sxs-lookup"><span data-stu-id="a3779-141">-InputObject</span></span>
<span data-ttu-id="a3779-142">指定要啟用的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="a3779-142">Specifies the job trigger to enable.</span></span>
<span data-ttu-id="a3779-143">輸入包含 **>scheduledjobtrigger** 物件的變數，或輸入可取得 **>scheduledjobtrigger** 物件的命令或運算式，例如 Get-JobTrigger 命令。</span><span class="sxs-lookup"><span data-stu-id="a3779-143">Enter a variable that contains **ScheduledJobTrigger** objects or type a command or expression that gets **ScheduledJobTrigger** objects, such as a Get-JobTrigger command.</span></span>
<span data-ttu-id="a3779-144">您也可以使用管線將 **ScheduledJobTrigger** 物件傳遞給 **Enable-JobTrigger** 。</span><span class="sxs-lookup"><span data-stu-id="a3779-144">You can also pipe a **ScheduledJobTrigger** object to **Enable-JobTrigger** .</span></span>

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

### <span data-ttu-id="a3779-145">-PassThru</span><span class="sxs-lookup"><span data-stu-id="a3779-145">-PassThru</span></span>
<span data-ttu-id="a3779-146">傳回代表您正在使用之項目的物件。</span><span class="sxs-lookup"><span data-stu-id="a3779-146">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="a3779-147">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="a3779-147">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="a3779-148">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a3779-148">-Confirm</span></span>
<span data-ttu-id="a3779-149">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="a3779-149">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a3779-150">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a3779-150">-WhatIf</span></span>
<span data-ttu-id="a3779-151">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="a3779-151">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="a3779-152">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="a3779-152">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a3779-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a3779-153">CommonParameters</span></span>
<span data-ttu-id="a3779-154">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="a3779-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a3779-155">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="a3779-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a3779-156">輸入</span><span class="sxs-lookup"><span data-stu-id="a3779-156">INPUTS</span></span>

### <span data-ttu-id="a3779-157">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span><span class="sxs-lookup"><span data-stu-id="a3779-157">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span></span>
<span data-ttu-id="a3779-158">您可以使用管線將工作觸發程序傳送至 **Enable-JobTrigger** 。</span><span class="sxs-lookup"><span data-stu-id="a3779-158">You can pipe job triggers to **Enable-JobTrigger** .</span></span>

## <span data-ttu-id="a3779-159">輸出</span><span class="sxs-lookup"><span data-stu-id="a3779-159">OUTPUTS</span></span>

### <span data-ttu-id="a3779-160">無</span><span class="sxs-lookup"><span data-stu-id="a3779-160">None</span></span>
<span data-ttu-id="a3779-161">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="a3779-161">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="a3779-162">注意</span><span class="sxs-lookup"><span data-stu-id="a3779-162">NOTES</span></span>

* <span data-ttu-id="a3779-163">若您啟用已經啟用的工作觸發程序， **Enable-JobTrigger** 就不會產生錯誤或警告。</span><span class="sxs-lookup"><span data-stu-id="a3779-163">**Enable-JobTrigger** does not generate errors or warnings if you enable a job trigger that is already enabled.</span></span>

## <span data-ttu-id="a3779-164">相關連結</span><span class="sxs-lookup"><span data-stu-id="a3779-164">RELATED LINKS</span></span>

[<span data-ttu-id="a3779-165">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="a3779-165">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="a3779-166">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="a3779-166">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="a3779-167">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="a3779-167">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="a3779-168">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="a3779-168">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="a3779-169">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="a3779-169">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="a3779-170">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="a3779-170">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="a3779-171">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="a3779-171">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="a3779-172">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="a3779-172">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="a3779-173">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="a3779-173">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="a3779-174">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="a3779-174">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="a3779-175">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="a3779-175">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="a3779-176">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="a3779-176">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="a3779-177">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="a3779-177">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="a3779-178">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="a3779-178">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="a3779-179">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="a3779-179">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="a3779-180">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="a3779-180">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
