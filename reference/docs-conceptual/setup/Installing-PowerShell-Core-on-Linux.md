---
title: 在 Linux 上安裝 PowerShell Core
description: 在各種 Linux 發佈上安裝 PowerShell Core 的相關資訊
ms.date: 08/06/2018
ms.openlocfilehash: a20384c768113ed2313591cfa8c29eeadd94f80f
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225993"
---
# <a name="installing-powershell-core-on-linux"></a>在 Linux 上安裝 PowerShell Core

支援 [Ubuntu 14.04][u14]、[Ubuntu 16.04][u16]、[Ubuntu 18.04][u1804]、[Ubuntu 18.10][u1810]、[Debian 8][deb8]、[Debian 9][deb9]、[CentOS 7][cos]、[Red Hat Enterprise Linux (RHEL) 7][rhel7]、[openSUSE 42.3][opensuse]、[openSUSE Leap 15][opensuse]、[Fedora 27][fedora]、[Fedora 28][fedora] 與 [Arch Linux][arch]。

若是未正式支援的 Linux 發佈，您可以嘗試使用 [PowerShell Snap 套件][snap]。
您也可以直接使用 Linux [`tar.gz` 封存][tar]嘗試部署 PowerShell 二進位檔，但您需要根據個別步驟中的作業系統，設定必要的相依性。

GitHub [版本][]頁面上提供所有套件。
安裝套件之後，請從終端機執行 `pwsh`。

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-423
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a>安裝預覽版本

透過套件存放庫安裝 Linux 的 PowerShell Core Preview 版本時，套件名稱會從 `powershell` 變更為 `powershell-preview`。

透過直接下載的安裝不會變更，但檔案名稱除外。

下表是使用各種套件管理員安裝穩定和預覽套件的命令：

|發行版本|穩定命令 | 預覽命令 |
|---------------|---------------|-----------------|
| Ubuntu、Debian |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| CentOS、RedHat |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| Fedora   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a>Ubuntu 14.04

### <a name="installation-via-package-repository---ubuntu-1404"></a>透過套件存放庫安裝 - Ubuntu 14.04

PowerShell Core for Linux 會發佈到套件存放庫進行簡易安裝 (及更新)。
這是慣用方法。

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

以超級使用者的身分，註冊 Microsoft 存放庫。
從那時起，您只需要使用`sudo apt-get upgrade powershell`來更新安裝。

### <a name="installation-via-direct-download---ubuntu-1404"></a>透過直接下載安裝 - Ubuntu 14.04

將 Debian 套件 `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`
從[版本][]頁面下載到 Ubuntu 電腦。

然後在終端機上執行下列作業：

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.14.04_amd64.deb
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

以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。

### <a name="installation-via-direct-download---ubuntu-1604"></a>透過直接下載安裝 - Ubuntu 16.04

將 Debian 套件 `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`
從[版本][]頁面下載到 Ubuntu 電腦。

然後在終端機上執行下列作業：

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> `dpkg -i` 命令因相依性不相符而失敗。
> 下一個命令 `apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。

### <a name="uninstallation---ubuntu-1604"></a>解除安裝 - Ubuntu 16.04

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

以超級使用者身分註冊過 Microsoft 存放庫一次之後，以後只需要使用 `sudo apt-get upgrade powershell` 更新它。

### <a name="installation-via-direct-download---ubuntu-1804"></a>透過直接下載安裝 - Ubuntu 18.04

將 Debian 套件 `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`
從[版本][]頁面下載到 Ubuntu 電腦。

然後在終端機上執行下列作業：

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> `dpkg -i` 命令因相依性不相符而失敗。
> 下一個命令 `apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。

### <a name="uninstallation---ubuntu-1804"></a>解除安裝 - Ubuntu 18.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a>Ubuntu 18.10

> [!NOTE]
> 在 `6.1.0-preview.3` 之後已新增 Ubuntu 18.10 支援。
> 由於 18.10 是 Daily Build，因此只有社群支援。

18.10 的安裝透過 `snapd`提供支援。 如需完整指示，請參閱 [Snap 套件][snap]；

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

將 Debian 套件 `powershell_6.1.0-1.debian.8_amd64.deb`
從[版本][]頁面下載到 Debian 電腦。

