---
title: 背景作業 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0ef5ac9-8254-4832-ace8-84b356c10f08
caps.latest.revision: 13
ms.openlocfilehash: ff4fe159eedc47fc69f4d783cd90d2b0e888c0d5
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363557"
---
# <a name="background-jobs"></a><span data-ttu-id="688d4-102">背景作業</span><span class="sxs-lookup"><span data-stu-id="688d4-102">Background Jobs</span></span>

<span data-ttu-id="688d4-103">Cmdlet 可以在內部或 Windows PowerShell*背景工作*執行其動作。</span><span class="sxs-lookup"><span data-stu-id="688d4-103">Cmdlets can perform their action internally or as a Windows PowerShell*background job*.</span></span> <span data-ttu-id="688d4-104">當 Cmdlet 以背景工作的形式執行時，工作會以非同步方式在自己的執行緒中完成，並與 Cmdlet 所使用的管線執行緒分開。</span><span class="sxs-lookup"><span data-stu-id="688d4-104">When a cmdlet runs as a background job, the work is done asynchronously in its own thread separate from the pipeline thread that the cmdlet is using.</span></span> <span data-ttu-id="688d4-105">從使用者的觀點來看，當 Cmdlet 以背景工作的形式執行時，即使工作需要相當長的時間才能完成，命令提示字元還是會立即傳回，而且當作業執行時，使用者可以繼續執行而不中斷。</span><span class="sxs-lookup"><span data-stu-id="688d4-105">From the user perspective, when a cmdlet runs as a background job, the command prompt returns immediately even if the job takes an extended amount of time to complete, and the user can continue without interruption while the job runs.</span></span>

## <a name="background-jobs-child-jobs-and-the-job-repository"></a><span data-ttu-id="688d4-106">背景工作、子作業和作業存放庫</span><span class="sxs-lookup"><span data-stu-id="688d4-106">Background Jobs, Child Jobs, and the Job Repository</span></span>

<span data-ttu-id="688d4-107">支援背景工作的 Cmdlet 所傳回的工作物件會定義作業。</span><span class="sxs-lookup"><span data-stu-id="688d4-107">The job object that is returned by the cmdlets that support background jobs defines the job.</span></span> <span data-ttu-id="688d4-108">（[啟動作業](/powershell/module/Microsoft.PowerShell.Core/Start-Job)Cmdlet 也會傳回工作物件）。作業的名稱、用來指定作業的識別碼、狀態資訊和子工作都會包含在此定義中。</span><span class="sxs-lookup"><span data-stu-id="688d4-108">(The [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet also returns a job object.) The name of the job, an identifier that is used to specify the job, the state information, and the child jobs are included in this definition.</span></span> <span data-ttu-id="688d4-109">作業不會執行任何工作。</span><span class="sxs-lookup"><span data-stu-id="688d4-109">The job does not perform any of the work.</span></span> <span data-ttu-id="688d4-110">每個背景工作都至少有一個子工作，因為子作業會執行實際的工作。</span><span class="sxs-lookup"><span data-stu-id="688d4-110">Each background job has at least one child job because the child job performs the actual work.</span></span> <span data-ttu-id="688d4-111">當您執行 Cmdlet，讓工作以背景工作的形式執行時，此 Cmdlet 必須將作業和子作業新增至通用存放庫，稱為「*作業存放庫*」。</span><span class="sxs-lookup"><span data-stu-id="688d4-111">When you run a cmdlet so that the work is performed as a background job, the cmdlet must add the job and the child jobs to a common repository, referred to as the *job repository*.</span></span>

<span data-ttu-id="688d4-112">如需如何在命令列處理背景工作的詳細資訊，請參閱下列各項：</span><span class="sxs-lookup"><span data-stu-id="688d4-112">For more information about how background jobs are handled at the command line, see the following:</span></span>

- [<span data-ttu-id="688d4-113">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="688d4-113">about_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [<span data-ttu-id="688d4-114">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="688d4-114">about_Job_Details</span></span>](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [<span data-ttu-id="688d4-115">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="688d4-115">about_Remote_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a><span data-ttu-id="688d4-116">撰寫以背景工作方式執行的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="688d4-116">Writing a Cmdlet That Runs as a Background Job</span></span>

<span data-ttu-id="688d4-117">若要撰寫可當做背景工作執行的 Cmdlet，您必須完成下列工作：</span><span class="sxs-lookup"><span data-stu-id="688d4-117">To write a cmdlet that can be run as a background job, you must complete the following tasks:</span></span>

- <span data-ttu-id="688d4-118">定義 `asJob` 切換參數，讓使用者可以決定是否要以背景工作的方式執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="688d4-118">Define an `asJob` switch parameter so that the user can decide whether to run the cmdlet as a background job.</span></span>

- <span data-ttu-id="688d4-119">建立一個衍生自[system.web](/dotnet/api/System.Management.Automation.Job)類別的物件。</span><span class="sxs-lookup"><span data-stu-id="688d4-119">Create an object that derives from the [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) class.</span></span> <span data-ttu-id="688d4-120">這個物件可以是自訂工作物件或 Windows PowerShell 所提供的工作物件，例如[Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob)物件。</span><span class="sxs-lookup"><span data-stu-id="688d4-120">This object can be a custom job object or a job object provided by Windows PowerShell, such as a [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) object.</span></span>

- <span data-ttu-id="688d4-121">在記錄處理方法中，加入 `if` 語句，以偵測是否應該以背景工作的方式執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="688d4-121">In a record processing method, add an `if` statement that detects whether the cmdlet should run as a background job.</span></span>

- <span data-ttu-id="688d4-122">若為自訂工作物件，請執行 job 類別。</span><span class="sxs-lookup"><span data-stu-id="688d4-122">For custom job objects, implement the job class.</span></span>

- <span data-ttu-id="688d4-123">根據 Cmdlet 是否以背景工作的方式執行，傳回適當的物件。</span><span class="sxs-lookup"><span data-stu-id="688d4-123">Return the appropriate objects, depending on whether the cmdlet is run as a background job.</span></span>

<span data-ttu-id="688d4-124">如需程式碼範例，請參閱[如何支援作業](./how-to-support-jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="688d4-124">For a code example, see [How to Support Jobs](./how-to-support-jobs.md).</span></span>

## <a name="background-job-related-apis"></a><span data-ttu-id="688d4-125">背景作業相關的 Api</span><span class="sxs-lookup"><span data-stu-id="688d4-125">Background Job-Related APIs</span></span>

<span data-ttu-id="688d4-126">Windows PowerShell 會提供下列 Api 來管理背景工作。</span><span class="sxs-lookup"><span data-stu-id="688d4-126">The following APIs are provided by Windows PowerShell to manage background jobs.</span></span>

<span data-ttu-id="688d4-127">[System.web](/dotnet/api/System.Management.Automation.Job)會衍生自訂工作物件。</span><span class="sxs-lookup"><span data-stu-id="688d4-127">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) Derives custom job objects.</span></span> <span data-ttu-id="688d4-128">這是抽象類別。</span><span class="sxs-lookup"><span data-stu-id="688d4-128">This is an abstract class.</span></span>

<span data-ttu-id="688d4-129">[Jobrepository](/dotnet/api/System.Management.Automation.JobRepository)會管理並提供目前作用中背景工作的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="688d4-129">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) Manages and provides information about the current active background jobs.</span></span>

<span data-ttu-id="688d4-130">[Jobstate](/dotnet/api/System.Management.Automation.JobState)會定義背景作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="688d4-130">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) Defines the state of the background job.</span></span> <span data-ttu-id="688d4-131">狀態包括 [已啟動]、[執行中] 和 [已停止]。</span><span class="sxs-lookup"><span data-stu-id="688d4-131">States include Started, Running, and Stopped.</span></span>

<span data-ttu-id="688d4-132">[Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo)提供背景工作狀態的相關資訊，而且如果上次狀態變更是由錯誤所造成，則作業會進入其目前狀態的原因。</span><span class="sxs-lookup"><span data-stu-id="688d4-132">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) Provides information about the state of a background job and, if the last state change was caused by an error, the reason the job entered its current state.</span></span>

<span data-ttu-id="688d4-133">[Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs)提供背景工作變更狀態時所引發事件的引數。</span><span class="sxs-lookup"><span data-stu-id="688d4-133">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) Provides the arguments for an event that is raised when a background job changes state.</span></span>

