---
description: PSReadLine 在 PowerShell 主控台中提供改良的命令列編輯體驗。
keywords: powershell
Locale: en-US
ms.date: 02/10/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 關於 PSReadLine
ms.openlocfilehash: ad6e85a30f866cb332c89a4c36f42231f511f5ae
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208747"
---
# <a name="psreadline"></a><span data-ttu-id="504a9-104">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="504a9-104">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="504a9-105">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="504a9-105">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="504a9-106">簡短描述</span><span class="sxs-lookup"><span data-stu-id="504a9-106">SHORT DESCRIPTION</span></span>

<span data-ttu-id="504a9-107">PSReadLine 在 PowerShell 主控台中提供改良的命令列編輯體驗。</span><span class="sxs-lookup"><span data-stu-id="504a9-107">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="504a9-108">詳細描述</span><span class="sxs-lookup"><span data-stu-id="504a9-108">LONG DESCRIPTION</span></span>

<span data-ttu-id="504a9-109">PSReadLine 2.0 為 PowerShell 主控台提供功能強大的命令列編輯體驗。</span><span class="sxs-lookup"><span data-stu-id="504a9-109">PSReadLine 2.0 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="504a9-110">它提供：</span><span class="sxs-lookup"><span data-stu-id="504a9-110">It provides:</span></span>

- <span data-ttu-id="504a9-111">命令列的語法著色</span><span class="sxs-lookup"><span data-stu-id="504a9-111">Syntax coloring of the command line</span></span>
- <span data-ttu-id="504a9-112">語法錯誤的視覺指示</span><span class="sxs-lookup"><span data-stu-id="504a9-112">A visual indication of syntax errors</span></span>
- <span data-ttu-id="504a9-113"> (編輯和歷程記錄的更佳多行體驗) </span><span class="sxs-lookup"><span data-stu-id="504a9-113">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="504a9-114">可自訂的按鍵系結</span><span class="sxs-lookup"><span data-stu-id="504a9-114">Customizable key bindings</span></span>
- <span data-ttu-id="504a9-115">Cmd 和 Emacs 模式</span><span class="sxs-lookup"><span data-stu-id="504a9-115">Cmd and Emacs modes</span></span>
- <span data-ttu-id="504a9-116">許多設定選項</span><span class="sxs-lookup"><span data-stu-id="504a9-116">Many configuration options</span></span>
- <span data-ttu-id="504a9-117">Bash 樣式完成 (在 Cmd 模式中為選擇性，預設為 Emacs 模式) </span><span class="sxs-lookup"><span data-stu-id="504a9-117">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="504a9-118">Emacs yank/kill-環形</span><span class="sxs-lookup"><span data-stu-id="504a9-118">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="504a9-119">以 PowerShell 權杖為基礎的「單字」移動和終止</span><span class="sxs-lookup"><span data-stu-id="504a9-119">PowerShell token based "word" movement and kill</span></span>

<span data-ttu-id="504a9-120">下列函式可在類別 **[PSConsoleReadLine]** 中使用。</span><span class="sxs-lookup"><span data-stu-id="504a9-120">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]** .</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="504a9-121">基本編輯函數</span><span class="sxs-lookup"><span data-stu-id="504a9-121">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="504a9-122">中止</span><span class="sxs-lookup"><span data-stu-id="504a9-122">Abort</span></span>

<span data-ttu-id="504a9-123">中止目前的動作，例如累加式歷程記錄搜尋。</span><span class="sxs-lookup"><span data-stu-id="504a9-123">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="504a9-124">Emacs： `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="504a9-124">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="504a9-125">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="504a9-125">AcceptAndGetNext</span></span>

<span data-ttu-id="504a9-126">嘗試執行目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="504a9-126">Attempt to execute the current input.</span></span> <span data-ttu-id="504a9-127">如果可以像 AcceptLine) 一樣執行 (，則會在下一次呼叫 ReadLine 時，重新叫用歷程記錄中的下一個專案。</span><span class="sxs-lookup"><span data-stu-id="504a9-127">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="504a9-128">Emacs： `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="504a9-128">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="504a9-129">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="504a9-129">AcceptLine</span></span>

