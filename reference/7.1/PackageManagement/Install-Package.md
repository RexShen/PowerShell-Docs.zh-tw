---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 05/23/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-package?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Package
ms.openlocfilehash: 32d3f86a78001fce896f8cf282eb6854f31a54ab
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891382"
---
# <span data-ttu-id="f8fdc-103">Install-Package</span><span class="sxs-lookup"><span data-stu-id="f8fdc-103">Install-Package</span></span>

## <span data-ttu-id="f8fdc-104">概要</span><span class="sxs-lookup"><span data-stu-id="f8fdc-104">SYNOPSIS</span></span>
<span data-ttu-id="f8fdc-105">安裝一或多個軟體套件。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-105">Installs one or more software packages.</span></span>

## <span data-ttu-id="f8fdc-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f8fdc-106">SYNTAX</span></span>

### <span data-ttu-id="f8fdc-107">PackageBySearch (預設) </span><span class="sxs-lookup"><span data-stu-id="f8fdc-107">PackageBySearch (Default)</span></span>

```
Install-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Source <String[]>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="f8fdc-108">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="f8fdc-108">PackageByInputObject</span></span>

```
Install-Package [-InputObject] <SoftwareIdentity[]> [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="f8fdc-109">NuGet： PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="f8fdc-109">NuGet:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ConfigFile <String>]
 [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>] [-Contains <String>]
 [-AllowPrereleaseVersions] [-Destination <String>] [-ExcludeVersion] [-Scope <String>]
 [-SkipDependencies] [<CommonParameters>]
```

### <span data-ttu-id="f8fdc-110">NuGet： PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="f8fdc-110">NuGet:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ConfigFile <String>]
 [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>] [-Contains <String>]
 [-AllowPrereleaseVersions] [-Destination <String>] [-ExcludeVersion] [-Scope <String>]
 [-SkipDependencies] [<CommonParameters>]
```

