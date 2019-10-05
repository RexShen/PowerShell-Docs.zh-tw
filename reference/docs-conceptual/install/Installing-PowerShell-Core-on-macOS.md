---
title: 在 macOS 上安裝 PowerShell Core
description: 在 macOS 上安裝 PowerShell Core 的相關資訊
ms.date: 12/12/2018
ms.openlocfilehash: a53cb5b7e159635dac45fb9ca3df28e86dffc653
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71325268"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="9e89c-103">在 macOS 上安裝 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="9e89c-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="9e89c-104">PowerShell Core 支援 macOS 10.12 和更版本。</span><span class="sxs-lookup"><span data-stu-id="9e89c-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="9e89c-105">GitHub [版本][]頁面上提供所有套件。</span><span class="sxs-lookup"><span data-stu-id="9e89c-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="9e89c-106">安裝套件之後，請從終端機執行 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="9e89c-106">After the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="about-brew"></a><span data-ttu-id="9e89c-107">關於 Brew</span><span class="sxs-lookup"><span data-stu-id="9e89c-107">About Brew</span></span>

<span data-ttu-id="9e89c-108">[Homebrew][brew] 是 macOS 首選的套件管理員。</span><span class="sxs-lookup"><span data-stu-id="9e89c-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="9e89c-109">如果找不到 `brew` 命令，您需要遵循[指示][brew]安裝 Homebrew。</span><span class="sxs-lookup"><span data-stu-id="9e89c-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>
<span data-ttu-id="9e89c-110">或者，您也可透過[直接下載](#installation-via-direct-download)或[二進位封存](#binary-archives)來安裝 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="9e89c-110">Otherwise you may install PowerShell via [Direct Download](#installation-via-direct-download) or from [Binary Archives](#binary-archives).</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="9e89c-111">在 macOS 10.12 或更高版本上透過 Homebrew 安裝最新的穩定版本</span><span class="sxs-lookup"><span data-stu-id="9e89c-111">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="9e89c-112">如需 Brew 的相關資訊，請參閱[關於 Brew](#about-brew)。</span><span class="sxs-lookup"><span data-stu-id="9e89c-112">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="9e89c-113">現在，您可以安裝 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="9e89c-113">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="9e89c-114">最後，確認您的安裝可以正常執行：</span><span class="sxs-lookup"><span data-stu-id="9e89c-114">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="9e89c-115">當新的 PowerShell 版本發行時，請更新 Homebrew 的公式並升級 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="9e89c-115">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="9e89c-116">您可以從 PowerShell (pwsh) 主機內呼叫上述命令，但必須結束並重新啟動 PowerShell 殼層，才能完成升級並重新整理 `$PSVersionTable` 中顯示的值。</span><span class="sxs-lookup"><span data-stu-id="9e89c-116">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="9e89c-117">在 macOS 10.12 或更高版本上透過 Homebrew 安裝最新的預覽版本</span><span class="sxs-lookup"><span data-stu-id="9e89c-117">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="9e89c-118">如需 Brew 的相關資訊，請參閱[關於 Brew](#about-brew)。</span><span class="sxs-lookup"><span data-stu-id="9e89c-118">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="9e89c-119">安裝 Homebrew 之後，您可以安裝 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="9e89c-119">After you've installed Homebrew, you can install PowerShell.</span></span>
<span data-ttu-id="9e89c-120">首先，安裝 [Cask-Versions][cask-versions] 套件，它可讓您安裝 Cask 套件的替代版本：</span><span class="sxs-lookup"><span data-stu-id="9e89c-120">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="9e89c-121">現在，您可以安裝 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="9e89c-121">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="9e89c-122">最後，確認您的安裝可以正常執行：</span><span class="sxs-lookup"><span data-stu-id="9e89c-122">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="9e89c-123">當新的 PowerShell 版本發行時，請更新 Homebrew 的公式並升級 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="9e89c-123">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="9e89c-124">上述命令可從 PowerShell (pwsh) 主機內呼叫，但 PowerShell 殼層必須結束並重新啟動，才能完成升級。</span><span class="sxs-lookup"><span data-stu-id="9e89c-124">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="9e89c-125">並重新整理 `$PSVersionTable` 中顯示的值。</span><span class="sxs-lookup"><span data-stu-id="9e89c-125">and refresh the values shown in `$PSVersionTable`.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="9e89c-126">透過直接下載來安裝</span><span class="sxs-lookup"><span data-stu-id="9e89c-126">Installation via Direct Download</span></span>

<span data-ttu-id="9e89c-127">將 PKG 套件 `powershell-6.2.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="9e89c-127">Download the PKG package `powershell-6.2.0-osx-x64.pkg`</span></span>
<span data-ttu-id="9e89c-128">從[版本][]頁面下載到您的 macOS 電腦。</span><span class="sxs-lookup"><span data-stu-id="9e89c-128">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="9e89c-129">您可以按兩下檔案並依照提示執行作業，或從終端機安裝：</span><span class="sxs-lookup"><span data-stu-id="9e89c-129">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.2.0-osx-x64.pkg -target /
```

<span data-ttu-id="9e89c-130">安裝 [OpenSSL](#install-openssl)。</span><span class="sxs-lookup"><span data-stu-id="9e89c-130">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="9e89c-131">PowerShell 遠端執行功能與 CIM 作業需要 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="9e89c-131">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="9e89c-132">二進位封存</span><span class="sxs-lookup"><span data-stu-id="9e89c-132">Binary Archives</span></span>

<span data-ttu-id="9e89c-133">macOS 平台有 PowerShell 二進位 `tar.gz` 封存，以啟用進階的部署案例。</span><span class="sxs-lookup"><span data-stu-id="9e89c-133">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="9e89c-134">解除安裝 macOS 上的二進位封存</span><span class="sxs-lookup"><span data-stu-id="9e89c-134">Installing binary archives on macOS</span></span>

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

<span data-ttu-id="9e89c-135">安裝 [OpenSSL](#install-openssl)。</span><span class="sxs-lookup"><span data-stu-id="9e89c-135">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="9e89c-136">PowerShell 遠端執行功能與 CIM 作業需要 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="9e89c-136">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="9e89c-137">安裝相依性</span><span class="sxs-lookup"><span data-stu-id="9e89c-137">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="9e89c-138">安裝 XCode 命令列工具</span><span class="sxs-lookup"><span data-stu-id="9e89c-138">Install XCode command-line tools</span></span>

```sh
xcode-select --install
```

### <a name="install-openssl"></a><span data-ttu-id="9e89c-139">安裝 OpenSSL</span><span class="sxs-lookup"><span data-stu-id="9e89c-139">Install OpenSSL</span></span>

<span data-ttu-id="9e89c-140">PowerShell 遠端執行功能與 CIM 作業需要 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="9e89c-140">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="9e89c-141">您可以透過 MacPorts 或 Brew 來安裝。</span><span class="sxs-lookup"><span data-stu-id="9e89c-141">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="9e89c-142">透過 Brew 安裝 OpenSSL</span><span class="sxs-lookup"><span data-stu-id="9e89c-142">Install OpenSSL via Brew</span></span>

<span data-ttu-id="9e89c-143">如需 Brew 的相關資訊，請參閱[關於 Brew](#about-brew)。</span><span class="sxs-lookup"><span data-stu-id="9e89c-143">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="9e89c-144">若要安裝 OpenSSL，請執行 `brew install openssl`。</span><span class="sxs-lookup"><span data-stu-id="9e89c-144">To install OpenSSL, run `brew install openssl`.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="9e89c-145">透過 MacPorts 安裝 OpenSSL</span><span class="sxs-lookup"><span data-stu-id="9e89c-145">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="9e89c-146">安裝 [XCode 命令列工具](#install-xcode-command-line-tools)。</span><span class="sxs-lookup"><span data-stu-id="9e89c-146">Install the [XCode command line tools](#install-xcode-command-line-tools).</span></span>
1. <span data-ttu-id="9e89c-147">安裝 MacPorts。</span><span class="sxs-lookup"><span data-stu-id="9e89c-147">Install MacPorts.</span></span>
   <span data-ttu-id="9e89c-148">若需要指示，請參閱[安裝指南](https://guide.macports.org/chunked/installing.macports.html) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="9e89c-148">If you need instructions, refer to the [installation guide](https://guide.macports.org/chunked/installing.macports.html).</span></span>
1. <span data-ttu-id="9e89c-149">透過執行 `sudo port selfupdate` 來更新 MacPorts。</span><span class="sxs-lookup"><span data-stu-id="9e89c-149">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="9e89c-150">透過執行 `sudo port upgrade outdated` 來升級 MacPorts 套件。</span><span class="sxs-lookup"><span data-stu-id="9e89c-150">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="9e89c-151">透過執行 `sudo port install openssl` 以安裝 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="9e89c-151">Install OpenSSL by running `sudo port install openssl`.</span></span>
1. <span data-ttu-id="9e89c-152">連結程式庫，以供 PowerShell 使用它們：</span><span class="sxs-lookup"><span data-stu-id="9e89c-152">Link the libraries to make them available to PowerShell:</span></span>

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="9e89c-153">解除安裝 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="9e89c-153">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="9e89c-154">如果您使用 Homebrew 安裝 PowerShell，請使用下列命令解除安裝：</span><span class="sxs-lookup"><span data-stu-id="9e89c-154">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="9e89c-155">如已透過直接下載安裝 PowerShell，即必須手動移除 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="9e89c-155">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="9e89c-156">若要移除其他的 PowerShell 路徑，請參閱此文件中的[路徑](#paths)一節，並使用 `sudo rm` 移除路徑。</span><span class="sxs-lookup"><span data-stu-id="9e89c-156">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="9e89c-157">如果使用 Homebrew 安裝，此即非必要。</span><span class="sxs-lookup"><span data-stu-id="9e89c-157">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="9e89c-158">路徑</span><span class="sxs-lookup"><span data-stu-id="9e89c-158">Paths</span></span>

* <span data-ttu-id="9e89c-159">`$PSHOME` 是 `/usr/local/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="9e89c-159">`$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="9e89c-160">會從 `~/.config/powershell/profile.ps1` 讀取使用者設定檔</span><span class="sxs-lookup"><span data-stu-id="9e89c-160">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="9e89c-161">會從 `$PSHOME/profile.ps1` 讀取預設設定檔</span><span class="sxs-lookup"><span data-stu-id="9e89c-161">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="9e89c-162">會從 `~/.local/share/powershell/Modules` 讀取使用者模組</span><span class="sxs-lookup"><span data-stu-id="9e89c-162">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="9e89c-163">會從 `/usr/local/share/powershell/Modules` 讀取共用的模組</span><span class="sxs-lookup"><span data-stu-id="9e89c-163">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="9e89c-164">會從 `$PSHOME/Modules` 讀取預設模組</span><span class="sxs-lookup"><span data-stu-id="9e89c-164">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="9e89c-165">PSReadline 記錄會記錄在 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="9e89c-165">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="9e89c-166">設定檔會採用 PowerShell 的每個主機設定。</span><span class="sxs-lookup"><span data-stu-id="9e89c-166">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="9e89c-167">因此預設主機特定設定檔便會存在於相同位置的 `Microsoft.PowerShell_profile.ps1`。</span><span class="sxs-lookup"><span data-stu-id="9e89c-167">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="9e89c-168">PowerShell 遵循 macOS 上的 [XDG 基底目錄規格][xdg-bds]。</span><span class="sxs-lookup"><span data-stu-id="9e89c-168">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="9e89c-169">因為 macOS 是 BSD 的衍生項，所以使用的前置詞是 `/usr/local` 而非 `/opt`。</span><span class="sxs-lookup"><span data-stu-id="9e89c-169">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="9e89c-170">因此，`$PSHOME` 是 `/usr/local/microsoft/powershell/6.2.0/`，而符號連結放置在 `/usr/local/bin/pwsh`。</span><span class="sxs-lookup"><span data-stu-id="9e89c-170">So, `$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="9e89c-171">其他資源</span><span class="sxs-lookup"><span data-stu-id="9e89c-171">Additional Resources</span></span>

* <span data-ttu-id="9e89c-172">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="9e89c-172">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="9e89c-173">[Homebrew Github 存放庫][GitHub]</span><span class="sxs-lookup"><span data-stu-id="9e89c-173">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="9e89c-174">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="9e89c-174">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[版本]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
