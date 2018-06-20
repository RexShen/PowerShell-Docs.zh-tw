# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="c3ef2-101">在 Linux 上安裝 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="c3ef2-101">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="c3ef2-102">支援 [Ubuntu 14.04][u14]、[Ubuntu 16.04][u16]、[Ubuntu 17.04][u17]、[Debian 8][deb8]、[Debian 9][deb9]、[CentOS 7][cos]、[Red Hat Enterprise Linux (RHEL) 7][rhel7]、[OpenSUSE 42.2][opensuse]、[Fedora 27][fedora]、[Fedora 28][fedora] 與 [Arch Linux][arch]。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="c3ef2-103">針對未正式支援的 Linux 發行版本，您可以嘗試使用 [PowerShell AppImage][lai]。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="c3ef2-104">您也可以直接使用 Linux [`tar.gz` 封存][tar]嘗試部署 PowerShell 二進位檔，但您需要根據個別步驟中的作業系統，設定必要的相依性。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="c3ef2-105">GitHub [版本][]頁面上提供所有套件。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="c3ef2-106">安裝套件之後，請從終端機執行 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1704
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fedora]: #fedora
[arch]: #arch-linux
[lai]: #linux-appimage
[tar]: #binary-archives

## <a name="ubuntu-1404"></a><span data-ttu-id="c3ef2-107">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="c3ef2-107">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="c3ef2-108">透過套件存放庫安裝 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="c3ef2-108">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="c3ef2-109">PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-109">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c3ef2-110">這是慣用方法。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-110">This is the preferred method.</span></span>

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

<span data-ttu-id="c3ef2-111">以超級使用者的身分，註冊 Microsoft 存放庫。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-111">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="c3ef2-112">從那時起，您只需要使用`sudo apt-get upgrade powershell`來更新安裝。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-112">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="c3ef2-113">透過直接下載安裝 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="c3ef2-113">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="c3ef2-114">將[版本][]頁面上的 Debian 套件 `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` 下載至 Ubuntu 電腦。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-114">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="c3ef2-115">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="c3ef2-115">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="c3ef2-116">請注意，`dpkg -i` 會因為不符合相依性而失敗；下一個命令 `apt-get install -f` 則會解決這些問題，然後完成 PowerShell 套件設定。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-116">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="c3ef2-117">解除安裝 - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="c3ef2-117">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="c3ef2-118">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="c3ef2-118">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="c3ef2-119">透過套件存放庫安裝 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="c3ef2-119">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="c3ef2-120">PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-120">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c3ef2-121">這是慣用方法。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-121">This is the preferred method.</span></span>

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

<span data-ttu-id="c3ef2-122">以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-122">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="c3ef2-123">透過直接下載安裝 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="c3ef2-123">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="c3ef2-124">將[版本][]頁面上的 Debian 套件 `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` 下載至 Ubuntu 電腦。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-124">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="c3ef2-125">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="c3ef2-125">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="c3ef2-126">請注意，`dpkg -i` 會因為不符合相依性而失敗；下一個命令 `apt-get install -f` 則會解決這些問題，然後完成 PowerShell 套件設定。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-126">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="c3ef2-127">解除安裝 - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="c3ef2-127">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a><span data-ttu-id="c3ef2-128">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="c3ef2-128">Ubuntu 17.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1704"></a><span data-ttu-id="c3ef2-129">透過套件存放庫安裝 - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="c3ef2-129">Installation via Package Repository - Ubuntu 17.04</span></span>

<span data-ttu-id="c3ef2-130">PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-130">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c3ef2-131">這是慣用方法。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-131">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/17.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="c3ef2-132">以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-132">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1704"></a><span data-ttu-id="c3ef2-133">透過直接下載安裝 - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="c3ef2-133">Installation via Direct Download - Ubuntu 17.04</span></span>

