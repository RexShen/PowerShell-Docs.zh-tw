---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 05/24/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/uninstall-package?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Package
ms.openlocfilehash: 6f22da7040413f64e9e96a7df57401a0701156bd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202920"
---
# <span data-ttu-id="b7f0e-103">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="b7f0e-103">Uninstall-Package</span></span>

## <span data-ttu-id="b7f0e-104">概要</span><span class="sxs-lookup"><span data-stu-id="b7f0e-104">SYNOPSIS</span></span>
<span data-ttu-id="b7f0e-105">卸載一或多個軟體套件。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-105">Uninstalls one or more software packages.</span></span>

## <span data-ttu-id="b7f0e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b7f0e-106">SYNTAX</span></span>

### <span data-ttu-id="b7f0e-107">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="b7f0e-107">PackageByInputObject</span></span>

```
Uninstall-Package [-InputObject] <SoftwareIdentity[]> [-AllVersions] [-Force] [-ForceBootstrap]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b7f0e-108">PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="b7f0e-108">PackageBySearch</span></span>

```
Uninstall-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="b7f0e-109">msi： PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="b7f0e-109">msi:PackageByInputObject</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-AdditionalArguments <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="b7f0e-110">msi： PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="b7f0e-110">msi:PackageBySearch</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-AdditionalArguments <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="b7f0e-111">程式： PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="b7f0e-111">Programs:PackageByInputObject</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-IncludeWindowsInstaller] [-IncludeSystemComponent] [<CommonParameters>]
```

### <span data-ttu-id="b7f0e-112">程式： PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="b7f0e-112">Programs:PackageBySearch</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-IncludeWindowsInstaller] [-IncludeSystemComponent] [<CommonParameters>]
```

### <span data-ttu-id="b7f0e-113">NuGet： PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="b7f0e-113">NuGet:PackageByInputObject</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### <span data-ttu-id="b7f0e-114">NuGet： PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="b7f0e-114">NuGet:PackageBySearch</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### <span data-ttu-id="b7f0e-115">PowerShellGet： PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="b7f0e-115">PowerShellGet:PackageByInputObject</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-Scope <String>]
 [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber] [-SkipPublisherCheck]
 [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="b7f0e-116">PowerShellGet： PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="b7f0e-116">PowerShellGet:PackageBySearch</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-Scope <String>]
 [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber] [-SkipPublisherCheck]
 [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions] [<CommonParameters>]
