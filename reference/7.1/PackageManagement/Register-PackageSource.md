---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 04/01/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/register-packagesource?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-PackageSource
ms.openlocfilehash: dfaccf285b8a53c1701919016509fd49eeee5da7
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891044"
---
# <span data-ttu-id="d8f87-103">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="d8f87-103">Register-PackageSource</span></span>

## <span data-ttu-id="d8f87-104">概要</span><span class="sxs-lookup"><span data-stu-id="d8f87-104">SYNOPSIS</span></span>
<span data-ttu-id="d8f87-105">加入指定套件提供者的套件來源。</span><span class="sxs-lookup"><span data-stu-id="d8f87-105">Adds a package source for a specified package provider.</span></span>

## <span data-ttu-id="d8f87-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d8f87-106">SYNTAX</span></span>

### <span data-ttu-id="d8f87-107">SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="d8f87-107">SourceBySearch</span></span>

```
Register-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String>]
 [[-Location] <String>] [-Credential <PSCredential>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ProviderName <String>] [<CommonParameters>]
```

### <span data-ttu-id="d8f87-108">NuGet</span><span class="sxs-lookup"><span data-stu-id="d8f87-108">NuGet</span></span>

```
Register-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String>]
 [[-Location] <String>] [-Credential <PSCredential>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="d8f87-109">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="d8f87-109">PowerShellGet</span></span>

```
Register-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String>]
 [[-Location] <String>] [-Credential <PSCredential>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="d8f87-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="d8f87-110">DESCRIPTION</span></span>

<span data-ttu-id="d8f87-111">指令 `Register-PackageSource` 程式會加入指定封裝提供者的封裝來源。</span><span class="sxs-lookup"><span data-stu-id="d8f87-111">The `Register-PackageSource` cmdlet adds a package source for a specified package provider.</span></span> <span data-ttu-id="d8f87-112">套件來源一律受套件提供者管理。</span><span class="sxs-lookup"><span data-stu-id="d8f87-112">Package sources are always managed by a package provider.</span></span> <span data-ttu-id="d8f87-113">如果套件提供者不能新增或取代套件來源，提供者會產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="d8f87-113">If the package provider cannot add or replace a package source, the provider generates an error message.</span></span>

## <span data-ttu-id="d8f87-114">範例</span><span class="sxs-lookup"><span data-stu-id="d8f87-114">EXAMPLES</span></span>

### <span data-ttu-id="d8f87-115">範例 1：註冊 NuGet 提供者的套件來源</span><span class="sxs-lookup"><span data-stu-id="d8f87-115">Example 1: Register a package source for the NuGet provider</span></span>

<span data-ttu-id="d8f87-116">此命令會註冊一個套件來源（ **NuGet** 提供者的 web 型位置）。</span><span class="sxs-lookup"><span data-stu-id="d8f87-116">This command registers a package source, a web-based location for the **NuGet** provider.</span></span> <span data-ttu-id="d8f87-117">依預設，來源不受信任。</span><span class="sxs-lookup"><span data-stu-id="d8f87-117">By default, sources aren't trusted.</span></span> <span data-ttu-id="d8f87-118">安裝封裝之前，系統會提示您確認來源是受信任的。</span><span class="sxs-lookup"><span data-stu-id="d8f87-118">You are prompted to confirm the source is trusted before packages are installed.</span></span> <span data-ttu-id="d8f87-119">若要覆寫預設值，請使用 `-Trusted` 參數。</span><span class="sxs-lookup"><span data-stu-id="d8f87-119">To override the default, use the `-Trusted` parameter.</span></span>

```powershell
Register-PackageSource -Name MyNuGet -Location https://www.nuget.org/api/v2 -ProviderName NuGet
```

```Output
Name          ProviderName     IsTrusted  Location
----          ------------     ---------  --------
MyNuGet       NuGet            False      https://www.nuget.org/api/v2
```

## <span data-ttu-id="d8f87-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d8f87-120">PARAMETERS</span></span>

### <span data-ttu-id="d8f87-121">-Read-configfile</span><span class="sxs-lookup"><span data-stu-id="d8f87-121">-ConfigFile</span></span>

<span data-ttu-id="d8f87-122">指定設定檔。</span><span class="sxs-lookup"><span data-stu-id="d8f87-122">Specifies a configuration file.</span></span>

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

### <span data-ttu-id="d8f87-123">-Credential</span><span class="sxs-lookup"><span data-stu-id="d8f87-123">-Credential</span></span>

<span data-ttu-id="d8f87-124">指定有權存取已驗證位置的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="d8f87-124">Specifies a user account that has permission to access the authenticated location.</span></span>

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

### <span data-ttu-id="d8f87-125">-Force</span><span class="sxs-lookup"><span data-stu-id="d8f87-125">-Force</span></span>

<span data-ttu-id="d8f87-126">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="d8f87-126">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="d8f87-127">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="d8f87-127">-ForceBootstrap</span></span>

<span data-ttu-id="d8f87-128">指示此 Cmdlet 會自動安裝套件提供者。</span><span class="sxs-lookup"><span data-stu-id="d8f87-128">Indicates that this cmdlet automatically installs the package provider.</span></span>

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

### <span data-ttu-id="d8f87-129">-Location</span><span class="sxs-lookup"><span data-stu-id="d8f87-129">-Location</span></span>

<span data-ttu-id="d8f87-130">指定套件來源位置。</span><span class="sxs-lookup"><span data-stu-id="d8f87-130">Specifies the package source location.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8f87-131">-Name</span><span class="sxs-lookup"><span data-stu-id="d8f87-131">-Name</span></span>

<span data-ttu-id="d8f87-132">指定要註冊的套件來源名稱。</span><span class="sxs-lookup"><span data-stu-id="d8f87-132">Specifies the name of the package source to register.</span></span>

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

### <span data-ttu-id="d8f87-133">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="d8f87-133">-PackageManagementProvider</span></span>

<span data-ttu-id="d8f87-134">指定套件管理提供者。</span><span class="sxs-lookup"><span data-stu-id="d8f87-134">Specifies the Package Management provider.</span></span>

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

### <span data-ttu-id="d8f87-135">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="d8f87-135">-ProviderName</span></span>

<span data-ttu-id="d8f87-136">指定封裝提供者的名稱。</span><span class="sxs-lookup"><span data-stu-id="d8f87-136">Specifies the package provider's name.</span></span>

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

### <span data-ttu-id="d8f87-137">-Proxy</span><span class="sxs-lookup"><span data-stu-id="d8f87-137">-Proxy</span></span>

<span data-ttu-id="d8f87-138">為要求指定 proxy 伺服器，而不是直接連線到網際網路資源。</span><span class="sxs-lookup"><span data-stu-id="d8f87-138">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="d8f87-139">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="d8f87-139">-ProxyCredential</span></span>

<span data-ttu-id="d8f87-140">指定具有使用 **Proxy** 參數所指定 Proxy 伺服器之權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="d8f87-140">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="d8f87-141">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="d8f87-141">-PublishLocation</span></span>

<span data-ttu-id="d8f87-142">指定發行位置。</span><span class="sxs-lookup"><span data-stu-id="d8f87-142">Specifies the publish location.</span></span>

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

### <span data-ttu-id="d8f87-143">->scriptpublishlocation</span><span class="sxs-lookup"><span data-stu-id="d8f87-143">-ScriptPublishLocation</span></span>

<span data-ttu-id="d8f87-144">指定腳本發行位置。</span><span class="sxs-lookup"><span data-stu-id="d8f87-144">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="d8f87-145">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="d8f87-145">-ScriptSourceLocation</span></span>

<span data-ttu-id="d8f87-146">指定腳本來源位置。</span><span class="sxs-lookup"><span data-stu-id="d8f87-146">Specifies the script source location.</span></span>

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

### <span data-ttu-id="d8f87-147">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="d8f87-147">-SkipValidate</span></span>

<span data-ttu-id="d8f87-148">略過驗證套件來源認證的參數。</span><span class="sxs-lookup"><span data-stu-id="d8f87-148">Switch that skips validating the credentials of a package source.</span></span>

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

### <span data-ttu-id="d8f87-149">-Trusted</span><span class="sxs-lookup"><span data-stu-id="d8f87-149">-Trusted</span></span>

<span data-ttu-id="d8f87-150">指示套件來源受信任。</span><span class="sxs-lookup"><span data-stu-id="d8f87-150">Indicates that the package source is trusted.</span></span>

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

### <span data-ttu-id="d8f87-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d8f87-151">-Confirm</span></span>

<span data-ttu-id="d8f87-152">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="d8f87-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="d8f87-153">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d8f87-153">-WhatIf</span></span>

<span data-ttu-id="d8f87-154">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="d8f87-154">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="d8f87-155">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="d8f87-155">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="d8f87-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d8f87-156">CommonParameters</span></span>

<span data-ttu-id="d8f87-157">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="d8f87-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d8f87-158">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="d8f87-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d8f87-159">輸入</span><span class="sxs-lookup"><span data-stu-id="d8f87-159">INPUTS</span></span>

## <span data-ttu-id="d8f87-160">輸出</span><span class="sxs-lookup"><span data-stu-id="d8f87-160">OUTPUTS</span></span>

## <span data-ttu-id="d8f87-161">注意</span><span class="sxs-lookup"><span data-stu-id="d8f87-161">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d8f87-162">從2020年4月起，PowerShell 資源庫不再支援傳輸層安全性 (TLS) 1.0 和1.1 版。</span><span class="sxs-lookup"><span data-stu-id="d8f87-162">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="d8f87-163">如果您不是使用 TLS 1.2 或更高版本，當您嘗試存取 PowerShell 資源庫時，將會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="d8f87-163">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="d8f87-164">使用下列命令，以確保您使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="d8f87-164">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="d8f87-165">如需詳細資訊，請參閱 PowerShell blog 中的 [公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 。</span><span class="sxs-lookup"><span data-stu-id="d8f87-165">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="d8f87-166">相關連結</span><span class="sxs-lookup"><span data-stu-id="d8f87-166">RELATED LINKS</span></span>

[<span data-ttu-id="d8f87-167">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="d8f87-167">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="d8f87-168">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="d8f87-168">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="d8f87-169">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="d8f87-169">Set-PackageSource</span></span>](Set-PackageSource.md)

[<span data-ttu-id="d8f87-170">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="d8f87-170">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
