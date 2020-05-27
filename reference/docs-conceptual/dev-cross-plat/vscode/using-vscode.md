---
title: 使用 Visual Studio Code 開發 PowerShell
description: 使用 Visual Studio Code 開發 PowerShell
ms.date: 11/07/2019
ms.openlocfilehash: b492e59f340f4cec92c177ad44bbab9dc95da5da
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808854"
---
# <a name="using-visual-studio-code-for-powershell-development"></a>使用 Visual Studio Code 開發 PowerShell

[Visual Studio Code][vscode] 是 Microsoft 提供的跨平台指令碼編輯器。 搭配 [PowerShell 擴充功能][psext]，其提供了豐富的互動式指令碼編輯體驗，讓您更輕鬆地撰寫可靠的 PowerShell 指令碼。 Visual Studio Code 搭配 PowerShell 延伸模組是撰寫 PowerShell 指令碼的建議編輯器。

其支援下列 PowerShell 版本：

- PowerShell 7 與更新版本 (Windows、macOS 與 Linux)
- PowerShell Core 6 (Windows、macOS 與 Linux)
- Windows PowerShell 5.1 (僅限 Windows)

> [!NOTE]
> Visual Studio Code 與 [Visual Studio][] 不同。

## <a name="getting-started"></a>開始使用

在開始前，請先確定系統上有 PowerShell。 如需 Windows、macOS 和 Linux 上的新型工作負載，請參閱下列連結：

- [在 Linux 上安裝 PowerShell][install-pscore-linux]
- [在 macOS 上安裝 PowerShell][install-pscore-macos]
- [在 Windows 上安裝 PowerShell][install-pscore-windows]

若為傳統的 Windows PowerShell 工作負載，請參閱[安裝 Windows PowerShell][install-winps]。

> [!IMPORTANT]
> Windows 仍可供 [Windows PowerShell ISE][ise] 使用。 不過，其不再有進行中功能開發。 ISE 無法搭配 PowerShell 6 與更新版本使用。 因為其是 Windows 的元件，所以官方仍會繼續支援其安全性與高優先順序的維護修正。
> 我們沒有計劃要將 ISE 從 Windows 移除。

## <a name="editing-with-visual-studio-code"></a>使用 Visual Studio Code 編輯

1. 安裝 Visual Studio Code。 如需詳細資訊，請參閱 [Setting up Visual Studio Code][vsc-setup] (設定 Visual Studio Code) 概觀。

   下列為每個平台的安裝指示：

   - **Windows**：遵循[在 Windows 上執行 Visual Studio Code][vsc-setup-win] \(英文\) 頁面的安裝指示操作。
   - **macOS**：遵循[在 macOS 上執行 Visual Studio Code][vsc-setup-macOS] \(英文\) 頁面的安裝指示操作。
   - **Linux**：遵循[在 Linux 上執行 Visual Studio Code][vsc-setup-linux] \(英文\) 頁面的安裝指示操作。

1. 安裝 PowerShell 延伸模組。

   1. 如果您已安裝 Visual Studio Code Insiders，請透過在主控台中輸入 `code` 或 `code-insiders` 以啟動 Visual Studio Code 應用程式。
   1. 按下 <kbd>Ctrl</kbd>+<kbd>P</kbd> 來啟動 Windows 或 Linux 上的 **Quick Open**。 針對 macOS，則按下 <kbd>Cmd</kbd>+<kbd>P</kbd>。
   1. 在 Quick Open 中，鍵入 `ext install powershell`，然後按下 [輸入]  。
   1. 提要欄位上隨即開啟 [延伸模組]  檢視。 從 Microsoft 選取 PowerShell 延伸模組。
      您應該會看到類似下圖的 Visual Studio Code 畫面：

      ![Visual Studio Code](media/using-vscode/vscode.png)

   1. 從 Microsoft 按一下 PowerShell 延伸模組的 [安裝]  按鈕。
   1. 安裝之後，若您看到 [安裝]  按鈕變成 [重新載入]  ，請按一下 [重新載入]  。
   1. 重新載入 Visual Studio Code 之後，就可以進行編輯。

例如，若要建立新的檔案，請按一下 [檔案] > [新增]  。 若要儲存，請按一下 [檔案] > [儲存]  ，然後提供檔案名稱，例如 `HelloWorld.ps1`。 若要關閉檔案，請按一下檔案名稱旁邊的 `X`。 若要結束 Visual Studio Code，請移至 [檔案] > [結束]  。

