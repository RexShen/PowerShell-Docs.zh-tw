---
external help file: Disable-DscDebug.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/disable-dscdebug?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-DscDebug
ms.openlocfilehash: fdaba8358772f559a33117c796a923d774b009cb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203963"
---
# <span data-ttu-id="155ef-103">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="155ef-103">Disable-DscDebug</span></span>

## <span data-ttu-id="155ef-104">概要</span><span class="sxs-lookup"><span data-stu-id="155ef-104">SYNOPSIS</span></span>
<span data-ttu-id="155ef-105">停止對 DSC 資源的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="155ef-105">Stops debugging of DSC resources.</span></span>

## <span data-ttu-id="155ef-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="155ef-106">SYNTAX</span></span>

```
Disable-DscDebug [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="155ef-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="155ef-107">DESCRIPTION</span></span>
<span data-ttu-id="155ef-108">**Enable-dscdebug** 指令程式要求 Windows PowerShell DESIRED STATE CONFIGURATION (dsc) 引擎會停止對 dsc 資源的偵測。</span><span class="sxs-lookup"><span data-stu-id="155ef-108">The **Disable-DscDebug** cmdlet requests that the Windows PowerShell Desired State Configuration (DSC) engine stop debugging of DSC resources.</span></span>
<span data-ttu-id="155ef-109">如果 DSC 引擎目前不在偵測模式中，此 Cmdlet 就不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="155ef-109">This cmdlet has no effect if the DSC engine is not currently in debugging mode.</span></span>

## <span data-ttu-id="155ef-110">範例</span><span class="sxs-lookup"><span data-stu-id="155ef-110">EXAMPLES</span></span>

### <span data-ttu-id="155ef-111">範例1：停止資源調試</span><span class="sxs-lookup"><span data-stu-id="155ef-111">Example 1: Stop resource debugging</span></span>

```
PS C:\> Disable-DscDebug
```

<span data-ttu-id="155ef-112">此命令指示本機 Configuration Manager (LCM) 的 DSC 引擎停止資源調試。</span><span class="sxs-lookup"><span data-stu-id="155ef-112">This command indicates to the DSC engine on the Local Configuration Manager (LCM) to stop resource debugging.</span></span>

### <span data-ttu-id="155ef-113">範例2：檢查引擎狀態並停止調試</span><span class="sxs-lookup"><span data-stu-id="155ef-113">Example 2: Check the engine state and stop debugging</span></span>

```
PS C:\> if((Get-DscLocalConfigurationManager).DebugMode -like '*Break*'){Disable-DscDebug}
```

<span data-ttu-id="155ef-114">此命令會檢查 DSC 引擎狀態，而且只有在已處於偵測模式時，才會停止資源偵錯工具</span><span class="sxs-lookup"><span data-stu-id="155ef-114">This command checks the DSC engine state, and stops resource debugging only if it is already in debugging mode</span></span>

## <span data-ttu-id="155ef-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="155ef-115">PARAMETERS</span></span>

### <span data-ttu-id="155ef-116">-AsJob</span><span class="sxs-lookup"><span data-stu-id="155ef-116">-AsJob</span></span>
<span data-ttu-id="155ef-117">指出此 Cmdlet 會以背景工作方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="155ef-117">Indicates that this cmdlet runs the command as a background job.</span></span>

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

### <span data-ttu-id="155ef-118">-CimSession</span><span class="sxs-lookup"><span data-stu-id="155ef-118">-CimSession</span></span>
<span data-ttu-id="155ef-119">在遠端工作階段或遠端電腦上執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="155ef-119">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="155ef-120">輸入電腦名稱稱或會話物件，例如 [CimSession](/powershell/module/cimcmdlets/new-cimsession) 或 [CimSession](/powershell/module/cimcmdlets/get-cimsession) Cmdlet 的輸出。</span><span class="sxs-lookup"><span data-stu-id="155ef-120">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="155ef-121">預設為本機電腦上的目前工作階段。</span><span class="sxs-lookup"><span data-stu-id="155ef-121">The default is the current session on the local computer.</span></span>

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

### <span data-ttu-id="155ef-122">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="155ef-122">-ThrottleLimit</span></span>
<span data-ttu-id="155ef-123">指定為執行 Cmdlet 可建立的最大並行作業數。</span><span class="sxs-lookup"><span data-stu-id="155ef-123">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="155ef-124">如果省略此參數或輸入的值 `0` ，則 Windows PowerShell 會根據電腦上執行的 CIM Cmdlet 數目，計算 Cmdlet 的最佳節流限制。</span><span class="sxs-lookup"><span data-stu-id="155ef-124">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="155ef-125">節流限制僅適用於目前 Cmdlet，不適用於工作階段或電腦。</span><span class="sxs-lookup"><span data-stu-id="155ef-125">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="155ef-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="155ef-126">-Confirm</span></span>
<span data-ttu-id="155ef-127">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="155ef-127">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="155ef-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="155ef-128">-WhatIf</span></span>
<span data-ttu-id="155ef-129">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="155ef-129">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="155ef-130">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="155ef-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="155ef-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="155ef-131">CommonParameters</span></span>
<span data-ttu-id="155ef-132">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="155ef-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="155ef-133">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="155ef-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="155ef-134">輸入</span><span class="sxs-lookup"><span data-stu-id="155ef-134">INPUTS</span></span>

## <span data-ttu-id="155ef-135">輸出</span><span class="sxs-lookup"><span data-stu-id="155ef-135">OUTPUTS</span></span>

## <span data-ttu-id="155ef-136">注意</span><span class="sxs-lookup"><span data-stu-id="155ef-136">NOTES</span></span>

## <span data-ttu-id="155ef-137">相關連結</span><span class="sxs-lookup"><span data-stu-id="155ef-137">RELATED LINKS</span></span>

[<span data-ttu-id="155ef-138">Windows PowerShell Desired State Configuration 概觀</span><span class="sxs-lookup"><span data-stu-id="155ef-138">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="155ef-139">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="155ef-139">Enable-DscDebug</span></span>](Enable-DscDebug.md)

[<span data-ttu-id="155ef-140">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="155ef-140">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="155ef-141">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="155ef-141">Get-DscLocalConfigurationManager</span></span>](Get-DscLocalConfigurationManager.md)

[<span data-ttu-id="155ef-142">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="155ef-142">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="155ef-143">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="155ef-143">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="155ef-144">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="155ef-144">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)
