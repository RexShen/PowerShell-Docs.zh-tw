---
description: PSReadLine 在 PowerShell 主控台中提供改良的命令列編輯體驗。
keywords: powershell
Locale: en-US
ms.date: 02/10/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 關於 PSReadLine
ms.openlocfilehash: 5b59ffcdfb35c2aa10f8e0caf3a3b365c5bcf93e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208132"
---
# <a name="psreadline"></a><span data-ttu-id="68707-104">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="68707-104">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="68707-105">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="68707-105">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="68707-106">簡短描述</span><span class="sxs-lookup"><span data-stu-id="68707-106">SHORT DESCRIPTION</span></span>

<span data-ttu-id="68707-107">PSReadLine 在 PowerShell 主控台中提供改良的命令列編輯體驗。</span><span class="sxs-lookup"><span data-stu-id="68707-107">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="68707-108">詳細描述</span><span class="sxs-lookup"><span data-stu-id="68707-108">LONG DESCRIPTION</span></span>

<span data-ttu-id="68707-109">PSReadLine 2.0 為 PowerShell 主控台提供功能強大的命令列編輯體驗。</span><span class="sxs-lookup"><span data-stu-id="68707-109">PSReadLine 2.0 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="68707-110">它提供：</span><span class="sxs-lookup"><span data-stu-id="68707-110">It provides:</span></span>

- <span data-ttu-id="68707-111">命令列的語法著色</span><span class="sxs-lookup"><span data-stu-id="68707-111">Syntax coloring of the command line</span></span>
- <span data-ttu-id="68707-112">語法錯誤的視覺指示</span><span class="sxs-lookup"><span data-stu-id="68707-112">A visual indication of syntax errors</span></span>
- <span data-ttu-id="68707-113"> (編輯和歷程記錄的更佳多行體驗) </span><span class="sxs-lookup"><span data-stu-id="68707-113">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="68707-114">可自訂的按鍵系結</span><span class="sxs-lookup"><span data-stu-id="68707-114">Customizable key bindings</span></span>
- <span data-ttu-id="68707-115">Cmd 和 Emacs 模式</span><span class="sxs-lookup"><span data-stu-id="68707-115">Cmd and Emacs modes</span></span>
- <span data-ttu-id="68707-116">許多設定選項</span><span class="sxs-lookup"><span data-stu-id="68707-116">Many configuration options</span></span>
- <span data-ttu-id="68707-117">Bash 樣式完成 (在 Cmd 模式中為選擇性，預設為 Emacs 模式) </span><span class="sxs-lookup"><span data-stu-id="68707-117">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="68707-118">Emacs yank/kill-環形</span><span class="sxs-lookup"><span data-stu-id="68707-118">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="68707-119">以 PowerShell 權杖為基礎的「單字」移動和終止</span><span class="sxs-lookup"><span data-stu-id="68707-119">PowerShell token based "word" movement and kill</span></span>

<span data-ttu-id="68707-120">下列函式可在類別 **[PSConsoleReadLine]** 中使用。</span><span class="sxs-lookup"><span data-stu-id="68707-120">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]** .</span></span>

> [!NOTE]
> <span data-ttu-id="68707-121">從 PowerShell 7.0 開始，如果偵測到螢幕讀取程式，PowerShell 會略過在 Windows 上自動載入 PSReadLine。</span><span class="sxs-lookup"><span data-stu-id="68707-121">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="68707-122">PSReadLine 目前無法與螢幕讀取器順利搭配運作。</span><span class="sxs-lookup"><span data-stu-id="68707-122">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="68707-123">Windows 上 PowerShell 7.0 的預設轉譯和格式可正常運作。</span><span class="sxs-lookup"><span data-stu-id="68707-123">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="68707-124">如有必要，您可以手動載入模組。</span><span class="sxs-lookup"><span data-stu-id="68707-124">You can manually load the module if necessary.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="68707-125">基本編輯函數</span><span class="sxs-lookup"><span data-stu-id="68707-125">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="68707-126">中止</span><span class="sxs-lookup"><span data-stu-id="68707-126">Abort</span></span>

<span data-ttu-id="68707-127">中止目前的動作，例如累加式歷程記錄搜尋。</span><span class="sxs-lookup"><span data-stu-id="68707-127">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="68707-128">Emacs： `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="68707-128">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="68707-129">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="68707-129">AcceptAndGetNext</span></span>

<span data-ttu-id="68707-130">嘗試執行目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="68707-130">Attempt to execute the current input.</span></span> <span data-ttu-id="68707-131">如果可以像 AcceptLine) 一樣執行 (，則會在下一次呼叫 ReadLine 時，重新叫用歷程記錄中的下一個專案。</span><span class="sxs-lookup"><span data-stu-id="68707-131">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="68707-132">Emacs： `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="68707-132">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="68707-133">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="68707-133">AcceptLine</span></span>

