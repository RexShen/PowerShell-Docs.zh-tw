---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 03/11/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-module?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Module
ms.openlocfilehash: 5795d48b2b76b4853d80d0cd79cb99d62332a39b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204291"
---
# <span data-ttu-id="eff91-103">Find-Module</span><span class="sxs-lookup"><span data-stu-id="eff91-103">Find-Module</span></span>

## <span data-ttu-id="eff91-104">概要</span><span class="sxs-lookup"><span data-stu-id="eff91-104">SYNOPSIS</span></span>
<span data-ttu-id="eff91-105">在存放庫中尋找符合指定準則的模組。</span><span class="sxs-lookup"><span data-stu-id="eff91-105">Finds modules in a repository that match specified criteria.</span></span>

## <span data-ttu-id="eff91-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="eff91-106">SYNTAX</span></span>

### <span data-ttu-id="eff91-107">全部</span><span class="sxs-lookup"><span data-stu-id="eff91-107">All</span></span>

```
Find-Module [[-Name] <string[]>] [-MinimumVersion <string>] [-MaximumVersion <string>]
 [-RequiredVersion <string>] [-AllVersions] [-IncludeDependencies] [-Filter <string>]
 [-Tag <string[]>] [-Includes <string[]>] [-DscResource <string[]>] [-RoleCapability <string[]>]
 [-Command <string[]>] [-Proxy <uri>] [-ProxyCredential <pscredential>] [-Repository <string[]>]
 [-Credential <pscredential>] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="eff91-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="eff91-108">DESCRIPTION</span></span>

<span data-ttu-id="eff91-109">此 `Find-Module` Cmdlet 會在存放庫中尋找符合指定準則的模組。</span><span class="sxs-lookup"><span data-stu-id="eff91-109">The `Find-Module` cmdlet finds modules in a repository that match the specified criteria.</span></span>
<span data-ttu-id="eff91-110">`Find-Module` 傳回所找到的每個模組的 **PSRepositoryItemInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="eff91-110">`Find-Module` returns a **PSRepositoryItemInfo** object for each module it finds.</span></span> <span data-ttu-id="eff91-111">物件可以向下傳送至 Cmdlet （例如） `Install-Module` 。</span><span class="sxs-lookup"><span data-stu-id="eff91-111">The objects can be sent down the pipeline to cmdlets such as `Install-Module`.</span></span>

<span data-ttu-id="eff91-112">第一次 `Find-Module` 嘗試使用存放庫時，系統可能會提示您安裝更新。</span><span class="sxs-lookup"><span data-stu-id="eff91-112">The first time `Find-Module` attempts to use a repository, you might be prompted to install updates.</span></span>
<span data-ttu-id="eff91-113">如果未向 Cmdlet 註冊存放庫來源 `Register-PSRepository` ，則會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="eff91-113">If the repository source is not registered with `Register-PSRepository` cmdlet, an error is returned.</span></span>

<span data-ttu-id="eff91-114">`Find-Module` 如果未使用任何參數來限制版本，則會傳回最新版本的模組。</span><span class="sxs-lookup"><span data-stu-id="eff91-114">`Find-Module` returns the newest version of a module if no parameters are used that limit the version.</span></span> <span data-ttu-id="eff91-115">若要取得存放庫的模組版本清單，請使用參數 **allversions 進行篩選** 。</span><span class="sxs-lookup"><span data-stu-id="eff91-115">To get a repository's list of a module's versions, use the parameter **AllVersions** .</span></span>

<span data-ttu-id="eff91-116">如果指定了 **MinimumVersion** 參數， `Find-Module` 會傳回等於或大於最小值的模組版本。</span><span class="sxs-lookup"><span data-stu-id="eff91-116">If the **MinimumVersion** parameter is specified, `Find-Module` returns the module's version that is equal to or greater than the minimum.</span></span> <span data-ttu-id="eff91-117">如果存放庫中有較新的版本可用，則會傳回較新的版本。</span><span class="sxs-lookup"><span data-stu-id="eff91-117">If there is a newer version available in the repository, the newer version is returned.</span></span>

<span data-ttu-id="eff91-118">如果指定了 **MaximumVersion** 參數，則 `Find-Module` 會傳回不超過所指定版本之模組的最新版本。</span><span class="sxs-lookup"><span data-stu-id="eff91-118">If the **MaximumVersion** parameter is specified, `Find-Module` returns the newest version of the module that does not exceed the version specified.</span></span>

<span data-ttu-id="eff91-119">如果指定 **RequiredVersion** 參數，則 `Find-Module` 只會傳回與指定版本完全相符的模組版本。</span><span class="sxs-lookup"><span data-stu-id="eff91-119">If the **RequiredVersion** parameter is specified, `Find-Module` only returns the module version that is an exact match to the specified version.</span></span> <span data-ttu-id="eff91-120">`Find-Module` 搜尋所有可用的模組，因為可能會發生來源之間的名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="eff91-120">`Find-Module` searches through all available modules, because name conflicts between sources can occur.</span></span>

<span data-ttu-id="eff91-121">下列範例使用 [PowerShell 資源庫](https://www.powershellgallery.com/) 作為唯一的已註冊存放庫。</span><span class="sxs-lookup"><span data-stu-id="eff91-121">The following examples use the [PowerShell Gallery](https://www.powershellgallery.com/) as the only registered repository.</span></span> <span data-ttu-id="eff91-122">`Get-PSRepository` 顯示已註冊的存放庫。</span><span class="sxs-lookup"><span data-stu-id="eff91-122">`Get-PSRepository` displays the registered repositories.</span></span> <span data-ttu-id="eff91-123">如果您有多個已註冊的存放庫，請使用 `-Repository` 參數來指定存放庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="eff91-123">If you have multiple registered repositories, use the `-Repository` parameter to specify the repository's name.</span></span>

## <span data-ttu-id="eff91-124">範例</span><span class="sxs-lookup"><span data-stu-id="eff91-124">EXAMPLES</span></span>

### <span data-ttu-id="eff91-125">範例1：依名稱尋找模組</span><span class="sxs-lookup"><span data-stu-id="eff91-125">Example 1: Find a module by name</span></span>

<span data-ttu-id="eff91-126">此範例會尋找預設存放庫中的模組。</span><span class="sxs-lookup"><span data-stu-id="eff91-126">This example finds a module in the default repository.</span></span>

```powershell
Find-Module -Name PowerShellGet
```

```Output
Version   Name              Repository           Description
-------   ----              ----------           -----------
2.1.0     PowerShellGet     PSGallery            PowerShell module with commands for discovering...
```

<span data-ttu-id="eff91-127">此 `Find-Module` Cmdlet 會使用 **Name** 參數來指定 **PowerShellGet** 模組。</span><span class="sxs-lookup"><span data-stu-id="eff91-127">The `Find-Module` cmdlet uses the **Name** parameter to specify the **PowerShellGet** module.</span></span>

### <span data-ttu-id="eff91-128">範例2：尋找具有類似名稱的模組</span><span class="sxs-lookup"><span data-stu-id="eff91-128">Example 2: Find modules with similar names</span></span>

<span data-ttu-id="eff91-129">此範例使用星號 (`*`) 萬用字元來尋找具有類似名稱的模組。</span><span class="sxs-lookup"><span data-stu-id="eff91-129">This example uses the asterisk (`*`) wildcard to find modules with similar names.</span></span>

```powershell
Find-Module -Name PowerShell*
```

```Output
Version   Name                            Repository    Description
-------   ----                            ----------    -----------
0.4.0     powershell-yaml                 PSGallery     Powershell module for serializing and...
2.1.0     PowerShellGet                   PSGallery     PowerShell module with commands for...
1.9       Powershell.Helper.Extension     PSGallery     # Powershell.Helper.Extension...
3.1       PowerShellHumanizer             PSGallery     PowerShell Humanizer wraps Humanizer...
4.0       PowerShellISEModule             PSGallery     a module that adds capability to the ISE
```

<span data-ttu-id="eff91-130">此 `Find-Module` Cmdlet 會使用 **Name** 參數搭配星號 (`*`) 萬用字元來尋找包含 **PowerShell** 的所有模組。</span><span class="sxs-lookup"><span data-stu-id="eff91-130">The `Find-Module` cmdlet uses the **Name** parameter with the asterisk (`*`) wildcard to find all modules that contain **PowerShell** .</span></span>

### <span data-ttu-id="eff91-131">範例3：依最小版本尋找模組</span><span class="sxs-lookup"><span data-stu-id="eff91-131">Example 3: Find a module by minimum version</span></span>

<span data-ttu-id="eff91-132">此範例會搜尋模組的最小版本。</span><span class="sxs-lookup"><span data-stu-id="eff91-132">This example searches for a module's minimum version.</span></span> <span data-ttu-id="eff91-133">如果存放庫包含較新版本的模組，則會傳回較新的版本。</span><span class="sxs-lookup"><span data-stu-id="eff91-133">If the repository contains a newer version of the module, the newer version is returned.</span></span>

```powershell
Find-Module -Name PowerShellGet -MinimumVersion 1.6.5
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
2.1.0     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

