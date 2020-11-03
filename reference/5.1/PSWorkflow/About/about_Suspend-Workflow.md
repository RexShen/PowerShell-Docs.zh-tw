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
# <a name="about-suspend-workflow"></a>關於 Suspend-Workflow

## <a name="short-description"></a>簡短描述

描述 `Suspend-Workflow` 活動，此活動會暫停活動顯示所在的工作流程。

## <a name="long-description"></a>完整描述

`Suspend-Workflow`活動會暫時停止工作流程內的工作流程處理。 在暫停之前，Windows PowerShell 工作流程會採用檢查點，因此會保留工作流程的狀態和資料，而且工作流程可以從暫停點繼續進行。

若要繼續工作流程，執行工作流程的使用者會使用 `Resume-Job` Cmdlet。 您無法從工作流程內繼續工作流程。

## <a name="syntax"></a>Syntax

```
workflow <Verb-Noun>
{
    Suspend-Workflow
}
```

## <a name="detailed-description"></a>詳細描述

`Suspend-Workflow`會暫時停止工作流程，並傳回代表工作流程工作的工作物件。 即使您未以工作的形式執行工作流程，也會傳回工作物件。 例如，使用 **AsJob** 工作流程一般參數。 作業狀態為 [已 **暫停** ]。

您可以使用 job Cmdlet 來管理已暫止的工作流程工作。 若要繼續工作流程工作，請使用 `Resume-Job` Cmdlet。

當您繼續工作流程工作時，工作流程會在活動後面的命令繼續進行 `Suspend-Workflow` 。

例如，下列工作流程包含 `Suspend-Workflow` 活動。
當您執行工作流程時，它會執行 `Get-Date` 活動、將其輸出儲存在變數中，然後暫止 `$a` 工作流程，並傳回代表已暫止工作流程的工作物件。 作業類型是 **PSWorkflowJob** 。

您可以使用工作 Cmdlet （例如 `Get-Job` ）來管理工作流程工作。

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

## <a name="resuming-a-workflow-job"></a>繼續工作流程工作

若要繼續工作流程工作，請使用 `Resume-Job` Cmdlet。 `Resume-Job` Cmdlet 會立即傳回工作流程工作物件，即使它可能尚未繼續。 若要等候工作繼續，請使用 **wait** 參數，或使用 `Get-Job` Cmdlet 取得目前的工作物件。

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

## <a name="getting-the-output-of-a-workflow-job"></a>取得工作流程工作的輸出

若要取得工作流程工作的輸出，請使用 `Receive-Job` Cmdlet。 輸出會顯示工作流程已在遵循指令程式的命令中繼續執行 `Suspend-Workflow` 。 在 `$a` 暫停之前填入的變數值，可在工作流程繼續時使用。

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

## <a name="see-also"></a>另請參閱

[about_Workflows](about_Workflows.md)

[about_WorkflowCommonParameters](about_WorkflowCommonParameters.md)

[PSWorkflow](xref:PSWorkflow) Cmdlet

[工作流程指南](/previous-versions/powershell/scripting/components/workflows-guide)

[撰寫 Windows PowerShell 工作流程](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
