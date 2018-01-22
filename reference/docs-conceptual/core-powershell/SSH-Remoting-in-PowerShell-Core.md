# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="42d5b-101">透過 SSH 的 PowerShell 遠端處理</span><span class="sxs-lookup"><span data-stu-id="42d5b-101">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="42d5b-102">概觀</span><span class="sxs-lookup"><span data-stu-id="42d5b-102">Overview</span></span>

<span data-ttu-id="42d5b-103">PowerShell 遠端通常會使用 WinRM 進行連線交涉和資料傳輸。</span><span class="sxs-lookup"><span data-stu-id="42d5b-103">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span>
<span data-ttu-id="42d5b-104">已選擇 SSH 進行此遠端實作，因為它現在適用於 Linux 和 Windows 平台，並允許真正多平台 PowerShell 遠端。</span><span class="sxs-lookup"><span data-stu-id="42d5b-104">SSH was chosen for this remoting implementation since it is now available for both Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>
<span data-ttu-id="42d5b-105">不過，WinRM 也提供穩固的裝載模型，來進行這項實作尚未執行的 PowerShell 遠端工作階段。</span><span class="sxs-lookup"><span data-stu-id="42d5b-105">However, WinRM also provides a robust hosting model for PowerShell remote sessions which this implementation does not yet do.</span></span>
<span data-ttu-id="42d5b-106">這表示，這項實作尚未支援 PowerShell 遠端端點設定和 JEA (Just Enough Administration)。</span><span class="sxs-lookup"><span data-stu-id="42d5b-106">And this means that PowerShell remote endpoint configuration and JEA (Just Enough Administration) is not yet supported in this implementation.</span></span>

<span data-ttu-id="42d5b-107">PowerShell SSH 遠端可讓您在 Windows 與 Linux 電腦之間執行基本 PowerShell 工作階段遠端。</span><span class="sxs-lookup"><span data-stu-id="42d5b-107">PowerShell SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span>
<span data-ttu-id="42d5b-108">做法是在目標電腦上建立 PowerShell 裝載處理序作為 SSH 子系統。</span><span class="sxs-lookup"><span data-stu-id="42d5b-108">This is done by creating a PowerShell hosting process on the target machine as an SSH subsystem.</span></span>
<span data-ttu-id="42d5b-109">最終，這會變更為與 WinRM 運作方式類似的更一般裝載模型，以支援端點設定和 JEA。</span><span class="sxs-lookup"><span data-stu-id="42d5b-109">Eventually this will be changed to a more general hosting model similar to how WinRM works in order to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="42d5b-110">New-PSSession、Enter-PSSession 和 Invoke-Command Cmdlet 現在有新的參數集，可方便進行這個新的遠端連線</span><span class="sxs-lookup"><span data-stu-id="42d5b-110">The New-PSSession, Enter-PSSession and Invoke-Command cmdlets now have a new parameter set to facilitate this new remoting connection</span></span>

