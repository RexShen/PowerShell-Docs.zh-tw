---
description: 描述 `Sequence` 依序執行所選活動的關鍵字。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_sequence?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Sequence
ms.openlocfilehash: a9dd4fb24274fe4e1478ca69c734b43a2f196792
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207228"
---
# <a name="about-sequence"></a><span data-ttu-id="958a2-104">關於 Sequence</span><span class="sxs-lookup"><span data-stu-id="958a2-104">About Sequence</span></span>

## <a name="short-description"></a><span data-ttu-id="958a2-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="958a2-105">Short description</span></span>

<span data-ttu-id="958a2-106">描述 `Sequence` 依序執行所選活動的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="958a2-106">Describes the `Sequence` keyword that runs selected activities sequentially.</span></span>

## <a name="long-description"></a><span data-ttu-id="958a2-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="958a2-107">Long description</span></span>

<span data-ttu-id="958a2-108">`Sequence`關鍵字會依序執行選取的工作流程活動。</span><span class="sxs-lookup"><span data-stu-id="958a2-108">The `Sequence` keyword runs selected workflow activities sequentially.</span></span> <span data-ttu-id="958a2-109">工作流程活動會依其出現的循序執行，而不會同時執行。</span><span class="sxs-lookup"><span data-stu-id="958a2-109">Workflow activities run in the order that they appear and do not run concurrently.</span></span> <span data-ttu-id="958a2-110">`Sequence`關鍵字只在 PowerShell 工作流程中有效。</span><span class="sxs-lookup"><span data-stu-id="958a2-110">The `Sequence` keyword is only valid in a PowerShell Workflow.</span></span>

<span data-ttu-id="958a2-111">`Sequence`關鍵字會在 `Parallel` 腳本區塊中用來依序執行選取的命令。</span><span class="sxs-lookup"><span data-stu-id="958a2-111">The `Sequence` keyword is used in a `Parallel` script block to run selected commands sequentially.</span></span>

<span data-ttu-id="958a2-112">因為工作流程活動依預設會依序執行，所以 `Sequence` 關鍵字只有在 `Parallel` 腳本區塊中才有效。</span><span class="sxs-lookup"><span data-stu-id="958a2-112">Because workflow activities run sequentially by default, the `Sequence` keyword is only effective in a `Parallel` script block.</span></span> <span data-ttu-id="958a2-113">如果 `Sequence` 關鍵字未包含在 `Parallel` 腳本區塊中，則為有效但無效。</span><span class="sxs-lookup"><span data-stu-id="958a2-113">If the `Sequence` keyword isn't included in a `Parallel` script block, it's valid but ineffective.</span></span>

<span data-ttu-id="958a2-114">`Sequence`腳本區塊可讓您依序執行相依命令，以平行方式執行多個命令。</span><span class="sxs-lookup"><span data-stu-id="958a2-114">The `Sequence` script block lets you run more commands in parallel by allowing you to run dependent commands sequentially.</span></span>

## <a name="syntax"></a><span data-ttu-id="958a2-115">Syntax</span><span class="sxs-lookup"><span data-stu-id="958a2-115">Syntax</span></span>

### <a name="workflow-using-sequence"></a><span data-ttu-id="958a2-116">使用 Sequence 的工作流程</span><span class="sxs-lookup"><span data-stu-id="958a2-116">Workflow using Sequence</span></span>

```
workflow <Verb-Noun>
{
    Sequence
    {
        [<Activity>]
        [<Activity>]
        # ...
    }
}
```

### <a name="workflow-using-parallel-and-sequence"></a><span data-ttu-id="958a2-117">使用 Parallel 和 Sequence 的工作流程</span><span class="sxs-lookup"><span data-stu-id="958a2-117">Workflow using Parallel and Sequence</span></span>

```
workflow <Verb-Noun>
{
    Parallel
    {
        [<Activity>]
        Sequence
        {
            [<Activity>]
            [<Activity>]
            # ...
        }
    }
}
```

## <a name="detailed-description"></a><span data-ttu-id="958a2-118">詳細描述</span><span class="sxs-lookup"><span data-stu-id="958a2-118">Detailed description</span></span>

<span data-ttu-id="958a2-119">`Parallel` 指令碼區塊中的命令可以同時執行。</span><span class="sxs-lookup"><span data-stu-id="958a2-119">The commands in a `Parallel` script block can run concurrently.</span></span> <span data-ttu-id="958a2-120">命令的執行順序不定。</span><span class="sxs-lookup"><span data-stu-id="958a2-120">The order in which they run is not determined.</span></span> <span data-ttu-id="958a2-121">這項功能可改善腳本工作流程的效能。</span><span class="sxs-lookup"><span data-stu-id="958a2-121">This feature improves the performance of a script workflow.</span></span>

