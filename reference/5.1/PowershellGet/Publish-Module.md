---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 10/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/publish-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Publish-Module
ms.openlocfilehash: 50f873e6691ead7c220b6250458f4fdf8a90af22
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203904"
---
# <span data-ttu-id="254c6-103">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="254c6-103">Publish-Module</span></span>

## <span data-ttu-id="254c6-104">概要</span><span class="sxs-lookup"><span data-stu-id="254c6-104">SYNOPSIS</span></span>
<span data-ttu-id="254c6-105">將指定的模組從本機電腦發行至線上資源庫。</span><span class="sxs-lookup"><span data-stu-id="254c6-105">Publishes a specified module from the local computer to an online gallery.</span></span>

## <span data-ttu-id="254c6-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="254c6-106">SYNTAX</span></span>

### <span data-ttu-id="254c6-107">ModuleNameParameterSet (預設) </span><span class="sxs-lookup"><span data-stu-id="254c6-107">ModuleNameParameterSet (Default)</span></span>

```
Publish-Module -Name <String> [-RequiredVersion <String>] [-NuGetApiKey <String>]
 [-Repository <String>] [-Credential <PSCredential>] [-FormatVersion <Version>]
 [-ReleaseNotes <String[]>] [-Tags <String[]>] [-LicenseUri <Uri>] [-IconUri <Uri>]
 [-ProjectUri <Uri>] [-Exclude <String[]>] [-Force] [-AllowPrerelease] [-SkipAutomaticTags]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="254c6-108">ModulePathParameterSet</span><span class="sxs-lookup"><span data-stu-id="254c6-108">ModulePathParameterSet</span></span>

```
Publish-Module -Path <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-FormatVersion <Version>] [-ReleaseNotes <String[]>]
 [-Tags <String[]>] [-LicenseUri <Uri>] [-IconUri <Uri>] [-ProjectUri <Uri>] [-Force]
 [-SkipAutomaticTags] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="254c6-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="254c6-109">DESCRIPTION</span></span>

<span data-ttu-id="254c6-110">此 `Publish-Module` Cmdlet 會使用 API 金鑰（儲存為資源庫中使用者設定檔的一部分），將模組發佈至以 NuGet 為基礎的線上資源庫。</span><span class="sxs-lookup"><span data-stu-id="254c6-110">The `Publish-Module` cmdlet publishes a module to an online NuGet-based gallery by using an API key, stored as part of a user's profile in the gallery.</span></span> <span data-ttu-id="254c6-111">您可以指定依模組名稱，或依包含模組之資料夾的路徑來發行模組。</span><span class="sxs-lookup"><span data-stu-id="254c6-111">You can specify the module to publish either by the module's name, or by the path to the folder containing the module.</span></span>

<span data-ttu-id="254c6-112">當您依名稱指定模組時， `Publish-Module` 會發佈可透過執行所找到的第一個模組 `Get-Module -ListAvailable <Name>` 。</span><span class="sxs-lookup"><span data-stu-id="254c6-112">When you specify a module by name, `Publish-Module` publishes the first module that would be found by running `Get-Module -ListAvailable <Name>`.</span></span> <span data-ttu-id="254c6-113">如果您指定要發佈之模組的最低版本，則 `Publish-Module` 會發行第一個版本大於或等於您所指定之最小版本的模組。</span><span class="sxs-lookup"><span data-stu-id="254c6-113">If you specify a minimum version of a module to publish, `Publish-Module` publishes the first module with a version that is greater than or equal to the minimum version that you have specified.</span></span>

<span data-ttu-id="254c6-114">發行模組時需要在模組之資源庫頁面上所顯示的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="254c6-114">Publishing a module requires metadata that is displayed on the gallery page for the module.</span></span> <span data-ttu-id="254c6-115">必要的中繼資料包含模組名稱、版本、描述和作者。</span><span class="sxs-lookup"><span data-stu-id="254c6-115">Required metadata includes the module name, version, description, and author.</span></span> <span data-ttu-id="254c6-116">雖然大部分的中繼資料都是取自模組資訊清單，但有些中繼資料必須在參數中指定 `Publish-Module` ，例如 **Tag** 、 **ReleaseNote** 、 **IconUri** 、 **ProjectUri** 和 **LicenseUri** ，因為這些參數符合以 NuGet 為基礎的資源庫中的欄位。</span><span class="sxs-lookup"><span data-stu-id="254c6-116">Although most metadata is taken from the module manifest, some metadata must be specified in `Publish-Module` parameters, such as **Tag** , **ReleaseNote** , **IconUri** , **ProjectUri** , and **LicenseUri** , because these parameters match fields in a NuGet-based gallery.</span></span>

