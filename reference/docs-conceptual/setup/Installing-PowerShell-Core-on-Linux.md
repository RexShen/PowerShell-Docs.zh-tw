---
title: 在 Linux 上安裝 PowerShell Core
description: 在各種 Linux 發佈上安裝 PowerShell Core 的相關資訊
ms.date: 08/06/2018
ms.openlocfilehash: 0a1f30ef75a0feeb97df9a35a08d6b0d3edaeccf
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133070"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="c6bae-103">在 Linux 上安裝 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="c6bae-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="c6bae-104">支援 [Ubuntu 14.04][u14]、[Ubuntu 16.04][u16]、[Ubuntu 18.10][u18]、[Debian 8][deb8]、[Debian 9][deb9]、[CentOS 7][cos]、[Red Hat Enterprise Linux (RHEL) 7][rhel7]、[OpenSUSE 42.3][opensuse]、[Fedora 27][fedora]、[Fedora 28][fedora] 與 [Arch Linux][arch]。</span><span class="sxs-lookup"><span data-stu-id="c6bae-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10][u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="c6bae-105">針對未正式支援的 Linux 發佈，您可以嘗試使用 [PowerShell Snap 套件][snap]。</span><span class="sxs-lookup"><span data-stu-id="c6bae-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="c6bae-106">您也可以直接使用 Linux [`tar.gz` 封存][tar]嘗試部署 PowerShell 二進位檔，但您需要根據個別步驟中的作業系統，設定必要的相依性。</span><span class="sxs-lookup"><span data-stu-id="c6bae-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="c6bae-107">GitHub [版本][]頁面上提供所有套件。</span><span class="sxs-lookup"><span data-stu-id="c6bae-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="c6bae-108">安裝套件之後，請從終端機執行 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="c6bae-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u18]: #ubuntu-1810
[u18]: #ubuntu-1804
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-423
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="c6bae-109">安裝預覽版本</span><span class="sxs-lookup"><span data-stu-id="c6bae-109">Installing Preview Releases</span></span>

