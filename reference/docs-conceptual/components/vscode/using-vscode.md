---
title: 使用 Visual Studio Code 開發 PowerShell
description: 使用 Visual Studio Code 開發 PowerShell
ms.date: 08/06/2018
ms.openlocfilehash: 6a0da6e060693dc7cfc08d40fd658414dc23d660
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733887"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="6d73d-103">使用 Visual Studio Code 開發 PowerShell</span><span class="sxs-lookup"><span data-stu-id="6d73d-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="6d73d-104">除了 [PowerShell ISE][ise] 之外，PowerShell 在 Visual Studio Code 中也受到良好支援。</span><span class="sxs-lookup"><span data-stu-id="6d73d-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="6d73d-105">而且，雖然所有平台 (Windows、macOS 和 Linux) 上的 PowerShell Core 都支援 Visual Studio Code，但 PowerShell Core 不支援 ISE</span><span class="sxs-lookup"><span data-stu-id="6d73d-105">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="6d73d-106">使用 Windows 10 或安裝適用於低階 Windows 作業系統 (例如 Windows 8.1 等) 的 [Windows Management Framework 5.0 RTM](https://devblogs.microsoft.com/powershell/windows-management-framework-wmf-5-0-rtm-is-now-available-via-the-microsoft-update-catalog/)，即可以在 Windows 上使用 Visual Studio Code 與 PowerShell 第 5 版。</span><span class="sxs-lookup"><span data-stu-id="6d73d-106">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://devblogs.microsoft.com/powershell/windows-management-framework-wmf-5-0-rtm-is-now-available-via-the-microsoft-update-catalog/) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="6d73d-107">啟動它之前，請先確定系統上有 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="6d73d-107">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="6d73d-108">若為 Windows、macOS 和 Linux 上的新型工作負載，請參閱：</span><span class="sxs-lookup"><span data-stu-id="6d73d-108">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="6d73d-109">[在 Linux 上安裝 PowerShell Core][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="6d73d-109">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="6d73d-110">[在 macOS 上安裝 PowerShell Core][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="6d73d-110">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="6d73d-111">[在 Windows 上安裝 PowerShell Core][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="6d73d-111">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="6d73d-112">若為傳統的 Windows PowerShell 工作負載，請參閱[安裝 Windows PowerShell][install-winps]。</span><span class="sxs-lookup"><span data-stu-id="6d73d-112">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="6d73d-113">使用 Visual Studio Code 編輯</span><span class="sxs-lookup"><span data-stu-id="6d73d-113">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="6d73d-114">1.安裝 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="6d73d-114">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="6d73d-115">**Linux**：遵循 [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) (在 Linux 上執行 VS Code) 頁面的安裝指示操作</span><span class="sxs-lookup"><span data-stu-id="6d73d-115">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="6d73d-116">**macOS**：遵循 [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) (在 macOS 上執行 VS Code) 頁面的安裝指示操作</span><span class="sxs-lookup"><span data-stu-id="6d73d-116">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="6d73d-117">在 macOS 上，您必須安裝 OpenSSL，PowerShell 延伸模組才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="6d73d-117">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
  > <span data-ttu-id="6d73d-118">完成這項作業最簡單的方式是安裝 [Homebrew](https://brew.sh/) ，然後執行 `brew install openssl`。</span><span class="sxs-lookup"><span data-stu-id="6d73d-118">The easiest way to accomplish this is to install [Homebrew](https://brew.sh/) and then run `brew install openssl`.</span></span>
  > <span data-ttu-id="6d73d-119">VS Code 現在可以成功載入 PowerShell 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="6d73d-119">VS Code can now load the PowerShell extension successfully.</span></span>

- <span data-ttu-id="6d73d-120">**Windows**：遵循 [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) (在 Windows 上執行 VS Code) 頁面的安裝指示操作</span><span class="sxs-lookup"><span data-stu-id="6d73d-120">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="6d73d-121">2.安裝 PowerShell 延伸模組</span><span class="sxs-lookup"><span data-stu-id="6d73d-121">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="6d73d-122">啟動 Visual Studio Code 應用程式：</span><span class="sxs-lookup"><span data-stu-id="6d73d-122">Launch the Visual Studio Code app by:</span></span>
  - <span data-ttu-id="6d73d-123">**Windows**：在您的 PowerShell 工作階段鍵入 `code`</span><span class="sxs-lookup"><span data-stu-id="6d73d-123">**Windows**: typing `code` in your PowerShell session</span></span>
  - <span data-ttu-id="6d73d-124">**Linux**：在您的終端機上鍵入 `code`</span><span class="sxs-lookup"><span data-stu-id="6d73d-124">**Linux**: typing `code` in your terminal</span></span>
  - <span data-ttu-id="6d73d-125">**macOS**：在您的終端機上鍵入 `code`</span><span class="sxs-lookup"><span data-stu-id="6d73d-125">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="6d73d-126">按 **Ctrl+P** (Mac 是 **Cmd+P**) 啟動 [快速開啟]  。</span><span class="sxs-lookup"><span data-stu-id="6d73d-126">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="6d73d-127">在 [快速開啟] 中鍵入 `ext install powershell` 並點擊 **Enter**。</span><span class="sxs-lookup"><span data-stu-id="6d73d-127">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="6d73d-128">提要欄位上隨即開啟 [延伸模組]  檢視。</span><span class="sxs-lookup"><span data-stu-id="6d73d-128">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="6d73d-129">從 Microsoft 選取 PowerShell 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="6d73d-129">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="6d73d-130">您應該會看到類似如下的畫面︰</span><span class="sxs-lookup"><span data-stu-id="6d73d-130">You should see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="6d73d-132">從 Microsoft 按一下 PowerShell 延伸模組的 [安裝]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="6d73d-132">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="6d73d-133">安裝之後，您會看到 [安裝]  按鈕變成 [重新載入]  。</span><span class="sxs-lookup"><span data-stu-id="6d73d-133">After the install, you see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="6d73d-134">按一下 [重新載入]  。</span><span class="sxs-lookup"><span data-stu-id="6d73d-134">Click on **Reload**.</span></span>
- <span data-ttu-id="6d73d-135">重新載入 Visual Studio Code 之後，就可以進行編輯。</span><span class="sxs-lookup"><span data-stu-id="6d73d-135">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="6d73d-136">例如，若要建立新的檔案，按一下 [檔案]->[新增]  。</span><span class="sxs-lookup"><span data-stu-id="6d73d-136">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="6d73d-137">若要儲存它，按一下 [檔案]->[儲存]  ，然後提供檔案名稱，例如 `HelloWorld.ps1`。</span><span class="sxs-lookup"><span data-stu-id="6d73d-137">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="6d73d-138">若要關閉檔案，請按一下檔案名稱旁邊的 "x"。</span><span class="sxs-lookup"><span data-stu-id="6d73d-138">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="6d73d-139">若要結束 Visual Studio Code，[檔案]->[結束]  。</span><span class="sxs-lookup"><span data-stu-id="6d73d-139">To exit Visual Studio Code, **File->Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="6d73d-140">在受限制的系統上安裝 PowerShell 延伸模組</span><span class="sxs-lookup"><span data-stu-id="6d73d-140">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="6d73d-141">某些系統已設定為需要檢查所有程式碼簽章，因此必須以手動方式核准 PowerShell Editor Services，才能在系統上執行。</span><span class="sxs-lookup"><span data-stu-id="6d73d-141">Some systems are set up in a way that requires all code signatures to be checked and thus requires PowerShell Editor Services to be manually approved to run on the system.</span></span>
<span data-ttu-id="6d73d-142">如果您已經安裝 PowerShell 延伸模組，但發生如下錯誤，變更執行原則的群組原則更新是可能的原因：</span><span class="sxs-lookup"><span data-stu-id="6d73d-142">A Group Policy update that changes execution policy is a likely cause if you have installed the PowerShell extension but are reaching an error like:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="6d73d-143">若要手動核准 PowerShell Editor Services，讓適用於 VSCode 的 PowerShell 延伸模組開啟 PowerShell 提示字元並執行：</span><span class="sxs-lookup"><span data-stu-id="6d73d-143">To manually approve PowerShell Editor Services and thus the PowerShell extension for VSCode open a PowerShell prompt and run:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="6d73d-144">系統會提示您「要執行來自這個不受信任的發行者的軟體嗎?」</span><span class="sxs-lookup"><span data-stu-id="6d73d-144">You are prompted with "Do you want to run software from this untrusted publisher?"</span></span>
<span data-ttu-id="6d73d-145">輸入 `R` 以執行檔案。</span><span class="sxs-lookup"><span data-stu-id="6d73d-145">Type `R` to run the file.</span></span> <span data-ttu-id="6d73d-146">然後，開啟 Visual Studio Code 並檢查 PowerShell 延伸模組是否正常運作。</span><span class="sxs-lookup"><span data-stu-id="6d73d-146">Then, open Visual Studio Code and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="6d73d-147">如果您仍有關於開始使用的問題，請透過 [GitHub](https://github.com/PowerShell/vscode-powershell/issues) \(英文\) 讓我們知道。</span><span class="sxs-lookup"><span data-stu-id="6d73d-147">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

#### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="6d73d-148">選擇要與擴充功能搭配使用的 PowerShell 版本</span><span class="sxs-lookup"><span data-stu-id="6d73d-148">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="6d73d-149">透過與 Windows PowerShell 並存安裝的 PowerShell Core，它現在能夠將特定版本的 PowerShell 與 PowerShell 擴充模組搭配使用。</span><span class="sxs-lookup"><span data-stu-id="6d73d-149">With PowerShell Core installing side-by-side with Windows PowerShell, is it now possible to use a particular version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="6d73d-150">使用下列這些步驟來選擇版本：</span><span class="sxs-lookup"><span data-stu-id="6d73d-150">Use the following these steps to choose the version:</span></span>

1. <span data-ttu-id="6d73d-151">開啟命令平板 (在 Windows & Linux 上為 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>，在 macOS 上為 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>)。</span><span class="sxs-lookup"><span data-stu-id="6d73d-151">Open the command pallet (<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on Windows & Linux, <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS).</span></span>
1. <span data-ttu-id="6d73d-152">搜尋「工作階段」。</span><span class="sxs-lookup"><span data-stu-id="6d73d-152">Search for "Session".</span></span>
1. <span data-ttu-id="6d73d-153">按一下 [PowerShell:顯示工作階段功能表]。</span><span class="sxs-lookup"><span data-stu-id="6d73d-153">Click on "PowerShell: Show Session Menu".</span></span>
1. <span data-ttu-id="6d73d-154">從清單中選擇要使用的 PowerShell 版本，例如 "PowerShell Core"。</span><span class="sxs-lookup"><span data-stu-id="6d73d-154">Choose the version of PowerShell you want to use from the list - for example, "PowerShell Core".</span></span>

>[!IMPORTANT]
> <span data-ttu-id="6d73d-155">此功能會查看不同作業系統上的一些已知路徑，以探索 PowerShell 的安裝位置。</span><span class="sxs-lookup"><span data-stu-id="6d73d-155">This feature looks at a few well-known paths on different operating systems to discover install locations of PowerShell.</span></span> <span data-ttu-id="6d73d-156">如果您已將 PowerShell 安裝到非典型位置，則它一開始可能不會顯示於工作階段功能表中。</span><span class="sxs-lookup"><span data-stu-id="6d73d-156">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="6d73d-157">您可以藉由[新增自己的自訂路徑](#adding-your-own-powershell-paths-to-the-session-menu)來擴充工作階段功能表，如下所述。</span><span class="sxs-lookup"><span data-stu-id="6d73d-157">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

>[!NOTE]
> <span data-ttu-id="6d73d-158">還有另一種方式可前往工作階段功能表。</span><span class="sxs-lookup"><span data-stu-id="6d73d-158">There is another way to get to the session menu.</span></span> <span data-ttu-id="6d73d-159">在您的編輯器中開啟 PowerShell 檔案時，您會在右下角看到綠色的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="6d73d-159">When a PowerShell file is open in your editor, you see a green version number in the bottom right.</span></span> <span data-ttu-id="6d73d-160">按一下此版本號碼，即會帶您前往工作階段功能表。</span><span class="sxs-lookup"><span data-stu-id="6d73d-160">Clicking this version number will bring you to the session menu.</span></span>

##### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="6d73d-161">將您自己的 PowerShell 路徑新增至工作階段功能表</span><span class="sxs-lookup"><span data-stu-id="6d73d-161">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="6d73d-162">您可以透過 VS Code 設定，將其他 PowerShell 可執行檔路徑新增至工作階段功能表。</span><span class="sxs-lookup"><span data-stu-id="6d73d-162">You can add other PowerShell executable paths to the session menu through a VS Code setting.</span></span>

<span data-ttu-id="6d73d-163">將項目新增至清單`powershell.powerShellAdditionalExePaths` 或建立清單 (如果它不存在您的 `settings.json` 中)：</span><span class="sxs-lookup"><span data-stu-id="6d73d-163">Add an item to the list  `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

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

<span data-ttu-id="6d73d-164">每個項目都必須具備：</span><span class="sxs-lookup"><span data-stu-id="6d73d-164">Each item must have:</span></span>

* <span data-ttu-id="6d73d-165">`exePath`:`pwsh` 或 `powershell` 可執行檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="6d73d-165">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
* <span data-ttu-id="6d73d-166">`versionName`:將顯示於工作階段功能表中的文字。</span><span class="sxs-lookup"><span data-stu-id="6d73d-166">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="6d73d-167">您可以將此文字設定為要顯示於工作階段功能表 (也稱為最後一個設定中的 `versionName`) 中的文字，藉以使用 `powershell.powerShellDefaultVersion` 設定來設定要使用的預設 PowerShell 版本：</span><span class="sxs-lookup"><span data-stu-id="6d73d-167">You can set the default PowerShell version to use using the `powershell.powerShellDefaultVersion` setting by setting this to the text displayed in the session menu (aka the `versionName` in the last setting):</span></span>

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

<span data-ttu-id="6d73d-168">設定此設定之後，重新啟動 Visual Studio Code，或使用 [開發人員:重新載入視窗] 命令平板動作，重新載入目前的 vscode 視窗。</span><span class="sxs-lookup"><span data-stu-id="6d73d-168">Once you've set this setting, restart Visual Studio Code or use the the "Developer: Reload Window" command pallet action to reload the current vscode window.</span></span>

<span data-ttu-id="6d73d-169">如果您開啟工作階段功能表，現在將會看到您其他的 PowerShell 版本！</span><span class="sxs-lookup"><span data-stu-id="6d73d-169">If you open the session menu, you will now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="6d73d-170">如果您從來源建置 PowerShell，則這是最適合用來測試 PowerShell 本機組建的方式。</span><span class="sxs-lookup"><span data-stu-id="6d73d-170">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="6d73d-171">Visual Studio Code 的組態設定</span><span class="sxs-lookup"><span data-stu-id="6d73d-171">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="6d73d-172">使用先前段落中的步驟，您可以在 `settings.json` 中新增組態設定。</span><span class="sxs-lookup"><span data-stu-id="6d73d-172">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="6d73d-173">我們建議下列 Visual Studio Code 組態設定：</span><span class="sxs-lookup"><span data-stu-id="6d73d-173">We recommend the following configuration settings for Visual Studio Code:</span></span>

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

<span data-ttu-id="6d73d-174">如果您不希望這些設定影響所有的檔案類型，VSCode 也允許依照語言的設定。</span><span class="sxs-lookup"><span data-stu-id="6d73d-174">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="6d73d-175">透過將設定放入 `[<language-name>]` 欄位，以建立語言特定設定。</span><span class="sxs-lookup"><span data-stu-id="6d73d-175">Create a language specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="6d73d-176">例如：</span><span class="sxs-lookup"><span data-stu-id="6d73d-176">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="6d73d-177">如需有關 VS Code 中檔案編碼的詳細資訊，請參閱[了解檔案編碼](understanding-file-encoding.md)。</span><span class="sxs-lookup"><span data-stu-id="6d73d-177">For more information about file encoding in VS Code, see [Understanding file encoding](understanding-file-encoding.md).</span></span>

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="6d73d-178">使用 Visual Studio Code 偵錯</span><span class="sxs-lookup"><span data-stu-id="6d73d-178">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="6d73d-179">無工作區偵錯</span><span class="sxs-lookup"><span data-stu-id="6d73d-179">No-workspace debugging</span></span>

<span data-ttu-id="6d73d-180">使用 Visual Studio Code 1.9 版可以偵錯 PowerShell 指令碼，不必開啟包含 PowerShell 指令碼的資料夾。</span><span class="sxs-lookup"><span data-stu-id="6d73d-180">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span> <span data-ttu-id="6d73d-181">以 [檔案] -> [開啟檔案]  開啟 PowerShell 指令碼檔案，在行上設定中斷點 (按 F9)，然後按 F5 開始偵錯。</span><span class="sxs-lookup"><span data-stu-id="6d73d-181">Open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span> <span data-ttu-id="6d73d-182">您會看到 [偵錯動作] 窗格出現，其可讓您中斷偵錯工具、中斷步驟、繼續和停止偵錯。</span><span class="sxs-lookup"><span data-stu-id="6d73d-182">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="6d73d-183">工作區偵錯</span><span class="sxs-lookup"><span data-stu-id="6d73d-183">Workspace debugging</span></span>

<span data-ttu-id="6d73d-184">工作區偵錯是指使用 [檔案]  功能表的 [開啟資料夾...]  ，在 Visual Studio Code 已開啟的資料夾內容中偵錯。</span><span class="sxs-lookup"><span data-stu-id="6d73d-184">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="6d73d-185">您開啟的資料夾通常是 PowerShell 專案資料夾及/或 Git 存放庫的根目錄。</span><span class="sxs-lookup"><span data-stu-id="6d73d-185">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="6d73d-186">即使在此模式中，只要按下 F5 就可以開始偵錯目前選取的 PowerShell 指令碼。</span><span class="sxs-lookup"><span data-stu-id="6d73d-186">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="6d73d-187">不過，工作區偵錯可讓您定義多個偵錯設定，不只是偵錯目前開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="6d73d-187">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="6d73d-188">例如，您可以新增設定以：</span><span class="sxs-lookup"><span data-stu-id="6d73d-188">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="6d73d-189">啟動偵錯工具中的 Pester 測試</span><span class="sxs-lookup"><span data-stu-id="6d73d-189">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="6d73d-190">以偵錯工具中的引數啟動特定檔案</span><span class="sxs-lookup"><span data-stu-id="6d73d-190">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="6d73d-191">啟動偵錯工具中的互動式工作階段</span><span class="sxs-lookup"><span data-stu-id="6d73d-191">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="6d73d-192">將偵錯工具附加至 PowerShell 主機處理程序</span><span class="sxs-lookup"><span data-stu-id="6d73d-192">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="6d73d-193">請遵循下列步驟建立您的偵錯設定檔：</span><span class="sxs-lookup"><span data-stu-id="6d73d-193">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="6d73d-194">按 **Ctrl+Shift+D** (Mac 是 **Cmd+Shift+D**) 開啟 [偵錯]  檢視。</span><span class="sxs-lookup"><span data-stu-id="6d73d-194">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
  2. <span data-ttu-id="6d73d-195">按工具列中的**設定**齒輪圖示。</span><span class="sxs-lookup"><span data-stu-id="6d73d-195">Press the **Configure** gear icon in the toolbar.</span></span>
  3. <span data-ttu-id="6d73d-196">Visual Studio Code 會提示您 [選取環境]  。</span><span class="sxs-lookup"><span data-stu-id="6d73d-196">Visual Studio Code prompts you to **Select Environment**.</span></span> <span data-ttu-id="6d73d-197">選擇 [PowerShell]  。</span><span class="sxs-lookup"><span data-stu-id="6d73d-197">Choose **PowerShell**.</span></span>

  <span data-ttu-id="6d73d-198">當您這樣做時，Visual Studio Code 會在工作區資料夾的根目錄中建立目錄和檔案：".vscode\launch.json"。</span><span class="sxs-lookup"><span data-stu-id="6d73d-198">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
  <span data-ttu-id="6d73d-199">這是儲存偵錯設定的位置。</span><span class="sxs-lookup"><span data-stu-id="6d73d-199">This is where your debug configuration is stored.</span></span> <span data-ttu-id="6d73d-200">如果檔案是在 Git 存放庫中，您通常要修訂 launch.json 檔案。</span><span class="sxs-lookup"><span data-stu-id="6d73d-200">If your files are in a Git repository, you typically want to commit the launch.json file.</span></span>
  <span data-ttu-id="6d73d-201">Launch.json 檔案的內容如下：</span><span class="sxs-lookup"><span data-stu-id="6d73d-201">The contents of the launch.json file are:</span></span>

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

  <span data-ttu-id="6d73d-202">這表示常見的偵錯案例。</span><span class="sxs-lookup"><span data-stu-id="6d73d-202">This represents the common debug scenarios.</span></span>
  <span data-ttu-id="6d73d-203">不過，當您在編輯器中開啟這個檔案時，您會看到 [新增設定]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="6d73d-203">However, when you open this file in the editor, you see an **Add Configuration...** button.</span></span>
  <span data-ttu-id="6d73d-204">您可以按此按鈕新增多個 PowerShell 偵錯設定。</span><span class="sxs-lookup"><span data-stu-id="6d73d-204">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="6d73d-205">**PowerShell：啟動指令碼**是可以新增的方便設定。</span><span class="sxs-lookup"><span data-stu-id="6d73d-205">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
  <span data-ttu-id="6d73d-206">使用此設定時，您可以指定有選擇性引數的特定檔案，只要按下 F5 就應該啟動，無論編輯器中當時作用的是哪個檔案。</span><span class="sxs-lookup"><span data-stu-id="6d73d-206">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

  <span data-ttu-id="6d73d-207">建立偵錯設定之後，您就可以從 [偵錯]  檢視工具列的偵錯設定下拉式清單中擇一，選取在偵錯工作階段期間想要使用的設定。</span><span class="sxs-lookup"><span data-stu-id="6d73d-207">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="6d73d-208">有幾個部落格可以協助您開始使用適用於 Visual Studio Code 的 PowerShell 擴充功能：</span><span class="sxs-lookup"><span data-stu-id="6d73d-208">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="6d73d-209">[PowerShell 延伸模組][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="6d73d-209">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="6d73d-210">[在 Visual Studio Code 中撰寫和偵錯 PowerShell 指令碼][debug]</span><span class="sxs-lookup"><span data-stu-id="6d73d-210">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="6d73d-211">[偵錯 Visual Studio Code 指引][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="6d73d-211">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="6d73d-212">[在 Visual Studio Code 中偵錯 PowerShell][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="6d73d-212">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="6d73d-213">[開始使用 Visual Studio Code 中的 PowerShell 開發][getting-started]</span><span class="sxs-lookup"><span data-stu-id="6d73d-213">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="6d73d-214">[適用於 PowerShell 開發的 Visual Studio Code 編輯功能 – 第 1 部分][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="6d73d-214">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="6d73d-215">[適用於 PowerShell 開發的 Visual Studio Code 編輯功能 – 第 2 部分][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="6d73d-215">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="6d73d-216">[在 Visual Studio Code 中偵錯 PowerShell 指令碼 – 第 1 部分][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="6d73d-216">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="6d73d-217">[在 Visual Studio Code 中偵錯 PowerShell 指令碼 – 第 2 部分][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="6d73d-217">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

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

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="6d73d-218">適用於 Visual Studio Code 的 PowerShell 延伸模組</span><span class="sxs-lookup"><span data-stu-id="6d73d-218">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="6d73d-219">[GitHub](https://github.com/PowerShell/vscode-powershell) 上可以找到 PowerShell 延伸模組的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="6d73d-219">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
