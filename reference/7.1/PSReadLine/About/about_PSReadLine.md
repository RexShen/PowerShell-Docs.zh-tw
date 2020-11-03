---
description: PSReadLine 在 PowerShell 主控台中提供改良的命令列編輯體驗。
keywords: powershell
Locale: en-US
ms.date: 02/10/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 關於 PSReadLine
ms.openlocfilehash: 1188b8dc0b4099a7c1dcc472e3b02c2d4fa908bc
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206691"
---
# <a name="psreadline"></a><span data-ttu-id="b1e15-104">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="b1e15-104">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="b1e15-105">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="b1e15-105">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="b1e15-106">簡短描述</span><span class="sxs-lookup"><span data-stu-id="b1e15-106">SHORT DESCRIPTION</span></span>

<span data-ttu-id="b1e15-107">PSReadLine 在 PowerShell 主控台中提供改良的命令列編輯體驗。</span><span class="sxs-lookup"><span data-stu-id="b1e15-107">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="b1e15-108">詳細描述</span><span class="sxs-lookup"><span data-stu-id="b1e15-108">LONG DESCRIPTION</span></span>

<span data-ttu-id="b1e15-109">PSReadLine 2.0 為 PowerShell 主控台提供功能強大的命令列編輯體驗。</span><span class="sxs-lookup"><span data-stu-id="b1e15-109">PSReadLine 2.0 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="b1e15-110">它提供：</span><span class="sxs-lookup"><span data-stu-id="b1e15-110">It provides:</span></span>

- <span data-ttu-id="b1e15-111">命令列的語法著色</span><span class="sxs-lookup"><span data-stu-id="b1e15-111">Syntax coloring of the command line</span></span>
- <span data-ttu-id="b1e15-112">語法錯誤的視覺指示</span><span class="sxs-lookup"><span data-stu-id="b1e15-112">A visual indication of syntax errors</span></span>
- <span data-ttu-id="b1e15-113"> (編輯和歷程記錄的更佳多行體驗) </span><span class="sxs-lookup"><span data-stu-id="b1e15-113">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="b1e15-114">可自訂的按鍵系結</span><span class="sxs-lookup"><span data-stu-id="b1e15-114">Customizable key bindings</span></span>
- <span data-ttu-id="b1e15-115">Cmd 和 Emacs 模式</span><span class="sxs-lookup"><span data-stu-id="b1e15-115">Cmd and Emacs modes</span></span>
- <span data-ttu-id="b1e15-116">許多設定選項</span><span class="sxs-lookup"><span data-stu-id="b1e15-116">Many configuration options</span></span>
- <span data-ttu-id="b1e15-117">Bash 樣式完成 (在 Cmd 模式中為選擇性，預設為 Emacs 模式) </span><span class="sxs-lookup"><span data-stu-id="b1e15-117">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="b1e15-118">Emacs yank/kill-環形</span><span class="sxs-lookup"><span data-stu-id="b1e15-118">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="b1e15-119">以 PowerShell 權杖為基礎的「單字」移動和終止</span><span class="sxs-lookup"><span data-stu-id="b1e15-119">PowerShell token based "word" movement and kill</span></span>

<span data-ttu-id="b1e15-120">下列函式可在類別 **[PSConsoleReadLine]** 中使用。</span><span class="sxs-lookup"><span data-stu-id="b1e15-120">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]** .</span></span>

> [!NOTE]
> <span data-ttu-id="b1e15-121">從 PowerShell 7.0 開始，如果偵測到螢幕讀取程式，PowerShell 會略過在 Windows 上自動載入 PSReadLine。</span><span class="sxs-lookup"><span data-stu-id="b1e15-121">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="b1e15-122">PSReadLine 目前無法與螢幕讀取器順利搭配運作。</span><span class="sxs-lookup"><span data-stu-id="b1e15-122">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="b1e15-123">Windows 上 PowerShell 7.0 的預設轉譯和格式可正常運作。</span><span class="sxs-lookup"><span data-stu-id="b1e15-123">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="b1e15-124">如有必要，您可以手動載入模組。</span><span class="sxs-lookup"><span data-stu-id="b1e15-124">You can manually load the module if necessary.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="b1e15-125">基本編輯函數</span><span class="sxs-lookup"><span data-stu-id="b1e15-125">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="b1e15-126">中止</span><span class="sxs-lookup"><span data-stu-id="b1e15-126">Abort</span></span>

<span data-ttu-id="b1e15-127">中止目前的動作，例如累加式歷程記錄搜尋。</span><span class="sxs-lookup"><span data-stu-id="b1e15-127">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="b1e15-128">Emacs： `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-128">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="b1e15-129">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="b1e15-129">AcceptAndGetNext</span></span>

<span data-ttu-id="b1e15-130">嘗試執行目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="b1e15-130">Attempt to execute the current input.</span></span> <span data-ttu-id="b1e15-131">如果可以像 AcceptLine) 一樣執行 (，則會在下一次呼叫 ReadLine 時，重新叫用歷程記錄中的下一個專案。</span><span class="sxs-lookup"><span data-stu-id="b1e15-131">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="b1e15-132">Emacs： `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-132">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="b1e15-133">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="b1e15-133">AcceptLine</span></span>