## <span data-ttu-id="254c6-117">範例</span><span class="sxs-lookup"><span data-stu-id="254c6-117">EXAMPLES</span></span>

### <span data-ttu-id="254c6-118">範例1：發佈模組</span><span class="sxs-lookup"><span data-stu-id="254c6-118">Example 1: Publish a module</span></span>

<span data-ttu-id="254c6-119">在此範例中，MyDscModule 會使用 API 金鑰來指出模組擁有者的線上資源庫帳戶，以發佈至線上元件庫。</span><span class="sxs-lookup"><span data-stu-id="254c6-119">In this example, MyDscModule is published to the online gallery by using the API key to indicate the module owner's online gallery account.</span></span> <span data-ttu-id="254c6-120">如果 MyDscModule 不是指定名稱、版本、描述和作者的有效資訊清單模組，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="254c6-120">If MyDscModule is not a valid manifest module that specifies a name, version, description, and author, an error occurs.</span></span>

```powershell
Publish-Module -Name "MyDscModule" -NuGetApiKey "11e4b435-6cb4-4bf7-8611-5162ed75eb73"
```

### <span data-ttu-id="254c6-121">範例2：使用資源庫中繼資料發佈模組</span><span class="sxs-lookup"><span data-stu-id="254c6-121">Example 2: Publish a module with gallery metadata</span></span>

<span data-ttu-id="254c6-122">在此範例中，MyDscModule 會使用 API 金鑰來指出模組擁有者的資源庫帳戶，以發佈至線上元件庫。</span><span class="sxs-lookup"><span data-stu-id="254c6-122">In this example, MyDscModule is published to the online gallery by using the API key to indicate the module owner's gallery account.</span></span> <span data-ttu-id="254c6-123">提供的額外中繼資料會顯示在資源庫中模組的網頁上。</span><span class="sxs-lookup"><span data-stu-id="254c6-123">The additional metadata provided is displayed on the webpage for the module in the gallery.</span></span> <span data-ttu-id="254c6-124">擁有者會新增模組的兩個搜尋標記，並將其與 Active Directory 相關聯;新增簡短的發行附注。</span><span class="sxs-lookup"><span data-stu-id="254c6-124">The owner adds two search tags for the module, relating it to Active Directory; a brief release note is added.</span></span> <span data-ttu-id="254c6-125">如果 MyDscModule 不是指定名稱、版本、描述和作者的有效資訊清單模組，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="254c6-125">If MyDscModule is not a valid manifest module that specifies a name, version, description, and author, an error occurs.</span></span>

```powershell
Publish-Module -Name "MyDscModule" -NuGetApiKey "11e4b435-6cb4-4bf7-8611-5162ed75eb73" -LicenseUri "http://contoso.com/license" -Tag "Active Directory","DSC" -ReleaseNote "Updated the ActiveDirectory DSC Resources to support adding users."
```

## <span data-ttu-id="254c6-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="254c6-126">PARAMETERS</span></span>

### <span data-ttu-id="254c6-127">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="254c6-127">-AllowPrerelease</span></span>

<span data-ttu-id="254c6-128">允許標示為發行前版本的模組發佈。</span><span class="sxs-lookup"><span data-stu-id="254c6-128">Allows modules marked as prerelease to be published.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="254c6-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="254c6-129">-Confirm</span></span>

<span data-ttu-id="254c6-130">在執行之前提示您確認 `Publish-Module` 。</span><span class="sxs-lookup"><span data-stu-id="254c6-130">Prompts you for confirmation before running the `Publish-Module`.</span></span>

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

### <span data-ttu-id="254c6-131">-Credential</span><span class="sxs-lookup"><span data-stu-id="254c6-131">-Credential</span></span>

