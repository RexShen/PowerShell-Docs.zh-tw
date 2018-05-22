---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: 4b006d2ac812abf1f281b6b4e382c2760f92a95c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2018
---
# <a name="known-issues-and-limitations"></a><span data-ttu-id="7a813-102">已知的問題和限制</span><span class="sxs-lookup"><span data-stu-id="7a813-102">Known Issues and Limitations</span></span>

<a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a><span data-ttu-id="7a813-103">第一次使用時，會無法使用 PowerShell 快速鍵</span><span class="sxs-lookup"><span data-stu-id="7a813-103">PowerShell Shortcuts are broken when used for the first time</span></span>
------------------------------------------------------------

<span data-ttu-id="7a813-104">**解決方法︰** 執行下列其中一項動作︰</span><span class="sxs-lookup"><span data-stu-id="7a813-104">**Resolution:** Perform one of the following actions:</span></span>

1.  <span data-ttu-id="7a813-105">以滑鼠右鍵按一下 [PowerShell] 捷徑。</span><span class="sxs-lookup"><span data-stu-id="7a813-105">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="7a813-106">選取 [Windows PowerShell]，在非提高權限模式下啟動。</span><span class="sxs-lookup"><span data-stu-id="7a813-106">Select “Windows PowerShell” to launch in a non-elevated mode.</span></span>
2.  <span data-ttu-id="7a813-107">以滑鼠右鍵按一下 [PowerShell] 捷徑。</span><span class="sxs-lookup"><span data-stu-id="7a813-107">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="7a813-108">在 [Windows PowerShell] 上按一下滑鼠右鍵，然後選取 [以系統管理員身分執行]，在提升權限的模式中啟動。</span><span class="sxs-lookup"><span data-stu-id="7a813-108">Right click on “Windows PowerShell” and select “Run As Administrator” to launch in an elevated mode.</span></span>

<span data-ttu-id="7a813-109">一旦您已經執行上述動作，PowerShell 快速鍵將可以使用。</span><span class="sxs-lookup"><span data-stu-id="7a813-109">Once you have performed either of the above actions, the PowerShell shortcuts will work.</span></span> <span data-ttu-id="7a813-110">這些動作只需要執行一次。</span><span class="sxs-lookup"><span data-stu-id="7a813-110">These actions need to be performed only once.</span></span>


<a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a><span data-ttu-id="7a813-111">在 Windows 7 上 ExecutionPolicy 相關的 PowerShell 模組和 DSC 資源報告錯誤</span><span class="sxs-lookup"><span data-stu-id="7a813-111">PowerShell Modules and DSC Resources report errors about ExecutionPolicy on Windows 7</span></span>
-------------------------------------------------------------------------------------
<span data-ttu-id="7a813-112">在 Windows 7 上，使用 PowerShell 模組和 DSC 資源可能會報告 ExecutionPolicy 的相關錯誤。</span><span class="sxs-lookup"><span data-stu-id="7a813-112">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

<span data-ttu-id="7a813-113">**解決方法︰** 在提升權限的 PowerShell 工作階段 (以系統管理員身分執行) 中執行下列命令，將 ExecutionPolicy 設定為 RemoteSigned：</span><span class="sxs-lookup"><span data-stu-id="7a813-113">**Resolution:** Set the ExecutionPolicy to RemoteSigned by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

<a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a><span data-ttu-id="7a813-114">連接到舊的遠端 Exchange 端點造成當機</span><span class="sxs-lookup"><span data-stu-id="7a813-114">Connecting to an old remote Exchange endpoint causes a crash</span></span>
------------------------------------------------------------

<span data-ttu-id="7a813-115">舊的 Exchange 端點會重新導向至新的端點。</span><span class="sxs-lookup"><span data-stu-id="7a813-115">The old Exchange endpoint redirects to a new endpoint.</span></span> <span data-ttu-id="7a813-116">重新導向邏輯中的 Bug 會導致當機。</span><span class="sxs-lookup"><span data-stu-id="7a813-116">There is a bug in the redirection logic that results in a crash.</span></span>

<span data-ttu-id="7a813-117">**解決方法︰** 直接連線到新的端點。</span><span class="sxs-lookup"><span data-stu-id="7a813-117">**Resolution:** Connect directly to the new endpoint.</span></span>


<a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a><span data-ttu-id="7a813-118">在 Windows Server 2012 R2 上安裝 WMF 5.0 之後，錯誤地停止軟體清查記錄功能</span><span class="sxs-lookup"><span data-stu-id="7a813-118">Software Inventory Logging feature is erroneously stopped after WMF 5.0 installation on Windows Server 2012 R2</span></span>
-------------------------------------------------------------------------------------------------------------

