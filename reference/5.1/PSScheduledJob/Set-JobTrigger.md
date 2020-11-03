---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/set-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-JobTrigger
ms.openlocfilehash: 8d1b12b67ccf695e1c4b948e6eeecf292c588af4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202987"
---
# <span data-ttu-id="947d1-103">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="947d1-103">Set-JobTrigger</span></span>

## <span data-ttu-id="947d1-104">概要</span><span class="sxs-lookup"><span data-stu-id="947d1-104">SYNOPSIS</span></span>
<span data-ttu-id="947d1-105">變更排程工作的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="947d1-105">Changes the job trigger of a scheduled job.</span></span>

## <span data-ttu-id="947d1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="947d1-106">SYNTAX</span></span>

```
Set-JobTrigger [-InputObject] <ScheduledJobTrigger[]> [-DaysInterval <Int32>] [-WeeksInterval <Int32>]
 [-RandomDelay <TimeSpan>] [-At <DateTime>] [-User <String>] [-DaysOfWeek <DayOfWeek[]>] [-AtStartup]
 [-AtLogOn] [-Once] [-RepetitionInterval <TimeSpan>] [-RepetitionDuration <TimeSpan>] [-RepeatIndefinitely]
 [-Daily] [-Weekly] [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="947d1-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="947d1-107">DESCRIPTION</span></span>
<span data-ttu-id="947d1-108">**Set-JobTrigger** Cmdlet 會變更排程工作的工作觸發程序屬性。</span><span class="sxs-lookup"><span data-stu-id="947d1-108">The **Set-JobTrigger** cmdlet changes the properties of the job triggers of scheduled jobs.</span></span>
<span data-ttu-id="947d1-109">您可以使用它來變更工作啟動時間或頻率，或將以時間為基礎的排程變更為依登入或啟動而觸發的排程。</span><span class="sxs-lookup"><span data-stu-id="947d1-109">You can use it to change the time or frequency at which the jobs start or to change from a time-based schedules to schedules that are triggered by a logon or startup.</span></span>

<span data-ttu-id="947d1-110">工作觸發程式會定義用於啟動排程工作的週期性排程或條件。</span><span class="sxs-lookup"><span data-stu-id="947d1-110">A job trigger defines a recurring schedule or conditions for starting a scheduled job.</span></span>
<span data-ttu-id="947d1-111">雖然工作觸發程序不會儲存到磁碟，您可以變更排程工作 (會儲存到磁碟) 的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="947d1-111">Although job triggers are not saved to disk, you can change the job triggers of scheduled jobs, which are saved to disk.</span></span>

<span data-ttu-id="947d1-112">若要變更排程工作的工作觸發程序，請先使用 Get-JobTrigger Cmdlet 取得排程工作的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="947d1-112">To change a job trigger of a scheduled job, begin by using the Get-JobTrigger cmdlet to get the job trigger of a scheduled job.</span></span>
<span data-ttu-id="947d1-113">接著，使用管線傳送觸發程序至 **Set-JobTrigger** ，或將觸發程序儲存在變數中並使用 *Set-JobTrigger* Cmdlet 的 **InputObject** 參數來識別該觸發程序。</span><span class="sxs-lookup"><span data-stu-id="947d1-113">Then, pipe the trigger to **Set-JobTrigger** or save the trigger in a variable and use the *InputObject* parameter of **Set-JobTrigger** cmdlet to identify the trigger.</span></span>
<span data-ttu-id="947d1-114">使用 **Set-JobTrigger** 的其他參數來變更工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="947d1-114">Use the remaining parameters of **Set-JobTrigger** to change the job trigger.</span></span>

<span data-ttu-id="947d1-115">當您變更工作觸發程式的類型時（例如將工作觸發程式從每日或每週觸發程式變更為 *AtLogon* 觸發程式），系統會刪除原始觸發程式屬性。</span><span class="sxs-lookup"><span data-stu-id="947d1-115">When you change the type of a job trigger, such as changing a job trigger from a daily or weekly trigger to an *AtLogon* trigger, the original trigger properties are deleted.</span></span>
<span data-ttu-id="947d1-116">不過，若變更觸發程序的值但未變更其類型 (例如變更每週觸發程序中的星期幾)，則只會變更您指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="947d1-116">However, if you change the values of the trigger, but not its type, such as changing the days in a weekly trigger, only the properties that you specify are changed.</span></span>
<span data-ttu-id="947d1-117">原始工作觸發程序的所有其他屬性會維持不變。</span><span class="sxs-lookup"><span data-stu-id="947d1-117">All other properties of the original job trigger are retained.</span></span>

<span data-ttu-id="947d1-118">**Set-JobTrigger** 為 Windows PowerShell 所包含 PSScheduledJob 模組中的其中一個工作排程 Cmdlet 集合。</span><span class="sxs-lookup"><span data-stu-id="947d1-118">**Set-JobTrigger** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="947d1-119">如需排程工作的詳細資訊，請參閱 PSScheduledJob 模組中的「關於」主題。</span><span class="sxs-lookup"><span data-stu-id="947d1-119">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="947d1-120">匯入 PSScheduledJob 模組，然後輸入：`Get-Help about_Scheduled*`，或參閱 about_Scheduled_Jobs。</span><span class="sxs-lookup"><span data-stu-id="947d1-120">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*`  or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="947d1-121">此 Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="947d1-121">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="947d1-122">範例</span><span class="sxs-lookup"><span data-stu-id="947d1-122">EXAMPLES</span></span>