<span data-ttu-id="504a9-130">嘗試執行目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="504a9-130">Attempt to execute the current input.</span></span> <span data-ttu-id="504a9-131">如果目前的輸入不完整 (例如遺漏右括弧、方括弧或引號，則接續提示會顯示在下一行，而 PSReadLine 會等候按鍵編輯目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="504a9-131">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="504a9-132">Cmd： `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="504a9-132">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="504a9-133">Emacs： `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="504a9-133">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="504a9-134">Vi 插入模式： `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="504a9-134">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="504a9-135">AddLine</span><span class="sxs-lookup"><span data-stu-id="504a9-135">AddLine</span></span>

<span data-ttu-id="504a9-136">接續提示會顯示在下一行，而 PSReadLine 會等候按鍵編輯目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="504a9-136">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="504a9-137">這對於將多行輸入輸入為單一命令很有用，即使單一行本身已完成輸入也是一樣。</span><span class="sxs-lookup"><span data-stu-id="504a9-137">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="504a9-138">Cmd： `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="504a9-138">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="504a9-139">Emacs： `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="504a9-139">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="504a9-140">Vi 插入模式： `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="504a9-140">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="504a9-141">Vi 命令模式： `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="504a9-141">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="504a9-142">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="504a9-142">BackwardDeleteChar</span></span>

<span data-ttu-id="504a9-143">刪除游標之前的字元。</span><span class="sxs-lookup"><span data-stu-id="504a9-143">Delete the character before the cursor.</span></span>

- <span data-ttu-id="504a9-144">Cmd： `<Backspace>` ， `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="504a9-144">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="504a9-145">Emacs： `<Backspace>` 、 `<Ctrl+Backspace>` 、 `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="504a9-145">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="504a9-146">Vi 插入模式： `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="504a9-146">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="504a9-147">Vi 命令模式： `<X>` 、 `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="504a9-147">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="504a9-148">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="504a9-148">BackwardDeleteLine</span></span>

<span data-ttu-id="504a9-149">如同 BackwardKillLine-刪除從點到行首的文字，但不會將已刪除的文字放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="504a9-149">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="504a9-150">Cmd： `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="504a9-150">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="504a9-151">Vi 插入模式： `<Ctrl+u>` 、 `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="504a9-151">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="504a9-152">Vi 命令模式： `<Ctrl+u>` 、 `<Ctrl+Home>` 、 `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="504a9-152">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`, `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="504a9-153">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="504a9-153">BackwardDeleteWord</span></span>

<span data-ttu-id="504a9-154">刪除上一個字組。</span><span class="sxs-lookup"><span data-stu-id="504a9-154">Deletes the previous word.</span></span>

- <span data-ttu-id="504a9-155">Vi 命令模式： `<Ctrl+w>` 、 `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="504a9-155">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="504a9-156">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="504a9-156">BackwardKillLine</span></span>

<span data-ttu-id="504a9-157">清除輸入至資料指標開頭的輸入。</span><span class="sxs-lookup"><span data-stu-id="504a9-157">Clear the input from the start of the input to the cursor.</span></span> <span data-ttu-id="504a9-158">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="504a9-158">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="504a9-159">Emacs： `<Ctrl+u>` ， `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="504a9-159">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="504a9-160">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="504a9-160">BackwardKillWord</span></span>

<span data-ttu-id="504a9-161">清除從目前單字開頭到游標處的輸入。</span><span class="sxs-lookup"><span data-stu-id="504a9-161">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="504a9-162">如果游標在單字之間，則會從上一個單字開頭開始清除輸入至游標。</span><span class="sxs-lookup"><span data-stu-id="504a9-162">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="504a9-163">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="504a9-163">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="504a9-164">Cmd： `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="504a9-164">Cmd: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="504a9-165">Emacs： `<Alt+Backspace>` ， `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="504a9-165">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="504a9-166">Vi 插入模式： `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="504a9-166">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="504a9-167">Vi 命令模式： `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="504a9-167">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="504a9-168">CancelLine</span><span class="sxs-lookup"><span data-stu-id="504a9-168">CancelLine</span></span>

<span data-ttu-id="504a9-169">取消目前的輸入，將輸入保留在畫面上，但返回主機，以便再次評估提示。</span><span class="sxs-lookup"><span data-stu-id="504a9-169">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="504a9-170">Vi 插入模式： `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="504a9-170">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="504a9-171">Vi 命令模式： `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="504a9-171">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="504a9-172">複製</span><span class="sxs-lookup"><span data-stu-id="504a9-172">Copy</span></span>

<span data-ttu-id="504a9-173">將選取的區域複製到系統剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="504a9-173">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="504a9-174">如果未選取任何區域，請複製整行。</span><span class="sxs-lookup"><span data-stu-id="504a9-174">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="504a9-175">Cmd： `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="504a9-175">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="504a9-176">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="504a9-176">CopyOrCancelLine</span></span>

<span data-ttu-id="504a9-177">如果已選取文字，請複製到剪貼簿，否則請取消該行。</span><span class="sxs-lookup"><span data-stu-id="504a9-177">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="504a9-178">Cmd： `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="504a9-178">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="504a9-179">Emacs： `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="504a9-179">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="504a9-180">剪下</span><span class="sxs-lookup"><span data-stu-id="504a9-180">Cut</span></span>

<span data-ttu-id="504a9-181">刪除選取的區域，將已刪除的文字放入系統剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="504a9-181">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="504a9-182">Cmd： `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="504a9-182">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="504a9-183">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="504a9-183">DeleteChar</span></span>

<span data-ttu-id="504a9-184">刪除游標下的字元。</span><span class="sxs-lookup"><span data-stu-id="504a9-184">Delete the character under the cursor.</span></span>

- <span data-ttu-id="504a9-185">Cmd： `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="504a9-185">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="504a9-186">Emacs： `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="504a9-186">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="504a9-187">Vi 插入模式： `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="504a9-187">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="504a9-188">Vi 命令模式： `<Delete>` 、 `<x>` 、 `<d,l>` 、 `<d,Space>`</span><span class="sxs-lookup"><span data-stu-id="504a9-188">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Space>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="504a9-189">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="504a9-189">DeleteCharOrExit</span></span>

<span data-ttu-id="504a9-190">刪除游標下的字元，如果行是空的，請結束進程。</span><span class="sxs-lookup"><span data-stu-id="504a9-190">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="504a9-191">Emacs： `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="504a9-191">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="504a9-192">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="504a9-192">DeleteEndOfWord</span></span>

<span data-ttu-id="504a9-193">刪除到字尾。</span><span class="sxs-lookup"><span data-stu-id="504a9-193">Delete to the end of the word.</span></span>

- <span data-ttu-id="504a9-194">Vi 命令模式： `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="504a9-194">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="504a9-195">DeleteLine</span><span class="sxs-lookup"><span data-stu-id="504a9-195">DeleteLine</span></span>

<span data-ttu-id="504a9-196">刪除目前的行，並啟用復原。</span><span class="sxs-lookup"><span data-stu-id="504a9-196">Deletes the current line, enabling undo.</span></span>

- <span data-ttu-id="504a9-197">Vi 命令模式： `<d,d>`</span><span class="sxs-lookup"><span data-stu-id="504a9-197">Vi command mode: `<d,d>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="504a9-198">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="504a9-198">DeleteLineToFirstChar</span></span>

<span data-ttu-id="504a9-199">將游標的文字刪除到行的第一個非空白字元。</span><span class="sxs-lookup"><span data-stu-id="504a9-199">Deletes text from the cursor to the first non-blank character of the line.</span></span>

- <span data-ttu-id="504a9-200">Vi 命令模式： `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="504a9-200">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="504a9-201">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="504a9-201">DeleteToEnd</span></span>

<span data-ttu-id="504a9-202">刪除至行尾。</span><span class="sxs-lookup"><span data-stu-id="504a9-202">Delete to the end of the line.</span></span>

- <span data-ttu-id="504a9-203">Vi 命令模式： `<D>` 、 `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="504a9-203">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="504a9-204">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="504a9-204">DeleteWord</span></span>

<span data-ttu-id="504a9-205">刪除下一個字組。</span><span class="sxs-lookup"><span data-stu-id="504a9-205">Delete the next word.</span></span>

- <span data-ttu-id="504a9-206">Vi 命令模式： `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="504a9-206">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="504a9-207">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="504a9-207">ForwardDeleteLine</span></span>

<span data-ttu-id="504a9-208">如同 ForwardKillLine-刪除從點到行尾的文字，但不會將已刪除的文字放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="504a9-208">Like ForwardKillLine - deletes text from the point to the end of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="504a9-209">Cmd： `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="504a9-209">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="504a9-210">Vi 插入模式： `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="504a9-210">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="504a9-211">Vi 命令模式： `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="504a9-211">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="504a9-212">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="504a9-212">InsertLineAbove</span></span>

<span data-ttu-id="504a9-213">無論游標位於目前的行上，都會在目前的行上方建立新的空白行。</span><span class="sxs-lookup"><span data-stu-id="504a9-213">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="504a9-214">游標移至新行的開頭。</span><span class="sxs-lookup"><span data-stu-id="504a9-214">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="504a9-215">Cmd： `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="504a9-215">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="504a9-216">InsertLineBelow</span><span class="sxs-lookup"><span data-stu-id="504a9-216">InsertLineBelow</span></span>

<span data-ttu-id="504a9-217">目前的行下方會建立新的空白行，而不論游標在目前的行上。</span><span class="sxs-lookup"><span data-stu-id="504a9-217">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="504a9-218">游標移至新行的開頭。</span><span class="sxs-lookup"><span data-stu-id="504a9-218">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="504a9-219">Cmd： `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="504a9-219">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="504a9-220">InvertCase</span><span class="sxs-lookup"><span data-stu-id="504a9-220">InvertCase</span></span>

<span data-ttu-id="504a9-221">將目前字元的大小寫反轉，並移至下一個字元。</span><span class="sxs-lookup"><span data-stu-id="504a9-221">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="504a9-222">Vi 命令模式： `<~>`</span><span class="sxs-lookup"><span data-stu-id="504a9-222">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="504a9-223">KillLine</span><span class="sxs-lookup"><span data-stu-id="504a9-223">KillLine</span></span>

<span data-ttu-id="504a9-224">清除游標至輸入結尾的輸入。</span><span class="sxs-lookup"><span data-stu-id="504a9-224">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="504a9-225">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="504a9-225">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="504a9-226">Emacs： `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="504a9-226">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="504a9-227">KillRegion</span><span class="sxs-lookup"><span data-stu-id="504a9-227">KillRegion</span></span>

<span data-ttu-id="504a9-228">終止游標與標記之間的文字。</span><span class="sxs-lookup"><span data-stu-id="504a9-228">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="504a9-229">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="504a9-229">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="504a9-230">KillWord</span><span class="sxs-lookup"><span data-stu-id="504a9-230">KillWord</span></span>

<span data-ttu-id="504a9-231">清除游標到目前單字結尾的輸入。</span><span class="sxs-lookup"><span data-stu-id="504a9-231">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="504a9-232">如果游標在單字之間，則會從資料指標清除輸入至下一個單字的結尾。</span><span class="sxs-lookup"><span data-stu-id="504a9-232">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="504a9-233">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="504a9-233">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="504a9-234">Cmd： `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="504a9-234">Cmd: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="504a9-235">Emacs： `<Alt+d>` ， `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="504a9-235">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="504a9-236">Vi 插入模式： `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="504a9-236">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="504a9-237">Vi 命令模式： `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="504a9-237">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="504a9-238">貼上</span><span class="sxs-lookup"><span data-stu-id="504a9-238">Paste</span></span>

<span data-ttu-id="504a9-239">貼上系統剪貼簿中的文字。</span><span class="sxs-lookup"><span data-stu-id="504a9-239">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="504a9-240">Cmd： `<Ctrl+v>` ， `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="504a9-240">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="504a9-241">Vi 插入模式： `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="504a9-241">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="504a9-242">Vi 命令模式： `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="504a9-242">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="504a9-243">使用 **Paste** 函式時，剪貼簿緩衝區的整個內容會貼到 PSReadLine 的輸入緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="504a9-243">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="504a9-244">輸入緩衝區接著會傳遞至 PowerShell 剖析器。</span><span class="sxs-lookup"><span data-stu-id="504a9-244">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="504a9-245">使用主控台應用程式的 **按右鍵** [貼上] 方法貼上的輸入會一次複製到輸入緩衝區一個字元。</span><span class="sxs-lookup"><span data-stu-id="504a9-245">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="504a9-246">當換行字元時，輸入緩衝區會傳遞給剖析器。</span><span class="sxs-lookup"><span data-stu-id="504a9-246">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="504a9-247">因此，輸入會一次剖析一行。</span><span class="sxs-lookup"><span data-stu-id="504a9-247">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="504a9-248">貼上方法之間的差異會導致不同的執行行為。</span><span class="sxs-lookup"><span data-stu-id="504a9-248">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="504a9-249">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="504a9-249">PasteAfter</span></span>

<span data-ttu-id="504a9-250">將剪貼簿貼到游標之後，將游標移至貼上文字的結尾。</span><span class="sxs-lookup"><span data-stu-id="504a9-250">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="504a9-251">Vi 命令模式： `<p>`</span><span class="sxs-lookup"><span data-stu-id="504a9-251">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="504a9-252">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="504a9-252">PasteBefore</span></span>

<span data-ttu-id="504a9-253">將剪貼簿貼到游標之前，將游標移至貼上文字的結尾。</span><span class="sxs-lookup"><span data-stu-id="504a9-253">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="504a9-254">Vi 命令模式： `<P>`</span><span class="sxs-lookup"><span data-stu-id="504a9-254">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="504a9-255">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="504a9-255">PrependAndAccept</span></span>

<span data-ttu-id="504a9-256">在前面加上 ' # ' 並接受該行。</span><span class="sxs-lookup"><span data-stu-id="504a9-256">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="504a9-257">Vi 命令模式： `<#>`</span><span class="sxs-lookup"><span data-stu-id="504a9-257">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="504a9-258">取消復原</span><span class="sxs-lookup"><span data-stu-id="504a9-258">Redo</span></span>

<span data-ttu-id="504a9-259">復原復原。</span><span class="sxs-lookup"><span data-stu-id="504a9-259">Undo an undo.</span></span>

- <span data-ttu-id="504a9-260">Cmd： `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="504a9-260">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="504a9-261">Vi 插入模式： `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="504a9-261">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="504a9-262">Vi 命令模式： `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="504a9-262">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="504a9-263">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="504a9-263">RepeatLastCommand</span></span>

<span data-ttu-id="504a9-264">重複上次修改文字。</span><span class="sxs-lookup"><span data-stu-id="504a9-264">Repeat the last text modification.</span></span>

- <span data-ttu-id="504a9-265">Vi 命令模式： `<.>`</span><span class="sxs-lookup"><span data-stu-id="504a9-265">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="504a9-266">RevertLine</span><span class="sxs-lookup"><span data-stu-id="504a9-266">RevertLine</span></span>

<span data-ttu-id="504a9-267">將所有輸入還原為目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="504a9-267">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="504a9-268">Cmd： `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="504a9-268">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="504a9-269">Emacs： `<Alt+r>` ， `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="504a9-269">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="504a9-270">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="504a9-270">ShellBackwardKillWord</span></span>

<span data-ttu-id="504a9-271">清除從目前單字開頭到游標處的輸入。</span><span class="sxs-lookup"><span data-stu-id="504a9-271">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="504a9-272">如果游標在單字之間，則會從上一個單字開頭開始清除輸入至游標。</span><span class="sxs-lookup"><span data-stu-id="504a9-272">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="504a9-273">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="504a9-273">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="504a9-274">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="504a9-274">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="504a9-275">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="504a9-275">ShellKillWord</span></span>

<span data-ttu-id="504a9-276">清除游標到目前單字結尾的輸入。</span><span class="sxs-lookup"><span data-stu-id="504a9-276">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="504a9-277">如果游標在單字之間，則會從資料指標清除輸入至下一個單字的結尾。</span><span class="sxs-lookup"><span data-stu-id="504a9-277">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="504a9-278">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="504a9-278">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="504a9-279">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="504a9-279">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="504a9-280">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="504a9-280">SwapCharacters</span></span>

<span data-ttu-id="504a9-281">交換目前的字元和前一個字元。</span><span class="sxs-lookup"><span data-stu-id="504a9-281">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="504a9-282">Emacs： `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="504a9-282">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="504a9-283">Vi 插入模式： `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="504a9-283">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="504a9-284">Vi 命令模式： `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="504a9-284">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="504a9-285">復原</span><span class="sxs-lookup"><span data-stu-id="504a9-285">Undo</span></span>

<span data-ttu-id="504a9-286">復原先前的編輯。</span><span class="sxs-lookup"><span data-stu-id="504a9-286">Undo a previous edit.</span></span>

- <span data-ttu-id="504a9-287">Cmd： `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="504a9-287">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="504a9-288">Emacs： `<Ctrl+_>` ， `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="504a9-288">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="504a9-289">Vi 插入模式： `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="504a9-289">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="504a9-290">Vi 命令模式： `<Ctrl+z>` 、 `<u>`</span><span class="sxs-lookup"><span data-stu-id="504a9-290">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="504a9-291">UndoAll</span><span class="sxs-lookup"><span data-stu-id="504a9-291">UndoAll</span></span>

<span data-ttu-id="504a9-292">復原所有先前編輯的行。</span><span class="sxs-lookup"><span data-stu-id="504a9-292">Undo all previous edits for line.</span></span>

- <span data-ttu-id="504a9-293">Vi 命令模式： `<U>`</span><span class="sxs-lookup"><span data-stu-id="504a9-293">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="504a9-294">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="504a9-294">UnixWordRubout</span></span>

<span data-ttu-id="504a9-295">清除從目前單字開頭到游標處的輸入。</span><span class="sxs-lookup"><span data-stu-id="504a9-295">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="504a9-296">如果游標在單字之間，則會從上一個單字開頭開始清除輸入至游標。</span><span class="sxs-lookup"><span data-stu-id="504a9-296">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="504a9-297">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="504a9-297">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="504a9-298">Emacs： `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="504a9-298">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="504a9-299">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="504a9-299">ValidateAndAcceptLine</span></span>

<span data-ttu-id="504a9-300">嘗試執行目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="504a9-300">Attempt to execute the current input.</span></span> <span data-ttu-id="504a9-301">如果目前的輸入不完整 (例如遺漏右括弧、方括弧或引號，則接續提示會顯示在下一行，而 PSReadLine 會等候按鍵編輯目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="504a9-301">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="504a9-302">Emacs： `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="504a9-302">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="504a9-303">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="504a9-303">ViAcceptLine</span></span>

<span data-ttu-id="504a9-304">接受行並切換至插入模式。</span><span class="sxs-lookup"><span data-stu-id="504a9-304">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="504a9-305">Vi 命令模式： `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="504a9-305">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="504a9-306">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="504a9-306">ViAcceptLineOrExit</span></span>

<span data-ttu-id="504a9-307">如同 Emacs 模式中的 DeleteCharOrExit，但會接受行，而不是刪除字元。</span><span class="sxs-lookup"><span data-stu-id="504a9-307">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="504a9-308">Vi 插入模式： `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="504a9-308">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="504a9-309">Vi 命令模式： `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="504a9-309">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="504a9-310">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="504a9-310">ViAppendLine</span></span>

<span data-ttu-id="504a9-311">新行會插入目前的行下方。</span><span class="sxs-lookup"><span data-stu-id="504a9-311">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="504a9-312">Vi 命令模式： `<o>`</span><span class="sxs-lookup"><span data-stu-id="504a9-312">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="504a9-313">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="504a9-313">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="504a9-314">刪除先前的單字，只使用空白字元做為文字分隔符號。</span><span class="sxs-lookup"><span data-stu-id="504a9-314">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="504a9-315">Vi 命令模式： `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="504a9-315">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="504a9-316">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="504a9-316">ViBackwardGlob</span></span>

<span data-ttu-id="504a9-317">將游標移回上一個單字的開頭，只使用空白字元做為分隔符號。</span><span class="sxs-lookup"><span data-stu-id="504a9-317">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="504a9-318">Vi 命令模式： `<B>`</span><span class="sxs-lookup"><span data-stu-id="504a9-318">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="504a9-319">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="504a9-319">ViDeleteBrace</span></span>

<span data-ttu-id="504a9-320">尋找相符的括弧、括弧或方括弧，並刪除內的所有內容，包括括弧。</span><span class="sxs-lookup"><span data-stu-id="504a9-320">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="504a9-321">Vi 命令模式： `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="504a9-321">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="504a9-322">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="504a9-322">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="504a9-323">刪除到字尾。</span><span class="sxs-lookup"><span data-stu-id="504a9-323">Delete to the end of the word.</span></span>

- <span data-ttu-id="504a9-324">Vi 命令模式： `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="504a9-324">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="504a9-325">ViDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="504a9-325">ViDeleteGlob</span></span>

<span data-ttu-id="504a9-326">刪除下一個 glob (以空白字元分隔的單字) 。</span><span class="sxs-lookup"><span data-stu-id="504a9-326">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="504a9-327">Vi 命令模式： `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="504a9-327">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="504a9-328">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="504a9-328">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="504a9-329">刪除指定的字元。</span><span class="sxs-lookup"><span data-stu-id="504a9-329">Deletes until given character.</span></span>

- <span data-ttu-id="504a9-330">Vi 命令模式： `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="504a9-330">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="504a9-331">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="504a9-331">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="504a9-332">刪除指定的字元。</span><span class="sxs-lookup"><span data-stu-id="504a9-332">Deletes until given character.</span></span>

- <span data-ttu-id="504a9-333">Vi 命令模式： `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="504a9-333">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="504a9-334">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="504a9-334">ViDeleteToChar</span></span>

<span data-ttu-id="504a9-335">刪除指定的字元。</span><span class="sxs-lookup"><span data-stu-id="504a9-335">Deletes until given character.</span></span>

- <span data-ttu-id="504a9-336">Vi 命令模式： `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="504a9-336">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="504a9-337">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="504a9-337">ViDeleteToCharBackward</span></span>

<span data-ttu-id="504a9-338">在指定的字元之前反向刪除。</span><span class="sxs-lookup"><span data-stu-id="504a9-338">Deletes backwards until given character.</span></span>

- <span data-ttu-id="504a9-339">Vi 命令模式： `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="504a9-339">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="504a9-340">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="504a9-340">ViInsertAtBegining</span></span>

<span data-ttu-id="504a9-341">切換至插入模式，並將游標放在行首。</span><span class="sxs-lookup"><span data-stu-id="504a9-341">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="504a9-342">Vi 命令模式： `<I>`</span><span class="sxs-lookup"><span data-stu-id="504a9-342">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="504a9-343">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="504a9-343">ViInsertAtEnd</span></span>

<span data-ttu-id="504a9-344">切換至插入模式，並將游標放在行尾。</span><span class="sxs-lookup"><span data-stu-id="504a9-344">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="504a9-345">Vi 命令模式： `<A>`</span><span class="sxs-lookup"><span data-stu-id="504a9-345">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="504a9-346">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="504a9-346">ViInsertLine</span></span>

<span data-ttu-id="504a9-347">新的行會插入到目前這一行的上方。</span><span class="sxs-lookup"><span data-stu-id="504a9-347">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="504a9-348">Vi 命令模式： `<O>`</span><span class="sxs-lookup"><span data-stu-id="504a9-348">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="504a9-349">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="504a9-349">ViInsertWithAppend</span></span>

<span data-ttu-id="504a9-350">從目前的行位置附加。</span><span class="sxs-lookup"><span data-stu-id="504a9-350">Append from the current line position.</span></span>

- <span data-ttu-id="504a9-351">Vi 命令模式： `<a>`</span><span class="sxs-lookup"><span data-stu-id="504a9-351">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="504a9-352">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="504a9-352">ViInsertWithDelete</span></span>

<span data-ttu-id="504a9-353">刪除目前的字元並切換至插入模式。</span><span class="sxs-lookup"><span data-stu-id="504a9-353">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="504a9-354">Vi 命令模式： `<s>`</span><span class="sxs-lookup"><span data-stu-id="504a9-354">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="504a9-355">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="504a9-355">ViJoinLines</span></span>

<span data-ttu-id="504a9-356">加入目前的行和下一行。</span><span class="sxs-lookup"><span data-stu-id="504a9-356">Joins the current line and the next line.</span></span>

- <span data-ttu-id="504a9-357">Vi 命令模式： `<J>`</span><span class="sxs-lookup"><span data-stu-id="504a9-357">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="504a9-358">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="504a9-358">ViReplaceLine</span></span>

<span data-ttu-id="504a9-359">清除整個命令列。</span><span class="sxs-lookup"><span data-stu-id="504a9-359">Erase the entire command line.</span></span>

- <span data-ttu-id="504a9-360">Vi 命令模式： `<S>` 、 `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="504a9-360">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="504a9-361">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="504a9-361">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="504a9-362">取代指定的字元。</span><span class="sxs-lookup"><span data-stu-id="504a9-362">Replaces until given character.</span></span>

- <span data-ttu-id="504a9-363">Vi 命令模式： `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="504a9-363">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="504a9-364">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="504a9-364">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="504a9-365">取代指定的字元。</span><span class="sxs-lookup"><span data-stu-id="504a9-365">Replaces until given character.</span></span>

- <span data-ttu-id="504a9-366">Vi 命令模式： `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="504a9-366">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="504a9-367">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="504a9-367">ViReplaceToChar</span></span>

<span data-ttu-id="504a9-368">刪除指定的字元。</span><span class="sxs-lookup"><span data-stu-id="504a9-368">Deletes until given character.</span></span>

- <span data-ttu-id="504a9-369">Vi 命令模式： `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="504a9-369">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="504a9-370">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="504a9-370">ViReplaceToCharBackward</span></span>

<span data-ttu-id="504a9-371">取代指定的字元。</span><span class="sxs-lookup"><span data-stu-id="504a9-371">Replaces until given character.</span></span>

- <span data-ttu-id="504a9-372">Vi 命令模式： `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="504a9-372">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="504a9-373">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="504a9-373">ViYankBeginningOfLine</span></span>

<span data-ttu-id="504a9-374">從緩衝區開頭 Yank 至資料指標。</span><span class="sxs-lookup"><span data-stu-id="504a9-374">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="504a9-375">Vi 命令模式： `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="504a9-375">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="504a9-376">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="504a9-376">ViYankEndOfGlob</span></span>

<span data-ttu-id="504a9-377">從資料指標 Yank 至 WORD (s) 的結尾。</span><span class="sxs-lookup"><span data-stu-id="504a9-377">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="504a9-378">Vi 命令模式： `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="504a9-378">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="504a9-379">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="504a9-379">ViYankEndOfWord</span></span>

<span data-ttu-id="504a9-380">從資料指標 Yank 至 word (s) 的結尾。</span><span class="sxs-lookup"><span data-stu-id="504a9-380">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="504a9-381">Vi 命令模式： `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="504a9-381">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="504a9-382">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="504a9-382">ViYankLeft</span></span>

<span data-ttu-id="504a9-383">Yank 字元 (s) 到游標的左邊。</span><span class="sxs-lookup"><span data-stu-id="504a9-383">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="504a9-384">Vi 命令模式： `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="504a9-384">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="504a9-385">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="504a9-385">ViYankLine</span></span>

<span data-ttu-id="504a9-386">Yank 整個緩衝區。</span><span class="sxs-lookup"><span data-stu-id="504a9-386">Yank the entire buffer.</span></span>

- <span data-ttu-id="504a9-387">Vi 命令模式： `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="504a9-387">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="504a9-388">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="504a9-388">ViYankNextGlob</span></span>

<span data-ttu-id="504a9-389">從資料指標 Yank 至下一個單字的開頭 (s) 。</span><span class="sxs-lookup"><span data-stu-id="504a9-389">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="504a9-390">Vi 命令模式： `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="504a9-390">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="504a9-391">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="504a9-391">ViYankNextWord</span></span>

<span data-ttu-id="504a9-392">Yank) 在游標之後 (s 的單字。</span><span class="sxs-lookup"><span data-stu-id="504a9-392">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="504a9-393">Vi 命令模式： `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="504a9-393">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="504a9-394">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="504a9-394">ViYankPercent</span></span>

<span data-ttu-id="504a9-395">Yank 至/從相符的括弧。</span><span class="sxs-lookup"><span data-stu-id="504a9-395">Yank to/from matching brace.</span></span>

- <span data-ttu-id="504a9-396">Vi 命令模式： `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="504a9-396">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="504a9-397">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="504a9-397">ViYankPreviousGlob</span></span>

<span data-ttu-id="504a9-398">從字組開頭 (s 的 Yank) 到資料指標。</span><span class="sxs-lookup"><span data-stu-id="504a9-398">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="504a9-399">Vi 命令模式： `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="504a9-399">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="504a9-400">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="504a9-400">ViYankPreviousWord</span></span>

<span data-ttu-id="504a9-401">Yank) 在游標之前的文字 (s。</span><span class="sxs-lookup"><span data-stu-id="504a9-401">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="504a9-402">Vi 命令模式： `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="504a9-402">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="504a9-403">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="504a9-403">ViYankRight</span></span>

<span data-ttu-id="504a9-404">Yank 字元 (s) 在游標右邊和右邊。</span><span class="sxs-lookup"><span data-stu-id="504a9-404">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="504a9-405">Vi 命令模式： `<y,l>` 、 `<y,Space>`</span><span class="sxs-lookup"><span data-stu-id="504a9-405">Vi command mode: `<y,l>`, `<y,Space>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="504a9-406">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="504a9-406">ViYankToEndOfLine</span></span>

<span data-ttu-id="504a9-407">從資料指標 Yank 至緩衝區的結尾。</span><span class="sxs-lookup"><span data-stu-id="504a9-407">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="504a9-408">Vi 命令模式： `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="504a9-408">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="504a9-409">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="504a9-409">ViYankToFirstChar</span></span>

<span data-ttu-id="504a9-410">從第一個非空白字元 Yank 至游標。</span><span class="sxs-lookup"><span data-stu-id="504a9-410">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="504a9-411">Vi 命令模式： `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="504a9-411">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="504a9-412">美國 佬</span><span class="sxs-lookup"><span data-stu-id="504a9-412">Yank</span></span>

<span data-ttu-id="504a9-413">將最近終止的文字加入至輸入。</span><span class="sxs-lookup"><span data-stu-id="504a9-413">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="504a9-414">Emacs： `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="504a9-414">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="504a9-415">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="504a9-415">YankLastArg</span></span>

<span data-ttu-id="504a9-416">Yank 前一個歷程記錄行中的最後一個引數。</span><span class="sxs-lookup"><span data-stu-id="504a9-416">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="504a9-417">使用引數時，第一次叫用時，其行為就像 YankNthArg 一樣。</span><span class="sxs-lookup"><span data-stu-id="504a9-417">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="504a9-418">如果叫用多次，則改為逐一查看歷程記錄和 arg，將方向 (負反轉方向。 ) </span><span class="sxs-lookup"><span data-stu-id="504a9-418">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="504a9-419">Cmd： `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="504a9-419">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="504a9-420">Emacs： `<Alt+.>` 、 `<Alt+_>` 、 `<Escape,.>` 、 `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="504a9-420">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="504a9-421">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="504a9-421">YankNthArg</span></span>

<span data-ttu-id="504a9-422">從上一個歷程記錄行中 Yank 命令) 之後，第一個引數 (。</span><span class="sxs-lookup"><span data-stu-id="504a9-422">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="504a9-423">使用引數時，請 yank 第 n 個引數 (從 0) 開始，如果引數為負數，則從最後一個引數開始。</span><span class="sxs-lookup"><span data-stu-id="504a9-423">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="504a9-424">Emacs： `<Ctrl+Alt+y>` ， `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="504a9-424">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="504a9-425">YankPop</span><span class="sxs-lookup"><span data-stu-id="504a9-425">YankPop</span></span>

<span data-ttu-id="504a9-426">如果先前的作業是 Yank 或 YankPop，請將先前 yanked 的文字取代為終止環形中的下一個已取消文字。</span><span class="sxs-lookup"><span data-stu-id="504a9-426">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="504a9-427">Emacs： `<Alt+y>` ， `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="504a9-427">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="504a9-428">資料指標移動函數</span><span class="sxs-lookup"><span data-stu-id="504a9-428">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="504a9-429">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="504a9-429">BackwardChar</span></span>

<span data-ttu-id="504a9-430">將游標向左移動一個字元。</span><span class="sxs-lookup"><span data-stu-id="504a9-430">Move the cursor one character to the left.</span></span> <span data-ttu-id="504a9-431">這可能會將游標移至多行輸入的上一行。</span><span class="sxs-lookup"><span data-stu-id="504a9-431">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="504a9-432">Cmd： `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="504a9-432">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="504a9-433">Emacs： `<LeftArrow>` ， `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="504a9-433">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>
- <span data-ttu-id="504a9-434">Vi 插入模式： `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="504a9-434">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="504a9-435">Vi 命令模式： `<LeftArrow>` 、 `<Backspace>` 、 `<h>`</span><span class="sxs-lookup"><span data-stu-id="504a9-435">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="504a9-436">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="504a9-436">BackwardWord</span></span>

<span data-ttu-id="504a9-437">將游標移回目前單字的開頭，或將游標移回上一個單字開頭的單字。</span><span class="sxs-lookup"><span data-stu-id="504a9-437">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="504a9-438">單字界限是由一組可設定的字元所定義。</span><span class="sxs-lookup"><span data-stu-id="504a9-438">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="504a9-439">Cmd： `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="504a9-439">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="504a9-440">Emacs： `<Alt+b>` ， `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="504a9-440">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="504a9-441">Vi 插入模式： `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="504a9-441">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="504a9-442">Vi 命令模式： `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="504a9-442">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="504a9-443">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="504a9-443">BeginningOfLine</span></span>

<span data-ttu-id="504a9-444">如果輸入有多行，請移至目前行的開頭，如果已經在行首，則移至輸入的開頭。</span><span class="sxs-lookup"><span data-stu-id="504a9-444">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="504a9-445">如果輸入具有單一行，請移至輸入的開頭。</span><span class="sxs-lookup"><span data-stu-id="504a9-445">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="504a9-446">Cmd： `<Home>`</span><span class="sxs-lookup"><span data-stu-id="504a9-446">Cmd: `<Home>`</span></span>
- <span data-ttu-id="504a9-447">Emacs： `<Home>` ， `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="504a9-447">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="504a9-448">Vi 插入模式： `<Home>`</span><span class="sxs-lookup"><span data-stu-id="504a9-448">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="504a9-449">Vi 命令模式： `<Home>`</span><span class="sxs-lookup"><span data-stu-id="504a9-449">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="504a9-450">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="504a9-450">EndOfLine</span></span>

<span data-ttu-id="504a9-451">如果輸入有多行，請移至目前行的結尾，如果已經在行尾，則移至輸入的結尾。</span><span class="sxs-lookup"><span data-stu-id="504a9-451">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="504a9-452">如果輸入具有單一行，請移至輸入的結尾。</span><span class="sxs-lookup"><span data-stu-id="504a9-452">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="504a9-453">Cmd： `<End>`</span><span class="sxs-lookup"><span data-stu-id="504a9-453">Cmd: `<End>`</span></span>
- <span data-ttu-id="504a9-454">Emacs： `<End>` ， `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="504a9-454">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="504a9-455">Vi 插入模式： `<End>`</span><span class="sxs-lookup"><span data-stu-id="504a9-455">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="504a9-456">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="504a9-456">ForwardChar</span></span>

<span data-ttu-id="504a9-457">將游標向右移動一個字元。</span><span class="sxs-lookup"><span data-stu-id="504a9-457">Move the cursor one character to the right.</span></span> <span data-ttu-id="504a9-458">這可能會將游標移至下一行的多行輸入。</span><span class="sxs-lookup"><span data-stu-id="504a9-458">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="504a9-459">Cmd： `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="504a9-459">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="504a9-460">Emacs： `<RightArrow>` ， `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="504a9-460">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>
- <span data-ttu-id="504a9-461">Vi 插入模式： `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="504a9-461">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="504a9-462">Vi 命令模式： `<RightArrow>` 、 `<Space>` 、 `<l>`</span><span class="sxs-lookup"><span data-stu-id="504a9-462">Vi command mode: `<RightArrow>`, `<Space>`, `<l>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="504a9-463">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="504a9-463">ForwardWord</span></span>

<span data-ttu-id="504a9-464">將游標向前移動至目前單字的結尾，或在文字之間移動到下一個單字的結尾。</span><span class="sxs-lookup"><span data-stu-id="504a9-464">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="504a9-465">單字界限是由一組可設定的字元所定義。</span><span class="sxs-lookup"><span data-stu-id="504a9-465">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="504a9-466">Emacs： `<Alt+f>` ， `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="504a9-466">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="504a9-467">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="504a9-467">GotoBrace</span></span>

<span data-ttu-id="504a9-468">移至相符的大括弧、括弧或方括弧。</span><span class="sxs-lookup"><span data-stu-id="504a9-468">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="504a9-469">Cmd： `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="504a9-469">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="504a9-470">Vi 插入模式： `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="504a9-470">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="504a9-471">Vi 命令模式： `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="504a9-471">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="504a9-472">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="504a9-472">GotoColumn</span></span>

<span data-ttu-id="504a9-473">移至 arg 所表示的資料行。</span><span class="sxs-lookup"><span data-stu-id="504a9-473">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="504a9-474">Vi 命令模式： `<|>`</span><span class="sxs-lookup"><span data-stu-id="504a9-474">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="504a9-475">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="504a9-475">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="504a9-476">將游標移至行中的第一個非空白字元。</span><span class="sxs-lookup"><span data-stu-id="504a9-476">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="504a9-477">Vi 命令模式： `<^>`</span><span class="sxs-lookup"><span data-stu-id="504a9-477">Vi command mode: `<^>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="504a9-478">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="504a9-478">MoveToEndOfLine</span></span>

<span data-ttu-id="504a9-479">將游標移至輸入的結尾。</span><span class="sxs-lookup"><span data-stu-id="504a9-479">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="504a9-480">Vi 命令模式： `<End>` 、 `<$>`</span><span class="sxs-lookup"><span data-stu-id="504a9-480">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="504a9-481">NextLine</span><span class="sxs-lookup"><span data-stu-id="504a9-481">NextLine</span></span>

<span data-ttu-id="504a9-482">將游標移至下一行。</span><span class="sxs-lookup"><span data-stu-id="504a9-482">Move the cursor to the next line.</span></span>

- <span data-ttu-id="504a9-483">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="504a9-483">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="504a9-484">NextWord</span><span class="sxs-lookup"><span data-stu-id="504a9-484">NextWord</span></span>

<span data-ttu-id="504a9-485">將游標向前移至下一個單字的開頭。</span><span class="sxs-lookup"><span data-stu-id="504a9-485">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="504a9-486">單字界限是由一組可設定的字元所定義。</span><span class="sxs-lookup"><span data-stu-id="504a9-486">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="504a9-487">Cmd： `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="504a9-487">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="504a9-488">Vi 插入模式： `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="504a9-488">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="504a9-489">Vi 命令模式： `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="504a9-489">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="504a9-490">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="504a9-490">NextWordEnd</span></span>

<span data-ttu-id="504a9-491">將游標向前移動至目前單字的結尾，或在文字之間移動到下一個單字的結尾。</span><span class="sxs-lookup"><span data-stu-id="504a9-491">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="504a9-492">單字界限是由一組可設定的字元所定義。</span><span class="sxs-lookup"><span data-stu-id="504a9-492">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="504a9-493">Vi 命令模式： `<e>`</span><span class="sxs-lookup"><span data-stu-id="504a9-493">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="504a9-494">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="504a9-494">PreviousLine</span></span>

<span data-ttu-id="504a9-495">將游標移至上一行。</span><span class="sxs-lookup"><span data-stu-id="504a9-495">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="504a9-496">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="504a9-496">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="504a9-497">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="504a9-497">ShellBackwardWord</span></span>

<span data-ttu-id="504a9-498">將游標移回目前單字的開頭，或將游標移回上一個單字開頭的單字。</span><span class="sxs-lookup"><span data-stu-id="504a9-498">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="504a9-499">單字界限是由 PowerShell 權杖所定義。</span><span class="sxs-lookup"><span data-stu-id="504a9-499">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="504a9-500">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="504a9-500">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="504a9-501">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="504a9-501">ShellForwardWord</span></span>

<span data-ttu-id="504a9-502">將游標向前移至下一個單字的開頭。</span><span class="sxs-lookup"><span data-stu-id="504a9-502">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="504a9-503">單字界限是由 PowerShell 權杖所定義。</span><span class="sxs-lookup"><span data-stu-id="504a9-503">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="504a9-504">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="504a9-504">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="504a9-505">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="504a9-505">ShellNextWord</span></span>

<span data-ttu-id="504a9-506">將游標向前移動至目前單字的結尾，或在文字之間移動到下一個單字的結尾。</span><span class="sxs-lookup"><span data-stu-id="504a9-506">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="504a9-507">單字界限是由 PowerShell 權杖所定義。</span><span class="sxs-lookup"><span data-stu-id="504a9-507">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="504a9-508">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="504a9-508">Function is unbound.</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="504a9-509">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="504a9-509">ViBackwardWord</span></span>

<span data-ttu-id="504a9-510">將游標移回目前單字的開頭，或將游標移回上一個單字開頭的單字。</span><span class="sxs-lookup"><span data-stu-id="504a9-510">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="504a9-511">單字界限是由一組可設定的字元所定義。</span><span class="sxs-lookup"><span data-stu-id="504a9-511">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="504a9-512">Vi 命令模式： `<b>`</span><span class="sxs-lookup"><span data-stu-id="504a9-512">Vi command mode: `<b>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="504a9-513">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="504a9-513">ViEndOfGlob</span></span>

<span data-ttu-id="504a9-514">將游標移至單字的結尾，只使用空白字元做為分隔符號。</span><span class="sxs-lookup"><span data-stu-id="504a9-514">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="504a9-515">Vi 命令模式： `<E>`</span><span class="sxs-lookup"><span data-stu-id="504a9-515">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="504a9-516">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="504a9-516">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="504a9-517">移至上一個單字的結尾，只使用空白字元做為單字分隔符號。</span><span class="sxs-lookup"><span data-stu-id="504a9-517">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="504a9-518">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="504a9-518">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="504a9-519">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="504a9-519">ViGotoBrace</span></span>

<span data-ttu-id="504a9-520">類似于 GotoBrace，但它是以字元為基礎，而不是以權杖為基礎。</span><span class="sxs-lookup"><span data-stu-id="504a9-520">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="504a9-521">Vi 命令模式： `<%>`</span><span class="sxs-lookup"><span data-stu-id="504a9-521">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="504a9-522">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="504a9-522">ViNextGlob</span></span>

<span data-ttu-id="504a9-523">移至下一個單字，只使用空白字元做為單字分隔符號。</span><span class="sxs-lookup"><span data-stu-id="504a9-523">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="504a9-524">Vi 命令模式： `<W>`</span><span class="sxs-lookup"><span data-stu-id="504a9-524">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="504a9-525">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="504a9-525">ViNextWord</span></span>

<span data-ttu-id="504a9-526">將游標向前移至下一個單字的開頭。</span><span class="sxs-lookup"><span data-stu-id="504a9-526">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="504a9-527">單字界限是由一組可設定的字元所定義。</span><span class="sxs-lookup"><span data-stu-id="504a9-527">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="504a9-528">Vi 命令模式： `<w>`</span><span class="sxs-lookup"><span data-stu-id="504a9-528">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="504a9-529">歷程記錄函數</span><span class="sxs-lookup"><span data-stu-id="504a9-529">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="504a9-530">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="504a9-530">BeginningOfHistory</span></span>

<span data-ttu-id="504a9-531">移至歷程記錄中的第一個專案。</span><span class="sxs-lookup"><span data-stu-id="504a9-531">Move to the first item in the history.</span></span>

- <span data-ttu-id="504a9-532">Emacs： `<Alt+`<>\`</span><span class="sxs-lookup"><span data-stu-id="504a9-532">Emacs: `<Alt+`<>\`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="504a9-533">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="504a9-533">ClearHistory</span></span>

<span data-ttu-id="504a9-534">清除 PSReadLine 中的歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="504a9-534">Clears history in PSReadLine.</span></span> <span data-ttu-id="504a9-535">這不會影響 PowerShell 歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="504a9-535">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="504a9-536">Cmd： `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="504a9-536">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="504a9-537">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="504a9-537">EndOfHistory</span></span>

<span data-ttu-id="504a9-538">移至記錄中目前輸入)  (的最後一個專案。</span><span class="sxs-lookup"><span data-stu-id="504a9-538">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="504a9-539">Emacs： `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="504a9-539">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="504a9-540">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="504a9-540">ForwardSearchHistory</span></span>

<span data-ttu-id="504a9-541">透過歷程記錄執行漸進式向前搜尋。</span><span class="sxs-lookup"><span data-stu-id="504a9-541">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="504a9-542">Cmd： `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="504a9-542">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="504a9-543">Emacs： `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="504a9-543">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="504a9-544">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="504a9-544">HistorySearchBackward</span></span>

<span data-ttu-id="504a9-545">將目前的輸入取代為 PSReadLine 記錄中與開始和輸入和資料指標之間的字元相符的 ' previous ' 專案。</span><span class="sxs-lookup"><span data-stu-id="504a9-545">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="504a9-546">Cmd： `<F8>`</span><span class="sxs-lookup"><span data-stu-id="504a9-546">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="504a9-547">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="504a9-547">HistorySearchForward</span></span>

<span data-ttu-id="504a9-548">將目前的輸入取代為 PSReadLine 記錄中與開始和輸入和資料指標之間的字元相符的 ' next ' 專案。</span><span class="sxs-lookup"><span data-stu-id="504a9-548">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="504a9-549">Cmd： `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="504a9-549">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="504a9-550">NextHistory</span><span class="sxs-lookup"><span data-stu-id="504a9-550">NextHistory</span></span>

<span data-ttu-id="504a9-551">將目前的輸入取代為 PSReadLine 記錄中的 ' next ' 專案。</span><span class="sxs-lookup"><span data-stu-id="504a9-551">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="504a9-552">Cmd： `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="504a9-552">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="504a9-553">Emacs： `<DownArrow>` ， `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="504a9-553">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="504a9-554">Vi 插入模式： `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="504a9-554">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="504a9-555">Vi 命令模式： `<DownArrow>` 、 `<j>` 、 `<+>`</span><span class="sxs-lookup"><span data-stu-id="504a9-555">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="504a9-556">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="504a9-556">PreviousHistory</span></span>

<span data-ttu-id="504a9-557">將目前的輸入取代為 PSReadLine 記錄中的 ' previous ' 專案。</span><span class="sxs-lookup"><span data-stu-id="504a9-557">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="504a9-558">Cmd： `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="504a9-558">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="504a9-559">Emacs： `<UpArrow>` ， `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="504a9-559">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="504a9-560">Vi 插入模式： `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="504a9-560">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="504a9-561">Vi 命令模式： `<UpArrow>` 、 `<k>` 、 `<->`</span><span class="sxs-lookup"><span data-stu-id="504a9-561">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="504a9-562">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="504a9-562">ReverseSearchHistory</span></span>

<span data-ttu-id="504a9-563">透過歷程記錄執行增量向前搜尋。</span><span class="sxs-lookup"><span data-stu-id="504a9-563">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="504a9-564">Cmd： `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="504a9-564">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="504a9-565">Emacs： `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="504a9-565">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="504a9-566">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="504a9-566">ViSearchHistoryBackward</span></span>

<span data-ttu-id="504a9-567">提示輸入搜尋字串，並在 AcceptLine 時起始搜尋。</span><span class="sxs-lookup"><span data-stu-id="504a9-567">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="504a9-568">Vi 插入模式： `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="504a9-568">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="504a9-569">Vi 命令模式： `</>` 、 `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="504a9-569">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="504a9-570">完成函式</span><span class="sxs-lookup"><span data-stu-id="504a9-570">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="504a9-571">完成</span><span class="sxs-lookup"><span data-stu-id="504a9-571">Complete</span></span>

<span data-ttu-id="504a9-572">嘗試對資料指標周圍的文字執行完成。</span><span class="sxs-lookup"><span data-stu-id="504a9-572">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="504a9-573">如果有多個可能的完成，則會使用最長的明確前置詞來完成。</span><span class="sxs-lookup"><span data-stu-id="504a9-573">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="504a9-574">如果嘗試完成最長的明確完成，則會顯示可能的完成清單。</span><span class="sxs-lookup"><span data-stu-id="504a9-574">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="504a9-575">Emacs： `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="504a9-575">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="504a9-576">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="504a9-576">MenuComplete</span></span>

<span data-ttu-id="504a9-577">嘗試對資料指標周圍的文字執行完成。</span><span class="sxs-lookup"><span data-stu-id="504a9-577">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="504a9-578">如果有多個可能的完成，則會使用最長的明確前置詞來完成。</span><span class="sxs-lookup"><span data-stu-id="504a9-578">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="504a9-579">如果嘗試完成最長的明確完成，則會顯示可能的完成清單。</span><span class="sxs-lookup"><span data-stu-id="504a9-579">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="504a9-580">Cmd： `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="504a9-580">Cmd: `<Ctrl+Space>`</span></span>
- <span data-ttu-id="504a9-581">Emacs： `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="504a9-581">Emacs: `<Ctrl+Space>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="504a9-582">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="504a9-582">PossibleCompletions</span></span>

<span data-ttu-id="504a9-583">顯示可能的完成清單。</span><span class="sxs-lookup"><span data-stu-id="504a9-583">Display the list of possible completions.</span></span>

- <span data-ttu-id="504a9-584">Emacs： `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="504a9-584">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="504a9-585">Vi 插入模式： `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="504a9-585">Vi insert mode: `<Ctrl+Space>`</span></span>
- <span data-ttu-id="504a9-586">Vi 命令模式： `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="504a9-586">Vi command mode: `<Ctrl+Space>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="504a9-587">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="504a9-587">TabCompleteNext</span></span>

<span data-ttu-id="504a9-588">嘗試使用下一個可用的完成來完成資料指標周圍的文字。</span><span class="sxs-lookup"><span data-stu-id="504a9-588">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="504a9-589">Cmd： `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="504a9-589">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="504a9-590">Vi 命令模式： `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="504a9-590">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="504a9-591">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="504a9-591">TabCompletePrevious</span></span>

<span data-ttu-id="504a9-592">嘗試使用先前的可用完成來完成資料指標周圍的文字。</span><span class="sxs-lookup"><span data-stu-id="504a9-592">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="504a9-593">Cmd： `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="504a9-593">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="504a9-594">Vi 命令模式： `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="504a9-594">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="504a9-595">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="504a9-595">ViTabCompleteNext</span></span>

<span data-ttu-id="504a9-596">視需要結束目前的編輯群組，並叫用 TabCompleteNext。</span><span class="sxs-lookup"><span data-stu-id="504a9-596">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="504a9-597">Vi 插入模式： `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="504a9-597">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="504a9-598">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="504a9-598">ViTabCompletePrevious</span></span>

<span data-ttu-id="504a9-599">視需要結束目前的編輯群組，並叫用 TabCompletePrevious。</span><span class="sxs-lookup"><span data-stu-id="504a9-599">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="504a9-600">Vi 插入模式： `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="504a9-600">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="504a9-601">其他函式</span><span class="sxs-lookup"><span data-stu-id="504a9-601">Miscellaneous functions</span></span>

### <a name="capturescreen"></a><span data-ttu-id="504a9-602">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="504a9-602">CaptureScreen</span></span>

<span data-ttu-id="504a9-603">啟動互動式螢幕擷取畫面-向上/向下箭號選取 [線條]，輸入將選取的文字複製到剪貼簿做為文字和 html。</span><span class="sxs-lookup"><span data-stu-id="504a9-603">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="504a9-604">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="504a9-604">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="504a9-605">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="504a9-605">ClearScreen</span></span>

<span data-ttu-id="504a9-606">清除畫面並在畫面頂端繪製目前的線。</span><span class="sxs-lookup"><span data-stu-id="504a9-606">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="504a9-607">Cmd： `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="504a9-607">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="504a9-608">Emacs： `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="504a9-608">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="504a9-609">Vi 插入模式： `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="504a9-609">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="504a9-610">Vi 命令模式： `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="504a9-610">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="504a9-611">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="504a9-611">DigitArgument</span></span>

<span data-ttu-id="504a9-612">開始新的數位引數以傳遞至其他函式。</span><span class="sxs-lookup"><span data-stu-id="504a9-612">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="504a9-613">Cmd： `<Alt+0>` 、 `<Alt+1>` 、 `<Alt+2>` 、 `<Alt+3>` 、 `<Alt+4>` 、 `<Alt+5>` 、 `<Alt+6>` `<Alt+7>` `<Alt+8>` `<Alt+9>` 、、、、、 `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="504a9-613">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="504a9-614">Emacs： `<Alt+0>` 、 `<Alt+1>` 、 `<Alt+2>` 、、、 `<Alt+3>` `<Alt+4>` `<Alt+5>` 、 `<Alt+6>` 、 `<Alt+7>` 、 `<Alt+8>` 、 `<Alt+9>` 、、 `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="504a9-614">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="504a9-615">Vi 命令模式： `<0>` 、 `<1>` 、 `<2>` 、 `<3>` 、 `<4>` 、 `<5>` 、 `<6>` `<7>` `<8>` 、、、、 `<9>`</span><span class="sxs-lookup"><span data-stu-id="504a9-615">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="504a9-616">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="504a9-616">InvokePrompt</span></span>

<span data-ttu-id="504a9-617">清除目前的提示，並呼叫 prompt 函式以重新顯示提示。</span><span class="sxs-lookup"><span data-stu-id="504a9-617">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="504a9-618">適用于變更狀態的自訂金鑰處理常式，例如變更目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="504a9-618">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="504a9-619">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="504a9-619">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="504a9-620">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="504a9-620">ScrollDisplayDown</span></span>

<span data-ttu-id="504a9-621">將顯示畫面向下移動一個畫面。</span><span class="sxs-lookup"><span data-stu-id="504a9-621">Scroll the display down one screen.</span></span>

- <span data-ttu-id="504a9-622">Cmd： `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="504a9-622">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="504a9-623">Emacs： `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="504a9-623">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="504a9-624">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="504a9-624">ScrollDisplayDownLine</span></span>

<span data-ttu-id="504a9-625">將向下移動一行。</span><span class="sxs-lookup"><span data-stu-id="504a9-625">Scroll the display down one line.</span></span>

- <span data-ttu-id="504a9-626">Cmd： `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="504a9-626">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="504a9-627">Emacs： `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="504a9-627">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="504a9-628">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="504a9-628">ScrollDisplayToCursor</span></span>

<span data-ttu-id="504a9-629">將顯示滾動至游標。</span><span class="sxs-lookup"><span data-stu-id="504a9-629">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="504a9-630">Emacs： `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="504a9-630">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="504a9-631">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="504a9-631">ScrollDisplayTop</span></span>

<span data-ttu-id="504a9-632">將顯示器向上方滾動。</span><span class="sxs-lookup"><span data-stu-id="504a9-632">Scroll the display to the top.</span></span>

- <span data-ttu-id="504a9-633">Emacs： `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="504a9-633">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="504a9-634">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="504a9-634">ScrollDisplayUp</span></span>

<span data-ttu-id="504a9-635">將顯示畫面向上移動一次。</span><span class="sxs-lookup"><span data-stu-id="504a9-635">Scroll the display up one screen.</span></span>

- <span data-ttu-id="504a9-636">Cmd： `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="504a9-636">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="504a9-637">Emacs： `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="504a9-637">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="504a9-638">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="504a9-638">ScrollDisplayUpLine</span></span>

<span data-ttu-id="504a9-639">將顯示畫面向下移動一行。</span><span class="sxs-lookup"><span data-stu-id="504a9-639">Scroll the display up one line.</span></span>

- <span data-ttu-id="504a9-640">Cmd： `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="504a9-640">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="504a9-641">Emacs： `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="504a9-641">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="504a9-642">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="504a9-642">SelfInsert</span></span>

<span data-ttu-id="504a9-643">插入金鑰。</span><span class="sxs-lookup"><span data-stu-id="504a9-643">Insert the key.</span></span>

- <span data-ttu-id="504a9-644">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="504a9-644">Function is unbound.</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="504a9-645">ShowKeyBindings</span><span class="sxs-lookup"><span data-stu-id="504a9-645">ShowKeyBindings</span></span>

<span data-ttu-id="504a9-646">顯示所有系結的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="504a9-646">Show all bound keys.</span></span>

- <span data-ttu-id="504a9-647">Cmd： `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="504a9-647">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="504a9-648">Emacs： `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="504a9-648">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="504a9-649">Vi 插入模式： `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="504a9-649">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="504a9-650">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="504a9-650">ViCommandMode</span></span>

<span data-ttu-id="504a9-651">將目前的作業模式從 Vi-Insert 切換至 Vi 命令。</span><span class="sxs-lookup"><span data-stu-id="504a9-651">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="504a9-652">Vi 插入模式： `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="504a9-652">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="504a9-653">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="504a9-653">ViDigitArgumentInChord</span></span>

<span data-ttu-id="504a9-654">開始新的數位引數，以傳遞至其他函式，而非 vi 的 chords 之一。</span><span class="sxs-lookup"><span data-stu-id="504a9-654">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="504a9-655">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="504a9-655">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="504a9-656">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="504a9-656">ViEditVisually</span></span>

<span data-ttu-id="504a9-657">在 [$env：編輯器] 或 [$env：視覺效果] 所指定的文字編輯器中編輯命令行。</span><span class="sxs-lookup"><span data-stu-id="504a9-657">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="504a9-658">Emacs： `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="504a9-658">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="504a9-659">Vi 命令模式： `<v>`</span><span class="sxs-lookup"><span data-stu-id="504a9-659">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="504a9-660">ViExit</span><span class="sxs-lookup"><span data-stu-id="504a9-660">ViExit</span></span>

<span data-ttu-id="504a9-661">離開 shell。</span><span class="sxs-lookup"><span data-stu-id="504a9-661">Exits the shell.</span></span>

- <span data-ttu-id="504a9-662">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="504a9-662">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="504a9-663">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="504a9-663">ViInsertMode</span></span>

<span data-ttu-id="504a9-664">切換至插入模式。</span><span class="sxs-lookup"><span data-stu-id="504a9-664">Switch to Insert mode.</span></span>

- <span data-ttu-id="504a9-665">Vi 命令模式： `<i>`</span><span class="sxs-lookup"><span data-stu-id="504a9-665">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="504a9-666">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="504a9-666">WhatIsKey</span></span>

<span data-ttu-id="504a9-667">讀取金鑰，並告訴我金鑰的系結目標。</span><span class="sxs-lookup"><span data-stu-id="504a9-667">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="504a9-668">Cmd： `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="504a9-668">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="504a9-669">Emacs： `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="504a9-669">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="504a9-670">選取函式</span><span class="sxs-lookup"><span data-stu-id="504a9-670">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="504a9-671">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="504a9-671">ExchangePointAndMark</span></span>

<span data-ttu-id="504a9-672">游標放在標記的位置，而標記會移至游標位置。</span><span class="sxs-lookup"><span data-stu-id="504a9-672">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="504a9-673">Emacs： `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="504a9-673">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="504a9-674">SelectAll</span><span class="sxs-lookup"><span data-stu-id="504a9-674">SelectAll</span></span>

<span data-ttu-id="504a9-675">選取整行。</span><span class="sxs-lookup"><span data-stu-id="504a9-675">Select the entire line.</span></span>

- <span data-ttu-id="504a9-676">Cmd： `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="504a9-676">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="504a9-677">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="504a9-677">SelectBackwardChar</span></span>

<span data-ttu-id="504a9-678">調整目前的選取範圍，以包含前一個字元。</span><span class="sxs-lookup"><span data-stu-id="504a9-678">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="504a9-679">Cmd： `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="504a9-679">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="504a9-680">Emacs： `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="504a9-680">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="504a9-681">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="504a9-681">SelectBackwardsLine</span></span>

<span data-ttu-id="504a9-682">調整目前的選取範圍，以包含從游標到行首的起點。</span><span class="sxs-lookup"><span data-stu-id="504a9-682">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="504a9-683">Cmd： `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="504a9-683">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="504a9-684">Emacs： `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="504a9-684">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="504a9-685">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="504a9-685">SelectBackwardWord</span></span>

<span data-ttu-id="504a9-686">調整目前的選取範圍，以包含前一個字組。</span><span class="sxs-lookup"><span data-stu-id="504a9-686">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="504a9-687">Cmd： `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="504a9-687">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="504a9-688">Emacs： `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="504a9-688">Emacs: `<Alt+B>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="504a9-689">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="504a9-689">SelectForwardChar</span></span>

<span data-ttu-id="504a9-690">調整目前的選取範圍，以包含下一個字元。</span><span class="sxs-lookup"><span data-stu-id="504a9-690">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="504a9-691">Cmd： `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="504a9-691">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="504a9-692">Emacs： `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="504a9-692">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="504a9-693">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="504a9-693">SelectForwardWord</span></span>

<span data-ttu-id="504a9-694">使用 ForwardWord 調整目前的選取範圍，以包含下一個字組。</span><span class="sxs-lookup"><span data-stu-id="504a9-694">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="504a9-695">Emacs： `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="504a9-695">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="504a9-696">SelectLine</span><span class="sxs-lookup"><span data-stu-id="504a9-696">SelectLine</span></span>

<span data-ttu-id="504a9-697">調整目前的選取範圍，以包含從游標到行尾。</span><span class="sxs-lookup"><span data-stu-id="504a9-697">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="504a9-698">Cmd： `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="504a9-698">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="504a9-699">Emacs： `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="504a9-699">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="504a9-700">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="504a9-700">SelectNextWord</span></span>

<span data-ttu-id="504a9-701">調整目前的選取範圍，以包含下一個字組。</span><span class="sxs-lookup"><span data-stu-id="504a9-701">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="504a9-702">Cmd： `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="504a9-702">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="504a9-703">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="504a9-703">SelectShellBackwardWord</span></span>

<span data-ttu-id="504a9-704">使用 ShellBackwardWord 調整目前的選取範圍，以包含前一個字組。</span><span class="sxs-lookup"><span data-stu-id="504a9-704">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="504a9-705">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="504a9-705">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="504a9-706">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="504a9-706">SelectShellForwardWord</span></span>

<span data-ttu-id="504a9-707">使用 ShellForwardWord 調整目前的選取範圍，以包含下一個字組。</span><span class="sxs-lookup"><span data-stu-id="504a9-707">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="504a9-708">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="504a9-708">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="504a9-709">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="504a9-709">SelectShellNextWord</span></span>

<span data-ttu-id="504a9-710">使用 ShellNextWord 調整目前的選取範圍，以包含下一個字組。</span><span class="sxs-lookup"><span data-stu-id="504a9-710">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="504a9-711">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="504a9-711">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="504a9-712">SetMark</span><span class="sxs-lookup"><span data-stu-id="504a9-712">SetMark</span></span>

<span data-ttu-id="504a9-713">標記目前的資料指標位置，以用於後續的編輯命令。</span><span class="sxs-lookup"><span data-stu-id="504a9-713">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="504a9-714">Emacs： `<Ctrl+`>\`</span><span class="sxs-lookup"><span data-stu-id="504a9-714">Emacs: `<Ctrl+`>\`</span></span>

## <a name="search-functions"></a><span data-ttu-id="504a9-715">搜尋函數</span><span class="sxs-lookup"><span data-stu-id="504a9-715">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="504a9-716">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="504a9-716">CharacterSearch</span></span>

<span data-ttu-id="504a9-717">讀取字元，並向前搜尋該字元的下一個出現位置。</span><span class="sxs-lookup"><span data-stu-id="504a9-717">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="504a9-718">如果指定了引數，則在第 n 次發生) 時，向前搜尋 (或向後搜尋。</span><span class="sxs-lookup"><span data-stu-id="504a9-718">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="504a9-719">Cmd： `<F3>`</span><span class="sxs-lookup"><span data-stu-id="504a9-719">Cmd: `<F3>`</span></span>
- <span data-ttu-id="504a9-720">Emacs： `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="504a9-720">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="504a9-721">Vi 插入模式： `<F3>`</span><span class="sxs-lookup"><span data-stu-id="504a9-721">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="504a9-722">Vi 命令模式： `<F3>`</span><span class="sxs-lookup"><span data-stu-id="504a9-722">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="504a9-723">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="504a9-723">CharacterSearchBackward</span></span>

<span data-ttu-id="504a9-724">讀取字元，並向後搜尋該字元的下一個出現位置。</span><span class="sxs-lookup"><span data-stu-id="504a9-724">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="504a9-725">如果指定了引數，則會在第 n 次出現) 時向後 (或向前搜尋。</span><span class="sxs-lookup"><span data-stu-id="504a9-725">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="504a9-726">Cmd： `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="504a9-726">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="504a9-727">Emacs： `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="504a9-727">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="504a9-728">Vi 插入模式： `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="504a9-728">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="504a9-729">Vi 命令模式： `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="504a9-729">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="504a9-730">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="504a9-730">RepeatLastCharSearch</span></span>

<span data-ttu-id="504a9-731">重複上次錄製的字元搜尋。</span><span class="sxs-lookup"><span data-stu-id="504a9-731">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="504a9-732">Vi 命令模式： `<;>`</span><span class="sxs-lookup"><span data-stu-id="504a9-732">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="504a9-733">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="504a9-733">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="504a9-734">重複上次錄製的字元搜尋，但方向相反。</span><span class="sxs-lookup"><span data-stu-id="504a9-734">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="504a9-735">Vi 命令模式： `<,>`</span><span class="sxs-lookup"><span data-stu-id="504a9-735">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="504a9-736">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="504a9-736">RepeatSearch</span></span>

<span data-ttu-id="504a9-737">以與之前相同的方向重複最後一個搜尋。</span><span class="sxs-lookup"><span data-stu-id="504a9-737">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="504a9-738">Vi 命令模式： `<n>`</span><span class="sxs-lookup"><span data-stu-id="504a9-738">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="504a9-739">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="504a9-739">RepeatSearchBackward</span></span>

<span data-ttu-id="504a9-740">以與之前相同的方向重複最後一個搜尋。</span><span class="sxs-lookup"><span data-stu-id="504a9-740">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="504a9-741">Vi 命令模式： `<N>`</span><span class="sxs-lookup"><span data-stu-id="504a9-741">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="504a9-742">SearchChar</span><span class="sxs-lookup"><span data-stu-id="504a9-742">SearchChar</span></span>

<span data-ttu-id="504a9-743">讀取下一個字元，然後找出該字元，再繼續進行，然後再移出一個字元。</span><span class="sxs-lookup"><span data-stu-id="504a9-743">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="504a9-744">這是「t」功能。</span><span class="sxs-lookup"><span data-stu-id="504a9-744">This is for 't' functionality.</span></span>

- <span data-ttu-id="504a9-745">Vi 命令模式： `<f>`</span><span class="sxs-lookup"><span data-stu-id="504a9-745">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="504a9-746">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="504a9-746">SearchCharBackward</span></span>

<span data-ttu-id="504a9-747">讀取下一個字元，然後找出它，然後再向後移一字元。</span><span class="sxs-lookup"><span data-stu-id="504a9-747">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="504a9-748">這是「t」功能。</span><span class="sxs-lookup"><span data-stu-id="504a9-748">This is for 'T' functionality.</span></span>

- <span data-ttu-id="504a9-749">Vi 命令模式： `<F>`</span><span class="sxs-lookup"><span data-stu-id="504a9-749">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="504a9-750">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="504a9-750">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="504a9-751">讀取下一個字元，然後找出它，然後再向後移一字元。</span><span class="sxs-lookup"><span data-stu-id="504a9-751">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="504a9-752">這是「t」功能。</span><span class="sxs-lookup"><span data-stu-id="504a9-752">This is for 'T' functionality.</span></span>

- <span data-ttu-id="504a9-753">Vi 命令模式： `<T>`</span><span class="sxs-lookup"><span data-stu-id="504a9-753">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="504a9-754">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="504a9-754">SearchCharWithBackoff</span></span>

<span data-ttu-id="504a9-755">讀取下一個字元，然後找出該字元，再繼續進行，然後再移出一個字元。</span><span class="sxs-lookup"><span data-stu-id="504a9-755">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="504a9-756">這是「t」功能。</span><span class="sxs-lookup"><span data-stu-id="504a9-756">This is for 't' functionality.</span></span>

- <span data-ttu-id="504a9-757">Vi 命令模式： `<t>`</span><span class="sxs-lookup"><span data-stu-id="504a9-757">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="504a9-758">SearchForward</span><span class="sxs-lookup"><span data-stu-id="504a9-758">SearchForward</span></span>

<span data-ttu-id="504a9-759">提示輸入搜尋字串，並在 AcceptLine 時起始搜尋。</span><span class="sxs-lookup"><span data-stu-id="504a9-759">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="504a9-760">Vi 插入模式： `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="504a9-760">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="504a9-761">Vi 命令模式： `<?>` 、 `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="504a9-761">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="504a9-762">自訂索引鍵系結</span><span class="sxs-lookup"><span data-stu-id="504a9-762">Custom Key Bindings</span></span>

<span data-ttu-id="504a9-763">PSReadLine 支援使用 Cmdlet 的自訂金鑰系結 `Set-PSReadLineKeyHandler` 。</span><span class="sxs-lookup"><span data-stu-id="504a9-763">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="504a9-764">大部分的自訂按鍵系結都會呼叫上述其中一項功能，例如</span><span class="sxs-lookup"><span data-stu-id="504a9-764">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="504a9-765">您可以將 ScriptBlock 系結至索引鍵。</span><span class="sxs-lookup"><span data-stu-id="504a9-765">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="504a9-766">ScriptBlock 可以進行任何您想要的動作。</span><span class="sxs-lookup"><span data-stu-id="504a9-766">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="504a9-767">一些實用的範例包括</span><span class="sxs-lookup"><span data-stu-id="504a9-767">Some useful examples include</span></span>

- <span data-ttu-id="504a9-768">編輯命令行</span><span class="sxs-lookup"><span data-stu-id="504a9-768">edit the command line</span></span>
- <span data-ttu-id="504a9-769">開啟新視窗 (例如說明) </span><span class="sxs-lookup"><span data-stu-id="504a9-769">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="504a9-770">變更目錄而不變更命令列</span><span class="sxs-lookup"><span data-stu-id="504a9-770">change directories without changing the command line</span></span>

<span data-ttu-id="504a9-771">ScriptBlock 會收到兩個引數：</span><span class="sxs-lookup"><span data-stu-id="504a9-771">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="504a9-772">`$key` -A **[ConsoleKeyInfo]** 物件，它是觸發自訂系結的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="504a9-772">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="504a9-773">如果您將相同的 ScriptBlock 系結至多個金鑰，且需要根據金鑰執行不同的動作，您可以檢查 $key。</span><span class="sxs-lookup"><span data-stu-id="504a9-773">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="504a9-774">許多自訂系結會忽略此引數。</span><span class="sxs-lookup"><span data-stu-id="504a9-774">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="504a9-775">`$arg` -任意引數。</span><span class="sxs-lookup"><span data-stu-id="504a9-775">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="504a9-776">通常，這會是使用者從索引鍵系結 DigitArgument 傳遞的整數引數。</span><span class="sxs-lookup"><span data-stu-id="504a9-776">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="504a9-777">如果您的系結不接受引數，則可以合理地忽略此引數。</span><span class="sxs-lookup"><span data-stu-id="504a9-777">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="504a9-778">讓我們看看將命令列新增至歷程記錄，而不執行的範例。</span><span class="sxs-lookup"><span data-stu-id="504a9-778">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="504a9-779">當您知道您忘了進行某個動作，但不想重新輸入您已經輸入的命令列時，這會很有用。</span><span class="sxs-lookup"><span data-stu-id="504a9-779">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

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

<span data-ttu-id="504a9-780">您可以在檔案中看到許多在 `SamplePSReadLineProfile.ps1` PSReadLine 模組資料夾中安裝的範例。</span><span class="sxs-lookup"><span data-stu-id="504a9-780">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="504a9-781">大部分的按鍵系結都會使用一些 helper 函數來編輯命令行。</span><span class="sxs-lookup"><span data-stu-id="504a9-781">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="504a9-782">這些 Api 記載于下一節。</span><span class="sxs-lookup"><span data-stu-id="504a9-782">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="504a9-783">自訂金鑰系結支援 Api</span><span class="sxs-lookup"><span data-stu-id="504a9-783">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="504a9-784">下列函式在 PSConsoleReadLine 中是公用的，但不能直接系結至索引鍵。</span><span class="sxs-lookup"><span data-stu-id="504a9-784">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="504a9-785">大部分在自訂金鑰系結中都很有用。</span><span class="sxs-lookup"><span data-stu-id="504a9-785">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="504a9-786">將命令列新增至歷程記錄，而不加以執行。</span><span class="sxs-lookup"><span data-stu-id="504a9-786">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="504a9-787">清除終止環形。</span><span class="sxs-lookup"><span data-stu-id="504a9-787">Clear the kill-ring.</span></span>  <span data-ttu-id="504a9-788">這大多用於測試。</span><span class="sxs-lookup"><span data-stu-id="504a9-788">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="504a9-789">從開始刪除長度字元。</span><span class="sxs-lookup"><span data-stu-id="504a9-789">Delete length characters from start.</span></span>  <span data-ttu-id="504a9-790">這種作業支援復原/重做。</span><span class="sxs-lookup"><span data-stu-id="504a9-790">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="504a9-791">根據使用者喜好設定來執行 Ding 動作。</span><span class="sxs-lookup"><span data-stu-id="504a9-791">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="504a9-792">這兩個函式會取出輸入緩衝區目前狀態的相關實用資訊。</span><span class="sxs-lookup"><span data-stu-id="504a9-792">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="504a9-793">第一個較常用於簡單的案例。</span><span class="sxs-lookup"><span data-stu-id="504a9-793">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="504a9-794">如果您的系結使用 Ast 更先進地執行，則會使用第二個。</span><span class="sxs-lookup"><span data-stu-id="504a9-794">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

```

<span data-ttu-id="504a9-795">Get-PSReadLineKeyHandler 使用這個函式，而且在自訂按鍵系結中可能不實用。</span><span class="sxs-lookup"><span data-stu-id="504a9-795">This function is used by Get-PSReadLineKeyHandler and probably isn't useful in a custom key binding.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="504a9-796">Get-PSReadLineOption 使用這個函式，而且在自訂索引鍵系結中可能不太實用。</span><span class="sxs-lookup"><span data-stu-id="504a9-796">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="504a9-797">如果未在命令列上選取任何專案，則會以開始和長度傳回-1。</span><span class="sxs-lookup"><span data-stu-id="504a9-797">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="504a9-798">如果在命令列上有選取專案，則會傳回選取範圍的開始和長度。</span><span class="sxs-lookup"><span data-stu-id="504a9-798">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="504a9-799">在游標處插入字元或字串。</span><span class="sxs-lookup"><span data-stu-id="504a9-799">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="504a9-800">這種作業支援復原/重做。</span><span class="sxs-lookup"><span data-stu-id="504a9-800">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="504a9-801">這是要 PSReadLine 的主要進入點。</span><span class="sxs-lookup"><span data-stu-id="504a9-801">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="504a9-802">它不支援遞迴，因此在自訂索引鍵系結中並不有用。</span><span class="sxs-lookup"><span data-stu-id="504a9-802">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="504a9-803">Remove-PSReadLineKeyHandler 使用這個函式，而且在自訂索引鍵系結中可能不太實用。</span><span class="sxs-lookup"><span data-stu-id="504a9-803">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="504a9-804">取代部分輸入。</span><span class="sxs-lookup"><span data-stu-id="504a9-804">Replace some of the input.</span></span> <span data-ttu-id="504a9-805">這種作業支援復原/重做。</span><span class="sxs-lookup"><span data-stu-id="504a9-805">This operation supports undo/redo.</span></span> <span data-ttu-id="504a9-806">這是優先于 Delete，後面接著 Insert，因為它會被視為復原的單一動作。</span><span class="sxs-lookup"><span data-stu-id="504a9-806">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="504a9-807">將游標移至指定的位移。</span><span class="sxs-lookup"><span data-stu-id="504a9-807">Move the cursor to the given offset.</span></span> <span data-ttu-id="504a9-808">不追蹤資料指標移動以進行復原。</span><span class="sxs-lookup"><span data-stu-id="504a9-808">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="504a9-809">此函式是 Cmdlet PSReadLineOption 所使用的 helper 方法，但對於想要暫時變更設定的自訂按鍵系結來說可能很有用。</span><span class="sxs-lookup"><span data-stu-id="504a9-809">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="504a9-810">此 helper 方法是用於接受 DigitArgument 的自訂系結。</span><span class="sxs-lookup"><span data-stu-id="504a9-810">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="504a9-811">一般呼叫看起來像</span><span class="sxs-lookup"><span data-stu-id="504a9-811">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="note"></a><span data-ttu-id="504a9-812">注意</span><span class="sxs-lookup"><span data-stu-id="504a9-812">NOTE</span></span>

### <a name="powershell-compatibility"></a><span data-ttu-id="504a9-813">POWERSHELL 相容性</span><span class="sxs-lookup"><span data-stu-id="504a9-813">POWERSHELL COMPATIBILITY</span></span>

<span data-ttu-id="504a9-814">PSReadLine 需要 PowerShell 3.0 或更新版本，以及主控台主機。</span><span class="sxs-lookup"><span data-stu-id="504a9-814">PSReadLine requires PowerShell 3.0, or newer, and the console host.</span></span> <span data-ttu-id="504a9-815">它無法在 PowerShell ISE 中運作。</span><span class="sxs-lookup"><span data-stu-id="504a9-815">It does not work in PowerShell ISE.</span></span> <span data-ttu-id="504a9-816">它會在 Visual Studio Code 的主控台中運作。</span><span class="sxs-lookup"><span data-stu-id="504a9-816">It does work in the console of Visual Studio Code.</span></span>

### <a name="command-history"></a><span data-ttu-id="504a9-817">命令歷程記錄</span><span class="sxs-lookup"><span data-stu-id="504a9-817">COMMAND HISTORY</span></span>

<span data-ttu-id="504a9-818">PSReadLine 會維護一個記錄檔，其中包含您從命令列輸入的所有命令和資料。</span><span class="sxs-lookup"><span data-stu-id="504a9-818">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="504a9-819">這可能包含機密資料，包括密碼。</span><span class="sxs-lookup"><span data-stu-id="504a9-819">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="504a9-820">例如，如果您使用指令 `ConvertTo-SecureString` 程式，密碼就會以純文字的形式記錄在記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="504a9-820">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="504a9-821">記錄檔是名為的檔案 `$($host.Name)_history.txt` 。</span><span class="sxs-lookup"><span data-stu-id="504a9-821">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="504a9-822">在 Windows 系統上，歷程記錄檔案會儲存在中 `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` 。</span><span class="sxs-lookup"><span data-stu-id="504a9-822">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="504a9-823">意見反應 & 參與 PSReadLine</span><span class="sxs-lookup"><span data-stu-id="504a9-823">FEEDBACK & CONTRIBUTING TO PSReadLine</span></span>

[<span data-ttu-id="504a9-824">GitHub 上的 PSReadLine</span><span class="sxs-lookup"><span data-stu-id="504a9-824">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="504a9-825">您可以隨時提交提取要求或在 GitHub 頁面上提交意見反應。</span><span class="sxs-lookup"><span data-stu-id="504a9-825">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="504a9-826">另請參閱</span><span class="sxs-lookup"><span data-stu-id="504a9-826">SEE ALSO</span></span>

<span data-ttu-id="504a9-827">PSReadLine 會受到 GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) 程式庫的高度影響。</span><span class="sxs-lookup"><span data-stu-id="504a9-827">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>
