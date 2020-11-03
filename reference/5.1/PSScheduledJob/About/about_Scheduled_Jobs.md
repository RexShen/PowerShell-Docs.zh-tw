---
description: 描述排程工作並說明如何在 PowerShell 和工作排程器中使用和管理排程工作。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs
ms.openlocfilehash: 4d4e86957a584bb4deb47cadcd8588c1236455ac
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207256"
---
# <a name="about-scheduled-jobs"></a><span data-ttu-id="f9fd5-104">關於排程工作</span><span class="sxs-lookup"><span data-stu-id="f9fd5-104">About Scheduled Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="f9fd5-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="f9fd5-105">Short description</span></span>

<span data-ttu-id="f9fd5-106">描述排程工作並說明如何在 PowerShell 和工作排程器中使用和管理排程工作。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-106">Describes scheduled jobs and explains how to use and manage scheduled jobs in PowerShell and in Task Scheduler.</span></span>

## <a name="long-description"></a><span data-ttu-id="f9fd5-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="f9fd5-107">Long description</span></span>

<span data-ttu-id="f9fd5-108">PowerShell 排程工作是 PowerShell 背景工作和工作排程器工作的實用混合。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-108">PowerShell scheduled jobs are a useful hybrid of PowerShell background jobs and Task Scheduler tasks.</span></span>

<span data-ttu-id="f9fd5-109">就像 PowerShell 背景工作一樣，排程工作會在背景中以非同步方式執行。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-109">Like PowerShell background jobs, scheduled jobs run asynchronously in the background.</span></span> <span data-ttu-id="f9fd5-110">您可以使用 job Cmdlet 來管理已執行之排程工作的實例，例如、、 `Start-Job` `Get-Job` `Stop-Job` 和 `Receive-Job` 。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-110">Instances of scheduled jobs that have run can be managed by using the job cmdlets, such as `Start-Job`, `Get-Job`, `Stop-Job`, and `Receive-Job`.</span></span>

<span data-ttu-id="f9fd5-111">就像工作排程器工作一樣，排程工作會儲存至磁片。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-111">Like Task Scheduler tasks, scheduled jobs are saved to disk.</span></span> <span data-ttu-id="f9fd5-112">您可以在工作排程器中查看和管理工作、視需要啟用及停用工作、執行工作或使用它們作為範本、建立單次或週期性排程來啟動作業，或設定工作開始的條件。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-112">You can view and manage the jobs in Task Scheduler, enable and disable them as needed, run them or use them as templates, establish a one-time or recurring schedules for starting the jobs, or set conditions under which the jobs start.</span></span>

<span data-ttu-id="f9fd5-113">此外，排程工作實例的結果會以容易存取的格式儲存到磁片，提供工作輸出的執行記錄。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-113">In addition, the results of scheduled job instances are saved to disk in an easily accessible format, providing a running log of job output.</span></span> <span data-ttu-id="f9fd5-114">排程的工作隨附一組自訂的 Cmdlet 來管理它們。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-114">Scheduled jobs come with a customized set of cmdlets for managing them.</span></span> <span data-ttu-id="f9fd5-115">這些 Cmdlet 可讓您建立、編輯、管理、停用及重新啟用排程工作、工作觸發程式和工作選項。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-115">The cmdlets let you create, edit, manage, disable, and re-enable scheduled jobs, job triggers and job options.</span></span>

<span data-ttu-id="f9fd5-116">這套全方位且彈性的工具組，讓排程工作成為許多專業版 PowerShell IT 解決方案的重要元件。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-116">This comprehensive and flexible set of tools make scheduled jobs an essential component of many professional PowerShell IT solutions.</span></span>

