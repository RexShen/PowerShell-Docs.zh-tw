---
title: 使用 Visual Studio Code 開發 PowerShell
description: 使用 Visual Studio Code 開發 PowerShell
ms.date: 08/06/2018
ms.openlocfilehash: 3101fa57896996a696385801303333e4a6406d20
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400639"
---
# <a name="using-visual-studio-code-for-powershell-development"></a>使用 Visual Studio Code 開發 PowerShell

除了 [PowerShell ISE][ise] 之外，PowerShell 在 Visual Studio Code 中也受到良好支援。
而且，雖然所有平台 (Windows、macOS 和 Linux) 上的 PowerShell Core 都支援 Visual Studio Code，但 PowerShell Core 不支援 ISE

使用 Windows 10 或安裝適用於低階 Windows 作業系統 (例如 Windows 8.1 等) 的 [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395)，即可以在 Windows 上使用 Visual Studio Code 與 PowerShell 第 5 版。

啟動它之前，請先確定系統上有 PowerShell。
若為 Windows、macOS 和 Linux 上的新型工作負載，請參閱：

- [在 Linux 上安裝 PowerShell Core][install-pscore-linux]
- [在 macOS 上安裝 PowerShell Core][install-pscore-macos]
- [在 Windows 上安裝 PowerShell Core][install-pscore-windows]

若為傳統的 Windows PowerShell 工作負載，請參閱[安裝 Windows PowerShell][install-winps]。

## <a name="editing-with-visual-studio-code"></a>使用 Visual Studio Code 編輯

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[1.安裝 Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview)

- **Linux**：遵循 [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) (在 Linux 上執行 VS Code) 頁面的安裝指示操作

