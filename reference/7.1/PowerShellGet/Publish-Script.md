---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/publish-script?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Publish-Script
ms.openlocfilehash: 1c333494525ed697ad04f6b500cabfb5964ec9eb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205060"
---
# <span data-ttu-id="f7863-103">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="f7863-103">Publish-Script</span></span>

## <span data-ttu-id="f7863-104">概要</span><span class="sxs-lookup"><span data-stu-id="f7863-104">SYNOPSIS</span></span>
<span data-ttu-id="f7863-105">發佈腳本。</span><span class="sxs-lookup"><span data-stu-id="f7863-105">Publishes a script.</span></span>

## <span data-ttu-id="f7863-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f7863-106">SYNTAX</span></span>

### <span data-ttu-id="f7863-107">PathParameterSet (預設) </span><span class="sxs-lookup"><span data-stu-id="f7863-107">PathParameterSet (Default)</span></span>

```
Publish-Script -Path <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f7863-108">LiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="f7863-108">LiteralPathParameterSet</span></span>

```
Publish-Script -LiteralPath <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f7863-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f7863-109">DESCRIPTION</span></span>

<span data-ttu-id="f7863-110">Cmdlet 會將 `Publish-Script` 指定的腳本發佈至線上元件庫。</span><span class="sxs-lookup"><span data-stu-id="f7863-110">The `Publish-Script` cmdlet publishes the specified script to the online gallery.</span></span>

## <span data-ttu-id="f7863-111">範例</span><span class="sxs-lookup"><span data-stu-id="f7863-111">EXAMPLES</span></span>

### <span data-ttu-id="f7863-112">範例1：建立腳本檔案、將內容新增至檔案，並加以發佈</span><span class="sxs-lookup"><span data-stu-id="f7863-112">Example 1: Create a script file, add content to it, and publish it</span></span>

<span data-ttu-id="f7863-113">`New-ScriptFileInfo`Cmdlet 會建立名為的腳本檔案 `Demo-Script.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="f7863-113">The `New-ScriptFileInfo` cmdlet creates a script file named `Demo-Script.ps1`.</span></span> <span data-ttu-id="f7863-114">`Get-Content` 顯示的內容 `Demo-Script.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="f7863-114">`Get-Content` displays the content of `Demo-Script.ps1`.</span></span> <span data-ttu-id="f7863-115">Cmdlet 會將函式 `Add-Content` 和工作流程加入至 `Demo-Script.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="f7863-115">The `Add-Content` cmdlet adds a function and a workflow to `Demo-Script.ps1`.</span></span>

```powershell
$newScriptInfo = @{
  Path = 'D:\ScriptSharingDemo\Demo-Script.ps1'
  Version = '1.0'
  Author = 'author@contoso.com'
  Description = "my test script file description goes here"
}
New-ScriptFileInfo @newScriptInfo
Get-Content -Path $newScriptInfo.Path
```

```Output
<#PSScriptInfo

.VERSION 1.0

.AUTHOR pattif@microsoft.com

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
#>

<#
.DESCRIPTION
 my test script file description goes here
#>
Param()
```

```powershell
Add-Content -Path D:\ScriptSharingDemo\Demo-Script.ps1 -Value @"

Function Demo-ScriptFunction { 'Demo-ScriptFunction' }

Workflow Demo-ScriptWorkflow { 'Demo-ScriptWorkflow' }

Demo-ScriptFunction
Demo-ScriptWorkflow
"@
Test-ScriptFileInfo -Path D:\ScriptSharingDemo\Demo-Script.ps1
```

```Output
Version    Name                 Author                   Description
-------    ----                 ------                   -----------
1.0        Demo-Script          author@contoso.com       my test script file description goes here
```

```powershell
Publish-Script -Path D:\ScriptSharingDemo\Demo-Script.ps1 -Repository LocalRepo1
Find-Script -Repository LocalRepo1 -Name "Demo-Script"
```

```Output
Version    Name                 Type       Repository    Description
-------    ----                 ----       ----------    -----------
1.0        Demo-Script          Script     LocalRepo1    my test script file description goes here
```

<span data-ttu-id="f7863-116">`Test-ScriptFileInfo`Cmdlet 會驗證 `Demo-Script.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="f7863-116">The `Test-ScriptFileInfo` cmdlet validates `Demo-Script.ps1`.</span></span> <span data-ttu-id="f7863-117">Cmdlet 會將 `Publish-Script` 腳本發佈至 **LocalRepo1** 存放庫。</span><span class="sxs-lookup"><span data-stu-id="f7863-117">The `Publish-Script` cmdlet publishes the script to the **LocalRepo1** repository.</span></span> <span data-ttu-id="f7863-118">最後，</span><span class="sxs-lookup"><span data-stu-id="f7863-118">Finally.</span></span> <span data-ttu-id="f7863-119">`Find-Script` 用來 `Demo-Script.ps1` 在 **LocalRepo1** 儲存機制中搜尋。</span><span class="sxs-lookup"><span data-stu-id="f7863-119">`Find-Script` is used to search for `Demo-Script.ps1` in the **LocalRepo1** repository.</span></span>

## <span data-ttu-id="f7863-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f7863-120">PARAMETERS</span></span>

