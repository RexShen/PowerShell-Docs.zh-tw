---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/unregister-pssessionconfiguration?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PSSessionConfiguration
ms.openlocfilehash: d56d71dccc54c07154a6f3302634b84779c00129
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205667"
---
# <span data-ttu-id="8db89-103">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="8db89-103">Unregister-PSSessionConfiguration</span></span>

## <span data-ttu-id="8db89-104">概要</span><span class="sxs-lookup"><span data-stu-id="8db89-104">SYNOPSIS</span></span>
<span data-ttu-id="8db89-105">從電腦刪除已註冊的工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="8db89-105">Deletes registered session configurations from the computer.</span></span>

## <span data-ttu-id="8db89-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8db89-106">SYNTAX</span></span>

```
Unregister-PSSessionConfiguration [-Name] <String> [-Force] [-NoServiceRestart] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="8db89-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8db89-107">DESCRIPTION</span></span>

<span data-ttu-id="8db89-108">`Unregister-PSSessionConfiguration`Cmdlet 會從電腦刪除已註冊的會話設定。</span><span class="sxs-lookup"><span data-stu-id="8db89-108">The `Unregister-PSSessionConfiguration` cmdlet deletes registered session configurations from the computer.</span></span> <span data-ttu-id="8db89-109">此 Cmdlet 是專為系統管理員管理使用者的自訂會話設定而設計的。</span><span class="sxs-lookup"><span data-stu-id="8db89-109">This cmdlet is designed for system administrators to manage customized session configurations for users.</span></span>

<span data-ttu-id="8db89-110">若要讓變更生效，請 `Unregister-PSSessionConfiguration` 重新開機 **WinRM** 服務。</span><span class="sxs-lookup"><span data-stu-id="8db89-110">To make the change effective, `Unregister-PSSessionConfiguration` restarts the **WinRM** service.</span></span> <span data-ttu-id="8db89-111">若要防止重新啟動，請指定 **NoServiceRestart** 參數。</span><span class="sxs-lookup"><span data-stu-id="8db89-111">To prevent the restart, specify the **NoServiceRestart** parameter.</span></span>

<span data-ttu-id="8db89-112">如果您不小心 **刪除預設的** **microsoft.powershell32** 會話設定，請使用 `Enable-PSRemoting` Cmdlet 來還原它們。</span><span class="sxs-lookup"><span data-stu-id="8db89-112">If you accidentally delete the default **Microsoft.PowerShell** or **Microsoft.PowerShell32** session configurations, use the `Enable-PSRemoting` cmdlet to restore them.</span></span> <span data-ttu-id="8db89-113">如需詳細資訊，請參閱 [about_Session_Configurations](About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="8db89-113">For more information, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

## <span data-ttu-id="8db89-114">範例</span><span class="sxs-lookup"><span data-stu-id="8db89-114">EXAMPLES</span></span>

### <span data-ttu-id="8db89-115">範例 1：刪除工作階段設定</span><span class="sxs-lookup"><span data-stu-id="8db89-115">Example 1: Delete a session configuration</span></span>

<span data-ttu-id="8db89-116">此範例會從電腦刪除 **MaintenanceShell** 會話設定。</span><span class="sxs-lookup"><span data-stu-id="8db89-116">This example deletes the **MaintenanceShell** session configuration from the computer.</span></span>

```powershell
Unregister-PSSessionConfiguration -Name "MaintenanceShell"
```

### <span data-ttu-id="8db89-117">範例 2︰刪除工作階段設定，並重新啟動 WinRM 服務</span><span class="sxs-lookup"><span data-stu-id="8db89-117">Example 2: Delete a session configuration and restart the WinRM service</span></span>

<span data-ttu-id="8db89-118">在此範例中，我們會刪除 **MaintenanceShell** 設定，並重新啟動 WinRM 服務。</span><span class="sxs-lookup"><span data-stu-id="8db89-118">In this example, we delete the **MaintenanceShell** configuration and restart the WinRM service.</span></span> <span data-ttu-id="8db89-119">**Force** 參數會抑制所有使用者訊息，以重新開機 **WinRM** 服務而不提示。</span><span class="sxs-lookup"><span data-stu-id="8db89-119">The **Force** parameter suppresses all user messages to restart the **WinRM** service without prompting.</span></span>

```powershell
Unregister-PSSessionConfiguration -Name MaintenanceShell -Force
```

### <span data-ttu-id="8db89-120">範例 3：刪除所有工作階段設定</span><span class="sxs-lookup"><span data-stu-id="8db89-120">Example 3: Delete all session configurations</span></span>

<span data-ttu-id="8db89-121">此範例顯示兩種刪除電腦上所有會話設定的方式。</span><span class="sxs-lookup"><span data-stu-id="8db89-121">This examples show two ways to delete all the session configurations on the computer.</span></span> <span data-ttu-id="8db89-122">這兩個命令都有相同的效果，而且可以交換使用。</span><span class="sxs-lookup"><span data-stu-id="8db89-122">Both commands have the same effect and can be used interchangeably.</span></span>

```
Unregister-PSSessionConfiguration -Name *
Get-PSSessionConfiguration -Name * | Unregister-PSSessionConfiguration
```

### <span data-ttu-id="8db89-123">範例 4︰取消註冊而不重新啟動</span><span class="sxs-lookup"><span data-stu-id="8db89-123">Example 4: Unregister without a restart</span></span>

<span data-ttu-id="8db89-124">此範例顯示使用 **NoServiceRestart** 參數來防止服務重新開機，而導致電腦上的任何會話中斷的效果。</span><span class="sxs-lookup"><span data-stu-id="8db89-124">This example shows the effect of using the **NoServiceRestart** parameter to prevent a service restart that would disrupt any sessions on the computer.</span></span>

```
PS> Unregister-PSSessionConfiguration -Name "MaintenanceShell" -NoServiceRestart
PS> Get-PSSessionConfiguration -Name "MaintenanceShell"

