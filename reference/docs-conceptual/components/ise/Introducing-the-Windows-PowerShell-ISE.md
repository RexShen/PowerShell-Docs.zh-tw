---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: Windows PowerShell ISE 簡介
ms.openlocfilehash: 729c8535dbcfcd2c51070b8beac5d328375f36ae
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057409"
---
# <a name="the-windows-powershell-ise"></a><span data-ttu-id="f797a-103">Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="f797a-103">The Windows PowerShell ISE</span></span>

<span data-ttu-id="f797a-104">Windows PowerShell 整合式指令碼環境 (ISE) 是適用於 Windows PowerShell 的主機應用程式。</span><span class="sxs-lookup"><span data-stu-id="f797a-104">The Windows PowerShell Integrated Scripting Environment (ISE) is a host application for Windows PowerShell.</span></span> <span data-ttu-id="f797a-105">在 ISE 中，您可以執行命令，並在以 Windows 為基礎的單一圖形化使用者介面中撰寫、測試及偵錯指令碼。</span><span class="sxs-lookup"><span data-stu-id="f797a-105">In the ISE, you can run commands and write, test, and debug scripts in a single Windows-based graphic user interface.</span></span> <span data-ttu-id="f797a-106">ISE 提供多行編輯、TAB 鍵自動完成、語法顏色設定、選擇性執行、即時線上說明，以及支援從右至左的語言。</span><span class="sxs-lookup"><span data-stu-id="f797a-106">The ISE provides multiline editing, tab completion, syntax coloring, selective execution, context-sensitive help, and support for right-to-left languages.</span></span> <span data-ttu-id="f797a-107">功能表項目與鍵盤快速鍵會對應到您在 Windows PowerShell 主控台中執行的許多相同工作。</span><span class="sxs-lookup"><span data-stu-id="f797a-107">Menu items and keyboard shortcuts are mapped to many of the same tasks that you would do in the Windows PowerShell console.</span></span> <span data-ttu-id="f797a-108">例如，當您在 ISE 中偵錯指令碼時，可在編輯窗格中以滑鼠右鍵按一下程式碼行來設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="f797a-108">For example, when you debug a script in the ISE, you can right-click on a line of code in the edit pane to set a breakpoint.</span></span>

## <a name="support"></a><span data-ttu-id="f797a-109">支援</span><span class="sxs-lookup"><span data-stu-id="f797a-109">Support</span></span>

