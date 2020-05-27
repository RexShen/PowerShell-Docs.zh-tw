---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: Windows PowerShell ISE 簡介
ms.openlocfilehash: 3e4471d0982ba4d7ef1a9d59906a9ff297f6f7cb
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808714"
---
# <a name="the-windows-powershell-ise"></a><span data-ttu-id="479fb-103">Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="479fb-103">The Windows PowerShell ISE</span></span>

<span data-ttu-id="479fb-104">Windows PowerShell 整合式指令碼環境 (ISE) 是適用於 Windows PowerShell 的主機應用程式。</span><span class="sxs-lookup"><span data-stu-id="479fb-104">The Windows PowerShell Integrated Scripting Environment (ISE) is a host application for Windows PowerShell.</span></span> <span data-ttu-id="479fb-105">在 ISE 中，您可以執行命令，並在以 Windows 為基礎的單一圖形化使用者介面中撰寫、測試及偵錯指令碼。</span><span class="sxs-lookup"><span data-stu-id="479fb-105">In the ISE, you can run commands and write, test, and debug scripts in a single Windows-based graphic user interface.</span></span> <span data-ttu-id="479fb-106">ISE 提供多行編輯、TAB 鍵自動完成、語法顏色設定、選擇性執行、即時線上說明，以及支援從右至左的語言。</span><span class="sxs-lookup"><span data-stu-id="479fb-106">The ISE provides multiline editing, tab completion, syntax coloring, selective execution, context-sensitive help, and support for right-to-left languages.</span></span> <span data-ttu-id="479fb-107">功能表項目與鍵盤快速鍵會對應到您在 Windows PowerShell 主控台中執行的許多相同工作。</span><span class="sxs-lookup"><span data-stu-id="479fb-107">Menu items and keyboard shortcuts are mapped to many of the same tasks that you would do in the Windows PowerShell console.</span></span> <span data-ttu-id="479fb-108">例如，當您在 ISE 中偵錯指令碼時，可在編輯窗格中以滑鼠右鍵按一下程式碼行來設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="479fb-108">For example, when you debug a script in the ISE, you can right-click on a line of code in the edit pane to set a breakpoint.</span></span>

## <a name="support"></a><span data-ttu-id="479fb-109">支援</span><span class="sxs-lookup"><span data-stu-id="479fb-109">Support</span></span>

<span data-ttu-id="479fb-110">ISE 最初是透過 Windows PowerShell V2 引進，並透過 PowerShell V3 重新設計。</span><span class="sxs-lookup"><span data-stu-id="479fb-110">The ISE was first introduced with Windows PowerShell V2 and was re-designed with PowerShell V3.</span></span> <span data-ttu-id="479fb-111">Windows PowerShell V5.1 (含) 以下的所有 Windows PowerShell 版本均支援 ISE。</span><span class="sxs-lookup"><span data-stu-id="479fb-111">The ISE is supported in all supported versions of Windows PowerShell up to and including Windows PowerShell V5.1.</span></span>

