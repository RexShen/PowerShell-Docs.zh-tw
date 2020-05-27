---
title: 在 macOS 上安裝 PowerShell
description: 在 macOS 上安裝 PowerShell 的相關資訊
ms.date: 05/21/2020
ms.openlocfilehash: 32b3ebf3eb4017af41fc1a062f2f0a2e08629a58
ms.sourcegitcommit: fd6a33b9fac973b3554fecfea7f51475e650a606
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83791465"
---
# <a name="installing-powershell-on-macos"></a>在 macOS 上安裝 PowerShell

PowerShell 支援 macOS 10.12 與更高版本。
GitHub [版本][]頁面上提供所有套件。
安裝套件之後，請從終端機執行 `pwsh`。

> [!NOTE]
> PowerShell 7 是會移除 PowerShell Core 6.x 的就地升級。
>
> `/usr/local/microsoft/powershell/6` 資料夾已由 `/usr/local/microsoft/powershell/7` 取代。
>
> 如果您需要與 PowerShell 7 並存執行 PowerShell 6，請使用[二進位封存](#binary-archives)方法來重新安裝 PowerShell 6。

## <a name="about-brew"></a>關於 Brew

[Homebrew][brew] 是 macOS 首選的套件管理員。 如果找不到 `brew` 命令，您需要遵循[指示][brew]安裝 Homebrew。 或者，您也可透過[直接下載](#installation-via-direct-download)或[二進位封存](#binary-archives)來安裝 PowerShell。

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a>在 macOS 10.12 或更高版本上透過 Homebrew 安裝最新的穩定版本

如需 Brew 的相關資訊，請參閱[關於 Brew](#about-brew)。

現在，您可以安裝 PowerShell：

```sh
brew cask install powershell
```

最後，確認您的安裝可以正常執行：

```sh
pwsh
```

當新的 PowerShell 版本發行時，請更新 Homebrew 的公式並升級 PowerShell：

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> 您可以從 PowerShell (pwsh) 主機內呼叫上述命令，但必須結束並重新啟動 PowerShell 殼層，才能完成升級並重新整理 `$PSVersionTable` 中顯示的值。

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a>在 macOS 10.12 或更高版本上透過 Homebrew 安裝最新的預覽版本

如需 Brew 的相關資訊，請參閱[關於 Brew](#about-brew)。

安裝 Homebrew 之後，您可以安裝 PowerShell。
首先，安裝 [Cask-Versions][cask-versions] 套件，它可讓您安裝 Cask 套件的替代版本：

```sh
brew tap homebrew/cask-versions
```

現在，您可以安裝 PowerShell：

```sh
brew cask install powershell-preview
```

最後，確認您的安裝可以正常執行：

```sh
pwsh-preview
```

當新的 PowerShell 版本發行時，請更新 Homebrew 的公式並升級 PowerShell：

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> 上述命令可從 PowerShell (pwsh) 主機內呼叫，但 PowerShell 殼層必須結束並重新啟動，才能完成升級。
> 並重新整理 `$PSVersionTable` 中顯示的值。

## <a name="installation-via-direct-download"></a>透過直接下載來安裝

將 PKG 套件 `powershell-lts-7.0.1-osx-x64.pkg`
從[版本][]頁面下載到您的 macOS 電腦。

您可以按兩下檔案並依照提示執行作業，或從終端機安裝：

```sh
sudo installer -pkg powershell-lts-7.0.1-osx-x64.pkg -target /
```

安裝 [OpenSSL](#install-openssl)。 PowerShell 遠端執行功能與 CIM 作業需要 OpenSSL。

## <a name="install-as-a-net-global-tool"></a>安裝為 .NET 全域工具

如果您已安裝 [.NET Core SDK](/dotnet/core/sdk)，就可以輕鬆地將 PowerShell 安裝為 [.NET 全域工具](/dotnet/core/tools/global-tools)。

```
dotnet tool install --global PowerShell
```

Dotnet 工具安裝程式會將 `~/.dotnet/tools` 新增至您的 `PATH` 環境變數。 不過，目前執行的殼層沒有更新的 `PATH`。 您應該能夠透過輸入 `pwsh`，以從新的殼層啟動 PowerShell。

## <a name="binary-archives"></a>二進位封存

macOS 平台有 PowerShell 二進位 `tar.gz` 封存，以啟用進階的部署案例。

### <a name="installing-binary-archives-on-macos"></a>解除安裝 macOS 上的二進位封存

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.0.1/powershell-7.0.1-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/7.0.1

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/7.0.1

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/7.0.1/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/7.0.1/pwsh /usr/local/bin/pwsh
```

安裝 [OpenSSL](#install-openssl)。 PowerShell 遠端執行功能與 CIM 作業需要 OpenSSL。

## <a name="installing-dependencies"></a>安裝相依性

### <a name="install-xcode-command-line-tools"></a>安裝 XCode 命令列工具

```sh
xcode-select --install
```

### <a name="install-openssl"></a>安裝 OpenSSL

PowerShell 遠端執行功能與 CIM 作業需要 OpenSSL。 您可以透過 MacPorts 來安裝。

#### <a name="install-openssl-via-macports"></a>透過 MacPorts 安裝 OpenSSL

1. 安裝 [XCode 命令列工具](#install-xcode-command-line-tools)。
1. 安裝 MacPorts。
   若需要指示，請參閱[安裝指南](https://guide.macports.org/chunked/installing.macports.html) \(英文\)。
1. 透過執行 `sudo port selfupdate` 來更新 MacPorts。
1. 透過執行 `sudo port upgrade outdated` 來升級 MacPorts 套件。
1. 透過執行 `sudo port install openssl10` 以安裝 OpenSSL。
1. 連結程式庫，以供 PowerShell 使用它們：

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib/openssl-1.0 /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell"></a>解除安裝 PowerShell

如果您使用 Homebrew 安裝 PowerShell，請使用下列命令解除安裝：

```sh
brew cask uninstall powershell
```

如已透過直接下載安裝 PowerShell，即必須手動移除 PowerShell：

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

若要移除其他的 PowerShell 路徑，請參閱此文件中的[路徑](#paths)一節，並使用 `sudo rm` 移除路徑。

> [!NOTE]
> 如果使用 Homebrew 安裝，此即非必要。

## <a name="paths"></a>路徑

* `$PSHOME` 是 `/usr/local/microsoft/powershell/7.0.1/`
* 會從 `~/.config/powershell/profile.ps1` 讀取使用者設定檔
* 會從 `$PSHOME/profile.ps1` 讀取預設設定檔
* 會從 `~/.local/share/powershell/Modules` 讀取使用者模組
* 會從 `/usr/local/share/powershell/Modules` 讀取共用的模組
* 會從 `$PSHOME/Modules` 讀取預設模組
* PSReadline 記錄會記錄在 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

設定檔會採用 PowerShell 的每個主機設定。
因此預設主機特定設定檔便會存在於相同位置的 `Microsoft.PowerShell_profile.ps1`。

PowerShell 遵循 macOS 上的 [XDG 基底目錄規格][xdg-bds]。

因為 macOS 是 BSD 的衍生項，所以使用的前置詞是 `/usr/local` 而非 `/opt`。
因此，`$PSHOME` 是 `/usr/local/microsoft/powershell/7.0.1/`，而符號連結放置在 `/usr/local/bin/pwsh`。

## <a name="additional-resources"></a>其他資源

* [Homebrew Web][brew]
* [Homebrew Github 存放庫][GitHub]
* [Homebrew-Cask][cask]

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[版本]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
