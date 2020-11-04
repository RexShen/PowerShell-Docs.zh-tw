---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 05/22/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-package?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Package
ms.openlocfilehash: aad8b6f033674c65b4cc56708e09e5320bb046dd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202959"
---
# <span data-ttu-id="bc377-103">Get-Package</span><span class="sxs-lookup"><span data-stu-id="bc377-103">Get-Package</span></span>

## <span data-ttu-id="bc377-104">概要</span><span class="sxs-lookup"><span data-stu-id="bc377-104">SYNOPSIS</span></span>
<span data-ttu-id="bc377-105">傳回與 **PackageManagement** 一起安裝的所有軟體套件清單。</span><span class="sxs-lookup"><span data-stu-id="bc377-105">Returns a list of all software packages that were installed with **PackageManagement** .</span></span>

## <span data-ttu-id="bc377-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bc377-106">SYNTAX</span></span>

### <span data-ttu-id="bc377-107">微星</span><span class="sxs-lookup"><span data-stu-id="bc377-107">msi</span></span>

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-AdditionalArguments <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="bc377-108">程式</span><span class="sxs-lookup"><span data-stu-id="bc377-108">Programs</span></span>

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-IncludeWindowsInstaller] [-IncludeSystemComponent] [<CommonParameters>]
```

### <span data-ttu-id="bc377-109">NuGet</span><span class="sxs-lookup"><span data-stu-id="bc377-109">NuGet</span></span>

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### <span data-ttu-id="bc377-110">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="bc377-110">PowerShellGet</span></span>

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-Scope <String>] [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions]
 [<CommonParameters>]
```

## <span data-ttu-id="bc377-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="bc377-111">DESCRIPTION</span></span>

<span data-ttu-id="bc377-112">指令 `Get-Package` 程式會傳回本機電腦上以 **PackageManagement** 安裝的所有軟體套件清單。</span><span class="sxs-lookup"><span data-stu-id="bc377-112">The `Get-Package` cmdlet returns a list of all software packages on the local computer that were installed with **PackageManagement** .</span></span> <span data-ttu-id="bc377-113">您可以 `Get-Package` 在遠端電腦上執行，方法是將它當作 `Invoke-Command` 或 `Enter-PSSession` 命令或腳本的一部分執行。</span><span class="sxs-lookup"><span data-stu-id="bc377-113">You can run `Get-Package` on remote computers by running it as part of an `Invoke-Command` or `Enter-PSSession` command or script.</span></span>

## <span data-ttu-id="bc377-114">範例</span><span class="sxs-lookup"><span data-stu-id="bc377-114">EXAMPLES</span></span>

### <span data-ttu-id="bc377-115">範例1：取得所有已安裝的套件</span><span class="sxs-lookup"><span data-stu-id="bc377-115">Example 1: Get all installed packages</span></span>

<span data-ttu-id="bc377-116">`Get-Package`Cmdlet 會取得本機電腦上安裝的所有套件。</span><span class="sxs-lookup"><span data-stu-id="bc377-116">The `Get-Package` cmdlet gets all packages that are installed on the local computer.</span></span>

```powershell
Get-Package
```

```Output
Name           Version      Source                                     ProviderName
----           -------      ------                                     ------------
posh-git       0.7.3        https://www.powershellgallery.com/api/v2   PowerShellGet
```

### <span data-ttu-id="bc377-117">範例2：取得安裝在遠端電腦上的封裝</span><span class="sxs-lookup"><span data-stu-id="bc377-117">Example 2: Get packages that are installed on a remote computer</span></span>

<span data-ttu-id="bc377-118">此命令會取得 **PackageManagement** 在遠端電腦上安裝的套件清單。</span><span class="sxs-lookup"><span data-stu-id="bc377-118">This command gets a list of packages that were installed by **PackageManagement** on a remote computer.</span></span> <span data-ttu-id="bc377-119">此命令會提示您提供指定的使用者密碼。</span><span class="sxs-lookup"><span data-stu-id="bc377-119">This command prompts you to provide the specified user's password.</span></span>

```
PS> Invoke-Command -ComputerName Server01 -Credential CONTOSO\TestUser -ScriptBlock {Get-Package}
```

