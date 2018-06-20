---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Windows PowerShell ISE 簡介
ms.openlocfilehash: b09e64d0258d11f1f16f96b319ef232ebdfa0c49
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952897"
---
# <a name="introducing-the-windows-powershell-ise"></a><span data-ttu-id="fabc5-103">Windows PowerShell ISE 簡介</span><span class="sxs-lookup"><span data-stu-id="fabc5-103">Introducing the Windows PowerShell ISE</span></span>

<span data-ttu-id="fabc5-104">Windows PowerShell 整合式指令碼環境 (ISE) 是適用於 Windows PowerShell 的主機應用程式。</span><span class="sxs-lookup"><span data-stu-id="fabc5-104">The Windows PowerShell Integrated Scripting Environment (ISE) is a host application for Windows PowerShell.</span></span> <span data-ttu-id="fabc5-105">在 Windows PowerShell ISE 中，您可以在單一 Windows 架構的圖形化使用者介面中執行命令，以及撰寫、測試及偵錯指令碼，此介面支援多行編輯、Tab 鍵自動完成、語法著色、選擇式執行、即時線上說明，以及從右至左的語言支援。</span><span class="sxs-lookup"><span data-stu-id="fabc5-105">In Windows PowerShell ISE, you can run commands and write, test, and debug scripts in a single Windows-based graphic user interface with multiline editing, tab completion, syntax coloring, selective execution, context-sensitive help, and support for right-to-left languages.</span></span> <span data-ttu-id="fabc5-106">您可以使用功能表項目與鍵盤快速鍵，來執行您在 Windows PowerShell 中執行的許多相同工作。</span><span class="sxs-lookup"><span data-stu-id="fabc5-106">You can use menu items and keyboard shortcuts to perform many of the same tasks that you would perform in the Windows PowerShell console.</span></span> <span data-ttu-id="fabc5-107">例如，當您在 Windows PowerShell ISE 中針對指令碼進行偵錯時，若要在指令碼中設定行中斷點，可在程式碼行上按一下滑鼠右鍵，然後按一下 [切換中斷點]。</span><span class="sxs-lookup"><span data-stu-id="fabc5-107">For example, when you debug a script in the Windows PowerShell ISE, to set a line breakpoint in a script, right-click the line of code, and then click **Toggle Breakpoint**.</span></span>

<span data-ttu-id="fabc5-108">在 Windows PowerShell ISE 中嘗試使用這些功能</span><span class="sxs-lookup"><span data-stu-id="fabc5-108">Try these features in Windows PowerShell ISE.</span></span>

- <span data-ttu-id="fabc5-109">多行編輯：若要在 [命令] 窗格中的目前行下插入空行，請按 SHIFT+ENTER。</span><span class="sxs-lookup"><span data-stu-id="fabc5-109">Multiline editing: To insert a blank line under the current line in the Command pane, press SHIFT+ENTER.</span></span>
- <span data-ttu-id="fabc5-110">選擇性執行：若要執行指令碼中的某部分，請選取您要執行的文字，然後按一下 **[執行指令碼]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="fabc5-110">Selective execution: To run part of a script, select the text you want to run, and then click the **Run Script** button.</span></span> <span data-ttu-id="fabc5-111">或者，按下 F5。</span><span class="sxs-lookup"><span data-stu-id="fabc5-111">Or, press F5.</span></span>
- <span data-ttu-id="fabc5-112">即時線上說明：輸入 **Invoke-Item**，然後按 F1。</span><span class="sxs-lookup"><span data-stu-id="fabc5-112">Context-sensitive help: Type **Invoke-Item**, and then press F1.</span></span> <span data-ttu-id="fabc5-113">隨即開啟說明檔案，並顯示 **Invoke-Item** Cmdlet 的說明主題。</span><span class="sxs-lookup"><span data-stu-id="fabc5-113">The Help file opens to the Help topic for the **Invoke-Item** cmdlet.</span></span>

<span data-ttu-id="fabc5-114">Windows PowerShell ISE 可讓您自訂其部分外觀。</span><span class="sxs-lookup"><span data-stu-id="fabc5-114">The Windows PowerShell ISE lets you customize some aspects of its appearance.</span></span> <span data-ttu-id="fabc5-115">它也有自己的 Windows PowerShell 設定檔，您可以在其中儲存您在 Windows PowerShell ISE 中使用的函式、別名、變數與命令。</span><span class="sxs-lookup"><span data-stu-id="fabc5-115">It also has its own Windows PowerShell profile, where you can store functions, aliases, variables, and commands you use in the Windows PowerShell ISE.</span></span>

## <a name="to-start-the-windows-powershell-ise"></a><span data-ttu-id="fabc5-116">啟動 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="fabc5-116">To start the Windows PowerShell ISE</span></span>

<span data-ttu-id="fabc5-117">執行下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="fabc5-117">Do one of the following:</span></span>

- <span data-ttu-id="fabc5-118">按一下 **[開始]**、指向 **[所有程式]**、指向 **[Windows PowerShell V2]**，然後按一下 **[Windows PowerShell ISE]**。</span><span class="sxs-lookup"><span data-stu-id="fabc5-118">Click **Start**, point to **All Programs**, point to **Windows PowerShell V2**, and then click **Windows PowerShell ISE**.</span></span>
- <span data-ttu-id="fabc5-119">在 Windows PowerShell 主控台 Cmd.exe 或 [執行] 方塊中，輸入 **powershell_ise.exe**。</span><span class="sxs-lookup"><span data-stu-id="fabc5-119">In the Windows PowerShell console Cmd.exe, or in the Run box, type, **powershell_ise.exe**.</span></span>

## <a name="to-get-help-in-the-windows-powershell-ise"></a><span data-ttu-id="fabc5-120">在 Windows PowerShell ISE 中取得說明</span><span class="sxs-lookup"><span data-stu-id="fabc5-120">To get Help in the Windows PowerShell ISE</span></span>

<span data-ttu-id="fabc5-121">在 **[說明]** 功能表上，按一下 **[Windows PowerShell 說明]**。</span><span class="sxs-lookup"><span data-stu-id="fabc5-121">On the **Help** menu, click **Windows PowerShell Help**.</span></span> <span data-ttu-id="fabc5-122">或者，按下 F1。</span><span class="sxs-lookup"><span data-stu-id="fabc5-122">Or, press F1.</span></span> <span data-ttu-id="fabc5-123">開啟的檔案會描述 Windows PowerShell ISE 與 Windows PowerShell，包括可從 Get-Help Cmdlet 取得的所有說明。</span><span class="sxs-lookup"><span data-stu-id="fabc5-123">The file that opens describes Windows PowerShell ISE and Windows PowerShell, including all of the help available from the Get-Help cmdlet.</span></span>