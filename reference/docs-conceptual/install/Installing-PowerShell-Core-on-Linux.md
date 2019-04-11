---
title: 在 Linux 上安裝 PowerShell Core
description: 在各種 Linux 發佈上安裝 PowerShell Core 的相關資訊
ms.date: 08/06/2018
ms.openlocfilehash: 06194550f4e73f9dd38f8cdc25f6c7f698cafce2
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293328"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="01b68-103">在 Linux 上安裝 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="01b68-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="01b68-104">支援 [Ubuntu 14.04][u14]、[Ubuntu 16.04][u16]、[Ubuntu 18.04][u1804]、[Ubuntu 18.10][u1810]、[Debian 9][deb9]、[CentOS 7][cos]、[Red Hat Enterprise Linux (RHEL) 7][rhel7]、[openSUSE 42.3][opensuse]、[openSUSE Leap 15][opensuse]、[Fedora 27][fedora]、[Fedora 28][fedora] 與 [Arch Linux][arch]。</span><span class="sxs-lookup"><span data-stu-id="01b68-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810],  [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="01b68-105">針對未正式支援的 Linux 發佈，您可以嘗試使用 [PowerShell Snap 套件][snap]。</span><span class="sxs-lookup"><span data-stu-id="01b68-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="01b68-106">您也可以直接使用 Linux [`tar.gz` 封存][tar]嘗試部署 PowerShell 二進位檔，但您需要根據個別步驟中的作業系統，設定必要的相依性。</span><span class="sxs-lookup"><span data-stu-id="01b68-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="01b68-107">GitHub [版本][]頁面上提供所有套件。</span><span class="sxs-lookup"><span data-stu-id="01b68-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="01b68-108">安裝套件之後，請從終端機執行 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="01b68-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
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

## <a name="installing-preview-releases"></a><span data-ttu-id="01b68-109">安裝預覽版本</span><span class="sxs-lookup"><span data-stu-id="01b68-109">Installing Preview Releases</span></span>

<span data-ttu-id="01b68-110">透過套件存放庫安裝 Linux 的 PowerShell Core Preview 版本時，套件名稱會從 `powershell` 變更為 `powershell-preview`。</span><span class="sxs-lookup"><span data-stu-id="01b68-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="01b68-111">透過直接下載的安裝不會變更，但檔案名稱除外。</span><span class="sxs-lookup"><span data-stu-id="01b68-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="01b68-112">下表是使用各種套件管理員安裝穩定和預覽套件的命令：</span><span class="sxs-lookup"><span data-stu-id="01b68-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="01b68-113">發行版本</span><span class="sxs-lookup"><span data-stu-id="01b68-113">Distribution(s)</span></span>|<span data-ttu-id="01b68-114">穩定命令</span><span class="sxs-lookup"><span data-stu-id="01b68-114">Stable Command</span></span> | <span data-ttu-id="01b68-115">預覽命令</span><span class="sxs-lookup"><span data-stu-id="01b68-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="01b68-116">Ubuntu、Debian</span><span class="sxs-lookup"><span data-stu-id="01b68-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="01b68-117">CentOS、RedHat</span><span class="sxs-lookup"><span data-stu-id="01b68-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="01b68-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="01b68-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="01b68-119">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="01b68-119">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="01b68-120">透過套件存放庫安裝 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="01b68-120">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="01b68-121">PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="01b68-121">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="01b68-122">這是慣用方法。</span><span class="sxs-lookup"><span data-stu-id="01b68-122">This is the preferred method.</span></span>

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