<span data-ttu-id="f9fd5-117">排程工作 Cmdlet 包含在隨 PowerShell 安裝的 **PSScheduledJob** 模組中。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-117">The scheduled job cmdlets are included in the **PSScheduledJob** module that is installed with PowerShell.</span></span> <span data-ttu-id="f9fd5-118">此課程模組是在 PowerShell 3.0 中引進，適用于 powershell 3.0 和更新版本的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-118">This module was introduced in PowerShell 3.0 and works in PowerShell 3.0 and later versions of PowerShell.</span></span> <span data-ttu-id="f9fd5-119">如需 **PSScheduledJob** 模組中所含 Cmdlet 的詳細資訊，請參閱 [PSScheduledJob](xref:PSScheduledJob)。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-119">For more information about the cmdlets contained in the **PSScheduledJob** module, see [PSScheduledJob](xref:PSScheduledJob).</span></span>

<span data-ttu-id="f9fd5-120">如需 PowerShell 背景工作的詳細資訊，請參閱 [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-120">For more information about PowerShell background jobs, see [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md).</span></span>

<span data-ttu-id="f9fd5-121">如需工作排程器的詳細資訊，請參閱 [工作排程器](/windows/desktop/TaskSchd/task-scheduler-reference)。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-121">For more information about Task Scheduler, see [Task Scheduler](/windows/desktop/TaskSchd/task-scheduler-reference).</span></span>

> [!NOTE]
> <span data-ttu-id="f9fd5-122">您可以在工作排程器中查看和管理 PowerShell 排程工作。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-122">You can view and manage PowerShell scheduled jobs in Task Scheduler.</span></span> <span data-ttu-id="f9fd5-123">PowerShell 工作和排程工作 Cmdlet 只適用于在 PowerShell 中建立的排程工作。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-123">The PowerShell jobs and scheduled job cmdlets work only on scheduled jobs that are created in PowerShell.</span></span>

## <a name="quick-start"></a><span data-ttu-id="f9fd5-124">快速入門</span><span class="sxs-lookup"><span data-stu-id="f9fd5-124">Quick start</span></span>

<span data-ttu-id="f9fd5-125">此範例會建立在每天上午3:00 開始的排程工作，並執行 `Get-Process` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-125">This example creates a scheduled job that starts every day at 3:00 AM and runs the `Get-Process` cmdlet.</span></span> <span data-ttu-id="f9fd5-126">即使電腦是以電池執行，也會啟動作業。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-126">The job starts even if the computer is running on batteries.</span></span>

```powershell
$trigger = New-JobTrigger -Daily -At 3AM
$options = New-ScheduledJobOption -StartIfOnBattery
Register-ScheduledJob -Name ProcessJob -ScriptBlock {Get-Process} `
-Trigger $trigger -ScheduledJobOption $options
```

<span data-ttu-id="f9fd5-127">`Get-ScheduledJob`Cmdlet 會取得本機電腦上的排程工作。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-127">The `Get-ScheduledJob` cmdlet gets the scheduled jobs on the local computer.</span></span>

```powershell
Get-ScheduledJob
```

```Output
Id         Name            Triggers        Command            Enabled
--         ----            --------        -------            -------
7          ProcessJob      {1}             Get-Process        True
```

<span data-ttu-id="f9fd5-128">`Get-JobTrigger` 取得 **ProcessJob** 的工作觸發程式。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-128">`Get-JobTrigger` gets the job triggers of **ProcessJob** .</span></span> <span data-ttu-id="f9fd5-129">輸入參數會指定排程工作，而不是觸發程式，因為觸發程式是儲存在排程工作中。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-129">The input parameters specify the scheduled job, not the trigger, because triggers are saved in a scheduled job.</span></span>

```powershell
Get-JobTrigger -Name ProcessJob
```

```Output
Id         Frequency       Time                   DaysOfWeek        Enabled
--         ---------       ----                   ----------        -------
1          Daily           11/5/2011 3:00:00 AM                     True
```

<span data-ttu-id="f9fd5-130">此範例會使用 Cmdlet 的 **ContinueIfGoingOnBattery** 參數 `Set-ScheduledJob` ，將 **ProcessJob** 的 **StopIfGoingOnBatteries** 屬性變更為 **False** 。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-130">This example uses the **ContinueIfGoingOnBattery** parameter of the `Set-ScheduledJob` cmdlet to change the **StopIfGoingOnBatteries** property of **ProcessJob** to **False** .</span></span>

```powershell
Get-ScheduledJob -Name ProcessJob | Set-ScheduledJobOption `
-ContinueIfGoingOnBattery -Passthru
```

```Output
StartIfOnBatteries     : True
StopIfGoingOnBatteries : False
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
MultipleInstancePolicy : IgnoreNew
JobDefinition          : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

<span data-ttu-id="f9fd5-131">`Get-ScheduledJob`Cmdlet 會取得 **ProcessJob** 排程工作。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-131">The `Get-ScheduledJob` cmdlet gets the **ProcessJob** scheduled job.</span></span>

```powershell
Get-ScheduledJob ProcessJob
```

```Output
Id         Name            Triggers        Command        Enabled
--         ----            --------        -------        -------
7          ProcessJob      {1}             Get-Process    True
```

<span data-ttu-id="f9fd5-132">此 `Get-Job` Cmdlet 會取得到目前為止執行的 **ProcessJob** 排程工作的所有實例。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-132">The `Get-Job` cmdlet gets all instances of the **ProcessJob** scheduled job that have run thus far.</span></span> <span data-ttu-id="f9fd5-133">`Get-Job`只有將 **PSScheduledJob** 模組匯入目前的會話時，此 Cmdlet 才會取得排程工作。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-133">The `Get-Job` cmdlet gets scheduled jobs only when the **PSScheduledJob** module is imported into the current session.</span></span>

> [!TIP]
> <span data-ttu-id="f9fd5-134">請注意，您可以使用「排程工作」 Cmdlet 來管理排程的工作，但您可以使用 job Cmdlet 來管理排程工作的實例。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-134">Notice that you use the scheduled job cmdlets to manage scheduled jobs, but you use the job cmdlets to manage instances of scheduled jobs.</span></span>

```powershell
Get-Job -Name ProcessJob
```

```Output
Id     Name        PSJobTypeName  State    HasMoreData   Location   Command
--     ----        ------------   -----    -----------   --------   -------
45     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
46     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
47     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
48     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
49     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
50     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
51     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
```

<span data-ttu-id="f9fd5-135">此 `Receive-Job` Cmdlet 會取得 **ProcessJob** 排程工作的最新實例的結果 (識別碼 = 51) 。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-135">The `Receive-Job` cmdlet gets the results of the most recent instance of the **ProcessJob** scheduled job (ID = 51).</span></span>

```powershell
Receive-Job -ID 51
```

<span data-ttu-id="f9fd5-136">即使命令未 `Receive-Job` 包含 **Keep** 參數，作業的結果仍會儲存在磁片上，直到您將其刪除或超過結果數目上限為止。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-136">Even though the `Receive-Job` command did not include the **Keep** parameter, the results of the job are saved on disk until you delete them or the maximum number of results are exceeded.</span></span>

<span data-ttu-id="f9fd5-137">此會話已無法再使用工作結果，但如果您啟動新的會話或開啟新的 PowerShell 視窗，則會再次提供作業的結果。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-137">The job results are no longer available in this session, but if you start a new session or open a new PowerShell window, the results of the job are available again.</span></span>

<span data-ttu-id="f9fd5-138">下列命令會使用 Cmdlet 的 **DefinitionName** 參數 `Start-Job` 來啟動 **ProcessJob** 排程工作。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-138">The following command uses the **DefinitionName** parameter of the `Start-Job` cmdlet to start the **ProcessJob** scheduled job.</span></span>

<span data-ttu-id="f9fd5-139">使用 Cmdlet 啟動的作業 `Start-Job` 是標準的 PowerShell 背景工作，而不是排程工作的實例。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-139">Jobs that are started by using the `Start-Job` cmdlet are standard PowerShell background jobs, not instances of the scheduled job.</span></span> <span data-ttu-id="f9fd5-140">就像所有背景工作一樣，這些作業會立即啟動、不受工作選項影響，也不會受到工作觸發程式的影響，且其輸出不會儲存在排程工作目錄的輸出目錄中。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-140">Like all background jobs, these jobs start immediately, they aren't subject to job options or affected by job triggers, and their output is not saved in the output directory of the scheduled job directory.</span></span>

```powershell
Start-Job -DefinitionName ProcessJob
```

<span data-ttu-id="f9fd5-141">此 `Unregister-ScheduledJob` Cmdlet 會刪除 **ProcessJob** 排程工作，以及其工作實例的所有儲存結果。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-141">The `Unregister-ScheduledJob` cmdlet deletes the **ProcessJob** scheduled job and all saved results of its job instances.</span></span>

```powershell
Unregister-ScheduledJob ProcessJob
```

## <a name="scheduled-jobs-concepts"></a><span data-ttu-id="f9fd5-142">排程工作概念</span><span class="sxs-lookup"><span data-stu-id="f9fd5-142">Scheduled jobs concepts</span></span>

<span data-ttu-id="f9fd5-143">排程工作會執行命令或腳本。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-143">A scheduled job runs commands or a script.</span></span> <span data-ttu-id="f9fd5-144">排程工作可以包含工作觸發程式，以啟動作業和工作選項來設定執行作業的條件。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-144">A scheduled job can include job triggers that start the job and job options that set conditions for running the job.</span></span>

<span data-ttu-id="f9fd5-145">工作觸發程式會自動啟動排程工作。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-145">A job trigger starts a scheduled job automatically.</span></span> <span data-ttu-id="f9fd5-146">工作觸發程式可以包含一次性或週期性排程，或指定事件，例如當使用者登入或 Windows 啟動時。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-146">A job trigger can include a one-time or recurring schedule or specify an event, such as when a user logs on or Windows starts.</span></span> <span data-ttu-id="f9fd5-147">排程工作可以有一或多個工作觸發程式，您可以建立、新增、啟用、停用和取得工作觸發程式。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-147">A scheduled job can have one or more job triggers, and you can create, add, enable, disable, and get job triggers.</span></span>

<span data-ttu-id="f9fd5-148">工作觸發程序是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-148">Job triggers are optional.</span></span> <span data-ttu-id="f9fd5-149">您可以使用來立即啟動排程工作 `Start-Job cmdlet` ，或將 **RunNow** 參數新增至 `Register-ScheduledJob` 命令。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-149">You can start scheduled jobs immediately by using the `Start-Job cmdlet`, or by adding the **RunNow** parameter to your `Register-ScheduledJob` command.</span></span>

<span data-ttu-id="f9fd5-150">作業選項會設定執行排程工作的條件。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-150">Job options set the conditions for running a scheduled job.</span></span> <span data-ttu-id="f9fd5-151">每個排程工作都有一個工作選項物件。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-151">Every scheduled job has one job options object.</span></span> <span data-ttu-id="f9fd5-152">您可以建立和編輯作業選項物件，並將它們新增至一或多個排程工作。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-152">You can create and edit job options objects and add them to one or more scheduled jobs.</span></span>

<span data-ttu-id="f9fd5-153">每次排程工作啟動時，就會建立一個工作實例。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-153">Each time a scheduled job starts, a job instance is created.</span></span> <span data-ttu-id="f9fd5-154">使用 PowerShell 工作 Cmdlet 來查看和管理作業實例。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-154">Use the PowerShell job cmdlets to view and manage the job instance.</span></span>

<span data-ttu-id="f9fd5-155">排程的工作會儲存至磁片，並使用 Cmdlet 動詞命令， `Register` 而不是 `New` 。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-155">Scheduled jobs are saved to disk and use the cmdlet verb, `Register`, instead of `New`.</span></span> <span data-ttu-id="f9fd5-156">XML 檔案位於目錄中的本機電腦上 `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` 。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-156">The XML files are located on the local computer in the directory `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs`.</span></span>

<span data-ttu-id="f9fd5-157">PowerShell 會建立每個排程工作的目錄，並將工作命令、工作觸發程式、工作選項和工作結果儲存在排程的工作目錄中。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-157">PowerShell creates a directory for each scheduled job and saves the job commands, job triggers, job options and job results in the scheduled job directory.</span></span> <span data-ttu-id="f9fd5-158">工作觸發程式和工作選項不會獨立儲存至磁片。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-158">Job triggers and job options aren't saved to disk independently.</span></span>
<span data-ttu-id="f9fd5-159">它們會儲存在與其相關聯之每個排程工作的排程工作 XML 中。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-159">They are saved in the scheduled job XML of each scheduled job with which they are associated.</span></span>

<span data-ttu-id="f9fd5-160">排程工作、工作觸發程式和工作選項會以物件的形式出現在 PowerShell 中。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-160">Scheduled jobs, job triggers, and job options appear in PowerShell as objects.</span></span>
<span data-ttu-id="f9fd5-161">這些物件是 interlinked 的，可讓您輕鬆地探索和使用命令和腳本。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-161">The objects are interlinked, which makes them easy to discover and use in commands and scripts.</span></span>

<span data-ttu-id="f9fd5-162">排程的工作會顯示為 **>scheduledjobdefinition** 物件。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-162">Scheduled jobs appear as **ScheduledJobDefinition** objects.</span></span> <span data-ttu-id="f9fd5-163">**>scheduledjobdefinition** 物件具有 **JobTriggers** 屬性，其中包含排程工作的工作觸發程式，以及包含作業選項的 **Options** 屬性。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-163">The **ScheduledJobDefinition** object has a **JobTriggers** property that contains the job triggers of the scheduled job and an **Options** property that contains the job options.</span></span> <span data-ttu-id="f9fd5-164">分別代表工作觸發程式和工作選項的 **ScheduledJobTriggers** 和 **ScheduledJobOptions** 物件具有 **JobDefinition** 屬性，其中包含與其相關聯的排程工作。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-164">The **ScheduledJobTriggers** and **ScheduledJobOptions** objects that represent job triggers and job options, respectively, each have a **JobDefinition** property that contains the scheduled job with which they are associated.</span></span> <span data-ttu-id="f9fd5-165">這種遞迴互連可讓您輕鬆地尋找排程工作的觸發程式和選項，以及尋找、腳本和顯示與任何工作觸發程式或工作選項相關聯的排程工作。</span><span class="sxs-lookup"><span data-stu-id="f9fd5-165">This recursive interconnection makes it easy to find the triggers and options of a scheduled job and to find, script, and display the scheduled job to which any job trigger or job option is associated.</span></span>

## <a name="see-also"></a><span data-ttu-id="f9fd5-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9fd5-166">See also</span></span>

[<span data-ttu-id="f9fd5-167">about_Scheduled_Jobs_Basics</span><span class="sxs-lookup"><span data-stu-id="f9fd5-167">about_Scheduled_Jobs_Basics</span></span>](about_Scheduled_Jobs_Basics.md)

[<span data-ttu-id="f9fd5-168">about_Scheduled_Jobs_Advanced</span><span class="sxs-lookup"><span data-stu-id="f9fd5-168">about_Scheduled_Jobs_Advanced</span></span>](about_Scheduled_Jobs_Advanced.md)

[<span data-ttu-id="f9fd5-169">about_Scheduled_Jobs_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="f9fd5-169">about_Scheduled_Jobs_Troubleshooting</span></span>](about_Scheduled_Jobs_Troubleshooting.md)

<span data-ttu-id="f9fd5-170">[PSScheduledJob](xref:PSScheduledJob) 模組 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f9fd5-170">[PSScheduledJob](xref:PSScheduledJob) module cmdlets</span></span>

[<span data-ttu-id="f9fd5-171">工作排程器</span><span class="sxs-lookup"><span data-stu-id="f9fd5-171">Task Scheduler</span></span>](/windows/desktop/TaskSchd/task-scheduler-reference)
