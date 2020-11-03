---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/02/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/uninstall-module?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Module
ms.openlocfilehash: 427f50a697186354c889e85bf080189f5ee4af9c
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201963"
---
# <span data-ttu-id="1e8b1-103">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="1e8b1-103">Uninstall-Module</span></span>

## <span data-ttu-id="1e8b1-104">概要</span><span class="sxs-lookup"><span data-stu-id="1e8b1-104">SYNOPSIS</span></span>
<span data-ttu-id="1e8b1-105">解除安裝模組。</span><span class="sxs-lookup"><span data-stu-id="1e8b1-105">Uninstalls a module.</span></span>

## <span data-ttu-id="1e8b1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1e8b1-106">SYNTAX</span></span>

### <span data-ttu-id="1e8b1-107">NameParameterSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="1e8b1-107">NameParameterSet (Default)</span></span>

```
Uninstall-Module [-Name] <String[]> [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-AllowPrerelease] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="1e8b1-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="1e8b1-108">InputObject</span></span>

```
Uninstall-Module [-InputObject] <PSObject[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="1e8b1-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="1e8b1-109">DESCRIPTION</span></span>

<span data-ttu-id="1e8b1-110">`Uninstall-Module`Cmdlet 會從本機電腦卸載指定的模組。</span><span class="sxs-lookup"><span data-stu-id="1e8b1-110">The `Uninstall-Module` cmdlet uninstalls a specified module from the local computer.</span></span> <span data-ttu-id="1e8b1-111">如果模組有其他模組作為相依性，您就無法將其卸載。</span><span class="sxs-lookup"><span data-stu-id="1e8b1-111">You can't uninstall a module if it has other modules as dependencies.</span></span>

## <span data-ttu-id="1e8b1-112">範例</span><span class="sxs-lookup"><span data-stu-id="1e8b1-112">EXAMPLES</span></span>

### <span data-ttu-id="1e8b1-113">範例1：卸載模組</span><span class="sxs-lookup"><span data-stu-id="1e8b1-113">Example 1: Uninstall a module</span></span>

<span data-ttu-id="1e8b1-114">此範例會卸載模組。</span><span class="sxs-lookup"><span data-stu-id="1e8b1-114">This example uninstalls a module.</span></span>

```powershell
Uninstall-Module -Name SpeculationControl
```

<span data-ttu-id="1e8b1-115">`Uninstall-Module` 使用 **Name** 參數來指定要從本機電腦卸載的模組。</span><span class="sxs-lookup"><span data-stu-id="1e8b1-115">`Uninstall-Module` uses the **Name** parameter to specify the module to uninstall from the local computer.</span></span>

### <span data-ttu-id="1e8b1-116">範例2：使用管線來卸載模組</span><span class="sxs-lookup"><span data-stu-id="1e8b1-116">Example 2: Use the pipeline to uninstall a module</span></span>

<span data-ttu-id="1e8b1-117">在此範例中，管線是用來卸載模組。</span><span class="sxs-lookup"><span data-stu-id="1e8b1-117">In this example, the pipeline is used to uninstall a module.</span></span>

```powershell
Get-InstalledModule -Name SpeculationControl | Uninstall-Module
```

<span data-ttu-id="1e8b1-118">`Get-InstalledModule` 使用 **Name** 參數來指定模組。</span><span class="sxs-lookup"><span data-stu-id="1e8b1-118">`Get-InstalledModule` uses the **Name** parameter to specify the module.</span></span> <span data-ttu-id="1e8b1-119">物件會沿著管線向下傳送至 `Uninstall-Module` ，並卸載。</span><span class="sxs-lookup"><span data-stu-id="1e8b1-119">The object is sent down the pipeline to `Uninstall-Module` and is uninstalled.</span></span>

## <span data-ttu-id="1e8b1-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1e8b1-120">PARAMETERS</span></span>

### <span data-ttu-id="1e8b1-121">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="1e8b1-121">-AllowPrerelease</span></span>

<span data-ttu-id="1e8b1-122">可讓您卸載標示為發行前版本的模組。</span><span class="sxs-lookup"><span data-stu-id="1e8b1-122">Allows you to uninstall a module marked as a prerelease.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1e8b1-123">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="1e8b1-123">-AllVersions</span></span>

<span data-ttu-id="1e8b1-124">指定您想要包含模組的所有可用版本。</span><span class="sxs-lookup"><span data-stu-id="1e8b1-124">Specifies that you want to include all available versions of a module.</span></span> <span data-ttu-id="1e8b1-125">您無法搭配 **MinimumVersion** 、 **MaximumVersion** 或 **RequiredVersion** 參數使用 **allversions 進行篩選** 參數。</span><span class="sxs-lookup"><span data-stu-id="1e8b1-125">You can't use the **AllVersions** parameter with the **MinimumVersion** , **MaximumVersion** , or **RequiredVersion** parameters.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1e8b1-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1e8b1-126">-Confirm</span></span>

<span data-ttu-id="1e8b1-127">在執行之前提示您確認 `Uninstall-Module` 。</span><span class="sxs-lookup"><span data-stu-id="1e8b1-127">Prompts you for confirmation before running the `Uninstall-Module`.</span></span>

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

### <span data-ttu-id="1e8b1-128">-Force</span><span class="sxs-lookup"><span data-stu-id="1e8b1-128">-Force</span></span>

<span data-ttu-id="1e8b1-129">強制 `Uninstall-Module` 執行而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="1e8b1-129">Forces `Uninstall-Module` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="1e8b1-130">-InputObject</span><span class="sxs-lookup"><span data-stu-id="1e8b1-130">-InputObject</span></span>

<span data-ttu-id="1e8b1-131">接受 **PSRepositoryItemInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="1e8b1-131">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="1e8b1-132">例如，輸出 `Get-InstalledModule` 到變數，並使用該變數作為 **InputObject** 引數。</span><span class="sxs-lookup"><span data-stu-id="1e8b1-132">For example, output `Get-InstalledModule` to a variable and use that variable as the **InputObject** argument.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="1e8b1-133">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="1e8b1-133">-MaximumVersion</span></span>

<span data-ttu-id="1e8b1-134">指定要解除安裝之模組的最高或最新版本。</span><span class="sxs-lookup"><span data-stu-id="1e8b1-134">Specifies the maximum, or newest, version of the module to uninstall.</span></span> <span data-ttu-id="1e8b1-135">在相同的命令中不能使用 **MaximumVersion** 和 **RequiredVersion** 參數。</span><span class="sxs-lookup"><span data-stu-id="1e8b1-135">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1e8b1-136">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="1e8b1-136">-MinimumVersion</span></span>

<span data-ttu-id="1e8b1-137">指定要卸載之模組的最小版本。</span><span class="sxs-lookup"><span data-stu-id="1e8b1-137">Specifies the minimum version of the module to uninstall.</span></span> <span data-ttu-id="1e8b1-138">**MinimumVersion** 和 **RequiredVersion** 參數無法在相同的命令中使用。</span><span class="sxs-lookup"><span data-stu-id="1e8b1-138">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1e8b1-139">-Name</span><span class="sxs-lookup"><span data-stu-id="1e8b1-139">-Name</span></span>

<span data-ttu-id="1e8b1-140">指定要卸載的模組名稱陣列。</span><span class="sxs-lookup"><span data-stu-id="1e8b1-140">Specifies an array of module names to uninstall.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1e8b1-141">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="1e8b1-141">-RequiredVersion</span></span>

<span data-ttu-id="1e8b1-142">指定要解除安裝的模組的確切版本號碼。</span><span class="sxs-lookup"><span data-stu-id="1e8b1-142">Specifies the exact version number of the module to uninstall.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1e8b1-143">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1e8b1-143">-WhatIf</span></span>

<span data-ttu-id="1e8b1-144">顯示執行時所發生 `Uninstall-Module` 的情況。</span><span class="sxs-lookup"><span data-stu-id="1e8b1-144">Shows what would happen if `Uninstall-Module` runs.</span></span> <span data-ttu-id="1e8b1-145">不會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1e8b1-145">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="1e8b1-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1e8b1-146">CommonParameters</span></span>

<span data-ttu-id="1e8b1-147">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="1e8b1-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1e8b1-148">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="1e8b1-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1e8b1-149">輸入</span><span class="sxs-lookup"><span data-stu-id="1e8b1-149">INPUTS</span></span>

### <span data-ttu-id="1e8b1-150">System.String[]</span><span class="sxs-lookup"><span data-stu-id="1e8b1-150">System.String[]</span></span>

### <span data-ttu-id="1e8b1-151">管理. PSObject []</span><span class="sxs-lookup"><span data-stu-id="1e8b1-151">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="1e8b1-152">System.String</span><span class="sxs-lookup"><span data-stu-id="1e8b1-152">System.String</span></span>

## <span data-ttu-id="1e8b1-153">輸出</span><span class="sxs-lookup"><span data-stu-id="1e8b1-153">OUTPUTS</span></span>

### <span data-ttu-id="1e8b1-154">System.Object</span><span class="sxs-lookup"><span data-stu-id="1e8b1-154">System.Object</span></span>

## <span data-ttu-id="1e8b1-155">注意</span><span class="sxs-lookup"><span data-stu-id="1e8b1-155">NOTES</span></span>

## <span data-ttu-id="1e8b1-156">相關連結</span><span class="sxs-lookup"><span data-stu-id="1e8b1-156">RELATED LINKS</span></span>

[<span data-ttu-id="1e8b1-157">Find-Module</span><span class="sxs-lookup"><span data-stu-id="1e8b1-157">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="1e8b1-158">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="1e8b1-158">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="1e8b1-159">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="1e8b1-159">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="1e8b1-160">Save-Module</span><span class="sxs-lookup"><span data-stu-id="1e8b1-160">Save-Module</span></span>](Save-Module.md)

[<span data-ttu-id="1e8b1-161">Update-Module</span><span class="sxs-lookup"><span data-stu-id="1e8b1-161">Update-Module</span></span>](Update-Module.md)
