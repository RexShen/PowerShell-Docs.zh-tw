---
title: 透過 SSH 的 PowerShell 遠端處理
description: 使用 SSH 在 PowerShell Core 中遠端
ms.date: 08/14/2018
ms.openlocfilehash: b5c6bd70841e270c2c128601612c07af9d9aa6e4
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655288"
---
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="3f59b-103">透過 SSH 的 PowerShell 遠端處理</span><span class="sxs-lookup"><span data-stu-id="3f59b-103">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="3f59b-104">概觀</span><span class="sxs-lookup"><span data-stu-id="3f59b-104">Overview</span></span>

<span data-ttu-id="3f59b-105">PowerShell 遠端通常會使用 WinRM 進行連線交涉和資料傳輸。</span><span class="sxs-lookup"><span data-stu-id="3f59b-105">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span> <span data-ttu-id="3f59b-106">SSH 目前適用於 Linux 與 Windows 平台，而且能夠執行真正的多平台 PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="3f59b-106">SSH is now available for Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>

<span data-ttu-id="3f59b-107">WinRM 提供一個健全裝載模型以供 PowerShell 遠端工作階段使用。</span><span class="sxs-lookup"><span data-stu-id="3f59b-107">WinRM provides a robust hosting model for PowerShell remote sessions.</span></span> <span data-ttu-id="3f59b-108">SSH 型遠端功能目前不支援遠端端點設定和 JEA (Just Enough Administration)。</span><span class="sxs-lookup"><span data-stu-id="3f59b-108">SSH-based remoting doesn't currently support remote endpoint configuration and JEA (Just Enough Administration).</span></span>

<span data-ttu-id="3f59b-109">SSH 遠端功能可讓您在 Windows 與 Linux 電腦之間執行基本 PowerShell 工作階段遠端功能。</span><span class="sxs-lookup"><span data-stu-id="3f59b-109">SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span> <span data-ttu-id="3f59b-110">SSH 遠端功能會在目標電腦上建立 PowerShell 裝載處理序作為 SSH 子系統。</span><span class="sxs-lookup"><span data-stu-id="3f59b-110">SSH Remoting creates a PowerShell host process on the target machine as an SSH subsystem.</span></span>
<span data-ttu-id="3f59b-111">最後，我們將實作一般裝載模型 (類似 WinRM) 以支援端點設定與 JEA。</span><span class="sxs-lookup"><span data-stu-id="3f59b-111">Eventually we'll implement a general hosting model, similar to WinRM, to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="3f59b-112">`New-PSSession`、`Enter-PSSession` 與 `Invoke-Command` Cmdlet 現在有新的參數集，可支援這個新的遠端連線。</span><span class="sxs-lookup"><span data-stu-id="3f59b-112">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets now have a new parameter set to support this new remoting connection.</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="3f59b-113">若要建立遠端工作階段，您可以使用 `HostName` 參數來指定目標電腦，並使用 `UserName` 來提供使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="3f59b-113">To create a remote session, you specify the target machine with the `HostName` parameter and provide the user name with `UserName`.</span></span> <span data-ttu-id="3f59b-114">以互動方式執行 Cmdlet 時，系統會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="3f59b-114">When running the cmdlets interactively, you're prompted for a password.</span></span> <span data-ttu-id="3f59b-115">您也可以搭配 `KeyFilePath` 參數使用私密金鑰檔案，來使用 SSH 金鑰驗證。</span><span class="sxs-lookup"><span data-stu-id="3f59b-115">You can also, use SSH key authentication using a private key file with the `KeyFilePath` parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="3f59b-116">一般安裝資訊</span><span class="sxs-lookup"><span data-stu-id="3f59b-116">General setup information</span></span>

