---
description: 提供有關 PowerShell 背景工作如何在背景中執行命令或運算式的資訊，而不需與目前的會話互動。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_jobs?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Jobs
ms.openlocfilehash: 51409a124363d21f540459d49eb7e08a7c70d39a
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524853"
---
# <a name="about-jobs"></a><span data-ttu-id="fa3ce-104">關於工作</span><span class="sxs-lookup"><span data-stu-id="fa3ce-104">About Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="fa3ce-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="fa3ce-105">Short description</span></span>
<span data-ttu-id="fa3ce-106">提供有關 PowerShell 背景工作如何在背景中執行命令或運算式的資訊，而不需與目前的會話互動。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-106">Provides information about how PowerShell background jobs run a command or expression in the background without interacting with the current session.</span></span>

## <a name="long-description"></a><span data-ttu-id="fa3ce-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="fa3ce-107">Long description</span></span>

<span data-ttu-id="fa3ce-108">PowerShell 會透過作業同時執行命令和腳本。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-108">PowerShell concurrently runs commands and scripts through jobs.</span></span> <span data-ttu-id="fa3ce-109">PowerShell 提供三種工作類型來支援平行存取。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-109">There are three jobs types provided by PowerShell to support concurrency.</span></span>

- <span data-ttu-id="fa3ce-110">`RemoteJob` -命令和腳本會在遠端會話上執行。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-110">`RemoteJob` - Commands and scripts run on a remote session.</span></span> <span data-ttu-id="fa3ce-111">如需詳細資訊，請參閱 [about_Remote_Jobs](about_Remote_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-111">For information, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>
- <span data-ttu-id="fa3ce-112">`BackgroundJob` -命令和腳本會在本機電腦上的個別進程中執行。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-112">`BackgroundJob` - Commands and scripts run in a separate process on the local machine.</span></span>
- <span data-ttu-id="fa3ce-113">`PSTaskJob` 或 `ThreadJob` -命令和腳本會在本機電腦上相同進程內的個別執行緒中執行。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-113">`PSTaskJob` or `ThreadJob` - Commands and scripts run in a separate thread within the same process on the local machine.</span></span> <span data-ttu-id="fa3ce-114">如需詳細資訊，請參閱 [about_Thread_Jobs](/powershell/module/ThreadJob/about_Thread_Jobs)。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-114">For more information, see [about_Thread_Jobs](/powershell/module/ThreadJob/about_Thread_Jobs).</span></span>

<span data-ttu-id="fa3ce-115">在不同的電腦或個別的進程中遠端執行腳本，可提供絕佳的隔離。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-115">Running scripts remotely, on a separate machine or in a separate process, provides great isolation.</span></span> <span data-ttu-id="fa3ce-116">在遠端作業中發生的任何錯誤，都不會影響到其他執行中的作業或啟動作業的父會話。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-116">Any errors that occur in the remote job do not affect other running jobs or the parent session that started the job.</span></span> <span data-ttu-id="fa3ce-117">不過，遠端層會增加額外負荷，包括物件序列化。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-117">However, the remoting layer adds overhead, including object serialization.</span></span> <span data-ttu-id="fa3ce-118">所有物件都會進行序列化和還原序列化，因為它們會在父會話和遠端 (作業) 會話之間傳遞。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-118">All objects are serialized and deserialized as they are passed between the parent session and the remote (job) session.</span></span> <span data-ttu-id="fa3ce-119">大型複雜資料物件的序列化可能會耗用大量的計算和記憶體資源，並在網路上傳輸大量資料。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-119">Serialization of large complex data objects can consume large amounts of compute and memory resources and transfer large amounts of data across the network.</span></span>

<span data-ttu-id="fa3ce-120">以執行緒為基礎的作業不像遠端和背景工作一樣健全，因為它們在不同執行緒上的相同進程中執行。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-120">Thread-based jobs are not as robust as remote and background jobs, because they run in the same process on different threads.</span></span> <span data-ttu-id="fa3ce-121">如果有一項作業發生嚴重錯誤，導致進程損毀，則會終止進程中的所有其他工作。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-121">If one job has a critical error that crashes the process, then all other jobs in the process are terminated.</span></span>