```powershell
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="42d5b-111">這個新的參數集很可能會變更，但現在可讓您建立 SSH PSSession，以從命令列與之互動或在其上叫用命令和指令碼。</span><span class="sxs-lookup"><span data-stu-id="42d5b-111">This new parameter set will likely change but for now allows you to create SSH PSSessions that you can interact with from the command line or invoke commands and scripts on.</span></span>
<span data-ttu-id="42d5b-112">您可以使用 HostName 參數指定目標電腦，並使用 UserName 來提供使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="42d5b-112">You specify the target machine with the HostName parameter and provide the user name with UserName.</span></span>
<span data-ttu-id="42d5b-113">在 PowerShell 命令列以互動方式執行 Cmdlet 時，系統會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="42d5b-113">When running the cmdlets interactively at the PowerShell command line you will be prompted for a password.</span></span>
<span data-ttu-id="42d5b-114">但是，您也可以選擇使用 SSH 金鑰驗證，並使用 KeyFilePath 參數提供私密金鑰檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="42d5b-114">But you also have the option to use SSH key authentication and provide a private key file path with the KeyFilePath parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="42d5b-115">一般安裝資訊</span><span class="sxs-lookup"><span data-stu-id="42d5b-115">General setup information</span></span>

<span data-ttu-id="42d5b-116">需要有 SSH 才能安裝在所有電腦上。</span><span class="sxs-lookup"><span data-stu-id="42d5b-116">SSH is required to be installed on all machines.</span></span>
<span data-ttu-id="42d5b-117">您應該同時安裝用戶端 (ssh.exe) 和伺服器 (sshd.exe)，讓您可以試驗往返電腦的遠端執行。</span><span class="sxs-lookup"><span data-stu-id="42d5b-117">You should install both client (ssh.exe) and server (sshd.exe) so that you can experiment with remoting to and from the machines.</span></span>
<span data-ttu-id="42d5b-118">針對 Windows，您需要[從 GitHub 安裝 Win32 OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/releases)。</span><span class="sxs-lookup"><span data-stu-id="42d5b-118">For Windows you will need to install [Win32 OpenSSH from GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span></span>
<span data-ttu-id="42d5b-119">針對 Linux，您需要安裝您平台適用的 SSH (包含 sshd 伺服器)。</span><span class="sxs-lookup"><span data-stu-id="42d5b-119">For Linux you will need to install SSH (including sshd server) appropriate to your platform.</span></span>
<span data-ttu-id="42d5b-120">您也需要來自 GitHub 且具有 SSH 遠端功能的新 PowerShell 組建或套件。</span><span class="sxs-lookup"><span data-stu-id="42d5b-120">You will also need a recent PowerShell build or package from GitHub having the SSH remoting feature.</span></span>
<span data-ttu-id="42d5b-121">SSH 子系統用來在遠端電腦上建立 PowerShell 處理序，因此需要設定 SSH 伺服器。</span><span class="sxs-lookup"><span data-stu-id="42d5b-121">SSH subsystems is used to establish a PowerShell process on the remote machine and the SSH server will need to be configured for that.</span></span>
<span data-ttu-id="42d5b-122">此外，您必須啟用密碼驗證，以及選擇性地啟用金鑰型驗證。</span><span class="sxs-lookup"><span data-stu-id="42d5b-122">In addition you will need to enable password authentication and optionally key based authentication.</span></span>

## <a name="setup-on-windows-machine"></a><span data-ttu-id="42d5b-123">Windows 電腦上的安裝</span><span class="sxs-lookup"><span data-stu-id="42d5b-123">Setup on Windows Machine</span></span>

1. <span data-ttu-id="42d5b-124">[安裝最新 PowerShell Core for Windows 版本][]</span><span class="sxs-lookup"><span data-stu-id="42d5b-124">[Install the latest version of PowerShell Core for Windows][]</span></span>
    - <span data-ttu-id="42d5b-125">您可以查看針對 New-PSSession 所設定的參數，得知它是否具有 SSH 遠端支援</span><span class="sxs-lookup"><span data-stu-id="42d5b-125">You can tell if it has the SSH remoting support by looking at the parameter sets for New-PSSession</span></span>
    ```powershell
    PS> Get-Command New-PSSession -syntax
    New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
    ```
1. <span data-ttu-id="42d5b-126">使用[安裝]指示，安裝 GitHub 中的最新 [Win32 OpenSSH] 組建</span><span class="sxs-lookup"><span data-stu-id="42d5b-126">Install the latest [Win32 OpenSSH] build from GitHub using the [installation] instructions</span></span>
1. <span data-ttu-id="42d5b-127">編輯 Win32 OpenSSH 所安裝位置中的 sshd_config 檔案</span><span class="sxs-lookup"><span data-stu-id="42d5b-127">Edit the sshd_config file at the location where you installed Win32 OpenSSH</span></span>
    - <span data-ttu-id="42d5b-128">確定已啟用密碼驗證</span><span class="sxs-lookup"><span data-stu-id="42d5b-128">Make sure password authentication is enabled</span></span>
    ```none
    PasswordAuthentication yes
    ```
    - <span data-ttu-id="42d5b-129">新增 PowerShell 子系統項目，以將 `c:/program files/powershell/6.0.0/pwsh.exe` 取代為您想要使用之版本的正確路徑</span><span class="sxs-lookup"><span data-stu-id="42d5b-129">Add a PowerShell subsystem entry, replace `c:/program files/powershell/6.0.0/pwsh.exe` with the correct path to the version you want to use</span></span>
    ```none
    Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
    ```
    - <span data-ttu-id="42d5b-130">選擇性啟用金鑰驗證</span><span class="sxs-lookup"><span data-stu-id="42d5b-130">Optionally enable key authentication</span></span>
    ```none
    PubkeyAuthentication yes
    ```
1. <span data-ttu-id="42d5b-131">重新啟動 sshd 服務</span><span class="sxs-lookup"><span data-stu-id="42d5b-131">Restart the sshd service</span></span>
    ```powershell
    Restart-Service sshd
    ```
1. <span data-ttu-id="42d5b-132">將安裝 OpenSSH 的路徑新增至路徑環境變數</span><span class="sxs-lookup"><span data-stu-id="42d5b-132">Add the path where OpenSSH is installed to your Path Env Variable</span></span>
    - <span data-ttu-id="42d5b-133">這應該是與 `C:\Program Files\OpenSSH\` 行一起</span><span class="sxs-lookup"><span data-stu-id="42d5b-133">This should be along the lines of `C:\Program Files\OpenSSH\`</span></span>
    - <span data-ttu-id="42d5b-134">這樣可以找到 ssh.exe</span><span class="sxs-lookup"><span data-stu-id="42d5b-134">This allows for the ssh.exe to be found</span></span>

## <a name="setup-on-linux-ubuntu-1404-machine"></a><span data-ttu-id="42d5b-135">Linux (Ubuntu 14.04) 電腦上的安裝</span><span class="sxs-lookup"><span data-stu-id="42d5b-135">Setup on Linux (Ubuntu 14.04) Machine</span></span>

1. <span data-ttu-id="42d5b-136">安裝 GitHub 中的最新 [PowerShell for Linux] 組建</span><span class="sxs-lookup"><span data-stu-id="42d5b-136">Install the latest [PowerShell for Linux] build from GitHub</span></span>
1. <span data-ttu-id="42d5b-137">視需要安裝 [Ubuntu SSH]</span><span class="sxs-lookup"><span data-stu-id="42d5b-137">Install [Ubuntu SSH] as needed</span></span>
    ```bash
    sudo apt install openssh-client
    sudo apt install openssh-server
    ```
1. <span data-ttu-id="42d5b-138">編輯 /etc/ssh 位置中的 sshd_config 檔案</span><span class="sxs-lookup"><span data-stu-id="42d5b-138">Edit the sshd_config file at location /etc/ssh</span></span>
    - <span data-ttu-id="42d5b-139">確定已啟用密碼驗證</span><span class="sxs-lookup"><span data-stu-id="42d5b-139">Make sure password authentication is enabled</span></span>
    ```none
    PasswordAuthentication yes
    ```
    - <span data-ttu-id="42d5b-140">新增 PowerShell 子系統項目</span><span class="sxs-lookup"><span data-stu-id="42d5b-140">Add a PowerShell subsystem entry</span></span>
    ```none
    Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
    ```
    - <span data-ttu-id="42d5b-141">選擇性啟用金鑰驗證</span><span class="sxs-lookup"><span data-stu-id="42d5b-141">Optionally enable key authentication</span></span>
    ```none
    PubkeyAuthentication yes
    ```
1. <span data-ttu-id="42d5b-142">重新啟動 sshd 服務</span><span class="sxs-lookup"><span data-stu-id="42d5b-142">Restart the sshd service</span></span>
    ```bash
    sudo service sshd restart
    ```

## <a name="setup-on-macos-machine"></a><span data-ttu-id="42d5b-143">MacOS 電腦上的安裝</span><span class="sxs-lookup"><span data-stu-id="42d5b-143">Setup on MacOS Machine</span></span>

1. <span data-ttu-id="42d5b-144">安裝最新 [PowerShell for MacOS] 組建</span><span class="sxs-lookup"><span data-stu-id="42d5b-144">Install the latest [PowerShell for MacOS] build</span></span>
    - <span data-ttu-id="42d5b-145">確定已遵循下列步驟來啟用 SSH 遠端：</span><span class="sxs-lookup"><span data-stu-id="42d5b-145">Make sure SSH Remoting is enabled by following these steps:</span></span>
      - <span data-ttu-id="42d5b-146">開啟 `System Preferences`</span><span class="sxs-lookup"><span data-stu-id="42d5b-146">Open `System Preferences`</span></span>
      - <span data-ttu-id="42d5b-147">按一下 `Sharing`</span><span class="sxs-lookup"><span data-stu-id="42d5b-147">Click on `Sharing`</span></span>
      - <span data-ttu-id="42d5b-148">檢查 `Remote Login` - 應該為 `Remote Login: On`</span><span class="sxs-lookup"><span data-stu-id="42d5b-148">Check `Remote Login` - Should say `Remote Login: On`</span></span>
      - <span data-ttu-id="42d5b-149">允許存取適當的使用者</span><span class="sxs-lookup"><span data-stu-id="42d5b-149">Allow access to appropriate users</span></span>
1. <span data-ttu-id="42d5b-150">編輯 `/private/etc/ssh/sshd_config` 位置中的 `sshd_config` 檔案</span><span class="sxs-lookup"><span data-stu-id="42d5b-150">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>
    - <span data-ttu-id="42d5b-151">使用您慣用的編輯器，或</span><span class="sxs-lookup"><span data-stu-id="42d5b-151">Use your favorite editor or</span></span>
    ```bash
    sudo nano /private/etc/ssh/sshd_config
    ```
    - <span data-ttu-id="42d5b-152">確定已啟用密碼驗證</span><span class="sxs-lookup"><span data-stu-id="42d5b-152">Make sure password authentication is enabled</span></span>
    ```none
    PasswordAuthentication yes
    ```
    - <span data-ttu-id="42d5b-153">新增 PowerShell 子系統項目</span><span class="sxs-lookup"><span data-stu-id="42d5b-153">Add a PowerShell subsystem entry</span></span>
    ```none
    Subsystem powershell /usr/local/bin/powershell -sshs -NoLogo -NoProfile
    ```
    - <span data-ttu-id="42d5b-154">選擇性啟用金鑰驗證</span><span class="sxs-lookup"><span data-stu-id="42d5b-154">Optionally enable key authentication</span></span>
    ```none
    PubkeyAuthentication yes
    ```
1. <span data-ttu-id="42d5b-155">重新啟動 sshd 服務</span><span class="sxs-lookup"><span data-stu-id="42d5b-155">Restart the sshd service</span></span>
    ```bash
    sudo launchctl stop com.openssh.sshd
    sudo launchctl start com.openssh.sshd
    ```

## <a name="powershell-remoting-example"></a><span data-ttu-id="42d5b-156">PowerShell 遠端範例</span><span class="sxs-lookup"><span data-stu-id="42d5b-156">PowerShell Remoting Example</span></span>

<span data-ttu-id="42d5b-157">測試遠端功能的最簡單方式是只在單一電腦上試用。</span><span class="sxs-lookup"><span data-stu-id="42d5b-157">The easiest way to test remoting is to just try it on a single machine.</span></span>
<span data-ttu-id="42d5b-158">我將在這裡建立回到 Linux 方塊上相同電腦的遠端工作階段。</span><span class="sxs-lookup"><span data-stu-id="42d5b-158">Here I will create a remote session back to the same machine on a Linux box.</span></span>
<span data-ttu-id="42d5b-159">請注意，我將會從命令提示字元使用 PowerShell Cmdlet，因此我們會看到要求驗證主機電腦的 SSH 提示以及密碼提示。</span><span class="sxs-lookup"><span data-stu-id="42d5b-159">Notice that I am using PowerShell cmdlets from a command prompt so we see prompts from SSH asking to verify the host computer as well as password prompts.</span></span>
<span data-ttu-id="42d5b-160">您可以在 Windows 電腦上執行相同的動作以確保遠端功能也可以運作，然後在電腦之間執行遠端功能，方法是只要變更主機名稱。</span><span class="sxs-lookup"><span data-stu-id="42d5b-160">You can do the same thing on a Windows machine to ensure remoting is working there and then remote between machines by simply changing the host name.</span></span>

```powershell
#
# Linux to Linux
#
PS /home/TestUser> $session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:

PS /home/TestUser> $session

 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            UbuntuVM1       RemoteMachine   Opened        DefaultShell             Available

PS /home/TestUser> Enter-PSSession $session

[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~14.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession

PS /home/TestUser> Invoke-Command $session -ScriptBlock { Get-Process powershell }

Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName                    PSComputerName
-------  ------    -----      -----     ------     --  -- -----------                    --------------
      0       0        0         19       3.23  10635 635 powershell                     UbuntuVM1
      0       0        0         21       4.92  11033 017 powershell                     UbuntuVM1
      0       0        0         20       3.07  11076 076 powershell                     UbuntuVM1


#
# Linux to Windows
#
PS /home/TestUser> Enter-PSSession -HostName WinVM1 -UserName PTestName
PTestName@WinVM1s password:

[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver

Microsoft Windows [Version 10.0.10586]

[WinVM1]: PS C:\Users\PTestName\Documents>

#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.

PS C:\Users\PSUser\Documents> $session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
PS C:\Users\PSUser\Documents> $session

 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available


PS C:\Users\PSUser\Documents> Enter-PSSession -Session $session
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

### <a name="known-issues"></a><span data-ttu-id="42d5b-161">已知問題</span><span class="sxs-lookup"><span data-stu-id="42d5b-161">Known Issues</span></span>

1. <span data-ttu-id="42d5b-162">sudo 命令不適用於 Linux 電腦的遠端工作階段。</span><span class="sxs-lookup"><span data-stu-id="42d5b-162">sudo command does not work in remote session to Linux machine.</span></span>

[PowerShell for Windows]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/windows.md#msi
[Win32 OpenSSH]: https://github.com/PowerShell/Win32-OpenSSH
[安裝]: https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH
[PowerShell for Linux]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#ubuntu-1404
[Ubuntu SSH]: https://help.ubuntu.com/lts/serverguide/openssh-server.html
[PowerShell for MacOS]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#macos-1012