<span data-ttu-id="c3ef2-134">將[版本][]頁面上的 Debian 套件 `powershell_6.0.2-1.ubuntu.17.04_amd64.deb` 下載至 Ubuntu 電腦。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-134">Download the Debian package `powershell_6.0.2-1.ubuntu.17.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="c3ef2-135">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="c3ef2-135">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="c3ef2-136">請注意，`dpkg -i` 會因為不符合相依性而失敗；下一個命令 `apt-get install -f` 則會解決這些問題，然後完成 PowerShell 套件設定。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-136">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1704"></a><span data-ttu-id="c3ef2-137">解除安裝 - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="c3ef2-137">Uninstallation - Ubuntu 17.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="c3ef2-138">Debian 8</span><span class="sxs-lookup"><span data-stu-id="c3ef2-138">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="c3ef2-139">透過套件存放庫安裝 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="c3ef2-139">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="c3ef2-140">PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-140">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c3ef2-141">這是慣用方法。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-141">This is the preferred method.</span></span>

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

<span data-ttu-id="c3ef2-142">以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-142">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="c3ef2-143">透過直接下載安裝 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="c3ef2-143">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="c3ef2-144">將[版本][]頁面上的 Debian 套件 `powershell_6.0.2-1.debian.8_amd64.deb` 下載至 Debian 電腦。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-144">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="c3ef2-145">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="c3ef2-145">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="c3ef2-146">請注意，`dpkg -i` 會因 unmet 相依性而失敗。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-146">Please note that `dpkg -i` will fail with unmet dependencies.</span></span>
> <span data-ttu-id="c3ef2-147">請注意，`apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-147">The next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="c3ef2-148">解除安裝 - Debian 8</span><span class="sxs-lookup"><span data-stu-id="c3ef2-148">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="c3ef2-149">Debian 9</span><span class="sxs-lookup"><span data-stu-id="c3ef2-149">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="c3ef2-150">透過套件存放庫安裝 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="c3ef2-150">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="c3ef2-151">PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-151">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c3ef2-152">這是慣用方法。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-152">This is the preferred method.</span></span>

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

<span data-ttu-id="c3ef2-153">以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-153">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="c3ef2-154">透過直接下載安裝 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="c3ef2-154">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="c3ef2-155">將[版本][]頁面上的 Debian 套件 `powershell_6.0.2-1.debian.9_amd64.deb` 下載至 Debian 電腦。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-155">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="c3ef2-156">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="c3ef2-156">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="c3ef2-157">請注意，`dpkg -i` 會因 unmet 相依性而失敗。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-157">Please note that `dpkg -i` will fail with unmet dependencies.</span></span>
> <span data-ttu-id="c3ef2-158">請注意，`apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-158">The next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-9"></a><span data-ttu-id="c3ef2-159">解除安裝 - Debian 9</span><span class="sxs-lookup"><span data-stu-id="c3ef2-159">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="c3ef2-160">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c3ef2-160">CentOS 7</span></span>

> <span data-ttu-id="c3ef2-161">此套件也適用於 Oracle Linux 7。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-161">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="c3ef2-162">透過套件存放庫安裝 (慣用) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c3ef2-162">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="c3ef2-163">PowerShell Core for Linux 會發佈到官方 Microsoft 存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-163">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="c3ef2-164">以超級使用者身分註冊過 Microsoft 存放庫一次之後，只需要使用 `sudo yum update powershell` 就可以更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-164">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="c3ef2-165">透過直接下載安裝 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c3ef2-165">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="c3ef2-166">使用 [CentOS 7][]，將[版本][]頁面上的 RPM 套件 `powershell-6.0.2-1.rhel.7.x86_64.rpm` 下載至 CentOS 電腦。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-166">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="c3ef2-167">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="c3ef2-167">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="c3ef2-168">您也可以不使用下載的中繼步驟來安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="c3ef2-168">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="c3ef2-169">解除安裝 - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c3ef2-169">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="c3ef2-171">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="c3ef2-171">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="c3ef2-172">透過套件存放庫安裝 (慣用) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="c3ef2-172">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="c3ef2-173">PowerShell Core for Linux 會發佈到官方 Microsoft 存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-173">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="c3ef2-174">以超級使用者身分註冊過 Microsoft 存放庫一次之後，只需要使用 `sudo yum update powershell` 就可以更新 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-174">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="c3ef2-175">透過直接下載安裝 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="c3ef2-175">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="c3ef2-176">將[版本][]頁面上的 RPM 套件 `powershell-6.0.2-1.rhel.7.x86_64.rpm` 下載到 Red Hat Enterprise Linux 電腦。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-176">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="c3ef2-177">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="c3ef2-177">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="c3ef2-178">您也可以不使用下載的中繼步驟來安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="c3ef2-178">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="c3ef2-179">解除安裝 - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="c3ef2-179">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="c3ef2-180">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="c3ef2-180">OpenSUSE 42.2</span></span>

