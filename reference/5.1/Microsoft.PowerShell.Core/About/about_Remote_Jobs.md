---
description: 說明如何在遠端電腦上執行背景工作。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_jobs?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Jobs
ms.openlocfilehash: 5e74de2684d65a66025c4f2c815e9130dfe57e05
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207931"
---
# <a name="about-remote-jobs"></a><span data-ttu-id="0d373-104">關於遠端作業</span><span class="sxs-lookup"><span data-stu-id="0d373-104">About Remote Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="0d373-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="0d373-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="0d373-106">說明如何在遠端電腦上執行背景工作。</span><span class="sxs-lookup"><span data-stu-id="0d373-106">Describes how to run background jobs on remote computers.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="0d373-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="0d373-107">DETAILED DESCRIPTION</span></span>

<span data-ttu-id="0d373-108">背景工作是非同步執行的命令，而不會與目前的會話互動。</span><span class="sxs-lookup"><span data-stu-id="0d373-108">A background job is a command that runs asynchronously without interacting with the current session.</span></span> <span data-ttu-id="0d373-109">命令提示字元會立即傳回，而您可以在作業執行時繼續使用會話。</span><span class="sxs-lookup"><span data-stu-id="0d373-109">The command prompt returns immediately, and you can continue to use the session while the job runs.</span></span>

<span data-ttu-id="0d373-110">根據預設，背景工作會在本機電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="0d373-110">By default, background jobs run on the local computer.</span></span> <span data-ttu-id="0d373-111">不過，您可以使用數個不同的程式，在遠端電腦上執行背景工作。</span><span class="sxs-lookup"><span data-stu-id="0d373-111">However, you can use several different procedures to run background jobs on remote computers.</span></span>

