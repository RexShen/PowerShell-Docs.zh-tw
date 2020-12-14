---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 05/23/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-package?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Package
ms.openlocfilehash: 9fcf71462e1bf411f3c7c5d8322e6b6f3a667b9f
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892809"
---
# <span data-ttu-id="1c64d-103">Install-Package</span><span class="sxs-lookup"><span data-stu-id="1c64d-103">Install-Package</span></span>

## <span data-ttu-id="1c64d-104">概要</span><span class="sxs-lookup"><span data-stu-id="1c64d-104">SYNOPSIS</span></span>
<span data-ttu-id="1c64d-105">安裝一或多個軟體套件。</span><span class="sxs-lookup"><span data-stu-id="1c64d-105">Installs one or more software packages.</span></span>

## <span data-ttu-id="1c64d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1c64d-106">SYNTAX</span></span>

### <span data-ttu-id="1c64d-107">PackageBySearch (預設) </span><span class="sxs-lookup"><span data-stu-id="1c64d-107">PackageBySearch (Default)</span></span>

```
Install-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Source <String[]>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="1c64d-108">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="1c64d-108">PackageByInputObject</span></span>

```
Install-Package [-InputObject] <SoftwareIdentity[]> [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="1c64d-109">程式： PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="1c64d-109">Programs:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-IncludeWindowsInstaller]
 [-IncludeSystemComponent] [<CommonParameters>]
```

### <span data-ttu-id="1c64d-110">程式： PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="1c64d-110">Programs:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-IncludeWindowsInstaller]
 [-IncludeSystemComponent] [<CommonParameters>]
```

### <span data-ttu-id="1c64d-111">msi： PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="1c64d-111">msi:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AdditionalArguments <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="1c64d-112">msi： PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="1c64d-112">msi:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AdditionalArguments <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="1c64d-113">NuGet： PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="1c64d-113">NuGet:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ConfigFile <String>]
 [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>] [-Contains <String>]
 [-AllowPrereleaseVersions] [-Destination <String>] [-ExcludeVersion] [-Scope <String>]
 [-SkipDependencies] [<CommonParameters>]
```

### <span data-ttu-id="1c64d-114">NuGet： PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="1c64d-114">NuGet:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ConfigFile <String>]
 [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>] [-Contains <String>]
 [-AllowPrereleaseVersions] [-Destination <String>] [-ExcludeVersion] [-Scope <String>]
 [-SkipDependencies] [<CommonParameters>]
```

