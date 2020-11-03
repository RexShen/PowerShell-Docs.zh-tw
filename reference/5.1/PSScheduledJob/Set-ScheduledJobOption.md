---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/set-scheduledjoboption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ScheduledJobOption
ms.openlocfilehash: 6647e9ba4e2ee49afa90dd382573d437d2deaee6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202975"
---
# <span data-ttu-id="82c1c-103">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="82c1c-103">Set-ScheduledJobOption</span></span>

## <span data-ttu-id="82c1c-104">概要</span><span class="sxs-lookup"><span data-stu-id="82c1c-104">SYNOPSIS</span></span>
<span data-ttu-id="82c1c-105">變更排程工作的工作選項。</span><span class="sxs-lookup"><span data-stu-id="82c1c-105">Changes the job options of a scheduled job.</span></span>

## <span data-ttu-id="82c1c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="82c1c-106">SYNTAX</span></span>

```
Set-ScheduledJobOption [-InputObject] <ScheduledJobOptions> [-PassThru] [-RunElevated] [-HideInTaskScheduler]
 [-RestartOnIdleResume] [-MultipleInstancePolicy <TaskMultipleInstancePolicy>] [-DoNotAllowDemandStart]
 [-RequireNetwork] [-StopIfGoingOffIdle] [-WakeToRun] [-ContinueIfGoingOnBattery] [-StartIfOnBattery]
 [-IdleTimeout <TimeSpan>] [-IdleDuration <TimeSpan>] [-StartIfIdle] [<CommonParameters>]
```

## <span data-ttu-id="82c1c-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="82c1c-107">DESCRIPTION</span></span>
<span data-ttu-id="82c1c-108">**Set-ScheduledJobOptions** Cmdlet 會變更排程工作的工作選項。</span><span class="sxs-lookup"><span data-stu-id="82c1c-108">The **Set-ScheduledJobOptions** cmdlet changes the job options of scheduled jobs.</span></span>

<span data-ttu-id="82c1c-109">若要變更排程工作的選項，請先使用 Get-ScheduledJobOption Cmdlet 來取得排程工作的工作選項。</span><span class="sxs-lookup"><span data-stu-id="82c1c-109">To change the options of a scheduled job, begin by using the Get-ScheduledJobOption cmdlet to get the job options of a scheduled job.</span></span>
<span data-ttu-id="82c1c-110">接著，使用管線傳送選項至 **Set-ScheduledJobOption** ，或將選項儲存在變數中並使用 *Set-ScheduledJobOption* Cmdlet 的 **InputObject** 參數來指定選項。</span><span class="sxs-lookup"><span data-stu-id="82c1c-110">Then, pipe the options to **Set-ScheduledJobOption** or save the options in a variable and use the *InputObject* parameter of **Set-ScheduledJobOption** cmdlet to identify the options.</span></span>
<span data-ttu-id="82c1c-111">使用 **Set-ScheduledJobOption** 的其他參數來變更工作選項。</span><span class="sxs-lookup"><span data-stu-id="82c1c-111">Use the remaining parameters of **Set-ScheduledJobOption** to change the job options.</span></span>

<span data-ttu-id="82c1c-112">若要開啟工作選項，請使用設定該選項的參數。</span><span class="sxs-lookup"><span data-stu-id="82c1c-112">To turn on a job option, use the parameter that sets that option.</span></span>
<span data-ttu-id="82c1c-113">若要關閉選項，請輸入參數名稱、冒號 (： ) 和 $False。</span><span class="sxs-lookup"><span data-stu-id="82c1c-113">To turn off an option, type the parameter name, a colon (:), and $False.</span></span>
<span data-ttu-id="82c1c-114">例如，若要關閉 *RunElevated* 選項，請輸入 `-RunElevated:$False` 。</span><span class="sxs-lookup"><span data-stu-id="82c1c-114">For example, to turn off the *RunElevated* option, type `-RunElevated:$False`.</span></span>

<span data-ttu-id="82c1c-115">每個工作選項物件都包含 JobDefinition 屬性 (其中包含排程工作)，因此當工作選項變更時，與該排程工作的關聯仍會維持。</span><span class="sxs-lookup"><span data-stu-id="82c1c-115">Each job options object includes a JobDefinition property that contains the scheduled job, so the association with the scheduled job is retained when the job options are changed.</span></span>

