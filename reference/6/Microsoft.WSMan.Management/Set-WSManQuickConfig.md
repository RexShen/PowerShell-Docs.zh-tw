---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 10/02/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/set-wsmanquickconfig?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WSManQuickConfig
ms.openlocfilehash: e8bc5bc248eafe479f366397aa947845e94e190c
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2020
ms.locfileid: "93206203"
---
# <span data-ttu-id="b5f28-103">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="b5f28-103">Set-WSManQuickConfig</span></span>

## <span data-ttu-id="b5f28-104">概要</span><span class="sxs-lookup"><span data-stu-id="b5f28-104">SYNOPSIS</span></span>
<span data-ttu-id="b5f28-105">針對遠端管理設定本機電腦。</span><span class="sxs-lookup"><span data-stu-id="b5f28-105">Configures the local computer for remote management.</span></span>

## <span data-ttu-id="b5f28-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b5f28-106">SYNTAX</span></span>

### <span data-ttu-id="b5f28-107">全部</span><span class="sxs-lookup"><span data-stu-id="b5f28-107">All</span></span>

```
Set-WSManQuickConfig [-UseSSL] [-Force] [-SkipNetworkProfileCheck] [<CommonParameters>]
```

## <span data-ttu-id="b5f28-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b5f28-108">DESCRIPTION</span></span>

<span data-ttu-id="b5f28-109">Cmdlet 會設定 `Set-WSManQuickConfig` 電腦，以接收使用 Web Services For management (ws-management) 技術傳送的 PowerShell 遠端命令。</span><span class="sxs-lookup"><span data-stu-id="b5f28-109">The `Set-WSManQuickConfig` cmdlet configures the computer to receive PowerShell remote commands that are sent by using the Web Services for Management (WS-Management) technology.</span></span>

<span data-ttu-id="b5f28-110">`Set-WSManQuickConfig` 會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="b5f28-110">`Set-WSManQuickConfig` performs the following actions:</span></span>

- <span data-ttu-id="b5f28-111">檢查 WinRM 服務是否正在執行。</span><span class="sxs-lookup"><span data-stu-id="b5f28-111">Checks whether the WinRM service is running.</span></span> <span data-ttu-id="b5f28-112">如果 WinRM 服務未執行，則會啟動服務。</span><span class="sxs-lookup"><span data-stu-id="b5f28-112">If the WinRM service isn't running, the service is started.</span></span>
- <span data-ttu-id="b5f28-113">將 WinRM 服務的啟動類型設定為自動。</span><span class="sxs-lookup"><span data-stu-id="b5f28-113">Sets the WinRM service startup type to automatic.</span></span>
- <span data-ttu-id="b5f28-114">建立接聽程式，以接受有關任何 IP 位址的要求。</span><span class="sxs-lookup"><span data-stu-id="b5f28-114">Creates a listener to accept requests on any IP address.</span></span> <span data-ttu-id="b5f28-115">預設傳輸為 **HTTP** 。</span><span class="sxs-lookup"><span data-stu-id="b5f28-115">The default transport is **HTTP** .</span></span>
- <span data-ttu-id="b5f28-116">為 WinRM 流量啟用防火牆例外。</span><span class="sxs-lookup"><span data-stu-id="b5f28-116">Enables a firewall exception for WinRM traffic.</span></span>

<span data-ttu-id="b5f28-117">若要執行 `Set-WSManQuickConfig` ，請使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="b5f28-117">To run `Set-WSManQuickConfig`, start PowerShell with the **Run as Administrator** option.</span></span>

## <span data-ttu-id="b5f28-118">範例</span><span class="sxs-lookup"><span data-stu-id="b5f28-118">EXAMPLES</span></span>

### <span data-ttu-id="b5f28-119">範例 1︰透過 HTTP 啟用本機電腦的遠端管理</span><span class="sxs-lookup"><span data-stu-id="b5f28-119">Example 1: Enable remote management of the local computer over HTTP</span></span>