### <span data-ttu-id="f8fdc-111">PowerShellGet： PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="f8fdc-111">PowerShellGet:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AllowPrereleaseVersions]
 [-Scope <String>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [<CommonParameters>]
```

### <span data-ttu-id="f8fdc-112">PowerShellGet： PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="f8fdc-112">PowerShellGet:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AllowPrereleaseVersions]
 [-Scope <String>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [<CommonParameters>]
```

## <span data-ttu-id="f8fdc-113">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f8fdc-113">DESCRIPTION</span></span>

<span data-ttu-id="f8fdc-114">`Install-Package`Cmdlet 會在本機電腦上安裝一或多個軟體套件。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-114">The `Install-Package` cmdlet installs one or more software packages on the local computer.</span></span> <span data-ttu-id="f8fdc-115">如果您有多個軟體來源，請使用 `Get-PackageProvider` 和 `Get-PackageSource` 來顯示關於提供者的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-115">If you have multiple software sources, use `Get-PackageProvider` and `Get-PackageSource` to display details about your providers.</span></span>

## <span data-ttu-id="f8fdc-116">範例</span><span class="sxs-lookup"><span data-stu-id="f8fdc-116">EXAMPLES</span></span>

### <span data-ttu-id="f8fdc-117">範例1：依封裝名稱安裝封裝</span><span class="sxs-lookup"><span data-stu-id="f8fdc-117">Example 1: Install a package by package name</span></span>

<span data-ttu-id="f8fdc-118">`Install-Package`Cmdlet 會安裝軟體套件及其相依性。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-118">The `Install-Package` cmdlet installs a software package and its dependencies.</span></span>

```
PS> Install-Package -Name NuGet.Core -Source MyNuGet -Credential Contoso\TestUser
```

<span data-ttu-id="f8fdc-119">`Install-Package` 使用參數來指定封裝 **名稱** 和 **來源**。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-119">`Install-Package` uses parameters to specify the packages **Name** and **Source**.</span></span> <span data-ttu-id="f8fdc-120">**Credential** 參數使用具有安裝套件許可權的網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-120">The **Credential** parameter uses a domain user account with permissions to install packages.</span></span> <span data-ttu-id="f8fdc-121">此命令會提示您輸入使用者帳戶密碼。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-121">The command prompts you for the user account password.</span></span>

### <span data-ttu-id="f8fdc-122">範例2：使用 Find-Package 安裝套件</span><span class="sxs-lookup"><span data-stu-id="f8fdc-122">Example 2: Use Find-Package to install a package</span></span>

<span data-ttu-id="f8fdc-123">在此範例中，所傳回的物件 `Find-Package` 會向下傳送管線並由安裝 `Install-Package` 。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-123">In this example, the object returned by `Find-Package` is sent down the pipeline and installed by `Install-Package`.</span></span>

```
PS> Find-Package -Name NuGet.Core -Source MyNuGet | Install-Package
```

<span data-ttu-id="f8fdc-124">`Find-Package` 使用 **名稱** 和 **來源** 參數來尋找封裝。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-124">`Find-Package` uses the **Name** and **Source** parameters to locate a package.</span></span> <span data-ttu-id="f8fdc-125">物件會沿著管線向下傳送，並 `Install-Package` 在本機電腦上安裝封裝。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-125">The object is sent down the pipeline and `Install-Package` installs the package on the local computer.</span></span>

### <span data-ttu-id="f8fdc-126">範例3：指定版本範圍來安裝封裝</span><span class="sxs-lookup"><span data-stu-id="f8fdc-126">Example 3: Install packages by specifying a range of versions</span></span>

<span data-ttu-id="f8fdc-127">`Install-Package` 使用 **MinimumVersion** 和 **MaximumVersion** 參數指定軟體版本的範圍。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-127">`Install-Package` uses the **MinimumVersion** and **MaximumVersion** parameters to specify a range of software versions.</span></span>

```
PS> Install-Package -Name NuGet.Core -Source MyNuGet -MinimumVersion 2.8.0 -MaximumVersion 2.9.0
```

<span data-ttu-id="f8fdc-128">`Install-Package` 使用 **名稱** 和 **來源** 參數來尋找封裝。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-128">`Install-Package` uses the **Name** and **Source** parameters to find a package.</span></span> <span data-ttu-id="f8fdc-129">**MinimumVersion** 和 **MaximumVersion** 參數會指定軟體版本的範圍。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-129">The **MinimumVersion** and **MaximumVersion** parameters specify a range of software versions.</span></span> <span data-ttu-id="f8fdc-130">已安裝範圍中的最高版本。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-130">The highest version in the range is installed.</span></span>

## <span data-ttu-id="f8fdc-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f8fdc-131">PARAMETERS</span></span>

### <span data-ttu-id="f8fdc-132">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="f8fdc-132">-AcceptLicense</span></span>

 <span data-ttu-id="f8fdc-133">**AcceptLicense** 會在安裝期間自動接受授權合約。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-133">**AcceptLicense** automatically accepts the license agreement during installation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f8fdc-134">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="f8fdc-134">-AllowClobber</span></span>

<span data-ttu-id="f8fdc-135">覆寫與現有命令衝突的警告訊息。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-135">Overrides warning messages about conflicts with existing commands.</span></span> <span data-ttu-id="f8fdc-136">覆寫與要安裝的命令同名的現有命令。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-136">Overwrites existing commands that have the same name as commands being installed.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f8fdc-137">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="f8fdc-137">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="f8fdc-138">允許安裝標記為發行前版本的套件。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-138">Allows the installation of packages marked as prerelease.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject, PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f8fdc-139">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="f8fdc-139">-AllVersions</span></span>

<span data-ttu-id="f8fdc-140">`Install-Package` 安裝所有可用的套件版本。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-140">`Install-Package` installs all available versions of the package.</span></span> <span data-ttu-id="f8fdc-141">依預設，只會安裝最新版本。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-141">By default, only the newest version is installed.</span></span>

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

### <span data-ttu-id="f8fdc-142">-Command</span><span class="sxs-lookup"><span data-stu-id="f8fdc-142">-Command</span></span>

<span data-ttu-id="f8fdc-143">指定一或多個搜尋的命令 `Install-Package` 。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-143">Specifies one or more commands that `Install-Package` searches.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f8fdc-144">-Read-configfile</span><span class="sxs-lookup"><span data-stu-id="f8fdc-144">-ConfigFile</span></span>

<span data-ttu-id="f8fdc-145">指定包含設定檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-145">Specifies a path that contains a configuration file.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f8fdc-146">-Contains</span><span class="sxs-lookup"><span data-stu-id="f8fdc-146">-Contains</span></span>

<span data-ttu-id="f8fdc-147">`Install-Package` 如果 **Contains** 參數指定的值符合物件的任何屬性值，就會取得物件。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-147">`Install-Package` gets objects if the **Contains** parameter specifies a value that matches any of the object's property values.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f8fdc-148">-Credential</span><span class="sxs-lookup"><span data-stu-id="f8fdc-148">-Credential</span></span>

<span data-ttu-id="f8fdc-149">指定擁有存取電腦和執行命令之許可權的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-149">Specifies a user account that has permission to access the computer and run commands.</span></span> <span data-ttu-id="f8fdc-150">輸入使用者名稱（例如 **User01**、 **Domain01\User01**），或輸入由 Cmdlet 產生的 **PSCredential** 物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-150">Type a user name, such as **User01**, **Domain01\User01**, or enter a **PSCredential** object, generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="f8fdc-151">如果您輸入使用者名稱，系統就會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-151">If you type a user name, you're prompted for a password.</span></span>

<span data-ttu-id="f8fdc-152">如果未指定 **Credential** 參數，會 `Install-Package` 使用目前的使用者。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-152">When the **Credential** parameter isn't specified, `Install-Package` uses the current user.</span></span>

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

### <span data-ttu-id="f8fdc-153">-Destination</span><span class="sxs-lookup"><span data-stu-id="f8fdc-153">-Destination</span></span>

<span data-ttu-id="f8fdc-154">指定輸入物件的路徑。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-154">Specifies a path to an input object.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f8fdc-155">-DscResource</span><span class="sxs-lookup"><span data-stu-id="f8fdc-155">-DscResource</span></span>

<span data-ttu-id="f8fdc-156">指定要搜尋的一或多個 Desired State Configuration (DSC) 資源 `Install-Package` 。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-156">Specifies one or more Desired State Configuration (DSC) resources that are searched by `Install-Package`.</span></span> <span data-ttu-id="f8fdc-157">使用 `Find-DscResource` Cmdlet 來尋找 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-157">Use the `Find-DscResource` cmdlet to find DSC resources.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f8fdc-158">-ExcludeVersion</span><span class="sxs-lookup"><span data-stu-id="f8fdc-158">-ExcludeVersion</span></span>

<span data-ttu-id="f8fdc-159">切換以排除資料夾路徑中的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-159">Switch to exclude the version number in the folder path.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f8fdc-160">-Filter</span><span class="sxs-lookup"><span data-stu-id="f8fdc-160">-Filter</span></span>

<span data-ttu-id="f8fdc-161">指定要在 [ **名稱** ] 和 [ **描述** ] 屬性內搜尋的字詞。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-161">Specifies terms to search for within the **Name** and **Description** properties.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f8fdc-162">-FilterOnTag</span><span class="sxs-lookup"><span data-stu-id="f8fdc-162">-FilterOnTag</span></span>

<span data-ttu-id="f8fdc-163">指定篩選結果並排除不包含指定標記之結果的標記。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-163">Specifies a tag that filters results and excludes results that don't contain the specified tag.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f8fdc-164">-Force</span><span class="sxs-lookup"><span data-stu-id="f8fdc-164">-Force</span></span>

<span data-ttu-id="f8fdc-165">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-165">Forces the command to run without asking for user confirmation.</span></span> <span data-ttu-id="f8fdc-166">覆寫防止 `Install-Package` 無法成功的限制，但安全性除外。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-166">Overrides restrictions that prevent `Install-Package` from succeeding, with the exception of security.</span></span>

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

### <span data-ttu-id="f8fdc-167">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="f8fdc-167">-ForceBootstrap</span></span>

<span data-ttu-id="f8fdc-168">強制 **PackageManagement** 自動安裝指定套件的封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-168">Forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="f8fdc-169">-Headers</span><span class="sxs-lookup"><span data-stu-id="f8fdc-169">-Headers</span></span>

<span data-ttu-id="f8fdc-170">指定封裝標頭。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-170">Specifies the package headers.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f8fdc-171">-Include</span><span class="sxs-lookup"><span data-stu-id="f8fdc-171">-Includes</span></span>

<span data-ttu-id="f8fdc-172">指定是否 `Install-Package` 應該尋找所有套件類型。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-172">Specifies whether `Install-Package` should find all package types.</span></span> <span data-ttu-id="f8fdc-173">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="f8fdc-173">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="f8fdc-174">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f8fdc-174">Cmdlet</span></span>
- <span data-ttu-id="f8fdc-175">DscResource</span><span class="sxs-lookup"><span data-stu-id="f8fdc-175">DscResource</span></span>
- <span data-ttu-id="f8fdc-176">函式</span><span class="sxs-lookup"><span data-stu-id="f8fdc-176">Function</span></span>
- <span data-ttu-id="f8fdc-177">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="f8fdc-177">RoleCapability</span></span>
- <span data-ttu-id="f8fdc-178">工作流程</span><span class="sxs-lookup"><span data-stu-id="f8fdc-178">Workflow</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:
Accepted values: Cmdlet, DscResource, Function, RoleCapability, Workflow

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f8fdc-179">-InputObject</span><span class="sxs-lookup"><span data-stu-id="f8fdc-179">-InputObject</span></span>

<span data-ttu-id="f8fdc-180">接受管線輸入。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-180">Accepts pipeline input.</span></span> <span data-ttu-id="f8fdc-181">使用封裝的 **SoftwareIdentity** 類型指定封裝。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-181">Specifies a package by using the package's **SoftwareIdentity** type.</span></span>
<span data-ttu-id="f8fdc-182">`Find-Package` 輸出 **SoftwareIdentity** 物件。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-182">`Find-Package` outputs a **SoftwareIdentity** object.</span></span>

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

### <span data-ttu-id="f8fdc-183">-InstallUpdate</span><span class="sxs-lookup"><span data-stu-id="f8fdc-183">-InstallUpdate</span></span>

<span data-ttu-id="f8fdc-184">指出會 `Install-Package` 安裝更新。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-184">Indicates that `Install-Package` installs updates.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f8fdc-185">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="f8fdc-185">-MaximumVersion</span></span>

<span data-ttu-id="f8fdc-186">指定您想要安裝的最大允許套件版本。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-186">Specifies the maximum allowed package version that you want to install.</span></span> <span data-ttu-id="f8fdc-187">如果您未指定此參數，則會 `Install-Package` 安裝套件的最新版本。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-187">If you don't specify this parameter, `Install-Package` installs the package's newest version.</span></span>

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

### <span data-ttu-id="f8fdc-188">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="f8fdc-188">-MinimumVersion</span></span>

<span data-ttu-id="f8fdc-189">指定您想要安裝的最小允許套件版本。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-189">Specifies the minimum allowed package version that you want to install.</span></span> <span data-ttu-id="f8fdc-190">如果您未新增此參數，則會 `Install-Package` 安裝套件的最新版本，以滿足 **MaximumVersion** 參數所指定的任何版本。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-190">If you don't add this parameter, `Install-Package` installs the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="f8fdc-191">-Name</span><span class="sxs-lookup"><span data-stu-id="f8fdc-191">-Name</span></span>

<span data-ttu-id="f8fdc-192">指定一或多個封裝名稱。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-192">Specifies one or more package names.</span></span> <span data-ttu-id="f8fdc-193">多個封裝名稱必須以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-193">Multiple package names must be separated by commas.</span></span>

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

### <span data-ttu-id="f8fdc-194">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="f8fdc-194">-NoPathUpdate</span></span>

<span data-ttu-id="f8fdc-195">**NoPathUpdate** 僅適用于 `Install-Script` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-195">**NoPathUpdate** only applies to the `Install-Script` cmdlet.</span></span> <span data-ttu-id="f8fdc-196">**NoPathUpdate** 是提供者所加入的動態參數，而且不受支援 `Install-Package` 。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-196">**NoPathUpdate** is a dynamic parameter added by the provider and isn't supported by `Install-Package`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f8fdc-197">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="f8fdc-197">-PackageManagementProvider</span></span>

<span data-ttu-id="f8fdc-198">指定 **PackageManagement** 提供者的名稱。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-198">Specifies the name of the **PackageManagement** provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f8fdc-199">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="f8fdc-199">-ProviderName</span></span>

<span data-ttu-id="f8fdc-200">指定要將套件搜尋範圍限定在其中的一或多個套件提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-200">Specifies one or more package provider names to which to scope your package search.</span></span> <span data-ttu-id="f8fdc-201">您可以執行 `Get-PackageProvider` 來取得套件提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-201">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>

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

### <span data-ttu-id="f8fdc-202">-Proxy</span><span class="sxs-lookup"><span data-stu-id="f8fdc-202">-Proxy</span></span>

<span data-ttu-id="f8fdc-203">指定要求的 proxy 伺服器，而不是直接連接到網際網路資源。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-203">Specifies a proxy server for the request, rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="f8fdc-204">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="f8fdc-204">-ProxyCredential</span></span>

<span data-ttu-id="f8fdc-205">指定擁有使用 **proxy** 參數所指定 proxy 伺服器之許可權的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-205">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="f8fdc-206">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="f8fdc-206">-PublishLocation</span></span>

<span data-ttu-id="f8fdc-207">指定封裝發佈位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-207">Specifies the path to a package's published location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f8fdc-208">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="f8fdc-208">-RequiredVersion</span></span>

<span data-ttu-id="f8fdc-209">指定您想要安裝之套件的確切允許版本。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-209">Specifies the exact allowed version of the package that you want to install.</span></span> <span data-ttu-id="f8fdc-210">如果您未新增此參數，則會 `Install-Package` 安裝套件的最新版本，以滿足 **MaximumVersion** 參數所指定的任何版本。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-210">If you don't add this parameter, `Install-Package` installs the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="f8fdc-211">-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="f8fdc-211">-RoleCapability</span></span>

<span data-ttu-id="f8fdc-212">指定角色功能的陣列。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-212">Specifies an array of role capabilities.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f8fdc-213">-Scope</span><span class="sxs-lookup"><span data-stu-id="f8fdc-213">-Scope</span></span>

<span data-ttu-id="f8fdc-214">指定要安裝套件的範圍。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-214">Specifies the scope for which to install the package.</span></span> <span data-ttu-id="f8fdc-215">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="f8fdc-215">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="f8fdc-216">CurrentUser</span><span class="sxs-lookup"><span data-stu-id="f8fdc-216">CurrentUser</span></span>
- <span data-ttu-id="f8fdc-217">AllUsers</span><span class="sxs-lookup"><span data-stu-id="f8fdc-217">AllUsers</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject, PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f8fdc-218">->scriptpublishlocation</span><span class="sxs-lookup"><span data-stu-id="f8fdc-218">-ScriptPublishLocation</span></span>

<span data-ttu-id="f8fdc-219">指定腳本發佈位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-219">Specifies the path to a script's published location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f8fdc-220">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="f8fdc-220">-ScriptSourceLocation</span></span>

<span data-ttu-id="f8fdc-221">指定腳本來源位置。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-221">Specifies the script source location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f8fdc-222">-SkipDependencies</span><span class="sxs-lookup"><span data-stu-id="f8fdc-222">-SkipDependencies</span></span>

<span data-ttu-id="f8fdc-223">略過軟體相依性的安裝。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-223">Skips the installation of software dependencies.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f8fdc-224">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="f8fdc-224">-SkipPublisherCheck</span></span>

<span data-ttu-id="f8fdc-225">可讓您取得比已安裝版本還新的套件版本。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-225">Allows you to get a package version that is newer than your installed version.</span></span> <span data-ttu-id="f8fdc-226">例如，已安裝的套件已由受信任的發行者進行數位簽署，但新版本未經過數位簽署。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-226">For example, an installed package that is digitally signed by a trusted publisher but a new version isn't digitally signed.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f8fdc-227">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="f8fdc-227">-SkipValidate</span></span>

<span data-ttu-id="f8fdc-228">略過驗證封裝認證的參數。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-228">Switch that skips validating the credentials of a package.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f8fdc-229">-Source</span><span class="sxs-lookup"><span data-stu-id="f8fdc-229">-Source</span></span>

<span data-ttu-id="f8fdc-230">指定一或多個套件來源。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-230">Specifies one or more package sources.</span></span> <span data-ttu-id="f8fdc-231">多個套件來源名稱必須以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-231">Multiple package source names must be separated by commas.</span></span>
<span data-ttu-id="f8fdc-232">您可以藉由執行 Cmdlet 來取得套件來源名稱 `Get-PackageSource` 。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-232">You can get package source names by running the `Get-PackageSource` cmdlet.</span></span>

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

### <span data-ttu-id="f8fdc-233">-Tag</span><span class="sxs-lookup"><span data-stu-id="f8fdc-233">-Tag</span></span>

<span data-ttu-id="f8fdc-234">指定要在套件中繼資料中搜尋的一或多個字串。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-234">Specifies one or more strings to search for in the package metadata.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f8fdc-235">-Type</span><span class="sxs-lookup"><span data-stu-id="f8fdc-235">-Type</span></span>

<span data-ttu-id="f8fdc-236">指定是否要使用模組、腳本或兩者來搜尋封裝。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-236">Specifies whether to search for packages with a module, a script, or both.</span></span> <span data-ttu-id="f8fdc-237">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="f8fdc-237">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="f8fdc-238">模組</span><span class="sxs-lookup"><span data-stu-id="f8fdc-238">Module</span></span>
- <span data-ttu-id="f8fdc-239">指令碼</span><span class="sxs-lookup"><span data-stu-id="f8fdc-239">Script</span></span>
- <span data-ttu-id="f8fdc-240">全部</span><span class="sxs-lookup"><span data-stu-id="f8fdc-240">All</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:
Accepted values: Module, Script, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f8fdc-241">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f8fdc-241">-Confirm</span></span>

<span data-ttu-id="f8fdc-242">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-242">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f8fdc-243">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f8fdc-243">-WhatIf</span></span>

<span data-ttu-id="f8fdc-244">顯示執行 Cmdlet 時會發生 `Install-Package` 的情況。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-244">Shows what would happen if `Install-Package` cmdlet is run.</span></span> <span data-ttu-id="f8fdc-245">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-245">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f8fdc-246">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f8fdc-246">CommonParameters</span></span>

<span data-ttu-id="f8fdc-247">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-247">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f8fdc-248">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-248">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f8fdc-249">輸入</span><span class="sxs-lookup"><span data-stu-id="f8fdc-249">INPUTS</span></span>

### <span data-ttu-id="f8fdc-250">`Install-Package` 接受來自管線的輸入。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-250">`Install-Package` accepts input from the pipeline.</span></span>

## <span data-ttu-id="f8fdc-251">輸出</span><span class="sxs-lookup"><span data-stu-id="f8fdc-251">OUTPUTS</span></span>

### <span data-ttu-id="f8fdc-252">SoftwareIdentity[]</span><span class="sxs-lookup"><span data-stu-id="f8fdc-252">SoftwareIdentity[]</span></span>

## <span data-ttu-id="f8fdc-253">注意</span><span class="sxs-lookup"><span data-stu-id="f8fdc-253">NOTES</span></span>

<span data-ttu-id="f8fdc-254">在命令中包含封裝提供者可以讓 Cmdlet 提供動態參數。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-254">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="f8fdc-255">動態參數是封裝提供者專用的。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-255">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="f8fdc-256">此 `Get-Help` Cmdlet 會列出 Cmdlet 的參數集，並包含提供者的參數集。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-256">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span> <span data-ttu-id="f8fdc-257">例如， `Install-Package` 具有 **PowerShellGet** 參數集，其中包含 `-NoPathUpdate` 、 `AllowClobber` 和 `SkipPublisherCheck` 。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-257">For example, `Install-Package` has the **PowerShellGet** parameter set that includes `-NoPathUpdate`, `AllowClobber`, and `SkipPublisherCheck`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f8fdc-258">從2020年4月起，PowerShell 資源庫不再支援傳輸層安全性 (TLS) 1.0 和1.1 版。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-258">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="f8fdc-259">如果您不是使用 TLS 1.2 或更高版本，當您嘗試存取 PowerShell 資源庫時，將會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-259">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="f8fdc-260">使用下列命令，以確保您使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="f8fdc-260">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="f8fdc-261">如需詳細資訊，請參閱 PowerShell blog 中的 [公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 。</span><span class="sxs-lookup"><span data-stu-id="f8fdc-261">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="f8fdc-262">相關連結</span><span class="sxs-lookup"><span data-stu-id="f8fdc-262">RELATED LINKS</span></span>

[<span data-ttu-id="f8fdc-263">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="f8fdc-263">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="f8fdc-264">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="f8fdc-264">Find-DscResource</span></span>](../PowershellGet/Find-DscResource.md)

[<span data-ttu-id="f8fdc-265">Get-Help</span><span class="sxs-lookup"><span data-stu-id="f8fdc-265">Get-Help</span></span>](../Microsoft.PowerShell.Core/Get-Help.md)

[<span data-ttu-id="f8fdc-266">Get-Package</span><span class="sxs-lookup"><span data-stu-id="f8fdc-266">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="f8fdc-267">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="f8fdc-267">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="f8fdc-268">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="f8fdc-268">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="f8fdc-269">Find-Package</span><span class="sxs-lookup"><span data-stu-id="f8fdc-269">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="f8fdc-270">Save-Package</span><span class="sxs-lookup"><span data-stu-id="f8fdc-270">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="f8fdc-271">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="f8fdc-271">Uninstall-Package</span></span>](Uninstall-Package.md)
