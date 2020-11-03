---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-packageprovider?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-PackageProvider
ms.openlocfilehash: ceae77cb6ef2e36f62da7872e9592292e6065ada
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203699"
---
# <span data-ttu-id="463fa-103">Install-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="463fa-103">Install-PackageProvider</span></span>

## <span data-ttu-id="463fa-104">概要</span><span class="sxs-lookup"><span data-stu-id="463fa-104">SYNOPSIS</span></span>
<span data-ttu-id="463fa-105">安裝一或多個套件管理封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="463fa-105">Installs one or more Package Management package providers.</span></span>

## <span data-ttu-id="463fa-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="463fa-106">SYNTAX</span></span>

### <span data-ttu-id="463fa-107">PackageBySearch (預設) </span><span class="sxs-lookup"><span data-stu-id="463fa-107">PackageBySearch (Default)</span></span>

```
Install-PackageProvider [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Credential <PSCredential>] [-Scope <String>] [-Source <String[]>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="463fa-108">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="463fa-108">PackageByInputObject</span></span>

```
Install-PackageProvider [-Scope <String>] [-InputObject] <SoftwareIdentity[]> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="463fa-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="463fa-109">DESCRIPTION</span></span>

<span data-ttu-id="463fa-110">**Install-packageprovider** 指令程式會安裝符合的套件管理提供者，這些提供者可在以 **PowerShellGet** 註冊的套件來源中使用。</span><span class="sxs-lookup"><span data-stu-id="463fa-110">The **Install-PackageProvider** cmdlet installs matching Package Management providers that are available in package sources registered with **PowerShellGet** .</span></span>
<span data-ttu-id="463fa-111">根據預設，這包括可在 PowerShell 資源庫中使用 **PackageManagement** 標記的模組。</span><span class="sxs-lookup"><span data-stu-id="463fa-111">By default, this includes modules available in the PowerShell Gallery with the **PackageManagement** tag.</span></span>
<span data-ttu-id="463fa-112">**PowerShellGet** 套件管理提供者是用來尋找這些存放庫中的提供者。</span><span class="sxs-lookup"><span data-stu-id="463fa-112">The **PowerShellGet** Package Management provider is used for finding providers in these repositories.</span></span>

<span data-ttu-id="463fa-113">此 Cmdlet 也會安裝可使用套件管理啟動載入應用程式所提供的相符套件管理提供者。</span><span class="sxs-lookup"><span data-stu-id="463fa-113">This cmdlet also installs matching Package Management providers that are available using the Package Management bootstrapping application.</span></span>

<span data-ttu-id="463fa-114">此 Cmdlet 也會安裝可在套件管理 Azure Blob 存放區中取得的相符套件管理提供者。</span><span class="sxs-lookup"><span data-stu-id="463fa-114">This cmdlet also installs matching Package Management providers that are available in the Package Management Azure Blob store.</span></span>
<span data-ttu-id="463fa-115">使用啟動載入器提供者來尋找並安裝它們。</span><span class="sxs-lookup"><span data-stu-id="463fa-115">Use the bootstrapper provider to find and install them.</span></span>

<span data-ttu-id="463fa-116">為了第一次執行，PackageManagement 需要有網際網路連線，才能下載 Nuget 套件提供者。</span><span class="sxs-lookup"><span data-stu-id="463fa-116">In order to execute the first time, PackageManagement requires an internet connection to download the Nuget package provider.</span></span>
<span data-ttu-id="463fa-117">但是，如果您的電腦沒有網際網路連線，而且您需要使用 Nuget 或 PowerShellGet 提供者，您可以在另一部電腦上下載它們，然後將它們複製到目的電腦。</span><span class="sxs-lookup"><span data-stu-id="463fa-117">However, if your computer does not have an internet connection and you need to use the Nuget or PowerShellGet provider, you can download them on another computer and copy them to your target computer.</span></span>
<span data-ttu-id="463fa-118">使用下列步驟執行這項作業：</span><span class="sxs-lookup"><span data-stu-id="463fa-118">Use the following steps to do this:</span></span>

