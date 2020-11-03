---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/08/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-modulemanifest?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-ModuleManifest
ms.openlocfilehash: f4eb5989f98517e70cc684457f0d0e3f0d12c1d4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204540"
---
# <span data-ttu-id="12279-103">Update-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="12279-103">Update-ModuleManifest</span></span>

## <span data-ttu-id="12279-104">概要</span><span class="sxs-lookup"><span data-stu-id="12279-104">SYNOPSIS</span></span>
<span data-ttu-id="12279-105">更新模組資訊清單檔案。</span><span class="sxs-lookup"><span data-stu-id="12279-105">Updates a module manifest file.</span></span>

## <span data-ttu-id="12279-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="12279-106">SYNTAX</span></span>

### <span data-ttu-id="12279-107">全部</span><span class="sxs-lookup"><span data-stu-id="12279-107">All</span></span>

```
Update-ModuleManifest [-Path] <String> [-NestedModules <Object[]>] [-Guid <Guid>] [-Author <String>]
 [-CompanyName <String>] [-Copyright <String>] [-RootModule <String>] [-ModuleVersion <Version>]
 [-Description <String>] [-ProcessorArchitecture <ProcessorArchitecture>]
 [-CompatiblePSEditions <String[]>] [-PowerShellVersion <Version>] [-ClrVersion <Version>]
 [-DotNetFrameworkVersion <Version>] [-PowerShellHostName <String>]
 [-PowerShellHostVersion <Version>] [-RequiredModules <Object[]>] [-TypesToProcess <String[]>]
 [-FormatsToProcess <String[]>] [-ScriptsToProcess <String[]>] [-RequiredAssemblies <String[]>]
 [-FileList <String[]>] [-ModuleList <Object[]>] [-FunctionsToExport <String[]>]
 [-AliasesToExport <String[]>] [-VariablesToExport <String[]>] [-CmdletsToExport <String[]>]
 [-DscResourcesToExport <String[]>] [-PrivateData <Hashtable>] [-Tags <String[]>]
 [-ProjectUri <Uri>] [-LicenseUri <Uri>] [-IconUri <Uri>] [-ReleaseNotes <String[]>]
 [-Prerelease <String>] [-HelpInfoUri <Uri>] [-PassThru] [-DefaultCommandPrefix <String>]
 [-ExternalModuleDependencies <String[]>] [-PackageManagementProviders <String[]>]
 [-RequireLicenseAcceptance] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="12279-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="12279-108">DESCRIPTION</span></span>

<span data-ttu-id="12279-109">`Update-ModuleManifest`指令程式會更新) 檔 (的模組資訊清單 `.psd1` 。</span><span class="sxs-lookup"><span data-stu-id="12279-109">The `Update-ModuleManifest` cmdlet updates a module manifest (`.psd1`) file.</span></span>

## <span data-ttu-id="12279-110">範例</span><span class="sxs-lookup"><span data-stu-id="12279-110">EXAMPLES</span></span>

### <span data-ttu-id="12279-111">範例1：更新模組資訊清單</span><span class="sxs-lookup"><span data-stu-id="12279-111">Example 1: Update a module manifest</span></span>

<span data-ttu-id="12279-112">此範例會更新現有的模組資訊清單檔案。</span><span class="sxs-lookup"><span data-stu-id="12279-112">This example updates an existing module manifest file.</span></span> <span data-ttu-id="12279-113">展開用來將參數值傳遞給 `Update-ModuleManifest` 。</span><span class="sxs-lookup"><span data-stu-id="12279-113">Splatting is used to pass parameter values to `Update-ModuleManifest`.</span></span> <span data-ttu-id="12279-114">如需詳細資訊，請參閱 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)。</span><span class="sxs-lookup"><span data-stu-id="12279-114">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

```powershell
$Parms = @{
  Path = "C:\Test\TestManifest.psd1"
  Author = "TestUser1"
  CompanyName = "Contoso Corporation"
  Copyright = "(c) 2019 Contoso Corporation. All rights reserved."
}

