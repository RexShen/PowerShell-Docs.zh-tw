---
title: 如何在 Visual Studio Code 中複寫 ISE 體驗
description: 如何在 Visual Studio Code 中複寫 ISE 體驗
ms.date: 08/06/2018
ms.openlocfilehash: d5542e9a3a48b1ae64356309be669418edf6c79e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74117453"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="b3f9f-103">如何在 Visual Studio Code 中複寫 ISE 體驗</span><span class="sxs-lookup"><span data-stu-id="b3f9f-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="b3f9f-104">雖然適用於 VSCode 的 PowerShell 延伸模組不會尋求與 PowerShell ISE 完全功能同位，但是已經有功能可以讓 ISE 的使用者獲得更自然的 VSCode 使用體驗。</span><span class="sxs-lookup"><span data-stu-id="b3f9f-104">While the PowerShell extension for VSCode doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VSCode experience more natural for users of the ISE.</span></span>

<span data-ttu-id="b3f9f-105">此文件列出您可以在 VSCode 中使用的設定，讓使用者獲得相較於 ISE 更熟悉 VSCode 的體驗。</span><span class="sxs-lookup"><span data-stu-id="b3f9f-105">This document tries to list settings you can configure in VSCode to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="key-bindings"></a><span data-ttu-id="b3f9f-106">按鍵繫結關係</span><span class="sxs-lookup"><span data-stu-id="b3f9f-106">Key bindings</span></span>

| <span data-ttu-id="b3f9f-107">函式</span><span class="sxs-lookup"><span data-stu-id="b3f9f-107">Function</span></span>                              | <span data-ttu-id="b3f9f-108">ISE 繫結</span><span class="sxs-lookup"><span data-stu-id="b3f9f-108">ISE Binding</span></span>                  | <span data-ttu-id="b3f9f-109">VSCode 繫結</span><span class="sxs-lookup"><span data-stu-id="b3f9f-109">VSCode Binding</span></span>                              |
| ----------------                      | -----------                  | --------------                              |
| <span data-ttu-id="b3f9f-110">插斷和中斷偵錯工具</span><span class="sxs-lookup"><span data-stu-id="b3f9f-110">Interrupt and break debugger</span></span>          | <span data-ttu-id="b3f9f-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="b3f9f-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="b3f9f-112"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="b3f9f-112"><kbd>F6</kbd></span></span>                               |
| <span data-ttu-id="b3f9f-113">執行目前的行/反白顯示的文字</span><span class="sxs-lookup"><span data-stu-id="b3f9f-113">Execute current line/highlighted text</span></span> | <span data-ttu-id="b3f9f-114"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="b3f9f-114"><kbd>F8</kbd></span></span>                | <span data-ttu-id="b3f9f-115"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="b3f9f-115"><kbd>F8</kbd></span></span>                               |
| <span data-ttu-id="b3f9f-116">列出可用的程式碼片段</span><span class="sxs-lookup"><span data-stu-id="b3f9f-116">List available snippets</span></span>               | <span data-ttu-id="b3f9f-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="b3f9f-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="b3f9f-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="b3f9f-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

### <a name="custom-key-bindings"></a><span data-ttu-id="b3f9f-119">自訂按鍵繫結關係</span><span class="sxs-lookup"><span data-stu-id="b3f9f-119">Custom Key bindings</span></span>

