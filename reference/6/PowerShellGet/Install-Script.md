---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/install-script?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Script
ms.openlocfilehash: ecae1ba3a3aea6628817bab2f09fc23e23162f03
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204279"
---
# <span data-ttu-id="5dd3e-103">Install-Script</span><span class="sxs-lookup"><span data-stu-id="5dd3e-103">Install-Script</span></span>

## <span data-ttu-id="5dd3e-104">概要</span><span class="sxs-lookup"><span data-stu-id="5dd3e-104">SYNOPSIS</span></span>
<span data-ttu-id="5dd3e-105">安裝腳本。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-105">Installs a script.</span></span>

## <span data-ttu-id="5dd3e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5dd3e-106">SYNTAX</span></span>

### <span data-ttu-id="5dd3e-107">NameParameterSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="5dd3e-107">NameParameterSet (Default)</span></span>

```
Install-Script [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Scope <String>] [-NoPathUpdate]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force]
 [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="5dd3e-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="5dd3e-108">InputObject</span></span>

```
Install-Script [-InputObject] <PSObject[]> [-Scope <String>] [-NoPathUpdate] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="5dd3e-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5dd3e-109">DESCRIPTION</span></span>

<span data-ttu-id="5dd3e-110">`Install-Script`Cmdlet 會從存放庫取得腳本承載、確認承載是有效的 PowerShell 腳本，並將腳本檔案複製到指定的安裝位置。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-110">The `Install-Script` cmdlet acquires a script payload from a repository, verifies that the payload is a valid PowerShell script, and copies the script file to a specified installation location.</span></span>

<span data-ttu-id="5dd3e-111">預設的存放庫 `Install-Script` 操作可透過 `Register-PSRepository` 、 `Set-PSRepository` 、 `Unregister-PSRepository` 和 Cmdlet 來設定 `Get-PSRepository` 。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-111">The default repositories `Install-Script` operates against are configurable through the `Register-PSRepository`, `Set-PSRepository`, `Unregister-PSRepository`, and `Get-PSRepository` cmdlets.</span></span> <span data-ttu-id="5dd3e-112">針對多個存放庫操作時， `Install-Script` 會從第一個存放庫安裝符合指定搜尋條件的第一個腳本， ( **名稱** 、 **MinimumVersion** 或 **MaximumVersion** ) ，而不會發生任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-112">When operating against multiple repositories, `Install-Script` installs the first script that matches the specified search criteria ( **Name** , **MinimumVersion** , or **MaximumVersion** ) from the first repository without any error.</span></span>

## <span data-ttu-id="5dd3e-113">範例</span><span class="sxs-lookup"><span data-stu-id="5dd3e-113">EXAMPLES</span></span>

### <span data-ttu-id="5dd3e-114">範例1：尋找並安裝腳本</span><span class="sxs-lookup"><span data-stu-id="5dd3e-114">Example 1: Find a script and install it</span></span>

```
PS C:\> Find-Script -Repository "Local1" -Name "Required-Script2"
Version    Name                           Type       Repository           Description
-------    ----                           ----       ----------           -----------
2.5        Required-Script2               Script     local1               Description for the Required-Script2 script

PS C:\> Find-Script -Repository "Local1" -Name "Required-Script2" | Install-Script
PS C:\> Get-Command -Name "Required-Script2"
CommandType     Name                      Version    Source
-----------     ----                      -------    ------
ExternalScript  Required-Script2.ps1      2.0       C:\Users\pattif\Documents\WindowsPowerShell\Scripts\Required-Script2.ps1

PS C:\> Get-InstalledScript -Name "Required-Script2"
Version    Name                  Type     Repository           Description
-------    ----                  ----     ----------           -----------
2.5        Required-Script2      Script   local1               Description for the Required-Script2 script

PS C:\> Get-InstalledScript -Name "Required-Script2" | Format-List *
Name                       : Required-Script2
Version                    : 2.5
Type                       : Script
Description                : Description for the Required-Script2 script
Author                     : pattif
CompanyName                :
Copyright                  : 2015 Microsoft Corporation. All rights reserved.
PublishedDate              : 8/15/2015 12:42:39 AM
LicenseUri                 : http://required-script2.com/license
ProjectUri                 : http://required-script2.com/
IconUri                    : http://required-script2.com/icon
Tags                       : {Tag1, Tag2, Tag-Required-Script2-2.5, PSScript...}
Includes                   : {Function, DscResource, Cmdlet, Command}
PowerShellGetFormatVersion :
ReleaseNotes               : Required-Script2 release notes
Dependencies               : {}
RepositorySourceLocation   : http://pattif-dev:8765/api/v2/
Repository                 : local1
PackageManagementProvider  : NuGet
InstalledLocation          : C:\Users\pattif\Documents\WindowsPowerShell\Scripts
```

