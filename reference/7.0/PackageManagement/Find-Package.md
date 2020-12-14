---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 04/03/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/find-package?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Package
ms.openlocfilehash: 83336a97f13dc100943c3d0008ee97d28873adfb
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94890295"
---
# <span data-ttu-id="d4f7b-103">Find-Package</span><span class="sxs-lookup"><span data-stu-id="d4f7b-103">Find-Package</span></span>

## <span data-ttu-id="d4f7b-104">概要</span><span class="sxs-lookup"><span data-stu-id="d4f7b-104">SYNOPSIS</span></span>
<span data-ttu-id="d4f7b-105">尋找可用套件來源中的軟體套件。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-105">Finds software packages in available package sources.</span></span>

## <span data-ttu-id="d4f7b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d4f7b-106">SYNTAX</span></span>

### <span data-ttu-id="d4f7b-107">NuGet</span><span class="sxs-lookup"><span data-stu-id="d4f7b-107">NuGet</span></span>

```
Find-Package [-IncludeDependencies] [-AllVersions] [-Source <String[]>] [-Credential <PSCredential>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String[]>] [-RequiredVersion <String>]
 [-MinimumVersion <String>] [-MaximumVersion <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-ConfigFile <String>] [-SkipValidate] [-Headers <String[]>]
 [-FilterOnTag <String[]>] [-Contains <String>] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="d4f7b-108">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="d4f7b-108">PowerShellGet</span></span>

```
Find-Package [-IncludeDependencies] [-AllVersions] [-Source <String[]>] [-Credential <PSCredential>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String[]>] [-RequiredVersion <String>]
 [-MinimumVersion <String>] [-MaximumVersion <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-AllowPrereleaseVersions] [-PackageManagementProvider <String>]
 [-PublishLocation <String>] [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>]
 [-Type <String>] [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>]
 [-DscResource <String[]>] [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense]
 [<CommonParameters>]
```

## <span data-ttu-id="d4f7b-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="d4f7b-109">DESCRIPTION</span></span>

<span data-ttu-id="d4f7b-110">`Find-Package` 尋找套件來源中可用的軟體套件。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-110">`Find-Package` finds software packages that are available in package sources.</span></span> <span data-ttu-id="d4f7b-111">`Get-PackageProvider` 並 `Get-PackageSource` 顯示您提供者的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-111">`Get-PackageProvider` and `Get-PackageSource` display details about your providers.</span></span>

## <span data-ttu-id="d4f7b-112">範例</span><span class="sxs-lookup"><span data-stu-id="d4f7b-112">EXAMPLES</span></span>

### <span data-ttu-id="d4f7b-113">範例1：尋找封裝提供者中的所有可用封裝</span><span class="sxs-lookup"><span data-stu-id="d4f7b-113">Example 1: Find all available packages from a package provider</span></span>

<span data-ttu-id="d4f7b-114">此命令會在已註冊的資源庫中尋找所有可用的 PowerShell 模組套件。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-114">This command finds all available PowerShell module packages in a registered gallery.</span></span> <span data-ttu-id="d4f7b-115">使用 `Get-PackageProvider` 取得提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-115">Use `Get-PackageProvider` to get the provider name.</span></span>

```
Find-Package -ProviderName NuGet
```

```Output
Name               Version   Source     Summary
----               -------   ------     -------
NUnit              3.11.0    MyNuGet    NUnit is a unit-testing framework for all .NET langua...
Newtonsoft.Json    12.0.1    MyNuGet    Json.NET is a popular high-performance JSON framework...
EntityFramework    6.2.0     MyNuGet    Entity Framework is Microsoft's recommended data acce...
MySql.Data         8.0.15    MyNuGet    MySql.Data.MySqlClient .Net Core Class Library
bootstrap          4.3.1     MyNuGet    Bootstrap framework in CSS. Includes fonts and JavaSc...
NuGet.Core         2.14.0    MyNuGet    NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="d4f7b-116">`Find-Package` 使用 **provider** 參數指定提供者 **NuGet**。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-116">`Find-Package` uses the **Provider** parameter to specify the provider **NuGet**.</span></span>

