---
ms.date: 01/02/2020
title: Windows PowerShell ISE 的鍵盤快速鍵
description: 此文章是 PowerShell ISE 中所使用的鍵盤快速鍵清單。
ms.openlocfilehash: d4e78c5e8e8e172ef3cdd30b0099d56ce6b6b01e
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94391199"
---
# <a name="keyboard-shortcuts-for-the-windows-powershell-ise"></a>Windows PowerShell ISE 的鍵盤快速鍵

使用下列鍵盤快速鍵，在 Windows PowerShell&reg; 整合式指令碼環境 (ISE) 中執行動作。 Windows PowerShell ISE 隨附於 Windows Server 和 Windows 用戶端作業系統，但也可當做 [Windows Management Framework 4.0 下載套件](https://go.microsoft.com/fwlink/?LinkID=293881)的一部分安裝到某些舊版的 Windows 作業系統。

## <a name="keyboard-shortcuts-for-editing-text"></a>編輯文字的鍵盤快速鍵

編輯文字時，您可以使用下列鍵盤快速鍵。

|              動作              |       鍵盤快速鍵       |                                                                                                                                                 使用位置                                                                                                                                                 |
| -------------------------------- | ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **說明**                         | <kbd>F1</kbd>                  | 指令碼窗格 **重要︰** 您可以指定 <kbd>F1</kbd> 說明是來自 docs.microsoft.com 或下載的說明 (請參閱 `Update-Help`)。 若要選取，請按一下 [工具]  、[選項]  ，然後在 [一般設定]  索引標籤上，設定或清除 [使用本機說明內容而非線上內容]  。 |
| **複製**                         | <kbd>CTRL</kbd>+<kbd>C</kbd>   | 指令碼窗格, 命令窗格, 輸出窗格                                                                                                                                                                                                                                                                 |
| **剪下**                          | <kbd>CTRL</kbd>+<kbd>X</kbd>   | 指令碼窗格, 命令窗格                                                                                                                                                                                                                                                                              |
| **展開或摺疊大綱** | <kbd>CTRL</kbd>+<kbd>M</kbd>   | 指令碼窗格                                                                                                                                                                                                                                                                                            |
| **在指令碼中尋找**               | <kbd>CTRL</kbd>+<kbd>F</kbd>   | 指令碼窗格                                                                                                                                                                                                                                                                                            |
| **在指令碼中找下一個**          | <kbd>F3</kbd>                  | 指令碼窗格                                                                                                                                                                                                                                                                                            |
| **在指令碼中找上一個**      | <kbd>SHIFT</kbd>+<kbd>F3</kbd> | 指令碼窗格                                                                                                                                                                                                                                                                                            |
| **尋找成對括弧**          | <kbd>CTRL</kbd>+<kbd>]</kbd>   | 指令碼窗格                                                                                                                                                                                                                                                                                            |
| **貼上**                        | <kbd>CTRL</kbd>+<kbd>V</kbd>   | 指令碼窗格, 命令窗格                                                                                                                                                                                                                                                                              |
| **取消復原**                         | <kbd>CTRL</kbd>+<kbd>Y</kbd>   | 指令碼窗格, 命令窗格                                                                                                                                                                                                                                                                              |
| **在指令碼中取代**            | <kbd>CTRL</kbd>+<kbd>H</kbd>   | 指令碼窗格                                                                                                                                                                                                                                                                                            |
| **儲存**                         | <kbd>CTRL</kbd>+<kbd>S</kbd>   | 指令碼窗格                                                                                                                                                                                                                                                                                            |
| **全選**                   | <kbd>CTRL</kbd>+<kbd>A</kbd>   | 指令碼窗格, 命令窗格, 輸出窗格                                                                                                                                                                                                                                                                 |
| **顯示程式碼片段**                | <kbd>CTRL</kbd>+<kbd>J</kbd>   | 指令碼窗格, 命令窗格                                                                                                                                                                                                                                                                              |
| **復原**                         | <kbd>CTRL</kbd>+<kbd>Z</kbd>   | 指令碼窗格, 命令窗格                                                                                                                                                                                                                                                                              |

## <a name="keyboard-shortcuts-for-running-scripts"></a>執行指令碼的鍵盤快速鍵

在指令碼窗格中執行指令碼時，您可以使用下列鍵盤快速鍵。

|            動作            |                                                                                                             鍵盤快速鍵                                                                                                             |
| ---------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **新增**                      | <kbd>CTRL</kbd>+<kbd>N</kbd>                                                                                                                                                                                                              |
| **開啟**                     | <kbd>CTRL</kbd>+<kbd>O</kbd>                                                                                                                                                                                                              |
| **執行**                      | <kbd>F5</kbd>                                                                                                                                                                                                                             |
| **執行選取項目**            | <kbd>F8</kbd>                                                                                                                                                                                                                             |
| **停止執行**           | <kbd>CTRL</kbd>+<kbd>BREAK</kbd>。 在內容明確 (未選取文字) 的情況下，可以使用 <kbd>CTRL</kbd>+<kbd>C</kbd>。                                                                                              |
| **Tab** (至下一個指令碼)     | <kbd>CTRL</kbd>+<kbd>TAB</kbd> **注意：** Tab 至下一個指令碼僅適用於開啟單一 Windows PowerShell 索引標籤的情況，或開啟多個 Windows PowerShell 索引標籤，但焦點是在指令碼窗格的情況。               |
| **Tab** (至上一個指令碼) | <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>TAB</kbd> **注意：** Tab 至上一個指令碼適用於只開啟一個 Windows PowerShell 索引標籤的情況，或開啟多個 Windows PowerShell 索引標籤，且焦點是在指令碼窗格的情況。 |

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>自訂檢視的鍵盤快速鍵

