# <a name="installing-powershell-core-on-macos-and-linux"></a><span data-ttu-id="97a92-101">在 macOS 與 Linux 上安裝 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="97a92-101">Installing PowerShell Core on macOS and Linux</span></span>

<span data-ttu-id="97a92-102">支援 [Ubuntu 14.04][u14]、[Ubuntu 16.04][u16]、[Ubuntu 17.04][u17]、[Debian 8][deb8]、[Debian 9][deb9]、[CentOS 7][cos]、[Red Hat Enterprise Linux (RHEL) 7][rhel7]、[OpenSUSE 42.2][opensuse]、[Fedora 25][fed25]、[Fedora 26][fed26]、[Arch Linux][arch] 和 [macOS 10.12][mac]。</span><span class="sxs-lookup"><span data-stu-id="97a92-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25][fed25], [Fedora 26][fed26], [Arch Linux][arch], and [macOS 10.12][mac].</span></span>

<span data-ttu-id="97a92-103">針對未正式支援的 Linux 發行版本，您可以嘗試使用 [PowerShell AppImage][lai]。</span><span class="sxs-lookup"><span data-stu-id="97a92-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span> <span data-ttu-id="97a92-104">您也可以直接使用 Linux [`tar.gz` 封存][tar]嘗試部署 PowerShell 二進位檔，但您需要根據個別步驟中的作業系統，設定必要的相依性。</span><span class="sxs-lookup"><span data-stu-id="97a92-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="97a92-105">GitHub [版本][]頁面上提供所有套件。</span><span class="sxs-lookup"><span data-stu-id="97a92-105">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="97a92-106">安裝套件之後，請從終端機執行 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="97a92-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1704
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fed25]: #fedora-25
[fed26]: #fedora-26
[arch]: #arch-linux
[lai]: #linux-appimage
[mac]: #macos-1012
[tar]: #binary-archives

## <a name="ubuntu-1404"></a><span data-ttu-id="97a92-107">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="97a92-107">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="97a92-108">透過套件存放庫安裝 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="97a92-108">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="97a92-109">PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="97a92-109">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span> <span data-ttu-id="97a92-110">這是慣用方法。</span><span class="sxs-lookup"><span data-stu-id="97a92-110">This is the preferred method.</span></span>

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

<span data-ttu-id="97a92-111">以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。</span><span class="sxs-lookup"><span data-stu-id="97a92-111">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="97a92-112">透過直接下載安裝 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="97a92-112">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="97a92-113">將[版本][]頁面上的 Debian 套件 `powershell_6.0.0-1.ubuntu.14.04_amd64.deb` 下載至 Ubuntu 電腦。</span><span class="sxs-lookup"><span data-stu-id="97a92-113">Download the Debian package `powershell_6.0.0-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.14.04_amd64.deb
```

<span data-ttu-id="97a92-114">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="97a92-114">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="97a92-115">請注意，`dpkg -i` 會因為不符合相依性而失敗；下一個命令 `apt-get install -f` 則會解決這些問題，然後完成 PowerShell 套件設定。</span><span class="sxs-lookup"><span data-stu-id="97a92-115">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="97a92-116">解除安裝 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="97a92-116">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="97a92-117">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="97a92-117">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="97a92-118">透過套件存放庫安裝 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="97a92-118">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="97a92-119">PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="97a92-119">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="97a92-120">這是慣用方法。</span><span class="sxs-lookup"><span data-stu-id="97a92-120">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="97a92-121">以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。</span><span class="sxs-lookup"><span data-stu-id="97a92-121">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="97a92-122">透過直接下載安裝 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="97a92-122">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="97a92-123">將[版本][]頁面上的 Debian 套件 `powershell_6.0.0-1.ubuntu.16.04_amd64.deb` 下載到 Ubuntu 電腦：</span><span class="sxs-lookup"><span data-stu-id="97a92-123">Download the Debian package `powershell_6.0.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.16.04_amd64.deb
```

<span data-ttu-id="97a92-124">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="97a92-124">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="97a92-125">請注意，`dpkg -i` 會因為不符合相依性而失敗；下一個命令 `apt-get install -f` 則會解決這些問題，然後完成 PowerShell 套件設定。</span><span class="sxs-lookup"><span data-stu-id="97a92-125">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="97a92-126">解除安裝 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="97a92-126">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a><span data-ttu-id="97a92-127">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="97a92-127">Ubuntu 17.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1704"></a><span data-ttu-id="97a92-128">透過套件存放庫安裝 - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="97a92-128">Installation via Package Repository - Ubuntu 17.04</span></span>

