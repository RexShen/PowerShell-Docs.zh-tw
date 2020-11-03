---
description: 說明如何建立及管理排程工作。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs_basics?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs_Basics
ms.openlocfilehash: d957c3267959c13b705e79fb220da4048e27a435
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207251"
---
# <a name="about-scheduled-jobs-basics"></a><span data-ttu-id="de356-104">關於排程工作的基本概念</span><span class="sxs-lookup"><span data-stu-id="de356-104">About Scheduled Jobs Basics</span></span>

## <a name="short-description"></a><span data-ttu-id="de356-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="de356-105">Short description</span></span>

<span data-ttu-id="de356-106">說明如何建立及管理排程工作。</span><span class="sxs-lookup"><span data-stu-id="de356-106">Explains how to create and manage scheduled jobs.</span></span>

## <a name="long-description"></a><span data-ttu-id="de356-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="de356-107">Long description</span></span>

<span data-ttu-id="de356-108">本檔說明如何執行建立和管理排程工作的基本工作。</span><span class="sxs-lookup"><span data-stu-id="de356-108">This document shows how to perform basic tasks of creating and managing scheduled jobs.</span></span> <span data-ttu-id="de356-109">如需更多工具的詳細資訊，請參閱 [about_Scheduled_Jobs_Advanced](about_Scheduled_Jobs_Advanced.md)。</span><span class="sxs-lookup"><span data-stu-id="de356-109">For information about more advanced tasks, see [about_Scheduled_Jobs_Advanced](about_Scheduled_Jobs_Advanced.md).</span></span>

<span data-ttu-id="de356-110">如需 **PSScheduledJob** 模組中所含 Cmdlet 的詳細資訊，請參閱 [PSScheduledJob](xref:PSScheduledJob)。</span><span class="sxs-lookup"><span data-stu-id="de356-110">For more information about the cmdlets contained in the **PSScheduledJob** module, see [PSScheduledJob](xref:PSScheduledJob).</span></span>

## <a name="how-to-create-a-scheduled-job"></a><span data-ttu-id="de356-111">如何建立排程工作</span><span class="sxs-lookup"><span data-stu-id="de356-111">How to create a scheduled job</span></span>

<span data-ttu-id="de356-112">若要建立排程工作，請使用 `Register-ScheduledJob` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="de356-112">To create a scheduled job, use the `Register-ScheduledJob` cmdlet.</span></span> <span data-ttu-id="de356-113">此 Cmdlet 需要工作執行的名稱和命令或腳本。</span><span class="sxs-lookup"><span data-stu-id="de356-113">The cmdlet requires a name and the commands or script that the job runs.</span></span> <span data-ttu-id="de356-114">您可以藉由新增 **RunNow** 參數來立即執行作業，或建立工作觸發程式，並在建立工作時設定工作選項，或編輯現有的作業。</span><span class="sxs-lookup"><span data-stu-id="de356-114">You can either run the job immediately by adding the **RunNow** parameter, or create a job trigger and set job options when you create the job, or edit an existing job.</span></span>

<span data-ttu-id="de356-115">若要建立執行腳本的作業，請使用 **FilePath** 參數指定腳本檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="de356-115">To create a job that runs a script, use the **FilePath** parameter to specify the path to the script file.</span></span> <span data-ttu-id="de356-116">若要建立執行命令的作業，請使用 **ScriptBlock** 參數。</span><span class="sxs-lookup"><span data-stu-id="de356-116">To create a job that runs commands, use the **ScriptBlock** parameter.</span></span>

<span data-ttu-id="de356-117">此 `Register-ScheduledJob` Cmdlet 會建立 **ProcessJob** ，以執行 `Get-Process` 命令。</span><span class="sxs-lookup"><span data-stu-id="de356-117">The `Register-ScheduledJob` cmdlet creates the **ProcessJob** , which runs a `Get-Process` command.</span></span> <span data-ttu-id="de356-118">此排程工作具有預設工作選項，且沒有工作觸發程式。</span><span class="sxs-lookup"><span data-stu-id="de356-118">This scheduled job has the default job options and no job trigger.</span></span>