<span data-ttu-id="82c1c-116">排程工作選項決定工作由 [工作排程器] 啟動時的執行方式。</span><span class="sxs-lookup"><span data-stu-id="82c1c-116">The scheduled job options determine how the job runs when it is started by Task Scheduler.</span></span>
<span data-ttu-id="82c1c-117">當您使用 Start-Job Cmdlet 來啟動排程工作時，這些選項不適用。</span><span class="sxs-lookup"><span data-stu-id="82c1c-117">These options to not apply when you use the Start-Job cmdlet to start a scheduled job.</span></span>

<span data-ttu-id="82c1c-118">**ScheduledJobOption** 是包含在 Windows PowerShell 之 PSScheduledJob 模組中的其中一個工作排程 Cmdlet 集合。</span><span class="sxs-lookup"><span data-stu-id="82c1c-118">**Set-ScheduledJobOption** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="82c1c-119">如需排程工作的詳細資訊，請參閱 PSScheduledJob 模組中的「關於」主題。</span><span class="sxs-lookup"><span data-stu-id="82c1c-119">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="82c1c-120">匯入 PSScheduledJob 模組，然後輸入：`Get-Help about_Scheduled*`，或參閱 about_Scheduled_Jobs。</span><span class="sxs-lookup"><span data-stu-id="82c1c-120">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="82c1c-121">此 Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="82c1c-121">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="82c1c-122">範例</span><span class="sxs-lookup"><span data-stu-id="82c1c-122">EXAMPLES</span></span>

### <span data-ttu-id="82c1c-123">範例1：變更工作選項</span><span class="sxs-lookup"><span data-stu-id="82c1c-123">Example 1: Change job options</span></span>

```
PS C:\> Get-ScheduledJobOption -Name "DeployPackage"
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : False
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : False
RunWithoutNetwork      : False
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNew
JobDefinition          :

The second command uses the **Set-ScheduledJobOpton** cmdlet to change the job options so the values of the WakeToRun and RunWithoutNetwork properties are $True. The command uses the *Passthru* parameter to return the trigger after the change.
PS C:\> Get-ScheduledJobOption -Name "DeployPackage" | Set-ScheduledJobOption -WakeToRun -RequireNetwork:$False -Passthru
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : True
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : False
RunWithoutNetwork      : True
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNewJobDefinition          :
```

<span data-ttu-id="82c1c-124">此範例顯示如何變更本機電腦上之排程工作的選項。</span><span class="sxs-lookup"><span data-stu-id="82c1c-124">This example shows how to change the options of a scheduled job on the local computer.</span></span>

<span data-ttu-id="82c1c-125">第一個命令會使用 Get-ScheduledJobOption Cmdlet 來取得 DeployPackage 排程工作的工作選項。</span><span class="sxs-lookup"><span data-stu-id="82c1c-125">The first command uses the Get-ScheduledJobOption cmdlet to get the job options of the DeployPackage scheduled job.</span></span>
<span data-ttu-id="82c1c-126">輸出顯示 WakeToRun 和 RunElevated 屬性設定為 $False。</span><span class="sxs-lookup"><span data-stu-id="82c1c-126">The output shows that the WakeToRun and RunElevated properties are set to $False.</span></span>

<span data-ttu-id="82c1c-127">此命令並非必要；包含此命令僅為顯示選項變更的效果。</span><span class="sxs-lookup"><span data-stu-id="82c1c-127">This command is not required; it is included only to show the effect of the option change.</span></span>

### <span data-ttu-id="82c1c-128">範例2：變更所有遠端排程工作的選項</span><span class="sxs-lookup"><span data-stu-id="82c1c-128">Example 2: Change an option on all remote scheduled jobs</span></span>

```
PS C:\> Invoke-Command -Computer "Server01" -ScriptBlock {Get-ScheduledJob | Get-ScheduledJobOption | Set-ScheduledJobOption -IdleTimeout 2:00:00}
```

<span data-ttu-id="82c1c-129">此命令會將 *IdleTimeout* 的值從一小時變更為 Server01 電腦上所有排程工作的 (預設值) 為兩小時。</span><span class="sxs-lookup"><span data-stu-id="82c1c-129">This command changes the value of the *IdleTimeout* from one hour (the default value) to two hours on all scheduled jobs on the Server01 computer.</span></span>

