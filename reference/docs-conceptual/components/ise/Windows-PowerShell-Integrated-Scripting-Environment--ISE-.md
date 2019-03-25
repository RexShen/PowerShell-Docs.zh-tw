---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Windows PowerShell 整合式指令碼環境 ISE
ms.assetid: f156b92d-0203-46d2-89c7-b4989d32e3d2
ms.openlocfilehash: 3002c2cb7213b1c2d7201dddf5ff3c0651fad767
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2019
ms.locfileid: "58054708"
---
# <a name="windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="e16bc-103">Windows PowerShell 整合式指令碼環境 (ISE)</span><span class="sxs-lookup"><span data-stu-id="e16bc-103">Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

<span data-ttu-id="e16bc-104">Windows PowerShell 整合式指令碼環境 (ISE) 是 Windows PowerShell 引擎和語言之兩部主機的其中一部。</span><span class="sxs-lookup"><span data-stu-id="e16bc-104">The Windows PowerShell Integrated Scripting Environment (ISE) is one of two hosts for the Windows PowerShell engine and language.</span></span> <span data-ttu-id="e16bc-105">您可以使用它，透過 Windows PowerShell 主控台中無法使用的方式來撰寫、執行和測試指令碼。</span><span class="sxs-lookup"><span data-stu-id="e16bc-105">With it you can write, run, and test scripts in ways that are not available in the Windows PowerShell Console.</span></span> <span data-ttu-id="e16bc-106">ISE 新增語法著色、Tab 鍵自動完成、IntelliSense、視覺化偵錯和即時線上說明。</span><span class="sxs-lookup"><span data-stu-id="e16bc-106">The ISE adds syntax-coloring, tab completion, IntelliSense, visual debugging, and context sensitive Help.</span></span>

<span data-ttu-id="e16bc-107">ISE 可讓您在主控台窗格中執行命令，但也支援數個窗格，可用來同時檢視您的指令碼和可插入 ISE 之其他工具的原始碼。</span><span class="sxs-lookup"><span data-stu-id="e16bc-107">The ISE lets you run commands in a console pane, but it also supports panes that you can use to simultaneously view the source code of your script and other tools that can plug into the ISE.</span></span> <span data-ttu-id="e16bc-108">您甚至可以同時開啟多個指令碼視窗，這在所偵錯的指令碼使用其他指令碼或模組中所定義的函式時特別有用。</span><span class="sxs-lookup"><span data-stu-id="e16bc-108">You can even open up multiple script windows at the same time, which is especially helpful when you are debugging a script that uses functions defined in other scripts or modules.</span></span>

## <a name="whats-new"></a><span data-ttu-id="e16bc-109">新功能</span><span class="sxs-lookup"><span data-stu-id="e16bc-109">What’s New</span></span>

<span data-ttu-id="e16bc-110">以下是一些已在最新版的 PowerShell ISE 中新增的功能。</span><span class="sxs-lookup"><span data-stu-id="e16bc-110">Here are some of the features that have been added to the ISE in the most recent releases of PowerShell.</span></span>

### <a name="added-in-powershell-30-windows-server-2012-windows-8"></a><span data-ttu-id="e16bc-111">PowerShell 3.0 的新功能 (Windows Server 2012、Windows 8)</span><span class="sxs-lookup"><span data-stu-id="e16bc-111">Added in PowerShell 3.0 (Windows Server 2012, Windows 8)</span></span>

<span data-ttu-id="e16bc-112">在您輸入文字時，**IntelliSense** 透過顯示與輸入文字相符的 Cmdlet、參數、參數值、檔案或資料夾的功能表，來自動完成命令。</span><span class="sxs-lookup"><span data-stu-id="e16bc-112">**IntelliSense** automatically completes your commands by displaying menus of matching cmdlets, parameters, parameter values, files, or folders as you type.</span></span>

<span data-ttu-id="e16bc-113">**程式碼片段**是可輕鬆地插入所撰寫指令碼的簡短程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="e16bc-113">**Snippets** are short sections of code that you can easily insert into the scripts your write.</span></span> <span data-ttu-id="e16bc-114">有用程式碼片段的集合包含在方塊中，而且使用 **New-Snippet** Cmdlet 可以有更多的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="e16bc-114">A collection of useful snippets is included in the box and you can more by using the **New-Snippet** cmdlet.</span></span>