<span data-ttu-id="eff91-134">此 `Find-Module` Cmdlet 會使用 **Name** 參數來指定 **PowerShellGet** 模組。</span><span class="sxs-lookup"><span data-stu-id="eff91-134">The `Find-Module` cmdlet uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="eff91-135">**MinimumVersion** 指定版本 **1.6.5** 。</span><span class="sxs-lookup"><span data-stu-id="eff91-135">The **MinimumVersion** specifies version **1.6.5** .</span></span> <span data-ttu-id="eff91-136">`Find-Module` 會傳回 PowerShellGet 版本 **2.1.0** ，因為它超過最小版本，而且是最新版本。</span><span class="sxs-lookup"><span data-stu-id="eff91-136">`Find-Module` returns PowerShellGet version **2.1.0** because it exceeds the minimum version and is the most current version.</span></span>

### <span data-ttu-id="eff91-137">範例4：依特定版本尋找模組</span><span class="sxs-lookup"><span data-stu-id="eff91-137">Example 4: Find a module by specific version</span></span>

<span data-ttu-id="eff91-138">這個範例會傳回代表模組特定版本的物件。</span><span class="sxs-lookup"><span data-stu-id="eff91-138">This example returns an object that represents a module's specific version.</span></span> <span data-ttu-id="eff91-139">如果找不到指定的版本，則會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="eff91-139">If the specified version is not found, an error is returned.</span></span>