<span data-ttu-id="97a92-129">PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="97a92-129">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="97a92-130">這是慣用方法。</span><span class="sxs-lookup"><span data-stu-id="97a92-130">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/17.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="97a92-131">以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。</span><span class="sxs-lookup"><span data-stu-id="97a92-131">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1704"></a><span data-ttu-id="97a92-132">透過直接下載安裝 - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="97a92-132">Installation via Direct Download - Ubuntu 17.04</span></span>

<span data-ttu-id="97a92-133">將[版本][]頁面上的 Debian 套件 `powershell_6.0.0-1.ubuntu.17.04_amd64.deb` 下載到 Ubuntu 電腦：</span><span class="sxs-lookup"><span data-stu-id="97a92-133">Download the Debian package `powershell_6.0.0-1.ubuntu.17.04_amd64.deb` from the [releases][] page onto the Ubuntu machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.17.04_amd64.deb
```

<span data-ttu-id="97a92-134">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="97a92-134">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="97a92-135">請注意，`dpkg -i` 會因為不符合相依性而失敗；下一個命令 `apt-get install -f` 則會解決這些問題，然後完成 PowerShell 套件設定。</span><span class="sxs-lookup"><span data-stu-id="97a92-135">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1704"></a><span data-ttu-id="97a92-136">解除安裝 - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="97a92-136">Uninstallation - Ubuntu 17.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="97a92-137">Debian 8</span><span class="sxs-lookup"><span data-stu-id="97a92-137">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="97a92-138">透過套件存放庫安裝 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="97a92-138">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="97a92-139">PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="97a92-139">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="97a92-140">這是慣用方法。</span><span class="sxs-lookup"><span data-stu-id="97a92-140">This is the preferred method.</span></span>

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

<span data-ttu-id="97a92-141">以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。</span><span class="sxs-lookup"><span data-stu-id="97a92-141">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="97a92-142">透過直接下載安裝 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="97a92-142">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="97a92-143">將[版本][]頁面上的 Debian 套件 `powershell_6.0.0-1.debian.8_amd64.deb` 下載到 Debian 電腦：</span><span class="sxs-lookup"><span data-stu-id="97a92-143">Download the Debian package `powershell_6.0.0-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.8_amd64.deb
```

<span data-ttu-id="97a92-144">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="97a92-144">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="97a92-145">請注意，`dpkg -i` 會因為不符合相依性而失敗；下一個命令 `apt-get install -f` 則會解決這些問題，然後完成 PowerShell 套件設定。</span><span class="sxs-lookup"><span data-stu-id="97a92-145">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="97a92-146">解除安裝 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="97a92-146">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="97a92-147">Debian 9</span><span class="sxs-lookup"><span data-stu-id="97a92-147">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="97a92-148">透過套件存放庫安裝 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="97a92-148">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="97a92-149">PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="97a92-149">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="97a92-150">這是慣用方法。</span><span class="sxs-lookup"><span data-stu-id="97a92-150">This is the preferred method.</span></span>

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

<span data-ttu-id="97a92-151">以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。</span><span class="sxs-lookup"><span data-stu-id="97a92-151">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="97a92-152">透過直接下載安裝 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="97a92-152">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="97a92-153">將[版本][]頁面上的 Debian 套件 `powershell_6.0.0-1.debian.9_amd64.deb` 下載到 Debian 電腦：</span><span class="sxs-lookup"><span data-stu-id="97a92-153">Download the Debian package `powershell_6.0.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

<span data-ttu-id="97a92-154">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="97a92-154">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="97a92-155">請注意，`dpkg -i` 會因為不符合相依性而失敗；下一個命令 `apt-get install -f` 則會解決這些問題，然後完成 PowerShell 套件設定。</span><span class="sxs-lookup"><span data-stu-id="97a92-155">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-9"></a><span data-ttu-id="97a92-156">解除安裝 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="97a92-156">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="97a92-157">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="97a92-157">CentOS 7</span></span>

