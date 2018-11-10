---
title: 在 macOS 上安裝 PowerShell Core
description: 在 macOS 上安裝 PowerShell Core 的相關資訊
ms.date: 11/02/2018
ms.openlocfilehash: 162e841bf71d708e9db84ea1bb2dbef13924783b
ms.sourcegitcommit: f4247d3f91d06ec392c4cd66921ce7d0456a2bd9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "50998498"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="be65a-103">在 macOS 上安裝 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="be65a-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="be65a-104">PowerShell Core 支援 macOS 10.12 和更版本。</span><span class="sxs-lookup"><span data-stu-id="be65a-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="be65a-105">GitHub [版本][]頁面上提供所有套件。</span><span class="sxs-lookup"><span data-stu-id="be65a-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="be65a-106">安裝套件之後，請從終端機執行 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="be65a-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="about-brew"></a><span data-ttu-id="be65a-107">關於 Brew</span><span class="sxs-lookup"><span data-stu-id="be65a-107">About Brew</span></span>

<span data-ttu-id="be65a-108">[Homebrew][ brew] 是 macOS 首選的套件管理員。</span><span class="sxs-lookup"><span data-stu-id="be65a-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="be65a-109">如果找不到 `brew` 命令，您需要遵循[指示][brew]安裝 Homebrew。</span><span class="sxs-lookup"><span data-stu-id="be65a-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="be65a-110">在 macOS 10.12 或更高版本上透過 Homebrew 安裝最新的穩定版本</span><span class="sxs-lookup"><span data-stu-id="be65a-110">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="be65a-111">如需 Brew 的相關資訊，請參閱[關於 Brew](#about-brew)。</span><span class="sxs-lookup"><span data-stu-id="be65a-111">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="be65a-112">現在，您可以安裝 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="be65a-112">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="be65a-113">最後，確認您的安裝可以正常執行：</span><span class="sxs-lookup"><span data-stu-id="be65a-113">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="be65a-114">發行新的 PowerShell 版本時，只要更新 Homebrew 的公式並升級 PowerShell 即可：</span><span class="sxs-lookup"><span data-stu-id="be65a-114">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="be65a-115">您可從 PowerShell (pwsh) 主機內呼叫上命令，但必須結束並重新啟動 PowerShell 殼層，才能完成升級並重新整理 $PSVersionTable 中顯示的值。</span><span class="sxs-lookup"><span data-stu-id="be65a-115">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="be65a-116">在 macOS 10.12 或更高版本上透過 Homebrew 安裝最新的預覽版本</span><span class="sxs-lookup"><span data-stu-id="be65a-116">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="be65a-117">如需 Brew 的相關資訊，請參閱[關於 Brew](#about-brew)。</span><span class="sxs-lookup"><span data-stu-id="be65a-117">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="be65a-118">安裝好 Homebrew 之後，安裝 PowerShell 就很容易。</span><span class="sxs-lookup"><span data-stu-id="be65a-118">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="be65a-119">首先，安裝 [Cask 版本][cask-versions]，這可讓您安裝 Cask 套件的替代版本：</span><span class="sxs-lookup"><span data-stu-id="be65a-119">First, install [Cask-Versions][cask-versions] which lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="be65a-120">現在，您可以安裝 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="be65a-120">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="be65a-121">最後，確認您的安裝可以正常執行：</span><span class="sxs-lookup"><span data-stu-id="be65a-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="be65a-122">發行新的 PowerShell 版本時，只要更新 Homebrew 的公式並升級 PowerShell 即可：</span><span class="sxs-lookup"><span data-stu-id="be65a-122">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="be65a-123">上述命令可從 PowerShell (pwsh) 主機內呼叫，但 PowerShell 殼層必須結束並重新啟動，才能完成升級。</span><span class="sxs-lookup"><span data-stu-id="be65a-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="be65a-124">並重新整理 $PSVersionTable 中顯示的值。</span><span class="sxs-lookup"><span data-stu-id="be65a-124">and refresh the values shown in $PSVersionTable.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="be65a-125">透過直接下載來安裝</span><span class="sxs-lookup"><span data-stu-id="be65a-125">Installation via Direct Download</span></span>

<span data-ttu-id="be65a-126">將 PKG 套件 `powershell-6.1.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="be65a-126">Download the PKG package `powershell-6.1.0-osx-x64.pkg`</span></span>
<span data-ttu-id="be65a-127">從[版本][]頁面下載到您的 macOS 電腦。</span><span class="sxs-lookup"><span data-stu-id="be65a-127">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="be65a-128">您可以按兩下檔案並依照提示執行作業，或從終端機安裝：</span><span class="sxs-lookup"><span data-stu-id="be65a-128">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

<span data-ttu-id="be65a-129">安裝 [OpenSSL](#install-openssl)，因為 PowerShell 遠端執行功能與 CIM 作業需要它。</span><span class="sxs-lookup"><span data-stu-id="be65a-129">Install [OpenSSL](#install-openssl) as this is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="be65a-130">二進位封存</span><span class="sxs-lookup"><span data-stu-id="be65a-130">Binary Archives</span></span>

<span data-ttu-id="be65a-131">macOS 平台有 PowerShell 二進位 `tar.gz` 封存，以啟用進階的部署案例。</span><span class="sxs-lookup"><span data-stu-id="be65a-131">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="be65a-132">解除安裝 macOS 上的二進位封存</span><span class="sxs-lookup"><span data-stu-id="be65a-132">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.1.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.1.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.1.0/pwsh /usr/local/bin/pwsh
```

<span data-ttu-id="be65a-133">安裝 [OpenSSL](#install-openssl)，因為 PowerShell 遠端執行功能與 CIM 作業需要它。</span><span class="sxs-lookup"><span data-stu-id="be65a-133">Install [OpenSSL](#install-openssl) as this is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="be65a-134">安裝相依性</span><span class="sxs-lookup"><span data-stu-id="be65a-134">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="be65a-135">安裝 XCode 命令列工具</span><span class="sxs-lookup"><span data-stu-id="be65a-135">Install XCode command line tools</span></span>

```shell
xcode-select -install
```

### <a name="install-openssl"></a><span data-ttu-id="be65a-136">安裝 OpenSSL</span><span class="sxs-lookup"><span data-stu-id="be65a-136">Install OpenSSL</span></span>

<span data-ttu-id="be65a-137">PowerShell 遠端執行功能與 CIM 作業需要 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="be65a-137">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>  <span data-ttu-id="be65a-138">您可以透過 MacPorts 或 Brew 來安裝。</span><span class="sxs-lookup"><span data-stu-id="be65a-138">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="be65a-139">透過 Brew 安裝 OpenSSL</span><span class="sxs-lookup"><span data-stu-id="be65a-139">Install OpenSSL via Brew</span></span>

<span data-ttu-id="be65a-140">如需 Brew 的相關資訊，請參閱[關於 Brew](#about-brew)。</span><span class="sxs-lookup"><span data-stu-id="be65a-140">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="be65a-141">執行 `brew install openssl` 以安裝 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="be65a-141">Run `brew install openssl` to install OpenSSL.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="be65a-142">透過 MacPorts 安裝 OpenSSL</span><span class="sxs-lookup"><span data-stu-id="be65a-142">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="be65a-143">安裝 [XCode 命令列工具](#install-xcode-command-line-tools)</span><span class="sxs-lookup"><span data-stu-id="be65a-143">Instal the [XCode command line tools](#install-xcode-command-line-tools)</span></span>
1. <span data-ttu-id="be65a-144">安裝 MacPorts。</span><span class="sxs-lookup"><span data-stu-id="be65a-144">Install MacPorts.</span></span>
   <span data-ttu-id="be65a-145">若需要指示，請參閱[安裝指南](https://guide.macports.org/chunked/installing.macports.html)。</span><span class="sxs-lookup"><span data-stu-id="be65a-145">See the [installation guide](https://guide.macports.org/chunked/installing.macports.html) if you need instructions.</span></span>
1. <span data-ttu-id="be65a-146">透過執行 `sudo port selfupdate` 以更新 MacPorts</span><span class="sxs-lookup"><span data-stu-id="be65a-146">Update MacPorts by running `sudo port selfupdate`</span></span>
1. <span data-ttu-id="be65a-147">透過執行 `sudo port upgrade outdated` 以升級 MacPorts 套件</span><span class="sxs-lookup"><span data-stu-id="be65a-147">Upgrade MacPorts packages by running `sudo port upgrade outdated`</span></span>
1. <span data-ttu-id="be65a-148">透過執行 `sudo port instal openssl` 以安裝 OpenSSL</span><span class="sxs-lookup"><span data-stu-id="be65a-148">Install OpenSSL by running by running `sudo port instal openssl`</span></span>
1. <span data-ttu-id="be65a-149">連結到程式庫，以便 PowerShell 可以使用它。</span><span class="sxs-lookup"><span data-stu-id="be65a-149">Link the libraries so that PowerShell can use it.</span></span>

```shell
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="be65a-150">解除安裝 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="be65a-150">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="be65a-151">如果您使用 Homebrew 安裝 PowerShell，解除安裝很簡單：</span><span class="sxs-lookup"><span data-stu-id="be65a-151">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="be65a-152">如已透過直接下載安裝 PowerShell，即必須手動移除 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="be65a-152">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="be65a-153">若要解除安裝其他的 PowerShell 路徑，請參閱本文件中的[路徑](#paths)一節，使用 `sudo rm` 移除所要的路徑。</span><span class="sxs-lookup"><span data-stu-id="be65a-153">To remove the additional PowerShell paths, please see the [paths](#paths) section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="be65a-154">如果使用 Homebrew 安裝，此即非必要。</span><span class="sxs-lookup"><span data-stu-id="be65a-154">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="be65a-155">路徑</span><span class="sxs-lookup"><span data-stu-id="be65a-155">Paths</span></span>

* <span data-ttu-id="be65a-156">`$PSHOME` 是 `/usr/local/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="be65a-156">`$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="be65a-157">會從 `~/.config/powershell/profile.ps1` 讀取使用者設定檔</span><span class="sxs-lookup"><span data-stu-id="be65a-157">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="be65a-158">會從 `$PSHOME/profile.ps1` 讀取預設設定檔</span><span class="sxs-lookup"><span data-stu-id="be65a-158">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="be65a-159">會從 `~/.local/share/powershell/Modules` 讀取使用者模組</span><span class="sxs-lookup"><span data-stu-id="be65a-159">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="be65a-160">會從 `/usr/local/share/powershell/Modules` 讀取共用的模組</span><span class="sxs-lookup"><span data-stu-id="be65a-160">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="be65a-161">會從 `$PSHOME/Modules` 讀取預設模組</span><span class="sxs-lookup"><span data-stu-id="be65a-161">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="be65a-162">PSReadline 記錄會記錄在 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="be65a-162">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="be65a-163">設定檔會採用 PowerShell 的每個主機設定。</span><span class="sxs-lookup"><span data-stu-id="be65a-163">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="be65a-164">因此預設主機特定設定檔便會存在於相同位置的 `Microsoft.PowerShell_profile.ps1`。</span><span class="sxs-lookup"><span data-stu-id="be65a-164">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="be65a-165">PowerShell 遵循 macOS 上的 [XDG 基底目錄規格][xdg-bds]。</span><span class="sxs-lookup"><span data-stu-id="be65a-165">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="be65a-166">因為 macOS 是 BSD 的衍生項，所以使用的前置詞是 `/usr/local` 而非 `/opt`。</span><span class="sxs-lookup"><span data-stu-id="be65a-166">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="be65a-167">因此，`$PSHOME` 是 `/usr/local/microsoft/powershell/6.1.0/`，而符號連結放置在 `/usr/local/bin/pwsh`。</span><span class="sxs-lookup"><span data-stu-id="be65a-167">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="be65a-168">其他資源</span><span class="sxs-lookup"><span data-stu-id="be65a-168">Additional Resources</span></span>

* <span data-ttu-id="be65a-169">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="be65a-169">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="be65a-170">[Homebrew Github 存放庫][GitHub]</span><span class="sxs-lookup"><span data-stu-id="be65a-170">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="be65a-171">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="be65a-171">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[版本]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