<span data-ttu-id="f797a-110">ISE 最初是透過 Windows PowerShell V2 引進，並透過 PowerShell V3 重新設計。</span><span class="sxs-lookup"><span data-stu-id="f797a-110">The ISE was first introduced with Windows PowerShell V2 and was re-designed with PowerShell V3.</span></span> <span data-ttu-id="f797a-111">Windows PowerShell V5.1 (含) 以下的所有 Windows PowerShell 版本均支援 ISE。</span><span class="sxs-lookup"><span data-stu-id="f797a-111">The ISE is supported in all supported versions of Windows PowerShell up to and including Windows PowerShell V5.1.</span></span> <span data-ttu-id="f797a-112">不過，ISE 目前處於維護模式，而且可能不會新增功能。</span><span class="sxs-lookup"><span data-stu-id="f797a-112">The ISE, however, is in maintenance mode and no new features are likely to be added.</span></span>
<span data-ttu-id="f797a-113">此外，PowerShell v6 及更新版本不支援 ISE。</span><span class="sxs-lookup"><span data-stu-id="f797a-113">Additionally, there is no support for the ISE with PowerShell v6 and beyond.</span></span> <span data-ttu-id="f797a-114">想要使用圖形化工具來管理 PowerShell 指令碼等項目的使用者應該考慮 [Visual Studio Code](https://code.visualstudio.com/) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="f797a-114">Users wanting a graphical tool with which to manage PowerShell scripts, etc, should consider [Visual Studio Code](https://code.visualstudio.com/).</span></span>

## <a name="key-features"></a><span data-ttu-id="f797a-115">重要功能</span><span class="sxs-lookup"><span data-stu-id="f797a-115">Key Features</span></span>

<span data-ttu-id="f797a-116">Windows PowerShell ISE 的重要功能包括：</span><span class="sxs-lookup"><span data-stu-id="f797a-116">Key features in Windows PowerShell ISE include:</span></span>

- <span data-ttu-id="f797a-117">多行編輯：若要在 [命令] 窗格中目前的行下方插入空行，請按下 SHIFT+ENTER。</span><span class="sxs-lookup"><span data-stu-id="f797a-117">Multiline editing: To insert a blank line under the current line in the Command pane, press SHIFT+ENTER.</span></span>
- <span data-ttu-id="f797a-118">選擇性執行：若要執行指令碼中的某部分，請選取您要執行的文字，然後按一下 [執行指令碼] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f797a-118">Selective execution: To run part of a script, select the text you want to run, and then click the **Run Script** button.</span></span> <span data-ttu-id="f797a-119">或者，按下 F5。</span><span class="sxs-lookup"><span data-stu-id="f797a-119">Or, press F5.</span></span>
- <span data-ttu-id="f797a-120">即時線上說明：鍵入 **Invoke-Item**，然後按 F1。</span><span class="sxs-lookup"><span data-stu-id="f797a-120">Context-sensitive help: Type **Invoke-Item**, and then press F1.</span></span> <span data-ttu-id="f797a-121">說明檔案隨即開啟，並顯示適用於 **Invoke-Item** Cmdlet 的文章。</span><span class="sxs-lookup"><span data-stu-id="f797a-121">The Help file opens to the article for the **Invoke-Item** cmdlet.</span></span>

<span data-ttu-id="f797a-122">Windows PowerShell ISE 可讓您自訂其部分外觀。</span><span class="sxs-lookup"><span data-stu-id="f797a-122">The Windows PowerShell ISE lets you customize some aspects of its appearance.</span></span> <span data-ttu-id="f797a-123">它也有自己的 Windows PowerShell 設定檔指令碼。</span><span class="sxs-lookup"><span data-stu-id="f797a-123">It also has its own Windows PowerShell profile script.</span></span>

## <a name="to-start-the-windows-powershell-ise"></a><span data-ttu-id="f797a-124">啟動 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="f797a-124">To start the Windows PowerShell ISE</span></span>

<span data-ttu-id="f797a-125">按一下 [開始]、選取 [Windows PowerShell]，然後按一下 [Windows PowerShell ISE]。</span><span class="sxs-lookup"><span data-stu-id="f797a-125">Click **Start**, select **Windows PowerShell**, and then click **Windows PowerShell ISE**.</span></span>
<span data-ttu-id="f797a-126">或者，您可以在任何命令殼層或在 [執行] 方塊中輸入 `powershell_ise.exe`。</span><span class="sxs-lookup"><span data-stu-id="f797a-126">Alternately, you can type `powershell_ise.exe` in any command shell or in the Run box.</span></span>

## <a name="to-get-help-in-the-windows-powershell-ise"></a><span data-ttu-id="f797a-127">在 Windows PowerShell ISE 中取得說明</span><span class="sxs-lookup"><span data-stu-id="f797a-127">To get Help in the Windows PowerShell ISE</span></span>

<span data-ttu-id="f797a-128">在 **[說明]** 功能表上，按一下 **[Windows PowerShell 說明]**。</span><span class="sxs-lookup"><span data-stu-id="f797a-128">On the **Help** menu, click **Windows PowerShell Help**.</span></span> <span data-ttu-id="f797a-129">或者，按下 F1。</span><span class="sxs-lookup"><span data-stu-id="f797a-129">Or, press F1.</span></span> <span data-ttu-id="f797a-130">開啟的檔案會描述 Windows PowerShell ISE 與 Windows PowerShell，包括可從 Get-Help Cmdlet 取得的所有說明。</span><span class="sxs-lookup"><span data-stu-id="f797a-130">The file that opens describes Windows PowerShell ISE and Windows PowerShell, including all of the help available from the Get-Help cmdlet.</span></span>
