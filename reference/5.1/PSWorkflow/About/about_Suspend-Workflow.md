---
description: 描述 `Suspend-Workflow` 活動，此活動會暫停活動顯示所在的工作流程。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_suspend-workflow?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Suspend 工作流程
ms.openlocfilehash: cbe5386ae5aa4bd863079fde240ddf2ce5384727
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207219"
---
# <a name="about-suspend-workflow"></a><span data-ttu-id="ac2bf-104">關於 Suspend-Workflow</span><span class="sxs-lookup"><span data-stu-id="ac2bf-104">About Suspend-Workflow</span></span>

## <a name="short-description"></a><span data-ttu-id="ac2bf-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="ac2bf-105">Short description</span></span>

<span data-ttu-id="ac2bf-106">描述 `Suspend-Workflow` 活動，此活動會暫停活動顯示所在的工作流程。</span><span class="sxs-lookup"><span data-stu-id="ac2bf-106">Describes the `Suspend-Workflow` activity, which suspends the workflow in which the activity appears.</span></span>

## <a name="long-description"></a><span data-ttu-id="ac2bf-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="ac2bf-107">Long description</span></span>

<span data-ttu-id="ac2bf-108">`Suspend-Workflow`活動會暫時停止工作流程內的工作流程處理。</span><span class="sxs-lookup"><span data-stu-id="ac2bf-108">The `Suspend-Workflow` activity temporarily stops workflow processing from within the workflow.</span></span> <span data-ttu-id="ac2bf-109">在暫停之前，Windows PowerShell 工作流程會採用檢查點，因此會保留工作流程的狀態和資料，而且工作流程可以從暫停點繼續進行。</span><span class="sxs-lookup"><span data-stu-id="ac2bf-109">Before suspending, Windows PowerShell Workflow takes a checkpoint so the workflow's state and data are preserved and the workflow can resume from the suspension point.</span></span>

<span data-ttu-id="ac2bf-110">若要繼續工作流程，執行工作流程的使用者會使用 `Resume-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ac2bf-110">To resume the workflow, the user running the workflow uses the `Resume-Job` cmdlet.</span></span> <span data-ttu-id="ac2bf-111">您無法從工作流程內繼續工作流程。</span><span class="sxs-lookup"><span data-stu-id="ac2bf-111">You can't resume a workflow from within the workflow.</span></span>

## <a name="syntax"></a><span data-ttu-id="ac2bf-112">Syntax</span><span class="sxs-lookup"><span data-stu-id="ac2bf-112">Syntax</span></span>

```
workflow <Verb-Noun>
{
    Suspend-Workflow
}
```

## <a name="detailed-description"></a><span data-ttu-id="ac2bf-113">詳細描述</span><span class="sxs-lookup"><span data-stu-id="ac2bf-113">Detailed description</span></span>

<span data-ttu-id="ac2bf-114">`Suspend-Workflow`會暫時停止工作流程，並傳回代表工作流程工作的工作物件。</span><span class="sxs-lookup"><span data-stu-id="ac2bf-114">The `Suspend-Workflow` temporarily stops the workflow and returns a job object that represents the workflow job.</span></span> <span data-ttu-id="ac2bf-115">即使您未以工作的形式執行工作流程，也會傳回工作物件。</span><span class="sxs-lookup"><span data-stu-id="ac2bf-115">A job object is returned even if you didn't run the workflow as a job.</span></span> <span data-ttu-id="ac2bf-116">例如，使用 **AsJob** 工作流程一般參數。</span><span class="sxs-lookup"><span data-stu-id="ac2bf-116">For example, such as by using the **AsJob** workflow common parameter.</span></span> <span data-ttu-id="ac2bf-117">作業狀態為 [已 **暫停** ]。</span><span class="sxs-lookup"><span data-stu-id="ac2bf-117">The job state is **Suspended** .</span></span>

<span data-ttu-id="ac2bf-118">您可以使用 job Cmdlet 來管理已暫止的工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="ac2bf-118">You can use the job cmdlets to manage the suspended workflow job.</span></span> <span data-ttu-id="ac2bf-119">若要繼續工作流程工作，請使用 `Resume-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ac2bf-119">To resume the workflow job, use the `Resume-Job` cmdlet.</span></span>

<span data-ttu-id="ac2bf-120">當您繼續工作流程工作時，工作流程會在活動後面的命令繼續進行 `Suspend-Workflow` 。</span><span class="sxs-lookup"><span data-stu-id="ac2bf-120">When you resume the workflow job, the workflow resumes at the command that follows the `Suspend-Workflow` activity.</span></span>

<span data-ttu-id="ac2bf-121">例如，下列工作流程包含 `Suspend-Workflow` 活動。</span><span class="sxs-lookup"><span data-stu-id="ac2bf-121">For example, the following workflow includes the `Suspend-Workflow` activity.</span></span>
<span data-ttu-id="ac2bf-122">當您執行工作流程時，它會執行 `Get-Date` 活動、將其輸出儲存在變數中，然後暫止 `$a` 工作流程，並傳回代表已暫止工作流程的工作物件。</span><span class="sxs-lookup"><span data-stu-id="ac2bf-122">When you run the workflow, it runs the `Get-Date` activity, saves its output in the `$a` variable, and then suspends the workflow, and returns a job object that represents the suspended workflow.</span></span> <span data-ttu-id="ac2bf-123">作業類型是 **PSWorkflowJob** 。</span><span class="sxs-lookup"><span data-stu-id="ac2bf-123">The job type is **PSWorkflowJob** .</span></span>

