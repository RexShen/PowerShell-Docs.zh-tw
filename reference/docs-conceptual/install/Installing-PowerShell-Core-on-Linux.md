---
title: 在 Linux 上安裝 PowerShell
description: 在各種 Linux 發行版本上安裝 PowerShell Core 的相關資訊
ms.date: 05/21/2020
ms.openlocfilehash: b87827635cc66de3714100dfac6de56860495d79
ms.sourcegitcommit: fd6a33b9fac973b3554fecfea7f51475e650a606
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83791510"
---
# <a name="installing-powershell-on-linux"></a><span data-ttu-id="3cc1c-103">在 Linux 上安裝 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3cc1c-103">Installing PowerShell on Linux</span></span>

<span data-ttu-id="3cc1c-104">GitHub [發行][]頁面上提供所有套件。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-104">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="3cc1c-105">安裝套件之後，請從終端機執行 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-105">After the package is installed, run `pwsh` from a terminal.</span></span> <span data-ttu-id="3cc1c-106">若您已安裝[預覽版](#installing-preview-releases)，請執行 `pwsh-preview`。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-106">Run `pwsh-preview` if you installed a [Preview release](#installing-preview-releases).</span></span>

> [!NOTE]
> <span data-ttu-id="3cc1c-107">PowerShell 7 是會移除 PowerShell Core 6.x 的就地升級。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-107">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="3cc1c-108">`/usr/local/microsoft/powershell/6` 資料夾已由 `/usr/local/microsoft/powershell/7` 取代。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="3cc1c-109">如果您需要與 PowerShell 7 並存執行 PowerShell 6，請使用[二進位封存](#binary-archives)方法來重新安裝 PowerShell 6。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-109">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

<span data-ttu-id="3cc1c-110">針對未正式支援的 Linux 發佈，您可以嘗試使用 [PowerShell Snap 套件][snap]來安裝 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-110">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="3cc1c-111">您也可以直接使用 Linux [`tar.gz` 封存][tar]來嘗試部署 PowerShell 二進位檔，但您需要根據個別步驟中作業系統設定必要的相依性。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-111">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

[snap]: #snap-package
[tar]: #binary-archives

<span data-ttu-id="3cc1c-112">正式支援的版本</span><span class="sxs-lookup"><span data-stu-id="3cc1c-112">Officially supported releases</span></span>

- <span data-ttu-id="3cc1c-113">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="3cc1c-113">Ubuntu 16.04</span></span>
- <span data-ttu-id="3cc1c-114">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="3cc1c-114">Ubuntu 18.04</span></span>
- <span data-ttu-id="3cc1c-115">Debian 8</span><span class="sxs-lookup"><span data-stu-id="3cc1c-115">Debian 8</span></span>
- <span data-ttu-id="3cc1c-116">Debian 9</span><span class="sxs-lookup"><span data-stu-id="3cc1c-116">Debian 9</span></span>
- <span data-ttu-id="3cc1c-117">Debian 10</span><span class="sxs-lookup"><span data-stu-id="3cc1c-117">Debian 10</span></span>
- <span data-ttu-id="3cc1c-118">Alpine 3.9 與 3.10</span><span class="sxs-lookup"><span data-stu-id="3cc1c-118">Alpine 3.9 and 3.10</span></span>
- <span data-ttu-id="3cc1c-119">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3cc1c-119">CentOS 7</span></span>
- <span data-ttu-id="3cc1c-120">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="3cc1c-120">Red Hat Enterprise Linux (RHEL) 7</span></span>
- <span data-ttu-id="3cc1c-121">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="3cc1c-121">Fedora 28</span></span>
- <span data-ttu-id="3cc1c-122">Fedora 29</span><span class="sxs-lookup"><span data-stu-id="3cc1c-122">Fedora 29</span></span>
- <span data-ttu-id="3cc1c-123">Fedora 30</span><span class="sxs-lookup"><span data-stu-id="3cc1c-123">Fedora 30</span></span>
- <span data-ttu-id="3cc1c-124">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="3cc1c-124">openSUSE 42.3</span></span>
- <span data-ttu-id="3cc1c-125">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="3cc1c-125">openSUSE Leap 15</span></span>

<span data-ttu-id="3cc1c-126">社群支援的版本</span><span class="sxs-lookup"><span data-stu-id="3cc1c-126">Community supported releases</span></span>

- <span data-ttu-id="3cc1c-127">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="3cc1c-127">Ubuntu 18.10</span></span>
- <span data-ttu-id="3cc1c-128">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="3cc1c-128">Ubuntu 19.04</span></span>
- <span data-ttu-id="3cc1c-129">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="3cc1c-129">Arch Linux</span></span>
- <span data-ttu-id="3cc1c-130">Kali</span><span class="sxs-lookup"><span data-stu-id="3cc1c-130">Kali</span></span>
- <span data-ttu-id="3cc1c-131">Raspbian (實驗性)</span><span class="sxs-lookup"><span data-stu-id="3cc1c-131">Raspbian (experimental)</span></span>

<span data-ttu-id="3cc1c-132">替代安裝方法</span><span class="sxs-lookup"><span data-stu-id="3cc1c-132">Alternate install methods</span></span>

- <span data-ttu-id="3cc1c-133">Snap 套件</span><span class="sxs-lookup"><span data-stu-id="3cc1c-133">Snap Package</span></span>
- <span data-ttu-id="3cc1c-134">二進位封存</span><span class="sxs-lookup"><span data-stu-id="3cc1c-134">Binary Archives</span></span>
- <span data-ttu-id="3cc1c-135">.NET 全域工具</span><span class="sxs-lookup"><span data-stu-id="3cc1c-135">.NET Global tool</span></span>

<span data-ttu-id="3cc1c-136">目前不支援</span><span class="sxs-lookup"><span data-stu-id="3cc1c-136">Not currently supported</span></span>

- <span data-ttu-id="3cc1c-137">Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="3cc1c-137">Ubuntu 20.04</span></span>

## <a name="ubuntu-1604"></a><span data-ttu-id="3cc1c-138">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="3cc1c-138">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="3cc1c-139">透過套件存放庫安裝 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="3cc1c-139">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="3cc1c-140">適用於 Linux 的 PowerShell 會發佈到套件存放庫，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-140">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="3cc1c-141">慣用的方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="3cc1c-141">The preferred method is as follows:</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="3cc1c-142">以超級使用者的身分，註冊 Microsoft 存放庫一次。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-142">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="3cc1c-143">註冊之後，您可以使用 `sudo apt-get upgrade powershell` 來更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-143">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="3cc1c-144">透過直接下載安裝 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="3cc1c-144">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="3cc1c-145">將[發行][]頁面上的 Debian 套件 `powershell-lts_7.0.1-1.ubuntu.16.04_amd64.deb` 下載至 Ubuntu 電腦。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-145">Download the Debian package `powershell-lts_7.0.1-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="3cc1c-146">然後，在終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="3cc1c-146">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.1-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="3cc1c-147">`dpkg -i` 命令因相依性不相符而失敗。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-147">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="3cc1c-148">下一個命令 `apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-148">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="3cc1c-149">解除安裝 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="3cc1c-149">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="3cc1c-150">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="3cc1c-150">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="3cc1c-151">透過套件存放庫安裝 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="3cc1c-151">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="3cc1c-152">適用於 Linux 的 PowerShell 會發佈到套件存放庫，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-152">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="3cc1c-153">慣用的方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="3cc1c-153">The preferred method is as follows:</span></span>

```sh
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

<span data-ttu-id="3cc1c-154">以超級使用者的身分，註冊 Microsoft 存放庫一次。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-154">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="3cc1c-155">註冊之後，您可以使用 `sudo apt-get upgrade powershell` 來更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-155">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="3cc1c-156">透過直接下載安裝 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="3cc1c-156">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="3cc1c-157">將[發行][]頁面上的 Debian 套件 `powershell-lts_7.0.1-1.ubuntu.18.04_amd64.deb` 下載至 Ubuntu 電腦。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-157">Download the Debian package `powershell-lts_7.0.1-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="3cc1c-158">然後，在終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="3cc1c-158">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.1-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="3cc1c-159">`dpkg -i` 命令因相依性不相符而失敗。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-159">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="3cc1c-160">下一個命令 `apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-160">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="3cc1c-161">解除安裝 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="3cc1c-161">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="3cc1c-162">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="3cc1c-162">Ubuntu 18.10</span></span>

<span data-ttu-id="3cc1c-163">安裝由 `snapd` 支援。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-163">Installation is supported via `snapd`.</span></span> <span data-ttu-id="3cc1c-164">如需指示，請參閱 [Snap 套件][snap]。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-164">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="3cc1c-165">Ubuntu 18.10 是[由社群支援](../powershell-support-lifecycle.md)的[過渡版本](https://www.ubuntu.com/about/release-cycle) (英文)。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-165">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1904"></a><span data-ttu-id="3cc1c-166">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="3cc1c-166">Ubuntu 19.04</span></span>

<span data-ttu-id="3cc1c-167">安裝由 `snapd` 支援。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-167">Installation is supported via `snapd`.</span></span> <span data-ttu-id="3cc1c-168">如需指示，請參閱 [Snap 套件][snap]。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-168">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="3cc1c-169">因為 Ubuntu 19.04 是[由社群支援](../powershell-support-lifecycle.md)的[過渡版本](https://www.ubuntu.com/about/release-cycle) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-169">Ubuntu 19.04 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-2004"></a><span data-ttu-id="3cc1c-170">Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="3cc1c-170">Ubuntu 20.04</span></span>

<span data-ttu-id="3cc1c-171">Ubuntu 20.04 為 LTS 版本。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-171">Ubuntu 20.04 is an LTS release.</span></span> <span data-ttu-id="3cc1c-172">PowerShell 目前不支援此版本。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-172">PowerShell does not currently support this version.</span></span> <span data-ttu-id="3cc1c-173">PowerShell 7.1 版正考慮增加對此版本的支援。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-173">Support for this version is being considered for the PowerShell 7.1 release.</span></span> <span data-ttu-id="3cc1c-174">如果您想支援 Ubuntu 20.04.，請附議此[要求](https://github.com/PowerShell/PowerShell/issues/12626)。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-174">Please upvote this [request](https://github.com/PowerShell/PowerShell/issues/12626) if you would like support for Ubuntu 20.04.</span></span>

## <a name="debian-8"></a><span data-ttu-id="3cc1c-175">Debian 8</span><span class="sxs-lookup"><span data-stu-id="3cc1c-175">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="3cc1c-176">透過套件存放庫安裝 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="3cc1c-176">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="3cc1c-177">適用於 Linux 的 PowerShell 會發佈到套件存放庫，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-177">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="3cc1c-178">慣用的方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="3cc1c-178">The preferred method is as follows:</span></span>

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

<span data-ttu-id="3cc1c-179">以超級使用者的身分，註冊 Microsoft 存放庫一次。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-179">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="3cc1c-180">註冊之後，您可以使用 `sudo apt-get upgrade powershell` 來更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-180">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="3cc1c-181">Debian 9</span><span class="sxs-lookup"><span data-stu-id="3cc1c-181">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="3cc1c-182">透過套件存放庫安裝 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="3cc1c-182">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="3cc1c-183">適用於 Linux 的 PowerShell 會發佈到套件存放庫，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-183">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="3cc1c-184">慣用的方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="3cc1c-184">The preferred method is as follows:</span></span>

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

<span data-ttu-id="3cc1c-185">以超級使用者的身分，註冊 Microsoft 存放庫一次。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-185">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="3cc1c-186">註冊之後，您可以使用 `sudo apt-get upgrade powershell` 來更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-186">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="3cc1c-187">透過直接下載安裝 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="3cc1c-187">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="3cc1c-188">將[發行][]頁面上的 Debian 套件 `powershell-lts_7.0.1-1.debian.9_amd64.deb` 下載至 Debian 電腦。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-188">Download the Debian package `powershell-lts_7.0.1-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="3cc1c-189">然後，在終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="3cc1c-189">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.1-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="3cc1c-190">解除安裝 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="3cc1c-190">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a><span data-ttu-id="3cc1c-191">Debian 10</span><span class="sxs-lookup"><span data-stu-id="3cc1c-191">Debian 10</span></span>

> [!NOTE]
> <span data-ttu-id="3cc1c-192">只有 PowerShell Core 7.0 才支援 Debian 10。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-192">Debian 10 is only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository---debian-10"></a><span data-ttu-id="3cc1c-193">透過套件存放庫安裝 - Debian 10</span><span class="sxs-lookup"><span data-stu-id="3cc1c-193">Installation via Package Repository - Debian 10</span></span>

<span data-ttu-id="3cc1c-194">適用於 Linux 的 PowerShell 會發佈到套件存放庫，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-194">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="3cc1c-195">慣用的方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="3cc1c-195">The preferred method is as follows:</span></span>

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

### <a name="installation-via-direct-download---debian-10"></a><span data-ttu-id="3cc1c-196">透過直接下載安裝 - Debian 10</span><span class="sxs-lookup"><span data-stu-id="3cc1c-196">Installation via Direct Download - Debian 10</span></span>

<span data-ttu-id="3cc1c-197">將[發行][]頁面上的 tar.gz 套件 `powershell-7.0.1-linux-x64.tar.gz` 下載到 Debian 電腦：</span><span class="sxs-lookup"><span data-stu-id="3cc1c-197">Download the tar.gz package `powershell-7.0.1-linux-x64.tar.gz` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="3cc1c-198">然後，在終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="3cc1c-198">Then, in the terminal, execute the following commands:</span></span>

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
curl -L  https://github.com/PowerShell/PowerShell/releases/download/v7.0.1/powershell-7.0.1-linux-x64.tar.gz -o /tmp/powershell.tar.gz

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

## <a name="alpine-39-and-310"></a><span data-ttu-id="3cc1c-199">Alpine 3.9 與 3.10</span><span class="sxs-lookup"><span data-stu-id="3cc1c-199">Alpine 3.9 and 3.10</span></span>

> [!NOTE]
> <span data-ttu-id="3cc1c-200">只有 PowerShell 7.0 與更新版本才支援 Alpine 3.9 與 3.10。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-200">Alpine 3.9 and 3.10 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---alpine-39-and-310"></a><span data-ttu-id="3cc1c-201">透過直接下載安裝 - Alpine 3.9 與 3.10</span><span class="sxs-lookup"><span data-stu-id="3cc1c-201">Installation via Direct Download - Alpine 3.9 and 3.10</span></span>

<span data-ttu-id="3cc1c-202">將[發行][]頁面上的 tar.gz 套件 `powershell-7.0.1-linux-alpine-x64.tar.gz` 下載到 Alpine 電腦：</span><span class="sxs-lookup"><span data-stu-id="3cc1c-202">Download the tar.gz package `powershell-7.0.1-linux-alpine-x64.tar.gz` from the [releases][] page onto the Alpine machine.</span></span>

<span data-ttu-id="3cc1c-203">然後，在終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="3cc1c-203">Then, in the terminal, execute the following commands:</span></span>

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
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.1/powershell-7.0.1-linux-alpine-x64.tar.gz -o /tmp/powershell.tar.gz

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

## <a name="centos-7"></a><span data-ttu-id="3cc1c-204">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3cc1c-204">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="3cc1c-205">此套件也適用於 Oracle Linux 7。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-205">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="3cc1c-206">透過套件存放庫安裝 (慣用) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3cc1c-206">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="3cc1c-207">適用於 Linux 的 PowerShell 會發佈到官方 Microsoft 存放庫，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-207">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="3cc1c-208">以超級使用者的身分，註冊 Microsoft 存放庫一次。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-208">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="3cc1c-209">註冊之後，您可以使用 `sudo yum update powershell` 來更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-209">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="3cc1c-210">透過直接下載安裝 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3cc1c-210">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="3cc1c-211">使用 [CentOS 7][]，將[發行][]頁面上的 RPM 套件 `powershell-lts-7.0.1-1.rhel.7.x86_64.rpm` 下載至 CentOS 電腦。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-211">Using [CentOS 7][], download the RPM package `powershell-lts-7.0.1-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="3cc1c-212">然後，在終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="3cc1c-212">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-lts-7.0.1-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="3cc1c-213">無需下載的中繼步驟便可安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="3cc1c-213">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.1/powershell-lts-7.0.1-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="3cc1c-214">解除安裝 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3cc1c-214">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="3cc1c-216">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="3cc1c-216">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="3cc1c-217">透過套件存放庫安裝 (慣用) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="3cc1c-217">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="3cc1c-218">適用於 Linux 的 PowerShell 會發佈到官方 Microsoft 存放庫，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-218">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="3cc1c-219">以超級使用者的身分，註冊 Microsoft 存放庫一次。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-219">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="3cc1c-220">註冊之後，您可以使用 `sudo yum update powershell` 來更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-220">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="3cc1c-221">透過直接下載安裝 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="3cc1c-221">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="3cc1c-222">將[發行][]頁面上的 RPM 套件 `powershell-lts-7.0.1-1.rhel.7.x86_64.rpm` 下載到 Red Hat Enterprise Linux 電腦。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-222">Download the RPM package `powershell-lts-7.0.1-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="3cc1c-223">然後，在終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="3cc1c-223">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-lts-7.0.1-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="3cc1c-224">無需下載的中繼步驟便可安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="3cc1c-224">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.1/powershell-lts-7.0.1-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="3cc1c-225">解除安裝 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="3cc1c-225">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="3cc1c-226">openSUSE</span><span class="sxs-lookup"><span data-stu-id="3cc1c-226">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="3cc1c-227">安裝 - openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="3cc1c-227">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.1/powershell-7.0.1-linux-x64.tar.gz -o /tmp/powershell.tar.gz

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="3cc1c-228">安裝 - openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="3cc1c-228">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.1/powershell-7.0.1-linux-x64.tar.gz -o /tmp/powershell.tar.gz

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="3cc1c-229">解除安裝 - openSUSE 42.3、openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="3cc1c-229">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="3cc1c-230">Fedora</span><span class="sxs-lookup"><span data-stu-id="3cc1c-230">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="3cc1c-231">只有 PowerShell Core 6.1 與更新版本才支援 Fedora 28。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-231">Fedora 28 is only supported in PowerShell 6.1 and newer.</span></span>

> [!NOTE]
> <span data-ttu-id="3cc1c-232">只有 PowerShell 7.0 與更新版本才支援 Fedora 29 與 30。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-232">Fedora 29 and 30 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a><span data-ttu-id="3cc1c-233">透過套件存放庫安裝 (慣用) - Fedora 28、29 與 30</span><span class="sxs-lookup"><span data-stu-id="3cc1c-233">Installation via Package Repository (preferred) - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="3cc1c-234">適用於 Linux 的 PowerShell 會發佈到官方 Microsoft 存放庫，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-234">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a><span data-ttu-id="3cc1c-235">透過直接下載安裝 - Fedora 28、29 與 30</span><span class="sxs-lookup"><span data-stu-id="3cc1c-235">Installation via Direct Download - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="3cc1c-236">將[發行][]頁面上的 RPM 套件 `powershell-7.0.1-1.rhel.7.x86_64.rpm` 下載到 Fedora 電腦。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-236">Download the RPM package `powershell-7.0.1-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="3cc1c-237">然後，在終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="3cc1c-237">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-7.0.1-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="3cc1c-238">無需下載的中繼步驟便可安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="3cc1c-238">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v7.0.1/powershell-7.0.1-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a><span data-ttu-id="3cc1c-239">解除安裝 - Fedora 28、29 與 30</span><span class="sxs-lookup"><span data-stu-id="3cc1c-239">Uninstallation - Fedora 28, 29, and 30</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="3cc1c-240">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="3cc1c-240">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="3cc1c-241">「架構」支援並非由 Microsoft 正式支援，而是由社群維護。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-241">Arch support is not officially supported by Microsoft and is maintained by the community.</span></span>

<span data-ttu-id="3cc1c-242">PowerShell 可從 [Arch Linux][] 使用者存放庫 (AUR) 取得。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-242">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

- <span data-ttu-id="3cc1c-243">可以使用[最新的標記版本][arch-release]編譯</span><span class="sxs-lookup"><span data-stu-id="3cc1c-243">It can be compiled with the [latest tagged release][arch-release]</span></span>
- <span data-ttu-id="3cc1c-244">可以從[主機的最新認可][arch-git]編譯</span><span class="sxs-lookup"><span data-stu-id="3cc1c-244">It can be compiled from the [latest commit to master][arch-git]</span></span>
- <span data-ttu-id="3cc1c-245">可以使用[最新版本的二進位檔][arch-bin]安裝</span><span class="sxs-lookup"><span data-stu-id="3cc1c-245">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="3cc1c-246">AUR 中的套件由社群維護，沒有官方支援。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-246">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="3cc1c-247">如需從 AUR 安裝套件的詳細資訊，請參閱 [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) 或[在 Docker 中使用 PowerShell](powershell-in-docker.md)。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-247">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or [Using PowerShell in Docker](powershell-in-docker.md).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="3cc1c-249">Snap 套件</span><span class="sxs-lookup"><span data-stu-id="3cc1c-249">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="3cc1c-250">取得 snapd</span><span class="sxs-lookup"><span data-stu-id="3cc1c-250">Getting snapd</span></span>

<span data-ttu-id="3cc1c-251">必須有 `snapd` 才能執行 Snap。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-251">`snapd` is required to run snaps.</span></span> <span data-ttu-id="3cc1c-252">請使用[這些指示](https://docs.snapcraft.io/core/install)確認您已安裝 `snapd`。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-252">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="3cc1c-253">透過 Snap 安裝</span><span class="sxs-lookup"><span data-stu-id="3cc1c-253">Installation via Snap</span></span>

<span data-ttu-id="3cc1c-254">適用於 Linux 的 PowerShell 會發佈到 [Snap Store](https://snapcraft.io/store)，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-254">PowerShell for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="3cc1c-255">慣用的方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="3cc1c-255">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="3cc1c-256">若要安裝預覽版，請使用下列方法：</span><span class="sxs-lookup"><span data-stu-id="3cc1c-256">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="3cc1c-257">安裝之後，Snap 將會自動升級。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-257">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="3cc1c-258">您可以使用 `sudo snap refresh powershell` 或 `sudo snap refresh powershell-preview` 觸發升級。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-258">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="3cc1c-259">解除安裝</span><span class="sxs-lookup"><span data-stu-id="3cc1c-259">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="3cc1c-260">或</span><span class="sxs-lookup"><span data-stu-id="3cc1c-260">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="3cc1c-261">Kali</span><span class="sxs-lookup"><span data-stu-id="3cc1c-261">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="3cc1c-262">Kali 支援並非由 Microsoft 正式支援，而是由社群維護。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-262">Kali support is not officially supported by Microsoft and is maintained by the community.</span></span>

### <a name="installation---kali"></a><span data-ttu-id="3cc1c-263">安裝 - Kali</span><span class="sxs-lookup"><span data-stu-id="3cc1c-263">Installation - Kali</span></span>

```sh
# Install PowerShell package
apt update && apt -y install powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="3cc1c-264">解除安裝 - Kali</span><span class="sxs-lookup"><span data-stu-id="3cc1c-264">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt -y remove powershell
```

## <a name="raspbian"></a><span data-ttu-id="3cc1c-265">Raspbian</span><span class="sxs-lookup"><span data-stu-id="3cc1c-265">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="3cc1c-266">Raspbian 支援為實驗性。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-266">Raspbian support is experimental.</span></span>

<span data-ttu-id="3cc1c-267">目前只有 Raspbian Stretch 支援 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-267">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="3cc1c-268">CoreCLR 與 PowerShell 僅適用於 Pi 2 與 Pi 3 裝置，因為像 [Pi Zero](https://github.com/dotnet/coreclr/issues/10605) \(英文\) 這類的其他裝置，其處理器不受支援。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-268">CoreCLR and PowerShell will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="3cc1c-269">下載 [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) 並遵循[安裝指示](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)來把它安裝到您的 Pi。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-269">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="3cc1c-270">安裝 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="3cc1c-270">Installation - Raspbian</span></span>

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
wget https://github.com/PowerShell/PowerShell/releases/download/v7.0.1/powershell-7.0.1-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-7.0.1-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="3cc1c-271">或者，您可以建立一個符號連結來啟動 PowerShell，而無需指定 `pwsh` 二進位檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-271">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="3cc1c-272">解除安裝 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="3cc1c-272">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="installing-preview-releases"></a><span data-ttu-id="3cc1c-273">安裝預覽版本</span><span class="sxs-lookup"><span data-stu-id="3cc1c-273">Installing Preview Releases</span></span>

<span data-ttu-id="3cc1c-274">透過套件存放庫安裝 Linux 的 PowerShell Preview 版本時，套件名稱會從 `powershell` 變更為 `powershell-preview`。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-274">When installing a PowerShell Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="3cc1c-275">透過直接下載的安裝不會變更，但檔案名稱除外。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-275">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="3cc1c-276">下表包含使用各種套件管理員安裝穩定和預覽套件的命令：</span><span class="sxs-lookup"><span data-stu-id="3cc1c-276">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

| <span data-ttu-id="3cc1c-277">發行版本</span><span class="sxs-lookup"><span data-stu-id="3cc1c-277">Distribution(s)</span></span> |            <span data-ttu-id="3cc1c-278">穩定命令</span><span class="sxs-lookup"><span data-stu-id="3cc1c-278">Stable Command</span></span>            |               <span data-ttu-id="3cc1c-279">預覽命令</span><span class="sxs-lookup"><span data-stu-id="3cc1c-279">Preview Command</span></span>                |
| --------------- | ------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="3cc1c-280">Ubuntu、Debian</span><span class="sxs-lookup"><span data-stu-id="3cc1c-280">Ubuntu, Debian</span></span>  | `sudo apt-get install -y powershell` | `sudo apt-get install -y powershell-preview` |
| <span data-ttu-id="3cc1c-281">CentOS、RedHat</span><span class="sxs-lookup"><span data-stu-id="3cc1c-281">CentOS, RedHat</span></span>  | `sudo yum install -y powershell`     | `sudo yum install -y powershell-preview`     |
| <span data-ttu-id="3cc1c-282">Fedora</span><span class="sxs-lookup"><span data-stu-id="3cc1c-282">Fedora</span></span>          | `sudo dnf install -y powershell`     | `sudo dnf install -y powershell-preview`     |

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="3cc1c-283">安裝為 .NET 全域工具</span><span class="sxs-lookup"><span data-stu-id="3cc1c-283">Install as a .NET Global tool</span></span>

<span data-ttu-id="3cc1c-284">如果您已安裝 [.NET Core SDK](/dotnet/core/sdk)，就可以輕鬆地將 PowerShell 安裝為 [.NET 全域工具](/dotnet/core/tools/global-tools)。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-284">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="3cc1c-285">Dotnet 工具安裝程式會將 `~/.dotnet/tools` 新增至您的 `PATH` 環境變數。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-285">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="3cc1c-286">不過，目前執行的殼層沒有更新的 `PATH`。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-286">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="3cc1c-287">您應該能夠透過輸入 `pwsh`，以從新的殼層啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-287">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="3cc1c-288">二進位封存</span><span class="sxs-lookup"><span data-stu-id="3cc1c-288">Binary Archives</span></span>

<span data-ttu-id="3cc1c-289">Linux 平台有 PowerShell 二進位 `tar.gz` 封存，以啟用進階的部署案例。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-289">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="3cc1c-290">相依性</span><span class="sxs-lookup"><span data-stu-id="3cc1c-290">Dependencies</span></span>

<span data-ttu-id="3cc1c-291">PowerShell 會為所有 Linux 發行版本建置可攜式二進位檔。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-291">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="3cc1c-292">但 .NET Core 執行階段在不同的發行版本需要不同的相依性，PowerShell 也一樣。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-292">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="3cc1c-293">下圖顯示不同 Linux 發行版本上，正式支援的 .NET Core 2.0 相依性。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-293">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="3cc1c-294">OS</span><span class="sxs-lookup"><span data-stu-id="3cc1c-294">OS</span></span>                 | <span data-ttu-id="3cc1c-295">相依性</span><span class="sxs-lookup"><span data-stu-id="3cc1c-295">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="3cc1c-296">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="3cc1c-296">Ubuntu 16.04</span></span>       | <span data-ttu-id="3cc1c-297">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="3cc1c-297">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3cc1c-298">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu55</span><span class="sxs-lookup"><span data-stu-id="3cc1c-298">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="3cc1c-299">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="3cc1c-299">Ubuntu 17.10</span></span>       | <span data-ttu-id="3cc1c-300">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="3cc1c-300">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3cc1c-301">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu57</span><span class="sxs-lookup"><span data-stu-id="3cc1c-301">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="3cc1c-302">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="3cc1c-302">Ubuntu 18.04</span></span>       | <span data-ttu-id="3cc1c-303">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="3cc1c-303">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3cc1c-304">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu60</span><span class="sxs-lookup"><span data-stu-id="3cc1c-304">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="3cc1c-305">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="3cc1c-305">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="3cc1c-306">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="3cc1c-306">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3cc1c-307">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52</span><span class="sxs-lookup"><span data-stu-id="3cc1c-307">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="3cc1c-308">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="3cc1c-308">Debian 9 (Stretch)</span></span> | <span data-ttu-id="3cc1c-309">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="3cc1c-309">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3cc1c-310">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.2、libicu57</span><span class="sxs-lookup"><span data-stu-id="3cc1c-310">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="3cc1c-311">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3cc1c-311">CentOS 7</span></span> <br> <span data-ttu-id="3cc1c-312">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="3cc1c-312">Oracle Linux 7</span></span> <br> <span data-ttu-id="3cc1c-313">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="3cc1c-313">RHEL 7</span></span> | <span data-ttu-id="3cc1c-314">libunwind、libcurl、openssl-libs、libicu</span><span class="sxs-lookup"><span data-stu-id="3cc1c-314">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="3cc1c-315">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="3cc1c-315">openSUSE 42.3</span></span> | <span data-ttu-id="3cc1c-316">libcurl4、libopenssl1_0_0、libicu52_1</span><span class="sxs-lookup"><span data-stu-id="3cc1c-316">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="3cc1c-317">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="3cc1c-317">openSUSE Leap 15</span></span> | <span data-ttu-id="3cc1c-318">libcurl4、libopenssl1_0_0、libicu60_2</span><span class="sxs-lookup"><span data-stu-id="3cc1c-318">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="3cc1c-319">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="3cc1c-319">Fedora 27</span></span> <br> <span data-ttu-id="3cc1c-320">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="3cc1c-320">Fedora 28</span></span> | <span data-ttu-id="3cc1c-321">libunwind、libcurl、openssl-libs、libicu、compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="3cc1c-321">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="3cc1c-322">若要在未正式支援的 Linux 發行版本上部署 PowerShell 二進位檔，您需要在個別步驟中為目標作業系統安裝必要的相依性。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-322">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="3cc1c-323">例如，[Amazon Linux dockerfile][amazon-dockerfile] 會先安裝相依性，再解壓縮 Linux `tar.gz` 封存。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-323">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="3cc1c-324">安裝 - 二進位封存</span><span class="sxs-lookup"><span data-stu-id="3cc1c-324">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="3cc1c-325">Linux</span><span class="sxs-lookup"><span data-stu-id="3cc1c-325">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.0.1/powershell-7.0.1-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="3cc1c-326">解除安裝二進位封存</span><span class="sxs-lookup"><span data-stu-id="3cc1c-326">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="3cc1c-327">路徑</span><span class="sxs-lookup"><span data-stu-id="3cc1c-327">Paths</span></span>

- <span data-ttu-id="3cc1c-328">`$PSHOME` 是 `/opt/microsoft/powershell/7/`</span><span class="sxs-lookup"><span data-stu-id="3cc1c-328">`$PSHOME` is `/opt/microsoft/powershell/7/`</span></span>
- <span data-ttu-id="3cc1c-329">會從 `~/.config/powershell/profile.ps1` 讀取使用者設定檔</span><span class="sxs-lookup"><span data-stu-id="3cc1c-329">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
- <span data-ttu-id="3cc1c-330">會從 `$PSHOME/profile.ps1` 讀取預設設定檔</span><span class="sxs-lookup"><span data-stu-id="3cc1c-330">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
- <span data-ttu-id="3cc1c-331">會從 `~/.local/share/powershell/Modules` 讀取使用者模組</span><span class="sxs-lookup"><span data-stu-id="3cc1c-331">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="3cc1c-332">會從 `/usr/local/share/powershell/Modules` 讀取共用的模組</span><span class="sxs-lookup"><span data-stu-id="3cc1c-332">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
- <span data-ttu-id="3cc1c-333">會從 `$PSHOME/Modules` 讀取預設模組</span><span class="sxs-lookup"><span data-stu-id="3cc1c-333">Default modules will be read from `$PSHOME/Modules`</span></span>
- <span data-ttu-id="3cc1c-334">PSReadline 記錄會記錄在 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="3cc1c-334">PSReadLine history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="3cc1c-335">設定檔會遵循 PowerShell 的每個主控件設定，讓預設主控件特定設定檔存在於相同位置的 `Microsoft.PowerShell_profile.ps1`。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-335">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="3cc1c-336">PowerShell 遵循 Linux 上的 [XDG 基底目錄規格][xdg-bds]。</span><span class="sxs-lookup"><span data-stu-id="3cc1c-336">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[發行]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
