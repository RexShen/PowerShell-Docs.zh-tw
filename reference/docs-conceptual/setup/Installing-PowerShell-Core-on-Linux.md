# <a name="installing-powershell-core-on-linux"></a>在 Linux 上安裝 PowerShell Core

支援 [Ubuntu 14.04][u14]、[Ubuntu 16.04][u16]、[Ubuntu 17.10][u17]、[Debian 8][deb8]、[Debian 9][deb9]、[CentOS 7][cos]、[Red Hat Enterprise Linux (RHEL) 7][rhel7]、[OpenSUSE 42.3][opensuse]、[Fedora 27][fedora]、[Fedora 28][fedora] 與 [Arch Linux][arch]。

針對未正式支援的 Linux 發行版本，您可以嘗試使用 [PowerShell AppImage][lai]。
您也可以直接使用 Linux [`tar.gz` 封存][tar]嘗試部署 PowerShell 二進位檔，但您需要根據個別步驟中的作業系統，設定必要的相依性。

GitHub [版本][]頁面上提供所有套件。
安裝套件之後，請從終端機執行 `pwsh`。

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1710
[u18]: #ubuntu-1804
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-423
[fedora]: #fedora
[arch]: #arch-linux
[lai]: #linux-appimage
[tar]: #binary-archives

## <a name="installing-preview-releases"></a>安裝預覽版本

透過套件存放庫安裝 Linux 的 PowerShell Core Preview 版本時，套件名稱會從 `powershell` 變更為 `powershell-preview`。

透過直接下載的安裝不會變更，但檔案名稱除外。

下表是使用各種套件管理員安裝穩定和預覽套件的命令：

|發行版本|穩定命令 | 預覽命令 |
|---------------|---------------|-----------------|
| Ubuntu、Debian |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| CentOS、RedHat |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| OpenSUSE |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| Fedora   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a>Ubuntu 14.04

### <a name="installation-via-package-repository---ubuntu-1404"></a>透過套件存放庫安裝 - Ubuntu 14.04

PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。
這是慣用方法。

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

以超級使用者的身分，註冊 Microsoft 存放庫。
從那時起，您只需要使用`sudo apt-get upgrade powershell`來更新安裝。

### <a name="installation-via-direct-download---ubuntu-1404"></a>透過直接下載安裝 - Ubuntu 14.04

將[版本][]頁面上的 Debian 套件 `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` 下載至 Ubuntu 電腦。

然後在終端機上執行下列作業：

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> `dpkg -i` 命令因相依性不相符而失敗。
> 下一個命令 `apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。

### <a name="uninstallation---ubuntu-1404"></a>解除安裝 - Ubuntu 14.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a>Ubuntu 16.04

### <a name="installation-via-package-repository---ubuntu-1604"></a>透過套件存放庫安裝 - Ubuntu 16.04

PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。
這是慣用方法。

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

以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。

### <a name="installation-via-direct-download---ubuntu-1604"></a>透過直接下載安裝 - Ubuntu 16.04

將[版本][]頁面上的 Debian 套件 `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` 下載至 Ubuntu 電腦。

然後在終端機上執行下列作業：

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> `dpkg -i` 命令因相依性不相符而失敗。
> 下一個命令 `apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。

### <a name="uninstallation---ubuntu-1604"></a>解除安裝 - Ubuntu 16.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1710"></a>Ubuntu 17.10

> [!NOTE]
> 在 `6.1.0-preview.2` 之後已新增 Ubuntu 17.04 支援

### <a name="installation-via-package-repository---ubuntu-1710"></a>透過套件存放庫安裝 - Ubuntu 17.10

PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。
這是慣用方法。

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

以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。

### <a name="installation-via-direct-download---ubuntu-1710"></a>透過直接下載安裝 - Ubuntu 17.10

將[版本][]頁面上的 Debian 套件 `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` 下載至 Ubuntu 電腦。

然後在終端機上執行下列作業：

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.10_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> `dpkg -i` 命令因相依性不相符而失敗。
> 下一個命令 `apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。

### <a name="uninstallation---ubuntu-1710"></a>解除安裝 - Ubuntu 17.10

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a>Ubuntu 18.04

> [!NOTE]
> 在 `6.1.0-preview.2` 之後已新增 Ubuntu 18.04 支援

### <a name="installation-via-package-repository---ubuntu-1804"></a>透過套件存放庫安裝 - Ubuntu 18.04

PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。
這是慣用方法。

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

以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。

### <a name="installation-via-direct-download---ubuntu-1804"></a>透過直接下載安裝 - Ubuntu 18.04

將[版本][]頁面上的 Debian 套件 `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` 下載至 Ubuntu 電腦。

然後在終端機上執行下列作業：

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> `dpkg -i` 命令因相依性不相符而失敗。
> 下一個命令 `apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。

