---
title: 透過 SSH 的 PowerShell 遠端處理
description: 使用 SSH 在 PowerShell Core 中遠端
ms.date: 09/30/2019
ms.openlocfilehash: 0f2fb13010d62dec5b19b373a24a199bff22665d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "73444366"
---
# <a name="powershell-remoting-over-ssh"></a>透過 SSH 的 PowerShell 遠端處理

## <a name="overview"></a>概觀

PowerShell 遠端通常會使用 WinRM 進行連線交涉和資料傳輸。 SSH 目前適用於 Linux 與 Windows 平台，而且能夠執行真正的多平台 PowerShell 遠端功能。

WinRM 提供一個健全裝載模型以供 PowerShell 遠端工作階段使用。 SSH 遠端功能目前不支援遠端端點設定和 Just Enough Administration (JEA)。

SSH 遠端功能可讓您在 Windows 與 Linux 電腦之間執行基本 PowerShell 工作階段遠端功能。 SSH 遠端功能會在目標電腦上建立 PowerShell 裝載處理序作為 SSH 子系統。 最後，我們將實作一般裝載模型 (類似 WinRM) 以支援端點設定與 JEA。

`New-PSSession`、`Enter-PSSession` 與 `Invoke-Command` Cmdlet 現在有新的參數集，可支援這個新的遠端連線。

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

若要建立遠端工作階段，您可以使用 `HostName` 參數來指定目標電腦，並使用 `UserName` 來提供使用者名稱。 以互動方式執行 Cmdlet 時，系統會提示您輸入密碼。 您也可以搭配 `KeyFilePath` 參數使用私密金鑰檔案，來使用 SSH 金鑰驗證。

## <a name="general-setup-information"></a>一般安裝資訊

PowerShell 6 或更新版本，且必須在所有電腦上安裝 SSH。 請同時安裝 SSH 用戶端 (`ssh.exe`) 與伺服器 (`sshd.exe`)，讓您可從遠端往返電腦。 適用於 Windows 的 OpenSSH 現在已可在 Windows 10 組建 1809 與 Windows Server 2019 中使用。 如需詳細資訊，請參閱[使用 OpenSSH 管理 Windows](/windows-server/administration/openssh/openssh_overview)。 針對 Linux，安裝您平台適用的 SSH (包括 sshd 伺服器)。 您也需要從 GitHub 安裝 PowerShell 來取得 SSH 遠端功能。 SSH 伺服器必須設定為建立 SSH 子系統，以便在遠端電腦上裝載 PowerShell 處理序。 而且，您也必須設定啟用**密碼**或**金鑰型**的驗證。

## <a name="set-up-on-a-windows-computer"></a>在 Windows 電腦上設定