### <span data-ttu-id="1c64d-115">PowerShellGet： PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="1c64d-115">PowerShellGet:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AllowPrereleaseVersions]
 [-Scope <String>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [<CommonParameters>]
```

### <span data-ttu-id="1c64d-116">PowerShellGet： PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="1c64d-116">PowerShellGet:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AllowPrereleaseVersions]
 [-Scope <String>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [<CommonParameters>]
```

## <span data-ttu-id="1c64d-117">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="1c64d-117">DESCRIPTION</span></span>

<span data-ttu-id="1c64d-118">`Install-Package`Cmdlet 會在本機電腦上安裝一或多個軟體套件。</span><span class="sxs-lookup"><span data-stu-id="1c64d-118">The `Install-Package` cmdlet installs one or more software packages on the local computer.</span></span> <span data-ttu-id="1c64d-119">如果您有多個軟體來源，請使用 `Get-PackageProvider` 和 `Get-PackageSource` 來顯示關於提供者的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="1c64d-119">If you have multiple software sources, use `Get-PackageProvider` and `Get-PackageSource` to display details about your providers.</span></span>

## <span data-ttu-id="1c64d-120">範例</span><span class="sxs-lookup"><span data-stu-id="1c64d-120">EXAMPLES</span></span>

### <span data-ttu-id="1c64d-121">範例1：依封裝名稱安裝封裝</span><span class="sxs-lookup"><span data-stu-id="1c64d-121">Example 1: Install a package by package name</span></span>

<span data-ttu-id="1c64d-122">`Install-Package`Cmdlet 會安裝軟體套件及其相依性。</span><span class="sxs-lookup"><span data-stu-id="1c64d-122">The `Install-Package` cmdlet installs a software package and its dependencies.</span></span>

```
PS> Install-Package -Name NuGet.Core -Source MyNuGet -Credential Contoso\TestUser
```

<span data-ttu-id="1c64d-123">`Install-Package` 使用參數來指定封裝 **名稱** 和 **來源**。</span><span class="sxs-lookup"><span data-stu-id="1c64d-123">`Install-Package` uses parameters to specify the packages **Name** and **Source**.</span></span> <span data-ttu-id="1c64d-124">**Credential** 參數使用具有安裝套件許可權的網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="1c64d-124">The **Credential** parameter uses a domain user account with permissions to install packages.</span></span> <span data-ttu-id="1c64d-125">此命令會提示您輸入使用者帳戶密碼。</span><span class="sxs-lookup"><span data-stu-id="1c64d-125">The command prompts you for the user account password.</span></span>

### <span data-ttu-id="1c64d-126">範例2：使用 Find-Package 安裝套件</span><span class="sxs-lookup"><span data-stu-id="1c64d-126">Example 2: Use Find-Package to install a package</span></span>

<span data-ttu-id="1c64d-127">在此範例中，所傳回的物件 `Find-Package` 會向下傳送管線並由安裝 `Install-Package` 。</span><span class="sxs-lookup"><span data-stu-id="1c64d-127">In this example, the object returned by `Find-Package` is sent down the pipeline and installed by `Install-Package`.</span></span>

```
PS> Find-Package -Name NuGet.Core -Source MyNuGet | Install-Package
```

<span data-ttu-id="1c64d-128">`Find-Package` 使用 **名稱** 和 **來源** 參數來尋找封裝。</span><span class="sxs-lookup"><span data-stu-id="1c64d-128">`Find-Package` uses the **Name** and **Source** parameters to locate a package.</span></span> <span data-ttu-id="1c64d-129">物件會沿著管線向下傳送，並 `Install-Package` 在本機電腦上安裝封裝。</span><span class="sxs-lookup"><span data-stu-id="1c64d-129">The object is sent down the pipeline and `Install-Package` installs the package on the local computer.</span></span>

### <span data-ttu-id="1c64d-130">範例3：指定版本範圍來安裝封裝</span><span class="sxs-lookup"><span data-stu-id="1c64d-130">Example 3: Install packages by specifying a range of versions</span></span>

<span data-ttu-id="1c64d-131">`Install-Package` 使用 **MinimumVersion** 和 **MaximumVersion** 參數指定軟體版本的範圍。</span><span class="sxs-lookup"><span data-stu-id="1c64d-131">`Install-Package` uses the **MinimumVersion** and **MaximumVersion** parameters to specify a range of software versions.</span></span>

```
PS> Install-Package -Name NuGet.Core -Source MyNuGet -MinimumVersion 2.8.0 -MaximumVersion 2.9.0
```

<span data-ttu-id="1c64d-132">`Install-Package` 使用 **名稱** 和 **來源** 參數來尋找封裝。</span><span class="sxs-lookup"><span data-stu-id="1c64d-132">`Install-Package` uses the **Name** and **Source** parameters to find a package.</span></span> <span data-ttu-id="1c64d-133">**MinimumVersion** 和 **MaximumVersion** 參數會指定軟體版本的範圍。</span><span class="sxs-lookup"><span data-stu-id="1c64d-133">The **MinimumVersion** and **MaximumVersion** parameters specify a range of software versions.</span></span> <span data-ttu-id="1c64d-134">已安裝範圍中的最高版本。</span><span class="sxs-lookup"><span data-stu-id="1c64d-134">The highest version in the range is installed.</span></span>

## <span data-ttu-id="1c64d-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1c64d-135">PARAMETERS</span></span>

### <span data-ttu-id="1c64d-136">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="1c64d-136">-AcceptLicense</span></span>

 <span data-ttu-id="1c64d-137">**AcceptLicense** 會在安裝期間自動接受授權合約。</span><span class="sxs-lookup"><span data-stu-id="1c64d-137">**AcceptLicense** automatically accepts the license agreement during installation.</span></span>

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

### <span data-ttu-id="1c64d-138">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="1c64d-138">-AllowClobber</span></span>

<span data-ttu-id="1c64d-139">覆寫與現有命令衝突的警告訊息。</span><span class="sxs-lookup"><span data-stu-id="1c64d-139">Overrides warning messages about conflicts with existing commands.</span></span> <span data-ttu-id="1c64d-140">覆寫與要安裝的命令同名的現有命令。</span><span class="sxs-lookup"><span data-stu-id="1c64d-140">Overwrites existing commands that have the same name as commands being installed.</span></span>

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

### <span data-ttu-id="1c64d-141">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="1c64d-141">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="1c64d-142">允許安裝標記為發行前版本的套件。</span><span class="sxs-lookup"><span data-stu-id="1c64d-142">Allows the installation of packages marked as prerelease.</span></span>

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

### <span data-ttu-id="1c64d-143">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="1c64d-143">-AllVersions</span></span>

<span data-ttu-id="1c64d-144">`Install-Package` 安裝所有可用的套件版本。</span><span class="sxs-lookup"><span data-stu-id="1c64d-144">`Install-Package` installs all available versions of the package.</span></span> <span data-ttu-id="1c64d-145">依預設，只會安裝最新版本。</span><span class="sxs-lookup"><span data-stu-id="1c64d-145">By default, only the newest version is installed.</span></span>

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

### <span data-ttu-id="1c64d-146">-Command</span><span class="sxs-lookup"><span data-stu-id="1c64d-146">-Command</span></span>

<span data-ttu-id="1c64d-147">指定一或多個搜尋的命令 `Install-Package` 。</span><span class="sxs-lookup"><span data-stu-id="1c64d-147">Specifies one or more commands that `Install-Package` searches.</span></span>

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

### <span data-ttu-id="1c64d-148">-Read-configfile</span><span class="sxs-lookup"><span data-stu-id="1c64d-148">-ConfigFile</span></span>

<span data-ttu-id="1c64d-149">指定包含設定檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="1c64d-149">Specifies a path that contains a configuration file.</span></span>

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

### <span data-ttu-id="1c64d-150">-Contains</span><span class="sxs-lookup"><span data-stu-id="1c64d-150">-Contains</span></span>

<span data-ttu-id="1c64d-151">`Install-Package` 如果 **Contains** 參數指定的值符合物件的任何屬性值，就會取得物件。</span><span class="sxs-lookup"><span data-stu-id="1c64d-151">`Install-Package` gets objects if the **Contains** parameter specifies a value that matches any of the object's property values.</span></span>

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

### <span data-ttu-id="1c64d-152">-Credential</span><span class="sxs-lookup"><span data-stu-id="1c64d-152">-Credential</span></span>

<span data-ttu-id="1c64d-153">指定擁有存取電腦和執行命令之許可權的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="1c64d-153">Specifies a user account that has permission to access the computer and run commands.</span></span> <span data-ttu-id="1c64d-154">輸入使用者名稱（例如 **User01**、 **Domain01\User01**），或輸入由 Cmdlet 產生的 **PSCredential** 物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="1c64d-154">Type a user name, such as **User01**, **Domain01\User01**, or enter a **PSCredential** object, generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="1c64d-155">如果您輸入使用者名稱，系統就會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="1c64d-155">If you type a user name, you're prompted for a password.</span></span>

<span data-ttu-id="1c64d-156">如果未指定 **Credential** 參數，會 `Install-Package` 使用目前的使用者。</span><span class="sxs-lookup"><span data-stu-id="1c64d-156">When the **Credential** parameter isn't specified, `Install-Package` uses the current user.</span></span>

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

### <span data-ttu-id="1c64d-157">-Destination</span><span class="sxs-lookup"><span data-stu-id="1c64d-157">-Destination</span></span>

<span data-ttu-id="1c64d-158">指定輸入物件的路徑。</span><span class="sxs-lookup"><span data-stu-id="1c64d-158">Specifies a path to an input object.</span></span>

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

### <span data-ttu-id="1c64d-159">-DscResource</span><span class="sxs-lookup"><span data-stu-id="1c64d-159">-DscResource</span></span>

<span data-ttu-id="1c64d-160">指定要搜尋的一或多個 Desired State Configuration (DSC) 資源 `Install-Package` 。</span><span class="sxs-lookup"><span data-stu-id="1c64d-160">Specifies one or more Desired State Configuration (DSC) resources that are searched by `Install-Package`.</span></span> <span data-ttu-id="1c64d-161">使用 `Find-DscResource` Cmdlet 來尋找 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="1c64d-161">Use the `Find-DscResource` cmdlet to find DSC resources.</span></span>

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

### <span data-ttu-id="1c64d-162">-ExcludeVersion</span><span class="sxs-lookup"><span data-stu-id="1c64d-162">-ExcludeVersion</span></span>

<span data-ttu-id="1c64d-163">切換以排除資料夾路徑中的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="1c64d-163">Switch to exclude the version number in the folder path.</span></span>

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

### <span data-ttu-id="1c64d-164">-Filter</span><span class="sxs-lookup"><span data-stu-id="1c64d-164">-Filter</span></span>

<span data-ttu-id="1c64d-165">指定要在 [ **名稱** ] 和 [ **描述** ] 屬性內搜尋的字詞。</span><span class="sxs-lookup"><span data-stu-id="1c64d-165">Specifies terms to search for within the **Name** and **Description** properties.</span></span>

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

### <span data-ttu-id="1c64d-166">-FilterOnTag</span><span class="sxs-lookup"><span data-stu-id="1c64d-166">-FilterOnTag</span></span>

<span data-ttu-id="1c64d-167">指定篩選結果並排除不包含指定標記之結果的標記。</span><span class="sxs-lookup"><span data-stu-id="1c64d-167">Specifies a tag that filters results and excludes results that don't contain the specified tag.</span></span>

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

### <span data-ttu-id="1c64d-168">-Force</span><span class="sxs-lookup"><span data-stu-id="1c64d-168">-Force</span></span>

<span data-ttu-id="1c64d-169">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="1c64d-169">Forces the command to run without asking for user confirmation.</span></span> <span data-ttu-id="1c64d-170">覆寫防止 `Install-Package` 無法成功的限制，但安全性除外。</span><span class="sxs-lookup"><span data-stu-id="1c64d-170">Overrides restrictions that prevent `Install-Package` from succeeding, with the exception of security.</span></span>

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

### <span data-ttu-id="1c64d-171">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="1c64d-171">-ForceBootstrap</span></span>

<span data-ttu-id="1c64d-172">強制 **PackageManagement** 自動安裝指定套件的封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="1c64d-172">Forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="1c64d-173">-Headers</span><span class="sxs-lookup"><span data-stu-id="1c64d-173">-Headers</span></span>

<span data-ttu-id="1c64d-174">指定封裝標頭。</span><span class="sxs-lookup"><span data-stu-id="1c64d-174">Specifies the package headers.</span></span>

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

### <span data-ttu-id="1c64d-175">-Include</span><span class="sxs-lookup"><span data-stu-id="1c64d-175">-Includes</span></span>

<span data-ttu-id="1c64d-176">指定是否 `Install-Package` 應該尋找所有套件類型。</span><span class="sxs-lookup"><span data-stu-id="1c64d-176">Specifies whether `Install-Package` should find all package types.</span></span> <span data-ttu-id="1c64d-177">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="1c64d-177">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="1c64d-178">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1c64d-178">Cmdlet</span></span>
- <span data-ttu-id="1c64d-179">DscResource</span><span class="sxs-lookup"><span data-stu-id="1c64d-179">DscResource</span></span>
- <span data-ttu-id="1c64d-180">函式</span><span class="sxs-lookup"><span data-stu-id="1c64d-180">Function</span></span>
- <span data-ttu-id="1c64d-181">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="1c64d-181">RoleCapability</span></span>
- <span data-ttu-id="1c64d-182">工作流程</span><span class="sxs-lookup"><span data-stu-id="1c64d-182">Workflow</span></span>

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

### <span data-ttu-id="1c64d-183">-InputObject</span><span class="sxs-lookup"><span data-stu-id="1c64d-183">-InputObject</span></span>

<span data-ttu-id="1c64d-184">接受管線輸入。</span><span class="sxs-lookup"><span data-stu-id="1c64d-184">Accepts pipeline input.</span></span> <span data-ttu-id="1c64d-185">使用封裝的 **SoftwareIdentity** 類型指定封裝。</span><span class="sxs-lookup"><span data-stu-id="1c64d-185">Specifies a package by using the package's **SoftwareIdentity** type.</span></span>
<span data-ttu-id="1c64d-186">`Find-Package` 輸出 **SoftwareIdentity** 物件。</span><span class="sxs-lookup"><span data-stu-id="1c64d-186">`Find-Package` outputs a **SoftwareIdentity** object.</span></span>

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

### <span data-ttu-id="1c64d-187">-InstallUpdate</span><span class="sxs-lookup"><span data-stu-id="1c64d-187">-InstallUpdate</span></span>

<span data-ttu-id="1c64d-188">指出會 `Install-Package` 安裝更新。</span><span class="sxs-lookup"><span data-stu-id="1c64d-188">Indicates that `Install-Package` installs updates.</span></span>

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

### <span data-ttu-id="1c64d-189">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="1c64d-189">-MaximumVersion</span></span>

<span data-ttu-id="1c64d-190">指定您想要安裝的最大允許套件版本。</span><span class="sxs-lookup"><span data-stu-id="1c64d-190">Specifies the maximum allowed package version that you want to install.</span></span> <span data-ttu-id="1c64d-191">如果您未指定此參數，則會 `Install-Package` 安裝套件的最新版本。</span><span class="sxs-lookup"><span data-stu-id="1c64d-191">If you don't specify this parameter, `Install-Package` installs the package's newest version.</span></span>

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

### <span data-ttu-id="1c64d-192">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="1c64d-192">-MinimumVersion</span></span>

<span data-ttu-id="1c64d-193">指定您想要安裝的最小允許套件版本。</span><span class="sxs-lookup"><span data-stu-id="1c64d-193">Specifies the minimum allowed package version that you want to install.</span></span> <span data-ttu-id="1c64d-194">如果您未新增此參數，則會 `Install-Package` 安裝套件的最新版本，以滿足 **MaximumVersion** 參數所指定的任何版本。</span><span class="sxs-lookup"><span data-stu-id="1c64d-194">If you don't add this parameter, `Install-Package` installs the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="1c64d-195">-Name</span><span class="sxs-lookup"><span data-stu-id="1c64d-195">-Name</span></span>

<span data-ttu-id="1c64d-196">指定一或多個封裝名稱。</span><span class="sxs-lookup"><span data-stu-id="1c64d-196">Specifies one or more package names.</span></span> <span data-ttu-id="1c64d-197">多個封裝名稱必須以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="1c64d-197">Multiple package names must be separated by commas.</span></span>

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

### <span data-ttu-id="1c64d-198">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="1c64d-198">-NoPathUpdate</span></span>

<span data-ttu-id="1c64d-199">**NoPathUpdate** 僅適用于 `Install-Script` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1c64d-199">**NoPathUpdate** only applies to the `Install-Script` cmdlet.</span></span> <span data-ttu-id="1c64d-200">**NoPathUpdate** 是提供者所加入的動態參數，而且不受支援 `Install-Package` 。</span><span class="sxs-lookup"><span data-stu-id="1c64d-200">**NoPathUpdate** is a dynamic parameter added by the provider and isn't supported by `Install-Package`.</span></span>

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

### <span data-ttu-id="1c64d-201">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="1c64d-201">-PackageManagementProvider</span></span>

<span data-ttu-id="1c64d-202">指定 **PackageManagement** 提供者的名稱。</span><span class="sxs-lookup"><span data-stu-id="1c64d-202">Specifies the name of the **PackageManagement** provider.</span></span>

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

### <span data-ttu-id="1c64d-203">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="1c64d-203">-ProviderName</span></span>

<span data-ttu-id="1c64d-204">指定要將套件搜尋範圍限定在其中的一或多個套件提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="1c64d-204">Specifies one or more package provider names to which to scope your package search.</span></span> <span data-ttu-id="1c64d-205">您可以執行 `Get-PackageProvider` 來取得套件提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="1c64d-205">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>

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

### <span data-ttu-id="1c64d-206">-Proxy</span><span class="sxs-lookup"><span data-stu-id="1c64d-206">-Proxy</span></span>

<span data-ttu-id="1c64d-207">指定要求的 proxy 伺服器，而不是直接連接到網際網路資源。</span><span class="sxs-lookup"><span data-stu-id="1c64d-207">Specifies a proxy server for the request, rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="1c64d-208">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="1c64d-208">-ProxyCredential</span></span>

<span data-ttu-id="1c64d-209">指定擁有使用 **proxy** 參數所指定 proxy 伺服器之許可權的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="1c64d-209">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="1c64d-210">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="1c64d-210">-PublishLocation</span></span>

<span data-ttu-id="1c64d-211">指定封裝發佈位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="1c64d-211">Specifies the path to a package's published location.</span></span>

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

### <span data-ttu-id="1c64d-212">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="1c64d-212">-RequiredVersion</span></span>

<span data-ttu-id="1c64d-213">指定您想要安裝之套件的確切允許版本。</span><span class="sxs-lookup"><span data-stu-id="1c64d-213">Specifies the exact allowed version of the package that you want to install.</span></span> <span data-ttu-id="1c64d-214">如果您未新增此參數，則會 `Install-Package` 安裝套件的最新版本，以滿足 **MaximumVersion** 參數所指定的任何版本。</span><span class="sxs-lookup"><span data-stu-id="1c64d-214">If you don't add this parameter, `Install-Package` installs the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="1c64d-215">-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="1c64d-215">-RoleCapability</span></span>

<span data-ttu-id="1c64d-216">指定角色功能的陣列。</span><span class="sxs-lookup"><span data-stu-id="1c64d-216">Specifies an array of role capabilities.</span></span>

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

### <span data-ttu-id="1c64d-217">-Scope</span><span class="sxs-lookup"><span data-stu-id="1c64d-217">-Scope</span></span>

<span data-ttu-id="1c64d-218">指定要安裝套件的範圍。</span><span class="sxs-lookup"><span data-stu-id="1c64d-218">Specifies the scope for which to install the package.</span></span> <span data-ttu-id="1c64d-219">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="1c64d-219">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="1c64d-220">CurrentUser</span><span class="sxs-lookup"><span data-stu-id="1c64d-220">CurrentUser</span></span>
- <span data-ttu-id="1c64d-221">AllUsers</span><span class="sxs-lookup"><span data-stu-id="1c64d-221">AllUsers</span></span>

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

### <span data-ttu-id="1c64d-222">->scriptpublishlocation</span><span class="sxs-lookup"><span data-stu-id="1c64d-222">-ScriptPublishLocation</span></span>

<span data-ttu-id="1c64d-223">指定腳本發佈位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="1c64d-223">Specifies the path to a script's published location.</span></span>

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

### <span data-ttu-id="1c64d-224">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="1c64d-224">-ScriptSourceLocation</span></span>

<span data-ttu-id="1c64d-225">指定腳本來源位置。</span><span class="sxs-lookup"><span data-stu-id="1c64d-225">Specifies the script source location.</span></span>

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

### <span data-ttu-id="1c64d-226">-SkipDependencies</span><span class="sxs-lookup"><span data-stu-id="1c64d-226">-SkipDependencies</span></span>

<span data-ttu-id="1c64d-227">略過軟體相依性的安裝。</span><span class="sxs-lookup"><span data-stu-id="1c64d-227">Skips the installation of software dependencies.</span></span>

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

### <span data-ttu-id="1c64d-228">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="1c64d-228">-SkipPublisherCheck</span></span>

<span data-ttu-id="1c64d-229">可讓您取得比已安裝版本還新的套件版本。</span><span class="sxs-lookup"><span data-stu-id="1c64d-229">Allows you to get a package version that is newer than your installed version.</span></span> <span data-ttu-id="1c64d-230">例如，已安裝的套件已由受信任的發行者進行數位簽署，但新版本未經過數位簽署。</span><span class="sxs-lookup"><span data-stu-id="1c64d-230">For example, an installed package that is digitally signed by a trusted publisher but a new version isn't digitally signed.</span></span>

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

### <span data-ttu-id="1c64d-231">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="1c64d-231">-SkipValidate</span></span>

<span data-ttu-id="1c64d-232">略過驗證封裝認證的參數。</span><span class="sxs-lookup"><span data-stu-id="1c64d-232">Switch that skips validating the credentials of a package.</span></span>

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

### <span data-ttu-id="1c64d-233">-Source</span><span class="sxs-lookup"><span data-stu-id="1c64d-233">-Source</span></span>

<span data-ttu-id="1c64d-234">指定一或多個套件來源。</span><span class="sxs-lookup"><span data-stu-id="1c64d-234">Specifies one or more package sources.</span></span> <span data-ttu-id="1c64d-235">多個套件來源名稱必須以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="1c64d-235">Multiple package source names must be separated by commas.</span></span>
<span data-ttu-id="1c64d-236">您可以藉由執行 Cmdlet 來取得套件來源名稱 `Get-PackageSource` 。</span><span class="sxs-lookup"><span data-stu-id="1c64d-236">You can get package source names by running the `Get-PackageSource` cmdlet.</span></span>

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

### <span data-ttu-id="1c64d-237">-Tag</span><span class="sxs-lookup"><span data-stu-id="1c64d-237">-Tag</span></span>

<span data-ttu-id="1c64d-238">指定要在套件中繼資料中搜尋的一或多個字串。</span><span class="sxs-lookup"><span data-stu-id="1c64d-238">Specifies one or more strings to search for in the package metadata.</span></span>

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

### <span data-ttu-id="1c64d-239">-Type</span><span class="sxs-lookup"><span data-stu-id="1c64d-239">-Type</span></span>

<span data-ttu-id="1c64d-240">指定是否要使用模組、腳本或兩者來搜尋封裝。</span><span class="sxs-lookup"><span data-stu-id="1c64d-240">Specifies whether to search for packages with a module, a script, or both.</span></span> <span data-ttu-id="1c64d-241">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="1c64d-241">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="1c64d-242">模組</span><span class="sxs-lookup"><span data-stu-id="1c64d-242">Module</span></span>
- <span data-ttu-id="1c64d-243">指令碼</span><span class="sxs-lookup"><span data-stu-id="1c64d-243">Script</span></span>
- <span data-ttu-id="1c64d-244">全部</span><span class="sxs-lookup"><span data-stu-id="1c64d-244">All</span></span>

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

### <span data-ttu-id="1c64d-245">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1c64d-245">-Confirm</span></span>

<span data-ttu-id="1c64d-246">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="1c64d-246">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="1c64d-247">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1c64d-247">-WhatIf</span></span>

<span data-ttu-id="1c64d-248">顯示執行 Cmdlet 時會發生 `Install-Package` 的情況。</span><span class="sxs-lookup"><span data-stu-id="1c64d-248">Shows what would happen if `Install-Package` cmdlet is run.</span></span> <span data-ttu-id="1c64d-249">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="1c64d-249">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="1c64d-250">-AdditionalArguments</span><span class="sxs-lookup"><span data-stu-id="1c64d-250">-AdditionalArguments</span></span>

<span data-ttu-id="1c64d-251">指定一或多個要安裝的額外引數。</span><span class="sxs-lookup"><span data-stu-id="1c64d-251">Specifies one or more additional arguments for installation.</span></span>

```yaml
Type: System.String[]
Parameter Sets: msi:PackageBySearch, msi:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c64d-252">-IncludeSystemComponent</span><span class="sxs-lookup"><span data-stu-id="1c64d-252">-IncludeSystemComponent</span></span>

<span data-ttu-id="1c64d-253">指出此 Cmdlet 包含結果中的系統元件。</span><span class="sxs-lookup"><span data-stu-id="1c64d-253">Indicates that this cmdlet includes system components in the results.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Programs:PackageBySearch, Programs:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c64d-254">-IncludeWindowsInstaller</span><span class="sxs-lookup"><span data-stu-id="1c64d-254">-IncludeWindowsInstaller</span></span>

<span data-ttu-id="1c64d-255">指出此 Cmdlet 會在結果中包含 Windows installer。</span><span class="sxs-lookup"><span data-stu-id="1c64d-255">Indicates that this cmdlet includes the Windows installer in the results.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Programs:PackageBySearch, Programs:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c64d-256">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1c64d-256">CommonParameters</span></span>

<span data-ttu-id="1c64d-257">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="1c64d-257">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1c64d-258">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="1c64d-258">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1c64d-259">輸入</span><span class="sxs-lookup"><span data-stu-id="1c64d-259">INPUTS</span></span>

### <span data-ttu-id="1c64d-260">`Install-Package` 接受來自管線的輸入。</span><span class="sxs-lookup"><span data-stu-id="1c64d-260">`Install-Package` accepts input from the pipeline.</span></span>

## <span data-ttu-id="1c64d-261">輸出</span><span class="sxs-lookup"><span data-stu-id="1c64d-261">OUTPUTS</span></span>

### <span data-ttu-id="1c64d-262">SoftwareIdentity[]</span><span class="sxs-lookup"><span data-stu-id="1c64d-262">SoftwareIdentity[]</span></span>

## <span data-ttu-id="1c64d-263">注意</span><span class="sxs-lookup"><span data-stu-id="1c64d-263">NOTES</span></span>

<span data-ttu-id="1c64d-264">在命令中包含封裝提供者可以讓 Cmdlet 提供動態參數。</span><span class="sxs-lookup"><span data-stu-id="1c64d-264">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="1c64d-265">動態參數是封裝提供者專用的。</span><span class="sxs-lookup"><span data-stu-id="1c64d-265">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="1c64d-266">此 `Get-Help` Cmdlet 會列出 Cmdlet 的參數集，並包含提供者的參數集。</span><span class="sxs-lookup"><span data-stu-id="1c64d-266">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span> <span data-ttu-id="1c64d-267">例如， `Install-Package` 具有 **PowerShellGet** 參數集，其中包含 `-NoPathUpdate` 、 `AllowClobber` 和 `SkipPublisherCheck` 。</span><span class="sxs-lookup"><span data-stu-id="1c64d-267">For example, `Install-Package` has the **PowerShellGet** parameter set that includes `-NoPathUpdate`, `AllowClobber`, and `SkipPublisherCheck`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1c64d-268">從2020年4月起，PowerShell 資源庫不再支援傳輸層安全性 (TLS) 1.0 和1.1 版。</span><span class="sxs-lookup"><span data-stu-id="1c64d-268">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="1c64d-269">如果您不是使用 TLS 1.2 或更高版本，當您嘗試存取 PowerShell 資源庫時，將會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="1c64d-269">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="1c64d-270">使用下列命令，以確保您使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="1c64d-270">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="1c64d-271">如需詳細資訊，請參閱 PowerShell blog 中的 [公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 。</span><span class="sxs-lookup"><span data-stu-id="1c64d-271">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="1c64d-272">相關連結</span><span class="sxs-lookup"><span data-stu-id="1c64d-272">RELATED LINKS</span></span>

[<span data-ttu-id="1c64d-273">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="1c64d-273">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="1c64d-274">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="1c64d-274">Find-DscResource</span></span>](../PowershellGet/Find-DscResource.md)

[<span data-ttu-id="1c64d-275">Get-Help</span><span class="sxs-lookup"><span data-stu-id="1c64d-275">Get-Help</span></span>](../Microsoft.PowerShell.Core/Get-Help.md)

[<span data-ttu-id="1c64d-276">Get-Package</span><span class="sxs-lookup"><span data-stu-id="1c64d-276">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="1c64d-277">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="1c64d-277">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="1c64d-278">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="1c64d-278">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="1c64d-279">Find-Package</span><span class="sxs-lookup"><span data-stu-id="1c64d-279">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="1c64d-280">Save-Package</span><span class="sxs-lookup"><span data-stu-id="1c64d-280">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="1c64d-281">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="1c64d-281">Uninstall-Package</span></span>](Uninstall-Package.md)
