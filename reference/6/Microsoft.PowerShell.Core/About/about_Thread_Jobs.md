---
description: 提供 PowerShell 執行緒型作業的相關資訊。 執行緒作業是背景工作的類型，會在目前會話進程內的不同執行緒中執行命令或運算式。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/11/2020
online version: 1.0.0
schema: 2.0.0
title: about_Thread_Jobs
ms.openlocfilehash: ba6251a195d3efdebd427b3f705386336b069211
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524476"
---
# <a name="about-thread-jobs"></a><span data-ttu-id="8f645-105">關於執行緒作業</span><span class="sxs-lookup"><span data-stu-id="8f645-105">About Thread Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="8f645-106">簡短描述</span><span class="sxs-lookup"><span data-stu-id="8f645-106">Short description</span></span>

<span data-ttu-id="8f645-107">提供 PowerShell 執行緒型作業的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8f645-107">Provides information about PowerShell thread-based jobs.</span></span> <span data-ttu-id="8f645-108">執行緒作業是背景工作的類型，會在目前會話進程內的不同執行緒中執行命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="8f645-108">A thread job is a type of background job that runs a command or expression in a separate thread within the current session process.</span></span>

## <a name="long-description"></a><span data-ttu-id="8f645-109">完整描述</span><span class="sxs-lookup"><span data-stu-id="8f645-109">Long description</span></span>

<span data-ttu-id="8f645-110">PowerShell 會透過作業同時執行命令和腳本。</span><span class="sxs-lookup"><span data-stu-id="8f645-110">PowerShell concurrently runs commands and scripts through jobs.</span></span> <span data-ttu-id="8f645-111">PowerShell 提供三種工作類型來支援平行存取。</span><span class="sxs-lookup"><span data-stu-id="8f645-111">There are three jobs types provided by PowerShell to support concurrency.</span></span>