> [!NOTE]
> <span data-ttu-id="c3ef2-181">安裝 PowerShell Core 時，`zypper` 可能會回報以下錯誤：</span><span class="sxs-lookup"><span data-stu-id="c3ef2-181">When installing PowerShell Core, `zypper` may report the following error:</span></span>
>
> ```Output
> Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
>  Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
>  Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
> ```
>
> <span data-ttu-id="c3ef2-182">在此情況下，請確認下列命令會顯示 `libcurl` 套件為已安裝，來驗證存在符合規範的 `libcurl4` 程式庫：</span><span class="sxs-lookup"><span data-stu-id="c3ef2-182">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>
>
> ```sh
> zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
> ```
>
> <span data-ttu-id="c3ef2-183">然後在安裝 PowerShell 套件時，選擇 `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` 解決方案。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-183">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="c3ef2-184">透過套件存放庫安裝 (慣用) - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="c3ef2-184">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="c3ef2-185">PowerShell Core for Linux 會發佈到官方 Microsoft 存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-185">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="c3ef2-186">透過直接下載安裝 - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="c3ef2-186">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="c3ef2-187">將[版本][]頁面上的 RPM 套件 `powershell-6.0.2-1.rhel.7.x86_64.rpm` 下載到 OpenSUSE 電腦。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-187">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="c3ef2-188">您也可以不使用下載的中繼步驟來安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="c3ef2-188">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="c3ef2-189">解除安裝 - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="c3ef2-189">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="c3ef2-190">Fedora</span><span class="sxs-lookup"><span data-stu-id="c3ef2-190">Fedora</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="c3ef2-191">透過套件存放庫安裝 (慣用) - Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="c3ef2-191">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="c3ef2-192">PowerShell Core for Linux 會發佈到官方 Microsoft 存放庫進行簡易安裝 (及更新)。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-192">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="c3ef2-193">透過直接下載安裝 - Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="c3ef2-193">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="c3ef2-194">將[版本][]頁面上的 RPM 套件 `powershell-6.0.2-1.rhel.7.x86_64.rpm` 下載到 Fedora 電腦。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-194">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="c3ef2-195">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="c3ef2-195">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="c3ef2-196">您也可以不使用下載的中繼步驟來安裝 RPM：</span><span class="sxs-lookup"><span data-stu-id="c3ef2-196">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="c3ef2-197">解除安裝 - Fedora 27、Fedora 28</span><span class="sxs-lookup"><span data-stu-id="c3ef2-197">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="c3ef2-198">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="c3ef2-198">Arch Linux</span></span>

<span data-ttu-id="c3ef2-199">PowerShell 可從 [Arch Linux][] 使用者存放庫 (AUR) 取得。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-199">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="c3ef2-200">它可以使用[最新的標記版本][arch-release]編譯</span><span class="sxs-lookup"><span data-stu-id="c3ef2-200">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="c3ef2-201">它可以從[主機的最新認可][arch-git]編譯</span><span class="sxs-lookup"><span data-stu-id="c3ef2-201">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="c3ef2-202">它可以使用[最新版本的二進位檔][arch-bin]安裝</span><span class="sxs-lookup"><span data-stu-id="c3ef2-202">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="c3ef2-203">AUR 中的套件由社群維護 - 沒有官方支援。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-203">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="c3ef2-204">如需從 AUR 安裝套件的詳細資訊，請參閱 [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) 或社群 [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile)。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-204">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="c3ef2-206">Linux AppImage</span><span class="sxs-lookup"><span data-stu-id="c3ef2-206">Linux AppImage</span></span>

