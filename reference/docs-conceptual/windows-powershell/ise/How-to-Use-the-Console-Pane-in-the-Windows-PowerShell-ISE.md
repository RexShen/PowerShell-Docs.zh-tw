---
ms.date: 01/02/2020
title: 如何在 Windows PowerShell ISE 中使用主控台窗格
description: 如何在 Windows PowerShell ISE 中使用主控台窗格
ms.openlocfilehash: 7f6d3f5a3e4e596beb0d5c0bc395e3e7bf39906d
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663660"
---
# <a name="how-to-use-the-console-pane-in-the-windows-powershell-ise"></a>如何在 Windows PowerShell ISE 中使用主控台窗格

Windows PowerShell 整合式指令碼環境 (ISE) 的 [主控台] 窗格與獨立 Windows PowerShell ISE 的 [主控台] 視窗以完全相同的方式運作。

若要在主控台窗格中執行命令，請輸入命令，然後按 <kbd>ENTER</kbd> 鍵。 若要輸入您要依序執行的多個命令，請在每個命令之間輸入 <kbd>SHIFT</kbd>+<kbd>ENTER</kbd>。 如需協助輸入命令，請參閱[如何在指令碼窗格和主控台窗格中使用 TAB 鍵自動完成](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md)。

若要停止命令，請按一下工具列中的 [停止操作]  ，或按 <kbd>CTRL</kbd>+<kbd>BREAK</kbd>。 在內容明確的情況下，您也可以使用 <kbd>CTRL</kbd>+<kbd>C</kbd> 來停止命令。 例如，如果在目前的窗格中選取了一些文字，則 <kbd>CTRL</kbd>+<kbd>C</kbd> 會對應至複製作業。

從 Windows PowerShell v3 開始，輸出窗格已與主控台窗格結合。 這樣做的優點是其運作方式就像是獨立的 Windows PowerShell 主控台，因而可消除分開時所需程序的差異。 您可以：

- 從主控台窗格選取文字並複製到 [剪貼簿]，以貼到任何其他視窗。 若要選取文字，請在輸出窗格中您要擷取的文字上，按住滑鼠進行拖曳。 您也可以在按住 <kbd>SHIFT</kbd> 鍵的同時，使用方向鍵選取文字。 然後按 <kbd>CTRL</kbd>+<kbd>C</kbd>，或按一下工具列中的 **複製** 圖示。

- 在目前的游標位置貼上選取的文字。 按一下工具列中的 **貼上** 圖示。

- 清除主控台窗格中的所有文字。 若要清除 [主控台] 窗格，您可以按一下工具列中的 **清除主控台窗格** 圖示，或是執行命令 `Clear-Host` 或其別名 `cls`。

## <a name="see-also"></a>另請參閱

- [Windows PowerShell ISE 簡介](Introducing-the-Windows-PowerShell-ISE.md)
