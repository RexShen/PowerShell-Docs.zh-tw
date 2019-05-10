---
title: 如何在 Visual Studio Code 中複寫 ISE 體驗
description: 如何在 Visual Studio Code 中複寫 ISE 體驗
ms.date: 08/06/2018
ms.openlocfilehash: 983da850c13d72bcdc7b2d33970c6e9e06b3d869
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058500"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="a0e4d-103">如何在 Visual Studio Code 中複寫 ISE 體驗</span><span class="sxs-lookup"><span data-stu-id="a0e4d-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="a0e4d-104">雖然適用於 VSCode 的 PowerShell 延伸模組不會尋求與 PowerShell ISE 完全功能同位，但是已經有功能可以讓 ISE 的使用者獲得更自然的 VSCode 使用體驗。</span><span class="sxs-lookup"><span data-stu-id="a0e4d-104">While the PowerShell extension for VSCode doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VSCode experience more natural for users of the ISE.</span></span>

<span data-ttu-id="a0e4d-105">此文件列出您可以在 VSCode 中使用的設定，讓使用者獲得相較於 ISE 更熟悉 VSCode 的體驗。</span><span class="sxs-lookup"><span data-stu-id="a0e4d-105">This document tries to list settings you can configure in VSCode to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="key-bindings"></a><span data-ttu-id="a0e4d-106">按鍵繫結關係</span><span class="sxs-lookup"><span data-stu-id="a0e4d-106">Key bindings</span></span>

| <span data-ttu-id="a0e4d-107">函式</span><span class="sxs-lookup"><span data-stu-id="a0e4d-107">Function</span></span>                              | <span data-ttu-id="a0e4d-108">ISE 繫結</span><span class="sxs-lookup"><span data-stu-id="a0e4d-108">ISE Binding</span></span>                  | <span data-ttu-id="a0e4d-109">VSCode 繫結</span><span class="sxs-lookup"><span data-stu-id="a0e4d-109">VSCode Binding</span></span>                              |
| ----------------                      | -----------                  | --------------                              |
| <span data-ttu-id="a0e4d-110">插斷和中斷偵錯工具</span><span class="sxs-lookup"><span data-stu-id="a0e4d-110">Interrupt and break debugger</span></span>          | <span data-ttu-id="a0e4d-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="a0e4d-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="a0e4d-112"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="a0e4d-112"><kbd>F6</kbd></span></span>                               |
| <span data-ttu-id="a0e4d-113">執行目前的行/反白顯示的文字</span><span class="sxs-lookup"><span data-stu-id="a0e4d-113">Execute current line/highlighted text</span></span> | <span data-ttu-id="a0e4d-114"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="a0e4d-114"><kbd>F8</kbd></span></span>                | <span data-ttu-id="a0e4d-115"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="a0e4d-115"><kbd>F8</kbd></span></span>                               |
| <span data-ttu-id="a0e4d-116">列出可用的程式碼片段</span><span class="sxs-lookup"><span data-stu-id="a0e4d-116">List available snippets</span></span>               | <span data-ttu-id="a0e4d-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="a0e4d-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="a0e4d-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="a0e4d-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

### <a name="custom-key-bindings"></a><span data-ttu-id="a0e4d-119">自訂按鍵繫結關係</span><span class="sxs-lookup"><span data-stu-id="a0e4d-119">Custom Key bindings</span></span>

