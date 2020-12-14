---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-packageprovider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-PackageProvider
ms.openlocfilehash: 8ab8a0fd505bca7cda5cef17a09baa9f7e571dd4
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892792"
---
# <span data-ttu-id="e7e48-103">Install-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="e7e48-103">Install-PackageProvider</span></span>

## <span data-ttu-id="e7e48-104">概要</span><span class="sxs-lookup"><span data-stu-id="e7e48-104">SYNOPSIS</span></span>
<span data-ttu-id="e7e48-105">安裝一或多個套件管理封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="e7e48-105">Installs one or more Package Management package providers.</span></span>

## <span data-ttu-id="e7e48-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e7e48-106">SYNTAX</span></span>

### <span data-ttu-id="e7e48-107">PackageBySearch (預設) </span><span class="sxs-lookup"><span data-stu-id="e7e48-107">PackageBySearch (Default)</span></span>

```
Install-PackageProvider [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Credential <PSCredential>] [-Scope <String>] [-Source <String[]>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="e7e48-108">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="e7e48-108">PackageByInputObject</span></span>

```
Install-PackageProvider [-Scope <String>] [-InputObject] <SoftwareIdentity[]> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="e7e48-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e7e48-109">DESCRIPTION</span></span>

<span data-ttu-id="e7e48-110">`Install-PackageProvider`指令程式會安裝符合的套件管理提供者，此提供者可在以 **PowerShellGet** 註冊的套件來源中使用。</span><span class="sxs-lookup"><span data-stu-id="e7e48-110">The `Install-PackageProvider` cmdlet installs matching Package Management providers that are available in package sources registered with **PowerShellGet**.</span></span> <span data-ttu-id="e7e48-111">根據預設，這包括可在 Windows PowerShell 資源庫中使用 **PackageManagement** 標記的模組。</span><span class="sxs-lookup"><span data-stu-id="e7e48-111">By default, this includes modules available in the Windows PowerShell Gallery with the **PackageManagement** tag.</span></span> <span data-ttu-id="e7e48-112">**PowerShellGet** 套件管理提供者是用來尋找這些存放庫中的提供者。</span><span class="sxs-lookup"><span data-stu-id="e7e48-112">The **PowerShellGet** Package Management provider is used for finding providers in these repositories.</span></span>

<span data-ttu-id="e7e48-113">此 Cmdlet 也會安裝可使用套件管理啟動載入應用程式所提供的相符套件管理提供者。</span><span class="sxs-lookup"><span data-stu-id="e7e48-113">This cmdlet also installs matching Package Management providers that are available using the Package Management bootstrapping application.</span></span>

<span data-ttu-id="e7e48-114">此 Cmdlet 也會安裝可在套件管理 Azure Blob 存放區中取得的相符套件管理提供者。</span><span class="sxs-lookup"><span data-stu-id="e7e48-114">This cmdlet also installs matching Package Management providers that are available in the Package Management Azure Blob store.</span></span> <span data-ttu-id="e7e48-115">使用啟動載入器提供者來尋找並安裝它們。</span><span class="sxs-lookup"><span data-stu-id="e7e48-115">Use the bootstrapper provider to find and install them.</span></span>

<span data-ttu-id="e7e48-116">為了第一次執行，PackageManagement 需要有網際網路連線，才能下載 NuGet 套件提供者。</span><span class="sxs-lookup"><span data-stu-id="e7e48-116">In order to execute the first time, PackageManagement requires an internet connection to download the NuGet package provider.</span></span> <span data-ttu-id="e7e48-117">但是，如果您的電腦沒有網際網路連線，而且您需要使用 NuGet 或 PowerShellGet 提供者，您可以在另一部電腦上下載它們，然後將它們複製到目的電腦。</span><span class="sxs-lookup"><span data-stu-id="e7e48-117">However, if your computer does not have an internet connection and you need to use the NuGet or PowerShellGet provider, you can download them on another computer and copy them to your target computer.</span></span> <span data-ttu-id="e7e48-118">使用下列步驟執行這項作業：</span><span class="sxs-lookup"><span data-stu-id="e7e48-118">Use the following steps to do this:</span></span>

