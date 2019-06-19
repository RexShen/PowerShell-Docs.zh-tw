---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 探索 Windows PowerShell ISE
ms.openlocfilehash: 8c47e236e2e345a887fc3af281e429f440e176ff
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2019
ms.locfileid: "67031038"
---
# <a name="exploring-the-windows-powershell-ise"></a><span data-ttu-id="59a15-103">探索 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="59a15-103">Exploring the Windows PowerShell ISE</span></span>

<span data-ttu-id="59a15-104">您可以使用 Windows PowerShell® 整合式指令碼環境 (ISE) 建立及執行命令和指令碼，並對其偵錯。</span><span class="sxs-lookup"><span data-stu-id="59a15-104">You can use the Windows PowerShell® Integrated Scripting Environment (ISE) to create, run, and debug commands and scripts.</span></span> <span data-ttu-id="59a15-105">Windows PowerShell ISE 是由功能表列、Windows PowerShell 索引標籤、工具列、指令碼索引標籤、指令碼窗格、主控台窗格、狀態列、文字大小滑桿和即時線上說明所組成。</span><span class="sxs-lookup"><span data-stu-id="59a15-105">The Windows PowerShell ISE consists of the menu bar, Windows PowerShell tabs, the toolbar, script tabs, a Script Pane, a Console Pane, a status bar, a text-size slider and context-sensitive Help.</span></span>

> [!NOTE]
> <span data-ttu-id="59a15-106">從 Windows PowerShell ISE 3.0 開始，命令窗格和輸出窗格已合併為單一主控台窗格。</span><span class="sxs-lookup"><span data-stu-id="59a15-106">Beginning with Windows PowerShell ISE 3.0 the Command and Output Panes were combined into a single Console Pane.</span></span>

## <a name="menu-bar"></a><span data-ttu-id="59a15-107">功能表列</span><span class="sxs-lookup"><span data-stu-id="59a15-107">Menu Bar</span></span>

<span data-ttu-id="59a15-108">功能表列包含 [檔案]  、[編輯]  、[檢視]  、[工具]  、[偵錯]  、[附加元件]  和 [說明]  功能表。</span><span class="sxs-lookup"><span data-stu-id="59a15-108">The menu bar contains the **File**, **Edit**, **View**, **Tools**, **Debug**, **Add-ons**, and **Help** menus.</span></span> <span data-ttu-id="59a15-109">功能表上的按鈕可讓您在 Windows PowerShell ISE 中執行與寫入和執行指令碼，以及執行命令相關的工作。</span><span class="sxs-lookup"><span data-stu-id="59a15-109">The buttons on the menus allow you to perform tasks related to writing and running scripts and running commands in the Windows PowerShell ISE.</span></span> <span data-ttu-id="59a15-110">此外，您可以執行使用 [ISE 物件模型階層](../../core-powershell/ise/The-ISE-Object-Model-Hierarchy.md)的指令碼，將[附加元件工具](../../core-powershell/ise/The-ISEAddOnTool-Object.md)放在功能表列上。</span><span class="sxs-lookup"><span data-stu-id="59a15-110">Additionally, an [add-on tool](../../core-powershell/ise/The-ISEAddOnTool-Object.md) may be placed on the menu bar by running scripts that use the [The ISE Object Model Hierarchy](../../core-powershell/ise/The-ISE-Object-Model-Hierarchy.md).</span></span>

> [!NOTE]
> <span data-ttu-id="59a15-111">在 Windows PowerShell ISE 2.0 中，不提供 [工具]  和 [附加元件]  功能表。</span><span class="sxs-lookup"><span data-stu-id="59a15-111">In Windows PowerShell ISE 2.0, The **Tools** and **Add-ons** menus were not present.</span></span>

## <a name="windows-powershell-tabs"></a><span data-ttu-id="59a15-112">Windows PowerShell 索引標籤</span><span class="sxs-lookup"><span data-stu-id="59a15-112">Windows PowerShell Tabs</span></span>

<span data-ttu-id="59a15-113">Windows PowerShell 索引標籤是 Windows PowerShell 指令碼的執行環境。</span><span class="sxs-lookup"><span data-stu-id="59a15-113">A Windows PowerShell tab is the environment in which a Windows PowerShell script runs.</span></span> <span data-ttu-id="59a15-114">您可以在 Windows PowerShell ISE 中開啟新的 Windows PowerShell 索引標籤，在您的本機電腦或遠端電腦上建立個別環境。</span><span class="sxs-lookup"><span data-stu-id="59a15-114">You can open new Windows PowerShell tabs in the Windows PowerShell ISE to create separate environments on your local computer or on remote computers.</span></span> <span data-ttu-id="59a15-115">您最多可以同時開啟 8 個 PowerShell 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="59a15-115">You may have a maximum of eight PowerShell tabs simultaneously open.</span></span>