<span data-ttu-id="7a813-119">在已執行 SIL 的 Windows Server 2012 R2 上安裝 WMF 5.0 時，軟體清查記錄功能在安裝後錯誤地停止。</span><span class="sxs-lookup"><span data-stu-id="7a813-119">When installing WMF 5.0 on a Windows Server 2012 R2 that is already running SIL, the Software Inventory Logging feature is erroneously stopped after installation.</span></span>

<span data-ttu-id="7a813-120">**解決方法︰** 一安裝 WMF 之後，執行 Start-SilLogging Cmdlet，因為安裝程序將會錯誤地停止軟體清查記錄功能。</span><span class="sxs-lookup"><span data-stu-id="7a813-120">**Resolution:** Run the Start-SilLogging cmdlet once after the WMF installation, as the installation process will errantly stop the Software Inventory Logging feature.</span></span>

<a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a><span data-ttu-id="7a813-121">如果同時使用 -LiteralPath 和 -Recurse 則 Get-ChildItem 無法運作</span><span class="sxs-lookup"><span data-stu-id="7a813-121">Get-ChildItem does not work if -LiteralPath and -Recurse are used together</span></span>
--------------------------------------------------------------------------

<span data-ttu-id="7a813-122">如果目錄名稱包含無效的萬用字元，在同時使用 -LiteralPath 和 -Recurse 時，Get-ChildItem 不會產生預期的結果。</span><span class="sxs-lookup"><span data-stu-id="7a813-122">If a directory name contains an invalid wildcard character, then Get-ChildItem will not produce expected results when both -LiteralPath and -Recurse are used together.</span></span>

<span data-ttu-id="7a813-123">**解決方法︰** 不理想，但目前的因應措施是在指令碼中實作遞迴，而不要依賴此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7a813-123">**Resolution:** Not ideal, but current workaround is to implement recursion in the script rather than rely on the cmdlet.</span></span>


<a name="sysprep-fails-after-wmf-50-installation"></a><span data-ttu-id="7a813-124">Sysprep 在安裝 WMF 5.0 之後失敗</span><span class="sxs-lookup"><span data-stu-id="7a813-124">Sysprep fails after WMF 5.0 installation</span></span>
----------------------------------------

<span data-ttu-id="7a813-125">根據您目前執行的 Windows Server 版本而定，有兩種因應措施可解決此問題。</span><span class="sxs-lookup"><span data-stu-id="7a813-125">There are two workarounds for this issue depending on the version of Windows Server you are running.</span></span>

<span data-ttu-id="7a813-126">**解決方法：**</span><span class="sxs-lookup"><span data-stu-id="7a813-126">**Resolution:**</span></span>
- <span data-ttu-id="7a813-127">針對執行 **Windows Server 2008 R2** 的系統</span><span class="sxs-lookup"><span data-stu-id="7a813-127">For systems running **Windows Server 2008 R2**</span></span>
  1. <span data-ttu-id="7a813-128">以系統管理員身分開啟 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7a813-128">Open Powershell as an administrator</span></span>
  2. <span data-ttu-id="7a813-129">執行下列命令</span><span class="sxs-lookup"><span data-stu-id="7a813-129">Run the following command</span></span>

  ```powershell
    Set-SilLogging –TargetUri https://BlankTarget –CertificateThumbprint 0123456789
  ```
  3. <span data-ttu-id="7a813-130">執行命令並忽略錯誤 (因為它們如預期般發生)。</span><span class="sxs-lookup"><span data-stu-id="7a813-130">Run the command and ignore the error, as they are expected.</span></span>

  ```powershell
    Publish-SilData
   ```
  4. <span data-ttu-id="7a813-131">刪除 \Windows\System32\Logfiles\SIL\ 目錄中的檔案</span><span class="sxs-lookup"><span data-stu-id="7a813-131">Delete the files in  \Windows\System32\Logfiles\SIL\ directory</span></span>

  ```powershell
    Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
  ```
  5. <span data-ttu-id="7a813-132">安裝所有可用的重要 Windows 更新，然後就能正常開始進行 Sysyprep 操作。</span><span class="sxs-lookup"><span data-stu-id="7a813-132">Install all available important Windows Updates, and begin Sysyprep operation normally.</span></span>