- <span data-ttu-id="8f645-112">`RemoteJob` -命令和腳本會在遠端會話中執行。</span><span class="sxs-lookup"><span data-stu-id="8f645-112">`RemoteJob` - Commands and scripts run in a remote session.</span></span> <span data-ttu-id="8f645-113">如需詳細資訊，請參閱 [about_Remote_Jobs](about_Remote_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="8f645-113">For information, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>
- <span data-ttu-id="8f645-114">`BackgroundJob` -命令和腳本會在本機電腦上的個別進程中執行。</span><span class="sxs-lookup"><span data-stu-id="8f645-114">`BackgroundJob` - Commands and scripts run in a separate process on the local machine.</span></span> <span data-ttu-id="8f645-115">如需詳細資訊，請參閱 [about_Jobs](about_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="8f645-115">For more information, see [about_Jobs](about_Jobs.md).</span></span>
- <span data-ttu-id="8f645-116">`PSTaskJob` 或 `ThreadJob` -命令和腳本會在本機電腦上相同進程內的個別執行緒中執行。</span><span class="sxs-lookup"><span data-stu-id="8f645-116">`PSTaskJob` or `ThreadJob` - Commands and scripts run in a separate thread within the same process on the local machine.</span></span>

<span data-ttu-id="8f645-117">以執行緒為基礎的作業不像遠端和背景工作一樣健全，因為它們在不同執行緒上的相同進程中執行。</span><span class="sxs-lookup"><span data-stu-id="8f645-117">Thread-based jobs are not as robust as remote and background jobs, because they run in the same process on different threads.</span></span> <span data-ttu-id="8f645-118">如果有一項作業發生嚴重錯誤，導致進程損毀，則會終止進程中的所有其他工作。</span><span class="sxs-lookup"><span data-stu-id="8f645-118">If one job has a critical error that crashes the process, then all other jobs in the process are terminated.</span></span>

<span data-ttu-id="8f645-119">不過，以執行緒為基礎的作業需要較少的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="8f645-119">However, thread-based jobs require less overhead.</span></span> <span data-ttu-id="8f645-120">它們不會使用遠端層或序列化。</span><span class="sxs-lookup"><span data-stu-id="8f645-120">They don't use the remoting layer or serialization.</span></span> <span data-ttu-id="8f645-121">結果物件會傳回做為目前會話中之即時物件的參考。</span><span class="sxs-lookup"><span data-stu-id="8f645-121">The result objects are returned as references to live objects in the current session.</span></span> <span data-ttu-id="8f645-122">如果沒有此額外負荷，以執行緒為基礎的作業執行速度會更快，且使用的資源比其他作業類型還要少。</span><span class="sxs-lookup"><span data-stu-id="8f645-122">Without this overhead, thread-based jobs run faster and use fewer resources than the other job types.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8f645-123">建立作業的父會話也會監視作業狀態，並收集管線資料。</span><span class="sxs-lookup"><span data-stu-id="8f645-123">The parent session that created the job also monitors the job status and collects pipeline data.</span></span> <span data-ttu-id="8f645-124">當工作達到已完成狀態時，父進程會終止作業子進程。</span><span class="sxs-lookup"><span data-stu-id="8f645-124">The job child process is terminated by the parent process once the job reaches a finished state.</span></span> <span data-ttu-id="8f645-125">如果父會話終止，則所有執行中的子工作都會連同其子進程一起終止。</span><span class="sxs-lookup"><span data-stu-id="8f645-125">If the parent session is terminated, all running child jobs are terminated along with their child processes.</span></span>

<span data-ttu-id="8f645-126">有兩種方法可以解決這種情況：</span><span class="sxs-lookup"><span data-stu-id="8f645-126">There are two ways work around this situation:</span></span>

1. <span data-ttu-id="8f645-127">用 `Invoke-Command` 來建立在已中斷連線的會話中執行的作業。</span><span class="sxs-lookup"><span data-stu-id="8f645-127">Use `Invoke-Command` to create jobs that run in disconnected sessions.</span></span> <span data-ttu-id="8f645-128">如需詳細資訊，請參閱 [about_Remote_Jobs](about_Remote_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="8f645-128">For more information, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>
1. <span data-ttu-id="8f645-129">用 `Start-Process` 來建立新的處理常式，而不是作業。</span><span class="sxs-lookup"><span data-stu-id="8f645-129">Use `Start-Process` to create a new process rather than a job.</span></span> <span data-ttu-id="8f645-130">如需詳細資訊，請參閱 [啟動流程](xref:Microsoft.PowerShell.Management.Start-Process)。</span><span class="sxs-lookup"><span data-stu-id="8f645-130">For more information, see [Start-Process](xref:Microsoft.PowerShell.Management.Start-Process).</span></span>

## <a name="how-to-start-and-manage-thread-based-jobs"></a><span data-ttu-id="8f645-131">如何啟動及管理以執行緒為基礎的作業</span><span class="sxs-lookup"><span data-stu-id="8f645-131">How to start and manage thread-based jobs</span></span>

<span data-ttu-id="8f645-132">有兩種方式可以啟動以執行緒為基礎的作業：</span><span class="sxs-lookup"><span data-stu-id="8f645-132">There are two ways to start thread-based jobs:</span></span>

- <span data-ttu-id="8f645-133">`Start-ThreadJob` -從 **ThreadJob** 模組</span><span class="sxs-lookup"><span data-stu-id="8f645-133">`Start-ThreadJob` - from the **ThreadJob** module</span></span>
- <span data-ttu-id="8f645-134">`ForEach-Object -Parallel -AsJob` -已在 PowerShell 7.0 中新增平行功能</span><span class="sxs-lookup"><span data-stu-id="8f645-134">`ForEach-Object -Parallel -AsJob` - the parallel feature was added in PowerShell 7.0</span></span>

<span data-ttu-id="8f645-135">使用 [about_Jobs](about_Jobs.md)所述的相同 **工作** Cmdlet 來管理以執行緒為基礎的作業。</span><span class="sxs-lookup"><span data-stu-id="8f645-135">Use the same **Job** cmdlets described in [about_Jobs](about_Jobs.md) to manage thread-based jobs.</span></span>

### <a name="using-start-threadjob"></a><span data-ttu-id="8f645-136">使用 `Start-ThreadJob`</span><span class="sxs-lookup"><span data-stu-id="8f645-136">Using `Start-ThreadJob`</span></span>

<span data-ttu-id="8f645-137">**ThreadJob** 模組第一次隨附于 PowerShell 6。</span><span class="sxs-lookup"><span data-stu-id="8f645-137">The **ThreadJob** module first shipped with PowerShell 6.</span></span> <span data-ttu-id="8f645-138">也可以從 Windows PowerShell 5.1 的 PowerShell 資源庫安裝。</span><span class="sxs-lookup"><span data-stu-id="8f645-138">It can also be installed from the PowerShell Gallery for Windows PowerShell 5.1.</span></span>

<span data-ttu-id="8f645-139">若要在本機電腦上啟動執行緒作業，請使用 `Start-ThreadJob` Cmdlet 搭配以大括弧括住的命令或腳本 (`{ }`) 。</span><span class="sxs-lookup"><span data-stu-id="8f645-139">To start a thread job on the local computer, use the `Start-ThreadJob` cmdlet with a command or script enclosed in curly braces (`{ }`).</span></span>

<span data-ttu-id="8f645-140">下列範例會啟動在 `Get-Process` 本機電腦上執行命令的執行緒作業。</span><span class="sxs-lookup"><span data-stu-id="8f645-140">The following example starts a thread job that runs a `Get-Process` command on the local computer.</span></span>

```powershell
Start-ThreadJob -ScriptBlock { Get-Process }
```

<span data-ttu-id="8f645-141">此 `Start-ThreadJob` 命令會傳回 `ThreadJob` 代表正在執行之作業的物件。</span><span class="sxs-lookup"><span data-stu-id="8f645-141">The `Start-ThreadJob` command returns a `ThreadJob` object that represents the running job.</span></span> <span data-ttu-id="8f645-142">工作物件包含工作的相關實用資訊，包括其目前正在執行的狀態。</span><span class="sxs-lookup"><span data-stu-id="8f645-142">The job object contains useful information about the job including its current running status.</span></span> <span data-ttu-id="8f645-143">它會在產生結果時收集工作結果。</span><span class="sxs-lookup"><span data-stu-id="8f645-143">It collects the results of the job as the results are being generated.</span></span>

### <a name="using-foreach-object--parallel--asjob"></a><span data-ttu-id="8f645-144">使用 `ForEach-Object -Parallel -AsJob`</span><span class="sxs-lookup"><span data-stu-id="8f645-144">Using `ForEach-Object -Parallel -AsJob`</span></span>

<span data-ttu-id="8f645-145">PowerShell 7.0 已將新的參數集新增至 `ForEach-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8f645-145">PowerShell 7.0 added a new parameter set to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="8f645-146">新的參數可讓您在平行線程中以 PowerShell 作業的形式執行腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="8f645-146">The new parameters allow you to run script blocks in parallel threads as PowerShell jobs.</span></span>

<span data-ttu-id="8f645-147">您可以透過管線將資料傳送至 `ForEach-Object -Parallel` 。</span><span class="sxs-lookup"><span data-stu-id="8f645-147">You can pipe data to `ForEach-Object -Parallel`.</span></span> <span data-ttu-id="8f645-148">資料會傳遞至平行執行的腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="8f645-148">The data is passed to the script block that is run in parallel.</span></span> <span data-ttu-id="8f645-149">`-AsJob`參數會為每個平行線程建立工作物件。</span><span class="sxs-lookup"><span data-stu-id="8f645-149">The `-AsJob` parameter creates jobs objects for each of the parallel threads.</span></span>

<span data-ttu-id="8f645-150">下列命令會啟動一個工作，其中包含以管道傳送至命令的每個輸入值的子工作。</span><span class="sxs-lookup"><span data-stu-id="8f645-150">The following command starts a job that contains child jobs for each input value piped to the command.</span></span> <span data-ttu-id="8f645-151">每個子作業都會以 `Write-Output` 輸送的輸入值做為引數來執行命令。</span><span class="sxs-lookup"><span data-stu-id="8f645-151">Each child job runs the `Write-Output` command with a piped input value as the argument.</span></span>

```powershell
1..5 | ForEach-Object -Parallel { Write-Output $_ } -AsJob
```

<span data-ttu-id="8f645-152">此 `ForEach-Object -Parallel` 命令會傳回 `PSTaskJob` 物件，其中包含每個管道輸入值的子工作。</span><span class="sxs-lookup"><span data-stu-id="8f645-152">The `ForEach-Object -Parallel` command returns a `PSTaskJob` object that contains child jobs for each piped input value.</span></span> <span data-ttu-id="8f645-153">工作物件包含有關子工作執行狀態的有用資訊。</span><span class="sxs-lookup"><span data-stu-id="8f645-153">The job object contains useful information about the child jobs running status.</span></span> <span data-ttu-id="8f645-154">它會在產生結果時收集子工作的結果。</span><span class="sxs-lookup"><span data-stu-id="8f645-154">It collects the results of the child jobs as the results are being generated.</span></span>

## <a name="how-to-wait-for-a-job-to-complete-and-retrieve-job-results"></a><span data-ttu-id="8f645-155">如何等候工作完成並取出工作結果</span><span class="sxs-lookup"><span data-stu-id="8f645-155">How to wait for a job to complete and retrieve job results</span></span>

<span data-ttu-id="8f645-156">您可以使用 PowerShell 工作 Cmdlet （例如 `Wait-Job` 和） `Receive-Job` 來等候作業完成，然後傳回作業所產生的所有結果。</span><span class="sxs-lookup"><span data-stu-id="8f645-156">You can use PowerShell job cmdlets, such as `Wait-Job` and `Receive-Job` to wait for a job to complete and then return all results generated by the job.</span></span>

<span data-ttu-id="8f645-157">下列命令會啟動執行命令的執行緒作業 `Get-Process` ，然後等候命令完成，最後傳回命令所產生的所有資料結果。</span><span class="sxs-lookup"><span data-stu-id="8f645-157">The following command starts a thread job that runs a `Get-Process` command, then waits for the command to complete, and finally returns all data results generated by the command.</span></span>

```powershell
Start-ThreadJob -ScriptBlock { Get-Process } | Wait-Job | Receive-Job
```

<span data-ttu-id="8f645-158">下列命令會啟動執行 `Write-Output` 每個輸送輸入之命令的作業，然後等候所有子工作完成，最後傳回子工作所產生的所有資料結果。</span><span class="sxs-lookup"><span data-stu-id="8f645-158">The following command starts a job that runs a `Write-Output` command for each piped input, then waits for all child jobs to complete, and finally returns all data results generated by the child jobs.</span></span>

```powershell
1..5 | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job
```

<span data-ttu-id="8f645-159">Cmdlet 會傳回 `Receive-Job` 子工作的結果。</span><span class="sxs-lookup"><span data-stu-id="8f645-159">The `Receive-Job` cmdlet returns the results of the child jobs.</span></span>

```powershell
1
3
2
4
5
```

<span data-ttu-id="8f645-160">由於每個子工作都平行執行，因此不保證產生的結果順序。</span><span class="sxs-lookup"><span data-stu-id="8f645-160">Because each child job runs parallel, the order of the generated results is not guaranteed.</span></span>

## <a name="thread-job-performance"></a><span data-ttu-id="8f645-161">執行緒作業效能</span><span class="sxs-lookup"><span data-stu-id="8f645-161">Thread job performance</span></span>

<span data-ttu-id="8f645-162">執行緒作業比其他類型的作業更快且更輕量。</span><span class="sxs-lookup"><span data-stu-id="8f645-162">Thread jobs are faster and lighter weight than other types of jobs.</span></span> <span data-ttu-id="8f645-163">但是，相較于工作正在進行的工作，它們的負荷仍可能很大。</span><span class="sxs-lookup"><span data-stu-id="8f645-163">But they still have overhead that can be large when compared to work the job is doing.</span></span>

<span data-ttu-id="8f645-164">PowerShell 會在會話中執行命令和腳本。</span><span class="sxs-lookup"><span data-stu-id="8f645-164">PowerShell runs commands and script in a session.</span></span> <span data-ttu-id="8f645-165">在會話中，一次只能執行一個命令或腳本。</span><span class="sxs-lookup"><span data-stu-id="8f645-165">Only one command or script can run at a time in a session.</span></span> <span data-ttu-id="8f645-166">因此，在執行多個工作時，每個工作會在不同的會話中執行。</span><span class="sxs-lookup"><span data-stu-id="8f645-166">So when running multiple jobs, each job runs in a separate session.</span></span> <span data-ttu-id="8f645-167">每個會話都有額外負荷。</span><span class="sxs-lookup"><span data-stu-id="8f645-167">Each session contributes to the overhead.</span></span>

<span data-ttu-id="8f645-168">當執行緒作業所執行的工作大於用來執行作業的會話負荷時，會提供最佳效能。</span><span class="sxs-lookup"><span data-stu-id="8f645-168">Thread jobs provide the best performance when the work they perform is greater than the overhead of the session used to run the job.</span></span> <span data-ttu-id="8f645-169">符合此準則的案例有兩種。</span><span class="sxs-lookup"><span data-stu-id="8f645-169">There are two cases for that meet this criteria.</span></span>

- <span data-ttu-id="8f645-170">工作需要大量計算-在多個執行緒工作上執行腳本可利用多個處理器核心並更快完成。</span><span class="sxs-lookup"><span data-stu-id="8f645-170">Work is compute intensive - Running a script on multiple thread jobs can take advantage of multiple processor cores and complete faster.</span></span>

- <span data-ttu-id="8f645-171">工作包含大量等候的腳本，該腳本會花時間等候 i/o 或遠端呼叫的結果。</span><span class="sxs-lookup"><span data-stu-id="8f645-171">Work consists of significant waiting - A script that spends time waiting for I/O or remote call results.</span></span> <span data-ttu-id="8f645-172">平行執行的速度通常會比循序執行的速度還要快。</span><span class="sxs-lookup"><span data-stu-id="8f645-172">Running in parallel usually completes quicker than if run sequentially.</span></span>

```powershell
(Measure-Command {
    1..1000 | ForEach { Start-ThreadJob { Write-Output "Hello $using:_" } } | Receive-Job -Wait
}).TotalMilliseconds
36860.8226

(Measure-Command {
    1..1000 | ForEach-Object { "Hello: $_" }
}).TotalMilliseconds
7.1975
```

<span data-ttu-id="8f645-173">上述第一個範例顯示一個 foreach 迴圈，該迴圈會建立1000執行緒作業來進行簡單的字串寫入。</span><span class="sxs-lookup"><span data-stu-id="8f645-173">The first example above shows a foreach loop that creates 1000 thread jobs to do a simple string write.</span></span> <span data-ttu-id="8f645-174">因為作業額外負荷，所以需要超過36秒才能完成。</span><span class="sxs-lookup"><span data-stu-id="8f645-174">Due to job overhead, it takes over 36 seconds to complete.</span></span>

<span data-ttu-id="8f645-175">第二個範例會 `ForEach` 執行 Cmdlet 來執行相同的1000作業。</span><span class="sxs-lookup"><span data-stu-id="8f645-175">The second example runs the `ForEach` cmdlet to do the same 1000 operations.</span></span>
<span data-ttu-id="8f645-176">這次 `ForEach-Object` 會在單一線程上循序執行，而不會產生任何作業額外負荷。</span><span class="sxs-lookup"><span data-stu-id="8f645-176">This time, `ForEach-Object` runs sequentially, on a single thread, without any job overhead.</span></span> <span data-ttu-id="8f645-177">它只會在7毫秒內完成。</span><span class="sxs-lookup"><span data-stu-id="8f645-177">It completes in a mere 7 milliseconds.</span></span>

<span data-ttu-id="8f645-178">在下列範例中，會針對10個不同的系統記錄檔收集最多5000個專案。</span><span class="sxs-lookup"><span data-stu-id="8f645-178">In the following example, up to 5000 entries are collected for 10 separate system logs.</span></span> <span data-ttu-id="8f645-179">由於腳本牽涉到讀取一些記錄，因此平行執行作業是有意義的。</span><span class="sxs-lookup"><span data-stu-id="8f645-179">Since the script involves reading a number of logs, it makes sense to do the operations in parallel.</span></span>

```powershell
$logNames.count
10

Measure-Command {
    $logs = $logNames | ForEach-Object {
        Get-WinEvent -LogName $_ -MaxEvents 5000 2>$null
    }
}

TotalMilliseconds : 252398.4321 (4 minutes 12 seconds)
$logs.Count
50000
```

<span data-ttu-id="8f645-180">腳本會在工作以平行方式執行的一半時間內完成。</span><span class="sxs-lookup"><span data-stu-id="8f645-180">The script completes in half the time when the jobs are run in parallel.</span></span>

```powershell
Measure-Command {
    $logs = $logNames | ForEach {
        Start-ThreadJob {
            Get-WinEvent -LogName $using:_ -MaxEvents 5000 2>$null
        } -ThrottleLimit 10
    } | Wait-Job | Receive-Job
}

TotalMilliseconds : 115994.3 (1 minute 56 seconds)
$logs.Count
50000
```

## <a name="thread-jobs-and-variables"></a><span data-ttu-id="8f645-181">執行緒作業和變數</span><span class="sxs-lookup"><span data-stu-id="8f645-181">Thread jobs and variables</span></span>

<span data-ttu-id="8f645-182">有多種方式可將值傳遞至以執行緒為基礎的作業。</span><span class="sxs-lookup"><span data-stu-id="8f645-182">There are multiple ways to pass values into the thread-based jobs.</span></span>

<span data-ttu-id="8f645-183">`Start-ThreadJob` 可以接受輸送至 Cmdlet 的變數，透過關鍵詞傳遞至腳本區塊， `$using` 或透過 **ArgumentList** 參數傳入。</span><span class="sxs-lookup"><span data-stu-id="8f645-183">`Start-ThreadJob` can accept variables that are piped to the cmdlet, passed in to the script block via the `$using` keyword, or passed in via the **ArgumentList** parameter.</span></span>

```powershell
$msg = "Hello"

$msg | Start-ThreadJob { $input | Write-Output } | Wait-Job | Receive-Job

Start-ThreadJob { Write-Output $using:msg } | Wait-Job | Receive-Job

Start-ThreadJob { param ([string] $message) Write-Output $message } -ArgumentList @($msg) |
  Wait-Job | Receive-Job
```

<span data-ttu-id="8f645-184">`ForEach-Object -Parallel` 接受變數中的管道，以及透過關鍵詞直接傳遞至腳本區塊的變數 `$using` 。</span><span class="sxs-lookup"><span data-stu-id="8f645-184">`ForEach-Object -Parallel` accepts piped in variables, and variables passed directly to the script block via the `$using` keyword.</span></span>

```powershell
$msg = "Hello"

$msg | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job

1..1 | ForEach-Object -Parallel { Write-Output $using:msg } -AsJob | Wait-Job | Receive-Job
```

<span data-ttu-id="8f645-185">因為執行緒作業是在相同的進程中執行，所以任何傳遞至作業的變數參考型別都必須小心處理。</span><span class="sxs-lookup"><span data-stu-id="8f645-185">Since thread jobs run in the same process, any variable reference type passed into the job has to be treated carefully.</span></span> <span data-ttu-id="8f645-186">如果它不是安全線程的物件，則永遠不會將它指派給，而且永遠不應該在其上叫用方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="8f645-186">If it is not a thread safe object, then it should never be assigned to, and method and properties should never be invoked on it.</span></span>

<span data-ttu-id="8f645-187">下列範例會將安全線程的 .NET `ConcurrentDictionary` 物件傳遞至所有子工作，以收集唯一的命名進程物件。</span><span class="sxs-lookup"><span data-stu-id="8f645-187">The following example passes a thread-safe .NET `ConcurrentDictionary` object to all child jobs to collect uniquely named process objects.</span></span> <span data-ttu-id="8f645-188">由於它是安全線程的物件，因此可以在進程中同時執行工作時安全地使用它。</span><span class="sxs-lookup"><span data-stu-id="8f645-188">Since it is a thread safe object, it can be safely used while the jobs run concurrently in the process.</span></span>

```powershell
$threadSafeDictionary = [System.Collections.Concurrent.ConcurrentDictionary[string,object]]::new()
$jobs = Get-Process | ForEach {
    Start-ThreadJob {
        $proc = $using:_
        $dict = $using:threadSafeDictionary
        $dict.TryAdd($proc.ProcessName, $proc)
    }
}
$jobs | Wait-Job | Receive-Job

$threadSafeDictionary.Count
96

$threadSafeDictionary["pwsh"]

NPM(K)  PM(M)   WS(M) CPU(s)    Id SI ProcessName
------  -----   ----- ------    -- -- -----------
  112  108.25  124.43  69.75 16272  1 pwsh
```

## <a name="see-also"></a><span data-ttu-id="8f645-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f645-189">See also</span></span>

- [<span data-ttu-id="8f645-190">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="8f645-190">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)
- [<span data-ttu-id="8f645-191">about_Thread_Jobs</span><span class="sxs-lookup"><span data-stu-id="8f645-191">about_Thread_Jobs</span></span>](about_Thread_Jobs.md)
- [<span data-ttu-id="8f645-192">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="8f645-192">about_Job_Details</span></span>](about_Job_Details.md)
- [<span data-ttu-id="8f645-193">about_Remote</span><span class="sxs-lookup"><span data-stu-id="8f645-193">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="8f645-194">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="8f645-194">about_PSSessions</span></span>](about_PSSessions.md)
- [<span data-ttu-id="8f645-195">Start-Job</span><span class="sxs-lookup"><span data-stu-id="8f645-195">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="8f645-196">Get-Job</span><span class="sxs-lookup"><span data-stu-id="8f645-196">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="8f645-197">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="8f645-197">Receive-Job</span></span>](xref:Microsoft.PowerShell.Core.Receive-Job)
- [<span data-ttu-id="8f645-198">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="8f645-198">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="8f645-199">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="8f645-199">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="8f645-200">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="8f645-200">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
