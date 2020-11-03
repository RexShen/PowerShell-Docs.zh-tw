---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 05/24/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/unregister-packagesource?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PackageSource
ms.openlocfilehash: 7f923c3d1b35f956479abd17e14861835dc80497
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204168"
---
# <span data-ttu-id="ee93e-103">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="ee93e-103">Unregister-PackageSource</span></span>

## <span data-ttu-id="ee93e-104">概要</span><span class="sxs-lookup"><span data-stu-id="ee93e-104">SYNOPSIS</span></span>
<span data-ttu-id="ee93e-105">移除已註冊的套件來源。</span><span class="sxs-lookup"><span data-stu-id="ee93e-105">Removes a registered package source.</span></span>

## <span data-ttu-id="ee93e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ee93e-106">SYNTAX</span></span>

### <span data-ttu-id="ee93e-107">SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="ee93e-107">SourceBySearch</span></span>

```
Unregister-PackageSource [[-Source] <String>] [-Location <String>] [-Credential <PSCredential>]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String>] [<CommonParameters>]
```

### <span data-ttu-id="ee93e-108">SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="ee93e-108">SourceByInputObject</span></span>

```
Unregister-PackageSource -InputObject <PackageSource[]> [-Credential <PSCredential>] [-Force]
 [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ee93e-109">NuGet： SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="ee93e-109">NuGet:SourceByInputObject</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="ee93e-110">NuGet： SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="ee93e-110">NuGet:SourceBySearch</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="ee93e-111">PowerShellGet： SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="ee93e-111">PowerShellGet:SourceByInputObject</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

### <span data-ttu-id="ee93e-112">PowerShellGet： SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="ee93e-112">PowerShellGet:SourceBySearch</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="ee93e-113">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="ee93e-113">DESCRIPTION</span></span>

<span data-ttu-id="ee93e-114">此 `Unregister-PackageSource` Cmdlet 會移除註冊的套件來源。</span><span class="sxs-lookup"><span data-stu-id="ee93e-114">The `Unregister-PackageSource` cmdlet removes a registered package source.</span></span> <span data-ttu-id="ee93e-115">套件來源一律受套件提供者管理。</span><span class="sxs-lookup"><span data-stu-id="ee93e-115">Package sources are always managed by a package provider.</span></span> <span data-ttu-id="ee93e-116">若要尋找套件來源，請使用 `Get-PackageSource` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ee93e-116">To find package sources, use the `Get-PackageSource` cmdlet.</span></span>

## <span data-ttu-id="ee93e-117">範例</span><span class="sxs-lookup"><span data-stu-id="ee93e-117">EXAMPLES</span></span>

### <span data-ttu-id="ee93e-118">範例1：取消註冊 Nuget 提供者的套件來源</span><span class="sxs-lookup"><span data-stu-id="ee93e-118">Example 1: Unregister a package source for the Nuget provider</span></span>

<span data-ttu-id="ee93e-119">`Unregister-PackageSource`Cmdlet 會從本機電腦取消註冊封裝來源。</span><span class="sxs-lookup"><span data-stu-id="ee93e-119">The `Unregister-PackageSource` cmdlet unregisters a package source from the local computer.</span></span> <span data-ttu-id="ee93e-120">**Location** 和 **Provider** 參數可以用來進一步指定要移除的來源。</span><span class="sxs-lookup"><span data-stu-id="ee93e-120">The **Location** and **Provider** parameters can be used to further specify the source to remove.</span></span>

```
PS> Unregister-PackageSource -Source MyNuGet
```

<span data-ttu-id="ee93e-121">此 `Unregister-PackageSource` Cmdlet 會使用 **source** 參數來指定要移除的來源。</span><span class="sxs-lookup"><span data-stu-id="ee93e-121">The `Unregister-PackageSource` cmdlet uses the **Source** parameter to specify which source to remove.</span></span>

### <span data-ttu-id="ee93e-122">範例2：使用 Register-packagesource 物件取消註冊封裝</span><span class="sxs-lookup"><span data-stu-id="ee93e-122">Example 2: Use a PackageSource object to unregister a package</span></span>

<span data-ttu-id="ee93e-123">這個範例會使用 `Get-PackageSource` 和 `Unregister-PackageSource` 來取消註冊封裝來源。</span><span class="sxs-lookup"><span data-stu-id="ee93e-123">This example uses the `Get-PackageSource` and `Unregister-PackageSource` to unregister a package source.</span></span> <span data-ttu-id="ee93e-124">**Register-packagesource** 物件儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="ee93e-124">The **PackageSource** object is stored in a variable.</span></span>

```
PS> $pkgsource = Get-PackageSource -Name MyNuGet
PS> Unregister-PackageSource -InputObject $pkgsource
```

<span data-ttu-id="ee93e-125">`$pkgsource`變數會儲存 Cmdlet **PackageSource** 所建立的 register-packagesource `Get-PackageSource` 。</span><span class="sxs-lookup"><span data-stu-id="ee93e-125">The `$pkgsource` variable stores the **PackageSource** created by the `Get-PackageSource` cmdlet.</span></span>
<span data-ttu-id="ee93e-126">`Unregister-PackageSource` 使用 `$pkgsource` 做為 **InputObject** 參數的輸入。</span><span class="sxs-lookup"><span data-stu-id="ee93e-126">`Unregister-PackageSource` uses the `$pkgsource` as input to the **InputObject** parameter.</span></span>

<span data-ttu-id="ee93e-127">或者， `Unregister-PackageSource` Cmdlet 可以指定 **InputObject** 參數的值：</span><span class="sxs-lookup"><span data-stu-id="ee93e-127">As an alternative, the `Unregister-PackageSource` cmdlet can specify a value for the **InputObject** parameter:</span></span>

`Unregister-PackageSource -InputObject ( Get-PackageSource -Name MyNuGet )`

## <span data-ttu-id="ee93e-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ee93e-128">PARAMETERS</span></span>

### <span data-ttu-id="ee93e-129">-Read-configfile</span><span class="sxs-lookup"><span data-stu-id="ee93e-129">-ConfigFile</span></span>

<span data-ttu-id="ee93e-130">指定設定檔。</span><span class="sxs-lookup"><span data-stu-id="ee93e-130">Specifies a configuration file.</span></span>

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

### <span data-ttu-id="ee93e-131">-Credential</span><span class="sxs-lookup"><span data-stu-id="ee93e-131">-Credential</span></span>

<span data-ttu-id="ee93e-132">指定擁有存取電腦和執行命令之許可權的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="ee93e-132">Specifies a user account that has permission to access the computer and run commands.</span></span> <span data-ttu-id="ee93e-133">輸入使用者名稱（例如 **User01** 、 **Domain01\User01** ），或輸入由 Cmdlet 產生的 **PSCredential** 物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="ee93e-133">Type a user name, such as **User01** , **Domain01\User01** , or enter a **PSCredential** object, generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="ee93e-134">如果您輸入使用者名稱，系統就會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="ee93e-134">If you type a user name, you're prompted for a password.</span></span>

<span data-ttu-id="ee93e-135">如果未指定 **Credential** 參數，則會使用目前的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="ee93e-135">When the **Credential** parameter isn't specified, the current user account is used.</span></span>

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

### <span data-ttu-id="ee93e-136">-Force</span><span class="sxs-lookup"><span data-stu-id="ee93e-136">-Force</span></span>

<span data-ttu-id="ee93e-137">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="ee93e-137">Forces the command to run without asking for user confirmation.</span></span> <span data-ttu-id="ee93e-138">覆寫防止 `Unregister-PackageSource` 無法成功的限制，但安全性除外。</span><span class="sxs-lookup"><span data-stu-id="ee93e-138">Overrides restrictions that prevent `Unregister-PackageSource` from succeeding, with the exception of security.</span></span>

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

### <span data-ttu-id="ee93e-139">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="ee93e-139">-ForceBootstrap</span></span>

<span data-ttu-id="ee93e-140">指出 `Unregister-PackageSource` 強制 **PackageManagement** 自動卸載指定套件來源的封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="ee93e-140">Indicates that `Unregister-PackageSource` forces **PackageManagement** to automatically uninstall the package provider for the specified package source.</span></span>

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

### <span data-ttu-id="ee93e-141">-InputObject</span><span class="sxs-lookup"><span data-stu-id="ee93e-141">-InputObject</span></span>

<span data-ttu-id="ee93e-142">接受從 Cmdlet 指定 **register-packagesource** 物件的管線輸入 `Get-PackageSource` 。</span><span class="sxs-lookup"><span data-stu-id="ee93e-142">Accepts pipeline input that specifies the **PackageSource** object from the `Get-PackageSource` cmdlet.</span></span> <span data-ttu-id="ee93e-143">**InputObject** 接受 **register-packagesource** 物件做為 `Get-PackageSource` 值或包含物件的變數。</span><span class="sxs-lookup"><span data-stu-id="ee93e-143">**InputObject** accepts the **PackageSource** object as a `Get-PackageSource` value or a variable that contains the object.</span></span>

```yaml
Type: Microsoft.PackageManagement.Packaging.PackageSource[]
Parameter Sets: SourceByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ee93e-144">-Location</span><span class="sxs-lookup"><span data-stu-id="ee93e-144">-Location</span></span>

