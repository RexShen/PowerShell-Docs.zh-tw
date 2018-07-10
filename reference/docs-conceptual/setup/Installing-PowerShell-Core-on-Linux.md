# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="e9259-101">在 Linux 上安裝 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="e9259-101">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="e9259-102">支援 [Ubuntu 14.04][u14]、[Ubuntu 16.04][u16]、[Ubuntu 17.10][u17]、[Debian 8][deb8]、[Debian 9][deb9]、[CentOS 7][cos]、[Red Hat Enterprise Linux (RHEL) 7][rhel7]、[OpenSUSE 42.2][opensuse]、[Fedora 27][fedora]、[Fedora 28][fedora] 與 [Arch Linux][arch]。</span><span class="sxs-lookup"><span data-stu-id="e9259-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="e9259-103">針對未正式支援的 Linux 發行版本，您可以嘗試使用 [PowerShell AppImage][lai]。</span><span class="sxs-lookup"><span data-stu-id="e9259-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="e9259-104">您也可以直接使用 Linux [`tar.gz` 封存][tar]嘗試部署 PowerShell 二進位檔，但您需要根據個別步驟中的作業系統，設定必要的相依性。</span><span class="sxs-lookup"><span data-stu-id="e9259-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="e9259-105">GitHub [版本][]頁面上提供所有套件。</span><span class="sxs-lookup"><span data-stu-id="e9259-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="e9259-106">安裝套件之後，請從終端機執行 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="e9259-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1710
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fedora]: #fedora
[arch]: #arch-linux
[lai]: #linux-appimage
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="e9259-107">安裝預覽版本</span><span class="sxs-lookup"><span data-stu-id="e9259-107">Installing Preview Releases</span></span>

<span data-ttu-id="e9259-108">透過套件存放庫安裝 Linux 的 PowerShell Core Preview 版本時，套件名稱會從 `powershell` 變更為 `powershell-preview`。</span><span class="sxs-lookup"><span data-stu-id="e9259-108">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="e9259-109">透過直接下載的安裝不會變更，但檔案名稱除外。</span><span class="sxs-lookup"><span data-stu-id="e9259-109">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="e9259-110">下表是使用各種套件管理員安裝穩定和預覽套件的命令：</span><span class="sxs-lookup"><span data-stu-id="e9259-110">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="e9259-111">散發</span><span class="sxs-lookup"><span data-stu-id="e9259-111">Distrobution(s)</span></span>|<span data-ttu-id="e9259-112">穩定命令</span><span class="sxs-lookup"><span data-stu-id="e9259-112">Stable Command</span></span> | <span data-ttu-id="e9259-113">預覽命令</span><span class="sxs-lookup"><span data-stu-id="e9259-113">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="e9259-114">Ubuntu、Debian</span><span class="sxs-lookup"><span data-stu-id="e9259-114">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="e9259-115">CentOS、RedHat</span><span class="sxs-lookup"><span data-stu-id="e9259-115">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="e9259-116">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="e9259-116">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="e9259-117">Fedora</span><span class="sxs-lookup"><span data-stu-id="e9259-117">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="e9259-118">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e9259-118">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="e9259-119">透過套件存放庫安裝 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e9259-119">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="e9259-120">PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="e9259-120">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e9259-121">這是慣用方法。</span><span class="sxs-lookup"><span data-stu-id="e9259-121">This is the preferred method.</span></span>

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

<span data-ttu-id="e9259-122">以超級使用者的身分，註冊 Microsoft 存放庫。</span><span class="sxs-lookup"><span data-stu-id="e9259-122">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="e9259-123">從那時起，您只需要使用`sudo apt-get upgrade powershell`來更新安裝。</span><span class="sxs-lookup"><span data-stu-id="e9259-123">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="e9259-124">透過直接下載安裝 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e9259-124">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="e9259-125">將[版本][]頁面上的 Debian 套件 `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` 下載至 Ubuntu 電腦。</span><span class="sxs-lookup"><span data-stu-id="e9259-125">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e9259-126">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="e9259-126">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e9259-127">`dpkg -i` 命令因相依性不相符而失敗。</span><span class="sxs-lookup"><span data-stu-id="e9259-127">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="e9259-128">下一個命令 `apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。</span><span class="sxs-lookup"><span data-stu-id="e9259-128">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="e9259-129">解除安裝 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e9259-129">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="e9259-130">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e9259-130">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="e9259-131">透過套件存放庫安裝 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e9259-131">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="e9259-132">PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="e9259-132">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e9259-133">這是慣用方法。</span><span class="sxs-lookup"><span data-stu-id="e9259-133">This is the preferred method.</span></span>

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