### <span data-ttu-id="947d1-123">範例 1：變更工作觸發程序中的星期幾</span><span class="sxs-lookup"><span data-stu-id="947d1-123">Example 1: Change the days in a job trigger</span></span>

```
PS C:\> Get-JobTrigger -Name "DeployPackage"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Weekly          9/29/2011 12:00:00 AM  {Wednesday, Saturday}   True

The second command uses the Get-JobTrigger cmdlet to get the job trigger of the DeployPackage scheduled job. A pipeline operator (|) sends the trigger to the **Set-JobTrigger** cmdlet, which changes the job trigger so that it starts the DeployPackage job on Wednesdays and Sundays. The command uses the *Passthru* parameter to return the trigger after the change.
PS C:\> Get-JobTrigger -Name "DeployPackage" | Set-JobTrigger -DaysOfWeek "Wednesday", "Sunday" -Passthru
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Weekly          9/29/2011 12:00:00 AM  {Wednesday, Sunday}     True
```

<span data-ttu-id="947d1-124">此範例顯示如何變更每週工作觸發程序中的星期幾。</span><span class="sxs-lookup"><span data-stu-id="947d1-124">This example shows how to change the days in a weekly job trigger.</span></span>

<span data-ttu-id="947d1-125">第一個命令會使用 Get-JobTrigger Cmdlet 來取得 DeployPackage 排程工作的工作觸發程式。</span><span class="sxs-lookup"><span data-stu-id="947d1-125">The first command uses the Get-JobTrigger cmdlet to get the job trigger of the DeployPackage scheduled job.</span></span>
<span data-ttu-id="947d1-126">輸出會顯示觸發程序在星期三與星期六午夜啟動工作。</span><span class="sxs-lookup"><span data-stu-id="947d1-126">The output shows that the trigger starts the job at midnight on Wednesdays and Saturdays.</span></span>

<span data-ttu-id="947d1-127">此命令並非必要；包含此命令僅為顯示觸發程序變更的效果。</span><span class="sxs-lookup"><span data-stu-id="947d1-127">This command is not required; it is included only to show the effect of the trigger change.</span></span>

### <span data-ttu-id="947d1-128">範例 2：變更工作觸發程序類型</span><span class="sxs-lookup"><span data-stu-id="947d1-128">Example 2: Change the job trigger type</span></span>

```
PS C:\> Get-JobTrigger -Name "Inventory"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Daily           9/27/2011 11:00:00 PM                          True
2          AtStartup                                                      True

The second command uses the **Get-JobTrigger** cmdlet to get the *AtStartup* job trigger of the Inventory job. The command uses the *TriggerID* parameter to identify the job trigger. A pipeline operator (|) sends the job trigger to the **Set-JobTrigger** cmdlet, which changes it to a weekly job trigger that runs every four weeks on Monday at midnight. The command uses the *Passthru* parameter to return the trigger after the change.
PS C:\> Get-JobTrigger -Name "Inventory" -TriggerID 2 | Set-JobTrigger -Weekly -WeeksInterval 4 -DaysOfWeek Monday -At "12:00 AM"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Daily           9/27/2011 11:00:00 PM                          True
2          Weekly          10/31/2011 12:00:00 AM {Monday}                True
```

<span data-ttu-id="947d1-129">此範例顯示如何變更啟動工作之工作觸發程序的類型。</span><span class="sxs-lookup"><span data-stu-id="947d1-129">This example shows how to change the type of job trigger that starts a job.</span></span>
<span data-ttu-id="947d1-130">此範例中的命令會將 AtStartup 工作觸發程序取代為每週觸發程序。</span><span class="sxs-lookup"><span data-stu-id="947d1-130">The commands in this example replace an AtStartup job trigger with a weekly trigger.</span></span>

<span data-ttu-id="947d1-131">第一個命令會使用 Get-JobTrigger Cmdlet 來取得清查排程工作的工作觸發程式。</span><span class="sxs-lookup"><span data-stu-id="947d1-131">The first command uses the Get-JobTrigger cmdlet to get the job trigger of the Inventory scheduled job.</span></span>
<span data-ttu-id="947d1-132">輸出顯示作業的每日觸發程式和 *AtStartup* 觸發程式都有兩個觸發程式。</span><span class="sxs-lookup"><span data-stu-id="947d1-132">The output shows that the job has two triggers a daily trigger and an *AtStartup* trigger.</span></span>