<span data-ttu-id="68707-134">嘗試執行目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="68707-134">Attempt to execute the current input.</span></span> <span data-ttu-id="68707-135">如果目前的輸入不完整 (例如遺漏右括弧、方括弧或引號，則接續提示會顯示在下一行，而 PSReadLine 會等候按鍵編輯目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="68707-135">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="68707-136">Cmd： `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="68707-136">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="68707-137">Emacs： `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="68707-137">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="68707-138">Vi 插入模式： `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="68707-138">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="68707-139">AddLine</span><span class="sxs-lookup"><span data-stu-id="68707-139">AddLine</span></span>

<span data-ttu-id="68707-140">接續提示會顯示在下一行，而 PSReadLine 會等候按鍵編輯目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="68707-140">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="68707-141">這對於將多行輸入輸入為單一命令很有用，即使單一行本身已完成輸入也是一樣。</span><span class="sxs-lookup"><span data-stu-id="68707-141">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="68707-142">Cmd： `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="68707-142">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="68707-143">Emacs： `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="68707-143">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="68707-144">Vi 插入模式： `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="68707-144">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="68707-145">Vi 命令模式： `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="68707-145">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="68707-146">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="68707-146">BackwardDeleteChar</span></span>

<span data-ttu-id="68707-147">刪除游標之前的字元。</span><span class="sxs-lookup"><span data-stu-id="68707-147">Delete the character before the cursor.</span></span>

- <span data-ttu-id="68707-148">Cmd： `<Backspace>` ， `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="68707-148">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="68707-149">Emacs： `<Backspace>` 、 `<Ctrl+Backspace>` 、 `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="68707-149">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="68707-150">Vi 插入模式： `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="68707-150">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="68707-151">Vi 命令模式： `<X>` 、 `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="68707-151">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="68707-152">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="68707-152">BackwardDeleteLine</span></span>

<span data-ttu-id="68707-153">如同 BackwardKillLine-刪除從點到行首的文字，但不會將已刪除的文字放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="68707-153">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="68707-154">Cmd： `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="68707-154">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="68707-155">Vi 插入模式： `<Ctrl+u>` 、 `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="68707-155">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="68707-156">Vi 命令模式： `<Ctrl+u>` 、 `<Ctrl+Home>` 、 `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="68707-156">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`, `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="68707-157">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="68707-157">BackwardDeleteWord</span></span>

<span data-ttu-id="68707-158">刪除上一個字組。</span><span class="sxs-lookup"><span data-stu-id="68707-158">Deletes the previous word.</span></span>

- <span data-ttu-id="68707-159">Vi 命令模式： `<Ctrl+w>` 、 `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="68707-159">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="68707-160">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="68707-160">BackwardKillLine</span></span>

<span data-ttu-id="68707-161">清除輸入至資料指標開頭的輸入。</span><span class="sxs-lookup"><span data-stu-id="68707-161">Clear the input from the start of the input to the cursor.</span></span> <span data-ttu-id="68707-162">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="68707-162">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="68707-163">Emacs： `<Ctrl+u>` ， `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="68707-163">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="68707-164">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="68707-164">BackwardKillWord</span></span>

<span data-ttu-id="68707-165">清除從目前單字開頭到游標處的輸入。</span><span class="sxs-lookup"><span data-stu-id="68707-165">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="68707-166">如果游標在單字之間，則會從上一個單字開頭開始清除輸入至游標。</span><span class="sxs-lookup"><span data-stu-id="68707-166">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="68707-167">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="68707-167">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="68707-168">Cmd： `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="68707-168">Cmd: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="68707-169">Emacs： `<Alt+Backspace>` ， `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="68707-169">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="68707-170">Vi 插入模式： `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="68707-170">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="68707-171">Vi 命令模式： `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="68707-171">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="68707-172">CancelLine</span><span class="sxs-lookup"><span data-stu-id="68707-172">CancelLine</span></span>

<span data-ttu-id="68707-173">取消目前的輸入，將輸入保留在畫面上，但返回主機，以便再次評估提示。</span><span class="sxs-lookup"><span data-stu-id="68707-173">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="68707-174">Vi 插入模式： `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="68707-174">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="68707-175">Vi 命令模式： `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="68707-175">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="68707-176">複製</span><span class="sxs-lookup"><span data-stu-id="68707-176">Copy</span></span>

<span data-ttu-id="68707-177">將選取的區域複製到系統剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="68707-177">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="68707-178">如果未選取任何區域，請複製整行。</span><span class="sxs-lookup"><span data-stu-id="68707-178">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="68707-179">Cmd： `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="68707-179">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="68707-180">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="68707-180">CopyOrCancelLine</span></span>

<span data-ttu-id="68707-181">如果已選取文字，請複製到剪貼簿，否則請取消該行。</span><span class="sxs-lookup"><span data-stu-id="68707-181">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="68707-182">Cmd： `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="68707-182">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="68707-183">Emacs： `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="68707-183">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="68707-184">剪下</span><span class="sxs-lookup"><span data-stu-id="68707-184">Cut</span></span>

<span data-ttu-id="68707-185">刪除選取的區域，將已刪除的文字放入系統剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="68707-185">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="68707-186">Cmd： `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="68707-186">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="68707-187">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="68707-187">DeleteChar</span></span>

<span data-ttu-id="68707-188">刪除游標下的字元。</span><span class="sxs-lookup"><span data-stu-id="68707-188">Delete the character under the cursor.</span></span>

- <span data-ttu-id="68707-189">Cmd： `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="68707-189">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="68707-190">Emacs： `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="68707-190">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="68707-191">Vi 插入模式： `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="68707-191">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="68707-192">Vi 命令模式： `<Delete>` 、 `<x>` 、 `<d,l>` 、 `<d,Space>`</span><span class="sxs-lookup"><span data-stu-id="68707-192">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Space>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="68707-193">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="68707-193">DeleteCharOrExit</span></span>

<span data-ttu-id="68707-194">刪除游標下的字元，如果行是空的，請結束進程。</span><span class="sxs-lookup"><span data-stu-id="68707-194">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="68707-195">Emacs： `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="68707-195">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="68707-196">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="68707-196">DeleteEndOfWord</span></span>

<span data-ttu-id="68707-197">刪除到字尾。</span><span class="sxs-lookup"><span data-stu-id="68707-197">Delete to the end of the word.</span></span>

- <span data-ttu-id="68707-198">Vi 命令模式： `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="68707-198">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="68707-199">DeleteLine</span><span class="sxs-lookup"><span data-stu-id="68707-199">DeleteLine</span></span>

<span data-ttu-id="68707-200">刪除目前的行，並啟用復原。</span><span class="sxs-lookup"><span data-stu-id="68707-200">Deletes the current line, enabling undo.</span></span>

- <span data-ttu-id="68707-201">Vi 命令模式： `<d,d>`</span><span class="sxs-lookup"><span data-stu-id="68707-201">Vi command mode: `<d,d>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="68707-202">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="68707-202">DeleteLineToFirstChar</span></span>

<span data-ttu-id="68707-203">將游標的文字刪除到行的第一個非空白字元。</span><span class="sxs-lookup"><span data-stu-id="68707-203">Deletes text from the cursor to the first non-blank character of the line.</span></span>

- <span data-ttu-id="68707-204">Vi 命令模式： `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="68707-204">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="68707-205">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="68707-205">DeleteToEnd</span></span>

<span data-ttu-id="68707-206">刪除至行尾。</span><span class="sxs-lookup"><span data-stu-id="68707-206">Delete to the end of the line.</span></span>

- <span data-ttu-id="68707-207">Vi 命令模式： `<D>` 、 `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="68707-207">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="68707-208">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="68707-208">DeleteWord</span></span>

<span data-ttu-id="68707-209">刪除下一個字組。</span><span class="sxs-lookup"><span data-stu-id="68707-209">Delete the next word.</span></span>

- <span data-ttu-id="68707-210">Vi 命令模式： `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="68707-210">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="68707-211">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="68707-211">ForwardDeleteLine</span></span>

<span data-ttu-id="68707-212">如同 ForwardKillLine-刪除從點到行尾的文字，但不會將已刪除的文字放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="68707-212">Like ForwardKillLine - deletes text from the point to the end of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="68707-213">Cmd： `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="68707-213">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="68707-214">Vi 插入模式： `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="68707-214">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="68707-215">Vi 命令模式： `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="68707-215">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="68707-216">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="68707-216">InsertLineAbove</span></span>

<span data-ttu-id="68707-217">無論游標位於目前的行上，都會在目前的行上方建立新的空白行。</span><span class="sxs-lookup"><span data-stu-id="68707-217">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="68707-218">游標移至新行的開頭。</span><span class="sxs-lookup"><span data-stu-id="68707-218">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="68707-219">Cmd： `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="68707-219">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="68707-220">InsertLineBelow</span><span class="sxs-lookup"><span data-stu-id="68707-220">InsertLineBelow</span></span>

<span data-ttu-id="68707-221">目前的行下方會建立新的空白行，而不論游標在目前的行上。</span><span class="sxs-lookup"><span data-stu-id="68707-221">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="68707-222">游標移至新行的開頭。</span><span class="sxs-lookup"><span data-stu-id="68707-222">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="68707-223">Cmd： `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="68707-223">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="68707-224">InvertCase</span><span class="sxs-lookup"><span data-stu-id="68707-224">InvertCase</span></span>

<span data-ttu-id="68707-225">將目前字元的大小寫反轉，並移至下一個字元。</span><span class="sxs-lookup"><span data-stu-id="68707-225">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="68707-226">Vi 命令模式： `<~>`</span><span class="sxs-lookup"><span data-stu-id="68707-226">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="68707-227">KillLine</span><span class="sxs-lookup"><span data-stu-id="68707-227">KillLine</span></span>

<span data-ttu-id="68707-228">清除游標至輸入結尾的輸入。</span><span class="sxs-lookup"><span data-stu-id="68707-228">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="68707-229">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="68707-229">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="68707-230">Emacs： `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="68707-230">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="68707-231">KillRegion</span><span class="sxs-lookup"><span data-stu-id="68707-231">KillRegion</span></span>

<span data-ttu-id="68707-232">終止游標與標記之間的文字。</span><span class="sxs-lookup"><span data-stu-id="68707-232">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="68707-233">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="68707-233">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="68707-234">KillWord</span><span class="sxs-lookup"><span data-stu-id="68707-234">KillWord</span></span>

<span data-ttu-id="68707-235">清除游標到目前單字結尾的輸入。</span><span class="sxs-lookup"><span data-stu-id="68707-235">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="68707-236">如果游標在單字之間，則會從資料指標清除輸入至下一個單字的結尾。</span><span class="sxs-lookup"><span data-stu-id="68707-236">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="68707-237">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="68707-237">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="68707-238">Cmd： `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="68707-238">Cmd: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="68707-239">Emacs： `<Alt+d>` ， `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="68707-239">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="68707-240">Vi 插入模式： `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="68707-240">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="68707-241">Vi 命令模式： `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="68707-241">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="68707-242">貼上</span><span class="sxs-lookup"><span data-stu-id="68707-242">Paste</span></span>

<span data-ttu-id="68707-243">貼上系統剪貼簿中的文字。</span><span class="sxs-lookup"><span data-stu-id="68707-243">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="68707-244">Cmd： `<Ctrl+v>` ， `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="68707-244">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="68707-245">Vi 插入模式： `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="68707-245">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="68707-246">Vi 命令模式： `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="68707-246">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="68707-247">使用 **Paste** 函式時，剪貼簿緩衝區的整個內容會貼到 PSReadLine 的輸入緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="68707-247">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="68707-248">輸入緩衝區接著會傳遞至 PowerShell 剖析器。</span><span class="sxs-lookup"><span data-stu-id="68707-248">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="68707-249">使用主控台應用程式的 **按右鍵** [貼上] 方法貼上的輸入會一次複製到輸入緩衝區一個字元。</span><span class="sxs-lookup"><span data-stu-id="68707-249">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="68707-250">當換行字元時，輸入緩衝區會傳遞給剖析器。</span><span class="sxs-lookup"><span data-stu-id="68707-250">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="68707-251">因此，輸入會一次剖析一行。</span><span class="sxs-lookup"><span data-stu-id="68707-251">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="68707-252">貼上方法之間的差異會導致不同的執行行為。</span><span class="sxs-lookup"><span data-stu-id="68707-252">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="68707-253">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="68707-253">PasteAfter</span></span>

<span data-ttu-id="68707-254">將剪貼簿貼到游標之後，將游標移至貼上文字的結尾。</span><span class="sxs-lookup"><span data-stu-id="68707-254">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="68707-255">Vi 命令模式： `<p>`</span><span class="sxs-lookup"><span data-stu-id="68707-255">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="68707-256">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="68707-256">PasteBefore</span></span>

<span data-ttu-id="68707-257">將剪貼簿貼到游標之前，將游標移至貼上文字的結尾。</span><span class="sxs-lookup"><span data-stu-id="68707-257">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="68707-258">Vi 命令模式： `<P>`</span><span class="sxs-lookup"><span data-stu-id="68707-258">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="68707-259">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="68707-259">PrependAndAccept</span></span>

<span data-ttu-id="68707-260">在前面加上 ' # ' 並接受該行。</span><span class="sxs-lookup"><span data-stu-id="68707-260">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="68707-261">Vi 命令模式： `<#>`</span><span class="sxs-lookup"><span data-stu-id="68707-261">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="68707-262">取消復原</span><span class="sxs-lookup"><span data-stu-id="68707-262">Redo</span></span>

<span data-ttu-id="68707-263">復原復原。</span><span class="sxs-lookup"><span data-stu-id="68707-263">Undo an undo.</span></span>

- <span data-ttu-id="68707-264">Cmd： `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="68707-264">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="68707-265">Vi 插入模式： `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="68707-265">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="68707-266">Vi 命令模式： `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="68707-266">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="68707-267">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="68707-267">RepeatLastCommand</span></span>

<span data-ttu-id="68707-268">重複上次修改文字。</span><span class="sxs-lookup"><span data-stu-id="68707-268">Repeat the last text modification.</span></span>

- <span data-ttu-id="68707-269">Vi 命令模式： `<.>`</span><span class="sxs-lookup"><span data-stu-id="68707-269">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="68707-270">RevertLine</span><span class="sxs-lookup"><span data-stu-id="68707-270">RevertLine</span></span>

<span data-ttu-id="68707-271">將所有輸入還原為目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="68707-271">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="68707-272">Cmd： `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="68707-272">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="68707-273">Emacs： `<Alt+r>` ， `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="68707-273">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="68707-274">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="68707-274">ShellBackwardKillWord</span></span>

<span data-ttu-id="68707-275">清除從目前單字開頭到游標處的輸入。</span><span class="sxs-lookup"><span data-stu-id="68707-275">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="68707-276">如果游標在單字之間，則會從上一個單字開頭開始清除輸入至游標。</span><span class="sxs-lookup"><span data-stu-id="68707-276">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="68707-277">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="68707-277">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="68707-278">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="68707-278">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="68707-279">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="68707-279">ShellKillWord</span></span>

<span data-ttu-id="68707-280">清除游標到目前單字結尾的輸入。</span><span class="sxs-lookup"><span data-stu-id="68707-280">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="68707-281">如果游標在單字之間，則會從資料指標清除輸入至下一個單字的結尾。</span><span class="sxs-lookup"><span data-stu-id="68707-281">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="68707-282">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="68707-282">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="68707-283">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="68707-283">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="68707-284">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="68707-284">SwapCharacters</span></span>

<span data-ttu-id="68707-285">交換目前的字元和前一個字元。</span><span class="sxs-lookup"><span data-stu-id="68707-285">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="68707-286">Emacs： `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="68707-286">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="68707-287">Vi 插入模式： `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="68707-287">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="68707-288">Vi 命令模式： `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="68707-288">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="68707-289">復原</span><span class="sxs-lookup"><span data-stu-id="68707-289">Undo</span></span>

<span data-ttu-id="68707-290">復原先前的編輯。</span><span class="sxs-lookup"><span data-stu-id="68707-290">Undo a previous edit.</span></span>

- <span data-ttu-id="68707-291">Cmd： `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="68707-291">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="68707-292">Emacs： `<Ctrl+_>` ， `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="68707-292">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="68707-293">Vi 插入模式： `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="68707-293">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="68707-294">Vi 命令模式： `<Ctrl+z>` 、 `<u>`</span><span class="sxs-lookup"><span data-stu-id="68707-294">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="68707-295">UndoAll</span><span class="sxs-lookup"><span data-stu-id="68707-295">UndoAll</span></span>

<span data-ttu-id="68707-296">復原所有先前編輯的行。</span><span class="sxs-lookup"><span data-stu-id="68707-296">Undo all previous edits for line.</span></span>

- <span data-ttu-id="68707-297">Vi 命令模式： `<U>`</span><span class="sxs-lookup"><span data-stu-id="68707-297">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="68707-298">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="68707-298">UnixWordRubout</span></span>

<span data-ttu-id="68707-299">清除從目前單字開頭到游標處的輸入。</span><span class="sxs-lookup"><span data-stu-id="68707-299">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="68707-300">如果游標在單字之間，則會從上一個單字開頭開始清除輸入至游標。</span><span class="sxs-lookup"><span data-stu-id="68707-300">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="68707-301">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="68707-301">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="68707-302">Emacs： `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="68707-302">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="68707-303">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="68707-303">ValidateAndAcceptLine</span></span>

<span data-ttu-id="68707-304">嘗試執行目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="68707-304">Attempt to execute the current input.</span></span> <span data-ttu-id="68707-305">如果目前的輸入不完整 (例如遺漏右括弧、方括弧或引號，則接續提示會顯示在下一行，而 PSReadLine 會等候按鍵編輯目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="68707-305">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="68707-306">Emacs： `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="68707-306">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="68707-307">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="68707-307">ViAcceptLine</span></span>

<span data-ttu-id="68707-308">接受行並切換至插入模式。</span><span class="sxs-lookup"><span data-stu-id="68707-308">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="68707-309">Vi 命令模式： `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="68707-309">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="68707-310">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="68707-310">ViAcceptLineOrExit</span></span>

<span data-ttu-id="68707-311">如同 Emacs 模式中的 DeleteCharOrExit，但會接受行，而不是刪除字元。</span><span class="sxs-lookup"><span data-stu-id="68707-311">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="68707-312">Vi 插入模式： `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="68707-312">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="68707-313">Vi 命令模式： `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="68707-313">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="68707-314">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="68707-314">ViAppendLine</span></span>

<span data-ttu-id="68707-315">新行會插入目前的行下方。</span><span class="sxs-lookup"><span data-stu-id="68707-315">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="68707-316">Vi 命令模式： `<o>`</span><span class="sxs-lookup"><span data-stu-id="68707-316">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="68707-317">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="68707-317">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="68707-318">刪除先前的單字，只使用空白字元做為文字分隔符號。</span><span class="sxs-lookup"><span data-stu-id="68707-318">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="68707-319">Vi 命令模式： `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="68707-319">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="68707-320">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="68707-320">ViBackwardGlob</span></span>

<span data-ttu-id="68707-321">將游標移回上一個單字的開頭，只使用空白字元做為分隔符號。</span><span class="sxs-lookup"><span data-stu-id="68707-321">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="68707-322">Vi 命令模式： `<B>`</span><span class="sxs-lookup"><span data-stu-id="68707-322">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="68707-323">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="68707-323">ViDeleteBrace</span></span>

<span data-ttu-id="68707-324">尋找相符的括弧、括弧或方括弧，並刪除內的所有內容，包括括弧。</span><span class="sxs-lookup"><span data-stu-id="68707-324">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="68707-325">Vi 命令模式： `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="68707-325">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="68707-326">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="68707-326">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="68707-327">刪除到字尾。</span><span class="sxs-lookup"><span data-stu-id="68707-327">Delete to the end of the word.</span></span>

- <span data-ttu-id="68707-328">Vi 命令模式： `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="68707-328">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="68707-329">ViDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="68707-329">ViDeleteGlob</span></span>

<span data-ttu-id="68707-330">刪除下一個 glob (以空白字元分隔的單字) 。</span><span class="sxs-lookup"><span data-stu-id="68707-330">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="68707-331">Vi 命令模式： `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="68707-331">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="68707-332">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="68707-332">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="68707-333">刪除指定的字元。</span><span class="sxs-lookup"><span data-stu-id="68707-333">Deletes until given character.</span></span>

- <span data-ttu-id="68707-334">Vi 命令模式： `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="68707-334">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="68707-335">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="68707-335">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="68707-336">刪除指定的字元。</span><span class="sxs-lookup"><span data-stu-id="68707-336">Deletes until given character.</span></span>

- <span data-ttu-id="68707-337">Vi 命令模式： `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="68707-337">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="68707-338">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="68707-338">ViDeleteToChar</span></span>

<span data-ttu-id="68707-339">刪除指定的字元。</span><span class="sxs-lookup"><span data-stu-id="68707-339">Deletes until given character.</span></span>

- <span data-ttu-id="68707-340">Vi 命令模式： `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="68707-340">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="68707-341">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="68707-341">ViDeleteToCharBackward</span></span>

<span data-ttu-id="68707-342">在指定的字元之前反向刪除。</span><span class="sxs-lookup"><span data-stu-id="68707-342">Deletes backwards until given character.</span></span>

- <span data-ttu-id="68707-343">Vi 命令模式： `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="68707-343">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="68707-344">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="68707-344">ViInsertAtBegining</span></span>

<span data-ttu-id="68707-345">切換至插入模式，並將游標放在行首。</span><span class="sxs-lookup"><span data-stu-id="68707-345">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="68707-346">Vi 命令模式： `<I>`</span><span class="sxs-lookup"><span data-stu-id="68707-346">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="68707-347">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="68707-347">ViInsertAtEnd</span></span>

<span data-ttu-id="68707-348">切換至插入模式，並將游標放在行尾。</span><span class="sxs-lookup"><span data-stu-id="68707-348">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="68707-349">Vi 命令模式： `<A>`</span><span class="sxs-lookup"><span data-stu-id="68707-349">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="68707-350">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="68707-350">ViInsertLine</span></span>

<span data-ttu-id="68707-351">新的行會插入到目前這一行的上方。</span><span class="sxs-lookup"><span data-stu-id="68707-351">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="68707-352">Vi 命令模式： `<O>`</span><span class="sxs-lookup"><span data-stu-id="68707-352">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="68707-353">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="68707-353">ViInsertWithAppend</span></span>

<span data-ttu-id="68707-354">從目前的行位置附加。</span><span class="sxs-lookup"><span data-stu-id="68707-354">Append from the current line position.</span></span>

- <span data-ttu-id="68707-355">Vi 命令模式： `<a>`</span><span class="sxs-lookup"><span data-stu-id="68707-355">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="68707-356">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="68707-356">ViInsertWithDelete</span></span>

<span data-ttu-id="68707-357">刪除目前的字元並切換至插入模式。</span><span class="sxs-lookup"><span data-stu-id="68707-357">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="68707-358">Vi 命令模式： `<s>`</span><span class="sxs-lookup"><span data-stu-id="68707-358">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="68707-359">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="68707-359">ViJoinLines</span></span>

<span data-ttu-id="68707-360">加入目前的行和下一行。</span><span class="sxs-lookup"><span data-stu-id="68707-360">Joins the current line and the next line.</span></span>

- <span data-ttu-id="68707-361">Vi 命令模式： `<J>`</span><span class="sxs-lookup"><span data-stu-id="68707-361">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="68707-362">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="68707-362">ViReplaceLine</span></span>

<span data-ttu-id="68707-363">清除整個命令列。</span><span class="sxs-lookup"><span data-stu-id="68707-363">Erase the entire command line.</span></span>

- <span data-ttu-id="68707-364">Vi 命令模式： `<S>` 、 `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="68707-364">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="68707-365">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="68707-365">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="68707-366">取代指定的字元。</span><span class="sxs-lookup"><span data-stu-id="68707-366">Replaces until given character.</span></span>

- <span data-ttu-id="68707-367">Vi 命令模式： `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="68707-367">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="68707-368">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="68707-368">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="68707-369">取代指定的字元。</span><span class="sxs-lookup"><span data-stu-id="68707-369">Replaces until given character.</span></span>

- <span data-ttu-id="68707-370">Vi 命令模式： `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="68707-370">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="68707-371">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="68707-371">ViReplaceToChar</span></span>

<span data-ttu-id="68707-372">刪除指定的字元。</span><span class="sxs-lookup"><span data-stu-id="68707-372">Deletes until given character.</span></span>

- <span data-ttu-id="68707-373">Vi 命令模式： `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="68707-373">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="68707-374">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="68707-374">ViReplaceToCharBackward</span></span>

<span data-ttu-id="68707-375">取代指定的字元。</span><span class="sxs-lookup"><span data-stu-id="68707-375">Replaces until given character.</span></span>

- <span data-ttu-id="68707-376">Vi 命令模式： `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="68707-376">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="68707-377">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="68707-377">ViYankBeginningOfLine</span></span>

<span data-ttu-id="68707-378">從緩衝區開頭 Yank 至資料指標。</span><span class="sxs-lookup"><span data-stu-id="68707-378">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="68707-379">Vi 命令模式： `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="68707-379">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="68707-380">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="68707-380">ViYankEndOfGlob</span></span>

<span data-ttu-id="68707-381">從資料指標 Yank 至 WORD (s) 的結尾。</span><span class="sxs-lookup"><span data-stu-id="68707-381">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="68707-382">Vi 命令模式： `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="68707-382">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="68707-383">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="68707-383">ViYankEndOfWord</span></span>

<span data-ttu-id="68707-384">從資料指標 Yank 至 word (s) 的結尾。</span><span class="sxs-lookup"><span data-stu-id="68707-384">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="68707-385">Vi 命令模式： `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="68707-385">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="68707-386">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="68707-386">ViYankLeft</span></span>

<span data-ttu-id="68707-387">Yank 字元 (s) 到游標的左邊。</span><span class="sxs-lookup"><span data-stu-id="68707-387">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="68707-388">Vi 命令模式： `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="68707-388">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="68707-389">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="68707-389">ViYankLine</span></span>

<span data-ttu-id="68707-390">Yank 整個緩衝區。</span><span class="sxs-lookup"><span data-stu-id="68707-390">Yank the entire buffer.</span></span>

- <span data-ttu-id="68707-391">Vi 命令模式： `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="68707-391">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="68707-392">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="68707-392">ViYankNextGlob</span></span>

<span data-ttu-id="68707-393">從資料指標 Yank 至下一個單字的開頭 (s) 。</span><span class="sxs-lookup"><span data-stu-id="68707-393">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="68707-394">Vi 命令模式： `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="68707-394">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="68707-395">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="68707-395">ViYankNextWord</span></span>

<span data-ttu-id="68707-396">Yank) 在游標之後 (s 的單字。</span><span class="sxs-lookup"><span data-stu-id="68707-396">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="68707-397">Vi 命令模式： `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="68707-397">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="68707-398">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="68707-398">ViYankPercent</span></span>

<span data-ttu-id="68707-399">Yank 至/從相符的括弧。</span><span class="sxs-lookup"><span data-stu-id="68707-399">Yank to/from matching brace.</span></span>

- <span data-ttu-id="68707-400">Vi 命令模式： `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="68707-400">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="68707-401">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="68707-401">ViYankPreviousGlob</span></span>

<span data-ttu-id="68707-402">從字組開頭 (s 的 Yank) 到資料指標。</span><span class="sxs-lookup"><span data-stu-id="68707-402">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="68707-403">Vi 命令模式： `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="68707-403">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="68707-404">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="68707-404">ViYankPreviousWord</span></span>

<span data-ttu-id="68707-405">Yank) 在游標之前的文字 (s。</span><span class="sxs-lookup"><span data-stu-id="68707-405">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="68707-406">Vi 命令模式： `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="68707-406">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="68707-407">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="68707-407">ViYankRight</span></span>

<span data-ttu-id="68707-408">Yank 字元 (s) 在游標右邊和右邊。</span><span class="sxs-lookup"><span data-stu-id="68707-408">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="68707-409">Vi 命令模式： `<y,l>` 、 `<y,Space>`</span><span class="sxs-lookup"><span data-stu-id="68707-409">Vi command mode: `<y,l>`, `<y,Space>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="68707-410">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="68707-410">ViYankToEndOfLine</span></span>

<span data-ttu-id="68707-411">從資料指標 Yank 至緩衝區的結尾。</span><span class="sxs-lookup"><span data-stu-id="68707-411">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="68707-412">Vi 命令模式： `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="68707-412">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="68707-413">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="68707-413">ViYankToFirstChar</span></span>

<span data-ttu-id="68707-414">從第一個非空白字元 Yank 至游標。</span><span class="sxs-lookup"><span data-stu-id="68707-414">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="68707-415">Vi 命令模式： `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="68707-415">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="68707-416">美國 佬</span><span class="sxs-lookup"><span data-stu-id="68707-416">Yank</span></span>

<span data-ttu-id="68707-417">將最近終止的文字加入至輸入。</span><span class="sxs-lookup"><span data-stu-id="68707-417">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="68707-418">Emacs： `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="68707-418">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="68707-419">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="68707-419">YankLastArg</span></span>

<span data-ttu-id="68707-420">Yank 前一個歷程記錄行中的最後一個引數。</span><span class="sxs-lookup"><span data-stu-id="68707-420">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="68707-421">使用引數時，第一次叫用時，其行為就像 YankNthArg 一樣。</span><span class="sxs-lookup"><span data-stu-id="68707-421">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="68707-422">如果叫用多次，則改為逐一查看歷程記錄和 arg，將方向 (負反轉方向。 ) </span><span class="sxs-lookup"><span data-stu-id="68707-422">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="68707-423">Cmd： `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="68707-423">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="68707-424">Emacs： `<Alt+.>` 、 `<Alt+_>` 、 `<Escape,.>` 、 `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="68707-424">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="68707-425">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="68707-425">YankNthArg</span></span>

<span data-ttu-id="68707-426">從上一個歷程記錄行中 Yank 命令) 之後，第一個引數 (。</span><span class="sxs-lookup"><span data-stu-id="68707-426">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="68707-427">使用引數時，請 yank 第 n 個引數 (從 0) 開始，如果引數為負數，則從最後一個引數開始。</span><span class="sxs-lookup"><span data-stu-id="68707-427">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="68707-428">Emacs： `<Ctrl+Alt+y>` ， `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="68707-428">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="68707-429">YankPop</span><span class="sxs-lookup"><span data-stu-id="68707-429">YankPop</span></span>

<span data-ttu-id="68707-430">如果先前的作業是 Yank 或 YankPop，請將先前 yanked 的文字取代為終止環形中的下一個已取消文字。</span><span class="sxs-lookup"><span data-stu-id="68707-430">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="68707-431">Emacs： `<Alt+y>` ， `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="68707-431">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="68707-432">資料指標移動函數</span><span class="sxs-lookup"><span data-stu-id="68707-432">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="68707-433">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="68707-433">BackwardChar</span></span>

<span data-ttu-id="68707-434">將游標向左移動一個字元。</span><span class="sxs-lookup"><span data-stu-id="68707-434">Move the cursor one character to the left.</span></span> <span data-ttu-id="68707-435">這可能會將游標移至多行輸入的上一行。</span><span class="sxs-lookup"><span data-stu-id="68707-435">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="68707-436">Cmd： `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="68707-436">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="68707-437">Emacs： `<LeftArrow>` ， `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="68707-437">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>
- <span data-ttu-id="68707-438">Vi 插入模式： `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="68707-438">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="68707-439">Vi 命令模式： `<LeftArrow>` 、 `<Backspace>` 、 `<h>`</span><span class="sxs-lookup"><span data-stu-id="68707-439">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="68707-440">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="68707-440">BackwardWord</span></span>

<span data-ttu-id="68707-441">將游標移回目前單字的開頭，或將游標移回上一個單字開頭的單字。</span><span class="sxs-lookup"><span data-stu-id="68707-441">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="68707-442">單字界限是由一組可設定的字元所定義。</span><span class="sxs-lookup"><span data-stu-id="68707-442">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="68707-443">Cmd： `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="68707-443">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="68707-444">Emacs： `<Alt+b>` ， `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="68707-444">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="68707-445">Vi 插入模式： `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="68707-445">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="68707-446">Vi 命令模式： `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="68707-446">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="68707-447">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="68707-447">BeginningOfLine</span></span>

<span data-ttu-id="68707-448">如果輸入有多行，請移至目前行的開頭，如果已經在行首，則移至輸入的開頭。</span><span class="sxs-lookup"><span data-stu-id="68707-448">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="68707-449">如果輸入具有單一行，請移至輸入的開頭。</span><span class="sxs-lookup"><span data-stu-id="68707-449">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="68707-450">Cmd： `<Home>`</span><span class="sxs-lookup"><span data-stu-id="68707-450">Cmd: `<Home>`</span></span>
- <span data-ttu-id="68707-451">Emacs： `<Home>` ， `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="68707-451">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="68707-452">Vi 插入模式： `<Home>`</span><span class="sxs-lookup"><span data-stu-id="68707-452">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="68707-453">Vi 命令模式： `<Home>`</span><span class="sxs-lookup"><span data-stu-id="68707-453">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="68707-454">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="68707-454">EndOfLine</span></span>

<span data-ttu-id="68707-455">如果輸入有多行，請移至目前行的結尾，如果已經在行尾，則移至輸入的結尾。</span><span class="sxs-lookup"><span data-stu-id="68707-455">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="68707-456">如果輸入具有單一行，請移至輸入的結尾。</span><span class="sxs-lookup"><span data-stu-id="68707-456">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="68707-457">Cmd： `<End>`</span><span class="sxs-lookup"><span data-stu-id="68707-457">Cmd: `<End>`</span></span>
- <span data-ttu-id="68707-458">Emacs： `<End>` ， `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="68707-458">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="68707-459">Vi 插入模式： `<End>`</span><span class="sxs-lookup"><span data-stu-id="68707-459">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="68707-460">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="68707-460">ForwardChar</span></span>

<span data-ttu-id="68707-461">將游標向右移動一個字元。</span><span class="sxs-lookup"><span data-stu-id="68707-461">Move the cursor one character to the right.</span></span> <span data-ttu-id="68707-462">這可能會將游標移至下一行的多行輸入。</span><span class="sxs-lookup"><span data-stu-id="68707-462">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="68707-463">Cmd： `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="68707-463">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="68707-464">Emacs： `<RightArrow>` ， `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="68707-464">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>
- <span data-ttu-id="68707-465">Vi 插入模式： `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="68707-465">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="68707-466">Vi 命令模式： `<RightArrow>` 、 `<Space>` 、 `<l>`</span><span class="sxs-lookup"><span data-stu-id="68707-466">Vi command mode: `<RightArrow>`, `<Space>`, `<l>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="68707-467">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="68707-467">ForwardWord</span></span>

<span data-ttu-id="68707-468">將游標向前移動至目前單字的結尾，或在文字之間移動到下一個單字的結尾。</span><span class="sxs-lookup"><span data-stu-id="68707-468">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="68707-469">單字界限是由一組可設定的字元所定義。</span><span class="sxs-lookup"><span data-stu-id="68707-469">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="68707-470">Emacs： `<Alt+f>` ， `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="68707-470">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="68707-471">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="68707-471">GotoBrace</span></span>

<span data-ttu-id="68707-472">移至相符的大括弧、括弧或方括弧。</span><span class="sxs-lookup"><span data-stu-id="68707-472">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="68707-473">Cmd： `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="68707-473">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="68707-474">Vi 插入模式： `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="68707-474">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="68707-475">Vi 命令模式： `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="68707-475">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="68707-476">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="68707-476">GotoColumn</span></span>

<span data-ttu-id="68707-477">移至 arg 所表示的資料行。</span><span class="sxs-lookup"><span data-stu-id="68707-477">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="68707-478">Vi 命令模式： `<|>`</span><span class="sxs-lookup"><span data-stu-id="68707-478">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="68707-479">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="68707-479">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="68707-480">將游標移至行中的第一個非空白字元。</span><span class="sxs-lookup"><span data-stu-id="68707-480">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="68707-481">Vi 命令模式： `<^>`</span><span class="sxs-lookup"><span data-stu-id="68707-481">Vi command mode: `<^>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="68707-482">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="68707-482">MoveToEndOfLine</span></span>

<span data-ttu-id="68707-483">將游標移至輸入的結尾。</span><span class="sxs-lookup"><span data-stu-id="68707-483">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="68707-484">Vi 命令模式： `<End>` 、 `<$>`</span><span class="sxs-lookup"><span data-stu-id="68707-484">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="68707-485">NextLine</span><span class="sxs-lookup"><span data-stu-id="68707-485">NextLine</span></span>

<span data-ttu-id="68707-486">將游標移至下一行。</span><span class="sxs-lookup"><span data-stu-id="68707-486">Move the cursor to the next line.</span></span>

- <span data-ttu-id="68707-487">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="68707-487">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="68707-488">NextWord</span><span class="sxs-lookup"><span data-stu-id="68707-488">NextWord</span></span>

<span data-ttu-id="68707-489">將游標向前移至下一個單字的開頭。</span><span class="sxs-lookup"><span data-stu-id="68707-489">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="68707-490">單字界限是由一組可設定的字元所定義。</span><span class="sxs-lookup"><span data-stu-id="68707-490">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="68707-491">Cmd： `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="68707-491">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="68707-492">Vi 插入模式： `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="68707-492">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="68707-493">Vi 命令模式： `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="68707-493">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="68707-494">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="68707-494">NextWordEnd</span></span>

<span data-ttu-id="68707-495">將游標向前移動至目前單字的結尾，或在文字之間移動到下一個單字的結尾。</span><span class="sxs-lookup"><span data-stu-id="68707-495">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="68707-496">單字界限是由一組可設定的字元所定義。</span><span class="sxs-lookup"><span data-stu-id="68707-496">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="68707-497">Vi 命令模式： `<e>`</span><span class="sxs-lookup"><span data-stu-id="68707-497">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="68707-498">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="68707-498">PreviousLine</span></span>

<span data-ttu-id="68707-499">將游標移至上一行。</span><span class="sxs-lookup"><span data-stu-id="68707-499">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="68707-500">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="68707-500">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="68707-501">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="68707-501">ShellBackwardWord</span></span>

<span data-ttu-id="68707-502">將游標移回目前單字的開頭，或將游標移回上一個單字開頭的單字。</span><span class="sxs-lookup"><span data-stu-id="68707-502">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="68707-503">單字界限是由 PowerShell 權杖所定義。</span><span class="sxs-lookup"><span data-stu-id="68707-503">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="68707-504">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="68707-504">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="68707-505">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="68707-505">ShellForwardWord</span></span>

<span data-ttu-id="68707-506">將游標向前移至下一個單字的開頭。</span><span class="sxs-lookup"><span data-stu-id="68707-506">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="68707-507">單字界限是由 PowerShell 權杖所定義。</span><span class="sxs-lookup"><span data-stu-id="68707-507">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="68707-508">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="68707-508">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="68707-509">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="68707-509">ShellNextWord</span></span>

<span data-ttu-id="68707-510">將游標向前移動至目前單字的結尾，或在文字之間移動到下一個單字的結尾。</span><span class="sxs-lookup"><span data-stu-id="68707-510">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="68707-511">單字界限是由 PowerShell 權杖所定義。</span><span class="sxs-lookup"><span data-stu-id="68707-511">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="68707-512">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="68707-512">Function is unbound.</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="68707-513">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="68707-513">ViBackwardWord</span></span>

<span data-ttu-id="68707-514">將游標移回目前單字的開頭，或將游標移回上一個單字開頭的單字。</span><span class="sxs-lookup"><span data-stu-id="68707-514">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="68707-515">單字界限是由一組可設定的字元所定義。</span><span class="sxs-lookup"><span data-stu-id="68707-515">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="68707-516">Vi 命令模式： `<b>`</span><span class="sxs-lookup"><span data-stu-id="68707-516">Vi command mode: `<b>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="68707-517">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="68707-517">ViEndOfGlob</span></span>

<span data-ttu-id="68707-518">將游標移至單字的結尾，只使用空白字元做為分隔符號。</span><span class="sxs-lookup"><span data-stu-id="68707-518">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="68707-519">Vi 命令模式： `<E>`</span><span class="sxs-lookup"><span data-stu-id="68707-519">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="68707-520">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="68707-520">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="68707-521">移至上一個單字的結尾，只使用空白字元做為單字分隔符號。</span><span class="sxs-lookup"><span data-stu-id="68707-521">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="68707-522">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="68707-522">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="68707-523">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="68707-523">ViGotoBrace</span></span>

<span data-ttu-id="68707-524">類似于 GotoBrace，但它是以字元為基礎，而不是以權杖為基礎。</span><span class="sxs-lookup"><span data-stu-id="68707-524">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="68707-525">Vi 命令模式： `<%>`</span><span class="sxs-lookup"><span data-stu-id="68707-525">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="68707-526">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="68707-526">ViNextGlob</span></span>

<span data-ttu-id="68707-527">移至下一個單字，只使用空白字元做為單字分隔符號。</span><span class="sxs-lookup"><span data-stu-id="68707-527">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="68707-528">Vi 命令模式： `<W>`</span><span class="sxs-lookup"><span data-stu-id="68707-528">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="68707-529">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="68707-529">ViNextWord</span></span>

<span data-ttu-id="68707-530">將游標向前移至下一個單字的開頭。</span><span class="sxs-lookup"><span data-stu-id="68707-530">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="68707-531">單字界限是由一組可設定的字元所定義。</span><span class="sxs-lookup"><span data-stu-id="68707-531">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="68707-532">Vi 命令模式： `<w>`</span><span class="sxs-lookup"><span data-stu-id="68707-532">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="68707-533">歷程記錄函數</span><span class="sxs-lookup"><span data-stu-id="68707-533">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="68707-534">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="68707-534">BeginningOfHistory</span></span>

<span data-ttu-id="68707-535">移至歷程記錄中的第一個專案。</span><span class="sxs-lookup"><span data-stu-id="68707-535">Move to the first item in the history.</span></span>

- <span data-ttu-id="68707-536">Emacs： `<Alt+`<>\`</span><span class="sxs-lookup"><span data-stu-id="68707-536">Emacs: `<Alt+`<>\`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="68707-537">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="68707-537">ClearHistory</span></span>

<span data-ttu-id="68707-538">清除 PSReadLine 中的歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="68707-538">Clears history in PSReadLine.</span></span> <span data-ttu-id="68707-539">這不會影響 PowerShell 歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="68707-539">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="68707-540">Cmd： `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="68707-540">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="68707-541">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="68707-541">EndOfHistory</span></span>

<span data-ttu-id="68707-542">移至記錄中目前輸入)  (的最後一個專案。</span><span class="sxs-lookup"><span data-stu-id="68707-542">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="68707-543">Emacs： `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="68707-543">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="68707-544">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="68707-544">ForwardSearchHistory</span></span>

<span data-ttu-id="68707-545">透過歷程記錄執行漸進式向前搜尋。</span><span class="sxs-lookup"><span data-stu-id="68707-545">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="68707-546">Cmd： `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="68707-546">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="68707-547">Emacs： `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="68707-547">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="68707-548">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="68707-548">HistorySearchBackward</span></span>

<span data-ttu-id="68707-549">將目前的輸入取代為 PSReadLine 記錄中與開始和輸入和資料指標之間的字元相符的 ' previous ' 專案。</span><span class="sxs-lookup"><span data-stu-id="68707-549">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="68707-550">Cmd： `<F8>`</span><span class="sxs-lookup"><span data-stu-id="68707-550">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="68707-551">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="68707-551">HistorySearchForward</span></span>

<span data-ttu-id="68707-552">將目前的輸入取代為 PSReadLine 記錄中與開始和輸入和資料指標之間的字元相符的 ' next ' 專案。</span><span class="sxs-lookup"><span data-stu-id="68707-552">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="68707-553">Cmd： `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="68707-553">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="68707-554">NextHistory</span><span class="sxs-lookup"><span data-stu-id="68707-554">NextHistory</span></span>

<span data-ttu-id="68707-555">將目前的輸入取代為 PSReadLine 記錄中的 ' next ' 專案。</span><span class="sxs-lookup"><span data-stu-id="68707-555">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="68707-556">Cmd： `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="68707-556">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="68707-557">Emacs： `<DownArrow>` ， `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="68707-557">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="68707-558">Vi 插入模式： `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="68707-558">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="68707-559">Vi 命令模式： `<DownArrow>` 、 `<j>` 、 `<+>`</span><span class="sxs-lookup"><span data-stu-id="68707-559">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="68707-560">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="68707-560">PreviousHistory</span></span>

<span data-ttu-id="68707-561">將目前的輸入取代為 PSReadLine 記錄中的 ' previous ' 專案。</span><span class="sxs-lookup"><span data-stu-id="68707-561">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="68707-562">Cmd： `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="68707-562">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="68707-563">Emacs： `<UpArrow>` ， `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="68707-563">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="68707-564">Vi 插入模式： `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="68707-564">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="68707-565">Vi 命令模式： `<UpArrow>` 、 `<k>` 、 `<->`</span><span class="sxs-lookup"><span data-stu-id="68707-565">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="68707-566">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="68707-566">ReverseSearchHistory</span></span>

<span data-ttu-id="68707-567">透過歷程記錄執行增量向前搜尋。</span><span class="sxs-lookup"><span data-stu-id="68707-567">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="68707-568">Cmd： `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="68707-568">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="68707-569">Emacs： `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="68707-569">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="68707-570">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="68707-570">ViSearchHistoryBackward</span></span>

<span data-ttu-id="68707-571">提示輸入搜尋字串，並在 AcceptLine 時起始搜尋。</span><span class="sxs-lookup"><span data-stu-id="68707-571">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="68707-572">Vi 插入模式： `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="68707-572">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="68707-573">Vi 命令模式： `</>` 、 `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="68707-573">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="68707-574">完成函式</span><span class="sxs-lookup"><span data-stu-id="68707-574">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="68707-575">完成</span><span class="sxs-lookup"><span data-stu-id="68707-575">Complete</span></span>

<span data-ttu-id="68707-576">嘗試對資料指標周圍的文字執行完成。</span><span class="sxs-lookup"><span data-stu-id="68707-576">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="68707-577">如果有多個可能的完成，則會使用最長的明確前置詞來完成。</span><span class="sxs-lookup"><span data-stu-id="68707-577">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="68707-578">如果嘗試完成最長的明確完成，則會顯示可能的完成清單。</span><span class="sxs-lookup"><span data-stu-id="68707-578">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="68707-579">Emacs： `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="68707-579">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="68707-580">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="68707-580">MenuComplete</span></span>

<span data-ttu-id="68707-581">嘗試對資料指標周圍的文字執行完成。</span><span class="sxs-lookup"><span data-stu-id="68707-581">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="68707-582">如果有多個可能的完成，則會使用最長的明確前置詞來完成。</span><span class="sxs-lookup"><span data-stu-id="68707-582">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="68707-583">如果嘗試完成最長的明確完成，則會顯示可能的完成清單。</span><span class="sxs-lookup"><span data-stu-id="68707-583">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="68707-584">Cmd： `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="68707-584">Cmd: `<Ctrl+Space>`</span></span>
- <span data-ttu-id="68707-585">Emacs： `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="68707-585">Emacs: `<Ctrl+Space>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="68707-586">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="68707-586">PossibleCompletions</span></span>

<span data-ttu-id="68707-587">顯示可能的完成清單。</span><span class="sxs-lookup"><span data-stu-id="68707-587">Display the list of possible completions.</span></span>

- <span data-ttu-id="68707-588">Emacs： `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="68707-588">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="68707-589">Vi 插入模式： `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="68707-589">Vi insert mode: `<Ctrl+Space>`</span></span>
- <span data-ttu-id="68707-590">Vi 命令模式： `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="68707-590">Vi command mode: `<Ctrl+Space>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="68707-591">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="68707-591">TabCompleteNext</span></span>

<span data-ttu-id="68707-592">嘗試使用下一個可用的完成來完成資料指標周圍的文字。</span><span class="sxs-lookup"><span data-stu-id="68707-592">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="68707-593">Cmd： `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="68707-593">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="68707-594">Vi 命令模式： `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="68707-594">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="68707-595">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="68707-595">TabCompletePrevious</span></span>

<span data-ttu-id="68707-596">嘗試使用先前的可用完成來完成資料指標周圍的文字。</span><span class="sxs-lookup"><span data-stu-id="68707-596">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="68707-597">Cmd： `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="68707-597">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="68707-598">Vi 命令模式： `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="68707-598">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="68707-599">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="68707-599">ViTabCompleteNext</span></span>

<span data-ttu-id="68707-600">視需要結束目前的編輯群組，並叫用 TabCompleteNext。</span><span class="sxs-lookup"><span data-stu-id="68707-600">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="68707-601">Vi 插入模式： `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="68707-601">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="68707-602">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="68707-602">ViTabCompletePrevious</span></span>

<span data-ttu-id="68707-603">視需要結束目前的編輯群組，並叫用 TabCompletePrevious。</span><span class="sxs-lookup"><span data-stu-id="68707-603">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="68707-604">Vi 插入模式： `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="68707-604">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="68707-605">其他函式</span><span class="sxs-lookup"><span data-stu-id="68707-605">Miscellaneous functions</span></span>

### <a name="capturescreen"></a><span data-ttu-id="68707-606">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="68707-606">CaptureScreen</span></span>

<span data-ttu-id="68707-607">啟動互動式螢幕擷取畫面-向上/向下箭號選取 [線條]，輸入將選取的文字複製到剪貼簿做為文字和 html。</span><span class="sxs-lookup"><span data-stu-id="68707-607">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="68707-608">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="68707-608">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="68707-609">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="68707-609">ClearScreen</span></span>

<span data-ttu-id="68707-610">清除畫面並在畫面頂端繪製目前的線。</span><span class="sxs-lookup"><span data-stu-id="68707-610">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="68707-611">Cmd： `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="68707-611">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="68707-612">Emacs： `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="68707-612">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="68707-613">Vi 插入模式： `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="68707-613">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="68707-614">Vi 命令模式： `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="68707-614">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="68707-615">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="68707-615">DigitArgument</span></span>

<span data-ttu-id="68707-616">開始新的數位引數以傳遞至其他函式。</span><span class="sxs-lookup"><span data-stu-id="68707-616">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="68707-617">Cmd： `<Alt+0>` 、 `<Alt+1>` 、 `<Alt+2>` 、 `<Alt+3>` 、 `<Alt+4>` 、 `<Alt+5>` 、 `<Alt+6>` `<Alt+7>` `<Alt+8>` `<Alt+9>` 、、、、、 `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="68707-617">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="68707-618">Emacs： `<Alt+0>` 、 `<Alt+1>` 、 `<Alt+2>` 、、、 `<Alt+3>` `<Alt+4>` `<Alt+5>` 、 `<Alt+6>` 、 `<Alt+7>` 、 `<Alt+8>` 、 `<Alt+9>` 、、 `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="68707-618">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="68707-619">Vi 命令模式： `<0>` 、 `<1>` 、 `<2>` 、 `<3>` 、 `<4>` 、 `<5>` 、 `<6>` `<7>` `<8>` 、、、、 `<9>`</span><span class="sxs-lookup"><span data-stu-id="68707-619">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="68707-620">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="68707-620">InvokePrompt</span></span>

<span data-ttu-id="68707-621">清除目前的提示，並呼叫 prompt 函式以重新顯示提示。</span><span class="sxs-lookup"><span data-stu-id="68707-621">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="68707-622">適用于變更狀態的自訂金鑰處理常式，例如變更目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="68707-622">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="68707-623">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="68707-623">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="68707-624">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="68707-624">ScrollDisplayDown</span></span>

<span data-ttu-id="68707-625">將顯示畫面向下移動一個畫面。</span><span class="sxs-lookup"><span data-stu-id="68707-625">Scroll the display down one screen.</span></span>

- <span data-ttu-id="68707-626">Cmd： `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="68707-626">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="68707-627">Emacs： `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="68707-627">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="68707-628">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="68707-628">ScrollDisplayDownLine</span></span>

<span data-ttu-id="68707-629">將向下移動一行。</span><span class="sxs-lookup"><span data-stu-id="68707-629">Scroll the display down one line.</span></span>

- <span data-ttu-id="68707-630">Cmd： `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="68707-630">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="68707-631">Emacs： `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="68707-631">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="68707-632">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="68707-632">ScrollDisplayToCursor</span></span>

<span data-ttu-id="68707-633">將顯示滾動至游標。</span><span class="sxs-lookup"><span data-stu-id="68707-633">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="68707-634">Emacs： `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="68707-634">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="68707-635">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="68707-635">ScrollDisplayTop</span></span>

<span data-ttu-id="68707-636">將顯示器向上方滾動。</span><span class="sxs-lookup"><span data-stu-id="68707-636">Scroll the display to the top.</span></span>

- <span data-ttu-id="68707-637">Emacs： `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="68707-637">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="68707-638">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="68707-638">ScrollDisplayUp</span></span>

<span data-ttu-id="68707-639">將顯示畫面向上移動一次。</span><span class="sxs-lookup"><span data-stu-id="68707-639">Scroll the display up one screen.</span></span>

- <span data-ttu-id="68707-640">Cmd： `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="68707-640">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="68707-641">Emacs： `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="68707-641">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="68707-642">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="68707-642">ScrollDisplayUpLine</span></span>

<span data-ttu-id="68707-643">將顯示畫面向下移動一行。</span><span class="sxs-lookup"><span data-stu-id="68707-643">Scroll the display up one line.</span></span>

- <span data-ttu-id="68707-644">Cmd： `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="68707-644">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="68707-645">Emacs： `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="68707-645">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="68707-646">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="68707-646">SelfInsert</span></span>

<span data-ttu-id="68707-647">插入金鑰。</span><span class="sxs-lookup"><span data-stu-id="68707-647">Insert the key.</span></span>

- <span data-ttu-id="68707-648">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="68707-648">Function is unbound.</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="68707-649">ShowKeyBindings</span><span class="sxs-lookup"><span data-stu-id="68707-649">ShowKeyBindings</span></span>

<span data-ttu-id="68707-650">顯示所有系結的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="68707-650">Show all bound keys.</span></span>

- <span data-ttu-id="68707-651">Cmd： `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="68707-651">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="68707-652">Emacs： `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="68707-652">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="68707-653">Vi 插入模式： `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="68707-653">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="68707-654">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="68707-654">ViCommandMode</span></span>

<span data-ttu-id="68707-655">將目前的作業模式從 Vi-Insert 切換至 Vi 命令。</span><span class="sxs-lookup"><span data-stu-id="68707-655">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="68707-656">Vi 插入模式： `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="68707-656">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="68707-657">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="68707-657">ViDigitArgumentInChord</span></span>

<span data-ttu-id="68707-658">開始新的數位引數，以傳遞至其他函式，而非 vi 的 chords 之一。</span><span class="sxs-lookup"><span data-stu-id="68707-658">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="68707-659">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="68707-659">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="68707-660">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="68707-660">ViEditVisually</span></span>

<span data-ttu-id="68707-661">在 [$env：編輯器] 或 [$env：視覺效果] 所指定的文字編輯器中編輯命令行。</span><span class="sxs-lookup"><span data-stu-id="68707-661">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="68707-662">Emacs： `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="68707-662">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="68707-663">Vi 命令模式： `<v>`</span><span class="sxs-lookup"><span data-stu-id="68707-663">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="68707-664">ViExit</span><span class="sxs-lookup"><span data-stu-id="68707-664">ViExit</span></span>

<span data-ttu-id="68707-665">離開 shell。</span><span class="sxs-lookup"><span data-stu-id="68707-665">Exits the shell.</span></span>

- <span data-ttu-id="68707-666">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="68707-666">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="68707-667">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="68707-667">ViInsertMode</span></span>

<span data-ttu-id="68707-668">切換至插入模式。</span><span class="sxs-lookup"><span data-stu-id="68707-668">Switch to Insert mode.</span></span>

- <span data-ttu-id="68707-669">Vi 命令模式： `<i>`</span><span class="sxs-lookup"><span data-stu-id="68707-669">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="68707-670">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="68707-670">WhatIsKey</span></span>

<span data-ttu-id="68707-671">讀取金鑰，並告訴我金鑰的系結目標。</span><span class="sxs-lookup"><span data-stu-id="68707-671">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="68707-672">Cmd： `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="68707-672">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="68707-673">Emacs： `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="68707-673">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="68707-674">選取函式</span><span class="sxs-lookup"><span data-stu-id="68707-674">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="68707-675">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="68707-675">ExchangePointAndMark</span></span>

<span data-ttu-id="68707-676">游標放在標記的位置，而標記會移至游標位置。</span><span class="sxs-lookup"><span data-stu-id="68707-676">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="68707-677">Emacs： `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="68707-677">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="68707-678">SelectAll</span><span class="sxs-lookup"><span data-stu-id="68707-678">SelectAll</span></span>

<span data-ttu-id="68707-679">選取整行。</span><span class="sxs-lookup"><span data-stu-id="68707-679">Select the entire line.</span></span>

- <span data-ttu-id="68707-680">Cmd： `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="68707-680">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="68707-681">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="68707-681">SelectBackwardChar</span></span>

<span data-ttu-id="68707-682">調整目前的選取範圍，以包含前一個字元。</span><span class="sxs-lookup"><span data-stu-id="68707-682">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="68707-683">Cmd： `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="68707-683">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="68707-684">Emacs： `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="68707-684">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="68707-685">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="68707-685">SelectBackwardsLine</span></span>

<span data-ttu-id="68707-686">調整目前的選取範圍，以包含從游標到行首的起點。</span><span class="sxs-lookup"><span data-stu-id="68707-686">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="68707-687">Cmd： `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="68707-687">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="68707-688">Emacs： `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="68707-688">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="68707-689">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="68707-689">SelectBackwardWord</span></span>

<span data-ttu-id="68707-690">調整目前的選取範圍，以包含前一個字組。</span><span class="sxs-lookup"><span data-stu-id="68707-690">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="68707-691">Cmd： `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="68707-691">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="68707-692">Emacs： `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="68707-692">Emacs: `<Alt+B>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="68707-693">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="68707-693">SelectForwardChar</span></span>

<span data-ttu-id="68707-694">調整目前的選取範圍，以包含下一個字元。</span><span class="sxs-lookup"><span data-stu-id="68707-694">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="68707-695">Cmd： `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="68707-695">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="68707-696">Emacs： `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="68707-696">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="68707-697">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="68707-697">SelectForwardWord</span></span>

<span data-ttu-id="68707-698">使用 ForwardWord 調整目前的選取範圍，以包含下一個字組。</span><span class="sxs-lookup"><span data-stu-id="68707-698">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="68707-699">Emacs： `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="68707-699">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="68707-700">SelectLine</span><span class="sxs-lookup"><span data-stu-id="68707-700">SelectLine</span></span>

<span data-ttu-id="68707-701">調整目前的選取範圍，以包含從游標到行尾。</span><span class="sxs-lookup"><span data-stu-id="68707-701">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="68707-702">Cmd： `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="68707-702">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="68707-703">Emacs： `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="68707-703">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="68707-704">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="68707-704">SelectNextWord</span></span>

<span data-ttu-id="68707-705">調整目前的選取範圍，以包含下一個字組。</span><span class="sxs-lookup"><span data-stu-id="68707-705">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="68707-706">Cmd： `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="68707-706">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="68707-707">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="68707-707">SelectShellBackwardWord</span></span>

<span data-ttu-id="68707-708">使用 ShellBackwardWord 調整目前的選取範圍，以包含前一個字組。</span><span class="sxs-lookup"><span data-stu-id="68707-708">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="68707-709">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="68707-709">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="68707-710">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="68707-710">SelectShellForwardWord</span></span>

<span data-ttu-id="68707-711">使用 ShellForwardWord 調整目前的選取範圍，以包含下一個字組。</span><span class="sxs-lookup"><span data-stu-id="68707-711">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="68707-712">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="68707-712">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="68707-713">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="68707-713">SelectShellNextWord</span></span>

<span data-ttu-id="68707-714">使用 ShellNextWord 調整目前的選取範圍，以包含下一個字組。</span><span class="sxs-lookup"><span data-stu-id="68707-714">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="68707-715">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="68707-715">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="68707-716">SetMark</span><span class="sxs-lookup"><span data-stu-id="68707-716">SetMark</span></span>

<span data-ttu-id="68707-717">標記目前的資料指標位置，以用於後續的編輯命令。</span><span class="sxs-lookup"><span data-stu-id="68707-717">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="68707-718">Emacs： `<Ctrl+`>\`</span><span class="sxs-lookup"><span data-stu-id="68707-718">Emacs: `<Ctrl+`>\`</span></span>

## <a name="search-functions"></a><span data-ttu-id="68707-719">搜尋函數</span><span class="sxs-lookup"><span data-stu-id="68707-719">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="68707-720">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="68707-720">CharacterSearch</span></span>

<span data-ttu-id="68707-721">讀取字元，並向前搜尋該字元的下一個出現位置。</span><span class="sxs-lookup"><span data-stu-id="68707-721">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="68707-722">如果指定了引數，則在第 n 次發生) 時，向前搜尋 (或向後搜尋。</span><span class="sxs-lookup"><span data-stu-id="68707-722">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="68707-723">Cmd： `<F3>`</span><span class="sxs-lookup"><span data-stu-id="68707-723">Cmd: `<F3>`</span></span>
- <span data-ttu-id="68707-724">Emacs： `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="68707-724">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="68707-725">Vi 插入模式： `<F3>`</span><span class="sxs-lookup"><span data-stu-id="68707-725">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="68707-726">Vi 命令模式： `<F3>`</span><span class="sxs-lookup"><span data-stu-id="68707-726">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="68707-727">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="68707-727">CharacterSearchBackward</span></span>

<span data-ttu-id="68707-728">讀取字元，並向後搜尋該字元的下一個出現位置。</span><span class="sxs-lookup"><span data-stu-id="68707-728">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="68707-729">如果指定了引數，則會在第 n 次出現) 時向後 (或向前搜尋。</span><span class="sxs-lookup"><span data-stu-id="68707-729">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="68707-730">Cmd： `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="68707-730">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="68707-731">Emacs： `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="68707-731">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="68707-732">Vi 插入模式： `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="68707-732">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="68707-733">Vi 命令模式： `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="68707-733">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="68707-734">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="68707-734">RepeatLastCharSearch</span></span>

<span data-ttu-id="68707-735">重複上次錄製的字元搜尋。</span><span class="sxs-lookup"><span data-stu-id="68707-735">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="68707-736">Vi 命令模式： `<;>`</span><span class="sxs-lookup"><span data-stu-id="68707-736">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="68707-737">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="68707-737">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="68707-738">重複上次錄製的字元搜尋，但方向相反。</span><span class="sxs-lookup"><span data-stu-id="68707-738">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="68707-739">Vi 命令模式： `<,>`</span><span class="sxs-lookup"><span data-stu-id="68707-739">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="68707-740">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="68707-740">RepeatSearch</span></span>

<span data-ttu-id="68707-741">以與之前相同的方向重複最後一個搜尋。</span><span class="sxs-lookup"><span data-stu-id="68707-741">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="68707-742">Vi 命令模式： `<n>`</span><span class="sxs-lookup"><span data-stu-id="68707-742">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="68707-743">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="68707-743">RepeatSearchBackward</span></span>

<span data-ttu-id="68707-744">以與之前相同的方向重複最後一個搜尋。</span><span class="sxs-lookup"><span data-stu-id="68707-744">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="68707-745">Vi 命令模式： `<N>`</span><span class="sxs-lookup"><span data-stu-id="68707-745">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="68707-746">SearchChar</span><span class="sxs-lookup"><span data-stu-id="68707-746">SearchChar</span></span>

<span data-ttu-id="68707-747">讀取下一個字元，然後找出該字元，再繼續進行，然後再移出一個字元。</span><span class="sxs-lookup"><span data-stu-id="68707-747">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="68707-748">這是「t」功能。</span><span class="sxs-lookup"><span data-stu-id="68707-748">This is for 't' functionality.</span></span>

- <span data-ttu-id="68707-749">Vi 命令模式： `<f>`</span><span class="sxs-lookup"><span data-stu-id="68707-749">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="68707-750">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="68707-750">SearchCharBackward</span></span>

<span data-ttu-id="68707-751">讀取下一個字元，然後找出它，然後再向後移一字元。</span><span class="sxs-lookup"><span data-stu-id="68707-751">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="68707-752">這是「t」功能。</span><span class="sxs-lookup"><span data-stu-id="68707-752">This is for 'T' functionality.</span></span>

- <span data-ttu-id="68707-753">Vi 命令模式： `<F>`</span><span class="sxs-lookup"><span data-stu-id="68707-753">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="68707-754">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="68707-754">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="68707-755">讀取下一個字元，然後找出它，然後再向後移一字元。</span><span class="sxs-lookup"><span data-stu-id="68707-755">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="68707-756">這是「t」功能。</span><span class="sxs-lookup"><span data-stu-id="68707-756">This is for 'T' functionality.</span></span>

- <span data-ttu-id="68707-757">Vi 命令模式： `<T>`</span><span class="sxs-lookup"><span data-stu-id="68707-757">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="68707-758">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="68707-758">SearchCharWithBackoff</span></span>

<span data-ttu-id="68707-759">讀取下一個字元，然後找出該字元，再繼續進行，然後再移出一個字元。</span><span class="sxs-lookup"><span data-stu-id="68707-759">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="68707-760">這是「t」功能。</span><span class="sxs-lookup"><span data-stu-id="68707-760">This is for 't' functionality.</span></span>

- <span data-ttu-id="68707-761">Vi 命令模式： `<t>`</span><span class="sxs-lookup"><span data-stu-id="68707-761">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="68707-762">SearchForward</span><span class="sxs-lookup"><span data-stu-id="68707-762">SearchForward</span></span>

<span data-ttu-id="68707-763">提示輸入搜尋字串，並在 AcceptLine 時起始搜尋。</span><span class="sxs-lookup"><span data-stu-id="68707-763">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="68707-764">Vi 插入模式： `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="68707-764">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="68707-765">Vi 命令模式： `<?>` 、 `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="68707-765">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="68707-766">自訂索引鍵系結</span><span class="sxs-lookup"><span data-stu-id="68707-766">Custom Key Bindings</span></span>

<span data-ttu-id="68707-767">PSReadLine 支援使用 Cmdlet 的自訂金鑰系結 `Set-PSReadLineKeyHandler` 。</span><span class="sxs-lookup"><span data-stu-id="68707-767">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="68707-768">大部分的自訂按鍵系結都會呼叫上述其中一項功能，例如</span><span class="sxs-lookup"><span data-stu-id="68707-768">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="68707-769">您可以將 ScriptBlock 系結至索引鍵。</span><span class="sxs-lookup"><span data-stu-id="68707-769">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="68707-770">ScriptBlock 可以進行任何您想要的動作。</span><span class="sxs-lookup"><span data-stu-id="68707-770">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="68707-771">一些實用的範例包括</span><span class="sxs-lookup"><span data-stu-id="68707-771">Some useful examples include</span></span>

- <span data-ttu-id="68707-772">編輯命令行</span><span class="sxs-lookup"><span data-stu-id="68707-772">edit the command line</span></span>
- <span data-ttu-id="68707-773">開啟新視窗 (例如說明) </span><span class="sxs-lookup"><span data-stu-id="68707-773">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="68707-774">變更目錄而不變更命令列</span><span class="sxs-lookup"><span data-stu-id="68707-774">change directories without changing the command line</span></span>

<span data-ttu-id="68707-775">ScriptBlock 會收到兩個引數：</span><span class="sxs-lookup"><span data-stu-id="68707-775">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="68707-776">`$key` -A **[ConsoleKeyInfo]** 物件，它是觸發自訂系結的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="68707-776">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="68707-777">如果您將相同的 ScriptBlock 系結至多個金鑰，且需要根據金鑰執行不同的動作，您可以檢查 $key。</span><span class="sxs-lookup"><span data-stu-id="68707-777">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="68707-778">許多自訂系結會忽略此引數。</span><span class="sxs-lookup"><span data-stu-id="68707-778">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="68707-779">`$arg` -任意引數。</span><span class="sxs-lookup"><span data-stu-id="68707-779">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="68707-780">通常，這會是使用者從索引鍵系結 DigitArgument 傳遞的整數引數。</span><span class="sxs-lookup"><span data-stu-id="68707-780">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="68707-781">如果您的系結不接受引數，則可以合理地忽略此引數。</span><span class="sxs-lookup"><span data-stu-id="68707-781">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="68707-782">讓我們看看將命令列新增至歷程記錄，而不執行的範例。</span><span class="sxs-lookup"><span data-stu-id="68707-782">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="68707-783">當您知道您忘了進行某個動作，但不想重新輸入您已經輸入的命令列時，這會很有用。</span><span class="sxs-lookup"><span data-stu-id="68707-783">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

```powershell
$parameters = @{
    Key = 'Alt+w'
    BriefDescription = 'SaveInHistory'
    LongDescription = 'Save current line in history but do not execute'
    ScriptBlock = {
      param($key, $arg)   # The arguments are ignored in this example

      # GetBufferState gives us the command line (with the cursor position)
      $line = $null
      $cursor = $null
      [Microsoft.PowerShell.PSConsoleReadLine]::GetBufferState([ref]$line,
        [ref]$cursor)

      # AddToHistory saves the line in history, but does not execute it.
      [Microsoft.PowerShell.PSConsoleReadLine]::AddToHistory($line)

      # RevertLine is like pressing Escape.
      [Microsoft.PowerShell.PSConsoleReadLine]::RevertLine()
  }
}
Set-PSReadLineKeyHandler @parameters
```

<span data-ttu-id="68707-784">您可以在檔案中看到許多在 `SamplePSReadLineProfile.ps1` PSReadLine 模組資料夾中安裝的範例。</span><span class="sxs-lookup"><span data-stu-id="68707-784">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="68707-785">大部分的按鍵系結都會使用一些 helper 函數來編輯命令行。</span><span class="sxs-lookup"><span data-stu-id="68707-785">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="68707-786">這些 Api 記載于下一節。</span><span class="sxs-lookup"><span data-stu-id="68707-786">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="68707-787">自訂金鑰系結支援 Api</span><span class="sxs-lookup"><span data-stu-id="68707-787">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="68707-788">下列函式在 PSConsoleReadLine 中是公用的，但不能直接系結至索引鍵。</span><span class="sxs-lookup"><span data-stu-id="68707-788">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="68707-789">大部分在自訂金鑰系結中都很有用。</span><span class="sxs-lookup"><span data-stu-id="68707-789">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="68707-790">將命令列新增至歷程記錄，而不加以執行。</span><span class="sxs-lookup"><span data-stu-id="68707-790">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="68707-791">清除終止環形。</span><span class="sxs-lookup"><span data-stu-id="68707-791">Clear the kill-ring.</span></span>  <span data-ttu-id="68707-792">這大多用於測試。</span><span class="sxs-lookup"><span data-stu-id="68707-792">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="68707-793">從開始刪除長度字元。</span><span class="sxs-lookup"><span data-stu-id="68707-793">Delete length characters from start.</span></span>  <span data-ttu-id="68707-794">這種作業支援復原/重做。</span><span class="sxs-lookup"><span data-stu-id="68707-794">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="68707-795">根據使用者喜好設定來執行 Ding 動作。</span><span class="sxs-lookup"><span data-stu-id="68707-795">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="68707-796">這兩個函式會取出輸入緩衝區目前狀態的相關實用資訊。</span><span class="sxs-lookup"><span data-stu-id="68707-796">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="68707-797">第一個較常用於簡單的案例。</span><span class="sxs-lookup"><span data-stu-id="68707-797">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="68707-798">如果您的系結使用 Ast 更先進地執行，則會使用第二個。</span><span class="sxs-lookup"><span data-stu-id="68707-798">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

```

<span data-ttu-id="68707-799">Get-PSReadLineKeyHandler 使用這個函式，而且在自訂按鍵系結中可能不實用。</span><span class="sxs-lookup"><span data-stu-id="68707-799">This function is used by Get-PSReadLineKeyHandler and probably isn't useful in a custom key binding.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="68707-800">Get-PSReadLineOption 使用這個函式，而且在自訂索引鍵系結中可能不太實用。</span><span class="sxs-lookup"><span data-stu-id="68707-800">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="68707-801">如果未在命令列上選取任何專案，則會以開始和長度傳回-1。</span><span class="sxs-lookup"><span data-stu-id="68707-801">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="68707-802">如果在命令列上有選取專案，則會傳回選取範圍的開始和長度。</span><span class="sxs-lookup"><span data-stu-id="68707-802">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="68707-803">在游標處插入字元或字串。</span><span class="sxs-lookup"><span data-stu-id="68707-803">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="68707-804">這種作業支援復原/重做。</span><span class="sxs-lookup"><span data-stu-id="68707-804">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="68707-805">這是要 PSReadLine 的主要進入點。</span><span class="sxs-lookup"><span data-stu-id="68707-805">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="68707-806">它不支援遞迴，因此在自訂索引鍵系結中並不有用。</span><span class="sxs-lookup"><span data-stu-id="68707-806">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="68707-807">Remove-PSReadLineKeyHandler 使用這個函式，而且在自訂索引鍵系結中可能不太實用。</span><span class="sxs-lookup"><span data-stu-id="68707-807">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="68707-808">取代部分輸入。</span><span class="sxs-lookup"><span data-stu-id="68707-808">Replace some of the input.</span></span> <span data-ttu-id="68707-809">這種作業支援復原/重做。</span><span class="sxs-lookup"><span data-stu-id="68707-809">This operation supports undo/redo.</span></span> <span data-ttu-id="68707-810">這是優先于 Delete，後面接著 Insert，因為它會被視為復原的單一動作。</span><span class="sxs-lookup"><span data-stu-id="68707-810">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="68707-811">將游標移至指定的位移。</span><span class="sxs-lookup"><span data-stu-id="68707-811">Move the cursor to the given offset.</span></span> <span data-ttu-id="68707-812">不追蹤資料指標移動以進行復原。</span><span class="sxs-lookup"><span data-stu-id="68707-812">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="68707-813">此函式是 Cmdlet PSReadLineOption 所使用的 helper 方法，但對於想要暫時變更設定的自訂按鍵系結來說可能很有用。</span><span class="sxs-lookup"><span data-stu-id="68707-813">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="68707-814">此 helper 方法是用於接受 DigitArgument 的自訂系結。</span><span class="sxs-lookup"><span data-stu-id="68707-814">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="68707-815">一般呼叫看起來像</span><span class="sxs-lookup"><span data-stu-id="68707-815">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="note"></a><span data-ttu-id="68707-816">注意</span><span class="sxs-lookup"><span data-stu-id="68707-816">NOTE</span></span>

### <a name="powershell-compatibility"></a><span data-ttu-id="68707-817">POWERSHELL 相容性</span><span class="sxs-lookup"><span data-stu-id="68707-817">POWERSHELL COMPATIBILITY</span></span>

<span data-ttu-id="68707-818">PSReadLine 需要 PowerShell 3.0 或更新版本，以及主控台主機。</span><span class="sxs-lookup"><span data-stu-id="68707-818">PSReadLine requires PowerShell 3.0, or newer, and the console host.</span></span> <span data-ttu-id="68707-819">它無法在 PowerShell ISE 中運作。</span><span class="sxs-lookup"><span data-stu-id="68707-819">It does not work in PowerShell ISE.</span></span> <span data-ttu-id="68707-820">它會在 Visual Studio Code 的主控台中運作。</span><span class="sxs-lookup"><span data-stu-id="68707-820">It does work in the console of Visual Studio Code.</span></span>

### <a name="command-history"></a><span data-ttu-id="68707-821">命令歷程記錄</span><span class="sxs-lookup"><span data-stu-id="68707-821">COMMAND HISTORY</span></span>

<span data-ttu-id="68707-822">PSReadLine 會維護一個記錄檔，其中包含您從命令列輸入的所有命令和資料。</span><span class="sxs-lookup"><span data-stu-id="68707-822">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="68707-823">這可能包含機密資料，包括密碼。</span><span class="sxs-lookup"><span data-stu-id="68707-823">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="68707-824">例如，如果您使用指令 `ConvertTo-SecureString` 程式，密碼就會以純文字的形式記錄在記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="68707-824">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="68707-825">記錄檔是名為的檔案 `$($host.Name)_history.txt` 。</span><span class="sxs-lookup"><span data-stu-id="68707-825">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="68707-826">在 Windows 系統上，歷程記錄檔案會儲存在中 `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` 。</span><span class="sxs-lookup"><span data-stu-id="68707-826">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span> <span data-ttu-id="68707-827">在非 Windows 系統上，記錄檔會儲存在 `$env:XDG_DATA_HOME/powershell/PSReadLine` 或 `$env:HOME/.local/share/powershell/PSReadLine` 。</span><span class="sxs-lookup"><span data-stu-id="68707-827">On non-Windows systems, the history files is stored at `$env:XDG_DATA_HOME/powershell/PSReadLine` or `$env:HOME/.local/share/powershell/PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="68707-828">意見反應 & 參與 PSReadLine</span><span class="sxs-lookup"><span data-stu-id="68707-828">FEEDBACK & CONTRIBUTING TO PSReadLine</span></span>

[<span data-ttu-id="68707-829">GitHub 上的 PSReadLine</span><span class="sxs-lookup"><span data-stu-id="68707-829">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="68707-830">您可以隨時提交提取要求或在 GitHub 頁面上提交意見反應。</span><span class="sxs-lookup"><span data-stu-id="68707-830">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="68707-831">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68707-831">SEE ALSO</span></span>

<span data-ttu-id="68707-832">PSReadLine 會受到 GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) 程式庫的高度影響。</span><span class="sxs-lookup"><span data-stu-id="68707-832">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>
