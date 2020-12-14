---
description: PSReadLine 在 PowerShell 主控台中提供改良的命令列編輯體驗。
keywords: powershell
Locale: en-US
ms.date: 11/16/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 關於 PSReadLine
ms.openlocfilehash: 25fc3a9a814728057b1ebc7e721d3fba84ae72c2
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94692304"
---
# <a name="psreadline"></a><span data-ttu-id="f994a-104">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="f994a-104">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="f994a-105">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="f994a-105">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="f994a-106">簡短描述</span><span class="sxs-lookup"><span data-stu-id="f994a-106">Short Description</span></span>

<span data-ttu-id="f994a-107">PSReadLine 在 PowerShell 主控台中提供改良的命令列編輯體驗。</span><span class="sxs-lookup"><span data-stu-id="f994a-107">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="f994a-108">完整描述</span><span class="sxs-lookup"><span data-stu-id="f994a-108">Long Description</span></span>

<span data-ttu-id="f994a-109">PSReadLine 2.0 為 PowerShell 主控台提供功能強大的命令列編輯體驗。</span><span class="sxs-lookup"><span data-stu-id="f994a-109">PSReadLine 2.0 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="f994a-110">它提供：</span><span class="sxs-lookup"><span data-stu-id="f994a-110">It provides:</span></span>

- <span data-ttu-id="f994a-111">命令列的語法著色</span><span class="sxs-lookup"><span data-stu-id="f994a-111">Syntax coloring of the command line</span></span>
- <span data-ttu-id="f994a-112">語法錯誤的視覺指示</span><span class="sxs-lookup"><span data-stu-id="f994a-112">A visual indication of syntax errors</span></span>
- <span data-ttu-id="f994a-113"> (編輯和歷程記錄的更佳多行體驗) </span><span class="sxs-lookup"><span data-stu-id="f994a-113">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="f994a-114">可自訂的按鍵系結</span><span class="sxs-lookup"><span data-stu-id="f994a-114">Customizable key bindings</span></span>
- <span data-ttu-id="f994a-115">Cmd 和 Emacs 模式</span><span class="sxs-lookup"><span data-stu-id="f994a-115">Cmd and Emacs modes</span></span>
- <span data-ttu-id="f994a-116">許多設定選項</span><span class="sxs-lookup"><span data-stu-id="f994a-116">Many configuration options</span></span>
- <span data-ttu-id="f994a-117">Bash 樣式完成 (在 Cmd 模式中為選擇性，預設為 Emacs 模式) </span><span class="sxs-lookup"><span data-stu-id="f994a-117">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="f994a-118">Emacs yank/kill-環形</span><span class="sxs-lookup"><span data-stu-id="f994a-118">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="f994a-119">以 PowerShell 權杖為基礎的「單字」移動和終止</span><span class="sxs-lookup"><span data-stu-id="f994a-119">PowerShell token based "word" movement and kill</span></span>

<span data-ttu-id="f994a-120">PSReadLine 需要 PowerShell 3.0 或更新版本，以及主控台主機。</span><span class="sxs-lookup"><span data-stu-id="f994a-120">PSReadLine requires PowerShell 3.0, or newer, and the console host.</span></span> <span data-ttu-id="f994a-121">它無法在 PowerShell ISE 中運作。</span><span class="sxs-lookup"><span data-stu-id="f994a-121">It does not work in PowerShell ISE.</span></span> <span data-ttu-id="f994a-122">它會在 Visual Studio Code 的主控台中運作。</span><span class="sxs-lookup"><span data-stu-id="f994a-122">It does work in the console of Visual Studio Code.</span></span>

<span data-ttu-id="f994a-123">下列函式可在類別 **[PSConsoleReadLine]** 中使用。</span><span class="sxs-lookup"><span data-stu-id="f994a-123">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]**.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="f994a-124">基本編輯函數</span><span class="sxs-lookup"><span data-stu-id="f994a-124">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="f994a-125">中止</span><span class="sxs-lookup"><span data-stu-id="f994a-125">Abort</span></span>

<span data-ttu-id="f994a-126">中止目前的動作，例如累加式歷程記錄搜尋。</span><span class="sxs-lookup"><span data-stu-id="f994a-126">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="f994a-127">Emacs： `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="f994a-127">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="f994a-128">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="f994a-128">AcceptAndGetNext</span></span>

<span data-ttu-id="f994a-129">嘗試執行目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="f994a-129">Attempt to execute the current input.</span></span> <span data-ttu-id="f994a-130">如果可以像 AcceptLine) 一樣執行 (，則會在下一次呼叫 ReadLine 時，重新叫用歷程記錄中的下一個專案。</span><span class="sxs-lookup"><span data-stu-id="f994a-130">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="f994a-131">Emacs： `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="f994a-131">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="f994a-132">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="f994a-132">AcceptLine</span></span>

