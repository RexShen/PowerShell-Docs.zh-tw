---
ms.date: 09/13/2016
ms.topic: reference
title: 背景作業
description: 背景作業
ms.openlocfilehash: 5478789a2ee1f2eabc71a46673e3a707643cdba8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648622"
---
# <a name="background-jobs"></a><span data-ttu-id="d0c6a-103">背景作業</span><span class="sxs-lookup"><span data-stu-id="d0c6a-103">Background Jobs</span></span>

<span data-ttu-id="d0c6a-104">Cmdlet 可以在內部執行其動作，或做為 Windows PowerShell 的 *背景工作*。</span><span class="sxs-lookup"><span data-stu-id="d0c6a-104">Cmdlets can perform their action internally or as a Windows PowerShell *background job*.</span></span> <span data-ttu-id="d0c6a-105">當 Cmdlet 以背景工作的形式執行時，工作會在自己的執行緒中以非同步方式完成，並與 Cmdlet 所使用的管線執行緒分開。</span><span class="sxs-lookup"><span data-stu-id="d0c6a-105">When a cmdlet runs as a background job, the work is done asynchronously in its own thread separate from the pipeline thread that the cmdlet is using.</span></span> <span data-ttu-id="d0c6a-106">從使用者的觀點來看，當 Cmdlet 以背景工作的形式執行時，即使作業需要相當長的時間才能完成，命令提示字元也會立即傳回，而且使用者可以在作業執行時繼續進行而不會中斷。</span><span class="sxs-lookup"><span data-stu-id="d0c6a-106">From the user perspective, when a cmdlet runs as a background job, the command prompt returns immediately even if the job takes an extended amount of time to complete, and the user can continue without interruption while the job runs.</span></span>

## <a name="background-jobs-child-jobs-and-the-job-repository"></a><span data-ttu-id="d0c6a-107">背景工作、子工作和作業儲存機制</span><span class="sxs-lookup"><span data-stu-id="d0c6a-107">Background Jobs, Child Jobs, and the Job Repository</span></span>

