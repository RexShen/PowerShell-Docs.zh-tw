---
title: 透過 SSH 的 PowerShell 遠端處理
description: 使用 SSH 在 PowerShell Core 中遠端
ms.date: 08/14/2018
ms.openlocfilehash: 1de034d667aa9a377e5460e7eb474402c690cb42
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133149"
---
# <a name="powershell-remoting-over-ssh"></a>透過 SSH 的 PowerShell 遠端處理

## <a name="overview"></a>概觀

PowerShell 遠端通常會使用 WinRM 進行連線交涉和資料傳輸。 SSH 目前適用於 Linux 與 Windows 平台，而且能夠執行真正的多平台 PowerShell 遠端功能。

WinRM 提供一個健全裝載模型以供 PowerShell 遠端工作階段使用。 使用這個實作時，SSH 型遠端功能目前不支援遠端端點設定和 JEA (Just Enough Administration)。

SSH 遠端功能可讓您在 Windows 與 Linux 電腦之間執行基本 PowerShell 工作階段遠端功能。 SSH 遠端功能會在目標電腦上建立 PowerShell 裝載處理序作為 SSH 子系統。
最後，我們將實作一般裝載模型 (類似 WinRM) 以支援端點設定與 JEA。

`New-PSSession`、`Enter-PSSession` 與 `Invoke-Command` Cmdlet 現在有新的參數集，可支援這個新的遠端連線。

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

若要建立遠端工作階段，您可以使用 `HostName` 參數來指定目標電腦，並使用 `UserName` 來提供使用者名稱。 以互動方式執行 Cmdlet 時，系統會提示您輸入密碼。 您也可以搭配 `KeyFilePath` 參數使用私密金鑰檔案，來使用 SSH 金鑰驗證。

## <a name="general-setup-information"></a>一般安裝資訊

SSH 必須安裝在所有電腦上。 請同時安裝 SSH 用戶端 (`ssh.exe`) 與伺服器 (`sshd.exe`)，讓您可從遠端往返電腦。 針對 Windows，[從 GitHub 安裝 Win32 OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/releases) \(英文\)。
針對 Linux，安裝您平台適用的 SSH (包括 sshd 伺服器)。 您也需要從 GitHub 安裝 PowerShell Core 來取得 SSH 遠端功能。 SSH 伺服器必須設定為建立 SSH 子系統，以便在遠端電腦上裝載 PowerShell 處理序。 您也必須設定啟用密碼或以金鑰為基礎的驗證。

## <a name="set-up-on-windows-machine"></a>在 Windows 電腦上進行安裝

1. 安裝最新的 [PowerShell Core for Windows] 版本

   - 您可以查看針對 `New-PSSession` 所設定的參數，得知它是否具有 SSH 遠端支援

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. 使用 [安裝] 指示，安裝 GitHub 中最新的 [Win32 OpenSSH] 組建
3. 編輯 Win32 OpenSSH 所安裝位置中的 sshd_config 檔案

   - 確定已啟用密碼驗證

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6.0.4/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > OpenSSH for Windows 中有一個錯 Bug，會讓空格無法在子系統可執行檔路徑中運作。 如需詳細資訊，請參閱[這個 GitHub 問題](https://github.com/PowerShell/Win32-OpenSSH/issues/784) \(英文\)。

     解決方案之一是建立未包含空格之 PowerShell 安裝目錄的符號連結：

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6.0.4"
     ```

     然後在子系統中輸入它：

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - 選擇性啟用金鑰驗證

     ```
     PubkeyAuthentication yes
     ```

4. 重新啟動 sshd 服務

   ```powershell
   Restart-Service sshd
   ```

5. 將 OpenSSH 安裝所在的路徑新增至 Path 環境變數。 例如，`C:\Program Files\OpenSSH\`。 這個項目能夠允許程式找到 ssh.exe。

## <a name="set-up-on-linux-ubuntu-1404-machine"></a>在 Linux (Ubuntu 14.04) 電腦上進行安裝

1. 安裝 GitHub 中最新的 [PowerShell Core for Linux] 組建
2. 視需要安裝 [Ubuntu SSH]

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. 編輯 /etc/ssh 位置中的 sshd_config 檔案

   - 確定已啟用密碼驗證

   ```
   PasswordAuthentication yes
   ```

   - 新增 PowerShell 子系統項目

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - 選擇性啟用金鑰驗證

   ```
   PubkeyAuthentication yes
   ```

4. 重新啟動 sshd 服務

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-macos-machine"></a>在 MacOS 電腦上進行安裝

1. 安裝最新的 [PowerShell Core for MacOS] 組建

   - 確定已遵循下列步驟來啟用 SSH 遠端：
     - 開啟 `System Preferences`
     - 按一下 `Sharing`
     - 檢查 `Remote Login` - 應該為 `Remote Login: On`
     - 允許存取適當的使用者

2. 編輯 `/private/etc/ssh/sshd_config` 位置中的 `sshd_config` 檔案

   - 使用您慣用的編輯器，或

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - 確定已啟用密碼驗證

     ```
     PasswordAuthentication yes
     ```

   - 新增 PowerShell 子系統項目

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - 選擇性啟用金鑰驗證

     ```
     PubkeyAuthentication yes
     ```

3. 重新啟動 sshd 服務

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="powershell-remoting-example"></a>PowerShell 遠端範例

測試遠端功能的最簡單方式是在單一電腦上進行試用。 在此範例中，我們會建立回到相同 Linux 電腦的遠端工作階段。 我們會以互動方式使用 PowerShell Cmdlet，因此，我們會看到要求驗證主機電腦的 SSH 提示以及密碼提示。 您可以在 Windows 電腦上執行相同的動作以確保遠端功能正在運作。 接著，透過變更主機名稱，在電腦之間執行遠端功能。

```powershell
#
# Linux to Linux
#
$session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
```

```output
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:
```

```powershell
$session
```

```output
 Id Name   ComputerName    ComputerType    State    ConfigurationName     Availability
 -- ----   ------------    ------------    -----    -----------------     ------------
  1 SSH1   UbuntuVM1       RemoteMachine   Opened   DefaultShell             Available
```

```powershell
Enter-PSSession $session
```

```output
[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~14.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession
```

```powershell
Invoke-Command $session -ScriptBlock { Get-Process powershell }
```

```output
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

```output
PTestName@WinVM1s password:
```

```powershell
[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver
```

```output
Microsoft Windows [Version 10.0.10586]
```

```powershell
#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
```

```output
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.
```

```powershell
$session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
```

```output
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
```

```powershell
$session
```

```output
 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available
```

```powershell
Enter-PSSession -Session $session
```

```output
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

sudo 命令不適用於連至 Linux 電腦的遠端工作階段。

## <a name="see-also"></a>另請參閱

[PowerShell Core for Windows](../setup/installing-powershell-core-on-windows.md#msi)

[PowerShell Core for Linux](../setup/installing-powershell-core-on-linux.md#ubuntu-1404)

[PowerShell Core for MacOS](../setup/installing-powershell-core-on-macos.md)

[Win32 OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/releases)

[安裝](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH)

[Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
