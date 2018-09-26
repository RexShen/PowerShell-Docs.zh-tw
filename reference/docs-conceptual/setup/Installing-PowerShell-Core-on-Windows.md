---
title: 在 Windows 上安裝 PowerShell Core
description: 在 Windows 上安裝 PowerShell Core 的相關資訊
ms.date: 08/06/2018
ms.openlocfilehash: 595f12efd060406264a1a4efb9d54035da06ffe3
ms.sourcegitcommit: b235c58b34d23317076540631f5cf83f1f309c0d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45557173"
---
# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="dd9e9-103">在 Windows 上安裝 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="dd9e9-103">Installing PowerShell Core on Windows</span></span>

## <a name="msi"></a><span data-ttu-id="dd9e9-104">MSI</span><span class="sxs-lookup"><span data-stu-id="dd9e9-104">MSI</span></span>

<span data-ttu-id="dd9e9-105">若要在 Windows 用戶端或 Windows Server 上安裝 PowerShell (適用於 Windows 7 SP1、Server 2008 R2 和更新版本)，請從我們的 GitHub [版本][]頁面下載 MSI 套件。</span><span class="sxs-lookup"><span data-stu-id="dd9e9-105">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span>

<span data-ttu-id="dd9e9-106">MSI 檔案看起來像這樣 - `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well --></span><span class="sxs-lookup"><span data-stu-id="dd9e9-106">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well --></span></span>

<span data-ttu-id="dd9e9-107">下載後，按兩下安裝程式，並依提示操作。</span><span class="sxs-lookup"><span data-stu-id="dd9e9-107">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="dd9e9-108">安裝時會在 [開始] 功能表中放置捷徑。</span><span class="sxs-lookup"><span data-stu-id="dd9e9-108">There is a shortcut placed in the Start Menu upon installation.</span></span>

- <span data-ttu-id="dd9e9-109">套件預設安裝在 `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="dd9e9-109">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="dd9e9-110">您可以透過 [開始] 功能表或 `$env:ProgramFiles\PowerShell\<version>\pwsh.exe` 啟動 PowerShell</span><span class="sxs-lookup"><span data-stu-id="dd9e9-110">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="prerequisites"></a><span data-ttu-id="dd9e9-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="dd9e9-111">Prerequisites</span></span>