<span data-ttu-id="01b68-123">以超級使用者的身分，註冊 Microsoft 存放庫。</span><span class="sxs-lookup"><span data-stu-id="01b68-123">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="01b68-124">從那時起，您只需要使用`sudo apt-get upgrade powershell`來更新安裝。</span><span class="sxs-lookup"><span data-stu-id="01b68-124">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="01b68-125">透過直接下載安裝 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="01b68-125">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="01b68-126">下載 Debian 套件</span><span class="sxs-lookup"><span data-stu-id="01b68-126">Download the Debian package</span></span>
`powershell_6.2.0-1.ubuntu.14.04_amd64.deb`
<span data-ttu-id="01b68-127">從[版本][]頁面下載到 Ubuntu 電腦。</span><span class="sxs-lookup"><span data-stu-id="01b68-127">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="01b68-128">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="01b68-128">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="01b68-129">`dpkg -i` 命令因相依性不相符而失敗。</span><span class="sxs-lookup"><span data-stu-id="01b68-129">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="01b68-130">下一個命令 `apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。</span><span class="sxs-lookup"><span data-stu-id="01b68-130">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="01b68-131">解除安裝 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="01b68-131">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="01b68-132">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="01b68-132">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="01b68-133">透過套件存放庫安裝 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="01b68-133">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="01b68-134">PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="01b68-134">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="01b68-135">這是慣用方法。</span><span class="sxs-lookup"><span data-stu-id="01b68-135">This is the preferred method.</span></span>

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

<span data-ttu-id="01b68-136">以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。</span><span class="sxs-lookup"><span data-stu-id="01b68-136">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="01b68-137">透過直接下載安裝 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="01b68-137">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="01b68-138">下載 Debian 套件</span><span class="sxs-lookup"><span data-stu-id="01b68-138">Download the Debian package</span></span>
`powershell_6.2.0-1.ubuntu.16.04_amd64.deb`
<span data-ttu-id="01b68-139">從[版本][]頁面下載到 Ubuntu 電腦。</span><span class="sxs-lookup"><span data-stu-id="01b68-139">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="01b68-140">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="01b68-140">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="01b68-141">`dpkg -i` 命令因相依性不相符而失敗。</span><span class="sxs-lookup"><span data-stu-id="01b68-141">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="01b68-142">下一個命令 `apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。</span><span class="sxs-lookup"><span data-stu-id="01b68-142">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="01b68-143">解除安裝 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="01b68-143">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="01b68-144">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="01b68-144">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="01b68-145">透過套件存放庫安裝 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="01b68-145">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="01b68-146">PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="01b68-146">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="01b68-147">這是慣用方法。</span><span class="sxs-lookup"><span data-stu-id="01b68-147">This is the preferred method.</span></span>

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