<span data-ttu-id="947d1-133">此命令並非必要；包含此命令僅為顯示觸發程序變更的效果。</span><span class="sxs-lookup"><span data-stu-id="947d1-133">This command is not required; it is included only to show the effect of the trigger change.</span></span>

### <span data-ttu-id="947d1-134">範例 3：變更遠端工作觸發程序的使用者</span><span class="sxs-lookup"><span data-stu-id="947d1-134">Example 3: Change the user on a remote job trigger</span></span>

```
PS C:\> Invoke-Command -ComputerName "Server01" -ScriptBlock {Get-ScheduledJob | Get-JobTrigger | Where-Object {$_.User} | Set-JobTrigger -User "Domain01/Admin02"}
```

<span data-ttu-id="947d1-135">此命令會變更 Server01 電腦上排程工作之所有 *AtLogon* 工作觸發程式中的使用者。</span><span class="sxs-lookup"><span data-stu-id="947d1-135">This command changes the user in all *AtLogon* job triggers of scheduled jobs on the Server01 computer.</span></span>

<span data-ttu-id="947d1-136">此命令會使用 Invoke-Command Cmdlet，在 Server01 電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="947d1-136">The command uses the Invoke-Command cmdlet to run a command on the Server01 computer.</span></span>

<span data-ttu-id="947d1-137">遠端命令的開頭是可取得電腦上所有排程工作的 Get-ScheduledJob 命令。</span><span class="sxs-lookup"><span data-stu-id="947d1-137">The remote command begins with a Get-ScheduledJob command that gets all scheduled jobs on the computer.</span></span>
<span data-ttu-id="947d1-138">排程的工作會以管線傳送至 Get-JobTrigger Cmdlet，此 Cmdlet 會取得排程工作的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="947d1-138">The scheduled jobs are piped to the Get-JobTrigger cmdlet, which gets the job triggers of the scheduled jobs.</span></span>
<span data-ttu-id="947d1-139">輸入包含 JobDefinition 屬性 (其中包含排程工作) 的工作觸發程序，這樣觸發程序就會維持與排程工作的關聯 (即使它已被變更)。</span><span class="sxs-lookup"><span data-stu-id="947d1-139">Each job trigger contains a JobDefinition property that contains the scheduled job, so the trigger remains associated with the scheduled job even when it is changed.</span></span>

<span data-ttu-id="947d1-140">工作觸發程式會以管線傳送至 Where-Object Cmdlet，此 Cmdlet 會取得具有 User 屬性的工作觸發程式。</span><span class="sxs-lookup"><span data-stu-id="947d1-140">The job triggers are piped to the Where-Object cmdlet, which gets job triggers that have the User property.</span></span>
<span data-ttu-id="947d1-141">系統會使用管線將選取的工作觸發程序傳送至 **Set-JobTrigger** Cmdlet，此 Cmdlet 會將使用者變更為 Domain01\Admin02。</span><span class="sxs-lookup"><span data-stu-id="947d1-141">The selected job triggers are piped to the **Set-JobTrigger** cmdlet, which changes the user to Domain01\Admin02.</span></span>

### <span data-ttu-id="947d1-142">範例 4：變更多個工作觸發程序的其中一個</span><span class="sxs-lookup"><span data-stu-id="947d1-142">Example 4: Change one of many job triggers</span></span>

