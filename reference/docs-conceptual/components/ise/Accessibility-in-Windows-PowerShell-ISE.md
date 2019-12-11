---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Windows PowerShell ISE 的協助工具
ms.openlocfilehash: 416b18dd492ca04d98b5adf9f7f0f88ea495740a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030643"
---
# <a name="accessibility-in-windows-powershell-ise"></a>Windows PowerShell ISE 的協助工具

本主題說明 Windows PowerShell 整合式指令碼環境 (ISE) 的協助工具功能，對您來說可能很實用。

* [如何變更主控台和指令碼窗格的大小和位置](#how-to-change-the-size-and-location-of-the-console-and-script-panes)
* [編輯文字的鍵盤快速鍵](#keyboard-shortcuts-for-editing-text)
* [執行指令碼的鍵盤快速鍵](#keyboard-shortcuts-for-running-scripts)
* [自訂檢視的鍵盤快速鍵](#keyboard-shortcuts-for-customizing-the-view)
* [偵錯指令碼的鍵盤快速鍵](#keyboard-shortcuts-for-debugging-scripts)
* [Windows PowerShell 索引標籤的鍵盤快速鍵](#keyboard-shortcuts-for-windows-powershell-tabs)
* [開始和結束的鍵盤快速鍵](#keyboard-shortcuts-for-starting-and-exiting)

Microsoft 致力於讓所有使用者都能輕鬆使用其產品與服務。 下列主題提供可更方便殘障人士使用 Windows PowerShell ISE 的功能、產品及服務的相關資訊。

Windows PowerShell ISE 支援高對比模式。 對視覺障礙者來說，可透過 Cmdlet 使用中斷點資訊來管理中斷點，例如 [Get-PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) 和 [Set-PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420)。 如需詳細資訊，請參閱[如何在 Windows PowerShell ISE 中偵錯指令碼](How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md)的＜如何管理中斷點＞。 除了 Microsoft Windows 中的協助工具功能和公用程式之外，下列功能也可以讓 Windows PowerShell ISE 更方便殘障人士使用：

- 鍵盤快速鍵

- 語法著色表，以及可使用 [$psISE.Options](https://technet.microsoft.com/library/75e2a76f-f3d1-490b-ad5d-e3829946aabb) 指令碼物件修改其他多項色彩設定的功能。

- 文字大小變更

## <a name="how-to-change-the-size-and-location-of-the-console-and-script-panes"></a>如何變更主控台和指令碼窗格的大小和位置

您可以使用下列步驟來變更主控台窗格和指令碼窗格的位置和大小。 當您再次開啟 Windows PowerShell ISE 時，即會保留您所做的大小和位置變更。

### <a name="to-resize-the-script-pane-and-console-pane"></a>若要調整指令碼窗格和主控台窗格的大小

1. 將指標停在指令碼窗格和主控台窗格的分割線上。

2. 當滑鼠指標變成雙頭箭號時，拖曳框線以變更窗格的大小。

### <a name="to-move-the-script-pane-and-console-pane"></a>若要移動指令碼窗格和主控台窗格

執行下列其中一個動作：

- 若要將指令碼窗格移動到主控台窗格上方，請按 **CTRL+1**，或者按一下工具列的**靠上顯示指令碼窗格**圖示，或在 [檢視]  功能表中，按一下 [靠上顯示指令碼窗格]  。

- 若要將指令碼窗格移動到主控台窗格右方，請按 **CTRL+2**；或者，按一下工具列的 [靠右顯示指令碼窗格]  圖示，或在 [檢視]  功能表中，按一下 [靠右顯示指令碼窗格]  。

- 若要將指令碼窗格最大化，請按 **CTRL+3**；或者，按一下工具列的 [顯示最大化的指令碼窗格]  圖示，或在 [檢視]  功能表中，按一下 [顯示最大化的指令碼窗格]  。

- 若要將主控台窗格最大化，並將指令碼窗格隱藏在索引標籤資料列最右側，請按一下**隱藏指令碼窗格**圖示；或在 **[檢視]** 功能表中，按一下以取消選取 **[顯示指令碼窗格]** 功能表選項。

- 若要在主控台窗格最大化時顯示指令碼窗格，請按一下**顯示指令碼窗格**圖示；或在 **[檢視]** 功能表中，按一下以選取 **[顯示指令碼窗格]** 功能表選項。

## <a name="keyboard-shortcuts-for-editing-text"></a>編輯文字的鍵盤快速鍵

編輯文字時，您可以使用下列鍵盤快速鍵。

|動作|鍵盤快速鍵|使用位置|
|----------|----------------------|----------|
|**複製**|CTRL+C|指令碼窗格，主控台窗格|
|**剪下**|CTRL+X|指令碼窗格，主控台窗格|
|**在指令碼中尋找**|CTRL+F|指令碼窗格|
|**在指令碼中找下一個**|F3|指令碼窗格|
|**在指令碼中找上一個**|SHIFT+F3|指令碼窗格|
|**貼上**|CTRL+V|指令碼窗格，主控台窗格|
|**取消復原**|CTRL+Y|指令碼窗格，主控台窗格|
|**在指令碼中取代**|CTRL+H|指令碼窗格|
|**儲存**|CTRL+S|指令碼窗格|
|**全選**|CTRL+A|指令碼窗格，主控台窗格|
|**復原**|CTRL+Z|指令碼窗格，主控台窗格|

## <a name="keyboard-shortcuts-for-running-scripts"></a>執行指令碼的鍵盤快速鍵

在指令碼窗格中執行指令碼時，您可以使用下列鍵盤快速鍵。

|動作|鍵盤快速鍵|
|----------|---------------------|
|**新增**|CTRL+N|
|**開啟**|CTRL+O|
|**執行**|F5|
|**執行選取項目**|F8|
|**停止執行**|CTRL+BREAK 在內容明確 (未選取文字) 的情況下，可以使用 CTRL+C。|
|**Tab** (至下一個指令碼)|CTRL+TAB **注意：** Tab 至下一個指令碼僅適用於開啟單一 PowerShell 索引標籤的情況，或開啟多個 PowerShell 索引標籤但焦點是在指令碼窗格中的情況。|
|**Tab** (至上一個指令碼)|CTRL+SHIFT+TAB **注意：** Tab 至上一個指令碼僅適用於開啟單一 PowerShell 索引標籤的情況，或開啟多個 PowerShell 索引標籤但焦點是在指令碼窗格中的情況。|

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>自訂檢視的鍵盤快速鍵

您可以使用下列鍵盤快速鍵，在 Windows PowerShell ISE 中自訂檢視。 您可從應用程式的所有窗格存取這些快速鍵。

|動作|鍵盤快速鍵|
|----------|---------------------|
|**移至主控台窗格**|CTRL+D|
|**前往指令碼窗格**|CTRL+I|
|**顯示指令碼窗格**|CTRL+R|
|**隱藏指令碼窗格**|CTRL+R|
||
|**將指令碼窗格向上移**|CTRL+1|
|**將指令碼窗格向右移**|CTRL+2|
|**最大化指令碼窗格**|CTRL+3|
|**放大**|CTRL+加號|
|**縮小**|CTRL+減號|

## <a name="keyboard-shortcuts-for-debugging-scripts"></a>偵錯指令碼的鍵盤快速鍵

偵錯程式碼時，您可以使用下列鍵盤快速鍵。

|動作|鍵盤快速鍵|使用位置|
|----------|---------------------|----------|
|**執行/繼續**|F5|偵錯指令碼時的指令碼窗格|
|**逐步執行**|F11|偵錯指令碼時的指令碼窗格|
|**逐程序**|F10|偵錯指令碼時的指令碼窗格|
|**跳出**|SHIFT+F11|偵錯指令碼時的指令碼窗格|
|**顯示呼叫堆疊**|CTRL+SHIFT+D|偵錯指令碼時的指令碼窗格|
|**列出中斷點**|CTRL+SHIFT+L|偵錯指令碼時的指令碼窗格|
|**切換中斷點**|F9|偵錯指令碼時的指令碼窗格|
|**移除所有中斷點**|CTRL+SHIFT+F9|偵錯指令碼時的指令碼窗格|
|**停止偵錯工具**|SHIFT+F5|偵錯指令碼時的指令碼窗格|

> [!NOTE]
>
> 當您在 Windows PowerShell ISE 中進行指令碼偵錯時，也可以使用專為 Windows PowerShell 主控台設計的鍵盤快速鍵。 若要使用這些快速鍵，您必須在主控台窗格中輸入捷徑，然後按 ENTER 鍵。

|動作|鍵盤快速鍵|使用位置|
|----------|---------------------|----------|
|**繼續**|C|偵錯指令碼時的主控台窗格|
|**逐步執行**|S|偵錯指令碼時的主控台窗格|
|**逐程序**|V|偵錯指令碼時的主控台窗格|
|**跳出**|O|偵錯指令碼時的主控台窗格|
|**重複最後一個命令** (適用於逐步執行或逐程序)|ENTER|偵錯指令碼時的主控台窗格|
|**顯示呼叫堆疊**|K|偵錯指令碼時的主控台窗格|
|**停止偵錯**|Q|偵錯指令碼時的主控台窗格|
|**列出指令碼**|L|偵錯指令碼時的主控台窗格|
|**顯示主控台偵錯命令**|H 或 ?|偵錯指令碼時的主控台窗格|

## <a name="keyboard-shortcuts-for-windows-powershell-tabs"></a>Windows PowerShell 索引標籤的鍵盤快速鍵

使用 Windows PowerShell 索引標籤時，您可以使用下列鍵盤快速鍵。

|動作|鍵盤快速鍵|
|----------|---------------------|
|**關閉 PowerShell 索引標籤**|CTRL+W|
|**新增 PowerShell 索引標籤**|CTRL+T|
|**上一個 PowerShell 索引標籤**|CTRL+SHIFT+TAB 僅有當任何 PowerShell 索引標籤上沒有檔案開啟時，才適用這個快速鍵。|
|**下一個 Windows PowerShell 索引標籤**|CTRL+TAB 僅有當任何 PowerShell 索引標籤上沒有檔案開啟時，才適用這個快速鍵。|

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>開始和結束的鍵盤快速鍵

您可以使用下列鍵盤快速鍵，啟動 Windows PowerShell 主控台 (PowerShell.exe) 或結束 Windows PowerShell ISE。

|動作|鍵盤快速鍵|
|----------|---------------------|
|**結束**|ALT+F4|
|**啟動 PowerShell.exe** (Windows PowerShell 主控台)|CTRL+SHIFT+P|

## <a name="see-also"></a>另請參閱

[Windows PowerShell ISE 簡介](Introducing-the-Windows-PowerShell-ISE.md)