### <span data-ttu-id="f7863-121">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f7863-121">-Confirm</span></span>

<span data-ttu-id="f7863-122">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="f7863-122">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f7863-123">-Credential</span><span class="sxs-lookup"><span data-stu-id="f7863-123">-Credential</span></span>

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

### <span data-ttu-id="f7863-124">-Force</span><span class="sxs-lookup"><span data-stu-id="f7863-124">-Force</span></span>

<span data-ttu-id="f7863-125">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="f7863-125">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="f7863-126">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="f7863-126">-LiteralPath</span></span>

<span data-ttu-id="f7863-127">指定一個或多個位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="f7863-127">Specifies a path to one or more locations.</span></span> <span data-ttu-id="f7863-128">與 **Path** 參數不同， **LiteralPath** 參數的值會完全依照輸入的方式使用。</span><span class="sxs-lookup"><span data-stu-id="f7863-128">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as entered.</span></span> <span data-ttu-id="f7863-129">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="f7863-129">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="f7863-130">如果路徑包含 escape 字元，請用單引號括住。</span><span class="sxs-lookup"><span data-stu-id="f7863-130">If the path includes escape characters, enclose them in single quotation marks.</span></span> <span data-ttu-id="f7863-131">單引號告知 Windows PowerShell 不要將任何字元視為逸出序列。</span><span class="sxs-lookup"><span data-stu-id="f7863-131">Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="f7863-132">-NuGetApiKey</span><span class="sxs-lookup"><span data-stu-id="f7863-132">-NuGetApiKey</span></span>

<span data-ttu-id="f7863-133">指定您想要用來將腳本發行至線上元件庫的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="f7863-133">Specifies the API key that you want to use to publish a script to the online gallery.</span></span> <span data-ttu-id="f7863-134">API 金鑰是線上元件庫中設定檔的一部分。</span><span class="sxs-lookup"><span data-stu-id="f7863-134">The API key is part of your profile in the online gallery.</span></span> <span data-ttu-id="f7863-135">如需詳細資訊，請參閱 [管理 API 金鑰](/powershell/scripting/gallery/how-to/managing-profile/creating-apikeys)。</span><span class="sxs-lookup"><span data-stu-id="f7863-135">For more information see [Managing API keys](/powershell/scripting/gallery/how-to/managing-profile/creating-apikeys).</span></span>

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

### <span data-ttu-id="f7863-136">-Path</span><span class="sxs-lookup"><span data-stu-id="f7863-136">-Path</span></span>

<span data-ttu-id="f7863-137">指定一個或多個位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="f7863-137">Specifies a path to one or more locations.</span></span> <span data-ttu-id="f7863-138">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="f7863-138">Wildcards are permitted.</span></span> <span data-ttu-id="f7863-139">預設位置是目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="f7863-139">The default location is the current directory.</span></span>

```yaml
Type: System.String
Parameter Sets: PathParameterSet
Aliases:

Required: True
Position: Named
Default value: <Current location>
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="f7863-140">-Repository</span><span class="sxs-lookup"><span data-stu-id="f7863-140">-Repository</span></span>

<span data-ttu-id="f7863-141">指定由執行註冊之存放庫的易記名稱 `Register-PSRepository` 。</span><span class="sxs-lookup"><span data-stu-id="f7863-141">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span>

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

### <span data-ttu-id="f7863-142">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f7863-142">-WhatIf</span></span>

<span data-ttu-id="f7863-143">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="f7863-143">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="f7863-144">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="f7863-144">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f7863-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f7863-145">CommonParameters</span></span>

<span data-ttu-id="f7863-146">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="f7863-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f7863-147">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="f7863-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f7863-148">輸入</span><span class="sxs-lookup"><span data-stu-id="f7863-148">INPUTS</span></span>

### <span data-ttu-id="f7863-149">System.String</span><span class="sxs-lookup"><span data-stu-id="f7863-149">System.String</span></span>

### <span data-ttu-id="f7863-150">System.Management.Automation.PSCredential</span><span class="sxs-lookup"><span data-stu-id="f7863-150">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="f7863-151">輸出</span><span class="sxs-lookup"><span data-stu-id="f7863-151">OUTPUTS</span></span>

### <span data-ttu-id="f7863-152">System.Object</span><span class="sxs-lookup"><span data-stu-id="f7863-152">System.Object</span></span>

## <span data-ttu-id="f7863-153">注意</span><span class="sxs-lookup"><span data-stu-id="f7863-153">NOTES</span></span>

## <span data-ttu-id="f7863-154">相關連結</span><span class="sxs-lookup"><span data-stu-id="f7863-154">RELATED LINKS</span></span>

[<span data-ttu-id="f7863-155">Find-Script</span><span class="sxs-lookup"><span data-stu-id="f7863-155">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="f7863-156">Install-Script</span><span class="sxs-lookup"><span data-stu-id="f7863-156">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="f7863-157">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="f7863-157">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="f7863-158">Save-Script</span><span class="sxs-lookup"><span data-stu-id="f7863-158">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="f7863-159">Update-Script</span><span class="sxs-lookup"><span data-stu-id="f7863-159">Update-Script</span></span>](Update-Script.md)

