---
title: 如何在 Visual Studio Code 中複寫 ISE 體驗
description: 如何在 Visual Studio Code 中複寫 ISE 體驗
ms.date: 08/06/2018
ms.openlocfilehash: 899e1c393fd49b0659631b88d610e80ec885e69e
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81005596"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a>如何在 Visual Studio Code 中複寫 ISE 體驗

雖然適用於 VS Code 的 PowerShell 擴充功能不會尋求與 PowerShell ISE 的功能完全相同，但是已經有功能可以讓 ISE 的使用者獲得更自然的 VS Code 使用體驗。

此文件列出您可以在 VS Code 中使用的設定，讓使用者體驗相較之下稍微類似 ISE。

## <a name="ise-mode"></a>ISE 模式

> [!NOTE]
> 此功能從 2019.12.0 版開始於 PowerShell Preview 延伸模組中提供，以及從 2020.3.0 版開始於 PowerShell 延伸模組中提供。

在 Visual Studio Code 中重現 ISE 體驗最簡單的方式，便是開啟「ISE 模式」。
若要這樣做，請開啟命令選擇區 (<kbd>F1</kbd> 或 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>，或在 macOS 上則為 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>)，然後輸入「ISE 模式」。 從清單中選取 [PowerShell:Enable ISE Mode] \(PowerShell: 啟用 ISE 模式\)。

此命令會自動套用下面所述設定。結果看起來像這樣：

![ISE 模式](media/How-To-Replicate-the-ISE-Experience-In-VSCode/3-ise-mode.png)

## <a name="ise-mode-configuration-settings"></a>ISE 模式組態設定

ISE 模式會對 VS Code 設定進行下列變更。

- 按鍵繫結關係

  |               函式                |         ISE 繫結          |              VS Code 繫結                |
  | ------------------------------------- | ---------------------------- | ------------------------------------------- |
  | 插斷和中斷偵錯工具          | <kbd>Ctrl</kbd>+<kbd>B</kbd> | <kbd>F6</kbd>                               |
  | 執行目前的行/反白顯示的文字 | <kbd>F8</kbd>                | <kbd>F8</kbd>                               |
  | 列出可用的程式碼片段               | <kbd>Ctrl</kbd>+<kbd>J</kbd> | <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd> |

  > [!NOTE]
  > 您也可以在 VS Code 中[設定自己的按鍵繫結關係](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) \(英文\)。

- 簡化的類 ISE UI

  如果您想要簡化 Visual Studio Code UI，讓它看起來更類似 ISE 的 UI，請套用下列兩項設定：

  ```json
  "workbench.activityBar.visible": false,
  "debug.openDebug": "neverOpen",
  ```

  這些設定會隱藏下方紅色方塊內的「活動列」與「偵錯側邊欄」區段：

  ![醒目提示的區段包含活動列與偵錯側邊欄](media/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

  最終結果如下所示：

  ![簡化的 VS Code 檢視](media/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

- Tab 鍵自動完成

  若要啟用更類似 ISE 的 Tab 鍵自動完成，請新增此設定：

  ```json
  "editor.tabCompletion": "on",
  ```

- 執行時的焦點不在主控台

  在使用 <kbd>F8</kbd> 執行時將焦點保持在編輯器中：

  ```json
  "powershell.integratedConsole.focusConsoleOnExecute": false
  ```

  為了達到協助目的，預設值為 `true`。

- 不要在啟動時啟動整合式主控台

  若要在啟動時停止整合式主控台，請設定：

  ```json
  "powershell.integratedConsole.showOnStartup": false
  ```

  > [!NOTE]
  > 背景 PowerShell 處理序還是會啟動，以提供 IntelliSense、指令碼分析、符號導覽等功能，但不會顯示主控台。

- 假設檔案預設為 PowerShell

  若要讓新/未命名的檔案預設註冊為 PowerShell：

  ```json
  "files.defaultLanguage": "powershell",
  ```

- 色彩配置

  有幾個 ISE 佈景主題可供 VS Code 使用，會讓編輯器看起來非常像 ISE。

  在 [[命令選擇區]][] 中輸入 `theme` 以取得 `Preferences: Color Theme`，然後按 <kbd>Enter</kbd>。 在下拉式清單中選取 `PowerShell ISE`。

  您可以在設定中透過下項目設定此佈景主題：

  ```json
  "workbench.colorTheme": "PowerShell ISE",
  ```

- PowerShell 命令總管

  感謝 [@corbob](https://github.com/corbob) 所做的一切，PowerShell 延伸模組開始有自己的命令檔案總管了。

  在[[命令選擇區]][]中，輸入 `PowerShell Command Explorer` 並按 <kbd>Enter</kbd>。

- 在 ISE 中開啟

  如果您想要在 Windows PowerShell ISE 中開啟檔案，請開啟 [[命令選擇區]][]，搜尋「在 ISE 中開啟」，然後選取 [PowerShell:  在 PowerShell ISE 中開啟目前的檔案]。

## <a name="other-resources"></a>其他資源

- 4sysops 有一篇[非常棒的文章][4sysops]，內容說明如何將 VS Code 設定成更像 ISE。
- Mike F Robbins 貼了一篇[很棒的貼文][mikefrobbins]，內容說明如何設定 VS Code。
- Learn PowerShell 有一篇[絕佳文章][learnpwsh]，內容說明如何針對 PowerShell 設定。

## <a name="vs-code-tips"></a>VS Code 提示

- 命令選擇區

  命令選擇區是在 VS Code 中執行命令的便利方式。 若要開啟命令選擇區，請使用 <kbd>F1</kbd> 或 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>，或在 macOS 上則為 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>。

  如需詳細資訊，請參閱 [VS Code 文件][vsc-docs]。

- 停用偵錯主控台

  如果您只打算使用 VS Code 來撰寫 PowerShell 指令碼，您可以隱藏 [偵錯主控台]  ，因為 PowerShell 擴充功能不會加以使用。 若要這樣做，請以滑鼠右鍵按一下 [偵錯主控台]  ，然後按一下核取記號來加以隱藏。

## <a name="more-settings"></a>更多設定

如果您知道其他能夠讓 VS Code 對 ISE 使用者來講更熟悉的方法，請將其加到此文件中。如果您正在尋找相容性設定，但怎麼樣都找不到啟用它的方式，可以[在這裡提出問題][]詢問！

我們非常歡迎 PR 與您的貢獻！

<!-- link references -->
[vsc-docs]: https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette
[[命令選擇區]]: #vs-code-tips
[在這裡提出問題]: https://github.com/PowerShell/VSCode-powershell/issues/new/choose

[4sysops]: https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/
[mikefrobbins]: https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/
[learnpwsh]: https://www.learnpwsh.com/setup-vs-code-for-powershell/
