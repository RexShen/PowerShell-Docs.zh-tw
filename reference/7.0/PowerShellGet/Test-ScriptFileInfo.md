---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/test-scriptfileinfo?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-ScriptFileInfo
ms.openlocfilehash: 24e2ac0c7bd9652c406e05259c57181b373b75f8
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201256"
---
# <span data-ttu-id="ac165-103">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="ac165-103">Test-ScriptFileInfo</span></span>

## <span data-ttu-id="ac165-104">概要</span><span class="sxs-lookup"><span data-stu-id="ac165-104">SYNOPSIS</span></span>
<span data-ttu-id="ac165-105">驗證腳本的批註區塊。</span><span class="sxs-lookup"><span data-stu-id="ac165-105">Validates a comment block for a script.</span></span>

## <span data-ttu-id="ac165-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ac165-106">SYNTAX</span></span>

### <span data-ttu-id="ac165-107">PathParameterSet (預設) </span><span class="sxs-lookup"><span data-stu-id="ac165-107">PathParameterSet (Default)</span></span>

```
Test-ScriptFileInfo [-Path] <String> [<CommonParameters>]
```

### <span data-ttu-id="ac165-108">LiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="ac165-108">LiteralPathParameterSet</span></span>

```
Test-ScriptFileInfo -LiteralPath <String> [<CommonParameters>]
```

## <span data-ttu-id="ac165-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="ac165-109">DESCRIPTION</span></span>

<span data-ttu-id="ac165-110">**New-scriptfileinfo** 指令程式會驗證腳本開頭的批註區塊，該腳本會使用 Publish-Script Cmdlet 發佈。</span><span class="sxs-lookup"><span data-stu-id="ac165-110">The **Test-ScriptFileInfo** cmdlet validates the comment block at the beginning of a script that will be published with the Publish-Script cmdlet.</span></span>
<span data-ttu-id="ac165-111">如果批註區塊有錯誤，此 Cmdlet 會傳回錯誤所在位置或修正方式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ac165-111">If the comment block has an error, this cmdlet returns information about where the error is located or how to correct it.</span></span>

## <span data-ttu-id="ac165-112">範例</span><span class="sxs-lookup"><span data-stu-id="ac165-112">EXAMPLES</span></span>

### <span data-ttu-id="ac165-113">範例1：測試指令檔</span><span class="sxs-lookup"><span data-stu-id="ac165-113">Example 1: Test a script file</span></span>

```
PS C:\> Test-ScriptFileInfo -Path "C:\temp\temp_scripts\New-ScriptFile.ps1"
Version    Name                      Author               Description
-------    ----                      ------               -----------
1.0        New-ScriptFile            pattif               my new script file test
```

<span data-ttu-id="ac165-114">此命令會測試 New-ScriptFile.ps1 腳本檔案並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="ac165-114">This command tests the New-ScriptFile.ps1 script file and displays the results.</span></span>
<span data-ttu-id="ac165-115">腳本檔案包含有效的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="ac165-115">The script file includes valid metadata.</span></span>

### <span data-ttu-id="ac165-116">範例2：測試具有所有中繼資料屬性值的腳本檔案</span><span class="sxs-lookup"><span data-stu-id="ac165-116">Example 2: Test a script file that has values for all metadata properties</span></span>

```
PS C:\> Test-ScriptFileInfo -Path "D:\code\Test-Runbook.ps1" | Format-List *
Name                       : Test-Runbook
Path                       : D:\code\Test-Runbook.ps1
ScriptBase                 : D:\code
ReleaseNotes               : {contoso script now supports following features, Feature 1, Feature 2, Feature 3...}
Version                    : 1.0
Guid                       : eb246b19-17da-4392-8c89-7c280f69ad0e
Author                     : pattif
CompanyName                : Microsoft Corporation
Copyright                  : 2015 Microsoft Corporation. All rights reserved.
Tags                       : {Tag1, Tag2, Tag3}
LicenseUri                 : https://contoso.com/License
ProjectUri                 : https://contoso.com/
IconUri                    : https://contoso.com/MyScriptIcon
ExternalModuleDependencies : ExternalModule1
RequiredScripts            : {Start-WFContosoServer, Stop-ContosoServerScript}
ExternalScriptDependencies : Stop-ContosoServerScript
Description                : Contoso Script example
RequiredModules            : {RequiredModule1, @{ ModuleName = 'RequiredModule2'; ModuleVersion = '1.0' }, @{ ModuleName = 'RequiredModule3'; RequiredVersion = '2.0' }, ExternalModule1}
ExportedCommands           : {Test-WebUri, ValidateAndAdd-PSScriptInfoEntry, Get-PSScriptInfo, My-Workflow...}
ExportedFunctions          : {Test-WebUri, ValidateAndAdd-PSScriptInfoEntry, Get-PSScriptInfo, My-AdvPSCmdlet}
ExportedWorkflows          : My-Workflow
```

