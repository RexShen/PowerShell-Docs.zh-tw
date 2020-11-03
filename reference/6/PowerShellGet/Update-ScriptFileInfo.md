---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/09/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-scriptfileinfo?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-ScriptFileInfo
ms.openlocfilehash: ff1d59cd3a956c6e6964bdfc64de6f52ef2e944b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204536"
---
# <span data-ttu-id="70883-103">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="70883-103">Update-ScriptFileInfo</span></span>

## <span data-ttu-id="70883-104">概要</span><span class="sxs-lookup"><span data-stu-id="70883-104">SYNOPSIS</span></span>
<span data-ttu-id="70883-105">更新腳本的資訊。</span><span class="sxs-lookup"><span data-stu-id="70883-105">Updates information for a script.</span></span>

## <span data-ttu-id="70883-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="70883-106">SYNTAX</span></span>

### <span data-ttu-id="70883-107">PathParameterSet (預設) </span><span class="sxs-lookup"><span data-stu-id="70883-107">PathParameterSet (Default)</span></span>

```
Update-ScriptFileInfo [-Path] <String> [-Version <String>] [-Author <String>] [-Guid <Guid>]
 [-Description <String>] [-CompanyName <String>] [-Copyright <String>] [-RequiredModules <Object[]>]
 [-ExternalModuleDependencies <String[]>] [-RequiredScripts <String[]>]
 [-ExternalScriptDependencies <String[]>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>]
 [-IconUri <Uri>] [-ReleaseNotes <String[]>] [-PrivateData <String>] [-PassThru] [-Force] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="70883-108">LiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="70883-108">LiteralPathParameterSet</span></span>

```
Update-ScriptFileInfo [-LiteralPath] <String> [-Version <String>] [-Author <String>] [-Guid <Guid>]
 [-Description <String>] [-CompanyName <String>] [-Copyright <String>] [-RequiredModules <Object[]>]
 [-ExternalModuleDependencies <String[]>] [-RequiredScripts <String[]>]
 [-ExternalScriptDependencies <String[]>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>]
 [-IconUri <Uri>] [-ReleaseNotes <String[]>] [-PrivateData <String>] [-PassThru] [-Force] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="70883-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="70883-109">DESCRIPTION</span></span>

<span data-ttu-id="70883-110">此 `Update-ScriptFileInfo` Cmdlet 會更新腳本的屬性值。</span><span class="sxs-lookup"><span data-stu-id="70883-110">The `Update-ScriptFileInfo` cmdlet updates a script's property values.</span></span> <span data-ttu-id="70883-111">例如，[版本]、[作者] 或 [描述] 的值。</span><span class="sxs-lookup"><span data-stu-id="70883-111">For example, the values for version, author, or description.</span></span>

## <span data-ttu-id="70883-112">範例</span><span class="sxs-lookup"><span data-stu-id="70883-112">EXAMPLES</span></span>

### <span data-ttu-id="70883-113">範例1：更新指令檔的版本</span><span class="sxs-lookup"><span data-stu-id="70883-113">Example 1: Update the version of a script file</span></span>

<span data-ttu-id="70883-114">在此範例中，會以新的屬性值更新現有的腳本檔案。</span><span class="sxs-lookup"><span data-stu-id="70883-114">In this example, an existing script file is updated with new property values.</span></span>

<span data-ttu-id="70883-115">展開用來將參數傳遞給 `Update-ScriptFileInfo` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="70883-115">Splatting is used to pass parameters to the `Update-ScriptFileInfo` cmdlet.</span></span> <span data-ttu-id="70883-116">如需詳細資訊，請參閱 [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md)。</span><span class="sxs-lookup"><span data-stu-id="70883-116">For more information, see [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md).</span></span>

```powershell
$Parms = @{
  Path = "C:\Test\Temp-Scriptfile.ps1"
  Version = "2.0"
  Author = "bob@contoso.com"
  CompanyName = "Contoso"
  Description = "This is the updated description"
  }
Update-ScriptFileInfo @Parms -PassThru
```

```Output
<#PSScriptInfo

.VERSION 2.0

.GUID 4609f00c-e850-4d3f-9c69-3741e56e4133

.AUTHOR bob@contoso.com

.COMPANYNAME Contoso

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
This is the updated description

#>
Param()
```

<span data-ttu-id="70883-117">`$Parms` 儲存 **路徑** 、 **版本** 、 **作者** 、 **公司名稱** 和 **描述** 的參數值。</span><span class="sxs-lookup"><span data-stu-id="70883-117">`$Parms` stores the parameter values for **Path** , **Version** , **Author** , **CompanyName** , and **Description** .</span></span> <span data-ttu-id="70883-118">`Update-ScriptFileInfo` 從取得參數值 `@Parms` ，並更新腳本。</span><span class="sxs-lookup"><span data-stu-id="70883-118">`Update-ScriptFileInfo` gets the parameter values from `@Parms` and updates the script.</span></span> <span data-ttu-id="70883-119">**PassThru** 參數會在 PowerShell 主控台中顯示腳本的內容。</span><span class="sxs-lookup"><span data-stu-id="70883-119">The **PassThru** parameter displays the script's contents in the PowerShell console.</span></span>

