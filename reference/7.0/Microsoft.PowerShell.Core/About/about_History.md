---
description: 描述如何在命令歷程記錄中取得和執行命令。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_history?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_History
ms.openlocfilehash: b9e8ab09553f8cd6452f4a891ecbaa1b914af895
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207419"
---
# <a name="about-history"></a><span data-ttu-id="a8623-104">關於歷程記錄</span><span class="sxs-lookup"><span data-stu-id="a8623-104">About History</span></span>

## <a name="short-description"></a><span data-ttu-id="a8623-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="a8623-105">Short Description</span></span>
<span data-ttu-id="a8623-106">描述如何在命令歷程記錄中取得和執行命令。</span><span class="sxs-lookup"><span data-stu-id="a8623-106">Describes how to get and run commands in the command history.</span></span>

## <a name="long-description"></a><span data-ttu-id="a8623-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="a8623-107">Long Description</span></span>

<span data-ttu-id="a8623-108">當您在命令提示字元中輸入命令時，PowerShell 會將命令儲存在命令歷程記錄中。</span><span class="sxs-lookup"><span data-stu-id="a8623-108">When you enter a command at the command prompt, PowerShell saves the command in the command history.</span></span> <span data-ttu-id="a8623-109">您可以使用歷程記錄中的命令作為工作的記錄。</span><span class="sxs-lookup"><span data-stu-id="a8623-109">You can use the commands in the history as a record of your work.</span></span> <span data-ttu-id="a8623-110">而且，您可以從命令歷程記錄中重新叫用和執行命令。</span><span class="sxs-lookup"><span data-stu-id="a8623-110">And, you can recall and run the commands from the command history.</span></span>

<span data-ttu-id="a8623-111">PowerShell 有兩種不同的歷程記錄提供者：內建的歷程記錄，以及由 **PSReadLine** 模組管理的歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="a8623-111">PowerShell has two different history providers: the built-in history and the history managed by the **PSReadLine** module.</span></span> <span data-ttu-id="a8623-112">歷程記錄是分開管理的，但這兩個歷程記錄都可以在載入 **PSReadLine** 的會話中使用。</span><span class="sxs-lookup"><span data-stu-id="a8623-112">The histories are managed separately, but both histories are available in sessions where **PSReadLine** is loaded.</span></span>

## <a name="using-the-psreadline-history"></a><span data-ttu-id="a8623-113">使用 PSReadLine 歷程記錄</span><span class="sxs-lookup"><span data-stu-id="a8623-113">Using the PSReadLine history</span></span>

<span data-ttu-id="a8623-114">PSReadLine 歷程記錄會追蹤所有 PowerShell 會話中使用的命令。</span><span class="sxs-lookup"><span data-stu-id="a8623-114">The PSReadLine history tracks the commands used in all PowerShell sessions.</span></span>
<span data-ttu-id="a8623-115">歷程記錄會寫入每個主機的中央檔案。</span><span class="sxs-lookup"><span data-stu-id="a8623-115">The history is written to a central file per host.</span></span> <span data-ttu-id="a8623-116">該記錄檔可供所有會話使用，並包含過去所有的歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="a8623-116">That history file is available to all sessions and contains all past history.</span></span> <span data-ttu-id="a8623-117">當會話結束時，不會刪除歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="a8623-117">The history is not deleted when the session ends.</span></span> <span data-ttu-id="a8623-118">此外，該歷程記錄無法由 Cmdlet 管理 `*-History` 。</span><span class="sxs-lookup"><span data-stu-id="a8623-118">Also, that history cannot be managed by the `*-History` cmdlets.</span></span> <span data-ttu-id="a8623-119">如需詳細資訊，請參閱 [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md)。</span><span class="sxs-lookup"><span data-stu-id="a8623-119">For more information, see [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md).</span></span>

## <a name="using-the-built-in-session-history"></a><span data-ttu-id="a8623-120">使用內建的會話歷程記錄</span><span class="sxs-lookup"><span data-stu-id="a8623-120">Using the built-in session history</span></span>

<span data-ttu-id="a8623-121">內建記錄只會追蹤目前會話中使用的命令。</span><span class="sxs-lookup"><span data-stu-id="a8623-121">The built-in history only tracks the commands used in the current session.</span></span> <span data-ttu-id="a8623-122">歷程記錄無法供其他會話使用，且會在會話結束時刪除。</span><span class="sxs-lookup"><span data-stu-id="a8623-122">The history is not available to other sessions and is deleted when the session ends.</span></span>

### <a name="history-cmdlets"></a><span data-ttu-id="a8623-123">歷程記錄 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a8623-123">History Cmdlets</span></span>

<span data-ttu-id="a8623-124">PowerShell 有一組 Cmdlet，可管理命令歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="a8623-124">PowerShell has a set of cmdlets that manage the command history.</span></span>

