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
# <a name="about-sequence"></a>關於 Sequence

## <a name="short-description"></a>簡短描述

描述 `Sequence` 依序執行所選活動的關鍵字。

## <a name="long-description"></a>完整描述

`Sequence`關鍵字會依序執行選取的工作流程活動。 工作流程活動會依其出現的循序執行，而不會同時執行。 `Sequence`關鍵字只在 PowerShell 工作流程中有效。

`Sequence`關鍵字會在 `Parallel` 腳本區塊中用來依序執行選取的命令。

因為工作流程活動依預設會依序執行，所以 `Sequence` 關鍵字只有在 `Parallel` 腳本區塊中才有效。 如果 `Sequence` 關鍵字未包含在 `Parallel` 腳本區塊中，則為有效但無效。

`Sequence`腳本區塊可讓您依序執行相依命令，以平行方式執行多個命令。

## <a name="syntax"></a>Syntax

### <a name="workflow-using-sequence"></a>使用 Sequence 的工作流程

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

### <a name="workflow-using-parallel-and-sequence"></a>使用 Parallel 和 Sequence 的工作流程

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

## <a name="detailed-description"></a>詳細描述

`Parallel` 指令碼區塊中的命令可以同時執行。 命令的執行順序不定。 這項功能可改善腳本工作流程的效能。

您可以使用 `Sequence` 腳本區塊循序執行選取的活動，即使活動出現在腳本區塊中也一樣 `Parallel` 。

腳本區塊中的活動 `Sequence` 會依列出的順序連續執行。 腳本區塊中的活動只會在 `Sequence` 上一個活動完成之後才開始。

不過，當腳本 `Sequence` 區塊出現在 `Parallel` 腳本區塊中時， `Sequence` 並不會決定腳本區塊執行的順序。 它可能會在腳本區塊中的其他活動之前、之後或同時執行 `Parallel` 。

例如，下列工作流程包含 `Parallel` 執行活動的腳本區塊，這些活動會取得電腦上的進程和服務。 `Parallel`腳本區塊包含的 `Sequence` 腳本區塊會從檔案取得資訊，並使用該資訊做為腳本的輸入。

`Get-Process`、 `Get-Service` 和與修補程式相關的命令彼此獨立。 這些命令可以並行或依任何循序執行。 但是，取得修復資訊的命令必須在使用它的命令之前執行。

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

## <a name="see-also"></a>另請參閱

[about_ForEach](../../Microsoft.PowerShell.Core/About/about_Foreach.md)

[about_ForEach-平行](about_ForEach-Parallel.md)

[about_Language_Keywords](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[about_Parallel](about_Parallel.md)

[about_Workflows](about_Workflows.md)

[使用 Windows PowerShell 指令碼建立工作流程](/previous-versions/powershell/scripting/developer/workflow/creating-a-workflow-by-using-a-windows-powershell-script)