```

## <span data-ttu-id="b7f0e-117">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b7f0e-117">DESCRIPTION</span></span>

<span data-ttu-id="b7f0e-118">`Uninstall-Package`Cmdlet 會從本機電腦卸載一或多個軟體套件。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-118">The `Uninstall-Package` cmdlet uninstalls one or more software packages from the local computer.</span></span> <span data-ttu-id="b7f0e-119">若要尋找已安裝的套件，請使用 `Get-Package` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-119">To find installed packages, use the `Get-Package` cmdlet.</span></span>

## <span data-ttu-id="b7f0e-120">範例</span><span class="sxs-lookup"><span data-stu-id="b7f0e-120">EXAMPLES</span></span>

### <span data-ttu-id="b7f0e-121">範例1：卸載套件</span><span class="sxs-lookup"><span data-stu-id="b7f0e-121">Example 1: Uninstall a package</span></span>

<span data-ttu-id="b7f0e-122">`Uninstall-Package`Cmdlet 會卸載套件。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-122">The `Uninstall-Package` cmdlet uninstalls packages.</span></span> <span data-ttu-id="b7f0e-123">**Name** 參數指定要卸載的封裝。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-123">The **Name** parameter specifies the package to uninstall.</span></span> <span data-ttu-id="b7f0e-124">如果安裝了多個版本的封裝，則會卸載最新版本。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-124">If multiple versions of a package are installed, the newest version is uninstalled.</span></span>

```
PS> Uninstall-Package -Name NuGet.Core
```

### <span data-ttu-id="b7f0e-125">範例2：使用管線卸載套件</span><span class="sxs-lookup"><span data-stu-id="b7f0e-125">Example 2: Use the pipeline to uninstall a package</span></span>

<span data-ttu-id="b7f0e-126">`Get-Package` 找出特定的封裝，並將 **SoftwareIdentity** 物件沿著管線向下傳送至 `Uninsall-Package` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-126">`Get-Package` locates a specific package and sends the **SoftwareIdentity** object down the pipeline to the `Uninsall-Package` cmdlet.</span></span>

```
PS> Get-Package -Name NuGet.Core -RequiredVersion 2.14.0 | Uninstall-Package
```

<span data-ttu-id="b7f0e-127">此 `Get-Package` Cmdlet 會使用 **Name** 和 **RequiredVersion** 參數來指定封裝。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-127">The `Get-Package` cmdlet uses the **Name** and **RequiredVersion** parameters to specify a package.</span></span>
<span data-ttu-id="b7f0e-128">**SoftwareIdentity** 物件會沿著管線向下傳送。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-128">A **SoftwareIdentity** object is sent down the pipeline.</span></span> <span data-ttu-id="b7f0e-129">`Uninstall-Package`Cmdlet 會以 **InputObject** 的形式接收物件，並移除封裝。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-129">The `Uninstall-Package` cmdlet receives the object as an **InputObject** and removes the package.</span></span>

<span data-ttu-id="b7f0e-130">或者， `Uninstall-Package` Cmdlet 可以指定 **InputObject** 參數的值：</span><span class="sxs-lookup"><span data-stu-id="b7f0e-130">As an alternative, the `Uninstall-Package` cmdlet can specify a value for the **InputObject** parameter:</span></span>

`Uninstall-Package -InputObject ( Get-Package -Name NuGet.Core -RequiredVersion 2.14.0 )`

## <span data-ttu-id="b7f0e-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b7f0e-131">PARAMETERS</span></span>

### <span data-ttu-id="b7f0e-132">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="b7f0e-132">-AllowClobber</span></span>

<span data-ttu-id="b7f0e-133">覆寫與現有命令衝突的警告訊息。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-133">Overrides warning messages about conflicts with existing commands.</span></span> <span data-ttu-id="b7f0e-134">覆寫與要安裝的命令同名的現有命令。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-134">Overwrites existing commands that have the same name as commands being installed.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7f0e-135">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="b7f0e-135">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="b7f0e-136">允許將標示為發行前版本的套件卸載。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-136">Allows packages marked as prerelease to be uninstalled.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7f0e-137">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="b7f0e-137">-AllVersions</span></span>

<span data-ttu-id="b7f0e-138">指出此 Cmdlet 會卸載所有版本的封裝。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-138">Indicates that this cmdlet uninstalls all versions of the package.</span></span>

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

### <span data-ttu-id="b7f0e-139">-Destination</span><span class="sxs-lookup"><span data-stu-id="b7f0e-139">-Destination</span></span>

<span data-ttu-id="b7f0e-140">指定輸入物件路徑的字串。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-140">Specifies a string of the path to the input object.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7f0e-141">-ExcludeVersion</span><span class="sxs-lookup"><span data-stu-id="b7f0e-141">-ExcludeVersion</span></span>

<span data-ttu-id="b7f0e-142">切換以排除資料夾路徑中的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-142">Switch to exclude the version number in the folder path.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7f0e-143">-Force</span><span class="sxs-lookup"><span data-stu-id="b7f0e-143">-Force</span></span>

<span data-ttu-id="b7f0e-144">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-144">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="b7f0e-145">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="b7f0e-145">-ForceBootstrap</span></span>

<span data-ttu-id="b7f0e-146">強制 **PackageManagement** 自動安裝指定套件的封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-146">Forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="b7f0e-147">-InputObject</span><span class="sxs-lookup"><span data-stu-id="b7f0e-147">-InputObject</span></span>

<span data-ttu-id="b7f0e-148">接受管線輸入，以從 Cmdlet 指定封裝的 **SoftwareIdentity** 物件 `Get-Package` 。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-148">Accepts pipeline input that specifies the package's **SoftwareIdentity** object from the `Get-Package` cmdlet.</span></span> <span data-ttu-id="b7f0e-149">**InputObject** 接受 **SoftwareIdentity** 物件做為 `Get-Package` 值或包含物件的變數。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-149">**InputObject** accepts the **SoftwareIdentity** object as a `Get-Package` value or a variable that contains the object.</span></span>

```yaml
Type: Microsoft.PackageManagement.Packaging.SoftwareIdentity[]
Parameter Sets: PackageByInputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b7f0e-150">-InstallUpdate</span><span class="sxs-lookup"><span data-stu-id="b7f0e-150">-InstallUpdate</span></span>

<span data-ttu-id="b7f0e-151">指出 `Uninstall-Package` 卸載更新。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-151">Indicates that `Uninstall-Package` uninstalls updates.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7f0e-152">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="b7f0e-152">-MaximumVersion</span></span>

<span data-ttu-id="b7f0e-153">指定您想要卸載的最大允許套件版本。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-153">Specifies the maximum allowed package version that you want to uninstall.</span></span> <span data-ttu-id="b7f0e-154">如果您未指定此參數，則會 `Uninstall-Package` 卸載封裝的最新版本。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-154">If you don't specify this parameter, `Uninstall-Package` uninstalls the package's newest version.</span></span>

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7f0e-155">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="b7f0e-155">-MinimumVersion</span></span>