### <span data-ttu-id="d4f7b-117">範例2：從套件來源尋找套件</span><span class="sxs-lookup"><span data-stu-id="d4f7b-117">Example 2: Find a package from a package source</span></span>

<span data-ttu-id="d4f7b-118">此命令會從指定的套件來源尋找最新版本的套件。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-118">This command finds the newest version of a package from a specified package source.</span></span> <span data-ttu-id="d4f7b-119">如果未提供套件來源，則會 `Find-Package` 搜尋每個已安裝的套件提供者及其套件來源。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-119">If a package source isn't provided, `Find-Package` searches each installed package provider and its package sources.</span></span> <span data-ttu-id="d4f7b-120">使用 `Get-PackageSource` 取得來源名稱。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-120">Use `Get-PackageSource` to get the source name.</span></span>

```
Find-Package -Name NuGet.Core -Source MyNuGet
```

```Output
Name         Version   Source    Summary
----         -------   ------    -------
NuGet.Core   2.14.0    MyNuGet   NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="d4f7b-121">`Find-Package` 使用 **Name** 參數來指定套件名稱 **nuget.exe**。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-121">`Find-Package` uses the **Name** parameter to specify the package name **NuGet.Core**.</span></span> <span data-ttu-id="d4f7b-122">**Source** 參數會指定在 **MyNuGet** 中搜尋封裝。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-122">The **Source** parameter specifies to search for the package in **MyNuGet**.</span></span>

### <span data-ttu-id="d4f7b-123">範例3：尋找套件的所有版本</span><span class="sxs-lookup"><span data-stu-id="d4f7b-123">Example 3: Find all versions of a package</span></span>

<span data-ttu-id="d4f7b-124">此命令會從指定的提供者找出所有可用的套件版本。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-124">This command finds all available package versions from a specified provider.</span></span>

```
Find-Package -Name NuGet.Core -Source MyNuGet -AllVersions
```

```Output
Name          Version          Source       Summary
----          -------          ------       -------
NuGet.Core    2.14.0           MyNuGet      NuGet.Core is the core framework assembly for NuGet...
NuGet.Core    2.14.0-rtm-832   MyNuGet      NuGet.Core is the core framework assembly for NuGet...
NuGet.Core    2.13.0           MyNuGet      NuGet.Core is the core framework assembly for NuGet...
...
NuGet.Core    1.1.229.159      MyNuGet      NuGet.Core is the core framework assembly for NuGet...
Nuget.Core    1.0.1120.104     MyNuGet      NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="d4f7b-125">`Find-Package` 使用 **Name** 參數來指定套件 **nuget.exe**。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-125">`Find-Package` uses the **Name** parameter to specify the package **NuGet.Core**.</span></span> <span data-ttu-id="d4f7b-126">**ProviderName** 參數指定要在 **MyNuGet** 中搜尋封裝。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-126">The **ProviderName** parameter specifies to search for the package in **MyNuGet**.</span></span> <span data-ttu-id="d4f7b-127">**Allversions 進行篩選** 指定傳回所有可用的版本。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-127">**AllVersions** specifies that all available versions are returned.</span></span>

### <span data-ttu-id="d4f7b-128">範例4：尋找具有特定名稱和版本的套件</span><span class="sxs-lookup"><span data-stu-id="d4f7b-128">Example 4: Find a package with a specific name and version</span></span>

<span data-ttu-id="d4f7b-129">此命令會從指定的提供者中尋找特定的封裝版本。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-129">This command finds a specific package version from a specified provider.</span></span>

```
Find-Package -Name NuGet.Core -ProviderName NuGet -RequiredVersion 2.9.0
```

