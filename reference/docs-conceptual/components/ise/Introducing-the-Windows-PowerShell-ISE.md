---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: Windows PowerShell ISE 簡介
ms.openlocfilehash: 09a28b295855fd2a3c62bba8a681399dae3454f8
ms.sourcegitcommit: 3402a478cf118c11a5642038eb117bc76553e3ab
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53411577"
---
# <a name="the-windows-powershell-ise"></a><span data-ttu-id="440f0-103">Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="440f0-103">The Windows PowerShell ISE</span></span>

<span data-ttu-id="440f0-104">Windows PowerShell 整合式指令碼環境 (ISE) 是適用於 Windows PowerShell 的主機應用程式。</span><span class="sxs-lookup"><span data-stu-id="440f0-104">The Windows PowerShell Integrated Scripting Environment (ISE) is a host application for Windows PowerShell.</span></span> <span data-ttu-id="440f0-105">在 ISE 中，您可以執行命令和撰寫、 測試，並在單一的以 Windows 為基礎的圖形化使用者介面中的指令碼偵錯。</span><span class="sxs-lookup"><span data-stu-id="440f0-105">In the ISE, you can run commands and write, test, and debug scripts in a single Windows-based graphic user interface.</span></span> <span data-ttu-id="440f0-106">ISE 提供多行編輯、 tab 鍵自動完成、 語法著色、 選擇性執行、 即時線上說明及支援從右至左的語言。</span><span class="sxs-lookup"><span data-stu-id="440f0-106">The ISE provides multiline editing, tab completion, syntax coloring, selective execution, context-sensitive help, and support for right-to-left languages.</span></span> <span data-ttu-id="440f0-107">功能表項目與鍵盤快速鍵會對應到您在 Windows PowerShell 主控台中執行的許多相同工作。</span><span class="sxs-lookup"><span data-stu-id="440f0-107">Menu items and keyboard shortcuts are mapped to many of the same tasks that you would do in the Windows PowerShell console.</span></span> <span data-ttu-id="440f0-108">比方說，當您偵錯指令碼在 ISE 中的，您可以以滑鼠右鍵按一下編輯窗格來設定中斷點的程式碼行。</span><span class="sxs-lookup"><span data-stu-id="440f0-108">For example, when you debug a script in the ISE, you can right-click on a line of code in the edit pane to set a breakpoint.</span></span>

## <a name="support"></a><span data-ttu-id="440f0-109">支援</span><span class="sxs-lookup"><span data-stu-id="440f0-109">Support</span></span>

