---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/new-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-JobTrigger
ms.openlocfilehash: de49ab937c6f3a8187f5aecd6aafc81425b8cd00
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202999"
---
# <span data-ttu-id="772bd-103">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="772bd-103">New-JobTrigger</span></span>

## <span data-ttu-id="772bd-104">概要</span><span class="sxs-lookup"><span data-stu-id="772bd-104">SYNOPSIS</span></span>
<span data-ttu-id="772bd-105">建立排程工作的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="772bd-105">Creates a job trigger for a scheduled job.</span></span>

## <span data-ttu-id="772bd-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="772bd-106">SYNTAX</span></span>

### <span data-ttu-id="772bd-107"> (預設值之後) </span><span class="sxs-lookup"><span data-stu-id="772bd-107">Once (Default)</span></span>

```
New-JobTrigger [-RandomDelay <TimeSpan>] -At <DateTime> [-Once] [-RepetitionInterval <TimeSpan>]
 [-RepetitionDuration <TimeSpan>] [-RepeatIndefinitely] [<CommonParameters>]
```

### <span data-ttu-id="772bd-108">每日</span><span class="sxs-lookup"><span data-stu-id="772bd-108">Daily</span></span>

```
New-JobTrigger [-DaysInterval <Int32>] [-RandomDelay <TimeSpan>] -At <DateTime> [-Daily] [<CommonParameters>]
```

### <span data-ttu-id="772bd-109">每週</span><span class="sxs-lookup"><span data-stu-id="772bd-109">Weekly</span></span>

```
New-JobTrigger [-WeeksInterval <Int32>] [-RandomDelay <TimeSpan>] -At <DateTime> -DaysOfWeek <DayOfWeek[]>
 [-Weekly] [<CommonParameters>]
```

### <span data-ttu-id="772bd-110">AtStartup</span><span class="sxs-lookup"><span data-stu-id="772bd-110">AtStartup</span></span>

```
New-JobTrigger [-RandomDelay <TimeSpan>] [-AtStartup] [<CommonParameters>]
```

### <span data-ttu-id="772bd-111">AtLogon</span><span class="sxs-lookup"><span data-stu-id="772bd-111">AtLogon</span></span>

```
New-JobTrigger [-RandomDelay <TimeSpan>] [-User <String>] [-AtLogOn] [<CommonParameters>]
```

## <span data-ttu-id="772bd-112">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="772bd-112">DESCRIPTION</span></span>
<span data-ttu-id="772bd-113">**Enable-jobtrigger 指令程式** 會建立工作觸發程式，以一次性或週期性排程來啟動排程工作，或在事件發生時啟動排程工作。</span><span class="sxs-lookup"><span data-stu-id="772bd-113">The **New-JobTrigger** cmdlet creates a job trigger that starts a scheduled job on a one-time or recurring schedule, or when an event occurs.</span></span>

<span data-ttu-id="772bd-114">您可以使用由 **New-JobTrigger** 所傳回的 **ScheduledJobTrigger** 物件為新的排程工作或現有的排程工作設定工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="772bd-114">You can use the **ScheduledJobTrigger** object that **New-JobTrigger** returns to set a job trigger for a new or existing scheduled job.</span></span>
<span data-ttu-id="772bd-115">您也可以使用 Get-JobTrigger Cmdlet 來建立工作觸發程式，以取得現有排程工作的工作觸發程式，或使用雜湊表值來代表工作觸發程式。</span><span class="sxs-lookup"><span data-stu-id="772bd-115">You can also create a job trigger by using the Get-JobTrigger cmdlet to get the job trigger of an existing scheduled job, or by using a hash table value to represent a job trigger.</span></span>

<span data-ttu-id="772bd-116">建立工作觸發程式時，請檢查 New-ScheduledJobOption Cmdlet 所指定之選項的預設值。</span><span class="sxs-lookup"><span data-stu-id="772bd-116">When creating a job trigger, review the default values of the options specified by the New-ScheduledJobOption cmdlet.</span></span>
<span data-ttu-id="772bd-117">這些選項的有效值/預設值與 **Task Scheduler** 中之對應選項的有效值/預設值相同，而且會影響排程工作的排程與執行時間。</span><span class="sxs-lookup"><span data-stu-id="772bd-117">These options, which have the same valid and default values as the corresponding options in **Task Scheduler** , affect the scheduling and timing of scheduled jobs.</span></span>

<span data-ttu-id="772bd-118">**Enable-jobtrigger** 是包含在 Windows PowerShell 之 PSScheduledJob 模組中的其中一個工作排程 Cmdlet 集合。</span><span class="sxs-lookup"><span data-stu-id="772bd-118">**New-JobTrigger** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="772bd-119">如需排程工作的詳細資訊，請參閱 PSScheduledJob 模組中的「關於」主題。</span><span class="sxs-lookup"><span data-stu-id="772bd-119">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="772bd-120">匯入 PSScheduledJob 模組，然後輸入：`Get-Help about_Scheduled*`，或參閱 about_Scheduled_Jobs。</span><span class="sxs-lookup"><span data-stu-id="772bd-120">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="772bd-121">此 Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="772bd-121">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="772bd-122">範例</span><span class="sxs-lookup"><span data-stu-id="772bd-122">EXAMPLES</span></span>