<span data-ttu-id="82c1c-130">此命令會使用 Invoke-Command Cmdlet，在 Server01 電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="82c1c-130">The command uses the Invoke-Command cmdlet to run a command on the Server01 computer.</span></span>

<span data-ttu-id="82c1c-131">遠端命令的開頭是可取得電腦上所有排程工作的 Get-ScheduledJob 命令。</span><span class="sxs-lookup"><span data-stu-id="82c1c-131">The remote command begins with a Get-ScheduledJob command that gets all scheduled jobs on the computer.</span></span>
<span data-ttu-id="82c1c-132">排程的工作會以管道傳送至 Get-ScheduledJobOption Cmdlet，以取得排程工作的工作選項。</span><span class="sxs-lookup"><span data-stu-id="82c1c-132">The scheduled jobs are piped to the Get-ScheduledJobOption cmdlet, which gets the job options of the scheduled jobs.</span></span>
<span data-ttu-id="82c1c-133">每個工作選項物件都包含 JobDefinition 屬性 (其中包含排程工作)，因此選項物件會維持與排程工作關聯 (即使它已被變更)。</span><span class="sxs-lookup"><span data-stu-id="82c1c-133">Each job options object contains a JobDefinition property that contains the scheduled job, so the options object remains associated with the scheduled job even when it is changed.</span></span>

<span data-ttu-id="82c1c-134">工作觸發程式會以管線傳送至 **ScheduledJobOption** Cmdlet，此 Cmdlet 會將 *IdleTimeout* 選項的值變更為兩小時， (2:00:00) 。</span><span class="sxs-lookup"><span data-stu-id="82c1c-134">The job triggers are piped to the **Set-ScheduledJobOption** cmdlet, which changes the value of the *IdleTimeout* option to two hours (2:00:00).</span></span>

## <span data-ttu-id="82c1c-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="82c1c-135">PARAMETERS</span></span>

### <span data-ttu-id="82c1c-136">-ContinueIfGoingOnBattery</span><span class="sxs-lookup"><span data-stu-id="82c1c-136">-ContinueIfGoingOnBattery</span></span>
<span data-ttu-id="82c1c-137">當電腦切換到電池電源 (中斷 AC 電源)，若工作正在執行，不要停止排程工作。</span><span class="sxs-lookup"><span data-stu-id="82c1c-137">Do not stop the scheduled job if the computer switches to battery power (disconnects from AC power) while the job is running.</span></span>
<span data-ttu-id="82c1c-138">根據預設值，當電腦中斷 AC 電源時，排程工作會停止。</span><span class="sxs-lookup"><span data-stu-id="82c1c-138">By default, scheduled jobs stop when the computer disconnects from AC power.</span></span>

<span data-ttu-id="82c1c-139">*ContinueIfGoingOnBattery* 參數會將排程工作的 StopIfGoingOnBatteries 屬性值設定為 $True。</span><span class="sxs-lookup"><span data-stu-id="82c1c-139">The *ContinueIfGoingOnBattery* parameter sets the value of the StopIfGoingOnBatteries property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="82c1c-140">-DoNotAllowDemandStart</span><span class="sxs-lookup"><span data-stu-id="82c1c-140">-DoNotAllowDemandStart</span></span>
<span data-ttu-id="82c1c-141">只有在工作被觸發時才啟動工作。</span><span class="sxs-lookup"><span data-stu-id="82c1c-141">Start the job only when it is triggered.</span></span>
<span data-ttu-id="82c1c-142">使用者無法手動啟動工作，例如使用 [工作排程器] 中的 [執行] 功能。</span><span class="sxs-lookup"><span data-stu-id="82c1c-142">Users cannot start the job manually, such as by using the Run feature in Task Scheduler.</span></span>

<span data-ttu-id="82c1c-143">此參數只會影響 [工作排程器]。</span><span class="sxs-lookup"><span data-stu-id="82c1c-143">This parameter only affects Task Scheduler.</span></span>
<span data-ttu-id="82c1c-144">它不會防止使用者使用 Start-Job Cmdlet 來啟動工作。</span><span class="sxs-lookup"><span data-stu-id="82c1c-144">It does not prevents users from using the Start-Job cmdlet to start the job.</span></span>

