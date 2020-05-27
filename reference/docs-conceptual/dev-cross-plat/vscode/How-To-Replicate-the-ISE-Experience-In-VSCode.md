---
title: 如何在 Visual Studio Code 中複寫 ISE 體驗
description: 如何在 Visual Studio Code 中複寫 ISE 體驗
ms.date: 08/06/2018
ms.openlocfilehash: 899e1c393fd49b0659631b88d610e80ec885e69e
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809594"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="a7166-103">如何在 Visual Studio Code 中複寫 ISE 體驗</span><span class="sxs-lookup"><span data-stu-id="a7166-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="a7166-104">雖然適用於 VS Code 的 PowerShell 擴充功能不會尋求與 PowerShell ISE 的功能完全相同，但是已經有功能可以讓 ISE 的使用者獲得更自然的 VS Code 使用體驗。</span><span class="sxs-lookup"><span data-stu-id="a7166-104">While the PowerShell extension for VS Code doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VS Code experience more natural for users of the ISE.</span></span>

<span data-ttu-id="a7166-105">此文件列出您可以在 VS Code 中使用的設定，讓使用者體驗相較之下稍微類似 ISE。</span><span class="sxs-lookup"><span data-stu-id="a7166-105">This document tries to list settings you can configure in VS Code to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="ise-mode"></a><span data-ttu-id="a7166-106">ISE 模式</span><span class="sxs-lookup"><span data-stu-id="a7166-106">ISE Mode</span></span>

> [!NOTE]
> <span data-ttu-id="a7166-107">此功能從 2019.12.0 版開始於 PowerShell Preview 延伸模組中提供，以及從 2020.3.0 版開始於 PowerShell 延伸模組中提供。</span><span class="sxs-lookup"><span data-stu-id="a7166-107">This feature is available in the PowerShell Preview extension since version 2019.12.0 and in the PowerShell extension since version 2020.3.0.</span></span>

<span data-ttu-id="a7166-108">在 Visual Studio Code 中重現 ISE 體驗最簡單的方式，便是開啟「ISE 模式」。</span><span class="sxs-lookup"><span data-stu-id="a7166-108">The easiest way to replicate the ISE experience in Visual Studio Code is by turning on "ISE Mode".</span></span>
<span data-ttu-id="a7166-109">若要這樣做，請開啟命令選擇區 (<kbd>F1</kbd> 或 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>，或在 macOS 上則為 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>)，然後輸入「ISE 模式」。</span><span class="sxs-lookup"><span data-stu-id="a7166-109">To do this, open the command palette (<kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> OR <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS) and type in "ISE Mode".</span></span> <span data-ttu-id="a7166-110">從清單中選取 [PowerShell:Enable ISE Mode] \(PowerShell: 啟用 ISE 模式\)。</span><span class="sxs-lookup"><span data-stu-id="a7166-110">Select "PowerShell: Enable ISE Mode" from the list.</span></span>

<span data-ttu-id="a7166-111">此命令會自動套用下面所述設定。結果看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="a7166-111">This command automatically applies the settings described below The result looks like this:</span></span>

![ISE 模式](media/How-To-Replicate-the-ISE-Experience-In-VSCode/3-ise-mode.png)

## <a name="ise-mode-configuration-settings"></a><span data-ttu-id="a7166-113">ISE 模式組態設定</span><span class="sxs-lookup"><span data-stu-id="a7166-113">ISE Mode configuration settings</span></span>

<span data-ttu-id="a7166-114">ISE 模式會對 VS Code 設定進行下列變更。</span><span class="sxs-lookup"><span data-stu-id="a7166-114">ISE Mode makes the following changes to VS Code settings.</span></span>