<span data-ttu-id="5dd3e-115">第一個命令會從 Local1 存放庫中尋找名為的腳本 `Required-Script2` ，並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-115">The first command finds the script named `Required-Script2` from the Local1 repository and displays the results.</span></span>

<span data-ttu-id="5dd3e-116">第二個命令 `Required-Script2` 會尋找腳本，然後使用管線運算子將它傳遞給 `Install-Script` Cmdlet 以進行安裝。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-116">The second command finds the `Required-Script2` script, and then uses the pipeline operator to pass it to the `Install-Script` cmdlet to install it.</span></span>

<span data-ttu-id="5dd3e-117">第三個命令會使用 `Get-Command` Cmdlet 來取得 `Required-Script2` ，然後顯示結果。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-117">The third command uses the `Get-Command` cmdlet to get `Required-Script2`, and then displays the results.</span></span>

<span data-ttu-id="5dd3e-118">第四個命令會使用 `Get-InstalledScript` Cmdlet 來取得 `Required-Script2` 和顯示結果。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-118">The fourth command uses the `Get-InstalledScript` cmdlet to get `Required-Script2` and display the results.</span></span>

<span data-ttu-id="5dd3e-119">第五個命令 `Required-Script2` 會取得並使用管線運算子，將它傳遞至 `Format-List` Cmdlet 以格式化輸出。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-119">The fifth command gets `Required-Script2` and uses the pipeline operator to pass it to the `Format-List` cmdlet to format the output.</span></span>

### <span data-ttu-id="5dd3e-120">範例2：使用 AllUsers 範圍安裝腳本</span><span class="sxs-lookup"><span data-stu-id="5dd3e-120">Example 2: Install a script with AllUsers scope</span></span>

```
PS C:\> Install-Script -Repository "Local1" -Name "Required-Script3" -Scope "AllUsers"
PS C:\> Get-InstalledScript -Name "Required-Script3"
Version    Name                  Type       Repository    Description
-------    ----                  ----       ----------    -----------
2.5        Required-Script3      Script     local1        Description for the Required-Script3 script

PS C:\> Get-InstalledScript -Name "Required-Script3" | Format-List *
Name                       : Required-Script3
Version                    : 2.5
Type                       : Script
Description                : Description for the Required-Script3 script
Author                     : pattif
CompanyName                :
Copyright                  : 2015 Microsoft Corporation. All rights reserved.
PublishedDate              : 8/15/2015 12:42:45 AM
LicenseUri                 : http://required-script3.com/license
ProjectUri                 : http://required-script3.com/
IconUri                    : http://required-script3.com/icon
Tags                       : {Tag1, Tag2, Tag-Required-Script3-2.5, PSScript...}
Includes                   : {Function, DscResource, Cmdlet, Command}
PowerShellGetFormatVersion :
ReleaseNotes               : Required-Script3 release notes
Dependencies               : {}
RepositorySourceLocation   : http://pattif-dev:8765/api/v2/
Repository                 : local1
PackageManagementProvider  : NuGet
InstalledLocation          : C:\Program Files\WindowsPowerShell\Scripts
```

<span data-ttu-id="5dd3e-121">第一個命令會安裝名為的腳本 `Required-Script3` ，並將它指派給它的 AllUsers 範圍。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-121">The first command installs the script named `Required-Script3` and assigns it AllUsers scope.</span></span>

<span data-ttu-id="5dd3e-122">第二個命令會取得已安裝的腳本 `Required-Script3` ，並顯示其相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-122">The second command gets the installed script `Required-Script3` and displays information about it.</span></span>

<span data-ttu-id="5dd3e-123">第三個命令 `Required-Script3` 會取得並使用管線運算子，將它傳遞至 `Format-List` Cmdlet 以格式化輸出。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-123">The third command gets `Required-Script3` and uses the pipeline operator to pass it to the `Format-List` cmdlet to format the output.</span></span>