1. <span data-ttu-id="e7e48-119">執行 `Install-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201 -Force` 以從具有網際網路連線的電腦安裝提供者。</span><span class="sxs-lookup"><span data-stu-id="e7e48-119">Run `Install-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201 -Force` to install the provider from a computer with an internet connection.</span></span>
1. <span data-ttu-id="e7e48-120">安裝之後，您可以在或中找到安裝的提供者 `$env:ProgramFiles\PackageManagement\ReferenceAssemblies\<ProviderName>\<ProviderVersion>` `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\<ProviderName>\<ProviderVersion>` 。</span><span class="sxs-lookup"><span data-stu-id="e7e48-120">After the install, you can find the provider installed in `$env:ProgramFiles\PackageManagement\ReferenceAssemblies\<ProviderName>\<ProviderVersion>` or `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\<ProviderName>\<ProviderVersion>`.</span></span>
1. <span data-ttu-id="e7e48-121">將 `<ProviderName>` 資料夾（在此案例中為 NuGet 資料夾）放在目的電腦上的對應位置。</span><span class="sxs-lookup"><span data-stu-id="e7e48-121">Place the `<ProviderName>` folder, which in this case is the NuGet folder, in the corresponding location on your target computer.</span></span> <span data-ttu-id="e7e48-122">如果您的目的電腦是 Nano 伺服器，您需要 `Install-PackageProvider` 從 Nano server 執行以下載正確的 NuGet 二進位檔。</span><span class="sxs-lookup"><span data-stu-id="e7e48-122">If your target computer is a Nano server, you need to run `Install-PackageProvider` from Nano Server to download the correct NuGet binaries.</span></span>
1. <span data-ttu-id="e7e48-123">重新開機 PowerShell 以自動載入封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="e7e48-123">Restart PowerShell to auto-load the package provider.</span></span> <span data-ttu-id="e7e48-124">或者，執行 `Get-PackageProvider -ListAvailable` 以列出電腦上所有可用的封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="e7e48-124">Alternatively, run `Get-PackageProvider -ListAvailable` to list all the package providers available on the computer.</span></span>
   <span data-ttu-id="e7e48-125">然後使用 `Import-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201` 將提供者匯入目前的 Windows PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="e7e48-125">Then use `Import-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201` to import the provider to the current Windows PowerShell session.</span></span>

## <span data-ttu-id="e7e48-126">範例</span><span class="sxs-lookup"><span data-stu-id="e7e48-126">EXAMPLES</span></span>

### <span data-ttu-id="e7e48-127">範例1：從 PowerShell 資源庫安裝套件提供者</span><span class="sxs-lookup"><span data-stu-id="e7e48-127">Example 1: Install a package provider from the PowerShell Gallery</span></span>

<span data-ttu-id="e7e48-128">此命令會從 PowerShell 資源庫安裝 >gistprovider 封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="e7e48-128">This command installs the GistProvider package provider from the PowerShell Gallery.</span></span>

```powershell
Install-PackageProvider -Name "GistProvider" -Verbose
```

### <span data-ttu-id="e7e48-129">範例2：安裝特定版本的套件提供者</span><span class="sxs-lookup"><span data-stu-id="e7e48-129">Example 2: Install a specified version of a package provider</span></span>

<span data-ttu-id="e7e48-130">此範例會安裝指定版本的 NuGet 封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="e7e48-130">This example installs a specified version of the NuGet package provider.</span></span>

<span data-ttu-id="e7e48-131">第一個命令會尋找名為 NuGet 的所有套件提供者版本。</span><span class="sxs-lookup"><span data-stu-id="e7e48-131">The first command finds all versions of the package provider named NuGet.</span></span>
<span data-ttu-id="e7e48-132">第二個命令會安裝指定版本的 NuGet 封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="e7e48-132">The second command installs a specified version of the NuGet package provider.</span></span>

```powershell
Find-PackageProvider -Name "NuGet" -AllVersions
Install-PackageProvider -Name "NuGet" -RequiredVersion "2.8.5.216" -Force
```

### <span data-ttu-id="e7e48-133">範例3：尋找提供者並加以安裝</span><span class="sxs-lookup"><span data-stu-id="e7e48-133">Example 3: Find a provider and install it</span></span>

