---
title: 在 Linux 上安裝 PowerShell
description: 在各種 Linux 發行版本上安裝 PowerShell Core 的相關資訊
ms.date: 03/09/2020
ms.openlocfilehash: 0c7b2bd804d07b2fcb61a61240b139f84fabd6db
ms.sourcegitcommit: c97dcf1e00ef540e7464c36c88f841474060044c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79402535"
---
# <a name="installing-powershell-on-linux"></a><span data-ttu-id="d37d0-103">在 Linux 上安裝 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d37d0-103">Installing PowerShell on Linux</span></span>

<span data-ttu-id="d37d0-104">支援 [Ubuntu 16.04][u16]、[Ubuntu 18.04][u1804]、[Ubuntu 18.10][u1810]、[Ubuntu 19.04][u1904]、[Debian 8][deb8]、[Debian 9][deb9]、[Debian 10][deb10]、[CentOS 7][cos]、[Red Hat Enterprise Linux (RHEL) 7][rhel7]、[openSUSE 42.3][opensuse]、[openSUSE Leap 15][opensuse]、[Fedora 27][fedora]、[Fedora 28][fedora] 與 [Arch Linux][arch]。</span><span class="sxs-lookup"><span data-stu-id="d37d0-104">Supports [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Ubuntu 19.04][u1904], [Debian 8][deb8], [Debian 9][deb9], [Debian 10][deb10], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="d37d0-105">針對未正式支援的 Linux 發佈，您可以嘗試使用 [PowerShell Snap 套件][snap]來安裝 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d37d0-105">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="d37d0-106">您也可以直接使用 Linux [`tar.gz` 封存][tar]來嘗試部署 PowerShell 二進位檔，但您需要根據個別步驟中作業系統設定必要的相依性。</span><span class="sxs-lookup"><span data-stu-id="d37d0-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="d37d0-107">GitHub [發行][]頁面上提供所有套件。</span><span class="sxs-lookup"><span data-stu-id="d37d0-107">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="d37d0-108">安裝套件之後，請從終端機執行 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="d37d0-108">After the package is installed, run `pwsh` from a terminal.</span></span> <span data-ttu-id="d37d0-109">若您已安裝[預覽版](#installing-preview-releases)，請執行 `pwsh-preview`。</span><span class="sxs-lookup"><span data-stu-id="d37d0-109">Run `pwsh-preview` if you installed a [Preview release](#installing-preview-releases).</span></span>

> [!NOTE]
> <span data-ttu-id="d37d0-110">PowerShell 7 是會移除 PowerShell Core 6.x 的就地升級。</span><span class="sxs-lookup"><span data-stu-id="d37d0-110">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="d37d0-111">`/usr/local/microsoft/powershell/6` 資料夾已由 `/usr/local/microsoft/powershell/7` 取代。</span><span class="sxs-lookup"><span data-stu-id="d37d0-111">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="d37d0-112">如果您需要與 PowerShell 7 並存執行 PowerShell 6，請使用 [二進位封存](#binary-archives)方法來重新安裝 PowerShell 6。</span><span class="sxs-lookup"><span data-stu-id="d37d0-112">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[u1904]: #ubuntu-1904
[deb8]: #debian-8
[deb9]: #debian-9
[deb10]: #debian-10
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives


## <a name="installing-preview-releases"></a><span data-ttu-id="d37d0-113">安裝預覽版本</span><span class="sxs-lookup"><span data-stu-id="d37d0-113">Installing Preview Releases</span></span>

<span data-ttu-id="d37d0-114">透過套件存放庫安裝 Linux 的 PowerShell Preview 版本時，套件名稱會從 `powershell` 變更為 `powershell-preview`。</span><span class="sxs-lookup"><span data-stu-id="d37d0-114">When installing a PowerShell Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="d37d0-115">透過直接下載的安裝不會變更，但檔案名稱除外。</span><span class="sxs-lookup"><span data-stu-id="d37d0-115">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="d37d0-116">下表包含使用各種套件管理員安裝穩定和預覽套件的命令：</span><span class="sxs-lookup"><span data-stu-id="d37d0-116">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

| <span data-ttu-id="d37d0-117">發行版本</span><span class="sxs-lookup"><span data-stu-id="d37d0-117">Distribution(s)</span></span> |            <span data-ttu-id="d37d0-118">穩定命令</span><span class="sxs-lookup"><span data-stu-id="d37d0-118">Stable Command</span></span>            |               <span data-ttu-id="d37d0-119">預覽命令</span><span class="sxs-lookup"><span data-stu-id="d37d0-119">Preview Command</span></span>                |
| --------------- | ------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="d37d0-120">Ubuntu、Debian</span><span class="sxs-lookup"><span data-stu-id="d37d0-120">Ubuntu, Debian</span></span>  | `sudo apt-get install -y powershell` | `sudo apt-get install -y powershell-preview` |
| <span data-ttu-id="d37d0-121">CentOS、RedHat</span><span class="sxs-lookup"><span data-stu-id="d37d0-121">CentOS, RedHat</span></span>  | `sudo yum install -y powershell`     | `sudo yum install -y powershell-preview`     |
| <span data-ttu-id="d37d0-122">Fedora</span><span class="sxs-lookup"><span data-stu-id="d37d0-122">Fedora</span></span>          | `sudo dnf install -y powershell`     | `sudo dnf install -y powershell-preview`     |

## <a name="ubuntu-1604"></a><span data-ttu-id="d37d0-123">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="d37d0-123">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="d37d0-124">透過套件存放庫安裝 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="d37d0-124">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="d37d0-125">適用於 Linux 的 PowerShell 會發佈到套件存放庫，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="d37d0-125">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="d37d0-126">慣用的方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="d37d0-126">The preferred method is as follows:</span></span>

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

<span data-ttu-id="d37d0-127">以超級使用者的身分，註冊 Microsoft 存放庫一次。</span><span class="sxs-lookup"><span data-stu-id="d37d0-127">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="d37d0-128">註冊之後，您可以使用 `sudo apt-get upgrade powershell` 來更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d37d0-128">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="d37d0-129">透過直接下載安裝 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="d37d0-129">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="d37d0-130">將[發行][]頁面上的 Debian 套件 `powershell_7.0.0-1.ubuntu.16.04_amd64.deb` 下載至 Ubuntu 電腦。</span><span class="sxs-lookup"><span data-stu-id="d37d0-130">Download the Debian package `powershell_7.0.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="d37d0-131">然後，在終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="d37d0-131">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="d37d0-132">`dpkg -i` 命令因相依性不相符而失敗。</span><span class="sxs-lookup"><span data-stu-id="d37d0-132">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="d37d0-133">下一個命令 `apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。</span><span class="sxs-lookup"><span data-stu-id="d37d0-133">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="d37d0-134">解除安裝 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="d37d0-134">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="d37d0-135">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="d37d0-135">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="d37d0-136">透過套件存放庫安裝 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="d37d0-136">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="d37d0-137">適用於 Linux 的 PowerShell 會發佈到套件存放庫，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="d37d0-137">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="d37d0-138">慣用的方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="d37d0-138">The preferred method is as follows:</span></span>

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

<span data-ttu-id="d37d0-139">以超級使用者的身分，註冊 Microsoft 存放庫一次。</span><span class="sxs-lookup"><span data-stu-id="d37d0-139">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="d37d0-140">註冊之後，您可以使用 `sudo apt-get upgrade powershell` 來更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d37d0-140">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="d37d0-141">透過直接下載安裝 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="d37d0-141">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="d37d0-142">將[發行][]頁面上的 Debian 套件 `powershell_7.0.0-1.ubuntu.18.04_amd64.deb` 下載至 Ubuntu 電腦。</span><span class="sxs-lookup"><span data-stu-id="d37d0-142">Download the Debian package `powershell_7.0.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="d37d0-143">然後，在終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="d37d0-143">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.0.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="d37d0-144">`dpkg -i` 命令因相依性不相符而失敗。</span><span class="sxs-lookup"><span data-stu-id="d37d0-144">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="d37d0-145">下一個命令 `apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。</span><span class="sxs-lookup"><span data-stu-id="d37d0-145">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="d37d0-146">解除安裝 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="d37d0-146">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="d37d0-147">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="d37d0-147">Ubuntu 18.10</span></span>

<span data-ttu-id="d37d0-148">安裝由 `snapd` 支援。</span><span class="sxs-lookup"><span data-stu-id="d37d0-148">Installation is supported via `snapd`.</span></span> <span data-ttu-id="d37d0-149">如需指示，請參閱 [Snap 套件][snap]。</span><span class="sxs-lookup"><span data-stu-id="d37d0-149">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="d37d0-150">Ubuntu 18.10 是[由社群支援](../powershell-support-lifecycle.md)的[過渡版本](https://www.ubuntu.com/about/release-cycle) (英文)。</span><span class="sxs-lookup"><span data-stu-id="d37d0-150">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1904"></a><span data-ttu-id="d37d0-151">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="d37d0-151">Ubuntu 19.04</span></span>

<span data-ttu-id="d37d0-152">安裝由 `snapd` 支援。</span><span class="sxs-lookup"><span data-stu-id="d37d0-152">Installation is supported via `snapd`.</span></span> <span data-ttu-id="d37d0-153">如需指示，請參閱 [Snap 套件][snap]。</span><span class="sxs-lookup"><span data-stu-id="d37d0-153">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="d37d0-154">因為 Ubuntu 19.04 是[由社群支援](../powershell-support-lifecycle.md)的[過渡版本](https://www.ubuntu.com/about/release-cycle) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="d37d0-154">Ubuntu 19.04 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="debian-8"></a><span data-ttu-id="d37d0-155">Debian 8</span><span class="sxs-lookup"><span data-stu-id="d37d0-155">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="d37d0-156">透過套件存放庫安裝 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="d37d0-156">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="d37d0-157">適用於 Linux 的 PowerShell 會發佈到套件存放庫，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="d37d0-157">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="d37d0-158">慣用的方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="d37d0-158">The preferred method is as follows:</span></span>

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

<span data-ttu-id="d37d0-159">以超級使用者的身分，註冊 Microsoft 存放庫一次。</span><span class="sxs-lookup"><span data-stu-id="d37d0-159">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="d37d0-160">註冊之後，您可以使用 `sudo apt-get upgrade powershell` 來更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d37d0-160">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="d37d0-161">Debian 9</span><span class="sxs-lookup"><span data-stu-id="d37d0-161">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="d37d0-162">透過套件存放庫安裝 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="d37d0-162">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="d37d0-163">適用於 Linux 的 PowerShell 會發佈到套件存放庫，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="d37d0-163">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="d37d0-164">慣用的方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="d37d0-164">The preferred method is as follows:</span></span>

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

<span data-ttu-id="d37d0-165">以超級使用者的身分，註冊 Microsoft 存放庫一次。</span><span class="sxs-lookup"><span data-stu-id="d37d0-165">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="d37d0-166">註冊之後，您可以使用 `sudo apt-get upgrade powershell` 來更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d37d0-166">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="d37d0-167">透過直接下載安裝 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="d37d0-167">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="d37d0-168">將[發行][]頁面上的 Debian 套件 `powershell_7.0.0-1.debian.9_amd64.deb` 下載至 Debian 電腦。</span><span class="sxs-lookup"><span data-stu-id="d37d0-168">Download the Debian package `powershell_7.0.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="d37d0-169">然後，在終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="d37d0-169">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="d37d0-170">解除安裝 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="d37d0-170">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a><span data-ttu-id="d37d0-171">Debian 10</span><span class="sxs-lookup"><span data-stu-id="d37d0-171">Debian 10</span></span>

> [!NOTE]
> <span data-ttu-id="d37d0-172">只有 PowerShell Core 7.0 才支援 Debian 10。</span><span class="sxs-lookup"><span data-stu-id="d37d0-172">Debian 10 is only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---debian-10"></a><span data-ttu-id="d37d0-173">透過直接下載安裝 - Debian 10</span><span class="sxs-lookup"><span data-stu-id="d37d0-173">Installation via Direct Download - Debian 10</span></span>

<span data-ttu-id="d37d0-174">將[發行][]頁面上的 tar.gz 套件 `powershell_7.0.0-linux-x64.tar.gz` 下載到 Debian 電腦：</span><span class="sxs-lookup"><span data-stu-id="d37d0-174">Download the tar.gz package `powershell_7.0.0-linux-x64.tar.gz` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="d37d0-175">然後，在終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="d37d0-175">Then, in the terminal, execute the following commands:</span></span>

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
curl -L  https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

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

## <a name="alpine-39-and-310"></a><span data-ttu-id="d37d0-176">Alpine 3.9 與 3.10</span><span class="sxs-lookup"><span data-stu-id="d37d0-176">Alpine 3.9 and 3.10</span></span>

> [!NOTE]
> <span data-ttu-id="d37d0-177">只有 PowerShell 7.0 與更新版本才支援 Alpine 3.9 與 3.10。</span><span class="sxs-lookup"><span data-stu-id="d37d0-177">Alpine 3.9 and 3.10 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---alpine-39-and-310"></a><span data-ttu-id="d37d0-178">透過直接下載安裝 - Alpine 3.9 與 3.10</span><span class="sxs-lookup"><span data-stu-id="d37d0-178">Installation via Direct Download - Alpine 3.9 and 3.10</span></span>

<span data-ttu-id="d37d0-179">將[發行][]頁面上的 tar.gz 套件 `powershell_7.0.0-linux-x64.tar.gz` 下載到 Alpine 電腦：</span><span class="sxs-lookup"><span data-stu-id="d37d0-179">Download the tar.gz package `powershell_7.0.0-linux-x64.tar.gz` from the [releases][] page onto the Alpine machine.</span></span>

<span data-ttu-id="d37d0-180">然後，在終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="d37d0-180">Then, in the terminal, execute the following commands:</span></span>

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
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-alpine-x64.tar.gz -o /tmp/powershell.tar.gz

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

## <a name="centos-7"></a><span data-ttu-id="d37d0-181">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="d37d0-181">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="d37d0-182">此套件也適用於 Oracle Linux 7。</span><span class="sxs-lookup"><span data-stu-id="d37d0-182">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="d37d0-183">透過套件存放庫安裝 (慣用) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="d37d0-183">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="d37d0-184">適用於 Linux 的 PowerShell 會發佈到官方 Microsoft 存放庫，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="d37d0-184">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="d37d0-185">以超級使用者的身分，註冊 Microsoft 存放庫一次。</span><span class="sxs-lookup"><span data-stu-id="d37d0-185">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="d37d0-186">註冊之後，您可以使用 `sudo yum update powershell` 來更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d37d0-186">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="d37d0-187">透過直接下載安裝 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="d37d0-187">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="d37d0-188">使用 [CentOS 7][]，將[發行][]頁面上的 RPM 套件 `powershell-7.0.0-1.rhel.7.x86_64.rpm` 下載至 CentOS 電腦。</span><span class="sxs-lookup"><span data-stu-id="d37d0-188">Using [CentOS 7][], download the RPM package `powershell-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="d37d0-189">然後，在終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="d37d0-189">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="d37d0-190">無需下載的中繼步驟便可安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="d37d0-190">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="d37d0-191">解除安裝 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="d37d0-191">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="d37d0-193">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="d37d0-193">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="d37d0-194">透過套件存放庫安裝 (慣用) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="d37d0-194">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="d37d0-195">適用於 Linux 的 PowerShell 會發佈到官方 Microsoft 存放庫，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="d37d0-195">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="d37d0-196">以超級使用者的身分，註冊 Microsoft 存放庫一次。</span><span class="sxs-lookup"><span data-stu-id="d37d0-196">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="d37d0-197">註冊之後，您可以使用 `sudo yum update powershell` 來更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d37d0-197">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="d37d0-198">透過直接下載安裝 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="d37d0-198">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="d37d0-199">將[發行][]頁面上的 RPM 套件 `powershell-7.0.0-1.rhel.7.x86_64.rpm` 下載到 Red Hat Enterprise Linux 電腦。</span><span class="sxs-lookup"><span data-stu-id="d37d0-199">Download the RPM package `powershell-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="d37d0-200">然後，在終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="d37d0-200">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="d37d0-201">無需下載的中繼步驟便可安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="d37d0-201">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="d37d0-202">解除安裝 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="d37d0-202">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="d37d0-203">openSUSE</span><span class="sxs-lookup"><span data-stu-id="d37d0-203">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="d37d0-204">安裝 - openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="d37d0-204">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="d37d0-205">安裝 - openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="d37d0-205">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="d37d0-206">解除安裝 - openSUSE 42.3、openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="d37d0-206">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="d37d0-207">Fedora</span><span class="sxs-lookup"><span data-stu-id="d37d0-207">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="d37d0-208">只有 PowerShell Core 6.1 與更新版本才支援 Fedora 28。</span><span class="sxs-lookup"><span data-stu-id="d37d0-208">Fedora 28 is only supported in PowerShell 6.1 and newer.</span></span>

> [!NOTE]
> <span data-ttu-id="d37d0-209">只有 PowerShell 7.0 與更新版本才支援 Fedora 29 與 30。</span><span class="sxs-lookup"><span data-stu-id="d37d0-209">Fedora 29 and 30 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a><span data-ttu-id="d37d0-210">透過套件存放庫安裝 (慣用) - Fedora 28、29 與 30</span><span class="sxs-lookup"><span data-stu-id="d37d0-210">Installation via Package Repository (preferred) - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="d37d0-211">適用於 Linux 的 PowerShell 會發佈到官方 Microsoft 存放庫，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="d37d0-211">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install a system component
sudo dnf install compat-openssl10

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a><span data-ttu-id="d37d0-212">透過直接下載安裝 - Fedora 28、29 與 30</span><span class="sxs-lookup"><span data-stu-id="d37d0-212">Installation via Direct Download - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="d37d0-213">將[發行][]頁面上的 RPM 套件 `powershell-7.0.0-1.rhel.7.x86_64.rpm` 下載到 Fedora 電腦。</span><span class="sxs-lookup"><span data-stu-id="d37d0-213">Download the RPM package `powershell-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="d37d0-214">然後，在終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="d37d0-214">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="d37d0-215">無需下載的中繼步驟便可安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="d37d0-215">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a><span data-ttu-id="d37d0-216">解除安裝 - Fedora 28、29 與 30</span><span class="sxs-lookup"><span data-stu-id="d37d0-216">Uninstallation - Fedora 28, 29, and 30</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="d37d0-217">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="d37d0-217">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="d37d0-218">「架構」支援並非由 Microsoft 正式支援，而是由社群維護。</span><span class="sxs-lookup"><span data-stu-id="d37d0-218">Arch support is not officially supported by Microsoft and is maintained by the community.</span></span>

<span data-ttu-id="d37d0-219">PowerShell 可從 [Arch Linux][] 使用者存放庫 (AUR) 取得。</span><span class="sxs-lookup"><span data-stu-id="d37d0-219">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="d37d0-220">可以使用[最新的標記版本][arch-release]編譯</span><span class="sxs-lookup"><span data-stu-id="d37d0-220">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="d37d0-221">可以從[主機的最新認可][arch-git]編譯</span><span class="sxs-lookup"><span data-stu-id="d37d0-221">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="d37d0-222">可以使用[最新版本的二進位檔][arch-bin]安裝</span><span class="sxs-lookup"><span data-stu-id="d37d0-222">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="d37d0-223">AUR 中的套件由社群維護，沒有官方支援。</span><span class="sxs-lookup"><span data-stu-id="d37d0-223">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="d37d0-224">如需從 AUR 安裝套件的詳細資訊，請參閱 [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) 或社群 [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile)。</span><span class="sxs-lookup"><span data-stu-id="d37d0-224">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="d37d0-226">Snap 套件</span><span class="sxs-lookup"><span data-stu-id="d37d0-226">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="d37d0-227">取得 snapd</span><span class="sxs-lookup"><span data-stu-id="d37d0-227">Getting snapd</span></span>

<span data-ttu-id="d37d0-228">必須有 `snapd` 才能執行 Snap。</span><span class="sxs-lookup"><span data-stu-id="d37d0-228">`snapd` is required to run snaps.</span></span> <span data-ttu-id="d37d0-229">請使用[這些指示](https://docs.snapcraft.io/core/install)確認您已安裝 `snapd`。</span><span class="sxs-lookup"><span data-stu-id="d37d0-229">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="d37d0-230">透過 Snap 安裝</span><span class="sxs-lookup"><span data-stu-id="d37d0-230">Installation via Snap</span></span>

<span data-ttu-id="d37d0-231">適用於 Linux 的 PowerShell 會發佈到 [Snap Store](https://snapcraft.io/store)，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="d37d0-231">PowerShell for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="d37d0-232">慣用的方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="d37d0-232">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="d37d0-233">若要安裝預覽版，請使用下列方法：</span><span class="sxs-lookup"><span data-stu-id="d37d0-233">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="d37d0-234">安裝之後，Snap 將會自動升級。</span><span class="sxs-lookup"><span data-stu-id="d37d0-234">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="d37d0-235">您可以使用 `sudo snap refresh powershell` 或 `sudo snap refresh powershell-preview` 觸發升級。</span><span class="sxs-lookup"><span data-stu-id="d37d0-235">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="d37d0-236">解除安裝</span><span class="sxs-lookup"><span data-stu-id="d37d0-236">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="d37d0-237">或</span><span class="sxs-lookup"><span data-stu-id="d37d0-237">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="d37d0-238">Kali</span><span class="sxs-lookup"><span data-stu-id="d37d0-238">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="d37d0-239">Kali 支援並非由 Microsoft 正式支援，而是由社群維護。</span><span class="sxs-lookup"><span data-stu-id="d37d0-239">Kali support is not officially supported by Microsoft and is maintained by the community.</span></span>

### <a name="installation---kali"></a><span data-ttu-id="d37d0-240">安裝 - Kali</span><span class="sxs-lookup"><span data-stu-id="d37d0-240">Installation - Kali</span></span>

```sh
# Install PowerShell package
apt update && apt -y install powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="d37d0-241">解除安裝 - Kali</span><span class="sxs-lookup"><span data-stu-id="d37d0-241">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt -y remove powershell
```

## <a name="raspbian"></a><span data-ttu-id="d37d0-242">Raspbian</span><span class="sxs-lookup"><span data-stu-id="d37d0-242">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="d37d0-243">Raspbian 支援為實驗性。</span><span class="sxs-lookup"><span data-stu-id="d37d0-243">Raspbian support is experimental.</span></span>

<span data-ttu-id="d37d0-244">目前只有 Raspbian Stretch 支援 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d37d0-244">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="d37d0-245">CoreCLR 與 PowerShell 僅適用於 Pi 2 與 Pi 3 裝置，因為像 [Pi Zero](https://github.com/dotnet/coreclr/issues/10605) \(英文\) 這類的其他裝置，其處理器不受支援。</span><span class="sxs-lookup"><span data-stu-id="d37d0-245">CoreCLR and PowerShell will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="d37d0-246">下載 [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) 並遵循[安裝指示](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)來把它安裝到您的 Pi。</span><span class="sxs-lookup"><span data-stu-id="d37d0-246">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="d37d0-247">安裝 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="d37d0-247">Installation - Raspbian</span></span>

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
wget https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-7.0.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="d37d0-248">或者，您可以建立一個符號連結來啟動 PowerShell，而無需指定 `pwsh` 二進位檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="d37d0-248">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="d37d0-249">解除安裝 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="d37d0-249">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="d37d0-250">安裝為 .NET 全域工具</span><span class="sxs-lookup"><span data-stu-id="d37d0-250">Install as a .NET Global tool</span></span>

<span data-ttu-id="d37d0-251">如果您已安裝 [.NET Core SDK](/dotnet/core/sdk)，就可以輕鬆地將 PowerShell 安裝為 [.NET 全域工具](/dotnet/core/tools/global-tools)。</span><span class="sxs-lookup"><span data-stu-id="d37d0-251">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

## <a name="binary-archives"></a><span data-ttu-id="d37d0-252">二進位封存</span><span class="sxs-lookup"><span data-stu-id="d37d0-252">Binary Archives</span></span>

<span data-ttu-id="d37d0-253">Linux 平台有 PowerShell 二進位 `tar.gz` 封存，以啟用進階的部署案例。</span><span class="sxs-lookup"><span data-stu-id="d37d0-253">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="d37d0-254">相依性</span><span class="sxs-lookup"><span data-stu-id="d37d0-254">Dependencies</span></span>

<span data-ttu-id="d37d0-255">PowerShell 會為所有 Linux 發行版本建置可攜式二進位檔。</span><span class="sxs-lookup"><span data-stu-id="d37d0-255">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="d37d0-256">但 .NET Core 執行階段在不同的發行版本需要不同的相依性，PowerShell 也一樣。</span><span class="sxs-lookup"><span data-stu-id="d37d0-256">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="d37d0-257">下圖顯示不同 Linux 發行版本上，正式支援的 .NET Core 2.0 相依性。</span><span class="sxs-lookup"><span data-stu-id="d37d0-257">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="d37d0-258">OS</span><span class="sxs-lookup"><span data-stu-id="d37d0-258">OS</span></span>                 | <span data-ttu-id="d37d0-259">相依性</span><span class="sxs-lookup"><span data-stu-id="d37d0-259">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="d37d0-260">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="d37d0-260">Ubuntu 16.04</span></span>       | <span data-ttu-id="d37d0-261">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="d37d0-261">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="d37d0-262">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu55</span><span class="sxs-lookup"><span data-stu-id="d37d0-262">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="d37d0-263">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="d37d0-263">Ubuntu 17.10</span></span>       | <span data-ttu-id="d37d0-264">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="d37d0-264">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="d37d0-265">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu57</span><span class="sxs-lookup"><span data-stu-id="d37d0-265">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="d37d0-266">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="d37d0-266">Ubuntu 18.04</span></span>       | <span data-ttu-id="d37d0-267">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="d37d0-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="d37d0-268">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu60</span><span class="sxs-lookup"><span data-stu-id="d37d0-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="d37d0-269">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="d37d0-269">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="d37d0-270">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="d37d0-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="d37d0-271">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52</span><span class="sxs-lookup"><span data-stu-id="d37d0-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="d37d0-272">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="d37d0-272">Debian 9 (Stretch)</span></span> | <span data-ttu-id="d37d0-273">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="d37d0-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="d37d0-274">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.2、libicu57</span><span class="sxs-lookup"><span data-stu-id="d37d0-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="d37d0-275">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="d37d0-275">CentOS 7</span></span> <br> <span data-ttu-id="d37d0-276">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="d37d0-276">Oracle Linux 7</span></span> <br> <span data-ttu-id="d37d0-277">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="d37d0-277">RHEL 7</span></span> | <span data-ttu-id="d37d0-278">libunwind、libcurl、openssl-libs、libicu</span><span class="sxs-lookup"><span data-stu-id="d37d0-278">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="d37d0-279">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="d37d0-279">openSUSE 42.3</span></span> | <span data-ttu-id="d37d0-280">libcurl4、libopenssl1_0_0、libicu52_1</span><span class="sxs-lookup"><span data-stu-id="d37d0-280">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="d37d0-281">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="d37d0-281">openSUSE Leap 15</span></span> | <span data-ttu-id="d37d0-282">libcurl4、libopenssl1_0_0、libicu60_2</span><span class="sxs-lookup"><span data-stu-id="d37d0-282">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="d37d0-283">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="d37d0-283">Fedora 27</span></span> <br> <span data-ttu-id="d37d0-284">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="d37d0-284">Fedora 28</span></span> | <span data-ttu-id="d37d0-285">libunwind、libcurl、openssl-libs、libicu、compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="d37d0-285">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="d37d0-286">若要在未正式支援的 Linux 發行版本上部署 PowerShell 二進位檔，您需要在個別步驟中為目標作業系統安裝必要的相依性。</span><span class="sxs-lookup"><span data-stu-id="d37d0-286">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="d37d0-287">例如，[Amazon Linux dockerfile][amazon-dockerfile] 會先安裝相依性，再解壓縮 Linux `tar.gz` 封存。</span><span class="sxs-lookup"><span data-stu-id="d37d0-287">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="d37d0-288">安裝 - 二進位封存</span><span class="sxs-lookup"><span data-stu-id="d37d0-288">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="d37d0-289">Linux</span><span class="sxs-lookup"><span data-stu-id="d37d0-289">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="d37d0-290">解除安裝二進位封存</span><span class="sxs-lookup"><span data-stu-id="d37d0-290">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="d37d0-291">路徑</span><span class="sxs-lookup"><span data-stu-id="d37d0-291">Paths</span></span>

- <span data-ttu-id="d37d0-292">`$PSHOME` 是 `/opt/microsoft/powershell/7/`</span><span class="sxs-lookup"><span data-stu-id="d37d0-292">`$PSHOME` is `/opt/microsoft/powershell/7/`</span></span>
- <span data-ttu-id="d37d0-293">會從 `~/.config/powershell/profile.ps1` 讀取使用者設定檔</span><span class="sxs-lookup"><span data-stu-id="d37d0-293">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
- <span data-ttu-id="d37d0-294">會從 `$PSHOME/profile.ps1` 讀取預設設定檔</span><span class="sxs-lookup"><span data-stu-id="d37d0-294">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
- <span data-ttu-id="d37d0-295">會從 `~/.local/share/powershell/Modules` 讀取使用者模組</span><span class="sxs-lookup"><span data-stu-id="d37d0-295">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="d37d0-296">會從 `/usr/local/share/powershell/Modules` 讀取共用的模組</span><span class="sxs-lookup"><span data-stu-id="d37d0-296">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
- <span data-ttu-id="d37d0-297">會從 `$PSHOME/Modules` 讀取預設模組</span><span class="sxs-lookup"><span data-stu-id="d37d0-297">Default modules will be read from `$PSHOME/Modules`</span></span>
- <span data-ttu-id="d37d0-298">PSReadline 記錄會記錄在 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="d37d0-298">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="d37d0-299">設定檔會遵循 PowerShell 的每個主控件設定，讓預設主控件特定設定檔存在於相同位置的 `Microsoft.PowerShell_profile.ps1`。</span><span class="sxs-lookup"><span data-stu-id="d37d0-299">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="d37d0-300">PowerShell 遵循 Linux 上的 [XDG 基底目錄規格][xdg-bds]。</span><span class="sxs-lookup"><span data-stu-id="d37d0-300">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[發行]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
