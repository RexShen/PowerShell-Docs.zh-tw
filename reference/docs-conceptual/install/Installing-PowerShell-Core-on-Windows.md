---
title: 在 Windows 上安裝 PowerShell Core
description: 在 Windows 上安裝 PowerShell Core 的相關資訊
ms.date: 08/06/2018
ms.openlocfilehash: 3f21761037311891162f1083234edb0aca80d28b
ms.sourcegitcommit: 4ec9e10647b752cc62b1eabb897ada3dc03c93eb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66830234"
---
# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="31e92-103">在 Windows 上安裝 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="31e92-103">Installing PowerShell Core on Windows</span></span>

<span data-ttu-id="31e92-104">有多種方法可以在 Windows 中安裝 PowerShell Core。</span><span class="sxs-lookup"><span data-stu-id="31e92-104">There are multiple ways to install PowerShell Core in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="31e92-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="31e92-105">Prerequisites</span></span>

<span data-ttu-id="31e92-106">若要透過 WSMan 啟用 PowerShell 遠端執行功能，必須符合下列必要條件：</span><span class="sxs-lookup"><span data-stu-id="31e92-106">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="31e92-107">在 Windows 10 以下的 Windows 版本中安裝[通用 C 執行階段](https://www.microsoft.com/download/details.aspx?id=50410)。</span><span class="sxs-lookup"><span data-stu-id="31e92-107">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span> <span data-ttu-id="31e92-108">透過直接下載或 Windows Update 即可取得。</span><span class="sxs-lookup"><span data-stu-id="31e92-108">It is available via direct download or Windows Update.</span></span> <span data-ttu-id="31e92-109">完整修補 (包括選擇性的套件) 的受支援系統已安裝此項目。</span><span class="sxs-lookup"><span data-stu-id="31e92-109">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="31e92-110">在 Windows 7 和 Windows Server 2008 R2 上安裝 Windows Management Framework (WMF) 4.0 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="31e92-110">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="31e92-111">如需 WMF 的詳細資訊，請參閱 [WMF 概觀](/powershell/wmf/overview)。</span><span class="sxs-lookup"><span data-stu-id="31e92-111">For more information about WMF, see [WMF Overview](/powershell/wmf/overview).</span></span>

## <a name="a-idmsi-installing-the-msi-package"></a><span data-ttu-id="31e92-112"><a id="msi" />安裝 MSI 套件</span><span class="sxs-lookup"><span data-stu-id="31e92-112"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="31e92-113">若要在 Windows 用戶端或 Windows Server 上安裝 PowerShell (適用於 Windows 7 SP1、Server 2008 R2 和更新版本)，請從我們的 GitHub [版本][releases]頁面下載 MSI 套件。</span><span class="sxs-lookup"><span data-stu-id="31e92-113">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="31e92-114">向下捲動至想安裝版本的 [資產]  區段。</span><span class="sxs-lookup"><span data-stu-id="31e92-114">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="31e92-115">[資產] 區段可能會摺疊，因此您可能需要按一下以展開它。</span><span class="sxs-lookup"><span data-stu-id="31e92-115">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="31e92-116">MSI 檔案看起來像這樣 - `PowerShell-<version>-win-<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="31e92-116">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="31e92-117">下載後，按兩下安裝程式，並依提示操作。</span><span class="sxs-lookup"><span data-stu-id="31e92-117">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="31e92-118">安裝程式會在 Windows [開始] 功能表中建立捷徑。</span><span class="sxs-lookup"><span data-stu-id="31e92-118">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="31e92-119">套件預設安裝在 `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="31e92-119">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="31e92-120">您可以透過 [開始] 功能表或 `$env:ProgramFiles\PowerShell\<version>\pwsh.exe` 啟動 PowerShell</span><span class="sxs-lookup"><span data-stu-id="31e92-120">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="31e92-121">從命令列進行系統管理安裝</span><span class="sxs-lookup"><span data-stu-id="31e92-121">Administrative install from the command line</span></span>

<span data-ttu-id="31e92-122">可以從命令列安裝 MSI 套件。</span><span class="sxs-lookup"><span data-stu-id="31e92-122">MSI packages can be installed from the command line.</span></span> <span data-ttu-id="31e92-123">這允許系統管理員無需使用者互動即可部署套件。</span><span class="sxs-lookup"><span data-stu-id="31e92-123">This allows administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="31e92-124">適用於 PowerShell 的 MSI 套件包含下列屬性以控制安裝選項：</span><span class="sxs-lookup"><span data-stu-id="31e92-124">The MSI package for PowerShell includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="31e92-125">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - 此屬性控制將 [開啟 PowerShell]  項目新增至 Windows 檔案總管中的內容功能表的選項。</span><span class="sxs-lookup"><span data-stu-id="31e92-125">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="31e92-126">**ENABLE_PSREMOTING** - 此屬性控制在安裝期間啟用 PowerShell 遠端執行功能的選項。</span><span class="sxs-lookup"><span data-stu-id="31e92-126">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="31e92-127">**REGISTER_MANIFEST** - 此屬性控制用於註冊 Windows 事件記錄資訊清單的選項。</span><span class="sxs-lookup"><span data-stu-id="31e92-127">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="31e92-128">下列範例示範如何在啟用所有安裝選項的情況下，以無訊息方式安裝 PowerShell Core。</span><span class="sxs-lookup"><span data-stu-id="31e92-128">The following examples shows how to silently install PowerShell Core with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="31e92-129">如需 Msiexec.exe 的命令列選項完整清單，請參閱[命令列選項](/windows/desktop/Msi/command-line-options)。</span><span class="sxs-lookup"><span data-stu-id="31e92-129">For a full list of command line options for Msiexec.exe, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="a-idzip-installing-the-zip-package"></a><span data-ttu-id="31e92-130"><a id="zip" />安裝 ZIP 套件</span><span class="sxs-lookup"><span data-stu-id="31e92-130"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="31e92-131">有 PowerShell 二進位 ZIP 封存，以啟用進階的部署案例。</span><span class="sxs-lookup"><span data-stu-id="31e92-131">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="31e92-132">請注意，當使用 ZIP 封存時，不會像 MSI 套件一樣檢查必要條件。</span><span class="sxs-lookup"><span data-stu-id="31e92-132">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span> <span data-ttu-id="31e92-133">若要使遠端功能能透過 WSMan 正常運作，請確定您已符合[必要條件](#prerequisites)。</span><span class="sxs-lookup"><span data-stu-id="31e92-133">For remoting over WSMan to work properly, ensure that you have met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="31e92-134">在 Windows IoT 上部署</span><span class="sxs-lookup"><span data-stu-id="31e92-134">Deploying on Windows IoT</span></span>

<span data-ttu-id="31e92-135">Windows IoT 附帶提供 Windows PowerShell， 我們就是用它來部署 PowerShell Core 6。</span><span class="sxs-lookup"><span data-stu-id="31e92-135">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="31e92-136">針對目標裝置建立 `PSSession`</span><span class="sxs-lookup"><span data-stu-id="31e92-136">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="31e92-137">將 ZIP 套件複製到裝置</span><span class="sxs-lookup"><span data-stu-id="31e92-137">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="31e92-138">連接到裝置並展開封存</span><span class="sxs-lookup"><span data-stu-id="31e92-138">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="31e92-139">設定 PowerShell Core 6 的遠端處理</span><span class="sxs-lookup"><span data-stu-id="31e92-139">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="31e92-140">連接到裝置上的 PowerShell 核心 6 端點</span><span class="sxs-lookup"><span data-stu-id="31e92-140">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="31e92-141">在 Nano Server 上部署</span><span class="sxs-lookup"><span data-stu-id="31e92-141">Deploying on Nano Server</span></span>

<span data-ttu-id="31e92-142">這些指示假設某個 PowerShell 版本已在 Nano Server 映像中執行，而且此映像是由 [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server) 產生。</span><span class="sxs-lookup"><span data-stu-id="31e92-142">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="31e92-143">Nano Server 是一種「無周邊」作業系統。</span><span class="sxs-lookup"><span data-stu-id="31e92-143">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="31e92-144">目前有兩種方法可以部署核心二進位檔。</span><span class="sxs-lookup"><span data-stu-id="31e92-144">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="31e92-145">離線 - 掛接 Nano Server VHD，並將 ZIP 檔案內容解壓縮至您在掛接映像中選擇的位置。</span><span class="sxs-lookup"><span data-stu-id="31e92-145">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="31e92-146">線上 - 透過 PowerShell 工作階段傳輸 ZIP 檔案，並將它解壓縮至您選擇的位置。</span><span class="sxs-lookup"><span data-stu-id="31e92-146">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="31e92-147">這兩種情況都需要 Windows 10 x64 ZIP 版套件，還需要在「系統管理員」PowerShell 執行個體中執行命令。</span><span class="sxs-lookup"><span data-stu-id="31e92-147">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="31e92-148">PowerShell Core 的離線部署</span><span class="sxs-lookup"><span data-stu-id="31e92-148">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="31e92-149">使用您最愛的 ZIP 公用程式將套件解壓縮至已掛接 Nano Server 映像的目錄。</span><span class="sxs-lookup"><span data-stu-id="31e92-149">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="31e92-150">取消掛接映像和開機映像。</span><span class="sxs-lookup"><span data-stu-id="31e92-150">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="31e92-151">連線到 Windows PowerShell 的收件匣執行個體。</span><span class="sxs-lookup"><span data-stu-id="31e92-151">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="31e92-152">請遵循下列指示來建立使用[另一個執行個體技術](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)的遠端端點。</span><span class="sxs-lookup"><span data-stu-id="31e92-152">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="31e92-153">PowerShell Core 的線上部署</span><span class="sxs-lookup"><span data-stu-id="31e92-153">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="31e92-154">下列步驟會引導您從部署 PowerShell Core 到執行 Nano Server 執行個體及其遠端端點的設定。</span><span class="sxs-lookup"><span data-stu-id="31e92-154">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="31e92-155">連線到 Windows PowerShell 的收件匣執行個體</span><span class="sxs-lookup"><span data-stu-id="31e92-155">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="31e92-156">將檔案複製到 Nano Server 執行個體</span><span class="sxs-lookup"><span data-stu-id="31e92-156">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="31e92-157">輸入工作階段</span><span class="sxs-lookup"><span data-stu-id="31e92-157">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="31e92-158">壓縮檔 ZIP 檔案</span><span class="sxs-lookup"><span data-stu-id="31e92-158">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="31e92-159">如需 WSMan 型的遠端功能，請遵循下列指示來建立使用[另一個執行個體技術](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)的遠端端點。</span><span class="sxs-lookup"><span data-stu-id="31e92-159">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="31e92-160">如何建立遠端端點</span><span class="sxs-lookup"><span data-stu-id="31e92-160">How to create a remoting endpoint</span></span>

<span data-ttu-id="31e92-161">PowerShell Core 支援 WSMan 和 SSH 上的 PowerShell 遠端通訊協定 (PSRP)。</span><span class="sxs-lookup"><span data-stu-id="31e92-161">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="31e92-162">如需詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="31e92-162">For more information, see:</span></span>

- <span data-ttu-id="31e92-163">[PowerShell Core 中的 SSH 遠端功能][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="31e92-163">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="31e92-164">[PowerShell Core 中的 WSMan 遠端功能][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="31e92-164">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
