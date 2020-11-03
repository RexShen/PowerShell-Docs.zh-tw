---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/find-packageprovider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-PackageProvider
ms.openlocfilehash: dc4450e1c9f8b9506ee57948e4cec2d0541c181d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202960"
---
# <span data-ttu-id="ae428-103">Find-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="ae428-103">Find-PackageProvider</span></span>

## <span data-ttu-id="ae428-104">概要</span><span class="sxs-lookup"><span data-stu-id="ae428-104">SYNOPSIS</span></span>
<span data-ttu-id="ae428-105">傳回可供安裝的套件管理封裝提供者的清單。</span><span class="sxs-lookup"><span data-stu-id="ae428-105">Returns a list of Package Management package providers available for installation.</span></span>

## <span data-ttu-id="ae428-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ae428-106">SYNTAX</span></span>

```
Find-PackageProvider [[-Name] <String[]>] [-AllVersions] [-Source <String[]>] [-IncludeDependencies]
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-RequiredVersion <String>]
 [-MinimumVersion <String>] [-MaximumVersion <String>] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## <span data-ttu-id="ae428-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="ae428-107">DESCRIPTION</span></span>

<span data-ttu-id="ae428-108">**Install-packageprovider** 指令程式會尋找相符的 PackageManagement 提供者，該提供者可在以 PowerShellGet 註冊的套件來源中使用。</span><span class="sxs-lookup"><span data-stu-id="ae428-108">The **Find-PackageProvider** cmdlet finds matching PackageManagement providers that are available in package sources registered with PowerShellGet.</span></span>
<span data-ttu-id="ae428-109">這些是可使用 Install-PackageProvider Cmdlet 進行安裝的封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="ae428-109">These are package providers available for installation with the Install-PackageProvider cmdlet.</span></span>
<span data-ttu-id="ae428-110">根據預設，這包括可在 PowerShell 資源庫中提供 **PackageManagement** 和 **提供者** 標記的模組。</span><span class="sxs-lookup"><span data-stu-id="ae428-110">By default, this includes modules available in the PowerShell Gallery with the **PackageManagement** and **Provider** tags.</span></span>

<span data-ttu-id="ae428-111">**Install-packageprovider** 也會尋找套件管理 Azure Blob 存放區中提供的相符套件管理提供者。</span><span class="sxs-lookup"><span data-stu-id="ae428-111">**Find-PackageProvider** also finds matching Package Management providers that are available in the Package Management Azure Blob store.</span></span>
<span data-ttu-id="ae428-112">使用啟動載入器提供者來尋找並安裝它們。</span><span class="sxs-lookup"><span data-stu-id="ae428-112">Use the bootstrapper provider to find and install them.</span></span>

## <span data-ttu-id="ae428-113">範例</span><span class="sxs-lookup"><span data-stu-id="ae428-113">EXAMPLES</span></span>

### <span data-ttu-id="ae428-114">範例1：尋找所有可用的封裝提供者</span><span class="sxs-lookup"><span data-stu-id="ae428-114">Example 1: Find all available package providers</span></span>

```
PS C:\> Find-PackageProvider
```

<span data-ttu-id="ae428-115">此命令會取得套件管理所支援的存放庫上可用之所有套件提供者的清單。</span><span class="sxs-lookup"><span data-stu-id="ae428-115">This command gets a list of all package providers that are available on the repositories supported by Package Management.</span></span>
<span data-ttu-id="ae428-116">根據預設，這些封裝提供者可在 PowerShell 資源庫和使用套件管理啟動載入應用程式中取得。</span><span class="sxs-lookup"><span data-stu-id="ae428-116">By default, those package providers are available on the PowerShell Gallery and by using the Package Management bootstrapping application.</span></span>

### <span data-ttu-id="ae428-117">範例2：尋找提供者的所有版本</span><span class="sxs-lookup"><span data-stu-id="ae428-117">Example 2: Find all versions of a provider</span></span>

```
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
```

<span data-ttu-id="ae428-118">此命令會尋找名為 Nuget 的所有套件提供者版本。</span><span class="sxs-lookup"><span data-stu-id="ae428-118">This command finds all versions of the package provider named Nuget.</span></span>

### <span data-ttu-id="ae428-119">範例3：從指定的來源尋找提供者</span><span class="sxs-lookup"><span data-stu-id="ae428-119">Example 3: Find a provider from a specified source</span></span>

```
PS C:\> Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