- **macOS**：遵循 [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) (在 macOS 上執行 VS Code) 頁面的安裝指示操作

  > [!IMPORTANT]
  > 在 macOS 上，您必須安裝 OpenSSL，PowerShell 延伸模組才能正常運作。
  > 完成這項作業最簡單的方式是安裝 [Homebrew](https://brew.sh/) ，然後執行 `brew install openssl`。
  > VS Code 現在可以成功載入 PowerShell 延伸模組。

- **Windows**：遵循 [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) (在 Windows 上執行 VS Code) 頁面的安裝指示操作

### <a name="2-installing-powershell-extension"></a>2.安裝 PowerShell 延伸模組

- 啟動 Visual Studio Code 應用程式：
  - **Windows**：在您的 PowerShell 工作階段鍵入 `code`
  - **Linux**：在您的終端機上鍵入 `code`
  - **macOS**：在您的終端機上鍵入 `code`

- 按 **Ctrl+P** (Mac 是 **Cmd+P**) 啟動 [快速開啟]。
- 在 [快速開啟] 中鍵入 `ext install powershell` 並點擊 **Enter**。
- 提要欄位上隨即開啟 [延伸模組] 檢視。 從 Microsoft 選取 PowerShell 延伸模組。
  您應該會看到類似如下的畫面︰

  ![VSCode](../../images/vscode.png)

- 從 Microsoft 按一下 PowerShell 延伸模組的 [安裝] 按鈕。
- 安裝之後，您會看到 [安裝] 按鈕變成 [重新載入]。
  按一下 [重新載入]。
- 重新載入 Visual Studio Code 之後，就可以進行編輯。

例如，若要建立新的檔案，按一下 [檔案]->[新增]。
若要儲存它，按一下 [檔案]->[儲存]，然後提供檔案名稱，例如 `HelloWorld.ps1`。
若要關閉檔案，請按一下檔案名稱旁邊的 "x"。
若要結束 Visual Studio Code，[檔案]->[結束]。

#### <a name="using-a-specific-installed-version-of-powershell"></a>使用 PowerShell 的特定安裝版本

如果您想要搭配使用特定安裝的 PowerShell 與 Visual Studio Code，則必須在使用者設定檔中新增變數。

1. 按一下 [檔案]-> [喜好設定]-> [設定]
1. 隨即出現兩個編輯器窗格。
   在最右邊的窗格中 (`settings.json`)，在兩個大括弧中間 (`{`和`}`) 插入下列適用於您作業系統的設定，並使用所安裝 PowerShell 的版本來取代 **\<version\>**：

   ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
   ```

1. 以所需 PowerShell 可執行檔的路徑取代設定
1. 儲存設定檔並重新啟動 Visual Studio Code

#### <a name="configuration-settings-for-visual-studio-code"></a>Visual Studio Code 的組態設定

使用先前段落中的步驟，您可以在 `settings.json` 中新增組態設定。

我們建議下列 Visual Studio Code 組態設定：

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true
}
```

## <a name="debugging-with-visual-studio-code"></a>使用 Visual Studio Code 偵錯

### <a name="no-workspace-debugging"></a>無工作區偵錯

使用 Visual Studio Code 1.9 版可以偵錯 PowerShell 指令碼，不必開啟包含 PowerShell 指令碼的資料夾。
只要以 [檔案]->[開啟檔案...] 開啟 PowerShell 指令碼檔案，在行中設定中斷點 (按 F9)，然後按 F5 啟動偵錯。
您會看到 [偵錯動作] 窗格出現，其可讓您中斷偵錯工具、中斷步驟、繼續和停止偵錯。

### <a name="workspace-debugging"></a>工作區偵錯

工作區偵錯是指使用 [檔案] 功能表的 [開啟資料夾...]，在 Visual Studio Code 已開啟的資料夾內容中偵錯。
您開啟的資料夾通常是 PowerShell 專案資料夾及/或 Git 存放庫的根目錄。

即使在此模式中，只要按下 F5 就可以開始偵錯目前選取的 PowerShell 指令碼。
不過，工作區偵錯可讓您定義多個偵錯設定，不只是偵錯目前開啟的檔案。
例如，您可以新增設定以：

- 啟動偵錯工具中的 Pester 測試
- 以偵錯工具中的引數啟動特定檔案
- 啟動偵錯工具中的互動式工作階段
- 將偵錯工具附加至 PowerShell 主機處理程序

請遵循下列步驟建立您的偵錯設定檔：

  1. 按 **Ctrl+Shift+D** (Mac 是 **Cmd+Shift+D**) 開啟 [偵錯] 檢視。
  2. 按工具列中的**設定**齒輪圖示。
  3. Visual Studio Code 會提示您 [選取環境]。 選擇 [PowerShell]。

  當您這樣做時，Visual Studio Code 會在工作區資料夾的根目錄中建立目錄和檔案：".vscode\launch.json"。
  這是儲存偵錯設定的位置。 如果檔案是在 Git 存放庫中，您通常要修訂 launch.json 檔案。
  Launch.json 檔案的內容如下：

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

  這表示常見的偵錯案例。
  不過，當您在編輯器中開啟這個檔案時，您會看到 [新增設定] 按鈕。
  您可以按此按鈕新增多個 PowerShell 偵錯設定。 一個好用的設定，以新增**PowerShell:啟動指令碼**。
  使用此設定時，您可以指定有選擇性引數的特定檔案，只要按下 F5 就應該啟動，無論編輯器中當時作用的是哪個檔案。

  建立偵錯設定之後，您就可以從 [偵錯] 檢視工具列的偵錯設定下拉式清單中擇一，選取在偵錯工作階段期間想要使用的設定。

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
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../setup/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://blogs.msdn.microsoft.com/powershell/2015/11/16/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://blogs.technet.microsoft.com/heyscriptingguy/2016/12/05/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/11/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/12/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/06/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/13/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-visual-studio-code"></a>適用於 Visual Studio Code 的 PowerShell 延伸模組

[GitHub](https://github.com/PowerShell/vscode-powershell) 上可以找到 PowerShell 延伸模組的原始程式碼。
