# <a name="installing-powershell-core-on-macos-and-linux"></a>在 macOS 與 Linux 上安裝 PowerShell Core

支援 [Ubuntu 14.04][u14]、[Ubuntu 16.04][u16]、[Ubuntu 17.04][u17]、[Debian 8][deb8]、[Debian 9][deb9]、[CentOS 7][cos]、[Red Hat Enterprise Linux (RHEL) 7][rhel7]、[OpenSUSE 42.2][opensuse]、[Fedora 25][fed25]、[Fedora 26][fed26]、[Arch Linux][arch] 和 [macOS 10.12][mac]。

針對未正式支援的 Linux 發行版本，您可以嘗試使用 [PowerShell AppImage][lai]。 您也可以直接使用 Linux [`tar.gz` 封存][tar]嘗試部署 PowerShell 二進位檔，但您需要根據個別步驟中的作業系統，設定必要的相依性。

GitHub [版本][]頁面上提供所有套件。 安裝套件之後，請從終端機執行 `pwsh`。

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

## <a name="ubuntu-1404"></a>Ubuntu 14.04

### <a name="installation-via-package-repository---ubuntu-1404"></a>透過套件存放庫安裝 - Ubuntu 14.04

PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。 這是慣用方法。

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

以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。

### <a name="installation-via-direct-download---ubuntu-1404"></a>透過直接下載安裝 - Ubuntu 14.04

將[版本][]頁面上的 Debian 套件 `powershell_6.0.0-1.ubuntu.14.04_amd64.deb` 下載至 Ubuntu 電腦。

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.14.04_amd64.deb
```

然後在終端機上執行下列作業：

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> 請注意，`dpkg -i` 會因為不符合相依性而失敗；下一個命令 `apt-get install -f` 則會解決這些問題，然後完成 PowerShell 套件設定。

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
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。

### <a name="installation-via-direct-download---ubuntu-1604"></a>透過直接下載安裝 - Ubuntu 16.04

將[版本][]頁面上的 Debian 套件 `powershell_6.0.0-1.ubuntu.16.04_amd64.deb` 下載到 Ubuntu 電腦：

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.16.04_amd64.deb
```

然後在終端機上執行下列作業：

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> 請注意，`dpkg -i` 會因為不符合相依性而失敗；下一個命令 `apt-get install -f` 則會解決這些問題，然後完成 PowerShell 套件設定。

### <a name="uninstallation---ubuntu-1604"></a>解除安裝 - Ubuntu 16.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a>Ubuntu 17.04

### <a name="installation-via-package-repository---ubuntu-1704"></a>透過套件存放庫安裝 - Ubuntu 17.04

PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。
這是慣用方法。

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

以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。

### <a name="installation-via-direct-download---ubuntu-1704"></a>透過直接下載安裝 - Ubuntu 17.04

將[版本][]頁面上的 Debian 套件 `powershell_6.0.0-1.ubuntu.17.04_amd64.deb` 下載到 Ubuntu 電腦：

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.17.04_amd64.deb
```

然後在終端機上執行下列作業：

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> 請注意，`dpkg -i` 會因為不符合相依性而失敗；下一個命令 `apt-get install -f` 則會解決這些問題，然後完成 PowerShell 套件設定。

### <a name="uninstallation---ubuntu-1704"></a>解除安裝 - Ubuntu 17.04

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

將[版本][]頁面上的 Debian 套件 `powershell_6.0.0-1.debian.8_amd64.deb` 下載到 Debian 電腦：

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.8_amd64.deb
```

然後在終端機上執行下列作業：

```sh
sudo dpkg -i powershell_6.0.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> 請注意，`dpkg -i` 會因為不符合相依性而失敗；下一個命令 `apt-get install -f` 則會解決這些問題，然後完成 PowerShell 套件設定。

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

將[版本][]頁面上的 Debian 套件 `powershell_6.0.0-1.debian.9_amd64.deb` 下載到 Debian 電腦：

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

然後在終端機上執行下列作業：

```sh
sudo dpkg -i powershell_6.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

> 請注意，`dpkg -i` 會因為不符合相依性而失敗；下一個命令 `apt-get install -f` 則會解決這些問題，然後完成 PowerShell 套件設定。

### <a name="uninstallation---debian-9"></a>解除安裝 - Debian 9

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a>CentOS 7

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

使用 [CentOS 7][]，將[版本][]頁面上的 RPM 套件 `powershell-6.0.0-1.rhel.7.x86_64.rpm` 下載到 CentOS 電腦：

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

然後在終端機上執行下列作業：

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