### <span data-ttu-id="772bd-123">範例1：排程</span><span class="sxs-lookup"><span data-stu-id="772bd-123">Example 1: Once Schedule</span></span>

```
PS C:\> New-JobTrigger -Once -At "1/20/2012 3:00 AM"
```

<span data-ttu-id="772bd-124">此命令會使用 **New-JobTrigger** Cmdlet 來建立工作觸發程序，此工作觸發程序會以一次性方式啟動排程工作。</span><span class="sxs-lookup"><span data-stu-id="772bd-124">This command uses the **New-JobTrigger** cmdlet to create a job trigger that starts a scheduled job only one time.</span></span>
<span data-ttu-id="772bd-125">*At* 參數的值是 Windows PowerShell 轉換為 **DateTime** 物件的字串。</span><span class="sxs-lookup"><span data-stu-id="772bd-125">The value of the *At* parameter is a string that Windows PowerShell converts into a **DateTime** object.</span></span>
<span data-ttu-id="772bd-126">*At* 參數值包含明確的日期，不只是時間。</span><span class="sxs-lookup"><span data-stu-id="772bd-126">The *At* parameter value includes an explicit date, not just a time.</span></span>
<span data-ttu-id="772bd-127">若省略日期，則會以目前日期與上午 3:00 的時間建立觸發程序，這可能代表過去的時間。</span><span class="sxs-lookup"><span data-stu-id="772bd-127">If the date were omitted, the trigger would be created with the current date and 3:00 AM time, which is likely to represent a time in the past.</span></span>

### <span data-ttu-id="772bd-128">範例2：每日排程</span><span class="sxs-lookup"><span data-stu-id="772bd-128">Example 2: Daily Schedule</span></span>

```
PS C:\> New-JobTrigger -Daily -At "4:15 AM" -DaysInterval 3
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
0          Daily           9/21/2012 4:15:00 AM                           True
```

<span data-ttu-id="772bd-129">此命令會建立每隔 3 天在上午 4:15 啟動排程工作的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="772bd-129">This command creates a job trigger that starts a scheduled job every 3 days at 4:15 a.m.</span></span>

<span data-ttu-id="772bd-130">因為 *At* 參數的值不包含日期，會使用目前日期做為 **DateTime** 物件中的日期值。</span><span class="sxs-lookup"><span data-stu-id="772bd-130">Because the value of the *At* parameter does not include a date, the current date is used as the date value in the **DateTime** object.</span></span>
<span data-ttu-id="772bd-131">若日期和時間為過去時間，則排程工作會在排定的下次執行時間啟動，亦即自 *At* 參數值起的三天後。</span><span class="sxs-lookup"><span data-stu-id="772bd-131">If the date and time is in the past, the scheduled job is started at the next occurrence, which is 3 days later from the *At* parameter value.</span></span>

### <span data-ttu-id="772bd-132">範例3：每週排程</span><span class="sxs-lookup"><span data-stu-id="772bd-132">Example 3: Weekly Schedule</span></span>

```
PS C:\> New-JobTrigger -Weekly -DaysOfWeek Monday, Wednesday, Friday -At "23:00" -WeeksInterval 4
Id Frequency Time                  DaysOfWeek                  Enabled
-- --------- ----                  ----------                  -------
0  Weekly    9/21/2012 11:00:00 PM {Monday, Wednesday, Friday} True
```

<span data-ttu-id="772bd-133">此命令會建立每隔四週在星期一、星期三與星期五 23:00 (下午 11:00) 啟動排程工作的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="772bd-133">This command creates a job trigger that starts a scheduled job every 4 weeks on Monday, Wednesday, and Friday at 2300 hours (11:00 PM).</span></span>

<span data-ttu-id="772bd-134">您也可以在整數中輸入 *DaysOfWeek* 參數值，例如 `-DaysOfWeek 1, 5` 。</span><span class="sxs-lookup"><span data-stu-id="772bd-134">You can also enter the *DaysOfWeek* parameter value in integers, such as `-DaysOfWeek 1, 5`.</span></span>

### <span data-ttu-id="772bd-135">範例4：登入排程</span><span class="sxs-lookup"><span data-stu-id="772bd-135">Example 4: Logon Schedule</span></span>

```
PS C:\> New-JobTrigger -AtLogOn -User Domain01\Admin01
```

