---
description: 說明如何在遠端電腦上執行工作。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_jobs?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Jobs
ms.openlocfilehash: 389db08a2b6528d14ff5f79cd4d369c23ed0c737
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524530"
---
# <a name="about-remote-jobs"></a><span data-ttu-id="a282f-104">關於遠端作業</span><span class="sxs-lookup"><span data-stu-id="a282f-104">About Remote Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="a282f-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="a282f-105">Short Description</span></span>
<span data-ttu-id="a282f-106">說明如何在遠端電腦上執行工作。</span><span class="sxs-lookup"><span data-stu-id="a282f-106">Describes how to run jobs on remote computers.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="a282f-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="a282f-107">Detailed Description</span></span>

<span data-ttu-id="a282f-108">PowerShell 會透過作業同時執行命令和腳本。</span><span class="sxs-lookup"><span data-stu-id="a282f-108">PowerShell concurrently runs commands and scripts through jobs.</span></span> <span data-ttu-id="a282f-109">PowerShell 提供三種工作類型來支援平行存取。</span><span class="sxs-lookup"><span data-stu-id="a282f-109">There are three jobs types provided by PowerShell to support concurrency.</span></span>

- <span data-ttu-id="a282f-110">`RemoteJob` -命令和腳本會在遠端會話中執行。</span><span class="sxs-lookup"><span data-stu-id="a282f-110">`RemoteJob` - Commands and scripts run in a remote session.</span></span>
- <span data-ttu-id="a282f-111">`BackgroundJob` -命令和腳本會在本機電腦上的個別進程中執行。</span><span class="sxs-lookup"><span data-stu-id="a282f-111">`BackgroundJob` - Commands and scripts run in a separate process on the local machine.</span></span> <span data-ttu-id="a282f-112">如需詳細資訊，請參閱 [about_Jobs](about_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="a282f-112">For more information, see [about_Jobs](about_Jobs.md).</span></span>
- <span data-ttu-id="a282f-113">`PSTaskJob` 或 `ThreadJob` -命令和腳本會在本機電腦上相同進程內的個別執行緒中執行。</span><span class="sxs-lookup"><span data-stu-id="a282f-113">`PSTaskJob` or `ThreadJob` - Commands and scripts run in a separate thread within the same process on the local machine.</span></span> <span data-ttu-id="a282f-114">如需詳細資訊，請參閱 [about_Thread_Jobs](/powershell/module/ThreadJob/about_Thread_Jobs)。</span><span class="sxs-lookup"><span data-stu-id="a282f-114">For more information, see [about_Thread_Jobs](/powershell/module/ThreadJob/about_Thread_Jobs).</span></span>

<span data-ttu-id="a282f-115">在不同的電腦或個別的進程中遠端執行腳本，可提供絕佳的隔離。</span><span class="sxs-lookup"><span data-stu-id="a282f-115">Running scripts remotely, on a separate machine or in a separate process, provide great isolation.</span></span> <span data-ttu-id="a282f-116">在遠端作業中發生的任何錯誤，都不會影響到其他執行中的作業或啟動作業的父會話。</span><span class="sxs-lookup"><span data-stu-id="a282f-116">Any errors that occur in the remote job do not affect other running jobs or the parent session that started the job.</span></span> <span data-ttu-id="a282f-117">不過，遠端層會增加額外負荷，包括物件序列化。</span><span class="sxs-lookup"><span data-stu-id="a282f-117">However, the remoting layer adds overhead, including object serialization.</span></span> <span data-ttu-id="a282f-118">所有物件都會進行序列化和還原序列化，因為它們會在父會話和遠端 (作業) 會話之間傳遞。</span><span class="sxs-lookup"><span data-stu-id="a282f-118">All objects are serialized and deserialized as they are passed between the parent session and the remote (job) session.</span></span> <span data-ttu-id="a282f-119">大型複雜資料物件的序列化可能會耗用大量的計算和記憶體資源，並在網路上傳輸大量資料。</span><span class="sxs-lookup"><span data-stu-id="a282f-119">Serialization of large complex data objects can consume large amounts of compute and memory resources and transfer large amounts of data across the network.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a282f-120">建立作業的父會話也會監視作業狀態，並收集管線資料。</span><span class="sxs-lookup"><span data-stu-id="a282f-120">The parent session that created the job also monitors the job status and collects pipeline data.</span></span> <span data-ttu-id="a282f-121">當工作達到已完成狀態時，父進程會終止作業子進程。</span><span class="sxs-lookup"><span data-stu-id="a282f-121">The job child process is terminated by the parent process once the job reaches a finished state.</span></span> <span data-ttu-id="a282f-122">如果父會話終止，則所有執行中的子工作都會連同其子進程一起終止。</span><span class="sxs-lookup"><span data-stu-id="a282f-122">If the parent session is terminated, all running child jobs are terminated along with their child processes.</span></span>

<span data-ttu-id="a282f-123">有兩種方法可以解決這種情況：</span><span class="sxs-lookup"><span data-stu-id="a282f-123">There are two ways work around this situation:</span></span>

1. <span data-ttu-id="a282f-124">用 `Invoke-Command` 來建立在已中斷連線的會話中執行的作業。</span><span class="sxs-lookup"><span data-stu-id="a282f-124">Use `Invoke-Command` to create jobs that run in disconnected sessions.</span></span> <span data-ttu-id="a282f-125">請參閱本文的卸 [離進程](#how-to-run-as-a-detached-process) 一節。</span><span class="sxs-lookup"><span data-stu-id="a282f-125">See the [detached processes](#how-to-run-as-a-detached-process) section of this article.</span></span>
1. <span data-ttu-id="a282f-126">用 `Start-Process` 來建立新的處理常式，而不是作業。</span><span class="sxs-lookup"><span data-stu-id="a282f-126">Use `Start-Process` to create a new process rather than a job.</span></span> <span data-ttu-id="a282f-127">如需詳細資訊，請參閱 [啟動流程](xref:Microsoft.PowerShell.Management.Start-Process)。</span><span class="sxs-lookup"><span data-stu-id="a282f-127">For more information, see [Start-Process](xref:Microsoft.PowerShell.Management.Start-Process).</span></span>

## <a name="remote-jobs"></a><span data-ttu-id="a282f-128">遠端作業</span><span class="sxs-lookup"><span data-stu-id="a282f-128">Remote Jobs</span></span>

<span data-ttu-id="a282f-129">您可以使用三種不同的方法，在遠端電腦上執行工作。</span><span class="sxs-lookup"><span data-stu-id="a282f-129">You can run jobs on remote computers by using three different methods.</span></span>

- <span data-ttu-id="a282f-130">在遠端電腦上啟動互動式會話。</span><span class="sxs-lookup"><span data-stu-id="a282f-130">Start an interactive session on a remote computer.</span></span> <span data-ttu-id="a282f-131">然後在互動式會話中啟動工作。</span><span class="sxs-lookup"><span data-stu-id="a282f-131">Then start a job in the interactive session.</span></span> <span data-ttu-id="a282f-132">雖然所有動作都是在遠端電腦上執行，但是這些程式與執行本機工作相同。</span><span class="sxs-lookup"><span data-stu-id="a282f-132">The procedures are the same as running a local job, although all actions are performed on the remote computer.</span></span>

- <span data-ttu-id="a282f-133">在將其結果傳回本機電腦的遠端電腦上執行工作。</span><span class="sxs-lookup"><span data-stu-id="a282f-133">Run a job on a remote computer that returns its results to the local computer.</span></span> <span data-ttu-id="a282f-134">當您想要收集工作的結果，並將其保留在本機電腦上的中央位置時，請使用這個方法。</span><span class="sxs-lookup"><span data-stu-id="a282f-134">Use this method when you want to collect the results of jobs and maintain them in a central location on the local computer.</span></span>

- <span data-ttu-id="a282f-135">在遠端電腦上執行作業，以在遠端電腦上維護其結果。</span><span class="sxs-lookup"><span data-stu-id="a282f-135">Run a job on a remote computer that maintains its results on the remote computer.</span></span> <span data-ttu-id="a282f-136">當工作資料在原始電腦上更安全地維護時，請使用這個方法。</span><span class="sxs-lookup"><span data-stu-id="a282f-136">Use this method when the job data is more securely maintained on the originating computer.</span></span>

### <a name="start-a-job-in-an-interactive-session"></a><span data-ttu-id="a282f-137">在互動式會話中啟動工作</span><span class="sxs-lookup"><span data-stu-id="a282f-137">Start a job in an interactive session</span></span>

<span data-ttu-id="a282f-138">您可以啟動遠端電腦的互動式會話，然後在互動式會話期間啟動作業。</span><span class="sxs-lookup"><span data-stu-id="a282f-138">You can start an interactive session with a remote computer and then start a job during the interactive session.</span></span> <span data-ttu-id="a282f-139">如需互動式會話的詳細資訊，請參閱 about_Remote，並參閱 `Enter-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="a282f-139">For more information about interactive sessions, see about_Remote, and see `Enter-PSSession`.</span></span>

<span data-ttu-id="a282f-140">在互動式會話中啟動作業的程式，與在本機電腦上啟動背景工作的程式幾乎完全相同。</span><span class="sxs-lookup"><span data-stu-id="a282f-140">The procedure for starting a job in an interactive session is almost identical to the procedure for starting a background job on the local computer.</span></span> <span data-ttu-id="a282f-141">但是，所有作業都會在遠端電腦上執行，而不是在本機電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="a282f-141">However, all of the operations occur on the remote computer, not the local computer.</span></span>

1. <span data-ttu-id="a282f-142">使用 `Enter-PSSession` Cmdlet 啟動遠端電腦的互動式會話。</span><span class="sxs-lookup"><span data-stu-id="a282f-142">Use the `Enter-PSSession` cmdlet to start an interactive session with a remote computer.</span></span> <span data-ttu-id="a282f-143">您可以使用的 ComputerName 參數 `Enter-PSSession` 來建立互動式會話的暫時連接。</span><span class="sxs-lookup"><span data-stu-id="a282f-143">You can use the ComputerName parameter of `Enter-PSSession` to establish a temporary connection for the interactive session.</span></span> <span data-ttu-id="a282f-144">或者，您可以使用 Session 參數，在 PowerShell 會話中執行互動式會話， (PSSession) 。</span><span class="sxs-lookup"><span data-stu-id="a282f-144">Or, you can use the Session parameter to run the interactive session in a PowerShell session (PSSession).</span></span>

   <span data-ttu-id="a282f-145">下列命令會在 Server01 電腦上啟動互動式會話。</span><span class="sxs-lookup"><span data-stu-id="a282f-145">The following command starts an interactive session on the Server01 computer.</span></span>

   ```powershell
   C:\PS> Enter-PSSession -computername Server01
   ```

   <span data-ttu-id="a282f-146">命令提示字元會變更，顯示您現在已連線到 Server01 電腦。</span><span class="sxs-lookup"><span data-stu-id="a282f-146">The command prompt changes to show that you are now connected to the Server01 computer.</span></span>

   ```
   Server01\C:>
   ```

1. <span data-ttu-id="a282f-147">若要在會話中啟動遠端作業，請使用 `Start-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a282f-147">To start a remote job in the session, use the `Start-Job` cmdlet.</span></span> <span data-ttu-id="a282f-148">下列命令會執行遠端作業，以取得 Server01 電腦上 Windows PowerShell 事件記錄檔中的事件。</span><span class="sxs-lookup"><span data-stu-id="a282f-148">The following command runs a remote job that gets the events in the Windows PowerShell event log on the Server01 computer.</span></span> <span data-ttu-id="a282f-149">`Start-Job`Cmdlet 會傳回代表作業的物件。</span><span class="sxs-lookup"><span data-stu-id="a282f-149">The `Start-Job` cmdlet returns an object that represents the job.</span></span>

   <span data-ttu-id="a282f-150">此命令會將工作物件儲存在 `$job` 變數中。</span><span class="sxs-lookup"><span data-stu-id="a282f-150">This command saves the job object in the `$job` variable.</span></span>

   ```powershell
   Server01\C:> $job = Start-Job -scriptblock {
     Get-Eventlog "Windows PowerShell"
   }
   ```

   <span data-ttu-id="a282f-151">當作業執行時，您可以使用互動式會話來執行其他命令，包括其他作業。</span><span class="sxs-lookup"><span data-stu-id="a282f-151">While the job runs, you can use the interactive session to run other commands, including other jobs.</span></span> <span data-ttu-id="a282f-152">不過，您必須讓互動式會話保持開啟，直到工作完成為止。</span><span class="sxs-lookup"><span data-stu-id="a282f-152">However, you must keep the interactive session open until the job is completed.</span></span> <span data-ttu-id="a282f-153">如果您結束會話，作業將會中斷，且結果會遺失。</span><span class="sxs-lookup"><span data-stu-id="a282f-153">If you end the session, the job is interrupted, and the results are lost.</span></span>

1. <span data-ttu-id="a282f-154">若要找出作業是否已完成，請顯示變數的值 `$job` ，或使用 `Get-Job` Cmdlet 來取得工作。</span><span class="sxs-lookup"><span data-stu-id="a282f-154">To find out if the job is complete, display the value of the `$job` variable, or use the `Get-Job` cmdlet to get the job.</span></span> <span data-ttu-id="a282f-155">下列命令會使用 `Get-Job` Cmdlet 來顯示工作。</span><span class="sxs-lookup"><span data-stu-id="a282f-155">The following command uses the `Get-Job` cmdlet to display the job.</span></span>

   ```powershell
   Server01\C:> Get-Job $job

   SessionId  Name  State      HasMoreData  Location   Command
   ---------  ----  -----      -----------  --------   -------
   1          Job1  Complete   True         localhost  Get-Eventlog "Windows...
   ```

   <span data-ttu-id="a282f-156">`Get-Job`輸出顯示作業在「localhost」電腦上執行，因為工作是在同一部電腦上啟動， (在此案例中為 Server01) 。</span><span class="sxs-lookup"><span data-stu-id="a282f-156">The `Get-Job` output shows that job is running on the "localhost" computer because the job was started on and is running on the same computer (in this case, Server01).</span></span>

1. <span data-ttu-id="a282f-157">若要取得作業的結果，請使用 `Receive-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a282f-157">To get the results of the job, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="a282f-158">您可以在互動式會話中顯示結果，或將結果儲存在遠端電腦上的檔案中。</span><span class="sxs-lookup"><span data-stu-id="a282f-158">You can display the results in the interactive session or save them to a file on the remote computer.</span></span> <span data-ttu-id="a282f-159">下列命令會取得 $job 變數中工作的結果。</span><span class="sxs-lookup"><span data-stu-id="a282f-159">The following command gets the results of the job in the $job variable.</span></span> <span data-ttu-id="a282f-160">此命令會使用重新導向操作員 (`>`) 將作業的結果儲存在 Server01 電腦上的 PsLog.txt 檔案中。</span><span class="sxs-lookup"><span data-stu-id="a282f-160">The command uses the redirection operator (`>`) to save the results of the job in the PsLog.txt file on the Server01 computer.</span></span>

   ```powershell
   Server01\C:> Receive-Job $job > c:\logs\PsLog.txt
   ```

1. <span data-ttu-id="a282f-161">若要結束互動式會話，請使用 `Exit-PSSession` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a282f-161">To end the interactive session, use the `Exit-PSSession` cmdlet.</span></span> <span data-ttu-id="a282f-162">命令提示字元會變更，顯示您已回到本機電腦上的原始會話。</span><span class="sxs-lookup"><span data-stu-id="a282f-162">The command prompt changes to show that you are back in the original session on the local computer.</span></span>

   ```powershell
   Server01\C:> Exit-PSSession
   C:\PS>
   ```

1. <span data-ttu-id="a282f-163">若要在 Server01 電腦上隨時查看檔案的內容 `PsLog.txt` ，請啟動另一個互動式會話，或執行遠端命令。</span><span class="sxs-lookup"><span data-stu-id="a282f-163">To view the contents of the `PsLog.txt` file on the Server01 computer at any time, start another interactive session, or run a remote command.</span></span> <span data-ttu-id="a282f-164">如果您想要使用數個命令來調查和管理檔案中的資料，這種類型的命令最適合在 PSSession (持續性連接) 中執行 `PsLog.txt` 。</span><span class="sxs-lookup"><span data-stu-id="a282f-164">This type of command is best run in a PSSession (a persistent connection) in case you want to use several commands to investigate and manage the data in the `PsLog.txt` file.</span></span> <span data-ttu-id="a282f-165">如需 Pssession 的詳細資訊，請參閱 [about_PSSessions](about_PSSessions.md)。</span><span class="sxs-lookup"><span data-stu-id="a282f-165">For more information about PSSessions, see [about_PSSessions](about_PSSessions.md).</span></span>

   <span data-ttu-id="a282f-166">下列命令使用指令程式 `New-PSSession` 來建立連線到 Server01 電腦的 **PSSession** ，並使用 `Invoke-Command` 指令程式 `Get-Content` 在 pssession 中執行命令以查看檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="a282f-166">The following commands use the `New-PSSession` cmdlet to create a **PSSession** that is connected to the Server01 computer, and they use the `Invoke-Command` cmdlet to run a `Get-Content` command in the PSSession to view the contents of the file.</span></span>

   ```powershell
   $s = New-PSSession -computername Server01
   Invoke-Command -session $s -scriptblock {
     Get-Content c:\logs\pslog.txt}
   ```

### <a name="start-a-remote-job-that-returns-the-results-to-the-local-computer-asjob"></a><span data-ttu-id="a282f-167">啟動將結果傳回到本機電腦 (AsJob 的遠端工作) </span><span class="sxs-lookup"><span data-stu-id="a282f-167">Start a remote job that returns the results to the local computer (AsJob)</span></span>

<span data-ttu-id="a282f-168">若要在將命令結果傳回本機電腦的遠端電腦上啟動作業，請使用 Cmdlet 的 **AsJob** 參數，例如 `Invoke-Command` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a282f-168">To start a job on a remote computer that returns the command results to the local computer, use the **AsJob** parameter of a cmdlet such as the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="a282f-169">當您使用 **AsJob** 參數時，會實際在本機電腦上建立工作物件，即使工作是在遠端電腦上執行也一樣。</span><span class="sxs-lookup"><span data-stu-id="a282f-169">When you use the **AsJob** parameter, the job object is actually created on the local computer even though the job runs on the remote computer.</span></span> <span data-ttu-id="a282f-170">當作業完成時，結果會傳回到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="a282f-170">When the job is completed, the results are returned to the local computer.</span></span>

<span data-ttu-id="a282f-171">您可以使用包含作業名詞 (工作 Cmdlet) 的 Cmdlet 來管理任何 Cmdlet 所建立的任何作業。</span><span class="sxs-lookup"><span data-stu-id="a282f-171">You can use the cmdlets that contain the Job noun (the Job cmdlets) to manage any job created by any cmdlet.</span></span> <span data-ttu-id="a282f-172">許多具有 **AsJob** 參數的 Cmdlet 都不會使用 PowerShell 遠端功能，因此您甚至可以在未設定為遠端執行且不符合遠端處理需求的電腦上使用它們。</span><span class="sxs-lookup"><span data-stu-id="a282f-172">Many of the cmdlets that have **AsJob** parameters do not use PowerShell remoting, so you can use them even on computers that are not configured for remoting and that do not meet the requirements for remoting.</span></span>

1. <span data-ttu-id="a282f-173">下列命令使用的 **AsJob** 參數，在 `Invoke-Command` Server01 電腦上啟動作業。</span><span class="sxs-lookup"><span data-stu-id="a282f-173">The following command uses the **AsJob** parameter of `Invoke-Command` to start a job on the Server01 computer.</span></span> <span data-ttu-id="a282f-174">作業 `Get-Eventlog` 會執行可取得系統記錄檔中事件的命令。</span><span class="sxs-lookup"><span data-stu-id="a282f-174">The job runs a `Get-Eventlog` command that gets the events in the System log.</span></span> <span data-ttu-id="a282f-175">您可以使用 JobName 參數來指派作業的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="a282f-175">You can use the JobName parameter to assign a display name to the job.</span></span>

   ```powershell
   Invoke-Command -computername Server01 -scriptblock {
     Get-Eventlog system} -AsJob
   ```

   <span data-ttu-id="a282f-176">命令的結果類似下列範例輸出。</span><span class="sxs-lookup"><span data-stu-id="a282f-176">The results of the command resemble the following sample output.</span></span>

   ```Output
   SessionId   Name   State    HasMoreData   Location   Command
   ---------   ----   -----    -----------   --------   -------
   1           Job1   Running  True          Server01   Get-Eventlog system
   ```

   <span data-ttu-id="a282f-177">使用 **AsJob** 參數時，會傳回 `Invoke-Command` 相同類型的工作物件，該物件會傳回 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="a282f-177">When the **AsJob** parameter is used, `Invoke-Command` returns the same type of job object that `Start-Job` returns.</span></span> <span data-ttu-id="a282f-178">您可以將工作物件儲存在變數中，也可以使用 `Get-Job` 命令來取得工作。</span><span class="sxs-lookup"><span data-stu-id="a282f-178">You can save the job object in a variable, or you can use a `Get-Job` command to get the job.</span></span>

   <span data-ttu-id="a282f-179">請注意，Location 屬性的值顯示作業已在 Server01 電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="a282f-179">Note that the value of the Location property shows that the job ran on the Server01 computer.</span></span>

1. <span data-ttu-id="a282f-180">若要使用 Cmdlet 的 **AsJob** 參數來管理啟動的作業 `Invoke-Command` ，請使用 job Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a282f-180">To manage a job started by using the **AsJob** parameter of the `Invoke-Command` cmdlet, use the Job cmdlets.</span></span> <span data-ttu-id="a282f-181">因為代表遠端作業的工作物件是在本機電腦上，所以您不需要執行遠端命令來管理作業。</span><span class="sxs-lookup"><span data-stu-id="a282f-181">Because the job object that represents the remote job is on the local computer, you do not need to run remote commands to manage the job.</span></span>

   <span data-ttu-id="a282f-182">若要判斷作業是否已完成，請使用 `Get-Job` 命令。</span><span class="sxs-lookup"><span data-stu-id="a282f-182">To determine whether the job is complete, use a `Get-Job` command.</span></span> <span data-ttu-id="a282f-183">下列命令會取得在目前會話中啟動的所有工作。</span><span class="sxs-lookup"><span data-stu-id="a282f-183">The following command gets all of the jobs that were started in the current session.</span></span>

   ```powershell
   Get-Job
   ```

   <span data-ttu-id="a282f-184">因為遠端作業是在目前的會話中啟動，所以本機 `Get-Job` 命令會取得工作。</span><span class="sxs-lookup"><span data-stu-id="a282f-184">Because the remote job was started in the current session, a local `Get-Job` command gets the job.</span></span> <span data-ttu-id="a282f-185">工作物件的 State 屬性顯示命令已順利完成。</span><span class="sxs-lookup"><span data-stu-id="a282f-185">The State property of the job object shows that the command was completed successfully.</span></span>

   ```Output
   SessionId   Name   State      HasMoreData   Location   Command
   ---------   ----   -----      -----------   --------   -------
   1           Job1   Completed  True          Server01   Get-Eventlog system
   ```

1. <span data-ttu-id="a282f-186">若要取得作業的結果，請使用 `Receive-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a282f-186">To get the results of the job, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="a282f-187">因為工作結果會自動傳回到工作物件所在的電腦，所以您可以使用本機命令來取得結果 `Receive-Job` 。</span><span class="sxs-lookup"><span data-stu-id="a282f-187">Because the job results are automatically returned to the computer where the job object resides, you can get the results with a local `Receive-Job` command.</span></span>

   <span data-ttu-id="a282f-188">下列命令會使用 `Receive-Job` Cmdlet 來取得工作的結果。</span><span class="sxs-lookup"><span data-stu-id="a282f-188">The following command uses the `Receive-Job` cmdlet to get the results of the job.</span></span> <span data-ttu-id="a282f-189">它會使用會話識別碼來識別工作。</span><span class="sxs-lookup"><span data-stu-id="a282f-189">It uses the session ID to identify the job.</span></span> <span data-ttu-id="a282f-190">此命令會將工作結果儲存在 $results 變數中。</span><span class="sxs-lookup"><span data-stu-id="a282f-190">This command saves the job results in the $results variable.</span></span> <span data-ttu-id="a282f-191">您也可以將結果重新導向至檔案。</span><span class="sxs-lookup"><span data-stu-id="a282f-191">You can also redirect the results to a file.</span></span>

   ```powershell
   $results = Receive-Job -id 1
   ```

### <a name="start-a-remote-job-that-keeps-the-results-on-the-remote-computer"></a><span data-ttu-id="a282f-192">啟動將結果保留在遠端電腦上的遠端作業</span><span class="sxs-lookup"><span data-stu-id="a282f-192">Start a remote job that keeps the results on the remote computer</span></span>

<span data-ttu-id="a282f-193">若要在遠端電腦上啟動可將命令結果保留在遠端電腦上的作業，請使用 `Invoke-Command` Cmdlet `Start-Job` 在遠端電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="a282f-193">To start a job on a remote computer that keeps the command results on the remote computer, use the `Invoke-Command` cmdlet to run a `Start-Job` command on a remote computer.</span></span> <span data-ttu-id="a282f-194">您可以使用此方法在多部電腦上執行工作。</span><span class="sxs-lookup"><span data-stu-id="a282f-194">You can use this method to run jobs on multiple computers.</span></span>

<span data-ttu-id="a282f-195">當您從遠端執行 `Start-Job` 命令時，會在遠端電腦上建立工作物件，並在遠端電腦上維護工作結果。</span><span class="sxs-lookup"><span data-stu-id="a282f-195">When you run a `Start-Job` command remotely, the job object is created on the remote computer, and the job results are maintained on the remote computer.</span></span>
<span data-ttu-id="a282f-196">從作業的觀點來看，所有作業都是本機的。</span><span class="sxs-lookup"><span data-stu-id="a282f-196">From the perspective of the job, all operations are local.</span></span> <span data-ttu-id="a282f-197">您只是在遠端執行命令來管理遠端電腦上的本機作業。</span><span class="sxs-lookup"><span data-stu-id="a282f-197">You are just running commands remotely to manage a local job on the remote computer.</span></span>

1. <span data-ttu-id="a282f-198">使用 `Invoke-Command` Cmdlet `Start-Job` 在遠端電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="a282f-198">Use the `Invoke-Command` cmdlet to run a `Start-Job` command on a remote computer.</span></span>

   <span data-ttu-id="a282f-199">此命令需要 PSSession (持續性連接) 。</span><span class="sxs-lookup"><span data-stu-id="a282f-199">This command requires a PSSession (a persistent connection).</span></span> <span data-ttu-id="a282f-200">如果您使用的 ComputerName 參數 `Invoke-Command` 建立暫時連接，則在 `Invoke-Command` 傳回工作物件時，會將該命令視為已完成。</span><span class="sxs-lookup"><span data-stu-id="a282f-200">If you use the ComputerName parameter of `Invoke-Command` to establish a temporary connection, the `Invoke-Command` command is considered to be complete when the job object is returned.</span></span> <span data-ttu-id="a282f-201">如此一來，就會關閉暫時連接，並取消作業。</span><span class="sxs-lookup"><span data-stu-id="a282f-201">As a result, the temporary connection is closed, and the job is canceled.</span></span>

   <span data-ttu-id="a282f-202">下列命令 `New-PSSession` 會使用 Cmdlet 來建立連線到 Server01 電腦的 PSSession。</span><span class="sxs-lookup"><span data-stu-id="a282f-202">The following command uses the `New-PSSession` cmdlet to create a PSSession that is connected to the Server01 computer.</span></span> <span data-ttu-id="a282f-203">此命令會將 PSSession 儲存在 `$s` 變數中。</span><span class="sxs-lookup"><span data-stu-id="a282f-203">The command saves the PSSession in the `$s` variable.</span></span>

   ```powershell
   $s = New-PSSession -computername Server01
   ```

   <span data-ttu-id="a282f-204">下一個命令會使用 `Invoke-Command` Cmdlet `Start-Job` 在 PSSession 中執行命令。</span><span class="sxs-lookup"><span data-stu-id="a282f-204">The next command uses the `Invoke-Command` cmdlet to run a `Start-Job` command in the PSSession.</span></span> <span data-ttu-id="a282f-205">`Start-Job`命令和 `Get-Eventlog` 命令會以大括弧括住。</span><span class="sxs-lookup"><span data-stu-id="a282f-205">The `Start-Job` command and the `Get-Eventlog` command are enclosed in braces.</span></span>

   ```powershell
   Invoke-Command -session $s -scriptblock {
     Start-Job -scriptblock {Get-Eventlog system}}
   ```

   <span data-ttu-id="a282f-206">結果類似下列範例輸出。</span><span class="sxs-lookup"><span data-stu-id="a282f-206">The results resemble the following sample output.</span></span>

   ```Output
   Id       Name    State      HasMoreData     Location   Command
   --       ----    -----      -----------     --------   -------
   2        Job2    Running    True            Localhost  Get-Eventlog system
   ```

   <span data-ttu-id="a282f-207">當您 `Start-Job` 從遠端執行命令時，會傳回 `Invoke-Command` 相同類型的工作物件，該物件會傳回 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="a282f-207">When you run a `Start-Job` command remotely, `Invoke-Command` returns the same type of job object that `Start-Job` returns.</span></span> <span data-ttu-id="a282f-208">您可以將工作物件儲存在變數中，也可以使用 `Get-Job` 命令來取得工作。</span><span class="sxs-lookup"><span data-stu-id="a282f-208">You can save the job object in a variable, or you can use a `Get-Job` command to get the job.</span></span>

   <span data-ttu-id="a282f-209">請注意，[ **位置** ] 屬性的值會顯示在本機電腦上執行的作業（稱為 "LocalHost"），即使作業在 Server01 電腦上執行也一樣。</span><span class="sxs-lookup"><span data-stu-id="a282f-209">Note that the value of the **Location** property shows that the job ran on the local computer, known as "LocalHost", even though the job ran on the Server01 computer.</span></span> <span data-ttu-id="a282f-210">由於工作物件是在 Server01 電腦上建立的，而且工作會在同一部電腦上執行，因此會被視為本機背景工作。</span><span class="sxs-lookup"><span data-stu-id="a282f-210">Because the job object is created on the Server01 computer and the job runs on the same computer, it is considered to be a local background job.</span></span>

1. <span data-ttu-id="a282f-211">若要管理遠端作業，請使用 **job** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a282f-211">To manage a remote job, use the **Job** cmdlets.</span></span> <span data-ttu-id="a282f-212">因為工作物件是在遠端電腦上，所以您需要執行遠端命令以取得、停止、等候或取出工作結果。</span><span class="sxs-lookup"><span data-stu-id="a282f-212">Because the job object is on the remote computer, you need to run remote commands to get, stop, wait for, or retrieve the job results.</span></span>

   <span data-ttu-id="a282f-213">若要查看作業是否已完成，請使用 `Invoke-Command` 命令 `Get-Job` 在連線到 Server01 電腦的 PSSession 中執行命令。</span><span class="sxs-lookup"><span data-stu-id="a282f-213">To see if the job is complete, use an `Invoke-Command` command to run a `Get-Job` command in the PSSession that is connected to the Server01 computer.</span></span>

   ```powershell
   Invoke-Command -session $s -scriptblock {Get-Job}
   ```

   <span data-ttu-id="a282f-214">命令會傳回工作物件。</span><span class="sxs-lookup"><span data-stu-id="a282f-214">The command returns a job object.</span></span> <span data-ttu-id="a282f-215">工作物件的 **State** 屬性顯示命令已順利完成。</span><span class="sxs-lookup"><span data-stu-id="a282f-215">The **State** property of the job object shows that the command was completed successfully.</span></span>

   ```Output
   SessionId   Name  State      HasMoreData   Location   Command
   ---------   ----  -----      -----------   --------   -------
   2           Job2  Completed  True          LocalHost   Get-Eventlog system
   ```

1. <span data-ttu-id="a282f-216">若要取得作業的結果，請使用 `Invoke-Command` `Receive-Job` 指令程式在連接到 Server01 電腦的 PSSession 中執行命令。</span><span class="sxs-lookup"><span data-stu-id="a282f-216">To get the results of the job, use the `Invoke-Command` cmdlet to run a `Receive-Job` command in the PSSession that is connected to the Server01 computer.</span></span>

   <span data-ttu-id="a282f-217">下列命令會使用 `Receive-Job` Cmdlet 來取得工作的結果。</span><span class="sxs-lookup"><span data-stu-id="a282f-217">The following command uses the `Receive-Job` cmdlet to get the results of the job.</span></span> <span data-ttu-id="a282f-218">它會使用會話識別碼來識別工作。</span><span class="sxs-lookup"><span data-stu-id="a282f-218">It uses the session ID to identify the job.</span></span> <span data-ttu-id="a282f-219">此命令會將工作結果儲存在 `$results` 變數中。</span><span class="sxs-lookup"><span data-stu-id="a282f-219">This command saves the job results in the `$results` variable.</span></span> <span data-ttu-id="a282f-220">它使用的 [保留] 參數 `Receive-Job` ，將結果保留在遠端電腦上的工作快取中。</span><span class="sxs-lookup"><span data-stu-id="a282f-220">It uses the Keep parameter of `Receive-Job` to keep the result in the job cache on the remote computer.</span></span>

   ```powershell
   $results = Invoke-Command -session $s -scriptblock {
     Receive-Job -SessionId 2 -Keep
   }
   ```

   <span data-ttu-id="a282f-221">您也可以將結果重新導向至本機或遠端電腦上的檔案。</span><span class="sxs-lookup"><span data-stu-id="a282f-221">You can also redirect the results to a file on the local or remote computer.</span></span>
   <span data-ttu-id="a282f-222">下列命令會使用重新導向運算子，將結果儲存在 Server01 電腦上的檔案中。</span><span class="sxs-lookup"><span data-stu-id="a282f-222">The following command uses a redirection operator to save the results in a file on the Server01 computer.</span></span>

   ```powershell
   Invoke-Command -session $s -command {
     Receive-Job -SessionId 2 > c:\logs\pslog.txt
   }
   ```

## <a name="how-to-run-as-a-detached-process"></a><span data-ttu-id="a282f-223">如何以卸離進程的形式執行</span><span class="sxs-lookup"><span data-stu-id="a282f-223">How to run as a detached process</span></span>

<span data-ttu-id="a282f-224">如先前所述，當父會話終止時，所有執行中的子工作都會連同其子進程一起終止。</span><span class="sxs-lookup"><span data-stu-id="a282f-224">As previously mentioned, when the parent session is terminated, all running child jobs are terminated along with their child processes.</span></span> <span data-ttu-id="a282f-225">您可以使用本機電腦上的遠端處理，來執行未附加至目前 PowerShell 會話的作業。</span><span class="sxs-lookup"><span data-stu-id="a282f-225">You can use remoting on the local machine to run jobs that are not attached to the current PowerShell session.</span></span>

<span data-ttu-id="a282f-226">在本機電腦上建立新的 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="a282f-226">Create a new PowerShell session on the local machine.</span></span> <span data-ttu-id="a282f-227">`Invoke-Command`在此會話中用來啟動作業的。</span><span class="sxs-lookup"><span data-stu-id="a282f-227">The use `Invoke-Command` to start a job in this session.</span></span> <span data-ttu-id="a282f-228">`Invoke-Command` 可讓您中斷遠端會話的連線，並終止父會話。</span><span class="sxs-lookup"><span data-stu-id="a282f-228">`Invoke-Command` allows you to disconnect a remote session and terminate the parent session.</span></span> <span data-ttu-id="a282f-229">稍後，您可以啟動新的 PowerShell 會話，並連接到先前已中斷連線的會話，以繼續監視工作。</span><span class="sxs-lookup"><span data-stu-id="a282f-229">Later, you can start a new PowerShell session and connect to the previously disconnected session to resume monitoring the job.</span></span> <span data-ttu-id="a282f-230">不過，當會話終止時，傳回至原始 PowerShell 會話的任何資料都會遺失。</span><span class="sxs-lookup"><span data-stu-id="a282f-230">However, any data that was returned to the original PowerShell session is lost when that session is terminated.</span></span> <span data-ttu-id="a282f-231">重新連線時，只會傳回中斷連接後所產生的新資料物件。</span><span class="sxs-lookup"><span data-stu-id="a282f-231">Only new data objects generated after the disconnect are returned when re-connected.</span></span>

```powershell
# Create remote session on local machine
PS> $session = New-PSSession -cn localhost

# Start remote job
PS> $job = Invoke-Command -Session $session -ScriptBlock { 1..60 | % { sleep 1; "Output $_" } } -AsJob
PS> $job

Id     Name     PSJobTypeName   State         HasMoreData     Location      Command
--     ----     -------------   -----         -----------     --------      -------
1      Job1     RemoteJob       Running       True            localhost     1..60 | % { sleep 1; ...

# Disconnect the job session
PS> Disconnect-PSSession $session

Id Name         Transport ComputerName    ComputerType    State         ConfigurationName     Availability
-- ----         --------- ------------    ------------    -----         -----------------     ------------
1 Runspace1     WSMan     localhost       RemoteMachine   Disconnected  Microsoft.PowerShell          None

PS> $job

Id     Name     PSJobTypeName   State         HasMoreData     Location      Command
--     ----     -------------   -----         -----------     --------      -------
1      Job1     RemoteJob       Disconnected  True            localhost     1..60 | % { sleep 1;

# Reconnect the session to a new job object
PS> $jobNew = Receive-PSSession -Session $session -OutTarget Job
PS> $job | Wait-Job | Receive-Job
Output 9
Output 10
Output 11
...
```

<span data-ttu-id="a282f-232">在此範例中，作業仍會附加至父 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="a282f-232">For this example, the jobs are still attached to a parent PowerShell session.</span></span>
<span data-ttu-id="a282f-233">不過，父會話不是執行所在的原始 PowerShell 會話 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="a282f-233">However, the parent session is not the original PowerShell session where `Invoke-Command` was run.</span></span>

## <a name="see-also"></a><span data-ttu-id="a282f-234">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a282f-234">See also</span></span>

- [<span data-ttu-id="a282f-235">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="a282f-235">about_Jobs</span></span>](about_Jobs.md)
- [<span data-ttu-id="a282f-236">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="a282f-236">about_Job_Details</span></span>](about_Job_Details.md)
- [<span data-ttu-id="a282f-237">about_Remote</span><span class="sxs-lookup"><span data-stu-id="a282f-237">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="a282f-238">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="a282f-238">about_Remote_Variables</span></span>](about_Remote_Variables.md)
- [<span data-ttu-id="a282f-239">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="a282f-239">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)
- [<span data-ttu-id="a282f-240">Start-Job</span><span class="sxs-lookup"><span data-stu-id="a282f-240">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="a282f-241">Get-Job</span><span class="sxs-lookup"><span data-stu-id="a282f-241">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="a282f-242">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="a282f-242">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="a282f-243">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="a282f-243">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="a282f-244">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="a282f-244">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
- [<span data-ttu-id="a282f-245">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="a282f-245">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)
- [<span data-ttu-id="a282f-246">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="a282f-246">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)
- [<span data-ttu-id="a282f-247">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="a282f-247">Exit-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Exit-PSSession)