```
PS C:\> Get-JobTrigger -Name "SecurityCheck"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Daily           4/24/2013 3:00:00 AM                           True
2          Weekly          4/24/2013 4:00:00 PM   {Sunday}                True
3          Once            4/24/2013 4:00:00 PM                           True

The second command uses the **TriggerID** parameter of the **Get-JobTrigger** cmdlet to get the *Once* trigger of the SecurityCheck scheduled job. The command pipes the trigger to the Format-List cmdlet, which displays all of the properties of the *Once* job trigger.The output shows that the trigger starts the job once every hour (RepetitionInterval = 1 hour) for one day (RepetitionDuration = 1 day).
PS C:\> Get-JobTrigger -Name "SecurityCheck" -TriggerID 3 | Format-List -Property *
At                 : 4/24/2012 4:00:00 PM
DaysOfWeek         :
Interval           : 1
Frequency          : Once
RandomDelay        : 00:00:00
RepetitionInterval : 01:00:00
RepetitionDuration : 1.00:00:00
User               :
Id                 : 3
Enabled            : True
JobDefinition      : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition

The third command changes the repetition interval of the job trigger from one hour to 90 minutes. The command does not return any output.
PS C:\> Get-JobTrigger -Name "SecurityCheck" -TriggerId 3 | Set-JobTrigger -RepetitionInterval (New-TimeSpan -Minutes 90)

The fourth command displays the effect of the change.The output shows that the trigger starts the job once every 90 minutes (RepetitionInterval = 1 hour, 30 minutes) for one day (RepetitionDuration = 1 day).
PS C:\> Get-JobTrigger -Name "SecurityCheck" -TriggerID 3 | Format-List -Property *
At                 : 4/24/2012 4:00:00 PM
DaysOfWeek         :
Interval           : 1
Frequency          : Once
RandomDelay        : 00:00:00
RepetitionInterval : 01:30:00
RepetitionDuration : 1.00:00:00
User               :
Id                 : 3
Enabled            : True
JobDefinition      : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

<span data-ttu-id="947d1-143">此範例中的命令會將 SecurityCheck 排程工作之 *Once* 工作觸發程序的重複間隔從 60 分鐘變更為 90 分鐘。</span><span class="sxs-lookup"><span data-stu-id="947d1-143">The commands in this example changes the repetition interval of the *Once* job trigger of SecurityCheck scheduled job from every 60 minutes to every 90 minutes.</span></span>
<span data-ttu-id="947d1-144">SecurityCheck 排程的工作有三個工作觸發程序，因此命令會使用 Get-JobTrigger Cmdlet 的 *TriggerId* 參數來識別正在變更的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="947d1-144">The SecurityCheck scheduled job has three job triggers, so the commands use the *TriggerId* parameter of the Get-JobTrigger cmdlet to identify the job trigger that is being changed.</span></span>

<span data-ttu-id="947d1-145">第一個命令使用 **Get-JobTrigger** Cmdlet 來取得 SecurityCheck 排程工作的所有工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="947d1-145">The first command uses the **Get-JobTrigger** cmdlet to get all job triggers of the SecurityCheck scheduled job.</span></span>
<span data-ttu-id="947d1-146">輸出 (顯示工作觸發程序的識別碼) 會顯示 *Once* 工作觸發程序具有 3 的識別碼。</span><span class="sxs-lookup"><span data-stu-id="947d1-146">The output, which displays the IDs of the job triggers, reveals that the *Once* job trigger has an ID of 3.</span></span>

## <span data-ttu-id="947d1-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="947d1-147">PARAMETERS</span></span>

### <span data-ttu-id="947d1-148">-At</span><span class="sxs-lookup"><span data-stu-id="947d1-148">-At</span></span>
<span data-ttu-id="947d1-149">在指定的日期和時間啟動工作。</span><span class="sxs-lookup"><span data-stu-id="947d1-149">Starts the job at the specified date and time.</span></span>
<span data-ttu-id="947d1-150">輸入 **DateTime** 物件 (例如 Get-Date Cmdlet 傳回的物件) 或可轉換為時間的字串 (例如 "April 19, 2012 15:00"、"12/31/2013 9:00 PM" 或 "3am")。</span><span class="sxs-lookup"><span data-stu-id="947d1-150">Enter a **DateTime** object, such as one that the Get-Date cmdlet returns, or a string that can be converted to a time, such as "April 19, 2012 15:00", "12/31/2013 9:00 PM", or "3am".</span></span>

<span data-ttu-id="947d1-151">如果您未指定 **DateTime** 物件的元素（例如秒），則工作觸發程式的該元素不會變更。</span><span class="sxs-lookup"><span data-stu-id="947d1-151">If you don't specify an element of the **DateTime** object, such as seconds, that element of the job trigger is not changed.</span></span>
<span data-ttu-id="947d1-152">如果原始工作觸發程式未包含 **DateTime** 物件且您省略某個元素，則會使用目前日期和時間的對應元素來建立工作觸發程式。</span><span class="sxs-lookup"><span data-stu-id="947d1-152">If the original job trigger didn't include a **DateTime** object and you omit an element, the job trigger is created with the corresponding element from the current date and time.</span></span>

<span data-ttu-id="947d1-153">使用 *Once* 參數時，將 *At* 參數的值設定為特定日期和時間。</span><span class="sxs-lookup"><span data-stu-id="947d1-153">When using the *Once* parameter, set the value of the *At* parameter to a particular date and time.</span></span>
<span data-ttu-id="947d1-154">因為 **DateTime** 物件中的預設日期是目前日期，若設定目前時間之前的時間且未指定明確的日期，則系統會建立時間為過去時間的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="947d1-154">Because the default date in a **DateTime** object is the current date, setting a time before the current time without an explicit date results in a job trigger for a time in the past.</span></span>

<span data-ttu-id="947d1-155">**DateTime** 物件與轉換為 **DateTime** 物件的字串會自動調整為與為本機電腦所選取的日期和時間格式 (在 [控制台] 中的[地區及語言]) 相容。</span><span class="sxs-lookup"><span data-stu-id="947d1-155">**DateTime** objects, and strings that are converted to **DateTime** objects, are automatically adjusted to be compatible with the date and time formats selected for the local computer in Region and Language in Control Panel.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="947d1-156">-AtLogOn</span><span class="sxs-lookup"><span data-stu-id="947d1-156">-AtLogOn</span></span>
<span data-ttu-id="947d1-157">在指定的使用者登入電腦時啟動排程工作。</span><span class="sxs-lookup"><span data-stu-id="947d1-157">Starts the scheduled job when the specified users log on to the computer.</span></span>
<span data-ttu-id="947d1-158">若要指定使用者，請使用 *User* 參數。</span><span class="sxs-lookup"><span data-stu-id="947d1-158">To specify a user, use the *User* parameter.</span></span>

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

### <span data-ttu-id="947d1-159">-AtStartup</span><span class="sxs-lookup"><span data-stu-id="947d1-159">-AtStartup</span></span>
<span data-ttu-id="947d1-160">在 Windows 啟動時啟動排程工作。</span><span class="sxs-lookup"><span data-stu-id="947d1-160">Starts the scheduled job when Windows starts.</span></span>

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

### <span data-ttu-id="947d1-161">-Daily</span><span class="sxs-lookup"><span data-stu-id="947d1-161">-Daily</span></span>
<span data-ttu-id="947d1-162">指定每日週期性工作排程。</span><span class="sxs-lookup"><span data-stu-id="947d1-162">Specifies a recurring daily job schedule.</span></span>
<span data-ttu-id="947d1-163">使用 *每日* 參數集中的其他參數來指定排程詳細資料。</span><span class="sxs-lookup"><span data-stu-id="947d1-163">Use the other parameters in the *Daily* parameter set to specify the schedule details.</span></span>

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

### <span data-ttu-id="947d1-164">-DaysInterval</span><span class="sxs-lookup"><span data-stu-id="947d1-164">-DaysInterval</span></span>
<span data-ttu-id="947d1-165">在每日排程上指定執行週期間隔天數。</span><span class="sxs-lookup"><span data-stu-id="947d1-165">Specifies the number of days between occurrences on a daily schedule.</span></span>
<span data-ttu-id="947d1-166">例如，3 的值會在第 1、4、7 天啟動排程工作，依此類推。</span><span class="sxs-lookup"><span data-stu-id="947d1-166">For example, a value of 3 starts the scheduled job on days 1, 4, 7 and so on.</span></span>
<span data-ttu-id="947d1-167">預設值為 1。</span><span class="sxs-lookup"><span data-stu-id="947d1-167">The default value is 1.</span></span>

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

### <span data-ttu-id="947d1-168">-DaysOfWeek</span><span class="sxs-lookup"><span data-stu-id="947d1-168">-DaysOfWeek</span></span>
<span data-ttu-id="947d1-169">指定每週排程工作要在星期幾執行。</span><span class="sxs-lookup"><span data-stu-id="947d1-169">Specifies the days of the week on which a weekly scheduled job runs.</span></span>
<span data-ttu-id="947d1-170">輸入日名稱，例如星期一、星期四、整數0-6、0代表星期日，或星號 (\*) 代表每一天。</span><span class="sxs-lookup"><span data-stu-id="947d1-170">Enter day names, such as Monday, Thursday, integers 0-6, where 0 represents Sunday, or an asterisk (\*) to represent every day.</span></span>
<span data-ttu-id="947d1-171">在 Weekly 參數集中，此為必要參數。</span><span class="sxs-lookup"><span data-stu-id="947d1-171">This parameter is required in the Weekly parameter set.</span></span>

<span data-ttu-id="947d1-172">在工作觸發程序中，星期幾名稱會轉換為其整數值。</span><span class="sxs-lookup"><span data-stu-id="947d1-172">Day names are converted to their integer values in the job trigger.</span></span>
<span data-ttu-id="947d1-173">當您在命令中將星期幾名稱放在引號中時，請將每個星期幾名稱放在各自的引號中，例如 "Monday"、"Tuesday"。</span><span class="sxs-lookup"><span data-stu-id="947d1-173">When you enclose day names in quotation marks in a command, enclose each day name in separate quotation marks, such as "Monday", "Tuesday".</span></span>
<span data-ttu-id="947d1-174">若將多個星期幾名稱放在一組引號中，則會加總對應的整數值。</span><span class="sxs-lookup"><span data-stu-id="947d1-174">If you enclose multiple day names in a single quotation mark pair, the corresponding integer values are summed.</span></span>
<span data-ttu-id="947d1-175">例如，"Monday, Tuesday" (1, 2) 會產生 "Wednesday" (3) 的值。</span><span class="sxs-lookup"><span data-stu-id="947d1-175">For example, "Monday, Tuesday" (1, 2) results in a value of "Wednesday" (3).</span></span>

```yaml
Type: System.DayOfWeek[]
Parameter Sets: (All)
Aliases:
Accepted values: Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="947d1-176">-InputObject</span><span class="sxs-lookup"><span data-stu-id="947d1-176">-InputObject</span></span>
<span data-ttu-id="947d1-177">指定工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="947d1-177">Specifies the job triggers.</span></span>
<span data-ttu-id="947d1-178">輸入包含 **>scheduledjobtrigger** 物件的變數，或輸入可取得 **>scheduledjobtrigger** 物件的命令或運算式，例如 Get-JobTrigger 命令。</span><span class="sxs-lookup"><span data-stu-id="947d1-178">Enter a variable that contains **ScheduledJobTrigger** objects or type a command or expression that gets **ScheduledJobTrigger** objects, such as a Get-JobTrigger command.</span></span>
<span data-ttu-id="947d1-179">您也可以使用管線將 **ScheduledJobTrigger** 物件傳遞給 **Set-JobTrigger** 。</span><span class="sxs-lookup"><span data-stu-id="947d1-179">You can also pipe a **ScheduledJobTrigger** object to **Set-JobTrigger** .</span></span>

