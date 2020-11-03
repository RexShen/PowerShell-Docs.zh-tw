---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSRemoting
ms.openlocfilehash: 0c8c386ab376afde3d15fcd29b3f653b3f738f63
ms.sourcegitcommit: 0e0f45d0d8deb8c9088a4f4a32218edde052b686
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2020
ms.locfileid: "93205307"
---
# <span data-ttu-id="c137c-103">Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="c137c-103">Enable-PSRemoting</span></span>

## <span data-ttu-id="c137c-104">概要</span><span class="sxs-lookup"><span data-stu-id="c137c-104">SYNOPSIS</span></span>
<span data-ttu-id="c137c-105">設定電腦接收遠端命令。</span><span class="sxs-lookup"><span data-stu-id="c137c-105">Configures the computer to receive remote commands.</span></span>

## <span data-ttu-id="c137c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c137c-106">SYNTAX</span></span>

```
Enable-PSRemoting [-Force] [-SkipNetworkProfileCheck] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="c137c-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="c137c-107">DESCRIPTION</span></span>

<span data-ttu-id="c137c-108">Cmdlet 會設定 `Enable-PSRemoting` 電腦以接收使用 WS-Management 技術傳送的 PowerShell 遠端命令。</span><span class="sxs-lookup"><span data-stu-id="c137c-108">The `Enable-PSRemoting` cmdlet configures the computer to receive PowerShell remote commands that are sent by using the WS-Management technology.</span></span>

<span data-ttu-id="c137c-109">Windows Server 2012 上預設會啟用 PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="c137c-109">PowerShell remoting is enabled by default on Windows Server 2012.</span></span> <span data-ttu-id="c137c-110">您可以使用在 `Enable-PSRemoting` 其他支援的 windows 版本上啟用 PowerShell 遠端功能，並在 Windows Server 2012 上重新啟用遠端功能（如果已停用）。</span><span class="sxs-lookup"><span data-stu-id="c137c-110">You can use `Enable-PSRemoting` to enable PowerShell remoting on other supported versions of Windows and to re-enable remoting on Windows Server 2012 if it becomes disabled.</span></span>

<span data-ttu-id="c137c-111">您只需在每一部將接收命令的電腦上執行此命令一次。</span><span class="sxs-lookup"><span data-stu-id="c137c-111">You have to run this command only one time on each computer that will receive commands.</span></span> <span data-ttu-id="c137c-112">您不需要在只傳送命令的電腦上執行它。</span><span class="sxs-lookup"><span data-stu-id="c137c-112">You do not have to run it on computers that only send commands.</span></span> <span data-ttu-id="c137c-113">因為設定會啟動接聽程式，所以最好只在需要時才執行。</span><span class="sxs-lookup"><span data-stu-id="c137c-113">Because the configuration starts listeners, it is prudent to run it only where it is needed.</span></span>

<span data-ttu-id="c137c-114">從 PowerShell 3.0 開始， `Enable-PSRemoting` 當電腦位於公用網路上時，此 Cmdlet 可以在用戶端版本的 Windows 上啟用 PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="c137c-114">Beginning in PowerShell 3.0, the `Enable-PSRemoting` cmdlet can enable PowerShell remoting on client versions of Windows when the computer is on a public network.</span></span> <span data-ttu-id="c137c-115">如需詳細資訊，請參閱 **SkipNetworkProfileCheck** 參數的描述。</span><span class="sxs-lookup"><span data-stu-id="c137c-115">For more information, see the description of the **SkipNetworkProfileCheck** parameter.</span></span>

<span data-ttu-id="c137c-116">此 `Enable-PSRemoting` Cmdlet 會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="c137c-116">The `Enable-PSRemoting` cmdlet performs the following operations:</span></span>

- <span data-ttu-id="c137c-117">執行 [>set-wsmanquickconfig](../Microsoft.WSMan.Management/Set-WSManQuickConfig.md) Cmdlet，此 Cmdlet 會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="c137c-117">Runs the [Set-WSManQuickConfig](../Microsoft.WSMan.Management/Set-WSManQuickConfig.md) cmdlet, which performs the following tasks:</span></span>
  - <span data-ttu-id="c137c-118">啟動 WinRM 服務。</span><span class="sxs-lookup"><span data-stu-id="c137c-118">Starts the WinRM service.</span></span>
  - <span data-ttu-id="c137c-119">將 WinRM 服務上的啟動類型設定為 [自動]。</span><span class="sxs-lookup"><span data-stu-id="c137c-119">Sets the startup type on the WinRM service to Automatic.</span></span>
  - <span data-ttu-id="c137c-120">建立接聽程式，以接受有關任何 IP 位址的要求。</span><span class="sxs-lookup"><span data-stu-id="c137c-120">Creates a listener to accept requests on any IP address.</span></span>
  - <span data-ttu-id="c137c-121">針對 WS-Management 通訊啟用防火牆例外。</span><span class="sxs-lookup"><span data-stu-id="c137c-121">Enables a firewall exception for WS-Management communications.</span></span>
  - <span data-ttu-id="c137c-122">註冊 **Microsoft powershell** 和 **microsoft. powershell** 會話設定（如果尚未註冊）。</span><span class="sxs-lookup"><span data-stu-id="c137c-122">Registers the **Microsoft.PowerShell** and **Microsoft.PowerShell.Workflow** session configurations, if it they are not already registered.</span></span>
  - <span data-ttu-id="c137c-123">註冊64位電腦上的 **microsoft.powershell32** 會話設定（如果尚未登錄）。</span><span class="sxs-lookup"><span data-stu-id="c137c-123">Registers the **Microsoft.PowerShell32** session configuration on 64-bit computers, if it is not already registered.</span></span>
  - <span data-ttu-id="c137c-124">啟用所有會話設定。</span><span class="sxs-lookup"><span data-stu-id="c137c-124">Enables all session configurations.</span></span>
  - <span data-ttu-id="c137c-125">變更所有會話設定的安全描述項，以允許遠端存取。</span><span class="sxs-lookup"><span data-stu-id="c137c-125">Changes the security descriptor of all session configurations to allow remote access.</span></span>
- <span data-ttu-id="c137c-126">重新開機 WinRM 服務，讓前述變更生效。</span><span class="sxs-lookup"><span data-stu-id="c137c-126">Restarts the WinRM service to make the preceding changes effective.</span></span>

<span data-ttu-id="c137c-127">若要在 Windows 平臺上執行此 Cmdlet，請使用 [以系統管理員身分執行] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="c137c-127">To run this cmdlet on the Windows platform, start PowerShell by using the Run as administrator option.</span></span> <span data-ttu-id="c137c-128">這並不適用于 Linux 或 MacOS 版本的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="c137c-128">This does not apply to Linux or MacOS versions of PowerShell.</span></span>

> [!CAUTION]
> <span data-ttu-id="c137c-129">在同時具有 PowerShell 3.0 和 PowerShell 2.0 的系統上，請勿使用 PowerShell 2.0 來執行 `Enable-PSRemoting` 和 `Disable-PSRemoting` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c137c-129">On systems that have both PowerShell 3.0 and PowerShell 2.0, do not use PowerShell 2.0 to run the `Enable-PSRemoting` and `Disable-PSRemoting` cmdlets.</span></span> <span data-ttu-id="c137c-130">命令可能會顯示成功，但並未正確設定遠端功能。</span><span class="sxs-lookup"><span data-stu-id="c137c-130">The commands might appear to succeed, but the remoting is not configured correctly.</span></span> <span data-ttu-id="c137c-131">遠端命令及稍後嘗試啟用和停用遠端處理的作業可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="c137c-131">Remote commands and later attempts to enable and disable remoting, are likely to fail.</span></span>

## <span data-ttu-id="c137c-132">範例</span><span class="sxs-lookup"><span data-stu-id="c137c-132">EXAMPLES</span></span>

### <span data-ttu-id="c137c-133">範例1：設定要接收遠端命令的電腦</span><span class="sxs-lookup"><span data-stu-id="c137c-133">Example 1: Configure a computer to receive remote commands</span></span>

<span data-ttu-id="c137c-134">這個命令會設定電腦接收遠端命令。</span><span class="sxs-lookup"><span data-stu-id="c137c-134">This command configures the computer to receive remote commands.</span></span>

```powershell
Enable-PSRemoting
```

### <span data-ttu-id="c137c-135">範例2：在沒有確認提示的情況下，設定電腦接收遠端命令</span><span class="sxs-lookup"><span data-stu-id="c137c-135">Example 2: Configure a computer to receive remote commands without a confirmation prompt</span></span>

<span data-ttu-id="c137c-136">這個命令會設定電腦接收遠端命令。</span><span class="sxs-lookup"><span data-stu-id="c137c-136">This command configures the computer to receive remote commands.</span></span>
<span data-ttu-id="c137c-137">**Force** 參數會抑制使用者提示。</span><span class="sxs-lookup"><span data-stu-id="c137c-137">The **Force** parameter suppresses the user prompts.</span></span>

```powershell
Enable-PSRemoting -Force
```

### <span data-ttu-id="c137c-138">範例3：允許用戶端上的遠端存取</span><span class="sxs-lookup"><span data-stu-id="c137c-138">Example 3: Allow remote access on clients</span></span>

<span data-ttu-id="c137c-139">此範例示範如何在用戶端版本的 Windows 作業系統上允許從公用網路進行遠端存取。</span><span class="sxs-lookup"><span data-stu-id="c137c-139">This example shows how to allow remote access from public networks on client versions of the Windows operating system.</span></span> <span data-ttu-id="c137c-140">不同版本的 Windows 可能會有不同的防火牆規則名稱。</span><span class="sxs-lookup"><span data-stu-id="c137c-140">The name of the firewall rule can be different for different versions of Windows.</span></span>
<span data-ttu-id="c137c-141">使用 `Get-NetFirewallRule` 以查看規則清單。</span><span class="sxs-lookup"><span data-stu-id="c137c-141">Use `Get-NetFirewallRule` to see a list of rules.</span></span> <span data-ttu-id="c137c-142">啟用防火牆規則之前，請先查看規則中的安全性設定，確認設定適用于您的環境。</span><span class="sxs-lookup"><span data-stu-id="c137c-142">Before enabling the firewall rule, view the security settings in the rule to verify that the configuration is appropriate for your environment.</span></span>

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

<span data-ttu-id="c137c-143">根據預設， `Enable-PSRemoting` 會建立允許從私人和網域網路進行遠端存取的網路規則。</span><span class="sxs-lookup"><span data-stu-id="c137c-143">By default, `Enable-PSRemoting` creates network rules that allow remote access from private and domain networks.</span></span> <span data-ttu-id="c137c-144">這個命令使用 **SkipNetworkProfileCheck** 參數，允許從同一個本機子網路中的公用網路進行遠端存取。</span><span class="sxs-lookup"><span data-stu-id="c137c-144">The command uses the **SkipNetworkProfileCheck** parameter to allow remote access from public networks in the same local subnet.</span></span> <span data-ttu-id="c137c-145">此命令會指定 **Force** 參數來抑制確認訊息。</span><span class="sxs-lookup"><span data-stu-id="c137c-145">The command specifies the **Force** parameter to suppress confirmation messages.</span></span>

<span data-ttu-id="c137c-146">**SkipNetworkProfileCheck** 參數不會影響伺服器版本的 Windows 作業系統，因此預設允許從同一個本機子網中的公用網路進行遠端存取。</span><span class="sxs-lookup"><span data-stu-id="c137c-146">The **SkipNetworkProfileCheck** parameter does not affect server versions of the Windows operating system, which allow remote access from public networks in the same local subnet by default.</span></span>

<span data-ttu-id="c137c-147">`Set-NetFirewallRule` **NetSecurity** 模組中的 Cmdlet 會加入防火牆規則，允許從任何遠端位置從公用網路進行遠端存取。</span><span class="sxs-lookup"><span data-stu-id="c137c-147">The `Set-NetFirewallRule` cmdlet in the **NetSecurity** module adds a firewall rule that allows remote access from public networks from any remote location.</span></span> <span data-ttu-id="c137c-148">這包括不同子網中的位置。</span><span class="sxs-lookup"><span data-stu-id="c137c-148">This includes locations in different subnets.</span></span>

> [!NOTE]
> <span data-ttu-id="c137c-149">根據 Windows 版本而定，防火牆規則的名稱可能會不同。</span><span class="sxs-lookup"><span data-stu-id="c137c-149">The name of the firewall rule can be different depending on the version of Windows.</span></span> <span data-ttu-id="c137c-150">使用 `Get-NetFirewallRule` Cmdlet 來列出您系統上的規則名稱。</span><span class="sxs-lookup"><span data-stu-id="c137c-150">Use the `Get-NetFirewallRule` cmdlet to list the names of the rules on your system.</span></span>

## <span data-ttu-id="c137c-151">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c137c-151">PARAMETERS</span></span>

### <span data-ttu-id="c137c-152">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c137c-152">-Confirm</span></span>

<span data-ttu-id="c137c-153">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="c137c-153">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="c137c-154">-Force</span><span class="sxs-lookup"><span data-stu-id="c137c-154">-Force</span></span>

<span data-ttu-id="c137c-155">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="c137c-155">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="c137c-156">-SkipNetworkProfileCheck</span><span class="sxs-lookup"><span data-stu-id="c137c-156">-SkipNetworkProfileCheck</span></span>

<span data-ttu-id="c137c-157">指出當電腦位於公用網路時，此 Cmdlet 會在用戶端版本的 Windows 作業系統上啟用遠端功能。</span><span class="sxs-lookup"><span data-stu-id="c137c-157">Indicates that this cmdlet enables remoting on client versions of the Windows operating system when the computer is on a public network.</span></span> <span data-ttu-id="c137c-158">此參數會針對公用網路啟用防火牆規則，以便只允許從位於相同本機子網路的電腦進行遠端存取。</span><span class="sxs-lookup"><span data-stu-id="c137c-158">This parameter enables a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="c137c-159">此參數不會影響伺服器版本的 Windows 作業系統，其預設會有公用網路的本機子網防火牆規則。</span><span class="sxs-lookup"><span data-stu-id="c137c-159">This parameter does not affect server versions of the Windows operating system, which, by default, have a local subnet firewall rule for public networks.</span></span> <span data-ttu-id="c137c-160">如果伺服器版本上的本機子網防火牆規則已停用， `Enable-PSRemoting` 不論此參數的值為何，都會重新啟用它。</span><span class="sxs-lookup"><span data-stu-id="c137c-160">If the local subnet firewall rule is disabled on a server version, `Enable-PSRemoting` re-enables it, regardless of the value of this parameter.</span></span>

<span data-ttu-id="c137c-161">若要移除本機子網限制，並允許從公用網路上的所有位置進行遠端存取，請使用 `Set-NetFirewallRule` **NetSecurity** 模組中的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c137c-161">To remove the local subnet restriction and enable remote access from all locations on public networks, use the `Set-NetFirewallRule` cmdlet in the **NetSecurity** module.</span></span>

<span data-ttu-id="c137c-162">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="c137c-162">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="c137c-163">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c137c-163">-WhatIf</span></span>

<span data-ttu-id="c137c-164">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="c137c-164">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="c137c-165">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="c137c-165">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="c137c-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c137c-166">CommonParameters</span></span>

<span data-ttu-id="c137c-167">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="c137c-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c137c-168">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="c137c-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c137c-169">輸入</span><span class="sxs-lookup"><span data-stu-id="c137c-169">INPUTS</span></span>

### <span data-ttu-id="c137c-170">無</span><span class="sxs-lookup"><span data-stu-id="c137c-170">None</span></span>

<span data-ttu-id="c137c-171">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c137c-171">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="c137c-172">輸出</span><span class="sxs-lookup"><span data-stu-id="c137c-172">OUTPUTS</span></span>

### <span data-ttu-id="c137c-173">System.String</span><span class="sxs-lookup"><span data-stu-id="c137c-173">System.String</span></span>

<span data-ttu-id="c137c-174">此 Cmdlet 會傳回描述其結果的字串。</span><span class="sxs-lookup"><span data-stu-id="c137c-174">This cmdlet returns strings that describe its results.</span></span>

## <span data-ttu-id="c137c-175">注意</span><span class="sxs-lookup"><span data-stu-id="c137c-175">NOTES</span></span>

<span data-ttu-id="c137c-176">在 PowerShell 3.0 中，會 `Enable-PSRemoting` 為 WS-Management 通訊建立下列防火牆例外。</span><span class="sxs-lookup"><span data-stu-id="c137c-176">In PowerShell 3.0, `Enable-PSRemoting` creates the following firewall exceptions for WS-Management communications.</span></span>

<span data-ttu-id="c137c-177">在伺服器版本的 Windows 作業系統上， `Enable-PSRemoting` 會針對允許遠端存取的私人和網域網路建立防火牆規則，並為公用網路建立防火牆規則，以允許從相同本機子網的電腦進行遠端存取。</span><span class="sxs-lookup"><span data-stu-id="c137c-177">On server versions of the Windows operating system, `Enable-PSRemoting` creates firewall rules for private and domain networks that allow remote access, and creates a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="c137c-178">在用戶端版本的 Windows 作業系統上， `Enable-PSRemoting` PowerShell 3.0 會為允許不受限制的遠端存取的私人和網域網路建立防火牆規則。</span><span class="sxs-lookup"><span data-stu-id="c137c-178">On client versions of the Windows operating system, `Enable-PSRemoting` in PowerShell 3.0 creates firewall rules for private and domain networks that allow unrestricted remote access.</span></span> <span data-ttu-id="c137c-179">若要針對允許從同一個本機子網路進行遠端存取的公用網路建立防火牆規則，請使用 **SkipNetworkProfileCheck** 參數。</span><span class="sxs-lookup"><span data-stu-id="c137c-179">To create a firewall rule for public networks that allows remote access from the same local subnet, use the **SkipNetworkProfileCheck** parameter.</span></span>

<span data-ttu-id="c137c-180">在用戶端或伺服器版本的 Windows 作業系統上，若要針對移除本機子網限制並允許遠端存取的公用網路建立防火牆規則，請使用 `Set-NetFirewallRule` NetSecurity 模組中的 Cmdlet 來執行下列命令： `Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any`</span><span class="sxs-lookup"><span data-stu-id="c137c-180">On client or server versions of the Windows operating system, to create a firewall rule for public networks that removes the local subnet restriction and allows remote access , use the `Set-NetFirewallRule` cmdlet in the NetSecurity module to run the following command: `Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any`</span></span>

<span data-ttu-id="c137c-181">在 PowerShell 2.0 中，會 `Enable-PSRemoting` 為 WS-Management 通訊建立下列防火牆例外。</span><span class="sxs-lookup"><span data-stu-id="c137c-181">In PowerShell 2.0, `Enable-PSRemoting` creates the following firewall exceptions for WS-Management communications.</span></span>

<span data-ttu-id="c137c-182">在伺服器版本的 Windows 作業系統上，它會針對允許遠端存取的所有網路建立防火牆規則。</span><span class="sxs-lookup"><span data-stu-id="c137c-182">On server versions of the Windows operating system, it creates firewall rules for all networks that allow remote access.</span></span>

<span data-ttu-id="c137c-183">在用戶端版本的 Windows 作業系統上， `Enable-PSRemoting` PowerShell 2.0 僅針對網域和私人網路位置建立防火牆例外。</span><span class="sxs-lookup"><span data-stu-id="c137c-183">On client versions of the Windows operating system, `Enable-PSRemoting` in PowerShell 2.0 creates a firewall exception only for domain and private network locations.</span></span> <span data-ttu-id="c137c-184">為了將安全性風險降至最低，不 `Enable-PSRemoting` 會在用戶端版本的 Windows 上建立公用網路的防火牆規則。</span><span class="sxs-lookup"><span data-stu-id="c137c-184">To minimize security risks, `Enable-PSRemoting` does not create a firewall rule for public networks on client versions of Windows.</span></span> <span data-ttu-id="c137c-185">當目前的網路位置是公用時，會傳回 `Enable-PSRemoting` 下列訊息：無法檢查防火牆的狀態。</span><span class="sxs-lookup"><span data-stu-id="c137c-185">When the current network location is public, `Enable-PSRemoting` returns the following message: Unable to check the status of the firewall.</span></span>

<span data-ttu-id="c137c-186">從 PowerShell 3.0 開始，會 `Enable-PSRemoting` 將所有會話設定的 **Enabled** 屬性值設定為，以啟用所有會話設定 `$True` 。</span><span class="sxs-lookup"><span data-stu-id="c137c-186">Starting in PowerShell 3.0, `Enable-PSRemoting` enables all session configurations by setting the value of the **Enabled** property of all session configurations to `$True`.</span></span>

<span data-ttu-id="c137c-187">在 PowerShell 2.0 中， `Enable-PSRemoting` 從會話設定的安全描述項中移除 **Deny_All** 設定。</span><span class="sxs-lookup"><span data-stu-id="c137c-187">In PowerShell 2.0, `Enable-PSRemoting` removes the **Deny_All** setting from the security descriptor of session configurations.</span></span> <span data-ttu-id="c137c-188">在 PowerShell 3.0 中， `Enable-PSRemoting` 移除 **Deny_All** ，並 **Network_Deny_All** 設定。</span><span class="sxs-lookup"><span data-stu-id="c137c-188">In PowerShell 3.0, `Enable-PSRemoting` removes the **Deny_All** and **Network_Deny_All** settings.</span></span> <span data-ttu-id="c137c-189">這可讓您從遠端存取保留給本機使用的會話設定。</span><span class="sxs-lookup"><span data-stu-id="c137c-189">This provides remote access to session configurations that were reserved for local use.</span></span>

## <span data-ttu-id="c137c-190">相關連結</span><span class="sxs-lookup"><span data-stu-id="c137c-190">RELATED LINKS</span></span>

[<span data-ttu-id="c137c-191">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="c137c-191">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="c137c-192">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="c137c-192">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="c137c-193">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="c137c-193">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="c137c-194">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="c137c-194">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="c137c-195">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="c137c-195">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="c137c-196">Disable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="c137c-196">Disable-PSRemoting</span></span>](Disable-PSRemoting.md)

[<span data-ttu-id="c137c-197">WSMan 提供者</span><span class="sxs-lookup"><span data-stu-id="c137c-197">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="c137c-198">about_Remote</span><span class="sxs-lookup"><span data-stu-id="c137c-198">about_Remote</span></span>](About/about_Remote.md)

[<span data-ttu-id="c137c-199">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="c137c-199">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)
