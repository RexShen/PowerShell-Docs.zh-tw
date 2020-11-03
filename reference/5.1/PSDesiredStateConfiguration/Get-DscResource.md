---
external help file: PSDesiredStateConfiguration-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dscresource?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscResource
ms.openlocfilehash: 4a46e3b78ae9db4ea58f97daf37dca399c925549
ms.sourcegitcommit: 9dddf1d2e91ebcd347fcfb7bf6ef670d49a12ab7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "93205751"
---
# <span data-ttu-id="2ad3d-103">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="2ad3d-103">Get-DscResource</span></span>

## <span data-ttu-id="2ad3d-104">概要</span><span class="sxs-lookup"><span data-stu-id="2ad3d-104">SYNOPSIS</span></span>
<span data-ttu-id="2ad3d-105">取得 Desired State Configuration (DSC) 資源存在於電腦上。</span><span class="sxs-lookup"><span data-stu-id="2ad3d-105">Gets Desired State Configuration (DSC) resources present on the computer.</span></span>

## <span data-ttu-id="2ad3d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2ad3d-106">SYNTAX</span></span>

```
Get-DscResource [[-Name] <String[]>] [[-Module] <Object>] [-Syntax] [<CommonParameters>]
```

## <span data-ttu-id="2ad3d-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="2ad3d-107">DESCRIPTION</span></span>

<span data-ttu-id="2ad3d-108">此 `Get-DscResource` Cmdlet 會抓取存在於電腦上的 POWERSHELL DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="2ad3d-108">The `Get-DscResource` cmdlet retrieves the PowerShell DSC resources present on the computer.</span></span> <span data-ttu-id="2ad3d-109">此 Cmdlet 只會探索安裝在 PSModulePath 中的資源。</span><span class="sxs-lookup"><span data-stu-id="2ad3d-109">This cmdlet discovers only the resources installed in the PSModulePath.</span></span> <span data-ttu-id="2ad3d-110">它會顯示使用者所建立之內建和自訂提供者的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="2ad3d-110">It shows the details about built-in and custom providers, which are created by the user.</span></span> <span data-ttu-id="2ad3d-111">此 Cmdlet 也會顯示覆合資源的詳細資料，也就是封裝為模組，或在會話的執行時間建立的其他設定。</span><span class="sxs-lookup"><span data-stu-id="2ad3d-111">This cmdlet also shows details about composite resources, which are other configurations that are packaged as module or created at run time in the session.</span></span>

## <span data-ttu-id="2ad3d-112">範例</span><span class="sxs-lookup"><span data-stu-id="2ad3d-112">EXAMPLES</span></span>

### <span data-ttu-id="2ad3d-113">範例1：取得本機電腦上的所有資源</span><span class="sxs-lookup"><span data-stu-id="2ad3d-113">Example 1: Get all resources on the local computer</span></span>

```powershell
Get-DscResource
```

<span data-ttu-id="2ad3d-114">此命令會取得本機電腦上的所有資源。</span><span class="sxs-lookup"><span data-stu-id="2ad3d-114">This command gets all the resources on the local computer.</span></span>

### <span data-ttu-id="2ad3d-115">範例2：指定名稱以取得資源</span><span class="sxs-lookup"><span data-stu-id="2ad3d-115">Example 2: Get a resource by specifying the name</span></span>

```powershell
Get-DscResource -Name "WindowsFeature"
```

<span data-ttu-id="2ad3d-116">此命令會取得 WindowsFeature 資源。</span><span class="sxs-lookup"><span data-stu-id="2ad3d-116">This command gets the WindowsFeature resource.</span></span>

### <span data-ttu-id="2ad3d-117">範例3：取得模組中的所有資源</span><span class="sxs-lookup"><span data-stu-id="2ad3d-117">Example 3: Get all the resources from a module</span></span>

```powershell
Get-DscResource -Module "xHyper-V"
```

<span data-ttu-id="2ad3d-118">此命令會從 xHyper-V 模組取得所有資源。</span><span class="sxs-lookup"><span data-stu-id="2ad3d-118">This command gets all the resources from the xHyper-V module.</span></span>

### <span data-ttu-id="2ad3d-119">範例4：使用萬用字元取得資源</span><span class="sxs-lookup"><span data-stu-id="2ad3d-119">Example 4: Get a resource by using wildcard characters</span></span>

```powershell
Get-DscResource -Name P*,r*
```

<span data-ttu-id="2ad3d-120">此命令會取得符合 **Name** 參數所指定之萬用字元模式的所有資源。</span><span class="sxs-lookup"><span data-stu-id="2ad3d-120">This command gets all resources that match the wildcard pattern specified by the **Name** parameter.</span></span>

### <span data-ttu-id="2ad3d-121">範例5：取得資源語法</span><span class="sxs-lookup"><span data-stu-id="2ad3d-121">Example 5: Get a resource syntax</span></span>

```powershell
Get-DscResource -Name "WindowsFeature" -Syntax
```

<span data-ttu-id="2ad3d-122">此命令會取得 WindowsFeature 資源，並顯示資源的語法。</span><span class="sxs-lookup"><span data-stu-id="2ad3d-122">This command gets the WindowsFeature resource, and shows the syntax for the resource.</span></span>

