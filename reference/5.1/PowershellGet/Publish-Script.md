---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/publish-script?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Publish-Script
ms.openlocfilehash: 6593148b493f15feb47af886681032aaf5d009e7
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891085"
---
# <span data-ttu-id="c539d-103">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="c539d-103">Publish-Script</span></span>

## <span data-ttu-id="c539d-104">概要</span><span class="sxs-lookup"><span data-stu-id="c539d-104">SYNOPSIS</span></span>
<span data-ttu-id="c539d-105">發佈腳本。</span><span class="sxs-lookup"><span data-stu-id="c539d-105">Publishes a script.</span></span>

## <span data-ttu-id="c539d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c539d-106">SYNTAX</span></span>

### <span data-ttu-id="c539d-107">PathParameterSet (預設) </span><span class="sxs-lookup"><span data-stu-id="c539d-107">PathParameterSet (Default)</span></span>

```
Publish-Script -Path <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="c539d-108">LiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="c539d-108">LiteralPathParameterSet</span></span>

```
Publish-Script -LiteralPath <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="c539d-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="c539d-109">DESCRIPTION</span></span>

<span data-ttu-id="c539d-110">Cmdlet 會將 `Publish-Script` 指定的腳本發佈至線上元件庫。</span><span class="sxs-lookup"><span data-stu-id="c539d-110">The `Publish-Script` cmdlet publishes the specified script to the online gallery.</span></span>

## <span data-ttu-id="c539d-111">範例</span><span class="sxs-lookup"><span data-stu-id="c539d-111">EXAMPLES</span></span>

### <span data-ttu-id="c539d-112">範例1：建立腳本檔案、將內容新增至檔案，並加以發佈</span><span class="sxs-lookup"><span data-stu-id="c539d-112">Example 1: Create a script file, add content to it, and publish it</span></span>

<span data-ttu-id="c539d-113">`New-ScriptFileInfo`Cmdlet 會建立名為的腳本檔案 `Demo-Script.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="c539d-113">The `New-ScriptFileInfo` cmdlet creates a script file named `Demo-Script.ps1`.</span></span> <span data-ttu-id="c539d-114">`Get-Content` 顯示的內容 `Demo-Script.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="c539d-114">`Get-Content` displays the content of `Demo-Script.ps1`.</span></span> <span data-ttu-id="c539d-115">Cmdlet 會將函式 `Add-Content` 和工作流程加入至 `Demo-Script.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="c539d-115">The `Add-Content` cmdlet adds a function and a workflow to `Demo-Script.ps1`.</span></span>

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

<span data-ttu-id="c539d-116">`Test-ScriptFileInfo`Cmdlet 會驗證 `Demo-Script.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="c539d-116">The `Test-ScriptFileInfo` cmdlet validates `Demo-Script.ps1`.</span></span> <span data-ttu-id="c539d-117">Cmdlet 會將 `Publish-Script` 腳本發佈至 **LocalRepo1** 存放庫。</span><span class="sxs-lookup"><span data-stu-id="c539d-117">The `Publish-Script` cmdlet publishes the script to the **LocalRepo1** repository.</span></span> <span data-ttu-id="c539d-118">最後，</span><span class="sxs-lookup"><span data-stu-id="c539d-118">Finally.</span></span> <span data-ttu-id="c539d-119">`Find-Script` 用來 `Demo-Script.ps1` 在 **LocalRepo1** 儲存機制中搜尋。</span><span class="sxs-lookup"><span data-stu-id="c539d-119">`Find-Script` is used to search for `Demo-Script.ps1` in the **LocalRepo1** repository.</span></span>

## <span data-ttu-id="c539d-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c539d-120">PARAMETERS</span></span>

### <span data-ttu-id="c539d-121">-Credential</span><span class="sxs-lookup"><span data-stu-id="c539d-121">-Credential</span></span>

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

### <span data-ttu-id="c539d-122">-Force</span><span class="sxs-lookup"><span data-stu-id="c539d-122">-Force</span></span>

<span data-ttu-id="c539d-123">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="c539d-123">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="c539d-124">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c539d-124">-LiteralPath</span></span>

<span data-ttu-id="c539d-125">指定一個或多個位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="c539d-125">Specifies a path to one or more locations.</span></span> <span data-ttu-id="c539d-126">與 **Path** 參數不同， **LiteralPath** 參數的值會完全依照輸入的方式使用。</span><span class="sxs-lookup"><span data-stu-id="c539d-126">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as entered.</span></span> <span data-ttu-id="c539d-127">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="c539d-127">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="c539d-128">如果路徑包含 escape 字元，請用單引號括住。</span><span class="sxs-lookup"><span data-stu-id="c539d-128">If the path includes escape characters, enclose them in single quotation marks.</span></span> <span data-ttu-id="c539d-129">單引號告知 Windows PowerShell 不要將任何字元視為逸出序列。</span><span class="sxs-lookup"><span data-stu-id="c539d-129">Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="c539d-130">-NuGetApiKey</span><span class="sxs-lookup"><span data-stu-id="c539d-130">-NuGetApiKey</span></span>