> <span data-ttu-id="97a92-158">此套件也適用於 Oracle Linux 7。</span><span class="sxs-lookup"><span data-stu-id="97a92-158">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="97a92-159">透過套件存放庫安裝 (慣用) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="97a92-159">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="97a92-160">PowerShell Core for Linux 會發佈到官方 Microsoft 存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="97a92-160">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="97a92-161">以超級使用者身分註冊過 Microsoft 存放庫一次之後，只需要使用 `sudo yum update powershell` 就可以更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="97a92-161">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="97a92-162">透過直接下載安裝 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="97a92-162">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="97a92-163">使用 [CentOS 7][]，將[版本][]頁面上的 RPM 套件 `powershell-6.0.0-1.rhel.7.x86_64.rpm` 下載到 CentOS 電腦：</span><span class="sxs-lookup"><span data-stu-id="97a92-163">Using [CentOS 7][], download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="97a92-164">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="97a92-164">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="97a92-165">您也可以不使用下載的中繼步驟來安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="97a92-165">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="97a92-166">解除安裝 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="97a92-166">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="97a92-168">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="97a92-168">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="97a92-169">透過套件存放庫安裝 (慣用) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="97a92-169">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="97a92-170">PowerShell Core for Linux 會發佈到官方 Microsoft 存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="97a92-170">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="97a92-171">以超級使用者身分註冊過 Microsoft 存放庫一次之後，只需要使用 `sudo yum update powershell` 就可以更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="97a92-171">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="97a92-172">透過直接下載安裝 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="97a92-172">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="97a92-173">將[版本][]頁面上的 RPM 套件 `powershell-6.0.0-1.rhel.7.x86_64.rpm` 下載到 Red Hat Enterprise Linux 電腦：</span><span class="sxs-lookup"><span data-stu-id="97a92-173">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

<span data-ttu-id="97a92-174">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="97a92-174">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="97a92-175">您也可以不使用下載的中繼步驟來安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="97a92-175">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="97a92-176">解除安裝 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="97a92-176">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="97a92-177">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="97a92-177">OpenSUSE 42.2</span></span>

> <span data-ttu-id="97a92-178">**注意：**在安裝 PowerShell Core 時，`zypper` 可能會回報以下錯誤：</span><span class="sxs-lookup"><span data-stu-id="97a92-178">**Note:** When installing PowerShell Core, `zypper` may report the following error:</span></span>
>
> ```text
> Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
>  Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
>  Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
> ```
>
> <span data-ttu-id="97a92-179">在此情況下，請確認下列命令會顯示 `libcurl` 套件為已安裝，來驗證存在符合規範的 `libcurl4` 程式庫：</span><span class="sxs-lookup"><span data-stu-id="97a92-179">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>
>
> ```sh
> zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
> ```
>
> <span data-ttu-id="97a92-180">然後在安裝 `powershell` 套件時選擇 `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` 解決方案。</span><span class="sxs-lookup"><span data-stu-id="97a92-180">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the `powershell` package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="97a92-181">透過套件存放庫安裝 (慣用) - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="97a92-181">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="97a92-182">PowerShell Core for Linux 會發佈到官方 Microsoft 存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="97a92-182">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Product feed
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/zypp/repos.d/microsoft.repo

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="97a92-183">透過直接下載安裝 - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="97a92-183">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="97a92-184">將[版本][]頁面上的 RPM 套件 `powershell-6.0.0-1.rhel.7.x86_64.rpm` 下載到 OpenSUSE 電腦：</span><span class="sxs-lookup"><span data-stu-id="97a92-184">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="97a92-185">您也可以不使用下載的中繼步驟來安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="97a92-185">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="97a92-186">解除安裝 - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="97a92-186">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora-25"></a><span data-ttu-id="97a92-187">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="97a92-187">Fedora 25</span></span>

### <a name="installation-via-package-repository-preferred---fedora-25"></a><span data-ttu-id="97a92-188">透過套件存放庫安裝 (慣用) - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="97a92-188">Installation via Package Repository (preferred) - Fedora 25</span></span>

<span data-ttu-id="97a92-189">PowerShell Core for Linux 會發佈到官方 Microsoft 存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="97a92-189">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-25"></a><span data-ttu-id="97a92-190">透過直接下載安裝 - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="97a92-190">Installation via Direct Download - Fedora 25</span></span>