```powershell
Register-ScheduledJob -Name ProcessJob -ScriptBlock { Get-Process }
```

```Output
Id         Name            Triggers        Command       Enabled
--         ----            --------        -------       -------
8          ProcessJob      {}              Get-Process   True
```

## <a name="how-to-create-a-job-trigger"></a><span data-ttu-id="de356-119">如何建立工作觸發程式</span><span class="sxs-lookup"><span data-stu-id="de356-119">How to create a job trigger</span></span>

<span data-ttu-id="de356-120">工作觸發程式會自動啟動排程工作。</span><span class="sxs-lookup"><span data-stu-id="de356-120">Job triggers start a scheduled job automatically.</span></span> <span data-ttu-id="de356-121">工作觸發程式可以是一次性或週期性排程或事件，例如當使用者登入或 Windows 啟動時。</span><span class="sxs-lookup"><span data-stu-id="de356-121">A job trigger can be one-time or recurring schedule or an event, such as when a user logs on or Windows starts.</span></span> <span data-ttu-id="de356-122">每個作業都可以有零個、一個或多個工作觸發程式。</span><span class="sxs-lookup"><span data-stu-id="de356-122">Each job can have zero, one, or multiple job triggers.</span></span>

<span data-ttu-id="de356-123">若要建立工作觸發程式，請使用 `New-JobTrigger` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="de356-123">To create a job trigger, use the `New-JobTrigger` cmdlet.</span></span> <span data-ttu-id="de356-124">下列命令會建立工作觸發程式，此觸發程式會在每星期一和星期四上午5:00 啟動工作。</span><span class="sxs-lookup"><span data-stu-id="de356-124">The following command creates a job trigger that starts a job every Monday and Thursday at 5:00 AM.</span></span>
<span data-ttu-id="de356-125">此命令會將工作觸發程式儲存在 `$T` 變數中。</span><span class="sxs-lookup"><span data-stu-id="de356-125">The command saves the job trigger in the `$T` variable.</span></span>

```powershell
$T = New-JobTrigger -Weekly -DaysOfWeek "Monday", "Thursday" -At "5:00 AM"
```

<span data-ttu-id="de356-126">工作觸發程序是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="de356-126">Job triggers are optional.</span></span> <span data-ttu-id="de356-127">您可以在命令中新增 **RunNow** 參數 `Register-ScheduledJob` ，或使用 Cmdlet，隨時啟動排程工作 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="de356-127">You can start a scheduled job at any time by adding the **RunNow** parameter to your `Register-ScheduledJob` command, or by using the `Start-Job` cmdlets.</span></span>

## <a name="how-to-add-a-job-trigger"></a><span data-ttu-id="de356-128">如何新增工作觸發程式</span><span class="sxs-lookup"><span data-stu-id="de356-128">How to add a job trigger</span></span>

<span data-ttu-id="de356-129">當您將工作觸發程式新增至排程工作時，工作觸發程式會新增至排程工作的排程工作 XML 檔案，並成為排程工作的一部分。</span><span class="sxs-lookup"><span data-stu-id="de356-129">When you add a job trigger to a scheduled job, the job trigger is added to the scheduled job XML file for the scheduled job and becomes part of the scheduled job.</span></span>

<span data-ttu-id="de356-130">您可以在建立排程工作時，將工作觸發程式新增至排程工作，或編輯現有的作業。</span><span class="sxs-lookup"><span data-stu-id="de356-130">You can add a job trigger to a scheduled job when you create the scheduled job, or edit an existing job.</span></span> <span data-ttu-id="de356-131">您可以隨時變更排程工作的工作觸發程式。</span><span class="sxs-lookup"><span data-stu-id="de356-131">You can change the job trigger of a scheduled job at any time.</span></span>

<span data-ttu-id="de356-132">PowerShell 會使用工作排程器使用的一些相同工作觸發程式。</span><span class="sxs-lookup"><span data-stu-id="de356-132">PowerShell uses some of the same job triggers that Task Scheduler uses.</span></span> <span data-ttu-id="de356-133">如需工作觸發程式的詳細資訊，請參閱 [enable-jobtrigger](xref:PSScheduledJob.New-JobTrigger) Cmdlet 的說明主題。</span><span class="sxs-lookup"><span data-stu-id="de356-133">For detailed information about job triggers, see the help topic for the [New-JobTrigger](xref:PSScheduledJob.New-JobTrigger) cmdlet.</span></span>

