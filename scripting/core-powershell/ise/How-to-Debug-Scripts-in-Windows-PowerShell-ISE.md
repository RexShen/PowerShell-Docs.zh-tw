---
title: 如何在 Windows PowerShell ISE 中偵錯指令碼
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6dc6d8f9-8978-46e9-a92f-169af37e2817
---
# 如何在 Windows PowerShell ISE 中偵錯指令碼
本主題說明如何使用 Windows PowerShell® 整合式指令碼環境 (ISE) 視覺化偵錯功能，對本機電腦上的指令碼進行偵錯。

[如何管理中斷點](#bkmk_1)
[如何管理偵錯工作階段](#bkmk_2)
[如何在偵錯時逐程序、逐步執行及跳出](#bkmk_3)
[如何在偵錯時顯示變數的值](#bkmk_4)

## <a name="bkmk_1"></a>如何管理中斷點
中斷點是您要在指令碼中暫停作業的指定位置，以便您可以檢查變數及指令碼執行所在之環境的目前狀態。 在中斷點暫停指令碼之後，您可以在主控台窗格中執行命令，以檢查指令碼的狀態。  您可以輸出變數或執行其他命令。 您甚至可以修改目前執行中指令碼內容所顯示的任何變數值。 檢查您要查看的項目之後，您可以繼續指令碼作業。

您可以在 Windows PowerShell 偵錯環境中，設定三種中斷點類型︰

1.  **行中斷點**： 在指令碼作業期間，當到達指定的行時，就會暫停指令碼

2.  **變數中斷點：** 當指定的變數值變更時，就會暫停指令碼。

3.  **命令中斷點：** 在指令碼作業期間，當指定的命令即將執行時，就會暫停指令碼。 它可以包含參數，以進一步將中斷點篩選到您需要的唯一作業。 此命令也可以是您已建立的函式。

在 Windows PowerShell ISE 偵錯環境中，只有行中斷點可以使用功能表或鍵盤快速鍵來設定。 您也可以設定其他兩種中斷點類型，但會從主控台窗格使用 [Set-PSBreakpoint [m2]](https://technet.microsoft.com/en-us/library/88d2d9ad-17dc-44ae-99aa-f841125b9dc8) Cmdlet 進行設定。 本節說明如何使用功能表 (可用時) 在 Windows PowerShell ISE 中執行偵錯工作，並從主控台窗格中使用指令碼執行更廣泛的命令。

### 設定中斷點
只有在儲存指令碼之後，才能在其中設定中斷點。 以滑鼠右鍵按一下您要設定行中斷點的行，然後按一下 **[切換中斷點]**。 或者，按一下要設定行中斷點的行，然後按 **F9** 鍵，或者在 [偵錯] 功能表上，按一下 [切換中斷點].

下列指令碼示範如何從主控台窗格使用 [Set-PSBreakpoint](https://technet.microsoft.com/en-us/library/6afd5d2c-a285-4796-8607-3cbf49471420) Cmdlet 設定變數中斷點。

```
# This command sets a breakpoint on the Server variable in the Sample.ps1 script.
set-psbreakpoint -script sample.ps1 -variable Server
```

### 列出所有中斷點
顯示目前 Windows PowerShell® 工作階段中的所有中斷點。

在 **[偵錯]** 功能表上，按一下 **[列出中斷點]**。 下列指令碼示範如何從主控台窗格使用 [Get-PSBreakpoint](https://technet.microsoft.com/en-us/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) Cmdlet 列出所有中斷點。

```
# This command lists all breakpoints in the current session. 
get-psbreakpoint
```

### 移除中斷點
移除中斷點會將它刪除。  如果您認為稍後可能需要重複使用，請考慮改為將它[停用](#bkmk_disable)。  以滑鼠右鍵按一下您要移除中斷點的行，然後按一下 **[切換中斷點]**。 或者，按一下您要移除中斷點的行，然後在 **[偵錯]** 功能表上，按一下 **[切換中斷點]**。 下列指令碼示範如何從主控台窗格使用 [Remove-PSBreakpoint](https://technet.microsoft.com/en-us/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) Cmdlet 移除具有指定識別碼的中斷點。

```
# This command deletes the breakpoint with breakpoint ID 2.
remove-psbreakpoint -id 2
```

### 移除所有中斷點
若要移除目前工作階段中定義的所有中斷點，可在 [偵錯] 功能表上，按一下 [移除所有中斷點].

下列指令碼示範如何從主控台窗格使用 [Remove-PSBreakpoint](https://technet.microsoft.com/en-us/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) Cmdlet 移除所有中斷點。

```
# This command deletes all of the breakpoints in the current session.
get-breakpoint | remove-breakpoint
```

### <a name="bkmk_disable"></a>停用中斷點
停用中斷點不會將它移除，而是將它關閉直到再次啟用為止。  若要停用特定行中斷點，請以滑鼠右鍵按一下您要停用中斷點的行，然後按一下 **[停用中斷點]**。 或者，按一下您要停用中斷點的行，然後按 **F9** 鍵，或在 **[偵錯]** 功能表上，按一下 **[停用中斷點]**。 下列指令碼示範如何從主控台窗格使用 [Disable-PSBreakpoint](https://technet.microsoft.com/en-us/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) Cmdlet 移除具有指定識別碼的中斷點。

```
# This command disables the breakpoint with breakpoint ID 0.
disable-psbreakpoint -id 0
```

### 停用所有中斷點
停用中斷點不會將它移除，而是將它關閉直到再次啟用為止。  若要停用目前工作階段中的所有中斷點，請在 **[偵錯]** 功能表上，按一下 **[停用所有中斷點]**。 下列指令碼示範如何從主控台窗格使用 [Disable-PSBreakpoint](https://technet.microsoft.com/en-us/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) Cmdlet 來停用所有中斷點。

```
# This command disables all breakpoints in the current session. 
# You can abbreviate this command as: "gbp | dbp".
get-psbreakpoint | disable-psbreakpoint
```

### 啟用中斷點
若要啟用特定中斷點，請以滑鼠右鍵按一下您要啟用中斷點的行，然後按一下 **[啟用中斷點]**。 或者，按一下您要啟用中斷點的行，然後按 **F9** 鍵，或在 **[偵錯]** 功能表上，按一下 **[啟用中斷點]**。 下列指令碼示範如何從主控台窗格使用 [Enable-PSBreakpoint](https://technet.microsoft.com/en-us/library/739e1091-3b3f-405f-a428-bec7543e5df0) Cmdlet 來啟用特定中斷點。

```
# This command enables breakpoints with breakpoint IDs 0, 1, and 5.
enable-psbreakpoint -id 0, 1, 5
```

### 啟用所有中斷點
若要啟用目前工作階段中定義的所有中斷點，請在 **[偵錯]** 功能表上，按一下 **[啟用所有中斷點]**。 下列指令碼示範如何從主控台窗格使用 [Enable-PSBreakpoint](https://technet.microsoft.com/en-us/library/739e1091-3b3f-405f-a428-bec7543e5df0) Cmdlet 啟用所有中斷點。

```
# This command enables all breakpoints in the current session. 
# You can abbreviate the command by using their aliases: "gbp | ebp".
get-psbreakpoint | enable-psbreakpoint
```

## <a name="bkmk_2"></a>如何管理偵錯工作階段
開始偵錯之前，您必須設定一或多個中斷點。 您必須儲存要偵錯的指令碼，才能設定中斷點。 如需如何設定中斷點的指示，請參閱[如何管理中斷點](#bkmk_1)或 [Set-PSBreakpoint](https://technet.microsoft.com/en-us/library/6afd5d2c-a285-4796-8607-3cbf49471420)。 開始偵錯之後，直到停止偵錯為止，都無法編輯指令碼。 已設定一或多個中斷點的指令碼會自動儲存後再執行。

### 開始偵錯
按 **F5** 鍵；按一下工具列中的**執行指令碼**圖示；或在 **[偵錯]** 功能表上，按一下 **[執行/繼續]**。 指令碼會執行，直到它遇到第一個中斷點為止。 然後它會在此暫停作業，並反白暫停的行。

### 繼續偵錯
請執行下列其中一個動作：按 **F5** 鍵、按一下工具列中的**執行指令碼**圖示、在 **[偵錯]** 功能表上，按一下 **[執行/繼續]**、在主控台窗格中輸入 **C**，然後按 **ENTER** 鍵。 這會使指令碼繼續執行到下一個中斷點，或到指令碼結尾 (如果未遇到任何其他中斷點)。

### 檢視呼叫堆疊
呼叫堆疊會顯示指令碼中的目前執行位置。 如果指令碼在由其他函式呼叫的函式中執行，則會在顯示中以輸出的其他資料列來表示其他函式。 最底端的資料列顯示原始指令碼及其中用來呼叫函式的行。 上一行顯示該函式及其中可能用來呼叫其他函式的行。  最頂端的資料列顯示設定中斷點之目前行的目前內容。

若要在暫停期間查看目前的呼叫堆疊，可以按 **CTRL+SHIFT+D**；在 [偵錯] 功能表上，按一下 [顯示呼叫堆疊]；或者，在主控台窗格中輸入 **K**，然後按 **ENTER** 鍵.

### 停止偵錯
按 **SHIFT-F5**；在 [偵錯] 功能表上，按一下 [停止偵錯工具]；或者，在主控台窗格中輸入 **Q**，然後按 **ENTER** 鍵.

## <a name="bkmk_3"></a>如何在偵錯時逐程序、逐步執行及跳出
逐步執行是一次執行一個陳述式的程序。 您可以在某行程式碼停止，然後檢查變數值和系統狀態。 下表說明常見的偵錯工作，例如逐程序、逐步執行及跳出。

||||
|-|-|-|
|**偵錯工作**|**描述**|**如何在 PowerShell ISE 中完成**|
|**逐步執行**|執行目前的陳述式，然後在下一個陳述式停止。 如果目前的陳述式是函式或指令碼呼叫，則偵錯工具會逐步執行該函式或指令碼，否則會在下一個陳述式停止。|按 **F11**；在 [偵錯] 功能表上，按一下 [逐步執行]；或者，在主控台窗格中輸入 **S**，然後按 **ENTER** 鍵.|
|**逐程序**|執行目前的陳述式，然後在下一個陳述式停止。 如果目前的陳述式是函式或指令碼呼叫，則偵錯工具會執行整個函式或指令碼，並在函式呼叫後於下一個陳述式停止。|按 **F10**；在 [偵錯] 功能表上，按一下 [逐程序]；或者，在主控台窗格中輸入 **V**，然後按 **ENTER** 鍵.|
|**跳出**|移離目前的函式，並在函式為巢狀時移到上一層。 如果在主體中，指令碼會執行到結尾，或到下一個中斷點。 這會執行已跳過的陳述式，但不會逐步執行。|按 **SHIFT+F11**；在 [偵錯] 功能表上，按一下 [跳出]；或者，在主控台窗格中輸入 **O**，然後按 **ENTER** 鍵.|
|**繼續**|繼續執行到結尾，或到下一個中斷點。 這會執行已跳過的函式和引動過程，但不會逐步執行。|按 **F5**；在 [偵錯] 功能表上，按一下 [執行/繼續]；或者，在主控台窗格中輸入 **C**，然後按 **ENTER** 鍵.|

## <a name="bkmk_4"></a>如何在偵錯時顯示變數的值
當您逐步執行程式碼時，您可以顯示指令碼中變數的目前值。

### 顯示標準變數的值
使用下列其中一個方法：

-   在指令碼窗格中，將游標移到變數上，以工具提示顯示其值。

-   在主控台窗格中輸入變數名稱，然後按 **ENTER** 鍵.

ISE 中的所有窗格一律會在相同範圍內。 因此，當您對指令碼進行偵錯時，您在主控台窗格中輸入的命令會在指令碼範圍內執行。 這可讓您使用主控台窗格尋找變數的值，然後只呼叫指令碼中定義的函式。

### 顯示自動變數的值
您可以使用上述方法，在對指令碼進行偵錯時顯示幾乎所有變數的值。 不過，這些方法不適用於下列自動變數。

-   $_

-   $Input

-   $MyInvocation

-   $PSBoundParameters

-   $Args

如果您嘗試顯示上述任何變數的值，您會取得偵錯工具所使用之內部管線中的變數值，而不是指令碼中的變數值。 您可以對一些變數 ($_、$Input、$MyInvocation、$PSBoundParameters 和 $Args) 使用下列方法，來解決此問題：

1.  在指令碼中，將自動變數的值指派給新變數。

2.  將游標移到指令碼窗格中的新變數上，或在主控台窗格中輸入新變數，以顯示新變數的值。

例如，若要顯示指令碼中的 $MyInvocation 變數值，請將該值指派給新變數 (例如 $scriptname)，然後將游標移到 $scriptname 變數上或輸入 $scriptname 變數，以顯示其值。

```
#In MyScript.ps1
$scriptname = $MyInvocation.MyCommand.Path

#In the Console Pane:
C:\ps-test> $scriptname
C:\ps-test\MyScript.ps1
```

## 另請參閱
[使用 Windows PowerShell ISE](Using-the-Windows-PowerShell-ISE.md)



<!--HONumber=May16_HO2-->


