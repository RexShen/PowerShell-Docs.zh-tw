---
description: 提供有關本機和遠端電腦上背景工作的詳細資料。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_job_details?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Job_Details
ms.openlocfilehash: cd6c633e9f409054b0ee89021de961c36d84ac3b
ms.sourcegitcommit: 108686b166672cc08817c637dd93eb1ad830511d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "93208575"
---
# <a name="about-job-details"></a><span data-ttu-id="dd893-104">關於工作詳細資料</span><span class="sxs-lookup"><span data-stu-id="dd893-104">About Job Details</span></span>

## <a name="short-description"></a><span data-ttu-id="dd893-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="dd893-105">Short description</span></span>
<span data-ttu-id="dd893-106">提供有關本機和遠端電腦上背景工作的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="dd893-106">Provides details about background jobs on local and remote computers.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="dd893-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="dd893-107">Detailed description</span></span>

<span data-ttu-id="dd893-108">本主題說明背景工作的概念，並提供有關如何在 PowerShell 中執行背景工作的技術資訊。</span><span class="sxs-lookup"><span data-stu-id="dd893-108">This topic explains the concept of a background job and provides technical information about how background jobs work in PowerShell.</span></span>

<span data-ttu-id="dd893-109">本主題是 [about_Jobs](about_Jobs.md)、 [about_Thread_Jobs](/powershell/module/microsoft.powershell.core/about/about_Thread_Jobs)和 [about_Remote_Jobs](about_Remote_Jobs.md) 主題的補充。</span><span class="sxs-lookup"><span data-stu-id="dd893-109">This topic is a supplement to the [about_Jobs](about_Jobs.md), [about_Thread_Jobs](/powershell/module/microsoft.powershell.core/about/about_Thread_Jobs), and [about_Remote_Jobs](about_Remote_Jobs.md) topics.</span></span>

### <a name="about-background-jobs"></a><span data-ttu-id="dd893-110">關於背景工作</span><span class="sxs-lookup"><span data-stu-id="dd893-110">About background jobs</span></span>

<span data-ttu-id="dd893-111">背景工作會以非同步方式執行命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="dd893-111">A background job runs a command or expression asynchronously.</span></span> <span data-ttu-id="dd893-112">它可能會執行 Cmdlet、函式、腳本或任何其他以命令為基礎的工作。</span><span class="sxs-lookup"><span data-stu-id="dd893-112">It might run a cmdlet, a function, a script, or any other command-based task.</span></span> <span data-ttu-id="dd893-113">它是設計來執行長時間執行的命令，但是您可以使用它在背景中執行任何命令。</span><span class="sxs-lookup"><span data-stu-id="dd893-113">It is designed to run commands that take an extended period of time, but you can use it to run any command in the background.</span></span>

<span data-ttu-id="dd893-114">當同步命令執行時，會隱藏 PowerShell 命令提示字元，直到命令完成為止。</span><span class="sxs-lookup"><span data-stu-id="dd893-114">When a synchronous command runs, the PowerShell command prompt is suppressed until the command is complete.</span></span> <span data-ttu-id="dd893-115">但背景工作不會抑制 PowerShell 提示字元。</span><span class="sxs-lookup"><span data-stu-id="dd893-115">But a background job does not suppress the PowerShell prompt.</span></span> <span data-ttu-id="dd893-116">啟動背景工作的命令會傳回工作物件。</span><span class="sxs-lookup"><span data-stu-id="dd893-116">A command to start a background job returns a job object.</span></span>
<span data-ttu-id="dd893-117">提示會立即傳回，讓您可以在背景工作執行時處理其他工作。</span><span class="sxs-lookup"><span data-stu-id="dd893-117">The prompt returns immediately so you can work on other tasks while the background job runs.</span></span>

<span data-ttu-id="dd893-118">不過，當您啟動背景工作時，即使作業的執行速度非常快，也不會立即取得結果。</span><span class="sxs-lookup"><span data-stu-id="dd893-118">However, when you start a background job, you do not get the results immediately even if the job runs very quickly.</span></span> <span data-ttu-id="dd893-119">傳回的工作物件包含工作的相關實用資訊，但是不包含工作結果。</span><span class="sxs-lookup"><span data-stu-id="dd893-119">The job object that is returned contains useful information about the job, but it does not contain the job results.</span></span> <span data-ttu-id="dd893-120">您必須執行個別的命令以取得工作結果。</span><span class="sxs-lookup"><span data-stu-id="dd893-120">You must run a separate command to get the job results.</span></span> <span data-ttu-id="dd893-121">您也可以執行命令來停止工作、等候工作完成，以及刪除工作。</span><span class="sxs-lookup"><span data-stu-id="dd893-121">You can also run commands to stop the job, to wait for the job to be completed, and to delete the job.</span></span>

