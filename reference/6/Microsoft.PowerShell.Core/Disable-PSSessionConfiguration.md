---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-pssessionconfiguration?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSSessionConfiguration
ms.openlocfilehash: 4e551c42c0ae6e447906c5541fb100ef0ef82681
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203816"
---
# <span data-ttu-id="5bd4a-103">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="5bd4a-103">Disable-PSSessionConfiguration</span></span>

## <span data-ttu-id="5bd4a-104">概要</span><span class="sxs-lookup"><span data-stu-id="5bd4a-104">SYNOPSIS</span></span>
<span data-ttu-id="5bd4a-105">停用本機電腦上的工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="5bd4a-105">Disables session configurations on the local computer.</span></span>

## <span data-ttu-id="5bd4a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5bd4a-106">SYNTAX</span></span>

```
Disable-PSSessionConfiguration [[-Name] <String[]>] [-Force] [-NoServiceRestart] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="5bd4a-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5bd4a-107">DESCRIPTION</span></span>

<span data-ttu-id="5bd4a-108">此 `Disable-PSSessionConfiguration` Cmdlet 會停用本機電腦上的會話設定，以防止所有使用者使用會話設定，在本機電腦上 ( **pssession** ) 建立使用者管理的會話。</span><span class="sxs-lookup"><span data-stu-id="5bd4a-108">The `Disable-PSSessionConfiguration` cmdlet disables session configurations on the local computer, which prevents all users from using the session configurations to create a user-managed sessions ( **PSSessions** ) on the local computer.</span></span> <span data-ttu-id="5bd4a-109">這是一個進階的 Cmdlet，專門設計給系統管理員用於管理其使用者的自訂工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="5bd4a-109">This is an advanced cmdlet that is designed to be used by system administrators to manage customized session configurations for their users.</span></span>

<span data-ttu-id="5bd4a-110">從 PowerShell 3.0 開始，此 `Disable-PSSessionConfiguration` Cmdlet 會將會話設定的 **啟用** 設定 (`WSMan:\localhost\Plugins\<SessionConfiguration>\Enabled`) 設定為 False。</span><span class="sxs-lookup"><span data-stu-id="5bd4a-110">Starting in PowerShell 3.0, the `Disable-PSSessionConfiguration` cmdlet sets the **Enabled** setting of the session configuration (`WSMan:\localhost\Plugins\<SessionConfiguration>\Enabled`) to False.</span></span>

<span data-ttu-id="5bd4a-111">在 PowerShell 2.0 中，此 `Disable-PSSessionConfiguration` Cmdlet 會將 **Deny_All** 專案新增至一或多個已註冊之會話設定的安全描述項。</span><span class="sxs-lookup"><span data-stu-id="5bd4a-111">In PowerShell 2.0, the `Disable-PSSessionConfiguration` cmdlet adds a **Deny_All** entry to the security descriptor of one or more registered session configurations.</span></span>

<span data-ttu-id="5bd4a-112">如果沒有參數，則會 `Disable-PSSessionConfiguration` 停用 **Microsoft PowerShell** 設定，這是用於會話的預設設定。</span><span class="sxs-lookup"><span data-stu-id="5bd4a-112">Without parameters, `Disable-PSSessionConfiguration` disables the **Microsoft.PowerShell** configuration, the default configuration used for sessions.</span></span> <span data-ttu-id="5bd4a-113">除非使用者指定不同的設定，否則本機和遠端使用者都無法建立任何連線到電腦的工作階段。</span><span class="sxs-lookup"><span data-stu-id="5bd4a-113">Unless the user specifies a different configuration, both local and remote users are effectively prevented from creating any sessions that connect to the computer.</span></span>

<span data-ttu-id="5bd4a-114">若要停用電腦上的所有會話設定，請使用 `Disable-PSRemoting` 。</span><span class="sxs-lookup"><span data-stu-id="5bd4a-114">To disable all session configurations on the computer, use `Disable-PSRemoting`.</span></span>

## <span data-ttu-id="5bd4a-115">範例</span><span class="sxs-lookup"><span data-stu-id="5bd4a-115">EXAMPLES</span></span>

### <span data-ttu-id="5bd4a-116">範例 1：停用預設設定</span><span class="sxs-lookup"><span data-stu-id="5bd4a-116">Example 1: Disable the default configuration</span></span>

<span data-ttu-id="5bd4a-117">此範例會停用 Microsoft PowerShell 會話設定。</span><span class="sxs-lookup"><span data-stu-id="5bd4a-117">This example disables the Microsoft.PowerShell session configuration.</span></span>

```powershell
Disable-PSSessionConfiguration
```

### <span data-ttu-id="5bd4a-118">範例 2︰停用所有已註冊的工作階段設定</span><span class="sxs-lookup"><span data-stu-id="5bd4a-118">Example 2: Disable all registered session configurations</span></span>

<span data-ttu-id="5bd4a-119">此範例會停用電腦上所有已註冊的會話設定。</span><span class="sxs-lookup"><span data-stu-id="5bd4a-119">This example disables all registered session configurations on the computer.</span></span>

```powershell
Disable-PSSessionConfiguration -Name *
```

### <span data-ttu-id="5bd4a-120">範例 3︰依名稱停用工作階段設定</span><span class="sxs-lookup"><span data-stu-id="5bd4a-120">Example 3: Disable session configurations by name</span></span>

<span data-ttu-id="5bd4a-121">此範例會停用所有名稱開頭為 Microsoft 的會話設定。</span><span class="sxs-lookup"><span data-stu-id="5bd4a-121">This example disables all session configurations that have names that begin with Microsoft.</span></span> <span data-ttu-id="5bd4a-122">**Force** 參數會抑制 Cmdlet 中的所有使用者提示。</span><span class="sxs-lookup"><span data-stu-id="5bd4a-122">The **Force** parameter suppresses all user prompts from the cmdlet.</span></span>

```powershell
Disable-PSSessionConfiguration -Name Microsoft* -Force
```

### <span data-ttu-id="5bd4a-123">範例 4︰使用管線停用工作階段設定</span><span class="sxs-lookup"><span data-stu-id="5bd4a-123">Example 4: Disable session configurations by using the pipeline</span></span>

<span data-ttu-id="5bd4a-124">此範例會停用 **MaintenanceShell** 和 **AdminShell** 會話設定。</span><span class="sxs-lookup"><span data-stu-id="5bd4a-124">This example disables the **MaintenanceShell** and **AdminShell** session configurations.</span></span> <span data-ttu-id="5bd4a-125">管線運算子 (|) 將的結果傳送 `Get-PSSessionConfiguration` 至 `Disable-PSSessionConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="5bd4a-125">The pipeline operator (|) sends the results of a `Get-PSSessionConfiguration` to `Disable-PSSessionConfiguration`.</span></span>

