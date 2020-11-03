---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/publish-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Publish-DscConfiguration
ms.openlocfilehash: 139de2bfdb88c443e7bc48d36e37e95644556bf5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203939"
---
# <span data-ttu-id="95fed-103">Publish-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="95fed-103">Publish-DscConfiguration</span></span>

## <span data-ttu-id="95fed-104">概要</span><span class="sxs-lookup"><span data-stu-id="95fed-104">SYNOPSIS</span></span>
<span data-ttu-id="95fed-105">將 DSC 設定發佈到一組電腦。</span><span class="sxs-lookup"><span data-stu-id="95fed-105">Publishes a DSC configuration to a set of computers.</span></span>

## <span data-ttu-id="95fed-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="95fed-106">SYNTAX</span></span>

### <span data-ttu-id="95fed-107">ComputerNameSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="95fed-107">ComputerNameSet (Default)</span></span>

```
Publish-DscConfiguration [-Path] <String> [-Force] [[-ComputerName] <String[]>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="95fed-108">CimSessionSet</span><span class="sxs-lookup"><span data-stu-id="95fed-108">CimSessionSet</span></span>

```
Publish-DscConfiguration [-Path] <String> [-Force] [-ThrottleLimit <Int32>] -CimSession <CimSession[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="95fed-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="95fed-109">DESCRIPTION</span></span>
<span data-ttu-id="95fed-110">**Publish-DscConfiguration** Cmdlet 會在一組電腦上發佈 Windows PowerShell 預期狀態設定 (DSC) 的設定文件。</span><span class="sxs-lookup"><span data-stu-id="95fed-110">The **Publish-DscConfiguration** cmdlet publishes a Windows PowerShell Desired State Configuration (DSC) configuration document on set of computers.</span></span>
<span data-ttu-id="95fed-111">此 Cmdlet 不會套用設定。</span><span class="sxs-lookup"><span data-stu-id="95fed-111">This cmdlet does not apply the configuration.</span></span>
<span data-ttu-id="95fed-112">設定是由 Start-DscConfiguration Cmdlet 搭配 *UseExisting* 參數搭配使用時所套用，或 DSC 引擎執行其一致性循環時所套用。</span><span class="sxs-lookup"><span data-stu-id="95fed-112">Configurations are applied by either the Start-DscConfiguration cmdlet when it is used with the *UseExisting* parameter or when the DSC engine runs its consistency cycle.</span></span>
<span data-ttu-id="95fed-113">DSC 引擎也稱為「本機設定管理員 (LCM)」。</span><span class="sxs-lookup"><span data-stu-id="95fed-113">The DSC engine is also known as the Local Configuration Manager (LCM).</span></span>

<span data-ttu-id="95fed-114">傳遞多個設定文件的片段時，此 Cmdlet 特別有用。</span><span class="sxs-lookup"><span data-stu-id="95fed-114">This cmdlet is especially useful when fragments of multiple configuration documents are delivered.</span></span>
<span data-ttu-id="95fed-115">傳遞多個設定文件片段時，它們會覆寫較舊的設定文件片段。</span><span class="sxs-lookup"><span data-stu-id="95fed-115">When multiple configuration documents fragments are delivered, they overwrite the older configuration document fragments.</span></span>

## <span data-ttu-id="95fed-116">範例</span><span class="sxs-lookup"><span data-stu-id="95fed-116">EXAMPLES</span></span>

### <span data-ttu-id="95fed-117">範例 1︰將設定發佈到遠端電腦</span><span class="sxs-lookup"><span data-stu-id="95fed-117">Example 1: Publish a configuration to a remote computer</span></span>

```
PS C:\> Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

<span data-ttu-id="95fed-118">此命令會將設定發佈到遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="95fed-118">This command publishes a configuration to a remote computer.</span></span>
<span data-ttu-id="95fed-119">執行此 Cmdlet 的使用者應為遠端電腦上的系統管理員。</span><span class="sxs-lookup"><span data-stu-id="95fed-119">The user who runs the cmdlet should be administrator on the remote computer.</span></span>

## <span data-ttu-id="95fed-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="95fed-120">PARAMETERS</span></span>

### <span data-ttu-id="95fed-121">-CimSession</span><span class="sxs-lookup"><span data-stu-id="95fed-121">-CimSession</span></span>
<span data-ttu-id="95fed-122">在遠端工作階段或遠端電腦上執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="95fed-122">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="95fed-123">輸入電腦名稱稱或會話物件，例如 [CimSession](/powershell/module/cimcmdlets/new-cimsession) 或 [CimSession](/powershell/module/cimcmdlets/get-cimsession) Cmdlet 的輸出。</span><span class="sxs-lookup"><span data-stu-id="95fed-123">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="95fed-124">預設為本機電腦上的目前工作階段。</span><span class="sxs-lookup"><span data-stu-id="95fed-124">The default is the current session on the local computer.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="95fed-125">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="95fed-125">-ComputerName</span></span>
<span data-ttu-id="95fed-126">指定此 Cmdlet 在其中發佈組態的一或多部電腦。</span><span class="sxs-lookup"><span data-stu-id="95fed-126">Specifies one or more computers on which this cmdlet publishes the configuration.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="95fed-127">-Credential</span><span class="sxs-lookup"><span data-stu-id="95fed-127">-Credential</span></span>
<span data-ttu-id="95fed-128">指定用來存取目標裝置的認證。</span><span class="sxs-lookup"><span data-stu-id="95fed-128">Specifies credentials that are used to access the target device.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="95fed-129">-Force</span><span class="sxs-lookup"><span data-stu-id="95fed-129">-Force</span></span>
<span data-ttu-id="95fed-130">強制此 Cmdlet 完成。</span><span class="sxs-lookup"><span data-stu-id="95fed-130">Forces the cmdlet to finish.</span></span>
<span data-ttu-id="95fed-131">如果「本機設定管理員」重新整理模式設為「提取」，使用此參數會將其變更為「推入」，並會發佈 DSC 設定。</span><span class="sxs-lookup"><span data-stu-id="95fed-131">If the Local Configuration Manager refresh mode is set to PULL, usage of this parameter changes it to PUSH and enables publication of the DSC configuration.</span></span>
<span data-ttu-id="95fed-132">此外，如果有擱置中的 DSC 設定，使用此參數會覆寫該擱置中設定。</span><span class="sxs-lookup"><span data-stu-id="95fed-132">Also, if a pending DSC configuration exists, usage of this parameter overwrites that pending configuration.</span></span>

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

### <span data-ttu-id="95fed-133">-Path</span><span class="sxs-lookup"><span data-stu-id="95fed-133">-Path</span></span>
<span data-ttu-id="95fed-134">指定一個路徑，其中包含要發佈到目標電腦的設定。</span><span class="sxs-lookup"><span data-stu-id="95fed-134">Specifies a path that contains configurations to publish to target computers.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="95fed-135">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="95fed-135">-ThrottleLimit</span></span>
<span data-ttu-id="95fed-136">指定為執行 Cmdlet 可建立的最大並行作業數。</span><span class="sxs-lookup"><span data-stu-id="95fed-136">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="95fed-137">如果省略此參數或輸入的值 `0` ，則 Windows PowerShell 會根據電腦上執行的 CIM Cmdlet 數目，計算 Cmdlet 的最佳節流限制。</span><span class="sxs-lookup"><span data-stu-id="95fed-137">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="95fed-138">節流限制僅適用於目前 Cmdlet，不適用於工作階段或電腦。</span><span class="sxs-lookup"><span data-stu-id="95fed-138">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="95fed-139">-Confirm</span><span class="sxs-lookup"><span data-stu-id="95fed-139">-Confirm</span></span>
<span data-ttu-id="95fed-140">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="95fed-140">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="95fed-141">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="95fed-141">-WhatIf</span></span>
<span data-ttu-id="95fed-142">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="95fed-142">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="95fed-143">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="95fed-143">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="95fed-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="95fed-144">CommonParameters</span></span>
<span data-ttu-id="95fed-145">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="95fed-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="95fed-146">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="95fed-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="95fed-147">輸入</span><span class="sxs-lookup"><span data-stu-id="95fed-147">INPUTS</span></span>

## <span data-ttu-id="95fed-148">輸出</span><span class="sxs-lookup"><span data-stu-id="95fed-148">OUTPUTS</span></span>

## <span data-ttu-id="95fed-149">注意</span><span class="sxs-lookup"><span data-stu-id="95fed-149">NOTES</span></span>

## <span data-ttu-id="95fed-150">相關連結</span><span class="sxs-lookup"><span data-stu-id="95fed-150">RELATED LINKS</span></span>

[<span data-ttu-id="95fed-151">Windows PowerShell Desired State Configuration 概觀</span><span class="sxs-lookup"><span data-stu-id="95fed-151">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="95fed-152">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="95fed-152">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="95fed-153">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="95fed-153">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="95fed-154">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="95fed-154">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="95fed-155">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="95fed-155">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="95fed-156">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="95fed-156">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)