<span data-ttu-id="fa3ce-122">不過，以執行緒為基礎的作業需要較少的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-122">However, thread-based jobs require less overhead.</span></span> <span data-ttu-id="fa3ce-123">它們不會使用遠端層或序列化。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-123">They don't use the remoting layer or serialization.</span></span> <span data-ttu-id="fa3ce-124">結果物件會傳回做為目前會話中之即時物件的參考。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-124">The result objects are returned as references to live objects in the current session.</span></span> <span data-ttu-id="fa3ce-125">如果沒有此額外負荷，以執行緒為基礎的作業執行速度會更快，且使用的資源比其他作業類型還要少。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-125">Without this overhead, thread-based jobs run faster and use fewer resources than the other job types.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fa3ce-126">建立作業的父會話也會監視作業狀態，並收集管線資料。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-126">The parent session that created the job also monitors the job status and collects pipeline data.</span></span> <span data-ttu-id="fa3ce-127">當工作達到已完成狀態時，父進程會終止作業子進程。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-127">The job child process is terminated by the parent process once the job reaches a finished state.</span></span> <span data-ttu-id="fa3ce-128">如果父會話終止，則所有執行中的子工作都會連同其子進程一起終止。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-128">If the parent session is terminated, all running child jobs are terminated along with their child processes.</span></span>

<span data-ttu-id="fa3ce-129">有兩種方法可以解決這種情況：</span><span class="sxs-lookup"><span data-stu-id="fa3ce-129">There are two ways work around this situation:</span></span>

1. <span data-ttu-id="fa3ce-130">用 `Invoke-Command` 來建立在已中斷連線的會話中執行的作業。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-130">Use `Invoke-Command` to create jobs that run in disconnected sessions.</span></span> <span data-ttu-id="fa3ce-131">如需詳細資訊，請參閱 [about_Remote_Jobs](about_Remote_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-131">For more information, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>
1. <span data-ttu-id="fa3ce-132">用 `Start-Process` 來建立新的處理常式，而不是作業。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-132">Use `Start-Process` to create a new process rather than a job.</span></span> <span data-ttu-id="fa3ce-133">如需詳細資訊，請參閱 [啟動流程](xref:Microsoft.PowerShell.Management.Start-Process)。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-133">For more information, see [Start-Process](xref:Microsoft.PowerShell.Management.Start-Process).</span></span>

## <a name="the-job-cmdlets"></a><span data-ttu-id="fa3ce-134">作業 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="fa3ce-134">The job cmdlets</span></span>

|<span data-ttu-id="fa3ce-135">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="fa3ce-135">Cmdlet</span></span>          |<span data-ttu-id="fa3ce-136">描述</span><span class="sxs-lookup"><span data-stu-id="fa3ce-136">Description</span></span>                                            |
|----------------|-------------------------------------------------------|
|`Start-Job`     |<span data-ttu-id="fa3ce-137">在本機電腦上啟動背景工作。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-137">Starts a background job on a local computer.</span></span>           |
|`Get-Job`       |<span data-ttu-id="fa3ce-138">取得在中啟動的背景工作。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-138">Gets the background jobs that were started in the</span></span>      |
|                |<span data-ttu-id="fa3ce-139">目前的會話。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-139">current session.</span></span>                                       |
|`Receive-Job`   |<span data-ttu-id="fa3ce-140">取得背景工作的結果。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-140">Gets the results of background jobs.</span></span>                   |
|`Stop-Job`      |<span data-ttu-id="fa3ce-141">停止背景工作。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-141">Stops a background job.</span></span>                                |
|`Wait-Job`      |<span data-ttu-id="fa3ce-142">抑制命令提示字元，直到其中一個或所有工作為</span><span class="sxs-lookup"><span data-stu-id="fa3ce-142">Suppresses the command prompt until one or all jobs are</span></span>|
|                |<span data-ttu-id="fa3ce-143">完成。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-143">complete.</span></span>                                              |
|`Remove-Job`    |<span data-ttu-id="fa3ce-144">移除背景工作。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-144">Deletes a background job.</span></span>                              |
|`Invoke-Command`|<span data-ttu-id="fa3ce-145">**AsJob** 參數會在上建立背景工作</span><span class="sxs-lookup"><span data-stu-id="fa3ce-145">The **AsJob** parameter creates a background job on a</span></span>  |
|                |<span data-ttu-id="fa3ce-146">遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-146">remote computer.</span></span> <span data-ttu-id="fa3ce-147">您可以使用 `Invoke-Command` 執行</span><span class="sxs-lookup"><span data-stu-id="fa3ce-147">You can use `Invoke-Command` to run</span></span>   |
|                |<span data-ttu-id="fa3ce-148">遠端的任何工作命令，包括 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-148">any job command remotely, including `Start-Job`.</span></span>       |