<span data-ttu-id="3f59b-117">SSH 必須安裝在所有電腦上。</span><span class="sxs-lookup"><span data-stu-id="3f59b-117">SSH must be installed on all machines.</span></span> <span data-ttu-id="3f59b-118">請同時安裝 SSH 用戶端 (`ssh.exe`) 與伺服器 (`sshd.exe`)，讓您可從遠端往返電腦。</span><span class="sxs-lookup"><span data-stu-id="3f59b-118">Install both the SSH client (`ssh.exe`) and server (`sshd.exe`) so that you can remote to and from the machines.</span></span> <span data-ttu-id="3f59b-119">適用於 Windows 10 組建 1809年和 Windows Server 2019 的現在 OpenSSH for Windows。</span><span class="sxs-lookup"><span data-stu-id="3f59b-119">OpenSSH for Windows is now availabe in Windows 10 build 1809 and Windows Server 2019.</span></span> <span data-ttu-id="3f59b-120">如需詳細資訊，請參閱 < [OpenSSH 的 Windows](/windows-server/administration/openssh/openssh_overview)。</span><span class="sxs-lookup"><span data-stu-id="3f59b-120">For more information, see [OpenSSH for Windows](/windows-server/administration/openssh/openssh_overview).</span></span> <span data-ttu-id="3f59b-121">針對 Linux，安裝您平台適用的 SSH (包括 sshd 伺服器)。</span><span class="sxs-lookup"><span data-stu-id="3f59b-121">For Linux, install SSH (including sshd server) appropriate to your platform.</span></span> <span data-ttu-id="3f59b-122">您也需要從 GitHub 安裝 PowerShell Core 來取得 SSH 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="3f59b-122">You also need to install PowerShell Core from GitHub to get the SSH remoting feature.</span></span> <span data-ttu-id="3f59b-123">SSH 伺服器必須設定為建立 SSH 子系統，以便在遠端電腦上裝載 PowerShell 處理序。</span><span class="sxs-lookup"><span data-stu-id="3f59b-123">The SSH server must be configured to create an SSH subsystem to host a PowerShell process on the remote machine.</span></span> <span data-ttu-id="3f59b-124">您也必須設定啟用密碼或以金鑰為基礎的驗證。</span><span class="sxs-lookup"><span data-stu-id="3f59b-124">You also must configure enable password or key-based authentication.</span></span>

## <a name="set-up-on-windows-machine"></a><span data-ttu-id="3f59b-125">在 Windows 電腦上進行安裝</span><span class="sxs-lookup"><span data-stu-id="3f59b-125">Set up on Windows Machine</span></span>