<span data-ttu-id="ae428-120">此命令會使用指定的套件來源，尋找可用的封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="ae428-120">This command finds a package provider available by using a specified package source.</span></span>

## <span data-ttu-id="ae428-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ae428-121">PARAMETERS</span></span>

### <span data-ttu-id="ae428-122">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="ae428-122">-AllVersions</span></span>

<span data-ttu-id="ae428-123">指出此 Cmdlet 會傳回所有可用版本的封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="ae428-123">Indicates that this cmdlet returns all available versions of the package provider.</span></span>
<span data-ttu-id="ae428-124">根據預設， **install-packageprovider** 只會傳回最新的可用版本。</span><span class="sxs-lookup"><span data-stu-id="ae428-124">By default, **Find-PackageProvider** only returns the newest available version.</span></span>

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

### <span data-ttu-id="ae428-125">-Credential</span><span class="sxs-lookup"><span data-stu-id="ae428-125">-Credential</span></span>

<span data-ttu-id="ae428-126">指定有權搜尋封裝提供者的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="ae428-126">Specifies a user account that has permission to search for package providers.</span></span>

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

### <span data-ttu-id="ae428-127">-Force</span><span class="sxs-lookup"><span data-stu-id="ae428-127">-Force</span></span>

<span data-ttu-id="ae428-128">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="ae428-128">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="ae428-129">目前，這相當於 *ForceBootstrap* 參數。</span><span class="sxs-lookup"><span data-stu-id="ae428-129">Currently, this is equivalent to the *ForceBootstrap* parameter.</span></span>

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

### <span data-ttu-id="ae428-130">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="ae428-130">-ForceBootstrap</span></span>

<span data-ttu-id="ae428-131">指出此 Cmdlet 會強制套件管理自動安裝封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="ae428-131">Indicates that this cmdlet forces Package Management to automatically install the package provider.</span></span>

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

### <span data-ttu-id="ae428-132">-Includedependencies 來</span><span class="sxs-lookup"><span data-stu-id="ae428-132">-IncludeDependencies</span></span>

<span data-ttu-id="ae428-133">指出此 Cmdlet 包含相依性。</span><span class="sxs-lookup"><span data-stu-id="ae428-133">Indicates that this cmdlet includes dependencies.</span></span>

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

### <span data-ttu-id="ae428-134">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="ae428-134">-MaximumVersion</span></span>

<span data-ttu-id="ae428-135">指定您想要尋找之封裝提供者的最大允許版本。</span><span class="sxs-lookup"><span data-stu-id="ae428-135">Specifies the maximum allowed version of the package provider that you want to find.</span></span>
<span data-ttu-id="ae428-136">如果您未新增此參數， **install-packageprovider** 會尋找提供者的最高可用版本。</span><span class="sxs-lookup"><span data-stu-id="ae428-136">If you do not add this parameter, **Find-PackageProvider** finds the highest available version of the provider.</span></span>

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

### <span data-ttu-id="ae428-137">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="ae428-137">-MinimumVersion</span></span>

<span data-ttu-id="ae428-138">指定您想要尋找的封裝提供者所允許的最低版本。</span><span class="sxs-lookup"><span data-stu-id="ae428-138">Specifies the minimum allowed version of the package provider that you want to find.</span></span>
<span data-ttu-id="ae428-139">如果您未新增此參數， **install-packageprovider** 會尋找最高可用的套件版本，此套件也會滿足 *MaximumVersion* 參數所指定的最大指定版本。</span><span class="sxs-lookup"><span data-stu-id="ae428-139">If you do not add this parameter, **Find-PackageProvider** finds the highest available version of the package that also satisfies any maximum specified version specified by the *MaximumVersion* parameter.</span></span>

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

### <span data-ttu-id="ae428-140">-Name</span><span class="sxs-lookup"><span data-stu-id="ae428-140">-Name</span></span>

