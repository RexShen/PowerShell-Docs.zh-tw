
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="4b413-101">透過 SSH 的 PowerShell 遠端處理</span><span class="sxs-lookup"><span data-stu-id="4b413-101">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="4b413-102">概觀</span><span class="sxs-lookup"><span data-stu-id="4b413-102">Overview</span></span>

<span data-ttu-id="4b413-103">PowerShell 遠端通常會使用 WinRM 進行連線交涉和資料傳輸。</span><span class="sxs-lookup"><span data-stu-id="4b413-103">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span> <span data-ttu-id="4b413-104">已選擇 SSH 進行此遠端實作，因為它現在適用於 Linux 和 Windows 平台，並允許真正多平台 PowerShell 遠端。</span><span class="sxs-lookup"><span data-stu-id="4b413-104">SSH was chosen for this remoting implementation since it is now available for both Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span> <span data-ttu-id="4b413-105">不過，WinRM 也提供穩固的裝載模型，來進行這項實作尚未執行的 PowerShell 遠端工作階段。</span><span class="sxs-lookup"><span data-stu-id="4b413-105">However, WinRM also provides a robust hosting model for PowerShell remote sessions which this implementation does not yet do.</span></span> <span data-ttu-id="4b413-106">這表示，這項實作尚未支援 PowerShell 遠端端點設定和 JEA (Just Enough Administration)。</span><span class="sxs-lookup"><span data-stu-id="4b413-106">And this means that PowerShell remote endpoint configuration and JEA (Just Enough Administration) is not yet supported in this implementation.</span></span>

<span data-ttu-id="4b413-107">PowerShell SSH 遠端可讓您在 Windows 與 Linux 電腦之間執行基本 PowerShell 工作階段遠端。</span><span class="sxs-lookup"><span data-stu-id="4b413-107">PowerShell SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span> <span data-ttu-id="4b413-108">做法是在目標電腦上建立 PowerShell 裝載處理序作為 SSH 子系統。</span><span class="sxs-lookup"><span data-stu-id="4b413-108">This is done by creating a PowerShell hosting process on the target machine as an SSH subsystem.</span></span> <span data-ttu-id="4b413-109">最終，這會變更為與 WinRM 運作方式類似的更一般裝載模型，以支援端點設定和 JEA。</span><span class="sxs-lookup"><span data-stu-id="4b413-109">Eventually this will be changed to a more general hosting model similar to how WinRM works in order to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="4b413-110">`New-PSSession`、`Enter-PSSession` 和 `Invoke-Command` Cmdlet 現在有新的參數集，可方便進行這個新的遠端連線</span><span class="sxs-lookup"><span data-stu-id="4b413-110">The `New-PSSession`, `Enter-PSSession` and `Invoke-Command` cmdlets now have a new parameter set to facilitate this new remoting connection</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="4b413-111">這個新的參數集很可能會變更，但現在可讓您建立 SSH PSSession，以從命令列與之互動或在其上叫用命令和指令碼。</span><span class="sxs-lookup"><span data-stu-id="4b413-111">This new parameter set will likely change but for now allows you to create SSH PSSessions that you can interact with from the command line or invoke commands and scripts on.</span></span> <span data-ttu-id="4b413-112">您可以使用 HostName 參數指定目標電腦，並使用 UserName 來提供使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="4b413-112">You specify the target machine with the HostName parameter and provide the user name with UserName.</span></span> <span data-ttu-id="4b413-113">在 PowerShell 命令列以互動方式執行 Cmdlet 時，系統會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="4b413-113">When running the cmdlets interactively at the PowerShell command line you will be prompted for a password.</span></span> <span data-ttu-id="4b413-114">但是，您也可以選擇使用 SSH 金鑰驗證，並使用 KeyFilePath 參數提供私密金鑰檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="4b413-114">But you also have the option to use SSH key authentication and provide a private key file path with the KeyFilePath parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="4b413-115">一般安裝資訊</span><span class="sxs-lookup"><span data-stu-id="4b413-115">General setup information</span></span>

