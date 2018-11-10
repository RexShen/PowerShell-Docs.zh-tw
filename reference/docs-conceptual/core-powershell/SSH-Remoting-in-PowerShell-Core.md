---
title: 透過 SSH 的 PowerShell 遠端處理
description: 使用 SSH 在 PowerShell Core 中遠端
ms.date: 08/14/2018
ms.openlocfilehash: 842e67e96661bca8be54aab33cbc11aa23dbd1c0
ms.sourcegitcommit: 47becf2823ece251a7264db2387bb503cf3abaa9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2018
ms.locfileid: "49451060"
---
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="f552f-103">透過 SSH 的 PowerShell 遠端處理</span><span class="sxs-lookup"><span data-stu-id="f552f-103">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="f552f-104">概觀</span><span class="sxs-lookup"><span data-stu-id="f552f-104">Overview</span></span>

<span data-ttu-id="f552f-105">PowerShell 遠端通常會使用 WinRM 進行連線交涉和資料傳輸。</span><span class="sxs-lookup"><span data-stu-id="f552f-105">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span> <span data-ttu-id="f552f-106">SSH 目前適用於 Linux 與 Windows 平台，而且能夠執行真正的多平台 PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="f552f-106">SSH is now available for Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>

<span data-ttu-id="f552f-107">WinRM 提供一個健全裝載模型以供 PowerShell 遠端工作階段使用。</span><span class="sxs-lookup"><span data-stu-id="f552f-107">WinRM provides a robust hosting model for PowerShell remote sessions.</span></span> <span data-ttu-id="f552f-108">SSH 型遠端功能目前不支援遠端端點設定和 JEA (Just Enough Administration)。</span><span class="sxs-lookup"><span data-stu-id="f552f-108">SSH-based remoting doesn't currently support remote endpoint configuration and JEA (Just Enough Administration).</span></span>

<span data-ttu-id="f552f-109">SSH 遠端功能可讓您在 Windows 與 Linux 電腦之間執行基本 PowerShell 工作階段遠端功能。</span><span class="sxs-lookup"><span data-stu-id="f552f-109">SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span> <span data-ttu-id="f552f-110">SSH 遠端功能會在目標電腦上建立 PowerShell 裝載處理序作為 SSH 子系統。</span><span class="sxs-lookup"><span data-stu-id="f552f-110">SSH Remoting creates a PowerShell host process on the target machine as an SSH subsystem.</span></span>
<span data-ttu-id="f552f-111">最後，我們將實作一般裝載模型 (類似 WinRM) 以支援端點設定與 JEA。</span><span class="sxs-lookup"><span data-stu-id="f552f-111">Eventually we'll implement a general hosting model, similar to WinRM, to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="f552f-112">`New-PSSession`、`Enter-PSSession` 與 `Invoke-Command` Cmdlet 現在有新的參數集，可支援這個新的遠端連線。</span><span class="sxs-lookup"><span data-stu-id="f552f-112">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets now have a new parameter set to support this new remoting connection.</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="f552f-113">若要建立遠端工作階段，您可以使用 `HostName` 參數來指定目標電腦，並使用 `UserName` 來提供使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="f552f-113">To create a remote session, you specify the target machine with the `HostName` parameter and provide the user name with `UserName`.</span></span> <span data-ttu-id="f552f-114">以互動方式執行 Cmdlet 時，系統會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="f552f-114">When running the cmdlets interactively, you're prompted for a password.</span></span> <span data-ttu-id="f552f-115">您也可以搭配 `KeyFilePath` 參數使用私密金鑰檔案，來使用 SSH 金鑰驗證。</span><span class="sxs-lookup"><span data-stu-id="f552f-115">You can also, use SSH key authentication using a private key file with the `KeyFilePath` parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="f552f-116">一般安裝資訊</span><span class="sxs-lookup"><span data-stu-id="f552f-116">General setup information</span></span>

