---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-command?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Command
ms.openlocfilehash: eb305801bb6f8c84ffdf0ff34936ec3156ba5b0e
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891249"
---
# <span data-ttu-id="4e4e6-103">Find-Command</span><span class="sxs-lookup"><span data-stu-id="4e4e6-103">Find-Command</span></span>

## <span data-ttu-id="4e4e6-104">概要</span><span class="sxs-lookup"><span data-stu-id="4e4e6-104">SYNOPSIS</span></span>
<span data-ttu-id="4e4e6-105">尋找模組中的 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-105">Finds PowerShell commands in modules.</span></span>

## <span data-ttu-id="4e4e6-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4e4e6-106">SYNTAX</span></span>

### <span data-ttu-id="4e4e6-107">全部</span><span class="sxs-lookup"><span data-stu-id="4e4e6-107">All</span></span>

```
Find-Command [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease]
 [-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Repository <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="4e4e6-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="4e4e6-108">DESCRIPTION</span></span>

<span data-ttu-id="4e4e6-109">`Find-Command`Cmdlet 會尋找 PowerShell 命令，例如 Cmdlet、別名、函式和工作流程。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-109">The `Find-Command` cmdlet finds PowerShell commands such as cmdlets, aliases, functions, and workflows.</span></span> <span data-ttu-id="4e4e6-110">`Find-Command` 搜尋已註冊存放庫中的模組。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-110">`Find-Command` searches modules in registered repositories.</span></span>

<span data-ttu-id="4e4e6-111">針對所找到的每個命令 `Find-Command` ，會傳回 **PSGetCommandInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-111">For each command found by `Find-Command`, a **PSGetCommandInfo** object is returned.</span></span> <span data-ttu-id="4e4e6-112">**PSGetCommandInfo** 物件可以向下傳送至 `Install-Module` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-112">The **PSGetCommandInfo** object can be sent down the pipeline to the `Install-Module` cmdlet.</span></span>
<span data-ttu-id="4e4e6-113">`Install-Module` 安裝包含命令的模組。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-113">`Install-Module` installs the module that contains the command.</span></span>

## <span data-ttu-id="4e4e6-114">範例</span><span class="sxs-lookup"><span data-stu-id="4e4e6-114">EXAMPLES</span></span>

### <span data-ttu-id="4e4e6-115">範例 1︰在指定的存放庫中尋找所有命令</span><span class="sxs-lookup"><span data-stu-id="4e4e6-115">Example 1: Find all commands in a specified repository</span></span>

<span data-ttu-id="4e4e6-116">Cmdlet 會在 `Find-Command` 已註冊的存放庫中搜尋模組。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-116">The `Find-Command` cmdlet searches a registered repository for modules.</span></span>

```powershell
Find-Command -Repository PSGallery | Select-Object -First 10
```

```output
Name                                Version    ModuleName          Repository
----                                -------    ----------          ----------
Disable-AzureRmDataCollection       5.8.3      AzureRM.profile     PSGallery
Disable-AzureRmContextAutosave      5.8.3      AzureRM.profile     PSGallery
Enable-AzureRmDataCollection        5.8.3      AzureRM.profile     PSGallery
Enable-AzureRmContextAutosave       5.8.3      AzureRM.profile     PSGallery
Remove-AzureRmEnvironment           5.8.3      AzureRM.profile     PSGallery
Get-AzureRmEnvironment              5.8.3      AzureRM.profile     PSGallery
Set-AzureRmEnvironment              5.8.3      AzureRM.profile     PSGallery
Add-AzureRmEnvironment              5.8.3      AzureRM.profile     PSGallery
Get-AzureRmSubscription             5.8.3      AzureRM.profile     PSGallery
Connect-AzureRmAccount              5.8.3      AzureRM.profile     PSGallery
```

<span data-ttu-id="4e4e6-117">`Find-Command` 使用存放 **庫** 參數來指定已註冊的存放庫名稱。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-117">`Find-Command` uses the **Repository** parameter to specify a registered repository's name.</span></span> <span data-ttu-id="4e4e6-118">物件會向下傳送到管線。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-118">The objects are sent down the pipeline.</span></span> <span data-ttu-id="4e4e6-119">`Select-Object` 接收物件，並使用 **第一個** 參數來顯示前10個結果。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-119">`Select-Object` receives the objects and uses the **First** parameter to display the first 10 results.</span></span>

### <span data-ttu-id="4e4e6-120">範例 2︰依名稱尋找命令</span><span class="sxs-lookup"><span data-stu-id="4e4e6-120">Example 2: Find a command by name</span></span>

<span data-ttu-id="4e4e6-121">`Find-Command` 可以使用命令的名稱，找出存放庫中的模組。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-121">`Find-Command` can use the name of a command to locate the module in a repository.</span></span> <span data-ttu-id="4e4e6-122">命令名稱有可能存在於多個 **ModuleNames** 中。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-122">It's possible that a command name exists in multiple **ModuleNames**.</span></span>

```powershell
Find-Command -Repository PSGallery -Name Get-TargetResource
```

```Output
Name                  Version    ModuleName                      Repository
----                  -------    ----------                      ----------
Get-TargetResource    3.1.0.0    xPowerShellExecutionPolicy      PSGallery
Get-TargetResource    1.0.0      xInternetExplorerHomePage       PSGallery
Get-TargetResource    1.2.0.0    SystemLocaleDsc                 PSGallery
```

<span data-ttu-id="4e4e6-123">`Find-Command` 使用存放 **庫** 參數來搜尋 **PSGallery**。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-123">`Find-Command` uses the **Repository** parameter to search the **PSGallery**.</span></span> <span data-ttu-id="4e4e6-124">**Name** 參數會指定 **get-targetresource** 命令。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-124">The **Name** parameter specifies the command **Get-TargetResource**.</span></span>

### <span data-ttu-id="4e4e6-125">範例3：依名稱尋找命令並安裝模組</span><span class="sxs-lookup"><span data-stu-id="4e4e6-125">Example 3: Find commands by name and install the module</span></span>

<span data-ttu-id="4e4e6-126">`Find-Command` 可以找到命令和模組，然後將物件傳送至 `Install-Module` 。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-126">`Find-Command` can locate the command and module, then send the object to `Install-Module`.</span></span> <span data-ttu-id="4e4e6-127">如果命令包含在多個模組中，請使用 `Find-Command` Cmdlet **模組名稱** 參數。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-127">If a command is included in multiple modules, use the `Find-Command` cmdlets **Module-Name** parameter.</span></span>
<span data-ttu-id="4e4e6-128">否則，可能會安裝您不想要安裝的模組。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-128">Otherwise, modules might be installed that you didn't want to install.</span></span>

```powershell
PS> Find-Command -Name Get-TargetResource -Repository PSGallery -ModuleName SystemLocaleDsc |
    Install-Module

