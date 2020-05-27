---
ms.date: 12/19/2019
keywords: powershell,cmdlet
title: Windows PowerShell ISE 的協助工具
ms.openlocfilehash: 89eff839d69fdbd5a1fa48b61dab627ef83f751b
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808514"
---
# <a name="accessibility-in-windows-powershell-ise"></a>Windows PowerShell ISE 的協助工具

本主題說明 Windows PowerShell 整合式指令碼環境 (ISE) 的協助工具功能，對您來說可能很實用。

- [如何變更主控台和指令碼窗格的大小和位置](#how-to-change-the-size-and-location-of-the-console-and-script-panes)
- [編輯文字的鍵盤快速鍵](#keyboard-shortcuts-for-editing-text)
- [執行指令碼的鍵盤快速鍵](#keyboard-shortcuts-for-running-scripts)
- [自訂檢視的鍵盤快速鍵](#keyboard-shortcuts-for-customizing-the-view)
- [偵錯指令碼的鍵盤快速鍵](#keyboard-shortcuts-for-debugging-scripts)
- [Windows PowerShell 索引標籤的鍵盤快速鍵](#keyboard-shortcuts-for-windows-powershell-tabs)
- [開始和結束的鍵盤快速鍵](#keyboard-shortcuts-for-starting-and-exiting)
- [使用 Cmdlet 進行中斷點管理](#breakpoint-management)

Microsoft 致力於讓所有使用者都能輕鬆使用其產品與服務。 下列主題提供可更方便殘障人士使用 Windows PowerShell ISE 的功能、產品及服務的相關資訊。

除了 Microsoft Windows 中的協助工具功能和公用程式之外，下列功能也可以讓 Windows PowerShell ISE 更方便殘障人士使用：

- 鍵盤快速鍵

- 語法著色表，以及可使用 [$psISE.Options](object-model/The-ISEOptions-Object.md) 指令碼物件修改其他多項色彩設定的功能。

- 文字大小變更

## <a name="how-to-change-the-size-and-location-of-the-console-and-script-panes"></a>如何變更主控台和指令碼窗格的大小和位置

您可以使用下列步驟來變更主控台窗格和指令碼窗格的位置和大小。 當您再次開啟 Windows PowerShell ISE 時，即會保留您所做的大小和位置變更。

### <a name="to-resize-the-script-pane-and-console-pane"></a>若要調整指令碼窗格和主控台窗格的大小

1. 將指標停在指令碼窗格和主控台窗格的分割線上。

2. 當滑鼠指標變成雙頭箭號時，拖曳框線以變更窗格的大小。

### <a name="to-move-the-script-pane-and-console-pane"></a>若要移動指令碼窗格和主控台窗格

執行下列其中一個動作：

- 若要將指令碼窗格移動到主控台窗格上方，請按 <kbd>CTRL</kbd>+<kbd>1</kbd>，或者按一下工具列的靠上的**顯示指令碼窗格**圖示，或在 [檢視]  功能表中，按一下 [靠上顯示指令碼窗格]  。

- 若要將指令碼窗格移動到主控台窗格右方，請按 <kbd>CTRL</kbd>+<kbd>2</kbd>，或者按一下工具列的**靠右顯示指令碼窗格**圖示，或在 [檢視]  功能表中，按一下 [靠右顯示指令碼窗格]  。

- 若要將指令碼窗格最大化，請按<kbd>CTRL</kbd>+<kbd>3</kbd>，或者按一下工具列的**顯示最大化的指令碼窗格**圖示，或在 [檢視]  功能表中，按一下 [顯示最大化的指令碼窗格]  。

- 若要將主控台窗格最大化，並將指令碼窗格隱藏在索引標籤資料列最右側，請按一下**隱藏指令碼窗格**圖示；或在 **[檢視]** 功能表中，按一下以取消選取 **[顯示指令碼窗格]** 功能表選項。

- 若要在主控台窗格最大化時顯示指令碼窗格，請按一下**顯示指令碼窗格**圖示；或在 **[檢視]** 功能表中，按一下以選取 **[顯示指令碼窗格]** 功能表選項。

## <a name="keyboard-shortcuts-for-editing-text"></a>編輯文字的鍵盤快速鍵

編輯文字時，您可以使用下列鍵盤快速鍵。

|           動作            |       鍵盤快速鍵       |          使用位置           |
| --------------------------- | ------------------------------ | ------------------------- |
| **複製**                    | <kbd>CTRL</kbd>+<kbd>C</kbd>   | 指令碼窗格，主控台窗格 |
| **剪下**                     | <kbd>CTRL</kbd>+<kbd>X</kbd>   | 指令碼窗格，主控台窗格 |
| **在指令碼中尋找**          | <kbd>CTRL</kbd>+<kbd>F</kbd>   | 指令碼窗格               |
| **在指令碼中找下一個**     | <kbd>F3</kbd>                  | 指令碼窗格               |
| **在指令碼中找上一個** | <kbd>SHIFT</kbd>+<kbd>F3</kbd> | 指令碼窗格               |
| **貼上**                   | <kbd>CTRL</kbd>+<kbd>V</kbd>   | 指令碼窗格，主控台窗格 |
| **取消復原**                    | <kbd>CTRL</kbd>+<kbd>Y</kbd>   | 指令碼窗格，主控台窗格 |
| **在指令碼中取代**       | <kbd>CTRL</kbd>+<kbd>H</kbd>   | 指令碼窗格               |
| **儲存**                    | <kbd>CTRL</kbd>+<kbd>S</kbd>   | 指令碼窗格               |
| **全選**              | <kbd>CTRL</kbd>+<kbd>A</kbd>   | 指令碼窗格，主控台窗格 |
| **復原**                    | <kbd>CTRL</kbd>+<kbd>Z</kbd>   | 指令碼窗格，主控台窗格 |

## <a name="keyboard-shortcuts-for-running-scripts"></a>執行指令碼的鍵盤快速鍵

在指令碼窗格中執行指令碼時，您可以使用下列鍵盤快速鍵。

|            動作            |                                                                                                     鍵盤快速鍵                                                                                                      |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **新增**                      | <kbd>CTRL</kbd>+<kbd>N</kbd>                                                                                                                                                                                               |
| **開啟**                     | <kbd>CTRL</kbd>+<kbd>O</kbd>                                                                                                                                                                                               |
| **執行**                      | <kbd>F5</kbd>                                                                                                                                                                                                              |
| **執行選取項目**            | <kbd>F8</kbd>                                                                                                                                                                                                              |
| **停止執行**           | <kbd>CTRL</kbd>+<kbd>BREAK</kbd>。 在內容明確 (未選取文字) 的情況下，可以使用 <kbd>CTRL</kbd>+<kbd>C</kbd>。                                                                               |
| **Tab** (至下一個指令碼)     | <kbd>CTRL</kbd>+<kbd>TAB</kbd> **注意：** Tab 至下一個指令碼僅適用於開啟單一 PowerShell 索引標籤的情況，或開啟多個 PowerShell 索引標籤但焦點是在指令碼窗格中的情況。                |
| **Tab** (至上一個指令碼) | <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>TAB</kbd> **注意：** Tab 至上一個指令碼僅適用於開啟單一 PowerShell 索引標籤的情況，或開啟多個 PowerShell 索引標籤但焦點是在指令碼窗格中的情況。 |

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>自訂檢視的鍵盤快速鍵

您可以使用下列鍵盤快速鍵，在 Windows PowerShell ISE 中自訂檢視。 您可從應用程式的所有窗格存取這些快速鍵。

|           動作           |         鍵盤快速鍵        |
| -------------------------- | -------------------------------- |
| **移至主控台窗格**     | <kbd>CTRL</kbd>+<kbd>D</kbd>     |
| **前往指令碼窗格**      | <kbd>CTRL</kbd>+<kbd>I</kbd>     |
| **顯示指令碼窗格**       | <kbd>CTRL</kbd>+<kbd>R</kbd>     |
| **隱藏指令碼窗格**       | <kbd>CTRL</kbd>+<kbd>R</kbd>     |
| **將指令碼窗格移至上方**    | <kbd>CTRL</kbd>+<kbd>1</kbd>     |
| **將指令碼窗格移至右方** | <kbd>CTRL</kbd>+<kbd>2</kbd>     |
| **最大化指令碼窗格**   | <kbd>CTRL</kbd>+<kbd>3</kbd>     |
| **放大**                | <kbd>CTRL</kbd>+<kbd>PLUS</kbd>  |
| **縮小**               | <kbd>CTRL</kbd>+<kbd>MINUS</kbd> |

## <a name="keyboard-shortcuts-for-debugging-scripts"></a>偵錯指令碼的鍵盤快速鍵

偵錯程式碼時，您可以使用下列鍵盤快速鍵。

|           動作           |               鍵盤快速鍵                |                使用位置                |
| -------------------------- | ---------------------------------------------- | ------------------------------------ |
| **執行/繼續**           | <kbd>F5</kbd>                                  | 偵錯指令碼時的指令碼窗格 |
| **逐步執行**              | <kbd>F11</kbd>                                 | 偵錯指令碼時的指令碼窗格 |
| **逐程序**              | <kbd>F10</kbd>                                 | 偵錯指令碼時的指令碼窗格 |
| **跳出**               | <kbd>SHIFT</kbd>+<kbd>F11</kbd>                | 偵錯指令碼時的指令碼窗格 |
| **顯示呼叫堆疊**     | <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>  | 偵錯指令碼時的指令碼窗格 |
| **列出中斷點**       | <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>L</kbd>  | 偵錯指令碼時的指令碼窗格 |
| **切換中斷點**      | <kbd>F9</kbd>                                  | 偵錯指令碼時的指令碼窗格 |
| **移除所有中斷點** | <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>F9</kbd> | 偵錯指令碼時的指令碼窗格 |
| **停止偵錯工具**          | <kbd>SHIFT</kbd>+<kbd>F5</kbd>                 | 偵錯指令碼時的指令碼窗格 |

> [!NOTE]
> 當您在 Windows PowerShell ISE 中進行指令碼偵錯時，也可以使用專為 Windows PowerShell 主控台設計的鍵盤快速鍵。 若要使用這些快速鍵，您必須在主控台窗格中輸入捷徑，然後按 <kbd>ENTER</kbd> 鍵。

|                 動作                  |      鍵盤快速鍵       |                使用位置                 |
| --------------------------------------- | ---------------------------- | ------------------------------------- |
| **繼續**                            | <kbd>C</kbd>                 | 偵錯指令碼時的主控台窗格 |
| **逐步執行**                           | <kbd>S</kbd>                 | 偵錯指令碼時的主控台窗格 |
| **逐程序**                           | <kbd>V</kbd>                 | 偵錯指令碼時的主控台窗格 |
| **跳出**                            | <kbd>O</kbd>                 | 偵錯指令碼時的主控台窗格 |
| **重複最後一個命令** (逐步執行或不進入函數) | <kbd>ENTER</kbd>             | 偵錯指令碼時的主控台窗格 |
| **顯示呼叫堆疊**                  | <kbd>K</kbd>                 | 偵錯指令碼時的主控台窗格 |
| **停止偵錯**                      | <kbd>Q</kbd>                 | 偵錯指令碼時的主控台窗格 |
| **列出指令碼**                     | <kbd>L</kbd>                 | 偵錯指令碼時的主控台窗格 |
| **顯示主控台偵錯命令**  | <kbd>H</kbd> 或 <kbd>?</kbd> | 偵錯指令碼時的主控台窗格 |

## <a name="keyboard-shortcuts-for-windows-powershell-tabs"></a>Windows PowerShell 索引標籤的鍵盤快速鍵

使用 Windows PowerShell 索引標籤時，您可以使用下列鍵盤快速鍵。

|             動作              |                                 鍵盤快速鍵                                  |
| ------------------------------- | ---------------------------------------------------------------------------------- |
| **關閉 PowerShell 索引標籤**        | <kbd>CTRL</kbd>+<kbd>W</kbd>                                                       |
| **新增 PowerShell 索引標籤**          | <kbd>CTRL</kbd>+<kbd>T</kbd>                                                       |
| **上一個 PowerShell 索引標籤**     | <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>TAB</kbd> (任何 PowerShell 索引標籤上都沒有檔案開啟時才適用) |
| **下一個 Windows PowerShell 索引標籤** | <kbd>CTRL</kbd>+<kbd>TAB</kbd> (任何 PowerShell 索引標籤上都沒有檔案開啟時才適用) |

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>開始和結束的鍵盤快速鍵

您可以使用下列鍵盤快速鍵，啟動 Windows PowerShell 主控台 (**PowerShell.exe**) 或結束 Windows PowerShell ISE。

|                        動作                         |               鍵盤快速鍵               |
| ----------------------------------------------------- | --------------------------------------------- |
| **結束**                                              | <kbd>ALT</kbd>+<kbd>F4</kbd>                  |
| **啟動 PowerShell.exe** (Windows PowerShell 主控台) | <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>P</kbd> |

## <a name="breakpoint-management"></a>中斷點管理

對視覺障礙者來說，可透過 Cmdlet 使用中斷點資訊來管理中斷點，例如 [Get-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Get-PSBreakpoint) 和 [Set-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Set-PSBreakpoint)。 如需詳細資訊，請參閱[如何在 Windows PowerShell ISE 中偵錯指令碼](How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md)的＜如何管理中斷點＞。

## <a name="see-also"></a>另請參閱

[Windows PowerShell ISE 簡介](Introducing-the-Windows-PowerShell-ISE.md)