<span data-ttu-id="b7f0e-156">指定您想要卸載的最小允許套件版本。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-156">Specifies the minimum allowed package version that you want to uninstall.</span></span> <span data-ttu-id="b7f0e-157">如果您未新增此參數，則會 `Uninstall-Package` 卸載封裝的最新版本，以滿足 **MaximumVersion** 參數所指定的任何版本。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-157">If you don't add this parameter, `Uninstall-Package` uninstalls the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7f0e-158">-Name</span><span class="sxs-lookup"><span data-stu-id="b7f0e-158">-Name</span></span>

<span data-ttu-id="b7f0e-159">指定一或多個封裝名稱。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-159">Specifies one or more package names.</span></span> <span data-ttu-id="b7f0e-160">多個封裝名稱必須以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-160">Multiple package names must be separated by commas.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7f0e-161">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="b7f0e-161">-NoPathUpdate</span></span>

<span data-ttu-id="b7f0e-162">**NoPathUpdate** 僅適用于 `Install-Script` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-162">**NoPathUpdate** only applies to the `Install-Script` cmdlet.</span></span> <span data-ttu-id="b7f0e-163">**NoPathUpdate** 是提供者所加入的動態參數，而且不受支援 `Uninstall-Package` 。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-163">**NoPathUpdate** is a dynamic parameter added by the provider and isn't supported by `Uninstall-Package`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7f0e-164">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="b7f0e-164">-PackageManagementProvider</span></span>

<span data-ttu-id="b7f0e-165">指定 **PackageManagement** 提供者。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-165">Specifies the **PackageManagement** provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7f0e-166">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="b7f0e-166">-ProviderName</span></span>

<span data-ttu-id="b7f0e-167">指定要搜尋封裝的一或多個封裝提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-167">Specifies one or more package provider names to search for packages.</span></span> <span data-ttu-id="b7f0e-168">您可以執行 `Get-PackageProvider` 來取得套件提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-168">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b7f0e-169">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="b7f0e-169">-RequiredVersion</span></span>

<span data-ttu-id="b7f0e-170">指定您想要卸載之套件的確切允許版本。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-170">Specifies the exact allowed version of the package that you want to uninstall.</span></span> <span data-ttu-id="b7f0e-171">如果您未新增此參數，則會 `Uninstall-Package` 卸載封裝的最新版本，以滿足 **MaximumVersion** 參數所指定的任何版本。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-171">If you don't add this parameter, `Uninstall-Package` uninstalls the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7f0e-172">-Scope</span><span class="sxs-lookup"><span data-stu-id="b7f0e-172">-Scope</span></span>

<span data-ttu-id="b7f0e-173">指定要將封裝卸載的範圍。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-173">Specifies the scope for which to uninstall the package.</span></span> <span data-ttu-id="b7f0e-174">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="b7f0e-174">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="b7f0e-175">CurrentUser</span><span class="sxs-lookup"><span data-stu-id="b7f0e-175">CurrentUser</span></span>
- <span data-ttu-id="b7f0e-176">AllUsers</span><span class="sxs-lookup"><span data-stu-id="b7f0e-176">AllUsers</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch, PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7f0e-177">-SkipDependencies</span><span class="sxs-lookup"><span data-stu-id="b7f0e-177">-SkipDependencies</span></span>

<span data-ttu-id="b7f0e-178">略過卸載軟體相依性。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-178">Skips the uninstallation of software dependencies.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7f0e-179">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="b7f0e-179">-SkipPublisherCheck</span></span>

<span data-ttu-id="b7f0e-180">可讓您取得比已安裝版本還新的套件版本。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-180">Allows you to get a package version that is newer than your installed version.</span></span> <span data-ttu-id="b7f0e-181">例如，已安裝的套件已由受信任的發行者進行數位簽署，但新版本未經過數位簽署。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-181">For example, an installed package that is digitally signed by a trusted publisher but a new version isn't digitally signed.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7f0e-182">-Type</span><span class="sxs-lookup"><span data-stu-id="b7f0e-182">-Type</span></span>

