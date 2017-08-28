---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "如何在 Windows PowerShell ISE 中撰寫和執行指令碼"
ms.assetid: 62f916d9-b3a1-484a-bdfb-41f57112c22b
ms.openlocfilehash: 871a4b6f4575af4f823a6957dc971335497320a4
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2017
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a><span data-ttu-id="b3fcb-103">如何在 Windows PowerShell ISE 中撰寫和執行指令碼</span><span class="sxs-lookup"><span data-stu-id="b3fcb-103">How to Write and Run Scripts in the Windows PowerShell ISE</span></span>
<span data-ttu-id="b3fcb-104">本主題說明如何在指令碼窗格中建立、編輯、執行和儲存指令碼。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-104">This topic describes how to create, edit, run, and save scripts in the Script Pane.</span></span>

-   [<span data-ttu-id="b3fcb-105">如何建立及執行指令碼</span><span class="sxs-lookup"><span data-stu-id="b3fcb-105">How to create and run scripts</span></span>](#bkmk_1)

-   [<span data-ttu-id="b3fcb-106">如何在指令碼窗格中撰寫及編輯文字</span><span class="sxs-lookup"><span data-stu-id="b3fcb-106">How to write and edit text in the Script Pane</span></span>](#bkmk_2)

-   [<span data-ttu-id="b3fcb-107">如何儲存指令碼</span><span class="sxs-lookup"><span data-stu-id="b3fcb-107">How to save a script</span></span>](#bkmk_3)

## <span data-ttu-id="b3fcb-108"><a name="bkmk_1"></a>如何建立和執行指令碼</span><span class="sxs-lookup"><span data-stu-id="b3fcb-108"><a name="bkmk_1"></a>How to create and run scripts</span></span>
<span data-ttu-id="b3fcb-109">您可以在指令碼窗格中開啟和編輯 Windows PowerShell® 檔案。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-109">You can open and edit Windows PowerShell® files in the Script Pane.</span></span> <span data-ttu-id="b3fcb-110">Windows PowerShell® 中需要注意的特定檔案類型包括指令碼檔案 (.ps1)、指令碼資料檔案 (.psd1) 和指令碼模組檔案 (.psm1)。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-110">Specific file types of interest in Windows PowerShell® are script files (.ps1), script data files (.psd1), and script module files (.psm1).</span></span> <span data-ttu-id="b3fcb-111">這些檔案類型是指令碼窗格編輯器中著色的語法。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-111">These file types are syntax colored in the Script Pane editor.</span></span> <span data-ttu-id="b3fcb-112">其他可在指令碼窗格中開啟的常見檔案類型還包括組態檔 (.ps1xml)、XML 檔案和文字檔。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-112">Other common file types you may open in the Script Pane are configuration files (.ps1xml), XML files, and text files.</span></span>

> [!NOTE]
> <span data-ttu-id="b3fcb-113">Windows PowerShell 執行原則會決定您是否可以執行指令碼，以及載入 Windows PowerShell 設定檔和組態檔。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-113">The Windows PowerShell execution policy determines whether you can run scripts and load Windows PowerShell profiles and configuration files.</span></span> <span data-ttu-id="b3fcb-114">預設執行原則 “Restricted” 可防止所有指令碼執行，並防止載入設定檔。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-114">The default execution policy, Restricted, prevents all scripts from running, and prevents loading profiles.</span></span> <span data-ttu-id="b3fcb-115">若要變更執行原則以允許載入及使用設定檔，請參閱 [Set-ExecutionPolicy[PSITPro5_Security]](https://technet.microsoft.com/en-us/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) 和 [about_Signing [v4]](https://technet.microsoft.com/en-us/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d)。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-115">To change the execution policy to allow profiles to load and be used, see [Set-ExecutionPolicy[PSITPro5_Security]](https://technet.microsoft.com/en-us/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) and [about_Signing [v4]](https://technet.microsoft.com/en-us/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d).</span></span>

### <a name="to-create-a-new-script-file"></a><span data-ttu-id="b3fcb-116">建立新的指令碼檔案</span><span class="sxs-lookup"><span data-stu-id="b3fcb-116">To create a new script file</span></span>
<span data-ttu-id="b3fcb-117">按一下工具列中的 **[新增]**，或在 **[檔案]** 功能表上，按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-117">On the toolbar, click **New** , or on the **File** menu, click **New**.</span></span> <span data-ttu-id="b3fcb-118">建立的檔案會顯示在目前 PowerShell 索引標籤下新的檔案索引標籤中。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-118">The created file appears in a new file tab under the current PowerShell tab.</span></span> <span data-ttu-id="b3fcb-119">請記住，只有在有多個 PowerShell 索引標籤時，才會顯示 PowerShell 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-119">Remember that the PowerShell tabs are only visible when there are more than one.</span></span> <span data-ttu-id="b3fcb-120">預設會建立指令碼類型的檔案 (.ps1)，但您可以使用新名稱和副檔名來儲存這個檔案。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-120">By default a file of type script (.ps1) is created, but it can be saved with a new name and extension.</span></span> <span data-ttu-id="b3fcb-121">在同一個 PowerShell 索引標籤中，可以建立多個指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-121">Multiple script files can be created in the same PowerShell tab.</span></span>

### <a name="to-open-an-existing-script"></a><span data-ttu-id="b3fcb-122">開啟現有的指令碼</span><span class="sxs-lookup"><span data-stu-id="b3fcb-122">To open an existing script</span></span>
<span data-ttu-id="b3fcb-123">按一下工具列中的 **[開啟...]**，或在 **[檔案]** 功能表上，按一下 **[開啟]**。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-123">On the toolbar, click **Open…**, or on the **File** menu, click **Open**.</span></span> <span data-ttu-id="b3fcb-124">在 **[開啟]** 對話方塊中，選取您要開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-124">In the **Open** dialog box, select the file you want to open.</span></span> <span data-ttu-id="b3fcb-125">開啟的檔案會顯示在新的索引標籤中。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-125">The opened file appears in a new tab.</span></span>

### <a name="to-close-a-script-tab"></a><span data-ttu-id="b3fcb-126">關閉指令碼索引標籤</span><span class="sxs-lookup"><span data-stu-id="b3fcb-126">To close a script tab</span></span>
<span data-ttu-id="b3fcb-127">按一下您要關閉之指令碼的指令碼索引標籤，然後執行下列其中一個動作︰</span><span class="sxs-lookup"><span data-stu-id="b3fcb-127">Click the script tab of the script you want to close, then do one of the following:</span></span>

1.  <span data-ttu-id="b3fcb-128">在 [指令碼] 索引標籤上，按一下**關閉**圖示 (X)。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-128">Click the **Close** icon (X) on the script tab.</span></span>

2.  <span data-ttu-id="b3fcb-129">在 **[檔案]** 功能表上，按一下 **[關閉]**。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-129">On the **File** menu, click **Close**.</span></span>

<span data-ttu-id="b3fcb-130">如果檔案自上次儲存後已變更，系統會提示您儲存或捨棄檔案。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-130">If the file has been altered since it was last saved, you are prompted to save or discard it.</span></span>

### <a name="to-display-the-file-path"></a><span data-ttu-id="b3fcb-131">顯示檔案路徑</span><span class="sxs-lookup"><span data-stu-id="b3fcb-131">To display the file path</span></span>
<span data-ttu-id="b3fcb-132">在 [檔案] 索引標籤上，指向檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-132">On the file tab, point to the file name.</span></span> <span data-ttu-id="b3fcb-133">指令碼檔案的完整路徑會顯示在工具提示中。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-133">The fully qualified path to the script file appears in a tooltip.</span></span>

### <a name="to-run-a-script"></a><span data-ttu-id="b3fcb-134">執行指令碼</span><span class="sxs-lookup"><span data-stu-id="b3fcb-134">To run a script</span></span>
<span data-ttu-id="b3fcb-135">按一下工具列中的 **[執行指令檔]**，或在 **[檔案]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-135">On the toolbar, click **Run Script**, or on the **File** menu, click **Run**.</span></span>

### <a name="to-run-a-portion-of-a-script"></a><span data-ttu-id="b3fcb-136">執行部分指令碼</span><span class="sxs-lookup"><span data-stu-id="b3fcb-136">To run a portion of a script</span></span>

1.  <span data-ttu-id="b3fcb-137">在指令碼窗格中，選取部分指令碼。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-137">In the Script Pane, select a portion of a script.</span></span>

2.  <span data-ttu-id="b3fcb-138">在 **[檔案]** 功能表上，按一下 **[執行選取項目]**，或按一下工具列中的 **[執行選取項目]**。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-138">On the **File** menu, click **Run Selection**, or on the toolbar, click **Run Selection**.</span></span>

### <a name="to-stop-a-running-script"></a><span data-ttu-id="b3fcb-139">停止執行中的指令碼</span><span class="sxs-lookup"><span data-stu-id="b3fcb-139">To stop a running script</span></span>
<span data-ttu-id="b3fcb-140">請執行下列其中一個動作︰按一下工具列中的 [停止操作]、按 CTRL+BREAK、在 [檔案] 功能表上，按一下 [停止操作]。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-140">On the toolbar, click **Stop Operation**, press CTRL+BREAK, or on the **File** menu, click **Stop Operation**.</span></span> <span data-ttu-id="b3fcb-141">除非目前已選取一些文字，否則按 **CTRL+C** 也適用；如果已選取文字，**CTRL+C** 會對應至選取文字的複製功能。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-141">Pressing **CTRL+C** also works unless some text is currently selected, in which case **CTRL+C** maps to the copy function for the selected text.</span></span>

## <span data-ttu-id="b3fcb-142"><a name="bkmk_2"></a>如何在指令碼窗格中撰寫和編輯文字</span><span class="sxs-lookup"><span data-stu-id="b3fcb-142"><a name="bkmk_2"></a>How to write and edit text in the Script Pane</span></span>
<span data-ttu-id="b3fcb-143">使用下列步驟在指令碼窗格中編輯文字。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-143">Use the following steps to edit text in the Script Pane.</span></span> <span data-ttu-id="b3fcb-144">您可以複製、剪下、貼上、尋找和取代文字。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-144">You can copy, cut, paste, find, and replace text.</span></span> <span data-ttu-id="b3fcb-145">您也可以復原和取消復原剛才執行的上一個動作。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-145">You can also undo and redo the last action you just performed.</span></span> <span data-ttu-id="b3fcb-146">執行這些動作的鍵盤快速鍵與所有 Windows 應用程式所使用的鍵盤快速鍵相同。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-146">The keyboard shortcuts for performing these actions are the same as those used for all Windows applications.</span></span>

### <a name="to-enter-text-in-the-script-pane"></a><span data-ttu-id="b3fcb-147">在指令碼窗格中輸入文字</span><span class="sxs-lookup"><span data-stu-id="b3fcb-147">To enter text in the Script Pane</span></span>

1.  <span data-ttu-id="b3fcb-148">將游標移至指令碼窗格，方法是按一下指令碼窗格中的任何位置，或按一下 **[檢視]** 功能表中的 **[移至指令碼窗格]**。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-148">Move the cursor to the Script Pane by clicking anywhere in the Script Pane, or by clicking **Go to Script Pane** in the **View** menu.</span></span>

2.  <span data-ttu-id="b3fcb-149">建立指令碼。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-149">Create a script.</span></span> <span data-ttu-id="b3fcb-150">語法著色和 TAB 鍵自動完成可讓 Windows PowerShell ISE 的使用體驗更豐富。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-150">Syntax coloring and tab completion make this a richer experience in Windows PowerShell ISE.</span></span>

3.  <span data-ttu-id="b3fcb-151">如需使用 TAB 鍵自動完成功能以協助輸入的詳細資訊，請參閱[如何在指令碼窗格和主控台窗格中使用 TAB 鍵自動完成](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md)。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-151">See [How to Use Tab Completion in the Script Pane and Console Pane](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) for details about using the tab completion feature to help in typing.</span></span>

### <a name="to-find-text-in-the-script-pane"></a><span data-ttu-id="b3fcb-152">在指令碼窗格中尋找文字</span><span class="sxs-lookup"><span data-stu-id="b3fcb-152">To find text in the Script Pane</span></span>

1.  <span data-ttu-id="b3fcb-153">若要尋找任何位置的文字，按 **CTRL+F**，或在 [編輯] 功能表上，按一下 [在指令碼中尋找]。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-153">To find text anywhere, press **CTRL+F** or, on the **Edit** menu, click **Find in Script**.</span></span>

2.  <span data-ttu-id="b3fcb-154">若要尋找游標後的文字，請按 **F3** 鍵，或在 **[編輯]** 功能表上，按一下 **[在指令碼中找下一個]**。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-154">To find text after the cursor, press **F3** or, on the **Edit** menu, click **Find Next in Script**.</span></span>

3.  <span data-ttu-id="b3fcb-155">若要尋找游標之前的文字，按 **SHIFT+F3**，或在 [編輯] 功能表上，按一下 [在指令碼中找上一個]。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-155">To find text before the cursor, press **SHIFT+F3** or, on the **Edit** menu, click **Find Previous in Script**.</span></span>

### <a name="to-find-and-replace-text-in-the-script-pane"></a><span data-ttu-id="b3fcb-156">在指令碼窗格中尋找和取代文字</span><span class="sxs-lookup"><span data-stu-id="b3fcb-156">To find and replace text in the Script Pane</span></span>
<span data-ttu-id="b3fcb-157">按 **CRTL+H**，或在 [編輯] 功能表上，按一下 [在指令碼中取代]。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-157">Press **CRTL+H** or, on the **Edit** menu, click **Replace in Script**.</span></span> <span data-ttu-id="b3fcb-158">輸入您要尋找的文字和用來取代的文字，然後按 **ENTER** 鍵。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-158">Enter both the text you want to find and the text with which you want to replace it, and then press **ENTER**.</span></span>

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a><span data-ttu-id="b3fcb-159">在指令碼窗格中移至特定文字行</span><span class="sxs-lookup"><span data-stu-id="b3fcb-159">To go to a particular line of text in the Script Pane</span></span>

1.  <span data-ttu-id="b3fcb-160">在指令碼窗格中，按 **CTRL+G**，或在 [編輯] 功能表上，按一下 [移至行]。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-160">In the Script Pane, press **CTRL+G** or, on the **Edit** menu, click **Go to Line**.</span></span>

2.  <span data-ttu-id="b3fcb-161">輸入行號。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-161">Enter a line number.</span></span>

### <a name="to-copy-text-in-the-script-pane"></a><span data-ttu-id="b3fcb-162">在指令碼窗格中複製文字</span><span class="sxs-lookup"><span data-stu-id="b3fcb-162">To copy text in the Script Pane</span></span>

1.  <span data-ttu-id="b3fcb-163">在指令碼窗格中，選取您要複製的文字。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-163">In the Script Pane, select the text that you want to copy.</span></span>

2.  <span data-ttu-id="b3fcb-164">按 **CTRL+C**；按一下工具列中的複製圖示；或者在 [編輯] 功能表上，按一下 [複製]。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-164">Press **CTRL+C** or, on the toolbar, click the **Copy** icon, or on the **Edit** menu, click **Copy**.</span></span>

### <a name="to-cut-text-in-the-script-pane"></a><span data-ttu-id="b3fcb-165">在指令碼窗格中剪下文字</span><span class="sxs-lookup"><span data-stu-id="b3fcb-165">To cut text in the Script Pane</span></span>

1.  <span data-ttu-id="b3fcb-166">在指令碼窗格中，選取您要剪下的文字。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-166">In the Script Pane, select the text that you want to cut.</span></span>

2.  <span data-ttu-id="b3fcb-167">按 **CTRL+X**；按一下工具列中的剪下圖示；或者在 [編輯] 功能表上，按一下 [剪下]。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-167">Press **CTRL+X** or, on the toolbar, click the **Cut** icon, or on the **Edit** menu, click **Cut**.</span></span>

### <a name="to-paste-text-into-the-script-pane"></a><span data-ttu-id="b3fcb-168">在指令碼窗格中貼上文字</span><span class="sxs-lookup"><span data-stu-id="b3fcb-168">To paste text into the Script Pane</span></span>
<span data-ttu-id="b3fcb-169">按 **CTRL+V**；按一下工具列中的貼上圖示；或者在 [編輯] 功能表上，按一下 [貼上]。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-169">Press **CTRL+V** or, on the toolbar, click the **Paste** icon, or on the **Edit** menu, click **Paste**.</span></span>

### <a name="to-undo-an-action-in-the-script-pane"></a><span data-ttu-id="b3fcb-170">在指令碼窗格中復原動作</span><span class="sxs-lookup"><span data-stu-id="b3fcb-170">To undo an action in the Script Pane</span></span>
<span data-ttu-id="b3fcb-171">按 **CTRL+Z**；按一下工具列中的復原圖示；或者在 [編輯] 功能表上，按一下 [復原]。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-171">Press **CTRL+Z** or, on the toolbar, click the **Undo** icon, or on the **Edit** menu, click **Undo**.</span></span>

### <a name="to-redo-an-action-in-the-script-pane"></a><span data-ttu-id="b3fcb-172">在指令碼窗格中取消復原動作</span><span class="sxs-lookup"><span data-stu-id="b3fcb-172">To redo an action in the Script Pane</span></span>
<span data-ttu-id="b3fcb-173">按 **CTRL+Y**；按一下工具列中的取消復原圖示；或者在 [編輯] 功能表上，按一下 [取消復原]。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-173">Press **CTRL+Y** or, on the toolbar, click the **Redo** icon, or on the **Edit** menu, click **Redo**.</span></span>

## <span data-ttu-id="b3fcb-174"><a name="bkmk_3"></a>如何儲存指令碼</span><span class="sxs-lookup"><span data-stu-id="b3fcb-174"><a name="bkmk_3"></a>How to save a script</span></span>
<span data-ttu-id="b3fcb-175">使用下列步驟儲存並命名指令碼。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-175">Use the following steps to save and name a script.</span></span> <span data-ttu-id="b3fcb-176">指令碼名稱旁若出現星號，表示檔案自變更後尚未儲存。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-176">An asterisk appears next to the script name to mark a file that has not been saved since it was altered.</span></span> <span data-ttu-id="b3fcb-177">儲存檔案之後，星號就會消失。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-177">The asterisk disappears when the file is saved.</span></span>

### <a name="to-save-a-script"></a><span data-ttu-id="b3fcb-178">儲存指令碼</span><span class="sxs-lookup"><span data-stu-id="b3fcb-178">To save a script</span></span>
<span data-ttu-id="b3fcb-179">按 **CTRL+S**；按一下工具列中的儲存圖示；或者在 [檔案] 功能表上，按一下 [儲存]。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-179">Press **CTRL+S** or, on the toolbar, click the **Save** icon, or on the **File** menu, click **Save**.</span></span>

### <a name="to-save-and-name-a-script"></a><span data-ttu-id="b3fcb-180">儲存並命名指令碼</span><span class="sxs-lookup"><span data-stu-id="b3fcb-180">To save and name a script</span></span>

1.  <span data-ttu-id="b3fcb-181">在 **[檔案]** 功能表上，按一下 **[另存新檔]**。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-181">On the **File** menu, click **Save As**.</span></span> <span data-ttu-id="b3fcb-182">**[另存新檔]** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-182">The **Save As** dialog box will appear.</span></span>

2.  <span data-ttu-id="b3fcb-183">在 **[檔案名稱]** 方塊中，輸入檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-183">In the **File name** box, enter a name for the file.</span></span>

3.  <span data-ttu-id="b3fcb-184">在 **[檔案類型]** 方塊中，選取檔案類型。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-184">In the **Save as type** box, select a file type.</span></span> <span data-ttu-id="b3fcb-185">例如，在 [檔案類型] 方塊中，選取 [PowerShell 指令碼 (\* .ps1)]。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-185">For example, in the **Save as type** box, select “PowerShell Scripts (\* .ps1)”.</span></span>

4.  <span data-ttu-id="b3fcb-186">按一下 **[儲存]**。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-186">Click **Save**.</span></span>

### <a name="to-save-a-script-in-ascii-encoding"></a><span data-ttu-id="b3fcb-187">以 ASCII 編碼方式儲存指令碼</span><span class="sxs-lookup"><span data-stu-id="b3fcb-187">To save a script in ASCII encoding</span></span>
<span data-ttu-id="b3fcb-188">根據預設，Windows PowerShell ISE 會以 Unicode (BigEndianUnicode) 格式儲存新的指令碼檔案 (.ps1)、指令碼資料檔案 (.psd1) 和指令碼模組檔案 (.psm1)。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-188">By default, Windows PowerShell ISE saves new script files (.ps1), script data files (.psd1), and script module files (.psm1) as Unicode (BigEndianUnicode) by default.</span></span> <span data-ttu-id="b3fcb-189">若要以 ASCII (ANSI) 等其他編碼方式儲存指令碼，請在 [$psISE.CurrentFile](https://technet.microsoft.com/en-us/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile) 物件上使用 **Save** 或 **SaveAs** 方法。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-189">To save a script in another encoding, such as ASCII (ANSI), use the **Save** or **SaveAs** methods on the [$psISE.CurrentFile](https://technet.microsoft.com/en-us/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile) object.</span></span>

<span data-ttu-id="b3fcb-190">下列命令會以 ASCII 編碼方式，將新的指令碼另存為 MyScript.ps1。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-190">The following command saves a new script as MyScript.ps1 with ASCII encoding.</span></span>

```
$psise.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

<span data-ttu-id="b3fcb-191">下列命令會以同名但使用 ASCII 編碼方式的檔案，取代目前的指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-191">The following command replaces the current script file with a file with the same name, but with ASCII encoding.</span></span>

```
$psise.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

<span data-ttu-id="b3fcb-192">下列命令會取得目前檔案的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-192">The following command gets the encoding of the current file.</span></span>

```
$psise.CurrentFile.encoding
```

<span data-ttu-id="b3fcb-193">Windows PowerShell ISE 支援下列編碼選項︰ASCII、BigEndianUnicode、Unicode、UTF32、UTF7、UTF8 和預設值。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-193">Windows PowerShell ISE supports the following encoding options: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 and Default.</span></span> <span data-ttu-id="b3fcb-194">預設選項的值會因系統而異。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-194">The value of the Default option varies with the system.</span></span>

<span data-ttu-id="b3fcb-195">Windows PowerShell ISE 不會變更以其他編輯器建立之指令碼的編碼方式，即使在 Windows PowerShell ISE 中使用 [儲存] 或 [另存新檔] 命令亦然。</span><span class="sxs-lookup"><span data-stu-id="b3fcb-195">Windows PowerShell ISE does not change the encoding of scripts that were created by in other editors, even when you use the Save or Save As commands in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="b3fcb-196">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3fcb-196">See Also</span></span>
- [<span data-ttu-id="b3fcb-197">使用 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="b3fcb-197">Using the Windows PowerShell ISE</span></span>](Using-the-Windows-PowerShell-ISE.md)
