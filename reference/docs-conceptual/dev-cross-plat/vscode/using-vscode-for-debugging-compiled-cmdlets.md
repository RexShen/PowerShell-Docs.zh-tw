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
# <a name="using-visual-studio-code-to-debug-compiled-cmdlets"></a><span data-ttu-id="b9ba8-104">使用 Visual Studio Code 對已編譯的 Cmdlet 進行偵錯</span><span class="sxs-lookup"><span data-stu-id="b9ba8-104">Using Visual Studio Code to debug compiled cmdlets</span></span>

<span data-ttu-id="b9ba8-105">本指南會示範如何使用 Visual Studio Code (VS Code) 與 C# 延伸模組，以互動方式針對已編譯 PowerShell 模組的 C# 原始程式碼進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-105">This guide shows you how to interactively debug C# source code for a compiled PowerShell module using Visual Studio Code (VS Code) and the C# extension.</span></span>

<span data-ttu-id="b9ba8-106">您應已熟悉 Visual Studio Code 偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-106">Some familiarity with the Visual Studio Code debugger is assumed.</span></span>

- <span data-ttu-id="b9ba8-107">如需 VS Code 偵錯工具的一般簡介，請參閱[在 Visual Studio Code 中進行偵錯][]。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-107">For a general introduction to the VS Code debugger, see [Debugging in Visual Studio Code][].</span></span>

- <span data-ttu-id="b9ba8-108">如需對 PowerShell 指令檔與模組進行偵錯的範例，請參閱[使用 Visual Studio Code 進行遠端編輯與偵錯][]。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-108">For examples of debugging PowerShell script files and modules, see [Using Visual Studio Code for remote editing and debugging][].</span></span>

<span data-ttu-id="b9ba8-109">本指南假設您已閱讀並遵循[撰寫可移植的模組][]指南中的指示。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-109">This guide assumes you have read and followed the instructions in the [Writing Portable Modules][] guide.</span></span>

## <a name="creating-a-build-task"></a><span data-ttu-id="b9ba8-110">建立建置工作</span><span class="sxs-lookup"><span data-stu-id="b9ba8-110">Creating a build task</span></span>

<span data-ttu-id="b9ba8-111">在啟動偵錯工作階段之前，自動建置您的專案。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-111">Build your project automatically before launching a debugging session.</span></span> <span data-ttu-id="b9ba8-112">重建可確保您對最新版本的程式碼進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-112">Rebuilding ensures that you debug the latest version of your code.</span></span>

<span data-ttu-id="b9ba8-113">設定建置工作：</span><span class="sxs-lookup"><span data-stu-id="b9ba8-113">Configure a build task:</span></span>

1. <span data-ttu-id="b9ba8-114">在 [命令選擇區]中，執行 [設定預設建置工作] 命令。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-114">In the **Command Palette** , run the **Configure Default Build Task** command.</span></span>

   ![執行 [設定預設建置工作]](media/using-vscode-for-debugging-compiled-cmdlets/configure-default-build-task.png)

1. <span data-ttu-id="b9ba8-116">在 [選取要設定的工作] 對話方塊中，選擇 [從範本建立 tasks.json 檔案]。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-116">In the **Select a task to configure** dialog, choose **Create tasks.json file from template** .</span></span>

1. <span data-ttu-id="b9ba8-117">在 [選取工作範本] 對話方塊中，選擇 [.NET Core]。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-117">In the **Select a Task Template** dialog, choose **.NET Core** .</span></span>

<span data-ttu-id="b9ba8-118">若 `tasks.json` 檔案尚不存在，則會建立新的。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-118">A new `tasks.json` file is created if one doesn't exist yet.</span></span>

<span data-ttu-id="b9ba8-119">若要測試您的建置工作：</span><span class="sxs-lookup"><span data-stu-id="b9ba8-119">To test your build task:</span></span>

1. <span data-ttu-id="b9ba8-120">在 [命令選擇區]中，執行 [執行建置工作] 命令。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-120">In the **Command Palette** , run the **Run Build Task** command.</span></span>

1. <span data-ttu-id="b9ba8-121">在 [選取要執行的建置工作] 對話方塊中，選擇 [建置]。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-121">In the **Select the build task to run** dialog, choose **build** .</span></span>

### <a name="information-about-dll-files-being-locked"></a><span data-ttu-id="b9ba8-122">DLL 檔案鎖定的相關資訊</span><span class="sxs-lookup"><span data-stu-id="b9ba8-122">Information about DLL files being locked</span></span>

