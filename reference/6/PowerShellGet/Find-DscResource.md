---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/04/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-dscresource?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-DscResource
ms.openlocfilehash: 9f6d10c0687b0030b26b28cca505493c5b66c8e3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203675"
---
# <span data-ttu-id="4908e-103">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="4908e-103">Find-DscResource</span></span>

## <span data-ttu-id="4908e-104">概要</span><span class="sxs-lookup"><span data-stu-id="4908e-104">SYNOPSIS</span></span>
<span data-ttu-id="4908e-105">尋找 Desired State Configuration (DSC) 資源。</span><span class="sxs-lookup"><span data-stu-id="4908e-105">Finds Desired State Configuration (DSC) resources.</span></span>

## <span data-ttu-id="4908e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4908e-106">SYNTAX</span></span>

### <span data-ttu-id="4908e-107">全部</span><span class="sxs-lookup"><span data-stu-id="4908e-107">All</span></span>

```
Find-DscResource [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease]
 [-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Repository <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="4908e-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="4908e-108">DESCRIPTION</span></span>

<span data-ttu-id="4908e-109">此 `Find-DscResource` Cmdlet 會搜尋已註冊的存放庫，以找出模組中包含的 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="4908e-109">The `Find-DscResource` cmdlet searches registered repositories to find DSC resources contained in modules.</span></span> <span data-ttu-id="4908e-110">依預設會 `Find-DscResource` 搜尋所有已註冊的存放庫。</span><span class="sxs-lookup"><span data-stu-id="4908e-110">By default `Find-DscResource` searches all registered repositories.</span></span>

<span data-ttu-id="4908e-111">針對所找到的每個模組 `Find-DscResource` ，會傳回 **PSGetDscResourceInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="4908e-111">For each module found by `Find-DscResource`, a **PSGetDscResourceInfo** object is returned.</span></span>
<span data-ttu-id="4908e-112">**PSGetDscResourceInfo** 物件可以透過管線傳送至 `Install-Module` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4908e-112">**PSGetDscResourceInfo** objects can be sent down the pipeline to the `Install-Module` cmdlet.</span></span>
<span data-ttu-id="4908e-113">`Install-Module` 安裝模組。</span><span class="sxs-lookup"><span data-stu-id="4908e-113">`Install-Module` installs the module.</span></span>

## <span data-ttu-id="4908e-114">範例</span><span class="sxs-lookup"><span data-stu-id="4908e-114">EXAMPLES</span></span>

### <span data-ttu-id="4908e-115">範例1：尋找所有 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="4908e-115">Example 1: Find all DSC resources</span></span>

<span data-ttu-id="4908e-116">`Find-DscResource` 從已註冊的存放庫傳回 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="4908e-116">`Find-DscResource` returns DSC resources from registered repositories.</span></span> <span data-ttu-id="4908e-117">若要搜尋特定的存放庫，請使用存放 **庫** 參數。</span><span class="sxs-lookup"><span data-stu-id="4908e-117">To search a specific repository, use the **Repository** parameter.</span></span>

```powershell
Find-DscResource
```

```Output
Name                           Version    ModuleName                     Repository
----                           -------    ----------                     ----------
Carbon_Privilege               2.8.1      Carbon                         PSGallery
Carbon_ScheduledTask           2.8.1      Carbon                         PSGallery
Carbon_Service                 2.8.1      Carbon                         PSGallery
PackageManagement              1.4        PackageManagement              PSGallery
PackageManagementSource        1.4        PackageManagement              PSGallery
PSModule                       2.1.4      PowerShellGet                  PSGallery
PSRepository                   2.1.4      PowerShellGet                  PSGallery
xArchive                       8.7.0.0    xPSDesiredStateConfiguration   PSGallery
xDSCWebService                 8.7.0.0    xPSDesiredStateConfiguration   PSGallery
xEnvironment                   8.7.0.0    xPSDesiredStateConfiguration   PSGallery
```

### <span data-ttu-id="4908e-118">範例2：依名稱尋找 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="4908e-118">Example 2: Find a DSC resource by name</span></span>

<span data-ttu-id="4908e-119">`Find-DscResource` 依名稱尋找 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="4908e-119">`Find-DscResource` locates DSC resources by name.</span></span> <span data-ttu-id="4908e-120">使用逗號來分隔資源名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="4908e-120">Use commas to separate an array of resource names.</span></span>

```powershell
Find-DscResource -Name xWebsite, xWebApplication, xWebSiteDefaults
```

```Output
Name               Version    ModuleName            Repository
----               -------    ----------            ----------
xWebApplication    2.6.0.0    xWebAdministration    PSGallery
xWebsite           2.6.0.0    xWebAdministration    PSGallery
xWebSiteDefaults   2.6.0.0    xWebAdministration    PSGallery
```

<span data-ttu-id="4908e-121">`Find-DscResource` 使用 **Name** 參數來尋找指定的 DSC 資源陣列。</span><span class="sxs-lookup"><span data-stu-id="4908e-121">`Find-DscResource` uses the **Name** parameter to find the specified array of DSC resources.</span></span>

### <span data-ttu-id="4908e-122">範例3：尋找 DSC 資源並加以安裝</span><span class="sxs-lookup"><span data-stu-id="4908e-122">Example 3: Find a DSC resource and install it</span></span>

<span data-ttu-id="4908e-123">`Find-DscResource` 尋找 DSC 資源，並將該物件向下傳送要安裝的管線。</span><span class="sxs-lookup"><span data-stu-id="4908e-123">`Find-DscResource` locates a DSC resource and sends the object down the pipeline to be installed.</span></span>
<span data-ttu-id="4908e-124">安裝之後，請使用 `Get-InstalledModule` 來查看結果。</span><span class="sxs-lookup"><span data-stu-id="4908e-124">After the installation, use `Get-InstalledModule` to view the results.</span></span>

<span data-ttu-id="4908e-125">相同模組中的多個資源可以向下傳送至 `Install-Module` 。</span><span class="sxs-lookup"><span data-stu-id="4908e-125">Multiple resources from the same module can be sent down the pipeline to the `Install-Module`.</span></span>
<span data-ttu-id="4908e-126">`Install-Module` 嘗試只安裝一次模組。</span><span class="sxs-lookup"><span data-stu-id="4908e-126">`Install-Module` attempts to only install the module once.</span></span>

```powershell
Find-DscResource -Name xWebsite | Install-Module
```

<span data-ttu-id="4908e-127">`Find-DscResource` 使用 **Name** 參數來尋找名為 **xWebsite** 的資源。</span><span class="sxs-lookup"><span data-stu-id="4908e-127">`Find-DscResource` uses the **Name** parameter to find the resource named **xWebsite** .</span></span> <span data-ttu-id="4908e-128">物件會向下傳送至 `Install-Module` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4908e-128">The object is sent down the pipeline to the `Install-Module` cmdlet.</span></span> <span data-ttu-id="4908e-129">`Install-Module` 安裝資源的 **>xwebadministration** 模組。</span><span class="sxs-lookup"><span data-stu-id="4908e-129">`Install-Module` installs the **xWebAdministration** module for the resource.</span></span>

### <span data-ttu-id="4908e-130">範例4：尋找模組中的所有 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="4908e-130">Example 4: Find all DSC resources in a module</span></span>

<span data-ttu-id="4908e-131">`Find-DscResource` 尋找包含在指定模組中的所有 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="4908e-131">`Find-DscResource` finds all the DSC resources contained in a specified module.</span></span> <span data-ttu-id="4908e-132">預設會顯示目前的版本。</span><span class="sxs-lookup"><span data-stu-id="4908e-132">By default, the current version is displayed.</span></span> <span data-ttu-id="4908e-133">若要顯示其他版本，請使用 **allversions 進行篩選** 或 **RequiredVersions** 參數。</span><span class="sxs-lookup"><span data-stu-id="4908e-133">To display other versions, use the **AllVersions** or **RequiredVersions** parameters.</span></span>

```powershell
Find-DscResource -ModuleName xWebAdministration
```

```Output
Name                                Version    ModuleName              Repository
----                                -------    ----------              ----------
WebApplicationHandler               2.6.0.0    xWebAdministration      PSGallery
xIisFeatureDelegation               2.6.0.0    xWebAdministration      PSGallery
xIisHandler                         2.6.0.0    xWebAdministration      PSGallery
xIisLogging                         2.6.0.0    xWebAdministration      PSGallery
```

<span data-ttu-id="4908e-134">`Find-DscResource` 使用 **ModuleName** 參數來指定 **>xwebadministration** ，並尋找模組中包含的 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="4908e-134">`Find-DscResource` uses the **ModuleName** parameter to specify the **xWebAdministration** and find the DSC resources contained in the module.</span></span> <span data-ttu-id="4908e-135">會顯示每個資源的目前版本。</span><span class="sxs-lookup"><span data-stu-id="4908e-135">The current version of each resource is displayed.</span></span>

### <span data-ttu-id="4908e-136">範例5：依標記和所需版本尋找 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="4908e-136">Example 5: Find a DSC resource by tag and required version</span></span>

<span data-ttu-id="4908e-137">您可以使用 parameters **標記** 和 **RequiredVersion** 來找出 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="4908e-137">DSC resources can be located using the parameters **Tag** and **RequiredVersion** .</span></span> <span data-ttu-id="4908e-138">**標記** 會顯示存放庫中包含指定標籤的每個資源目前的版本。</span><span class="sxs-lookup"><span data-stu-id="4908e-138">**Tag** displays the current version of every resource that contains the specified tag in the repository.</span></span>
<span data-ttu-id="4908e-139">**RequiredVersion** 需要 **ModuleName** 參數，而 **Name** 參數是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="4908e-139">**RequiredVersion** needs the **ModuleName** parameter and the **Name** parameter is optional.</span></span> <span data-ttu-id="4908e-140">**Name** 和 **ModuleName** 參數會限制輸出。</span><span class="sxs-lookup"><span data-stu-id="4908e-140">The **Name** and **ModuleName** parameters limit the output.</span></span> <span data-ttu-id="4908e-141">使用 **allversions 進行篩選** 參數來顯示 DSC 資源的可用版本。</span><span class="sxs-lookup"><span data-stu-id="4908e-141">Use the **AllVersions** parameter to display a DSC resource's available versions.</span></span>

```powershell
Find-DscResource -ModuleName xWebAdministration -Tag DSC -RequiredVersion 1.20
```

```output
Name                    Version    ModuleName             Repository
----                    -------    ----------             ----------
xIisFeatureDelegation   1.20.0.0   xWebAdministration     PSGallery
xIisHandler             1.20.0.0   xWebAdministration     PSGallery
xIisLogging             1.20.0.0   xWebAdministration     PSGallery
xIisMimeTypeMapping     1.20.0.0   xWebAdministration     PSGallery
```

### <span data-ttu-id="4908e-142">範例6：使用篩選準則尋找資源</span><span class="sxs-lookup"><span data-stu-id="4908e-142">Example 6: Find a resource by using a filter</span></span>

<span data-ttu-id="4908e-143">`Find-DscResource` 尋找所有資源，並使用 **篩選** 參數來指定依 **網域** 的結果。</span><span class="sxs-lookup"><span data-stu-id="4908e-143">`Find-DscResource` finds all resources and uses the **Filter** parameter to specify the results by **Domain** .</span></span> <span data-ttu-id="4908e-144">**篩選** 參數會在物件的描述或模組名稱中尋找篩選值。</span><span class="sxs-lookup"><span data-stu-id="4908e-144">The **Filter** parameter finds the filter value in the object's description or module name.</span></span> <span data-ttu-id="4908e-145">使用 `Select-Object` Cmdlet 來查看物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="4908e-145">Use the `Select-Object` cmdlet to view an object's properties.</span></span>

```powershell
Find-DscResource -Filter Domain
```

```output
Name                    Version    ModuleName                 Repository
----                    -------    ----------                 ---------
xComputer               4.1.0.0    xComputerManagement        PSGallery
Computer                6.4.0.0    ComputerManagementDsc      PSGallery
xDSCDomainjoin          1.1        xDSCDomainjoin             PSGallery
xDisk                   1.0        xDisk                      PSGallery
xDSCFirewall            1.6.21     xDSCFirewall               PSGallery
dmAwsTagInstance        1.0.1      domainAwsDSCResources      PSGallery
```

## <span data-ttu-id="4908e-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4908e-146">PARAMETERS</span></span>

### <span data-ttu-id="4908e-147">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="4908e-147">-AllowPrerelease</span></span>

<span data-ttu-id="4908e-148">在結果中包含標示為發行前版本的資源。</span><span class="sxs-lookup"><span data-stu-id="4908e-148">Includes resources marked as a prerelease in the results.</span></span>

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4908e-149">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="4908e-149">-AllVersions</span></span>

<span data-ttu-id="4908e-150">**Allversions 進行篩選** 參數會顯示 DSC 資源的每個可用版本。</span><span class="sxs-lookup"><span data-stu-id="4908e-150">The **AllVersions** parameter displays each of a DSC resource's available versions.</span></span> <span data-ttu-id="4908e-151">您無法搭配 **MinimumVersion** 、 **MaximumVersion** 或 **RequiredVersion** 參數使用 **allversions 進行篩選** 參數。</span><span class="sxs-lookup"><span data-stu-id="4908e-151">You can't use the **AllVersions** parameter with the **MinimumVersion** , **MaximumVersion** , or **RequiredVersion** parameters.</span></span>

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

### <span data-ttu-id="4908e-152">-Filter</span><span class="sxs-lookup"><span data-stu-id="4908e-152">-Filter</span></span>

<span data-ttu-id="4908e-153">根據 **PackageManagement** 提供者的搜尋語法尋找資源。</span><span class="sxs-lookup"><span data-stu-id="4908e-153">Finds resources based on the **PackageManagement** provider's search syntax.</span></span> <span data-ttu-id="4908e-154">例如，在 [ **ModuleName** ] 和 [ **描述** ] 屬性中指定要搜尋的文字。</span><span class="sxs-lookup"><span data-stu-id="4908e-154">For example, specify words to search for within the **ModuleName** and **Description** properties.</span></span>

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

### <span data-ttu-id="4908e-155">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="4908e-155">-MaximumVersion</span></span>

<span data-ttu-id="4908e-156">指定要包含在結果中之資源的最大版本。</span><span class="sxs-lookup"><span data-stu-id="4908e-156">Specifies the maximum version of the resource to include in results.</span></span> <span data-ttu-id="4908e-157">無法在同一個命令中使用 **MaximumVersion** 和 **RequiredVersion** 參數。</span><span class="sxs-lookup"><span data-stu-id="4908e-157">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="4908e-158">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="4908e-158">-MinimumVersion</span></span>

<span data-ttu-id="4908e-159">指定要包含在結果中之資源的最小版本。</span><span class="sxs-lookup"><span data-stu-id="4908e-159">Specifies the minimum version of the resource to include in results.</span></span> <span data-ttu-id="4908e-160">**MinimumVersion** 和 **RequiredVersion** 參數無法在相同的命令中使用。</span><span class="sxs-lookup"><span data-stu-id="4908e-160">The **MinimumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="4908e-161">-ModuleName</span><span class="sxs-lookup"><span data-stu-id="4908e-161">-ModuleName</span></span>

<span data-ttu-id="4908e-162">指定包含 DSC 資源的模組。</span><span class="sxs-lookup"><span data-stu-id="4908e-162">Specifies a module that contains the DSC resource.</span></span>

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

### <span data-ttu-id="4908e-163">-Name</span><span class="sxs-lookup"><span data-stu-id="4908e-163">-Name</span></span>

<span data-ttu-id="4908e-164">指定資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="4908e-164">Specifies the name of a resource.</span></span> <span data-ttu-id="4908e-165">預設值為 [所有資源]。</span><span class="sxs-lookup"><span data-stu-id="4908e-165">The default is all resources.</span></span> <span data-ttu-id="4908e-166">使用逗號來分隔資源名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="4908e-166">Use commas to separate an array of resource names.</span></span>

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

### <span data-ttu-id="4908e-167">-Proxy</span><span class="sxs-lookup"><span data-stu-id="4908e-167">-Proxy</span></span>

<span data-ttu-id="4908e-168">為要求指定 proxy 伺服器，而不是直接連線到網際網路資源。</span><span class="sxs-lookup"><span data-stu-id="4908e-168">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="4908e-169">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="4908e-169">-ProxyCredential</span></span>

<span data-ttu-id="4908e-170">指定具有使用 **proxy** 參數中所指定 proxy 伺服器之許可權的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="4908e-170">Specifies a user account with permission to use the proxy server specified in the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="4908e-171">-Repository</span><span class="sxs-lookup"><span data-stu-id="4908e-171">-Repository</span></span>

<span data-ttu-id="4908e-172">指定要搜尋資源的儲存機制。</span><span class="sxs-lookup"><span data-stu-id="4908e-172">Specifies a repository to search for resources.</span></span> <span data-ttu-id="4908e-173">使用逗號來分隔存放庫名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="4908e-173">Use commas to separate an array of repository names.</span></span>

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

### <span data-ttu-id="4908e-174">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="4908e-174">-RequiredVersion</span></span>

<span data-ttu-id="4908e-175">指定要包含在結果中的模組確切版本號碼。</span><span class="sxs-lookup"><span data-stu-id="4908e-175">Specifies the module's exact version number to include in the results.</span></span> <span data-ttu-id="4908e-176">**RequiredVersion** 和 **MinimumVersion** 參數無法在相同的命令中使用。</span><span class="sxs-lookup"><span data-stu-id="4908e-176">The **RequiredVersion** and the **MinimumVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="4908e-177">-Tag</span><span class="sxs-lookup"><span data-stu-id="4908e-177">-Tag</span></span>

<span data-ttu-id="4908e-178">指定將存放庫中的模組分類的標記。</span><span class="sxs-lookup"><span data-stu-id="4908e-178">Specifies tags that categorize modules in a repository.</span></span> <span data-ttu-id="4908e-179">使用逗號來分隔標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="4908e-179">Use commas to separate an array of tags.</span></span>

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

### <span data-ttu-id="4908e-180">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4908e-180">CommonParameters</span></span>

<span data-ttu-id="4908e-181">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="4908e-181">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4908e-182">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="4908e-182">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4908e-183">輸入</span><span class="sxs-lookup"><span data-stu-id="4908e-183">INPUTS</span></span>

## <span data-ttu-id="4908e-184">輸出</span><span class="sxs-lookup"><span data-stu-id="4908e-184">OUTPUTS</span></span>

### <span data-ttu-id="4908e-185">PSGetDscResourceInfo</span><span class="sxs-lookup"><span data-stu-id="4908e-185">PSGetDscResourceInfo</span></span>

<span data-ttu-id="4908e-186">`Find-DscResource` 傳回 **PSGetDscResourceInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="4908e-186">`Find-DscResource` returns a **PSGetDscResourceInfo** object.</span></span>

## <span data-ttu-id="4908e-187">注意</span><span class="sxs-lookup"><span data-stu-id="4908e-187">NOTES</span></span>

## <span data-ttu-id="4908e-188">相關連結</span><span class="sxs-lookup"><span data-stu-id="4908e-188">RELATED LINKS</span></span>

[<span data-ttu-id="4908e-189">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="4908e-189">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="4908e-190">Install-Module</span><span class="sxs-lookup"><span data-stu-id="4908e-190">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="4908e-191">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="4908e-191">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="4908e-192">Select-Object</span><span class="sxs-lookup"><span data-stu-id="4908e-192">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="4908e-193">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="4908e-193">Uninstall-Module</span></span>](Uninstall-Module.md)