Update-ModuleManifest @Parms
```

<span data-ttu-id="12279-115">`$Parms` 是儲存 **路徑** 、 **作者** 、 **公司名稱** 和 **著作權** 之參數值的 splat。</span><span class="sxs-lookup"><span data-stu-id="12279-115">`$Parms` is a splat that stores the parameter values for **Path** , **Author** , **CompanyName** , and **Copyright** .</span></span> <span data-ttu-id="12279-116">`Update-ModuleManifest` 從取得參數值 `@Parms` ，並更新 **TestManifest.psd1** 的模組資訊清單。</span><span class="sxs-lookup"><span data-stu-id="12279-116">`Update-ModuleManifest` gets the parameter values from `@Parms` and updates the module manifest, **TestManifest.psd1** .</span></span>

## <span data-ttu-id="12279-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="12279-117">PARAMETERS</span></span>

### <span data-ttu-id="12279-118">-AliasesToExport</span><span class="sxs-lookup"><span data-stu-id="12279-118">-AliasesToExport</span></span>

<span data-ttu-id="12279-119">指定模組匯出的別名。</span><span class="sxs-lookup"><span data-stu-id="12279-119">Specifies the aliases that the module exports.</span></span> <span data-ttu-id="12279-120">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="12279-120">Wildcards are permitted.</span></span>

<span data-ttu-id="12279-121">使用此參數來限制模組匯出的別名。</span><span class="sxs-lookup"><span data-stu-id="12279-121">Use this parameter to restrict the aliases that are exported by the module.</span></span> <span data-ttu-id="12279-122">**AliasesToExport** 可以從匯出的別名清單中移除別名，但不能將別名新增至清單。</span><span class="sxs-lookup"><span data-stu-id="12279-122">**AliasesToExport** can remove aliases from the list of exported aliases, but it can't add aliases to the list.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="12279-123">-作者</span><span class="sxs-lookup"><span data-stu-id="12279-123">-Author</span></span>

<span data-ttu-id="12279-124">指定模組作者。</span><span class="sxs-lookup"><span data-stu-id="12279-124">Specifies the module author.</span></span>

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

### <span data-ttu-id="12279-125">-ClrVersion</span><span class="sxs-lookup"><span data-stu-id="12279-125">-ClrVersion</span></span>

<span data-ttu-id="12279-126">指定模組所需要的 Microsoft .NET Framework Common Language Runtime (CLR) 最低版本。</span><span class="sxs-lookup"><span data-stu-id="12279-126">Specifies the minimum version of the Common Language Runtime (CLR) of the Microsoft .NET Framework that the module requires.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12279-127">-CmdletsToExport</span><span class="sxs-lookup"><span data-stu-id="12279-127">-CmdletsToExport</span></span>

<span data-ttu-id="12279-128">指定模組匯出的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="12279-128">Specifies the cmdlets that the module exports.</span></span> <span data-ttu-id="12279-129">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="12279-129">Wildcards are permitted.</span></span>

<span data-ttu-id="12279-130">使用此參數來限制模組匯出的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="12279-130">Use this parameter to restrict the cmdlets that are exported by the module.</span></span> <span data-ttu-id="12279-131">**CmdletsToExport** 可以從匯出的 Cmdlet 清單中移除 Cmdlet，但是無法將 Cmdlet 新增至清單。</span><span class="sxs-lookup"><span data-stu-id="12279-131">**CmdletsToExport** can remove cmdlets from the list of exported cmdlets, but it can't add cmdlets to the list.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="12279-132">-公司名稱</span><span class="sxs-lookup"><span data-stu-id="12279-132">-CompanyName</span></span>

<span data-ttu-id="12279-133">指定建立模組的公司或廠商。</span><span class="sxs-lookup"><span data-stu-id="12279-133">Specifies the company or vendor who created the module.</span></span>

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

### <span data-ttu-id="12279-134">-CompatiblePSEditions</span><span class="sxs-lookup"><span data-stu-id="12279-134">-CompatiblePSEditions</span></span>

<span data-ttu-id="12279-135">指定模組的相容 **PSEditions** 。</span><span class="sxs-lookup"><span data-stu-id="12279-135">Specifies the compatible **PSEditions** of the module.</span></span> <span data-ttu-id="12279-136">如需 **PSEdition** 的相關資訊，請參閱 [具有相容 PowerShell 版本的模組](/powershell/scripting/gallery/concepts/module-psedition-support)。</span><span class="sxs-lookup"><span data-stu-id="12279-136">For information about **PSEdition** , see [Modules with compatible PowerShell Editions](/powershell/scripting/gallery/concepts/module-psedition-support).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Desktop, Core

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12279-137">-Confirm</span><span class="sxs-lookup"><span data-stu-id="12279-137">-Confirm</span></span>

<span data-ttu-id="12279-138">在執行之前提示您確認 `Update-ModuleManifest` 。</span><span class="sxs-lookup"><span data-stu-id="12279-138">Prompts you for confirmation before running `Update-ModuleManifest`.</span></span>

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

### <span data-ttu-id="12279-139">-著作權</span><span class="sxs-lookup"><span data-stu-id="12279-139">-Copyright</span></span>

<span data-ttu-id="12279-140">指定模組的著作權聲明。</span><span class="sxs-lookup"><span data-stu-id="12279-140">Specifies a copyright statement for the module.</span></span>

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

### <span data-ttu-id="12279-141">-DefaultCommandPrefix</span><span class="sxs-lookup"><span data-stu-id="12279-141">-DefaultCommandPrefix</span></span>

<span data-ttu-id="12279-142">指定預設的命令前置詞。</span><span class="sxs-lookup"><span data-stu-id="12279-142">Specifies the default command prefix.</span></span>

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

### <span data-ttu-id="12279-143">-Description</span><span class="sxs-lookup"><span data-stu-id="12279-143">-Description</span></span>

<span data-ttu-id="12279-144">指定模組的描述。</span><span class="sxs-lookup"><span data-stu-id="12279-144">Specifies a description of the module.</span></span>

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

### <span data-ttu-id="12279-145">-DotNetFrameworkVersion</span><span class="sxs-lookup"><span data-stu-id="12279-145">-DotNetFrameworkVersion</span></span>

<span data-ttu-id="12279-146">指定模組所需要的 Microsoft .NET Framework 最低版本。</span><span class="sxs-lookup"><span data-stu-id="12279-146">Specifies the minimum version of the Microsoft .NET Framework that the module requires.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12279-147">-DscResourcesToExport</span><span class="sxs-lookup"><span data-stu-id="12279-147">-DscResourcesToExport</span></span>

<span data-ttu-id="12279-148">指定模組匯出的 Desired State Configuration (DSC) 資源。</span><span class="sxs-lookup"><span data-stu-id="12279-148">Specifies the Desired State Configuration (DSC) resources that the module exports.</span></span> <span data-ttu-id="12279-149">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="12279-149">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="12279-150">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="12279-150">-ExternalModuleDependencies</span></span>

<span data-ttu-id="12279-151">指定外部模組相依性的陣列。</span><span class="sxs-lookup"><span data-stu-id="12279-151">Specifies an array of external module dependencies.</span></span>

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

### <span data-ttu-id="12279-152">-FileList</span><span class="sxs-lookup"><span data-stu-id="12279-152">-FileList</span></span>

<span data-ttu-id="12279-153">指定模組中所包含的所有項目。</span><span class="sxs-lookup"><span data-stu-id="12279-153">Specifies all items that are included in the module.</span></span>

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

### <span data-ttu-id="12279-154">-FormatsToProcess</span><span class="sxs-lookup"><span data-stu-id="12279-154">-FormatsToProcess</span></span>

<span data-ttu-id="12279-155">指定匯 `.ps1xml` 入模組時所執行)  (格式檔案。</span><span class="sxs-lookup"><span data-stu-id="12279-155">Specifies the formatting files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="12279-156">當您匯入模組時，PowerShell 會 `Update-FormatData` 使用指定的檔案來執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="12279-156">When you import a module, PowerShell runs the `Update-FormatData` cmdlet with the specified files.</span></span>
<span data-ttu-id="12279-157">因為格式化檔案未設定範圍，所以它們會影響會話中所有的會話狀態。</span><span class="sxs-lookup"><span data-stu-id="12279-157">Because formatting files aren't scoped, they affect all session states in the session.</span></span>

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

### <span data-ttu-id="12279-158">-FunctionsToExport</span><span class="sxs-lookup"><span data-stu-id="12279-158">-FunctionsToExport</span></span>

<span data-ttu-id="12279-159">指定模組匯出的函式。</span><span class="sxs-lookup"><span data-stu-id="12279-159">Specifies the functions that the module exports.</span></span> <span data-ttu-id="12279-160">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="12279-160">Wildcards are permitted.</span></span>

<span data-ttu-id="12279-161">使用此參數來限制模組匯出的函式。</span><span class="sxs-lookup"><span data-stu-id="12279-161">Use this parameter to restrict the functions that are exported by the module.</span></span> <span data-ttu-id="12279-162">**FunctionsToExport** 可以從匯出的別名清單中移除函式，但無法將函數新增至清單。</span><span class="sxs-lookup"><span data-stu-id="12279-162">**FunctionsToExport** can remove functions from the list of exported aliases, but it can't add functions to the list.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="12279-163">-Guid</span><span class="sxs-lookup"><span data-stu-id="12279-163">-Guid</span></span>

<span data-ttu-id="12279-164">指定模組的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="12279-164">Specifies a unique identifier for the module.</span></span> <span data-ttu-id="12279-165">GUID 可用來區別具有相同名稱的模組。</span><span class="sxs-lookup"><span data-stu-id="12279-165">The GUID can be used to distinguish among modules with the same name.</span></span>

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12279-166">-HelpInfoUri</span><span class="sxs-lookup"><span data-stu-id="12279-166">-HelpInfoUri</span></span>

<span data-ttu-id="12279-167">指定模組 **HELPINFO XML** 檔案的網際網路位址。</span><span class="sxs-lookup"><span data-stu-id="12279-167">Specifies the internet address of the module's **HelpInfo XML** file.</span></span> <span data-ttu-id="12279-168">輸入以 **HTTP** 或 **HTTPS** 開頭 (URI) 的統一資源識別項。</span><span class="sxs-lookup"><span data-stu-id="12279-168">Enter a Uniform Resource Identifier (URI) that begins with **http** or **https** .</span></span>

<span data-ttu-id="12279-169">**HELPINFO XML** 檔案支援 PowerShell 3.0 版中引進的可更新說明功能。</span><span class="sxs-lookup"><span data-stu-id="12279-169">The **HelpInfo XML** file supports the Updatable Help feature that was introduced in PowerShell version 3.0.</span></span> <span data-ttu-id="12279-170">它包含模組可下載說明檔案位置的相關資訊，以及每個支援的地區設定最新說明檔案的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="12279-170">It contains information about the location of the module's downloadable help files and the version numbers of the newest help files for each supported locale.</span></span>

<span data-ttu-id="12279-171">如需「可更新的說明」的詳細資訊，請參閱 [about_Updatable_Help](../Microsoft.PowerShell.Core/About/about_Updatable_Help.md)。</span><span class="sxs-lookup"><span data-stu-id="12279-171">For information about Updatable Help, see [about_Updatable_Help](../Microsoft.PowerShell.Core/About/about_Updatable_Help.md).</span></span>
<span data-ttu-id="12279-172">如需 **HELPINFO XML** 檔案的相關資訊，請參閱 [支援可更新](/powershell/scripting/developer/module/supporting-updatable-help)的說明。</span><span class="sxs-lookup"><span data-stu-id="12279-172">For information about the **HelpInfo XML** file, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

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

### <span data-ttu-id="12279-173">-IconUri</span><span class="sxs-lookup"><span data-stu-id="12279-173">-IconUri</span></span>

<span data-ttu-id="12279-174">指定模組的圖示 URL。</span><span class="sxs-lookup"><span data-stu-id="12279-174">Specifies the URL of an icon for the module.</span></span> <span data-ttu-id="12279-175">指定的圖示會顯示在該模組的資源庫網頁上。</span><span class="sxs-lookup"><span data-stu-id="12279-175">The specified icon is displayed on the gallery web page for the module.</span></span>

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

### <span data-ttu-id="12279-176">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="12279-176">-LicenseUri</span></span>

<span data-ttu-id="12279-177">指定模組的授權條款 URL。</span><span class="sxs-lookup"><span data-stu-id="12279-177">Specifies the URL of licensing terms for the module.</span></span>

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

### <span data-ttu-id="12279-178">-ModuleList</span><span class="sxs-lookup"><span data-stu-id="12279-178">-ModuleList</span></span>

<span data-ttu-id="12279-179">指定模組中包含的模組陣列。</span><span class="sxs-lookup"><span data-stu-id="12279-179">Specifies an array of modules that are included in the module.</span></span>

<span data-ttu-id="12279-180">輸入每個模組名稱做為字串或含 **ModuleName** 和 **ModuleVersion** 索引鍵的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="12279-180">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="12279-181">雜湊表也可以有選用的 **GUID** 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="12279-181">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="12279-182">您可以在參數值中結合字串和雜湊表。</span><span class="sxs-lookup"><span data-stu-id="12279-182">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="12279-183">這個索引鍵被設計來做為模組詳細目錄。</span><span class="sxs-lookup"><span data-stu-id="12279-183">This key is designed to act as a module inventory.</span></span> <span data-ttu-id="12279-184">系統不會自動處理此索引鍵值中所列的模組。</span><span class="sxs-lookup"><span data-stu-id="12279-184">The modules that are listed in the value of this key aren't automatically processed.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12279-185">-ModuleVersion</span><span class="sxs-lookup"><span data-stu-id="12279-185">-ModuleVersion</span></span>

<span data-ttu-id="12279-186">指定模組的版本。</span><span class="sxs-lookup"><span data-stu-id="12279-186">Specifies the version of the module.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12279-187">-NestedModules</span><span class="sxs-lookup"><span data-stu-id="12279-187">-NestedModules</span></span>

<span data-ttu-id="12279-188">指定腳本模組 (`.psm1`) 和二進位模組， (`.dll`) 匯入模組的會話狀態。</span><span class="sxs-lookup"><span data-stu-id="12279-188">Specifies script modules (`.psm1`) and binary modules (`.dll`) that are imported into the module's session state.</span></span> <span data-ttu-id="12279-189">**NestedModules** 機碼中的檔案會依它們在值中的列出循序執行。</span><span class="sxs-lookup"><span data-stu-id="12279-189">The files in the **NestedModules** key run in the order in which they're listed in the value.</span></span>

<span data-ttu-id="12279-190">輸入每個模組名稱做為字串或含 **ModuleName** 和 **ModuleVersion** 索引鍵的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="12279-190">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="12279-191">雜湊表也可以有選用的 **GUID** 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="12279-191">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="12279-192">您可以在參數值中結合字串和雜湊表。</span><span class="sxs-lookup"><span data-stu-id="12279-192">You can combine strings and hash tables in the parameter value.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12279-193">-PackageManagementProviders</span><span class="sxs-lookup"><span data-stu-id="12279-193">-PackageManagementProviders</span></span>

<span data-ttu-id="12279-194">指定封裝管理提供者的陣列。</span><span class="sxs-lookup"><span data-stu-id="12279-194">Specifies an array of package management providers.</span></span>

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

### <span data-ttu-id="12279-195">-PassThru</span><span class="sxs-lookup"><span data-stu-id="12279-195">-PassThru</span></span>

<span data-ttu-id="12279-196">傳回代表您正在使用之專案的物件。</span><span class="sxs-lookup"><span data-stu-id="12279-196">Returns an object representing the item with which you're working.</span></span> <span data-ttu-id="12279-197">依預設， `Update-ModuleManifest` 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="12279-197">By default, `Update-ModuleManifest` doesn't generate any output.</span></span>

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

### <span data-ttu-id="12279-198">-Path</span><span class="sxs-lookup"><span data-stu-id="12279-198">-Path</span></span>

<span data-ttu-id="12279-199">指定模組資訊清單的路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="12279-199">Specifies the path and file name of the module manifest.</span></span> <span data-ttu-id="12279-200">輸入副檔名為的路徑和檔案名 `.psd1` ，例如 `$PSHOME\Modules\MyModule\MyModule.psd1` 。</span><span class="sxs-lookup"><span data-stu-id="12279-200">Enter a path and file name with a `.psd1` file name extension, such as `$PSHOME\Modules\MyModule\MyModule.psd1`.</span></span>

<span data-ttu-id="12279-201">如果您指定現有檔案的路徑，則 `Update-ModuleManifest` 會在沒有警告的情況下取代檔案，除非檔案具有唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="12279-201">If you specify the path to an existing file, `Update-ModuleManifest` replaces the file without warning unless the file has the read-only attribute.</span></span>

<span data-ttu-id="12279-202">資訊清單應該位於模組的目錄中，且資訊清單檔案名應該與模組目錄名稱相同，但是 `.psd1` 副檔名為。</span><span class="sxs-lookup"><span data-stu-id="12279-202">The manifest should be located in the module's directory, and the manifest file name should be the same as the module directory name, but with a `.psd1` extension.</span></span>

<span data-ttu-id="12279-203">您無法使用變數（例如 `$PSHOME` 或 `$HOME` ）來回應 **路徑** 參數值的提示。</span><span class="sxs-lookup"><span data-stu-id="12279-203">You can't use variables, such as `$PSHOME` or `$HOME`, in response to a prompt for a **Path** parameter value.</span></span> <span data-ttu-id="12279-204">如果要使用變數，請在命令中包含 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="12279-204">To use a variable, include the **Path** parameter in the command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="12279-205">-PowerShellHostName</span><span class="sxs-lookup"><span data-stu-id="12279-205">-PowerShellHostName</span></span>

<span data-ttu-id="12279-206">指定模組所需之 PowerShell 主機程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="12279-206">Specifies the name of the PowerShell host program that the module requires.</span></span> <span data-ttu-id="12279-207">輸入主機程式的名稱，例如 PowerShell ISE 主機或 ConsoleHost。</span><span class="sxs-lookup"><span data-stu-id="12279-207">Enter the name of the host program, such as PowerShell ISE Host or ConsoleHost.</span></span> <span data-ttu-id="12279-208">不允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="12279-208">Wildcards aren't permitted.</span></span>

<span data-ttu-id="12279-209">若要尋找主機程式的名稱，請在程式中輸入 `$Host.Name` 。</span><span class="sxs-lookup"><span data-stu-id="12279-209">To find the name of a host program, in the program, type `$Host.Name`.</span></span>

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

### <span data-ttu-id="12279-210">-PowerShellHostVersion</span><span class="sxs-lookup"><span data-stu-id="12279-210">-PowerShellHostVersion</span></span>

<span data-ttu-id="12279-211">指定適用于模組的 PowerShell 主機程式的最小版本。</span><span class="sxs-lookup"><span data-stu-id="12279-211">Specifies the minimum version of the PowerShell host program that works with the module.</span></span> <span data-ttu-id="12279-212">輸入版本號碼，例如 1.1。</span><span class="sxs-lookup"><span data-stu-id="12279-212">Enter a version number, such as 1.1.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12279-213">-PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="12279-213">-PowerShellVersion</span></span>

<span data-ttu-id="12279-214">指定可使用此模組的 PowerShell 最低版本。</span><span class="sxs-lookup"><span data-stu-id="12279-214">Specifies the minimum version of PowerShell that will work with this module.</span></span> <span data-ttu-id="12279-215">例如，您可以將3.0、4.0 或5.0 指定為此參數的值。</span><span class="sxs-lookup"><span data-stu-id="12279-215">For example, you can specify 3.0, 4.0, or 5.0 as the value of this parameter.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12279-216">-發行前版本</span><span class="sxs-lookup"><span data-stu-id="12279-216">-Prerelease</span></span>

<span data-ttu-id="12279-217">指出模組為發行前版本。</span><span class="sxs-lookup"><span data-stu-id="12279-217">Indicates the module is prerelease.</span></span>

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

### <span data-ttu-id="12279-218">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="12279-218">-PrivateData</span></span>

<span data-ttu-id="12279-219">指定匯入模組時傳遞給模組的資料。</span><span class="sxs-lookup"><span data-stu-id="12279-219">Specifies data that is passed to the module when it's imported.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12279-220">-ProcessorArchitecture</span><span class="sxs-lookup"><span data-stu-id="12279-220">-ProcessorArchitecture</span></span>

<span data-ttu-id="12279-221">指定模組需要的處理器架構。</span><span class="sxs-lookup"><span data-stu-id="12279-221">Specifies the processor architecture that the module requires.</span></span>

<span data-ttu-id="12279-222">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="12279-222">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="12279-223">Amd64</span><span class="sxs-lookup"><span data-stu-id="12279-223">Amd64</span></span>
- <span data-ttu-id="12279-224">Arm</span><span class="sxs-lookup"><span data-stu-id="12279-224">Arm</span></span>
- <span data-ttu-id="12279-225">IA64</span><span class="sxs-lookup"><span data-stu-id="12279-225">IA64</span></span>
- <span data-ttu-id="12279-226">MSIL</span><span class="sxs-lookup"><span data-stu-id="12279-226">MSIL</span></span>
- <span data-ttu-id="12279-227">無 (未知或未指定) </span><span class="sxs-lookup"><span data-stu-id="12279-227">None (unknown or unspecified)</span></span>
- <span data-ttu-id="12279-228">X86</span><span class="sxs-lookup"><span data-stu-id="12279-228">X86</span></span>

```yaml
Type: System.Reflection.ProcessorArchitecture
Parameter Sets: (All)
Aliases:
Accepted values: None, MSIL, X86, IA64, Amd64, Arm

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12279-229">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="12279-229">-ProjectUri</span></span>

