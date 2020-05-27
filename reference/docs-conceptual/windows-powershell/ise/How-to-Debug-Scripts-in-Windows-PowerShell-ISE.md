---
ms.date: 01/02/2020
keywords: powershell,cmdlet
title: 如何在 Windows PowerShell ISE 中偵錯指令碼
ms.openlocfilehash: 6fbe340cbff832b5d0e2a5515ef432cec574a3c1
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809344"
---
# <a name="how-to-debug-scripts-in-windows-powershell-ise"></a>如何在 Windows PowerShell ISE 中偵錯指令碼

本文章說明如何使用 Windows PowerShell 整合式指令碼環境 (ISE) 視覺化偵錯功能，對本機電腦上的指令碼執行偵錯。

## <a name="how-to-manage-breakpoints"></a>如何管理中斷點

中斷點是您要在指令碼中暫停作業的指定位置，以便您可以檢查變數及指令碼執行所在之環境的目前狀態。
在中斷點暫停指令碼之後，您可以在主控台窗格中執行命令，以檢查指令碼的狀態。 您可以輸出變數或執行其他命令。 您甚至可以修改目前執行中指令碼內容所顯示的任何變數值。 檢查您要查看的項目之後，您可以繼續指令碼作業。

您可以在 Windows PowerShell 偵錯環境中，設定三種中斷點類型︰

1. **行中斷點**： 在指令碼作業期間，當到達指定的行時，就會暫停指令碼

1. **變數中斷點。** 當指定的變數值變更時，指令碼就會暫停。

1. **命令中斷點。** 在指令碼作業期間，當指定的命令即將執行時，就會暫停指令碼。 它可以包含參數，以進一步將中斷點篩選到您需要的唯一作業。 此命令也可以是您已建立的函式。

在 Windows PowerShell ISE 偵錯環境中，只有行中斷點可以使用功能表或鍵盤快速鍵來設定。 另有其他兩種中斷點類型可供設定，但必須使用 [Set-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Set-PSBreakpoint) Cmdlet 從 [主控台] 設定。 本節說明如何使用功能表 (可用時) 在 Windows PowerShell ISE 中執行偵錯工作，並從主控台窗格中使用指令碼執行更廣泛的命令。

### <a name="to-set-a-breakpoint"></a>設定中斷點

只有在儲存指令碼之後，才能在其中設定中斷點。 以滑鼠右鍵按一下您要設定行中斷點的行，然後按一下 [切換中斷點]  。 或者，按一下您要設定行中斷點的行，然後按 <kbd>F9</kbd> 鍵，或在 **[偵錯]** 功能表上，按一下 **[切換中斷點]** 。

下列指令碼示範如何從主控台窗格使用 [Set-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Set-PSBreakpoint) Cmdlet 設定變數中斷點。

```powershell
# This command sets a breakpoint on the Server variable in the Sample.ps1 script.
Set-PSBreakpoint -Script sample.ps1 -Variable Server
```

### <a name="list-all-breakpoints"></a>列出所有中斷點

顯示目前 Windows PowerShell 工作階段中的所有中斷點。

在 **[偵錯]** 功能表上，按一下 **[列出中斷點]** 。 下列指令碼示範如何從主控台窗格使用 [Get-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Get-PSBreakpoint) Cmdlet 列出所有中斷點。

```powershell
# This command lists all breakpoints in the current session.
Get-PSBreakpoint
```

### <a name="remove-a-breakpoint"></a>移除中斷點

移除中斷點會將它刪除。

