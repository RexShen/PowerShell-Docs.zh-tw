---
external help file: Enable-DscDebug.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/enable-dscdebug?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-DscDebug
ms.openlocfilehash: 136481c5a1945c3d5cbd1ca7fc8ce5f580c39b0f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203967"
---
# <span data-ttu-id="20ce7-103">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="20ce7-103">Enable-DscDebug</span></span>

## <span data-ttu-id="20ce7-104">概要</span><span class="sxs-lookup"><span data-stu-id="20ce7-104">SYNOPSIS</span></span>
<span data-ttu-id="20ce7-105">開始對所有 DSC 資源進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="20ce7-105">Starts debugging of all DSC resources.</span></span>

## <span data-ttu-id="20ce7-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="20ce7-106">SYNTAX</span></span>

```
Enable-DscDebug [-BreakAll] [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="20ce7-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="20ce7-107">DESCRIPTION</span></span>
<span data-ttu-id="20ce7-108">**Enable-DscDebug** Cmdlet 會透過 DSC 引擎 (也稱為「本機設定管理員 (LCM)」) 來啟用 Windows PowerShell 預期狀態設定 (DSC) 資源偵錯。</span><span class="sxs-lookup"><span data-stu-id="20ce7-108">The **Enable-DscDebug** cmdlet enables Windows PowerShell Desired State Configuration (DSC) resource debugging by the DSC engine, which is also known as the Local Configuration Manager (LCM).</span></span>
<span data-ttu-id="20ce7-109">根據預設，所有資源執行個體會開始偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="20ce7-109">By default, all resource instances break into the debugger.</span></span>

## <span data-ttu-id="20ce7-110">範例</span><span class="sxs-lookup"><span data-stu-id="20ce7-110">EXAMPLES</span></span>

### <span data-ttu-id="20ce7-111">範例 1︰開始偵錯</span><span class="sxs-lookup"><span data-stu-id="20ce7-111">Example 1: Start debugging</span></span>

```
PS C:\> Enable-DscDebug -BreakAll
```

<span data-ttu-id="20ce7-112">此命令指示 DSC 引擎或 LCM 開始對資源偵錯。</span><span class="sxs-lookup"><span data-stu-id="20ce7-112">This command indicates to the DSC engine or LCM to start resource debugging.</span></span>
<span data-ttu-id="20ce7-113">下次執行設定時，程序會進入偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="20ce7-113">The next time the configuration is run, the process enters the debugger.</span></span>

### <span data-ttu-id="20ce7-114">範例 2︰開始遠端偵錯</span><span class="sxs-lookup"><span data-stu-id="20ce7-114">Example 2: Start remote debugging</span></span>

```
PS C:\> Enable-DscDebug -BreakAll -CimSession DeploymentServer
```

<span data-ttu-id="20ce7-115">此命令指示遠端電腦的 DSC 引擎開始對資源偵錯。</span><span class="sxs-lookup"><span data-stu-id="20ce7-115">This command indicates to the DSC engine of the remote computer to start resource debugging.</span></span>

## <span data-ttu-id="20ce7-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="20ce7-116">PARAMETERS</span></span>

### <span data-ttu-id="20ce7-117">-AsJob</span><span class="sxs-lookup"><span data-stu-id="20ce7-117">-AsJob</span></span>
<span data-ttu-id="20ce7-118">指出此 Cmdlet 會以背景工作方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="20ce7-118">Indicates that this cmdlet runs the command as a background job.</span></span>

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

### <span data-ttu-id="20ce7-119">-BreakAll</span><span class="sxs-lookup"><span data-stu-id="20ce7-119">-BreakAll</span></span>
<span data-ttu-id="20ce7-120">指示所有資源在執行設定時進入偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="20ce7-120">Indicates that all resources enter the debugger when a configuration runs.</span></span>

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

### <span data-ttu-id="20ce7-121">-CimSession</span><span class="sxs-lookup"><span data-stu-id="20ce7-121">-CimSession</span></span>
<span data-ttu-id="20ce7-122">在遠端工作階段或遠端電腦上執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="20ce7-122">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="20ce7-123">輸入電腦名稱稱或會話物件，例如 [CimSession](/powershell/module/cimcmdlets/new-cimsession) 或 [CimSession](/powershell/module/cimcmdlets/get-cimsession) Cmdlet 的輸出。</span><span class="sxs-lookup"><span data-stu-id="20ce7-123">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="20ce7-124">預設為本機電腦上的目前工作階段。</span><span class="sxs-lookup"><span data-stu-id="20ce7-124">The default is the current session on the local computer.</span></span>

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

### <span data-ttu-id="20ce7-125">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="20ce7-125">-ThrottleLimit</span></span>
<span data-ttu-id="20ce7-126">指定為執行 Cmdlet 可建立的最大並行作業數。</span><span class="sxs-lookup"><span data-stu-id="20ce7-126">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="20ce7-127">如果省略此參數或輸入的值 `0` ，則 Windows PowerShell 會根據電腦上執行的 CIM Cmdlet 數目，計算 Cmdlet 的最佳節流限制。</span><span class="sxs-lookup"><span data-stu-id="20ce7-127">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="20ce7-128">節流限制僅適用於目前 Cmdlet，不適用於工作階段或電腦。</span><span class="sxs-lookup"><span data-stu-id="20ce7-128">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="20ce7-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="20ce7-129">-Confirm</span></span>
<span data-ttu-id="20ce7-130">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="20ce7-130">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="20ce7-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="20ce7-131">-WhatIf</span></span>
<span data-ttu-id="20ce7-132">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="20ce7-132">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="20ce7-133">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="20ce7-133">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="20ce7-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="20ce7-134">CommonParameters</span></span>
<span data-ttu-id="20ce7-135">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="20ce7-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="20ce7-136">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="20ce7-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="20ce7-137">輸入</span><span class="sxs-lookup"><span data-stu-id="20ce7-137">INPUTS</span></span>

## <span data-ttu-id="20ce7-138">輸出</span><span class="sxs-lookup"><span data-stu-id="20ce7-138">OUTPUTS</span></span>

## <span data-ttu-id="20ce7-139">注意</span><span class="sxs-lookup"><span data-stu-id="20ce7-139">NOTES</span></span>

## <span data-ttu-id="20ce7-140">相關連結</span><span class="sxs-lookup"><span data-stu-id="20ce7-140">RELATED LINKS</span></span>

[<span data-ttu-id="20ce7-141">Windows PowerShell Desired State Configuration 概觀</span><span class="sxs-lookup"><span data-stu-id="20ce7-141">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="20ce7-142">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="20ce7-142">Disable-DscDebug</span></span>](Disable-DscDebug.md)

[<span data-ttu-id="20ce7-143">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="20ce7-143">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="20ce7-144">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="20ce7-144">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="20ce7-145">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="20ce7-145">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="20ce7-146">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="20ce7-146">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="20ce7-147">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="20ce7-147">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)
