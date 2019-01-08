---
title: 在 Linux 上安裝 PowerShell Core
description: 在各種 Linux 發佈上安裝 PowerShell Core 的相關資訊
ms.date: 08/06/2018
ms.openlocfilehash: afb11f053517af592fe42754d543f9f4a9966c5b
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400743"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="5cde1-103">在 Linux 上安裝 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="5cde1-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="5cde1-104">支援 [Ubuntu 14.04][u14]、[Ubuntu 16.04][u16]、[Ubuntu 18.04][u1804]、[Ubuntu 18.10][u1810]、[Debian 8][deb8]、[Debian 9][deb9]、[CentOS 7][cos]、[Red Hat Enterprise Linux (RHEL) 7][rhel7]、[openSUSE 42.3][opensuse]、[openSUSE Leap 15][opensuse]、[Fedora 27][fedora]、[Fedora 28][fedora] 與 [Arch Linux][arch]。</span><span class="sxs-lookup"><span data-stu-id="5cde1-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="5cde1-105">若是未正式支援的 Linux 發佈，您可以嘗試使用 [PowerShell Snap 套件][snap]。</span><span class="sxs-lookup"><span data-stu-id="5cde1-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="5cde1-106">您也可以直接使用 Linux [`tar.gz` 封存][tar]嘗試部署 PowerShell 二進位檔，但您需要根據個別步驟中的作業系統，設定必要的相依性。</span><span class="sxs-lookup"><span data-stu-id="5cde1-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="5cde1-107">GitHub [版本][]頁面上提供所有套件。</span><span class="sxs-lookup"><span data-stu-id="5cde1-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="5cde1-108">安裝套件之後，請從終端機執行 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="5cde1-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="5cde1-109">安裝預覽版本</span><span class="sxs-lookup"><span data-stu-id="5cde1-109">Installing Preview Releases</span></span>