您可以使用下列鍵盤快速鍵，在 Windows PowerShell ISE 中自訂檢視。 您可從應用程式的所有窗格存取這些快速鍵。

|                        動作                         |               鍵盤快速鍵               |
| ----------------------------------------------------- | --------------------------------------------- |
| **移至命令 (v2) 或主控台 (v3 和更新版本) 窗格** | <kbd>CTRL</kbd>+<kbd>D</kbd>                  |
| **移至輸出窗格 (僅限 v2)**                       | <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>O</kbd> |
| **前往指令碼窗格**                                 | <kbd>CTRL</kbd>+<kbd>I</kbd>                  |
| **顯示指令碼窗格**                                  | <kbd>CTRL</kbd>+<kbd>R</kbd>                  |
| **隱藏指令碼窗格**                                  | <kbd>CTRL</kbd>+<kbd>R</kbd>                  |
| **將指令碼窗格移至上方**                               | <kbd>CTRL</kbd>+<kbd>1</kbd>                  |
| **將指令碼窗格移至右方**                            | <kbd>CTRL</kbd>+<kbd>2</kbd>                  |
| **最大化指令碼窗格**                              | <kbd>CTRL</kbd>+<kbd>3</kbd>                  |
| **放大**                                           | <kbd>CTRL</kbd>+<kbd>+</kbd>                  |
| **縮小**                                          | <kbd>CTRL</kbd>+<kbd>-</kbd>                  |

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
> 當您在 Windows PowerShell ISE 中進行指令碼偵錯時，也可以使用專為 Windows PowerShell 主控台設計的鍵盤快速鍵。 若要使用這些快速鍵，您必須在命令窗格中輸入捷徑，然後按 <kbd>ENTER</kbd> 鍵。

|                        動作                        | 鍵盤快速鍵 |                使用位置                 |
| ---------------------------------------------------- | ----------------- | ------------------------------------- |
| **繼續**                                         | `C`               | 偵錯指令碼時的主控台窗格 |
| **逐步執行**                                        | `S`               | 偵錯指令碼時的主控台窗格 |
| **逐程序**                                        | `V`               | 偵錯指令碼時的主控台窗格 |
| **跳出**                                         | `O`               | 偵錯指令碼時的主控台窗格 |
| **重複最後一個命令** (適用於逐步執行或逐程序) | <kbd>ENTER</kbd>  | 偵錯指令碼時的主控台窗格 |
| **顯示呼叫堆疊**                               | `K`               | 偵錯指令碼時的主控台窗格 |
| **停止偵錯**                                   | `Q`               | 偵錯指令碼時的主控台窗格 |
| **列出指令碼**                                  | `L`               | 偵錯指令碼時的主控台窗格 |
| **顯示主控台偵錯命令**               | `H` 或 `?`        | 偵錯指令碼時的主控台窗格 |

## <a name="keyboard-shortcuts-for-windows-powershell-tabs"></a>Windows PowerShell 索引標籤的鍵盤快速鍵

使用 Windows PowerShell 索引標籤時，您可以使用下列鍵盤快速鍵。

|             動作              |                                                        鍵盤快速鍵                                                        |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| **關閉 PowerShell 索引標籤**        | <kbd>CTRL</kbd>+<kbd>W</kbd>                                                                                                    |
| **新增 PowerShell 索引標籤**          | <kbd>CTRL</kbd>+<kbd>T</kbd>                                                                                                    |
| **上一個 PowerShell 索引標籤**     | <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>TAB</kbd>。 只有在任何 Windows PowerShell 索引標籤上沒有檔案開啟時，才適用這個快速鍵。 |
| **下一個 Windows PowerShell 索引標籤** | <kbd>CTRL</kbd>+<kbd>TAB</kbd>。 只有在任何 Windows PowerShell 索引標籤上沒有檔案開啟時，才適用這個快速鍵。                  |

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>開始和結束的鍵盤快速鍵

您可以使用下列鍵盤快速鍵，啟動 Windows PowerShell 主控台 (PowerShell.exe) 或結束 Windows PowerShell ISE。

|                        動作                        |               鍵盤快速鍵               |
| ---------------------------------------------------- | --------------------------------------------- |
| **結束**                                             | <kbd>ALT</kbd>+<kbd>F4</kbd>                  |
| **啟動 PowerShell.exe** (Windows PowerShell 主控台) | <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>P</kbd> |

## <a name="see-also"></a>另請參閱

- [PowerShell 雜誌：Windows PowerShell ISE 鍵盤快速鍵的完整清單](https://www.powershellmagazine.com/2013/01/29/the-complete-list-of-powershell-ise-3-0-keyboard-shortcuts/) \(英文\)