> [!NOTE]
> <span data-ttu-id="479fb-112">我們將不再為 PowerShell ISE 開發新功能。</span><span class="sxs-lookup"><span data-stu-id="479fb-112">The PowerShell ISE is no longer in active feature development.</span></span> <span data-ttu-id="479fb-113">因為此功能屬於 Windows 的出貨元件，所以官方仍會繼續支援其安全性與高優先順序的服務修正。</span><span class="sxs-lookup"><span data-stu-id="479fb-113">As a shipping component of Windows, it continues to be officially supported for security and high-priority servicing fixes.</span></span>
> <span data-ttu-id="479fb-114">目前尚無任何計劃要將 ISE 從 Windows 移除。</span><span class="sxs-lookup"><span data-stu-id="479fb-114">We currently have no plans to remove the ISE from Windows.</span></span>
>
> <span data-ttu-id="479fb-115">PowerShell v6 及更新版本不支援 ISE。</span><span class="sxs-lookup"><span data-stu-id="479fb-115">There is no support for the ISE in PowerShell v6 and beyond.</span></span> <span data-ttu-id="479fb-116">使用者如有需要 ISE 的替代解決方案，可使用 [Visual Studio Code](https://code.visualstudio.com/) 搭配 [PowerShell 延伸模組](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell)。</span><span class="sxs-lookup"><span data-stu-id="479fb-116">Users looking for replacement for the ISE should use [Visual Studio Code](https://code.visualstudio.com/) with the [PowerShell Extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell).</span></span>

## <a name="key-features"></a><span data-ttu-id="479fb-117">重要功能</span><span class="sxs-lookup"><span data-stu-id="479fb-117">Key Features</span></span>

<span data-ttu-id="479fb-118">Windows PowerShell ISE 的重要功能包括：</span><span class="sxs-lookup"><span data-stu-id="479fb-118">Key features in Windows PowerShell ISE include:</span></span>

- <span data-ttu-id="479fb-119">多行編輯：若要在 [命令] 窗格中目前的行下方插入空白行，請按 <kbd>SHIFT</kbd>+<kbd>ENTER</kbd>。</span><span class="sxs-lookup"><span data-stu-id="479fb-119">Multiline editing: To insert a blank line under the current line in the Command pane, press <kbd>SHIFT</kbd>+<kbd>ENTER</kbd>.</span></span>
- <span data-ttu-id="479fb-120">選擇性執行：若要執行指令碼中的某部分，請選取您要執行的文字，然後按一下 [執行指令碼]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="479fb-120">Selective execution: To run part of a script, select the text you want to run, and then click the **Run Script** button.</span></span> <span data-ttu-id="479fb-121">您也可以按 <kbd>F5</kbd>。</span><span class="sxs-lookup"><span data-stu-id="479fb-121">Or, press <kbd>F5</kbd>.</span></span>
- <span data-ttu-id="479fb-122">即時線上說明：鍵入 `Invoke-Item`，然後按 <kbd>F1</kbd>。</span><span class="sxs-lookup"><span data-stu-id="479fb-122">Context-sensitive help: Type `Invoke-Item`, and then press <kbd>F1</kbd>.</span></span> <span data-ttu-id="479fb-123">說明檔案會隨即開啟，並顯示 `Invoke-Item` Cmdlet 的相關文章。</span><span class="sxs-lookup"><span data-stu-id="479fb-123">The Help file opens to the article for the `Invoke-Item` cmdlet.</span></span>

<span data-ttu-id="479fb-124">Windows PowerShell ISE 可讓您自訂其部分外觀。</span><span class="sxs-lookup"><span data-stu-id="479fb-124">The Windows PowerShell ISE lets you customize some aspects of its appearance.</span></span> <span data-ttu-id="479fb-125">它也有自己的 Windows PowerShell 設定檔指令碼。</span><span class="sxs-lookup"><span data-stu-id="479fb-125">It also has its own Windows PowerShell profile script.</span></span>

## <a name="to-start-the-windows-powershell-ise"></a><span data-ttu-id="479fb-126">啟動 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="479fb-126">To start the Windows PowerShell ISE</span></span>

<span data-ttu-id="479fb-127">按一下 [開始]  、選取 [Windows PowerShell]  ，然後按一下 [Windows PowerShell ISE]  。</span><span class="sxs-lookup"><span data-stu-id="479fb-127">Click **Start**, select **Windows PowerShell**, and then click **Windows PowerShell ISE**.</span></span>
<span data-ttu-id="479fb-128">或者，您可以在任何命令殼層或在 [執行] 方塊中輸入 `powershell_ise.exe`。</span><span class="sxs-lookup"><span data-stu-id="479fb-128">Alternately, you can type `powershell_ise.exe` in any command shell or in the Run box.</span></span>

## <a name="to-get-help-in-the-windows-powershell-ise"></a><span data-ttu-id="479fb-129">在 Windows PowerShell ISE 中取得說明</span><span class="sxs-lookup"><span data-stu-id="479fb-129">To get Help in the Windows PowerShell ISE</span></span>

<span data-ttu-id="479fb-130">在 **[說明]** 功能表上，按一下 **[Windows PowerShell 說明]** 。</span><span class="sxs-lookup"><span data-stu-id="479fb-130">On the **Help** menu, click **Windows PowerShell Help**.</span></span> <span data-ttu-id="479fb-131">您也可以按 <kbd>F1</kbd>。</span><span class="sxs-lookup"><span data-stu-id="479fb-131">Or, press <kbd>F1</kbd>.</span></span> <span data-ttu-id="479fb-132">開啟的檔案將會說明 Windows PowerShell ISE 與 Windows PowerShell，包括 `Get-Help` Cmdlet 所提供的所有說明。</span><span class="sxs-lookup"><span data-stu-id="479fb-132">The file that opens describes Windows PowerShell ISE and Windows PowerShell, including all the help available from the `Get-Help` cmdlet.</span></span>