<span data-ttu-id="d0c6a-108">支援背景工作的 Cmdlet 所傳回的工作物件會定義工作。</span><span class="sxs-lookup"><span data-stu-id="d0c6a-108">The job object that is returned by the cmdlets that support background jobs defines the job.</span></span> <span data-ttu-id="d0c6a-109"> ([啟動工作](/powershell/module/Microsoft.PowerShell.Core/Start-Job) Cmdlet 也會傳回工作物件。 ) 作業的名稱、用來指定作業的識別碼、狀態資訊和子工作都包含在此定義中。</span><span class="sxs-lookup"><span data-stu-id="d0c6a-109">(The [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet also returns a job object.) The name of the job, an identifier that is used to specify the job, the state information, and the child jobs are included in this definition.</span></span> <span data-ttu-id="d0c6a-110">作業不會執行任何工作。</span><span class="sxs-lookup"><span data-stu-id="d0c6a-110">The job does not perform any of the work.</span></span> <span data-ttu-id="d0c6a-111">每個背景工作都至少有一個子工作，因為子工作會執行實際的工作。</span><span class="sxs-lookup"><span data-stu-id="d0c6a-111">Each background job has at least one child job because the child job performs the actual work.</span></span> <span data-ttu-id="d0c6a-112">當您執行 Cmdlet 讓工作以背景工作的形式執行時，此 Cmdlet 必須將作業和子工作新增至一般儲存機制，稱為「 *作業存放庫*」。</span><span class="sxs-lookup"><span data-stu-id="d0c6a-112">When you run a cmdlet so that the work is performed as a background job, the cmdlet must add the job and the child jobs to a common repository, referred to as the *job repository*.</span></span>

<span data-ttu-id="d0c6a-113">如需有關如何在命令列處理背景工作的詳細資訊，請參閱下列各項：</span><span class="sxs-lookup"><span data-stu-id="d0c6a-113">For more information about how background jobs are handled at the command line, see the following:</span></span>

- [<span data-ttu-id="d0c6a-114">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="d0c6a-114">about_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [<span data-ttu-id="d0c6a-115">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="d0c6a-115">about_Job_Details</span></span>](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [<span data-ttu-id="d0c6a-116">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="d0c6a-116">about_Remote_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a><span data-ttu-id="d0c6a-117">撰寫以背景工作方式執行的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d0c6a-117">Writing a Cmdlet That Runs as a Background Job</span></span>

<span data-ttu-id="d0c6a-118">若要撰寫可作為背景工作執行的 Cmdlet，您必須完成下列工作：</span><span class="sxs-lookup"><span data-stu-id="d0c6a-118">To write a cmdlet that can be run as a background job, you must complete the following tasks:</span></span>

- <span data-ttu-id="d0c6a-119">定義 `asJob` 切換參數，讓使用者可以決定是否要以背景工作的方式執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d0c6a-119">Define an `asJob` switch parameter so that the user can decide whether to run the cmdlet as a background job.</span></span>

- <span data-ttu-id="d0c6a-120">建立一個衍生自[system.string 類別的物件。](/dotnet/api/System.Management.Automation.Job)</span><span class="sxs-lookup"><span data-stu-id="d0c6a-120">Create an object that derives from the [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) class.</span></span> <span data-ttu-id="d0c6a-121">這個物件可以是自訂工作物件或 Windows PowerShell 提供的工作物件，例如 [Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) 物件。</span><span class="sxs-lookup"><span data-stu-id="d0c6a-121">This object can be a custom job object or a job object provided by Windows PowerShell, such as a [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) object.</span></span>

- <span data-ttu-id="d0c6a-122">在記錄處理方法中，新增可 `if` 偵測 Cmdlet 是否應以背景工作的方式執行的語句。</span><span class="sxs-lookup"><span data-stu-id="d0c6a-122">In a record processing method, add an `if` statement that detects whether the cmdlet should run as a background job.</span></span>

- <span data-ttu-id="d0c6a-123">若為自訂工作物件，請執行 job 類別。</span><span class="sxs-lookup"><span data-stu-id="d0c6a-123">For custom job objects, implement the job class.</span></span>

- <span data-ttu-id="d0c6a-124">根據 Cmdlet 是否以背景工作的形式執行，傳回適當的物件。</span><span class="sxs-lookup"><span data-stu-id="d0c6a-124">Return the appropriate objects, depending on whether the cmdlet is run as a background job.</span></span>

<span data-ttu-id="d0c6a-125">如需程式碼範例，請參閱 [如何支援工作](./how-to-support-jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="d0c6a-125">For a code example, see [How to Support Jobs](./how-to-support-jobs.md).</span></span>

## <a name="background-job-related-apis"></a><span data-ttu-id="d0c6a-126">背景 Job-Related Api</span><span class="sxs-lookup"><span data-stu-id="d0c6a-126">Background Job-Related APIs</span></span>

<span data-ttu-id="d0c6a-127">下列 Api 是由 Windows PowerShell 提供來管理背景工作。</span><span class="sxs-lookup"><span data-stu-id="d0c6a-127">The following APIs are provided by Windows PowerShell to manage background jobs.</span></span>

<span data-ttu-id="d0c6a-128">[系統管理作業](/dotnet/api/System.Management.Automation.Job) 會衍生自訂工作物件。</span><span class="sxs-lookup"><span data-stu-id="d0c6a-128">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) Derives custom job objects.</span></span> <span data-ttu-id="d0c6a-129">這是 abstract 類別。</span><span class="sxs-lookup"><span data-stu-id="d0c6a-129">This is an abstract class.</span></span>

<span data-ttu-id="d0c6a-130">[Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) 會管理和提供有關目前作用中背景工作的資訊。</span><span class="sxs-lookup"><span data-stu-id="d0c6a-130">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) Manages and provides information about the current active background jobs.</span></span>

<span data-ttu-id="d0c6a-131">[Jobstate](/dotnet/api/System.Management.Automation.JobState) 會定義背景工作的狀態。</span><span class="sxs-lookup"><span data-stu-id="d0c6a-131">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) Defines the state of the background job.</span></span> <span data-ttu-id="d0c6a-132">狀態包括 [已啟動]、[正在執行] 和 [已停止]。</span><span class="sxs-lookup"><span data-stu-id="d0c6a-132">States include Started, Running, and Stopped.</span></span>

<span data-ttu-id="d0c6a-133">[Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) 會提供背景工作狀態的相關資訊，而且如果上次狀態變更是由錯誤所造成，則工作會進入其目前的狀態。</span><span class="sxs-lookup"><span data-stu-id="d0c6a-133">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) Provides information about the state of a background job and, if the last state change was caused by an error, the reason the job entered its current state.</span></span>

<span data-ttu-id="d0c6a-134">[Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) 會提供背景工作變更狀態時引發之事件的引數。</span><span class="sxs-lookup"><span data-stu-id="d0c6a-134">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) Provides the arguments for an event that is raised when a background job changes state.</span></span>

