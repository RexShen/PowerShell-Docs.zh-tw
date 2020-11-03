---
description: 提供有關 PowerShell 背景工作如何在背景中執行命令或運算式的資訊，而不需與目前的會話互動。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_jobs?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Jobs
ms.openlocfilehash: 6668e8a060c2468a4c7d98f52c7d493e1751970b
ms.sourcegitcommit: 108686b166672cc08817c637dd93eb1ad830511d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "93208572"
---
# <a name="about-jobs"></a><span data-ttu-id="d93b9-104">關於工作</span><span class="sxs-lookup"><span data-stu-id="d93b9-104">About Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="d93b9-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="d93b9-105">Short description</span></span>
<span data-ttu-id="d93b9-106">提供有關 PowerShell 背景工作如何在背景中執行命令或運算式的資訊，而不需與目前的會話互動。</span><span class="sxs-lookup"><span data-stu-id="d93b9-106">Provides information about how PowerShell background jobs run a command or expression in the background without interacting with the current session.</span></span>

## <a name="long-description"></a><span data-ttu-id="d93b9-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="d93b9-107">Long description</span></span>

<span data-ttu-id="d93b9-108">PowerShell 會透過作業同時執行命令和腳本。</span><span class="sxs-lookup"><span data-stu-id="d93b9-108">PowerShell concurrently runs commands and script through jobs.</span></span> <span data-ttu-id="d93b9-109">PowerShell 提供三個以工作為基礎的解決方案，以支援平行存取。</span><span class="sxs-lookup"><span data-stu-id="d93b9-109">There are three jobs-based solutions provided by PowerShell to support concurrency.</span></span>

|<span data-ttu-id="d93b9-110">工作 (Job)</span><span class="sxs-lookup"><span data-stu-id="d93b9-110">Job</span></span>            |<span data-ttu-id="d93b9-111">Description</span><span class="sxs-lookup"><span data-stu-id="d93b9-111">Description</span></span>                                                  |
|---------------|-------------------------------------------------------------|
|`RemoteJob`    |<span data-ttu-id="d93b9-112">命令和腳本會在遠端電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="d93b9-112">Command and script run on a remote computer.</span></span>                 |
|`BackgroundJob`|<span data-ttu-id="d93b9-113">命令和腳本在本機的個別進程中執行</span><span class="sxs-lookup"><span data-stu-id="d93b9-113">Command and script run in a separate process on the local</span></span>    |
|               |<span data-ttu-id="d93b9-114">新的虛擬主機。</span><span class="sxs-lookup"><span data-stu-id="d93b9-114">machine.</span></span>                                                     |
|`ThreadJob`    |<span data-ttu-id="d93b9-115">命令和腳本在相同的執行緒中執行</span><span class="sxs-lookup"><span data-stu-id="d93b9-115">Command and script run in a separate thread within the same</span></span>  |
|               |<span data-ttu-id="d93b9-116">在本機電腦上處理。</span><span class="sxs-lookup"><span data-stu-id="d93b9-116">process on the local machine.</span></span>                                |

<span data-ttu-id="d93b9-117">每種類型的作業都有其優點和缺點。</span><span class="sxs-lookup"><span data-stu-id="d93b9-117">Each type of job has benefits and drawbacks.</span></span> <span data-ttu-id="d93b9-118">在不同的電腦上或在個別的進程中遠端執行腳本有很大的隔離。</span><span class="sxs-lookup"><span data-stu-id="d93b9-118">Running script remotely on a separate machine or in a separate process has great isolation.</span></span> <span data-ttu-id="d93b9-119">任何錯誤都不會影響其他執行中的工作或啟動作業的用戶端。</span><span class="sxs-lookup"><span data-stu-id="d93b9-119">Any errors won't affect other running jobs or the client that started the job.</span></span> <span data-ttu-id="d93b9-120">但是遠端層會增加額外負荷，包括物件序列化。</span><span class="sxs-lookup"><span data-stu-id="d93b9-120">But the remoting layer adds overhead, including object serialization.</span></span> <span data-ttu-id="d93b9-121">在遠端會話中傳遞的所有物件都必須序列化，然後在用戶端與目標會話之間傳遞時還原序列化。</span><span class="sxs-lookup"><span data-stu-id="d93b9-121">All objects passed to and from the remote session must be serialized and then deserialized as it passes between the client and the target session.</span></span> <span data-ttu-id="d93b9-122">序列化作業可以針對大型複雜資料物件使用許多計算和記憶體資源。</span><span class="sxs-lookup"><span data-stu-id="d93b9-122">The serialization operation can use many compute and memory resources for large complex data objects.</span></span>

