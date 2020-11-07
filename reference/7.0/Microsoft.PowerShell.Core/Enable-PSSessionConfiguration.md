---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-pssessionconfiguration?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSSessionConfiguration
ms.openlocfilehash: 6c8c64161ef674e3a9babaa7ad18c33b3f18cbf0
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344434"
---
# <span data-ttu-id="79003-103">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="79003-103">Enable-PSSessionConfiguration</span></span>

## <span data-ttu-id="79003-104">概要</span><span class="sxs-lookup"><span data-stu-id="79003-104">SYNOPSIS</span></span>
<span data-ttu-id="79003-105">啟用本機電腦上的工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="79003-105">Enables the session configurations on the local computer.</span></span>

## <span data-ttu-id="79003-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="79003-106">SYNTAX</span></span>

```
Enable-PSSessionConfiguration [[-Name] <String[]>] [-Force] [-SecurityDescriptorSddl <String>]
 [-SkipNetworkProfileCheck] [-NoServiceRestart] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="79003-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="79003-107">DESCRIPTION</span></span>

<span data-ttu-id="79003-108">`Enable-PSSessionConfiguration`Cmdlet 會啟用已停用的已註冊會話設定，例如使用 `Disable-PSSessionConfiguration` 或 `Disable-PSRemoting` Cmdlet，或的 **AccessMode** 參數 `Register-PSSessionConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="79003-108">The `Enable-PSSessionConfiguration` cmdlet enables registered session configurations that have been disabled, such as by using the `Disable-PSSessionConfiguration` or `Disable-PSRemoting` cmdlets, or the **AccessMode** parameter of `Register-PSSessionConfiguration`.</span></span> <span data-ttu-id="79003-109">這是一個進階的 Cmdlet，專門設計給系統管理員用於管理其使用者的自訂工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="79003-109">This is an advanced cmdlet that is designed to be used by system administrators to manage customized session configurations for their users.</span></span>

<span data-ttu-id="79003-110">如果沒有參數，則會 `Enable-PSSessionConfiguration` 啟用 **Microsoft PowerShell** 設定，這是用於會話的預設設定。</span><span class="sxs-lookup"><span data-stu-id="79003-110">Without parameters, `Enable-PSSessionConfiguration` enables the **Microsoft.PowerShell** configuration, which is the default configuration that is used for sessions.</span></span>

<span data-ttu-id="79003-111">`Enable-PSSessionConfiguration` 從受影響之會話設定的安全描述項中移除 **Deny_All** 設定、開啟接受任何 IP 位址要求的接聽程式，然後重新開機 WinRM 服務。</span><span class="sxs-lookup"><span data-stu-id="79003-111">`Enable-PSSessionConfiguration` removes the **Deny_All** setting from the security descriptor of the affected session configurations, turns on the listener that accepts requests on any IP address, and restarts the WinRM service.</span></span> <span data-ttu-id="79003-112">從 PowerShell 3.0 開始， `Enable-PSSessionConfiguration` 也會將會話設定的 **Enabled** 屬性值 (`WSMan:\<computer>\PlugIn\<SessionConfigurationName>\Enabled`) 設定為 True。</span><span class="sxs-lookup"><span data-stu-id="79003-112">Beginning in PowerShell 3.0, `Enable-PSSessionConfiguration` also sets the value of the **Enabled** property of the session configuration (`WSMan:\<computer>\PlugIn\<SessionConfigurationName>\Enabled`) to True.</span></span> <span data-ttu-id="79003-113">但是，不 `Enable-PSSessionConfiguration` 會移除或變更 **Network_Deny_All** (`AccessMode=Local`) 安全描述項設定，只允許本機電腦的使用者使用會話設定。</span><span class="sxs-lookup"><span data-stu-id="79003-113">However, `Enable-PSSessionConfiguration` does not remove or change the **Network_Deny_All** (`AccessMode=Local`) security descriptor setting that allows only users of the local computer to use to the session configuration.</span></span>

