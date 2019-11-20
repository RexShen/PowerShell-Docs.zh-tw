---
title: 使用 Visual Studio Code 開發 PowerShell
description: 使用 Visual Studio Code 開發 PowerShell
ms.date: 11/07/2019
ms.openlocfilehash: 4f197e71d3b79828f466584f5d862415726818b1
ms.sourcegitcommit: a6e54a305fdeb6482321c77da8066d2f991c93e1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2019
ms.locfileid: "74117392"
---
# <a name="using-visual-studio-code-for-powershell-development"></a>使用 Visual Studio Code 開發 PowerShell

除了 [PowerShell ISE][ise] 之外，PowerShell 在 Visual Studio Code (VSCode) 中也受到良好支援。 雖然 PowerShell Core 不支援 ISE，但這些平台上的 PowerShell Core 都支援 VSCode：Windows、macOS 和 Linux。

使用 Windows 10 或安裝適用於低階 Windows 作業系統 (例如 Windows 8.1) 的 Windows Management Framework 5.1，即可以在 Windows 上使用 VSCode 與 PowerShell 第 5 版。 如需詳細資訊，請參閱[安裝與設定 WMF 5.1](/powershell/scripting/wmf/setup/install-configure)。

在開始前，請先確定系統上有 PowerShell。 如需 Windows、macOS 和 Linux 上的新型工作負載，請參閱下列連結：

- [在 Linux 上安裝 PowerShell Core][install-pscore-linux]
- [在 macOS 上安裝 PowerShell Core][install-pscore-macos]
- [在 Windows 上安裝 PowerShell Core][install-pscore-windows]

若為傳統的 Windows PowerShell 工作負載，請參閱[安裝 Windows PowerShell][install-winps]。

## <a name="editing-with-vscode"></a>使用 VSCode 編輯