<span data-ttu-id="d93b9-123">本主題說明如何在本機電腦上的 PowerShell 中執行背景工作。</span><span class="sxs-lookup"><span data-stu-id="d93b9-123">This topic explains how to run background jobs in PowerShell on a local computer.</span></span> <span data-ttu-id="d93b9-124">如需在遠端電腦上執行背景工作的詳細資訊，請參閱 [about_Remote_Jobs](about_Remote_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="d93b9-124">For information about running background jobs on remote computers, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span> <span data-ttu-id="d93b9-125">如需執行緒作業的詳細資訊，請參閱 [about_Thread_Jobs](about_Thread_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="d93b9-125">For more information about thread jobs, see [about_Thread_Jobs](about_Thread_Jobs.md).</span></span>

<span data-ttu-id="d93b9-126">當您啟動背景工作時，命令提示字元會立即傳回，即使作業需要較長的時間才能完成。</span><span class="sxs-lookup"><span data-stu-id="d93b9-126">When you start a background job, the command prompt returns immediately, even if the job takes an extended time to complete.</span></span> <span data-ttu-id="d93b9-127">工作執行時，您可以在工作階段中繼續工作，而不需中斷。</span><span class="sxs-lookup"><span data-stu-id="d93b9-127">You can continue to work in the session without interruption while the job runs.</span></span>

## <a name="the-job-cmdlets"></a><span data-ttu-id="d93b9-128">作業 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d93b9-128">The job cmdlets</span></span>

|<span data-ttu-id="d93b9-129">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d93b9-129">Cmdlet</span></span>          |<span data-ttu-id="d93b9-130">描述</span><span class="sxs-lookup"><span data-stu-id="d93b9-130">Description</span></span>                                            |
|----------------|-------------------------------------------------------|
|`Start-Job`     |<span data-ttu-id="d93b9-131">在本機電腦上啟動背景工作。</span><span class="sxs-lookup"><span data-stu-id="d93b9-131">Starts a background job on a local computer.</span></span>           |
|`Get-Job`       |<span data-ttu-id="d93b9-132">取得在中啟動的背景工作。</span><span class="sxs-lookup"><span data-stu-id="d93b9-132">Gets the background jobs that were started in the</span></span>      |
|                |<span data-ttu-id="d93b9-133">目前的會話。</span><span class="sxs-lookup"><span data-stu-id="d93b9-133">current session.</span></span>                                       |
|`Receive-Job`   |<span data-ttu-id="d93b9-134">取得背景工作的結果。</span><span class="sxs-lookup"><span data-stu-id="d93b9-134">Gets the results of background jobs.</span></span>                   |
|`Stop-Job`      |<span data-ttu-id="d93b9-135">停止背景工作。</span><span class="sxs-lookup"><span data-stu-id="d93b9-135">Stops a background job.</span></span>                                |
|`Wait-Job`      |<span data-ttu-id="d93b9-136">抑制命令提示字元，直到其中一個或所有工作為</span><span class="sxs-lookup"><span data-stu-id="d93b9-136">Suppresses the command prompt until one or all jobs are</span></span>|
|                |<span data-ttu-id="d93b9-137">完成。</span><span class="sxs-lookup"><span data-stu-id="d93b9-137">complete.</span></span>                                              |
|`Remove-Job`    |<span data-ttu-id="d93b9-138">移除背景工作。</span><span class="sxs-lookup"><span data-stu-id="d93b9-138">Deletes a background job.</span></span>                              |
|`Invoke-Command`|<span data-ttu-id="d93b9-139">**AsJob** 參數會在上建立背景工作</span><span class="sxs-lookup"><span data-stu-id="d93b9-139">The **AsJob** parameter creates a background job on a</span></span>  |
|                |<span data-ttu-id="d93b9-140">遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="d93b9-140">remote computer.</span></span> <span data-ttu-id="d93b9-141">您可以使用 `Invoke-Command` 執行</span><span class="sxs-lookup"><span data-stu-id="d93b9-141">You can use `Invoke-Command` to run</span></span>   |
|                |<span data-ttu-id="d93b9-142">遠端的任何工作命令，包括 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="d93b9-142">any job command remotely, including `Start-Job`.</span></span>       |

## <a name="how-to-start-a-job-on-the-local-computer"></a><span data-ttu-id="d93b9-143">如何在本機電腦上啟動作業</span><span class="sxs-lookup"><span data-stu-id="d93b9-143">How to start a job on the local computer</span></span>

<span data-ttu-id="d93b9-144">若要在本機電腦上啟動背景工作，請使用 `Start-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d93b9-144">To start a background job on the local computer, use the `Start-Job` cmdlet.</span></span>

<span data-ttu-id="d93b9-145">若要撰寫 `Start-Job` 命令，請以大括弧括住工作執行的命令 (`{}`) 。</span><span class="sxs-lookup"><span data-stu-id="d93b9-145">To write a `Start-Job` command, enclose the command that the job runs in curly braces (`{}`).</span></span> <span data-ttu-id="d93b9-146">使用 **ScriptBlock** 參數來指定命令。</span><span class="sxs-lookup"><span data-stu-id="d93b9-146">Use the **ScriptBlock** parameter to specify the command.</span></span>

<span data-ttu-id="d93b9-147">下列命令會啟動在 `Get-Process` 本機電腦上執行命令的背景工作。</span><span class="sxs-lookup"><span data-stu-id="d93b9-147">The following command starts a background job that runs a `Get-Process` command on the local computer.</span></span>

```powershell
Start-Job -ScriptBlock {Get-Process}
```

<span data-ttu-id="d93b9-148">此 `Start-Job` 命令會傳回代表作業的物件。</span><span class="sxs-lookup"><span data-stu-id="d93b9-148">The `Start-Job` command returns an object that represents the job.</span></span> <span data-ttu-id="d93b9-149">工作物件包含工作的相關實用資訊，但是不包含工作結果。</span><span class="sxs-lookup"><span data-stu-id="d93b9-149">The job object contains useful information about the job, but it does not contain the job results.</span></span>

<span data-ttu-id="d93b9-150">將工作物件儲存在變數中，然後使用其他工作 Cmdlet 來管理背景工作。</span><span class="sxs-lookup"><span data-stu-id="d93b9-150">Save the job object in a variable, and then use it with the other Job cmdlets to manage the background job.</span></span> <span data-ttu-id="d93b9-151">下列命令會啟動工作物件，並將產生的工作物件儲存在 `$job` 變數中。</span><span class="sxs-lookup"><span data-stu-id="d93b9-151">The following command starts a job object and saves the resulting job object in the `$job` variable.</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
```

<span data-ttu-id="d93b9-152">從 PowerShell 6.0 開始，您可以 `&` 在管線結尾使用 amersand () ，以啟動背景工作。</span><span class="sxs-lookup"><span data-stu-id="d93b9-152">Beginning in PowerShell 6.0, you can use an amersand (`&`) at the end of a pipeline to start a background job.</span></span> <span data-ttu-id="d93b9-153">下列命令在功能上等同于上述命令。</span><span class="sxs-lookup"><span data-stu-id="d93b9-153">The following command is functionally equivalent to the command above.</span></span>

```powershell
$job = Get-Process &
```

<span data-ttu-id="d93b9-154"> () 的 & 符號 `&` 稱為背景運算子。</span><span class="sxs-lookup"><span data-stu-id="d93b9-154">The ampersand (`&`) is called the background operator.</span></span> <span data-ttu-id="d93b9-155">如需詳細資訊，請參閱 [背景運算子](about_Operators.md#background-operator-)。</span><span class="sxs-lookup"><span data-stu-id="d93b9-155">For more information, see [background operator](about_Operators.md#background-operator-).</span></span>

<span data-ttu-id="d93b9-156">您也可以使用 `Get-Job` Cmdlet 來取得物件，這些物件代表在目前會話中啟動的工作。</span><span class="sxs-lookup"><span data-stu-id="d93b9-156">You can also use the `Get-Job` cmdlet to get objects that represent the jobs started in the current session.</span></span> <span data-ttu-id="d93b9-157">`Get-Job` 傳回傳回的相同工作物件 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="d93b9-157">`Get-Job` returns the same job object that `Start-Job` returns.</span></span>

## <a name="getting-job-objects"></a><span data-ttu-id="d93b9-158">取得工作物件</span><span class="sxs-lookup"><span data-stu-id="d93b9-158">Getting job objects</span></span>

<span data-ttu-id="d93b9-159">若要取得物件，以代表目前會話中啟動的背景工作，請使用 `Get-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d93b9-159">To get object that represent the background jobs that were started in the current session, use the `Get-Job` cmdlet.</span></span> <span data-ttu-id="d93b9-160">如果沒有參數，則會傳回 `Get-Job` 在目前會話中啟動的所有工作。</span><span class="sxs-lookup"><span data-stu-id="d93b9-160">Without parameters, `Get-Job` returns all of the jobs that were started in the current session.</span></span>

<span data-ttu-id="d93b9-161">例如，下列命令會取得目前會話中的工作。</span><span class="sxs-lookup"><span data-stu-id="d93b9-161">For example, the following command gets the jobs in the current session.</span></span>

```powershell
PS C:> Get-Job

Id  Name  PSJobTypeName State      HasMoreData  Location   Command
--  ----  ------------- -----      -----------  --------   -------
1   Job1  BackgroundJob Running    True         localhost  Get-Process
```

<span data-ttu-id="d93b9-162">您也可以將工作物件儲存在變數中，並在稍後的命令中使用它來表示作業。</span><span class="sxs-lookup"><span data-stu-id="d93b9-162">You can also save the job object in a variable and use it to represent the job in a later command.</span></span> <span data-ttu-id="d93b9-163">下列命令會取得識別碼為1的作業，並將它儲存在 `$job` 變數中。</span><span class="sxs-lookup"><span data-stu-id="d93b9-163">The following command gets the job with ID 1 and saves it in the `$job` variable.</span></span>

```powershell
$job = Get-Job -Id 1
```

<span data-ttu-id="d93b9-164">工作物件包含工作的狀態，指出作業是否已完成。</span><span class="sxs-lookup"><span data-stu-id="d93b9-164">The job object contains the state of the job, which indicates whether the job has finished.</span></span> <span data-ttu-id="d93b9-165">完成的作業狀態為 [已 **完成** ] 或 [ **失敗** ]。</span><span class="sxs-lookup"><span data-stu-id="d93b9-165">A finished job has a state of **Complete** or **Failed** .</span></span> <span data-ttu-id="d93b9-166">作業也可能 **遭到封鎖** 或 **正在** 執行。</span><span class="sxs-lookup"><span data-stu-id="d93b9-166">A job might also be **blocked** or **running** .</span></span>

```powershell
Get-Job

Id  Name  PSJobTypeName State      HasMoreData  Location   Command
--  ----  ------------- -----      -----------  --------   -------
1   Job1  BackgroundJob Complete   True         localhost  Get-Process
```

## <a name="getting-the-results-of-a-job"></a><span data-ttu-id="d93b9-167">取得作業的結果</span><span class="sxs-lookup"><span data-stu-id="d93b9-167">Getting the results of a job</span></span>

<span data-ttu-id="d93b9-168">當您執行背景工作時，結果不會立即出現。</span><span class="sxs-lookup"><span data-stu-id="d93b9-168">When you run a background job, the results do not appear immediately.</span></span> <span data-ttu-id="d93b9-169">相反地，此 `Start-Job` Cmdlet 會傳回代表工作的工作物件，但不包含結果。</span><span class="sxs-lookup"><span data-stu-id="d93b9-169">Instead, the `Start-Job` cmdlet returns a job object that represents the job, but it does not contain the results.</span></span> <span data-ttu-id="d93b9-170">若要取得背景工作的結果，請使用 `Receive-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d93b9-170">To get the results of a background job, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="d93b9-171">下列命令會使用 `Receive-Job` Cmdlet 來取得工作的結果。</span><span class="sxs-lookup"><span data-stu-id="d93b9-171">The following command uses the `Receive-Job` cmdlet to get the results of the job.</span></span> <span data-ttu-id="d93b9-172">它會使用儲存在變數中的工作物件 `$job` 來識別作業。</span><span class="sxs-lookup"><span data-stu-id="d93b9-172">It uses a job object saved in the `$job` variable to identify the job.</span></span>

```powershell
Receive-Job -Job $job
```

<span data-ttu-id="d93b9-173">Cmdlet 會傳回 `Receive-Job` 作業的結果。</span><span class="sxs-lookup"><span data-stu-id="d93b9-173">The `Receive-Job` cmdlet returns the results of the job.</span></span>

```
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------    -----      ----- -----   ------    -- -----------
    103       4    11328       9692    56           1176 audiodg
    804      14    12228      14108   100   101.74  1740 CcmExec
    668       7     2672       6168   104    32.26   488 csrss
# ...
```

<span data-ttu-id="d93b9-174">您也可以將工作的結果儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="d93b9-174">You can also save the results of a job in a variable.</span></span> <span data-ttu-id="d93b9-175">下列命令會將工作的結果儲存在變數中 `$job` `$results` 。</span><span class="sxs-lookup"><span data-stu-id="d93b9-175">The following command saves the results of the job in the `$job` variable to the `$results` variable.</span></span>

```powershell
$results = Receive-Job -Job $job
```

<span data-ttu-id="d93b9-176">而且，您可以使用重新導向運算子 () 或 Cmdlet，將作業的結果儲存在檔案中 `>` `Out-File` 。</span><span class="sxs-lookup"><span data-stu-id="d93b9-176">And, you can save the results of the job in a file by using the redirection operator (`>`) or the `Out-File` cmdlet.</span></span> <span data-ttu-id="d93b9-177">下列命令會使用重新導向運算子，將作業的結果儲存在檔案中的 `$job` 變數中 `Results.txt` 。</span><span class="sxs-lookup"><span data-stu-id="d93b9-177">The following command uses the redirection operator to save the results of the job in the `$job` variable in the `Results.txt` file.</span></span>

```powershell
Receive-Job -Job $job > results.txt
```

## <a name="getting-and-keeping-partial-job-results"></a><span data-ttu-id="d93b9-178">取得和保留部分工作結果</span><span class="sxs-lookup"><span data-stu-id="d93b9-178">Getting and keeping partial job results</span></span>

<span data-ttu-id="d93b9-179">`Receive-Job`Cmdlet 會取得背景工作的結果。</span><span class="sxs-lookup"><span data-stu-id="d93b9-179">The `Receive-Job` cmdlet gets the results of a background job.</span></span> <span data-ttu-id="d93b9-180">如果作業已完成，則會 `Receive-Job` 取得所有工作結果。</span><span class="sxs-lookup"><span data-stu-id="d93b9-180">If the job is complete, `Receive-Job` gets all job results.</span></span> <span data-ttu-id="d93b9-181">如果作業仍在執行中， `Receive-Job` 則會取得到目前為止產生的結果。</span><span class="sxs-lookup"><span data-stu-id="d93b9-181">If the job is still running, `Receive-Job` gets the results that have been generated thus far.</span></span> <span data-ttu-id="d93b9-182">您可以 `Receive-Job` 再次執行命令以取得剩餘的結果。</span><span class="sxs-lookup"><span data-stu-id="d93b9-182">You can run `Receive-Job` commands again to get the remaining results.</span></span>

<span data-ttu-id="d93b9-183">傳回 `Receive-Job` 結果時，根據預設，它會從儲存工作結果的快取中刪除這些結果。</span><span class="sxs-lookup"><span data-stu-id="d93b9-183">When `Receive-Job` returns results, by default, it deletes those results from the cache where job results are stored.</span></span> <span data-ttu-id="d93b9-184">如果您執行另一個 `Receive-Job` 命令，則只會取得尚未接收的結果。</span><span class="sxs-lookup"><span data-stu-id="d93b9-184">If you run another `Receive-Job` command, you get only the results that are not yet received.</span></span>

<span data-ttu-id="d93b9-185">下列命令 `Receive-Job` 會顯示作業完成之前執行的命令結果。</span><span class="sxs-lookup"><span data-stu-id="d93b9-185">The following commands show the results of `Receive-Job` commands run before the job is complete.</span></span>

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

<span data-ttu-id="d93b9-186">若要防止 `Receive-Job` 刪除傳回的工作結果，請使用 **Keep** 參數。</span><span class="sxs-lookup"><span data-stu-id="d93b9-186">To prevent `Receive-Job` from deleting the job results that it has returned, use the **Keep** parameter.</span></span> <span data-ttu-id="d93b9-187">如此一來，就會傳回 `Receive-Job` 所有在該時間之前產生的結果。</span><span class="sxs-lookup"><span data-stu-id="d93b9-187">As a result, `Receive-Job` returns all of the results that have been generated until that time.</span></span>

<span data-ttu-id="d93b9-188">下列命令顯示在尚未完成的作業上使用 **Keep** 參數的效果。</span><span class="sxs-lookup"><span data-stu-id="d93b9-188">The following commands show the effect of using the **Keep** parameter on a job that is not yet complete.</span></span>

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

## <a name="waiting-for-the-results"></a><span data-ttu-id="d93b9-189">等候結果</span><span class="sxs-lookup"><span data-stu-id="d93b9-189">Waiting for the results</span></span>

<span data-ttu-id="d93b9-190">如果您執行需要很長時間才能完成的命令，您可以使用工作物件的屬性來判斷作業何時完成。</span><span class="sxs-lookup"><span data-stu-id="d93b9-190">If you run a command that takes a long time to complete, you can use the properties of the job object to determine when the job is complete.</span></span> <span data-ttu-id="d93b9-191">下列命令會使用 `Get-Job` 物件取得目前會話中的所有背景工作。</span><span class="sxs-lookup"><span data-stu-id="d93b9-191">The following command uses the `Get-Job` object to get all of the background jobs in the current session.</span></span>

```powershell
Get-Job
```

<span data-ttu-id="d93b9-192">結果會出現在資料表中。</span><span class="sxs-lookup"><span data-stu-id="d93b9-192">The results appear in a table.</span></span> <span data-ttu-id="d93b9-193">作業狀態會顯示在 [ **狀態** ] 資料行中。</span><span class="sxs-lookup"><span data-stu-id="d93b9-193">The status of the job appears in the **State** column.</span></span>

```
Id Name  PSJobTypeName State    HasMoreData Location  Command
-- ----  ------------- -----    ----------- --------  -------
1  Job1  BackgroundJob Complete True        localhost Get-Process
2  Job2  BackgroundJob Running  True        localhost Get-EventLog -Log ...
3  Job3  BackgroundJob Complete True        localhost dir -Path C:\* -Re...
```

<span data-ttu-id="d93b9-194">在此情況下，State 屬性會顯示作業2仍在執行。</span><span class="sxs-lookup"><span data-stu-id="d93b9-194">In this case, the State property reveals that Job 2 is still running.</span></span> <span data-ttu-id="d93b9-195">如果您現在要使用 `Receive-Job` Cmdlet 來取得工作結果，結果會是不完整的。</span><span class="sxs-lookup"><span data-stu-id="d93b9-195">If you were to use the `Receive-Job` cmdlet to get the job results now, the results would be incomplete.</span></span> <span data-ttu-id="d93b9-196">您可以重複使用此 `Receive-Job` Cmdlet 來取得所有結果。</span><span class="sxs-lookup"><span data-stu-id="d93b9-196">You can use the `Receive-Job` cmdlet repeatedly to get all of the results.</span></span> <span data-ttu-id="d93b9-197">根據預設，每次使用它時，您只會取得尚未接收的結果，但您可以使用 Cmdlet 的 **Keep** 參數 `Receive-Job` 來保留結果，即使已經收到這些結果也是一樣。</span><span class="sxs-lookup"><span data-stu-id="d93b9-197">By default, each time you use it, you get only the results that were not already received, but you can use the **Keep** parameter of the `Receive-Job` cmdlet to retain the results, even though they were already received.</span></span>

<span data-ttu-id="d93b9-198">您可以將部分結果寫入檔案，然後在新的結果抵達時附加它們，或者您可以稍後等候並檢查作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="d93b9-198">You can write the partial results to a file and then append newer results as they arrive or you can wait and check the state of the job later.</span></span>

<span data-ttu-id="d93b9-199">您可以使用 Cmdlet 的 **Wait** 參數 `Receive-Job` ，它不會傳回命令提示字元，直到工作完成且所有結果都可供使用為止。</span><span class="sxs-lookup"><span data-stu-id="d93b9-199">You can use the **Wait** parameter of the `Receive-Job` cmdlet, which does not return the command prompt until the job is complete and all results are available.</span></span>

<span data-ttu-id="d93b9-200">您也可以使用 `Wait-Job` Cmdlet 來等候工作的任何或所有結果。</span><span class="sxs-lookup"><span data-stu-id="d93b9-200">You can also use the `Wait-Job` cmdlet to wait for any or all of the results of the job.</span></span> <span data-ttu-id="d93b9-201">`Wait-Job` 讓您等待特定工作、所有作業，或任何要完成的作業。</span><span class="sxs-lookup"><span data-stu-id="d93b9-201">`Wait-Job` lets you wait for a particular job, for all jobs, or for any of the jobs to be completed.</span></span>

<span data-ttu-id="d93b9-202">下列命令會使用 `Wait-Job` Cmdlet 來等候 **識別碼** 為</span><span class="sxs-lookup"><span data-stu-id="d93b9-202">The following command uses the `Wait-Job` cmdlet to wait for a job with **ID**</span></span>
10.

```powershell
Wait-Job -ID 10
```

<span data-ttu-id="d93b9-203">因此，在作業完成之前，會抑制 PowerShell 提示字元。</span><span class="sxs-lookup"><span data-stu-id="d93b9-203">As a result, the PowerShell prompt is suppressed until the job is completed.</span></span>

<span data-ttu-id="d93b9-204">您也可以等候預定的一段時間。</span><span class="sxs-lookup"><span data-stu-id="d93b9-204">You can also wait for a predetermined period of time.</span></span> <span data-ttu-id="d93b9-205">此命令會使用 **Timeout** 參數將等待時間限制為120秒。</span><span class="sxs-lookup"><span data-stu-id="d93b9-205">This command uses the **Timeout** parameter to limit the wait to 120 seconds.</span></span> <span data-ttu-id="d93b9-206">當時間過期時，命令提示字元會傳回，但是工作會繼續在背景執行。</span><span class="sxs-lookup"><span data-stu-id="d93b9-206">When the time expires, the command prompt returns, but the job continues to run in the background.</span></span>

```powershell
Wait-Job -ID 10 -Timeout 120
```

## <a name="stopping-a-job"></a><span data-ttu-id="d93b9-207">停止作業</span><span class="sxs-lookup"><span data-stu-id="d93b9-207">Stopping a job</span></span>

<span data-ttu-id="d93b9-208">若要停止背景工作，請使用 `Stop-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d93b9-208">To stop a background job, use the `Stop-Job` cmdlet.</span></span> <span data-ttu-id="d93b9-209">下列命令會啟動作業，以取得系統事件記錄檔中的每個專案。</span><span class="sxs-lookup"><span data-stu-id="d93b9-209">The following command starts a job to get every entry in the System event log.</span></span> <span data-ttu-id="d93b9-210">它會將工作物件儲存在 `$job` 變數中。</span><span class="sxs-lookup"><span data-stu-id="d93b9-210">It saves the job object in the `$job` variable.</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-EventLog -Log System}
```

<span data-ttu-id="d93b9-211">下列命令會停止作業。</span><span class="sxs-lookup"><span data-stu-id="d93b9-211">The following command stops the job.</span></span> <span data-ttu-id="d93b9-212">它使用管線運算子 (`|`) 將變數中的工作傳送 `$job` 至 `Stop-Job` 。</span><span class="sxs-lookup"><span data-stu-id="d93b9-212">It uses a pipeline operator (`|`) to send the job in the `$job` variable to `Stop-Job`.</span></span>

```powershell
$job | Stop-Job
```

## <a name="deleting-a-job"></a><span data-ttu-id="d93b9-213">刪除作業</span><span class="sxs-lookup"><span data-stu-id="d93b9-213">Deleting a job</span></span>

<span data-ttu-id="d93b9-214">若要移除背景工作，請使用 `Remove-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d93b9-214">To delete a background job, use the `Remove-Job` cmdlet.</span></span> <span data-ttu-id="d93b9-215">下列命令會刪除變數中的工作 `$job` 。</span><span class="sxs-lookup"><span data-stu-id="d93b9-215">The following command deletes the job in the `$job` variable.</span></span>

```powershell
Remove-Job -Job $job
```

## <a name="investigating-a-failed-job"></a><span data-ttu-id="d93b9-216">調查失敗的作業</span><span class="sxs-lookup"><span data-stu-id="d93b9-216">Investigating a failed job</span></span>

<span data-ttu-id="d93b9-217">若要找出作業失敗的原因，請使用工作物件的 **Reason** 屬性。</span><span class="sxs-lookup"><span data-stu-id="d93b9-217">To find out why a job failed, use the **Reason** property of the job object.</span></span>

<span data-ttu-id="d93b9-218">下列命令會啟動不含所需認證的作業。</span><span class="sxs-lookup"><span data-stu-id="d93b9-218">The following command starts a job without the required credentials.</span></span> <span data-ttu-id="d93b9-219">它會將工作物件儲存在 `$job` 變數中。</span><span class="sxs-lookup"><span data-stu-id="d93b9-219">It saves the job object in the `$job` variable.</span></span>

```powershell
$job = Start-Job -ScriptBlock {New-Item -Path HKLM:\Software\MyCompany}

Id Name  PSJobTypeName State  HasMoreData  Location  Command
-- ----  ------------- -----  -----------  --------  -------
1  Job1  BackgroundJob Failed False        localhost New-Item -Path HKLM:...
```

<span data-ttu-id="d93b9-220">下列命令會使用 Reason 屬性來尋找導致作業失敗的錯誤。</span><span class="sxs-lookup"><span data-stu-id="d93b9-220">The following command uses the Reason property to find the error that caused the job to fail.</span></span>

```powershell
$job.ChildJobs[0].JobStateInfo.Reason
```

<span data-ttu-id="d93b9-221">在此情況下，作業失敗，因為遠端電腦需要明確的認證才能執行此命令。</span><span class="sxs-lookup"><span data-stu-id="d93b9-221">In this case, the job failed because the remote computer required explicit credentials to run the command.</span></span> <span data-ttu-id="d93b9-222">**Reason** 屬性的值為：</span><span class="sxs-lookup"><span data-stu-id="d93b9-222">The value of the **Reason** property is:</span></span>

<span data-ttu-id="d93b9-223">連線到遠端伺服器失敗，出現下列錯誤訊息：「拒絕存取」。</span><span class="sxs-lookup"><span data-stu-id="d93b9-223">Connecting to remote server failed with the following error message: "Access is denied".</span></span>

## <a name="see-also"></a><span data-ttu-id="d93b9-224">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d93b9-224">See also</span></span>

- [<span data-ttu-id="d93b9-225">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="d93b9-225">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)
- [<span data-ttu-id="d93b9-226">about_Thread_Jobs</span><span class="sxs-lookup"><span data-stu-id="d93b9-226">about_Thread_Jobs</span></span>](about_Thread_Jobs.md)
- [<span data-ttu-id="d93b9-227">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="d93b9-227">about_Job_Details</span></span>](about_Job_Details.md)
- [<span data-ttu-id="d93b9-228">about_Remote</span><span class="sxs-lookup"><span data-stu-id="d93b9-228">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="d93b9-229">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="d93b9-229">about_PSSessions</span></span>](about_PSSessions.md)
- [<span data-ttu-id="d93b9-230">Start-Job</span><span class="sxs-lookup"><span data-stu-id="d93b9-230">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="d93b9-231">Get-Job</span><span class="sxs-lookup"><span data-stu-id="d93b9-231">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="d93b9-232">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="d93b9-232">Receive-Job</span></span>](xref:Microsoft.PowerShell.Core.Receive-Job)
- [<span data-ttu-id="d93b9-233">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="d93b9-233">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="d93b9-234">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="d93b9-234">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="d93b9-235">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="d93b9-235">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
- [<span data-ttu-id="d93b9-236">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="d93b9-236">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)
