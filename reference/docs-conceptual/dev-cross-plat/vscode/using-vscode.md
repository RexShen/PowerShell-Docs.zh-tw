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
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="fcf8e-103">使用 Visual Studio Code 開發 PowerShell</span><span class="sxs-lookup"><span data-stu-id="fcf8e-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="fcf8e-104">[Visual Studio Code][vscode] 是 Microsoft 提供的跨平台指令碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-104">[Visual Studio Code][vscode] is a cross-platform script editor by Microsoft.</span></span> <span data-ttu-id="fcf8e-105">搭配 [PowerShell 擴充功能][psext]，其提供了豐富的互動式指令碼編輯體驗，讓您更輕鬆地撰寫可靠的 PowerShell 指令碼。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-105">Together with the [PowerShell extension][psext], it provides a rich and interactive script editing experience, making it easier to write reliable PowerShell scripts.</span></span> <span data-ttu-id="fcf8e-106">Visual Studio Code 搭配 PowerShell 延伸模組是撰寫 PowerShell 指令碼的建議編輯器。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-106">Visual Studio Code with the PowerShell extension is the recommended editor for writing PowerShell scripts.</span></span>

<span data-ttu-id="fcf8e-107">其支援下列 PowerShell 版本：</span><span class="sxs-lookup"><span data-stu-id="fcf8e-107">It supports the following PowerShell versions:</span></span>

- <span data-ttu-id="fcf8e-108">PowerShell 7 與更新版本 (Windows、macOS 與 Linux)</span><span class="sxs-lookup"><span data-stu-id="fcf8e-108">PowerShell 7 and up (Windows, macOS, and Linux)</span></span>
- <span data-ttu-id="fcf8e-109">PowerShell Core 6 (Windows、macOS 與 Linux)</span><span class="sxs-lookup"><span data-stu-id="fcf8e-109">PowerShell Core 6 (Windows, macOS, and Linux)</span></span>
- <span data-ttu-id="fcf8e-110">Windows PowerShell 5.1 (僅限 Windows)</span><span class="sxs-lookup"><span data-stu-id="fcf8e-110">Windows PowerShell 5.1 (Windows-only)</span></span>

> [!NOTE]
> <span data-ttu-id="fcf8e-111">Visual Studio Code 與 [Visual Studio][] 不同。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-111">Visual Studio Code is not the same as [Visual Studio][].</span></span>

## <a name="getting-started"></a><span data-ttu-id="fcf8e-112">開始使用</span><span class="sxs-lookup"><span data-stu-id="fcf8e-112">Getting started</span></span>

<span data-ttu-id="fcf8e-113">在開始前，請先確定系統上有 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-113">Before you begin, make sure PowerShell exists on your system.</span></span> <span data-ttu-id="fcf8e-114">如需 Windows、macOS 和 Linux 上的新型工作負載，請參閱下列連結：</span><span class="sxs-lookup"><span data-stu-id="fcf8e-114">For modern workloads on Windows, macOS, and Linux, see the following links:</span></span>

