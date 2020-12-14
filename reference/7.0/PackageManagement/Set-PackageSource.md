---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 04/03/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/set-packagesource?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PackageSource
ms.openlocfilehash: 67a5a97c4e29556c9b93a17d25576d4bd6eaea0c
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892700"
---
# <span data-ttu-id="d2099-103">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="d2099-103">Set-PackageSource</span></span>

## <span data-ttu-id="d2099-104">概要</span><span class="sxs-lookup"><span data-stu-id="d2099-104">SYNOPSIS</span></span>
<span data-ttu-id="d2099-105">取代指定封裝提供者的封裝來源。</span><span class="sxs-lookup"><span data-stu-id="d2099-105">Replaces a package source for a specified package provider.</span></span>

## <span data-ttu-id="d2099-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d2099-106">SYNTAX</span></span>

### <span data-ttu-id="d2099-107">SourceBySearch (預設) </span><span class="sxs-lookup"><span data-stu-id="d2099-107">SourceBySearch (Default)</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [[-Name] <String>] [-Location <String>] [-NewLocation <String>] [-NewName <String>] [-Trusted]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String>] [<CommonParameters>]
```

### <span data-ttu-id="d2099-108">SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="d2099-108">SourceByInputObject</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] -InputObject <PackageSource> [-Force]
 [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d2099-109">NuGet： SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="d2099-109">NuGet:SourceByInputObject</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="d2099-110">NuGet： SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="d2099-110">NuGet:SourceBySearch</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="d2099-111">PowerShellGet： SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="d2099-111">PowerShellGet:SourceByInputObject</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

### <span data-ttu-id="d2099-112">PowerShellGet： SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="d2099-112">PowerShellGet:SourceBySearch</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="d2099-113">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="d2099-113">DESCRIPTION</span></span>

<span data-ttu-id="d2099-114">會 `Set-PackageSource` 取代指定封裝提供者的封裝來源。</span><span class="sxs-lookup"><span data-stu-id="d2099-114">The `Set-PackageSource` replaces a package source for a specified package provider.</span></span> <span data-ttu-id="d2099-115">套件來源一律受套件提供者管理。</span><span class="sxs-lookup"><span data-stu-id="d2099-115">Package sources are always managed by a package provider.</span></span>

## <span data-ttu-id="d2099-116">範例</span><span class="sxs-lookup"><span data-stu-id="d2099-116">EXAMPLES</span></span>

### <span data-ttu-id="d2099-117">範例1：變更套件來源</span><span class="sxs-lookup"><span data-stu-id="d2099-117">Example 1: Change a package source</span></span>

<span data-ttu-id="d2099-118">此命令會變更套件來源的現有名稱。</span><span class="sxs-lookup"><span data-stu-id="d2099-118">This command changes the existing name of a package source.</span></span> <span data-ttu-id="d2099-119">來源設定為 [ **受信任**]，這可在安裝套件時排除提示以驗證來源。</span><span class="sxs-lookup"><span data-stu-id="d2099-119">The source is set to **Trusted**, which eliminates prompts to verify the source when packages are installed.</span></span>

```
PS C:\> Set-PackageSource -Name MyNuget -NewName NewNuGet -Trusted -ProviderName NuGet
```

## <span data-ttu-id="d2099-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d2099-120">PARAMETERS</span></span>

### <span data-ttu-id="d2099-121">-Read-configfile</span><span class="sxs-lookup"><span data-stu-id="d2099-121">-ConfigFile</span></span>

<span data-ttu-id="d2099-122">指定設定檔。</span><span class="sxs-lookup"><span data-stu-id="d2099-122">Specifies a configuration file.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:SourceByInputObject, NuGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d2099-123">-Credential</span><span class="sxs-lookup"><span data-stu-id="d2099-123">-Credential</span></span>

<span data-ttu-id="d2099-124">指定具有安裝套件提供者權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="d2099-124">Specifies a user account that has permission to install package providers.</span></span>

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

### <span data-ttu-id="d2099-125">-Force</span><span class="sxs-lookup"><span data-stu-id="d2099-125">-Force</span></span>

<span data-ttu-id="d2099-126">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="d2099-126">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="d2099-127">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="d2099-127">-ForceBootstrap</span></span>

<span data-ttu-id="d2099-128">指出 `Set-PackageSource` 強制 **PackageManagement** 自動安裝封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="d2099-128">Indicates that `Set-PackageSource` forces **PackageManagement** to automatically install the package provider.</span></span>

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

### <span data-ttu-id="d2099-129">-InputObject</span><span class="sxs-lookup"><span data-stu-id="d2099-129">-InputObject</span></span>

<span data-ttu-id="d2099-130">指定代表要變更之封裝的封裝來源識別碼物件。</span><span class="sxs-lookup"><span data-stu-id="d2099-130">Specifies a package source ID object that represents the package that you want to change.</span></span> <span data-ttu-id="d2099-131">套件來源識別碼是 Cmdlet 結果的一部分 `Get-PackageSource` 。</span><span class="sxs-lookup"><span data-stu-id="d2099-131">Package source IDs are part of the results of the `Get-PackageSource` cmdlet.</span></span>

```yaml
Type: Microsoft.PackageManagement.Packaging.PackageSource
Parameter Sets: SourceByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d2099-132">-Location</span><span class="sxs-lookup"><span data-stu-id="d2099-132">-Location</span></span>