1.
<span data-ttu-id="463fa-119">執行 `Install-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201 -Force` 以從具有網際網路連線的電腦安裝提供者。</span><span class="sxs-lookup"><span data-stu-id="463fa-119">Run `Install-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201 -Force` to install the provider from a computer with an internet connection.</span></span>

2.
<span data-ttu-id="463fa-120">安裝之後，您可以在或中找到安裝的提供者 `$env:ProgramFiles\PackageManagement\ReferenceAssemblies\\\<ProviderName\>\\\<ProviderVersion\>` `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\\\<ProviderName\>\\\<ProviderVersion\>` 。</span><span class="sxs-lookup"><span data-stu-id="463fa-120">After the install, you can find the provider installed in `$env:ProgramFiles\PackageManagement\ReferenceAssemblies\\\<ProviderName\>\\\<ProviderVersion\>` or `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\\\<ProviderName\>\\\<ProviderVersion\>`.</span></span>

3.
<span data-ttu-id="463fa-121">將 \<ProviderName\> 資料夾（在此案例中為 Nuget 資料夾）放在目的電腦上的對應位置。</span><span class="sxs-lookup"><span data-stu-id="463fa-121">Place the \<ProviderName\> folder, which in this case is the Nuget folder, in the corresponding location on your target computer.</span></span>
<span data-ttu-id="463fa-122">如果您的目的電腦是 Nano 伺服器，您需要從 Nano Server 執行 **安裝 install-packageprovider** ，以下載正確的 Nuget 二進位檔。</span><span class="sxs-lookup"><span data-stu-id="463fa-122">If your target computer is a Nano server, you need to run **Install-PackageProvider** from Nano Server to download the correct Nuget binaries.</span></span>

4.
<span data-ttu-id="463fa-123">重新開機 PowerShell 以自動載入封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="463fa-123">Restart PowerShell to auto-load the package provider.</span></span>
<span data-ttu-id="463fa-124">或者，執行 `Get-PackageProvider -ListAvailable` 以列出電腦上所有可用的封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="463fa-124">Alternatively, run `Get-PackageProvider -ListAvailable` to list all the package providers available on the computer.</span></span>
<span data-ttu-id="463fa-125">然後使用 `Import-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201` 將提供者匯入至目前的 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="463fa-125">Then use `Import-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201` to import the provider to the current PowerShell session.</span></span>

## <span data-ttu-id="463fa-126">範例</span><span class="sxs-lookup"><span data-stu-id="463fa-126">EXAMPLES</span></span>

### <span data-ttu-id="463fa-127">範例1：從 PowerShell 資源庫安裝套件提供者</span><span class="sxs-lookup"><span data-stu-id="463fa-127">Example 1: Install a package provider from the PowerShell Gallery</span></span>

```
PS C:\> Install-PackageProvider -Name "Gistprovider" -Verbose
```

<span data-ttu-id="463fa-128">此命令會從 PowerShell 資源庫安裝 >gistprovider。</span><span class="sxs-lookup"><span data-stu-id="463fa-128">This command installs the Gistprovider from the PowerShell Gallery.</span></span>

### <span data-ttu-id="463fa-129">範例2：安裝特定版本的套件提供者</span><span class="sxs-lookup"><span data-stu-id="463fa-129">Example 2: Install a specified version of a package provider</span></span>

```
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
PS C:\> Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.216" -Force
```

<span data-ttu-id="463fa-130">此範例會安裝指定版本的 Nuget 封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="463fa-130">This example installs a specified version of the Nuget package provider.</span></span>

<span data-ttu-id="463fa-131">第一個命令會尋找名為 Nuget 的所有套件提供者版本。</span><span class="sxs-lookup"><span data-stu-id="463fa-131">The first command finds all versions of the package provider named Nuget.</span></span>
<span data-ttu-id="463fa-132">第二個命令會安裝指定版本的 Nuget 封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="463fa-132">The second command installs a specified version of the Nuget package provider.</span></span>