- <span data-ttu-id="fcf8e-115">[在 Linux 上安裝 PowerShell][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="fcf8e-115">[Installing PowerShell on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="fcf8e-116">[在 macOS 上安裝 PowerShell][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="fcf8e-116">[Installing PowerShell on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="fcf8e-117">[在 Windows 上安裝 PowerShell][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="fcf8e-117">[Installing PowerShell on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="fcf8e-118">若為傳統的 Windows PowerShell 工作負載，請參閱[安裝 Windows PowerShell][install-winps]。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-118">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fcf8e-119">Windows 仍可供 [Windows PowerShell ISE][ise] 使用。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-119">The [Windows PowerShell ISE][ise] is still available for Windows.</span></span> <span data-ttu-id="fcf8e-120">不過，其不再有進行中功能開發。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-120">However, it is no longer in active feature development.</span></span> <span data-ttu-id="fcf8e-121">ISE 無法搭配 PowerShell 6 與更新版本使用。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-121">The ISE does not work with PowerShell 6 and higher.</span></span> <span data-ttu-id="fcf8e-122">因為其是 Windows 的元件，所以官方仍會繼續支援其安全性與高優先順序的維護修正。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-122">As a component of Windows, it continues to be officially supported for security and high-priority servicing fixes.</span></span>
> <span data-ttu-id="fcf8e-123">我們沒有計劃要將 ISE 從 Windows 移除。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-123">We have no plans to remove the ISE from Windows.</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="fcf8e-124">使用 Visual Studio Code 編輯</span><span class="sxs-lookup"><span data-stu-id="fcf8e-124">Editing with Visual Studio Code</span></span>

1. <span data-ttu-id="fcf8e-125">安裝 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-125">Install Visual Studio Code.</span></span> <span data-ttu-id="fcf8e-126">如需詳細資訊，請參閱 [Setting up Visual Studio Code][vsc-setup] (設定 Visual Studio Code) 概觀。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-126">For more information, see the overview [Setting up Visual Studio Code][vsc-setup].</span></span>

   <span data-ttu-id="fcf8e-127">下列為每個平台的安裝指示：</span><span class="sxs-lookup"><span data-stu-id="fcf8e-127">There are installation instructions for each platform:</span></span>

   - <span data-ttu-id="fcf8e-128">**Windows**：遵循[在 Windows 上執行 Visual Studio Code][vsc-setup-win] \(英文\) 頁面的安裝指示操作。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-128">**Windows**: follow the installation instructions on the [Running Visual Studio Code on Windows][vsc-setup-win] page.</span></span>
   - <span data-ttu-id="fcf8e-129">**macOS**：遵循[在 macOS 上執行 Visual Studio Code][vsc-setup-macOS] \(英文\) 頁面的安裝指示操作。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-129">**macOS**: follow the installation instructions on the [Running Visual Studio Code on macOS][vsc-setup-macOS] page.</span></span>
   - <span data-ttu-id="fcf8e-130">**Linux**：遵循[在 Linux 上執行 Visual Studio Code][vsc-setup-linux] \(英文\) 頁面的安裝指示操作。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-130">**Linux**: follow the installation instructions on the [Running Visual Studio Code on Linux][vsc-setup-linux] page.</span></span>

1. <span data-ttu-id="fcf8e-131">安裝 PowerShell 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-131">Install the PowerShell Extension.</span></span>

   1. <span data-ttu-id="fcf8e-132">如果您已安裝 Visual Studio Code Insiders，請透過在主控台中輸入 `code` 或 `code-insiders` 以啟動 Visual Studio Code 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-132">Launch the Visual Studio Code app by typing `code` in a console or `code-insiders` if you installed Visual Studio Code Insiders.</span></span>
   1. <span data-ttu-id="fcf8e-133">按下 <kbd>Ctrl</kbd>+<kbd>P</kbd> 來啟動 Windows 或 Linux 上的 **Quick Open**。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-133">Launch **Quick Open** on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="fcf8e-134">針對 macOS，則按下 <kbd>Cmd</kbd>+<kbd>P</kbd>。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-134">On macOS, press <kbd>Cmd</kbd>+<kbd>P</kbd>.</span></span>
   1. <span data-ttu-id="fcf8e-135">在 Quick Open 中，鍵入 `ext install powershell`，然後按下 [輸入]  。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-135">In Quick Open, type `ext install powershell` and press **Enter**.</span></span>
   1. <span data-ttu-id="fcf8e-136">提要欄位上隨即開啟 [延伸模組]  檢視。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-136">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="fcf8e-137">從 Microsoft 選取 PowerShell 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-137">Select the PowerShell extension from Microsoft.</span></span>
      <span data-ttu-id="fcf8e-138">您應該會看到類似下圖的 Visual Studio Code 畫面：</span><span class="sxs-lookup"><span data-stu-id="fcf8e-138">You should see a Visual Studio Code screen similar to the following image:</span></span>

      ![Visual Studio Code](media/using-vscode/vscode.png)

   1. <span data-ttu-id="fcf8e-140">從 Microsoft 按一下 PowerShell 延伸模組的 [安裝]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-140">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
   1. <span data-ttu-id="fcf8e-141">安裝之後，若您看到 [安裝]  按鈕變成 [重新載入]  ，請按一下 [重新載入]  。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-141">After the install, if you see the **Install** button turn into **Reload**, Click on **Reload**.</span></span>
   1. <span data-ttu-id="fcf8e-142">重新載入 Visual Studio Code 之後，就可以進行編輯。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-142">After Visual Studio Code has reloaded, you're ready for editing.</span></span>

<span data-ttu-id="fcf8e-143">例如，若要建立新的檔案，請按一下 [檔案] > [新增]  。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-143">For example, to create a new file, click **File > New**.</span></span> <span data-ttu-id="fcf8e-144">若要儲存，請按一下 [檔案] > [儲存]  ，然後提供檔案名稱，例如 `HelloWorld.ps1`。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-144">To save it, click **File > Save** and then provide a file name, such as `HelloWorld.ps1`.</span></span> <span data-ttu-id="fcf8e-145">若要關閉檔案，請按一下檔案名稱旁邊的 `X`。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-145">To close the file, click the `X` next to the file name.</span></span> <span data-ttu-id="fcf8e-146">若要結束 Visual Studio Code，請移至 [檔案] > [結束]  。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-146">To exit Visual Studio Code, **File > Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="fcf8e-147">在受限制的系統上安裝 PowerShell 延伸模組</span><span class="sxs-lookup"><span data-stu-id="fcf8e-147">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="fcf8e-148">某些系統已設定為需要所有程式碼簽章的驗證。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-148">Some systems are set up to require validation of all code signatures.</span></span> <span data-ttu-id="fcf8e-149">您可能收到下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="fcf8e-149">You may receive the following error:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="fcf8e-150">當 PowerShell 的執行原則是由 Windows 群組原則設定時，可能會發生此問題。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-150">This problem can occur when PowerShell's execution policy is set by Windows Group Policy.</span></span> <span data-ttu-id="fcf8e-151">若要手動核准 PowerShell Editor Services 與適用於 Visual Studio Code 的 PowerShell 延伸模組，請開啟 PowerShell 提示字元並執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="fcf8e-151">To manually approve PowerShell Editor Services and the PowerShell extension for Visual Studio Code, open a PowerShell prompt and run the following command:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="fcf8e-152">系統會提示您**要執行來自這個不受信任的發行者的軟體嗎？**</span><span class="sxs-lookup"><span data-stu-id="fcf8e-152">You're prompted with **Do you want to run software from this untrusted publisher?**</span></span> <span data-ttu-id="fcf8e-153">輸入 `A` 以執行檔案。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-153">Type `A` to run the file.</span></span> <span data-ttu-id="fcf8e-154">然後，開啟 Visual Studio Code 並檢查 PowerShell 延伸模組是否正常運作。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-154">Then, open Visual Studio Code and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="fcf8e-155">如果您仍有關於開始使用的問題，請透過 [GitHub 問題][]讓我們知道。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-155">If you still have problems getting started, let us know on [GitHub issues][].</span></span>

> [!NOTE]
> <span data-ttu-id="fcf8e-156">適用於 Visual Studio Code 的 PowerShell 延伸模組不支援在限制語言模式中執行。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-156">The PowerShell extension for Visual Studio Code does not support running in constrained language mode.</span></span> <span data-ttu-id="fcf8e-157">如需詳細資訊，請參閱 [GitHub 問題 #606][i606]。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-157">For more information, see [GitHub issue #606][i606].</span></span>

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="fcf8e-158">選擇要與擴充功能搭配使用的 PowerShell 版本</span><span class="sxs-lookup"><span data-stu-id="fcf8e-158">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="fcf8e-159">有了與 Windows PowerShell 並存安裝的 PowerShell Core 之後，現在能夠將特定版本的 PowerShell 與 PowerShell 擴充功能搭配使用。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-159">With PowerShell Core installing side-by-side with Windows PowerShell, it's now possible to use a specific version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="fcf8e-160">此功能會查看不同作業系統上的一些已知路徑，以探索 PowerShell 的安裝位置。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-160">This feature looks at a few well-known paths on different operating systems to discover installations of PowerShell.</span></span>

<span data-ttu-id="fcf8e-161">使用下列步驟來選擇版本：</span><span class="sxs-lookup"><span data-stu-id="fcf8e-161">Use the following steps to choose the version:</span></span>

1. <span data-ttu-id="fcf8e-162">按下 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> 來開啟 Windows 或 Linux 上的 [命令選擇區]  。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-162">Open the **Command Palette** on Windows or Linux with <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="fcf8e-163">若為 macOS，請按下 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-163">On macOS, use <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span>
1. <span data-ttu-id="fcf8e-164">搜尋**工作階段**。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-164">Search for **Session**.</span></span>
1. <span data-ttu-id="fcf8e-165">按一下 [PowerShell:  顯示工作階段功能表]。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-165">Click on **PowerShell: Show Session Menu**.</span></span>
1. <span data-ttu-id="fcf8e-166">從清單中選擇要使用的 PowerShell 版本，例如：**PowerShell Core**。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-166">Choose the version of PowerShell you want to use from the list, for example: **PowerShell Core**.</span></span>

<span data-ttu-id="fcf8e-167">如果您已將 PowerShell 安裝到非典型位置，則它一開始可能不會顯示於工作階段功能表中。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-167">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="fcf8e-168">您可以藉由[新增自己的自訂路徑](#adding-your-own-powershell-paths-to-the-session-menu)來擴充工作階段功能表，如下所述。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-168">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

> [!NOTE]
> <span data-ttu-id="fcf8e-169">您也可以從狀態列右下角的綠色版本號碼存取 PowerShell 工作階段功能表。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-169">The PowerShell session menu can also be accessed from the green version number in the bottom right corner of status bar.</span></span> <span data-ttu-id="fcf8e-170">按一下此版本號碼，即會開啟工作階段功能表。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-170">Clicking this version number opens the session menu.</span></span>

## <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="fcf8e-171">Visual Studio Code 的組態設定</span><span class="sxs-lookup"><span data-stu-id="fcf8e-171">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="fcf8e-172">首先，如果您不熟悉如何在 Visual Studio Code 中變更設定，建議您閱讀 [Visual Studio Code 的設定][vsc-settings]文件。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-172">First, if you're not familiar with how to change settings in Visual Studio Code, we recommend reading [Visual Studio Code's settings][vsc-settings] documentation.</span></span>

<span data-ttu-id="fcf8e-173">閱讀文件之後，您可以在 `settings.json` 中新增組態設定。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-173">After reading the documentation, you can add configuration settings in `settings.json`.</span></span>

```json
{
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="fcf8e-174">如果您不希望這些設定影響所有檔案類型，Visual Studio Code 也允許個別語言設定。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-174">If you don't want these settings to affect all files types, Visual Studio Code also allows per-language configurations.</span></span> <span data-ttu-id="fcf8e-175">將設定放入 `[<language-name>]` 欄位，建立語言特定設定。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-175">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="fcf8e-176">例如：</span><span class="sxs-lookup"><span data-stu-id="fcf8e-176">For example:</span></span>

```json
{
    "[powershell]": {
        "files.encoding": "utf8bom",
        "files.autoGuessEncoding": true
    }
}
```

> [!TIP]
> <span data-ttu-id="fcf8e-177">如需有關 Visual Studio Code 中檔案編碼的詳細資訊，請參閱[了解檔案編碼][file-encoding]。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-177">For more information about file encoding in Visual Studio Code, see [Understanding file encoding][file-encoding].</span></span>
>
> <span data-ttu-id="fcf8e-178">另請參閱[如何在 Visual Studio Code 中複寫 ISE 體驗][vsc-ise]，以取得有關如何設定 Visual Studio Code 以進行 PowerShell 編輯的其他提示。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-178">Also, check out [How to replicate the ISE experience in Visual Studio Code][vsc-ise] for other tips on how to configure Visual Studio Code for PowerShell editing.</span></span>

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="fcf8e-179">將您自己的 PowerShell 路徑新增至工作階段功能表</span><span class="sxs-lookup"><span data-stu-id="fcf8e-179">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="fcf8e-180">您可以透過 [Visual Studio Code 設定](https://code.visualstudio.com/docs/getstarted/settings) \(英文\)，將其他 PowerShell 可執行檔路徑新增至工作階段功能表：`powershell.powerShellAdditionalExePaths`。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-180">You can add other PowerShell executable paths to the session menu through the [Visual Studio Code setting](https://code.visualstudio.com/docs/getstarted/settings): `powershell.powerShellAdditionalExePaths`.</span></span>

<span data-ttu-id="fcf8e-181">將項目新增至清單 `powershell.powerShellAdditionalExePaths` 或建立清單 (如果它不存在您的 `settings.json` 中)：</span><span class="sxs-lookup"><span data-stu-id="fcf8e-181">Add an item to the list `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

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

<span data-ttu-id="fcf8e-182">每個項目都必須具備：</span><span class="sxs-lookup"><span data-stu-id="fcf8e-182">Each item must have:</span></span>

- <span data-ttu-id="fcf8e-183">`exePath`:`pwsh` 或 `powershell` 可執行檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-183">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
- <span data-ttu-id="fcf8e-184">`versionName`:將顯示於工作階段功能表中的文字。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-184">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="fcf8e-185">若要設定預設 PowerShell 版本，請將值 `powershell.powerShellDefaultVersion` 設定為工作階段功能表中所顯示的文字 (亦稱為 `versionName`)：</span><span class="sxs-lookup"><span data-stu-id="fcf8e-185">To set the default PowerShell version, set the value `powershell.powerShellDefaultVersion` to the text displayed in the session menu (also known as the `versionName`):</span></span>

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

<span data-ttu-id="fcf8e-186">當完成此設定之後，請重新啟動 Visual Studio Code，或從 命令選擇區  重新載入目前的 Visual Studio Code 視窗，並輸入 **Developer:** 重新載入視窗。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-186">After you've configured this setting, restart Visual Studio Code or to reload the current Visual Studio Code window from the **Command Palette**, type **Developer: Reload Window**.</span></span>

<span data-ttu-id="fcf8e-187">如果您開啟工作階段功能表，現在將會看到您其他的 PowerShell 版本！</span><span class="sxs-lookup"><span data-stu-id="fcf8e-187">If you open the session menu, you now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="fcf8e-188">如果您從來源建置 PowerShell，則這是最適合用來測試 PowerShell 本機組建的方式。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-188">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

### <a name="using-an-older-version-of-the-powershell-extension-for-windows-powershell-v3-and-v4"></a><span data-ttu-id="fcf8e-189">針對 Windows PowerShell v3 與 v4 使用較舊版本的 PowerShell 延伸模組</span><span class="sxs-lookup"><span data-stu-id="fcf8e-189">Using an older version of the PowerShell Extension for Windows PowerShell v3 and v4</span></span>

<span data-ttu-id="fcf8e-190">目前的 PowerShell 擴充功能不支援 [PowerShell v3 與 v4][i1310]。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-190">The current PowerShell extension doesn't support [PowerShell v3 and v4][i1310].</span></span> <span data-ttu-id="fcf8e-191">不過，您可以使用支援 PowerShell v3 與 v4 的最新版擴充功能。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-191">However, you can use the last version of the extension that supports PowerShell v3 and v4.</span></span>

> [!CAUTION]
> <span data-ttu-id="fcf8e-192">這個較舊版本的延伸模組不會有額外的修正程式。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-192">There will be no additional fixes to this older version of the extension.</span></span> <span data-ttu-id="fcf8e-193">其是以「現況」提供，但如果您仍在使用 Windows PowerShell v3 與 Windows PowerShell v4，則可以加以使用。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-193">It's provided "AS IS" but is available for you if you are still using Windows PowerShell v3 and Windows PowerShell v4.</span></span>

<span data-ttu-id="fcf8e-194">首先，開啟 [延伸模組] 窗格，然後搜尋 `PowerShell`。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-194">First, open the Extension pane and search for `PowerShell`.</span></span> <span data-ttu-id="fcf8e-195">然後按一下齒輪，並選取 [安裝其他版本]  。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-195">Then click the gear and select **Install another version...**.</span></span>

![安裝其他版本...](media/using-vscode/install-another-version.png)

<span data-ttu-id="fcf8e-197">然後選取 **2020.1.0** 版。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-197">Then select the **2020.1.0** version.</span></span> <span data-ttu-id="fcf8e-198">此版本的延伸模組是支援 v3 與 v4 的最後一個版本。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-198">This version of the extension was the last version to support v3 and v4.</span></span> <span data-ttu-id="fcf8e-199">請務必新增下列設定，讓您的擴充功能版本不會自動更新：</span><span class="sxs-lookup"><span data-stu-id="fcf8e-199">Be sure to add the following setting so that your extension version doesn't update automatically:</span></span>

```json
{
    "extensions.autoUpdate": false
}
```

<span data-ttu-id="fcf8e-200">**2020.1.0** 版在可預見的未來將能繼續運作。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-200">Version **2020.1.0** will work for the foreseeable future.</span></span> <span data-ttu-id="fcf8e-201">不過，Visual Studio Code 可能會實作變更，使此版本的擴充功能中斷。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-201">However, Visual Studio Code could implement a change that breaks this version of the extension.</span></span> <span data-ttu-id="fcf8e-202">基於此原因，且由於支援不足，我們建議：</span><span class="sxs-lookup"><span data-stu-id="fcf8e-202">Because of this, and lack of support, we recommend:</span></span>

- <span data-ttu-id="fcf8e-203">升級至 Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="fcf8e-203">Upgrading to Windows PowerShell 5.1</span></span>
- <span data-ttu-id="fcf8e-204">安裝 PowerShell 7，這是 Windows PowerShell 的並存安裝，而且與 PowerShell 擴充功能搭配使用效果最佳</span><span class="sxs-lookup"><span data-stu-id="fcf8e-204">Install PowerShell 7, which is a side-by-side install to Windows PowerShell and works the best with the PowerShell extension</span></span>

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="fcf8e-205">使用 Visual Studio Code 偵錯</span><span class="sxs-lookup"><span data-stu-id="fcf8e-205">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="fcf8e-206">無工作區偵錯</span><span class="sxs-lookup"><span data-stu-id="fcf8e-206">No-workspace debugging</span></span>

<span data-ttu-id="fcf8e-207">在 Visual Studio Code 1.9 版 (或更新版本) 中，您可以對 PowerShell 指令碼進行偵錯，而無須開啟包含 PowerShell 指令碼的資料夾。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-207">In Visual Studio Code version 1.9 (or higher), you can debug PowerShell scripts without opening the folder that contains the PowerShell script.</span></span>

1. <span data-ttu-id="fcf8e-208">以 [檔案] > [開啟檔案]  開啟 PowerShell 指令碼檔案</span><span class="sxs-lookup"><span data-stu-id="fcf8e-208">Open the PowerShell script file with **File > Open File...**</span></span>
1. <span data-ttu-id="fcf8e-209">設定中斷點 - 選取一行，然後按 <kbd>F9</kbd></span><span class="sxs-lookup"><span data-stu-id="fcf8e-209">Set a breakpoint - select a line then press <kbd>F9</kbd></span></span>
1. <span data-ttu-id="fcf8e-210">按 <kbd>F5</kbd> 開始偵錯</span><span class="sxs-lookup"><span data-stu-id="fcf8e-210">Press <kbd>F5</kbd> to start debugging</span></span>

<span data-ttu-id="fcf8e-211">[偵錯動作] 窗格應該會隨即出現，您可在該窗格中進行偵錯工具、步驟、繼續和停止偵錯。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-211">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume, and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="fcf8e-212">工作區偵錯</span><span class="sxs-lookup"><span data-stu-id="fcf8e-212">Workspace debugging</span></span>

<span data-ttu-id="fcf8e-213">工作區偵錯是指在從 [檔案]  功能表使用 [開啟資料夾]  所開啟的資料夾內容中進行偵錯。您開啟的資料夾通常是 PowerShell 專案資料夾或 Git 存放庫的根目錄。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-213">Workspace debugging refers to debugging in the context of a folder that you've opened from the **File** menu using **Open Folder...**. The folder you open is typically your PowerShell project folder or the root of your Git repository.</span></span> <span data-ttu-id="fcf8e-214">工作區偵錯可讓您定義多個偵錯設定，不只是針對目前開啟的檔案進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-214">Workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>

<span data-ttu-id="fcf8e-215">請遵循這些步驟建立偵錯設定檔：</span><span class="sxs-lookup"><span data-stu-id="fcf8e-215">Follow these steps to create a debug configuration file:</span></span>

1. <span data-ttu-id="fcf8e-216">按下 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd> 以開啟 [偵錯]  檢視。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-216">Open the **Debug** view on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span> <span data-ttu-id="fcf8e-217">若為 macOS，請按下 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-217">On macOS, press <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span>
1. <span data-ttu-id="fcf8e-218">按一下 [建立 launch.json 檔案]  連結。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-218">Click the **create a launch.json file** link.</span></span>
1. <span data-ttu-id="fcf8e-219">從 [選取環境]  提示中，選擇 [PowerShell]  。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-219">From the **Select Environment** prompt, choose **PowerShell**.</span></span>
1. <span data-ttu-id="fcf8e-220">選擇您要使用的偵錯類型：</span><span class="sxs-lookup"><span data-stu-id="fcf8e-220">Choose the type of debugging you'd like to use:</span></span>

   - <span data-ttu-id="fcf8e-221">**啟動目前的檔案** - 在目前作用中的編輯器視窗中啟動檔案及對檔案進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-221">**Launch Current File** - Launch and debug the file in the currently active editor window</span></span>
   - <span data-ttu-id="fcf8e-222">**啟動指令碼** -啟動和偵錯指定的檔案或命令</span><span class="sxs-lookup"><span data-stu-id="fcf8e-222">**Launch Script** - Launch and debug the specified file or command</span></span>
   - <span data-ttu-id="fcf8e-223">**互動式工作階段** - 從整合式主控台執行的偵錯命令</span><span class="sxs-lookup"><span data-stu-id="fcf8e-223">**Interactive Session** - Debug commands executed from the Integrated Console</span></span>
   - <span data-ttu-id="fcf8e-224">**附加** - 將偵錯工具附加至執行中的 PowerShell 主機處理程序</span><span class="sxs-lookup"><span data-stu-id="fcf8e-224">**Attach** - Attach the debugger to a running PowerShell Host Process</span></span>

<span data-ttu-id="fcf8e-225">Visual Studio Code 會在工作區資料夾的根目錄中建立目錄與檔案 `.vscode\launch.json`，以儲存偵錯設定。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-225">Visual Studio Code creates a directory and a file `.vscode\launch.json` in the root of your workspace folder to store the debug configuration.</span></span> <span data-ttu-id="fcf8e-226">如果檔案是在 Git 存放庫中，您通常要修訂 `launch.json` 檔案。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-226">If your files are in a Git repository, you typically want to commit the `launch.json` file.</span></span> <span data-ttu-id="fcf8e-227">`launch.json` 檔案的內容如下：</span><span class="sxs-lookup"><span data-stu-id="fcf8e-227">The contents of the `launch.json` file are:</span></span>

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

<span data-ttu-id="fcf8e-228">此檔案表示常見的偵錯案例。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-228">This file represents the common debug scenarios.</span></span> <span data-ttu-id="fcf8e-229">當在編輯器中開啟這個檔案時，您會看到 [新增設定...]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-229">When you open this file in the editor, you see an **Add Configuration...** button.</span></span> <span data-ttu-id="fcf8e-230">您可以按一下此按鈕來新增多個 PowerShell 偵錯設定。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-230">You can click this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="fcf8e-231">PowerShell: **啟動指令碼**是可以新增的方便設定。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-231">One useful configuration to add is **PowerShell: Launch Script**.</span></span> <span data-ttu-id="fcf8e-232">使用此設定時，您可以指定包含選擇性引數的檔案，無論編輯器中當時作用中的是哪個檔案，只要按下 <kbd>F5</kbd> 就會加以使用。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-232">With this configuration, you can specify a file containing optional arguments that are used whenever you press <kbd>F5</kbd> no matter which file is active in the editor.</span></span>

<span data-ttu-id="fcf8e-233">建立偵錯設定之後，您可以選取在偵錯工作階段期間想要使用的設定。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-233">After the debug configuration is established, you can select which configuration you want to use during a debug session.</span></span> <span data-ttu-id="fcf8e-234">從 [偵錯]  檢視工具列的 [偵錯設定] 下拉式清單中選取設定。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-234">Select a configuration from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

## <a name="troubleshooting-the-powershell-extension-for-visual-studio-code"></a><span data-ttu-id="fcf8e-235">針對適用於 Visual Studio Code 的 PowerShell 延伸模組進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="fcf8e-235">Troubleshooting the PowerShell extension for Visual Studio Code</span></span>

<span data-ttu-id="fcf8e-236">如果您使用 Visual Studio Code 進行 PowerShell 指令碼開發時遇到任何問題，請參閱 GitHub 上的[疑難排解指南][troubleshooting]。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-236">If you experience any issues using Visual Studio Code for PowerShell script development, see the [troubleshooting guide][troubleshooting] on GitHub.</span></span>

## <a name="useful-resources"></a><span data-ttu-id="fcf8e-237">有用的資源</span><span class="sxs-lookup"><span data-stu-id="fcf8e-237">Useful resources</span></span>

<span data-ttu-id="fcf8e-238">有幾個影片和部落格文章可以協助您開始使用適用於 Visual Studio Code 的 PowerShell 延伸模組：</span><span class="sxs-lookup"><span data-stu-id="fcf8e-238">There are a few videos and blog posts that may be helpful to get you started using the PowerShell extension for Visual Studio Code:</span></span>

### <a name="videos"></a><span data-ttu-id="fcf8e-239">影片</span><span class="sxs-lookup"><span data-stu-id="fcf8e-239">Videos</span></span>

- [<span data-ttu-id="fcf8e-240">使用 Visual Studio Code 作為您的預設 PowerShell 編輯器</span><span class="sxs-lookup"><span data-stu-id="fcf8e-240">Using Visual Studio Code as Your Default PowerShell Editor</span></span>](https://youtu.be/bGn45vIeAMM)
- [<span data-ttu-id="fcf8e-241">Visual Studio Code：深入探討針對您的 PowerShell 指令碼進行偵錯</span><span class="sxs-lookup"><span data-stu-id="fcf8e-241">Visual Studio Code: deep dive into debugging your PowerShell scripts</span></span>](https://youtu.be/cSbIXmlkr8o)

### <a name="blog-posts"></a><span data-ttu-id="fcf8e-242">部落格文章</span><span class="sxs-lookup"><span data-stu-id="fcf8e-242">Blog posts</span></span>

- <span data-ttu-id="fcf8e-243">[PowerShell 延伸模組][pscdn]</span><span class="sxs-lookup"><span data-stu-id="fcf8e-243">[PowerShell Extension][pscdn]</span></span>
- <span data-ttu-id="fcf8e-244">[在 Visual Studio Code 中撰寫和偵錯 PowerShell 指令碼][debug]</span><span class="sxs-lookup"><span data-stu-id="fcf8e-244">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="fcf8e-245">[偵錯 Visual Studio Code 指引][psdbgblog]</span><span class="sxs-lookup"><span data-stu-id="fcf8e-245">[Debugging Visual Studio Code Guidance][psdbgblog]</span></span>
- <span data-ttu-id="fcf8e-246">[在 Visual Studio Code 中偵錯 PowerShell][psdbg-gh]</span><span class="sxs-lookup"><span data-stu-id="fcf8e-246">[Debugging PowerShell in Visual Studio Code][psdbg-gh]</span></span>
- <span data-ttu-id="fcf8e-247">[開始使用 Visual Studio Code 中的 PowerShell 開發][getting-started]</span><span class="sxs-lookup"><span data-stu-id="fcf8e-247">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="fcf8e-248">[適用於 PowerShell 開發的 Visual Studio Code 編輯功能 – 第 1 部分][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="fcf8e-248">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="fcf8e-249">[適用於 PowerShell 開發的 Visual Studio Code 編輯功能 – 第 2 部分][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="fcf8e-249">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="fcf8e-250">[在 Visual Studio Code 中偵錯 PowerShell 指令碼 – 第 1 部分][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="fcf8e-250">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="fcf8e-251">[在 Visual Studio Code 中偵錯 PowerShell 指令碼 – 第 2 部分][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="fcf8e-251">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

## <a name="powershell-extension-project-source-code"></a><span data-ttu-id="fcf8e-252">PowerShell 擴充功能專案原始程式碼</span><span class="sxs-lookup"><span data-stu-id="fcf8e-252">PowerShell extension project source code</span></span>

<span data-ttu-id="fcf8e-253">[GitHub][psext-src] 上可以找到 PowerShell 延伸模組的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-253">The PowerShell extension's source code can be found on [GitHub][psext-src].</span></span>

<span data-ttu-id="fcf8e-254">如果您對參與感興趣，非常歡迎您建立提取要求。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-254">If you're interested in contributing, Pull Requests are greatly appreciated.</span></span> <span data-ttu-id="fcf8e-255">請依照 GitHub 上的[開發人員文件][dev-docs]開始使用。</span><span class="sxs-lookup"><span data-stu-id="fcf8e-255">Follow along with the [developer documentation][dev-docs] on GitHub to get started.</span></span>

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
[GitHub issues]:          https://github.com/PowerShell/vscode-powershell/issues
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