<span data-ttu-id="b3f9f-120">您也可以在 VSCode 中[設定自己的按鍵繫結關係](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="b3f9f-120">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode as well.</span></span>

## <a name="simplified-ise-like-ui"></a><span data-ttu-id="b3f9f-121">簡化的類 ISE UI</span><span class="sxs-lookup"><span data-stu-id="b3f9f-121">Simplified ISE-like UI</span></span>

<span data-ttu-id="b3f9f-122">如果您想要簡化 Visual Studio Code UI，讓它看起來更類似 ISE 的 UI，請套用下列兩項設定：</span><span class="sxs-lookup"><span data-stu-id="b3f9f-122">If you're looking to simplify the Visual Studio Code UI to look more closely to the UI of the ISE, apply these two settings:</span></span>

```json
"workbench.activityBar.visible": false,
"debug.openDebug": "neverOpen",
```

<span data-ttu-id="b3f9f-123">這會隱藏下方紅色方塊內的「活動列」和「偵錯側邊欄」區段：</span><span class="sxs-lookup"><span data-stu-id="b3f9f-123">This will hide the "Activity Bar" and the "Debug Side Bar" sections below inside of the red box:</span></span>

![醒目提示的區段包含活動列與偵錯側邊欄](images/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

<span data-ttu-id="b3f9f-125">最終結果如下所示：</span><span class="sxs-lookup"><span data-stu-id="b3f9f-125">The end result looks like this:</span></span>

![簡化的 VS Code 檢視](images/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

## <a name="tab-completion"></a><span data-ttu-id="b3f9f-127">Tab 鍵自動完成</span><span class="sxs-lookup"><span data-stu-id="b3f9f-127">Tab completion</span></span>

<span data-ttu-id="b3f9f-128">若要啟用更類似 ISE 的 Tab 鍵自動完成，請新增此設定：</span><span class="sxs-lookup"><span data-stu-id="b3f9f-128">To enable more ISE-like tab completion, add this setting:</span></span>

```json
"editor.tabCompletion": "on",
```

> [!NOTE]
> <span data-ttu-id="b3f9f-129">此設定已直接新增至 VSCode (而不是放在延伸模組中)。</span><span class="sxs-lookup"><span data-stu-id="b3f9f-129">This setting was added directly to VSCode (rather than in the extension).</span></span> <span data-ttu-id="b3f9f-130">其行為直接取決於 VSCode，而且無法透過延伸模組來變更。</span><span class="sxs-lookup"><span data-stu-id="b3f9f-130">Its behavior is determined by VSCode directly and cannot be changed by the extension.</span></span>

## <a name="no-focus-on-console-when-executing"></a><span data-ttu-id="b3f9f-131">執行時不會將焦點放在主控台上</span><span class="sxs-lookup"><span data-stu-id="b3f9f-131">No focus on console when executing</span></span>

<span data-ttu-id="b3f9f-132">在使用 <kbd>F8</kbd> 執行時將焦點保持在編輯器中：</span><span class="sxs-lookup"><span data-stu-id="b3f9f-132">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

<span data-ttu-id="b3f9f-133">預設值是 `true`，代表協助工具目的。</span><span class="sxs-lookup"><span data-stu-id="b3f9f-133">The default is `true` for accessibility purposes.</span></span>

## <a name="dont-start-integrated-console-on-startup"></a><span data-ttu-id="b3f9f-134">不要在啟動時啟動整合式主控台</span><span class="sxs-lookup"><span data-stu-id="b3f9f-134">Don't start integrated console on startup</span></span>

<span data-ttu-id="b3f9f-135">若要在啟動時停止整合式主控台，請設定：</span><span class="sxs-lookup"><span data-stu-id="b3f9f-135">To stop the integrated console on startup, set:</span></span>

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> <span data-ttu-id="b3f9f-136">但是還是會啟動背景 PowerShell 處理序，因為這可以提供 IntelliSense、指令碼分析、符號導覽等等功能。但主控台將不會顯示。</span><span class="sxs-lookup"><span data-stu-id="b3f9f-136">The background PowerShell process will still start since that provides IntelliSense, script analysis, symbol navigation, etc. But the console won't be shown.</span></span>

## <a name="assume-files-are-powershell-by-default"></a><span data-ttu-id="b3f9f-137">假設檔案預設為 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b3f9f-137">Assume files are PowerShell by default</span></span>

<span data-ttu-id="b3f9f-138">若要讓新/未命名的檔案預設註冊為 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="b3f9f-138">To make new/untitled files, register as PowerShell by default:</span></span>

```json
"files.defaultLanguage": "powershell",
```

## <a name="color-scheme"></a><span data-ttu-id="b3f9f-139">色彩配置</span><span class="sxs-lookup"><span data-stu-id="b3f9f-139">Color scheme</span></span>

<span data-ttu-id="b3f9f-140">有幾個 ISE 佈景主題可供 VSCode 使用，會讓編輯器看起來非常像 ISE。</span><span class="sxs-lookup"><span data-stu-id="b3f9f-140">There are a number of ISE themes available for VSCode to make the editor look much more like the ISE.</span></span>

<span data-ttu-id="b3f9f-141">在 [命令選擇區] 中輸入 `theme` 以取得 `Preferences: Color Theme`，然後按 <kbd>Enter</kbd>。</span><span class="sxs-lookup"><span data-stu-id="b3f9f-141">In the [Command Palette] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span>
<span data-ttu-id="b3f9f-142">在下拉式清單中選取 `PowerShell ISE`。</span><span class="sxs-lookup"><span data-stu-id="b3f9f-142">In the drop-down list, select `PowerShell ISE`.</span></span>

<span data-ttu-id="b3f9f-143">您可以在設定中透過下項目設定此佈景主題：</span><span class="sxs-lookup"><span data-stu-id="b3f9f-143">You can set this theme in the settings with:</span></span>

```json
"workbench.colorTheme": "PowerShell ISE",
```

## <a name="powershell-command-explorer"></a><span data-ttu-id="b3f9f-144">PowerShell 命令總管</span><span class="sxs-lookup"><span data-stu-id="b3f9f-144">PowerShell Command Explorer</span></span>

<span data-ttu-id="b3f9f-145">感謝 [@corbob](https://github.com/corbob) 所做的一切，PowerShell 延伸模組開始有自己的命令檔案總管了。</span><span class="sxs-lookup"><span data-stu-id="b3f9f-145">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

<span data-ttu-id="b3f9f-146">在[命令選擇區]中，輸入 `PowerShell Command Explorer` 並按 <kbd>Enter</kbd>。</span><span class="sxs-lookup"><span data-stu-id="b3f9f-146">In the [Command Palette], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

## <a name="open-in-the-ise"></a><span data-ttu-id="b3f9f-147">在 ISE 中開啟</span><span class="sxs-lookup"><span data-stu-id="b3f9f-147">Open in the ISE</span></span>

<span data-ttu-id="b3f9f-148">如果您最後還是想要在 ISE 中開啟檔案，可以使用 <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>。</span><span class="sxs-lookup"><span data-stu-id="b3f9f-148">If you end up wanting to open a file in the ISE anyway, you can use <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span></span>

## <a name="other-resources"></a><span data-ttu-id="b3f9f-149">其他資源</span><span class="sxs-lookup"><span data-stu-id="b3f9f-149">Other resources</span></span>

- <span data-ttu-id="b3f9f-150">4sysops 有一篇[非常棒的文章](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) \(英文\)，內容說明如何設定 VSCode，讓它更像 ISE。</span><span class="sxs-lookup"><span data-stu-id="b3f9f-150">4sysops has [a great article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) on configuring VSCode to be more like the ISE.</span></span>
- <span data-ttu-id="b3f9f-151">Mike F Robbins 貼了一篇[很棒的貼文](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) \(英文\)，內容說明如何設定 VSCode。</span><span class="sxs-lookup"><span data-stu-id="b3f9f-151">Mike F Robbins has [a great post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) on setting up VSCode.</span></span>
- <span data-ttu-id="b3f9f-152">Learn PowerShell 有一篇[絕佳文章](https://www.learnpwsh.com/setup-vs-code-for-powershell/) \(英文\)，內容說明如何為 PowerShell 設定 VSCode。</span><span class="sxs-lookup"><span data-stu-id="b3f9f-152">Learn PowerShell has [an excellent write up](https://www.learnpwsh.com/setup-vs-code-for-powershell/) on getting VSCode setup for PowerShell.</span></span>

## <a name="more-settings"></a><span data-ttu-id="b3f9f-153">更多設定</span><span class="sxs-lookup"><span data-stu-id="b3f9f-153">More settings</span></span>

<span data-ttu-id="b3f9f-154">如果您知道其他能夠讓 ISE 使用者更熟悉 VSCode 的方法，請將它們加到此文件中。如果您正在尋找相容性設定，但怎麼樣都找不到啟用它的方式，可以[在這裡提出問題](https://github.com/PowerShell/vscode-powershell/issues/new/choose)詢問！</span><span class="sxs-lookup"><span data-stu-id="b3f9f-154">If you know of more ways to make VSCode feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue](https://github.com/PowerShell/vscode-powershell/issues/new/choose) and ask away!</span></span>

<span data-ttu-id="b3f9f-155">我們非常歡迎 PR 與您的貢獻！</span><span class="sxs-lookup"><span data-stu-id="b3f9f-155">We're always happy to accept PRs and contributions as well!</span></span>

## <a name="vscode-tips"></a><span data-ttu-id="b3f9f-156">VSCode 祕訣</span><span class="sxs-lookup"><span data-stu-id="b3f9f-156">VSCode Tips</span></span>

### <a name="command-palette"></a><span data-ttu-id="b3f9f-157">命令選擇區</span><span class="sxs-lookup"><span data-stu-id="b3f9f-157">Command Palette</span></span>

<span data-ttu-id="b3f9f-158"><kbd>F1</kbd> 或是 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (在 macOS 上為 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>)</span><span class="sxs-lookup"><span data-stu-id="b3f9f-158"><kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS)</span></span>

<span data-ttu-id="b3f9f-159">在 VSCode 中執行命令的便利方式。</span><span class="sxs-lookup"><span data-stu-id="b3f9f-159">A handy way of executing commands in VSCode.</span></span>
<span data-ttu-id="b3f9f-160">如需詳細資訊，請參閱 [VSCode 文件](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette) (英文)。</span><span class="sxs-lookup"><span data-stu-id="b3f9f-160">For more information, see [the VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span></span>

[命令選擇區]: #command-palette
[Command Palette]: #command-palette
