---
description: 說明進階排程工作主題，包括構成排程工作基礎的檔案結構。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs_advanced?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs_Advanced
ms.openlocfilehash: 7b09a72e8ad7e68641c73d2f7e59065dbf8f889b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207255"
---
# <a name="about-scheduled-jobs-advanced"></a><span data-ttu-id="04cb9-104">關於排程工作 Advanced</span><span class="sxs-lookup"><span data-stu-id="04cb9-104">About Scheduled Jobs Advanced</span></span>

## <a name="short-description"></a><span data-ttu-id="04cb9-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="04cb9-105">Short description</span></span>

<span data-ttu-id="04cb9-106">說明進階排程工作主題，包括構成排程工作基礎的檔案結構。</span><span class="sxs-lookup"><span data-stu-id="04cb9-106">Explains advanced scheduled job topics, including the file structure that underlies scheduled jobs.</span></span>

## <a name="long-description"></a><span data-ttu-id="04cb9-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="04cb9-107">Long description</span></span>

<span data-ttu-id="04cb9-108">如需 **PSScheduledJob** 模組中所含 Cmdlet 的詳細資訊，請參閱 [PSScheduledJob](xref:PSScheduledJob)。</span><span class="sxs-lookup"><span data-stu-id="04cb9-108">For more information about the cmdlets contained in the **PSScheduledJob** module, see [PSScheduledJob](xref:PSScheduledJob).</span></span>

## <a name="scheduled-job-directories-and-files"></a><span data-ttu-id="04cb9-109">排程的工作目錄和檔案</span><span class="sxs-lookup"><span data-stu-id="04cb9-109">Scheduled job directories and files</span></span>

<span data-ttu-id="04cb9-110">PowerShell 排程工作是 PowerShell 作業和工作排程器工作。</span><span class="sxs-lookup"><span data-stu-id="04cb9-110">PowerShell scheduled jobs are both PowerShell jobs and Task Scheduler tasks.</span></span>
<span data-ttu-id="04cb9-111">每個排程工作都是在工作排程器中註冊，並以 Microsoft .NET Framework 序列化 XML 格式儲存在磁片上。</span><span class="sxs-lookup"><span data-stu-id="04cb9-111">Each scheduled job is registered in Task Scheduler and saved on disk in Microsoft .NET Framework Serialization XML format.</span></span>

<span data-ttu-id="04cb9-112">當您建立排程工作時，PowerShell 會在本機電腦的目錄中建立排程工作的目錄 `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` 。</span><span class="sxs-lookup"><span data-stu-id="04cb9-112">When you create a scheduled job, PowerShell creates a directory for the scheduled job in the `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` directory on the local computer.</span></span> <span data-ttu-id="04cb9-113">目錄名稱與作業名稱相同。</span><span class="sxs-lookup"><span data-stu-id="04cb9-113">The directory name is the same as the job name.</span></span>

<span data-ttu-id="04cb9-114">以下是範例 **ScheduledJobs** 目錄。</span><span class="sxs-lookup"><span data-stu-id="04cb9-114">The following is a sample **ScheduledJobs** directory.</span></span>

```powershell
Get-ChildItem $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs
```

```Output
Directory: C:\Users\User01\AppData\Local
               \Microsoft\Windows\PowerShell\ScheduledJobs

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         9/29/2011  10:03 AM            ArchiveProjects
d----         9/30/2011   1:18 PM            Inventory
d----        10/20/2011   9:15 AM            Backup-Scripts
d----         11/7/2011  10:40 AM            ProcessJob
d----         11/2/2011  10:25 AM            SecureJob
d----         9/27/2011   1:29 PM            Test-HelpFiles
d----         9/26/2011   4:22 PM            DeployPackage
```

<span data-ttu-id="04cb9-115">每個排程工作都有自己的目錄。</span><span class="sxs-lookup"><span data-stu-id="04cb9-115">Each scheduled job has its own directory.</span></span> <span data-ttu-id="04cb9-116">目錄包含已排程的工作 XML 檔案和 **輸出** 子目錄。</span><span class="sxs-lookup"><span data-stu-id="04cb9-116">The directory contains the scheduled job XML file and an **Output** subdirectory.</span></span>

```powershell
$Path = "$home\AppData\Local\Microsoft\Windows\PowerShell"
$Path += "\ScheduledJobs\ProcessJob"
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         11/1/2011   3:00 PM            Output
-a---         11/1/2011   3:43 PM       7281 ScheduledJobDefinition.xml
```