```powershell
Get-PSSessionConfiguration -Name MaintenanceShell, AdminShell | Disable-PSSessionConfiguration
```

### <span data-ttu-id="5bd4a-126">範例 5︰停用工作階段設定的效果</span><span class="sxs-lookup"><span data-stu-id="5bd4a-126">Example 5: Effects of disabling a session configuration</span></span>

<span data-ttu-id="5bd4a-127">此範例顯示執行之前和之後的許可權 `Disable-PSSessionConfiguration` ，以及停用會話設定的影響。</span><span class="sxs-lookup"><span data-stu-id="5bd4a-127">This example shows the permissions before and after running `Disable-PSSessionConfiguration` and the effect of disabling a session configuration.</span></span>

```
PS> Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Name                   Permission
----                   ----------
MaintenanceShell       BUILTIN\Administrators AccessAllowed
microsoft.powershell   BUILTIN\Administrators AccessAllowed
microsoft.powershell32 BUILTIN\Administrators AccessAllowed

PS> Disable-PSSessionConfiguration -Name MaintenanceShell -Force
PS> Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Name                   Permission
----                   ----------
MaintenanceShell       Everyone AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell   BUILTIN\Administrators AccessAllowed
microsoft.powershell32 BUILTIN\Administrators AccessAllowed

PS> New-PSSession -ComputerName localhost -ConfigurationName MaintenanceShell

[localhost] Connecting to remote server failed with the following error message : Access is denied.
For more information, see the about_Remote_Troubleshooting Help topic.
+ CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [], PSRemotingTransportException
+ FullyQualifiedErrorId : PSSessionOpenFailed
```