<span data-ttu-id="b1e15-134">嘗試執行目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="b1e15-134">Attempt to execute the current input.</span></span> <span data-ttu-id="b1e15-135">如果目前的輸入不完整 (例如遺漏右括弧、方括弧或引號，則接續提示會顯示在下一行，而 PSReadLine 會等候按鍵編輯目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="b1e15-135">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="b1e15-136">Cmd： `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-136">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="b1e15-137">Emacs： `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-137">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="b1e15-138">Vi 插入模式： `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-138">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="b1e15-139">AddLine</span><span class="sxs-lookup"><span data-stu-id="b1e15-139">AddLine</span></span>

<span data-ttu-id="b1e15-140">接續提示會顯示在下一行，而 PSReadLine 會等候按鍵編輯目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="b1e15-140">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="b1e15-141">這對於將多行輸入輸入為單一命令很有用，即使單一行本身已完成輸入也是一樣。</span><span class="sxs-lookup"><span data-stu-id="b1e15-141">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="b1e15-142">Cmd： `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-142">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="b1e15-143">Emacs： `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-143">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="b1e15-144">Vi 插入模式： `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-144">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="b1e15-145">Vi 命令模式： `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-145">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="b1e15-146">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="b1e15-146">BackwardDeleteChar</span></span>

<span data-ttu-id="b1e15-147">刪除游標之前的字元。</span><span class="sxs-lookup"><span data-stu-id="b1e15-147">Delete the character before the cursor.</span></span>

- <span data-ttu-id="b1e15-148">Cmd： `<Backspace>` ， `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-148">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="b1e15-149">Emacs： `<Backspace>` 、 `<Ctrl+Backspace>` 、 `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-149">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="b1e15-150">Vi 插入模式： `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-150">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="b1e15-151">Vi 命令模式： `<X>` 、 `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-151">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="b1e15-152">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="b1e15-152">BackwardDeleteLine</span></span>

<span data-ttu-id="b1e15-153">如同 BackwardKillLine-刪除從點到行首的文字，但不會將已刪除的文字放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="b1e15-153">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="b1e15-154">Cmd： `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-154">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="b1e15-155">Vi 插入模式： `<Ctrl+u>` 、 `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-155">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="b1e15-156">Vi 命令模式： `<Ctrl+u>` 、 `<Ctrl+Home>` 、 `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-156">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`, `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="b1e15-157">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="b1e15-157">BackwardDeleteWord</span></span>

<span data-ttu-id="b1e15-158">刪除上一個字組。</span><span class="sxs-lookup"><span data-stu-id="b1e15-158">Deletes the previous word.</span></span>

- <span data-ttu-id="b1e15-159">Vi 命令模式： `<Ctrl+w>` 、 `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-159">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="b1e15-160">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="b1e15-160">BackwardKillLine</span></span>

<span data-ttu-id="b1e15-161">清除輸入至資料指標開頭的輸入。</span><span class="sxs-lookup"><span data-stu-id="b1e15-161">Clear the input from the start of the input to the cursor.</span></span> <span data-ttu-id="b1e15-162">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="b1e15-162">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="b1e15-163">Emacs： `<Ctrl+u>` ， `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-163">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="b1e15-164">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="b1e15-164">BackwardKillWord</span></span>

<span data-ttu-id="b1e15-165">清除從目前單字開頭到游標處的輸入。</span><span class="sxs-lookup"><span data-stu-id="b1e15-165">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="b1e15-166">如果游標在單字之間，則會從上一個單字開頭開始清除輸入至游標。</span><span class="sxs-lookup"><span data-stu-id="b1e15-166">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="b1e15-167">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="b1e15-167">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="b1e15-168">Cmd： `<Ctrl+Backspace>` ， `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-168">Cmd: `<Ctrl+Backspace>`, `<Ctrl+w>`</span></span>
- <span data-ttu-id="b1e15-169">Emacs： `<Alt+Backspace>` ， `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-169">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="b1e15-170">Vi 插入模式： `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-170">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="b1e15-171">Vi 命令模式： `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-171">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="b1e15-172">CancelLine</span><span class="sxs-lookup"><span data-stu-id="b1e15-172">CancelLine</span></span>

<span data-ttu-id="b1e15-173">取消目前的輸入，將輸入保留在畫面上，但返回主機，以便再次評估提示。</span><span class="sxs-lookup"><span data-stu-id="b1e15-173">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="b1e15-174">Vi 插入模式： `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-174">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="b1e15-175">Vi 命令模式： `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-175">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="b1e15-176">複製</span><span class="sxs-lookup"><span data-stu-id="b1e15-176">Copy</span></span>

<span data-ttu-id="b1e15-177">將選取的區域複製到系統剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="b1e15-177">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="b1e15-178">如果未選取任何區域，請複製整行。</span><span class="sxs-lookup"><span data-stu-id="b1e15-178">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="b1e15-179">Cmd： `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-179">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="b1e15-180">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="b1e15-180">CopyOrCancelLine</span></span>

<span data-ttu-id="b1e15-181">如果已選取文字，請複製到剪貼簿，否則請取消該行。</span><span class="sxs-lookup"><span data-stu-id="b1e15-181">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="b1e15-182">Cmd： `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-182">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="b1e15-183">Emacs： `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-183">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="b1e15-184">剪下</span><span class="sxs-lookup"><span data-stu-id="b1e15-184">Cut</span></span>

<span data-ttu-id="b1e15-185">刪除選取的區域，將已刪除的文字放入系統剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="b1e15-185">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="b1e15-186">Cmd： `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-186">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="b1e15-187">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="b1e15-187">DeleteChar</span></span>

<span data-ttu-id="b1e15-188">刪除游標下的字元。</span><span class="sxs-lookup"><span data-stu-id="b1e15-188">Delete the character under the cursor.</span></span>

- <span data-ttu-id="b1e15-189">Cmd： `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-189">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="b1e15-190">Emacs： `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-190">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="b1e15-191">Vi 插入模式： `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-191">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="b1e15-192">Vi 命令模式： `<Delete>` 、 `<x>` 、 `<d,l>` 、 `<d,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-192">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Spacebar>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="b1e15-193">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="b1e15-193">DeleteCharOrExit</span></span>

<span data-ttu-id="b1e15-194">刪除游標下的字元，如果行是空的，請結束進程。</span><span class="sxs-lookup"><span data-stu-id="b1e15-194">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="b1e15-195">Emacs： `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-195">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofbuffer"></a><span data-ttu-id="b1e15-196">DeleteEndOfBuffer</span><span class="sxs-lookup"><span data-stu-id="b1e15-196">DeleteEndOfBuffer</span></span>

<span data-ttu-id="b1e15-197">刪除多行緩衝區的結尾。</span><span class="sxs-lookup"><span data-stu-id="b1e15-197">Deletes to the end of the multiline buffer.</span></span>

- <span data-ttu-id="b1e15-198">Vi 命令模式： `<d,G>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-198">Vi command mode: `<d,G>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="b1e15-199">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="b1e15-199">DeleteEndOfWord</span></span>

<span data-ttu-id="b1e15-200">刪除到字尾。</span><span class="sxs-lookup"><span data-stu-id="b1e15-200">Delete to the end of the word.</span></span>

- <span data-ttu-id="b1e15-201">Vi 命令模式： `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-201">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="b1e15-202">DeleteLine</span><span class="sxs-lookup"><span data-stu-id="b1e15-202">DeleteLine</span></span>

<span data-ttu-id="b1e15-203">刪除多行緩衝區的目前邏輯行，以啟用復原。</span><span class="sxs-lookup"><span data-stu-id="b1e15-203">Deletes the current logical line of a multiline buffer, enabling undo.</span></span>

- <span data-ttu-id="b1e15-204">Vi 命令模式： `<d,d>` 、 `<d,_>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-204">Vi command mode: `<d,d>`, `<d,_>`</span></span>

### <a name="deletepreviouslines"></a><span data-ttu-id="b1e15-205">DeletePreviousLines</span><span class="sxs-lookup"><span data-stu-id="b1e15-205">DeletePreviousLines</span></span>

<span data-ttu-id="b1e15-206">刪除多行緩衝區中之前要求的邏輯行和目前的邏輯行。</span><span class="sxs-lookup"><span data-stu-id="b1e15-206">Deletes the previous requested logical lines and the current logical line in a multiline buffer.</span></span>

- <span data-ttu-id="b1e15-207">Vi 命令模式： `<d,k>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-207">Vi command mode: `<d,k>`</span></span>

### <a name="deleterelativelines"></a><span data-ttu-id="b1e15-208">DeleteRelativeLines</span><span class="sxs-lookup"><span data-stu-id="b1e15-208">DeleteRelativeLines</span></span>

<span data-ttu-id="b1e15-209">從緩衝區的開頭刪除多行緩衝區中目前的邏輯行。</span><span class="sxs-lookup"><span data-stu-id="b1e15-209">Deletes from the beginning of the buffer to the current logical line in a multiline buffer.</span></span>

<span data-ttu-id="b1e15-210">最多有 Vi 個命令， `<d,g,g>` 命令前面會加上指定絕對行號的數值引數，這會和目前的行號一起組成要刪除的行範圍。</span><span class="sxs-lookup"><span data-stu-id="b1e15-210">As most Vi commands, the `<d,g,g>` command can be prepended with a numeric argument that specifies an absolute line number, which, together with the current line number, make up a range of lines to be deleted.</span></span>
<span data-ttu-id="b1e15-211">如果未指定，則數值引數會預設為1，這會參考多行緩衝區中的第一個邏輯行。</span><span class="sxs-lookup"><span data-stu-id="b1e15-211">If not specified, the numeric argument defaults to 1, which refers to the first logical line in a multiline buffer.</span></span>

<span data-ttu-id="b1e15-212">要從多行刪除的實際行數，會計算為目前的邏輯行號和指定的數值引數之間的差異，因此可能是負數。</span><span class="sxs-lookup"><span data-stu-id="b1e15-212">The actual number of lines to be deleted from the multiline is computed as the difference between the current logical line number and the specified numeric argument, which can thus be negative.</span></span> <span data-ttu-id="b1e15-213">因此，方法名稱的 _相對_ 部分。</span><span class="sxs-lookup"><span data-stu-id="b1e15-213">Hence the _relative_ part of method name.</span></span>

- <span data-ttu-id="b1e15-214">Vi 命令模式： `<d,g,g>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-214">Vi command mode: `<d,g,g>`</span></span>

### <a name="deletenextlines"></a><span data-ttu-id="b1e15-215">DeleteNextLines</span><span class="sxs-lookup"><span data-stu-id="b1e15-215">DeleteNextLines</span></span>

<span data-ttu-id="b1e15-216">刪除多行緩衝區中目前的邏輯行和下一個要求的邏輯行。</span><span class="sxs-lookup"><span data-stu-id="b1e15-216">Deletes the current logical line and the next requested logical lines in a multiline buffer.</span></span>

- <span data-ttu-id="b1e15-217">Vi 命令模式： `<d,j>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-217">Vi command mode: `<d,j>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="b1e15-218">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="b1e15-218">DeleteLineToFirstChar</span></span>

<span data-ttu-id="b1e15-219">將游標的文字刪除到行的第一個非空白字元。</span><span class="sxs-lookup"><span data-stu-id="b1e15-219">Deletes text from the cursor to the first non-blank character of the line.</span></span>

- <span data-ttu-id="b1e15-220">Vi 命令模式： `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-220">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="b1e15-221">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="b1e15-221">DeleteToEnd</span></span>

<span data-ttu-id="b1e15-222">刪除至行尾。</span><span class="sxs-lookup"><span data-stu-id="b1e15-222">Delete to the end of the line.</span></span>

- <span data-ttu-id="b1e15-223">Vi 命令模式： `<D>` 、 `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-223">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="b1e15-224">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="b1e15-224">DeleteWord</span></span>

<span data-ttu-id="b1e15-225">刪除下一個字組。</span><span class="sxs-lookup"><span data-stu-id="b1e15-225">Delete the next word.</span></span>

- <span data-ttu-id="b1e15-226">Vi 命令模式： `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-226">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="b1e15-227">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="b1e15-227">ForwardDeleteLine</span></span>

<span data-ttu-id="b1e15-228">如同 ForwardKillLine-刪除從點到行尾的文字，但不會將已刪除的文字放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="b1e15-228">Like ForwardKillLine - deletes text from the point to the end of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="b1e15-229">Cmd： `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-229">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="b1e15-230">Vi 插入模式： `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-230">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="b1e15-231">Vi 命令模式： `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-231">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="b1e15-232">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="b1e15-232">InsertLineAbove</span></span>

<span data-ttu-id="b1e15-233">無論游標位於目前的行上，都會在目前的行上方建立新的空白行。</span><span class="sxs-lookup"><span data-stu-id="b1e15-233">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="b1e15-234">游標移至新行的開頭。</span><span class="sxs-lookup"><span data-stu-id="b1e15-234">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="b1e15-235">Cmd： `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-235">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="b1e15-236">InsertLineBelow</span><span class="sxs-lookup"><span data-stu-id="b1e15-236">InsertLineBelow</span></span>

<span data-ttu-id="b1e15-237">目前的行下方會建立新的空白行，而不論游標在目前的行上。</span><span class="sxs-lookup"><span data-stu-id="b1e15-237">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="b1e15-238">游標移至新行的開頭。</span><span class="sxs-lookup"><span data-stu-id="b1e15-238">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="b1e15-239">Cmd： `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-239">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="b1e15-240">InvertCase</span><span class="sxs-lookup"><span data-stu-id="b1e15-240">InvertCase</span></span>

<span data-ttu-id="b1e15-241">將目前字元的大小寫反轉，並移至下一個字元。</span><span class="sxs-lookup"><span data-stu-id="b1e15-241">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="b1e15-242">Vi 命令模式： `<~>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-242">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="b1e15-243">KillLine</span><span class="sxs-lookup"><span data-stu-id="b1e15-243">KillLine</span></span>

<span data-ttu-id="b1e15-244">清除游標至輸入結尾的輸入。</span><span class="sxs-lookup"><span data-stu-id="b1e15-244">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="b1e15-245">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="b1e15-245">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="b1e15-246">Emacs： `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-246">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="b1e15-247">KillRegion</span><span class="sxs-lookup"><span data-stu-id="b1e15-247">KillRegion</span></span>

<span data-ttu-id="b1e15-248">終止游標與標記之間的文字。</span><span class="sxs-lookup"><span data-stu-id="b1e15-248">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="b1e15-249">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="b1e15-249">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="b1e15-250">KillWord</span><span class="sxs-lookup"><span data-stu-id="b1e15-250">KillWord</span></span>

<span data-ttu-id="b1e15-251">清除游標到目前單字結尾的輸入。</span><span class="sxs-lookup"><span data-stu-id="b1e15-251">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="b1e15-252">如果游標在單字之間，則會從資料指標清除輸入至下一個單字的結尾。</span><span class="sxs-lookup"><span data-stu-id="b1e15-252">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="b1e15-253">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="b1e15-253">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="b1e15-254">Cmd： `<Alt+d>` ， `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-254">Cmd: `<Alt+d>`, `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="b1e15-255">Emacs： `<Alt+d>` ， `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-255">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="b1e15-256">Vi 插入模式： `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-256">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="b1e15-257">Vi 命令模式： `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-257">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="b1e15-258">貼上</span><span class="sxs-lookup"><span data-stu-id="b1e15-258">Paste</span></span>

<span data-ttu-id="b1e15-259">貼上系統剪貼簿中的文字。</span><span class="sxs-lookup"><span data-stu-id="b1e15-259">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="b1e15-260">Cmd： `<Ctrl+v>` ， `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-260">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="b1e15-261">Vi 插入模式： `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-261">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="b1e15-262">Vi 命令模式： `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-262">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b1e15-263">使用 **Paste** 函式時，剪貼簿緩衝區的整個內容會貼到 PSReadLine 的輸入緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="b1e15-263">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="b1e15-264">輸入緩衝區接著會傳遞至 PowerShell 剖析器。</span><span class="sxs-lookup"><span data-stu-id="b1e15-264">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="b1e15-265">使用主控台應用程式的 **按右鍵** [貼上] 方法貼上的輸入會一次複製到輸入緩衝區一個字元。</span><span class="sxs-lookup"><span data-stu-id="b1e15-265">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="b1e15-266">當換行字元時，輸入緩衝區會傳遞給剖析器。</span><span class="sxs-lookup"><span data-stu-id="b1e15-266">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="b1e15-267">因此，輸入會一次剖析一行。</span><span class="sxs-lookup"><span data-stu-id="b1e15-267">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="b1e15-268">貼上方法之間的差異會導致不同的執行行為。</span><span class="sxs-lookup"><span data-stu-id="b1e15-268">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="b1e15-269">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="b1e15-269">PasteAfter</span></span>

<span data-ttu-id="b1e15-270">將剪貼簿貼到游標之後，將游標移至貼上文字的結尾。</span><span class="sxs-lookup"><span data-stu-id="b1e15-270">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="b1e15-271">Vi 命令模式： `<p>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-271">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="b1e15-272">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="b1e15-272">PasteBefore</span></span>

<span data-ttu-id="b1e15-273">將剪貼簿貼到游標之前，將游標移至貼上文字的結尾。</span><span class="sxs-lookup"><span data-stu-id="b1e15-273">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="b1e15-274">Vi 命令模式： `<P>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-274">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="b1e15-275">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="b1e15-275">PrependAndAccept</span></span>

<span data-ttu-id="b1e15-276">在前面加上 ' # ' 並接受該行。</span><span class="sxs-lookup"><span data-stu-id="b1e15-276">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="b1e15-277">Vi 命令模式： `<#>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-277">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="b1e15-278">取消復原</span><span class="sxs-lookup"><span data-stu-id="b1e15-278">Redo</span></span>

<span data-ttu-id="b1e15-279">復原復原。</span><span class="sxs-lookup"><span data-stu-id="b1e15-279">Undo an undo.</span></span>

- <span data-ttu-id="b1e15-280">Cmd： `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-280">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="b1e15-281">Vi 插入模式： `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-281">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="b1e15-282">Vi 命令模式： `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-282">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="b1e15-283">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="b1e15-283">RepeatLastCommand</span></span>

<span data-ttu-id="b1e15-284">重複上次修改文字。</span><span class="sxs-lookup"><span data-stu-id="b1e15-284">Repeat the last text modification.</span></span>

- <span data-ttu-id="b1e15-285">Vi 命令模式： `<.>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-285">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="b1e15-286">RevertLine</span><span class="sxs-lookup"><span data-stu-id="b1e15-286">RevertLine</span></span>

<span data-ttu-id="b1e15-287">將所有輸入還原為目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="b1e15-287">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="b1e15-288">Cmd： `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-288">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="b1e15-289">Emacs： `<Alt+r>` ， `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-289">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="b1e15-290">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="b1e15-290">ShellBackwardKillWord</span></span>

<span data-ttu-id="b1e15-291">清除從目前單字開頭到游標處的輸入。</span><span class="sxs-lookup"><span data-stu-id="b1e15-291">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="b1e15-292">如果游標在單字之間，則會從上一個單字開頭開始清除輸入至游標。</span><span class="sxs-lookup"><span data-stu-id="b1e15-292">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="b1e15-293">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="b1e15-293">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="b1e15-294">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="b1e15-294">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="b1e15-295">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="b1e15-295">ShellKillWord</span></span>

<span data-ttu-id="b1e15-296">清除游標到目前單字結尾的輸入。</span><span class="sxs-lookup"><span data-stu-id="b1e15-296">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="b1e15-297">如果游標在單字之間，則會從資料指標清除輸入至下一個單字的結尾。</span><span class="sxs-lookup"><span data-stu-id="b1e15-297">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="b1e15-298">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="b1e15-298">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="b1e15-299">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="b1e15-299">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="b1e15-300">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="b1e15-300">SwapCharacters</span></span>

<span data-ttu-id="b1e15-301">交換目前的字元和前一個字元。</span><span class="sxs-lookup"><span data-stu-id="b1e15-301">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="b1e15-302">Emacs： `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-302">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="b1e15-303">Vi 插入模式： `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-303">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="b1e15-304">Vi 命令模式： `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-304">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="b1e15-305">復原</span><span class="sxs-lookup"><span data-stu-id="b1e15-305">Undo</span></span>

<span data-ttu-id="b1e15-306">復原先前的編輯。</span><span class="sxs-lookup"><span data-stu-id="b1e15-306">Undo a previous edit.</span></span>

- <span data-ttu-id="b1e15-307">Cmd： `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-307">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="b1e15-308">Emacs： `<Ctrl+_>` ， `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-308">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="b1e15-309">Vi 插入模式： `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-309">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="b1e15-310">Vi 命令模式： `<Ctrl+z>` 、 `<u>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-310">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="b1e15-311">UndoAll</span><span class="sxs-lookup"><span data-stu-id="b1e15-311">UndoAll</span></span>

<span data-ttu-id="b1e15-312">復原所有先前編輯的行。</span><span class="sxs-lookup"><span data-stu-id="b1e15-312">Undo all previous edits for line.</span></span>

- <span data-ttu-id="b1e15-313">Vi 命令模式： `<U>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-313">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="b1e15-314">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="b1e15-314">UnixWordRubout</span></span>

<span data-ttu-id="b1e15-315">清除從目前單字開頭到游標處的輸入。</span><span class="sxs-lookup"><span data-stu-id="b1e15-315">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="b1e15-316">如果游標在單字之間，則會從上一個單字開頭開始清除輸入至游標。</span><span class="sxs-lookup"><span data-stu-id="b1e15-316">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="b1e15-317">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="b1e15-317">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="b1e15-318">Emacs： `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-318">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="b1e15-319">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="b1e15-319">ValidateAndAcceptLine</span></span>

<span data-ttu-id="b1e15-320">嘗試執行目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="b1e15-320">Attempt to execute the current input.</span></span> <span data-ttu-id="b1e15-321">如果目前的輸入不完整 (例如遺漏右括弧、方括弧或引號，則接續提示會顯示在下一行，而 PSReadLine 會等候按鍵編輯目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="b1e15-321">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="b1e15-322">Emacs： `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-322">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="b1e15-323">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="b1e15-323">ViAcceptLine</span></span>

<span data-ttu-id="b1e15-324">接受行並切換至插入模式。</span><span class="sxs-lookup"><span data-stu-id="b1e15-324">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="b1e15-325">Vi 命令模式： `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-325">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="b1e15-326">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="b1e15-326">ViAcceptLineOrExit</span></span>

<span data-ttu-id="b1e15-327">如同 Emacs 模式中的 DeleteCharOrExit，但會接受行，而不是刪除字元。</span><span class="sxs-lookup"><span data-stu-id="b1e15-327">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="b1e15-328">Vi 插入模式： `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-328">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="b1e15-329">Vi 命令模式： `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-329">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="b1e15-330">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="b1e15-330">ViAppendLine</span></span>

<span data-ttu-id="b1e15-331">新行會插入目前的行下方。</span><span class="sxs-lookup"><span data-stu-id="b1e15-331">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="b1e15-332">Vi 命令模式： `<o>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-332">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="b1e15-333">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="b1e15-333">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="b1e15-334">刪除先前的單字，只使用空白字元做為文字分隔符號。</span><span class="sxs-lookup"><span data-stu-id="b1e15-334">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="b1e15-335">Vi 命令模式： `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-335">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="b1e15-336">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="b1e15-336">ViBackwardGlob</span></span>

<span data-ttu-id="b1e15-337">將游標移回上一個單字的開頭，只使用空白字元做為分隔符號。</span><span class="sxs-lookup"><span data-stu-id="b1e15-337">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="b1e15-338">Vi 命令模式： `<B>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-338">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="b1e15-339">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="b1e15-339">ViDeleteBrace</span></span>

<span data-ttu-id="b1e15-340">尋找相符的括弧、括弧或方括弧，並刪除內的所有內容，包括括弧。</span><span class="sxs-lookup"><span data-stu-id="b1e15-340">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="b1e15-341">Vi 命令模式： `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-341">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="b1e15-342">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="b1e15-342">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="b1e15-343">刪除到字尾。</span><span class="sxs-lookup"><span data-stu-id="b1e15-343">Delete to the end of the word.</span></span>

- <span data-ttu-id="b1e15-344">Vi 命令模式： `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-344">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="b1e15-345">ViDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="b1e15-345">ViDeleteGlob</span></span>

<span data-ttu-id="b1e15-346">刪除下一個 glob (以空白字元分隔的單字) 。</span><span class="sxs-lookup"><span data-stu-id="b1e15-346">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="b1e15-347">Vi 命令模式： `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-347">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="b1e15-348">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="b1e15-348">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="b1e15-349">刪除指定的字元。</span><span class="sxs-lookup"><span data-stu-id="b1e15-349">Deletes until given character.</span></span>

- <span data-ttu-id="b1e15-350">Vi 命令模式： `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-350">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="b1e15-351">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="b1e15-351">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="b1e15-352">刪除指定的字元。</span><span class="sxs-lookup"><span data-stu-id="b1e15-352">Deletes until given character.</span></span>

- <span data-ttu-id="b1e15-353">Vi 命令模式： `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-353">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="b1e15-354">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="b1e15-354">ViDeleteToChar</span></span>

<span data-ttu-id="b1e15-355">刪除指定的字元。</span><span class="sxs-lookup"><span data-stu-id="b1e15-355">Deletes until given character.</span></span>

- <span data-ttu-id="b1e15-356">Vi 命令模式： `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-356">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="b1e15-357">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="b1e15-357">ViDeleteToCharBackward</span></span>

<span data-ttu-id="b1e15-358">在指定的字元之前反向刪除。</span><span class="sxs-lookup"><span data-stu-id="b1e15-358">Deletes backwards until given character.</span></span>

- <span data-ttu-id="b1e15-359">Vi 命令模式： `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-359">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="b1e15-360">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="b1e15-360">ViInsertAtBegining</span></span>

<span data-ttu-id="b1e15-361">切換至插入模式，並將游標放在行首。</span><span class="sxs-lookup"><span data-stu-id="b1e15-361">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="b1e15-362">Vi 命令模式： `<I>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-362">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="b1e15-363">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="b1e15-363">ViInsertAtEnd</span></span>

<span data-ttu-id="b1e15-364">切換至插入模式，並將游標放在行尾。</span><span class="sxs-lookup"><span data-stu-id="b1e15-364">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="b1e15-365">Vi 命令模式： `<A>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-365">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="b1e15-366">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="b1e15-366">ViInsertLine</span></span>

<span data-ttu-id="b1e15-367">新的行會插入到目前這一行的上方。</span><span class="sxs-lookup"><span data-stu-id="b1e15-367">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="b1e15-368">Vi 命令模式： `<O>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-368">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="b1e15-369">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="b1e15-369">ViInsertWithAppend</span></span>

<span data-ttu-id="b1e15-370">從目前的行位置附加。</span><span class="sxs-lookup"><span data-stu-id="b1e15-370">Append from the current line position.</span></span>

- <span data-ttu-id="b1e15-371">Vi 命令模式： `<a>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-371">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="b1e15-372">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="b1e15-372">ViInsertWithDelete</span></span>

<span data-ttu-id="b1e15-373">刪除目前的字元並切換至插入模式。</span><span class="sxs-lookup"><span data-stu-id="b1e15-373">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="b1e15-374">Vi 命令模式： `<s>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-374">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="b1e15-375">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="b1e15-375">ViJoinLines</span></span>

<span data-ttu-id="b1e15-376">加入目前的行和下一行。</span><span class="sxs-lookup"><span data-stu-id="b1e15-376">Joins the current line and the next line.</span></span>

- <span data-ttu-id="b1e15-377">Vi 命令模式： `<J>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-377">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="b1e15-378">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="b1e15-378">ViReplaceLine</span></span>

<span data-ttu-id="b1e15-379">清除整個命令列。</span><span class="sxs-lookup"><span data-stu-id="b1e15-379">Erase the entire command line.</span></span>

- <span data-ttu-id="b1e15-380">Vi 命令模式： `<S>` 、 `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-380">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="b1e15-381">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="b1e15-381">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="b1e15-382">取代指定的字元。</span><span class="sxs-lookup"><span data-stu-id="b1e15-382">Replaces until given character.</span></span>

- <span data-ttu-id="b1e15-383">Vi 命令模式： `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-383">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="b1e15-384">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="b1e15-384">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="b1e15-385">取代指定的字元。</span><span class="sxs-lookup"><span data-stu-id="b1e15-385">Replaces until given character.</span></span>

- <span data-ttu-id="b1e15-386">Vi 命令模式： `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-386">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="b1e15-387">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="b1e15-387">ViReplaceToChar</span></span>

<span data-ttu-id="b1e15-388">刪除指定的字元。</span><span class="sxs-lookup"><span data-stu-id="b1e15-388">Deletes until given character.</span></span>

- <span data-ttu-id="b1e15-389">Vi 命令模式： `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-389">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="b1e15-390">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="b1e15-390">ViReplaceToCharBackward</span></span>

<span data-ttu-id="b1e15-391">取代指定的字元。</span><span class="sxs-lookup"><span data-stu-id="b1e15-391">Replaces until given character.</span></span>

- <span data-ttu-id="b1e15-392">Vi 命令模式： `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-392">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="b1e15-393">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="b1e15-393">ViYankBeginningOfLine</span></span>

<span data-ttu-id="b1e15-394">從緩衝區開頭 Yank 至資料指標。</span><span class="sxs-lookup"><span data-stu-id="b1e15-394">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="b1e15-395">Vi 命令模式： `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-395">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="b1e15-396">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="b1e15-396">ViYankEndOfGlob</span></span>

<span data-ttu-id="b1e15-397">從資料指標 Yank 至 WORD (s) 的結尾。</span><span class="sxs-lookup"><span data-stu-id="b1e15-397">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="b1e15-398">Vi 命令模式： `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-398">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="b1e15-399">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="b1e15-399">ViYankEndOfWord</span></span>

<span data-ttu-id="b1e15-400">從資料指標 Yank 至 word (s) 的結尾。</span><span class="sxs-lookup"><span data-stu-id="b1e15-400">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="b1e15-401">Vi 命令模式： `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-401">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="b1e15-402">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="b1e15-402">ViYankLeft</span></span>

<span data-ttu-id="b1e15-403">Yank 字元 (s) 到游標的左邊。</span><span class="sxs-lookup"><span data-stu-id="b1e15-403">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="b1e15-404">Vi 命令模式： `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-404">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="b1e15-405">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="b1e15-405">ViYankLine</span></span>

<span data-ttu-id="b1e15-406">Yank 整個緩衝區。</span><span class="sxs-lookup"><span data-stu-id="b1e15-406">Yank the entire buffer.</span></span>

- <span data-ttu-id="b1e15-407">Vi 命令模式： `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-407">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="b1e15-408">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="b1e15-408">ViYankNextGlob</span></span>

<span data-ttu-id="b1e15-409">從資料指標 Yank 至下一個單字的開頭 (s) 。</span><span class="sxs-lookup"><span data-stu-id="b1e15-409">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="b1e15-410">Vi 命令模式： `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-410">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="b1e15-411">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="b1e15-411">ViYankNextWord</span></span>

<span data-ttu-id="b1e15-412">Yank) 在游標之後 (s 的單字。</span><span class="sxs-lookup"><span data-stu-id="b1e15-412">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="b1e15-413">Vi 命令模式： `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-413">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="b1e15-414">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="b1e15-414">ViYankPercent</span></span>

<span data-ttu-id="b1e15-415">Yank 至/從相符的括弧。</span><span class="sxs-lookup"><span data-stu-id="b1e15-415">Yank to/from matching brace.</span></span>

- <span data-ttu-id="b1e15-416">Vi 命令模式： `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-416">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="b1e15-417">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="b1e15-417">ViYankPreviousGlob</span></span>

<span data-ttu-id="b1e15-418">從字組開頭 (s 的 Yank) 到資料指標。</span><span class="sxs-lookup"><span data-stu-id="b1e15-418">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="b1e15-419">Vi 命令模式： `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-419">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="b1e15-420">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="b1e15-420">ViYankPreviousWord</span></span>

<span data-ttu-id="b1e15-421">Yank) 在游標之前的文字 (s。</span><span class="sxs-lookup"><span data-stu-id="b1e15-421">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="b1e15-422">Vi 命令模式： `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-422">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="b1e15-423">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="b1e15-423">ViYankRight</span></span>

<span data-ttu-id="b1e15-424">Yank 字元 (s) 在游標右邊和右邊。</span><span class="sxs-lookup"><span data-stu-id="b1e15-424">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="b1e15-425">Vi 命令模式： `<y,l>` 、 `<y,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-425">Vi command mode: `<y,l>`, `<y,Spacebar>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="b1e15-426">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="b1e15-426">ViYankToEndOfLine</span></span>

<span data-ttu-id="b1e15-427">從資料指標 Yank 至緩衝區的結尾。</span><span class="sxs-lookup"><span data-stu-id="b1e15-427">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="b1e15-428">Vi 命令模式： `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-428">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="b1e15-429">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="b1e15-429">ViYankToFirstChar</span></span>

<span data-ttu-id="b1e15-430">從第一個非空白字元 Yank 至游標。</span><span class="sxs-lookup"><span data-stu-id="b1e15-430">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="b1e15-431">Vi 命令模式： `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-431">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="b1e15-432">美國 佬</span><span class="sxs-lookup"><span data-stu-id="b1e15-432">Yank</span></span>

<span data-ttu-id="b1e15-433">將最近終止的文字加入至輸入。</span><span class="sxs-lookup"><span data-stu-id="b1e15-433">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="b1e15-434">Emacs： `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-434">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="b1e15-435">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="b1e15-435">YankLastArg</span></span>

<span data-ttu-id="b1e15-436">Yank 前一個歷程記錄行中的最後一個引數。</span><span class="sxs-lookup"><span data-stu-id="b1e15-436">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="b1e15-437">使用引數時，第一次叫用時，其行為就像 YankNthArg 一樣。</span><span class="sxs-lookup"><span data-stu-id="b1e15-437">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="b1e15-438">如果叫用多次，則改為逐一查看歷程記錄和 arg，將方向 (負反轉方向。 ) </span><span class="sxs-lookup"><span data-stu-id="b1e15-438">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="b1e15-439">Cmd： `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-439">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="b1e15-440">Emacs： `<Alt+.>` 、 `<Alt+_>` 、 `<Escape,.>` 、 `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-440">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="b1e15-441">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="b1e15-441">YankNthArg</span></span>

<span data-ttu-id="b1e15-442">從上一個歷程記錄行中 Yank 命令) 之後，第一個引數 (。</span><span class="sxs-lookup"><span data-stu-id="b1e15-442">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="b1e15-443">使用引數時，請 yank 第 n 個引數 (從 0) 開始，如果引數為負數，則從最後一個引數開始。</span><span class="sxs-lookup"><span data-stu-id="b1e15-443">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="b1e15-444">Emacs： `<Ctrl+Alt+y>` ， `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-444">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="b1e15-445">YankPop</span><span class="sxs-lookup"><span data-stu-id="b1e15-445">YankPop</span></span>

<span data-ttu-id="b1e15-446">如果先前的作業是 Yank 或 YankPop，請將先前 yanked 的文字取代為終止環形中的下一個已取消文字。</span><span class="sxs-lookup"><span data-stu-id="b1e15-446">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="b1e15-447">Emacs： `<Alt+y>` ， `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-447">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="b1e15-448">資料指標移動函數</span><span class="sxs-lookup"><span data-stu-id="b1e15-448">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="b1e15-449">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="b1e15-449">BackwardChar</span></span>

<span data-ttu-id="b1e15-450">將游標向左移動一個字元。</span><span class="sxs-lookup"><span data-stu-id="b1e15-450">Move the cursor one character to the left.</span></span> <span data-ttu-id="b1e15-451">這可能會將游標移至多行輸入的上一行。</span><span class="sxs-lookup"><span data-stu-id="b1e15-451">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="b1e15-452">Cmd： `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-452">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="b1e15-453">Emacs： `<LeftArrow>` ， `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-453">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="b1e15-454">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="b1e15-454">BackwardWord</span></span>

<span data-ttu-id="b1e15-455">將游標移回目前單字的開頭，或將游標移回上一個單字開頭的單字。</span><span class="sxs-lookup"><span data-stu-id="b1e15-455">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="b1e15-456">單字界限是由一組可設定的字元所定義。</span><span class="sxs-lookup"><span data-stu-id="b1e15-456">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="b1e15-457">Cmd： `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-457">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="b1e15-458">Emacs： `<Alt+b>` ， `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-458">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="b1e15-459">Vi 插入模式： `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-459">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="b1e15-460">Vi 命令模式： `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-460">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="b1e15-461">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="b1e15-461">BeginningOfLine</span></span>

<span data-ttu-id="b1e15-462">如果輸入有多行，請移至目前行的開頭，如果已經在行首，則移至輸入的開頭。</span><span class="sxs-lookup"><span data-stu-id="b1e15-462">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="b1e15-463">如果輸入具有單一行，請移至輸入的開頭。</span><span class="sxs-lookup"><span data-stu-id="b1e15-463">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="b1e15-464">Cmd： `<Home>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-464">Cmd: `<Home>`</span></span>
- <span data-ttu-id="b1e15-465">Emacs： `<Home>` ， `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-465">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="b1e15-466">Vi 插入模式： `<Home>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-466">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="b1e15-467">Vi 命令模式： `<Home>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-467">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="b1e15-468">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="b1e15-468">EndOfLine</span></span>

<span data-ttu-id="b1e15-469">如果輸入有多行，請移至目前行的結尾，如果已經在行尾，則移至輸入的結尾。</span><span class="sxs-lookup"><span data-stu-id="b1e15-469">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="b1e15-470">如果輸入具有單一行，請移至輸入的結尾。</span><span class="sxs-lookup"><span data-stu-id="b1e15-470">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="b1e15-471">Cmd： `<End>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-471">Cmd: `<End>`</span></span>
- <span data-ttu-id="b1e15-472">Emacs： `<End>` ， `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-472">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="b1e15-473">Vi 插入模式： `<End>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-473">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="b1e15-474">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="b1e15-474">ForwardChar</span></span>

<span data-ttu-id="b1e15-475">將游標向右移動一個字元。</span><span class="sxs-lookup"><span data-stu-id="b1e15-475">Move the cursor one character to the right.</span></span> <span data-ttu-id="b1e15-476">這可能會將游標移至下一行的多行輸入。</span><span class="sxs-lookup"><span data-stu-id="b1e15-476">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="b1e15-477">Cmd： `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-477">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="b1e15-478">Emacs： `<RightArrow>` ， `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-478">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="b1e15-479">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="b1e15-479">ForwardWord</span></span>

<span data-ttu-id="b1e15-480">將游標向前移動至目前單字的結尾，或在文字之間移動到下一個單字的結尾。</span><span class="sxs-lookup"><span data-stu-id="b1e15-480">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="b1e15-481">單字界限是由一組可設定的字元所定義。</span><span class="sxs-lookup"><span data-stu-id="b1e15-481">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="b1e15-482">Emacs： `<Alt+f>` ， `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-482">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="b1e15-483">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="b1e15-483">GotoBrace</span></span>

<span data-ttu-id="b1e15-484">移至相符的大括弧、括弧或方括弧。</span><span class="sxs-lookup"><span data-stu-id="b1e15-484">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="b1e15-485">Cmd： `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-485">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="b1e15-486">Vi 插入模式： `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-486">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="b1e15-487">Vi 命令模式： `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-487">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="b1e15-488">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="b1e15-488">GotoColumn</span></span>

<span data-ttu-id="b1e15-489">移至 arg 所表示的資料行。</span><span class="sxs-lookup"><span data-stu-id="b1e15-489">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="b1e15-490">Vi 命令模式： `<|>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-490">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="b1e15-491">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="b1e15-491">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="b1e15-492">將游標移至行中的第一個非空白字元。</span><span class="sxs-lookup"><span data-stu-id="b1e15-492">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="b1e15-493">Vi 命令模式： `<^>` 、 `<_>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-493">Vi command mode: `<^>`, `<_>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="b1e15-494">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="b1e15-494">MoveToEndOfLine</span></span>

<span data-ttu-id="b1e15-495">將游標移至輸入的結尾。</span><span class="sxs-lookup"><span data-stu-id="b1e15-495">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="b1e15-496">Vi 命令模式： `<End>` 、 `<$>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-496">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="b1e15-497">NextLine</span><span class="sxs-lookup"><span data-stu-id="b1e15-497">NextLine</span></span>

<span data-ttu-id="b1e15-498">將游標移至下一行。</span><span class="sxs-lookup"><span data-stu-id="b1e15-498">Move the cursor to the next line.</span></span>

- <span data-ttu-id="b1e15-499">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="b1e15-499">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="b1e15-500">NextWord</span><span class="sxs-lookup"><span data-stu-id="b1e15-500">NextWord</span></span>

<span data-ttu-id="b1e15-501">將游標向前移至下一個單字的開頭。</span><span class="sxs-lookup"><span data-stu-id="b1e15-501">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="b1e15-502">單字界限是由一組可設定的字元所定義。</span><span class="sxs-lookup"><span data-stu-id="b1e15-502">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="b1e15-503">Cmd： `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-503">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="b1e15-504">Vi 插入模式： `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-504">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="b1e15-505">Vi 命令模式： `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-505">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="b1e15-506">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="b1e15-506">NextWordEnd</span></span>

<span data-ttu-id="b1e15-507">將游標向前移動至目前單字的結尾，或在文字之間移動到下一個單字的結尾。</span><span class="sxs-lookup"><span data-stu-id="b1e15-507">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="b1e15-508">單字界限是由一組可設定的字元所定義。</span><span class="sxs-lookup"><span data-stu-id="b1e15-508">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="b1e15-509">Vi 命令模式： `<e>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-509">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="b1e15-510">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="b1e15-510">PreviousLine</span></span>

<span data-ttu-id="b1e15-511">將游標移至上一行。</span><span class="sxs-lookup"><span data-stu-id="b1e15-511">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="b1e15-512">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="b1e15-512">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="b1e15-513">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="b1e15-513">ShellBackwardWord</span></span>

<span data-ttu-id="b1e15-514">將游標移回目前單字的開頭，或將游標移回上一個單字開頭的單字。</span><span class="sxs-lookup"><span data-stu-id="b1e15-514">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="b1e15-515">單字界限是由 PowerShell 權杖所定義。</span><span class="sxs-lookup"><span data-stu-id="b1e15-515">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="b1e15-516">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="b1e15-516">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="b1e15-517">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="b1e15-517">ShellForwardWord</span></span>

<span data-ttu-id="b1e15-518">將游標向前移至下一個單字的開頭。</span><span class="sxs-lookup"><span data-stu-id="b1e15-518">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="b1e15-519">單字界限是由 PowerShell 權杖所定義。</span><span class="sxs-lookup"><span data-stu-id="b1e15-519">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="b1e15-520">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="b1e15-520">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="b1e15-521">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="b1e15-521">ShellNextWord</span></span>

<span data-ttu-id="b1e15-522">將游標向前移動至目前單字的結尾，或在文字之間移動到下一個單字的結尾。</span><span class="sxs-lookup"><span data-stu-id="b1e15-522">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="b1e15-523">單字界限是由 PowerShell 權杖所定義。</span><span class="sxs-lookup"><span data-stu-id="b1e15-523">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="b1e15-524">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="b1e15-524">Function is unbound.</span></span>

### <a name="vibackwardchar"></a><span data-ttu-id="b1e15-525">ViBackwardChar</span><span class="sxs-lookup"><span data-stu-id="b1e15-525">ViBackwardChar</span></span>

<span data-ttu-id="b1e15-526">將游標移至 Vi 編輯模式的左邊一個字元。</span><span class="sxs-lookup"><span data-stu-id="b1e15-526">Move the cursor one character to the left in the Vi edit mode.</span></span> <span data-ttu-id="b1e15-527">這可能會將游標移至多行輸入的上一行。</span><span class="sxs-lookup"><span data-stu-id="b1e15-527">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="b1e15-528">Vi 插入模式： `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-528">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="b1e15-529">Vi 命令模式： `<LeftArrow>` 、 `<Backspace>` 、 `<h>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-529">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="b1e15-530">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="b1e15-530">ViBackwardWord</span></span>

<span data-ttu-id="b1e15-531">將游標移回目前單字的開頭，或將游標移回上一個單字開頭的單字。</span><span class="sxs-lookup"><span data-stu-id="b1e15-531">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="b1e15-532">單字界限是由一組可設定的字元所定義。</span><span class="sxs-lookup"><span data-stu-id="b1e15-532">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="b1e15-533">Vi 命令模式： `<b>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-533">Vi command mode: `<b>`</span></span>

### <a name="viforwardchar"></a><span data-ttu-id="b1e15-534">ViForwardChar</span><span class="sxs-lookup"><span data-stu-id="b1e15-534">ViForwardChar</span></span>

<span data-ttu-id="b1e15-535">將游標移至 Vi 編輯模式的右側一個字元。</span><span class="sxs-lookup"><span data-stu-id="b1e15-535">Move the cursor one character to the right in the Vi edit mode.</span></span> <span data-ttu-id="b1e15-536">這可能會將游標移至下一行的多行輸入。</span><span class="sxs-lookup"><span data-stu-id="b1e15-536">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="b1e15-537">Vi 插入模式： `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-537">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="b1e15-538">Vi 命令模式： `<RightArrow>` 、 `<Spacebar>` 、 `<l>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-538">Vi command mode: `<RightArrow>`, `<Spacebar>`, `<l>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="b1e15-539">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="b1e15-539">ViEndOfGlob</span></span>

<span data-ttu-id="b1e15-540">將游標移至單字的結尾，只使用空白字元做為分隔符號。</span><span class="sxs-lookup"><span data-stu-id="b1e15-540">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="b1e15-541">Vi 命令模式： `<E>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-541">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="b1e15-542">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="b1e15-542">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="b1e15-543">移至上一個單字的結尾，只使用空白字元做為單字分隔符號。</span><span class="sxs-lookup"><span data-stu-id="b1e15-543">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="b1e15-544">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="b1e15-544">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="b1e15-545">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="b1e15-545">ViGotoBrace</span></span>

<span data-ttu-id="b1e15-546">類似于 GotoBrace，但它是以字元為基礎，而不是以權杖為基礎。</span><span class="sxs-lookup"><span data-stu-id="b1e15-546">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="b1e15-547">Vi 命令模式： `<%>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-547">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="b1e15-548">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="b1e15-548">ViNextGlob</span></span>

<span data-ttu-id="b1e15-549">移至下一個單字，只使用空白字元做為單字分隔符號。</span><span class="sxs-lookup"><span data-stu-id="b1e15-549">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="b1e15-550">Vi 命令模式： `<W>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-550">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="b1e15-551">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="b1e15-551">ViNextWord</span></span>

<span data-ttu-id="b1e15-552">將游標向前移至下一個單字的開頭。</span><span class="sxs-lookup"><span data-stu-id="b1e15-552">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="b1e15-553">單字界限是由一組可設定的字元所定義。</span><span class="sxs-lookup"><span data-stu-id="b1e15-553">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="b1e15-554">Vi 命令模式： `<w>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-554">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="b1e15-555">歷程記錄函數</span><span class="sxs-lookup"><span data-stu-id="b1e15-555">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="b1e15-556">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="b1e15-556">BeginningOfHistory</span></span>

<span data-ttu-id="b1e15-557">移至歷程記錄中的第一個專案。</span><span class="sxs-lookup"><span data-stu-id="b1e15-557">Move to the first item in the history.</span></span>

- <span data-ttu-id="b1e15-558">Emacs： `<Alt+<>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-558">Emacs: `<Alt+<>`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="b1e15-559">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="b1e15-559">ClearHistory</span></span>

<span data-ttu-id="b1e15-560">清除 PSReadLine 中的歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="b1e15-560">Clears history in PSReadLine.</span></span> <span data-ttu-id="b1e15-561">這不會影響 PowerShell 歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="b1e15-561">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="b1e15-562">Cmd： `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-562">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="b1e15-563">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="b1e15-563">EndOfHistory</span></span>

<span data-ttu-id="b1e15-564">移至記錄中目前輸入)  (的最後一個專案。</span><span class="sxs-lookup"><span data-stu-id="b1e15-564">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="b1e15-565">Emacs： `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-565">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="b1e15-566">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="b1e15-566">ForwardSearchHistory</span></span>

<span data-ttu-id="b1e15-567">透過歷程記錄執行漸進式向前搜尋。</span><span class="sxs-lookup"><span data-stu-id="b1e15-567">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="b1e15-568">Cmd： `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-568">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="b1e15-569">Emacs： `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-569">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="b1e15-570">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="b1e15-570">HistorySearchBackward</span></span>

<span data-ttu-id="b1e15-571">將目前的輸入取代為 PSReadLine 記錄中與開始和輸入和資料指標之間的字元相符的 ' previous ' 專案。</span><span class="sxs-lookup"><span data-stu-id="b1e15-571">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="b1e15-572">Cmd： `<F8>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-572">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="b1e15-573">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="b1e15-573">HistorySearchForward</span></span>

<span data-ttu-id="b1e15-574">將目前的輸入取代為 PSReadLine 記錄中與開始和輸入和資料指標之間的字元相符的 ' next ' 專案。</span><span class="sxs-lookup"><span data-stu-id="b1e15-574">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="b1e15-575">Cmd： `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-575">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="b1e15-576">NextHistory</span><span class="sxs-lookup"><span data-stu-id="b1e15-576">NextHistory</span></span>

<span data-ttu-id="b1e15-577">將目前的輸入取代為 PSReadLine 記錄中的 ' next ' 專案。</span><span class="sxs-lookup"><span data-stu-id="b1e15-577">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="b1e15-578">Cmd： `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-578">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="b1e15-579">Emacs： `<DownArrow>` ， `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-579">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="b1e15-580">Vi 插入模式： `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-580">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="b1e15-581">Vi 命令模式： `<DownArrow>` 、 `<j>` 、 `<+>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-581">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="b1e15-582">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="b1e15-582">PreviousHistory</span></span>

<span data-ttu-id="b1e15-583">將目前的輸入取代為 PSReadLine 記錄中的 ' previous ' 專案。</span><span class="sxs-lookup"><span data-stu-id="b1e15-583">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="b1e15-584">Cmd： `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-584">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="b1e15-585">Emacs： `<UpArrow>` ， `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-585">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="b1e15-586">Vi 插入模式： `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-586">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="b1e15-587">Vi 命令模式： `<UpArrow>` 、 `<k>` 、 `<->`</span><span class="sxs-lookup"><span data-stu-id="b1e15-587">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="b1e15-588">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="b1e15-588">ReverseSearchHistory</span></span>

<span data-ttu-id="b1e15-589">透過歷程記錄執行增量向前搜尋。</span><span class="sxs-lookup"><span data-stu-id="b1e15-589">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="b1e15-590">Cmd： `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-590">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="b1e15-591">Emacs： `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-591">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="b1e15-592">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="b1e15-592">ViSearchHistoryBackward</span></span>

<span data-ttu-id="b1e15-593">提示輸入搜尋字串，並在 AcceptLine 時起始搜尋。</span><span class="sxs-lookup"><span data-stu-id="b1e15-593">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="b1e15-594">Vi 插入模式： `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-594">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="b1e15-595">Vi 命令模式： `</>` 、 `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-595">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="b1e15-596">完成函式</span><span class="sxs-lookup"><span data-stu-id="b1e15-596">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="b1e15-597">完成</span><span class="sxs-lookup"><span data-stu-id="b1e15-597">Complete</span></span>

<span data-ttu-id="b1e15-598">嘗試對資料指標周圍的文字執行完成。</span><span class="sxs-lookup"><span data-stu-id="b1e15-598">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="b1e15-599">如果有多個可能的完成，則會使用最長的明確前置詞來完成。</span><span class="sxs-lookup"><span data-stu-id="b1e15-599">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="b1e15-600">如果嘗試完成最長的明確完成，則會顯示可能的完成清單。</span><span class="sxs-lookup"><span data-stu-id="b1e15-600">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="b1e15-601">Emacs： `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-601">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="b1e15-602">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="b1e15-602">MenuComplete</span></span>

<span data-ttu-id="b1e15-603">嘗試對資料指標周圍的文字執行完成。</span><span class="sxs-lookup"><span data-stu-id="b1e15-603">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="b1e15-604">如果有多個可能的完成，則會使用最長的明確前置詞來完成。</span><span class="sxs-lookup"><span data-stu-id="b1e15-604">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="b1e15-605">如果嘗試完成最長的明確完成，則會顯示可能的完成清單。</span><span class="sxs-lookup"><span data-stu-id="b1e15-605">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="b1e15-606">Cmd： `<Ctrl+@>` ， `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-606">Cmd: `<Ctrl+@>`, `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="b1e15-607">Emacs： `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-607">Emacs: `<Ctrl+Spacebar>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="b1e15-608">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="b1e15-608">PossibleCompletions</span></span>

<span data-ttu-id="b1e15-609">顯示可能的完成清單。</span><span class="sxs-lookup"><span data-stu-id="b1e15-609">Display the list of possible completions.</span></span>

- <span data-ttu-id="b1e15-610">Emacs： `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-610">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="b1e15-611">Vi 插入模式： `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-611">Vi insert mode: `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="b1e15-612">Vi 命令模式： `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-612">Vi command mode: `<Ctrl+Spacebar>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="b1e15-613">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="b1e15-613">TabCompleteNext</span></span>

<span data-ttu-id="b1e15-614">嘗試使用下一個可用的完成來完成資料指標周圍的文字。</span><span class="sxs-lookup"><span data-stu-id="b1e15-614">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="b1e15-615">Cmd： `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-615">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="b1e15-616">Vi 命令模式： `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-616">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="b1e15-617">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="b1e15-617">TabCompletePrevious</span></span>

<span data-ttu-id="b1e15-618">嘗試使用先前的可用完成來完成資料指標周圍的文字。</span><span class="sxs-lookup"><span data-stu-id="b1e15-618">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="b1e15-619">Cmd： `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-619">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="b1e15-620">Vi 命令模式： `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-620">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="b1e15-621">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="b1e15-621">ViTabCompleteNext</span></span>

<span data-ttu-id="b1e15-622">視需要結束目前的編輯群組，並叫用 TabCompleteNext。</span><span class="sxs-lookup"><span data-stu-id="b1e15-622">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="b1e15-623">Vi 插入模式： `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-623">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="b1e15-624">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="b1e15-624">ViTabCompletePrevious</span></span>

<span data-ttu-id="b1e15-625">視需要結束目前的編輯群組，並叫用 TabCompletePrevious。</span><span class="sxs-lookup"><span data-stu-id="b1e15-625">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="b1e15-626">Vi 插入模式： `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-626">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="b1e15-627">其他函式</span><span class="sxs-lookup"><span data-stu-id="b1e15-627">Miscellaneous functions</span></span>

### <a name="acceptnextsuggestionword"></a><span data-ttu-id="b1e15-628">AcceptNextSuggestionWord</span><span class="sxs-lookup"><span data-stu-id="b1e15-628">AcceptNextSuggestionWord</span></span>

<span data-ttu-id="b1e15-629">接受內嵌或選取建議的下一個字組。</span><span class="sxs-lookup"><span data-stu-id="b1e15-629">Accept the next word of the inline or selected suggestion.</span></span>

- <span data-ttu-id="b1e15-630">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="b1e15-630">Function is unbound.</span></span>

### <a name="acceptsuggestion"></a><span data-ttu-id="b1e15-631">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="b1e15-631">AcceptSuggestion</span></span>

<span data-ttu-id="b1e15-632">接受目前的內嵌或選取的建議。</span><span class="sxs-lookup"><span data-stu-id="b1e15-632">Accept the current inline or selected suggestion.</span></span>

- <span data-ttu-id="b1e15-633">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="b1e15-633">Function is unbound.</span></span>

### <a name="capturescreen"></a><span data-ttu-id="b1e15-634">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="b1e15-634">CaptureScreen</span></span>

<span data-ttu-id="b1e15-635">啟動互動式螢幕擷取畫面-向上/向下箭號選取 [線條]，輸入將選取的文字複製到剪貼簿做為文字和 html。</span><span class="sxs-lookup"><span data-stu-id="b1e15-635">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="b1e15-636">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="b1e15-636">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="b1e15-637">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="b1e15-637">ClearScreen</span></span>

<span data-ttu-id="b1e15-638">清除畫面並在畫面頂端繪製目前的線。</span><span class="sxs-lookup"><span data-stu-id="b1e15-638">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="b1e15-639">Cmd： `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-639">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="b1e15-640">Emacs： `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-640">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="b1e15-641">Vi 插入模式： `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-641">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="b1e15-642">Vi 命令模式： `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-642">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="b1e15-643">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="b1e15-643">DigitArgument</span></span>

<span data-ttu-id="b1e15-644">開始新的數位引數以傳遞至其他函式。</span><span class="sxs-lookup"><span data-stu-id="b1e15-644">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="b1e15-645">Cmd： `<Alt+0>` 、 `<Alt+1>` 、 `<Alt+2>` 、 `<Alt+3>` 、 `<Alt+4>` 、 `<Alt+5>` 、 `<Alt+6>` `<Alt+7>` `<Alt+8>` `<Alt+9>` 、、、、、 `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="b1e15-645">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="b1e15-646">Emacs： `<Alt+0>` 、 `<Alt+1>` 、 `<Alt+2>` 、、、 `<Alt+3>` `<Alt+4>` `<Alt+5>` 、 `<Alt+6>` 、 `<Alt+7>` 、 `<Alt+8>` 、 `<Alt+9>` 、、 `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="b1e15-646">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="b1e15-647">Vi 命令模式： `<0>` 、 `<1>` 、 `<2>` 、 `<3>` 、 `<4>` 、 `<5>` 、 `<6>` `<7>` `<8>` 、、、、 `<9>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-647">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="b1e15-648">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="b1e15-648">InvokePrompt</span></span>

<span data-ttu-id="b1e15-649">清除目前的提示，並呼叫 prompt 函式以重新顯示提示。</span><span class="sxs-lookup"><span data-stu-id="b1e15-649">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="b1e15-650">適用于變更狀態的自訂金鑰處理常式，例如變更目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="b1e15-650">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="b1e15-651">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="b1e15-651">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="b1e15-652">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="b1e15-652">ScrollDisplayDown</span></span>

<span data-ttu-id="b1e15-653">將顯示畫面向下移動一個畫面。</span><span class="sxs-lookup"><span data-stu-id="b1e15-653">Scroll the display down one screen.</span></span>

- <span data-ttu-id="b1e15-654">Cmd： `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-654">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="b1e15-655">Emacs： `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-655">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="b1e15-656">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="b1e15-656">ScrollDisplayDownLine</span></span>

<span data-ttu-id="b1e15-657">將向下移動一行。</span><span class="sxs-lookup"><span data-stu-id="b1e15-657">Scroll the display down one line.</span></span>

- <span data-ttu-id="b1e15-658">Cmd： `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-658">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="b1e15-659">Emacs： `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-659">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="b1e15-660">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="b1e15-660">ScrollDisplayToCursor</span></span>

<span data-ttu-id="b1e15-661">將顯示滾動至游標。</span><span class="sxs-lookup"><span data-stu-id="b1e15-661">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="b1e15-662">Emacs： `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-662">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="b1e15-663">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="b1e15-663">ScrollDisplayTop</span></span>

<span data-ttu-id="b1e15-664">將顯示器向上方滾動。</span><span class="sxs-lookup"><span data-stu-id="b1e15-664">Scroll the display to the top.</span></span>

- <span data-ttu-id="b1e15-665">Emacs： `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-665">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="b1e15-666">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="b1e15-666">ScrollDisplayUp</span></span>

<span data-ttu-id="b1e15-667">將顯示畫面向上移動一次。</span><span class="sxs-lookup"><span data-stu-id="b1e15-667">Scroll the display up one screen.</span></span>

- <span data-ttu-id="b1e15-668">Cmd： `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-668">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="b1e15-669">Emacs： `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-669">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="b1e15-670">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="b1e15-670">ScrollDisplayUpLine</span></span>

<span data-ttu-id="b1e15-671">將顯示畫面向下移動一行。</span><span class="sxs-lookup"><span data-stu-id="b1e15-671">Scroll the display up one line.</span></span>

- <span data-ttu-id="b1e15-672">Cmd： `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-672">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="b1e15-673">Emacs： `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-673">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="b1e15-674">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="b1e15-674">SelfInsert</span></span>

<span data-ttu-id="b1e15-675">插入金鑰。</span><span class="sxs-lookup"><span data-stu-id="b1e15-675">Insert the key.</span></span>

- <span data-ttu-id="b1e15-676">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="b1e15-676">Function is unbound.</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="b1e15-677">ShowKeyBindings</span><span class="sxs-lookup"><span data-stu-id="b1e15-677">ShowKeyBindings</span></span>

<span data-ttu-id="b1e15-678">顯示所有系結的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="b1e15-678">Show all bound keys.</span></span>

- <span data-ttu-id="b1e15-679">Cmd： `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-679">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="b1e15-680">Emacs： `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-680">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="b1e15-681">Vi 插入模式： `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-681">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="b1e15-682">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="b1e15-682">ViCommandMode</span></span>

<span data-ttu-id="b1e15-683">將目前的作業模式從 Vi-Insert 切換至 Vi 命令。</span><span class="sxs-lookup"><span data-stu-id="b1e15-683">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="b1e15-684">Vi 插入模式： `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-684">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="b1e15-685">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="b1e15-685">ViDigitArgumentInChord</span></span>

<span data-ttu-id="b1e15-686">開始新的數位引數，以傳遞至其他函式，而非 vi 的 chords 之一。</span><span class="sxs-lookup"><span data-stu-id="b1e15-686">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="b1e15-687">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="b1e15-687">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="b1e15-688">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="b1e15-688">ViEditVisually</span></span>

<span data-ttu-id="b1e15-689">在 [$env：編輯器] 或 [$env：視覺效果] 所指定的文字編輯器中編輯命令行。</span><span class="sxs-lookup"><span data-stu-id="b1e15-689">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="b1e15-690">Emacs： `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-690">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="b1e15-691">Vi 命令模式： `<v>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-691">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="b1e15-692">ViExit</span><span class="sxs-lookup"><span data-stu-id="b1e15-692">ViExit</span></span>

<span data-ttu-id="b1e15-693">離開 shell。</span><span class="sxs-lookup"><span data-stu-id="b1e15-693">Exits the shell.</span></span>

- <span data-ttu-id="b1e15-694">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="b1e15-694">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="b1e15-695">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="b1e15-695">ViInsertMode</span></span>

<span data-ttu-id="b1e15-696">切換至插入模式。</span><span class="sxs-lookup"><span data-stu-id="b1e15-696">Switch to Insert mode.</span></span>

- <span data-ttu-id="b1e15-697">Vi 命令模式： `<i>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-697">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="b1e15-698">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="b1e15-698">WhatIsKey</span></span>

<span data-ttu-id="b1e15-699">讀取金鑰，並告訴我金鑰的系結目標。</span><span class="sxs-lookup"><span data-stu-id="b1e15-699">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="b1e15-700">Cmd： `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-700">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="b1e15-701">Emacs： `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-701">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="b1e15-702">選取函式</span><span class="sxs-lookup"><span data-stu-id="b1e15-702">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="b1e15-703">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="b1e15-703">ExchangePointAndMark</span></span>

<span data-ttu-id="b1e15-704">游標放在標記的位置，而標記會移至游標位置。</span><span class="sxs-lookup"><span data-stu-id="b1e15-704">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="b1e15-705">Emacs： `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-705">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="b1e15-706">SelectAll</span><span class="sxs-lookup"><span data-stu-id="b1e15-706">SelectAll</span></span>

<span data-ttu-id="b1e15-707">選取整行。</span><span class="sxs-lookup"><span data-stu-id="b1e15-707">Select the entire line.</span></span>

- <span data-ttu-id="b1e15-708">Cmd： `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-708">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="b1e15-709">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="b1e15-709">SelectBackwardChar</span></span>

<span data-ttu-id="b1e15-710">調整目前的選取範圍，以包含前一個字元。</span><span class="sxs-lookup"><span data-stu-id="b1e15-710">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="b1e15-711">Cmd： `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-711">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="b1e15-712">Emacs： `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-712">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="b1e15-713">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="b1e15-713">SelectBackwardsLine</span></span>

<span data-ttu-id="b1e15-714">調整目前的選取範圍，以包含從游標到行首的起點。</span><span class="sxs-lookup"><span data-stu-id="b1e15-714">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="b1e15-715">Cmd： `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-715">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="b1e15-716">Emacs： `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-716">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="b1e15-717">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="b1e15-717">SelectBackwardWord</span></span>

<span data-ttu-id="b1e15-718">調整目前的選取範圍，以包含前一個字組。</span><span class="sxs-lookup"><span data-stu-id="b1e15-718">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="b1e15-719">Cmd： `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-719">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="b1e15-720">Emacs： `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-720">Emacs: `<Alt+B>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="b1e15-721">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="b1e15-721">SelectForwardChar</span></span>

<span data-ttu-id="b1e15-722">調整目前的選取範圍，以包含下一個字元。</span><span class="sxs-lookup"><span data-stu-id="b1e15-722">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="b1e15-723">Cmd： `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-723">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="b1e15-724">Emacs： `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-724">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="b1e15-725">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="b1e15-725">SelectForwardWord</span></span>

<span data-ttu-id="b1e15-726">使用 ForwardWord 調整目前的選取範圍，以包含下一個字組。</span><span class="sxs-lookup"><span data-stu-id="b1e15-726">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="b1e15-727">Emacs： `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-727">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="b1e15-728">SelectLine</span><span class="sxs-lookup"><span data-stu-id="b1e15-728">SelectLine</span></span>

<span data-ttu-id="b1e15-729">調整目前的選取範圍，以包含從游標到行尾。</span><span class="sxs-lookup"><span data-stu-id="b1e15-729">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="b1e15-730">Cmd： `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-730">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="b1e15-731">Emacs： `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-731">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="b1e15-732">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="b1e15-732">SelectNextWord</span></span>

<span data-ttu-id="b1e15-733">調整目前的選取範圍，以包含下一個字組。</span><span class="sxs-lookup"><span data-stu-id="b1e15-733">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="b1e15-734">Cmd： `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-734">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="b1e15-735">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="b1e15-735">SelectShellBackwardWord</span></span>

<span data-ttu-id="b1e15-736">使用 ShellBackwardWord 調整目前的選取範圍，以包含前一個字組。</span><span class="sxs-lookup"><span data-stu-id="b1e15-736">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="b1e15-737">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="b1e15-737">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="b1e15-738">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="b1e15-738">SelectShellForwardWord</span></span>

<span data-ttu-id="b1e15-739">使用 ShellForwardWord 調整目前的選取範圍，以包含下一個字組。</span><span class="sxs-lookup"><span data-stu-id="b1e15-739">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="b1e15-740">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="b1e15-740">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="b1e15-741">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="b1e15-741">SelectShellNextWord</span></span>

<span data-ttu-id="b1e15-742">使用 ShellNextWord 調整目前的選取範圍，以包含下一個字組。</span><span class="sxs-lookup"><span data-stu-id="b1e15-742">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="b1e15-743">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="b1e15-743">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="b1e15-744">SetMark</span><span class="sxs-lookup"><span data-stu-id="b1e15-744">SetMark</span></span>

<span data-ttu-id="b1e15-745">標記目前的資料指標位置，以用於後續的編輯命令。</span><span class="sxs-lookup"><span data-stu-id="b1e15-745">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="b1e15-746">Emacs： `<Ctrl+@>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-746">Emacs: `<Ctrl+@>`</span></span>

## <a name="search-functions"></a><span data-ttu-id="b1e15-747">搜尋函數</span><span class="sxs-lookup"><span data-stu-id="b1e15-747">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="b1e15-748">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="b1e15-748">CharacterSearch</span></span>

<span data-ttu-id="b1e15-749">讀取字元，並向前搜尋該字元的下一個出現位置。</span><span class="sxs-lookup"><span data-stu-id="b1e15-749">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="b1e15-750">如果指定了引數，則在第 n 次發生) 時，向前搜尋 (或向後搜尋。</span><span class="sxs-lookup"><span data-stu-id="b1e15-750">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="b1e15-751">Cmd： `<F3>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-751">Cmd: `<F3>`</span></span>
- <span data-ttu-id="b1e15-752">Emacs： `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-752">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="b1e15-753">Vi 插入模式： `<F3>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-753">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="b1e15-754">Vi 命令模式： `<F3>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-754">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="b1e15-755">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="b1e15-755">CharacterSearchBackward</span></span>

<span data-ttu-id="b1e15-756">讀取字元，並向後搜尋該字元的下一個出現位置。</span><span class="sxs-lookup"><span data-stu-id="b1e15-756">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="b1e15-757">如果指定了引數，則會在第 n 次出現) 時向後 (或向前搜尋。</span><span class="sxs-lookup"><span data-stu-id="b1e15-757">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="b1e15-758">Cmd： `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-758">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="b1e15-759">Emacs： `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-759">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="b1e15-760">Vi 插入模式： `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-760">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="b1e15-761">Vi 命令模式： `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-761">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="b1e15-762">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="b1e15-762">RepeatLastCharSearch</span></span>

<span data-ttu-id="b1e15-763">重複上次錄製的字元搜尋。</span><span class="sxs-lookup"><span data-stu-id="b1e15-763">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="b1e15-764">Vi 命令模式： `<;>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-764">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="b1e15-765">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="b1e15-765">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="b1e15-766">重複上次錄製的字元搜尋，但方向相反。</span><span class="sxs-lookup"><span data-stu-id="b1e15-766">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="b1e15-767">Vi 命令模式： `<,>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-767">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="b1e15-768">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="b1e15-768">RepeatSearch</span></span>

<span data-ttu-id="b1e15-769">以與之前相同的方向重複最後一個搜尋。</span><span class="sxs-lookup"><span data-stu-id="b1e15-769">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="b1e15-770">Vi 命令模式： `<n>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-770">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="b1e15-771">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="b1e15-771">RepeatSearchBackward</span></span>

<span data-ttu-id="b1e15-772">以與之前相同的方向重複最後一個搜尋。</span><span class="sxs-lookup"><span data-stu-id="b1e15-772">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="b1e15-773">Vi 命令模式： `<N>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-773">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="b1e15-774">SearchChar</span><span class="sxs-lookup"><span data-stu-id="b1e15-774">SearchChar</span></span>

<span data-ttu-id="b1e15-775">讀取下一個字元，然後找出該字元，再繼續進行，然後再移出一個字元。</span><span class="sxs-lookup"><span data-stu-id="b1e15-775">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="b1e15-776">這是「t」功能。</span><span class="sxs-lookup"><span data-stu-id="b1e15-776">This is for 't' functionality.</span></span>

- <span data-ttu-id="b1e15-777">Vi 命令模式： `<f>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-777">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="b1e15-778">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="b1e15-778">SearchCharBackward</span></span>

<span data-ttu-id="b1e15-779">讀取下一個字元，然後找出它，然後再向後移一字元。</span><span class="sxs-lookup"><span data-stu-id="b1e15-779">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="b1e15-780">這是「t」功能。</span><span class="sxs-lookup"><span data-stu-id="b1e15-780">This is for 'T' functionality.</span></span>

- <span data-ttu-id="b1e15-781">Vi 命令模式： `<F>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-781">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="b1e15-782">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="b1e15-782">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="b1e15-783">讀取下一個字元，然後找出它，然後再向後移一字元。</span><span class="sxs-lookup"><span data-stu-id="b1e15-783">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="b1e15-784">這是「t」功能。</span><span class="sxs-lookup"><span data-stu-id="b1e15-784">This is for 'T' functionality.</span></span>

- <span data-ttu-id="b1e15-785">Vi 命令模式： `<T>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-785">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="b1e15-786">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="b1e15-786">SearchCharWithBackoff</span></span>

<span data-ttu-id="b1e15-787">讀取下一個字元，然後找出該字元，再繼續進行，然後再移出一個字元。</span><span class="sxs-lookup"><span data-stu-id="b1e15-787">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="b1e15-788">這是「t」功能。</span><span class="sxs-lookup"><span data-stu-id="b1e15-788">This is for 't' functionality.</span></span>

- <span data-ttu-id="b1e15-789">Vi 命令模式： `<t>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-789">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="b1e15-790">SearchForward</span><span class="sxs-lookup"><span data-stu-id="b1e15-790">SearchForward</span></span>

<span data-ttu-id="b1e15-791">提示輸入搜尋字串，並在 AcceptLine 時起始搜尋。</span><span class="sxs-lookup"><span data-stu-id="b1e15-791">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="b1e15-792">Vi 插入模式： `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-792">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="b1e15-793">Vi 命令模式： `<?>` 、 `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="b1e15-793">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="b1e15-794">自訂索引鍵系結</span><span class="sxs-lookup"><span data-stu-id="b1e15-794">Custom Key Bindings</span></span>

<span data-ttu-id="b1e15-795">PSReadLine 支援使用 Cmdlet 的自訂金鑰系結 `Set-PSReadLineKeyHandler` 。</span><span class="sxs-lookup"><span data-stu-id="b1e15-795">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="b1e15-796">大部分的自訂按鍵系結都會呼叫上述其中一項功能，例如</span><span class="sxs-lookup"><span data-stu-id="b1e15-796">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="b1e15-797">您可以將 ScriptBlock 系結至索引鍵。</span><span class="sxs-lookup"><span data-stu-id="b1e15-797">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="b1e15-798">ScriptBlock 可以進行任何您想要的動作。</span><span class="sxs-lookup"><span data-stu-id="b1e15-798">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="b1e15-799">一些實用的範例包括</span><span class="sxs-lookup"><span data-stu-id="b1e15-799">Some useful examples include</span></span>

- <span data-ttu-id="b1e15-800">編輯命令行</span><span class="sxs-lookup"><span data-stu-id="b1e15-800">edit the command line</span></span>
- <span data-ttu-id="b1e15-801">開啟新視窗 (例如說明) </span><span class="sxs-lookup"><span data-stu-id="b1e15-801">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="b1e15-802">變更目錄而不變更命令列</span><span class="sxs-lookup"><span data-stu-id="b1e15-802">change directories without changing the command line</span></span>

<span data-ttu-id="b1e15-803">ScriptBlock 會收到兩個引數：</span><span class="sxs-lookup"><span data-stu-id="b1e15-803">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="b1e15-804">`$key` -A **[ConsoleKeyInfo]** 物件，它是觸發自訂系結的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="b1e15-804">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="b1e15-805">如果您將相同的 ScriptBlock 系結至多個金鑰，且需要根據金鑰執行不同的動作，您可以檢查 $key。</span><span class="sxs-lookup"><span data-stu-id="b1e15-805">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="b1e15-806">許多自訂系結會忽略此引數。</span><span class="sxs-lookup"><span data-stu-id="b1e15-806">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="b1e15-807">`$arg` -任意引數。</span><span class="sxs-lookup"><span data-stu-id="b1e15-807">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="b1e15-808">通常，這會是使用者從索引鍵系結 DigitArgument 傳遞的整數引數。</span><span class="sxs-lookup"><span data-stu-id="b1e15-808">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="b1e15-809">如果您的系結不接受引數，則可以合理地忽略此引數。</span><span class="sxs-lookup"><span data-stu-id="b1e15-809">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="b1e15-810">讓我們看看將命令列新增至歷程記錄，而不執行的範例。</span><span class="sxs-lookup"><span data-stu-id="b1e15-810">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="b1e15-811">當您知道您忘了進行某個動作，但不想重新輸入您已經輸入的命令列時，這會很有用。</span><span class="sxs-lookup"><span data-stu-id="b1e15-811">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

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

<span data-ttu-id="b1e15-812">您可以在檔案中看到許多在 `SamplePSReadLineProfile.ps1` PSReadLine 模組資料夾中安裝的範例。</span><span class="sxs-lookup"><span data-stu-id="b1e15-812">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="b1e15-813">大部分的按鍵系結都會使用一些 helper 函數來編輯命令行。</span><span class="sxs-lookup"><span data-stu-id="b1e15-813">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="b1e15-814">這些 Api 記載于下一節。</span><span class="sxs-lookup"><span data-stu-id="b1e15-814">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="b1e15-815">自訂金鑰系結支援 Api</span><span class="sxs-lookup"><span data-stu-id="b1e15-815">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="b1e15-816">下列函式在 PSConsoleReadLine 中是公用的，但不能直接系結至索引鍵。</span><span class="sxs-lookup"><span data-stu-id="b1e15-816">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="b1e15-817">大部分在自訂金鑰系結中都很有用。</span><span class="sxs-lookup"><span data-stu-id="b1e15-817">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="b1e15-818">將命令列新增至歷程記錄，而不加以執行。</span><span class="sxs-lookup"><span data-stu-id="b1e15-818">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="b1e15-819">清除終止環形。</span><span class="sxs-lookup"><span data-stu-id="b1e15-819">Clear the kill-ring.</span></span>  <span data-ttu-id="b1e15-820">這大多用於測試。</span><span class="sxs-lookup"><span data-stu-id="b1e15-820">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="b1e15-821">從開始刪除長度字元。</span><span class="sxs-lookup"><span data-stu-id="b1e15-821">Delete length characters from start.</span></span>  <span data-ttu-id="b1e15-822">這種作業支援復原/重做。</span><span class="sxs-lookup"><span data-stu-id="b1e15-822">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="b1e15-823">根據使用者喜好設定來執行 Ding 動作。</span><span class="sxs-lookup"><span data-stu-id="b1e15-823">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="b1e15-824">這兩個函式會取出輸入緩衝區目前狀態的相關實用資訊。</span><span class="sxs-lookup"><span data-stu-id="b1e15-824">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="b1e15-825">第一個較常用於簡單的案例。</span><span class="sxs-lookup"><span data-stu-id="b1e15-825">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="b1e15-826">如果您的系結使用 Ast 更先進地執行，則會使用第二個。</span><span class="sxs-lookup"><span data-stu-id="b1e15-826">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(string[] Chord)
```

<span data-ttu-id="b1e15-827">這兩個函數是由所使用 `Get-PSReadLineKeyHandler` 。</span><span class="sxs-lookup"><span data-stu-id="b1e15-827">These two functions are used by `Get-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="b1e15-828">第一個用來取得所有按鍵系結。</span><span class="sxs-lookup"><span data-stu-id="b1e15-828">The first is used to get all key bindings.</span></span> <span data-ttu-id="b1e15-829">第二個是用來取得特定的索引鍵系結。</span><span class="sxs-lookup"><span data-stu-id="b1e15-829">The second is used to get specific key bindings.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="b1e15-830">Get-PSReadLineOption 使用這個函式，而且在自訂索引鍵系結中可能不太實用。</span><span class="sxs-lookup"><span data-stu-id="b1e15-830">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="b1e15-831">如果未在命令列上選取任何專案，則會以開始和長度傳回-1。</span><span class="sxs-lookup"><span data-stu-id="b1e15-831">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="b1e15-832">如果在命令列上有選取專案，則會傳回選取範圍的開始和長度。</span><span class="sxs-lookup"><span data-stu-id="b1e15-832">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="b1e15-833">在游標處插入字元或字串。</span><span class="sxs-lookup"><span data-stu-id="b1e15-833">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="b1e15-834">這種作業支援復原/重做。</span><span class="sxs-lookup"><span data-stu-id="b1e15-834">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="b1e15-835">這是要 PSReadLine 的主要進入點。</span><span class="sxs-lookup"><span data-stu-id="b1e15-835">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="b1e15-836">它不支援遞迴，因此在自訂索引鍵系結中並不有用。</span><span class="sxs-lookup"><span data-stu-id="b1e15-836">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="b1e15-837">Remove-PSReadLineKeyHandler 使用這個函式，而且在自訂索引鍵系結中可能不太實用。</span><span class="sxs-lookup"><span data-stu-id="b1e15-837">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="b1e15-838">取代部分輸入。</span><span class="sxs-lookup"><span data-stu-id="b1e15-838">Replace some of the input.</span></span> <span data-ttu-id="b1e15-839">這種作業支援復原/重做。</span><span class="sxs-lookup"><span data-stu-id="b1e15-839">This operation supports undo/redo.</span></span> <span data-ttu-id="b1e15-840">這是優先于 Delete，後面接著 Insert，因為它會被視為復原的單一動作。</span><span class="sxs-lookup"><span data-stu-id="b1e15-840">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="b1e15-841">將游標移至指定的位移。</span><span class="sxs-lookup"><span data-stu-id="b1e15-841">Move the cursor to the given offset.</span></span> <span data-ttu-id="b1e15-842">不追蹤資料指標移動以進行復原。</span><span class="sxs-lookup"><span data-stu-id="b1e15-842">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="b1e15-843">此函式是 Cmdlet PSReadLineOption 所使用的 helper 方法，但對於想要暫時變更設定的自訂按鍵系結來說可能很有用。</span><span class="sxs-lookup"><span data-stu-id="b1e15-843">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="b1e15-844">此 helper 方法是用於接受 DigitArgument 的自訂系結。</span><span class="sxs-lookup"><span data-stu-id="b1e15-844">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="b1e15-845">一般呼叫看起來像</span><span class="sxs-lookup"><span data-stu-id="b1e15-845">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="note"></a><span data-ttu-id="b1e15-846">注意</span><span class="sxs-lookup"><span data-stu-id="b1e15-846">NOTE</span></span>

### <a name="powershell-compatibility"></a><span data-ttu-id="b1e15-847">POWERSHELL 相容性</span><span class="sxs-lookup"><span data-stu-id="b1e15-847">POWERSHELL COMPATIBILITY</span></span>

<span data-ttu-id="b1e15-848">PSReadLine 需要 PowerShell 3.0 或更新版本，以及主控台主機。</span><span class="sxs-lookup"><span data-stu-id="b1e15-848">PSReadLine requires PowerShell 3.0, or newer, and the console host.</span></span> <span data-ttu-id="b1e15-849">它無法在 PowerShell ISE 中運作。</span><span class="sxs-lookup"><span data-stu-id="b1e15-849">It does not work in PowerShell ISE.</span></span> <span data-ttu-id="b1e15-850">它會在 Visual Studio Code 的主控台中運作。</span><span class="sxs-lookup"><span data-stu-id="b1e15-850">It does work in the console of Visual Studio Code.</span></span>

### <a name="command-history"></a><span data-ttu-id="b1e15-851">命令歷程記錄</span><span class="sxs-lookup"><span data-stu-id="b1e15-851">COMMAND HISTORY</span></span>

<span data-ttu-id="b1e15-852">PSReadLine 會維護一個記錄檔，其中包含您從命令列輸入的所有命令和資料。</span><span class="sxs-lookup"><span data-stu-id="b1e15-852">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="b1e15-853">這可能包含機密資料，包括密碼。</span><span class="sxs-lookup"><span data-stu-id="b1e15-853">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="b1e15-854">例如，如果您使用指令 `ConvertTo-SecureString` 程式，密碼就會以純文字的形式記錄在記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="b1e15-854">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="b1e15-855">記錄檔是名為的檔案 `$($host.Name)_history.txt` 。</span><span class="sxs-lookup"><span data-stu-id="b1e15-855">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="b1e15-856">在 Windows 系統上，歷程記錄檔案會儲存在中 `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` 。</span><span class="sxs-lookup"><span data-stu-id="b1e15-856">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span> <span data-ttu-id="b1e15-857">在非 Windows 系統上，記錄檔會儲存在 `$env:XDG_DATA_HOME/powershell/PSReadLine` 或 `$env:HOME/.local/share/powershell/PSReadLine` 。</span><span class="sxs-lookup"><span data-stu-id="b1e15-857">On non-Windows systems, the history files is stored at `$env:XDG_DATA_HOME/powershell/PSReadLine` or `$env:HOME/.local/share/powershell/PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="b1e15-858">意見反應 & 參與 PSReadLine</span><span class="sxs-lookup"><span data-stu-id="b1e15-858">FEEDBACK & CONTRIBUTING TO PSReadLine</span></span>

[<span data-ttu-id="b1e15-859">GitHub 上的 PSReadLine</span><span class="sxs-lookup"><span data-stu-id="b1e15-859">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="b1e15-860">您可以隨時提交提取要求或在 GitHub 頁面上提交意見反應。</span><span class="sxs-lookup"><span data-stu-id="b1e15-860">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="b1e15-861">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1e15-861">SEE ALSO</span></span>

<span data-ttu-id="b1e15-862">PSReadLine 會受到 GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) 程式庫的高度影響。</span><span class="sxs-lookup"><span data-stu-id="b1e15-862">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>