<span data-ttu-id="04cb9-117">排程工作的 **輸出** 目錄包含其執行歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="04cb9-117">The **Output** directory for a scheduled job contains its execution history.</span></span>
<span data-ttu-id="04cb9-118">每次工作觸發程式啟動排程工作時，PowerShell 會在輸出目錄中建立時間戳記命名的目錄。</span><span class="sxs-lookup"><span data-stu-id="04cb9-118">Each time a job trigger starts a scheduled job, PowerShell creates a timestamp-named directory in the output directory.</span></span> <span data-ttu-id="04cb9-119">時間戳記目錄包含 **Results.xml** 檔案中的作業結果，以及 **Status.xml** 檔案中的作業狀態。</span><span class="sxs-lookup"><span data-stu-id="04cb9-119">The timestamp directory contains the results of the job in a **Results.xml** file and the job status in a **Status.xml** file.</span></span>

<span data-ttu-id="04cb9-120">下列命令會顯示 **ProcessJob** 排程工作的執行歷程記錄目錄。</span><span class="sxs-lookup"><span data-stu-id="04cb9-120">The following command shows the execution history directories for the **ProcessJob** scheduled job.</span></span>

```powershell
$Path = "$home\AppData\Local\Microsoft"
$Path += "\Windows\PowerShell\ScheduledJobs\ProcessJob\Output"
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft
               \Windows\PowerShell\ScheduledJobs\ProcessJob\Output

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         11/2/2011   3:00 AM            20111102-030002-260
d----         11/3/2011   3:00 AM            20111103-030002-277
d----         11/4/2011   3:00 AM            20111104-030002-209
d----         11/5/2011   3:00 AM            20111105-030002-251
d----         11/6/2011   3:00 AM            20111106-030002-174
d----         11/7/2011  12:00 AM            20111107-000001-914
d----         11/7/2011   3:00 AM            20111107-030002-376
```

```powershell
$Path = "$home\AppData\Local\Microsoft\Windows\PowerShell\"
$Path += "ScheduledJobs\ProcessJob\Output\20111102-030002-260"
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob\Output\20111102-030002-260

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---         11/2/2011   3:00 AM     581106 Results.xml
-a---         11/2/2011   3:00 AM       9451 Status.xml
```

<span data-ttu-id="04cb9-121">您可以開啟和檢查 **ScheduledJobDefinition.xml** 、 **Results.xml** 和 **Status.xml** 檔案，或使用 `Select-XML` Cmdlet 來剖析檔案。</span><span class="sxs-lookup"><span data-stu-id="04cb9-121">You can open and examine the **ScheduledJobDefinition.xml** , **Results.xml** and **Status.xml** files or use the `Select-XML` cmdlet to parse the files.</span></span>

> [!WARNING]
> <span data-ttu-id="04cb9-122">請勿編輯 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="04cb9-122">Do not edit the XML files.</span></span> <span data-ttu-id="04cb9-123">如果任何 XML 檔案包含不正確 XML，PowerShell 就會刪除排程工作和其執行歷程記錄，包括工作結果。</span><span class="sxs-lookup"><span data-stu-id="04cb9-123">If any XML file contains invalid XML, PowerShell deletes the scheduled job and its execution history, including job results.</span></span>

## <a name="start-a-scheduled-job-immediately"></a><span data-ttu-id="04cb9-124">立即啟動排程工作</span><span class="sxs-lookup"><span data-stu-id="04cb9-124">Start a scheduled job immediately</span></span>

<span data-ttu-id="04cb9-125">您可以使用下列兩種方式之一來立即啟動排程工作：</span><span class="sxs-lookup"><span data-stu-id="04cb9-125">You can start a scheduled job immediately in one of two ways:</span></span>

- <span data-ttu-id="04cb9-126">執行 `Start-Job` Cmdlet 以啟動任何排程工作。</span><span class="sxs-lookup"><span data-stu-id="04cb9-126">Run the `Start-Job` cmdlet to start any scheduled job.</span></span>
- <span data-ttu-id="04cb9-127">將 **RunNow** 參數新增至 `Register-ScheduledJob` 命令，以在命令執行時立即啟動工作。</span><span class="sxs-lookup"><span data-stu-id="04cb9-127">Add the **RunNow** parameter to your `Register-ScheduledJob` command to start the job as soon as the command is run.</span></span>

