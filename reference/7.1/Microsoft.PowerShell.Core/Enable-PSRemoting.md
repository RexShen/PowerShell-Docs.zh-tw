---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSRemoting
ms.openlocfilehash: 893031f197f0be8996fdbec4bd316b70cf354825
ms.sourcegitcommit: 0e0f45d0d8deb8c9088a4f4a32218edde052b686
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2020
ms.locfileid: "93205300"
---
# <span data-ttu-id="ba005-103">Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="ba005-103">Enable-PSRemoting</span></span>

## <span data-ttu-id="ba005-104">概要</span><span class="sxs-lookup"><span data-stu-id="ba005-104">SYNOPSIS</span></span>
<span data-ttu-id="ba005-105">設定電腦接收遠端命令。</span><span class="sxs-lookup"><span data-stu-id="ba005-105">Configures the computer to receive remote commands.</span></span>

## <span data-ttu-id="ba005-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ba005-106">SYNTAX</span></span>

```
Enable-PSRemoting [-Force] [-SkipNetworkProfileCheck] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ba005-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="ba005-107">DESCRIPTION</span></span>

<span data-ttu-id="ba005-108">Cmdlet 會設定 `Enable-PSRemoting` 電腦以接收使用 WS-Management 技術傳送的 PowerShell 遠端命令。</span><span class="sxs-lookup"><span data-stu-id="ba005-108">The `Enable-PSRemoting` cmdlet configures the computer to receive PowerShell remote commands that are sent by using the WS-Management technology.</span></span> <span data-ttu-id="ba005-109">目前只有在 Windows 平臺上才支援以 WS-Management 為基礎的 PowerShell 遠端處理。</span><span class="sxs-lookup"><span data-stu-id="ba005-109">WS-Management based PowerShell remoting is currently supported only on Windows platform.</span></span>

<span data-ttu-id="ba005-110">預設會在 Windows Server 平臺上啟用 PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="ba005-110">PowerShell remoting is enabled by default on Windows Server platforms.</span></span> <span data-ttu-id="ba005-111">您可以使用在 `Enable-PSRemoting` 其他支援的 Windows 版本上啟用 PowerShell 遠端功能，並在停用時重新啟用遠端功能。</span><span class="sxs-lookup"><span data-stu-id="ba005-111">You can use `Enable-PSRemoting` to enable PowerShell remoting on other supported versions of Windows and to re-enable remoting if it becomes disabled.</span></span>

<span data-ttu-id="ba005-112">您只需在每一部將接收命令的電腦上執行此命令一次。</span><span class="sxs-lookup"><span data-stu-id="ba005-112">You have to run this command only one time on each computer that will receive commands.</span></span> <span data-ttu-id="ba005-113">您不需要在只傳送命令的電腦上執行它。</span><span class="sxs-lookup"><span data-stu-id="ba005-113">You do not have to run it on computers that only send commands.</span></span> <span data-ttu-id="ba005-114">由於設定會啟動接聽程式以接受遠端連線，因此最好只在需要時才執行。</span><span class="sxs-lookup"><span data-stu-id="ba005-114">Because the configuration starts listeners to accept remote connections, it is prudent to run it only where it is needed.</span></span>

<span data-ttu-id="ba005-115">當電腦位於公用網路上時，通常不允許在用戶端版本的 Windows 上啟用 PowerShell 遠端功能，但您可以使用 **SkipNetworkProfileCheck** 參數略過這項限制。</span><span class="sxs-lookup"><span data-stu-id="ba005-115">Enabling PowerShell remoting on client versions of Windows when the computer is on a public network is normally disallowed, but you can skip this restriction by using the **SkipNetworkProfileCheck** parameter.</span></span> <span data-ttu-id="ba005-116">如需詳細資訊，請參閱 **SkipNetworkProfileCheck** 參數的描述。</span><span class="sxs-lookup"><span data-stu-id="ba005-116">For more information, see the description of the **SkipNetworkProfileCheck** parameter.</span></span>

<span data-ttu-id="ba005-117">多個 PowerShell 安裝可以並存存在於單一電腦上。</span><span class="sxs-lookup"><span data-stu-id="ba005-117">Multiple PowerShell installations can exist side-by-side on a single computer.</span></span> <span data-ttu-id="ba005-118">`Enable-PSRemoting`執行會針對您在中執行 Cmdlet 的特定安裝版本，設定遠端端點。</span><span class="sxs-lookup"><span data-stu-id="ba005-118">Running `Enable-PSRemoting` will configure a remoting endpoint for the specific installation version that you are running the cmdlet in.</span></span> <span data-ttu-id="ba005-119">因此，如果您在執行 `Enable-PSRemoting` powershell 6.2 時執行，將會設定執行 powershell 6.2 的遠端端點。</span><span class="sxs-lookup"><span data-stu-id="ba005-119">So if you run `Enable-PSRemoting` while running PowerShell 6.2, a remoting endpoint will be configured that runs PowerShell 6.2.</span></span> <span data-ttu-id="ba005-120">如果您在執行 `Enable-PSRemoting` powershell 7-preview 時執行，將會設定執行 powershell 7-preview 的遠端端點。</span><span class="sxs-lookup"><span data-stu-id="ba005-120">If you run `Enable-PSRemoting` while running PowerShell 7-preview, a remoting endpoint will be configured that runs PowerShell 7-preview.</span></span>

<span data-ttu-id="ba005-121">`Enable-PSRemoting` 視需要建立兩個遠端端點設定。</span><span class="sxs-lookup"><span data-stu-id="ba005-121">`Enable-PSRemoting` creates two remoting endpoint configurations as needed.</span></span> <span data-ttu-id="ba005-122">如果端點設定已經存在，則只會確保已啟用。</span><span class="sxs-lookup"><span data-stu-id="ba005-122">If the endpoint configurations already exist, then they are simply ensured to be enabled.</span></span> <span data-ttu-id="ba005-123">建立的設定完全相同，但有不同的名稱。</span><span class="sxs-lookup"><span data-stu-id="ba005-123">The created configurations are identical but have different names.</span></span> <span data-ttu-id="ba005-124">其中一個會有一個簡單的名稱，對應至裝載會話的 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="ba005-124">One will have a simple name corresponding to the PowerShell version that hosts the session.</span></span> <span data-ttu-id="ba005-125">另一個設定名稱包含裝載會話之 PowerShell 版本的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="ba005-125">The other configuration name contains more detailed information about the PowerShell version which hosts the session.</span></span> <span data-ttu-id="ba005-126">例如， `Enable-PSRemoting` 在 PowerShell 6.2 中執行時，您會取得名為 **6.2.2** 的 **PowerShell.6** 兩個已設定端點。</span><span class="sxs-lookup"><span data-stu-id="ba005-126">For example, when running `Enable-PSRemoting` in PowerShell 6.2, you will get two configured endpoints named **PowerShell.6** , **PowerShell.6.2.2** .</span></span>
<span data-ttu-id="ba005-127">這可讓您使用簡單名稱 **powershell** 來建立最新 powershell 6 主機版本的連接。</span><span class="sxs-lookup"><span data-stu-id="ba005-127">This allows you to create a connection to the latest PowerShell 6 host version by using the simple name **PowerShell.6** .</span></span> <span data-ttu-id="ba005-128">或者，您可以使用較長的 **6.2.2** 名稱來連接到特定的 powershell 主機版本。</span><span class="sxs-lookup"><span data-stu-id="ba005-128">Or you can connect to a specific PowerShell host version by using the longer name **PowerShell.6.2.2** .</span></span>

<span data-ttu-id="ba005-129">若要使用新啟用的遠端端點，您必須在使用 **ConfigurationName** `Invoke-Command` 、 `New-PSSession` 、Cmdlet 建立遠端連線時，使用 ConfigurationName 參數來指定它們 `Enter-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="ba005-129">To use the newly enabled remoting endpoints, you must specify them by name with the **ConfigurationName** parameter when creating a remote connection using the `Invoke-Command`,`New-PSSession`,`Enter-PSSession` cmdlets.</span></span> <span data-ttu-id="ba005-130">如需詳細資訊，請參閱範例4。</span><span class="sxs-lookup"><span data-stu-id="ba005-130">For more information, see Example 4.</span></span>

