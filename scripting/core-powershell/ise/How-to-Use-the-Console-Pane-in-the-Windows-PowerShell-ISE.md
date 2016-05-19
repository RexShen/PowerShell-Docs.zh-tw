---
title: 如何在 Windows PowerShell ISE 中使用主控台窗格
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 44d67705-87c7-4a69-a53e-6471fdebb757
---
# 如何在 Windows PowerShell ISE 中使用主控台窗格
Windows PowerShell® 整合式指令碼環境 (ISE) 中主控台窗格的運作方式，與單獨 Windows PowerShell ISE 主控台視窗的運作方式完全相同。

若要在主控台窗格中執行命令，請輸入命令，然後按 ENTER 鍵。 若要輸入您要依序執行的多個命令，請在每個命令之間輸入 SHIFT+ENTER。 如需協助輸入命令，請參閱[如何在指令碼窗格和主控台窗格中使用 TAB 鍵自動完成](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md)。

若要停止命令，請按一下工具列中的 **[停止操作]**，或按 CTRL+BREAK。 在內容明確的情況下，您也可以使用 CTRL+C 來停止命令。 例如，如果在目前的窗格中選取了一些文字，則 CTRL+C 會對應至複製操作。

從 Windows PowerShell v3 開始，輸出窗格已與主控台窗格結合。 這樣做的優點是其運作方式就像是獨立的 Windows PowerShell 主控台，因而可消除分開時所需程序的差異。 您可以：

-   從主控台窗格選取文字並複製到 [剪貼簿]，以貼到任何其他視窗。 若要選取文字，請在輸出窗格中您要擷取的文字上，按住滑鼠進行拖曳。 您也可以在按住 **SHIFT** 鍵的同時，使用方向鍵選取文字。 然後按 CTRL+C，或按一下工具列中的**複製**圖示。

-   在目前的游標位置貼上選取的文字。 按一下工具列中的**貼上**圖示。

-   清除主控台窗格中的所有文字。 若要清除主控台窗格，您可以按一下工具列中的 [清除主控台窗格] 圖示，或是執行命令 **Clear-Host** 或其別名 **cls**.

## 另請參閱
[使用 Windows PowerShell ISE](Using-the-Windows-PowerShell-ISE.md)



<!--HONumber=May16_HO2-->