<span data-ttu-id="c3ef2-207">使用最新的 Linux 發行版本，將[版本][]頁面上的 AppImage `powershell-6.0.1-x86_64.AppImage` 下載到 Linux 電腦。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-207">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="c3ef2-208">然後在終端機上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="c3ef2-208">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="c3ef2-209">[AppImage][] 讓您不用安裝就可執行 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-209">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="c3ef2-210">它是將 PowerShell 及其相依性 (包括.NET Core 系統相依性) 組合成一個緊密套件的可攜式應用程式。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-210">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="c3ef2-211">此套件的運作不受使用者的 Linux 發行版本影響，且是單一的二進位檔。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-211">This package  is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="c3ef2-213">Kali</span><span class="sxs-lookup"><span data-stu-id="c3ef2-213">Kali</span></span>

### <a name="installation"></a><span data-ttu-id="c3ef2-214">安裝</span><span class="sxs-lookup"><span data-stu-id="c3ef2-214">Installation</span></span>

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="c3ef2-215">在最新的 Kali (Kali GNU/Linux Rolling) 中不用安裝即可執行 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c3ef2-215">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="c3ef2-216">解除安裝 - Kali</span><span class="sxs-lookup"><span data-stu-id="c3ef2-216">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="c3ef2-217">Raspbian</span><span class="sxs-lookup"><span data-stu-id="c3ef2-217">Raspbian</span></span>

<span data-ttu-id="c3ef2-218">目前只有 Raspbian Stretch 支援 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-218">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="c3ef2-219">另外，CoreCLR (和 PowerShell Core) 僅適用於 Pi 2 和 Pi 3 裝置，因為像 [Pi Zero](https://github.com/dotnet/coreclr/issues/10605) 此類的其他裝置，它們的處理器不被支援。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-219">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="c3ef2-220">下載 [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/)並 遵循[安裝指示](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)來把它安裝到您的 Pi。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-220">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="c3ef2-221">安裝</span><span class="sxs-lookup"><span data-stu-id="c3ef2-221">Installation</span></span>

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

<span data-ttu-id="c3ef2-222">或者，您可以建立一個符號連結，無需指定 "pwsh" 二進位路徑，便能啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-222">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="c3ef2-223">解除安裝 - Raspbian</span><span class="sxs-lookup"><span data-stu-id="c3ef2-223">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="c3ef2-224">二進位封存</span><span class="sxs-lookup"><span data-stu-id="c3ef2-224">Binary Archives</span></span>

<span data-ttu-id="c3ef2-225">Linux 平台有 PowerShell 二進位 `tar.gz` 封存，以啟用進階的部署案例。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-225">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="c3ef2-226">相依性</span><span class="sxs-lookup"><span data-stu-id="c3ef2-226">Dependencies</span></span>

