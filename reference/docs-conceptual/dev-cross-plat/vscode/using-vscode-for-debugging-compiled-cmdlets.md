---
ms.date: 10/19/2020
keywords: powershell,cmdlet,debug
title: 使用 Visual Studio Code 對已編譯的 Cmdlet 進行偵錯
description: 如何在 .NET Core 中為 PSModule 專案設定建置工作與啟動組態
ms.openlocfilehash: b51a69110c64b386f5c3ccf2527d1e184ef89257
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501638"
---
# <a name="using-visual-studio-code-to-debug-compiled-cmdlets"></a>使用 Visual Studio Code 對已編譯的 Cmdlet 進行偵錯

本指南會示範如何使用 Visual Studio Code (VS Code) 與 C# 延伸模組，以互動方式針對已編譯 PowerShell 模組的 C# 原始程式碼進行偵錯。

您應已熟悉 Visual Studio Code 偵錯工具。

- 如需 VS Code 偵錯工具的一般簡介，請參閱[在 Visual Studio Code 中進行偵錯][]。

- 如需對 PowerShell 指令檔與模組進行偵錯的範例，請參閱[使用 Visual Studio Code 進行遠端編輯與偵錯][]。

本指南假設您已閱讀並遵循[撰寫可移植的模組][]指南中的指示。

## <a name="creating-a-build-task"></a>建立建置工作

在啟動偵錯工作階段之前，自動建置您的專案。 重建可確保您對最新版本的程式碼進行偵錯。

設定建置工作：

1. 在 [命令選擇區]中，執行 [設定預設建置工作] 命令。

   ![執行 [設定預設建置工作]](media/using-vscode-for-debugging-compiled-cmdlets/configure-default-build-task.png)

1. 在 [選取要設定的工作] 對話方塊中，選擇 [從範本建立 tasks.json 檔案]。

1. 在 [選取工作範本] 對話方塊中，選擇 [.NET Core]。

若 `tasks.json` 檔案尚不存在，則會建立新的。

若要測試您的建置工作：

1. 在 [命令選擇區]中，執行 [執行建置工作] 命令。

1. 在 [選取要執行的建置工作] 對話方塊中，選擇 [建置]。

### <a name="information-about-dll-files-being-locked"></a>DLL 檔案鎖定的相關資訊

根據預設，成功的組建不會在終端機窗格中顯示輸出。 若您看到輸出包含文字 **專案檔不存在** ，則您應該編輯 `tasks.json` 檔案。 包含 C# 專案的明確路徑，表示為 `"${workspaceFolder}/myModule"`。 在此範例中，`myModule` 為專案資料夾的名稱。 此項目必須在 `args` 清單中的 `build` 項目之後，如下所示：

```json
    {
        "label": "build",
        "command": "dotnet",
        "type": "shell",
        "args": [
            "build",
            "${workspaceFolder}/myModule",
            // Ask dotnet build to generate full paths for file names.
            "/property:GenerateFullPaths=true",
            // Do not generate summary otherwise it leads to duplicate errors in Problems panel
            "/consoleloggerparameters:NoSummary",
        ],
        "group": "build",
        "presentation": {
            "reveal": "silent"
        },
        "problemMatcher": "$msCompile"
    }
```

在進行偵錯時，您的模組 DLL 會匯入 VS Code 終端機的 PowerShell 工作階段中。 DLL 的狀態會變為鎖定。 當您執行建置工作而不關閉終端機工作階段時，就會顯示下列訊息：