<span data-ttu-id="f994a-133">嘗試執行目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="f994a-133">Attempt to execute the current input.</span></span> <span data-ttu-id="f994a-134">如果目前的輸入不完整 (例如遺漏右括弧、方括弧或引號，則接續提示會顯示在下一行，而 PSReadLine 會等候按鍵編輯目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="f994a-134">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="f994a-135">Cmd： `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="f994a-135">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="f994a-136">Emacs： `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="f994a-136">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="f994a-137">Vi 插入模式： `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="f994a-137">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="f994a-138">AddLine</span><span class="sxs-lookup"><span data-stu-id="f994a-138">AddLine</span></span>

<span data-ttu-id="f994a-139">接續提示會顯示在下一行，而 PSReadLine 會等候按鍵編輯目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="f994a-139">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="f994a-140">這對於將多行輸入輸入為單一命令很有用，即使單一行本身已完成輸入也是一樣。</span><span class="sxs-lookup"><span data-stu-id="f994a-140">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="f994a-141">Cmd： `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="f994a-141">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="f994a-142">Emacs： `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="f994a-142">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="f994a-143">Vi 插入模式： `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="f994a-143">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="f994a-144">Vi 命令模式： `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="f994a-144">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="f994a-145">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="f994a-145">BackwardDeleteChar</span></span>

<span data-ttu-id="f994a-146">刪除游標之前的字元。</span><span class="sxs-lookup"><span data-stu-id="f994a-146">Delete the character before the cursor.</span></span>

- <span data-ttu-id="f994a-147">Cmd： `<Backspace>` ， `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="f994a-147">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="f994a-148">Emacs： `<Backspace>` 、 `<Ctrl+Backspace>` 、 `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="f994a-148">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="f994a-149">Vi 插入模式： `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="f994a-149">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="f994a-150">Vi 命令模式： `<X>` 、 `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="f994a-150">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="f994a-151">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="f994a-151">BackwardDeleteLine</span></span>

<span data-ttu-id="f994a-152">如同 BackwardKillLine-刪除從點到行首的文字，但不會將已刪除的文字放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="f994a-152">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="f994a-153">Cmd： `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="f994a-153">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="f994a-154">Vi 插入模式： `<Ctrl+u>` 、 `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="f994a-154">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="f994a-155">Vi 命令模式： `<Ctrl+u>` 、 `<Ctrl+Home>` 、 `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="f994a-155">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`, `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="f994a-156">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="f994a-156">BackwardDeleteWord</span></span>

<span data-ttu-id="f994a-157">刪除上一個字組。</span><span class="sxs-lookup"><span data-stu-id="f994a-157">Deletes the previous word.</span></span>

- <span data-ttu-id="f994a-158">Vi 命令模式： `<Ctrl+w>` 、 `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="f994a-158">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="f994a-159">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="f994a-159">BackwardKillLine</span></span>

<span data-ttu-id="f994a-160">清除輸入至資料指標開頭的輸入。</span><span class="sxs-lookup"><span data-stu-id="f994a-160">Clear the input from the start of the input to the cursor.</span></span> <span data-ttu-id="f994a-161">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="f994a-161">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="f994a-162">Emacs： `<Ctrl+u>` ， `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="f994a-162">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="f994a-163">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="f994a-163">BackwardKillWord</span></span>

<span data-ttu-id="f994a-164">清除從目前單字開頭到游標處的輸入。</span><span class="sxs-lookup"><span data-stu-id="f994a-164">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="f994a-165">如果游標在單字之間，則會從上一個單字開頭開始清除輸入至游標。</span><span class="sxs-lookup"><span data-stu-id="f994a-165">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="f994a-166">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="f994a-166">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="f994a-167">Cmd： `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="f994a-167">Cmd: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="f994a-168">Emacs： `<Alt+Backspace>` ， `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="f994a-168">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="f994a-169">Vi 插入模式： `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="f994a-169">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="f994a-170">Vi 命令模式： `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="f994a-170">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="f994a-171">CancelLine</span><span class="sxs-lookup"><span data-stu-id="f994a-171">CancelLine</span></span>

<span data-ttu-id="f994a-172">取消目前的輸入，將輸入保留在畫面上，但返回主機，以便再次評估提示。</span><span class="sxs-lookup"><span data-stu-id="f994a-172">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="f994a-173">Vi 插入模式： `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="f994a-173">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="f994a-174">Vi 命令模式： `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="f994a-174">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="f994a-175">複製</span><span class="sxs-lookup"><span data-stu-id="f994a-175">Copy</span></span>

<span data-ttu-id="f994a-176">將選取的區域複製到系統剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="f994a-176">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="f994a-177">如果未選取任何區域，請複製整行。</span><span class="sxs-lookup"><span data-stu-id="f994a-177">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="f994a-178">Cmd： `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="f994a-178">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="f994a-179">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="f994a-179">CopyOrCancelLine</span></span>

<span data-ttu-id="f994a-180">如果已選取文字，請複製到剪貼簿，否則請取消該行。</span><span class="sxs-lookup"><span data-stu-id="f994a-180">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="f994a-181">Cmd： `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="f994a-181">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="f994a-182">Emacs： `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="f994a-182">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="f994a-183">剪下</span><span class="sxs-lookup"><span data-stu-id="f994a-183">Cut</span></span>

<span data-ttu-id="f994a-184">刪除選取的區域，將已刪除的文字放入系統剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="f994a-184">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="f994a-185">Cmd： `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="f994a-185">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="f994a-186">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="f994a-186">DeleteChar</span></span>

<span data-ttu-id="f994a-187">刪除游標下的字元。</span><span class="sxs-lookup"><span data-stu-id="f994a-187">Delete the character under the cursor.</span></span>

- <span data-ttu-id="f994a-188">Cmd： `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="f994a-188">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="f994a-189">Emacs： `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="f994a-189">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="f994a-190">Vi 插入模式： `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="f994a-190">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="f994a-191">Vi 命令模式： `<Delete>` 、 `<x>` 、 `<d,l>` 、 `<d,Space>`</span><span class="sxs-lookup"><span data-stu-id="f994a-191">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Space>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="f994a-192">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="f994a-192">DeleteCharOrExit</span></span>

<span data-ttu-id="f994a-193">刪除游標下的字元，如果行是空的，請結束進程。</span><span class="sxs-lookup"><span data-stu-id="f994a-193">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="f994a-194">Emacs： `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="f994a-194">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="f994a-195">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="f994a-195">DeleteEndOfWord</span></span>

<span data-ttu-id="f994a-196">刪除到字尾。</span><span class="sxs-lookup"><span data-stu-id="f994a-196">Delete to the end of the word.</span></span>

- <span data-ttu-id="f994a-197">Vi 命令模式： `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="f994a-197">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="f994a-198">DeleteLine</span><span class="sxs-lookup"><span data-stu-id="f994a-198">DeleteLine</span></span>

<span data-ttu-id="f994a-199">刪除目前的行，並啟用復原。</span><span class="sxs-lookup"><span data-stu-id="f994a-199">Deletes the current line, enabling undo.</span></span>

- <span data-ttu-id="f994a-200">Vi 命令模式： `<d,d>`</span><span class="sxs-lookup"><span data-stu-id="f994a-200">Vi command mode: `<d,d>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="f994a-201">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="f994a-201">DeleteLineToFirstChar</span></span>

<span data-ttu-id="f994a-202">將游標的文字刪除到行的第一個非空白字元。</span><span class="sxs-lookup"><span data-stu-id="f994a-202">Deletes text from the cursor to the first non-blank character of the line.</span></span>

- <span data-ttu-id="f994a-203">Vi 命令模式： `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="f994a-203">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="f994a-204">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="f994a-204">DeleteToEnd</span></span>

<span data-ttu-id="f994a-205">刪除至行尾。</span><span class="sxs-lookup"><span data-stu-id="f994a-205">Delete to the end of the line.</span></span>

- <span data-ttu-id="f994a-206">Vi 命令模式： `<D>` 、 `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="f994a-206">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="f994a-207">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="f994a-207">DeleteWord</span></span>

<span data-ttu-id="f994a-208">刪除下一個字組。</span><span class="sxs-lookup"><span data-stu-id="f994a-208">Delete the next word.</span></span>

- <span data-ttu-id="f994a-209">Vi 命令模式： `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="f994a-209">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="f994a-210">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="f994a-210">ForwardDeleteLine</span></span>

<span data-ttu-id="f994a-211">如同 ForwardKillLine-刪除從點到行尾的文字，但不會將已刪除的文字放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="f994a-211">Like ForwardKillLine - deletes text from the point to the end of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="f994a-212">Cmd： `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="f994a-212">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="f994a-213">Vi 插入模式： `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="f994a-213">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="f994a-214">Vi 命令模式： `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="f994a-214">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="f994a-215">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="f994a-215">InsertLineAbove</span></span>

<span data-ttu-id="f994a-216">無論游標位於目前的行上，都會在目前的行上方建立新的空白行。</span><span class="sxs-lookup"><span data-stu-id="f994a-216">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="f994a-217">游標移至新行的開頭。</span><span class="sxs-lookup"><span data-stu-id="f994a-217">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="f994a-218">Cmd： `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="f994a-218">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="f994a-219">InsertLineBelow</span><span class="sxs-lookup"><span data-stu-id="f994a-219">InsertLineBelow</span></span>

<span data-ttu-id="f994a-220">目前的行下方會建立新的空白行，而不論游標在目前的行上。</span><span class="sxs-lookup"><span data-stu-id="f994a-220">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="f994a-221">游標移至新行的開頭。</span><span class="sxs-lookup"><span data-stu-id="f994a-221">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="f994a-222">Cmd： `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="f994a-222">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="f994a-223">InvertCase</span><span class="sxs-lookup"><span data-stu-id="f994a-223">InvertCase</span></span>

<span data-ttu-id="f994a-224">將目前字元的大小寫反轉，並移至下一個字元。</span><span class="sxs-lookup"><span data-stu-id="f994a-224">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="f994a-225">Vi 命令模式： `<~>`</span><span class="sxs-lookup"><span data-stu-id="f994a-225">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="f994a-226">KillLine</span><span class="sxs-lookup"><span data-stu-id="f994a-226">KillLine</span></span>

<span data-ttu-id="f994a-227">清除游標至輸入結尾的輸入。</span><span class="sxs-lookup"><span data-stu-id="f994a-227">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="f994a-228">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="f994a-228">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="f994a-229">Emacs： `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="f994a-229">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="f994a-230">KillRegion</span><span class="sxs-lookup"><span data-stu-id="f994a-230">KillRegion</span></span>

<span data-ttu-id="f994a-231">終止游標與標記之間的文字。</span><span class="sxs-lookup"><span data-stu-id="f994a-231">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="f994a-232">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="f994a-232">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="f994a-233">KillWord</span><span class="sxs-lookup"><span data-stu-id="f994a-233">KillWord</span></span>

<span data-ttu-id="f994a-234">清除游標到目前單字結尾的輸入。</span><span class="sxs-lookup"><span data-stu-id="f994a-234">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="f994a-235">如果游標在單字之間，則會從資料指標清除輸入至下一個單字的結尾。</span><span class="sxs-lookup"><span data-stu-id="f994a-235">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="f994a-236">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="f994a-236">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="f994a-237">Cmd： `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="f994a-237">Cmd: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="f994a-238">Emacs： `<Alt+d>` ， `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="f994a-238">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="f994a-239">Vi 插入模式： `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="f994a-239">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="f994a-240">Vi 命令模式： `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="f994a-240">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="f994a-241">貼上</span><span class="sxs-lookup"><span data-stu-id="f994a-241">Paste</span></span>

<span data-ttu-id="f994a-242">貼上系統剪貼簿中的文字。</span><span class="sxs-lookup"><span data-stu-id="f994a-242">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="f994a-243">Cmd： `<Ctrl+v>` ， `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="f994a-243">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="f994a-244">Vi 插入模式： `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="f994a-244">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="f994a-245">Vi 命令模式： `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="f994a-245">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f994a-246">使用 **Paste** 函式時，剪貼簿緩衝區的整個內容會貼到 PSReadLine 的輸入緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="f994a-246">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="f994a-247">輸入緩衝區接著會傳遞至 PowerShell 剖析器。</span><span class="sxs-lookup"><span data-stu-id="f994a-247">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="f994a-248">使用主控台應用程式的 **按右鍵** [貼上] 方法貼上的輸入會一次複製到輸入緩衝區一個字元。</span><span class="sxs-lookup"><span data-stu-id="f994a-248">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="f994a-249">當換行字元時，輸入緩衝區會傳遞給剖析器。</span><span class="sxs-lookup"><span data-stu-id="f994a-249">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="f994a-250">因此，輸入會一次剖析一行。</span><span class="sxs-lookup"><span data-stu-id="f994a-250">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="f994a-251">貼上方法之間的差異會導致不同的執行行為。</span><span class="sxs-lookup"><span data-stu-id="f994a-251">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="f994a-252">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="f994a-252">PasteAfter</span></span>

<span data-ttu-id="f994a-253">將剪貼簿貼到游標之後，將游標移至貼上文字的結尾。</span><span class="sxs-lookup"><span data-stu-id="f994a-253">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="f994a-254">Vi 命令模式： `<p>`</span><span class="sxs-lookup"><span data-stu-id="f994a-254">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="f994a-255">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="f994a-255">PasteBefore</span></span>

<span data-ttu-id="f994a-256">將剪貼簿貼到游標之前，將游標移至貼上文字的結尾。</span><span class="sxs-lookup"><span data-stu-id="f994a-256">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="f994a-257">Vi 命令模式： `<P>`</span><span class="sxs-lookup"><span data-stu-id="f994a-257">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="f994a-258">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="f994a-258">PrependAndAccept</span></span>

<span data-ttu-id="f994a-259">在前面加上 ' # ' 並接受該行。</span><span class="sxs-lookup"><span data-stu-id="f994a-259">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="f994a-260">Vi 命令模式： `<#>`</span><span class="sxs-lookup"><span data-stu-id="f994a-260">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="f994a-261">取消復原</span><span class="sxs-lookup"><span data-stu-id="f994a-261">Redo</span></span>

<span data-ttu-id="f994a-262">復原復原。</span><span class="sxs-lookup"><span data-stu-id="f994a-262">Undo an undo.</span></span>

- <span data-ttu-id="f994a-263">Cmd： `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="f994a-263">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="f994a-264">Vi 插入模式： `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="f994a-264">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="f994a-265">Vi 命令模式： `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="f994a-265">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="f994a-266">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="f994a-266">RepeatLastCommand</span></span>

<span data-ttu-id="f994a-267">重複上次修改文字。</span><span class="sxs-lookup"><span data-stu-id="f994a-267">Repeat the last text modification.</span></span>

- <span data-ttu-id="f994a-268">Vi 命令模式： `<.>`</span><span class="sxs-lookup"><span data-stu-id="f994a-268">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="f994a-269">RevertLine</span><span class="sxs-lookup"><span data-stu-id="f994a-269">RevertLine</span></span>

<span data-ttu-id="f994a-270">將所有輸入還原為目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="f994a-270">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="f994a-271">Cmd： `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="f994a-271">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="f994a-272">Emacs： `<Alt+r>` ， `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="f994a-272">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="f994a-273">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="f994a-273">ShellBackwardKillWord</span></span>

<span data-ttu-id="f994a-274">清除從目前單字開頭到游標處的輸入。</span><span class="sxs-lookup"><span data-stu-id="f994a-274">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="f994a-275">如果游標在單字之間，則會從上一個單字開頭開始清除輸入至游標。</span><span class="sxs-lookup"><span data-stu-id="f994a-275">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="f994a-276">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="f994a-276">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="f994a-277">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="f994a-277">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="f994a-278">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="f994a-278">ShellKillWord</span></span>

<span data-ttu-id="f994a-279">清除游標到目前單字結尾的輸入。</span><span class="sxs-lookup"><span data-stu-id="f994a-279">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="f994a-280">如果游標在單字之間，則會從資料指標清除輸入至下一個單字的結尾。</span><span class="sxs-lookup"><span data-stu-id="f994a-280">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="f994a-281">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="f994a-281">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="f994a-282">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="f994a-282">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="f994a-283">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="f994a-283">SwapCharacters</span></span>

<span data-ttu-id="f994a-284">交換目前的字元和前一個字元。</span><span class="sxs-lookup"><span data-stu-id="f994a-284">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="f994a-285">Emacs： `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="f994a-285">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="f994a-286">Vi 插入模式： `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="f994a-286">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="f994a-287">Vi 命令模式： `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="f994a-287">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="f994a-288">復原</span><span class="sxs-lookup"><span data-stu-id="f994a-288">Undo</span></span>

<span data-ttu-id="f994a-289">復原先前的編輯。</span><span class="sxs-lookup"><span data-stu-id="f994a-289">Undo a previous edit.</span></span>

- <span data-ttu-id="f994a-290">Cmd： `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="f994a-290">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="f994a-291">Emacs： `<Ctrl+_>` ， `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="f994a-291">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="f994a-292">Vi 插入模式： `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="f994a-292">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="f994a-293">Vi 命令模式： `<Ctrl+z>` 、 `<u>`</span><span class="sxs-lookup"><span data-stu-id="f994a-293">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="f994a-294">UndoAll</span><span class="sxs-lookup"><span data-stu-id="f994a-294">UndoAll</span></span>

<span data-ttu-id="f994a-295">復原所有先前編輯的行。</span><span class="sxs-lookup"><span data-stu-id="f994a-295">Undo all previous edits for line.</span></span>

- <span data-ttu-id="f994a-296">Vi 命令模式： `<U>`</span><span class="sxs-lookup"><span data-stu-id="f994a-296">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="f994a-297">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="f994a-297">UnixWordRubout</span></span>

<span data-ttu-id="f994a-298">清除從目前單字開頭到游標處的輸入。</span><span class="sxs-lookup"><span data-stu-id="f994a-298">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="f994a-299">如果游標在單字之間，則會從上一個單字開頭開始清除輸入至游標。</span><span class="sxs-lookup"><span data-stu-id="f994a-299">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="f994a-300">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="f994a-300">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="f994a-301">Emacs： `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="f994a-301">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="f994a-302">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="f994a-302">ValidateAndAcceptLine</span></span>

<span data-ttu-id="f994a-303">嘗試執行目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="f994a-303">Attempt to execute the current input.</span></span> <span data-ttu-id="f994a-304">如果目前的輸入不完整 (例如遺漏右括弧、方括弧或引號，則接續提示會顯示在下一行，而 PSReadLine 會等候按鍵編輯目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="f994a-304">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="f994a-305">Emacs： `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="f994a-305">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="f994a-306">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="f994a-306">ViAcceptLine</span></span>

<span data-ttu-id="f994a-307">接受行並切換至插入模式。</span><span class="sxs-lookup"><span data-stu-id="f994a-307">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="f994a-308">Vi 命令模式： `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="f994a-308">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="f994a-309">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="f994a-309">ViAcceptLineOrExit</span></span>

<span data-ttu-id="f994a-310">如同 Emacs 模式中的 DeleteCharOrExit，但會接受行，而不是刪除字元。</span><span class="sxs-lookup"><span data-stu-id="f994a-310">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="f994a-311">Vi 插入模式： `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="f994a-311">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="f994a-312">Vi 命令模式： `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="f994a-312">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="f994a-313">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="f994a-313">ViAppendLine</span></span>

<span data-ttu-id="f994a-314">新行會插入目前的行下方。</span><span class="sxs-lookup"><span data-stu-id="f994a-314">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="f994a-315">Vi 命令模式： `<o>`</span><span class="sxs-lookup"><span data-stu-id="f994a-315">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="f994a-316">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="f994a-316">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="f994a-317">刪除先前的單字，只使用空白字元做為文字分隔符號。</span><span class="sxs-lookup"><span data-stu-id="f994a-317">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="f994a-318">Vi 命令模式： `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="f994a-318">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="f994a-319">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="f994a-319">ViBackwardGlob</span></span>

<span data-ttu-id="f994a-320">將游標移回上一個單字的開頭，只使用空白字元做為分隔符號。</span><span class="sxs-lookup"><span data-stu-id="f994a-320">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="f994a-321">Vi 命令模式： `<B>`</span><span class="sxs-lookup"><span data-stu-id="f994a-321">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="f994a-322">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="f994a-322">ViDeleteBrace</span></span>

<span data-ttu-id="f994a-323">尋找相符的括弧、括弧或方括弧，並刪除內的所有內容，包括括弧。</span><span class="sxs-lookup"><span data-stu-id="f994a-323">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="f994a-324">Vi 命令模式： `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="f994a-324">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="f994a-325">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="f994a-325">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="f994a-326">刪除到字尾。</span><span class="sxs-lookup"><span data-stu-id="f994a-326">Delete to the end of the word.</span></span>

- <span data-ttu-id="f994a-327">Vi 命令模式： `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="f994a-327">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="f994a-328">ViDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="f994a-328">ViDeleteGlob</span></span>

<span data-ttu-id="f994a-329">刪除下一個 glob (以空白字元分隔的單字) 。</span><span class="sxs-lookup"><span data-stu-id="f994a-329">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="f994a-330">Vi 命令模式： `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="f994a-330">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="f994a-331">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="f994a-331">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="f994a-332">刪除指定的字元。</span><span class="sxs-lookup"><span data-stu-id="f994a-332">Deletes until given character.</span></span>

- <span data-ttu-id="f994a-333">Vi 命令模式： `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="f994a-333">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="f994a-334">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="f994a-334">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="f994a-335">刪除指定的字元。</span><span class="sxs-lookup"><span data-stu-id="f994a-335">Deletes until given character.</span></span>

- <span data-ttu-id="f994a-336">Vi 命令模式： `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="f994a-336">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="f994a-337">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="f994a-337">ViDeleteToChar</span></span>

<span data-ttu-id="f994a-338">刪除指定的字元。</span><span class="sxs-lookup"><span data-stu-id="f994a-338">Deletes until given character.</span></span>

- <span data-ttu-id="f994a-339">Vi 命令模式： `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="f994a-339">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="f994a-340">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="f994a-340">ViDeleteToCharBackward</span></span>

<span data-ttu-id="f994a-341">在指定的字元之前反向刪除。</span><span class="sxs-lookup"><span data-stu-id="f994a-341">Deletes backwards until given character.</span></span>

- <span data-ttu-id="f994a-342">Vi 命令模式： `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="f994a-342">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="f994a-343">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="f994a-343">ViInsertAtBegining</span></span>

<span data-ttu-id="f994a-344">切換至插入模式，並將游標放在行首。</span><span class="sxs-lookup"><span data-stu-id="f994a-344">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="f994a-345">Vi 命令模式： `<I>`</span><span class="sxs-lookup"><span data-stu-id="f994a-345">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="f994a-346">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="f994a-346">ViInsertAtEnd</span></span>

<span data-ttu-id="f994a-347">切換至插入模式，並將游標放在行尾。</span><span class="sxs-lookup"><span data-stu-id="f994a-347">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="f994a-348">Vi 命令模式： `<A>`</span><span class="sxs-lookup"><span data-stu-id="f994a-348">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="f994a-349">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="f994a-349">ViInsertLine</span></span>

<span data-ttu-id="f994a-350">新的行會插入到目前這一行的上方。</span><span class="sxs-lookup"><span data-stu-id="f994a-350">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="f994a-351">Vi 命令模式： `<O>`</span><span class="sxs-lookup"><span data-stu-id="f994a-351">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="f994a-352">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="f994a-352">ViInsertWithAppend</span></span>

<span data-ttu-id="f994a-353">從目前的行位置附加。</span><span class="sxs-lookup"><span data-stu-id="f994a-353">Append from the current line position.</span></span>

- <span data-ttu-id="f994a-354">Vi 命令模式： `<a>`</span><span class="sxs-lookup"><span data-stu-id="f994a-354">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="f994a-355">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="f994a-355">ViInsertWithDelete</span></span>

<span data-ttu-id="f994a-356">刪除目前的字元並切換至插入模式。</span><span class="sxs-lookup"><span data-stu-id="f994a-356">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="f994a-357">Vi 命令模式： `<s>`</span><span class="sxs-lookup"><span data-stu-id="f994a-357">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="f994a-358">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="f994a-358">ViJoinLines</span></span>

<span data-ttu-id="f994a-359">加入目前的行和下一行。</span><span class="sxs-lookup"><span data-stu-id="f994a-359">Joins the current line and the next line.</span></span>

- <span data-ttu-id="f994a-360">Vi 命令模式： `<J>`</span><span class="sxs-lookup"><span data-stu-id="f994a-360">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="f994a-361">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="f994a-361">ViReplaceLine</span></span>

<span data-ttu-id="f994a-362">清除整個命令列。</span><span class="sxs-lookup"><span data-stu-id="f994a-362">Erase the entire command line.</span></span>

- <span data-ttu-id="f994a-363">Vi 命令模式： `<S>` 、 `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="f994a-363">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="f994a-364">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="f994a-364">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="f994a-365">取代指定的字元。</span><span class="sxs-lookup"><span data-stu-id="f994a-365">Replaces until given character.</span></span>

- <span data-ttu-id="f994a-366">Vi 命令模式： `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="f994a-366">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="f994a-367">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="f994a-367">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="f994a-368">取代指定的字元。</span><span class="sxs-lookup"><span data-stu-id="f994a-368">Replaces until given character.</span></span>

- <span data-ttu-id="f994a-369">Vi 命令模式： `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="f994a-369">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="f994a-370">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="f994a-370">ViReplaceToChar</span></span>

<span data-ttu-id="f994a-371">刪除指定的字元。</span><span class="sxs-lookup"><span data-stu-id="f994a-371">Deletes until given character.</span></span>

- <span data-ttu-id="f994a-372">Vi 命令模式： `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="f994a-372">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="f994a-373">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="f994a-373">ViReplaceToCharBackward</span></span>

<span data-ttu-id="f994a-374">取代指定的字元。</span><span class="sxs-lookup"><span data-stu-id="f994a-374">Replaces until given character.</span></span>

- <span data-ttu-id="f994a-375">Vi 命令模式： `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="f994a-375">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="f994a-376">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="f994a-376">ViYankBeginningOfLine</span></span>

<span data-ttu-id="f994a-377">從緩衝區開頭 Yank 至資料指標。</span><span class="sxs-lookup"><span data-stu-id="f994a-377">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="f994a-378">Vi 命令模式： `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="f994a-378">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="f994a-379">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="f994a-379">ViYankEndOfGlob</span></span>

<span data-ttu-id="f994a-380">從資料指標 Yank 至 WORD (s) 的結尾。</span><span class="sxs-lookup"><span data-stu-id="f994a-380">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="f994a-381">Vi 命令模式： `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="f994a-381">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="f994a-382">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="f994a-382">ViYankEndOfWord</span></span>

<span data-ttu-id="f994a-383">從資料指標 Yank 至 word (s) 的結尾。</span><span class="sxs-lookup"><span data-stu-id="f994a-383">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="f994a-384">Vi 命令模式： `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="f994a-384">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="f994a-385">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="f994a-385">ViYankLeft</span></span>

<span data-ttu-id="f994a-386">Yank 字元 (s) 到游標的左邊。</span><span class="sxs-lookup"><span data-stu-id="f994a-386">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="f994a-387">Vi 命令模式： `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="f994a-387">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="f994a-388">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="f994a-388">ViYankLine</span></span>

<span data-ttu-id="f994a-389">Yank 整個緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f994a-389">Yank the entire buffer.</span></span>

- <span data-ttu-id="f994a-390">Vi 命令模式： `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="f994a-390">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="f994a-391">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="f994a-391">ViYankNextGlob</span></span>

<span data-ttu-id="f994a-392">從資料指標 Yank 至下一個單字的開頭 (s) 。</span><span class="sxs-lookup"><span data-stu-id="f994a-392">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="f994a-393">Vi 命令模式： `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="f994a-393">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="f994a-394">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="f994a-394">ViYankNextWord</span></span>

<span data-ttu-id="f994a-395">Yank) 在游標之後 (s 的單字。</span><span class="sxs-lookup"><span data-stu-id="f994a-395">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="f994a-396">Vi 命令模式： `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="f994a-396">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="f994a-397">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="f994a-397">ViYankPercent</span></span>

<span data-ttu-id="f994a-398">Yank 至/從相符的括弧。</span><span class="sxs-lookup"><span data-stu-id="f994a-398">Yank to/from matching brace.</span></span>

- <span data-ttu-id="f994a-399">Vi 命令模式： `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="f994a-399">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="f994a-400">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="f994a-400">ViYankPreviousGlob</span></span>

<span data-ttu-id="f994a-401">從字組開頭 (s 的 Yank) 到資料指標。</span><span class="sxs-lookup"><span data-stu-id="f994a-401">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="f994a-402">Vi 命令模式： `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="f994a-402">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="f994a-403">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="f994a-403">ViYankPreviousWord</span></span>

<span data-ttu-id="f994a-404">Yank) 在游標之前的文字 (s。</span><span class="sxs-lookup"><span data-stu-id="f994a-404">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="f994a-405">Vi 命令模式： `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="f994a-405">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="f994a-406">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="f994a-406">ViYankRight</span></span>

<span data-ttu-id="f994a-407">Yank 字元 (s) 在游標右邊和右邊。</span><span class="sxs-lookup"><span data-stu-id="f994a-407">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="f994a-408">Vi 命令模式： `<y,l>` 、 `<y,Space>`</span><span class="sxs-lookup"><span data-stu-id="f994a-408">Vi command mode: `<y,l>`, `<y,Space>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="f994a-409">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="f994a-409">ViYankToEndOfLine</span></span>

<span data-ttu-id="f994a-410">從資料指標 Yank 至緩衝區的結尾。</span><span class="sxs-lookup"><span data-stu-id="f994a-410">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="f994a-411">Vi 命令模式： `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="f994a-411">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="f994a-412">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="f994a-412">ViYankToFirstChar</span></span>

<span data-ttu-id="f994a-413">從第一個非空白字元 Yank 至游標。</span><span class="sxs-lookup"><span data-stu-id="f994a-413">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="f994a-414">Vi 命令模式： `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="f994a-414">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="f994a-415">美國 佬</span><span class="sxs-lookup"><span data-stu-id="f994a-415">Yank</span></span>

<span data-ttu-id="f994a-416">將最近終止的文字加入至輸入。</span><span class="sxs-lookup"><span data-stu-id="f994a-416">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="f994a-417">Emacs： `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="f994a-417">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="f994a-418">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="f994a-418">YankLastArg</span></span>

<span data-ttu-id="f994a-419">Yank 前一個歷程記錄行中的最後一個引數。</span><span class="sxs-lookup"><span data-stu-id="f994a-419">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="f994a-420">使用引數時，第一次叫用時，其行為就像 YankNthArg 一樣。</span><span class="sxs-lookup"><span data-stu-id="f994a-420">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="f994a-421">如果叫用多次，則改為逐一查看歷程記錄和 arg，將方向 (負反轉方向。 ) </span><span class="sxs-lookup"><span data-stu-id="f994a-421">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="f994a-422">Cmd： `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="f994a-422">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="f994a-423">Emacs： `<Alt+.>` 、 `<Alt+_>` 、 `<Escape,.>` 、 `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="f994a-423">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="f994a-424">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="f994a-424">YankNthArg</span></span>

<span data-ttu-id="f994a-425">從上一個歷程記錄行中 Yank 命令) 之後，第一個引數 (。</span><span class="sxs-lookup"><span data-stu-id="f994a-425">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="f994a-426">使用引數時，請 yank 第 n 個引數 (從 0) 開始，如果引數為負數，則從最後一個引數開始。</span><span class="sxs-lookup"><span data-stu-id="f994a-426">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="f994a-427">Emacs： `<Ctrl+Alt+y>` ， `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="f994a-427">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="f994a-428">YankPop</span><span class="sxs-lookup"><span data-stu-id="f994a-428">YankPop</span></span>

<span data-ttu-id="f994a-429">如果先前的作業是 Yank 或 YankPop，請將先前 yanked 的文字取代為終止環形中的下一個已取消文字。</span><span class="sxs-lookup"><span data-stu-id="f994a-429">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="f994a-430">Emacs： `<Alt+y>` ， `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="f994a-430">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="f994a-431">資料指標移動函數</span><span class="sxs-lookup"><span data-stu-id="f994a-431">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="f994a-432">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="f994a-432">BackwardChar</span></span>

<span data-ttu-id="f994a-433">將游標向左移動一個字元。</span><span class="sxs-lookup"><span data-stu-id="f994a-433">Move the cursor one character to the left.</span></span> <span data-ttu-id="f994a-434">這可能會將游標移至多行輸入的上一行。</span><span class="sxs-lookup"><span data-stu-id="f994a-434">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="f994a-435">Cmd： `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="f994a-435">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="f994a-436">Emacs： `<LeftArrow>` ， `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="f994a-436">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>
- <span data-ttu-id="f994a-437">Vi 插入模式： `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="f994a-437">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="f994a-438">Vi 命令模式： `<LeftArrow>` 、 `<Backspace>` 、 `<h>`</span><span class="sxs-lookup"><span data-stu-id="f994a-438">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="f994a-439">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="f994a-439">BackwardWord</span></span>

<span data-ttu-id="f994a-440">將游標移回目前單字的開頭，或將游標移回上一個單字開頭的單字。</span><span class="sxs-lookup"><span data-stu-id="f994a-440">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="f994a-441">單字界限是由一組可設定的字元所定義。</span><span class="sxs-lookup"><span data-stu-id="f994a-441">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="f994a-442">Cmd： `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="f994a-442">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="f994a-443">Emacs： `<Alt+b>` ， `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="f994a-443">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="f994a-444">Vi 插入模式： `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="f994a-444">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="f994a-445">Vi 命令模式： `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="f994a-445">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="f994a-446">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="f994a-446">BeginningOfLine</span></span>

<span data-ttu-id="f994a-447">如果輸入有多行，請移至目前行的開頭，如果已經在行首，則移至輸入的開頭。</span><span class="sxs-lookup"><span data-stu-id="f994a-447">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="f994a-448">如果輸入具有單一行，請移至輸入的開頭。</span><span class="sxs-lookup"><span data-stu-id="f994a-448">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="f994a-449">Cmd： `<Home>`</span><span class="sxs-lookup"><span data-stu-id="f994a-449">Cmd: `<Home>`</span></span>
- <span data-ttu-id="f994a-450">Emacs： `<Home>` ， `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="f994a-450">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="f994a-451">Vi 插入模式： `<Home>`</span><span class="sxs-lookup"><span data-stu-id="f994a-451">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="f994a-452">Vi 命令模式： `<Home>`</span><span class="sxs-lookup"><span data-stu-id="f994a-452">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="f994a-453">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="f994a-453">EndOfLine</span></span>

<span data-ttu-id="f994a-454">如果輸入有多行，請移至目前行的結尾，如果已經在行尾，則移至輸入的結尾。</span><span class="sxs-lookup"><span data-stu-id="f994a-454">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="f994a-455">如果輸入具有單一行，請移至輸入的結尾。</span><span class="sxs-lookup"><span data-stu-id="f994a-455">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="f994a-456">Cmd： `<End>`</span><span class="sxs-lookup"><span data-stu-id="f994a-456">Cmd: `<End>`</span></span>
- <span data-ttu-id="f994a-457">Emacs： `<End>` ， `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="f994a-457">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="f994a-458">Vi 插入模式： `<End>`</span><span class="sxs-lookup"><span data-stu-id="f994a-458">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="f994a-459">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="f994a-459">ForwardChar</span></span>

<span data-ttu-id="f994a-460">將游標向右移動一個字元。</span><span class="sxs-lookup"><span data-stu-id="f994a-460">Move the cursor one character to the right.</span></span> <span data-ttu-id="f994a-461">這可能會將游標移至下一行的多行輸入。</span><span class="sxs-lookup"><span data-stu-id="f994a-461">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="f994a-462">Cmd： `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="f994a-462">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="f994a-463">Emacs： `<RightArrow>` ， `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="f994a-463">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>
- <span data-ttu-id="f994a-464">Vi 插入模式： `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="f994a-464">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="f994a-465">Vi 命令模式： `<RightArrow>` 、 `<Space>` 、 `<l>`</span><span class="sxs-lookup"><span data-stu-id="f994a-465">Vi command mode: `<RightArrow>`, `<Space>`, `<l>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="f994a-466">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="f994a-466">ForwardWord</span></span>

<span data-ttu-id="f994a-467">將游標向前移動至目前單字的結尾，或在文字之間移動到下一個單字的結尾。</span><span class="sxs-lookup"><span data-stu-id="f994a-467">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="f994a-468">單字界限是由一組可設定的字元所定義。</span><span class="sxs-lookup"><span data-stu-id="f994a-468">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="f994a-469">Emacs： `<Alt+f>` ， `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="f994a-469">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="f994a-470">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="f994a-470">GotoBrace</span></span>

<span data-ttu-id="f994a-471">移至相符的大括弧、括弧或方括弧。</span><span class="sxs-lookup"><span data-stu-id="f994a-471">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="f994a-472">Cmd： `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="f994a-472">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="f994a-473">Vi 插入模式： `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="f994a-473">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="f994a-474">Vi 命令模式： `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="f994a-474">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="f994a-475">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="f994a-475">GotoColumn</span></span>

<span data-ttu-id="f994a-476">移至 arg 所表示的資料行。</span><span class="sxs-lookup"><span data-stu-id="f994a-476">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="f994a-477">Vi 命令模式： `<|>`</span><span class="sxs-lookup"><span data-stu-id="f994a-477">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="f994a-478">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="f994a-478">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="f994a-479">將游標移至行中的第一個非空白字元。</span><span class="sxs-lookup"><span data-stu-id="f994a-479">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="f994a-480">Vi 命令模式： `<^>`</span><span class="sxs-lookup"><span data-stu-id="f994a-480">Vi command mode: `<^>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="f994a-481">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="f994a-481">MoveToEndOfLine</span></span>

<span data-ttu-id="f994a-482">將游標移至輸入的結尾。</span><span class="sxs-lookup"><span data-stu-id="f994a-482">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="f994a-483">Vi 命令模式： `<End>` 、 `<$>`</span><span class="sxs-lookup"><span data-stu-id="f994a-483">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="f994a-484">NextLine</span><span class="sxs-lookup"><span data-stu-id="f994a-484">NextLine</span></span>

<span data-ttu-id="f994a-485">將游標移至下一行。</span><span class="sxs-lookup"><span data-stu-id="f994a-485">Move the cursor to the next line.</span></span>

- <span data-ttu-id="f994a-486">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="f994a-486">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="f994a-487">NextWord</span><span class="sxs-lookup"><span data-stu-id="f994a-487">NextWord</span></span>

<span data-ttu-id="f994a-488">將游標向前移至下一個單字的開頭。</span><span class="sxs-lookup"><span data-stu-id="f994a-488">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="f994a-489">單字界限是由一組可設定的字元所定義。</span><span class="sxs-lookup"><span data-stu-id="f994a-489">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="f994a-490">Cmd： `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="f994a-490">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="f994a-491">Vi 插入模式： `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="f994a-491">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="f994a-492">Vi 命令模式： `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="f994a-492">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="f994a-493">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="f994a-493">NextWordEnd</span></span>

<span data-ttu-id="f994a-494">將游標向前移動至目前單字的結尾，或在文字之間移動到下一個單字的結尾。</span><span class="sxs-lookup"><span data-stu-id="f994a-494">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="f994a-495">單字界限是由一組可設定的字元所定義。</span><span class="sxs-lookup"><span data-stu-id="f994a-495">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="f994a-496">Vi 命令模式： `<e>`</span><span class="sxs-lookup"><span data-stu-id="f994a-496">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="f994a-497">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="f994a-497">PreviousLine</span></span>

<span data-ttu-id="f994a-498">將游標移至上一行。</span><span class="sxs-lookup"><span data-stu-id="f994a-498">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="f994a-499">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="f994a-499">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="f994a-500">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="f994a-500">ShellBackwardWord</span></span>

<span data-ttu-id="f994a-501">將游標移回目前單字的開頭，或將游標移回上一個單字開頭的單字。</span><span class="sxs-lookup"><span data-stu-id="f994a-501">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="f994a-502">單字界限是由 PowerShell 權杖所定義。</span><span class="sxs-lookup"><span data-stu-id="f994a-502">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="f994a-503">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="f994a-503">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="f994a-504">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="f994a-504">ShellForwardWord</span></span>

<span data-ttu-id="f994a-505">將游標向前移至下一個單字的開頭。</span><span class="sxs-lookup"><span data-stu-id="f994a-505">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="f994a-506">單字界限是由 PowerShell 權杖所定義。</span><span class="sxs-lookup"><span data-stu-id="f994a-506">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="f994a-507">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="f994a-507">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="f994a-508">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="f994a-508">ShellNextWord</span></span>

<span data-ttu-id="f994a-509">將游標向前移動至目前單字的結尾，或在文字之間移動到下一個單字的結尾。</span><span class="sxs-lookup"><span data-stu-id="f994a-509">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="f994a-510">單字界限是由 PowerShell 權杖所定義。</span><span class="sxs-lookup"><span data-stu-id="f994a-510">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="f994a-511">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="f994a-511">Function is unbound.</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="f994a-512">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="f994a-512">ViBackwardWord</span></span>

<span data-ttu-id="f994a-513">將游標移回目前單字的開頭，或將游標移回上一個單字開頭的單字。</span><span class="sxs-lookup"><span data-stu-id="f994a-513">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="f994a-514">單字界限是由一組可設定的字元所定義。</span><span class="sxs-lookup"><span data-stu-id="f994a-514">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="f994a-515">Vi 命令模式： `<b>`</span><span class="sxs-lookup"><span data-stu-id="f994a-515">Vi command mode: `<b>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="f994a-516">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="f994a-516">ViEndOfGlob</span></span>

<span data-ttu-id="f994a-517">將游標移至單字的結尾，只使用空白字元做為分隔符號。</span><span class="sxs-lookup"><span data-stu-id="f994a-517">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="f994a-518">Vi 命令模式： `<E>`</span><span class="sxs-lookup"><span data-stu-id="f994a-518">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="f994a-519">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="f994a-519">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="f994a-520">移至上一個單字的結尾，只使用空白字元做為單字分隔符號。</span><span class="sxs-lookup"><span data-stu-id="f994a-520">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="f994a-521">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="f994a-521">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="f994a-522">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="f994a-522">ViGotoBrace</span></span>

<span data-ttu-id="f994a-523">類似于 GotoBrace，但它是以字元為基礎，而不是以權杖為基礎。</span><span class="sxs-lookup"><span data-stu-id="f994a-523">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="f994a-524">Vi 命令模式： `<%>`</span><span class="sxs-lookup"><span data-stu-id="f994a-524">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="f994a-525">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="f994a-525">ViNextGlob</span></span>

<span data-ttu-id="f994a-526">移至下一個單字，只使用空白字元做為單字分隔符號。</span><span class="sxs-lookup"><span data-stu-id="f994a-526">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="f994a-527">Vi 命令模式： `<W>`</span><span class="sxs-lookup"><span data-stu-id="f994a-527">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="f994a-528">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="f994a-528">ViNextWord</span></span>

<span data-ttu-id="f994a-529">將游標向前移至下一個單字的開頭。</span><span class="sxs-lookup"><span data-stu-id="f994a-529">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="f994a-530">單字界限是由一組可設定的字元所定義。</span><span class="sxs-lookup"><span data-stu-id="f994a-530">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="f994a-531">Vi 命令模式： `<w>`</span><span class="sxs-lookup"><span data-stu-id="f994a-531">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="f994a-532">歷程記錄函數</span><span class="sxs-lookup"><span data-stu-id="f994a-532">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="f994a-533">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="f994a-533">BeginningOfHistory</span></span>

<span data-ttu-id="f994a-534">移至歷程記錄中的第一個專案。</span><span class="sxs-lookup"><span data-stu-id="f994a-534">Move to the first item in the history.</span></span>

- <span data-ttu-id="f994a-535">Emacs： `<Alt+`<>\`</span><span class="sxs-lookup"><span data-stu-id="f994a-535">Emacs: `<Alt+`<>\`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="f994a-536">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="f994a-536">ClearHistory</span></span>

<span data-ttu-id="f994a-537">清除 PSReadLine 中的歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="f994a-537">Clears history in PSReadLine.</span></span> <span data-ttu-id="f994a-538">這不會影響 PowerShell 歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="f994a-538">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="f994a-539">Cmd： `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="f994a-539">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="f994a-540">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="f994a-540">EndOfHistory</span></span>

<span data-ttu-id="f994a-541">移至記錄中目前輸入)  (的最後一個專案。</span><span class="sxs-lookup"><span data-stu-id="f994a-541">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="f994a-542">Emacs： `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="f994a-542">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="f994a-543">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="f994a-543">ForwardSearchHistory</span></span>

<span data-ttu-id="f994a-544">透過歷程記錄執行漸進式向前搜尋。</span><span class="sxs-lookup"><span data-stu-id="f994a-544">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="f994a-545">Cmd： `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="f994a-545">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="f994a-546">Emacs： `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="f994a-546">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="f994a-547">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="f994a-547">HistorySearchBackward</span></span>

<span data-ttu-id="f994a-548">將目前的輸入取代為 PSReadLine 記錄中與開始和輸入和資料指標之間的字元相符的 ' previous ' 專案。</span><span class="sxs-lookup"><span data-stu-id="f994a-548">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="f994a-549">Cmd： `<F8>`</span><span class="sxs-lookup"><span data-stu-id="f994a-549">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="f994a-550">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="f994a-550">HistorySearchForward</span></span>

<span data-ttu-id="f994a-551">將目前的輸入取代為 PSReadLine 記錄中與開始和輸入和資料指標之間的字元相符的 ' next ' 專案。</span><span class="sxs-lookup"><span data-stu-id="f994a-551">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="f994a-552">Cmd： `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="f994a-552">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="f994a-553">NextHistory</span><span class="sxs-lookup"><span data-stu-id="f994a-553">NextHistory</span></span>

<span data-ttu-id="f994a-554">將目前的輸入取代為 PSReadLine 記錄中的 ' next ' 專案。</span><span class="sxs-lookup"><span data-stu-id="f994a-554">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="f994a-555">Cmd： `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="f994a-555">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="f994a-556">Emacs： `<DownArrow>` ， `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="f994a-556">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="f994a-557">Vi 插入模式： `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="f994a-557">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="f994a-558">Vi 命令模式： `<DownArrow>` 、 `<j>` 、 `<+>`</span><span class="sxs-lookup"><span data-stu-id="f994a-558">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="f994a-559">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="f994a-559">PreviousHistory</span></span>

<span data-ttu-id="f994a-560">將目前的輸入取代為 PSReadLine 記錄中的 ' previous ' 專案。</span><span class="sxs-lookup"><span data-stu-id="f994a-560">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="f994a-561">Cmd： `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="f994a-561">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="f994a-562">Emacs： `<UpArrow>` ， `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="f994a-562">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="f994a-563">Vi 插入模式： `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="f994a-563">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="f994a-564">Vi 命令模式： `<UpArrow>` 、 `<k>` 、 `<->`</span><span class="sxs-lookup"><span data-stu-id="f994a-564">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="f994a-565">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="f994a-565">ReverseSearchHistory</span></span>

<span data-ttu-id="f994a-566">透過歷程記錄執行增量向前搜尋。</span><span class="sxs-lookup"><span data-stu-id="f994a-566">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="f994a-567">Cmd： `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="f994a-567">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="f994a-568">Emacs： `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="f994a-568">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="f994a-569">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="f994a-569">ViSearchHistoryBackward</span></span>

<span data-ttu-id="f994a-570">提示輸入搜尋字串，並在 AcceptLine 時起始搜尋。</span><span class="sxs-lookup"><span data-stu-id="f994a-570">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="f994a-571">Vi 插入模式： `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="f994a-571">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="f994a-572">Vi 命令模式： `</>` 、 `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="f994a-572">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="f994a-573">完成函式</span><span class="sxs-lookup"><span data-stu-id="f994a-573">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="f994a-574">完成</span><span class="sxs-lookup"><span data-stu-id="f994a-574">Complete</span></span>

<span data-ttu-id="f994a-575">嘗試對資料指標周圍的文字執行完成。</span><span class="sxs-lookup"><span data-stu-id="f994a-575">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="f994a-576">如果有多個可能的完成，則會使用最長的明確前置詞來完成。</span><span class="sxs-lookup"><span data-stu-id="f994a-576">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="f994a-577">如果嘗試完成最長的明確完成，則會顯示可能的完成清單。</span><span class="sxs-lookup"><span data-stu-id="f994a-577">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="f994a-578">Emacs： `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="f994a-578">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="f994a-579">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="f994a-579">MenuComplete</span></span>

<span data-ttu-id="f994a-580">嘗試對資料指標周圍的文字執行完成。</span><span class="sxs-lookup"><span data-stu-id="f994a-580">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="f994a-581">如果有多個可能的完成，則會使用最長的明確前置詞來完成。</span><span class="sxs-lookup"><span data-stu-id="f994a-581">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="f994a-582">如果嘗試完成最長的明確完成，則會顯示可能的完成清單。</span><span class="sxs-lookup"><span data-stu-id="f994a-582">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="f994a-583">Cmd： `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="f994a-583">Cmd: `<Ctrl+Space>`</span></span>
- <span data-ttu-id="f994a-584">Emacs： `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="f994a-584">Emacs: `<Ctrl+Space>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="f994a-585">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="f994a-585">PossibleCompletions</span></span>

<span data-ttu-id="f994a-586">顯示可能的完成清單。</span><span class="sxs-lookup"><span data-stu-id="f994a-586">Display the list of possible completions.</span></span>

- <span data-ttu-id="f994a-587">Emacs： `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="f994a-587">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="f994a-588">Vi 插入模式： `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="f994a-588">Vi insert mode: `<Ctrl+Space>`</span></span>
- <span data-ttu-id="f994a-589">Vi 命令模式： `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="f994a-589">Vi command mode: `<Ctrl+Space>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="f994a-590">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="f994a-590">TabCompleteNext</span></span>

<span data-ttu-id="f994a-591">嘗試使用下一個可用的完成來完成資料指標周圍的文字。</span><span class="sxs-lookup"><span data-stu-id="f994a-591">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="f994a-592">Cmd： `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="f994a-592">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="f994a-593">Vi 命令模式： `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="f994a-593">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="f994a-594">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="f994a-594">TabCompletePrevious</span></span>

<span data-ttu-id="f994a-595">嘗試使用先前的可用完成來完成資料指標周圍的文字。</span><span class="sxs-lookup"><span data-stu-id="f994a-595">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="f994a-596">Cmd： `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="f994a-596">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="f994a-597">Vi 命令模式： `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="f994a-597">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="f994a-598">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="f994a-598">ViTabCompleteNext</span></span>

<span data-ttu-id="f994a-599">視需要結束目前的編輯群組，並叫用 TabCompleteNext。</span><span class="sxs-lookup"><span data-stu-id="f994a-599">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="f994a-600">Vi 插入模式： `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="f994a-600">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="f994a-601">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="f994a-601">ViTabCompletePrevious</span></span>

<span data-ttu-id="f994a-602">視需要結束目前的編輯群組，並叫用 TabCompletePrevious。</span><span class="sxs-lookup"><span data-stu-id="f994a-602">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="f994a-603">Vi 插入模式： `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="f994a-603">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="f994a-604">其他函式</span><span class="sxs-lookup"><span data-stu-id="f994a-604">Miscellaneous functions</span></span>

### <a name="capturescreen"></a><span data-ttu-id="f994a-605">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="f994a-605">CaptureScreen</span></span>

<span data-ttu-id="f994a-606">啟動互動式螢幕擷取畫面-向上/向下箭號選取 [線條]，輸入將選取的文字複製到剪貼簿做為文字和 html。</span><span class="sxs-lookup"><span data-stu-id="f994a-606">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="f994a-607">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="f994a-607">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="f994a-608">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="f994a-608">ClearScreen</span></span>

<span data-ttu-id="f994a-609">清除畫面並在畫面頂端繪製目前的線。</span><span class="sxs-lookup"><span data-stu-id="f994a-609">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="f994a-610">Cmd： `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="f994a-610">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="f994a-611">Emacs： `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="f994a-611">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="f994a-612">Vi 插入模式： `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="f994a-612">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="f994a-613">Vi 命令模式： `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="f994a-613">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="f994a-614">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="f994a-614">DigitArgument</span></span>

<span data-ttu-id="f994a-615">開始新的數位引數以傳遞至其他函式。</span><span class="sxs-lookup"><span data-stu-id="f994a-615">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="f994a-616">Cmd： `<Alt+0>` 、 `<Alt+1>` 、 `<Alt+2>` 、 `<Alt+3>` 、 `<Alt+4>` 、 `<Alt+5>` 、 `<Alt+6>` `<Alt+7>` `<Alt+8>` `<Alt+9>` 、、、、、 `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="f994a-616">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="f994a-617">Emacs： `<Alt+0>` 、 `<Alt+1>` 、 `<Alt+2>` 、、、 `<Alt+3>` `<Alt+4>` `<Alt+5>` 、 `<Alt+6>` 、 `<Alt+7>` 、 `<Alt+8>` 、 `<Alt+9>` 、、 `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="f994a-617">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="f994a-618">Vi 命令模式： `<0>` 、 `<1>` 、 `<2>` 、 `<3>` 、 `<4>` 、 `<5>` 、 `<6>` `<7>` `<8>` 、、、、 `<9>`</span><span class="sxs-lookup"><span data-stu-id="f994a-618">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="f994a-619">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="f994a-619">InvokePrompt</span></span>

<span data-ttu-id="f994a-620">清除目前的提示，並呼叫 prompt 函式以重新顯示提示。</span><span class="sxs-lookup"><span data-stu-id="f994a-620">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="f994a-621">適用于變更狀態的自訂金鑰處理常式，例如變更目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="f994a-621">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="f994a-622">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="f994a-622">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="f994a-623">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="f994a-623">ScrollDisplayDown</span></span>

<span data-ttu-id="f994a-624">將顯示畫面向下移動一個畫面。</span><span class="sxs-lookup"><span data-stu-id="f994a-624">Scroll the display down one screen.</span></span>

- <span data-ttu-id="f994a-625">Cmd： `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="f994a-625">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="f994a-626">Emacs： `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="f994a-626">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="f994a-627">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="f994a-627">ScrollDisplayDownLine</span></span>

<span data-ttu-id="f994a-628">將向下移動一行。</span><span class="sxs-lookup"><span data-stu-id="f994a-628">Scroll the display down one line.</span></span>

- <span data-ttu-id="f994a-629">Cmd： `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="f994a-629">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="f994a-630">Emacs： `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="f994a-630">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="f994a-631">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="f994a-631">ScrollDisplayToCursor</span></span>

<span data-ttu-id="f994a-632">將顯示滾動至游標。</span><span class="sxs-lookup"><span data-stu-id="f994a-632">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="f994a-633">Emacs： `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="f994a-633">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="f994a-634">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="f994a-634">ScrollDisplayTop</span></span>

<span data-ttu-id="f994a-635">將顯示器向上方滾動。</span><span class="sxs-lookup"><span data-stu-id="f994a-635">Scroll the display to the top.</span></span>

- <span data-ttu-id="f994a-636">Emacs： `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="f994a-636">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="f994a-637">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="f994a-637">ScrollDisplayUp</span></span>

<span data-ttu-id="f994a-638">將顯示畫面向上移動一次。</span><span class="sxs-lookup"><span data-stu-id="f994a-638">Scroll the display up one screen.</span></span>

- <span data-ttu-id="f994a-639">Cmd： `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="f994a-639">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="f994a-640">Emacs： `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="f994a-640">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="f994a-641">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="f994a-641">ScrollDisplayUpLine</span></span>

<span data-ttu-id="f994a-642">將顯示畫面向下移動一行。</span><span class="sxs-lookup"><span data-stu-id="f994a-642">Scroll the display up one line.</span></span>

- <span data-ttu-id="f994a-643">Cmd： `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="f994a-643">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="f994a-644">Emacs： `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="f994a-644">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="f994a-645">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="f994a-645">SelfInsert</span></span>

<span data-ttu-id="f994a-646">插入金鑰。</span><span class="sxs-lookup"><span data-stu-id="f994a-646">Insert the key.</span></span>

- <span data-ttu-id="f994a-647">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="f994a-647">Function is unbound.</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="f994a-648">ShowKeyBindings</span><span class="sxs-lookup"><span data-stu-id="f994a-648">ShowKeyBindings</span></span>

<span data-ttu-id="f994a-649">顯示所有系結的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="f994a-649">Show all bound keys.</span></span>

- <span data-ttu-id="f994a-650">Cmd： `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="f994a-650">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="f994a-651">Emacs： `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="f994a-651">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="f994a-652">Vi 插入模式： `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="f994a-652">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="f994a-653">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="f994a-653">ViCommandMode</span></span>

<span data-ttu-id="f994a-654">將目前的作業模式從 Vi-Insert 切換至 Vi 命令。</span><span class="sxs-lookup"><span data-stu-id="f994a-654">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="f994a-655">Vi 插入模式： `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="f994a-655">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="f994a-656">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="f994a-656">ViDigitArgumentInChord</span></span>

<span data-ttu-id="f994a-657">開始新的數位引數，以傳遞至其他函式，而非 vi 的 chords 之一。</span><span class="sxs-lookup"><span data-stu-id="f994a-657">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="f994a-658">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="f994a-658">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="f994a-659">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="f994a-659">ViEditVisually</span></span>

<span data-ttu-id="f994a-660">在 [$env：編輯器] 或 [$env：視覺效果] 所指定的文字編輯器中編輯命令行。</span><span class="sxs-lookup"><span data-stu-id="f994a-660">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="f994a-661">Emacs： `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="f994a-661">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="f994a-662">Vi 命令模式： `<v>`</span><span class="sxs-lookup"><span data-stu-id="f994a-662">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="f994a-663">ViExit</span><span class="sxs-lookup"><span data-stu-id="f994a-663">ViExit</span></span>

<span data-ttu-id="f994a-664">離開 shell。</span><span class="sxs-lookup"><span data-stu-id="f994a-664">Exits the shell.</span></span>

- <span data-ttu-id="f994a-665">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="f994a-665">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="f994a-666">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="f994a-666">ViInsertMode</span></span>

<span data-ttu-id="f994a-667">切換至插入模式。</span><span class="sxs-lookup"><span data-stu-id="f994a-667">Switch to Insert mode.</span></span>

- <span data-ttu-id="f994a-668">Vi 命令模式： `<i>`</span><span class="sxs-lookup"><span data-stu-id="f994a-668">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="f994a-669">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="f994a-669">WhatIsKey</span></span>

<span data-ttu-id="f994a-670">讀取金鑰，並告訴我金鑰的系結目標。</span><span class="sxs-lookup"><span data-stu-id="f994a-670">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="f994a-671">Cmd： `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="f994a-671">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="f994a-672">Emacs： `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="f994a-672">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="f994a-673">選取函式</span><span class="sxs-lookup"><span data-stu-id="f994a-673">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="f994a-674">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="f994a-674">ExchangePointAndMark</span></span>

<span data-ttu-id="f994a-675">游標放在標記的位置，而標記會移至游標位置。</span><span class="sxs-lookup"><span data-stu-id="f994a-675">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="f994a-676">Emacs： `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="f994a-676">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="f994a-677">SelectAll</span><span class="sxs-lookup"><span data-stu-id="f994a-677">SelectAll</span></span>

<span data-ttu-id="f994a-678">選取整行。</span><span class="sxs-lookup"><span data-stu-id="f994a-678">Select the entire line.</span></span>

- <span data-ttu-id="f994a-679">Cmd： `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="f994a-679">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="f994a-680">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="f994a-680">SelectBackwardChar</span></span>

<span data-ttu-id="f994a-681">調整目前的選取範圍，以包含前一個字元。</span><span class="sxs-lookup"><span data-stu-id="f994a-681">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="f994a-682">Cmd： `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="f994a-682">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="f994a-683">Emacs： `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="f994a-683">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="f994a-684">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="f994a-684">SelectBackwardsLine</span></span>

<span data-ttu-id="f994a-685">調整目前的選取範圍，以包含從游標到行首的起點。</span><span class="sxs-lookup"><span data-stu-id="f994a-685">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="f994a-686">Cmd： `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="f994a-686">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="f994a-687">Emacs： `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="f994a-687">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="f994a-688">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="f994a-688">SelectBackwardWord</span></span>

<span data-ttu-id="f994a-689">調整目前的選取範圍，以包含前一個字組。</span><span class="sxs-lookup"><span data-stu-id="f994a-689">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="f994a-690">Cmd： `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="f994a-690">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="f994a-691">Emacs： `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="f994a-691">Emacs: `<Alt+B>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="f994a-692">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="f994a-692">SelectForwardChar</span></span>

<span data-ttu-id="f994a-693">調整目前的選取範圍，以包含下一個字元。</span><span class="sxs-lookup"><span data-stu-id="f994a-693">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="f994a-694">Cmd： `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="f994a-694">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="f994a-695">Emacs： `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="f994a-695">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="f994a-696">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="f994a-696">SelectForwardWord</span></span>

<span data-ttu-id="f994a-697">使用 ForwardWord 調整目前的選取範圍，以包含下一個字組。</span><span class="sxs-lookup"><span data-stu-id="f994a-697">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="f994a-698">Emacs： `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="f994a-698">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="f994a-699">SelectLine</span><span class="sxs-lookup"><span data-stu-id="f994a-699">SelectLine</span></span>

<span data-ttu-id="f994a-700">調整目前的選取範圍，以包含從游標到行尾。</span><span class="sxs-lookup"><span data-stu-id="f994a-700">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="f994a-701">Cmd： `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="f994a-701">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="f994a-702">Emacs： `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="f994a-702">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="f994a-703">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="f994a-703">SelectNextWord</span></span>

<span data-ttu-id="f994a-704">調整目前的選取範圍，以包含下一個字組。</span><span class="sxs-lookup"><span data-stu-id="f994a-704">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="f994a-705">Cmd： `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="f994a-705">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="f994a-706">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="f994a-706">SelectShellBackwardWord</span></span>

<span data-ttu-id="f994a-707">使用 ShellBackwardWord 調整目前的選取範圍，以包含前一個字組。</span><span class="sxs-lookup"><span data-stu-id="f994a-707">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="f994a-708">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="f994a-708">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="f994a-709">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="f994a-709">SelectShellForwardWord</span></span>

<span data-ttu-id="f994a-710">使用 ShellForwardWord 調整目前的選取範圍，以包含下一個字組。</span><span class="sxs-lookup"><span data-stu-id="f994a-710">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="f994a-711">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="f994a-711">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="f994a-712">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="f994a-712">SelectShellNextWord</span></span>

<span data-ttu-id="f994a-713">使用 ShellNextWord 調整目前的選取範圍，以包含下一個字組。</span><span class="sxs-lookup"><span data-stu-id="f994a-713">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="f994a-714">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="f994a-714">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="f994a-715">SetMark</span><span class="sxs-lookup"><span data-stu-id="f994a-715">SetMark</span></span>

<span data-ttu-id="f994a-716">標記目前的資料指標位置，以用於後續的編輯命令。</span><span class="sxs-lookup"><span data-stu-id="f994a-716">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="f994a-717">Emacs： `<Ctrl+`>\`</span><span class="sxs-lookup"><span data-stu-id="f994a-717">Emacs: `<Ctrl+`>\`</span></span>

## <a name="search-functions"></a><span data-ttu-id="f994a-718">搜尋函數</span><span class="sxs-lookup"><span data-stu-id="f994a-718">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="f994a-719">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="f994a-719">CharacterSearch</span></span>

<span data-ttu-id="f994a-720">讀取字元，並向前搜尋該字元的下一個出現位置。</span><span class="sxs-lookup"><span data-stu-id="f994a-720">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="f994a-721">如果指定了引數，則在第 n 次發生) 時，向前搜尋 (或向後搜尋。</span><span class="sxs-lookup"><span data-stu-id="f994a-721">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="f994a-722">Cmd： `<F3>`</span><span class="sxs-lookup"><span data-stu-id="f994a-722">Cmd: `<F3>`</span></span>
- <span data-ttu-id="f994a-723">Emacs： `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="f994a-723">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="f994a-724">Vi 插入模式： `<F3>`</span><span class="sxs-lookup"><span data-stu-id="f994a-724">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="f994a-725">Vi 命令模式： `<F3>`</span><span class="sxs-lookup"><span data-stu-id="f994a-725">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="f994a-726">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="f994a-726">CharacterSearchBackward</span></span>

<span data-ttu-id="f994a-727">讀取字元，並向後搜尋該字元的下一個出現位置。</span><span class="sxs-lookup"><span data-stu-id="f994a-727">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="f994a-728">如果指定了引數，則會在第 n 次出現) 時向後 (或向前搜尋。</span><span class="sxs-lookup"><span data-stu-id="f994a-728">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="f994a-729">Cmd： `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="f994a-729">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="f994a-730">Emacs： `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="f994a-730">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="f994a-731">Vi 插入模式： `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="f994a-731">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="f994a-732">Vi 命令模式： `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="f994a-732">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="f994a-733">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="f994a-733">RepeatLastCharSearch</span></span>

<span data-ttu-id="f994a-734">重複上次錄製的字元搜尋。</span><span class="sxs-lookup"><span data-stu-id="f994a-734">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="f994a-735">Vi 命令模式： `<;>`</span><span class="sxs-lookup"><span data-stu-id="f994a-735">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="f994a-736">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="f994a-736">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="f994a-737">重複上次錄製的字元搜尋，但方向相反。</span><span class="sxs-lookup"><span data-stu-id="f994a-737">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="f994a-738">Vi 命令模式： `<,>`</span><span class="sxs-lookup"><span data-stu-id="f994a-738">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="f994a-739">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="f994a-739">RepeatSearch</span></span>

<span data-ttu-id="f994a-740">以與之前相同的方向重複最後一個搜尋。</span><span class="sxs-lookup"><span data-stu-id="f994a-740">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="f994a-741">Vi 命令模式： `<n>`</span><span class="sxs-lookup"><span data-stu-id="f994a-741">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="f994a-742">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="f994a-742">RepeatSearchBackward</span></span>

<span data-ttu-id="f994a-743">以與之前相同的方向重複最後一個搜尋。</span><span class="sxs-lookup"><span data-stu-id="f994a-743">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="f994a-744">Vi 命令模式： `<N>`</span><span class="sxs-lookup"><span data-stu-id="f994a-744">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="f994a-745">SearchChar</span><span class="sxs-lookup"><span data-stu-id="f994a-745">SearchChar</span></span>

<span data-ttu-id="f994a-746">讀取下一個字元，然後找出該字元，再繼續進行，然後再移出一個字元。</span><span class="sxs-lookup"><span data-stu-id="f994a-746">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="f994a-747">這是「t」功能。</span><span class="sxs-lookup"><span data-stu-id="f994a-747">This is for 't' functionality.</span></span>

- <span data-ttu-id="f994a-748">Vi 命令模式： `<f>`</span><span class="sxs-lookup"><span data-stu-id="f994a-748">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="f994a-749">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="f994a-749">SearchCharBackward</span></span>

<span data-ttu-id="f994a-750">讀取下一個字元，然後找出它，然後再向後移一字元。</span><span class="sxs-lookup"><span data-stu-id="f994a-750">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="f994a-751">這是「t」功能。</span><span class="sxs-lookup"><span data-stu-id="f994a-751">This is for 'T' functionality.</span></span>

- <span data-ttu-id="f994a-752">Vi 命令模式： `<F>`</span><span class="sxs-lookup"><span data-stu-id="f994a-752">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="f994a-753">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="f994a-753">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="f994a-754">讀取下一個字元，然後找出它，然後再向後移一字元。</span><span class="sxs-lookup"><span data-stu-id="f994a-754">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="f994a-755">這是「t」功能。</span><span class="sxs-lookup"><span data-stu-id="f994a-755">This is for 'T' functionality.</span></span>

- <span data-ttu-id="f994a-756">Vi 命令模式： `<T>`</span><span class="sxs-lookup"><span data-stu-id="f994a-756">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="f994a-757">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="f994a-757">SearchCharWithBackoff</span></span>

<span data-ttu-id="f994a-758">讀取下一個字元，然後找出該字元，再繼續進行，然後再移出一個字元。</span><span class="sxs-lookup"><span data-stu-id="f994a-758">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="f994a-759">這是「t」功能。</span><span class="sxs-lookup"><span data-stu-id="f994a-759">This is for 't' functionality.</span></span>

- <span data-ttu-id="f994a-760">Vi 命令模式： `<t>`</span><span class="sxs-lookup"><span data-stu-id="f994a-760">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="f994a-761">SearchForward</span><span class="sxs-lookup"><span data-stu-id="f994a-761">SearchForward</span></span>

<span data-ttu-id="f994a-762">提示輸入搜尋字串，並在 AcceptLine 時起始搜尋。</span><span class="sxs-lookup"><span data-stu-id="f994a-762">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="f994a-763">Vi 插入模式： `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="f994a-763">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="f994a-764">Vi 命令模式： `<?>` 、 `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="f994a-764">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="f994a-765">自訂索引鍵系結</span><span class="sxs-lookup"><span data-stu-id="f994a-765">Custom Key Bindings</span></span>

<span data-ttu-id="f994a-766">PSReadLine 支援使用 Cmdlet 的自訂金鑰系結 `Set-PSReadLineKeyHandler` 。</span><span class="sxs-lookup"><span data-stu-id="f994a-766">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="f994a-767">大部分的自訂按鍵系結都會呼叫上述其中一項功能，例如</span><span class="sxs-lookup"><span data-stu-id="f994a-767">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="f994a-768">您可以將 ScriptBlock 系結至索引鍵。</span><span class="sxs-lookup"><span data-stu-id="f994a-768">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="f994a-769">ScriptBlock 可以進行任何您想要的動作。</span><span class="sxs-lookup"><span data-stu-id="f994a-769">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="f994a-770">一些實用的範例包括</span><span class="sxs-lookup"><span data-stu-id="f994a-770">Some useful examples include</span></span>

- <span data-ttu-id="f994a-771">編輯命令行</span><span class="sxs-lookup"><span data-stu-id="f994a-771">edit the command line</span></span>
- <span data-ttu-id="f994a-772">開啟新視窗 (例如說明) </span><span class="sxs-lookup"><span data-stu-id="f994a-772">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="f994a-773">變更目錄而不變更命令列</span><span class="sxs-lookup"><span data-stu-id="f994a-773">change directories without changing the command line</span></span>

<span data-ttu-id="f994a-774">ScriptBlock 會收到兩個引數：</span><span class="sxs-lookup"><span data-stu-id="f994a-774">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="f994a-775">`$key` -A **[ConsoleKeyInfo]** 物件，它是觸發自訂系結的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="f994a-775">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="f994a-776">如果您將相同的 ScriptBlock 系結至多個金鑰，且需要根據金鑰執行不同的動作，您可以檢查 $key。</span><span class="sxs-lookup"><span data-stu-id="f994a-776">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="f994a-777">許多自訂系結會忽略此引數。</span><span class="sxs-lookup"><span data-stu-id="f994a-777">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="f994a-778">`$arg` -任意引數。</span><span class="sxs-lookup"><span data-stu-id="f994a-778">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="f994a-779">通常，這會是使用者從索引鍵系結 DigitArgument 傳遞的整數引數。</span><span class="sxs-lookup"><span data-stu-id="f994a-779">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="f994a-780">如果您的系結不接受引數，則可以合理地忽略此引數。</span><span class="sxs-lookup"><span data-stu-id="f994a-780">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="f994a-781">讓我們看看將命令列新增至歷程記錄，而不執行的範例。</span><span class="sxs-lookup"><span data-stu-id="f994a-781">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="f994a-782">當您知道您忘了進行某個動作，但不想重新輸入您已經輸入的命令列時，這會很有用。</span><span class="sxs-lookup"><span data-stu-id="f994a-782">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

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

<span data-ttu-id="f994a-783">您可以在檔案中看到許多在 `SamplePSReadLineProfile.ps1` PSReadLine 模組資料夾中安裝的範例。</span><span class="sxs-lookup"><span data-stu-id="f994a-783">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="f994a-784">大部分的按鍵系結都會使用一些 helper 函數來編輯命令行。</span><span class="sxs-lookup"><span data-stu-id="f994a-784">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="f994a-785">這些 Api 記載于下一節。</span><span class="sxs-lookup"><span data-stu-id="f994a-785">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="f994a-786">自訂金鑰系結支援 Api</span><span class="sxs-lookup"><span data-stu-id="f994a-786">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="f994a-787">下列函式在 PSConsoleReadLine 中是公用的，但不能直接系結至索引鍵。</span><span class="sxs-lookup"><span data-stu-id="f994a-787">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="f994a-788">大部分在自訂金鑰系結中都很有用。</span><span class="sxs-lookup"><span data-stu-id="f994a-788">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="f994a-789">將命令列新增至歷程記錄，而不加以執行。</span><span class="sxs-lookup"><span data-stu-id="f994a-789">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="f994a-790">清除終止環形。</span><span class="sxs-lookup"><span data-stu-id="f994a-790">Clear the kill-ring.</span></span>  <span data-ttu-id="f994a-791">這大多用於測試。</span><span class="sxs-lookup"><span data-stu-id="f994a-791">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="f994a-792">從開始刪除長度字元。</span><span class="sxs-lookup"><span data-stu-id="f994a-792">Delete length characters from start.</span></span>  <span data-ttu-id="f994a-793">這種作業支援復原/重做。</span><span class="sxs-lookup"><span data-stu-id="f994a-793">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="f994a-794">根據使用者喜好設定來執行 Ding 動作。</span><span class="sxs-lookup"><span data-stu-id="f994a-794">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="f994a-795">這兩個函式會取出輸入緩衝區目前狀態的相關實用資訊。</span><span class="sxs-lookup"><span data-stu-id="f994a-795">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="f994a-796">第一個較常用於簡單的案例。</span><span class="sxs-lookup"><span data-stu-id="f994a-796">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="f994a-797">如果您的系結使用 Ast 更先進地執行，則會使用第二個。</span><span class="sxs-lookup"><span data-stu-id="f994a-797">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

```

<span data-ttu-id="f994a-798">Get-PSReadLineKeyHandler 使用這個函式，而且在自訂按鍵系結中可能不實用。</span><span class="sxs-lookup"><span data-stu-id="f994a-798">This function is used by Get-PSReadLineKeyHandler and probably isn't useful in a custom key binding.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="f994a-799">Get-PSReadLineOption 使用這個函式，而且在自訂索引鍵系結中可能不太實用。</span><span class="sxs-lookup"><span data-stu-id="f994a-799">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="f994a-800">如果未在命令列上選取任何專案，則會以開始和長度傳回-1。</span><span class="sxs-lookup"><span data-stu-id="f994a-800">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="f994a-801">如果在命令列上有選取專案，則會傳回選取範圍的開始和長度。</span><span class="sxs-lookup"><span data-stu-id="f994a-801">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="f994a-802">在游標處插入字元或字串。</span><span class="sxs-lookup"><span data-stu-id="f994a-802">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="f994a-803">這種作業支援復原/重做。</span><span class="sxs-lookup"><span data-stu-id="f994a-803">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="f994a-804">這是要 PSReadLine 的主要進入點。</span><span class="sxs-lookup"><span data-stu-id="f994a-804">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="f994a-805">它不支援遞迴，因此在自訂索引鍵系結中並不有用。</span><span class="sxs-lookup"><span data-stu-id="f994a-805">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="f994a-806">Remove-PSReadLineKeyHandler 使用這個函式，而且在自訂索引鍵系結中可能不太實用。</span><span class="sxs-lookup"><span data-stu-id="f994a-806">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="f994a-807">取代部分輸入。</span><span class="sxs-lookup"><span data-stu-id="f994a-807">Replace some of the input.</span></span> <span data-ttu-id="f994a-808">這種作業支援復原/重做。</span><span class="sxs-lookup"><span data-stu-id="f994a-808">This operation supports undo/redo.</span></span> <span data-ttu-id="f994a-809">這是優先于 Delete，後面接著 Insert，因為它會被視為復原的單一動作。</span><span class="sxs-lookup"><span data-stu-id="f994a-809">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="f994a-810">將游標移至指定的位移。</span><span class="sxs-lookup"><span data-stu-id="f994a-810">Move the cursor to the given offset.</span></span> <span data-ttu-id="f994a-811">不追蹤資料指標移動以進行復原。</span><span class="sxs-lookup"><span data-stu-id="f994a-811">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="f994a-812">此函式是 Cmdlet PSReadLineOption 所使用的 helper 方法，但對於想要暫時變更設定的自訂按鍵系結來說可能很有用。</span><span class="sxs-lookup"><span data-stu-id="f994a-812">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="f994a-813">此 helper 方法是用於接受 DigitArgument 的自訂系結。</span><span class="sxs-lookup"><span data-stu-id="f994a-813">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="f994a-814">一般呼叫看起來像</span><span class="sxs-lookup"><span data-stu-id="f994a-814">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="note"></a><span data-ttu-id="f994a-815">注意</span><span class="sxs-lookup"><span data-stu-id="f994a-815">Note</span></span>

### <a name="command-history"></a><span data-ttu-id="f994a-816">命令歷程記錄</span><span class="sxs-lookup"><span data-stu-id="f994a-816">Command History</span></span>

<span data-ttu-id="f994a-817">PSReadLine 會維護一個記錄檔，其中包含您從命令列輸入的所有命令和資料。</span><span class="sxs-lookup"><span data-stu-id="f994a-817">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="f994a-818">這可能包含機密資料，包括密碼。</span><span class="sxs-lookup"><span data-stu-id="f994a-818">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="f994a-819">例如，如果您使用指令 `ConvertTo-SecureString` 程式，密碼就會以純文字的形式記錄在記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="f994a-819">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="f994a-820">記錄檔是名為的檔案 `$($host.Name)_history.txt` 。</span><span class="sxs-lookup"><span data-stu-id="f994a-820">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="f994a-821">在 Windows 系統上，歷程記錄檔案會儲存在中 `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` 。</span><span class="sxs-lookup"><span data-stu-id="f994a-821">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="f994a-822">意見反應 & 參與 PSReadLine</span><span class="sxs-lookup"><span data-stu-id="f994a-822">Feedback & Contributing To PSReadLine</span></span>

[<span data-ttu-id="f994a-823">GitHub 上的 PSReadLine</span><span class="sxs-lookup"><span data-stu-id="f994a-823">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="f994a-824">您可以隨時提交提取要求或在 GitHub 頁面上提交意見反應。</span><span class="sxs-lookup"><span data-stu-id="f994a-824">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="f994a-825">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f994a-825">See Also</span></span>

<span data-ttu-id="f994a-826">PSReadLine 會受到 GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) 程式庫的高度影響。</span><span class="sxs-lookup"><span data-stu-id="f994a-826">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>