<span data-ttu-id="947d1-180">若指定多個工作觸發程序， **Set-JobTrigger** 會對所有工作觸發程序進行相同的變更。</span><span class="sxs-lookup"><span data-stu-id="947d1-180">If you specify multiple job triggers, **Set-JobTrigger** makes the same changes to all job triggers.</span></span>

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

### <span data-ttu-id="947d1-181">-Once</span><span class="sxs-lookup"><span data-stu-id="947d1-181">-Once</span></span>
<span data-ttu-id="947d1-182">指定非週期性 (一次性) 排程。</span><span class="sxs-lookup"><span data-stu-id="947d1-182">Specifies a non-recurring (one time) schedule.</span></span>

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

### <span data-ttu-id="947d1-183">-PassThru</span><span class="sxs-lookup"><span data-stu-id="947d1-183">-PassThru</span></span>
<span data-ttu-id="947d1-184">傳回已變更的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="947d1-184">Returns the job triggers that changed.</span></span>
<span data-ttu-id="947d1-185">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="947d1-185">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="947d1-186">-RandomDelay</span><span class="sxs-lookup"><span data-stu-id="947d1-186">-RandomDelay</span></span>
<span data-ttu-id="947d1-187">啟用排定的開始時間前的隨機延遲，並設定最大延遲值。</span><span class="sxs-lookup"><span data-stu-id="947d1-187">Enables a random delay that begins at the scheduled start time, and sets the maximum delay value.</span></span>
<span data-ttu-id="947d1-188">延遲長度是在每次開始前隨機設定，其值介於無延遲到此參數值所指定的時間之間。</span><span class="sxs-lookup"><span data-stu-id="947d1-188">The length of the delay is set pseudo-randomly for each start and varies from no delay to the time specified by the value of this parameter.</span></span>
<span data-ttu-id="947d1-189">預設值零 (00:00:00) 會停用隨機延遲。</span><span class="sxs-lookup"><span data-stu-id="947d1-189">The default value, zero (00:00:00), disables the random delay.</span></span>

