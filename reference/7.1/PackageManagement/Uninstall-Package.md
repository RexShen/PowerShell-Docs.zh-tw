---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 05/24/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/uninstall-package?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Package
ms.openlocfilehash: 4da97d9643483db0eae4fc7d34e0e6997d16bd04
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204171"
---
# <span data-ttu-id="2dab2-103">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="2dab2-103">Uninstall-Package</span></span>

## <span data-ttu-id="2dab2-104">概要</span><span class="sxs-lookup"><span data-stu-id="2dab2-104">SYNOPSIS</span></span>
<span data-ttu-id="2dab2-105">卸載一或多個軟體套件。</span><span class="sxs-lookup"><span data-stu-id="2dab2-105">Uninstalls one or more software packages.</span></span>

## <span data-ttu-id="2dab2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2dab2-106">SYNTAX</span></span>

### <span data-ttu-id="2dab2-107">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="2dab2-107">PackageByInputObject</span></span>

```
Uninstall-Package [-InputObject] <SoftwareIdentity[]> [-AllVersions] [-Force] [-ForceBootstrap]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2dab2-108">PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="2dab2-108">PackageBySearch</span></span>

```
Uninstall-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="2dab2-109">NuGet： PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="2dab2-109">NuGet:PackageByInputObject</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### <span data-ttu-id="2dab2-110">NuGet： PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="2dab2-110">NuGet:PackageBySearch</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### <span data-ttu-id="2dab2-111">PowerShellGet： PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="2dab2-111">PowerShellGet:PackageByInputObject</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-Scope <String>]
 [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber] [-SkipPublisherCheck]
 [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="2dab2-112">PowerShellGet： PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="2dab2-112">PowerShellGet:PackageBySearch</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-Scope <String>]
 [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber] [-SkipPublisherCheck]
 [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions] [<CommonParameters>]
