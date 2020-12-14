---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 04/03/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/save-package?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Package
ms.openlocfilehash: f756c294c9a40170a94f9a35b8909cf164616bea
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891729"
---
# <span data-ttu-id="27489-103">Save-Package</span><span class="sxs-lookup"><span data-stu-id="27489-103">Save-Package</span></span>

## <span data-ttu-id="27489-104">概要</span><span class="sxs-lookup"><span data-stu-id="27489-104">SYNOPSIS</span></span>
<span data-ttu-id="27489-105">將封裝儲存到本機電腦，而不進行安裝。</span><span class="sxs-lookup"><span data-stu-id="27489-105">Saves packages to the local computer without installing them.</span></span>

## <span data-ttu-id="27489-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="27489-106">SYNTAX</span></span>

### <span data-ttu-id="27489-107">PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="27489-107">PackageBySearch</span></span>

```
Save-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Source <String[]>] [-Path <String>] [-LiteralPath <String>]
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllVersions]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="27489-108">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="27489-108">PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] -InputObject <SoftwareIdentity>
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllVersions]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="27489-109">NuGet： PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="27489-109">NuGet:PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ConfigFile <String>] [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>]
 [-Contains <String>] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="27489-110">NuGet</span><span class="sxs-lookup"><span data-stu-id="27489-110">NuGet</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ConfigFile <String>] [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>]
 [-Contains <String>] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="27489-111">PowerShellGet： PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="27489-111">PowerShellGet:PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-AllowPrereleaseVersions] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [<CommonParameters>]
```