1. 安裝 VSCode。 如需詳細資訊，請參閱 [Setting up Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview) (設定 Visual Studio Code) 概觀。

   下列為每個平台的安裝指示：

   - **Linux**：請遵循 [Running VSCode on Linux在](https://code.visualstudio.com/docs/setup/linux) ( Linux 上執行 VS Code) 頁面的安裝指示。
   - **macOS**：請遵循 [Running VSCode on macOS](https://code.visualstudio.com/docs/setup/mac) (在 macOS 上執行 VS Code) 頁面的安裝指示。

     > [!IMPORTANT]
     > 在 macOS 上，您必須安裝 OpenSSL，PowerShell 延伸模組才能正常運作。 完成這項作業最簡單的方式是安裝 [Homebrew](https://brew.sh/) ，然後執行 `brew install openssl`。 VSCode 現在可以成功載入 PowerShell 延伸模組。

   - **Windows**：請遵循 [Running VSCode on Windows](https://code.visualstudio.com/docs/setup/windows) (在 Windows 上執行 VS Code) 頁面的安裝指示。

1. 安裝 PowerShell 延伸模組。

   1. 啟動 VSCode 應用程式，方法是：
      - **Windows**：在您的 PowerShell 工作階段鍵入 `code`
      - **Linux**：在您的終端機上鍵入 `code`
      - **macOS**：在您的終端機上鍵入 `code`
   1. 按下 <kbd>Ctrl</kbd>+<kbd>P</kbd> 來啟動 Windows 或 Linux 上的 **Quick Open**。 針對 macOS，則按下 <kbd>Cmd</kbd>+<kbd>P</kbd>。
   1. 在 Quick Open 中，鍵入 `ext install powershell`，然後按下 [輸入]  。
   1. 提要欄位上隨即開啟 [延伸模組]  檢視。 從 Microsoft 選取 PowerShell 延伸模組。
      您應該會看到類似下圖的 VSCode 畫面：

      ![VSCode](../../images/using-vscode/vscode.png)

   1. 從 Microsoft 按一下 PowerShell 延伸模組的 [安裝]  按鈕。
   1. 安裝之後，您會看到 [安裝]  按鈕變成 [重新載入]  。 按一下 [重新載入]  。
   1. 重新載入 VSCode 之後，即可進行編輯。

例如，若要建立新的檔案，請按一下 [檔案] > [新增]  。 若要儲存，請按一下 [檔案] > [儲存]  ，然後提供檔案名稱，例如 `HelloWorld.ps1`。 若要關閉檔案，請按一下檔案名稱旁邊的 `X`。 若要結束 VSCode，請按一下 [檔案] > [結束]  。

### <a name="installing-the-powershell-extension-on-restricted-systems"></a>在受限制的系統上安裝 PowerShell 延伸模組

某些系統已設定為需要檢查所有程式碼簽章，且必須以手動方式核准 PowerShell Editor Services，才能在系統上執行。 如果已經安裝 PowerShell 延伸模組，但發生下列錯誤，則可能原因是變更執行原則的群組原則更新：

```
Language server startup failed.
```

若要手動核准 PowerShell Editor Services 以及適用於 VSCode 的 PowerShell 延伸模組，請開啟 PowerShell 提示字元並執行下列命令：

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

系統會提示您**要執行來自這個不受信任的發行者的軟體嗎？** 輸入 `A` 以執行檔案。 然後，開啟 VSCode 並檢查 PowerShell 延伸模組是否正常運作。 如果您仍有關於開始使用的問題，請透過 [GitHub](https://github.com/PowerShell/vscode-powershell/issues) \(英文\) 讓我們知道。

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a>選擇要與擴充功能搭配使用的 PowerShell 版本

透過與 Windows PowerShell 並存安裝的 PowerShell Core，其現在能夠將特定版本的 PowerShell 與 PowerShell 延伸模組搭配使用。 使用下列步驟來選擇版本：

1. 按下 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> 來開啟 Windows 或 Linux 上的 [命令選擇區]  。 若為 macOS，請按下 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>。
1. 搜尋**工作階段**。
1. 按一下 [PowerShell:  顯示工作階段功能表]。
1. 從清單中選擇要使用的 PowerShell 版本，例如：**PowerShell Core**。

> [!IMPORTANT]
> 此功能會查看不同作業系統上的一些已知路徑，以探索 PowerShell 的安裝位置。 如果您已將 PowerShell 安裝到非典型位置，則它一開始可能不會顯示於工作階段功能表中。 您可以藉由[新增自己的自訂路徑](#adding-your-own-powershell-paths-to-the-session-menu)來擴充工作階段功能表，如下所述。

>[!NOTE]
> 還有另一種方式可前往工作階段功能表。 在您的編輯器中開啟 PowerShell 檔案時，您會在右下角看到綠色的版本號碼。 按一下此版本號碼，即會帶您前往工作階段功能表。

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a>將您自己的 PowerShell 路徑新增至工作階段功能表

您可以透過 VSCode 設定，將其他 PowerShell 可執行檔路徑新增至工作階段功能表。

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

* `exePath`:`pwsh` 或 `powershell` 可執行檔的路徑。
* `versionName`:將顯示於工作階段功能表中的文字。

您可以將此文字設定為要顯示於工作階段功能表 (也稱為最後一個設定中的 `versionName`) 中的文字，藉以使用 `powershell.powerShellDefaultVersion` 設定來設定要使用的預設 PowerShell 版本：

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

當完成此設定之後，請重新開機 VSCode，或從 [命令選擇區]  重新載入目前的 VSCode 視窗，並鍵入 [Developer:  重新載入視窗]。

如果您開啟工作階段功能表，現在將會看到您其他的 PowerShell 版本！

> [!NOTE]
> 如果您從來源建置 PowerShell，則這是最適合用來測試 PowerShell 本機組建的方式。

### <a name="configuration-settings-for-vscode"></a>編輯 VSCode 組態設定

使用先前段落中的步驟，您可以在 `settings.json` 中新增組態設定。

我們建議下列 VSCode 組態設定：

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

如果您不希望這些設定影響所有的檔案類型，VSCode 也允許依照語言的設定。 將設定放入 `[<language-name>]` 欄位，建立語言特定設定。 例如：

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

如需 VSCode 中檔案編碼的詳細資訊，請參閱[了解檔案編碼](understanding-file-encoding.md)。

## <a name="debugging-with-vscode"></a>使用 VSCode 進行偵錯

### <a name="no-workspace-debugging"></a>無工作區偵錯

使用 VSCode 1.9 版可以對 PowerShell 指令碼進行偵錯，而無須開啟包含 PowerShell 指令碼的資料夾。 以 [檔案] > [開啟檔案...]  開啟 PowerShell 指令碼檔案，在行上設定中斷點，依序按下 <kbd>F9</kbd> 和 <kbd>F5</kbd> 來開始偵錯。 [偵錯動作] 窗格應該會隨即出現，您可在該窗格中進行偵錯工具、步驟、繼續和停止偵錯。

### <a name="workspace-debugging"></a>工作區偵錯

工作區偵錯是指使用 [開啟資料夾...]  來在 [檔案]  功能表的 Visual Studio Code 中對已開啟的資料夾內容進行偵錯。您開啟的資料夾通常是 PowerShell 專案資料夾及/或 Git 存放庫的根目錄。

即使在此模式中，只要按下 <kbd>F5</kbd> 就可以開始針對目前選取的 PowerShell 指令碼進行偵錯。 不過，工作區偵錯可讓您定義多個偵錯設定，不只是偵錯目前開啟的檔案。 例如，您可以新增設定以：

- 啟動偵錯工具中的 Pester 測試。
- 以偵錯工具中的引數啟動特定檔案。
- 啟動偵錯工具中的互動式工作階段。
- 將偵錯工具附加至 PowerShell 主機處理程序。

請遵循下列步驟建立您的偵錯設定檔：

  1. 按下 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd> 以開啟 [偵錯]  檢視。 若為 macOS，請按下 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>。
  1. 按一下工具列中的**設定**齒輪圖示。
  1. VSCode 會提示您 [選取環境]  。 選擇 [PowerShell]  。

接著 VSCode 會在工作區資料夾的根目錄中建立目錄和檔案 `.vscode\launch.json`。 該位置為儲存偵錯設定的位置。 如果檔案是在 Git 存放庫中，您通常要修訂 `launch.json` 檔案。 `launch.json` 檔案的內容如下：

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

此檔案表示常見的偵錯案例。 當在編輯器中開啟這個檔案時，您會看到 [新增設定...]  按鈕。 您可以按一下此按鈕來新增多個 PowerShell 偵錯設定。 PowerShell: **啟動指令碼**是可以新增的方便設定。 使用此設定時，您可以指定有選擇性引數的檔案，無論編輯器中當時作用中的是哪個檔案，只要按下 <kbd>F5</kbd> 應該就會啟動。

建立偵錯設定之後，您可以選取在偵錯工作階段期間想要使用的設定。 從 [偵錯]  檢視工具列的 [偵錯設定] 下拉式清單中選取設定。

有幾個部落格可以協助您開始使用適用於 Visual Studio Code 的 PowerShell 擴充功能：

- [PowerShell 延伸模組][ps-extension]
- [在 Visual Studio Code 中撰寫和偵錯 PowerShell 指令碼][debug]
- [偵錯 Visual Studio Code 指引][vscode-guide]
- [在 Visual Studio Code 中偵錯 PowerShell][ps-vscode]
- [開始使用 Visual Studio Code 中的 PowerShell 開發][getting-started]
- [適用於 PowerShell 開發的 Visual Studio Code 編輯功能 – 第 1 部分][editing-part1]
- [適用於 PowerShell 開發的 Visual Studio Code 編輯功能 – 第 2 部分][editing-part2]
- [在 Visual Studio Code 中偵錯 PowerShell 指令碼 – 第 1 部分][debugging-part1]
- [在 Visual Studio Code 中偵錯 PowerShell 指令碼 – 第 2 部分][debugging-part2]

[ise]: ../ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:  ../../install/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../install/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../install/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../install/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://devblogs.microsoft.com/powershell/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://devblogs.microsoft.com/scripting/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-vscode"></a>適用於 VSCode 的 PowerShell 延伸模組

[GitHub](https://github.com/PowerShell/vscode-powershell) 上可以找到 PowerShell 延伸模組的原始程式碼。
