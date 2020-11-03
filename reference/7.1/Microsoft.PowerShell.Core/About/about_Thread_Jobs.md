---
description: 提供 PowerShell 執行緒型作業的相關資訊。 執行緒作業是背景工作的類型，會在目前會話進程內的不同執行緒中執行命令或運算式。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/16/2020
online version: 1.0.0
schema: 2.0.0
title: about_Thread_Jobs
ms.openlocfilehash: d3f7c2754a2e54bc1b6f9fb95d1cf6ce2fed5b9b
ms.sourcegitcommit: 108686b166672cc08817c637dd93eb1ad830511d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "93208583"
---
# <a name="about-thread-jobs"></a><span data-ttu-id="716c8-105">關於執行緒作業</span><span class="sxs-lookup"><span data-stu-id="716c8-105">About Thread Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="716c8-106">簡短描述</span><span class="sxs-lookup"><span data-stu-id="716c8-106">Short description</span></span>

<span data-ttu-id="716c8-107">提供 PowerShell 執行緒型作業的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="716c8-107">Provides information about PowerShell thread-based jobs.</span></span> <span data-ttu-id="716c8-108">執行緒作業是背景工作的類型，會在目前會話進程內的不同執行緒中執行命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="716c8-108">A thread job is a type of background job that runs a command or expression in a separate thread within the current session process.</span></span>

## <a name="long-description"></a><span data-ttu-id="716c8-109">完整描述</span><span class="sxs-lookup"><span data-stu-id="716c8-109">Long description</span></span>

