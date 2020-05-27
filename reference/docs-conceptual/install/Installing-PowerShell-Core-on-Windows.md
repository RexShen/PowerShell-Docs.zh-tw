---
title: 在 Windows 上安裝 PowerShell
description: 在 Windows 上安裝 PowerShell 的相關資訊
ms.date: 05/21/2020
ms.openlocfilehash: 864f297e4f569030439bd6b581ef593d36f8b910
ms.sourcegitcommit: fd6a33b9fac973b3554fecfea7f51475e650a606
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83791493"
---
# <a name="installing-powershell-on-windows"></a><span data-ttu-id="77897-103">在 Windows 上安裝 PowerShell</span><span class="sxs-lookup"><span data-stu-id="77897-103">Installing PowerShell on Windows</span></span>

<span data-ttu-id="77897-104">有多種方法可以在 Windows 中安裝 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="77897-104">There are multiple ways to install PowerShell in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="77897-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="77897-105">Prerequisites</span></span>

<span data-ttu-id="77897-106">在 Windows 7 SP1、Server 2008 R2 和更新版本上支援 PowerShell 的最新版本。</span><span class="sxs-lookup"><span data-stu-id="77897-106">The latest release of PowerShell is supported on Windows 7 SP1, Server 2008 R2, and later versions.</span></span>