<span data-ttu-id="04cb9-128">使用 Cmdlet 啟動的作業 `Start-Job` 是標準的 PowerShell 背景工作，而不是排程工作的實例。</span><span class="sxs-lookup"><span data-stu-id="04cb9-128">Jobs that are started by using the `Start-Job` cmdlet are standard PowerShell background jobs, not instances of the scheduled job.</span></span> <span data-ttu-id="04cb9-129">就像所有背景工作一樣，這些工作會立即開始，而不會受限於工作選項或由工作觸發程式所影響。</span><span class="sxs-lookup"><span data-stu-id="04cb9-129">Like all background jobs, these jobs start immediately, they aren't subject to job options or affected by job triggers.</span></span> <span data-ttu-id="04cb9-130">作業輸出不會儲存在排程工作目錄的 **輸出** 目錄中。</span><span class="sxs-lookup"><span data-stu-id="04cb9-130">The job output isn't saved in the **Output** directory of the scheduled job directory.</span></span>

<span data-ttu-id="04cb9-131">下列命令會使用 Cmdlet 的 **DefinitionName** 參數 `Start-Job` 來啟動 ProcessJob 排程工作。</span><span class="sxs-lookup"><span data-stu-id="04cb9-131">The following command uses the **DefinitionName** parameter of the `Start-Job` cmdlet to start the ProcessJob scheduled job.</span></span>

```powershell
Start-Job -DefinitionName ProcessJob
```