```powershell
Find-Module -Name PowerShellGet -RequiredVersion 1.6.5
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
1.6.5     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

<span data-ttu-id="eff91-140">此 `Find-Module` Cmdlet 會使用 **Name** 參數來指定 **PowerShellGet** 模組。</span><span class="sxs-lookup"><span data-stu-id="eff91-140">The `Find-Module` cmdlet uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="eff91-141">**RequiredVersion** 參數指定 version **1.6.5** 。</span><span class="sxs-lookup"><span data-stu-id="eff91-141">The **RequiredVersion** parameter specifies version **1.6.5** .</span></span>

### <span data-ttu-id="eff91-142">範例5：在特定存放庫中尋找模組</span><span class="sxs-lookup"><span data-stu-id="eff91-142">Example 5: Find a module in a specific repository</span></span>

<span data-ttu-id="eff91-143">此範例會使用存放 **庫** 參數來尋找特定存放庫中的模組。</span><span class="sxs-lookup"><span data-stu-id="eff91-143">This example uses the **Repository** parameter to find a module in a specific repository.</span></span>

```powershell
Find-Module -Name PowerShellGet -Repository PSGallery
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
2.1.0     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

<span data-ttu-id="eff91-144">此 `Find-Module` Cmdlet 會使用 **Name** 參數來指定 **PowerShellGet** 模組。</span><span class="sxs-lookup"><span data-stu-id="eff91-144">The `Find-Module` cmdlet uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="eff91-145">存放 **庫** 參數指定要搜尋 **PSGallery** 存放庫。</span><span class="sxs-lookup"><span data-stu-id="eff91-145">The **Repository** parameter specifies to search the **PSGallery** repository.</span></span>

