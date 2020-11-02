---
ms.date: 06/12/2017
title: WMF 5.0 中的已知問題
description: WMF 5.0 中的已知問題
ms.openlocfilehash: 3f8dcf0f7aab27ff9d3c3a17377959988844a430
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663361"
---
# <a name="known-issues-in-wmf-50"></a><span data-ttu-id="46391-103">WMF 5.0 中的已知問題</span><span class="sxs-lookup"><span data-stu-id="46391-103">Known Issues in WMF 5.0</span></span>

## <a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a><span data-ttu-id="46391-104">第一次使用時，會無法使用 PowerShell 快速鍵</span><span class="sxs-lookup"><span data-stu-id="46391-104">PowerShell Shortcuts are broken when used for the first time</span></span>

<span data-ttu-id="46391-105">**解決方案：** 執行下列動作之一：</span><span class="sxs-lookup"><span data-stu-id="46391-105">**Resolution:** Perform one of the following actions:</span></span>

1. <span data-ttu-id="46391-106">以滑鼠右鍵按一下 [PowerShell] 捷徑。</span><span class="sxs-lookup"><span data-stu-id="46391-106">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="46391-107">選取 [Windows PowerShell] 以在未提高權限的模式中啟動。</span><span class="sxs-lookup"><span data-stu-id="46391-107">Select "Windows PowerShell" to launch in a non-elevated mode.</span></span>
2. <span data-ttu-id="46391-108">以滑鼠右鍵按一下 [PowerShell] 捷徑。</span><span class="sxs-lookup"><span data-stu-id="46391-108">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="46391-109">以滑鼠右鍵按一下 [Windows PowerShell]，然後選取 [以系統管理員身分執行] 以在提高權限的模式中啟動。</span><span class="sxs-lookup"><span data-stu-id="46391-109">Right click on "Windows PowerShell" and select "Run As Administrator" to launch in an elevated mode.</span></span>

<span data-ttu-id="46391-110">一旦您已經執行上述動作，PowerShell 快速鍵將可以使用。</span><span class="sxs-lookup"><span data-stu-id="46391-110">Once you have performed either of the above actions, the PowerShell shortcuts will work.</span></span> <span data-ttu-id="46391-111">這些動作只需要執行一次。</span><span class="sxs-lookup"><span data-stu-id="46391-111">These actions need to be performed only once.</span></span>

## <a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a><span data-ttu-id="46391-112">在 Windows 7 上 ExecutionPolicy 相關的 PowerShell 模組和 DSC 資源報告錯誤</span><span class="sxs-lookup"><span data-stu-id="46391-112">PowerShell Modules and DSC Resources report errors about ExecutionPolicy on Windows 7</span></span>

<span data-ttu-id="46391-113">在 Windows 7 上，使用 PowerShell 模組和 DSC 資源可能導致報告有關 ExecutionPolicy 的錯誤。</span><span class="sxs-lookup"><span data-stu-id="46391-113">On Windows 7, using PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

<span data-ttu-id="46391-114">**解決方案：** 在提高權限的 PowerShell 工作階段 (以系統管理員身分執行) 中執行下列命令，藉以將 ExecutionPolicy 設定為 **RemoteSigned** ：</span><span class="sxs-lookup"><span data-stu-id="46391-114">**Resolution:** Set the ExecutionPolicy to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

## <a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a><span data-ttu-id="46391-115">連接到舊的遠端 Exchange 端點造成當機</span><span class="sxs-lookup"><span data-stu-id="46391-115">Connecting to an old remote Exchange endpoint causes a crash</span></span>

<span data-ttu-id="46391-116">舊的 Exchange 端點會重新導向至新的端點。</span><span class="sxs-lookup"><span data-stu-id="46391-116">The old Exchange endpoint redirects to a new endpoint.</span></span> <span data-ttu-id="46391-117">重新導向邏輯中的 Bug 會導致當機。</span><span class="sxs-lookup"><span data-stu-id="46391-117">There is a bug in the redirection logic that results in a crash.</span></span>

<span data-ttu-id="46391-118">**解決方案：** 直接連線到新的端點。</span><span class="sxs-lookup"><span data-stu-id="46391-118">**Resolution:** Connect directly to the new endpoint.</span></span>

## <a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a><span data-ttu-id="46391-119">在 Windows Server 2012 R2 上安裝 WMF 5.0 之後，錯誤地停止軟體清查記錄功能</span><span class="sxs-lookup"><span data-stu-id="46391-119">Software Inventory Logging feature is erroneously stopped after WMF 5.0 installation on Windows Server 2012 R2</span></span>

