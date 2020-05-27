---
ms.date: 01/02/2020
keywords: powershell,cmdlet
title: 如何在 Windows PowerShell ISE 中使用主控台窗格
ms.openlocfilehash: f0ef07e410ed494f5732eab360c4e050c9c09a7f
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808724"
---
# <a name="how-to-use-the-console-pane-in-the-windows-powershell-ise"></a><span data-ttu-id="f065a-103">如何在 Windows PowerShell ISE 中使用主控台窗格</span><span class="sxs-lookup"><span data-stu-id="f065a-103">How to Use the Console Pane in the Windows PowerShell ISE</span></span>

<span data-ttu-id="f065a-104">Windows PowerShell 整合式指令碼環境 (ISE) 的 [主控台] 窗格與獨立 Windows PowerShell ISE 的 [主控台] 視窗以完全相同的方式運作。</span><span class="sxs-lookup"><span data-stu-id="f065a-104">The Console pane in the Windows PowerShell Integrated Scripting Environment (ISE) operates exactly like the stand-alone Windows PowerShell ISE console window.</span></span>

<span data-ttu-id="f065a-105">若要在主控台窗格中執行命令，請輸入命令，然後按 <kbd>ENTER</kbd> 鍵。</span><span class="sxs-lookup"><span data-stu-id="f065a-105">To run a command in the Console Pane, type a command, and then press <kbd>ENTER</kbd>.</span></span> <span data-ttu-id="f065a-106">若要輸入您要依序執行的多個命令，請在每個命令之間輸入 <kbd>SHIFT</kbd>+<kbd>ENTER</kbd>。</span><span class="sxs-lookup"><span data-stu-id="f065a-106">To enter multiple commands that you want to execute in sequence, type <kbd>SHIFT</kbd>+<kbd>ENTER</kbd> between commands.</span></span> <span data-ttu-id="f065a-107">如需協助輸入命令，請參閱[如何在指令碼窗格和主控台窗格中使用 TAB 鍵自動完成](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md)。</span><span class="sxs-lookup"><span data-stu-id="f065a-107">See [How to Use Tab Completion in the Script Pane and Console Pane](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) for help in typing commands.</span></span>

<span data-ttu-id="f065a-108">若要停止命令，請按一下工具列中的 [停止操作]  ，或按 <kbd>CTRL</kbd>+<kbd>BREAK</kbd>。</span><span class="sxs-lookup"><span data-stu-id="f065a-108">To stop a command, on the toolbar, click **Stop Operation**, or press <kbd>CTRL</kbd>+<kbd>BREAK</kbd>.</span></span> <span data-ttu-id="f065a-109">在內容明確的情況下，您也可以使用 <kbd>CTRL</kbd>+<kbd>C</kbd> 來停止命令。</span><span class="sxs-lookup"><span data-stu-id="f065a-109">You can also use <kbd>CTRL</kbd>+<kbd>C</kbd> to stop a command if the context is unambiguous.</span></span> <span data-ttu-id="f065a-110">例如，如果在目前的窗格中選取了一些文字，則 <kbd>CTRL</kbd>+<kbd>C</kbd> 會對應至複製作業。</span><span class="sxs-lookup"><span data-stu-id="f065a-110">For example, if some text has been selected in the current Pane, then <kbd>CTRL</kbd>+<kbd>C</kbd> maps to the copy operation.</span></span>

<span data-ttu-id="f065a-111">從 Windows PowerShell v3 開始，輸出窗格已與主控台窗格結合。</span><span class="sxs-lookup"><span data-stu-id="f065a-111">Beginning in Windows PowerShell v3, the Output pane was combined with the Console pane.</span></span> <span data-ttu-id="f065a-112">這樣做的優點是其運作方式就像是獨立的 Windows PowerShell 主控台，因而可消除分開時所需程序的差異。</span><span class="sxs-lookup"><span data-stu-id="f065a-112">This has the benefit of behaving like the stand-alone Windows PowerShell console and eliminates the differences in procedures that were needed when they were separate.</span></span> <span data-ttu-id="f065a-113">您可以：</span><span class="sxs-lookup"><span data-stu-id="f065a-113">You can:</span></span>

- <span data-ttu-id="f065a-114">從主控台窗格選取文字並複製到 [剪貼簿]，以貼到任何其他視窗。</span><span class="sxs-lookup"><span data-stu-id="f065a-114">Select and copy text from the Console pane to the Clipboard for pasting in any other window.</span></span> <span data-ttu-id="f065a-115">若要選取文字，請在輸出窗格中您要擷取的文字上，按住滑鼠進行拖曳。</span><span class="sxs-lookup"><span data-stu-id="f065a-115">To select text, click and hold the mouse in the output pane while dragging the mouse over the text you want to capture.</span></span> <span data-ttu-id="f065a-116">您也可以在按住 <kbd>SHIFT</kbd> 鍵的同時，使用方向鍵選取文字。</span><span class="sxs-lookup"><span data-stu-id="f065a-116">You can also use the cursor arrow keys while holding <kbd>SHIFT</kbd> to select text.</span></span> <span data-ttu-id="f065a-117">然後按 <kbd>CTRL</kbd>+<kbd>C</kbd>，或按一下工具列中的**複製**圖示。</span><span class="sxs-lookup"><span data-stu-id="f065a-117">Then press <kbd>CTRL</kbd>+<kbd>C</kbd> or click the **Copy** icon in the toolbar.</span></span>

- <span data-ttu-id="f065a-118">在目前的游標位置貼上選取的文字。</span><span class="sxs-lookup"><span data-stu-id="f065a-118">Paste the selected text at a current cursor position.</span></span> <span data-ttu-id="f065a-119">按一下工具列中的**貼上**圖示。</span><span class="sxs-lookup"><span data-stu-id="f065a-119">Click the **Paste** icon on the toolbar.</span></span>

- <span data-ttu-id="f065a-120">清除主控台窗格中的所有文字。</span><span class="sxs-lookup"><span data-stu-id="f065a-120">Clear all the text in the Console pane.</span></span> <span data-ttu-id="f065a-121">若要清除 [主控台] 窗格，您可以按一下工具列中的**清除主控台窗格**圖示，或是執行命令 `Clear-Host` 或其別名 `cls`。</span><span class="sxs-lookup"><span data-stu-id="f065a-121">To clear the Console pane, you can click the **Clear Console Pane** icon on the toolbar, or run the command `Clear-Host` or its alias, `cls`.</span></span>

## <a name="see-also"></a><span data-ttu-id="f065a-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f065a-122">See Also</span></span>

- [<span data-ttu-id="f065a-123">Windows PowerShell ISE 簡介</span><span class="sxs-lookup"><span data-stu-id="f065a-123">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)