<span data-ttu-id="01b68-148">以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。</span><span class="sxs-lookup"><span data-stu-id="01b68-148">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="01b68-149">透過直接下載安裝 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="01b68-149">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="01b68-150">下載 Debian 套件</span><span class="sxs-lookup"><span data-stu-id="01b68-150">Download the Debian package</span></span>
`powershell_6.2.0-1.ubuntu.18.04_amd64.deb`
<span data-ttu-id="01b68-151">從[版本][]頁面下載到 Ubuntu 電腦。</span><span class="sxs-lookup"><span data-stu-id="01b68-151">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="01b68-152">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="01b68-152">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="01b68-153">`dpkg -i` 命令因相依性不相符而失敗。</span><span class="sxs-lookup"><span data-stu-id="01b68-153">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="01b68-154">下一個命令 `apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。</span><span class="sxs-lookup"><span data-stu-id="01b68-154">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="01b68-155">解除安裝 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="01b68-155">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="01b68-156">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="01b68-156">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="01b68-157">因為 18.10 是[過渡版本](https://www.ubuntu.com/about/release-cycle)，所以只[支援社群](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6)。</span><span class="sxs-lookup"><span data-stu-id="01b68-157">As 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle), it is only [community supported](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span></span>

<span data-ttu-id="01b68-158">18.10 的安裝透過 `snapd`提供支援。</span><span class="sxs-lookup"><span data-stu-id="01b68-158">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="01b68-159">如需完整指示，請參閱 [Snap 套件][snap]；</span><span class="sxs-lookup"><span data-stu-id="01b68-159">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="01b68-160">Debian 8</span><span class="sxs-lookup"><span data-stu-id="01b68-160">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="01b68-161">透過套件存放庫安裝 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="01b68-161">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="01b68-162">PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="01b68-162">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="01b68-163">這是慣用方法。</span><span class="sxs-lookup"><span data-stu-id="01b68-163">This is the preferred method.</span></span>

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

<span data-ttu-id="01b68-164">以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。</span><span class="sxs-lookup"><span data-stu-id="01b68-164">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

## <a name="debian-9"></a><span data-ttu-id="01b68-165">Debian 9</span><span class="sxs-lookup"><span data-stu-id="01b68-165">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="01b68-166">透過套件存放庫安裝 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="01b68-166">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="01b68-167">PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="01b68-167">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="01b68-168">這是慣用方法。</span><span class="sxs-lookup"><span data-stu-id="01b68-168">This is the preferred method.</span></span>

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

<span data-ttu-id="01b68-169">以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。</span><span class="sxs-lookup"><span data-stu-id="01b68-169">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="01b68-170">透過直接下載安裝 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="01b68-170">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="01b68-171">下載 Debian 套件</span><span class="sxs-lookup"><span data-stu-id="01b68-171">Download the Debian package</span></span>
`powershell_6.2.0-1.debian.9_amd64.deb`
<span data-ttu-id="01b68-172">從[版本][]頁面下載到 Debian 電腦。</span><span class="sxs-lookup"><span data-stu-id="01b68-172">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="01b68-173">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="01b68-173">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="01b68-174">解除安裝 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="01b68-174">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="01b68-175">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="01b68-175">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="01b68-176">此套件也適用於 Oracle Linux 7。</span><span class="sxs-lookup"><span data-stu-id="01b68-176">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="01b68-177">透過套件存放庫安裝 (慣用) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="01b68-177">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="01b68-178">PowerShell Core for Linux 會發佈到官方 Microsoft 存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="01b68-178">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="01b68-179">以超級使用者身分註冊過 Microsoft 存放庫一次之後，只需要使用 `sudo yum update powershell` 就可以更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="01b68-179">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="01b68-180">透過直接下載安裝 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="01b68-180">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="01b68-181">使用 [CentOS 7][] 下載 RPM 套件</span><span class="sxs-lookup"><span data-stu-id="01b68-181">Using [CentOS 7][], download the RPM package</span></span>
`powershell-6.2.0-1.rhel.7.x86_64.rpm`
<span data-ttu-id="01b68-182">從[版本][]頁面下載到 CentOS 電腦。</span><span class="sxs-lookup"><span data-stu-id="01b68-182">from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="01b68-183">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="01b68-183">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="01b68-184">您也可以不使用下載的中繼步驟來安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="01b68-184">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="01b68-185">解除安裝 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="01b68-185">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[<span data-ttu-id="01b68-186">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="01b68-186">CentOS 7</span></span>]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="01b68-187">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="01b68-187">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="01b68-188">透過套件存放庫安裝 (慣用) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="01b68-188">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="01b68-189">PowerShell Core for Linux 會發佈到官方 Microsoft 存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="01b68-189">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="01b68-190">以超級使用者身分註冊過 Microsoft 存放庫一次之後，只需要使用 `sudo yum update powershell` 就可以更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="01b68-190">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="01b68-191">透過直接下載安裝 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="01b68-191">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="01b68-192">下載 RPM 套件</span><span class="sxs-lookup"><span data-stu-id="01b68-192">Download the RPM package</span></span>
`powershell-6.2.0-1.rhel.7.x86_64.rpm`
<span data-ttu-id="01b68-193">從[版本][]頁面下載到 Red Hat Enterprise Linux 電腦。</span><span class="sxs-lookup"><span data-stu-id="01b68-193">from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="01b68-194">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="01b68-194">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="01b68-195">您也可以不使用下載的中繼步驟來安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="01b68-195">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="01b68-196">解除安裝 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="01b68-196">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="01b68-197">openSUSE</span><span class="sxs-lookup"><span data-stu-id="01b68-197">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="01b68-198">安裝 - openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="01b68-198">Installation - openSUSE 42.3</span></span>

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="01b68-199">安裝 - openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="01b68-199">Installation - openSUSE Leap 15</span></span>

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="01b68-200">解除安裝 - openSUSE 42.3、openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="01b68-200">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="01b68-201">Fedora</span><span class="sxs-lookup"><span data-stu-id="01b68-201">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="01b68-202">只有 PowerShell Core 6.1 和更新版本才支援 Fedora 28。</span><span class="sxs-lookup"><span data-stu-id="01b68-202">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="01b68-203">透過套件存放庫安裝 (慣用) - Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="01b68-203">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="01b68-204">PowerShell Core for Linux 會發佈到官方 Microsoft 存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="01b68-204">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="01b68-205">透過直接下載安裝 - Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="01b68-205">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="01b68-206">下載 RPM 套件</span><span class="sxs-lookup"><span data-stu-id="01b68-206">Download the RPM package</span></span>
`powershell-6.2.0-1.rhel.7.x86_64.rpm`
<span data-ttu-id="01b68-207">從[版本][]頁面下載到 Fedora 電腦。</span><span class="sxs-lookup"><span data-stu-id="01b68-207">from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="01b68-208">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="01b68-208">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="01b68-209">您也可以不使用下載的中繼步驟來安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="01b68-209">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="01b68-210">解除安裝 - Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="01b68-210">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="01b68-211">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="01b68-211">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="01b68-212">Arch 支援為實驗性。</span><span class="sxs-lookup"><span data-stu-id="01b68-212">Arch support is experimental.</span></span>

<span data-ttu-id="01b68-213">PowerShell 可從 [Arch Linux][] 使用者存放庫 (AUR) 取得。</span><span class="sxs-lookup"><span data-stu-id="01b68-213">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="01b68-214">它可以使用[最新的標記版本][arch-release]編譯</span><span class="sxs-lookup"><span data-stu-id="01b68-214">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="01b68-215">它可以從[主機的最新認可][arch-git]編譯</span><span class="sxs-lookup"><span data-stu-id="01b68-215">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="01b68-216">它可以使用[最新版本的二進位檔][arch-bin]安裝</span><span class="sxs-lookup"><span data-stu-id="01b68-216">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="01b68-217">AUR 中的套件由社群維護 - 沒有官方支援。</span><span class="sxs-lookup"><span data-stu-id="01b68-217">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="01b68-218">如需從 AUR 安裝套件的詳細資訊，請參閱 [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) 或社群 [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile)。</span><span class="sxs-lookup"><span data-stu-id="01b68-218">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[<span data-ttu-id="01b68-219">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="01b68-219">Arch Linux</span></span>]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="01b68-220">Snap 套件</span><span class="sxs-lookup"><span data-stu-id="01b68-220">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="01b68-221">取得 snapd</span><span class="sxs-lookup"><span data-stu-id="01b68-221">Getting snapd</span></span>

`snapd` <span data-ttu-id="01b68-222">必須有下列項目才能執行 Snap：</span><span class="sxs-lookup"><span data-stu-id="01b68-222">is required to run snaps.</span></span>
<span data-ttu-id="01b68-223">請使用[這些指示](https://docs.snapcraft.io/core/install)確認您已安裝 `snapd`。</span><span class="sxs-lookup"><span data-stu-id="01b68-223">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="01b68-224">透過 Snap 安裝</span><span class="sxs-lookup"><span data-stu-id="01b68-224">Installation via Snap</span></span>

<span data-ttu-id="01b68-225">適用於 Linux 的 PowerShell Core 會發佈到 [Snap 市集](https://snapcraft.io/store)以供輕鬆安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="01b68-225">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="01b68-226">這是慣用方法。</span><span class="sxs-lookup"><span data-stu-id="01b68-226">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="01b68-227">若要安裝預覽版，請使用下列方法。</span><span class="sxs-lookup"><span data-stu-id="01b68-227">If you want to install preview version, use following method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="01b68-228">在安裝之後，Snap 會自動升級，不過您也可以使用 `sudo snap refresh powershell` 或 `sudo snap refresh powershell-preview` 觸發升級。</span><span class="sxs-lookup"><span data-stu-id="01b68-228">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="01b68-229">解除安裝</span><span class="sxs-lookup"><span data-stu-id="01b68-229">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="01b68-230">或</span><span class="sxs-lookup"><span data-stu-id="01b68-230">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="01b68-231">Kali</span><span class="sxs-lookup"><span data-stu-id="01b68-231">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="01b68-232">安裝 - Kali</span><span class="sxs-lookup"><span data-stu-id="01b68-232">Installation - Kali</span></span>

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

### <a name="uninstallation---kali"></a><span data-ttu-id="01b68-233">解除安裝 - Kali</span><span class="sxs-lookup"><span data-stu-id="01b68-233">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="01b68-234">Raspbian</span><span class="sxs-lookup"><span data-stu-id="01b68-234">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="01b68-235">Raspbian 支援為實驗性。</span><span class="sxs-lookup"><span data-stu-id="01b68-235">Raspbian support is experimental.</span></span>

<span data-ttu-id="01b68-236">目前只有 Raspbian Stretch 支援 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="01b68-236">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="01b68-237">另外，CoreCLR (和 PowerShell Core) 僅適用於 Pi 2 和 Pi 3 裝置，因為像 [Pi Zero](https://github.com/dotnet/coreclr/issues/10605) 此類的其他裝置，它們的處理器不被支援。</span><span class="sxs-lookup"><span data-stu-id="01b68-237">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="01b68-238">下載 [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/)並 遵循[安裝指示](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)來把它安裝到您的 Pi。</span><span class="sxs-lookup"><span data-stu-id="01b68-238">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="01b68-239">安裝 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="01b68-239">Installation - Raspbian</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.2.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="01b68-240">或者，您可以建立一個符號連結，無需指定 "pwsh" 二進位路徑，便能啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="01b68-240">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="01b68-241">解除安裝 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="01b68-241">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="01b68-242">二進位封存</span><span class="sxs-lookup"><span data-stu-id="01b68-242">Binary Archives</span></span>

<span data-ttu-id="01b68-243">Linux 平台有 PowerShell 二進位 `tar.gz` 封存，以啟用進階的部署案例。</span><span class="sxs-lookup"><span data-stu-id="01b68-243">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="01b68-244">相依性</span><span class="sxs-lookup"><span data-stu-id="01b68-244">Dependencies</span></span>

<span data-ttu-id="01b68-245">PowerShell 會為所有 Linux 發行版本建置可攜式二進位檔。</span><span class="sxs-lookup"><span data-stu-id="01b68-245">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="01b68-246">但 .NET Core 執行階段在不同的發行版本需要不同的相依性，所以 PowerShell 也一樣。</span><span class="sxs-lookup"><span data-stu-id="01b68-246">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="01b68-247">下圖顯示不同 Linux 發行版本上，正式支援的 .NET Core 2.0 相依性。</span><span class="sxs-lookup"><span data-stu-id="01b68-247">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="01b68-248">作業系統</span><span class="sxs-lookup"><span data-stu-id="01b68-248">OS</span></span>                 | <span data-ttu-id="01b68-249">相依性</span><span class="sxs-lookup"><span data-stu-id="01b68-249">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="01b68-250">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="01b68-250">Ubuntu 14.04</span></span>       | <span data-ttu-id="01b68-251">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="01b68-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="01b68-252">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52</span><span class="sxs-lookup"><span data-stu-id="01b68-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="01b68-253">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="01b68-253">Ubuntu 16.04</span></span>       | <span data-ttu-id="01b68-254">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="01b68-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="01b68-255">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu55</span><span class="sxs-lookup"><span data-stu-id="01b68-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="01b68-256">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="01b68-256">Ubuntu 17.10</span></span>       | <span data-ttu-id="01b68-257">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="01b68-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="01b68-258">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu57</span><span class="sxs-lookup"><span data-stu-id="01b68-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="01b68-259">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="01b68-259">Ubuntu 18.04</span></span>       | <span data-ttu-id="01b68-260">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="01b68-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="01b68-261">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu60</span><span class="sxs-lookup"><span data-stu-id="01b68-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="01b68-262">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="01b68-262">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="01b68-263">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="01b68-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="01b68-264">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52</span><span class="sxs-lookup"><span data-stu-id="01b68-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="01b68-265">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="01b68-265">Debian 9 (Stretch)</span></span> | <span data-ttu-id="01b68-266">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="01b68-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="01b68-267">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.2、libicu57</span><span class="sxs-lookup"><span data-stu-id="01b68-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="01b68-268">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="01b68-268">CentOS 7</span></span> <br> <span data-ttu-id="01b68-269">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="01b68-269">Oracle Linux 7</span></span> <br> <span data-ttu-id="01b68-270">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="01b68-270">RHEL 7</span></span> | <span data-ttu-id="01b68-271">libunwind、libcurl、openssl-libs、libicu</span><span class="sxs-lookup"><span data-stu-id="01b68-271">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="01b68-272">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="01b68-272">openSUSE 42.3</span></span> | <span data-ttu-id="01b68-273">libcurl4、libopenssl1_0_0、libicu52_1</span><span class="sxs-lookup"><span data-stu-id="01b68-273">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="01b68-274">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="01b68-274">openSUSE Leap 15</span></span> | <span data-ttu-id="01b68-275">libcurl4、libopenssl1_0_0、libicu60_2</span><span class="sxs-lookup"><span data-stu-id="01b68-275">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="01b68-276">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="01b68-276">Fedora 27</span></span> <br> <span data-ttu-id="01b68-277">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="01b68-277">Fedora 28</span></span> | <span data-ttu-id="01b68-278">libunwind、libcurl、openssl-libs、libicu、compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="01b68-278">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="01b68-279">若要在未正式支援的 Linux 發行版本上部署 PowerShell 二進位檔，您需要在個別步驟中為目標作業系統安裝必要的相依性。</span><span class="sxs-lookup"><span data-stu-id="01b68-279">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="01b68-280">例如，[Amazon Linux dockerfile][amazon-dockerfile] 會先安裝相依性，再解壓縮 Linux `tar.gz` 封存。</span><span class="sxs-lookup"><span data-stu-id="01b68-280">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="01b68-281">安裝 - 二進位封存</span><span class="sxs-lookup"><span data-stu-id="01b68-281">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="01b68-282">Linux</span><span class="sxs-lookup"><span data-stu-id="01b68-282">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="01b68-283">解除安裝二進位封存</span><span class="sxs-lookup"><span data-stu-id="01b68-283">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="01b68-284">路徑</span><span class="sxs-lookup"><span data-stu-id="01b68-284">Paths</span></span>

* `$PSHOME` <span data-ttu-id="01b68-285">是</span><span class="sxs-lookup"><span data-stu-id="01b68-285">is</span></span> `/opt/microsoft/powershell/6.2.0/`
* <span data-ttu-id="01b68-286">使用者設定檔會讀取自</span><span class="sxs-lookup"><span data-stu-id="01b68-286">User profiles will be read from</span></span> `~/.config/powershell/profile.ps1`
* <span data-ttu-id="01b68-287">預設設定檔會讀取自</span><span class="sxs-lookup"><span data-stu-id="01b68-287">Default profiles will be read from</span></span> `$PSHOME/profile.ps1`
* <span data-ttu-id="01b68-288">使用者模組會讀取自</span><span class="sxs-lookup"><span data-stu-id="01b68-288">User modules will be read from</span></span> `~/.local/share/powershell/Modules`
* <span data-ttu-id="01b68-289">共用模組會讀取自</span><span class="sxs-lookup"><span data-stu-id="01b68-289">Shared modules will be read from</span></span> `/usr/local/share/powershell/Modules`
* <span data-ttu-id="01b68-290">預設模組會讀取自</span><span class="sxs-lookup"><span data-stu-id="01b68-290">Default modules will be read from</span></span> `$PSHOME/Modules`
* <span data-ttu-id="01b68-291">PSReadline 記錄會記錄在</span><span class="sxs-lookup"><span data-stu-id="01b68-291">PSReadline history will be recorded to</span></span> `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

<span data-ttu-id="01b68-292">設定檔會遵循 PowerShell 的每個主控件設定，讓預設主控件特定設定檔存在於相同位置的 `Microsoft.PowerShell_profile.ps1`。</span><span class="sxs-lookup"><span data-stu-id="01b68-292">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="01b68-293">PowerShell 遵循 Linux 上的 [XDG 基底目錄規格][xdg-bds]。</span><span class="sxs-lookup"><span data-stu-id="01b68-293">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[<span data-ttu-id="01b68-294">版本</span><span class="sxs-lookup"><span data-stu-id="01b68-294">releases</span></span>]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