<span data-ttu-id="b7f0e-183">指定是否要使用模組、腳本或兩者來搜尋封裝。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-183">Specifies whether to search for packages with a module, a script, or both.</span></span> <span data-ttu-id="b7f0e-184">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="b7f0e-184">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="b7f0e-185">模組</span><span class="sxs-lookup"><span data-stu-id="b7f0e-185">Module</span></span>
- <span data-ttu-id="b7f0e-186">指令碼</span><span class="sxs-lookup"><span data-stu-id="b7f0e-186">Script</span></span>
- <span data-ttu-id="b7f0e-187">全部</span><span class="sxs-lookup"><span data-stu-id="b7f0e-187">All</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:
Accepted values: Module, Script, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7f0e-188">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b7f0e-188">-Confirm</span></span>

<span data-ttu-id="b7f0e-189">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-189">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b7f0e-190">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b7f0e-190">-WhatIf</span></span>

<span data-ttu-id="b7f0e-191">顯示執行 Cmdlet 時會發生 `Uninstall-Package` 的情況。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-191">Shows what would happen if `Uninstall-Package` cmdlet is run.</span></span> <span data-ttu-id="b7f0e-192">不會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-192">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="b7f0e-193">-AdditionalArguments</span><span class="sxs-lookup"><span data-stu-id="b7f0e-193">-AdditionalArguments</span></span>

<span data-ttu-id="b7f0e-194">指定其他引數。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-194">Specifies additional arguments.</span></span>

```yaml
Type: System.String[]
Parameter Sets: msi:PackageByInputObject, msi:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7f0e-195">-IncludeSystemComponent</span><span class="sxs-lookup"><span data-stu-id="b7f0e-195">-IncludeSystemComponent</span></span>

<span data-ttu-id="b7f0e-196">指定此 Cmdlet 會卸載系統元件。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-196">Specifies that this cmdlet uninstalls system components.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Programs:PackageByInputObject, Programs:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7f0e-197">-IncludeWindowsInstaller</span><span class="sxs-lookup"><span data-stu-id="b7f0e-197">-IncludeWindowsInstaller</span></span>

<span data-ttu-id="b7f0e-198">指出此 Cmdlet 會透過 Windows Installer 卸載套件。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-198">Indicates that this cmdlet uninstalls the package through Windows Installer.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Programs:PackageByInputObject, Programs:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7f0e-199">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b7f0e-199">CommonParameters</span></span>

<span data-ttu-id="b7f0e-200">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-200">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b7f0e-201">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-201">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b7f0e-202">輸入</span><span class="sxs-lookup"><span data-stu-id="b7f0e-202">INPUTS</span></span>

### <span data-ttu-id="b7f0e-203">`Uninstall-Package` 接受來自管線的 **SoftwareIdentity** 物件做為輸入。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-203">`Uninstall-Package` accepts **SoftwareIdentity** objects from the pipeline as input.</span></span>

## <span data-ttu-id="b7f0e-204">輸出</span><span class="sxs-lookup"><span data-stu-id="b7f0e-204">OUTPUTS</span></span>

### <span data-ttu-id="b7f0e-205">`Uninstall-Package` 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-205">`Uninstall-Package` doesn't generate any output.</span></span>

## <span data-ttu-id="b7f0e-206">注意</span><span class="sxs-lookup"><span data-stu-id="b7f0e-206">NOTES</span></span>

<span data-ttu-id="b7f0e-207">在命令中包含封裝提供者可以讓 Cmdlet 提供動態參數。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-207">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="b7f0e-208">動態參數是封裝提供者專用的。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-208">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="b7f0e-209">此 `Get-Help` Cmdlet 會列出 Cmdlet 的參數集，並包含提供者的參數集。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-209">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span> <span data-ttu-id="b7f0e-210">例如， `Uninstall-Package` 具有 **PowerShellGet** 參數集，其中包含 `-NoPathUpdate` 、 `AllowClobber` 和 `SkipPublisherCheck` 。</span><span class="sxs-lookup"><span data-stu-id="b7f0e-210">For example, `Uninstall-Package` has the **PowerShellGet** parameter set that includes `-NoPathUpdate`, `AllowClobber`, and `SkipPublisherCheck`.</span></span>

## <span data-ttu-id="b7f0e-211">相關連結</span><span class="sxs-lookup"><span data-stu-id="b7f0e-211">RELATED LINKS</span></span>

[<span data-ttu-id="b7f0e-212">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="b7f0e-212">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="b7f0e-213">Find-Package</span><span class="sxs-lookup"><span data-stu-id="b7f0e-213">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="b7f0e-214">Get-Package</span><span class="sxs-lookup"><span data-stu-id="b7f0e-214">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="b7f0e-215">Install-Package</span><span class="sxs-lookup"><span data-stu-id="b7f0e-215">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="b7f0e-216">Save-Package</span><span class="sxs-lookup"><span data-stu-id="b7f0e-216">Save-Package</span></span>](Save-Package.md)
