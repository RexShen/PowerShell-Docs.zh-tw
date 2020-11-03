---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/01/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/new-scriptfileinfo?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ScriptFileInfo
ms.openlocfilehash: f416447c2c13d3dbf2d14ed5ca045164779fcbe0
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201839"
---
# <span data-ttu-id="2f68b-103">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="2f68b-103">New-ScriptFileInfo</span></span>

## <span data-ttu-id="2f68b-104">概要</span><span class="sxs-lookup"><span data-stu-id="2f68b-104">SYNOPSIS</span></span>
<span data-ttu-id="2f68b-105">建立含有中繼資料的指令檔。</span><span class="sxs-lookup"><span data-stu-id="2f68b-105">Creates a script file with metadata.</span></span>

## <span data-ttu-id="2f68b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2f68b-106">SYNTAX</span></span>

### <span data-ttu-id="2f68b-107">全部</span><span class="sxs-lookup"><span data-stu-id="2f68b-107">All</span></span>

```
New-ScriptFileInfo [[-Path] <String>] [-Version <String>] [-Author <String>] -Description <String>
 [-Guid <Guid>] [-CompanyName <String>] [-Copyright <String>] [-RequiredModules <Object[]>]
 [-ExternalModuleDependencies <String[]>] [-RequiredScripts <String[]>]
 [-ExternalScriptDependencies <String[]>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>]
 [-IconUri <Uri>] [-ReleaseNotes <String[]>] [-PrivateData <String>] [-PassThru] [-Force] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="2f68b-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="2f68b-108">DESCRIPTION</span></span>

<span data-ttu-id="2f68b-109">此 `New-ScriptFileInfo` Cmdlet 會建立 PowerShell 腳本檔案，包括腳本的相關中繼資料。</span><span class="sxs-lookup"><span data-stu-id="2f68b-109">The `New-ScriptFileInfo` cmdlet creates a PowerShell script file, including metadata about the script.</span></span>

<span data-ttu-id="2f68b-110">這些範例會使用展開將參數傳遞給 `New-ScriptFileInfo` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2f68b-110">The examples use splatting to pass parameters to the `New-ScriptFileInfo` cmdlet.</span></span> <span data-ttu-id="2f68b-111">如需詳細資訊，請參閱 [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md)。</span><span class="sxs-lookup"><span data-stu-id="2f68b-111">For more information, see [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md).</span></span>

## <span data-ttu-id="2f68b-112">範例</span><span class="sxs-lookup"><span data-stu-id="2f68b-112">EXAMPLES</span></span>

### <span data-ttu-id="2f68b-113">範例1：建立腳本檔案，並指定其版本、作者和描述</span><span class="sxs-lookup"><span data-stu-id="2f68b-113">Example 1: Create a script file and specify its version, author, and description</span></span>

<span data-ttu-id="2f68b-114">在此範例中，會建立腳本檔案，且其內容會顯示在 PowerShell 主控台中。</span><span class="sxs-lookup"><span data-stu-id="2f68b-114">In this example, a script file is created and its contents are displayed in the PowerShell console.</span></span>

```powershell
$Parms = @{
  Path = "C:\Test\Temp-Scriptfile.ps1"
  Version = "1.0"
  Author = "pattif@contoso.com"
  Description = "My test script file description goes here"
  }
New-ScriptFileInfo @Parms
Get-Content -Path C:\Test\Temp-Scriptfile.ps1
```

```Output
<#PSScriptInfo

.VERSION 1.0

.GUID 3bb10ee7-38c1-41b9-88ea-16899164fc19

.AUTHOR pattif@contoso.com

.COMPANYNAME

.COPYRIGHT

.TAGS

.LICENSEURI

.PROJECTURI

.ICONURI

.EXTERNALMODULEDEPENDENCIES

.REQUIREDSCRIPTS

.EXTERNALSCRIPTDEPENDENCIES

.RELEASENOTES