<span data-ttu-id="b5f28-120">此範例會設定必要的設定，以啟用本機電腦的遠端系統管理。</span><span class="sxs-lookup"><span data-stu-id="b5f28-120">This example sets the required configuration to enable remote management of the local computer.</span></span> <span data-ttu-id="b5f28-121">根據預設，此命令會在 **HTTP** 上建立 WS-Management 接聽程式。</span><span class="sxs-lookup"><span data-stu-id="b5f28-121">By default, this command creates a WS-Management listener on **HTTP** .</span></span>

```powershell
Set-WSManQuickConfig
```

### <span data-ttu-id="b5f28-122">範例 2︰透過 HTTPS 啟用本機電腦的遠端管理</span><span class="sxs-lookup"><span data-stu-id="b5f28-122">Example 2: Enable remote management of the local computer over HTTPS</span></span>

<span data-ttu-id="b5f28-123">此範例會設定必要的設定，以啟用本機電腦的遠端系統管理。</span><span class="sxs-lookup"><span data-stu-id="b5f28-123">This example sets the required configuration to enable remote management of the local computer.</span></span> <span data-ttu-id="b5f28-124">**UseSSL** 參數會指定使用 **HTTPS** 來與電腦通訊。</span><span class="sxs-lookup"><span data-stu-id="b5f28-124">The **UseSSL** parameter specifies that **HTTPS** is used to communicate with the computer.</span></span>

```powershell
Set-WSManQuickConfig -UseSSL
```

> [!NOTE]
> <span data-ttu-id="b5f28-125">**HTTPS** 需要手動設定。</span><span class="sxs-lookup"><span data-stu-id="b5f28-125">**HTTPS** requires manual configuration.</span></span> <span data-ttu-id="b5f28-126">如需詳細資訊，請參閱 **UseSSL** 參數的描述。</span><span class="sxs-lookup"><span data-stu-id="b5f28-126">For more information, see the **UseSSL** parameter's description.</span></span>

## <span data-ttu-id="b5f28-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b5f28-127">PARAMETERS</span></span>

### <span data-ttu-id="b5f28-128">-Force</span><span class="sxs-lookup"><span data-stu-id="b5f28-128">-Force</span></span>

<span data-ttu-id="b5f28-129">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="b5f28-129">Forces the command to run without asking for user confirmation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5f28-130">-SkipNetworkProfileCheck</span><span class="sxs-lookup"><span data-stu-id="b5f28-130">-SkipNetworkProfileCheck</span></span>

<span data-ttu-id="b5f28-131">當電腦位於公用網路時，設定 Windows 用戶端版本進行遠端處理。</span><span class="sxs-lookup"><span data-stu-id="b5f28-131">Configures Windows client versions for remoting when the computer is on a public network.</span></span> <span data-ttu-id="b5f28-132">此參數會針對公用網路啟用防火牆規則，以便只允許從位於相同本機子網路的電腦進行遠端存取。</span><span class="sxs-lookup"><span data-stu-id="b5f28-132">This parameter enables a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span>

<span data-ttu-id="b5f28-133">此參數不會影響 Windows server 版本，預設為具有公用網路的本機子網防火牆規則。</span><span class="sxs-lookup"><span data-stu-id="b5f28-133">This parameter has no effect on server versions of Windows, that by default, have a local subnet firewall rule for public networks.</span></span> <span data-ttu-id="b5f28-134">如果伺服器版本的 Windows 上已停用本機子網防火牆規則， `Enable-PSRemoting` 則不論此參數的值為何，都會重新啟用它。</span><span class="sxs-lookup"><span data-stu-id="b5f28-134">If the local subnet firewall rule is disabled on the server version of Windows, `Enable-PSRemoting` re-enables it, regardless of this parameter's value.</span></span>

<span data-ttu-id="b5f28-135">若要移除本機子網限制，並允許從公用網路上的所有位置進行遠端存取，請使用 `Set-NetFirewallRule` **NetSecurity** 模組中的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b5f28-135">To remove the local subnet restriction and enable remote access from all locations on public networks, use the `Set-NetFirewallRule` cmdlet in the **NetSecurity** module.</span></span>