<span data-ttu-id="ee93e-145">指定封裝來源指向的位置。</span><span class="sxs-lookup"><span data-stu-id="ee93e-145">Specifies the location to which a package source points.</span></span> <span data-ttu-id="ee93e-146">此參數的值可以是 URI、檔案路徑或封裝提供者所支援的任何其他目的地格式。</span><span class="sxs-lookup"><span data-stu-id="ee93e-146">The value of this parameter can be a URI, a file path, or any other destination format that is supported by the package provider.</span></span>

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

### <span data-ttu-id="ee93e-147">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="ee93e-147">-PackageManagementProvider</span></span>

<span data-ttu-id="ee93e-148">指定 **PackageManagement** 提供者。</span><span class="sxs-lookup"><span data-stu-id="ee93e-148">Specifies the **PackageManagement** provider.</span></span>

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

### <span data-ttu-id="ee93e-149">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="ee93e-149">-ProviderName</span></span>

<span data-ttu-id="ee93e-150">指定提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="ee93e-150">Specifies the provider name.</span></span>

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

### <span data-ttu-id="ee93e-151">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="ee93e-151">-PublishLocation</span></span>

<span data-ttu-id="ee93e-152">指定發行位置。</span><span class="sxs-lookup"><span data-stu-id="ee93e-152">Specifies the publish location.</span></span>

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