### <span data-ttu-id="27489-112">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="27489-112">PowerShellGet</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-AllowPrereleaseVersions] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [<CommonParameters>]
```

## <span data-ttu-id="27489-113">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="27489-113">DESCRIPTION</span></span>

<span data-ttu-id="27489-114">`Save-Package`Cmdlet 會將套件儲存至本機電腦，但不會安裝套件。</span><span class="sxs-lookup"><span data-stu-id="27489-114">The `Save-Package` cmdlet saves packages to the local computer but doesn't install the packages.</span></span>
<span data-ttu-id="27489-115">除非您指定 **RequiredVerion**，否則此 Cmdlet 會儲存套件的最新版本。</span><span class="sxs-lookup"><span data-stu-id="27489-115">This cmdlet saves the newest version of a package unless you specify a **RequiredVerion**.</span></span> <span data-ttu-id="27489-116">**Path** 和 **LiteralPath** 參數彼此互斥，而且無法加入至相同的命令。</span><span class="sxs-lookup"><span data-stu-id="27489-116">The **Path** and **LiteralPath** parameters are mutually exclusive, and cannot be added to the same command.</span></span>

## <span data-ttu-id="27489-117">範例</span><span class="sxs-lookup"><span data-stu-id="27489-117">EXAMPLES</span></span>

### <span data-ttu-id="27489-118">範例1：將封裝儲存至本機電腦</span><span class="sxs-lookup"><span data-stu-id="27489-118">Example 1: Save a package to the local computer</span></span>

<span data-ttu-id="27489-119">此範例會將最新版本的封裝儲存到本機電腦上的目錄。</span><span class="sxs-lookup"><span data-stu-id="27489-119">This example saves the newest version of the package to a directory on the local computer.</span></span> <span data-ttu-id="27489-120">套件的相依性會與套件一起下載。</span><span class="sxs-lookup"><span data-stu-id="27489-120">The package's dependencies are download with the package.</span></span>

```
PS> Save-Package -Name NuGet.Core -ProviderName NuGet -Path C:\LocalPkg
```

```Output
Name                    Version    Source    Summary
----                    -------    ------    -------
Microsoft.Web.Xdt       3.0.0      Nuget     Microsoft Xml Document Transformation (XDT) enables...
NuGet.Core              2.14.0     Nuget     NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="27489-121">`Save-Package` 使用 **Name** 參數來指定封裝。</span><span class="sxs-lookup"><span data-stu-id="27489-121">`Save-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="27489-122">封裝是從 **ProviderName** 參數所指定的存放庫下載。</span><span class="sxs-lookup"><span data-stu-id="27489-122">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="27489-123">**Path** 參數會決定封裝的儲存位置。</span><span class="sxs-lookup"><span data-stu-id="27489-123">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="27489-124">範例2：儲存特定套件版本</span><span class="sxs-lookup"><span data-stu-id="27489-124">Example 2: Save a specific package version</span></span>

<span data-ttu-id="27489-125">此範例會指定套件版本，並將其儲存至本機電腦上的目錄。</span><span class="sxs-lookup"><span data-stu-id="27489-125">This example specifies the package version and saves it to a directory on the local computer.</span></span>

```
PS> Save-Package -Name NuGet.Core -RequiredVersion 2.9.0 -ProviderName NuGet -Path C:\LocalPkg
```

```Output
Name                    Version    Source    Summary
----                    -------    ------    -------
Microsoft.Web.Xdt       3.0.0      Nuget     Microsoft Xml Document Transformation (XDT) enables...
NuGet.Core              2.9.0      Nuget     NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="27489-126">`Save-Package` 使用 **Name** 參數來指定封裝。</span><span class="sxs-lookup"><span data-stu-id="27489-126">`Save-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="27489-127">**RequiredVersion** 表示特定套件版本。</span><span class="sxs-lookup"><span data-stu-id="27489-127">**RequiredVersion** indicates a specific package version.</span></span> <span data-ttu-id="27489-128">封裝是從 **ProviderName** 參數所指定的存放庫下載。</span><span class="sxs-lookup"><span data-stu-id="27489-128">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="27489-129">**Path** 參數會決定封裝的儲存位置。</span><span class="sxs-lookup"><span data-stu-id="27489-129">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="27489-130">範例3：使用 Find-Package 儲存封裝</span><span class="sxs-lookup"><span data-stu-id="27489-130">Example 3: Use Find-Package to save a package</span></span>

<span data-ttu-id="27489-131">此命令會使用 `Find-Package` 找出封裝的最新版本，並將物件傳送至 `Save-Package` 。</span><span class="sxs-lookup"><span data-stu-id="27489-131">This command uses `Find-Package` to locate the newest version of the package and sends the object to `Save-Package`.</span></span>

```
PS> Find-Package -Name NuGet.Core -ProviderName NuGet | Save-Package -Path C:\LocalPkg
```

<span data-ttu-id="27489-132">`Find-Package` 使用 **Name** 參數來指定封裝。</span><span class="sxs-lookup"><span data-stu-id="27489-132">`Find-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="27489-133">封裝是從 **ProviderName** 參數所指定的存放庫下載。</span><span class="sxs-lookup"><span data-stu-id="27489-133">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="27489-134">物件會向下傳送到管線 `Save-Package` 。</span><span class="sxs-lookup"><span data-stu-id="27489-134">The object is sent down the pipeline to `Save-Package`.</span></span> <span data-ttu-id="27489-135">**Path** 參數會決定封裝的儲存位置。</span><span class="sxs-lookup"><span data-stu-id="27489-135">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="27489-136">範例4：儲存並安裝封裝</span><span class="sxs-lookup"><span data-stu-id="27489-136">Example 4: Save and install the package</span></span>

<span data-ttu-id="27489-137">封裝的最新版本和其相依性會下載並安裝在本機電腦上。</span><span class="sxs-lookup"><span data-stu-id="27489-137">The newest version of the package and its dependencies are downloaded and installed on the local computer.</span></span>

```
PS> Save-Package -Name NuGet.Core -ProviderName NuGet -Path C:\LocalPkg
PS> Install-Package C:\LocalPkg\NuGet.Core.2.14.0.nupkg
```

<span data-ttu-id="27489-138">`Save-Package` 將封裝檔案及其相依性下載到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="27489-138">`Save-Package` downloads the package file and its dependencies to the local computer.</span></span>
<span data-ttu-id="27489-139">`Install-Package` 從指定的目錄安裝封裝和相依性。</span><span class="sxs-lookup"><span data-stu-id="27489-139">`Install-Package` installs the package and dependencies from the specified directory.</span></span>

## <span data-ttu-id="27489-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="27489-140">PARAMETERS</span></span>

### <span data-ttu-id="27489-141">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="27489-141">-AcceptLicense</span></span>