<span data-ttu-id="12279-230">指定與這個專案相關之網頁的 URL。</span><span class="sxs-lookup"><span data-stu-id="12279-230">Specifies the URL of a web page about this project.</span></span>

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

### <span data-ttu-id="12279-231">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="12279-231">-ReleaseNotes</span></span>

<span data-ttu-id="12279-232">指定字串陣列，其中包含您想要用於此版本腳本的版本資訊或批註。</span><span class="sxs-lookup"><span data-stu-id="12279-232">Specifies a string array that contains release notes or comments that you want available for this version of the script.</span></span>

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

### <span data-ttu-id="12279-233">-RequiredAssemblies</span><span class="sxs-lookup"><span data-stu-id="12279-233">-RequiredAssemblies</span></span>

<span data-ttu-id="12279-234">指定模組所需 () 檔案的元件 `.dll` 。</span><span class="sxs-lookup"><span data-stu-id="12279-234">Specifies the assembly (`.dll`) files that the module requires.</span></span> <span data-ttu-id="12279-235">輸入組件檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="12279-235">Enter the assembly file names.</span></span>
<span data-ttu-id="12279-236">PowerShell 會在更新類型或格式、匯入嵌套模組，或匯入在 **RootModule** 索引鍵值中指定的模組檔案之前，先載入指定的元件。</span><span class="sxs-lookup"><span data-stu-id="12279-236">PowerShell loads the specified assemblies before updating types or formats, importing nested modules, or importing the module file that is specified in the value of the **RootModule** key.</span></span>