<span data-ttu-id="947d1-190">輸入 timespan 物件（例如 New-TimeSpan Cmdlet 所傳回的物件），或輸入 \<hours\> ： \<minutes\> ： format 格式的值 \<seconds\> ，此物件會自動轉換為 timespan 物件。</span><span class="sxs-lookup"><span data-stu-id="947d1-190">Enter a timespan object, such as one returned by the New-TimeSpan cmdlet, or enter a value in \<hours\>:\<minutes\>:\<seconds\> format, which is automatically converted to a timespan object.</span></span>

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

### <span data-ttu-id="947d1-191">-RepeatIndefinitely</span><span class="sxs-lookup"><span data-stu-id="947d1-191">-RepeatIndefinitely</span></span>
<span data-ttu-id="947d1-192">若要重複執行無終止時間之排程工作，使用此參數 (從 Windows PowerShell 4.0 開始提供) 可取代為 **RepetitionDuration** 參數指定 *TimeSpan.MaxValue* 值。</span><span class="sxs-lookup"><span data-stu-id="947d1-192">This parameter, available starting in Windows PowerShell 4.0, eliminates the necessity of specifying a **TimeSpan.MaxValue** value for the *RepetitionDuration* parameter to run a scheduled job repeatedly, for an indefinite period.</span></span>

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

### <span data-ttu-id="947d1-193">-RepetitionDuration</span><span class="sxs-lookup"><span data-stu-id="947d1-193">-RepetitionDuration</span></span>
<span data-ttu-id="947d1-194">重複執行工作，直到經過指定的時間。</span><span class="sxs-lookup"><span data-stu-id="947d1-194">Repeats the job until the specified time expires.</span></span>
<span data-ttu-id="947d1-195">重複頻率是由 *RepetitionInterval* 參數的值指定。</span><span class="sxs-lookup"><span data-stu-id="947d1-195">The repetition frequency is determined by the value of the *RepetitionInterval* parameter.</span></span>
<span data-ttu-id="947d1-196">例如，若 **RepetitionInterval** 的值是 5 分鐘且 *RepetitionDuration* 的值是 2 小時，則在兩小時內，每隔五分鐘會觸發該工作。</span><span class="sxs-lookup"><span data-stu-id="947d1-196">For example, if the value of **RepetitionInterval** is 5 minutes and the value of *RepetitionDuration* is 2 hours, the job is triggered every five minutes for two hours.</span></span>