如果您認為稍後可能需要再度使用，請考慮改為[停用中斷點](#disable-a-breakpoint)。 以滑鼠右鍵按一下您要移除中斷點的行，然後按一下 [切換中斷點]  。
或者，按一下您要移除中斷點的行，然後在 **[偵錯]** 功能表上，按一下 **[切換中斷點]** 。 下列指令碼示範如何從主控台窗格使用 [Remove-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Remove-PSBreakpoint) Cmdlet 移除具有指定識別碼的中斷點。

```powershell
# This command deletes the breakpoint with breakpoint ID 2.
Remove-PSBreakpoint -Id 2
```

### <a name="remove-all-breakpoints"></a>移除所有中斷點

若要移除目前工作階段中定義的所有中斷點，請在 **[偵錯]** 功能表上，按一下 **[移除所有中斷點]** 。

下列指令碼示範如何從主控台窗格使用 [Remove-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Remove-PSBreakpoint) Cmdlet 移除所有中斷點。

```powershell
# This command deletes all of the breakpoints in the current session.
Get-PSBreakpoint | Remove-PSBreakpoint
```

### <a name="disable-a-breakpoint"></a>停用中斷點

停用中斷點不會將它移除，而是將它關閉直到再次啟用為止。 若要停用特定行中斷點，請以滑鼠右鍵按一下您要停用中斷點的行，然後按一下 [停用中斷點]  。 或者，按一下您要停用中斷點的行，然後按 <kbd>F9</kbd> 鍵，或在 **[偵錯]** 功能表上，按一下 **[停用中斷點]** 。 下列指令碼示範如何從主控台窗格使用 [Disable-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Disable-PSBreakpoint) Cmdlet 移除具有指定識別碼的中斷點。

```powershell
# This command disables the breakpoint with breakpoint ID 0.
Disable-PSBreakpoint -Id 0
```

### <a name="disable-all-breakpoints"></a>停用所有中斷點

停用中斷點不會將它移除，而是將它關閉直到再次啟用為止。 若要停用目前工作階段中的所有中斷點，請在 **[偵錯]** 功能表上，按一下 **[停用所有中斷點]** 。 下列指令碼示範如何從主控台窗格使用 [Disable-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Disable-PSBreakpoint) Cmdlet 來停用所有中斷點。

```powershell
# This command disables all breakpoints in the current session.
# You can abbreviate this command as: "gbp | dbp".
Get-PSBreakpoint | Disable-PSBreakpoint
```

### <a name="enable-a-breakpoint"></a>啟用中斷點

若要啟用特定中斷點，請以滑鼠右鍵按一下您要啟用中斷點的行，然後按一下 [啟用中斷點]  。 或者，按一下您要啟用中斷點的行，然後按 <kbd>F9</kbd> 鍵，或在 **[偵錯]** 功能表上，按一下 **[啟用中斷點]** 。 下列指令碼示範如何從主控台窗格使用 [Enable-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Enable-PSBreakpoint) Cmdlet 來啟用特定中斷點。

```powershell
# This command enables breakpoints with breakpoint IDs 0, 1, and 5.
Enable-PSBreakpoint -Id 0, 1, 5
```

### <a name="enable-all-breakpoints"></a>啟用所有中斷點

若要啟用目前工作階段中定義的所有中斷點，請在 **[偵錯]** 功能表上，按一下 **[啟用所有中斷點]** 。 下列指令碼示範如何從主控台窗格使用 [Enable-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Enable-PSBreakpoint) Cmdlet 啟用所有中斷點。

```powershell
# This command enables all breakpoints in the current session.
# You can abbreviate the command by using their aliases: "gbp | ebp".
Get-PSBreakpoint | Enable-PSBreakpoint
```

## <a name="how-to-manage-a-debugging-session"></a>如何管理偵錯工作階段

開始偵錯之前，您必須設定一或多個中斷點。 您必須儲存要偵錯的指令碼，才能設定中斷點。 如需如何設定中斷點的指示，請參閱[如何管理中斷點](#how-to-manage-breakpoints)或 [Set-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Set-PSBreakpoint)。
開始偵錯之後，直到停止偵錯為止，都無法編輯指令碼。 已設定一或多個中斷點的指令碼會自動儲存後再執行。

### <a name="to-start-debugging"></a>開始偵錯

按 <kbd>F5</kbd> 鍵；按一下工具列中的**執行指令碼**圖示；或在 [偵錯]  功能表上，按一下 [執行/繼續]  。 指令碼會執行，直到它遇到第一個中斷點為止。 然後它會在此暫停作業，並反白暫停的行。

### <a name="to-continue-debugging"></a>繼續偵錯

請執行下列其中一個動作：按 <kbd>F5</kbd> 鍵、按一下工具列中的**執行指令碼**圖示、在 [偵錯]  功能表上，按一下 [執行/繼續]  、在主控台窗格中輸入 `C`，然後按 <kbd>ENTER</kbd>。 這會使指令碼繼續執行到下一個中斷點，或到指令碼結尾 (如果未遇到任何其他中斷點)。

### <a name="to-view-the-call-stack"></a>檢視呼叫堆疊

呼叫堆疊會顯示指令碼中的目前執行位置。 如果指令碼在由其他函式呼叫的函式中執行，則會在顯示中以輸出的其他資料列來表示其他函式。 最底端的資料列顯示原始指令碼及其中用來呼叫函式的行。 上一行顯示該函式及其中可能用來呼叫其他函式的行。 最頂端的資料列顯示設定中斷點之目前行的目前內容。

若要在暫停期間查看目前的呼叫堆疊，請執行下列其中一個動作：按 <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>、在 [偵錯]  功能表上，按一下 [顯示呼叫堆疊]  、在主控台窗格中輸入 `K`，然後按 <kbd>ENTER</kbd>。

### <a name="to-stop-debugging"></a>停止偵錯

請執行下列其中一個動作：按 <kbd>SHIFT</kbd>+<kbd>F5</kbd>、在 [偵錯]  功能表上，按一下 [停止偵錯工具]  、在主控台窗格中輸入 `Q`，然後按 <kbd>ENTER</kbd>。

## <a name="how-to-step-over-step-into-and-step-out-while-debugging"></a>如何在偵錯時逐程序、逐步執行及跳出

逐步執行是一次執行一個陳述式的程序。 您可以在某行程式碼停止，然後檢查變數值和系統狀態。 下表說明常見的偵錯工作，例如逐程序、逐步執行及跳出。

| 偵錯工作 |                                                                                                                   描述                                                                                                                    |                                                      如何在 PowerShell ISE 中完成                                                       |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| **逐步執行**  | 執行目前的陳述式，然後在下一個陳述式停止。 如果目前的陳述式是函式或指令碼呼叫，則偵錯工具會逐步執行該函式或指令碼，否則會在下一個陳述式停止。                      | 請執行下列其中一個動作：按 <kbd>F11</kbd>、在 [偵錯]  功能表上，按一下 [逐步執行]  、在主控台窗格中輸入 `S`，然後按 <kbd>ENTER</kbd>。                 |
| **逐程序**  | 執行目前的陳述式，然後在下一個陳述式停止。 如果目前的陳述式是函式或指令碼呼叫，則偵錯工具會執行整個函式或指令碼，並在函式呼叫後於下一個陳述式停止。 | 請執行下列其中一個動作：按 <kbd>F10</kbd>、在 [偵錯]  功能表上，按一下 [不進入函數]  、在主控台窗格中輸入 `V`，然後按 <kbd>ENTER</kbd>。                 |
| **跳出**   | 移離目前的函式，並在函式為巢狀時移到上一層。 如果在主體中，指令碼會執行到結尾，或到下一個中斷點。 這會執行已跳過的陳述式，但不會逐步執行。                   | 請執行下列其中一個動作：<kbd>SHIFT</kbd>+<kbd>F11</kbd>、在 [偵錯]  功能表上，按一下 [跳離]  、在主控台窗格中輸入 `O`，然後按 <kbd>ENTER</kbd>。 |
| **繼續**   | 繼續執行到結尾，或到下一個中斷點。 這會執行已跳過的函式和引動過程，但不會逐步執行。                                                                                                          | 請執行下列其中一個動作：按 <kbd>F5</kbd>、在 [偵錯]  功能表上，按一下 [執行/繼續]  、在主控台窗格中輸入 `C`，然後按 <kbd>ENTER</kbd>。               |

## <a name="how-to-display-the-values-of-variables-while-debugging"></a>如何在偵錯時顯示變數的值

當您逐步執行程式碼時，您可以顯示指令碼中變數的目前值。

### <a name="to-display-the-values-of-standard-variables"></a>顯示標準變數的值

請使用下列其中一個方法：

- 在指令碼窗格中，將游標移到變數上，以工具提示顯示其值。

- 在主控台窗格中輸入變數名稱，然後按 <kbd>ENTER</kbd> 鍵。

ISE 中的所有窗格一律會在相同範圍內。 因此，當您對指令碼進行偵錯時，您在主控台窗格中輸入的命令會在指令碼範圍內執行。 這可讓您使用主控台窗格尋找變數的值，然後只呼叫指令碼中定義的函式。

### <a name="to-display-the-values-of-automatic-variables"></a>顯示自動變數的值

您可以使用上述方法，在對指令碼進行偵錯時顯示幾乎所有變數的值。 不過，這些方法不適用於下列自動變數。

- `$_`

- `$Input`

- `$MyInvocation`

- `$PSBoundParameters`

- `$Args`

如果您嘗試顯示上述任何變數的值，您會取得偵錯工具所使用之內部管線中的變數值，而不是指令碼中的變數值。 您可以對一些變數 (`$_`、`$Input`、`$MyInvocation`、`$PSBoundParameters` 和 `$Args`) 使用下列方法，來解決此問題：

1. 在指令碼中，將自動變數的值指派給新變數。

1. 將游標移到指令碼窗格中的新變數上，或在主控台窗格中輸入新變數，以顯示新變數的值。

例如，若要顯示指令碼中的 `$MyInvocation` 變數值，請將該值指派給新變數 (例如 `$scriptName`)，然後將游標移到 `$scriptName` 變數上或輸入該變數，以顯示其值。

```powershell
# In C:\ps-test\MyScript.ps1
$scriptName = $MyInvocation.MyCommand.Path
```

```PowerShell
# In the Console Pane:
.\MyScript.ps1
$scriptName
```

```Output
C:\ps-test\MyScript.ps1
```

## <a name="see-also"></a>另請參閱

[探索 Windows PowerShell ISE](exploring-the-windows-powershell-ise.md)
