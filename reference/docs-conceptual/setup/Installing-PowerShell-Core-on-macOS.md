---
title: 在 macOS 上安裝 PowerShell Core
description: 在 macOS 上安裝 PowerShell Core 的相關資訊
ms.date: 08/06/2018
ms.openlocfilehash: ff1814d95b3ca3fa8497069dff249fd2ad5576ef
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587460"
---
# <a name="installing-powershell-core-on-macos"></a>在 macOS 上安裝 PowerShell Core

PowerShell Core 支援 macOS 10.12 和更版本。
GitHub [版本][]頁面上提供所有套件。
安裝套件之後，請從終端機執行 `pwsh`。

### <a name="installation-via-homebrew-on-macos-1012"></a>在 macOS 10.12+ 上透過 Homebrew 進行安裝

[Homebrew][ brew] 是 macOS 首選的套件管理員。
從終端機視窗中，輸入 `brew` 來執行 Homebrew。  如果找不到 `brew` 命令，您需要遵循[指示][brew]安裝 Homebrew。

> [!NOTE]
> 如果您過去已安裝 Homebrew，那麼，比較好的辦法是執行 'brew update-reset' 與 'brew update'。
```sh
brew update-reset
brew update
```

> 較舊的 Homebrew 版本會使用 tap 'caskroom/cask'，其已被取代並遷移到 'homebrew/cask'。  詳細資訊位於 [Homebrew-cask][cask]。 使用 'brew tap' 命令來列出您目前的點選。  如果您看到 'caskroom/cask'，您可以使用 'brew update' 來讓 Homebrew 遷移點選。

```sh
brew tap
brew update
```

當您安裝/更新 Homebrew 之後，安裝 PowerShell 就很容易。

安裝 PowerShell：

```sh
brew cask install powershell
```

最後，確認您的安裝可以正常執行：

```sh
pwsh
```

若要結束 PowerShell 並返回 Bash，請使用 'exit' 命令。
```sh
exit
```

發行新的 PowerShell 版本時，只要更新 Homebrew 的公式並升級 PowerShell 即可：

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> 您可從 PowerShell (pwsh) 主機內呼叫上命令，但必須結束並重新啟動 PowerShell 殼層，才能完成升級並重新整理 $PSVersionTable 中顯示的值。

### <a name="installing-preview-via-homebrew-on-macos-1012"></a>在 macOS 10.12+ 上透過 Homebrew 安裝預覽

[Homebrew][ brew] 是 macOS 首選的套件管理員。
從終端機視窗中，輸入 `brew` 來執行 Homebrew。  如果找不到 `brew` 命令，您需要遵循[指示][brew]安裝 Homebrew。

> [!NOTE]
> 如果您過去已安裝 Homebrew，那麼，比較好的辦法是執行 'brew update-reset' 與 'brew update'。
```sh
brew update-reset
brew update
```

接著，您必須點選 `versions` casks 存放庫來取得預覽套件：

```sh
brew tap homebrew/cask-versions
```

安裝 PowerShell 預覽：

```sh
brew cask install powershell-preview
```

最後，確認您的安裝可以正常執行：

```sh
pwsh-preview
```

發行新的 PowerShell 版本時，只需更新 Homebrew 的公式並升級 PowerShell 預覽即可：

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> 您可從 PowerShell (pwsh) 主機內呼叫上命令，但必須結束並重新啟動 PowerShell 殼層，才能完成升級並重新整理 $PSVersionTable 中顯示的值。

### <a name="installation-via-direct-download"></a>透過直接下載來安裝

將[版本][]頁面上的 PKG 套件 `powershell-6.0.2-osx.10.12-x64.pkg` 下載至 macOS 電腦。

您可以按兩下檔案並依照提示執行作業，或從終端機安裝：

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a>二進位封存

macOS 和 Linux 平台有 PowerShell 二進位 `tar.gz` 封存，以啟用進階的部署案例。

### <a name="installing-binary-archives-on-macos"></a>解除安裝 macOS 上的二進位封存

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.2/pwsh /usr/local/bin/pwsh
```

## <a name="uninstalling-powershell-core"></a>解除安裝 PowerShell Core

如果您使用 Homebrew 安裝 PowerShell，解除安裝很簡單：

```sh
brew cask uninstall powershell
```

如已透過直接下載安裝 PowerShell，即必須手動移除 PowerShell：

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

若要解除安裝其他的 PowerShell 路徑，請參閱本文件中的[路徑][]一節，使用 `sudo rm` 移除所要的路徑。

> [!NOTE]
> 如果使用 Homebrew 安裝，此即非必要。

[路徑]:#paths

## <a name="paths"></a>路徑

* `$PSHOME` 是 `/usr/local/microsoft/powershell/6.0.2/`
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
因此，`$PSHOME` 是 `/usr/local/microsoft/powershell/6.0.2/`，而且符號連結放在 `/usr/local/bin/pwsh`。

## <a name="additional-resources"></a>其他資源

* [Homebrew Web][brew]
* [Homebrew Github 存放庫][GitHub]
* [Homebrew-Cask][cask]


[brew]: http://brew.sh/
[GitHub]: https://github.com/Homebrew
[Cask]: https://github.com/Homebrew/homebrew-cask
[版本]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