### <span data-ttu-id="eff91-146">範例6：在多個存放庫中尋找模組</span><span class="sxs-lookup"><span data-stu-id="eff91-146">Example 6: Find a module in multiple repositories</span></span>

<span data-ttu-id="eff91-147">這個範例會使用 `Register-PSRepository` 來指定存放庫。</span><span class="sxs-lookup"><span data-stu-id="eff91-147">This example uses the `Register-PSRepository` to specify a repository.</span></span> <span data-ttu-id="eff91-148">`Find-Module` 使用存放庫來搜尋模組。</span><span class="sxs-lookup"><span data-stu-id="eff91-148">`Find-Module` uses the repository to search for a module.</span></span>

```powershell
Register-PSRepository -Name MySource -SourceLocation https://www.myget.org/F/powershellgetdemo/
Find-Module -Name Contoso* -Repository PSGallery, MySource
```

```Output
Repository    Version   Name             Description
----------    -------   ----             -----------
PSGallery     2.0.0.0   ContosoServer    Cmdlets and DSC resources for managing Contoso Server...
MySource      1.2.0.0   ContosoClient    Cmdlets and DSC resources for managing Contoso Client...
```

<span data-ttu-id="eff91-149">`Register-PSRepository`Cmdlet 會註冊新的存放庫。</span><span class="sxs-lookup"><span data-stu-id="eff91-149">The `Register-PSRepository` cmdlet registers a new repository.</span></span> <span data-ttu-id="eff91-150">**Name** 參數會指派名稱 **MySource** 。</span><span class="sxs-lookup"><span data-stu-id="eff91-150">The **Name** parameter assigns the name **MySource** .</span></span> <span data-ttu-id="eff91-151">**SourceLocation** 參數會指定存放庫的位址。</span><span class="sxs-lookup"><span data-stu-id="eff91-151">The **SourceLocation** parameter specifies the repository's address.</span></span>

<span data-ttu-id="eff91-152">此 `Find-Module` Cmdlet 會使用 **Name** 參數搭配星號 (`*`) 萬用字元來指定 **Contoso** 模組。</span><span class="sxs-lookup"><span data-stu-id="eff91-152">The `Find-Module` cmdlet uses the **Name** parameter with the asterisk (`*`) wildcard to specify the **Contoso** module.</span></span> <span data-ttu-id="eff91-153">存放 **庫** 參數指定要搜尋兩個儲存機制： **PSGallery** 和 **MySource** 。</span><span class="sxs-lookup"><span data-stu-id="eff91-153">The **Repository** parameter specifies to search two repositories, **PSGallery** and **MySource** .</span></span>

### <span data-ttu-id="eff91-154">範例7：尋找包含 DSC 資源的模組</span><span class="sxs-lookup"><span data-stu-id="eff91-154">Example 7: Find a module that contains a DSC resource</span></span>

<span data-ttu-id="eff91-155">此命令會傳回包含 DSC 資源的模組。</span><span class="sxs-lookup"><span data-stu-id="eff91-155">This command returns modules that contain DSC resources.</span></span> <span data-ttu-id="eff91-156">**Include** 參數有四個預先定義的功能，可用來搜尋存放庫。</span><span class="sxs-lookup"><span data-stu-id="eff91-156">The **Includes** parameter has four predefined functionalities that are used to search the repository.</span></span> <span data-ttu-id="eff91-157">使用 tab 鍵完成以顯示 **包含** 參數所支援的四項功能。</span><span class="sxs-lookup"><span data-stu-id="eff91-157">Use tab-complete to display the four functionalities supported by the **Includes** parameter.</span></span>

```powershell
Find-Module -Repository PSGallery -Includes DscResource
```

