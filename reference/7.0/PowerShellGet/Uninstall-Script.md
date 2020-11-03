---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/uninstall-script?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Script
ms.openlocfilehash: 640ef2187369599d35eea1bca9ad404f5dde745c
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93202024"
---
# <span data-ttu-id="0ac5f-103">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="0ac5f-103">Uninstall-Script</span></span>

## <span data-ttu-id="0ac5f-104">概要</span><span class="sxs-lookup"><span data-stu-id="0ac5f-104">SYNOPSIS</span></span>
<span data-ttu-id="0ac5f-105">卸載腳本。</span><span class="sxs-lookup"><span data-stu-id="0ac5f-105">Uninstalls a script.</span></span>

## <span data-ttu-id="0ac5f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0ac5f-106">SYNTAX</span></span>

### <span data-ttu-id="0ac5f-107">NameParameterSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="0ac5f-107">NameParameterSet (Default)</span></span>

```
Uninstall-Script [-Name] <String[]> [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-Force] [-AllowPrerelease] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="0ac5f-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="0ac5f-108">InputObject</span></span>

```
Uninstall-Script [-InputObject] <PSObject[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="0ac5f-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0ac5f-109">DESCRIPTION</span></span>

<span data-ttu-id="0ac5f-110">`Uninstall-Script`Cmdlet 會從本機電腦卸載指定的腳本。</span><span class="sxs-lookup"><span data-stu-id="0ac5f-110">The `Uninstall-Script` cmdlet uninstalls a specified script from the local computer.</span></span>

## <span data-ttu-id="0ac5f-111">範例</span><span class="sxs-lookup"><span data-stu-id="0ac5f-111">EXAMPLES</span></span>

### <span data-ttu-id="0ac5f-112">範例1：卸載腳本</span><span class="sxs-lookup"><span data-stu-id="0ac5f-112">Example 1: Uninstall a script</span></span>

<span data-ttu-id="0ac5f-113">此範例會卸載腳本。</span><span class="sxs-lookup"><span data-stu-id="0ac5f-113">This example uninstalls a script.</span></span>

```powershell
Uninstall-Script -Name UpdateManagement-Template
```

<span data-ttu-id="0ac5f-114">`Uninstall-Script` 使用 **Name** 參數來指定要從本機電腦卸載的腳本。</span><span class="sxs-lookup"><span data-stu-id="0ac5f-114">`Uninstall-Script` uses the **Name** parameter to specify the script to uninstall from the local computer.</span></span>

### <span data-ttu-id="0ac5f-115">範例2：使用管線卸載腳本</span><span class="sxs-lookup"><span data-stu-id="0ac5f-115">Example 2: Use the pipeline to uninstall a script</span></span>

<span data-ttu-id="0ac5f-116">在此範例中，管線是用來卸載腳本。</span><span class="sxs-lookup"><span data-stu-id="0ac5f-116">In this example, the pipeline is used to uninstall a script.</span></span>

```powershell
Get-InstalledScript -Name UpdateManagement-Template | Uninstall-Script
```

<span data-ttu-id="0ac5f-117">`Get-InstalledScript` 使用 **Name** 參數來指定腳本。</span><span class="sxs-lookup"><span data-stu-id="0ac5f-117">`Get-InstalledScript` uses the **Name** parameter to specify the script.</span></span> <span data-ttu-id="0ac5f-118">物件會沿著管線向下傳送至 `Uninstall-Script` ，並卸載腳本。</span><span class="sxs-lookup"><span data-stu-id="0ac5f-118">The object is sent down the pipeline to `Uninstall-Script` and the script is uninstalled.</span></span>

## <span data-ttu-id="0ac5f-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0ac5f-119">PARAMETERS</span></span>

### <span data-ttu-id="0ac5f-120">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="0ac5f-120">-AllowPrerelease</span></span>

<span data-ttu-id="0ac5f-121">可讓您卸載標記為發行前版本的腳本。</span><span class="sxs-lookup"><span data-stu-id="0ac5f-121">Allows you to uninstall a script marked as a prerelease.</span></span>

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

### <span data-ttu-id="0ac5f-122">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0ac5f-122">-Confirm</span></span>

<span data-ttu-id="0ac5f-123">在執行之前提示您確認 `Uninstall-Script` 。</span><span class="sxs-lookup"><span data-stu-id="0ac5f-123">Prompts you for confirmation before running `Uninstall-Script`.</span></span>

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

### <span data-ttu-id="0ac5f-124">-Force</span><span class="sxs-lookup"><span data-stu-id="0ac5f-124">-Force</span></span>

<span data-ttu-id="0ac5f-125">強制 `Uninstall-Script` 執行而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="0ac5f-125">Forces `Uninstall-Script` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="0ac5f-126">-InputObject</span><span class="sxs-lookup"><span data-stu-id="0ac5f-126">-InputObject</span></span>

<span data-ttu-id="0ac5f-127">接受 **PSRepositoryItemInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="0ac5f-127">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="0ac5f-128">例如，輸出 `Get-InstalledScript` 到變數，並使用該變數作為 **InputObject** 引數。</span><span class="sxs-lookup"><span data-stu-id="0ac5f-128">For example, output `Get-InstalledScript` to a variable and use that variable as the **InputObject** argument.</span></span>

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

### <span data-ttu-id="0ac5f-129">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="0ac5f-129">-MaximumVersion</span></span>

<span data-ttu-id="0ac5f-130">指定要卸載之腳本的最大或最新版本。</span><span class="sxs-lookup"><span data-stu-id="0ac5f-130">Specifies the maximum, or newest, version of the script to uninstall.</span></span> <span data-ttu-id="0ac5f-131">在相同的命令中不能使用 **MaximumVersion** 和 **RequiredVersion** 參數。</span><span class="sxs-lookup"><span data-stu-id="0ac5f-131">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="0ac5f-132">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="0ac5f-132">-MinimumVersion</span></span>

<span data-ttu-id="0ac5f-133">指定要解除安裝的指令碼的最低版本。</span><span class="sxs-lookup"><span data-stu-id="0ac5f-133">Specifies the minimum version of the script to uninstall.</span></span> <span data-ttu-id="0ac5f-134">**MinimumVersion** 和 **RequiredVersion** 參數無法在相同的命令中使用。</span><span class="sxs-lookup"><span data-stu-id="0ac5f-134">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="0ac5f-135">-Name</span><span class="sxs-lookup"><span data-stu-id="0ac5f-135">-Name</span></span>

<span data-ttu-id="0ac5f-136">指定要卸載之腳本名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="0ac5f-136">Specifies an array of script names to uninstall.</span></span>

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

### <span data-ttu-id="0ac5f-137">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="0ac5f-137">-RequiredVersion</span></span>

<span data-ttu-id="0ac5f-138">指定要卸載之腳本的確切版本號碼。</span><span class="sxs-lookup"><span data-stu-id="0ac5f-138">Specifies the exact version number of the script to uninstall.</span></span>

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

### <span data-ttu-id="0ac5f-139">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0ac5f-139">-WhatIf</span></span>

<span data-ttu-id="0ac5f-140">顯示執行時所發生 `Uninstall-Script` 的情況。</span><span class="sxs-lookup"><span data-stu-id="0ac5f-140">Shows what would happen if `Uninstall-Script` runs.</span></span> <span data-ttu-id="0ac5f-141">不會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0ac5f-141">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="0ac5f-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0ac5f-142">CommonParameters</span></span>

<span data-ttu-id="0ac5f-143">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="0ac5f-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0ac5f-144">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="0ac5f-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0ac5f-145">輸入</span><span class="sxs-lookup"><span data-stu-id="0ac5f-145">INPUTS</span></span>

### <span data-ttu-id="0ac5f-146">System.String[]</span><span class="sxs-lookup"><span data-stu-id="0ac5f-146">System.String[]</span></span>

### <span data-ttu-id="0ac5f-147">管理. PSObject []</span><span class="sxs-lookup"><span data-stu-id="0ac5f-147">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="0ac5f-148">System.String</span><span class="sxs-lookup"><span data-stu-id="0ac5f-148">System.String</span></span>

## <span data-ttu-id="0ac5f-149">輸出</span><span class="sxs-lookup"><span data-stu-id="0ac5f-149">OUTPUTS</span></span>

### <span data-ttu-id="0ac5f-150">System.Object</span><span class="sxs-lookup"><span data-stu-id="0ac5f-150">System.Object</span></span>

## <span data-ttu-id="0ac5f-151">注意</span><span class="sxs-lookup"><span data-stu-id="0ac5f-151">NOTES</span></span>

## <span data-ttu-id="0ac5f-152">相關連結</span><span class="sxs-lookup"><span data-stu-id="0ac5f-152">RELATED LINKS</span></span>

[<span data-ttu-id="0ac5f-153">Find-Script</span><span class="sxs-lookup"><span data-stu-id="0ac5f-153">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="0ac5f-154">Install-Script</span><span class="sxs-lookup"><span data-stu-id="0ac5f-154">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="0ac5f-155">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="0ac5f-155">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="0ac5f-156">Save-Script</span><span class="sxs-lookup"><span data-stu-id="0ac5f-156">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="0ac5f-157">Update-Script</span><span class="sxs-lookup"><span data-stu-id="0ac5f-157">Update-Script</span></span>](Update-Script.md)
