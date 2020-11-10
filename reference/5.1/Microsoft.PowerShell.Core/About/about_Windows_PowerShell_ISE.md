---
description: 說明 Windows PowerShell 整合式腳本環境 (ISE) 的功能和系統需求。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_powershell_ise?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_PowerShell_ISE
ms.openlocfilehash: ff543024d7c62c70217eeaf3ded192a5a24c4757
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388836"
---
# <a name="about-windows-powershell-ise"></a><span data-ttu-id="779b7-104">關於 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="779b7-104">About Windows PowerShell ISE</span></span>

## <a name="short-description"></a><span data-ttu-id="779b7-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="779b7-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="779b7-106">說明 Windows PowerShell 整合式腳本環境 (ISE) 的功能和系統需求。</span><span class="sxs-lookup"><span data-stu-id="779b7-106">Describes the features and system requirements of Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="long-description"></a><span data-ttu-id="779b7-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="779b7-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="779b7-108">Windows PowerShell ISE 是 Windows PowerShell 的圖形化主機應用程式。</span><span class="sxs-lookup"><span data-stu-id="779b7-108">Windows PowerShell ISE is a graphical host application for Windows PowerShell.</span></span>
<span data-ttu-id="779b7-109">在 Windows PowerShell ISE 中，您可以在以 Windows 為基礎的單一圖形化使用者介面中執行命令，以及撰寫、測試和調試腳本。</span><span class="sxs-lookup"><span data-stu-id="779b7-109">In Windows PowerShell ISE, you can run commands and write, test, and debug scripts in a single Windows-based graphical user interface.</span></span> <span data-ttu-id="779b7-110">其功能包括 Intellisense、多行編輯、tab 鍵自動完成、自動儲存、語法著色、選擇性執行、即時線上說明、顯示命令 (在視窗) 撰寫命令，以及支援雙位元組字元集和從右至左的語言。</span><span class="sxs-lookup"><span data-stu-id="779b7-110">Its features include Intellisense, multiline editing, tab completion, auto-save, syntax coloring, selective execution, context-sensitive help, Show Command (compose commands in a window) and support for double-byte character sets and right-to-left languages.</span></span>

<span data-ttu-id="779b7-111">Windows PowerShell ISE 是適用于初學者的絕佳工具。</span><span class="sxs-lookup"><span data-stu-id="779b7-111">Windows PowerShell ISE is an excellent tool for beginners.</span></span> <span data-ttu-id="779b7-112">[顯示命令視窗] 和 [新增遠端 PowerShell] 索引標籤會引導您完成工作，讓您可以在第一次嘗試時成功。</span><span class="sxs-lookup"><span data-stu-id="779b7-112">The Show Command window and New Remote PowerShell Tab guide you through tasks so that you can be successful on the first try.</span></span> <span data-ttu-id="779b7-113">程式碼片段和錯誤指標可協助您在工作時學習 Windows PowerShell 的語言。</span><span class="sxs-lookup"><span data-stu-id="779b7-113">Snippets and error indicators help you learn the Windows PowerShell language as you work.</span></span>

<span data-ttu-id="779b7-114">Advanced users 可以利用精密的偵錯工具功能、附加元件和 Windows PowerShell ISE 物件模型。</span><span class="sxs-lookup"><span data-stu-id="779b7-114">Advanced users can take advantage of the sophisticated debugging features, add-ons, and the Windows PowerShell ISE object model.</span></span>

<span data-ttu-id="779b7-115">Windows PowerShell 4.0 中 Windows PowerShell ISE 的新功能</span><span class="sxs-lookup"><span data-stu-id="779b7-115">What's New in Windows PowerShell ISE in Windows PowerShell 4.0</span></span>

<span data-ttu-id="779b7-116">Windows PowerShell ISE 在 Windows PowerShell 4.0 中引進了兩項新功能。</span><span class="sxs-lookup"><span data-stu-id="779b7-116">Windows PowerShell ISE introduces two new features in Windows PowerShell 4.0.</span></span>

- <span data-ttu-id="779b7-117">Windows PowerShell ISE 現在支援 Windows PowerShell 工作流程調試和遠端腳本的調試。</span><span class="sxs-lookup"><span data-stu-id="779b7-117">Windows PowerShell ISE now supports both Windows PowerShell Workflow debugging and remote script debugging.</span></span> <span data-ttu-id="779b7-118">如需詳細資訊，請參閱 about_Debuggers。</span><span class="sxs-lookup"><span data-stu-id="779b7-118">For more Information, see about_Debuggers.</span></span>

