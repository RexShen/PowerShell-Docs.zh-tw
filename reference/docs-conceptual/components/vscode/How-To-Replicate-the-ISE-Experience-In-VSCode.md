---
title: 如何在 Visual Studio Code 中複寫 ISE 體驗
description: 如何在 Visual Studio Code 中複寫 ISE 體驗
ms.date: 08/06/2018
ms.openlocfilehash: 193243dc2e3e921b22a6ee068370200ae84ce4ac
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279232"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="d0155-103">如何在 Visual Studio Code 中複寫 ISE 體驗</span><span class="sxs-lookup"><span data-stu-id="d0155-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="d0155-104">雖然適用於 VSCode 的 PowerShell 延伸模組不會尋求與 PowerShell ISE 完全功能同位，但是已經有功能可以讓 ISE 的使用者獲得更自然的 VSCode 使用體驗。</span><span class="sxs-lookup"><span data-stu-id="d0155-104">While the PowerShell extension for VSCode doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VSCode experience more natural for users of the ISE.</span></span>

<span data-ttu-id="d0155-105">此文件列出您可以在 VSCode 中使用的設定，讓使用者獲得相較於 ISE 更熟悉 VSCode 的體驗。</span><span class="sxs-lookup"><span data-stu-id="d0155-105">This document tries to list settings you can configure in VSCode to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="ise-mode"></a><span data-ttu-id="d0155-106">ISE 模式</span><span class="sxs-lookup"><span data-stu-id="d0155-106">ISE Mode</span></span>

> [!NOTE]
> <span data-ttu-id="d0155-107">此功能從 2019.12.0 版開始於 PowerShell Preview 延伸模組中提供，以及從 2020.3.0 版開始於 PowerShell 延伸模組中提供。</span><span class="sxs-lookup"><span data-stu-id="d0155-107">This feature is available in the PowerShell Preview extension since version 2019.12.0 and in the PowerShell extension since version 2020.3.0.</span></span>

<span data-ttu-id="d0155-108">在 Visual Studio Code 中重現 ISE 體驗最簡單的方式，便是開啟「ISE 模式」。</span><span class="sxs-lookup"><span data-stu-id="d0155-108">The easiest way to replicate the ISE experience in Visual Studio Code is by turning on "ISE Mode".</span></span>
<span data-ttu-id="d0155-109">若要這麼做，請開啟命令選擇區 (<kbd>F1</kbd> 或 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> 或 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (於 macOS 上))，然後輸入「ISE 模式」。</span><span class="sxs-lookup"><span data-stu-id="d0155-109">To do this, open the command pallet (<kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> OR <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS) and type in "ISE Mode".</span></span>
<span data-ttu-id="d0155-110">從清單中選取 [PowerShell:Enable ISE Mode] \(PowerShell: 啟用 ISE 模式\)。</span><span class="sxs-lookup"><span data-stu-id="d0155-110">Select "PowerShell: Enable ISE Mode" from the list.</span></span>

<span data-ttu-id="d0155-111">此命令將會自動套用可在此文件中找到的許多設定。</span><span class="sxs-lookup"><span data-stu-id="d0155-111">This command will apply a lot of the settings found in this document automatically.</span></span>
<span data-ttu-id="d0155-112">結果如下所示：</span><span class="sxs-lookup"><span data-stu-id="d0155-112">The result looks like this:</span></span>

![ISE 模式](media/How-To-Replicate-the-ISE-Experience-In-VSCode/3-ise-mode.png)

<span data-ttu-id="d0155-114">此文章的其餘部分會包含 ISE 模式中的設定及一些其他設定的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="d0155-114">The rest of this article includes more detailed information on settings in ISE Mode and some additional settings.</span></span>

## <a name="key-bindings"></a><span data-ttu-id="d0155-115">按鍵繫結關係</span><span class="sxs-lookup"><span data-stu-id="d0155-115">Key bindings</span></span>