<span data-ttu-id="254c6-132">指定有許可權可針對指定的套件提供者或來源發佈模組的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="254c6-132">Specifies a user account that has rights to publish a module for a specified package provider or source.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="254c6-133">-Exclude</span><span class="sxs-lookup"><span data-stu-id="254c6-133">-Exclude</span></span>

<span data-ttu-id="254c6-134">定義要從已發行的模組中排除的檔案。</span><span class="sxs-lookup"><span data-stu-id="254c6-134">Defines files to exclude from the published module.</span></span> <span data-ttu-id="254c6-135">在 **PowershellGet** 版本2.0.0 中，會新增 **Exclude** 參數支援。</span><span class="sxs-lookup"><span data-stu-id="254c6-135">**Exclude** parameter support is add in **PowershellGet** version 2.0.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="254c6-136">-Force</span><span class="sxs-lookup"><span data-stu-id="254c6-136">-Force</span></span>

<span data-ttu-id="254c6-137">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="254c6-137">Forces the command to run without asking for user confirmation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="254c6-138">-FormatVersion</span><span class="sxs-lookup"><span data-stu-id="254c6-138">-FormatVersion</span></span>

<span data-ttu-id="254c6-139">只接受 **ValidateSet** 屬性所指定的有效值。</span><span class="sxs-lookup"><span data-stu-id="254c6-139">Accepts only valid values specified by the **ValidateSet** attribute.</span></span>

<span data-ttu-id="254c6-140">如需詳細資訊，請參閱 [ValidateSet 屬性聲明](/powershell/scripting/developer/cmdlet/validateset-attribute-declaration) 和 [ValidateSetAttribute](/dotnet/api/system.management.automation.validatesetattribute)。</span><span class="sxs-lookup"><span data-stu-id="254c6-140">For more information, see [ValidateSet Attribute Declaration](/powershell/scripting/developer/cmdlet/validateset-attribute-declaration) and [ValidateSetAttribute](/dotnet/api/system.management.automation.validatesetattribute).</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:
Accepted values: 2.0

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="254c6-141">-IconUri</span><span class="sxs-lookup"><span data-stu-id="254c6-141">-IconUri</span></span>

<span data-ttu-id="254c6-142">指定模組的圖示 URL。</span><span class="sxs-lookup"><span data-stu-id="254c6-142">Specifies the URL of an icon for the module.</span></span> <span data-ttu-id="254c6-143">指定的圖示會顯示在模組的資源庫網頁上。</span><span class="sxs-lookup"><span data-stu-id="254c6-143">The specified icon is displayed on the gallery webpage for the module.</span></span>

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

### <span data-ttu-id="254c6-144">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="254c6-144">-LicenseUri</span></span>

<span data-ttu-id="254c6-145">指定您要發行之模組的授權條款 URL。</span><span class="sxs-lookup"><span data-stu-id="254c6-145">Specifies the URL of licensing terms for the module you want to publish.</span></span>

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

### <span data-ttu-id="254c6-146">-Name</span><span class="sxs-lookup"><span data-stu-id="254c6-146">-Name</span></span>

<span data-ttu-id="254c6-147">指定您要發行之模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="254c6-147">Specifies the name of the module that you want to publish.</span></span> <span data-ttu-id="254c6-148">`Publish-Module` 在中搜尋指定的模組名稱 `$Env:PSModulePath` 。</span><span class="sxs-lookup"><span data-stu-id="254c6-148">`Publish-Module` searches for the specified module name in `$Env:PSModulePath`.</span></span>