<span data-ttu-id="772bd-136">此命令會建立在網域系統管理員登入電腦時執行排程工作的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="772bd-136">This command creates a job trigger that starts a scheduled job whenever the domain administrator logs onto the computer.</span></span>

### <span data-ttu-id="772bd-137">範例5：使用隨機延遲</span><span class="sxs-lookup"><span data-stu-id="772bd-137">Example 5: Using a Random Delay</span></span>

```
PS C:\> New-JobTrigger -Daily -At 1:00 -RandomDelay 00:20:00
```

<span data-ttu-id="772bd-138">此命令會建立在每天凌晨 1:00 啟動排程工作的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="772bd-138">This command creates a job trigger that starts a scheduled job every day at 1:00 in the morning.</span></span>
<span data-ttu-id="772bd-139">此命令會使用 *RandomDelay* 參數將最大延遲設定為 20 分鐘。</span><span class="sxs-lookup"><span data-stu-id="772bd-139">The command uses the *RandomDelay* parameter to set the maximum delay to 20 minutes.</span></span>
<span data-ttu-id="772bd-140">因此，該工作會在每天凌晨 1:00 到凌晨 1:20 之間執行，且間隔為隨機指定。</span><span class="sxs-lookup"><span data-stu-id="772bd-140">As a result, the job runs every day between 1:00 AM and 1:20 AM, with the interval varying pseudo-randomly.</span></span>

<span data-ttu-id="772bd-141">您可以將隨機延遲用於取樣、負載平衡與其他系統管理工作。</span><span class="sxs-lookup"><span data-stu-id="772bd-141">You can use a random delay for sampling, load balancing, and other administrative tasks.</span></span>
<span data-ttu-id="772bd-142">設定延遲值時，請檢查 New-ScheduledJobOption Cmdlet 的有效和預設值，並協調延遲與選項設定。</span><span class="sxs-lookup"><span data-stu-id="772bd-142">When setting the delay value, review the effective and default values of the New-ScheduledJobOption cmdlet and coordinate the delay with the option settings.</span></span>

### <span data-ttu-id="772bd-143">範例6：建立新排程工作的工作觸發程式</span><span class="sxs-lookup"><span data-stu-id="772bd-143">Example 6: Create a Job Trigger for a New Scheduled Job</span></span>

```
The first command uses the **New-JobTrigger** cmdlet to create a job trigger that starts a job every Monday, Wednesday, and Friday at 12:01 AM. The command saves the job trigger in the $T variable.
PS C:\> $T = New-JobTrigger -Weekly -DaysOfWeek 1,3,5 -At 12:01AM


The second command uses the Register-ScheduledJob cmdlet to create a scheduled job that starts a job every Monday, Wednesday, and Friday at 12:01 AM. The value of the *Trigger* parameter is the trigger that is stored in the $T variable.
PS C:\> Register-ScheduledJob -Name Test-HelpFiles -FilePath C:\Scripts\Test-HelpFiles.ps1 -Trigger $T
```

<span data-ttu-id="772bd-144">這些命令使用工作觸發程序來建立新的排程工作。</span><span class="sxs-lookup"><span data-stu-id="772bd-144">These commands use a job trigger to create a new scheduled job.</span></span>

### <span data-ttu-id="772bd-145">範例7：將工作觸發程式新增至排程工作</span><span class="sxs-lookup"><span data-stu-id="772bd-145">Example 7: Add a Job Trigger to a Scheduled Job</span></span>

```
PS C:\> Add-JobTrigger -Name SynchronizeApps -Trigger (New-JobTrigger -Daily -At 3:10AM)
```

<span data-ttu-id="772bd-146">此範例顯示如何將工作觸發程序新增到現有的排程工作。</span><span class="sxs-lookup"><span data-stu-id="772bd-146">This example shows how to add a job trigger to an existing scheduled job.</span></span>
<span data-ttu-id="772bd-147">您可以將多個工作觸發程序新增到任何排程工作。</span><span class="sxs-lookup"><span data-stu-id="772bd-147">You can add multiple job triggers to any scheduled job.</span></span>

<span data-ttu-id="772bd-148">此命令會使用 Add-JobTrigger Cmdlet，將工作觸發程式新增至 SynchronizeApps 排程工作。</span><span class="sxs-lookup"><span data-stu-id="772bd-148">The command uses the Add-JobTrigger cmdlet to add the job trigger to the SynchronizeApps scheduled job.</span></span>
<span data-ttu-id="772bd-149">*Trigger* 參數的值是 **New-JobTrigger** 命令，此命令會在每天上午 3:10 執行工作。</span><span class="sxs-lookup"><span data-stu-id="772bd-149">The value of the *Trigger* parameter is a **New-JobTrigger** command that runs the job every day at 3:10 AM.</span></span>

<span data-ttu-id="772bd-150">當命令完成時，SynchronizeApps 是在由工作觸發程序所指定之時間執行的排程工作。</span><span class="sxs-lookup"><span data-stu-id="772bd-150">When the command completes, SynchronizeApps is a scheduled job that runs at the times specified by the job trigger.</span></span>