<span data-ttu-id="e7e48-134">這個範例 `Find-PackageProvider` 會使用和管線來搜尋 Gist 提供者，並加以安裝。</span><span class="sxs-lookup"><span data-stu-id="e7e48-134">This example uses `Find-PackageProvider` and the pipeline to search for the Gist provider and install it.</span></span>

```powershell
Find-PackageProvider -Name "GistProvider" | Install-PackageProvider -Verbose
```

### <span data-ttu-id="e7e48-135">範例4：將提供者安裝到目前使用者的模組資料夾</span><span class="sxs-lookup"><span data-stu-id="e7e48-135">Example 4: Install a provider to the current user's module folder</span></span>

<span data-ttu-id="e7e48-136">此命令會將封裝提供者安裝到，如此一來 `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies` ，只有目前的使用者可以使用它。</span><span class="sxs-lookup"><span data-stu-id="e7e48-136">This command installs a package provider to `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies` so that only the current user can use it.</span></span>

```powershell
Install-PackageProvider -Name GistProvider -Verbose -Scope CurrentUser
```

## <span data-ttu-id="e7e48-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e7e48-137">PARAMETERS</span></span>

### <span data-ttu-id="e7e48-138">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="e7e48-138">-AllVersions</span></span>

<span data-ttu-id="e7e48-139">指出此 Cmdlet 會安裝所有可用版本的封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="e7e48-139">Indicates that this cmdlet installs all available versions of the package provider.</span></span> <span data-ttu-id="e7e48-140">根據預設， `Install-PackageProvider` 只會傳回最高可用版本。</span><span class="sxs-lookup"><span data-stu-id="e7e48-140">By default, `Install-PackageProvider` only returns the highest available version.</span></span>

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

### <span data-ttu-id="e7e48-141">-Credential</span><span class="sxs-lookup"><span data-stu-id="e7e48-141">-Credential</span></span>

<span data-ttu-id="e7e48-142">指定具有安裝套件提供者權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="e7e48-142">Specifies a user account that has permission to install package providers.</span></span>

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

### <span data-ttu-id="e7e48-143">-Force</span><span class="sxs-lookup"><span data-stu-id="e7e48-143">-Force</span></span>

<span data-ttu-id="e7e48-144">指出此 Cmdlet 會使用可強制執行的這個 Cmdlet 來強制執行所有動作。</span><span class="sxs-lookup"><span data-stu-id="e7e48-144">Indicates that this cmdlet forces all actions with this cmdlet that can be forced.</span></span> <span data-ttu-id="e7e48-145">目前，這表示 **Force** 參數的作用與 **ForceBootstrap** 參數相同。</span><span class="sxs-lookup"><span data-stu-id="e7e48-145">Currently, this means the **Force** parameter acts the same as the **ForceBootstrap** parameter.</span></span>

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

### <span data-ttu-id="e7e48-146">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="e7e48-146">-ForceBootstrap</span></span>

<span data-ttu-id="e7e48-147">指示此 Cmdlet 會自動安裝套件提供者。</span><span class="sxs-lookup"><span data-stu-id="e7e48-147">Indicates that this cmdlet automatically installs the package provider.</span></span>

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

### <span data-ttu-id="e7e48-148">-InputObject</span><span class="sxs-lookup"><span data-stu-id="e7e48-148">-InputObject</span></span>

<span data-ttu-id="e7e48-149">指定 **SoftwareIdentity** 物件。</span><span class="sxs-lookup"><span data-stu-id="e7e48-149">Specifies a **SoftwareIdentity** object.</span></span> <span data-ttu-id="e7e48-150">使用 `Find-PackageProvider` Cmdlet 取得要輸送至的 **SoftwareIdentity** 物件 `Install-PackageProvider` 。</span><span class="sxs-lookup"><span data-stu-id="e7e48-150">Use the `Find-PackageProvider` cmdlet to obtain a **SoftwareIdentity** object to pipe into `Install-PackageProvider`.</span></span>

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

### <span data-ttu-id="e7e48-151">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="e7e48-151">-MaximumVersion</span></span>

