---
title: 如何在 Visual Studio Code 中複寫 ISE 體驗
description: 如何在 Visual Studio Code 中複寫 ISE 體驗
ms.date: 08/06/2018
ms.openlocfilehash: 983da850c13d72bcdc7b2d33970c6e9e06b3d869
ms.sourcegitcommit: 9df29dfc637191b62ca591893c251c1e02d4eb4c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2019
ms.locfileid: "54012478"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="40e09-103">如何在 Visual Studio Code 中複寫 ISE 體驗</span><span class="sxs-lookup"><span data-stu-id="40e09-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="40e09-104">雖然 VSCode 的 PowerShell 延伸模組不會尋找完整的功能同位檢查，以 PowerShell ISE 功能中有地方，VSCode 體驗更自然的 ISE 使用者。</span><span class="sxs-lookup"><span data-stu-id="40e09-104">While the PowerShell extension for VSCode doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VSCode experience more natural for users of the ISE.</span></span>

<span data-ttu-id="40e09-105">這份文件會嘗試在 VSCode，若要讓使用者體驗更熟悉相較於 ISE 中，您可以設定的清單設定。</span><span class="sxs-lookup"><span data-stu-id="40e09-105">This document tries to list settings you can configure in VSCode to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="key-bindings"></a><span data-ttu-id="40e09-106">按鍵繫結</span><span class="sxs-lookup"><span data-stu-id="40e09-106">Key bindings</span></span>

| <span data-ttu-id="40e09-107">函式</span><span class="sxs-lookup"><span data-stu-id="40e09-107">Function</span></span>                              | <span data-ttu-id="40e09-108">ISE 繫結</span><span class="sxs-lookup"><span data-stu-id="40e09-108">ISE Binding</span></span>                  | <span data-ttu-id="40e09-109">VSCode 繫結</span><span class="sxs-lookup"><span data-stu-id="40e09-109">VSCode Binding</span></span>                              |
| ----------------                      | -----------                  | --------------                              |
| <span data-ttu-id="40e09-110">插斷和中斷偵錯工具</span><span class="sxs-lookup"><span data-stu-id="40e09-110">Interrupt and break debugger</span></span>          | <span data-ttu-id="40e09-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="40e09-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="40e09-112"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="40e09-112"><kbd>F6</kbd></span></span>                               |
| <span data-ttu-id="40e09-113">執行目前該行/反白顯示的文字</span><span class="sxs-lookup"><span data-stu-id="40e09-113">Execute current line/highlighted text</span></span> | <span data-ttu-id="40e09-114"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="40e09-114"><kbd>F8</kbd></span></span>                | <span data-ttu-id="40e09-115"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="40e09-115"><kbd>F8</kbd></span></span>                               |
| <span data-ttu-id="40e09-116">清單中可用的程式碼片段</span><span class="sxs-lookup"><span data-stu-id="40e09-116">List available snippets</span></span>               | <span data-ttu-id="40e09-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="40e09-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="40e09-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="40e09-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

### <a name="custom-key-bindings"></a><span data-ttu-id="40e09-119">自訂按鍵繫結</span><span class="sxs-lookup"><span data-stu-id="40e09-119">Custom Key bindings</span></span>

<span data-ttu-id="40e09-120">您可以[設定您自己的金鑰繫結](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)也 VSCode 中。</span><span class="sxs-lookup"><span data-stu-id="40e09-120">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode as well.</span></span>

## <a name="tab-completion"></a><span data-ttu-id="40e09-121">Tab 鍵自動完成</span><span class="sxs-lookup"><span data-stu-id="40e09-121">Tab completion</span></span>

<span data-ttu-id="40e09-122">若要啟用更類似 ISE 的 tab 鍵自動完成，請新增這項設定：</span><span class="sxs-lookup"><span data-stu-id="40e09-122">To enable more ISE-like tab completion, add this setting:</span></span>

```json
"editor.tabCompletion": "on"
```

