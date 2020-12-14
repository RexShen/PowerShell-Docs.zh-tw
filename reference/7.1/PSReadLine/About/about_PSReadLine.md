---
description: PSReadLine 在 PowerShell 主控台中提供改良的命令列編輯體驗。
keywords: powershell
Locale: en-US
ms.date: 11/16/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 關於 PSReadLine
ms.openlocfilehash: 6d52bb04118914a9ccca5d3442a9d1915c1c2818
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94692270"
---
# <a name="psreadline"></a><span data-ttu-id="83915-104">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="83915-104">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="83915-105">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="83915-105">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="83915-106">簡短描述</span><span class="sxs-lookup"><span data-stu-id="83915-106">Short Description</span></span>

<span data-ttu-id="83915-107">PSReadLine 在 PowerShell 主控台中提供改良的命令列編輯體驗。</span><span class="sxs-lookup"><span data-stu-id="83915-107">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="83915-108">完整描述</span><span class="sxs-lookup"><span data-stu-id="83915-108">Long Description</span></span>

<span data-ttu-id="83915-109">PSReadLine 2.1 為 PowerShell 主控台提供功能強大的命令列編輯體驗。</span><span class="sxs-lookup"><span data-stu-id="83915-109">PSReadLine 2.1 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="83915-110">它提供：</span><span class="sxs-lookup"><span data-stu-id="83915-110">It provides:</span></span>

- <span data-ttu-id="83915-111">命令列的語法著色</span><span class="sxs-lookup"><span data-stu-id="83915-111">Syntax coloring of the command line</span></span>
- <span data-ttu-id="83915-112">語法錯誤的視覺指示</span><span class="sxs-lookup"><span data-stu-id="83915-112">A visual indication of syntax errors</span></span>
- <span data-ttu-id="83915-113"> (編輯和歷程記錄的更佳多行體驗) </span><span class="sxs-lookup"><span data-stu-id="83915-113">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="83915-114">可自訂的按鍵系結</span><span class="sxs-lookup"><span data-stu-id="83915-114">Customizable key bindings</span></span>
- <span data-ttu-id="83915-115">Cmd 和 Emacs 模式</span><span class="sxs-lookup"><span data-stu-id="83915-115">Cmd and Emacs modes</span></span>
- <span data-ttu-id="83915-116">許多設定選項</span><span class="sxs-lookup"><span data-stu-id="83915-116">Many configuration options</span></span>
- <span data-ttu-id="83915-117">Bash 樣式完成 (在 Cmd 模式中為選擇性，預設為 Emacs 模式) </span><span class="sxs-lookup"><span data-stu-id="83915-117">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="83915-118">Emacs yank/kill-環形</span><span class="sxs-lookup"><span data-stu-id="83915-118">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="83915-119">以 PowerShell 權杖為基礎的「單字」移動和終止</span><span class="sxs-lookup"><span data-stu-id="83915-119">PowerShell token based "word" movement and kill</span></span>
- <span data-ttu-id="83915-120">預測性 IntelliSense</span><span class="sxs-lookup"><span data-stu-id="83915-120">Predictive IntelliSense</span></span>

<span data-ttu-id="83915-121">PSReadLine 需要 PowerShell 3.0 或更新版本，以及主控台主機。</span><span class="sxs-lookup"><span data-stu-id="83915-121">PSReadLine requires PowerShell 3.0, or newer, and the console host.</span></span> <span data-ttu-id="83915-122">它無法在 PowerShell ISE 中運作。</span><span class="sxs-lookup"><span data-stu-id="83915-122">It does not work in PowerShell ISE.</span></span> <span data-ttu-id="83915-123">它會在 Visual Studio Code 的主控台中運作。</span><span class="sxs-lookup"><span data-stu-id="83915-123">It does work in the console of Visual Studio Code.</span></span>

<span data-ttu-id="83915-124">PSReadLine 2.1.0 隨附于 PowerShell 7.1，並支援所有支援的 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="83915-124">PSReadLine 2.1.0 ships with PowerShell 7.1 and is supported in all supported versions of PowerShell.</span></span> <span data-ttu-id="83915-125">您可以從 PowerShell 資源庫安裝。</span><span class="sxs-lookup"><span data-stu-id="83915-125">It is available to install from the PowerShell Gallery.</span></span>
<span data-ttu-id="83915-126">若要在支援的 PowerShell 版本中安裝 PSReadLine 2.1.0，請執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="83915-126">To install PSReadLine 2.1.0 in a supported version of PowerShell run the following command.</span></span>

```powershell
Install-Module -Name PSReadLine -RequiredVersion 2.1.0
```

> [!NOTE]
> <span data-ttu-id="83915-127">從 PowerShell 7.0 開始，如果偵測到螢幕讀取程式，PowerShell 會略過在 Windows 上自動載入 PSReadLine。</span><span class="sxs-lookup"><span data-stu-id="83915-127">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="83915-128">PSReadLine 目前無法與螢幕讀取器順利搭配運作。</span><span class="sxs-lookup"><span data-stu-id="83915-128">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="83915-129">Windows 上 PowerShell 7.0 的預設轉譯和格式可正常運作。</span><span class="sxs-lookup"><span data-stu-id="83915-129">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="83915-130">如有必要，您可以手動載入模組。</span><span class="sxs-lookup"><span data-stu-id="83915-130">You can manually load the module if necessary.</span></span>

## <a name="predictive-intellisense"></a><span data-ttu-id="83915-131">預測性 IntelliSense</span><span class="sxs-lookup"><span data-stu-id="83915-131">Predictive IntelliSense</span></span>

<span data-ttu-id="83915-132">預測性 IntelliSense 是 tab 鍵自動完成概念的補充，可協助使用者成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="83915-132">Predictive IntelliSense is an addition to the concept of tab completion that assists the user in successfully completing commands.</span></span> <span data-ttu-id="83915-133">它可讓使用者根據使用者歷程記錄和其他網域專屬外掛程式的相符預測，來探索、編輯及執行完整的命令。</span><span class="sxs-lookup"><span data-stu-id="83915-133">It enables users to discover, edit, and execute full commands based on matching predictions from the user's history and additional domain specific plugins.</span></span>

### <a name="enable-predictive-intellisense"></a><span data-ttu-id="83915-134">啟用預測性 IntelliSense</span><span class="sxs-lookup"><span data-stu-id="83915-134">Enable Predictive IntelliSense</span></span>

<span data-ttu-id="83915-135">預設會停用預測性 IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="83915-135">Predictive IntelliSense is disabled by default.</span></span> <span data-ttu-id="83915-136">若要啟用預測，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="83915-136">To enable predictions, just run the following command:</span></span>

```powershell
Set-PSReadLineOption -PredictionSource History
```

<span data-ttu-id="83915-137">**PredictionSource** 參數也可以接受適用于網域專屬和自訂需求的外掛程式。</span><span class="sxs-lookup"><span data-stu-id="83915-137">The **PredictionSource** parameter can also accept plugins for domain specific and custom requirements.</span></span>

<span data-ttu-id="83915-138">若要停用預測性 IntelliSense，請直接執行：</span><span class="sxs-lookup"><span data-stu-id="83915-138">To disable Predictive IntelliSense, just run:</span></span>

```powershell
Set-PSReadLineOption -PredictionSource None
```

<span data-ttu-id="83915-139">下列函式可在類別 **[PSConsoleReadLine]** 中使用。</span><span class="sxs-lookup"><span data-stu-id="83915-139">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]**.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="83915-140">基本編輯函數</span><span class="sxs-lookup"><span data-stu-id="83915-140">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="83915-141">中止</span><span class="sxs-lookup"><span data-stu-id="83915-141">Abort</span></span>

<span data-ttu-id="83915-142">中止目前的動作，例如累加式歷程記錄搜尋。</span><span class="sxs-lookup"><span data-stu-id="83915-142">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="83915-143">Emacs： `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="83915-143">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="83915-144">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="83915-144">AcceptAndGetNext</span></span>

<span data-ttu-id="83915-145">嘗試執行目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="83915-145">Attempt to execute the current input.</span></span> <span data-ttu-id="83915-146">如果可以像 AcceptLine) 一樣執行 (，則會在下一次呼叫 ReadLine 時，重新叫用歷程記錄中的下一個專案。</span><span class="sxs-lookup"><span data-stu-id="83915-146">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="83915-147">Emacs： `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="83915-147">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="83915-148">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="83915-148">AcceptLine</span></span>