<span data-ttu-id="ba005-131">此 `Enable-PSRemoting` Cmdlet 會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="ba005-131">The `Enable-PSRemoting` cmdlet performs the following operations:</span></span>

- <span data-ttu-id="ba005-132">執行 [>set-wsmanquickconfig](../Microsoft.WSMan.Management/Set-WSManQuickConfig.md) Cmdlet，此 Cmdlet 會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="ba005-132">Runs the [Set-WSManQuickConfig](../Microsoft.WSMan.Management/Set-WSManQuickConfig.md) cmdlet, which performs the following tasks:</span></span>
  - <span data-ttu-id="ba005-133">啟動 WinRM 服務。</span><span class="sxs-lookup"><span data-stu-id="ba005-133">Starts the WinRM service.</span></span>
  - <span data-ttu-id="ba005-134">將 WinRM 服務上的啟動類型設定為 [自動]。</span><span class="sxs-lookup"><span data-stu-id="ba005-134">Sets the startup type on the WinRM service to Automatic.</span></span>
  - <span data-ttu-id="ba005-135">建立接聽程式，以接受有關任何 IP 位址的要求。</span><span class="sxs-lookup"><span data-stu-id="ba005-135">Creates a listener to accept requests on any IP address.</span></span>
  - <span data-ttu-id="ba005-136">針對 WS-Management 通訊啟用防火牆例外。</span><span class="sxs-lookup"><span data-stu-id="ba005-136">Enables a firewall exception for WS-Management communications.</span></span>
  - <span data-ttu-id="ba005-137">視需要建立簡單和完整名稱交談端點設定。</span><span class="sxs-lookup"><span data-stu-id="ba005-137">Creates the simple and long name session endpoint configurations if needed.</span></span>
  - <span data-ttu-id="ba005-138">啟用所有會話設定。</span><span class="sxs-lookup"><span data-stu-id="ba005-138">Enables all session configurations.</span></span>
  - <span data-ttu-id="ba005-139">變更所有會話設定的安全描述項，以允許遠端存取。</span><span class="sxs-lookup"><span data-stu-id="ba005-139">Changes the security descriptor of all session configurations to allow remote access.</span></span>