### <span data-ttu-id="ee93e-153">->scriptpublishlocation</span><span class="sxs-lookup"><span data-stu-id="ee93e-153">-ScriptPublishLocation</span></span>

<span data-ttu-id="ee93e-154">指定腳本發行位置。</span><span class="sxs-lookup"><span data-stu-id="ee93e-154">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="ee93e-155">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="ee93e-155">-ScriptSourceLocation</span></span>

<span data-ttu-id="ee93e-156">指定腳本來源位置。</span><span class="sxs-lookup"><span data-stu-id="ee93e-156">Specifies the script source location.</span></span>

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

### <span data-ttu-id="ee93e-157">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="ee93e-157">-SkipValidate</span></span>

<span data-ttu-id="ee93e-158">略過驗證套件來源認證的參數。</span><span class="sxs-lookup"><span data-stu-id="ee93e-158">Switch that skips validating the credentials of a package source.</span></span>

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

### <span data-ttu-id="ee93e-159">-Source</span><span class="sxs-lookup"><span data-stu-id="ee93e-159">-Source</span></span>

<span data-ttu-id="ee93e-160">指定套件來源的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="ee93e-160">Specifies the friendly name of the package source.</span></span>

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases: Name

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ee93e-161">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ee93e-161">-Confirm</span></span>

<span data-ttu-id="ee93e-162">在執行之前提示您確認 `Unregister-PackageSource` 。</span><span class="sxs-lookup"><span data-stu-id="ee93e-162">Prompts you for confirmation before `Unregister-PackageSource` is run.</span></span>

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

### <span data-ttu-id="ee93e-163">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ee93e-163">-WhatIf</span></span>

<span data-ttu-id="ee93e-164">顯示執行 Cmdlet 時會發生 `Unregister-PackageSource` 的情況。</span><span class="sxs-lookup"><span data-stu-id="ee93e-164">Shows what would happen if `Unregister-PackageSource` cmdlet is run.</span></span> <span data-ttu-id="ee93e-165">不會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ee93e-165">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="ee93e-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ee93e-166">CommonParameters</span></span>

<span data-ttu-id="ee93e-167">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="ee93e-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ee93e-168">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="ee93e-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ee93e-169">輸入</span><span class="sxs-lookup"><span data-stu-id="ee93e-169">INPUTS</span></span>

### <span data-ttu-id="ee93e-170">`Unregister-PackageSource` 接受來自管線的 **register-packagesource** 物件做為輸入。</span><span class="sxs-lookup"><span data-stu-id="ee93e-170">`Unregister-PackageSource` accepts **PackageSource** objects from the pipeline as input.</span></span>

## <span data-ttu-id="ee93e-171">輸出</span><span class="sxs-lookup"><span data-stu-id="ee93e-171">OUTPUTS</span></span>

### <span data-ttu-id="ee93e-172">`Unregister-PackageSource` 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="ee93e-172">`Unregister-PackageSource` doesn't generate any output.</span></span>

## <span data-ttu-id="ee93e-173">注意</span><span class="sxs-lookup"><span data-stu-id="ee93e-173">NOTES</span></span>

<span data-ttu-id="ee93e-174">在命令中包含封裝提供者可以讓 Cmdlet 提供動態參數。</span><span class="sxs-lookup"><span data-stu-id="ee93e-174">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="ee93e-175">動態參數是封裝提供者專用的。</span><span class="sxs-lookup"><span data-stu-id="ee93e-175">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="ee93e-176">此 `Get-Help` Cmdlet 會列出 Cmdlet 的參數集，並包含提供者的參數集。</span><span class="sxs-lookup"><span data-stu-id="ee93e-176">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span>

## <span data-ttu-id="ee93e-177">相關連結</span><span class="sxs-lookup"><span data-stu-id="ee93e-177">RELATED LINKS</span></span>

[<span data-ttu-id="ee93e-178">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="ee93e-178">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="ee93e-179">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="ee93e-179">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="ee93e-180">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="ee93e-180">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="ee93e-181">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="ee93e-181">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="ee93e-182">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="ee93e-182">Set-PackageSource</span></span>](Set-PackageSource.md)

