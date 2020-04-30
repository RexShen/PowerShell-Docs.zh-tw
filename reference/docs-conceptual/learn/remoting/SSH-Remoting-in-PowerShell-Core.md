---
title: 透過 SSH 的 PowerShell 遠端處理
description: 使用 SSH 在 PowerShell Core 中遠端
ms.date: 09/30/2019
ms.openlocfilehash: 9fe3e22c54a4695a1027f416acf113f2f7fd2cd7
ms.sourcegitcommit: 7c7f8bb9afdc592d07bf7ff4179d000a48716f13
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "82174123"
---
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="43282-103">透過 SSH 的 PowerShell 遠端處理</span><span class="sxs-lookup"><span data-stu-id="43282-103">PowerShell remoting over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="43282-104">概觀</span><span class="sxs-lookup"><span data-stu-id="43282-104">Overview</span></span>

<span data-ttu-id="43282-105">PowerShell 遠端通常會使用 WinRM 進行連線交涉和資料傳輸。</span><span class="sxs-lookup"><span data-stu-id="43282-105">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span> <span data-ttu-id="43282-106">SSH 目前適用於 Linux 與 Windows 平台，而且能夠執行真正的多平台 PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="43282-106">SSH is now available for Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>

<span data-ttu-id="43282-107">WinRM 提供一個健全裝載模型以供 PowerShell 遠端工作階段使用。</span><span class="sxs-lookup"><span data-stu-id="43282-107">WinRM provides a robust hosting model for PowerShell remote sessions.</span></span> <span data-ttu-id="43282-108">SSH 遠端功能目前不支援遠端端點設定和 Just Enough Administration (JEA)。</span><span class="sxs-lookup"><span data-stu-id="43282-108">SSH-based remoting doesn't currently support remote endpoint configuration and Just Enough Administration (JEA).</span></span>

<span data-ttu-id="43282-109">SSH 遠端功能可讓您在 Windows 與 Linux 電腦之間執行基本 PowerShell 工作階段遠端功能。</span><span class="sxs-lookup"><span data-stu-id="43282-109">SSH remoting lets you do basic PowerShell session remoting between Windows and Linux computers.</span></span> <span data-ttu-id="43282-110">SSH 遠端功能會在目標電腦上建立 PowerShell 裝載處理序作為 SSH 子系統。</span><span class="sxs-lookup"><span data-stu-id="43282-110">SSH remoting creates a PowerShell host process on the target computer as an SSH subsystem.</span></span> <span data-ttu-id="43282-111">最後，我們將實作一般裝載模型 (類似 WinRM) 以支援端點設定與 JEA。</span><span class="sxs-lookup"><span data-stu-id="43282-111">Eventually we'll implement a general hosting model, similar to WinRM, to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="43282-112">`New-PSSession`、`Enter-PSSession` 與 `Invoke-Command` Cmdlet 現在有新的參數集，可支援這個新的遠端連線。</span><span class="sxs-lookup"><span data-stu-id="43282-112">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets now have a new parameter set to support this new remoting connection.</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="43282-113">若要建立遠端工作階段，您可以使用 `HostName` 參數來指定目標電腦，並使用 `UserName` 來提供使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="43282-113">To create a remote session, you specify the target computer with the `HostName` parameter and provide the user name with `UserName`.</span></span> <span data-ttu-id="43282-114">以互動方式執行 Cmdlet 時，系統會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="43282-114">When running the cmdlets interactively, you're prompted for a password.</span></span> <span data-ttu-id="43282-115">您也可以搭配 `KeyFilePath` 參數使用私密金鑰檔案，來使用 SSH 金鑰驗證。</span><span class="sxs-lookup"><span data-stu-id="43282-115">You can also, use SSH key authentication using a private key file with the `KeyFilePath` parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="43282-116">一般安裝資訊</span><span class="sxs-lookup"><span data-stu-id="43282-116">General setup information</span></span>