- <span data-ttu-id="779b7-119">已新增對 Windows PowerShell 預期狀態設定之提供者與設定的 IntelliSense 支援。</span><span class="sxs-lookup"><span data-stu-id="779b7-119">IntelliSense support has been added for Windows PowerShell Desired State Configuration providers and configurations.</span></span>

## <a name="starting-windows-powershell-ise"></a><span data-ttu-id="779b7-120">開始 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="779b7-120">Starting Windows PowerShell ISE</span></span>

<span data-ttu-id="779b7-121">您可以在所有支援的 Windows 版本中安裝、啟用和準備使用 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="779b7-121">Windows PowerShell ISE is installed, enabled, and ready to use in all supported versions of Windows.</span></span>

- <span data-ttu-id="779b7-122">在 Windows 8.1、Windows 8、Windows Server 2012 R2 和 Windows Server 2012 的 [開始畫面上，輸入 PowerShell_ISE，然後按一下 [PowerShell_ISE] 或 [Windows PowerShell ISE]。</span><span class="sxs-lookup"><span data-stu-id="779b7-122">In Windows 8.1, Windows 8, Windows Server 2012 R2, and Windows Server 2012, on the Start screen, type PowerShell_ISE, and then click PowerShell_ISE or Windows PowerShell ISE.</span></span>

- <span data-ttu-id="779b7-123">在 Windows Server 2012 R2 和 Windows Server 2012 的伺服器管理員中，按一下 [工具] 功能表上的 [Windows PowerShell ISE]。</span><span class="sxs-lookup"><span data-stu-id="779b7-123">In Windows Server 2012 R2 and Windows Server 2012, in Server Manager, on the Tools menu, click Windows PowerShell ISE.</span></span>

- <span data-ttu-id="779b7-124">在舊版的 Windows 中，依序按一下 [開始]、[所有程式]、[附屬應用程式] Windows PowerShell，然後按一下 [Windows PowerShell ISE]。</span><span class="sxs-lookup"><span data-stu-id="779b7-124">In earlier versions of Windows, click Start, All Programs, Accessories, Windows PowerShell, and then click Windows PowerShell ISE.</span></span>

- <span data-ttu-id="779b7-125">在 Windows PowerShell 主控台中，Cmd.exe，或 Windows 中的 [執行] 或 [搜尋] 方塊中，輸入 "PowerShell_ise.exe"。</span><span class="sxs-lookup"><span data-stu-id="779b7-125">In a Windows PowerShell console, Cmd.exe, or the Run or Search box in Windows, type "PowerShell_ise.exe".</span></span> <span data-ttu-id="779b7-126">您也可以使用命令列參數，包括 NoProfile 參數。</span><span class="sxs-lookup"><span data-stu-id="779b7-126">You can also use the command-line parameters, including the NoProfile switch.</span></span> <span data-ttu-id="779b7-127">如需詳細資訊，請參閱 [PowerShell_ISE.exe 主控台](about_powershell_ise_exe.md)說明。</span><span class="sxs-lookup"><span data-stu-id="779b7-127">For more information, see [PowerShell_ISE.exe Console Help](about_powershell_ise_exe.md).</span></span>

## <a name="running-interactive-commands"></a><span data-ttu-id="779b7-128">執行互動式命令</span><span class="sxs-lookup"><span data-stu-id="779b7-128">Running Interactive Commands</span></span>

<span data-ttu-id="779b7-129">您可以在 Windows PowerShell ISE 中執行任何 Windows PowerShell 運算式或命令。</span><span class="sxs-lookup"><span data-stu-id="779b7-129">You can run any Windows PowerShell expression or command in Windows PowerShell ISE.</span></span> <span data-ttu-id="779b7-130">您可以使用 Cmdlet、提供者、嵌入式管理單元和模組，就像在 Windows PowerShell 主控台中使用一樣。</span><span class="sxs-lookup"><span data-stu-id="779b7-130">You can use cmdlets, providers, snap-ins, and modules as you would use them in the Windows PowerShell console.</span></span>

<span data-ttu-id="779b7-131">您可以在主控台窗格中輸入或貼上互動式命令。</span><span class="sxs-lookup"><span data-stu-id="779b7-131">You can type or paste interactive commands in the Console pane.</span></span> <span data-ttu-id="779b7-132">若要執行命令，您可以使用按鈕、功能表項目和鍵盤快速鍵。</span><span class="sxs-lookup"><span data-stu-id="779b7-132">To run the commands, you can use buttons, menu items, and keyboard shortcuts.</span></span>

<span data-ttu-id="779b7-133">您可以使用多行編輯功能，一次在主控台窗格中輸入或貼上數行程式碼。</span><span class="sxs-lookup"><span data-stu-id="779b7-133">You can use the multiline editing feature to type or paste several lines of code into the Console pane at once.</span></span> <span data-ttu-id="779b7-134">當您按向上鍵來重新叫用先前的命令時，命令中的所有行都會被回收。</span><span class="sxs-lookup"><span data-stu-id="779b7-134">When you press the UP ARROW key to recall the previous command, all the lines in the command are recalled.</span></span> <span data-ttu-id="779b7-135">當您輸入命令時，請按 SHIFT + ENTER 鍵，讓新的空白行出現在目前的行下方。</span><span class="sxs-lookup"><span data-stu-id="779b7-135">When you type commands, press SHIFT+ENTER to make a new blank line appear under the current line.</span></span>

## <a name="viewing-output"></a><span data-ttu-id="779b7-136">查看輸出</span><span class="sxs-lookup"><span data-stu-id="779b7-136">Viewing Output</span></span>

<span data-ttu-id="779b7-137">命令和腳本的結果會顯示在主控台窗格中。</span><span class="sxs-lookup"><span data-stu-id="779b7-137">The results of commands and scripts are displayed in the Console pane.</span></span> <span data-ttu-id="779b7-138">您可以使用鍵盤快速鍵或工具列上的 [複製] 按鈕來移動或複製主控台窗格中的結果，也可以在腳本窗格或主控台窗格或其他程式中貼上結果。</span><span class="sxs-lookup"><span data-stu-id="779b7-138">You can move or copy the results from the Console pane by using keyboard shortcuts or the Copy button on the toolbar, and you can paste the results in the Script pane or Console panes or other programs.</span></span> <span data-ttu-id="779b7-139">若要清除主控台窗格，請按一下 [清除輸出窗格] 按鈕，或輸入下列其中一個命令：</span><span class="sxs-lookup"><span data-stu-id="779b7-139">To clear the Console pane, click the "Clear Output Pane" button or type one of the following commands:</span></span>

```
Clear-Host
cls
```

## <a name="writing-scripts-and-functions"></a><span data-ttu-id="779b7-140">撰寫腳本和函式</span><span class="sxs-lookup"><span data-stu-id="779b7-140">Writing Scripts and Functions</span></span>

<span data-ttu-id="779b7-141">在腳本窗格中，您可以開啟、撰寫、編輯和執行腳本。</span><span class="sxs-lookup"><span data-stu-id="779b7-141">In the Script pane, you can open, compose, edit, and run scripts.</span></span> <span data-ttu-id="779b7-142">腳本窗格可讓您使用按鈕和鍵盤快速鍵來編輯腳本。</span><span class="sxs-lookup"><span data-stu-id="779b7-142">The Script pane lets you edit scripts by using buttons and keyboard shortcuts.</span></span> <span data-ttu-id="779b7-143">您也可以在腳本窗格和主控台窗格之間複製、剪下和貼上文字。</span><span class="sxs-lookup"><span data-stu-id="779b7-143">You can also copy, cut, and paste text between the Script pane and the Console pane.</span></span>

<span data-ttu-id="779b7-144">您可以使用選擇性執行功能來執行全部或部分的腳本。</span><span class="sxs-lookup"><span data-stu-id="779b7-144">You can use the selective run feature to run all or part of a script.</span></span> <span data-ttu-id="779b7-145">若要執行腳本的一部分，請選取您要執行的文字，然後按一下 [執行選取範圍] 按鈕或按下 F8。</span><span class="sxs-lookup"><span data-stu-id="779b7-145">To run part of a script, select the text you want to run, and then click the Run Selection button or press F8.</span></span> <span data-ttu-id="779b7-146">根據預設，F8 會執行目前的行。</span><span class="sxs-lookup"><span data-stu-id="779b7-146">By default, F8 runs the current line.</span></span>

<span data-ttu-id="779b7-147">先進的編輯功能包括大括弧比對、展開-折迭、行號、錯誤指標、區塊編輯和縮排、rich copy 和大小寫轉換。</span><span class="sxs-lookup"><span data-stu-id="779b7-147">Advanced editing features include brace-matching, expand-collapse, line numbers, error indicators, block editing and indenting, rich copy, and case conversion.</span></span>

## <a name="getting-help"></a><span data-ttu-id="779b7-148">取得協助</span><span class="sxs-lookup"><span data-stu-id="779b7-148">Getting Help</span></span>

<span data-ttu-id="779b7-149">Windows PowerShell ISE 包含描述其用法的說明主題。</span><span class="sxs-lookup"><span data-stu-id="779b7-149">Windows PowerShell ISE includes help topics that describe its use.</span></span> <span data-ttu-id="779b7-150">此外，您可以從腳本和命令窗格存取所有已安裝的說明檔。</span><span class="sxs-lookup"><span data-stu-id="779b7-150">In addition, all installed help files are accessible from the Script and Command panes.</span></span>

<span data-ttu-id="779b7-151">Windows PowerShell ISE 也支援即時線上說明。</span><span class="sxs-lookup"><span data-stu-id="779b7-151">Windows PowerShell ISE also supports context-sensitive help.</span></span> <span data-ttu-id="779b7-152">若要取得特定 Cmdlet、提供者或關鍵字的說明，請將游標放在專案的名稱，然後按下 F1。</span><span class="sxs-lookup"><span data-stu-id="779b7-152">To get help about a particular cmdlet, provider, or keyword, place the cursor in the name of the item and press F1.</span></span> <span data-ttu-id="779b7-153">若要搜尋說明主題，請按 F1 並輸入搜尋字詞。</span><span class="sxs-lookup"><span data-stu-id="779b7-153">To search the help topics, press F1 and type the search term.</span></span>

<span data-ttu-id="779b7-154">若要更新電腦上的說明主題，請使用 [說明] 功能表中的 [更新 Windows PowerShell 說明] 專案。</span><span class="sxs-lookup"><span data-stu-id="779b7-154">To update the help topics on the computer, use the Update Windows PowerShell Help item in the Help menu.</span></span> <span data-ttu-id="779b7-155">此專案會在目前的 UI 文化特性中，更新目前會話中模組的說明。</span><span class="sxs-lookup"><span data-stu-id="779b7-155">This item updates help for the modules in the current session in the current UI culture.</span></span> <span data-ttu-id="779b7-156">它相當於執行不含參數的 Update-Help Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="779b7-156">It is equivalent to running the Update-Help cmdlet without parameters.</span></span> <span data-ttu-id="779b7-157">若要更新 Windows PowerShell 隨附的 Cmdlet 說明，請使用 [以系統管理員身分執行] 選項開始 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="779b7-157">To update help for the cmdlets that come with Windows PowerShell, start Windows PowerShell ISE with the "Run as administrator" option.</span></span>

<span data-ttu-id="779b7-158">您也可以在 Windows PowerShell ISE 中使用 Get-help、Save-Help 和 Update-Help Cmdlet，就像在 Windows PowerShell 主控台中使用一樣。</span><span class="sxs-lookup"><span data-stu-id="779b7-158">You can also use the Get-Help, Save-Help, and Update-Help cmdlets in Windows PowerShell ISE, just as you use it in the Windows PowerShell console.</span></span> <span data-ttu-id="779b7-159">不過，在 Windows PowerShell ISE 中，Help 函式會顯示整個說明主題，而不是一次一個頁面。</span><span class="sxs-lookup"><span data-stu-id="779b7-159">However, in Windows PowerShell ISE, the Help function displays the entire help topic, not one page at a time.</span></span>

## <a name="debugging-scripts"></a><span data-ttu-id="779b7-160">調試腳本</span><span class="sxs-lookup"><span data-stu-id="779b7-160">Debugging Scripts</span></span>

<span data-ttu-id="779b7-161">您可以使用 Windows PowerShell ISE 偵錯工具來進行 Windows PowerShell 腳本或函式的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="779b7-161">You can use the Windows PowerShell ISE debugger to debug a Windows PowerShell script or function.</span></span> <span data-ttu-id="779b7-162">當您對腳本進行偵錯工具時，您可以使用功能表項目和快速鍵來執行您在 Windows PowerShell 主控台中執行的許多相同工作。</span><span class="sxs-lookup"><span data-stu-id="779b7-162">When you debug a script, you can use menu items and shortcut keys to perform many of the same tasks that you would perform in the Windows PowerShell console.</span></span> <span data-ttu-id="779b7-163">例如，若要在腳本中設定行中斷點，請在程式程式碼上按一下滑鼠右鍵，然後按一下 [切換中斷點]。</span><span class="sxs-lookup"><span data-stu-id="779b7-163">For example, to set a line breakpoint in a script, right-click the line of code, and then click Toggle Breakpoint.</span></span>

<span data-ttu-id="779b7-164">當您在偵錯工具中逐步執行腳本時，偵錯工具會精確地顯示命令的哪個部分正在執行，並自動開啟包含所呼叫函式和腳本的檔案。</span><span class="sxs-lookup"><span data-stu-id="779b7-164">As you step through a script while debugging, the debugging highlighter shows precisely which part of the command is running and automatically opens files that include called functions and scripts.</span></span>

<span data-ttu-id="779b7-165">根據預設，切換中斷點功能表項目會在腳本中的整個程式列上設定中斷點，但您可以在變數或命令名稱上設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="779b7-165">By default, the Toggle Breakpoint menu item sets a breakpoint on an entire line in a script, but you can set a breakpoint on a variable or command name.</span></span>
<span data-ttu-id="779b7-166">您也可以根據行號和資料行編號，在命令上設定中斷點，讓您更輕鬆地進行較長的管線命令的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="779b7-166">You can also set a breakpoint on a command by line and column number, making it easier to debug long pipeline commands.</span></span>

<span data-ttu-id="779b7-167">通常，您只要在 Windows PowerShell ISE 中開啟腳本檔案，就可以在腳本中進行語法錯誤的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="779b7-167">Often, you can debug syntax errors in a script just by opening the script file in Windows PowerShell ISE.</span></span> <span data-ttu-id="779b7-168">錯誤指標會識別語法錯誤和大綱功能，可讓您折迭腳本的各個部分以專注于問題點。</span><span class="sxs-lookup"><span data-stu-id="779b7-168">The error indicators identify syntax errors and the outlining features let you collapse parts of the script to focus on trouble spots.</span></span>

<span data-ttu-id="779b7-169">您也可以在命令窗格中使用 Windows PowerShell 偵錯工具 Cmdlet，就如同您在主控台中使用它們一樣。</span><span class="sxs-lookup"><span data-stu-id="779b7-169">You can also use the Windows PowerShell debugger cmdlets in the Command pane just as you would use them in the console.</span></span>

## <a name="running-remote-commands"></a><span data-ttu-id="779b7-170">執行遠端命令</span><span class="sxs-lookup"><span data-stu-id="779b7-170">Running Remote Commands</span></span>

<span data-ttu-id="779b7-171">新的遠端 PowerShell 索引標籤功能，可讓您輕鬆地在本機電腦或遠端電腦上建立持續性的使用者管理 Windows PowerShell 會話 ( 「PSSession」 ) 。</span><span class="sxs-lookup"><span data-stu-id="779b7-171">The New Remote PowerShell Tab feature makes it easy to establish a persistent user-managed Windows PowerShell session ("PSSession") to the local computer or a remote computer.</span></span> <span data-ttu-id="779b7-172">此命令會開啟一個快顯視窗，提示您輸入電腦名稱稱，以及有權在遠端電腦上執行命令的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="779b7-172">The command opens a pop-up window that prompts you for a computer name and for the user account that has permission to run commands on the remote computer.</span></span>

## <a name="customizing-the-view"></a><span data-ttu-id="779b7-173">自訂視圖</span><span class="sxs-lookup"><span data-stu-id="779b7-173">Customizing the View</span></span>

<span data-ttu-id="779b7-174">您可以使用 Windows PowerShell ISE 功能來移動和調整主控台窗格和腳本窗格的大小。</span><span class="sxs-lookup"><span data-stu-id="779b7-174">You can use Windows PowerShell ISE features to move and to resize the Console pane and the Script pane.</span></span> <span data-ttu-id="779b7-175">您可以顯示和隱藏任一個窗格，也可以變更所有窗格中的文字大小。</span><span class="sxs-lookup"><span data-stu-id="779b7-175">You can show and hide either pane, and you can change the text size in all the panes.</span></span>

<span data-ttu-id="779b7-176">您也可以使用 [選項] 視窗來自訂 Windows PowerShell ISE 的外觀和操作。</span><span class="sxs-lookup"><span data-stu-id="779b7-176">You can also use the Options window to customize the appearance and operation of Windows PowerShell ISE.</span></span> <span data-ttu-id="779b7-177">此外，Windows PowerShell ISE 還有自訂主機變數 $psISE，您可以用來自訂 Windows PowerShell ISE，包括加入功能表和功能表項目。</span><span class="sxs-lookup"><span data-stu-id="779b7-177">In addition, Windows PowerShell ISE has a custom host variable, $psISE, that you can use to customize Windows PowerShell ISE, including adding menus and menu items.</span></span>

## <a name="windows-powershell-ise-profile"></a><span data-ttu-id="779b7-178">Windows PowerShell ISE 設定檔</span><span class="sxs-lookup"><span data-stu-id="779b7-178">Windows PowerShell ISE Profile</span></span>

<span data-ttu-id="779b7-179">Windows PowerShell ISE 有自己的 Windows PowerShell 設定檔 Microsoft.PowerShellISE_profile.ps1。</span><span class="sxs-lookup"><span data-stu-id="779b7-179">Windows PowerShell ISE has its own Windows PowerShell profile, Microsoft.PowerShellISE_profile.ps1.</span></span> <span data-ttu-id="779b7-180">在此設定檔中，您可以儲存 Windows PowerShell ISE 中使用的函式、別名、變數與命令。</span><span class="sxs-lookup"><span data-stu-id="779b7-180">In this profile, you can store functions, aliases, variables, and commands that you use in Windows PowerShell ISE.</span></span>

<span data-ttu-id="779b7-181">Windows PowerShell AllHosts 設定檔中的專案 (CurrentUser \\ AllHosts 和 AllUsers \\ AllHosts) 也可以在 Windows PowerShell ISE 中取得，就如同在任何 Windows PowerShell 主機程式中一樣。</span><span class="sxs-lookup"><span data-stu-id="779b7-181">Items in the Windows PowerShell AllHosts profiles (CurrentUser\\AllHosts and AllUsers\\AllHosts) are also available in Windows PowerShell ISE, just as they are in any Windows PowerShell host program.</span></span> <span data-ttu-id="779b7-182">不過，Windows PowerShell 主控台設定檔中的專案無法在 Windows PowerShell ISE 中使用。</span><span class="sxs-lookup"><span data-stu-id="779b7-182">However, the items in your Windows PowerShell console profiles are not available in Windows PowerShell ISE.</span></span>

<span data-ttu-id="779b7-183">您可以在 Windows PowerShell ISE 說明和 about_Profiles 中取得移動和重新設定設定檔的指示。</span><span class="sxs-lookup"><span data-stu-id="779b7-183">Instructions for moving and reconfiguring your profiles are available in Windows PowerShell ISE Help and in about_Profiles.</span></span>

## <a name="notes"></a><span data-ttu-id="779b7-184">注意</span><span class="sxs-lookup"><span data-stu-id="779b7-184">NOTES</span></span>

<span data-ttu-id="779b7-185">Windows PowerShell ISE 是選用的 Windows 功能，預設會在用戶端和伺服器版本的 Windows 上開啟。</span><span class="sxs-lookup"><span data-stu-id="779b7-185">Windows PowerShell ISE is an optional Windows Feature that is turned on by default on client and server versions of Windows.</span></span> <span data-ttu-id="779b7-186">若要在用戶端版本的 Windows 中啟用和停用 Windows PowerShell ISE，請使用主控台中的 [開啟或關閉 Windows 功能]。</span><span class="sxs-lookup"><span data-stu-id="779b7-186">To enable and disable Windows PowerShell ISE in client versions of Windows, use Turn Windows Features On or Off in Control Panel.</span></span> <span data-ttu-id="779b7-187">若要在伺服器版本的 Windows 中啟用和停用 Windows PowerShell ISE，請使用伺服器管理員中的 [新增角色及功能]。</span><span class="sxs-lookup"><span data-stu-id="779b7-187">To enable and disable Windows PowerShell ISE in server versions of Windows, use the Add Roles and Features Wizard in Server Manager.</span></span>

<span data-ttu-id="779b7-188">由於 Windows PowerShell ISE 需要使用者介面，因此無法在 Windows Server 的 Server Core 安裝上運作。</span><span class="sxs-lookup"><span data-stu-id="779b7-188">Because Windows PowerShell ISE requires a user interface, it does not work on Server Core installations of Windows Server.</span></span> <span data-ttu-id="779b7-189">但是，如果您新增 Windows PowerShell ISE 功能，安裝會自動以 GUI 轉換成伺服器。</span><span class="sxs-lookup"><span data-stu-id="779b7-189">However, if you add the Windows PowerShell ISE feature, the installation automatically converts to Server with a GUI.</span></span>

<span data-ttu-id="779b7-190">Windows PowerShell ISE 建置於 Windows Presentation Foundation (WPF) 上。</span><span class="sxs-lookup"><span data-stu-id="779b7-190">Windows PowerShell ISE is built on the Windows Presentation Foundation (WPF).</span></span>
<span data-ttu-id="779b7-191">如果 Windows PowerShell ISE 的圖形化元素無法在您的系統上正確轉譯，您可以在系統上新增或調整「停用 WPF 硬體加速」圖形轉譯設定，以解決此問題。</span><span class="sxs-lookup"><span data-stu-id="779b7-191">If the graphical elements of Windows PowerShell ISE do not render correctly on your system, you might resolve the problem by adding or adjusting the "Disable WPF Hardware acceleration" graphics rendering settings on your system.</span></span> <span data-ttu-id="779b7-192">如需詳細資訊，請參閱[圖形轉譯登錄設定](/dotnet/framework/wpf/graphics-multimedia/graphics-rendering-registry-settings)。</span><span class="sxs-lookup"><span data-stu-id="779b7-192">For more information, see [Graphics Rendering Registry Settings](/dotnet/framework/wpf/graphics-multimedia/graphics-rendering-registry-settings).</span></span>

## <a name="see-also"></a><span data-ttu-id="779b7-193">另請參閱</span><span class="sxs-lookup"><span data-stu-id="779b7-193">SEE ALSO</span></span>

[<span data-ttu-id="779b7-194">about_Debuggers</span><span class="sxs-lookup"><span data-stu-id="779b7-194">about_Debuggers</span></span>](about_Debuggers.md)

[<span data-ttu-id="779b7-195">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="779b7-195">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="779b7-196">about_Updatable_Help</span><span class="sxs-lookup"><span data-stu-id="779b7-196">about_Updatable_Help</span></span>](about_Updatable_Help.md)

[<span data-ttu-id="779b7-197">Get-Help</span><span class="sxs-lookup"><span data-stu-id="779b7-197">Get-Help</span></span>](xref:Microsoft.PowerShell.Core.Get-Help)

[<span data-ttu-id="779b7-198">Get-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="779b7-198">Get-IseSnippet</span></span>](xref:ISE.Get-IseSnippet)

[<span data-ttu-id="779b7-199">Import-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="779b7-199">Import-IseSnippet</span></span>](xref:ISE.Import-IseSnippet)

[<span data-ttu-id="779b7-200">New-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="779b7-200">New-IseSnippet</span></span>](xref:ISE.New-IseSnippet)

[<span data-ttu-id="779b7-201">Save-Help</span><span class="sxs-lookup"><span data-stu-id="779b7-201">Save-Help</span></span>](xref:Microsoft.PowerShell.Core.Save-Help)

[<span data-ttu-id="779b7-202">Show-Command</span><span class="sxs-lookup"><span data-stu-id="779b7-202">Show-Command</span></span>](xref:Microsoft.PowerShell.Utility.Show-Command)

[<span data-ttu-id="779b7-203">Update-Help</span><span class="sxs-lookup"><span data-stu-id="779b7-203">Update-Help</span></span>](xref:Microsoft.PowerShell.Core.Update-Help)