```Output
Name          Version          Source       Summary
----          -------          ------       -------
NuGet.Core    2.9.0            MyNuGet      NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="d4f7b-130">`Find-Package` 使用 **Name** 參數來指定套件名稱 **nuget.exe**。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-130">`Find-Package` uses the **Name** parameter to specify the package name **NuGet.Core**.</span></span> <span data-ttu-id="d4f7b-131">**ProviderName** 參數指定要在 **NuGet** 中搜尋套件。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-131">The **ProviderName** parameter specifies to search for the package in **NuGet**.</span></span> <span data-ttu-id="d4f7b-132">**RequiredVersion** 指定只傳回版本 **2.9.0 版** 。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-132">**RequiredVersion** specifies that only version **2.9.0** is returned.</span></span>

### <span data-ttu-id="d4f7b-133">範例5：尋找版本範圍內的套件</span><span class="sxs-lookup"><span data-stu-id="d4f7b-133">Example 5: Find packages within a range of versions</span></span>

<span data-ttu-id="d4f7b-134">此命令會尋找指定套件的版本範圍。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-134">This command finds a range of versions for a specified package.</span></span>

```
Find-Package -Name NuGet.Core -ProviderName NuGet -MinimumVersion 2.7.0 -MaximumVersion 2.9.0 -AllVersions
```

```Output
Name          Version          Source       Summary
----          -------          ------       -------
NuGet.Core    2.9.0            MyNuGet      NuGet.Core is the core framework assembly for NuGet...
NuGet.Core    2.8.6            MyNuGet      NuGet.Core is the core framework assembly for NuGet...
NuGet.Core    2.8.0            MyNuGet      NuGet.Core is the core framework assembly for NuGet...
NuGet.Core    2.7.0            MyNuGet      NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="d4f7b-135">`Find-Package` 使用 **Name** 參數來指定套件名稱 **nuget.exe**。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-135">`Find-Package` uses the **Name** parameter to specify the package name **NuGet.Core**.</span></span> <span data-ttu-id="d4f7b-136">**ProviderName** 參數指定要在 **NuGet** 中搜尋套件。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-136">The **ProviderName** parameter specifies to search for the package in **NuGet**.</span></span> <span data-ttu-id="d4f7b-137">**MinimumVersion** 會指定最低版本的 **2.7.0**。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-137">**MinimumVersion** specifies the lowest version **2.7.0**.</span></span> <span data-ttu-id="d4f7b-138">**MaximumVersion** 指定最高版本的 **2.9.0 版**。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-138">**MaximumVersion** specifies the highest version **2.9.0**.</span></span>
<span data-ttu-id="d4f7b-139">**Allversions 進行篩選** 會根據最小值和最大值來判斷傳回的範圍。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-139">**AllVersions** determines the range is returned as specified by the minimum and maximum.</span></span>

### <span data-ttu-id="d4f7b-140">範例6：尋找檔案系統中的封裝</span><span class="sxs-lookup"><span data-stu-id="d4f7b-140">Example 6: Find a package from a file system</span></span>

<span data-ttu-id="d4f7b-141">此命令會尋找副檔名 `.nupkg` 儲存在本機電腦上的封裝。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-141">This command finds packages with the file extension `.nupkg` that are stored on the local computer.</span></span>
<span data-ttu-id="d4f7b-142">這些檔案是從資源庫（例如 **NuGet**）下載的套件。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-142">The files are packages downloaded from a gallery such as the **NuGet**.</span></span>

```
PS> Find-Package -Source C:\LocalPkg
```

```Output
Name                 Version    Source           Summary
----                 -------    ------           -------
Microsoft.Web.Xdt    3.0.0      C:\LocalPkg\     Microsoft Xml Document Transformation (XDT)...
NuGet.Core           2.14.0     C:\LocalPkg\     NuGet.Core is the core framework assembly...
```

## <span data-ttu-id="d4f7b-143">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d4f7b-143">PARAMETERS</span></span>

### <span data-ttu-id="d4f7b-144">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="d4f7b-144">-AcceptLicense</span></span>

<span data-ttu-id="d4f7b-145">如果封裝需要授權合約，就會自動接受授權合約。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-145">Automatically accepts a license agreement if the package requires it.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d4f7b-146">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="d4f7b-146">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="d4f7b-147">在結果中包含標記為發行前版本的套件。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-147">Includes packages marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="d4f7b-148">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="d4f7b-148">-AllVersions</span></span>

<span data-ttu-id="d4f7b-149">指出會傳回 `Find-Package` 所有可用的封裝版本。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-149">Indicates that `Find-Package` returns all available versions of the package.</span></span> <span data-ttu-id="d4f7b-150">根據預設， `Find-Package` 只會傳回最新的可用版本。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-150">By default, `Find-Package` only returns the newest available version.</span></span>

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

