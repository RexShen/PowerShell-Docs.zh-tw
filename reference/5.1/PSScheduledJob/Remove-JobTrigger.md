---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/remove-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-JobTrigger
ms.openlocfilehash: adcd74361b1a045a57c7db2f15996f4ea53d6d5b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202992"
---
# <span data-ttu-id="4ed84-103">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="4ed84-103">Remove-JobTrigger</span></span>

## <span data-ttu-id="4ed84-104">概要</span><span class="sxs-lookup"><span data-stu-id="4ed84-104">SYNOPSIS</span></span>
<span data-ttu-id="4ed84-105">從排程工作刪除工作觸發程式。</span><span class="sxs-lookup"><span data-stu-id="4ed84-105">Delete job triggers from scheduled jobs.</span></span>

## <span data-ttu-id="4ed84-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4ed84-106">SYNTAX</span></span>

### <span data-ttu-id="4ed84-107">JobDefinition (預設值)</span><span class="sxs-lookup"><span data-stu-id="4ed84-107">JobDefinition (Default)</span></span>

```
Remove-JobTrigger [-TriggerId <Int32[]>] [-InputObject] <ScheduledJobDefinition[]> [<CommonParameters>]
```

### <span data-ttu-id="4ed84-108">JobDefinitionId</span><span class="sxs-lookup"><span data-stu-id="4ed84-108">JobDefinitionId</span></span>

```
Remove-JobTrigger [-TriggerId <Int32[]>] [-Id] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="4ed84-109">JobDefinitionName</span><span class="sxs-lookup"><span data-stu-id="4ed84-109">JobDefinitionName</span></span>

```
Remove-JobTrigger [-TriggerId <Int32[]>] [-Name] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="4ed84-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="4ed84-110">DESCRIPTION</span></span>
<span data-ttu-id="4ed84-111">**Enable-jobtrigger 指令程式** 會從排程工作刪除工作觸發程式。</span><span class="sxs-lookup"><span data-stu-id="4ed84-111">The **Remove-JobTrigger** cmdlet deletes job triggers from scheduled jobs.</span></span>

<span data-ttu-id="4ed84-112">工作觸發程式會定義用於啟動排程工作的週期性排程或條件。</span><span class="sxs-lookup"><span data-stu-id="4ed84-112">A job trigger defines a recurring schedule or conditions for starting a scheduled job.</span></span>
<span data-ttu-id="4ed84-113">若要管理工作觸發程序，請使用 New-JobTrigger、Add-JobTrigger、Set-JobTrigger 及 Set-ScheduledJob Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4ed84-113">To manage job triggers, use the New-JobTrigger, Add-JobTrigger, Set-JobTrigger, and Set-ScheduledJob cmdlets.</span></span>

<span data-ttu-id="4ed84-114">使用 *Remove-JobTrigger* 的 *Name* 、 *ID* 或 **InputObject** 參數來識別要從中移除觸發程序的排程工作。</span><span class="sxs-lookup"><span data-stu-id="4ed84-114">Use the *Name* , *ID* , or *InputObject* parameters of **Remove-JobTrigger** to identify the scheduled jobs from which the triggers are removed.</span></span>
<span data-ttu-id="4ed84-115">使用 *TriggerID* 參數來識別要刪除的工作觸發程式。</span><span class="sxs-lookup"><span data-stu-id="4ed84-115">Use the *TriggerID* parameter to identify the job triggers to delete.</span></span>
<span data-ttu-id="4ed84-116">根據預設值， **Remove-JobTrigger** 會刪除排程工作的所有工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="4ed84-116">By default, **Remove-JobTrigger** deletes all job triggers of a scheduled job.</span></span>

<span data-ttu-id="4ed84-117">**Remove-JobTrigger** 為 Windows PowerShell 所包含 PSScheduledJob 模組中的其中一個工作排程 Cmdlet 集合。</span><span class="sxs-lookup"><span data-stu-id="4ed84-117">**Remove-JobTrigger** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="4ed84-118">如需排程工作的詳細資訊，請參閱 PSScheduledJob 模組中的「關於」主題。</span><span class="sxs-lookup"><span data-stu-id="4ed84-118">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="4ed84-119">匯入 PSScheduledJob 模組，然後輸入：`Get-Help about_Scheduled*`，或參閱 about_Scheduled_Jobs。</span><span class="sxs-lookup"><span data-stu-id="4ed84-119">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="4ed84-120">此 Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="4ed84-120">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="4ed84-121">範例</span><span class="sxs-lookup"><span data-stu-id="4ed84-121">EXAMPLES</span></span>

