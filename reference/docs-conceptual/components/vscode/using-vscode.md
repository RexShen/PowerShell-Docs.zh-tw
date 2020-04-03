---
title: 使用 Visual Studio Code 開發 PowerShell
description: 使用 Visual Studio Code 開發 PowerShell
ms.date: 11/07/2019
ms.openlocfilehash: 8644aa7c648d649651ca679238e0b79ff35ac579
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500903"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="51196-103">使用 Visual Studio Code 開發 PowerShell</span><span class="sxs-lookup"><span data-stu-id="51196-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="51196-104">[Visual Studio Code](https://code.visualstudio.com/) \(英文\) 是 Microsoft 提供的跨平台 (Windows、macOS 與 Linux) 指令碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="51196-104">[Visual Studio Code](https://code.visualstudio.com/) is a cross-platform (Windows, macOS, and Linux) script editor by Microsoft.</span></span> <span data-ttu-id="51196-105">搭配 [PowerShell 延伸模組](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell) \(英文\)，其提供了豐富的互動式指令碼編輯體驗，讓您更輕鬆地撰寫可靠的 PowerShell 指令碼。</span><span class="sxs-lookup"><span data-stu-id="51196-105">Together with the [the PowerShell extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell), it provides a rich and interactive script editing experience, making it easier to write reliable PowerShell scripts.</span></span>

<span data-ttu-id="51196-106">Visual Studio Code 搭配 PowerShell 延伸模組是撰寫 PowerShell 指令碼的建議編輯器。</span><span class="sxs-lookup"><span data-stu-id="51196-106">Visual Studio Code with the PowerShell extension is the recommended editor for writing PowerShell scripts.</span></span>
<span data-ttu-id="51196-107">其支援下列 PowerShell 版本：</span><span class="sxs-lookup"><span data-stu-id="51196-107">It supports the following PowerShell versions:</span></span>

- <span data-ttu-id="51196-108">PowerShell 7 與更新版本</span><span class="sxs-lookup"><span data-stu-id="51196-108">PowerShell 7 and up</span></span>
- <span data-ttu-id="51196-109">PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="51196-109">PowerShell Core 6</span></span>
- <span data-ttu-id="51196-110">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="51196-110">Windows PowerShell 5.1</span></span>

<span data-ttu-id="51196-111">在開始前，請先確定系統上有 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="51196-111">Before you begin, make sure PowerShell exists on your system.</span></span> <span data-ttu-id="51196-112">如需 Windows、macOS 和 Linux 上的新型工作負載，請參閱下列連結：</span><span class="sxs-lookup"><span data-stu-id="51196-112">For modern workloads on Windows, macOS, and Linux, see the following links:</span></span>

- <span data-ttu-id="51196-113">[在 Linux 上安裝 PowerShell][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="51196-113">[Installing PowerShell on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="51196-114">[在 macOS 上安裝 PowerShell][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="51196-114">[Installing PowerShell on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="51196-115">[在 Windows 上安裝 PowerShell][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="51196-115">[Installing PowerShell on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="51196-116">若為傳統的 Windows PowerShell 工作負載，請參閱[安裝 Windows PowerShell][install-winps]。</span><span class="sxs-lookup"><span data-stu-id="51196-116">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

> [!NOTE]
> <span data-ttu-id="51196-117">Visual Studio Code 與 [Visual Studio](https://visualstudio.microsoft.com/) 不同。</span><span class="sxs-lookup"><span data-stu-id="51196-117">Visual Studio Code is not the same as [Visual Studio](https://visualstudio.microsoft.com/).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="51196-118">Windows 仍然可以使用 [Windows PowerShell ISE][ise]，不過，我們已不再主動開發其功能，而且無法與 PowerShell 7 和更新版本或 PowerShell Core 6 搭配運作。</span><span class="sxs-lookup"><span data-stu-id="51196-118">The [Windows PowerShell ISE][ise] is also still available for Windows, however, it is no longer in active feature development and does not work with PowerShell 7 and up or PowerShell Core 6.</span></span>
> <span data-ttu-id="51196-119">因為此功能屬於 Windows 的出貨元件，所以官方仍會繼續支援其安全性與高優先順序的服務修正。</span><span class="sxs-lookup"><span data-stu-id="51196-119">As a shipping component of Windows, it continues to be officially supported for security and high-priority servicing fixes.</span></span> <span data-ttu-id="51196-120">目前尚無任何計劃要將 ISE 從 Windows 移除。</span><span class="sxs-lookup"><span data-stu-id="51196-120">We currently have no plans to remove the ISE from Windows.</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="51196-121">使用 Visual Studio Code 編輯</span><span class="sxs-lookup"><span data-stu-id="51196-121">Editing with Visual Studio Code</span></span>

1. <span data-ttu-id="51196-122">安裝 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="51196-122">Install Visual Studio Code.</span></span> <span data-ttu-id="51196-123">如需詳細資訊，請參閱 [Setting up Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview) (設定 Visual Studio Code) 概觀。</span><span class="sxs-lookup"><span data-stu-id="51196-123">For more information, see the overview [Setting up Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview).</span></span>

    <span data-ttu-id="51196-124">下列為每個平台的安裝指示：</span><span class="sxs-lookup"><span data-stu-id="51196-124">There are installation instructions for each platform:</span></span>

    - <span data-ttu-id="51196-125">**Windows**：遵循[在 Windows 上執行 Visual Studio Code](https://code.visualstudio.com/docs/setup/windows) \(英文\) 頁面的安裝指示操作。</span><span class="sxs-lookup"><span data-stu-id="51196-125">**Windows**: follow the installation instructions on the [Running Visual Studio Code on Windows](https://code.visualstudio.com/docs/setup/windows) page.</span></span>
    - <span data-ttu-id="51196-126">**macOS**：遵循[在 macOS 上執行 Visual Studio Code](https://code.visualstudio.com/docs/setup/mac) \(英文\) 頁面的安裝指示操作。</span><span class="sxs-lookup"><span data-stu-id="51196-126">**macOS**: follow the installation instructions on the [Running Visual Studio Code on macOS](https://code.visualstudio.com/docs/setup/mac) page.</span></span>
    - <span data-ttu-id="51196-127">**Linux**：遵循[在 Linux 上執行 Visual Studio Code](https://code.visualstudio.com/docs/setup/linux) \(英文\) 頁面的安裝指示操作。</span><span class="sxs-lookup"><span data-stu-id="51196-127">**Linux**: follow the installation instructions on the [Running Visual Studio Code on Linux](https://code.visualstudio.com/docs/setup/linux) page.</span></span>

1. <span data-ttu-id="51196-128">安裝 PowerShell 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="51196-128">Install the PowerShell Extension.</span></span>

   1. <span data-ttu-id="51196-129">如果您已安裝 Visual Studio Code Insiders，請透過在主控台中輸入 `code` 或 `code-insiders` 以啟動 Visual Studio Code 應用程式。</span><span class="sxs-lookup"><span data-stu-id="51196-129">Launch the Visual Studio Code app by typing `code` in a console or `code-insiders` if you installed Visual Studio Code Insiders.</span></span>
   1. <span data-ttu-id="51196-130">按下 <kbd>Ctrl</kbd>+<kbd>P</kbd> 來啟動 Windows 或 Linux 上的 **Quick Open**。</span><span class="sxs-lookup"><span data-stu-id="51196-130">Launch **Quick Open** on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="51196-131">針對 macOS，則按下 <kbd>Cmd</kbd>+<kbd>P</kbd>。</span><span class="sxs-lookup"><span data-stu-id="51196-131">On macOS, press <kbd>Cmd</kbd>+<kbd>P</kbd>.</span></span>
   1. <span data-ttu-id="51196-132">在 Quick Open 中，鍵入 `ext install powershell`，然後按下 [輸入]  。</span><span class="sxs-lookup"><span data-stu-id="51196-132">In Quick Open, type `ext install powershell` and press **Enter**.</span></span>
   1. <span data-ttu-id="51196-133">提要欄位上隨即開啟 [延伸模組]  檢視。</span><span class="sxs-lookup"><span data-stu-id="51196-133">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="51196-134">從 Microsoft 選取 PowerShell 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="51196-134">Select the PowerShell extension from Microsoft.</span></span>
      <span data-ttu-id="51196-135">您應該會看到類似下圖的 Visual Studio Code 畫面：</span><span class="sxs-lookup"><span data-stu-id="51196-135">You should see a Visual Studio Code screen similar to the following image:</span></span>

      ![Visual Studio Code](media/using-vscode/vscode.png)

   1. <span data-ttu-id="51196-137">從 Microsoft 按一下 PowerShell 延伸模組的 [安裝]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="51196-137">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
   1. <span data-ttu-id="51196-138">安裝之後，若您看到 [安裝]  按鈕變成 [重新載入]  ，請按一下 [重新載入]  。</span><span class="sxs-lookup"><span data-stu-id="51196-138">After the install, if you see the **Install** button turn into **Reload**, Click on **Reload**.</span></span>
   1. <span data-ttu-id="51196-139">重新載入 Visual Studio Code 之後，就可以進行編輯。</span><span class="sxs-lookup"><span data-stu-id="51196-139">After Visual Studio Code has reloaded, you're ready for editing.</span></span>

<span data-ttu-id="51196-140">例如，若要建立新的檔案，請按一下 [檔案] > [新增]  。</span><span class="sxs-lookup"><span data-stu-id="51196-140">For example, to create a new file, click **File > New**.</span></span> <span data-ttu-id="51196-141">若要儲存，請按一下 [檔案] > [儲存]  ，然後提供檔案名稱，例如 `HelloWorld.ps1`。</span><span class="sxs-lookup"><span data-stu-id="51196-141">To save it, click **File > Save** and then provide a file name, such as `HelloWorld.ps1`.</span></span> <span data-ttu-id="51196-142">若要關閉檔案，請按一下檔案名稱旁邊的 `X`。</span><span class="sxs-lookup"><span data-stu-id="51196-142">To close the file, click the `X` next to the file name.</span></span> <span data-ttu-id="51196-143">若要結束 Visual Studio Code，請移至 [檔案] > [結束]  。</span><span class="sxs-lookup"><span data-stu-id="51196-143">To exit Visual Studio Code, **File > Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="51196-144">在受限制的系統上安裝 PowerShell 延伸模組</span><span class="sxs-lookup"><span data-stu-id="51196-144">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="51196-145">某些系統已設定為需要檢查所有程式碼簽章，且必須以手動方式核准 PowerShell Editor Services，才能在系統上執行。</span><span class="sxs-lookup"><span data-stu-id="51196-145">Some systems are set up in a way that requires all code signatures to be checked and requires PowerShell Editor Services to be manually approved to run on the system.</span></span> <span data-ttu-id="51196-146">如果已經安裝 PowerShell 延伸模組，但發生下列錯誤，則可能原因是變更執行原則的群組原則更新：</span><span class="sxs-lookup"><span data-stu-id="51196-146">A Group Policy update that changes execution policy is a likely cause if you've installed the PowerShell extension but are receiving an error such as:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="51196-147">若要手動核准 PowerShell Editor Services 與適用於 Visual Studio Code 的 PowerShell 延伸模組，請開啟 PowerShell 提示字元並執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="51196-147">To manually approve PowerShell Editor Services and the PowerShell extension for Visual Studio Code, open a PowerShell prompt and run the following command:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="51196-148">系統會提示您**要執行來自這個不受信任的發行者的軟體嗎？**</span><span class="sxs-lookup"><span data-stu-id="51196-148">You're prompted with **Do you want to run software from this untrusted publisher?**</span></span>
<span data-ttu-id="51196-149">輸入 `A` 以執行檔案。</span><span class="sxs-lookup"><span data-stu-id="51196-149">Type `A` to run the file.</span></span> <span data-ttu-id="51196-150">然後，開啟 Visual Studio Code 並檢查 PowerShell 延伸模組是否正常運作。</span><span class="sxs-lookup"><span data-stu-id="51196-150">Then, open Visual Studio Code and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="51196-151">如果您仍有關於開始使用的問題，請透過 [GitHub](https://github.com/PowerShell/vscode-powershell/issues) \(英文\) 讓我們知道。</span><span class="sxs-lookup"><span data-stu-id="51196-151">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

> [!NOTE]
> <span data-ttu-id="51196-152">適用於 Visual Studio Code 的 PowerShell 延伸模組不支援在限制語言模式中執行。</span><span class="sxs-lookup"><span data-stu-id="51196-152">The PowerShell extension for Visual Studio Code does not support running in constrained language mode.</span></span> <span data-ttu-id="51196-153">如需詳細資訊，請參閱[支援的 GitHub 問題追蹤](https://github.com/PowerShell/vscode-powershell/issues/606) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="51196-153">Please see the [GitHub issue tracking that support](https://github.com/PowerShell/vscode-powershell/issues/606) for more information.</span></span>

### <a name="using-an-older-version-of-the-powershell-extension-for-windows-powershell-v3-and-v4"></a><span data-ttu-id="51196-154">針對 Windows PowerShell v3 與 v4 使用較舊版本的 PowerShell 延伸模組</span><span class="sxs-lookup"><span data-stu-id="51196-154">Using an older version of the PowerShell Extension for Windows PowerShell v3 and v4</span></span>

<span data-ttu-id="51196-155">雖然目前的 PowerShell 延伸模組[已停止支援 v3 與 v4](https://github.com/PowerShell/vscode-powershell/issues/1310) \(英文\)，但是您仍然可以使用該延伸模組的最新版本。</span><span class="sxs-lookup"><span data-stu-id="51196-155">Although the current PowerShell extension [stopped supporting v3 and v4](https://github.com/PowerShell/vscode-powershell/issues/1310), you can still use the last version of the extension that did.</span></span>

> [!NOTE]
> <span data-ttu-id="51196-156">這個較舊版本的延伸模組不會有額外的修正程式。</span><span class="sxs-lookup"><span data-stu-id="51196-156">There will be no additional fixes to this older version of the extension.</span></span> <span data-ttu-id="51196-157">其是以「現況」提供，但如果您仍在使用 Windows PowerShell v3 與 Windows PowerShell v4，則可以加以使用。</span><span class="sxs-lookup"><span data-stu-id="51196-157">It's provided "AS IS" but is available for you if you are still using Windows PowerShell v3 and Windows PowerShell v4.</span></span>

<span data-ttu-id="51196-158">首先，開啟 [延伸模組] 窗格，然後搜尋 `PowerShell`。</span><span class="sxs-lookup"><span data-stu-id="51196-158">First, open the Extension pane and search for `PowerShell`.</span></span> <span data-ttu-id="51196-159">然後按一下齒輪，並選取 [安裝其他版本]  。</span><span class="sxs-lookup"><span data-stu-id="51196-159">Then click the gear and select **Install another version...**.</span></span>

![安裝其他版本...](media/using-vscode/install-another-version.png)

<span data-ttu-id="51196-161">然後選取 `2020.1.0` 版本  。</span><span class="sxs-lookup"><span data-stu-id="51196-161">Then select the **`2020.1.0`** version.</span></span> <span data-ttu-id="51196-162">此版本的延伸模組是支援 v3 與 v4 的最後一個版本。</span><span class="sxs-lookup"><span data-stu-id="51196-162">This version of the extension was the last version to support v3 and v4.</span></span>

<span data-ttu-id="51196-163">此外，新增下列設定，讓您的延伸模組版本不會自動更新：</span><span class="sxs-lookup"><span data-stu-id="51196-163">Also, add the following setting so that your extension version doesn't update automatically:</span></span>

```json
{
    "extensions.autoUpdate": false
}
```

<span data-ttu-id="51196-164">雖然這在可預見的未來將有作用，但是 Visual Studio Code 可能會實作變更，使此版本的延伸模組中斷。</span><span class="sxs-lookup"><span data-stu-id="51196-164">Although this will work in the forseeable future, Visual Studio Code could implement a change that breaks this version of the extension.</span></span>
<span data-ttu-id="51196-165">因此，且由於支援不足，我們強烈建議：</span><span class="sxs-lookup"><span data-stu-id="51196-165">Because of this, and lack of support, we highly recommend either:</span></span>

- <span data-ttu-id="51196-166">下載 PowerShell 7 - 這是 Windows PowerShell 的並存安裝，而且與 PowerShell 延伸模組搭配使用效果最佳</span><span class="sxs-lookup"><span data-stu-id="51196-166">Downloading PowerShell 7 - which is a side-by-side install to Windows PowerShell and works the best with the PowerShell extension</span></span>
- <span data-ttu-id="51196-167">升級至 Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="51196-167">Upgrading to Windows PowerShell 5.1</span></span>

<span data-ttu-id="51196-168">此文章中的[使用 Visual Studio Code 進行編輯](#editing-with-visual-studio-code)一節會連結到安裝這些軟體的位置。</span><span class="sxs-lookup"><span data-stu-id="51196-168">The [Editing with Visual Studio Code](#editing-with-visual-studio-code) section in this article links to where to install these.</span></span>

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="51196-169">選擇要與擴充功能搭配使用的 PowerShell 版本</span><span class="sxs-lookup"><span data-stu-id="51196-169">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="51196-170">透過與 Windows PowerShell 並存安裝的 PowerShell Core，其現在能夠將特定版本的 PowerShell 與 PowerShell 延伸模組搭配使用。</span><span class="sxs-lookup"><span data-stu-id="51196-170">With PowerShell Core installing side-by-side with Windows PowerShell, it's now possible to use a particular version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="51196-171">使用下列步驟來選擇版本：</span><span class="sxs-lookup"><span data-stu-id="51196-171">Use the following steps to choose the version:</span></span>

1. <span data-ttu-id="51196-172">按下 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> 來開啟 Windows 或 Linux 上的 [命令選擇區]  。</span><span class="sxs-lookup"><span data-stu-id="51196-172">Open the **Command Palette** on Windows or Linux with <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="51196-173">若為 macOS，請按下 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>。</span><span class="sxs-lookup"><span data-stu-id="51196-173">On macOS, use <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span>
1. <span data-ttu-id="51196-174">搜尋**工作階段**。</span><span class="sxs-lookup"><span data-stu-id="51196-174">Search for **Session**.</span></span>
1. <span data-ttu-id="51196-175">按一下 [PowerShell:  顯示工作階段功能表]。</span><span class="sxs-lookup"><span data-stu-id="51196-175">Click on **PowerShell: Show Session Menu**.</span></span>
1. <span data-ttu-id="51196-176">從清單中選擇要使用的 PowerShell 版本，例如：**PowerShell Core**。</span><span class="sxs-lookup"><span data-stu-id="51196-176">Choose the version of PowerShell you want to use from the list, for example: **PowerShell Core**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="51196-177">此功能會查看不同作業系統上的一些已知路徑，以探索 PowerShell 的安裝位置。</span><span class="sxs-lookup"><span data-stu-id="51196-177">This feature looks at a few well-known paths on different operating systems to discover install locations of PowerShell.</span></span> <span data-ttu-id="51196-178">如果您已將 PowerShell 安裝到非典型位置，則它一開始可能不會顯示於工作階段功能表中。</span><span class="sxs-lookup"><span data-stu-id="51196-178">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="51196-179">您可以藉由[新增自己的自訂路徑](#adding-your-own-powershell-paths-to-the-session-menu)來擴充工作階段功能表，如下所述。</span><span class="sxs-lookup"><span data-stu-id="51196-179">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

>[!NOTE]
> <span data-ttu-id="51196-180">還有另一種方式可前往工作階段功能表。</span><span class="sxs-lookup"><span data-stu-id="51196-180">There's another way to get to the session menu.</span></span> <span data-ttu-id="51196-181">在您的編輯器中開啟 PowerShell 檔案時，您會在右下角看到綠色的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="51196-181">When a PowerShell file is open in your editor, you see a green version number in the bottom right.</span></span> <span data-ttu-id="51196-182">按一下此版本號碼，即會帶您前往工作階段功能表。</span><span class="sxs-lookup"><span data-stu-id="51196-182">Clicking this version number will bring you to the session menu.</span></span>

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="51196-183">將您自己的 PowerShell 路徑新增至工作階段功能表</span><span class="sxs-lookup"><span data-stu-id="51196-183">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="51196-184">您可以透過 [Visual Studio Code 設定](https://code.visualstudio.com/docs/getstarted/settings) \(英文\)，將其他 PowerShell 可執行檔路徑新增至工作階段功能表：`powershell.powerShellAdditionalExePaths`。</span><span class="sxs-lookup"><span data-stu-id="51196-184">You can add other PowerShell executable paths to the session menu through the [Visual Studio Code setting](https://code.visualstudio.com/docs/getstarted/settings): `powershell.powerShellAdditionalExePaths`.</span></span>

<span data-ttu-id="51196-185">將項目新增至清單 `powershell.powerShellAdditionalExePaths` 或建立清單 (如果它不存在您的 `settings.json` 中)：</span><span class="sxs-lookup"><span data-stu-id="51196-185">Add an item to the list `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

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

<span data-ttu-id="51196-186">每個項目都必須具備：</span><span class="sxs-lookup"><span data-stu-id="51196-186">Each item must have:</span></span>

- <span data-ttu-id="51196-187">`exePath`:`pwsh` 或 `powershell` 可執行檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="51196-187">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
- <span data-ttu-id="51196-188">`versionName`:將顯示於工作階段功能表中的文字。</span><span class="sxs-lookup"><span data-stu-id="51196-188">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="51196-189">您可以將此文字設定為要顯示於工作階段功能表 (也稱為最後一個設定中的 `versionName`) 中的文字，藉以使用 `powershell.powerShellDefaultVersion` 設定來設定要使用的預設 PowerShell 版本：</span><span class="sxs-lookup"><span data-stu-id="51196-189">You can set the default PowerShell version to use the `powershell.powerShellDefaultVersion` setting by setting this to the text displayed in the session menu (also known as the `versionName` in the last setting):</span></span>

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

<span data-ttu-id="51196-190">當完成此設定之後，請重新啟動 Visual Studio Code，或從 命令選擇區  重新載入目前的 Visual Studio Code 視窗，並輸入 **Developer:** 重新載入視窗。</span><span class="sxs-lookup"><span data-stu-id="51196-190">After you've configured this setting, restart Visual Studio Code or to reload the current Visual Studio Code window from the **Command Palette**, type **Developer: Reload Window**.</span></span>

<span data-ttu-id="51196-191">如果您開啟工作階段功能表，現在將會看到您其他的 PowerShell 版本！</span><span class="sxs-lookup"><span data-stu-id="51196-191">If you open the session menu, you now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="51196-192">如果您從來源建置 PowerShell，則這是最適合用來測試 PowerShell 本機組建的方式。</span><span class="sxs-lookup"><span data-stu-id="51196-192">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="51196-193">Visual Studio Code 的組態設定</span><span class="sxs-lookup"><span data-stu-id="51196-193">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="51196-194">首先，如果您不熟悉如何在 Visual Studio Code 中變更設定，建議您查看 [Visual Studio Code 的設定文件](https://code.visualstudio.com/docs/getstarted/settings) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="51196-194">First, if you're not familiar with how to change settings in Visual Studio Code, we recommend looking at [Visual Studio Code's settings documentation](https://code.visualstudio.com/docs/getstarted/settings).</span></span>

<span data-ttu-id="51196-195">使用先前段落中的步驟，您可以在 `settings.json` 中新增組態設定。</span><span class="sxs-lookup"><span data-stu-id="51196-195">By using the steps in the previous paragraph, you can add configuration settings in `settings.json`.</span></span>

```json
{
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="51196-196">如果您不希望這些設定影響所有檔案類型，Visual Studio Code 也允許個別語言設定。</span><span class="sxs-lookup"><span data-stu-id="51196-196">If you don't want these settings to affect all files types, Visual Studio Code also allows per-language configurations.</span></span> <span data-ttu-id="51196-197">將設定放入 `[<language-name>]` 欄位，建立語言特定設定。</span><span class="sxs-lookup"><span data-stu-id="51196-197">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="51196-198">例如：</span><span class="sxs-lookup"><span data-stu-id="51196-198">For example:</span></span>

```json
{
    "[powershell]": {
        "files.encoding": "utf8bom",
        "files.autoGuessEncoding": true
    }
}
```

> [!TIP]
> <span data-ttu-id="51196-199">如需有關 Visual Studio Code 中檔案編碼的詳細資訊，請參閱[了解檔案編碼](understanding-file-encoding.md)。</span><span class="sxs-lookup"><span data-stu-id="51196-199">For more information about file encoding in Visual Studio Code, see [Understanding file encoding](understanding-file-encoding.md).</span></span>
>
> <span data-ttu-id="51196-200">另請參閱[如何在 Visual Studio Code 中複寫 ISE 體驗](How-To-Replicate-the-ISE-Experience-In-VSCode.md)，以取得有關如何設定 Visual Studio Code 以進行 PowerShell 編輯的其他祕訣。</span><span class="sxs-lookup"><span data-stu-id="51196-200">Also check out the [How to replicate the ISE experience in Visual Studio Code](How-To-Replicate-the-ISE-Experience-In-VSCode.md) for other tips on how to configure Visual Studio Code for PowerShell editing.</span></span>

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="51196-201">使用 Visual Studio Code 偵錯</span><span class="sxs-lookup"><span data-stu-id="51196-201">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="51196-202">無工作區偵錯</span><span class="sxs-lookup"><span data-stu-id="51196-202">No-workspace debugging</span></span>

<span data-ttu-id="51196-203">從 Visual Studio Code 1.9 版起，您可以對 PowerShell 指令碼進行偵錯，而無須開啟包含 PowerShell 指令碼的資料夾。</span><span class="sxs-lookup"><span data-stu-id="51196-203">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without opening the folder that contains the PowerShell script.</span></span> <span data-ttu-id="51196-204">以 [檔案] > [開啟檔案...]  開啟 PowerShell 指令碼檔案，在行上設定中斷點，依序按下 <kbd>F9</kbd> 和 <kbd>F5</kbd> 來開始偵錯。</span><span class="sxs-lookup"><span data-stu-id="51196-204">Open the PowerShell script file with **File > Open File...**, set a breakpoint on a line, press <kbd>F9</kbd>, and then press <kbd>F5</kbd> to start debugging.</span></span> <span data-ttu-id="51196-205">[偵錯動作] 窗格應該會隨即出現，您可在該窗格中進行偵錯工具、步驟、繼續和停止偵錯。</span><span class="sxs-lookup"><span data-stu-id="51196-205">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume, and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="51196-206">工作區偵錯</span><span class="sxs-lookup"><span data-stu-id="51196-206">Workspace debugging</span></span>

<span data-ttu-id="51196-207">工作區偵錯是指使用 [開啟資料夾...]  來在 [檔案]  功能表的 Visual Studio Code 中對已開啟的資料夾內容進行偵錯。您開啟的資料夾通常是 PowerShell 專案資料夾及/或 Git 存放庫的根目錄。</span><span class="sxs-lookup"><span data-stu-id="51196-207">Workspace debugging refers to debugging in the context of a folder that you've opened in Visual Studio Code from the **File** menu using **Open Folder...**. The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="51196-208">即使在此模式中，只要按下 <kbd>F5</kbd> 就可以開始針對目前選取的 PowerShell 指令碼進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="51196-208">Even in this mode, you can start debugging the currently selected PowerShell script by pressing <kbd>F5</kbd>.</span></span> <span data-ttu-id="51196-209">不過，工作區偵錯可讓您定義多個偵錯設定，不只是偵錯目前開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="51196-209">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span> <span data-ttu-id="51196-210">稍後我們將深入介紹。</span><span class="sxs-lookup"><span data-stu-id="51196-210">We'll get to those in a moment.</span></span>

<span data-ttu-id="51196-211">請遵循下列步驟建立您的偵錯設定檔：</span><span class="sxs-lookup"><span data-stu-id="51196-211">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="51196-212">按下 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd> 以開啟 [偵錯]  檢視。</span><span class="sxs-lookup"><span data-stu-id="51196-212">Open the **Debug** view on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span> <span data-ttu-id="51196-213">若為 macOS，請按下 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>。</span><span class="sxs-lookup"><span data-stu-id="51196-213">On macOS, press <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span>
  1. <span data-ttu-id="51196-214">按一下 [建立 launch.json 檔案] 連結。</span><span class="sxs-lookup"><span data-stu-id="51196-214">Click the "create a launch.json file" link.</span></span>
  1. <span data-ttu-id="51196-215">Visual Studio Code 會提示您 [選取環境]  。</span><span class="sxs-lookup"><span data-stu-id="51196-215">Visual Studio Code prompts you to **Select Environment**.</span></span> <span data-ttu-id="51196-216">選擇 [PowerShell]  。</span><span class="sxs-lookup"><span data-stu-id="51196-216">Choose **PowerShell**.</span></span>
  1. <span data-ttu-id="51196-217">最後，選擇您要使用的偵錯類型：</span><span class="sxs-lookup"><span data-stu-id="51196-217">Lastly, choose the type of debugging you'd like to use:</span></span>

- <span data-ttu-id="51196-218">**啟動目前的檔案** - 在目前作用中的編輯器視窗中啟動檔案及對檔案進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="51196-218">**Launch Current File** - Launch and debug the file in the currently active editor window</span></span>
- <span data-ttu-id="51196-219">**啟動指令碼** -啟動和偵錯指定的檔案或命令</span><span class="sxs-lookup"><span data-stu-id="51196-219">**Launch Script** - Launch and debug the specified file or command</span></span>
- <span data-ttu-id="51196-220">**互動式工作階段** - 從整合式主控台執行的偵錯命令</span><span class="sxs-lookup"><span data-stu-id="51196-220">**Interactive Session** - Debug commands executed from the Integrated Console</span></span>
- <span data-ttu-id="51196-221">**附加** - 將偵錯工具附加至執行中的 PowerShell 主機處理程序</span><span class="sxs-lookup"><span data-stu-id="51196-221">**Attach** - Attach the debugger to a running PowerShell Host Process</span></span>

<span data-ttu-id="51196-222">接著 Visual Studio Code 會在工作區資料夾的根目錄中建立目錄與檔案 `.vscode\launch.json`。</span><span class="sxs-lookup"><span data-stu-id="51196-222">The result is that Visual Studio Code creates a directory and a file `.vscode\launch.json` in the root of your workspace folder.</span></span> <span data-ttu-id="51196-223">該位置為儲存偵錯設定的位置。</span><span class="sxs-lookup"><span data-stu-id="51196-223">This location is where your debug configuration is stored.</span></span> <span data-ttu-id="51196-224">如果檔案是在 Git 存放庫中，您通常要修訂 `launch.json` 檔案。</span><span class="sxs-lookup"><span data-stu-id="51196-224">If your files are in a Git repository, you typically want to commit the `launch.json` file.</span></span> <span data-ttu-id="51196-225">`launch.json` 檔案的內容如下：</span><span class="sxs-lookup"><span data-stu-id="51196-225">The contents of the `launch.json` file are:</span></span>

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

<span data-ttu-id="51196-226">此檔案表示常見的偵錯案例。</span><span class="sxs-lookup"><span data-stu-id="51196-226">This file represents the common debug scenarios.</span></span> <span data-ttu-id="51196-227">當在編輯器中開啟這個檔案時，您會看到 [新增設定...]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="51196-227">When you open this file in the editor, you see an **Add Configuration...** button.</span></span> <span data-ttu-id="51196-228">您可以按一下此按鈕來新增多個 PowerShell 偵錯設定。</span><span class="sxs-lookup"><span data-stu-id="51196-228">You can click this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="51196-229">PowerShell: **啟動指令碼**是可以新增的方便設定。</span><span class="sxs-lookup"><span data-stu-id="51196-229">One useful configuration to add is **PowerShell: Launch Script**.</span></span> <span data-ttu-id="51196-230">使用此設定時，您可以指定有選擇性引數的檔案，無論編輯器中當時作用中的是哪個檔案，只要按下 <kbd>F5</kbd> 應該就會啟動。</span><span class="sxs-lookup"><span data-stu-id="51196-230">With this configuration, you can specify a file with optional arguments that should be launched whenever you press <kbd>F5</kbd> no matter which file is currently active in the editor.</span></span>

<span data-ttu-id="51196-231">建立偵錯設定之後，您可以選取在偵錯工作階段期間想要使用的設定。</span><span class="sxs-lookup"><span data-stu-id="51196-231">After the debug configuration is established, you can select which configuration you want to use during a debug session.</span></span> <span data-ttu-id="51196-232">從 [偵錯]  檢視工具列的 [偵錯設定] 下拉式清單中選取設定。</span><span class="sxs-lookup"><span data-stu-id="51196-232">Select a configuration from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

## <a name="useful-resources"></a><span data-ttu-id="51196-233">有用的資源</span><span class="sxs-lookup"><span data-stu-id="51196-233">Useful resources</span></span>

<span data-ttu-id="51196-234">有幾個影片和部落格文章可以協助您開始使用適用於 Visual Studio Code 的 PowerShell 延伸模組：</span><span class="sxs-lookup"><span data-stu-id="51196-234">There are a few videos and blog posts that may be helpful to get you started using the PowerShell extension for Visual Studio Code:</span></span>

### <a name="videos"></a><span data-ttu-id="51196-235">影片</span><span class="sxs-lookup"><span data-stu-id="51196-235">Videos</span></span>

- [<span data-ttu-id="51196-236">使用 Visual Studio Code 作為您的預設 PowerShell 編輯器</span><span class="sxs-lookup"><span data-stu-id="51196-236">Using Visual Studio Code as Your Default PowerShell Editor</span></span>](https://youtu.be/bGn45vIeAMM)
- [<span data-ttu-id="51196-237">Visual Studio Code：深入探討針對您的 PowerShell 指令碼進行偵錯</span><span class="sxs-lookup"><span data-stu-id="51196-237">Visual Studio Code: deep dive into debugging your PowerShell scripts</span></span>](https://youtu.be/cSbIXmlkr8o)

### <a name="blog-posts"></a><span data-ttu-id="51196-238">部落格文章</span><span class="sxs-lookup"><span data-stu-id="51196-238">Blog posts</span></span>

- <span data-ttu-id="51196-239">[PowerShell 延伸模組][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="51196-239">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="51196-240">[在 Visual Studio Code 中撰寫和偵錯 PowerShell 指令碼][debug]</span><span class="sxs-lookup"><span data-stu-id="51196-240">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="51196-241">[偵錯 Visual Studio Code 指引][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="51196-241">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="51196-242">[在 Visual Studio Code 中偵錯 PowerShell][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="51196-242">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="51196-243">[開始使用 Visual Studio Code 中的 PowerShell 開發][getting-started]</span><span class="sxs-lookup"><span data-stu-id="51196-243">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="51196-244">[適用於 PowerShell 開發的 Visual Studio Code 編輯功能 – 第 1 部分][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="51196-244">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="51196-245">[適用於 PowerShell 開發的 Visual Studio Code 編輯功能 – 第 2 部分][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="51196-245">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="51196-246">[在 Visual Studio Code 中偵錯 PowerShell 指令碼 – 第 1 部分][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="51196-246">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="51196-247">[在 Visual Studio Code 中偵錯 PowerShell 指令碼 – 第 2 部分][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="51196-247">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="51196-248">適用於 Visual Studio Code 的 PowerShell 延伸模組</span><span class="sxs-lookup"><span data-stu-id="51196-248">PowerShell extension for Visual Studio Code</span></span>

<span data-ttu-id="51196-249">[GitHub](https://github.com/PowerShell/vscode-powershell) 上可以找到 PowerShell 延伸模組的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="51196-249">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>

<span data-ttu-id="51196-250">如果您對參與感興趣，非常歡迎您建立提取要求。</span><span class="sxs-lookup"><span data-stu-id="51196-250">If you're interested in contributing, Pull Request are greatly appreciated.</span></span> <span data-ttu-id="51196-251">請依照 [GitHub 上的開發人員文件](https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md) \(英文\) 開始使用。</span><span class="sxs-lookup"><span data-stu-id="51196-251">Follow along with the [developer documentation on GitHub](https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md) to get started.</span></span>

## <a name="troubleshooting-the-powershell-extension-for-visual-studio-code"></a><span data-ttu-id="51196-252">針對適用於 Visual Studio Code 的 PowerShell 延伸模組進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="51196-252">Troubleshooting the PowerShell extension for Visual Studio Code</span></span>

<span data-ttu-id="51196-253">如果您使用 Visual Studio Code 進行 PowerShell 指令碼開發時遇到任何問題，請參閱 [GitHub 上的疑難排解指南](https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="51196-253">If you experience any issues using Visual Studio Code for PowerShell script development, please take a look at the [troubleshooting guide on GitHub](https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md)</span></span>

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
