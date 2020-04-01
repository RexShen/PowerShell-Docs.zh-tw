---
title: 在 macOS 上安裝 PowerShell
description: 在 macOS 上安裝 PowerShell 的相關資訊
ms.date: 12/12/2018
ms.openlocfilehash: 3a5e71d0f69d0c39f9b7f3fa667863d7ec0a31dd
ms.sourcegitcommit: bf71c8c5e2a4fc7d5c3a67a537db1285089d03a7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395000"
---
# <a name="installing-powershell-on-macos"></a><span data-ttu-id="10726-103">在 macOS 上安裝 PowerShell</span><span class="sxs-lookup"><span data-stu-id="10726-103">Installing PowerShell on macOS</span></span>

<span data-ttu-id="10726-104">PowerShell 支援 macOS 10.12 與更高版本。</span><span class="sxs-lookup"><span data-stu-id="10726-104">PowerShell supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="10726-105">GitHub [版本][]頁面上提供所有套件。</span><span class="sxs-lookup"><span data-stu-id="10726-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="10726-106">安裝套件之後，請從終端機執行 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="10726-106">After the package is installed, run `pwsh` from a terminal.</span></span>

> [!NOTE]
> <span data-ttu-id="10726-107">PowerShell 7 是會移除 PowerShell Core 6.x 的就地升級。</span><span class="sxs-lookup"><span data-stu-id="10726-107">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="10726-108">`/usr/local/microsoft/powershell/6` 資料夾已由 `/usr/local/microsoft/powershell/7` 取代。</span><span class="sxs-lookup"><span data-stu-id="10726-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="10726-109">如果您需要與 PowerShell 7 並存執行 PowerShell 6，請使用[二進位封存](#binary-archives)方法來重新安裝 PowerShell 6。</span><span class="sxs-lookup"><span data-stu-id="10726-109">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

## <a name="about-brew"></a><span data-ttu-id="10726-110">關於 Brew</span><span class="sxs-lookup"><span data-stu-id="10726-110">About Brew</span></span>