## <a name="toolbar"></a><span data-ttu-id="59a15-116">工具列</span><span class="sxs-lookup"><span data-stu-id="59a15-116">Toolbar</span></span>

<span data-ttu-id="59a15-117">您可以在工具列上找到下列按鈕。</span><span class="sxs-lookup"><span data-stu-id="59a15-117">The following buttons are located on the toolbar.</span></span>

|<span data-ttu-id="59a15-118">按鈕</span><span class="sxs-lookup"><span data-stu-id="59a15-118">Button</span></span>|<span data-ttu-id="59a15-119">函式</span><span class="sxs-lookup"><span data-stu-id="59a15-119">Function</span></span>|
|----------|------------|
|<span data-ttu-id="59a15-120">**新增**</span><span class="sxs-lookup"><span data-stu-id="59a15-120">**New**</span></span>|<span data-ttu-id="59a15-121">開啟新的指令碼。</span><span class="sxs-lookup"><span data-stu-id="59a15-121">Opens a new script.</span></span>|
|<span data-ttu-id="59a15-122">**開啟**</span><span class="sxs-lookup"><span data-stu-id="59a15-122">**Open**</span></span>|<span data-ttu-id="59a15-123">開啟現有的指令碼或檔案。</span><span class="sxs-lookup"><span data-stu-id="59a15-123">Opens an existing script or file.</span></span>|
|<span data-ttu-id="59a15-124">**儲存**</span><span class="sxs-lookup"><span data-stu-id="59a15-124">**Save**</span></span>|<span data-ttu-id="59a15-125">儲存指令碼或檔案。</span><span class="sxs-lookup"><span data-stu-id="59a15-125">Saves a script or file.</span></span>|
|<span data-ttu-id="59a15-126">**剪下**</span><span class="sxs-lookup"><span data-stu-id="59a15-126">**Cut**</span></span>|<span data-ttu-id="59a15-127">剪下選取的文字並複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="59a15-127">Cuts the selected text and copies it to the clipboard.</span></span>|
|<span data-ttu-id="59a15-128">**複製**</span><span class="sxs-lookup"><span data-stu-id="59a15-128">**Copy**</span></span>|<span data-ttu-id="59a15-129">將選取文字複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="59a15-129">Copies the selected text to the clipboard.</span></span>|
|<span data-ttu-id="59a15-130">**貼上**</span><span class="sxs-lookup"><span data-stu-id="59a15-130">**Paste**</span></span>|<span data-ttu-id="59a15-131">在游標位置貼上剪貼簿的內容。</span><span class="sxs-lookup"><span data-stu-id="59a15-131">Pastes the contents of the clipboard at the cursor location.</span></span>|
|<span data-ttu-id="59a15-132">**清除輸出窗格**</span><span class="sxs-lookup"><span data-stu-id="59a15-132">**Clear Output Pane**</span></span>|<span data-ttu-id="59a15-133">清除輸出窗格中的所有內容。</span><span class="sxs-lookup"><span data-stu-id="59a15-133">Clears all content in the Output Pane.</span></span>|
|<span data-ttu-id="59a15-134">**復原**</span><span class="sxs-lookup"><span data-stu-id="59a15-134">**Undo**</span></span>|<span data-ttu-id="59a15-135">回復剛才執行的動作。</span><span class="sxs-lookup"><span data-stu-id="59a15-135">Reverses the action that was just performed.</span></span>|
|<span data-ttu-id="59a15-136">**取消復原**</span><span class="sxs-lookup"><span data-stu-id="59a15-136">**Redo**</span></span>|<span data-ttu-id="59a15-137">執行剛才復原的動作。</span><span class="sxs-lookup"><span data-stu-id="59a15-137">Performs the action that was just undone.</span></span>|
|<span data-ttu-id="59a15-138">**執行指令碼**</span><span class="sxs-lookup"><span data-stu-id="59a15-138">**Run Script**</span></span>|<span data-ttu-id="59a15-139">執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="59a15-139">Runs a script.</span></span>|
|<span data-ttu-id="59a15-140">**執行選取項目**</span><span class="sxs-lookup"><span data-stu-id="59a15-140">**Run Selection**</span></span>|<span data-ttu-id="59a15-141">執行選取的指令碼部分。</span><span class="sxs-lookup"><span data-stu-id="59a15-141">Runs a selected portion of a script.</span></span>|
|<span data-ttu-id="59a15-142">**停止執行**</span><span class="sxs-lookup"><span data-stu-id="59a15-142">**Stop Execution**</span></span>|<span data-ttu-id="59a15-143">停止執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="59a15-143">Stops a script that is running.</span></span>|
|<span data-ttu-id="59a15-144">**新增遠端 PowerShell 索引標籤**</span><span class="sxs-lookup"><span data-stu-id="59a15-144">**New Remote PowerShell Tab**</span></span>|<span data-ttu-id="59a15-145">建立新的 PowerShell 索引標籤，以在遠端電腦上建立工作階段。</span><span class="sxs-lookup"><span data-stu-id="59a15-145">Creates a new PowerShell Tab that establishes a session on a remote computer.</span></span> <span data-ttu-id="59a15-146">對話方塊隨即出現，並提示您輸入建立遠端連線所需的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="59a15-146">A dialog box appears and prompts you to enter details required to establish the remote connection.</span></span>|
|<span data-ttu-id="59a15-147">**啟動 PowerShell.exe**</span><span class="sxs-lookup"><span data-stu-id="59a15-147">**Start PowerShell.exe**</span></span>|<span data-ttu-id="59a15-148">開啟 PowerShell 主控台。</span><span class="sxs-lookup"><span data-stu-id="59a15-148">Opens a PowerShell Console.</span></span>|
|<span data-ttu-id="59a15-149">**靠上顯示指令碼窗格**</span><span class="sxs-lookup"><span data-stu-id="59a15-149">**Show Script Pane Top**</span></span>|<span data-ttu-id="59a15-150">將指令碼窗格移至顯示畫面上方。</span><span class="sxs-lookup"><span data-stu-id="59a15-150">Moves the Script Pane to the top in the display.</span></span>|
|<span data-ttu-id="59a15-151">**靠右顯示指令碼窗格**</span><span class="sxs-lookup"><span data-stu-id="59a15-151">**Show Script Pane Right**</span></span>|<span data-ttu-id="59a15-152">將指令碼窗格移至顯示畫面右側。</span><span class="sxs-lookup"><span data-stu-id="59a15-152">Moves the Script Pane to the right in the display.</span></span>|
|<span data-ttu-id="59a15-153">**顯示最大化的指令碼窗格**</span><span class="sxs-lookup"><span data-stu-id="59a15-153">**Show Script Pane Maximized**</span></span>|<span data-ttu-id="59a15-154">將指令碼窗格最大化。</span><span class="sxs-lookup"><span data-stu-id="59a15-154">Maximizes the Script Pane.</span></span>|