<span data-ttu-id="c3ef2-227">PowerShell 會為所有 Linux 發行版本建置可攜式二進位檔。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-227">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="c3ef2-228">但 .NET Core 執行階段在不同的發行版本需要不同的相依性，所以 PowerShell 也一樣。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-228">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="c3ef2-229">下圖顯示不同 Linux 發行版本上，正式支援的 .NET Core 2.0 相依性。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-229">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="c3ef2-230">作業系統</span><span class="sxs-lookup"><span data-stu-id="c3ef2-230">OS</span></span>                 | <span data-ttu-id="c3ef2-231">相依性</span><span class="sxs-lookup"><span data-stu-id="c3ef2-231">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="c3ef2-232">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="c3ef2-232">Ubuntu 14.04</span></span>       | <span data-ttu-id="c3ef2-233">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="c3ef2-233">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c3ef2-234">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52</span><span class="sxs-lookup"><span data-stu-id="c3ef2-234">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="c3ef2-235">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="c3ef2-235">Ubuntu 16.04</span></span>       | <span data-ttu-id="c3ef2-236">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="c3ef2-236">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c3ef2-237">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu55</span><span class="sxs-lookup"><span data-stu-id="c3ef2-237">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="c3ef2-238">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="c3ef2-238">Ubuntu 17.04</span></span>       | <span data-ttu-id="c3ef2-239">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="c3ef2-239">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c3ef2-240">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu57</span><span class="sxs-lookup"><span data-stu-id="c3ef2-240">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="c3ef2-241">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="c3ef2-241">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="c3ef2-242">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="c3ef2-242">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c3ef2-243">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52</span><span class="sxs-lookup"><span data-stu-id="c3ef2-243">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="c3ef2-244">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="c3ef2-244">Debian 9 (Stretch)</span></span> | <span data-ttu-id="c3ef2-245">libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、</span><span class="sxs-lookup"><span data-stu-id="c3ef2-245">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c3ef2-246">libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.2、libicu57</span><span class="sxs-lookup"><span data-stu-id="c3ef2-246">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="c3ef2-247">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c3ef2-247">CentOS 7</span></span> <br> <span data-ttu-id="c3ef2-248">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="c3ef2-248">Oracle Linux 7</span></span> <br> <span data-ttu-id="c3ef2-249">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="c3ef2-249">RHEL 7</span></span> <br> <span data-ttu-id="c3ef2-250">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="c3ef2-250">OpenSUSE 42.2</span></span> | <span data-ttu-id="c3ef2-251">libunwind、libcurl、openssl-libs、libicu</span><span class="sxs-lookup"><span data-stu-id="c3ef2-251">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="c3ef2-252">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="c3ef2-252">Fedora 27</span></span> <br> <span data-ttu-id="c3ef2-253">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="c3ef2-253">Fedora 28</span></span> | <span data-ttu-id="c3ef2-254">libunwind、libcurl、openssl-libs、libicu、compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="c3ef2-254">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="c3ef2-255">若要在未正式支援的 Linux 發行版本上部署 PowerShell 二進位檔，您需要在個別步驟中為目標作業系統安裝必要的相依性。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-255">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="c3ef2-256">例如，[Amazon Linux dockerfile][amazon-dockerfile] 會先安裝相依性，再解壓縮 Linux `tar.gz` 封存。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-256">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="c3ef2-257">安裝 - 二進位封存</span><span class="sxs-lookup"><span data-stu-id="c3ef2-257">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="c3ef2-258">Linux</span><span class="sxs-lookup"><span data-stu-id="c3ef2-258">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="c3ef2-259">解除安裝二進位封存</span><span class="sxs-lookup"><span data-stu-id="c3ef2-259">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="c3ef2-260">路徑</span><span class="sxs-lookup"><span data-stu-id="c3ef2-260">Paths</span></span>

* <span data-ttu-id="c3ef2-261">`$PSHOME` 是 `/opt/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="c3ef2-261">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="c3ef2-262">會從 `~/.config/powershell/profile.ps1` 讀取使用者設定檔</span><span class="sxs-lookup"><span data-stu-id="c3ef2-262">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="c3ef2-263">會從 `$PSHOME/profile.ps1` 讀取預設設定檔</span><span class="sxs-lookup"><span data-stu-id="c3ef2-263">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="c3ef2-264">會從 `~/.local/share/powershell/Modules` 讀取使用者模組</span><span class="sxs-lookup"><span data-stu-id="c3ef2-264">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="c3ef2-265">會從 `/usr/local/share/powershell/Modules` 讀取共用的模組</span><span class="sxs-lookup"><span data-stu-id="c3ef2-265">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="c3ef2-266">會從 `$PSHOME/Modules` 讀取預設模組</span><span class="sxs-lookup"><span data-stu-id="c3ef2-266">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="c3ef2-267">PSReadline 記錄會記錄在 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="c3ef2-267">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="c3ef2-268">設定檔會遵循 PowerShell 的每個主控件設定，讓預設主控件特定設定檔存在於相同位置的 `Microsoft.PowerShell_profile.ps1`。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-268">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="c3ef2-269">PowerShell 遵循 Linux 上的 [XDG 基底目錄規格][xdg-bds]。</span><span class="sxs-lookup"><span data-stu-id="c3ef2-269">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[版本]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