<span data-ttu-id="e9259-134">以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。</span><span class="sxs-lookup"><span data-stu-id="e9259-134">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="e9259-135">透過直接下載安裝 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e9259-135">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="e9259-136">將[版本][]頁面上的 Debian 套件 `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` 下載至 Ubuntu 電腦。</span><span class="sxs-lookup"><span data-stu-id="e9259-136">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e9259-137">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="e9259-137">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e9259-138">`dpkg -i` 命令因相依性不相符而失敗。</span><span class="sxs-lookup"><span data-stu-id="e9259-138">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="e9259-139">下一個命令 `apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。</span><span class="sxs-lookup"><span data-stu-id="e9259-139">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="e9259-140">解除安裝 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e9259-140">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1710"></a><span data-ttu-id="e9259-141">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="e9259-141">Ubuntu 17.10</span></span>

> [!NOTE]
> <span data-ttu-id="e9259-142">在 `6.1.0-preview.2` 之後已新增 Ubuntu 17.04 支援</span><span class="sxs-lookup"><span data-stu-id="e9259-142">Support for Ubuntu 17.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1710"></a><span data-ttu-id="e9259-143">透過套件存放庫安裝 - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="e9259-143">Installation via Package Repository - Ubuntu 17.10</span></span>

<span data-ttu-id="e9259-144">PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="e9259-144">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e9259-145">這是慣用方法。</span><span class="sxs-lookup"><span data-stu-id="e9259-145">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/17.10/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e9259-146">以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。</span><span class="sxs-lookup"><span data-stu-id="e9259-146">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1710"></a><span data-ttu-id="e9259-147">透過直接下載安裝 - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="e9259-147">Installation via Direct Download - Ubuntu 17.10</span></span>

<span data-ttu-id="e9259-148">將[版本][]頁面上的 Debian 套件 `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` 下載至 Ubuntu 電腦。</span><span class="sxs-lookup"><span data-stu-id="e9259-148">Download the Debian package `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e9259-149">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="e9259-149">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.10_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e9259-150">`dpkg -i` 命令因相依性不相符而失敗。</span><span class="sxs-lookup"><span data-stu-id="e9259-150">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="e9259-151">下一個命令 `apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。</span><span class="sxs-lookup"><span data-stu-id="e9259-151">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1710"></a><span data-ttu-id="e9259-152">解除安裝 - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="e9259-152">Uninstallation - Ubuntu 17.10</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="e9259-153">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e9259-153">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="e9259-154">在 `6.1.0-preview.2` 之後已新增 Ubuntu 18.04 支援</span><span class="sxs-lookup"><span data-stu-id="e9259-154">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="e9259-155">透過套件存放庫安裝 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e9259-155">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="e9259-156">PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="e9259-156">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e9259-157">這是慣用方法。</span><span class="sxs-lookup"><span data-stu-id="e9259-157">This is the preferred method.</span></span>

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
pwsh
```

<span data-ttu-id="e9259-158">以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。</span><span class="sxs-lookup"><span data-stu-id="e9259-158">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="e9259-159">透過直接下載安裝 - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e9259-159">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="e9259-160">將[版本][]頁面上的 Debian 套件 `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` 下載至 Ubuntu 電腦。</span><span class="sxs-lookup"><span data-stu-id="e9259-160">Download the Debian package `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e9259-161">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="e9259-161">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e9259-162">`dpkg -i` 命令因相依性不相符而失敗。</span><span class="sxs-lookup"><span data-stu-id="e9259-162">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="e9259-163">下一個命令 `apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。</span><span class="sxs-lookup"><span data-stu-id="e9259-163">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1710"></a><span data-ttu-id="e9259-164">解除安裝 - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="e9259-164">Uninstallation - Ubuntu 17.10</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="e9259-165">Debian 8</span><span class="sxs-lookup"><span data-stu-id="e9259-165">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="e9259-166">透過套件存放庫安裝 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="e9259-166">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="e9259-167">PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="e9259-167">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e9259-168">這是慣用方法。</span><span class="sxs-lookup"><span data-stu-id="e9259-168">This is the preferred method.</span></span>

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

<span data-ttu-id="e9259-169">以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。</span><span class="sxs-lookup"><span data-stu-id="e9259-169">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="e9259-170">透過直接下載安裝 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="e9259-170">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="e9259-171">將[版本][]頁面上的 Debian 套件 `powershell_6.0.2-1.debian.8_amd64.deb` 下載至 Debian 電腦。</span><span class="sxs-lookup"><span data-stu-id="e9259-171">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="e9259-172">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="e9259-172">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e9259-173">`dpkg -i` 命令因相依性不相符而失敗。</span><span class="sxs-lookup"><span data-stu-id="e9259-173">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="e9259-174">下一個命令 `apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。</span><span class="sxs-lookup"><span data-stu-id="e9259-174">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="e9259-175">解除安裝 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="e9259-175">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="e9259-176">Debian 9</span><span class="sxs-lookup"><span data-stu-id="e9259-176">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="e9259-177">透過套件存放庫安裝 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="e9259-177">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="e9259-178">PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="e9259-178">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e9259-179">這是慣用方法。</span><span class="sxs-lookup"><span data-stu-id="e9259-179">This is the preferred method.</span></span>

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