PS> Get-InstalledModule

Version   Name               Repository   Description
-------   ----               ----------   -----------
1.2.0.0   SystemLocaleDsc    PSGallery    This DSC Resource allows configuration of the Windows...
```

<span data-ttu-id="4e4e6-129">`Find-Command` 使用 **Name** 參數來指定 **get-targetresource** 命令。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-129">`Find-Command` uses the **Name** parameter to specify the command **Get-TargetResource**.</span></span> <span data-ttu-id="4e4e6-130">存放 **庫** 參數會搜尋 **PSGallery**。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-130">The **Repository** parameter searches the **PSGallery**.</span></span> <span data-ttu-id="4e4e6-131">**ModuleName** 參數指定您想要安裝的模組（ **SystemLocaleDsc**）。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-131">The **ModuleName** parameter specifies the module you want to install, **SystemLocaleDsc**.</span></span> <span data-ttu-id="4e4e6-132">物件會沿著管線向下傳送 `Install-Module` ，而且會安裝模組。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-132">The object is sent down the pipeline to `Install-Module` and the module is installed.</span></span> <span data-ttu-id="4e4e6-133">安裝完成之後，您可以使用 `Get-InstalledModule` 來顯示結果。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-133">After the installation finishes, you can use `Get-InstalledModule` to display the results.</span></span>

### <span data-ttu-id="4e4e6-134">範例 4︰尋找命令並儲存其模組</span><span class="sxs-lookup"><span data-stu-id="4e4e6-134">Example 4: Find a command and save its module</span></span>

```
PS> Find-Command -Name Invoke-ScriptAnalyzer -Repository PSGallery | Save-Module -Path C:\Test\Modules -Verbose

VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/PSScriptAnalyzer/1.18.0'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/PSScriptAnalyzer/1.18.0'.
VERBOSE: Completed downloading 'PSScriptAnalyzer'.
VERBOSE: Module 'PSScriptAnalyzer' was saved successfully to path 'C:\Test\Modules\PSScriptAnalyzer\1.18.0'.
```

<span data-ttu-id="4e4e6-135">`Find-Command`使用 **名稱** 和 **儲存** 機制參數，在 **PSGallery** 存放庫中搜尋命令 **調用-ScriptAnalyzer** 。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-135">`Find-Command` uses the **Name** and **Repository** parameters to search for the command **Invoke-ScriptAnalyzer** in the **PSGallery** repository.</span></span> <span data-ttu-id="4e4e6-136">物件會向下傳送到管線 `Save-Module` 。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-136">The object is sent down the pipeline to `Save-Module`.</span></span> <span data-ttu-id="4e4e6-137">**Path** 參數會決定要儲存模組的位置。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-137">The **Path** parameter determines the location to save the module.</span></span> <span data-ttu-id="4e4e6-138">**Verbose** 是選擇性參數，但會在 PowerShell 主控台中顯示狀態輸出。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-138">**Verbose** is an optional parameter, but displays status output in the PowerShell console.</span></span> <span data-ttu-id="4e4e6-139">詳細資訊輸出有助於進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-139">The verbose output is beneficial for troubleshooting.</span></span>

## <span data-ttu-id="4e4e6-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4e4e6-140">PARAMETERS</span></span>

### <span data-ttu-id="4e4e6-141">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="4e4e6-141">-AllowPrerelease</span></span>

<span data-ttu-id="4e4e6-142">在結果中包含標示為發行前版本的模組。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-142">Includes modules marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="4e4e6-143">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="4e4e6-143">-AllVersions</span></span>

<span data-ttu-id="4e4e6-144">指出此 Cmdlet 會取得模組的所有版本。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-144">Indicates that this cmdlet gets all versions of a module.</span></span>

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

### <span data-ttu-id="4e4e6-145">-Filter</span><span class="sxs-lookup"><span data-stu-id="4e4e6-145">-Filter</span></span>

<span data-ttu-id="4e4e6-146">根據 **PackageManagement** 提供者的搜尋語法尋找模組。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-146">Finds modules based on the **PackageManagement** provider's search syntax.</span></span> <span data-ttu-id="4e4e6-147">例如，在 [ **ModuleName** ] 和 [ **描述** ] 屬性中指定要搜尋的文字。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-147">For example, specify words to search for within the **ModuleName** and **Description** properties.</span></span>

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

### <span data-ttu-id="4e4e6-148">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="4e4e6-148">-MaximumVersion</span></span>

<span data-ttu-id="4e4e6-149">指定要包含在結果中之模組的最大版本。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-149">Specifies the maximum version of the module to include in results.</span></span> <span data-ttu-id="4e4e6-150">無法在同一個命令中使用 **MaximumVersion** 和 **RequiredVersion** 參數。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-150">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="4e4e6-151">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="4e4e6-151">-MinimumVersion</span></span>

<span data-ttu-id="4e4e6-152">指定要包含於結果中的模組最低版本。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-152">Specifies the minimum version of the module to include in results.</span></span> <span data-ttu-id="4e4e6-153">**MinimumVersion** 和 **RequiredVersion** 參數無法在相同的命令中使用。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-153">The **MinimumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="4e4e6-154">-ModuleName</span><span class="sxs-lookup"><span data-stu-id="4e4e6-154">-ModuleName</span></span>

<span data-ttu-id="4e4e6-155">指定要搜尋命令的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-155">Specifies the name of a module to search for commands.</span></span> <span data-ttu-id="4e4e6-156">預設為所有模組。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-156">The default is all modules.</span></span>

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

### <span data-ttu-id="4e4e6-157">-Name</span><span class="sxs-lookup"><span data-stu-id="4e4e6-157">-Name</span></span>

<span data-ttu-id="4e4e6-158">指定要在存放庫中搜尋的命令名稱。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-158">Specifies the command name to search for in a repository.</span></span> <span data-ttu-id="4e4e6-159">使用逗號來分隔命令名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-159">Use commas to separate an array of command names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e4e6-160">-Proxy</span><span class="sxs-lookup"><span data-stu-id="4e4e6-160">-Proxy</span></span>

<span data-ttu-id="4e4e6-161">為要求指定 proxy 伺服器，而不是直接連線到網際網路資源。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-161">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="4e4e6-162">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="4e4e6-162">-ProxyCredential</span></span>

<span data-ttu-id="4e4e6-163">指定具有使用 **Proxy** 參數所指定 Proxy 伺服器之權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-163">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="4e4e6-164">-Repository</span><span class="sxs-lookup"><span data-stu-id="4e4e6-164">-Repository</span></span>

<span data-ttu-id="4e4e6-165">指定要搜尋命令的存放庫。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-165">Specifies the repository to search for commands.</span></span> <span data-ttu-id="4e4e6-166">使用逗號來分隔存放庫名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-166">Use commas to separate an array of repository names.</span></span> <span data-ttu-id="4e4e6-167">預設為所有存放庫。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-167">The default is all repositories.</span></span>

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

### <span data-ttu-id="4e4e6-168">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="4e4e6-168">-RequiredVersion</span></span>

<span data-ttu-id="4e4e6-169">指定要包含於結果中的模組版本。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-169">Specifies the version of the module to include in the results.</span></span>

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

### <span data-ttu-id="4e4e6-170">-Tag</span><span class="sxs-lookup"><span data-stu-id="4e4e6-170">-Tag</span></span>

<span data-ttu-id="4e4e6-171">指定將存放庫中的模組分類的標記。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-171">Specifies tags that categorize modules in a repository.</span></span> <span data-ttu-id="4e4e6-172">使用逗號來分隔標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-172">Use commas to separate an array of tags.</span></span>

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

### <span data-ttu-id="4e4e6-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4e4e6-173">CommonParameters</span></span>

<span data-ttu-id="4e4e6-174">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-174">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4e4e6-175">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-175">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4e4e6-176">輸入</span><span class="sxs-lookup"><span data-stu-id="4e4e6-176">INPUTS</span></span>

## <span data-ttu-id="4e4e6-177">輸出</span><span class="sxs-lookup"><span data-stu-id="4e4e6-177">OUTPUTS</span></span>

### <span data-ttu-id="4e4e6-178">PSGetCommandInfo</span><span class="sxs-lookup"><span data-stu-id="4e4e6-178">PSGetCommandInfo</span></span>

<span data-ttu-id="4e4e6-179">`Find-Command` 輸出 **PSGetCommandInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-179">`Find-Command` outputs a **PSGetCommandInfo** object.</span></span>

## <span data-ttu-id="4e4e6-180">注意</span><span class="sxs-lookup"><span data-stu-id="4e4e6-180">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4e4e6-181">從2020年4月起，PowerShell 資源庫不再支援傳輸層安全性 (TLS) 1.0 和1.1 版。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-181">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="4e4e6-182">如果您不是使用 TLS 1.2 或更高版本，當您嘗試存取 PowerShell 資源庫時，將會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-182">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="4e4e6-183">使用下列命令，以確保您使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="4e4e6-183">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="4e4e6-184">如需詳細資訊，請參閱 PowerShell blog 中的 [公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 。</span><span class="sxs-lookup"><span data-stu-id="4e4e6-184">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="4e4e6-185">相關連結</span><span class="sxs-lookup"><span data-stu-id="4e4e6-185">RELATED LINKS</span></span>

[<span data-ttu-id="4e4e6-186">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="4e4e6-186">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="4e4e6-187">Install-Module</span><span class="sxs-lookup"><span data-stu-id="4e4e6-187">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="4e4e6-188">Save-Module</span><span class="sxs-lookup"><span data-stu-id="4e4e6-188">Save-Module</span></span>](Save-Module.md)

[<span data-ttu-id="4e4e6-189">Select-Object</span><span class="sxs-lookup"><span data-stu-id="4e4e6-189">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="4e4e6-190">卸載模組</span><span class="sxs-lookup"><span data-stu-id="4e4e6-190">Uninstall-Module</span></span>](Uninstall-Module.md)