<span data-ttu-id="b9ba8-123">根據預設，成功的組建不會在終端機窗格中顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-123">By default, a successful build doesn't show output in the terminal pane.</span></span> <span data-ttu-id="b9ba8-124">若您看到輸出包含文字 **專案檔不存在** ，則您應該編輯 `tasks.json` 檔案。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-124">If you see output that contains the text **Project file doesn't exist** , you should edit the `tasks.json` file.</span></span> <span data-ttu-id="b9ba8-125">包含 C# 專案的明確路徑，表示為 `"${workspaceFolder}/myModule"`。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-125">Include the explicit path to the C# project expressed as `"${workspaceFolder}/myModule"`.</span></span> <span data-ttu-id="b9ba8-126">在此範例中，`myModule` 為專案資料夾的名稱。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-126">In this example, `myModule` is the name of the project folder.</span></span> <span data-ttu-id="b9ba8-127">此項目必須在 `args` 清單中的 `build` 項目之後，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b9ba8-127">This entry must go after the `build` entry in the `args` list as follows:</span></span>

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

<span data-ttu-id="b9ba8-128">在進行偵錯時，您的模組 DLL 會匯入 VS Code 終端機的 PowerShell 工作階段中。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-128">When debugging, your module DLL is imported into the PowerShell session in the VS Code terminal.</span></span> <span data-ttu-id="b9ba8-129">DLL 的狀態會變為鎖定。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-129">The DLL becomes locked.</span></span> <span data-ttu-id="b9ba8-130">當您執行建置工作而不關閉終端機工作階段時，就會顯示下列訊息：</span><span class="sxs-lookup"><span data-stu-id="b9ba8-130">The following message is displayed when you run the build task without closing the terminal session:</span></span>