## <a name="windows-powershell-job-cmdlets"></a><span data-ttu-id="d0c6a-135">Windows PowerShell 作業 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d0c6a-135">Windows PowerShell Job Cmdlets</span></span>

<span data-ttu-id="d0c6a-136">下列 Cmdlet 是由 Windows PowerShell 提供來管理背景工作。</span><span class="sxs-lookup"><span data-stu-id="d0c6a-136">The following cmdlets are provided by Windows PowerShell to manage background jobs.</span></span>

[<span data-ttu-id="d0c6a-137">Get-Job</span><span class="sxs-lookup"><span data-stu-id="d0c6a-137">Get-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

<span data-ttu-id="d0c6a-138">取得正在目前工作階段中執行的 Windows PowerShell 背景工作。</span><span class="sxs-lookup"><span data-stu-id="d0c6a-138">Gets Windows PowerShell background jobs that are running in the current session.</span></span>

[<span data-ttu-id="d0c6a-139">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="d0c6a-139">Receive-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

<span data-ttu-id="d0c6a-140">取得目前工作階段中 Windows PowerShell 背景工作的結果。</span><span class="sxs-lookup"><span data-stu-id="d0c6a-140">Gets the results of the Windows PowerShell background jobs in the current session.</span></span>

[<span data-ttu-id="d0c6a-141">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="d0c6a-141">Remove-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

<span data-ttu-id="d0c6a-142">刪除 Windows PowerShell 背景工作。</span><span class="sxs-lookup"><span data-stu-id="d0c6a-142">Deletes a Windows PowerShell background job.</span></span>

[<span data-ttu-id="d0c6a-143">Start-Job</span><span class="sxs-lookup"><span data-stu-id="d0c6a-143">Start-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

<span data-ttu-id="d0c6a-144">啟動 Windows PowerShell 背景工作。</span><span class="sxs-lookup"><span data-stu-id="d0c6a-144">Starts a Windows PowerShell background job.</span></span>

[<span data-ttu-id="d0c6a-145">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="d0c6a-145">Stop-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

<span data-ttu-id="d0c6a-146">停止 Windows PowerShell 背景工作。</span><span class="sxs-lookup"><span data-stu-id="d0c6a-146">Stops a Windows PowerShell background job.</span></span>

[<span data-ttu-id="d0c6a-147">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="d0c6a-147">Wait-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

<span data-ttu-id="d0c6a-148">抑制命令提示字元，直到工作階段中正在執行的其中一個或所有 Windows PowerShell 背景工作完成為止。</span><span class="sxs-lookup"><span data-stu-id="d0c6a-148">Suppresses the command prompt until one or all of the Windows PowerShell background jobs running in the session are complete.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0c6a-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0c6a-149">See Also</span></span>

[<span data-ttu-id="d0c6a-150">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d0c6a-150">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
