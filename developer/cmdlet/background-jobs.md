---
title: 背景工作 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0ef5ac9-8254-4832-ace8-84b356c10f08
caps.latest.revision: 13
ms.openlocfilehash: ff4fe159eedc47fc69f4d783cd90d2b0e888c0d5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068671"
---
# <a name="background-jobs"></a><span data-ttu-id="f70aa-102">背景作業</span><span class="sxs-lookup"><span data-stu-id="f70aa-102">Background Jobs</span></span>

<span data-ttu-id="f70aa-103">在內部或 Windows powershell Cmdlet 可以執行其動作*背景工作*。</span><span class="sxs-lookup"><span data-stu-id="f70aa-103">Cmdlets can perform their action internally or as a Windows PowerShell*background job*.</span></span> <span data-ttu-id="f70aa-104">當 cmdlet 執行背景工作時，工作會在其自己的執行緒不同於 cmdlet 正在使用的管線執行緒以非同步方式完成。</span><span class="sxs-lookup"><span data-stu-id="f70aa-104">When a cmdlet runs as a background job, the work is done asynchronously in its own thread separate from the pipeline thread that the cmdlet is using.</span></span> <span data-ttu-id="f70aa-105">從使用者觀點來看，當指令程式會執行為背景工作，命令提示字元會立即傳回即使工作需要長時間才能完成，且使用者可以繼續使用不中斷工作執行時。</span><span class="sxs-lookup"><span data-stu-id="f70aa-105">From the user perspective, when a cmdlet runs as a background job, the command prompt returns immediately even if the job takes an extended amount of time to complete, and the user can continue without interruption while the job runs.</span></span>

## <a name="background-jobs-child-jobs-and-the-job-repository"></a><span data-ttu-id="f70aa-106">背景工作、 子工作與工作存放庫</span><span class="sxs-lookup"><span data-stu-id="f70aa-106">Background Jobs, Child Jobs, and the Job Repository</span></span>

<span data-ttu-id="f70aa-107">支援背景工作的 cmdlet 所傳回工作物件會定義工作。</span><span class="sxs-lookup"><span data-stu-id="f70aa-107">The job object that is returned by the cmdlets that support background jobs defines the job.</span></span> <span data-ttu-id="f70aa-108">( [Start-job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet 也會傳回工作物件。)在此定義包含作業，用來指定工作、 狀態資訊和子工作的識別項的名稱。</span><span class="sxs-lookup"><span data-stu-id="f70aa-108">(The [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet also returns a job object.) The name of the job, an identifier that is used to specify the job, the state information, and the child jobs are included in this definition.</span></span> <span data-ttu-id="f70aa-109">作業不會執行任何工作。</span><span class="sxs-lookup"><span data-stu-id="f70aa-109">The job does not perform any of the work.</span></span> <span data-ttu-id="f70aa-110">每個背景工作有至少一個子工作，因為子工作會執行實際工作。</span><span class="sxs-lookup"><span data-stu-id="f70aa-110">Each background job has at least one child job because the child job performs the actual work.</span></span> <span data-ttu-id="f70aa-111">指令程式時，讓背景工作執行的工作，您可以執行 cmdlet，必須將工作與子工作，加入通用儲存機制，稱為*工作存放庫*。</span><span class="sxs-lookup"><span data-stu-id="f70aa-111">When you run a cmdlet so that the work is performed as a background job, the cmdlet must add the job and the child jobs to a common repository, referred to as the *job repository*.</span></span>

<span data-ttu-id="f70aa-112">如需有關如何在命令列處理背景工作的詳細資訊，請參閱下列各項：</span><span class="sxs-lookup"><span data-stu-id="f70aa-112">For more information about how background jobs are handled at the command line, see the following:</span></span>

- [<span data-ttu-id="f70aa-113">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="f70aa-113">about_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [<span data-ttu-id="f70aa-114">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="f70aa-114">about_Job_Details</span></span>](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [<span data-ttu-id="f70aa-115">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="f70aa-115">about_Remote_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a><span data-ttu-id="f70aa-116">撰寫以背景工作執行的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f70aa-116">Writing a Cmdlet That Runs as a Background Job</span></span>

<span data-ttu-id="f70aa-117">若要撰寫的 cmdlet，可以執行為背景工作，您必須完成下列工作：</span><span class="sxs-lookup"><span data-stu-id="f70aa-117">To write a cmdlet that can be run as a background job, you must complete the following tasks:</span></span>

- <span data-ttu-id="f70aa-118">定義`asJob`切換參數，以便使用者可以決定是否要以背景工作方式執行 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f70aa-118">Define an `asJob` switch parameter so that the user can decide whether to run the cmdlet as a background job.</span></span>

- <span data-ttu-id="f70aa-119">建立物件衍生自[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job)類別。</span><span class="sxs-lookup"><span data-stu-id="f70aa-119">Create an object that derives from the [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) class.</span></span> <span data-ttu-id="f70aa-120">這個物件可以是自訂的工作物件或工作物件，提供 Windows powershell，例如[System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob)物件。</span><span class="sxs-lookup"><span data-stu-id="f70aa-120">This object can be a custom job object or a job object provided by Windows PowerShell, such as a [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) object.</span></span>

- <span data-ttu-id="f70aa-121">在記錄處理方法中，新增`if`會偵測是否應該以背景工作執行 cmdlet 的陳述式。</span><span class="sxs-lookup"><span data-stu-id="f70aa-121">In a record processing method, add an `if` statement that detects whether the cmdlet should run as a background job.</span></span>

- <span data-ttu-id="f70aa-122">自訂的工作物件，實作作業的類別。</span><span class="sxs-lookup"><span data-stu-id="f70aa-122">For custom job objects, implement the job class.</span></span>

- <span data-ttu-id="f70aa-123">傳回適當的物件，取決於是否執行背景工作的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f70aa-123">Return the appropriate objects, depending on whether the cmdlet is run as a background job.</span></span>

<span data-ttu-id="f70aa-124">如需程式碼範例，請參閱 <<c0> [ 如何支援工作](./how-to-support-jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="f70aa-124">For a code example, see [How to Support Jobs](./how-to-support-jobs.md).</span></span>

## <a name="background-job-related-apis"></a><span data-ttu-id="f70aa-125">背景工作相關的 Api</span><span class="sxs-lookup"><span data-stu-id="f70aa-125">Background Job-Related APIs</span></span>

<span data-ttu-id="f70aa-126">下列 Api 會提供 Windows PowerShell 來管理背景工作。</span><span class="sxs-lookup"><span data-stu-id="f70aa-126">The following APIs are provided by Windows PowerShell to manage background jobs.</span></span>

<span data-ttu-id="f70aa-127">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job)衍生自訂的工作物件。</span><span class="sxs-lookup"><span data-stu-id="f70aa-127">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) Derives custom job objects.</span></span> <span data-ttu-id="f70aa-128">這是抽象類別。</span><span class="sxs-lookup"><span data-stu-id="f70aa-128">This is an abstract class.</span></span>

<span data-ttu-id="f70aa-129">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository)管理，並提供目前的作用中的背景工作的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f70aa-129">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) Manages and provides information about the current active background jobs.</span></span>

<span data-ttu-id="f70aa-130">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState)定義背景作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="f70aa-130">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) Defines the state of the background job.</span></span> <span data-ttu-id="f70aa-131">狀態包括啟動、 執行，且已停止。</span><span class="sxs-lookup"><span data-stu-id="f70aa-131">States include Started, Running, and Stopped.</span></span>

<span data-ttu-id="f70aa-132">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo)提供背景工作的狀態相關資訊，以及如果上次狀態變更，因發生錯誤時，工作進入其目前狀態的原因。</span><span class="sxs-lookup"><span data-stu-id="f70aa-132">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) Provides information about the state of a background job and, if the last state change was caused by an error, the reason the job entered its current state.</span></span>