<span data-ttu-id="e7e48-152">指定您想要安裝的套件提供者所允許的最大版本。</span><span class="sxs-lookup"><span data-stu-id="e7e48-152">Specifies the maximum allowed version of the package provider that you want to install.</span></span> <span data-ttu-id="e7e48-153">如果您未新增此參數，則會 `Install-PackageProvider` 安裝提供者的最高可用版本。</span><span class="sxs-lookup"><span data-stu-id="e7e48-153">If you do not add this parameter, `Install-PackageProvider` installs the highest available version of the provider.</span></span>

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

### <span data-ttu-id="e7e48-154">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="e7e48-154">-MinimumVersion</span></span>

<span data-ttu-id="e7e48-155">指定您想要安裝的套件提供者所允許的最低版本。</span><span class="sxs-lookup"><span data-stu-id="e7e48-155">Specifies the minimum allowed version of the package provider that you want to install.</span></span> <span data-ttu-id="e7e48-156">如果您未新增此參數，則會 `Install-PackageProvider` 安裝套件的最高可用版本，此套件也會滿足 *MaximumVersion* 參數所指定的任何需求。</span><span class="sxs-lookup"><span data-stu-id="e7e48-156">If you do not add this parameter, `Install-PackageProvider` installs the highest available version of the package that also satisfies any requirement specified by the *MaximumVersion* parameter.</span></span>

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

### <span data-ttu-id="e7e48-157">-Name</span><span class="sxs-lookup"><span data-stu-id="e7e48-157">-Name</span></span>

<span data-ttu-id="e7e48-158">指定一或多個封裝提供者模組名稱。</span><span class="sxs-lookup"><span data-stu-id="e7e48-158">Specifies one or more package provider module names.</span></span> <span data-ttu-id="e7e48-159">以逗號分隔多個封裝名稱。</span><span class="sxs-lookup"><span data-stu-id="e7e48-159">Separate multiple package names with commas.</span></span>
<span data-ttu-id="e7e48-160">不支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="e7e48-160">Wildcard characters are not supported.</span></span>

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

### <span data-ttu-id="e7e48-161">-Proxy</span><span class="sxs-lookup"><span data-stu-id="e7e48-161">-Proxy</span></span>

<span data-ttu-id="e7e48-162">指定要求的 proxy 伺服器，而不是直接連接到網際網路資源。</span><span class="sxs-lookup"><span data-stu-id="e7e48-162">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="e7e48-163">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="e7e48-163">-ProxyCredential</span></span>

<span data-ttu-id="e7e48-164">指定具有使用 **Proxy** 參數所指定 Proxy 伺服器之權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="e7e48-164">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="e7e48-165">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="e7e48-165">-RequiredVersion</span></span>

<span data-ttu-id="e7e48-166">指定您想要安裝之封裝提供者的確切允許版本。</span><span class="sxs-lookup"><span data-stu-id="e7e48-166">Specifies the exact allowed version of the package provider that you want to install.</span></span> <span data-ttu-id="e7e48-167">如果您未新增此參數，則會 `Install-PackageProvider` 安裝提供者的最高可用版本，同時也會滿足 **MaximumVersion** 參數所指定的最大版本。</span><span class="sxs-lookup"><span data-stu-id="e7e48-167">If you do not add this parameter, `Install-PackageProvider` installs the highest available version of the provider that also satisfies any maximum version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="e7e48-168">-Scope</span><span class="sxs-lookup"><span data-stu-id="e7e48-168">-Scope</span></span>

<span data-ttu-id="e7e48-169">指定提供者的安裝範圍。</span><span class="sxs-lookup"><span data-stu-id="e7e48-169">Specifies the installation scope of the provider.</span></span> <span data-ttu-id="e7e48-170">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="e7e48-170">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="e7e48-171">**AllUsers** -將提供者安裝在電腦的所有使用者都可存取的位置。</span><span class="sxs-lookup"><span data-stu-id="e7e48-171">**AllUsers** - installs providers in a location that is accessible to all users of the computer.</span></span>
  <span data-ttu-id="e7e48-172">根據預設，這是 **$env:P rogramfiles\packagemanagement\providerassemblies.**</span><span class="sxs-lookup"><span data-stu-id="e7e48-172">By default, this is **$env:ProgramFiles\PackageManagement\ProviderAssemblies.**</span></span>