- <span data-ttu-id="ba005-140">重新開機 WinRM 服務，讓前述變更生效。</span><span class="sxs-lookup"><span data-stu-id="ba005-140">Restarts the WinRM service to make the preceding changes effective.</span></span>

<span data-ttu-id="ba005-141">若要在 Windows 平臺上執行此 Cmdlet，請使用 [以系統管理員身分執行] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="ba005-141">To run this cmdlet on the Windows platform, start PowerShell by using the Run as administrator option.</span></span> <span data-ttu-id="ba005-142">Linux 或 MacOS 版本的 PowerShell 無法使用此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ba005-142">This cmdlet is not available on Linux or MacOS versions of PowerShell.</span></span>

> [!CAUTION]
> <span data-ttu-id="ba005-143">此 Cmdlet 不會影響 Windows PowerShell 所建立的遠端端點設定。</span><span class="sxs-lookup"><span data-stu-id="ba005-143">This cmdlet does not affect remote endpoint configurations created by Windows PowerShell.</span></span>
> <span data-ttu-id="ba005-144">它只會影響以 PowerShell 第6版和更新版本建立的端點。</span><span class="sxs-lookup"><span data-stu-id="ba005-144">It only affects endpoints created with PowerShell version 6 and greater.</span></span> <span data-ttu-id="ba005-145">若要啟用和停用 Windows PowerShell 所裝載的 PowerShell 遠端端點，請 `Enable-PSRemoting` 從 Windows PowerShell 會話內執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ba005-145">To enable and disable PowerShell remoting endpoints that are hosted by Windows PowerShell, run the `Enable-PSRemoting` cmdlet from within a Windows PowerShell session.</span></span>

