---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 03/29/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-packagesource?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PackageSource
ms.openlocfilehash: 8428f51c27cf52a7e0910a7b6c759e1f75b89339
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94890108"
---
# <span data-ttu-id="98dfa-103">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="98dfa-103">Get-PackageSource</span></span>

## <span data-ttu-id="98dfa-104">概要</span><span class="sxs-lookup"><span data-stu-id="98dfa-104">SYNOPSIS</span></span>
<span data-ttu-id="98dfa-105">取得為封裝提供者註冊的封裝來源清單。</span><span class="sxs-lookup"><span data-stu-id="98dfa-105">Gets a list of package sources that are registered for a package provider.</span></span>

## <span data-ttu-id="98dfa-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="98dfa-106">SYNTAX</span></span>

### <span data-ttu-id="98dfa-107">NuGet</span><span class="sxs-lookup"><span data-stu-id="98dfa-107">NuGet</span></span>

```
Get-PackageSource [[-Name] <String>] [-Location <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="98dfa-108">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="98dfa-108">PowerShellGet</span></span>

```
Get-PackageSource [[-Name] <String>] [-Location <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="98dfa-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="98dfa-109">DESCRIPTION</span></span>

<span data-ttu-id="98dfa-110">此 `Get-PackageSource` Cmdlet 會取得在本機電腦上向 **PackageManagement** 註冊的套件來源清單。</span><span class="sxs-lookup"><span data-stu-id="98dfa-110">The `Get-PackageSource` cmdlet gets a list of package sources that are registered with **PackageManagement** on the local computer.</span></span> <span data-ttu-id="98dfa-111">如果您指定了封裝提供者，則 `Get-PackageSource` 只會取得與指定的提供者相關聯的來源。</span><span class="sxs-lookup"><span data-stu-id="98dfa-111">If you specify a package provider, `Get-PackageSource` gets only those sources that are associated with the specified provider.</span></span> <span data-ttu-id="98dfa-112">否則，此命令會傳回所有已向 **PackageManagement** 註冊的套件來源。</span><span class="sxs-lookup"><span data-stu-id="98dfa-112">Otherwise, the command returns all package sources that are registered with **PackageManagement**.</span></span>

## <span data-ttu-id="98dfa-113">範例</span><span class="sxs-lookup"><span data-stu-id="98dfa-113">EXAMPLES</span></span>

### <span data-ttu-id="98dfa-114">範例1：取得所有套件來源</span><span class="sxs-lookup"><span data-stu-id="98dfa-114">Example 1: Get all package sources</span></span>

<span data-ttu-id="98dfa-115">此 `Get-PackageSource` Cmdlet 會取得在本機電腦上向 **PackageManagement** 註冊的所有套件來源。</span><span class="sxs-lookup"><span data-stu-id="98dfa-115">The `Get-PackageSource` cmdlet gets all package sources that are registered with **PackageManagement** on the local computer.</span></span>

```powershell
Get-PackageSource
```

```Output
Name                 ProviderName     IsTrusted  Location
----                 ------------     ---------  --------
LocalPackages        NuGet            False      C:\LocalPkg\
MyNuget              NuGet            False      https://www.nuget.org/api/v2
PSGallery            PowerShellGet    False      https://www.powershellgallery.com/api/v2
```

### <span data-ttu-id="98dfa-116">範例2：取得特定提供者的所有套件來源</span><span class="sxs-lookup"><span data-stu-id="98dfa-116">Example 2: Get all package sources for a specific provider</span></span>

<span data-ttu-id="98dfa-117">此命令會取得針對特定提供者註冊的套件來源。</span><span class="sxs-lookup"><span data-stu-id="98dfa-117">This command gets package sources that are registered for a specific provider.</span></span>

```powershell
Get-PackageSource -ProviderName NuGet
```

```Output
Name                 ProviderName     IsTrusted  Location
----                 ------------     ---------  --------
LocalPackages        NuGet            False      C:\LocalPkg\
MyNuget              NuGet            False      https://www.nuget.org/api/v2
```

<span data-ttu-id="98dfa-118">`Get-PackageSource` 使用 **ProviderName** 參數來取得為 **NuGet** 提供者註冊的套件來源。</span><span class="sxs-lookup"><span data-stu-id="98dfa-118">`Get-PackageSource` uses the **ProviderName** parameter to get package sources that are registered for the **NuGet** provider.</span></span>

### <span data-ttu-id="98dfa-119">範例3：從封裝提供者取得來源</span><span class="sxs-lookup"><span data-stu-id="98dfa-119">Example 3: Get sources from a package provider</span></span>

<span data-ttu-id="98dfa-120">此命令會使用封裝提供者來取得套件來源。</span><span class="sxs-lookup"><span data-stu-id="98dfa-120">This command uses a package provider to get package sources.</span></span>

```powershell
Get-PackageProvider -Name NuGet | Get-PackageSource
```

```Output
Name                 ProviderName     IsTrusted  Location
----                 ------------     ---------  --------
LocalPackages        NuGet            False      C:\LocalPkg\
MyNuget              NuGet            False      https://www.nuget.org/api/v2
```

<span data-ttu-id="98dfa-121">`Get-PackageProvider` 使用 **Name** 參數指定提供者名稱（ **NuGet**）。</span><span class="sxs-lookup"><span data-stu-id="98dfa-121">`Get-PackageProvider` uses the **Name** parameter specify the provider name, **NuGet**.</span></span> <span data-ttu-id="98dfa-122">物件會向下傳送到管線 `Get-PackageSource` 。</span><span class="sxs-lookup"><span data-stu-id="98dfa-122">The object is sent down the pipeline to `Get-PackageSource`.</span></span>

## <span data-ttu-id="98dfa-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="98dfa-123">PARAMETERS</span></span>

### <span data-ttu-id="98dfa-124">-Read-configfile</span><span class="sxs-lookup"><span data-stu-id="98dfa-124">-ConfigFile</span></span>

<span data-ttu-id="98dfa-125">指定設定檔。</span><span class="sxs-lookup"><span data-stu-id="98dfa-125">Specifies a configuration file.</span></span>

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

### <span data-ttu-id="98dfa-126">-Force</span><span class="sxs-lookup"><span data-stu-id="98dfa-126">-Force</span></span>

<span data-ttu-id="98dfa-127">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="98dfa-127">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="98dfa-128">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="98dfa-128">-ForceBootstrap</span></span>

<span data-ttu-id="98dfa-129">指出此 Cmdlet 會強制 **PackageManagement** 自動安裝封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="98dfa-129">Indicates that this cmdlet forces **PackageManagement** to automatically install a package provider.</span></span>

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

### <span data-ttu-id="98dfa-130">-Location</span><span class="sxs-lookup"><span data-stu-id="98dfa-130">-Location</span></span>

<span data-ttu-id="98dfa-131">指定封裝管理來源或存放庫的位置。</span><span class="sxs-lookup"><span data-stu-id="98dfa-131">Specifies the location of a package management source or repository.</span></span>

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

### <span data-ttu-id="98dfa-132">-Name</span><span class="sxs-lookup"><span data-stu-id="98dfa-132">-Name</span></span>

<span data-ttu-id="98dfa-133">指定封裝管理來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="98dfa-133">Specifies the name of a package management source.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="98dfa-134">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="98dfa-134">-PackageManagementProvider</span></span>

<span data-ttu-id="98dfa-135">指定套件管理提供者。</span><span class="sxs-lookup"><span data-stu-id="98dfa-135">Specifies a package management provider.</span></span>

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

### <span data-ttu-id="98dfa-136">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="98dfa-136">-ProviderName</span></span>

<span data-ttu-id="98dfa-137">指定一或多個封裝提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="98dfa-137">Specifies one or more package provider names.</span></span> <span data-ttu-id="98dfa-138">以逗號分隔多個封裝提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="98dfa-138">Separate multiple package provider names with commas.</span></span>
<span data-ttu-id="98dfa-139">使用 `Get-PackageProvider` 取得可用封裝提供者的清單。</span><span class="sxs-lookup"><span data-stu-id="98dfa-139">Use `Get-PackageProvider` to get a list of available package providers.</span></span>

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

### <span data-ttu-id="98dfa-140">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="98dfa-140">-PublishLocation</span></span>

<span data-ttu-id="98dfa-141">指定封裝來源的發佈位置。</span><span class="sxs-lookup"><span data-stu-id="98dfa-141">Specifies the publish location for the package source.</span></span>

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

### <span data-ttu-id="98dfa-142">->scriptpublishlocation</span><span class="sxs-lookup"><span data-stu-id="98dfa-142">-ScriptPublishLocation</span></span>

<span data-ttu-id="98dfa-143">指定腳本發行位置。</span><span class="sxs-lookup"><span data-stu-id="98dfa-143">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="98dfa-144">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="98dfa-144">-ScriptSourceLocation</span></span>

<span data-ttu-id="98dfa-145">指定腳本來源位置。</span><span class="sxs-lookup"><span data-stu-id="98dfa-145">Specifies the script source location.</span></span>

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

### <span data-ttu-id="98dfa-146">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="98dfa-146">-SkipValidate</span></span>

<span data-ttu-id="98dfa-147">略過驗證套件來源認證的參數。</span><span class="sxs-lookup"><span data-stu-id="98dfa-147">Switch that skips validating the credentials of a package source.</span></span>

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

### <span data-ttu-id="98dfa-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="98dfa-148">CommonParameters</span></span>

<span data-ttu-id="98dfa-149">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="98dfa-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="98dfa-150">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="98dfa-150">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="98dfa-151">輸入</span><span class="sxs-lookup"><span data-stu-id="98dfa-151">INPUTS</span></span>

## <span data-ttu-id="98dfa-152">輸出</span><span class="sxs-lookup"><span data-stu-id="98dfa-152">OUTPUTS</span></span>

### <span data-ttu-id="98dfa-153">Register-packagesource []</span><span class="sxs-lookup"><span data-stu-id="98dfa-153">PackageSource[]</span></span>

<span data-ttu-id="98dfa-154">指定一或多個套件來源。</span><span class="sxs-lookup"><span data-stu-id="98dfa-154">Specifies one or more package sources.</span></span>

## <span data-ttu-id="98dfa-155">注意</span><span class="sxs-lookup"><span data-stu-id="98dfa-155">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="98dfa-156">從2020年4月起，PowerShell 資源庫不再支援傳輸層安全性 (TLS) 1.0 和1.1 版。</span><span class="sxs-lookup"><span data-stu-id="98dfa-156">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="98dfa-157">如果您不是使用 TLS 1.2 或更高版本，當您嘗試存取 PowerShell 資源庫時，將會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="98dfa-157">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="98dfa-158">使用下列命令，以確保您使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="98dfa-158">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="98dfa-159">如需詳細資訊，請參閱 PowerShell blog 中的 [公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 。</span><span class="sxs-lookup"><span data-stu-id="98dfa-159">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="98dfa-160">相關連結</span><span class="sxs-lookup"><span data-stu-id="98dfa-160">RELATED LINKS</span></span>

[<span data-ttu-id="98dfa-161">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="98dfa-161">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="98dfa-162">Find-Package</span><span class="sxs-lookup"><span data-stu-id="98dfa-162">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="98dfa-163">Get-Package</span><span class="sxs-lookup"><span data-stu-id="98dfa-163">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="98dfa-164">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="98dfa-164">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="98dfa-165">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="98dfa-165">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="98dfa-166">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="98dfa-166">Set-PackageSource</span></span>](Set-PackageSource.md)

[<span data-ttu-id="98dfa-167">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="98dfa-167">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