<span data-ttu-id="77897-107">若要透過 WSMan 啟用 PowerShell 遠端執行功能，必須符合下列必要條件：</span><span class="sxs-lookup"><span data-stu-id="77897-107">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="77897-108">在 Windows 10 以前的 Windows 版本中安裝[通用 C 執行階段](https://www.microsoft.com/download/details.aspx?id=50410)。</span><span class="sxs-lookup"><span data-stu-id="77897-108">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions predating Windows 10.</span></span> <span data-ttu-id="77897-109">透過直接下載或 Windows Update 即可取得。</span><span class="sxs-lookup"><span data-stu-id="77897-109">It's available via direct download or Windows Update.</span></span> <span data-ttu-id="77897-110">已完整修補的系統已安裝此套件。</span><span class="sxs-lookup"><span data-stu-id="77897-110">Fully patched systems already have this package installed.</span></span>
- <span data-ttu-id="77897-111">在 Windows 7 和 Windows Server 2008 R2 上安裝 Windows Management Framework (WMF) 4.0 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="77897-111">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="77897-112">如需 WMF 的詳細資訊，請參閱 [WMF 概觀](/powershell/scripting/wmf/overview)。</span><span class="sxs-lookup"><span data-stu-id="77897-112">For more information about WMF, see [WMF Overview](/powershell/scripting/wmf/overview).</span></span>

## <a name="download-the-installer-package"></a><span data-ttu-id="77897-113">下載安裝程式套件</span><span class="sxs-lookup"><span data-stu-id="77897-113">Download the installer package</span></span>

<span data-ttu-id="77897-114">若要在 Windows 上安裝 PowerShell，請從我們的 GitHub [版本][releases] 頁面下載安裝套件。</span><span class="sxs-lookup"><span data-stu-id="77897-114">To install PowerShell on Windows, download the install package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="77897-115">向下捲動至 [版本] 頁面的 [資產]  區段。</span><span class="sxs-lookup"><span data-stu-id="77897-115">Scroll down to the **Assets** section of the Release page.</span></span> <span data-ttu-id="77897-116">[資產]  區段可能會摺疊，因此您可能需要按一下加以展開。</span><span class="sxs-lookup"><span data-stu-id="77897-116">The **Assets** section may be collapsed, so you may need to click to expand it.</span></span>

## <a name="installing-the-msi-package"></a><span data-ttu-id="77897-117"><a id="msi" />安裝 MSI 套件</span><span class="sxs-lookup"><span data-stu-id="77897-117"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="77897-118">MSI 檔案看起來像 `PowerShell-<version>-win-<os-arch>.msi`。</span><span class="sxs-lookup"><span data-stu-id="77897-118">The MSI file looks like `PowerShell-<version>-win-<os-arch>.msi`.</span></span> <span data-ttu-id="77897-119">例如：</span><span class="sxs-lookup"><span data-stu-id="77897-119">For example:</span></span>

- `PowerShell-7.0.1-win-x64.msi`
- `PowerShell-7.0.1-win-x86.msi`

<span data-ttu-id="77897-120">下載後，按兩下安裝程式，並依提示操作。</span><span class="sxs-lookup"><span data-stu-id="77897-120">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="77897-121">安裝程式會在 Windows [開始] 功能表中建立捷徑。</span><span class="sxs-lookup"><span data-stu-id="77897-121">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="77897-122">套件預設安裝在 `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="77897-122">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="77897-123">您可以透過 [開始] 功能表或 `$env:ProgramFiles\PowerShell\<version>\pwsh.exe` 啟動 PowerShell</span><span class="sxs-lookup"><span data-stu-id="77897-123">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

> [!NOTE]
> <span data-ttu-id="77897-124">PowerShell 7 會安裝到新目錄，並與 Windows PowerShell 5.1 並存執行。</span><span class="sxs-lookup"><span data-stu-id="77897-124">PowerShell 7 installs to a new directory and runs side-by-side with Windows PowerShell 5.1.</span></span> <span data-ttu-id="77897-125">針對 PowerShell Core 6.x，PowerShell 7 會就地升級並移除 PowerShell Core 6.x。</span><span class="sxs-lookup"><span data-stu-id="77897-125">For PowerShell Core 6.x, PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> - <span data-ttu-id="77897-126">PowerShell 7 會安裝到 `$env:ProgramFiles\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="77897-126">PowerShell 7 is installed to `$env:ProgramFiles\PowerShell\7`</span></span>
> - <span data-ttu-id="77897-127">系統會在 `$env:PATH` 中新增 `$env:ProgramFiles\PowerShell\7` 資料夾</span><span class="sxs-lookup"><span data-stu-id="77897-127">The `$env:ProgramFiles\PowerShell\7` folder is added to `$env:PATH`</span></span>
> - <span data-ttu-id="77897-128">系統會刪除 `$env:ProgramFiles\PowerShell\6` 資料夾</span><span class="sxs-lookup"><span data-stu-id="77897-128">The `$env:ProgramFiles\PowerShell\6` folder is deleted</span></span>
>
> <span data-ttu-id="77897-129">如果您需要與 PowerShell 7 並存執行 PowerShell 6，請使用 [ZIP 安裝](#zip)方法來重新安裝 PowerShell 6。</span><span class="sxs-lookup"><span data-stu-id="77897-129">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [ZIP install](#zip) method.</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="77897-130">從命令列進行系統管理安裝</span><span class="sxs-lookup"><span data-stu-id="77897-130">Administrative install from the command line</span></span>

<span data-ttu-id="77897-131">您可以從命令列安裝 MSI 套件，讓系統管理員不需要使用者互動即可部署套件。</span><span class="sxs-lookup"><span data-stu-id="77897-131">MSI packages can be installed from the command line allowing administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="77897-132">MSI 套件包含下列屬性以控制安裝選項：</span><span class="sxs-lookup"><span data-stu-id="77897-132">The MSI package includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="77897-133">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - 此屬性控制將 [開啟 PowerShell]  項目新增至 Windows 檔案總管中的內容功能表的選項。</span><span class="sxs-lookup"><span data-stu-id="77897-133">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="77897-134">**ENABLE_PSREMOTING** - 此屬性控制在安裝期間啟用 PowerShell 遠端執行功能的選項。</span><span class="sxs-lookup"><span data-stu-id="77897-134">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="77897-135">**REGISTER_MANIFEST** - 此屬性控制用於註冊 Windows 事件記錄資訊清單的選項。</span><span class="sxs-lookup"><span data-stu-id="77897-135">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="77897-136">下列範例示範如何在啟用所有安裝選項的情況下，以無訊息方式安裝 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="77897-136">The following example shows how to silently install PowerShell with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-7.0.1-win-x64.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="77897-137">如需 `Msiexec.exe` 的命令列選項完整清單，請參閱[命令列選項](/windows/desktop/Msi/command-line-options)。</span><span class="sxs-lookup"><span data-stu-id="77897-137">For a full list of command-line options for `Msiexec.exe`, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="installing-the-msix-package"></a><span data-ttu-id="77897-138"><a id="msix" />安裝 MSIX 套件</span><span class="sxs-lookup"><span data-stu-id="77897-138"><a id="msix" />Installing the MSIX package</span></span>

<span data-ttu-id="77897-139">若要手動在 Windows 10 用戶端上安裝 MSIX 套件，請從我們的 GitHub [發行][releases] 頁面下載 MSIX 套件。</span><span class="sxs-lookup"><span data-stu-id="77897-139">To manually install the MSIX package on a Windows 10 client, download the MSIX package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="77897-140">向下捲動至想安裝版本的 [資產]  區段。</span><span class="sxs-lookup"><span data-stu-id="77897-140">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="77897-141">[資產] 區段可能會摺疊，因此您可能需要按一下以展開它。</span><span class="sxs-lookup"><span data-stu-id="77897-141">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="77897-142">MSIX 檔案看起來像這樣 - `PowerShell-<version>-win-<os-arch>.msix`</span><span class="sxs-lookup"><span data-stu-id="77897-142">The MSIX file looks like this - `PowerShell-<version>-win-<os-arch>.msix`</span></span>

<span data-ttu-id="77897-143">若要安裝套件，您必須使用 `Add-AppxPackage` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="77897-143">To install the package, you must use the `Add-AppxPackage` cmdlet.</span></span>

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

> [!NOTE]
> <span data-ttu-id="77897-144">MSIX 套件尚未發行。</span><span class="sxs-lookup"><span data-stu-id="77897-144">The MSIX package has not been released yet.</span></span> <span data-ttu-id="77897-145">發行後，套件可在 Microsoft Store 中取得，以及從 GitHub [版本][releases] 頁面中取得。</span><span class="sxs-lookup"><span data-stu-id="77897-145">When released, the package will be available in the Microsoft Store and from the GitHub [releases][releases] page.</span></span>

## <a name="installing-the-zip-package"></a><span data-ttu-id="77897-146"><a id="zip" />安裝 ZIP 套件</span><span class="sxs-lookup"><span data-stu-id="77897-146"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="77897-147">有 PowerShell 二進位 ZIP 封存，以啟用進階的部署案例。</span><span class="sxs-lookup"><span data-stu-id="77897-147">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="77897-148">安裝 ZIP 封存並不會像 MSI 套件一樣檢查必要條件。</span><span class="sxs-lookup"><span data-stu-id="77897-148">Installing the ZIP archive doesn't check the prerequisites like the MSI packages do.</span></span> <span data-ttu-id="77897-149">從 [[版本]][releases] 頁面下載 ZIP 封存。</span><span class="sxs-lookup"><span data-stu-id="77897-149">Download the ZIP archive from the [releases][releases] page.</span></span> <span data-ttu-id="77897-150">依據您下載檔案的方式，可能需要使用 `Unblock-File`Cmdlet 以將檔案解除封鎖。</span><span class="sxs-lookup"><span data-stu-id="77897-150">Depending on how you download the file you may need to unblock the file using the `Unblock-File` cmdlet.</span></span> <span data-ttu-id="77897-151">將內容解壓縮至您選擇的位置，並從該處執行 `pwsh.exe`。</span><span class="sxs-lookup"><span data-stu-id="77897-151">Unzip the contents to the location of your choice and run `pwsh.exe` from there.</span></span> <span data-ttu-id="77897-152">若要使遠端功能能透過 WSMan 正常運作，請確定您已符合[必要條件](#prerequisites)。</span><span class="sxs-lookup"><span data-stu-id="77897-152">For remoting over WSMan to work properly, ensure that you've met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-10-iot-enterprise"></a><span data-ttu-id="77897-153">在 Windows 10 IoT 企業版上部署</span><span class="sxs-lookup"><span data-stu-id="77897-153">Deploying on Windows 10 IoT Enterprise</span></span>

<span data-ttu-id="77897-154">Windows 10 IoT 企業版隨附 Windows PowerShell，我們可以將其用來部署 PowerShell 7。</span><span class="sxs-lookup"><span data-stu-id="77897-154">Windows 10 IoT Enterprise comes with Windows PowerShell, which we can use to deploy PowerShell 7.</span></span>

1. <span data-ttu-id="77897-155">針對目標裝置建立 `PSSession`</span><span class="sxs-lookup"><span data-stu-id="77897-155">Create `PSSession` to target device</span></span>

   ```powershell
   Set-Item -Path WSMan:\localhost\Client\TrustedHosts <deviceip>
   $S = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="77897-156">將 ZIP 套件複製到裝置</span><span class="sxs-lookup"><span data-stu-id="77897-156">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="77897-157">連接到裝置並展開封存</span><span class="sxs-lookup"><span data-stu-id="77897-157">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="77897-158">設定 PowerShell 7 的遠端功能</span><span class="sxs-lookup"><span data-stu-id="77897-158">Set up remoting to PowerShell 7</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="77897-159">連線到裝置上的 PowerShell 7 端點</span><span class="sxs-lookup"><span data-stu-id="77897-159">Connect to PowerShell 7 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-windows-10-iot-core"></a><span data-ttu-id="77897-160">在 Windows 10 IoT 核心版上部署</span><span class="sxs-lookup"><span data-stu-id="77897-160">Deploying on Windows 10 IoT Core</span></span>

<span data-ttu-id="77897-161">當您包含 *IOT_POWERSHELL* 功能 (可供我們用來部署 PowerShell 7) 時，Windows 10 IoT 核心版會新增 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="77897-161">Windows 10 IoT Core adds Windows PowerShell when you include *IOT_POWERSHELL* feature, which we can use to deploy PowerShell 7.</span></span>
<span data-ttu-id="77897-162">針對 Windows 10 IoT 企業版所定義的步驟也可以用於 IoT 核心版。</span><span class="sxs-lookup"><span data-stu-id="77897-162">The steps defined above for Windows 10 IoT Enterprise can be followed for IoT Core as well.</span></span>

<span data-ttu-id="77897-163">若要在出貨映像中新增最新的 powershell，請使用 [Import-PSCoreRelease](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease) 命令在工作區包括套件，並新增 *OPENSRC_POWERSHELL* 功能到您的映像。</span><span class="sxs-lookup"><span data-stu-id="77897-163">For adding the latest powershell in the shipping image, use [Import-PSCoreRelease](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease) command to include the package in the workarea and add *OPENSRC_POWERSHELL* feature to your image.</span></span>

> [!NOTE]
> <span data-ttu-id="77897-164">針對 ARM64 架構，當您包括 *IOT_POWERSHELL* 時，不會新增 Windows Powershell。</span><span class="sxs-lookup"><span data-stu-id="77897-164">For ARM64 architecture, Windows Powershell is not added when you include *IOT_POWERSHELL*.</span></span> <span data-ttu-id="77897-165">因此，以 zip 為基礎的安裝將無法使用。</span><span class="sxs-lookup"><span data-stu-id="77897-165">So the zip based install will not work.</span></span>
> <span data-ttu-id="77897-166">您將必須使用 Import-PSCoreRelease 命令，將其加入映像中。</span><span class="sxs-lookup"><span data-stu-id="77897-166">You will need to use Import-PSCoreRelease command to add it in the image.</span></span>

## <a name="deploying-on-nano-server"></a><span data-ttu-id="77897-167">在 Nano Server 上部署</span><span class="sxs-lookup"><span data-stu-id="77897-167">Deploying on Nano Server</span></span>

<span data-ttu-id="77897-168">這些指示假設 Nano Server 是一個 PowerShell 版本已在其上執行的「無周邊」作業系統。</span><span class="sxs-lookup"><span data-stu-id="77897-168">These instructions assume that the Nano Server is a "headless" OS that has a version of PowerShell is already running on it.</span></span> <span data-ttu-id="77897-169">如需詳細資訊，請參閱 [Nano Server 映像建立器](/windows-server/get-started/deploy-nano-server) 文件。</span><span class="sxs-lookup"><span data-stu-id="77897-169">For more information, see the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server) documentation.</span></span>

<span data-ttu-id="77897-170">目前可以使用兩種方法來部署 PowerShell 二進位檔。</span><span class="sxs-lookup"><span data-stu-id="77897-170">PowerShell binaries can be deployed using two different methods.</span></span>

1. <span data-ttu-id="77897-171">離線 - 掛接 Nano Server VHD，並將 ZIP 檔案內容解壓縮至您在掛接映像中選擇的位置。</span><span class="sxs-lookup"><span data-stu-id="77897-171">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="77897-172">線上 - 透過 PowerShell 工作階段傳輸 ZIP 檔案，並將它解壓縮至您選擇的位置。</span><span class="sxs-lookup"><span data-stu-id="77897-172">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="77897-173">在這兩種情況下，您都需要 Windows 10 x64 ZIP 版套件。</span><span class="sxs-lookup"><span data-stu-id="77897-173">In both cases, you need the Windows 10 x64 ZIP release package.</span></span> <span data-ttu-id="77897-174">在 PowerShell 的「系統管理員」執行個體中執行命令。</span><span class="sxs-lookup"><span data-stu-id="77897-174">Run the commands within an "Administrator" instance of PowerShell.</span></span>

### <a name="offline-deployment-of-powershell"></a><span data-ttu-id="77897-175">PowerShell 的離線部署</span><span class="sxs-lookup"><span data-stu-id="77897-175">Offline Deployment of PowerShell</span></span>

1. <span data-ttu-id="77897-176">使用您最愛的 ZIP 公用程式將套件解壓縮至已掛接 Nano Server 映像的目錄。</span><span class="sxs-lookup"><span data-stu-id="77897-176">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="77897-177">取消掛接映像和開機映像。</span><span class="sxs-lookup"><span data-stu-id="77897-177">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="77897-178">連線到 Windows PowerShell 的收件匣執行個體。</span><span class="sxs-lookup"><span data-stu-id="77897-178">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="77897-179">請遵循下列指示來建立使用[另一個執行個體技術](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)的遠端端點。</span><span class="sxs-lookup"><span data-stu-id="77897-179">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell"></a><span data-ttu-id="77897-180">PowerShell 的線上部署</span><span class="sxs-lookup"><span data-stu-id="77897-180">Online Deployment of PowerShell</span></span>

<span data-ttu-id="77897-181">使用下列步驟，將 PowerShell 部署到 Nano Server。</span><span class="sxs-lookup"><span data-stu-id="77897-181">Deploy PowerShell to Nano Server using the following steps.</span></span>

- <span data-ttu-id="77897-182">連線到 Windows PowerShell 的收件匣執行個體</span><span class="sxs-lookup"><span data-stu-id="77897-182">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="77897-183">將檔案複製到 Nano Server 執行個體</span><span class="sxs-lookup"><span data-stu-id="77897-183">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="77897-184">輸入工作階段</span><span class="sxs-lookup"><span data-stu-id="77897-184">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="77897-185">壓縮檔 ZIP 檔案</span><span class="sxs-lookup"><span data-stu-id="77897-185">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShell_<version>"
  ```

- <span data-ttu-id="77897-186">如需 WSMan 型的遠端功能，請遵循下列指示來建立使用[另一個執行個體技術](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)的遠端端點。</span><span class="sxs-lookup"><span data-stu-id="77897-186">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="77897-187">安裝為 .NET 全域工具</span><span class="sxs-lookup"><span data-stu-id="77897-187">Install as a .NET Global tool</span></span>

<span data-ttu-id="77897-188">如果您已安裝 [.NET Core SDK](/dotnet/core/sdk)，就可以輕鬆地將 PowerShell 安裝為 [.NET 全域工具](/dotnet/core/tools/global-tools)。</span><span class="sxs-lookup"><span data-stu-id="77897-188">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="77897-189">Dotnet 工具安裝程式會將 `$env:USERPROFILE\dotnet\tools` 新增至您的 `$env:PATH` 環境變數。</span><span class="sxs-lookup"><span data-stu-id="77897-189">The dotnet tool installer adds `$env:USERPROFILE\dotnet\tools` to your `$env:PATH` environment variable.</span></span> <span data-ttu-id="77897-190">不過，目前執行的殼層沒有更新的 `$env:PATH`。</span><span class="sxs-lookup"><span data-stu-id="77897-190">However, the currently running shell doesn't have the updated `$env:PATH`.</span></span> <span data-ttu-id="77897-191">您可以透過輸入 `pwsh`，以從新的殼層啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="77897-191">You can start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="77897-192">如何建立遠端端點</span><span class="sxs-lookup"><span data-stu-id="77897-192">How to create a remoting endpoint</span></span>

<span data-ttu-id="77897-193">PowerShell 支援透過 WSMan 與 SSH 的 PowerShell 遠端通訊協定 (PSRP)。</span><span class="sxs-lookup"><span data-stu-id="77897-193">PowerShell supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="77897-194">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="77897-194">For more information, see:</span></span>

- <span data-ttu-id="77897-195">[PowerShell Core 中的 SSH 遠端功能][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="77897-195">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="77897-196">[PowerShell Core 中的 WSMan 遠端功能][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="77897-196">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