## <span data-ttu-id="ba005-146">範例</span><span class="sxs-lookup"><span data-stu-id="ba005-146">EXAMPLES</span></span>

### <span data-ttu-id="ba005-147">範例1：設定要接收遠端命令的電腦</span><span class="sxs-lookup"><span data-stu-id="ba005-147">Example 1: Configure a computer to receive remote commands</span></span>

<span data-ttu-id="ba005-148">這個命令會設定電腦接收遠端命令。</span><span class="sxs-lookup"><span data-stu-id="ba005-148">This command configures the computer to receive remote commands.</span></span>

```powershell
Enable-PSRemoting
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.
```

### <span data-ttu-id="ba005-149">範例2：在沒有確認提示的情況下，設定電腦接收遠端命令</span><span class="sxs-lookup"><span data-stu-id="ba005-149">Example 2: Configure a computer to receive remote commands without a confirmation prompt</span></span>

<span data-ttu-id="ba005-150">這個命令會設定電腦接收遠端命令。</span><span class="sxs-lookup"><span data-stu-id="ba005-150">This command configures the computer to receive remote commands.</span></span>
<span data-ttu-id="ba005-151">**Force** 參數會抑制使用者提示。</span><span class="sxs-lookup"><span data-stu-id="ba005-151">The **Force** parameter suppresses the user prompts.</span></span>

```powershell
Enable-PSRemoting -Force
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.
```

### <span data-ttu-id="ba005-152">範例3：允許用戶端上的遠端存取</span><span class="sxs-lookup"><span data-stu-id="ba005-152">Example 3: Allow remote access on clients</span></span>

<span data-ttu-id="ba005-153">此範例示範如何在用戶端版本的 Windows 作業系統上允許從公用網路進行遠端存取。</span><span class="sxs-lookup"><span data-stu-id="ba005-153">This example shows how to allow remote access from public networks on client versions of the Windows operating system.</span></span> <span data-ttu-id="ba005-154">不同版本的 Windows 可能會有不同的防火牆規則名稱。</span><span class="sxs-lookup"><span data-stu-id="ba005-154">The name of the firewall rule can be different for different versions of Windows.</span></span>
<span data-ttu-id="ba005-155">使用 `Get-NetFirewallRule` 以查看規則清單。</span><span class="sxs-lookup"><span data-stu-id="ba005-155">Use `Get-NetFirewallRule` to see a list of rules.</span></span> <span data-ttu-id="ba005-156">啟用防火牆規則之前，請先查看規則中的安全性設定，確認設定適用于您的環境。</span><span class="sxs-lookup"><span data-stu-id="ba005-156">Before enabling the firewall rule, view the security settings in the rule to verify that the configuration is appropriate for your environment.</span></span>

```powershell
Get-NetFirewallRule -Name 'WINRM*' | Select-Object Name
```

```Output
Name
----
WINRM-HTTP-In-TCP-NoScope
WINRM-HTTP-In-TCP
WINRM-HTTP-Compat-In-TCP-NoScope
WINRM-HTTP-Compat-In-TCP
```

```powershell
Enable-PSRemoting -SkipNetworkProfileCheck -Force
Set-NetFirewallRule -Name 'WINRM-HTTP-In-TCP' -RemoteAddress Any
```

<span data-ttu-id="ba005-157">根據預設， `Enable-PSRemoting` 會建立允許從私人和網域網路進行遠端存取的網路規則。</span><span class="sxs-lookup"><span data-stu-id="ba005-157">By default, `Enable-PSRemoting` creates network rules that allow remote access from private and domain networks.</span></span> <span data-ttu-id="ba005-158">這個命令使用 **SkipNetworkProfileCheck** 參數，允許從同一個本機子網路中的公用網路進行遠端存取。</span><span class="sxs-lookup"><span data-stu-id="ba005-158">The command uses the **SkipNetworkProfileCheck** parameter to allow remote access from public networks in the same local subnet.</span></span> <span data-ttu-id="ba005-159">此命令會指定 **Force** 參數來抑制確認訊息。</span><span class="sxs-lookup"><span data-stu-id="ba005-159">The command specifies the **Force** parameter to suppress confirmation messages.</span></span>