<span data-ttu-id="e16bc-115">**附加元件工具**可將功能新增至 ISE，藉由撰寫與 [Windows PowerShell ISE 指令碼物件模型](../../core-powershell/ise/The-ISE-Object-Model-Hierarchy.md)互動的程式碼即可建立。</span><span class="sxs-lookup"><span data-stu-id="e16bc-115">**Add-on tools** that add features to the ISE can be created by writing code that interacts with [The Windows PowerShell ISE Scripting Object Model](../../core-powershell/ise/The-ISE-Object-Model-Hierarchy.md).</span></span>

<span data-ttu-id="e16bc-116">這些工具可以在索引標籤式窗格中顯示控制項，或在背景無形地工作。</span><span class="sxs-lookup"><span data-stu-id="e16bc-116">These tools can display controls in a tabbed pane or work invisibly in the background.</span></span> <span data-ttu-id="e16bc-117">**命令**附加元件是不錯的範例，並包含 3.0 版和更新版本，會顯示可用命令的清單和其說明。</span><span class="sxs-lookup"><span data-stu-id="e16bc-117">The **Commands** add-on is a good example and is included with version 3.0 and later that displays a list of the available commands and their Help.</span></span>

<span data-ttu-id="e16bc-118">**重新啟動管理員和自動儲存**每兩分鐘會自動儲存您的指令碼，協助您避免在當機或意外重新啟動時遺失工作。</span><span class="sxs-lookup"><span data-stu-id="e16bc-118">**Restart Manager and Auto-save** automatically save your scripts every two minutes to help you avoid the loss of your work in the event of a crash or unexpected restart.</span></span>

<span data-ttu-id="e16bc-119">**[最近使用的清單]** 現在是 [開啟舊檔] 功能表的一部分，讓您更輕鬆地取得您最常使用的檔案。</span><span class="sxs-lookup"><span data-stu-id="e16bc-119">**Most Recently Used list** is now part of the File Open menu to make it easier to get to the files you use most often.</span></span>

<span data-ttu-id="e16bc-120">**合併的主控台窗格**。</span><span class="sxs-lookup"><span data-stu-id="e16bc-120">**Merged Console pane**.</span></span> <span data-ttu-id="e16bc-121">在舊版的 ISE 中，具有個別的 [命令] 和 [輸出] 窗格。</span><span class="sxs-lookup"><span data-stu-id="e16bc-121">In previous versions of the ISE there were separate Command and Output panes.</span></span> <span data-ttu-id="e16bc-122">它們現在合併成單一窗格，更直接與您在 Windows PowerShell 主控台中看到的內容相似。</span><span class="sxs-lookup"><span data-stu-id="e16bc-122">They are now combined into a single pane that more directly mimics what you see in the Windows PowerShell Console.</span></span>

<span data-ttu-id="e16bc-123">**命令列參數**。</span><span class="sxs-lookup"><span data-stu-id="e16bc-123">**Command-line switches**.</span></span> <span data-ttu-id="e16bc-124">數個新的命令列參數可讓您更充分掌控 ISE 的運作方式。</span><span class="sxs-lookup"><span data-stu-id="e16bc-124">Several new command-line switches give you more control over the way the ISE works.</span></span> <span data-ttu-id="e16bc-125">-NoProfile 會啟動 ISE，但不執行設定檔指令碼。</span><span class="sxs-lookup"><span data-stu-id="e16bc-125">-NoProfile starts the ISE without running a profile script.</span></span> <span data-ttu-id="e16bc-126">-Help 會開啟含 ISE 的說明視窗。</span><span class="sxs-lookup"><span data-stu-id="e16bc-126">-Help opens up a help window with the ISE.</span></span> <span data-ttu-id="e16bc-127">-mta 會使用「多執行緒 Apartment 模式」啟動 ISE。</span><span class="sxs-lookup"><span data-stu-id="e16bc-127">-mta starts the ISE in “multi-threaded apartment mode”.</span></span> <span data-ttu-id="e16bc-128">預設值是單一執行緒。</span><span class="sxs-lookup"><span data-stu-id="e16bc-128">The default is single-threaded.</span></span>

