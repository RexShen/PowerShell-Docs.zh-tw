---
description: 描述 Parallel 關鍵字，該關鍵字會平行執行工作流程中的活動。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_parallel?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parallel
ms.openlocfilehash: 402e93672bbea4ec9b6bfda8d608f266f6c40a21
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207232"
---
# <a name="about-parallel"></a><span data-ttu-id="90719-104">關於平行</span><span class="sxs-lookup"><span data-stu-id="90719-104">About Parallel</span></span>

## <a name="short-description"></a><span data-ttu-id="90719-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="90719-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="90719-106">描述 Parallel 關鍵字，該關鍵字會平行執行工作流程中的活動。</span><span class="sxs-lookup"><span data-stu-id="90719-106">Describes the Parallel keyword, which runs the activities in a workflow in parallel.</span></span>

## <a name="long-description"></a><span data-ttu-id="90719-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="90719-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="90719-108">Parallel 關鍵字會以平行方式執行工作流程活動。</span><span class="sxs-lookup"><span data-stu-id="90719-108">The Parallel keyword runs workflow activities in parallel.</span></span> <span data-ttu-id="90719-109">這個關鍵字只在 Windows PowerShell 工作流程中有效。</span><span class="sxs-lookup"><span data-stu-id="90719-109">This keyword is valid only in  Windows PowerShell  Workflow.</span></span>

### <a name="syntax"></a><span data-ttu-id="90719-110">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="90719-110">SYNTAX</span></span>

```
workflow <Verb-Noun>
{
     Parallel
     {
          [<Activity>]
          [<Activity>]
        ...
     }
 }
```

## <a name="detailed-description"></a><span data-ttu-id="90719-111">詳細描述</span><span class="sxs-lookup"><span data-stu-id="90719-111">DETAILED DESCRIPTION</span></span>

<span data-ttu-id="90719-112">Parallel 指令碼區塊中的命令可以同時執行。</span><span class="sxs-lookup"><span data-stu-id="90719-112">The commands in a Parallel script block can run concurrently.</span></span> <span data-ttu-id="90719-113">命令的執行順序不定。</span><span class="sxs-lookup"><span data-stu-id="90719-113">The order in which they run is not determined.</span></span>

<span data-ttu-id="90719-114">例如，下列工作流程包含 Parallel 指令碼區塊，它會執行取得電腦上執行之處理程序與服務的活動。</span><span class="sxs-lookup"><span data-stu-id="90719-114">For example, the following workflow includes a Parallel script block that runs activities that get processes and services on the computer.</span></span> <span data-ttu-id="90719-115">由於 Get-Process 和 Get-Service 命令彼此獨立，因此可以依任何順序並存執行。</span><span class="sxs-lookup"><span data-stu-id="90719-115">Because the Get-Process and Get-Service commands are independent of each other, they can run concurrently and in any order.</span></span>

```powershell
workflow Test-Workflow
{
    Parallel
    {
         Get-Process
         Get-Service
    }
}
```

<span data-ttu-id="90719-116">以平行方式執行命令非常有效率，而且可減少大幅完成工作流程所需的時間。</span><span class="sxs-lookup"><span data-stu-id="90719-116">Running commands in parallel is very efficient and reduces the time it takes to complete a workflow significantly.</span></span>

<span data-ttu-id="90719-117">若要依順序在平行腳本區塊中執行選取的命令，請使用 Sequence 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="90719-117">To run selected commands in a Parallel script block in sequential order, use the Sequence keyword.</span></span> <span data-ttu-id="90719-118">如需詳細資訊，請參閱 about_Sequence。</span><span class="sxs-lookup"><span data-stu-id="90719-118">For more information, see about_Sequence.</span></span>

<span data-ttu-id="90719-119">若要在集合中的專案上執行平行腳本區塊，請使用 ForEach 或 ForEach 平行關鍵字。</span><span class="sxs-lookup"><span data-stu-id="90719-119">To run a Parallel script block on items in a collection, use the ForEach or ForEach -Parallel keywords.</span></span>

## <a name="see-also"></a><span data-ttu-id="90719-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90719-120">SEE ALSO</span></span>

<span data-ttu-id="90719-121">[「撰寫腳本工作流程」](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574157(v=ws.11))</span><span class="sxs-lookup"><span data-stu-id="90719-121">["Writing a Script Workflow"](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574157(v=ws.11))</span></span>

[<span data-ttu-id="90719-122">about_ForEach</span><span class="sxs-lookup"><span data-stu-id="90719-122">about_ForEach</span></span>](../../Microsoft.PowerShell.Core/About/about_Foreach.md)

[<span data-ttu-id="90719-123">about_ForEach-平行</span><span class="sxs-lookup"><span data-stu-id="90719-123">about_ForEach-Parallel</span></span>](about_ForEach-Parallel.md)

[<span data-ttu-id="90719-124">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="90719-124">about_Language_Keywords</span></span>](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[<span data-ttu-id="90719-125">about_Sequence</span><span class="sxs-lookup"><span data-stu-id="90719-125">about_Sequence</span></span>](about_Sequence.md)

[<span data-ttu-id="90719-126">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="90719-126">about_Workflows</span></span>](about_workflows.md)