<span data-ttu-id="12279-237">使用這個參數來指定模組所需的所有元件，包括必須載入的元件，以更新 **FormatsToProcess** 或 **TypesToProcess** 索引鍵中列出的任何格式或類型檔案，即使這些元件也在 **NestedModules** 索引鍵中列為二進位模組。</span><span class="sxs-lookup"><span data-stu-id="12279-237">Use this parameter to specify all the assemblies that the module requires, including assemblies that must be loaded to update any formatting or type files that are listed in the **FormatsToProcess** or **TypesToProcess** keys, even if those assemblies are also listed as binary modules in the **NestedModules** key.</span></span>

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

### <span data-ttu-id="12279-238">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="12279-238">-RequiredModules</span></span>

<span data-ttu-id="12279-239">指定必須在全域工作階段狀態的模組。</span><span class="sxs-lookup"><span data-stu-id="12279-239">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="12279-240">如果必要的模組不在全域會話狀態中，則 PowerShell 會將它們匯入。</span><span class="sxs-lookup"><span data-stu-id="12279-240">If the required modules aren't in the global session state, PowerShell imports them.</span></span> <span data-ttu-id="12279-241">如果無法使用必要的模組，則 `Import-Module` 命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="12279-241">If the required modules aren't available, the `Import-Module` command fails.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12279-242">-RequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="12279-242">-RequireLicenseAcceptance</span></span>

