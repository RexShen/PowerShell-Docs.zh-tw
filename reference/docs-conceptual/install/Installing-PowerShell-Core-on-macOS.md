---
title: 在 macOS 上安裝 PowerShell
description: 在 macOS 上安裝 PowerShell 的相關資訊
ms.date: 11/11/2020
ms.openlocfilehash: 1ce96e993d8fc87edd93fca840ede250d5632577
ms.sourcegitcommit: 3ab2951a5460a39ca5fb3d25ffcb1d8868f4e011
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2020
ms.locfileid: "96535095"
---
# <a name="installing-powershell-on-macos"></a>在 macOS 上安裝 PowerShell

PowerShell 7.0 或更高版本需要 macOS 10.13 與更高版本。 GitHub [發行][]頁面上提供所有套件。 安裝套件之後，請從終端機執行 `pwsh`。

> [!NOTE]
> PowerShell 7.1 是會移除 PowerShell Core 6.x 與 7.0 的就地升級。
>
> `/usr/local/microsoft/powershell/6` 資料夾已由 `/usr/local/microsoft/powershell/7` 取代。
>
> 如果您需要與 PowerShell 7.1 並存執行較舊版本的 PowerShell Core，請使用[二進位封存](#binary-archives)方法來安裝所需版本。

有幾種方式可在 macOS 上安裝 PowerShell。 請選擇下列其中一個方法：

- 使用 Homebrew 安裝。 Homebrew 是 macOS 首選的套件管理員。
- 透過[直接下載](#installation-via-direct-download)安裝 PowerShell
- 從[二進位封存](#binary-archives)進行安裝。

安裝 PowerShell 之後，會需要一併安裝 [OpenSSL](#installing-dependencies)。 PowerShell 遠端執行功能與 CIM 作業需要 OpenSSL。

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1013-or-higher"></a>在 macOS 10.13 或更新版本上透過 Homebrew 安裝最新的穩定版本

如果找不到 `brew` 命令，您需要遵循[指示][brew]安裝 Homebrew。

現在，您可以安裝 PowerShell：

```sh
brew install --cask powershell
```

最後，確認您的安裝可以正常執行：

```sh
pwsh
```

當新的 PowerShell 版本發行時，請更新 Homebrew 的公式並升級 PowerShell：

```sh
brew update
brew upgrade powershell --cask
```

> [!NOTE]
> 您可以從 PowerShell (pwsh) 主機內呼叫上述命令，但必須結束並重新啟動 PowerShell 殼層，才能完成升級並重新整理 `$PSVersionTable` 中顯示的值。

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1013-or-higher"></a>在 macOS 10.13 或更新版本上透過 Homebrew 安裝最新的預覽版本

安裝 Homebrew 之後，您可以安裝 PowerShell。 首先，安裝 [Cask-Versions][cask-versions] 套件，它可讓您安裝 Cask 套件的替代版本：

```sh
brew tap homebrew/cask-versions
```

現在，您可以安裝 PowerShell：

```sh
brew install --cask powershell-preview
```

最後，確認您的安裝可以正常執行：

```sh
pwsh-preview
```

當新的 PowerShell 版本發行時，請更新 Homebrew 的公式並升級 PowerShell：

```sh
brew update
brew upgrade powershell-preview --cask
```

> [!NOTE]
> 上述命令可從 PowerShell (pwsh) 主機內呼叫，但 PowerShell 殼層必須結束並重新啟動，才能完成升級。
> 並重新整理 `$PSVersionTable` 中顯示的值。

穩定版本與 LTS 版本也支援使用 Homebrew tap 方法安裝 PowerShell。

```sh
brew install powershell/tap/powershell
```

您現在可驗證安裝

```sh
pwsh
```

發行新版本的 PowerShell 時，只要執行下列命令即可。

```sh
brew upgrade powershell
```

> [!NOTE]
> 無論使用 cask 或 tap 方法，當更新至較新版本的 PowerShell 時，請使用與當初安裝 PowerShell 時相同的方法。 如果使用不同的方法，則開啟新的 pwsh 工作階段時將會繼續使用舊版 PowerShell。
>
> 如果決定使用不同的方法，則可使用 [Homebrew link 方法](https://docs.brew.sh/Manpage#link-ln-options-formula)來修正問題。

## <a name="installation-via-direct-download"></a>透過直接下載來安裝

將[版本][]頁面上的 PKG 套件 `powershell-7.1.0-osx-x64.pkg` 下載至 macOS 電腦。

您可以按兩下檔案並依照提示執行作業，或從終端機安裝：

```sh
sudo installer -pkg powershell-7.1.0-osx-x64.pkg -target /
```

安裝 [OpenSSL](#installing-dependencies)。 PowerShell 遠端執行功能與 CIM 作業需要 OpenSSL。

## <a name="install-as-a-net-global-tool"></a>安裝為 .NET 全域工具

如果您已安裝 [.NET Core SDK](/dotnet/core/sdk)，就可以輕鬆地將 PowerShell 安裝為 [.NET 全域工具](/dotnet/core/tools/global-tools)。

```
dotnet tool install --global PowerShell
```

Dotnet 工具安裝程式會將 `~/.dotnet/tools` 新增至您的 `PATH` 環境變數。 不過，目前執行的殼層沒有更新的 `PATH`。 您應該能夠透過輸入 `pwsh`，以從新的殼層啟動 PowerShell。

安裝 [OpenSSL](#installing-dependencies)。 PowerShell 遠端執行功能與 CIM 作業需要 OpenSSL。

## <a name="binary-archives"></a>二進位封存

macOS 平台有 PowerShell 二進位 `tar.gz` 封存，以啟用進階的部署案例。 當使用此方法安裝時，也必須手動安裝相依性。

安裝 [OpenSSL](#installing-dependencies)。 PowerShell 遠端執行功能與 CIM 作業需要 OpenSSL。

### <a name="installing-binary-archives-on-macos"></a>解除安裝 macOS 上的二進位封存

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.1.0/powershell-7.1.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/7.1.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/7.1.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/7.1.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/7.1.0/pwsh /usr/local/bin/pwsh
```

## <a name="installing-dependencies"></a>安裝相依性

PowerShell 遠端執行功能與 CIM 作業需要 OpenSSL。 如有需要，您可透過 MacPorts 安裝 OpenSSL。

> [!NOTE]
> 當 MacPorts 和 Homebrew 在同一個系統上一起使用時可能會發生問題。 不過，Homebrew 沒有 OpenSSL 1.0 的套件。 如需詳細資訊，請參閱 [MacPorts 常見問題集](https://trac.macports.org/wiki/FAQ)。

1. 安裝 Xcode 命令列工具。 MacPorts 需要 Xcode 工具。

   ```sh
   xcode-select --install
   ```

1. 安裝 MacPorts。 若需要指示，請參閱[安裝指南](https://www.macports.org/install.php) \(英文\)。
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

- `$PSHOME` 是 `/usr/local/microsoft/powershell/7.1.0/`
- 會從 `~/.config/powershell/profile.ps1` 讀取使用者設定檔
- 會從 `$PSHOME/profile.ps1` 讀取預設設定檔
- 會從 `~/.local/share/powershell/Modules` 讀取使用者模組
- 會從 `/usr/local/share/powershell/Modules` 讀取共用的模組
- 會從 `$PSHOME/Modules` 讀取預設模組
- PSReadline 記錄會記錄在 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

設定檔會採用 PowerShell 的每個主機設定。 因此預設主機特定設定檔便會存在於相同位置的 `Microsoft.PowerShell_profile.ps1`。

PowerShell 遵循 macOS 上的 [XDG 基底目錄規格][xdg-bds]。

因為 macOS 是 BSD 的衍生項，所以使用的前置詞是 `/usr/local` 而非 `/opt`。 因此，`$PSHOME` 是 `/usr/local/microsoft/powershell/7.1.0/`，而符號連結放置在 `/usr/local/bin/pwsh`。

## <a name="installation-support"></a>安裝支援

Microsoft 支援此文件中的安裝方法。 其他來源可能會提供其他安裝方法。 雖然那些工具與方法都有用，但 Microsoft 無法支援那些方法。

## <a name="additional-resources"></a>其他資源

- [Homebrew Web][brew]
- [Homebrew Github 存放庫][GitHub]
- [Homebrew-Cask][cask]

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[發行]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