<span data-ttu-id="5cde1-110">透過套件存放庫安裝 Linux 的 PowerShell Core Preview 版本時，套件名稱會從 `powershell` 變更為 `powershell-preview`。</span><span class="sxs-lookup"><span data-stu-id="5cde1-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="5cde1-111">透過直接下載的安裝不會變更，但檔案名稱除外。</span><span class="sxs-lookup"><span data-stu-id="5cde1-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="5cde1-112">下表是使用各種套件管理員安裝穩定和預覽套件的命令：</span><span class="sxs-lookup"><span data-stu-id="5cde1-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="5cde1-113">發行版本</span><span class="sxs-lookup"><span data-stu-id="5cde1-113">Distribution(s)</span></span>|<span data-ttu-id="5cde1-114">穩定命令</span><span class="sxs-lookup"><span data-stu-id="5cde1-114">Stable Command</span></span> | <span data-ttu-id="5cde1-115">預覽命令</span><span class="sxs-lookup"><span data-stu-id="5cde1-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="5cde1-116">Ubuntu、Debian</span><span class="sxs-lookup"><span data-stu-id="5cde1-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="5cde1-117">CentOS、RedHat</span><span class="sxs-lookup"><span data-stu-id="5cde1-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="5cde1-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="5cde1-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="5cde1-119">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="5cde1-119">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="5cde1-120">透過套件存放庫安裝 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="5cde1-120">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="5cde1-121">PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="5cde1-121">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="5cde1-122">這是慣用方法。</span><span class="sxs-lookup"><span data-stu-id="5cde1-122">This is the preferred method.</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/14.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="5cde1-123">以超級使用者的身分，註冊 Microsoft 存放庫。</span><span class="sxs-lookup"><span data-stu-id="5cde1-123">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="5cde1-124">從那時起，您只需要使用`sudo apt-get upgrade powershell`來更新安裝。</span><span class="sxs-lookup"><span data-stu-id="5cde1-124">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="5cde1-125">透過直接下載安裝 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="5cde1-125">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="5cde1-126">將 Debian 套件 `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="5cde1-126">Download the Debian package `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span></span>
<span data-ttu-id="5cde1-127">從[版本][]頁面下載到 Ubuntu 電腦。</span><span class="sxs-lookup"><span data-stu-id="5cde1-127">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="5cde1-128">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="5cde1-128">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="5cde1-129">`dpkg -i` 命令因相依性不相符而失敗。</span><span class="sxs-lookup"><span data-stu-id="5cde1-129">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="5cde1-130">下一個命令 `apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。</span><span class="sxs-lookup"><span data-stu-id="5cde1-130">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="5cde1-131">解除安裝 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="5cde1-131">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="5cde1-132">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="5cde1-132">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="5cde1-133">透過套件存放庫安裝 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="5cde1-133">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="5cde1-134">PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="5cde1-134">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="5cde1-135">這是慣用方法。</span><span class="sxs-lookup"><span data-stu-id="5cde1-135">This is the preferred method.</span></span>

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

<span data-ttu-id="5cde1-136">以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。</span><span class="sxs-lookup"><span data-stu-id="5cde1-136">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="5cde1-137">透過直接下載安裝 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="5cde1-137">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="5cde1-138">將 Debian 套件 `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="5cde1-138">Download the Debian package `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span></span>
<span data-ttu-id="5cde1-139">從[版本][]頁面下載到 Ubuntu 電腦。</span><span class="sxs-lookup"><span data-stu-id="5cde1-139">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="5cde1-140">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="5cde1-140">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="5cde1-141">`dpkg -i` 命令因相依性不相符而失敗。</span><span class="sxs-lookup"><span data-stu-id="5cde1-141">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="5cde1-142">下一個命令 `apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。</span><span class="sxs-lookup"><span data-stu-id="5cde1-142">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="5cde1-143">解除安裝 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="5cde1-143">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="5cde1-144">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="5cde1-144">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="5cde1-145">在 `6.1.0-preview.2` 之後已新增 Ubuntu 18.04 支援</span><span class="sxs-lookup"><span data-stu-id="5cde1-145">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="5cde1-146">透過套件存放庫安裝 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="5cde1-146">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="5cde1-147">PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="5cde1-147">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="5cde1-148">這是慣用方法。</span><span class="sxs-lookup"><span data-stu-id="5cde1-148">This is the preferred method.</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="5cde1-149">以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。</span><span class="sxs-lookup"><span data-stu-id="5cde1-149">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="5cde1-150">透過直接下載安裝 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="5cde1-150">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="5cde1-151">將 Debian 套件 `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="5cde1-151">Download the Debian package `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span></span>
<span data-ttu-id="5cde1-152">從[版本][]頁面下載到 Ubuntu 電腦。</span><span class="sxs-lookup"><span data-stu-id="5cde1-152">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="5cde1-153">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="5cde1-153">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="5cde1-154">`dpkg -i` 命令因相依性不相符而失敗。</span><span class="sxs-lookup"><span data-stu-id="5cde1-154">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="5cde1-155">下一個命令 `apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。</span><span class="sxs-lookup"><span data-stu-id="5cde1-155">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="5cde1-156">解除安裝 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="5cde1-156">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="5cde1-157">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="5cde1-157">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="5cde1-158">在 `6.1.0-preview.3` 之後已新增 Ubuntu 18.10 支援。</span><span class="sxs-lookup"><span data-stu-id="5cde1-158">Support for Ubuntu 18.10 was added after `6.1.0-preview.3`.</span></span>
> <span data-ttu-id="5cde1-159">由於 18.10 是 Daily Build，因此只有社群支援。</span><span class="sxs-lookup"><span data-stu-id="5cde1-159">As 18.10 is a daily build, it is only community supported.</span></span>

<span data-ttu-id="5cde1-160">18.10 的安裝透過 `snapd`提供支援。</span><span class="sxs-lookup"><span data-stu-id="5cde1-160">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="5cde1-161">如需完整指示，請參閱 [Snap 套件][snap]；</span><span class="sxs-lookup"><span data-stu-id="5cde1-161">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="5cde1-162">Debian 8</span><span class="sxs-lookup"><span data-stu-id="5cde1-162">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="5cde1-163">透過套件存放庫安裝 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="5cde1-163">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="5cde1-164">PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="5cde1-164">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="5cde1-165">這是慣用方法。</span><span class="sxs-lookup"><span data-stu-id="5cde1-165">This is the preferred method.</span></span>

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

<span data-ttu-id="5cde1-166">以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。</span><span class="sxs-lookup"><span data-stu-id="5cde1-166">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="5cde1-167">透過直接下載安裝 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="5cde1-167">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="5cde1-168">將 Debian 套件 `powershell_6.1.0-1.debian.8_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="5cde1-168">Download the Debian package `powershell_6.1.0-1.debian.8_amd64.deb`</span></span>
<span data-ttu-id="5cde1-169">從[版本][]頁面下載到 Debian 電腦。</span><span class="sxs-lookup"><span data-stu-id="5cde1-169">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="5cde1-170">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="5cde1-170">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="5cde1-171">`dpkg -i` 命令因相依性不相符而失敗。</span><span class="sxs-lookup"><span data-stu-id="5cde1-171">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="5cde1-172">下一個命令 `apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。</span><span class="sxs-lookup"><span data-stu-id="5cde1-172">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="5cde1-173">解除安裝 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="5cde1-173">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="5cde1-174">Debian 9</span><span class="sxs-lookup"><span data-stu-id="5cde1-174">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="5cde1-175">透過套件存放庫安裝 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="5cde1-175">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="5cde1-176">PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="5cde1-176">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="5cde1-177">這是慣用方法。</span><span class="sxs-lookup"><span data-stu-id="5cde1-177">This is the preferred method.</span></span>

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

<span data-ttu-id="5cde1-178">以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。</span><span class="sxs-lookup"><span data-stu-id="5cde1-178">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="5cde1-179">透過直接下載安裝 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="5cde1-179">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="5cde1-180">將 Debian 套件 `powershell_6.1.0-1.debian.9_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="5cde1-180">Download the Debian package `powershell_6.1.0-1.debian.9_amd64.deb`</span></span>
<span data-ttu-id="5cde1-181">從[版本][]頁面下載到 Debian 電腦。</span><span class="sxs-lookup"><span data-stu-id="5cde1-181">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="5cde1-182">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="5cde1-182">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="5cde1-183">解除安裝 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="5cde1-183">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="5cde1-184">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="5cde1-184">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="5cde1-185">此套件也適用於 Oracle Linux 7。</span><span class="sxs-lookup"><span data-stu-id="5cde1-185">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="5cde1-186">透過套件存放庫安裝 (慣用) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="5cde1-186">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="5cde1-187">PowerShell Core for Linux 會發佈到官方 Microsoft 存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="5cde1-187">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="5cde1-188">以超級使用者身分註冊過 Microsoft 存放庫一次之後，只需要使用 `sudo yum update powershell` 就可以更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="5cde1-188">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="5cde1-189">透過直接下載安裝 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="5cde1-189">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="5cde1-190">使用 [CentOS 7][]，將 RPM 套件 `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="5cde1-190">Using [CentOS 7][], download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="5cde1-191">從[版本][]頁面下載到 CentOS 電腦。</span><span class="sxs-lookup"><span data-stu-id="5cde1-191">from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="5cde1-192">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="5cde1-192">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="5cde1-193">您也可以不使用下載的中繼步驟來安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="5cde1-193">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="5cde1-194">解除安裝 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="5cde1-194">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="5cde1-196">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="5cde1-196">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="5cde1-197">透過套件存放庫安裝 (慣用) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="5cde1-197">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="5cde1-198">PowerShell Core for Linux 會發佈到官方 Microsoft 存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="5cde1-198">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="5cde1-199">以超級使用者身分註冊過 Microsoft 存放庫一次之後，只需要使用 `sudo yum update powershell` 就可以更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="5cde1-199">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="5cde1-200">透過直接下載安裝 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="5cde1-200">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="5cde1-201">將 RPM 套件 `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="5cde1-201">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="5cde1-202">從[版本][]頁面下載到 Red Hat Enterprise Linux 電腦。</span><span class="sxs-lookup"><span data-stu-id="5cde1-202">from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="5cde1-203">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="5cde1-203">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="5cde1-204">您也可以不使用下載的中繼步驟來安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="5cde1-204">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="5cde1-205">解除安裝 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="5cde1-205">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="5cde1-206">openSUSE</span><span class="sxs-lookup"><span data-stu-id="5cde1-206">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="5cde1-207">安裝 - openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="5cde1-207">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="5cde1-208">安裝 - openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="5cde1-208">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="5cde1-209">解除安裝 - openSUSE 42.3、openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="5cde1-209">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="5cde1-210">Fedora</span><span class="sxs-lookup"><span data-stu-id="5cde1-210">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="5cde1-211">只有 PowerShell Core 6.1 和更新版本才支援 Fedora 28。</span><span class="sxs-lookup"><span data-stu-id="5cde1-211">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="5cde1-212">透過套件存放庫安裝 (慣用) - Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="5cde1-212">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="5cde1-213">PowerShell Core for Linux 會發佈到官方 Microsoft 存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="5cde1-213">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="5cde1-214">透過直接下載安裝 - Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="5cde1-214">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="5cde1-215">將 RPM 套件 `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="5cde1-215">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="5cde1-216">從[版本][]頁面下載到 Fedora 電腦。</span><span class="sxs-lookup"><span data-stu-id="5cde1-216">from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="5cde1-217">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="5cde1-217">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="5cde1-218">您也可以不使用下載的中繼步驟來安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="5cde1-218">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="5cde1-219">解除安裝 - Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="5cde1-219">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="5cde1-220">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="5cde1-220">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="5cde1-221">Arch 支援為實驗性。</span><span class="sxs-lookup"><span data-stu-id="5cde1-221">Arch support is experimental.</span></span>

<span data-ttu-id="5cde1-222">PowerShell 可從 [Arch Linux][] 使用者存放庫 (AUR) 取得。</span><span class="sxs-lookup"><span data-stu-id="5cde1-222">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="5cde1-223">它可以使用[最新的標記版本][arch-release]編譯</span><span class="sxs-lookup"><span data-stu-id="5cde1-223">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="5cde1-224">它可以從[主機的最新認可][arch-git]編譯</span><span class="sxs-lookup"><span data-stu-id="5cde1-224">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="5cde1-225">它可以使用[最新版本的二進位檔][arch-bin]安裝</span><span class="sxs-lookup"><span data-stu-id="5cde1-225">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="5cde1-226">AUR 中的套件由社群維護 - 沒有官方支援。</span><span class="sxs-lookup"><span data-stu-id="5cde1-226">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="5cde1-227">如需從 AUR 安裝套件的詳細資訊，請參閱 [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) 或社群 [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile)。</span><span class="sxs-lookup"><span data-stu-id="5cde1-227">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="5cde1-229">Snap 套件</span><span class="sxs-lookup"><span data-stu-id="5cde1-229">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="5cde1-230">取得 snapd</span><span class="sxs-lookup"><span data-stu-id="5cde1-230">Getting snapd</span></span>

<span data-ttu-id="5cde1-231">必須有 `snapd` 才能執行 Snap。</span><span class="sxs-lookup"><span data-stu-id="5cde1-231">`snapd` is required to run snaps.</span></span>
<span data-ttu-id="5cde1-232">請使用[這些指示](https://docs.snapcraft.io/core/install)確認您已安裝 `snapd`。</span><span class="sxs-lookup"><span data-stu-id="5cde1-232">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="5cde1-233">透過 Snap 安裝</span><span class="sxs-lookup"><span data-stu-id="5cde1-233">Installation via Snap</span></span>

<span data-ttu-id="5cde1-234">適用於 Linux 的 PowerShell Core 會發佈到 [Snap 市集](https://snapcraft.io/store)以供輕鬆安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="5cde1-234">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="5cde1-235">這是慣用方法。</span><span class="sxs-lookup"><span data-stu-id="5cde1-235">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="5cde1-236">若要安裝預覽版，請使用下列方法。</span><span class="sxs-lookup"><span data-stu-id="5cde1-236">If you want to install preview version, use following method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="5cde1-237">在安裝之後，Snap 會自動升級，不過您也可以使用 `sudo snap refresh powershell` 或 `sudo snap refresh powershell-preview` 觸發升級。</span><span class="sxs-lookup"><span data-stu-id="5cde1-237">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="5cde1-238">解除安裝</span><span class="sxs-lookup"><span data-stu-id="5cde1-238">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="5cde1-239">或</span><span class="sxs-lookup"><span data-stu-id="5cde1-239">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="5cde1-240">Kali</span><span class="sxs-lookup"><span data-stu-id="5cde1-240">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="5cde1-241">安裝 - Kali</span><span class="sxs-lookup"><span data-stu-id="5cde1-241">Installation - Kali</span></span>

```sh
# Download & Install prerequisites
wget http://ftp.us.debian.org/debian/pool/main/i/icu/libicu57_57.1-9_amd64.deb
dpkg -i libicu57_57.1-9_amd64.deb
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