<span data-ttu-id="de356-134">下列範例會使用展開來建立將 `$JobParms` 參數值傳遞給 Cmdlet 的參數值 `Register-ScheduledJob` 。</span><span class="sxs-lookup"><span data-stu-id="de356-134">The following example uses splatting to create `$JobParms` which are parameter values that are passed to the `Register-ScheduledJob` cmdlet.</span></span> <span data-ttu-id="de356-135">如需詳細資訊，請參閱 [about_Splatting md](../../Microsoft.PowerShell.Core/About/about_Splatting.md)。</span><span class="sxs-lookup"><span data-stu-id="de356-135">For more information, see [about_Splatting.md](../../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>
<span data-ttu-id="de356-136">`Register-ScheduledJob`用 `@JobParms` 來建立排程工作。</span><span class="sxs-lookup"><span data-stu-id="de356-136">The `Register-ScheduledJob` uses `@JobParms` to create a scheduled job.</span></span> <span data-ttu-id="de356-137">它會使用 **Trigger** 參數來指定變數中的工作觸發程式 `$T` 。</span><span class="sxs-lookup"><span data-stu-id="de356-137">It uses the **Trigger** parameter to specify the job trigger in the `$T` variable.</span></span>

```powershell
$JobParms = @{
  Name = "ProcessJob"
  ScriptBlock = {Get-Command}
  Trigger = $T
}

Register-ScheduledJob @JobParms
```

<span data-ttu-id="de356-138">您也可以在任何時間將工作觸發程式新增至現有的排程工作。</span><span class="sxs-lookup"><span data-stu-id="de356-138">You can also add a job trigger to an existing scheduled job at any time.</span></span> <span data-ttu-id="de356-139">`Add-JobTrigger`Cmdlet 會將變數中的工作觸發程式新增 `$T` 至 **ProcessJob** 排程工作。</span><span class="sxs-lookup"><span data-stu-id="de356-139">The `Add-JobTrigger` cmdlet adds the job trigger in the `$T` variable to the **ProcessJob** scheduled job.</span></span>

```powershell
Add-JobTrigger -Name ProcessJob -Trigger $T
```

<span data-ttu-id="de356-140">如此一來，工作觸發程式就會在每星期一和星期四的上午5:00 自動啟動 **ProcessJob** 。</span><span class="sxs-lookup"><span data-stu-id="de356-140">As a result, the job trigger starts the **ProcessJob** automatically every Monday and Thursday at 5:00 AM.</span></span>

## <a name="how-to-get-a-job-trigger"></a><span data-ttu-id="de356-141">如何取得工作觸發程式</span><span class="sxs-lookup"><span data-stu-id="de356-141">How to get a job trigger</span></span>

<span data-ttu-id="de356-142">若要取得排程工作的工作觸發程式，請使用 `Get-JobTrigger` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="de356-142">To get the job trigger of a scheduled job, use the `Get-JobTrigger` cmdlet.</span></span> <span data-ttu-id="de356-143">您可以使用 **Name** 、 **ID** 和 **InputObject** 參數來指定排程工作，而不是工作觸發程式。</span><span class="sxs-lookup"><span data-stu-id="de356-143">Use the **Name** , **ID** , and **InputObject** parameters to specify the scheduled job, not the job trigger.</span></span>

<span data-ttu-id="de356-144">`Get-JobTrigger` 取得 **ProcessJob** 的工作觸發程式。</span><span class="sxs-lookup"><span data-stu-id="de356-144">`Get-JobTrigger` gets the job trigger of the **ProcessJob** .</span></span>

```powershell
Get-JobTrigger -Name ProcessJob
```

```Output
Id   Frequency       Time                   DaysOfWeek              Enabled
--   ---------       ----                   ----------              -------
1    Weekly          11/7/2011 5:00:00 AM   {Monday, Thursday}      True
```

## <a name="how-to-create-job-options"></a><span data-ttu-id="de356-145">如何建立工作選項</span><span class="sxs-lookup"><span data-stu-id="de356-145">How to create job options</span></span>

<span data-ttu-id="de356-146">作業選項會建立開始和執行工作的條件。</span><span class="sxs-lookup"><span data-stu-id="de356-146">Job options establish conditions for starting and running the job.</span></span> <span data-ttu-id="de356-147">每個作業都有預設的工作選項，除非您變更它們。</span><span class="sxs-lookup"><span data-stu-id="de356-147">Every job has the default job options unless you change them.</span></span> <span data-ttu-id="de356-148">因為工作選項可以防止工作在排程的時間執行，所以請務必瞭解工作選項並謹慎使用。</span><span class="sxs-lookup"><span data-stu-id="de356-148">Because job options can prevent a job from running at the scheduled time, it is important to understand the job options and use them carefully.</span></span>

<span data-ttu-id="de356-149">PowerShell 會使用工作排程器使用的相同工作選項。</span><span class="sxs-lookup"><span data-stu-id="de356-149">PowerShell uses the same job options that Task Scheduler uses.</span></span> <span data-ttu-id="de356-150">如需作業選項的詳細資訊，請參閱 [ScheduledJobOption](xref:PSScheduledJob.New-ScheduledJobOption)的說明主題。</span><span class="sxs-lookup"><span data-stu-id="de356-150">For detailed information about the job options, see the help topic for [New-ScheduledJobOption](xref:PSScheduledJob.New-ScheduledJobOption).</span></span>

<span data-ttu-id="de356-151">工作選項會儲存在排程的工作 XML 檔案中。</span><span class="sxs-lookup"><span data-stu-id="de356-151">Job options are stored in the scheduled job XML file.</span></span> <span data-ttu-id="de356-152">您可以在建立排程工作時設定工作選項，或隨時變更工作選項。</span><span class="sxs-lookup"><span data-stu-id="de356-152">You can set job options when you create a scheduled job or change them at any time.</span></span>

<span data-ttu-id="de356-153">此 `New-ScheduledJobOption` Cmdlet 會建立排程工作選項，其中 **WakeToRun** 排程工作選項會設定為 True。</span><span class="sxs-lookup"><span data-stu-id="de356-153">The `New-ScheduledJobOption` cmdlet creates a scheduled job option in which the **WakeToRun** scheduled job option is set to True.</span></span> <span data-ttu-id="de356-154">**WakeToRun** 選項會執行排程工作，即使電腦在排定的開始時間處於睡眠或休眠狀態。</span><span class="sxs-lookup"><span data-stu-id="de356-154">The **WakeToRun** option runs the scheduled job even if the computer is in the Sleep or Hibernate state at the scheduled start time.</span></span> <span data-ttu-id="de356-155">此命令會將工作選項儲存在 `$O` 變數中。</span><span class="sxs-lookup"><span data-stu-id="de356-155">The command saves the job options in the `$O` variable.</span></span>

```powershell
$O = New-ScheduledJobOption -WakeToRun
```

## <a name="how-to-get-job-options"></a><span data-ttu-id="de356-156">如何取得工作選項</span><span class="sxs-lookup"><span data-stu-id="de356-156">How to get job options</span></span>

<span data-ttu-id="de356-157">若要取得排程工作的工作選項，請使用 `Get-ScheduledJobOption` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="de356-157">To get the job options of a scheduled job, use the `Get-ScheduledJobOption` cmdlet.</span></span> <span data-ttu-id="de356-158">您可以使用 **Name** 、 **ID** 和 **InputObject** 參數來指定排程工作，而不是工作選項。</span><span class="sxs-lookup"><span data-stu-id="de356-158">Use the **Name** , **ID** , and **InputObject** parameters to specify the scheduled job, not the job options.</span></span>

<span data-ttu-id="de356-159">`Get-ScheduledJobOption` 取得 **ProcessJob** 的工作選項。</span><span class="sxs-lookup"><span data-stu-id="de356-159">`Get-ScheduledJobOption` gets the job options of the **ProcessJob** .</span></span>

```powershell
Get-ScheduledJobOption -Name ProcessJob
```

```Output
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
MultipleInstancePolicy : IgnoreNew
JobDefinition          : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

## <a name="how-to-change-job-options"></a><span data-ttu-id="de356-160">如何變更工作選項</span><span class="sxs-lookup"><span data-stu-id="de356-160">How to change job options</span></span>

<span data-ttu-id="de356-161">當您建立排程工作或編輯現有的作業時，您可以變更排程工作的工作選項。</span><span class="sxs-lookup"><span data-stu-id="de356-161">You can change the job options of a scheduled job when you create a scheduled job or edit an existing job.</span></span>

<span data-ttu-id="de356-162">Splatted `$JobParms` 會傳遞至 `Add-JobTrigger` Cmdlet 以建立處理作業。</span><span class="sxs-lookup"><span data-stu-id="de356-162">The splatted `$JobParms` are passed to the `Add-JobTrigger` cmdlet to create the process job.</span></span> <span data-ttu-id="de356-163">它會使用 **ScheduledJobOption** 參數來指定變數中的工作選項 `$O` 。</span><span class="sxs-lookup"><span data-stu-id="de356-163">It uses the **ScheduledJobOption** parameter to specify the job options in the `$O` variable.</span></span>

```powershell
$JobParms = @{
  Name = "ProcessJob"
  ScriptBlock = {Get-Process}
  ScheduledJobOption = $O
}

Add-JobTrigger @JobParms
```

<span data-ttu-id="de356-164">您也可以在任何時間將工作選項變更為現有的排程工作。</span><span class="sxs-lookup"><span data-stu-id="de356-164">You can also change the job options to an existing scheduled job at any time.</span></span>
<span data-ttu-id="de356-165">下列命令會使用 `Set-ScheduledJobOption` Cmdlet，將 **ProcessJob** register-scheduledjob 的 **WakeToRun** 選項值變更為 **True** 。</span><span class="sxs-lookup"><span data-stu-id="de356-165">The following command uses the `Set-ScheduledJobOption` cmdlet to change the value of the **WakeToRun** option of the **ProcessJob** scheduledJob to **True** .</span></span>

<span data-ttu-id="de356-166">`Set` **PSScheduledJob** 模組中的 Cmdlet （例如 `Set-ScheduledJobOption` Cmdlet）沒有 **名稱** 或 **識別碼** 參數。</span><span class="sxs-lookup"><span data-stu-id="de356-166">The `Set` cmdlets in the **PSScheduledJob** module, such as the `Set-ScheduledJobOption` cmdlet, don't have **Name** or **ID** parameters.</span></span> <span data-ttu-id="de356-167">您可以使用 **InputObject** 參數來指定排程工作選項，或使用管線將排程工作從 `Get-ScheduledJobOption` Cmdlet 傳送至 `Set-ScheduledJobOption` 。</span><span class="sxs-lookup"><span data-stu-id="de356-167">You can use the **InputObject** parameter to specify the scheduled job options or pipe a scheduled job from `Get-ScheduledJobOption` cmdlet to `Set-ScheduledJobOption`.</span></span>

<span data-ttu-id="de356-168">此範例會使用 `Get-ScheduledJob` Cmdlet 來取得 ProcessJob。</span><span class="sxs-lookup"><span data-stu-id="de356-168">This example uses the `Get-ScheduledJob` cmdlet to get the ProcessJob.</span></span> <span data-ttu-id="de356-169">它會使用 `Get-ScheduledJobOption` Cmdlet 來取得 **ProcessJob** 中的工作選項，以及使用 `Set-ScheduledJobOption` Cmdlet 將 ProcessJob 中的 **WakeToRun** 作業選項變更為 True。</span><span class="sxs-lookup"><span data-stu-id="de356-169">It uses the `Get-ScheduledJobOption` cmdlet to get the job options in the **ProcessJob** and the `Set-ScheduledJobOption` cmdlet to change the **WakeToRun** job option in the ProcessJob to True.</span></span>

```powershell
Get-ScheduledJob -Name ProcessJob | Get-ScheduledJobOption |
 Set-ScheduledJobOption -WakeToRun
```

## <a name="how-to-get-scheduled-job-instances"></a><span data-ttu-id="de356-170">如何取得排程工作實例</span><span class="sxs-lookup"><span data-stu-id="de356-170">How to get scheduled job instances</span></span>

<span data-ttu-id="de356-171">當排程工作啟動時，PowerShell 會建立類似于標準 PowerShell 背景工作的工作實例。</span><span class="sxs-lookup"><span data-stu-id="de356-171">When a scheduled job is started, PowerShell creates a job instance that is similar to a standard PowerShell background job.</span></span> <span data-ttu-id="de356-172">您可以使用 job Cmdlet （例如 `Get-Job` ） `Stop-Job` 和 `Receive-Job` 來管理工作實例。</span><span class="sxs-lookup"><span data-stu-id="de356-172">You can use the job cmdlets, such as `Get-Job`, `Stop-Job` and `Receive-Job` to manage the job instances.</span></span>

> [!NOTE]
> <span data-ttu-id="de356-173">若要在排程工作的實例上使用 job Cmdlet，必須將 **PSScheduledJob** 模組匯入到會話中。</span><span class="sxs-lookup"><span data-stu-id="de356-173">To use the job cmdlets on instances of scheduled jobs, the **PSScheduledJob** module must be imported into the session.</span></span> <span data-ttu-id="de356-174">若要匯入 **PSScheduledJob** 模組，請輸入 `Import-Module PSScheduledJob` 或使用任何排程工作 Cmdlet，例如 `Get-ScheduledJob` 。</span><span class="sxs-lookup"><span data-stu-id="de356-174">To import the **PSScheduledJob** module, type `Import-Module PSScheduledJob` or use any scheduled job cmdlet, such as `Get-ScheduledJob`.</span></span>

<span data-ttu-id="de356-175">若要取得 PowerShell 排程工作的所有實例，以及所有使用中的標準作業，請使用 `Get-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="de356-175">To get all instances of PowerShell scheduled jobs, and all active standard jobs, use the `Get-Job` cmdlet.</span></span> <span data-ttu-id="de356-176">此 `Import-Module` Cmdlet 會匯入 **PSScheduledJob** 模組，並 `Get-Job` 取得本機電腦上的工作。</span><span class="sxs-lookup"><span data-stu-id="de356-176">The `Import-Module` cmdlet imports the **PSScheduledJob** module and `Get-Job` gets the jobs on the local computer.</span></span>

```powershell
Import-Module PSScheduledJob
Get-Job
```

<span data-ttu-id="de356-177">`Get-Job` 取得本機電腦上的 **ProcessJob** 實例。</span><span class="sxs-lookup"><span data-stu-id="de356-177">`Get-Job` gets instances of **ProcessJob** on the local computer.</span></span>

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

<span data-ttu-id="de356-178">預設顯示不會顯示開始時間，這通常會區分相同排程工作的實例。</span><span class="sxs-lookup"><span data-stu-id="de356-178">The default display does not show the start time, which typically distinguishes instances of the same scheduled job.</span></span>

<span data-ttu-id="de356-179">`Get-Job`Cmdlet 會將物件沿著管線向下傳送。</span><span class="sxs-lookup"><span data-stu-id="de356-179">The `Get-Job` cmdlet sends objects down the pipeline.</span></span> <span data-ttu-id="de356-180">此 `Format-Table` Cmdlet 會顯示排程工作的 **名稱** 、 **識別碼** 和 **system.windows.media.animation.timeline.begintime** 屬性。</span><span class="sxs-lookup"><span data-stu-id="de356-180">The `Format-Table` cmdlet displays the **Name** , **ID** , and **BeginTime** properties of the scheduled job.</span></span>

```powershell
Get-Job ProcessJob | Format-Table -Property Name, ID, BeginTime
```

```Output
Name       Id BeginTime
----       -- ---------
ProcessJob 43 11/2/2011 3:00:02 AM
ProcessJob 44 11/3/2011 3:00:02 AM
ProcessJob 45 11/4/2011 3:00:02 AM
ProcessJob 46 11/5/2011 3:00:02 AM
ProcessJob 47 11/6/2011 3:00:02 AM
ProcessJob 48 11/7/2011 12:00:01 AM
ProcessJob 49 11/7/2011 3:00:02 AM
ProcessJob 50 11/8/2011 3:00:02 AM
```

## <a name="get-scheduled-job-results"></a><span data-ttu-id="de356-181">取得排程的工作結果</span><span class="sxs-lookup"><span data-stu-id="de356-181">Get scheduled job results</span></span>

<span data-ttu-id="de356-182">若要取得排程工作實例的結果，請使用 `Receive-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="de356-182">To get the results of an instance of a scheduled job, use the `Receive-Job` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="de356-183">若要在排程工作的實例上使用 Job Cmdlet，必須將 **PSScheduledJob** 模組匯入到會話中。</span><span class="sxs-lookup"><span data-stu-id="de356-183">To use the Job cmdlets on instances of scheduled jobs, the **PSScheduledJob** module must be imported into the session.</span></span> <span data-ttu-id="de356-184">若要匯入 **PSScheduledJob** 模組，請輸入 `Import-Module PSScheduledJob` 或使用任何排程工作 Cmdlet，例如 `Get-ScheduledJob` 。</span><span class="sxs-lookup"><span data-stu-id="de356-184">To import the **PSScheduledJob** module, type `Import-Module PSScheduledJob` or use any scheduled job cmdlet, such as `Get-ScheduledJob`.</span></span>

<span data-ttu-id="de356-185">此範例會取得 **ProcessJob** 排程工作的最新實例的結果 (識別碼 = 51) 。</span><span class="sxs-lookup"><span data-stu-id="de356-185">This examples gets the results of the newest instance of the **ProcessJob** scheduled job (ID = 51).</span></span>

```powershell
Import-Module PSScheduledJob
Receive-Job -ID 51 -Keep
```

<span data-ttu-id="de356-186">排程工作的結果會儲存在磁片上，因此不需要 **Keep** 的參數 `Receive-Job` 。</span><span class="sxs-lookup"><span data-stu-id="de356-186">The results of scheduled jobs are saved on disk, so the **Keep** parameter of `Receive-Job` is not required.</span></span> <span data-ttu-id="de356-187">不過，若沒有 **保留** 參數，您只可以在每個 PowerShell 會話中取得排程工作的結果一次。</span><span class="sxs-lookup"><span data-stu-id="de356-187">However, without the **Keep** parameter, you can get the results of a scheduled job only once in each PowerShell session.</span></span> <span data-ttu-id="de356-188">若要啟動新的 PowerShell 會話，請輸入 `PowerShell` 或開啟新的 powershell 視窗。</span><span class="sxs-lookup"><span data-stu-id="de356-188">To start a new PowerShell session, type `PowerShell` or open a new PowerShell window.</span></span>

## <a name="see-also"></a><span data-ttu-id="de356-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de356-189">See also</span></span>

[<span data-ttu-id="de356-190">about_Scheduled_Jobs_Advanced</span><span class="sxs-lookup"><span data-stu-id="de356-190">about_Scheduled_Jobs_Advanced</span></span>](about_Scheduled_Jobs_Advanced.md)

[<span data-ttu-id="de356-191">about_Scheduled_Jobs_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="de356-191">about_Scheduled_Jobs_Troubleshooting</span></span>](about_Scheduled_Jobs_Troubleshooting.md)

[<span data-ttu-id="de356-192">about_Scheduled_Jobs</span><span class="sxs-lookup"><span data-stu-id="de356-192">about_Scheduled_Jobs</span></span>](about_Scheduled_Jobs.md)

[<span data-ttu-id="de356-193">about_Splatting md</span><span class="sxs-lookup"><span data-stu-id="de356-193">about_Splatting.md</span></span>](../../Microsoft.PowerShell.Core/About/about_Splatting.md)

<span data-ttu-id="de356-194">[PSScheduledJob](xref:PSScheduledJob) 模組 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="de356-194">[PSScheduledJob](xref:PSScheduledJob) module cmdlets</span></span>

[<span data-ttu-id="de356-195">工作排程器</span><span class="sxs-lookup"><span data-stu-id="de356-195">Task Scheduler</span></span>](/windows/desktop/TaskSchd/task-scheduler-reference)