.PRIVATEDATA

#>

<#

.DESCRIPTION
 My test script file description goes here

#>
Param()
```

<span data-ttu-id="2f68b-115">此 `New-ScriptFileInfo` Cmdlet 會使用展開來設定腳本的數個參數。</span><span class="sxs-lookup"><span data-stu-id="2f68b-115">The `New-ScriptFileInfo` cmdlet uses splatting to configure several parameters for the script.</span></span>
<span data-ttu-id="2f68b-116">**路徑** ：設定腳本的位置和名稱。</span><span class="sxs-lookup"><span data-stu-id="2f68b-116">**Path** sets the location and name of the script.</span></span> <span data-ttu-id="2f68b-117">**Version** 指定腳本的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="2f68b-117">**Version** specifies the script's version number.</span></span> <span data-ttu-id="2f68b-118">**Author** 是建立腳本之人員的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="2f68b-118">**Author** is the email address of the person who created the script.</span></span> <span data-ttu-id="2f68b-119">**描述** 說明腳本的用途。</span><span class="sxs-lookup"><span data-stu-id="2f68b-119">**Description** explains the script's purpose.</span></span>

<span data-ttu-id="2f68b-120">建立腳本之後，會 `Get-Content` 使用 **Path** 參數來尋找腳本。</span><span class="sxs-lookup"><span data-stu-id="2f68b-120">After the script is created, `Get-Content` uses the **Path** parameter to locate the script.</span></span> <span data-ttu-id="2f68b-121">腳本的內容會顯示在 PowerShell 主控台中。</span><span class="sxs-lookup"><span data-stu-id="2f68b-121">The script's contents are displayed in the PowerShell console.</span></span>

### <span data-ttu-id="2f68b-122">範例2：測試指令檔</span><span class="sxs-lookup"><span data-stu-id="2f68b-122">Example 2: Test a script file</span></span>

<span data-ttu-id="2f68b-123">在此範例中，會測試 **範例 1** 中所建立之腳本的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="2f68b-123">In this example, the metadata for the script created in **Example 1** is tested.</span></span>

```powershell
Test-ScriptFileInfo -Path C:\Test\Temp-Scriptfile.ps1
```

```Output
Version   Name                  Author               Description
-------   ----                  ------               -----------
1.0       Temp-Scriptfile       pattif@contoso.com   My test script file description goes here
```

<span data-ttu-id="2f68b-124">此 `Test-ScriptFileInfo` Cmdlet 會使用 **Path** 參數來指定腳本檔的位置。</span><span class="sxs-lookup"><span data-stu-id="2f68b-124">The `Test-ScriptFileInfo` cmdlet uses the **Path** parameter to specify the script file's location.</span></span>

### <span data-ttu-id="2f68b-125">範例3：建立包含所有中繼資料屬性的腳本檔案</span><span class="sxs-lookup"><span data-stu-id="2f68b-125">Example 3: Create a script file with all the metadata properties</span></span>

<span data-ttu-id="2f68b-126">此範例會使用展開來建立名為的腳本檔案 `New-ScriptFile.ps1` ，其中包含其所有的中繼資料屬性。</span><span class="sxs-lookup"><span data-stu-id="2f68b-126">This example uses splatting to create a script file named `New-ScriptFile.ps1` that includes all its metadata properties.</span></span> <span data-ttu-id="2f68b-127">**Verbose** 參數會指定在建立腳本時顯示詳細資訊輸出。</span><span class="sxs-lookup"><span data-stu-id="2f68b-127">The **Verbose** parameter specifies that verbose output is displayed as the script is created.</span></span>

```powershell
$Parms = @{
 Path = "C:\Test\New-ScriptFile.ps1"
 Verbose = $True
 Version = "1.0"
 Author = "pattif@contoso.com"
 Description = "My new script file test"
 CompanyName = "Contoso Corporation"
 Copyright = "2019 Contoso Corporation. All rights reserved."
 ExternalModuleDependencies = "ff","bb"
 RequiredScripts = "Start-WFContosoServer", "Stop-ContosoServerScript"
 ExternalScriptDependencies = "Stop-ContosoServerScript"
 Tags = @("Tag1", "Tag2", "Tag3")
 ProjectUri = "https://contoso.com"
 LicenseUri = "https://contoso.com/License"
 IconUri = "https://contoso.com/Icon"
 PassThru = $True
 ReleaseNotes = @("Contoso script now supports the following features:",
   "Feature 1",
   "Feature 2",
   "Feature 3",
   "Feature 4",
   "Feature 5")
 RequiredModules =
   "1",
   "2",
   "RequiredModule1",
   @{ModuleName="RequiredModule2";ModuleVersion="1.0"},
   @{ModuleName="RequiredModule3";RequiredVersion="2.0"},
   "ExternalModule1"
 }
