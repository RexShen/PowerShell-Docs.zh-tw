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
# <a name="about-parallel"></a>關於平行

## <a name="short-description"></a>簡短描述
描述 Parallel 關鍵字，該關鍵字會平行執行工作流程中的活動。

## <a name="long-description"></a>詳細描述

Parallel 關鍵字會以平行方式執行工作流程活動。 這個關鍵字只在 Windows PowerShell 工作流程中有效。

### <a name="syntax"></a>SYNTAX

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

## <a name="detailed-description"></a>詳細描述

Parallel 指令碼區塊中的命令可以同時執行。 命令的執行順序不定。

例如，下列工作流程包含 Parallel 指令碼區塊，它會執行取得電腦上執行之處理程序與服務的活動。 由於 Get-Process 和 Get-Service 命令彼此獨立，因此可以依任何順序並存執行。

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

以平行方式執行命令非常有效率，而且可減少大幅完成工作流程所需的時間。

若要依順序在平行腳本區塊中執行選取的命令，請使用 Sequence 關鍵字。 如需詳細資訊，請參閱 about_Sequence。

若要在集合中的專案上執行平行腳本區塊，請使用 ForEach 或 ForEach 平行關鍵字。

## <a name="see-also"></a>另請參閱

[「撰寫腳本工作流程」](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574157(v=ws.11))

[about_ForEach](../../Microsoft.PowerShell.Core/About/about_Foreach.md)

[about_ForEach-平行](about_ForEach-Parallel.md)

[about_Language_Keywords](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[about_Sequence](about_Sequence.md)

[about_Workflows](about_workflows.md)