<span data-ttu-id="46391-120">在已執行 SIL 的 Windows Server 2012 R2 上安裝 WMF 5.0 時，軟體清查記錄功能在安裝後錯誤地停止。</span><span class="sxs-lookup"><span data-stu-id="46391-120">When installing WMF 5.0 on a Windows Server 2012 R2 that is already running SIL, the Software Inventory Logging feature is erroneously stopped after installation.</span></span>

<span data-ttu-id="46391-121">**解決方案：** 安裝 WMF 之後立即執行 `Start-SilLogging` Cmdlet，因為安裝程序將會不當停止軟體清查記錄功能。</span><span class="sxs-lookup"><span data-stu-id="46391-121">**Resolution:** Run the `Start-SilLogging` cmdlet once after the WMF installation, as the installation process will errantly stop the Software Inventory Logging feature.</span></span>

## <a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a><span data-ttu-id="46391-122">如果同時使用 -LiteralPath 和 -Recurse，`Get-ChildItem` 就無法運作</span><span class="sxs-lookup"><span data-stu-id="46391-122">`Get-ChildItem` does not work if -LiteralPath and -Recurse are used together</span></span>

<span data-ttu-id="46391-123">如果目錄名稱包含無效的萬用字元，則在同時使用 -LiteralPath 和 -Recurse 時，`Get-ChildItem` 將不會產生預期的結果。</span><span class="sxs-lookup"><span data-stu-id="46391-123">If a directory name contains an invalid wildcard character, then `Get-ChildItem` will not produce expected results when both -LiteralPath and -Recurse are used together.</span></span>

<span data-ttu-id="46391-124">**解決方案：** 不理想，但目前的因應措施是在指令碼中實作遞迴，不是依賴此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="46391-124">**Resolution:** Not ideal, but current workaround is to implement recursion in the script rather than rely on the cmdlet.</span></span>

## <a name="sysprep-fails-after-wmf-50-installation"></a><span data-ttu-id="46391-125">Sysprep 在安裝 WMF 5.0 之後失敗</span><span class="sxs-lookup"><span data-stu-id="46391-125">Sysprep fails after WMF 5.0 installation</span></span>

<span data-ttu-id="46391-126">根據您目前執行的 Windows Server 版本而定，有兩種因應措施可解決此問題。</span><span class="sxs-lookup"><span data-stu-id="46391-126">There are two workarounds for this issue depending on the version of Windows Server you are running.</span></span>

<span data-ttu-id="46391-127">**解決方案：**</span><span class="sxs-lookup"><span data-stu-id="46391-127">**Resolution:**</span></span>

- <span data-ttu-id="46391-128">針對執行 **Windows Server 2008 R2** 的系統</span><span class="sxs-lookup"><span data-stu-id="46391-128">For systems running **Windows Server 2008 R2**</span></span>
  1. <span data-ttu-id="46391-129">以系統管理員身分開啟 PowerShell</span><span class="sxs-lookup"><span data-stu-id="46391-129">Open PowerShell as an administrator</span></span>
  2. <span data-ttu-id="46391-130">執行下列命令</span><span class="sxs-lookup"><span data-stu-id="46391-130">Run the following command</span></span>

     ```powershell
     Set-SilLogging -TargetUri https://BlankTarget -CertificateThumbprint 0123456789
     ```

  3. <span data-ttu-id="46391-131">執行命令並忽略錯誤 (因為它們如預期般發生)。</span><span class="sxs-lookup"><span data-stu-id="46391-131">Run the command and ignore the error, as they are expected.</span></span>

     ```powershell
     Publish-SilData
     ```

  4. <span data-ttu-id="46391-132">刪除 \Windows\System32\Logfiles\SIL\ 目錄中的檔案</span><span class="sxs-lookup"><span data-stu-id="46391-132">Delete the files in  \Windows\System32\Logfiles\SIL\ directory</span></span>

     ```powershell
     Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
     ```

  5. <span data-ttu-id="46391-133">安裝所有可用的重要 Windows 更新，然後就能正常開始進行 Sysyprep 操作。</span><span class="sxs-lookup"><span data-stu-id="46391-133">Install all available important Windows Updates, and begin Sysyprep operation normally.</span></span>