```yaml
Type: System.String
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="254c6-149">-NuGetApiKey</span><span class="sxs-lookup"><span data-stu-id="254c6-149">-NuGetApiKey</span></span>

<span data-ttu-id="254c6-150">指定您想要用來將模組發行至線上元件庫的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="254c6-150">Specifies the API key that you want to use to publish a module to the online gallery.</span></span> <span data-ttu-id="254c6-151">API 金鑰是線上元件庫中設定檔的一部分，而且可以在資源庫中的 [使用者帳戶] 頁面上找到。</span><span class="sxs-lookup"><span data-stu-id="254c6-151">The API key is part of your profile in the online gallery, and can be found on your user account page in the gallery.</span></span> <span data-ttu-id="254c6-152">API 金鑰是 NuGet 特有的功能。</span><span class="sxs-lookup"><span data-stu-id="254c6-152">The API key is NuGet-specific functionality.</span></span>

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

### <span data-ttu-id="254c6-153">-Path</span><span class="sxs-lookup"><span data-stu-id="254c6-153">-Path</span></span>

<span data-ttu-id="254c6-154">指定您要發行之模組的路徑。</span><span class="sxs-lookup"><span data-stu-id="254c6-154">Specifies the path to the module that you want to publish.</span></span> <span data-ttu-id="254c6-155">此參數會接受包含模組之資料夾的路徑。</span><span class="sxs-lookup"><span data-stu-id="254c6-155">This parameter accepts the path to the folder that contains the module.</span></span>

```yaml
Type: System.String
Parameter Sets: ModulePathParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="254c6-156">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="254c6-156">-ProjectUri</span></span>

<span data-ttu-id="254c6-157">指定此專案之網頁的 URL。</span><span class="sxs-lookup"><span data-stu-id="254c6-157">Specifies the URL of a webpage about this project.</span></span>

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

### <span data-ttu-id="254c6-158">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="254c6-158">-ReleaseNotes</span></span>

<span data-ttu-id="254c6-159">指定字串，其中包含您想要提供給此模組版本之使用者使用的版本資訊或批註。</span><span class="sxs-lookup"><span data-stu-id="254c6-159">Specifies a string containing release notes or comments that you want to be available to users of this version of the module.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="254c6-160">-Repository</span><span class="sxs-lookup"><span data-stu-id="254c6-160">-Repository</span></span>

<span data-ttu-id="254c6-161">指定由執行註冊之存放庫的易記名稱 `Register-PSRepository` 。</span><span class="sxs-lookup"><span data-stu-id="254c6-161">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span> <span data-ttu-id="254c6-162">存放庫必須具有 **PublishLocation** ，這是有效的 NuGet URI。</span><span class="sxs-lookup"><span data-stu-id="254c6-162">The repository must have a **PublishLocation** , which is a valid NuGet URI.</span></span>
<span data-ttu-id="254c6-163">您可以藉由執行來設定 **PublishLocation** `Set-PSRepository` 。</span><span class="sxs-lookup"><span data-stu-id="254c6-163">The **PublishLocation** can be set by running `Set-PSRepository`.</span></span>

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

### <span data-ttu-id="254c6-164">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="254c6-164">-RequiredVersion</span></span>

<span data-ttu-id="254c6-165">指定要發行之單一模組的確切版本。</span><span class="sxs-lookup"><span data-stu-id="254c6-165">Specifies the exact version of a single module to publish.</span></span>