### <span data-ttu-id="5dd3e-124">範例3：安裝腳本及其相依性</span><span class="sxs-lookup"><span data-stu-id="5dd3e-124">Example 3: Install a script and its dependencies</span></span>

```
PS C:\> Find-Script -Repository "Local1" -Name "Script-WithDependencies2" -IncludeDependencies
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.0        Script-WithDependencies2    Script     local1        Description for the Script-WithDependencies2 script
2.5        RequiredModule1             Module     local1        RequiredModule1 module
2.5        RequiredModule2             Module     local1        RequiredModule2 module
2.5        RequiredModule3             Module     local1        RequiredModule3 module
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script

PS C:\> Install-Script -Repository "Local1" -Name "Script-WithDependencies2"
PS C:\> Get-InstalledScript
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script
2.0        Script-WithDependencies2    Script     local1        Description for the Script-WithDependencies2 script

PS C:\> Get-InstalledModule
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        RequiredModule1             Module     local1        RequiredModule1 module
2.5        RequiredModule2             Module     local1        RequiredModule2 module
2.5        RequiredModule3             Module     local1        RequiredModule3 module

PS C:\> Find-Script -Repository "Local1" -Name "Required-Script*"
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script

PS C:\> Install-Script -Repository "Local1" -Name "Required-Script*"
PS C:\> Get-InstalledScript
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script
```

<span data-ttu-id="5dd3e-125">第一個命令會在 Local1 儲存機制中尋找名為的腳本及其相依性 `Script-WithDependencies2` ，並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-125">The first command finds the script named `Script-WithDependencies2` and its dependencies in the Local1 repository and displays the results.</span></span>

<span data-ttu-id="5dd3e-126">第二個命令會安裝 `Script-WithDependencies2` 。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-126">The second command installs `Script-WithDependencies2`.</span></span>

<span data-ttu-id="5dd3e-127">第三個命令使用 `Get-InstalledScript` script Cmdlet 來取得已安裝的腳本並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-127">The third command uses the `Get-InstalledScript` script cmdlet to get installed scripts and display the results.</span></span>

<span data-ttu-id="5dd3e-128">第四個命令會使用 `Get-InstalledModule` Cmdlet 來取得已安裝的模組，並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-128">The fourth command uses the `Get-InstalledModule` cmdlet to get installed modules and display the results.</span></span>

<span data-ttu-id="5dd3e-129">第五個命令會使用 `Find-Script` Cmdlet 來尋找名稱開頭為的腳本 `Required-Script` ，並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-129">The fifth command uses the `Find-Script` cmdlet to find scripts where the name begins with `Required-Script` and display the results.</span></span>

<span data-ttu-id="5dd3e-130">第六個命令會安裝 Local1 存放庫中名稱開頭的腳本 `Required-Script` 。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-130">The sixth command installs the scripts where the name begins with `Required-Script` in the Local1 repository.</span></span>

<span data-ttu-id="5dd3e-131">最後一個命令會取得已安裝的腳本，並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-131">The final command gets installed scripts and displays the results.</span></span>

## <span data-ttu-id="5dd3e-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5dd3e-132">PARAMETERS</span></span>

### <span data-ttu-id="5dd3e-133">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="5dd3e-133">-AcceptLicense</span></span>

<span data-ttu-id="5dd3e-134">如果模組需要，則會在安裝期間自動接受授權合約。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-134">Automatically accept the license agreement during installation if the module requires it.</span></span>

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

### <span data-ttu-id="5dd3e-135">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="5dd3e-135">-AllowPrerelease</span></span>

<span data-ttu-id="5dd3e-136">可讓您安裝標示為發行前版本的腳本。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-136">Allows you to install a script marked as a prerelease.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5dd3e-137">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5dd3e-137">-Confirm</span></span>

<span data-ttu-id="5dd3e-138">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-138">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5dd3e-139">-Credential</span><span class="sxs-lookup"><span data-stu-id="5dd3e-139">-Credential</span></span>

<span data-ttu-id="5dd3e-140">指定有權為指定的套件提供者或來源安裝腳本的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-140">Specifies a user account that has rights to install a script for a specified package provider or source.</span></span>

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

### <span data-ttu-id="5dd3e-141">-Force</span><span class="sxs-lookup"><span data-stu-id="5dd3e-141">-Force</span></span>

