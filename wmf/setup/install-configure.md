---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,設定
contributor: keithb
title: 安裝與設定 WMF 5.1
ms.openlocfilehash: cb223844c2a214846e7206bcb476fac9154fda4b
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855403"
---
# <a name="install-and-configure-wmf-51"></a><span data-ttu-id="ab918-103">安裝與設定 WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="ab918-103">Install and Configure WMF 5.1</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ab918-104">WMF 5.1 已取代 WMF 5.0。</span><span class="sxs-lookup"><span data-stu-id="ab918-104">WMF 5.0 is superseded by WMF 5.1.</span></span> <span data-ttu-id="ab918-105">使用 WMF 5.0 的使用者必須升級至 WMF 5.1 才能獲得支援。</span><span class="sxs-lookup"><span data-stu-id="ab918-105">Users with WMF 5.0 must upgrade to WMF 5.1 to receive support.</span></span>
> <span data-ttu-id="ab918-106">**WMF 5.1 需要 .NET Framework 4.5.2** (或更新版本)。</span><span class="sxs-lookup"><span data-stu-id="ab918-106">**WMF 5.1 requires the .NET Framework 4.5.2** (or above).</span></span> <span data-ttu-id="ab918-107">雖然安裝會成功，但若未安裝 .NET 4.5.2 (或更新版本)，主要功能將會失敗。</span><span class="sxs-lookup"><span data-stu-id="ab918-107">Installation will succeed, but key features will fail if .NET 4.5.2 (or above) is not installed.</span></span>

## <a name="download-and-install-the-wmf-51-package"></a><span data-ttu-id="ab918-108">下載並安裝 WMF 5.1 套件</span><span class="sxs-lookup"><span data-stu-id="ab918-108">Download and install the WMF 5.1 package</span></span>

<span data-ttu-id="ab918-109">為適用於其安裝所在的作業系統和架構下載 WMF 5.1 封裝︰</span><span class="sxs-lookup"><span data-stu-id="ab918-109">Download the WMF 5.1 package for the operating system and architecture you wish to install it on:</span></span>