- <span data-ttu-id="e7e48-173">**CurrentUser** -在只能由目前使用者存取的位置中安裝提供者。</span><span class="sxs-lookup"><span data-stu-id="e7e48-173">**CurrentUser** - installs providers in a location where they are only accessible to the current user.</span></span> <span data-ttu-id="e7e48-174">根據預設，這是 **$env： LOCALAPPDATA\PackageManagement\ProviderAssemblies.**</span><span class="sxs-lookup"><span data-stu-id="e7e48-174">By default, this is **$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies.**</span></span>

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

### <span data-ttu-id="e7e48-175">-Source</span><span class="sxs-lookup"><span data-stu-id="e7e48-175">-Source</span></span>

<span data-ttu-id="e7e48-176">指定一或多個套件來源。</span><span class="sxs-lookup"><span data-stu-id="e7e48-176">Specifies one or more package sources.</span></span> <span data-ttu-id="e7e48-177">使用 `Get-PackageSource` Cmdlet 取得可用套件來源的清單。</span><span class="sxs-lookup"><span data-stu-id="e7e48-177">Use the `Get-PackageSource` cmdlet to get a list of available package sources.</span></span>

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

### <span data-ttu-id="e7e48-178">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e7e48-178">-Confirm</span></span>

<span data-ttu-id="e7e48-179">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="e7e48-179">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="e7e48-180">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e7e48-180">-WhatIf</span></span>

<span data-ttu-id="e7e48-181">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="e7e48-181">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="e7e48-182">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="e7e48-182">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="e7e48-183">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e7e48-183">CommonParameters</span></span>

<span data-ttu-id="e7e48-184">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="e7e48-184">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e7e48-185">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="e7e48-185">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e7e48-186">輸入</span><span class="sxs-lookup"><span data-stu-id="e7e48-186">INPUTS</span></span>

### <span data-ttu-id="e7e48-187">SoftwareIdentity。</span><span class="sxs-lookup"><span data-stu-id="e7e48-187">Microsoft.PackageManagement.Packaging.SoftwareIdentity</span></span>

<span data-ttu-id="e7e48-188">您可以使用管線將 **SoftwareIdentity** 物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e7e48-188">You can pipe a **SoftwareIdentity** object to this cmdlet.</span></span> <span data-ttu-id="e7e48-189">使用 `Find-PackageProvider` 取得可輸送至的 **SoftwareIdentity** 物件 `Install-PackageProvider` 。</span><span class="sxs-lookup"><span data-stu-id="e7e48-189">Use `Find-PackageProvider` to get a **SoftwareIdentity** object that can be piped into `Install-PackageProvider`.</span></span>

## <span data-ttu-id="e7e48-190">輸出</span><span class="sxs-lookup"><span data-stu-id="e7e48-190">OUTPUTS</span></span>

## <span data-ttu-id="e7e48-191">注意</span><span class="sxs-lookup"><span data-stu-id="e7e48-191">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e7e48-192">從2020年4月起，PowerShell 資源庫不再支援傳輸層安全性 (TLS) 1.0 和1.1 版。</span><span class="sxs-lookup"><span data-stu-id="e7e48-192">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="e7e48-193">如果您不是使用 TLS 1.2 或更高版本，當您嘗試存取 PowerShell 資源庫時，將會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="e7e48-193">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="e7e48-194">使用下列命令，以確保您使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="e7e48-194">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="e7e48-195">如需詳細資訊，請參閱 PowerShell blog 中的 [公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 。</span><span class="sxs-lookup"><span data-stu-id="e7e48-195">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="e7e48-196">相關連結</span><span class="sxs-lookup"><span data-stu-id="e7e48-196">RELATED LINKS</span></span>

[<span data-ttu-id="e7e48-197">Find-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="e7e48-197">Find-PackageProvider</span></span>](Find-PackageProvider.md)

[<span data-ttu-id="e7e48-198">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="e7e48-198">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="e7e48-199">Import-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="e7e48-199">Import-PackageProvider</span></span>](Import-PackageProvider.md)