## <span data-ttu-id="79003-114">範例</span><span class="sxs-lookup"><span data-stu-id="79003-114">EXAMPLES</span></span>

### <span data-ttu-id="79003-115">範例1：重新啟用預設會話</span><span class="sxs-lookup"><span data-stu-id="79003-115">Example 1: Re-enable the default session</span></span>

<span data-ttu-id="79003-116">此範例會重新啟用電腦上的 **Microsoft PowerShell** 預設會話設定。</span><span class="sxs-lookup"><span data-stu-id="79003-116">This example re-enables the **Microsoft.PowerShell** default session configuration on the computer.</span></span>

```powershell
Enable-PSSessionConfiguration
```

### <span data-ttu-id="79003-117">範例2：重新啟用指定的會話</span><span class="sxs-lookup"><span data-stu-id="79003-117">Example 2: Re-enable specified sessions</span></span>

<span data-ttu-id="79003-118">此範例會重新啟用電腦上的 **MaintenanceShell** 和 **AdminShell** 會話設定。</span><span class="sxs-lookup"><span data-stu-id="79003-118">This example re-enables the **MaintenanceShell** and **AdminShell** session configurations on the computer.</span></span>

```powershell
Enable-PSSessionConfiguration -Name MaintenanceShell, AdminShell
```

### <span data-ttu-id="79003-119">範例3：重新啟用所有會話</span><span class="sxs-lookup"><span data-stu-id="79003-119">Example 3: Re-enable the all sessions</span></span>

<span data-ttu-id="79003-120">此範例會重新啟用電腦上的所有會話設定。</span><span class="sxs-lookup"><span data-stu-id="79003-120">This example re-enables all session configurations on the computer.</span></span> <span data-ttu-id="79003-121">這些命令是相等的。</span><span class="sxs-lookup"><span data-stu-id="79003-121">These commands are equivalent.</span></span>
<span data-ttu-id="79003-122">因此，您可以使用其中一種。</span><span class="sxs-lookup"><span data-stu-id="79003-122">Therefore, you can use either.</span></span>

```powershell
Enable-PSSessionConfiguration -Name *
Get-PSSessionConfiguration | Enable-PSSessionConfiguration
```

<span data-ttu-id="79003-123">`Enable-PSSessionConfiguration` 如果您啟用已經啟用的會話設定，則不會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="79003-123">`Enable-PSSessionConfiguration` does not generate an error if you enable a session configuration that is already enabled.</span></span>

### <span data-ttu-id="79003-124">範例4：重新啟用會話，並指定新的安全描述項</span><span class="sxs-lookup"><span data-stu-id="79003-124">Example 4: Re-enable a session and specify a new security descriptor</span></span>

<span data-ttu-id="79003-125">此範例會重新啟用 **MaintenanceShell** 會話設定，並為設定指定新的安全描述項。</span><span class="sxs-lookup"><span data-stu-id="79003-125">This example re-enables the **MaintenanceShell** session configuration and specifies a new security descriptor for the configuration.</span></span>

```powershell
$sddl = "O:NSG:BAD:P(A;;GXGWGR;;;BA)(A;;GAGR;;;S-1-5-21-123456789-188441444-3100496)S:P"
Enable-PSSessionConfiguration -Name MaintenanceShell -SecurityDescriptorSDDL $sddl
```

## <span data-ttu-id="79003-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="79003-126">PARAMETERS</span></span>

### <span data-ttu-id="79003-127">-Force</span><span class="sxs-lookup"><span data-stu-id="79003-127">-Force</span></span>