<span data-ttu-id="e9259-180">以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。</span><span class="sxs-lookup"><span data-stu-id="e9259-180">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="e9259-181">透過直接下載安裝 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="e9259-181">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="e9259-182">將[版本][]頁面上的 Debian 套件 `powershell_6.0.2-1.debian.9_amd64.deb` 下載至 Debian 電腦。</span><span class="sxs-lookup"><span data-stu-id="e9259-182">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="e9259-183">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="e9259-183">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="e9259-184">解除安裝 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="e9259-184">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="e9259-185">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e9259-185">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="e9259-186">此套件也適用於 Oracle Linux 7。</span><span class="sxs-lookup"><span data-stu-id="e9259-186">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="e9259-187">透過套件存放庫安裝 (慣用) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e9259-187">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="e9259-188">PowerShell Core for Linux 會發佈到官方 Microsoft 存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="e9259-188">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e9259-189">以超級使用者身分註冊過 Microsoft 存放庫一次之後，只需要使用 `sudo yum update powershell` 就可以更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="e9259-189">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="e9259-190">透過直接下載安裝 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e9259-190">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="e9259-191">使用 [CentOS 7][]，將[版本][]頁面上的 RPM 套件 `powershell-6.0.2-1.rhel.7.x86_64.rpm` 下載至 CentOS 電腦。</span><span class="sxs-lookup"><span data-stu-id="e9259-191">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="e9259-192">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="e9259-192">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e9259-193">您也可以不使用下載的中繼步驟來安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="e9259-193">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="e9259-194">解除安裝 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e9259-194">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e9259-196">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e9259-196">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e9259-197">透過套件存放庫安裝 (慣用) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e9259-197">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="e9259-198">PowerShell Core for Linux 會發佈到官方 Microsoft 存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="e9259-198">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e9259-199">以超級使用者身分註冊過 Microsoft 存放庫一次之後，只需要使用 `sudo yum update powershell` 就可以更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="e9259-199">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e9259-200">透過直接下載安裝 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e9259-200">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="e9259-201">將[版本][]頁面上的 RPM 套件 `powershell-6.0.2-1.rhel.7.x86_64.rpm` 下載到 Red Hat Enterprise Linux 電腦。</span><span class="sxs-lookup"><span data-stu-id="e9259-201">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="e9259-202">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="e9259-202">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e9259-203">您也可以不使用下載的中繼步驟來安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="e9259-203">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e9259-204">解除安裝 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e9259-204">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="e9259-205">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="e9259-205">OpenSUSE 42.2</span></span>