<span data-ttu-id="958a2-122">您可以使用 `Sequence` 腳本區塊循序執行選取的活動，即使活動出現在腳本區塊中也一樣 `Parallel` 。</span><span class="sxs-lookup"><span data-stu-id="958a2-122">You can use a `Sequence` script block to run selected activities sequentially, even though the activities appear in a `Parallel` script block.</span></span>

<span data-ttu-id="958a2-123">腳本區塊中的活動 `Sequence` 會依列出的順序連續執行。</span><span class="sxs-lookup"><span data-stu-id="958a2-123">The activities in a `Sequence` script block run consecutively in the order that they are listed.</span></span> <span data-ttu-id="958a2-124">腳本區塊中的活動只會在 `Sequence` 上一個活動完成之後才開始。</span><span class="sxs-lookup"><span data-stu-id="958a2-124">An activity in a `Sequence` script block starts only after the previous activity completes.</span></span>

<span data-ttu-id="958a2-125">不過，當腳本 `Sequence` 區塊出現在 `Parallel` 腳本區塊中時， `Sequence` 並不會決定腳本區塊執行的順序。</span><span class="sxs-lookup"><span data-stu-id="958a2-125">However, when the `Sequence` script block appears in a `Parallel` script block, the order in which the `Sequence` script block runs isn't determined.</span></span> <span data-ttu-id="958a2-126">它可能會在腳本區塊中的其他活動之前、之後或同時執行 `Parallel` 。</span><span class="sxs-lookup"><span data-stu-id="958a2-126">It might run before, after, or concurrent with other activities in the `Parallel` script block.</span></span>

<span data-ttu-id="958a2-127">例如，下列工作流程包含 `Parallel` 執行活動的腳本區塊，這些活動會取得電腦上的進程和服務。</span><span class="sxs-lookup"><span data-stu-id="958a2-127">For example, the following workflow includes a `Parallel` script block that runs activities that get processes and services on the computer.</span></span> <span data-ttu-id="958a2-128">`Parallel`腳本區塊包含的 `Sequence` 腳本區塊會從檔案取得資訊，並使用該資訊做為腳本的輸入。</span><span class="sxs-lookup"><span data-stu-id="958a2-128">The `Parallel` script block contains a `Sequence` script block that gets information from a file and uses the information as input to a script.</span></span>

<span data-ttu-id="958a2-129">`Get-Process`、 `Get-Service` 和與修補程式相關的命令彼此獨立。</span><span class="sxs-lookup"><span data-stu-id="958a2-129">The `Get-Process`, `Get-Service`, and hotfix-related commands are independent of each other.</span></span> <span data-ttu-id="958a2-130">這些命令可以並行或依任何循序執行。</span><span class="sxs-lookup"><span data-stu-id="958a2-130">The commands can run concurrently or in any order.</span></span> <span data-ttu-id="958a2-131">但是，取得修復資訊的命令必須在使用它的命令之前執行。</span><span class="sxs-lookup"><span data-stu-id="958a2-131">But, the command that gets the hotfix information must run before the command that uses it.</span></span>

```powershell
workflow Test-Workflow
{
    Parallel
    {
    Get-Process
    Get-Service

    Sequence
    {
        $Hotfix = Get-Content 'D:\HotFixes\Required.txt'
        Foreach ($h in $Hotfix) {'D:\Scripts\Verify-Hotfix' -Hotfix $h}
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="958a2-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="958a2-132">See also</span></span>

[<span data-ttu-id="958a2-133">about_ForEach</span><span class="sxs-lookup"><span data-stu-id="958a2-133">about_ForEach</span></span>](../../Microsoft.PowerShell.Core/About/about_Foreach.md)

[<span data-ttu-id="958a2-134">about_ForEach-平行</span><span class="sxs-lookup"><span data-stu-id="958a2-134">about_ForEach-Parallel</span></span>](about_ForEach-Parallel.md)

[<span data-ttu-id="958a2-135">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="958a2-135">about_Language_Keywords</span></span>](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[<span data-ttu-id="958a2-136">about_Parallel</span><span class="sxs-lookup"><span data-stu-id="958a2-136">about_Parallel</span></span>](about_Parallel.md)

[<span data-ttu-id="958a2-137">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="958a2-137">about_Workflows</span></span>](about_Workflows.md)

[<span data-ttu-id="958a2-138">使用 Windows PowerShell 指令碼建立工作流程</span><span class="sxs-lookup"><span data-stu-id="958a2-138">Creating a Workflow by Using a Windows PowerShell Script</span></span>](/previous-versions/powershell/scripting/developer/workflow/creating-a-workflow-by-using-a-windows-powershell-script)