### <a name="uninstallation---ubuntu-1804"></a>解除安裝 - Ubuntu 18.04

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a>Debian 8

### <a name="installation-via-package-repository---debian-8"></a>透過套件存放庫安裝 - Debian 8

PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。
這是慣用方法。

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

以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。

### <a name="installation-via-direct-download---debian-8"></a>透過直接下載安裝 - Debian 8

將[版本][]頁面上的 Debian 套件 `powershell_6.0.2-1.debian.8_amd64.deb` 下載至 Debian 電腦。

然後在終端機上執行下列作業：

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> `dpkg -i` 命令因相依性不相符而失敗。
> 下一個命令 `apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。

### <a name="uninstallation---debian-8"></a>解除安裝 - Debian 8

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a>Debian 9

### <a name="installation-via-package-repository---debian-9"></a>透過套件存放庫安裝 - Debian 9

PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。
這是慣用方法。

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

以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。

### <a name="installation-via-direct-download---debian-9"></a>透過直接下載安裝 - Debian 9

將[版本][]頁面上的 Debian 套件 `powershell_6.0.2-1.debian.9_amd64.deb` 下載至 Debian 電腦。

然後在終端機上執行下列作業：

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a>解除安裝 - Debian 9

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a>CentOS 7

> [!NOTE]
> 此套件也適用於 Oracle Linux 7。

### <a name="installation-via-package-repository-preferred---centos-7"></a>透過套件存放庫安裝 (慣用) - CentOS 7

PowerShell Core for Linux 會發佈到官方 Microsoft 存放庫進行簡易安裝 (及更新)。

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

以超級使用者身分註冊過 Microsoft 存放庫一次之後，只需要使用 `sudo yum update powershell` 就可以更新 PowerShell。

### <a name="installation-via-direct-download---centos-7"></a>透過直接下載安裝 - CentOS 7

使用 [CentOS 7][]，將[版本][]頁面上的 RPM 套件 `powershell-6.0.2-1.rhel.7.x86_64.rpm` 下載至 CentOS 電腦。

然後在終端機上執行下列作業：

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

您也可以不使用下載的中繼步驟來安裝 RPM：

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a>解除安裝 - CentOS 7

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a>透過套件存放庫安裝 (慣用) - Red Hat Enterprise Linux (RHEL) 7

PowerShell Core for Linux 會發佈到官方 Microsoft 存放庫進行簡易安裝 (及更新)。

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

以超級使用者身分註冊過 Microsoft 存放庫一次之後，只需要使用 `sudo yum update powershell` 就可以更新 PowerShell。

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a>透過直接下載安裝 - Red Hat Enterprise Linux (RHEL) 7

將[版本][]頁面上的 RPM 套件 `powershell-6.0.2-1.rhel.7.x86_64.rpm` 下載到 Red Hat Enterprise Linux 電腦。

然後在終端機上執行下列作業：

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

您也可以不使用下載的中繼步驟來安裝 RPM：

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>解除安裝 - Red Hat Enterprise Linux (RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse-423"></a>OpenSUSE 42.3

安裝 PowerShell Core 時，`zypper` 可能會回報以下錯誤：

```Output
Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
 Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