<span data-ttu-id="947d1-197">輸入 timespan 物件 (例如 New-TimeSpan Cmdlet 傳回的物件) 或可轉換為 timespan 物件的字串 (例如 "1:05:30")。</span><span class="sxs-lookup"><span data-stu-id="947d1-197">Enter a timespan object, such as one that the New-TimeSpan cmdlet returns or a string that can be converted to a timespan object, such as "1:05:30".</span></span>

<span data-ttu-id="947d1-198">若要以無終止時間方式執行工作，請改為新增 *RepeatIndefinitely* 參數。</span><span class="sxs-lookup"><span data-stu-id="947d1-198">To run a job indefinitely, add the *RepeatIndefinitely* parameter instead.</span></span>

<span data-ttu-id="947d1-199">若要在工作觸發程序重複期間過期之前停止工作，請將 **RepetitionDuration** 值設定為零 (0)。</span><span class="sxs-lookup"><span data-stu-id="947d1-199">To stop a job before the job trigger repetition duration expires, set the **RepetitionDuration** value to zero (0).</span></span>

<span data-ttu-id="947d1-200">若要變更 *Once* 工作觸發程序的重複期間或重複間隔，命令必須包含 **RepetitionInterval** 與 **RepetitionDuration** 參數。</span><span class="sxs-lookup"><span data-stu-id="947d1-200">To change the repetition duration or repetition interval of a *Once* job trigger, the command must include both the **RepetitionInterval** and **RepetitionDuration** parameters.</span></span>
<span data-ttu-id="947d1-201">若要變更其他類型之工作觸發程序的重複期間或重複間隔，命令必須包含 *Once* 、 *At* 、 *RepetitionInterval* 與 *RepetitionDuration* 參數。</span><span class="sxs-lookup"><span data-stu-id="947d1-201">To change the repetition duration or repetition intervals of other types of job triggers, the command must include the *Once* , *At* , *RepetitionInterval* and *RepetitionDuration* parameters.</span></span>

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

### <span data-ttu-id="947d1-202">-RepetitionInterval</span><span class="sxs-lookup"><span data-stu-id="947d1-202">-RepetitionInterval</span></span>
<span data-ttu-id="947d1-203">以指定的時間間隔重複執行工作。</span><span class="sxs-lookup"><span data-stu-id="947d1-203">Repeats the job at the specified time interval.</span></span>
<span data-ttu-id="947d1-204">例如，若此參數的值是設定為 2 小時，則每隔兩小時會觸發一次工作。</span><span class="sxs-lookup"><span data-stu-id="947d1-204">For example, if the value of this parameter is 2 hours, the job is triggered every two hours.</span></span>
<span data-ttu-id="947d1-205">預設值 0 不會重複執行工作。</span><span class="sxs-lookup"><span data-stu-id="947d1-205">The default value, 0, does not repeat the job.</span></span>

<span data-ttu-id="947d1-206">輸入 timespan 物件 (例如 New-TimeSpan Cmdlet 傳回的物件) 或可轉換為 timespan 物件的字串 (例如 "1:05:30")。</span><span class="sxs-lookup"><span data-stu-id="947d1-206">Enter a timespan object, such as one that the New-TimeSpan cmdlet returns or a string that can be converted to a timespan object, such as "1:05:30".</span></span>

<span data-ttu-id="947d1-207">若要變更 **Once** 工作觸發程序的重複期間或重複間隔，命令必須包含 **RepetitionInterval** 與 **RepetitionDuration** 參數。</span><span class="sxs-lookup"><span data-stu-id="947d1-207">To change the repetition duration or repetition interval of a **Once** job trigger, the command must include both the **RepetitionInterval** and **RepetitionDuration** parameters.</span></span>
<span data-ttu-id="947d1-208">若要變更其他類型之工作觸發程序的重複期間或重複間隔，命令必須包含 **Once** 、 **At** 、 **RepetitionInterval** 與 **RepetitionDuration** 參數。</span><span class="sxs-lookup"><span data-stu-id="947d1-208">To change the repetition duration or repetition intervals of other types of job triggers, the command must include the **Once** , **At** , **RepetitionInterval** and **RepetitionDuration** parameters.</span></span>

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

### <span data-ttu-id="947d1-209">-User</span><span class="sxs-lookup"><span data-stu-id="947d1-209">-User</span></span>
<span data-ttu-id="947d1-210">指定觸發 *AtLogon* 排程工作啟動的使用者。</span><span class="sxs-lookup"><span data-stu-id="947d1-210">Specifies the users who trigger an *AtLogon* start of a scheduled job.</span></span>
<span data-ttu-id="947d1-211">以或格式輸入使用者的名稱 \<UserName\> ， \<Domain\Username\> 或輸入星號 (\*) 代表所有使用者。</span><span class="sxs-lookup"><span data-stu-id="947d1-211">Enter the name of a user in \<UserName\> or \<Domain\Username\> format or enter an asterisk (\*) to represent all users.</span></span>
<span data-ttu-id="947d1-212">預設值是所有使用者。</span><span class="sxs-lookup"><span data-stu-id="947d1-212">The default value is all users.</span></span>

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