New-ScriptFileInfo @Parms
```

```Output
VERBOSE: Performing the operation "Creating the 'C:\Test\New-ScriptFile.ps1'
  PowerShell Script file" on target "C:\Test\New-ScriptFile.ps1".

<#PSScriptInfo

.VERSION 1.0

.GUID 4fabe8c7-7862-45b1-a72e-1352a433b77d

.AUTHOR pattif@contoso.com

.COMPANYNAME Contoso Corporation

.COPYRIGHT 2019 Contoso Corporation. All rights reserved.

.TAGS Tag1 Tag2 Tag3

.LICENSEURI https://contoso.com/License

.PROJECTURI https://contoso.com/

.ICONURI https://contoso.com/Icon

.EXTERNALMODULEDEPENDENCIES ff,bb

.REQUIREDSCRIPTS Start-WFContosoServer,Stop-ContosoServerScript

.EXTERNALSCRIPTDEPENDENCIES Stop-ContosoServerScript

.RELEASENOTES
Contoso script now supports the following features:
Feature 1
Feature 2
Feature 3
Feature 4
Feature 5

.PRIVATEDATA

#>

#Requires -Module 1
#Requires -Module 2
#Requires -Module RequiredModule1
#Requires -Module @{ModuleName = 'RequiredModule2'; ModuleVersion = '1.0'}
#Requires -Module @{RequiredVersion = '2.0'; ModuleName = 'RequiredModule3'}
#Requires -Module ExternalModule1

<#

.DESCRIPTION
 My new script file test