```Output
Could not copy "obj\Debug\netstandard2.0\myModule.dll" to "bin\Debug\netstandard2.0\myModule.dll"`.
```

您必須先關閉終端機工作階段，再進行重建。

## <a name="setting-up-the-debugger"></a>設定偵錯工具

若要對 PowerShell Cmdlet 進行偵錯，您必須設定自訂啟動組態。 此組態是用來：

- 建置您的原始程式碼
- 在載入模組後啟動 PowerShell
- 讓 PowerShell 在終端機窗格中保持開啟

當您在終端機工作階段中叫用您的 Cmdlet 時，偵錯工具即會在原始程式碼中設定的所有中斷點上停止。

### <a name="configuring-launchjson-for-powershell-core"></a>設定 PowerShell Core 的 launch.json

1. 安裝 [C# for Visual Studio Code][] 延伸模組

1. 在 [偵錯] 窗格中，新增偵錯組態

1. 在 [`Select environment`] 對話方塊中，選擇 [`.NET Core`]

1. `launch.json` 檔案隨即會在編輯器中開啟。 當您的游標位於 `configurations` 陣列內時，您會看到 `configuration` 選擇器。 若您看不到此清單，請選取 [新增組態]。

1. 若要建立預設的偵錯組態，請選取 [啟動 .NET Core 主控台應用程式]：

   ![啟動 .NET Core 主控台應用程式](media/using-vscode-for-debugging-compiled-cmdlets/add-configuration-dialog.png)

1. 編輯 `name`、`program`、`args` 及 `console` 欄位，如下所示：

   ```json
    {
        "name": "PowerShell cmdlets: pwsh",
        "type": "coreclr",
        "request": "launch",
        "preLaunchTask": "build",
        "program": "pwsh",
        "args": [
            "-NoExit",
            "-NoProfile",
            "-Command",
            "Import-Module ${workspaceFolder}/myModule/bin/Debug/netstandard2.0/myModule.dll",
        ],
        "cwd": "${workspaceFolder}",
        "stopAtEntry": false,
        "console": "integratedTerminal"
    }
   ```

`program` 欄位可用來啟動 `pwsh`，以便能夠執行正在偵錯的 Cmdlet。 `-NoExit` 引數會在模組匯入之後，使 PowerShell 工作階段保持開啟。
在您遵循[撰寫可移植的模組][]指南後，`Import-Module` 引數中的路徑即為預設的建置輸出路徑。 若您已建立模組資訊清單 (`.psd1` 檔案)，您應該改為使用該清單的路徑。 `/` 路徑分隔符號適用於 Windows、Linux 以及 macOS。 您必須使用整合式終端機，來執行要對其偵錯的 PowerShell 命令。

> [!NOTE]
> 若偵錯工具未在任何中斷點停止，請在 Visual Studio Code 偵錯主控台中找出下列描述：
>
> ```
> Loaded '/path/to/myModule.dll'. Skipped loading symbols. Module is optimized and the debugger option 'Just My Code' is enabled.
> ```
>
> 若您看到此描述，請將 `"justMyCode": false` 新增至您的啟動組態 (與 `"console": "integratedTerminal"` 相同的層級)。

### <a name="configuring-launchjson-for-windows-powershell"></a>設定 Windows PowerShell 的 launch.json

此啟動組態適用於在 Windows PowerShell (`powershell.exe`) 中測試 Cmdlet。
建立第二個啟動組態，並進行下列變更：

1. `name` 應該是 `PowerShell cmdlets: powershell`

1. `type` 應該是 `clr`

1. `program` 應該是 `powershell`

   其看起來應該如下：

   ```json
    {
        "name": "PowerShell cmdlets: powershell",
        "type": "clr",
        "request": "launch",
        "preLaunchTask": "build",
        "program": "powershell",
        "args": [
            "-NoExit",
            "-NoProfile",
            "-Command",
            "Import-Module ${workspaceFolder}/myModule/bin/Debug/netstandard2.0/myModule.dll",
        ],
        "cwd": "${workspaceFolder}",
        "stopAtEntry": false,
        "console": "integratedTerminal"
    }
   ```

## <a name="launching-a-debugging-session"></a>啟動偵錯工作階段

現在一切都已準備完成，可開始進行偵錯。

- 將中斷點置於欲進行偵錯之 Cmdlet 的原始程式碼中：

  ![中斷點會顯示為裝訂邊中的紅點](media/using-vscode-for-debugging-compiled-cmdlets/set-breakpoint.png)

- 請確定已在 [偵錯] 檢視的 [組態] 下拉式功能表中，選取相關的 [PowerShell Cmdlet] 組態：

  ![選取 [啟動組態]](media/using-vscode-for-debugging-compiled-cmdlets/select-launch-configuration.png)

- 按 <kbd>F5</kbd>，或按一下 [開始偵錯] 按鈕

- 切換至終端機窗格，並叫用您的 Cmdlet：

  ![叫用 Cmdlet](media/using-vscode-for-debugging-compiled-cmdlets/invoke-the-cmdlet.png)

- 執行會在中斷點停止：

  ![執行會在中斷點終止](media/using-vscode-for-debugging-compiled-cmdlets/stopped-at-breakpoint.png)

您可以逐步執行原始程式碼、檢查變數，並檢查呼叫堆疊。

若要結束偵錯，請按一下 [偵錯] 工具列中的 [停止]，或按 <kbd>Shift</kbd>-<kbd>F5</kbd>。 用來進行偵錯的殼層會隨即結束，並解除鎖定已編譯的 DLL 檔案。

<!-- reference links -->
[在 Visual Studio Code 中偵錯]: https://code.visualstudio.com/docs/editor/debugging
[使用 Visual Studio Code 來進行遠端編輯與偵錯]: using-vscode-for-remote-editing-and-debugging.md
[撰寫可移植的模組]: ../writing-portable-modules.md
[C# for Visual Studio Code]: https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp
