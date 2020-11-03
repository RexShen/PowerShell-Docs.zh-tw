---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/16/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Module
ms.openlocfilehash: 719eaa019dd721b156b26d2e38e8790e6b9af584
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203871"
---
# <span data-ttu-id="ade77-103">Update-Module</span><span class="sxs-lookup"><span data-stu-id="ade77-103">Update-Module</span></span>

## <span data-ttu-id="ade77-104">概要</span><span class="sxs-lookup"><span data-stu-id="ade77-104">SYNOPSIS</span></span>
<span data-ttu-id="ade77-105">將來自線上組件庫之指定模組的最新版本下載並安裝至本機電腦。</span><span class="sxs-lookup"><span data-stu-id="ade77-105">Downloads and installs the newest version of specified modules from an online gallery to the local computer.</span></span>

## <span data-ttu-id="ade77-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ade77-106">SYNTAX</span></span>

### <span data-ttu-id="ade77-107">全部</span><span class="sxs-lookup"><span data-stu-id="ade77-107">All</span></span>

```
Update-Module [[-Name] <String[]>] [-RequiredVersion <String>] [-MaximumVersion <String>]
 [-Credential <PSCredential>] [-Scope <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Force] [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ade77-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="ade77-108">DESCRIPTION</span></span>

<span data-ttu-id="ade77-109">`Update-Module`Cmdlet 會從線上元件庫安裝模組的最新版本。</span><span class="sxs-lookup"><span data-stu-id="ade77-109">The `Update-Module` cmdlet installs a module's newest version from an online gallery.</span></span> <span data-ttu-id="ade77-110">安裝之前，系統會提示您確認更新。</span><span class="sxs-lookup"><span data-stu-id="ade77-110">You're prompted to confirm the update before it's installed.</span></span> <span data-ttu-id="ade77-111">只有安裝在本機電腦上的模組才會安裝更新 `Install-Module` 。</span><span class="sxs-lookup"><span data-stu-id="ade77-111">Updates are installed only for modules that were installed on the local computer with `Install-Module`.</span></span> <span data-ttu-id="ade77-112">`Update-Module` 搜尋 `$env:PSModulePath` 已安裝的模組。</span><span class="sxs-lookup"><span data-stu-id="ade77-112">`Update-Module` searches `$env:PSModulePath` for installed modules.</span></span>

<span data-ttu-id="ade77-113">`Update-Module` 未指定參數時，會更新所有已安裝的模組。</span><span class="sxs-lookup"><span data-stu-id="ade77-113">`Update-Module` with no parameters specified updates all installed modules.</span></span> <span data-ttu-id="ade77-114">若要指定要更新的模組，請使用 **Name** 參數。</span><span class="sxs-lookup"><span data-stu-id="ade77-114">To specify a module to update, use the **Name** parameter.</span></span> <span data-ttu-id="ade77-115">您可以使用 **RequiredVersion** 參數來更新為模組的特定版本。</span><span class="sxs-lookup"><span data-stu-id="ade77-115">You can update to a module's specific version by using the **RequiredVersion** parameter.</span></span>

<span data-ttu-id="ade77-116">如果已安裝的模組已是最新版本，則不會更新模組。</span><span class="sxs-lookup"><span data-stu-id="ade77-116">If an installed module is already the newest version, the module isn't updated.</span></span> <span data-ttu-id="ade77-117">如果在中找不到模組 `$env:PSModulePath` ，則會顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="ade77-117">If the module isn't found in `$env:PSModulePath`, an error is displayed.</span></span>

<span data-ttu-id="ade77-118">若要顯示已安裝的模組，請使用 `Get-InstalledModule` 。</span><span class="sxs-lookup"><span data-stu-id="ade77-118">To display the installed modules, use `Get-InstalledModule`.</span></span>

## <span data-ttu-id="ade77-119">範例</span><span class="sxs-lookup"><span data-stu-id="ade77-119">EXAMPLES</span></span>

### <span data-ttu-id="ade77-120">範例 1：更新所有模組</span><span class="sxs-lookup"><span data-stu-id="ade77-120">Example 1: Update all modules</span></span>

<span data-ttu-id="ade77-121">此範例會將所有已安裝的模組更新為線上元件庫中的最新版本。</span><span class="sxs-lookup"><span data-stu-id="ade77-121">This example updates all installed modules to the newest version in an online gallery.</span></span>

```powershell
Update-Module
```

### <span data-ttu-id="ade77-122">範例 2：透過名稱更新模組</span><span class="sxs-lookup"><span data-stu-id="ade77-122">Example 2: Update a module by name</span></span>

<span data-ttu-id="ade77-123">此範例會將特定模組更新為線上元件庫中的最新版本。</span><span class="sxs-lookup"><span data-stu-id="ade77-123">This example updates a specific module to the newest version in an online gallery.</span></span>

```powershell
Update-Module -Name SpeculationControl
```

<span data-ttu-id="ade77-124">`Update-Module` 使用 **Name** 參數來更新特定模組（ **SpeculationControl** ）。</span><span class="sxs-lookup"><span data-stu-id="ade77-124">`Update-Module` uses the **Name** parameter to update a specific module, **SpeculationControl** .</span></span>

### <span data-ttu-id="ade77-125">範例3：查看 Update-Module 的執行</span><span class="sxs-lookup"><span data-stu-id="ade77-125">Example 3: View what-if Update-Module runs</span></span>

<span data-ttu-id="ade77-126">此範例會執行假設案例，以顯示執行時所發生的情況 `Update-Module` 。</span><span class="sxs-lookup"><span data-stu-id="ade77-126">This example does a what-if scenario to show what happens if `Update-Module` is run.</span></span> <span data-ttu-id="ade77-127">命令不會執行。</span><span class="sxs-lookup"><span data-stu-id="ade77-127">The command isn't run.</span></span>

```powershell
Update-Module -WhatIf
```

```Output
What if: Performing the operation "Update-Module" on target "Version '2.8.0' of module
  'Carbon', updating to version '2.8.1'".
What if: Performing the operation "Update-Module" on target "Version '1.0.10' of module
  'SpeculationControl', updating to version '1.0.14'".
```

<span data-ttu-id="ade77-128">`Update-Module` 使用 **WhatIf** 參數顯示如果已執行，會發生什麼事 `Update-Module` 。</span><span class="sxs-lookup"><span data-stu-id="ade77-128">`Update-Module` uses the **WhatIf** parameter display what would happen if `Update-Module` were run.</span></span>

### <span data-ttu-id="ade77-129">範例 4：將模組更新至指定版本</span><span class="sxs-lookup"><span data-stu-id="ade77-129">Example 4: Update a module to a specified version</span></span>

<span data-ttu-id="ade77-130">在此範例中，模組會更新為特定版本。</span><span class="sxs-lookup"><span data-stu-id="ade77-130">In this example, a module is updated to a specific version.</span></span> <span data-ttu-id="ade77-131">版本必須存在於線上元件庫中，否則會顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="ade77-131">The version must exist in the online gallery or an error is displayed.</span></span>

```powershell
Update-Module -Name SpeculationControl -RequiredVersion 1.0.14
```

<span data-ttu-id="ade77-132">`Update-Module` 使用 **Name** 參數來指定模組（ **SpeculationControl** ）。</span><span class="sxs-lookup"><span data-stu-id="ade77-132">`Update-Module` uses the **Name** parameter to specify the module, **SpeculationControl** .</span></span> <span data-ttu-id="ade77-133">**RequiredVersion** 參數會指定版本 **1.0.14** 。</span><span class="sxs-lookup"><span data-stu-id="ade77-133">The **RequiredVersion** parameter specifies the version, **1.0.14** .</span></span>

### <span data-ttu-id="ade77-134">範例5：不確認即更新模組</span><span class="sxs-lookup"><span data-stu-id="ade77-134">Example 5: Update a module without confirmation</span></span>

<span data-ttu-id="ade77-135">此範例不會要求確認，從線上元件庫將模組更新為最新版本。</span><span class="sxs-lookup"><span data-stu-id="ade77-135">This example doesn't request confirmation to update the module to the newest version from an online gallery.</span></span> <span data-ttu-id="ade77-136">如果已安裝模組， **Force** 參數會重新安裝模組。</span><span class="sxs-lookup"><span data-stu-id="ade77-136">If the module is already installed, the **Force** parameter reinstalls the module.</span></span>

```powershell
Update-Module -Name SpeculationControl -Force
```

<span data-ttu-id="ade77-137">`Update-Module` 使用 **Name** 參數來指定模組（ **SpeculationControl** ）。</span><span class="sxs-lookup"><span data-stu-id="ade77-137">`Update-Module` uses the **Name** parameter to specify the module, **SpeculationControl** .</span></span> <span data-ttu-id="ade77-138">**Force** 參數會更新模組，而不會要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="ade77-138">The **Force** parameter updates the module without requesting user confirmation.</span></span>

## <span data-ttu-id="ade77-139">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ade77-139">PARAMETERS</span></span>

### <span data-ttu-id="ade77-140">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="ade77-140">-AcceptLicense</span></span>

<span data-ttu-id="ade77-141">如果套件需要，則會在安裝期間自動接受授權合約。</span><span class="sxs-lookup"><span data-stu-id="ade77-141">Automatically accept the license agreement during installation if the package requires it.</span></span>

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

### <span data-ttu-id="ade77-142">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="ade77-142">-AllowPrerelease</span></span>

<span data-ttu-id="ade77-143">可讓您使用標記為發行前版本的較新模組來更新模組。</span><span class="sxs-lookup"><span data-stu-id="ade77-143">Allows you to update a module with the newer module marked as a prerelease.</span></span>

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

### <span data-ttu-id="ade77-144">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ade77-144">-Confirm</span></span>

<span data-ttu-id="ade77-145">在執行之前提示您確認 `Update-Module` 。</span><span class="sxs-lookup"><span data-stu-id="ade77-145">Prompts you for confirmation before running `Update-Module`.</span></span>

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

### <span data-ttu-id="ade77-146">-Credential</span><span class="sxs-lookup"><span data-stu-id="ade77-146">-Credential</span></span>

<span data-ttu-id="ade77-147">指定具有更新模組之許可權的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="ade77-147">Specifies a user account that has permission to update a module.</span></span>

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

### <span data-ttu-id="ade77-148">-Force</span><span class="sxs-lookup"><span data-stu-id="ade77-148">-Force</span></span>

<span data-ttu-id="ade77-149">強制更新每個指定的模組，而不提示要求確認。</span><span class="sxs-lookup"><span data-stu-id="ade77-149">Forces an update of each specified module without a prompt to request confirmation.</span></span> <span data-ttu-id="ade77-150">如果已安裝模組，請 **強制** 重新安裝模組。</span><span class="sxs-lookup"><span data-stu-id="ade77-150">If the module is already installed, **Force** reinstalls the module.</span></span>

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

### <span data-ttu-id="ade77-151">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="ade77-151">-MaximumVersion</span></span>

<span data-ttu-id="ade77-152">指定單一模組的最新版本來更新。</span><span class="sxs-lookup"><span data-stu-id="ade77-152">Specifies the maximum version of a single module to update.</span></span> <span data-ttu-id="ade77-153">如果您嘗試更新多個模組，就無法新增此參數。</span><span class="sxs-lookup"><span data-stu-id="ade77-153">You can't add this parameter if you're attempting to update multiple modules.</span></span> <span data-ttu-id="ade77-154">無法在同一個命令中使用 **MaximumVersion** 和 **RequiredVersion** 參數。</span><span class="sxs-lookup"><span data-stu-id="ade77-154">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="ade77-155">-Name</span><span class="sxs-lookup"><span data-stu-id="ade77-155">-Name</span></span>

<span data-ttu-id="ade77-156">指定要更新的一個或多個模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="ade77-156">Specifies the names of one or more modules to update.</span></span> <span data-ttu-id="ade77-157">`Update-Module` 搜尋 `$env:PSModulePath` 要更新的模組。</span><span class="sxs-lookup"><span data-stu-id="ade77-157">`Update-Module` searches `$env:PSModulePath` for the modules to update.</span></span> <span data-ttu-id="ade77-158">如果找不到符合指定之模組名稱的相符專案 `$env:PSModulePath` ，則會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="ade77-158">If no matches are found in `$env:PSModulePath` for the specified module name, an error occurs.</span></span>

<span data-ttu-id="ade77-159">模組名稱中接受萬用字元。</span><span class="sxs-lookup"><span data-stu-id="ade77-159">Wildcards are accepted in module names.</span></span> <span data-ttu-id="ade77-160">如果您將萬用字元新增至指定的名稱，而且找不到相符專案，則不會發生任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="ade77-160">If you add wildcard characters to the specified name and no matches are found, no error occurs.</span></span>

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

### <span data-ttu-id="ade77-161">-PassThru</span><span class="sxs-lookup"><span data-stu-id="ade77-161">-PassThru</span></span>

<span data-ttu-id="ade77-162">傳回代表您正在使用之項目的物件。</span><span class="sxs-lookup"><span data-stu-id="ade77-162">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="ade77-163">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="ade77-163">By default, this cmdlet does not generate any output.</span></span> <span data-ttu-id="ade77-164">在 **PowerShellGet** 2.0.0 中新增了 **PassThru** 參數支援</span><span class="sxs-lookup"><span data-stu-id="ade77-164">The **PassThru** parameter support was added in **PowerShellGet** 2.0.0</span></span>

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

### <span data-ttu-id="ade77-165">-Proxy</span><span class="sxs-lookup"><span data-stu-id="ade77-165">-Proxy</span></span>

<span data-ttu-id="ade77-166">指定要求的 proxy 伺服器，而不是直接連接到網際網路資源。</span><span class="sxs-lookup"><span data-stu-id="ade77-166">Specifies a proxy server for the request, rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="ade77-167">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="ade77-167">-ProxyCredential</span></span>

<span data-ttu-id="ade77-168">指定擁有使用 **proxy** 參數所指定 proxy 伺服器之許可權的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="ade77-168">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="ade77-169">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="ade77-169">-RequiredVersion</span></span>

<span data-ttu-id="ade77-170">指定要將現有已安裝的模組更新至哪一個正確版本。</span><span class="sxs-lookup"><span data-stu-id="ade77-170">Specifies the exact version to which the existing installed module will be updated.</span></span> <span data-ttu-id="ade77-171">**RequiredVersion** 指定的版本必須存在於線上元件庫中，否則會顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="ade77-171">The version specified by **RequiredVersion** must exist in the online gallery or an error is displayed.</span></span> <span data-ttu-id="ade77-172">如果在單一命令中更新一個以上的模組，您就無法使用 **RequiredVersion** 。</span><span class="sxs-lookup"><span data-stu-id="ade77-172">If more than one module is updated in a single command, you can't use **RequiredVersion** .</span></span>

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

### <span data-ttu-id="ade77-173">-Scope</span><span class="sxs-lookup"><span data-stu-id="ade77-173">-Scope</span></span>

<span data-ttu-id="ade77-174">指定模組的安裝範圍。</span><span class="sxs-lookup"><span data-stu-id="ade77-174">Specifies the installation scope of the module.</span></span> <span data-ttu-id="ade77-175">此參數可接受的值為 **AllUsers** 和 **CurrentUser** 。</span><span class="sxs-lookup"><span data-stu-id="ade77-175">The acceptable values for this parameter are **AllUsers** and **CurrentUser** .</span></span> <span data-ttu-id="ade77-176">如果未指定 **範圍** ，則更新會安裝在 **CurrentUser** 範圍中。</span><span class="sxs-lookup"><span data-stu-id="ade77-176">If **Scope** isn't specified, the update is installed in the **CurrentUser** scope.</span></span>

<span data-ttu-id="ade77-177">**AllUsers** 範圍需要較高的許可權，並將模組安裝在可供電腦的所有使用者存取的位置：</span><span class="sxs-lookup"><span data-stu-id="ade77-177">The **AllUsers** scope requires elevated permissions and installs modules in a location that is accessible to all users of the computer:</span></span>

`$env:ProgramFiles\PowerShell\Modules`

<span data-ttu-id="ade77-178">**CurrentUser** 不需要較高的許可權，而且會將模組安裝在僅供電腦目前使用者存取的位置：</span><span class="sxs-lookup"><span data-stu-id="ade77-178">The **CurrentUser** doesn't require elevated permissions and installs modules in a location that is accessible only to the current user of the computer:</span></span>

`$home\Documents\PowerShell\Modules`

<span data-ttu-id="ade77-179">未定義 **範圍** 時，會根據 PowerShellGet 版本設定預設值。</span><span class="sxs-lookup"><span data-stu-id="ade77-179">When no **Scope** is defined, the default is set based on the PowerShellGet version.</span></span>

- <span data-ttu-id="ade77-180">在 PowerShellGet 版本2.0.0 和更新版本中，針對所有其他的會話執行提高許可權的會話和 **CurrentUser** 時，預設值為 **AllUsers** 。</span><span class="sxs-lookup"><span data-stu-id="ade77-180">In PowerShellGet versions 2.0.0 and above, the default is **AllUsers** when running an elevated session and **CurrentUser** for all others.</span></span>
- <span data-ttu-id="ade77-181">在 PowerShellGet 1.x 版中，預設值為 **AllUsers** ，這需要提高安裝的許可權。</span><span class="sxs-lookup"><span data-stu-id="ade77-181">In PowerShellGet 1.x versions, the default is **AllUsers** , which requires elevation for install.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: CurrentUser
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ade77-182">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ade77-182">-WhatIf</span></span>

<span data-ttu-id="ade77-183">顯示執行時所發生 `Update-Module` 的情況。</span><span class="sxs-lookup"><span data-stu-id="ade77-183">Shows what would happen if `Update-Module` runs.</span></span> <span data-ttu-id="ade77-184">不會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ade77-184">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="ade77-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ade77-185">CommonParameters</span></span>

<span data-ttu-id="ade77-186">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="ade77-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ade77-187">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="ade77-187">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ade77-188">輸入</span><span class="sxs-lookup"><span data-stu-id="ade77-188">INPUTS</span></span>

### <span data-ttu-id="ade77-189">System.String[]</span><span class="sxs-lookup"><span data-stu-id="ade77-189">System.String[]</span></span>

### <span data-ttu-id="ade77-190">System.String</span><span class="sxs-lookup"><span data-stu-id="ade77-190">System.String</span></span>

### <span data-ttu-id="ade77-191">System.Management.Automation.PSCredential</span><span class="sxs-lookup"><span data-stu-id="ade77-191">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="ade77-192">System.Uri</span><span class="sxs-lookup"><span data-stu-id="ade77-192">System.Uri</span></span>

## <span data-ttu-id="ade77-193">輸出</span><span class="sxs-lookup"><span data-stu-id="ade77-193">OUTPUTS</span></span>

### <span data-ttu-id="ade77-194">System.Object</span><span class="sxs-lookup"><span data-stu-id="ade77-194">System.Object</span></span>

## <span data-ttu-id="ade77-195">注意</span><span class="sxs-lookup"><span data-stu-id="ade77-195">NOTES</span></span>

<span data-ttu-id="ade77-196">針對 PowerShell 5.1 或以下，提高許可權的會話中的預設範圍是 **AllUsers** ，而在非提高許可權的會話中， **CurrentUser** 。</span><span class="sxs-lookup"><span data-stu-id="ade77-196">For PowerShell 5.1 or below, the default scope in an elevated session is **AllUsers** , and in a non-elevated session, **CurrentUser** .</span></span> <span data-ttu-id="ade77-197">**AllUsers** 、的模組更新 `$env:ProgramFiles\PowerShell\Modules` 需要較高的許可權。</span><span class="sxs-lookup"><span data-stu-id="ade77-197">Module updates for **AllUsers** , `$env:ProgramFiles\PowerShell\Modules`, need elevated permissions.</span></span> <span data-ttu-id="ade77-198">**CurrentUser** 、的模組更新 `$home\Documents\PowerShell\Modules` 不需要較高的許可權。</span><span class="sxs-lookup"><span data-stu-id="ade77-198">Module updates for **CurrentUser** , `$home\Documents\PowerShell\Modules`, don't need elevated permissions.</span></span>

<span data-ttu-id="ade77-199">`Update-Module` 在 Windows 7 或 Windows 2008 R2 和更新版本的 Windows 上，于 powershell 3.0 或更新版本的 PowerShell 上執行。</span><span class="sxs-lookup"><span data-stu-id="ade77-199">`Update-Module` runs on PowerShell 3.0 or later releases of PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

<span data-ttu-id="ade77-200">如果未使用安裝 **名稱** 參數所指定的模組 `Install-Module` ，則會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="ade77-200">If the module that you specify with the **Name** parameter wasn't installed by using `Install-Module`, an error occurs.</span></span>

<span data-ttu-id="ade77-201">您只能藉由執行， `Update-Module` 在從線上元件庫安裝的模組上執行 `Install-Module` 。</span><span class="sxs-lookup"><span data-stu-id="ade77-201">You can only run `Update-Module` on modules that you installed from the online gallery by running `Install-Module`.</span></span>

<span data-ttu-id="ade77-202">如果 `Update-Module` 嘗試更新使用中的二進位檔，則會傳回 `Update-Module` 識別問題處理常式的錯誤。</span><span class="sxs-lookup"><span data-stu-id="ade77-202">If `Update-Module` attempts to update binaries that are in use, `Update-Module` returns an error that identifies the problem processes.</span></span> <span data-ttu-id="ade77-203">系統會在進程停止後通知使用者重試 `Update-Module` 。</span><span class="sxs-lookup"><span data-stu-id="ade77-203">The user is informed to retry `Update-Module` after the processes are stopped.</span></span>

## <span data-ttu-id="ade77-204">相關連結</span><span class="sxs-lookup"><span data-stu-id="ade77-204">RELATED LINKS</span></span>

[<span data-ttu-id="ade77-205">Find-Module</span><span class="sxs-lookup"><span data-stu-id="ade77-205">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="ade77-206">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="ade77-206">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="ade77-207">Install-Module</span><span class="sxs-lookup"><span data-stu-id="ade77-207">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="ade77-208">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="ade77-208">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="ade77-209">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="ade77-209">Uninstall-Module</span></span>](Uninstall-Module.md)