<span data-ttu-id="12279-243">指定模組需要接受授權。</span><span class="sxs-lookup"><span data-stu-id="12279-243">Specifies that a license acceptance is required for the module.</span></span>

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

### <span data-ttu-id="12279-244">-RootModule</span><span class="sxs-lookup"><span data-stu-id="12279-244">-RootModule</span></span>

<span data-ttu-id="12279-245">指定模組的主要或根檔案。</span><span class="sxs-lookup"><span data-stu-id="12279-245">Specifies the primary or root file of the module.</span></span> <span data-ttu-id="12279-246">輸入腳本 (的檔案名 `.ps1`) 、腳本模組 (`.psm1`) 、模組資訊清單 () `.psd1` 、元件 () 、 `.dll` Cmdlet 定義 XML 檔案 (`.cdxml`) 或工作流程 (`.xaml`) 。</span><span class="sxs-lookup"><span data-stu-id="12279-246">Enter the file name of a script (`.ps1`), a script module (`.psm1`), a module manifest (`.psd1`), an assembly (`.dll`), a cmdlet definition XML file (`.cdxml`), or a workflow (`.xaml`).</span></span> <span data-ttu-id="12279-247">匯入模組時，從根模組檔案匯出的成員會匯入呼叫者工作階段狀態。</span><span class="sxs-lookup"><span data-stu-id="12279-247">When the module is imported, the members that are exported from the root module file are imported into the caller's session state.</span></span>