### <span data-ttu-id="4ed84-122">範例 1：刪除所有工作觸發程序</span><span class="sxs-lookup"><span data-stu-id="4ed84-122">Example 1: Delete all job triggers</span></span>

```
PS C:\> Remove-JobTrigger -Name "Test*"
```

<span data-ttu-id="4ed84-123">此命令會從名稱開頭為 Test 的排程工作中刪除所有工作觸發程式。</span><span class="sxs-lookup"><span data-stu-id="4ed84-123">This command deletes all job triggers from scheduled job that have names that begin with Test.</span></span>

### <span data-ttu-id="4ed84-124">範例 2：刪除選取的工作觸發程序</span><span class="sxs-lookup"><span data-stu-id="4ed84-124">Example 2: Delete selected job triggers</span></span>

```
PS C:\> Remove-JobTrigger -Name "BackupArchive" -TriggerID 3
```

<span data-ttu-id="4ed84-125">此命令只會刪除 BackupArchive 排程工作中的第三個觸發程序 (識別碼 = 3)。</span><span class="sxs-lookup"><span data-stu-id="4ed84-125">This command deletes only the third trigger (ID = 3) from the BackupArchive scheduled job.</span></span>

### <span data-ttu-id="4ed84-126">範例 3：刪除所有排程工作中的 AtStartup 工作觸發程序</span><span class="sxs-lookup"><span data-stu-id="4ed84-126">Example 3: Delete AtStartup job triggers from all scheduled jobs</span></span>

```
PS C:\> function Delete-AtStartup
{
    Get-ScheduledJob | Get-JobTrigger | Where-Object {$_.Frequency -eq "AtStartup"} | ForEach-Object { Remove-JobTrigger -InputObject $_.JobDefinition -TriggerID $_.ID}
}
```

<span data-ttu-id="4ed84-127">此功能會刪除本機電腦上所有工作中的所有 AtStartup 工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="4ed84-127">This function deletes all AtStartup job triggers from all jobs on the local computer.</span></span>
<span data-ttu-id="4ed84-128">若要使用函數，請在您的會話中執行函數，然後輸入 `Delete-AtStartup` 。</span><span class="sxs-lookup"><span data-stu-id="4ed84-128">To use the function, run the function in your session and then type `Delete-AtStartup`.</span></span>

<span data-ttu-id="4ed84-129">Delete-AtStartup 功能包含單一命令。</span><span class="sxs-lookup"><span data-stu-id="4ed84-129">The Delete-AtStartup function contains a single command.</span></span>
<span data-ttu-id="4ed84-130">此命令會使用 Get-ScheduledJob Cmdlet 來取得本機電腦上的排程工作。</span><span class="sxs-lookup"><span data-stu-id="4ed84-130">The command uses the Get-ScheduledJob cmdlet to get the scheduled jobs on the local computer.</span></span>
<span data-ttu-id="4ed84-131">管線運算子 (|) 會將排程的工作傳送至 Get-JobTrigger Cmdlet，此 Cmdlet 會取得每個排程工作的所有工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="4ed84-131">A pipeline operator (|) sends the scheduled jobs to the Get-JobTrigger cmdlet, which gets all of the job triggers from each of the scheduled jobs.</span></span>
<span data-ttu-id="4ed84-132">管線運算子會將工作觸發程式傳送至 Where-Object Cmdlet，此 Cmdlet 會選取工作觸發程式之 Frequency 屬性值等於 AtStartup 的工作觸發程式。</span><span class="sxs-lookup"><span data-stu-id="4ed84-132">A pipeline operator sends the job triggers to the Where-Object cmdlet, which selects job triggers where the value of the Frequency property of the job trigger equals AtStartup.</span></span>

<span data-ttu-id="4ed84-133">**Enable-jobtrigger** 物件具有 **JobDefinition** 屬性，其中包含其所觸發的排程工作。</span><span class="sxs-lookup"><span data-stu-id="4ed84-133">**JobTrigger** objects have a **JobDefinition** property that contains the scheduled job that they trigger.</span></span>
<span data-ttu-id="4ed84-134">命令的其餘部分使用該實用功能。</span><span class="sxs-lookup"><span data-stu-id="4ed84-134">The remainder of the command uses that valuable feature.</span></span>