<span data-ttu-id="0d373-112">本主題說明如何在遠端電腦上執行背景工作。</span><span class="sxs-lookup"><span data-stu-id="0d373-112">This topic explains how to run a background job on a remote computer.</span></span> <span data-ttu-id="0d373-113">如需有關如何在本機電腦上執行背景工作的詳細資訊，請參閱 [about_Jobs](about_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="0d373-113">For information about how to run background jobs on a local computer, see [about_Jobs](about_Jobs.md).</span></span> <span data-ttu-id="0d373-114">如需背景工作的詳細資訊，請參閱 [about_Job_Details](about_Job_Details.md)。</span><span class="sxs-lookup"><span data-stu-id="0d373-114">For more information about background jobs, see [about_Job_Details](about_Job_Details.md).</span></span>

## <a name="remote-background-jobs"></a><span data-ttu-id="0d373-115">遠端背景工作</span><span class="sxs-lookup"><span data-stu-id="0d373-115">REMOTE BACKGROUND JOBS</span></span>

<span data-ttu-id="0d373-116">您可以使用三種不同的方法，在遠端電腦上執行背景工作。</span><span class="sxs-lookup"><span data-stu-id="0d373-116">You can run background jobs on remote computers by using three different methods.</span></span>

- <span data-ttu-id="0d373-117">啟動遠端電腦的互動式會話，並在互動式會話中啟動工作。</span><span class="sxs-lookup"><span data-stu-id="0d373-117">Start an interactive session with a remote computer, and start a job in the interactive session.</span></span> <span data-ttu-id="0d373-118">雖然所有動作都是在遠端電腦上執行，但是這些程式與執行本機工作相同。</span><span class="sxs-lookup"><span data-stu-id="0d373-118">The procedures are the same as running a local job, although all actions are performed on the remote computer.</span></span>

- <span data-ttu-id="0d373-119">在將其結果傳回本機電腦的遠端電腦上執行背景工作。</span><span class="sxs-lookup"><span data-stu-id="0d373-119">Run a background job on a remote computer that returns its results to the local computer.</span></span> <span data-ttu-id="0d373-120">當您想要收集背景工作的結果，並將其保留在本機電腦上的中央位置時，請使用這個方法。</span><span class="sxs-lookup"><span data-stu-id="0d373-120">Use this method when you want to collect the results of background jobs and maintain them in a central location on the local computer.</span></span>

- <span data-ttu-id="0d373-121">在遠端電腦上執行背景工作，以在遠端電腦上維護其結果。</span><span class="sxs-lookup"><span data-stu-id="0d373-121">Run a background job on a remote computer that maintains its results on the remote computer.</span></span> <span data-ttu-id="0d373-122">當工作資料在原始電腦上更安全地維護時，請使用這個方法。</span><span class="sxs-lookup"><span data-stu-id="0d373-122">Use this method when the job data is more securely maintained on the originating computer.</span></span>

### <a name="start-a-background-job-in-an-interactive-session"></a><span data-ttu-id="0d373-123">在互動式會話中啟動背景工作</span><span class="sxs-lookup"><span data-stu-id="0d373-123">START A BACKGROUND JOB IN AN INTERACTIVE SESSION</span></span>

<span data-ttu-id="0d373-124">您可以啟動遠端電腦的互動式會話，然後在互動式會話期間啟動背景工作。</span><span class="sxs-lookup"><span data-stu-id="0d373-124">You can start an interactive session with a remote computer and then start a background job during the interactive session.</span></span> <span data-ttu-id="0d373-125">如需互動式會話的詳細資訊，請參閱 about_Remote，並查看輸入 PSSession。</span><span class="sxs-lookup"><span data-stu-id="0d373-125">For more information about interactive sessions, see about_Remote, and see Enter-PSSession.</span></span>

<span data-ttu-id="0d373-126">在互動式會話中啟動背景工作的程式，與在本機電腦上啟動背景工作的程式幾乎完全相同。</span><span class="sxs-lookup"><span data-stu-id="0d373-126">The procedure for starting a background job in an interactive session is almost identical to the procedure for starting a background job on the local computer.</span></span> <span data-ttu-id="0d373-127">但是，所有作業都會在遠端電腦上執行，而不是在本機電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="0d373-127">However, all of the operations occur on the remote computer, not the local computer.</span></span>

#### <a name="step-1-enter-pssession"></a><span data-ttu-id="0d373-128">步驟1：輸入-PSSESSION</span><span class="sxs-lookup"><span data-stu-id="0d373-128">STEP 1: ENTER-PSSESSION</span></span>

<span data-ttu-id="0d373-129">使用 Enter-PSSession Cmdlet 來啟動遠端電腦的互動式會話。</span><span class="sxs-lookup"><span data-stu-id="0d373-129">Use the Enter-PSSession cmdlet to start an interactive session with a remote computer.</span></span> <span data-ttu-id="0d373-130">您可以使用 Enter-PSSession 的 ComputerName 參數來建立互動式會話的暫時連接。</span><span class="sxs-lookup"><span data-stu-id="0d373-130">You can use the ComputerName parameter of Enter-PSSession to establish a temporary connection for the interactive session.</span></span> <span data-ttu-id="0d373-131">或者，您可以使用 Session 參數，在 Windows PowerShell 會話中執行互動式會話 (PSSession) 。</span><span class="sxs-lookup"><span data-stu-id="0d373-131">Or, you can use the Session parameter to run the interactive session in a Windows PowerShell session (PSSession).</span></span>

<span data-ttu-id="0d373-132">下列命令會在 Server01 電腦上啟動互動式會話。</span><span class="sxs-lookup"><span data-stu-id="0d373-132">The following command starts an interactive session on the Server01 computer.</span></span>

```powershell
C:\PS> Enter-PSSession -computername Server01
```

<span data-ttu-id="0d373-133">命令提示字元會變更，顯示您現在已連線到 Server01 電腦。</span><span class="sxs-lookup"><span data-stu-id="0d373-133">The command prompt changes to show that you are now connected to the Server01 computer.</span></span>

```
Server01\C:>
```

#### <a name="step-2-start-job"></a><span data-ttu-id="0d373-134">步驟2：啟動-作業</span><span class="sxs-lookup"><span data-stu-id="0d373-134">STEP 2: START-JOB</span></span>

<span data-ttu-id="0d373-135">若要在會話中啟動背景工作，請使用 Start-Job Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0d373-135">To start a background job in the session, use the Start-Job cmdlet.</span></span>

<span data-ttu-id="0d373-136">下列命令會執行背景工作，以取得 Server01 電腦上 Windows PowerShell 事件記錄檔中的事件。</span><span class="sxs-lookup"><span data-stu-id="0d373-136">The following command runs a background job that gets the events in the Windows PowerShell event log on the Server01 computer.</span></span> <span data-ttu-id="0d373-137">Start-Job Cmdlet 會傳回代表作業的物件。</span><span class="sxs-lookup"><span data-stu-id="0d373-137">The Start-Job cmdlet returns an object that represents the job.</span></span>

<span data-ttu-id="0d373-138">此命令會將工作物件儲存在 \$ 工作變數中。</span><span class="sxs-lookup"><span data-stu-id="0d373-138">This command saves the job object in the \$job variable.</span></span>

```powershell
Server01\C:> $job = start-job -scriptblock {
  get-eventlog "Windows PowerShell"
}
```

<span data-ttu-id="0d373-139">當作業執行時，您可以使用互動式會話來執行其他命令，包括其他背景工作。</span><span class="sxs-lookup"><span data-stu-id="0d373-139">While the job runs, you can use the interactive session to run other commands, including other background jobs.</span></span> <span data-ttu-id="0d373-140">不過，您必須讓互動式會話保持開啟，直到工作完成為止。</span><span class="sxs-lookup"><span data-stu-id="0d373-140">However, you must keep the interactive session open until the job is completed.</span></span> <span data-ttu-id="0d373-141">如果您結束會話，作業將會中斷，且結果會遺失。</span><span class="sxs-lookup"><span data-stu-id="0d373-141">If you end the session, the job is interrupted, and the results are lost.</span></span>

#### <a name="step-3-get-job"></a><span data-ttu-id="0d373-142">步驟3：取得-作業</span><span class="sxs-lookup"><span data-stu-id="0d373-142">STEP 3: GET-JOB</span></span>

<span data-ttu-id="0d373-143">若要找出作業是否已完成，請顯示 \$ 工作變數的值，或使用 Get-Job Cmdlet 取得工作。</span><span class="sxs-lookup"><span data-stu-id="0d373-143">To find out if the job is complete, display the value of the \$job variable, or use the Get-Job cmdlet to get the job.</span></span> <span data-ttu-id="0d373-144">下列命令使用 Get-Job Cmdlet 來顯示工作。</span><span class="sxs-lookup"><span data-stu-id="0d373-144">The following command uses the Get-Job cmdlet to display the job.</span></span>

```powershell
Server01\C:> get-job $job

SessionId  Name  State      HasMoreData  Location   Command
---------  ----  -----      -----------  --------   -------
1          Job1  Complete   True         localhost  get-eventlog "Windows...
```

<span data-ttu-id="0d373-145">Get-Job 輸出顯示作業正在 "localhost" 電腦上執行，因為工作是在同一部電腦上啟動，而且在相同的電腦上執行 (在此案例中為 Server01) 。</span><span class="sxs-lookup"><span data-stu-id="0d373-145">The Get-Job output shows that job is running on the "localhost" computer because the job was started on and is running on the same computer (in this case, Server01).</span></span>

#### <a name="step-4-receive-job"></a><span data-ttu-id="0d373-146">步驟4：接收作業</span><span class="sxs-lookup"><span data-stu-id="0d373-146">STEP 4: RECEIVE-JOB</span></span>

<span data-ttu-id="0d373-147">若要取得作業的結果，請使用 Receive-Job Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0d373-147">To get the results of the job, use the Receive-Job cmdlet.</span></span> <span data-ttu-id="0d373-148">您可以在互動式會話中顯示結果，或將結果儲存在遠端電腦上的檔案中。</span><span class="sxs-lookup"><span data-stu-id="0d373-148">You can display the results in the interactive session or save them to a file on the remote computer.</span></span> <span data-ttu-id="0d373-149">下列命令會取得 $job 變數中工作的結果。</span><span class="sxs-lookup"><span data-stu-id="0d373-149">The following command gets the results of the job in the $job variable.</span></span> <span data-ttu-id="0d373-150">此命令會使用重新導向操作員 ( # A0) 將作業的結果儲存在 Server01 電腦上的 PsLog.txt 檔案中。</span><span class="sxs-lookup"><span data-stu-id="0d373-150">The command uses the redirection operator (>) to save the results of the job in the PsLog.txt file on the Server01 computer.</span></span>

```powershell
Server01\C:> receive-job $job > c:\logs\PsLog.txt
```

#### <a name="step-5-exit-pssession"></a><span data-ttu-id="0d373-151">步驟5： EXIT-PSSESSION</span><span class="sxs-lookup"><span data-stu-id="0d373-151">STEP 5: EXIT-PSSESSION</span></span>

<span data-ttu-id="0d373-152">若要結束互動式會話，請使用 Exit-PSSession Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0d373-152">To end the interactive session, use the Exit-PSSession cmdlet.</span></span> <span data-ttu-id="0d373-153">命令提示字元會變更，顯示您已回到本機電腦上的原始會話。</span><span class="sxs-lookup"><span data-stu-id="0d373-153">The command prompt changes to show that you are back in the original session on the local computer.</span></span>

```powershell
Server01\C:> Exit-PSSession
C:\PS>
```

#### <a name="step-6-invoke-command-get-content"></a><span data-ttu-id="0d373-154">步驟6： INVOKE-COMMAND： GET-CONTENT</span><span class="sxs-lookup"><span data-stu-id="0d373-154">STEP 6: INVOKE-COMMAND: GET-CONTENT</span></span>

<span data-ttu-id="0d373-155">若要在 Server01 電腦上隨時查看 PsLog.txt 檔案的內容，請啟動另一個互動式會話，或執行遠端命令。</span><span class="sxs-lookup"><span data-stu-id="0d373-155">To view the contents of the PsLog.txt file on the Server01 computer at any time, start another interactive session, or run a remote command.</span></span> <span data-ttu-id="0d373-156">如果您想要使用數個命令來調查和管理 PsLog.txt 檔中的資料，這種類型的命令最適合在 PSSession (持續性連接) 中執行。</span><span class="sxs-lookup"><span data-stu-id="0d373-156">This type of command is best run in a PSSession (a persistent connection) in case you want to use several commands to investigate and manage the data in the PsLog.txt file.</span></span> <span data-ttu-id="0d373-157">如需 Pssession 的詳細資訊，請參閱 about_PSSessions。</span><span class="sxs-lookup"><span data-stu-id="0d373-157">For more information about PSSessions, see about_PSSessions.</span></span>

<span data-ttu-id="0d373-158">下列命令使用 New-PSSession Cmdlet 來建立連線到 Server01 電腦的 PSSession，並使用 Invoke-Command Cmdlet 在 PSSession 中執行 Get-Content 命令以查看檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="0d373-158">The following commands use the New-PSSession cmdlet to create a PSSession that is connected to the Server01 computer, and they use the Invoke-Command cmdlet to run a Get-Content command in the PSSession to view the contents of the file.</span></span>

```powershell
$s = new-pssession -computername Server01
invoke-command -session $s -scriptblock {
  get-content c:\logs\pslog.txt}
```

### <a name="start-a-remote-job-that-returns-the-results-to-the-local-computer-asjob"></a><span data-ttu-id="0d373-159">啟動將結果傳回到本機電腦 ASJOB 的遠端作業 \(\)</span><span class="sxs-lookup"><span data-stu-id="0d373-159">START A REMOTE JOB THAT RETURNS THE RESULTS TO THE LOCAL COMPUTER \(ASJOB\)</span></span>

<span data-ttu-id="0d373-160">若要在將命令結果傳回本機電腦的遠端電腦上啟動背景工作，請使用 Cmdlet 的 AsJob 參數，例如 Invoke-Command Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0d373-160">To start a background job on a remote computer that returns the command results to the local computer, use the AsJob parameter of a cmdlet such as the Invoke-Command cmdlet.</span></span>

<span data-ttu-id="0d373-161">當您使用 AsJob 參數時，會實際在本機電腦上建立工作物件，即使工作是在遠端電腦上執行也一樣。</span><span class="sxs-lookup"><span data-stu-id="0d373-161">When you use the AsJob parameter, the job object is actually created on the local computer even though the job runs on the remote computer.</span></span> <span data-ttu-id="0d373-162">當作業完成時，結果會傳回到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="0d373-162">When the job is completed, the results are returned to the local computer.</span></span>

<span data-ttu-id="0d373-163">您可以使用包含作業名詞 (工作 Cmdlet) 的 Cmdlet 來管理任何 Cmdlet 所建立的任何作業。</span><span class="sxs-lookup"><span data-stu-id="0d373-163">You can use the cmdlets that contain the Job noun (the Job cmdlets) to manage any job created by any cmdlet.</span></span> <span data-ttu-id="0d373-164">許多具有 AsJob 參數的 Cmdlet 都不會使用 Windows PowerShell 遠端功能，因此您甚至可以在未設定為進行遠端處理的電腦上使用它們，也不符合遠端處理的需求。</span><span class="sxs-lookup"><span data-stu-id="0d373-164">Many of the cmdlets that have AsJob parameters do not use Windows PowerShell remoting, so you can use them even on computers that are not configured for remoting and that do not meet the requirements for remoting.</span></span>

#### <a name="step-1-invoke-command--asjob"></a><span data-ttu-id="0d373-165">步驟1：調用-命令-ASJOB</span><span class="sxs-lookup"><span data-stu-id="0d373-165">STEP 1: INVOKE-COMMAND -ASJOB</span></span>

<span data-ttu-id="0d373-166">下列命令使用 Invoke-Command 的 AsJob 參數，在 Server01 電腦上啟動背景工作。</span><span class="sxs-lookup"><span data-stu-id="0d373-166">The following command uses the AsJob parameter of Invoke-Command to start a background job on the Server01 computer.</span></span> <span data-ttu-id="0d373-167">此工作會執行取得系統記錄檔中之事件的 Get-Eventlog 命令。</span><span class="sxs-lookup"><span data-stu-id="0d373-167">The job runs a Get-Eventlog command that gets the events in the System log.</span></span> <span data-ttu-id="0d373-168">您可以使用 JobName 參數來指派作業的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="0d373-168">You can use the JobName parameter to assign a display name to the job.</span></span>

```powershell
invoke-command -computername Server01 -scriptblock {
  get-eventlog system} -asjob
```

<span data-ttu-id="0d373-169">命令的結果類似下列範例輸出。</span><span class="sxs-lookup"><span data-stu-id="0d373-169">The results of the command resemble the following sample output.</span></span>

```Output
SessionId   Name   State    HasMoreData   Location   Command
---------   ----   -----    -----------   --------   -------
1           Job1   Running  True          Server01   get-eventlog system
```

<span data-ttu-id="0d373-170">使用 AsJob 參數時，Invoke-Command 會傳回 Start-Job 傳回的相同工作物件類型。</span><span class="sxs-lookup"><span data-stu-id="0d373-170">When the AsJob parameter is used, Invoke-Command returns the same type of job object that Start-Job returns.</span></span> <span data-ttu-id="0d373-171">您可以將工作物件儲存在變數中，也可以使用 Get-Job 命令來取得工作。</span><span class="sxs-lookup"><span data-stu-id="0d373-171">You can save the job object in a variable, or you can use a Get-Job command to get the job.</span></span>

<span data-ttu-id="0d373-172">請注意，Location 屬性的值顯示作業已在 Server01 電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="0d373-172">Note that the value of the Location property shows that the job ran on the Server01 computer.</span></span>

#### <a name="step-2-get-job"></a><span data-ttu-id="0d373-173">步驟2：取得-作業</span><span class="sxs-lookup"><span data-stu-id="0d373-173">STEP 2: GET-JOB</span></span>

<span data-ttu-id="0d373-174">若要管理使用 Invoke-Command Cmdlet 的 AsJob 參數啟動的工作，請使用 Job Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0d373-174">To manage a job started by using the AsJob parameter of the Invoke-Command cmdlet, use the Job cmdlets.</span></span> <span data-ttu-id="0d373-175">因為代表遠端作業的工作物件是在本機電腦上，所以您不需要執行遠端命令來管理作業。</span><span class="sxs-lookup"><span data-stu-id="0d373-175">Because the job object that represents the remote job is on the local computer, you do not need to run remote commands to manage the job.</span></span>

<span data-ttu-id="0d373-176">若要判斷作業是否已完成，請使用 Get-Job 命令。</span><span class="sxs-lookup"><span data-stu-id="0d373-176">To determine whether the job is complete, use a Get-Job command.</span></span> <span data-ttu-id="0d373-177">下列命令會取得在目前會話中啟動的所有工作。</span><span class="sxs-lookup"><span data-stu-id="0d373-177">The following command gets all of the jobs that were started in the current session.</span></span>

```powershell
get-job
```

<span data-ttu-id="0d373-178">因為遠端作業是在目前會話中啟動，所以本機 Get-Job 命令會取得工作。</span><span class="sxs-lookup"><span data-stu-id="0d373-178">Because the remote job was started in the current session, a local Get-Job command gets the job.</span></span> <span data-ttu-id="0d373-179">工作物件的 State 屬性顯示命令已順利完成。</span><span class="sxs-lookup"><span data-stu-id="0d373-179">The State property of the job object shows that the command was completed successfully.</span></span>

```Output
SessionId   Name   State      HasMoreData   Location   Command
---------   ----   -----      -----------   --------   -------
1           Job1   Completed  True          Server01   get-eventlog system
```

#### <a name="step-3-receive-job"></a><span data-ttu-id="0d373-180">步驟3：接收作業</span><span class="sxs-lookup"><span data-stu-id="0d373-180">STEP 3: RECEIVE-JOB</span></span>

<span data-ttu-id="0d373-181">若要取得作業的結果，請使用 Receive-Job Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0d373-181">To get the results of the job, use the Receive-Job cmdlet.</span></span> <span data-ttu-id="0d373-182">因為工作結果會自動傳回到工作物件所在的電腦，所以您可以使用本機 Receive-Job 命令取得結果。</span><span class="sxs-lookup"><span data-stu-id="0d373-182">Because the job results are automatically returned to the computer where the job object resides, you can get the results with a local Receive-Job command.</span></span>

<span data-ttu-id="0d373-183">下列命令使用 Receive-Job Cmdlet 取得工作的結果。</span><span class="sxs-lookup"><span data-stu-id="0d373-183">The following command uses the Receive-Job cmdlet to get the results of the job.</span></span> <span data-ttu-id="0d373-184">它會使用會話識別碼來識別工作。</span><span class="sxs-lookup"><span data-stu-id="0d373-184">It uses the session ID to identify the job.</span></span> <span data-ttu-id="0d373-185">此命令會將工作結果儲存在 $results 變數中。</span><span class="sxs-lookup"><span data-stu-id="0d373-185">This command saves the job results in the $results variable.</span></span> <span data-ttu-id="0d373-186">您也可以將結果重新導向至檔案。</span><span class="sxs-lookup"><span data-stu-id="0d373-186">You can also redirect the results to a file.</span></span>

```powershell
$results = receive-job -id 1
```

### <a name="start-a-remote-job-that-keeps-the-results-on-the-remote-computer"></a><span data-ttu-id="0d373-187">啟動將結果保留在遠端電腦上的遠端作業</span><span class="sxs-lookup"><span data-stu-id="0d373-187">START A REMOTE JOB THAT KEEPS THE RESULTS ON THE REMOTE COMPUTER</span></span>

<span data-ttu-id="0d373-188">若要在遠端電腦上啟動背景工作，以在遠端電腦上保存命令結果，請使用 Invoke-Command Cmdlet 在遠端電腦上執行 Start-Job 命令。</span><span class="sxs-lookup"><span data-stu-id="0d373-188">To start a background job on a remote computer that keeps the command results on the remote computer, use the Invoke-Command cmdlet to run a Start-Job command on a remote computer.</span></span> <span data-ttu-id="0d373-189">您可以使用此方法在多部電腦上執行背景工作。</span><span class="sxs-lookup"><span data-stu-id="0d373-189">You can use this method to run background jobs on multiple computers.</span></span>

<span data-ttu-id="0d373-190">當您從遠端執行 Start-Job 命令時，會在遠端電腦上建立工作物件，並在遠端電腦上維護工作結果。</span><span class="sxs-lookup"><span data-stu-id="0d373-190">When you run a Start-Job command remotely, the job object is created on the remote computer, and the job results are maintained on the remote computer.</span></span>
<span data-ttu-id="0d373-191">從作業的觀點來看，所有作業都是本機的。</span><span class="sxs-lookup"><span data-stu-id="0d373-191">From the perspective of the job, all operations are local.</span></span> <span data-ttu-id="0d373-192">您只是在遠端執行命令來管理遠端電腦上的本機作業。</span><span class="sxs-lookup"><span data-stu-id="0d373-192">You are just running commands remotely to manage a local job on the remote computer.</span></span>

#### <a name="step-1-invoke-command-start-job"></a><span data-ttu-id="0d373-193">步驟1： INVOKE-命令啟動-作業</span><span class="sxs-lookup"><span data-stu-id="0d373-193">STEP 1: INVOKE-COMMAND START-JOB</span></span>

<span data-ttu-id="0d373-194">使用 Invoke-Command Cmdlet 在遠端電腦上執行 Start-Job 命令。</span><span class="sxs-lookup"><span data-stu-id="0d373-194">Use the Invoke-Command cmdlet to run a Start-Job command on a remote computer.</span></span>

<span data-ttu-id="0d373-195">此命令需要 PSSession (持續性連接) 。</span><span class="sxs-lookup"><span data-stu-id="0d373-195">This command requires a PSSession (a persistent connection).</span></span> <span data-ttu-id="0d373-196">如果您使用 Invoke-Command 的 ComputerName 參數來建立暫時連接，則在傳回工作物件時，Invoke-Command 命令會被視為已完成。</span><span class="sxs-lookup"><span data-stu-id="0d373-196">If you use the ComputerName parameter of Invoke-Command to establish a temporary connection, the Invoke-Command command is considered to be complete when the job object is returned.</span></span> <span data-ttu-id="0d373-197">如此一來，就會關閉暫時連接，並取消作業。</span><span class="sxs-lookup"><span data-stu-id="0d373-197">As a result, the temporary connection is closed, and the job is canceled.</span></span>

<span data-ttu-id="0d373-198">下列命令使用 New-PSSession Cmdlet 來建立連線到 Server01 電腦的 PSSession。</span><span class="sxs-lookup"><span data-stu-id="0d373-198">The following command uses the New-PSSession cmdlet to create a PSSession that is connected to the Server01 computer.</span></span> <span data-ttu-id="0d373-199">命令會將 PSSession 儲存在 \$ s 變數中。</span><span class="sxs-lookup"><span data-stu-id="0d373-199">The command saves the PSSession in the \$s variable.</span></span>

```powershell
$s = new-pssession -computername Server01
```

<span data-ttu-id="0d373-200">下一個命令會使用 Invoke-Command Cmdlet 在 PSSession 中執行 Start-Job 命令。</span><span class="sxs-lookup"><span data-stu-id="0d373-200">The next command uses the Invoke-Command cmdlet to run a Start-Job command in the PSSession.</span></span> <span data-ttu-id="0d373-201">Start-Job 命令和 Get-Eventlog 命令會以大括弧括住。</span><span class="sxs-lookup"><span data-stu-id="0d373-201">The Start-Job command and the Get-Eventlog command are enclosed in braces.</span></span>

```powershell
invoke-command -session $s -scriptblock {
  start-job -scriptblock {get-eventlog system}}
```

<span data-ttu-id="0d373-202">結果類似下列範例輸出。</span><span class="sxs-lookup"><span data-stu-id="0d373-202">The results resemble the following sample output.</span></span>

```Output
Id       Name    State      HasMoreData     Location   Command
--       ----    -----      -----------     --------   -------
2        Job2    Running    True            Localhost  get-eventlog system
```

<span data-ttu-id="0d373-203">當您從遠端執行 Start-Job 命令時，Invoke-Command 會傳回 Start-Job 傳回的相同工作物件類型。</span><span class="sxs-lookup"><span data-stu-id="0d373-203">When you run a Start-Job command remotely, Invoke-Command returns the same type of job object that Start-Job returns.</span></span> <span data-ttu-id="0d373-204">您可以將工作物件儲存在變數中，也可以使用 Get-Job 命令來取得工作。</span><span class="sxs-lookup"><span data-stu-id="0d373-204">You can save the job object in a variable, or you can use a Get-Job command to get the job.</span></span>

<span data-ttu-id="0d373-205">請注意，[位置] 屬性的值會顯示在本機電腦上執行的作業（稱為 "LocalHost"），即使作業在 Server01 電腦上執行也一樣。</span><span class="sxs-lookup"><span data-stu-id="0d373-205">Note that the value of the Location property shows that the job ran on the local computer, known as "LocalHost", even though the job ran on the Server01 computer.</span></span> <span data-ttu-id="0d373-206">由於工作物件是在 Server01 電腦上建立的，而且工作會在同一部電腦上執行，因此會被視為本機背景工作。</span><span class="sxs-lookup"><span data-stu-id="0d373-206">Because the job object is created on the Server01 computer and the job runs on the same computer, it is considered to be a local background job.</span></span>

#### <a name="step-2-invoke-command-get-job"></a><span data-ttu-id="0d373-207">步驟2：叫用-命令 GET-JOB</span><span class="sxs-lookup"><span data-stu-id="0d373-207">STEP 2: INVOKE-COMMAND GET-JOB</span></span>

<span data-ttu-id="0d373-208">若要管理遠端背景工作，請使用 Job Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0d373-208">To manage a remote background job, use the Job cmdlets.</span></span> <span data-ttu-id="0d373-209">因為工作物件是在遠端電腦上，所以您需要執行遠端命令以取得、停止、等候或取出工作結果。</span><span class="sxs-lookup"><span data-stu-id="0d373-209">Because the job object is on the remote computer, you need to run remote commands to get, stop, wait for, or retrieve the job results.</span></span>

<span data-ttu-id="0d373-210">若要查看作業是否已完成，請使用 Invoke-Command 命令，在連線到 Server01 電腦的 PSSession 中執行 Get-Job 命令。</span><span class="sxs-lookup"><span data-stu-id="0d373-210">To see if the job is complete, use an Invoke-Command command to run a Get-Job command in the PSSession that is connected to the Server01 computer.</span></span>

```powershell
invoke-command -session $s -scriptblock {get-job}
```

<span data-ttu-id="0d373-211">命令會傳回工作物件。</span><span class="sxs-lookup"><span data-stu-id="0d373-211">The command returns a job object.</span></span> <span data-ttu-id="0d373-212">工作物件的 State 屬性顯示命令已順利完成。</span><span class="sxs-lookup"><span data-stu-id="0d373-212">The State property of the job object shows that the command was completed successfully.</span></span>

```Output
SessionId   Name  State      HasMoreData   Location   Command
---------   ----  -----      -----------   --------   -------
2           Job2  Completed  True          LocalHost   get-eventlog system
```

#### <a name="step-3-invoke-command-receive-job"></a><span data-ttu-id="0d373-213">步驟3：調用-命令接收-作業</span><span class="sxs-lookup"><span data-stu-id="0d373-213">STEP 3: INVOKE-COMMAND RECEIVE-JOB</span></span>

<span data-ttu-id="0d373-214">若要取得工作的結果，請使用 Invoke-Command Cmdlet，在連線到 Server01 電腦的 PSSession 中執行 Receive-Job 命令。</span><span class="sxs-lookup"><span data-stu-id="0d373-214">To get the results of the job, use the Invoke-Command cmdlet to run a Receive-Job command in the PSSession that is connected to the Server01 computer.</span></span>

<span data-ttu-id="0d373-215">下列命令使用 Receive-Job Cmdlet 取得工作的結果。</span><span class="sxs-lookup"><span data-stu-id="0d373-215">The following command uses the Receive-Job cmdlet to get the results of the job.</span></span> <span data-ttu-id="0d373-216">它會使用會話識別碼來識別工作。</span><span class="sxs-lookup"><span data-stu-id="0d373-216">It uses the session ID to identify the job.</span></span> <span data-ttu-id="0d373-217">此命令會將工作結果儲存在 \$ 結果變數中。</span><span class="sxs-lookup"><span data-stu-id="0d373-217">This command saves the job results in the \$results variable.</span></span> <span data-ttu-id="0d373-218">它使用 Receive-Job 的 Keep 參數，將結果保留在遠端電腦上的工作快取中。</span><span class="sxs-lookup"><span data-stu-id="0d373-218">It uses the Keep parameter of Receive-Job to keep the result in the job cache on the remote computer.</span></span>

```powershell
$results = invoke-command -session $s -scriptblock {
  receive-job -sessionid 2 -keep}
```

<span data-ttu-id="0d373-219">您也可以將結果重新導向至本機或遠端電腦上的檔案。</span><span class="sxs-lookup"><span data-stu-id="0d373-219">You can also redirect the results to a file on the local or remote computer.</span></span>
<span data-ttu-id="0d373-220">下列命令會使用重新導向運算子，將結果儲存在 Server01 電腦上的檔案中。</span><span class="sxs-lookup"><span data-stu-id="0d373-220">The following command uses a redirection operator to save the results in a file on the Server01 computer.</span></span>

```powershell
invoke-command -session $s -command {
  receive-job -sessionid 2 > c:\logs\pslog.txt}
```

## <a name="see-also"></a><span data-ttu-id="0d373-221">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d373-221">SEE ALSO</span></span>

[<span data-ttu-id="0d373-222">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="0d373-222">about_Jobs</span></span>](about_Jobs.md)

[<span data-ttu-id="0d373-223">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="0d373-223">about_Job_Details</span></span>](about_Job_Details.md)

[<span data-ttu-id="0d373-224">about_Remote</span><span class="sxs-lookup"><span data-stu-id="0d373-224">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="0d373-225">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="0d373-225">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="0d373-226">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="0d373-226">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="0d373-227">Start-Job</span><span class="sxs-lookup"><span data-stu-id="0d373-227">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)

[<span data-ttu-id="0d373-228">Get-Job</span><span class="sxs-lookup"><span data-stu-id="0d373-228">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)

[<span data-ttu-id="0d373-229">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="0d373-229">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)

[<span data-ttu-id="0d373-230">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="0d373-230">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)

[<span data-ttu-id="0d373-231">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="0d373-231">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)

[<span data-ttu-id="0d373-232">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="0d373-232">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

[<span data-ttu-id="0d373-233">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="0d373-233">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="0d373-234">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="0d373-234">Exit-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Exit-PSSession)