<span data-ttu-id="d2099-133">指定目前的套件來源位置。</span><span class="sxs-lookup"><span data-stu-id="d2099-133">Specifies the current package source location.</span></span> <span data-ttu-id="d2099-134">此值可以是 URI、檔案路徑或封裝提供者所支援的任何其他目的地格式。</span><span class="sxs-lookup"><span data-stu-id="d2099-134">The value can be a URI, a file path, or any other destination format supported by the package provider.</span></span>

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d2099-135">-Name</span><span class="sxs-lookup"><span data-stu-id="d2099-135">-Name</span></span>

<span data-ttu-id="d2099-136">指定套件來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="d2099-136">Specifies a package source's name.</span></span>

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases: SourceName

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d2099-137">-NewLocation</span><span class="sxs-lookup"><span data-stu-id="d2099-137">-NewLocation</span></span>

<span data-ttu-id="d2099-138">指定套件來源的新位置。</span><span class="sxs-lookup"><span data-stu-id="d2099-138">Specifies the new location for a package source.</span></span> <span data-ttu-id="d2099-139">此值可以是 URI、檔案路徑或封裝提供者所支援的任何其他目的地格式。</span><span class="sxs-lookup"><span data-stu-id="d2099-139">The value can be a URI, a file path, or any other destination format supported by the package provider.</span></span>

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

### <span data-ttu-id="d2099-140">-NewName</span><span class="sxs-lookup"><span data-stu-id="d2099-140">-NewName</span></span>

<span data-ttu-id="d2099-141">指定您指派給套件來源的新名稱。</span><span class="sxs-lookup"><span data-stu-id="d2099-141">Specifies the new name you assign to a package source.</span></span>

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

### <span data-ttu-id="d2099-142">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="d2099-142">-PackageManagementProvider</span></span>

<span data-ttu-id="d2099-143">指定套件管理提供者。</span><span class="sxs-lookup"><span data-stu-id="d2099-143">Specifies a package management provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d2099-144">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="d2099-144">-ProviderName</span></span>

<span data-ttu-id="d2099-145">指定提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="d2099-145">Specifies a provider name.</span></span>

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d2099-146">-Proxy</span><span class="sxs-lookup"><span data-stu-id="d2099-146">-Proxy</span></span>

<span data-ttu-id="d2099-147">指定要求的 proxy 伺服器，而不是直接連接到網際網路資源。</span><span class="sxs-lookup"><span data-stu-id="d2099-147">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="d2099-148">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="d2099-148">-ProxyCredential</span></span>