Get-PSSessionConfiguration -Name MaintenanceShell : No Session Configuration matches criteria "MaintenanceShell".
+ CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
+ FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException

PS> New-PSSession -ConfigurationName "MaintenanceShell"

Id Name      ComputerName    State    Configuration         Availability
-- ----      ------------    -----    -------------         ------------
1 Session1  localhost       Opened   MaintenanceShell      Available

PS> Restart-Service winrm
PS> New-PSSession -ConfigurationName MaintenanceShell

[localhost] Connecting to remote server failed with the following error message :
 The WS-Management service cannot process the request.
 The resource URI (http://schemas.microsoft.com/powershell/MaintenanceShell) was not found in the WS-Management catalog.
 The catalog contains the metadata that describes resources, or logical endpoints.
 For more information, see the about_Remote_Troubleshooting Help topic.
 + CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [], PSRemotingTransportException
 + FullyQualifiedErrorId : PSSessionOpenFailed
```

<span data-ttu-id="8db89-125">會 `Unregister-PSSessionConfiguration` 刪除 **MaintenanceShell** 會話設定。</span><span class="sxs-lookup"><span data-stu-id="8db89-125">The `Unregister-PSSessionConfiguration` deletes the **MaintenanceShell** session configuration.</span></span>
<span data-ttu-id="8db89-126">不過，因為命令使用 **NoServiceRestart** 參數，所以 **WinRM** 服務不會重新啟動，而變更尚未完全生效。</span><span class="sxs-lookup"><span data-stu-id="8db89-126">However, because the command uses the **NoServiceRestart** parameter, the **WinRM** service is not restarted and the change is not yet completely effective.</span></span>

<span data-ttu-id="8db89-127">接下來， `Get-PSSessionConfiguration` 嘗試取得 **MaintenanceShell** 會話。</span><span class="sxs-lookup"><span data-stu-id="8db89-127">Next, the `Get-PSSessionConfiguration` tries to get the **MaintenanceShell** session.</span></span> <span data-ttu-id="8db89-128">因為會話已經從 WS-Management 資源資料表中移除，所以 `Get-PSSessionConfiguration` 無法將它傳回。</span><span class="sxs-lookup"><span data-stu-id="8db89-128">Because the session has been removed from the WS-Management resource table, `Get-PSSessionConfiguration` cannot return it.</span></span>

<span data-ttu-id="8db89-129">此 `New-PSSession` Cmdlet 會使用 **MaintenanceShell** 設定來建立會話。</span><span class="sxs-lookup"><span data-stu-id="8db89-129">The `New-PSSession` cmdlet creates a session using the **MaintenanceShell** configuration.</span></span> <span data-ttu-id="8db89-130">命令執行成功。</span><span class="sxs-lookup"><span data-stu-id="8db89-130">The command succeeds.</span></span> <span data-ttu-id="8db89-131">接下來，我們會重新開機 **WinRM** 服務。</span><span class="sxs-lookup"><span data-stu-id="8db89-131">Next, we restart the **WinRM** service.</span></span>

<span data-ttu-id="8db89-132">最後， `New-PSSession` Cmdlet 會嘗試建立使用 **MaintenanceShell** 設定的會話。</span><span class="sxs-lookup"><span data-stu-id="8db89-132">Finally, the `New-PSSession` cmdlet tries to create a session that uses the **MaintenanceShell** configuration.</span></span> <span data-ttu-id="8db89-133">這次，會話失敗，因為 WinRM 服務重新開機時已刪除 **MaintenanceShell** 設定。</span><span class="sxs-lookup"><span data-stu-id="8db89-133">This time, the session fails because the **MaintenanceShell** configuration was deleted when the WinRM service restarted.</span></span>

## <span data-ttu-id="8db89-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8db89-134">PARAMETERS</span></span>

### <span data-ttu-id="8db89-135">-Force</span><span class="sxs-lookup"><span data-stu-id="8db89-135">-Force</span></span>

<span data-ttu-id="8db89-136">指出 Cmdlet 不會提示您進行確認，並會在不提示的情況下重新啟動 **WinRM** 服務。</span><span class="sxs-lookup"><span data-stu-id="8db89-136">Indicates that the cmdlet does not prompt you for confirmation, and restarts the **WinRM** service without prompting.</span></span> <span data-ttu-id="8db89-137">重新啟動服務可讓設定變更生效。</span><span class="sxs-lookup"><span data-stu-id="8db89-137">Restarting the service makes the configuration change effective.</span></span>

<span data-ttu-id="8db89-138">若要避免重新啟動並抑制重新啟動提示，請使用 **NoServiceRestart** 參數。</span><span class="sxs-lookup"><span data-stu-id="8db89-138">To prevent a restart and suppress the restart prompt, use the **NoServiceRestart** parameter.</span></span>

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

### <span data-ttu-id="8db89-139">-Name</span><span class="sxs-lookup"><span data-stu-id="8db89-139">-Name</span></span>

<span data-ttu-id="8db89-140">指定要刪除的工作階段設定名稱。</span><span class="sxs-lookup"><span data-stu-id="8db89-140">Specifies the names of the session configurations to delete.</span></span> <span data-ttu-id="8db89-141">輸入一個工作階段設定名稱或設定名稱模式。</span><span class="sxs-lookup"><span data-stu-id="8db89-141">Enter one session configuration name or a configuration name pattern.</span></span> <span data-ttu-id="8db89-142">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="8db89-142">Wildcard characters are permitted.</span></span> <span data-ttu-id="8db89-143">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="8db89-143">This parameter is required.</span></span>

<span data-ttu-id="8db89-144">您也可以使用管線將會話設定傳送至 `Unregister-PSSessionConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="8db89-144">You can also pipe a session configurations to `Unregister-PSSessionConfiguration`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="8db89-145">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="8db89-145">-NoServiceRestart</span></span>

<span data-ttu-id="8db89-146">指出此 Cmdlet 不會重新啟動 **WinRM** 服務，且會抑制重新啟動服務的提示。</span><span class="sxs-lookup"><span data-stu-id="8db89-146">Indicates that this cmdlet does not restart the **WinRM** service, and suppresses the prompt to restart the service.</span></span>

<span data-ttu-id="8db89-147">依預設，當您執行 `Unregister-PSSessionConfiguration` 命令時，系統會提示您重新開機 **WinRM** 服務，讓變更生效。</span><span class="sxs-lookup"><span data-stu-id="8db89-147">By default, when you run an `Unregister-PSSessionConfiguration` command, you are prompted to restart the **WinRM** service to make the change effective.</span></span> <span data-ttu-id="8db89-148">在 **WinRM** 服務重新開機之前，使用者仍然可以使用未註冊的會話設定，即使找 `Get-PSSessionConfiguration` 不到它也一樣。</span><span class="sxs-lookup"><span data-stu-id="8db89-148">Until the **WinRM** service is restarted, users can still use the unregistered session configuration, even though `Get-PSSessionConfiguration` does not find it.</span></span>

<span data-ttu-id="8db89-149">若要重新啟動 **WinRM** 服務而不提示，請指定 **Force** 參數。</span><span class="sxs-lookup"><span data-stu-id="8db89-149">To restart the **WinRM** service without prompting, specify the **Force** parameter.</span></span> <span data-ttu-id="8db89-150">若要手動重新開機 **WinRM** 服務，請使用 `Restart-Service` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8db89-150">To restart the **WinRM** service manually, use the `Restart-Service` cmdlet.</span></span>

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

### <span data-ttu-id="8db89-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="8db89-151">-Confirm</span></span>

<span data-ttu-id="8db89-152">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="8db89-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="8db89-153">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="8db89-153">-WhatIf</span></span>

<span data-ttu-id="8db89-154">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="8db89-154">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="8db89-155">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="8db89-155">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="8db89-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8db89-156">CommonParameters</span></span>

<span data-ttu-id="8db89-157">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="8db89-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8db89-158">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="8db89-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8db89-159">輸入</span><span class="sxs-lookup"><span data-stu-id="8db89-159">INPUTS</span></span>

### <span data-ttu-id="8db89-160">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="8db89-160">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration</span></span>

<span data-ttu-id="8db89-161">您可以使用管線將會話設定物件傳送 `Get-PSSessionConfiguration` 至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8db89-161">You can pipe a session configuration object from `Get-PSSessionConfiguration` to this cmdlet.</span></span>

## <span data-ttu-id="8db89-162">輸出</span><span class="sxs-lookup"><span data-stu-id="8db89-162">OUTPUTS</span></span>

### <span data-ttu-id="8db89-163">無</span><span class="sxs-lookup"><span data-stu-id="8db89-163">None</span></span>

<span data-ttu-id="8db89-164">此 Cmdlet 不會傳回任何物件。</span><span class="sxs-lookup"><span data-stu-id="8db89-164">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="8db89-165">注意</span><span class="sxs-lookup"><span data-stu-id="8db89-165">NOTES</span></span>

<span data-ttu-id="8db89-166">若要執行此 Cmdlet，您必須使用 [ **以系統管理員身分執行** ] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="8db89-166">To run this cmdlet you must start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="8db89-167">相關連結</span><span class="sxs-lookup"><span data-stu-id="8db89-167">RELATED LINKS</span></span>

[<span data-ttu-id="8db89-168">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="8db89-168">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="8db89-169">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="8db89-169">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="8db89-170">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="8db89-170">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="8db89-171">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="8db89-171">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="8db89-172">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="8db89-172">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="8db89-173">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="8db89-173">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="8db89-174">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="8db89-174">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="8db89-175">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="8db89-175">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="8db89-176">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="8db89-176">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="8db89-177">WSMan 提供者</span><span class="sxs-lookup"><span data-stu-id="8db89-177">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="8db89-178">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="8db89-178">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="8db89-179">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="8db89-179">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)