<span data-ttu-id="c6bae-110">透過套件存放庫安裝 Linux 的 PowerShell Core Preview 版本時，套件名稱會從 `powershell` 變更為 `powershell-preview`。</span><span class="sxs-lookup"><span data-stu-id="c6bae-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="c6bae-111">透過直接下載的安裝不會變更，但檔案名稱除外。</span><span class="sxs-lookup"><span data-stu-id="c6bae-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="c6bae-112">下表是使用各種套件管理員安裝穩定和預覽套件的命令：</span><span class="sxs-lookup"><span data-stu-id="c6bae-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="c6bae-113">發行版本</span><span class="sxs-lookup"><span data-stu-id="c6bae-113">Distribution(s)</span></span>|<span data-ttu-id="c6bae-114">穩定命令</span><span class="sxs-lookup"><span data-stu-id="c6bae-114">Stable Command</span></span> | <span data-ttu-id="c6bae-115">預覽命令</span><span class="sxs-lookup"><span data-stu-id="c6bae-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="c6bae-116">Ubuntu、Debian</span><span class="sxs-lookup"><span data-stu-id="c6bae-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="c6bae-117">CentOS、RedHat</span><span class="sxs-lookup"><span data-stu-id="c6bae-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="c6bae-118">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="c6bae-118">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="c6bae-119">Fedora</span><span class="sxs-lookup"><span data-stu-id="c6bae-119">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="c6bae-120">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="c6bae-120">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="c6bae-121">透過套件存放庫安裝 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="c6bae-121">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="c6bae-122">PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="c6bae-122">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c6bae-123">這是慣用方法。</span><span class="sxs-lookup"><span data-stu-id="c6bae-123">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/14.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="c6bae-124">以超級使用者的身分，註冊 Microsoft 存放庫。</span><span class="sxs-lookup"><span data-stu-id="c6bae-124">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="c6bae-125">從那時起，您只需要使用`sudo apt-get upgrade powershell`來更新安裝。</span><span class="sxs-lookup"><span data-stu-id="c6bae-125">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="c6bae-126">透過直接下載安裝 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="c6bae-126">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="c6bae-127">將 Debian 套件 `powershell_6.0.3-1.ubuntu.14.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="c6bae-127">Download the Debian package `powershell_6.0.3-1.ubuntu.14.04_amd64.deb`</span></span>
<span data-ttu-id="c6bae-128">從[版本][]頁面下載到 Ubuntu 電腦。</span><span class="sxs-lookup"><span data-stu-id="c6bae-128">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="c6bae-129">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="c6bae-129">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.3-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="c6bae-130">`dpkg -i` 命令因相依性不相符而失敗。</span><span class="sxs-lookup"><span data-stu-id="c6bae-130">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="c6bae-131">下一個命令 `apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。</span><span class="sxs-lookup"><span data-stu-id="c6bae-131">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="c6bae-132">解除安裝 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="c6bae-132">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="c6bae-133">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="c6bae-133">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="c6bae-134">透過套件存放庫安裝 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="c6bae-134">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="c6bae-135">PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="c6bae-135">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c6bae-136">這是慣用方法。</span><span class="sxs-lookup"><span data-stu-id="c6bae-136">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/16.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="c6bae-137">以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。</span><span class="sxs-lookup"><span data-stu-id="c6bae-137">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="c6bae-138">透過直接下載安裝 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="c6bae-138">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="c6bae-139">將 Debian 套件 `powershell_6.0.3-1.ubuntu.16.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="c6bae-139">Download the Debian package `powershell_6.0.3-1.ubuntu.16.04_amd64.deb`</span></span>
<span data-ttu-id="c6bae-140">從[版本][]頁面下載到 Ubuntu 電腦。</span><span class="sxs-lookup"><span data-stu-id="c6bae-140">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="c6bae-141">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="c6bae-141">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.3-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="c6bae-142">`dpkg -i` 命令因相依性不相符而失敗。</span><span class="sxs-lookup"><span data-stu-id="c6bae-142">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="c6bae-143">下一個命令 `apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。</span><span class="sxs-lookup"><span data-stu-id="c6bae-143">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="c6bae-144">解除安裝 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="c6bae-144">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="c6bae-145">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="c6bae-145">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="c6bae-146">在 `6.1.0-preview.2` 之後已新增 Ubuntu 18.04 支援</span><span class="sxs-lookup"><span data-stu-id="c6bae-146">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="c6bae-147">透過套件存放庫安裝 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="c6bae-147">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="c6bae-148">PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="c6bae-148">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c6bae-149">這是慣用方法。</span><span class="sxs-lookup"><span data-stu-id="c6bae-149">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell-preview

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="c6bae-150">以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。</span><span class="sxs-lookup"><span data-stu-id="c6bae-150">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="c6bae-151">透過直接下載安裝 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="c6bae-151">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="c6bae-152">將 Debian 套件 `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="c6bae-152">Download the Debian package `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb`</span></span>
<span data-ttu-id="c6bae-153">從[版本][]頁面下載到 Ubuntu 電腦。</span><span class="sxs-lookup"><span data-stu-id="c6bae-153">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="c6bae-154">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="c6bae-154">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="c6bae-155">`dpkg -i` 命令因相依性不相符而失敗。</span><span class="sxs-lookup"><span data-stu-id="c6bae-155">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="c6bae-156">下一個命令 `apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。</span><span class="sxs-lookup"><span data-stu-id="c6bae-156">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="c6bae-157">解除安裝 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="c6bae-157">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="c6bae-158">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="c6bae-158">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="c6bae-159">在 `6.1.0-preview.3` 之後已新增 Ubuntu 18.10 支援。</span><span class="sxs-lookup"><span data-stu-id="c6bae-159">Support for Ubuntu 18.10 was added after `6.1.0-preview.3`.</span></span>
> <span data-ttu-id="c6bae-160">由於 18.10 是 Daily Build，因此只有社群支援。</span><span class="sxs-lookup"><span data-stu-id="c6bae-160">As 18.10 is a daily build, it is only community supported.</span></span>

<span data-ttu-id="c6bae-161">18.10 的安裝透過 `snapd`提供支援。</span><span class="sxs-lookup"><span data-stu-id="c6bae-161">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="c6bae-162">如需完整指示，請參閱 [Snap 套件][snap]；</span><span class="sxs-lookup"><span data-stu-id="c6bae-162">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="c6bae-163">Debian 8</span><span class="sxs-lookup"><span data-stu-id="c6bae-163">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="c6bae-164">透過套件存放庫安裝 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="c6bae-164">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="c6bae-165">PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="c6bae-165">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c6bae-166">這是慣用方法。</span><span class="sxs-lookup"><span data-stu-id="c6bae-166">This is the preferred method.</span></span>

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

<span data-ttu-id="c6bae-167">以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。</span><span class="sxs-lookup"><span data-stu-id="c6bae-167">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="c6bae-168">透過直接下載安裝 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="c6bae-168">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="c6bae-169">將 Debian 套件 `powershell_6.0.3-1.debian.8_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="c6bae-169">Download the Debian package `powershell_6.0.3-1.debian.8_amd64.deb`</span></span>
<span data-ttu-id="c6bae-170">從[版本][]頁面下載到 Debian 電腦。</span><span class="sxs-lookup"><span data-stu-id="c6bae-170">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="c6bae-171">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="c6bae-171">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.3-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="c6bae-172">`dpkg -i` 命令因相依性不相符而失敗。</span><span class="sxs-lookup"><span data-stu-id="c6bae-172">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="c6bae-173">下一個命令 `apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。</span><span class="sxs-lookup"><span data-stu-id="c6bae-173">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="c6bae-174">解除安裝 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="c6bae-174">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="c6bae-175">Debian 9</span><span class="sxs-lookup"><span data-stu-id="c6bae-175">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="c6bae-176">透過套件存放庫安裝 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="c6bae-176">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="c6bae-177">PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="c6bae-177">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c6bae-178">這是慣用方法。</span><span class="sxs-lookup"><span data-stu-id="c6bae-178">This is the preferred method.</span></span>

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

<span data-ttu-id="c6bae-179">以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。</span><span class="sxs-lookup"><span data-stu-id="c6bae-179">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="c6bae-180">透過直接下載安裝 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="c6bae-180">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="c6bae-181">將 Debian 套件 `powershell_6.0.3-1.debian.9_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="c6bae-181">Download the Debian package `powershell_6.0.3-1.debian.9_amd64.deb`</span></span>
<span data-ttu-id="c6bae-182">從[版本][]頁面下載到 Debian 電腦。</span><span class="sxs-lookup"><span data-stu-id="c6bae-182">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="c6bae-183">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="c6bae-183">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.3-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="c6bae-184">解除安裝 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="c6bae-184">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="c6bae-185">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c6bae-185">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="c6bae-186">此套件也適用於 Oracle Linux 7。</span><span class="sxs-lookup"><span data-stu-id="c6bae-186">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="c6bae-187">透過套件存放庫安裝 (慣用) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c6bae-187">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="c6bae-188">PowerShell Core for Linux 會發佈到官方 Microsoft 存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="c6bae-188">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="c6bae-189">以超級使用者身分註冊過 Microsoft 存放庫一次之後，只需要使用 `sudo yum update powershell` 就可以更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="c6bae-189">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="c6bae-190">透過直接下載安裝 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c6bae-190">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="c6bae-191">使用 [CentOS 7][]，將 RPM 套件 `powershell-6.0.3-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="c6bae-191">Using [CentOS 7][], download the RPM package `powershell-6.0.3-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="c6bae-192">從[版本][]頁面下載到 CentOS 電腦。</span><span class="sxs-lookup"><span data-stu-id="c6bae-192">from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="c6bae-193">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="c6bae-193">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.3-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="c6bae-194">您也可以不使用下載的中繼步驟來安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="c6bae-194">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.3/powershell-6.0.3-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="c6bae-195">解除安裝 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c6bae-195">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="c6bae-197">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="c6bae-197">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="c6bae-198">透過套件存放庫安裝 (慣用) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="c6bae-198">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="c6bae-199">PowerShell Core for Linux 會發佈到官方 Microsoft 存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="c6bae-199">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="c6bae-200">以超級使用者身分註冊過 Microsoft 存放庫一次之後，只需要使用 `sudo yum update powershell` 就可以更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="c6bae-200">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="c6bae-201">透過直接下載安裝 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="c6bae-201">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="c6bae-202">將 RPM 套件 `powershell-6.0.3-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="c6bae-202">Download the RPM package `powershell-6.0.3-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="c6bae-203">從[版本][]頁面下載到 Red Hat Enterprise Linux 電腦。</span><span class="sxs-lookup"><span data-stu-id="c6bae-203">from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="c6bae-204">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="c6bae-204">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.3-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="c6bae-205">您也可以不使用下載的中繼步驟來安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="c6bae-205">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.3/powershell-6.0.3-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="c6bae-206">解除安裝 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="c6bae-206">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-423"></a><span data-ttu-id="c6bae-207">OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="c6bae-207">OpenSUSE 42.3</span></span>