```Output
Version     Name                            Repository    Description
-------     ----                            ----------    -----------
2.7.0       Carbon                          PSGallery     Carbon is a PowerShell module...
8.5.0.0     xPSDesiredStateConfiguration    PSGallery     The xPSDesiredStateConfiguration module...
1.3.1       PackageManagement               PSGallery     PackageManagement (a.k.a. OneGet) is...
2.7.0.0     xWindowsUpdate                  PSGallery     Module with DSC Resources...
3.2.0.0     xCertificate                    PSGallery     This module includes DSC resources...
3.1.0.0     xPowerShellExecutionPolicy      PSGallery     This DSC resource can change the user...
```

<span data-ttu-id="eff91-158">此 `Find-Module` Cmdlet 會使用存放 **庫** 參數來搜尋存放庫 **PSGallery** 。</span><span class="sxs-lookup"><span data-stu-id="eff91-158">The `Find-Module` cmdlet uses the **Repository** parameter to search the repository, **PSGallery** .</span></span>
<span data-ttu-id="eff91-159">**Include** 參數會指定 **DscResource** ，這是參數可以在儲存機制中搜尋的功能。</span><span class="sxs-lookup"><span data-stu-id="eff91-159">The **Includes** parameter specifies **DscResource** , which is a functionality that the parameter can search for in the repository.</span></span>

### <span data-ttu-id="eff91-160">範例8：尋找具有篩選的模組</span><span class="sxs-lookup"><span data-stu-id="eff91-160">Example 8: Find a module with a filter</span></span>

<span data-ttu-id="eff91-161">在此範例中，若要尋找模組，會使用篩選準則來搜尋存放庫。</span><span class="sxs-lookup"><span data-stu-id="eff91-161">In this example, to find modules, a filter is used to search the repository.</span></span>

<span data-ttu-id="eff91-162">針對以 NuGet 為基礎的存放庫， **篩選** 參數會搜尋引數的名稱、描述和標記。</span><span class="sxs-lookup"><span data-stu-id="eff91-162">For a NuGet-based repository, the **Filter** parameter searches through the name, description, and tags for the argument.</span></span>

```powershell
Find-Module -Filter AppDomain
```

```Output
Version    Name              Repository           Description
-------    ----              ----------           -----------
1.0.0.0  AppDomainConfig     PSGallery            Manipulate AppDomain configuration...
1.1.0    ClassExplorer       PSGallery            Quickly search the AppDomain for classes...
```

<span data-ttu-id="eff91-163">此 `Find-Module` Cmdlet 會使用 **篩選** 參數來搜尋 **AppDomain** 的儲存機制。</span><span class="sxs-lookup"><span data-stu-id="eff91-163">The `Find-Module` cmdlet uses the **Filter** parameter to search the repository for **AppDomain** .</span></span>

## <span data-ttu-id="eff91-164">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="eff91-164">PARAMETERS</span></span>

### <span data-ttu-id="eff91-165">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="eff91-165">-AllowPrerelease</span></span>

<span data-ttu-id="eff91-166">包含在標記為發行前版本的結果模組中。</span><span class="sxs-lookup"><span data-stu-id="eff91-166">Includes in the results modules marked as a pre-release.</span></span>

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

### <span data-ttu-id="eff91-167">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="eff91-167">-AllVersions</span></span>

<span data-ttu-id="eff91-168">指定要在結果中包含模組的所有版本。</span><span class="sxs-lookup"><span data-stu-id="eff91-168">Specifies to include all versions of a module in the results.</span></span> <span data-ttu-id="eff91-169">您無法搭配 **MinimumVersion** 、 **MaximumVersion** 或 **RequiredVersion** 參數使用 **allversions 進行篩選** 參數。</span><span class="sxs-lookup"><span data-stu-id="eff91-169">You cannot use the **AllVersions** parameter with the **MinimumVersion** , **MaximumVersion** , or **RequiredVersion** parameters.</span></span>

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

### <span data-ttu-id="eff91-170">-Command</span><span class="sxs-lookup"><span data-stu-id="eff91-170">-Command</span></span>

<span data-ttu-id="eff91-171">指定要在模組中尋找的命令陣列。</span><span class="sxs-lookup"><span data-stu-id="eff91-171">Specifies an array of commands to find in modules.</span></span> <span data-ttu-id="eff91-172">命令可以是函數或工作流程。</span><span class="sxs-lookup"><span data-stu-id="eff91-172">A command can be a function or workflow.</span></span>

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