<span data-ttu-id="440f0-110">ISE 最初是使用 Windows PowerShell V2 和 PowerShell V3 的重新設計。</span><span class="sxs-lookup"><span data-stu-id="440f0-110">The ISE was first introduced with Windows PowerShell V2 and was re-designed with PowerShell V3.</span></span> <span data-ttu-id="440f0-111">ISE 支援所有支援的最高的 Windows PowerShell，包括 Windows PowerShell V5.1 版本。</span><span class="sxs-lookup"><span data-stu-id="440f0-111">The ISE is supported in all supported versions of Windows PowerShell up to and including Windows PowerShell V5.1.</span></span> <span data-ttu-id="440f0-112">ISE 中，不過，為 maintennce 模式，而且可能會加入任何新功能。</span><span class="sxs-lookup"><span data-stu-id="440f0-112">The ISE, however, is in maintennce mode and no new features are likely to be added.</span></span>
<span data-ttu-id="440f0-113">此外，也沒有 ISE 與 PowerShell v6 及更新版本的支援。</span><span class="sxs-lookup"><span data-stu-id="440f0-113">Additionally, there is no support for the ISE with PowerShell v6 and beyond.</span></span> <span data-ttu-id="440f0-114">使用者想要的圖形工具，用來管理等 PowerShell scrips，應該考慮[Visual Studio Code](https://code.visualstudio.com/)。</span><span class="sxs-lookup"><span data-stu-id="440f0-114">Users wanting a graphical tool with which to manage PowerShell scrips, etc, should consider [Visual Studio Code](https://code.visualstudio.com/).</span></span>

## <a name="key-features"></a><span data-ttu-id="440f0-115">重要功能</span><span class="sxs-lookup"><span data-stu-id="440f0-115">Key Features</span></span>

<span data-ttu-id="440f0-116">在 Windows PowerShell ISE 中的主要功能包括：</span><span class="sxs-lookup"><span data-stu-id="440f0-116">Key features in Windows PowerShell ISE include:</span></span>

- <span data-ttu-id="440f0-117">多行編輯：若要在 [命令] 窗格中在目前的行下插入空行，請按下 SHIFT+ENTER。</span><span class="sxs-lookup"><span data-stu-id="440f0-117">Multiline editing: To insert a blank line under the current line in the Command pane, press SHIFT+ENTER.</span></span>
- <span data-ttu-id="440f0-118">選擇性執行：若要執行指令碼中的某部分，請選取您要執行的文字，然後按一下 [執行指令碼] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="440f0-118">Selective execution: To run part of a script, select the text you want to run, and then click the **Run Script** button.</span></span> <span data-ttu-id="440f0-119">或者，按下 F5。</span><span class="sxs-lookup"><span data-stu-id="440f0-119">Or, press F5.</span></span>
- <span data-ttu-id="440f0-120">即時線上說明：鍵入 **Invoke-Item**，然後按 F1。</span><span class="sxs-lookup"><span data-stu-id="440f0-120">Context-sensitive help: Type **Invoke-Item**, and then press F1.</span></span> <span data-ttu-id="440f0-121">說明檔案隨即開啟，並顯示適用於 **Invoke-Item** Cmdlet 的文章。</span><span class="sxs-lookup"><span data-stu-id="440f0-121">The Help file opens to the article for the **Invoke-Item** cmdlet.</span></span>

<span data-ttu-id="440f0-122">Windows PowerShell ISE 可讓您自訂其部分外觀。</span><span class="sxs-lookup"><span data-stu-id="440f0-122">The Windows PowerShell ISE lets you customize some aspects of its appearance.</span></span> <span data-ttu-id="440f0-123">它也有自己的 Windows PowerShell 設定檔指令碼。</span><span class="sxs-lookup"><span data-stu-id="440f0-123">It also has its own Windows PowerShell profile script.</span></span>

## <a name="to-start-the-windows-powershell-ise"></a><span data-ttu-id="440f0-124">啟動 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="440f0-124">To start the Windows PowerShell ISE</span></span>

<span data-ttu-id="440f0-125">按一下 [開始]、選取 [Windows PowerShell]，然後按一下 [Windows PowerShell ISE]。</span><span class="sxs-lookup"><span data-stu-id="440f0-125">Click **Start**, select **Windows PowerShell**, and then click **Windows PowerShell ISE**.</span></span>
<span data-ttu-id="440f0-126">或者，您可以在任何命令殼層或在 [執行] 方塊中輸入 `powershell_ise.exe`。</span><span class="sxs-lookup"><span data-stu-id="440f0-126">Alternately, you can type `powershell_ise.exe` in any command shell or in the Run box.</span></span>

## <a name="to-get-help-in-the-windows-powershell-ise"></a><span data-ttu-id="440f0-127">在 Windows PowerShell ISE 中取得說明</span><span class="sxs-lookup"><span data-stu-id="440f0-127">To get Help in the Windows PowerShell ISE</span></span>

<span data-ttu-id="440f0-128">在 **[說明]** 功能表上，按一下 **[Windows PowerShell 說明]**。</span><span class="sxs-lookup"><span data-stu-id="440f0-128">On the **Help** menu, click **Windows PowerShell Help**.</span></span> <span data-ttu-id="440f0-129">或者，按下 F1。</span><span class="sxs-lookup"><span data-stu-id="440f0-129">Or, press F1.</span></span> <span data-ttu-id="440f0-130">開啟的檔案會描述 Windows PowerShell ISE 與 Windows PowerShell，包括可從 Get-Help Cmdlet 取得的所有說明。</span><span class="sxs-lookup"><span data-stu-id="440f0-130">The file that opens describes Windows PowerShell ISE and Windows PowerShell, including all of the help available from the Get-Help cmdlet.</span></span>
