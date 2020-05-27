---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
title: PowerShell 指令碼偵錯的增強功能
ms.openlocfilehash: f1771a451ba671da2371fcfc95374e6131573ddc
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808944"
---
# <a name="improvements-in-powershell-script-debugging"></a>PowerShell 指令碼偵錯的增強功能

PowerShell 5.0 包含數個可增強偵錯體驗的改進。

## <a name="break-all"></a>全部中斷

PowerShell 主控台和 PowerShell ISE 現在可讓您針對執行中的指令碼切換到偵錯工具。 這在本機和遠端工作階段皆適用。

在主控台中，按下 <kbd>Ctrl</kbd>+<kbd>Break</kbd>。

在 ISE 中，按下 <kbd>Ctrl</kbd>+<kbd>B</kbd>，或使用 [偵錯] -> [全部中斷]  功能表命令。

## <a name="remote-debugging-and-remote-file-editing-in-powershell-ise"></a>PowerShell ISE 中的遠端偵錯和遠端檔案編輯

PowerShell ISE 現在可讓您藉由執行 PSEdit 命令，在遠端工作階段中開啟及編輯檔案。
例如，您可以開啟檔案從遠端工作階段的命令列中進行編輯，如下所示︰

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

此外，您現在可以編輯並儲存遠端檔案中的變更，當您點擊中斷點時，該遠端檔案就會在 PowerShell ISE 中自動開啟。 現在，您可以偵錯在遠端電腦上執行的指令碼檔案、編輯檔案以修正錯誤，然後重新執行修改過的指令碼。

## <a name="advanced-script-debugging"></a>進階指令碼偵錯

有新的進階偵錯功能，可讓您附加至任何已載入 PowerShell 的本機電腦處理序，並對該處理序中的任意 Runspace 進行偵錯。

### <a name="runspace-debugging"></a>Runspace 偵錯

已新增新的 Cmdlet，可讓您列出處理序中目前的 Runspace，並將 PowerShell 主控台或 PowerShell ISE 偵錯工具附加至該 Runspace，以進行指令碼偵錯：

- Get-Runspace
- Debug-Runspace
- Enable-RunspaceDebug
- Disable-RunspaceDebug
- Get-RunspaceDebug

### <a name="attach-to-process-hosting-powershell"></a>附加至裝載 PowerShell 的處理程序

您現在可以附加至任何已載入 PowerShell 的電腦處理序。 您可以進入與主機處理序的互動式工作階段，來執行此動作。 如需詳細資訊，請參閱

- [Enter-PSHostProcess](/powershell/module/Microsoft.PowerShell.Core/Enter-PSHostProcess)
- [Exit-PSHostProcess](/powershell/module/Microsoft.PowerShell.Core/Exit-PSHostProcess)