<span data-ttu-id="4b413-116">需要有 SSH 才能安裝在所有電腦上。</span><span class="sxs-lookup"><span data-stu-id="4b413-116">SSH is required to be installed on all machines.</span></span> <span data-ttu-id="4b413-117">您應該同時安裝用戶端 (`ssh.exe`) 和伺服器 (`sshd.exe`)，讓您可以試驗往返電腦的遠端執行。</span><span class="sxs-lookup"><span data-stu-id="4b413-117">You should install both client (`ssh.exe`) and server (`sshd.exe`) so that you can experiment with remoting to and from the machines.</span></span> <span data-ttu-id="4b413-118">針對 Windows，您需要[從 GitHub 安裝 Win32 OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/releases)。</span><span class="sxs-lookup"><span data-stu-id="4b413-118">For Windows you will need to install [Win32 OpenSSH from GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span></span>
<span data-ttu-id="4b413-119">針對 Linux，您需要安裝您平台適用的 SSH (包含 sshd 伺服器)。</span><span class="sxs-lookup"><span data-stu-id="4b413-119">For Linux you will need to install SSH (including sshd server) appropriate to your platform.</span></span> <span data-ttu-id="4b413-120">您也需要來自 GitHub 且具有 SSH 遠端功能的新 PowerShell 組建或套件。</span><span class="sxs-lookup"><span data-stu-id="4b413-120">You will also need a recent PowerShell build or package from GitHub having the SSH remoting feature.</span></span>
<span data-ttu-id="4b413-121">SSH 子系統用來在遠端電腦上建立 PowerShell 處理序，因此需要設定 SSH 伺服器。</span><span class="sxs-lookup"><span data-stu-id="4b413-121">SSH subsystems is used to establish a PowerShell process on the remote machine and the SSH server will need to be configured for that.</span></span> <span data-ttu-id="4b413-122">此外，您必須啟用密碼驗證，以及選擇性地啟用金鑰型驗證。</span><span class="sxs-lookup"><span data-stu-id="4b413-122">In addition you will need to enable password authentication and optionally key based authentication.</span></span>

## <a name="setup-on-windows-machine"></a><span data-ttu-id="4b413-123">Windows 電腦上的安裝</span><span class="sxs-lookup"><span data-stu-id="4b413-123">Setup on Windows Machine</span></span>

1. <span data-ttu-id="4b413-124">安裝最新的 [PowerShell Core for Windows] 版本</span><span class="sxs-lookup"><span data-stu-id="4b413-124">Install the latest version of [PowerShell Core for Windows]</span></span>

   - <span data-ttu-id="4b413-125">您可以查看針對 `New-PSSession` 所設定的參數，得知它是否具有 SSH 遠端支援</span><span class="sxs-lookup"><span data-stu-id="4b413-125">You can tell if it has the SSH remoting support by looking at the parameter sets for `New-PSSession`</span></span>

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. <span data-ttu-id="4b413-126">使用 [安裝] 指示，安裝 GitHub 中最新的 [Win32 OpenSSH] 組建</span><span class="sxs-lookup"><span data-stu-id="4b413-126">Install the latest [Win32 OpenSSH] build from GitHub using the [installation] instructions</span></span>
3. <span data-ttu-id="4b413-127">編輯 Win32 OpenSSH 所安裝位置中的 sshd_config 檔案</span><span class="sxs-lookup"><span data-stu-id="4b413-127">Edit the sshd_config file at the location where you installed Win32 OpenSSH</span></span>

   - <span data-ttu-id="4b413-128">確定已啟用密碼驗證</span><span class="sxs-lookup"><span data-stu-id="4b413-128">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > <span data-ttu-id="4b413-129">OpenSSH for Windows 中有一個錯 Bug，會讓空格無法在子系統可執行檔路徑中運作。</span><span class="sxs-lookup"><span data-stu-id="4b413-129">There is a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span>
     > <span data-ttu-id="4b413-130">請參閱 [GitHub 上的這個問題來取得詳細資訊](https://github.com/PowerShell/Win32-OpenSSH/issues/784)。</span><span class="sxs-lookup"><span data-stu-id="4b413-130">See [this issue on GitHub for more information](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>

     <span data-ttu-id="4b413-131">其中一種解決方案是建立未包含空格之 Powershell 安裝目錄的符號連結：</span><span class="sxs-lookup"><span data-stu-id="4b413-131">One solution is to create a symlink to the Powershell installation directory that does not contain spaces:</span></span>

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6.0.0"
     ```

     <span data-ttu-id="4b413-132">然後在子系統中輸入它：</span><span class="sxs-lookup"><span data-stu-id="4b413-132">and then enter it in the subsystem:</span></span>

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="4b413-133">選擇性啟用金鑰驗證</span><span class="sxs-lookup"><span data-stu-id="4b413-133">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

4. <span data-ttu-id="4b413-134">重新啟動 sshd 服務</span><span class="sxs-lookup"><span data-stu-id="4b413-134">Restart the sshd service</span></span>

   ```powershell
   Restart-Service sshd
   ```

5. <span data-ttu-id="4b413-135">將安裝 OpenSSH 的路徑新增至路徑環境變數</span><span class="sxs-lookup"><span data-stu-id="4b413-135">Add the path where OpenSSH is installed to your Path Env Variable</span></span>

   - <span data-ttu-id="4b413-136">這應該是與 `C:\Program Files\OpenSSH\` 行一起</span><span class="sxs-lookup"><span data-stu-id="4b413-136">This should be along the lines of `C:\Program Files\OpenSSH\`</span></span>
   - <span data-ttu-id="4b413-137">這樣可以找到 ssh.exe</span><span class="sxs-lookup"><span data-stu-id="4b413-137">This allows for the ssh.exe to be found</span></span>

## <a name="setup-on-linux-ubuntu-1404-machine"></a><span data-ttu-id="4b413-138">Linux (Ubuntu 14.04) 電腦上的安裝</span><span class="sxs-lookup"><span data-stu-id="4b413-138">Setup on Linux (Ubuntu 14.04) Machine</span></span>

1. <span data-ttu-id="4b413-139">安裝 GitHub 中最新的 [PowerShell Core for Linux] 組建</span><span class="sxs-lookup"><span data-stu-id="4b413-139">Install the latest [PowerShell Core for Linux] build from GitHub</span></span>
2. <span data-ttu-id="4b413-140">視需要安裝 [Ubuntu SSH]</span><span class="sxs-lookup"><span data-stu-id="4b413-140">Install [Ubuntu SSH] as needed</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. <span data-ttu-id="4b413-141">編輯 /etc/ssh 位置中的 sshd_config 檔案</span><span class="sxs-lookup"><span data-stu-id="4b413-141">Edit the sshd_config file at location /etc/ssh</span></span>

   - <span data-ttu-id="4b413-142">確定已啟用密碼驗證</span><span class="sxs-lookup"><span data-stu-id="4b413-142">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

   - <span data-ttu-id="4b413-143">新增 PowerShell 子系統項目</span><span class="sxs-lookup"><span data-stu-id="4b413-143">Add a PowerShell subsystem entry</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="4b413-144">選擇性啟用金鑰驗證</span><span class="sxs-lookup"><span data-stu-id="4b413-144">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

4. <span data-ttu-id="4b413-145">重新啟動 sshd 服務</span><span class="sxs-lookup"><span data-stu-id="4b413-145">Restart the sshd service</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="setup-on-macos-machine"></a><span data-ttu-id="4b413-146">MacOS 電腦上的安裝</span><span class="sxs-lookup"><span data-stu-id="4b413-146">Setup on MacOS Machine</span></span>

1. <span data-ttu-id="4b413-147">安裝最新的 [PowerShell Core for MacOS] 組建</span><span class="sxs-lookup"><span data-stu-id="4b413-147">Install the latest [PowerShell Core for MacOS] build</span></span>

   - <span data-ttu-id="4b413-148">確定已遵循下列步驟來啟用 SSH 遠端：</span><span class="sxs-lookup"><span data-stu-id="4b413-148">Make sure SSH Remoting is enabled by following these steps:</span></span>
     - <span data-ttu-id="4b413-149">開啟 `System Preferences`</span><span class="sxs-lookup"><span data-stu-id="4b413-149">Open `System Preferences`</span></span>
     - <span data-ttu-id="4b413-150">按一下 `Sharing`</span><span class="sxs-lookup"><span data-stu-id="4b413-150">Click on `Sharing`</span></span>
     - <span data-ttu-id="4b413-151">檢查 `Remote Login` - 應該為 `Remote Login: On`</span><span class="sxs-lookup"><span data-stu-id="4b413-151">Check `Remote Login` - Should say `Remote Login: On`</span></span>
     - <span data-ttu-id="4b413-152">允許存取適當的使用者</span><span class="sxs-lookup"><span data-stu-id="4b413-152">Allow access to appropriate users</span></span>

2. <span data-ttu-id="4b413-153">編輯 `/private/etc/ssh/sshd_config` 位置中的 `sshd_config` 檔案</span><span class="sxs-lookup"><span data-stu-id="4b413-153">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>

   - <span data-ttu-id="4b413-154">使用您慣用的編輯器，或</span><span class="sxs-lookup"><span data-stu-id="4b413-154">Use your favorite editor or</span></span>

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - <span data-ttu-id="4b413-155">確定已啟用密碼驗證</span><span class="sxs-lookup"><span data-stu-id="4b413-155">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

   - <span data-ttu-id="4b413-156">新增 PowerShell 子系統項目</span><span class="sxs-lookup"><span data-stu-id="4b413-156">Add a PowerShell subsystem entry</span></span>

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="4b413-157">選擇性啟用金鑰驗證</span><span class="sxs-lookup"><span data-stu-id="4b413-157">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

3. <span data-ttu-id="4b413-158">重新啟動 sshd 服務</span><span class="sxs-lookup"><span data-stu-id="4b413-158">Restart the sshd service</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="powershell-remoting-example"></a><span data-ttu-id="4b413-159">PowerShell 遠端範例</span><span class="sxs-lookup"><span data-stu-id="4b413-159">PowerShell Remoting Example</span></span>

<span data-ttu-id="4b413-160">測試遠端功能的最簡單方式是只在單一電腦上試用。</span><span class="sxs-lookup"><span data-stu-id="4b413-160">The easiest way to test remoting is to just try it on a single machine.</span></span> <span data-ttu-id="4b413-161">我將在這裡建立回到 Linux 方塊上相同電腦的遠端工作階段。</span><span class="sxs-lookup"><span data-stu-id="4b413-161">Here I will create a remote session back to the same machine on a Linux box.</span></span> <span data-ttu-id="4b413-162">請注意，我將會從命令提示字元使用 PowerShell Cmdlet，因此我們會看到要求驗證主機電腦的 SSH 提示以及密碼提示。</span><span class="sxs-lookup"><span data-stu-id="4b413-162">Notice that I am using PowerShell cmdlets from a command prompt so we see prompts from SSH asking to verify the host computer as well as password prompts.</span></span> <span data-ttu-id="4b413-163">您可以在 Windows 電腦上執行相同的動作以確保遠端功能也可以運作，然後在電腦之間執行遠端功能，方法是只要變更主機名稱。</span><span class="sxs-lookup"><span data-stu-id="4b413-163">You can do the same thing on a Windows machine to ensure remoting is working there and then remote between machines by simply changing the host name.</span></span>

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
 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            UbuntuVM1       RemoteMachine   Opened        DefaultShell             Available
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

### <a name="known-issues"></a><span data-ttu-id="4b413-164">已知問題</span><span class="sxs-lookup"><span data-stu-id="4b413-164">Known Issues</span></span>

<span data-ttu-id="4b413-165">sudo 命令不適用於連至 Linux 電腦的遠端工作階段。</span><span class="sxs-lookup"><span data-stu-id="4b413-165">The sudo command does not work in remote session to Linux machine.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b413-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b413-166">See Also</span></span>

[<span data-ttu-id="4b413-167">PowerShell Core for Windows</span><span class="sxs-lookup"><span data-stu-id="4b413-167">PowerShell Core for Windows</span></span>](../setup/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="4b413-168">PowerShell Core for Linux</span><span class="sxs-lookup"><span data-stu-id="4b413-168">PowerShell Core for Linux</span></span>](../setup/installing-powershell-core-on-linux.md#ubuntu-1404)

[<span data-ttu-id="4b413-169">PowerShell Core for MacOS</span><span class="sxs-lookup"><span data-stu-id="4b413-169">PowerShell Core for MacOS</span></span>](../setup/installing-powershell-core-on-macos.md)

[<span data-ttu-id="4b413-170">Win32 OpenSSH</span><span class="sxs-lookup"><span data-stu-id="4b413-170">Win32 OpenSSH</span></span>](https://github.com/PowerShell/Win32-OpenSSH/releases)

[<span data-ttu-id="4b413-171">安裝</span><span class="sxs-lookup"><span data-stu-id="4b413-171">installation</span></span>](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH)

[<span data-ttu-id="4b413-172">Ubuntu SSH</span><span class="sxs-lookup"><span data-stu-id="4b413-172">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)