### <a name="installing-the-powershell-extension-on-restricted-systems"></a>在受限制的系統上安裝 PowerShell 延伸模組

某些系統已設定為需要所有程式碼簽章的驗證。 您可能收到下列錯誤：

```
Language server startup failed.
```

當 PowerShell 的執行原則是由 Windows 群組原則設定時，可能會發生此問題。 若要手動核准 PowerShell Editor Services 與適用於 Visual Studio Code 的 PowerShell 延伸模組，請開啟 PowerShell 提示字元並執行下列命令：

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

系統會提示您**要執行來自這個不受信任的發行者的軟體嗎？** 輸入 `A` 以執行檔案。 然後，開啟 Visual Studio Code 並檢查 PowerShell 延伸模組是否正常運作。 如果您仍有關於開始使用的問題，請透過 [GitHub 問題][]讓我們知道。

> [!NOTE]
> 適用於 Visual Studio Code 的 PowerShell 延伸模組不支援在限制語言模式中執行。 如需詳細資訊，請參閱 [GitHub 問題 #606][i606]。

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a>選擇要與擴充功能搭配使用的 PowerShell 版本

有了與 Windows PowerShell 並存安裝的 PowerShell Core 之後，現在能夠將特定版本的 PowerShell 與 PowerShell 擴充功能搭配使用。 此功能會查看不同作業系統上的一些已知路徑，以探索 PowerShell 的安裝位置。

使用下列步驟來選擇版本：

1. 按下 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> 來開啟 Windows 或 Linux 上的 [命令選擇區]  。 若為 macOS，請按下 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>。
1. 搜尋**工作階段**。
1. 按一下 [PowerShell:  顯示工作階段功能表]。
1. 從清單中選擇要使用的 PowerShell 版本，例如：**PowerShell Core**。

如果您已將 PowerShell 安裝到非典型位置，則它一開始可能不會顯示於工作階段功能表中。 您可以藉由[新增自己的自訂路徑](#adding-your-own-powershell-paths-to-the-session-menu)來擴充工作階段功能表，如下所述。

> [!NOTE]
> 您也可以從狀態列右下角的綠色版本號碼存取 PowerShell 工作階段功能表。 按一下此版本號碼，即會開啟工作階段功能表。

## <a name="configuration-settings-for-visual-studio-code"></a>Visual Studio Code 的組態設定

首先，如果您不熟悉如何在 Visual Studio Code 中變更設定，建議您閱讀 [Visual Studio Code 的設定][vsc-settings]文件。

閱讀文件之後，您可以在 `settings.json` 中新增組態設定。

```json
{
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

如果您不希望這些設定影響所有檔案類型，Visual Studio Code 也允許個別語言設定。 將設定放入 `[<language-name>]` 欄位，建立語言特定設定。 例如：

```json
{
    "[powershell]": {
        "files.encoding": "utf8bom",
        "files.autoGuessEncoding": true
    }
}
```

> [!TIP]
> 如需有關 Visual Studio Code 中檔案編碼的詳細資訊，請參閱[了解檔案編碼][file-encoding]。
>
> 另請參閱[如何在 Visual Studio Code 中複寫 ISE 體驗][vsc-ise]，以取得有關如何設定 Visual Studio Code 以進行 PowerShell 編輯的其他提示。

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a>將您自己的 PowerShell 路徑新增至工作階段功能表

您可以透過 [Visual Studio Code 設定](https://code.visualstudio.com/docs/getstarted/settings) \(英文\)，將其他 PowerShell 可執行檔路徑新增至工作階段功能表：`powershell.powerShellAdditionalExePaths`。

將項目新增至清單 `powershell.powerShellAdditionalExePaths` 或建立清單 (如果它不存在您的 `settings.json` 中)：

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],

    // other settings...
}
```

每個項目都必須具備：

- `exePath`:`pwsh` 或 `powershell` 可執行檔的路徑。
- `versionName`:將顯示於工作階段功能表中的文字。

若要設定預設 PowerShell 版本，請將值 `powershell.powerShellDefaultVersion` 設定為工作階段功能表中所顯示的文字 (亦稱為 `versionName`)：

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],

    "powershell.powerShellDefaultVersion": "Downloaded PowerShell",

    // other settings...
}
```

當完成此設定之後，請重新啟動 Visual Studio Code，或從 命令選擇區  重新載入目前的 Visual Studio Code 視窗，並輸入 **Developer:** 重新載入視窗。

如果您開啟工作階段功能表，現在將會看到您其他的 PowerShell 版本！

> [!NOTE]
> 如果您從來源建置 PowerShell，則這是最適合用來測試 PowerShell 本機組建的方式。

### <a name="using-an-older-version-of-the-powershell-extension-for-windows-powershell-v3-and-v4"></a>針對 Windows PowerShell v3 與 v4 使用較舊版本的 PowerShell 延伸模組

目前的 PowerShell 擴充功能不支援 [PowerShell v3 與 v4][i1310]。 不過，您可以使用支援 PowerShell v3 與 v4 的最新版擴充功能。

> [!CAUTION]
> 這個較舊版本的延伸模組不會有額外的修正程式。 其是以「現況」提供，但如果您仍在使用 Windows PowerShell v3 與 Windows PowerShell v4，則可以加以使用。

首先，開啟 [延伸模組] 窗格，然後搜尋 `PowerShell`。 然後按一下齒輪，並選取 [安裝其他版本]  。

![安裝其他版本...](media/using-vscode/install-another-version.png)

然後選取 **2020.1.0** 版。 此版本的延伸模組是支援 v3 與 v4 的最後一個版本。 請務必新增下列設定，讓您的擴充功能版本不會自動更新：

```json
{
    "extensions.autoUpdate": false
}
```

**2020.1.0** 版在可預見的未來將能繼續運作。 不過，Visual Studio Code 可能會實作變更，使此版本的擴充功能中斷。 基於此原因，且由於支援不足，我們建議：

- 升級至 Windows PowerShell 5.1
- 安裝 PowerShell 7，這是 Windows PowerShell 的並存安裝，而且與 PowerShell 擴充功能搭配使用效果最佳

## <a name="debugging-with-visual-studio-code"></a>使用 Visual Studio Code 偵錯

### <a name="no-workspace-debugging"></a>無工作區偵錯

在 Visual Studio Code 1.9 版 (或更新版本) 中，您可以對 PowerShell 指令碼進行偵錯，而無須開啟包含 PowerShell 指令碼的資料夾。

1. 以 [檔案] > [開啟檔案]  開啟 PowerShell 指令碼檔案
1. 設定中斷點 - 選取一行，然後按 <kbd>F9</kbd>
1. 按 <kbd>F5</kbd> 開始偵錯

[偵錯動作] 窗格應該會隨即出現，您可在該窗格中進行偵錯工具、步驟、繼續和停止偵錯。

### <a name="workspace-debugging"></a>工作區偵錯

工作區偵錯是指在從 [檔案]  功能表使用 [開啟資料夾]  所開啟的資料夾內容中進行偵錯。您開啟的資料夾通常是 PowerShell 專案資料夾或 Git 存放庫的根目錄。 工作區偵錯可讓您定義多個偵錯設定，不只是針對目前開啟的檔案進行偵錯。

請遵循這些步驟建立偵錯設定檔：

1. 按下 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd> 以開啟 [偵錯]  檢視。 若為 macOS，請按下 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>。
1. 按一下 [建立 launch.json 檔案]  連結。
1. 從 [選取環境]  提示中，選擇 [PowerShell]  。
1. 選擇您要使用的偵錯類型：

   - **啟動目前的檔案** - 在目前作用中的編輯器視窗中啟動檔案及對檔案進行偵錯。
   - **啟動指令碼** -啟動和偵錯指定的檔案或命令
   - **互動式工作階段** - 從整合式主控台執行的偵錯命令
   - **附加** - 將偵錯工具附加至執行中的 PowerShell 主機處理程序

Visual Studio Code 會在工作區資料夾的根目錄中建立目錄與檔案 `.vscode\launch.json`，以儲存偵錯設定。 如果檔案是在 Git 存放庫中，您通常要修訂 `launch.json` 檔案。 `launch.json` 檔案的內容如下：

```json
{
  "version": "0.2.0",
  "configurations": [
      {
          "type": "PowerShell",
          "request": "launch",
          "name": "PowerShell Launch (current file)",
          "script": "${file}",
          "args": [],
          "cwd": "${file}"
      },
      {
          "type": "PowerShell",
          "request": "attach",
          "name": "PowerShell Attach to Host Process",
          "processId": "${command.PickPSHostProcess}",
          "runspaceId": 1
      },
      {
          "type": "PowerShell",
          "request": "launch",
          "name": "PowerShell Interactive Session",
          "cwd": "${workspaceRoot}"
      }
  ]
}
```

此檔案表示常見的偵錯案例。 當在編輯器中開啟這個檔案時，您會看到 [新增設定...]  按鈕。 您可以按一下此按鈕來新增多個 PowerShell 偵錯設定。 PowerShell: **啟動指令碼**是可以新增的方便設定。 使用此設定時，您可以指定包含選擇性引數的檔案，無論編輯器中當時作用中的是哪個檔案，只要按下 <kbd>F5</kbd> 就會加以使用。

建立偵錯設定之後，您可以選取在偵錯工作階段期間想要使用的設定。 從 [偵錯]  檢視工具列的 [偵錯設定] 下拉式清單中選取設定。

## <a name="troubleshooting-the-powershell-extension-for-visual-studio-code"></a>針對適用於 Visual Studio Code 的 PowerShell 延伸模組進行疑難排解

如果您使用 Visual Studio Code 進行 PowerShell 指令碼開發時遇到任何問題，請參閱 GitHub 上的[疑難排解指南][troubleshooting]。

## <a name="useful-resources"></a>有用的資源

有幾個影片和部落格文章可以協助您開始使用適用於 Visual Studio Code 的 PowerShell 延伸模組：

### <a name="videos"></a>影片

- [使用 Visual Studio Code 作為您的預設 PowerShell 編輯器](https://youtu.be/bGn45vIeAMM)
- [Visual Studio Code：深入探討針對您的 PowerShell 指令碼進行偵錯](https://youtu.be/cSbIXmlkr8o)

### <a name="blog-posts"></a>部落格文章

- [PowerShell 延伸模組][pscdn]
- [在 Visual Studio Code 中撰寫和偵錯 PowerShell 指令碼][debug]
- [偵錯 Visual Studio Code 指引][psdbgblog]
- [在 Visual Studio Code 中偵錯 PowerShell][psdbg-gh]
- [開始使用 Visual Studio Code 中的 PowerShell 開發][getting-started]
- [適用於 PowerShell 開發的 Visual Studio Code 編輯功能 – 第 1 部分][editing-part1]
- [適用於 PowerShell 開發的 Visual Studio Code 編輯功能 – 第 2 部分][editing-part2]
- [在 Visual Studio Code 中偵錯 PowerShell 指令碼 – 第 1 部分][debugging-part1]
- [在 Visual Studio Code 中偵錯 PowerShell 指令碼 – 第 2 部分][debugging-part2]

## <a name="powershell-extension-project-source-code"></a>PowerShell 擴充功能專案原始程式碼

[GitHub][psext-src] 上可以找到 PowerShell 延伸模組的原始程式碼。

如果您對參與感興趣，非常歡迎您建立提取要求。 請依照 GitHub 上的[開發人員文件][dev-docs]開始使用。

<!-- related articles -->
[ise]:                    ../../windows-powershell/ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:   ../../install/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:   ../../install/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../install/Installing-PowerShell-Core-on-Windows.md
[install-winps]:          ../../install/Installing-Windows-PowerShell.md
[file-encoding]:          understanding-file-encoding.md
[vsc-ise]:                How-To-Replicate-the-ISE-Experience-In-VSCode.md

<!-- blogs -->
[debug]:                  https://devblogs.microsoft.com/powershell/announcing-powershell-language-support-for-visual-studio-code-and-more/
[debugging-part1]:        https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]:        https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-2/
[editing-part1]:          https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]:          https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-2/
[getting-started]:        https://devblogs.microsoft.com/scripting/get-started-with-powershell-development-in-visual-studio-code/
[psdbgblog]:              https://johnpapa.net/debugging-with-visual-studio-code/
[psdbg-gh]:               https://github.com/PowerShell/vscode-powershell/tree/master/examples
[pscdn]:                  https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/

<!-- issues -->
[GitHub 問題]:          https://github.com/PowerShell/vscode-powershell/issues
[i1310]:                  https://github.com/PowerShell/vscode-powershell/issues/1310
[i606]:                   https://github.com/PowerShell/vscode-powershell/issues/606

<!-- product links -->
[Visual Studio]:          https://visualstudio.microsoft.com/
[vscode]:                 https://code.visualstudio.com/
[psext]:                  https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell
[vsc-settings]:           https://code.visualstudio.com/docs/getstarted/settings
[vsc-setup]:              https://code.visualstudio.com/Docs/setup/setup-overview
[vsc-setup-win]:          https://code.visualstudio.com/docs/setup/windows
[vsc-setup-macos]:        https://code.visualstudio.com/docs/setup/mac
[vsc-setup-linux]:        https://code.visualstudio.com/docs/setup/linux
[psext-src]:              https://github.com/PowerShell/vscode-powershell
[troubleshooting]:        https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md
[dev-docs]:               https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md