### <span data-ttu-id="463fa-133">範例3：尋找提供者並加以安裝</span><span class="sxs-lookup"><span data-stu-id="463fa-133">Example 3: Find a provider and install it</span></span>

```
PS C:\> Find-PackageProvider -Name "Gistprovider" | Install-PackageProvider -Verbose
```

<span data-ttu-id="463fa-134">此命令會使用 **尋找 install-packageprovider** 和管線來搜尋 Gist 提供者，並加以安裝。</span><span class="sxs-lookup"><span data-stu-id="463fa-134">This command uses **Find-PackageProvider** and the pipeline to search for the Gist provider and install it.</span></span>

### <span data-ttu-id="463fa-135">範例4：將提供者安裝到目前使用者的模組資料夾</span><span class="sxs-lookup"><span data-stu-id="463fa-135">Example 4: Install a provider to the current user's module folder</span></span>

```
PS C:\> Install-PackageProvider -Name Gistprovider -Verbose -Scope CurrentUser
```

<span data-ttu-id="463fa-136">此命令會將封裝提供者安裝至 $env： Localappdata\packagemanagement\providerassemblies 有舊版，如此一來，只有目前的使用者可以使用它。</span><span class="sxs-lookup"><span data-stu-id="463fa-136">This command installs a package provider to $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies so that only the current user can use it.</span></span>

## <span data-ttu-id="463fa-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="463fa-137">PARAMETERS</span></span>

### <span data-ttu-id="463fa-138">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="463fa-138">-AllVersions</span></span>

<span data-ttu-id="463fa-139">指出此 Cmdlet 會安裝所有可用版本的封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="463fa-139">Indicates that this cmdlet installs all available versions of the package provider.</span></span>
<span data-ttu-id="463fa-140">根據預設， **安裝-install-packageprovider** 只會傳回最高可用版本。</span><span class="sxs-lookup"><span data-stu-id="463fa-140">By default, **Install-PackageProvider** only returns the highest available version.</span></span>

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

### <span data-ttu-id="463fa-141">-Credential</span><span class="sxs-lookup"><span data-stu-id="463fa-141">-Credential</span></span>

<span data-ttu-id="463fa-142">指定具有安裝套件提供者權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="463fa-142">Specifies a user account that has permission to install package providers.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="463fa-143">-Force</span><span class="sxs-lookup"><span data-stu-id="463fa-143">-Force</span></span>

<span data-ttu-id="463fa-144">指出此 Cmdlet 會使用可強制執行的這個 Cmdlet 來強制執行所有動作。</span><span class="sxs-lookup"><span data-stu-id="463fa-144">Indicates that this cmdlet forces all actions with this cmdlet that can be forced.</span></span>
<span data-ttu-id="463fa-145">目前，這表示 *Force* 參數的作用與 *ForceBootstrap* 參數相同。</span><span class="sxs-lookup"><span data-stu-id="463fa-145">Currently, this means the *Force* parameter acts the same as the *ForceBootstrap* parameter.</span></span>

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

### <span data-ttu-id="463fa-146">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="463fa-146">-ForceBootstrap</span></span>

<span data-ttu-id="463fa-147">指示此 Cmdlet 會自動安裝套件提供者。</span><span class="sxs-lookup"><span data-stu-id="463fa-147">Indicates that this cmdlet automatically installs the package provider.</span></span>

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

### <span data-ttu-id="463fa-148">-InputObject</span><span class="sxs-lookup"><span data-stu-id="463fa-148">-InputObject</span></span>

<span data-ttu-id="463fa-149">指定 **SoftwareIdentity** 物件。</span><span class="sxs-lookup"><span data-stu-id="463fa-149">Specifies a **SoftwareIdentity** object.</span></span>
<span data-ttu-id="463fa-150">使用 **install-packageprovider** Cmdlet 取得 **SoftwareIdentity** 物件，以輸送到 **install-packageprovider** 。</span><span class="sxs-lookup"><span data-stu-id="463fa-150">Use the **Find-PackageProvider** cmdlet to obtain a **SoftwareIdentity** object to pipe into **Install-PackageProvider** .</span></span>

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

