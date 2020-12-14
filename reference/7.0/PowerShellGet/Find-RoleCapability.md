---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/05/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-rolecapability?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-RoleCapability
ms.openlocfilehash: 1cee4ac54bf83d387f61a4842104a80512a8b223
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891519"
---
# <span data-ttu-id="e1d00-103">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="e1d00-103">Find-RoleCapability</span></span>

## <span data-ttu-id="e1d00-104">概要</span><span class="sxs-lookup"><span data-stu-id="e1d00-104">SYNOPSIS</span></span>
<span data-ttu-id="e1d00-105">尋找模組中的角色功能。</span><span class="sxs-lookup"><span data-stu-id="e1d00-105">Finds role capabilities in modules.</span></span>

## <span data-ttu-id="e1d00-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e1d00-106">SYNTAX</span></span>

### <span data-ttu-id="e1d00-107">全部</span><span class="sxs-lookup"><span data-stu-id="e1d00-107">All</span></span>

```
Find-RoleCapability [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>] 
[-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease] 
[-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] 
[-Repository <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="e1d00-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e1d00-108">DESCRIPTION</span></span>

<span data-ttu-id="e1d00-109">此 `Find-RoleCapability` Cmdlet 會搜尋已註冊的存放庫，以尋找 PowerShell 角色功能和模組。</span><span class="sxs-lookup"><span data-stu-id="e1d00-109">The `Find-RoleCapability` cmdlet searches registered repositories to find PowerShell role capabilities and modules.</span></span>

<span data-ttu-id="e1d00-110">針對所找到的每個角色功能 `Find-RoleCapability` ，會傳回 **PSGetRoleCapabilityInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="e1d00-110">For each role capability found by `Find-RoleCapability`, a **PSGetRoleCapabilityInfo** object is returned.</span></span> <span data-ttu-id="e1d00-111">**PSGetRoleCapabilityInfo** 物件可以透過管線傳送至 `Install-Module` 或 `Save-Module` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e1d00-111">**PSGetRoleCapabilityInfo** objects can be sent down the pipeline to the `Install-Module` or `Save-Module` cmdlets.</span></span>

<span data-ttu-id="e1d00-112">PowerShell 角色功能定義使用者可以在 (JEA) 端點的足夠系統管理中使用哪些命令和應用程式。</span><span class="sxs-lookup"><span data-stu-id="e1d00-112">PowerShell role capabilities define which commands and applications are available to a user at a Just Enough Administration (JEA) endpoint.</span></span> <span data-ttu-id="e1d00-113">角色功能是由副檔名為的檔案所定義 `.psrc` 。</span><span class="sxs-lookup"><span data-stu-id="e1d00-113">Role capabilities are defined by files with a `.psrc` extension.</span></span>

## <span data-ttu-id="e1d00-114">範例</span><span class="sxs-lookup"><span data-stu-id="e1d00-114">EXAMPLES</span></span>

### <span data-ttu-id="e1d00-115">範例1：尋找角色功能</span><span class="sxs-lookup"><span data-stu-id="e1d00-115">Example 1: Find role capabilities</span></span>

<span data-ttu-id="e1d00-116">`Find-RoleCapability` 在每個已註冊的存放庫中尋找角色功能。</span><span class="sxs-lookup"><span data-stu-id="e1d00-116">`Find-RoleCapability` finds role capabilities in each registered repository.</span></span> <span data-ttu-id="e1d00-117">若要搜尋特定的存放庫，請使用存放 **庫** 參數。</span><span class="sxs-lookup"><span data-stu-id="e1d00-117">To search a specific repository, use the **Repository** parameter.</span></span>

```powershell
Find-RoleCapability
```

```output
Name             Version    ModuleName     Repository
----             -------    ----------     ----------
General-Lev1     1.0        JeaExamples    PSGallery
General-Lev2     1.0        JeaExamples    PSGallery
IIS-Lev1         1.0        JeaExamples    PSGallery
IIS-Lev2         1.0        JeaExamples    PSGallery
```

### <span data-ttu-id="e1d00-118">範例2：依名稱尋找角色功能</span><span class="sxs-lookup"><span data-stu-id="e1d00-118">Example 2: Find role capabilities by name</span></span>

<span data-ttu-id="e1d00-119">`Find-RoleCapability` 依名稱尋找角色功能。</span><span class="sxs-lookup"><span data-stu-id="e1d00-119">`Find-RoleCapability` finds role capabilities by name.</span></span> <span data-ttu-id="e1d00-120">使用逗號來分隔名稱陣列。</span><span class="sxs-lookup"><span data-stu-id="e1d00-120">Use commas to separate an array of names.</span></span>

```powershell
Find-RoleCapability -Name General-Lev1, IIS-Lev2
```

```output
Name             Version    ModuleName     Repository
----             -------    ----------     ----------
General-Lev1     1.0        JeaExamples    PSGallery
IIS-Lev2         1.0        JeaExamples    PSGallery
```

### <span data-ttu-id="e1d00-121">範例3：尋找並儲存角色功能的模組</span><span class="sxs-lookup"><span data-stu-id="e1d00-121">Example 3: Find and save a role capability's module</span></span>

<span data-ttu-id="e1d00-122">`Find-RoleCapability`Cmdlet 會尋找角色功能，並將物件沿著管線向下傳送。</span><span class="sxs-lookup"><span data-stu-id="e1d00-122">The `Find-RoleCapability` cmdlet finds a role capability and sends the object down the pipeline.</span></span>
<span data-ttu-id="e1d00-123">`Save-Module` 將角色功能的模組儲存至檔案系統。</span><span class="sxs-lookup"><span data-stu-id="e1d00-123">`Save-Module` saves the role capability's module to a file system.</span></span> <span data-ttu-id="e1d00-124">`Get-ChildItem` 顯示模組目錄的內容。</span><span class="sxs-lookup"><span data-stu-id="e1d00-124">`Get-ChildItem` displays the contents of the module's directory.</span></span>

```
PS> Find-RoleCapability -Name General-Lev1 | Save-Module -Path C:\Test\Modules