<span data-ttu-id="bc377-120">`Invoke-Command` 使用 **ComputerName** 參數來指定遠端電腦 **Server01** 。</span><span class="sxs-lookup"><span data-stu-id="bc377-120">`Invoke-Command` uses the **ComputerName** parameter to specify a remote computer, **Server01** .</span></span> <span data-ttu-id="bc377-121">**Credential** 參數指定具有在電腦上執行命令之許可權的網域和使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="bc377-121">The **Credential** parameter specifies a domain and user name with permissions to run commands on the computer.</span></span> <span data-ttu-id="bc377-122">**ScriptBlock** 參數會 `Get-Package` 在遠端電腦上執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bc377-122">The **ScriptBlock** parameter runs the `Get-Package` cmdlet on the remote computer.</span></span>

### <span data-ttu-id="bc377-123">範例3：取得指定提供者的封裝</span><span class="sxs-lookup"><span data-stu-id="bc377-123">Example 3: Get packages for a specified provider</span></span>

<span data-ttu-id="bc377-124">此命令會從特定提供者取得安裝在本機電腦上的軟體套件。</span><span class="sxs-lookup"><span data-stu-id="bc377-124">This command gets software packages installed on the local computer from a specific provider.</span></span>

```powershell
Get-Package -ProviderName PowerShellGet -AllVersions
```

```Output
Name                  Version      Source                                     ProviderName
----                  -------      ------                                     ------------
PackageManagement     1.2.2        https://www.powershellgallery.com/api/v2   PowerShellGet
PackageManagement     1.3.1        https://www.powershellgallery.com/api/v2   PowerShellGet
posh-git              0.7.3        https://www.powershellgallery.com/api/v2   PowerShellGet
PowerShellGet         2.0.1        https://www.powershellgallery.com/api/v2   PowerShellGet
```

<span data-ttu-id="bc377-125">`Get-Package` 使用 **ProviderName** 參數來指定特定提供者（ **PowerShellGet** ）。</span><span class="sxs-lookup"><span data-stu-id="bc377-125">`Get-Package` uses the **ProviderName** parameter to specify a specific provider, **PowerShellGet** .</span></span>
<span data-ttu-id="bc377-126">**所有版本** 參數會顯示每個已安裝的版本。</span><span class="sxs-lookup"><span data-stu-id="bc377-126">The **All-Versions** parameter displays each version that is installed.</span></span>

### <span data-ttu-id="bc377-127">範例4：取得特定封裝的精確版本</span><span class="sxs-lookup"><span data-stu-id="bc377-127">Example 4: Get an exact version of a specific package</span></span>

<span data-ttu-id="bc377-128">此命令會取得已安裝套件的特定版本。</span><span class="sxs-lookup"><span data-stu-id="bc377-128">This command gets a specific version of an installed package.</span></span> <span data-ttu-id="bc377-129">您可以安裝一個以上的封裝版本。</span><span class="sxs-lookup"><span data-stu-id="bc377-129">More than one version of a package can be installed.</span></span>

```powershell
Get-Package -Name PackageManagement -ProviderName PowerShellGet -RequiredVersion 1.3.1
```

```Output
Name                  Version      Source                                     ProviderName
----                  -------      ------                                     ------------
PackageManagement     1.3.1        https://www.powershellgallery.com/api/v2   PowerShellGet
```

<span data-ttu-id="bc377-130">`Get-Package` 使用 **Name** 參數來指定封裝名稱， **PackageManagement** 。</span><span class="sxs-lookup"><span data-stu-id="bc377-130">`Get-Package` uses **Name** parameter to specify the package name, **PackageManagement** .</span></span> <span data-ttu-id="bc377-131">**ProviderName** 參數會指定提供者（ **PowerShellGet** ）。</span><span class="sxs-lookup"><span data-stu-id="bc377-131">The **ProviderName** parameter specifies the provider, **PowerShellGet** .</span></span> <span data-ttu-id="bc377-132">**必要的版本** 參數指定已安裝的版本。</span><span class="sxs-lookup"><span data-stu-id="bc377-132">The **Required-Version** parameter specifies an installed version.</span></span>

### <span data-ttu-id="bc377-133">範例5：卸載套件</span><span class="sxs-lookup"><span data-stu-id="bc377-133">Example 5: Uninstall a package</span></span>

<span data-ttu-id="bc377-134">此範例會取得封裝資訊，然後卸載封裝。</span><span class="sxs-lookup"><span data-stu-id="bc377-134">This example gets package information and then uninstalls the package.</span></span>

```powershell
Get-Package -Name posh-git -RequiredVersion 0.7.3 | Uninstall-Package
```