<span data-ttu-id="b5f28-136">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="b5f28-136">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5f28-137">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="b5f28-137">-UseSSL</span></span>

<span data-ttu-id="b5f28-138">指定使用安全通訊端層 (SSL) 通訊協定來建立遠端電腦連線。</span><span class="sxs-lookup"><span data-stu-id="b5f28-138">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span> <span data-ttu-id="b5f28-139">預設不會使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="b5f28-139">By default, SSL isn't used.</span></span>

<span data-ttu-id="b5f28-140">WS-Management 會加密透過網路傳輸的所有 PowerShell 內容。</span><span class="sxs-lookup"><span data-stu-id="b5f28-140">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span> <span data-ttu-id="b5f28-141">**UseSSL** 參數可讓您指定 HTTPS （而非 HTTP）的額外保護。</span><span class="sxs-lookup"><span data-stu-id="b5f28-141">The **UseSSL** parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span> <span data-ttu-id="b5f28-142">如果您使用此參數，而且在用於連線的埠上無法使用 SSL，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="b5f28-142">If you use this parameter and SSL isn't available on the port that's used for the connection, the command fails.</span></span>

<span data-ttu-id="b5f28-143">**HTTPS** 需要手動設定 WinRM 和防火牆規則。</span><span class="sxs-lookup"><span data-stu-id="b5f28-143">**HTTPS** requires manual configuration of WinRM and firewall rules.</span></span> <span data-ttu-id="b5f28-144">如需詳細資訊，請參閱 how [To：設定 WINRM FOR HTTPS](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https)。</span><span class="sxs-lookup"><span data-stu-id="b5f28-144">For more information, see [How To: Configure WINRM for HTTPS](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5f28-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b5f28-145">CommonParameters</span></span>

<span data-ttu-id="b5f28-146">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="b5f28-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b5f28-147">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="b5f28-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b5f28-148">輸入</span><span class="sxs-lookup"><span data-stu-id="b5f28-148">INPUTS</span></span>

### <span data-ttu-id="b5f28-149">無</span><span class="sxs-lookup"><span data-stu-id="b5f28-149">None</span></span>

<span data-ttu-id="b5f28-150">此 Cmdlet 不接受任何輸入。</span><span class="sxs-lookup"><span data-stu-id="b5f28-150">This cmdlet doesn't accept any input.</span></span>

## <span data-ttu-id="b5f28-151">輸出</span><span class="sxs-lookup"><span data-stu-id="b5f28-151">OUTPUTS</span></span>

### <span data-ttu-id="b5f28-152">無</span><span class="sxs-lookup"><span data-stu-id="b5f28-152">None</span></span>

<span data-ttu-id="b5f28-153">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="b5f28-153">This cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="b5f28-154">注意</span><span class="sxs-lookup"><span data-stu-id="b5f28-154">NOTES</span></span>

## <span data-ttu-id="b5f28-155">相關連結</span><span class="sxs-lookup"><span data-stu-id="b5f28-155">RELATED LINKS</span></span>

[<span data-ttu-id="b5f28-156">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="b5f28-156">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="b5f28-157">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="b5f28-157">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="b5f28-158">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="b5f28-158">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="b5f28-159">Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="b5f28-159">Enable-PSRemoting</span></span>](../Microsoft.PowerShell.Core/Enable-PSRemoting.md)

[<span data-ttu-id="b5f28-160">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="b5f28-160">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="b5f28-161">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="b5f28-161">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="b5f28-162">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="b5f28-162">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="b5f28-163">如何：為 HTTPS 設定 WINRM</span><span class="sxs-lookup"><span data-stu-id="b5f28-163">How To: Configure WINRM for HTTPS</span></span>](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https)

[<span data-ttu-id="b5f28-164">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="b5f28-164">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="b5f28-165">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="b5f28-165">New-PSSession</span></span>](../Microsoft.PowerShell.Core/New-PSSession.md)

[<span data-ttu-id="b5f28-166">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="b5f28-166">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="b5f28-167">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="b5f28-167">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="b5f28-168">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="b5f28-168">Test-WSMan</span></span>](Test-WSMan.md)