### <span data-ttu-id="772bd-151">範例8：建立重複的工作觸發程式</span><span class="sxs-lookup"><span data-stu-id="772bd-151">Example 8: Create a repeating job trigger</span></span>

```
PS C:\> New-JobTrigger -Once -At "09/12/2013 1:00:00" -RepetitionInterval (New-TimeSpan -Hours 1) -RepetitionDuration (New-Timespan -Hours 48)
```

<span data-ttu-id="772bd-152">此命令會建立每隔 60 48 分鐘執行一次工作的工作觸發程式2013，從年9月12日（上午1:00）開始。</span><span class="sxs-lookup"><span data-stu-id="772bd-152">This command creates a job trigger that runs a job every 60 minutes for 48 hours beginning on September 12, 2013 at 1:00 AM.</span></span>

### <span data-ttu-id="772bd-153">範例9：停止重複的工作觸發程式</span><span class="sxs-lookup"><span data-stu-id="772bd-153">Example 9: Stop a repeating job trigger</span></span>

```
PS C:\> Get-JobTrigger -Name SecurityCheck | Set-JobTrigger -RepetitionInterval 0:00 -RepetitionDuration 0:00
```

<span data-ttu-id="772bd-154">此命令會強制停止 SecurityCheck 工作，此工作是觸發為每隔 60 分鐘執行一次，直到其工作觸發程序過期。</span><span class="sxs-lookup"><span data-stu-id="772bd-154">This command forcibly stops the SecurityCheck job, which is triggered to run every 60 minutes until its job trigger expires.</span></span>

<span data-ttu-id="772bd-155">為了避免重複作業，此命令會使用 Get-JobTrigger 取得 SecurityCheck 作業的工作觸發程式，並使用 Set-JobTrigger Cmdlet 將工作觸發程式的重複間隔和重複期間變更為零 (0) 。</span><span class="sxs-lookup"><span data-stu-id="772bd-155">To prevent the job from repeating, the command uses the Get-JobTrigger to get the job trigger of the SecurityCheck job and the Set-JobTrigger cmdlet to change the repetition interval and repetition duration of the job trigger to zero (0).</span></span>

### <span data-ttu-id="772bd-156">範例10：建立每小時工作觸發程式</span><span class="sxs-lookup"><span data-stu-id="772bd-156">Example 10: Create an hourly job trigger</span></span>

```
PS C:\> New-JobTrigger -Once -At "9/21/2012 0am" -RepetitionInterval (New-TimeSpan -Hour 12) -RepetitionDuration ([TimeSpan]::MaxValue)
```

<span data-ttu-id="772bd-157">下列命令會建立工作觸發程序，此工作觸發程序會以無終止時間的方式每隔 12 小時執行排程工作。</span><span class="sxs-lookup"><span data-stu-id="772bd-157">The following command creates a job trigger that runs a scheduled job once every 12 hours for an indefinite period of time.</span></span>
<span data-ttu-id="772bd-158">該排程是從明天 (9/21/2012) 午夜 (上午 0:00) 開始。</span><span class="sxs-lookup"><span data-stu-id="772bd-158">The schedule begins tomorrow (9/21/2012) at midnight (0:00 AM).</span></span>

## <span data-ttu-id="772bd-159">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="772bd-159">PARAMETERS</span></span>

### <span data-ttu-id="772bd-160">-At</span><span class="sxs-lookup"><span data-stu-id="772bd-160">-At</span></span>
<span data-ttu-id="772bd-161">在指定的日期和時間啟動工作。</span><span class="sxs-lookup"><span data-stu-id="772bd-161">Starts the job at the specified date and time.</span></span>
<span data-ttu-id="772bd-162">輸入 **DateTime** 物件（例如 Get-Date Cmdlet 傳回的物件），或是可轉換成日期和時間的字串，例如 "4 月19日、2012 15:00"、"12/31" 或 "3am"。</span><span class="sxs-lookup"><span data-stu-id="772bd-162">Enter a **DateTime** object, such as one that the Get-Date cmdlet returns, or a string that can be converted to a date and time, such as "April 19, 2012 15:00", "12/31", or "3am".</span></span>
<span data-ttu-id="772bd-163">若未指定日期的元素 (例如年)，觸發程序中的日期會具有與目前日期對應的元素。</span><span class="sxs-lookup"><span data-stu-id="772bd-163">If you don't specify an element of the date, such as the year, the date in the trigger has the corresponding element from the current date.</span></span>

