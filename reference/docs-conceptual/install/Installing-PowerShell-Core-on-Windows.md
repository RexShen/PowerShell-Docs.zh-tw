---
title: 在 Windows 上安裝 PowerShell
description: 在 Windows 上安裝 PowerShell 的相關資訊
ms.date: 10/30/2020
ms.openlocfilehash: 825c9066d0a4e4734b9255514520b32f0876ecea
ms.sourcegitcommit: 109ff625773389be56e98e994b7e56146f2b9d93
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/04/2020
ms.locfileid: "93296378"
---
# <a name="installing-powershell-on-windows"></a>在 Windows 上安裝 PowerShell

有多種方法可以在 Windows 中安裝 PowerShell。

## <a name="prerequisites"></a>Prerequisites

在 Windows 7 SP1、Server 2008 R2 和更新版本上支援 PowerShell 的最新版本。

若要透過 WSMan 啟用 PowerShell 遠端執行功能，必須符合下列必要條件：

- 在 Windows 10 以前的 Windows 版本中安裝[通用 C 執行階段](https://www.microsoft.com/download/details.aspx?id=50410)。 透過直接下載或 Windows Update 即可取得。 已完整修補的系統已安裝此套件。
- 在 Windows 7 和 Windows Server 2008 R2 上安裝 Windows Management Framework (WMF) 4.0 或更新版本。 如需 WMF 的詳細資訊，請參閱 [WMF 概觀](/powershell/scripting/wmf/overview)。

## <a name="download-the-installer-package"></a>下載安裝程式套件

若要在 Windows 上安裝 PowerShell，請從 GitHub 下載[最新的][]安裝套件。 您也可以在[版本][]頁面上找到最新的預覽版本。 向下捲動至 [版本] 頁面的 [資產]  區段。 [資產]  區段可能會摺疊，因此您可能需要按一下加以展開。

## <a name="installing-the-msi-package"></a><a id="msi" />安裝 MSI 套件

MSI 檔案看起來像 `PowerShell-<version>-win-<os-arch>.msi`。 例如：

- `PowerShell-7.0.3-win-x64.msi`
- `PowerShell-7.0.3-win-x86.msi`

下載後，按兩下安裝程式，並依提示操作。

安裝程式會在 Windows [開始] 功能表中建立捷徑。

- 套件預設安裝在 `$env:ProgramFiles\PowerShell\<version>`
- 您可以透過 [開始] 功能表或 `$env:ProgramFiles\PowerShell\<version>\pwsh.exe` 啟動 PowerShell

> [!NOTE]
> PowerShell 7 會安裝到新目錄，並與 Windows PowerShell 5.1 並存執行。 針對 PowerShell Core 6.x，PowerShell 7 會就地升級並移除 PowerShell Core 6.x。
>
> - PowerShell 7 會安裝到 `$env:ProgramFiles\PowerShell\7`
> - 系統會在 `$env:PATH` 中新增 `$env:ProgramFiles\PowerShell\7` 資料夾
> - 系統會刪除 `$env:ProgramFiles\PowerShell\6` 資料夾
>
> 如果您需要與 PowerShell 7 並存執行 PowerShell 6，請使用 [ZIP 安裝](#zip)方法來重新安裝 PowerShell 6。

### <a name="administrative-install-from-the-command-line"></a>從命令列進行系統管理安裝

您可以從命令列安裝 MSI 套件，讓系統管理員不需要使用者互動即可部署套件。 MSI 套件包含下列屬性以控制安裝選項：

- **ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - 此屬性控制將 [開啟 PowerShell]  項目新增至 Windows 檔案總管中的內容功能表的選項。
- **ENABLE_PSREMOTING** - 此屬性控制在安裝期間啟用 PowerShell 遠端執行功能的選項。
- **REGISTER_MANIFEST** - 此屬性控制用於註冊 Windows 事件記錄資訊清單的選項。

下列範例示範如何在啟用所有安裝選項的情況下，以無訊息方式安裝 PowerShell。

```powershell
msiexec.exe /package PowerShell-7.0.3-win-x64.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

如需 `Msiexec.exe` 的命令列選項完整清單，請參閱[命令列選項](/windows/desktop/Msi/command-line-options)。

### <a name="registry-keys-created-during-installation"></a>安裝期間建立的登錄機碼

從 PowerShell 7.1 開始，MSI 套件會建立登錄機碼以儲存 PowerShell 的安裝位置與版本。 這些值位於 `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\<GUID>`。 針對每個組建類型 (發行版本或預覽版)、主要版本與架構，`<GUID>` 的值都不重複。

|    版本    | 架構 |                                          登錄金鑰                                           |
| ------------- | :----------: | ----------------------------------------------------------------------------------------------- |
| 7.1.x 發行版本 |     x86      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\1d00683b-0f84-4db8-a64f-2f98ad42fe06` |
| 7.1.x 發行版本 |     x64      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\31ab5147-9a97-4452-8443-d9709f0516e1` |
| 7.1.x 預覽版 |     x86      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\86abcfbd-1ccc-4a88-b8b2-0facfde29094` |
| 7.1.x 預覽版 |     x64      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\39243d76-adaf-42b1-94fb-16ecf83237c8` |

系統管理員與開發人員可以加以使用來尋找 PowerShell 的路徑。 所有預覽版與次要發行版本的 `<GUID>` 值都相同。 每個主要發行版本的 `<GUID>` 值都會變更。

## <a name="installing-the-msix-package"></a><a id="msix" />安裝 MSIX 套件

> [!NOTE]
> 目前尚未正式支援 MSIX 套件。 我們會繼續建置僅供內部測試之用的套件。

若要在 Windows 10 用戶端上手動安裝 MSIX 套件，請從我們的 GitHub [版本][版本]頁面下載 MSIX 套件。 向下捲動至想安裝版本的 [資產]  區段。 [資產] 區段可能會摺疊，因此您可能需要按一下以展開它。

MSIX 檔案看起來像這樣 - `PowerShell-<version>-win-<os-arch>.msix`

若要安裝套件，您必須使用 `Add-AppxPackage` Cmdlet。

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

## <a name="installing-the-zip-package"></a><a id="zip" />安裝 ZIP 套件

有 PowerShell 二進位 ZIP 封存，以啟用進階的部署案例。 從[版本][版本]頁面下載下列其中一個 ZIP 封存。

- PowerShell-7.0.3-win-x64.zip
- PowerShell-7.0.3-win-x86.zip
- PowerShell-7.0.3-win-arm64.zip
- PowerShell-7.0.3-win-arm32.zip

依據您下載檔案的方式，可能需要使用 `Unblock-File`Cmdlet 以將檔案解除封鎖。 將內容解壓縮至您選擇的位置，並從該處執行 `pwsh.exe`。 與安裝 MSI 套件不同，安裝 ZIP 封存不會檢查先決條件。 若要使遠端功能能透過 WSMan 正常運作，請確定您已符合[必要條件](#prerequisites)。

使用此方法，在 Microsoft Surface Pro X 之類的電腦上安裝 ARM 型 PowerShell 版本。為獲得最佳結果，請將 PowerShell 安裝到 `$env:ProgramFiles\PowerShell\7` 資料夾。

## <a name="deploying-on-windows-10-iot-enterprise"></a>在 Windows 10 IoT 企業版上部署

Windows 10 IoT 企業版隨附 Windows PowerShell，我們可以將其用來部署 PowerShell 7。

1. 針對目標裝置建立 `PSSession`

   ```powershell
   Set-Item -Path WSMan:\localhost\Client\TrustedHosts <deviceip>
   $S = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

1. 將 ZIP 套件複製到裝置

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

1. 連接到裝置並展開封存

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

1. 設定 PowerShell 7 的遠端功能

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because
   # it has to restart WinRM
   ```

1. 連線到裝置上的 PowerShell 7 端點

   ```powershell
   # Be sure to use the -Configuration parameter. If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-windows-10-iot-core"></a>在 Windows 10 IoT 核心版上部署

當您包含 _IOT_POWERSHELL_ 功能 (可供我們用來部署 PowerShell 7) 時，Windows 10 IoT 核心版會新增 Windows PowerShell。 針對 Windows 10 IoT 企業版所定義的步驟也可以用於 IoT 核心版。

若要在出貨映像中新增最新的 PowerShell，請使用 [Import-PSCoreRelease][] 命令以在工作區包括套件，並將 _OPENSRC_POWERSHELL_ 功能新增到您的映像。

> [!NOTE]
> 針對 ARM64 架構，當您包括 _IOT_POWERSHELL_ 時，不會新增 Windows PowerShell。 因此，以 zip 為基礎的安裝將無法使用。 您將必須使用 `Import-PSCoreRelease` 命令，以將其新增至映像中。

## <a name="deploying-on-nano-server"></a>在 Nano Server 上部署

這些指示假設 Nano Server 是一個 PowerShell 版本已在其上執行的「無周邊」作業系統。 如需詳細資訊，請參閱 [Nano Server 映像建立器](/windows-server/get-started/deploy-nano-server) 文件。

目前可以使用兩種方法來部署 PowerShell 二進位檔。

1. 離線 - 掛接 Nano Server VHD，並將 ZIP 檔案內容解壓縮至您在掛接映像中選擇的位置。
1. 線上 - 透過 PowerShell 工作階段傳輸 ZIP 檔案，並將它解壓縮至您選擇的位置。

在這兩種情況下，您都需要 Windows 10 x64 ZIP 版套件。 在 PowerShell 的「系統管理員」執行個體中執行命令。

### <a name="offline-deployment-of-powershell"></a>PowerShell 的離線部署

1. 使用您最愛的 ZIP 公用程式將套件解壓縮至已掛接 Nano Server 映像的目錄。
1. 取消掛接映像和開機映像。
1. 連線到 Windows PowerShell 的內建執行個體。
1. 請遵循下列指示來建立使用[另一個執行個體技術][]的遠端端點。

### <a name="online-deployment-of-powershell"></a>PowerShell 的線上部署

使用下列步驟，將 PowerShell 部署到 Nano Server。

- 連線到 Windows PowerShell 的內建執行個體

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- 將檔案複製到 Nano Server 執行個體

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- 輸入工作階段

  ```powershell
  Enter-PSSession $session
  ```

- 壓縮檔 ZIP 檔案

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShell_<version>"
  ```

- 如需 WSMan 型的遠端功能，請遵循下列指示來建立使用[另一個執行個體技術][]的遠端端點。

## <a name="install-as-a-net-global-tool"></a>安裝為 .NET 全域工具

如果您已安裝 [.NET Core SDK](/dotnet/core/sdk)，就可以輕鬆地將 PowerShell 安裝為 [.NET 全域工具](/dotnet/core/tools/global-tools)。

```
dotnet tool install --global PowerShell
```

Dotnet 工具安裝程式會將 `$env:USERPROFILE\dotnet\tools` 新增至您的 `$env:PATH` 環境變數。 不過，目前執行的殼層沒有更新的 `$env:PATH`。 您可以透過輸入 `pwsh`，以從新的殼層啟動 PowerShell。

## <a name="install-powershell-via-winget"></a>透過 Winget 安裝 PowerShell

`winget` 命令列工具可讓開發人員探索、安裝、升級、移除及設定 Windows 10 電腦上的應用程式。 此工具是 Windows 封裝管理員服務的用戶端介面。

> [!NOTE]
> `winget` 工具目前處於預覽狀態。 目前並非所有已規劃的功能都可用。
> 您不應該在生產部署案例中使用此方法。 如需系統需求清單與安裝指示，請參閱 [winget] 文件。

您可以透過下列命令使用已發佈的 `winget` 套件來安裝 PowerShell：

1. 搜尋最新版的 PowerShell

   ```powershell
   winget search Microsoft.PowerShell
   ```

   ```Output
   Name               Id                           Version
   ---------------------------------------------------------------
   PowerShell         Microsoft.PowerShell         7.0.3
   PowerShell-Preview Microsoft.PowerShell-Preview 7.1.0-preview.5
   ```

1. 使用 `--exact` 參數安裝特定版本的 PowerShell

   ```powershell
   winget install --name PowerShell --exact
   winget install --name PowerShell-Preview --exact
   ```

## <a name="how-to-create-a-remoting-endpoint"></a>如何建立遠端端點

PowerShell 支援透過 WSMan 與 SSH 的 PowerShell 遠端通訊協定 (PSRP)。 如需詳細資訊，請參閱

- [PowerShell Core 中的 SSH 遠端功能][ssh-remoting]
- [PowerShell Core 中的 WSMan 遠端功能][wsman-remoting]

## <a name="upgrading-an-existing-installation"></a>升級現有的安裝

為了在升級時獲得最佳結果，您應該使用第一次安裝 PowerShell 時所使用的相同安裝方法。 每個安裝方法都會將 PowerShell 安裝於不同的位置。 如果您不確定 PowerShell 的安裝方式，則可將安裝的位置與此文章中的套件資訊進行比較。 如果您已透過 MSI 套件安裝，該資訊便會顯示於 [程式和功能] 控制台中。

## <a name="installation-support"></a>安裝支援

Microsoft 支援此文件中的安裝方法。 其他來源可能會提供其他安裝方法。 雖然那些工具與方法都有用，但 Microsoft 無法支援那些方法。

<!-- link references -->

[發行]: https://github.com/PowerShell/PowerShell/releases
[最新]: https://github.com/PowerShell/PowerShell/releases/latest
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
[winget]: /windows/package-manager/winget
[「另一個執行個體技術」]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register
[Import-PSCoreRelease]: https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease
