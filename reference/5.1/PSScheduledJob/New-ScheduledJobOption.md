---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/new-scheduledjoboption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ScheduledJobOption
ms.openlocfilehash: 35ada8d5aaa6a6c1fdc74a089308aefe13598b10
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202996"
---
# <span data-ttu-id="6498b-103">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="6498b-103">New-ScheduledJobOption</span></span>

## <span data-ttu-id="6498b-104">概要</span><span class="sxs-lookup"><span data-stu-id="6498b-104">SYNOPSIS</span></span>
<span data-ttu-id="6498b-105">建立包含排程工作之進階選項的物件。</span><span class="sxs-lookup"><span data-stu-id="6498b-105">Creates an object that contains advanced options for a scheduled job.</span></span>

## <span data-ttu-id="6498b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6498b-106">SYNTAX</span></span>

```
New-ScheduledJobOption [-RunElevated] [-HideInTaskScheduler] [-RestartOnIdleResume]
 [-MultipleInstancePolicy <TaskMultipleInstancePolicy>] [-DoNotAllowDemandStart] [-RequireNetwork]
 [-StopIfGoingOffIdle] [-WakeToRun] [-ContinueIfGoingOnBattery] [-StartIfOnBattery] [-IdleTimeout <TimeSpan>]
 [-IdleDuration <TimeSpan>] [-StartIfIdle] [<CommonParameters>]
```

## <span data-ttu-id="6498b-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6498b-107">DESCRIPTION</span></span>
<span data-ttu-id="6498b-108">**New-ScheduledJobOption** Cmdlet 會建立包含排程工作之進階選項的物件。</span><span class="sxs-lookup"><span data-stu-id="6498b-108">The **New-ScheduledJobOption** cmdlet creates an object that contains advanced options for a scheduled job.</span></span>

<span data-ttu-id="6498b-109">您可以使用由 **New-ScheduledJobOption** 所傳回的 **ScheduledJobOptions** 物件來設定新的或現有的排程工作的工作選項。</span><span class="sxs-lookup"><span data-stu-id="6498b-109">You can use the **ScheduledJobOptions** object that **New-ScheduledJobOption** returns to set job options for a new or existing scheduled job.</span></span>
<span data-ttu-id="6498b-110">或者，您也可以使用 Get-ScheduledJobOption Cmdlet 來取得現有排程工作的工作選項，或使用雜湊表值來代表工作選項，以設定工作選項。</span><span class="sxs-lookup"><span data-stu-id="6498b-110">Alternatively, you can set job options by using the Get-ScheduledJobOption cmdlet to get the job options of an existing scheduled job or by using a hash table value to represent the job options.</span></span>

<span data-ttu-id="6498b-111">如果沒有參數， **ScheduledJobOption** 會產生包含所有選項之預設值的物件。</span><span class="sxs-lookup"><span data-stu-id="6498b-111">Without parameters, **New-ScheduledJobOption** generates an object that contains the default values for all of the options.</span></span>
<span data-ttu-id="6498b-112">因為所有屬性 (JobDefinition 屬性除外) 都可以編輯，所以您可以使用產生的物件作為範本，然後為您的企業建立標準選項物件。</span><span class="sxs-lookup"><span data-stu-id="6498b-112">Because all of the properties except for the JobDefinition property can be edited, you can use the resulting object as a template, and create standard option objects for your enterprise.</span></span>

<span data-ttu-id="6498b-113">建立排程工作並設定排程工作選項時，請檢閱所有排程工作選項的預設值。</span><span class="sxs-lookup"><span data-stu-id="6498b-113">When creating scheduled jobs and setting scheduled job options, review the default values of all scheduled job options.</span></span>
<span data-ttu-id="6498b-114">只有當符合為排程工作設定的所有執行條件時，排程工作才會執行。</span><span class="sxs-lookup"><span data-stu-id="6498b-114">Scheduled jobs run only when all conditions set for their execution are satisfied.</span></span>