<span data-ttu-id="12279-248">如果模組有資訊清單檔案，但 **RootModule** 索引鍵中沒有指定根檔案，資訊清單會變成模組的主要檔案。</span><span class="sxs-lookup"><span data-stu-id="12279-248">If a module has a manifest file and no root file has been specified in the **RootModule** key, the manifest becomes the primary file for the module.</span></span> <span data-ttu-id="12279-249">而且，模組會變成資訊清單模組 (ModuleType = 資訊清單) 。</span><span class="sxs-lookup"><span data-stu-id="12279-249">And, the module becomes a manifest module (ModuleType = Manifest).</span></span>

<span data-ttu-id="12279-250">若要從 `.psm1` 具有資訊清單之模組中的或檔案匯出成員 `.dll` ，則必須在資訊清單中的 **RootModule** 或 **NestedModules** 索引鍵的值中指定這些檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="12279-250">To export members from `.psm1` or `.dll` files in a module that has a manifest, the names of those files must be specified in the values of the **RootModule** or **NestedModules** keys in the manifest.</span></span> <span data-ttu-id="12279-251">否則，不會匯出其成員。</span><span class="sxs-lookup"><span data-stu-id="12279-251">Otherwise, their members aren't exported.</span></span>

<span data-ttu-id="12279-252">在 PowerShell 2.0 中，此機碼稱為 **ModuleToProcess** 。</span><span class="sxs-lookup"><span data-stu-id="12279-252">In PowerShell 2.0, this key was called **ModuleToProcess** .</span></span>

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