<span data-ttu-id="a0e4d-120">您也可以在 VSCode 中[設定自己的按鍵繫結關係](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="a0e4d-120">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode as well.</span></span>

## <a name="tab-completion"></a><span data-ttu-id="a0e4d-121">Tab 鍵自動完成</span><span class="sxs-lookup"><span data-stu-id="a0e4d-121">Tab completion</span></span>

<span data-ttu-id="a0e4d-122">若要啟用更類似 ISE 的 Tab 鍵自動完成，請新增此設定：</span><span class="sxs-lookup"><span data-stu-id="a0e4d-122">To enable more ISE-like tab completion, add this setting:</span></span>

```json
"editor.tabCompletion": "on"
```

> [!NOTE]
> <span data-ttu-id="a0e4d-123">此設定已直接新增至 VSCode (而不是放在延伸模組中)。</span><span class="sxs-lookup"><span data-stu-id="a0e4d-123">This setting was added directly to VSCode (rather than in the extension).</span></span> <span data-ttu-id="a0e4d-124">其行為直接取決於 VSCode，而且無法透過延伸模組來變更。</span><span class="sxs-lookup"><span data-stu-id="a0e4d-124">Its behavior is determined by VSCode directly and cannot be changed by the extension.</span></span>

## <a name="no-focus-on-console-when-executing"></a><span data-ttu-id="a0e4d-125">執行時不會將焦點放在主控台上</span><span class="sxs-lookup"><span data-stu-id="a0e4d-125">No focus on console when executing</span></span>

<span data-ttu-id="a0e4d-126">在使用 <kbd>F8</kbd> 執行時將焦點保持在編輯器中：</span><span class="sxs-lookup"><span data-stu-id="a0e4d-126">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

<span data-ttu-id="a0e4d-127">預設值是 `true`，代表協助工具目的。</span><span class="sxs-lookup"><span data-stu-id="a0e4d-127">The default is `true` for accessibility purposes.</span></span>

## <a name="dont-start-integrated-console-on-startup"></a><span data-ttu-id="a0e4d-128">不要在啟動時啟動整合式主控台</span><span class="sxs-lookup"><span data-stu-id="a0e4d-128">Don't start integrated console on startup</span></span>

<span data-ttu-id="a0e4d-129">若要在啟動時停止整合式主控台，請設定：</span><span class="sxs-lookup"><span data-stu-id="a0e4d-129">To stop the integrated console on startup, set:</span></span>

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> <span data-ttu-id="a0e4d-130">但是還是會啟動背景 PowerShell 處理序，因為這可以提供 IntelliSense、指令碼分析、符號導覽等等功能。但主控台將不會顯示。</span><span class="sxs-lookup"><span data-stu-id="a0e4d-130">The background PowerShell process will still start since that provides IntelliSense, script analysis, symbol navigation, etc. But the console won't be shown.</span></span>

## <a name="assume-files-are-powershell-by-default"></a><span data-ttu-id="a0e4d-131">假設檔案預設為 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a0e4d-131">Assume files are PowerShell by default</span></span>

<span data-ttu-id="a0e4d-132">若要讓新/未命名的檔案預設註冊為 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="a0e4d-132">To make new/untitled files, register as PowerShell by default:</span></span>

```json
"files.defaultLanguage": "powershell"
```

## <a name="color-scheme"></a><span data-ttu-id="a0e4d-133">色彩配置</span><span class="sxs-lookup"><span data-stu-id="a0e4d-133">Color scheme</span></span>

<span data-ttu-id="a0e4d-134">有幾個 ISE 佈景主題可供 VSCode 使用，會讓編輯器看起來非常像 ISE。</span><span class="sxs-lookup"><span data-stu-id="a0e4d-134">There are a number of ISE themes available for VSCode to make the editor look much more like the ISE.</span></span>

<span data-ttu-id="a0e4d-135">在 [命令選擇區] 中輸入 `theme` 以取得 `Preferences: Color Theme`，然後按 <kbd>Enter</kbd>。</span><span class="sxs-lookup"><span data-stu-id="a0e4d-135">In the [Command Palette] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span>
<span data-ttu-id="a0e4d-136">在下拉式清單中選取 `PowerShell ISE`。</span><span class="sxs-lookup"><span data-stu-id="a0e4d-136">In the drop-down list, select `PowerShell ISE`.</span></span>

<span data-ttu-id="a0e4d-137">您可以在設定中透過下項目設定此佈景主題：</span><span class="sxs-lookup"><span data-stu-id="a0e4d-137">You can set this theme in the settings with:</span></span>

```json
"workbench.colorTheme": "PowerShell ISE"
```

## <a name="powershell-command-explorer"></a><span data-ttu-id="a0e4d-138">PowerShell 命令總管</span><span class="sxs-lookup"><span data-stu-id="a0e4d-138">PowerShell Command Explorer</span></span>

<span data-ttu-id="a0e4d-139">感謝 [@corbob](https://github.com/corbob) 所做的一切，PowerShell 延伸模組開始有自己的命令檔案總管了。</span><span class="sxs-lookup"><span data-stu-id="a0e4d-139">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

<span data-ttu-id="a0e4d-140">在[命令選擇區]中，輸入 `PowerShell Command Explorer` 並按 <kbd>Enter</kbd>。</span><span class="sxs-lookup"><span data-stu-id="a0e4d-140">In the [Command Palette], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

## <a name="open-in-the-ise"></a><span data-ttu-id="a0e4d-141">在 ISE 中開啟</span><span class="sxs-lookup"><span data-stu-id="a0e4d-141">Open in the ISE</span></span>

<span data-ttu-id="a0e4d-142">如果您最後還是想要在 ISE 中開啟檔案，可以使用 <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>。</span><span class="sxs-lookup"><span data-stu-id="a0e4d-142">If you end up wanting to open a file in the ISE anyway, you can use <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span></span>

## <a name="other-resources"></a><span data-ttu-id="a0e4d-143">其他資源</span><span class="sxs-lookup"><span data-stu-id="a0e4d-143">Other resources</span></span>

- <span data-ttu-id="a0e4d-144">4sysops 有一篇[非常棒的文章](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) \(英文\)，內容說明如何設定 VSCode，讓它更像 ISE。</span><span class="sxs-lookup"><span data-stu-id="a0e4d-144">4sysops has [a great article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) on configuring VSCode to be more like the ISE.</span></span>
- <span data-ttu-id="a0e4d-145">Mike F Robbins 貼了一篇[很棒的貼文](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) \(英文\)，內容說明如何設定 VSCode。</span><span class="sxs-lookup"><span data-stu-id="a0e4d-145">Mike F Robbins has [a great post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) on setting up VSCode.</span></span>
- <span data-ttu-id="a0e4d-146">Learn PowerShell 有一篇[絕佳文章](https://www.learnpwsh.com/setup-vs-code-for-powershell/) \(英文\)，內容說明如何為 PowerShell 設定 VSCode。</span><span class="sxs-lookup"><span data-stu-id="a0e4d-146">Learn PowerShell has [an excellent write up](https://www.learnpwsh.com/setup-vs-code-for-powershell/) on getting VSCode setup for PowerShell.</span></span>

## <a name="more-settings"></a><span data-ttu-id="a0e4d-147">更多設定</span><span class="sxs-lookup"><span data-stu-id="a0e4d-147">More settings</span></span>

<span data-ttu-id="a0e4d-148">如果您知道其他能夠讓 ISE 使用者更熟悉 VSCode 的方法，請將它們加到此文件中。如果您正在尋找相容性設定，但怎麼樣都找不到啟用它的方式，可以[在這裡提出問題](https://github.com/PowerShell/vscode-powershell/issues/new/choose)詢問！</span><span class="sxs-lookup"><span data-stu-id="a0e4d-148">If you know of more ways to make VSCode feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue](https://github.com/PowerShell/vscode-powershell/issues/new/choose) and ask away!</span></span>

<span data-ttu-id="a0e4d-149">我們非常歡迎 PR 與您的貢獻！</span><span class="sxs-lookup"><span data-stu-id="a0e4d-149">We're always happy to accept PRs and contributions as well!</span></span>

## <a name="vscode-tips"></a><span data-ttu-id="a0e4d-150">VSCode 祕訣</span><span class="sxs-lookup"><span data-stu-id="a0e4d-150">VSCode Tips</span></span>

### <a name="command-palette"></a><span data-ttu-id="a0e4d-151">命令選擇區</span><span class="sxs-lookup"><span data-stu-id="a0e4d-151">Command Palette</span></span>

<span data-ttu-id="a0e4d-152"><kbd>F1</kbd> 或是 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (在 macOS 上為 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>)</span><span class="sxs-lookup"><span data-stu-id="a0e4d-152"><kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS)</span></span>

<span data-ttu-id="a0e4d-153">在 VSCode 中執行命令的便利方式。</span><span class="sxs-lookup"><span data-stu-id="a0e4d-153">A handy way of executing commands in VSCode.</span></span>
<span data-ttu-id="a0e4d-154">如需詳細資訊，請參閱 [VSCode 文件](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette) (英文)。</span><span class="sxs-lookup"><span data-stu-id="a0e4d-154">For more information, see [the VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span></span>

[命令選擇區]: #command-palette
[Command Palette]: #command-palette