<span data-ttu-id="e9259-206">安裝 PowerShell Core 時，`zypper` 可能會回報以下錯誤：</span><span class="sxs-lookup"><span data-stu-id="e9259-206">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
 Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="e9259-207">在此情況下，請確認下列命令會顯示 `libcurl` 套件為已安裝，來驗證存在符合規範的 `libcurl4` 程式庫：</span><span class="sxs-lookup"><span data-stu-id="e9259-207">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="e9259-208">然後在安裝 PowerShell 套件時，選擇 `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` 解決方案。</span><span class="sxs-lookup"><span data-stu-id="e9259-208">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="e9259-209">透過套件存放庫安裝 (慣用) - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="e9259-209">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="e9259-210">PowerShell Core for Linux 會發佈到官方 Microsoft 存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="e9259-210">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Product feed
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/zypp/repos.d/microsoft.repo

# Update the list of products
sudo zypper update

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="e9259-211">透過直接下載安裝 - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="e9259-211">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="e9259-212">將[版本][]頁面上的 RPM 套件 `powershell-6.0.2-1.rhel.7.x86_64.rpm` 下載到 OpenSUSE 電腦。</span><span class="sxs-lookup"><span data-stu-id="e9259-212">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e9259-213">您也可以不使用下載的中繼步驟來安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="e9259-213">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="e9259-214">解除安裝 - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="e9259-214">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="e9259-215">Fedora</span><span class="sxs-lookup"><span data-stu-id="e9259-215">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="e9259-216">只有 PowerShell Core 6.1 和更新版本才支援 Fedora 28。</span><span class="sxs-lookup"><span data-stu-id="e9259-216">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="e9259-217">透過套件存放庫安裝 (慣用) - Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e9259-217">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="e9259-218">PowerShell Core for Linux 會發佈到官方 Microsoft 存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="e9259-218">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="e9259-219">透過直接下載安裝 - Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e9259-219">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="e9259-220">將[版本][]頁面上的 RPM 套件 `powershell-6.0.2-1.rhel.7.x86_64.rpm` 下載到 Fedora 電腦。</span><span class="sxs-lookup"><span data-stu-id="e9259-220">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="e9259-221">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="e9259-221">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e9259-222">您也可以不使用下載的中繼步驟來安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="e9259-222">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="e9259-223">解除安裝 - Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e9259-223">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="e9259-224">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="e9259-224">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="e9259-225">Arch 支援為實驗性。</span><span class="sxs-lookup"><span data-stu-id="e9259-225">Arch support is experimental.</span></span>

<span data-ttu-id="e9259-226">PowerShell 可從 [Arch Linux][] 使用者存放庫 (AUR) 取得。</span><span class="sxs-lookup"><span data-stu-id="e9259-226">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="e9259-227">它可以使用[最新的標記版本][arch-release]編譯</span><span class="sxs-lookup"><span data-stu-id="e9259-227">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="e9259-228">它可以從[主機的最新認可][arch-git]編譯</span><span class="sxs-lookup"><span data-stu-id="e9259-228">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="e9259-229">它可以使用[最新版本的二進位檔][arch-bin]安裝</span><span class="sxs-lookup"><span data-stu-id="e9259-229">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="e9259-230">AUR 中的套件由社群維護 - 沒有官方支援。</span><span class="sxs-lookup"><span data-stu-id="e9259-230">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="e9259-231">如需從 AUR 安裝套件的詳細資訊，請參閱 [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) 或社群 [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile)。</span><span class="sxs-lookup"><span data-stu-id="e9259-231">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="e9259-233">Linux AppImage</span><span class="sxs-lookup"><span data-stu-id="e9259-233">Linux AppImage</span></span>

> [!NOTE]
> <span data-ttu-id="e9259-234">AppImage 支援為實驗性</span><span class="sxs-lookup"><span data-stu-id="e9259-234">AppImage support is experimental</span></span>