<span data-ttu-id="43282-117">PowerShell 6 或更新版本，且必須在所有電腦上安裝 SSH。</span><span class="sxs-lookup"><span data-stu-id="43282-117">PowerShell 6 or higher, and SSH must be installed on all computers.</span></span> <span data-ttu-id="43282-118">請同時安裝 SSH 用戶端 (`ssh.exe`) 與伺服器 (`sshd.exe`)，讓您可從遠端往返電腦。</span><span class="sxs-lookup"><span data-stu-id="43282-118">Install both the SSH client (`ssh.exe`) and server (`sshd.exe`) so that you can remote to and from the computers.</span></span> <span data-ttu-id="43282-119">適用於 Windows 的 OpenSSH 現在已可在 Windows 10 組建 1809 與 Windows Server 2019 中使用。</span><span class="sxs-lookup"><span data-stu-id="43282-119">OpenSSH for Windows is now available in Windows 10 build 1809 and Windows Server 2019.</span></span> <span data-ttu-id="43282-120">如需詳細資訊，請參閱[使用 OpenSSH 管理 Windows](/windows-server/administration/openssh/openssh_overview)。</span><span class="sxs-lookup"><span data-stu-id="43282-120">For more information, see [Manage Windows with OpenSSH](/windows-server/administration/openssh/openssh_overview).</span></span> <span data-ttu-id="43282-121">針對 Linux，安裝您平台適用的 SSH (包括 sshd 伺服器)。</span><span class="sxs-lookup"><span data-stu-id="43282-121">For Linux, install SSH, including sshd server, that's appropriate for your platform.</span></span> <span data-ttu-id="43282-122">您也需要從 GitHub 安裝 PowerShell 來取得 SSH 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="43282-122">You also need to install PowerShell from GitHub to get the SSH remoting feature.</span></span> <span data-ttu-id="43282-123">SSH 伺服器必須設定為建立 SSH 子系統，以便在遠端電腦上裝載 PowerShell 處理序。</span><span class="sxs-lookup"><span data-stu-id="43282-123">The SSH server must be configured to create an SSH subsystem to host a PowerShell process on the remote computer.</span></span> <span data-ttu-id="43282-124">而且，您也必須設定啟用**密碼**或**金鑰型**的驗證。</span><span class="sxs-lookup"><span data-stu-id="43282-124">And, you must enable **password** or **key-based** authentication.</span></span>

## <a name="set-up-on-a-windows-computer"></a><span data-ttu-id="43282-125">在 Windows 電腦上設定</span><span class="sxs-lookup"><span data-stu-id="43282-125">Set up on a Windows computer</span></span>

