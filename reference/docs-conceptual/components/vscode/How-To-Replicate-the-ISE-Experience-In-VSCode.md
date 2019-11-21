---
title: 如何在 Visual Studio Code 中複寫 ISE 體驗
description: 如何在 Visual Studio Code 中複寫 ISE 體驗
ms.date: 08/06/2018
ms.openlocfilehash: d5542e9a3a48b1ae64356309be669418edf6c79e
ms.sourcegitcommit: a6e54a305fdeb6482321c77da8066d2f991c93e1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2019
ms.locfileid: "74117453"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a>如何在 Visual Studio Code 中複寫 ISE 體驗

雖然適用於 VSCode 的 PowerShell 延伸模組不會尋求與 PowerShell ISE 完全功能同位，但是已經有功能可以讓 ISE 的使用者獲得更自然的 VSCode 使用體驗。

此文件列出您可以在 VSCode 中使用的設定，讓使用者獲得相較於 ISE 更熟悉 VSCode 的體驗。

## <a name="key-bindings"></a>按鍵繫結關係

| 函式                              | ISE 繫結                  | VSCode 繫結                              |
| ----------------                      | -----------                  | --------------                              |
| 插斷和中斷偵錯工具          | <kbd>Ctrl</kbd>+<kbd>B</kbd> | <kbd>F6</kbd>                               |
| 執行目前的行/反白顯示的文字 | <kbd>F8</kbd>                | <kbd>F8</kbd>                               |
| 列出可用的程式碼片段               | <kbd>Ctrl</kbd>+<kbd>J</kbd> | <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd> |

### <a name="custom-key-bindings"></a>自訂按鍵繫結關係

您也可以在 VSCode 中[設定自己的按鍵繫結關係](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) \(英文\)。

## <a name="simplified-ise-like-ui"></a>簡化的類 ISE UI

如果您想要簡化 Visual Studio Code UI，讓它看起來更類似 ISE 的 UI，請套用下列兩項設定：

```json
"workbench.activityBar.visible": false,
"debug.openDebug": "neverOpen",
```

這會隱藏下方紅色方塊內的「活動列」和「偵錯側邊欄」區段：

![醒目提示的區段包含活動列與偵錯側邊欄](images/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

最終結果如下所示：

![簡化的 VS Code 檢視](images/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

## <a name="tab-completion"></a>Tab 鍵自動完成

若要啟用更類似 ISE 的 Tab 鍵自動完成，請新增此設定：

```json
"editor.tabCompletion": "on",
```

> [!NOTE]
> 此設定已直接新增至 VSCode (而不是放在延伸模組中)。 其行為直接取決於 VSCode，而且無法透過延伸模組來變更。

## <a name="no-focus-on-console-when-executing"></a>執行時不會將焦點放在主控台上

在使用 <kbd>F8</kbd> 執行時將焦點保持在編輯器中：

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

預設值是 `true`，代表協助工具目的。

## <a name="dont-start-integrated-console-on-startup"></a>不要在啟動時啟動整合式主控台

若要在啟動時停止整合式主控台，請設定：

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> 但是還是會啟動背景 PowerShell 處理序，因為這可以提供 IntelliSense、指令碼分析、符號導覽等等功能。但主控台將不會顯示。

## <a name="assume-files-are-powershell-by-default"></a>假設檔案預設為 PowerShell

若要讓新/未命名的檔案預設註冊為 PowerShell：

```json
"files.defaultLanguage": "powershell",
```

## <a name="color-scheme"></a>色彩配置

有幾個 ISE 佈景主題可供 VSCode 使用，會讓編輯器看起來非常像 ISE。

在 [命令選擇區] 中輸入 `theme` 以取得 `Preferences: Color Theme`，然後按 <kbd>Enter</kbd>。
在下拉式清單中選取 `PowerShell ISE`。

您可以在設定中透過下項目設定此佈景主題：

```json
"workbench.colorTheme": "PowerShell ISE",
```

## <a name="powershell-command-explorer"></a>PowerShell 命令總管

感謝 [@corbob](https://github.com/corbob) 所做的一切，PowerShell 延伸模組開始有自己的命令檔案總管了。

在[命令選擇區]中，輸入 `PowerShell Command Explorer` 並按 <kbd>Enter</kbd>。

## <a name="open-in-the-ise"></a>在 ISE 中開啟

如果您最後還是想要在 ISE 中開啟檔案，可以使用 <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>。

## <a name="other-resources"></a>其他資源

- 4sysops 有一篇[非常棒的文章](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) \(英文\)，內容說明如何設定 VSCode，讓它更像 ISE。
- Mike F Robbins 貼了一篇[很棒的貼文](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) \(英文\)，內容說明如何設定 VSCode。
- Learn PowerShell 有一篇[絕佳文章](https://www.learnpwsh.com/setup-vs-code-for-powershell/) \(英文\)，內容說明如何為 PowerShell 設定 VSCode。

## <a name="more-settings"></a>更多設定

如果您知道其他能夠讓 ISE 使用者更熟悉 VSCode 的方法，請將它們加到此文件中。如果您正在尋找相容性設定，但怎麼樣都找不到啟用它的方式，可以[在這裡提出問題](https://github.com/PowerShell/vscode-powershell/issues/new/choose)詢問！

我們非常歡迎 PR 與您的貢獻！

## <a name="vscode-tips"></a>VSCode 祕訣

### <a name="command-palette"></a>命令選擇區

<kbd>F1</kbd> 或是 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (在 macOS 上為 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>)

在 VSCode 中執行命令的便利方式。
如需詳細資訊，請參閱 [VSCode 文件](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette) (英文)。

[命令選擇區]: #command-palette
