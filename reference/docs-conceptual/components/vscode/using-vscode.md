---
title: 使用 Visual Studio Code 開發 PowerShell
description: 使用 Visual Studio Code 開發 PowerShell
ms.date: 11/07/2019
ms.openlocfilehash: 4f197e71d3b79828f466584f5d862415726818b1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74117392"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="385cb-103">使用 Visual Studio Code 開發 PowerShell</span><span class="sxs-lookup"><span data-stu-id="385cb-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="385cb-104">除了 [PowerShell ISE][ise] 之外，PowerShell 在 Visual Studio Code (VSCode) 中也受到良好支援。</span><span class="sxs-lookup"><span data-stu-id="385cb-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code (VSCode).</span></span> <span data-ttu-id="385cb-105">雖然 PowerShell Core 不支援 ISE，但這些平台上的 PowerShell Core 都支援 VSCode：Windows、macOS 和 Linux。</span><span class="sxs-lookup"><span data-stu-id="385cb-105">The ISE isn't supported with PowerShell Core, but VSCode is supported for PowerShell Core on all platforms: Windows, macOS, and Linux.</span></span>

<span data-ttu-id="385cb-106">使用 Windows 10 或安裝適用於低階 Windows 作業系統 (例如 Windows 8.1) 的 Windows Management Framework 5.1，即可以在 Windows 上使用 VSCode 與 PowerShell 第 5 版。</span><span class="sxs-lookup"><span data-stu-id="385cb-106">You can use VSCode on Windows with PowerShell version 5 by using Windows 10 or by installing Windows Management Framework 5.1 for down-level Windows OSs such as Windows 8.1.</span></span> <span data-ttu-id="385cb-107">如需詳細資訊，請參閱[安裝與設定 WMF 5.1](/powershell/scripting/wmf/setup/install-configure)。</span><span class="sxs-lookup"><span data-stu-id="385cb-107">For more information, see [Install and Configure WMF 5.1](/powershell/scripting/wmf/setup/install-configure).</span></span>

<span data-ttu-id="385cb-108">在開始前，請先確定系統上有 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="385cb-108">Before you begin, make sure PowerShell exists on your system.</span></span> <span data-ttu-id="385cb-109">如需 Windows、macOS 和 Linux 上的新型工作負載，請參閱下列連結：</span><span class="sxs-lookup"><span data-stu-id="385cb-109">For modern workloads on Windows, macOS, and Linux, see the following links:</span></span>

