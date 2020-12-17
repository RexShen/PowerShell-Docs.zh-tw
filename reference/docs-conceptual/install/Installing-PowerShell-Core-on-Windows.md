---
title: 在 Windows 上安裝 PowerShell
description: 在 Windows 上安裝 PowerShell 的相關資訊
ms.date: 11/11/2020
ms.openlocfilehash: 039db904a315bd3ad3f4e1358d414c98c3a84be5
ms.sourcegitcommit: 7f712e12ec5b3f3f3e695da804b050ea0ce58b3a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94661421"
---
# <a name="installing-powershell-on-windows"></a><span data-ttu-id="ad168-103">在 Windows 上安裝 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ad168-103">Installing PowerShell on Windows</span></span>

<span data-ttu-id="ad168-104">有多種方法可以在 Windows 中安裝 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="ad168-104">There are multiple ways to install PowerShell in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ad168-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="ad168-105">Prerequisites</span></span>

<span data-ttu-id="ad168-106">在 Windows 7 SP1、Server 2008 R2 和更新版本上支援 PowerShell 的最新版本。</span><span class="sxs-lookup"><span data-stu-id="ad168-106">The latest release of PowerShell is supported on Windows 7 SP1, Server 2008 R2, and later versions.</span></span>

<span data-ttu-id="ad168-107">若要透過 WSMan 啟用 PowerShell 遠端執行功能，必須符合下列必要條件：</span><span class="sxs-lookup"><span data-stu-id="ad168-107">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="ad168-108">在 Windows 10 以前的 Windows 版本中安裝[通用 C 執行階段](https://www.microsoft.com/download/details.aspx?id=50410)。</span><span class="sxs-lookup"><span data-stu-id="ad168-108">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions predating Windows 10.</span></span> <span data-ttu-id="ad168-109">透過直接下載或 Windows Update 即可取得。</span><span class="sxs-lookup"><span data-stu-id="ad168-109">It's available via direct download or Windows Update.</span></span> <span data-ttu-id="ad168-110">已完整修補的系統已安裝此套件。</span><span class="sxs-lookup"><span data-stu-id="ad168-110">Fully patched systems already have this package installed.</span></span>
- <span data-ttu-id="ad168-111">在 Windows 7 和 Windows Server 2008 R2 上安裝 Windows Management Framework (WMF) 4.0 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="ad168-111">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="ad168-112">如需 WMF 的詳細資訊，請參閱 [WMF 概觀](/powershell/scripting/wmf/overview)。</span><span class="sxs-lookup"><span data-stu-id="ad168-112">For more information about WMF, see [WMF Overview](/powershell/scripting/wmf/overview).</span></span>

## <a name="download-the-installer-package"></a><span data-ttu-id="ad168-113">下載安裝程式套件</span><span class="sxs-lookup"><span data-stu-id="ad168-113">Download the installer package</span></span>

<span data-ttu-id="ad168-114">若要在 Windows 上安裝 PowerShell，請從 GitHub 下載[最新的][]安裝套件。</span><span class="sxs-lookup"><span data-stu-id="ad168-114">To install PowerShell on Windows, download the [latest][] install package from GitHub.</span></span> <span data-ttu-id="ad168-115">您也可以在[版本][]頁面上找到最新的預覽版本。</span><span class="sxs-lookup"><span data-stu-id="ad168-115">You can also find the latest preview version on the [releases][] page.</span></span> <span data-ttu-id="ad168-116">向下捲動至 [版本] 頁面的 [資產]  區段。</span><span class="sxs-lookup"><span data-stu-id="ad168-116">Scroll down to the **Assets** section of the Release page.</span></span> <span data-ttu-id="ad168-117">[資產]  區段可能會摺疊，因此您可能需要按一下加以展開。</span><span class="sxs-lookup"><span data-stu-id="ad168-117">The **Assets** section may be collapsed, so you may need to click to expand it.</span></span>

## <a name="installing-the-msi-package"></a><span data-ttu-id="ad168-118"><a id="msi" />安裝 MSI 套件</span><span class="sxs-lookup"><span data-stu-id="ad168-118"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="ad168-119">MSI 檔案看起來像 `PowerShell-<version>-win-<os-arch>.msi`。</span><span class="sxs-lookup"><span data-stu-id="ad168-119">The MSI file looks like `PowerShell-<version>-win-<os-arch>.msi`.</span></span> <span data-ttu-id="ad168-120">例如：</span><span class="sxs-lookup"><span data-stu-id="ad168-120">For example:</span></span>

- `PowerShell-7.1.0-win-x64.msi`
- `PowerShell-7.1.0-win-x86.msi`

<span data-ttu-id="ad168-121">下載後，按兩下安裝程式，並依提示操作。</span><span class="sxs-lookup"><span data-stu-id="ad168-121">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="ad168-122">安裝程式會在 Windows [開始] 功能表中建立捷徑。</span><span class="sxs-lookup"><span data-stu-id="ad168-122">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="ad168-123">套件預設安裝在 `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="ad168-123">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="ad168-124">您可以透過 [開始] 功能表或 `$env:ProgramFiles\PowerShell\<version>\pwsh.exe` 啟動 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ad168-124">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

> [!NOTE]
> <span data-ttu-id="ad168-125">PowerShell 7.1 會安裝到新目錄，並與 Windows PowerShell 5.1 並存執行。</span><span class="sxs-lookup"><span data-stu-id="ad168-125">PowerShell 7.1 installs to a new directory and runs side-by-side with Windows PowerShell 5.1.</span></span>
> <span data-ttu-id="ad168-126">PowerShell 7.1 是會取代 PowerShell 6.x</span><span class="sxs-lookup"><span data-stu-id="ad168-126">PowerShell 7.1 is an in-place upgrade that replaces PowerShell 6.x.</span></span> <span data-ttu-id="ad168-127">或 PowerShell 7.0 的就地升級。</span><span class="sxs-lookup"><span data-stu-id="ad168-127">or PowerShell 7.0.</span></span>
>
> - <span data-ttu-id="ad168-128">PowerShell 7.1 會安裝到 `$env:ProgramFiles\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="ad168-128">PowerShell 7.1 is installed to `$env:ProgramFiles\PowerShell\7`</span></span>
> - <span data-ttu-id="ad168-129">系統會在 `$env:PATH` 中新增 `$env:ProgramFiles\PowerShell\7` 資料夾</span><span class="sxs-lookup"><span data-stu-id="ad168-129">The `$env:ProgramFiles\PowerShell\7` folder is added to `$env:PATH`</span></span>
> - <span data-ttu-id="ad168-130">系統會刪除 `$env:ProgramFiles\PowerShell\6` 資料夾</span><span class="sxs-lookup"><span data-stu-id="ad168-130">The `$env:ProgramFiles\PowerShell\6` folder is deleted</span></span>
>
> <span data-ttu-id="ad168-131">如果您需要與其他版本並存執行 PowerShell 7.1，請使用 [ZIP 安裝](#zip)方法來將其他版本安裝到不同的資料夾。</span><span class="sxs-lookup"><span data-stu-id="ad168-131">If you need to run PowerShell 7.1 side-by-side with other versions, use the [ZIP install](#zip) method to install the other version to a different folder.</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="ad168-132">從命令列進行系統管理安裝</span><span class="sxs-lookup"><span data-stu-id="ad168-132">Administrative install from the command line</span></span>

<span data-ttu-id="ad168-133">您可以從命令列安裝 MSI 套件，讓系統管理員不需要使用者互動即可部署套件。</span><span class="sxs-lookup"><span data-stu-id="ad168-133">MSI packages can be installed from the command line allowing administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="ad168-134">MSI 套件包含下列屬性以控制安裝選項：</span><span class="sxs-lookup"><span data-stu-id="ad168-134">The MSI package includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="ad168-135">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - 此屬性控制將 [開啟 PowerShell]  項目新增至 Windows 檔案總管中的內容功能表的選項。</span><span class="sxs-lookup"><span data-stu-id="ad168-135">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="ad168-136">**ENABLE_PSREMOTING** - 此屬性控制在安裝期間啟用 PowerShell 遠端執行功能的選項。</span><span class="sxs-lookup"><span data-stu-id="ad168-136">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="ad168-137">**REGISTER_MANIFEST** - 此屬性控制用於註冊 Windows 事件記錄資訊清單的選項。</span><span class="sxs-lookup"><span data-stu-id="ad168-137">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="ad168-138">下列範例示範如何在啟用所有安裝選項的情況下，以無訊息方式安裝 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="ad168-138">The following example shows how to silently install PowerShell with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-7.1.0-win-x64.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="ad168-139">如需 `Msiexec.exe` 的命令列選項完整清單，請參閱[命令列選項](/windows/desktop/Msi/command-line-options)。</span><span class="sxs-lookup"><span data-stu-id="ad168-139">For a full list of command-line options for `Msiexec.exe`, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

### <a name="registry-keys-created-during-installation"></a><span data-ttu-id="ad168-140">安裝期間建立的登錄機碼</span><span class="sxs-lookup"><span data-stu-id="ad168-140">Registry keys created during installation</span></span>

<span data-ttu-id="ad168-141">從 PowerShell 7.1 開始，MSI 套件會建立登錄機碼以儲存 PowerShell 的安裝位置與版本。</span><span class="sxs-lookup"><span data-stu-id="ad168-141">Beginning in PowerShell 7.1, the MSI package creates registry keys that store the installation location and version of PowerShell.</span></span> <span data-ttu-id="ad168-142">這些值位於 `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\<GUID>`。</span><span class="sxs-lookup"><span data-stu-id="ad168-142">These values are located in `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\<GUID>`.</span></span> <span data-ttu-id="ad168-143">針對每個組建類型 (發行版本或預覽版)、主要版本與架構，`<GUID>` 的值都不重複。</span><span class="sxs-lookup"><span data-stu-id="ad168-143">The value of `<GUID>` is unique for each build type (release or preview), major version, and architecture.</span></span>

|    <span data-ttu-id="ad168-144">版本</span><span class="sxs-lookup"><span data-stu-id="ad168-144">Release</span></span>    | <span data-ttu-id="ad168-145">架構</span><span class="sxs-lookup"><span data-stu-id="ad168-145">Architecture</span></span> |                                          <span data-ttu-id="ad168-146">登錄金鑰</span><span class="sxs-lookup"><span data-stu-id="ad168-146">Registry Key</span></span>                                           |
| ------------- | :----------: | ----------------------------------------------------------------------------------------------- |
| <span data-ttu-id="ad168-147">7.1.x 發行版本</span><span class="sxs-lookup"><span data-stu-id="ad168-147">7.1.x Release</span></span> |     <span data-ttu-id="ad168-148">x86</span><span class="sxs-lookup"><span data-stu-id="ad168-148">x86</span></span>      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\1d00683b-0f84-4db8-a64f-2f98ad42fe06` |
| <span data-ttu-id="ad168-149">7.1.x 發行版本</span><span class="sxs-lookup"><span data-stu-id="ad168-149">7.1.x Release</span></span> |     <span data-ttu-id="ad168-150">x64</span><span class="sxs-lookup"><span data-stu-id="ad168-150">x64</span></span>      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\31ab5147-9a97-4452-8443-d9709f0516e1` |
| <span data-ttu-id="ad168-151">7.1.x 預覽版</span><span class="sxs-lookup"><span data-stu-id="ad168-151">7.1.x Preview</span></span> |     <span data-ttu-id="ad168-152">x86</span><span class="sxs-lookup"><span data-stu-id="ad168-152">x86</span></span>      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\86abcfbd-1ccc-4a88-b8b2-0facfde29094` |
| <span data-ttu-id="ad168-153">7.1.x 預覽版</span><span class="sxs-lookup"><span data-stu-id="ad168-153">7.1.x Preview</span></span> |     <span data-ttu-id="ad168-154">x64</span><span class="sxs-lookup"><span data-stu-id="ad168-154">x64</span></span>      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\39243d76-adaf-42b1-94fb-16ecf83237c8` |

<span data-ttu-id="ad168-155">系統管理員與開發人員可以加以使用來尋找 PowerShell 的路徑。</span><span class="sxs-lookup"><span data-stu-id="ad168-155">This can be used by administrators and developers to find the path to PowerShell.</span></span> <span data-ttu-id="ad168-156">所有預覽版與次要發行版本的 `<GUID>` 值都相同。</span><span class="sxs-lookup"><span data-stu-id="ad168-156">The `<GUID>` values will be the same for all preview and minor version releases.</span></span> <span data-ttu-id="ad168-157">每個主要發行版本的 `<GUID>` 值都會變更。</span><span class="sxs-lookup"><span data-stu-id="ad168-157">The `<GUID>` values are changed for each major release.</span></span>

## <a name="installing-the-zip-package"></a><span data-ttu-id="ad168-158"><a id="zip" />安裝 ZIP 套件</span><span class="sxs-lookup"><span data-stu-id="ad168-158"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="ad168-159">有 PowerShell 二進位 ZIP 封存，以啟用進階的部署案例。</span><span class="sxs-lookup"><span data-stu-id="ad168-159">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="ad168-160">從[版本][版本]頁面下載下列其中一個 ZIP 封存。</span><span class="sxs-lookup"><span data-stu-id="ad168-160">Download one of the following ZIP archives from the [releases][releases] page.</span></span>

- <span data-ttu-id="ad168-161">PowerShell-7.1.0-win-x64.zip</span><span class="sxs-lookup"><span data-stu-id="ad168-161">PowerShell-7.1.0-win-x64.zip</span></span>
- <span data-ttu-id="ad168-162">PowerShell-7.1.0-win-x86.zip</span><span class="sxs-lookup"><span data-stu-id="ad168-162">PowerShell-7.1.0-win-x86.zip</span></span>
- <span data-ttu-id="ad168-163">PowerShell-7.1.0-win-arm64.zip</span><span class="sxs-lookup"><span data-stu-id="ad168-163">PowerShell-7.1.0-win-arm64.zip</span></span>
- <span data-ttu-id="ad168-164">PowerShell-7.1.0-win-arm32.zip</span><span class="sxs-lookup"><span data-stu-id="ad168-164">PowerShell-7.1.0-win-arm32.zip</span></span>

<span data-ttu-id="ad168-165">依據您下載檔案的方式，可能需要使用 `Unblock-File`Cmdlet 以將檔案解除封鎖。</span><span class="sxs-lookup"><span data-stu-id="ad168-165">Depending on how you download the file you may need to unblock the file using the `Unblock-File` cmdlet.</span></span> <span data-ttu-id="ad168-166">將內容解壓縮至您選擇的位置，並從該處執行 `pwsh.exe`。</span><span class="sxs-lookup"><span data-stu-id="ad168-166">Unzip the contents to the location of your choice and run `pwsh.exe` from there.</span></span> <span data-ttu-id="ad168-167">與安裝 MSI 套件不同，安裝 ZIP 封存不會檢查先決條件。</span><span class="sxs-lookup"><span data-stu-id="ad168-167">Unlike installing the MSI packages, installing the ZIP archive doesn't check for prerequisites.</span></span> <span data-ttu-id="ad168-168">若要使遠端功能能透過 WSMan 正常運作，請確定您已符合[必要條件](#prerequisites)。</span><span class="sxs-lookup"><span data-stu-id="ad168-168">For remoting over WSMan to work properly, ensure that you've met the [prerequisites](#prerequisites).</span></span>

<span data-ttu-id="ad168-169">使用此方法，在 Microsoft Surface Pro X 之類的電腦上安裝 ARM 型 PowerShell 版本。為獲得最佳結果，請將 PowerShell 安裝到 `$env:ProgramFiles\PowerShell\7` 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ad168-169">Use this method to install the ARM-based version of PowerShell on computers like the Microsoft Surface Pro X. For best results, install PowerShell to the to `$env:ProgramFiles\PowerShell\7` folder.</span></span>

## <a name="deploying-on-windows-10-iot-enterprise"></a><span data-ttu-id="ad168-170">在 Windows 10 IoT 企業版上部署</span><span class="sxs-lookup"><span data-stu-id="ad168-170">Deploying on Windows 10 IoT Enterprise</span></span>

<span data-ttu-id="ad168-171">Windows 10 IoT 企業版隨附 Windows PowerShell，我們可以將其用來部署 PowerShell 7。</span><span class="sxs-lookup"><span data-stu-id="ad168-171">Windows 10 IoT Enterprise comes with Windows PowerShell, which we can use to deploy PowerShell 7.</span></span>

1. <span data-ttu-id="ad168-172">針對目標裝置建立 `PSSession`</span><span class="sxs-lookup"><span data-stu-id="ad168-172">Create `PSSession` to target device</span></span>

   ```powershell
   Set-Item -Path WSMan:\localhost\Client\TrustedHosts <deviceip>
   $S = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

1. <span data-ttu-id="ad168-173">將 ZIP 套件複製到裝置</span><span class="sxs-lookup"><span data-stu-id="ad168-173">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

1. <span data-ttu-id="ad168-174">連接到裝置並展開封存</span><span class="sxs-lookup"><span data-stu-id="ad168-174">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

1. <span data-ttu-id="ad168-175">設定 PowerShell 7 的遠端功能</span><span class="sxs-lookup"><span data-stu-id="ad168-175">Set up remoting to PowerShell 7</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because
   # it has to restart WinRM
   ```

1. <span data-ttu-id="ad168-176">連線到裝置上的 PowerShell 7 端點</span><span class="sxs-lookup"><span data-stu-id="ad168-176">Connect to PowerShell 7 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter. If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-windows-10-iot-core"></a><span data-ttu-id="ad168-177">在 Windows 10 IoT 核心版上部署</span><span class="sxs-lookup"><span data-stu-id="ad168-177">Deploying on Windows 10 IoT Core</span></span>

<span data-ttu-id="ad168-178">當您包含 _IOT_POWERSHELL_ 功能 (可供我們用來部署 PowerShell 7) 時，Windows 10 IoT 核心版會新增 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="ad168-178">Windows 10 IoT Core adds Windows PowerShell when you include _IOT_POWERSHELL_ feature, which we can use to deploy PowerShell 7.</span></span> <span data-ttu-id="ad168-179">針對 Windows 10 IoT 企業版所定義的步驟也可以用於 IoT 核心版。</span><span class="sxs-lookup"><span data-stu-id="ad168-179">The steps defined above for Windows 10 IoT Enterprise can be followed for IoT Core as well.</span></span>

<span data-ttu-id="ad168-180">若要在出貨映像中新增最新的 PowerShell，請使用 [Import-PSCoreRelease][] 命令以在工作區包括套件，並將 _OPENSRC_POWERSHELL_ 功能新增到您的映像。</span><span class="sxs-lookup"><span data-stu-id="ad168-180">For adding the latest PowerShell in the shipping image, use [Import-PSCoreRelease][] command to include the package in the workarea and add _OPENSRC_POWERSHELL_ feature to your image.</span></span>

> [!NOTE]
> <span data-ttu-id="ad168-181">針對 ARM64 架構，當您包括 _IOT_POWERSHELL_ 時，不會新增 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="ad168-181">For ARM64 architecture, Windows PowerShell is not added when you include _IOT_POWERSHELL_.</span></span> <span data-ttu-id="ad168-182">因此，以 zip 為基礎的安裝將無法使用。</span><span class="sxs-lookup"><span data-stu-id="ad168-182">So the zip based install will not work.</span></span> <span data-ttu-id="ad168-183">您將必須使用 `Import-PSCoreRelease` 命令，以將其新增至映像中。</span><span class="sxs-lookup"><span data-stu-id="ad168-183">You will need to use `Import-PSCoreRelease` command to add it in the image.</span></span>

## <a name="deploying-on-nano-server"></a><span data-ttu-id="ad168-184">在 Nano Server 上部署</span><span class="sxs-lookup"><span data-stu-id="ad168-184">Deploying on Nano Server</span></span>

<span data-ttu-id="ad168-185">這些指示假設 Nano Server 是一個 PowerShell 版本已在其上執行的「無周邊」作業系統。</span><span class="sxs-lookup"><span data-stu-id="ad168-185">These instructions assume that the Nano Server is a "headless" OS that has a version of PowerShell is already running on it.</span></span> <span data-ttu-id="ad168-186">如需詳細資訊，請參閱 [Nano Server 映像建立器](/windows-server/get-started/deploy-nano-server) 文件。</span><span class="sxs-lookup"><span data-stu-id="ad168-186">For more information, see the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server) documentation.</span></span>

<span data-ttu-id="ad168-187">目前可以使用兩種方法來部署 PowerShell 二進位檔。</span><span class="sxs-lookup"><span data-stu-id="ad168-187">PowerShell binaries can be deployed using two different methods.</span></span>

1. <span data-ttu-id="ad168-188">離線 - 掛接 Nano Server VHD，並將 ZIP 檔案內容解壓縮至您在掛接映像中選擇的位置。</span><span class="sxs-lookup"><span data-stu-id="ad168-188">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
1. <span data-ttu-id="ad168-189">線上 - 透過 PowerShell 工作階段傳輸 ZIP 檔案，並將它解壓縮至您選擇的位置。</span><span class="sxs-lookup"><span data-stu-id="ad168-189">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="ad168-190">在這兩種情況下，您都需要 Windows 10 x64 ZIP 版套件。</span><span class="sxs-lookup"><span data-stu-id="ad168-190">In both cases, you need the Windows 10 x64 ZIP release package.</span></span> <span data-ttu-id="ad168-191">在 PowerShell 的「系統管理員」執行個體中執行命令。</span><span class="sxs-lookup"><span data-stu-id="ad168-191">Run the commands within an "Administrator" instance of PowerShell.</span></span>

### <a name="offline-deployment-of-powershell"></a><span data-ttu-id="ad168-192">PowerShell 的離線部署</span><span class="sxs-lookup"><span data-stu-id="ad168-192">Offline Deployment of PowerShell</span></span>

1. <span data-ttu-id="ad168-193">使用您最愛的 ZIP 公用程式將套件解壓縮至已掛接 Nano Server 映像的目錄。</span><span class="sxs-lookup"><span data-stu-id="ad168-193">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
1. <span data-ttu-id="ad168-194">取消掛接映像和開機映像。</span><span class="sxs-lookup"><span data-stu-id="ad168-194">Unmount the image and boot it.</span></span>
1. <span data-ttu-id="ad168-195">連線到 Windows PowerShell 的內建執行個體。</span><span class="sxs-lookup"><span data-stu-id="ad168-195">Connect to the built-in instance of Windows PowerShell.</span></span>
1. <span data-ttu-id="ad168-196">請遵循下列指示來建立使用[另一個執行個體技術][]的遠端端點。</span><span class="sxs-lookup"><span data-stu-id="ad168-196">Follow the instructions to create a remoting endpoint using the ["another instance technique"][].</span></span>

### <a name="online-deployment-of-powershell"></a><span data-ttu-id="ad168-197">PowerShell 的線上部署</span><span class="sxs-lookup"><span data-stu-id="ad168-197">Online Deployment of PowerShell</span></span>

<span data-ttu-id="ad168-198">使用下列步驟，將 PowerShell 部署到 Nano Server。</span><span class="sxs-lookup"><span data-stu-id="ad168-198">Deploy PowerShell to Nano Server using the following steps.</span></span>

- <span data-ttu-id="ad168-199">連線到 Windows PowerShell 的內建執行個體</span><span class="sxs-lookup"><span data-stu-id="ad168-199">Connect to the built-in instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="ad168-200">將檔案複製到 Nano Server 執行個體</span><span class="sxs-lookup"><span data-stu-id="ad168-200">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="ad168-201">輸入工作階段</span><span class="sxs-lookup"><span data-stu-id="ad168-201">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="ad168-202">壓縮檔 ZIP 檔案</span><span class="sxs-lookup"><span data-stu-id="ad168-202">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShell_<version>"
  ```

- <span data-ttu-id="ad168-203">如需 WSMan 型的遠端功能，請遵循下列指示來建立使用[另一個執行個體技術][]的遠端端點。</span><span class="sxs-lookup"><span data-stu-id="ad168-203">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"][].</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="ad168-204">安裝為 .NET 全域工具</span><span class="sxs-lookup"><span data-stu-id="ad168-204">Install as a .NET Global tool</span></span>

<span data-ttu-id="ad168-205">如果您已安裝 [.NET Core SDK](/dotnet/core/sdk)，就可以輕鬆地將 PowerShell 安裝為 [.NET 全域工具](/dotnet/core/tools/global-tools)。</span><span class="sxs-lookup"><span data-stu-id="ad168-205">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="ad168-206">Dotnet 工具安裝程式會將 `$env:USERPROFILE\dotnet\tools` 新增至您的 `$env:PATH` 環境變數。</span><span class="sxs-lookup"><span data-stu-id="ad168-206">The dotnet tool installer adds `$env:USERPROFILE\dotnet\tools` to your `$env:PATH` environment variable.</span></span> <span data-ttu-id="ad168-207">不過，目前執行的殼層沒有更新的 `$env:PATH`。</span><span class="sxs-lookup"><span data-stu-id="ad168-207">However, the currently running shell doesn't have the updated `$env:PATH`.</span></span> <span data-ttu-id="ad168-208">您可以透過輸入 `pwsh`，以從新的殼層啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="ad168-208">You can start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="install-powershell-via-winget"></a><span data-ttu-id="ad168-209">透過 Winget 安裝 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ad168-209">Install PowerShell via Winget</span></span>

<span data-ttu-id="ad168-210">`winget` 命令列工具可讓開發人員探索、安裝、升級、移除及設定 Windows 10 電腦上的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ad168-210">The `winget` command-line tool enables developers to discover, install, upgrade, remove, and configure applications on Windows 10 computers.</span></span> <span data-ttu-id="ad168-211">此工具是 Windows 封裝管理員服務的用戶端介面。</span><span class="sxs-lookup"><span data-stu-id="ad168-211">This tool is the client interface to the Windows Package Manager service.</span></span>

> [!NOTE]
> <span data-ttu-id="ad168-212">`winget` 工具目前處於預覽狀態。</span><span class="sxs-lookup"><span data-stu-id="ad168-212">The `winget` tool is currently a preview.</span></span> <span data-ttu-id="ad168-213">目前並非所有已規劃的功能都可用。</span><span class="sxs-lookup"><span data-stu-id="ad168-213">Not all planned functionality is available at this time.</span></span>
> <span data-ttu-id="ad168-214">您不應該在生產部署案例中使用此方法。</span><span class="sxs-lookup"><span data-stu-id="ad168-214">You should not use this method in a production deployment scenario.</span></span> <span data-ttu-id="ad168-215">如需系統需求清單與安裝指示，請參閱 [winget] 文件。</span><span class="sxs-lookup"><span data-stu-id="ad168-215">See the [winget] documentation for a list of system requirements and install instructions.</span></span>

<span data-ttu-id="ad168-216">您可以透過下列命令使用已發佈的 `winget` 套件來安裝 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="ad168-216">The following commands can be used to install PowerShell using the published `winget` packages:</span></span>

1. <span data-ttu-id="ad168-217">搜尋最新版的 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ad168-217">Search for the latest version of PowerShell</span></span>

   ```powershell
   winget search Microsoft.PowerShell
   ```

   ```Output
   Name               Id                           Version
   ---------------------------------------------------------------
   PowerShell         Microsoft.PowerShell         7.1.0
   PowerShell-Preview Microsoft.PowerShell-Preview 7.1.0-preview.5
   ```

1. <span data-ttu-id="ad168-218">使用 `--exact` 參數安裝特定版本的 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ad168-218">Install a version of PowerShell using the `--exact` parameter</span></span>

   ```powershell
   winget install --name PowerShell --exact
   winget install --name PowerShell-Preview --exact
   ```

## <a name="installing-from-the-microsoft-store"></a><span data-ttu-id="ad168-219"><a id="msix" />從 Microsoft Store 安裝</span><span class="sxs-lookup"><span data-stu-id="ad168-219"><a id="msix" />Installing from the Microsoft Store</span></span>

<span data-ttu-id="ad168-220">PowerShell 7.1 已經發佈至 Microsoft Store。</span><span class="sxs-lookup"><span data-stu-id="ad168-220">PowerShell 7.1 has been published to the Microsoft Store.</span></span> <span data-ttu-id="ad168-221">您可以在 [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) 網站上或 Windows 的 [Store] 應用程式中找到該 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="ad168-221">You can find the PowerShell release on the [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) website or in the Store application in Windows.</span></span>

<span data-ttu-id="ad168-222">Microsoft Store 套件的優點：</span><span class="sxs-lookup"><span data-stu-id="ad168-222">Benefits of the Microsoft Store package:</span></span>

- <span data-ttu-id="ad168-223">直接內建於 Windows 10 的自動更新</span><span class="sxs-lookup"><span data-stu-id="ad168-223">Automatic updates built right into Windows 10</span></span>
- <span data-ttu-id="ad168-224">與其他軟體散發機制 (例如 Intune 與 SCCM) 的整合</span><span class="sxs-lookup"><span data-stu-id="ad168-224">Integrates with other software distribution mechanisms like Intune and SCCM</span></span>

<span data-ttu-id="ad168-225">限制：</span><span class="sxs-lookup"><span data-stu-id="ad168-225">Limitations:</span></span>

<span data-ttu-id="ad168-226">MSIX 套件會在應用程式沙箱中執行，該沙箱會將針對某些檔案系統與登錄位置的存取虛擬化。</span><span class="sxs-lookup"><span data-stu-id="ad168-226">MSIX packages run in an application sandbox that virtualizes access to some filesystem and registry locations.</span></span>

- <span data-ttu-id="ad168-227">HKEY_CURRENT_USER 下的所有登錄變更都會在寫入時複製到以個別使用者與個別應用程式為基礎的私人位置。</span><span class="sxs-lookup"><span data-stu-id="ad168-227">All registry changes under HKEY_CURRENT_USER are copied on write to a private, per-user, per-app location.</span></span> <span data-ttu-id="ad168-228">因此，那些值將無法提供給其他應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="ad168-228">Therefore, those values are not available to other applications.</span></span>
- <span data-ttu-id="ad168-229">儲存在 `$PSHOME` 中的所有系統層級組態設定都無法修改。</span><span class="sxs-lookup"><span data-stu-id="ad168-229">Any system-level configuration settings stored in `$PSHOME` cannot be modified.</span></span> <span data-ttu-id="ad168-230">這包含 WSMAN 設定。</span><span class="sxs-lookup"><span data-stu-id="ad168-230">This includes the WSMAN configuration.</span></span> <span data-ttu-id="ad168-231">這會防止遠端工作階段連線到 PowerShell 的 Store 型安裝。</span><span class="sxs-lookup"><span data-stu-id="ad168-231">This prevents remote sessions from connecting to Store-based installs of PowerShell.</span></span> <span data-ttu-id="ad168-232">支援使用者層級設定與 SSH 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="ad168-232">User-level configurations and SSH remoting are supported.</span></span>

<span data-ttu-id="ad168-233">如需詳細資訊，請參閱[了解封裝的傳統型應用程式在 Windows 上執行的方式](/windows/msix/desktop/desktop-to-uwp-behind-the-scenes)。</span><span class="sxs-lookup"><span data-stu-id="ad168-233">For more information, see [Understanding how packaged desktop apps run on Windows](/windows/msix/desktop/desktop-to-uwp-behind-the-scenes).</span></span>

### <a name="using-the-msix-package"></a><span data-ttu-id="ad168-234">使用 MSIX 套件</span><span class="sxs-lookup"><span data-stu-id="ad168-234">Using the MSIX package</span></span>

> [!NOTE]
> <span data-ttu-id="ad168-235">PowerShell 的預覽組建包含 MSIX 套件。</span><span class="sxs-lookup"><span data-stu-id="ad168-235">The preview builds of PowerShell include an MSIX package.</span></span> <span data-ttu-id="ad168-236">尚未正式支援 MSIX 套件。</span><span class="sxs-lookup"><span data-stu-id="ad168-236">The MSIX package is not officially supported.</span></span> <span data-ttu-id="ad168-237">該套件的建置目的是為了在預覽期間進行測試之用。</span><span class="sxs-lookup"><span data-stu-id="ad168-237">The package is built for testing purposes during the preview period.</span></span>

<span data-ttu-id="ad168-238">若要在 Windows 10 用戶端上手動安裝 MSIX 套件，請從我們的 GitHub [版本][版本]頁面下載 MSIX 套件。</span><span class="sxs-lookup"><span data-stu-id="ad168-238">To manually install the MSIX package on a Windows 10 client, download the MSIX package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="ad168-239">向下捲動至想安裝版本的 [資產]  區段。</span><span class="sxs-lookup"><span data-stu-id="ad168-239">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="ad168-240">[資產] 區段可能會摺疊，因此您可能需要按一下以展開它。</span><span class="sxs-lookup"><span data-stu-id="ad168-240">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="ad168-241">MSIX 檔案看起來像這樣 - `PowerShell-<version>-win-<os-arch>.msix`</span><span class="sxs-lookup"><span data-stu-id="ad168-241">The MSIX file looks like this - `PowerShell-<version>-win-<os-arch>.msix`</span></span>

<span data-ttu-id="ad168-242">若要安裝套件，您必須使用 `Add-AppxPackage` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ad168-242">To install the package, you must use the `Add-AppxPackage` cmdlet.</span></span>

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="ad168-243">如何建立遠端端點</span><span class="sxs-lookup"><span data-stu-id="ad168-243">How to create a remoting endpoint</span></span>

<span data-ttu-id="ad168-244">PowerShell 支援透過 WSMan 與 SSH 的 PowerShell 遠端通訊協定 (PSRP)。</span><span class="sxs-lookup"><span data-stu-id="ad168-244">PowerShell supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="ad168-245">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="ad168-245">For more information, see:</span></span>

- <span data-ttu-id="ad168-246">[PowerShell Core 中的 SSH 遠端功能][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="ad168-246">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="ad168-247">[PowerShell Core 中的 WSMan 遠端功能][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="ad168-247">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="upgrading-an-existing-installation"></a><span data-ttu-id="ad168-248">升級現有的安裝</span><span class="sxs-lookup"><span data-stu-id="ad168-248">Upgrading an existing installation</span></span>

<span data-ttu-id="ad168-249">為了在升級時獲得最佳結果，您應該使用第一次安裝 PowerShell 時所使用的相同安裝方法。</span><span class="sxs-lookup"><span data-stu-id="ad168-249">For best results when upgrading, you should use the same install method you used when you first installed PowerShell.</span></span> <span data-ttu-id="ad168-250">每個安裝方法都會將 PowerShell 安裝於不同的位置。</span><span class="sxs-lookup"><span data-stu-id="ad168-250">Each installation method installs PowerShell in a different location.</span></span> <span data-ttu-id="ad168-251">如果您不確定 PowerShell 的安裝方式，則可將安裝的位置與此文章中的套件資訊進行比較。</span><span class="sxs-lookup"><span data-stu-id="ad168-251">If you are not sure how PowerShell was installed, you can compare the installed location with the package information in this article.</span></span> <span data-ttu-id="ad168-252">如果您已透過 MSI 套件安裝，該資訊便會顯示於 [程式和功能] 控制台中。</span><span class="sxs-lookup"><span data-stu-id="ad168-252">If you installed via the MSI package, that information appears in the **Programs and Features** Control Panel.</span></span>

## <a name="installation-support"></a><span data-ttu-id="ad168-253">安裝支援</span><span class="sxs-lookup"><span data-stu-id="ad168-253">Installation support</span></span>

<span data-ttu-id="ad168-254">Microsoft 支援此文件中的安裝方法。</span><span class="sxs-lookup"><span data-stu-id="ad168-254">Microsoft supports the installation methods in this document.</span></span> <span data-ttu-id="ad168-255">其他來源可能會提供其他安裝方法。</span><span class="sxs-lookup"><span data-stu-id="ad168-255">There may be other methods of installation available from other sources.</span></span> <span data-ttu-id="ad168-256">雖然那些工具與方法都有用，但 Microsoft 無法支援那些方法。</span><span class="sxs-lookup"><span data-stu-id="ad168-256">While those tools and methods may work, Microsoft cannot support those methods.</span></span>

<!-- link references -->

[發行]: https://github.com/PowerShell/PowerShell/releases
[releases]: https://github.com/PowerShell/PowerShell/releases
[最新]: https://github.com/PowerShell/PowerShell/releases/latest
[latest]: https://github.com/PowerShell/PowerShell/releases/latest
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
[winget]: /windows/package-manager/winget
[「另一個執行個體技術」]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register
["another instance technique"]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register
[Import-PSCoreRelease]: https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease
