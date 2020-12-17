---
title: 在 Linux 上安裝 PowerShell
description: 在各種 Linux 發行版本上安裝 PowerShell Core 的相關資訊
ms.date: 12/10/2020
ms.openlocfilehash: 1bf96bc6bfb3f6544d8a4fd5b287dd6d659691ec
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "97069864"
---
# <a name="installing-powershell-on-linux"></a><span data-ttu-id="44172-103">在 Linux 上安裝 PowerShell</span><span class="sxs-lookup"><span data-stu-id="44172-103">Installing PowerShell on Linux</span></span>

<span data-ttu-id="44172-104">GitHub [發行][]頁面上提供所有套件。</span><span class="sxs-lookup"><span data-stu-id="44172-104">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="44172-105">安裝套件之後，請從終端機執行 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="44172-105">After the package is installed, run `pwsh` from a terminal.</span></span> <span data-ttu-id="44172-106">若您已安裝[預覽版](#installing-preview-releases)，請執行 `pwsh-preview`。</span><span class="sxs-lookup"><span data-stu-id="44172-106">Run `pwsh-preview` if you installed a [Preview release](#installing-preview-releases).</span></span>

> [!NOTE]
> <span data-ttu-id="44172-107">PowerShell 7 是會移除 PowerShell Core 6.x 的就地升級。</span><span class="sxs-lookup"><span data-stu-id="44172-107">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="44172-108">`/usr/local/microsoft/powershell/6` 資料夾已由 `/usr/local/microsoft/powershell/7` 取代。</span><span class="sxs-lookup"><span data-stu-id="44172-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="44172-109">如果您需要與 PowerShell 7 並存執行 PowerShell 6，請使用[二進位封存](#binary-archives)方法來重新安裝 PowerShell 6。</span><span class="sxs-lookup"><span data-stu-id="44172-109">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

<span data-ttu-id="44172-110">針對未正式支援的 Linux 發佈，您可以嘗試使用 [PowerShell Snap 套件][snap]來安裝 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="44172-110">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="44172-111">您也可以直接使用 Linux [`tar.gz` 封存][tar]來嘗試部署 PowerShell 二進位檔，但您需要根據個別步驟中作業系統設定必要的相依性。</span><span class="sxs-lookup"><span data-stu-id="44172-111">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

[snap]: #snap-package
[tar]: #binary-archives

<!-- TODO: Update for supported releases v7.0 & v7.1 -->

<span data-ttu-id="44172-112">適用於 PowerShell 7.1 的正式支援平台版本</span><span class="sxs-lookup"><span data-stu-id="44172-112">Officially supported platform releases for PowerShell 7.1</span></span>

- <span data-ttu-id="44172-113">Ubuntu 16.04/18.04/20.04 (包含 ARM64)</span><span class="sxs-lookup"><span data-stu-id="44172-113">Ubuntu 16.04/18.04/20.04 (including ARM64)</span></span>
- <span data-ttu-id="44172-114">Ubuntu 19.10 (透過 Snap 套件)</span><span class="sxs-lookup"><span data-stu-id="44172-114">Ubuntu 19.10 (via Snap package)</span></span>
- <span data-ttu-id="44172-115">Debian 9/10</span><span class="sxs-lookup"><span data-stu-id="44172-115">Debian 9/10</span></span>
- <span data-ttu-id="44172-116">CentOS 與 RHEL 7/8</span><span class="sxs-lookup"><span data-stu-id="44172-116">CentOS and RHEL 7/8</span></span>
- <span data-ttu-id="44172-117">Fedora 30</span><span class="sxs-lookup"><span data-stu-id="44172-117">Fedora 30</span></span>
- <span data-ttu-id="44172-118">Alpine 3.11+ (包含 ARM64)</span><span class="sxs-lookup"><span data-stu-id="44172-118">Alpine 3.11+ (including ARM64)</span></span>

<span data-ttu-id="44172-119">適用於 PowerShell 7.0 的正式支援平台版本</span><span class="sxs-lookup"><span data-stu-id="44172-119">Officially supported platform releases for PowerShell 7.0</span></span>

- <span data-ttu-id="44172-120">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="44172-120">Ubuntu 16.04</span></span>
- <span data-ttu-id="44172-121">Ubuntu 18.04 與 20.04</span><span class="sxs-lookup"><span data-stu-id="44172-121">Ubuntu 18.04 and 20.04</span></span>
- <span data-ttu-id="44172-122">Debian 8</span><span class="sxs-lookup"><span data-stu-id="44172-122">Debian 8</span></span>
- <span data-ttu-id="44172-123">Debian 9</span><span class="sxs-lookup"><span data-stu-id="44172-123">Debian 9</span></span>
- <span data-ttu-id="44172-124">Debian 10</span><span class="sxs-lookup"><span data-stu-id="44172-124">Debian 10</span></span>
- <span data-ttu-id="44172-125">Alpine 3.9 與 3.10</span><span class="sxs-lookup"><span data-stu-id="44172-125">Alpine 3.9 and 3.10</span></span>
- <span data-ttu-id="44172-126">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="44172-126">CentOS 7</span></span>
- <span data-ttu-id="44172-127">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="44172-127">Red Hat Enterprise Linux (RHEL) 7</span></span>
- <span data-ttu-id="44172-128">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="44172-128">Fedora 28</span></span>
- <span data-ttu-id="44172-129">Fedora 29</span><span class="sxs-lookup"><span data-stu-id="44172-129">Fedora 29</span></span>
- <span data-ttu-id="44172-130">Fedora 30</span><span class="sxs-lookup"><span data-stu-id="44172-130">Fedora 30</span></span>
- <span data-ttu-id="44172-131">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="44172-131">openSUSE 42.3</span></span>
- <span data-ttu-id="44172-132">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="44172-132">openSUSE Leap 15</span></span>

<span data-ttu-id="44172-133">社群支援的版本</span><span class="sxs-lookup"><span data-stu-id="44172-133">Community supported releases</span></span>

- <span data-ttu-id="44172-134">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="44172-134">Ubuntu 18.10</span></span>
- <span data-ttu-id="44172-135">Ubuntu 19.10 與 20.10</span><span class="sxs-lookup"><span data-stu-id="44172-135">Ubuntu 19.10 and 20.10</span></span>
- <span data-ttu-id="44172-136">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="44172-136">Arch Linux</span></span>
- <span data-ttu-id="44172-137">Kali</span><span class="sxs-lookup"><span data-stu-id="44172-137">Kali</span></span>
- <span data-ttu-id="44172-138">Raspbian (實驗性)</span><span class="sxs-lookup"><span data-stu-id="44172-138">Raspbian (experimental)</span></span>

<span data-ttu-id="44172-139">替代安裝方法</span><span class="sxs-lookup"><span data-stu-id="44172-139">Alternate install methods</span></span>

- <span data-ttu-id="44172-140">Snap 套件</span><span class="sxs-lookup"><span data-stu-id="44172-140">Snap Package</span></span>
- <span data-ttu-id="44172-141">二進位封存</span><span class="sxs-lookup"><span data-stu-id="44172-141">Binary Archives</span></span>
- <span data-ttu-id="44172-142">.NET 全域工具</span><span class="sxs-lookup"><span data-stu-id="44172-142">.NET Global tool</span></span>

## <a name="ubuntu-1604"></a><span data-ttu-id="44172-143">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="44172-143">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="44172-144">透過套件存放庫安裝 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="44172-144">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="44172-145">適用於 Linux 的 PowerShell 會發佈到套件存放庫，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="44172-145">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="44172-146">慣用的方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="44172-146">The preferred method is as follows:</span></span>

```sh
# Update the list of packages
sudo apt-get update
# Install pre-requisite packages.
sudo apt-get install -y wget apt-transport-https software-properties-common
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb
# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb
# Update the list of packages after we added packages.microsoft.com
sudo apt-get update
# Install PowerShell
sudo apt-get install -y powershell
# Start PowerShell
pwsh
```

<span data-ttu-id="44172-147">以超級使用者的身分，註冊 Microsoft 存放庫一次。</span><span class="sxs-lookup"><span data-stu-id="44172-147">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="44172-148">註冊之後，您可以使用 `sudo apt-get install powershell` 來更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="44172-148">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="44172-149">透過直接下載安裝 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="44172-149">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="44172-150">將[發行][]頁面上的 Debian 套件 `powershell_7.1.0-1.ubuntu.16.04_amd64.deb` 下載至 Ubuntu 電腦。</span><span class="sxs-lookup"><span data-stu-id="44172-150">Download the Debian package `powershell_7.1.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="44172-151">然後，在終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="44172-151">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.1.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="44172-152">`dpkg -i` 命令因相依性不相符而失敗。</span><span class="sxs-lookup"><span data-stu-id="44172-152">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="44172-153">下一個命令 `apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。</span><span class="sxs-lookup"><span data-stu-id="44172-153">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="44172-154">解除安裝 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="44172-154">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="44172-155">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="44172-155">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="44172-156">透過套件存放庫安裝 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="44172-156">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="44172-157">適用於 Linux 的 PowerShell 會發佈到套件存放庫，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="44172-157">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="44172-158">慣用的方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="44172-158">The preferred method is as follows:</span></span>

```sh
# Update the list of packages
sudo apt-get update
# Install pre-requisite packages.
sudo apt-get install -y wget apt-transport-https software-properties-common
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb
# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb
# Update the list of products
sudo apt-get update
# Enable the "universe" repositories
sudo add-apt-repository universe
# Install PowerShell
sudo apt-get install -y powershell
# Start PowerShell
pwsh
```

<span data-ttu-id="44172-159">以超級使用者的身分，註冊 Microsoft 存放庫一次。</span><span class="sxs-lookup"><span data-stu-id="44172-159">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="44172-160">註冊之後，您可以使用 `sudo apt-get install powershell` 來更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="44172-160">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="44172-161">透過直接下載安裝 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="44172-161">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="44172-162">將[發行][]頁面上的 Debian 套件 `powershell_7.1.0-1.ubuntu.18.04_amd64.deb` 下載至 Ubuntu 電腦。</span><span class="sxs-lookup"><span data-stu-id="44172-162">Download the Debian package `powershell_7.1.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="44172-163">然後，在終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="44172-163">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.1.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="44172-164">`dpkg -i` 命令因相依性不相符而失敗。</span><span class="sxs-lookup"><span data-stu-id="44172-164">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="44172-165">下一個命令 `apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。</span><span class="sxs-lookup"><span data-stu-id="44172-165">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="44172-166">解除安裝 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="44172-166">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-2004"></a><span data-ttu-id="44172-167">Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="44172-167">Ubuntu 20.04</span></span>

### <a name="installation-via-package-repository---ubuntu-2004"></a><span data-ttu-id="44172-168">透過套件存放庫安裝 - Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="44172-168">Installation via Package Repository - Ubuntu 20.04</span></span>

<span data-ttu-id="44172-169">適用於 Linux 的 PowerShell 會發佈到套件存放庫，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="44172-169">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="44172-170">慣用的方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="44172-170">The preferred method is as follows:</span></span>

```sh
# Update the list of packages
sudo apt-get update
# Install pre-requisite packages.
sudo apt-get install -y wget apt-transport-https software-properties-common
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb
# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb
# Update the list of products
sudo apt-get update
# Enable the "universe" repositories
sudo add-apt-repository universe
# Install PowerShell
sudo apt-get install -y powershell
# Start PowerShell
pwsh
```

<span data-ttu-id="44172-171">以超級使用者的身分，註冊 Microsoft 存放庫一次。</span><span class="sxs-lookup"><span data-stu-id="44172-171">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="44172-172">註冊之後，您可以使用 `sudo apt-get install powershell` 來更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="44172-172">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-2004"></a><span data-ttu-id="44172-173">透過直接下載安裝 - Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="44172-173">Installation via Direct Download - Ubuntu 20.04</span></span>

<span data-ttu-id="44172-174">將[發行][]頁面上的 Debian 套件 `powershell_7.1.0-1.ubuntu.20.04_amd64.deb` 下載至 Ubuntu 電腦。</span><span class="sxs-lookup"><span data-stu-id="44172-174">Download the Debian package `powershell_7.1.0-1.ubuntu.20.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="44172-175">然後，在終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="44172-175">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.1.0-1.ubuntu.20.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="44172-176">`dpkg -i` 命令因相依性不相符而失敗。</span><span class="sxs-lookup"><span data-stu-id="44172-176">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="44172-177">下一個命令 `apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。</span><span class="sxs-lookup"><span data-stu-id="44172-177">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-2004"></a><span data-ttu-id="44172-178">解除安裝 - Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="44172-178">Uninstallation - Ubuntu 20.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="44172-179">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="44172-179">Ubuntu 18.10</span></span>

<span data-ttu-id="44172-180">安裝由 `snapd` 支援。</span><span class="sxs-lookup"><span data-stu-id="44172-180">Installation is supported via `snapd`.</span></span> <span data-ttu-id="44172-181">如需指示，請參閱 [Snap 套件][snap]。</span><span class="sxs-lookup"><span data-stu-id="44172-181">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="44172-182">Ubuntu 18.10 是[由社群支援](../powershell-support-lifecycle.md)的[過渡版本](https://www.ubuntu.com/about/release-cycle) (英文)。</span><span class="sxs-lookup"><span data-stu-id="44172-182">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1910-and-2010"></a><span data-ttu-id="44172-183">Ubuntu 19.10 與 20.10</span><span class="sxs-lookup"><span data-stu-id="44172-183">Ubuntu 19.10 and 20.10</span></span>

<span data-ttu-id="44172-184">安裝由 `snapd` 支援。</span><span class="sxs-lookup"><span data-stu-id="44172-184">Installation is supported via `snapd`.</span></span> <span data-ttu-id="44172-185">如需指示，請參閱 [Snap 套件][snap]。</span><span class="sxs-lookup"><span data-stu-id="44172-185">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="44172-186">Ubuntu 19.10 是[由社群支援](../powershell-support-lifecycle.md)的[過渡版本](https://www.ubuntu.com/about/release-cycle) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="44172-186">Ubuntu 19.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="debian-8"></a><span data-ttu-id="44172-187">Debian 8</span><span class="sxs-lookup"><span data-stu-id="44172-187">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="44172-188">透過套件存放庫安裝 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="44172-188">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="44172-189">適用於 Linux 的 PowerShell 會發佈到套件存放庫，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="44172-189">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="44172-190">慣用的方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="44172-190">The preferred method is as follows:</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install -y curl apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="44172-191">以超級使用者的身分，註冊 Microsoft 存放庫一次。</span><span class="sxs-lookup"><span data-stu-id="44172-191">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="44172-192">註冊之後，您可以使用 `sudo apt-get install powershell` 來更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="44172-192">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="44172-193">Debian 9</span><span class="sxs-lookup"><span data-stu-id="44172-193">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="44172-194">透過套件存放庫安裝 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="44172-194">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="44172-195">適用於 Linux 的 PowerShell 會發佈到套件存放庫，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="44172-195">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="44172-196">慣用的方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="44172-196">The preferred method is as follows:</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install -y curl gnupg apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="44172-197">以超級使用者的身分，註冊 Microsoft 存放庫一次。</span><span class="sxs-lookup"><span data-stu-id="44172-197">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="44172-198">註冊之後，您可以使用 `sudo apt-get install powershell` 來更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="44172-198">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="44172-199">透過直接下載安裝 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="44172-199">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="44172-200">將[發行][]頁面上的 Debian 套件 `powershell_7.1.0-1.debian.9_amd64.deb` 下載至 Debian 電腦。</span><span class="sxs-lookup"><span data-stu-id="44172-200">Download the Debian package `powershell_7.1.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="44172-201">然後，在終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="44172-201">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.1.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="44172-202">解除安裝 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="44172-202">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a><span data-ttu-id="44172-203">Debian 10</span><span class="sxs-lookup"><span data-stu-id="44172-203">Debian 10</span></span>

> [!NOTE]
> <span data-ttu-id="44172-204">只有 PowerShell Core 7.0 才支援 Debian 10。</span><span class="sxs-lookup"><span data-stu-id="44172-204">Debian 10 is only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository---debian-10"></a><span data-ttu-id="44172-205">透過套件存放庫安裝 - Debian 10</span><span class="sxs-lookup"><span data-stu-id="44172-205">Installation via Package Repository - Debian 10</span></span>

<span data-ttu-id="44172-206">適用於 Linux 的 PowerShell 會發佈到套件存放庫，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="44172-206">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="44172-207">慣用的方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="44172-207">The preferred method is as follows:</span></span>

```sh
# Download the Microsoft repository GPG keys
wget https://packages.microsoft.com/config/debian/10/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---debian-10"></a><span data-ttu-id="44172-208">透過直接下載安裝 - Debian 10</span><span class="sxs-lookup"><span data-stu-id="44172-208">Installation via Direct Download - Debian 10</span></span>

<span data-ttu-id="44172-209">將[發行][]頁面上的 tar.gz 套件 `powershell-7.1.0-linux-x64.tar.gz` 下載到 Debian 電腦：</span><span class="sxs-lookup"><span data-stu-id="44172-209">Download the tar.gz package `powershell-7.1.0-linux-x64.tar.gz` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="44172-210">然後，在終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="44172-210">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo apt-get update
# install the requirements
sudo apt-get install -y \
        less \
        locales \
        ca-certificates \
        libicu63 \
        libssl1.1 \
        libc6 \
        libgcc1 \
        libgssapi-krb5-2 \
        liblttng-ust0 \
        libstdc++6 \
        zlib1g \
        curl

# Download the powershell '.tar.gz' archive
curl -L  https://github.com/PowerShell/PowerShell/releases/download/v7.1.0/powershell-7.1.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

## <a name="alpine-39-and-310"></a><span data-ttu-id="44172-211">Alpine 3.9 與 3.10</span><span class="sxs-lookup"><span data-stu-id="44172-211">Alpine 3.9 and 3.10</span></span>

> [!NOTE]
> <span data-ttu-id="44172-212">只有 PowerShell 7.0 與更新版本才支援 Alpine 3.9 與 3.10。</span><span class="sxs-lookup"><span data-stu-id="44172-212">Alpine 3.9 and 3.10 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---alpine-39-and-310"></a><span data-ttu-id="44172-213">透過直接下載安裝 - Alpine 3.9 與 3.10</span><span class="sxs-lookup"><span data-stu-id="44172-213">Installation via Direct Download - Alpine 3.9 and 3.10</span></span>

<span data-ttu-id="44172-214">將[發行][]頁面上的 tar.gz 套件 `powershell-7.1.0-linux-alpine-x64.tar.gz` 下載到 Alpine 電腦：</span><span class="sxs-lookup"><span data-stu-id="44172-214">Download the tar.gz package `powershell-7.1.0-linux-alpine-x64.tar.gz` from the [releases][] page onto the Alpine machine.</span></span>

<span data-ttu-id="44172-215">然後，在終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="44172-215">Then, in the terminal, execute the following commands:</span></span>

```sh
# install the requirements
sudo apk add --no-cache \
    ca-certificates \
    less \
    ncurses-terminfo-base \
    krb5-libs \
    libgcc \
    libintl \
    libssl1.1 \
    libstdc++ \
    tzdata \
    userspace-rcu \
    zlib \
    icu-libs \
    curl

sudo apk -X https://dl-cdn.alpinelinux.org/alpine/edge/main add --no-cache \
    lttng-ust

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.1.0/powershell-7.1.0-linux-alpine-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

## <a name="centos-7"></a><span data-ttu-id="44172-216">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="44172-216">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="44172-217">此套件也適用於 Oracle Linux 7。</span><span class="sxs-lookup"><span data-stu-id="44172-217">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="44172-218">透過套件存放庫安裝 (慣用) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="44172-218">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="44172-219">適用於 Linux 的 PowerShell 會發佈到官方 Microsoft 存放庫，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="44172-219">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="44172-220">以超級使用者的身分，註冊 Microsoft 存放庫一次。</span><span class="sxs-lookup"><span data-stu-id="44172-220">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="44172-221">註冊之後，您可以使用 `sudo yum update powershell` 來更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="44172-221">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="44172-222">透過直接下載安裝 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="44172-222">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="44172-223">使用 [CentOS 7][]，將[發行][]頁面上的 RPM 套件 `powershell-7.1.0-1.rhel.7.x86_64.rpm` 下載至 CentOS 電腦。</span><span class="sxs-lookup"><span data-stu-id="44172-223">Using [CentOS 7][], download the RPM package `powershell-7.1.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="44172-224">然後，在終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="44172-224">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-7.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="44172-225">無需下載的中繼步驟便可安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="44172-225">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.1.0/powershell-7.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="44172-226">解除安裝 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="44172-226">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="44172-228">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="44172-228">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="44172-229">透過套件存放庫安裝 (慣用) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="44172-229">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="44172-230">適用於 Linux 的 PowerShell 會發佈到官方 Microsoft 存放庫，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="44172-230">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="44172-231">以超級使用者的身分，註冊 Microsoft 存放庫一次。</span><span class="sxs-lookup"><span data-stu-id="44172-231">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="44172-232">註冊之後，您可以使用 `sudo yum update powershell` 來更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="44172-232">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="44172-233">透過直接下載安裝 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="44172-233">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="44172-234">將[發行][]頁面上的 RPM 套件 `powershell-7.1.0-1.rhel.7.x86_64.rpm` 下載到 Red Hat Enterprise Linux 電腦。</span><span class="sxs-lookup"><span data-stu-id="44172-234">Download the RPM package `powershell-7.1.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="44172-235">然後，在終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="44172-235">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-7.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="44172-236">無需下載的中繼步驟便可安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="44172-236">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.1.0/powershell-7.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="44172-237">解除安裝 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="44172-237">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="44172-238">openSUSE</span><span class="sxs-lookup"><span data-stu-id="44172-238">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="44172-239">安裝 - openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="44172-239">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.1.0/powershell-7.1.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="44172-240">安裝 - openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="44172-240">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.1.0/powershell-7.1.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="44172-241">解除安裝 - openSUSE 42.3、openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="44172-241">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="44172-242">Fedora</span><span class="sxs-lookup"><span data-stu-id="44172-242">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="44172-243">只有 PowerShell Core 6.1 與更新版本才支援 Fedora 28。</span><span class="sxs-lookup"><span data-stu-id="44172-243">Fedora 28 is only supported in PowerShell 6.1 and newer.</span></span>

> [!NOTE]
> <span data-ttu-id="44172-244">只有 PowerShell 7.0 與更新版本才支援 Fedora 29 與 30。</span><span class="sxs-lookup"><span data-stu-id="44172-244">Fedora 29 and 30 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a><span data-ttu-id="44172-245">透過套件存放庫安裝 (慣用) - Fedora 28、29 與 30</span><span class="sxs-lookup"><span data-stu-id="44172-245">Installation via Package Repository (preferred) - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="44172-246">適用於 Linux 的 PowerShell 會發佈到官方 Microsoft 存放庫，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="44172-246">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf check-update

# Install a system component
sudo dnf install compat-openssl10

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a><span data-ttu-id="44172-247">透過直接下載安裝 - Fedora 28、29 與 30</span><span class="sxs-lookup"><span data-stu-id="44172-247">Installation via Direct Download - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="44172-248">將[發行][]頁面上的 RPM 套件 `powershell-7.1.0-1.rhel.7.x86_64.rpm` 下載到 Fedora 電腦。</span><span class="sxs-lookup"><span data-stu-id="44172-248">Download the RPM package `powershell-7.1.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="44172-249">然後，在終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="44172-249">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-7.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="44172-250">無需下載的中繼步驟便可安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="44172-250">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v7.1.0/powershell-7.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a><span data-ttu-id="44172-251">解除安裝 - Fedora 28、29 與 30</span><span class="sxs-lookup"><span data-stu-id="44172-251">Uninstallation - Fedora 28, 29, and 30</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="44172-252">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="44172-252">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="44172-253">「架構」支援並非由 Microsoft 正式支援，而是由社群維護。</span><span class="sxs-lookup"><span data-stu-id="44172-253">Arch support is not officially supported by Microsoft and is maintained by the community.</span></span>

<span data-ttu-id="44172-254">PowerShell 可從 [Arch Linux][] 使用者存放庫 (AUR) 取得。</span><span class="sxs-lookup"><span data-stu-id="44172-254">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

- <span data-ttu-id="44172-255">可以使用[最新的標記版本][arch-release]編譯</span><span class="sxs-lookup"><span data-stu-id="44172-255">It can be compiled with the [latest tagged release][arch-release]</span></span>
- <span data-ttu-id="44172-256">可以從[主機的最新認可][arch-git]編譯</span><span class="sxs-lookup"><span data-stu-id="44172-256">It can be compiled from the [latest commit to master][arch-git]</span></span>
- <span data-ttu-id="44172-257">可以使用[最新版本的二進位檔][arch-bin]安裝</span><span class="sxs-lookup"><span data-stu-id="44172-257">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="44172-258">AUR 中的套件由社群維護，沒有官方支援。</span><span class="sxs-lookup"><span data-stu-id="44172-258">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="44172-259">如需從 AUR 安裝套件的詳細資訊，請參閱 [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) 或[在 Docker 中使用 PowerShell](powershell-in-docker.md)。</span><span class="sxs-lookup"><span data-stu-id="44172-259">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or [Using PowerShell in Docker](powershell-in-docker.md).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="44172-261">Snap 套件</span><span class="sxs-lookup"><span data-stu-id="44172-261">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="44172-262">取得 snapd</span><span class="sxs-lookup"><span data-stu-id="44172-262">Getting snapd</span></span>

<span data-ttu-id="44172-263">必須有 `snapd` 才能執行 Snap。</span><span class="sxs-lookup"><span data-stu-id="44172-263">`snapd` is required to run snaps.</span></span> <span data-ttu-id="44172-264">請使用[這些指示](https://docs.snapcraft.io/core/install)確認您已安裝 `snapd`。</span><span class="sxs-lookup"><span data-stu-id="44172-264">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="44172-265">透過 Snap 安裝</span><span class="sxs-lookup"><span data-stu-id="44172-265">Installation via Snap</span></span>

<span data-ttu-id="44172-266">適用於 Linux 的 PowerShell 會發佈到 [Snap Store](https://snapcraft.io/store)，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="44172-266">PowerShell for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="44172-267">慣用的方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="44172-267">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="44172-268">若要安裝預覽版，請使用下列方法：</span><span class="sxs-lookup"><span data-stu-id="44172-268">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="44172-269">安裝之後，Snap 將會自動升級。</span><span class="sxs-lookup"><span data-stu-id="44172-269">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="44172-270">您可以使用 `sudo snap refresh powershell` 或 `sudo snap refresh powershell-preview` 觸發升級。</span><span class="sxs-lookup"><span data-stu-id="44172-270">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="44172-271">解除安裝</span><span class="sxs-lookup"><span data-stu-id="44172-271">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="44172-272">或</span><span class="sxs-lookup"><span data-stu-id="44172-272">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="44172-273">Kali</span><span class="sxs-lookup"><span data-stu-id="44172-273">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="44172-274">Kali 支援並非由 Microsoft 正式支援，而是由社群維護。</span><span class="sxs-lookup"><span data-stu-id="44172-274">Kali support is not officially supported by Microsoft and is maintained by the community.</span></span>

### <a name="installation---kali"></a><span data-ttu-id="44172-275">安裝 - Kali</span><span class="sxs-lookup"><span data-stu-id="44172-275">Installation - Kali</span></span>

```sh
# Install PowerShell package
apt update && apt -y install powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="44172-276">解除安裝 - Kali</span><span class="sxs-lookup"><span data-stu-id="44172-276">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt -y remove powershell
```

## <a name="raspbian"></a><span data-ttu-id="44172-277">Raspbian</span><span class="sxs-lookup"><span data-stu-id="44172-277">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="44172-278">Raspbian 支援為實驗性。</span><span class="sxs-lookup"><span data-stu-id="44172-278">Raspbian support is experimental.</span></span>

<span data-ttu-id="44172-279">目前只有 Raspbian Stretch 支援 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="44172-279">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="44172-280">CoreCLR 與 PowerShell 僅適用於 Pi 2 與 Pi 3 裝置，因為像 [Pi Zero](https://github.com/dotnet/coreclr/issues/10605) \(英文\) 這類的其他裝置，其處理器不受支援。</span><span class="sxs-lookup"><span data-stu-id="44172-280">CoreCLR and PowerShell will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="44172-281">下載 [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) 並遵循[安裝指示](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)來把它安裝到您的 Pi。</span><span class="sxs-lookup"><span data-stu-id="44172-281">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="44172-282">安裝 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="44172-282">Installation - Raspbian</span></span>

```sh
###################################
# Prerequisites

# Update package lists
sudo apt-get update

# Install libunwind8 and libssl1.0
# Regex is used to ensure that we do not install libssl1.0-dev, as it is a variant that is not required
sudo apt-get install '^libssl1.0.[0-9]$' libunwind8 -y

###################################
# Download and extract PowerShell

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v7.1.0/powershell-7.1.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-7.1.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="44172-283">或者，您可以建立一個符號連結來啟動 PowerShell，而無需指定 `pwsh` 二進位檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="44172-283">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="44172-284">解除安裝 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="44172-284">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="installing-preview-releases"></a><span data-ttu-id="44172-285">安裝預覽版本</span><span class="sxs-lookup"><span data-stu-id="44172-285">Installing Preview Releases</span></span>

<span data-ttu-id="44172-286">透過套件存放庫安裝 Linux 的 PowerShell Preview 版本時，套件名稱會從 `powershell` 變更為 `powershell-preview`。</span><span class="sxs-lookup"><span data-stu-id="44172-286">When installing a PowerShell Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="44172-287">透過直接下載的安裝不會變更，但檔案名稱除外。</span><span class="sxs-lookup"><span data-stu-id="44172-287">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="44172-288">下表包含使用各種套件管理員安裝穩定和預覽套件的命令：</span><span class="sxs-lookup"><span data-stu-id="44172-288">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

| <span data-ttu-id="44172-289">發行版本</span><span class="sxs-lookup"><span data-stu-id="44172-289">Distribution(s)</span></span> |            <span data-ttu-id="44172-290">穩定命令</span><span class="sxs-lookup"><span data-stu-id="44172-290">Stable Command</span></span>            |               <span data-ttu-id="44172-291">預覽命令</span><span class="sxs-lookup"><span data-stu-id="44172-291">Preview Command</span></span>                |
| --------------- | ------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="44172-292">Ubuntu、Debian</span><span class="sxs-lookup"><span data-stu-id="44172-292">Ubuntu, Debian</span></span>  | `sudo apt-get install -y powershell` | `sudo apt-get install -y powershell-preview` |
| <span data-ttu-id="44172-293">CentOS、RedHat</span><span class="sxs-lookup"><span data-stu-id="44172-293">CentOS, RedHat</span></span>  | `sudo yum install -y powershell`     | `sudo yum install -y powershell-preview`     |
| <span data-ttu-id="44172-294">Fedora</span><span class="sxs-lookup"><span data-stu-id="44172-294">Fedora</span></span>          | `sudo dnf install -y powershell`     | `sudo dnf install -y powershell-preview`     |

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="44172-295">安裝為 .NET 全域工具</span><span class="sxs-lookup"><span data-stu-id="44172-295">Install as a .NET Global tool</span></span>

<span data-ttu-id="44172-296">如果您已安裝 [.NET Core SDK](/dotnet/core/sdk)，就可以輕鬆地將 PowerShell 安裝為 [.NET 全域工具](/dotnet/core/tools/global-tools)。</span><span class="sxs-lookup"><span data-stu-id="44172-296">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="44172-297">Dotnet 工具安裝程式會將 `~/.dotnet/tools` 新增至您的 `PATH` 環境變數。</span><span class="sxs-lookup"><span data-stu-id="44172-297">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="44172-298">不過，目前執行的殼層沒有更新的 `PATH`。</span><span class="sxs-lookup"><span data-stu-id="44172-298">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="44172-299">您應該能夠透過輸入 `pwsh`，以從新的殼層啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="44172-299">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="44172-300">二進位封存</span><span class="sxs-lookup"><span data-stu-id="44172-300">Binary Archives</span></span>

<span data-ttu-id="44172-301">Linux 平台有 PowerShell 二進位 `tar.gz` 封存，以啟用進階的部署案例。</span><span class="sxs-lookup"><span data-stu-id="44172-301">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="44172-302">相依性</span><span class="sxs-lookup"><span data-stu-id="44172-302">Dependencies</span></span>

<span data-ttu-id="44172-303">PowerShell 會為所有 Linux 發行版本建置可攜式二進位檔。</span><span class="sxs-lookup"><span data-stu-id="44172-303">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="44172-304">但 .NET Core 執行階段在不同的發行版本需要不同的相依性，PowerShell 也一樣。</span><span class="sxs-lookup"><span data-stu-id="44172-304">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="44172-305">下圖顯示不同 Linux 發行版本上，正式支援的 .NET Core 2.0 相依性。</span><span class="sxs-lookup"><span data-stu-id="44172-305">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="44172-306">OS</span><span class="sxs-lookup"><span data-stu-id="44172-306">OS</span></span>                 | <span data-ttu-id="44172-307">相依性</span><span class="sxs-lookup"><span data-stu-id="44172-307">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="44172-308">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="44172-308">Ubuntu 16.04</span></span>       | <span data-ttu-id="44172-309">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="44172-309">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="44172-310">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu55</span><span class="sxs-lookup"><span data-stu-id="44172-310">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="44172-311">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="44172-311">Ubuntu 17.10</span></span>       | <span data-ttu-id="44172-312">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="44172-312">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="44172-313">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu57</span><span class="sxs-lookup"><span data-stu-id="44172-313">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="44172-314">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="44172-314">Ubuntu 18.04</span></span>       | <span data-ttu-id="44172-315">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="44172-315">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="44172-316">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu60</span><span class="sxs-lookup"><span data-stu-id="44172-316">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="44172-317">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="44172-317">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="44172-318">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="44172-318">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="44172-319">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52</span><span class="sxs-lookup"><span data-stu-id="44172-319">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="44172-320">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="44172-320">Debian 9 (Stretch)</span></span> | <span data-ttu-id="44172-321">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="44172-321">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="44172-322">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.2、libicu57</span><span class="sxs-lookup"><span data-stu-id="44172-322">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="44172-323">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="44172-323">CentOS 7</span></span> <br> <span data-ttu-id="44172-324">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="44172-324">Oracle Linux 7</span></span> <br> <span data-ttu-id="44172-325">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="44172-325">RHEL 7</span></span> | <span data-ttu-id="44172-326">libunwind、libcurl、openssl-libs、libicu</span><span class="sxs-lookup"><span data-stu-id="44172-326">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="44172-327">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="44172-327">openSUSE 42.3</span></span> | <span data-ttu-id="44172-328">libcurl4、libopenssl1_0_0、libicu52_1</span><span class="sxs-lookup"><span data-stu-id="44172-328">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="44172-329">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="44172-329">openSUSE Leap 15</span></span> | <span data-ttu-id="44172-330">libcurl4、libopenssl1_0_0、libicu60_2</span><span class="sxs-lookup"><span data-stu-id="44172-330">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="44172-331">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="44172-331">Fedora 27</span></span> <br> <span data-ttu-id="44172-332">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="44172-332">Fedora 28</span></span> | <span data-ttu-id="44172-333">libunwind、libcurl、openssl-libs、libicu、compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="44172-333">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="44172-334">若要在未正式支援的 Linux 發行版本上部署 PowerShell 二進位檔，您需要在個別步驟中為目標作業系統安裝必要的相依性。</span><span class="sxs-lookup"><span data-stu-id="44172-334">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="44172-335">例如，[Amazon Linux dockerfile][amazon-dockerfile] 會先安裝相依性，再解壓縮 Linux `tar.gz` 封存。</span><span class="sxs-lookup"><span data-stu-id="44172-335">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="44172-336">安裝 - 二進位封存</span><span class="sxs-lookup"><span data-stu-id="44172-336">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="44172-337">Linux</span><span class="sxs-lookup"><span data-stu-id="44172-337">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.1.0/powershell-7.1.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="44172-338">解除安裝二進位封存</span><span class="sxs-lookup"><span data-stu-id="44172-338">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="44172-339">路徑</span><span class="sxs-lookup"><span data-stu-id="44172-339">Paths</span></span>

- <span data-ttu-id="44172-340">`$PSHOME` 是 `/opt/microsoft/powershell/7/`</span><span class="sxs-lookup"><span data-stu-id="44172-340">`$PSHOME` is `/opt/microsoft/powershell/7/`</span></span>
- <span data-ttu-id="44172-341">會從 `~/.config/powershell/profile.ps1` 讀取使用者設定檔</span><span class="sxs-lookup"><span data-stu-id="44172-341">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
- <span data-ttu-id="44172-342">會從 `$PSHOME/profile.ps1` 讀取預設設定檔</span><span class="sxs-lookup"><span data-stu-id="44172-342">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
- <span data-ttu-id="44172-343">會從 `~/.local/share/powershell/Modules` 讀取使用者模組</span><span class="sxs-lookup"><span data-stu-id="44172-343">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="44172-344">會從 `/usr/local/share/powershell/Modules` 讀取共用的模組</span><span class="sxs-lookup"><span data-stu-id="44172-344">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
- <span data-ttu-id="44172-345">會從 `$PSHOME/Modules` 讀取預設模組</span><span class="sxs-lookup"><span data-stu-id="44172-345">Default modules will be read from `$PSHOME/Modules`</span></span>
- <span data-ttu-id="44172-346">PSReadline 記錄會記錄在 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="44172-346">PSReadLine history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="44172-347">設定檔會遵循 PowerShell 的每個主控件設定，讓預設主控件特定設定檔存在於相同位置的 `Microsoft.PowerShell_profile.ps1`。</span><span class="sxs-lookup"><span data-stu-id="44172-347">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="44172-348">PowerShell 遵循 Linux 上的 [XDG 基底目錄規格][xdg-bds]。</span><span class="sxs-lookup"><span data-stu-id="44172-348">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

## <a name="installation-support"></a><span data-ttu-id="44172-349">安裝支援</span><span class="sxs-lookup"><span data-stu-id="44172-349">Installation support</span></span>

<span data-ttu-id="44172-350">Microsoft 支援此文件中的安裝方法。</span><span class="sxs-lookup"><span data-stu-id="44172-350">Microsoft supports the installation methods in this document.</span></span> <span data-ttu-id="44172-351">其他來源可能會提供其他安裝方法。</span><span class="sxs-lookup"><span data-stu-id="44172-351">There may be other methods of installation available from other sources.</span></span> <span data-ttu-id="44172-352">雖然那些工具與方法都有用，但 Microsoft 無法支援那些方法。</span><span class="sxs-lookup"><span data-stu-id="44172-352">While those tools and methods may work, Microsoft cannot support those methods.</span></span>

<!-- link references -->
[發行]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
[distros]: https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md#linux
[Distribution Support Request]: https://github.com/PowerShell/PowerShell/issues/new?assignees=&labels=Distribution-Request&template=Distribution_Request.md&title=Distribution+Support+Request