## <a name="how-to-start-a-job-on-the-local-computer"></a><span data-ttu-id="fa3ce-149">如何在本機電腦上啟動作業</span><span class="sxs-lookup"><span data-stu-id="fa3ce-149">How to start a job on the local computer</span></span>

<span data-ttu-id="fa3ce-150">若要在本機電腦上啟動背景工作，請使用 `Start-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-150">To start a background job on the local computer, use the `Start-Job` cmdlet.</span></span>

<span data-ttu-id="fa3ce-151">若要撰寫 `Start-Job` 命令，請以大括弧括住工作執行的命令 (`{}`) 。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-151">To write a `Start-Job` command, enclose the command that the job runs in curly braces (`{}`).</span></span> <span data-ttu-id="fa3ce-152">使用 **ScriptBlock** 參數來指定命令。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-152">Use the **ScriptBlock** parameter to specify the command.</span></span>

<span data-ttu-id="fa3ce-153">下列命令會啟動在 `Get-Process` 本機電腦上執行命令的背景工作。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-153">The following command starts a background job that runs a `Get-Process` command on the local computer.</span></span>

```powershell
Start-Job -ScriptBlock {Get-Process}
```

<span data-ttu-id="fa3ce-154">當您啟動背景工作時，命令提示字元會立即傳回，即使作業需要較長的時間才能完成。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-154">When you start a background job, the command prompt returns immediately, even if the job takes an extended time to complete.</span></span> <span data-ttu-id="fa3ce-155">工作執行時，您可以在工作階段中繼續工作，而不需中斷。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-155">You can continue to work in the session without interruption while the job runs.</span></span>

<span data-ttu-id="fa3ce-156">此 `Start-Job` 命令會傳回代表作業的物件。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-156">The `Start-Job` command returns an object that represents the job.</span></span> <span data-ttu-id="fa3ce-157">工作物件包含工作的相關實用資訊，但是不包含工作結果。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-157">The job object contains useful information about the job, but it does not contain the job results.</span></span>

<span data-ttu-id="fa3ce-158">您可以將工作物件儲存在變數中，然後將它與其他 **工作** Cmdlet 搭配使用，以管理背景工作。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-158">You can save the job object in a variable and then use it with the other **Job** cmdlets to manage the background job.</span></span> <span data-ttu-id="fa3ce-159">下列命令會啟動工作物件，並將產生的工作物件儲存在 `$job` 變數中。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-159">The following command starts a job object and saves the resulting job object in the `$job` variable.</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
```