<span data-ttu-id="4ed84-135">管線運算子會將 AtStartup 工作觸發程序傳送至 ForEach-Object Cmdlet，它會在每個 AtStartup 觸發程序上執行 **Remove-JobTrigger** 命令。</span><span class="sxs-lookup"><span data-stu-id="4ed84-135">A pipeline operator sends the AtStartup job triggers to the ForEach-Object cmdlet, which runs a **Remove-JobTrigger** command on each AtStartup trigger.</span></span>
<span data-ttu-id="4ed84-136">**Remove-JobTrigger** 的 *InputObject* 參數值是工作觸發程序之 JobDefinition 屬性中的排程工作。</span><span class="sxs-lookup"><span data-stu-id="4ed84-136">The value of the *InputObject* parameter of **Remove-JobTrigger** is the scheduled job in the JobDefinition property of the job trigger.</span></span>
<span data-ttu-id="4ed84-137">*TriggerID* 參數的值是工作觸發程序之 ID 屬性中的識別碼。</span><span class="sxs-lookup"><span data-stu-id="4ed84-137">The value of the *TriggerID* parameter is the identifier in the ID property of the job trigger.</span></span>

### <span data-ttu-id="4ed84-138">範例 4：刪除遠端排程工作的工作觸發程序</span><span class="sxs-lookup"><span data-stu-id="4ed84-138">Example 4: Delete a job trigger from a remote scheduled job</span></span>

```
PS C:\> Invoke-Command -ComputerName "Server01" { Remove-JobTrigger -ID 38 -TriggerID 1 }
```

<span data-ttu-id="4ed84-139">此命令會刪除 Server01 電腦上 Inventory 工作的第一個工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="4ed84-139">This command deletes the first job trigger from the Inventory job on the Server01 computer.</span></span>

<span data-ttu-id="4ed84-140">此命令會使用 **Invoke 命令** Cmdlet 在 Server01 電腦上執行 **enable-jobtrigger** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4ed84-140">The command uses the **Invoke-Command** cmdlet to run the **Remove-JobTrigger** cmdlet on the Server01 computer.</span></span>
<span data-ttu-id="4ed84-141">Enable-jobtrigger Cmdlet 會使用 *ID* 參數來識別清查排程工作，並使用 *TriggerID* 參數來指定第一個觸發 **程式** 。</span><span class="sxs-lookup"><span data-stu-id="4ed84-141">The **Remove-JobTrigger** cmdlet uses the *ID* parameter to identify the Inventory scheduled job and the *TriggerID* parameter to specify the first trigger.</span></span>
<span data-ttu-id="4ed84-142">當多個排程工作具有相同或類似的名稱時， *ID* 參數特別有用。</span><span class="sxs-lookup"><span data-stu-id="4ed84-142">The *ID* parameter is especially useful when multiple scheduled jobs have the same or similar names.</span></span>

## <span data-ttu-id="4ed84-143">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4ed84-143">PARAMETERS</span></span>

### <span data-ttu-id="4ed84-144">-Id</span><span class="sxs-lookup"><span data-stu-id="4ed84-144">-Id</span></span>
<span data-ttu-id="4ed84-145">指定排程工作的識別碼。</span><span class="sxs-lookup"><span data-stu-id="4ed84-145">Specifies the identification numbers of the scheduled jobs.</span></span>
<span data-ttu-id="4ed84-146">**Remove-JobTrigger** 會將工作觸發程序從指定的排程工作刪除。</span><span class="sxs-lookup"><span data-stu-id="4ed84-146">**Remove-JobTrigger** deletes job triggers from the specified scheduled jobs.</span></span>

<span data-ttu-id="4ed84-147">若要取得本機電腦或遠端電腦上排程工作的識別碼，請使用 Get-ScheduledJob Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4ed84-147">To get the identification number of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: JobDefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4ed84-148">-InputObject</span><span class="sxs-lookup"><span data-stu-id="4ed84-148">-InputObject</span></span>
<span data-ttu-id="4ed84-149">指定排程工作。</span><span class="sxs-lookup"><span data-stu-id="4ed84-149">Specifies the scheduled jobs.</span></span>
<span data-ttu-id="4ed84-150">輸入包含 **register-scheduledjob** 物件的變數，或輸入可取得 **register-scheduledjob** 物件的命令或運算式，例如 Get-ScheduledJob 命令。</span><span class="sxs-lookup"><span data-stu-id="4ed84-150">Enter a variable that contains **ScheduledJob** objects or type a command or expression that gets **ScheduledJob** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="4ed84-151">您也可以使用管線將 **ScheduledJob** 物件傳送至 **Remove-JobTrigger** 。</span><span class="sxs-lookup"><span data-stu-id="4ed84-151">You can also pipe **ScheduledJob** objects to **Remove-JobTrigger** .</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition[]
Parameter Sets: JobDefinition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4ed84-152">-Name</span><span class="sxs-lookup"><span data-stu-id="4ed84-152">-Name</span></span>
<span data-ttu-id="4ed84-153">指定排程工作的名稱。</span><span class="sxs-lookup"><span data-stu-id="4ed84-153">Specifies the names of the scheduled jobs.</span></span>
<span data-ttu-id="4ed84-154">**Remove-JobTrigger** 會將工作觸發程序從指定的排程工作刪除。</span><span class="sxs-lookup"><span data-stu-id="4ed84-154">**Remove-JobTrigger** deletes the job triggers from the specified scheduled jobs.</span></span>
<span data-ttu-id="4ed84-155">支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="4ed84-155">Wildcards are supported.</span></span>

