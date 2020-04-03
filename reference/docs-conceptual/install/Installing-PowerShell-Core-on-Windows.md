---
title: 在 Windows 上安裝 PowerShell
description: 在 Windows 上安裝 PowerShell 的相關資訊
ms.date: 08/06/2018
ms.openlocfilehash: ea5432725f4baea8c688fb8e67482910e2c3981e
ms.sourcegitcommit: b6cf10224eb9f32919a505cdffbe5968241c18a1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2020
ms.locfileid: "80374885"
---
# <a name="installing-powershell-on-windows"></a><span data-ttu-id="b543a-103">在 Windows 上安裝 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b543a-103">Installing PowerShell on Windows</span></span>

<span data-ttu-id="b543a-104">有多種方法可以在 Windows 中安裝 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="b543a-104">There are multiple ways to install PowerShell in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b543a-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="b543a-105">Prerequisites</span></span>

<span data-ttu-id="b543a-106">在 Windows 7 SP1、Server 2008 R2 和更新版本上支援 PowerShell 的最新版本。</span><span class="sxs-lookup"><span data-stu-id="b543a-106">The latest release of PowerShell is supported on Windows 7 SP1, Server 2008 R2, and later versions.</span></span>

<span data-ttu-id="b543a-107">若要透過 WSMan 啟用 PowerShell 遠端執行功能，必須符合下列必要條件：</span><span class="sxs-lookup"><span data-stu-id="b543a-107">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="b543a-108">在 Windows 10 以前的 Windows 版本中安裝[通用 C 執行階段](https://www.microsoft.com/download/details.aspx?id=50410)。</span><span class="sxs-lookup"><span data-stu-id="b543a-108">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions predating Windows 10.</span></span> <span data-ttu-id="b543a-109">透過直接下載或 Windows Update 即可取得。</span><span class="sxs-lookup"><span data-stu-id="b543a-109">It's available via direct download or Windows Update.</span></span> <span data-ttu-id="b543a-110">已完整修補的系統已安裝此套件。</span><span class="sxs-lookup"><span data-stu-id="b543a-110">Fully patched systems already have this package installed.</span></span>
- <span data-ttu-id="b543a-111">在 Windows 7 和 Windows Server 2008 R2 上安裝 Windows Management Framework (WMF) 4.0 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="b543a-111">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="b543a-112">如需 WMF 的詳細資訊，請參閱 [WMF 概觀](/powershell/scripting/wmf/overview)。</span><span class="sxs-lookup"><span data-stu-id="b543a-112">For more information about WMF, see [WMF Overview](/powershell/scripting/wmf/overview).</span></span>

## <a name="download-the-installer-package"></a><span data-ttu-id="b543a-113">下載安裝程式套件</span><span class="sxs-lookup"><span data-stu-id="b543a-113">Download the installer package</span></span>

<span data-ttu-id="b543a-114">若要在 Windows 上安裝 PowerShell，請從我們的 GitHub [版本][releases] 頁面下載安裝套件。</span><span class="sxs-lookup"><span data-stu-id="b543a-114">To install PowerShell on Windows, download the install package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="b543a-115">向下捲動至 [版本] 頁面的 [資產] 區段。</span><span class="sxs-lookup"><span data-stu-id="b543a-115">Scroll down to the **Assets** section of the Release page.</span></span> <span data-ttu-id="b543a-116">[資產] 區段可能會摺疊，因此您可能需要按一下加以展開。</span><span class="sxs-lookup"><span data-stu-id="b543a-116">The **Assets** section may be collapsed, so you may need to click to expand it.</span></span>

## <a name="installing-the-msi-package"></a><span data-ttu-id="b543a-117"><a id="msi" />安裝 MSI 套件</span><span class="sxs-lookup"><span data-stu-id="b543a-117"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="b543a-118">MSI 檔案看起來像 `PowerShell-<version>-win-<os-arch>.msi`。</span><span class="sxs-lookup"><span data-stu-id="b543a-118">The MSI file looks like `PowerShell-<version>-win-<os-arch>.msi`.</span></span> <span data-ttu-id="b543a-119">例如：</span><span class="sxs-lookup"><span data-stu-id="b543a-119">For example:</span></span>

- `PowerShell-7.0.0-win-x64.msi`
- `PowerShell-7.0.0-win-x86.msi`

<span data-ttu-id="b543a-120">下載後，按兩下安裝程式，並依提示操作。</span><span class="sxs-lookup"><span data-stu-id="b543a-120">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="b543a-121">安裝程式會在 Windows [開始] 功能表中建立捷徑。</span><span class="sxs-lookup"><span data-stu-id="b543a-121">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="b543a-122">套件預設安裝在 `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="b543a-122">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="b543a-123">您可以透過 [開始] 功能表或 `$env:ProgramFiles\PowerShell\<version>\pwsh.exe` 啟動 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b543a-123">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

> [!NOTE]
> <span data-ttu-id="b543a-124">PowerShell 7 會安裝到新目錄，並與 Windows PowerShell 5.1 並存執行。</span><span class="sxs-lookup"><span data-stu-id="b543a-124">PowerShell 7 installs to a new directory and runs side-by-side with Windows PowerShell 5.1.</span></span> <span data-ttu-id="b543a-125">針對 PowerShell Core 6.x，PowerShell 7 會就地升級並移除 PowerShell Core 6.x。</span><span class="sxs-lookup"><span data-stu-id="b543a-125">For PowerShell Core 6.x, PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> - <span data-ttu-id="b543a-126">PowerShell 7 會安裝到 `$env:ProgramFiles\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="b543a-126">PowerShell 7 is installed to `$env:ProgramFiles\PowerShell\7`</span></span>
> - <span data-ttu-id="b543a-127">系統會在 `$env:PATH` 中新增 `$env:ProgramFiles\PowerShell\7` 資料夾</span><span class="sxs-lookup"><span data-stu-id="b543a-127">The `$env:ProgramFiles\PowerShell\7` folder is added to `$env:PATH`</span></span>
> - <span data-ttu-id="b543a-128">系統會刪除 `$env:ProgramFiles\PowerShell\6` 資料夾</span><span class="sxs-lookup"><span data-stu-id="b543a-128">The `$env:ProgramFiles\PowerShell\6` folder is deleted</span></span>
>
> <span data-ttu-id="b543a-129">如果您需要與 PowerShell 7 並存執行 PowerShell 6，請使用 [ZIP 安裝](#zip)方法來重新安裝 PowerShell 6。</span><span class="sxs-lookup"><span data-stu-id="b543a-129">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [ZIP install](#zip) method.</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="b543a-130">從命令列進行系統管理安裝</span><span class="sxs-lookup"><span data-stu-id="b543a-130">Administrative install from the command line</span></span>

<span data-ttu-id="b543a-131">您可以從命令列安裝 MSI 套件，讓系統管理員不需要使用者互動即可部署套件。</span><span class="sxs-lookup"><span data-stu-id="b543a-131">MSI packages can be installed from the command line allowing administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="b543a-132">MSI 套件包含下列屬性以控制安裝選項：</span><span class="sxs-lookup"><span data-stu-id="b543a-132">The MSI package includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="b543a-133">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - 此屬性控制將 [開啟 PowerShell] 項目新增至 Windows 檔案總管中的內容功能表的選項。</span><span class="sxs-lookup"><span data-stu-id="b543a-133">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="b543a-134">**ENABLE_PSREMOTING** - 此屬性控制在安裝期間啟用 PowerShell 遠端執行功能的選項。</span><span class="sxs-lookup"><span data-stu-id="b543a-134">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="b543a-135">**REGISTER_MANIFEST** - 此屬性控制用於註冊 Windows 事件記錄資訊清單的選項。</span><span class="sxs-lookup"><span data-stu-id="b543a-135">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="b543a-136">下列範例示範如何在啟用所有安裝選項的情況下，以無訊息方式安裝 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="b543a-136">The following example shows how to silently install PowerShell with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-7.0.0-win-x64.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="b543a-137">如需 `Msiexec.exe` 的命令列選項完整清單，請參閱[命令列選項](/windows/desktop/Msi/command-line-options)。</span><span class="sxs-lookup"><span data-stu-id="b543a-137">For a full list of command-line options for `Msiexec.exe`, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="installing-the-msix-package"></a><span data-ttu-id="b543a-138"><a id="msix" />安裝 MSIX 套件</span><span class="sxs-lookup"><span data-stu-id="b543a-138"><a id="msix" />Installing the MSIX package</span></span>

<span data-ttu-id="b543a-139">若要手動在 Windows 10 用戶端上安裝 MSIX 套件，請從我們的 GitHub [發行][releases] 頁面下載 MSIX 套件。</span><span class="sxs-lookup"><span data-stu-id="b543a-139">To manually install the MSIX package on a Windows 10 client, download the MSIX package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="b543a-140">向下捲動至想安裝版本的 [資產] 區段。</span><span class="sxs-lookup"><span data-stu-id="b543a-140">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="b543a-141">[資產] 區段可能會摺疊，因此您可能需要按一下以展開它。</span><span class="sxs-lookup"><span data-stu-id="b543a-141">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="b543a-142">MSIX 檔案看起來像這樣 - `PowerShell-<version>-win-<os-arch>.msix`</span><span class="sxs-lookup"><span data-stu-id="b543a-142">The MSIX file looks like this - `PowerShell-<version>-win-<os-arch>.msix`</span></span>

<span data-ttu-id="b543a-143">若要安裝套件，您必須使用 `Add-AppxPackage` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b543a-143">To install the package, you must use the `Add-AppxPackage` cmdlet.</span></span>

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

> [!NOTE]
> <span data-ttu-id="b543a-144">MSIX 套件尚未發行。</span><span class="sxs-lookup"><span data-stu-id="b543a-144">The MSIX package has not been released yet.</span></span> <span data-ttu-id="b543a-145">發行後，套件可在 Microsoft Store 中取得，以及從 GitHub [版本][releases] 頁面中取得。</span><span class="sxs-lookup"><span data-stu-id="b543a-145">When released, the package will be available in the Microsoft Store and from the GitHub [releases][releases] page.</span></span>

## <a name="installing-the-zip-package"></a><span data-ttu-id="b543a-146"><a id="zip" />安裝 ZIP 套件</span><span class="sxs-lookup"><span data-stu-id="b543a-146"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="b543a-147">有 PowerShell 二進位 ZIP 封存，以啟用進階的部署案例。</span><span class="sxs-lookup"><span data-stu-id="b543a-147">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="b543a-148">安裝 ZIP 封存並不會像 MSI 套件一樣檢查必要條件。</span><span class="sxs-lookup"><span data-stu-id="b543a-148">Installing the ZIP archive doesn't check the prerequisites like the MSI packages do.</span></span> <span data-ttu-id="b543a-149">若要使遠端功能能透過 WSMan 正常運作，請確定您已符合[必要條件](#prerequisites)。</span><span class="sxs-lookup"><span data-stu-id="b543a-149">For remoting over WSMan to work properly, ensure that you've met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="b543a-150">在 Windows IoT 上部署</span><span class="sxs-lookup"><span data-stu-id="b543a-150">Deploying on Windows IoT</span></span>

<span data-ttu-id="b543a-151">Windows IoT 隨附 Windows PowerShell，我們可以將其用來部署 PowerShell 7。</span><span class="sxs-lookup"><span data-stu-id="b543a-151">Windows IoT comes with Windows PowerShell, which we can use to deploy PowerShell 7.</span></span>

1. <span data-ttu-id="b543a-152">針對目標裝置建立 `PSSession`</span><span class="sxs-lookup"><span data-stu-id="b543a-152">Create `PSSession` to target device</span></span>

   ```powershell
   Set-Item -Path WSMan:\localhost\Client\TrustedHosts <deviceip>
   $S = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="b543a-153">將 ZIP 套件複製到裝置</span><span class="sxs-lookup"><span data-stu-id="b543a-153">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="b543a-154">連接到裝置並展開封存</span><span class="sxs-lookup"><span data-stu-id="b543a-154">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="b543a-155">設定 PowerShell 7 的遠端功能</span><span class="sxs-lookup"><span data-stu-id="b543a-155">Set up remoting to PowerShell 7</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="b543a-156">連線到裝置上的 PowerShell 7 端點</span><span class="sxs-lookup"><span data-stu-id="b543a-156">Connect to PowerShell 7 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="b543a-157">在 Nano Server 上部署</span><span class="sxs-lookup"><span data-stu-id="b543a-157">Deploying on Nano Server</span></span>

<span data-ttu-id="b543a-158">這些指示假設 Nano Server 是一個 PowerShell 版本已在其上執行的「無周邊」作業系統。</span><span class="sxs-lookup"><span data-stu-id="b543a-158">These instructions assume that the Nano Server is a "headless" OS that has a version of PowerShell is already running on it.</span></span> <span data-ttu-id="b543a-159">如需詳細資訊，請參閱 [Nano Server 映像建立器](/windows-server/get-started/deploy-nano-server) 文件。</span><span class="sxs-lookup"><span data-stu-id="b543a-159">For more information, see the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server) documentation.</span></span>

<span data-ttu-id="b543a-160">目前可以使用兩種方法來部署 PowerShell 二進位檔。</span><span class="sxs-lookup"><span data-stu-id="b543a-160">PowerShell binaries can be deployed using two different methods.</span></span>

1. <span data-ttu-id="b543a-161">離線 - 掛接 Nano Server VHD，並將 ZIP 檔案內容解壓縮至您在掛接映像中選擇的位置。</span><span class="sxs-lookup"><span data-stu-id="b543a-161">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="b543a-162">線上 - 透過 PowerShell 工作階段傳輸 ZIP 檔案，並將它解壓縮至您選擇的位置。</span><span class="sxs-lookup"><span data-stu-id="b543a-162">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="b543a-163">在這兩種情況下，您都需要 Windows 10 x64 ZIP 版套件。</span><span class="sxs-lookup"><span data-stu-id="b543a-163">In both cases, you need the Windows 10 x64 ZIP release package.</span></span> <span data-ttu-id="b543a-164">在 PowerShell 的「系統管理員」執行個體中執行命令。</span><span class="sxs-lookup"><span data-stu-id="b543a-164">Run the commands within an "Administrator" instance of PowerShell.</span></span>

### <a name="offline-deployment-of-powershell"></a><span data-ttu-id="b543a-165">PowerShell 的離線部署</span><span class="sxs-lookup"><span data-stu-id="b543a-165">Offline Deployment of PowerShell</span></span>

1. <span data-ttu-id="b543a-166">使用您最愛的 ZIP 公用程式將套件解壓縮至已掛接 Nano Server 映像的目錄。</span><span class="sxs-lookup"><span data-stu-id="b543a-166">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="b543a-167">取消掛接映像和開機映像。</span><span class="sxs-lookup"><span data-stu-id="b543a-167">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="b543a-168">連線到 Windows PowerShell 的收件匣執行個體。</span><span class="sxs-lookup"><span data-stu-id="b543a-168">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="b543a-169">請遵循下列指示來建立使用[另一個執行個體技術](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)的遠端端點。</span><span class="sxs-lookup"><span data-stu-id="b543a-169">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell"></a><span data-ttu-id="b543a-170">PowerShell 的線上部署</span><span class="sxs-lookup"><span data-stu-id="b543a-170">Online Deployment of PowerShell</span></span>

<span data-ttu-id="b543a-171">使用下列步驟，將 PowerShell 部署到 Nano Server。</span><span class="sxs-lookup"><span data-stu-id="b543a-171">Deploy PowerShell to Nano Server using the following steps.</span></span>

- <span data-ttu-id="b543a-172">連線到 Windows PowerShell 的收件匣執行個體</span><span class="sxs-lookup"><span data-stu-id="b543a-172">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="b543a-173">將檔案複製到 Nano Server 執行個體</span><span class="sxs-lookup"><span data-stu-id="b543a-173">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="b543a-174">輸入工作階段</span><span class="sxs-lookup"><span data-stu-id="b543a-174">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="b543a-175">壓縮檔 ZIP 檔案</span><span class="sxs-lookup"><span data-stu-id="b543a-175">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShell_<version>"
  ```

- <span data-ttu-id="b543a-176">如需 WSMan 型的遠端功能，請遵循下列指示來建立使用[另一個執行個體技術](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)的遠端端點。</span><span class="sxs-lookup"><span data-stu-id="b543a-176">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="b543a-177">安裝為 .NET 全域工具</span><span class="sxs-lookup"><span data-stu-id="b543a-177">Install as a .NET Global tool</span></span>

<span data-ttu-id="b543a-178">如果您已安裝 [.NET Core SDK](/dotnet/core/sdk)，就可以輕鬆地將 PowerShell 安裝為 [.NET 全域工具](/dotnet/core/tools/global-tools)。</span><span class="sxs-lookup"><span data-stu-id="b543a-178">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="b543a-179">Dotnet 工具安裝程式會將 `$env:USERPROFILE\dotnet\tools` 新增至您的 `$env:PATH` 環境變數。</span><span class="sxs-lookup"><span data-stu-id="b543a-179">The dotnet tool installer adds `$env:USERPROFILE\dotnet\tools` to your `$env:PATH` environment variable.</span></span> <span data-ttu-id="b543a-180">不過，目前執行的殼層沒有更新的 `$env:PATH`。</span><span class="sxs-lookup"><span data-stu-id="b543a-180">However, the currently running shell doesn't have the updated `$env:PATH`.</span></span> <span data-ttu-id="b543a-181">您可以透過輸入 `pwsh`，以從新的殼層啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="b543a-181">You can start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="b543a-182">如何建立遠端端點</span><span class="sxs-lookup"><span data-stu-id="b543a-182">How to create a remoting endpoint</span></span>

<span data-ttu-id="b543a-183">PowerShell 支援透過 WSMan 與 SSH 的 PowerShell 遠端通訊協定 (PSRP)。</span><span class="sxs-lookup"><span data-stu-id="b543a-183">PowerShell supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="b543a-184">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="b543a-184">For more information, see:</span></span>

- <span data-ttu-id="b543a-185">[PowerShell Core 中的 SSH 遠端功能][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="b543a-185">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="b543a-186">[PowerShell Core 中的 WSMan 遠端功能][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="b543a-186">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