<span data-ttu-id="04cb9-132">若要管理作業並取得工作結果，請使用 job Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="04cb9-132">To manage the job and get the job results, use the job cmdlets.</span></span> <span data-ttu-id="04cb9-133">如需工作 Cmdlet 的詳細資訊，請參閱 [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="04cb9-133">For more information about the job cmdlets, see [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md).</span></span>

> [!NOTE]
> <span data-ttu-id="04cb9-134">若要在排程工作的實例上使用 Job Cmdlet，必須將 **PSScheduledJob** 模組匯入到會話中。</span><span class="sxs-lookup"><span data-stu-id="04cb9-134">To use the Job cmdlets on instances of scheduled jobs, the **PSScheduledJob** module must be imported into the session.</span></span> <span data-ttu-id="04cb9-135">若要匯入 **PSScheduledJob** 模組，請輸入 `Import-Module PSScheduledJob` 或使用任何排程工作 Cmdlet，例如 `Get-ScheduledJob` 。</span><span class="sxs-lookup"><span data-stu-id="04cb9-135">To import the **PSScheduledJob** module, type `Import-Module PSScheduledJob` or use any scheduled job cmdlet, such as `Get-ScheduledJob`.</span></span>

## <a name="rename-a-scheduled-job"></a><span data-ttu-id="04cb9-136">重新命名排程工作</span><span class="sxs-lookup"><span data-stu-id="04cb9-136">Rename a scheduled job</span></span>

<span data-ttu-id="04cb9-137">若要重新命名排程工作，請使用 Cmdlet 的 Name 參數 `Set-ScheduledJob` 。</span><span class="sxs-lookup"><span data-stu-id="04cb9-137">To rename a scheduled job, use the Name parameter of the `Set-ScheduledJob` cmdlet.</span></span> <span data-ttu-id="04cb9-138">當您重新命名排程工作時，PowerShell 會變更排程工作的名稱和排程的工作目錄。</span><span class="sxs-lookup"><span data-stu-id="04cb9-138">When you rename a scheduled job, PowerShell changes the name of the scheduled job and the scheduled job directory.</span></span> <span data-ttu-id="04cb9-139">但是，它不會變更已執行之排程工作的實例名稱。</span><span class="sxs-lookup"><span data-stu-id="04cb9-139">However, it doesn't change the names of instances of the scheduled job that have already run.</span></span>

## <a name="get-start-and-end-times"></a><span data-ttu-id="04cb9-140">取得開始和結束時間</span><span class="sxs-lookup"><span data-stu-id="04cb9-140">Get start and end times</span></span>

<span data-ttu-id="04cb9-141">若要取得工作實例開始和結束的日期和時間，請使用針對排程工作所傳回之 Register-scheduledjob 物件的 **PSBeginTime** 和 **PSEndTime** 屬性 `Get-Job` 。</span><span class="sxs-lookup"><span data-stu-id="04cb9-141">To get the dates and times that job instances started and ended, use the **PSBeginTime** and **PSEndTime** properties of the ScheduledJob object that `Get-Job` returns for scheduled jobs.</span></span>

<span data-ttu-id="04cb9-142">下列範例會使用 Cmdlet 的 **Property** 參數 `Format-Table` ，在資料表中顯示每個工作實例的 **PSBeginTime** 和 **PSEndTime** 屬性。</span><span class="sxs-lookup"><span data-stu-id="04cb9-142">The following example uses the **Property** parameter of the `Format-Table` cmdlet to display the **PSBeginTime** and **PSEndTime** properties of each job instance in a table.</span></span> <span data-ttu-id="04cb9-143">名為 **Label** 的計算屬性會顯示每個工作實例的經過時間。</span><span class="sxs-lookup"><span data-stu-id="04cb9-143">A calculated property named **Label** displays the elapsed time of each job instance.</span></span>

```powershell
Get-job -Name UpdateHelpJob | 
  Format-Table -Property ID, PSBeginTime, PSEndTime,
@{Label="Elapsed Time";Expression={$.PsEndTime - $.PSBeginTime}}
```

```Output
Id   PSBeginTime             PSEndTime                Elapsed Time
--   -----------             ---------                ------------
 2   11/3/2011 3:00:01 AM    11/3/2011 3:00:39 AM     00:00:38.0053854
 3   11/4/2011 3:00:02 AM    11/4/2011 3:01:01 AM     00:00:59.1188475
 4   11/5/2011 3:00:02 AM    11/5/2011 3:00:50 AM     00:00:48.3692034
 5   11/6/2011 3:00:01 AM    11/6/2011 3:00:54 AM     00:00:52.8013036
 6   11/7/2011 3:00:01 AM    11/7/2011 3:00:38 AM     00:00:37.1930350
 7   11/8/2011 3:00:01 AM    11/8/2011 3:00:57 AM     00:00:56.2570556
 8   11/9/2011 3:00:03 AM    11/9/2011 3:00:55 AM     00:00:51.8142222
 9   11/10/2011 3:00:02 AM   11/10/2011 3:00:42 AM    00:00:40.7195954
```

## <a name="manage-execution-history"></a><span data-ttu-id="04cb9-144">管理執行歷程記錄</span><span class="sxs-lookup"><span data-stu-id="04cb9-144">Manage execution history</span></span>

<span data-ttu-id="04cb9-145">您可以決定為每個排程工作儲存的工作實例結果數目，並刪除執行歷程記錄和任何排程工作的已儲存工作結果。</span><span class="sxs-lookup"><span data-stu-id="04cb9-145">You can determine the number of job instance results that are saved for each scheduled job and delete the execution history and saved job results of any scheduled job.</span></span>

<span data-ttu-id="04cb9-146">排程工作的 **ExecutionHistoryLength** 屬性會決定為排程工作儲存的工作實例結果數目。</span><span class="sxs-lookup"><span data-stu-id="04cb9-146">The **ExecutionHistoryLength** property of a scheduled job determines how many job instance results are saved for the scheduled job.</span></span> <span data-ttu-id="04cb9-147">當儲存的結果數目超過 **ExecutionHistoryLength** 屬性的值時，PowerShell 會刪除最舊實例的結果，以騰出空間給最新實例的結果。</span><span class="sxs-lookup"><span data-stu-id="04cb9-147">When the number of saved results exceeds the value of the **ExecutionHistoryLength** property, PowerShell deletes the results of the oldest instance to make room for the results of the newest instance.</span></span>

<span data-ttu-id="04cb9-148">根據預設，PowerShell 會儲存每個排程工作的執行歷程記錄和32實例的結果。</span><span class="sxs-lookup"><span data-stu-id="04cb9-148">By default, PowerShell saves the execution history and results of 32 instances of each scheduled job.</span></span> <span data-ttu-id="04cb9-149">若要變更該值，請使用 **MaxResultCount** 或 Cmdlet 的 MaxResultCount `Register-ScheduledJob` 參數 `Set-ScheduledJob` 。</span><span class="sxs-lookup"><span data-stu-id="04cb9-149">To change that value, use the **MaxResultCount** parameters of the `Register-ScheduledJob` or `Set-ScheduledJob` cmdlets.</span></span>

<span data-ttu-id="04cb9-150">若要刪除排程工作的執行歷程記錄和所有結果，請使用 Cmdlet 的 **ClearExecutionHistory** 參數 `Set-ScheduledJob` 。</span><span class="sxs-lookup"><span data-stu-id="04cb9-150">To delete the execution history and all results for a scheduled job, use the **ClearExecutionHistory** parameter of the `Set-ScheduledJob` cmdlet.</span></span> <span data-ttu-id="04cb9-151">刪除此執行歷程記錄並不會防止 PowerShell 儲存排程工作新實例的結果。</span><span class="sxs-lookup"><span data-stu-id="04cb9-151">Deleting this execution history does not prevent PowerShell from saving the results of new instances of the scheduled job.</span></span>

<span data-ttu-id="04cb9-152">下列範例會使用展開來建立將 `$JobParms` 參數值傳遞給 Cmdlet 的參數值 `Register-ScheduledJob` 。</span><span class="sxs-lookup"><span data-stu-id="04cb9-152">The following example uses splatting to create `$JobParms` which are parameter values that are passed to the `Register-ScheduledJob` cmdlet.</span></span> <span data-ttu-id="04cb9-153">如需詳細資訊，請參閱 [about_Splatting md](../../Microsoft.PowerShell.Core/About/about_Splatting.md)。</span><span class="sxs-lookup"><span data-stu-id="04cb9-153">For more information, see [about_Splatting.md](../../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>
<span data-ttu-id="04cb9-154">`Register-ScheduledJob`用 `@JobParms` 來建立排程工作。</span><span class="sxs-lookup"><span data-stu-id="04cb9-154">The `Register-ScheduledJob` uses `@JobParms` to create a scheduled job.</span></span> <span data-ttu-id="04cb9-155">此命令會使用值為12的 **MaxResultCount** 參數，只儲存排程工作的12個最新工作實例結果。</span><span class="sxs-lookup"><span data-stu-id="04cb9-155">The command uses the **MaxResultCount** parameter with a value of 12 to save only the 12 newest job instance results of the scheduled job.</span></span>

```powershell
$JobParms = @{
  Name = "ProcessJob"
  ScriptBlock = {Get-Process}
  MaxResultCount = "12"
}

Register-ScheduledJob @JobParms
```

<span data-ttu-id="04cb9-156">下列命令會使用 Cmdlet 的 **MaxResultCount** 參數， `Set-ScheduledJob` 將儲存的實例結果數目增加至</span><span class="sxs-lookup"><span data-stu-id="04cb9-156">The following command uses the **MaxResultCount** parameter of the `Set-ScheduledJob` cmdlet to increase the number of saved instance results to</span></span>
15.

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -MaxResultCount 15
```

<span data-ttu-id="04cb9-157">下列命令會刪除 **ProcessJob** 排程工作的執行歷程記錄和目前儲存的結果。</span><span class="sxs-lookup"><span data-stu-id="04cb9-157">The following command deletes the execution history and the current saved results of the **ProcessJob** scheduled job.</span></span>

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -ClearExecutionHistory
```

<span data-ttu-id="04cb9-158">下列命令會取得電腦上所有排程工作的 name 和 **ExecutionHistoryLength** 屬性值，並將它們顯示在資料表中。</span><span class="sxs-lookup"><span data-stu-id="04cb9-158">The following command gets the values of the name and **ExecutionHistoryLength** properties of all scheduled jobs on the computer and displays them in a table.</span></span>

```powershell
Get-ScheduledJob | 
  Format-Table -Property Name, ExecutionHistoryLength -AutoSize
```

## <a name="see-also"></a><span data-ttu-id="04cb9-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04cb9-159">See also</span></span>

[<span data-ttu-id="04cb9-160">about_Scheduled_Jobs_Basics</span><span class="sxs-lookup"><span data-stu-id="04cb9-160">about_Scheduled_Jobs_Basics</span></span>](about_Scheduled_Jobs_Basics.md)

[<span data-ttu-id="04cb9-161">about_Scheduled_Jobs_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="04cb9-161">about_Scheduled_Jobs_Troubleshooting</span></span>](about_Scheduled_Jobs_Troubleshooting.md)

[<span data-ttu-id="04cb9-162">about_Scheduled_Jobs</span><span class="sxs-lookup"><span data-stu-id="04cb9-162">about_Scheduled_Jobs</span></span>](about_Scheduled_Jobs.md)

[<span data-ttu-id="04cb9-163">about_Splatting md</span><span class="sxs-lookup"><span data-stu-id="04cb9-163">about_Splatting.md</span></span>](../../Microsoft.PowerShell.Core/About/about_Splatting.md)

<span data-ttu-id="04cb9-164">[PSScheduledJob](xref:PSScheduledJob) 模組 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="04cb9-164">[PSScheduledJob](xref:PSScheduledJob) module cmdlets</span></span>

[<span data-ttu-id="04cb9-165">工作排程器</span><span class="sxs-lookup"><span data-stu-id="04cb9-165">Task Scheduler</span></span>](/windows/desktop/TaskSchd/task-scheduler-reference)
