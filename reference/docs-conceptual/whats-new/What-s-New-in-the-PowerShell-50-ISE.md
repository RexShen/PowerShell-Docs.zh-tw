---
ms.date: 09/06/2019
keywords: powershell,cmdlet
title: PowerShell 5.0 ISE 的新功能
ms.openlocfilehash: 8f15e99c5a6ae33aeae9bd33eb0cf58fb27e3b90
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416641"
---
# <a name="whats-new-in-the-windows-powershell-50-ise"></a><span data-ttu-id="9eef7-103">Windows PowerShell 5.0 ISE 的新功能</span><span class="sxs-lookup"><span data-stu-id="9eef7-103">What's New in the Windows PowerShell 5.0 ISE</span></span>

<span data-ttu-id="9eef7-104">本主題說明先前在 Windows PowerShell 整合式指令碼環境 (ISE) 5.0 版中推出的新功能及更新功能。</span><span class="sxs-lookup"><span data-stu-id="9eef7-104">This topic explains the new and updated features that have been introduced in version 5.0 of the Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

> [!NOTE]
> <span data-ttu-id="9eef7-105">我們將不再為 PowerShell ISE 開發新功能。</span><span class="sxs-lookup"><span data-stu-id="9eef7-105">The PowerShell ISE is no longer in active feature development.</span></span> <span data-ttu-id="9eef7-106">因為此功能屬於 Windows 的出貨元件，所以官方仍會繼續支援其安全性與高優先順序的服務修正。</span><span class="sxs-lookup"><span data-stu-id="9eef7-106">As a shipping component of Windows, it continues to be officially supported for security and high-priority servicing fixes.</span></span>
> <span data-ttu-id="9eef7-107">目前尚無任何計劃要將 ISE 從 Windows 移除。</span><span class="sxs-lookup"><span data-stu-id="9eef7-107">We currently have no plans to remove the ISE from Windows.</span></span>
>
> <span data-ttu-id="9eef7-108">PowerShell v6 及更新版本不支援 ISE。</span><span class="sxs-lookup"><span data-stu-id="9eef7-108">There is no support for the ISE in PowerShell v6 and beyond.</span></span> <span data-ttu-id="9eef7-109">使用者如有需要 ISE 的替代解決方案，可使用 [Visual Studio Code](https://code.visualstudio.com/) 搭配 [PowerShell 延伸模組](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell)。</span><span class="sxs-lookup"><span data-stu-id="9eef7-109">Users looking for replacement for the ISE should use [Visual Studio Code](https://code.visualstudio.com/) with the [PowerShell Extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell).</span></span>

## <a name="feature-description"></a><span data-ttu-id="9eef7-110">功能說明</span><span class="sxs-lookup"><span data-stu-id="9eef7-110">Feature description</span></span>

<span data-ttu-id="9eef7-111">Windows PowerShell ISE 是一個主應用程式，可以讓您在圖形化與直覺式的環境中撰寫、執行及測試指令碼和模組。</span><span class="sxs-lookup"><span data-stu-id="9eef7-111">The Windows PowerShell ISE is a host application that enables you to write, run, and test scripts and modules in a graphical and intuitive environment.</span></span> <span data-ttu-id="9eef7-112">語法標色、TAB 鍵自動完成、視覺化偵錯、Unicode 相容性、即時線上說明等主要功能，提供豐富的指令碼撰寫體驗。</span><span class="sxs-lookup"><span data-stu-id="9eef7-112">Key features such as syntax-coloring, tab completion, visual debugging, Unicode compliance, and context-sensitive Help provide a rich scripting experience.</span></span>

<span data-ttu-id="9eef7-113">如需詳細資訊，請參閱 [Windows PowerShell ISE 簡介](../components/ise/Introducing-the-Windows-PowerShell-ISE.md)。</span><span class="sxs-lookup"><span data-stu-id="9eef7-113">For more information, see [Introducing the Windows PowerShell ISE](../components/ise/Introducing-the-Windows-PowerShell-ISE.md).</span></span>

<span data-ttu-id="9eef7-114">下表列出 Windows PowerShell 中這版 Windows PowerShell ISE 的新功能和變更功能。</span><span class="sxs-lookup"><span data-stu-id="9eef7-114">The following table lists the new and changed features for this release of Windows PowerShell ISE in Windows PowerShell.</span></span>

## <a name="intellisense"></a><span data-ttu-id="9eef7-115">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="9eef7-115">IntelliSense</span></span>

> <span data-ttu-id="9eef7-116">ISE 3.0 的新功能</span><span class="sxs-lookup"><span data-stu-id="9eef7-116">Added in ISE 3.0</span></span>

<span data-ttu-id="9eef7-117">IntelliSense 是屬於 Windows PowerShell ISE 的自動完成協助功能。</span><span class="sxs-lookup"><span data-stu-id="9eef7-117">IntelliSense is an automatic-completion assistance feature that is part of Windows PowerShell ISE.</span></span>
<span data-ttu-id="9eef7-118">在您輸入文字時，IntelliSense 會顯示與輸入文字可能相符的 Cmdlet、參數、參數值、檔案或資料夾的可點選功能表。</span><span class="sxs-lookup"><span data-stu-id="9eef7-118">IntelliSense displays clickable menus of potentially matching cmdlets, parameters, parameter values, files, or folders as you type.</span></span>

<span data-ttu-id="9eef7-119">**這項變更增加了什麼價值？**</span><span class="sxs-lookup"><span data-stu-id="9eef7-119">**What value does this change add?**</span></span>

<span data-ttu-id="9eef7-120">透過 IntelliSense，您可以在使用 Windows PowerShell ISE 建立指令碼時更輕鬆地探索 Cmdlet 和語法。</span><span class="sxs-lookup"><span data-stu-id="9eef7-120">With the addition of IntelliSense, it's easier to discover cmdlets and syntax when you use Windows PowerShell ISE to create scripts.</span></span> <span data-ttu-id="9eef7-121">您也可以在建立新指令碼時透過 Windows PowerShell ISE 學習 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="9eef7-121">You can also use Windows PowerShell ISE to learn Windows PowerShell while you create new scripts.</span></span>

<span data-ttu-id="9eef7-122">**有哪些不同？**</span><span class="sxs-lookup"><span data-stu-id="9eef7-122">**What works differently?**</span></span>

<span data-ttu-id="9eef7-123">在 Windows PowerShell ISE 中輸入 Cmdlet 時，會顯示可捲動和可點選的功能表，可讓您瀏覽和選取適當的命令。</span><span class="sxs-lookup"><span data-stu-id="9eef7-123">When you type cmdlets in the Windows PowerShell ISE, a scrollable and clickable menu displays, allowing you to browse and select the appropriate commands.</span></span>

## <a name="snippets"></a><span data-ttu-id="9eef7-124">程式碼片段</span><span class="sxs-lookup"><span data-stu-id="9eef7-124">Snippets</span></span>

> <span data-ttu-id="9eef7-125">ISE 3.0 的新功能</span><span class="sxs-lookup"><span data-stu-id="9eef7-125">Added in ISE 3.0</span></span>

<span data-ttu-id="9eef7-126">*程式碼片段*是可以插入您在 Windows PowerShell ISE 中所建立之指令碼的簡短 Windows PowerShell 程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="9eef7-126">*Snippets* are short sections of Windows PowerShell code that you can insert into the scripts you create in Windows PowerShell ISE.</span></span> <span data-ttu-id="9eef7-127">Windows PowerShell ISE 隨附一組預設程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="9eef7-127">Windows PowerShell ISE comes with a default set of snippets.</span></span> <span data-ttu-id="9eef7-128">在 Windows PowerShell ISE 中工作時，您可以使用 `New-Snippet` Cmdlet 來新增程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="9eef7-128">You can add snippets by using the `New-Snippet` cmdlet while working in Windows PowerShell ISE.</span></span>

<span data-ttu-id="9eef7-129">**這項變更增加了什麼價值？**</span><span class="sxs-lookup"><span data-stu-id="9eef7-129">**What value does this change add?**</span></span>

<span data-ttu-id="9eef7-130">使用程式碼片段，您可以快速地組合並建立指令碼，以自動化您的環境。</span><span class="sxs-lookup"><span data-stu-id="9eef7-130">By using snippets, you can quickly assemble and create scripts to automate your environment.</span></span>

<span data-ttu-id="9eef7-131">**有哪些不同？**</span><span class="sxs-lookup"><span data-stu-id="9eef7-131">**What works differently?**</span></span>

<span data-ttu-id="9eef7-132">若要在 Windows PowerShell 3.0 或更新版本中使用程式碼片段，請按一下 [編輯]  功能表上的 [開始程式碼片段]  ，或按 <kbd>Ctrl</kbd>+<kbd>J</kbd>。</span><span class="sxs-lookup"><span data-stu-id="9eef7-132">To use snippets in Windows PowerShell 3.0 or later, on the **Edit** menu, click **Start Snippets**, or press <kbd>Ctrl</kbd>+<kbd>J</kbd>.</span></span>

## <a name="add-on-tools"></a><span data-ttu-id="9eef7-133">附加元件工具</span><span class="sxs-lookup"><span data-stu-id="9eef7-133">Add-on tools</span></span>

> <span data-ttu-id="9eef7-134">PowerShell 3.0 的新功能</span><span class="sxs-lookup"><span data-stu-id="9eef7-134">Added in PowerShell 3.0</span></span>

<span data-ttu-id="9eef7-135">Windows PowerShell ISE 現在支援使用物件模型的附加元件工具。</span><span class="sxs-lookup"><span data-stu-id="9eef7-135">Windows PowerShell ISE now supports add-on tools using the object model.</span></span> <span data-ttu-id="9eef7-136">這些附加元件是在主控台中顯示為垂直或水準窗格的 Windows Presentation Foundation (WPF) 控制項。</span><span class="sxs-lookup"><span data-stu-id="9eef7-136">These add-ons are Windows Presentation Foundation (WPF) controls that are displayed as a vertical or horizontal pane in the console.</span></span> <span data-ttu-id="9eef7-137">窗格中的多個附加元件工具會顯示成一個索引標籤式控制項。</span><span class="sxs-lookup"><span data-stu-id="9eef7-137">Multiple add-on tools in a pane are displayed as a tabbed control.</span></span> <span data-ttu-id="9eef7-138">您也可以新增或移除非 Microsoft 合作廠商製作的附加元件工具。</span><span class="sxs-lookup"><span data-stu-id="9eef7-138">You can also add or remove add-on tools that are produced by non-Microsoft parties.</span></span> <span data-ttu-id="9eef7-139">如需詳細資訊，請參閱 [Windows PowerShell ISE 指令碼物件模型的用途](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)。</span><span class="sxs-lookup"><span data-stu-id="9eef7-139">For more information, see [The Purpose of the Windows PowerShell ISE Scripting Object Model](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md).</span></span>

<span data-ttu-id="9eef7-140">**這項變更增加了什麼價值？**</span><span class="sxs-lookup"><span data-stu-id="9eef7-140">**What value does this change add?**</span></span>

<span data-ttu-id="9eef7-141">附加元件可讓您使用可新增功能及可增強指令碼體驗的工具來擴充和自訂 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="9eef7-141">Add-ons allow you to extend and customize Windows PowerShell ISE with tools that add functionality and enhance your scripting experience.</span></span>

<span data-ttu-id="9eef7-142">**有哪些不同？**</span><span class="sxs-lookup"><span data-stu-id="9eef7-142">**What works differently?**</span></span>

<span data-ttu-id="9eef7-143">Windows PowerShell ISE 3.0 和更新版本隨附 **Commands** 附加元件。</span><span class="sxs-lookup"><span data-stu-id="9eef7-143">Windows PowerShell ISE 3.0 and later come with the **Commands** add-on.</span></span> <span data-ttu-id="9eef7-144">**Commands** 附加元件可讓您瀏覽 Cmdlet，以及使用 指令碼  和 主控台  窗格並列存取 Cmdlet 的說明。</span><span class="sxs-lookup"><span data-stu-id="9eef7-144">The **Commands** add-on allows you to browse cmdlets, and access help about the cmdlets side-by-side with the **Script** and **Console** Panes.</span></span>

<span data-ttu-id="9eef7-145">使用 [附加元件]  功能表上的 [開啟附加元件工具網站]  命令，可以找到額外的附加元件。</span><span class="sxs-lookup"><span data-stu-id="9eef7-145">Additional add-ons can be found by using the **Open Add-on Tools Website** command on the **Add-ons** menu.</span></span>

## <a name="restart-manager-and-auto-save"></a><span data-ttu-id="9eef7-146">重新啟動管理員和自動儲存</span><span class="sxs-lookup"><span data-stu-id="9eef7-146">Restart manager and auto-save</span></span>

> <span data-ttu-id="9eef7-147">PowerShell 3.0 的新功能</span><span class="sxs-lookup"><span data-stu-id="9eef7-147">Added in PowerShell 3.0</span></span>

<span data-ttu-id="9eef7-148">Windows PowerShell ISE 現在每兩分鐘會自動在不同的位置儲存您未完成的指令碼。</span><span class="sxs-lookup"><span data-stu-id="9eef7-148">Windows PowerShell ISE now automatically saves your open scripts every two minutes, in a separate location.</span></span> <span data-ttu-id="9eef7-149">當 Windows PowerShell ISE 在非預期的當機或重新啟動之後重新開機時，會復原已在上一個工作階段中開啟的指令碼，即使指令碼並未儲存也一樣。</span><span class="sxs-lookup"><span data-stu-id="9eef7-149">When Windows PowerShell ISE restarts after an unexpected crash or reboot, it recovers scripts that were open in the last session, even if the scripts weren't saved.</span></span>

<span data-ttu-id="9eef7-150">若要變更自動儲存間隔，請在主控台窗格中執行下列命令：`$psise.Options.AutoSaveMinuteInterval`。</span><span class="sxs-lookup"><span data-stu-id="9eef7-150">To change the automatic saving interval, run the following command in the Console pane: `$psise.Options.AutoSaveMinuteInterval`.</span></span>

<span data-ttu-id="9eef7-151">**這項變更增加了什麼價值？**</span><span class="sxs-lookup"><span data-stu-id="9eef7-151">**What value does this change add?**</span></span>

<span data-ttu-id="9eef7-152">由於已開啟的指令碼會自動儲存，您將能安心地在 Windows PowerShell ISE 內工作。</span><span class="sxs-lookup"><span data-stu-id="9eef7-152">You can now work within Windows PowerShell ISE knowing that your open scripts are automatically saved.</span></span>

<span data-ttu-id="9eef7-153">**有哪些不同？**</span><span class="sxs-lookup"><span data-stu-id="9eef7-153">**What works differently?**</span></span>

<span data-ttu-id="9eef7-154">Windows PowerShell ISE 2.0 不會自動儲存指令碼。</span><span class="sxs-lookup"><span data-stu-id="9eef7-154">Windows PowerShell ISE 2.0 doesn't save the scripts automatically.</span></span>

## <a name="most-recently-used-list"></a><span data-ttu-id="9eef7-155">最近使用的清單</span><span class="sxs-lookup"><span data-stu-id="9eef7-155">Most-recently used list</span></span>

> <span data-ttu-id="9eef7-156">PowerShell 3.0 的新功能</span><span class="sxs-lookup"><span data-stu-id="9eef7-156">Added in PowerShell 3.0</span></span>

<span data-ttu-id="9eef7-157">Windows PowerShell ISE 現在具有最近使用之檔案的清單。</span><span class="sxs-lookup"><span data-stu-id="9eef7-157">Windows PowerShell ISE now has a most-recently used list for files.</span></span> <span data-ttu-id="9eef7-158">當您在 Windows PowerShell ISE 中開啟檔案時，該檔案會被新增至 [檔案]  功能表上的 [最近使用的清單]。</span><span class="sxs-lookup"><span data-stu-id="9eef7-158">When you open a file in Windows PowerShell ISE, the file is added to the most-recently used list on the **File** menu.</span></span>

<span data-ttu-id="9eef7-159">若要變更最近使用清單中預設數目的檔案，請在主控台窗格中執行下列命令：`$psise.Options.MruCount`。</span><span class="sxs-lookup"><span data-stu-id="9eef7-159">To change the default number of files in the most-recently used list, run the following command in the Console Pane: `$psise.Options.MruCount`.</span></span>

<span data-ttu-id="9eef7-160">**這項變更增加了什麼價值？**</span><span class="sxs-lookup"><span data-stu-id="9eef7-160">**What value does this change add?**</span></span>

<span data-ttu-id="9eef7-161">您現在可以使用最近使用的清單來輕鬆地存取常用檔案。</span><span class="sxs-lookup"><span data-stu-id="9eef7-161">You can now use the most-recently used list to easily access your frequently used files.</span></span>

<span data-ttu-id="9eef7-162">**有哪些不同？**</span><span class="sxs-lookup"><span data-stu-id="9eef7-162">**What works differently?**</span></span>

<span data-ttu-id="9eef7-163">Windows PowerShell ISE 2.0 並不具有最近使用的清單。</span><span class="sxs-lookup"><span data-stu-id="9eef7-163">Windows PowerShell ISE 2.0 doesn't have a most-recently used list.</span></span>

## <a name="console-pane"></a><span data-ttu-id="9eef7-164">主控台窗格</span><span class="sxs-lookup"><span data-stu-id="9eef7-164">Console Pane</span></span>

> <span data-ttu-id="9eef7-165">PowerShell 3.0 的新功能</span><span class="sxs-lookup"><span data-stu-id="9eef7-165">Added in PowerShell 3.0</span></span>

<span data-ttu-id="9eef7-166">第一版 Windows PowerShell ISE 中獨立的命令與輸出窗格已結合成單一主控台窗格。</span><span class="sxs-lookup"><span data-stu-id="9eef7-166">The separate Command and Output Panes that were available in the first release of Windows PowerShell ISE have been combined into a single Console Pane.</span></span> <span data-ttu-id="9eef7-167">這個主控台窗格在功能與外觀上與典型的 Windows PowerShell 主控台類似，但包含下列增強功能：</span><span class="sxs-lookup"><span data-stu-id="9eef7-167">The Console Pane is similar in function and appearance to a typical Windows PowerShell console, but it includes the following enhancements:</span></span>

- <span data-ttu-id="9eef7-168">輸入文字 (非輸出文字) 的語法著色 (包括 XML 語法)</span><span class="sxs-lookup"><span data-stu-id="9eef7-168">Syntax coloring for input text (not output text), including XML syntax</span></span>
- <span data-ttu-id="9eef7-169">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="9eef7-169">IntelliSense</span></span>
- <span data-ttu-id="9eef7-170">括號對稱</span><span class="sxs-lookup"><span data-stu-id="9eef7-170">Brace matching</span></span>
- <span data-ttu-id="9eef7-171">錯誤指示</span><span class="sxs-lookup"><span data-stu-id="9eef7-171">Error indication</span></span>
- <span data-ttu-id="9eef7-172">完整 Unicode 支援</span><span class="sxs-lookup"><span data-stu-id="9eef7-172">Full Unicode support</span></span>
- <span data-ttu-id="9eef7-173"><kbd>F1</kbd> 即時線上說明</span><span class="sxs-lookup"><span data-stu-id="9eef7-173"><kbd>F1</kbd> context-sensitive help</span></span>
- <span data-ttu-id="9eef7-174"><kbd>Ctrl</kbd>+<kbd>F1</kbd> 即時線上顯示命令 (Show-Command)</span><span class="sxs-lookup"><span data-stu-id="9eef7-174"><kbd>Ctrl</kbd>+<kbd>F1</kbd> context-sensitive Show-Command</span></span>
- <span data-ttu-id="9eef7-175">複雜指令碼與由右至左語言支援</span><span class="sxs-lookup"><span data-stu-id="9eef7-175">Complex script and right-to-left support</span></span>
- <span data-ttu-id="9eef7-176">字型支援</span><span class="sxs-lookup"><span data-stu-id="9eef7-176">Font support</span></span>
- <span data-ttu-id="9eef7-177">縮放</span><span class="sxs-lookup"><span data-stu-id="9eef7-177">Zoom</span></span>
- <span data-ttu-id="9eef7-178">行選取與區塊選取模式</span><span class="sxs-lookup"><span data-stu-id="9eef7-178">Line-select and block-select modes</span></span>
- <span data-ttu-id="9eef7-179">按 <kbd>UpArrow</kbd> 以在主控台中檢視歷程記錄時，保留命令列中輸入的內容</span><span class="sxs-lookup"><span data-stu-id="9eef7-179">Preservation of typed content at the command line when you press the <kbd>UpArrow</kbd> to view history in the console</span></span>

<span data-ttu-id="9eef7-180">**這項變更增加了什麼價值？**</span><span class="sxs-lookup"><span data-stu-id="9eef7-180">**What value does this change add?**</span></span>

<span data-ttu-id="9eef7-181">新增這些主控台窗格變更可提供主控台介面更一致的指令碼體驗。</span><span class="sxs-lookup"><span data-stu-id="9eef7-181">The addition of these Console Pane changes provides a scripting experience that is more consistent with the console interface.</span></span>

<span data-ttu-id="9eef7-182">**有哪些不同？**</span><span class="sxs-lookup"><span data-stu-id="9eef7-182">**What works differently?**</span></span>

<span data-ttu-id="9eef7-183">Windows PowerShell ISE 2.0 具有個別的命令和輸出窗格。</span><span class="sxs-lookup"><span data-stu-id="9eef7-183">Windows PowerShell ISE 2.0 has separate Command and Output Panes.</span></span>

## <a name="command-line-switches"></a><span data-ttu-id="9eef7-184">命令列參數</span><span class="sxs-lookup"><span data-stu-id="9eef7-184">Command-line switches</span></span>

> <span data-ttu-id="9eef7-185">PowerShell 3.0 的新功能</span><span class="sxs-lookup"><span data-stu-id="9eef7-185">Added in PowerShell 3.0</span></span>

<span data-ttu-id="9eef7-186">如果透過命令列啟動 Windows PowerShell ISE (輸入 **Powershell_ise.exe**)，您可以新增下列新的命令列參數。</span><span class="sxs-lookup"><span data-stu-id="9eef7-186">If you start Windows PowerShell ISE from the command line (by typing **powershell_ise.exe**), you can add the following new command-line switches.</span></span>

- <span data-ttu-id="9eef7-187">`-NoProfile`:在沒有執行 `$profile` 的情況下啟動 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="9eef7-187">`-NoProfile`: Starts Windows PowerShell ISE without running `$profile`</span></span>
- <span data-ttu-id="9eef7-188">`-Help`:顯示 [說明] 視窗</span><span class="sxs-lookup"><span data-stu-id="9eef7-188">`-Help`: Displays a Help window</span></span>
- <span data-ttu-id="9eef7-189">`-mta`:以多執行緒 Apartment 模式啟動 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="9eef7-189">`-mta`: Starts Windows PowerShell ISE in multithreaded apartment mode.</span></span> <span data-ttu-id="9eef7-190">Windows PowerShell ISE 的預設作業模式是單一執行緒 Apartment 模式，或 `-sta`。</span><span class="sxs-lookup"><span data-stu-id="9eef7-190">The default operation mode for Windows PowerShell ISE is single-threaded apartment mode, or `-sta`.</span></span>

<span data-ttu-id="9eef7-191">**這項變更增加了什麼價值？**</span><span class="sxs-lookup"><span data-stu-id="9eef7-191">**What value does this change add?**</span></span>

<span data-ttu-id="9eef7-192">新增這些命令列參數可讓您控制 Windows PowerShell ISE 的執行環境。</span><span class="sxs-lookup"><span data-stu-id="9eef7-192">The addition of these command-line switches allows you to control the environment in which the Windows PowerShell ISE runs.</span></span>

<span data-ttu-id="9eef7-193">**有哪些不同？**</span><span class="sxs-lookup"><span data-stu-id="9eef7-193">**What works differently?**</span></span>

<span data-ttu-id="9eef7-194">Windows PowerShell ISE 2.0 無法辨識這些命令列參數。</span><span class="sxs-lookup"><span data-stu-id="9eef7-194">Windows PowerShell ISE 2.0 doesn't recognize these command-line switches.</span></span>

## <a name="new-editor-features"></a><span data-ttu-id="9eef7-195">新編輯器功能</span><span class="sxs-lookup"><span data-stu-id="9eef7-195">New editor features</span></span>

> <span data-ttu-id="9eef7-196">PowerShell 3.0 的新功能</span><span class="sxs-lookup"><span data-stu-id="9eef7-196">Added in PowerShell 3.0</span></span>

<span data-ttu-id="9eef7-197">Windows PowerShell ISE 其他的編輯功能包括：</span><span class="sxs-lookup"><span data-stu-id="9eef7-197">Other Windows PowerShell ISE editing features include:</span></span>

- <span data-ttu-id="9eef7-198">**XML 語法著色** - Windows PowerShell ISE 現在會以對 Windows PowerShell 語法進行著色的相同方法，對 XML 語法進行著色。</span><span class="sxs-lookup"><span data-stu-id="9eef7-198">**XML syntax coloring** - Windows PowerShell ISE now colors XML syntax in the same way as it colors Windows PowerShell syntax.</span></span>
- <span data-ttu-id="9eef7-199">**括號對稱** - Windows PowerShell ISE 包括括號對稱和醒目顯示，且可以透過下列方式使用：(例如，如果已選取左大括號，則使用 [移至相符項目]  命令或 <kbd>[Ctrl</kbd>+<kbd>]</kbd> 便能找到右大括號)。</span><span class="sxs-lookup"><span data-stu-id="9eef7-199">**Brace matching** - Windows PowerShell ISE includes brace matching and highlighting, and can be used in the following ways: (for example, using the **Go to Match** command or <kbd>Ctrl</kbd>+<kbd>]</kbd> locates the closing brace, if you have an opening brace selected).</span></span>
- <span data-ttu-id="9eef7-200">**大綱檢視** 指令碼窗格支援大綱功能，按一下左邊界的加號或減號，即允許摺疊或展開程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="9eef7-200">**Outline view** The Script Pane supports outlining, which allows collapsing or expanding sections of code by clicking plus or minus signs in the left margin.</span></span> <span data-ttu-id="9eef7-201">您可以使用大括號或 `#region` 和 `#endregion` 標籤來標示可摺疊區段的開頭或結尾。</span><span class="sxs-lookup"><span data-stu-id="9eef7-201">You can use braces or the `#region` and `#endregion` tags to mark the beginning or end of a collapsible section.</span></span> <span data-ttu-id="9eef7-202">若要展開或摺疊所有區域，請按 <kbd>Ctrl</kbd>+<kbd>M</kbd>。</span><span class="sxs-lookup"><span data-stu-id="9eef7-202">To expand or collapse all regions, press <kbd>Ctrl</kbd>+<kbd>M</kbd>.</span></span>
- <span data-ttu-id="9eef7-203">**拖放文字編輯** - Windows PowerShell ISE 現在支援拖放文字編輯。</span><span class="sxs-lookup"><span data-stu-id="9eef7-203">**Drag and drop text editing** - Windows PowerShell ISE now supports drag and drop text editing.</span></span> <span data-ttu-id="9eef7-204">您可以選取任何文字區塊，並將該文字拖曳到編輯器或主控台中的其他位置來移動文字。</span><span class="sxs-lookup"><span data-stu-id="9eef7-204">You can select any block of text and drag that text to another location in the editor or the console to move the text.</span></span> <span data-ttu-id="9eef7-205">如果您在拖曳選取的文字時按住 <kbd>Ctrl</kbd> 鍵，則放開滑鼠按鈕時，會將文字複製到新位置。</span><span class="sxs-lookup"><span data-stu-id="9eef7-205">If you hold down the <kbd>Ctrl</kbd> key while you drag the selected text, when you release the mouse button the text is copied to the new location.</span></span> <span data-ttu-id="9eef7-206">在此版本的 Windows PowerShell ISE 中，當您將檔案拖放到 Windows PowerShell ISE 上時，Windows PowerShell ISE 便會開啟該檔案。</span><span class="sxs-lookup"><span data-stu-id="9eef7-206">In this version of Windows PowerShell ISE, when you drag and drop files onto Windows PowerShell ISE, Windows PowerShell ISE opens the file.</span></span>
- <span data-ttu-id="9eef7-207">**剖析錯誤顯示** - 剖析錯誤會以紅色底線表示。</span><span class="sxs-lookup"><span data-stu-id="9eef7-207">**Parse error display** - Parse errors are indicated with red underlines.</span></span> <span data-ttu-id="9eef7-208">暫留於指示的錯誤時，工具提示文字會顯示在程式碼中發現的問題。</span><span class="sxs-lookup"><span data-stu-id="9eef7-208">When you hover over an indicated error, tooltip text displays the problem that was found in the code.</span></span>
- <span data-ttu-id="9eef7-209">**縮放** - 您可以使用縮放滑桿 (在 Windows PowerShell ISE 視窗的右下角) 或在主控台窗格中輸入 `$psise.options.Zoom` 命令，來設定主控台內容的縮放百分比。</span><span class="sxs-lookup"><span data-stu-id="9eef7-209">**Zoom** - The zoom percentage of the console's content can be set by using the zoom slider (in the lower right corner of Windows PowerShell ISE window), or by entering the command `$psise.options.Zoom` in the Console Pane.</span></span>
- <span data-ttu-id="9eef7-210">**RTF 複製與貼上** - 複製到 Windows PowerShell ISE 中的剪貼簿將會保留原始選取項目的字型、大小及色彩資訊。</span><span class="sxs-lookup"><span data-stu-id="9eef7-210">**Rich text copy and paste** - Copying to the clipboard in Windows PowerShell ISE preserves the font, size, and color information of the original selection.</span></span>
- <span data-ttu-id="9eef7-211">**區塊選取** - 在使用滑鼠選取指令碼窗格中的文字時按住 <kbd>ALT</kbd> 鍵或按 <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>方向鍵</kbd>，就可以選取一個區塊的文字。</span><span class="sxs-lookup"><span data-stu-id="9eef7-211">**Block selection** - You can select a block of text by holding down the <kbd>ALT</kbd> key while selecting text in the Script Pane with your mouse, or by pressing <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>Arrow</kbd>.</span></span>