<span data-ttu-id="27489-142">如果套件需要，則會在安裝期間自動接受授權合約。</span><span class="sxs-lookup"><span data-stu-id="27489-142">Automatically accept the license agreement during installation if the package requires it.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27489-143">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="27489-143">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="27489-144">允許儲存標記為發行前版本的套件。</span><span class="sxs-lookup"><span data-stu-id="27489-144">Allows packages marked as Prerelease to be saved.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageByInputObject, NuGet, PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27489-145">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="27489-145">-AllVersions</span></span>

<span data-ttu-id="27489-146">指出此 Cmdlet 會儲存套件的所有可用版本。</span><span class="sxs-lookup"><span data-stu-id="27489-146">Indicates that this cmdlet saves all available versions of the package.</span></span>

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

### <span data-ttu-id="27489-147">-Command</span><span class="sxs-lookup"><span data-stu-id="27489-147">-Command</span></span>

<span data-ttu-id="27489-148">指定封裝中包含的一或多個命令。</span><span class="sxs-lookup"><span data-stu-id="27489-148">Specifies one or more commands included in the package.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27489-149">-Read-configfile</span><span class="sxs-lookup"><span data-stu-id="27489-149">-ConfigFile</span></span>

<span data-ttu-id="27489-150">指定設定檔。</span><span class="sxs-lookup"><span data-stu-id="27489-150">Specifies a configuration File.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27489-151">-Contains</span><span class="sxs-lookup"><span data-stu-id="27489-151">-Contains</span></span>

<span data-ttu-id="27489-152">`Save-Package` 如果物件的屬性值中有任何專案與指定的值完全相符，就會取得物件。</span><span class="sxs-lookup"><span data-stu-id="27489-152">`Save-Package` gets objects if any item in the object's property values are an exact match for the specified value.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27489-153">-Credential</span><span class="sxs-lookup"><span data-stu-id="27489-153">-Credential</span></span>

<span data-ttu-id="27489-154">指定有許可權可從指定的封裝提供者或來源儲存封裝的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="27489-154">Specifies a user account that has permission to save a package from a specified package provider or source.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27489-155">-DscResource</span><span class="sxs-lookup"><span data-stu-id="27489-155">-DscResource</span></span>

<span data-ttu-id="27489-156">指定封裝的一或多個 Desired State Configuration (DSC) 資源。</span><span class="sxs-lookup"><span data-stu-id="27489-156">Specifies one or more Desired State Configuration (DSC) resources for the package.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27489-157">-Filter</span><span class="sxs-lookup"><span data-stu-id="27489-157">-Filter</span></span>

<span data-ttu-id="27489-158">指定封裝的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="27489-158">Specifies a filter for the package.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27489-159">-FilterOnTag</span><span class="sxs-lookup"><span data-stu-id="27489-159">-FilterOnTag</span></span>

<span data-ttu-id="27489-160">指定篩選結果的標記。</span><span class="sxs-lookup"><span data-stu-id="27489-160">Specifies the tag that filters the results.</span></span> <span data-ttu-id="27489-161">不包含指定標記的結果會被排除。</span><span class="sxs-lookup"><span data-stu-id="27489-161">Results that don't contain the specified tag are excluded.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27489-162">-Force</span><span class="sxs-lookup"><span data-stu-id="27489-162">-Force</span></span>

<span data-ttu-id="27489-163">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="27489-163">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="27489-164">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="27489-164">-ForceBootstrap</span></span>

<span data-ttu-id="27489-165">指出 `Save-Package` 強制 **PackageManagement** 自動安裝指定套件的封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="27489-165">Indicates that `Save-Package` forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="27489-166">-Headers</span><span class="sxs-lookup"><span data-stu-id="27489-166">-Headers</span></span>

<span data-ttu-id="27489-167">指定封裝的標頭。</span><span class="sxs-lookup"><span data-stu-id="27489-167">Specifies the headers for the package.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27489-168">-Include</span><span class="sxs-lookup"><span data-stu-id="27489-168">-Includes</span></span>

<span data-ttu-id="27489-169">指出封裝所包含的資源。</span><span class="sxs-lookup"><span data-stu-id="27489-169">Indicates the resources that the package includes.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:
Accepted values: DscResource, Cmdlet, Function, Workflow, RoleCapability

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27489-170">-InputObject</span><span class="sxs-lookup"><span data-stu-id="27489-170">-InputObject</span></span>

