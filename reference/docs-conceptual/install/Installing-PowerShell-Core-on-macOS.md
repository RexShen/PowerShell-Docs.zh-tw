---
title: 在 macOS 上安裝 PowerShell
description: 在 macOS 上安裝 PowerShell 的相關資訊
ms.date: 11/11/2020
ms.openlocfilehash: 1ce96e993d8fc87edd93fca840ede250d5632577
ms.sourcegitcommit: 3ab2951a5460a39ca5fb3d25ffcb1d8868f4e011
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2020
ms.locfileid: "96535095"
---
# <a name="installing-powershell-on-macos"></a><span data-ttu-id="b60c3-103">在 macOS 上安裝 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b60c3-103">Installing PowerShell on macOS</span></span>

<span data-ttu-id="b60c3-104">PowerShell 7.0 或更高版本需要 macOS 10.13 與更高版本。</span><span class="sxs-lookup"><span data-stu-id="b60c3-104">PowerShell 7.0 or higher require macOS 10.13 and higher.</span></span> <span data-ttu-id="b60c3-105">GitHub [發行][]頁面上提供所有套件。</span><span class="sxs-lookup"><span data-stu-id="b60c3-105">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="b60c3-106">安裝套件之後，請從終端機執行 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="b60c3-106">After the package is installed, run `pwsh` from a terminal.</span></span>

> [!NOTE]
> <span data-ttu-id="b60c3-107">PowerShell 7.1 是會移除 PowerShell Core 6.x 與 7.0 的就地升級。</span><span class="sxs-lookup"><span data-stu-id="b60c3-107">PowerShell 7.1 is an in-place upgrade that removes PowerShell Core 6.x and 7.0.</span></span>
>
> <span data-ttu-id="b60c3-108">`/usr/local/microsoft/powershell/6` 資料夾已由 `/usr/local/microsoft/powershell/7` 取代。</span><span class="sxs-lookup"><span data-stu-id="b60c3-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="b60c3-109">如果您需要與 PowerShell 7.1 並存執行較舊版本的 PowerShell Core，請使用[二進位封存](#binary-archives)方法來安裝所需版本。</span><span class="sxs-lookup"><span data-stu-id="b60c3-109">If you need to run and older version of PowerShell core side-by-side with PowerShell 7.1, install the version you want using the [binary archive](#binary-archives) method.</span></span>

<span data-ttu-id="b60c3-110">有幾種方式可在 macOS 上安裝 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="b60c3-110">There are several ways to install PowerShell on macOS.</span></span> <span data-ttu-id="b60c3-111">請選擇下列其中一個方法：</span><span class="sxs-lookup"><span data-stu-id="b60c3-111">Choose one of the following methods:</span></span>