### <span data-ttu-id="12279-253">-ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="12279-253">-ScriptsToProcess</span></span>

<span data-ttu-id="12279-254">指定匯 `.ps1` 入模組時，在呼叫者會話狀態中執行的腳本 () 檔。</span><span class="sxs-lookup"><span data-stu-id="12279-254">Specifies script (`.ps1`) files that run in the caller's session state when the module is imported.</span></span>
<span data-ttu-id="12279-255">您可以使用這些指令碼來準備環境，就像您使用登入指令碼一般。</span><span class="sxs-lookup"><span data-stu-id="12279-255">You can use these scripts to prepare an environment, just as you might use a login script.</span></span>

<span data-ttu-id="12279-256">如果要指定在模組工作階段狀態中執行的指令碼，請使用 **NestedModules** 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="12279-256">To specify scripts that run in the module's session state, use the **NestedModules** key.</span></span>

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

### <span data-ttu-id="12279-257">-Tags</span><span class="sxs-lookup"><span data-stu-id="12279-257">-Tags</span></span>

<span data-ttu-id="12279-258">指定標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="12279-258">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="12279-259">-TypesToProcess</span><span class="sxs-lookup"><span data-stu-id="12279-259">-TypesToProcess</span></span>

<span data-ttu-id="12279-260">指定匯入模組時要執行的類型檔案 (`.ps1xml`) 。</span><span class="sxs-lookup"><span data-stu-id="12279-260">Specifies the type files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="12279-261">當您匯入模組時，PowerShell 會 `Update-TypeData` 使用指定的檔案來執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="12279-261">When you import the module, PowerShell runs the `Update-TypeData` cmdlet with the specified files.</span></span>
<span data-ttu-id="12279-262">因為類型檔案未設定範圍，所以它們會影響會話中所有的會話狀態。</span><span class="sxs-lookup"><span data-stu-id="12279-262">Because type files aren't scoped, they affect all session states in the session.</span></span>

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