<span data-ttu-id="97a92-191">將[版本][]頁面上的 RPM 套件 `powershell-6.0.0-1.rhel.7.x86_64.rpm` 下載到 Fedora 電腦：</span><span class="sxs-lookup"><span data-stu-id="97a92-191">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="97a92-192">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="97a92-192">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="97a92-193">您也可以不使用下載的中繼步驟來安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="97a92-193">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-25"></a><span data-ttu-id="97a92-194">解除安裝 - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="97a92-194">Uninstallation - Fedora 25</span></span>

```sh
sudo dnf remove powershell
```

## <a name="fedora-26"></a><span data-ttu-id="97a92-195">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="97a92-195">Fedora 26</span></span>

### <a name="installation-via-package-repository-preferred---fedora-26"></a><span data-ttu-id="97a92-196">透過套件存放庫安裝 (慣用) - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="97a92-196">Installation via Package Repository (preferred) - Fedora 26</span></span>

<span data-ttu-id="97a92-197">PowerShell Core for Linux 會發佈到官方 Microsoft 存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="97a92-197">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-26"></a><span data-ttu-id="97a92-198">透過直接下載安裝 - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="97a92-198">Installation via Direct Download - Fedora 26</span></span>

<span data-ttu-id="97a92-199">將[版本][]頁面上的 RPM 套件 `powershell-6.0.0-1.rhel.7.x86_64.rpm` 下載到 Fedora 電腦：</span><span class="sxs-lookup"><span data-stu-id="97a92-199">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="97a92-200">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="97a92-200">Then execute the following in the terminal:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="97a92-201">您也可以不使用下載的中繼步驟來安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="97a92-201">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-26"></a><span data-ttu-id="97a92-202">解除安裝 - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="97a92-202">Uninstallation - Fedora 26</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="97a92-203">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="97a92-203">Arch Linux</span></span>

<span data-ttu-id="97a92-204">PowerShell 可從 [Arch Linux][] 使用者存放庫 (AUR) 取得。</span><span class="sxs-lookup"><span data-stu-id="97a92-204">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="97a92-205">它可以使用[最新的標記版本][arch-release]編譯</span><span class="sxs-lookup"><span data-stu-id="97a92-205">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="97a92-206">它可以從[主機的最新認可][arch-git]編譯</span><span class="sxs-lookup"><span data-stu-id="97a92-206">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="97a92-207">它可以使用[最新版本的二進位檔][arch-bin]安裝</span><span class="sxs-lookup"><span data-stu-id="97a92-207">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="97a92-208">AUR 中的套件由社群維護 - 沒有官方支援。</span><span class="sxs-lookup"><span data-stu-id="97a92-208">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="97a92-209">如需從 AUR 安裝套件的詳細資訊，請參閱 [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) 或社群 [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile)。</span><span class="sxs-lookup"><span data-stu-id="97a92-209">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="97a92-211">Linux AppImage</span><span class="sxs-lookup"><span data-stu-id="97a92-211">Linux AppImage</span></span>

<span data-ttu-id="97a92-212">使用最新的 Linux 發行版本，將[版本][]頁面上的 AppImage `powershell-6.0.0-x86_64.AppImage` 下載到 Linux 電腦。</span><span class="sxs-lookup"><span data-stu-id="97a92-212">Using a recent Linux distribution, download the AppImage `powershell-6.0.0-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="97a92-213">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="97a92-213">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.0-x86_64.AppImage
./powershell-6.0.0-x86_64.AppImage
```

<span data-ttu-id="97a92-214">[AppImage][] 讓您不用安裝就可執行 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="97a92-214">The [AppImage][] lets you run PowerShell without installing it.</span></span> <span data-ttu-id="97a92-215">它是將 PowerShell 及其相依性 (包括.NET Core 系統相依性) 組合成一個緊密套件的可攜式應用程式。</span><span class="sxs-lookup"><span data-stu-id="97a92-215">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span> <span data-ttu-id="97a92-216">此套件運作不受使用者的 Linux 發行版本影響，且是單一的二進位檔。</span><span class="sxs-lookup"><span data-stu-id="97a92-216">This package works independently of the user's Linux distribution, and is a single binary.</span></span>

[appimage]: http://appimage.org/

## <a name="macos-1012"></a><span data-ttu-id="97a92-218">macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="97a92-218">macOS 10.12</span></span>