<span data-ttu-id="d2099-149">指定具有使用 **Proxy** 參數所指定 Proxy 伺服器之權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="d2099-149">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="d2099-150">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="d2099-150">-PublishLocation</span></span>

<span data-ttu-id="d2099-151">指定發行位置。</span><span class="sxs-lookup"><span data-stu-id="d2099-151">Specifies the publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d2099-152">->scriptpublishlocation</span><span class="sxs-lookup"><span data-stu-id="d2099-152">-ScriptPublishLocation</span></span>

<span data-ttu-id="d2099-153">指定腳本發行位置。</span><span class="sxs-lookup"><span data-stu-id="d2099-153">Specifies the script publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d2099-154">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="d2099-154">-ScriptSourceLocation</span></span>

<span data-ttu-id="d2099-155">指定腳本來源位置。</span><span class="sxs-lookup"><span data-stu-id="d2099-155">Specifies the script source location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d2099-156">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="d2099-156">-SkipValidate</span></span>

<span data-ttu-id="d2099-157">略過驗證套件來源認證的參數。</span><span class="sxs-lookup"><span data-stu-id="d2099-157">Switch that skips validating the credentials of a package source.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:SourceByInputObject, NuGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d2099-158">-Trusted</span><span class="sxs-lookup"><span data-stu-id="d2099-158">-Trusted</span></span>

<span data-ttu-id="d2099-159">指出來源是信任的封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="d2099-159">Indicates that the source is a trusted package provider.</span></span> <span data-ttu-id="d2099-160">信任來源不會提示您進行驗證，以安裝套件。</span><span class="sxs-lookup"><span data-stu-id="d2099-160">Trusted sources don't prompt for verification to install packages.</span></span>

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

### <span data-ttu-id="d2099-161">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d2099-161">-Confirm</span></span>

<span data-ttu-id="d2099-162">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="d2099-162">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="d2099-163">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d2099-163">-WhatIf</span></span>

<span data-ttu-id="d2099-164">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="d2099-164">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="d2099-165">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="d2099-165">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="d2099-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d2099-166">CommonParameters</span></span>

<span data-ttu-id="d2099-167">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="d2099-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d2099-168">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="d2099-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d2099-169">輸入</span><span class="sxs-lookup"><span data-stu-id="d2099-169">INPUTS</span></span>

### <span data-ttu-id="d2099-170">`Set-PackageSource` 不接受管線輸入。</span><span class="sxs-lookup"><span data-stu-id="d2099-170">`Set-PackageSource` doesn't accept pipeline input.</span></span>

## <span data-ttu-id="d2099-171">輸出</span><span class="sxs-lookup"><span data-stu-id="d2099-171">OUTPUTS</span></span>

### <span data-ttu-id="d2099-172">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="d2099-172">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="d2099-173">注意</span><span class="sxs-lookup"><span data-stu-id="d2099-173">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d2099-174">從2020年4月起，PowerShell 資源庫不再支援傳輸層安全性 (TLS) 1.0 和1.1 版。</span><span class="sxs-lookup"><span data-stu-id="d2099-174">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="d2099-175">如果您不是使用 TLS 1.2 或更高版本，當您嘗試存取 PowerShell 資源庫時，將會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="d2099-175">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="d2099-176">使用下列命令，以確保您使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="d2099-176">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="d2099-177">如需詳細資訊，請參閱 PowerShell blog 中的 [公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 。</span><span class="sxs-lookup"><span data-stu-id="d2099-177">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="d2099-178">相關連結</span><span class="sxs-lookup"><span data-stu-id="d2099-178">RELATED LINKS</span></span>

[<span data-ttu-id="d2099-179">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="d2099-179">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="d2099-180">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="d2099-180">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="d2099-181">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="d2099-181">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="d2099-182">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="d2099-182">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
