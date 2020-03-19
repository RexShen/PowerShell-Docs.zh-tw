---
title: 在 Windows 上安裝 PowerShell
description: 在 Windows 上安裝 PowerShell 的相關資訊
ms.date: 08/06/2018
ms.openlocfilehash: df05a16bcf7a81d43d24535e50517fa217f82e7a
ms.sourcegitcommit: c97dcf1e00ef540e7464c36c88f841474060044c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79402415"
---
# <a name="installing-powershell-on-windows"></a><span data-ttu-id="59ce7-103">在 Windows 上安裝 PowerShell</span><span class="sxs-lookup"><span data-stu-id="59ce7-103">Installing PowerShell on Windows</span></span>

<span data-ttu-id="59ce7-104">有多種方法可以在 Windows 中安裝 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="59ce7-104">There are multiple ways to install PowerShell in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="59ce7-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="59ce7-105">Prerequisites</span></span>

<span data-ttu-id="59ce7-106">若要透過 WSMan 啟用 PowerShell 遠端執行功能，必須符合下列必要條件：</span><span class="sxs-lookup"><span data-stu-id="59ce7-106">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="59ce7-107">在 Windows 10 以下的 Windows 版本中安裝[通用 C 執行階段](https://www.microsoft.com/download/details.aspx?id=50410)。</span><span class="sxs-lookup"><span data-stu-id="59ce7-107">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span> <span data-ttu-id="59ce7-108">透過直接下載或 Windows Update 即可取得。</span><span class="sxs-lookup"><span data-stu-id="59ce7-108">It is available via direct download or Windows Update.</span></span> <span data-ttu-id="59ce7-109">完整修補 (包括選擇性的套件) 的受支援系統已安裝此項目。</span><span class="sxs-lookup"><span data-stu-id="59ce7-109">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="59ce7-110">在 Windows 7 和 Windows Server 2008 R2 上安裝 Windows Management Framework (WMF) 4.0 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="59ce7-110">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="59ce7-111">如需 WMF 的詳細資訊，請參閱 [WMF 概觀](/powershell/scripting/wmf/overview)。</span><span class="sxs-lookup"><span data-stu-id="59ce7-111">For more information about WMF, see [WMF Overview](/powershell/scripting/wmf/overview).</span></span>

## <a name="a-idmsi-installing-the-msi-package"></a><span data-ttu-id="59ce7-112"><a id="msi" />安裝 MSI 套件</span><span class="sxs-lookup"><span data-stu-id="59ce7-112"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="59ce7-113">若要在 Windows 用戶端或 Windows Server 上安裝 PowerShell (適用於 Windows 7 SP1、Server 2008 R2 和更新版本)，請從我們的 GitHub [版本][releases]頁面下載 MSI 套件。</span><span class="sxs-lookup"><span data-stu-id="59ce7-113">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="59ce7-114">向下捲動至想安裝版本的 [資產]  區段。</span><span class="sxs-lookup"><span data-stu-id="59ce7-114">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="59ce7-115">[資產] 區段可能會摺疊，因此您可能需要按一下以展開它。</span><span class="sxs-lookup"><span data-stu-id="59ce7-115">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="59ce7-116">MSI 檔案看起來像這樣 - `PowerShell-<version>-win-<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="59ce7-116">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`</span></span>

<span data-ttu-id="59ce7-117">下載後，按兩下安裝程式，並依提示操作。</span><span class="sxs-lookup"><span data-stu-id="59ce7-117">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="59ce7-118">安裝程式會在 Windows [開始] 功能表中建立捷徑。</span><span class="sxs-lookup"><span data-stu-id="59ce7-118">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="59ce7-119">套件預設安裝在 `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="59ce7-119">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="59ce7-120">您可以透過 [開始] 功能表或 `$env:ProgramFiles\PowerShell\<version>\pwsh.exe` 啟動 PowerShell</span><span class="sxs-lookup"><span data-stu-id="59ce7-120">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

> [!NOTE]
> <span data-ttu-id="59ce7-121">PowerShell 7 會安裝到新目錄，並與 Windows PowerShell 5.1 並存執行。</span><span class="sxs-lookup"><span data-stu-id="59ce7-121">PowerShell 7 installs to a new directory and runs side-by-side with Windows PowerShell 5.1.</span></span> <span data-ttu-id="59ce7-122">針對 PowerShell Core 6.x，PowerShell 7 會就地升級並移除 PowerShell Core 6.x。</span><span class="sxs-lookup"><span data-stu-id="59ce7-122">For PowerShell Core 6.x, PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> - <span data-ttu-id="59ce7-123">PowerShell 7 會安裝到 `%programfiles%\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="59ce7-123">PowerShell 7 is installed to `%programfiles%\PowerShell\7`</span></span>
> - <span data-ttu-id="59ce7-124">系統會在 `$env:PATH` 中新增 `%programfiles%\PowerShell\7` 資料夾</span><span class="sxs-lookup"><span data-stu-id="59ce7-124">The `%programfiles%\PowerShell\7` folder is added to `$env:PATH`</span></span>
> - <span data-ttu-id="59ce7-125">系統會刪除 `%programfiles%\PowerShell\6` 資料夾</span><span class="sxs-lookup"><span data-stu-id="59ce7-125">The `%programfiles%\PowerShell\6` folder is deleted</span></span>
>
> <span data-ttu-id="59ce7-126">如果您需要與 PowerShell 7 並存執行 PowerShell 6，請使用 [ZIP 安裝](#zip)方法來重新安裝 PowerShell 6。</span><span class="sxs-lookup"><span data-stu-id="59ce7-126">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [ZIP install](#zip) method.</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="59ce7-127">從命令列進行系統管理安裝</span><span class="sxs-lookup"><span data-stu-id="59ce7-127">Administrative install from the command line</span></span>

<span data-ttu-id="59ce7-128">可以從命令列安裝 MSI 套件。</span><span class="sxs-lookup"><span data-stu-id="59ce7-128">MSI packages can be installed from the command line.</span></span> <span data-ttu-id="59ce7-129">這允許系統管理員無需使用者互動即可部署套件。</span><span class="sxs-lookup"><span data-stu-id="59ce7-129">This allows administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="59ce7-130">適用於 PowerShell 的 MSI 套件包含下列屬性以控制安裝選項：</span><span class="sxs-lookup"><span data-stu-id="59ce7-130">The MSI package for PowerShell includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="59ce7-131">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - 此屬性控制將 [開啟 PowerShell]  項目新增至 Windows 檔案總管中的內容功能表的選項。</span><span class="sxs-lookup"><span data-stu-id="59ce7-131">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="59ce7-132">**ENABLE_PSREMOTING** - 此屬性控制在安裝期間啟用 PowerShell 遠端執行功能的選項。</span><span class="sxs-lookup"><span data-stu-id="59ce7-132">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="59ce7-133">**REGISTER_MANIFEST** - 此屬性控制用於註冊 Windows 事件記錄資訊清單的選項。</span><span class="sxs-lookup"><span data-stu-id="59ce7-133">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="59ce7-134">下列範例示範如何在啟用所有安裝選項的情況下，以無訊息方式安裝 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="59ce7-134">The following examples shows how to silently install PowerShell with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="59ce7-135">如需 Msiexec.exe 的命令列選項完整清單，請參閱[命令列選項](/windows/desktop/Msi/command-line-options)。</span><span class="sxs-lookup"><span data-stu-id="59ce7-135">For a full list of command line options for Msiexec.exe, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="a-idmsix-installing-the-msix-package"></a><span data-ttu-id="59ce7-136"><a id="msix" />安裝 MSIX 套件</span><span class="sxs-lookup"><span data-stu-id="59ce7-136"><a id="msix" />Installing the MSIX package</span></span>

<span data-ttu-id="59ce7-137">若要手動在 Windows 10 用戶端上安裝 MSIX 套件，請從我們的 GitHub [發行][releases] 頁面下載 MSIX 套件。</span><span class="sxs-lookup"><span data-stu-id="59ce7-137">To manually install the MSIX package on a Windows 10 client, download the MSIX package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="59ce7-138">向下捲動至想安裝版本的 [資產]  區段。</span><span class="sxs-lookup"><span data-stu-id="59ce7-138">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="59ce7-139">[資產] 區段可能會摺疊，因此您可能需要按一下以展開它。</span><span class="sxs-lookup"><span data-stu-id="59ce7-139">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="59ce7-140">MSIX 檔案看起來像這樣 - `PowerShell-<version>-win-<os-arch>.msix`</span><span class="sxs-lookup"><span data-stu-id="59ce7-140">The MSIX file looks like this - `PowerShell-<version>-win-<os-arch>.msix`</span></span>

<span data-ttu-id="59ce7-141">因為此套件必須使用非虛擬化資源，所以無法在下載之後，直接按兩下安裝程式進行安裝。</span><span class="sxs-lookup"><span data-stu-id="59ce7-141">Once downloaded, you cannot simply double-click on the installer as this package requires use of un-virtualized resources.</span></span>  <span data-ttu-id="59ce7-142">若要安裝，必須使用 `Add-AppxPackage` Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="59ce7-142">To install, you must use the `Add-AppxPackage` cmdlet:</span></span>

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

## <a name="a-idzip-installing-the-zip-package"></a><span data-ttu-id="59ce7-143"><a id="zip" />安裝 ZIP 套件</span><span class="sxs-lookup"><span data-stu-id="59ce7-143"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="59ce7-144">有 PowerShell 二進位 ZIP 封存，以啟用進階的部署案例。</span><span class="sxs-lookup"><span data-stu-id="59ce7-144">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="59ce7-145">請注意，當使用 ZIP 封存時，不會像 MSI 套件一樣檢查必要條件。</span><span class="sxs-lookup"><span data-stu-id="59ce7-145">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span> <span data-ttu-id="59ce7-146">若要使遠端功能能透過 WSMan 正常運作，請確定您已符合[必要條件](#prerequisites)。</span><span class="sxs-lookup"><span data-stu-id="59ce7-146">For remoting over WSMan to work properly, ensure that you have met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="59ce7-147">在 Windows IoT 上部署</span><span class="sxs-lookup"><span data-stu-id="59ce7-147">Deploying on Windows IoT</span></span>

<span data-ttu-id="59ce7-148">Windows IoT 已經隨附 Windows PowerShell，我們可以將其用來部署 PowerShell 7。</span><span class="sxs-lookup"><span data-stu-id="59ce7-148">Windows IoT already comes with Windows PowerShell which we can use to deploy PowerShell 7.</span></span>

1. <span data-ttu-id="59ce7-149">針對目標裝置建立 `PSSession`</span><span class="sxs-lookup"><span data-stu-id="59ce7-149">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="59ce7-150">將 ZIP 套件複製到裝置</span><span class="sxs-lookup"><span data-stu-id="59ce7-150">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="59ce7-151">連接到裝置並展開封存</span><span class="sxs-lookup"><span data-stu-id="59ce7-151">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="59ce7-152">設定 PowerShell 7 的遠端處理</span><span class="sxs-lookup"><span data-stu-id="59ce7-152">Setup remoting to PowerShell 7</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="59ce7-153">連線到裝置上的 PowerShell 7 端點</span><span class="sxs-lookup"><span data-stu-id="59ce7-153">Connect to PowerShell 7 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="59ce7-154">在 Nano Server 上部署</span><span class="sxs-lookup"><span data-stu-id="59ce7-154">Deploying on Nano Server</span></span>

<span data-ttu-id="59ce7-155">這些指示假設某個 PowerShell 版本已在 Nano Server 映像中執行，而且此映像是由 [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server) 產生。</span><span class="sxs-lookup"><span data-stu-id="59ce7-155">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="59ce7-156">Nano Server 是一種「無周邊」作業系統。</span><span class="sxs-lookup"><span data-stu-id="59ce7-156">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="59ce7-157">目前可以使用兩種方法來部署 PowerShell 二進位檔。</span><span class="sxs-lookup"><span data-stu-id="59ce7-157">PowerShell binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="59ce7-158">離線 - 掛接 Nano Server VHD，並將 ZIP 檔案內容解壓縮至您在掛接映像中選擇的位置。</span><span class="sxs-lookup"><span data-stu-id="59ce7-158">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="59ce7-159">線上 - 透過 PowerShell 工作階段傳輸 ZIP 檔案，並將它解壓縮至您選擇的位置。</span><span class="sxs-lookup"><span data-stu-id="59ce7-159">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="59ce7-160">這兩種情況都需要 Windows 10 x64 ZIP 版套件，還需要在「系統管理員」PowerShell 執行個體中執行命令。</span><span class="sxs-lookup"><span data-stu-id="59ce7-160">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell"></a><span data-ttu-id="59ce7-161">PowerShell 的離線部署</span><span class="sxs-lookup"><span data-stu-id="59ce7-161">Offline Deployment of PowerShell</span></span>

1. <span data-ttu-id="59ce7-162">使用您最愛的 ZIP 公用程式將套件解壓縮至已掛接 Nano Server 映像的目錄。</span><span class="sxs-lookup"><span data-stu-id="59ce7-162">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="59ce7-163">取消掛接映像和開機映像。</span><span class="sxs-lookup"><span data-stu-id="59ce7-163">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="59ce7-164">連線到 Windows PowerShell 的收件匣執行個體。</span><span class="sxs-lookup"><span data-stu-id="59ce7-164">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="59ce7-165">請遵循下列指示來建立使用[另一個執行個體技術](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)的遠端端點。</span><span class="sxs-lookup"><span data-stu-id="59ce7-165">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell"></a><span data-ttu-id="59ce7-166">PowerShell 的線上部署</span><span class="sxs-lookup"><span data-stu-id="59ce7-166">Online Deployment of PowerShell</span></span>

<span data-ttu-id="59ce7-167">下列步驟會引導您將 PowerShell 部署到正在執行的 Nano Server 執行個體，並完成其遠端端點的設定。</span><span class="sxs-lookup"><span data-stu-id="59ce7-167">The following steps guide you through the deployment of PowerShell to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="59ce7-168">連線到 Windows PowerShell 的收件匣執行個體</span><span class="sxs-lookup"><span data-stu-id="59ce7-168">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="59ce7-169">將檔案複製到 Nano Server 執行個體</span><span class="sxs-lookup"><span data-stu-id="59ce7-169">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="59ce7-170">輸入工作階段</span><span class="sxs-lookup"><span data-stu-id="59ce7-170">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="59ce7-171">壓縮檔 ZIP 檔案</span><span class="sxs-lookup"><span data-stu-id="59ce7-171">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShell_<version>"
  ```

- <span data-ttu-id="59ce7-172">如需 WSMan 型的遠端功能，請遵循下列指示來建立使用[另一個執行個體技術](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)的遠端端點。</span><span class="sxs-lookup"><span data-stu-id="59ce7-172">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="59ce7-173">安裝為 .NET 全域工具</span><span class="sxs-lookup"><span data-stu-id="59ce7-173">Install as a .NET Global tool</span></span>

<span data-ttu-id="59ce7-174">如果您已安裝 [.NET Core SDK](/dotnet/core/sdk)，就可以輕鬆地將 PowerShell 安裝為 [.NET 全域工具](/dotnet/core/tools/global-tools)。</span><span class="sxs-lookup"><span data-stu-id="59ce7-174">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="59ce7-175">如何建立遠端端點</span><span class="sxs-lookup"><span data-stu-id="59ce7-175">How to create a remoting endpoint</span></span>

<span data-ttu-id="59ce7-176">PowerShell 支援透過 WSMan 與 SSH 的 PowerShell 遠端通訊協定 (PSRP)。</span><span class="sxs-lookup"><span data-stu-id="59ce7-176">PowerShell supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="59ce7-177">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="59ce7-177">For more information, see:</span></span>

- <span data-ttu-id="59ce7-178">[PowerShell Core 中的 SSH 遠端功能][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="59ce7-178">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="59ce7-179">[PowerShell Core 中的 WSMan 遠端功能][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="59ce7-179">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