<span data-ttu-id="fa3ce-160">從 PowerShell 6.0 開始，您可以使用 `&` 管線結尾 () 背景運算子來啟動背景工作。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-160">Beginning in PowerShell 6.0, you can use the background operator (`&`) at the end of a pipeline to start a background job.</span></span> <span data-ttu-id="fa3ce-161">如需詳細資訊，請參閱 [背景運算子](about_Operators.md#background-operator-)。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-161">For more information, see [background operator](about_Operators.md#background-operator-).</span></span>

<span data-ttu-id="fa3ce-162">使用 background 運算子的功能相當於使用 `Start-Job` 上述範例中的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-162">Using the background operator is functionally equivalent to using the `Start-Job` cmdlet in the previous example.</span></span>

```powershell
$job = Get-Process &
```

## <a name="getting-job-objects"></a><span data-ttu-id="fa3ce-163">取得工作物件</span><span class="sxs-lookup"><span data-stu-id="fa3ce-163">Getting job objects</span></span>

<span data-ttu-id="fa3ce-164">指令 `Get-Job` 程式會傳回物件，代表在目前會話中啟動的背景工作。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-164">The `Get-Job` cmdlet returns objects that represent the background jobs that were started in the current session.</span></span> <span data-ttu-id="fa3ce-165">如果沒有參數，則會傳回 `Get-Job` 在目前會話中啟動的所有工作。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-165">Without parameters, `Get-Job` returns all of the jobs that were started in the current session.</span></span>

```powershell
Get-Job
```

<span data-ttu-id="fa3ce-166">工作物件包含工作的狀態，指出作業是否已完成。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-166">The job object contains the state of the job, which indicates whether the job has finished.</span></span> <span data-ttu-id="fa3ce-167">完成的作業狀態為 [已 **完成** ] 或 [ **失敗** ]。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-167">A finished job has a state of **Complete** or **Failed**.</span></span> <span data-ttu-id="fa3ce-168">作業也可能 **遭到封鎖** 或 **正在** 執行。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-168">A job might also be **Blocked** or **Running**.</span></span>

```Output
Id  Name  PSJobTypeName State      HasMoreData  Location   Command
--  ----  ------------- -----      -----------  --------   -------
1   Job1  BackgroundJob Complete   True         localhost  Get-Process
```

<span data-ttu-id="fa3ce-169">您可以將工作物件儲存在變數中，並在稍後的命令中使用它來表示作業。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-169">You can save the job object in a variable and use it to represent the job in a later command.</span></span> <span data-ttu-id="fa3ce-170">下列命令會取得識別碼為1的作業，並將它儲存在 `$job` 變數中。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-170">The following command gets the job with ID 1 and saves it in the `$job` variable.</span></span>

```powershell
$job = Get-Job -Id 1
```

## <a name="getting-the-results-of-a-job"></a><span data-ttu-id="fa3ce-171">取得作業的結果</span><span class="sxs-lookup"><span data-stu-id="fa3ce-171">Getting the results of a job</span></span>

<span data-ttu-id="fa3ce-172">當您執行背景工作時，結果不會立即出現。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-172">When you run a background job, the results do not appear immediately.</span></span> <span data-ttu-id="fa3ce-173">若要取得背景工作的結果，請使用 `Receive-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-173">To get the results of a background job, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="fa3ce-174">下列範例會 `Receive-Job` 使用變數中的工作物件，來取得工作的結果 `$job` 。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-174">The following example, the `Receive-Job` cmdlet gets the results of the job using job object in the `$job` variable.</span></span>

```powershell
Receive-Job -Job $job
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------    -----      ----- -----   ------    -- -----------
    103       4    11328       9692    56           1176 audiodg
    804      14    12228      14108   100   101.74  1740 CcmExec
    668       7     2672       6168   104    32.26   488 csrss
...
```

<span data-ttu-id="fa3ce-175">您可以將工作的結果儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-175">You can save the results of a job in a variable.</span></span> <span data-ttu-id="fa3ce-176">下列命令會將工作的結果儲存在變數中 `$job` `$results` 。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-176">The following command saves the results of the job in the `$job` variable to the `$results` variable.</span></span>

```powershell
$results = Receive-Job -Job $job
```

### <a name="getting-and-keeping-partial-job-results"></a><span data-ttu-id="fa3ce-177">取得和保留部分工作結果</span><span class="sxs-lookup"><span data-stu-id="fa3ce-177">Getting and keeping partial job results</span></span>

<span data-ttu-id="fa3ce-178">`Receive-Job`Cmdlet 會取得背景工作的結果。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-178">The `Receive-Job` cmdlet gets the results of a background job.</span></span> <span data-ttu-id="fa3ce-179">如果作業已完成，則會 `Receive-Job` 取得所有工作結果。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-179">If the job is complete, `Receive-Job` gets all job results.</span></span> <span data-ttu-id="fa3ce-180">如果作業仍在執行中， `Receive-Job` 則會取得到目前為止產生的結果。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-180">If the job is still running, `Receive-Job` gets the results that have been generated thus far.</span></span> <span data-ttu-id="fa3ce-181">您可以 `Receive-Job` 再次執行命令以取得剩餘的結果。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-181">You can run `Receive-Job` commands again to get the remaining results.</span></span>

<span data-ttu-id="fa3ce-182">根據預設， `Receive-Job` 會從儲存工作結果的快取中刪除結果。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-182">By default, `Receive-Job` deletes the results from the cache where job results are stored.</span></span> <span data-ttu-id="fa3ce-183">當您再次執行時 `Receive-Job` ，只會取得第一次執行後抵達的新結果。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-183">When you run `Receive-Job` again, you get only the new results that arrived after the first run.</span></span>

<span data-ttu-id="fa3ce-184">下列命令 `Receive-Job` 會顯示作業完成之前執行的命令結果。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-184">The following commands show the results of `Receive-Job` commands run before the job is complete.</span></span>

```powershell
C:\PS> Receive-Job -Job $job

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec

C:\PS> Receive-Job -Job $job

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    68       3     2632        664    29     0.36   1388 ccmsetup
   749      22    21468      19940   203   122.13   3644 communicator
   905       7     2980       2628    34   197.97    424 csrss
  1121      25    28408      32940   174   430.14   3048 explorer
```

<span data-ttu-id="fa3ce-185">使用 **Keep** 參數以防止 `Receive-Job` 刪除傳回的工作結果。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-185">Use the **Keep** parameter to prevent `Receive-Job` from deleting the job results that are returned.</span></span> <span data-ttu-id="fa3ce-186">下列命令顯示在尚未完成的作業上使用 **Keep** 參數的效果。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-186">The following commands show the effect of using the **Keep** parameter on a job that is not yet complete.</span></span>

```powershell
C:\PS> Receive-Job -Job $job -Keep

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec

C:\PS> Receive-Job -Job $job -Keep

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec
     68       3     2632        664    29     0.36   1388 ccmsetup
    749      22    21468      19940   203   122.13   3644 communicator
    905       7     2980       2628    34   197.97    424 csrss
   1121      25    28408      32940   174   430.14   3048 explorer
```

### <a name="waiting-for-the-results"></a><span data-ttu-id="fa3ce-187">等候結果</span><span class="sxs-lookup"><span data-stu-id="fa3ce-187">Waiting for the results</span></span>

<span data-ttu-id="fa3ce-188">如果您執行需要很長時間才能完成的命令，您可以使用工作物件的屬性來判斷作業何時完成。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-188">If you run a command that takes a long time to complete, you can use the properties of the job object to determine when the job is complete.</span></span> <span data-ttu-id="fa3ce-189">下列命令會使用 `Get-Job` 物件取得目前會話中的所有背景工作。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-189">The following command uses the `Get-Job` object to get all of the background jobs in the current session.</span></span>

```powershell
Get-Job
```

<span data-ttu-id="fa3ce-190">結果會出現在資料表中。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-190">The results appear in a table.</span></span> <span data-ttu-id="fa3ce-191">作業狀態會顯示在 [ **狀態** ] 資料行中。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-191">The status of the job appears in the **State** column.</span></span>

```Output
Id Name  PSJobTypeName State    HasMoreData Location  Command
-- ----  ------------- -----    ----------- --------  -------
1  Job1  BackgroundJob Complete True        localhost Get-Process
2  Job2  BackgroundJob Running  True        localhost Get-EventLog -Log ...
3  Job3  BackgroundJob Complete True        localhost dir -Path C:\* -Re...
```

<span data-ttu-id="fa3ce-192">在此情況下， **State** 屬性會顯示作業2仍在執行。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-192">In this case, the **State** property reveals that Job 2 is still running.</span></span> <span data-ttu-id="fa3ce-193">如果您現在要使用 `Receive-Job` Cmdlet 來取得工作結果，結果會是不完整的。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-193">If you were to use the `Receive-Job` cmdlet to get the job results now, the results would be incomplete.</span></span> <span data-ttu-id="fa3ce-194">您可以重複使用此 `Receive-Job` Cmdlet 來取得所有結果。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-194">You can use the `Receive-Job` cmdlet repeatedly to get all of the results.</span></span> <span data-ttu-id="fa3ce-195">使用 **State** 屬性來判斷作業何時完成。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-195">Use the **State** property to determine when the job is complete.</span></span>

<span data-ttu-id="fa3ce-196">您也可以使用 Cmdlet 的 **Wait** 參數 `Receive-Job` 。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-196">You can also use the **Wait** parameter of the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="fa3ce-197">使用此參數時，此 Cmdlet 不會傳回命令提示字元，直到工作完成且所有結果都可用為止。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-197">When use use this parameter, the cmdlet does not return the command prompt until the job is completed and all results are available.</span></span>

<span data-ttu-id="fa3ce-198">您也可以使用 `Wait-Job` Cmdlet 來等候工作的任何或所有結果。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-198">You can also use the `Wait-Job` cmdlet to wait for any or all of the results of the job.</span></span> <span data-ttu-id="fa3ce-199">`Wait-Job` 讓您等候一或多個特定工作或所有作業。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-199">`Wait-Job` lets you wait for one or more specific job or for all jobs.</span></span>
<span data-ttu-id="fa3ce-200">下列命令會使用 `Wait-Job` Cmdlet 來等候 **識別碼** 為</span><span class="sxs-lookup"><span data-stu-id="fa3ce-200">The following command uses the `Wait-Job` cmdlet to wait for a job with **ID**</span></span>
10.

```powershell
Wait-Job -ID 10
```

<span data-ttu-id="fa3ce-201">因此，在作業完成之前，會抑制 PowerShell 提示字元。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-201">As a result, the PowerShell prompt is suppressed until the job is completed.</span></span>

<span data-ttu-id="fa3ce-202">您也可以等候預定的一段時間。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-202">You can also wait for a predetermined period of time.</span></span> <span data-ttu-id="fa3ce-203">此命令會使用 **Timeout** 參數將等待時間限制為120秒。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-203">This command uses the **Timeout** parameter to limit the wait to 120 seconds.</span></span> <span data-ttu-id="fa3ce-204">當時間過期時，命令提示字元會傳回，但是工作會繼續在背景執行。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-204">When the time expires, the command prompt returns, but the job continues to run in the background.</span></span>

```powershell
Wait-Job -ID 10 -Timeout 120
```

## <a name="stopping-a-job"></a><span data-ttu-id="fa3ce-205">停止作業</span><span class="sxs-lookup"><span data-stu-id="fa3ce-205">Stopping a job</span></span>

<span data-ttu-id="fa3ce-206">若要停止背景工作，請使用 `Stop-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-206">To stop a background job, use the `Stop-Job` cmdlet.</span></span> <span data-ttu-id="fa3ce-207">下列命令會啟動作業，以取得系統事件記錄檔中的每個專案。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-207">The following command starts a job to get every entry in the System event log.</span></span> <span data-ttu-id="fa3ce-208">它會將工作物件儲存在 `$job` 變數中。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-208">It saves the job object in the `$job` variable.</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-EventLog -Log System}
```

<span data-ttu-id="fa3ce-209">下列命令會停止作業。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-209">The following command stops the job.</span></span> <span data-ttu-id="fa3ce-210">它使用管線運算子 (`|`) 將變數中的工作傳送 `$job` 至 `Stop-Job` 。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-210">It uses a pipeline operator (`|`) to send the job in the `$job` variable to `Stop-Job`.</span></span>

```powershell
$job | Stop-Job
```

## <a name="deleting-a-job"></a><span data-ttu-id="fa3ce-211">刪除作業</span><span class="sxs-lookup"><span data-stu-id="fa3ce-211">Deleting a job</span></span>

<span data-ttu-id="fa3ce-212">若要移除背景工作，請使用 `Remove-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-212">To delete a background job, use the `Remove-Job` cmdlet.</span></span> <span data-ttu-id="fa3ce-213">下列命令會刪除變數中的工作 `$job` 。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-213">The following command deletes the job in the `$job` variable.</span></span>

```powershell
Remove-Job -Job $job
```

## <a name="investigating-a-failed-job"></a><span data-ttu-id="fa3ce-214">調查失敗的作業</span><span class="sxs-lookup"><span data-stu-id="fa3ce-214">Investigating a failed job</span></span>

<span data-ttu-id="fa3ce-215">作業可能會因為許多原因而失敗。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-215">Jobs can fail for many reasons.</span></span> <span data-ttu-id="fa3ce-216">工作物件包含 **Reason** 屬性，其中包含失敗原因的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-216">the job object contains a **Reason** property that contains information about the cause of the failure.</span></span>

<span data-ttu-id="fa3ce-217">下列範例會在沒有所需認證的情況下啟動作業。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-217">The following example starts a job without the required credentials.</span></span>

```powershell
$job = Start-Job -ScriptBlock {New-Item -Path HKLM:\Software\MyCompany}
Get-Job $job

Id Name  PSJobTypeName State  HasMoreData  Location  Command
-- ----  ------------- -----  -----------  --------  -------
1  Job1  BackgroundJob Failed False        localhost New-Item -Path HKLM:...
```

<span data-ttu-id="fa3ce-218">檢查 **Reason** 屬性以找出造成作業失敗的錯誤。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-218">Inspect the **Reason** property to find the error that caused the job to fail.</span></span>

```powershell
$job.ChildJobs[0].JobStateInfo.Reason
```

<span data-ttu-id="fa3ce-219">在此情況下，作業失敗，因為遠端電腦需要明確的認證才能執行此命令。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-219">In this case, the job failed because the remote computer required explicit credentials to run the command.</span></span> <span data-ttu-id="fa3ce-220">**Reason** 屬性包含下列訊息：</span><span class="sxs-lookup"><span data-stu-id="fa3ce-220">The **Reason** property contains the following message:</span></span>

> <span data-ttu-id="fa3ce-221">連線到遠端伺服器失敗，出現下列錯誤訊息：「拒絕存取」。</span><span class="sxs-lookup"><span data-stu-id="fa3ce-221">Connecting to remote server failed with the following error message: "Access is denied".</span></span>

## <a name="see-also"></a><span data-ttu-id="fa3ce-222">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa3ce-222">See also</span></span>

- [<span data-ttu-id="fa3ce-223">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="fa3ce-223">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)
- [<span data-ttu-id="fa3ce-224">about_Thread_Jobs</span><span class="sxs-lookup"><span data-stu-id="fa3ce-224">about_Thread_Jobs</span></span>](about_Thread_Jobs.md)
- [<span data-ttu-id="fa3ce-225">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="fa3ce-225">about_Job_Details</span></span>](about_Job_Details.md)
- [<span data-ttu-id="fa3ce-226">about_Remote</span><span class="sxs-lookup"><span data-stu-id="fa3ce-226">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="fa3ce-227">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="fa3ce-227">about_PSSessions</span></span>](about_PSSessions.md)
- [<span data-ttu-id="fa3ce-228">Start-Job</span><span class="sxs-lookup"><span data-stu-id="fa3ce-228">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="fa3ce-229">Get-Job</span><span class="sxs-lookup"><span data-stu-id="fa3ce-229">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="fa3ce-230">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="fa3ce-230">Receive-Job</span></span>](xref:Microsoft.PowerShell.Core.Receive-Job)
- [<span data-ttu-id="fa3ce-231">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="fa3ce-231">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="fa3ce-232">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="fa3ce-232">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="fa3ce-233">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="fa3ce-233">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
- [<span data-ttu-id="fa3ce-234">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="fa3ce-234">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)