<span data-ttu-id="e16bc-129">**新編輯器功能**可輕鬆地建立和讀取您的程式碼︰</span><span class="sxs-lookup"><span data-stu-id="e16bc-129">**New editor features** make it easier to create and read your code:</span></span>

- <span data-ttu-id="e16bc-130">**XML 語法著色**。</span><span class="sxs-lookup"><span data-stu-id="e16bc-130">**XML syntax coloring**.</span></span> <span data-ttu-id="e16bc-131">ISE 編輯器現在將 XML 語法著色，方法與將 Windows PowerShell 程式碼語法著色相同。</span><span class="sxs-lookup"><span data-stu-id="e16bc-131">The ISE editor now colors XML syntax in the same way as it colors Windows PowerShell code syntax.</span></span>

- <span data-ttu-id="e16bc-132">**括號對稱**。</span><span class="sxs-lookup"><span data-stu-id="e16bc-132">**Brace matching**.</span></span> <span data-ttu-id="e16bc-133">Windows PowerShell ISE 會反白顯示對稱的括號，協助您確保左右括號數目相符。</span><span class="sxs-lookup"><span data-stu-id="e16bc-133">The ISEWindows PowerShell ISE highlights matching braces to help you ensure you have the right number of closing braces to match your opening ones.</span></span> <span data-ttu-id="e16bc-134">使用 CTRL- \[ 找出與游標所在左括號對稱的右括號。</span><span class="sxs-lookup"><span data-stu-id="e16bc-134">Use CTRL-\[ to locate the closing brace that matches the opening brace that the cursor is on.</span></span>

- <span data-ttu-id="e16bc-135">**大綱檢視**。</span><span class="sxs-lookup"><span data-stu-id="e16bc-135">**Outline view**.</span></span> <span data-ttu-id="e16bc-136">您可以按一下左邊界的加號和減號，來摺疊或展開程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="e16bc-136">You can collapse or expand sections of your code by clicking the plus and minus signs in the left margin.</span></span> <span data-ttu-id="e16bc-137">這可讓您更輕鬆地找到您要在長指令碼中尋找的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e16bc-137">This makes it easier to find the code you’re looking for in a long script.</span></span>

- <span data-ttu-id="e16bc-138">**拖放文字編輯**。</span><span class="sxs-lookup"><span data-stu-id="e16bc-138">**Drag and drop text editing**.</span></span> <span data-ttu-id="e16bc-139">您可以選取某區塊的文字，並將它拖曳至另一個位置來移動它。</span><span class="sxs-lookup"><span data-stu-id="e16bc-139">You can select a block of text and drag it to another location to move it.</span></span> <span data-ttu-id="e16bc-140">如果您在按住 Ctrl 鍵時拖曳選取的文字，則會進行複製，而不是移動。</span><span class="sxs-lookup"><span data-stu-id="e16bc-140">If you hold down the Ctrl key while you drag the selected text you copy instead of move.</span></span>

- <span data-ttu-id="e16bc-141">**剖析錯誤顯示**。</span><span class="sxs-lookup"><span data-stu-id="e16bc-141">**Parse error display**.</span></span> <span data-ttu-id="e16bc-142">當您輸入時，Windows PowerShell 會檢查您的指令碼。</span><span class="sxs-lookup"><span data-stu-id="e16bc-142">Windows PowerShell examines your script as you type.</span></span> <span data-ttu-id="e16bc-143">如果它偵測到錯誤，則會在違規程式碼下顯示紅色曲線。</span><span class="sxs-lookup"><span data-stu-id="e16bc-143">If it detects an error, it shows a red squiggle under the offending code.</span></span> <span data-ttu-id="e16bc-144">暫留於指示的錯誤時，工具提示會顯示發現的問題。</span><span class="sxs-lookup"><span data-stu-id="e16bc-144">When you hover over the indicated error, a tooltip shows you the problem that was found.</span></span>

- <span data-ttu-id="e16bc-145">**縮放**。</span><span class="sxs-lookup"><span data-stu-id="e16bc-145">**Zoom**.</span></span> <span data-ttu-id="e16bc-146">您可以使用 ISE 視窗右下角的滑桿來放大文字以輕鬆地讀取，或縮小來查看較大的圖片。</span><span class="sxs-lookup"><span data-stu-id="e16bc-146">You can zoom in on your text to make it easier to read or zoom out to see the bigger picture by using the slider in the bottom-right corner of the ISE window.</span></span>

- <span data-ttu-id="e16bc-147">**RTF 複製與貼上**。</span><span class="sxs-lookup"><span data-stu-id="e16bc-147">**Rich text copy and paste**.</span></span> <span data-ttu-id="e16bc-148">從 ISE 複製到剪貼簿時，會包括所選取文字的字型、大小和色彩資訊。</span><span class="sxs-lookup"><span data-stu-id="e16bc-148">When you copy from the ISE to the clipboard, the font, size, and color information of the selected text is included.</span></span>

- <span data-ttu-id="e16bc-149">**區塊選擇**。</span><span class="sxs-lookup"><span data-stu-id="e16bc-149">**Block selection**.</span></span> <span data-ttu-id="e16bc-150">在使用滑鼠選取指令碼窗格中的文字時按住 ALT 鍵或按 **Alt+Shift+方向鍵**，就可以選取一個區塊形狀的文字區塊。</span><span class="sxs-lookup"><span data-stu-id="e16bc-150">You can select a block-shaped chunk of text by holding down the ALT key while selecting text in the script pane with your mouse, or by pressing **Alt+Shift+Arrow**.</span></span>

### <a name="added-in-powershell-20-windows-server-2008-r2-windows-7"></a><span data-ttu-id="e16bc-151">PowerShell 2.0 的新功能 (Windows Server 2008 R2、Windows 7)</span><span class="sxs-lookup"><span data-stu-id="e16bc-151">Added in PowerShell 2.0 (Windows Server 2008 R2, Windows 7)</span></span>

<span data-ttu-id="e16bc-152">ISE 是在 PowerShell 2.0 版引進。</span><span class="sxs-lookup"><span data-stu-id="e16bc-152">The ISE was introduced with PowerShell v2.0.</span></span>

## <a name="requirements-for-running-the-windows-powershell-ise"></a><span data-ttu-id="e16bc-153">Windows PowerShell ISE 的執行需求</span><span class="sxs-lookup"><span data-stu-id="e16bc-153">Requirements for running the Windows PowerShell ISE</span></span>

<span data-ttu-id="e16bc-154">ISE 可以在任何可執行 Windows PowerShell 2.0 版或更新版本的 Windows 電腦上使用。</span><span class="sxs-lookup"><span data-stu-id="e16bc-154">The ISE is available on any Windows computer that can run Windows PowerShell v2.0 or later.</span></span> <span data-ttu-id="e16bc-155">每個版本的 Windows 和 Windows Server 都包括某個版本的 Windows PowerShell 和 ISE，但您可以安裝 Windows Management Framework (WMF) 來升級到最新可用版本。</span><span class="sxs-lookup"><span data-stu-id="e16bc-155">Each version of Windows and Windows Server includes a version of Windows PowerShell and the ISE, but you can upgrade to the latest available by installing the Windows Management Framework (WMF).</span></span> <span data-ttu-id="e16bc-156">如需詳細資訊，請參閱 [WMF](/powershell/wmf) 文件。</span><span class="sxs-lookup"><span data-stu-id="e16bc-156">See the [WMF](/powershell/wmf) documentation for more information.</span></span>

> [!NOTE]
> <span data-ttu-id="e16bc-157">因為 Windows PowerShell ISE 需要圖形化使用者介面，所以無法在 Windows Server 的 Server Core 選項上執行它。</span><span class="sxs-lookup"><span data-stu-id="e16bc-157">Because Windows PowerShell ISE requires a graphical user interface, you can’t run it on the Server Core option of Windows Server.</span></span>

## <a name="see-also"></a><span data-ttu-id="e16bc-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e16bc-158">See also</span></span>

[<span data-ttu-id="e16bc-159">Windows PowerShell ISE 指令碼物件模型的用途</span><span class="sxs-lookup"><span data-stu-id="e16bc-159">Purpose of the windows power shell ise scripting object model</span></span>](../../core-powershell/ise/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)