<span data-ttu-id="bc377-135">`Get-Package` 使用 **Name** 參數來指定封裝名稱 **posh-git** 。</span><span class="sxs-lookup"><span data-stu-id="bc377-135">`Get-Package` uses the **Name** parameter to specify the package name, **posh-git** .</span></span> <span data-ttu-id="bc377-136">**RequiredVersion** 參數是封裝的特定版本。</span><span class="sxs-lookup"><span data-stu-id="bc377-136">The **RequiredVersion** parameter is a specific version of the package.</span></span> <span data-ttu-id="bc377-137">物件會向下傳送至 `Uninstall-Package` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bc377-137">The object is sent down the pipeline to the `Uninstall-Package` cmdlet.</span></span> <span data-ttu-id="bc377-138">`Uninstall-Package` 移除封裝。</span><span class="sxs-lookup"><span data-stu-id="bc377-138">`Uninstall-Package` removes the package.</span></span>

## <span data-ttu-id="bc377-139">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bc377-139">PARAMETERS</span></span>

### <span data-ttu-id="bc377-140">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="bc377-140">-AllowClobber</span></span>

<span data-ttu-id="bc377-141">覆寫與現有命令衝突的警告訊息。</span><span class="sxs-lookup"><span data-stu-id="bc377-141">Overrides warning messages about conflicts with existing commands.</span></span> <span data-ttu-id="bc377-142">覆寫現有的命令，其名稱與模組所安裝的命令相同。</span><span class="sxs-lookup"><span data-stu-id="bc377-142">Overwrites existing commands that have the same name as commands being installed by a module.</span></span>

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

### <span data-ttu-id="bc377-143">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="bc377-143">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="bc377-144">在結果中包含標記為發行前版本的套件。</span><span class="sxs-lookup"><span data-stu-id="bc377-144">Includes packages marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="bc377-145">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="bc377-145">-AllVersions</span></span>

<span data-ttu-id="bc377-146">指出會傳回 `Get-Package` 所有可用的封裝版本。</span><span class="sxs-lookup"><span data-stu-id="bc377-146">Indicates that `Get-Package` returns all available versions of the package.</span></span> <span data-ttu-id="bc377-147">根據預設， `Get-Package` 只會傳回最新的可用版本。</span><span class="sxs-lookup"><span data-stu-id="bc377-147">By default, `Get-Package` only returns the newest available version.</span></span>

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

### <span data-ttu-id="bc377-148">-Destination</span><span class="sxs-lookup"><span data-stu-id="bc377-148">-Destination</span></span>

<span data-ttu-id="bc377-149">指定包含解壓縮封裝檔案之目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="bc377-149">Specifies the path to a directory that contains extracted package files.</span></span>

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

### <span data-ttu-id="bc377-150">-ExcludeVersion</span><span class="sxs-lookup"><span data-stu-id="bc377-150">-ExcludeVersion</span></span>

<span data-ttu-id="bc377-151">切換以排除資料夾路徑中的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="bc377-151">Switch to exclude the version number in the folder path.</span></span>

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

### <span data-ttu-id="bc377-152">-Force</span><span class="sxs-lookup"><span data-stu-id="bc377-152">-Force</span></span>

<span data-ttu-id="bc377-153">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="bc377-153">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="bc377-154">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="bc377-154">-ForceBootstrap</span></span>

<span data-ttu-id="bc377-155">指出 `Get-Package` 強制 **PackageManagement** 自動安裝封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="bc377-155">Indicates that `Get-Package` forces **PackageManagement** to automatically install the package provider.</span></span>

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

### <span data-ttu-id="bc377-156">-InstallUpdate</span><span class="sxs-lookup"><span data-stu-id="bc377-156">-InstallUpdate</span></span>

<span data-ttu-id="bc377-157">指出此 Cmdlet 會安裝更新。</span><span class="sxs-lookup"><span data-stu-id="bc377-157">Indicates that this cmdlet installs updates.</span></span>

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

### <span data-ttu-id="bc377-158">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="bc377-158">-MaximumVersion</span></span>

<span data-ttu-id="bc377-159">指定您想要尋找的最大套件版本。</span><span class="sxs-lookup"><span data-stu-id="bc377-159">Specifies the maximum package version that you want to find.</span></span>

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

### <span data-ttu-id="bc377-160">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="bc377-160">-MinimumVersion</span></span>