### <span data-ttu-id="12279-263">-VariablesToExport</span><span class="sxs-lookup"><span data-stu-id="12279-263">-VariablesToExport</span></span>

<span data-ttu-id="12279-264">指定模組匯出的變數。</span><span class="sxs-lookup"><span data-stu-id="12279-264">Specifies the variables that the module exports.</span></span> <span data-ttu-id="12279-265">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="12279-265">Wildcards are permitted.</span></span>

<span data-ttu-id="12279-266">使用此參數來限制模組匯出的變數。</span><span class="sxs-lookup"><span data-stu-id="12279-266">Use this parameter to restrict the variables that are exported by the module.</span></span> <span data-ttu-id="12279-267">**VariablesToExport** 可以從匯出的變數清單中移除變數，但它無法將變數新增至清單。</span><span class="sxs-lookup"><span data-stu-id="12279-267">**VariablesToExport** can remove variables from the list of exported variables, but it can't add variables to the list.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="12279-268">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="12279-268">-WhatIf</span></span>

<span data-ttu-id="12279-269">顯示執行時所發生 `Update-ModuleManifest` 的情況。</span><span class="sxs-lookup"><span data-stu-id="12279-269">Shows what would happen if `Update-ModuleManifest` runs.</span></span> <span data-ttu-id="12279-270">不會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="12279-270">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="12279-271">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="12279-271">CommonParameters</span></span>

<span data-ttu-id="12279-272">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="12279-272">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="12279-273">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="12279-273">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="12279-274">輸入</span><span class="sxs-lookup"><span data-stu-id="12279-274">INPUTS</span></span>

### <span data-ttu-id="12279-275">System.String</span><span class="sxs-lookup"><span data-stu-id="12279-275">System.String</span></span>

## <span data-ttu-id="12279-276">輸出</span><span class="sxs-lookup"><span data-stu-id="12279-276">OUTPUTS</span></span>

### <span data-ttu-id="12279-277">System.Object</span><span class="sxs-lookup"><span data-stu-id="12279-277">System.Object</span></span>

## <span data-ttu-id="12279-278">注意</span><span class="sxs-lookup"><span data-stu-id="12279-278">NOTES</span></span>

## <span data-ttu-id="12279-279">相關連結</span><span class="sxs-lookup"><span data-stu-id="12279-279">RELATED LINKS</span></span>