| <span data-ttu-id="a8623-125">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a8623-125">Cmdlet</span></span>           | <span data-ttu-id="a8623-126">Alias</span><span class="sxs-lookup"><span data-stu-id="a8623-126">Alias</span></span>  | <span data-ttu-id="a8623-127">Description</span><span class="sxs-lookup"><span data-stu-id="a8623-127">Description</span></span>                                |
| ---------------- | ------ | ------------------------------------------ |
| `Get-History`    | `h`    | <span data-ttu-id="a8623-128">取得命令歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="a8623-128">Gets the command history.</span></span>                  |
| `Invoke-History` | `r`    | <span data-ttu-id="a8623-129">在命令歷程記錄中執行命令。</span><span class="sxs-lookup"><span data-stu-id="a8623-129">Runs a command in the command history.</span></span>     |
| `Add-History`    |        | <span data-ttu-id="a8623-130">將命令加入至命令歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="a8623-130">Adds a command to the command history.</span></span>     |
| `Clear-History`  | `clhy` | <span data-ttu-id="a8623-131">從命令歷程記錄中刪除命令。</span><span class="sxs-lookup"><span data-stu-id="a8623-131">Deletes commands from the command history.</span></span> |

### <a name="keyboard-shortcuts-for-managing-history"></a><span data-ttu-id="a8623-132">管理歷程記錄的鍵盤快速鍵</span><span class="sxs-lookup"><span data-stu-id="a8623-132">Keyboard Shortcuts for Managing History</span></span>

<span data-ttu-id="a8623-133">在 PowerShell 主控台中，您可以使用下列快速鍵來管理命令歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="a8623-133">In the PowerShell console, you can use the following shortcuts to manage the command history.</span></span>

- <span data-ttu-id="a8623-134"><kbd>UpArrow</kbd> -顯示上一個命令。</span><span class="sxs-lookup"><span data-stu-id="a8623-134"><kbd>UpArrow</kbd> - Displays the previous command.</span></span>
- <span data-ttu-id="a8623-135"><kbd>Download-downarrow-circled</kbd> -顯示下一個命令。</span><span class="sxs-lookup"><span data-stu-id="a8623-135"><kbd>DownArrow</kbd> - Displays the next command.</span></span>
- <span data-ttu-id="a8623-136"><kbd>F7</kbd> -顯示命令歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="a8623-136"><kbd>F7</kbd> - Displays the command history.</span></span>
- <span data-ttu-id="a8623-137"><kbd>ESC</kbd> -隱藏曆程記錄。</span><span class="sxs-lookup"><span data-stu-id="a8623-137"><kbd>ESC</kbd> - To hide the history.</span></span>
- <span data-ttu-id="a8623-138"><kbd>F8</kbd> -尋找命令。</span><span class="sxs-lookup"><span data-stu-id="a8623-138"><kbd>F8</kbd> - Finds a command.</span></span> <span data-ttu-id="a8623-139">輸入一或多個字元，然後按 <kbd>F8</kbd>。</span><span class="sxs-lookup"><span data-stu-id="a8623-139">Type one or more characters then press <kbd>F8</kbd>.</span></span> <span data-ttu-id="a8623-140">再按一次 <kbd>F8</kbd> 下一個實例。</span><span class="sxs-lookup"><span data-stu-id="a8623-140">Press <kbd>F8</kbd> again the next instance.</span></span>
- <span data-ttu-id="a8623-141"><kbd>F9</kbd> -依歷程記錄識別碼尋找命令。</span><span class="sxs-lookup"><span data-stu-id="a8623-141"><kbd>F9</kbd> - Find a command by history ID.</span></span> <span data-ttu-id="a8623-142">輸入歷程記錄識別碼，然後按 <kbd>F9</kbd>。</span><span class="sxs-lookup"><span data-stu-id="a8623-142">Type the history ID then press <kbd>F9</kbd>.</span></span> <span data-ttu-id="a8623-143">按 <kbd>F7</kbd> 以尋找識別碼。</span><span class="sxs-lookup"><span data-stu-id="a8623-143">Press <kbd>F7</kbd> to find the ID.</span></span>
- <span data-ttu-id="a8623-144"><kbd>#</kbd>`<string>`</kbd><kbd>Tab</kbd> -搜尋的歷程記錄 `*<string>*` ，並傳回最新的相符項。</span><span class="sxs-lookup"><span data-stu-id="a8623-144"><kbd>#</kbd>`<string>`</kbd><kbd>Tab</kbd> - Search the history for `*<string>*` and returns the most recent match.</span></span> <span data-ttu-id="a8623-145">如果您重複按下 <kbd>tab</kbd> 鍵，它會迴圈顯示歷程記錄中相符的專案。</span><span class="sxs-lookup"><span data-stu-id="a8623-145">If you press <kbd>Tab</kbd> repeatedly, it cycles through the matching items in your history.</span></span>