<span data-ttu-id="bc377-161">指定您想要尋找的最小套件版本。</span><span class="sxs-lookup"><span data-stu-id="bc377-161">Specifies the minimum package version that you want to find.</span></span> <span data-ttu-id="bc377-162">如果有更高的版本可用，則會傳回該版本。</span><span class="sxs-lookup"><span data-stu-id="bc377-162">If a higher version is available, that version is returned.</span></span>

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

### <span data-ttu-id="bc377-163">-Name</span><span class="sxs-lookup"><span data-stu-id="bc377-163">-Name</span></span>

<span data-ttu-id="bc377-164">指定一或多個封裝名稱，或包含萬用字元的封裝名稱。</span><span class="sxs-lookup"><span data-stu-id="bc377-164">Specifies one or more package names, or package names with wildcard characters.</span></span> <span data-ttu-id="bc377-165">以逗號分隔多個封裝名稱。</span><span class="sxs-lookup"><span data-stu-id="bc377-165">Separate multiple package names with commas.</span></span>

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

### <span data-ttu-id="bc377-166">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="bc377-166">-NoPathUpdate</span></span>

<span data-ttu-id="bc377-167">**NoPathUpdate** 僅適用于 `Install-Script` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bc377-167">**NoPathUpdate** only applies to the `Install-Script` cmdlet.</span></span> <span data-ttu-id="bc377-168">**NoPathUpdate** 是提供者所加入的動態參數，而且不受支援 `Get-Package` 。</span><span class="sxs-lookup"><span data-stu-id="bc377-168">**NoPathUpdate** is a dynamic parameter added by the provider and isn't supported by `Get-Package`.</span></span>

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

### <span data-ttu-id="bc377-169">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="bc377-169">-PackageManagementProvider</span></span>

<span data-ttu-id="bc377-170">指定套件管理提供者的名稱。</span><span class="sxs-lookup"><span data-stu-id="bc377-170">Specifies the name of a package management provider.</span></span>

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

### <span data-ttu-id="bc377-171">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="bc377-171">-ProviderName</span></span>

<span data-ttu-id="bc377-172">指定一或多個封裝提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="bc377-172">Specifies one or more package provider names.</span></span> <span data-ttu-id="bc377-173">以逗號分隔多個封裝提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="bc377-173">Separate multiple package provider names with commas.</span></span>
<span data-ttu-id="bc377-174">使用 `Get-PackageProvider` 取得可用封裝提供者的清單。</span><span class="sxs-lookup"><span data-stu-id="bc377-174">Use `Get-PackageProvider` to get a list of available package providers.</span></span>

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

### <span data-ttu-id="bc377-175">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="bc377-175">-RequiredVersion</span></span>

<span data-ttu-id="bc377-176">指定要尋找之封裝的確切版本。</span><span class="sxs-lookup"><span data-stu-id="bc377-176">Specifies the exact version of the package to find.</span></span>

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

### <span data-ttu-id="bc377-177">-Scope</span><span class="sxs-lookup"><span data-stu-id="bc377-177">-Scope</span></span>

<span data-ttu-id="bc377-178">指定封裝的搜尋範圍。</span><span class="sxs-lookup"><span data-stu-id="bc377-178">Specifies the search scope for the package.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet, PowerShellGet
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bc377-179">-SkipDependencies</span><span class="sxs-lookup"><span data-stu-id="bc377-179">-SkipDependencies</span></span>

<span data-ttu-id="bc377-180">參數，指定略過尋找任何套件相依性。</span><span class="sxs-lookup"><span data-stu-id="bc377-180">Switch that specifies to skip finding any package dependencies.</span></span>

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

### <span data-ttu-id="bc377-181">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="bc377-181">-SkipPublisherCheck</span></span>

<span data-ttu-id="bc377-182">可讓您取得比已安裝版本還新的套件版本。</span><span class="sxs-lookup"><span data-stu-id="bc377-182">Allows you to get a package version that is newer than your installed version.</span></span> <span data-ttu-id="bc377-183">例如，已安裝的套件已由受信任的發行者進行數位簽署，但新版本未經過數位簽署。</span><span class="sxs-lookup"><span data-stu-id="bc377-183">For example, an installed package that is digitally signed by a trusted publisher but a new version isn't digitally signed.</span></span>

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

### <span data-ttu-id="bc377-184">-Type</span><span class="sxs-lookup"><span data-stu-id="bc377-184">-Type</span></span>