<span data-ttu-id="c539d-131">指定您想要用來將腳本發行至線上元件庫的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="c539d-131">Specifies the API key that you want to use to publish a script to the online gallery.</span></span> <span data-ttu-id="c539d-132">API 金鑰是線上元件庫中設定檔的一部分。</span><span class="sxs-lookup"><span data-stu-id="c539d-132">The API key is part of your profile in the online gallery.</span></span> <span data-ttu-id="c539d-133">如需詳細資訊，請參閱 [管理 API 金鑰](/powershell/scripting/gallery/how-to/managing-profile/creating-apikeys)。</span><span class="sxs-lookup"><span data-stu-id="c539d-133">For more information see [Managing API keys](/powershell/scripting/gallery/how-to/managing-profile/creating-apikeys).</span></span>

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

### <span data-ttu-id="c539d-134">-Path</span><span class="sxs-lookup"><span data-stu-id="c539d-134">-Path</span></span>

<span data-ttu-id="c539d-135">指定一個或多個位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="c539d-135">Specifies a path to one or more locations.</span></span> <span data-ttu-id="c539d-136">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="c539d-136">Wildcards are permitted.</span></span> <span data-ttu-id="c539d-137">預設位置是目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="c539d-137">The default location is the current directory.</span></span>

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

### <span data-ttu-id="c539d-138">-Repository</span><span class="sxs-lookup"><span data-stu-id="c539d-138">-Repository</span></span>

<span data-ttu-id="c539d-139">指定由執行註冊之存放庫的易記名稱 `Register-PSRepository` 。</span><span class="sxs-lookup"><span data-stu-id="c539d-139">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span>

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

### <span data-ttu-id="c539d-140">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c539d-140">-Confirm</span></span>

<span data-ttu-id="c539d-141">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="c539d-141">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="c539d-142">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c539d-142">-WhatIf</span></span>

<span data-ttu-id="c539d-143">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="c539d-143">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="c539d-144">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="c539d-144">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="c539d-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c539d-145">CommonParameters</span></span>

<span data-ttu-id="c539d-146">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="c539d-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c539d-147">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="c539d-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c539d-148">輸入</span><span class="sxs-lookup"><span data-stu-id="c539d-148">INPUTS</span></span>

### <span data-ttu-id="c539d-149">System.String</span><span class="sxs-lookup"><span data-stu-id="c539d-149">System.String</span></span>

### <span data-ttu-id="c539d-150">System.Management.Automation.PSCredential</span><span class="sxs-lookup"><span data-stu-id="c539d-150">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="c539d-151">輸出</span><span class="sxs-lookup"><span data-stu-id="c539d-151">OUTPUTS</span></span>

### <span data-ttu-id="c539d-152">System.Object</span><span class="sxs-lookup"><span data-stu-id="c539d-152">System.Object</span></span>

## <span data-ttu-id="c539d-153">注意</span><span class="sxs-lookup"><span data-stu-id="c539d-153">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c539d-154">從2020年4月起，PowerShell 資源庫不再支援傳輸層安全性 (TLS) 1.0 和1.1 版。</span><span class="sxs-lookup"><span data-stu-id="c539d-154">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="c539d-155">如果您不是使用 TLS 1.2 或更高版本，當您嘗試存取 PowerShell 資源庫時，將會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="c539d-155">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="c539d-156">使用下列命令，以確保您使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="c539d-156">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="c539d-157">如需詳細資訊，請參閱 PowerShell blog 中的 [公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 。</span><span class="sxs-lookup"><span data-stu-id="c539d-157">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="c539d-158">相關連結</span><span class="sxs-lookup"><span data-stu-id="c539d-158">RELATED LINKS</span></span>

[<span data-ttu-id="c539d-159">Find-Script</span><span class="sxs-lookup"><span data-stu-id="c539d-159">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="c539d-160">Install-Script</span><span class="sxs-lookup"><span data-stu-id="c539d-160">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="c539d-161">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="c539d-161">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="c539d-162">Save-Script</span><span class="sxs-lookup"><span data-stu-id="c539d-162">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="c539d-163">Update-Script</span><span class="sxs-lookup"><span data-stu-id="c539d-163">Update-Script</span></span>](Update-Script.md)