<span data-ttu-id="82c1c-145">*DoNotAllowDemandStart* 參數會將排程工作的 DoNotAllowDemandStart 屬性值設定為 $True。</span><span class="sxs-lookup"><span data-stu-id="82c1c-145">The *DoNotAllowDemandStart* parameter sets the value of the DoNotAllowDemandStart property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="82c1c-146">-HideInTaskScheduler</span><span class="sxs-lookup"><span data-stu-id="82c1c-146">-HideInTaskScheduler</span></span>
<span data-ttu-id="82c1c-147">不要在 [工作排程器] 中顯示工作。</span><span class="sxs-lookup"><span data-stu-id="82c1c-147">Do not display the job in Task Scheduler.</span></span>
<span data-ttu-id="82c1c-148">此值只會影響工作執行所在電腦。</span><span class="sxs-lookup"><span data-stu-id="82c1c-148">This value affects only the computer on which the job runs.</span></span>
<span data-ttu-id="82c1c-149">根據預設值，排程工作會出現在 [工作排程器] 中。</span><span class="sxs-lookup"><span data-stu-id="82c1c-149">By default, scheduled tasks appear in Task Scheduler.</span></span>

<span data-ttu-id="82c1c-150">即使工作是隱藏的，使用者也可以選取工作排程器中的 [ **顯示隱藏** 的工作] 選項來顯示工作。</span><span class="sxs-lookup"><span data-stu-id="82c1c-150">Even if a task is hidden, users can display the task by selecting the **Show hidden tasks** view option in Task Scheduler.</span></span>

<span data-ttu-id="82c1c-151">*HideInTaskScheduler* 參數會將排程工作的 ShowInTaskScheduler 屬性值設定為 $False。</span><span class="sxs-lookup"><span data-stu-id="82c1c-151">The *HideInTaskScheduler* parameter sets the value of the ShowInTaskScheduler property of scheduled jobs to $False.</span></span>

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