您也可以不使用下載的中繼步驟來安裝 RPM：

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
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

將[版本][]頁面上的 RPM 套件 `powershell-6.0.0-1.rhel.7.x86_64.rpm` 下載到 Red Hat Enterprise Linux 電腦：

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

然後在終端機上執行下列作業：

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

您也可以不使用下載的中繼步驟來安裝 RPM：

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>解除安裝 - Red Hat Enterprise Linux (RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a>OpenSUSE 42.2

> **注意：**在安裝 PowerShell Core 時，`zypper` 可能會回報以下錯誤：
>
> ```text
> Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
>  Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
>  Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
> ```
>
> 在此情況下，請確認下列命令會顯示 `libcurl` 套件為已安裝，來驗證存在符合規範的 `libcurl4` 程式庫：
>
> ```sh
> zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
> ```
>
> 然後在安裝 `powershell` 套件時選擇 `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` 解決方案。

### <a name="installation-via-package-repository-preferred---opensuse-422"></a>透過套件存放庫安裝 (慣用) - OpenSUSE 42.2

PowerShell Core for Linux 會發佈到官方 Microsoft 存放庫進行簡易安裝 (及更新)。

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

### <a name="installation-via-direct-download---opensuse-422"></a>透過直接下載安裝 - OpenSUSE 42.2

將[版本][]頁面上的 RPM 套件 `powershell-6.0.0-1.rhel.7.x86_64.rpm` 下載到 OpenSUSE 電腦：

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

您也可以不使用下載的中繼步驟來安裝 RPM：

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a>解除安裝 - OpenSUSE 42.2

```sh
sudo zypper remove powershell
```

## <a name="fedora-25"></a>Fedora 25

### <a name="installation-via-package-repository-preferred---fedora-25"></a>透過套件存放庫安裝 (慣用) - Fedora 25

PowerShell Core for Linux 會發佈到官方 Microsoft 存放庫進行簡易安裝 (及更新)。

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

### <a name="installation-via-direct-download---fedora-25"></a>透過直接下載安裝 - Fedora 25

將[版本][]頁面上的 RPM 套件 `powershell-6.0.0-1.rhel.7.x86_64.rpm` 下載到 Fedora 電腦：

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

然後在終端機上執行下列作業：

```sh
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

您也可以不使用下載的中繼步驟來安裝 RPM：

```sh
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-25"></a>解除安裝 - Fedora 25

```sh
sudo dnf remove powershell
```

## <a name="fedora-26"></a>Fedora 26

### <a name="installation-via-package-repository-preferred---fedora-26"></a>透過套件存放庫安裝 (慣用) - Fedora 26

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

### <a name="installation-via-direct-download---fedora-26"></a>透過直接下載安裝 - Fedora 26

將[版本][]頁面上的 RPM 套件 `powershell-6.0.0-1.rhel.7.x86_64.rpm` 下載到 Fedora 電腦：

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

然後在終端機上執行下列作業：

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

您也可以不使用下載的中繼步驟來安裝 RPM：

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-26"></a>解除安裝 - Fedora 26

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a>Arch Linux

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

使用最新的 Linux 發行版本，將[版本][]頁面上的 AppImage `powershell-6.0.0-x86_64.AppImage` 下載到 Linux 電腦。

然後在終端機上執行下列作業：

```bash
chmod a+x powershell-6.0.0-x86_64.AppImage
./powershell-6.0.0-x86_64.AppImage
```

[AppImage][] 讓您不用安裝就可執行 PowerShell。 它是將 PowerShell 及其相依性 (包括.NET Core 系統相依性) 組合成一個緊密套件的可攜式應用程式。 此套件運作不受使用者的 Linux 發行版本影響，且是單一的二進位檔。

[appimage]: http://appimage.org/

## <a name="macos-1012"></a>macOS 10.12

### <a name="installation-via-homebrew-preferred---macos-1012"></a>透過 Homebrew 安裝 (慣用) - macOS 10.12

[Homebrew][ brew] 是 macOS 遺漏的套件管理員。 如果找不到 `brew` 命令，您需要遵循[指示][brew]安裝 Homebrew。

安裝好 Homebrew 之後，安裝 PowerShell 就很容易。 首先，安裝 [Homebrew-Cask][cask]，以便安裝更多套件：

```sh
brew tap caskroom/cask
```

現在，您可以安裝 PowerShell：

```sh
brew cask install powershell
```

發行新的 PowerShell 版本時，只要更新 Homebrew 的公式並升級 PowerShell 即可：

```sh
brew update
brew cask reinstall powershell
```

> 注意：因為 [Cask 的這個問題](https://github.com/caskroom/homebrew-cask/issues/29301)，目前必須重新安裝才能升級。

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download---macos-1012"></a>透過直接下載安裝 - macOS 10.12

使用 macOS 10.12，將[版本][]頁面上的 PKG 套件 `powershell-6.0.0-osx.10.12-x64.pkg` 下載至 macOS 電腦。

按兩下檔案依提示執行作業，或從終端機安裝：

```sh
sudo installer -pkg powershell-6.0.0-osx.10.12-x64.pkg -target /
```

### <a name="uninstallation---macos-1012"></a>解除安裝 - macOS 10.12

如果您使用 Homebrew 安裝 PowerShell，解除安裝很簡單：

```sh
brew cask uninstall powershell
```

如已透過直接下載安裝 PowerShell，即必須手動移除 PowerShell：

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

若要解除安裝其他的 PowerShell 路徑 (例如使用者設定檔路徑)，請參閱本文件下文中的[路徑][ paths]一節，使用 `sudo rm` 移除所要的路徑。 (注意：如果使用 Homebrew 安裝，此即非必要。)

[paths]:#paths

## <a name="kali"></a>Kali

### <a name="installation"></a>安裝

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a>在最新的 Kali (Kali GNU/Linux Rolling) 中不用安裝即可執行 PowerShell

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.0-x86_64.AppImage

# Start PowerShell
./powershell-6.0.0-x86_64.AppImage
```

### <a name="uninstallation---kali"></a>解除安裝 - Kali

```sh
sudo dpkg -r powershell-6.0.0-x86_64.AppImage
```

## <a name="raspbian"></a>Raspbian

目前只有 Raspbian Stretch 支援 PowerShell。

### <a name="installation"></a>安裝

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

### <a name="uninstallation---raspbian"></a>解除安裝 - Raspbian

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a>二進位封存

macOS 和 Linux 平台有 PowerShell 二進位 `tar.gz` 封存，以啟用進階的部署案例。

### <a name="dependencies"></a>相依性

在 Linux，PowerShell 為所有 Linux 發行版本建置可攜式二進位檔。
但 .NET Core 執行階段在不同的發行版本需要不同的相依性，所以 PowerShell 也一樣。

下圖顯示正式支援的不同 Linux 發行版本的 .NET Core 2.0 相依性。

| 作業系統                 | 相依性 |
| ------------------ | ------------ |
| Ubuntu 14.04       | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52 |
| Ubuntu 16.04       | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu55 |
| Ubuntu 17.04       | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu57 |
| Debian 8 (Jessie)  | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52 |
| Debian 9 (Stretch) | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.2、libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 <br> OpenSUSE 42.2 <br> Fedora 25 | libunwind、libcurl、openssl-libs、libicu |
| Fedora 26          | libunwind、libcurl、openssl-libs、libicu、compat-openssl10 |

為在未正式支援的 Linux 發行版本上部署 PowerShell 二進位檔，您需要在個別步驟中為目標作業系統安裝必要的相依性。 例如，[Amazon Linux dockerfile][amazon-dockerfile] 會先安裝相依性，再解壓縮 Linux `tar.gz` 封存。

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a>安裝 - 二進位封存

#### <a name="linux"></a>Linux

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

#### <a name="macos"></a>macOS

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

### <a name="uninstallation---binary-archives"></a>解除安裝 - 二進位封存

#### <a name="linux"></a>Linux

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

#### <a name="macos"></a>macOS

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

## <a name="paths"></a>路徑

* `$PSHOME` 是 `/opt/microsoft/powershell/6.0.0/`
* 會從 `~/.config/powershell/profile.ps1` 讀取使用者設定檔
* 會從 `$PSHOME/profile.ps1` 讀取預設設定檔
* 會從 `~/.local/share/powershell/Modules` 讀取使用者模組
* 會從 `/usr/local/share/powershell/Modules` 讀取共用的模組
* 會從 `$PSHOME/Modules` 讀取預設模組
* PSReadline 記錄會記錄在 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

設定檔會遵循 PowerShell 的每個主控件設定，讓預設主控件特定設定檔存在於相同位置的 `Microsoft.PowerShell_profile.ps1`。

在 Linux 及 macOS 上，遵循 [XDG 基底目錄規格][xdg-bds]。

請注意，因為 macOS 是 BSD 而非 `/opt` 的衍生項，所以使用的前置詞是 `/usr/local`。 因此，`$PSHOME` 是 `/usr/local/microsoft/powershell/6.0.0/`，而且符號連結放在 `/usr/local/bin/pwsh`。

[版本]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