然後在終端機上執行下列作業：

```sh
sudo dpkg -i powershell_6.1.0-1.debian.8_amd64.deb
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

將 Debian 套件 `powershell_6.1.0-1.debian.9_amd64.deb`
從[版本][]頁面下載到 Debian 電腦。

然後在終端機上執行下列作業：

```sh
sudo dpkg -i powershell_6.1.0-1.debian.9_amd64.deb
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

使用 [CentOS 7][]，將 RPM 套件 `powershell-6.1.0-1.rhel.7.x86_64.rpm`
從[版本][]頁面下載到 CentOS 電腦。

然後在終端機上執行下列作業：

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

您也可以不使用下載的中繼步驟來安裝 RPM：

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
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

將 RPM 套件 `powershell-6.1.0-1.rhel.7.x86_64.rpm`
從[版本][]頁面下載到 Red Hat Enterprise Linux 電腦。

然後在終端機上執行下列作業：

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

您也可以不使用下載的中繼步驟來安裝 RPM：

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>解除安裝 - Red Hat Enterprise Linux (RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a>openSUSE

### <a name="installation---opensuse-423"></a>安裝 - openSUSE 42.3

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

### <a name="installation---opensuse-leap-15"></a>安裝 - openSUSE Leap 15

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a>解除安裝 - openSUSE 42.3、openSUSE Leap 15

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
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

將 RPM 套件 `powershell-6.1.0-1.rhel.7.x86_64.rpm`
從[版本][]頁面下載到 Fedora 電腦。

然後在終端機上執行下列作業：

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

您也可以不使用下載的中繼步驟來安裝 RPM：

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
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

## <a name="snap-package"></a>Snap 套件

### <a name="getting-snapd"></a>取得 snapd

必須有 `snapd` 才能執行 Snap。
請使用[這些指示](https://docs.snapcraft.io/core/install)確認您已安裝 `snapd`。

### <a name="installation-via-snap"></a>透過 Snap 安裝

適用於 Linux 的 PowerShell Core 會發佈到 [Snap 市集](https://snapcraft.io/store)以供輕鬆安裝 (及更新)。
這是慣用方法。

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

若要安裝預覽版，請使用下列方法。

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

在安裝之後，Snap 會自動升級，不過您也可以使用 `sudo snap refresh powershell` 或 `sudo snap refresh powershell-preview` 觸發升級。

### <a name="uninstallation"></a>解除安裝

```sh
sudo snap remove powershell
```

或

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a>Kali

### <a name="installation---kali"></a>安裝 - Kali

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

### <a name="uninstallation---kali"></a>解除安裝 - Kali

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a>Raspbian

> [!NOTE]
> Raspbian 支援為實驗性。

目前只有 Raspbian Stretch 支援 PowerShell。

另外，CoreCLR (和 PowerShell Core) 僅適用於 Pi 2 和 Pi 3 裝置，因為像 [Pi Zero](https://github.com/dotnet/coreclr/issues/10605) 此類的其他裝置，它們的處理器不被支援。

下載 [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/)並 遵循[安裝指示](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)來把它安裝到您的 Pi。

### <a name="installation---raspbian"></a>安裝 - Raspbian

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
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 | libunwind、libcurl、openssl-libs、libicu |
| openSUSE 42.3 | libcurl4、libopenssl1_0_0、libicu52_1 |
| openSUSE Leap 15 | libcurl4、libopenssl1_0_0、libicu60_2 |
| Fedora 27 <br> Fedora 28 | libunwind、libcurl、openssl-libs、libicu、compat-openssl10 |

若要在未正式支援的 Linux 發行版本上部署 PowerShell 二進位檔，您需要在個別步驟中為目標作業系統安裝必要的相依性。
例如，[Amazon Linux dockerfile][amazon-dockerfile] 會先安裝相依性，再解壓縮 Linux `tar.gz` 封存。

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a>安裝 - 二進位封存

#### <a name="linux"></a>Linux

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

### <a name="uninstalling-binary-archives"></a>解除安裝二進位封存

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a>路徑

* `$PSHOME` 是 `/opt/microsoft/powershell/6.1.0/`
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