<span data-ttu-id="83915-149">嘗試執行目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="83915-149">Attempt to execute the current input.</span></span> <span data-ttu-id="83915-150">如果目前的輸入不完整 (例如遺漏右括弧、方括弧或引號，則接續提示會顯示在下一行，而 PSReadLine 會等候按鍵編輯目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="83915-150">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="83915-151">Cmd： `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="83915-151">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="83915-152">Emacs： `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="83915-152">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="83915-153">Vi 插入模式： `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="83915-153">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="83915-154">AddLine</span><span class="sxs-lookup"><span data-stu-id="83915-154">AddLine</span></span>

<span data-ttu-id="83915-155">接續提示會顯示在下一行，而 PSReadLine 會等候按鍵編輯目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="83915-155">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="83915-156">這對於將多行輸入輸入為單一命令很有用，即使單一行本身已完成輸入也是一樣。</span><span class="sxs-lookup"><span data-stu-id="83915-156">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="83915-157">Cmd： `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="83915-157">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="83915-158">Emacs： `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="83915-158">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="83915-159">Vi 插入模式： `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="83915-159">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="83915-160">Vi 命令模式： `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="83915-160">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="83915-161">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="83915-161">BackwardDeleteChar</span></span>

<span data-ttu-id="83915-162">刪除游標之前的字元。</span><span class="sxs-lookup"><span data-stu-id="83915-162">Delete the character before the cursor.</span></span>

- <span data-ttu-id="83915-163">Cmd： `<Backspace>` ， `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="83915-163">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="83915-164">Emacs： `<Backspace>` 、 `<Ctrl+Backspace>` 、 `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="83915-164">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="83915-165">Vi 插入模式： `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="83915-165">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="83915-166">Vi 命令模式： `<X>` 、 `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="83915-166">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="83915-167">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="83915-167">BackwardDeleteLine</span></span>

<span data-ttu-id="83915-168">如同 BackwardKillLine-刪除從點到行首的文字，但不會將已刪除的文字放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="83915-168">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="83915-169">Cmd： `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="83915-169">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="83915-170">Vi 插入模式： `<Ctrl+u>` 、 `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="83915-170">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="83915-171">Vi 命令模式： `<Ctrl+u>` 、 `<Ctrl+Home>` 、 `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="83915-171">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`, `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="83915-172">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="83915-172">BackwardDeleteWord</span></span>

<span data-ttu-id="83915-173">刪除上一個字組。</span><span class="sxs-lookup"><span data-stu-id="83915-173">Deletes the previous word.</span></span>

- <span data-ttu-id="83915-174">Vi 命令模式： `<Ctrl+w>` 、 `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="83915-174">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="83915-175">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="83915-175">BackwardKillLine</span></span>

<span data-ttu-id="83915-176">清除輸入至資料指標開頭的輸入。</span><span class="sxs-lookup"><span data-stu-id="83915-176">Clear the input from the start of the input to the cursor.</span></span> <span data-ttu-id="83915-177">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="83915-177">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="83915-178">Emacs： `<Ctrl+u>` ， `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="83915-178">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="83915-179">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="83915-179">BackwardKillWord</span></span>

<span data-ttu-id="83915-180">清除從目前單字開頭到游標處的輸入。</span><span class="sxs-lookup"><span data-stu-id="83915-180">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="83915-181">如果游標在單字之間，則會從上一個單字開頭開始清除輸入至游標。</span><span class="sxs-lookup"><span data-stu-id="83915-181">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="83915-182">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="83915-182">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="83915-183">Cmd： `<Ctrl+Backspace>` ， `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="83915-183">Cmd: `<Ctrl+Backspace>`, `<Ctrl+w>`</span></span>
- <span data-ttu-id="83915-184">Emacs： `<Alt+Backspace>` ， `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="83915-184">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="83915-185">Vi 插入模式： `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="83915-185">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="83915-186">Vi 命令模式： `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="83915-186">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="83915-187">CancelLine</span><span class="sxs-lookup"><span data-stu-id="83915-187">CancelLine</span></span>

<span data-ttu-id="83915-188">取消目前的輸入，將輸入保留在畫面上，但返回主機，以便再次評估提示。</span><span class="sxs-lookup"><span data-stu-id="83915-188">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="83915-189">Vi 插入模式： `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="83915-189">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="83915-190">Vi 命令模式： `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="83915-190">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="83915-191">複製</span><span class="sxs-lookup"><span data-stu-id="83915-191">Copy</span></span>

<span data-ttu-id="83915-192">將選取的區域複製到系統剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="83915-192">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="83915-193">如果未選取任何區域，請複製整行。</span><span class="sxs-lookup"><span data-stu-id="83915-193">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="83915-194">Cmd： `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="83915-194">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="83915-195">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="83915-195">CopyOrCancelLine</span></span>

<span data-ttu-id="83915-196">如果已選取文字，請複製到剪貼簿，否則請取消該行。</span><span class="sxs-lookup"><span data-stu-id="83915-196">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="83915-197">Cmd： `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="83915-197">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="83915-198">Emacs： `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="83915-198">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="83915-199">剪下</span><span class="sxs-lookup"><span data-stu-id="83915-199">Cut</span></span>

<span data-ttu-id="83915-200">刪除選取的區域，將已刪除的文字放入系統剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="83915-200">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="83915-201">Cmd： `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="83915-201">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="83915-202">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="83915-202">DeleteChar</span></span>

<span data-ttu-id="83915-203">刪除游標下的字元。</span><span class="sxs-lookup"><span data-stu-id="83915-203">Delete the character under the cursor.</span></span>

- <span data-ttu-id="83915-204">Cmd： `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="83915-204">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="83915-205">Emacs： `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="83915-205">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="83915-206">Vi 插入模式： `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="83915-206">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="83915-207">Vi 命令模式： `<Delete>` 、 `<x>` 、 `<d,l>` 、 `<d,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="83915-207">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Spacebar>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="83915-208">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="83915-208">DeleteCharOrExit</span></span>

<span data-ttu-id="83915-209">刪除游標下的字元，如果行是空的，請結束進程。</span><span class="sxs-lookup"><span data-stu-id="83915-209">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="83915-210">Emacs： `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="83915-210">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofbuffer"></a><span data-ttu-id="83915-211">DeleteEndOfBuffer</span><span class="sxs-lookup"><span data-stu-id="83915-211">DeleteEndOfBuffer</span></span>

<span data-ttu-id="83915-212">刪除多行緩衝區的結尾。</span><span class="sxs-lookup"><span data-stu-id="83915-212">Deletes to the end of the multiline buffer.</span></span>

- <span data-ttu-id="83915-213">Vi 命令模式： `<d,G>`</span><span class="sxs-lookup"><span data-stu-id="83915-213">Vi command mode: `<d,G>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="83915-214">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="83915-214">DeleteEndOfWord</span></span>

<span data-ttu-id="83915-215">刪除到字尾。</span><span class="sxs-lookup"><span data-stu-id="83915-215">Delete to the end of the word.</span></span>

- <span data-ttu-id="83915-216">Vi 命令模式： `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="83915-216">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="83915-217">DeleteLine</span><span class="sxs-lookup"><span data-stu-id="83915-217">DeleteLine</span></span>

<span data-ttu-id="83915-218">刪除多行緩衝區的目前邏輯行，以啟用復原。</span><span class="sxs-lookup"><span data-stu-id="83915-218">Deletes the current logical line of a multiline buffer, enabling undo.</span></span>

- <span data-ttu-id="83915-219">Vi 命令模式： `<d,d>` 、 `<d,_>`</span><span class="sxs-lookup"><span data-stu-id="83915-219">Vi command mode: `<d,d>`, `<d,_>`</span></span>

### <a name="deletepreviouslines"></a><span data-ttu-id="83915-220">DeletePreviousLines</span><span class="sxs-lookup"><span data-stu-id="83915-220">DeletePreviousLines</span></span>

<span data-ttu-id="83915-221">刪除多行緩衝區中之前要求的邏輯行和目前的邏輯行。</span><span class="sxs-lookup"><span data-stu-id="83915-221">Deletes the previous requested logical lines and the current logical line in a multiline buffer.</span></span>

- <span data-ttu-id="83915-222">Vi 命令模式： `<d,k>`</span><span class="sxs-lookup"><span data-stu-id="83915-222">Vi command mode: `<d,k>`</span></span>

### <a name="deleterelativelines"></a><span data-ttu-id="83915-223">DeleteRelativeLines</span><span class="sxs-lookup"><span data-stu-id="83915-223">DeleteRelativeLines</span></span>

<span data-ttu-id="83915-224">從緩衝區的開頭刪除多行緩衝區中目前的邏輯行。</span><span class="sxs-lookup"><span data-stu-id="83915-224">Deletes from the beginning of the buffer to the current logical line in a multiline buffer.</span></span>

<span data-ttu-id="83915-225">最多有 Vi 個命令， `<d,g,g>` 命令前面會加上指定絕對行號的數值引數，這會和目前的行號一起組成要刪除的行範圍。</span><span class="sxs-lookup"><span data-stu-id="83915-225">As most Vi commands, the `<d,g,g>` command can be prepended with a numeric argument that specifies an absolute line number, which, together with the current line number, make up a range of lines to be deleted.</span></span>
<span data-ttu-id="83915-226">如果未指定，則數值引數會預設為1，這會參考多行緩衝區中的第一個邏輯行。</span><span class="sxs-lookup"><span data-stu-id="83915-226">If not specified, the numeric argument defaults to 1, which refers to the first logical line in a multiline buffer.</span></span>

<span data-ttu-id="83915-227">要從多行刪除的實際行數，會計算為目前的邏輯行號和指定的數值引數之間的差異，因此可能是負數。</span><span class="sxs-lookup"><span data-stu-id="83915-227">The actual number of lines to be deleted from the multiline is computed as the difference between the current logical line number and the specified numeric argument, which can thus be negative.</span></span> <span data-ttu-id="83915-228">因此，方法名稱的 _相對_ 部分。</span><span class="sxs-lookup"><span data-stu-id="83915-228">Hence the _relative_ part of method name.</span></span>

- <span data-ttu-id="83915-229">Vi 命令模式： `<d,g,g>`</span><span class="sxs-lookup"><span data-stu-id="83915-229">Vi command mode: `<d,g,g>`</span></span>

### <a name="deletenextlines"></a><span data-ttu-id="83915-230">DeleteNextLines</span><span class="sxs-lookup"><span data-stu-id="83915-230">DeleteNextLines</span></span>

<span data-ttu-id="83915-231">刪除多行緩衝區中目前的邏輯行和下一個要求的邏輯行。</span><span class="sxs-lookup"><span data-stu-id="83915-231">Deletes the current logical line and the next requested logical lines in a multiline buffer.</span></span>

- <span data-ttu-id="83915-232">Vi 命令模式： `<d,j>`</span><span class="sxs-lookup"><span data-stu-id="83915-232">Vi command mode: `<d,j>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="83915-233">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="83915-233">DeleteLineToFirstChar</span></span>

<span data-ttu-id="83915-234">將游標的文字刪除到行的第一個非空白字元。</span><span class="sxs-lookup"><span data-stu-id="83915-234">Deletes text from the cursor to the first non-blank character of the line.</span></span>

- <span data-ttu-id="83915-235">Vi 命令模式： `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="83915-235">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="83915-236">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="83915-236">DeleteToEnd</span></span>

<span data-ttu-id="83915-237">刪除至行尾。</span><span class="sxs-lookup"><span data-stu-id="83915-237">Delete to the end of the line.</span></span>

- <span data-ttu-id="83915-238">Vi 命令模式： `<D>` 、 `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="83915-238">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="83915-239">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="83915-239">DeleteWord</span></span>

<span data-ttu-id="83915-240">刪除下一個字組。</span><span class="sxs-lookup"><span data-stu-id="83915-240">Delete the next word.</span></span>

- <span data-ttu-id="83915-241">Vi 命令模式： `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="83915-241">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="83915-242">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="83915-242">ForwardDeleteLine</span></span>

<span data-ttu-id="83915-243">如同 ForwardKillLine-刪除從點到行尾的文字，但不會將已刪除的文字放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="83915-243">Like ForwardKillLine - deletes text from the point to the end of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="83915-244">Cmd： `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="83915-244">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="83915-245">Vi 插入模式： `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="83915-245">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="83915-246">Vi 命令模式： `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="83915-246">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="83915-247">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="83915-247">InsertLineAbove</span></span>

<span data-ttu-id="83915-248">無論游標位於目前的行上，都會在目前的行上方建立新的空白行。</span><span class="sxs-lookup"><span data-stu-id="83915-248">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="83915-249">游標移至新行的開頭。</span><span class="sxs-lookup"><span data-stu-id="83915-249">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="83915-250">Cmd： `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="83915-250">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="83915-251">InsertLineBelow</span><span class="sxs-lookup"><span data-stu-id="83915-251">InsertLineBelow</span></span>

<span data-ttu-id="83915-252">目前的行下方會建立新的空白行，而不論游標在目前的行上。</span><span class="sxs-lookup"><span data-stu-id="83915-252">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="83915-253">游標移至新行的開頭。</span><span class="sxs-lookup"><span data-stu-id="83915-253">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="83915-254">Cmd： `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="83915-254">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="83915-255">InvertCase</span><span class="sxs-lookup"><span data-stu-id="83915-255">InvertCase</span></span>

<span data-ttu-id="83915-256">將目前字元的大小寫反轉，並移至下一個字元。</span><span class="sxs-lookup"><span data-stu-id="83915-256">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="83915-257">Vi 命令模式： `<~>`</span><span class="sxs-lookup"><span data-stu-id="83915-257">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="83915-258">KillLine</span><span class="sxs-lookup"><span data-stu-id="83915-258">KillLine</span></span>

<span data-ttu-id="83915-259">清除游標至輸入結尾的輸入。</span><span class="sxs-lookup"><span data-stu-id="83915-259">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="83915-260">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="83915-260">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="83915-261">Emacs： `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="83915-261">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="83915-262">KillRegion</span><span class="sxs-lookup"><span data-stu-id="83915-262">KillRegion</span></span>

<span data-ttu-id="83915-263">終止游標與標記之間的文字。</span><span class="sxs-lookup"><span data-stu-id="83915-263">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="83915-264">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="83915-264">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="83915-265">KillWord</span><span class="sxs-lookup"><span data-stu-id="83915-265">KillWord</span></span>

<span data-ttu-id="83915-266">清除游標到目前單字結尾的輸入。</span><span class="sxs-lookup"><span data-stu-id="83915-266">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="83915-267">如果游標在單字之間，則會從資料指標清除輸入至下一個單字的結尾。</span><span class="sxs-lookup"><span data-stu-id="83915-267">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="83915-268">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="83915-268">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="83915-269">Cmd： `<Alt+d>` ， `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="83915-269">Cmd: `<Alt+d>`, `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="83915-270">Emacs： `<Alt+d>` ， `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="83915-270">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="83915-271">Vi 插入模式： `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="83915-271">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="83915-272">Vi 命令模式： `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="83915-272">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="83915-273">貼上</span><span class="sxs-lookup"><span data-stu-id="83915-273">Paste</span></span>

<span data-ttu-id="83915-274">貼上系統剪貼簿中的文字。</span><span class="sxs-lookup"><span data-stu-id="83915-274">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="83915-275">Cmd： `<Ctrl+v>` ， `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="83915-275">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="83915-276">Vi 插入模式： `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="83915-276">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="83915-277">Vi 命令模式： `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="83915-277">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="83915-278">使用 **Paste** 函式時，剪貼簿緩衝區的整個內容會貼到 PSReadLine 的輸入緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="83915-278">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="83915-279">輸入緩衝區接著會傳遞至 PowerShell 剖析器。</span><span class="sxs-lookup"><span data-stu-id="83915-279">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="83915-280">使用主控台應用程式的 **按右鍵** [貼上] 方法貼上的輸入會一次複製到輸入緩衝區一個字元。</span><span class="sxs-lookup"><span data-stu-id="83915-280">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="83915-281">當換行字元時，輸入緩衝區會傳遞給剖析器。</span><span class="sxs-lookup"><span data-stu-id="83915-281">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="83915-282">因此，輸入會一次剖析一行。</span><span class="sxs-lookup"><span data-stu-id="83915-282">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="83915-283">貼上方法之間的差異會導致不同的執行行為。</span><span class="sxs-lookup"><span data-stu-id="83915-283">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="83915-284">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="83915-284">PasteAfter</span></span>

<span data-ttu-id="83915-285">將剪貼簿貼到游標之後，將游標移至貼上文字的結尾。</span><span class="sxs-lookup"><span data-stu-id="83915-285">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="83915-286">Vi 命令模式： `<p>`</span><span class="sxs-lookup"><span data-stu-id="83915-286">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="83915-287">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="83915-287">PasteBefore</span></span>

<span data-ttu-id="83915-288">將剪貼簿貼到游標之前，將游標移至貼上文字的結尾。</span><span class="sxs-lookup"><span data-stu-id="83915-288">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="83915-289">Vi 命令模式： `<P>`</span><span class="sxs-lookup"><span data-stu-id="83915-289">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="83915-290">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="83915-290">PrependAndAccept</span></span>

<span data-ttu-id="83915-291">在前面加上 ' # ' 並接受該行。</span><span class="sxs-lookup"><span data-stu-id="83915-291">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="83915-292">Vi 命令模式： `<#>`</span><span class="sxs-lookup"><span data-stu-id="83915-292">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="83915-293">取消復原</span><span class="sxs-lookup"><span data-stu-id="83915-293">Redo</span></span>

<span data-ttu-id="83915-294">復原復原。</span><span class="sxs-lookup"><span data-stu-id="83915-294">Undo an undo.</span></span>

- <span data-ttu-id="83915-295">Cmd： `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="83915-295">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="83915-296">Vi 插入模式： `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="83915-296">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="83915-297">Vi 命令模式： `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="83915-297">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="83915-298">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="83915-298">RepeatLastCommand</span></span>

<span data-ttu-id="83915-299">重複上次修改文字。</span><span class="sxs-lookup"><span data-stu-id="83915-299">Repeat the last text modification.</span></span>

- <span data-ttu-id="83915-300">Vi 命令模式： `<.>`</span><span class="sxs-lookup"><span data-stu-id="83915-300">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="83915-301">RevertLine</span><span class="sxs-lookup"><span data-stu-id="83915-301">RevertLine</span></span>

<span data-ttu-id="83915-302">將所有輸入還原為目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="83915-302">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="83915-303">Cmd： `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="83915-303">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="83915-304">Emacs： `<Alt+r>` ， `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="83915-304">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="83915-305">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="83915-305">ShellBackwardKillWord</span></span>

<span data-ttu-id="83915-306">清除從目前單字開頭到游標處的輸入。</span><span class="sxs-lookup"><span data-stu-id="83915-306">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="83915-307">如果游標在單字之間，則會從上一個單字開頭開始清除輸入至游標。</span><span class="sxs-lookup"><span data-stu-id="83915-307">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="83915-308">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="83915-308">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="83915-309">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="83915-309">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="83915-310">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="83915-310">ShellKillWord</span></span>

<span data-ttu-id="83915-311">清除游標到目前單字結尾的輸入。</span><span class="sxs-lookup"><span data-stu-id="83915-311">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="83915-312">如果游標在單字之間，則會從資料指標清除輸入至下一個單字的結尾。</span><span class="sxs-lookup"><span data-stu-id="83915-312">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="83915-313">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="83915-313">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="83915-314">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="83915-314">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="83915-315">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="83915-315">SwapCharacters</span></span>

<span data-ttu-id="83915-316">交換目前的字元和前一個字元。</span><span class="sxs-lookup"><span data-stu-id="83915-316">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="83915-317">Emacs： `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="83915-317">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="83915-318">Vi 插入模式： `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="83915-318">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="83915-319">Vi 命令模式： `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="83915-319">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="83915-320">復原</span><span class="sxs-lookup"><span data-stu-id="83915-320">Undo</span></span>

<span data-ttu-id="83915-321">復原先前的編輯。</span><span class="sxs-lookup"><span data-stu-id="83915-321">Undo a previous edit.</span></span>

- <span data-ttu-id="83915-322">Cmd： `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="83915-322">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="83915-323">Emacs： `<Ctrl+_>` ， `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="83915-323">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="83915-324">Vi 插入模式： `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="83915-324">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="83915-325">Vi 命令模式： `<Ctrl+z>` 、 `<u>`</span><span class="sxs-lookup"><span data-stu-id="83915-325">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="83915-326">UndoAll</span><span class="sxs-lookup"><span data-stu-id="83915-326">UndoAll</span></span>

<span data-ttu-id="83915-327">復原所有先前編輯的行。</span><span class="sxs-lookup"><span data-stu-id="83915-327">Undo all previous edits for line.</span></span>

- <span data-ttu-id="83915-328">Vi 命令模式： `<U>`</span><span class="sxs-lookup"><span data-stu-id="83915-328">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="83915-329">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="83915-329">UnixWordRubout</span></span>

<span data-ttu-id="83915-330">清除從目前單字開頭到游標處的輸入。</span><span class="sxs-lookup"><span data-stu-id="83915-330">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="83915-331">如果游標在單字之間，則會從上一個單字開頭開始清除輸入至游標。</span><span class="sxs-lookup"><span data-stu-id="83915-331">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="83915-332">清除的文字會放在終止環形中。</span><span class="sxs-lookup"><span data-stu-id="83915-332">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="83915-333">Emacs： `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="83915-333">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="83915-334">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="83915-334">ValidateAndAcceptLine</span></span>

<span data-ttu-id="83915-335">嘗試執行目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="83915-335">Attempt to execute the current input.</span></span> <span data-ttu-id="83915-336">如果目前的輸入不完整 (例如遺漏右括弧、方括弧或引號，則接續提示會顯示在下一行，而 PSReadLine 會等候按鍵編輯目前的輸入。</span><span class="sxs-lookup"><span data-stu-id="83915-336">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="83915-337">Emacs： `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="83915-337">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="83915-338">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="83915-338">ViAcceptLine</span></span>

<span data-ttu-id="83915-339">接受行並切換至插入模式。</span><span class="sxs-lookup"><span data-stu-id="83915-339">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="83915-340">Vi 命令模式： `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="83915-340">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="83915-341">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="83915-341">ViAcceptLineOrExit</span></span>

<span data-ttu-id="83915-342">如同 Emacs 模式中的 DeleteCharOrExit，但會接受行，而不是刪除字元。</span><span class="sxs-lookup"><span data-stu-id="83915-342">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="83915-343">Vi 插入模式： `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="83915-343">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="83915-344">Vi 命令模式： `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="83915-344">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="83915-345">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="83915-345">ViAppendLine</span></span>

<span data-ttu-id="83915-346">新行會插入目前的行下方。</span><span class="sxs-lookup"><span data-stu-id="83915-346">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="83915-347">Vi 命令模式： `<o>`</span><span class="sxs-lookup"><span data-stu-id="83915-347">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="83915-348">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="83915-348">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="83915-349">刪除先前的單字，只使用空白字元做為文字分隔符號。</span><span class="sxs-lookup"><span data-stu-id="83915-349">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="83915-350">Vi 命令模式： `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="83915-350">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="83915-351">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="83915-351">ViBackwardGlob</span></span>

<span data-ttu-id="83915-352">將游標移回上一個單字的開頭，只使用空白字元做為分隔符號。</span><span class="sxs-lookup"><span data-stu-id="83915-352">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="83915-353">Vi 命令模式： `<B>`</span><span class="sxs-lookup"><span data-stu-id="83915-353">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="83915-354">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="83915-354">ViDeleteBrace</span></span>

<span data-ttu-id="83915-355">尋找相符的括弧、括弧或方括弧，並刪除內的所有內容，包括括弧。</span><span class="sxs-lookup"><span data-stu-id="83915-355">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="83915-356">Vi 命令模式： `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="83915-356">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="83915-357">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="83915-357">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="83915-358">刪除到字尾。</span><span class="sxs-lookup"><span data-stu-id="83915-358">Delete to the end of the word.</span></span>

- <span data-ttu-id="83915-359">Vi 命令模式： `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="83915-359">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="83915-360">ViDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="83915-360">ViDeleteGlob</span></span>

<span data-ttu-id="83915-361">刪除下一個 glob (以空白字元分隔的單字) 。</span><span class="sxs-lookup"><span data-stu-id="83915-361">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="83915-362">Vi 命令模式： `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="83915-362">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="83915-363">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="83915-363">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="83915-364">刪除指定的字元。</span><span class="sxs-lookup"><span data-stu-id="83915-364">Deletes until given character.</span></span>

- <span data-ttu-id="83915-365">Vi 命令模式： `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="83915-365">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="83915-366">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="83915-366">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="83915-367">刪除指定的字元。</span><span class="sxs-lookup"><span data-stu-id="83915-367">Deletes until given character.</span></span>

- <span data-ttu-id="83915-368">Vi 命令模式： `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="83915-368">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="83915-369">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="83915-369">ViDeleteToChar</span></span>

<span data-ttu-id="83915-370">刪除指定的字元。</span><span class="sxs-lookup"><span data-stu-id="83915-370">Deletes until given character.</span></span>

- <span data-ttu-id="83915-371">Vi 命令模式： `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="83915-371">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="83915-372">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="83915-372">ViDeleteToCharBackward</span></span>

<span data-ttu-id="83915-373">在指定的字元之前反向刪除。</span><span class="sxs-lookup"><span data-stu-id="83915-373">Deletes backwards until given character.</span></span>

- <span data-ttu-id="83915-374">Vi 命令模式： `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="83915-374">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="83915-375">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="83915-375">ViInsertAtBegining</span></span>

<span data-ttu-id="83915-376">切換至插入模式，並將游標放在行首。</span><span class="sxs-lookup"><span data-stu-id="83915-376">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="83915-377">Vi 命令模式： `<I>`</span><span class="sxs-lookup"><span data-stu-id="83915-377">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="83915-378">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="83915-378">ViInsertAtEnd</span></span>

<span data-ttu-id="83915-379">切換至插入模式，並將游標放在行尾。</span><span class="sxs-lookup"><span data-stu-id="83915-379">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="83915-380">Vi 命令模式： `<A>`</span><span class="sxs-lookup"><span data-stu-id="83915-380">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="83915-381">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="83915-381">ViInsertLine</span></span>

<span data-ttu-id="83915-382">新的行會插入到目前這一行的上方。</span><span class="sxs-lookup"><span data-stu-id="83915-382">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="83915-383">Vi 命令模式： `<O>`</span><span class="sxs-lookup"><span data-stu-id="83915-383">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="83915-384">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="83915-384">ViInsertWithAppend</span></span>

<span data-ttu-id="83915-385">從目前的行位置附加。</span><span class="sxs-lookup"><span data-stu-id="83915-385">Append from the current line position.</span></span>

- <span data-ttu-id="83915-386">Vi 命令模式： `<a>`</span><span class="sxs-lookup"><span data-stu-id="83915-386">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="83915-387">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="83915-387">ViInsertWithDelete</span></span>

<span data-ttu-id="83915-388">刪除目前的字元並切換至插入模式。</span><span class="sxs-lookup"><span data-stu-id="83915-388">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="83915-389">Vi 命令模式： `<s>`</span><span class="sxs-lookup"><span data-stu-id="83915-389">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="83915-390">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="83915-390">ViJoinLines</span></span>

<span data-ttu-id="83915-391">加入目前的行和下一行。</span><span class="sxs-lookup"><span data-stu-id="83915-391">Joins the current line and the next line.</span></span>

- <span data-ttu-id="83915-392">Vi 命令模式： `<J>`</span><span class="sxs-lookup"><span data-stu-id="83915-392">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="83915-393">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="83915-393">ViReplaceLine</span></span>

<span data-ttu-id="83915-394">清除整個命令列。</span><span class="sxs-lookup"><span data-stu-id="83915-394">Erase the entire command line.</span></span>

- <span data-ttu-id="83915-395">Vi 命令模式： `<S>` 、 `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="83915-395">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="83915-396">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="83915-396">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="83915-397">取代指定的字元。</span><span class="sxs-lookup"><span data-stu-id="83915-397">Replaces until given character.</span></span>

- <span data-ttu-id="83915-398">Vi 命令模式： `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="83915-398">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="83915-399">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="83915-399">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="83915-400">取代指定的字元。</span><span class="sxs-lookup"><span data-stu-id="83915-400">Replaces until given character.</span></span>

- <span data-ttu-id="83915-401">Vi 命令模式： `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="83915-401">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="83915-402">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="83915-402">ViReplaceToChar</span></span>

<span data-ttu-id="83915-403">刪除指定的字元。</span><span class="sxs-lookup"><span data-stu-id="83915-403">Deletes until given character.</span></span>

- <span data-ttu-id="83915-404">Vi 命令模式： `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="83915-404">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="83915-405">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="83915-405">ViReplaceToCharBackward</span></span>

<span data-ttu-id="83915-406">取代指定的字元。</span><span class="sxs-lookup"><span data-stu-id="83915-406">Replaces until given character.</span></span>

- <span data-ttu-id="83915-407">Vi 命令模式： `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="83915-407">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="83915-408">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="83915-408">ViYankBeginningOfLine</span></span>

<span data-ttu-id="83915-409">從緩衝區開頭 Yank 至資料指標。</span><span class="sxs-lookup"><span data-stu-id="83915-409">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="83915-410">Vi 命令模式： `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="83915-410">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="83915-411">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="83915-411">ViYankEndOfGlob</span></span>

<span data-ttu-id="83915-412">從資料指標 Yank 至 WORD (s) 的結尾。</span><span class="sxs-lookup"><span data-stu-id="83915-412">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="83915-413">Vi 命令模式： `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="83915-413">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="83915-414">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="83915-414">ViYankEndOfWord</span></span>

<span data-ttu-id="83915-415">從資料指標 Yank 至 word (s) 的結尾。</span><span class="sxs-lookup"><span data-stu-id="83915-415">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="83915-416">Vi 命令模式： `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="83915-416">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="83915-417">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="83915-417">ViYankLeft</span></span>

<span data-ttu-id="83915-418">Yank 字元 (s) 到游標的左邊。</span><span class="sxs-lookup"><span data-stu-id="83915-418">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="83915-419">Vi 命令模式： `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="83915-419">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="83915-420">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="83915-420">ViYankLine</span></span>

<span data-ttu-id="83915-421">Yank 整個緩衝區。</span><span class="sxs-lookup"><span data-stu-id="83915-421">Yank the entire buffer.</span></span>

- <span data-ttu-id="83915-422">Vi 命令模式： `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="83915-422">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="83915-423">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="83915-423">ViYankNextGlob</span></span>

<span data-ttu-id="83915-424">從資料指標 Yank 至下一個單字的開頭 (s) 。</span><span class="sxs-lookup"><span data-stu-id="83915-424">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="83915-425">Vi 命令模式： `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="83915-425">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="83915-426">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="83915-426">ViYankNextWord</span></span>

<span data-ttu-id="83915-427">Yank) 在游標之後 (s 的單字。</span><span class="sxs-lookup"><span data-stu-id="83915-427">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="83915-428">Vi 命令模式： `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="83915-428">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="83915-429">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="83915-429">ViYankPercent</span></span>

<span data-ttu-id="83915-430">Yank 至/從相符的括弧。</span><span class="sxs-lookup"><span data-stu-id="83915-430">Yank to/from matching brace.</span></span>

- <span data-ttu-id="83915-431">Vi 命令模式： `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="83915-431">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="83915-432">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="83915-432">ViYankPreviousGlob</span></span>

<span data-ttu-id="83915-433">從字組開頭 (s 的 Yank) 到資料指標。</span><span class="sxs-lookup"><span data-stu-id="83915-433">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="83915-434">Vi 命令模式： `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="83915-434">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="83915-435">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="83915-435">ViYankPreviousWord</span></span>

<span data-ttu-id="83915-436">Yank) 在游標之前的文字 (s。</span><span class="sxs-lookup"><span data-stu-id="83915-436">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="83915-437">Vi 命令模式： `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="83915-437">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="83915-438">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="83915-438">ViYankRight</span></span>

<span data-ttu-id="83915-439">Yank 字元 (s) 在游標右邊和右邊。</span><span class="sxs-lookup"><span data-stu-id="83915-439">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="83915-440">Vi 命令模式： `<y,l>` 、 `<y,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="83915-440">Vi command mode: `<y,l>`, `<y,Spacebar>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="83915-441">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="83915-441">ViYankToEndOfLine</span></span>

<span data-ttu-id="83915-442">從資料指標 Yank 至緩衝區的結尾。</span><span class="sxs-lookup"><span data-stu-id="83915-442">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="83915-443">Vi 命令模式： `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="83915-443">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="83915-444">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="83915-444">ViYankToFirstChar</span></span>

<span data-ttu-id="83915-445">從第一個非空白字元 Yank 至游標。</span><span class="sxs-lookup"><span data-stu-id="83915-445">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="83915-446">Vi 命令模式： `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="83915-446">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="83915-447">美國 佬</span><span class="sxs-lookup"><span data-stu-id="83915-447">Yank</span></span>

<span data-ttu-id="83915-448">將最近終止的文字加入至輸入。</span><span class="sxs-lookup"><span data-stu-id="83915-448">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="83915-449">Emacs： `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="83915-449">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="83915-450">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="83915-450">YankLastArg</span></span>

<span data-ttu-id="83915-451">Yank 前一個歷程記錄行中的最後一個引數。</span><span class="sxs-lookup"><span data-stu-id="83915-451">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="83915-452">使用引數時，第一次叫用時，其行為就像 YankNthArg 一樣。</span><span class="sxs-lookup"><span data-stu-id="83915-452">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="83915-453">如果叫用多次，則改為逐一查看歷程記錄和 arg，將方向 (負反轉方向。 ) </span><span class="sxs-lookup"><span data-stu-id="83915-453">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="83915-454">Cmd： `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="83915-454">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="83915-455">Emacs： `<Alt+.>` 、 `<Alt+_>` 、 `<Escape,.>` 、 `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="83915-455">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="83915-456">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="83915-456">YankNthArg</span></span>

<span data-ttu-id="83915-457">從上一個歷程記錄行中 Yank 命令) 之後，第一個引數 (。</span><span class="sxs-lookup"><span data-stu-id="83915-457">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="83915-458">使用引數時，請 yank 第 n 個引數 (從 0) 開始，如果引數為負數，則從最後一個引數開始。</span><span class="sxs-lookup"><span data-stu-id="83915-458">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="83915-459">Emacs： `<Ctrl+Alt+y>` ， `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="83915-459">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="83915-460">YankPop</span><span class="sxs-lookup"><span data-stu-id="83915-460">YankPop</span></span>

<span data-ttu-id="83915-461">如果先前的作業是 Yank 或 YankPop，請將先前 yanked 的文字取代為終止環形中的下一個已取消文字。</span><span class="sxs-lookup"><span data-stu-id="83915-461">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="83915-462">Emacs： `<Alt+y>` ， `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="83915-462">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="83915-463">資料指標移動函數</span><span class="sxs-lookup"><span data-stu-id="83915-463">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="83915-464">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="83915-464">BackwardChar</span></span>

<span data-ttu-id="83915-465">將游標向左移動一個字元。</span><span class="sxs-lookup"><span data-stu-id="83915-465">Move the cursor one character to the left.</span></span> <span data-ttu-id="83915-466">這可能會將游標移至多行輸入的上一行。</span><span class="sxs-lookup"><span data-stu-id="83915-466">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="83915-467">Cmd： `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="83915-467">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="83915-468">Emacs： `<LeftArrow>` ， `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="83915-468">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="83915-469">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="83915-469">BackwardWord</span></span>

<span data-ttu-id="83915-470">將游標移回目前單字的開頭，或將游標移回上一個單字開頭的單字。</span><span class="sxs-lookup"><span data-stu-id="83915-470">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="83915-471">單字界限是由一組可設定的字元所定義。</span><span class="sxs-lookup"><span data-stu-id="83915-471">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="83915-472">Cmd： `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="83915-472">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="83915-473">Emacs： `<Alt+b>` ， `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="83915-473">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="83915-474">Vi 插入模式： `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="83915-474">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="83915-475">Vi 命令模式： `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="83915-475">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="83915-476">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="83915-476">BeginningOfLine</span></span>

<span data-ttu-id="83915-477">如果輸入有多行，請移至目前行的開頭，如果已經在行首，則移至輸入的開頭。</span><span class="sxs-lookup"><span data-stu-id="83915-477">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="83915-478">如果輸入具有單一行，請移至輸入的開頭。</span><span class="sxs-lookup"><span data-stu-id="83915-478">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="83915-479">Cmd： `<Home>`</span><span class="sxs-lookup"><span data-stu-id="83915-479">Cmd: `<Home>`</span></span>
- <span data-ttu-id="83915-480">Emacs： `<Home>` ， `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="83915-480">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="83915-481">Vi 插入模式： `<Home>`</span><span class="sxs-lookup"><span data-stu-id="83915-481">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="83915-482">Vi 命令模式： `<Home>`</span><span class="sxs-lookup"><span data-stu-id="83915-482">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="83915-483">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="83915-483">EndOfLine</span></span>

<span data-ttu-id="83915-484">如果輸入有多行，請移至目前行的結尾，如果已經在行尾，則移至輸入的結尾。</span><span class="sxs-lookup"><span data-stu-id="83915-484">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="83915-485">如果輸入具有單一行，請移至輸入的結尾。</span><span class="sxs-lookup"><span data-stu-id="83915-485">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="83915-486">Cmd： `<End>`</span><span class="sxs-lookup"><span data-stu-id="83915-486">Cmd: `<End>`</span></span>
- <span data-ttu-id="83915-487">Emacs： `<End>` ， `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="83915-487">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="83915-488">Vi 插入模式： `<End>`</span><span class="sxs-lookup"><span data-stu-id="83915-488">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="83915-489">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="83915-489">ForwardChar</span></span>

<span data-ttu-id="83915-490">將游標向右移動一個字元。</span><span class="sxs-lookup"><span data-stu-id="83915-490">Move the cursor one character to the right.</span></span> <span data-ttu-id="83915-491">這可能會將游標移至下一行的多行輸入。</span><span class="sxs-lookup"><span data-stu-id="83915-491">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="83915-492">Cmd： `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="83915-492">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="83915-493">Emacs： `<RightArrow>` ， `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="83915-493">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="83915-494">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="83915-494">ForwardWord</span></span>

<span data-ttu-id="83915-495">將游標向前移動至目前單字的結尾，或在文字之間移動到下一個單字的結尾。</span><span class="sxs-lookup"><span data-stu-id="83915-495">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="83915-496">單字界限是由一組可設定的字元所定義。</span><span class="sxs-lookup"><span data-stu-id="83915-496">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="83915-497">Emacs： `<Alt+f>` ， `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="83915-497">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="83915-498">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="83915-498">GotoBrace</span></span>

<span data-ttu-id="83915-499">移至相符的大括弧、括弧或方括弧。</span><span class="sxs-lookup"><span data-stu-id="83915-499">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="83915-500">Cmd： `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="83915-500">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="83915-501">Vi 插入模式： `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="83915-501">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="83915-502">Vi 命令模式： `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="83915-502">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="83915-503">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="83915-503">GotoColumn</span></span>

<span data-ttu-id="83915-504">移至 arg 所表示的資料行。</span><span class="sxs-lookup"><span data-stu-id="83915-504">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="83915-505">Vi 命令模式： `<|>`</span><span class="sxs-lookup"><span data-stu-id="83915-505">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="83915-506">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="83915-506">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="83915-507">將游標移至行中的第一個非空白字元。</span><span class="sxs-lookup"><span data-stu-id="83915-507">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="83915-508">Vi 命令模式： `<^>` 、 `<_>`</span><span class="sxs-lookup"><span data-stu-id="83915-508">Vi command mode: `<^>`, `<_>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="83915-509">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="83915-509">MoveToEndOfLine</span></span>

<span data-ttu-id="83915-510">將游標移至輸入的結尾。</span><span class="sxs-lookup"><span data-stu-id="83915-510">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="83915-511">Vi 命令模式： `<End>` 、 `<$>`</span><span class="sxs-lookup"><span data-stu-id="83915-511">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="83915-512">NextLine</span><span class="sxs-lookup"><span data-stu-id="83915-512">NextLine</span></span>

<span data-ttu-id="83915-513">將游標移至下一行。</span><span class="sxs-lookup"><span data-stu-id="83915-513">Move the cursor to the next line.</span></span>

- <span data-ttu-id="83915-514">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="83915-514">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="83915-515">NextWord</span><span class="sxs-lookup"><span data-stu-id="83915-515">NextWord</span></span>

<span data-ttu-id="83915-516">將游標向前移至下一個單字的開頭。</span><span class="sxs-lookup"><span data-stu-id="83915-516">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="83915-517">單字界限是由一組可設定的字元所定義。</span><span class="sxs-lookup"><span data-stu-id="83915-517">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="83915-518">Cmd： `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="83915-518">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="83915-519">Vi 插入模式： `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="83915-519">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="83915-520">Vi 命令模式： `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="83915-520">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="83915-521">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="83915-521">NextWordEnd</span></span>

<span data-ttu-id="83915-522">將游標向前移動至目前單字的結尾，或在文字之間移動到下一個單字的結尾。</span><span class="sxs-lookup"><span data-stu-id="83915-522">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="83915-523">單字界限是由一組可設定的字元所定義。</span><span class="sxs-lookup"><span data-stu-id="83915-523">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="83915-524">Vi 命令模式： `<e>`</span><span class="sxs-lookup"><span data-stu-id="83915-524">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="83915-525">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="83915-525">PreviousLine</span></span>

<span data-ttu-id="83915-526">將游標移至上一行。</span><span class="sxs-lookup"><span data-stu-id="83915-526">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="83915-527">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="83915-527">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="83915-528">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="83915-528">ShellBackwardWord</span></span>

<span data-ttu-id="83915-529">將游標移回目前單字的開頭，或將游標移回上一個單字開頭的單字。</span><span class="sxs-lookup"><span data-stu-id="83915-529">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="83915-530">單字界限是由 PowerShell 權杖所定義。</span><span class="sxs-lookup"><span data-stu-id="83915-530">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="83915-531">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="83915-531">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="83915-532">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="83915-532">ShellForwardWord</span></span>

<span data-ttu-id="83915-533">將游標向前移至下一個單字的開頭。</span><span class="sxs-lookup"><span data-stu-id="83915-533">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="83915-534">單字界限是由 PowerShell 權杖所定義。</span><span class="sxs-lookup"><span data-stu-id="83915-534">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="83915-535">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="83915-535">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="83915-536">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="83915-536">ShellNextWord</span></span>

<span data-ttu-id="83915-537">將游標向前移動至目前單字的結尾，或在文字之間移動到下一個單字的結尾。</span><span class="sxs-lookup"><span data-stu-id="83915-537">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="83915-538">單字界限是由 PowerShell 權杖所定義。</span><span class="sxs-lookup"><span data-stu-id="83915-538">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="83915-539">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="83915-539">Function is unbound.</span></span>

### <a name="vibackwardchar"></a><span data-ttu-id="83915-540">ViBackwardChar</span><span class="sxs-lookup"><span data-stu-id="83915-540">ViBackwardChar</span></span>

<span data-ttu-id="83915-541">將游標移至 Vi 編輯模式的左邊一個字元。</span><span class="sxs-lookup"><span data-stu-id="83915-541">Move the cursor one character to the left in the Vi edit mode.</span></span> <span data-ttu-id="83915-542">這可能會將游標移至多行輸入的上一行。</span><span class="sxs-lookup"><span data-stu-id="83915-542">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="83915-543">Vi 插入模式： `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="83915-543">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="83915-544">Vi 命令模式： `<LeftArrow>` 、 `<Backspace>` 、 `<h>`</span><span class="sxs-lookup"><span data-stu-id="83915-544">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="83915-545">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="83915-545">ViBackwardWord</span></span>

<span data-ttu-id="83915-546">將游標移回目前單字的開頭，或將游標移回上一個單字開頭的單字。</span><span class="sxs-lookup"><span data-stu-id="83915-546">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="83915-547">單字界限是由一組可設定的字元所定義。</span><span class="sxs-lookup"><span data-stu-id="83915-547">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="83915-548">Vi 命令模式： `<b>`</span><span class="sxs-lookup"><span data-stu-id="83915-548">Vi command mode: `<b>`</span></span>

### <a name="viforwardchar"></a><span data-ttu-id="83915-549">ViForwardChar</span><span class="sxs-lookup"><span data-stu-id="83915-549">ViForwardChar</span></span>

<span data-ttu-id="83915-550">將游標移至 Vi 編輯模式的右側一個字元。</span><span class="sxs-lookup"><span data-stu-id="83915-550">Move the cursor one character to the right in the Vi edit mode.</span></span> <span data-ttu-id="83915-551">這可能會將游標移至下一行的多行輸入。</span><span class="sxs-lookup"><span data-stu-id="83915-551">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="83915-552">Vi 插入模式： `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="83915-552">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="83915-553">Vi 命令模式： `<RightArrow>` 、 `<Spacebar>` 、 `<l>`</span><span class="sxs-lookup"><span data-stu-id="83915-553">Vi command mode: `<RightArrow>`, `<Spacebar>`, `<l>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="83915-554">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="83915-554">ViEndOfGlob</span></span>

<span data-ttu-id="83915-555">將游標移至單字的結尾，只使用空白字元做為分隔符號。</span><span class="sxs-lookup"><span data-stu-id="83915-555">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="83915-556">Vi 命令模式： `<E>`</span><span class="sxs-lookup"><span data-stu-id="83915-556">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="83915-557">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="83915-557">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="83915-558">移至上一個單字的結尾，只使用空白字元做為單字分隔符號。</span><span class="sxs-lookup"><span data-stu-id="83915-558">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="83915-559">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="83915-559">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="83915-560">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="83915-560">ViGotoBrace</span></span>

<span data-ttu-id="83915-561">類似于 GotoBrace，但它是以字元為基礎，而不是以權杖為基礎。</span><span class="sxs-lookup"><span data-stu-id="83915-561">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="83915-562">Vi 命令模式： `<%>`</span><span class="sxs-lookup"><span data-stu-id="83915-562">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="83915-563">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="83915-563">ViNextGlob</span></span>

<span data-ttu-id="83915-564">移至下一個單字，只使用空白字元做為單字分隔符號。</span><span class="sxs-lookup"><span data-stu-id="83915-564">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="83915-565">Vi 命令模式： `<W>`</span><span class="sxs-lookup"><span data-stu-id="83915-565">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="83915-566">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="83915-566">ViNextWord</span></span>

<span data-ttu-id="83915-567">將游標向前移至下一個單字的開頭。</span><span class="sxs-lookup"><span data-stu-id="83915-567">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="83915-568">單字界限是由一組可設定的字元所定義。</span><span class="sxs-lookup"><span data-stu-id="83915-568">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="83915-569">Vi 命令模式： `<w>`</span><span class="sxs-lookup"><span data-stu-id="83915-569">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="83915-570">歷程記錄函數</span><span class="sxs-lookup"><span data-stu-id="83915-570">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="83915-571">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="83915-571">BeginningOfHistory</span></span>

<span data-ttu-id="83915-572">移至歷程記錄中的第一個專案。</span><span class="sxs-lookup"><span data-stu-id="83915-572">Move to the first item in the history.</span></span>

- <span data-ttu-id="83915-573">Emacs： `<Alt+<>`</span><span class="sxs-lookup"><span data-stu-id="83915-573">Emacs: `<Alt+<>`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="83915-574">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="83915-574">ClearHistory</span></span>

<span data-ttu-id="83915-575">清除 PSReadLine 中的歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="83915-575">Clears history in PSReadLine.</span></span> <span data-ttu-id="83915-576">這不會影響 PowerShell 歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="83915-576">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="83915-577">Cmd： `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="83915-577">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="83915-578">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="83915-578">EndOfHistory</span></span>

<span data-ttu-id="83915-579">移至記錄中目前輸入)  (的最後一個專案。</span><span class="sxs-lookup"><span data-stu-id="83915-579">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="83915-580">Emacs： `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="83915-580">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="83915-581">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="83915-581">ForwardSearchHistory</span></span>

<span data-ttu-id="83915-582">透過歷程記錄執行漸進式向前搜尋。</span><span class="sxs-lookup"><span data-stu-id="83915-582">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="83915-583">Cmd： `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="83915-583">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="83915-584">Emacs： `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="83915-584">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="83915-585">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="83915-585">HistorySearchBackward</span></span>

<span data-ttu-id="83915-586">將目前的輸入取代為 PSReadLine 記錄中與開始和輸入和資料指標之間的字元相符的 ' previous ' 專案。</span><span class="sxs-lookup"><span data-stu-id="83915-586">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="83915-587">Cmd： `<F8>`</span><span class="sxs-lookup"><span data-stu-id="83915-587">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="83915-588">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="83915-588">HistorySearchForward</span></span>

<span data-ttu-id="83915-589">將目前的輸入取代為 PSReadLine 記錄中與開始和輸入和資料指標之間的字元相符的 ' next ' 專案。</span><span class="sxs-lookup"><span data-stu-id="83915-589">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="83915-590">Cmd： `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="83915-590">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="83915-591">NextHistory</span><span class="sxs-lookup"><span data-stu-id="83915-591">NextHistory</span></span>

<span data-ttu-id="83915-592">將目前的輸入取代為 PSReadLine 記錄中的 ' next ' 專案。</span><span class="sxs-lookup"><span data-stu-id="83915-592">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="83915-593">Cmd： `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="83915-593">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="83915-594">Emacs： `<DownArrow>` ， `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="83915-594">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="83915-595">Vi 插入模式： `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="83915-595">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="83915-596">Vi 命令模式： `<DownArrow>` 、 `<j>` 、 `<+>`</span><span class="sxs-lookup"><span data-stu-id="83915-596">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="83915-597">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="83915-597">PreviousHistory</span></span>

<span data-ttu-id="83915-598">將目前的輸入取代為 PSReadLine 記錄中的 ' previous ' 專案。</span><span class="sxs-lookup"><span data-stu-id="83915-598">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="83915-599">Cmd： `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="83915-599">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="83915-600">Emacs： `<UpArrow>` ， `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="83915-600">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="83915-601">Vi 插入模式： `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="83915-601">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="83915-602">Vi 命令模式： `<UpArrow>` 、 `<k>` 、 `<->`</span><span class="sxs-lookup"><span data-stu-id="83915-602">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="83915-603">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="83915-603">ReverseSearchHistory</span></span>

<span data-ttu-id="83915-604">透過歷程記錄執行增量向前搜尋。</span><span class="sxs-lookup"><span data-stu-id="83915-604">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="83915-605">Cmd： `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="83915-605">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="83915-606">Emacs： `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="83915-606">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="83915-607">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="83915-607">ViSearchHistoryBackward</span></span>

<span data-ttu-id="83915-608">提示輸入搜尋字串，並在 AcceptLine 時起始搜尋。</span><span class="sxs-lookup"><span data-stu-id="83915-608">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="83915-609">Vi 插入模式： `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="83915-609">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="83915-610">Vi 命令模式： `</>` 、 `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="83915-610">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="83915-611">完成函式</span><span class="sxs-lookup"><span data-stu-id="83915-611">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="83915-612">完成</span><span class="sxs-lookup"><span data-stu-id="83915-612">Complete</span></span>

<span data-ttu-id="83915-613">嘗試對資料指標周圍的文字執行完成。</span><span class="sxs-lookup"><span data-stu-id="83915-613">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="83915-614">如果有多個可能的完成，則會使用最長的明確前置詞來完成。</span><span class="sxs-lookup"><span data-stu-id="83915-614">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="83915-615">如果嘗試完成最長的明確完成，則會顯示可能的完成清單。</span><span class="sxs-lookup"><span data-stu-id="83915-615">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="83915-616">Emacs： `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="83915-616">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="83915-617">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="83915-617">MenuComplete</span></span>

<span data-ttu-id="83915-618">嘗試對資料指標周圍的文字執行完成。</span><span class="sxs-lookup"><span data-stu-id="83915-618">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="83915-619">如果有多個可能的完成，則會使用最長的明確前置詞來完成。</span><span class="sxs-lookup"><span data-stu-id="83915-619">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="83915-620">如果嘗試完成最長的明確完成，則會顯示可能的完成清單。</span><span class="sxs-lookup"><span data-stu-id="83915-620">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="83915-621">Cmd： `<Ctrl+@>` ， `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="83915-621">Cmd: `<Ctrl+@>`, `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="83915-622">Emacs： `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="83915-622">Emacs: `<Ctrl+Spacebar>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="83915-623">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="83915-623">PossibleCompletions</span></span>

<span data-ttu-id="83915-624">顯示可能的完成清單。</span><span class="sxs-lookup"><span data-stu-id="83915-624">Display the list of possible completions.</span></span>

- <span data-ttu-id="83915-625">Emacs： `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="83915-625">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="83915-626">Vi 插入模式： `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="83915-626">Vi insert mode: `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="83915-627">Vi 命令模式： `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="83915-627">Vi command mode: `<Ctrl+Spacebar>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="83915-628">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="83915-628">TabCompleteNext</span></span>

<span data-ttu-id="83915-629">嘗試使用下一個可用的完成來完成資料指標周圍的文字。</span><span class="sxs-lookup"><span data-stu-id="83915-629">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="83915-630">Cmd： `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="83915-630">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="83915-631">Vi 命令模式： `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="83915-631">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="83915-632">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="83915-632">TabCompletePrevious</span></span>

<span data-ttu-id="83915-633">嘗試使用先前的可用完成來完成資料指標周圍的文字。</span><span class="sxs-lookup"><span data-stu-id="83915-633">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="83915-634">Cmd： `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="83915-634">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="83915-635">Vi 命令模式： `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="83915-635">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="83915-636">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="83915-636">ViTabCompleteNext</span></span>

<span data-ttu-id="83915-637">視需要結束目前的編輯群組，並叫用 TabCompleteNext。</span><span class="sxs-lookup"><span data-stu-id="83915-637">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="83915-638">Vi 插入模式： `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="83915-638">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="83915-639">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="83915-639">ViTabCompletePrevious</span></span>

<span data-ttu-id="83915-640">視需要結束目前的編輯群組，並叫用 TabCompletePrevious。</span><span class="sxs-lookup"><span data-stu-id="83915-640">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="83915-641">Vi 插入模式： `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="83915-641">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="83915-642">其他函式</span><span class="sxs-lookup"><span data-stu-id="83915-642">Miscellaneous functions</span></span>

### <a name="acceptnextsuggestionword"></a><span data-ttu-id="83915-643">AcceptNextSuggestionWord</span><span class="sxs-lookup"><span data-stu-id="83915-643">AcceptNextSuggestionWord</span></span>

<span data-ttu-id="83915-644">接受內嵌或選取建議的下一個字組。</span><span class="sxs-lookup"><span data-stu-id="83915-644">Accept the next word of the inline or selected suggestion.</span></span>

- <span data-ttu-id="83915-645">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="83915-645">Function is unbound.</span></span>

### <a name="acceptsuggestion"></a><span data-ttu-id="83915-646">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="83915-646">AcceptSuggestion</span></span>

<span data-ttu-id="83915-647">接受目前的內嵌或選取的建議。</span><span class="sxs-lookup"><span data-stu-id="83915-647">Accept the current inline or selected suggestion.</span></span>

- <span data-ttu-id="83915-648">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="83915-648">Function is unbound.</span></span>

### <a name="capturescreen"></a><span data-ttu-id="83915-649">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="83915-649">CaptureScreen</span></span>

<span data-ttu-id="83915-650">啟動互動式螢幕擷取畫面-向上/向下箭號選取 [線條]，輸入將選取的文字複製到剪貼簿做為文字和 html。</span><span class="sxs-lookup"><span data-stu-id="83915-650">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="83915-651">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="83915-651">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="83915-652">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="83915-652">ClearScreen</span></span>

<span data-ttu-id="83915-653">清除畫面並在畫面頂端繪製目前的線。</span><span class="sxs-lookup"><span data-stu-id="83915-653">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="83915-654">Cmd： `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="83915-654">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="83915-655">Emacs： `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="83915-655">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="83915-656">Vi 插入模式： `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="83915-656">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="83915-657">Vi 命令模式： `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="83915-657">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="83915-658">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="83915-658">DigitArgument</span></span>

<span data-ttu-id="83915-659">開始新的數位引數以傳遞至其他函式。</span><span class="sxs-lookup"><span data-stu-id="83915-659">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="83915-660">Cmd： `<Alt+0>` 、 `<Alt+1>` 、 `<Alt+2>` 、 `<Alt+3>` 、 `<Alt+4>` 、 `<Alt+5>` 、 `<Alt+6>` `<Alt+7>` `<Alt+8>` `<Alt+9>` 、、、、、 `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="83915-660">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="83915-661">Emacs： `<Alt+0>` 、 `<Alt+1>` 、 `<Alt+2>` 、、、 `<Alt+3>` `<Alt+4>` `<Alt+5>` 、 `<Alt+6>` 、 `<Alt+7>` 、 `<Alt+8>` 、 `<Alt+9>` 、、 `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="83915-661">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="83915-662">Vi 命令模式： `<0>` 、 `<1>` 、 `<2>` 、 `<3>` 、 `<4>` 、 `<5>` 、 `<6>` `<7>` `<8>` 、、、、 `<9>`</span><span class="sxs-lookup"><span data-stu-id="83915-662">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="83915-663">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="83915-663">InvokePrompt</span></span>

<span data-ttu-id="83915-664">清除目前的提示，並呼叫 prompt 函式以重新顯示提示。</span><span class="sxs-lookup"><span data-stu-id="83915-664">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="83915-665">適用于變更狀態的自訂金鑰處理常式，例如變更目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="83915-665">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="83915-666">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="83915-666">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="83915-667">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="83915-667">ScrollDisplayDown</span></span>

<span data-ttu-id="83915-668">將顯示畫面向下移動一個畫面。</span><span class="sxs-lookup"><span data-stu-id="83915-668">Scroll the display down one screen.</span></span>

- <span data-ttu-id="83915-669">Cmd： `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="83915-669">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="83915-670">Emacs： `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="83915-670">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="83915-671">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="83915-671">ScrollDisplayDownLine</span></span>

<span data-ttu-id="83915-672">將向下移動一行。</span><span class="sxs-lookup"><span data-stu-id="83915-672">Scroll the display down one line.</span></span>

- <span data-ttu-id="83915-673">Cmd： `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="83915-673">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="83915-674">Emacs： `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="83915-674">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="83915-675">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="83915-675">ScrollDisplayToCursor</span></span>

<span data-ttu-id="83915-676">將顯示滾動至游標。</span><span class="sxs-lookup"><span data-stu-id="83915-676">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="83915-677">Emacs： `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="83915-677">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="83915-678">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="83915-678">ScrollDisplayTop</span></span>

<span data-ttu-id="83915-679">將顯示器向上方滾動。</span><span class="sxs-lookup"><span data-stu-id="83915-679">Scroll the display to the top.</span></span>

- <span data-ttu-id="83915-680">Emacs： `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="83915-680">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="83915-681">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="83915-681">ScrollDisplayUp</span></span>

<span data-ttu-id="83915-682">將顯示畫面向上移動一次。</span><span class="sxs-lookup"><span data-stu-id="83915-682">Scroll the display up one screen.</span></span>

- <span data-ttu-id="83915-683">Cmd： `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="83915-683">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="83915-684">Emacs： `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="83915-684">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="83915-685">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="83915-685">ScrollDisplayUpLine</span></span>

<span data-ttu-id="83915-686">將顯示畫面向下移動一行。</span><span class="sxs-lookup"><span data-stu-id="83915-686">Scroll the display up one line.</span></span>

- <span data-ttu-id="83915-687">Cmd： `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="83915-687">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="83915-688">Emacs： `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="83915-688">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="83915-689">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="83915-689">SelfInsert</span></span>

<span data-ttu-id="83915-690">插入金鑰。</span><span class="sxs-lookup"><span data-stu-id="83915-690">Insert the key.</span></span>

- <span data-ttu-id="83915-691">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="83915-691">Function is unbound.</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="83915-692">ShowKeyBindings</span><span class="sxs-lookup"><span data-stu-id="83915-692">ShowKeyBindings</span></span>

<span data-ttu-id="83915-693">顯示所有系結的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="83915-693">Show all bound keys.</span></span>

- <span data-ttu-id="83915-694">Cmd： `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="83915-694">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="83915-695">Emacs： `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="83915-695">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="83915-696">Vi 插入模式： `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="83915-696">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="83915-697">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="83915-697">ViCommandMode</span></span>

<span data-ttu-id="83915-698">將目前的作業模式從 Vi-Insert 切換至 Vi 命令。</span><span class="sxs-lookup"><span data-stu-id="83915-698">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="83915-699">Vi 插入模式： `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="83915-699">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="83915-700">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="83915-700">ViDigitArgumentInChord</span></span>

<span data-ttu-id="83915-701">開始新的數位引數，以傳遞至其他函式，而非 vi 的 chords 之一。</span><span class="sxs-lookup"><span data-stu-id="83915-701">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="83915-702">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="83915-702">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="83915-703">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="83915-703">ViEditVisually</span></span>

<span data-ttu-id="83915-704">在 [$env：編輯器] 或 [$env：視覺效果] 所指定的文字編輯器中編輯命令行。</span><span class="sxs-lookup"><span data-stu-id="83915-704">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="83915-705">Emacs： `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="83915-705">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="83915-706">Vi 命令模式： `<v>`</span><span class="sxs-lookup"><span data-stu-id="83915-706">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="83915-707">ViExit</span><span class="sxs-lookup"><span data-stu-id="83915-707">ViExit</span></span>

<span data-ttu-id="83915-708">離開 shell。</span><span class="sxs-lookup"><span data-stu-id="83915-708">Exits the shell.</span></span>

- <span data-ttu-id="83915-709">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="83915-709">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="83915-710">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="83915-710">ViInsertMode</span></span>

<span data-ttu-id="83915-711">切換至插入模式。</span><span class="sxs-lookup"><span data-stu-id="83915-711">Switch to Insert mode.</span></span>

- <span data-ttu-id="83915-712">Vi 命令模式： `<i>`</span><span class="sxs-lookup"><span data-stu-id="83915-712">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="83915-713">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="83915-713">WhatIsKey</span></span>

<span data-ttu-id="83915-714">讀取金鑰，並告訴我金鑰的系結目標。</span><span class="sxs-lookup"><span data-stu-id="83915-714">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="83915-715">Cmd： `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="83915-715">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="83915-716">Emacs： `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="83915-716">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="83915-717">選取函式</span><span class="sxs-lookup"><span data-stu-id="83915-717">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="83915-718">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="83915-718">ExchangePointAndMark</span></span>

<span data-ttu-id="83915-719">游標放在標記的位置，而標記會移至游標位置。</span><span class="sxs-lookup"><span data-stu-id="83915-719">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="83915-720">Emacs： `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="83915-720">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="83915-721">SelectAll</span><span class="sxs-lookup"><span data-stu-id="83915-721">SelectAll</span></span>

<span data-ttu-id="83915-722">選取整行。</span><span class="sxs-lookup"><span data-stu-id="83915-722">Select the entire line.</span></span>

- <span data-ttu-id="83915-723">Cmd： `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="83915-723">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="83915-724">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="83915-724">SelectBackwardChar</span></span>

<span data-ttu-id="83915-725">調整目前的選取範圍，以包含前一個字元。</span><span class="sxs-lookup"><span data-stu-id="83915-725">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="83915-726">Cmd： `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="83915-726">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="83915-727">Emacs： `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="83915-727">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="83915-728">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="83915-728">SelectBackwardsLine</span></span>

<span data-ttu-id="83915-729">調整目前的選取範圍，以包含從游標到行首的起點。</span><span class="sxs-lookup"><span data-stu-id="83915-729">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="83915-730">Cmd： `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="83915-730">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="83915-731">Emacs： `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="83915-731">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="83915-732">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="83915-732">SelectBackwardWord</span></span>

<span data-ttu-id="83915-733">調整目前的選取範圍，以包含前一個字組。</span><span class="sxs-lookup"><span data-stu-id="83915-733">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="83915-734">Cmd： `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="83915-734">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="83915-735">Emacs： `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="83915-735">Emacs: `<Alt+B>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="83915-736">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="83915-736">SelectForwardChar</span></span>

<span data-ttu-id="83915-737">調整目前的選取範圍，以包含下一個字元。</span><span class="sxs-lookup"><span data-stu-id="83915-737">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="83915-738">Cmd： `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="83915-738">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="83915-739">Emacs： `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="83915-739">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="83915-740">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="83915-740">SelectForwardWord</span></span>

<span data-ttu-id="83915-741">使用 ForwardWord 調整目前的選取範圍，以包含下一個字組。</span><span class="sxs-lookup"><span data-stu-id="83915-741">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="83915-742">Emacs： `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="83915-742">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="83915-743">SelectLine</span><span class="sxs-lookup"><span data-stu-id="83915-743">SelectLine</span></span>

<span data-ttu-id="83915-744">調整目前的選取範圍，以包含從游標到行尾。</span><span class="sxs-lookup"><span data-stu-id="83915-744">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="83915-745">Cmd： `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="83915-745">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="83915-746">Emacs： `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="83915-746">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="83915-747">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="83915-747">SelectNextWord</span></span>

<span data-ttu-id="83915-748">調整目前的選取範圍，以包含下一個字組。</span><span class="sxs-lookup"><span data-stu-id="83915-748">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="83915-749">Cmd： `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="83915-749">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="83915-750">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="83915-750">SelectShellBackwardWord</span></span>

<span data-ttu-id="83915-751">使用 ShellBackwardWord 調整目前的選取範圍，以包含前一個字組。</span><span class="sxs-lookup"><span data-stu-id="83915-751">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="83915-752">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="83915-752">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="83915-753">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="83915-753">SelectShellForwardWord</span></span>

<span data-ttu-id="83915-754">使用 ShellForwardWord 調整目前的選取範圍，以包含下一個字組。</span><span class="sxs-lookup"><span data-stu-id="83915-754">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="83915-755">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="83915-755">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="83915-756">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="83915-756">SelectShellNextWord</span></span>

<span data-ttu-id="83915-757">使用 ShellNextWord 調整目前的選取範圍，以包含下一個字組。</span><span class="sxs-lookup"><span data-stu-id="83915-757">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="83915-758">函數已解除系結。</span><span class="sxs-lookup"><span data-stu-id="83915-758">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="83915-759">SetMark</span><span class="sxs-lookup"><span data-stu-id="83915-759">SetMark</span></span>

<span data-ttu-id="83915-760">標記目前的資料指標位置，以用於後續的編輯命令。</span><span class="sxs-lookup"><span data-stu-id="83915-760">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="83915-761">Emacs： `<Ctrl+@>`</span><span class="sxs-lookup"><span data-stu-id="83915-761">Emacs: `<Ctrl+@>`</span></span>

## <a name="predictive-intellisense-functions"></a><span data-ttu-id="83915-762">預測性 IntelliSense 函數</span><span class="sxs-lookup"><span data-stu-id="83915-762">Predictive IntelliSense functions</span></span>

> [!NOTE]
> <span data-ttu-id="83915-763">必須啟用預測性 IntelliSense 才能使用這些函數。</span><span class="sxs-lookup"><span data-stu-id="83915-763">Predictive IntelliSense needs to be enabled to use these functions.</span></span>

### <a name="acceptnextwordsuggestion"></a><span data-ttu-id="83915-764">AcceptNextWordSuggestion</span><span class="sxs-lookup"><span data-stu-id="83915-764">AcceptNextWordSuggestion</span></span>

<span data-ttu-id="83915-765">接受預測性 IntelliSense 中的下一個字組內嵌建議。</span><span class="sxs-lookup"><span data-stu-id="83915-765">Accepts the next word of the inline suggestion from Predictive IntelliSense.</span></span>
<span data-ttu-id="83915-766">您可以藉由執行下列命令，使用<kbd>Ctrl</kbd>F 來系結此函數 + <kbd></kbd> 。</span><span class="sxs-lookup"><span data-stu-id="83915-766">This function can be bound with <kbd>Ctrl</kbd>+<kbd>F</kbd> by running the following command.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord "Ctrl+f" -Function ForwardWord
```

### <a name="acceptsuggestion"></a><span data-ttu-id="83915-767">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="83915-767">AcceptSuggestion</span></span>

<span data-ttu-id="83915-768">當游標位於目前行的結尾時，藉由按下 <kbd>向右鍵</kbd> ，接受預測性 IntelliSense 的目前內嵌建議。</span><span class="sxs-lookup"><span data-stu-id="83915-768">Accepts the current inline suggestion from Predictive IntelliSense by pressing <kbd>RightArrow</kbd> when the cursor is at the end of the current line.</span></span>

## <a name="search-functions"></a><span data-ttu-id="83915-769">搜尋函數</span><span class="sxs-lookup"><span data-stu-id="83915-769">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="83915-770">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="83915-770">CharacterSearch</span></span>

<span data-ttu-id="83915-771">讀取字元，並向前搜尋該字元的下一個出現位置。</span><span class="sxs-lookup"><span data-stu-id="83915-771">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="83915-772">如果指定了引數，則在第 n 次發生) 時，向前搜尋 (或向後搜尋。</span><span class="sxs-lookup"><span data-stu-id="83915-772">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="83915-773">Cmd： `<F3>`</span><span class="sxs-lookup"><span data-stu-id="83915-773">Cmd: `<F3>`</span></span>
- <span data-ttu-id="83915-774">Emacs： `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="83915-774">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="83915-775">Vi 插入模式： `<F3>`</span><span class="sxs-lookup"><span data-stu-id="83915-775">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="83915-776">Vi 命令模式： `<F3>`</span><span class="sxs-lookup"><span data-stu-id="83915-776">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="83915-777">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="83915-777">CharacterSearchBackward</span></span>

<span data-ttu-id="83915-778">讀取字元，並向後搜尋該字元的下一個出現位置。</span><span class="sxs-lookup"><span data-stu-id="83915-778">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="83915-779">如果指定了引數，則會在第 n 次出現) 時向後 (或向前搜尋。</span><span class="sxs-lookup"><span data-stu-id="83915-779">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="83915-780">Cmd： `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="83915-780">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="83915-781">Emacs： `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="83915-781">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="83915-782">Vi 插入模式： `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="83915-782">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="83915-783">Vi 命令模式： `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="83915-783">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="83915-784">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="83915-784">RepeatLastCharSearch</span></span>

<span data-ttu-id="83915-785">重複上次錄製的字元搜尋。</span><span class="sxs-lookup"><span data-stu-id="83915-785">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="83915-786">Vi 命令模式： `<;>`</span><span class="sxs-lookup"><span data-stu-id="83915-786">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="83915-787">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="83915-787">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="83915-788">重複上次錄製的字元搜尋，但方向相反。</span><span class="sxs-lookup"><span data-stu-id="83915-788">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="83915-789">Vi 命令模式： `<,>`</span><span class="sxs-lookup"><span data-stu-id="83915-789">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="83915-790">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="83915-790">RepeatSearch</span></span>

<span data-ttu-id="83915-791">以與之前相同的方向重複最後一個搜尋。</span><span class="sxs-lookup"><span data-stu-id="83915-791">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="83915-792">Vi 命令模式： `<n>`</span><span class="sxs-lookup"><span data-stu-id="83915-792">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="83915-793">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="83915-793">RepeatSearchBackward</span></span>

<span data-ttu-id="83915-794">以與之前相同的方向重複最後一個搜尋。</span><span class="sxs-lookup"><span data-stu-id="83915-794">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="83915-795">Vi 命令模式： `<N>`</span><span class="sxs-lookup"><span data-stu-id="83915-795">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="83915-796">SearchChar</span><span class="sxs-lookup"><span data-stu-id="83915-796">SearchChar</span></span>

<span data-ttu-id="83915-797">讀取下一個字元，然後找出該字元，再繼續進行，然後再移出一個字元。</span><span class="sxs-lookup"><span data-stu-id="83915-797">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="83915-798">這是「t」功能。</span><span class="sxs-lookup"><span data-stu-id="83915-798">This is for 't' functionality.</span></span>

- <span data-ttu-id="83915-799">Vi 命令模式： `<f>`</span><span class="sxs-lookup"><span data-stu-id="83915-799">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="83915-800">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="83915-800">SearchCharBackward</span></span>

<span data-ttu-id="83915-801">讀取下一個字元，然後找出它，然後再向後移一字元。</span><span class="sxs-lookup"><span data-stu-id="83915-801">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="83915-802">這是「t」功能。</span><span class="sxs-lookup"><span data-stu-id="83915-802">This is for 'T' functionality.</span></span>

- <span data-ttu-id="83915-803">Vi 命令模式： `<F>`</span><span class="sxs-lookup"><span data-stu-id="83915-803">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="83915-804">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="83915-804">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="83915-805">讀取下一個字元，然後找出它，然後再向後移一字元。</span><span class="sxs-lookup"><span data-stu-id="83915-805">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="83915-806">這是「t」功能。</span><span class="sxs-lookup"><span data-stu-id="83915-806">This is for 'T' functionality.</span></span>

- <span data-ttu-id="83915-807">Vi 命令模式： `<T>`</span><span class="sxs-lookup"><span data-stu-id="83915-807">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="83915-808">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="83915-808">SearchCharWithBackoff</span></span>

<span data-ttu-id="83915-809">讀取下一個字元，然後找出該字元，再繼續進行，然後再移出一個字元。</span><span class="sxs-lookup"><span data-stu-id="83915-809">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="83915-810">這是「t」功能。</span><span class="sxs-lookup"><span data-stu-id="83915-810">This is for 't' functionality.</span></span>

- <span data-ttu-id="83915-811">Vi 命令模式： `<t>`</span><span class="sxs-lookup"><span data-stu-id="83915-811">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="83915-812">SearchForward</span><span class="sxs-lookup"><span data-stu-id="83915-812">SearchForward</span></span>

<span data-ttu-id="83915-813">提示輸入搜尋字串，並在 AcceptLine 時起始搜尋。</span><span class="sxs-lookup"><span data-stu-id="83915-813">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="83915-814">Vi 插入模式： `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="83915-814">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="83915-815">Vi 命令模式： `<?>` 、 `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="83915-815">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="83915-816">自訂索引鍵系結</span><span class="sxs-lookup"><span data-stu-id="83915-816">Custom Key Bindings</span></span>

<span data-ttu-id="83915-817">PSReadLine 支援使用 Cmdlet 的自訂金鑰系結 `Set-PSReadLineKeyHandler` 。</span><span class="sxs-lookup"><span data-stu-id="83915-817">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="83915-818">大部分的自訂按鍵系結都會呼叫上述其中一項功能，例如</span><span class="sxs-lookup"><span data-stu-id="83915-818">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="83915-819">您可以將 ScriptBlock 系結至索引鍵。</span><span class="sxs-lookup"><span data-stu-id="83915-819">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="83915-820">ScriptBlock 可以進行任何您想要的動作。</span><span class="sxs-lookup"><span data-stu-id="83915-820">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="83915-821">一些實用的範例包括</span><span class="sxs-lookup"><span data-stu-id="83915-821">Some useful examples include</span></span>

- <span data-ttu-id="83915-822">編輯命令行</span><span class="sxs-lookup"><span data-stu-id="83915-822">edit the command line</span></span>
- <span data-ttu-id="83915-823">開啟新視窗 (例如說明) </span><span class="sxs-lookup"><span data-stu-id="83915-823">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="83915-824">變更目錄而不變更命令列</span><span class="sxs-lookup"><span data-stu-id="83915-824">change directories without changing the command line</span></span>

<span data-ttu-id="83915-825">ScriptBlock 會收到兩個引數：</span><span class="sxs-lookup"><span data-stu-id="83915-825">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="83915-826">`$key` -A **[ConsoleKeyInfo]** 物件，它是觸發自訂系結的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="83915-826">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="83915-827">如果您將相同的 ScriptBlock 系結至多個金鑰，且需要根據金鑰執行不同的動作，您可以檢查 $key。</span><span class="sxs-lookup"><span data-stu-id="83915-827">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="83915-828">許多自訂系結會忽略此引數。</span><span class="sxs-lookup"><span data-stu-id="83915-828">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="83915-829">`$arg` -任意引數。</span><span class="sxs-lookup"><span data-stu-id="83915-829">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="83915-830">通常，這會是使用者從索引鍵系結 DigitArgument 傳遞的整數引數。</span><span class="sxs-lookup"><span data-stu-id="83915-830">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="83915-831">如果您的系結不接受引數，則可以合理地忽略此引數。</span><span class="sxs-lookup"><span data-stu-id="83915-831">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="83915-832">讓我們看看將命令列新增至歷程記錄，而不執行的範例。</span><span class="sxs-lookup"><span data-stu-id="83915-832">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="83915-833">當您知道您忘了進行某個動作，但不想重新輸入您已經輸入的命令列時，這會很有用。</span><span class="sxs-lookup"><span data-stu-id="83915-833">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

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

<span data-ttu-id="83915-834">您可以在檔案中看到許多在 `SamplePSReadLineProfile.ps1` PSReadLine 模組資料夾中安裝的範例。</span><span class="sxs-lookup"><span data-stu-id="83915-834">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="83915-835">大部分的按鍵系結都會使用一些 helper 函數來編輯命令行。</span><span class="sxs-lookup"><span data-stu-id="83915-835">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="83915-836">這些 Api 記載于下一節。</span><span class="sxs-lookup"><span data-stu-id="83915-836">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="83915-837">自訂金鑰系結支援 Api</span><span class="sxs-lookup"><span data-stu-id="83915-837">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="83915-838">下列函式在 PSConsoleReadLine 中是公用的，但不能直接系結至索引鍵。</span><span class="sxs-lookup"><span data-stu-id="83915-838">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="83915-839">大部分在自訂金鑰系結中都很有用。</span><span class="sxs-lookup"><span data-stu-id="83915-839">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="83915-840">將命令列新增至歷程記錄，而不加以執行。</span><span class="sxs-lookup"><span data-stu-id="83915-840">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="83915-841">清除終止環形。</span><span class="sxs-lookup"><span data-stu-id="83915-841">Clear the kill-ring.</span></span>  <span data-ttu-id="83915-842">這大多用於測試。</span><span class="sxs-lookup"><span data-stu-id="83915-842">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="83915-843">從開始刪除長度字元。</span><span class="sxs-lookup"><span data-stu-id="83915-843">Delete length characters from start.</span></span>  <span data-ttu-id="83915-844">這種作業支援復原/重做。</span><span class="sxs-lookup"><span data-stu-id="83915-844">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="83915-845">根據使用者喜好設定來執行 Ding 動作。</span><span class="sxs-lookup"><span data-stu-id="83915-845">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="83915-846">這兩個函式會取出輸入緩衝區目前狀態的相關實用資訊。</span><span class="sxs-lookup"><span data-stu-id="83915-846">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="83915-847">第一個較常用於簡單的案例。</span><span class="sxs-lookup"><span data-stu-id="83915-847">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="83915-848">如果您的系結使用 Ast 更先進地執行，則會使用第二個。</span><span class="sxs-lookup"><span data-stu-id="83915-848">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(string[] Chord)
```

<span data-ttu-id="83915-849">這兩個函數是由所使用 `Get-PSReadLineKeyHandler` 。</span><span class="sxs-lookup"><span data-stu-id="83915-849">These two functions are used by `Get-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="83915-850">第一個用來取得所有按鍵系結。</span><span class="sxs-lookup"><span data-stu-id="83915-850">The first is used to get all key bindings.</span></span> <span data-ttu-id="83915-851">第二個是用來取得特定的索引鍵系結。</span><span class="sxs-lookup"><span data-stu-id="83915-851">The second is used to get specific key bindings.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="83915-852">Get-PSReadLineOption 使用這個函式，而且在自訂索引鍵系結中可能不太實用。</span><span class="sxs-lookup"><span data-stu-id="83915-852">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="83915-853">如果未在命令列上選取任何專案，則會以開始和長度傳回-1。</span><span class="sxs-lookup"><span data-stu-id="83915-853">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="83915-854">如果在命令列上有選取專案，則會傳回選取範圍的開始和長度。</span><span class="sxs-lookup"><span data-stu-id="83915-854">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="83915-855">在游標處插入字元或字串。</span><span class="sxs-lookup"><span data-stu-id="83915-855">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="83915-856">這種作業支援復原/重做。</span><span class="sxs-lookup"><span data-stu-id="83915-856">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="83915-857">這是要 PSReadLine 的主要進入點。</span><span class="sxs-lookup"><span data-stu-id="83915-857">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="83915-858">它不支援遞迴，因此在自訂索引鍵系結中並不有用。</span><span class="sxs-lookup"><span data-stu-id="83915-858">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="83915-859">Remove-PSReadLineKeyHandler 使用這個函式，而且在自訂索引鍵系結中可能不太實用。</span><span class="sxs-lookup"><span data-stu-id="83915-859">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="83915-860">取代部分輸入。</span><span class="sxs-lookup"><span data-stu-id="83915-860">Replace some of the input.</span></span> <span data-ttu-id="83915-861">這種作業支援復原/重做。</span><span class="sxs-lookup"><span data-stu-id="83915-861">This operation supports undo/redo.</span></span> <span data-ttu-id="83915-862">這是優先于 Delete，後面接著 Insert，因為它會被視為復原的單一動作。</span><span class="sxs-lookup"><span data-stu-id="83915-862">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="83915-863">將游標移至指定的位移。</span><span class="sxs-lookup"><span data-stu-id="83915-863">Move the cursor to the given offset.</span></span> <span data-ttu-id="83915-864">不追蹤資料指標移動以進行復原。</span><span class="sxs-lookup"><span data-stu-id="83915-864">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="83915-865">此函式是 Cmdlet PSReadLineOption 所使用的 helper 方法，但對於想要暫時變更設定的自訂按鍵系結來說可能很有用。</span><span class="sxs-lookup"><span data-stu-id="83915-865">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="83915-866">此 helper 方法是用於接受 DigitArgument 的自訂系結。</span><span class="sxs-lookup"><span data-stu-id="83915-866">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="83915-867">一般呼叫看起來像</span><span class="sxs-lookup"><span data-stu-id="83915-867">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="note"></a><span data-ttu-id="83915-868">注意</span><span class="sxs-lookup"><span data-stu-id="83915-868">Note</span></span>

### <a name="command-history"></a><span data-ttu-id="83915-869">命令歷程記錄</span><span class="sxs-lookup"><span data-stu-id="83915-869">Command History</span></span>

<span data-ttu-id="83915-870">PSReadLine 會維護一個記錄檔，其中包含您從命令列輸入的所有命令和資料。</span><span class="sxs-lookup"><span data-stu-id="83915-870">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="83915-871">這可能包含機密資料，包括密碼。</span><span class="sxs-lookup"><span data-stu-id="83915-871">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="83915-872">例如，如果您使用指令 `ConvertTo-SecureString` 程式，密碼就會以純文字的形式記錄在記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="83915-872">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="83915-873">記錄檔是名為的檔案 `$($host.Name)_history.txt` 。</span><span class="sxs-lookup"><span data-stu-id="83915-873">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="83915-874">在 Windows 系統上，歷程記錄檔案會儲存在中 `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` 。</span><span class="sxs-lookup"><span data-stu-id="83915-874">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span> <span data-ttu-id="83915-875">在非 Windows 系統上，記錄檔會儲存在 `$env:XDG_DATA_HOME/powershell/PSReadLine` 或 `$env:HOME/.local/share/powershell/PSReadLine` 。</span><span class="sxs-lookup"><span data-stu-id="83915-875">On non-Windows systems, the history files is stored at `$env:XDG_DATA_HOME/powershell/PSReadLine` or `$env:HOME/.local/share/powershell/PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="83915-876">意見反應 & 參與 PSReadLine</span><span class="sxs-lookup"><span data-stu-id="83915-876">Feedback & Contributing To PSReadLine</span></span>

[<span data-ttu-id="83915-877">GitHub 上的 PSReadLine</span><span class="sxs-lookup"><span data-stu-id="83915-877">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="83915-878">您可以隨時提交提取要求或在 GitHub 頁面上提交意見反應。</span><span class="sxs-lookup"><span data-stu-id="83915-878">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="83915-879">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83915-879">See Also</span></span>

<span data-ttu-id="83915-880">PSReadLine 會受到 GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) 程式庫的高度影響。</span><span class="sxs-lookup"><span data-stu-id="83915-880">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>