| <span data-ttu-id="ab918-110">作業系統</span><span class="sxs-lookup"><span data-stu-id="ab918-110">Operating System</span></span>       | <span data-ttu-id="ab918-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="ab918-111">Prerequisites</span></span>           | <span data-ttu-id="ab918-112">封裝連結</span><span class="sxs-lookup"><span data-stu-id="ab918-112">Package Links</span></span>                          |
|------------------------|-------------------------|----------------------------------------|
| <span data-ttu-id="ab918-113">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="ab918-113">Windows Server 2012 R2</span></span> |                         | <span data-ttu-id="ab918-114">[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="ab918-114">[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span></span> |
| <span data-ttu-id="ab918-115">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="ab918-115">Windows Server 2012</span></span>    |                         | <span data-ttu-id="ab918-116">[W2K12-KB3191565-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="ab918-116">[W2K12-KB3191565-x64.msu][]</span></span>            |
| <span data-ttu-id="ab918-117">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="ab918-117">Windows Server 2008 R2</span></span> | <span data-ttu-id="ab918-118">[.NET Framework 4.5.2][]</span><span class="sxs-lookup"><span data-stu-id="ab918-118">[.NET Framework 4.5.2][]</span></span>| <span data-ttu-id="ab918-119">[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="ab918-119">[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span></span>    |
| <span data-ttu-id="ab918-120">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="ab918-120">Windows 8.1</span></span>            |                         | <span data-ttu-id="ab918-121">**x64:**[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="ab918-121">**x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</span></span></br><span data-ttu-id="ab918-122">**x86:**[Win8.1-KB3191564-x86.msu][]</span><span class="sxs-lookup"><span data-stu-id="ab918-122">**x86:** [Win8.1-KB3191564-x86.msu][]</span></span> |
| <span data-ttu-id="ab918-123">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="ab918-123">Windows 7 SP1</span></span>          | <span data-ttu-id="ab918-124">[.NET Framework 4.5.2][]</span><span class="sxs-lookup"><span data-stu-id="ab918-124">[.NET Framework 4.5.2][]</span></span>| <span data-ttu-id="ab918-125">**x64:**[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="ab918-125">**x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</span></span></br><span data-ttu-id="ab918-126">**x86:**[Win7-KB3191566-x86.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="ab918-126">**x86:** [Win7-KB3191566-x86.ZIP][]</span></span> |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

- <span data-ttu-id="ab918-133">安裝 WMF 5.1 RTM 之前，必須先解除安裝 WMF 5.1 Preview。</span><span class="sxs-lookup"><span data-stu-id="ab918-133">WMF 5.1 Preview must be uninstalled before installing WMF 5.1 RTM.</span></span>
- <span data-ttu-id="ab918-134">WMF 5.1 可直接透過 WMF 5.0 或 WMF 4.0 安裝。</span><span class="sxs-lookup"><span data-stu-id="ab918-134">WMF 5.1 may be installed directly over WMF 5.0 or WMF 4.0.</span></span>
- <span data-ttu-id="ab918-135">在 Windows 7 和 Windows Server 2008 R2 上安裝 WMF 5.1 之前，**不需要**先安裝 WMF 4.0。</span><span class="sxs-lookup"><span data-stu-id="ab918-135">It is **not required** to install WMF 4.0 prior to installing WMF 5.1 on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a><span data-ttu-id="ab918-136">安裝適用於 Windows Server 2008 R2 和 Windows 7 的 WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="ab918-136">Install WMF 5.1 for Windows Server 2008 R2 and Windows 7</span></span>

> [!NOTE]
> <span data-ttu-id="ab918-137">Windows Server 2008 R2 和 Windows 7 的安裝指示已變更，且與其他套件的指示不同。</span><span class="sxs-lookup"><span data-stu-id="ab918-137">Installation instructions for Windows Server 2008 R2 and Windows 7 have changed, and differ from the instructions for the other packages.</span></span> <span data-ttu-id="ab918-138">適用於 Windows Server 2012 R2、Windows Server 2012 和 Windows 8.1 的安裝指示如下。</span><span class="sxs-lookup"><span data-stu-id="ab918-138">Installation instructions for Windows Server 2012 R2, Windows Server 2012, and Windows 8.1 are below.</span></span>

### <a name="installing-wmf-51-on-windows-server-2008-r2-and-windows-7"></a><span data-ttu-id="ab918-139">在 Windows Server 2008 R2 和 Windows 7 上安裝 WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="ab918-139">Installing WMF 5.1 on Windows Server 2008 R2 and Windows 7</span></span>

1. <span data-ttu-id="ab918-140">瀏覽至您用來下載 ZIP 檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="ab918-140">Navigate to the folder into which you downloaded the ZIP file.</span></span>

2. <span data-ttu-id="ab918-141">以滑鼠右鍵按一下 ZIP 檔案，並選取 [解壓縮全部...]。</span><span class="sxs-lookup"><span data-stu-id="ab918-141">Right-click on the ZIP file, and select "Extract All...".</span></span> <span data-ttu-id="ab918-142">ZIP 包含 2 個檔案︰MSU 和 Install-WMF5.1.PS1 指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="ab918-142">The Zip contains 2 files: an MSU and the Install-WMF5.1.PS1 script file.</span></span> <span data-ttu-id="ab918-143">一旦您解壓縮 ZIP 檔案，您可以將內容複製到執行 Windows 7 或 Windows Server 2008 R2 的任何電腦。</span><span class="sxs-lookup"><span data-stu-id="ab918-143">Once you have unpacked the ZIP file, you can copy the contents to any machine running Windows 7 or Windows Server 2008 R2.</span></span>

3. <span data-ttu-id="ab918-144">將 ZIP 檔案內容解壓縮之後，以系統管理員身分開啟 PowerShell，然後瀏覽至包含 ZIP 檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="ab918-144">After extracting the ZIP file contents, open PowerShell as administrator, then navigate to the folder containing the contents of the ZIP file.</span></span>

4. <span data-ttu-id="ab918-145">在該資料夾中執行 Install-Wmf5.1.ps1 指令碼，並遵循指示。</span><span class="sxs-lookup"><span data-stu-id="ab918-145">Run the Install-Wmf5.1.ps1 script in that folder, and follow the instructions.</span></span> <span data-ttu-id="ab918-146">此指令碼會檢查本機電腦上的必要條件，並安裝 WMF 5.1 (如果符合必要條件)。</span><span class="sxs-lookup"><span data-stu-id="ab918-146">This script will check the prerequisites on the local machine, and install WMF 5.1 if the prerequisites have been met.</span></span> <span data-ttu-id="ab918-147">以下列出必要條件。</span><span class="sxs-lookup"><span data-stu-id="ab918-147">The prerequisites are listed below.</span></span>

   <span data-ttu-id="ab918-148">Install-WMF5.1.ps1 會採用下列參數以簡化針對 Windows Server 2008 R2 和 Windows 7 上安裝的自動化：</span><span class="sxs-lookup"><span data-stu-id="ab918-148">Install-WMF5.1.ps1 takes the following parameters to ease automating the installation on Windows Server 2008 R2 and Windows 7:</span></span>

   - <span data-ttu-id="ab918-149">AcceptEula：當包含此參數時，會自動接受 EULA 且不會顯示。</span><span class="sxs-lookup"><span data-stu-id="ab918-149">AcceptEula: When this parameter is included, the EULA is automatically accepted and will not be displayed.</span></span>
   - <span data-ttu-id="ab918-150">AllowRestart：此參數只能在指定 AcceptEula 時使用。</span><span class="sxs-lookup"><span data-stu-id="ab918-150">AllowRestart: This parameter can only be used if AcceptEula is specified.</span></span> <span data-ttu-id="ab918-151">如果包含此參數，且安裝 WMF 5.1 之後需要重新啟動，則在完成安裝之後會立即重新啟動而不提示。</span><span class="sxs-lookup"><span data-stu-id="ab918-151">If this parameter is included, and a restart is required after installing WMF 5.1, the restart will happen without prompting immediately after the installation is completed.</span></span>

### <a name="wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1"></a><span data-ttu-id="ab918-152">Windows Server 2008 R2 SP1 和 Windows 7 SP1 的 WMF 5.1 必要條件</span><span class="sxs-lookup"><span data-stu-id="ab918-152">WMF 5.1 Prerequisites for Windows Server 2008 R2 SP1 and Windows 7 SP1</span></span>

<span data-ttu-id="ab918-153">在 Windows Server 2008 R2 SP1 或 Windows 7 SP1 上安裝 WMF 5.1 需要下列各項：</span><span class="sxs-lookup"><span data-stu-id="ab918-153">Installation of WMF 5.1 on either Windows Server 2008 R2 SP1 or Windows 7 SP1, requires the following:</span></span>

- <span data-ttu-id="ab918-154">必須安裝最新的 Service Pack。</span><span class="sxs-lookup"><span data-stu-id="ab918-154">Latest service pack must be installed.</span></span>
- <span data-ttu-id="ab918-155">「不可以」安裝 WMF 3.0。</span><span class="sxs-lookup"><span data-stu-id="ab918-155">WMF 3.0 **must not** be installed.</span></span> <span data-ttu-id="ab918-156">在具有 WMF 3.0 的情況下安裝 WMF 5.1 會導致 PSModulePath 遺失，這可能造成其他應用程式失敗。</span><span class="sxs-lookup"><span data-stu-id="ab918-156">Installing WMF 5.1 over WMF 3.0 will result in the loss of the PSModulePath, which can cause other applications to fail.</span></span> <span data-ttu-id="ab918-157">在安裝 WMF 5.1 之前，您必須將 WMF 3.0 解除安裝，或是儲存 PSModulePath，並在完成 WMF 5.1 安裝之後，將它手動還原。</span><span class="sxs-lookup"><span data-stu-id="ab918-157">Before installing WMF 5.1, you must either un-install WMF 3.0, or save the PSModulePath and then restore it manually after WMF 5.1 installation is complete.</span></span>
- <span data-ttu-id="ab918-158">WMF 5.1 需要至少[.NET Framework 4.5.2](https://www.microsoft.com/download/details.aspx?id=42642)。</span><span class="sxs-lookup"><span data-stu-id="ab918-158">WMF 5.1 requires at least [.NET Framework 4.5.2](https://www.microsoft.com/download/details.aspx?id=42642).</span></span>
  <span data-ttu-id="ab918-159">您可以遵循下載位置的指示來安裝 Microsoft.NET Framework 4.5.2。</span><span class="sxs-lookup"><span data-stu-id="ab918-159">You can install Microsoft .NET Framework 4.5.2 by following the instructions at the download location.</span></span>

## <a name="winrm-dependency"></a><span data-ttu-id="ab918-160">WinRM 相依性</span><span class="sxs-lookup"><span data-stu-id="ab918-160">WinRM Dependency</span></span>

<span data-ttu-id="ab918-161">Windows PowerShell 預期狀態設定 (DSC) 取決於 WinRM。</span><span class="sxs-lookup"><span data-stu-id="ab918-161">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span> <span data-ttu-id="ab918-162">在 Windows Server 2008 R2 和 Windows 7 上預設不啟用 WinRM。</span><span class="sxs-lookup"><span data-stu-id="ab918-162">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span> <span data-ttu-id="ab918-163">若要啟用 WinRM，請在 Windows PowerShell 提高權限的工作階段中，執行 `Set-WSManQuickConfig`。</span><span class="sxs-lookup"><span data-stu-id="ab918-163">Run `Set-WSManQuickConfig`, in a Windows PowerShell elevated session, to enable WinRM.</span></span>

## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a><span data-ttu-id="ab918-164">安裝適用於 Windows Server 2012 R2、Windows Server 2012 和 Windows 8.1 的 WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="ab918-164">Install WMF 5.1 for Windows Server 2012 R2, Windows Server 2012, and Windows 8.1</span></span>

### <a name="install-from-windows-file-explorer"></a><span data-ttu-id="ab918-165">從 Windows 檔案總管安裝</span><span class="sxs-lookup"><span data-stu-id="ab918-165">Install from Windows File Explorer</span></span>

1. <span data-ttu-id="ab918-166">瀏覽至您用來下載 MSU 檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="ab918-166">Navigate to the folder into which you downloaded the MSU file.</span></span>
2. <span data-ttu-id="ab918-167">按兩下 MSU 以執行。</span><span class="sxs-lookup"><span data-stu-id="ab918-167">Double-click the MSU to run it.</span></span>

### <a name="installing-from-the-command-prompt"></a><span data-ttu-id="ab918-168">從命令提示字元安裝</span><span class="sxs-lookup"><span data-stu-id="ab918-168">Installing from the Command Prompt</span></span>

1. <span data-ttu-id="ab918-169">下載您電腦架構的正確封裝之後，以提高的使用者權限 (以系統管理員身分執行) 開啟 [命令提示字元] 視窗。</span><span class="sxs-lookup"><span data-stu-id="ab918-169">After downloading the correct package for your computer's architecture, open a Command Prompt window with elevated user rights (Run as Administrator).</span></span> <span data-ttu-id="ab918-170">在 Windows Server 2012 R2、Windows Server 2012 或 Windows Server 2008 R2 SP1 的 Server Core 安裝選項上，預設會以提高的使用者權限開啟 [命令提示字元]。</span><span class="sxs-lookup"><span data-stu-id="ab918-170">On the Server Core installation options of Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1, Command Prompt opens with elevated user rights by default.</span></span>
2. <span data-ttu-id="ab918-171">將目錄變更為您已下載或複製 WMF 5.1 安裝封裝的資料夾。</span><span class="sxs-lookup"><span data-stu-id="ab918-171">Change directories to the folder into which you have downloaded or copied the WMF 5.1 installation package.</span></span>
3. <span data-ttu-id="ab918-172">執行下列其中一個命令：</span><span class="sxs-lookup"><span data-stu-id="ab918-172">Run one of the following commands:</span></span>
   - <span data-ttu-id="ab918-173">在執行 Windows Server 2012 R2 或 Windows 8.1 x64 的電腦上執行 `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`。</span><span class="sxs-lookup"><span data-stu-id="ab918-173">On computers that are running Windows Server 2012 R2 or Windows 8.1 x64, run `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.</span></span>
   - <span data-ttu-id="ab918-174">在執行 Windows Server 2012 的電腦上執行 `W2K12-KB3191565-x64.msu /quiet`。</span><span class="sxs-lookup"><span data-stu-id="ab918-174">On computers that are running Windows Server 2012, run `W2K12-KB3191565-x64.msu /quiet`.</span></span>
   - <span data-ttu-id="ab918-175">在執行 Windows 8.1 x86 的電腦上執行 `Win8.1-KB3191564-x86.msu /quiet`。</span><span class="sxs-lookup"><span data-stu-id="ab918-175">On computers that are running Windows 8.1 x86, run `Win8.1-KB3191564-x86.msu /quiet`.</span></span>

> [!NOTE]
> <span data-ttu-id="ab918-176">安裝 WMF 5.1 需要重新開機。</span><span class="sxs-lookup"><span data-stu-id="ab918-176">Installing WMF 5.1 requires a reboot.</span></span> <span data-ttu-id="ab918-177">使用 `/quiet` 選項會將系統重新開機，而不發出警告。</span><span class="sxs-lookup"><span data-stu-id="ab918-177">Using the `/quiet` option will reboot the system without warning.</span></span> <span data-ttu-id="ab918-178">使用 `/norestart` 選項可避免重新開機。</span><span class="sxs-lookup"><span data-stu-id="ab918-178">Use the `/norestart` option to avoid rebooting.</span></span> <span data-ttu-id="ab918-179">不過，在重新開機之前都不會安裝 WMF 5.1。</span><span class="sxs-lookup"><span data-stu-id="ab918-179">However, WMF 5.1 will not be installed until you have rebooted.</span></span>