<span data-ttu-id="10726-111">[Homebrew][brew] 是 macOS 首選的套件管理員。</span><span class="sxs-lookup"><span data-stu-id="10726-111">[Homebrew][brew] is the preferred package manager for macOS.</span></span> <span data-ttu-id="10726-112">如果找不到 `brew` 命令，您需要遵循[指示][brew]安裝 Homebrew。</span><span class="sxs-lookup"><span data-stu-id="10726-112">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span> <span data-ttu-id="10726-113">或者，您也可透過[直接下載](#installation-via-direct-download)或[二進位封存](#binary-archives)來安裝 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="10726-113">Otherwise you may install PowerShell via [Direct Download](#installation-via-direct-download) or from [Binary Archives](#binary-archives).</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="10726-114">在 macOS 10.12 或更高版本上透過 Homebrew 安裝最新的穩定版本</span><span class="sxs-lookup"><span data-stu-id="10726-114">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="10726-115">如需 Brew 的相關資訊，請參閱[關於 Brew](#about-brew)。</span><span class="sxs-lookup"><span data-stu-id="10726-115">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="10726-116">現在，您可以安裝 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="10726-116">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="10726-117">最後，確認您的安裝可以正常執行：</span><span class="sxs-lookup"><span data-stu-id="10726-117">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="10726-118">當新的 PowerShell 版本發行時，請更新 Homebrew 的公式並升級 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="10726-118">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="10726-119">您可以從 PowerShell (pwsh) 主機內呼叫上述命令，但必須結束並重新啟動 PowerShell 殼層，才能完成升級並重新整理 `$PSVersionTable` 中顯示的值。</span><span class="sxs-lookup"><span data-stu-id="10726-119">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="10726-120">在 macOS 10.12 或更高版本上透過 Homebrew 安裝最新的預覽版本</span><span class="sxs-lookup"><span data-stu-id="10726-120">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="10726-121">如需 Brew 的相關資訊，請參閱[關於 Brew](#about-brew)。</span><span class="sxs-lookup"><span data-stu-id="10726-121">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="10726-122">安裝 Homebrew 之後，您可以安裝 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="10726-122">After you've installed Homebrew, you can install PowerShell.</span></span>
<span data-ttu-id="10726-123">首先，安裝 [Cask-Versions][cask-versions] 套件，它可讓您安裝 Cask 套件的替代版本：</span><span class="sxs-lookup"><span data-stu-id="10726-123">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="10726-124">現在，您可以安裝 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="10726-124">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="10726-125">最後，確認您的安裝可以正常執行：</span><span class="sxs-lookup"><span data-stu-id="10726-125">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="10726-126">當新的 PowerShell 版本發行時，請更新 Homebrew 的公式並升級 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="10726-126">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="10726-127">上述命令可從 PowerShell (pwsh) 主機內呼叫，但 PowerShell 殼層必須結束並重新啟動，才能完成升級。</span><span class="sxs-lookup"><span data-stu-id="10726-127">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="10726-128">並重新整理 `$PSVersionTable` 中顯示的值。</span><span class="sxs-lookup"><span data-stu-id="10726-128">and refresh the values shown in `$PSVersionTable`.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="10726-129">透過直接下載來安裝</span><span class="sxs-lookup"><span data-stu-id="10726-129">Installation via Direct Download</span></span>

<span data-ttu-id="10726-130">將 PKG 套件 `powershell-lts-7.0.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="10726-130">Download the PKG package `powershell-lts-7.0.0-osx-x64.pkg`</span></span>
<span data-ttu-id="10726-131">從[版本][]頁面下載到您的 macOS 電腦。</span><span class="sxs-lookup"><span data-stu-id="10726-131">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="10726-132">您可以按兩下檔案並依照提示執行作業，或從終端機安裝：</span><span class="sxs-lookup"><span data-stu-id="10726-132">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-lts-7.0.0-osx-x64.pkg -target /
```

<span data-ttu-id="10726-133">安裝 [OpenSSL](#install-openssl)。</span><span class="sxs-lookup"><span data-stu-id="10726-133">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="10726-134">PowerShell 遠端執行功能與 CIM 作業需要 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="10726-134">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="10726-135">安裝為 .NET 全域工具</span><span class="sxs-lookup"><span data-stu-id="10726-135">Install as a .NET Global tool</span></span>

<span data-ttu-id="10726-136">如果您已安裝 [.NET Core SDK](/dotnet/core/sdk)，就可以輕鬆地將 PowerShell 安裝為 [.NET 全域工具](/dotnet/core/tools/global-tools)。</span><span class="sxs-lookup"><span data-stu-id="10726-136">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="10726-137">Dotnet 工具安裝程式會將 `~/.dotnet/tools` 新增至您的 `PATH` 環境變數。</span><span class="sxs-lookup"><span data-stu-id="10726-137">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="10726-138">不過，目前執行的殼層沒有更新的 `PATH`。</span><span class="sxs-lookup"><span data-stu-id="10726-138">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="10726-139">您應該能夠透過輸入 `pwsh`，以從新的殼層啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="10726-139">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="10726-140">二進位封存</span><span class="sxs-lookup"><span data-stu-id="10726-140">Binary Archives</span></span>

<span data-ttu-id="10726-141">macOS 平台有 PowerShell 二進位 `tar.gz` 封存，以啟用進階的部署案例。</span><span class="sxs-lookup"><span data-stu-id="10726-141">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="10726-142">解除安裝 macOS 上的二進位封存</span><span class="sxs-lookup"><span data-stu-id="10726-142">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/7.0.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/7.0.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/7.0.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/7.0.0/pwsh /usr/local/bin/pwsh
```

<span data-ttu-id="10726-143">安裝 [OpenSSL](#install-openssl)。</span><span class="sxs-lookup"><span data-stu-id="10726-143">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="10726-144">PowerShell 遠端執行功能與 CIM 作業需要 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="10726-144">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="10726-145">安裝相依性</span><span class="sxs-lookup"><span data-stu-id="10726-145">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="10726-146">安裝 XCode 命令列工具</span><span class="sxs-lookup"><span data-stu-id="10726-146">Install XCode command-line tools</span></span>

```sh
xcode-select --install
```

### <a name="install-openssl"></a><span data-ttu-id="10726-147">安裝 OpenSSL</span><span class="sxs-lookup"><span data-stu-id="10726-147">Install OpenSSL</span></span>

<span data-ttu-id="10726-148">PowerShell 遠端執行功能與 CIM 作業需要 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="10726-148">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="10726-149">您可以透過 MacPorts 或 Brew 來安裝。</span><span class="sxs-lookup"><span data-stu-id="10726-149">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="10726-150">透過 Brew 安裝 OpenSSL</span><span class="sxs-lookup"><span data-stu-id="10726-150">Install OpenSSL via Brew</span></span>

<span data-ttu-id="10726-151">如需 Brew 的相關資訊，請參閱[關於 Brew](#about-brew)。</span><span class="sxs-lookup"><span data-stu-id="10726-151">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="10726-152">若要安裝 OpenSSL，請執行 `brew install openssl`。</span><span class="sxs-lookup"><span data-stu-id="10726-152">To install OpenSSL, run `brew install openssl`.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="10726-153">透過 MacPorts 安裝 OpenSSL</span><span class="sxs-lookup"><span data-stu-id="10726-153">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="10726-154">安裝 [XCode 命令列工具](#install-xcode-command-line-tools)。</span><span class="sxs-lookup"><span data-stu-id="10726-154">Install the [XCode command line tools](#install-xcode-command-line-tools).</span></span>
1. <span data-ttu-id="10726-155">安裝 MacPorts。</span><span class="sxs-lookup"><span data-stu-id="10726-155">Install MacPorts.</span></span>
   <span data-ttu-id="10726-156">若需要指示，請參閱[安裝指南](https://guide.macports.org/chunked/installing.macports.html) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="10726-156">If you need instructions, refer to the [installation guide](https://guide.macports.org/chunked/installing.macports.html).</span></span>
1. <span data-ttu-id="10726-157">透過執行 `sudo port selfupdate` 來更新 MacPorts。</span><span class="sxs-lookup"><span data-stu-id="10726-157">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="10726-158">透過執行 `sudo port upgrade outdated` 來升級 MacPorts 套件。</span><span class="sxs-lookup"><span data-stu-id="10726-158">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="10726-159">透過執行 `sudo port install openssl` 以安裝 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="10726-159">Install OpenSSL by running `sudo port install openssl`.</span></span>
1. <span data-ttu-id="10726-160">連結程式庫，以供 PowerShell 使用它們：</span><span class="sxs-lookup"><span data-stu-id="10726-160">Link the libraries to make them available to PowerShell:</span></span>

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell"></a><span data-ttu-id="10726-161">解除安裝 PowerShell</span><span class="sxs-lookup"><span data-stu-id="10726-161">Uninstalling PowerShell</span></span>

<span data-ttu-id="10726-162">如果您使用 Homebrew 安裝 PowerShell，請使用下列命令解除安裝：</span><span class="sxs-lookup"><span data-stu-id="10726-162">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="10726-163">如已透過直接下載安裝 PowerShell，即必須手動移除 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="10726-163">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="10726-164">若要移除其他的 PowerShell 路徑，請參閱此文件中的[路徑](#paths)一節，並使用 `sudo rm` 移除路徑。</span><span class="sxs-lookup"><span data-stu-id="10726-164">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="10726-165">如果使用 Homebrew 安裝，此即非必要。</span><span class="sxs-lookup"><span data-stu-id="10726-165">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="10726-166">路徑</span><span class="sxs-lookup"><span data-stu-id="10726-166">Paths</span></span>

* <span data-ttu-id="10726-167">`$PSHOME` 是 `/usr/local/microsoft/powershell/7.0.0/`</span><span class="sxs-lookup"><span data-stu-id="10726-167">`$PSHOME` is `/usr/local/microsoft/powershell/7.0.0/`</span></span>
* <span data-ttu-id="10726-168">會從 `~/.config/powershell/profile.ps1` 讀取使用者設定檔</span><span class="sxs-lookup"><span data-stu-id="10726-168">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="10726-169">會從 `$PSHOME/profile.ps1` 讀取預設設定檔</span><span class="sxs-lookup"><span data-stu-id="10726-169">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="10726-170">會從 `~/.local/share/powershell/Modules` 讀取使用者模組</span><span class="sxs-lookup"><span data-stu-id="10726-170">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="10726-171">會從 `/usr/local/share/powershell/Modules` 讀取共用的模組</span><span class="sxs-lookup"><span data-stu-id="10726-171">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="10726-172">會從 `$PSHOME/Modules` 讀取預設模組</span><span class="sxs-lookup"><span data-stu-id="10726-172">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="10726-173">PSReadline 記錄會記錄在 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="10726-173">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="10726-174">設定檔會採用 PowerShell 的每個主機設定。</span><span class="sxs-lookup"><span data-stu-id="10726-174">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="10726-175">因此預設主機特定設定檔便會存在於相同位置的 `Microsoft.PowerShell_profile.ps1`。</span><span class="sxs-lookup"><span data-stu-id="10726-175">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="10726-176">PowerShell 遵循 macOS 上的 [XDG 基底目錄規格][xdg-bds]。</span><span class="sxs-lookup"><span data-stu-id="10726-176">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="10726-177">因為 macOS 是 BSD 的衍生項，所以使用的前置詞是 `/usr/local` 而非 `/opt`。</span><span class="sxs-lookup"><span data-stu-id="10726-177">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="10726-178">因此，`$PSHOME` 是 `/usr/local/microsoft/powershell/7.0.0/`，而符號連結放置在 `/usr/local/bin/pwsh`。</span><span class="sxs-lookup"><span data-stu-id="10726-178">So, `$PSHOME` is `/usr/local/microsoft/powershell/7.0.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="10726-179">其他資源</span><span class="sxs-lookup"><span data-stu-id="10726-179">Additional Resources</span></span>

* <span data-ttu-id="10726-180">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="10726-180">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="10726-181">[Homebrew Github 存放庫][GitHub]</span><span class="sxs-lookup"><span data-stu-id="10726-181">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="10726-182">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="10726-182">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[版本]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