> [!NOTE]
> <span data-ttu-id="a8623-146">這些按鍵系結是由主控台主機應用程式所執行。</span><span class="sxs-lookup"><span data-stu-id="a8623-146">These key bindings are implemented by the console host application.</span></span> <span data-ttu-id="a8623-147">其他應用程式（例如 Visual Studio Code 或 Windows 終端機）可以有不同的索引鍵系結。</span><span class="sxs-lookup"><span data-stu-id="a8623-147">Other applications, such as Visual Studio Code or Windows Terminal, can have different key bindings.</span></span> <span data-ttu-id="a8623-148">PSReadLine 模組可以覆寫系結。</span><span class="sxs-lookup"><span data-stu-id="a8623-148">The bindings can be overridden by the PSReadLine module.</span></span> <span data-ttu-id="a8623-149">PSReadLine 會在您啟動 PowerShell 會話時自動載入。</span><span class="sxs-lookup"><span data-stu-id="a8623-149">PSReadLine loads automatically when you start a PowerShell session.</span></span>
> <span data-ttu-id="a8623-150">載入 PSReadLine 後， <kbd>F7</kbd> 和 <kbd>F9</kbd> 不會系結至任何函數。</span><span class="sxs-lookup"><span data-stu-id="a8623-150">With PSReadLine loaded, <kbd>F7</kbd> and <kbd>F9</kbd> are not bound to any function.</span></span> <span data-ttu-id="a8623-151">PSReadLine 不會提供對等的功能。</span><span class="sxs-lookup"><span data-stu-id="a8623-151">PSReadLine does not provide equivalent functionality.</span></span> <span data-ttu-id="a8623-152">如需詳細資訊，請參閱 [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md)。</span><span class="sxs-lookup"><span data-stu-id="a8623-152">For more information, see [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md).</span></span>

### <a name="maximumhistorycount"></a><span data-ttu-id="a8623-153">MaximumHistoryCount</span><span class="sxs-lookup"><span data-stu-id="a8623-153">MaximumHistoryCount</span></span>

<span data-ttu-id="a8623-154">`$MaximumHistoryCount`喜好設定變數會決定 PowerShell 在命令歷程記錄中儲存的命令數目上限。</span><span class="sxs-lookup"><span data-stu-id="a8623-154">The `$MaximumHistoryCount` preference variable determines the maximum number of commands that PowerShell saves in the command history.</span></span> <span data-ttu-id="a8623-155">預設值為</span><span class="sxs-lookup"><span data-stu-id="a8623-155">The default value is</span></span>
4096.

<span data-ttu-id="a8623-156">例如，下列命令會減少 `$MaximumHistoryCount` 到100命令：</span><span class="sxs-lookup"><span data-stu-id="a8623-156">For example, the following command lowers the `$MaximumHistoryCount` to 100 commands:</span></span>

```powershell
$MaximumHistoryCount = 100
```

<span data-ttu-id="a8623-157">若要套用此設定，請重新開機 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="a8623-157">To apply the setting, restart PowerShell.</span></span>

<span data-ttu-id="a8623-158">若要為您所有的 PowerShell 會話儲存新的變數值，請將指派語句新增至 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="a8623-158">To save the new variable value for all your PowerShell sessions, add the assignment statement to a PowerShell profile.</span></span> <span data-ttu-id="a8623-159">如需設定檔的詳細資訊，請參閱 [about_Profiles](about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="a8623-159">For more information about profiles, see [about_Profiles](about_Profiles.md).</span></span>

<span data-ttu-id="a8623-160">如需喜好設定變數的詳細資訊 `$MaximumHistoryCount` ，請參閱 [about_Preference_Variables](about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="a8623-160">For more information about the `$MaximumHistoryCount` preference variable, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

### <a name="order-of-commands-in-the-history"></a><span data-ttu-id="a8623-161">記錄中的命令順序</span><span class="sxs-lookup"><span data-stu-id="a8623-161">Order of Commands in the History</span></span>

<span data-ttu-id="a8623-162">當命令執行完成時，不會將命令新增至歷程記錄，而不是在輸入命令時。</span><span class="sxs-lookup"><span data-stu-id="a8623-162">Commands are added to the history when the command finishes executing, not when the command is entered.</span></span> <span data-ttu-id="a8623-163">如果命令需要一些時間才能完成，或命令以嵌套提示執行，命令在歷程記錄中可能看起來不是順序。</span><span class="sxs-lookup"><span data-stu-id="a8623-163">If commands take some time to be completed, or if the commands are executing in a nested prompt, the commands might appear to be out of order in the history.</span></span> <span data-ttu-id="a8623-164">只有當您離開提示層級時，才會完成以嵌套提示字元執行的命令。</span><span class="sxs-lookup"><span data-stu-id="a8623-164">Commands that are executing in a nested prompt are completed only when you exit the prompt level.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8623-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8623-165">See Also</span></span>

- [<span data-ttu-id="a8623-166">about_Line_Editing</span><span class="sxs-lookup"><span data-stu-id="a8623-166">about_Line_Editing</span></span>](about_Line_Editing.md)
- [<span data-ttu-id="a8623-167">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="a8623-167">about_Preference_Variables</span></span>](about_Preference_Variables.md)
- [<span data-ttu-id="a8623-168">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="a8623-168">about_Profiles</span></span>](about_Profiles.md)
- [<span data-ttu-id="a8623-169">about_Variables</span><span class="sxs-lookup"><span data-stu-id="a8623-169">about_Variables</span></span>](about_Variables.md)
- [<span data-ttu-id="a8623-170">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="a8623-170">about_PSReadLine</span></span>](../../PSReadLine/About/about_PSReadLine.md)
