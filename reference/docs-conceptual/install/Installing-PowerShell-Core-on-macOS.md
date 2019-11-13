---
title: 在 macOS 上安裝 PowerShell Core
description: 在 macOS 上安裝 PowerShell Core 的相關資訊
ms.date: 12/12/2018
ms.openlocfilehash: ad1306e99261e8e6e2fd49d3199d863929c31e92
ms.sourcegitcommit: 36e4c79afda2ce11febd93951e143687245f0b50
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2019
ms.locfileid: "73444437"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="324bf-103">在 macOS 上安裝 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="324bf-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="324bf-104">PowerShell Core 支援 macOS 10.12 和更版本。</span><span class="sxs-lookup"><span data-stu-id="324bf-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="324bf-105">GitHub [版本][]頁面上提供所有套件。</span><span class="sxs-lookup"><span data-stu-id="324bf-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="324bf-106">安裝套件之後，請從終端機執行 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="324bf-106">After the package is installed, run `pwsh` from a terminal.</span></span>

> [!TIP]
> <span data-ttu-id="324bf-107">如果您已安裝 [.NET Core SDK](/dotnet/core/sdk)，就可以輕鬆地將 PowerShell 安裝為 [.NET 通用工具](/dotnet/core/tools/global-tools)。</span><span class="sxs-lookup"><span data-stu-id="324bf-107">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it’s easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>
>
> ```
> dotnet tool install --global PowerShell
> ```

## <a name="about-brew"></a><span data-ttu-id="324bf-108">關於 Brew</span><span class="sxs-lookup"><span data-stu-id="324bf-108">About Brew</span></span>