### <a name="uninstallation---kali"></a><span data-ttu-id="5cde1-242">解除安裝 - Kali</span><span class="sxs-lookup"><span data-stu-id="5cde1-242">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="5cde1-243">Raspbian</span><span class="sxs-lookup"><span data-stu-id="5cde1-243">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="5cde1-244">Raspbian 支援為實驗性。</span><span class="sxs-lookup"><span data-stu-id="5cde1-244">Raspbian support is experimental.</span></span>

<span data-ttu-id="5cde1-245">目前只有 Raspbian Stretch 支援 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="5cde1-245">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="5cde1-246">另外，CoreCLR (和 PowerShell Core) 僅適用於 Pi 2 和 Pi 3 裝置，因為像 [Pi Zero](https://github.com/dotnet/coreclr/issues/10605) 此類的其他裝置，它們的處理器不被支援。</span><span class="sxs-lookup"><span data-stu-id="5cde1-246">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="5cde1-247">下載 [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/)並 遵循[安裝指示](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)來把它安裝到您的 Pi。</span><span class="sxs-lookup"><span data-stu-id="5cde1-247">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="5cde1-248">安裝 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="5cde1-248">Installation - Raspbian</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.1.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="5cde1-249">或者，您可以建立一個符號連結，無需指定 "pwsh" 二進位路徑，便能啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="5cde1-249">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="5cde1-250">解除安裝 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="5cde1-250">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="5cde1-251">二進位封存</span><span class="sxs-lookup"><span data-stu-id="5cde1-251">Binary Archives</span></span>

<span data-ttu-id="5cde1-252">Linux 平台有 PowerShell 二進位 `tar.gz` 封存，以啟用進階的部署案例。</span><span class="sxs-lookup"><span data-stu-id="5cde1-252">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="5cde1-253">相依性</span><span class="sxs-lookup"><span data-stu-id="5cde1-253">Dependencies</span></span>

<span data-ttu-id="5cde1-254">PowerShell 會為所有 Linux 發行版本建置可攜式二進位檔。</span><span class="sxs-lookup"><span data-stu-id="5cde1-254">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="5cde1-255">但 .NET Core 執行階段在不同的發行版本需要不同的相依性，所以 PowerShell 也一樣。</span><span class="sxs-lookup"><span data-stu-id="5cde1-255">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="5cde1-256">下圖顯示不同 Linux 發行版本上，正式支援的 .NET Core 2.0 相依性。</span><span class="sxs-lookup"><span data-stu-id="5cde1-256">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="5cde1-257">作業系統</span><span class="sxs-lookup"><span data-stu-id="5cde1-257">OS</span></span>                 | <span data-ttu-id="5cde1-258">相依性</span><span class="sxs-lookup"><span data-stu-id="5cde1-258">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="5cde1-259">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="5cde1-259">Ubuntu 14.04</span></span>       | <span data-ttu-id="5cde1-260">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="5cde1-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="5cde1-261">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52</span><span class="sxs-lookup"><span data-stu-id="5cde1-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="5cde1-262">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="5cde1-262">Ubuntu 16.04</span></span>       | <span data-ttu-id="5cde1-263">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="5cde1-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="5cde1-264">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu55</span><span class="sxs-lookup"><span data-stu-id="5cde1-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="5cde1-265">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="5cde1-265">Ubuntu 17.10</span></span>       | <span data-ttu-id="5cde1-266">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="5cde1-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="5cde1-267">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu57</span><span class="sxs-lookup"><span data-stu-id="5cde1-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="5cde1-268">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="5cde1-268">Ubuntu 18.04</span></span>       | <span data-ttu-id="5cde1-269">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="5cde1-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="5cde1-270">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu60</span><span class="sxs-lookup"><span data-stu-id="5cde1-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="5cde1-271">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="5cde1-271">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="5cde1-272">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="5cde1-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="5cde1-273">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52</span><span class="sxs-lookup"><span data-stu-id="5cde1-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="5cde1-274">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="5cde1-274">Debian 9 (Stretch)</span></span> | <span data-ttu-id="5cde1-275">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="5cde1-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="5cde1-276">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.2、libicu57</span><span class="sxs-lookup"><span data-stu-id="5cde1-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="5cde1-277">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="5cde1-277">CentOS 7</span></span> <br> <span data-ttu-id="5cde1-278">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="5cde1-278">Oracle Linux 7</span></span> <br> <span data-ttu-id="5cde1-279">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="5cde1-279">RHEL 7</span></span> | <span data-ttu-id="5cde1-280">libunwind、libcurl、openssl-libs、libicu</span><span class="sxs-lookup"><span data-stu-id="5cde1-280">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="5cde1-281">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="5cde1-281">openSUSE 42.3</span></span> | <span data-ttu-id="5cde1-282">libcurl4、libopenssl1_0_0、libicu52_1</span><span class="sxs-lookup"><span data-stu-id="5cde1-282">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="5cde1-283">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="5cde1-283">openSUSE Leap 15</span></span> | <span data-ttu-id="5cde1-284">libcurl4、libopenssl1_0_0、libicu60_2</span><span class="sxs-lookup"><span data-stu-id="5cde1-284">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="5cde1-285">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="5cde1-285">Fedora 27</span></span> <br> <span data-ttu-id="5cde1-286">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="5cde1-286">Fedora 28</span></span> | <span data-ttu-id="5cde1-287">libunwind、libcurl、openssl-libs、libicu、compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="5cde1-287">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="5cde1-288">若要在未正式支援的 Linux 發行版本上部署 PowerShell 二進位檔，您需要在個別步驟中為目標作業系統安裝必要的相依性。</span><span class="sxs-lookup"><span data-stu-id="5cde1-288">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="5cde1-289">例如，[Amazon Linux dockerfile][amazon-dockerfile] 會先安裝相依性，再解壓縮 Linux `tar.gz` 封存。</span><span class="sxs-lookup"><span data-stu-id="5cde1-289">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="5cde1-290">安裝 - 二進位封存</span><span class="sxs-lookup"><span data-stu-id="5cde1-290">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="5cde1-291">Linux</span><span class="sxs-lookup"><span data-stu-id="5cde1-291">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="5cde1-292">解除安裝二進位封存</span><span class="sxs-lookup"><span data-stu-id="5cde1-292">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="5cde1-293">路徑</span><span class="sxs-lookup"><span data-stu-id="5cde1-293">Paths</span></span>

* <span data-ttu-id="5cde1-294">`$PSHOME` 是 `/opt/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="5cde1-294">`$PSHOME` is `/opt/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="5cde1-295">會從 `~/.config/powershell/profile.ps1` 讀取使用者設定檔</span><span class="sxs-lookup"><span data-stu-id="5cde1-295">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="5cde1-296">會從 `$PSHOME/profile.ps1` 讀取預設設定檔</span><span class="sxs-lookup"><span data-stu-id="5cde1-296">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="5cde1-297">會從 `~/.local/share/powershell/Modules` 讀取使用者模組</span><span class="sxs-lookup"><span data-stu-id="5cde1-297">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="5cde1-298">會從 `/usr/local/share/powershell/Modules` 讀取共用的模組</span><span class="sxs-lookup"><span data-stu-id="5cde1-298">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="5cde1-299">會從 `$PSHOME/Modules` 讀取預設模組</span><span class="sxs-lookup"><span data-stu-id="5cde1-299">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="5cde1-300">PSReadline 記錄會記錄在 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="5cde1-300">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="5cde1-301">設定檔會遵循 PowerShell 的每個主控件設定，讓預設主控件特定設定檔存在於相同位置的 `Microsoft.PowerShell_profile.ps1`。</span><span class="sxs-lookup"><span data-stu-id="5cde1-301">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="5cde1-302">PowerShell 遵循 Linux 上的 [XDG 基底目錄規格][xdg-bds]。</span><span class="sxs-lookup"><span data-stu-id="5cde1-302">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[版本]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