<span data-ttu-id="ac2bf-124">您可以使用工作 Cmdlet （例如 `Get-Job` ）來管理工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="ac2bf-124">You can use the job cmdlets, such as `Get-Job`, to manage the workflow job.</span></span>

```powershell
Workflow Test-Suspend
{
    $a = Get-Date
    Suspend-Workflow
    (Get-Date)- $a
}

Test-Suspend
```

```Output
Id  Name  PSJobTypeName  State      HasMoreData  Location  Command
--  ----  -------------  -----      -----------  --------  -------
8   Job8  PSWorkflowJob  Suspended  True         localhost Test-Suspend
```

## <a name="resuming-a-workflow-job"></a><span data-ttu-id="ac2bf-125">繼續工作流程工作</span><span class="sxs-lookup"><span data-stu-id="ac2bf-125">Resuming a workflow job</span></span>

<span data-ttu-id="ac2bf-126">若要繼續工作流程工作，請使用 `Resume-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ac2bf-126">To resume the workflow job, use the `Resume-Job` cmdlet.</span></span> <span data-ttu-id="ac2bf-127">`Resume-Job` Cmdlet 會立即傳回工作流程工作物件，即使它可能尚未繼續。</span><span class="sxs-lookup"><span data-stu-id="ac2bf-127">The `Resume-Job` cmdlet returns the workflow job object immediately, even though it might not yet be resumed.</span></span> <span data-ttu-id="ac2bf-128">若要等候工作繼續，請使用 **wait** 參數，或使用 `Get-Job` Cmdlet 取得目前的工作物件。</span><span class="sxs-lookup"><span data-stu-id="ac2bf-128">To wait for the job to be resumed, use the **Wait** parameter, or use the `Get-Job` cmdlet to get the current job object.</span></span>

```powershell
Resume-Job -Name Job8
```

```Output
Id  Name  PSJobTypeName  State    HasMoreData  Location  Command
--  ----  -------------  -----    -----------  --------  -------
8   Job8  PSWorkflowJob  Running  True         localhost Test-Suspend
```

```powershell
Get-Job -Name Job8
```

```Output
Id  Name  PSJobTypeName  State      HasMoreData  Location  Command
--  ----  -------------  -----      -----------  --------  -------
8   Job8  PSWorkflowJob  Completed  True         localhost Test-Suspend
```

## <a name="getting-the-output-of-a-workflow-job"></a><span data-ttu-id="ac2bf-129">取得工作流程工作的輸出</span><span class="sxs-lookup"><span data-stu-id="ac2bf-129">Getting the output of a workflow job</span></span>

<span data-ttu-id="ac2bf-130">若要取得工作流程工作的輸出，請使用 `Receive-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ac2bf-130">To get the output of a workflow job, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="ac2bf-131">輸出會顯示工作流程已在遵循指令程式的命令中繼續執行 `Suspend-Workflow` 。</span><span class="sxs-lookup"><span data-stu-id="ac2bf-131">The output shows that the workflow resumed at the command that followed the `Suspend-Workflow` cmdlet.</span></span> <span data-ttu-id="ac2bf-132">在 `$a` 暫停之前填入的變數值，可在工作流程繼續時使用。</span><span class="sxs-lookup"><span data-stu-id="ac2bf-132">The value of the `$a` variable, which was populated before the suspension, is available to the workflow when it resumes.</span></span>

```powershell
Get-Job -Name Job8 | Receive-Job
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 19
Milliseconds      : 823
Ticks             : 198230041
TotalDays         : 0.000229432917824074
TotalHours        : 0.00550639002777778
TotalMinutes      : 0.330383401666667
TotalSeconds      : 19.8230041
TotalMilliseconds : 19823.0041
PSComputerName    : localhost
```

## <a name="see-also"></a><span data-ttu-id="ac2bf-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac2bf-133">See also</span></span>

[<span data-ttu-id="ac2bf-134">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="ac2bf-134">about_Workflows</span></span>](about_Workflows.md)

[<span data-ttu-id="ac2bf-135">about_WorkflowCommonParameters</span><span class="sxs-lookup"><span data-stu-id="ac2bf-135">about_WorkflowCommonParameters</span></span>](about_WorkflowCommonParameters.md)

<span data-ttu-id="ac2bf-136">[PSWorkflow](xref:PSWorkflow) Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ac2bf-136">[PSWorkflow](xref:PSWorkflow) cmdlets</span></span>

[<span data-ttu-id="ac2bf-137">工作流程指南</span><span class="sxs-lookup"><span data-stu-id="ac2bf-137">Workflows Guide</span></span>](/previous-versions/powershell/scripting/components/workflows-guide)

[<span data-ttu-id="ac2bf-138">撰寫 Windows PowerShell 工作流程</span><span class="sxs-lookup"><span data-stu-id="ac2bf-138">Writing a Windows PowerShell Workflow</span></span>](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