<span data-ttu-id="9eef7-212">**這項變更增加了什麼價值？**</span><span class="sxs-lookup"><span data-stu-id="9eef7-212">**What value does this change add?**</span></span>

<span data-ttu-id="9eef7-213">其他編輯功能提供更一致且功能強大的編輯環境。</span><span class="sxs-lookup"><span data-stu-id="9eef7-213">The additional editing features provide a more consistent and powerful editing environment.</span></span>

<span data-ttu-id="9eef7-214">**有哪些不同？**</span><span class="sxs-lookup"><span data-stu-id="9eef7-214">**What works differently?**</span></span>

<span data-ttu-id="9eef7-215">Windows PowerShell ISE 2.0 沒有這些編輯增強功能。</span><span class="sxs-lookup"><span data-stu-id="9eef7-215">These editing enhancements weren't present in Windows PowerShell ISE 2.0.</span></span>

## <a name="new-help-viewer-window"></a><span data-ttu-id="9eef7-216">新的說明檢視器視窗</span><span class="sxs-lookup"><span data-stu-id="9eef7-216">New Help viewer window</span></span>

> <span data-ttu-id="9eef7-217">PowerShell 3.0 的新功能</span><span class="sxs-lookup"><span data-stu-id="9eef7-217">Added in PowerShell 3.0</span></span>