### <a name="installation-via-homebrew-preferred---macos-1012"></a><span data-ttu-id="97a92-219">透過 Homebrew 安裝 (慣用) - macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="97a92-219">Installation via Homebrew (preferred) - macOS 10.12</span></span>

<span data-ttu-id="97a92-220">[Homebrew][ brew] 是 macOS 遺漏的套件管理員。</span><span class="sxs-lookup"><span data-stu-id="97a92-220">[Homebrew][brew] is the missing package manager for macOS.</span></span> <span data-ttu-id="97a92-221">如果找不到 `brew` 命令，您需要遵循[指示][brew]安裝 Homebrew。</span><span class="sxs-lookup"><span data-stu-id="97a92-221">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="97a92-222">安裝好 Homebrew 之後，安裝 PowerShell 就很容易。</span><span class="sxs-lookup"><span data-stu-id="97a92-222">Once you've installed Homebrew, installing PowerShell is easy.</span></span> <span data-ttu-id="97a92-223">首先，安裝 [Homebrew-Cask][cask]，以便安裝更多套件：</span><span class="sxs-lookup"><span data-stu-id="97a92-223">First, install [Homebrew-Cask][cask], so you can install more packages:</span></span>

```sh
brew tap caskroom/cask
```

<span data-ttu-id="97a92-224">現在，您可以安裝 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="97a92-224">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="97a92-225">發行新的 PowerShell 版本時，只要更新 Homebrew 的公式並升級 PowerShell 即可：</span><span class="sxs-lookup"><span data-stu-id="97a92-225">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask reinstall powershell
```

> <span data-ttu-id="97a92-226">注意：因為 [Cask 的這個問題](https://github.com/caskroom/homebrew-cask/issues/29301)，目前必須重新安裝才能升級。</span><span class="sxs-lookup"><span data-stu-id="97a92-226">Note: because of [this issue in Cask](https://github.com/caskroom/homebrew-cask/issues/29301), you currently have to do a reinstall to upgrade.</span></span>

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download---macos-1012"></a><span data-ttu-id="97a92-227">透過直接下載安裝 - macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="97a92-227">Installation via Direct Download - macOS 10.12</span></span>

<span data-ttu-id="97a92-228">使用 macOS 10.12，將[版本][]頁面上的 PKG 套件 `powershell-6.0.0-osx.10.12-x64.pkg` 下載至 macOS 電腦。</span><span class="sxs-lookup"><span data-stu-id="97a92-228">Using macOS 10.12, download the PKG package `powershell-6.0.0-osx.10.12-x64.pkg` from the [releases][] page onto the macOS machine.</span></span>

<span data-ttu-id="97a92-229">按兩下檔案依提示執行作業，或從終端機安裝：</span><span class="sxs-lookup"><span data-stu-id="97a92-229">Either double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.0-osx.10.12-x64.pkg -target /
```

### <a name="uninstallation---macos-1012"></a><span data-ttu-id="97a92-230">解除安裝 - macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="97a92-230">Uninstallation - macOS 10.12</span></span>

<span data-ttu-id="97a92-231">如果您使用 Homebrew 安裝 PowerShell，解除安裝很簡單：</span><span class="sxs-lookup"><span data-stu-id="97a92-231">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="97a92-232">如已透過直接下載安裝 PowerShell，即必須手動移除 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="97a92-232">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="97a92-233">若要解除安裝其他的 PowerShell 路徑 (例如使用者設定檔路徑)，請參閱本文件下文中的[路徑][ paths]一節，使用 `sudo rm` 移除所要的路徑。</span><span class="sxs-lookup"><span data-stu-id="97a92-233">To uninstall the additional PowerShell paths (such as the user profile path) please see the [paths][paths] section below in this document and remove the desired the paths with `sudo rm`.</span></span> <span data-ttu-id="97a92-234">(注意：如果使用 Homebrew 安裝，此即非必要。)</span><span class="sxs-lookup"><span data-stu-id="97a92-234">(Note: this is not necessary if you installed with Homebrew.)</span></span>

[paths]:#paths

## <a name="kali"></a><span data-ttu-id="97a92-235">Kali</span><span class="sxs-lookup"><span data-stu-id="97a92-235">Kali</span></span>