> [!NOTE]
> <span data-ttu-id="40e09-123">此設定已加入直接 VSCode （而不是在延伸模組）。</span><span class="sxs-lookup"><span data-stu-id="40e09-123">This setting was added directly to VSCode (rather than in the extension).</span></span> <span data-ttu-id="40e09-124">其行為取決於 VSCode 直接而且無法變更延伸模組。</span><span class="sxs-lookup"><span data-stu-id="40e09-124">Its behavior is determined by VSCode directly and cannot be changed by the extension.</span></span>

## <a name="no-focus-on-console-when-executing"></a><span data-ttu-id="40e09-125">在主控台中執行時沒有焦點</span><span class="sxs-lookup"><span data-stu-id="40e09-125">No focus on console when executing</span></span>

<span data-ttu-id="40e09-126">若要將焦點保持在編輯器中，當您執行與<kbd>F8</kbd>:</span><span class="sxs-lookup"><span data-stu-id="40e09-126">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

<span data-ttu-id="40e09-127">預設值是`true`協助工具。</span><span class="sxs-lookup"><span data-stu-id="40e09-127">The default is `true` for accessibility purposes.</span></span>

## <a name="dont-start-integrated-console-on-startup"></a><span data-ttu-id="40e09-128">不要在啟動時啟動整合式的主控台</span><span class="sxs-lookup"><span data-stu-id="40e09-128">Don't start integrated console on startup</span></span>

<span data-ttu-id="40e09-129">若要停止啟動整合式的主控台，設定：</span><span class="sxs-lookup"><span data-stu-id="40e09-129">To stop the integrated console on startup, set:</span></span>

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> <span data-ttu-id="40e09-130">因為可提供 IntelliSense、 指令碼分析、 符號瀏覽等，還是會啟動背景 PowerShell 處理程序。但主控台將不會顯示。</span><span class="sxs-lookup"><span data-stu-id="40e09-130">The background PowerShell process will still start since that provides IntelliSense, script analysis, symbol navigation, etc. But the console won't be shown.</span></span>

## <a name="assume-files-are-powershell-by-default"></a><span data-ttu-id="40e09-131">假設檔案是預設的 PowerShell</span><span class="sxs-lookup"><span data-stu-id="40e09-131">Assume files are PowerShell by default</span></span>

<span data-ttu-id="40e09-132">若要讓新/未命名的檔案，註冊 PowerShell 作為預設：</span><span class="sxs-lookup"><span data-stu-id="40e09-132">To make new/untitled files, register as PowerShell by default:</span></span>

```json
"files.defaultLanguage": "powershell"
```

## <a name="color-scheme"></a><span data-ttu-id="40e09-133">色彩配置</span><span class="sxs-lookup"><span data-stu-id="40e09-133">Color scheme</span></span>

<span data-ttu-id="40e09-134">有數個 ISE 主題適用於 VSCode 看起來比較像 ISE 編輯器進行。</span><span class="sxs-lookup"><span data-stu-id="40e09-134">There are a number of ISE themes available for VSCode to make the editor look much more like the ISE.</span></span>

<span data-ttu-id="40e09-135">在 [命令調色盤]型別`theme`以取得`Preferences: Color Theme`按<kbd>Enter</kbd>。</span><span class="sxs-lookup"><span data-stu-id="40e09-135">In the [Command Palette] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span>
<span data-ttu-id="40e09-136">在下拉式清單中，選取  `PowerShell ISE`。</span><span class="sxs-lookup"><span data-stu-id="40e09-136">In the drop-down list, select `PowerShell ISE`.</span></span>

<span data-ttu-id="40e09-137">您可以在設定中設定此佈景主題：</span><span class="sxs-lookup"><span data-stu-id="40e09-137">You can set this theme in the settings with:</span></span>

```json
"workbench.colorTheme": "PowerShell ISE"
```

## <a name="powershell-command-explorer"></a><span data-ttu-id="40e09-138">PowerShell 命令總管</span><span class="sxs-lookup"><span data-stu-id="40e09-138">PowerShell Command Explorer</span></span>