<span data-ttu-id="27489-171">代表您要儲存之封裝的軟體識別碼物件。</span><span class="sxs-lookup"><span data-stu-id="27489-171">A software ID object that represents the package that you want to save.</span></span> <span data-ttu-id="27489-172">軟體識別碼是 Cmdlet 結果的一部分 `Find-Package` 。</span><span class="sxs-lookup"><span data-stu-id="27489-172">Software IDs are part of the results of the `Find-Package` cmdlet.</span></span>

```yaml
Type: Microsoft.PackageManagement.Packaging.SoftwareIdentity
Parameter Sets: PackageByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="27489-173">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="27489-173">-LiteralPath</span></span>

<span data-ttu-id="27489-174">指定您要儲存封裝的常值路徑。</span><span class="sxs-lookup"><span data-stu-id="27489-174">Specifies the literal path to which you want to save the package.</span></span> <span data-ttu-id="27489-175">您無法將此參數和 **Path** 參數同時新增到相同的命令。</span><span class="sxs-lookup"><span data-stu-id="27489-175">You cannot add both this parameter and the **Path** parameter to the same command.</span></span>

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

### <span data-ttu-id="27489-176">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="27489-176">-MaximumVersion</span></span>

<span data-ttu-id="27489-177">指定您要儲存之封裝的最大版本。</span><span class="sxs-lookup"><span data-stu-id="27489-177">Specifies the maximum version of the package that you want to save.</span></span>

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

### <span data-ttu-id="27489-178">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="27489-178">-MinimumVersion</span></span>

<span data-ttu-id="27489-179">指定您想要尋找之封裝的最小版本。</span><span class="sxs-lookup"><span data-stu-id="27489-179">Specifies the minimum version of the package that you want to find.</span></span>

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

### <span data-ttu-id="27489-180">-Name</span><span class="sxs-lookup"><span data-stu-id="27489-180">-Name</span></span>

<span data-ttu-id="27489-181">指定一或多個封裝名稱。</span><span class="sxs-lookup"><span data-stu-id="27489-181">Specifies one or more package names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="27489-182">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="27489-182">-PackageManagementProvider</span></span>

<span data-ttu-id="27489-183">指定套件管理提供者。</span><span class="sxs-lookup"><span data-stu-id="27489-183">Specifies a package management provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27489-184">-Path</span><span class="sxs-lookup"><span data-stu-id="27489-184">-Path</span></span>

<span data-ttu-id="27489-185">指定本機電腦上儲存封裝的位置。</span><span class="sxs-lookup"><span data-stu-id="27489-185">Specifies the location on the local computer to store the package.</span></span>

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

### <span data-ttu-id="27489-186">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="27489-186">-ProviderName</span></span>

<span data-ttu-id="27489-187">指定一或多個提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="27489-187">Specifies one or more provider names.</span></span>

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

### <span data-ttu-id="27489-188">-Proxy</span><span class="sxs-lookup"><span data-stu-id="27489-188">-Proxy</span></span>

<span data-ttu-id="27489-189">為要求指定 proxy 伺服器，而不是直接連線到網際網路資源。</span><span class="sxs-lookup"><span data-stu-id="27489-189">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27489-190">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="27489-190">-ProxyCredential</span></span>

<span data-ttu-id="27489-191">指定具有使用 **Proxy** 參數所指定 Proxy 伺服器之權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="27489-191">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27489-192">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="27489-192">-PublishLocation</span></span>

<span data-ttu-id="27489-193">指定發行位置。</span><span class="sxs-lookup"><span data-stu-id="27489-193">Specifies the publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27489-194">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="27489-194">-RequiredVersion</span></span>

<span data-ttu-id="27489-195">指定要儲存之封裝的確切版本。</span><span class="sxs-lookup"><span data-stu-id="27489-195">Specifies the exact version of the package to save.</span></span>

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

### <span data-ttu-id="27489-196">-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="27489-196">-RoleCapability</span></span>

<span data-ttu-id="27489-197">指定角色功能的陣列。</span><span class="sxs-lookup"><span data-stu-id="27489-197">Specifies an array of role capabilities.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27489-198">->scriptpublishlocation</span><span class="sxs-lookup"><span data-stu-id="27489-198">-ScriptPublishLocation</span></span>

<span data-ttu-id="27489-199">指定腳本發行位置。</span><span class="sxs-lookup"><span data-stu-id="27489-199">Specifies the script publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27489-200">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="27489-200">-ScriptSourceLocation</span></span>

<span data-ttu-id="27489-201">指定腳本來源位置。</span><span class="sxs-lookup"><span data-stu-id="27489-201">Specifies the script source location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27489-202">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="27489-202">-SkipValidate</span></span>

<span data-ttu-id="27489-203">略過驗證封裝認證的參數。</span><span class="sxs-lookup"><span data-stu-id="27489-203">Switch that skips validating the credentials of a package.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27489-204">-Source</span><span class="sxs-lookup"><span data-stu-id="27489-204">-Source</span></span>

<span data-ttu-id="27489-205">指定一或多個套件來源。</span><span class="sxs-lookup"><span data-stu-id="27489-205">Specifies one or more package sources.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="27489-206">-Tag</span><span class="sxs-lookup"><span data-stu-id="27489-206">-Tag</span></span>

<span data-ttu-id="27489-207">指定要在套件中繼資料內搜尋的標記。</span><span class="sxs-lookup"><span data-stu-id="27489-207">Specifies a tag to search for within the package metadata.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27489-208">-Type</span><span class="sxs-lookup"><span data-stu-id="27489-208">-Type</span></span>

<span data-ttu-id="27489-209">指定是否要使用模組、腳本或其中一個來搜尋封裝。</span><span class="sxs-lookup"><span data-stu-id="27489-209">Specifies whether to search for packages with a module, a script, or either.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:
Accepted values: Module, Script, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27489-210">-Confirm</span><span class="sxs-lookup"><span data-stu-id="27489-210">-Confirm</span></span>

<span data-ttu-id="27489-211">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="27489-211">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="27489-212">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="27489-212">-WhatIf</span></span>

<span data-ttu-id="27489-213">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="27489-213">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="27489-214">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="27489-214">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="27489-215">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="27489-215">CommonParameters</span></span>

<span data-ttu-id="27489-216">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="27489-216">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="27489-217">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="27489-217">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="27489-218">輸入</span><span class="sxs-lookup"><span data-stu-id="27489-218">INPUTS</span></span>

### <span data-ttu-id="27489-219">`Save-Package` 接受來自管線的物件。</span><span class="sxs-lookup"><span data-stu-id="27489-219">`Save-Package` accepts objects from the pipeline.</span></span>

## <span data-ttu-id="27489-220">輸出</span><span class="sxs-lookup"><span data-stu-id="27489-220">OUTPUTS</span></span>

### <span data-ttu-id="27489-221">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="27489-221">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="27489-222">注意</span><span class="sxs-lookup"><span data-stu-id="27489-222">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27489-223">從2020年4月起，PowerShell 資源庫不再支援傳輸層安全性 (TLS) 1.0 和1.1 版。</span><span class="sxs-lookup"><span data-stu-id="27489-223">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="27489-224">如果您不是使用 TLS 1.2 或更高版本，當您嘗試存取 PowerShell 資源庫時，將會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="27489-224">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="27489-225">使用下列命令，以確保您使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="27489-225">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="27489-226">如需詳細資訊，請參閱 PowerShell blog 中的 [公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 。</span><span class="sxs-lookup"><span data-stu-id="27489-226">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="27489-227">相關連結</span><span class="sxs-lookup"><span data-stu-id="27489-227">RELATED LINKS</span></span>

[<span data-ttu-id="27489-228">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="27489-228">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="27489-229">Get-Package</span><span class="sxs-lookup"><span data-stu-id="27489-229">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="27489-230">Install-Package</span><span class="sxs-lookup"><span data-stu-id="27489-230">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="27489-231">Save-Package</span><span class="sxs-lookup"><span data-stu-id="27489-231">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="27489-232">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="27489-232">Uninstall-Package</span></span>](Uninstall-Package.md)