<span data-ttu-id="dd9e9-112">若要透過 WSMan 啟用 PowerShell 遠端執行功能，必須符合下列必要條件：</span><span class="sxs-lookup"><span data-stu-id="dd9e9-112">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="dd9e9-113">在 Windows 10 以下的 Windows 版本中安裝[通用 C 執行階段](https://www.microsoft.com/download/details.aspx?id=50410)。</span><span class="sxs-lookup"><span data-stu-id="dd9e9-113">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span>
  <span data-ttu-id="dd9e9-114">透過直接下載或 Windows Update 即可取得。</span><span class="sxs-lookup"><span data-stu-id="dd9e9-114">It is available via direct download or Windows Update.</span></span>
  <span data-ttu-id="dd9e9-115">完整修補 (包括選擇性的套件) 的受支援系統已安裝此項目。</span><span class="sxs-lookup"><span data-stu-id="dd9e9-115">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="dd9e9-116">在 Windows 7 和 Windows Server 2008 R2 上安裝 Windows Management Framework (WMF) 4.0 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="dd9e9-116">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="zip"></a><span data-ttu-id="dd9e9-117">ZIP</span><span class="sxs-lookup"><span data-stu-id="dd9e9-117">ZIP</span></span>

<span data-ttu-id="dd9e9-118">有 PowerShell 二進位 ZIP 封存，以啟用進階的部署案例。</span><span class="sxs-lookup"><span data-stu-id="dd9e9-118">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span>
<span data-ttu-id="dd9e9-119">請注意，當使用 ZIP 封存時，不會像 MSI 套件一樣檢查必要條件。</span><span class="sxs-lookup"><span data-stu-id="dd9e9-119">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span>
<span data-ttu-id="dd9e9-120">因此，為讓透過 WSMan 進行的遠端功能能在 Windows 10 以下的 Windows 版本上正常運作，請務必符合[必要條件](#prerequisites)。</span><span class="sxs-lookup"><span data-stu-id="dd9e9-120">So in order for remoting over WSMan to work properly on Windows versions prior to Windows 10, you need to make sure the [prerequisites](#prerequisites) are met.</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="dd9e9-121">在 Windows IoT 上部署</span><span class="sxs-lookup"><span data-stu-id="dd9e9-121">Deploying on Windows IoT</span></span>

<span data-ttu-id="dd9e9-122">Windows IoT 附帶提供 Windows PowerShell， 我們就是用它來部署 PowerShell Core 6。</span><span class="sxs-lookup"><span data-stu-id="dd9e9-122">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="dd9e9-123">針對目標裝置建立 `PSSession`</span><span class="sxs-lookup"><span data-stu-id="dd9e9-123">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="dd9e9-124">將 ZIP 套件複製到裝置</span><span class="sxs-lookup"><span data-stu-id="dd9e9-124">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-6.1.0-win-arm32.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="dd9e9-125">連接到裝置並展開封存</span><span class="sxs-lookup"><span data-stu-id="dd9e9-125">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   cd u:\users\administrator\downloads
   Expand-Archive .\PowerShell-6.1.0-win-arm32.zip
   ```

4. <span data-ttu-id="dd9e9-126">設定 PowerShell Core 6 的遠端處理</span><span class="sxs-lookup"><span data-stu-id="dd9e9-126">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   cd .\PowerShell-6.1.0-win-arm32
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="dd9e9-127">連接到裝置上的 PowerShell 核心 6 端點</span><span class="sxs-lookup"><span data-stu-id="dd9e9-127">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.6.1.0
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="dd9e9-128">在 Nano Server 上部署</span><span class="sxs-lookup"><span data-stu-id="dd9e9-128">Deploying on Nano Server</span></span>

<span data-ttu-id="dd9e9-129">這些指示假設某個 PowerShell 版本已在 Nano Server 映像中執行，而且此映像是由 [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server) 產生。</span><span class="sxs-lookup"><span data-stu-id="dd9e9-129">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="dd9e9-130">Nano Server 是一種「無周邊」作業系統。</span><span class="sxs-lookup"><span data-stu-id="dd9e9-130">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="dd9e9-131">目前有兩種方法可以部署核心二進位檔。</span><span class="sxs-lookup"><span data-stu-id="dd9e9-131">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="dd9e9-132">離線 - 掛接 Nano Server VHD，並將 ZIP 檔案內容解壓縮至您在掛接映像中選擇的位置。</span><span class="sxs-lookup"><span data-stu-id="dd9e9-132">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="dd9e9-133">線上 - 透過 PowerShell 工作階段傳輸 ZIP 檔案，並將它解壓縮至您選擇的位置。</span><span class="sxs-lookup"><span data-stu-id="dd9e9-133">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="dd9e9-134">這兩種情況都需要 Windows 10 x64 ZIP 版套件，還需要在「系統管理員」PowerShell 執行個體中執行命令。</span><span class="sxs-lookup"><span data-stu-id="dd9e9-134">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="dd9e9-135">PowerShell Core 的離線部署</span><span class="sxs-lookup"><span data-stu-id="dd9e9-135">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="dd9e9-136">使用您最愛的 ZIP 公用程式將套件解壓縮至已掛接 Nano Server 映像的目錄。</span><span class="sxs-lookup"><span data-stu-id="dd9e9-136">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="dd9e9-137">取消掛接映像和開機映像。</span><span class="sxs-lookup"><span data-stu-id="dd9e9-137">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="dd9e9-138">連線到 Windows PowerShell 的收件匣執行個體。</span><span class="sxs-lookup"><span data-stu-id="dd9e9-138">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="dd9e9-139">請遵循下列指示來建立使用[另一個執行個體技術](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)的遠端端點。</span><span class="sxs-lookup"><span data-stu-id="dd9e9-139">Follow the instructions to create a remoting endpoint using the ["another instance technique"](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="dd9e9-140">PowerShell Core 的線上部署</span><span class="sxs-lookup"><span data-stu-id="dd9e9-140">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="dd9e9-141">下列步驟會引導您從部署 PowerShell Core 到執行 Nano Server 執行個體及其遠端端點的設定。</span><span class="sxs-lookup"><span data-stu-id="dd9e9-141">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="dd9e9-142">連線到 Windows PowerShell 的收件匣執行個體</span><span class="sxs-lookup"><span data-stu-id="dd9e9-142">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="dd9e9-143">將檔案複製到 Nano Server 執行個體</span><span class="sxs-lookup"><span data-stu-id="dd9e9-143">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="dd9e9-144">輸入工作階段</span><span class="sxs-lookup"><span data-stu-id="dd9e9-144">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="dd9e9-145">壓縮檔 ZIP 檔案</span><span class="sxs-lookup"><span data-stu-id="dd9e9-145">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="dd9e9-146">如需 WSMan 型的遠端功能，請遵循下列指示來建立使用[另一個執行個體技術](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)的遠端端點。</span><span class="sxs-lookup"><span data-stu-id="dd9e9-146">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="dd9e9-147">建立遠端端點的指示</span><span class="sxs-lookup"><span data-stu-id="dd9e9-147">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="dd9e9-148">PowerShell Core 支援 WSMan 和 SSH 上的 PowerShell 遠端通訊協定 (PSRP)。</span><span class="sxs-lookup"><span data-stu-id="dd9e9-148">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span>
<span data-ttu-id="dd9e9-149">如需詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="dd9e9-149">For more information, see:</span></span>

- <span data-ttu-id="dd9e9-150">[PowerShell Core 中的 SSH 遠端功能][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="dd9e9-150">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="dd9e9-151">[PowerShell Core 中的 WSMan 遠端功能][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="dd9e9-151">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="artifact-installation-instructions"></a><span data-ttu-id="dd9e9-152">成品安裝指示</span><span class="sxs-lookup"><span data-stu-id="dd9e9-152">Artifact Installation Instructions</span></span>

<span data-ttu-id="dd9e9-153">我們在每個以 [AppVeyor][] 建置的 CI 上發行具有 CoreCLR 位元的封存。</span><span class="sxs-lookup"><span data-stu-id="dd9e9-153">We publish an archive with CoreCLR bits on every CI build with [AppVeyor][].</span></span>

<span data-ttu-id="dd9e9-154">若要從 CoreCLR 成品安裝 PowerShell Core：</span><span class="sxs-lookup"><span data-stu-id="dd9e9-154">To install PowerShell Core from the CoreCLR Artifact:</span></span>

1. <span data-ttu-id="dd9e9-155">從特定組建的 [成品] 索引標籤下載 ZIP 套件。</span><span class="sxs-lookup"><span data-stu-id="dd9e9-155">Download ZIP package from **artifacts** tab of the particular build.</span></span>
2. <span data-ttu-id="dd9e9-156">解除封鎖 ZIP 檔案：以滑鼠右鍵按一下檔案總管 -> [屬性] -> 核取 [解除封鎖] 方塊 -> [套用]</span><span class="sxs-lookup"><span data-stu-id="dd9e9-156">Unblock ZIP file: right-click in File Explorer -> Properties -> check 'Unblock' box -> apply</span></span>
3. <span data-ttu-id="dd9e9-157">將 ZIP 檔案解壓縮至 `bin` 目錄</span><span class="sxs-lookup"><span data-stu-id="dd9e9-157">Extract zip file to `bin` directory</span></span>
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO -->

[版本]: https://github.com/PowerShell/PowerShell/releases
[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
