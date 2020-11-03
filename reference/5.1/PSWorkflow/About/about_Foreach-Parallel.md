---
description: 描述 `ForEach -Parallel` Windows PowerShell 工作流程中的語言結構。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/10/2019
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_foreach-parallel?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Foreach 平行
ms.openlocfilehash: 1012b45396b65d424dacac067c2af8d3b6823f92
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207240"
---
# <a name="about-foreach-parallel"></a>關於 Foreach-Parallel

## <a name="short-description"></a>簡短描述
描述 `ForEach -Parallel` Windows PowerShell 工作流程中的語言結構。

## <a name="long-description"></a>詳細描述

關鍵字的 **Parallel** 參數會 `ForEach` 針對所 `ForEach` 指定集合中的每個專案執行一次腳本區塊中的命令。

集合中的專案（例如磁片集合中的磁片）會以平行方式處理。 腳本區塊中的命令會在集合中的每個專案上依序執行。

`ForEach -Parallel` 只有在 Windows PowerShell 工作流程中才有效。

### <a name="syntax"></a>SYNTAX

```
ForEach -Parallel ($<item> in $<collection>)
{
    [<Activity1>]
    [<Activity2>]
    ...
}
```

### <a name="detailed-description"></a>詳細描述

就像 Windows PowerShell 中的 ForEach 語句一樣，包含集合的變數 `$<collection>` 必須在語句之前定義 `ForEach -Parallel` ，但代表目前專案的變數 `$<item>` 是在語句中定義 `ForEach -Parallel` 。

此 `ForEach -Parallel` 結構與 `ForEach` 關鍵字和 **Parallel** 參數不同。 關鍵字會依 `ForEach` 序處理集合中的專案。 **Parallel** 參數會以平行方式在腳本區塊中執行命令。 您可以將平行腳本區塊放在 `ForEach -Parallel` 腳本區塊中。

工作流程中的目的電腦（例如 **PSComputerName** 工作流程一般參數所指定的電腦）一律會以平行方式處理。
您不需要為 `ForEach -Parallel` 此用途指定關鍵字。

### <a name="examples"></a>範例

下列工作流程包含 `ForEach -Parallel` 處理活動所取得之磁片的語句 `Get-Disk` 。 腳本區塊中的命令 `ForEach -Parallel` 會依序執行，但它們會以平行方式在磁片上執行。 磁片可能會以任何順序同時進行處理。

```powershell
workflow Test-Workflow
{
    $Disks = Get-Disk

    # The disks are processed in parallel.
    ForEach -Parallel ($Disk in $Disks)
    {
        # The commands run sequentially on each disk.
        $DiskPath = $Disk.Path
        $Disk | Initialize-Disk
        Set-Disk -Path $DiskPath
    }
}

workflow Test-Workflow
{
    #Run commands in parallel.
    Parallel
    {
        Get-Process
        Get-Service
    }

   $Disks = Get-Disk

   # The disks are processed in parallel.
   ForEach -Parallel ($Disk in $Disks)
   {
       # The commands run in parallel on each disk.
       Parallel
       {
           Initialize-Disk
           InlineScript {.\Get-DiskInventory}
       }
   }
}
```

## <a name="see-also"></a>另請參閱

[Writing a Script Workflow](/previous-versions/powershell/scripting/developer/workflow/creating-a-workflow-by-using-a-windows-powershell-script)

[about_ForEach](../../Microsoft.PowerShell.Core/About/about_ForEach.md)

[about_Language_Keywords](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[about_Parallel](about_Parallel.md)

[about_Workflows](about_Workflows.md)