<span data-ttu-id="f70aa-133">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs)提供背景工作變更狀態時引發事件的引數。</span><span class="sxs-lookup"><span data-stu-id="f70aa-133">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) Provides the arguments for an event that is raised when a background job changes state.</span></span>

## <a name="windows-powershell-job-cmdlets"></a><span data-ttu-id="f70aa-134">Windows PowerShell 工作 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f70aa-134">Windows PowerShell Job Cmdlets</span></span>

<span data-ttu-id="f70aa-135">下列指令程式會提供 Windows PowerShell 來管理背景工作。</span><span class="sxs-lookup"><span data-stu-id="f70aa-135">The following cmdlets are provided by Windows PowerShell to manage background jobs.</span></span>

[<span data-ttu-id="f70aa-136">Get-Job</span><span class="sxs-lookup"><span data-stu-id="f70aa-136">Get-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

<span data-ttu-id="f70aa-137">取得正在目前工作階段中執行的 Windows PowerShell 背景工作。</span><span class="sxs-lookup"><span data-stu-id="f70aa-137">Gets Windows PowerShell background jobs that are running in the current session.</span></span>

[<span data-ttu-id="f70aa-138">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="f70aa-138">Receive-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

<span data-ttu-id="f70aa-139">取得目前工作階段中 Windows PowerShell 背景工作的結果。</span><span class="sxs-lookup"><span data-stu-id="f70aa-139">Gets the results of the Windows PowerShell background jobs in the current session.</span></span>

[<span data-ttu-id="f70aa-140">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="f70aa-140">Remove-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

<span data-ttu-id="f70aa-141">刪除 Windows PowerShell 背景工作。</span><span class="sxs-lookup"><span data-stu-id="f70aa-141">Deletes a Windows PowerShell background job.</span></span>

[<span data-ttu-id="f70aa-142">Start-Job</span><span class="sxs-lookup"><span data-stu-id="f70aa-142">Start-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

<span data-ttu-id="f70aa-143">啟動 Windows PowerShell 背景工作。</span><span class="sxs-lookup"><span data-stu-id="f70aa-143">Starts a Windows PowerShell background job.</span></span>

[<span data-ttu-id="f70aa-144">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="f70aa-144">Stop-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

<span data-ttu-id="f70aa-145">停止 Windows PowerShell 背景工作。</span><span class="sxs-lookup"><span data-stu-id="f70aa-145">Stops a Windows PowerShell background job.</span></span>

[<span data-ttu-id="f70aa-146">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="f70aa-146">Wait-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

<span data-ttu-id="f70aa-147">抑制命令提示字元，直到工作階段中正在執行的其中一個或所有 Windows PowerShell 背景工作完成為止。</span><span class="sxs-lookup"><span data-stu-id="f70aa-147">Suppresses the command prompt until one or all of the Windows PowerShell background jobs running in the session are complete.</span></span>

## <a name="see-also"></a><span data-ttu-id="f70aa-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f70aa-148">See Also</span></span>

[<span data-ttu-id="f70aa-149">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f70aa-149">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