## <a name="windows-powershell-job-cmdlets"></a><span data-ttu-id="688d4-134">Windows PowerShell 作業 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="688d4-134">Windows PowerShell Job Cmdlets</span></span>

<span data-ttu-id="688d4-135">Windows PowerShell 會提供下列 Cmdlet 來管理背景工作。</span><span class="sxs-lookup"><span data-stu-id="688d4-135">The following cmdlets are provided by Windows PowerShell to manage background jobs.</span></span>

[<span data-ttu-id="688d4-136">Get-Job</span><span class="sxs-lookup"><span data-stu-id="688d4-136">Get-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

<span data-ttu-id="688d4-137">取得正在目前工作階段中執行的 Windows PowerShell 背景工作。</span><span class="sxs-lookup"><span data-stu-id="688d4-137">Gets Windows PowerShell background jobs that are running in the current session.</span></span>

[<span data-ttu-id="688d4-138">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="688d4-138">Receive-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

<span data-ttu-id="688d4-139">取得目前工作階段中 Windows PowerShell 背景工作的結果。</span><span class="sxs-lookup"><span data-stu-id="688d4-139">Gets the results of the Windows PowerShell background jobs in the current session.</span></span>

[<span data-ttu-id="688d4-140">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="688d4-140">Remove-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

<span data-ttu-id="688d4-141">刪除 Windows PowerShell 背景工作。</span><span class="sxs-lookup"><span data-stu-id="688d4-141">Deletes a Windows PowerShell background job.</span></span>

[<span data-ttu-id="688d4-142">Start-Job</span><span class="sxs-lookup"><span data-stu-id="688d4-142">Start-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

<span data-ttu-id="688d4-143">啟動 Windows PowerShell 背景工作。</span><span class="sxs-lookup"><span data-stu-id="688d4-143">Starts a Windows PowerShell background job.</span></span>

[<span data-ttu-id="688d4-144">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="688d4-144">Stop-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

<span data-ttu-id="688d4-145">停止 Windows PowerShell 背景工作。</span><span class="sxs-lookup"><span data-stu-id="688d4-145">Stops a Windows PowerShell background job.</span></span>

[<span data-ttu-id="688d4-146">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="688d4-146">Wait-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

<span data-ttu-id="688d4-147">抑制命令提示字元，直到工作階段中正在執行的其中一個或所有 Windows PowerShell 背景工作完成為止。</span><span class="sxs-lookup"><span data-stu-id="688d4-147">Suppresses the command prompt until one or all of the Windows PowerShell background jobs running in the session are complete.</span></span>

## <a name="see-also"></a><span data-ttu-id="688d4-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="688d4-148">See Also</span></span>

[<span data-ttu-id="688d4-149">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="688d4-149">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