```yaml
Type: System.String
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="254c6-166">-SkipAutomaticTags</span><span class="sxs-lookup"><span data-stu-id="254c6-166">-SkipAutomaticTags</span></span>

<span data-ttu-id="254c6-167">移除包含為標記的命令和資源。</span><span class="sxs-lookup"><span data-stu-id="254c6-167">Removes commands and resources from being included as tags.</span></span> <span data-ttu-id="254c6-168">略過自動將標記新增至模組。</span><span class="sxs-lookup"><span data-stu-id="254c6-168">Skips automatically adding tags to a module.</span></span> <span data-ttu-id="254c6-169">**PowerShellGet** 版本2.0.0 中新增了 **SkipAutomaticTags** 參數支援</span><span class="sxs-lookup"><span data-stu-id="254c6-169">**SkipAutomaticTags** parameter support is added in **PowerShellGet** version 2.0.0</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="254c6-170">-Tags</span><span class="sxs-lookup"><span data-stu-id="254c6-170">-Tags</span></span>

<span data-ttu-id="254c6-171">將一或多個標記新增至您要發佈的模組。</span><span class="sxs-lookup"><span data-stu-id="254c6-171">Adds one or more tags to the module that you are publishing.</span></span> <span data-ttu-id="254c6-172">範例標記包括 DesiredStateConfiguration、DSC、DSCResourceKit 或 PSModule。</span><span class="sxs-lookup"><span data-stu-id="254c6-172">Example tags include DesiredStateConfiguration, DSC, DSCResourceKit, or PSModule.</span></span> <span data-ttu-id="254c6-173">以逗號分隔多個標記。</span><span class="sxs-lookup"><span data-stu-id="254c6-173">Separate multiple tags with commas.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="254c6-174">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="254c6-174">-WhatIf</span></span>

<span data-ttu-id="254c6-175">顯示執行時所發生的情況 `Publish-Module` 。</span><span class="sxs-lookup"><span data-stu-id="254c6-175">Shows what would happen if the `Publish-Module` runs.</span></span> <span data-ttu-id="254c6-176">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="254c6-176">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="254c6-177">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="254c6-177">CommonParameters</span></span>

<span data-ttu-id="254c6-178">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="254c6-178">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="254c6-179">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="254c6-179">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="254c6-180">輸入</span><span class="sxs-lookup"><span data-stu-id="254c6-180">INPUTS</span></span>

### <span data-ttu-id="254c6-181">System.String</span><span class="sxs-lookup"><span data-stu-id="254c6-181">System.String</span></span>

### <span data-ttu-id="254c6-182">System.Management.Automation.PSCredential</span><span class="sxs-lookup"><span data-stu-id="254c6-182">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="254c6-183">輸出</span><span class="sxs-lookup"><span data-stu-id="254c6-183">OUTPUTS</span></span>

### <span data-ttu-id="254c6-184">System.Object</span><span class="sxs-lookup"><span data-stu-id="254c6-184">System.Object</span></span>

## <span data-ttu-id="254c6-185">注意</span><span class="sxs-lookup"><span data-stu-id="254c6-185">NOTES</span></span>

<span data-ttu-id="254c6-186">`Publish-Module` 在 Windows 7 或 Windows 2008 R2 和更新版本的 Windows 上，于 powershell 3.0 或更新版本的 PowerShell 上執行。</span><span class="sxs-lookup"><span data-stu-id="254c6-186">`Publish-Module` runs on PowerShell 3.0 or later releases of PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

<span data-ttu-id="254c6-187">發行模組時需要在模組之資源庫頁面上所顯示的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="254c6-187">Publishing a module requires metadata that is displayed on the gallery page for the module.</span></span> <span data-ttu-id="254c6-188">必要的中繼資料包含模組名稱、版本、描述和作者。</span><span class="sxs-lookup"><span data-stu-id="254c6-188">Required metadata includes the module name, version, description, and author.</span></span> <span data-ttu-id="254c6-189">大部分的中繼資料都是取自模組資訊清單，但有些中繼資料可以在參數中指定 `Publish-Module` ，例如 **Tag** 、 **ReleaseNote** 、 **IconUri** 、 **ProjectUri** 和 **LicenseUri** 。</span><span class="sxs-lookup"><span data-stu-id="254c6-189">Most metadata is taken from the module manifest, but some metadata can be specified in `Publish-Module` parameters, such as **Tag** , **ReleaseNote** , **IconUri** , **ProjectUri** , and **LicenseUri** .</span></span> <span data-ttu-id="254c6-190">如需詳細資訊，請參閱 [影響 POWERSHELL 資源庫 UI 的套件資訊清單值](/powershell/scripting/gallery/concepts/package-manifest-affecting-ui)。</span><span class="sxs-lookup"><span data-stu-id="254c6-190">For more information, see [Package manifest values that impact the PowerShell Gallery UI](/powershell/scripting/gallery/concepts/package-manifest-affecting-ui).</span></span>

## <span data-ttu-id="254c6-191">相關連結</span><span class="sxs-lookup"><span data-stu-id="254c6-191">RELATED LINKS</span></span>

[<span data-ttu-id="254c6-192">Find-Module</span><span class="sxs-lookup"><span data-stu-id="254c6-192">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="254c6-193">Install-Module</span><span class="sxs-lookup"><span data-stu-id="254c6-193">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="254c6-194">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="254c6-194">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="254c6-195">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="254c6-195">Set-PSRepository</span></span>](Set-PSRepository.md)

[<span data-ttu-id="254c6-196">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="254c6-196">Uninstall-Module</span></span>](Uninstall-Module.md)

[<span data-ttu-id="254c6-197">Update-Module</span><span class="sxs-lookup"><span data-stu-id="254c6-197">Update-Module</span></span>](Update-Module.md)