### <span data-ttu-id="82c1c-152">-IdleDuration</span><span class="sxs-lookup"><span data-stu-id="82c1c-152">-IdleDuration</span></span>
<span data-ttu-id="82c1c-153">指定工作啟動前的電腦閒置時間長度。</span><span class="sxs-lookup"><span data-stu-id="82c1c-153">Specifies how long the computer must be idle before the job starts.</span></span>
<span data-ttu-id="82c1c-154">預設值是 10 分鐘。</span><span class="sxs-lookup"><span data-stu-id="82c1c-154">The default value is 10 minutes.</span></span>
<span data-ttu-id="82c1c-155">若 *IdleTimeout* 值所指定的時間經過之前，電腦閒置時間未達指定的時間長度，則排程工作不會執行 (直到下次排定的時間，如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="82c1c-155">If the computer is not idle for the specified duration before the value of *IdleTimeout* expires, the scheduled job does not run until the next scheduled time, if any.</span></span>

<span data-ttu-id="82c1c-156">輸入 timespan 物件（例如 New-TimeSpan Cmdlet 所產生的物件），或輸入會 \<hours\> \<minutes\> \<seconds\> 自動轉換成 **timespan** 物件的值（以：：格式表示）。</span><span class="sxs-lookup"><span data-stu-id="82c1c-156">Enter a timespan object, such as one generated by the New-TimeSpan cmdlet, or enter a value in \<hours\>:\<minutes\>:\<seconds\> format that is automatically converted to a **TimeSpan** object.</span></span>

<span data-ttu-id="82c1c-157">若要啟用此值，請使用 *StartIfIdle* 參數。</span><span class="sxs-lookup"><span data-stu-id="82c1c-157">To enable this value, use the *StartIfIdle* parameter.</span></span>
<span data-ttu-id="82c1c-158">根據預設，排程工作的 StartIfNotIdle 屬性會設定為 $True，Windows PowerShell 會忽略 *IdleDuration* 和 *IdleTimeout* 值。</span><span class="sxs-lookup"><span data-stu-id="82c1c-158">By default, the StartIfNotIdle property of scheduled jobs is set to $True and Windows PowerShell ignores the *IdleDuration* and *IdleTimeout* values.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="82c1c-159">-IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="82c1c-159">-IdleTimeout</span></span>
<span data-ttu-id="82c1c-160">指定工作啟動前的電腦閒置時間長度。</span><span class="sxs-lookup"><span data-stu-id="82c1c-160">Specifies how long the computer must be idle before the job starts.</span></span>
<span data-ttu-id="82c1c-161">預設值是 10 分鐘。</span><span class="sxs-lookup"><span data-stu-id="82c1c-161">The default value is 10 minutes.</span></span>
<span data-ttu-id="82c1c-162">若 **IdleTimeout** 值所指定的時間經過之前，電腦閒置時間未達指定的時間長度，則排程工作不會執行 (直到下次排定的時間，如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="82c1c-162">If the computer is not idle for the specified duration before the value of **IdleTimeout** expires, the scheduled job does not run until the next scheduled time, if any.</span></span>

<span data-ttu-id="82c1c-163">輸入 timespan 物件（例如 New-TimeSpan Cmdlet 所產生的物件），或輸入會 \<hours\> \<minutes\> \<seconds\> 自動轉換成 **timespan** 物件的值（以：：格式表示）。</span><span class="sxs-lookup"><span data-stu-id="82c1c-163">Enter a timespan object, such as one generated by the New-TimeSpan cmdlet, or enter a value in \<hours\>:\<minutes\>:\<seconds\> format that is automatically converted to a **TimeSpan** object.</span></span>

<span data-ttu-id="82c1c-164">若要啟用此值，請使用 *StartIfIdle* 參數。</span><span class="sxs-lookup"><span data-stu-id="82c1c-164">To enable this value, use the *StartIfIdle* parameter.</span></span>
<span data-ttu-id="82c1c-165">根據預設，排程工作的 StartIfNotIdle 屬性會設定為 $True，Windows PowerShell 會忽略 *IdleDuration* 和 *IdleTimeout* 值。</span><span class="sxs-lookup"><span data-stu-id="82c1c-165">By default, the StartIfNotIdle property of scheduled jobs is set to $True and Windows PowerShell ignores the *IdleDuration* and *IdleTimeout* values.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="82c1c-166">-InputObject</span><span class="sxs-lookup"><span data-stu-id="82c1c-166">-InputObject</span></span>
<span data-ttu-id="82c1c-167">指定工作選項。</span><span class="sxs-lookup"><span data-stu-id="82c1c-167">Specifies the job options.</span></span>
<span data-ttu-id="82c1c-168">輸入包含 **ScheduledJobOptions** 物件的變數，或輸入可取得 **ScheduledJobOptions** 物件的命令或運算式，例如 Get-ScheduledJobOption 命令。</span><span class="sxs-lookup"><span data-stu-id="82c1c-168">Enter a variable that contains **ScheduledJobOptions** objects or type a command or expression that gets **ScheduledJobOptions** objects, such as a Get-ScheduledJobOption command.</span></span>
<span data-ttu-id="82c1c-169">您也可以使用管線將 **ScheduledJobOptions** 物件傳送至 **ScheduledJobOption** 。</span><span class="sxs-lookup"><span data-stu-id="82c1c-169">You can also pipe a **ScheduledJobOptions** object to **Set-ScheduledJobOption** .</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="82c1c-170">-MultipleInstancePolicy</span><span class="sxs-lookup"><span data-stu-id="82c1c-170">-MultipleInstancePolicy</span></span>
<span data-ttu-id="82c1c-171">決定當排程工作的某個執行個體已在執行時，系統如何回應啟動該排程工作之另一個執行個體的要求。</span><span class="sxs-lookup"><span data-stu-id="82c1c-171">Determines how the system responds to a request to start an instance of a scheduled job while another instance of the job is running.</span></span>
<span data-ttu-id="82c1c-172">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="82c1c-172">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="82c1c-173">IgnoreNew.</span><span class="sxs-lookup"><span data-stu-id="82c1c-173">IgnoreNew.</span></span>
<span data-ttu-id="82c1c-174">將略過新的工作執行個體。</span><span class="sxs-lookup"><span data-stu-id="82c1c-174">The new job instance is ignored.</span></span>
<span data-ttu-id="82c1c-175">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="82c1c-175">This is the default value.</span></span>
- <span data-ttu-id="82c1c-176">Parallel</span><span class="sxs-lookup"><span data-stu-id="82c1c-176">Parallel.</span></span>
<span data-ttu-id="82c1c-177">將立即啟動新的工作執行個體。</span><span class="sxs-lookup"><span data-stu-id="82c1c-177">The new job instance starts immediately.</span></span>
- <span data-ttu-id="82c1c-178">佇列。</span><span class="sxs-lookup"><span data-stu-id="82c1c-178">Queue.</span></span>
<span data-ttu-id="82c1c-179">新的工作執行個體會在目前的執行個體完成時立即啟動。</span><span class="sxs-lookup"><span data-stu-id="82c1c-179">The new job instance starts as soon as the current instance completes.</span></span>
- <span data-ttu-id="82c1c-180">StopExisting.</span><span class="sxs-lookup"><span data-stu-id="82c1c-180">StopExisting.</span></span>
<span data-ttu-id="82c1c-181">將停止目前的工作執行個體，並啟動新的執行個體。</span><span class="sxs-lookup"><span data-stu-id="82c1c-181">The current instance of the job stop and the new instance starts.</span></span>

<span data-ttu-id="82c1c-182">必須符合工作排程的所有條件，工作才會執行。</span><span class="sxs-lookup"><span data-stu-id="82c1c-182">To run the job, all conditions for the job schedule must be met.</span></span>
<span data-ttu-id="82c1c-183">例如，如果不符合 *RequireNetwork* 、 *IdleDuration* 和 *IdleTimeout* 參數所設定的條件，則不論此參數的值為何，工作實例都不會啟動。</span><span class="sxs-lookup"><span data-stu-id="82c1c-183">For example, if the conditions that are set by the *RequireNetwork* , *IdleDuration* , and *IdleTimeout* parameters are not satisfied, the job instance is not started, regardless of the value of this parameter.</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.TaskMultipleInstancePolicy
Parameter Sets: (All)
Aliases:
Accepted values: None, IgnoreNew, Parallel, Queue, StopExisting

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="82c1c-184">-PassThru</span><span class="sxs-lookup"><span data-stu-id="82c1c-184">-PassThru</span></span>
<span data-ttu-id="82c1c-185">傳回代表您正在使用之項目的物件。</span><span class="sxs-lookup"><span data-stu-id="82c1c-185">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="82c1c-186">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="82c1c-186">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="82c1c-187">-RequireNetwork</span><span class="sxs-lookup"><span data-stu-id="82c1c-187">-RequireNetwork</span></span>
<span data-ttu-id="82c1c-188">只有在網路連線可以使用時才執行排程工作。</span><span class="sxs-lookup"><span data-stu-id="82c1c-188">Runs the scheduled job only when network connections are available.</span></span>

<span data-ttu-id="82c1c-189">若指定此參數且網路連線在排定的啟動時間無法使用，該工作不會執行 (直到排定的下次啟動時間，如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="82c1c-189">If you specify this parameter and the network is not available at the scheduled start time, the job does not run until the next scheduled start time, if any.</span></span>

<span data-ttu-id="82c1c-190">*RequireNetwork* 參數會將排程工作的 RunWithoutNetwork 屬性值設定為 $False。</span><span class="sxs-lookup"><span data-stu-id="82c1c-190">The *RequireNetwork* parameter sets the value of the RunWithoutNetwork property of scheduled jobs to $False.</span></span>

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

### <span data-ttu-id="82c1c-191">-RestartOnIdleResume</span><span class="sxs-lookup"><span data-stu-id="82c1c-191">-RestartOnIdleResume</span></span>
<span data-ttu-id="82c1c-192">當電腦成為閒置時重新啟動排程工作。</span><span class="sxs-lookup"><span data-stu-id="82c1c-192">Restarts a scheduled job when the computer becomes idle.</span></span>
<span data-ttu-id="82c1c-193">此參數搭配 *StopIfGoingOffIdle* 參數使用，它可以在電腦成為作用中 (離開閒置狀態) 時暫停執行中的排程工作。</span><span class="sxs-lookup"><span data-stu-id="82c1c-193">This parameter works with the *StopIfGoingOffIdle* parameter, which suspends a running scheduled job if the computer becomes active (leaves the idle state).</span></span>

<span data-ttu-id="82c1c-194">*RestartOnIdleResume* 參數會將排程工作的 RestartOnIdleResume 屬性值設定為 $True。</span><span class="sxs-lookup"><span data-stu-id="82c1c-194">The *RestartOnIdleResume* parameter sets the value of the RestartOnIdleResume property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="82c1c-195">-RunElevated</span><span class="sxs-lookup"><span data-stu-id="82c1c-195">-RunElevated</span></span>
<span data-ttu-id="82c1c-196">使用工作執行所在電腦上 Administrators 群組成員的權限執行排程工作。</span><span class="sxs-lookup"><span data-stu-id="82c1c-196">Runs the scheduled job with the permissions of a member of the Administrators group on the computer on which the job runs.</span></span>

<span data-ttu-id="82c1c-197">若要讓排程工作以系統管理員許可權執行，請使用 Register-ScheduledJob 的 *credential* 參數來提供作業的明確認證。</span><span class="sxs-lookup"><span data-stu-id="82c1c-197">To enable a scheduled job to run with Administrator permissions, use the *Credential* parameter of Register-ScheduledJob to provide explicit credential for the job.</span></span>

<span data-ttu-id="82c1c-198">**RunElevated** 參數會將排程工作的 **RunElevated** 屬性值設定為 True。</span><span class="sxs-lookup"><span data-stu-id="82c1c-198">The **RunElevated** parameter sets the value of the **RunElevated** property of scheduled jobs to True.</span></span>

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

### <span data-ttu-id="82c1c-199">-StartIfIdle</span><span class="sxs-lookup"><span data-stu-id="82c1c-199">-StartIfIdle</span></span>
<span data-ttu-id="82c1c-200">若電腦已閒置 **IdleDuration** 參數所指定的時間，但 *IdleTimeout* 參數所指定的時間尚未經過，則啟動排程工作。</span><span class="sxs-lookup"><span data-stu-id="82c1c-200">Starts the scheduled job if the computer has been idle for the time specified by the **IdleDuration** parameter before the time specified by the *IdleTimeout* parameter expires.</span></span>

<span data-ttu-id="82c1c-201">根據預設值，系統會略過 *IdleDuration* 與 *IdleTimeout* 參數，且工作會在排定的開始時間執行 (即使電腦忙碌中)。</span><span class="sxs-lookup"><span data-stu-id="82c1c-201">By default, the *IdleDuration* and *IdleTimeout* parameters are ignored and the job starts at the scheduled start time even if the computer is busy.</span></span>

<span data-ttu-id="82c1c-202">若指定此參數且電腦在排定的開始時間為忙碌中 (非閒置)，則工作不會執行 (直到排定的下次開始時間，如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="82c1c-202">If you specify this parameter and the computer is busy (not idle) at the scheduled start time, the job does not run until the next scheduled start time, if any.</span></span>

<span data-ttu-id="82c1c-203">*StartIfIdle* 參數會將排程工作的 **StartIfNotIdle** 屬性值設定為 False。</span><span class="sxs-lookup"><span data-stu-id="82c1c-203">The *StartIfIdle* parameter sets the value of the **StartIfNotIdle** property of scheduled jobs to False.</span></span>

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

### <span data-ttu-id="82c1c-204">-StartIfOnBattery</span><span class="sxs-lookup"><span data-stu-id="82c1c-204">-StartIfOnBattery</span></span>
<span data-ttu-id="82c1c-205">即使電腦在排定的開始時間是使用電池電力執行，也啟動排程工作。</span><span class="sxs-lookup"><span data-stu-id="82c1c-205">Starts the scheduled job even if the computer is running on batteries at the scheduled start time.</span></span>
<span data-ttu-id="82c1c-206">預設值是 False。</span><span class="sxs-lookup"><span data-stu-id="82c1c-206">The default value is False.</span></span>

<span data-ttu-id="82c1c-207">*StartIfOnBattery* 參數會將排程工作的 **StartIfOnBatteries** 屬性值設定為 $True。</span><span class="sxs-lookup"><span data-stu-id="82c1c-207">The *StartIfOnBattery* parameter sets the value of the **StartIfOnBatteries** property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="82c1c-208">-StopIfGoingOffIdle</span><span class="sxs-lookup"><span data-stu-id="82c1c-208">-StopIfGoingOffIdle</span></span>
<span data-ttu-id="82c1c-209">若電腦在工作正在執行時成為作用中 (非閒置)，則暫停執行中的排程工作。</span><span class="sxs-lookup"><span data-stu-id="82c1c-209">Suspends a running scheduled job if the computer becomes active (not idle) while the job is running.</span></span>

<span data-ttu-id="82c1c-210">根據預設值，當電腦再度進入閒置狀態時，當初在電腦成為作用中時暫停的排程工作會繼續執行。</span><span class="sxs-lookup"><span data-stu-id="82c1c-210">By default, a scheduled job that is suspended when the computer becomes active resumes when the computer becomes idle again.</span></span>
<span data-ttu-id="82c1c-211">若要變更此預設行為，請使用 *RestartOnIdleResume* 參數。</span><span class="sxs-lookup"><span data-stu-id="82c1c-211">To change this default behavior, use the *RestartOnIdleResume* parameter.</span></span>

<span data-ttu-id="82c1c-212">*StopIfGoingOffIdle* 參數會將排程工作的 StopIfGoingOffIdle 屬性值設定為 $True。</span><span class="sxs-lookup"><span data-stu-id="82c1c-212">The *StopIfGoingOffIdle* parameter sets the value of the StopIfGoingOffIdle property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="82c1c-213">-WakeToRun</span><span class="sxs-lookup"><span data-stu-id="82c1c-213">-WakeToRun</span></span>
<span data-ttu-id="82c1c-214">在到了排定的開始時間時將電腦從休眠或睡眠狀態喚醒以執行工作。</span><span class="sxs-lookup"><span data-stu-id="82c1c-214">Wakes the computer from a Hibernate or Sleep state at the scheduled start time so it can run the job.</span></span>
<span data-ttu-id="82c1c-215">根據預設值，在到了排定的開始時間時，若電腦處於休眠或睡眠狀態，則工作不會執行。</span><span class="sxs-lookup"><span data-stu-id="82c1c-215">By default, if the computer is in a Hibernate or Sleep state at the scheduled start time, the job does not run.</span></span>

<span data-ttu-id="82c1c-216">*WakeToRun* 參數會將排程工作的 WakeToRun 屬性值設定為 $True。</span><span class="sxs-lookup"><span data-stu-id="82c1c-216">The *WakeToRun* parameter sets the value of the WakeToRun property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="82c1c-217">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="82c1c-217">CommonParameters</span></span>
<span data-ttu-id="82c1c-218">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="82c1c-218">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="82c1c-219">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="82c1c-219">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="82c1c-220">輸入</span><span class="sxs-lookup"><span data-stu-id="82c1c-220">INPUTS</span></span>

### <span data-ttu-id="82c1c-221">Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions</span><span class="sxs-lookup"><span data-stu-id="82c1c-221">Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions</span></span>
<span data-ttu-id="82c1c-222">您可以使用管線傳送排程工作選項物件至 **Set-ScheduledJobOption** 。</span><span class="sxs-lookup"><span data-stu-id="82c1c-222">You can pipe a scheduled job options object to **Set-ScheduledJobOption** .</span></span>

## <span data-ttu-id="82c1c-223">輸出</span><span class="sxs-lookup"><span data-stu-id="82c1c-223">OUTPUTS</span></span>

### <span data-ttu-id="82c1c-224">None 或 Register-scheduledjob. ScheduledJobOptions</span><span class="sxs-lookup"><span data-stu-id="82c1c-224">None or Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions</span></span>
<span data-ttu-id="82c1c-225">當您使用 *Passthru* 參數時， **Set-ScheduledJobOption** 會傳回已變更的工作選項。</span><span class="sxs-lookup"><span data-stu-id="82c1c-225">When you use the *Passthru* parameter, **Set-ScheduledJobOption** returns the job options that were changed.</span></span>
<span data-ttu-id="82c1c-226">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="82c1c-226">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="82c1c-227">注意</span><span class="sxs-lookup"><span data-stu-id="82c1c-227">NOTES</span></span>

## <span data-ttu-id="82c1c-228">相關連結</span><span class="sxs-lookup"><span data-stu-id="82c1c-228">RELATED LINKS</span></span>

[<span data-ttu-id="82c1c-229">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="82c1c-229">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="82c1c-230">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="82c1c-230">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="82c1c-231">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="82c1c-231">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="82c1c-232">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="82c1c-232">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="82c1c-233">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="82c1c-233">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="82c1c-234">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="82c1c-234">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="82c1c-235">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="82c1c-235">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="82c1c-236">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="82c1c-236">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="82c1c-237">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="82c1c-237">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="82c1c-238">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="82c1c-238">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="82c1c-239">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="82c1c-239">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="82c1c-240">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="82c1c-240">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="82c1c-241">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="82c1c-241">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="82c1c-242">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="82c1c-242">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="82c1c-243">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="82c1c-243">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="82c1c-244">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="82c1c-244">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
