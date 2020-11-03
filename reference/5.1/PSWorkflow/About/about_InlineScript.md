---
description: 描述在 `InlineScript` 工作流程中執行 PowerShell 命令的活動。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_inlinescript?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_InlineScript
ms.openlocfilehash: 2eaeb02c6441865551b586e27a39c4000826752b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207239"
---
# <a name="about-inlinescript"></a><span data-ttu-id="3bbdd-104">關於 InlineScript</span><span class="sxs-lookup"><span data-stu-id="3bbdd-104">About InlineScript</span></span>

## <a name="short-description"></a><span data-ttu-id="3bbdd-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="3bbdd-105">Short description</span></span>

<span data-ttu-id="3bbdd-106">描述在 `InlineScript` 工作流程中執行 PowerShell 命令的活動。</span><span class="sxs-lookup"><span data-stu-id="3bbdd-106">Describes the `InlineScript` activity, that runs PowerShell commands in a workflow.</span></span>

## <a name="long-description"></a><span data-ttu-id="3bbdd-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="3bbdd-107">Long description</span></span>

<span data-ttu-id="3bbdd-108">`InlineScript`活動會在共用的 PowerShell 會話工作流程中執行命令。</span><span class="sxs-lookup"><span data-stu-id="3bbdd-108">The `InlineScript` activity runs commands in a shared PowerShell session's workflow.</span></span> <span data-ttu-id="3bbdd-109">`InlineScript` 只在工作流程中有效。</span><span class="sxs-lookup"><span data-stu-id="3bbdd-109">`InlineScript` is only valid in workflows.</span></span>

## <a name="syntax"></a><span data-ttu-id="3bbdd-110">Syntax</span><span class="sxs-lookup"><span data-stu-id="3bbdd-110">Syntax</span></span>

```
InlineScript {<script block>} <ActivityCommonParameters>
```

## <a name="detailed-description"></a><span data-ttu-id="3bbdd-111">詳細描述</span><span class="sxs-lookup"><span data-stu-id="3bbdd-111">Detailed description</span></span>

<span data-ttu-id="3bbdd-112">`InlineScript`活動會在共用的 PowerShell 會話中執行命令。</span><span class="sxs-lookup"><span data-stu-id="3bbdd-112">The `InlineScript` activity runs commands in a shared PowerShell session.</span></span> <span data-ttu-id="3bbdd-113">您可以將它包含在工作流程中，以執行共用資料的命令，以及在工作流程中不正確命令。</span><span class="sxs-lookup"><span data-stu-id="3bbdd-113">You can include it in a workflow to run commands that share data and commands that aren't otherwise valid in a workflow.</span></span>

<span data-ttu-id="3bbdd-114">`InlineScript`腳本區塊可包含所有有效的 PowerShell 命令和運算式。</span><span class="sxs-lookup"><span data-stu-id="3bbdd-114">The `InlineScript` script block can include all valid PowerShell commands and expressions.</span></span> <span data-ttu-id="3bbdd-115">由於腳本區塊中的命令和運算式 `InlineScript` 會在相同的會話中執行，因此它們會共用所有狀態和資料，包括匯入的模組和變數的值。</span><span class="sxs-lookup"><span data-stu-id="3bbdd-115">Because the commands and expressions in an `InlineScript` script block run in the same session, they share all state and data, including imported modules and the values of variables.</span></span>

<span data-ttu-id="3bbdd-116">您可以將 `InlineScript` 活動放在工作流程或嵌套工作流程中的任何位置，包括迴圈或控制語句或平行或序列腳本區塊內。</span><span class="sxs-lookup"><span data-stu-id="3bbdd-116">You can place an `InlineScript` activity anywhere in a workflow or nested workflow, including inside a loop or control statement or a Parallel or Sequence script block.</span></span>