<span data-ttu-id="4ed84-156">若要取得本機電腦或遠端電腦上排程工作的名稱，請使用 Get-ScheduledJob Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4ed84-156">To get the names of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: JobDefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4ed84-157">-TriggerId</span><span class="sxs-lookup"><span data-stu-id="4ed84-157">-TriggerId</span></span>
<span data-ttu-id="4ed84-158">只刪除指定的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="4ed84-158">Deletes only the specified job triggers.</span></span>
<span data-ttu-id="4ed84-159">根據預設值， **Remove-JobTrigger** 會刪除排程工作的所有觸發程序。</span><span class="sxs-lookup"><span data-stu-id="4ed84-159">By default, **Remove-JobTrigger** deletes all triggers from the scheduled jobs.</span></span>
<span data-ttu-id="4ed84-160">當排程工作有多個工作觸發程序時，請使用此參數。</span><span class="sxs-lookup"><span data-stu-id="4ed84-160">Use this parameter when the scheduled jobs have multiple job triggers.</span></span>

<span data-ttu-id="4ed84-161">輸入排程工作之一或多個工作觸發程序的觸發程序識別碼。</span><span class="sxs-lookup"><span data-stu-id="4ed84-161">Enter the trigger IDs of one or more job triggers of a scheduled job.</span></span>
<span data-ttu-id="4ed84-162">如果您指定多個排程工作，Enable-jobtrigger 會刪除所有排程工作中具有指定識別碼的工作觸發 **程式** 。</span><span class="sxs-lookup"><span data-stu-id="4ed84-162">If you specify multiple scheduled jobs, **Remove-JobTrigger** deletes the job trigger with the specified ID from all scheduled jobs.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4ed84-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4ed84-163">CommonParameters</span></span>
<span data-ttu-id="4ed84-164">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="4ed84-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4ed84-165">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="4ed84-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4ed84-166">輸入</span><span class="sxs-lookup"><span data-stu-id="4ed84-166">INPUTS</span></span>

### <span data-ttu-id="4ed84-167">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="4ed84-167">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="4ed84-168">您可以使用管線傳送排程工作至 **Remove-JobTrigger** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4ed84-168">You can pipe scheduled jobs to the **Remove-JobTrigger** cmdlet.</span></span>

## <span data-ttu-id="4ed84-169">輸出</span><span class="sxs-lookup"><span data-stu-id="4ed84-169">OUTPUTS</span></span>

### <span data-ttu-id="4ed84-170">無</span><span class="sxs-lookup"><span data-stu-id="4ed84-170">None</span></span>
<span data-ttu-id="4ed84-171">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="4ed84-171">The cmdlet does not generate any output.</span></span>

## <span data-ttu-id="4ed84-172">注意</span><span class="sxs-lookup"><span data-stu-id="4ed84-172">NOTES</span></span>

## <span data-ttu-id="4ed84-173">相關連結</span><span class="sxs-lookup"><span data-stu-id="4ed84-173">RELATED LINKS</span></span>

[<span data-ttu-id="4ed84-174">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="4ed84-174">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="4ed84-175">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="4ed84-175">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="4ed84-176">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="4ed84-176">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="4ed84-177">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="4ed84-177">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="4ed84-178">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="4ed84-178">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="4ed84-179">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="4ed84-179">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="4ed84-180">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="4ed84-180">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="4ed84-181">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="4ed84-181">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="4ed84-182">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="4ed84-182">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="4ed84-183">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="4ed84-183">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="4ed84-184">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="4ed84-184">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="4ed84-185">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="4ed84-185">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="4ed84-186">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="4ed84-186">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="4ed84-187">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="4ed84-187">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="4ed84-188">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="4ed84-188">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="4ed84-189">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="4ed84-189">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