<span data-ttu-id="772bd-164">使用 *Once* 參數時，將 *At* 參數的值設定為未來的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="772bd-164">When using the *Once* parameter, set the value of the *At* parameter to a future date and time.</span></span>
<span data-ttu-id="772bd-165">因為 **DateTime** 物件中的預設日期是目前日期，若指定目前時間以前的時間且未指定明確的日期，則系統會建立時間為過去時間的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="772bd-165">Because the default date in a **DateTime** object is the current date, if you specify a time before the current time without an explicit date, the job trigger is created for a time in the past.</span></span>

<span data-ttu-id="772bd-166">**DateTime** 物件與轉換為 **DateTime** 物件的字串會自動調整為與為本機電腦所選取的日期和時間格式 (在 [控制台] 中的[地區及語言]) 相容。</span><span class="sxs-lookup"><span data-stu-id="772bd-166">**DateTime** objects, and strings that are converted to **DateTime** objects, are automatically adjusted to be compatible with the date and time formats selected for the local computer in Region and Language in Control Panel.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: Once, Daily, Weekly
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="772bd-167">-AtLogOn</span><span class="sxs-lookup"><span data-stu-id="772bd-167">-AtLogOn</span></span>
<span data-ttu-id="772bd-168">在指定的使用者登入電腦時啟動排程工作。</span><span class="sxs-lookup"><span data-stu-id="772bd-168">Starts the scheduled job when the specified users log on to the computer.</span></span>
<span data-ttu-id="772bd-169">若要指定使用者，請使用 *User* 參數。</span><span class="sxs-lookup"><span data-stu-id="772bd-169">To specify a user, use the *User* parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AtLogon
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="772bd-170">-AtStartup</span><span class="sxs-lookup"><span data-stu-id="772bd-170">-AtStartup</span></span>
<span data-ttu-id="772bd-171">在 Windows 啟動時啟動排程工作。</span><span class="sxs-lookup"><span data-stu-id="772bd-171">Starts the scheduled job when Windows starts.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AtStartup
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="772bd-172">-Daily</span><span class="sxs-lookup"><span data-stu-id="772bd-172">-Daily</span></span>
<span data-ttu-id="772bd-173">指定每日週期性工作排程。</span><span class="sxs-lookup"><span data-stu-id="772bd-173">Specifies a recurring daily job schedule.</span></span>
<span data-ttu-id="772bd-174">使用 *每日* 參數集中的其他參數來指定排程詳細資料。</span><span class="sxs-lookup"><span data-stu-id="772bd-174">Use the other parameters in the *Daily* parameter set to specify the schedule details.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Daily
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="772bd-175">-DaysInterval</span><span class="sxs-lookup"><span data-stu-id="772bd-175">-DaysInterval</span></span>
<span data-ttu-id="772bd-176">在每日排程上指定執行週期間隔天數。</span><span class="sxs-lookup"><span data-stu-id="772bd-176">Specifies the number of days between occurrences on a daily schedule.</span></span>
<span data-ttu-id="772bd-177">例如，3 的值會在第 1、4、7 天啟動排程工作，依此類推。</span><span class="sxs-lookup"><span data-stu-id="772bd-177">For example, a value of 3 starts the scheduled job on days 1, 4, 7 and so on.</span></span>
<span data-ttu-id="772bd-178">預設值為 1。</span><span class="sxs-lookup"><span data-stu-id="772bd-178">The default value is 1.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Daily
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="772bd-179">-DaysOfWeek</span><span class="sxs-lookup"><span data-stu-id="772bd-179">-DaysOfWeek</span></span>
<span data-ttu-id="772bd-180">指定每週排程工作要在星期幾執行。</span><span class="sxs-lookup"><span data-stu-id="772bd-180">Specifies the days of the week on which a weekly scheduled job runs.</span></span>
<span data-ttu-id="772bd-181">輸入星期幾名稱，例如 "Monday" 或 0-6 之間的整數，其中 0 代表 Sunday。</span><span class="sxs-lookup"><span data-stu-id="772bd-181">Enter day names, such as "Monday" or integers 0-6, where 0 represents Sunday.</span></span>
<span data-ttu-id="772bd-182">在 Weekly 參數集中，此為必要參數。</span><span class="sxs-lookup"><span data-stu-id="772bd-182">This parameter is required in the Weekly parameter set.</span></span>

<span data-ttu-id="772bd-183">在工作觸發程序中，星期幾名稱會轉換為其整數值。</span><span class="sxs-lookup"><span data-stu-id="772bd-183">Day names are converted to their integer values in the job trigger.</span></span>
<span data-ttu-id="772bd-184">當您在命令中將星期幾名稱放在引號中時，請將每個星期幾名稱放在各自的引號中，例如 "Monday"、"Tuesday"。</span><span class="sxs-lookup"><span data-stu-id="772bd-184">When you enclose day names in quotation marks in a command, enclose each day name in separate quotation marks, such as "Monday", "Tuesday".</span></span>
<span data-ttu-id="772bd-185">若將多個星期幾名稱放在一組引號中，則會加總對應的整數值。</span><span class="sxs-lookup"><span data-stu-id="772bd-185">If you enclose multiple day names in a single quotation mark pair, the corresponding integer values are summed.</span></span>
<span data-ttu-id="772bd-186">例如，"Monday, Tuesday" (1, 2) 會產生 "Wednesday" (3) 的值。</span><span class="sxs-lookup"><span data-stu-id="772bd-186">For example, "Monday, Tuesday" (1, 2) results in a value of "Wednesday" (3).</span></span>