<span data-ttu-id="3bbdd-117">`InlineScript`活動有活動一般參數，包括 **PSPersist** 。</span><span class="sxs-lookup"><span data-stu-id="3bbdd-117">The `InlineScript` activity has the activity common parameters, including **PSPersist** .</span></span> <span data-ttu-id="3bbdd-118">不過，腳本區塊中的命令和運算式 `InlineScript` 沒有工作流程功能，例如檢查點或持續性，以及工作流程或活動一般參數。</span><span class="sxs-lookup"><span data-stu-id="3bbdd-118">However, the commands and expressions in an `InlineScript` script block don't have the workflow features such as checkpointing, or persistence, and workflow or activity common parameters.</span></span> <span data-ttu-id="3bbdd-119">如需詳細資訊，請參閱 [about_ActivityCommonParameters](about_ActivityCommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="3bbdd-119">For more information, see [about_ActivityCommonParameters](about_ActivityCommonParameters.md).</span></span>

## <a name="inlinescript-variables"></a><span data-ttu-id="3bbdd-120">InlineScript 變數</span><span class="sxs-lookup"><span data-stu-id="3bbdd-120">InlineScript Variables</span></span>

<span data-ttu-id="3bbdd-121">根據預設，腳本區塊中的命令看不到工作流程中定義的變數 `InlineScript` 。</span><span class="sxs-lookup"><span data-stu-id="3bbdd-121">By default, the variables that are defined in a workflow aren't visible to the commands in the `InlineScript` script block.</span></span> <span data-ttu-id="3bbdd-122">若要讓可以看見的工作流程變數 `InlineScript` ，請使用 `$Using` 範圍修飾符。</span><span class="sxs-lookup"><span data-stu-id="3bbdd-122">To make workflow variables visible to the `InlineScript`, use the `$Using` scope modifier.</span></span> <span data-ttu-id="3bbdd-123">`$Using`只有在中的每個變數都需要有一次範圍修飾符 `InlineScript` 。</span><span class="sxs-lookup"><span data-stu-id="3bbdd-123">The `$Using` scope modifier is required only once for each variable in the `InlineScript`.</span></span>