<span data-ttu-id="c6bae-208">安裝 PowerShell Core 時，`zypper` 可能會回報以下錯誤：</span><span class="sxs-lookup"><span data-stu-id="c6bae-208">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
 Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="c6bae-209">在此情況下，請確認下列命令會顯示 `libcurl` 套件為已安裝，來驗證存在符合規範的 `libcurl4` 程式庫：</span><span class="sxs-lookup"><span data-stu-id="c6bae-209">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="c6bae-210">然後在安裝 PowerShell 套件時，選擇 `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` 解決方案。</span><span class="sxs-lookup"><span data-stu-id="c6bae-210">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-423"></a><span data-ttu-id="c6bae-211">透過套件存放庫安裝 (慣用) - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="c6bae-211">Installation via Package Repository (preferred) - OpenSUSE 42.3</span></span>

<span data-ttu-id="c6bae-212">PowerShell Core for Linux 會發佈到官方 Microsoft 存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="c6bae-212">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Repository
zypper ar https://packages.microsoft.com/rhel/7/prod/

# Update the list of products
sudo zypper update

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-423"></a><span data-ttu-id="c6bae-213">透過直接下載安裝 - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="c6bae-213">Installation via Direct Download - OpenSUSE 42.3</span></span>

<span data-ttu-id="c6bae-214">將[版本][]頁面上的 RPM 套件 `powershell-6.0.3-1.rhel.7.x86_64.rpm` 下載到 OpenSUSE 電腦。</span><span class="sxs-lookup"><span data-stu-id="c6bae-214">Download the RPM package `powershell-6.0.3-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.3-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="c6bae-215">您也可以不使用下載的中繼步驟來安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="c6bae-215">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.3/powershell-6.0.3-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-423"></a><span data-ttu-id="c6bae-216">解除安裝 - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="c6bae-216">Uninstallation - OpenSUSE 42.3</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="c6bae-217">Fedora</span><span class="sxs-lookup"><span data-stu-id="c6bae-217">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="c6bae-218">只有 PowerShell Core 6.1 和更新版本才支援 Fedora 28。</span><span class="sxs-lookup"><span data-stu-id="c6bae-218">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="c6bae-219">透過套件存放庫安裝 (慣用) - Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="c6bae-219">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="c6bae-220">PowerShell Core for Linux 會發佈到官方 Microsoft 存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="c6bae-220">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="c6bae-221">透過直接下載安裝 - Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="c6bae-221">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="c6bae-222">將 RPM 套件 `powershell-6.0.3-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="c6bae-222">Download the RPM package `powershell-6.0.3-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="c6bae-223">從[版本][]頁面下載到 Fedora 電腦。</span><span class="sxs-lookup"><span data-stu-id="c6bae-223">from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="c6bae-224">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="c6bae-224">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.3-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="c6bae-225">您也可以不使用下載的中繼步驟來安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="c6bae-225">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="c6bae-226">解除安裝 - Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="c6bae-226">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="c6bae-227">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="c6bae-227">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="c6bae-228">Arch 支援為實驗性。</span><span class="sxs-lookup"><span data-stu-id="c6bae-228">Arch support is experimental.</span></span>

<span data-ttu-id="c6bae-229">PowerShell 可從 [Arch Linux][] 使用者存放庫 (AUR) 取得。</span><span class="sxs-lookup"><span data-stu-id="c6bae-229">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="c6bae-230">它可以使用[最新的標記版本][arch-release]編譯</span><span class="sxs-lookup"><span data-stu-id="c6bae-230">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="c6bae-231">它可以從[主機的最新認可][arch-git]編譯</span><span class="sxs-lookup"><span data-stu-id="c6bae-231">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="c6bae-232">它可以使用[最新版本的二進位檔][arch-bin]安裝</span><span class="sxs-lookup"><span data-stu-id="c6bae-232">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="c6bae-233">AUR 中的套件由社群維護 - 沒有官方支援。</span><span class="sxs-lookup"><span data-stu-id="c6bae-233">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="c6bae-234">如需從 AUR 安裝套件的詳細資訊，請參閱 [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) 或社群 [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile)。</span><span class="sxs-lookup"><span data-stu-id="c6bae-234">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="c6bae-236">Snap 套件</span><span class="sxs-lookup"><span data-stu-id="c6bae-236">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="c6bae-237">取得 snapd</span><span class="sxs-lookup"><span data-stu-id="c6bae-237">Getting snapd</span></span>

<span data-ttu-id="c6bae-238">必須有 `snapd` 才能執行 Snap。</span><span class="sxs-lookup"><span data-stu-id="c6bae-238">`snapd` is required to run snaps.</span></span>  <span data-ttu-id="c6bae-239">請使用[這些指示](https://docs.snapcraft.io/core/install)確認您已安裝 `snapd`。</span><span class="sxs-lookup"><span data-stu-id="c6bae-239">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="c6bae-240">透過 Snap 安裝</span><span class="sxs-lookup"><span data-stu-id="c6bae-240">Installation via Snap</span></span>

<span data-ttu-id="c6bae-241">適用於 Linux 的 PowerShell Core 會發佈到 [Snap 市集](https://snapcraft.io/store)以供輕鬆安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="c6bae-241">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="c6bae-242">這是慣用方法。</span><span class="sxs-lookup"><span data-stu-id="c6bae-242">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="c6bae-243">在安裝之後，Snap 會自動升級，不過您也可使用 `sudo snap refresh powershell-preview` 觸發升級。</span><span class="sxs-lookup"><span data-stu-id="c6bae-243">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="c6bae-244">解除安裝</span><span class="sxs-lookup"><span data-stu-id="c6bae-244">Uninstallation</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="linux-appimage"></a><span data-ttu-id="c6bae-245">Linux AppImage</span><span class="sxs-lookup"><span data-stu-id="c6bae-245">Linux AppImage</span></span>

> [!NOTE]
> <span data-ttu-id="c6bae-246">AppImage 支援為實驗性</span><span class="sxs-lookup"><span data-stu-id="c6bae-246">AppImage support is experimental</span></span>

<span data-ttu-id="c6bae-247">使用最新的 Linux 發行版本，將[版本][]頁面上的 AppImage `powershell-6.0.1-x86_64.AppImage` 下載到 Linux 電腦。</span><span class="sxs-lookup"><span data-stu-id="c6bae-247">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="c6bae-248">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="c6bae-248">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="c6bae-249">[AppImage][] 讓您不用安裝就可執行 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="c6bae-249">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="c6bae-250">它是將 PowerShell 及其相依性 (包括.NET Core 系統相依性) 組合成一個緊密套件的可攜式應用程式。</span><span class="sxs-lookup"><span data-stu-id="c6bae-250">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="c6bae-251">此套件是單一的二進位檔，可不受使用者的 Linux 發行版本影響而運作。</span><span class="sxs-lookup"><span data-stu-id="c6bae-251">This package is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="c6bae-253">Kali</span><span class="sxs-lookup"><span data-stu-id="c6bae-253">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="c6bae-254">Kali 支援為實驗性。</span><span class="sxs-lookup"><span data-stu-id="c6bae-254">Kali support is experimental.</span></span>

### <a name="installation"></a><span data-ttu-id="c6bae-255">安裝</span><span class="sxs-lookup"><span data-stu-id="c6bae-255">Installation</span></span>

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Install PowerShell
sudo dpkg -i powershell_6.0.3-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="c6bae-256">在最新的 Kali (Kali GNU/Linux Rolling) 中不用安裝即可執行 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c6bae-256">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="c6bae-257">解除安裝 - Kali</span><span class="sxs-lookup"><span data-stu-id="c6bae-257">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="c6bae-258">Raspbian</span><span class="sxs-lookup"><span data-stu-id="c6bae-258">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="c6bae-259">Raspbian 支援為實驗性。</span><span class="sxs-lookup"><span data-stu-id="c6bae-259">Raspbian support is experimental.</span></span>

<span data-ttu-id="c6bae-260">目前只有 Raspbian Stretch 支援 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="c6bae-260">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="c6bae-261">另外，CoreCLR (和 PowerShell Core) 僅適用於 Pi 2 和 Pi 3 裝置，因為像 [Pi Zero](https://github.com/dotnet/coreclr/issues/10605) 此類的其他裝置，它們的處理器不被支援。</span><span class="sxs-lookup"><span data-stu-id="c6bae-261">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="c6bae-262">下載 [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/)並 遵循[安裝指示](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)來把它安裝到您的 Pi。</span><span class="sxs-lookup"><span data-stu-id="c6bae-262">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="c6bae-263">安裝</span><span class="sxs-lookup"><span data-stu-id="c6bae-263">Installation</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.3/powershell-6.0.3-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.3-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="c6bae-264">或者，您可以建立一個符號連結，無需指定 "pwsh" 二進位路徑，便能啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="c6bae-264">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="c6bae-265">解除安裝 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="c6bae-265">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="c6bae-266">二進位封存</span><span class="sxs-lookup"><span data-stu-id="c6bae-266">Binary Archives</span></span>

<span data-ttu-id="c6bae-267">Linux 平台有 PowerShell 二進位 `tar.gz` 封存，以啟用進階的部署案例。</span><span class="sxs-lookup"><span data-stu-id="c6bae-267">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="c6bae-268">相依性</span><span class="sxs-lookup"><span data-stu-id="c6bae-268">Dependencies</span></span>

<span data-ttu-id="c6bae-269">PowerShell 會為所有 Linux 發行版本建置可攜式二進位檔。</span><span class="sxs-lookup"><span data-stu-id="c6bae-269">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="c6bae-270">但 .NET Core 執行階段在不同的發行版本需要不同的相依性，所以 PowerShell 也一樣。</span><span class="sxs-lookup"><span data-stu-id="c6bae-270">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="c6bae-271">下圖顯示不同 Linux 發行版本上，正式支援的 .NET Core 2.0 相依性。</span><span class="sxs-lookup"><span data-stu-id="c6bae-271">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="c6bae-272">作業系統</span><span class="sxs-lookup"><span data-stu-id="c6bae-272">OS</span></span>                 | <span data-ttu-id="c6bae-273">相依性</span><span class="sxs-lookup"><span data-stu-id="c6bae-273">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="c6bae-274">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="c6bae-274">Ubuntu 14.04</span></span>       | <span data-ttu-id="c6bae-275">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="c6bae-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c6bae-276">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52</span><span class="sxs-lookup"><span data-stu-id="c6bae-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="c6bae-277">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="c6bae-277">Ubuntu 16.04</span></span>       | <span data-ttu-id="c6bae-278">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="c6bae-278">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c6bae-279">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu55</span><span class="sxs-lookup"><span data-stu-id="c6bae-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="c6bae-280">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="c6bae-280">Ubuntu 17.10</span></span>       | <span data-ttu-id="c6bae-281">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="c6bae-281">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c6bae-282">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu57</span><span class="sxs-lookup"><span data-stu-id="c6bae-282">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="c6bae-283">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="c6bae-283">Ubuntu 18.04</span></span>       | <span data-ttu-id="c6bae-284">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="c6bae-284">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c6bae-285">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu60</span><span class="sxs-lookup"><span data-stu-id="c6bae-285">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="c6bae-286">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="c6bae-286">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="c6bae-287">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="c6bae-287">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c6bae-288">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52</span><span class="sxs-lookup"><span data-stu-id="c6bae-288">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="c6bae-289">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="c6bae-289">Debian 9 (Stretch)</span></span> | <span data-ttu-id="c6bae-290">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="c6bae-290">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c6bae-291">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.2、libicu57</span><span class="sxs-lookup"><span data-stu-id="c6bae-291">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="c6bae-292">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c6bae-292">CentOS 7</span></span> <br> <span data-ttu-id="c6bae-293">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="c6bae-293">Oracle Linux 7</span></span> <br> <span data-ttu-id="c6bae-294">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="c6bae-294">RHEL 7</span></span> <br> <span data-ttu-id="c6bae-295">OpenSUSE OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="c6bae-295">OpenSUSE OpenSUSE 42.3</span></span> | <span data-ttu-id="c6bae-296">libunwind、libcurl、openssl-libs、libicu</span><span class="sxs-lookup"><span data-stu-id="c6bae-296">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="c6bae-297">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="c6bae-297">Fedora 27</span></span> <br> <span data-ttu-id="c6bae-298">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="c6bae-298">Fedora 28</span></span> | <span data-ttu-id="c6bae-299">libunwind、libcurl、openssl-libs、libicu、compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="c6bae-299">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="c6bae-300">若要在未正式支援的 Linux 發行版本上部署 PowerShell 二進位檔，您需要在個別步驟中為目標作業系統安裝必要的相依性。</span><span class="sxs-lookup"><span data-stu-id="c6bae-300">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="c6bae-301">例如，[Amazon Linux dockerfile][amazon-dockerfile] 會先安裝相依性，再解壓縮 Linux `tar.gz` 封存。</span><span class="sxs-lookup"><span data-stu-id="c6bae-301">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="c6bae-302">安裝 - 二進位封存</span><span class="sxs-lookup"><span data-stu-id="c6bae-302">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="c6bae-303">Linux</span><span class="sxs-lookup"><span data-stu-id="c6bae-303">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.2/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="c6bae-304">解除安裝二進位封存</span><span class="sxs-lookup"><span data-stu-id="c6bae-304">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="c6bae-305">路徑</span><span class="sxs-lookup"><span data-stu-id="c6bae-305">Paths</span></span>

* <span data-ttu-id="c6bae-306">`$PSHOME` 是 `/opt/microsoft/powershell/6.0.3/`</span><span class="sxs-lookup"><span data-stu-id="c6bae-306">`$PSHOME` is `/opt/microsoft/powershell/6.0.3/`</span></span>
* <span data-ttu-id="c6bae-307">會從 `~/.config/powershell/profile.ps1` 讀取使用者設定檔</span><span class="sxs-lookup"><span data-stu-id="c6bae-307">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="c6bae-308">會從 `$PSHOME/profile.ps1` 讀取預設設定檔</span><span class="sxs-lookup"><span data-stu-id="c6bae-308">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="c6bae-309">會從 `~/.local/share/powershell/Modules` 讀取使用者模組</span><span class="sxs-lookup"><span data-stu-id="c6bae-309">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="c6bae-310">會從 `/usr/local/share/powershell/Modules` 讀取共用的模組</span><span class="sxs-lookup"><span data-stu-id="c6bae-310">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="c6bae-311">會從 `$PSHOME/Modules` 讀取預設模組</span><span class="sxs-lookup"><span data-stu-id="c6bae-311">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="c6bae-312">PSReadline 記錄會記錄在 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="c6bae-312">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="c6bae-313">設定檔會遵循 PowerShell 的每個主控件設定，讓預設主控件特定設定檔存在於相同位置的 `Microsoft.PowerShell_profile.ps1`。</span><span class="sxs-lookup"><span data-stu-id="c6bae-313">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="c6bae-314">PowerShell 遵循 Linux 上的 [XDG 基底目錄規格][xdg-bds]。</span><span class="sxs-lookup"><span data-stu-id="c6bae-314">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[版本]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