1. <span data-ttu-id="3f59b-126">最新 [PowerShell Core for Windows](../../install/installing-powershell-core-on-windows.md#msi) 版本</span><span class="sxs-lookup"><span data-stu-id="3f59b-126">Install the latest version of [PowerShell Core for Windows](../../install/installing-powershell-core-on-windows.md#msi)</span></span>

   - <span data-ttu-id="3f59b-127">您可以查看針對 `New-PSSession` 所設定的參數，得知它是否具有 SSH 遠端支援</span><span class="sxs-lookup"><span data-stu-id="3f59b-127">You can tell if it has the SSH remoting support by looking at the parameter sets for `New-PSSession`</span></span>

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. <span data-ttu-id="3f59b-128">安裝最新的 Win32 OpenSSH。</span><span class="sxs-lookup"><span data-stu-id="3f59b-128">Install the latest Win32 OpenSSH.</span></span> <span data-ttu-id="3f59b-129">如需安裝指示，請參閱[安裝的 OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse)。</span><span class="sxs-lookup"><span data-stu-id="3f59b-129">For installation instructions, see [Installation of OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).</span></span>
3. <span data-ttu-id="3f59b-130">編輯`sshd_config`位於檔案`%ProgramData%\ssh`。</span><span class="sxs-lookup"><span data-stu-id="3f59b-130">Edit the `sshd_config` file located at `%ProgramData%\ssh`.</span></span>

   - <span data-ttu-id="3f59b-131">確定已啟用密碼驗證</span><span class="sxs-lookup"><span data-stu-id="3f59b-131">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > <span data-ttu-id="3f59b-132">OpenSSH for Windows 中有一個錯 Bug，會讓空格無法在子系統可執行檔路徑中運作。</span><span class="sxs-lookup"><span data-stu-id="3f59b-132">There is a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span> <span data-ttu-id="3f59b-133">如需詳細資訊，請參閱[這個 GitHub 問題](https://github.com/PowerShell/Win32-OpenSSH/issues/784) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="3f59b-133">For more information, see [this GitHub issue](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>

     <span data-ttu-id="3f59b-134">解決方案之一是建立未包含空格之 PowerShell 安裝目錄的符號連結：</span><span class="sxs-lookup"><span data-stu-id="3f59b-134">One solution is to create a symlink to the Powershell installation directory that doesn't have spaces:</span></span>

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6"
     ```

     <span data-ttu-id="3f59b-135">然後在子系統中輸入它：</span><span class="sxs-lookup"><span data-stu-id="3f59b-135">and then enter it in the subsystem:</span></span>

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="3f59b-136">選擇性啟用金鑰驗證</span><span class="sxs-lookup"><span data-stu-id="3f59b-136">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

4. <span data-ttu-id="3f59b-137">重新啟動 sshd 服務</span><span class="sxs-lookup"><span data-stu-id="3f59b-137">Restart the sshd service</span></span>

   ```powershell
   Restart-Service sshd
   ```

5. <span data-ttu-id="3f59b-138">將 OpenSSH 安裝所在的路徑新增至 Path 環境變數。</span><span class="sxs-lookup"><span data-stu-id="3f59b-138">Add the path where OpenSSH is installed to your Path environment variable.</span></span> <span data-ttu-id="3f59b-139">例如，`C:\Program Files\OpenSSH\`。</span><span class="sxs-lookup"><span data-stu-id="3f59b-139">For example, `C:\Program Files\OpenSSH\`.</span></span> <span data-ttu-id="3f59b-140">這個項目能夠允許程式找到 ssh.exe。</span><span class="sxs-lookup"><span data-stu-id="3f59b-140">This entry allows for the ssh.exe to be found.</span></span>

## <a name="set-up-on-linux-ubuntu-1404-machine"></a><span data-ttu-id="3f59b-141">在 Linux (Ubuntu 14.04) 電腦上進行安裝</span><span class="sxs-lookup"><span data-stu-id="3f59b-141">Set up on Linux (Ubuntu 14.04) Machine</span></span>

1. <span data-ttu-id="3f59b-142">安裝 GitHub 中的最新 [PowerShell Core for Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1404) 組建</span><span class="sxs-lookup"><span data-stu-id="3f59b-142">Install the latest [PowerShell Core for Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1404) build from GitHub</span></span>
2. <span data-ttu-id="3f59b-143">視需要安裝 [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html)</span><span class="sxs-lookup"><span data-stu-id="3f59b-143">Install [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html) as needed</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. <span data-ttu-id="3f59b-144">編輯 /etc/ssh 位置中的 sshd_config 檔案</span><span class="sxs-lookup"><span data-stu-id="3f59b-144">Edit the sshd_config file at location /etc/ssh</span></span>

   - <span data-ttu-id="3f59b-145">確定已啟用密碼驗證</span><span class="sxs-lookup"><span data-stu-id="3f59b-145">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

   - <span data-ttu-id="3f59b-146">新增 PowerShell 子系統項目</span><span class="sxs-lookup"><span data-stu-id="3f59b-146">Add a PowerShell subsystem entry</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="3f59b-147">選擇性啟用金鑰驗證</span><span class="sxs-lookup"><span data-stu-id="3f59b-147">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

4. <span data-ttu-id="3f59b-148">重新啟動 sshd 服務</span><span class="sxs-lookup"><span data-stu-id="3f59b-148">Restart the sshd service</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-macos-machine"></a><span data-ttu-id="3f59b-149">在 MacOS 電腦上進行安裝</span><span class="sxs-lookup"><span data-stu-id="3f59b-149">Set up on MacOS Machine</span></span>

1. <span data-ttu-id="3f59b-150">安裝最新 [PowerShell Core for MacOS](../../install/installing-powershell-core-on-macos.md) 組建</span><span class="sxs-lookup"><span data-stu-id="3f59b-150">Install the latest [PowerShell Core for MacOS](../../install/installing-powershell-core-on-macos.md) build</span></span>

   - <span data-ttu-id="3f59b-151">確定已遵循下列步驟來啟用 SSH 遠端：</span><span class="sxs-lookup"><span data-stu-id="3f59b-151">Make sure SSH Remoting is enabled by following these steps:</span></span>
     - <span data-ttu-id="3f59b-152">開啟 `System Preferences`</span><span class="sxs-lookup"><span data-stu-id="3f59b-152">Open `System Preferences`</span></span>
     - <span data-ttu-id="3f59b-153">按一下 `Sharing`</span><span class="sxs-lookup"><span data-stu-id="3f59b-153">Click on `Sharing`</span></span>
     - <span data-ttu-id="3f59b-154">檢查 `Remote Login` - 應該為 `Remote Login: On`</span><span class="sxs-lookup"><span data-stu-id="3f59b-154">Check `Remote Login` - Should say `Remote Login: On`</span></span>
     - <span data-ttu-id="3f59b-155">允許存取適當的使用者</span><span class="sxs-lookup"><span data-stu-id="3f59b-155">Allow access to appropriate users</span></span>

2. <span data-ttu-id="3f59b-156">編輯 `/private/etc/ssh/sshd_config` 位置中的 `sshd_config` 檔案</span><span class="sxs-lookup"><span data-stu-id="3f59b-156">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>

   - <span data-ttu-id="3f59b-157">使用您慣用的編輯器，或</span><span class="sxs-lookup"><span data-stu-id="3f59b-157">Use your favorite editor or</span></span>

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - <span data-ttu-id="3f59b-158">確定已啟用密碼驗證</span><span class="sxs-lookup"><span data-stu-id="3f59b-158">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

   - <span data-ttu-id="3f59b-159">新增 PowerShell 子系統項目</span><span class="sxs-lookup"><span data-stu-id="3f59b-159">Add a PowerShell subsystem entry</span></span>

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="3f59b-160">選擇性啟用金鑰驗證</span><span class="sxs-lookup"><span data-stu-id="3f59b-160">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

3. <span data-ttu-id="3f59b-161">重新啟動 sshd 服務</span><span class="sxs-lookup"><span data-stu-id="3f59b-161">Restart the sshd service</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a><span data-ttu-id="3f59b-162">驗證</span><span class="sxs-lookup"><span data-stu-id="3f59b-162">Authentication</span></span>

<span data-ttu-id="3f59b-163">透過 SSH 的 PowerShell 遠端功能需要在 SSH 用戶端與 SSH 服務之間交換驗證，本身並不會實作任何驗證配置。</span><span class="sxs-lookup"><span data-stu-id="3f59b-163">PowerShell remoting over SSH relies on the authentication exchange between the SSH client and SSH service and does not implement any authentication schemes itself.</span></span>
<span data-ttu-id="3f59b-164">這表示任何已設定的驗證配置 (包括多重要素驗證) 都是由 SSH 處理，與 PowerShell 無關。</span><span class="sxs-lookup"><span data-stu-id="3f59b-164">This means that any configured authentication schemes including multi-factor authentication is handled by SSH and independent of PowerShell.</span></span>
<span data-ttu-id="3f59b-165">例如，您可以設定 SSH 服務要求公開金鑰驗證及單次密碼來增強安全性。</span><span class="sxs-lookup"><span data-stu-id="3f59b-165">For example, you can configure the SSH service to require public key authentication as well as a one-time password for added security.</span></span>
<span data-ttu-id="3f59b-166">設定多重要素驗證不在本文件的討論範圍內。</span><span class="sxs-lookup"><span data-stu-id="3f59b-166">Configuration of multi-factor authentication is outside the scope of this documentation.</span></span>
<span data-ttu-id="3f59b-167">請參閱 SSH 文件，以了解如何正確地設定多重要素驗證，並驗證它在 PowerShell 之外是否運作正常，再嘗試與 PowerShell 遠端功能搭配使用。</span><span class="sxs-lookup"><span data-stu-id="3f59b-167">Refer to documentation for SSH on how to correctly configure multi-factor authentication and validate it works outside of PowerShell before attempting to use it with PowerShell remoting.</span></span>

## <a name="powershell-remoting-example"></a><span data-ttu-id="3f59b-168">PowerShell 遠端範例</span><span class="sxs-lookup"><span data-stu-id="3f59b-168">PowerShell Remoting Example</span></span>

<span data-ttu-id="3f59b-169">測試遠端功能的最簡單方式是在單一電腦上進行試用。</span><span class="sxs-lookup"><span data-stu-id="3f59b-169">The easiest way to test remoting is to try it on a single machine.</span></span> <span data-ttu-id="3f59b-170">在此範例中，我們會建立回到相同 Linux 電腦的遠端工作階段。</span><span class="sxs-lookup"><span data-stu-id="3f59b-170">In this example, we create a remote session back to the same Linux machine.</span></span> <span data-ttu-id="3f59b-171">我們會以互動方式使用 PowerShell Cmdlet，因此，我們會看到要求驗證主機電腦的 SSH 提示以及密碼提示。</span><span class="sxs-lookup"><span data-stu-id="3f59b-171">We are using PowerShell cmdlets interactively so we see prompts from SSH asking to verify the host computer and prompting for a password.</span></span> <span data-ttu-id="3f59b-172">您可以在 Windows 電腦上執行相同的動作以確保遠端功能正在運作。</span><span class="sxs-lookup"><span data-stu-id="3f59b-172">You can do the same thing on a Windows machine to ensure remoting is working.</span></span> <span data-ttu-id="3f59b-173">接著，透過變更主機名稱，在電腦之間執行遠端功能。</span><span class="sxs-lookup"><span data-stu-id="3f59b-173">Then remote between machines by changing the host name.</span></span>

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

### <a name="known-issues"></a><span data-ttu-id="3f59b-174">已知問題</span><span class="sxs-lookup"><span data-stu-id="3f59b-174">Known Issues</span></span>

<span data-ttu-id="3f59b-175">sudo 命令不適用於連至 Linux 電腦的遠端工作階段。</span><span class="sxs-lookup"><span data-stu-id="3f59b-175">The sudo command doesn't work in remote session to Linux machine.</span></span>

## <a name="see-also"></a><span data-ttu-id="3f59b-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f59b-176">See Also</span></span>

[<span data-ttu-id="3f59b-177">PowerShell Core for Windows</span><span class="sxs-lookup"><span data-stu-id="3f59b-177">PowerShell Core for Windows</span></span>](../../install/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="3f59b-178">PowerShell Core for Linux</span><span class="sxs-lookup"><span data-stu-id="3f59b-178">PowerShell Core for Linux</span></span>](../../install/installing-powershell-core-on-linux.md#ubuntu-1404)

[<span data-ttu-id="3f59b-179">PowerShell Core for MacOS</span><span class="sxs-lookup"><span data-stu-id="3f59b-179">PowerShell Core for MacOS</span></span>](../../install/installing-powershell-core-on-macos.md)

[<span data-ttu-id="3f59b-180">Windows 的 OpenSSH</span><span class="sxs-lookup"><span data-stu-id="3f59b-180">OpenSSH for Windows</span></span>](/windows-server/administration/openssh/openssh_overview)

[<span data-ttu-id="3f59b-181">Ubuntu SSH</span><span class="sxs-lookup"><span data-stu-id="3f59b-181">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