### <span data-ttu-id="d4f7b-151">-Command</span><span class="sxs-lookup"><span data-stu-id="d4f7b-151">-Command</span></span>

<span data-ttu-id="d4f7b-152">指定所搜尋的命令陣列 `Find-Package` 。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-152">Specifies an array of commands searched by `Find-Package`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d4f7b-153">-Read-configfile</span><span class="sxs-lookup"><span data-stu-id="d4f7b-153">-ConfigFile</span></span>

<span data-ttu-id="d4f7b-154">指定設定檔。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-154">Specifies a configuration file.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d4f7b-155">-Contains</span><span class="sxs-lookup"><span data-stu-id="d4f7b-155">-Contains</span></span>

<span data-ttu-id="d4f7b-156">`Find-Package` 如果物件的屬性值中有任何專案與指定的值完全相符，就會取得物件。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-156">`Find-Package` gets objects if any item in the object's property values are an exact match for the specified value.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d4f7b-157">-Credential</span><span class="sxs-lookup"><span data-stu-id="d4f7b-157">-Credential</span></span>

<span data-ttu-id="d4f7b-158">指定有權搜尋封裝的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-158">Specifies a user account that has permission to search for packages.</span></span>

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

### <span data-ttu-id="d4f7b-159">-DscResource</span><span class="sxs-lookup"><span data-stu-id="d4f7b-159">-DscResource</span></span>

<span data-ttu-id="d4f7b-160">指定此 Cmdlet 搜尋的 Desired State Configuration (DSC) 資源陣列。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-160">Specifies an array of Desired State Configuration (DSC) resources that this cmdlet searches.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d4f7b-161">-Filter</span><span class="sxs-lookup"><span data-stu-id="d4f7b-161">-Filter</span></span>

<span data-ttu-id="d4f7b-162">指定要在 [ **名稱** ] 和 [ **描述** ] 屬性內搜尋的字詞。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-162">Specifies terms to search for within the **Name** and **Description** properties.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d4f7b-163">-FilterOnTag</span><span class="sxs-lookup"><span data-stu-id="d4f7b-163">-FilterOnTag</span></span>

<span data-ttu-id="d4f7b-164">指定篩選結果的標記。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-164">Specifies the tag that filters the results.</span></span> <span data-ttu-id="d4f7b-165">不包含指定標記的結果會被排除。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-165">Results that don't contain the specified tag are excluded.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d4f7b-166">-Force</span><span class="sxs-lookup"><span data-stu-id="d4f7b-166">-Force</span></span>

<span data-ttu-id="d4f7b-167">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-167">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="d4f7b-168">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="d4f7b-168">-ForceBootstrap</span></span>

<span data-ttu-id="d4f7b-169">指出 `Find-Package` 強制 **PackageManagement** 自動安裝封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-169">Indicates that `Find-Package` forces **PackageManagement** to automatically install the package provider.</span></span>

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

### <span data-ttu-id="d4f7b-170">-Headers</span><span class="sxs-lookup"><span data-stu-id="d4f7b-170">-Headers</span></span>

<span data-ttu-id="d4f7b-171">指定封裝的標頭。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-171">Specifies the headers for the package.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d4f7b-172">-Includedependencies 來</span><span class="sxs-lookup"><span data-stu-id="d4f7b-172">-IncludeDependencies</span></span>

<span data-ttu-id="d4f7b-173">指出此 Cmdlet 會在結果中包含套件相依性。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-173">Indicates that this cmdlet includes package dependencies in the results.</span></span>

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

### <span data-ttu-id="d4f7b-174">-Include</span><span class="sxs-lookup"><span data-stu-id="d4f7b-174">-Includes</span></span>

<span data-ttu-id="d4f7b-175">指定是否 `Find-Package` 應該尋找類別中的所有套件。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-175">Specifies whether `Find-Package` should find all packages within a category.</span></span>

<span data-ttu-id="d4f7b-176">接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="d4f7b-176">The accepted values are as follows:</span></span>