### <span data-ttu-id="2ad3d-123">範例6：取得資源的所有屬性</span><span class="sxs-lookup"><span data-stu-id="2ad3d-123">Example 6: Get all the properties for a resource</span></span>

```powershell
Get-DscResource -Name "User" | Select-Object -ExpandProperty Properties
```

<span data-ttu-id="2ad3d-124">此命令會取得使用者資源，然後使用管線運算子傳回使用者資源的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="2ad3d-124">This command gets the User resource, and then uses the pipeline operator to return all the properties for the User resource.</span></span>

### <span data-ttu-id="2ad3d-125">範例7：從指定的模組取得具有指定版本的所有資源</span><span class="sxs-lookup"><span data-stu-id="2ad3d-125">Example 7: Get all the resources from a specified module with a specified version</span></span>

```powershell
Get-DscResource -Module @{ModuleName='xHyper-V';RequiredVersion='3.0.0.0'}
```

<span data-ttu-id="2ad3d-126">此命令會從 xHyper-V 模組取得具有版本3.0.0.0 的所有資源。</span><span class="sxs-lookup"><span data-stu-id="2ad3d-126">This command gets all the resources from xHyper-V module with version 3.0.0.0.</span></span>

## <span data-ttu-id="2ad3d-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2ad3d-127">PARAMETERS</span></span>

### <span data-ttu-id="2ad3d-128">-Module</span><span class="sxs-lookup"><span data-stu-id="2ad3d-128">-Module</span></span>

<span data-ttu-id="2ad3d-129">指定要為其查看 DSC 資源的模組名稱或完整名稱。</span><span class="sxs-lookup"><span data-stu-id="2ad3d-129">Specifies the name or fully qualified name of the module for which to view the DSC resource.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2ad3d-130">-Name</span><span class="sxs-lookup"><span data-stu-id="2ad3d-130">-Name</span></span>

<span data-ttu-id="2ad3d-131">指定要查看之 DSC 資源的名稱陣列。</span><span class="sxs-lookup"><span data-stu-id="2ad3d-131">Specifies an array of names of the DSC resource to view.</span></span>

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

### <span data-ttu-id="2ad3d-132">-語法</span><span class="sxs-lookup"><span data-stu-id="2ad3d-132">-Syntax</span></span>

<span data-ttu-id="2ad3d-133">指出此 Cmdlet 會傳回指定之 DSC 資源的語法視圖。</span><span class="sxs-lookup"><span data-stu-id="2ad3d-133">Indicates that the cmdlet returns the syntax view of the specified DSC resources.</span></span> <span data-ttu-id="2ad3d-134">傳回的語法說明如何使用 PowerShell 腳本中的資源。</span><span class="sxs-lookup"><span data-stu-id="2ad3d-134">The returned syntax shows how to use the resources in a PowerShell script.</span></span>

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

### <span data-ttu-id="2ad3d-135">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2ad3d-135">CommonParameters</span></span>

<span data-ttu-id="2ad3d-136">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="2ad3d-136">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2ad3d-137">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="2ad3d-137">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2ad3d-138">輸入</span><span class="sxs-lookup"><span data-stu-id="2ad3d-138">INPUTS</span></span>

### <span data-ttu-id="2ad3d-139">System.String[]</span><span class="sxs-lookup"><span data-stu-id="2ad3d-139">System.String[]</span></span>

### <span data-ttu-id="2ad3d-140">System.Object</span><span class="sxs-lookup"><span data-stu-id="2ad3d-140">System.Object</span></span>

## <span data-ttu-id="2ad3d-141">輸出</span><span class="sxs-lookup"><span data-stu-id="2ad3d-141">OUTPUTS</span></span>

### <span data-ttu-id="2ad3d-142">DesiredStateConfiguration. DscResourceInfo []</span><span class="sxs-lookup"><span data-stu-id="2ad3d-142">Microsoft.PowerShell.DesiredStateConfiguration.DscResourceInfo[]</span></span>

### <span data-ttu-id="2ad3d-143">string[]</span><span class="sxs-lookup"><span data-stu-id="2ad3d-143">string[]</span></span>

## <span data-ttu-id="2ad3d-144">注意</span><span class="sxs-lookup"><span data-stu-id="2ad3d-144">NOTES</span></span>

- <span data-ttu-id="2ad3d-145">`Get-DscResource` 在7.0 以下的 PowerShell 版本中找不到以類別為基礎的 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="2ad3d-145">`Get-DscResource` does not find Class based DSC resources in PowerShell versions below 7.0.</span></span>

## <span data-ttu-id="2ad3d-146">相關連結</span><span class="sxs-lookup"><span data-stu-id="2ad3d-146">RELATED LINKS</span></span>

[<span data-ttu-id="2ad3d-147">PowerShell Desired State Configuration 總覽</span><span class="sxs-lookup"><span data-stu-id="2ad3d-147">PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/overview)

[<span data-ttu-id="2ad3d-148">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="2ad3d-148">Invoke-DscResource</span></span>](Invoke-DscResource.md)