<span data-ttu-id="ba005-160">**SkipNetworkProfileCheck** 參數不會影響伺服器版本的 Windows 作業系統，因此預設允許從同一個本機子網中的公用網路進行遠端存取。</span><span class="sxs-lookup"><span data-stu-id="ba005-160">The **SkipNetworkProfileCheck** parameter does not affect server versions of the Windows operating system, which allow remote access from public networks in the same local subnet by default.</span></span>

<span data-ttu-id="ba005-161">`Set-NetFirewallRule` **NetSecurity** 模組中的 Cmdlet 會加入防火牆規則，允許從任何遠端位置從公用網路進行遠端存取。</span><span class="sxs-lookup"><span data-stu-id="ba005-161">The `Set-NetFirewallRule` cmdlet in the **NetSecurity** module adds a firewall rule that allows remote access from public networks from any remote location.</span></span> <span data-ttu-id="ba005-162">這包括不同子網中的位置。</span><span class="sxs-lookup"><span data-stu-id="ba005-162">This includes locations in different subnets.</span></span>

### <span data-ttu-id="ba005-163">範例4：建立新啟用端點設定的遠端會話</span><span class="sxs-lookup"><span data-stu-id="ba005-163">Example 4: Create a remote session to the newly enabled endpoint configuration</span></span>

<span data-ttu-id="ba005-164">此範例說明如何在電腦上啟用 PowerShell 遠端功能、尋找已設定的端點名稱，以及建立指向其中一個端點的遠端會話。</span><span class="sxs-lookup"><span data-stu-id="ba005-164">This example shows how to enable PowerShell remoting on a computer, find the configured endpoint names, and create a remote session to one of the endpoints.</span></span>

<span data-ttu-id="ba005-165">第一個命令會在電腦上啟用 PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="ba005-165">The first command enables PowerShell remoting on the computer.</span></span>

<span data-ttu-id="ba005-166">第二個命令會列出端點設定。</span><span class="sxs-lookup"><span data-stu-id="ba005-166">The second command lists the endpoint configurations.</span></span>

<span data-ttu-id="ba005-167">第三個命令會在同一部電腦上建立遠端 PowerShell 會話，並依名稱指定 **PowerShell 6** 端點。</span><span class="sxs-lookup"><span data-stu-id="ba005-167">The third command creates a remote PowerShell session to the same machine, specifying the **PowerShell.6** endpoint by name.</span></span> <span data-ttu-id="ba005-168">遠端會話將使用最新的 PowerShell 6 版 (6.2.2) 來裝載。</span><span class="sxs-lookup"><span data-stu-id="ba005-168">The remote session will be hosted with the latest PowerShell 6 version (6.2.2).</span></span>

<span data-ttu-id="ba005-169">最後一個命令會存取 `$PSVersionTable` 遠端會話中的變數，以顯示裝載會話的 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="ba005-169">The last command accesses the `$PSVersionTable` variable in the remote session to display the PowerShell version that is hosting the session.</span></span>

```powershell
Enable-PSRemoting -Force

Get-PSSessionConfiguration

$session = New-PSSession -ComputerName localhost -ConfigurationName PowerShell.6

Invoke-Command -Session $session -ScriptBlock { $PSVersionTable }
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.

Name          : PowerShell.6
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6.2.2
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                BUILTIN\Remote Management Users AccessAllowed

Name                           Value
----                           -----
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0…}
PSEdition                      Core
PSRemotingProtocolVersion      2.3
Platform                       Win32NT
SerializationVersion           1.1.0.1
GitCommitId                    6.2.2
WSManStackVersion              3.0
PSVersion                      6.2.2
OS                             Microsoft Windows 10.0.18363
```

