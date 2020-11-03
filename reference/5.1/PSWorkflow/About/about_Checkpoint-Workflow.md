---
description: 描述會在工作流程中使用檢查點的 Checkpoint-Workflow 活動。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_checkpoint-workflow?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Checkpoint 工作流程
ms.openlocfilehash: 223deb07ff6ed387cf04736116ea0ce3f998bb59
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207243"
---
# <a name="about-checkpoint-workflow"></a><span data-ttu-id="827d8-104">關於 Checkpoint-Workflow</span><span class="sxs-lookup"><span data-stu-id="827d8-104">About Checkpoint-Workflow</span></span>

## <a name="short-description"></a><span data-ttu-id="827d8-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="827d8-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="827d8-106">描述會在工作流程中使用檢查點的 Checkpoint-Workflow 活動。</span><span class="sxs-lookup"><span data-stu-id="827d8-106">Describes the Checkpoint-Workflow activity, which takes a checkpoint in a workflow.</span></span>

## <a name="long-description"></a><span data-ttu-id="827d8-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="827d8-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="827d8-108">Checkpoint-Workflow 活動會採用檢查點，以在工作流程中儲存狀態和資料。</span><span class="sxs-lookup"><span data-stu-id="827d8-108">The Checkpoint-Workflow activity takes a checkpoint, which saves state and data in the workflow.</span></span> <span data-ttu-id="827d8-109">如果工作流程暫停或中斷，它可以從最新的檢查點繼續，而不需要重新開機。</span><span class="sxs-lookup"><span data-stu-id="827d8-109">If the workflow is suspended or interrupted, it can be resumed from the most recent checkpoint, rather than having to be restarted.</span></span>

<span data-ttu-id="827d8-110">Checkpoint-Workflow 活動只在工作流程中有效。</span><span class="sxs-lookup"><span data-stu-id="827d8-110">The Checkpoint-Workflow activity is valid only in a workflow.</span></span>

### <a name="syntax"></a><span data-ttu-id="827d8-111">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="827d8-111">SYNTAX</span></span>

```
Workflow <Verb-Noun>
{
    Checkpoint-Workflow
}
```

<span data-ttu-id="827d8-112">Checkpoint-Workflow 活動不接受任何參數，包括一般參數和工作流程一般參數。</span><span class="sxs-lookup"><span data-stu-id="827d8-112">The Checkpoint-Workflow activity does not accept any parameters, including common parameters and workflow common parameters.</span></span>

<span data-ttu-id="827d8-113">您可以在 CmdletBinding 或 Param 語句之後，將 Checkpoint-Activity 檢查點放在工作流程中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="827d8-113">You can place the Checkpoint-Activity checkpoint anywhere in a workflow after the CmdletBinding or Param statement.</span></span> <span data-ttu-id="827d8-114">不過，在放置檢查點時，請考慮收集資料，並將資料寫入執行工作流程之電腦上磁片的效能成本。</span><span class="sxs-lookup"><span data-stu-id="827d8-114">However, when placing checkpoints, consider the performance cost of collecting the data and writing it to disk on the computer that is running the workflow.</span></span>

<span data-ttu-id="827d8-115">請確定如果工作流程被中斷，重新執行工作流程區段所花費的時間，大於將檢查點狀態和資料寫入磁碟所花費的時間。</span><span class="sxs-lookup"><span data-stu-id="827d8-115">Be sure that the time it takes to rerun a section of the workflow if it is interrupted is greater than the time it takes to write the checkpoint state and data to disk.</span></span>

<span data-ttu-id="827d8-116">考慮在重要步驟之後取得檢查點，讓工作流程可以繼續執行，而不是重新開機。</span><span class="sxs-lookup"><span data-stu-id="827d8-116">Consider taking checkpoints after critical steps so the workflow can be resumed rather than restarted.</span></span> <span data-ttu-id="827d8-117">例如，在不具等冪性的命令之後取得檢查點。</span><span class="sxs-lookup"><span data-stu-id="827d8-117">For example, take a checkpoint after commands that are not idempotent.</span></span>

### <a name="about-checkpoints"></a><span data-ttu-id="827d8-118">關於檢查點</span><span class="sxs-lookup"><span data-stu-id="827d8-118">ABOUT CHECKPOINTS</span></span>