### <a name="installation"></a><span data-ttu-id="97a92-236">安裝</span><span class="sxs-lookup"><span data-stu-id="97a92-236">Installation</span></span>

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Download & Install PowerShell
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.16.04_amd64.deb
sudo dpkg -i powershell_6.0.0-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="97a92-237">在最新的 Kali (Kali GNU/Linux Rolling) 中不用安裝即可執行 PowerShell</span><span class="sxs-lookup"><span data-stu-id="97a92-237">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.0-x86_64.AppImage

# Start PowerShell
./powershell-6.0.0-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="97a92-238">解除安裝 - Kali</span><span class="sxs-lookup"><span data-stu-id="97a92-238">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell-6.0.0-x86_64.AppImage
```

## <a name="raspbian"></a><span data-ttu-id="97a92-239">Raspbian</span><span class="sxs-lookup"><span data-stu-id="97a92-239">Raspbian</span></span>

<span data-ttu-id="97a92-240">目前只有 Raspbian Stretch 支援 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="97a92-240">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

### <a name="installation"></a><span data-ttu-id="97a92-241">安裝</span><span class="sxs-lookup"><span data-stu-id="97a92-241">Installation</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="97a92-242">解除安裝 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="97a92-242">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="97a92-243">二進位封存</span><span class="sxs-lookup"><span data-stu-id="97a92-243">Binary Archives</span></span>

<span data-ttu-id="97a92-244">macOS 和 Linux 平台有 PowerShell 二進位 `tar.gz` 封存，以啟用進階的部署案例。</span><span class="sxs-lookup"><span data-stu-id="97a92-244">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="97a92-245">相依性</span><span class="sxs-lookup"><span data-stu-id="97a92-245">Dependencies</span></span>

<span data-ttu-id="97a92-246">在 Linux，PowerShell 為所有 Linux 發行版本建置可攜式二進位檔。</span><span class="sxs-lookup"><span data-stu-id="97a92-246">For Linux, PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="97a92-247">但 .NET Core 執行階段在不同的發行版本需要不同的相依性，所以 PowerShell 也一樣。</span><span class="sxs-lookup"><span data-stu-id="97a92-247">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="97a92-248">下圖顯示正式支援的不同 Linux 發行版本的 .NET Core 2.0 相依性。</span><span class="sxs-lookup"><span data-stu-id="97a92-248">The following chart shows the .NET Core 2.0 dependencies on different Linux distributions that are officially supported.</span></span>

| <span data-ttu-id="97a92-249">作業系統</span><span class="sxs-lookup"><span data-stu-id="97a92-249">OS</span></span>                 | <span data-ttu-id="97a92-250">相依性</span><span class="sxs-lookup"><span data-stu-id="97a92-250">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="97a92-251">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="97a92-251">Ubuntu 14.04</span></span>       | <span data-ttu-id="97a92-252">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="97a92-252">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="97a92-253">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52</span><span class="sxs-lookup"><span data-stu-id="97a92-253">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="97a92-254">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="97a92-254">Ubuntu 16.04</span></span>       | <span data-ttu-id="97a92-255">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="97a92-255">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="97a92-256">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu55</span><span class="sxs-lookup"><span data-stu-id="97a92-256">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="97a92-257">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="97a92-257">Ubuntu 17.04</span></span>       | <span data-ttu-id="97a92-258">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="97a92-258">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="97a92-259">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu57</span><span class="sxs-lookup"><span data-stu-id="97a92-259">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="97a92-260">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="97a92-260">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="97a92-261">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="97a92-261">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="97a92-262">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52</span><span class="sxs-lookup"><span data-stu-id="97a92-262">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="97a92-263">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="97a92-263">Debian 9 (Stretch)</span></span> | <span data-ttu-id="97a92-264">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="97a92-264">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="97a92-265">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.2、libicu57</span><span class="sxs-lookup"><span data-stu-id="97a92-265">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="97a92-266">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="97a92-266">CentOS 7</span></span> <br> <span data-ttu-id="97a92-267">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="97a92-267">Oracle Linux 7</span></span> <br> <span data-ttu-id="97a92-268">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="97a92-268">RHEL 7</span></span> <br> <span data-ttu-id="97a92-269">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="97a92-269">OpenSUSE 42.2</span></span> <br> <span data-ttu-id="97a92-270">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="97a92-270">Fedora 25</span></span> | <span data-ttu-id="97a92-271">libunwind、libcurl、openssl-libs、libicu</span><span class="sxs-lookup"><span data-stu-id="97a92-271">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="97a92-272">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="97a92-272">Fedora 26</span></span>          | <span data-ttu-id="97a92-273">libunwind、libcurl、openssl-libs、libicu、compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="97a92-273">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="97a92-274">為在未正式支援的 Linux 發行版本上部署 PowerShell 二進位檔，您需要在個別步驟中為目標作業系統安裝必要的相依性。</span><span class="sxs-lookup"><span data-stu-id="97a92-274">In order to deploy PowerShell binaries on Linux distributions that are not officially supported, you would need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="97a92-275">例如，[Amazon Linux dockerfile][amazon-dockerfile] 會先安裝相依性，再解壓縮 Linux `tar.gz` 封存。</span><span class="sxs-lookup"><span data-stu-id="97a92-275">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="97a92-276">安裝 - 二進位封存</span><span class="sxs-lookup"><span data-stu-id="97a92-276">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="97a92-277">Linux</span><span class="sxs-lookup"><span data-stu-id="97a92-277">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.0/pwsh /usr/bin/pwsh
```