<span data-ttu-id="9eef7-218">當您的游標在 Cmdlet 中或當您反白顯示 Cmdlet 的一部分時，如果按 <kbd>F1</kbd>，新的說明檢視器就會開啟有關反白顯示 Cmdlet 的即時線上說明。</span><span class="sxs-lookup"><span data-stu-id="9eef7-218">If you press <kbd>F1</kbd> when your cursor is in a cmdlet, or you have part of a cmdlet highlighted, the new Help viewer opens context-sensitive Help about the highlighted cmdlet.</span></span> <span data-ttu-id="9eef7-219">若要顯示「關於 Windows PowerShell」  說明，請在主控台窗格中輸入 `operators`，然後按 <kbd>F1</kbd>。</span><span class="sxs-lookup"><span data-stu-id="9eef7-219">To display Windows PowerShell **About** help, type `operators` in the console pane, and then press <kbd>F1</kbd>.</span></span>

<span data-ttu-id="9eef7-220">使用這項功能之前，請先從 Microsoft 網站下載最新版本的 Windows PowerShell 說明主題。</span><span class="sxs-lookup"><span data-stu-id="9eef7-220">Before you use this feature, download the most current version of Windows PowerShell Help topics from the Microsoft website.</span></span> <span data-ttu-id="9eef7-221">下載說明主題的最簡單方法是以系統管理員身分執行 Windows PowerShell ISE，並於主控台窗格中執行 `Update-Help` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9eef7-221">The simplest method for downloading the Help topics is to run the `Update-Help` cmdlet in the Console Pane when running Windows PowerShell ISE as administrator.</span></span>