<span data-ttu-id="6498b-115">**ScheduledJobOption** 是包含在 Windows PowerShell 之 PSScheduledJob 模組中的其中一個工作排程 Cmdlet 集合。</span><span class="sxs-lookup"><span data-stu-id="6498b-115">**New-ScheduledJobOption** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="6498b-116">如需排程工作的詳細資訊，請參閱 PSScheduledJob 模組中的「關於」主題。</span><span class="sxs-lookup"><span data-stu-id="6498b-116">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="6498b-117">匯入 PSScheduledJob 模組，然後輸入：`Get-Help about_Scheduled*`，或參閱 about_Scheduled_Jobs。</span><span class="sxs-lookup"><span data-stu-id="6498b-117">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="6498b-118">此 Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="6498b-118">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="6498b-119">範例</span><span class="sxs-lookup"><span data-stu-id="6498b-119">EXAMPLES</span></span>

### <span data-ttu-id="6498b-120">範例1：建立具有預設值的排程工作選項物件</span><span class="sxs-lookup"><span data-stu-id="6498b-120">Example 1: Create a scheduled job option object with default values</span></span>

```
PS C:\> New-ScheduledJobOption
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
RunWithoutNetwork      : True
DoNotAllowDemandStart  : False
MultipleInstancePolicy : Ignore
NewJobDefinition       :
```

<span data-ttu-id="6498b-121">此命令會建立具有所有預設值的排程工作選項物件。</span><span class="sxs-lookup"><span data-stu-id="6498b-121">This command creates a scheduled job option object that has all of the default values.</span></span>

### <span data-ttu-id="6498b-122">範例2：使用自訂值建立排程工作選項物件</span><span class="sxs-lookup"><span data-stu-id="6498b-122">Example 2: Create a scheduled job option object with custom values</span></span>

```
PS C:\> New-ScheduledJobOption -RequireNetwork -StartIfOnBattery
StartIfOnBatteries     : True
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
MultipleInstancePolicy : Ignore
NewJobDefinition       :
```

<span data-ttu-id="6498b-123">下列命令會建立一個排程工作物件，此排程工作要求必須有網路連線，且會在即使電腦未連接 AC 電源時執行。</span><span class="sxs-lookup"><span data-stu-id="6498b-123">The following command creates a scheduled job object that requires the network and runs the scheduled job even if the computer is not connected to AC power.</span></span>

<span data-ttu-id="6498b-124">輸出顯示 *RequireNetwork* 參數將 RunWithoutNetwork 屬性的值變更為 $False，且 *StartIfOnBattery* 參數將 StartIfOnBatteries 屬性的值變更為 $True。</span><span class="sxs-lookup"><span data-stu-id="6498b-124">The output shows that the *RequireNetwork* parameter changed the value of the RunWithoutNetwork property to $False and the *StartIfOnBattery* parameter changed the value of the StartIfOnBatteries property to $True.</span></span>

### <span data-ttu-id="6498b-125">範例3：設定新排程工作的選項</span><span class="sxs-lookup"><span data-stu-id="6498b-125">Example 3: Set options for a new scheduled job</span></span>