<span data-ttu-id="ae428-141">指定一或多個封裝提供者模組名稱，或包含萬用字元的提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="ae428-141">Specifies one or more package provider module names, or provider names with wildcard characters.</span></span>
<span data-ttu-id="ae428-142">以逗號分隔多個封裝名稱。</span><span class="sxs-lookup"><span data-stu-id="ae428-142">Separate multiple package names with commas.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="ae428-143">-Proxy</span><span class="sxs-lookup"><span data-stu-id="ae428-143">-Proxy</span></span>

<span data-ttu-id="ae428-144">指定要求的 proxy 伺服器，而不是直接連接到網際網路資源。</span><span class="sxs-lookup"><span data-stu-id="ae428-144">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="ae428-145">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="ae428-145">-ProxyCredential</span></span>

<span data-ttu-id="ae428-146">指定具有使用 **Proxy** 參數所指定 Proxy 伺服器之權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="ae428-146">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="ae428-147">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="ae428-147">-RequiredVersion</span></span>

<span data-ttu-id="ae428-148">指定您想要尋找之封裝提供者的確切允許版本。</span><span class="sxs-lookup"><span data-stu-id="ae428-148">Specifies the exact allowed version of the package provider that you want to find.</span></span>
<span data-ttu-id="ae428-149">如果您未新增此參數，則 **install-packageprovider** 會尋找提供者的最高可用版本，同時也會滿足 *MaximumVersion* 參數所指定的最大版本。</span><span class="sxs-lookup"><span data-stu-id="ae428-149">If you do not add this parameter, **Find-PackageProvider** finds the highest available version of the provider that also satisfies any maximum version specified by the *MaximumVersion* parameter.</span></span>

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

### <span data-ttu-id="ae428-150">-Source</span><span class="sxs-lookup"><span data-stu-id="ae428-150">-Source</span></span>

<span data-ttu-id="ae428-151">指定一或多個套件來源。</span><span class="sxs-lookup"><span data-stu-id="ae428-151">Specifies one or more package sources.</span></span>
<span data-ttu-id="ae428-152">您可以使用 Get-PackageSource Cmdlet 取得可用套件來源的清單。</span><span class="sxs-lookup"><span data-stu-id="ae428-152">You can get a list of available package sources by using the Get-PackageSource cmdlet.</span></span>

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

### <span data-ttu-id="ae428-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ae428-153">CommonParameters</span></span>

<span data-ttu-id="ae428-154">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="ae428-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ae428-155">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="ae428-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ae428-156">輸入</span><span class="sxs-lookup"><span data-stu-id="ae428-156">INPUTS</span></span>

## <span data-ttu-id="ae428-157">輸出</span><span class="sxs-lookup"><span data-stu-id="ae428-157">OUTPUTS</span></span>

### <span data-ttu-id="ae428-158">SoftwareIdentity。</span><span class="sxs-lookup"><span data-stu-id="ae428-158">Microsoft.PackageManagement.Packaging.SoftwareIdentity</span></span>

<span data-ttu-id="ae428-159">此 Cmdlet 會傳回 **SoftwareIdentity** 物件。</span><span class="sxs-lookup"><span data-stu-id="ae428-159">This cmdlet returns a **SoftwareIdentity** object.</span></span>
<span data-ttu-id="ae428-160">您可以使用管線將 **SoftwareIdentity** 物件輸送到 **安裝 install-packageprovider** ，以安裝 **install-packageprovider** 的結果。</span><span class="sxs-lookup"><span data-stu-id="ae428-160">A **SoftwareIdentity** object can be piped into **Install-PackageProvider** to install the results of **Find-PackageProvider** .</span></span>

## <span data-ttu-id="ae428-161">注意</span><span class="sxs-lookup"><span data-stu-id="ae428-161">NOTES</span></span>

## <span data-ttu-id="ae428-162">相關連結</span><span class="sxs-lookup"><span data-stu-id="ae428-162">RELATED LINKS</span></span>

[<span data-ttu-id="ae428-163">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="ae428-163">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="ae428-164">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="ae428-164">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)

[<span data-ttu-id="ae428-165">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="ae428-165">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="ae428-166">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="ae428-166">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="ae428-167">Install-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="ae428-167">Install-PackageProvider</span></span>](Install-PackageProvider.md)