```

在此情況下，請確認下列命令會顯示 `libcurl` 套件為已安裝，來驗證存在符合規範的 `libcurl4` 程式庫：

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

然後在安裝 PowerShell 套件時，選擇 `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` 解決方案。

### <a name="installation-via-package-repository-preferred---opensuse-423"></a>透過套件存放庫安裝 (慣用) - OpenSUSE 42.3

PowerShell Core for Linux 會發佈到官方 Microsoft 存放庫進行簡易安裝 (及更新)。

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

### <a name="installation-via-direct-download---opensuse-423"></a>透過直接下載安裝 - OpenSUSE 42.3

將[版本][]頁面上的 RPM 套件 `powershell-6.0.2-1.rhel.7.x86_64.rpm` 下載到 OpenSUSE 電腦。

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

您也可以不使用下載的中繼步驟來安裝 RPM：

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-423"></a>解除安裝 - OpenSUSE 42.3

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a>Fedora

> [!NOTE]
> 只有 PowerShell Core 6.1 和更新版本才支援 Fedora 28。

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a>透過套件存放庫安裝 (慣用) - Fedora 27、Fedora 28

PowerShell Core for Linux 會發佈到官方 Microsoft 存放庫進行簡易安裝 (及更新)。

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a>透過直接下載安裝 - Fedora 27、Fedora 28

將[版本][]頁面上的 RPM 套件 `powershell-6.0.2-1.rhel.7.x86_64.rpm` 下載到 Fedora 電腦。

然後在終端機上執行下列作業：

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

您也可以不使用下載的中繼步驟來安裝 RPM：

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a>解除安裝 - Fedora 27、Fedora 28

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a>Arch Linux

> [!NOTE]
> Arch 支援為實驗性。

PowerShell 可從 [Arch Linux][] 使用者存放庫 (AUR) 取得。

* 它可以使用[最新的標記版本][arch-release]編譯
* 它可以從[主機的最新認可][arch-git]編譯
* 它可以使用[最新版本的二進位檔][arch-bin]安裝

AUR 中的套件由社群維護 - 沒有官方支援。

如需從 AUR 安裝套件的詳細資訊，請參閱 [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) 或社群 [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile)。

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a>Linux AppImage

> [!NOTE]
> AppImage 支援為實驗性

使用最新的 Linux 發行版本，將[版本][]頁面上的 AppImage `powershell-6.0.1-x86_64.AppImage` 下載到 Linux 電腦。

然後在終端機上執行下列作業：

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

[AppImage][] 讓您不用安裝就可執行 PowerShell。
它是將 PowerShell 及其相依性 (包括.NET Core 系統相依性) 組合成一個緊密套件的可攜式應用程式。
此套件是單一的二進位檔，可不受使用者的 Linux 發行版本影響而運作。

[appimage]: http://appimage.org/

## <a name="kali"></a>Kali

> [!NOTE]
> Kali 支援為實驗性。

### <a name="installation"></a>安裝

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a>在最新的 Kali (Kali GNU/Linux Rolling) 中不用安裝即可執行 PowerShell

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a>解除安裝 - Kali

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a>Raspbian

> [!NOTE]
> Raspbian 支援為實驗性。

目前只有 Raspbian Stretch 支援 PowerShell。

另外，CoreCLR (和 PowerShell Core) 僅適用於 Pi 2 和 Pi 3 裝置，因為像 [Pi Zero](https://github.com/dotnet/coreclr/issues/10605) 此類的其他裝置，它們的處理器不被支援。

下載 [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/)並 遵循[安裝指示](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)來把它安裝到您的 Pi。

### <a name="installation"></a>安裝

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

或者，您可以建立一個符號連結，無需指定 "pwsh" 二進位路徑，便能啟動 PowerShell。

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a>解除安裝 - Raspbian

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a>二進位封存

Linux 平台有 PowerShell 二進位 `tar.gz` 封存，以啟用進階的部署案例。

### <a name="dependencies"></a>相依性

PowerShell 會為所有 Linux 發行版本建置可攜式二進位檔。
但 .NET Core 執行階段在不同的發行版本需要不同的相依性，所以 PowerShell 也一樣。

下圖顯示不同 Linux 發行版本上，正式支援的 .NET Core 2.0 相依性。

| 作業系統                 | 相依性 |
| ------------------ | ------------ |
| Ubuntu 14.04       | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52 |
| Ubuntu 16.04       | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu55 |
| Ubuntu 17.10       | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu57 |
| Ubuntu 18.04       | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu60 |
| Debian 8 (Jessie)  | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52 |
| Debian 9 (Stretch) | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.2、libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 <br> OpenSUSE OpenSUSE 42.3 | libunwind、libcurl、openssl-libs、libicu |
| Fedora 27 <br> Fedora 28 | libunwind、libcurl、openssl-libs、libicu、compat-openssl10 |

若要在未正式支援的 Linux 發行版本上部署 PowerShell 二進位檔，您需要在個別步驟中為目標作業系統安裝必要的相依性。
例如，[Amazon Linux dockerfile][amazon-dockerfile] 會先安裝相依性，再解壓縮 Linux `tar.gz` 封存。

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a>安裝 - 二進位封存

#### <a name="linux"></a>Linux

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

### <a name="uninstalling-binary-archives"></a>解除安裝二進位封存

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a>路徑

* `$PSHOME` 是 `/opt/microsoft/powershell/6.0.2/`
* 會從 `~/.config/powershell/profile.ps1` 讀取使用者設定檔
* 會從 `$PSHOME/profile.ps1` 讀取預設設定檔
* 會從 `~/.local/share/powershell/Modules` 讀取使用者模組
* 會從 `/usr/local/share/powershell/Modules` 讀取共用的模組
* 會從 `$PSHOME/Modules` 讀取預設模組
* PSReadline 記錄會記錄在 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

設定檔會遵循 PowerShell 的每個主控件設定，讓預設主控件特定設定檔存在於相同位置的 `Microsoft.PowerShell_profile.ps1`。

PowerShell 遵循 Linux 上的 [XDG 基底目錄規格][xdg-bds]。

[版本]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
