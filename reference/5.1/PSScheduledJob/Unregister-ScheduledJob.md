---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/unregister-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-ScheduledJob
ms.openlocfilehash: 0c0b55513bcfdcebdcd5d8a6f17968a4a45e2839
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202972"
---
# <span data-ttu-id="95e93-103">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="95e93-103">Unregister-ScheduledJob</span></span>

## <span data-ttu-id="95e93-104">概要</span><span class="sxs-lookup"><span data-stu-id="95e93-104">SYNOPSIS</span></span>
<span data-ttu-id="95e93-105">刪除本機電腦上的排程工作。</span><span class="sxs-lookup"><span data-stu-id="95e93-105">Deletes scheduled jobs on the local computer.</span></span>

## <span data-ttu-id="95e93-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="95e93-106">SYNTAX</span></span>

### <span data-ttu-id="95e93-107">Definition (預設值)</span><span class="sxs-lookup"><span data-stu-id="95e93-107">Definition (Default)</span></span>

```
Unregister-ScheduledJob [-InputObject] <ScheduledJobDefinition[]> [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="95e93-108">DefinitionId</span><span class="sxs-lookup"><span data-stu-id="95e93-108">DefinitionId</span></span>

```
Unregister-ScheduledJob [-Id] <Int32[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="95e93-109">DefinitionName</span><span class="sxs-lookup"><span data-stu-id="95e93-109">DefinitionName</span></span>

```
Unregister-ScheduledJob [-Name] <String[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="95e93-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="95e93-110">DESCRIPTION</span></span>
<span data-ttu-id="95e93-111">**Unregister-ScheduledJob** Cmdlet 會刪除本機電腦上的排程工作。</span><span class="sxs-lookup"><span data-stu-id="95e93-111">The **Unregister-ScheduledJob** cmdlet deletes scheduled jobs from the local computer.</span></span>

<span data-ttu-id="95e93-112">當它刪除或取消註冊排程工作時， **取消註冊-register-scheduledjob** 會刪除 $home \appdata\local\microsoft\windows\powershell\scheduledjobs directory) 中 (排程工作的目錄，其中包含定義排程工作的 XML 檔案、工作執行歷程記錄，以及所有工作結果。</span><span class="sxs-lookup"><span data-stu-id="95e93-112">When it deletes or unregisters a scheduled job, **Unregister-ScheduledJob** deletes the directory for the scheduled job (in the $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs directory), which contains the XML file that defines the scheduled job, the job execution history, and all job results.</span></span>
<span data-ttu-id="95e93-113">此動作也會將工作從 [工作排程器] 刪除。</span><span class="sxs-lookup"><span data-stu-id="95e93-113">This action also deletes the job from Task Scheduler.</span></span>

<span data-ttu-id="95e93-114">**Unregister-ScheduledJob** 只會刪除使用 Register-ScheduledJob Cmdlet 所建立的排程工作。</span><span class="sxs-lookup"><span data-stu-id="95e93-114">**Unregister-ScheduledJob** deletes only the scheduled jobs that are created by using the Register-ScheduledJob cmdlet.</span></span>
<span data-ttu-id="95e93-115">它不會刪除在 [工作排程器] 中建立的排程工作。</span><span class="sxs-lookup"><span data-stu-id="95e93-115">It does not delete scheduled jobs that are created in Task Scheduler.</span></span>

<span data-ttu-id="95e93-116">您可以使用 **register-scheduledjob** 的參數，依識別碼或名稱刪除排程工作，或使用管線將排程工作從 Get-ScheduledJob 傳送至 **取消註冊-register-scheduledjob** 。</span><span class="sxs-lookup"><span data-stu-id="95e93-116">You can use the parameters of **Unregister-ScheduledJob** to delete scheduled jobs by ID or name, or pipe scheduled jobs from Get-ScheduledJob to **Unregister-ScheduledJob** .</span></span>

<span data-ttu-id="95e93-117">**Unregister-ScheduledJob** 為 Windows PowerShell 內含之 PSScheduledJob 模組中其中一個工作排程 Cmdlet 的集合。</span><span class="sxs-lookup"><span data-stu-id="95e93-117">**Unregister-ScheduledJob** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="95e93-118">如需排程工作的詳細資訊，請參閱 PSScheduledJob 模組中的「關於」主題。</span><span class="sxs-lookup"><span data-stu-id="95e93-118">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="95e93-119">匯入 PSScheduledJob 模組，然後輸入：`Get-Help about_Scheduled*`，或參閱 about_Scheduled_Jobs。</span><span class="sxs-lookup"><span data-stu-id="95e93-119">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="95e93-120">此 Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="95e93-120">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="95e93-121">範例</span><span class="sxs-lookup"><span data-stu-id="95e93-121">EXAMPLES</span></span>

### <span data-ttu-id="95e93-122">範例 1：刪除排程工作</span><span class="sxs-lookup"><span data-stu-id="95e93-122">Example 1: Delete a scheduled job</span></span>

```
PS C:\> Unregister-ScheduledJob TestJob
```

<span data-ttu-id="95e93-123">此命令會刪除本機電腦上的 TestJob 排程工作。</span><span class="sxs-lookup"><span data-stu-id="95e93-123">This command deletes the TestJob scheduled job on the local computer.</span></span>

### <span data-ttu-id="95e93-124">範例 2：刪除所有排程工作</span><span class="sxs-lookup"><span data-stu-id="95e93-124">Example 2: Delete all scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob | Unregister-ScheduledJob -Force
PS C:\> Unregister-ScheduledJob -Name "*" -Force
```

<span data-ttu-id="95e93-125">此範例顯示兩個不同的命令，這些命令會刪除本機電腦上的所有排程工作。</span><span class="sxs-lookup"><span data-stu-id="95e93-125">This example shows two different commands that delete all scheduled jobs on the local computer.</span></span>

<span data-ttu-id="95e93-126">第一個命令會使用 Get-ScheduledJob Cmdlet 來取得電腦上的所有排程工作。</span><span class="sxs-lookup"><span data-stu-id="95e93-126">The first command uses the Get-ScheduledJob cmdlet to get all scheduled jobs on the local computer.</span></span>
<span data-ttu-id="95e93-127">管線運算子 (|) 會傳送排程工作至 **Unregister-ScheduleJob** ，此 Cmdlet 會將它們刪除。</span><span class="sxs-lookup"><span data-stu-id="95e93-127">A pipeline operator (|) sends the scheduled jobs to **Unregister-ScheduleJob** , which deletes them.</span></span>

<span data-ttu-id="95e93-128">第二個命令使用 *Unregister-ScheduledJob* 的 **Name** 參數搭配全部 (\*) 的值來刪除所有排程工作。</span><span class="sxs-lookup"><span data-stu-id="95e93-128">The second command uses the *Name* parameter of **Unregister-ScheduledJob** with a value of all (\*) to delete all scheduled jobs.</span></span>

<span data-ttu-id="95e93-129">這兩個命令都使用 *Force* 參數，此參數會刪除排程工作，即使工作的執行個體在執行中。</span><span class="sxs-lookup"><span data-stu-id="95e93-129">Both commands use the *Force* parameter, which deletes a scheduled job even if an instance of the job is running.</span></span>

### <span data-ttu-id="95e93-130">範例 3：刪除遠端電腦上的排程工作</span><span class="sxs-lookup"><span data-stu-id="95e93-130">Example 3: Delete a scheduled job on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName "Server01" { Unregister-ScheduledJob -Name "Test*"}
```

<span data-ttu-id="95e93-131">此命令會刪除 Server01 遠端電腦上名稱開頭為 Test 的排程工作。</span><span class="sxs-lookup"><span data-stu-id="95e93-131">This command deletes scheduled jobs with names that begin with Test on the Server01 remote computer.</span></span>
<span data-ttu-id="95e93-132">此命令會使用 Invoke-Command Cmdlet，在 Server02 電腦上執行 **Unregister-ScheduledJob** 命令。</span><span class="sxs-lookup"><span data-stu-id="95e93-132">The command uses the Invoke-Command cmdlet to run the **Unregister-ScheduledJob** command on the Server02 computer.</span></span>

## <span data-ttu-id="95e93-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="95e93-133">PARAMETERS</span></span>

### <span data-ttu-id="95e93-134">-Force</span><span class="sxs-lookup"><span data-stu-id="95e93-134">-Force</span></span>
<span data-ttu-id="95e93-135">刪除排程工作，即使工作的執行個體正在執行。</span><span class="sxs-lookup"><span data-stu-id="95e93-135">Deletes the scheduled job even if an instance of the job is running.</span></span>
<span data-ttu-id="95e93-136">根據預設值， **Unregister-ScheduledJob** 不會中斷執行中的工作。</span><span class="sxs-lookup"><span data-stu-id="95e93-136">By default, **Unregister-ScheduledJob** does not interrupt running jobs.</span></span>

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

### <span data-ttu-id="95e93-137">-Id</span><span class="sxs-lookup"><span data-stu-id="95e93-137">-Id</span></span>
<span data-ttu-id="95e93-138">刪除具有所指定識別碼 (ID) 的排程工作。</span><span class="sxs-lookup"><span data-stu-id="95e93-138">Deletes the scheduled jobs with the specified identification numbers (ID).</span></span>
<span data-ttu-id="95e93-139">輸入電腦上之排程工作的識別碼。</span><span class="sxs-lookup"><span data-stu-id="95e93-139">Enter the IDs of scheduled jobs on the computer.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: DefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="95e93-140">-InputObject</span><span class="sxs-lookup"><span data-stu-id="95e93-140">-InputObject</span></span>
<span data-ttu-id="95e93-141">指定排程工作。</span><span class="sxs-lookup"><span data-stu-id="95e93-141">Specifies a scheduled job.</span></span>
<span data-ttu-id="95e93-142">輸入包含 **register-scheduledjob** 物件的變數，或輸入可取得 **register-scheduledjob** 物件的命令或運算式，例如 Get-ScheduledJob 命令。</span><span class="sxs-lookup"><span data-stu-id="95e93-142">Enter a variable that contains **ScheduledJob** objects or type a command or expression that gets **ScheduledJob** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="95e93-143">您也可以使用管線將 **ScheduledJob** 物件傳送至 **Unregister-JobTrigger** 。</span><span class="sxs-lookup"><span data-stu-id="95e93-143">You can also pipe **ScheduledJob** objects to **Unregister-JobTrigger** .</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition[]
Parameter Sets: Definition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="95e93-144">-Name</span><span class="sxs-lookup"><span data-stu-id="95e93-144">-Name</span></span>
<span data-ttu-id="95e93-145">刪除具有所指定名稱的排程工作。</span><span class="sxs-lookup"><span data-stu-id="95e93-145">Deletes the scheduled jobs with the specified names.</span></span>
<span data-ttu-id="95e93-146">輸入電腦上一或多個排程工作的名稱。</span><span class="sxs-lookup"><span data-stu-id="95e93-146">Enter the names of one or more scheduled jobs on the computer.</span></span>
<span data-ttu-id="95e93-147">支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="95e93-147">Wildcards are supported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="95e93-148">-Confirm</span><span class="sxs-lookup"><span data-stu-id="95e93-148">-Confirm</span></span>
<span data-ttu-id="95e93-149">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="95e93-149">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="95e93-150">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="95e93-150">-WhatIf</span></span>
<span data-ttu-id="95e93-151">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="95e93-151">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="95e93-152">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="95e93-152">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="95e93-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="95e93-153">CommonParameters</span></span>
<span data-ttu-id="95e93-154">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="95e93-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="95e93-155">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="95e93-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="95e93-156">輸入</span><span class="sxs-lookup"><span data-stu-id="95e93-156">INPUTS</span></span>

### <span data-ttu-id="95e93-157">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="95e93-157">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="95e93-158">您可以使用管線傳送排程工作至 Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="95e93-158">You can pipe scheduled jobs to Unregister-ScheduledJob</span></span>

## <span data-ttu-id="95e93-159">輸出</span><span class="sxs-lookup"><span data-stu-id="95e93-159">OUTPUTS</span></span>

### <span data-ttu-id="95e93-160">無</span><span class="sxs-lookup"><span data-stu-id="95e93-160">None</span></span>
<span data-ttu-id="95e93-161">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="95e93-161">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="95e93-162">注意</span><span class="sxs-lookup"><span data-stu-id="95e93-162">NOTES</span></span>

## <span data-ttu-id="95e93-163">相關連結</span><span class="sxs-lookup"><span data-stu-id="95e93-163">RELATED LINKS</span></span>

[<span data-ttu-id="95e93-164">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="95e93-164">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="95e93-165">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="95e93-165">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="95e93-166">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="95e93-166">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="95e93-167">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="95e93-167">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="95e93-168">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="95e93-168">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="95e93-169">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="95e93-169">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="95e93-170">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="95e93-170">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="95e93-171">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="95e93-171">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="95e93-172">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="95e93-172">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="95e93-173">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="95e93-173">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="95e93-174">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="95e93-174">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="95e93-175">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="95e93-175">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="95e93-176">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="95e93-176">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="95e93-177">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="95e93-177">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="95e93-178">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="95e93-178">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="95e93-179">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="95e93-179">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