<span data-ttu-id="9eef7-222">您可以變更 <kbd>F1</kbd> 鍵尋找說明的位置。</span><span class="sxs-lookup"><span data-stu-id="9eef7-222">You can alter where the <kbd>F1</kbd> key looks for Help.</span></span> <span data-ttu-id="9eef7-223">您在 [工具]  /[選項]  功能表中，於 [一般設定]  索引標籤的 [其他設定]  下，可以設定或清除 [使用本機說明內容而非線上內容]  核取方塊。</span><span class="sxs-lookup"><span data-stu-id="9eef7-223">In the **Tools**/**Options** menu, on the **General Settings** tab, under **Other Settings**, you can set or clear the checkbox **Use local help content instead of online content**.</span></span> <span data-ttu-id="9eef7-224">選取時，用戶端會在模組資料夾中發現的已下載說明中尋找 Cmdlet 說明。</span><span class="sxs-lookup"><span data-stu-id="9eef7-224">When checked, the client looks for the cmdlet Help in the downloaded Help found in the modules folder.</span></span> <span data-ttu-id="9eef7-225">如果清除此核取方塊，用戶端就會在線上尋找說明。</span><span class="sxs-lookup"><span data-stu-id="9eef7-225">If the checkbox is cleared, the client looks for help online.</span></span>

<span data-ttu-id="9eef7-226">**這項變更增加了什麼價值？**</span><span class="sxs-lookup"><span data-stu-id="9eef7-226">**What value does this change add?**</span></span>

<span data-ttu-id="9eef7-227">不需要離開目前 Cmdlet 或指令碼的即時線上說明，即可提供整合的學習體驗。</span><span class="sxs-lookup"><span data-stu-id="9eef7-227">Context-sensitive Help without leaving your current cmdlet or script provides an integrated learning experience.</span></span>

<span data-ttu-id="9eef7-228">**有哪些不同？**</span><span class="sxs-lookup"><span data-stu-id="9eef7-228">**What works differently?**</span></span>

<span data-ttu-id="9eef7-229">在舊版 Windows PowerShell ISE 中按 <kbd>F1</kbd>，會開啟本機電腦上的說明檔。</span><span class="sxs-lookup"><span data-stu-id="9eef7-229">Pressing <kbd>F1</kbd> in previous versions of Windows PowerShell ISE opened the help file on the local computer.</span></span> <span data-ttu-id="9eef7-230">在 Windows PowerShell ISE 3.0 和更新版本中，則會開啟內含可搜尋和可設定之 Cmdlet 說明的視窗。</span><span class="sxs-lookup"><span data-stu-id="9eef7-230">In Windows PowerShell ISE 3.0 and later, a window opens that contains the help for the cmdlet that is searchable and configurable.</span></span> <span data-ttu-id="9eef7-231">此說明體驗為 Windows PowerShell ISE 3.0 的新功能，而可更新說明則是 Windows PowerShell 3.0 的新功能。</span><span class="sxs-lookup"><span data-stu-id="9eef7-231">This Help experience is new for Windows PowerShell ISE 3.0, and Updatable Help is new for Windows PowerShell 3.0.</span></span>

## <a name="show-command-cmdlet"></a><span data-ttu-id="9eef7-232">Show-Command</span><span class="sxs-lookup"><span data-stu-id="9eef7-232">Show-Command cmdlet</span></span>

> <span data-ttu-id="9eef7-233">PowerShell 3.0 的新功能</span><span class="sxs-lookup"><span data-stu-id="9eef7-233">Added in PowerShell 3.0</span></span>

<span data-ttu-id="9eef7-234">`Show-Command` Cmdlet 可讓您填入圖形表單來撰寫或執行 Cmdlet 或函式。</span><span class="sxs-lookup"><span data-stu-id="9eef7-234">The `Show-Command` cmdlet enables you to compose or run a cmdlet or function by filling in a graphical form.</span></span> <span data-ttu-id="9eef7-235">此表單可讓使用者在圖形化環境中使用 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="9eef7-235">The form lets users work with Windows PowerShell in a graphical environment.</span></span>
<span data-ttu-id="9eef7-236">`Show-Command` 也可以啟用進階 Scripter 來建立快速的 Windows PowerShell 式 GUI。</span><span class="sxs-lookup"><span data-stu-id="9eef7-236">`Show-Command` also enables advanced scripters to create a quick Windows PowerShell-based GUI.</span></span>

<span data-ttu-id="9eef7-237">**這項變更增加了什麼價值？**</span><span class="sxs-lookup"><span data-stu-id="9eef7-237">**What value does this change add?**</span></span>

<span data-ttu-id="9eef7-238">透過在 Windows PowerShell 指令碼中使用 `Show-Command`，您可以提供使用者其所熟悉的圖形化環境。</span><span class="sxs-lookup"><span data-stu-id="9eef7-238">By using `Show-Command` in your Windows PowerShell scripts, you can provide your users with the graphical environment with which they're familiar.</span></span> <span data-ttu-id="9eef7-239">`Show-Command` 也可以協助入門使用者了解 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="9eef7-239">`Show-Command` can also help introductory users learn Windows PowerShell.</span></span>

<span data-ttu-id="9eef7-240">**有哪些不同？**</span><span class="sxs-lookup"><span data-stu-id="9eef7-240">**What works differently?**</span></span>

<span data-ttu-id="9eef7-241">`Show-Command` 是 Windows PowerShell ISE 3.0 的新功能。</span><span class="sxs-lookup"><span data-stu-id="9eef7-241">`Show-Command` is new Windows PowerShell ISE 3.0.</span></span>

## <a name="see-also"></a><span data-ttu-id="9eef7-242">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9eef7-242">See also</span></span>

<span data-ttu-id="9eef7-243">如需使用 Windows PowerShell ISE 的詳細資訊，請參閱[探索 Windows PowerShell 整合式指令碼環境](../components/ise/exploring-the-windows-powershell-ise.md)。</span><span class="sxs-lookup"><span data-stu-id="9eef7-243">For more information about using Windows PowerShell ISE, see [Exploring the Windows PowerShell Integrated Scripting Environment](../components/ise/exploring-the-windows-powershell-ise.md).</span></span>