<span data-ttu-id="40e09-139">工作的感謝[ @corbob ](https://github.com/corbob)，PowerShell 延伸模組有自己的命令檔案總管的開頭。</span><span class="sxs-lookup"><span data-stu-id="40e09-139">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

<span data-ttu-id="40e09-140">在 [命令調色盤]，輸入`PowerShell Command Explorer`按下<kbd>Enter</kbd>。</span><span class="sxs-lookup"><span data-stu-id="40e09-140">In the [Command Palette], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

## <a name="open-in-the-ise"></a><span data-ttu-id="40e09-141">在 ISE 中開啟</span><span class="sxs-lookup"><span data-stu-id="40e09-141">Open in the ISE</span></span>

<span data-ttu-id="40e09-142">如果您最後想要在 ISE 中仍開啟檔案，您可以使用<kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>。</span><span class="sxs-lookup"><span data-stu-id="40e09-142">If you end up wanting to open a file in the ISE anyway, you can use <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span></span>

## <a name="other-resources"></a><span data-ttu-id="40e09-143">其他資源</span><span class="sxs-lookup"><span data-stu-id="40e09-143">Other resources</span></span>

- <span data-ttu-id="40e09-144">具有 4sysops[非常棒的文章](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/)上設定為更像是 ISE VSCode。</span><span class="sxs-lookup"><span data-stu-id="40e09-144">4sysops has [a great article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) on configuring VSCode to be more like the ISE.</span></span>
- <span data-ttu-id="40e09-145">具有 Mike F Robbins[很棒的文章](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/)設定 VSCode。</span><span class="sxs-lookup"><span data-stu-id="40e09-145">Mike F Robbins has [a great post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) on setting up VSCode.</span></span>
- <span data-ttu-id="40e09-146">了解 PowerShell 的[絕佳寫入](https://www.learnpwsh.com/setup-vs-code-for-powershell/)取得 VSCode 安裝 powershell。</span><span class="sxs-lookup"><span data-stu-id="40e09-146">Learn PowerShell has [an excellent write up](https://www.learnpwsh.com/setup-vs-code-for-powershell/) on getting VSCode setup for PowerShell.</span></span>

## <a name="more-settings"></a><span data-ttu-id="40e09-147">更多設定</span><span class="sxs-lookup"><span data-stu-id="40e09-147">More settings</span></span>

<span data-ttu-id="40e09-148">如果您知道如何讓 VSCode 覺得 ISE 使用者較熟悉的對此文件。如果沒有您所尋找的相容性設定，但找不到任何方式來啟用它，[開立](https://github.com/PowerShell/vscode-powershell/issues/new/choose)和請立即詢問 ！</span><span class="sxs-lookup"><span data-stu-id="40e09-148">If you know of more ways to make VSCode feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue](https://github.com/PowerShell/vscode-powershell/issues/new/choose) and ask away!</span></span>

<span data-ttu-id="40e09-149">我們很高興一律接受 Pr 和以及貢獻 ！</span><span class="sxs-lookup"><span data-stu-id="40e09-149">We're always happy to accept PRs and contributions as well!</span></span>

## <a name="vscode-tips"></a><span data-ttu-id="40e09-150">VSCode 秘訣</span><span class="sxs-lookup"><span data-stu-id="40e09-150">VSCode Tips</span></span>

### <a name="command-palette"></a><span data-ttu-id="40e09-151">命令選擇區</span><span class="sxs-lookup"><span data-stu-id="40e09-151">Command Palette</span></span>

<span data-ttu-id="40e09-152"><kbd>F1</kbd>或是<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd> + <kbd>移位</kbd>+<kbd>P</kbd>在 macOS 上)</span><span class="sxs-lookup"><span data-stu-id="40e09-152"><kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS)</span></span>

<span data-ttu-id="40e09-153">在 VSCode 中執行命令的便利的方式。</span><span class="sxs-lookup"><span data-stu-id="40e09-153">A handy way of executing commands in VSCode.</span></span>
<span data-ttu-id="40e09-154">如需詳細資訊，請參閱 < [VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette)。</span><span class="sxs-lookup"><span data-stu-id="40e09-154">For more information, see [the VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span></span>

[命令調色盤]: #command-palette
[Command Palette]: #command-palette