- <span data-ttu-id="b60c3-112">使用 Homebrew 安裝。</span><span class="sxs-lookup"><span data-stu-id="b60c3-112">Install using Homebrew.</span></span> <span data-ttu-id="b60c3-113">Homebrew 是 macOS 首選的套件管理員。</span><span class="sxs-lookup"><span data-stu-id="b60c3-113">Homebrew is the preferred package manager for macOS.</span></span>
- <span data-ttu-id="b60c3-114">透過[直接下載](#installation-via-direct-download)安裝 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b60c3-114">Install PowerShell via [Direct Download](#installation-via-direct-download)</span></span>
- <span data-ttu-id="b60c3-115">從[二進位封存](#binary-archives)進行安裝。</span><span class="sxs-lookup"><span data-stu-id="b60c3-115">Install from [binary archives](#binary-archives).</span></span>

<span data-ttu-id="b60c3-116">安裝 PowerShell 之後，會需要一併安裝 [OpenSSL](#installing-dependencies)。</span><span class="sxs-lookup"><span data-stu-id="b60c3-116">After installing PowerShell, you should install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="b60c3-117">PowerShell 遠端執行功能與 CIM 作業需要 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="b60c3-117">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1013-or-higher"></a><span data-ttu-id="b60c3-118">在 macOS 10.13 或更新版本上透過 Homebrew 安裝最新的穩定版本</span><span class="sxs-lookup"><span data-stu-id="b60c3-118">Installation of latest stable release via Homebrew on macOS 10.13 or higher</span></span>

<span data-ttu-id="b60c3-119">如果找不到 `brew` 命令，您需要遵循[指示][brew]安裝 Homebrew。</span><span class="sxs-lookup"><span data-stu-id="b60c3-119">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="b60c3-120">現在，您可以安裝 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="b60c3-120">Now, you can install PowerShell:</span></span>

```sh
brew install --cask powershell
```

<span data-ttu-id="b60c3-121">最後，確認您的安裝可以正常執行：</span><span class="sxs-lookup"><span data-stu-id="b60c3-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="b60c3-122">當新的 PowerShell 版本發行時，請更新 Homebrew 的公式並升級 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="b60c3-122">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew upgrade powershell --cask
```

> [!NOTE]
> <span data-ttu-id="b60c3-123">您可以從 PowerShell (pwsh) 主機內呼叫上述命令，但必須結束並重新啟動 PowerShell 殼層，才能完成升級並重新整理 `$PSVersionTable` 中顯示的值。</span><span class="sxs-lookup"><span data-stu-id="b60c3-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1013-or-higher"></a><span data-ttu-id="b60c3-124">在 macOS 10.13 或更新版本上透過 Homebrew 安裝最新的預覽版本</span><span class="sxs-lookup"><span data-stu-id="b60c3-124">Installation of latest preview release via Homebrew on macOS 10.13 or higher</span></span>

<span data-ttu-id="b60c3-125">安裝 Homebrew 之後，您可以安裝 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="b60c3-125">After you've installed Homebrew, you can install PowerShell.</span></span> <span data-ttu-id="b60c3-126">首先，安裝 [Cask-Versions][cask-versions] 套件，它可讓您安裝 Cask 套件的替代版本：</span><span class="sxs-lookup"><span data-stu-id="b60c3-126">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="b60c3-127">現在，您可以安裝 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="b60c3-127">Now, you can install PowerShell:</span></span>

```sh
brew install --cask powershell-preview
```

<span data-ttu-id="b60c3-128">最後，確認您的安裝可以正常執行：</span><span class="sxs-lookup"><span data-stu-id="b60c3-128">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="b60c3-129">當新的 PowerShell 版本發行時，請更新 Homebrew 的公式並升級 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="b60c3-129">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew upgrade powershell-preview --cask
```

> [!NOTE]
> <span data-ttu-id="b60c3-130">上述命令可從 PowerShell (pwsh) 主機內呼叫，但 PowerShell 殼層必須結束並重新啟動，才能完成升級。</span><span class="sxs-lookup"><span data-stu-id="b60c3-130">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="b60c3-131">並重新整理 `$PSVersionTable` 中顯示的值。</span><span class="sxs-lookup"><span data-stu-id="b60c3-131">and refresh the values shown in `$PSVersionTable`.</span></span>

<span data-ttu-id="b60c3-132">穩定版本與 LTS 版本也支援使用 Homebrew tap 方法安裝 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="b60c3-132">Installing PowerShell using the Homebrew tap method is also supported for stable and LTS versions.</span></span>

```sh
brew install powershell/tap/powershell
```

<span data-ttu-id="b60c3-133">您現在可驗證安裝</span><span class="sxs-lookup"><span data-stu-id="b60c3-133">You can now verify your install</span></span>

```sh
pwsh
```

<span data-ttu-id="b60c3-134">發行新版本的 PowerShell 時，只要執行下列命令即可。</span><span class="sxs-lookup"><span data-stu-id="b60c3-134">When new versions of PowerShell are released, simply run the following command.</span></span>

```sh
brew upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="b60c3-135">無論使用 cask 或 tap 方法，當更新至較新版本的 PowerShell 時，請使用與當初安裝 PowerShell 時相同的方法。</span><span class="sxs-lookup"><span data-stu-id="b60c3-135">Whether you use the cask or the tap method, when updating to a newer version of PowerShell, use the same method you used to initially install PowerShell.</span></span> <span data-ttu-id="b60c3-136">如果使用不同的方法，則開啟新的 pwsh 工作階段時將會繼續使用舊版 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="b60c3-136">If you use a different method, opening a new pwsh session will continue to use the older version of PowerShell.</span></span>
>
> <span data-ttu-id="b60c3-137">如果決定使用不同的方法，則可使用 [Homebrew link 方法](https://docs.brew.sh/Manpage#link-ln-options-formula)來修正問題。</span><span class="sxs-lookup"><span data-stu-id="b60c3-137">If you do decide to use different methods, there are ways to correct the issue using the [Homebrew link method](https://docs.brew.sh/Manpage#link-ln-options-formula).</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="b60c3-138">透過直接下載來安裝</span><span class="sxs-lookup"><span data-stu-id="b60c3-138">Installation via Direct Download</span></span>

<span data-ttu-id="b60c3-139">將[版本][]頁面上的 PKG 套件 `powershell-7.1.0-osx-x64.pkg` 下載至 macOS 電腦。</span><span class="sxs-lookup"><span data-stu-id="b60c3-139">Download the PKG package `powershell-7.1.0-osx-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="b60c3-140">您可以按兩下檔案並依照提示執行作業，或從終端機安裝：</span><span class="sxs-lookup"><span data-stu-id="b60c3-140">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-7.1.0-osx-x64.pkg -target /
```

<span data-ttu-id="b60c3-141">安裝 [OpenSSL](#installing-dependencies)。</span><span class="sxs-lookup"><span data-stu-id="b60c3-141">Install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="b60c3-142">PowerShell 遠端執行功能與 CIM 作業需要 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="b60c3-142">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="b60c3-143">安裝為 .NET 全域工具</span><span class="sxs-lookup"><span data-stu-id="b60c3-143">Install as a .NET Global tool</span></span>

<span data-ttu-id="b60c3-144">如果您已安裝 [.NET Core SDK](/dotnet/core/sdk)，就可以輕鬆地將 PowerShell 安裝為 [.NET 全域工具](/dotnet/core/tools/global-tools)。</span><span class="sxs-lookup"><span data-stu-id="b60c3-144">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="b60c3-145">Dotnet 工具安裝程式會將 `~/.dotnet/tools` 新增至您的 `PATH` 環境變數。</span><span class="sxs-lookup"><span data-stu-id="b60c3-145">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="b60c3-146">不過，目前執行的殼層沒有更新的 `PATH`。</span><span class="sxs-lookup"><span data-stu-id="b60c3-146">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="b60c3-147">您應該能夠透過輸入 `pwsh`，以從新的殼層啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="b60c3-147">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

<span data-ttu-id="b60c3-148">安裝 [OpenSSL](#installing-dependencies)。</span><span class="sxs-lookup"><span data-stu-id="b60c3-148">Install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="b60c3-149">PowerShell 遠端執行功能與 CIM 作業需要 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="b60c3-149">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="b60c3-150">二進位封存</span><span class="sxs-lookup"><span data-stu-id="b60c3-150">Binary Archives</span></span>

<span data-ttu-id="b60c3-151">macOS 平台有 PowerShell 二進位 `tar.gz` 封存，以啟用進階的部署案例。</span><span class="sxs-lookup"><span data-stu-id="b60c3-151">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span> <span data-ttu-id="b60c3-152">當使用此方法安裝時，也必須手動安裝相依性。</span><span class="sxs-lookup"><span data-stu-id="b60c3-152">When you install using this method you must also manually install any dependencies.</span></span>

<span data-ttu-id="b60c3-153">安裝 [OpenSSL](#installing-dependencies)。</span><span class="sxs-lookup"><span data-stu-id="b60c3-153">Install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="b60c3-154">PowerShell 遠端執行功能與 CIM 作業需要 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="b60c3-154">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="b60c3-155">解除安裝 macOS 上的二進位封存</span><span class="sxs-lookup"><span data-stu-id="b60c3-155">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.1.0/powershell-7.1.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/7.1.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/7.1.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/7.1.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/7.1.0/pwsh /usr/local/bin/pwsh
```

## <a name="installing-dependencies"></a><span data-ttu-id="b60c3-156">安裝相依性</span><span class="sxs-lookup"><span data-stu-id="b60c3-156">Installing dependencies</span></span>

<span data-ttu-id="b60c3-157">PowerShell 遠端執行功能與 CIM 作業需要 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="b60c3-157">OpenSSL is required for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="b60c3-158">如有需要，您可透過 MacPorts 安裝 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="b60c3-158">You can install OpenSSL via MacPorts if needed.</span></span>

> [!NOTE]
> <span data-ttu-id="b60c3-159">當 MacPorts 和 Homebrew 在同一個系統上一起使用時可能會發生問題。</span><span class="sxs-lookup"><span data-stu-id="b60c3-159">MacPorts and Homebrew can have problems when used to together on the same system.</span></span> <span data-ttu-id="b60c3-160">不過，Homebrew 沒有 OpenSSL 1.0 的套件。</span><span class="sxs-lookup"><span data-stu-id="b60c3-160">However, Homebrew does not have a package for OpenSSL 1.0.</span></span> <span data-ttu-id="b60c3-161">如需詳細資訊，請參閱 [MacPorts 常見問題集](https://trac.macports.org/wiki/FAQ)。</span><span class="sxs-lookup"><span data-stu-id="b60c3-161">For more information, see the [MacPorts FAQ](https://trac.macports.org/wiki/FAQ).</span></span>

1. <span data-ttu-id="b60c3-162">安裝 Xcode 命令列工具。</span><span class="sxs-lookup"><span data-stu-id="b60c3-162">Install the Xcode command-line tools.</span></span> <span data-ttu-id="b60c3-163">MacPorts 需要 Xcode 工具。</span><span class="sxs-lookup"><span data-stu-id="b60c3-163">The Xcode tools are required by MacPorts.</span></span>

   ```sh
   xcode-select --install
   ```

1. <span data-ttu-id="b60c3-164">安裝 MacPorts。</span><span class="sxs-lookup"><span data-stu-id="b60c3-164">Install MacPorts.</span></span> <span data-ttu-id="b60c3-165">若需要指示，請參閱[安裝指南](https://www.macports.org/install.php) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="b60c3-165">If you need instructions, refer to the [installation guide](https://www.macports.org/install.php).</span></span>
1. <span data-ttu-id="b60c3-166">透過執行 `sudo port selfupdate` 來更新 MacPorts。</span><span class="sxs-lookup"><span data-stu-id="b60c3-166">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="b60c3-167">透過執行 `sudo port upgrade outdated` 來升級 MacPorts 套件。</span><span class="sxs-lookup"><span data-stu-id="b60c3-167">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="b60c3-168">透過執行 `sudo port install openssl10` 以安裝 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="b60c3-168">Install OpenSSL by running `sudo port install openssl10`.</span></span>
1. <span data-ttu-id="b60c3-169">連結程式庫，以供 PowerShell 使用它們：</span><span class="sxs-lookup"><span data-stu-id="b60c3-169">Link the libraries to make them available to PowerShell:</span></span>

   ```sh
   sudo mkdir -p /usr/local/opt/openssl
   sudo ln -s /opt/local/lib/openssl-1.0 /usr/local/opt/openssl/lib
   ```

## <a name="uninstalling-powershell"></a><span data-ttu-id="b60c3-170">解除安裝 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b60c3-170">Uninstalling PowerShell</span></span>

<span data-ttu-id="b60c3-171">如果您使用 Homebrew 安裝 PowerShell，請使用下列命令解除安裝：</span><span class="sxs-lookup"><span data-stu-id="b60c3-171">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="b60c3-172">如已透過直接下載安裝 PowerShell，即必須手動移除 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="b60c3-172">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="b60c3-173">若要移除其他的 PowerShell 路徑，請參閱此文件中的[路徑](#paths)一節，並使用 `sudo rm` 移除路徑。</span><span class="sxs-lookup"><span data-stu-id="b60c3-173">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="b60c3-174">如果使用 Homebrew 安裝，此即非必要。</span><span class="sxs-lookup"><span data-stu-id="b60c3-174">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="b60c3-175">路徑</span><span class="sxs-lookup"><span data-stu-id="b60c3-175">Paths</span></span>

- <span data-ttu-id="b60c3-176">`$PSHOME` 是 `/usr/local/microsoft/powershell/7.1.0/`</span><span class="sxs-lookup"><span data-stu-id="b60c3-176">`$PSHOME` is `/usr/local/microsoft/powershell/7.1.0/`</span></span>
- <span data-ttu-id="b60c3-177">會從 `~/.config/powershell/profile.ps1` 讀取使用者設定檔</span><span class="sxs-lookup"><span data-stu-id="b60c3-177">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
- <span data-ttu-id="b60c3-178">會從 `$PSHOME/profile.ps1` 讀取預設設定檔</span><span class="sxs-lookup"><span data-stu-id="b60c3-178">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
- <span data-ttu-id="b60c3-179">會從 `~/.local/share/powershell/Modules` 讀取使用者模組</span><span class="sxs-lookup"><span data-stu-id="b60c3-179">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="b60c3-180">會從 `/usr/local/share/powershell/Modules` 讀取共用的模組</span><span class="sxs-lookup"><span data-stu-id="b60c3-180">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
- <span data-ttu-id="b60c3-181">會從 `$PSHOME/Modules` 讀取預設模組</span><span class="sxs-lookup"><span data-stu-id="b60c3-181">Default modules will be read from `$PSHOME/Modules`</span></span>
- <span data-ttu-id="b60c3-182">PSReadline 記錄會記錄在 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="b60c3-182">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="b60c3-183">設定檔會採用 PowerShell 的每個主機設定。</span><span class="sxs-lookup"><span data-stu-id="b60c3-183">The profiles respect PowerShell's per-host configuration.</span></span> <span data-ttu-id="b60c3-184">因此預設主機特定設定檔便會存在於相同位置的 `Microsoft.PowerShell_profile.ps1`。</span><span class="sxs-lookup"><span data-stu-id="b60c3-184">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="b60c3-185">PowerShell 遵循 macOS 上的 [XDG 基底目錄規格][xdg-bds]。</span><span class="sxs-lookup"><span data-stu-id="b60c3-185">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="b60c3-186">因為 macOS 是 BSD 的衍生項，所以使用的前置詞是 `/usr/local` 而非 `/opt`。</span><span class="sxs-lookup"><span data-stu-id="b60c3-186">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span> <span data-ttu-id="b60c3-187">因此，`$PSHOME` 是 `/usr/local/microsoft/powershell/7.1.0/`，而符號連結放置在 `/usr/local/bin/pwsh`。</span><span class="sxs-lookup"><span data-stu-id="b60c3-187">So, `$PSHOME` is `/usr/local/microsoft/powershell/7.1.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="installation-support"></a><span data-ttu-id="b60c3-188">安裝支援</span><span class="sxs-lookup"><span data-stu-id="b60c3-188">Installation support</span></span>

<span data-ttu-id="b60c3-189">Microsoft 支援此文件中的安裝方法。</span><span class="sxs-lookup"><span data-stu-id="b60c3-189">Microsoft supports the installation methods in this document.</span></span> <span data-ttu-id="b60c3-190">其他來源可能會提供其他安裝方法。</span><span class="sxs-lookup"><span data-stu-id="b60c3-190">There may be other methods of installation available from other sources.</span></span> <span data-ttu-id="b60c3-191">雖然那些工具與方法都有用，但 Microsoft 無法支援那些方法。</span><span class="sxs-lookup"><span data-stu-id="b60c3-191">While those tools and methods may work, Microsoft cannot support those methods.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="b60c3-192">其他資源</span><span class="sxs-lookup"><span data-stu-id="b60c3-192">Additional Resources</span></span>

- <span data-ttu-id="b60c3-193">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="b60c3-193">[Homebrew Web][brew]</span></span>
- <span data-ttu-id="b60c3-194">[Homebrew Github 存放庫][GitHub]</span><span class="sxs-lookup"><span data-stu-id="b60c3-194">[Homebrew Github Repository][GitHub]</span></span>
- <span data-ttu-id="b60c3-195">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="b60c3-195">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[發行]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