<span data-ttu-id="716c8-110">本文說明如何在本機電腦上的 PowerShell 中執行執行緒作業。</span><span class="sxs-lookup"><span data-stu-id="716c8-110">This article explains how to run thread jobs in PowerShell on a local computer.</span></span>
<span data-ttu-id="716c8-111">如需在本機電腦上執行背景工作的詳細資訊，請參閱 [about_Jobs](about_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="716c8-111">For information about running background jobs on a local computer, see [about_Jobs](about_Jobs.md).</span></span>

<span data-ttu-id="716c8-112">您可以使用兩種方式之一來啟動執行緒作業。</span><span class="sxs-lookup"><span data-stu-id="716c8-112">You can start a thread job in one of two ways.</span></span>

<span data-ttu-id="716c8-113">第一種方式是使用 `Start-ThreadJob` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="716c8-113">The first way is with the `Start-ThreadJob` cmdlet.</span></span> <span data-ttu-id="716c8-114">此 Cmdlet 適用于 PowerShell 隨附的 **ThreadJob** 模組。</span><span class="sxs-lookup"><span data-stu-id="716c8-114">This cmdlet is available in the **ThreadJob** module that ships with PowerShell.</span></span> <span data-ttu-id="716c8-115">`Start-ThreadJob` 傳回單一工作物件，該物件會封裝執行中的命令或腳本，並可與所有 PowerShell 作業操作 Cmdlet 一起使用。</span><span class="sxs-lookup"><span data-stu-id="716c8-115">`Start-ThreadJob` returns a single job object that encapsulates the running command or script, and can be used with all PowerShell job manipulating cmdlets.</span></span>

<span data-ttu-id="716c8-116">第二種方式是使用 `ForEach-Object` Cmdlet， `-Parallel` 搭配參數腳本區塊引數和 `-AsJob` 參數參數。</span><span class="sxs-lookup"><span data-stu-id="716c8-116">The second way is with the `ForEach-Object` cmdlet, with the `-Parallel` parameter script block argument along with the `-AsJob` parameter switch.</span></span> <span data-ttu-id="716c8-117">這個 Cmdlet 會傳回單一 (父) 工作物件，其中包含每個以管線傳送至 Cmdlet 的輸入子工作。</span><span class="sxs-lookup"><span data-stu-id="716c8-117">This cmdlet returns a single (parent) job object that contains a child job for each input piped to the cmdlet.</span></span> <span data-ttu-id="716c8-118">每個子工作會在不同的執行緒中執行腳本，並 (`-ThrottleLimit`) 限制在指定時間執行的子工作數目。</span><span class="sxs-lookup"><span data-stu-id="716c8-118">Each child job runs script in a separate thread with a (`-ThrottleLimit`) limit to how many child jobs run at a given time.</span></span>

## <a name="the-job-cmdlets"></a><span data-ttu-id="716c8-119">作業 CMDLET</span><span class="sxs-lookup"><span data-stu-id="716c8-119">THE JOB CMDLETS</span></span>

|<span data-ttu-id="716c8-120">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="716c8-120">Cmdlet</span></span>           |<span data-ttu-id="716c8-121">描述</span><span class="sxs-lookup"><span data-stu-id="716c8-121">Description</span></span>                                            |
|-----------------|-------------------------------------------------------|
|`Start-ThreadJob`|<span data-ttu-id="716c8-122">在本機電腦上啟動執行緒作業。</span><span class="sxs-lookup"><span data-stu-id="716c8-122">Starts a thread job on a local computer.</span></span>               |
|`ForEach-Object` |<span data-ttu-id="716c8-123">啟動每個管道輸入物件的執行緒作業（當</span><span class="sxs-lookup"><span data-stu-id="716c8-123">Starts thread jobs for each piped input object, when</span></span>   |
|                 |<span data-ttu-id="716c8-124">搭配-Parallel 和-AsJob 參數使用。</span><span class="sxs-lookup"><span data-stu-id="716c8-124">used with -Parallel and -AsJob parameters.</span></span>             |
|`Get-Job`        |<span data-ttu-id="716c8-125">取得在目前會話中啟動的工作。</span><span class="sxs-lookup"><span data-stu-id="716c8-125">Gets the jobs that were started in the current session.</span></span>|
|`Receive-Job`    |<span data-ttu-id="716c8-126">取得工作的結果。</span><span class="sxs-lookup"><span data-stu-id="716c8-126">Gets the results of jobs.</span></span>                              |
|`Stop-Job`       |<span data-ttu-id="716c8-127">停止正在執行的作業。</span><span class="sxs-lookup"><span data-stu-id="716c8-127">Stops a running job.</span></span>                                   |
|`Wait-Job`       |<span data-ttu-id="716c8-128">抑制命令提示字元，直到其中一個或所有工作為</span><span class="sxs-lookup"><span data-stu-id="716c8-128">Suppresses the command prompt until one or all jobs are</span></span>|
|                 |<span data-ttu-id="716c8-129">完成。</span><span class="sxs-lookup"><span data-stu-id="716c8-129">complete.</span></span>                                              |
|`Remove-Job`     |<span data-ttu-id="716c8-130">刪除作業。</span><span class="sxs-lookup"><span data-stu-id="716c8-130">Deletes a job.</span></span>                                         |

## <a name="how-to-start-a-thread-job-on-the-local-computer"></a><span data-ttu-id="716c8-131">如何在本機電腦上啟動執行緒作業</span><span class="sxs-lookup"><span data-stu-id="716c8-131">How to start a thread job on the local computer</span></span>

<span data-ttu-id="716c8-132">若要在本機電腦上啟動執行緒作業，請使用 `Start-ThreadJob` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="716c8-132">To start a thread job on the local computer, use the `Start-ThreadJob` cmdlet.</span></span>

<span data-ttu-id="716c8-133">若要撰寫 `Start-ThreadJob` 命令，請以大括弧括住命令或腳本 (`{ }`) 。</span><span class="sxs-lookup"><span data-stu-id="716c8-133">To write a `Start-ThreadJob` command, enclose the command or script the job runs in curly braces (`{ }`).</span></span>

<span data-ttu-id="716c8-134">下列命令會啟動在 `Get-Process` 本機電腦上執行命令的執行緒作業。</span><span class="sxs-lookup"><span data-stu-id="716c8-134">The following command starts a thread job that runs a `Get-Process` command on the local computer.</span></span>

```powershell
Start-ThreadJob -ScriptBlock { Get-Process }
```

<span data-ttu-id="716c8-135">此 `Start-ThreadJob` 命令會傳回 `ThreadJob` 代表正在執行之作業的物件。</span><span class="sxs-lookup"><span data-stu-id="716c8-135">The `Start-ThreadJob` command returns a `ThreadJob` object that represents the running job.</span></span> <span data-ttu-id="716c8-136">工作物件包含工作的相關實用資訊，包括其目前正在執行的狀態。</span><span class="sxs-lookup"><span data-stu-id="716c8-136">The job object contains useful information about the job including its current running status.</span></span> <span data-ttu-id="716c8-137">它會在產生結果時收集工作結果。</span><span class="sxs-lookup"><span data-stu-id="716c8-137">It collects the results of the job as the results are being generated.</span></span>

<span data-ttu-id="716c8-138">若要撰寫 `ForEach-Object -Parallel` 命令，請使用管線將資料傳送至命令，並將工作以大括弧括住的命令或腳本 (`{}`) 。</span><span class="sxs-lookup"><span data-stu-id="716c8-138">To write a `ForEach-Object -Parallel` command, pipe data to the command and enclose the command or script the job runs in curly braces(`{}`).</span></span> <span data-ttu-id="716c8-139">使用 `-AsJob` 參數參數，以傳回工作物件。</span><span class="sxs-lookup"><span data-stu-id="716c8-139">Use the `-AsJob` parameter switch so that a job object is returned.</span></span>

<span data-ttu-id="716c8-140">下列命令會啟動一個工作，其中包含以管道傳送至命令的每個輸入值的子工作。</span><span class="sxs-lookup"><span data-stu-id="716c8-140">The following command starts a job that contains child jobs for each input value piped to the command.</span></span> <span data-ttu-id="716c8-141">每個子作業都會以 `Write-Output` 輸送的輸入值做為引數來執行命令。</span><span class="sxs-lookup"><span data-stu-id="716c8-141">Each child job runs the `Write-Output` command with a piped input value as the argument.</span></span>

```powershell
1..5 | ForEach-Object -Parallel { Write-Output $_ } -AsJob
```

<span data-ttu-id="716c8-142">此 `ForEach-Object -Parallel` 命令會傳回 `PSTaskJob` 物件，其中包含每個管道輸入值的子工作。</span><span class="sxs-lookup"><span data-stu-id="716c8-142">The `ForEach-Object -Parallel` command returns a `PSTaskJob` object that contains child jobs for each piped input value.</span></span> <span data-ttu-id="716c8-143">工作物件包含有關子工作執行狀態的有用資訊。</span><span class="sxs-lookup"><span data-stu-id="716c8-143">The job object contains useful information about the child jobs running status.</span></span> <span data-ttu-id="716c8-144">它會在產生結果時收集子工作的結果。</span><span class="sxs-lookup"><span data-stu-id="716c8-144">It collects the results of the child jobs as the results are being generated.</span></span>

## <a name="how-to-wait-for-a-job-to-complete-and-retrieve-job-results"></a><span data-ttu-id="716c8-145">如何等候工作完成並取出工作結果</span><span class="sxs-lookup"><span data-stu-id="716c8-145">How to wait for a job to complete and retrieve job results</span></span>

<span data-ttu-id="716c8-146">您可以使用 PowerShell 工作 Cmdlet （例如 `Wait-Job` 和） `Receive-Job` 來等候作業完成，然後傳回作業所產生的所有結果。</span><span class="sxs-lookup"><span data-stu-id="716c8-146">You can use PowerShell job cmdlets, such as `Wait-Job` and `Receive-Job` to wait for a job to complete and then return all results generated by the job.</span></span>

<span data-ttu-id="716c8-147">下列命令會啟動執行命令的執行緒作業 `Get-Process` ，然後等候命令完成，最後傳回命令所產生的所有資料結果。</span><span class="sxs-lookup"><span data-stu-id="716c8-147">The following command starts a thread job that runs a `Get-Process` command, then waits for the command to complete, and finally returns all data results generated by the command.</span></span>

```powershell
Start-ThreadJob -ScriptBlock { Get-Process } | Wait-Job | Receive-Job
```

<span data-ttu-id="716c8-148">下列命令會啟動執行 `Write-Output` 每個輸送輸入之命令的作業，然後等候所有子工作完成，最後傳回子工作所產生的所有資料結果。</span><span class="sxs-lookup"><span data-stu-id="716c8-148">The following command starts a job that runs a `Write-Output` command for each piped input, then waits for all child jobs to complete, and finally returns all data results generated by the child jobs.</span></span>

```powershell
1..5 | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job
```

<span data-ttu-id="716c8-149">Cmdlet 會傳回 `Receive-Job` 子工作的結果。</span><span class="sxs-lookup"><span data-stu-id="716c8-149">The `Receive-Job` cmdlet returns the results of the child jobs.</span></span>

```powershell
1
3
2
4
5
```

<span data-ttu-id="716c8-150">由於每個子工作都平行執行，因此不保證產生的結果順序。</span><span class="sxs-lookup"><span data-stu-id="716c8-150">Because each child job runs parallel, the order of the generated results is not guaranteed.</span></span>

## <a name="powershell-concurrency-and-jobs"></a><span data-ttu-id="716c8-151">PowerShell 並行和作業</span><span class="sxs-lookup"><span data-stu-id="716c8-151">PowerShell concurrency and jobs</span></span>

<span data-ttu-id="716c8-152">PowerShell 會透過作業同時執行命令和腳本。</span><span class="sxs-lookup"><span data-stu-id="716c8-152">PowerShell concurrently runs commands and script through jobs.</span></span> <span data-ttu-id="716c8-153">PowerShell 提供三個以工作為基礎的解決方案，以支援平行存取。</span><span class="sxs-lookup"><span data-stu-id="716c8-153">There are three jobs-based solutions provided by PowerShell to support concurrency.</span></span>

|<span data-ttu-id="716c8-154">工作 (Job)</span><span class="sxs-lookup"><span data-stu-id="716c8-154">Job</span></span>            |<span data-ttu-id="716c8-155">Description</span><span class="sxs-lookup"><span data-stu-id="716c8-155">Description</span></span>                                                  |
|---------------|-------------------------------------------------------------|
|`RemoteJob`    |<span data-ttu-id="716c8-156">命令和腳本會在遠端電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="716c8-156">Command and script run on a remote computer.</span></span>                 |
|`BackgroundJob`|<span data-ttu-id="716c8-157">命令和腳本在本機的個別進程中執行</span><span class="sxs-lookup"><span data-stu-id="716c8-157">Command and script run in a separate process on the local</span></span>    |
|               |<span data-ttu-id="716c8-158">新的虛擬主機。</span><span class="sxs-lookup"><span data-stu-id="716c8-158">machine.</span></span>                                                     |
|`ThreadJob`    |<span data-ttu-id="716c8-159">命令和腳本在相同的執行緒中執行</span><span class="sxs-lookup"><span data-stu-id="716c8-159">Command and script run in a separate thread within the same</span></span>  |
|               |<span data-ttu-id="716c8-160">在本機電腦上處理。</span><span class="sxs-lookup"><span data-stu-id="716c8-160">process on the local machine.</span></span>                                |

<span data-ttu-id="716c8-161">每種類型的作業都有其優點和缺點。</span><span class="sxs-lookup"><span data-stu-id="716c8-161">Each type of job has benefits and drawbacks.</span></span> <span data-ttu-id="716c8-162">在不同的電腦上或在個別的進程中遠端執行腳本有很大的隔離。</span><span class="sxs-lookup"><span data-stu-id="716c8-162">Running script remotely on a separate machine or in a separate process has great isolation.</span></span> <span data-ttu-id="716c8-163">任何錯誤都不會影響其他執行中的工作或啟動作業的用戶端。</span><span class="sxs-lookup"><span data-stu-id="716c8-163">Any errors won't affect other running jobs or the client that started the job.</span></span> <span data-ttu-id="716c8-164">但是遠端層會增加額外負荷，包括物件序列化。</span><span class="sxs-lookup"><span data-stu-id="716c8-164">But the remoting layer adds overhead, including object serialization.</span></span> <span data-ttu-id="716c8-165">在遠端會話中傳遞的所有物件都必須序列化，然後在用戶端與目標會話之間傳遞時還原序列化。</span><span class="sxs-lookup"><span data-stu-id="716c8-165">All objects passed to and from the remote session must be serialized and then deserialized as it passes between the client and the target session.</span></span> <span data-ttu-id="716c8-166">序列化作業可以針對大型複雜資料物件使用許多計算和記憶體資源。</span><span class="sxs-lookup"><span data-stu-id="716c8-166">The serialization operation can use many compute and memory resources for large complex data objects.</span></span>

## <a name="powershell-thread-based-jobs"></a><span data-ttu-id="716c8-167">以 PowerShell 執行緒為基礎的作業</span><span class="sxs-lookup"><span data-stu-id="716c8-167">PowerShell thread based jobs</span></span>

<span data-ttu-id="716c8-168">以執行緒為基礎的作業不像遠端和背景工作一樣健全，因為它們在不同執行緒上的相同進程中執行。</span><span class="sxs-lookup"><span data-stu-id="716c8-168">Thread based jobs are not as robust as Remote and Background jobs, because they run in the same process on different threads.</span></span> <span data-ttu-id="716c8-169">如果有一項作業發生嚴重錯誤，導致進程損毀，則程式中的所有其他作業也會失敗。</span><span class="sxs-lookup"><span data-stu-id="716c8-169">If one job has a critical error that crashes the process, then all other jobs in the process will also fail.</span></span>

<span data-ttu-id="716c8-170">不過，以執行緒為基礎的作業會有較少的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="716c8-170">However, thread-based jobs have much less overhead.</span></span> <span data-ttu-id="716c8-171">它們不需要使用遠端層或序列化。</span><span class="sxs-lookup"><span data-stu-id="716c8-171">They don't need to use the remoting layer or serialization.</span></span> <span data-ttu-id="716c8-172">結果是，以執行緒為基礎的作業的執行速度通常會比其他工作類型更快，且使用的資源更少。</span><span class="sxs-lookup"><span data-stu-id="716c8-172">The result is that thread-based jobs tend to run much faster and use far less resources than the other job types.</span></span>

## <a name="thread-job-performance"></a><span data-ttu-id="716c8-173">執行緒作業效能</span><span class="sxs-lookup"><span data-stu-id="716c8-173">Thread job performance</span></span>

<span data-ttu-id="716c8-174">執行緒作業比其他類型的作業更快且更輕量。</span><span class="sxs-lookup"><span data-stu-id="716c8-174">Thread jobs are faster and lighter weight than other types of jobs.</span></span> <span data-ttu-id="716c8-175">但是，相較于工作正在進行的工作，它們的負荷仍可能很大。</span><span class="sxs-lookup"><span data-stu-id="716c8-175">But they still have overhead that can be large when compared to work the job is doing.</span></span>

<span data-ttu-id="716c8-176">PowerShell 會在會話中執行命令和腳本。</span><span class="sxs-lookup"><span data-stu-id="716c8-176">PowerShell runs commands and script in a session.</span></span> <span data-ttu-id="716c8-177">在會話中，一次只能執行一個命令或腳本。</span><span class="sxs-lookup"><span data-stu-id="716c8-177">Only one command or script can run at a time in a session.</span></span> <span data-ttu-id="716c8-178">因此，在執行多個工作時，每個工作會在不同的會話中執行。</span><span class="sxs-lookup"><span data-stu-id="716c8-178">So when running multiple jobs, each job runs in a separate session.</span></span> <span data-ttu-id="716c8-179">每個會話都有額外負荷。</span><span class="sxs-lookup"><span data-stu-id="716c8-179">Each session contributes to the overhead.</span></span>

<span data-ttu-id="716c8-180">當執行緒作業所執行的工作大於用來執行作業的會話負荷時，會提供最佳效能。</span><span class="sxs-lookup"><span data-stu-id="716c8-180">Thread jobs provide the best performance when the work they perform is greater than the overhead of the session used to run the job.</span></span> <span data-ttu-id="716c8-181">符合此準則的案例有兩種。</span><span class="sxs-lookup"><span data-stu-id="716c8-181">There are two cases for that meet this criteria.</span></span>

- <span data-ttu-id="716c8-182">工作需要大量計算-在多個執行緒工作上執行腳本可利用多個處理器核心並更快完成。</span><span class="sxs-lookup"><span data-stu-id="716c8-182">Work is compute intensive - Running a script on multiple thread jobs can take advantage of multiple processor cores and complete faster.</span></span>

- <span data-ttu-id="716c8-183">工作包含大量等候的腳本，該腳本會花時間等候 i/o 或遠端呼叫的結果。</span><span class="sxs-lookup"><span data-stu-id="716c8-183">Work consists of significant waiting - A script that spends time waiting for I/O or remote call results.</span></span> <span data-ttu-id="716c8-184">平行執行的速度通常會比循序執行的速度還要快。</span><span class="sxs-lookup"><span data-stu-id="716c8-184">Running in parallel usually completes quicker than if run sequentially.</span></span>

```powershell
(Measure-Command {
    1..1000 | ForEach { Start-ThreadJob { Write-Output "Hello $using:_" } } | Receive-Job -Wait
}).TotalMilliseconds
10457.962


(Measure-Command {
    1..1000 | ForEach-Object { "Hello: $_" }
}).TotalMilliseconds
24.9277
```

<span data-ttu-id="716c8-185">上述第一個範例顯示一個 foreach 迴圈，該迴圈會建立1000執行緒作業來進行簡單的字串寫入。</span><span class="sxs-lookup"><span data-stu-id="716c8-185">The first example above shows a foreach loop that creates 1000 thread jobs to do a simple string write.</span></span> <span data-ttu-id="716c8-186">因為作業額外負荷，所以需要超過33秒才能完成。</span><span class="sxs-lookup"><span data-stu-id="716c8-186">Due to job overhead, it takes over 33 seconds to complete.</span></span>

<span data-ttu-id="716c8-187">第二個範例會執行指令 `ForEach` 程式來執行相同的1000作業，並依序執行每個字串寫入，而不會有任何作業額外負荷。</span><span class="sxs-lookup"><span data-stu-id="716c8-187">The second example runs the `ForEach` cmdlet to do the same 1000 operations and each string write is executed sequentially without any job overhead.</span></span> <span data-ttu-id="716c8-188">它只會在25毫秒內完成。</span><span class="sxs-lookup"><span data-stu-id="716c8-188">It completes in a mere 25 milliseconds.</span></span>

```powershell
$logNames.count
10

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

<span data-ttu-id="716c8-189">在上述範例中，會針對10個不同的系統記錄檔收集最多5000個專案。</span><span class="sxs-lookup"><span data-stu-id="716c8-189">In the above example, up to 5000 entries are collected for 10 separate system logs.</span></span> <span data-ttu-id="716c8-190">由於腳本牽涉到讀取一些記錄，因此平行執行作業是有意義的。</span><span class="sxs-lookup"><span data-stu-id="716c8-190">Since the script involves reading a number of logs, it makes sense to do the operations in parallel.</span></span> <span data-ttu-id="716c8-191">而且作業會以順序完成，就像腳本執行時一樣快完成兩次。</span><span class="sxs-lookup"><span data-stu-id="716c8-191">And the job completes over twice as fast as when the script is run sequentially.</span></span>

```powershell
Measure-Command {
    $logs = $logNames | ForEach-Object {
        Get-WinEvent -LogName $_ -MaxEvents 5000 2>$null
    }
}

TotalMilliseconds : 252398.4321 (4 minutes 12 seconds)
$logs.Count
50000
```

## <a name="thread-jobs-and-variables"></a><span data-ttu-id="716c8-192">執行緒作業和變數</span><span class="sxs-lookup"><span data-stu-id="716c8-192">Thread jobs and variables</span></span>

<span data-ttu-id="716c8-193">變數會以各種方式傳遞至執行緒作業。</span><span class="sxs-lookup"><span data-stu-id="716c8-193">Variables are passed into thread jobs in various ways.</span></span>

<span data-ttu-id="716c8-194">`Start-ThreadJob` 可以接受輸送至 Cmdlet 的變數，透過關鍵詞傳遞至腳本區塊， `$using` 或透過 **ArgumentList** 參數傳入。</span><span class="sxs-lookup"><span data-stu-id="716c8-194">`Start-ThreadJob` can accept variables that are piped to the cmdlet, passed in to the script block via the `$using` keyword, or passed in via the **ArgumentList** parameter.</span></span>

```powershell
$msg = "Hello"

$msg | Start-ThreadJob { $input | Write-Output } | Wait-Job | Receive-Job

Start-ThreadJob { Write-Output $using:msg } | Wait-Job | Receive-Job

Start-ThreadJob { param ([string] $message) Write-Output $message } -ArgumentList @($msg) |
  Wait-Job | Receive-Job

`ForEach-Object -Parallel` accepts piped in variables, and variables passed
directly to the script block via the `$using` keyword.

```powershell
$msg = "Hello"

$msg | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job

1..1 | ForEach-Object -Parallel { Write-Output $using:msg } -AsJob | Wait-Job | Receive-Job
```

<span data-ttu-id="716c8-195">因為執行緒作業是在相同的進程中執行，所以任何傳遞至作業的變數參考型別都必須小心處理。</span><span class="sxs-lookup"><span data-stu-id="716c8-195">Since thread jobs run in the same process, any variable reference type passed into the job has to be treated carefully.</span></span> <span data-ttu-id="716c8-196">如果它不是安全線程的物件，則永遠不會將它指派給，而且永遠不應該在其上叫用方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="716c8-196">If it is not a thread safe object, then it should never be assigned to, and method and properties should never be invoked on it.</span></span>

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

<span data-ttu-id="716c8-197">上述範例會將安全線程的 dotNet `ConcurrentDictionary` 物件傳遞至所有子工作，以收集唯一名稱的處理常式物件。</span><span class="sxs-lookup"><span data-stu-id="716c8-197">The above example passes a thread safe dotNet `ConcurrentDictionary` object to all child jobs to collect uniquely named process objects.</span></span> <span data-ttu-id="716c8-198">由於它是安全線程的物件，因此可以在進程中同時執行工作時安全地使用它。</span><span class="sxs-lookup"><span data-stu-id="716c8-198">Since it is a thread safe object, it can be safely used while the jobs run concurrently in the process.</span></span>

## <a name="see-also"></a><span data-ttu-id="716c8-199">另請參閱</span><span class="sxs-lookup"><span data-stu-id="716c8-199">See also</span></span>

- [<span data-ttu-id="716c8-200">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="716c8-200">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)
- [<span data-ttu-id="716c8-201">about_Thread_Jobs</span><span class="sxs-lookup"><span data-stu-id="716c8-201">about_Thread_Jobs</span></span>](about_Thread_Jobs.md)
- [<span data-ttu-id="716c8-202">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="716c8-202">about_Job_Details</span></span>](about_Job_Details.md)
- [<span data-ttu-id="716c8-203">about_Remote</span><span class="sxs-lookup"><span data-stu-id="716c8-203">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="716c8-204">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="716c8-204">about_PSSessions</span></span>](about_PSSessions.md)
- [<span data-ttu-id="716c8-205">Start-Job</span><span class="sxs-lookup"><span data-stu-id="716c8-205">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="716c8-206">Get-Job</span><span class="sxs-lookup"><span data-stu-id="716c8-206">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="716c8-207">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="716c8-207">Receive-Job</span></span>](xref:Microsoft.PowerShell.Core.Receive-Job)
- [<span data-ttu-id="716c8-208">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="716c8-208">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="716c8-209">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="716c8-209">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="716c8-210">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="716c8-210">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