<span data-ttu-id="3bbdd-124">如需範圍修飾符的詳細資訊 `$Using` ，請參閱 [about_Remote_Variables](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="3bbdd-124">For more information about the `$Using` scope modifier, see [about_Remote_Variables](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md).</span></span>

<span data-ttu-id="3bbdd-125">下列範例顯示 `$Using` 範圍修飾詞會讓 `$a` 腳本區塊中的命令使用最上層工作流程變數的值 `InlineScript` 。</span><span class="sxs-lookup"><span data-stu-id="3bbdd-125">The following example shows that the `$Using` scope modifier makes the value of the `$a` top-level workflow variable available to the commands in the `InlineScript` script block.</span></span>

```powershell
workflow Test-Workflow {
  $a = 3

  ## Without $Using, the $a workflow variable isn't visible
  ## in inline script.
  InlineScript {"Inline A0 = $a"}

  ## $Using imports the variable and its current value.
  InlineScript {"Inline A1 = $Using:a"}
}

Test-Workflow
```

```output
Inline A0 =
Inline A1 = 3
```

## <a name="returning-variables-in-inlinescript"></a><span data-ttu-id="3bbdd-126">傳回 InlineScript 中的變數</span><span class="sxs-lookup"><span data-stu-id="3bbdd-126">Returning variables in InlineScript</span></span>

<span data-ttu-id="3bbdd-127">`InlineScript` 命令可以變更從工作流程範圍匯入之變數的值，但變更不會顯示在工作流程範圍中。</span><span class="sxs-lookup"><span data-stu-id="3bbdd-127">`InlineScript` commands can change the value of the variable that was imported from workflow scope, but the changes aren't visible in workflow scope.</span></span> <span data-ttu-id="3bbdd-128">若要讓變更可見，請將變更的值傳回到工作流程範圍，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="3bbdd-128">To make them visible, return the changed value to the workflow scope, as shown in the following example.</span></span>

```powershell
workflow Test-Workflow {
  $a = 3

  ##  Changes to the InlineScript variable value don't
  ##  change the workflow variable.
  InlineScript {
    $a = $Using:a+1;
    "Inline A = $a"
  }
  "Workflow A = $a"

  ##  To change the variable in workflow scope, return the
  ##  new value.
  $a = InlineScript {$b = $Using:a+1; $b}
  "Workflow New A = $a"
}

Test-Workflow
```

```output
Inline A = 4
Workflow A = 3
Workflow New A = 4
```

> [!NOTE]
> <span data-ttu-id="3bbdd-129">具有 `$Using` 範圍修飾符的語句應該在腳本區塊中的任何變數使用之前出現 `InlineScript` 。</span><span class="sxs-lookup"><span data-stu-id="3bbdd-129">A statement with the `$Using` scope modifier should appear before any use of the variable in the `InlineScript` script block.</span></span>

## <a name="running-in-process"></a><span data-ttu-id="3bbdd-130">執行同進程</span><span class="sxs-lookup"><span data-stu-id="3bbdd-130">Running in-process</span></span>

<span data-ttu-id="3bbdd-131">為了改善可靠性，腳本區塊中的命令會 `InlineScript` 在自己的進程中執行，並與工作流程執行所在的進程分開，然後將其輸出傳回工作流程進程。</span><span class="sxs-lookup"><span data-stu-id="3bbdd-131">To improve reliability, the commands in the `InlineScript` script block run in their own process, separate from the process in which the workflow runs, and then return their output to the workflow process.</span></span>

<span data-ttu-id="3bbdd-132">若要指示 PowerShell `InlineScript` 在工作流程處理常式中執行活動，請 `InlineScript` 從會話設定的 **OutOfProcessActivity** 屬性移除值，例如使用 `New-PSWorkflowExecutionOption` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3bbdd-132">To direct PowerShell to run the `InlineScript` activity in the workflow process, remove the `InlineScript` value from the **OutOfProcessActivity** property of the session configuration, such as by using the `New-PSWorkflowExecutionOption` cmdlet.</span></span>

### <a name="example"></a><span data-ttu-id="3bbdd-133">範例</span><span class="sxs-lookup"><span data-stu-id="3bbdd-133">Example</span></span>

<span data-ttu-id="3bbdd-134">`InlineScript`下列工作流程中的會包含在 PowerShell 中有效但在工作流程中不正確命令。</span><span class="sxs-lookup"><span data-stu-id="3bbdd-134">The `InlineScript` in the following workflow includes commands that are valid in PowerShell but aren't valid in workflows.</span></span> <span data-ttu-id="3bbdd-135">例如， `New-Object` 具有 **ComObject** 參數的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3bbdd-135">For example, the `New-Object` cmdlet with the **ComObject** parameter.</span></span>

```powershell
workflow Test-Workflow
{
  $ie = InlineScript {
    $ie = New-Object -ComObject InternetExplorer.Application -Property @{navigate2="www.microsoft.com"}

    $ie.Visible = $true
  }

  $ie
}

Test-Workflow
```

## <a name="see-also"></a><span data-ttu-id="3bbdd-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3bbdd-136">See also</span></span>

[<span data-ttu-id="3bbdd-137">about_ActivityCommonParameters</span><span class="sxs-lookup"><span data-stu-id="3bbdd-137">about_ActivityCommonParameters</span></span>](about_ActivityCommonParameters.md)

[<span data-ttu-id="3bbdd-138">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="3bbdd-138">about_Remote_Variables</span></span>](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md)

[<span data-ttu-id="3bbdd-139">about_WorkflowCommonParameters</span><span class="sxs-lookup"><span data-stu-id="3bbdd-139">about_WorkflowCommonParameters</span></span>](about_WorkflowCommonParameters.md)

<span data-ttu-id="3bbdd-140">[PSWorkflow](xref:PSWorkflow) Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3bbdd-140">[PSWorkflow](xref:PSWorkflow) cmdlets</span></span>

[<span data-ttu-id="3bbdd-141">工作流程指南</span><span class="sxs-lookup"><span data-stu-id="3bbdd-141">Workflows Guide</span></span>](/previous-versions/powershell/scripting/components/workflows-guide)

[<span data-ttu-id="3bbdd-142">撰寫 Windows PowerShell 工作流程</span><span class="sxs-lookup"><span data-stu-id="3bbdd-142">Writing a Windows PowerShell Workflow</span></span>](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