### <span data-ttu-id="eff91-173">-Credential</span><span class="sxs-lookup"><span data-stu-id="eff91-173">-Credential</span></span>

<span data-ttu-id="eff91-174">指定擁有為指定的套件提供者或來源安裝模組之許可權的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="eff91-174">Specifies a user account that has rights to install a module for a specified package provider or source.</span></span>

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

### <span data-ttu-id="eff91-175">-DscResource</span><span class="sxs-lookup"><span data-stu-id="eff91-175">-DscResource</span></span>

<span data-ttu-id="eff91-176">指定包含 DSC 資源之模組的名稱或部分名稱。</span><span class="sxs-lookup"><span data-stu-id="eff91-176">Specifies the name, or part of the name, of modules that contain DSC resources.</span></span> <span data-ttu-id="eff91-177">根據 PowerShell 慣例，當您提供多個引數時，會執行 **或** 搜尋。</span><span class="sxs-lookup"><span data-stu-id="eff91-177">Per PowerShell conventions, performs an **OR** search when you provide multiple arguments.</span></span>

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

### <span data-ttu-id="eff91-178">-Filter</span><span class="sxs-lookup"><span data-stu-id="eff91-178">-Filter</span></span>

<span data-ttu-id="eff91-179">根據 **PackageManagement** 提供者特定的搜尋語法來指定篩選。</span><span class="sxs-lookup"><span data-stu-id="eff91-179">Specifies a filter based on the **PackageManagement** provider-specific search syntax.</span></span> <span data-ttu-id="eff91-180">針對 NuGet 模組，此參數相當於使用 [PowerShell 資源庫](https://www.powershellgallery.com/) 網站上的搜尋列來搜尋。</span><span class="sxs-lookup"><span data-stu-id="eff91-180">For NuGet modules, this parameter is the equivalent of searching by using the Search bar on the [PowerShell Gallery](https://www.powershellgallery.com/) website.</span></span>

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

### <span data-ttu-id="eff91-181">-Includedependencies 來</span><span class="sxs-lookup"><span data-stu-id="eff91-181">-IncludeDependencies</span></span>

<span data-ttu-id="eff91-182">指出此作業包含相依于 **Name** 參數中指定之模組的所有模組。</span><span class="sxs-lookup"><span data-stu-id="eff91-182">Indicates that this operation includes all modules that are dependent upon the module specified in the **Name** parameter.</span></span>

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

### <span data-ttu-id="eff91-183">-Include</span><span class="sxs-lookup"><span data-stu-id="eff91-183">-Includes</span></span>

<span data-ttu-id="eff91-184">只傳回包含特定類型之 PowerShell 功能的模組。</span><span class="sxs-lookup"><span data-stu-id="eff91-184">Returns only those modules that include specific kinds of PowerShell functionality.</span></span> <span data-ttu-id="eff91-185">例如，您可能只想要尋找包含 **DSCResource** 的模組。</span><span class="sxs-lookup"><span data-stu-id="eff91-185">For example, you might only want to find modules that include **DSCResource** .</span></span> <span data-ttu-id="eff91-186">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="eff91-186">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="eff91-187">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="eff91-187">Cmdlet</span></span>
- <span data-ttu-id="eff91-188">DscResource</span><span class="sxs-lookup"><span data-stu-id="eff91-188">DscResource</span></span>
- <span data-ttu-id="eff91-189">函式</span><span class="sxs-lookup"><span data-stu-id="eff91-189">Function</span></span>
- <span data-ttu-id="eff91-190">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="eff91-190">RoleCapability</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: DscResource, Cmdlet, Function, RoleCapability

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eff91-191">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="eff91-191">-MaximumVersion</span></span>

<span data-ttu-id="eff91-192">指定要包含在搜尋結果中的模組最大或最新版本。</span><span class="sxs-lookup"><span data-stu-id="eff91-192">Specifies the maximum, or latest, version of the module to include in the search results.</span></span>
<span data-ttu-id="eff91-193">無法在同一個命令中使用 **MaximumVersion** 和 **RequiredVersion** 。</span><span class="sxs-lookup"><span data-stu-id="eff91-193">**MaximumVersion** and **RequiredVersion** cannot be used in the same command.</span></span>

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

### <span data-ttu-id="eff91-194">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="eff91-194">-MinimumVersion</span></span>

<span data-ttu-id="eff91-195">指定要包含於結果中的模組最低版本。</span><span class="sxs-lookup"><span data-stu-id="eff91-195">Specifies the minimum version of the module to include in results.</span></span> <span data-ttu-id="eff91-196">**MinimumVersion** 和 **RequiredVersion** 無法在相同的命令中使用。</span><span class="sxs-lookup"><span data-stu-id="eff91-196">**MinimumVersion** and **RequiredVersion** cannot be used in the same command.</span></span>

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

### <span data-ttu-id="eff91-197">-Name</span><span class="sxs-lookup"><span data-stu-id="eff91-197">-Name</span></span>

<span data-ttu-id="eff91-198">指定要在存放庫中搜尋的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="eff91-198">Specifies the names of modules to search for in the repository.</span></span> <span data-ttu-id="eff91-199">接受以逗號分隔的模組名稱清單。</span><span class="sxs-lookup"><span data-stu-id="eff91-199">A comma-separated list of module names is accepted.</span></span> <span data-ttu-id="eff91-200">可使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="eff91-200">Wildcards are accepted.</span></span>

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

### <span data-ttu-id="eff91-201">-Proxy</span><span class="sxs-lookup"><span data-stu-id="eff91-201">-Proxy</span></span>

<span data-ttu-id="eff91-202">指定要求的 proxy 伺服器，而不是直接連接到網際網路資源。</span><span class="sxs-lookup"><span data-stu-id="eff91-202">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="eff91-203">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="eff91-203">-ProxyCredential</span></span>

<span data-ttu-id="eff91-204">指定具有使用 **Proxy** 參數所指定 Proxy 伺服器之權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="eff91-204">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="eff91-205">-Repository</span><span class="sxs-lookup"><span data-stu-id="eff91-205">-Repository</span></span>

<span data-ttu-id="eff91-206">使用存放 **庫** 參數來指定要搜尋模組的存放庫。</span><span class="sxs-lookup"><span data-stu-id="eff91-206">Use the **Repository** parameter to specify which repository to search for a module.</span></span> <span data-ttu-id="eff91-207">在註冊多個存放庫時使用。</span><span class="sxs-lookup"><span data-stu-id="eff91-207">Used when multiple repositories are registered.</span></span> <span data-ttu-id="eff91-208">接受以逗號分隔的存放庫清單。</span><span class="sxs-lookup"><span data-stu-id="eff91-208">Accepts a comma-separated list of repositories.</span></span> <span data-ttu-id="eff91-209">若要註冊存放庫，請使用 `Register-PSRepository` 。</span><span class="sxs-lookup"><span data-stu-id="eff91-209">To register a repository, use `Register-PSRepository`.</span></span> <span data-ttu-id="eff91-210">若要顯示已註冊的存放庫，請使用 `Get-PSRepository` 。</span><span class="sxs-lookup"><span data-stu-id="eff91-210">To display registered repositories, use `Get-PSRepository`.</span></span>

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

### <span data-ttu-id="eff91-211">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="eff91-211">-RequiredVersion</span></span>

<span data-ttu-id="eff91-212">指定要包含在結果中之模組的確切版本號碼。</span><span class="sxs-lookup"><span data-stu-id="eff91-212">Specifies the exact version number of the module to include in the results.</span></span> <span data-ttu-id="eff91-213">**RequiredVersion** 無法在與 **MinimumVersion** 或 **MaximumVersion** 相同的命令中使用。</span><span class="sxs-lookup"><span data-stu-id="eff91-213">**RequiredVersion** cannot be used in the same command as **MinimumVersion** or **MaximumVersion** .</span></span>

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

### <span data-ttu-id="eff91-214">-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="eff91-214">-RoleCapability</span></span>

<span data-ttu-id="eff91-215">指定角色功能的陣列。</span><span class="sxs-lookup"><span data-stu-id="eff91-215">Specifies an array of role capabilities.</span></span>

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

### <span data-ttu-id="eff91-216">-Tag</span><span class="sxs-lookup"><span data-stu-id="eff91-216">-Tag</span></span>

<span data-ttu-id="eff91-217">指定標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="eff91-217">Specifies an array of tags.</span></span> <span data-ttu-id="eff91-218">範例標記包括 **DesiredStateConfiguration** 、 **DSC** 、 **DSCResourceKit** 或 **PSModule** 。</span><span class="sxs-lookup"><span data-stu-id="eff91-218">Example tags include **DesiredStateConfiguration** , **DSC** , **DSCResourceKit** , or **PSModule** .</span></span>

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

### <span data-ttu-id="eff91-219">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="eff91-219">CommonParameters</span></span>

<span data-ttu-id="eff91-220">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="eff91-220">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="eff91-221">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="eff91-221">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="eff91-222">輸入</span><span class="sxs-lookup"><span data-stu-id="eff91-222">INPUTS</span></span>

### <span data-ttu-id="eff91-223">System.String[]</span><span class="sxs-lookup"><span data-stu-id="eff91-223">System.String[]</span></span>

### <span data-ttu-id="eff91-224">System.String</span><span class="sxs-lookup"><span data-stu-id="eff91-224">System.String</span></span>

### <span data-ttu-id="eff91-225">System.Uri</span><span class="sxs-lookup"><span data-stu-id="eff91-225">System.Uri</span></span>

### <span data-ttu-id="eff91-226">System.Management.Automation.PSCredential</span><span class="sxs-lookup"><span data-stu-id="eff91-226">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="eff91-227">輸出</span><span class="sxs-lookup"><span data-stu-id="eff91-227">OUTPUTS</span></span>

### <span data-ttu-id="eff91-228">PSRepositoryItemInfo</span><span class="sxs-lookup"><span data-stu-id="eff91-228">PSRepositoryItemInfo</span></span>

<span data-ttu-id="eff91-229">`Find-Module` 建立可將管線向下傳送至 Cmdlet 的 **PSRepositoryItemInfo** 物件，例如 `Install-Module` 。</span><span class="sxs-lookup"><span data-stu-id="eff91-229">`Find-Module` creates **PSRepositoryItemInfo** objects that can be sent down the pipeline to cmdlets such as `Install-Module`.</span></span>

## <span data-ttu-id="eff91-230">注意</span><span class="sxs-lookup"><span data-stu-id="eff91-230">NOTES</span></span>

<span data-ttu-id="eff91-231">此 Cmdlet 會在 powershell 5.0 或更新版本的 PowerShell、Windows 7 或 Windows 2008 R2 和更新版本的 Windows 上執行。</span><span class="sxs-lookup"><span data-stu-id="eff91-231">This cmdlet runs on PowerShell 5.0 or later releases of PowerShell, on Windows 7, or Windows 2008 R2 and later releases of Windows.</span></span>

## <span data-ttu-id="eff91-232">相關連結</span><span class="sxs-lookup"><span data-stu-id="eff91-232">RELATED LINKS</span></span>

[<span data-ttu-id="eff91-233">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="eff91-233">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="eff91-234">Install-Module</span><span class="sxs-lookup"><span data-stu-id="eff91-234">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="eff91-235">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="eff91-235">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="eff91-236">Save-Module</span><span class="sxs-lookup"><span data-stu-id="eff91-236">Save-Module</span></span>](Save-Module.md)

[<span data-ttu-id="eff91-237">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="eff91-237">Uninstall-Module</span></span>](Uninstall-Module.md)

[<span data-ttu-id="eff91-238">Update-Module</span><span class="sxs-lookup"><span data-stu-id="eff91-238">Update-Module</span></span>](Update-Module.md)

[<span data-ttu-id="eff91-239">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="eff91-239">Register-PSRepository</span></span>](Register-PSRepository.md)