```Output
Could not copy "obj\Debug\netstandard2.0\myModule.dll" to "bin\Debug\netstandard2.0\myModule.dll"`.
```

<span data-ttu-id="b9ba8-131">您必須先關閉終端機工作階段，再進行重建。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-131">Terminal sessions must be closed before you rebuild.</span></span>

## <a name="setting-up-the-debugger"></a><span data-ttu-id="b9ba8-132">設定偵錯工具</span><span class="sxs-lookup"><span data-stu-id="b9ba8-132">Setting up the debugger</span></span>

<span data-ttu-id="b9ba8-133">若要對 PowerShell Cmdlet 進行偵錯，您必須設定自訂啟動組態。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-133">To debug the PowerShell cmdlet, you need to set up a custom launch configuration.</span></span> <span data-ttu-id="b9ba8-134">此組態是用來：</span><span class="sxs-lookup"><span data-stu-id="b9ba8-134">This configuration is used to:</span></span>

- <span data-ttu-id="b9ba8-135">建置您的原始程式碼</span><span class="sxs-lookup"><span data-stu-id="b9ba8-135">Build your source code</span></span>
- <span data-ttu-id="b9ba8-136">在載入模組後啟動 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b9ba8-136">Start PowerShell with your module loaded</span></span>
- <span data-ttu-id="b9ba8-137">讓 PowerShell 在終端機窗格中保持開啟</span><span class="sxs-lookup"><span data-stu-id="b9ba8-137">Leave PowerShell open in the terminal pane</span></span>

<span data-ttu-id="b9ba8-138">當您在終端機工作階段中叫用您的 Cmdlet 時，偵錯工具即會在原始程式碼中設定的所有中斷點上停止。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-138">When you invoke your cmdlet in the terminal session, the debugger stops at any breakpoints set in your source code.</span></span>

### <a name="configuring-launchjson-for-powershell-core"></a><span data-ttu-id="b9ba8-139">設定 PowerShell Core 的 launch.json</span><span class="sxs-lookup"><span data-stu-id="b9ba8-139">Configuring launch.json for PowerShell Core</span></span>

1. <span data-ttu-id="b9ba8-140">安裝 [C# for Visual Studio Code][] 延伸模組</span><span class="sxs-lookup"><span data-stu-id="b9ba8-140">Install the [C# for Visual Studio Code][] extension</span></span>

1. <span data-ttu-id="b9ba8-141">在 [偵錯] 窗格中，新增偵錯組態</span><span class="sxs-lookup"><span data-stu-id="b9ba8-141">In the Debug pane, add a debug configuration</span></span>

1. <span data-ttu-id="b9ba8-142">在 [`Select environment`] 對話方塊中，選擇 [`.NET Core`]</span><span class="sxs-lookup"><span data-stu-id="b9ba8-142">In the `Select environment` dialog, choose `.NET Core`</span></span>

1. <span data-ttu-id="b9ba8-143">`launch.json` 檔案隨即會在編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-143">The `launch.json` file is opened in the editor.</span></span> <span data-ttu-id="b9ba8-144">當您的游標位於 `configurations` 陣列內時，您會看到 `configuration` 選擇器。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-144">With your cursor inside the `configurations` array, you see the `configuration` picker.</span></span> <span data-ttu-id="b9ba8-145">若您看不到此清單，請選取 [新增組態]。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-145">If you don't see this list, select **Add Configuration** .</span></span>

1. <span data-ttu-id="b9ba8-146">若要建立預設的偵錯組態，請選取 [啟動 .NET Core 主控台應用程式]：</span><span class="sxs-lookup"><span data-stu-id="b9ba8-146">To create a default debug configuration, select **Launch .NET Core Console App** :</span></span>

   ![啟動 .NET Core 主控台應用程式](media/using-vscode-for-debugging-compiled-cmdlets/add-configuration-dialog.png)

1. <span data-ttu-id="b9ba8-148">編輯 `name`、`program`、`args` 及 `console` 欄位，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b9ba8-148">Edit the `name`, `program`, `args`, and `console` fields as follows:</span></span>

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

<span data-ttu-id="b9ba8-149">`program` 欄位可用來啟動 `pwsh`，以便能夠執行正在偵錯的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-149">The `program` field is used to launch `pwsh` so that the cmdlet being debugged can be run.</span></span> <span data-ttu-id="b9ba8-150">`-NoExit` 引數會在模組匯入之後，使 PowerShell 工作階段保持開啟。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-150">The `-NoExit` argument prevents the PowerShell session from exiting as soon as the module is imported.</span></span>
<span data-ttu-id="b9ba8-151">在您遵循[撰寫可移植的模組][]指南後，`Import-Module` 引數中的路徑即為預設的建置輸出路徑。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-151">The path in the `Import-Module` argument is the default build output path when you've followed the [Writing Portable Modules][] guide.</span></span> <span data-ttu-id="b9ba8-152">若您已建立模組資訊清單 (`.psd1` 檔案)，您應該改為使用該清單的路徑。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-152">If you've created a module manifest (`.psd1` file), you should use the path to that instead.</span></span> <span data-ttu-id="b9ba8-153">`/` 路徑分隔符號適用於 Windows、Linux 以及 macOS。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-153">The `/` path separator works on Windows, Linux, and macOS.</span></span> <span data-ttu-id="b9ba8-154">您必須使用整合式終端機，來執行要對其偵錯的 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-154">You must use the integrated terminal to run the PowerShell commands you want to debug.</span></span>

> [!NOTE]
> <span data-ttu-id="b9ba8-155">若偵錯工具未在任何中斷點停止，請在 Visual Studio Code 偵錯主控台中找出下列描述：</span><span class="sxs-lookup"><span data-stu-id="b9ba8-155">If the debugger doesn't stop at any breakpoints, look in the Visual Studio Code Debug Console for a line that says:</span></span>
>
> ```
> Loaded '/path/to/myModule.dll'. Skipped loading symbols. Module is optimized and the debugger option 'Just My Code' is enabled.
> ```
>
> <span data-ttu-id="b9ba8-156">若您看到此描述，請將 `"justMyCode": false` 新增至您的啟動組態 (與 `"console": "integratedTerminal"` 相同的層級)。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-156">If you see this, add `"justMyCode": false` to your launch config (at the same level as `"console": "integratedTerminal"`.</span></span>

### <a name="configuring-launchjson-for-windows-powershell"></a><span data-ttu-id="b9ba8-157">設定 Windows PowerShell 的 launch.json</span><span class="sxs-lookup"><span data-stu-id="b9ba8-157">Configuring launch.json for Windows PowerShell</span></span>

<span data-ttu-id="b9ba8-158">此啟動組態適用於在 Windows PowerShell (`powershell.exe`) 中測試 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-158">This launch configuration works for testing your cmdlets in Windows PowerShell (`powershell.exe`).</span></span>
<span data-ttu-id="b9ba8-159">建立第二個啟動組態，並進行下列變更：</span><span class="sxs-lookup"><span data-stu-id="b9ba8-159">Create a second launch configuration with the following changes:</span></span>

1. <span data-ttu-id="b9ba8-160">`name` 應該是 `PowerShell cmdlets: powershell`</span><span class="sxs-lookup"><span data-stu-id="b9ba8-160">`name` should be `PowerShell cmdlets: powershell`</span></span>

1. <span data-ttu-id="b9ba8-161">`type` 應該是 `clr`</span><span class="sxs-lookup"><span data-stu-id="b9ba8-161">`type` should be `clr`</span></span>

1. <span data-ttu-id="b9ba8-162">`program` 應該是 `powershell`</span><span class="sxs-lookup"><span data-stu-id="b9ba8-162">`program` should be `powershell`</span></span>

   <span data-ttu-id="b9ba8-163">其看起來應該如下：</span><span class="sxs-lookup"><span data-stu-id="b9ba8-163">It should look like this:</span></span>

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

## <a name="launching-a-debugging-session"></a><span data-ttu-id="b9ba8-164">啟動偵錯工作階段</span><span class="sxs-lookup"><span data-stu-id="b9ba8-164">Launching a debugging session</span></span>

<span data-ttu-id="b9ba8-165">現在一切都已準備完成，可開始進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-165">Now everything is ready to begin debugging.</span></span>

- <span data-ttu-id="b9ba8-166">將中斷點置於欲進行偵錯之 Cmdlet 的原始程式碼中：</span><span class="sxs-lookup"><span data-stu-id="b9ba8-166">Place a breakpoint in the source code for the cmdlet you want to debug:</span></span>

  ![中斷點會顯示為裝訂邊中的紅點](media/using-vscode-for-debugging-compiled-cmdlets/set-breakpoint.png)

- <span data-ttu-id="b9ba8-168">請確定已在 [偵錯] 檢視的 [組態] 下拉式功能表中，選取相關的 [PowerShell Cmdlet] 組態：</span><span class="sxs-lookup"><span data-stu-id="b9ba8-168">Ensure that the relevant **PowerShell cmdlets** configuration is selected in the configuration drop-down menu in the **Debug** view:</span></span>

  ![選取 [啟動組態]](media/using-vscode-for-debugging-compiled-cmdlets/select-launch-configuration.png)

- <span data-ttu-id="b9ba8-170">按 <kbd>F5</kbd>，或按一下 [開始偵錯] 按鈕</span><span class="sxs-lookup"><span data-stu-id="b9ba8-170">Press <kbd>F5</kbd> or click on the **Start Debugging** button</span></span>

- <span data-ttu-id="b9ba8-171">切換至終端機窗格，並叫用您的 Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="b9ba8-171">Switch to the terminal pane and invoke your cmdlet:</span></span>

  ![叫用 Cmdlet](media/using-vscode-for-debugging-compiled-cmdlets/invoke-the-cmdlet.png)

- <span data-ttu-id="b9ba8-173">執行會在中斷點停止：</span><span class="sxs-lookup"><span data-stu-id="b9ba8-173">Execution stops at the breakpoint:</span></span>

  ![執行會在中斷點終止](media/using-vscode-for-debugging-compiled-cmdlets/stopped-at-breakpoint.png)

<span data-ttu-id="b9ba8-175">您可以逐步執行原始程式碼、檢查變數，並檢查呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-175">You can step through the source code, inspect variables, and inspect the call stack.</span></span>

<span data-ttu-id="b9ba8-176">若要結束偵錯，請按一下 [偵錯] 工具列中的 [停止]，或按 <kbd>Shift</kbd>-<kbd>F5</kbd>。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-176">To end debugging, click **Stop** in the debug toolbar or press <kbd>Shift</kbd>-<kbd>F5</kbd>.</span></span> <span data-ttu-id="b9ba8-177">用來進行偵錯的殼層會隨即結束，並解除鎖定已編譯的 DLL 檔案。</span><span class="sxs-lookup"><span data-stu-id="b9ba8-177">The shell used for debugging exits and releases the lock on the compiled DLL file.</span></span>

<!-- reference links -->
[在 Visual Studio Code 中偵錯]: https://code.visualstudio.com/docs/editor/debugging
[Debugging in Visual Studio Code]: https://code.visualstudio.com/docs/editor/debugging
[使用 Visual Studio Code 來進行遠端編輯與偵錯]: using-vscode-for-remote-editing-and-debugging.md
[Using Visual Studio Code for remote editing and debugging]: using-vscode-for-remote-editing-and-debugging.md
[撰寫可移植的模組]: ../writing-portable-modules.md
[Writing Portable Modules]: ../writing-portable-modules.md
[C# for Visual Studio Code]: https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp
