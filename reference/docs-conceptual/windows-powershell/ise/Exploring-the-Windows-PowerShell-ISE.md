---
ms.date: 01/02/2020
title: 探索 Windows PowerShell ISE
description: 此文章是 Windows PowerShell ISE 的功能概觀
ms.topic: conceptual
ms.custom: ISE-F1-page
ms.openlocfilehash: 91161763c817972a62b4da1558a7ca119d8c8616
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "97090441"
---
# <a name="exploring-the-windows-powershell-ise"></a>探索 Windows PowerShell ISE

您可以使用 Windows PowerShell 整合式指令碼環境 (ISE)，來建立及執行命令與指令碼，並對其偵錯。 Windows PowerShell ISE 是由功能表列、Windows PowerShell 索引標籤、工具列、指令碼索引標籤、指令碼窗格、主控台窗格、狀態列、文字大小滑桿和即時線上說明所組成。

## <a name="menu-bar"></a>功能表列

功能表列包含 [檔案]  、[編輯]  、[檢視]  、[工具]  、[偵錯]  、[附加元件]  和 [說明]  功能表。 功能表上的按鈕可讓您在 Windows PowerShell ISE 中執行與寫入和執行指令碼，以及執行命令相關的工作。 此外，您可以執行使用 [ISE 物件模型階層](object-model/The-ISE-Object-Model-Hierarchy.md)的指令碼，將[附加元件工具](object-model/The-ISEAddOnTool-Object.md)放在功能表列上。

## <a name="windows-powershell-tabs"></a>Windows PowerShell 索引標籤

Windows PowerShell 索引標籤是 Windows PowerShell 指令碼的執行環境。 您可以在 Windows PowerShell ISE 中開啟新的 Windows PowerShell 索引標籤，在您的本機電腦或遠端電腦上建立個別環境。 您最多可以同時開啟 8 個 PowerShell 索引標籤。

如需詳細資訊，請參閱[如何在 Windows PowerShell ISE 中建立 PowerShell 索引標籤](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)。

## <a name="toolbar"></a>工具列

您可以在工具列上找到下列按鈕。

|             按鈕             |                                                                                     函式                                                                                     |
| ------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **新增**                        | 開啟新的指令碼。                                                                                                                                                              |
| **開啟**                       | 開啟現有的指令碼或檔案。                                                                                                                                                |
| **儲存**                       | 儲存指令碼或檔案。                                                                                                                                                          |
| **剪下**                        | 剪下選取的文字並複製到剪貼簿。                                                                                                                           |
| **複製**                       | 將選取文字複製到剪貼簿。                                                                                                                                       |
| **貼上**                      | 在游標位置貼上剪貼簿的內容。                                                                                                                     |
| **清除輸出窗格**          | 清除輸出窗格中的所有內容。                                                                                                                                           |
| **復原**                       | 回復剛才執行的動作。                                                                                                                                     |
| **取消復原**                       | 執行剛才復原的動作。                                                                                                                                        |
| **執行指令碼**                 | 執行指令碼。                                                                                                                                                                   |
| **執行選取項目**              | 執行選取的指令碼部分。                                                                                                                                             |
| **停止執行**             | 停止執行指令碼。                                                                                                                                                  |
| **新增遠端 PowerShell 索引標籤**  | 建立新的 PowerShell 索引標籤，以在遠端電腦上建立工作階段。 對話方塊隨即出現，並提示您輸入建立遠端連線所需的詳細資料。 |
| **啟動 PowerShell.exe**       | 開啟 PowerShell 主控台。                                                                                                                                                      |
| **靠上顯示指令碼窗格**       | 將指令碼窗格移至顯示畫面上方。                                                                                                                                 |
| **靠右顯示指令碼窗格**     | 將指令碼窗格移至顯示畫面右側。                                                                                                                               |
| **顯示最大化的指令碼窗格** | 將指令碼窗格最大化。                                                                                                                                                       |

## <a name="script-tab"></a>指令碼索引標籤

顯示您正在編輯的指令碼名稱。 您可以按一下指令碼索引標籤，選取要編輯的指令碼。

當您指向指令碼索引標籤時，指令碼檔案的完整路徑會顯示在工具提示中。

## <a name="script-pane"></a>指令碼窗格

可讓您建立及執行指令碼。 您可以在指令碼窗格中開啟、編輯及執行現有的指令碼。 如需詳細資訊，請參閱[如何在 Windows PowerShell ISE 中撰寫和執行指令碼](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md)。

## <a name="console-pane"></a>主控台窗格

顯示已執行的命令和指令碼結果。 您可以在主控台窗格中執行命令， 也可以複製並清除主控台窗格中的內容。

如需詳細資訊，請參閱下列文章：

- [如何在 Windows PowerShell ISE 中使用主控台窗格](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)
- [如何在 Windows PowerShell ISE 中針對指令碼進行偵錯](How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md)
- [如何在指令碼窗格和主控台窗格中使用 TAB 鍵自動完成](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md)

## <a name="status-bar"></a>狀態列

可讓您查看所執行的命令和指令碼是否已完成。 狀態列位於顯示畫面最底部。 錯誤訊息的選定部分會顯示在狀態列上。

## <a name="text-size-slider"></a>文字大小滑桿

增加或減少螢幕上文字的大小。

## <a name="help"></a>説明

您可以在 docs.microsoft.com 上取得 Windows PowerShell ISE 的說明。 開啟 [說明] 的方式是在 [說明] 功能表上按一下 [Windows PowerShell ISE 說明]，或在任何位置按下 <kbd>F1</kbd> 鍵，但游標不可以是在指令碼窗格或主控台窗格中的 Cmdlet 名稱上方。
您也可以從 [說明]  功能表執行 `Update-Help` Cmdlet，並顯示命令視窗，透過顯示 Cmdlet 的所有參數並讓您在容易使用的表單中填入參數，來協助您建構命令。

## <a name="see-also"></a>另請參閱

- [Windows PowerShell ISE 簡介](Introducing-the-Windows-PowerShell-ISE.md)
- [如何在 Windows PowerShell ISE 中使用設定檔](How-to-Use-Profiles-in-Windows-PowerShell-ISE.md)
- [Windows PowerShell ISE 的協助工具](Accessibility-in-Windows-PowerShell-ISE.md)
- [Windows PowerShell ISE 的鍵盤快速鍵](Keyboard-Shortcuts-for-the-Windows-PowerShell-ISE.md)