<span data-ttu-id="324bf-109">[Homebrew][brew] 是 macOS 首選的套件管理員。</span><span class="sxs-lookup"><span data-stu-id="324bf-109">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="324bf-110">如果找不到 `brew` 命令，您需要遵循[指示][brew]安裝 Homebrew。</span><span class="sxs-lookup"><span data-stu-id="324bf-110">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>
<span data-ttu-id="324bf-111">或者，您也可透過[直接下載](#installation-via-direct-download)或[二進位封存](#binary-archives)來安裝 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="324bf-111">Otherwise you may install PowerShell via [Direct Download](#installation-via-direct-download) or from [Binary Archives](#binary-archives).</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="324bf-112">在 macOS 10.12 或更高版本上透過 Homebrew 安裝最新的穩定版本</span><span class="sxs-lookup"><span data-stu-id="324bf-112">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="324bf-113">如需 Brew 的相關資訊，請參閱[關於 Brew](#about-brew)。</span><span class="sxs-lookup"><span data-stu-id="324bf-113">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="324bf-114">現在，您可以安裝 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="324bf-114">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="324bf-115">最後，確認您的安裝可以正常執行：</span><span class="sxs-lookup"><span data-stu-id="324bf-115">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="324bf-116">當新的 PowerShell 版本發行時，請更新 Homebrew 的公式並升級 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="324bf-116">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="324bf-117">您可以從 PowerShell (pwsh) 主機內呼叫上述命令，但必須結束並重新啟動 PowerShell 殼層，才能完成升級並重新整理 `$PSVersionTable` 中顯示的值。</span><span class="sxs-lookup"><span data-stu-id="324bf-117">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="324bf-118">在 macOS 10.12 或更高版本上透過 Homebrew 安裝最新的預覽版本</span><span class="sxs-lookup"><span data-stu-id="324bf-118">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="324bf-119">如需 Brew 的相關資訊，請參閱[關於 Brew](#about-brew)。</span><span class="sxs-lookup"><span data-stu-id="324bf-119">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="324bf-120">安裝 Homebrew 之後，您可以安裝 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="324bf-120">After you've installed Homebrew, you can install PowerShell.</span></span>
<span data-ttu-id="324bf-121">首先，安裝 [Cask-Versions][cask-versions] 套件，它可讓您安裝 Cask 套件的替代版本：</span><span class="sxs-lookup"><span data-stu-id="324bf-121">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="324bf-122">現在，您可以安裝 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="324bf-122">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="324bf-123">最後，確認您的安裝可以正常執行：</span><span class="sxs-lookup"><span data-stu-id="324bf-123">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="324bf-124">當新的 PowerShell 版本發行時，請更新 Homebrew 的公式並升級 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="324bf-124">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="324bf-125">上述命令可從 PowerShell (pwsh) 主機內呼叫，但 PowerShell 殼層必須結束並重新啟動，才能完成升級。</span><span class="sxs-lookup"><span data-stu-id="324bf-125">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="324bf-126">並重新整理 `$PSVersionTable` 中顯示的值。</span><span class="sxs-lookup"><span data-stu-id="324bf-126">and refresh the values shown in `$PSVersionTable`.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="324bf-127">透過直接下載來安裝</span><span class="sxs-lookup"><span data-stu-id="324bf-127">Installation via Direct Download</span></span>

<span data-ttu-id="324bf-128">將 PKG 套件 `powershell-6.2.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="324bf-128">Download the PKG package `powershell-6.2.0-osx-x64.pkg`</span></span>
<span data-ttu-id="324bf-129">從[版本][]頁面下載到您的 macOS 電腦。</span><span class="sxs-lookup"><span data-stu-id="324bf-129">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="324bf-130">您可以按兩下檔案並依照提示執行作業，或從終端機安裝：</span><span class="sxs-lookup"><span data-stu-id="324bf-130">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.2.0-osx-x64.pkg -target /
```

<span data-ttu-id="324bf-131">安裝 [OpenSSL](#install-openssl)。</span><span class="sxs-lookup"><span data-stu-id="324bf-131">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="324bf-132">PowerShell 遠端執行功能與 CIM 作業需要 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="324bf-132">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="324bf-133">二進位封存</span><span class="sxs-lookup"><span data-stu-id="324bf-133">Binary Archives</span></span>

<span data-ttu-id="324bf-134">macOS 平台有 PowerShell 二進位 `tar.gz` 封存，以啟用進階的部署案例。</span><span class="sxs-lookup"><span data-stu-id="324bf-134">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="324bf-135">解除安裝 macOS 上的二進位封存</span><span class="sxs-lookup"><span data-stu-id="324bf-135">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.2.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.2.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.2.0/pwsh /usr/local/bin/pwsh
```

<span data-ttu-id="324bf-136">安裝 [OpenSSL](#install-openssl)。</span><span class="sxs-lookup"><span data-stu-id="324bf-136">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="324bf-137">PowerShell 遠端執行功能與 CIM 作業需要 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="324bf-137">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="324bf-138">安裝相依性</span><span class="sxs-lookup"><span data-stu-id="324bf-138">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="324bf-139">安裝 XCode 命令列工具</span><span class="sxs-lookup"><span data-stu-id="324bf-139">Install XCode command-line tools</span></span>

```sh
xcode-select --install
```

### <a name="install-openssl"></a><span data-ttu-id="324bf-140">安裝 OpenSSL</span><span class="sxs-lookup"><span data-stu-id="324bf-140">Install OpenSSL</span></span>

<span data-ttu-id="324bf-141">PowerShell 遠端執行功能與 CIM 作業需要 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="324bf-141">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="324bf-142">您可以透過 MacPorts 或 Brew 來安裝。</span><span class="sxs-lookup"><span data-stu-id="324bf-142">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="324bf-143">透過 Brew 安裝 OpenSSL</span><span class="sxs-lookup"><span data-stu-id="324bf-143">Install OpenSSL via Brew</span></span>

<span data-ttu-id="324bf-144">如需 Brew 的相關資訊，請參閱[關於 Brew](#about-brew)。</span><span class="sxs-lookup"><span data-stu-id="324bf-144">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="324bf-145">若要安裝 OpenSSL，請執行 `brew install openssl`。</span><span class="sxs-lookup"><span data-stu-id="324bf-145">To install OpenSSL, run `brew install openssl`.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="324bf-146">透過 MacPorts 安裝 OpenSSL</span><span class="sxs-lookup"><span data-stu-id="324bf-146">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="324bf-147">安裝 [XCode 命令列工具](#install-xcode-command-line-tools)。</span><span class="sxs-lookup"><span data-stu-id="324bf-147">Install the [XCode command line tools](#install-xcode-command-line-tools).</span></span>
1. <span data-ttu-id="324bf-148">安裝 MacPorts。</span><span class="sxs-lookup"><span data-stu-id="324bf-148">Install MacPorts.</span></span>
   <span data-ttu-id="324bf-149">若需要指示，請參閱[安裝指南](https://guide.macports.org/chunked/installing.macports.html) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="324bf-149">If you need instructions, refer to the [installation guide](https://guide.macports.org/chunked/installing.macports.html).</span></span>
1. <span data-ttu-id="324bf-150">透過執行 `sudo port selfupdate` 來更新 MacPorts。</span><span class="sxs-lookup"><span data-stu-id="324bf-150">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="324bf-151">透過執行 `sudo port upgrade outdated` 來升級 MacPorts 套件。</span><span class="sxs-lookup"><span data-stu-id="324bf-151">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="324bf-152">透過執行 `sudo port install openssl` 以安裝 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="324bf-152">Install OpenSSL by running `sudo port install openssl`.</span></span>
1. <span data-ttu-id="324bf-153">連結程式庫，以供 PowerShell 使用它們：</span><span class="sxs-lookup"><span data-stu-id="324bf-153">Link the libraries to make them available to PowerShell:</span></span>

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="324bf-154">解除安裝 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="324bf-154">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="324bf-155">如果您使用 Homebrew 安裝 PowerShell，請使用下列命令解除安裝：</span><span class="sxs-lookup"><span data-stu-id="324bf-155">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="324bf-156">如已透過直接下載安裝 PowerShell，即必須手動移除 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="324bf-156">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="324bf-157">若要移除其他的 PowerShell 路徑，請參閱此文件中的[路徑](#paths)一節，並使用 `sudo rm` 移除路徑。</span><span class="sxs-lookup"><span data-stu-id="324bf-157">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="324bf-158">如果使用 Homebrew 安裝，此即非必要。</span><span class="sxs-lookup"><span data-stu-id="324bf-158">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="324bf-159">路徑</span><span class="sxs-lookup"><span data-stu-id="324bf-159">Paths</span></span>

* <span data-ttu-id="324bf-160">`$PSHOME` 是 `/usr/local/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="324bf-160">`$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="324bf-161">會從 `~/.config/powershell/profile.ps1` 讀取使用者設定檔</span><span class="sxs-lookup"><span data-stu-id="324bf-161">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="324bf-162">會從 `$PSHOME/profile.ps1` 讀取預設設定檔</span><span class="sxs-lookup"><span data-stu-id="324bf-162">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="324bf-163">會從 `~/.local/share/powershell/Modules` 讀取使用者模組</span><span class="sxs-lookup"><span data-stu-id="324bf-163">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="324bf-164">會從 `/usr/local/share/powershell/Modules` 讀取共用的模組</span><span class="sxs-lookup"><span data-stu-id="324bf-164">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="324bf-165">會從 `$PSHOME/Modules` 讀取預設模組</span><span class="sxs-lookup"><span data-stu-id="324bf-165">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="324bf-166">PSReadline 記錄會記錄在 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="324bf-166">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="324bf-167">設定檔會採用 PowerShell 的每個主機設定。</span><span class="sxs-lookup"><span data-stu-id="324bf-167">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="324bf-168">因此預設主機特定設定檔便會存在於相同位置的 `Microsoft.PowerShell_profile.ps1`。</span><span class="sxs-lookup"><span data-stu-id="324bf-168">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="324bf-169">PowerShell 遵循 macOS 上的 [XDG 基底目錄規格][xdg-bds]。</span><span class="sxs-lookup"><span data-stu-id="324bf-169">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="324bf-170">因為 macOS 是 BSD 的衍生項，所以使用的前置詞是 `/usr/local` 而非 `/opt`。</span><span class="sxs-lookup"><span data-stu-id="324bf-170">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="324bf-171">因此，`$PSHOME` 是 `/usr/local/microsoft/powershell/6.2.0/`，而符號連結放置在 `/usr/local/bin/pwsh`。</span><span class="sxs-lookup"><span data-stu-id="324bf-171">So, `$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="324bf-172">其他資源</span><span class="sxs-lookup"><span data-stu-id="324bf-172">Additional Resources</span></span>

* <span data-ttu-id="324bf-173">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="324bf-173">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="324bf-174">[Homebrew Github 存放庫][GitHub]</span><span class="sxs-lookup"><span data-stu-id="324bf-174">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="324bf-175">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="324bf-175">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[版本]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
