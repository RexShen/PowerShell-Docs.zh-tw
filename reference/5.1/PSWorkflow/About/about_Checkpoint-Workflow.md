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
# <a name="about-checkpoint-workflow"></a>關於 Checkpoint-Workflow

## <a name="short-description"></a>簡短描述
描述會在工作流程中使用檢查點的 Checkpoint-Workflow 活動。

## <a name="long-description"></a>詳細描述

Checkpoint-Workflow 活動會採用檢查點，以在工作流程中儲存狀態和資料。 如果工作流程暫停或中斷，它可以從最新的檢查點繼續，而不需要重新開機。

Checkpoint-Workflow 活動只在工作流程中有效。

### <a name="syntax"></a>SYNTAX

```
Workflow <Verb-Noun>
{
    Checkpoint-Workflow
}
```

Checkpoint-Workflow 活動不接受任何參數，包括一般參數和工作流程一般參數。

您可以在 CmdletBinding 或 Param 語句之後，將 Checkpoint-Activity 檢查點放在工作流程中的任何位置。 不過，在放置檢查點時，請考慮收集資料，並將資料寫入執行工作流程之電腦上磁片的效能成本。

請確定如果工作流程被中斷，重新執行工作流程區段所花費的時間，大於將檢查點狀態和資料寫入磁碟所花費的時間。

考慮在重要步驟之後取得檢查點，讓工作流程可以繼續執行，而不是重新開機。 例如，在不具等冪性的命令之後取得檢查點。

### <a name="about-checkpoints"></a>關於檢查點

檢查點是工作流程目前狀態的快照，包括變數的目前值，以及至該點為止產生的任何輸出，檢查點會將快照儲存到磁碟。

如果工作流程被刻意或無意地中斷，Windows PowerShell 工作流程會自動使用最新檢查點中的資料來復原和繼續工作流程。

當您將工作流程執行為工作（例如使用 AsJob 工作流程一般參數）時，會保留工作流程檢查點直到您刪除該工作（例如使用 Remove-Job Cmdlet）。
否則會在工作流程完成時刪除工作流程檢查點。

### <a name="other-checkpointing-techniques"></a>其他檢查點技術

除了 Checkpoint-Workflow 活動之外，Windows PowerShell 工作流程還支援其他檢查點技術，包括下列各項：

- PSPersist 工作流程一般參數
- PSPersist 活動一般參數
- 在工作流程中 PSPersistPreference 變數 () 

如需將檢查點加入至工作流程的詳細資訊，請參閱「如何將檢查點加入至工作流程」。

## <a name="examples"></a>範例

下列工作流程會在完成長時間執行的函式和共用資料的腳本之後，包括對 Checkpoint-Workflow 活動的呼叫。

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

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell 工作流程](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
