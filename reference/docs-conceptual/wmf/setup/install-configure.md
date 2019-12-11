---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,設定
contributor: keithb
title: 安裝與設定 WMF 5.1
ms.openlocfilehash: 241f52be011e1afc87d25c9a934db0c1e0361b76
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "71147688"
---
# <a name="install-and-configure-wmf-51"></a><span data-ttu-id="03788-103">安裝與設定 WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="03788-103">Install and Configure WMF 5.1</span></span>

> [!IMPORTANT]
> <span data-ttu-id="03788-104">WMF 5.1 已取代 WMF 5.0。</span><span class="sxs-lookup"><span data-stu-id="03788-104">WMF 5.0 is superseded by WMF 5.1.</span></span> <span data-ttu-id="03788-105">使用 WMF 5.0 的使用者必須升級至 WMF 5.1 才能獲得支援。</span><span class="sxs-lookup"><span data-stu-id="03788-105">Users with WMF 5.0 must upgrade to WMF 5.1 to receive support.</span></span>
> <span data-ttu-id="03788-106">**WMF 5.1 需要 .NET Framework 4.5.2** (或更新版本)。</span><span class="sxs-lookup"><span data-stu-id="03788-106">**WMF 5.1 requires the .NET Framework 4.5.2** (or above).</span></span> <span data-ttu-id="03788-107">雖然安裝會成功，但若未安裝 .NET 4.5.2 (或更新版本)，主要功能將會失敗。</span><span class="sxs-lookup"><span data-stu-id="03788-107">Installation will succeed, but key features will fail if .NET 4.5.2 (or above) is not installed.</span></span>

## <a name="download-and-install-the-wmf-51-package"></a><span data-ttu-id="03788-108">下載並安裝 WMF 5.1 套件</span><span class="sxs-lookup"><span data-stu-id="03788-108">Download and install the WMF 5.1 package</span></span>

<span data-ttu-id="03788-109">為適用於其安裝所在的作業系統和架構下載 WMF 5.1 封裝︰</span><span class="sxs-lookup"><span data-stu-id="03788-109">Download the WMF 5.1 package for the operating system and architecture you wish to install it on:</span></span>