<span data-ttu-id="f552f-117">SSH 必須安裝在所有電腦上。</span><span class="sxs-lookup"><span data-stu-id="f552f-117">SSH must be installed on all machines.</span></span> <span data-ttu-id="f552f-118">請同時安裝 SSH 用戶端 (`ssh.exe`) 與伺服器 (`sshd.exe`)，讓您可從遠端往返電腦。</span><span class="sxs-lookup"><span data-stu-id="f552f-118">Install both the SSH client (`ssh.exe`) and server (`sshd.exe`) so that you can remote to and from the machines.</span></span> <span data-ttu-id="f552f-119">針對 Windows，[從 GitHub 安裝 Win32 OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/releases) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="f552f-119">For Windows, install [Win32 OpenSSH from GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span></span>
<span data-ttu-id="f552f-120">針對 Linux，安裝您平台適用的 SSH (包括 sshd 伺服器)。</span><span class="sxs-lookup"><span data-stu-id="f552f-120">For Linux, install SSH (including sshd server) appropriate to your platform.</span></span> <span data-ttu-id="f552f-121">您也需要從 GitHub 安裝 PowerShell Core 來取得 SSH 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="f552f-121">You also need to install PowerShell Core from GitHub to get the SSH remoting feature.</span></span> <span data-ttu-id="f552f-122">SSH 伺服器必須設定為建立 SSH 子系統，以便在遠端電腦上裝載 PowerShell 處理序。</span><span class="sxs-lookup"><span data-stu-id="f552f-122">The SSH server must be configured to create an SSH subsystem to host a PowerShell process on the remote machine.</span></span> <span data-ttu-id="f552f-123">您也必須設定啟用密碼或以金鑰為基礎的驗證。</span><span class="sxs-lookup"><span data-stu-id="f552f-123">You also must configure enable password or key-based authentication.</span></span>

## <a name="set-up-on-windows-machine"></a><span data-ttu-id="f552f-124">在 Windows 電腦上進行安裝</span><span class="sxs-lookup"><span data-stu-id="f552f-124">Set up on Windows Machine</span></span>

1. <span data-ttu-id="f552f-125">最新 [PowerShell Core for Windows](../setup/installing-powershell-core-on-windows.md#msi) 版本</span><span class="sxs-lookup"><span data-stu-id="f552f-125">Install the latest version of [PowerShell Core for Windows](../setup/installing-powershell-core-on-windows.md#msi)</span></span>

   - <span data-ttu-id="f552f-126">您可以查看針對 `New-PSSession` 所設定的參數，得知它是否具有 SSH 遠端支援</span><span class="sxs-lookup"><span data-stu-id="f552f-126">You can tell if it has the SSH remoting support by looking at the parameter sets for `New-PSSession`</span></span>

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. <span data-ttu-id="f552f-127">使用[安裝](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH)指示，安裝 GitHub 中的最新 [Win32 OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/releases) 組建</span><span class="sxs-lookup"><span data-stu-id="f552f-127">Install the latest [Win32 OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/releases) build from GitHub using the [installation](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH) instructions</span></span>
3. <span data-ttu-id="f552f-128">編輯位於 `%ProgramData%\ssh` 的 sshd_config 檔案。</span><span class="sxs-lookup"><span data-stu-id="f552f-128">Edit the sshd_config file located at `%ProgramData%\ssh`.</span></span>

   - <span data-ttu-id="f552f-129">確定已啟用密碼驗證</span><span class="sxs-lookup"><span data-stu-id="f552f-129">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > <span data-ttu-id="f552f-130">OpenSSH for Windows 中有一個錯 Bug，會讓空格無法在子系統可執行檔路徑中運作。</span><span class="sxs-lookup"><span data-stu-id="f552f-130">There is a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span> <span data-ttu-id="f552f-131">如需詳細資訊，請參閱[這個 GitHub 問題](https://github.com/PowerShell/Win32-OpenSSH/issues/784) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="f552f-131">For more information, see [this GitHub issue](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>

     <span data-ttu-id="f552f-132">解決方案之一是建立未包含空格之 PowerShell 安裝目錄的符號連結：</span><span class="sxs-lookup"><span data-stu-id="f552f-132">One solution is to create a symlink to the Powershell installation directory that doesn't have spaces:</span></span>

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6"
     ```

     <span data-ttu-id="f552f-133">然後在子系統中輸入它：</span><span class="sxs-lookup"><span data-stu-id="f552f-133">and then enter it in the subsystem:</span></span>

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="f552f-134">選擇性啟用金鑰驗證</span><span class="sxs-lookup"><span data-stu-id="f552f-134">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

4. <span data-ttu-id="f552f-135">重新啟動 sshd 服務</span><span class="sxs-lookup"><span data-stu-id="f552f-135">Restart the sshd service</span></span>

   ```powershell
   Restart-Service sshd
   ```

5. <span data-ttu-id="f552f-136">將 OpenSSH 安裝所在的路徑新增至 Path 環境變數。</span><span class="sxs-lookup"><span data-stu-id="f552f-136">Add the path where OpenSSH is installed to your Path environment variable.</span></span> <span data-ttu-id="f552f-137">例如，`C:\Program Files\OpenSSH\`。</span><span class="sxs-lookup"><span data-stu-id="f552f-137">For example, `C:\Program Files\OpenSSH\`.</span></span> <span data-ttu-id="f552f-138">這個項目能夠允許程式找到 ssh.exe。</span><span class="sxs-lookup"><span data-stu-id="f552f-138">This entry allows for the ssh.exe to be found.</span></span>

## <a name="set-up-on-linux-ubuntu-1404-machine"></a><span data-ttu-id="f552f-139">在 Linux (Ubuntu 14.04) 電腦上進行安裝</span><span class="sxs-lookup"><span data-stu-id="f552f-139">Set up on Linux (Ubuntu 14.04) Machine</span></span>

1. <span data-ttu-id="f552f-140">安裝 GitHub 中的最新 [PowerShell Core for Linux](../setup/installing-powershell-core-on-linux.md#ubuntu-1404) 組建</span><span class="sxs-lookup"><span data-stu-id="f552f-140">Install the latest [PowerShell Core for Linux](../setup/installing-powershell-core-on-linux.md#ubuntu-1404) build from GitHub</span></span>
2. <span data-ttu-id="f552f-141">視需要安裝 [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html)</span><span class="sxs-lookup"><span data-stu-id="f552f-141">Install [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html) as needed</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. <span data-ttu-id="f552f-142">編輯 /etc/ssh 位置中的 sshd_config 檔案</span><span class="sxs-lookup"><span data-stu-id="f552f-142">Edit the sshd_config file at location /etc/ssh</span></span>

   - <span data-ttu-id="f552f-143">確定已啟用密碼驗證</span><span class="sxs-lookup"><span data-stu-id="f552f-143">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

   - <span data-ttu-id="f552f-144">新增 PowerShell 子系統項目</span><span class="sxs-lookup"><span data-stu-id="f552f-144">Add a PowerShell subsystem entry</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="f552f-145">選擇性啟用金鑰驗證</span><span class="sxs-lookup"><span data-stu-id="f552f-145">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

4. <span data-ttu-id="f552f-146">重新啟動 sshd 服務</span><span class="sxs-lookup"><span data-stu-id="f552f-146">Restart the sshd service</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-macos-machine"></a><span data-ttu-id="f552f-147">在 MacOS 電腦上進行安裝</span><span class="sxs-lookup"><span data-stu-id="f552f-147">Set up on MacOS Machine</span></span>

1. <span data-ttu-id="f552f-148">安裝最新 [PowerShell Core for MacOS](../setup/installing-powershell-core-on-macos.md) 組建</span><span class="sxs-lookup"><span data-stu-id="f552f-148">Install the latest [PowerShell Core for MacOS](../setup/installing-powershell-core-on-macos.md) build</span></span>

   - <span data-ttu-id="f552f-149">確定已遵循下列步驟來啟用 SSH 遠端：</span><span class="sxs-lookup"><span data-stu-id="f552f-149">Make sure SSH Remoting is enabled by following these steps:</span></span>
     - <span data-ttu-id="f552f-150">開啟 `System Preferences`</span><span class="sxs-lookup"><span data-stu-id="f552f-150">Open `System Preferences`</span></span>
     - <span data-ttu-id="f552f-151">按一下 `Sharing`</span><span class="sxs-lookup"><span data-stu-id="f552f-151">Click on `Sharing`</span></span>
     - <span data-ttu-id="f552f-152">檢查 `Remote Login` - 應該為 `Remote Login: On`</span><span class="sxs-lookup"><span data-stu-id="f552f-152">Check `Remote Login` - Should say `Remote Login: On`</span></span>
     - <span data-ttu-id="f552f-153">允許存取適當的使用者</span><span class="sxs-lookup"><span data-stu-id="f552f-153">Allow access to appropriate users</span></span>

2. <span data-ttu-id="f552f-154">編輯 `/private/etc/ssh/sshd_config` 位置中的 `sshd_config` 檔案</span><span class="sxs-lookup"><span data-stu-id="f552f-154">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>

   - <span data-ttu-id="f552f-155">使用您慣用的編輯器，或</span><span class="sxs-lookup"><span data-stu-id="f552f-155">Use your favorite editor or</span></span>

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - <span data-ttu-id="f552f-156">確定已啟用密碼驗證</span><span class="sxs-lookup"><span data-stu-id="f552f-156">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

   - <span data-ttu-id="f552f-157">新增 PowerShell 子系統項目</span><span class="sxs-lookup"><span data-stu-id="f552f-157">Add a PowerShell subsystem entry</span></span>

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="f552f-158">選擇性啟用金鑰驗證</span><span class="sxs-lookup"><span data-stu-id="f552f-158">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

3. <span data-ttu-id="f552f-159">重新啟動 sshd 服務</span><span class="sxs-lookup"><span data-stu-id="f552f-159">Restart the sshd service</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a><span data-ttu-id="f552f-160">驗證</span><span class="sxs-lookup"><span data-stu-id="f552f-160">Authentication</span></span>

<span data-ttu-id="f552f-161">透過 SSH 的 PowerShell 遠端功能需要在 SSH 用戶端與 SSH 服務之間交換驗證，本身並不會實作任何驗證配置。</span><span class="sxs-lookup"><span data-stu-id="f552f-161">PowerShell remoting over SSH relies on the authentication exchange between the SSH client and SSH service and does not implement any authentication schemes itself.</span></span>
<span data-ttu-id="f552f-162">這表示任何已設定的驗證配置 (包括多重要素驗證) 都是由 SSH 處理，與 PowerShell 無關。</span><span class="sxs-lookup"><span data-stu-id="f552f-162">This means that any configured authentication schemes including multi-factor authentication is handled by SSH and independent of PowerShell.</span></span>
<span data-ttu-id="f552f-163">例如，您可以設定 SSH 服務要求公開金鑰驗證及單次密碼來增強安全性。</span><span class="sxs-lookup"><span data-stu-id="f552f-163">For example, you can configure the SSH service to require public key authentication as well as a one-time password for added security.</span></span>
<span data-ttu-id="f552f-164">設定多重要素驗證不在本文件的討論範圍內。</span><span class="sxs-lookup"><span data-stu-id="f552f-164">Configuration of multi-factor authentication is outside the scope of this documentation.</span></span>
<span data-ttu-id="f552f-165">請參閱 SSH 文件，以了解如何正確地設定多重要素驗證，並驗證它在 PowerShell 之外是否運作正常，再嘗試與 PowerShell 遠端功能搭配使用。</span><span class="sxs-lookup"><span data-stu-id="f552f-165">Refer to documentation for SSH on how to correctly configure multi-factor authentication and validate it works outside of PowerShell before attempting to use it with PowerShell remoting.</span></span>

## <a name="powershell-remoting-example"></a><span data-ttu-id="f552f-166">PowerShell 遠端範例</span><span class="sxs-lookup"><span data-stu-id="f552f-166">PowerShell Remoting Example</span></span>

<span data-ttu-id="f552f-167">測試遠端功能的最簡單方式是在單一電腦上進行試用。</span><span class="sxs-lookup"><span data-stu-id="f552f-167">The easiest way to test remoting is to try it on a single machine.</span></span> <span data-ttu-id="f552f-168">在此範例中，我們會建立回到相同 Linux 電腦的遠端工作階段。</span><span class="sxs-lookup"><span data-stu-id="f552f-168">In this example, we create a remote session back to the same Linux machine.</span></span> <span data-ttu-id="f552f-169">我們會以互動方式使用 PowerShell Cmdlet，因此，我們會看到要求驗證主機電腦的 SSH 提示以及密碼提示。</span><span class="sxs-lookup"><span data-stu-id="f552f-169">We are using PowerShell cmdlets interactively so we see prompts from SSH asking to verify the host computer and prompting for a password.</span></span> <span data-ttu-id="f552f-170">您可以在 Windows 電腦上執行相同的動作以確保遠端功能正在運作。</span><span class="sxs-lookup"><span data-stu-id="f552f-170">You can do the same thing on a Windows machine to ensure remoting is working.</span></span> <span data-ttu-id="f552f-171">接著，透過變更主機名稱，在電腦之間執行遠端功能。</span><span class="sxs-lookup"><span data-stu-id="f552f-171">Then remote between machines by changing the host name.</span></span>

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

### <a name="known-issues"></a><span data-ttu-id="f552f-172">已知問題</span><span class="sxs-lookup"><span data-stu-id="f552f-172">Known Issues</span></span>

<span data-ttu-id="f552f-173">sudo 命令不適用於連至 Linux 電腦的遠端工作階段。</span><span class="sxs-lookup"><span data-stu-id="f552f-173">The sudo command doesn't work in remote session to Linux machine.</span></span>

## <a name="see-also"></a><span data-ttu-id="f552f-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f552f-174">See Also</span></span>

[<span data-ttu-id="f552f-175">PowerShell Core for Windows</span><span class="sxs-lookup"><span data-stu-id="f552f-175">PowerShell Core for Windows</span></span>](../setup/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="f552f-176">PowerShell Core for Linux</span><span class="sxs-lookup"><span data-stu-id="f552f-176">PowerShell Core for Linux</span></span>](../setup/installing-powershell-core-on-linux.md#ubuntu-1404)

[<span data-ttu-id="f552f-177">PowerShell Core for MacOS</span><span class="sxs-lookup"><span data-stu-id="f552f-177">PowerShell Core for MacOS</span></span>](../setup/installing-powershell-core-on-macos.md)

[<span data-ttu-id="f552f-178">Win32 OpenSSH</span><span class="sxs-lookup"><span data-stu-id="f552f-178">Win32 OpenSSH</span></span>](https://github.com/PowerShell/Win32-OpenSSH/releases)

[<span data-ttu-id="f552f-179">Ubuntu SSH</span><span class="sxs-lookup"><span data-stu-id="f552f-179">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