> [!NOTE]
> <span data-ttu-id="ba005-170">根據 Windows 版本而定，防火牆規則的名稱可能會不同。</span><span class="sxs-lookup"><span data-stu-id="ba005-170">The name of the firewall rule can be different depending on the version of Windows.</span></span> <span data-ttu-id="ba005-171">使用 `Get-NetFirewallRule` Cmdlet 來列出您系統上的規則名稱。</span><span class="sxs-lookup"><span data-stu-id="ba005-171">Use the `Get-NetFirewallRule` cmdlet to list the names of the rules on your system.</span></span>

## <span data-ttu-id="ba005-172">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ba005-172">PARAMETERS</span></span>

### <span data-ttu-id="ba005-173">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ba005-173">-Confirm</span></span>

<span data-ttu-id="ba005-174">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="ba005-174">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ba005-175">-Force</span><span class="sxs-lookup"><span data-stu-id="ba005-175">-Force</span></span>

<span data-ttu-id="ba005-176">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="ba005-176">Forces the command to run without asking for user confirmation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ba005-177">-SkipNetworkProfileCheck</span><span class="sxs-lookup"><span data-stu-id="ba005-177">-SkipNetworkProfileCheck</span></span>

<span data-ttu-id="ba005-178">指出當電腦位於公用網路時，此 Cmdlet 會在用戶端版本的 Windows 作業系統上啟用遠端功能。</span><span class="sxs-lookup"><span data-stu-id="ba005-178">Indicates that this cmdlet enables remoting on client versions of the Windows operating system when the computer is on a public network.</span></span> <span data-ttu-id="ba005-179">此參數會針對公用網路啟用防火牆規則，以便只允許從位於相同本機子網路的電腦進行遠端存取。</span><span class="sxs-lookup"><span data-stu-id="ba005-179">This parameter enables a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="ba005-180">此參數不會影響伺服器版本的 Windows 作業系統，其預設會有公用網路的本機子網防火牆規則。</span><span class="sxs-lookup"><span data-stu-id="ba005-180">This parameter does not affect server versions of the Windows operating system, which, by default, have a local subnet firewall rule for public networks.</span></span> <span data-ttu-id="ba005-181">如果伺服器版本上的本機子網防火牆規則已停用， `Enable-PSRemoting` 不論此參數的值為何，都會重新啟用它。</span><span class="sxs-lookup"><span data-stu-id="ba005-181">If the local subnet firewall rule is disabled on a server version, `Enable-PSRemoting` re-enables it, regardless of the value of this parameter.</span></span>

<span data-ttu-id="ba005-182">若要移除本機子網限制，並允許從公用網路上的所有位置進行遠端存取，請使用 `Set-NetFirewallRule` **NetSecurity** 模組中的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ba005-182">To remove the local subnet restriction and enable remote access from all locations on public networks, use the `Set-NetFirewallRule` cmdlet in the **NetSecurity** module.</span></span>

<span data-ttu-id="ba005-183">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="ba005-183">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ba005-184">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ba005-184">-WhatIf</span></span>

<span data-ttu-id="ba005-185">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="ba005-185">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="ba005-186">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="ba005-186">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ba005-187">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ba005-187">CommonParameters</span></span>

<span data-ttu-id="ba005-188">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="ba005-188">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ba005-189">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="ba005-189">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ba005-190">輸入</span><span class="sxs-lookup"><span data-stu-id="ba005-190">INPUTS</span></span>

### <span data-ttu-id="ba005-191">無</span><span class="sxs-lookup"><span data-stu-id="ba005-191">None</span></span>

<span data-ttu-id="ba005-192">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ba005-192">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="ba005-193">輸出</span><span class="sxs-lookup"><span data-stu-id="ba005-193">OUTPUTS</span></span>

### <span data-ttu-id="ba005-194">System.String</span><span class="sxs-lookup"><span data-stu-id="ba005-194">System.String</span></span>