### <span data-ttu-id="463fa-151">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="463fa-151">-MaximumVersion</span></span>

<span data-ttu-id="463fa-152">指定您想要安裝的套件提供者所允許的最大版本。</span><span class="sxs-lookup"><span data-stu-id="463fa-152">Specifies the maximum allowed version of the package provider that you want to install.</span></span>
<span data-ttu-id="463fa-153">如果您未新增此參數， **install-packageprovider** 會安裝提供者的最高可用版本。</span><span class="sxs-lookup"><span data-stu-id="463fa-153">If you do not add this parameter, **Install-PackageProvider** installs the highest available version of the provider.</span></span>

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

### <span data-ttu-id="463fa-154">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="463fa-154">-MinimumVersion</span></span>

<span data-ttu-id="463fa-155">指定您想要安裝的套件提供者所允許的最低版本。</span><span class="sxs-lookup"><span data-stu-id="463fa-155">Specifies the minimum allowed version of the package provider that you want to install.</span></span>
<span data-ttu-id="463fa-156">如果您未新增此參數， **install-packageprovider** 會安裝套件的最高可用版本，同時也會滿足 *MaximumVersion* 參數所指定的任何需求。</span><span class="sxs-lookup"><span data-stu-id="463fa-156">If you do not add this parameter, **Install-PackageProvider** installs the highest available version of the package that also satisfies any requirement specified by the *MaximumVersion* parameter.</span></span>

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

### <span data-ttu-id="463fa-157">-Name</span><span class="sxs-lookup"><span data-stu-id="463fa-157">-Name</span></span>

<span data-ttu-id="463fa-158">指定一或多個封裝提供者模組名稱。</span><span class="sxs-lookup"><span data-stu-id="463fa-158">Specifies one or more package provider module names.</span></span>
<span data-ttu-id="463fa-159">以逗號分隔多個封裝名稱。</span><span class="sxs-lookup"><span data-stu-id="463fa-159">Separate multiple package names with commas.</span></span>
<span data-ttu-id="463fa-160">不支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="463fa-160">Wildcard characters are not supported.</span></span>

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

### <span data-ttu-id="463fa-161">-Proxy</span><span class="sxs-lookup"><span data-stu-id="463fa-161">-Proxy</span></span>

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

### <span data-ttu-id="463fa-162">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="463fa-162">-ProxyCredential</span></span>

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

### <span data-ttu-id="463fa-163">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="463fa-163">-RequiredVersion</span></span>

<span data-ttu-id="463fa-164">指定您想要安裝之封裝提供者的確切允許版本。</span><span class="sxs-lookup"><span data-stu-id="463fa-164">Specifies the exact allowed version of the package provider that you want to install.</span></span>
<span data-ttu-id="463fa-165">如果您未新增此參數，則 **install-packageprovider** 會安裝提供者的最高可用版本，同時也會滿足 *MaximumVersion* 參數所指定的最大版本。</span><span class="sxs-lookup"><span data-stu-id="463fa-165">If you do not add this parameter, **Install-PackageProvider** installs the highest available version of the provider that also satisfies any maximum version specified by the *MaximumVersion* parameter.</span></span>

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

### <span data-ttu-id="463fa-166">-Scope</span><span class="sxs-lookup"><span data-stu-id="463fa-166">-Scope</span></span>

<span data-ttu-id="463fa-167">指定提供者的安裝範圍。</span><span class="sxs-lookup"><span data-stu-id="463fa-167">Specifies the installation scope of the provider.</span></span>
<span data-ttu-id="463fa-168">此參數可接受的值為： **AllUsers** 和 **CurrentUser** 。</span><span class="sxs-lookup"><span data-stu-id="463fa-168">The acceptable values for this parameter are: **AllUsers** and **CurrentUser** .</span></span>

