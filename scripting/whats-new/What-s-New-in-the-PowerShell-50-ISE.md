---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "PowerShell 50 ISE 的新功能"
ms.assetid: 38648d47-7c27-4b37-a40e-ad29948519c2
ms.openlocfilehash: e772c31ae407e73a96364ffedf98057760037836
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2017
---
# <a name="what39s-new-in-the-windows-powershell-ise"></a><span data-ttu-id="d2474-103">Windows PowerShell ISE 的新功能</span><span class="sxs-lookup"><span data-stu-id="d2474-103">What&#39;s New in the Windows PowerShell ISE</span></span>
<span data-ttu-id="d2474-104">本主題說明已在 Windows PowerShell® 整合式指令碼環境 (ISE) 版本中引進的新功能和更新功能。</span><span class="sxs-lookup"><span data-stu-id="d2474-104">This topic explains the new and updated features that have been introduced in versions of Windows PowerShell ® Integrated Scripting Environment (ISE).</span></span>

## <span data-ttu-id="d2474-105"><a name="overview"></a>功能描述</span><span class="sxs-lookup"><span data-stu-id="d2474-105"><a name="overview"></a>Feature description</span></span>
<span data-ttu-id="d2474-106">Windows PowerShell ISE 是一個主應用程式，可以讓您在圖形化與直覺式的環境中撰寫、執行及測試指令碼和模組。</span><span class="sxs-lookup"><span data-stu-id="d2474-106">The Windows PowerShell ISE is a host application that enables you to write, run, and test scripts and modules in a graphical and intuitive environment.</span></span> <span data-ttu-id="d2474-107">語法標色、TAB 鍵自動完成、視覺化偵錯、Unicode 相容性、即時線上說明等主要功能，提供豐富的指令碼撰寫體驗。</span><span class="sxs-lookup"><span data-stu-id="d2474-107">Key features such as syntax-coloring, tab completion, visual debugging, Unicode compliance, and context-sensitive Help provide a rich scripting experience.</span></span>

