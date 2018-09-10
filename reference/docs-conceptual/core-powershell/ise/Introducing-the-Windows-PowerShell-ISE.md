---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: Windows PowerShell ISE 簡介
ms.openlocfilehash: d27a0eb594d7271121cee59f38d096995cc98648
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133075"
---
# <a name="introducing-the-windows-powershell-ise"></a><span data-ttu-id="ddc90-103">Windows PowerShell ISE 簡介</span><span class="sxs-lookup"><span data-stu-id="ddc90-103">Introducing the Windows PowerShell ISE</span></span>

<span data-ttu-id="ddc90-104">Windows PowerShell 整合式指令碼環境 (ISE) 是適用於 Windows PowerShell 的主機應用程式。</span><span class="sxs-lookup"><span data-stu-id="ddc90-104">The Windows PowerShell Integrated Scripting Environment (ISE) is a host application for Windows PowerShell.</span></span> <span data-ttu-id="ddc90-105">在 Windows PowerShell ISE 中，您可以執行命令，並在以 Windows 為基礎的單一圖形化使用者介面中撰寫、測試及偵錯指令碼。</span><span class="sxs-lookup"><span data-stu-id="ddc90-105">In Windows PowerShell ISE, you can run commands and write, test, and debug scripts in a single Windows-based graphic user interface.</span></span> <span data-ttu-id="ddc90-106">此介面提供多行編輯、TAB 鍵自動完成、語法顏色設定、選擇性執行、即時線上說明，以及支援從右至左的語言。</span><span class="sxs-lookup"><span data-stu-id="ddc90-106">The interface provides multiline editing, tab completion, syntax coloring, selective execution, context-sensitive help, and support for right-to-left languages.</span></span> <span data-ttu-id="ddc90-107">功能表項目與鍵盤快速鍵會對應到您在 Windows PowerShell 主控台中執行的許多相同工作。</span><span class="sxs-lookup"><span data-stu-id="ddc90-107">Menu items and keyboard shortcuts are mapped to many of the same tasks that you would do in the Windows PowerShell console.</span></span> <span data-ttu-id="ddc90-108">例如，當您在 Windows PowerShell ISE 中針對指令碼進行偵錯時，您可以利用滑鼠右鍵按一下程式碼行以設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="ddc90-108">For example, when you debug a script in the Windows PowerShell ISE, you can right-click on a line of code to set a breakpoint.</span></span>

<span data-ttu-id="ddc90-109">在 Windows PowerShell ISE 中嘗試使用這些功能</span><span class="sxs-lookup"><span data-stu-id="ddc90-109">Try these features in Windows PowerShell ISE.</span></span>

- <span data-ttu-id="ddc90-110">多行編輯：若要在 [命令] 窗格中的目前行下插入空行，請按 SHIFT+ENTER。</span><span class="sxs-lookup"><span data-stu-id="ddc90-110">Multiline editing: To insert a blank line under the current line in the Command pane, press SHIFT+ENTER.</span></span>
- <span data-ttu-id="ddc90-111">選擇性執行：若要執行指令碼中的某部分，請選取您要執行的文字，然後按一下 **[執行指令碼]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ddc90-111">Selective execution: To run part of a script, select the text you want to run, and then click the **Run Script** button.</span></span> <span data-ttu-id="ddc90-112">或者，按下 F5。</span><span class="sxs-lookup"><span data-stu-id="ddc90-112">Or, press F5.</span></span>
- <span data-ttu-id="ddc90-113">即時線上說明：輸入 **Invoke-Item**，然後按 F1。</span><span class="sxs-lookup"><span data-stu-id="ddc90-113">Context-sensitive help: Type **Invoke-Item**, and then press F1.</span></span> <span data-ttu-id="ddc90-114">說明檔案隨即開啟，並顯示適用於 **Invoke-Item** Cmdlet 的文章。</span><span class="sxs-lookup"><span data-stu-id="ddc90-114">The Help file opens to the article for the **Invoke-Item** cmdlet.</span></span>

<span data-ttu-id="ddc90-115">Windows PowerShell ISE 可讓您自訂其部分外觀。</span><span class="sxs-lookup"><span data-stu-id="ddc90-115">The Windows PowerShell ISE lets you customize some aspects of its appearance.</span></span> <span data-ttu-id="ddc90-116">它也有自己的 Windows PowerShell 設定檔指令碼。</span><span class="sxs-lookup"><span data-stu-id="ddc90-116">It also has its own Windows PowerShell profile script.</span></span>

## <a name="to-start-the-windows-powershell-ise"></a><span data-ttu-id="ddc90-117">啟動 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="ddc90-117">To start the Windows PowerShell ISE</span></span>

<span data-ttu-id="ddc90-118">按一下 [開始]、選取 [Windows PowerShell]，然後按一下 [Windows PowerShell ISE]。</span><span class="sxs-lookup"><span data-stu-id="ddc90-118">Click **Start**, select **Windows PowerShell**, and then click **Windows PowerShell ISE**.</span></span>
<span data-ttu-id="ddc90-119">或者，您可以在任何命令殼層或在 [執行] 方塊中輸入 `powershell_ise.exe`。</span><span class="sxs-lookup"><span data-stu-id="ddc90-119">Alternately, you can type `powershell_ise.exe` in any command shell or in the Run box.</span></span>

## <a name="to-get-help-in-the-windows-powershell-ise"></a><span data-ttu-id="ddc90-120">在 Windows PowerShell ISE 中取得說明</span><span class="sxs-lookup"><span data-stu-id="ddc90-120">To get Help in the Windows PowerShell ISE</span></span>

<span data-ttu-id="ddc90-121">在 [說明] 功能表上，按一下 [Windows PowerShell 說明]。</span><span class="sxs-lookup"><span data-stu-id="ddc90-121">On the **Help** menu, click **Windows PowerShell Help**.</span></span> <span data-ttu-id="ddc90-122">或者，按下 F1。</span><span class="sxs-lookup"><span data-stu-id="ddc90-122">Or, press F1.</span></span> <span data-ttu-id="ddc90-123">開啟的檔案會描述 Windows PowerShell ISE 與 Windows PowerShell，包括可從 Get-Help Cmdlet 取得的所有說明。</span><span class="sxs-lookup"><span data-stu-id="ddc90-123">The file that opens describes Windows PowerShell ISE and Windows PowerShell, including all of the help available from the Get-Help cmdlet.</span></span>