<span data-ttu-id="e9259-235">使用最新的 Linux 發行版本，將[版本][]頁面上的 AppImage `powershell-6.0.1-x86_64.AppImage` 下載到 Linux 電腦。</span><span class="sxs-lookup"><span data-stu-id="e9259-235">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="e9259-236">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="e9259-236">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="e9259-237">[AppImage][] 讓您不用安裝就可執行 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="e9259-237">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="e9259-238">它是將 PowerShell 及其相依性 (包括.NET Core 系統相依性) 組合成一個緊密套件的可攜式應用程式。</span><span class="sxs-lookup"><span data-stu-id="e9259-238">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="e9259-239">此套件的運作不受使用者的 Linux 發行版本影響，且是單一的二進位檔。</span><span class="sxs-lookup"><span data-stu-id="e9259-239">This package  is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="e9259-241">Kali</span><span class="sxs-lookup"><span data-stu-id="e9259-241">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="e9259-242">Kali 支援為實驗性。</span><span class="sxs-lookup"><span data-stu-id="e9259-242">Kali support is experimental.</span></span>

### <a name="installation"></a><span data-ttu-id="e9259-243">安裝</span><span class="sxs-lookup"><span data-stu-id="e9259-243">Installation</span></span>

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Install PowerShell
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="e9259-244">在最新的 Kali (Kali GNU/Linux Rolling) 中不用安裝即可執行 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e9259-244">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="e9259-245">解除安裝 - Kali</span><span class="sxs-lookup"><span data-stu-id="e9259-245">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="e9259-246">Raspbian</span><span class="sxs-lookup"><span data-stu-id="e9259-246">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="e9259-247">Raspbian 支援為實驗性。</span><span class="sxs-lookup"><span data-stu-id="e9259-247">Raspbian support is experimental.</span></span>