- <span data-ttu-id="d4f7b-177">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d4f7b-177">Cmdlet</span></span>
- <span data-ttu-id="d4f7b-178">DscResource</span><span class="sxs-lookup"><span data-stu-id="d4f7b-178">DscResource</span></span>
- <span data-ttu-id="d4f7b-179">函式</span><span class="sxs-lookup"><span data-stu-id="d4f7b-179">Function</span></span>
- <span data-ttu-id="d4f7b-180">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="d4f7b-180">RoleCapability</span></span>
- <span data-ttu-id="d4f7b-181">工作流程</span><span class="sxs-lookup"><span data-stu-id="d4f7b-181">Workflow</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet
Aliases:
Accepted values: Cmdlet, DscResource, Function, RoleCapability, Workflow

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d4f7b-182">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="d4f7b-182">-MaximumVersion</span></span>

<span data-ttu-id="d4f7b-183">指定您想要尋找的最大套件版本。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-183">Specifies the maximum package version that you want to find.</span></span>

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

### <span data-ttu-id="d4f7b-184">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="d4f7b-184">-MinimumVersion</span></span>

<span data-ttu-id="d4f7b-185">指定您想要尋找的最小套件版本。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-185">Specifies the minimum package version that you want to find.</span></span> <span data-ttu-id="d4f7b-186">如果有更高的版本可用，則會傳回該版本。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-186">If a higher version is available, that version is returned.</span></span>

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

### <span data-ttu-id="d4f7b-187">-Name</span><span class="sxs-lookup"><span data-stu-id="d4f7b-187">-Name</span></span>

<span data-ttu-id="d4f7b-188">指定一或多個封裝名稱，或包含萬用字元的封裝名稱。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-188">Specifies one or more package names, or package names with wildcard characters.</span></span> <span data-ttu-id="d4f7b-189">以逗號分隔多個封裝名稱。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-189">Separate multiple package names with commas.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="d4f7b-190">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="d4f7b-190">-PackageManagementProvider</span></span>

<span data-ttu-id="d4f7b-191">指定套件管理提供者的名稱。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-191">Specifies the name of a package management provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d4f7b-192">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="d4f7b-192">-ProviderName</span></span>

<span data-ttu-id="d4f7b-193">指定一或多個封裝提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-193">Specifies one or more package provider names.</span></span> <span data-ttu-id="d4f7b-194">以逗號分隔多個封裝提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-194">Separate multiple package provider names with commas.</span></span>
<span data-ttu-id="d4f7b-195">使用 `Get-PackageProvider` 取得可用封裝提供者的清單。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-195">Use `Get-PackageProvider` to get a list of available package providers.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d4f7b-196">-Proxy</span><span class="sxs-lookup"><span data-stu-id="d4f7b-196">-Proxy</span></span>

<span data-ttu-id="d4f7b-197">為要求指定 proxy 伺服器，而不是直接連線到網際網路資源。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-197">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="d4f7b-198">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="d4f7b-198">-ProxyCredential</span></span>

<span data-ttu-id="d4f7b-199">指定具有使用 **Proxy** 參數所指定 Proxy 伺服器之權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-199">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="d4f7b-200">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="d4f7b-200">-PublishLocation</span></span>

<span data-ttu-id="d4f7b-201">指定發佈封裝的位置。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-201">Specifies a location for publishing the package.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d4f7b-202">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="d4f7b-202">-RequiredVersion</span></span>

<span data-ttu-id="d4f7b-203">指定您想要尋找的確切套件版本。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-203">Specifies an exact package version that you want to find.</span></span>

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

### <span data-ttu-id="d4f7b-204">-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="d4f7b-204">-RoleCapability</span></span>

<span data-ttu-id="d4f7b-205">指定角色功能的陣列。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-205">Specifies an array of role capabilities.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d4f7b-206">->scriptpublishlocation</span><span class="sxs-lookup"><span data-stu-id="d4f7b-206">-ScriptPublishLocation</span></span>

<span data-ttu-id="d4f7b-207">指定封裝的腳本發行位置。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-207">Specifies a script publishing location for the package.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d4f7b-208">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="d4f7b-208">-ScriptSourceLocation</span></span>