<span data-ttu-id="5dd3e-142">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-142">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="5dd3e-143">-InputObject</span><span class="sxs-lookup"><span data-stu-id="5dd3e-143">-InputObject</span></span>

<span data-ttu-id="5dd3e-144">用於管線輸入。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-144">Used for pipeline input.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5dd3e-145">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="5dd3e-145">-MaximumVersion</span></span>

<span data-ttu-id="5dd3e-146">指定要安裝之單一腳本的最大版本。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-146">Specifies the maximum version of a single scripts to install.</span></span> <span data-ttu-id="5dd3e-147">如果您嘗試安裝多個腳本，就無法新增此參數。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-147">You cannot add this parameter if you are attempting to install multiple scripts.</span></span> <span data-ttu-id="5dd3e-148">**MaximumVersion** 和 **RequiredVersion** 參數是互斥的；您無法在相同的命令中使用這兩個參數。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-148">The **MaximumVersion** and the **RequiredVersion** parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5dd3e-149">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="5dd3e-149">-MinimumVersion</span></span>

<span data-ttu-id="5dd3e-150">指定要安裝之單一腳本的最小版本。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-150">Specifies the minimum version of a single script to install.</span></span> <span data-ttu-id="5dd3e-151">如果您嘗試安裝多個腳本，就無法新增此參數。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-151">You cannot add this parameter if you are attempting to install multiple scripts.</span></span> <span data-ttu-id="5dd3e-152">**MinimumVersion** 和 **RequiredVersion** 參數是互斥的；您無法在相同的命令中使用這兩個參數。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-152">The **MinimumVersion** and the **RequiredVersion** parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5dd3e-153">-Name</span><span class="sxs-lookup"><span data-stu-id="5dd3e-153">-Name</span></span>

<span data-ttu-id="5dd3e-154">指定要安裝之腳本的名稱陣列。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-154">Specifies an array of names of scripts to install.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5dd3e-155">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="5dd3e-155">-NoPathUpdate</span></span>

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

### <span data-ttu-id="5dd3e-156">-PassThru</span><span class="sxs-lookup"><span data-stu-id="5dd3e-156">-PassThru</span></span>

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

### <span data-ttu-id="5dd3e-157">-Proxy</span><span class="sxs-lookup"><span data-stu-id="5dd3e-157">-Proxy</span></span>

<span data-ttu-id="5dd3e-158">指定要求的 proxy 伺服器，而不是直接連接到網際網路資源。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-158">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="5dd3e-159">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="5dd3e-159">-ProxyCredential</span></span>

<span data-ttu-id="5dd3e-160">指定具有使用 **Proxy** 參數所指定 Proxy 伺服器之權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-160">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="5dd3e-161">-Repository</span><span class="sxs-lookup"><span data-stu-id="5dd3e-161">-Repository</span></span>

<span data-ttu-id="5dd3e-162">指定已向 Cmdlet 註冊之存放庫的易記名稱 `Register-PSRepository` 。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-162">Specifies the friendly name of a repository that has been registered with the `Register-PSRepository` cmdlet.</span></span> <span data-ttu-id="5dd3e-163">預設值為所有已註冊的存放庫。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-163">The default is all registered repositories.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5dd3e-164">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="5dd3e-164">-RequiredVersion</span></span>

<span data-ttu-id="5dd3e-165">指定要安裝之腳本的確切版本號碼。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-165">Specifies the exact version number of the script to install.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5dd3e-166">-Scope</span><span class="sxs-lookup"><span data-stu-id="5dd3e-166">-Scope</span></span>

<span data-ttu-id="5dd3e-167">指定指令碼的安裝範圍。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-167">Specifies the installation scope of the script.</span></span>
<span data-ttu-id="5dd3e-168">有效值為︰AllUsers 和 CurrentUser。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-168">Valid values are: AllUsers and CurrentUser.</span></span>

<span data-ttu-id="5dd3e-169">AllUsers 範圍可讓模組安裝在電腦的所有使用者都可存取的位置，也就是 `$env:ProgramFiles\WindowsPowerShell\Scripts` 。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-169">The AllUsers scope lets modules be installed in a location that is accessible to all users of the computer, that is, `$env:ProgramFiles\WindowsPowerShell\Scripts`.</span></span>