PS> Get-ChildItem -Path C:\Test\Modules\JeaExamples\1.0\

    Directory: C:\Test\Modules\JeaExamples\1.0

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----          6/4/2019    16:37                RoleCapabilities
-a----          2/5/2019    18:46           1702 CreateRegisterPSSC.ps1
-a----          2/5/2019    18:46           7656 JeaExamples.psd1
-a----         10/1/2018    08:16            595 JeaExamples.psm1
```

<span data-ttu-id="e1d00-125">`Find-RoleCapability` 使用 **Name** 參數來指定 **一般 Lev1** 角色功能。</span><span class="sxs-lookup"><span data-stu-id="e1d00-125">`Find-RoleCapability` uses the **Name** parameter to specify the **General-Lev1** role capability.</span></span>
<span data-ttu-id="e1d00-126">物件會向下傳送到管線。</span><span class="sxs-lookup"><span data-stu-id="e1d00-126">The object is sent down the pipeline.</span></span> <span data-ttu-id="e1d00-127">`Save-Module` 使用檔案系統位置的 **Path** 參數來儲存模組。</span><span class="sxs-lookup"><span data-stu-id="e1d00-127">`Save-Module` uses the **Path** parameter for the file system location to save the module.</span></span> <span data-ttu-id="e1d00-128">儲存模組之後，請 `Get-ChildItem` 指定模組的 **路徑** ，並顯示 **JeaExamples** 模組目錄的內容。</span><span class="sxs-lookup"><span data-stu-id="e1d00-128">After the module is saved, `Get-ChildItem` specifies the module's **Path** and displays the contents of the **JeaExamples** module's directory.</span></span>

### <span data-ttu-id="e1d00-129">範例4：尋找並安裝角色功能的模組</span><span class="sxs-lookup"><span data-stu-id="e1d00-129">Example 4: Find and install a role capability's module</span></span>

<span data-ttu-id="e1d00-130">`Find-RoleCapability` 尋找模組並將物件沿著管線向下傳送。</span><span class="sxs-lookup"><span data-stu-id="e1d00-130">`Find-RoleCapability` finds the module and sends the object down the pipeline.</span></span> <span data-ttu-id="e1d00-131">`Install-Module` 安裝模組。</span><span class="sxs-lookup"><span data-stu-id="e1d00-131">`Install-Module` installs the module.</span></span> <span data-ttu-id="e1d00-132">安裝之後，請使用 `Get-InstalledModule` 來查看結果。</span><span class="sxs-lookup"><span data-stu-id="e1d00-132">After the installation, use `Get-InstalledModule` to see the results.</span></span>

```
PS> Find-RoleCapability -Name General-Lev1 | Install-Module -Verbose

VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/JeaExamples/1.0.0'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/JeaExamples/1.0.0'.
VERBOSE: Completed downloading 'JeaExamples'.
VERBOSE: InstallPackageLocal' - name='JeaExamples', version='1.0',
VERBOSE: Validating the 'JeaExamples' module contents
VERBOSE: Test-ModuleManifest successfully validated the module manifest file
VERBOSE: Module 'JeaExamples' was installed successfully to path

PS> Get-InstalledModule

Version    Name            Repository     Description
-------    ----            ----------     -----------
1.0        JeaExamples     PSGallery      Some example Jea roles for general server maintenance...
```

<span data-ttu-id="e1d00-133">`Find-RoleCapability` 使用 **Name** 參數來指定 **一般 Lev1** 角色功能。</span><span class="sxs-lookup"><span data-stu-id="e1d00-133">`Find-RoleCapability` uses the **Name** parameter to specify the **General-Lev1** role capability.</span></span>
<span data-ttu-id="e1d00-134">物件會向下傳送到管線。</span><span class="sxs-lookup"><span data-stu-id="e1d00-134">The object is sent down the pipeline.</span></span> <span data-ttu-id="e1d00-135">`Install-Module` 使用 **Verbose** 參數，在安裝期間顯示狀態訊息。</span><span class="sxs-lookup"><span data-stu-id="e1d00-135">`Install-Module` uses the **Verbose** parameter to display status messages during the installation.</span></span> <span data-ttu-id="e1d00-136">安裝完成之後， `Get-InstalledModule` 輸出會確認已安裝 **JeaExamples** 模組。</span><span class="sxs-lookup"><span data-stu-id="e1d00-136">After the install is finished, the `Get-InstalledModule` output confirms that the **JeaExamples** module was installed.</span></span>

## <span data-ttu-id="e1d00-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e1d00-137">PARAMETERS</span></span>

### <span data-ttu-id="e1d00-138">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="e1d00-138">-AllowPrerelease</span></span>

<span data-ttu-id="e1d00-139">在結果中包含標示為發行前版本的資源。</span><span class="sxs-lookup"><span data-stu-id="e1d00-139">Includes resources marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="e1d00-140">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="e1d00-140">-AllVersions</span></span>

<span data-ttu-id="e1d00-141">指出此 Cmdlet 會取得模組的所有版本。</span><span class="sxs-lookup"><span data-stu-id="e1d00-141">Indicates that this cmdlet gets all versions of a module.</span></span> <span data-ttu-id="e1d00-142">**Allversions 進行篩選** 參數會顯示模組的每個可用版本。</span><span class="sxs-lookup"><span data-stu-id="e1d00-142">The **AllVersions** parameter displays each of a module's available versions.</span></span>

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

### <span data-ttu-id="e1d00-143">-Filter</span><span class="sxs-lookup"><span data-stu-id="e1d00-143">-Filter</span></span>

<span data-ttu-id="e1d00-144">根據 **PackageManagement** 提供者的搜尋語法尋找資源。</span><span class="sxs-lookup"><span data-stu-id="e1d00-144">Finds resources based on the **PackageManagement** provider's search syntax.</span></span> <span data-ttu-id="e1d00-145">例如，在 [ **ModuleName** ] 和 [ **描述** ] 屬性中指定要搜尋的文字。</span><span class="sxs-lookup"><span data-stu-id="e1d00-145">For example, specify words to search for within the **ModuleName** and **Description** properties.</span></span>

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

### <span data-ttu-id="e1d00-146">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="e1d00-146">-MaximumVersion</span></span>

<span data-ttu-id="e1d00-147">指定要包含在結果中之模組的最大版本。</span><span class="sxs-lookup"><span data-stu-id="e1d00-147">Specifies the maximum version of the module to include in results.</span></span> <span data-ttu-id="e1d00-148">無法在同一個命令中使用 **MaximumVersion** 和 **RequiredVersion** 參數。</span><span class="sxs-lookup"><span data-stu-id="e1d00-148">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="e1d00-149">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="e1d00-149">-MinimumVersion</span></span>

<span data-ttu-id="e1d00-150">指定要包含於結果中的模組最低版本。</span><span class="sxs-lookup"><span data-stu-id="e1d00-150">Specifies the minimum version of the module to include in results.</span></span> <span data-ttu-id="e1d00-151">**MinimumVersion** 和 **RequiredVersion** 參數無法在相同的命令中使用。</span><span class="sxs-lookup"><span data-stu-id="e1d00-151">The **MinimumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="e1d00-152">-ModuleName</span><span class="sxs-lookup"><span data-stu-id="e1d00-152">-ModuleName</span></span>

<span data-ttu-id="e1d00-153">指定要在其中搜尋角色功能的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="e1d00-153">Specifies the name of the module in which to search for role capabilities.</span></span> <span data-ttu-id="e1d00-154">預設為所有模組。</span><span class="sxs-lookup"><span data-stu-id="e1d00-154">The default is all modules.</span></span>

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

### <span data-ttu-id="e1d00-155">-Name</span><span class="sxs-lookup"><span data-stu-id="e1d00-155">-Name</span></span>

<span data-ttu-id="e1d00-156">指定角色功能的名稱。</span><span class="sxs-lookup"><span data-stu-id="e1d00-156">Specifies the name of a role capability.</span></span> <span data-ttu-id="e1d00-157">預設值為所有角色功能。</span><span class="sxs-lookup"><span data-stu-id="e1d00-157">The default is all role capabilities.</span></span> <span data-ttu-id="e1d00-158">使用逗號來分隔資源名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="e1d00-158">Use commas to separate an array of resource names.</span></span>

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

### <span data-ttu-id="e1d00-159">-Proxy</span><span class="sxs-lookup"><span data-stu-id="e1d00-159">-Proxy</span></span>

<span data-ttu-id="e1d00-160">為要求指定 proxy 伺服器，而不是直接連線到網際網路資源。</span><span class="sxs-lookup"><span data-stu-id="e1d00-160">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="e1d00-161">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="e1d00-161">-ProxyCredential</span></span>

<span data-ttu-id="e1d00-162">指定具有使用 **proxy** 參數中所指定 proxy 伺服器之許可權的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="e1d00-162">Specifies a user account with permission to use the proxy server specified in the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="e1d00-163">-Repository</span><span class="sxs-lookup"><span data-stu-id="e1d00-163">-Repository</span></span>

<span data-ttu-id="e1d00-164">指定要搜尋角色功能的存放庫。</span><span class="sxs-lookup"><span data-stu-id="e1d00-164">Specifies a repository to search for role capabilities.</span></span> <span data-ttu-id="e1d00-165">使用逗號來分隔存放庫名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="e1d00-165">Use commas to separate an array of repository names.</span></span>

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

### <span data-ttu-id="e1d00-166">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="e1d00-166">-RequiredVersion</span></span>

<span data-ttu-id="e1d00-167">指定要包含在結果中的模組確切版本號碼。</span><span class="sxs-lookup"><span data-stu-id="e1d00-167">Specifies the module's exact version number to include in the results.</span></span> <span data-ttu-id="e1d00-168">**RequiredVersion** 和 **MinimumVersion** 參數無法在相同的命令中使用。</span><span class="sxs-lookup"><span data-stu-id="e1d00-168">The **RequiredVersion** and the **MinimumVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="e1d00-169">-Tag</span><span class="sxs-lookup"><span data-stu-id="e1d00-169">-Tag</span></span>

<span data-ttu-id="e1d00-170">指定將存放庫中的模組分類的標記。</span><span class="sxs-lookup"><span data-stu-id="e1d00-170">Specifies tags that categorize modules in a repository.</span></span> <span data-ttu-id="e1d00-171">使用逗號來分隔標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="e1d00-171">Use commas to separate an array of tags.</span></span>

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

### <span data-ttu-id="e1d00-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e1d00-172">CommonParameters</span></span>

<span data-ttu-id="e1d00-173">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="e1d00-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e1d00-174">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="e1d00-174">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e1d00-175">輸入</span><span class="sxs-lookup"><span data-stu-id="e1d00-175">INPUTS</span></span>

### <span data-ttu-id="e1d00-176">System.Uri</span><span class="sxs-lookup"><span data-stu-id="e1d00-176">System.Uri</span></span>

### <span data-ttu-id="e1d00-177">System.Management.Automation.PSCredential</span><span class="sxs-lookup"><span data-stu-id="e1d00-177">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="e1d00-178">輸出</span><span class="sxs-lookup"><span data-stu-id="e1d00-178">OUTPUTS</span></span>

### <span data-ttu-id="e1d00-179">PSGetRoleCapabilityInfo</span><span class="sxs-lookup"><span data-stu-id="e1d00-179">PSGetRoleCapabilityInfo</span></span>

<span data-ttu-id="e1d00-180">Cmdlet 會傳回 `Find-RoleCapability` **PSGetRoleCapabilityInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="e1d00-180">The `Find-RoleCapability` cmdlet returns a **PSGetRoleCapabilityInfo** object.</span></span>

## <span data-ttu-id="e1d00-181">注意</span><span class="sxs-lookup"><span data-stu-id="e1d00-181">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1d00-182">從2020年4月起，PowerShell 資源庫不再支援傳輸層安全性 (TLS) 1.0 和1.1 版。</span><span class="sxs-lookup"><span data-stu-id="e1d00-182">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="e1d00-183">如果您不是使用 TLS 1.2 或更高版本，當您嘗試存取 PowerShell 資源庫時，將會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1d00-183">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="e1d00-184">使用下列命令，以確保您使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="e1d00-184">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="e1d00-185">如需詳細資訊，請參閱 PowerShell blog 中的 [公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 。</span><span class="sxs-lookup"><span data-stu-id="e1d00-185">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="e1d00-186">相關連結</span><span class="sxs-lookup"><span data-stu-id="e1d00-186">RELATED LINKS</span></span>

[<span data-ttu-id="e1d00-187">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="e1d00-187">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[<span data-ttu-id="e1d00-188">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="e1d00-188">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="e1d00-189">Install-Module</span><span class="sxs-lookup"><span data-stu-id="e1d00-189">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="e1d00-190">New-PSRoleCapabilityFile</span><span class="sxs-lookup"><span data-stu-id="e1d00-190">New-PSRoleCapabilityFile</span></span>](../Microsoft.PowerShell.Core/New-PSRoleCapabilityFile.md)

[<span data-ttu-id="e1d00-191">Save-Module</span><span class="sxs-lookup"><span data-stu-id="e1d00-191">Save-Module</span></span>](Save-Module.md)