<span data-ttu-id="827d8-119">檢查點是工作流程目前狀態的快照，包括變數的目前值，以及至該點為止產生的任何輸出，檢查點會將快照儲存到磁碟。</span><span class="sxs-lookup"><span data-stu-id="827d8-119">A checkpoint is a snapshot of the current state of the workflow, including the current values of variables, and any output generated up to that point, and it saves it to disk.</span></span>

<span data-ttu-id="827d8-120">如果工作流程被刻意或無意地中斷，Windows PowerShell 工作流程會自動使用最新檢查點中的資料來復原和繼續工作流程。</span><span class="sxs-lookup"><span data-stu-id="827d8-120">If a workflow is interrupted, intentionally or unintentionally, Windows PowerShell Workflow automatically uses the data in newest checkpoint to recover and resume the workflow.</span></span>

<span data-ttu-id="827d8-121">當您將工作流程執行為工作（例如使用 AsJob 工作流程一般參數）時，會保留工作流程檢查點直到您刪除該工作（例如使用 Remove-Job Cmdlet）。</span><span class="sxs-lookup"><span data-stu-id="827d8-121">When you run the workflow as a job, such as by using the AsJob workflow common parameter, the workflow checkpoints are retained until you delete the job, such as by using the Remove-Job cmdlet.</span></span>
<span data-ttu-id="827d8-122">否則會在工作流程完成時刪除工作流程檢查點。</span><span class="sxs-lookup"><span data-stu-id="827d8-122">Otherwise, workflow checkpoints are deleted when the workflow completes.</span></span>

### <a name="other-checkpointing-techniques"></a><span data-ttu-id="827d8-123">其他檢查點技術</span><span class="sxs-lookup"><span data-stu-id="827d8-123">OTHER CHECKPOINTING TECHNIQUES</span></span>

<span data-ttu-id="827d8-124">除了 Checkpoint-Workflow 活動之外，Windows PowerShell 工作流程還支援其他檢查點技術，包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="827d8-124">In addition to the Checkpoint-Workflow activity, Windows PowerShell Workflow supports other checkpointing techniques, including the following:</span></span>

- <span data-ttu-id="827d8-125">PSPersist 工作流程一般參數</span><span class="sxs-lookup"><span data-stu-id="827d8-125">PSPersist workflow common parameter</span></span>
- <span data-ttu-id="827d8-126">PSPersist 活動一般參數</span><span class="sxs-lookup"><span data-stu-id="827d8-126">PSPersist activity common parameter</span></span>
- <span data-ttu-id="827d8-127">在工作流程中 PSPersistPreference 變數 () </span><span class="sxs-lookup"><span data-stu-id="827d8-127">PSPersistPreference variable (in a workflow)</span></span>

<span data-ttu-id="827d8-128">如需將檢查點加入至工作流程的詳細資訊，請參閱「如何將檢查點加入至工作流程」。</span><span class="sxs-lookup"><span data-stu-id="827d8-128">For more information about adding a checkpoint to a workflow, see "How to Add Checkpoints to a Workflow."</span></span>

## <a name="examples"></a><span data-ttu-id="827d8-129">範例</span><span class="sxs-lookup"><span data-stu-id="827d8-129">EXAMPLES</span></span>

<span data-ttu-id="827d8-130">下列工作流程會在完成長時間執行的函式和共用資料的腳本之後，包括對 Checkpoint-Workflow 活動的呼叫。</span><span class="sxs-lookup"><span data-stu-id="827d8-130">The following workflow includes a call to the Checkpoint-Workflow activity after completing a long-running function and a script that share data.</span></span>

```powershell
Workflow Test-Workflow
{
    $a = Invoke-LongRunningFunction
    InlineScript { \\Server\Share\Get-DataPacks.ps1 $Using:a}
    Checkpoint-Workflow

    Invoke-LongRunningFunction
    {
        ...
    }
}
```

## <a name="see-also"></a><span data-ttu-id="827d8-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="827d8-131">SEE ALSO</span></span>

[<span data-ttu-id="827d8-132">撰寫 Windows PowerShell 工作流程</span><span class="sxs-lookup"><span data-stu-id="827d8-132">Writing a Windows PowerShell Workflow</span></span>](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