## <span data-ttu-id="70883-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="70883-120">PARAMETERS</span></span>

### <span data-ttu-id="70883-121">-作者</span><span class="sxs-lookup"><span data-stu-id="70883-121">-Author</span></span>

<span data-ttu-id="70883-122">指定腳本作者。</span><span class="sxs-lookup"><span data-stu-id="70883-122">Specifies the script author.</span></span>

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

### <span data-ttu-id="70883-123">-公司名稱</span><span class="sxs-lookup"><span data-stu-id="70883-123">-CompanyName</span></span>

<span data-ttu-id="70883-124">指定建立腳本的公司或廠商。</span><span class="sxs-lookup"><span data-stu-id="70883-124">Specifies the company or vendor who created the script.</span></span>

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

### <span data-ttu-id="70883-125">-Confirm</span><span class="sxs-lookup"><span data-stu-id="70883-125">-Confirm</span></span>

<span data-ttu-id="70883-126">在執行之前提示您確認 `Update-ScriptFileInfo` 。</span><span class="sxs-lookup"><span data-stu-id="70883-126">Prompts you for confirmation before running `Update-ScriptFileInfo`.</span></span>

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

### <span data-ttu-id="70883-127">-著作權</span><span class="sxs-lookup"><span data-stu-id="70883-127">-Copyright</span></span>

<span data-ttu-id="70883-128">指定腳本的著作權語句。</span><span class="sxs-lookup"><span data-stu-id="70883-128">Specifies a copyright statement for the script.</span></span>

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

### <span data-ttu-id="70883-129">-Description</span><span class="sxs-lookup"><span data-stu-id="70883-129">-Description</span></span>

<span data-ttu-id="70883-130">指定腳本的描述。</span><span class="sxs-lookup"><span data-stu-id="70883-130">Specifies a description for the script.</span></span>

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

### <span data-ttu-id="70883-131">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="70883-131">-ExternalModuleDependencies</span></span>

<span data-ttu-id="70883-132">指定外部模組相依性的陣列。</span><span class="sxs-lookup"><span data-stu-id="70883-132">Specifies an array of external module dependencies.</span></span>

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

### <span data-ttu-id="70883-133">-ExternalScriptDependencies</span><span class="sxs-lookup"><span data-stu-id="70883-133">-ExternalScriptDependencies</span></span>

<span data-ttu-id="70883-134">指定外部腳本相依性的陣列。</span><span class="sxs-lookup"><span data-stu-id="70883-134">Specifies an array of external script dependencies.</span></span>

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

### <span data-ttu-id="70883-135">-Force</span><span class="sxs-lookup"><span data-stu-id="70883-135">-Force</span></span>

<span data-ttu-id="70883-136">強制 `Update-ScriptFileInfo` 執行而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="70883-136">Forces `Update-ScriptFileInfo` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="70883-137">-Guid</span><span class="sxs-lookup"><span data-stu-id="70883-137">-Guid</span></span>

<span data-ttu-id="70883-138">指定腳本的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="70883-138">Specifies a unique ID for a script.</span></span>

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

### <span data-ttu-id="70883-139">-IconUri</span><span class="sxs-lookup"><span data-stu-id="70883-139">-IconUri</span></span>

<span data-ttu-id="70883-140">指定腳本圖示的 URL。</span><span class="sxs-lookup"><span data-stu-id="70883-140">Specifies the URL of an icon for the script.</span></span> <span data-ttu-id="70883-141">指定的圖示會顯示在腳本的資源庫網頁上。</span><span class="sxs-lookup"><span data-stu-id="70883-141">The specified icon is displayed on the gallery web page for the script.</span></span>

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

### <span data-ttu-id="70883-142">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="70883-142">-LicenseUri</span></span>

<span data-ttu-id="70883-143">指定授權條款的 URL。</span><span class="sxs-lookup"><span data-stu-id="70883-143">Specifies the URL of licensing terms.</span></span>

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

### <span data-ttu-id="70883-144">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="70883-144">-LiteralPath</span></span>

<span data-ttu-id="70883-145">指定一個或多個位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="70883-145">Specifies a path to one or more locations.</span></span> <span data-ttu-id="70883-146">**LiteralPath** 參數的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="70883-146">The **LiteralPath** parameter's value is used exactly as it's entered.</span></span> <span data-ttu-id="70883-147">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="70883-147">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="70883-148">如果路徑包含 escape 字元，請用單引號括住。</span><span class="sxs-lookup"><span data-stu-id="70883-148">If the path includes escape characters, enclose them in single quotation marks.</span></span> <span data-ttu-id="70883-149">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="70883-149">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPathParameterSet
Aliases: PSPath

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="70883-150">-PassThru</span><span class="sxs-lookup"><span data-stu-id="70883-150">-PassThru</span></span>

