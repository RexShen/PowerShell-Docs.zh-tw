---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/02/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/save-script?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Script
ms.openlocfilehash: a6dcc87b00be1fb71acff60b3cf2cae9d73179da
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204244"
---
# <span data-ttu-id="12e6c-103">Save-Script</span><span class="sxs-lookup"><span data-stu-id="12e6c-103">Save-Script</span></span>

## <span data-ttu-id="12e6c-104">概要</span><span class="sxs-lookup"><span data-stu-id="12e6c-104">SYNOPSIS</span></span>
<span data-ttu-id="12e6c-105">儲存腳本。</span><span class="sxs-lookup"><span data-stu-id="12e6c-105">Saves a script.</span></span>

## <span data-ttu-id="12e6c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="12e6c-106">SYNTAX</span></span>

### <span data-ttu-id="12e6c-107">NameAndPathParameterSet (預設) </span><span class="sxs-lookup"><span data-stu-id="12e6c-107">NameAndPathParameterSet (Default)</span></span>

```
Save-Script [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="12e6c-108">NameAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="12e6c-108">NameAndLiteralPathParameterSet</span></span>

```
Save-Script [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="12e6c-109">InputObjectAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="12e6c-109">InputObjectAndLiteralPathParameterSet</span></span>

```
Save-Script [-InputObject] <PSObject[]> -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="12e6c-110">InputObjectAndPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="12e6c-110">InputObjectAndPathParameterSet</span></span>

```
Save-Script [-InputObject] <PSObject[]> [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="12e6c-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="12e6c-111">DESCRIPTION</span></span>

<span data-ttu-id="12e6c-112">Cmdlet 會儲存 `Save-Script` 指定的腳本。</span><span class="sxs-lookup"><span data-stu-id="12e6c-112">The `Save-Script` cmdlet saves the specified script.</span></span>

## <span data-ttu-id="12e6c-113">範例</span><span class="sxs-lookup"><span data-stu-id="12e6c-113">EXAMPLES</span></span>

### <span data-ttu-id="12e6c-114">範例1：儲存腳本並驗證腳本的中繼資料</span><span class="sxs-lookup"><span data-stu-id="12e6c-114">Example 1: Save a script and validate the script's metadata</span></span>

<span data-ttu-id="12e6c-115">在此範例中，存放庫中的腳本會儲存至本機電腦，並驗證腳本的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="12e6c-115">In this example, a script from a repository is saved to the local computer and the script's metadata is validated.</span></span>

```powershell
Save-Script -Name Install-VSCode -Repository PSGallery -Path C:\Test\Scripts
Test-ScriptFileInfo -Path C:\Test\Scripts\Install-VSCode.ps1
```

```Output
Version   Name              Author      Description
-------   ----              ------      -----------
1.3       Install-VSCode    Microsoft   This script can be used to easily install Visual Studio Code
```

<span data-ttu-id="12e6c-116">`Save-Script` 使用 **Name** 參數來指定腳本的名稱。</span><span class="sxs-lookup"><span data-stu-id="12e6c-116">`Save-Script` uses the **Name** parameter to specify the script's name.</span></span> <span data-ttu-id="12e6c-117">存放 **庫** 參數指定要在哪裡尋找腳本。</span><span class="sxs-lookup"><span data-stu-id="12e6c-117">The **Repository** parameter specifies where to find the script.</span></span> <span data-ttu-id="12e6c-118">腳本會儲存在 **Path** 參數所指定的位置。</span><span class="sxs-lookup"><span data-stu-id="12e6c-118">The script is saved in the location specified by the **Path** parameter.</span></span> <span data-ttu-id="12e6c-119">`Test-ScriptFileInfo` 指定 **路徑** 並驗證腳本的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="12e6c-119">`Test-ScriptFileInfo` specifies the **Path** and validates the script's metadata.</span></span>

## <span data-ttu-id="12e6c-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="12e6c-120">PARAMETERS</span></span>

### <span data-ttu-id="12e6c-121">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="12e6c-121">-AcceptLicense</span></span>

<span data-ttu-id="12e6c-122">如果腳本需要，則自動接受授權合約。</span><span class="sxs-lookup"><span data-stu-id="12e6c-122">Automatically accept the license agreement if the script requires it.</span></span>

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

### <span data-ttu-id="12e6c-123">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="12e6c-123">-AllowPrerelease</span></span>

<span data-ttu-id="12e6c-124">允許您儲存標記為發行前版本的腳本。</span><span class="sxs-lookup"><span data-stu-id="12e6c-124">Allows you to save a script marked as a prerelease.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12e6c-125">-Confirm</span><span class="sxs-lookup"><span data-stu-id="12e6c-125">-Confirm</span></span>

<span data-ttu-id="12e6c-126">在執行之前提示您確認 `Save-Script` 。</span><span class="sxs-lookup"><span data-stu-id="12e6c-126">Prompts you for confirmation before running `Save-Script`.</span></span>

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

### <span data-ttu-id="12e6c-127">-Credential</span><span class="sxs-lookup"><span data-stu-id="12e6c-127">-Credential</span></span>

<span data-ttu-id="12e6c-128">指定有權儲存腳本的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="12e6c-128">Specifies a user account that has permission to save a script.</span></span>

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

### <span data-ttu-id="12e6c-129">-Force</span><span class="sxs-lookup"><span data-stu-id="12e6c-129">-Force</span></span>

<span data-ttu-id="12e6c-130">強制 `Save-Script` 執行而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="12e6c-130">Forces `Save-Script` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="12e6c-131">-InputObject</span><span class="sxs-lookup"><span data-stu-id="12e6c-131">-InputObject</span></span>

<span data-ttu-id="12e6c-132">接受 **PSRepositoryItemInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="12e6c-132">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="12e6c-133">例如，輸出 `Find-Script` 到變數，並使用該變數作為 **InputObject** 引數。</span><span class="sxs-lookup"><span data-stu-id="12e6c-133">For example, output `Find-Script` to a variable and use that variable as the **InputObject** argument.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObjectAndLiteralPathParameterSet, InputObjectAndPathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="12e6c-134">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="12e6c-134">-LiteralPath</span></span>

<span data-ttu-id="12e6c-135">指定一個或多個位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="12e6c-135">Specifies a path to one or more locations.</span></span> <span data-ttu-id="12e6c-136">**LiteralPath** 參數的值會完全依照輸入的方式使用。</span><span class="sxs-lookup"><span data-stu-id="12e6c-136">The value of the **LiteralPath** parameter is used exactly as entered.</span></span> <span data-ttu-id="12e6c-137">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="12e6c-137">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="12e6c-138">如果路徑包含 escape 字元，請將路徑括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="12e6c-138">If the path includes escape characters, enclose the path within single quotation marks.</span></span> <span data-ttu-id="12e6c-139">PowerShell 不會將以單引號括住的任何字元視為 escape 序列來解讀。</span><span class="sxs-lookup"><span data-stu-id="12e6c-139">PowerShell doesn't interpret any characters enclosed in single quotation marks as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndLiteralPathParameterSet, InputObjectAndLiteralPathParameterSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="12e6c-140">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="12e6c-140">-MaximumVersion</span></span>

<span data-ttu-id="12e6c-141">指定要儲存之腳本的最大值或最新版本。</span><span class="sxs-lookup"><span data-stu-id="12e6c-141">Specifies the maximum, or newest version of the script to save.</span></span> <span data-ttu-id="12e6c-142">在相同的命令中不能使用 **MaximumVersion** 和 **RequiredVersion** 參數。</span><span class="sxs-lookup"><span data-stu-id="12e6c-142">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="12e6c-143">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="12e6c-143">-MinimumVersion</span></span>

<span data-ttu-id="12e6c-144">指定要儲存之腳本的最小版本。</span><span class="sxs-lookup"><span data-stu-id="12e6c-144">Specifies the minimum version of a script to save.</span></span> <span data-ttu-id="12e6c-145">**MinimumVersion** 和 **RequiredVersion** 參數無法在相同的命令中使用。</span><span class="sxs-lookup"><span data-stu-id="12e6c-145">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="12e6c-146">-Name</span><span class="sxs-lookup"><span data-stu-id="12e6c-146">-Name</span></span>

<span data-ttu-id="12e6c-147">指定要儲存之腳本名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="12e6c-147">Specifies an array of script names to save.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="12e6c-148">-Path</span><span class="sxs-lookup"><span data-stu-id="12e6c-148">-Path</span></span>

<span data-ttu-id="12e6c-149">指定本機電腦上儲存已儲存模組的位置。</span><span class="sxs-lookup"><span data-stu-id="12e6c-149">Specifies the location on the local computer to store a saved module.</span></span> <span data-ttu-id="12e6c-150">接受萬用字元。</span><span class="sxs-lookup"><span data-stu-id="12e6c-150">Accepts wildcard characters.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, InputObjectAndPathParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="12e6c-151">-Proxy</span><span class="sxs-lookup"><span data-stu-id="12e6c-151">-Proxy</span></span>

<span data-ttu-id="12e6c-152">指定要求的 proxy 伺服器，而不是直接連接到網際網路資源。</span><span class="sxs-lookup"><span data-stu-id="12e6c-152">Specifies a proxy server for the request, rather than connecting directly to an internet resource.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="12e6c-153">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="12e6c-153">-ProxyCredential</span></span>

<span data-ttu-id="12e6c-154">指定擁有使用 **proxy** 參數所指定 proxy 伺服器之許可權的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="12e6c-154">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="12e6c-155">-Repository</span><span class="sxs-lookup"><span data-stu-id="12e6c-155">-Repository</span></span>

<span data-ttu-id="12e6c-156">指定由執行註冊之存放庫的易記名稱 `Register-PSRepository` 。</span><span class="sxs-lookup"><span data-stu-id="12e6c-156">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span> <span data-ttu-id="12e6c-157">用 `Get-PSRepository` 來顯示已註冊的存放庫。</span><span class="sxs-lookup"><span data-stu-id="12e6c-157">Use `Get-PSRepository` to display registered repositories.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="12e6c-158">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="12e6c-158">-RequiredVersion</span></span>

<span data-ttu-id="12e6c-159">指定要儲存之腳本的確切版本號碼。</span><span class="sxs-lookup"><span data-stu-id="12e6c-159">Specifies the exact version number of the script to save.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="12e6c-160">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="12e6c-160">-WhatIf</span></span>

<span data-ttu-id="12e6c-161">顯示執行時所發生 `Save-Script` 的情況。</span><span class="sxs-lookup"><span data-stu-id="12e6c-161">Shows what would happen if `Save-Script` runs.</span></span> <span data-ttu-id="12e6c-162">不會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="12e6c-162">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="12e6c-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="12e6c-163">CommonParameters</span></span>

<span data-ttu-id="12e6c-164">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="12e6c-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="12e6c-165">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="12e6c-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="12e6c-166">輸入</span><span class="sxs-lookup"><span data-stu-id="12e6c-166">INPUTS</span></span>

### <span data-ttu-id="12e6c-167">System.String[]</span><span class="sxs-lookup"><span data-stu-id="12e6c-167">System.String[]</span></span>

### <span data-ttu-id="12e6c-168">管理. PSObject []</span><span class="sxs-lookup"><span data-stu-id="12e6c-168">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="12e6c-169">System.String</span><span class="sxs-lookup"><span data-stu-id="12e6c-169">System.String</span></span>

### <span data-ttu-id="12e6c-170">System.Uri</span><span class="sxs-lookup"><span data-stu-id="12e6c-170">System.Uri</span></span>

### <span data-ttu-id="12e6c-171">System.Management.Automation.PSCredential</span><span class="sxs-lookup"><span data-stu-id="12e6c-171">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="12e6c-172">輸出</span><span class="sxs-lookup"><span data-stu-id="12e6c-172">OUTPUTS</span></span>

### <span data-ttu-id="12e6c-173">System.Object</span><span class="sxs-lookup"><span data-stu-id="12e6c-173">System.Object</span></span>

## <span data-ttu-id="12e6c-174">注意</span><span class="sxs-lookup"><span data-stu-id="12e6c-174">NOTES</span></span>

## <span data-ttu-id="12e6c-175">相關連結</span><span class="sxs-lookup"><span data-stu-id="12e6c-175">RELATED LINKS</span></span>

[<span data-ttu-id="12e6c-176">Find-Script</span><span class="sxs-lookup"><span data-stu-id="12e6c-176">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="12e6c-177">Install-Script</span><span class="sxs-lookup"><span data-stu-id="12e6c-177">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="12e6c-178">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="12e6c-178">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="12e6c-179">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="12e6c-179">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)

[<span data-ttu-id="12e6c-180">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="12e6c-180">Uninstall-Script</span></span>](Uninstall-Script.md)

[<span data-ttu-id="12e6c-181">Update-Script</span><span class="sxs-lookup"><span data-stu-id="12e6c-181">Update-Script</span></span>](Update-Script.md)