## <a name="script-tab"></a><span data-ttu-id="59a15-155">指令碼索引標籤</span><span class="sxs-lookup"><span data-stu-id="59a15-155">Script Tab</span></span>

<span data-ttu-id="59a15-156">顯示您正在編輯的指令碼名稱。</span><span class="sxs-lookup"><span data-stu-id="59a15-156">Displays the name of the script you are editing.</span></span> <span data-ttu-id="59a15-157">您可以按一下指令碼索引標籤，選取要編輯的指令碼。</span><span class="sxs-lookup"><span data-stu-id="59a15-157">You can click a script tab to select the script you want to edit.</span></span>

<span data-ttu-id="59a15-158">當您指向指令碼索引標籤時，指令碼檔案的完整路徑會顯示在工具提示中。</span><span class="sxs-lookup"><span data-stu-id="59a15-158">When you point to the script tab, the fully qualified path to the script file appears in a tooltip.</span></span>

## <a name="script-pane"></a><span data-ttu-id="59a15-159">指令碼窗格</span><span class="sxs-lookup"><span data-stu-id="59a15-159">Script Pane</span></span>

<span data-ttu-id="59a15-160">可讓您建立及執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="59a15-160">Allows you to create and run scripts.</span></span> <span data-ttu-id="59a15-161">您可以在指令碼窗格中開啟、編輯及執行現有的指令碼。</span><span class="sxs-lookup"><span data-stu-id="59a15-161">You can open, edit and run existing scripts in the Script Pane.</span></span>

## <a name="output-pane"></a><span data-ttu-id="59a15-162">輸出窗格</span><span class="sxs-lookup"><span data-stu-id="59a15-162">Output Pane</span></span>

<span data-ttu-id="59a15-163">顯示已執行的命令和指令碼結果。</span><span class="sxs-lookup"><span data-stu-id="59a15-163">Displays the results of the commands and scripts you have run.</span></span> <span data-ttu-id="59a15-164">您也可以複製並清除輸出窗格中的內容。</span><span class="sxs-lookup"><span data-stu-id="59a15-164">You can also copy and clear the contents in the Output Pane.</span></span>

