---
external help file: Stop-DscConfiguration.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 08/19/2019
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/stop-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-DscConfiguration
ms.openlocfilehash: 93c8585ae948dfa360a2ae8e2563670de8fd6e93
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203087"
---
# <span data-ttu-id="1966b-103">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="1966b-103">Stop-DscConfiguration</span></span>

## <span data-ttu-id="1966b-104">概要</span><span class="sxs-lookup"><span data-stu-id="1966b-104">SYNOPSIS</span></span>
<span data-ttu-id="1966b-105">停止正在執行的設定工作。</span><span class="sxs-lookup"><span data-stu-id="1966b-105">Stops a configuration job that is running.</span></span>

## <span data-ttu-id="1966b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1966b-106">SYNTAX</span></span>

### <span data-ttu-id="1966b-107">全部</span><span class="sxs-lookup"><span data-stu-id="1966b-107">All</span></span>

```
Stop-DscConfiguration [-Force] [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="1966b-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="1966b-108">DESCRIPTION</span></span>

<span data-ttu-id="1966b-109">此 `Stop-DscConfiguration` Cmdlet 會停止執行中的設定工作。</span><span class="sxs-lookup"><span data-stu-id="1966b-109">The `Stop-DscConfiguration` cmdlet stops a configuration job that is running.</span></span> <span data-ttu-id="1966b-110">使用通用訊息模型 (CIM) 工作階段，來指定要將此 Cmdlet 套用至哪些電腦。</span><span class="sxs-lookup"><span data-stu-id="1966b-110">Specify which computers this cmdlet applies to by using Common Information Model (CIM) sessions.</span></span> <span data-ttu-id="1966b-111">如果沒有執行中的設定作業，此 Cmdlet 會傳回一則警告訊息。</span><span class="sxs-lookup"><span data-stu-id="1966b-111">If there's no configuration job running, this cmdlet returns a warning message.</span></span>

<span data-ttu-id="1966b-112">`Stop-DscConfiguration` 僅適用于2014年11月更新彙總套件的一部分，可從 Microsoft 支援服務程式庫 [Windows RT 8.1、Windows 8.1 和 Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) 。</span><span class="sxs-lookup"><span data-stu-id="1966b-112">`Stop-DscConfiguration` is only available as part of the [November 2014 update rollup for Windows RT 8.1, Windows 8.1, and Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) from the Microsoft Support library.</span></span> <span data-ttu-id="1966b-113">使用這個 Cmdlet 之前，請先複習[Windows PowerShell 5.0 的新功能](/powershell/scripting/whats-new/What-s-New-in-Windows-PowerShell-50)中的資訊。</span><span class="sxs-lookup"><span data-stu-id="1966b-113">Before you use this cmdlet, review the information in [What's New in Windows PowerShell 5.0](/powershell/scripting/whats-new/What-s-New-in-Windows-PowerShell-50)</span></span>

## <span data-ttu-id="1966b-114">範例</span><span class="sxs-lookup"><span data-stu-id="1966b-114">EXAMPLES</span></span>

### <span data-ttu-id="1966b-115">範例 1︰停止設定工作</span><span class="sxs-lookup"><span data-stu-id="1966b-115">Example 1: Stop a configuration job</span></span>

<span data-ttu-id="1966b-116">在此範例中，會使用 Cmdlet 建立 CIM 會話 `New-CimSession` 。</span><span class="sxs-lookup"><span data-stu-id="1966b-116">In this example, a CIM session is created using the `New-CimSession` cmdlet.</span></span> <span data-ttu-id="1966b-117">**CimSession** 物件是用來停止執行中的設定工作。</span><span class="sxs-lookup"><span data-stu-id="1966b-117">The **CimSession** object is used to stop a running configuration job.</span></span>

```powershell
$Session = New-CimSession -ComputerName Server01 -Credential ACCOUNTS\User01
Stop-DscConfiguration -CimSession $Session
```

<span data-ttu-id="1966b-118">`New-CimSession` 使用 **ComputerName** 參數來指定 Server01 電腦。</span><span class="sxs-lookup"><span data-stu-id="1966b-118">`New-CimSession` uses the **ComputerName** parameter to specify the Server01 computer.</span></span> <span data-ttu-id="1966b-119">**Credential** 參數會指定使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="1966b-119">The **Credential** parameter specifies the user account.</span></span> <span data-ttu-id="1966b-120">**CimSession** 物件儲存在 `$Session` 變數中。</span><span class="sxs-lookup"><span data-stu-id="1966b-120">The **CimSession** object is stored in the `$Session` variable.</span></span> <span data-ttu-id="1966b-121">當命令執行時，系統會提示您輸入使用者帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="1966b-121">When the command is run, you're prompted for the user account's password.</span></span>

<span data-ttu-id="1966b-122">`Stop-DscConfiguration` 使用 **CimSession** 參數和儲存在中的物件 `$Session` 來停止設定工作。</span><span class="sxs-lookup"><span data-stu-id="1966b-122">`Stop-DscConfiguration` uses the **CimSession** parameter and the object stored in `$Session` to stop the configuration job.</span></span>

## <span data-ttu-id="1966b-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1966b-123">PARAMETERS</span></span>

### <span data-ttu-id="1966b-124">-AsJob</span><span class="sxs-lookup"><span data-stu-id="1966b-124">-AsJob</span></span>

<span data-ttu-id="1966b-125">指出此 Cmdlet 會以背景工作方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="1966b-125">Indicates that this cmdlet runs the command as a background job.</span></span> <span data-ttu-id="1966b-126">如需 PowerShell 背景工作的詳細資訊，請參閱 [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) 和 [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="1966b-126">For more information about PowerShell background jobs, see [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) and [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).</span></span>

<span data-ttu-id="1966b-127">若要使用 **AsJob** 參數，必須設定本機和遠端電腦以進行遠端處理。</span><span class="sxs-lookup"><span data-stu-id="1966b-127">To use the **AsJob** parameter, the local and remote computers must be configured for remoting.</span></span> <span data-ttu-id="1966b-128">在 Windows Vista 和更新版本的 Windows 作業系統上，您必須使用 [以 **系統管理員身分執行** ] 選項開啟 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="1966b-128">On Windows Vista and later versions of the Windows operating system, you must open PowerShell with the **Run as administrator** option.</span></span> <span data-ttu-id="1966b-129">如需詳細資訊，請參閱[about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1966b-129">For more information, see [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span></span>

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

### <span data-ttu-id="1966b-130">-CimSession</span><span class="sxs-lookup"><span data-stu-id="1966b-130">-CimSession</span></span>

<span data-ttu-id="1966b-131">在遠端工作階段或遠端電腦上執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1966b-131">Runs the cmdlet in a remote session or on a remote computer.</span></span> <span data-ttu-id="1966b-132">輸入電腦名稱稱或會話物件，例如或的輸出 `New-CimSession` `Get-CimSession` 。</span><span class="sxs-lookup"><span data-stu-id="1966b-132">Enter a computer name or a session object, such as the output from `New-CimSession` or `Get-CimSession`.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: (All)
Aliases: Session

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1966b-133">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1966b-133">-Confirm</span></span>

<span data-ttu-id="1966b-134">`Stop-DscConfiguration` 不支援 **Confirm** 參數。</span><span class="sxs-lookup"><span data-stu-id="1966b-134">`Stop-DscConfiguration` doesn't support the **Confirm** parameter.</span></span> <span data-ttu-id="1966b-135">如果使用 **Confirm** 參數，則會顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="1966b-135">If the **Confirm** parameter is used, an error is displayed.</span></span>

<span data-ttu-id="1966b-136">針對支援 **確認** 的 PowerShell Cmdlet，使用參數會在執行命令之前提示您進行驗證。</span><span class="sxs-lookup"><span data-stu-id="1966b-136">For PowerShell cmdlets that support **Confirm** , using the parameter prompts you for verification before a command is run.</span></span>

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

### <span data-ttu-id="1966b-137">-Force</span><span class="sxs-lookup"><span data-stu-id="1966b-137">-Force</span></span>

<span data-ttu-id="1966b-138">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="1966b-138">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="1966b-139">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="1966b-139">-ThrottleLimit</span></span>

<span data-ttu-id="1966b-140">指定為執行 Cmdlet 可建立的最大並行作業數。</span><span class="sxs-lookup"><span data-stu-id="1966b-140">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>

<span data-ttu-id="1966b-141">如果省略此參數或輸入的值 `0` ，則 PowerShell 會根據電腦上執行的 CIM Cmdlet 數目，計算最佳的節流限制。</span><span class="sxs-lookup"><span data-stu-id="1966b-141">If this parameter is omitted or a value of `0` is entered, PowerShell calculates an optimum throttle limit based on the number of CIM cmdlets that are running on the computer.</span></span> <span data-ttu-id="1966b-142">節流限制僅適用於目前 Cmdlet，不適用於工作階段或電腦。</span><span class="sxs-lookup"><span data-stu-id="1966b-142">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1966b-143">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1966b-143">-WhatIf</span></span>

<span data-ttu-id="1966b-144">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="1966b-144">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="1966b-145">不會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1966b-145">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="1966b-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1966b-146">CommonParameters</span></span>

<span data-ttu-id="1966b-147">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="1966b-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1966b-148">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="1966b-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1966b-149">輸入</span><span class="sxs-lookup"><span data-stu-id="1966b-149">INPUTS</span></span>

### <span data-ttu-id="1966b-150">無</span><span class="sxs-lookup"><span data-stu-id="1966b-150">None</span></span>

## <span data-ttu-id="1966b-151">輸出</span><span class="sxs-lookup"><span data-stu-id="1966b-151">OUTPUTS</span></span>

### <span data-ttu-id="1966b-152">無</span><span class="sxs-lookup"><span data-stu-id="1966b-152">None</span></span>

## <span data-ttu-id="1966b-153">注意</span><span class="sxs-lookup"><span data-stu-id="1966b-153">NOTES</span></span>

## <span data-ttu-id="1966b-154">相關連結</span><span class="sxs-lookup"><span data-stu-id="1966b-154">RELATED LINKS</span></span>

[<span data-ttu-id="1966b-155">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="1966b-155">Get-CimSession</span></span>](../CimCmdlets/Get-CimSession.md)

[<span data-ttu-id="1966b-156">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="1966b-156">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="1966b-157">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="1966b-157">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="1966b-158">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="1966b-158">New-CimSession</span></span>](../CimCmdlets/New-CimSession.md)

[<span data-ttu-id="1966b-159">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="1966b-159">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="1966b-160">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="1966b-160">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="1966b-161">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="1966b-161">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)

[<span data-ttu-id="1966b-162">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="1966b-162">Update-DscConfiguration</span></span>](Update-DscConfiguration.md)

[<span data-ttu-id="1966b-163">Windows PowerShell Desired State Configuration 概觀</span><span class="sxs-lookup"><span data-stu-id="1966b-163">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/overview)