<span data-ttu-id="79003-128">指出 Cmdlet 不會提示您進行確認，並會在不提示的情況下重新啟動 WinRM 服務。</span><span class="sxs-lookup"><span data-stu-id="79003-128">Indicates that the cmdlet does not prompt you for confirmation, and restarts the WinRM service without prompting.</span></span> <span data-ttu-id="79003-129">重新啟動服務可讓設定變更生效。</span><span class="sxs-lookup"><span data-stu-id="79003-129">Restarting the service makes the configuration change effective.</span></span>

<span data-ttu-id="79003-130">若要避免重新啟動並抑制重新啟動提示，請使用 **NoServiceRestart** 參數。</span><span class="sxs-lookup"><span data-stu-id="79003-130">To prevent a restart and suppress the restart prompt, use the **NoServiceRestart** parameter.</span></span>

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

### <span data-ttu-id="79003-131">-Name</span><span class="sxs-lookup"><span data-stu-id="79003-131">-Name</span></span>

<span data-ttu-id="79003-132">指定要啟用之工作階段設定的名稱。</span><span class="sxs-lookup"><span data-stu-id="79003-132">Specifies the names of session configurations to enable.</span></span> <span data-ttu-id="79003-133">輸入一或多個設定名稱。</span><span class="sxs-lookup"><span data-stu-id="79003-133">Enter one or more configuration names.</span></span>
<span data-ttu-id="79003-134">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="79003-134">Wildcard characters are permitted.</span></span>