| <span data-ttu-id="d0155-116">函式</span><span class="sxs-lookup"><span data-stu-id="d0155-116">Function</span></span>                              | <span data-ttu-id="d0155-117">ISE 繫結</span><span class="sxs-lookup"><span data-stu-id="d0155-117">ISE Binding</span></span>                  | <span data-ttu-id="d0155-118">VSCode 繫結</span><span class="sxs-lookup"><span data-stu-id="d0155-118">VSCode Binding</span></span>                              |
| ----------------                      | -----------                  | --------------                              |
| <span data-ttu-id="d0155-119">插斷和中斷偵錯工具</span><span class="sxs-lookup"><span data-stu-id="d0155-119">Interrupt and break debugger</span></span>          | <span data-ttu-id="d0155-120"><kbd>Ctrl</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="d0155-120"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="d0155-121"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="d0155-121"><kbd>F6</kbd></span></span>                               |
| <span data-ttu-id="d0155-122">執行目前的行/反白顯示的文字</span><span class="sxs-lookup"><span data-stu-id="d0155-122">Execute current line/highlighted text</span></span> | <span data-ttu-id="d0155-123"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="d0155-123"><kbd>F8</kbd></span></span>                | <span data-ttu-id="d0155-124"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="d0155-124"><kbd>F8</kbd></span></span>                               |
| <span data-ttu-id="d0155-125">列出可用的程式碼片段</span><span class="sxs-lookup"><span data-stu-id="d0155-125">List available snippets</span></span>               | <span data-ttu-id="d0155-126"><kbd>Ctrl</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="d0155-126"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="d0155-127"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="d0155-127"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

### <a name="custom-key-bindings"></a><span data-ttu-id="d0155-128">自訂按鍵繫結關係</span><span class="sxs-lookup"><span data-stu-id="d0155-128">Custom Key bindings</span></span>