## <a name="command-pane"></a><span data-ttu-id="59a15-165">命令窗格</span><span class="sxs-lookup"><span data-stu-id="59a15-165">Command Pane</span></span>

<span data-ttu-id="59a15-166">可讓您撰寫命令。</span><span class="sxs-lookup"><span data-stu-id="59a15-166">Allows you to write commands.</span></span> <span data-ttu-id="59a15-167">您可以在命令窗格中執行一或多行命令。</span><span class="sxs-lookup"><span data-stu-id="59a15-167">You can run a one line command or a multiline command in the Command Pane.</span></span> <span data-ttu-id="59a15-168">按 SHIFT+ENTER 可輸入多行命令的每一行，而在最後一行後面按 ENTER 鍵可執行多行命令。</span><span class="sxs-lookup"><span data-stu-id="59a15-168">Press SHIFT+ENTER to enter each line of a multiline command, and press ENTER after the last line to execute the multiline command.</span></span> <span data-ttu-id="59a15-169">出現在命令窗格頂端的提示會顯示目前工作目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="59a15-169">The prompt displayed on top of the Command Pane shows the path to the current working directory.</span></span>

## <a name="status-bar"></a><span data-ttu-id="59a15-170">狀態列</span><span class="sxs-lookup"><span data-stu-id="59a15-170">Status Bar</span></span>

<span data-ttu-id="59a15-171">可讓您查看所執行的命令和指令碼是否已完成。</span><span class="sxs-lookup"><span data-stu-id="59a15-171">Allows you to see whether the commands and scripts that you run are complete.</span></span> <span data-ttu-id="59a15-172">狀態列位於顯示畫面最底部。</span><span class="sxs-lookup"><span data-stu-id="59a15-172">The status bar is at the very bottom of the display.</span></span> <span data-ttu-id="59a15-173">錯誤訊息的選定部分會顯示在狀態列上。</span><span class="sxs-lookup"><span data-stu-id="59a15-173">Selected portions of error messages are displayed on the status bar.</span></span>

## <a name="text-size-slider"></a><span data-ttu-id="59a15-174">文字大小滑桿</span><span class="sxs-lookup"><span data-stu-id="59a15-174">Text-Size Slider</span></span>

<span data-ttu-id="59a15-175">增加或減少螢幕上文字的大小。</span><span class="sxs-lookup"><span data-stu-id="59a15-175">Increases or decreases the size of the text on the screen.</span></span>

## <a name="help"></a><span data-ttu-id="59a15-176">[說明]</span><span class="sxs-lookup"><span data-stu-id="59a15-176">Help</span></span>

<span data-ttu-id="59a15-177">您可以在 Web 上的 TechNet Library 中取得 Windows PowerShell ISE 的說明。</span><span class="sxs-lookup"><span data-stu-id="59a15-177">Help for Windows PowerShell ISE is available on the Web in the TechNet Library.</span></span> <span data-ttu-id="59a15-178">開啟 [說明] 的方式是在 **[說明]** 功能表上按一下 **[Windows PowerShell ISE 說明]** ，或在在指令碼窗格或主控台窗格的任何位置按下 F1 鍵 (但游標不可以在 Cmdlet 名稱上方)。</span><span class="sxs-lookup"><span data-stu-id="59a15-178">You can open the Help by clicking **Windows PowerShell ISE Help** on the **Help** menu or by pressing the F1 key anywhere except when the cursor is on a cmdlet name in either the Script Pane or the Console Pane.</span></span> <span data-ttu-id="59a15-179">您也可以從 [說明]  功能表執行 Update-Help Cmdlet，並顯示命令視窗，透過顯示 Cmdlet 的所有參數並讓您在容易使用的表單中填入參數，來協助您建構命令。</span><span class="sxs-lookup"><span data-stu-id="59a15-179">From the **Help** menu you can also run the Update-Help cmdlet, and display the Command Window which assists you in constructing commands by showing you all of the parameters for a cmdlet and enabling you to fill in the parameters in an easy-to-use form.</span></span>

## <a name="see-also"></a><span data-ttu-id="59a15-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59a15-180">See Also</span></span>

- [<span data-ttu-id="59a15-181">Windows PowerShell ISE 簡介</span><span class="sxs-lookup"><span data-stu-id="59a15-181">Introducing the Windows PowerShell ISE</span></span>](../../core-powershell/ise/Introducing-the-Windows-PowerShell-ISE.md)