<span data-ttu-id="70883-151">傳回代表您正在使用之專案的物件。</span><span class="sxs-lookup"><span data-stu-id="70883-151">Returns an object that represents the item with which you're working.</span></span> <span data-ttu-id="70883-152">依預設， `Update-ScriptFileInfo` 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="70883-152">By default, `Update-ScriptFileInfo` doesn't generate any output.</span></span>

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

### <span data-ttu-id="70883-153">-Path</span><span class="sxs-lookup"><span data-stu-id="70883-153">-Path</span></span>

<span data-ttu-id="70883-154">指定腳本檔的位置。</span><span class="sxs-lookup"><span data-stu-id="70883-154">Specifies the script file's location.</span></span> <span data-ttu-id="70883-155">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="70883-155">Wildcards are permitted.</span></span>

```yaml
Type: System.String
Parameter Sets: PathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="70883-156">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="70883-156">-PrivateData</span></span>

<span data-ttu-id="70883-157">指定腳本的私用資料。</span><span class="sxs-lookup"><span data-stu-id="70883-157">Specifies the private data for the script.</span></span>

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

### <span data-ttu-id="70883-158">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="70883-158">-ProjectUri</span></span>

<span data-ttu-id="70883-159">指定與這個專案相關之網頁的 URL。</span><span class="sxs-lookup"><span data-stu-id="70883-159">Specifies the URL of a web page about this project.</span></span>

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

### <span data-ttu-id="70883-160">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="70883-160">-ReleaseNotes</span></span>

<span data-ttu-id="70883-161">指定字串陣列，其中包含您想要用於此版本腳本的版本資訊或批註。</span><span class="sxs-lookup"><span data-stu-id="70883-161">Specifies a string array that contains release notes or comments that you want available for this version of the script.</span></span>

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

### <span data-ttu-id="70883-162">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="70883-162">-RequiredModules</span></span>

<span data-ttu-id="70883-163">指定必須在全域工作階段狀態的模組。</span><span class="sxs-lookup"><span data-stu-id="70883-163">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="70883-164">如果必要的模組不在全域會話狀態中，則 PowerShell 會將它們匯入。</span><span class="sxs-lookup"><span data-stu-id="70883-164">If the required modules aren't in the global session state, PowerShell imports them.</span></span>

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

### <span data-ttu-id="70883-165">-RequiredScripts</span><span class="sxs-lookup"><span data-stu-id="70883-165">-RequiredScripts</span></span>

<span data-ttu-id="70883-166">指定必要腳本的陣列。</span><span class="sxs-lookup"><span data-stu-id="70883-166">Specifies an array of required scripts.</span></span>

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

### <span data-ttu-id="70883-167">-Tags</span><span class="sxs-lookup"><span data-stu-id="70883-167">-Tags</span></span>

<span data-ttu-id="70883-168">指定標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="70883-168">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="70883-169">-Version</span><span class="sxs-lookup"><span data-stu-id="70883-169">-Version</span></span>

<span data-ttu-id="70883-170">指定腳本的版本。</span><span class="sxs-lookup"><span data-stu-id="70883-170">Specifies the script's version.</span></span>

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

### <span data-ttu-id="70883-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="70883-171">-WhatIf</span></span>

<span data-ttu-id="70883-172">顯示執行時所發生 `Update-ScriptFileInfo` 的情況。</span><span class="sxs-lookup"><span data-stu-id="70883-172">Shows what would happen if `Update-ScriptFileInfo` runs.</span></span> <span data-ttu-id="70883-173">不會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="70883-173">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="70883-174">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="70883-174">CommonParameters</span></span>

<span data-ttu-id="70883-175">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="70883-175">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="70883-176">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="70883-176">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="70883-177">輸入</span><span class="sxs-lookup"><span data-stu-id="70883-177">INPUTS</span></span>

### <span data-ttu-id="70883-178">System.String</span><span class="sxs-lookup"><span data-stu-id="70883-178">System.String</span></span>

## <span data-ttu-id="70883-179">輸出</span><span class="sxs-lookup"><span data-stu-id="70883-179">OUTPUTS</span></span>

### <span data-ttu-id="70883-180">System.Object</span><span class="sxs-lookup"><span data-stu-id="70883-180">System.Object</span></span>

## <span data-ttu-id="70883-181">注意</span><span class="sxs-lookup"><span data-stu-id="70883-181">NOTES</span></span>

<span data-ttu-id="70883-182">使用 `Test-ScriptFileInfo` Cmdlet 來驗證腳本的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="70883-182">Use the `Test-ScriptFileInfo` cmdlet to validate a script's metadata.</span></span> <span data-ttu-id="70883-183">腳本必須包含版本、GUID、描述和作者的值。</span><span class="sxs-lookup"><span data-stu-id="70883-183">Scripts must include values for version, GUID, description, and author.</span></span>

## <span data-ttu-id="70883-184">相關連結</span><span class="sxs-lookup"><span data-stu-id="70883-184">RELATED LINKS</span></span>

[<span data-ttu-id="70883-185">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="70883-185">New-ScriptFileInfo</span></span>](New-ScriptFileInfo.md)

[<span data-ttu-id="70883-186">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="70883-186">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)
