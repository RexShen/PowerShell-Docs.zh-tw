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
# <a name="about-inlinescript"></a>關於 InlineScript

## <a name="short-description"></a>簡短描述

描述在 `InlineScript` 工作流程中執行 PowerShell 命令的活動。

## <a name="long-description"></a>完整描述

`InlineScript`活動會在共用的 PowerShell 會話工作流程中執行命令。 `InlineScript` 只在工作流程中有效。

## <a name="syntax"></a>Syntax

```
InlineScript {<script block>} <ActivityCommonParameters>
```

## <a name="detailed-description"></a>詳細描述

`InlineScript`活動會在共用的 PowerShell 會話中執行命令。 您可以將它包含在工作流程中，以執行共用資料的命令，以及在工作流程中不正確命令。

`InlineScript`腳本區塊可包含所有有效的 PowerShell 命令和運算式。 由於腳本區塊中的命令和運算式 `InlineScript` 會在相同的會話中執行，因此它們會共用所有狀態和資料，包括匯入的模組和變數的值。

您可以將 `InlineScript` 活動放在工作流程或嵌套工作流程中的任何位置，包括迴圈或控制語句或平行或序列腳本區塊內。

`InlineScript`活動有活動一般參數，包括 **PSPersist** 。 不過，腳本區塊中的命令和運算式 `InlineScript` 沒有工作流程功能，例如檢查點或持續性，以及工作流程或活動一般參數。 如需詳細資訊，請參閱 [about_ActivityCommonParameters](about_ActivityCommonParameters.md)。

## <a name="inlinescript-variables"></a>InlineScript 變數

根據預設，腳本區塊中的命令看不到工作流程中定義的變數 `InlineScript` 。 若要讓可以看見的工作流程變數 `InlineScript` ，請使用 `$Using` 範圍修飾符。 `$Using`只有在中的每個變數都需要有一次範圍修飾符 `InlineScript` 。

如需範圍修飾符的詳細資訊 `$Using` ，請參閱 [about_Remote_Variables](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md)。

下列範例顯示 `$Using` 範圍修飾詞會讓 `$a` 腳本區塊中的命令使用最上層工作流程變數的值 `InlineScript` 。

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

## <a name="returning-variables-in-inlinescript"></a>傳回 InlineScript 中的變數

`InlineScript` 命令可以變更從工作流程範圍匯入之變數的值，但變更不會顯示在工作流程範圍中。 若要讓變更可見，請將變更的值傳回到工作流程範圍，如下列範例所示。

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
> 具有 `$Using` 範圍修飾符的語句應該在腳本區塊中的任何變數使用之前出現 `InlineScript` 。

## <a name="running-in-process"></a>執行同進程

為了改善可靠性，腳本區塊中的命令會 `InlineScript` 在自己的進程中執行，並與工作流程執行所在的進程分開，然後將其輸出傳回工作流程進程。

若要指示 PowerShell `InlineScript` 在工作流程處理常式中執行活動，請 `InlineScript` 從會話設定的 **OutOfProcessActivity** 屬性移除值，例如使用 `New-PSWorkflowExecutionOption` Cmdlet。

### <a name="example"></a>範例

`InlineScript`下列工作流程中的會包含在 PowerShell 中有效但在工作流程中不正確命令。 例如， `New-Object` 具有 **ComObject** 參數的 Cmdlet。

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

## <a name="see-also"></a>另請參閱

[about_ActivityCommonParameters](about_ActivityCommonParameters.md)

[about_Remote_Variables](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md)

[about_WorkflowCommonParameters](about_WorkflowCommonParameters.md)

[PSWorkflow](xref:PSWorkflow) Cmdlet

[工作流程指南](/previous-versions/powershell/scripting/components/workflows-guide)

[撰寫 Windows PowerShell 工作流程](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