<span data-ttu-id="dd893-122">為了讓背景工作的時間與其他命令無關，每個背景工作會在自己的 PowerShell 會話中執行。</span><span class="sxs-lookup"><span data-stu-id="dd893-122">To make the timing of a background job independent of other commands, each background job runs in its own PowerShell session.</span></span> <span data-ttu-id="dd893-123">不過，這可以是只為了執行工作而建立的暫時連線，然後終結，也可以是持續的 **PSSession** ，讓您用來執行數個相關的作業或命令。</span><span class="sxs-lookup"><span data-stu-id="dd893-123">However, this can be a temporary connection that is created only to run the job and is then destroyed, or it can be a persistent **PSSession** that you can use to run several related jobs or commands.</span></span>

### <a name="using-the-job-cmdlets"></a><span data-ttu-id="dd893-124">使用 job Cmdlet</span><span class="sxs-lookup"><span data-stu-id="dd893-124">Using the job cmdlets</span></span>

<span data-ttu-id="dd893-125">使用 `Start-Job` 命令在本機電腦上啟動背景工作。</span><span class="sxs-lookup"><span data-stu-id="dd893-125">Use a `Start-Job` command to start a background job on a local computer.</span></span>
<span data-ttu-id="dd893-126">`Start-Job` 傳回工作物件。</span><span class="sxs-lookup"><span data-stu-id="dd893-126">`Start-Job` returns a job object.</span></span> <span data-ttu-id="dd893-127">您也可以使用 Cmdlet 取得代表在本機電腦上啟動之作業的物件 `Get-Job` 。</span><span class="sxs-lookup"><span data-stu-id="dd893-127">You can also get objects representing the jobs that were started on the local computer using the `Get-Job` cmdlet.</span></span>

<span data-ttu-id="dd893-128">若要取得工作結果，請使用 `Receive-Job` 命令。</span><span class="sxs-lookup"><span data-stu-id="dd893-128">To get the job results, use a `Receive-Job` command.</span></span> <span data-ttu-id="dd893-129">如果作業未完成，則會傳回 `Receive-Job` 部分結果。</span><span class="sxs-lookup"><span data-stu-id="dd893-129">If the job is not complete, `Receive-Job` returns partial results.</span></span> <span data-ttu-id="dd893-130">您也可以使用 `Wait-Job` Cmdlet 來抑制命令提示字元，直到會話中啟動的一或所有工作完成為止。</span><span class="sxs-lookup"><span data-stu-id="dd893-130">You can also use the `Wait-Job` cmdlet to suppress the command prompt until one or all of the jobs that were started in the session are complete.</span></span>

<span data-ttu-id="dd893-131">若要停止背景工作，請使用 `Stop-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="dd893-131">To stop a background job, use the `Stop-Job` cmdlet.</span></span> <span data-ttu-id="dd893-132">若要刪除作業，請使用 `Remove-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="dd893-132">To delete a job, use the `Remove-Job` cmdlet.</span></span>