```yaml
Type: System.DayOfWeek[]
Parameter Sets: Weekly
Aliases:
Accepted values: Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="772bd-187">-Once</span><span class="sxs-lookup"><span data-stu-id="772bd-187">-Once</span></span>
<span data-ttu-id="772bd-188">指定非週期性 (一次性) 或自訂重複性排程。</span><span class="sxs-lookup"><span data-stu-id="772bd-188">Specifies a non-recurring (one time) or custom repeating schedule.</span></span>
<span data-ttu-id="772bd-189">若要建立重複性排程，請使用 *Once* 參數搭配 *RepetitionDuration* 與 *RepetitionInterval* 參數。</span><span class="sxs-lookup"><span data-stu-id="772bd-189">To create a repeating schedule, use the *Once* parameter with the *RepetitionDuration* and *RepetitionInterval* parameters.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Once
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="772bd-190">-RandomDelay</span><span class="sxs-lookup"><span data-stu-id="772bd-190">-RandomDelay</span></span>
<span data-ttu-id="772bd-191">啟用排定的開始時間前的隨機延遲，並設定最大延遲值。</span><span class="sxs-lookup"><span data-stu-id="772bd-191">Enables a random delay that begins at the scheduled start time, and sets the maximum delay value.</span></span>
<span data-ttu-id="772bd-192">延遲長度是在每次開始前隨機設定，其值介於無延遲到此參數值所指定的時間之間。</span><span class="sxs-lookup"><span data-stu-id="772bd-192">The length of the delay is set pseudo-randomly for each start and varies from no delay to the time specified by the value of this parameter.</span></span>
<span data-ttu-id="772bd-193">預設值零 (00:00:00) 會停用隨機延遲。</span><span class="sxs-lookup"><span data-stu-id="772bd-193">The default value, zero (00:00:00), disables the random delay.</span></span>

<span data-ttu-id="772bd-194">輸入 timespan 物件（例如 New-TimeSpan Cmdlet 所傳回的物件），或輸入 \<hours\> ： \<minutes\> ： format 格式的值 \<seconds\> ，此物件會自動轉換為 **timespan** 物件。</span><span class="sxs-lookup"><span data-stu-id="772bd-194">Enter a timespan object, such as one returned by the New-TimeSpan cmdlet, or enter a value in \<hours\>:\<minutes\>:\<seconds\> format, which is automatically converted to a **TimeSpan** object.</span></span>

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

### <span data-ttu-id="772bd-195">-RepeatIndefinitely</span><span class="sxs-lookup"><span data-stu-id="772bd-195">-RepeatIndefinitely</span></span>
<span data-ttu-id="772bd-196">若要重複執行無終止時間之排程工作，使用此參數 (從 Windows PowerShell 4.0 開始提供) 可取代為 **RepetitionDuration** 參數指定 *TimeSpan.MaxValue* 值。</span><span class="sxs-lookup"><span data-stu-id="772bd-196">This parameter, available starting in Windows PowerShell 4.0, eliminates the necessity of specifying a **TimeSpan.MaxValue** value for the *RepetitionDuration* parameter to run a scheduled job repeatedly, for an indefinite period.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Once
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="772bd-197">-RepetitionDuration</span><span class="sxs-lookup"><span data-stu-id="772bd-197">-RepetitionDuration</span></span>
<span data-ttu-id="772bd-198">重複執行工作，直到經過指定的時間。</span><span class="sxs-lookup"><span data-stu-id="772bd-198">Repeats the job until the specified time expires.</span></span>
<span data-ttu-id="772bd-199">重複頻率是由 *RepetitionInterval* 參數的值指定。</span><span class="sxs-lookup"><span data-stu-id="772bd-199">The repetition frequency is determined by the value of the *RepetitionInterval* parameter.</span></span>
<span data-ttu-id="772bd-200">例如，若 **RepetitionInterval** 的值是 5 分鐘且 **RepetitionDuration** 的值是 2 小時，則在兩小時內，每隔五分鐘會觸發該工作。</span><span class="sxs-lookup"><span data-stu-id="772bd-200">For example, if the value of **RepetitionInterval** is 5 minutes and the value of **RepetitionDuration** is 2 hours, the job is triggered every five minutes for two hours.</span></span>

<span data-ttu-id="772bd-201">輸入 timespan 物件 (例如 New-TimeSpan Cmdlet 傳回的物件) 或可轉換為 timespan 物件的字串 (例如 "1:05:30")。</span><span class="sxs-lookup"><span data-stu-id="772bd-201">Enter a timespan object, such as one that the New-TimeSpan cmdlet returns or a string that can be converted to a timespan object, such as "1:05:30".</span></span>

<span data-ttu-id="772bd-202">若要以無終止時間方式執行工作，請改為新增 *RepeatIndefinitely* 參數。</span><span class="sxs-lookup"><span data-stu-id="772bd-202">To run a job indefinitely, add the *RepeatIndefinitely* parameter instead.</span></span>

<span data-ttu-id="772bd-203">若要在工作觸發程式重複期間過期之前停止工作，請使用 Set-JobTrigger Cmdlet 將 *RepetitionDuration* 值設定為零 (0) 。</span><span class="sxs-lookup"><span data-stu-id="772bd-203">To stop a job before the job trigger repetition duration expires, use the Set-JobTrigger cmdlet to set the *RepetitionDuration* value to zero (0).</span></span>

<span data-ttu-id="772bd-204">只有當已在命令中使用 *Once* 、 *At* 與 *RepetitionInterval* 參數時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="772bd-204">This parameter is valid only when the *Once* , *At* and *RepetitionInterval* parameters are used in the command.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: Once
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="772bd-205">-RepetitionInterval</span><span class="sxs-lookup"><span data-stu-id="772bd-205">-RepetitionInterval</span></span>
<span data-ttu-id="772bd-206">以指定的時間間隔重複執行工作。</span><span class="sxs-lookup"><span data-stu-id="772bd-206">Repeats the job at the specified time interval.</span></span>
<span data-ttu-id="772bd-207">例如，若此參數的值是設定為 2 小時，則每隔兩小時會觸發一次工作。</span><span class="sxs-lookup"><span data-stu-id="772bd-207">For example, if the value of this parameter is 2 hours, the job is triggered every two hours.</span></span>
<span data-ttu-id="772bd-208">預設值 0 不會重複執行工作。</span><span class="sxs-lookup"><span data-stu-id="772bd-208">The default value, 0, does not repeat the job.</span></span>

<span data-ttu-id="772bd-209">輸入 timespan 物件 (例如 New-TimeSpan Cmdlet 傳回的物件) 或可轉換為 timespan 物件的字串 (例如 "1:05:30")。</span><span class="sxs-lookup"><span data-stu-id="772bd-209">Enter a timespan object, such as one that the New-TimeSpan cmdlet returns or a string that can be converted to a timespan object, such as "1:05:30".</span></span>

<span data-ttu-id="772bd-210">只有當已在命令中使用 *Once* 、 *At* 與 *RepetitionDuration* 參數時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="772bd-210">This parameter is valid only when the *Once* , *At* , and *RepetitionDuration* parameters are used in the command.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: Once
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="772bd-211">-User</span><span class="sxs-lookup"><span data-stu-id="772bd-211">-User</span></span>
<span data-ttu-id="772bd-212">指定觸發 *AtLogon* 排程工作啟動的使用者。</span><span class="sxs-lookup"><span data-stu-id="772bd-212">Specifies the users who trigger an *AtLogon* start of a scheduled job.</span></span>
<span data-ttu-id="772bd-213">以或格式輸入使用者的名稱 \<UserName\> ， \<Domain\Username\> 或輸入星號 (\*) 代表所有使用者。</span><span class="sxs-lookup"><span data-stu-id="772bd-213">Enter the name of a user in \<UserName\> or \<Domain\Username\> format or enter an asterisk (\*) to represent all users.</span></span>
<span data-ttu-id="772bd-214">預設值是所有使用者。</span><span class="sxs-lookup"><span data-stu-id="772bd-214">The default value is all users.</span></span>

```yaml
Type: System.String
Parameter Sets: AtLogon
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="772bd-215">-Weekly</span><span class="sxs-lookup"><span data-stu-id="772bd-215">-Weekly</span></span>
<span data-ttu-id="772bd-216">指定週期性每週工作排程。</span><span class="sxs-lookup"><span data-stu-id="772bd-216">Specifies a recurring weekly job schedule.</span></span>
<span data-ttu-id="772bd-217">使用 Weekly 參數中的其他參數來指定排程詳細資料。</span><span class="sxs-lookup"><span data-stu-id="772bd-217">Use the other parameters in the Weekly parameter set to specify the schedule details.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Weekly
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="772bd-218">-WeeksInterval</span><span class="sxs-lookup"><span data-stu-id="772bd-218">-WeeksInterval</span></span>
<span data-ttu-id="772bd-219">指定每週工作排程的週次。</span><span class="sxs-lookup"><span data-stu-id="772bd-219">Specifies the number of weeks between occurrences on a weekly job schedule.</span></span>
<span data-ttu-id="772bd-220">例如，3 的值會在第 1、4、7 週啟動排程工作，依此類推。</span><span class="sxs-lookup"><span data-stu-id="772bd-220">For example, a value of 3 starts the scheduled job on weeks 1, 4, 7 and so on.</span></span>
<span data-ttu-id="772bd-221">預設值為 1。</span><span class="sxs-lookup"><span data-stu-id="772bd-221">The default value is 1.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Weekly
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="772bd-222">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="772bd-222">CommonParameters</span></span>
<span data-ttu-id="772bd-223">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="772bd-223">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="772bd-224">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="772bd-224">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="772bd-225">輸入</span><span class="sxs-lookup"><span data-stu-id="772bd-225">INPUTS</span></span>