1. <span data-ttu-id="43282-126">安裝最新版的 PowerShell，請參閱[在 Windows 上安裝 PowerShell Core](../../install/installing-powershell-core-on-windows.md#msi)。</span><span class="sxs-lookup"><span data-stu-id="43282-126">Install the latest version of PowerShell, see [Installing PowerShell Core on Windows](../../install/installing-powershell-core-on-windows.md#msi).</span></span>

   <span data-ttu-id="43282-127">您可以列出 `New-PSSession` 參數集來確認 PowerShell 具有 SSH 遠端支援。</span><span class="sxs-lookup"><span data-stu-id="43282-127">You can confirm that PowerShell has SSH remoting support by listing the `New-PSSession` parameter sets.</span></span> <span data-ttu-id="43282-128">您會注意到以 **SSH** 開頭的參數集名稱。</span><span class="sxs-lookup"><span data-stu-id="43282-128">You'll notice there are parameter set names that begin with **SSH**.</span></span> <span data-ttu-id="43282-129">這些參數集包括 **SSH** 參數。</span><span class="sxs-lookup"><span data-stu-id="43282-129">Those parameter sets include **SSH** parameters.</span></span>

   ```powershell
   (Get-Command New-PSSession).ParameterSets.Name
   ```

   ```Output
   Name
   ----
   SSHHost
   SSHHostHashParam
   ```

1. <span data-ttu-id="43282-130">安裝最新的 Win32 OpenSSH。</span><span class="sxs-lookup"><span data-stu-id="43282-130">Install the latest Win32 OpenSSH.</span></span> <span data-ttu-id="43282-131">如需安裝指示，請參閱[開始使用 OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse)。</span><span class="sxs-lookup"><span data-stu-id="43282-131">For installation instructions, see [Getting started with OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).</span></span>

   > [!NOTE]
   > <span data-ttu-id="43282-132">如果您想要將 PowerShell 設定為 OpenSSH 的預設殼層，請參閱[為 OpenSSH 設定 Windows](/windows-server/administration/openssh/openssh_server_configuration)。</span><span class="sxs-lookup"><span data-stu-id="43282-132">If you want to set PowerShell as the default shell for OpenSSH, see [Configuring Windows for OpenSSH](/windows-server/administration/openssh/openssh_server_configuration).</span></span>

1. <span data-ttu-id="43282-133">編輯位於 `$env:ProgramData\ssh` 的 `sshd_config` 檔案。</span><span class="sxs-lookup"><span data-stu-id="43282-133">Edit the `sshd_config` file located at `$env:ProgramData\ssh`.</span></span>

   <span data-ttu-id="43282-134">確定已啟用密碼驗證：</span><span class="sxs-lookup"><span data-stu-id="43282-134">Make sure password authentication is enabled:</span></span>

   ```
   PasswordAuthentication yes
   ```

   <span data-ttu-id="43282-135">在遠端電腦上建立裝載 PowerShell 處理程序的 SSH 子系統：</span><span class="sxs-lookup"><span data-stu-id="43282-135">Create the SSH subsystem that hosts a PowerShell process on the remote computer:</span></span>

   ```
   Subsystem powershell c:/progra~1/powershell/7/pwsh.exe -sshs -NoLogo -NoProfile
   ```

   > [!NOTE]
   > <span data-ttu-id="43282-136">PowerShell 可執行檔的預設位置為 `c:/progra~1/powershell/7/pwsh.exe`。</span><span class="sxs-lookup"><span data-stu-id="43282-136">The default location of the PowerShell executable is `c:/progra~1/powershell/7/pwsh.exe`.</span></span> <span data-ttu-id="43282-137">該位置會根據您安裝 PowerShell 的方式而有所不同。</span><span class="sxs-lookup"><span data-stu-id="43282-137">The location can vary depending on how you installed PowerShell.</span></span>
   >
   > <span data-ttu-id="43282-138">您必須針對任何包含空格的檔案路徑使用 8.3 簡短名稱。</span><span class="sxs-lookup"><span data-stu-id="43282-138">You must use the 8.3 short name for any file paths that contain spaces.</span></span> <span data-ttu-id="43282-139">OpenSSH for Windows 中有一個 Bug，會讓空格無法在子系統可執行檔路徑中運作。</span><span class="sxs-lookup"><span data-stu-id="43282-139">There's a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span> <span data-ttu-id="43282-140">如需詳細資訊，請參閱此 [GitHub 問題](https://github.com/PowerShell/Win32-OpenSSH/issues/784)。</span><span class="sxs-lookup"><span data-stu-id="43282-140">For more information, see this [GitHub issue](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>
   >
   > <span data-ttu-id="43282-141">Windows 中 `Program Files` 資料夾的 8.3 簡短名稱通常是 `Progra~1`。</span><span class="sxs-lookup"><span data-stu-id="43282-141">The 8.3 short name for the `Program Files` folder in Windows is usually `Progra~1`.</span></span> <span data-ttu-id="43282-142">但您可以使用下列命令來確保：</span><span class="sxs-lookup"><span data-stu-id="43282-142">However, you can use the following command to make sure:</span></span>
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

   <span data-ttu-id="43282-143">選擇性啟用金鑰驗證：</span><span class="sxs-lookup"><span data-stu-id="43282-143">Optionally, enable key authentication:</span></span>

   ```
   PubkeyAuthentication yes
   ```

   <span data-ttu-id="43282-144">如需詳細資訊，請參閱[管理 OpenSSH 金鑰](/windows-server/administration/openssh/openssh_keymanagement)。</span><span class="sxs-lookup"><span data-stu-id="43282-144">For more information, see [Managing OpenSSH Keys](/windows-server/administration/openssh/openssh_keymanagement).</span></span>

1. <span data-ttu-id="43282-145">重新啟動 **sshd** 服務。</span><span class="sxs-lookup"><span data-stu-id="43282-145">Restart the **sshd** service.</span></span>

   ```powershell
   Restart-Service sshd
   ```

1. <span data-ttu-id="43282-146">將 OpenSSH 安裝所在的路徑新增至 Path 環境變數。</span><span class="sxs-lookup"><span data-stu-id="43282-146">Add the path where OpenSSH is installed to your Path environment variable.</span></span> <span data-ttu-id="43282-147">例如： `C:\Program Files\OpenSSH\` 。</span><span class="sxs-lookup"><span data-stu-id="43282-147">For example, `C:\Program Files\OpenSSH\`.</span></span> <span data-ttu-id="43282-148">此項目可允許程式找到 `ssh.exe`。</span><span class="sxs-lookup"><span data-stu-id="43282-148">This entry allows for the `ssh.exe` to be found.</span></span>

## <a name="set-up-on-an-ubuntu-1604-linux-computer"></a><span data-ttu-id="43282-149">在 Ubuntu 16.04 Linux 電腦上設定</span><span class="sxs-lookup"><span data-stu-id="43282-149">Set up on an Ubuntu 16.04 Linux computer</span></span>

1. <span data-ttu-id="43282-150">安裝最新版的 PowerShell，請參閱[在 Linux 上安裝 PowerShell Core](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)。</span><span class="sxs-lookup"><span data-stu-id="43282-150">Install the latest version of PowerShell, see [Installing PowerShell Core on Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604).</span></span>
1. <span data-ttu-id="43282-151">安裝 [Ubuntu OpenSSH Server](https://help.ubuntu.com/lts/serverguide/openssh-server.html)。</span><span class="sxs-lookup"><span data-stu-id="43282-151">Install [Ubuntu OpenSSH Server](https://help.ubuntu.com/lts/serverguide/openssh-server.html).</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

1. <span data-ttu-id="43282-152">編輯 `/etc/ssh` 位置中的 `sshd_config` 檔案。</span><span class="sxs-lookup"><span data-stu-id="43282-152">Edit the `sshd_config` file at location `/etc/ssh`.</span></span>

   <span data-ttu-id="43282-153">確定已啟用密碼驗證：</span><span class="sxs-lookup"><span data-stu-id="43282-153">Make sure password authentication is enabled:</span></span>

   ```
   PasswordAuthentication yes
   ```

   <span data-ttu-id="43282-154">新增 PowerShell 子系統項目：</span><span class="sxs-lookup"><span data-stu-id="43282-154">Add a PowerShell subsystem entry:</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   > [!NOTE]
   > <span data-ttu-id="43282-155">PowerShell 可執行檔的預設位置為 `/usr/bin/pwsh`。</span><span class="sxs-lookup"><span data-stu-id="43282-155">The default location of the PowerShell executable is `/usr/bin/pwsh`.</span></span> <span data-ttu-id="43282-156">該位置會根據您安裝 PowerShell 的方式而有所不同。</span><span class="sxs-lookup"><span data-stu-id="43282-156">The location can vary depending on how you installed PowerShell.</span></span>

   <span data-ttu-id="43282-157">選擇性啟用金鑰驗證：</span><span class="sxs-lookup"><span data-stu-id="43282-157">Optionally, enable key authentication:</span></span>

   ```
   PubkeyAuthentication yes
   ```

1. <span data-ttu-id="43282-158">重新啟動 **sshd** 服務。</span><span class="sxs-lookup"><span data-stu-id="43282-158">Restart the **sshd** service.</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-a-macos-computer"></a><span data-ttu-id="43282-159">在 macOS 電腦上設定</span><span class="sxs-lookup"><span data-stu-id="43282-159">Set up on a macOS computer</span></span>

1. <span data-ttu-id="43282-160">安裝最新版的 PowerShell，請參閱[在 macOS 上安裝 PowerShell Core](../../install/installing-powershell-core-on-macos.md)。</span><span class="sxs-lookup"><span data-stu-id="43282-160">Install the latest version of PowerShell, see [Installing PowerShell Core on macOS](../../install/installing-powershell-core-on-macos.md).</span></span>

   <span data-ttu-id="43282-161">確定已遵循下列步驟來啟用 SSH 遠端：</span><span class="sxs-lookup"><span data-stu-id="43282-161">Make sure SSH Remoting is enabled by following these steps:</span></span>

   1. <span data-ttu-id="43282-162">開啟 `System Preferences`。</span><span class="sxs-lookup"><span data-stu-id="43282-162">Open `System Preferences`.</span></span>
   1. <span data-ttu-id="43282-163">按一下 `Sharing`。</span><span class="sxs-lookup"><span data-stu-id="43282-163">Click on `Sharing`.</span></span>
   1. <span data-ttu-id="43282-164">選取 `Remote Login` 以設定 `Remote Login: On`。</span><span class="sxs-lookup"><span data-stu-id="43282-164">Check `Remote Login` to set `Remote Login: On`.</span></span>
   1. <span data-ttu-id="43282-165">允許適當的使用者存取。</span><span class="sxs-lookup"><span data-stu-id="43282-165">Allow access to the appropriate users.</span></span>

1. <span data-ttu-id="43282-166">編輯 `/private/etc/ssh/sshd_config` 位置中的 `sshd_config` 檔案。</span><span class="sxs-lookup"><span data-stu-id="43282-166">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`.</span></span>

   <span data-ttu-id="43282-167">開啟文字編輯器，例如 **nano**：</span><span class="sxs-lookup"><span data-stu-id="43282-167">Use a text editor such as **nano**:</span></span>

   ```bash
   sudo nano /private/etc/ssh/sshd_config
   ```

   <span data-ttu-id="43282-168">確定已啟用密碼驗證：</span><span class="sxs-lookup"><span data-stu-id="43282-168">Make sure password authentication is enabled:</span></span>

   ```
   PasswordAuthentication yes
   ```

   <span data-ttu-id="43282-169">新增 PowerShell 子系統項目：</span><span class="sxs-lookup"><span data-stu-id="43282-169">Add a PowerShell subsystem entry:</span></span>

   ```
   Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   > [!NOTE]
   > <span data-ttu-id="43282-170">PowerShell 可執行檔的預設位置為 `/usr/local/bin/pwsh`。</span><span class="sxs-lookup"><span data-stu-id="43282-170">The default location of the PowerShell executable is `/usr/local/bin/pwsh`.</span></span> <span data-ttu-id="43282-171">該位置會根據您安裝 PowerShell 的方式而有所不同。</span><span class="sxs-lookup"><span data-stu-id="43282-171">The location can vary depending on how you installed PowerShell.</span></span>

   <span data-ttu-id="43282-172">選擇性啟用金鑰驗證：</span><span class="sxs-lookup"><span data-stu-id="43282-172">Optionally, enable key authentication:</span></span>

   ```
   PubkeyAuthentication yes
   ```

1. <span data-ttu-id="43282-173">重新啟動 **sshd** 服務。</span><span class="sxs-lookup"><span data-stu-id="43282-173">Restart the **sshd** service.</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a><span data-ttu-id="43282-174">驗證</span><span class="sxs-lookup"><span data-stu-id="43282-174">Authentication</span></span>

<span data-ttu-id="43282-175">透過 SSH 的 PowerShell 遠端功能需要在 SSH 用戶端與 SSH 服務之間交換驗證，且本身不會實作任何驗證配置。</span><span class="sxs-lookup"><span data-stu-id="43282-175">PowerShell remoting over SSH relies on the authentication exchange between the SSH client and SSH service and doesn't implement any authentication schemes itself.</span></span> <span data-ttu-id="43282-176">結果是，任何已設定的驗證配置 (包括多重要素驗證) 都是由 SSH 處理，與 PowerShell 無關。</span><span class="sxs-lookup"><span data-stu-id="43282-176">The result is that any configured authentication schemes including multi-factor authentication are handled by SSH and independent of PowerShell.</span></span> <span data-ttu-id="43282-177">例如，您可以設定 SSH 服務要求公開金鑰驗證及單次密碼來增強安全性。</span><span class="sxs-lookup"><span data-stu-id="43282-177">For example, you can configure the SSH service to require public key authentication and a one-time password for added security.</span></span> <span data-ttu-id="43282-178">設定多重要素驗證不在本文件的討論範圍內。</span><span class="sxs-lookup"><span data-stu-id="43282-178">Configuration of multi-factor authentication is outside the scope of this documentation.</span></span> <span data-ttu-id="43282-179">請參閱 SSH 文件，以了解如何正確地設定多重要素驗證，並驗證它在 PowerShell 之外是否運作正常，再嘗試與 PowerShell 遠端功能搭配使用。</span><span class="sxs-lookup"><span data-stu-id="43282-179">Refer to documentation for SSH on how to correctly configure multi-factor authentication and validate it works outside of PowerShell before attempting to use it with PowerShell remoting.</span></span>

## <a name="powershell-remoting-example"></a><span data-ttu-id="43282-180">PowerShell 遠端範例</span><span class="sxs-lookup"><span data-stu-id="43282-180">PowerShell remoting example</span></span>

<span data-ttu-id="43282-181">測試遠端功能的最簡單方式是在單一電腦上進行試用。</span><span class="sxs-lookup"><span data-stu-id="43282-181">The easiest way to test remoting is to try it on a single computer.</span></span> <span data-ttu-id="43282-182">在此範例中，我們會建立回到相同 Linux 電腦的遠端工作階段。</span><span class="sxs-lookup"><span data-stu-id="43282-182">In this example, we create a remote session back to the same Linux computer.</span></span> <span data-ttu-id="43282-183">我們會以互動方式使用 PowerShell Cmdlet；因此，我們會看到要求驗證主機電腦的 SSH 提示以及密碼提示。</span><span class="sxs-lookup"><span data-stu-id="43282-183">We're using PowerShell cmdlets interactively so we see prompts from SSH asking to verify the host computer and prompting for a password.</span></span> <span data-ttu-id="43282-184">您可以在 Windows 電腦上執行相同的動作以確保遠端功能正在運作。</span><span class="sxs-lookup"><span data-stu-id="43282-184">You can do the same thing on a Windows computer to ensure remoting is working.</span></span> <span data-ttu-id="43282-185">接著，透過變更主機名稱，在電腦之間執行遠端功能。</span><span class="sxs-lookup"><span data-stu-id="43282-185">Then, remote between computers by changing the host name.</span></span>

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

### <a name="known-issues"></a><span data-ttu-id="43282-186">已知問題</span><span class="sxs-lookup"><span data-stu-id="43282-186">Known issues</span></span>

<span data-ttu-id="43282-187">**sudo** 命令不適用於 Linux 電腦的遠端工作階段。</span><span class="sxs-lookup"><span data-stu-id="43282-187">The **sudo** command doesn't work in a remote session to a Linux computer.</span></span>

## <a name="see-also"></a><span data-ttu-id="43282-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43282-188">See also</span></span>

[<span data-ttu-id="43282-189">在 Linux 上安裝 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="43282-189">Installing PowerShell Core on Linux</span></span>](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)

[<span data-ttu-id="43282-190">在 macOS 上安裝 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="43282-190">Installing PowerShell Core on macOS</span></span>](../../install/installing-powershell-core-on-macos.md)

[<span data-ttu-id="43282-191">在 Windows 上安裝 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="43282-191">Installing PowerShell Core on Windows</span></span>](../../install/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="43282-192">使用 OpenSSH 管理 Windows</span><span class="sxs-lookup"><span data-stu-id="43282-192">Manage Windows with OpenSSH</span></span>](/windows-server/administration/openssh/openssh_overview)

[<span data-ttu-id="43282-193">管理 OpenSSH 金鑰</span><span class="sxs-lookup"><span data-stu-id="43282-193">Managing OpenSSH Keys</span></span>](/windows-server/administration/openssh/openssh_keymanagement)

[<span data-ttu-id="43282-194">Ubuntu SSH</span><span class="sxs-lookup"><span data-stu-id="43282-194">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
