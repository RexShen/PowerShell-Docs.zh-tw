---
title: 在 Windows 上安裝 PowerShell Core
description: 在 Windows 上安裝 PowerShell Core 的相關資訊
ms.date: 08/06/2018
ms.openlocfilehash: 2b21908c38796117308f2ac1219db00ff9086408
ms.sourcegitcommit: 6749f67c32e05999e10deb9d45f90f45ac21a599
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850974"
---
# <a name="installing-powershell-core-on-windows"></a>在 Windows 上安裝 PowerShell Core

## <a name="msi"></a>MSI

若要在 Windows 用戶端或 Windows Server 上安裝 PowerShell (適用於 Windows 7 SP1、Server 2008 R2 和更新版本)，請從我們的 GitHub [版本][]頁面下載 MSI 套件。

MSI 檔案看起來像這樣 - `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well -->

下載後，按兩下安裝程式，並依提示操作。

安裝時會在 [開始] 功能表中放置捷徑。

- 套件預設安裝在 `$env:ProgramFiles\PowerShell\<version>`
- 您可以透過 [開始] 功能表或 `$env:ProgramFiles\PowerShell\<version>\pwsh.exe` 啟動 PowerShell

### <a name="prerequisites"></a>必要條件

若要透過 WSMan 啟用 PowerShell 遠端執行功能，必須符合下列必要條件：

- 在 Windows 10 以下的 Windows 版本中安裝[通用 C 執行階段](https://www.microsoft.com/download/details.aspx?id=50410)。
  透過直接下載或 Windows Update 即可取得。
  完整修補 (包括選擇性的套件) 的受支援系統已安裝此項目。
- 在 Windows 7 和 Windows Server 2008 R2 上安裝 Windows Management Framework (WMF) 4.0 或更新版本。

## <a name="zip"></a>ZIP

有 PowerShell 二進位 ZIP 封存，以啟用進階的部署案例。
請注意，當使用 ZIP 封存時，不會像 MSI 套件一樣檢查必要條件。
因此，為讓透過 WSMan 進行的遠端功能能在 Windows 10 以下的 Windows 版本上正常運作，請務必符合[必要條件](#prerequisites)。

## <a name="deploying-on-windows-iot"></a>在 Windows IoT 上部署

Windows IoT 附帶提供 Windows PowerShell， 我們就是用它來部署 PowerShell Core 6。

1. 針對目標裝置建立 `PSSession`

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. 將 ZIP 套件複製到裝置

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-6.1.0-win-arm32.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. 連接到裝置並展開封存

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-6.1.0-win-arm32.zip
   ```

4. 設定 PowerShell Core 6 的遠端處理

   ```powershell
   Set-Location .\PowerShell-6.1.0-win-arm32
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. 連接到裝置上的 PowerShell 核心 6 端點

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.6.1.0
   ```

## <a name="deploying-on-nano-server"></a>在 Nano Server 上部署

這些指示假設某個 PowerShell 版本已在 Nano Server 映像中執行，而且此映像是由 [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server) 產生。
Nano Server 是一種「無周邊」作業系統。 目前有兩種方法可以部署核心二進位檔。

1. 離線 - 掛接 Nano Server VHD，並將 ZIP 檔案內容解壓縮至您在掛接映像中選擇的位置。
2. 線上 - 透過 PowerShell 工作階段傳輸 ZIP 檔案，並將它解壓縮至您選擇的位置。

這兩種情況都需要 Windows 10 x64 ZIP 版套件，還需要在「系統管理員」PowerShell 執行個體中執行命令。

### <a name="offline-deployment-of-powershell-core"></a>PowerShell Core 的離線部署

1. 使用您最愛的 ZIP 公用程式將套件解壓縮至已掛接 Nano Server 映像的目錄。
2. 取消掛接映像和開機映像。
3. 連線到 Windows PowerShell 的收件匣執行個體。
4. 請遵循下列指示來建立使用[另一個執行個體技術](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)的遠端端點。

### <a name="online-deployment-of-powershell-core"></a>PowerShell Core 的線上部署

下列步驟會引導您從部署 PowerShell Core 到執行 Nano Server 執行個體及其遠端端點的設定。

- 連線到 Windows PowerShell 的收件匣執行個體

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
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- 如需 WSMan 型的遠端功能，請遵循下列指示來建立使用[另一個執行個體技術](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)的遠端端點。

## <a name="instructions-to-create-a-remoting-endpoint"></a>建立遠端端點的指示

PowerShell Core 支援 WSMan 和 SSH 上的 PowerShell 遠端通訊協定 (PSRP)。
如需詳細資訊，請參閱：

- [PowerShell Core 中的 SSH 遠端功能][ssh-remoting]
- [PowerShell Core 中的 WSMan 遠端功能][wsman-remoting]

## <a name="artifact-installation-instructions"></a>成品安裝指示

我們在每個以 [AppVeyor][] 建置的 CI 上發行具有 CoreCLR 位元的封存。

若要從 CoreCLR 成品安裝 PowerShell Core：

1. 從特定組建的 [成品] 索引標籤下載 ZIP 套件。
2. 解除封鎖 ZIP 檔案：以滑鼠右鍵按一下檔案總管 -> [屬性] -> 核取 [解除封鎖] 方塊 -> [套用]
3. 將 ZIP 檔案解壓縮至 `bin` 目錄
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO -->

[版本]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