<span data-ttu-id="bc377-185">指定是否要使用模組、腳本或其中一個來搜尋封裝。</span><span class="sxs-lookup"><span data-stu-id="bc377-185">Specifies whether to search for packages with a module, a script, or either.</span></span>

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

### <span data-ttu-id="bc377-186">-AdditionalArguments</span><span class="sxs-lookup"><span data-stu-id="bc377-186">-AdditionalArguments</span></span>

<span data-ttu-id="bc377-187">指定其他引數。</span><span class="sxs-lookup"><span data-stu-id="bc377-187">Specifies additional arguments.</span></span>

```yaml
Type: System.String[]
Parameter Sets: msi
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bc377-188">-IncludeSystemComponent</span><span class="sxs-lookup"><span data-stu-id="bc377-188">-IncludeSystemComponent</span></span>

<span data-ttu-id="bc377-189">指出此 Cmdlet 包含結果中的系統元件。</span><span class="sxs-lookup"><span data-stu-id="bc377-189">Indicates that this cmdlet includes system components in the results.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Programs
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bc377-190">-IncludeWindowsInstaller</span><span class="sxs-lookup"><span data-stu-id="bc377-190">-IncludeWindowsInstaller</span></span>

<span data-ttu-id="bc377-191">指出此 Cmdlet 會在結果中包含 Windows Installer。</span><span class="sxs-lookup"><span data-stu-id="bc377-191">Indicates that this cmdlet includes the Windows Installer in the results.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Programs
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bc377-192">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bc377-192">CommonParameters</span></span>

<span data-ttu-id="bc377-193">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="bc377-193">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bc377-194">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="bc377-194">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bc377-195">輸入</span><span class="sxs-lookup"><span data-stu-id="bc377-195">INPUTS</span></span>

## <span data-ttu-id="bc377-196">輸出</span><span class="sxs-lookup"><span data-stu-id="bc377-196">OUTPUTS</span></span>

### <span data-ttu-id="bc377-197">SoftwareIdentity[]</span><span class="sxs-lookup"><span data-stu-id="bc377-197">SoftwareIdentity[]</span></span>

## <span data-ttu-id="bc377-198">注意</span><span class="sxs-lookup"><span data-stu-id="bc377-198">NOTES</span></span>

<span data-ttu-id="bc377-199">在命令中包含封裝提供者可以讓 Cmdlet 提供動態參數。</span><span class="sxs-lookup"><span data-stu-id="bc377-199">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="bc377-200">動態參數是封裝提供者專用的。</span><span class="sxs-lookup"><span data-stu-id="bc377-200">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="bc377-201">此 `Get-Help` Cmdlet 會列出 Cmdlet 的參數集，並包含提供者的參數集。</span><span class="sxs-lookup"><span data-stu-id="bc377-201">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span> <span data-ttu-id="bc377-202">例如， `Get-Package` 具有 **PowerShellGet** 參數集，其中包含 `-NoPathUpdate` 、 `AllowClobber` 和 `SkipPublisherCheck` 。</span><span class="sxs-lookup"><span data-stu-id="bc377-202">For example, `Get-Package` has the **PowerShellGet** parameter set that includes `-NoPathUpdate`, `AllowClobber`, and `SkipPublisherCheck`.</span></span>

## <span data-ttu-id="bc377-203">相關連結</span><span class="sxs-lookup"><span data-stu-id="bc377-203">RELATED LINKS</span></span>

[<span data-ttu-id="bc377-204">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="bc377-204">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="bc377-205">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="bc377-205">Enter-PSSession</span></span>](../Microsoft.PowerShell.Core/Enter-PSSession.md)

[<span data-ttu-id="bc377-206">Find-Package</span><span class="sxs-lookup"><span data-stu-id="bc377-206">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="bc377-207">Get-Help</span><span class="sxs-lookup"><span data-stu-id="bc377-207">Get-Help</span></span>](../Microsoft.PowerShell.Core/Get-Help.md)

[<span data-ttu-id="bc377-208">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="bc377-208">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="bc377-209">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="bc377-209">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="bc377-210">Install-Package</span><span class="sxs-lookup"><span data-stu-id="bc377-210">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="bc377-211">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="bc377-211">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="bc377-212">Save-Package</span><span class="sxs-lookup"><span data-stu-id="bc377-212">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="bc377-213">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="bc377-213">Uninstall-Package</span></span>](Uninstall-Package.md)