# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="8c99d-101">使用 Visual Studio Code 開發 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8c99d-101">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="8c99d-102">除了 [PowerShell ISE][ise] 之外，PowerShell 在 Visual Studio Code 中也受到良好支援。</span><span class="sxs-lookup"><span data-stu-id="8c99d-102">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="8c99d-103">而且，雖然所有平台 (Windows、macOS 和 Linux) 上的 PowerShell Core 都支援 Visual Studio Code，但 PowerShell Core 不支援 ISE</span><span class="sxs-lookup"><span data-stu-id="8c99d-103">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="8c99d-104">使用 Windows 10 或安裝適用於低階 Windows 作業系統 (例如 Windows 8.1 等) 的 [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395)，即可以在 Windows 上使用 Visual Studio Code 與 PowerShell 第 5 版。</span><span class="sxs-lookup"><span data-stu-id="8c99d-104">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="8c99d-105">啟動它之前，請先確定系統上有 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="8c99d-105">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="8c99d-106">若為 Windows、macOS 和 Linux 上的新型工作負載，請參閱：</span><span class="sxs-lookup"><span data-stu-id="8c99d-106">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="8c99d-107">[在 Linux 上安裝 PowerShell Core][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="8c99d-107">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="8c99d-108">[在 macOS 上安裝 PowerShell Core][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="8c99d-108">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="8c99d-109">[在 Windows 上安裝 PowerShell Core][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="8c99d-109">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="8c99d-110">若為傳統的 Windows PowerShell 工作負載，請參閱[安裝 Windows PowerShell][install-winps]。</span><span class="sxs-lookup"><span data-stu-id="8c99d-110">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="8c99d-111">使用 Visual Studio Code 編輯</span><span class="sxs-lookup"><span data-stu-id="8c99d-111">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="8c99d-112">1.安裝 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="8c99d-112">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="8c99d-113">**Linux**：遵循 [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) (在 Linux 上執行 VS Code) 頁面的安裝指示操作</span><span class="sxs-lookup"><span data-stu-id="8c99d-113">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="8c99d-114">**macOS**：遵循 [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) (在 macOS 上執行 VS Code) 頁面的安裝指示操作</span><span class="sxs-lookup"><span data-stu-id="8c99d-114">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="8c99d-115">在 macOS 上，您必須安裝 OpenSSL，PowerShell 延伸模組才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="8c99d-115">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
  > <span data-ttu-id="8c99d-116">完成這項作業最簡單的方式是安裝 [Homebrew](http://brew.sh/) ，然後執行 `brew install openssl`。</span><span class="sxs-lookup"><span data-stu-id="8c99d-116">The easiest way to accomplish this is to install [Homebrew](http://brew.sh/) and then run `brew install openssl`.</span></span>
  > <span data-ttu-id="8c99d-117">現在，VS Code 可以成功載入 PowerShell 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="8c99d-117">VS Code can now load the the PowerShell extension successfully.</span></span>

- <span data-ttu-id="8c99d-118">**Windows**：遵循 [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) (在 Windows 上執行 VS Code) 頁面的安裝指示操作</span><span class="sxs-lookup"><span data-stu-id="8c99d-118">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="8c99d-119">2.安裝 PowerShell 延伸模組</span><span class="sxs-lookup"><span data-stu-id="8c99d-119">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="8c99d-120">啟動 Visual Studio Code 應用程式：</span><span class="sxs-lookup"><span data-stu-id="8c99d-120">Launch the Visual Studio Code app by:</span></span>
  - <span data-ttu-id="8c99d-121">**Windows**：在您的 PowerShell 工作階段鍵入 `code`</span><span class="sxs-lookup"><span data-stu-id="8c99d-121">**Windows**: typing `code` in your PowerShell session</span></span>
  - <span data-ttu-id="8c99d-122">**Linux**：在您的終端機上鍵入 `code`</span><span class="sxs-lookup"><span data-stu-id="8c99d-122">**Linux**: typing `code` in your terminal</span></span>
  - <span data-ttu-id="8c99d-123">**macOS**：在您的終端機上鍵入 `code`</span><span class="sxs-lookup"><span data-stu-id="8c99d-123">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="8c99d-124">按 **Ctrl+P** (Mac 是 **Cmd+P**) 啟動 [快速開啟]。</span><span class="sxs-lookup"><span data-stu-id="8c99d-124">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="8c99d-125">在 [快速開啟] 中鍵入 `ext install powershell` 並點擊 **Enter**。</span><span class="sxs-lookup"><span data-stu-id="8c99d-125">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="8c99d-126">提要欄位上隨即開啟 [延伸模組] 檢視。</span><span class="sxs-lookup"><span data-stu-id="8c99d-126">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="8c99d-127">從 Microsoft 選取 PowerShell 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="8c99d-127">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="8c99d-128">您應該會看到類似如下的畫面︰</span><span class="sxs-lookup"><span data-stu-id="8c99d-128">You should see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="8c99d-130">從 Microsoft 按一下 PowerShell 延伸模組的 [安裝] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="8c99d-130">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="8c99d-131">安裝之後，您會看到 [安裝] 按鈕變成 [重新載入]。</span><span class="sxs-lookup"><span data-stu-id="8c99d-131">After the install, you see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="8c99d-132">按一下 [重新載入]。</span><span class="sxs-lookup"><span data-stu-id="8c99d-132">Click on **Reload**.</span></span>
- <span data-ttu-id="8c99d-133">重新載入 Visual Studio Code 之後，就可以進行編輯。</span><span class="sxs-lookup"><span data-stu-id="8c99d-133">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="8c99d-134">例如，若要建立新的檔案，按一下 [檔案]->[新增]。</span><span class="sxs-lookup"><span data-stu-id="8c99d-134">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="8c99d-135">若要儲存它，按一下 [檔案]->[儲存]，然後提供檔案名稱，例如 `HelloWorld.ps1`。</span><span class="sxs-lookup"><span data-stu-id="8c99d-135">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="8c99d-136">若要關閉檔案，請按一下檔案名稱旁邊的 "x"。</span><span class="sxs-lookup"><span data-stu-id="8c99d-136">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="8c99d-137">若要結束 Visual Studio Code，[檔案]->[結束]。</span><span class="sxs-lookup"><span data-stu-id="8c99d-137">To exit Visual Studio Code, **File->Exit**.</span></span>

#### <a name="using-a-specific-installed-version-of-powershell"></a><span data-ttu-id="8c99d-138">使用 PowerShell 的特定安裝版本</span><span class="sxs-lookup"><span data-stu-id="8c99d-138">Using a specific installed version of PowerShell</span></span>

<span data-ttu-id="8c99d-139">如果您想要搭配使用特定安裝的 PowerShell 與 Visual Studio Code，則必須在使用者設定檔中新增變數。</span><span class="sxs-lookup"><span data-stu-id="8c99d-139">If you wish to use a specific installation of PowerShell with Visual Studio Code, you need to add a new variable to your user settings file.</span></span>

1. <span data-ttu-id="8c99d-140">按一下 [檔案]-> [喜好設定]-> [設定]</span><span class="sxs-lookup"><span data-stu-id="8c99d-140">Click **File -> Preferences -> Settings**</span></span>
2. <span data-ttu-id="8c99d-141">隨即出現兩個編輯器窗格。</span><span class="sxs-lookup"><span data-stu-id="8c99d-141">Two editor panes appear.</span></span>
   <span data-ttu-id="8c99d-142">在最右邊的窗格中 (`settings.json`)，在兩個大括弧中間 (`{`和`}`) 插入下列適用於您作業系統的設定，使用已安裝的 PowerShell 版本取代 *<version>*：</span><span class="sxs-lookup"><span data-stu-id="8c99d-142">In the right-most pane (`settings.json`), insert the setting below appropriate for your OS somewhere between the two curly brackets (`{` and `}`) and replace *<version>* with the installed PowerShell version:</span></span>

   ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
   ```

3. <span data-ttu-id="8c99d-143">以所需 PowerShell 可執行檔的路徑取代設定</span><span class="sxs-lookup"><span data-stu-id="8c99d-143">Replace the setting with the path to the desired PowerShell executable</span></span>
4. <span data-ttu-id="8c99d-144">儲存設定檔並重新啟動 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="8c99d-144">Save the settings file and restart Visual Studio Code</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="8c99d-145">Visual Studio Code 的組態設定</span><span class="sxs-lookup"><span data-stu-id="8c99d-145">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="8c99d-146">使用先前段落中的步驟，您可以在 `settings.json` 中新增組態設定。</span><span class="sxs-lookup"><span data-stu-id="8c99d-146">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="8c99d-147">我們建議下列 Visual Studio Code 組態設定：</span><span class="sxs-lookup"><span data-stu-id="8c99d-147">We recommend the following configuration settings for Visual Studio Code:</span></span>

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true
}
```

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="8c99d-148">使用 Visual Studio Code 偵錯</span><span class="sxs-lookup"><span data-stu-id="8c99d-148">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="8c99d-149">無工作區偵錯</span><span class="sxs-lookup"><span data-stu-id="8c99d-149">No-workspace debugging</span></span>

<span data-ttu-id="8c99d-150">使用 Visual Studio Code 1.9 版可以偵錯 PowerShell 指令碼，不必開啟包含 PowerShell 指令碼的資料夾。</span><span class="sxs-lookup"><span data-stu-id="8c99d-150">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span>
<span data-ttu-id="8c99d-151">只要以 [檔案]->[開啟檔案...] 開啟 PowerShell 指令碼檔案，在行中設定中斷點 (按 F9)，然後按 F5 啟動偵錯。</span><span class="sxs-lookup"><span data-stu-id="8c99d-151">Simply open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span>
<span data-ttu-id="8c99d-152">您會看到 [偵錯動作] 窗格出現，其可讓您中斷偵錯工具、中斷步驟、繼續和停止偵錯。</span><span class="sxs-lookup"><span data-stu-id="8c99d-152">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="8c99d-153">工作區偵錯</span><span class="sxs-lookup"><span data-stu-id="8c99d-153">Workspace debugging</span></span>

<span data-ttu-id="8c99d-154">工作區偵錯是指使用 [檔案] 功能表的 [開啟資料夾...]，在 Visual Studio Code 已開啟的資料夾內容中偵錯。</span><span class="sxs-lookup"><span data-stu-id="8c99d-154">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="8c99d-155">您開啟的資料夾通常是 PowerShell 專案資料夾及/或 Git 存放庫的根目錄。</span><span class="sxs-lookup"><span data-stu-id="8c99d-155">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="8c99d-156">即使在此模式中，只要按下 F5 就可以開始偵錯目前選取的 PowerShell 指令碼。</span><span class="sxs-lookup"><span data-stu-id="8c99d-156">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="8c99d-157">不過，工作區偵錯可讓您定義多個偵錯設定，不只是偵錯目前開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="8c99d-157">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="8c99d-158">例如，您可以新增設定以：</span><span class="sxs-lookup"><span data-stu-id="8c99d-158">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="8c99d-159">啟動偵錯工具中的 Pester 測試</span><span class="sxs-lookup"><span data-stu-id="8c99d-159">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="8c99d-160">以偵錯工具中的引數啟動特定檔案</span><span class="sxs-lookup"><span data-stu-id="8c99d-160">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="8c99d-161">啟動偵錯工具中的互動式工作階段</span><span class="sxs-lookup"><span data-stu-id="8c99d-161">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="8c99d-162">將偵錯工具附加至 PowerShell 主機處理程序</span><span class="sxs-lookup"><span data-stu-id="8c99d-162">Attach the debugger to a PowerShell host process</span></span>

  <span data-ttu-id="8c99d-163">請遵循下列步驟建立您的偵錯設定檔：</span><span class="sxs-lookup"><span data-stu-id="8c99d-163">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="8c99d-164">按 **Ctrl+Shift+D** (Mac 是 **Cmd+Shift+D**) 開啟 [偵錯] 檢視。</span><span class="sxs-lookup"><span data-stu-id="8c99d-164">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
  2. <span data-ttu-id="8c99d-165">按工具列中的**設定**齒輪圖示。</span><span class="sxs-lookup"><span data-stu-id="8c99d-165">Press the **Configure** gear icon in the toolbar.</span></span>
  3. <span data-ttu-id="8c99d-166">Visual Studio Code 會提示您 [選取環境]。</span><span class="sxs-lookup"><span data-stu-id="8c99d-166">Visual Studio Code prompts you to **Select Environment**.</span></span>
  <span data-ttu-id="8c99d-167">選擇 [PowerShell]。</span><span class="sxs-lookup"><span data-stu-id="8c99d-167">Choose **PowerShell**.</span></span>

  <span data-ttu-id="8c99d-168">當您這樣做時，Visual Studio Code 會在工作區資料夾的根目錄中建立目錄和檔案：".vscode\launch.json"。</span><span class="sxs-lookup"><span data-stu-id="8c99d-168">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
  <span data-ttu-id="8c99d-169">這是儲存偵錯設定的位置。</span><span class="sxs-lookup"><span data-stu-id="8c99d-169">This is where your debug configuration is stored.</span></span> <span data-ttu-id="8c99d-170">如果檔案是在 Git 存放庫中，您通常要修訂 launch.json 檔案。</span><span class="sxs-lookup"><span data-stu-id="8c99d-170">If your files are in a Git repository, you typically want to commit the launch.json file.</span></span>
  <span data-ttu-id="8c99d-171">Launch.json 檔案的內容如下：</span><span class="sxs-lookup"><span data-stu-id="8c99d-171">The contents of the launch.json file are:</span></span>

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

  <span data-ttu-id="8c99d-172">這表示常見的偵錯案例。</span><span class="sxs-lookup"><span data-stu-id="8c99d-172">This represents the common debug scenarios.</span></span>
  <span data-ttu-id="8c99d-173">不過，當您在編輯器中開啟這個檔案時，您會看到 [新增設定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="8c99d-173">However, when you open this file in the editor, you see an **Add Configuration...** button.</span></span>
  <span data-ttu-id="8c99d-174">您可以按此按鈕新增多個 PowerShell 偵錯設定。</span><span class="sxs-lookup"><span data-stu-id="8c99d-174">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="8c99d-175">**PowerShell：啟動指令碼**是可以新增的方便設定。</span><span class="sxs-lookup"><span data-stu-id="8c99d-175">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
  <span data-ttu-id="8c99d-176">使用此設定時，您可以指定有選擇性引數的特定檔案，只要按下 F5 就應該啟動，無論編輯器中當時作用的是哪個檔案。</span><span class="sxs-lookup"><span data-stu-id="8c99d-176">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

  <span data-ttu-id="8c99d-177">建立偵錯設定之後，您就可以從 [偵錯] 檢視工具列的偵錯設定下拉式清單中擇一，選取在偵錯工作階段期間想要使用的設定。</span><span class="sxs-lookup"><span data-stu-id="8c99d-177">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

  <span data-ttu-id="8c99d-178">有幾個部落格可以協助您開始使用適用於 Visual Studio Code 的 PowerShell 延伸模組</span><span class="sxs-lookup"><span data-stu-id="8c99d-178">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code</span></span>

<span data-ttu-id="8c99d-179">Visual Studio Code：</span><span class="sxs-lookup"><span data-stu-id="8c99d-179">Visual Studio Code:</span></span>

- <span data-ttu-id="8c99d-180">[PowerShell 延伸模組][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="8c99d-180">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="8c99d-181">[在 Visual Studio Code 中撰寫和偵錯 PowerShell 指令碼][debug]</span><span class="sxs-lookup"><span data-stu-id="8c99d-181">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="8c99d-182">[偵錯 Visual Studio Code 指引][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="8c99d-182">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="8c99d-183">[在 Visual Studio Code 中偵錯 PowerShell][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="8c99d-183">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="8c99d-184">[開始使用 Visual Studio Code 中的 PowerShell 開發][getting-started]</span><span class="sxs-lookup"><span data-stu-id="8c99d-184">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="8c99d-185">[適用於 PowerShell 開發的 Visual Studio Code 編輯功能 – 第 1 部分][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="8c99d-185">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="8c99d-186">[適用於 PowerShell 開發的 Visual Studio Code 編輯功能 – 第 2 部分][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="8c99d-186">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="8c99d-187">[在 Visual Studio Code 中偵錯 PowerShell 指令碼 – 第 1 部分][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="8c99d-187">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="8c99d-188">[在 Visual Studio Code 中偵錯 PowerShell 指令碼 – 第 2 部分][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="8c99d-188">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise-guide.md
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

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="8c99d-189">適用於 Visual Studio Code 的 PowerShell 延伸模組</span><span class="sxs-lookup"><span data-stu-id="8c99d-189">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="8c99d-190">[GitHub](https://github.com/PowerShell/vscode-powershell) 上可以找到 PowerShell 延伸模組的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="8c99d-190">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>