#### <a name="macos"></a><span data-ttu-id="97a92-278">macOS</span><span class="sxs-lookup"><span data-stu-id="97a92-278">macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.0/pwsh /usr/local/bin/pwsh
```

### <a name="uninstallation---binary-archives"></a><span data-ttu-id="97a92-279">解除安裝 - 二進位封存</span><span class="sxs-lookup"><span data-stu-id="97a92-279">Uninstallation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="97a92-280">Linux</span><span class="sxs-lookup"><span data-stu-id="97a92-280">Linux</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

#### <a name="macos"></a><span data-ttu-id="97a92-281">macOS</span><span class="sxs-lookup"><span data-stu-id="97a92-281">macOS</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="97a92-282">路徑</span><span class="sxs-lookup"><span data-stu-id="97a92-282">Paths</span></span>

* <span data-ttu-id="97a92-283">`$PSHOME` 是 `/opt/microsoft/powershell/6.0.0/`</span><span class="sxs-lookup"><span data-stu-id="97a92-283">`$PSHOME` is `/opt/microsoft/powershell/6.0.0/`</span></span>
* <span data-ttu-id="97a92-284">會從 `~/.config/powershell/profile.ps1` 讀取使用者設定檔</span><span class="sxs-lookup"><span data-stu-id="97a92-284">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="97a92-285">會從 `$PSHOME/profile.ps1` 讀取預設設定檔</span><span class="sxs-lookup"><span data-stu-id="97a92-285">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="97a92-286">會從 `~/.local/share/powershell/Modules` 讀取使用者模組</span><span class="sxs-lookup"><span data-stu-id="97a92-286">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="97a92-287">會從 `/usr/local/share/powershell/Modules` 讀取共用的模組</span><span class="sxs-lookup"><span data-stu-id="97a92-287">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="97a92-288">會從 `$PSHOME/Modules` 讀取預設模組</span><span class="sxs-lookup"><span data-stu-id="97a92-288">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="97a92-289">PSReadline 記錄會記錄在 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="97a92-289">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="97a92-290">設定檔會遵循 PowerShell 的每個主控件設定，讓預設主控件特定設定檔存在於相同位置的 `Microsoft.PowerShell_profile.ps1`。</span><span class="sxs-lookup"><span data-stu-id="97a92-290">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="97a92-291">在 Linux 及 macOS 上，遵循 [XDG 基底目錄規格][xdg-bds]。</span><span class="sxs-lookup"><span data-stu-id="97a92-291">On Linux and macOS, the [XDG Base Directory Specification][xdg-bds] is respected.</span></span>

<span data-ttu-id="97a92-292">請注意，因為 macOS 是 BSD 而非 `/opt` 的衍生項，所以使用的前置詞是 `/usr/local`。</span><span class="sxs-lookup"><span data-stu-id="97a92-292">Note that because macOS is a derivation of BSD, instead of `/opt`, the prefix used is `/usr/local`.</span></span> <span data-ttu-id="97a92-293">因此，`$PSHOME` 是 `/usr/local/microsoft/powershell/6.0.0/`，而且符號連結放在 `/usr/local/bin/pwsh`。</span><span class="sxs-lookup"><span data-stu-id="97a92-293">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.0/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

[版本]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