<span data-ttu-id="ac165-117">此命令會測試腳本檔 Test-Runbook.ps1 並使用管線運算子將結果傳送至 Format-List Cmdlet 以格式化結果。</span><span class="sxs-lookup"><span data-stu-id="ac165-117">This command tests the script file Test-Runbook.ps1 and uses the pipeline operator to pass the results to the Format-List cmdlet to format the results.</span></span>

### <span data-ttu-id="ac165-118">範例3：測試沒有中繼資料的腳本檔</span><span class="sxs-lookup"><span data-stu-id="ac165-118">Example 3: Test a script file that has no metadata</span></span>

```
PS C:\> Test-ScriptFileInfo -Path "D:\code\Hello-World.ps1"
Test-ScriptFileInfo : Script 'D:\code\Hello-World.ps1' is missing required metadata properties. Verify that the script file has Version, Description
and Author properties. You can use the Update-ScriptFileInfo or New-ScriptFileInfo cmdlet to add or update the PSScriptInfo to the script file.
At line:1 char:1
+ Test-ScriptFileInfo D:\code\Hello-World.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidArgument: (D:\code\Hello-World.ps1:String) [Test-ScriptFileInfo], ArgumentException

+ FullyQualifiedErrorId : MissingRequiredPSScriptInfoProperties,Test-ScriptFile
```

<span data-ttu-id="ac165-119">此命令會測試腳本檔 Hello-World.ps1，其沒有相關聯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="ac165-119">This command tests the script file Hello-World.ps1, which has no metadata associated with it.</span></span>

## <span data-ttu-id="ac165-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ac165-120">PARAMETERS</span></span>

### <span data-ttu-id="ac165-121">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="ac165-121">-LiteralPath</span></span>

<span data-ttu-id="ac165-122">指定一個或多個位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="ac165-122">Specifies a path to one or more locations.</span></span>
<span data-ttu-id="ac165-123">與 *Path* 參數不同， *LiteralPath* 參數的值會完全依照輸入的值來使用。</span><span class="sxs-lookup"><span data-stu-id="ac165-123">Unlike the *Path* parameter, the value of the *LiteralPath* parameter is used exactly as it is entered.</span></span>
<span data-ttu-id="ac165-124">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="ac165-124">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="ac165-125">如果路徑包含 escape 字元，請用單引號括住。</span><span class="sxs-lookup"><span data-stu-id="ac165-125">If the path includes escape characters, enclose them in single quotation marks.</span></span>
<span data-ttu-id="ac165-126">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="ac165-126">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPathParameterSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ac165-127">-Path</span><span class="sxs-lookup"><span data-stu-id="ac165-127">-Path</span></span>

<span data-ttu-id="ac165-128">指定一個或多個位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="ac165-128">Specifies a path to one or more locations.</span></span>
<span data-ttu-id="ac165-129">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="ac165-129">Wildcards are permitted.</span></span>
<span data-ttu-id="ac165-130">預設位置是目前的目錄 (.)。</span><span class="sxs-lookup"><span data-stu-id="ac165-130">The default location is the current directory (.).</span></span>

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

### <span data-ttu-id="ac165-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ac165-131">CommonParameters</span></span>

<span data-ttu-id="ac165-132">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="ac165-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ac165-133">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="ac165-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ac165-134">輸入</span><span class="sxs-lookup"><span data-stu-id="ac165-134">INPUTS</span></span>

### <span data-ttu-id="ac165-135">System.String</span><span class="sxs-lookup"><span data-stu-id="ac165-135">System.String</span></span>

## <span data-ttu-id="ac165-136">輸出</span><span class="sxs-lookup"><span data-stu-id="ac165-136">OUTPUTS</span></span>

### <span data-ttu-id="ac165-137">System.Object</span><span class="sxs-lookup"><span data-stu-id="ac165-137">System.Object</span></span>

## <span data-ttu-id="ac165-138">注意</span><span class="sxs-lookup"><span data-stu-id="ac165-138">NOTES</span></span>

## <span data-ttu-id="ac165-139">相關連結</span><span class="sxs-lookup"><span data-stu-id="ac165-139">RELATED LINKS</span></span>

[<span data-ttu-id="ac165-140">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="ac165-140">New-ScriptFileInfo</span></span>](New-ScriptFileInfo.md)

[<span data-ttu-id="ac165-141">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="ac165-141">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="ac165-142">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="ac165-142">Update-ScriptFileInfo</span></span>](Update-ScriptFileInfo.md)