<span data-ttu-id="d4f7b-209">指定腳本來源位置。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-209">Specifies a script source location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d4f7b-210">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="d4f7b-210">-SkipValidate</span></span>

<span data-ttu-id="d4f7b-211">略過封裝認證驗證的參數。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-211">Switch that skips package credential validation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d4f7b-212">-Source</span><span class="sxs-lookup"><span data-stu-id="d4f7b-212">-Source</span></span>

<span data-ttu-id="d4f7b-213">指定一或多個套件來源。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-213">Specifies one or more package sources.</span></span> <span data-ttu-id="d4f7b-214">用 `Get-PackageSource` 來取得可用套件來源的清單。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-214">Use `Get-PackageSource` to get a list of available package sources.</span></span> <span data-ttu-id="d4f7b-215">檔案系統目錄可以作為下載封裝的來源。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-215">A file system directory can be used as a source for download packages.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d4f7b-216">-Tag</span><span class="sxs-lookup"><span data-stu-id="d4f7b-216">-Tag</span></span>

<span data-ttu-id="d4f7b-217">指定要在套件中繼資料中搜尋的一或多個字串。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-217">Specifies one or more strings to search for in the package metadata.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d4f7b-218">-Type</span><span class="sxs-lookup"><span data-stu-id="d4f7b-218">-Type</span></span>

<span data-ttu-id="d4f7b-219">指定是否要使用模組、腳本或其中一個來搜尋封裝。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-219">Specifies whether to search for packages with a module, a script, or either.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:
Accepted values: Module, Script, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d4f7b-220">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d4f7b-220">CommonParameters</span></span>

<span data-ttu-id="d4f7b-221">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-221">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d4f7b-222">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-222">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d4f7b-223">輸入</span><span class="sxs-lookup"><span data-stu-id="d4f7b-223">INPUTS</span></span>

### <span data-ttu-id="d4f7b-224">無</span><span class="sxs-lookup"><span data-stu-id="d4f7b-224">None</span></span>

<span data-ttu-id="d4f7b-225">`Find-Package` 不接受來自管線的輸入。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-225">`Find-Package` doesn't accept input from the pipeline.</span></span>

## <span data-ttu-id="d4f7b-226">輸出</span><span class="sxs-lookup"><span data-stu-id="d4f7b-226">OUTPUTS</span></span>

### <span data-ttu-id="d4f7b-227">SoftwareIdentify[]</span><span class="sxs-lookup"><span data-stu-id="d4f7b-227">SoftwareIdentify[]</span></span>

<span data-ttu-id="d4f7b-228">`Find-Package` 輸出 **SoftwareIdentity** 物件。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-228">`Find-Package` outputs a **SoftwareIdentity** object.</span></span>

## <span data-ttu-id="d4f7b-229">注意</span><span class="sxs-lookup"><span data-stu-id="d4f7b-229">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d4f7b-230">從2020年4月起，PowerShell 資源庫不再支援傳輸層安全性 (TLS) 1.0 和1.1 版。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-230">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="d4f7b-231">如果您不是使用 TLS 1.2 或更高版本，當您嘗試存取 PowerShell 資源庫時，將會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-231">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="d4f7b-232">使用下列命令，以確保您使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="d4f7b-232">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="d4f7b-233">如需詳細資訊，請參閱 PowerShell blog 中的 [公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 。</span><span class="sxs-lookup"><span data-stu-id="d4f7b-233">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="d4f7b-234">相關連結</span><span class="sxs-lookup"><span data-stu-id="d4f7b-234">RELATED LINKS</span></span>

[<span data-ttu-id="d4f7b-235">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="d4f7b-235">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="d4f7b-236">Get-Package</span><span class="sxs-lookup"><span data-stu-id="d4f7b-236">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="d4f7b-237">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="d4f7b-237">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="d4f7b-238">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="d4f7b-238">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="d4f7b-239">Install-Package</span><span class="sxs-lookup"><span data-stu-id="d4f7b-239">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="d4f7b-240">Save-Package</span><span class="sxs-lookup"><span data-stu-id="d4f7b-240">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="d4f7b-241">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="d4f7b-241">Uninstall-Package</span></span>](Uninstall-Package.md)
