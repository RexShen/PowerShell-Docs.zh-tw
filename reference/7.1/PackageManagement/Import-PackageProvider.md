---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/import-packageprovider?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PackageProvider
ms.openlocfilehash: 8b900f8e7ff2583e20d359fd3d15aee653b9c1d6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202723"
---
# <span data-ttu-id="25feb-103">Import-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="25feb-103">Import-PackageProvider</span></span>

## <span data-ttu-id="25feb-104">概要</span><span class="sxs-lookup"><span data-stu-id="25feb-104">SYNOPSIS</span></span>
<span data-ttu-id="25feb-105">將套件管理封裝提供者加入至目前的會話。</span><span class="sxs-lookup"><span data-stu-id="25feb-105">Adds Package Management package providers to the current session.</span></span>

## <span data-ttu-id="25feb-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="25feb-106">SYNTAX</span></span>

```
Import-PackageProvider [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## <span data-ttu-id="25feb-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="25feb-107">DESCRIPTION</span></span>

<span data-ttu-id="25feb-108">`Import-PackageProvider`Cmdlet 會將一或多個封裝提供者加入至目前的會話。</span><span class="sxs-lookup"><span data-stu-id="25feb-108">The `Import-PackageProvider` cmdlet adds one or more package providers to the current session.</span></span>
<span data-ttu-id="25feb-109">您匯入的提供者必須安裝在本機電腦上。</span><span class="sxs-lookup"><span data-stu-id="25feb-109">The provider that you import must be installed on the local computer.</span></span>

<span data-ttu-id="25feb-110">若要取得可用提供者的清單，請執行 `Get-PackageProvider -ListAvailable` 。</span><span class="sxs-lookup"><span data-stu-id="25feb-110">To get a list of available providers, run `Get-PackageProvider -ListAvailable`.</span></span>
<span data-ttu-id="25feb-111">請注意，套件提供者名稱可以與其模組名稱不同。</span><span class="sxs-lookup"><span data-stu-id="25feb-111">Note that a package provider name can be different from its module name.</span></span>

<span data-ttu-id="25feb-112">基於安全性理由， **PackageManagement** 要求以 c # 為基礎的提供者必須包含 `provider.manifest` 。</span><span class="sxs-lookup"><span data-stu-id="25feb-112">Due to security reasons, **PackageManagement** requires C#-based providers to contain a `provider.manifest`.</span></span> <span data-ttu-id="25feb-113">如需有關如何建立已插入之提供者的詳細資訊 `provider.manifest` ，請參閱 `.csproj` 中的專案檔 [https://github.com/oneget/oneget](https://github.com/oneget/oneget) 。</span><span class="sxs-lookup"><span data-stu-id="25feb-113">For more information on how to build a provider with `provider.manifest` injected, see the `.csproj` project files on [https://github.com/oneget/oneget](https://github.com/oneget/oneget).</span></span>

## <span data-ttu-id="25feb-114">範例</span><span class="sxs-lookup"><span data-stu-id="25feb-114">EXAMPLES</span></span>

### <span data-ttu-id="25feb-115">範例1：從本機電腦匯入封裝提供者</span><span class="sxs-lookup"><span data-stu-id="25feb-115">Example 1: Import a package provider from the local computer</span></span>

```powershell
PS C:\> Import-PackageProvider -Name "Nuget"
```

<span data-ttu-id="25feb-116">此命令會在安裝到本機電腦之後，匯入 Nuget 提供者。</span><span class="sxs-lookup"><span data-stu-id="25feb-116">This command imports the Nuget provider after it has been installed on the local computer.</span></span>

### <span data-ttu-id="25feb-117">範例2：匯入特定版本的封裝提供者</span><span class="sxs-lookup"><span data-stu-id="25feb-117">Example 2: Import a specific version of a package provider</span></span>

```powershell
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force
Get-PackageProvider -ListAvailable
Import-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Verbose
```

<span data-ttu-id="25feb-118">此命令會尋找、安裝和匯入特定版本的 Nuget 封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="25feb-118">This command finds, installs, and imports a specific version of the Nuget package provider.</span></span>

## <span data-ttu-id="25feb-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="25feb-119">PARAMETERS</span></span>

### <span data-ttu-id="25feb-120">-Force</span><span class="sxs-lookup"><span data-stu-id="25feb-120">-Force</span></span>

<span data-ttu-id="25feb-121">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="25feb-121">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="25feb-122">重新匯入封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="25feb-122">Re-imports a package provider.</span></span>

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

### <span data-ttu-id="25feb-123">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="25feb-123">-ForceBootstrap</span></span>

<span data-ttu-id="25feb-124">指出此 Cmdlet 會強制套件管理自動安裝封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="25feb-124">Indicates that this cmdlet forces Package Management to automatically install the package provider.</span></span>

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

### <span data-ttu-id="25feb-125">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="25feb-125">-MaximumVersion</span></span>

<span data-ttu-id="25feb-126">指定您想要匯入的套件提供者所允許的最大版本。</span><span class="sxs-lookup"><span data-stu-id="25feb-126">Specifies the maximum allowed version of the package provider that you want to import.</span></span> <span data-ttu-id="25feb-127">如果您沒有加入此參數，則會匯 `Import-PackageProvider` 入提供者的最高可用版本。</span><span class="sxs-lookup"><span data-stu-id="25feb-127">If you do not add this parameter, `Import-PackageProvider` imports the highest available version of the provider.</span></span>

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

### <span data-ttu-id="25feb-128">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="25feb-128">-MinimumVersion</span></span>

<span data-ttu-id="25feb-129">指定您要匯入的套件提供者所允許的最低版本。</span><span class="sxs-lookup"><span data-stu-id="25feb-129">Specifies the minimum allowed version of the package provider that you want to import.</span></span> <span data-ttu-id="25feb-130">如果您未新增此參數，則會匯 `Import-PackageProvider` 入最高可用的套件版本，此套件也會滿足使用 *MaximumVersion* 參數所指定的最大版本。</span><span class="sxs-lookup"><span data-stu-id="25feb-130">If you do not add this parameter, `Import-PackageProvider` imports the highest available version of the package that also satisfies any maximum version that is specified using the *MaximumVersion* parameter.</span></span>

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

### <span data-ttu-id="25feb-131">-Name</span><span class="sxs-lookup"><span data-stu-id="25feb-131">-Name</span></span>

<span data-ttu-id="25feb-132">指定一或多個封裝提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="25feb-132">Specifies one or more package provider names.</span></span> <span data-ttu-id="25feb-133">不允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="25feb-133">Wildcards are not permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="25feb-134">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="25feb-134">-RequiredVersion</span></span>

<span data-ttu-id="25feb-135">指定您想要匯入之封裝提供者的確切版本。</span><span class="sxs-lookup"><span data-stu-id="25feb-135">Specifies the exact version of the package provider that you want to import.</span></span> <span data-ttu-id="25feb-136">如果您未新增此參數，則會匯 `Import-PackageProvider` 入提供者的最高可用版本，同時也會滿足使用 **MaximumVersion** 參數所指定的最大版本。</span><span class="sxs-lookup"><span data-stu-id="25feb-136">If you do not add this parameter, `Import-PackageProvider` imports the highest available version of the provider that also satisfies any maximum version specified using the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="25feb-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="25feb-137">CommonParameters</span></span>

<span data-ttu-id="25feb-138">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="25feb-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="25feb-139">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="25feb-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="25feb-140">輸入</span><span class="sxs-lookup"><span data-stu-id="25feb-140">INPUTS</span></span>

### <span data-ttu-id="25feb-141">Install-packageprovider。</span><span class="sxs-lookup"><span data-stu-id="25feb-141">Microsoft.PackageManagement.Implementation.PackageProvider</span></span>

<span data-ttu-id="25feb-142">您可以使用管線將所傳回的 **install-packageprovider** 物件傳送 `Get-PackageProvider` 至 `Import-PackageProvider` 。</span><span class="sxs-lookup"><span data-stu-id="25feb-142">You can pipe a **PackageProvider** object returned by `Get-PackageProvider` into `Import-PackageProvider`.</span></span>

## <span data-ttu-id="25feb-143">輸出</span><span class="sxs-lookup"><span data-stu-id="25feb-143">OUTPUTS</span></span>

## <span data-ttu-id="25feb-144">注意</span><span class="sxs-lookup"><span data-stu-id="25feb-144">NOTES</span></span>

## <span data-ttu-id="25feb-145">相關連結</span><span class="sxs-lookup"><span data-stu-id="25feb-145">RELATED LINKS</span></span>

[<span data-ttu-id="25feb-146">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="25feb-146">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="25feb-147">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="25feb-147">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)

[<span data-ttu-id="25feb-148">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="25feb-148">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="25feb-149">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="25feb-149">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="25feb-150">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="25feb-150">Get-PackageProvider</span></span>](Get-PackageProvider.md)