<span data-ttu-id="e9259-248">目前只有 Raspbian Stretch 支援 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="e9259-248">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="e9259-249">另外，CoreCLR (和 PowerShell Core) 僅適用於 Pi 2 和 Pi 3 裝置，因為像 [Pi Zero](https://github.com/dotnet/coreclr/issues/10605) 此類的其他裝置，它們的處理器不被支援。</span><span class="sxs-lookup"><span data-stu-id="e9259-249">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="e9259-250">下載 [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/)並 遵循[安裝指示](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)來把它安裝到您的 Pi。</span><span class="sxs-lookup"><span data-stu-id="e9259-250">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="e9259-251">安裝</span><span class="sxs-lookup"><span data-stu-id="e9259-251">Installation</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.2-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="e9259-252">或者，您可以建立一個符號連結，無需指定 "pwsh" 二進位路徑，便能啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="e9259-252">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="e9259-253">解除安裝 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="e9259-253">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="e9259-254">二進位封存</span><span class="sxs-lookup"><span data-stu-id="e9259-254">Binary Archives</span></span>

<span data-ttu-id="e9259-255">Linux 平台有 PowerShell 二進位 `tar.gz` 封存，以啟用進階的部署案例。</span><span class="sxs-lookup"><span data-stu-id="e9259-255">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="e9259-256">相依性</span><span class="sxs-lookup"><span data-stu-id="e9259-256">Dependencies</span></span>

<span data-ttu-id="e9259-257">PowerShell 會為所有 Linux 發行版本建置可攜式二進位檔。</span><span class="sxs-lookup"><span data-stu-id="e9259-257">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="e9259-258">但 .NET Core 執行階段在不同的發行版本需要不同的相依性，所以 PowerShell 也一樣。</span><span class="sxs-lookup"><span data-stu-id="e9259-258">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="e9259-259">下圖顯示不同 Linux 發行版本上，正式支援的 .NET Core 2.0 相依性。</span><span class="sxs-lookup"><span data-stu-id="e9259-259">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="e9259-260">作業系統</span><span class="sxs-lookup"><span data-stu-id="e9259-260">OS</span></span>                 | <span data-ttu-id="e9259-261">相依性</span><span class="sxs-lookup"><span data-stu-id="e9259-261">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="e9259-262">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e9259-262">Ubuntu 14.04</span></span>       | <span data-ttu-id="e9259-263">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="e9259-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e9259-264">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52</span><span class="sxs-lookup"><span data-stu-id="e9259-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="e9259-265">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e9259-265">Ubuntu 16.04</span></span>       | <span data-ttu-id="e9259-266">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="e9259-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e9259-267">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu55</span><span class="sxs-lookup"><span data-stu-id="e9259-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="e9259-268">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="e9259-268">Ubuntu 17.10</span></span>       | <span data-ttu-id="e9259-269">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="e9259-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e9259-270">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu57</span><span class="sxs-lookup"><span data-stu-id="e9259-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="e9259-271">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e9259-271">Ubuntu 18.04</span></span>       | <span data-ttu-id="e9259-272">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="e9259-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e9259-273">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu60</span><span class="sxs-lookup"><span data-stu-id="e9259-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="e9259-274">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="e9259-274">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="e9259-275">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="e9259-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e9259-276">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52</span><span class="sxs-lookup"><span data-stu-id="e9259-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="e9259-277">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="e9259-277">Debian 9 (Stretch)</span></span> | <span data-ttu-id="e9259-278">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="e9259-278">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e9259-279">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.2、libicu57</span><span class="sxs-lookup"><span data-stu-id="e9259-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="e9259-280">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e9259-280">CentOS 7</span></span> <br> <span data-ttu-id="e9259-281">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="e9259-281">Oracle Linux 7</span></span> <br> <span data-ttu-id="e9259-282">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="e9259-282">RHEL 7</span></span> <br> <span data-ttu-id="e9259-283">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="e9259-283">OpenSUSE 42.2</span></span> | <span data-ttu-id="e9259-284">libunwind、libcurl、openssl-libs、libicu</span><span class="sxs-lookup"><span data-stu-id="e9259-284">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="e9259-285">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="e9259-285">Fedora 27</span></span> <br> <span data-ttu-id="e9259-286">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e9259-286">Fedora 28</span></span> | <span data-ttu-id="e9259-287">libunwind、libcurl、openssl-libs、libicu、compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="e9259-287">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="e9259-288">若要在未正式支援的 Linux 發行版本上部署 PowerShell 二進位檔，您需要在個別步驟中為目標作業系統安裝必要的相依性。</span><span class="sxs-lookup"><span data-stu-id="e9259-288">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="e9259-289">例如，[Amazon Linux dockerfile][amazon-dockerfile] 會先安裝相依性，再解壓縮 Linux `tar.gz` 封存。</span><span class="sxs-lookup"><span data-stu-id="e9259-289">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="e9259-290">安裝 - 二進位封存</span><span class="sxs-lookup"><span data-stu-id="e9259-290">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="e9259-291">Linux</span><span class="sxs-lookup"><span data-stu-id="e9259-291">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="e9259-292">解除安裝二進位封存</span><span class="sxs-lookup"><span data-stu-id="e9259-292">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="e9259-293">路徑</span><span class="sxs-lookup"><span data-stu-id="e9259-293">Paths</span></span>

* <span data-ttu-id="e9259-294">`$PSHOME` 是 `/opt/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="e9259-294">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="e9259-295">會從 `~/.config/powershell/profile.ps1` 讀取使用者設定檔</span><span class="sxs-lookup"><span data-stu-id="e9259-295">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="e9259-296">會從 `$PSHOME/profile.ps1` 讀取預設設定檔</span><span class="sxs-lookup"><span data-stu-id="e9259-296">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="e9259-297">會從 `~/.local/share/powershell/Modules` 讀取使用者模組</span><span class="sxs-lookup"><span data-stu-id="e9259-297">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="e9259-298">會從 `/usr/local/share/powershell/Modules` 讀取共用的模組</span><span class="sxs-lookup"><span data-stu-id="e9259-298">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="e9259-299">會從 `$PSHOME/Modules` 讀取預設模組</span><span class="sxs-lookup"><span data-stu-id="e9259-299">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="e9259-300">PSReadline 記錄會記錄在 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="e9259-300">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="e9259-301">設定檔會遵循 PowerShell 的每個主控件設定，讓預設主控件特定設定檔存在於相同位置的 `Microsoft.PowerShell_profile.ps1`。</span><span class="sxs-lookup"><span data-stu-id="e9259-301">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="e9259-302">PowerShell 遵循 Linux 上的 [XDG 基底目錄規格][xdg-bds]。</span><span class="sxs-lookup"><span data-stu-id="e9259-302">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[版本]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
