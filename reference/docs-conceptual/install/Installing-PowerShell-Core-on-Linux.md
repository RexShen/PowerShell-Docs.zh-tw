---
title: 在 Linux 上安裝 PowerShell Core
description: 在各種 Linux 發佈上安裝 PowerShell Core 的相關資訊
ms.date: 07/19/2019
ms.openlocfilehash: 929b153ef784f3203cd31a0e2fc52e744a07532f
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2019
ms.locfileid: "68372192"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="2f7b1-103">在 Linux 上安裝 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="2f7b1-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="2f7b1-104">支援 [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804]、[Ubuntu 18.10][u1810]、[Debian 9][deb9],
 [CentOS 7][cos]、[Red Hat Enterprise Linux (RHEL) 7][rhel7]、[openSUSE 42.3][opensuse]、[openSUSE Leap 15][opensuse], [Fedora 27][fedora]、[Fedora 28][fedora] 與 [Arch Linux][arch]。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-104">Supports [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Debian 9][deb9],
 [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="2f7b1-105">針對未正式支援的 Linux 發佈，您可以嘗試使用 [PowerShell Snap 套件][snap]來安裝 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-105">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="2f7b1-106">您也可以直接使用 Linux [`tar.gz` 封存][tar]來嘗試部署 PowerShell 二進位檔，但您需要根據個別步驟中作業系統設定必要的相依性。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="2f7b1-107">GitHub [版本][]頁面上提供所有套件。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-107">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="2f7b1-108">安裝套件之後，請從終端機執行 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-108">After the package is installed, run `pwsh` from a terminal.</span></span>

[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="2f7b1-109">安裝預覽版本</span><span class="sxs-lookup"><span data-stu-id="2f7b1-109">Installing Preview Releases</span></span>

<span data-ttu-id="2f7b1-110">透過套件存放庫安裝 Linux 的 PowerShell Core Preview 版本時，套件名稱會從 `powershell` 變更為 `powershell-preview`。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="2f7b1-111">透過直接下載的安裝不會變更，但檔案名稱除外。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-111">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="2f7b1-112">下表包含使用各種套件管理員安裝穩定和預覽套件的命令：</span><span class="sxs-lookup"><span data-stu-id="2f7b1-112">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="2f7b1-113">發行版本</span><span class="sxs-lookup"><span data-stu-id="2f7b1-113">Distribution(s)</span></span>|<span data-ttu-id="2f7b1-114">穩定命令</span><span class="sxs-lookup"><span data-stu-id="2f7b1-114">Stable Command</span></span> | <span data-ttu-id="2f7b1-115">預覽命令</span><span class="sxs-lookup"><span data-stu-id="2f7b1-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="2f7b1-116">Ubuntu、Debian</span><span class="sxs-lookup"><span data-stu-id="2f7b1-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="2f7b1-117">CentOS、RedHat</span><span class="sxs-lookup"><span data-stu-id="2f7b1-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="2f7b1-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="2f7b1-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1604"></a><span data-ttu-id="2f7b1-119">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="2f7b1-119">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="2f7b1-120">透過套件存放庫安裝 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="2f7b1-120">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="2f7b1-121">PowerShell Core for Linux 會發佈到套件存放庫，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-121">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="2f7b1-122">慣用的方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="2f7b1-122">The preferred method is as follows:</span></span>

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

<span data-ttu-id="2f7b1-123">以超級使用者的身分，註冊 Microsoft 存放庫一次。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-123">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="2f7b1-124">註冊之後，您可以使用 `sudo apt-get upgrade powershell` 來更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-124">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="2f7b1-125">透過直接下載安裝 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="2f7b1-125">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="2f7b1-126">將[版本][]頁面上的 Debian 套件 `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` 下載至 Ubuntu 電腦。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-126">Download the Debian package `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="2f7b1-127">然後，在終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="2f7b1-127">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="2f7b1-128">`dpkg -i` 命令因相依性不相符而失敗。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-128">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="2f7b1-129">下一個命令 `apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-129">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="2f7b1-130">解除安裝 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="2f7b1-130">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="2f7b1-131">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="2f7b1-131">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="2f7b1-132">透過套件存放庫安裝 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="2f7b1-132">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="2f7b1-133">PowerShell Core for Linux 會發佈到套件存放庫，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-133">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="2f7b1-134">慣用的方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="2f7b1-134">The preferred method is as follows:</span></span>

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

<span data-ttu-id="2f7b1-135">以超級使用者的身分，註冊 Microsoft 存放庫一次。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-135">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="2f7b1-136">註冊之後，您可以使用 `sudo apt-get upgrade powershell` 來更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-136">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="2f7b1-137">透過直接下載安裝 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="2f7b1-137">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="2f7b1-138">將[版本][]頁面上的 Debian 套件 `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` 下載至 Ubuntu 電腦。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-138">Download the Debian package `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="2f7b1-139">然後，在終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="2f7b1-139">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="2f7b1-140">`dpkg -i` 命令因相依性不相符而失敗。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-140">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="2f7b1-141">下一個命令 `apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-141">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="2f7b1-142">解除安裝 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="2f7b1-142">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="2f7b1-143">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="2f7b1-143">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="2f7b1-144">因為 18.10 是[過渡版本](https://www.ubuntu.com/about/release-cycle)，所以只[支援社群](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6)。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-144">As 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle), it is only [community supported](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span></span>

<span data-ttu-id="2f7b1-145">18.10 的安裝透過 `snapd`提供支援。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-145">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="2f7b1-146">如需完整指示，請參閱 [Snap 套件][snap]；</span><span class="sxs-lookup"><span data-stu-id="2f7b1-146">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="2f7b1-147">Debian 8</span><span class="sxs-lookup"><span data-stu-id="2f7b1-147">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="2f7b1-148">透過套件存放庫安裝 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="2f7b1-148">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="2f7b1-149">PowerShell Core for Linux 會發佈到套件存放庫，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-149">PowerShell Core, for Linux, is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="2f7b1-150">慣用的方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="2f7b1-150">The preferred method is as follows:</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl apt-transport-https

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

<span data-ttu-id="2f7b1-151">以超級使用者的身分，註冊 Microsoft 存放庫一次。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-151">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="2f7b1-152">註冊之後，您可以使用 `sudo apt-get upgrade powershell` 來更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-152">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="2f7b1-153">Debian 9</span><span class="sxs-lookup"><span data-stu-id="2f7b1-153">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="2f7b1-154">透過套件存放庫安裝 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="2f7b1-154">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="2f7b1-155">PowerShell Core for Linux 會發佈到套件存放庫，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-155">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="2f7b1-156">慣用的方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="2f7b1-156">The preferred method is as follows:</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl gnupg apt-transport-https

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

<span data-ttu-id="2f7b1-157">以超級使用者的身分，註冊 Microsoft 存放庫一次。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-157">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="2f7b1-158">註冊之後，您可以使用 `sudo apt-get upgrade powershell` 來更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-158">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="2f7b1-159">透過直接下載安裝 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="2f7b1-159">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="2f7b1-160">將[版本][]頁面上的 Debian 套件 `powershell_6.2.0-1.debian.9_amd64.deb` 下載至 Debian 電腦。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-160">Download the Debian package `powershell_6.2.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="2f7b1-161">然後，在終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="2f7b1-161">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="2f7b1-162">解除安裝 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="2f7b1-162">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="2f7b1-163">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="2f7b1-163">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="2f7b1-164">此套件也適用於 Oracle Linux 7。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-164">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="2f7b1-165">透過套件存放庫安裝 (慣用) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="2f7b1-165">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="2f7b1-166">PowerShell Core for Linux 會發佈到官方 Microsoft 存放庫，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-166">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="2f7b1-167">以超級使用者的身分，註冊 Microsoft 存放庫一次。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-167">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="2f7b1-168">註冊之後，您可以使用 `sudo yum update powershell` 來更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-168">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="2f7b1-169">透過直接下載安裝 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="2f7b1-169">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="2f7b1-170">使用 [CentOS 7][]，將[版本][]頁面上的 RPM 套件 `powershell-6.2.0-1.rhel.7.x86_64.rpm` 下載至 CentOS 電腦。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-170">Using [CentOS 7][], download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="2f7b1-171">然後，在終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="2f7b1-171">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="2f7b1-172">您可以不使用下載的中繼步驟來安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="2f7b1-172">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="2f7b1-173">解除安裝 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="2f7b1-173">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="2f7b1-175">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="2f7b1-175">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="2f7b1-176">透過套件存放庫安裝 (慣用) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="2f7b1-176">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="2f7b1-177">PowerShell Core for Linux 會發佈到官方 Microsoft 存放庫，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-177">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="2f7b1-178">以超級使用者的身分，註冊 Microsoft 存放庫一次。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-178">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="2f7b1-179">註冊之後，您可以使用 `sudo yum update powershell` 來更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-179">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="2f7b1-180">透過直接下載安裝 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="2f7b1-180">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="2f7b1-181">將[版本][]頁面上的 RPM 套件 `powershell-6.2.0-1.rhel.7.x86_64.rpm` 下載到 Red Hat Enterprise Linux 電腦。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-181">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="2f7b1-182">然後，在終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="2f7b1-182">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="2f7b1-183">您可以不使用下載的中繼步驟來安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="2f7b1-183">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="2f7b1-184">解除安裝 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="2f7b1-184">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="2f7b1-185">openSUSE</span><span class="sxs-lookup"><span data-stu-id="2f7b1-185">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="2f7b1-186">安裝 - openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="2f7b1-186">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="2f7b1-187">安裝 - openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="2f7b1-187">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="2f7b1-188">解除安裝 - openSUSE 42.3、openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="2f7b1-188">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="2f7b1-189">Fedora</span><span class="sxs-lookup"><span data-stu-id="2f7b1-189">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="2f7b1-190">只有 PowerShell Core 6.1 和更新版本才支援 Fedora 28。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-190">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="2f7b1-191">透過套件存放庫安裝 (慣用) - Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="2f7b1-191">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="2f7b1-192">PowerShell Core for Linux 會發佈到官方 Microsoft 存放庫，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-192">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="2f7b1-193">透過直接下載安裝 - Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="2f7b1-193">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="2f7b1-194">將[版本][]頁面上的 RPM 套件 `powershell-6.2.0-1.rhel.7.x86_64.rpm` 下載到 Fedora 電腦。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-194">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="2f7b1-195">然後，在終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="2f7b1-195">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="2f7b1-196">您可以不使用下載的中繼步驟來安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="2f7b1-196">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="2f7b1-197">解除安裝 - Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="2f7b1-197">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="2f7b1-198">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="2f7b1-198">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="2f7b1-199">Arch 支援為實驗性。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-199">Arch support is experimental.</span></span>

<span data-ttu-id="2f7b1-200">PowerShell 可從 [Arch Linux][] 使用者存放庫 (AUR) 取得。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-200">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="2f7b1-201">可以使用[最新的標記版本][arch-release]編譯</span><span class="sxs-lookup"><span data-stu-id="2f7b1-201">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="2f7b1-202">可以從[主機的最新認可][arch-git]編譯</span><span class="sxs-lookup"><span data-stu-id="2f7b1-202">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="2f7b1-203">可以使用[最新版本的二進位檔][arch-bin]安裝</span><span class="sxs-lookup"><span data-stu-id="2f7b1-203">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="2f7b1-204">AUR 中的套件由社群維護，沒有官方支援。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-204">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="2f7b1-205">如需從 AUR 安裝套件的詳細資訊，請參閱 [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) 或社群 [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile)。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-205">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="2f7b1-207">Snap 套件</span><span class="sxs-lookup"><span data-stu-id="2f7b1-207">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="2f7b1-208">取得 snapd</span><span class="sxs-lookup"><span data-stu-id="2f7b1-208">Getting snapd</span></span>

<span data-ttu-id="2f7b1-209">必須有 `snapd` 才能執行 Snap。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-209">`snapd` is required to run snaps.</span></span> <span data-ttu-id="2f7b1-210">請使用[這些指示](https://docs.snapcraft.io/core/install)確認您已安裝 `snapd`。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-210">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="2f7b1-211">透過 Snap 安裝</span><span class="sxs-lookup"><span data-stu-id="2f7b1-211">Installation via Snap</span></span>

<span data-ttu-id="2f7b1-212">適用於 Linux 的 PowerShell Core 會發佈到 [Snap Store](https://snapcraft.io/store)，以供輕鬆安裝及更新。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-212">PowerShell Core for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="2f7b1-213">慣用的方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="2f7b1-213">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="2f7b1-214">若要安裝預覽版，請使用下列方法：</span><span class="sxs-lookup"><span data-stu-id="2f7b1-214">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="2f7b1-215">安裝之後，Snap 將會自動升級。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-215">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="2f7b1-216">您可以使用 `sudo snap refresh powershell` 或 `sudo snap refresh powershell-preview` 觸發升級。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-216">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="2f7b1-217">解除安裝</span><span class="sxs-lookup"><span data-stu-id="2f7b1-217">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="2f7b1-218">或</span><span class="sxs-lookup"><span data-stu-id="2f7b1-218">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="2f7b1-219">Kali</span><span class="sxs-lookup"><span data-stu-id="2f7b1-219">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="2f7b1-220">安裝 - Kali</span><span class="sxs-lookup"><span data-stu-id="2f7b1-220">Installation - Kali</span></span>

```sh
# Download & Install prerequisites
wget http://ftp.us.debian.org/debian/pool/main/i/icu/libicu57_57.1-6+deb9u2_amd64.deb
dpkg -i libicu57_57.1-6+deb9u2_amd64.deb
apt-get update && apt-get install -y curl gnupg apt-transport-https

# Add Microsoft public repository key to APT
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -

# Add Microsoft package repository to the source list
echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" | tee /etc/apt/sources.list.d/powershell.list

# Install PowerShell package
apt-get update && apt-get install -y powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="2f7b1-221">解除安裝 - Kali</span><span class="sxs-lookup"><span data-stu-id="2f7b1-221">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="2f7b1-222">Raspbian</span><span class="sxs-lookup"><span data-stu-id="2f7b1-222">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="2f7b1-223">Raspbian 支援為實驗性。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-223">Raspbian support is experimental.</span></span>

<span data-ttu-id="2f7b1-224">目前只有 Raspbian Stretch 支援 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-224">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="2f7b1-225">CoreCLR 與 PowerShell Core 僅適用於 Pi 2 與 Pi 3 裝置，因為像 [Pi Zero](https://github.com/dotnet/coreclr/issues/10605) \(英文\) 這類的其他裝置，其處理器不受支援。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-225">CoreCLR and PowerShell Core will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="2f7b1-226">下載 [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/)並 遵循[安裝指示](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)來把它安裝到您的 Pi。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-226">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="2f7b1-227">安裝 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="2f7b1-227">Installation - Raspbian</span></span>

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
wget https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.2.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="2f7b1-228">或者，您可以建立一個符號連結來啟動 PowerShell，而無需指定 `pwsh` 二進位檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-228">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="2f7b1-229">解除安裝 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="2f7b1-229">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="2f7b1-230">二進位封存</span><span class="sxs-lookup"><span data-stu-id="2f7b1-230">Binary Archives</span></span>

<span data-ttu-id="2f7b1-231">Linux 平台有 PowerShell 二進位 `tar.gz` 封存，以啟用進階的部署案例。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-231">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="2f7b1-232">相依性</span><span class="sxs-lookup"><span data-stu-id="2f7b1-232">Dependencies</span></span>

<span data-ttu-id="2f7b1-233">PowerShell 會為所有 Linux 發行版本建置可攜式二進位檔。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-233">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="2f7b1-234">但 .NET Core 執行階段在不同的發行版本需要不同的相依性，PowerShell 也一樣。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-234">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="2f7b1-235">下圖顯示不同 Linux 發行版本上，正式支援的 .NET Core 2.0 相依性。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-235">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="2f7b1-236">作業系統</span><span class="sxs-lookup"><span data-stu-id="2f7b1-236">OS</span></span>                 | <span data-ttu-id="2f7b1-237">相依性</span><span class="sxs-lookup"><span data-stu-id="2f7b1-237">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="2f7b1-238">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="2f7b1-238">Ubuntu 16.04</span></span>       | <span data-ttu-id="2f7b1-239">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="2f7b1-239">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="2f7b1-240">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu55</span><span class="sxs-lookup"><span data-stu-id="2f7b1-240">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="2f7b1-241">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="2f7b1-241">Ubuntu 17.10</span></span>       | <span data-ttu-id="2f7b1-242">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="2f7b1-242">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="2f7b1-243">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu57</span><span class="sxs-lookup"><span data-stu-id="2f7b1-243">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="2f7b1-244">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="2f7b1-244">Ubuntu 18.04</span></span>       | <span data-ttu-id="2f7b1-245">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="2f7b1-245">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="2f7b1-246">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu60</span><span class="sxs-lookup"><span data-stu-id="2f7b1-246">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="2f7b1-247">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="2f7b1-247">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="2f7b1-248">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="2f7b1-248">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="2f7b1-249">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52</span><span class="sxs-lookup"><span data-stu-id="2f7b1-249">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="2f7b1-250">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="2f7b1-250">Debian 9 (Stretch)</span></span> | <span data-ttu-id="2f7b1-251">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="2f7b1-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="2f7b1-252">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.2、libicu57</span><span class="sxs-lookup"><span data-stu-id="2f7b1-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="2f7b1-253">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="2f7b1-253">CentOS 7</span></span> <br> <span data-ttu-id="2f7b1-254">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="2f7b1-254">Oracle Linux 7</span></span> <br> <span data-ttu-id="2f7b1-255">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="2f7b1-255">RHEL 7</span></span> | <span data-ttu-id="2f7b1-256">libunwind、libcurl、openssl-libs、libicu</span><span class="sxs-lookup"><span data-stu-id="2f7b1-256">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="2f7b1-257">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="2f7b1-257">openSUSE 42.3</span></span> | <span data-ttu-id="2f7b1-258">libcurl4、libopenssl1_0_0、libicu52_1</span><span class="sxs-lookup"><span data-stu-id="2f7b1-258">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="2f7b1-259">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="2f7b1-259">openSUSE Leap 15</span></span> | <span data-ttu-id="2f7b1-260">libcurl4、libopenssl1_0_0、libicu60_2</span><span class="sxs-lookup"><span data-stu-id="2f7b1-260">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="2f7b1-261">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="2f7b1-261">Fedora 27</span></span> <br> <span data-ttu-id="2f7b1-262">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="2f7b1-262">Fedora 28</span></span> | <span data-ttu-id="2f7b1-263">libunwind、libcurl、openssl-libs、libicu、compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="2f7b1-263">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="2f7b1-264">若要在未正式支援的 Linux 發行版本上部署 PowerShell 二進位檔，您需要在個別步驟中為目標作業系統安裝必要的相依性。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-264">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="2f7b1-265">例如，[Amazon Linux dockerfile][amazon-dockerfile] 會先安裝相依性，再解壓縮 Linux `tar.gz` 封存。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-265">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="2f7b1-266">安裝 - 二進位封存</span><span class="sxs-lookup"><span data-stu-id="2f7b1-266">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="2f7b1-267">Linux</span><span class="sxs-lookup"><span data-stu-id="2f7b1-267">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="2f7b1-268">解除安裝二進位封存</span><span class="sxs-lookup"><span data-stu-id="2f7b1-268">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="2f7b1-269">路徑</span><span class="sxs-lookup"><span data-stu-id="2f7b1-269">Paths</span></span>

* <span data-ttu-id="2f7b1-270">`$PSHOME` 是 `/opt/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="2f7b1-270">`$PSHOME` is `/opt/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="2f7b1-271">會從 `~/.config/powershell/profile.ps1` 讀取使用者設定檔</span><span class="sxs-lookup"><span data-stu-id="2f7b1-271">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="2f7b1-272">會從 `$PSHOME/profile.ps1` 讀取預設設定檔</span><span class="sxs-lookup"><span data-stu-id="2f7b1-272">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="2f7b1-273">會從 `~/.local/share/powershell/Modules` 讀取使用者模組</span><span class="sxs-lookup"><span data-stu-id="2f7b1-273">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="2f7b1-274">會從 `/usr/local/share/powershell/Modules` 讀取共用的模組</span><span class="sxs-lookup"><span data-stu-id="2f7b1-274">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="2f7b1-275">會從 `$PSHOME/Modules` 讀取預設模組</span><span class="sxs-lookup"><span data-stu-id="2f7b1-275">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="2f7b1-276">PSReadline 記錄會記錄在 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="2f7b1-276">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="2f7b1-277">設定檔會遵循 PowerShell 的每個主控件設定，讓預設主控件特定設定檔存在於相同位置的 `Microsoft.PowerShell_profile.ps1`。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-277">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="2f7b1-278">PowerShell 遵循 Linux 上的 [XDG 基底目錄規格][xdg-bds]。</span><span class="sxs-lookup"><span data-stu-id="2f7b1-278">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[版本]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
