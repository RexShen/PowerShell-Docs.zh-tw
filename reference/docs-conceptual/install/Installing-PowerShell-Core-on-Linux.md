---
title: 在 Linux 上安裝 PowerShell
description: 在各種 Linux 發行版本上安裝 PowerShell Core 的相關資訊
ms.date: 07/30/2020
ms.openlocfilehash: ce69f75416eb326e38d42991a4ae85a3a7298c5d
ms.sourcegitcommit: 79d430fe48ad77a058f42b6bc9955d21b657987e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2020
ms.locfileid: "87441774"
---
# <a name="installing-powershell-on-linux"></a>在 Linux 上安裝 PowerShell

GitHub [發行][]頁面上提供所有套件。 安裝套件之後，請從終端機執行 `pwsh`。 若您已安裝[預覽版](#installing-preview-releases)，請執行 `pwsh-preview`。

> [!NOTE]
> PowerShell 7 是會移除 PowerShell Core 6.x 的就地升級。
>
> `/usr/local/microsoft/powershell/6` 資料夾已由 `/usr/local/microsoft/powershell/7` 取代。
>
> 如果您需要與 PowerShell 7 並存執行 PowerShell 6，請使用[二進位封存](#binary-archives)方法來重新安裝 PowerShell 6。

針對未正式支援的 Linux 發佈，您可以嘗試使用 [PowerShell Snap 套件][snap]來安裝 PowerShell。 您也可以直接使用 Linux [`tar.gz` 封存][tar]來嘗試部署 PowerShell 二進位檔，但您需要根據個別步驟中作業系統設定必要的相依性。

[snap]: #snap-package
[tar]: #binary-archives

正式支援的版本

- Ubuntu 16.04
- Ubuntu 18.04
- Debian 8
- Debian 9
- Debian 10
- Alpine 3.9 與 3.10
- CentOS 7
- Red Hat Enterprise Linux (RHEL) 7
- Fedora 28
- Fedora 29
- Fedora 30
- openSUSE 42.3
- openSUSE Leap 15

社群支援的版本

- Ubuntu 18.10
- Ubuntu 19.04
- Arch Linux
- Kali
- Raspbian (實驗性)

替代安裝方法

- Snap 套件
- 二進位封存
- .NET 全域工具

目前不支援

- Ubuntu 20.04

> [!NOTE]
> PowerShell 僅支援 .NET 支援的發行版本。 如需支援的發行版本清單，請參閱 [.NET Core 版本資訊][distros]。 如果這裡沒有列出 .NET 支援的發行版本，則可要求新增對該發行版本的支援。 請使用[發行版本支援要求][]範本來提出要求。

## <a name="ubuntu-1604"></a>Ubuntu 16.04

### <a name="installation-via-package-repository---ubuntu-1604"></a>透過套件存放庫安裝 - Ubuntu 16.04

適用於 Linux 的 PowerShell 會發佈到套件存放庫，以供輕鬆安裝及更新。

慣用的方法如下所示：

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

以超級使用者的身分，註冊 Microsoft 存放庫一次。 註冊之後，您可以使用 `sudo apt-get install powershell` 來更新 PowerShell。

### <a name="installation-via-direct-download---ubuntu-1604"></a>透過直接下載安裝 - Ubuntu 16.04

將[發行][]頁面上的 Debian 套件 `powershell-lts_7.0.3-1.ubuntu.16.04_amd64.deb` 下載至 Ubuntu 電腦。

然後，在終端機中執行下列命令：

```sh
sudo dpkg -i powershell-lts_7.0.3-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> `dpkg -i` 命令因相依性不相符而失敗。 下一個命令 `apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。

### <a name="uninstallation---ubuntu-1604"></a>解除安裝 - Ubuntu 16.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a>Ubuntu 18.04

### <a name="installation-via-package-repository---ubuntu-1804"></a>透過套件存放庫安裝 - Ubuntu 18.04

適用於 Linux 的 PowerShell 會發佈到套件存放庫，以供輕鬆安裝及更新。

慣用的方法如下所示：

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

以超級使用者的身分，註冊 Microsoft 存放庫一次。 註冊之後，您可以使用 `sudo apt-get install powershell` 來更新 PowerShell。

### <a name="installation-via-direct-download---ubuntu-1804"></a>透過直接下載安裝 - Ubuntu 18.04

將[發行][]頁面上的 Debian 套件 `powershell-lts_7.0.3-1.ubuntu.18.04_amd64.deb` 下載至 Ubuntu 電腦。

然後，在終端機中執行下列命令：

```sh
sudo dpkg -i powershell-lts_7.0.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> `dpkg -i` 命令因相依性不相符而失敗。 下一個命令 `apt-get install -f` 會解決這些問題，然後完成 PowerShell 套件的設定。

### <a name="uninstallation---ubuntu-1804"></a>解除安裝 - Ubuntu 18.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a>Ubuntu 18.10

安裝由 `snapd` 支援。 如需指示，請參閱 [Snap 套件][snap]。

> [!NOTE]
> Ubuntu 18.10 是[由社群支援](../powershell-support-lifecycle.md)的[過渡版本](https://www.ubuntu.com/about/release-cycle) (英文)。

## <a name="ubuntu-1904"></a>Ubuntu 19.04

安裝由 `snapd` 支援。 如需指示，請參閱 [Snap 套件][snap]。

> [!NOTE]
> 因為 Ubuntu 19.04 是[由社群支援](../powershell-support-lifecycle.md)的[過渡版本](https://www.ubuntu.com/about/release-cycle) \(英文\)。

## <a name="ubuntu-2004"></a>Ubuntu 20.04

Ubuntu 20.04 為 LTS 版本。 PowerShell 目前不支援此版本。 PowerShell 7.1 版正考慮增加對此版本的支援。 如果您想支援 Ubuntu 20.04.，請附議此[要求](https://github.com/PowerShell/PowerShell/issues/12626)。

## <a name="debian-8"></a>Debian 8

### <a name="installation-via-package-repository---debian-8"></a>透過套件存放庫安裝 - Debian 8

適用於 Linux 的 PowerShell 會發佈到套件存放庫，以供輕鬆安裝及更新。

慣用的方法如下所示：

```sh
# Install system components
sudo apt-get update
sudo apt-get install -y curl apt-transport-https

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

以超級使用者的身分，註冊 Microsoft 存放庫一次。 註冊之後，您可以使用 `sudo apt-get install powershell` 來更新 PowerShell。

## <a name="debian-9"></a>Debian 9

### <a name="installation-via-package-repository---debian-9"></a>透過套件存放庫安裝 - Debian 9

適用於 Linux 的 PowerShell 會發佈到套件存放庫，以供輕鬆安裝及更新。

慣用的方法如下所示：

```sh
# Install system components
sudo apt-get update
sudo apt-get install -y curl gnupg apt-transport-https

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

以超級使用者的身分，註冊 Microsoft 存放庫一次。 註冊之後，您可以使用 `sudo apt-get install powershell` 來更新 PowerShell。

### <a name="installation-via-direct-download---debian-9"></a>透過直接下載安裝 - Debian 9

將[發行][]頁面上的 Debian 套件 `powershell-lts_7.0.3-1.debian.9_amd64.deb` 下載至 Debian 電腦。

然後，在終端機中執行下列命令：

```sh
sudo dpkg -i powershell-lts_7.0.3-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a>解除安裝 - Debian 9

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a>Debian 10

> [!NOTE]
> 只有 PowerShell Core 7.0 才支援 Debian 10。

### <a name="installation-via-package-repository---debian-10"></a>透過套件存放庫安裝 - Debian 10

適用於 Linux 的 PowerShell 會發佈到套件存放庫，以供輕鬆安裝及更新。

慣用的方法如下所示：

```sh
# Download the Microsoft repository GPG keys
wget https://packages.microsoft.com/config/debian/10/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---debian-10"></a>透過直接下載安裝 - Debian 10

將[發行][]頁面上的 tar.gz 套件 `powershell-7.0.3-linux-x64.tar.gz` 下載到 Debian 電腦：

然後，在終端機中執行下列命令：

```sh
sudo apt-get update
# install the requirements
sudo apt-get install -y \
        less \
        locales \
        ca-certificates \
        libicu63 \
        libssl1.1 \
        libc6 \
        libgcc1 \
        libgssapi-krb5-2 \
        liblttng-ust0 \
        libstdc++6 \
        zlib1g \
        curl

# Download the powershell '.tar.gz' archive
curl -L  https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-7.0.3-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

## <a name="alpine-39-and-310"></a>Alpine 3.9 與 3.10

> [!NOTE]
> 只有 PowerShell 7.0 與更新版本才支援 Alpine 3.9 與 3.10。

### <a name="installation-via-direct-download---alpine-39-and-310"></a>透過直接下載安裝 - Alpine 3.9 與 3.10

將[發行][]頁面上的 tar.gz 套件 `powershell-7.0.3-linux-alpine-x64.tar.gz` 下載到 Alpine 電腦：

然後，在終端機中執行下列命令：

```sh
# install the requirements
sudo apk add --no-cache \
    ca-certificates \
    less \
    ncurses-terminfo-base \
    krb5-libs \
    libgcc \
    libintl \
    libssl1.1 \
    libstdc++ \
    tzdata \
    userspace-rcu \
    zlib \
    icu-libs \
    curl

sudo apk -X https://dl-cdn.alpinelinux.org/alpine/edge/main add --no-cache \
    lttng-ust

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-7.0.3-linux-alpine-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

## <a name="centos-7"></a>CentOS 7

> [!NOTE]
> 此套件也適用於 Oracle Linux 7。

### <a name="installation-via-package-repository-preferred---centos-7"></a>透過套件存放庫安裝 (慣用) - CentOS 7

適用於 Linux 的 PowerShell 會發佈到官方 Microsoft 存放庫，以供輕鬆安裝及更新。

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

以超級使用者的身分，註冊 Microsoft 存放庫一次。 註冊之後，您可以使用 `sudo yum update powershell` 來更新 PowerShell。

### <a name="installation-via-direct-download---centos-7"></a>透過直接下載安裝 - CentOS 7

使用 [CentOS 7][]，將[發行][]頁面上的 RPM 套件 `powershell-lts-7.0.3-1.rhel.7.x86_64.rpm` 下載至 CentOS 電腦。

然後，在終端機中執行下列命令：

```sh
sudo yum install powershell-lts-7.0.3-1.rhel.7.x86_64.rpm
```

無需下載的中繼步驟便可安裝 RPM：

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-lts-7.0.3-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a>解除安裝 - CentOS 7

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a>透過套件存放庫安裝 (慣用) - Red Hat Enterprise Linux (RHEL) 7

適用於 Linux 的 PowerShell 會發佈到官方 Microsoft 存放庫，以供輕鬆安裝及更新。

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

以超級使用者的身分，註冊 Microsoft 存放庫一次。 註冊之後，您可以使用 `sudo yum update powershell` 來更新 PowerShell。

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a>透過直接下載安裝 - Red Hat Enterprise Linux (RHEL) 7

將[發行][]頁面上的 RPM 套件 `powershell-lts-7.0.3-1.rhel.7.x86_64.rpm` 下載到 Red Hat Enterprise Linux 電腦。

然後，在終端機中執行下列命令：

```sh
sudo yum install powershell-lts-7.0.3-1.rhel.7.x86_64.rpm
```

無需下載的中繼步驟便可安裝 RPM：

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-lts-7.0.3-1.rhel.7.x86_64.rpm
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
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-7.0.3-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a>安裝 - openSUSE Leap 15

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-7.0.3-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a>解除安裝 - openSUSE 42.3、openSUSE Leap 15

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a>Fedora

> [!NOTE]
> 只有 PowerShell Core 6.1 與更新版本才支援 Fedora 28。

> [!NOTE]
> 只有 PowerShell 7.0 與更新版本才支援 Fedora 29 與 30。

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a>透過套件存放庫安裝 (慣用) - Fedora 28、29 與 30

適用於 Linux 的 PowerShell 會發佈到官方 Microsoft 存放庫，以供輕鬆安裝及更新。

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf check-update

# Install a system component
sudo dnf install compat-openssl10

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a>透過直接下載安裝 - Fedora 28、29 與 30

將[發行][]頁面上的 RPM 套件 `powershell-7.0.3-1.rhel.7.x86_64.rpm` 下載到 Fedora 電腦。

然後，在終端機中執行下列命令：

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-7.0.3-1.rhel.7.x86_64.rpm
```

無需下載的中繼步驟便可安裝 RPM：

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-7.0.3-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a>解除安裝 - Fedora 28、29 與 30

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a>Arch Linux

> [!NOTE]
> 「架構」支援並非由 Microsoft 正式支援，而是由社群維護。

PowerShell 可從 [Arch Linux][] 使用者存放庫 (AUR) 取得。

- 可以使用[最新的標記版本][arch-release]編譯
- 可以從[主機的最新認可][arch-git]編譯
- 可以使用[最新版本的二進位檔][arch-bin]安裝

AUR 中的套件由社群維護，沒有官方支援。

如需從 AUR 安裝套件的詳細資訊，請參閱 [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) 或[在 Docker 中使用 PowerShell](powershell-in-docker.md)。

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a>Snap 套件

### <a name="getting-snapd"></a>取得 snapd

必須有 `snapd` 才能執行 Snap。 請使用[這些指示](https://docs.snapcraft.io/core/install)確認您已安裝 `snapd`。

### <a name="installation-via-snap"></a>透過 Snap 安裝

適用於 Linux 的 PowerShell 會發佈到 [Snap Store](https://snapcraft.io/store)，以供輕鬆安裝及更新。

慣用的方法如下所示：

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

若要安裝預覽版，請使用下列方法：

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

安裝之後，Snap 將會自動升級。 您可以使用 `sudo snap refresh powershell` 或 `sudo snap refresh powershell-preview` 觸發升級。

### <a name="uninstallation"></a>解除安裝

```sh
sudo snap remove powershell
```

或

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a>Kali

> [!NOTE]
> Kali 支援並非由 Microsoft 正式支援，而是由社群維護。

### <a name="installation---kali"></a>安裝 - Kali

```sh
# Install PowerShell package
apt update && apt -y install powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a>解除安裝 - Kali

```sh
# Uninstall PowerShell package
apt -y remove powershell
```

## <a name="raspbian"></a>Raspbian

> [!NOTE]
> Raspbian 支援為實驗性。

目前只有 Raspbian Stretch 支援 PowerShell。

CoreCLR 與 PowerShell 僅適用於 Pi 2 與 Pi 3 裝置，因為像 [Pi Zero](https://github.com/dotnet/coreclr/issues/10605) \(英文\) 這類的其他裝置，其處理器不受支援。

下載 [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) 並遵循[安裝指示](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)來把它安裝到您的 Pi。

### <a name="installation---raspbian"></a>安裝 - Raspbian

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
wget https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-7.0.3-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-7.0.3-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

或者，您可以建立一個符號連結來啟動 PowerShell，而無需指定 `pwsh` 二進位檔案路徑。

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a>解除安裝 - Raspbian

```sh
rm -rf ~/powershell
```

## <a name="installing-preview-releases"></a>安裝預覽版本

透過套件存放庫安裝 Linux 的 PowerShell Preview 版本時，套件名稱會從 `powershell` 變更為 `powershell-preview`。

透過直接下載的安裝不會變更，但檔案名稱除外。

下表包含使用各種套件管理員安裝穩定和預覽套件的命令：

| 發行版本 |            穩定命令            |               預覽命令                |
| --------------- | ------------------------------------ | -------------------------------------------- |
| Ubuntu、Debian  | `sudo apt-get install -y powershell` | `sudo apt-get install -y powershell-preview` |
| CentOS、RedHat  | `sudo yum install -y powershell`     | `sudo yum install -y powershell-preview`     |
| Fedora          | `sudo dnf install -y powershell`     | `sudo dnf install -y powershell-preview`     |

## <a name="install-as-a-net-global-tool"></a>安裝為 .NET 全域工具

如果您已安裝 [.NET Core SDK](/dotnet/core/sdk)，就可以輕鬆地將 PowerShell 安裝為 [.NET 全域工具](/dotnet/core/tools/global-tools)。

```
dotnet tool install --global PowerShell
```

Dotnet 工具安裝程式會將 `~/.dotnet/tools` 新增至您的 `PATH` 環境變數。 不過，目前執行的殼層沒有更新的 `PATH`。 您應該能夠透過輸入 `pwsh`，以從新的殼層啟動 PowerShell。

## <a name="binary-archives"></a>二進位封存

Linux 平台有 PowerShell 二進位 `tar.gz` 封存，以啟用進階的部署案例。

### <a name="dependencies"></a>相依性

PowerShell 會為所有 Linux 發行版本建置可攜式二進位檔。 但 .NET Core 執行階段在不同的發行版本需要不同的相依性，PowerShell 也一樣。

下圖顯示不同 Linux 發行版本上，正式支援的 .NET Core 2.0 相依性。

| OS                 | 相依性 |
| ------------------ | ------------ |
| Ubuntu 16.04       | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu55 |
| Ubuntu 17.10       | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu57 |
| Ubuntu 18.04       | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu60 |
| Debian 8 (Jessie)  | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.0、libicu52 |
| Debian 9 (Stretch) | libc6、libgcc1、libgssapi-krb5-2、liblttng-ust0、libstdc++6、 <br> libcurl3、libunwind8、libuuid1、zlib1g、libssl1.0.2、libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 | libunwind、libcurl、openssl-libs、libicu |
| openSUSE 42.3 | libcurl4、libopenssl1_0_0、libicu52_1 |
| openSUSE Leap 15 | libcurl4、libopenssl1_0_0、libicu60_2 |
| Fedora 27 <br> Fedora 28 | libunwind、libcurl、openssl-libs、libicu、compat-openssl10 |

若要在未正式支援的 Linux 發行版本上部署 PowerShell 二進位檔，您需要在個別步驟中為目標作業系統安裝必要的相依性。 例如，[Amazon Linux dockerfile][amazon-dockerfile] 會先安裝相依性，再解壓縮 Linux `tar.gz` 封存。

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a>安裝 - 二進位封存

#### <a name="linux"></a>Linux

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-7.0.3-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a>解除安裝二進位封存

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a>路徑

- `$PSHOME` 是 `/opt/microsoft/powershell/7/`
- 會從 `~/.config/powershell/profile.ps1` 讀取使用者設定檔
- 會從 `$PSHOME/profile.ps1` 讀取預設設定檔
- 會從 `~/.local/share/powershell/Modules` 讀取使用者模組
- 會從 `/usr/local/share/powershell/Modules` 讀取共用的模組
- 會從 `$PSHOME/Modules` 讀取預設模組
- PSReadline 記錄會記錄在 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

設定檔會遵循 PowerShell 的每個主控件設定，讓預設主控件特定設定檔存在於相同位置的 `Microsoft.PowerShell_profile.ps1`。

PowerShell 遵循 Linux 上的 [XDG 基底目錄規格][xdg-bds]。

## <a name="installation-support"></a>安裝支援

Microsoft 支援此文件中的安裝方法。 其他來源可能會提供其他安裝方法。 雖然那些工具與方法都有用，但 Microsoft 無法支援那些方法。

<!-- link references -->
[發行]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
[distros]: https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md#linux
[發行版本支援要求]: https://github.com/PowerShell/PowerShell/issues/new?assignees=&labels=Distribution-Request&template=Distribution_Request.md&title=Distribution+Support+Request