1. 安裝最新版的 PowerShell，請參閱[在 Windows 上安裝 PowerShell Core](../../install/installing-powershell-core-on-windows.md#msi)。

   您可以列出 `New-PSSession` 參數集來確認 PowerShell 具有 SSH 遠端支援。 您會注意到以 **SSH** 開頭的參數集名稱。 這些參數集包括 **SSH** 參數。

   ```powershell
   (Get-Command New-PSSession).ParameterSets.Name
   ```

   ```Output
   Name
   ----
   SSHHost
   SSHHostHashParam
   ```

1. 安裝最新的 Win32 OpenSSH。 如需安裝指示，請參閱[開始使用 OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse)。

   > [!NOTE]
   > 如果您想要將 PowerShell 設定為 OpenSSH 的預設殼層，請參閱[為 OpenSSH 設定 Windows](/windows-server/administration/openssh/openssh_server_configuration)。

1. 編輯位於 `$env:ProgramData\ssh` 的 `sshd_config` 檔案。

   確定已啟用密碼驗證：

   ```
   PasswordAuthentication yes
   ```

   在遠端電腦上建立裝載 PowerShell 處理程序的 SSH 子系統：

   ```
   Subsystem powershell c:/progra~1/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
   ```

   > [!NOTE]
   > 您必須針對任何包含空格的檔案路徑使用 8.3 簡短名稱。 OpenSSH for Windows 中有一個 Bug，會讓空格無法在子系統可執行檔路徑中運作。 如需詳細資訊，請參閱此 [GitHub 問題](https://github.com/PowerShell/Win32-OpenSSH/issues/784)。
   >
   > Windows 中 `Program Files` 資料夾的 8.3 簡短名稱通常是 `Progra~1`。 但您可以使用下列命令來確保：
   >
   > ```powershell
   > Get-CimInstance Win32_Directory -Filter 'Name="C:\\Program Files"' |
   >   Select-Object EightDotThreeFileName
   > ```
   >
   > ```Output
   > EightDotThreeFileName
   > ---------------------
   > c:\progra~1
   > ```

   選擇性啟用金鑰驗證：

   ```
   PubkeyAuthentication yes
   ```

   如需詳細資訊，請參閱[管理 OpenSSH 金鑰](/windows-server/administration/openssh/openssh_keymanagement)。

1. 重新啟動 **sshd** 服務。

   ```powershell
   Restart-Service sshd
   ```

1. 將 OpenSSH 安裝所在的路徑新增至 Path 環境變數。 例如，`C:\Program Files\OpenSSH\`。 此項目可允許程式找到 `ssh.exe`。

## <a name="set-up-on-an-ubuntu-1604-linux-computer"></a>在 Ubuntu 16.04 Linux 電腦上設定

1. 安裝最新版的 PowerShell，請參閱[在 Linux 上安裝 PowerShell Core](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)。
1. 安裝 [Ubuntu OpenSSH Server](https://help.ubuntu.com/lts/serverguide/openssh-server.html)。

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

1. 編輯 `/etc/ssh` 位置中的 `sshd_config` 檔案。

   確定已啟用密碼驗證：

   ```
   PasswordAuthentication yes
   ```

   新增 PowerShell 子系統項目：

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   選擇性啟用金鑰驗證：

   ```
   PubkeyAuthentication yes
   ```

1. 重新啟動 **sshd** 服務。

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-a-macos-computer"></a>在 macOS 電腦上設定

1. 安裝最新版的 PowerShell，請參閱[在 macOS 上安裝 PowerShell Core](../../install/installing-powershell-core-on-macos.md)。

   確定已遵循下列步驟來啟用 SSH 遠端：

   1. 開啟 `System Preferences`。
   1. 按一下 `Sharing`。
   1. 選取 `Remote Login` 以設定 `Remote Login: On`。
   1. 允許適當的使用者存取。

1. 編輯 `/private/etc/ssh/sshd_config` 位置中的 `sshd_config` 檔案。

   開啟文字編輯器，例如 **nano**：

   ```bash
   sudo nano /private/etc/ssh/sshd_config
   ```

   確定已啟用密碼驗證：

   ```
   PasswordAuthentication yes
   ```

   新增 PowerShell 子系統項目：

   ```
   Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   選擇性啟用金鑰驗證：

   ```
   PubkeyAuthentication yes
   ```

1. 重新啟動 **sshd** 服務。

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a>驗證

透過 SSH 的 PowerShell 遠端功能需要在 SSH 用戶端與 SSH 服務之間交換驗證，且本身不會實作任何驗證配置。 結果是，任何已設定的驗證配置 (包括多重要素驗證) 都是由 SSH 處理，與 PowerShell 無關。 例如，您可以設定 SSH 服務要求公開金鑰驗證及單次密碼來增強安全性。 設定多重要素驗證不在本文件的討論範圍內。 請參閱 SSH 文件，以了解如何正確地設定多重要素驗證，並驗證它在 PowerShell 之外是否運作正常，再嘗試與 PowerShell 遠端功能搭配使用。

## <a name="powershell-remoting-example"></a>PowerShell 遠端範例

測試遠端功能的最簡單方式是在單一電腦上進行試用。 在此範例中，我們會建立回到相同 Linux 電腦的遠端工作階段。 我們會以互動方式使用 PowerShell Cmdlet；因此，我們會看到要求驗證主機電腦的 SSH 提示以及密碼提示。 您可以在 Windows 電腦上執行相同的動作以確保遠端功能正在運作。 接著，透過變更主機名稱，在電腦之間執行遠端功能。

```powershell
#
# Linux to Linux
#
$session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
```

```Output
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:
```

```powershell
$session
```

```Output
 Id Name   ComputerName    ComputerType    State    ConfigurationName     Availability
 -- ----   ------------    ------------    -----    -----------------     ------------
  1 SSH1   UbuntuVM1       RemoteMachine   Opened   DefaultShell             Available
```

```powershell
Enter-PSSession $session
```

```Output
[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~16.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession
```

```powershell
Invoke-Command $session -ScriptBlock { Get-Process powershell }
```

```Output
Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName                    PSComputerName
-------  ------    -----      -----     ------     --  -- -----------                    --------------
      0       0        0         19       3.23  10635 635 powershell                     UbuntuVM1
      0       0        0         21       4.92  11033 017 powershell                     UbuntuVM1
      0       0        0         20       3.07  11076 076 powershell                     UbuntuVM1
```

```powershell
#
# Linux to Windows
#
Enter-PSSession -HostName WinVM1 -UserName PTestName
```

```Output
PTestName@WinVM1s password:
```

```powershell
[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver
```

```Output
Microsoft Windows [Version 10.0.10586]
```

```powershell
#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
```

```Output
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.
```

```powershell
$session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
```

```Output
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
```

```powershell
$session
```

```Output
 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available
```

```powershell
Enter-PSSession -Session $session
```

```Output
[WinVM2]: PS C:\Users\PSRemoteUser\Documents> $PSVersionTable

Name                           Value
----                           -----
PSEdition                      Core
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
SerializationVersion           1.1.0.1
BuildVersion                   3.0.0.0
CLRVersion
PSVersion                      6.0.0-alpha
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
GitCommitId                    v6.0.0-alpha.17


[WinVM2]: PS C:\Users\PSRemoteUser\Documents>
```

### <a name="known-issues"></a>已知問題

**sudo** 命令不適用於 Linux 電腦的遠端工作階段。

## <a name="see-also"></a>另請參閱

[在 Linux 上安裝 PowerShell Core](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)

[在 macOS 上安裝 PowerShell Core](../../install/installing-powershell-core-on-macos.md)

[在 Windows 上安裝 PowerShell Core](../../install/installing-powershell-core-on-windows.md#msi)

[使用 OpenSSH 管理 Windows](/windows-server/administration/openssh/openssh_overview)

[管理 OpenSSH 金鑰](/windows-server/administration/openssh/openssh_keymanagement)

[Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