- <span data-ttu-id="385cb-110">[在 Linux 上安裝 PowerShell Core][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="385cb-110">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="385cb-111">[在 macOS 上安裝 PowerShell Core][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="385cb-111">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="385cb-112">[在 Windows 上安裝 PowerShell Core][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="385cb-112">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="385cb-113">若為傳統的 Windows PowerShell 工作負載，請參閱[安裝 Windows PowerShell][install-winps]。</span><span class="sxs-lookup"><span data-stu-id="385cb-113">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-vscode"></a><span data-ttu-id="385cb-114">使用 VSCode 編輯</span><span class="sxs-lookup"><span data-stu-id="385cb-114">Editing with VSCode</span></span>

1. <span data-ttu-id="385cb-115">安裝 VSCode。</span><span class="sxs-lookup"><span data-stu-id="385cb-115">Install VSCode.</span></span> <span data-ttu-id="385cb-116">如需詳細資訊，請參閱 [Setting up Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview) (設定 Visual Studio Code) 概觀。</span><span class="sxs-lookup"><span data-stu-id="385cb-116">For more information, see the overview [Setting up Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview).</span></span>

   <span data-ttu-id="385cb-117">下列為每個平台的安裝指示：</span><span class="sxs-lookup"><span data-stu-id="385cb-117">There are installation instructions for each platform:</span></span>

   - <span data-ttu-id="385cb-118">**Linux**：請遵循 [Running VSCode on Linux在](https://code.visualstudio.com/docs/setup/linux) ( Linux 上執行 VS Code) 頁面的安裝指示。</span><span class="sxs-lookup"><span data-stu-id="385cb-118">**Linux**: follow the installation instructions on the [Running VSCode on Linux](https://code.visualstudio.com/docs/setup/linux) page.</span></span>
   - <span data-ttu-id="385cb-119">**macOS**：請遵循 [Running VSCode on macOS](https://code.visualstudio.com/docs/setup/mac) (在 macOS 上執行 VS Code) 頁面的安裝指示。</span><span class="sxs-lookup"><span data-stu-id="385cb-119">**macOS**: follow the installation instructions on the [Running VSCode on macOS](https://code.visualstudio.com/docs/setup/mac) page.</span></span>

     > [!IMPORTANT]
     > <span data-ttu-id="385cb-120">在 macOS 上，您必須安裝 OpenSSL，PowerShell 延伸模組才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="385cb-120">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span> <span data-ttu-id="385cb-121">完成這項作業最簡單的方式是安裝 [Homebrew](https://brew.sh/) ，然後執行 `brew install openssl`。</span><span class="sxs-lookup"><span data-stu-id="385cb-121">The easiest way to accomplish this is to install [Homebrew](https://brew.sh/) and then run `brew install openssl`.</span></span> <span data-ttu-id="385cb-122">VSCode 現在可以成功載入 PowerShell 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="385cb-122">VSCode can now load the PowerShell extension successfully.</span></span>

   - <span data-ttu-id="385cb-123">**Windows**：請遵循 [Running VSCode on Windows](https://code.visualstudio.com/docs/setup/windows) (在 Windows 上執行 VS Code) 頁面的安裝指示。</span><span class="sxs-lookup"><span data-stu-id="385cb-123">**Windows**: follow the installation instructions on the [Running VSCode on Windows](https://code.visualstudio.com/docs/setup/windows) page.</span></span>

1. <span data-ttu-id="385cb-124">安裝 PowerShell 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="385cb-124">Install the PowerShell Extension.</span></span>

   1. <span data-ttu-id="385cb-125">啟動 VSCode 應用程式，方法是：</span><span class="sxs-lookup"><span data-stu-id="385cb-125">Launch the VSCode app by:</span></span>
      - <span data-ttu-id="385cb-126">**Windows**：在您的 PowerShell 工作階段鍵入 `code`</span><span class="sxs-lookup"><span data-stu-id="385cb-126">**Windows**: typing `code` in your PowerShell session</span></span>
      - <span data-ttu-id="385cb-127">**Linux**：在您的終端機上鍵入 `code`</span><span class="sxs-lookup"><span data-stu-id="385cb-127">**Linux**: typing `code` in your terminal</span></span>
      - <span data-ttu-id="385cb-128">**macOS**：在您的終端機上鍵入 `code`</span><span class="sxs-lookup"><span data-stu-id="385cb-128">**macOS**: typing `code` in your terminal</span></span>
   1. <span data-ttu-id="385cb-129">按下 <kbd>Ctrl</kbd>+<kbd>P</kbd> 來啟動 Windows 或 Linux 上的 **Quick Open**。</span><span class="sxs-lookup"><span data-stu-id="385cb-129">Launch **Quick Open** on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="385cb-130">針對 macOS，則按下 <kbd>Cmd</kbd>+<kbd>P</kbd>。</span><span class="sxs-lookup"><span data-stu-id="385cb-130">On macOS, press <kbd>Cmd</kbd>+<kbd>P</kbd>.</span></span>
   1. <span data-ttu-id="385cb-131">在 Quick Open 中，鍵入 `ext install powershell`，然後按下 [輸入]  。</span><span class="sxs-lookup"><span data-stu-id="385cb-131">In Quick Open, type `ext install powershell` and press **Enter**.</span></span>
   1. <span data-ttu-id="385cb-132">提要欄位上隨即開啟 [延伸模組]  檢視。</span><span class="sxs-lookup"><span data-stu-id="385cb-132">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="385cb-133">從 Microsoft 選取 PowerShell 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="385cb-133">Select the PowerShell extension from Microsoft.</span></span>
      <span data-ttu-id="385cb-134">您應該會看到類似下圖的 VSCode 畫面：</span><span class="sxs-lookup"><span data-stu-id="385cb-134">You should see a VSCode screen similar to the following image:</span></span>

      ![VSCode](../../images/using-vscode/vscode.png)

   1. <span data-ttu-id="385cb-136">從 Microsoft 按一下 PowerShell 延伸模組的 [安裝]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="385cb-136">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
   1. <span data-ttu-id="385cb-137">安裝之後，您會看到 [安裝]  按鈕變成 [重新載入]  。</span><span class="sxs-lookup"><span data-stu-id="385cb-137">After the install, you see the **Install** button turns to **Reload**.</span></span> <span data-ttu-id="385cb-138">按一下 [重新載入]  。</span><span class="sxs-lookup"><span data-stu-id="385cb-138">Click on **Reload**.</span></span>
   1. <span data-ttu-id="385cb-139">重新載入 VSCode 之後，即可進行編輯。</span><span class="sxs-lookup"><span data-stu-id="385cb-139">After VSCode has reloaded, you're ready for editing.</span></span>

<span data-ttu-id="385cb-140">例如，若要建立新的檔案，請按一下 [檔案] > [新增]  。</span><span class="sxs-lookup"><span data-stu-id="385cb-140">For example, to create a new file, click **File > New**.</span></span> <span data-ttu-id="385cb-141">若要儲存，請按一下 [檔案] > [儲存]  ，然後提供檔案名稱，例如 `HelloWorld.ps1`。</span><span class="sxs-lookup"><span data-stu-id="385cb-141">To save it, click **File > Save** and then provide a file name, such as `HelloWorld.ps1`.</span></span> <span data-ttu-id="385cb-142">若要關閉檔案，請按一下檔案名稱旁邊的 `X`。</span><span class="sxs-lookup"><span data-stu-id="385cb-142">To close the file, click the `X` next to the file name.</span></span> <span data-ttu-id="385cb-143">若要結束 VSCode，請按一下 [檔案] > [結束]  。</span><span class="sxs-lookup"><span data-stu-id="385cb-143">To exit VSCode, **File > Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="385cb-144">在受限制的系統上安裝 PowerShell 延伸模組</span><span class="sxs-lookup"><span data-stu-id="385cb-144">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="385cb-145">某些系統已設定為需要檢查所有程式碼簽章，且必須以手動方式核准 PowerShell Editor Services，才能在系統上執行。</span><span class="sxs-lookup"><span data-stu-id="385cb-145">Some systems are set up in a way that requires all code signatures to be checked and requires PowerShell Editor Services to be manually approved to run on the system.</span></span> <span data-ttu-id="385cb-146">如果已經安裝 PowerShell 延伸模組，但發生下列錯誤，則可能原因是變更執行原則的群組原則更新：</span><span class="sxs-lookup"><span data-stu-id="385cb-146">A Group Policy update that changes execution policy is a likely cause if you've installed the PowerShell extension but are receiving an error such as:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="385cb-147">若要手動核准 PowerShell Editor Services 以及適用於 VSCode 的 PowerShell 延伸模組，請開啟 PowerShell 提示字元並執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="385cb-147">To manually approve PowerShell Editor Services and the PowerShell extension for VSCode, open a PowerShell prompt and run the following command:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="385cb-148">系統會提示您**要執行來自這個不受信任的發行者的軟體嗎？**</span><span class="sxs-lookup"><span data-stu-id="385cb-148">You're prompted with **Do you want to run software from this untrusted publisher?**</span></span> <span data-ttu-id="385cb-149">輸入 `A` 以執行檔案。</span><span class="sxs-lookup"><span data-stu-id="385cb-149">Type `A` to run the file.</span></span> <span data-ttu-id="385cb-150">然後，開啟 VSCode 並檢查 PowerShell 延伸模組是否正常運作。</span><span class="sxs-lookup"><span data-stu-id="385cb-150">Then, open VSCode and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="385cb-151">如果您仍有關於開始使用的問題，請透過 [GitHub](https://github.com/PowerShell/vscode-powershell/issues) \(英文\) 讓我們知道。</span><span class="sxs-lookup"><span data-stu-id="385cb-151">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="385cb-152">選擇要與擴充功能搭配使用的 PowerShell 版本</span><span class="sxs-lookup"><span data-stu-id="385cb-152">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="385cb-153">透過與 Windows PowerShell 並存安裝的 PowerShell Core，其現在能夠將特定版本的 PowerShell 與 PowerShell 延伸模組搭配使用。</span><span class="sxs-lookup"><span data-stu-id="385cb-153">With PowerShell Core installing side-by-side with Windows PowerShell, it's now possible to use a particular version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="385cb-154">使用下列步驟來選擇版本：</span><span class="sxs-lookup"><span data-stu-id="385cb-154">Use the following steps to choose the version:</span></span>

1. <span data-ttu-id="385cb-155">按下 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> 來開啟 Windows 或 Linux 上的 [命令選擇區]  。</span><span class="sxs-lookup"><span data-stu-id="385cb-155">Open the **Command Palette** on Windows or Linux with <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="385cb-156">若為 macOS，請按下 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>。</span><span class="sxs-lookup"><span data-stu-id="385cb-156">On macOS, use <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span>
1. <span data-ttu-id="385cb-157">搜尋**工作階段**。</span><span class="sxs-lookup"><span data-stu-id="385cb-157">Search for **Session**.</span></span>
1. <span data-ttu-id="385cb-158">按一下 [PowerShell:  顯示工作階段功能表]。</span><span class="sxs-lookup"><span data-stu-id="385cb-158">Click on **PowerShell: Show Session Menu**.</span></span>
1. <span data-ttu-id="385cb-159">從清單中選擇要使用的 PowerShell 版本，例如：**PowerShell Core**。</span><span class="sxs-lookup"><span data-stu-id="385cb-159">Choose the version of PowerShell you want to use from the list, for example: **PowerShell Core**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="385cb-160">此功能會查看不同作業系統上的一些已知路徑，以探索 PowerShell 的安裝位置。</span><span class="sxs-lookup"><span data-stu-id="385cb-160">This feature looks at a few well-known paths on different operating systems to discover install locations of PowerShell.</span></span> <span data-ttu-id="385cb-161">如果您已將 PowerShell 安裝到非典型位置，則它一開始可能不會顯示於工作階段功能表中。</span><span class="sxs-lookup"><span data-stu-id="385cb-161">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="385cb-162">您可以藉由[新增自己的自訂路徑](#adding-your-own-powershell-paths-to-the-session-menu)來擴充工作階段功能表，如下所述。</span><span class="sxs-lookup"><span data-stu-id="385cb-162">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

>[!NOTE]
> <span data-ttu-id="385cb-163">還有另一種方式可前往工作階段功能表。</span><span class="sxs-lookup"><span data-stu-id="385cb-163">There's another way to get to the session menu.</span></span> <span data-ttu-id="385cb-164">在您的編輯器中開啟 PowerShell 檔案時，您會在右下角看到綠色的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="385cb-164">When a PowerShell file is open in your editor, you see a green version number in the bottom right.</span></span> <span data-ttu-id="385cb-165">按一下此版本號碼，即會帶您前往工作階段功能表。</span><span class="sxs-lookup"><span data-stu-id="385cb-165">Clicking this version number will bring you to the session menu.</span></span>

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="385cb-166">將您自己的 PowerShell 路徑新增至工作階段功能表</span><span class="sxs-lookup"><span data-stu-id="385cb-166">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="385cb-167">您可以透過 VSCode 設定，將其他 PowerShell 可執行檔路徑新增至工作階段功能表。</span><span class="sxs-lookup"><span data-stu-id="385cb-167">You can add other PowerShell executable paths to the session menu through a VSCode setting.</span></span>

<span data-ttu-id="385cb-168">將項目新增至清單 `powershell.powerShellAdditionalExePaths` 或建立清單 (如果它不存在您的 `settings.json` 中)：</span><span class="sxs-lookup"><span data-stu-id="385cb-168">Add an item to the list `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

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

<span data-ttu-id="385cb-169">每個項目都必須具備：</span><span class="sxs-lookup"><span data-stu-id="385cb-169">Each item must have:</span></span>

* <span data-ttu-id="385cb-170">`exePath`:`pwsh` 或 `powershell` 可執行檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="385cb-170">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
* <span data-ttu-id="385cb-171">`versionName`:將顯示於工作階段功能表中的文字。</span><span class="sxs-lookup"><span data-stu-id="385cb-171">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="385cb-172">您可以將此文字設定為要顯示於工作階段功能表 (也稱為最後一個設定中的 `versionName`) 中的文字，藉以使用 `powershell.powerShellDefaultVersion` 設定來設定要使用的預設 PowerShell 版本：</span><span class="sxs-lookup"><span data-stu-id="385cb-172">You can set the default PowerShell version to use the `powershell.powerShellDefaultVersion` setting by setting this to the text displayed in the session menu (also known as the `versionName` in the last setting):</span></span>

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

<span data-ttu-id="385cb-173">當完成此設定之後，請重新開機 VSCode，或從 [命令選擇區]  重新載入目前的 VSCode 視窗，並鍵入 [Developer:  重新載入視窗]。</span><span class="sxs-lookup"><span data-stu-id="385cb-173">After you've configured this setting, restart VSCode or to reload the current VSCode window from the **Command Palette**, type **Developer: Reload Window**.</span></span>

<span data-ttu-id="385cb-174">如果您開啟工作階段功能表，現在將會看到您其他的 PowerShell 版本！</span><span class="sxs-lookup"><span data-stu-id="385cb-174">If you open the session menu, you now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="385cb-175">如果您從來源建置 PowerShell，則這是最適合用來測試 PowerShell 本機組建的方式。</span><span class="sxs-lookup"><span data-stu-id="385cb-175">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

### <a name="configuration-settings-for-vscode"></a><span data-ttu-id="385cb-176">編輯 VSCode 組態設定</span><span class="sxs-lookup"><span data-stu-id="385cb-176">Configuration settings for VSCode</span></span>

<span data-ttu-id="385cb-177">使用先前段落中的步驟，您可以在 `settings.json` 中新增組態設定。</span><span class="sxs-lookup"><span data-stu-id="385cb-177">By using the steps in the previous paragraph, you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="385cb-178">我們建議下列 VSCode 組態設定：</span><span class="sxs-lookup"><span data-stu-id="385cb-178">We recommend the following configuration settings for VSCode:</span></span>

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

<span data-ttu-id="385cb-179">如果您不希望這些設定影響所有的檔案類型，VSCode 也允許依照語言的設定。</span><span class="sxs-lookup"><span data-stu-id="385cb-179">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="385cb-180">將設定放入 `[<language-name>]` 欄位，建立語言特定設定。</span><span class="sxs-lookup"><span data-stu-id="385cb-180">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="385cb-181">例如：</span><span class="sxs-lookup"><span data-stu-id="385cb-181">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="385cb-182">如需 VSCode 中檔案編碼的詳細資訊，請參閱[了解檔案編碼](understanding-file-encoding.md)。</span><span class="sxs-lookup"><span data-stu-id="385cb-182">For more information about file encoding in VSCode, see [Understanding file encoding](understanding-file-encoding.md).</span></span>

## <a name="debugging-with-vscode"></a><span data-ttu-id="385cb-183">使用 VSCode 進行偵錯</span><span class="sxs-lookup"><span data-stu-id="385cb-183">Debugging with VSCode</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="385cb-184">無工作區偵錯</span><span class="sxs-lookup"><span data-stu-id="385cb-184">No-workspace debugging</span></span>

<span data-ttu-id="385cb-185">使用 VSCode 1.9 版可以對 PowerShell 指令碼進行偵錯，而無須開啟包含 PowerShell 指令碼的資料夾。</span><span class="sxs-lookup"><span data-stu-id="385cb-185">As of VSCode version 1.9 you can debug PowerShell scripts without opening the folder that contains the PowerShell script.</span></span> <span data-ttu-id="385cb-186">以 [檔案] > [開啟檔案...]  開啟 PowerShell 指令碼檔案，在行上設定中斷點，依序按下 <kbd>F9</kbd> 和 <kbd>F5</kbd> 來開始偵錯。</span><span class="sxs-lookup"><span data-stu-id="385cb-186">Open the PowerShell script file with **File > Open File...**, set a breakpoint on a line, press <kbd>F9</kbd>, and then press <kbd>F5</kbd> to start debugging.</span></span> <span data-ttu-id="385cb-187">[偵錯動作] 窗格應該會隨即出現，您可在該窗格中進行偵錯工具、步驟、繼續和停止偵錯。</span><span class="sxs-lookup"><span data-stu-id="385cb-187">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume, and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="385cb-188">工作區偵錯</span><span class="sxs-lookup"><span data-stu-id="385cb-188">Workspace debugging</span></span>

<span data-ttu-id="385cb-189">工作區偵錯是指使用 [開啟資料夾...]  來在 [檔案]  功能表的 Visual Studio Code 中對已開啟的資料夾內容進行偵錯。您開啟的資料夾通常是 PowerShell 專案資料夾及/或 Git 存放庫的根目錄。</span><span class="sxs-lookup"><span data-stu-id="385cb-189">Workspace debugging refers to debugging in the context of a folder that you've opened in Visual Studio Code from the **File** menu using **Open Folder...**. The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="385cb-190">即使在此模式中，只要按下 <kbd>F5</kbd> 就可以開始針對目前選取的 PowerShell 指令碼進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="385cb-190">Even in this mode, you can start debugging the currently selected PowerShell script by pressing <kbd>F5</kbd>.</span></span> <span data-ttu-id="385cb-191">不過，工作區偵錯可讓您定義多個偵錯設定，不只是偵錯目前開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="385cb-191">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span> <span data-ttu-id="385cb-192">例如，您可以新增設定以：</span><span class="sxs-lookup"><span data-stu-id="385cb-192">For instance, you can add a configuration to:</span></span>

- <span data-ttu-id="385cb-193">啟動偵錯工具中的 Pester 測試。</span><span class="sxs-lookup"><span data-stu-id="385cb-193">Launch Pester tests in the debugger.</span></span>
- <span data-ttu-id="385cb-194">以偵錯工具中的引數啟動特定檔案。</span><span class="sxs-lookup"><span data-stu-id="385cb-194">Launch a specific file with arguments in the debugger.</span></span>
- <span data-ttu-id="385cb-195">啟動偵錯工具中的互動式工作階段。</span><span class="sxs-lookup"><span data-stu-id="385cb-195">Launch an interactive session in the debugger.</span></span>
- <span data-ttu-id="385cb-196">將偵錯工具附加至 PowerShell 主機處理程序。</span><span class="sxs-lookup"><span data-stu-id="385cb-196">Attach the debugger to a PowerShell host process.</span></span>

<span data-ttu-id="385cb-197">請遵循下列步驟建立您的偵錯設定檔：</span><span class="sxs-lookup"><span data-stu-id="385cb-197">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="385cb-198">按下 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd> 以開啟 [偵錯]  檢視。</span><span class="sxs-lookup"><span data-stu-id="385cb-198">Open the **Debug** view on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span> <span data-ttu-id="385cb-199">若為 macOS，請按下 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>。</span><span class="sxs-lookup"><span data-stu-id="385cb-199">On macOS, press <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span>
  1. <span data-ttu-id="385cb-200">按一下工具列中的**設定**齒輪圖示。</span><span class="sxs-lookup"><span data-stu-id="385cb-200">Click the **Configure** gear icon in the toolbar.</span></span>
  1. <span data-ttu-id="385cb-201">VSCode 會提示您 [選取環境]  。</span><span class="sxs-lookup"><span data-stu-id="385cb-201">VSCode prompts you to **Select Environment**.</span></span> <span data-ttu-id="385cb-202">選擇 [PowerShell]  。</span><span class="sxs-lookup"><span data-stu-id="385cb-202">Choose **PowerShell**.</span></span>

<span data-ttu-id="385cb-203">接著 VSCode 會在工作區資料夾的根目錄中建立目錄和檔案 `.vscode\launch.json`。</span><span class="sxs-lookup"><span data-stu-id="385cb-203">The result is that VSCode creates a directory and a file `.vscode\launch.json` in the root of your workspace folder.</span></span> <span data-ttu-id="385cb-204">該位置為儲存偵錯設定的位置。</span><span class="sxs-lookup"><span data-stu-id="385cb-204">This location is where your debug configuration is stored.</span></span> <span data-ttu-id="385cb-205">如果檔案是在 Git 存放庫中，您通常要修訂 `launch.json` 檔案。</span><span class="sxs-lookup"><span data-stu-id="385cb-205">If your files are in a Git repository, you typically want to commit the `launch.json` file.</span></span> <span data-ttu-id="385cb-206">`launch.json` 檔案的內容如下：</span><span class="sxs-lookup"><span data-stu-id="385cb-206">The contents of the `launch.json` file are:</span></span>

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

<span data-ttu-id="385cb-207">此檔案表示常見的偵錯案例。</span><span class="sxs-lookup"><span data-stu-id="385cb-207">This file represents the common debug scenarios.</span></span> <span data-ttu-id="385cb-208">當在編輯器中開啟這個檔案時，您會看到 [新增設定...]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="385cb-208">When you open this file in the editor, you see an **Add Configuration...** button.</span></span> <span data-ttu-id="385cb-209">您可以按一下此按鈕來新增多個 PowerShell 偵錯設定。</span><span class="sxs-lookup"><span data-stu-id="385cb-209">You can click this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="385cb-210">PowerShell: **啟動指令碼**是可以新增的方便設定。</span><span class="sxs-lookup"><span data-stu-id="385cb-210">One useful configuration to add is **PowerShell: Launch Script**.</span></span> <span data-ttu-id="385cb-211">使用此設定時，您可以指定有選擇性引數的檔案，無論編輯器中當時作用中的是哪個檔案，只要按下 <kbd>F5</kbd> 應該就會啟動。</span><span class="sxs-lookup"><span data-stu-id="385cb-211">With this configuration, you can specify a file with optional arguments that should be launched whenever you press <kbd>F5</kbd> no matter which file is currently active in the editor.</span></span>

<span data-ttu-id="385cb-212">建立偵錯設定之後，您可以選取在偵錯工作階段期間想要使用的設定。</span><span class="sxs-lookup"><span data-stu-id="385cb-212">After the debug configuration is established, you can select which configuration you want to use during a debug session.</span></span> <span data-ttu-id="385cb-213">從 [偵錯]  檢視工具列的 [偵錯設定] 下拉式清單中選取設定。</span><span class="sxs-lookup"><span data-stu-id="385cb-213">Select a configuration from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="385cb-214">有幾個部落格可以協助您開始使用適用於 Visual Studio Code 的 PowerShell 擴充功能：</span><span class="sxs-lookup"><span data-stu-id="385cb-214">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="385cb-215">[PowerShell 延伸模組][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="385cb-215">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="385cb-216">[在 Visual Studio Code 中撰寫和偵錯 PowerShell 指令碼][debug]</span><span class="sxs-lookup"><span data-stu-id="385cb-216">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="385cb-217">[偵錯 Visual Studio Code 指引][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="385cb-217">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="385cb-218">[在 Visual Studio Code 中偵錯 PowerShell][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="385cb-218">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="385cb-219">[開始使用 Visual Studio Code 中的 PowerShell 開發][getting-started]</span><span class="sxs-lookup"><span data-stu-id="385cb-219">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="385cb-220">[適用於 PowerShell 開發的 Visual Studio Code 編輯功能 – 第 1 部分][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="385cb-220">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="385cb-221">[適用於 PowerShell 開發的 Visual Studio Code 編輯功能 – 第 2 部分][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="385cb-221">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="385cb-222">[在 Visual Studio Code 中偵錯 PowerShell 指令碼 – 第 1 部分][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="385cb-222">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="385cb-223">[在 Visual Studio Code 中偵錯 PowerShell 指令碼 – 第 2 部分][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="385cb-223">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

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

## <a name="powershell-extension-for-vscode"></a><span data-ttu-id="385cb-224">適用於 VSCode 的 PowerShell 延伸模組</span><span class="sxs-lookup"><span data-stu-id="385cb-224">PowerShell Extension for VSCode</span></span>

<span data-ttu-id="385cb-225">[GitHub](https://github.com/PowerShell/vscode-powershell) 上可以找到 PowerShell 延伸模組的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="385cb-225">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