```
The first command creates a **ScheduledJobOptions** object with the *RunElevated* parameter. It saves the object in the $RunAsAdmin variable.
PS C:\> $RunAsAdmin = New-ScheduledJobOption -RunElevated

The second command uses the Register-ScheduledJob cmdlet to create a new scheduled job. The value of the *ScheduledJobOption* parameter is the option object in the value of the $RunAsAdmin variable.
PS C:\> Register-ScheduledJob -Name Backup -FilePath D:\Scripts\Backup.ps1 -Trigger $Mondays -ScheduledJobOption $RunAsAdmin

The third command uses the Get-ScheduledJobOption cmdlet to get the job options of the Backup scheduled job.The cmdlet output shows that the RunElevated property is set to $True and the JobDefinition property of the job option object is now populated with the scheduled job object for the Backup scheduled job.
PS C:\> Get-ScheduledJobOption -Name Backup
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : False
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : True
RunWithoutNetwork      : True
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNew
JobDefinition          : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

<span data-ttu-id="6498b-126">此範例顯示如何使用由 **New-ScheduledJobOption** 所傳回的 **ScheduledJobOptions** 物件來設定新排程工作的選項。</span><span class="sxs-lookup"><span data-stu-id="6498b-126">This example shows how to use the **ScheduledJobOptions** object that **New-ScheduledJobOption** returns to set the options for a new scheduled job.</span></span>

### <span data-ttu-id="6498b-127">範例4：排序排程工作選項物件的屬性</span><span class="sxs-lookup"><span data-stu-id="6498b-127">Example 4: Sort the properties of a scheduled job option object</span></span>

```
PS C:\> $Options = New-ScheduledJobOption -WakeToRun
PS C:\> $Options.PSObject.Properties | Sort-Object -Property Name | Format-Table -Property Name, Value -Autosize
Name                       Value
----                       -----
DoNotAllowDemandStart      False
IdleDuration            00:10:00
IdleTimeout             01:00:00
JobDefinition
MultipleInstancePolicy IgnoreNew
RestartOnIdleResume        False
RunElevated                False
RunWithoutNetwork           True
ShowInTaskScheduler         True
StartIfNotIdle              True
StartIfOnBatteries         False
StopIfGoingOffIdle         False
StopIfGoingOnBatteries      True
WakeToRun                   True
```

<span data-ttu-id="6498b-128">此範例顯示如何以字母順序排序 **ScheduledJobOptions** 物件的屬性以方便閱讀。</span><span class="sxs-lookup"><span data-stu-id="6498b-128">This example shows how to sort the properties of a **ScheduledJobOptions** object in alphabetical order for easy reading.</span></span>

<span data-ttu-id="6498b-129">第一個命令使用 **New-ScheduledJobOption** Cmdlet 來建立 **ScheduledJobOptions** 物件。</span><span class="sxs-lookup"><span data-stu-id="6498b-129">The first command uses the **New-ScheduledJobOption** cmdlet to create a **ScheduledJobOptions** object.</span></span>
<span data-ttu-id="6498b-130">此命令使用 *WakeToRun* 參數並將產生的結果物件儲存在 $Options 變數中。</span><span class="sxs-lookup"><span data-stu-id="6498b-130">The command uses the *WakeToRun* parameter and saves the resulting object in the $Options variable.</span></span>

<span data-ttu-id="6498b-131">若要取得 $Options 的屬性做為物件，第二個命令會使用所有 Windows PowerShell 物件的 **PSObject** 屬性及其 properties 屬性。</span><span class="sxs-lookup"><span data-stu-id="6498b-131">To get the properties of $Options as objects, the second command uses the **PSObject** property of all Windows PowerShell objects and its Properties property.</span></span>
<span data-ttu-id="6498b-132">然後，此命令會使用管線將屬性物件傳送至 Sort-Object Cmdlet，此 Cmdlet 會依名稱依字母順序排序屬性，然後再傳送至 Format-Table Cmdlet，以顯示資料表中屬性的名稱和值。</span><span class="sxs-lookup"><span data-stu-id="6498b-132">The command then pipes the property objects to the Sort-Object cmdlet, which sorts the properties in alphabetical order by name, and then to the Format-Table cmdlet, which displays the names and values of the properties in a table.</span></span>

<span data-ttu-id="6498b-133">此格式可讓您更輕鬆地在 $Options 中尋找 **ScheduledJobOptions** 物件的 WakeToRun 屬性，並確認其值已從 $False 變更為 $True。</span><span class="sxs-lookup"><span data-stu-id="6498b-133">This format makes it much easier to find the WakeToRun property of the **ScheduledJobOptions** object in $Options and to verify that its value was changed from $False to $True.</span></span>

## <span data-ttu-id="6498b-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6498b-134">PARAMETERS</span></span>

### <span data-ttu-id="6498b-135">-ContinueIfGoingOnBattery</span><span class="sxs-lookup"><span data-stu-id="6498b-135">-ContinueIfGoingOnBattery</span></span>
<span data-ttu-id="6498b-136">當電腦切換到電池電源 (中斷 AC 電源)，若工作正在執行，不要停止排程工作。</span><span class="sxs-lookup"><span data-stu-id="6498b-136">Do not stop the scheduled job if the computer switches to battery power (disconnects from AC power) while the job is running.</span></span>
<span data-ttu-id="6498b-137">根據預設值，當電腦中斷 AC 電源時，排程工作會停止。</span><span class="sxs-lookup"><span data-stu-id="6498b-137">By default, scheduled jobs stop when the computer disconnects from AC power.</span></span>

<span data-ttu-id="6498b-138">*ContinueIfGoingOnBattery* 參數會將排程工作的 StopIfGoingOnBatteries 屬性值設定為 $True。</span><span class="sxs-lookup"><span data-stu-id="6498b-138">The *ContinueIfGoingOnBattery* parameter sets the value of the StopIfGoingOnBatteries property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="6498b-139">-DoNotAllowDemandStart</span><span class="sxs-lookup"><span data-stu-id="6498b-139">-DoNotAllowDemandStart</span></span>
<span data-ttu-id="6498b-140">只有在工作被觸發時才啟動工作。</span><span class="sxs-lookup"><span data-stu-id="6498b-140">Start the job only when it is triggered.</span></span>
<span data-ttu-id="6498b-141">使用者無法手動啟動工作，例如使用 [工作排程器] 中的 [執行] 功能。</span><span class="sxs-lookup"><span data-stu-id="6498b-141">Users cannot start the job manually, such as by using the Run feature in Task Scheduler.</span></span>

<span data-ttu-id="6498b-142">此參數只會影響 [工作排程器]。</span><span class="sxs-lookup"><span data-stu-id="6498b-142">This parameter only affects Task Scheduler.</span></span>
<span data-ttu-id="6498b-143">它不會防止使用者使用 Start-Job Cmdlet 來啟動工作。</span><span class="sxs-lookup"><span data-stu-id="6498b-143">It does not prevents users from using the Start-Job cmdlet to start the job.</span></span>

<span data-ttu-id="6498b-144">*DoNotAllowDemandStart* 參數會將排程工作的 DoNotAllowDemandStart 屬性值設定為 $True。</span><span class="sxs-lookup"><span data-stu-id="6498b-144">The *DoNotAllowDemandStart* parameter sets the value of the DoNotAllowDemandStart property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="6498b-145">-HideInTaskScheduler</span><span class="sxs-lookup"><span data-stu-id="6498b-145">-HideInTaskScheduler</span></span>
<span data-ttu-id="6498b-146">不要在 [工作排程器] 中顯示工作。</span><span class="sxs-lookup"><span data-stu-id="6498b-146">Do not display the job in Task Scheduler.</span></span>
<span data-ttu-id="6498b-147">此值只會影響工作執行所在電腦。</span><span class="sxs-lookup"><span data-stu-id="6498b-147">This value affects only the computer on which the job runs.</span></span>
<span data-ttu-id="6498b-148">根據預設值，排程工作會出現在 [工作排程器] 中。</span><span class="sxs-lookup"><span data-stu-id="6498b-148">By default, scheduled tasks appear in Task Scheduler.</span></span>

<span data-ttu-id="6498b-149">即使工作是隱藏的，使用者也可以選取工作排程器中的 [顯示隱藏的工作] 選項來顯示工作。</span><span class="sxs-lookup"><span data-stu-id="6498b-149">Even if a task is hidden, users can display the task by selecting the Show hidden tasks view option in Task Scheduler.</span></span>

<span data-ttu-id="6498b-150">*HideInTaskScheduler* 參數會將排程工作的 ShowInTaskScheduler 屬性值設定為 $False。</span><span class="sxs-lookup"><span data-stu-id="6498b-150">The *HideInTaskScheduler* parameter sets the value of the ShowInTaskScheduler property of scheduled jobs to $False.</span></span>

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

### <span data-ttu-id="6498b-151">-IdleDuration</span><span class="sxs-lookup"><span data-stu-id="6498b-151">-IdleDuration</span></span>
<span data-ttu-id="6498b-152">指定工作啟動前的電腦閒置時間長度。</span><span class="sxs-lookup"><span data-stu-id="6498b-152">Specifies how long the computer must be idle before the job starts.</span></span>
<span data-ttu-id="6498b-153">預設值是 10 分鐘。</span><span class="sxs-lookup"><span data-stu-id="6498b-153">The default value is 10 minutes.</span></span>
<span data-ttu-id="6498b-154">若 *IdleTimeout* 值所指定的時間經過之前，電腦閒置時間未達指定的時間長度，則排程工作不會執行 (直到下次排定的時間，如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="6498b-154">If the computer is not idle for the specified duration before the value of *IdleTimeout* expires, the scheduled job does not run until the next scheduled time, if any.</span></span>

<span data-ttu-id="6498b-155">輸入 **TimeSpan** 物件（例如 New-TimeSpan Cmdlet 所產生的物件），或輸入會 \<hours\> \<minutes\> \<seconds\> 自動轉換成 **TimeSpan** 物件的值（以：：格式表示）。</span><span class="sxs-lookup"><span data-stu-id="6498b-155">Enter a **TimeSpan** object, such as one generated by the New-TimeSpan cmdlet, or enter a value in \<hours\>:\<minutes\>:\<seconds\> format  that is automatically converted to a **TimeSpan** object.</span></span>

<span data-ttu-id="6498b-156">若要啟用此值，請使用 *StartIfIdle* 參數。</span><span class="sxs-lookup"><span data-stu-id="6498b-156">To enable this value, use the *StartIfIdle* parameter.</span></span>
<span data-ttu-id="6498b-157">根據預設，排程工作的 StartIfNotIdle 屬性會設定為 $True，Windows PowerShell 會忽略 *IdleDuration* 和 *IdleTimeout* 值。</span><span class="sxs-lookup"><span data-stu-id="6498b-157">By default, the StartIfNotIdle property of scheduled jobs is set to $True and Windows PowerShell ignores the *IdleDuration* and *IdleTimeout* values.</span></span>

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

### <span data-ttu-id="6498b-158">-IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="6498b-158">-IdleTimeout</span></span>
<span data-ttu-id="6498b-159">指定排程工作等候電腦閒置的時間長度。</span><span class="sxs-lookup"><span data-stu-id="6498b-159">Specifies how long the scheduled job waits for the computer to be idle.</span></span>
<span data-ttu-id="6498b-160">若電腦閒置時間未達到由 *IdleDuration* 參數所指定之時間之前，此時間就已經過，則工作不會執行 (直到排定的下次執行間，如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="6498b-160">If this timeout expires before the computer remains idle for the time period that is specified by the *IdleDuration* parameter, the job does not run until the next scheduled time, if any.</span></span>
<span data-ttu-id="6498b-161">預設值是一小時。</span><span class="sxs-lookup"><span data-stu-id="6498b-161">The default value is one hour.</span></span>

<span data-ttu-id="6498b-162">輸入 **TimeSpan** 物件（例如 New-TimeSpan Cmdlet 所產生的物件），或輸入會 \<hours\> \<minutes\> \<seconds\> 自動轉換成 **TimeSpan** 物件的值（以：：格式表示）。</span><span class="sxs-lookup"><span data-stu-id="6498b-162">Enter a **TimeSpan** object, such as one generated by the New-TimeSpan cmdlet, or enter a value in \<hours\>:\<minutes\>:\<seconds\> format that is automatically converted to a **TimeSpan** object.</span></span>

<span data-ttu-id="6498b-163">若要啟用此值，請使用 *StartIfIdle* 參數。</span><span class="sxs-lookup"><span data-stu-id="6498b-163">To enable this value, use the *StartIfIdle* parameter.</span></span>
<span data-ttu-id="6498b-164">根據預設，排程工作的 StartIfNotIdle 屬性會設定為 $True，Windows PowerShell 會忽略 *IdleDuration* 和 *IdleTimeout* 值。</span><span class="sxs-lookup"><span data-stu-id="6498b-164">By default, the StartIfNotIdle property of scheduled jobs is set to $True and Windows PowerShell ignores the *IdleDuration* and *IdleTimeout* values.</span></span>

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

### <span data-ttu-id="6498b-165">-MultipleInstancePolicy</span><span class="sxs-lookup"><span data-stu-id="6498b-165">-MultipleInstancePolicy</span></span>
<span data-ttu-id="6498b-166">決定當排程工作的某個執行個體已在執行時，系統如何回應啟動該排程工作之另一個執行個體的要求。</span><span class="sxs-lookup"><span data-stu-id="6498b-166">Determines how the system responds to a request to start an instance of a scheduled job while another instance of the job is running.</span></span>
<span data-ttu-id="6498b-167">預設值為 IgnoreNew。</span><span class="sxs-lookup"><span data-stu-id="6498b-167">The default value is IgnoreNew.</span></span>
<span data-ttu-id="6498b-168">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="6498b-168">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="6498b-169">IgnoreNew.</span><span class="sxs-lookup"><span data-stu-id="6498b-169">IgnoreNew.</span></span>
<span data-ttu-id="6498b-170">將略過新的工作執行個體。</span><span class="sxs-lookup"><span data-stu-id="6498b-170">The new job instance is ignored.</span></span>
- <span data-ttu-id="6498b-171">Parallel</span><span class="sxs-lookup"><span data-stu-id="6498b-171">Parallel.</span></span>
<span data-ttu-id="6498b-172">將立即啟動新的工作執行個體。</span><span class="sxs-lookup"><span data-stu-id="6498b-172">The new job instance starts immediately.</span></span>
- <span data-ttu-id="6498b-173">佇列。</span><span class="sxs-lookup"><span data-stu-id="6498b-173">Queue.</span></span>
<span data-ttu-id="6498b-174">新的工作執行個體會在目前的執行個體完成時立即啟動。</span><span class="sxs-lookup"><span data-stu-id="6498b-174">The new job instance starts as soon as the current instance completes.</span></span>
- <span data-ttu-id="6498b-175">StopExisting.</span><span class="sxs-lookup"><span data-stu-id="6498b-175">StopExisting.</span></span>
<span data-ttu-id="6498b-176">目前的作業實例會停止，並啟動新的實例。</span><span class="sxs-lookup"><span data-stu-id="6498b-176">The current instance of the job stops and the new instance starts.</span></span>

<span data-ttu-id="6498b-177">必須符合工作排程的所有條件，工作才會執行。</span><span class="sxs-lookup"><span data-stu-id="6498b-177">To run the job, all conditions for the job schedule must be met.</span></span>
<span data-ttu-id="6498b-178">例如，如果不符合 *RequireNetwork* 、 *IdleDuration* 和 *IdleTimeout* 參數所設定的條件，則不論此參數的值為何，工作實例都不會啟動。</span><span class="sxs-lookup"><span data-stu-id="6498b-178">For example, if the conditions that are set by the *RequireNetwork* , *IdleDuration* , and *IdleTimeout* parameters are not satisfied, the job instance is not started, regardless of the value of this parameter.</span></span>

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

### <span data-ttu-id="6498b-179">-RequireNetwork</span><span class="sxs-lookup"><span data-stu-id="6498b-179">-RequireNetwork</span></span>
<span data-ttu-id="6498b-180">只有在網路連線可以使用時才執行排程工作。</span><span class="sxs-lookup"><span data-stu-id="6498b-180">Runs the scheduled job only when network connections are available.</span></span>

<span data-ttu-id="6498b-181">若指定此參數且網路連線在排定的啟動時間無法使用，該工作不會執行 (直到排定的下次啟動時間，如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="6498b-181">If you specify this parameter and the network is not available at the scheduled start time, the job does not run until the next scheduled start time, if any.</span></span>

<span data-ttu-id="6498b-182">*RequireNetwork* 參數會將排程工作的 RunWithoutNetwork 屬性值設定為 $False。</span><span class="sxs-lookup"><span data-stu-id="6498b-182">The *RequireNetwork* parameter sets the value of the RunWithoutNetwork property of scheduled jobs to $False.</span></span>

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

### <span data-ttu-id="6498b-183">-RestartOnIdleResume</span><span class="sxs-lookup"><span data-stu-id="6498b-183">-RestartOnIdleResume</span></span>
<span data-ttu-id="6498b-184">當電腦成為閒置時重新啟動排程工作。</span><span class="sxs-lookup"><span data-stu-id="6498b-184">Restarts a scheduled job when the computer becomes idle.</span></span>
<span data-ttu-id="6498b-185">此參數搭配 *StopIfGoingOffIdle* 參數使用，它可以在電腦成為作用中 (離開閒置狀態) 時暫停執行中的排程工作。</span><span class="sxs-lookup"><span data-stu-id="6498b-185">This parameter works with the *StopIfGoingOffIdle* parameter, which suspends a running scheduled job if the computer becomes active (leaves the idle state).</span></span>

<span data-ttu-id="6498b-186">*RestartOnIdleResume* 參數會將排程工作的 RestartOnIdleResume 屬性值設定為 $True。</span><span class="sxs-lookup"><span data-stu-id="6498b-186">The *RestartOnIdleResume* parameter sets the value of the RestartOnIdleResume property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="6498b-187">-RunElevated</span><span class="sxs-lookup"><span data-stu-id="6498b-187">-RunElevated</span></span>
<span data-ttu-id="6498b-188">使用工作執行所在電腦上 Administrators 群組成員的權限執行排程工作。</span><span class="sxs-lookup"><span data-stu-id="6498b-188">Runs the scheduled job with the permissions of a member of the Administrators group on the computer on which the job runs.</span></span>

<span data-ttu-id="6498b-189">若要讓排程工作以系統管理員許可權執行，請使用 Register-ScheduledJob 的 *credential* 參數來提供作業的明確認證。</span><span class="sxs-lookup"><span data-stu-id="6498b-189">To enable a scheduled job to run with Administrator permissions, use the *Credential* parameter of Register-ScheduledJob to provide explicit credential for the job.</span></span>

<span data-ttu-id="6498b-190">*RunElevated* 參數會將排程工作的 RunElevated 屬性值設定為 $True。</span><span class="sxs-lookup"><span data-stu-id="6498b-190">The *RunElevated* parameter sets the value of the RunElevated property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="6498b-191">-StartIfIdle</span><span class="sxs-lookup"><span data-stu-id="6498b-191">-StartIfIdle</span></span>
<span data-ttu-id="6498b-192">若電腦已閒置 *IdleDuration* 參數所指定的時間，但 *IdleTimeout* 參數所指定的時間尚未經過，則啟動排程工作。</span><span class="sxs-lookup"><span data-stu-id="6498b-192">Starts the scheduled job if the computer has been idle for the time specified by the *IdleDuration* parameter before the time specified by the *IdleTimeout* parameter expires.</span></span>

<span data-ttu-id="6498b-193">根據預設值，系統會略過 *IdleDuration* 與 *IdleTimeout* 參數，且工作會在排定的開始時間執行 (即使電腦忙碌中)。</span><span class="sxs-lookup"><span data-stu-id="6498b-193">By default, the *IdleDuration* and *IdleTimeout* parameters are ignored and the job starts at the scheduled start time even if the computer is busy.</span></span>

<span data-ttu-id="6498b-194">若指定此參數且電腦在排定的開始時間為忙碌中 (非閒置)，則工作不會執行 (直到排定的下次開始時間，如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="6498b-194">If you specify this parameter and the computer is busy (not idle) at the scheduled start time, the job does not run until the next scheduled start time, if any.</span></span>

<span data-ttu-id="6498b-195">*StartIfIdle* 參數會將排程工作的 StartIfNotIdle 屬性值設定為 $False。</span><span class="sxs-lookup"><span data-stu-id="6498b-195">The *StartIfIdle* parameter sets the value of the StartIfNotIdle property of scheduled jobs to $False.</span></span>

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

### <span data-ttu-id="6498b-196">-StartIfOnBattery</span><span class="sxs-lookup"><span data-stu-id="6498b-196">-StartIfOnBattery</span></span>
<span data-ttu-id="6498b-197">即使電腦在排定的開始時間是使用電池電力執行，也啟動排程工作。</span><span class="sxs-lookup"><span data-stu-id="6498b-197">Starts the scheduled job even if the computer is running on batteries at the scheduled start time.</span></span>
<span data-ttu-id="6498b-198">預設值為 $False。</span><span class="sxs-lookup"><span data-stu-id="6498b-198">The default value is $False.</span></span>

<span data-ttu-id="6498b-199">*StartIfOnBattery* 參數會將排程工作的 StartIfOnBatteries 屬性值設定為 $True。</span><span class="sxs-lookup"><span data-stu-id="6498b-199">The *StartIfOnBattery* parameter sets the value of the StartIfOnBatteries property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="6498b-200">-StopIfGoingOffIdle</span><span class="sxs-lookup"><span data-stu-id="6498b-200">-StopIfGoingOffIdle</span></span>
<span data-ttu-id="6498b-201">若電腦在工作正在執行時成為作用中 (非閒置)，則暫停執行中的排程工作。</span><span class="sxs-lookup"><span data-stu-id="6498b-201">Suspends a running scheduled job if the computer becomes active (not idle) while the job is running.</span></span>

<span data-ttu-id="6498b-202">根據預設值，當電腦再度進入閒置狀態時，當初在電腦成為作用中時暫停的排程工作會繼續執行。</span><span class="sxs-lookup"><span data-stu-id="6498b-202">By default, a scheduled job that is suspended when the computer becomes active resumes when the computer becomes idle again.</span></span>
<span data-ttu-id="6498b-203">若要變更此預設行為，請使用 *RestartOnIdleResume* 參數。</span><span class="sxs-lookup"><span data-stu-id="6498b-203">To change this default behavior, use the *RestartOnIdleResume* parameter.</span></span>

<span data-ttu-id="6498b-204">*StopIfGoingOffIdle* 參數會將排程工作的 StopIfGoingOffIdle 屬性值設定為 $True。</span><span class="sxs-lookup"><span data-stu-id="6498b-204">The *StopIfGoingOffIdle* parameter sets the value of the StopIfGoingOffIdle property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="6498b-205">-WakeToRun</span><span class="sxs-lookup"><span data-stu-id="6498b-205">-WakeToRun</span></span>
<span data-ttu-id="6498b-206">在到了排定的開始時間時將電腦從休眠或睡眠狀態喚醒以執行工作。</span><span class="sxs-lookup"><span data-stu-id="6498b-206">Wakes the computer from a Hibernate or Sleep state at the scheduled start time so it can run the job.</span></span>
<span data-ttu-id="6498b-207">根據預設值，在到了排定的開始時間時，若電腦處於休眠或睡眠狀態，則工作不會執行。</span><span class="sxs-lookup"><span data-stu-id="6498b-207">By default, if the computer is in a Hibernate or Sleep state at the scheduled start time, the job does not run.</span></span>

<span data-ttu-id="6498b-208">*WakeToRun* 參數會將排程工作的 WakeToRun 屬性值設定為 $True。</span><span class="sxs-lookup"><span data-stu-id="6498b-208">The *WakeToRun* parameter sets the value of the WakeToRun property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="6498b-209">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6498b-209">CommonParameters</span></span>
<span data-ttu-id="6498b-210">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="6498b-210">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6498b-211">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="6498b-211">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6498b-212">輸入</span><span class="sxs-lookup"><span data-stu-id="6498b-212">INPUTS</span></span>

### <span data-ttu-id="6498b-213">無</span><span class="sxs-lookup"><span data-stu-id="6498b-213">None</span></span>
<span data-ttu-id="6498b-214">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6498b-214">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="6498b-215">輸出</span><span class="sxs-lookup"><span data-stu-id="6498b-215">OUTPUTS</span></span>

### <span data-ttu-id="6498b-216">Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions</span><span class="sxs-lookup"><span data-stu-id="6498b-216">Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions</span></span>

## <span data-ttu-id="6498b-217">注意</span><span class="sxs-lookup"><span data-stu-id="6498b-217">NOTES</span></span>

* <span data-ttu-id="6498b-218">您可以使用 **ScheduledJobOption** 所建立的 **ScheduledJobOptions** 物件，做為 Register-ScheduledJob Cmdlet 的 *ScheduledJobOption* 參數值。</span><span class="sxs-lookup"><span data-stu-id="6498b-218">You can use the **ScheduledJobOptions** object that **New-ScheduledJobOption** creates as the value of the *ScheduledJobOption* parameter of the Register-ScheduledJob cmdlet.</span></span> <span data-ttu-id="6498b-219">不過， *ScheduledJobOption* 參數也可以採用雜湊表值來指定 **ScheduledJobOptions** 物件的屬性及其值，例如：</span><span class="sxs-lookup"><span data-stu-id="6498b-219">However, the *ScheduledJobOption* parameter can also take a hash table value that specifies the properties of the **ScheduledJobOptions** object and their values, such as:</span></span>

  `@{ShowInTaskScheduler=$False; RunElevated=$True; IdleDuration="00:05"}`

## <span data-ttu-id="6498b-220">相關連結</span><span class="sxs-lookup"><span data-stu-id="6498b-220">RELATED LINKS</span></span>

[<span data-ttu-id="6498b-221">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="6498b-221">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="6498b-222">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="6498b-222">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="6498b-223">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="6498b-223">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="6498b-224">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="6498b-224">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="6498b-225">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="6498b-225">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="6498b-226">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="6498b-226">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="6498b-227">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="6498b-227">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="6498b-228">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="6498b-228">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="6498b-229">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="6498b-229">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="6498b-230">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="6498b-230">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="6498b-231">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="6498b-231">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="6498b-232">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="6498b-232">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="6498b-233">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="6498b-233">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="6498b-234">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="6498b-234">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="6498b-235">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="6498b-235">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="6498b-236">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="6498b-236">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
