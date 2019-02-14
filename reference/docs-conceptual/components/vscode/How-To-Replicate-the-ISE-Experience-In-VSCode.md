---
title: 如何在 Visual Studio Code 中複寫 ISE 體驗
description: 如何在 Visual Studio Code 中複寫 ISE 體驗
ms.date: 08/06/2018
ms.openlocfilehash: 983da850c13d72bcdc7b2d33970c6e9e06b3d869
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55678846"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a>如何在 Visual Studio Code 中複寫 ISE 體驗

雖然 VSCode 的 PowerShell 延伸模組不會尋找完整的功能同位檢查，以 PowerShell ISE 功能中有地方，VSCode 體驗更自然的 ISE 使用者。

這份文件會嘗試在 VSCode，若要讓使用者體驗更熟悉相較於 ISE 中，您可以設定的清單設定。

## <a name="key-bindings"></a>按鍵繫結

| 函式                              | ISE 繫結                  | VSCode 繫結                              |
| ----------------                      | -----------                  | --------------                              |
| 插斷和中斷偵錯工具          | <kbd>Ctrl</kbd>+<kbd>B</kbd> | <kbd>F6</kbd>                               |
| 執行目前該行/反白顯示的文字 | <kbd>F8</kbd>                | <kbd>F8</kbd>                               |
| 清單中可用的程式碼片段               | <kbd>Ctrl</kbd>+<kbd>J</kbd> | <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd> |

### <a name="custom-key-bindings"></a>自訂按鍵繫結

您可以[設定您自己的金鑰繫結](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)也 VSCode 中。

## <a name="tab-completion"></a>Tab 鍵自動完成

若要啟用更類似 ISE 的 tab 鍵自動完成，請新增這項設定：

```json
"editor.tabCompletion": "on"
```

> [!NOTE]
> 此設定已加入直接 VSCode （而不是在延伸模組）。 其行為取決於 VSCode 直接而且無法變更延伸模組。

## <a name="no-focus-on-console-when-executing"></a>在主控台中執行時沒有焦點

若要將焦點保持在編輯器中，當您執行與<kbd>F8</kbd>:

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

預設值是`true`協助工具。

## <a name="dont-start-integrated-console-on-startup"></a>不要在啟動時啟動整合式的主控台

若要停止啟動整合式的主控台，設定：

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> 因為可提供 IntelliSense、 指令碼分析、 符號瀏覽等，還是會啟動背景 PowerShell 處理程序。但主控台將不會顯示。

## <a name="assume-files-are-powershell-by-default"></a>假設檔案是預設的 PowerShell

若要讓新/未命名的檔案，註冊 PowerShell 作為預設：

```json
"files.defaultLanguage": "powershell"
```

## <a name="color-scheme"></a>色彩配置

有數個 ISE 主題適用於 VSCode 看起來比較像 ISE 編輯器進行。

在 [命令調色盤]型別`theme`以取得`Preferences: Color Theme`按<kbd>Enter</kbd>。
在下拉式清單中，選取  `PowerShell ISE`。

您可以在設定中設定此佈景主題：

```json
"workbench.colorTheme": "PowerShell ISE"
```

## <a name="powershell-command-explorer"></a>PowerShell 命令總管

工作的感謝[ @corbob ](https://github.com/corbob)，PowerShell 延伸模組有自己的命令檔案總管的開頭。

在 [命令調色盤]，輸入`PowerShell Command Explorer`按下<kbd>Enter</kbd>。

## <a name="open-in-the-ise"></a>在 ISE 中開啟

如果您最後想要在 ISE 中仍開啟檔案，您可以使用<kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>。

## <a name="other-resources"></a>其他資源

- 具有 4sysops[非常棒的文章](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/)上設定為更像是 ISE VSCode。
- 具有 Mike F Robbins[很棒的文章](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/)設定 VSCode。
- 了解 PowerShell 的[絕佳寫入](https://www.learnpwsh.com/setup-vs-code-for-powershell/)取得 VSCode 安裝 powershell。

## <a name="more-settings"></a>更多設定

如果您知道如何讓 VSCode 覺得 ISE 使用者較熟悉的對此文件。如果沒有您所尋找的相容性設定，但找不到任何方式來啟用它，[開立](https://github.com/PowerShell/vscode-powershell/issues/new/choose)和請立即詢問 ！

我們很高興一律接受 Pr 和以及貢獻 ！

## <a name="vscode-tips"></a>VSCode 秘訣

### <a name="command-palette"></a>命令選擇區

<kbd>F1</kbd>或是<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd> + <kbd>移位</kbd>+<kbd>P</kbd>在 macOS 上)

在 VSCode 中執行命令的便利的方式。
如需詳細資訊，請參閱 < [VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette)。

[命令調色盤]: #command-palette