### <span data-ttu-id="772bd-226">無</span><span class="sxs-lookup"><span data-stu-id="772bd-226">None</span></span>
<span data-ttu-id="772bd-227">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="772bd-227">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="772bd-228">輸出</span><span class="sxs-lookup"><span data-stu-id="772bd-228">OUTPUTS</span></span>

### <span data-ttu-id="772bd-229">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span><span class="sxs-lookup"><span data-stu-id="772bd-229">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span></span>

## <span data-ttu-id="772bd-230">注意</span><span class="sxs-lookup"><span data-stu-id="772bd-230">NOTES</span></span>

* <span data-ttu-id="772bd-231">工作觸發程序不會儲存到磁碟。</span><span class="sxs-lookup"><span data-stu-id="772bd-231">Job triggers are not saved to disk.</span></span> <span data-ttu-id="772bd-232">不過，排程的工作會儲存至磁片，而您可以使用 Get-JobTrigger 取得任何排程工作的工作觸發程式。</span><span class="sxs-lookup"><span data-stu-id="772bd-232">However, scheduled jobs are saved to disk, and you can use the Get-JobTrigger to get the job trigger of any scheduled job.</span></span>
* <span data-ttu-id="772bd-233">**Enable-jobtrigger** 不會防止您建立將不會執行排程工作的工作觸發程式，例如過去日期的一次性觸發程式。</span><span class="sxs-lookup"><span data-stu-id="772bd-233">**New-JobTrigger** does not prevent you from creating a job trigger that will not run a scheduled job, such as one-time trigger for a date in the past.</span></span>
* <span data-ttu-id="772bd-234">Register-ScheduledJob Cmdlet 會接受 >scheduledjobtrigger 物件，例如 **enable-jobtrigger** 或 Get-JobTrigger Cmdlet 所傳回的物件，或具有觸發程式值的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="772bd-234">The Register-ScheduledJob cmdlet accepts a ScheduledJobTrigger object, such as one returned by the **New-JobTrigger** or Get-JobTrigger cmdlets, or a hash table with trigger values.</span></span>

  <span data-ttu-id="772bd-235">若要提交雜湊表，請使用下列索引鍵。</span><span class="sxs-lookup"><span data-stu-id="772bd-235">To submit a hash table, use the following keys.</span></span>

  <span data-ttu-id="772bd-236">`@{Frequency="Once" (or Daily, Weekly, AtStartup, AtLogon);At="3am"` (或任何有效的時間字串) ; `DaysOfWeek="Monday", "Wednesday"` (或日期名稱的任何組合) ; `Interval=2` (或任何有效的頻率間隔) ; `RandomDelay="30minutes"` (或任何有效的 timespan 字串) ; `User="Domain1\User01` (或任何有效的使用者;只能與 *AtLogon* 頻率值搭配使用) }</span><span class="sxs-lookup"><span data-stu-id="772bd-236">`@{Frequency="Once" (or Daily, Weekly, AtStartup, AtLogon);At="3am"` (or any valid time string); `DaysOfWeek="Monday", "Wednesday"` (or any combination of day names); `Interval=2` (or any valid frequency interval); `RandomDelay="30minutes"` (or any valid timespan string); `User="Domain1\User01` (or any valid user; used only with the *AtLogon* frequency value) }</span></span>

## <span data-ttu-id="772bd-237">相關連結</span><span class="sxs-lookup"><span data-stu-id="772bd-237">RELATED LINKS</span></span>

[<span data-ttu-id="772bd-238">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="772bd-238">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="772bd-239">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="772bd-239">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="772bd-240">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="772bd-240">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="772bd-241">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="772bd-241">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="772bd-242">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="772bd-242">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="772bd-243">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="772bd-243">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="772bd-244">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="772bd-244">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="772bd-245">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="772bd-245">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="772bd-246">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="772bd-246">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="772bd-247">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="772bd-247">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="772bd-248">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="772bd-248">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="772bd-249">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="772bd-249">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="772bd-250">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="772bd-250">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="772bd-251">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="772bd-251">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="772bd-252">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="772bd-252">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="772bd-253">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="772bd-253">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