<span data-ttu-id="ba005-195">此 Cmdlet 會傳回描述其結果的字串。</span><span class="sxs-lookup"><span data-stu-id="ba005-195">This cmdlet returns strings that describe its results.</span></span>

## <span data-ttu-id="ba005-196">注意</span><span class="sxs-lookup"><span data-stu-id="ba005-196">NOTES</span></span>

<span data-ttu-id="ba005-197">在伺服器版本的 Windows 作業系統上， `Enable-PSRemoting` 會針對允許遠端存取的私人和網域網路建立防火牆規則，並為公用網路建立防火牆規則，以允許從相同本機子網的電腦進行遠端存取。</span><span class="sxs-lookup"><span data-stu-id="ba005-197">On server versions of the Windows operating system, `Enable-PSRemoting` creates firewall rules for private and domain networks that allow remote access, and creates a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="ba005-198">在用戶端版本的 Windows 作業系統上， `Enable-PSRemoting` 會針對允許不受限制的遠端存取的私人和網域網路建立防火牆規則。</span><span class="sxs-lookup"><span data-stu-id="ba005-198">On client versions of the Windows operating system, `Enable-PSRemoting` creates firewall rules for private and domain networks that allow unrestricted remote access.</span></span> <span data-ttu-id="ba005-199">若要針對允許從同一個本機子網路進行遠端存取的公用網路建立防火牆規則，請使用 **SkipNetworkProfileCheck** 參數。</span><span class="sxs-lookup"><span data-stu-id="ba005-199">To create a firewall rule for public networks that allows remote access from the same local subnet, use the **SkipNetworkProfileCheck** parameter.</span></span>

<span data-ttu-id="ba005-200">在用戶端或伺服器版本的 Windows 作業系統上，若要針對移除本機子網限制並允許遠端存取的公用網路建立防火牆規則，請使用 `Set-NetFirewallRule` NetSecurity 模組中的 Cmdlet 來執行下列命令： `Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any`</span><span class="sxs-lookup"><span data-stu-id="ba005-200">On client or server versions of the Windows operating system, to create a firewall rule for public networks that removes the local subnet restriction and allows remote access , use the `Set-NetFirewallRule` cmdlet in the NetSecurity module to run the following command: `Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any`</span></span>

<span data-ttu-id="ba005-201">`Enable-PSRemoting` 藉由將所有會話設定的 **Enabled** 屬性值設定為，以啟用所有會話設定 `$True` 。</span><span class="sxs-lookup"><span data-stu-id="ba005-201">`Enable-PSRemoting` enables all session configurations by setting the value of the **Enabled** property of all session configurations to `$True`.</span></span>

<span data-ttu-id="ba005-202">`Enable-PSRemoting` 移除 **Deny_All** 並 **Network_Deny_All** 設定。</span><span class="sxs-lookup"><span data-stu-id="ba005-202">`Enable-PSRemoting` removes the **Deny_All** and **Network_Deny_All** settings.</span></span> <span data-ttu-id="ba005-203">這可讓您從遠端存取保留給本機使用的會話設定。</span><span class="sxs-lookup"><span data-stu-id="ba005-203">This provides remote access to session configurations that were reserved for local use.</span></span>

## <span data-ttu-id="ba005-204">相關連結</span><span class="sxs-lookup"><span data-stu-id="ba005-204">RELATED LINKS</span></span>

[<span data-ttu-id="ba005-205">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ba005-205">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="ba005-206">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ba005-206">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="ba005-207">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ba005-207">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="ba005-208">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ba005-208">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="ba005-209">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ba005-209">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="ba005-210">Disable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="ba005-210">Disable-PSRemoting</span></span>](Disable-PSRemoting.md)

[<span data-ttu-id="ba005-211">WSMan 提供者</span><span class="sxs-lookup"><span data-stu-id="ba005-211">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="ba005-212">about_Remote</span><span class="sxs-lookup"><span data-stu-id="ba005-212">about_Remote</span></span>](About/about_Remote.md)

[<span data-ttu-id="ba005-213">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="ba005-213">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)