<span data-ttu-id="dd893-133">如需 Cmdlet 運作方式的詳細資訊，請參閱每個 Cmdlet 的說明主題，並查看 [about_Jobs](about_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="dd893-133">For more information about how the cmdlets work, see the Help topic for each cmdlet, and see [about_Jobs](about_Jobs.md).</span></span>

### <a name="starting-background-jobs-on-remote-computers"></a><span data-ttu-id="dd893-134">在遠端電腦上啟動背景工作</span><span class="sxs-lookup"><span data-stu-id="dd893-134">Starting background jobs on remote computers</span></span>

<span data-ttu-id="dd893-135">您可以在本機或遠端電腦上建立和管理背景工作。</span><span class="sxs-lookup"><span data-stu-id="dd893-135">You can create and manage background jobs on a local or remote computer.</span></span> <span data-ttu-id="dd893-136">若要從遠端執行背景工作，請使用 Cmdlet 的 **AsJob** 參數（例如 `Invoke-Command` ），或使用 `Invoke-Command` Cmdlet `Start-Job` 從遠端執行命令。</span><span class="sxs-lookup"><span data-stu-id="dd893-136">To run a background job remotely, use the **AsJob** parameter of a cmdlet such as `Invoke-Command`, or use the `Invoke-Command` cmdlet to run a `Start-Job` command remotely.</span></span> <span data-ttu-id="dd893-137">您也可以在互動式會話中啟動背景工作。</span><span class="sxs-lookup"><span data-stu-id="dd893-137">You can also start a background job in an interactive session.</span></span>

<span data-ttu-id="dd893-138">如需有關遠端背景工作的詳細資訊，請參閱 [about_Remote_Jobs](about_Remote_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="dd893-138">For more information about remote background jobs, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>

### <a name="child-jobs"></a><span data-ttu-id="dd893-139">子工作</span><span class="sxs-lookup"><span data-stu-id="dd893-139">Child jobs</span></span>

<span data-ttu-id="dd893-140">每個背景工作都是由父工作和一或多個子作業所組成。</span><span class="sxs-lookup"><span data-stu-id="dd893-140">Each background job consists of a parent job and one or more child jobs.</span></span> <span data-ttu-id="dd893-141">在使用 `Start-Job` 或的 **AsJob** 參數啟動的工作中 `Invoke-Command` ，父作業為執行。</span><span class="sxs-lookup"><span data-stu-id="dd893-141">In jobs started using `Start-Job` or the **AsJob** parameter of `Invoke-Command`, the parent job is an executive.</span></span> <span data-ttu-id="dd893-142">它不會執行任何命令或傳回任何結果。</span><span class="sxs-lookup"><span data-stu-id="dd893-142">It does not run any commands or return any results.</span></span> <span data-ttu-id="dd893-143">這些命令實際上是由子工作所執行。</span><span class="sxs-lookup"><span data-stu-id="dd893-143">The commands are actually run by the child jobs.</span></span> <span data-ttu-id="dd893-144">使用其他 Cmdlet 啟動的工作可能會有不同的運作方式。</span><span class="sxs-lookup"><span data-stu-id="dd893-144">Jobs started using other cmdlets might work differently.</span></span>

<span data-ttu-id="dd893-145">子工作會儲存在父工作物件的 **ChildJobs** 屬性中。</span><span class="sxs-lookup"><span data-stu-id="dd893-145">The child jobs are stored in the **ChildJobs** property of the parent job object.</span></span> <span data-ttu-id="dd893-146">**ChildJobs** 屬性可包含一或多個子工作物件。</span><span class="sxs-lookup"><span data-stu-id="dd893-146">The **ChildJobs** property can contain one or many child job objects.</span></span>
<span data-ttu-id="dd893-147">子工作物件的 **名稱** 、 **識別碼** 和 **InstanceId** 與父作業不同，因此您可以個別或單位來管理父工作和子工作。</span><span class="sxs-lookup"><span data-stu-id="dd893-147">The child job objects have a **Name** , **ID** , and **InstanceId** that differ from the parent job so that you can manage the parent and child jobs individually or as a unit.</span></span>

<span data-ttu-id="dd893-148">若要取得作業的父系和子作業，請使用 Cmdlet 的 **IncludeChildJobs** 參數 `Get-Job` 。</span><span class="sxs-lookup"><span data-stu-id="dd893-148">To get the parent and child jobs of a job, use the **IncludeChildJobs** parameter of the `Get-Job` cmdlet.</span></span> <span data-ttu-id="dd893-149">**IncludeChildJob** 參數是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="dd893-149">The **IncludeChildJob** parameter was introduced in Windows PowerShell 3.0.</span></span>

```powershell
PS> Get-Job -IncludeChildJob

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
1  Job1   RemoteJob     Failed     True          localhost   Get-Process
2  Job2                 Completed  True          Server01    Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

<span data-ttu-id="dd893-150">若要取得父工作，且僅取得具有特定 **狀態值** 的子工作，請使用 Cmdlet 的 **ChildJobState** 參數 `Get-Job` 。</span><span class="sxs-lookup"><span data-stu-id="dd893-150">To get the parent job and only the child jobs with a particular **State** value, use the **ChildJobState** parameter of the `Get-Job` cmdlet.</span></span> <span data-ttu-id="dd893-151">**ChildJobState** 參數是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="dd893-151">The **ChildJobState** parameter was introduced in Windows PowerShell 3.0.</span></span>

```powershell
PS> Get-Job -ChildJobState Failed

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
1  Job1   RemoteJob     Failed     True          localhost   Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

<span data-ttu-id="dd893-152">若要在所有版本的 PowerShell 上取得作業的子工作，請使用父工作的 **>childjob** 屬性。</span><span class="sxs-lookup"><span data-stu-id="dd893-152">To get the child jobs of a job on all versions of PowerShell, use the **ChildJob** property of the parent job.</span></span>

```powershell
PS> (Get-Job Job1).ChildJobs

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
2  Job2                 Completed  True          Server01    Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

<span data-ttu-id="dd893-153">您也可以 `Get-Job` 在子工作上使用命令，如下列命令所示：</span><span class="sxs-lookup"><span data-stu-id="dd893-153">You can also use a `Get-Job` command on the child job, as shown in the following command:</span></span>

```powershell
PS> Get-Job Job3

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
3  Job3                 Failed     False         localhost   Get-Process
```

<span data-ttu-id="dd893-154">子工作的設定取決於您用來啟動作業的命令。</span><span class="sxs-lookup"><span data-stu-id="dd893-154">The configuration of the child job depends on the command that you use to start the job.</span></span>

- <span data-ttu-id="dd893-155">當您使用在 `Start-Job` 本機電腦上啟動作業時，此作業包含執行命令的執行程式父工作和子工作。</span><span class="sxs-lookup"><span data-stu-id="dd893-155">When you use `Start-Job` to start a job on a local computer, the job consists of an executive parent job and a child job that runs the command.</span></span>

- <span data-ttu-id="dd893-156">當您使用的 **AsJob** 參數 `Invoke-Command` 在一或多部電腦上啟動作業時，此作業會由執行父工作和每一部電腦上執行的每個作業組成子工作。</span><span class="sxs-lookup"><span data-stu-id="dd893-156">When you use the **AsJob** parameter of `Invoke-Command` to start a job on one or more computers, the job consists of an executive parent job and a child job for each job run on each computer.</span></span>

- <span data-ttu-id="dd893-157">當您使用在 `Invoke-Command` `Start-Job` 一或多部遠端電腦上執行命令時，其結果與在每部遠端電腦上執行的本機命令相同。</span><span class="sxs-lookup"><span data-stu-id="dd893-157">When you use `Invoke-Command` to run a `Start-Job` command on one or more remote computers, the result is the same as a local command run on each remote computer.</span></span> <span data-ttu-id="dd893-158">此命令會傳回每一部電腦的工作物件。</span><span class="sxs-lookup"><span data-stu-id="dd893-158">The command returns a job object for each computer.</span></span> <span data-ttu-id="dd893-159">工作物件包含執行命令的執行父項作業和一個子工作。</span><span class="sxs-lookup"><span data-stu-id="dd893-159">The job object consists of an executive parent job and one child job that runs the command.</span></span>

<span data-ttu-id="dd893-160">父作業代表所有子工作。</span><span class="sxs-lookup"><span data-stu-id="dd893-160">The parent job represents all of the child jobs.</span></span> <span data-ttu-id="dd893-161">當您管理父工作時，也會管理相關聯的子工作。</span><span class="sxs-lookup"><span data-stu-id="dd893-161">When you manage a parent job, you also manage the associated child jobs.</span></span> <span data-ttu-id="dd893-162">例如，如果您停止父工作，則會停止所有子工作。</span><span class="sxs-lookup"><span data-stu-id="dd893-162">For example, if you stop a parent job, all child jobs are stopped.</span></span> <span data-ttu-id="dd893-163">如果您取得父作業的結果，則會取得所有子工作的結果。</span><span class="sxs-lookup"><span data-stu-id="dd893-163">If you get the results of a parent job, you get the results of all child jobs.</span></span>

<span data-ttu-id="dd893-164">不過，您也可以個別管理子工作。</span><span class="sxs-lookup"><span data-stu-id="dd893-164">However, you can also manage child jobs individually.</span></span> <span data-ttu-id="dd893-165">當您想要調查作業的問題，或是只使用的 **AsJob** 參數來取得一些子工作的結果時，這項功能最有用 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="dd893-165">This is most useful when you want to investigate a problem with a job or get the results of only one of a number of child jobs started using the **AsJob** parameter of `Invoke-Command`.</span></span>

<span data-ttu-id="dd893-166">下列命令使用的 **AsJob** 參數， `Invoke-Command` 在本機電腦和兩部遠端電腦上啟動背景工作。</span><span class="sxs-lookup"><span data-stu-id="dd893-166">The following command uses the **AsJob** parameter of `Invoke-Command` to start background jobs on the local computer and two remote computers.</span></span> <span data-ttu-id="dd893-167">此命令會將工作儲存在 `$j` 變數中。</span><span class="sxs-lookup"><span data-stu-id="dd893-167">The command saves the job in the `$j` variable.</span></span>

```powershell
PS> $j = Invoke-Command -ComputerName localhost, Server01, Server02 `
-Command {Get-Date} -AsJob
```

<span data-ttu-id="dd893-168">當您在中顯示作業的 Name 和 **>childjob** 屬性時 `$j` ，會顯示命令傳回具有三個子工作的工作物件，每一部電腦各一項。</span><span class="sxs-lookup"><span data-stu-id="dd893-168">When you display the Name and **ChildJob** properties of the job in `$j`, it shows that the command returned a job object with three child jobs, one for each computer.</span></span>

```powershell
PS> $j | Format-List Name, ChildJobs

Name      : Job3
ChildJobs : {Job4, Job5, Job6}
```

<span data-ttu-id="dd893-169">當您顯示父工作時，會顯示作業失敗。</span><span class="sxs-lookup"><span data-stu-id="dd893-169">When you display the parent job, it shows that the job failed.</span></span>

```powershell
PS> $j

Id Name   PSJobTypeName State      HasMoreData   Location
-- ----   ------------- -----      -----------   --------
3  Job3   RemotingJob   Failed     False         localhost,Server...
```

<span data-ttu-id="dd893-170">但是，當您執行可 `Get-Job` 取得子工作的命令時，輸出會顯示只有一個子工作失敗。</span><span class="sxs-lookup"><span data-stu-id="dd893-170">But when you run a `Get-Job` command that gets the child jobs, the output shows that only one child job failed.</span></span>

```powershell
PS> Get-Job -IncludeChildJobs

Id  Name   PSJobTypeName State      HasMoreData   Location    Command
--  ----   ------------- -----      -----------   --------    -------
3   Job3   RemotingJob   Failed     False         localhost,Server...
4   Job4                 Completed  True          localhost   Get-Date
5   Job5                 Failed     False         Server01    Get-Date
6   Job6                 Completed  True          Server02    Get-Date
```

<span data-ttu-id="dd893-171">若要取得所有子作業的結果，請使用 `Receive-Job` Cmdlet 來取得父工作的結果。</span><span class="sxs-lookup"><span data-stu-id="dd893-171">To get the results of all child jobs, use the `Receive-Job` cmdlet to get the results of the parent job.</span></span> <span data-ttu-id="dd893-172">但是，您也可以取得特定子作業的結果，如下列命令所示。</span><span class="sxs-lookup"><span data-stu-id="dd893-172">But you can also get the results of a particular child job, as shown in the following command.</span></span>

```powershell
PS> Receive-Job -Name Job6 -Keep | Format-Table ComputerName,
>> DateTime -AutoSize
ComputerName DateTime
------------ --------
Server02     Thursday, March 13, 2008 4:16:03 PM
```

<span data-ttu-id="dd893-173">PowerShell 背景工作的子工作功能可讓您更充分掌控您所執行的作業。</span><span class="sxs-lookup"><span data-stu-id="dd893-173">The child jobs feature of PowerShell background jobs gives you more control over the jobs that you run.</span></span>

### <a name="job-types"></a><span data-ttu-id="dd893-174">工作類型</span><span class="sxs-lookup"><span data-stu-id="dd893-174">Job types</span></span>

<span data-ttu-id="dd893-175">PowerShell 針對不同的工作支援不同類型的作業。</span><span class="sxs-lookup"><span data-stu-id="dd893-175">PowerShell supports different types of jobs for different tasks.</span></span> <span data-ttu-id="dd893-176">從 Windows PowerShell 3.0 開始，開發人員可以撰寫「作業來源介面卡」，以將新的作業類型新增至 PowerShell，並在模組中包含作業來源介面卡。</span><span class="sxs-lookup"><span data-stu-id="dd893-176">Beginning in Windows PowerShell 3.0, developers can write "job source adapters" that add new job types to PowerShell and include the job source adapters in modules.</span></span>
<span data-ttu-id="dd893-177">當您匯入模組時，您可以在會話中使用新的作業類型。</span><span class="sxs-lookup"><span data-stu-id="dd893-177">When you import the module, you can use the new job type in your session.</span></span>

<span data-ttu-id="dd893-178">例如，PSScheduledJob 模組會新增排程的工作，而 PSWorkflow 模組會新增工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="dd893-178">For example, the PSScheduledJob module adds scheduled jobs and the PSWorkflow module adds workflow jobs.</span></span>

<span data-ttu-id="dd893-179">自訂工作類型與標準 PowerShell 背景工作的差異可能會大不相同。</span><span class="sxs-lookup"><span data-stu-id="dd893-179">Custom jobs types might differ significantly from standard PowerShell background jobs.</span></span> <span data-ttu-id="dd893-180">例如，排程的工作會儲存在磁片上;它們只存在於特定會話中。</span><span class="sxs-lookup"><span data-stu-id="dd893-180">For example, scheduled jobs are saved on disk; they do not exist only in a particular session.</span></span> <span data-ttu-id="dd893-181">您可以暫停和繼續工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="dd893-181">Workflow jobs can be suspended and resumed.</span></span>

<span data-ttu-id="dd893-182">您用來管理自訂作業的 Cmdlet 取決於作業類型。</span><span class="sxs-lookup"><span data-stu-id="dd893-182">The cmdlets that you use to manage custom jobs depend on the job type.</span></span> <span data-ttu-id="dd893-183">在某些情況下，您會使用標準的工作 Cmdlet，例如 `Get-Job` 和 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="dd893-183">For some, you use the standard job cmdlets, such as `Get-Job` and `Start-Job`.</span></span> <span data-ttu-id="dd893-184">有些則是專門用來管理特定工作類型的專用 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="dd893-184">Others come with specialized cmdlets that manage only a particular type of job.</span></span> <span data-ttu-id="dd893-185">如需自訂工作類型的詳細資訊，請參閱有關工作類型的說明主題。</span><span class="sxs-lookup"><span data-stu-id="dd893-185">For detailed information about custom job types, see the help topics about the job type.</span></span>

<span data-ttu-id="dd893-186">若要尋找工作的工作類型，請使用 `Get-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="dd893-186">To find the job type of a job, use the `Get-Job` cmdlet.</span></span> <span data-ttu-id="dd893-187">`Get-Job` 針對不同類型的作業傳回不同的工作物件。</span><span class="sxs-lookup"><span data-stu-id="dd893-187">`Get-Job` returns different job objects for different types of jobs.</span></span> <span data-ttu-id="dd893-188">傳回的工作物件之 **PSJobTypeName** 屬性的值 `Get-Job` 表示作業類型。</span><span class="sxs-lookup"><span data-stu-id="dd893-188">The value of the **PSJobTypeName** property of the job objects that `Get-Job` returns indicates the job type.</span></span>

<span data-ttu-id="dd893-189">下表列出 PowerShell 隨附的作業類型。</span><span class="sxs-lookup"><span data-stu-id="dd893-189">The following table lists the job types that come with PowerShell.</span></span>

|    <span data-ttu-id="dd893-190">作業類型</span><span class="sxs-lookup"><span data-stu-id="dd893-190">Job Type</span></span>    |                       <span data-ttu-id="dd893-191">Description</span><span class="sxs-lookup"><span data-stu-id="dd893-191">Description</span></span>                        |
| -------------- | -------------------------------------------------------- |
| <span data-ttu-id="dd893-192">BackgroundJob</span><span class="sxs-lookup"><span data-stu-id="dd893-192">BackgroundJob</span></span>  | <span data-ttu-id="dd893-193">已開始使用 `Start-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="dd893-193">Started using the `Start-Job` cmdlet.</span></span>                    |
| <span data-ttu-id="dd893-194">RemoteJob</span><span class="sxs-lookup"><span data-stu-id="dd893-194">RemoteJob</span></span>      | <span data-ttu-id="dd893-195">開始使用的 **AsJob** 參數</span><span class="sxs-lookup"><span data-stu-id="dd893-195">Started using the **AsJob** parameter of the</span></span>             |
|                | <span data-ttu-id="dd893-196">`Invoke-Command` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="dd893-196">`Invoke-Command` cmdlet.</span></span>                                 |
| <span data-ttu-id="dd893-197">PSWorkflowJob</span><span class="sxs-lookup"><span data-stu-id="dd893-197">PSWorkflowJob</span></span>  | <span data-ttu-id="dd893-198">開始使用工作流程的 **AsJob** 參數。</span><span class="sxs-lookup"><span data-stu-id="dd893-198">Started using the **AsJob** parameter of a workflow.</span></span>     |
| <span data-ttu-id="dd893-199">PSScheduledJob</span><span class="sxs-lookup"><span data-stu-id="dd893-199">PSScheduledJob</span></span> | <span data-ttu-id="dd893-200">工作觸發程式啟動的排程工作實例。</span><span class="sxs-lookup"><span data-stu-id="dd893-200">An instance of a scheduled job started by a job trigger.</span></span> |
| <span data-ttu-id="dd893-201">CIMJob</span><span class="sxs-lookup"><span data-stu-id="dd893-201">CIMJob</span></span>         | <span data-ttu-id="dd893-202">開始使用來自的 Cmdlet 的 **AsJob** 參數</span><span class="sxs-lookup"><span data-stu-id="dd893-202">Started using the **AsJob** parameter of a cmdlet from a</span></span> |
|                | <span data-ttu-id="dd893-203">CDXML 模組。</span><span class="sxs-lookup"><span data-stu-id="dd893-203">CDXML module.</span></span>                                            |
| <span data-ttu-id="dd893-204">WMIJob</span><span class="sxs-lookup"><span data-stu-id="dd893-204">WMIJob</span></span>         | <span data-ttu-id="dd893-205">開始使用來自的 Cmdlet 的 **AsJob** 參數</span><span class="sxs-lookup"><span data-stu-id="dd893-205">Started using the **AsJob** parameter of a cmdlet from a</span></span> |
|                | <span data-ttu-id="dd893-206">WMI 模組。</span><span class="sxs-lookup"><span data-stu-id="dd893-206">WMI module.</span></span>                                              |
| <span data-ttu-id="dd893-207">PSEventJob</span><span class="sxs-lookup"><span data-stu-id="dd893-207">PSEventJob</span></span>     | <span data-ttu-id="dd893-208">使用建立 `Register-ObjectEvent` ，並指定</span><span class="sxs-lookup"><span data-stu-id="dd893-208">Created using`Register-ObjectEvent` and specifying an</span></span>    |
|                | <span data-ttu-id="dd893-209">**action 參數的** 動作。</span><span class="sxs-lookup"><span data-stu-id="dd893-209">action with the **Action** parameter.</span></span>                    |

<span data-ttu-id="dd893-210">注意：使用指令程式 `Get-Job` 取得特定類型的作業之前，請先確認新增工作類型的模組已匯入至目前的會話。</span><span class="sxs-lookup"><span data-stu-id="dd893-210">NOTE: Before using the `Get-Job` cmdlet to get jobs of a particular type, verify that the module that adds the job type is imported into the current session.</span></span>
<span data-ttu-id="dd893-211">否則，就 `Get-Job` 不會取得該類型的作業。</span><span class="sxs-lookup"><span data-stu-id="dd893-211">Otherwise, `Get-Job` does not get jobs of that type.</span></span>

## <a name="examples"></a><span data-ttu-id="dd893-212">範例</span><span class="sxs-lookup"><span data-stu-id="dd893-212">Examples</span></span>

<span data-ttu-id="dd893-213">下列命令會建立本機背景工作、遠端背景工作、工作流程工作和排程工作。</span><span class="sxs-lookup"><span data-stu-id="dd893-213">The following commands create a local background job, a remote background job, a workflow job, and a scheduled job.</span></span> <span data-ttu-id="dd893-214">然後，它會使用 `Get-Job` Cmdlet 來取得工作。</span><span class="sxs-lookup"><span data-stu-id="dd893-214">Then, it uses the `Get-Job` cmdlet to get the jobs.</span></span> <span data-ttu-id="dd893-215">`Get-Job` 不會取得排程工作，但會取得排程工作的任何已啟動實例。</span><span class="sxs-lookup"><span data-stu-id="dd893-215">`Get-Job` does not get the scheduled job, but it gets any started instances of the scheduled job.</span></span>

<span data-ttu-id="dd893-216">在本機電腦上啟動背景工作。</span><span class="sxs-lookup"><span data-stu-id="dd893-216">Start a background job on the local computer.</span></span>

```powershell
PS> Start-Job -Name LocalData {Get-Process}

Id Name        PSJobTypeName   State   HasMoreData   Location   Command
-- ----        -------------   -----   -----------   --------   -------
2  LocalData   BackgroundJob   Running        True   localhost  Get-Process
```

<span data-ttu-id="dd893-217">啟動在遠端電腦上執行的背景工作。</span><span class="sxs-lookup"><span data-stu-id="dd893-217">Start a background job that runs on a remote computer.</span></span>

```powershell
PS> Invoke-Command -ComputerName Server01 {Get-Process} `
-AsJob -JobName RemoteData

Id  Name        PSJobTypeName  State   HasMoreData   Location   Command
--  ----        -------------  -----   -----------   --------   -------
2   RemoteData  RemoteJob      Running        True   Server01   Get-Process
```

<span data-ttu-id="dd893-218">建立排程工作</span><span class="sxs-lookup"><span data-stu-id="dd893-218">Create a scheduled job</span></span>

```powershell
PS>  Register-ScheduledJob -Name ScheduledJob -ScriptBlock `
 {Get-Process} -Trigger (New-JobTrigger -Once -At "3 PM")

Id         Name            JobTriggers     Command       Enabled
--         ----            -----------     -------       -------
1          ScheduledJob    1               Get-Process   True
```

<span data-ttu-id="dd893-219">建立工作流程。</span><span class="sxs-lookup"><span data-stu-id="dd893-219">Create a workflow.</span></span>

```powershell
PS> workflow Test-Workflow {Get-Process}
```

<span data-ttu-id="dd893-220">以工作的形式執行工作流程。</span><span class="sxs-lookup"><span data-stu-id="dd893-220">Run the workflow as a job.</span></span>

```powershell

PS> Test-Workflow -AsJob -JobName TestWFJob

Id  Name       PSJobTypeName   State   HasMoreData   Location   Command
--  ----       -------------   -----   -----------   --------   -------
2   TestWFJob  PSWorkflowJob   NotStarted     True   localhost  Get-Process
```

<span data-ttu-id="dd893-221">取得作業。</span><span class="sxs-lookup"><span data-stu-id="dd893-221">Get the jobs.</span></span> <span data-ttu-id="dd893-222">此 `Get-Job` 命令不會取得排程的工作，但會取得已啟動之排程工作的實例。</span><span class="sxs-lookup"><span data-stu-id="dd893-222">The `Get-Job` command does not get scheduled jobs, but it gets instances of the scheduled job that are started.</span></span>

```powershell
PS> Get-Job

Id  Name         PSJobTypeName  State     HasMoreData  Location  Command
--  ----         -------------  -----     -----------  --------  -------
2   LocalData    BackgroundJob  Completed True         localhost Get-Process
4   RemoteData   RemoteJob      Completed True         Server01  Get-Process
6   TestWFJob    PSWorkflowJob  Completed True         localhost WorkflowJob
8   ScheduledJob PSScheduledJob Completed True         localhost Get-Process
```

<span data-ttu-id="dd893-223">若要取得排程工作，請使用 `Get-ScheduledJob` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="dd893-223">To get scheduled jobs, use the `Get-ScheduledJob` cmdlet.</span></span>

```powershell
PS> Get-ScheduledJob

Id         Name            JobTriggers     Command       Enabled
--         ----            -----------     -------       -------
1          ScheduledJob    1               Get-Process   True
```

## <a name="see-also"></a><span data-ttu-id="dd893-224">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd893-224">See also</span></span>

- [<span data-ttu-id="dd893-225">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="dd893-225">about_Jobs</span></span>](about_Jobs.md)
- [<span data-ttu-id="dd893-226">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="dd893-226">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)
- [<span data-ttu-id="dd893-227">about_Thread_Jobs</span><span class="sxs-lookup"><span data-stu-id="dd893-227">about_Thread_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_Thread_Jobs)
- [<span data-ttu-id="dd893-228">about_Remote</span><span class="sxs-lookup"><span data-stu-id="dd893-228">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="dd893-229">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="dd893-229">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)
- [<span data-ttu-id="dd893-230">Start-Job</span><span class="sxs-lookup"><span data-stu-id="dd893-230">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="dd893-231">Get-Job</span><span class="sxs-lookup"><span data-stu-id="dd893-231">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="dd893-232">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="dd893-232">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="dd893-233">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="dd893-233">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="dd893-234">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="dd893-234">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
- [<span data-ttu-id="dd893-235">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="dd893-235">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)
- [<span data-ttu-id="dd893-236">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="dd893-236">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)
- [<span data-ttu-id="dd893-237">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="dd893-237">Exit-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Exit-PSSession)