```

## <span data-ttu-id="2dab2-113">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="2dab2-113">DESCRIPTION</span></span>

<span data-ttu-id="2dab2-114">`Uninstall-Package`Cmdlet 會從本機電腦卸載一或多個軟體套件。</span><span class="sxs-lookup"><span data-stu-id="2dab2-114">The `Uninstall-Package` cmdlet uninstalls one or more software packages from the local computer.</span></span> <span data-ttu-id="2dab2-115">若要尋找已安裝的套件，請使用 `Get-Package` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2dab2-115">To find installed packages, use the `Get-Package` cmdlet.</span></span>

## <span data-ttu-id="2dab2-116">範例</span><span class="sxs-lookup"><span data-stu-id="2dab2-116">EXAMPLES</span></span>

### <span data-ttu-id="2dab2-117">範例1：卸載套件</span><span class="sxs-lookup"><span data-stu-id="2dab2-117">Example 1: Uninstall a package</span></span>

<span data-ttu-id="2dab2-118">`Uninstall-Package`Cmdlet 會卸載套件。</span><span class="sxs-lookup"><span data-stu-id="2dab2-118">The `Uninstall-Package` cmdlet uninstalls packages.</span></span> <span data-ttu-id="2dab2-119">**Name** 參數指定要卸載的封裝。</span><span class="sxs-lookup"><span data-stu-id="2dab2-119">The **Name** parameter specifies the package to uninstall.</span></span> <span data-ttu-id="2dab2-120">如果安裝了多個版本的封裝，則會卸載最新版本。</span><span class="sxs-lookup"><span data-stu-id="2dab2-120">If multiple versions of a package are installed, the newest version is uninstalled.</span></span>

```
PS> Uninstall-Package -Name NuGet.Core
```

### <span data-ttu-id="2dab2-121">範例2：使用管線卸載套件</span><span class="sxs-lookup"><span data-stu-id="2dab2-121">Example 2: Use the pipeline to uninstall a package</span></span>

<span data-ttu-id="2dab2-122">`Get-Package` 找出特定的封裝，並將 **SoftwareIdentity** 物件沿著管線向下傳送至 `Uninsall-Package` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2dab2-122">`Get-Package` locates a specific package and sends the **SoftwareIdentity** object down the pipeline to the `Uninsall-Package` cmdlet.</span></span>

```
PS> Get-Package -Name NuGet.Core -RequiredVersion 2.14.0 | Uninstall-Package
```

<span data-ttu-id="2dab2-123">此 `Get-Package` Cmdlet 會使用 **Name** 和 **RequiredVersion** 參數來指定封裝。</span><span class="sxs-lookup"><span data-stu-id="2dab2-123">The `Get-Package` cmdlet uses the **Name** and **RequiredVersion** parameters to specify a package.</span></span>
<span data-ttu-id="2dab2-124">**SoftwareIdentity** 物件會沿著管線向下傳送。</span><span class="sxs-lookup"><span data-stu-id="2dab2-124">A **SoftwareIdentity** object is sent down the pipeline.</span></span> <span data-ttu-id="2dab2-125">`Uninstall-Package`Cmdlet 會以 **InputObject** 的形式接收物件，並移除封裝。</span><span class="sxs-lookup"><span data-stu-id="2dab2-125">The `Uninstall-Package` cmdlet receives the object as an **InputObject** and removes the package.</span></span>

<span data-ttu-id="2dab2-126">或者， `Uninstall-Package` Cmdlet 可以指定 **InputObject** 參數的值：</span><span class="sxs-lookup"><span data-stu-id="2dab2-126">As an alternative, the `Uninstall-Package` cmdlet can specify a value for the **InputObject** parameter:</span></span>

`Uninstall-Package -InputObject ( Get-Package -Name NuGet.Core -RequiredVersion 2.14.0 )`

## <span data-ttu-id="2dab2-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2dab2-127">PARAMETERS</span></span>

### <span data-ttu-id="2dab2-128">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="2dab2-128">-AllowClobber</span></span>

<span data-ttu-id="2dab2-129">覆寫與現有命令衝突的警告訊息。</span><span class="sxs-lookup"><span data-stu-id="2dab2-129">Overrides warning messages about conflicts with existing commands.</span></span> <span data-ttu-id="2dab2-130">覆寫與要安裝的命令同名的現有命令。</span><span class="sxs-lookup"><span data-stu-id="2dab2-130">Overwrites existing commands that have the same name as commands being installed.</span></span>

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

### <span data-ttu-id="2dab2-131">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="2dab2-131">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="2dab2-132">允許將標示為發行前版本的套件卸載。</span><span class="sxs-lookup"><span data-stu-id="2dab2-132">Allows packages marked as prerelease to be uninstalled.</span></span>

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

### <span data-ttu-id="2dab2-133">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="2dab2-133">-AllVersions</span></span>

<span data-ttu-id="2dab2-134">指出此 Cmdlet 會卸載所有版本的封裝。</span><span class="sxs-lookup"><span data-stu-id="2dab2-134">Indicates that this cmdlet uninstalls all versions of the package.</span></span>

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

### <span data-ttu-id="2dab2-135">-Destination</span><span class="sxs-lookup"><span data-stu-id="2dab2-135">-Destination</span></span>

<span data-ttu-id="2dab2-136">指定輸入物件路徑的字串。</span><span class="sxs-lookup"><span data-stu-id="2dab2-136">Specifies a string of the path to the input object.</span></span>

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

### <span data-ttu-id="2dab2-137">-ExcludeVersion</span><span class="sxs-lookup"><span data-stu-id="2dab2-137">-ExcludeVersion</span></span>

<span data-ttu-id="2dab2-138">切換以排除資料夾路徑中的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="2dab2-138">Switch to exclude the version number in the folder path.</span></span>

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

### <span data-ttu-id="2dab2-139">-Force</span><span class="sxs-lookup"><span data-stu-id="2dab2-139">-Force</span></span>

<span data-ttu-id="2dab2-140">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="2dab2-140">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="2dab2-141">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="2dab2-141">-ForceBootstrap</span></span>

<span data-ttu-id="2dab2-142">強制 **PackageManagement** 自動安裝指定套件的封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="2dab2-142">Forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="2dab2-143">-InputObject</span><span class="sxs-lookup"><span data-stu-id="2dab2-143">-InputObject</span></span>

<span data-ttu-id="2dab2-144">接受管線輸入，以從 Cmdlet 指定封裝的 **SoftwareIdentity** 物件 `Get-Package` 。</span><span class="sxs-lookup"><span data-stu-id="2dab2-144">Accepts pipeline input that specifies the package's **SoftwareIdentity** object from the `Get-Package` cmdlet.</span></span> <span data-ttu-id="2dab2-145">**InputObject** 接受 **SoftwareIdentity** 物件做為 `Get-Package` 值或包含物件的變數。</span><span class="sxs-lookup"><span data-stu-id="2dab2-145">**InputObject** accepts the **SoftwareIdentity** object as a `Get-Package` value or a variable that contains the object.</span></span>

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

### <span data-ttu-id="2dab2-146">-InstallUpdate</span><span class="sxs-lookup"><span data-stu-id="2dab2-146">-InstallUpdate</span></span>

<span data-ttu-id="2dab2-147">指出 `Uninstall-Package` 卸載更新。</span><span class="sxs-lookup"><span data-stu-id="2dab2-147">Indicates that `Uninstall-Package` uninstalls updates.</span></span>

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

### <span data-ttu-id="2dab2-148">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="2dab2-148">-MaximumVersion</span></span>

<span data-ttu-id="2dab2-149">指定您想要卸載的最大允許套件版本。</span><span class="sxs-lookup"><span data-stu-id="2dab2-149">Specifies the maximum allowed package version that you want to uninstall.</span></span> <span data-ttu-id="2dab2-150">如果您未指定此參數，則會 `Uninstall-Package` 卸載封裝的最新版本。</span><span class="sxs-lookup"><span data-stu-id="2dab2-150">If you don't specify this parameter, `Uninstall-Package` uninstalls the package's newest version.</span></span>

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

### <span data-ttu-id="2dab2-151">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="2dab2-151">-MinimumVersion</span></span>

<span data-ttu-id="2dab2-152">指定您想要卸載的最小允許套件版本。</span><span class="sxs-lookup"><span data-stu-id="2dab2-152">Specifies the minimum allowed package version that you want to uninstall.</span></span> <span data-ttu-id="2dab2-153">如果您未新增此參數，則會 `Uninstall-Package` 卸載封裝的最新版本，以滿足 **MaximumVersion** 參數所指定的任何版本。</span><span class="sxs-lookup"><span data-stu-id="2dab2-153">If you don't add this parameter, `Uninstall-Package` uninstalls the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="2dab2-154">-Name</span><span class="sxs-lookup"><span data-stu-id="2dab2-154">-Name</span></span>

<span data-ttu-id="2dab2-155">指定一或多個封裝名稱。</span><span class="sxs-lookup"><span data-stu-id="2dab2-155">Specifies one or more package names.</span></span> <span data-ttu-id="2dab2-156">多個封裝名稱必須以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="2dab2-156">Multiple package names must be separated by commas.</span></span>

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

### <span data-ttu-id="2dab2-157">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="2dab2-157">-NoPathUpdate</span></span>

<span data-ttu-id="2dab2-158">**NoPathUpdate** 僅適用于 `Install-Script` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2dab2-158">**NoPathUpdate** only applies to the `Install-Script` cmdlet.</span></span> <span data-ttu-id="2dab2-159">**NoPathUpdate** 是提供者所加入的動態參數，而且不受支援 `Uninstall-Package` 。</span><span class="sxs-lookup"><span data-stu-id="2dab2-159">**NoPathUpdate** is a dynamic parameter added by the provider and isn't supported by `Uninstall-Package`.</span></span>

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

### <span data-ttu-id="2dab2-160">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="2dab2-160">-PackageManagementProvider</span></span>

<span data-ttu-id="2dab2-161">指定 **PackageManagement** 提供者。</span><span class="sxs-lookup"><span data-stu-id="2dab2-161">Specifies the **PackageManagement** provider.</span></span>

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

### <span data-ttu-id="2dab2-162">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="2dab2-162">-ProviderName</span></span>

<span data-ttu-id="2dab2-163">指定要搜尋封裝的一或多個封裝提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="2dab2-163">Specifies one or more package provider names to search for packages.</span></span> <span data-ttu-id="2dab2-164">您可以執行 `Get-PackageProvider` 來取得套件提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="2dab2-164">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>

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

### <span data-ttu-id="2dab2-165">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="2dab2-165">-RequiredVersion</span></span>

<span data-ttu-id="2dab2-166">指定您想要卸載之套件的確切允許版本。</span><span class="sxs-lookup"><span data-stu-id="2dab2-166">Specifies the exact allowed version of the package that you want to uninstall.</span></span> <span data-ttu-id="2dab2-167">如果您未新增此參數，則會 `Uninstall-Package` 卸載封裝的最新版本，以滿足 **MaximumVersion** 參數所指定的任何版本。</span><span class="sxs-lookup"><span data-stu-id="2dab2-167">If you don't add this parameter, `Uninstall-Package` uninstalls the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="2dab2-168">-Scope</span><span class="sxs-lookup"><span data-stu-id="2dab2-168">-Scope</span></span>

<span data-ttu-id="2dab2-169">指定要將封裝卸載的範圍。</span><span class="sxs-lookup"><span data-stu-id="2dab2-169">Specifies the scope for which to uninstall the package.</span></span> <span data-ttu-id="2dab2-170">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="2dab2-170">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="2dab2-171">CurrentUser</span><span class="sxs-lookup"><span data-stu-id="2dab2-171">CurrentUser</span></span>
- <span data-ttu-id="2dab2-172">AllUsers</span><span class="sxs-lookup"><span data-stu-id="2dab2-172">AllUsers</span></span>

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

### <span data-ttu-id="2dab2-173">-SkipDependencies</span><span class="sxs-lookup"><span data-stu-id="2dab2-173">-SkipDependencies</span></span>

<span data-ttu-id="2dab2-174">略過卸載軟體相依性。</span><span class="sxs-lookup"><span data-stu-id="2dab2-174">Skips the uninstallation of software dependencies.</span></span>

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

### <span data-ttu-id="2dab2-175">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="2dab2-175">-SkipPublisherCheck</span></span>

<span data-ttu-id="2dab2-176">可讓您取得比已安裝版本還新的套件版本。</span><span class="sxs-lookup"><span data-stu-id="2dab2-176">Allows you to get a package version that is newer than your installed version.</span></span> <span data-ttu-id="2dab2-177">例如，已安裝的套件已由受信任的發行者進行數位簽署，但新版本未經過數位簽署。</span><span class="sxs-lookup"><span data-stu-id="2dab2-177">For example, an installed package that is digitally signed by a trusted publisher but a new version isn't digitally signed.</span></span>

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

### <span data-ttu-id="2dab2-178">-Type</span><span class="sxs-lookup"><span data-stu-id="2dab2-178">-Type</span></span>

<span data-ttu-id="2dab2-179">指定是否要使用模組、腳本或兩者來搜尋封裝。</span><span class="sxs-lookup"><span data-stu-id="2dab2-179">Specifies whether to search for packages with a module, a script, or both.</span></span> <span data-ttu-id="2dab2-180">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="2dab2-180">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="2dab2-181">模組</span><span class="sxs-lookup"><span data-stu-id="2dab2-181">Module</span></span>
- <span data-ttu-id="2dab2-182">指令碼</span><span class="sxs-lookup"><span data-stu-id="2dab2-182">Script</span></span>
- <span data-ttu-id="2dab2-183">全部</span><span class="sxs-lookup"><span data-stu-id="2dab2-183">All</span></span>

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

### <span data-ttu-id="2dab2-184">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2dab2-184">-Confirm</span></span>

<span data-ttu-id="2dab2-185">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="2dab2-185">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="2dab2-186">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2dab2-186">-WhatIf</span></span>

<span data-ttu-id="2dab2-187">顯示執行 Cmdlet 時會發生 `Uninstall-Package` 的情況。</span><span class="sxs-lookup"><span data-stu-id="2dab2-187">Shows what would happen if `Uninstall-Package` cmdlet is run.</span></span> <span data-ttu-id="2dab2-188">不會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2dab2-188">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="2dab2-189">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2dab2-189">CommonParameters</span></span>

<span data-ttu-id="2dab2-190">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="2dab2-190">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2dab2-191">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="2dab2-191">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2dab2-192">輸入</span><span class="sxs-lookup"><span data-stu-id="2dab2-192">INPUTS</span></span>

### <span data-ttu-id="2dab2-193">`Uninstall-Package` 接受來自管線的 **SoftwareIdentity** 物件做為輸入。</span><span class="sxs-lookup"><span data-stu-id="2dab2-193">`Uninstall-Package` accepts **SoftwareIdentity** objects from the pipeline as input.</span></span>

## <span data-ttu-id="2dab2-194">輸出</span><span class="sxs-lookup"><span data-stu-id="2dab2-194">OUTPUTS</span></span>

### <span data-ttu-id="2dab2-195">`Uninstall-Package` 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="2dab2-195">`Uninstall-Package` doesn't generate any output.</span></span>

## <span data-ttu-id="2dab2-196">注意</span><span class="sxs-lookup"><span data-stu-id="2dab2-196">NOTES</span></span>

<span data-ttu-id="2dab2-197">在命令中包含封裝提供者可以讓 Cmdlet 提供動態參數。</span><span class="sxs-lookup"><span data-stu-id="2dab2-197">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="2dab2-198">動態參數是封裝提供者專用的。</span><span class="sxs-lookup"><span data-stu-id="2dab2-198">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="2dab2-199">此 `Get-Help` Cmdlet 會列出 Cmdlet 的參數集，並包含提供者的參數集。</span><span class="sxs-lookup"><span data-stu-id="2dab2-199">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span> <span data-ttu-id="2dab2-200">例如， `Uninstall-Package` 具有 **PowerShellGet** 參數集，其中包含 `-NoPathUpdate` 、 `AllowClobber` 和 `SkipPublisherCheck` 。</span><span class="sxs-lookup"><span data-stu-id="2dab2-200">For example, `Uninstall-Package` has the **PowerShellGet** parameter set that includes `-NoPathUpdate`, `AllowClobber`, and `SkipPublisherCheck`.</span></span>

## <span data-ttu-id="2dab2-201">相關連結</span><span class="sxs-lookup"><span data-stu-id="2dab2-201">RELATED LINKS</span></span>

[<span data-ttu-id="2dab2-202">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="2dab2-202">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="2dab2-203">Find-Package</span><span class="sxs-lookup"><span data-stu-id="2dab2-203">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="2dab2-204">Get-Package</span><span class="sxs-lookup"><span data-stu-id="2dab2-204">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="2dab2-205">Install-Package</span><span class="sxs-lookup"><span data-stu-id="2dab2-205">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="2dab2-206">Save-Package</span><span class="sxs-lookup"><span data-stu-id="2dab2-206">Save-Package</span></span>](Save-Package.md)