- <span data-ttu-id="46391-134">針對執行 **Windows Server 2012** 的系統</span><span class="sxs-lookup"><span data-stu-id="46391-134">For systems running **Windows Server 2012**</span></span>
  1. <span data-ttu-id="46391-135">在伺服器上安裝 WMF 5.0，並使其成為 Sysprep 之後，以系統管理員身分登入。</span><span class="sxs-lookup"><span data-stu-id="46391-135">After installing WMF 5.0 on the server to be Sysprep'd, login as administrator.</span></span>
  2. <span data-ttu-id="46391-136">將 Generize.xml 從目錄 `\Windows\System32\Sysprep\ActionFiles\` 複製到 Windows 目錄之外的位置，例如 `C:\`。</span><span class="sxs-lookup"><span data-stu-id="46391-136">Copy Generize.xml from directory `\Windows\System32\Sysprep\ActionFiles\` to a location outside of the Windows directory, `C:\` for example.</span></span>
  3. <span data-ttu-id="46391-137">使用「記事本」開啟 Generalize.xml 複本。</span><span class="sxs-lookup"><span data-stu-id="46391-137">Open your Generalize.xml copy with notepad.</span></span>
  4. <span data-ttu-id="46391-138">找出並移除下列文字，每一個都有一個執行個體需要刪除 (它們將位於文件結尾附近)。</span><span class="sxs-lookup"><span data-stu-id="46391-138">Find and remove the following text, one instance of each needs to be deleted (they will be near the end of the document).</span></span>

     ```xml
     <sysprepOrder order="0x3200"></sysprepOrder>
     <sysprepOrder order="0x3300"></sysprepOrder>
     ```

  5. <span data-ttu-id="46391-139">儲存編輯過的 Generalize.xml 複本並關閉檔案。</span><span class="sxs-lookup"><span data-stu-id="46391-139">Save the edited copy of Generalize.xml and close the file.</span></span>
  6. <span data-ttu-id="46391-140">以系統管理員身分開啟命令提示字元</span><span class="sxs-lookup"><span data-stu-id="46391-140">Open a command prompt as administrator</span></span>
  7. <span data-ttu-id="46391-141">執行下列命令，以取得 system32 資料夾中 Generalize.xml 檔案的擁有權︰</span><span class="sxs-lookup"><span data-stu-id="46391-141">Run the following command to take ownership of the Generalize.xml file in system32 folder:</span></span>

     ```powershell
     Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

  8. <span data-ttu-id="46391-142">執行下列命令，在檔案中設定適當的權限︰</span><span class="sxs-lookup"><span data-stu-id="46391-142">Run the following command to set appropriate permission on the file:</span></span>

     ```powershell
     Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
     ```

     - <span data-ttu-id="46391-143">在提示字元中回答 [是]，以進行確認。</span><span class="sxs-lookup"><span data-stu-id="46391-143">Answer Yes at the prompt for confirmation.</span></span>
     - <span data-ttu-id="46391-144">請注意，您只能使用電腦上系統管理員的使用者名稱來取代 `<AdministratorUserName>`。</span><span class="sxs-lookup"><span data-stu-id="46391-144">Note that `<AdministratorUserName>` should be replaced by the username who is administrator on the machine.</span></span> <span data-ttu-id="46391-145">例如，"Administrator"。</span><span class="sxs-lookup"><span data-stu-id="46391-145">For example, "Administrator".</span></span>

  9. <span data-ttu-id="46391-146">使用下列命令，複製您編輯過的檔案，並儲存到 Sysprep 目錄︰</span><span class="sxs-lookup"><span data-stu-id="46391-146">Copy the file you edited and saved over to the Sysprep directory using the following command:</span></span>

     ```powershell
     xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

     - <span data-ttu-id="46391-147">回答 [是] 以進行覆寫 (注意，如果沒有提示要進行覆寫，請再次檢查所輸入的路徑)。</span><span class="sxs-lookup"><span data-stu-id="46391-147">Answer Yes to overwrite (note that if there is no prompt to overwrite, double check the path entered).</span></span>
     - <span data-ttu-id="46391-148">假設已將您編輯過的 Generalize.xml 複本複製到 C:\。</span><span class="sxs-lookup"><span data-stu-id="46391-148">Assumes your edited copy of Generalize.xml was copied to C:\ .</span></span>

  10. <span data-ttu-id="46391-149">現在已使用因應措施來更新 Generalize.xml。</span><span class="sxs-lookup"><span data-stu-id="46391-149">Generalize.xml is now updated with the workaround.</span></span> <span data-ttu-id="46391-150">請搭配已啟用的一般化選項來執行 Sysprep。</span><span class="sxs-lookup"><span data-stu-id="46391-150">Please run Sysprep with the generalize option enabled.</span></span>