- <span data-ttu-id="7a813-133">針對執行 **Windows Server 2012** 的系統</span><span class="sxs-lookup"><span data-stu-id="7a813-133">For systems running **Windows Server 2012**</span></span>
  1.    <span data-ttu-id="7a813-134">在伺服器上安裝 WMF 5.0，使其成為 Sysprep 之後，以系統管理員身分登入。</span><span class="sxs-lookup"><span data-stu-id="7a813-134">After installing WMF 5.0 on the server to be Sysprep’d, login as administrator.</span></span>
  2.    <span data-ttu-id="7a813-135">將 Generize.xml 從目錄 \Windows\System32\Sysprep\ActionFiles\ 複製到 Windows 目錄之外的位置，例如 C:\。</span><span class="sxs-lookup"><span data-stu-id="7a813-135">Copy Generize.xml from directory \Windows\System32\Sysprep\ActionFiles\ to a location outside of the Windows directory, C:\ for example.</span></span>
  3.    <span data-ttu-id="7a813-136">使用「記事本」開啟 Generalize.xml 複本。</span><span class="sxs-lookup"><span data-stu-id="7a813-136">Open your Generalize.xml copy with notepad.</span></span>
  4.    <span data-ttu-id="7a813-137">找出並移除下列文字，每一個都有一個執行個體需要刪除 (它們將位於文件結尾附近)。</span><span class="sxs-lookup"><span data-stu-id="7a813-137">Find and remove the following text, one instance of each needs to be deleted (they will be near the end of the document).</span></span>

    ```
    <sysprepOrder order="0x3200"></sysprepOrder>
    <sysprepOrder order="0x3300"></sysprepOrder>
    ```

  5.    <span data-ttu-id="7a813-138">儲存編輯過的 Generalize.xml 複本並關閉檔案。</span><span class="sxs-lookup"><span data-stu-id="7a813-138">Save the edited copy of Generalize.xml and close the file.</span></span>
  6.    <span data-ttu-id="7a813-139">以系統管理員身分開啟命令提示字元</span><span class="sxs-lookup"><span data-stu-id="7a813-139">Open a command prompt as administrator</span></span>
  7.    <span data-ttu-id="7a813-140">執行下列命令，以取得 system32 資料夾中 Generalize.xml 檔案的擁有權︰</span><span class="sxs-lookup"><span data-stu-id="7a813-140">Run the following command to take ownership of the Generalize.xml file in system32 folder:</span></span>

    ```
    Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
    ```

  8.    <span data-ttu-id="7a813-141">執行下列命令，在檔案中設定適當的權限︰</span><span class="sxs-lookup"><span data-stu-id="7a813-141">Run the following command to set appropriate permission on the file:</span></span>

    ```
    Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
    ```
      * <span data-ttu-id="7a813-142">在提示字元中回答 [是]，以進行確認。</span><span class="sxs-lookup"><span data-stu-id="7a813-142">Answer Yes at the prompt for confirmation.</span></span>
      * <span data-ttu-id="7a813-143">請注意，您只能使用電腦上系統管理員的使用者名稱來取代 `<AdministratorUserName>`。</span><span class="sxs-lookup"><span data-stu-id="7a813-143">Note that `<AdministratorUserName>` should be replaced by the username who is administrator on the machine.</span></span> <span data-ttu-id="7a813-144">例如，"Administrator"。</span><span class="sxs-lookup"><span data-stu-id="7a813-144">For example, "Administrator".</span></span>

  9.    <span data-ttu-id="7a813-145">使用下列命令，複製您編輯過的檔案，並儲存到 Sysprep 目錄︰</span><span class="sxs-lookup"><span data-stu-id="7a813-145">Copy the file you edited and saved over to the Sysprep directory using the following command:</span></span>

    ```
    xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
    ```
      * <span data-ttu-id="7a813-146">回答 [是] 以進行覆寫 (注意，如果沒有提示要進行覆寫，請再次檢查所輸入的路徑)。</span><span class="sxs-lookup"><span data-stu-id="7a813-146">Answer Yes to overwrite (note that if there is no prompt to overwrite, double check the path entered).</span></span>
      * <span data-ttu-id="7a813-147">假設已將您編輯過的 Generalize.xml 複本複製到 C:\。</span><span class="sxs-lookup"><span data-stu-id="7a813-147">Assumes your edited copy of Generalize.xml was copied to C:\ .</span></span>

  10.   <span data-ttu-id="7a813-148">現在已使用因應措施來更新 Generalize.xml。</span><span class="sxs-lookup"><span data-stu-id="7a813-148">Generalize.xml is now updated with the workaround.</span></span> <span data-ttu-id="7a813-149">請搭配已啟用的一般化選項來執行 Sysprep。</span><span class="sxs-lookup"><span data-stu-id="7a813-149">Please run Sysprep with the generalize option enabled.</span></span>
