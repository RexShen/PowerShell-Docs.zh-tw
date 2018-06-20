---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: 9ead27fd5d4f146e9062488c1c8cc22a073b922e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187097"
---
# <a name="improvements-in-powershell-script-debugging"></a>PowerShell 指令碼偵錯的增強功能

PowerShell 5.0 已改善數項功能，以增強偵錯經驗︰

## <a name="break-all"></a>全部中斷

PowerShell 主控台和 Windows PowerShell ISE 現在可讓您開始偵錯工具執行指令碼。 這在本機和遠端工作階段皆適用。

在主控台中，按 **Ctrl+Break**。

在 ISE 中，按 **Ctrl+B**，或使用 **[偵錯] -> [全部中斷]** 功能表命令。

## <a name="remote-debugging-and-remote-file-editing-in-windows-powershell-ise"></a>Windows PowerShell ISE 的遠端偵錯和遠端檔案編輯

Windows PowerShell ISE 現在可讓您執行 PSEdit 命令，在遠端工作階段中開啟及編輯檔案。
例如，您可以開啟檔案從遠端工作階段的命令列中進行編輯，如下所示︰

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

此外，您現在可以編輯並儲存遠端檔案的變更，當您點擊中斷點時遠端檔案就會自動在 Windows PowerShell ISE 中開啟。
現在，您可以偵錯在遠端電腦上執行的指令碼檔案、編輯檔案以修正錯誤，然後重新執行修改過的指令碼。

## <a name="advanced-script-debugging"></a>進階指令碼偵錯

有新的進階偵錯功能，可讓您附加至任何已載入 Windows PowerShell 的本機電腦處理程序，並偵錯該處理程序的任意 Runspace。

### <a name="runspace-debugging"></a>Runspace 偵錯

已加入新的 Cmdlet，可讓您列出處理程序目前的 Runspace，並將 Windows PowerShell 主控台或 ISE 偵錯工具附加至指令碼偵錯的 Runspace：

-   Get-Runspace
-   Debug-Runspace
-   Enable-RunspaceDebug
-   Disable-RunspaceDebug
-   Get-RunspaceDebug

### <a name="attach-to-process-hosting-powershell"></a>附加至裝載 PowerShell 的處理程序

您現在可以附加至已載入 Windows PowerShell 的任何電腦處理程序。 方法是：進入有此處理程序的互動式工作階段，類似執行 Enter-PSSession Cmdlet 進入互動遠端工作階段的方式：

-   Enter-PSHostProcess
-   Exit-PSHostProcess