#>
Param()
```

## <span data-ttu-id="2f68b-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2f68b-128">PARAMETERS</span></span>

### <span data-ttu-id="2f68b-129">-作者</span><span class="sxs-lookup"><span data-stu-id="2f68b-129">-Author</span></span>

<span data-ttu-id="2f68b-130">指定腳本作者。</span><span class="sxs-lookup"><span data-stu-id="2f68b-130">Specifies the script author.</span></span>

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

### <span data-ttu-id="2f68b-131">-公司名稱</span><span class="sxs-lookup"><span data-stu-id="2f68b-131">-CompanyName</span></span>

<span data-ttu-id="2f68b-132">指定建立腳本的公司或廠商。</span><span class="sxs-lookup"><span data-stu-id="2f68b-132">Specifies the company or vendor who created the script.</span></span>

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

### <span data-ttu-id="2f68b-133">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2f68b-133">-Confirm</span></span>

<span data-ttu-id="2f68b-134">在執行之前提示您確認 `New-ScriptFileInfo` 。</span><span class="sxs-lookup"><span data-stu-id="2f68b-134">Prompts you for confirmation before running the `New-ScriptFileInfo`.</span></span>

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

### <span data-ttu-id="2f68b-135">-著作權</span><span class="sxs-lookup"><span data-stu-id="2f68b-135">-Copyright</span></span>

<span data-ttu-id="2f68b-136">指定腳本的著作權語句。</span><span class="sxs-lookup"><span data-stu-id="2f68b-136">Specifies a copyright statement for the script.</span></span>

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

### <span data-ttu-id="2f68b-137">-Description</span><span class="sxs-lookup"><span data-stu-id="2f68b-137">-Description</span></span>

<span data-ttu-id="2f68b-138">指定腳本的描述。</span><span class="sxs-lookup"><span data-stu-id="2f68b-138">Specifies a description for the script.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f68b-139">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="2f68b-139">-ExternalModuleDependencies</span></span>

<span data-ttu-id="2f68b-140">指定外部模組相依性的陣列。</span><span class="sxs-lookup"><span data-stu-id="2f68b-140">Specifies an array of external module dependencies.</span></span>

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

### <span data-ttu-id="2f68b-141">-ExternalScriptDependencies</span><span class="sxs-lookup"><span data-stu-id="2f68b-141">-ExternalScriptDependencies</span></span>

<span data-ttu-id="2f68b-142">指定外部腳本相依性的陣列。</span><span class="sxs-lookup"><span data-stu-id="2f68b-142">Specifies an array of external script dependencies.</span></span>

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

### <span data-ttu-id="2f68b-143">-Force</span><span class="sxs-lookup"><span data-stu-id="2f68b-143">-Force</span></span>

<span data-ttu-id="2f68b-144">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="2f68b-144">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="2f68b-145">-Guid</span><span class="sxs-lookup"><span data-stu-id="2f68b-145">-Guid</span></span>

<span data-ttu-id="2f68b-146">指定腳本的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="2f68b-146">Specifies a unique ID for the script.</span></span>

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

### <span data-ttu-id="2f68b-147">-IconUri</span><span class="sxs-lookup"><span data-stu-id="2f68b-147">-IconUri</span></span>

<span data-ttu-id="2f68b-148">指定腳本圖示的 URL。</span><span class="sxs-lookup"><span data-stu-id="2f68b-148">Specifies the URL of an icon for the script.</span></span> <span data-ttu-id="2f68b-149">指定的圖示會顯示在腳本的資源庫網頁上。</span><span class="sxs-lookup"><span data-stu-id="2f68b-149">The specified icon is displayed on the gallery web page for the script.</span></span>

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

### <span data-ttu-id="2f68b-150">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="2f68b-150">-LicenseUri</span></span>

<span data-ttu-id="2f68b-151">指定授權條款的 URL。</span><span class="sxs-lookup"><span data-stu-id="2f68b-151">Specifies the URL of licensing terms.</span></span>

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

### <span data-ttu-id="2f68b-152">-PassThru</span><span class="sxs-lookup"><span data-stu-id="2f68b-152">-PassThru</span></span>

<span data-ttu-id="2f68b-153">傳回代表您正在使用之專案的物件。</span><span class="sxs-lookup"><span data-stu-id="2f68b-153">Returns an object that represents the item with which you're working.</span></span> <span data-ttu-id="2f68b-154">依預設， `New-ScriptFileInfo` 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="2f68b-154">By default, `New-ScriptFileInfo` doesn't generate any output.</span></span>

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

### <span data-ttu-id="2f68b-155">-Path</span><span class="sxs-lookup"><span data-stu-id="2f68b-155">-Path</span></span>

<span data-ttu-id="2f68b-156">指定儲存指令檔的位置。</span><span class="sxs-lookup"><span data-stu-id="2f68b-156">Specifies the location where the script file is saved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2f68b-157">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="2f68b-157">-PrivateData</span></span>

<span data-ttu-id="2f68b-158">指定腳本的私用資料。</span><span class="sxs-lookup"><span data-stu-id="2f68b-158">Specifies private data for the script.</span></span>

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

### <span data-ttu-id="2f68b-159">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="2f68b-159">-ProjectUri</span></span>

<span data-ttu-id="2f68b-160">指定與這個專案相關之網頁的 URL。</span><span class="sxs-lookup"><span data-stu-id="2f68b-160">Specifies the URL of a web page about this project.</span></span>

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

### <span data-ttu-id="2f68b-161">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="2f68b-161">-ReleaseNotes</span></span>

<span data-ttu-id="2f68b-162">指定字串陣列，其中包含您想要提供給這個版本腳本使用者使用的版本資訊或批註。</span><span class="sxs-lookup"><span data-stu-id="2f68b-162">Specifies a string array that contains release notes or comments that you want available to users of this version of the script.</span></span>

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

### <span data-ttu-id="2f68b-163">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="2f68b-163">-RequiredModules</span></span>

<span data-ttu-id="2f68b-164">指定必須在全域工作階段狀態的模組。</span><span class="sxs-lookup"><span data-stu-id="2f68b-164">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="2f68b-165">如果必要的模組不在全域會話狀態中，則 PowerShell 會將它們匯入。</span><span class="sxs-lookup"><span data-stu-id="2f68b-165">If the required modules aren't in the global session state, PowerShell imports them.</span></span>

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

### <span data-ttu-id="2f68b-166">-RequiredScripts</span><span class="sxs-lookup"><span data-stu-id="2f68b-166">-RequiredScripts</span></span>

<span data-ttu-id="2f68b-167">指定必要腳本的陣列。</span><span class="sxs-lookup"><span data-stu-id="2f68b-167">Specifies an array of required scripts.</span></span>

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

### <span data-ttu-id="2f68b-168">-Tags</span><span class="sxs-lookup"><span data-stu-id="2f68b-168">-Tags</span></span>

<span data-ttu-id="2f68b-169">指定標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="2f68b-169">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="2f68b-170">-Version</span><span class="sxs-lookup"><span data-stu-id="2f68b-170">-Version</span></span>

<span data-ttu-id="2f68b-171">指定腳本的版本。</span><span class="sxs-lookup"><span data-stu-id="2f68b-171">Specifies the version of the script.</span></span>

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

### <span data-ttu-id="2f68b-172">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2f68b-172">-WhatIf</span></span>

<span data-ttu-id="2f68b-173">顯示執行時所發生 `New-ScriptFileInfo` 的情況。</span><span class="sxs-lookup"><span data-stu-id="2f68b-173">Shows what would happen if `New-ScriptFileInfo` runs.</span></span> <span data-ttu-id="2f68b-174">不會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2f68b-174">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="2f68b-175">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2f68b-175">CommonParameters</span></span>

<span data-ttu-id="2f68b-176">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="2f68b-176">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2f68b-177">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="2f68b-177">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2f68b-178">輸入</span><span class="sxs-lookup"><span data-stu-id="2f68b-178">INPUTS</span></span>

### <span data-ttu-id="2f68b-179">System.String</span><span class="sxs-lookup"><span data-stu-id="2f68b-179">System.String</span></span>

## <span data-ttu-id="2f68b-180">輸出</span><span class="sxs-lookup"><span data-stu-id="2f68b-180">OUTPUTS</span></span>

### <span data-ttu-id="2f68b-181">System.Object</span><span class="sxs-lookup"><span data-stu-id="2f68b-181">System.Object</span></span>

## <span data-ttu-id="2f68b-182">注意</span><span class="sxs-lookup"><span data-stu-id="2f68b-182">NOTES</span></span>

## <span data-ttu-id="2f68b-183">相關連結</span><span class="sxs-lookup"><span data-stu-id="2f68b-183">RELATED LINKS</span></span>

[<span data-ttu-id="2f68b-184">about_Splatting</span><span class="sxs-lookup"><span data-stu-id="2f68b-184">about_Splatting</span></span>](../Microsoft.Powershell.Core/About/about_splatting.md)

[<span data-ttu-id="2f68b-185">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="2f68b-185">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)

[<span data-ttu-id="2f68b-186">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="2f68b-186">Update-ScriptFileInfo</span></span>](Update-ScriptFileInfo.md)