<span data-ttu-id="d2474-108">如需 Windows PowerShell ISE 的概觀，請參閱 [Windows PowerShell Integrated Scripting Environment overview](https://technet.microsoft.com/en-us/library/3c1892c2-bf84-4cb6-af26-1f453be9e671) (Windows PowerShell 整合式指令碼環境 (ISE))。</span><span class="sxs-lookup"><span data-stu-id="d2474-108">For an overview of Windows PowerShell ISE, see [Windows PowerShell Integrated Scripting Environment overview](https://technet.microsoft.com/en-us/library/3c1892c2-bf84-4cb6-af26-1f453be9e671).</span></span>

## <span data-ttu-id="d2474-109"><a name="versions"></a>Windows PowerShell ISE 的新功能和變更功能</span><span class="sxs-lookup"><span data-stu-id="d2474-109"><a name="versions"></a>New and changed functionality in Windows PowerShell ISE</span></span>
<span data-ttu-id="d2474-110">下表列出 Windows PowerShell 中這版 Windows PowerShell ISE 的新功能和變更功能。</span><span class="sxs-lookup"><span data-stu-id="d2474-110">The following table lists the new and changed features for this release of Windows PowerShell ISE in Windows PowerShell.</span></span>

|<span data-ttu-id="d2474-111">特色/功能</span><span class="sxs-lookup"><span data-stu-id="d2474-111">Feature/functionality</span></span>|<span data-ttu-id="d2474-112">Windows PowerShell ISE 4.0</span><span class="sxs-lookup"><span data-stu-id="d2474-112">Windows PowerShell ISE 4.0</span></span>|<span data-ttu-id="d2474-113">Windows PowerShell ISE 3.0</span><span class="sxs-lookup"><span data-stu-id="d2474-113">Windows PowerShell ISE 3.0</span></span>|<span data-ttu-id="d2474-114">Windows PowerShell ISE 2.0</span><span class="sxs-lookup"><span data-stu-id="d2474-114">Windows PowerShell ISE 2.0</span></span>|
|--------------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
|<span data-ttu-id="d2474-115">**[IntelliSense](#BKMK_Intellisense)**</span><span class="sxs-lookup"><span data-stu-id="d2474-115">**[IntelliSense](#BKMK_Intellisense)**</span></span>|<span data-ttu-id="d2474-116">X</span><span class="sxs-lookup"><span data-stu-id="d2474-116">X</span></span>|<span data-ttu-id="d2474-117">X</span><span class="sxs-lookup"><span data-stu-id="d2474-117">X</span></span>||
|<span data-ttu-id="d2474-118">**[程式碼片段](#bkmk_snippets)**</span><span class="sxs-lookup"><span data-stu-id="d2474-118">**[Snippets](#bkmk_snippets)**</span></span>|<span data-ttu-id="d2474-119">X</span><span class="sxs-lookup"><span data-stu-id="d2474-119">X</span></span>|<span data-ttu-id="d2474-120">X</span><span class="sxs-lookup"><span data-stu-id="d2474-120">X</span></span>||
|<span data-ttu-id="d2474-121">**[附加元件工具](#BKMK_AddOnTools)**</span><span class="sxs-lookup"><span data-stu-id="d2474-121">**[Add-on Tools](#BKMK_AddOnTools)**</span></span>|<span data-ttu-id="d2474-122">X</span><span class="sxs-lookup"><span data-stu-id="d2474-122">X</span></span>|<span data-ttu-id="d2474-123">X</span><span class="sxs-lookup"><span data-stu-id="d2474-123">X</span></span>||
|<span data-ttu-id="d2474-124">**[重新啟動管理員和自動儲存](#BKMK_RestartMgr)**</span><span class="sxs-lookup"><span data-stu-id="d2474-124">**[Restart Manager and Auto-save](#BKMK_RestartMgr)**</span></span>|<span data-ttu-id="d2474-125">X</span><span class="sxs-lookup"><span data-stu-id="d2474-125">X</span></span>|<span data-ttu-id="d2474-126">X</span><span class="sxs-lookup"><span data-stu-id="d2474-126">X</span></span>||
|<span data-ttu-id="d2474-127">**[主控台窗格](#BKMK_ConsolePane)**</span><span class="sxs-lookup"><span data-stu-id="d2474-127">**[Console Pane](#BKMK_ConsolePane)**</span></span>|<span data-ttu-id="d2474-128">X</span><span class="sxs-lookup"><span data-stu-id="d2474-128">X</span></span>|<span data-ttu-id="d2474-129">X</span><span class="sxs-lookup"><span data-stu-id="d2474-129">X</span></span>||
|<span data-ttu-id="d2474-130">**[最近使用的清單](#BKMK_MRU)**</span><span class="sxs-lookup"><span data-stu-id="d2474-130">**[Most-recently used list](#BKMK_MRU)**</span></span>|<span data-ttu-id="d2474-131">X</span><span class="sxs-lookup"><span data-stu-id="d2474-131">X</span></span>|<span data-ttu-id="d2474-132">X</span><span class="sxs-lookup"><span data-stu-id="d2474-132">X</span></span>||
|<span data-ttu-id="d2474-133">**[命令列參數](#BKMK_CommandLine)**</span><span class="sxs-lookup"><span data-stu-id="d2474-133">**[Command-line switches](#BKMK_CommandLine)**</span></span>|<span data-ttu-id="d2474-134">X</span><span class="sxs-lookup"><span data-stu-id="d2474-134">X</span></span>|<span data-ttu-id="d2474-135">X</span><span class="sxs-lookup"><span data-stu-id="d2474-135">X</span></span>||
|<span data-ttu-id="d2474-136">**[新編輯器功能](#BKMK_NewEditorFeatures)**</span><span class="sxs-lookup"><span data-stu-id="d2474-136">**[New editor features](#BKMK_NewEditorFeatures)**</span></span>|<span data-ttu-id="d2474-137">X</span><span class="sxs-lookup"><span data-stu-id="d2474-137">X</span></span>|<span data-ttu-id="d2474-138">X</span><span class="sxs-lookup"><span data-stu-id="d2474-138">X</span></span>||
|<span data-ttu-id="d2474-139">**[新的說明檢視器視窗](#BKMK_NewHelpViewer)**</span><span class="sxs-lookup"><span data-stu-id="d2474-139">**[New Help viewer window](#BKMK_NewHelpViewer)**</span></span>|<span data-ttu-id="d2474-140">X</span><span class="sxs-lookup"><span data-stu-id="d2474-140">X</span></span>|<span data-ttu-id="d2474-141">X</span><span class="sxs-lookup"><span data-stu-id="d2474-141">X</span></span>||
|<span data-ttu-id="d2474-142">**[Show-Command Cmdlet](#BKMK_ShowCommand)**</span><span class="sxs-lookup"><span data-stu-id="d2474-142">**[Show-Command cmdlet](#BKMK_ShowCommand)**</span></span>|<span data-ttu-id="d2474-143">X</span><span class="sxs-lookup"><span data-stu-id="d2474-143">X</span></span>|<span data-ttu-id="d2474-144">X</span><span class="sxs-lookup"><span data-stu-id="d2474-144">X</span></span>||

### <span data-ttu-id="d2474-145"><a name="BKMK_Intellisense"></a>IntelliSense</span><span class="sxs-lookup"><span data-stu-id="d2474-145"><a name="BKMK_Intellisense"></a>IntelliSense</span></span>
<span data-ttu-id="d2474-146">**ISE 3.0 的新功能**</span><span class="sxs-lookup"><span data-stu-id="d2474-146">**Added in ISE 3.0**</span></span>

<span data-ttu-id="d2474-147">IntelliSense 是屬於 Windows PowerShell ISE 的自動完成協助功能。</span><span class="sxs-lookup"><span data-stu-id="d2474-147">IntelliSense is an automatic-completion assistance feature that is part of Windows PowerShell ISE.</span></span> <span data-ttu-id="d2474-148">在您輸入文字時，IntelliSense 會顯示與輸入文字可能相符的 Cmdlet、參數、參數值、檔案或資料夾的可點選功能表。</span><span class="sxs-lookup"><span data-stu-id="d2474-148">IntelliSense displays clickable menus of potentially matching cmdlets, parameters, parameter values, files, or folders as you type.</span></span>

<span data-ttu-id="d2474-149">**這項變更增加了什麼價值？**</span><span class="sxs-lookup"><span data-stu-id="d2474-149">**What value does this change add?**</span></span>

<span data-ttu-id="d2474-150">透過 IntelliSense，您可以在使用 Windows PowerShell ISE 建立指令碼時更輕鬆地探索 Cmdlet 和語法。</span><span class="sxs-lookup"><span data-stu-id="d2474-150">With the addition of IntelliSense, it is easier to discover cmdlets and syntax when you use Windows PowerShell ISE to create scripts.</span></span> <span data-ttu-id="d2474-151">您也可以在建立新指令碼時透過 Windows PowerShell ISE 學習 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d2474-151">You can also use Windows PowerShell ISE to learn Windows PowerShell while you create new scripts.</span></span>

<span data-ttu-id="d2474-152">**有哪些不同？**</span><span class="sxs-lookup"><span data-stu-id="d2474-152">**What works differently?**</span></span>

<span data-ttu-id="d2474-153">在 Windows PowerShell ISE 3.0 或更新版本中輸入 Cmdlet 時，會顯示可捲動和可點選的功能表，可讓您瀏覽和選取適當的命令。</span><span class="sxs-lookup"><span data-stu-id="d2474-153">When you type cmdlets in the Windows PowerShell ISE 3.0 or later, a scrollable and clickable menu displays, allowing you to browse and select the appropriate commands.</span></span>

### <span data-ttu-id="d2474-154"><a name="BKMK_Snippets"></a>程式碼片段</span><span class="sxs-lookup"><span data-stu-id="d2474-154"><a name="BKMK_Snippets"></a>Snippets</span></span>
<span data-ttu-id="d2474-155">**ISE 3.0 的新功能**</span><span class="sxs-lookup"><span data-stu-id="d2474-155">**Added in ISE 3.0**</span></span>

<span data-ttu-id="d2474-156">*程式碼片段*是可以插入您在 Windows PowerShell ISE 中所建立之指令碼的簡短 Windows PowerShell 程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="d2474-156">*Snippets* are short sections of Windows PowerShell code that you can insert into the scripts you create in Windows PowerShell ISE.</span></span> <span data-ttu-id="d2474-157">Windows PowerShell ISE 隨附一組預設程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="d2474-157">Windows PowerShell ISE comes with a default set of snippets.</span></span> <span data-ttu-id="d2474-158">在 Windows PowerShell ISE 中工作時，您可以使用 **New-Snippet** Cmdlet 來新增程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="d2474-158">You can add snippets by using the **New-Snippet** cmdlet while working in Windows PowerShell ISE.</span></span>

<span data-ttu-id="d2474-159">**這項變更增加了什麼價值？**</span><span class="sxs-lookup"><span data-stu-id="d2474-159">**What value does this change add?**</span></span>

<span data-ttu-id="d2474-160">使用程式碼片段，您可以快速地組合並建立指令碼，以自動化您的環境。</span><span class="sxs-lookup"><span data-stu-id="d2474-160">By using snippets, you can quickly assemble and create scripts to automate your environment.</span></span>

<span data-ttu-id="d2474-161">**有哪些不同？**</span><span class="sxs-lookup"><span data-stu-id="d2474-161">**What works differently?**</span></span>

<span data-ttu-id="d2474-162">若要在 Windows PowerShell 3.0 或更新版本中使用程式碼片段，請按一下 [編輯] 功能表上的 [啟動片段]，或按 **Ctrl-J**。</span><span class="sxs-lookup"><span data-stu-id="d2474-162">To use snippets in Windows PowerShell 3.0 or later, on the **Edit** menu, click **Start Snippets**, or press **Ctrl-J**.</span></span>

### <span data-ttu-id="d2474-163"><a name="BKMK_AddOnTools"></a>附加元件工具</span><span class="sxs-lookup"><span data-stu-id="d2474-163"><a name="BKMK_AddOnTools"></a>Add-on tools</span></span>
<span data-ttu-id="d2474-164">**PowerShell 3.0 的新功能**</span><span class="sxs-lookup"><span data-stu-id="d2474-164">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="d2474-165">Windows PowerShell ISE 現在支援附加元件工具，這些工具是使用物件模型所新增的 Windows Presentation Foundation (WPF) 控制項。</span><span class="sxs-lookup"><span data-stu-id="d2474-165">Windows PowerShell ISE now supports add-on tools, which are Windows Presentation Foundation (WPF) controls that are added by using the object model.</span></span> <span data-ttu-id="d2474-166">附加元件工具可以顯示為主控台中的垂直或水平窗格。</span><span class="sxs-lookup"><span data-stu-id="d2474-166">Add-on tools can be displayed as a vertical or horizontal pane in the console.</span></span> <span data-ttu-id="d2474-167">窗格中的多個附加元件工具會顯示成一個索引標籤式控制項。</span><span class="sxs-lookup"><span data-stu-id="d2474-167">Multiple add-on tools in a pane are displayed as a tabbed control.</span></span> <span data-ttu-id="d2474-168">您也可以新增或移除非 Microsoft 合作廠商製作的附加元件工具。</span><span class="sxs-lookup"><span data-stu-id="d2474-168">You can also add or remove add-on tools that are produced by non-Microsoft parties.</span></span> <span data-ttu-id="d2474-169">如需如何匯入或移除附加元件工具的詳細資訊，請參閱 [Windows PowerShell ISE 作業](http://technet.microsoft.com/library/cc732148.aspx)。</span><span class="sxs-lookup"><span data-stu-id="d2474-169">For more information about how to import or remove add-on tools, see [Windows PowerShell ISE Operations](http://technet.microsoft.com/library/cc732148.aspx).</span></span>

<span data-ttu-id="d2474-170">**這項變更增加了什麼價值？**</span><span class="sxs-lookup"><span data-stu-id="d2474-170">**What value does this change add?**</span></span>

<span data-ttu-id="d2474-171">附加元件可讓您使用可加強指令碼體驗或為 Windows PowerShell ISE 新增功能的工具來擴充和自訂 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="d2474-171">Add-ons allow you to extend and customize Windows PowerShell ISE with tools that can enhance your scripting experience or add functionality to Windows PowerShell ISE.</span></span>

<span data-ttu-id="d2474-172">**有哪些不同？**</span><span class="sxs-lookup"><span data-stu-id="d2474-172">**What works differently?**</span></span>

<span data-ttu-id="d2474-173">Windows PowerShell ISE 3.0 和更新版本隨附 **Commands** 附加元件。</span><span class="sxs-lookup"><span data-stu-id="d2474-173">Windows PowerShell ISE 3.0 and later come with the **Commands** add-on.</span></span> <span data-ttu-id="d2474-174">**Commands** 附加元件可讓您瀏覽 Cmdlet，以及使用 指令碼 和 主控台 窗格並列存取 Cmdlet 的說明。</span><span class="sxs-lookup"><span data-stu-id="d2474-174">The **Commands** add-on allows you to browse cmdlets, and access help about the cmdlets side-by-side with the **Script** and **Console** Panes.</span></span>

<span data-ttu-id="d2474-175">使用 [附加元件] 功能表上的 [開啟附加元件工具網站] 命令，可以找到額外的附加元件。</span><span class="sxs-lookup"><span data-stu-id="d2474-175">Additional add-ons can be found by using the **Open Add-on Tools Website** command on the **Add-ons** menu.</span></span>

### <span data-ttu-id="d2474-176"><a name="BKMK_RestartMgr"></a>重新啟動管理員和自動儲存</span><span class="sxs-lookup"><span data-stu-id="d2474-176"><a name="BKMK_RestartMgr"></a>Restart manager and auto-save</span></span>
<span data-ttu-id="d2474-177">**PowerShell 3.0 的新功能**</span><span class="sxs-lookup"><span data-stu-id="d2474-177">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="d2474-178">Windows PowerShell ISE 現在每兩分鐘會自動在不同的位置儲存您未完成的指令碼。</span><span class="sxs-lookup"><span data-stu-id="d2474-178">Windows PowerShell ISE now automatically saves your open scripts every two minutes, in a separate location.</span></span>  <span data-ttu-id="d2474-179">如果 Windows PowerShell ISE 停止運作，或是作業系統重新啟動，則 Windows PowerShell ISE 在重新啟動之後，將會復原上一個工作階段中未完成的指令碼，即使該指令碼之前並未儲存也一樣。</span><span class="sxs-lookup"><span data-stu-id="d2474-179">If Windows PowerShell ISE stops working, or if the operating system is restarted, after Windows PowerShell ISE restarts, it recovers scripts that were open in the last session, even if the scripts were not saved.</span></span>

<span data-ttu-id="d2474-180">若要變更自動儲存間隔，請在主控台窗格中執行下列命令：**$psise.Options.AutoSaveMinuteInterval**。</span><span class="sxs-lookup"><span data-stu-id="d2474-180">To change the automatic saving interval, run the following command in the Console pane: **$psise.Options.AutoSaveMinuteInterval**.</span></span>

<span data-ttu-id="d2474-181">**這項變更增加了什麼價值？**</span><span class="sxs-lookup"><span data-stu-id="d2474-181">**What value does this change add?**</span></span>

<span data-ttu-id="d2474-182">由於已開啟的指令碼會在意外重新啟動的情況下自動儲存，您將能安心地在 Windows PowerShell ISE 內工作。</span><span class="sxs-lookup"><span data-stu-id="d2474-182">You can now work within Windows PowerShell ISE knowing that your open scripts are automatically saved in the event of an unexpected restart.</span></span>

<span data-ttu-id="d2474-183">**有哪些不同？**</span><span class="sxs-lookup"><span data-stu-id="d2474-183">**What works differently?**</span></span>

<span data-ttu-id="d2474-184">Windows PowerShell ISE 2.0 不會在重新啟動的情況下自動儲存指令碼。</span><span class="sxs-lookup"><span data-stu-id="d2474-184">Windows PowerShell ISE 2.0 does not save the scripts automatically in the event of a restart.</span></span>

### <span data-ttu-id="d2474-185"><a name="BKMK_MRU"></a>最近使用的清單</span><span class="sxs-lookup"><span data-stu-id="d2474-185"><a name="BKMK_MRU"></a>Most-recently used list</span></span>
<span data-ttu-id="d2474-186">**PowerShell 3.0 的新功能**</span><span class="sxs-lookup"><span data-stu-id="d2474-186">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="d2474-187">Windows PowerShell ISE 現在具有最近使用之檔案的清單。</span><span class="sxs-lookup"><span data-stu-id="d2474-187">Windows PowerShell ISE now has a most-recently used list for files.</span></span> <span data-ttu-id="d2474-188">當您在 Windows PowerShell ISE 中開啟檔案時，該檔案會被新增至 [檔案] 功能表上的 [最近使用的清單]。</span><span class="sxs-lookup"><span data-stu-id="d2474-188">When you open a file in Windows PowerShell ISE, the file is added to the most-recently used list on the **File** menu.</span></span>

<span data-ttu-id="d2474-189">若要變更 [最近使用的清單] 中預設數目的檔案，請在主控台窗格中執行下列命令：**$psise.Options.MruCount**。</span><span class="sxs-lookup"><span data-stu-id="d2474-189">To change the default number of files in the most-recently used list, run the following command in the Console Pane: **$psise.Options.MruCount**.</span></span>

<span data-ttu-id="d2474-190">**這項變更增加了什麼價值？**</span><span class="sxs-lookup"><span data-stu-id="d2474-190">**What value does this change add?**</span></span>

<span data-ttu-id="d2474-191">您現在可以使用 [最近使用的清單] 來輕鬆地存取常用檔案。</span><span class="sxs-lookup"><span data-stu-id="d2474-191">You can now use the most-recently used list to easily access your frequently-used files.</span></span>

<span data-ttu-id="d2474-192">**有哪些不同？**</span><span class="sxs-lookup"><span data-stu-id="d2474-192">**What works differently?**</span></span>

<span data-ttu-id="d2474-193">Windows PowerShell ISE 2.0 並不具有 [最近使用的清單]。</span><span class="sxs-lookup"><span data-stu-id="d2474-193">Windows PowerShell ISE 2.0 does not have a most-recently used list.</span></span>

### <span data-ttu-id="d2474-194"><a name="BKMK_ConsolePane"></a>主控台窗格</span><span class="sxs-lookup"><span data-stu-id="d2474-194"><a name="BKMK_ConsolePane"></a>Console Pane</span></span>
<span data-ttu-id="d2474-195">**PowerShell 3.0 的新功能**</span><span class="sxs-lookup"><span data-stu-id="d2474-195">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="d2474-196">第一版 Windows PowerShell ISE 中獨立的命令與輸出窗格已結合成單一主控台窗格。</span><span class="sxs-lookup"><span data-stu-id="d2474-196">The separate Command and Output Panes that were available in the first release of Windows PowerShell ISE have been combined into a single Console Pane.</span></span> <span data-ttu-id="d2474-197">這個主控台窗格在功能和外觀上與一般的 Windows PowerShell 主控台類似，但包含下列增強功能 (大部分已在本主題中描述)。</span><span class="sxs-lookup"><span data-stu-id="d2474-197">The Console Pane is similar in function and appearance to a typical Windows PowerShell console, but it includes the following enhancements (most are described in this topic).</span></span>

-   <span data-ttu-id="d2474-198">輸入文字 (非輸出文字) 的語法著色 (包括 XML 語法)</span><span class="sxs-lookup"><span data-stu-id="d2474-198">Syntax coloring for input text (not output text), including XML syntax</span></span>

-   <span data-ttu-id="d2474-199">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="d2474-199">IntelliSense</span></span>

-   <span data-ttu-id="d2474-200">括號對稱</span><span class="sxs-lookup"><span data-stu-id="d2474-200">Brace matching</span></span>

-   <span data-ttu-id="d2474-201">錯誤指示</span><span class="sxs-lookup"><span data-stu-id="d2474-201">Error indication</span></span>

-   <span data-ttu-id="d2474-202">完整 Unicode 支援</span><span class="sxs-lookup"><span data-stu-id="d2474-202">Full Unicode support</span></span>

-   <span data-ttu-id="d2474-203">**F1** 即時線上說明</span><span class="sxs-lookup"><span data-stu-id="d2474-203">**F1** context-sensitive help</span></span>

-   <span data-ttu-id="d2474-204">**Ctrl+F1** 即時線上顯示命令 (Show-Command)</span><span class="sxs-lookup"><span data-stu-id="d2474-204">**Ctrl+F1** context-sensitive Show-Command</span></span>

-   <span data-ttu-id="d2474-205">複雜指令碼與由右至左語言支援</span><span class="sxs-lookup"><span data-stu-id="d2474-205">Complex script and right-to-left support</span></span>

-   <span data-ttu-id="d2474-206">字型支援</span><span class="sxs-lookup"><span data-stu-id="d2474-206">Font support</span></span>

-   <span data-ttu-id="d2474-207">縮放</span><span class="sxs-lookup"><span data-stu-id="d2474-207">Zoom</span></span>

-   <span data-ttu-id="d2474-208">行選取與區塊選取模式</span><span class="sxs-lookup"><span data-stu-id="d2474-208">Line-select and block-select modes</span></span>

-   <span data-ttu-id="d2474-209">按**向上**鍵以在主控台中檢視歷程記錄時，保留命令列中輸入的內容</span><span class="sxs-lookup"><span data-stu-id="d2474-209">Preservation of typed content at the command line when you press the **Up** arrow to view history in the console</span></span>

<span data-ttu-id="d2474-210">**這項變更增加了什麼價值？**</span><span class="sxs-lookup"><span data-stu-id="d2474-210">**What value does this change add?**</span></span>

<span data-ttu-id="d2474-211">新增這些主控台窗格變更可提供主控台介面更一致的指令碼體驗。</span><span class="sxs-lookup"><span data-stu-id="d2474-211">The addition of these Console Pane changes provides a scripting experience that is more consistent with the console interface.</span></span>

<span data-ttu-id="d2474-212">**有哪些不同？**</span><span class="sxs-lookup"><span data-stu-id="d2474-212">**What works differently?**</span></span>

<span data-ttu-id="d2474-213">Windows PowerShell ISE 2.0 具有個別的命令和輸出窗格。</span><span class="sxs-lookup"><span data-stu-id="d2474-213">Windows PowerShell ISE 2.0 has separate Command and Output Panes.</span></span>

### <span data-ttu-id="d2474-214"><a name="BKMK_CommandLine"></a>命令列參數</span><span class="sxs-lookup"><span data-stu-id="d2474-214"><a name="BKMK_CommandLine"></a>Command-line switches</span></span>
<span data-ttu-id="d2474-215">**PowerShell 3.0 的新功能**</span><span class="sxs-lookup"><span data-stu-id="d2474-215">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="d2474-216">如果透過命令列啟動 Windows PowerShell ISE (輸入 **Powershell_ise.exe**)，您可以新增下列新的命令列參數。</span><span class="sxs-lookup"><span data-stu-id="d2474-216">If you start Windows PowerShell ISE from the command line (by typing **powershell_ise.exe**), you can add the following new command-line switches.</span></span>

-   <span data-ttu-id="d2474-217">*-NoProfile*：在沒有執行 **$profile** 的情況下啟動 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="d2474-217">*-NoProfile*: Starts Windows PowerShell ISE without running **$profile**</span></span>

-   <span data-ttu-id="d2474-218">*-Help*：顯示 [說明] 視窗</span><span class="sxs-lookup"><span data-stu-id="d2474-218">*-Help*: Displays a Help window</span></span>

-   <span data-ttu-id="d2474-219">*-mta*：以多執行緒 Apartment 模式啟動 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="d2474-219">*-mta*: Starts Windows PowerShell ISE in multithreaded apartment mode.</span></span> <span data-ttu-id="d2474-220">Windows PowerShell ISE 的預設作業模式是單一執行緒 Apartment 模式，或 *-sta*。</span><span class="sxs-lookup"><span data-stu-id="d2474-220">The default operation mode for Windows PowerShell ISE is single-threaded apartment mode, or *-sta*.</span></span>

<span data-ttu-id="d2474-221">**這項變更增加了什麼價值？**</span><span class="sxs-lookup"><span data-stu-id="d2474-221">**What value does this change add?**</span></span>

<span data-ttu-id="d2474-222">新增這些命令列參數可讓您控制 Windows PowerShell ISE 的執行環境。</span><span class="sxs-lookup"><span data-stu-id="d2474-222">The addition of these command-line switches allows you to control the environment in which the Windows PowerShell ISE runs.</span></span>

<span data-ttu-id="d2474-223">**有哪些不同？**</span><span class="sxs-lookup"><span data-stu-id="d2474-223">**What works differently?**</span></span>

<span data-ttu-id="d2474-224">Windows PowerShell ISE 2.0 無法辨識這些命令列參數。</span><span class="sxs-lookup"><span data-stu-id="d2474-224">Windows PowerShell ISE 2.0 does not recognize these command-line switches.</span></span>

### <span data-ttu-id="d2474-225"><a name="BKMK_NewEditorFeatures"></a>新編輯器功能</span><span class="sxs-lookup"><span data-stu-id="d2474-225"><a name="BKMK_NewEditorFeatures"></a>New editor features</span></span>
<span data-ttu-id="d2474-226">**PowerShell 3.0 的新功能**</span><span class="sxs-lookup"><span data-stu-id="d2474-226">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="d2474-227">Windows PowerShell ISE 其他的編輯功能包括：</span><span class="sxs-lookup"><span data-stu-id="d2474-227">Other Windows PowerShell ISE editing features include:</span></span>

-   <span data-ttu-id="d2474-228">**XML 語法著色**Windows PowerShell ISE 現在會以對 Windows PowerShell 語法進行著色的相同方法，對 XML 語法進行著色。</span><span class="sxs-lookup"><span data-stu-id="d2474-228">**XML syntax coloring**Windows PowerShell ISE now colors XML syntax in the same way as it colors Windows PowerShell syntax.</span></span>

-   <span data-ttu-id="d2474-229">**括號對稱** Windows PowerShell ISE 包括括號對稱和反白顯示，而且可以透過下列方式使用：(例如，如果已選取左大括號，則使用 [移至相符項目] 命令或 **[Ctrl + ]** 便能找到右大括號)。</span><span class="sxs-lookup"><span data-stu-id="d2474-229">**Brace matching** Windows PowerShell ISE includes brace matching and highlighting, and can be used in the following ways: (for example, using the **Go to Match** command or **Ctrl + ]** locates the closing brace, if you have an opening brace selected).</span></span>

-   <span data-ttu-id="d2474-230">**大綱檢視** 指令碼窗格支援大綱功能，按一下左邊界的加號或減號，即允許摺疊或展開程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="d2474-230">**Outline view** The Script Pane supports outlining, which allows collapsing or expanding sections of code by clicking plus or minus signs in the left margin.</span></span> <span data-ttu-id="d2474-231">您可以使用大括號或 **#region** 和 **#endregion** 標籤，標示可摺疊區段的開頭或結尾。</span><span class="sxs-lookup"><span data-stu-id="d2474-231">You can use braces or the **#region** and **#endregion** tags to mark the beginning or end of a collapsible section.</span></span> <span data-ttu-id="d2474-232">若要展開或摺疊所有區域，請按 **Ctrl + M**。</span><span class="sxs-lookup"><span data-stu-id="d2474-232">To expand or collapse all regions, press **Ctrl + M**.</span></span>

-   <span data-ttu-id="d2474-233">**拖放文字編輯**Windows PowerShell ISE 現在支援拖放文字編輯。</span><span class="sxs-lookup"><span data-stu-id="d2474-233">**Drag and drop text editing**Windows PowerShell ISE now supports drag and drop text editing.</span></span> <span data-ttu-id="d2474-234">您可以選取任何文字區塊，並將該文字拖曳到編輯器或主控台中的其他位置來移動文字。</span><span class="sxs-lookup"><span data-stu-id="d2474-234">You can select any block of text and drag that text to another location in the editor or the console to move the text.</span></span> <span data-ttu-id="d2474-235">如果您在拖曳選取的文字時按住 Ctrl 鍵，則放開滑鼠按鈕時，會將文字複製到新位置。</span><span class="sxs-lookup"><span data-stu-id="d2474-235">If you hold down the Ctrl key while you drag the selected text, when you release the mouse button the text is copied to the new location.</span></span> <span data-ttu-id="d2474-236">在此版本及舊版的 Windows PowerShell ISE 中，當您將檔案拖放到 Windows PowerShell ISE 上時，Windows PowerShell ISE 便會開啟該檔案。</span><span class="sxs-lookup"><span data-stu-id="d2474-236">In this version of Windows PowerShell ISE, as well as the previous version of Windows PowerShell ISE, when you drag and drop files onto Windows PowerShell ISE, Windows PowerShell ISE opens the file.</span></span>

-   <span data-ttu-id="d2474-237">**剖析錯誤顯示** 剖析錯誤會以紅色底線表示。</span><span class="sxs-lookup"><span data-stu-id="d2474-237">**Parse error display** Parse errors are indicated with red underlines.</span></span> <span data-ttu-id="d2474-238">暫留於指示的錯誤時，工具提示文字會顯示在程式碼中發現的問題。</span><span class="sxs-lookup"><span data-stu-id="d2474-238">When you hover over an indicated error, tooltip text displays the problem that was found in the code.</span></span>

-   <span data-ttu-id="d2474-239">**縮放** 您可以使用縮放滑桿 (在 Windows PowerShell ISE 視窗的右下角) 或在主控台窗格中輸入 **$psise.options.Zoom** 命令，來設定主控台內容的縮放百分比。</span><span class="sxs-lookup"><span data-stu-id="d2474-239">**Zoom** The zoom percentage of the console’s content can be set by using the zoom slider (in the lower right corner of Windows PowerShell ISE window), or by entering the command **$psise.options.Zoom** in the Console Pane.</span></span>

-   <span data-ttu-id="d2474-240">**RTF 複製與貼上** 複製到 Windows PowerShell ISE 中的剪貼簿將會保留原始選取項目的字型、大小及色彩資訊。</span><span class="sxs-lookup"><span data-stu-id="d2474-240">**Rich text copy and paste** Copying to the clipboard in Windows PowerShell ISE preserves the font, size, and color information of the original selection.</span></span>

-   <span data-ttu-id="d2474-241">**區塊選擇** 在使用滑鼠選取指令碼窗格中的文字時按住 ALT 鍵或按 **Alt+Shift+方向鍵**，即可選取一個區塊的文字。</span><span class="sxs-lookup"><span data-stu-id="d2474-241">**Block selection** You can select a block of text by holding down the ALT key while selecting text in the Script Pane with your mouse, or by pressing **Alt+Shift+Arrow**.</span></span>

<span data-ttu-id="d2474-242">**這項變更增加了什麼價值？**</span><span class="sxs-lookup"><span data-stu-id="d2474-242">**What value does this change add?**</span></span>

<span data-ttu-id="d2474-243">其他編輯功能提供更一致且功能強大的編輯環境。</span><span class="sxs-lookup"><span data-stu-id="d2474-243">The additional editing features provide a more consistent and powerful editing environment.</span></span>

<span data-ttu-id="d2474-244">**有哪些不同？**</span><span class="sxs-lookup"><span data-stu-id="d2474-244">**What works differently?**</span></span>

<span data-ttu-id="d2474-245">Windows PowerShell ISE 2.0 沒有這些編輯增強功能。</span><span class="sxs-lookup"><span data-stu-id="d2474-245">These editing enhancements were not present in Windows PowerShell ISE 2.0.</span></span>

### <span data-ttu-id="d2474-246"><a name="BKMK_NewHelpViewer"></a>新的說明檢視器視窗</span><span class="sxs-lookup"><span data-stu-id="d2474-246"><a name="BKMK_NewHelpViewer"></a>New Help viewer window</span></span>
<span data-ttu-id="d2474-247">**PowerShell 3.0 的新功能**</span><span class="sxs-lookup"><span data-stu-id="d2474-247">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="d2474-248">當您的游標在 Cmdlet 中或當您反白顯示 Cmdlet 的一部分時，如果按 **F1**，新的說明檢視器就會開啟有關反白顯示 Cmdlet 的即時線上說明。</span><span class="sxs-lookup"><span data-stu-id="d2474-248">If you press **F1** when your cursor is in a cmdlet, or you have part of a cmdlet highlighted, the new Help viewer opens context-sensitive Help about the highlighted cmdlet.</span></span> <span data-ttu-id="d2474-249">如果要顯示「關於 Windows PowerShell 」說明，請在主控台窗格中輸入 **operators**，然後按 **F1**。</span><span class="sxs-lookup"><span data-stu-id="d2474-249">To display Windows PowerShell About help, type  **operators** in the console pane, and then press **F1**.</span></span>

<span data-ttu-id="d2474-250">使用這項功能之前，請先從 Microsoft 網站下載最新版本的 Windows PowerShell 說明主題。</span><span class="sxs-lookup"><span data-stu-id="d2474-250">Before you use this feature, download the most current version of Windows PowerShell Help topics from the Microsoft website.</span></span> <span data-ttu-id="d2474-251">下載說明主題的最簡單方法是以系統管理員身分執行 Windows PowerShell ISE，並於主控台窗格中執行 **Update-Help** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d2474-251">The simplest method for downloading the Help topics is to run the **Update-Help** cmdlet in the Console Pane when running Windows PowerShell ISE as administrator.</span></span>

<span data-ttu-id="d2474-252">您可以變更 **F1** 鍵尋找說明的位置。</span><span class="sxs-lookup"><span data-stu-id="d2474-252">You can alter where the **F1** key looks for Help.</span></span> <span data-ttu-id="d2474-253">您在 [工具]/[選項] 功能表中，於 [一般設定] 索引標籤的 [其他設定] 下，可以設定或清除 [使用本機說明內容而非線上內容] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d2474-253">In the **Tools**/**Options** menu, on the **General Settings** tab, under **Other Settings**, you can set or clear the checkbox **Use local help content instead of online content**.</span></span> <span data-ttu-id="d2474-254">核取時，用戶端會在模組資料夾中發現的已下載說明中尋找 Cmdlet 說明。</span><span class="sxs-lookup"><span data-stu-id="d2474-254">If checked, then the client looks for the cmdlet Help in the downloaded Help found in the modules folder.</span></span>  <span data-ttu-id="d2474-255">如果清除此核取方塊，則用戶端會在 TechNet 文件庫中尋找 Cmdlet 說明。</span><span class="sxs-lookup"><span data-stu-id="d2474-255">If the checkbox is cleared, then the client looks on the TechNet library for the cmdlet help.</span></span>

<span data-ttu-id="d2474-256">**這項變更增加了什麼價值？**</span><span class="sxs-lookup"><span data-stu-id="d2474-256">**What value does this change add?**</span></span>

<span data-ttu-id="d2474-257">不需要離開目前 Cmdlet 或指令碼的即時線上說明，即可提供順暢的學習經驗。</span><span class="sxs-lookup"><span data-stu-id="d2474-257">Context-sensitive Help without leaving your current cmdlet or script provides a seamless learning experience.</span></span>

<span data-ttu-id="d2474-258">**有哪些不同？**</span><span class="sxs-lookup"><span data-stu-id="d2474-258">**What works differently?**</span></span>

<span data-ttu-id="d2474-259">在舊版的 Windows PowerShell ISE 中按 F1，會開啟本機電腦上的說明檔。</span><span class="sxs-lookup"><span data-stu-id="d2474-259">Pressing F1 in previous versions of Windows PowerShell ISE opened the help file on the local computer.</span></span> <span data-ttu-id="d2474-260">在 Windows PowerShell ISE 3.0 和更新版本中，則會開啟內含可搜尋和可設定之 Cmdlet 說明的視窗。</span><span class="sxs-lookup"><span data-stu-id="d2474-260">In Windows PowerShell ISE 3.0 and later, a window opens that contains the help for the cmdlet that is searchable and configurable.</span></span> <span data-ttu-id="d2474-261">此說明體驗為 Windows PowerShell ISE 3.0 的新功能，而可更新說明則是 Windows PowerShell 3.0 的新功能。</span><span class="sxs-lookup"><span data-stu-id="d2474-261">This Help experience is new for Windows PowerShell ISE 3.0, and Updatable Help is new for Windows PowerShell 3.0.</span></span>

### <span data-ttu-id="d2474-262"><a name="BKMK_ShowCommand"></a>Show-Command Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d2474-262"><a name="BKMK_ShowCommand"></a>Show-Command cmdlet</span></span>
<span data-ttu-id="d2474-263">**PowerShell 3.0 的新功能**</span><span class="sxs-lookup"><span data-stu-id="d2474-263">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="d2474-264">**Show-Command** Cmdlet 可讓您填入圖形表單，來撰寫或執行 Cmdlet 或函式。</span><span class="sxs-lookup"><span data-stu-id="d2474-264">The **Show-Command** cmdlet enables you to compose or run a cmdlet or function by filling in a graphical form.</span></span> <span data-ttu-id="d2474-265">此表單可讓使用者在圖形化環境中使用 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d2474-265">The form lets users work with Windows PowerShell in a graphical environment.</span></span> <span data-ttu-id="d2474-266">**Show-Command** 也可以啟用進階 Scripter 來建立快速的 Windows PowerShell 式 GUI。</span><span class="sxs-lookup"><span data-stu-id="d2474-266">**Show-Command** also enables advanced scripters to create a quick Windows PowerShell-based GUI.</span></span>

<span data-ttu-id="d2474-267">**這項變更增加了什麼價值？**</span><span class="sxs-lookup"><span data-stu-id="d2474-267">**What value does this change add?**</span></span>

<span data-ttu-id="d2474-268">透過在 Windows PowerShell 指令碼中使用 **Show-Command**，您可以將使用者所熟悉的圖形化環境提供給他們。</span><span class="sxs-lookup"><span data-stu-id="d2474-268">By using **Show-Command** in your Windows PowerShell scripts, you can provide your users with the graphical environment with which they are familiar.</span></span> <span data-ttu-id="d2474-269">**Show-Command** 也可以協助入門使用者了解 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d2474-269">**Show-Command** can also help introductory users learn Windows PowerShell.</span></span>

<span data-ttu-id="d2474-270">**有哪些不同？**</span><span class="sxs-lookup"><span data-stu-id="d2474-270">**What works differently?**</span></span>

<span data-ttu-id="d2474-271">Show-Command 為 Windows PowerShell ISE 3.0 的新功能</span><span class="sxs-lookup"><span data-stu-id="d2474-271">Show-Command is new Windows PowerShell ISE 3.0.</span></span>

## <span data-ttu-id="d2474-272"><a name="BKMK_LINKS"></a>另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2474-272"><a name="BKMK_LINKS"></a>See also</span></span>
<span data-ttu-id="d2474-273">如需在 Windows PowerShell 中使用 Windows PowerShell ISE 的詳細資訊，請參閱下列連結。</span><span class="sxs-lookup"><span data-stu-id="d2474-273">For more information about using Windows PowerShell ISE in Windows PowerShell, see the following links.</span></span>

- [<span data-ttu-id="d2474-274">使用 Windows PowerShell 整合式指令碼環境</span><span class="sxs-lookup"><span data-stu-id="d2474-274">Using the Windows PowerShell Integrated Scripting Environment</span></span>](../core-powershell/ise/Using-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="d2474-275">TechNet Wiki 上的 ISE</span><span class="sxs-lookup"><span data-stu-id="d2474-275">ISE on the TechNet Wiki</span></span>](http://social.technet.microsoft.com/wiki/search/searchresults.aspx?q=ISE)
- [<span data-ttu-id="d2474-276">Script Center</span><span class="sxs-lookup"><span data-stu-id="d2474-276">Script Center</span></span>](http://technet.microsoft.com/scriptcenter/default)