<span data-ttu-id="79003-135">您也可以使用管線將包含設定名稱的字串或會話設定物件傳送至 `Enable-PSSessionConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="79003-135">You can also pipe a string that contains a configuration name or a session configuration object to `Enable-PSSessionConfiguration`.</span></span>

<span data-ttu-id="79003-136">如果您省略此參數，則會 `Enable-PSSessionConfiguration` 啟用 **Microsoft PowerShell** 會話設定。</span><span class="sxs-lookup"><span data-stu-id="79003-136">If you omit this parameter, `Enable-PSSessionConfiguration` enables the **Microsoft.PowerShell** session configuration.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="79003-137">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="79003-137">-NoServiceRestart</span></span>

<span data-ttu-id="79003-138">指出 Cmdlet 不會重新開機服務。</span><span class="sxs-lookup"><span data-stu-id="79003-138">Indicates that the cmdlet does not restart the service.</span></span>

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

### <span data-ttu-id="79003-139">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="79003-139">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="79003-140">指定此 Cmdlet 用來取代會話設定之安全描述項的安全描述項。</span><span class="sxs-lookup"><span data-stu-id="79003-140">Specifies a security descriptor with which this cmdlet replaces the security descriptor on the session configuration.</span></span>

<span data-ttu-id="79003-141">如果您省略此參數，則 `Enable-PSSessionConfiguration` 只會從安全描述項中刪除 [拒絕所有專案]。</span><span class="sxs-lookup"><span data-stu-id="79003-141">If you omit this parameter, `Enable-PSSessionConfiguration` only deletes the deny all item from the security descriptor.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79003-142">-SkipNetworkProfileCheck</span><span class="sxs-lookup"><span data-stu-id="79003-142">-SkipNetworkProfileCheck</span></span>

<span data-ttu-id="79003-143">指出當電腦位於公用網路時，此 Cmdlet 會啟用會話設定。</span><span class="sxs-lookup"><span data-stu-id="79003-143">Indicates that this cmdlet enables the session configuration when the computer is on a public network.</span></span> <span data-ttu-id="79003-144">此參數會針對公用網路啟用防火牆規則，以便只允許從位於相同本機子網路的電腦進行遠端存取。</span><span class="sxs-lookup"><span data-stu-id="79003-144">This parameter enables a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span> <span data-ttu-id="79003-145">依預設， `Enable-PSSessionConfiguration` 在公用網路上會失敗。</span><span class="sxs-lookup"><span data-stu-id="79003-145">By default, `Enable-PSSessionConfiguration` fails on a public network.</span></span>

<span data-ttu-id="79003-146">此參數是針對用戶端版本的 Windows 作業系統所設計。</span><span class="sxs-lookup"><span data-stu-id="79003-146">This parameter is designed for client versions of the Windows operating system.</span></span> <span data-ttu-id="79003-147">伺服器版本的 Windows 作業系統具有公用網路的本機子網防火牆規則。</span><span class="sxs-lookup"><span data-stu-id="79003-147">Server versions of the Windows operating system have a local subnet firewall rule for public networks.</span></span> <span data-ttu-id="79003-148">但是，如果在伺服器版本的 Windows 作業系統上停用本機子網防火牆規則，此參數便會重新啟用。</span><span class="sxs-lookup"><span data-stu-id="79003-148">However, if the local subnet firewall rule is disabled on a server version of the Windows operating system, this parameter re-enables it.</span></span>

<span data-ttu-id="79003-149">若要移除本機子網限制，並允許從公用網路上的所有位置進行遠端存取，請使用 `Set-NetFirewallRule` NetSecurity 模組中的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="79003-149">To remove the local subnet restriction and enable remote access from all locations on public networks, use the `Set-NetFirewallRule` cmdlet in the NetSecurity module.</span></span> <span data-ttu-id="79003-150">如需詳細資訊，請參閱`Enable-PSRemoting`。</span><span class="sxs-lookup"><span data-stu-id="79003-150">For more information, see `Enable-PSRemoting`.</span></span>

<span data-ttu-id="79003-151">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="79003-151">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="79003-152">-Confirm</span><span class="sxs-lookup"><span data-stu-id="79003-152">-Confirm</span></span>

<span data-ttu-id="79003-153">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="79003-153">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="79003-154">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="79003-154">-WhatIf</span></span>

<span data-ttu-id="79003-155">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="79003-155">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="79003-156">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="79003-156">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="79003-157">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="79003-157">CommonParameters</span></span>

<span data-ttu-id="79003-158">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="79003-158">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="79003-159">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="79003-159">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="79003-160">輸入</span><span class="sxs-lookup"><span data-stu-id="79003-160">INPUTS</span></span>

### <span data-ttu-id="79003-161">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration、System.String</span><span class="sxs-lookup"><span data-stu-id="79003-161">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration, System.String</span></span>

<span data-ttu-id="79003-162">您可以使用管線將工作階段設定物件或包含工作階段設定名稱的字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="79003-162">You can pipe a session configuration object or a string that contains the name of a session configuration to this cmdlet.</span></span>

## <span data-ttu-id="79003-163">輸出</span><span class="sxs-lookup"><span data-stu-id="79003-163">OUTPUTS</span></span>

### <span data-ttu-id="79003-164">None</span><span class="sxs-lookup"><span data-stu-id="79003-164">None</span></span>

<span data-ttu-id="79003-165">此 Cmdlet 不會傳回任何物件。</span><span class="sxs-lookup"><span data-stu-id="79003-165">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="79003-166">注意</span><span class="sxs-lookup"><span data-stu-id="79003-166">NOTES</span></span>

<span data-ttu-id="79003-167">此 Cmdlet 僅適用于 Windows 平臺。</span><span class="sxs-lookup"><span data-stu-id="79003-167">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="79003-168">若要使用此 Cmdlet，您必須使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="79003-168">To use this cmdlet, you must start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="79003-169">相關連結</span><span class="sxs-lookup"><span data-stu-id="79003-169">RELATED LINKS</span></span>

[<span data-ttu-id="79003-170">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="79003-170">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="79003-171">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="79003-171">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="79003-172">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="79003-172">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="79003-173">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="79003-173">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="79003-174">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="79003-174">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="79003-175">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="79003-175">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="79003-176">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="79003-176">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="79003-177">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="79003-177">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="79003-178">WSMan 提供者</span><span class="sxs-lookup"><span data-stu-id="79003-178">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="79003-179">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="79003-179">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="79003-180">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="79003-180">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