> [!NOTE]
> <span data-ttu-id="5bd4a-128">停用此設定並不會讓您無法使用 Cmdlet 來變更設定 `Set-PSSessionConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="5bd4a-128">Disabling the configuration does not prevent you from changing the configuration using the `Set-PSSessionConfiguration` cmdlet.</span></span> <span data-ttu-id="5bd4a-129">它只會防止使用設定。</span><span class="sxs-lookup"><span data-stu-id="5bd4a-129">It only prevents use of the configuration.</span></span>

## <span data-ttu-id="5bd4a-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5bd4a-130">PARAMETERS</span></span>

### <span data-ttu-id="5bd4a-131">-Force</span><span class="sxs-lookup"><span data-stu-id="5bd4a-131">-Force</span></span>

<span data-ttu-id="5bd4a-132">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="5bd4a-132">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="5bd4a-133">-Name</span><span class="sxs-lookup"><span data-stu-id="5bd4a-133">-Name</span></span>

<span data-ttu-id="5bd4a-134">指定要停用之工作階段設定名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="5bd4a-134">Specifies an array of names of session configurations to disable.</span></span> <span data-ttu-id="5bd4a-135">輸入一或多個設定名稱。</span><span class="sxs-lookup"><span data-stu-id="5bd4a-135">Enter one or more configuration names.</span></span> <span data-ttu-id="5bd4a-136">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="5bd4a-136">Wildcard characters are permitted.</span></span> <span data-ttu-id="5bd4a-137">您也可以使用管線將包含設定名稱的字串或會話設定物件傳送至 `Disable-PSSessionConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="5bd4a-137">You can also pipe a string that contains a configuration name or a session configuration object to `Disable-PSSessionConfiguration`.</span></span>

<span data-ttu-id="5bd4a-138">如果您省略此參數，則會 `Disable-PSSessionConfiguration` 停用 Microsoft PowerShell 會話設定。</span><span class="sxs-lookup"><span data-stu-id="5bd4a-138">If you omit this parameter, `Disable-PSSessionConfiguration` disables the Microsoft.PowerShell session configuration.</span></span>

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

### <span data-ttu-id="5bd4a-139">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="5bd4a-139">-NoServiceRestart</span></span>

<span data-ttu-id="5bd4a-140">用來防止重新開機 WSMan 服務。</span><span class="sxs-lookup"><span data-stu-id="5bd4a-140">Used to prevent the restart of the WSMan service.</span></span> <span data-ttu-id="5bd4a-141">不需要重新開機服務來停用設定。</span><span class="sxs-lookup"><span data-stu-id="5bd4a-141">It is not necessary to restart the service to disable the configuration.</span></span>

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

### <span data-ttu-id="5bd4a-142">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5bd4a-142">-Confirm</span></span>

<span data-ttu-id="5bd4a-143">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="5bd4a-143">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5bd4a-144">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5bd4a-144">-WhatIf</span></span>

<span data-ttu-id="5bd4a-145">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="5bd4a-145">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="5bd4a-146">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="5bd4a-146">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5bd4a-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5bd4a-147">CommonParameters</span></span>

<span data-ttu-id="5bd4a-148">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="5bd4a-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5bd4a-149">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="5bd4a-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5bd4a-150">輸入</span><span class="sxs-lookup"><span data-stu-id="5bd4a-150">INPUTS</span></span>

### <span data-ttu-id="5bd4a-151">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration、System.String</span><span class="sxs-lookup"><span data-stu-id="5bd4a-151">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration, System.String</span></span>

<span data-ttu-id="5bd4a-152">您可以使用管線將工作階段設定物件或包含工作階段設定名稱的字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5bd4a-152">You can pipe a session configuration object or a string that contains the name of a session configuration to this cmdlet.</span></span>

## <span data-ttu-id="5bd4a-153">輸出</span><span class="sxs-lookup"><span data-stu-id="5bd4a-153">OUTPUTS</span></span>

### <span data-ttu-id="5bd4a-154">無</span><span class="sxs-lookup"><span data-stu-id="5bd4a-154">None</span></span>

<span data-ttu-id="5bd4a-155">此 Cmdlet 不會傳回任何物件。</span><span class="sxs-lookup"><span data-stu-id="5bd4a-155">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="5bd4a-156">注意</span><span class="sxs-lookup"><span data-stu-id="5bd4a-156">NOTES</span></span>

<span data-ttu-id="5bd4a-157">若要執行此 Cmdlet，您必須使用 [ **以系統管理員身分執行** ] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="5bd4a-157">To run this cmdlet you must start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="5bd4a-158">相關連結</span><span class="sxs-lookup"><span data-stu-id="5bd4a-158">RELATED LINKS</span></span>

[<span data-ttu-id="5bd4a-159">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="5bd4a-159">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="5bd4a-160">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="5bd4a-160">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="5bd4a-161">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="5bd4a-161">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="5bd4a-162">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="5bd4a-162">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="5bd4a-163">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="5bd4a-163">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="5bd4a-164">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="5bd4a-164">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="5bd4a-165">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="5bd4a-165">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="5bd4a-166">WSMan 提供者</span><span class="sxs-lookup"><span data-stu-id="5bd4a-166">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="5bd4a-167">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="5bd4a-167">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="5bd4a-168">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="5bd4a-168">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