- <span data-ttu-id="a7166-115">按鍵繫結關係</span><span class="sxs-lookup"><span data-stu-id="a7166-115">Key bindings</span></span>

  |               <span data-ttu-id="a7166-116">函式</span><span class="sxs-lookup"><span data-stu-id="a7166-116">Function</span></span>                |         <span data-ttu-id="a7166-117">ISE 繫結</span><span class="sxs-lookup"><span data-stu-id="a7166-117">ISE Binding</span></span>          |              <span data-ttu-id="a7166-118">VS Code 繫結</span><span class="sxs-lookup"><span data-stu-id="a7166-118">VS Code Binding</span></span>                |
  | ------------------------------------- | ---------------------------- | ------------------------------------------- |
  | <span data-ttu-id="a7166-119">插斷和中斷偵錯工具</span><span class="sxs-lookup"><span data-stu-id="a7166-119">Interrupt and break debugger</span></span>          | <span data-ttu-id="a7166-120"><kbd>Ctrl</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="a7166-120"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="a7166-121"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="a7166-121"><kbd>F6</kbd></span></span>                               |
  | <span data-ttu-id="a7166-122">執行目前的行/反白顯示的文字</span><span class="sxs-lookup"><span data-stu-id="a7166-122">Execute current line/highlighted text</span></span> | <span data-ttu-id="a7166-123"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="a7166-123"><kbd>F8</kbd></span></span>                | <span data-ttu-id="a7166-124"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="a7166-124"><kbd>F8</kbd></span></span>                               |
  | <span data-ttu-id="a7166-125">列出可用的程式碼片段</span><span class="sxs-lookup"><span data-stu-id="a7166-125">List available snippets</span></span>               | <span data-ttu-id="a7166-126"><kbd>Ctrl</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="a7166-126"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="a7166-127"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="a7166-127"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

  > [!NOTE]
  > <span data-ttu-id="a7166-128">您也可以在 VS Code 中[設定自己的按鍵繫結關係](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="a7166-128">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VS Code as well.</span></span>

- <span data-ttu-id="a7166-129">簡化的類 ISE UI</span><span class="sxs-lookup"><span data-stu-id="a7166-129">Simplified ISE-like UI</span></span>

  <span data-ttu-id="a7166-130">如果您想要簡化 Visual Studio Code UI，讓它看起來更類似 ISE 的 UI，請套用下列兩項設定：</span><span class="sxs-lookup"><span data-stu-id="a7166-130">If you're looking to simplify the Visual Studio Code UI to look more closely to the UI of the ISE, apply these two settings:</span></span>

  ```json
  "workbench.activityBar.visible": false,
  "debug.openDebug": "neverOpen",
  ```

  <span data-ttu-id="a7166-131">這些設定會隱藏下方紅色方塊內的「活動列」與「偵錯側邊欄」區段：</span><span class="sxs-lookup"><span data-stu-id="a7166-131">These settings hide the "Activity Bar" and the "Debug Side Bar" sections shown inside the red box below:</span></span>

  ![醒目提示的區段包含活動列與偵錯側邊欄](media/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

  <span data-ttu-id="a7166-133">最終結果如下所示：</span><span class="sxs-lookup"><span data-stu-id="a7166-133">The end result looks like this:</span></span>

  ![簡化的 VS Code 檢視](media/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

- <span data-ttu-id="a7166-135">Tab 鍵自動完成</span><span class="sxs-lookup"><span data-stu-id="a7166-135">Tab completion</span></span>

  <span data-ttu-id="a7166-136">若要啟用更類似 ISE 的 Tab 鍵自動完成，請新增此設定：</span><span class="sxs-lookup"><span data-stu-id="a7166-136">To enable more ISE-like tab completion, add this setting:</span></span>

  ```json
  "editor.tabCompletion": "on",
  ```

- <span data-ttu-id="a7166-137">執行時的焦點不在主控台</span><span class="sxs-lookup"><span data-stu-id="a7166-137">No focus on console when executing</span></span>

  <span data-ttu-id="a7166-138">在使用 <kbd>F8</kbd> 執行時將焦點保持在編輯器中：</span><span class="sxs-lookup"><span data-stu-id="a7166-138">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

  ```json
  "powershell.integratedConsole.focusConsoleOnExecute": false
  ```

  <span data-ttu-id="a7166-139">為了達到協助目的，預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="a7166-139">The default is `true` for accessibility purposes.</span></span>

- <span data-ttu-id="a7166-140">不要在啟動時啟動整合式主控台</span><span class="sxs-lookup"><span data-stu-id="a7166-140">Don't start integrated console on startup</span></span>

  <span data-ttu-id="a7166-141">若要在啟動時停止整合式主控台，請設定：</span><span class="sxs-lookup"><span data-stu-id="a7166-141">To stop the integrated console on startup, set:</span></span>

  ```json
  "powershell.integratedConsole.showOnStartup": false
  ```

  > [!NOTE]
  > <span data-ttu-id="a7166-142">背景 PowerShell 處理序還是會啟動，以提供 IntelliSense、指令碼分析、符號導覽等功能，但不會顯示主控台。</span><span class="sxs-lookup"><span data-stu-id="a7166-142">The background PowerShell process still starts to provide IntelliSense, script analysis, symbol navigation, etc., but the console won't be shown.</span></span>

- <span data-ttu-id="a7166-143">假設檔案預設為 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a7166-143">Assume files are PowerShell by default</span></span>

  <span data-ttu-id="a7166-144">若要讓新/未命名的檔案預設註冊為 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="a7166-144">To make new/untitled files, register as PowerShell by default:</span></span>

  ```json
  "files.defaultLanguage": "powershell",
  ```

- <span data-ttu-id="a7166-145">色彩配置</span><span class="sxs-lookup"><span data-stu-id="a7166-145">Color scheme</span></span>

  <span data-ttu-id="a7166-146">有幾個 ISE 佈景主題可供 VS Code 使用，會讓編輯器看起來非常像 ISE。</span><span class="sxs-lookup"><span data-stu-id="a7166-146">There are a number of ISE themes available for VS Code to make the editor look much more like the ISE.</span></span>

  <span data-ttu-id="a7166-147">在 [[命令選擇區]][] 中輸入 `theme` 以取得 `Preferences: Color Theme`，然後按 <kbd>Enter</kbd>。</span><span class="sxs-lookup"><span data-stu-id="a7166-147">In the [Command Palette][] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span> <span data-ttu-id="a7166-148">在下拉式清單中選取 `PowerShell ISE`。</span><span class="sxs-lookup"><span data-stu-id="a7166-148">In the drop-down list, select `PowerShell ISE`.</span></span>

  <span data-ttu-id="a7166-149">您可以在設定中透過下項目設定此佈景主題：</span><span class="sxs-lookup"><span data-stu-id="a7166-149">You can set this theme in the settings with:</span></span>

  ```json
  "workbench.colorTheme": "PowerShell ISE",
  ```

- <span data-ttu-id="a7166-150">PowerShell 命令總管</span><span class="sxs-lookup"><span data-stu-id="a7166-150">PowerShell Command Explorer</span></span>

  <span data-ttu-id="a7166-151">感謝 [@corbob](https://github.com/corbob) 所做的一切，PowerShell 延伸模組開始有自己的命令檔案總管了。</span><span class="sxs-lookup"><span data-stu-id="a7166-151">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

  <span data-ttu-id="a7166-152">在[[命令選擇區]][]中，輸入 `PowerShell Command Explorer` 並按 <kbd>Enter</kbd>。</span><span class="sxs-lookup"><span data-stu-id="a7166-152">In the [Command Palette][], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

- <span data-ttu-id="a7166-153">在 ISE 中開啟</span><span class="sxs-lookup"><span data-stu-id="a7166-153">Open in the ISE</span></span>

  <span data-ttu-id="a7166-154">如果您想要在 Windows PowerShell ISE 中開啟檔案，請開啟 [[命令選擇區]][]，搜尋「在 ISE 中開啟」，然後選取 [PowerShell:  在 PowerShell ISE 中開啟目前的檔案]。</span><span class="sxs-lookup"><span data-stu-id="a7166-154">If you want to open a file in the Windows PowerShell ISE anyway, open the [Command Palette][], search for "open in ise", then select **PowerShell: Open Current File in PowerShell ISE**.</span></span>

## <a name="other-resources"></a><span data-ttu-id="a7166-155">其他資源</span><span class="sxs-lookup"><span data-stu-id="a7166-155">Other resources</span></span>

- <span data-ttu-id="a7166-156">4sysops 有一篇[非常棒的文章][4sysops]，內容說明如何將 VS Code 設定成更像 ISE。</span><span class="sxs-lookup"><span data-stu-id="a7166-156">4sysops has [a great article][4sysops] on configuring VS Code to be more like the ISE.</span></span>
- <span data-ttu-id="a7166-157">Mike F Robbins 貼了一篇[很棒的貼文][mikefrobbins]，內容說明如何設定 VS Code。</span><span class="sxs-lookup"><span data-stu-id="a7166-157">Mike F Robbins has [a great post][mikefrobbins] on setting up VS Code.</span></span>
- <span data-ttu-id="a7166-158">Learn PowerShell 有一篇[絕佳文章][learnpwsh]，內容說明如何針對 PowerShell 設定。</span><span class="sxs-lookup"><span data-stu-id="a7166-158">Learn PowerShell has [an excellent write up][learnpwsh] setup for PowerShell.</span></span>

## <a name="vs-code-tips"></a><span data-ttu-id="a7166-159">VS Code 提示</span><span class="sxs-lookup"><span data-stu-id="a7166-159">VS Code Tips</span></span>

- <span data-ttu-id="a7166-160">命令選擇區</span><span class="sxs-lookup"><span data-stu-id="a7166-160">Command Palette</span></span>

  <span data-ttu-id="a7166-161">命令選擇區是在 VS Code 中執行命令的便利方式。</span><span class="sxs-lookup"><span data-stu-id="a7166-161">The Command Palette is handy way of executing commands in VS Code.</span></span> <span data-ttu-id="a7166-162">若要開啟命令選擇區，請使用 <kbd>F1</kbd> 或 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>，或在 macOS 上則為 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>。</span><span class="sxs-lookup"><span data-stu-id="a7166-162">Open the command palette using <kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> OR <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS.</span></span>

  <span data-ttu-id="a7166-163">如需詳細資訊，請參閱 [VS Code 文件][vsc-docs]。</span><span class="sxs-lookup"><span data-stu-id="a7166-163">For more information, see [the VS Code documentation][vsc-docs].</span></span>

- <span data-ttu-id="a7166-164">停用偵錯主控台</span><span class="sxs-lookup"><span data-stu-id="a7166-164">Disable the Debug Console</span></span>

  <span data-ttu-id="a7166-165">如果您只打算使用 VS Code 來撰寫 PowerShell 指令碼，您可以隱藏 [偵錯主控台]  ，因為 PowerShell 擴充功能不會加以使用。</span><span class="sxs-lookup"><span data-stu-id="a7166-165">If you only plan on using VS Code for PowerShell scripting, you can hide the **Debug Console** since it is not used by the PowerShell extension.</span></span> <span data-ttu-id="a7166-166">若要這樣做，請以滑鼠右鍵按一下 [偵錯主控台]  ，然後按一下核取記號來加以隱藏。</span><span class="sxs-lookup"><span data-stu-id="a7166-166">To do so, right click on **Debug Console** then click on the check mark to hide it.</span></span>

## <a name="more-settings"></a><span data-ttu-id="a7166-167">更多設定</span><span class="sxs-lookup"><span data-stu-id="a7166-167">More settings</span></span>

<span data-ttu-id="a7166-168">如果您知道其他能夠讓 VS Code 對 ISE 使用者來講更熟悉的方法，請將其加到此文件中。如果您正在尋找相容性設定，但怎麼樣都找不到啟用它的方式，可以[在這裡提出問題][]詢問！</span><span class="sxs-lookup"><span data-stu-id="a7166-168">If you know of more ways to make VS Code feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue][] and ask away!</span></span>

<span data-ttu-id="a7166-169">我們非常歡迎 PR 與您的貢獻！</span><span class="sxs-lookup"><span data-stu-id="a7166-169">We're always happy to accept PRs and contributions as well!</span></span>

<!-- link references -->
[vsc-docs]: https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette
<span data-ttu-id="a7166-170">[[命令選擇區]]: #vs-code-tips</span><span class="sxs-lookup"><span data-stu-id="a7166-170">[Command Palette]: #vs-code-tips</span></span>
[在這裡提出問題]: https://github.com/PowerShell/VSCode-powershell/issues/new/choose
[open an issue]: https://github.com/PowerShell/VSCode-powershell/issues/new/choose

[4sysops]: https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/
[mikefrobbins]: https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/
[learnpwsh]: https://www.learnpwsh.com/setup-vs-code-for-powershell/