| <span data-ttu-id="03788-110">作業系統</span><span class="sxs-lookup"><span data-stu-id="03788-110">Operating System</span></span>       | <span data-ttu-id="03788-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="03788-111">Prerequisites</span></span>           | <span data-ttu-id="03788-112">封裝連結</span><span class="sxs-lookup"><span data-stu-id="03788-112">Package Links</span></span>                          |
|------------------------|-------------------------|----------------------------------------|
| <span data-ttu-id="03788-113">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="03788-113">Windows Server 2012 R2</span></span> |                         | <span data-ttu-id="03788-114">[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="03788-114">[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span></span> |
| <span data-ttu-id="03788-115">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="03788-115">Windows Server 2012</span></span>    |                         | <span data-ttu-id="03788-116">[W2K12-KB3191565-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="03788-116">[W2K12-KB3191565-x64.msu][]</span></span>            |
| <span data-ttu-id="03788-117">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="03788-117">Windows Server 2008 R2</span></span> | <span data-ttu-id="03788-118">[.NET Framework 4.5.2][]</span><span class="sxs-lookup"><span data-stu-id="03788-118">[.NET Framework 4.5.2][]</span></span>| <span data-ttu-id="03788-119">[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="03788-119">[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span></span>    |
| <span data-ttu-id="03788-120">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="03788-120">Windows 8.1</span></span>            |                         | <span data-ttu-id="03788-121">**x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="03788-121">**x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</span></span></br><span data-ttu-id="03788-122">**x86:** [Win8.1-KB3191564-x86.msu][]</span><span class="sxs-lookup"><span data-stu-id="03788-122">**x86:** [Win8.1-KB3191564-x86.msu][]</span></span> |
| <span data-ttu-id="03788-123">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="03788-123">Windows 7 SP1</span></span>          | <span data-ttu-id="03788-124">[.NET Framework 4.5.2][]</span><span class="sxs-lookup"><span data-stu-id="03788-124">[.NET Framework 4.5.2][]</span></span>| <span data-ttu-id="03788-125">**x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="03788-125">**x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</span></span></br><span data-ttu-id="03788-126">**x86:** [Win7-KB3191566-x86.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="03788-126">**x86:** [Win7-KB3191566-x86.ZIP][]</span></span> |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

- <span data-ttu-id="03788-133">安裝 WMF 5.1 RTM 之前，必須先解除安裝 WMF 5.1 Preview。</span><span class="sxs-lookup"><span data-stu-id="03788-133">WMF 5.1 Preview must be uninstalled before installing WMF 5.1 RTM.</span></span>
- <span data-ttu-id="03788-134">WMF 5.1 可直接透過 WMF 5.0 或 WMF 4.0 安裝。</span><span class="sxs-lookup"><span data-stu-id="03788-134">WMF 5.1 may be installed directly over WMF 5.0 or WMF 4.0.</span></span>
- <span data-ttu-id="03788-135">在 Windows 7 和 Windows Server 2008 R2 上安裝 WMF 5.1 之前，**不需要**先安裝 WMF 4.0。</span><span class="sxs-lookup"><span data-stu-id="03788-135">It is **not required** to install WMF 4.0 prior to installing WMF 5.1 on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a><span data-ttu-id="03788-136">安裝適用於 Windows Server 2008 R2 和 Windows 7 的 WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="03788-136">Install WMF 5.1 for Windows Server 2008 R2 and Windows 7</span></span>

> [!NOTE]
> <span data-ttu-id="03788-137">Windows Server 2008 R2 和 Windows 7 的安裝指示已變更，且與其他套件的指示不同。</span><span class="sxs-lookup"><span data-stu-id="03788-137">Installation instructions for Windows Server 2008 R2 and Windows 7 have changed, and differ from the instructions for the other packages.</span></span> <span data-ttu-id="03788-138">適用於 Windows Server 2012 R2、Windows Server 2012 和 Windows 8.1 的安裝指示如下。</span><span class="sxs-lookup"><span data-stu-id="03788-138">Installation instructions for Windows Server 2012 R2, Windows Server 2012, and Windows 8.1 are below.</span></span>

### <a name="wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1"></a><span data-ttu-id="03788-139">Windows Server 2008 R2 SP1 和 Windows 7 SP1 的 WMF 5.1 必要條件</span><span class="sxs-lookup"><span data-stu-id="03788-139">WMF 5.1 Prerequisites for Windows Server 2008 R2 SP1 and Windows 7 SP1</span></span>

<span data-ttu-id="03788-140">在 Windows Server 2008 R2 SP1 或 Windows 7 SP1 上安裝 WMF 5.1 需要下列各項：</span><span class="sxs-lookup"><span data-stu-id="03788-140">Installation of WMF 5.1 on either Windows Server 2008 R2 SP1 or Windows 7 SP1, requires the following:</span></span>

- <span data-ttu-id="03788-141">必須安裝最新的 Service Pack。</span><span class="sxs-lookup"><span data-stu-id="03788-141">Latest service pack must be installed.</span></span>
- <span data-ttu-id="03788-142">「不可以」  安裝 WMF 3.0。</span><span class="sxs-lookup"><span data-stu-id="03788-142">WMF 3.0 **must not** be installed.</span></span> <span data-ttu-id="03788-143">在具有 WMF 3.0 的情況下安裝 WMF 5.1 會導致 **PSModulePath** (`$env:PSModulePath`) 遺失，這可能造成其他應用程式失敗。</span><span class="sxs-lookup"><span data-stu-id="03788-143">Installing WMF 5.1 over WMF 3.0 will result in the loss of the **PSModulePath** (`$env:PSModulePath`), which can cause other applications to fail.</span></span> <span data-ttu-id="03788-144">在安裝 WMF 5.1 之前，您必須解除安裝 WMF 3.0，或是儲存 **PSModulePath**，並在完成 WMF 5.1 安裝之後手動將其還原。</span><span class="sxs-lookup"><span data-stu-id="03788-144">Before installing WMF 5.1, you must either un-install WMF 3.0, or save the **PSModulePath** and then restore it manually after WMF 5.1 installation is complete.</span></span>
- <span data-ttu-id="03788-145">WMF 5.1 需要至少[.NET Framework 4.5.2](https://www.microsoft.com/download/details.aspx?id=42642)。</span><span class="sxs-lookup"><span data-stu-id="03788-145">WMF 5.1 requires at least [.NET Framework 4.5.2](https://www.microsoft.com/download/details.aspx?id=42642).</span></span>
  <span data-ttu-id="03788-146">您可以遵循下載位置的指示來安裝 Microsoft.NET Framework 4.5.2。</span><span class="sxs-lookup"><span data-stu-id="03788-146">You can install Microsoft .NET Framework 4.5.2 by following the instructions at the download location.</span></span>

### <a name="installing-wmf-51-on-windows-server-2008-r2-and-windows-7"></a><span data-ttu-id="03788-147">在 Windows Server 2008 R2 和 Windows 7 上安裝 WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="03788-147">Installing WMF 5.1 on Windows Server 2008 R2 and Windows 7</span></span>

1. <span data-ttu-id="03788-148">瀏覽至您用來下載 ZIP 檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="03788-148">Navigate to the folder into which you downloaded the ZIP file.</span></span>

2. <span data-ttu-id="03788-149">以滑鼠右鍵按一下 ZIP 檔案，並選取 [解壓縮全部...]  。ZIP 檔案包含兩個檔案：MSU 和 `Install-WMF5.1.ps1` 指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="03788-149">Right-click on the ZIP file, and select **Extract All...**. The ZIP file contains two files: an MSU and the `Install-WMF5.1.ps1` script file.</span></span> <span data-ttu-id="03788-150">一旦您解壓縮 ZIP 檔案，您可以將內容複製到執行 Windows 7 或 Windows Server 2008 R2 的任何電腦。</span><span class="sxs-lookup"><span data-stu-id="03788-150">Once you have unpacked the ZIP file, you can copy the contents to any machine running Windows 7 or Windows Server 2008 R2.</span></span>

3. <span data-ttu-id="03788-151">將 ZIP 檔案內容解壓縮之後，以系統管理員身分開啟 PowerShell，然後瀏覽至包含 ZIP 檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="03788-151">After extracting the ZIP file contents, open PowerShell as administrator, then navigate to the folder containing the contents of the ZIP file.</span></span>

4. <span data-ttu-id="03788-152">在該資料夾中執行 `Install-WMF5.1.ps1` 指令碼，並遵循指示。</span><span class="sxs-lookup"><span data-stu-id="03788-152">Run the `Install-WMF5.1.ps1` script in that folder, and follow the instructions.</span></span> <span data-ttu-id="03788-153">此指令碼會檢查本機電腦上的必要條件，並安裝 WMF 5.1 (如果符合必要條件)。</span><span class="sxs-lookup"><span data-stu-id="03788-153">This script will check the prerequisites on the local machine, and install WMF 5.1 if the prerequisites have been met.</span></span> <span data-ttu-id="03788-154">以下列出必要條件。</span><span class="sxs-lookup"><span data-stu-id="03788-154">The prerequisites are listed below.</span></span>

   <span data-ttu-id="03788-155">`Install-WMF5.1.ps1` 會採用下列參數以簡化針對 Windows Server 2008 R2 和 Windows 7 上安裝的自動化：</span><span class="sxs-lookup"><span data-stu-id="03788-155">`Install-WMF5.1.ps1` takes the following parameters to ease automating the installation on Windows Server 2008 R2 and Windows 7:</span></span>

   - <span data-ttu-id="03788-156">**AcceptEula**：當包含此參數時，會自動接受 EULA 且不會顯示。</span><span class="sxs-lookup"><span data-stu-id="03788-156">**AcceptEula**: When this parameter is included, the EULA is automatically accepted and will not be displayed.</span></span>
   - <span data-ttu-id="03788-157">**AllowRestart**：此參數只能在指定 AcceptEula 時使用。</span><span class="sxs-lookup"><span data-stu-id="03788-157">**AllowRestart**: This parameter can only be used if AcceptEula is specified.</span></span> <span data-ttu-id="03788-158">如果包含此參數，且安裝 WMF 5.1 之後需要重新啟動，則在完成安裝之後會立即重新啟動而不提示。</span><span class="sxs-lookup"><span data-stu-id="03788-158">If this parameter is included, and a restart is required after installing WMF 5.1, the restart will happen without prompting immediately after the installation is completed.</span></span>

## <a name="winrm-dependency"></a><span data-ttu-id="03788-159">WinRM 相依性</span><span class="sxs-lookup"><span data-stu-id="03788-159">WinRM Dependency</span></span>

<span data-ttu-id="03788-160">Windows PowerShell 預期狀態設定 (DSC) 取決於 WinRM。</span><span class="sxs-lookup"><span data-stu-id="03788-160">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span> <span data-ttu-id="03788-161">在 Windows Server 2008 R2 和 Windows 7 上預設不啟用 WinRM。</span><span class="sxs-lookup"><span data-stu-id="03788-161">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span> <span data-ttu-id="03788-162">若要啟用 WinRM，請在 Windows PowerShell 提高權限的工作階段中，執行 `Set-WSManQuickConfig`。</span><span class="sxs-lookup"><span data-stu-id="03788-162">Run `Set-WSManQuickConfig`, in a Windows PowerShell elevated session, to enable WinRM.</span></span>

## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a><span data-ttu-id="03788-163">安裝適用於 Windows Server 2012 R2、Windows Server 2012 和 Windows 8.1 的 WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="03788-163">Install WMF 5.1 for Windows Server 2012 R2, Windows Server 2012, and Windows 8.1</span></span>

### <a name="install-from-windows-file-explorer"></a><span data-ttu-id="03788-164">從 Windows 檔案總管安裝</span><span class="sxs-lookup"><span data-stu-id="03788-164">Install from Windows File Explorer</span></span>

1. <span data-ttu-id="03788-165">瀏覽至您用來下載 MSU 檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="03788-165">Navigate to the folder into which you downloaded the MSU file.</span></span>
2. <span data-ttu-id="03788-166">按兩下 MSU 以執行。</span><span class="sxs-lookup"><span data-stu-id="03788-166">Double-click the MSU to run it.</span></span>

### <a name="installing-from-the-command-prompt"></a><span data-ttu-id="03788-167">從命令提示字元安裝</span><span class="sxs-lookup"><span data-stu-id="03788-167">Installing from the Command Prompt</span></span>

1. <span data-ttu-id="03788-168">下載您電腦架構的正確封裝之後，以提高的使用者權限 (以系統管理員身分執行) 開啟 [命令提示字元] 視窗。</span><span class="sxs-lookup"><span data-stu-id="03788-168">After downloading the correct package for your computer's architecture, open a Command Prompt window with elevated user rights (Run as Administrator).</span></span> <span data-ttu-id="03788-169">在 Windows Server 2012 R2、Windows Server 2012 或 Windows Server 2008 R2 SP1 的 Server Core 安裝選項上，預設會以提高的使用者權限開啟 [命令提示字元]。</span><span class="sxs-lookup"><span data-stu-id="03788-169">On the Server Core installation options of Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1, Command Prompt opens with elevated user rights by default.</span></span>
2. <span data-ttu-id="03788-170">將目錄變更為您已下載或複製 WMF 5.1 安裝封裝的資料夾。</span><span class="sxs-lookup"><span data-stu-id="03788-170">Change directories to the folder into which you have downloaded or copied the WMF 5.1 installation package.</span></span>
3. <span data-ttu-id="03788-171">執行下列其中一個命令：</span><span class="sxs-lookup"><span data-stu-id="03788-171">Run one of the following commands:</span></span>
   - <span data-ttu-id="03788-172">在執行 Windows Server 2012 R2 或 Windows 8.1 x64 的電腦上執行 `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`。</span><span class="sxs-lookup"><span data-stu-id="03788-172">On computers that are running Windows Server 2012 R2 or Windows 8.1 x64, run `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.</span></span>
   - <span data-ttu-id="03788-173">在執行 Windows Server 2012 的電腦上執行 `W2K12-KB3191565-x64.msu /quiet`。</span><span class="sxs-lookup"><span data-stu-id="03788-173">On computers that are running Windows Server 2012, run `W2K12-KB3191565-x64.msu /quiet`.</span></span>
   - <span data-ttu-id="03788-174">在執行 Windows 8.1 x86 的電腦上執行 `Win8.1-KB3191564-x86.msu /quiet`。</span><span class="sxs-lookup"><span data-stu-id="03788-174">On computers that are running Windows 8.1 x86, run `Win8.1-KB3191564-x86.msu /quiet`.</span></span>

> [!NOTE]
> <span data-ttu-id="03788-175">安裝 WMF 5.1 需要重新開機。</span><span class="sxs-lookup"><span data-stu-id="03788-175">Installing WMF 5.1 requires a reboot.</span></span> <span data-ttu-id="03788-176">使用 `/quiet` 選項會將系統重新開機，而不發出警告。</span><span class="sxs-lookup"><span data-stu-id="03788-176">Using the `/quiet` option will reboot the system without warning.</span></span> <span data-ttu-id="03788-177">使用 `/norestart` 選項可避免重新開機。</span><span class="sxs-lookup"><span data-stu-id="03788-177">Use the `/norestart` option to avoid rebooting.</span></span> <span data-ttu-id="03788-178">不過，在重新開機之前都不會安裝 WMF 5.1。</span><span class="sxs-lookup"><span data-stu-id="03788-178">However, WMF 5.1 will not be installed until you have rebooted.</span></span>