<span data-ttu-id="5dd3e-170">CurrentUser 範圍只會將模組安裝到 `$home\Documents\WindowsPowerShell\Scripts` ，讓模組只能供目前的使用者使用。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-170">The CurrentUser scope lets modules be installed only to `$home\Documents\WindowsPowerShell\Scripts`, so that the module is available only to the current user.</span></span>

<span data-ttu-id="5dd3e-171">未定義 **範圍** 時，會根據目前的會話設定預設值：</span><span class="sxs-lookup"><span data-stu-id="5dd3e-171">When no **Scope** is defined, the default will be set based on the current session:</span></span>

- <span data-ttu-id="5dd3e-172">若為提高許可權的 PowerShell 會話， **範圍** 預設為 AllUsers;</span><span class="sxs-lookup"><span data-stu-id="5dd3e-172">For an elevated PowerShell session, **Scope** defaults to AllUsers;</span></span>
- <span data-ttu-id="5dd3e-173">若為 [PowerShellGet 版 2.0.0](https://www.powershellgallery.com/packages/PowerShellGet) 和更新版本中未提高許可權的 PowerShell 會話， **範圍** 為 CurrentUser;</span><span class="sxs-lookup"><span data-stu-id="5dd3e-173">For non-elevated PowerShell sessions in [PowerShellGet versions 2.0.0](https://www.powershellgallery.com/packages/PowerShellGet) and above, **Scope** is CurrentUser;</span></span>
- <span data-ttu-id="5dd3e-174">若為 PowerShellGet 版1.6.7 和更早版本中未提高許可權的 PowerShell 會話，則未定義 **範圍** ，且 `Install-Module` 會失敗。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-174">For non-elevated PowerShell sessions in PowerShellGet versions 1.6.7 and earlier, **Scope** is undefined, and `Install-Module` fails.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5dd3e-175">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5dd3e-175">-WhatIf</span></span>

<span data-ttu-id="5dd3e-176">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-176">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="5dd3e-177">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-177">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5dd3e-178">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5dd3e-178">CommonParameters</span></span>

<span data-ttu-id="5dd3e-179">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-179">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5dd3e-180">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="5dd3e-180">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5dd3e-181">輸入</span><span class="sxs-lookup"><span data-stu-id="5dd3e-181">INPUTS</span></span>

### <span data-ttu-id="5dd3e-182">System.String[]</span><span class="sxs-lookup"><span data-stu-id="5dd3e-182">System.String[]</span></span>

### <span data-ttu-id="5dd3e-183">管理. PSObject []</span><span class="sxs-lookup"><span data-stu-id="5dd3e-183">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="5dd3e-184">System.String</span><span class="sxs-lookup"><span data-stu-id="5dd3e-184">System.String</span></span>

### <span data-ttu-id="5dd3e-185">System.Uri</span><span class="sxs-lookup"><span data-stu-id="5dd3e-185">System.Uri</span></span>

### <span data-ttu-id="5dd3e-186">System.Management.Automation.PSCredential</span><span class="sxs-lookup"><span data-stu-id="5dd3e-186">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="5dd3e-187">輸出</span><span class="sxs-lookup"><span data-stu-id="5dd3e-187">OUTPUTS</span></span>

### <span data-ttu-id="5dd3e-188">System.Object</span><span class="sxs-lookup"><span data-stu-id="5dd3e-188">System.Object</span></span>

## <span data-ttu-id="5dd3e-189">注意</span><span class="sxs-lookup"><span data-stu-id="5dd3e-189">NOTES</span></span>

## <span data-ttu-id="5dd3e-190">相關連結</span><span class="sxs-lookup"><span data-stu-id="5dd3e-190">RELATED LINKS</span></span>

[<span data-ttu-id="5dd3e-191">Find-Script</span><span class="sxs-lookup"><span data-stu-id="5dd3e-191">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="5dd3e-192">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="5dd3e-192">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="5dd3e-193">Save-Script</span><span class="sxs-lookup"><span data-stu-id="5dd3e-193">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="5dd3e-194">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="5dd3e-194">Uninstall-Script</span></span>](Uninstall-Script.md)

[<span data-ttu-id="5dd3e-195">Update-Script</span><span class="sxs-lookup"><span data-stu-id="5dd3e-195">Update-Script</span></span>](Update-Script.md)