<span data-ttu-id="d0155-129">您也可以在 VSCode 中[設定自己的按鍵繫結關係](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="d0155-129">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode as well.</span></span>

## <a name="simplified-ise-like-ui"></a><span data-ttu-id="d0155-130">簡化的類 ISE UI</span><span class="sxs-lookup"><span data-stu-id="d0155-130">Simplified ISE-like UI</span></span>

<span data-ttu-id="d0155-131">如果您想要簡化 Visual Studio Code UI，讓它看起來更類似 ISE 的 UI，請套用下列兩項設定：</span><span class="sxs-lookup"><span data-stu-id="d0155-131">If you're looking to simplify the Visual Studio Code UI to look more closely to the UI of the ISE, apply these two settings:</span></span>

```json
"workbench.activityBar.visible": false,
"debug.openDebug": "neverOpen",
```

> [!NOTE]
> <span data-ttu-id="d0155-132">這些設定已包含在 [ISE 模式](#ise-mode)中。</span><span class="sxs-lookup"><span data-stu-id="d0155-132">These settings are included in ["ISE Mode"](#ise-mode).</span></span>

<span data-ttu-id="d0155-133">這會隱藏下方紅色方塊內的「活動列」和「偵錯側邊欄」區段：</span><span class="sxs-lookup"><span data-stu-id="d0155-133">This will hide the "Activity Bar" and the "Debug Side Bar" sections below inside of the red box:</span></span>

![醒目提示的區段包含活動列與偵錯側邊欄](media/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

<span data-ttu-id="d0155-135">最終結果如下所示：</span><span class="sxs-lookup"><span data-stu-id="d0155-135">The end result looks like this:</span></span>

![簡化的 VS Code 檢視](media/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

## <a name="tab-completion"></a><span data-ttu-id="d0155-137">Tab 鍵自動完成</span><span class="sxs-lookup"><span data-stu-id="d0155-137">Tab completion</span></span>

<span data-ttu-id="d0155-138">若要啟用更類似 ISE 的 Tab 鍵自動完成，請新增此設定：</span><span class="sxs-lookup"><span data-stu-id="d0155-138">To enable more ISE-like tab completion, add this setting:</span></span>

```json
"editor.tabCompletion": "on",
```

> [!NOTE]
> <span data-ttu-id="d0155-139">此設定已直接新增至 VSCode (而不是放在延伸模組中)。</span><span class="sxs-lookup"><span data-stu-id="d0155-139">This setting was added directly to VSCode (rather than in the extension).</span></span> <span data-ttu-id="d0155-140">其行為直接取決於 VSCode，而且無法透過延伸模組來變更。</span><span class="sxs-lookup"><span data-stu-id="d0155-140">Its behavior is determined by VSCode directly and cannot be changed by the extension.</span></span>

> [!NOTE]
> <span data-ttu-id="d0155-141">此設定已包含在 [ISE 模式](#ise-mode)中。</span><span class="sxs-lookup"><span data-stu-id="d0155-141">This setting is included in ["ISE Mode"](#ise-mode).</span></span>

## <a name="no-focus-on-console-when-executing"></a><span data-ttu-id="d0155-142">執行時的焦點不在主控台</span><span class="sxs-lookup"><span data-stu-id="d0155-142">No focus on console when executing</span></span>

<span data-ttu-id="d0155-143">在使用 <kbd>F8</kbd> 執行時將焦點保持在編輯器中：</span><span class="sxs-lookup"><span data-stu-id="d0155-143">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

> [!NOTE]
> <span data-ttu-id="d0155-144">此設定已包含在 [ISE 模式](#ise-mode)中。</span><span class="sxs-lookup"><span data-stu-id="d0155-144">This setting is included in ["ISE Mode"](#ise-mode).</span></span>

<span data-ttu-id="d0155-145">為了達到協助目的，預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="d0155-145">The default is `true` for accessibility purposes.</span></span>

## <a name="dont-start-integrated-console-on-startup"></a><span data-ttu-id="d0155-146">不要在啟動時啟動整合式主控台</span><span class="sxs-lookup"><span data-stu-id="d0155-146">Don't start integrated console on startup</span></span>

<span data-ttu-id="d0155-147">若要在啟動時停止整合式主控台，請設定：</span><span class="sxs-lookup"><span data-stu-id="d0155-147">To stop the integrated console on startup, set:</span></span>

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> <span data-ttu-id="d0155-148">但是還是會啟動背景 PowerShell 處理序，因為這可以提供 IntelliSense、指令碼分析、符號導覽等等功能。但主控台將不會顯示。</span><span class="sxs-lookup"><span data-stu-id="d0155-148">The background PowerShell process will still start since that provides IntelliSense, script analysis, symbol navigation, etc. But the console won't be shown.</span></span>

## <a name="assume-files-are-powershell-by-default"></a><span data-ttu-id="d0155-149">假設檔案預設為 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d0155-149">Assume files are PowerShell by default</span></span>

<span data-ttu-id="d0155-150">若要讓新/未命名的檔案預設註冊為 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="d0155-150">To make new/untitled files, register as PowerShell by default:</span></span>

```json
"files.defaultLanguage": "powershell",
```

> [!NOTE]
> <span data-ttu-id="d0155-151">此設定已包含在 [ISE 模式](#ise-mode)中。</span><span class="sxs-lookup"><span data-stu-id="d0155-151">This setting is included in ["ISE Mode"](#ise-mode).</span></span>

## <a name="color-scheme"></a><span data-ttu-id="d0155-152">色彩配置</span><span class="sxs-lookup"><span data-stu-id="d0155-152">Color scheme</span></span>

<span data-ttu-id="d0155-153">有幾個 ISE 佈景主題可供 VSCode 使用，會讓編輯器看起來非常像 ISE。</span><span class="sxs-lookup"><span data-stu-id="d0155-153">There are a number of ISE themes available for VSCode to make the editor look much more like the ISE.</span></span>

<span data-ttu-id="d0155-154">在 [命令選擇區] 中輸入 `theme` 以取得 `Preferences: Color Theme`，然後按 <kbd>Enter</kbd>。</span><span class="sxs-lookup"><span data-stu-id="d0155-154">In the [Command Palette] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span>
<span data-ttu-id="d0155-155">在下拉式清單中選取 `PowerShell ISE`。</span><span class="sxs-lookup"><span data-stu-id="d0155-155">In the drop-down list, select `PowerShell ISE`.</span></span>

<span data-ttu-id="d0155-156">您可以在設定中透過下項目設定此佈景主題：</span><span class="sxs-lookup"><span data-stu-id="d0155-156">You can set this theme in the settings with:</span></span>

```json
"workbench.colorTheme": "PowerShell ISE",
```

> [!NOTE]
> <span data-ttu-id="d0155-157">此設定已包含在 [ISE 模式](#ise-mode)中。</span><span class="sxs-lookup"><span data-stu-id="d0155-157">This setting is included in ["ISE Mode"](#ise-mode).</span></span>

## <a name="powershell-command-explorer"></a><span data-ttu-id="d0155-158">PowerShell 命令總管</span><span class="sxs-lookup"><span data-stu-id="d0155-158">PowerShell Command Explorer</span></span>

<span data-ttu-id="d0155-159">感謝 [@corbob](https://github.com/corbob) 所做的一切，PowerShell 延伸模組開始有自己的命令檔案總管了。</span><span class="sxs-lookup"><span data-stu-id="d0155-159">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

<span data-ttu-id="d0155-160">在[命令選擇區]中，輸入 `PowerShell Command Explorer` 並按 <kbd>Enter</kbd>。</span><span class="sxs-lookup"><span data-stu-id="d0155-160">In the [Command Palette], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

> [!NOTE]
> <span data-ttu-id="d0155-161">這會在 [ISE 模式](#ise-mode)中自動顯示。</span><span class="sxs-lookup"><span data-stu-id="d0155-161">This is shown automatically in ["ISE Mode"](#ise-mode).</span></span>

## <a name="open-in-the-ise"></a><span data-ttu-id="d0155-162">在 ISE 中開啟</span><span class="sxs-lookup"><span data-stu-id="d0155-162">Open in the ISE</span></span>

<span data-ttu-id="d0155-163">如果您最後還是想要在 ISE 中開啟檔案，可以使用 <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>。</span><span class="sxs-lookup"><span data-stu-id="d0155-163">If you end up wanting to open a file in the ISE anyway, you can use <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span></span>

## <a name="other-resources"></a><span data-ttu-id="d0155-164">其他資源</span><span class="sxs-lookup"><span data-stu-id="d0155-164">Other resources</span></span>

- <span data-ttu-id="d0155-165">4sysops 有一篇[非常棒的文章](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) \(英文\)，內容說明如何設定 VSCode，讓它更像 ISE。</span><span class="sxs-lookup"><span data-stu-id="d0155-165">4sysops has [a great article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) on configuring VSCode to be more like the ISE.</span></span>
- <span data-ttu-id="d0155-166">Mike F Robbins 貼了一篇[很棒的貼文](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) \(英文\)，內容說明如何設定 VSCode。</span><span class="sxs-lookup"><span data-stu-id="d0155-166">Mike F Robbins has [a great post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) on setting up VSCode.</span></span>
- <span data-ttu-id="d0155-167">Learn PowerShell 有一篇[絕佳文章](https://www.learnpwsh.com/setup-vs-code-for-powershell/) \(英文\)，內容說明如何為 PowerShell 設定 VSCode。</span><span class="sxs-lookup"><span data-stu-id="d0155-167">Learn PowerShell has [an excellent write up](https://www.learnpwsh.com/setup-vs-code-for-powershell/) on getting VSCode setup for PowerShell.</span></span>

## <a name="more-settings"></a><span data-ttu-id="d0155-168">更多設定</span><span class="sxs-lookup"><span data-stu-id="d0155-168">More settings</span></span>

<span data-ttu-id="d0155-169">如果您知道其他能夠讓 ISE 使用者更熟悉 VSCode 的方法，請將它們加到此文件中。如果您正在尋找相容性設定，但怎麼樣都找不到啟用它的方式，可以[在這裡提出問題](https://github.com/PowerShell/vscode-powershell/issues/new/choose)詢問！</span><span class="sxs-lookup"><span data-stu-id="d0155-169">If you know of more ways to make VSCode feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue](https://github.com/PowerShell/vscode-powershell/issues/new/choose) and ask away!</span></span>

<span data-ttu-id="d0155-170">我們非常歡迎 PR 與您的貢獻！</span><span class="sxs-lookup"><span data-stu-id="d0155-170">We're always happy to accept PRs and contributions as well!</span></span>

## <a name="vscode-tips"></a><span data-ttu-id="d0155-171">VSCode 祕訣</span><span class="sxs-lookup"><span data-stu-id="d0155-171">VSCode Tips</span></span>

### <a name="command-palette"></a><span data-ttu-id="d0155-172">命令選擇區</span><span class="sxs-lookup"><span data-stu-id="d0155-172">Command Palette</span></span>

<span data-ttu-id="d0155-173"><kbd>F1</kbd> 或是 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (在 macOS 上為 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>)</span><span class="sxs-lookup"><span data-stu-id="d0155-173"><kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS)</span></span>

<span data-ttu-id="d0155-174">在 VSCode 中執行命令的便利方式。</span><span class="sxs-lookup"><span data-stu-id="d0155-174">A handy way of executing commands in VSCode.</span></span>
<span data-ttu-id="d0155-175">如需詳細資訊，請參閱 [VSCode 文件](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette) (英文)。</span><span class="sxs-lookup"><span data-stu-id="d0155-175">For more information, see [the VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span></span>

[命令選擇區]: #command-palette
[Command Palette]: #command-palette