<span data-ttu-id="463fa-169">**AllUsers** 範圍會將提供者安裝在可供電腦的所有使用者存取的位置。</span><span class="sxs-lookup"><span data-stu-id="463fa-169">The **AllUsers** scope installs providers in a location that is accessible to all users of the computer.</span></span>
<span data-ttu-id="463fa-170">根據預設，這是 **$env:P rogramfiles\packagemanagement\providerassemblies.**</span><span class="sxs-lookup"><span data-stu-id="463fa-170">By default, this is **$env:ProgramFiles\PackageManagement\ProviderAssemblies.**</span></span>

<span data-ttu-id="463fa-171">**CurrentUser** 範圍會將提供者安裝在只能由目前使用者存取的位置。</span><span class="sxs-lookup"><span data-stu-id="463fa-171">The **CurrentUser** scope installs providers in a location where they are only accessible to the current user.</span></span>
<span data-ttu-id="463fa-172">根據預設，這是 **$env： LOCALAPPDATA\PackageManagement\ProviderAssemblies.**</span><span class="sxs-lookup"><span data-stu-id="463fa-172">By default, this is **$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies.**</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="463fa-173">-Source</span><span class="sxs-lookup"><span data-stu-id="463fa-173">-Source</span></span>

<span data-ttu-id="463fa-174">指定一或多個套件來源。</span><span class="sxs-lookup"><span data-stu-id="463fa-174">Specifies one or more package sources.</span></span>
<span data-ttu-id="463fa-175">使用 Get-PackageSource Cmdlet 取得可用套件來源的清單。</span><span class="sxs-lookup"><span data-stu-id="463fa-175">Use the Get-PackageSource cmdlet to get a list of available package sources.</span></span>

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

### <span data-ttu-id="463fa-176">-Confirm</span><span class="sxs-lookup"><span data-stu-id="463fa-176">-Confirm</span></span>

<span data-ttu-id="463fa-177">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="463fa-177">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="463fa-178">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="463fa-178">-WhatIf</span></span>

<span data-ttu-id="463fa-179">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="463fa-179">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="463fa-180">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="463fa-180">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="463fa-181">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="463fa-181">CommonParameters</span></span>

<span data-ttu-id="463fa-182">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="463fa-182">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="463fa-183">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="463fa-183">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="463fa-184">輸入</span><span class="sxs-lookup"><span data-stu-id="463fa-184">INPUTS</span></span>

### <span data-ttu-id="463fa-185">SoftwareIdentity。</span><span class="sxs-lookup"><span data-stu-id="463fa-185">Microsoft.PackageManagement.Packaging.SoftwareIdentity</span></span>

<span data-ttu-id="463fa-186">您可以使用管線將 **SoftwareIdentity** 物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="463fa-186">You can pipe a **SoftwareIdentity** object to this cmdlet.</span></span>
<span data-ttu-id="463fa-187">使用 Find-PackageProvider 取得可輸送至 **安裝-install-packageprovider** 的 **SoftwareIdentity** 物件。</span><span class="sxs-lookup"><span data-stu-id="463fa-187">Use Find-PackageProvider to get a **SoftwareIdentity** object that can be piped into **Install-PackageProvider** .</span></span>

## <span data-ttu-id="463fa-188">輸出</span><span class="sxs-lookup"><span data-stu-id="463fa-188">OUTPUTS</span></span>

## <span data-ttu-id="463fa-189">注意</span><span class="sxs-lookup"><span data-stu-id="463fa-189">NOTES</span></span>

## <span data-ttu-id="463fa-190">相關連結</span><span class="sxs-lookup"><span data-stu-id="463fa-190">RELATED LINKS</span></span>

[<span data-ttu-id="463fa-191">Find-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="463fa-191">Find-PackageProvider</span></span>](Find-PackageProvider.md)

[<span data-ttu-id="463fa-192">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="463fa-192">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="463fa-193">Import-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="463fa-193">Import-PackageProvider</span></span>](Import-PackageProvider.md)
