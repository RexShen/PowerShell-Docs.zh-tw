---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/find-script?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Script
ms.openlocfilehash: 6eb617987b437337dc3c42c33f55033b64ec8a79
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201411"
---
# <span data-ttu-id="d8311-103">Find-Script</span><span class="sxs-lookup"><span data-stu-id="d8311-103">Find-Script</span></span>

## <span data-ttu-id="d8311-104">概要</span><span class="sxs-lookup"><span data-stu-id="d8311-104">SYNOPSIS</span></span>
<span data-ttu-id="d8311-105">尋找腳本。</span><span class="sxs-lookup"><span data-stu-id="d8311-105">Finds a script.</span></span>

## <span data-ttu-id="d8311-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d8311-106">SYNTAX</span></span>

```
Find-Script [[-Name] <String[]>] [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-AllVersions] [-IncludeDependencies] [-Filter <String>] [-Tag <String[]>]
 [-Includes <String[]>] [-Command <String[]>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Repository <String[]>] [-Credential <PSCredential>] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="d8311-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="d8311-107">DESCRIPTION</span></span>

<span data-ttu-id="d8311-108">**Find 腳本** Cmdlet 會在已註冊的存放庫中尋找指定的腳本。</span><span class="sxs-lookup"><span data-stu-id="d8311-108">The **Find-Script** cmdlet finds a specified script in registered repositories.</span></span>

## <span data-ttu-id="d8311-109">範例</span><span class="sxs-lookup"><span data-stu-id="d8311-109">EXAMPLES</span></span>

### <span data-ttu-id="d8311-110">範例1：尋找所有可用的腳本</span><span class="sxs-lookup"><span data-stu-id="d8311-110">Example 1: Find all available scripts</span></span>

```
PS C:\> Find-Script
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Fabrikam-ClientScript               Script     LocalRepo1           Description for the Fabrikam-ClientScript script
2.5        Fabrikam-Script                     Script     LocalRepo1           Description for the Fabrikam-Script script
2.5        Fabrikam-ServerScript               Script     LocalRepo1           Description for the Fabrikam-ServerScript script
2.5        Required-Script1                    Script     LocalRepo1           Description for the Required-Script1 script
2.5        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
2.5        Required-Script3                    Script     LocalRepo1           Description for the Required-Script3 script
2.0        Script-WithDependencies1            Script     LocalRepo1           Description for the Script-WithDependencies1 script
2.0        Script-WithDependencies2            Script     LocalRepo1           Description for the Script-WithDependencies2 script
2.0        Start-WFContosoServer               Script     LocalRepo1           Start-WFContosoServer Script example
2.1        Test-Script1                        Script     LocalRepo1           Test-Script1 Script example
2.0        Test-Script2                        Script     LocalRepo1           Test-Script2 Script example
1.0        TestRunbook                         Script     LocalRepo1           Contoso Script example
```

<span data-ttu-id="d8311-111">此命令會尋找所有可用的腳本。</span><span class="sxs-lookup"><span data-stu-id="d8311-111">This command finds all available scripts.</span></span>

### <span data-ttu-id="d8311-112">範例2：依名稱尋找腳本</span><span class="sxs-lookup"><span data-stu-id="d8311-112">Example 2: Find a script by name</span></span>

```
PS C:\> Find-Script -Name "Start-WFContosoServer"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.0        Start-WFContosoServer               Script     LocalRepo1           Start-WFContosoServer Script example
```

<span data-ttu-id="d8311-113">此命令會尋找名為 WFContosoServer 的腳本。</span><span class="sxs-lookup"><span data-stu-id="d8311-113">This command find the script named Start-WFContosoServer.</span></span>

### <span data-ttu-id="d8311-114">範例3：依名稱、所需的版本，以及從指定的存放庫尋找腳本</span><span class="sxs-lookup"><span data-stu-id="d8311-114">Example 3: Find a script by name, required version, and from a specified repository</span></span>

```
PS C:\> Find-Script -Name "Required-Script2" -RequiredVersion 2.0 -Repository "LocalRepo01"
```

<span data-ttu-id="d8311-115">此命令會依名稱尋找腳本，並在 LocalRepo01 儲存機制中尋找所需的版本。</span><span class="sxs-lookup"><span data-stu-id="d8311-115">This command finds a script by name and required version in the LocalRepo01 repository.</span></span>

### <span data-ttu-id="d8311-116">範例4：尋找腳本並將輸出格式化為清單</span><span class="sxs-lookup"><span data-stu-id="d8311-116">Example 4: Find a script and format the output as a list</span></span>

```
PS C:\> Find-Script -Name "Required-Script2" -RequiredVersion 2.0 -Repository "LocalRepo1" | Format-List * -Force
Name                       : Required-Script2
Version                    : 2.0
Type                       : Script
Description                : Description for the Required-Script2 script
Author                     : pattif
CompanyName                : Microsoft Corporation
Copyright                  : 2015 Microsoft Corporation. All rights reserved.
PublishedDate              : 8/14/2015 2:37:01 PM
LicenseUri                 : http://required-script2.com/license
ProjectUri                 : http://required-script2.com/
IconUri                    : http://required-script2.com/icon
Tags                       : {, Tag1, Tag2, Tag-Required-Script2-2.0...}
Includes                   : {Function, DscResource, Cmdlet, Command}
PowerShellGetFormatVersion :
ReleaseNotes               : Required-Script2 release notes
Dependencies               : {}
RepositorySourceLocation   : C:\MyLocalRepo
Repository                 : LocalRepo01
PackageManagementProvider  : NuGet
```

<span data-ttu-id="d8311-117">此命令會在 LocalRepo1 儲存機制中尋找 Required-Script2，然後將產生的 **PSRepositoryItemInfo** 物件傳遞給 Format-List Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d8311-117">This command finds Required-Script2 in the LocalRepo1 repository, and then passes the resulting **PSRepositoryItemInfo** object to the Format-List cmdlet.</span></span>

### <span data-ttu-id="d8311-118">範例5：在指定的版本範圍中尋找腳本</span><span class="sxs-lookup"><span data-stu-id="d8311-118">Example 5: Find a script in the specified version range</span></span>

```
PS C:\> Find-Script -Name "Required-Script2" -MinimumVersion 2.1 -MaximumVersion 2.5 -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
```

<span data-ttu-id="d8311-119">此命令會在 LocalRepo1 存放庫中尋找2.1 和2.5 版之間的所有 RequiredScript2 版本。</span><span class="sxs-lookup"><span data-stu-id="d8311-119">This command finds all versions of RequiredScript2 between versions 2.1 and 2.5 in the LocalRepo1 respository.</span></span>

### <span data-ttu-id="d8311-120">範例6：尋找腳本的所有版本</span><span class="sxs-lookup"><span data-stu-id="d8311-120">Example 6: Find all versions of a script</span></span>

```
PS C:\> Find-Script -Name "Required-Script02" -AllVersions
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
1.5        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
2.0        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
2.5        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
```

<span data-ttu-id="d8311-121">此命令會尋找所需的所有版本-Script02。</span><span class="sxs-lookup"><span data-stu-id="d8311-121">This command finds all versions of Required-Script02.</span></span>

### <span data-ttu-id="d8311-122">範例7：尋找腳本和其相依性</span><span class="sxs-lookup"><span data-stu-id="d8311-122">Example 7: Find a script and its dependencies</span></span>

```
PS C:\> Find-Script -Name "Script-WithDependencies1" -IncludeDependencies -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        Script-WithDependencies1            Script     LocalRepo1           Description for the Script-WithDependencies1 script
2.0        RequiredModule3                     Script     LocalRepo1           RequiredModule3 module
2.5        Required-Script1                    Script     LocalRepo1           Description for the Required-Script1 script
2.5        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
```

<span data-ttu-id="d8311-123">此命令會尋找腳本及其相依性。</span><span class="sxs-lookup"><span data-stu-id="d8311-123">This command finds a script and its dependencies.</span></span>

### <span data-ttu-id="d8311-124">範例8：尋找具有指定標記的腳本</span><span class="sxs-lookup"><span data-stu-id="d8311-124">Example 8: Find scripts with the specified tag</span></span>

```
PS C:\> Find-Script -Tag "Tag1" -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        Fabrikam-ClientScript               Script     LocalRepo1           Description for the Fabrikam-ClientScript script
```

<span data-ttu-id="d8311-125">此命令會在 LocalRepo1 存放庫中尋找具有標記 Tag1 的腳本</span><span class="sxs-lookup"><span data-stu-id="d8311-125">This command finds scripts that have the tag Tag1 in the LocalRepo1 repository</span></span>

### <span data-ttu-id="d8311-126">範例9：尋找具有指定命令名稱的腳本</span><span class="sxs-lookup"><span data-stu-id="d8311-126">Example 9: Find scripts with specified command name</span></span>

```
PS C:\> Find-Script -Command Test-FunctionFromScript_Required-Script3 -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script3                    Script     LocalRepo1           Description for the Required-Script3 script
```

<span data-ttu-id="d8311-127">此命令會尋找包含指定命令名稱的腳本。</span><span class="sxs-lookup"><span data-stu-id="d8311-127">This command finds a script that contains the specified command name.</span></span>

### <span data-ttu-id="d8311-128">範例10：使用工作流程尋找腳本</span><span class="sxs-lookup"><span data-stu-id="d8311-128">Example 10: Find scripts with workflows</span></span>

```
PS C:\> Find-Script -Includes "Workflow" -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Fabrikam-ClientScript               Script     LocalRepo1           Description for the Fabrikam-ClientScript script
1.0        Fabrikam-Script                     Script     LocalRepo1           Description for the Fabrikam-Script script
```

<span data-ttu-id="d8311-129">此命令會尋找 LocalRepo1 存放庫中的工作流程腳本。</span><span class="sxs-lookup"><span data-stu-id="d8311-129">This command finds workflow scripts in the LocalRepo1 repository.</span></span>

### <span data-ttu-id="d8311-130">範例11：使用萬用字元尋找腳本</span><span class="sxs-lookup"><span data-stu-id="d8311-130">Example 11: Find scripts using wildcards</span></span>

```
PS C:\> Find-Script -Name "Required-Script*" -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script1                    Script     local1               Description for the Required-Script1 script
2.5        Required-Script2                    Script     local1               Description for the Required-Script2 script
2.5        Required-Script3                    Script     local1               Description for the Required-Script3 script
```

<span data-ttu-id="d8311-131">此命令會使用萬用字元 ( \* ) 來尋找以必要-Script 開頭的腳本。</span><span class="sxs-lookup"><span data-stu-id="d8311-131">This command uses the wildcard character (\*) to find scripts that begin with Required-Script.</span></span>

## <span data-ttu-id="d8311-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d8311-132">PARAMETERS</span></span>

### <span data-ttu-id="d8311-133">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="d8311-133">-AllowPrerelease</span></span>

<span data-ttu-id="d8311-134">包含在標記為發行前版本的結果腳本中。</span><span class="sxs-lookup"><span data-stu-id="d8311-134">Includes in the results scripts marked as a prerelease.</span></span>

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

### <span data-ttu-id="d8311-135">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="d8311-135">-AllVersions</span></span>

<span data-ttu-id="d8311-136">指出此作業會尋找所有的腳本版本。</span><span class="sxs-lookup"><span data-stu-id="d8311-136">Indicates that this operation finds all script versions.</span></span>

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

### <span data-ttu-id="d8311-137">-Command</span><span class="sxs-lookup"><span data-stu-id="d8311-137">-Command</span></span>

<span data-ttu-id="d8311-138">指定要在腳本中尋找的命令陣列。</span><span class="sxs-lookup"><span data-stu-id="d8311-138">Specifies an array of commands to find in scripts.</span></span>
<span data-ttu-id="d8311-139">命令可以是函數或工作流程。</span><span class="sxs-lookup"><span data-stu-id="d8311-139">A command can be a function or workflow.</span></span>

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

### <span data-ttu-id="d8311-140">-Credential</span><span class="sxs-lookup"><span data-stu-id="d8311-140">-Credential</span></span>

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

### <span data-ttu-id="d8311-141">-Filter</span><span class="sxs-lookup"><span data-stu-id="d8311-141">-Filter</span></span>

<span data-ttu-id="d8311-142">根據 PackageManagement 提供者特定的搜尋語法尋找腳本。</span><span class="sxs-lookup"><span data-stu-id="d8311-142">Finds scripts based on the PackageManagement provider-specific search syntax.</span></span>

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

### <span data-ttu-id="d8311-143">-Includedependencies 來</span><span class="sxs-lookup"><span data-stu-id="d8311-143">-IncludeDependencies</span></span>

<span data-ttu-id="d8311-144">指出此作業會取得相依于 *Name* 參數中指定之腳本的所有腳本。</span><span class="sxs-lookup"><span data-stu-id="d8311-144">Indicates that this operation gets all scripts that are dependent upon the script specified in the *Name* parameter.</span></span>

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

### <span data-ttu-id="d8311-145">-Include</span><span class="sxs-lookup"><span data-stu-id="d8311-145">-Includes</span></span>

<span data-ttu-id="d8311-146">指定要取得的腳本類型。</span><span class="sxs-lookup"><span data-stu-id="d8311-146">Specifies type of script to get.</span></span>
<span data-ttu-id="d8311-147">此參數可接受的值為： Function、Workflow。</span><span class="sxs-lookup"><span data-stu-id="d8311-147">The acceptable values for this parameter are: Function, Workflow.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Function, Workflow

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8311-148">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="d8311-148">-MaximumVersion</span></span>

<span data-ttu-id="d8311-149">指定要尋找之腳本的最大或最新版本。</span><span class="sxs-lookup"><span data-stu-id="d8311-149">Specifies the maximum, or newest, version of the script to find.</span></span>
<span data-ttu-id="d8311-150">*MaximumVersion* 和 *RequiredVersion* 參數是互斥的；您無法在相同的命令中使用這兩個參數。</span><span class="sxs-lookup"><span data-stu-id="d8311-150">The *MaximumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d8311-151">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="d8311-151">-MinimumVersion</span></span>

<span data-ttu-id="d8311-152">指定要尋找之腳本的最小版本。</span><span class="sxs-lookup"><span data-stu-id="d8311-152">Specifies the minimum version of the script to find.</span></span>
<span data-ttu-id="d8311-153">*MinimumVersion* 和 *RequiredVersion* 參數是互斥的；您無法在相同的命令中使用這兩個參數。</span><span class="sxs-lookup"><span data-stu-id="d8311-153">The *MinimumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d8311-154">-Name</span><span class="sxs-lookup"><span data-stu-id="d8311-154">-Name</span></span>

<span data-ttu-id="d8311-155">指定要尋找之腳本的名稱陣列。</span><span class="sxs-lookup"><span data-stu-id="d8311-155">Specifies an array of names of scripts to find.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="d8311-156">-Proxy</span><span class="sxs-lookup"><span data-stu-id="d8311-156">-Proxy</span></span>

<span data-ttu-id="d8311-157">指定要求的 proxy 伺服器，而不是直接連接到網際網路資源。</span><span class="sxs-lookup"><span data-stu-id="d8311-157">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="d8311-158">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="d8311-158">-ProxyCredential</span></span>

<span data-ttu-id="d8311-159">指定具有使用 **Proxy** 參數所指定 Proxy 伺服器之權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="d8311-159">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="d8311-160">-Repository</span><span class="sxs-lookup"><span data-stu-id="d8311-160">-Repository</span></span>

<span data-ttu-id="d8311-161">指定由執行 PSRepository 註冊之存放庫的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="d8311-161">Specifies the friendly name of a repository that has been registered by running Register-PSRepository.</span></span>

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

### <span data-ttu-id="d8311-162">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="d8311-162">-RequiredVersion</span></span>

<span data-ttu-id="d8311-163">指定要尋找之腳本的確切版本號碼。</span><span class="sxs-lookup"><span data-stu-id="d8311-163">Specifies the exact version number of the script to find.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d8311-164">-Tag</span><span class="sxs-lookup"><span data-stu-id="d8311-164">-Tag</span></span>

<span data-ttu-id="d8311-165">指定標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="d8311-165">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="d8311-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d8311-166">CommonParameters</span></span>

<span data-ttu-id="d8311-167">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="d8311-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d8311-168">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="d8311-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d8311-169">輸入</span><span class="sxs-lookup"><span data-stu-id="d8311-169">INPUTS</span></span>

### <span data-ttu-id="d8311-170">System.String[]</span><span class="sxs-lookup"><span data-stu-id="d8311-170">System.String[]</span></span>

### <span data-ttu-id="d8311-171">System.String</span><span class="sxs-lookup"><span data-stu-id="d8311-171">System.String</span></span>

### <span data-ttu-id="d8311-172">System.Uri</span><span class="sxs-lookup"><span data-stu-id="d8311-172">System.Uri</span></span>

### <span data-ttu-id="d8311-173">System.Management.Automation.PSCredential</span><span class="sxs-lookup"><span data-stu-id="d8311-173">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="d8311-174">輸出</span><span class="sxs-lookup"><span data-stu-id="d8311-174">OUTPUTS</span></span>

### <span data-ttu-id="d8311-175">PSRepositoryItemInfo</span><span class="sxs-lookup"><span data-stu-id="d8311-175">PSRepositoryItemInfo</span></span>

## <span data-ttu-id="d8311-176">注意</span><span class="sxs-lookup"><span data-stu-id="d8311-176">NOTES</span></span>

## <span data-ttu-id="d8311-177">相關連結</span><span class="sxs-lookup"><span data-stu-id="d8311-177">RELATED LINKS</span></span>

[<span data-ttu-id="d8311-178">Install-Script</span><span class="sxs-lookup"><span data-stu-id="d8311-178">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="d8311-179">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="d8311-179">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="d8311-180">Save-Script</span><span class="sxs-lookup"><span data-stu-id="d8311-180">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="d8311-181">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="d8311-181">Uninstall-Script</span></span>](Uninstall-Script.md)

[<span data-ttu-id="d8311-182">Update-Script</span><span class="sxs-lookup"><span data-stu-id="d8311-182">Update-Script</span></span>](Update-Script.md)