### <span data-ttu-id="947d1-213">-Weekly</span><span class="sxs-lookup"><span data-stu-id="947d1-213">-Weekly</span></span>
<span data-ttu-id="947d1-214">指定週期性每週工作排程。</span><span class="sxs-lookup"><span data-stu-id="947d1-214">Specifies a recurring weekly job schedule.</span></span>
<span data-ttu-id="947d1-215">使用 *每週* 參數集中的其他參數來指定排程詳細資料。</span><span class="sxs-lookup"><span data-stu-id="947d1-215">Use the other parameters in the *Weekly* parameter set to specify the schedule details.</span></span>

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

### <span data-ttu-id="947d1-216">-WeeksInterval</span><span class="sxs-lookup"><span data-stu-id="947d1-216">-WeeksInterval</span></span>
<span data-ttu-id="947d1-217">指定每週工作排程的週次。</span><span class="sxs-lookup"><span data-stu-id="947d1-217">Specifies the number of weeks between occurrences on a weekly job schedule.</span></span>
<span data-ttu-id="947d1-218">例如，3 的值會在第 1、4、7 週啟動排程工作，依此類推。</span><span class="sxs-lookup"><span data-stu-id="947d1-218">For example, a value of 3 starts the scheduled job on weeks 1, 4, 7 and so on.</span></span>
<span data-ttu-id="947d1-219">預設值為 1。</span><span class="sxs-lookup"><span data-stu-id="947d1-219">The default value is 1.</span></span>

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

### <span data-ttu-id="947d1-220">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="947d1-220">CommonParameters</span></span>
<span data-ttu-id="947d1-221">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="947d1-221">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="947d1-222">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="947d1-222">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="947d1-223">輸入</span><span class="sxs-lookup"><span data-stu-id="947d1-223">INPUTS</span></span>

### <span data-ttu-id="947d1-224">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span><span class="sxs-lookup"><span data-stu-id="947d1-224">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span></span>
<span data-ttu-id="947d1-225">您可以透過管線將多個工作觸發程式傳送至 **enable-jobtrigger** 。</span><span class="sxs-lookup"><span data-stu-id="947d1-225">You can pipe multiple job triggers to **Set-JobTrigger** .</span></span>

## <span data-ttu-id="947d1-226">輸出</span><span class="sxs-lookup"><span data-stu-id="947d1-226">OUTPUTS</span></span>

### <span data-ttu-id="947d1-227">無或 Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span><span class="sxs-lookup"><span data-stu-id="947d1-227">None or Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span></span>
<span data-ttu-id="947d1-228">當您使用 *Passthru* 參數時， **Set-JobTrigger** 會傳回已變更的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="947d1-228">When you use the *Passthru* parameter, **Set-JobTrigger** returns the job triggers that were changed.</span></span>
<span data-ttu-id="947d1-229">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="947d1-229">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="947d1-230">注意</span><span class="sxs-lookup"><span data-stu-id="947d1-230">NOTES</span></span>

* <span data-ttu-id="947d1-231">工作觸發程序具有 JobDefintion 屬性，此屬性會將它們與排程工作關聯。</span><span class="sxs-lookup"><span data-stu-id="947d1-231">Job triggers have a JobDefintion property that associates them with the scheduled job.</span></span> <span data-ttu-id="947d1-232">當您變更排程工作的工作觸發程序時，工作也會被變更。</span><span class="sxs-lookup"><span data-stu-id="947d1-232">When you change the job trigger of a scheduled job, the job is changed.</span></span> <span data-ttu-id="947d1-233">您不需要使用 Set-ScheduledJob 命令將已變更的觸發程序套用到排程工作。</span><span class="sxs-lookup"><span data-stu-id="947d1-233">You do not need to use a Set-ScheduledJob command to apply the changed trigger to the scheduled job.</span></span>

## <span data-ttu-id="947d1-234">相關連結</span><span class="sxs-lookup"><span data-stu-id="947d1-234">RELATED LINKS</span></span>

[<span data-ttu-id="947d1-235">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="947d1-235">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="947d1-236">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="947d1-236">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="947d1-237">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="947d1-237">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="947d1-238">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="947d1-238">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="947d1-239">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="947d1-239">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="947d1-240">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="947d1-240">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="947d1-241">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="947d1-241">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="947d1-242">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="947d1-242">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="947d1-243">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="947d1-243">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="947d1-244">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="947d1-244">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="947d1-245">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="947d1-245">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="947d1-246">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="947d1-246">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="947d1-247">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="947d1-247">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="947d1-248">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="947d1-248">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="947d1-249">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="947d1-249">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="947d1-250">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="947d1-250">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
