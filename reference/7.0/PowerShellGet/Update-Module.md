---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/16/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-module?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Module
ms.openlocfilehash: 29ba3907a349257f63e127739786ab6e210c0f82
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201391"
---
# <span data-ttu-id="291aa-103">Update-Module</span><span class="sxs-lookup"><span data-stu-id="291aa-103">Update-Module</span></span>

## <span data-ttu-id="291aa-104">概要</span><span class="sxs-lookup"><span data-stu-id="291aa-104">SYNOPSIS</span></span>
<span data-ttu-id="291aa-105">將來自線上組件庫之指定模組的最新版本下載並安裝至本機電腦。</span><span class="sxs-lookup"><span data-stu-id="291aa-105">Downloads and installs the newest version of specified modules from an online gallery to the local computer.</span></span>

## <span data-ttu-id="291aa-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="291aa-106">SYNTAX</span></span>

### <span data-ttu-id="291aa-107">全部</span><span class="sxs-lookup"><span data-stu-id="291aa-107">All</span></span>

```
Update-Module [[-Name] <String[]>] [-RequiredVersion <String>] [-MaximumVersion <String>]
 [-Credential <PSCredential>] [-Scope <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Force] [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="291aa-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="291aa-108">DESCRIPTION</span></span>

<span data-ttu-id="291aa-109">`Update-Module`Cmdlet 會從線上元件庫安裝模組的最新版本。</span><span class="sxs-lookup"><span data-stu-id="291aa-109">The `Update-Module` cmdlet installs a module's newest version from an online gallery.</span></span> <span data-ttu-id="291aa-110">安裝之前，系統會提示您確認更新。</span><span class="sxs-lookup"><span data-stu-id="291aa-110">You're prompted to confirm the update before it's installed.</span></span> <span data-ttu-id="291aa-111">只有安裝在本機電腦上的模組才會安裝更新 `Install-Module` 。</span><span class="sxs-lookup"><span data-stu-id="291aa-111">Updates are installed only for modules that were installed on the local computer with `Install-Module`.</span></span> <span data-ttu-id="291aa-112">`Update-Module` 搜尋 `$env:PSModulePath` 已安裝的模組。</span><span class="sxs-lookup"><span data-stu-id="291aa-112">`Update-Module` searches `$env:PSModulePath` for installed modules.</span></span>

<span data-ttu-id="291aa-113">`Update-Module` 未指定參數時，會更新所有已安裝的模組。</span><span class="sxs-lookup"><span data-stu-id="291aa-113">`Update-Module` with no parameters specified updates all installed modules.</span></span> <span data-ttu-id="291aa-114">若要指定要更新的模組，請使用 **Name** 參數。</span><span class="sxs-lookup"><span data-stu-id="291aa-114">To specify a module to update, use the **Name** parameter.</span></span> <span data-ttu-id="291aa-115">您可以使用 **RequiredVersion** 參數來更新為模組的特定版本。</span><span class="sxs-lookup"><span data-stu-id="291aa-115">You can update to a module's specific version by using the **RequiredVersion** parameter.</span></span>

<span data-ttu-id="291aa-116">如果已安裝的模組已是最新版本，則不會更新模組。</span><span class="sxs-lookup"><span data-stu-id="291aa-116">If an installed module is already the newest version, the module isn't updated.</span></span> <span data-ttu-id="291aa-117">如果在中找不到模組 `$env:PSModulePath` ，則會顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="291aa-117">If the module isn't found in `$env:PSModulePath`, an error is displayed.</span></span>

<span data-ttu-id="291aa-118">若要顯示已安裝的模組，請使用 `Get-InstalledModule` 。</span><span class="sxs-lookup"><span data-stu-id="291aa-118">To display the installed modules, use `Get-InstalledModule`.</span></span>

## <span data-ttu-id="291aa-119">範例</span><span class="sxs-lookup"><span data-stu-id="291aa-119">EXAMPLES</span></span>

### <span data-ttu-id="291aa-120">範例 1：更新所有模組</span><span class="sxs-lookup"><span data-stu-id="291aa-120">Example 1: Update all modules</span></span>

<span data-ttu-id="291aa-121">此範例會將所有已安裝的模組更新為線上元件庫中的最新版本。</span><span class="sxs-lookup"><span data-stu-id="291aa-121">This example updates all installed modules to the newest version in an online gallery.</span></span>

```powershell
Update-Module
```

### <span data-ttu-id="291aa-122">範例 2：透過名稱更新模組</span><span class="sxs-lookup"><span data-stu-id="291aa-122">Example 2: Update a module by name</span></span>

<span data-ttu-id="291aa-123">此範例會將特定模組更新為線上元件庫中的最新版本。</span><span class="sxs-lookup"><span data-stu-id="291aa-123">This example updates a specific module to the newest version in an online gallery.</span></span>

```powershell
Update-Module -Name SpeculationControl
```

<span data-ttu-id="291aa-124">`Update-Module` 使用 **Name** 參數來更新特定模組（ **SpeculationControl** ）。</span><span class="sxs-lookup"><span data-stu-id="291aa-124">`Update-Module` uses the **Name** parameter to update a specific module, **SpeculationControl** .</span></span>

### <span data-ttu-id="291aa-125">範例3：查看 Update-Module 的執行</span><span class="sxs-lookup"><span data-stu-id="291aa-125">Example 3: View what-if Update-Module runs</span></span>

<span data-ttu-id="291aa-126">此範例會執行假設案例，以顯示執行時所發生的情況 `Update-Module` 。</span><span class="sxs-lookup"><span data-stu-id="291aa-126">This example does a what-if scenario to show what happens if `Update-Module` is run.</span></span> <span data-ttu-id="291aa-127">命令不會執行。</span><span class="sxs-lookup"><span data-stu-id="291aa-127">The command isn't run.</span></span>

```powershell
Update-Module -WhatIf
```

```Output
What if: Performing the operation "Update-Module" on target "Version '2.8.0' of module
  'Carbon', updating to version '2.8.1'".
What if: Performing the operation "Update-Module" on target "Version '1.0.10' of module
  'SpeculationControl', updating to version '1.0.14'".
```

<span data-ttu-id="291aa-128">`Update-Module` 使用 **WhatIf** 參數顯示如果已執行，會發生什麼事 `Update-Module` 。</span><span class="sxs-lookup"><span data-stu-id="291aa-128">`Update-Module` uses the **WhatIf** parameter display what would happen if `Update-Module` were run.</span></span>

### <span data-ttu-id="291aa-129">範例 4：將模組更新至指定版本</span><span class="sxs-lookup"><span data-stu-id="291aa-129">Example 4: Update a module to a specified version</span></span>

<span data-ttu-id="291aa-130">在此範例中，模組會更新為特定版本。</span><span class="sxs-lookup"><span data-stu-id="291aa-130">In this example, a module is updated to a specific version.</span></span> <span data-ttu-id="291aa-131">版本必須存在於線上元件庫中，否則會顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="291aa-131">The version must exist in the online gallery or an error is displayed.</span></span>

```powershell
Update-Module -Name SpeculationControl -RequiredVersion 1.0.14
```

<span data-ttu-id="291aa-132">`Update-Module` 使用 **Name** 參數來指定模組（ **SpeculationControl** ）。</span><span class="sxs-lookup"><span data-stu-id="291aa-132">`Update-Module` uses the **Name** parameter to specify the module, **SpeculationControl** .</span></span> <span data-ttu-id="291aa-133">**RequiredVersion** 參數會指定版本 **1.0.14** 。</span><span class="sxs-lookup"><span data-stu-id="291aa-133">The **RequiredVersion** parameter specifies the version, **1.0.14** .</span></span>

### <span data-ttu-id="291aa-134">範例5：不確認即更新模組</span><span class="sxs-lookup"><span data-stu-id="291aa-134">Example 5: Update a module without confirmation</span></span>

<span data-ttu-id="291aa-135">此範例不會要求確認，從線上元件庫將模組更新為最新版本。</span><span class="sxs-lookup"><span data-stu-id="291aa-135">This example doesn't request confirmation to update the module to the newest version from an online gallery.</span></span> <span data-ttu-id="291aa-136">如果已安裝模組， **Force** 參數會重新安裝模組。</span><span class="sxs-lookup"><span data-stu-id="291aa-136">If the module is already installed, the **Force** parameter reinstalls the module.</span></span>

```powershell
Update-Module -Name SpeculationControl -Force
```

<span data-ttu-id="291aa-137">`Update-Module` 使用 **Name** 參數來指定模組（ **SpeculationControl** ）。</span><span class="sxs-lookup"><span data-stu-id="291aa-137">`Update-Module` uses the **Name** parameter to specify the module, **SpeculationControl** .</span></span> <span data-ttu-id="291aa-138">**Force** 參數會更新模組，而不會要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="291aa-138">The **Force** parameter updates the module without requesting user confirmation.</span></span>

## <span data-ttu-id="291aa-139">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="291aa-139">PARAMETERS</span></span>

### <span data-ttu-id="291aa-140">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="291aa-140">-AcceptLicense</span></span>

<span data-ttu-id="291aa-141">如果套件需要，則會在安裝期間自動接受授權合約。</span><span class="sxs-lookup"><span data-stu-id="291aa-141">Automatically accept the license agreement during installation if the package requires it.</span></span>

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

### <span data-ttu-id="291aa-142">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="291aa-142">-AllowPrerelease</span></span>

<span data-ttu-id="291aa-143">可讓您使用標記為發行前版本的較新模組來更新模組。</span><span class="sxs-lookup"><span data-stu-id="291aa-143">Allows you to update a module with the newer module marked as a prerelease.</span></span>

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

### <span data-ttu-id="291aa-144">-Confirm</span><span class="sxs-lookup"><span data-stu-id="291aa-144">-Confirm</span></span>

<span data-ttu-id="291aa-145">在執行之前提示您確認 `Update-Module` 。</span><span class="sxs-lookup"><span data-stu-id="291aa-145">Prompts you for confirmation before running `Update-Module`.</span></span>

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

### <span data-ttu-id="291aa-146">-Credential</span><span class="sxs-lookup"><span data-stu-id="291aa-146">-Credential</span></span>

<span data-ttu-id="291aa-147">指定具有更新模組之許可權的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="291aa-147">Specifies a user account that has permission to update a module.</span></span>

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

### <span data-ttu-id="291aa-148">-Force</span><span class="sxs-lookup"><span data-stu-id="291aa-148">-Force</span></span>

<span data-ttu-id="291aa-149">強制更新每個指定的模組，而不提示要求確認。</span><span class="sxs-lookup"><span data-stu-id="291aa-149">Forces an update of each specified module without a prompt to request confirmation.</span></span> <span data-ttu-id="291aa-150">如果已安裝模組，請 **強制** 重新安裝模組。</span><span class="sxs-lookup"><span data-stu-id="291aa-150">If the module is already installed, **Force** reinstalls the module.</span></span>

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

### <span data-ttu-id="291aa-151">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="291aa-151">-MaximumVersion</span></span>

<span data-ttu-id="291aa-152">指定單一模組的最新版本來更新。</span><span class="sxs-lookup"><span data-stu-id="291aa-152">Specifies the maximum version of a single module to update.</span></span> <span data-ttu-id="291aa-153">如果您嘗試更新多個模組，就無法新增此參數。</span><span class="sxs-lookup"><span data-stu-id="291aa-153">You can't add this parameter if you're attempting to update multiple modules.</span></span> <span data-ttu-id="291aa-154">無法在同一個命令中使用 **MaximumVersion** 和 **RequiredVersion** 參數。</span><span class="sxs-lookup"><span data-stu-id="291aa-154">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="291aa-155">-Name</span><span class="sxs-lookup"><span data-stu-id="291aa-155">-Name</span></span>

<span data-ttu-id="291aa-156">指定要更新的一個或多個模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="291aa-156">Specifies the names of one or more modules to update.</span></span> <span data-ttu-id="291aa-157">`Update-Module` 搜尋 `$env:PSModulePath` 要更新的模組。</span><span class="sxs-lookup"><span data-stu-id="291aa-157">`Update-Module` searches `$env:PSModulePath` for the modules to update.</span></span> <span data-ttu-id="291aa-158">如果找不到符合指定之模組名稱的相符專案 `$env:PSModulePath` ，則會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="291aa-158">If no matches are found in `$env:PSModulePath` for the specified module name, an error occurs.</span></span>

<span data-ttu-id="291aa-159">模組名稱中接受萬用字元。</span><span class="sxs-lookup"><span data-stu-id="291aa-159">Wildcards are accepted in module names.</span></span> <span data-ttu-id="291aa-160">如果您將萬用字元新增至指定的名稱，而且找不到相符專案，則不會發生任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="291aa-160">If you add wildcard characters to the specified name and no matches are found, no error occurs.</span></span>

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

### <span data-ttu-id="291aa-161">-PassThru</span><span class="sxs-lookup"><span data-stu-id="291aa-161">-PassThru</span></span>

<span data-ttu-id="291aa-162">傳回代表您正在使用之項目的物件。</span><span class="sxs-lookup"><span data-stu-id="291aa-162">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="291aa-163">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="291aa-163">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="291aa-164">-Proxy</span><span class="sxs-lookup"><span data-stu-id="291aa-164">-Proxy</span></span>

<span data-ttu-id="291aa-165">指定要求的 proxy 伺服器，而不是直接連接到網際網路資源。</span><span class="sxs-lookup"><span data-stu-id="291aa-165">Specifies a proxy server for the request, rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="291aa-166">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="291aa-166">-ProxyCredential</span></span>

<span data-ttu-id="291aa-167">指定擁有使用 **proxy** 參數所指定 proxy 伺服器之許可權的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="291aa-167">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="291aa-168">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="291aa-168">-RequiredVersion</span></span>

<span data-ttu-id="291aa-169">指定要將現有已安裝的模組更新至哪一個正確版本。</span><span class="sxs-lookup"><span data-stu-id="291aa-169">Specifies the exact version to which the existing installed module will be updated.</span></span> <span data-ttu-id="291aa-170">**RequiredVersion** 指定的版本必須存在於線上元件庫中，否則會顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="291aa-170">The version specified by **RequiredVersion** must exist in the online gallery or an error is displayed.</span></span> <span data-ttu-id="291aa-171">如果在單一命令中更新一個以上的模組，您就無法使用 **RequiredVersion** 。</span><span class="sxs-lookup"><span data-stu-id="291aa-171">If more than one module is updated in a single command, you can't use **RequiredVersion** .</span></span>

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

### <span data-ttu-id="291aa-172">-Scope</span><span class="sxs-lookup"><span data-stu-id="291aa-172">-Scope</span></span>

<span data-ttu-id="291aa-173">指定模組的安裝範圍。</span><span class="sxs-lookup"><span data-stu-id="291aa-173">Specifies the installation scope of the module.</span></span> <span data-ttu-id="291aa-174">此參數可接受的值為 **AllUsers** 和 **CurrentUser** 。</span><span class="sxs-lookup"><span data-stu-id="291aa-174">The acceptable values for this parameter are **AllUsers** and **CurrentUser** .</span></span> <span data-ttu-id="291aa-175">如果未指定 **範圍** ，則更新會安裝在 **CurrentUser** 範圍中。</span><span class="sxs-lookup"><span data-stu-id="291aa-175">If **Scope** isn't specified, the update is installed in the **CurrentUser** scope.</span></span>

<span data-ttu-id="291aa-176">**AllUsers** 範圍需要較高的許可權，並將模組安裝在可供電腦的所有使用者存取的位置：</span><span class="sxs-lookup"><span data-stu-id="291aa-176">The **AllUsers** scope requires elevated permissions and installs modules in a location that is accessible to all users of the computer:</span></span>

`$env:ProgramFiles\PowerShell\Modules`

<span data-ttu-id="291aa-177">**CurrentUser** 不需要較高的許可權，而且會將模組安裝在僅供電腦目前使用者存取的位置：</span><span class="sxs-lookup"><span data-stu-id="291aa-177">The **CurrentUser** doesn't require elevated permissions and installs modules in a location that is accessible only to the current user of the computer:</span></span>

`$home\Documents\PowerShell\Modules`

<span data-ttu-id="291aa-178">未定義 **範圍** 時，會根據 PowerShellGet 版本設定預設值。</span><span class="sxs-lookup"><span data-stu-id="291aa-178">When no **Scope** is defined, the default is set based on the PowerShellGet version.</span></span>

- <span data-ttu-id="291aa-179">在 PowerShellGet 版本2.1.0 和更新版本中，預設值為 **CurrentUser** ，不需要提高安裝的許可權。</span><span class="sxs-lookup"><span data-stu-id="291aa-179">In PowerShellGet versions 2.1.0 and above, the default is **CurrentUser** , which does not require elevation for install.</span></span>
- <span data-ttu-id="291aa-180">在 PowerShellGet 1.x 版中，無法使用 **範圍** 參數，預設值為 **AllUsers** ，這需要提高安裝的許可權。</span><span class="sxs-lookup"><span data-stu-id="291aa-180">In PowerShellGet 1.x - 2.0.x versions, the **Scope** parameter is not available and the default is **AllUsers** , which requires elevation for install.</span></span>

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

### <span data-ttu-id="291aa-181">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="291aa-181">-WhatIf</span></span>

<span data-ttu-id="291aa-182">顯示執行時所發生 `Update-Module` 的情況。</span><span class="sxs-lookup"><span data-stu-id="291aa-182">Shows what would happen if `Update-Module` runs.</span></span> <span data-ttu-id="291aa-183">不會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="291aa-183">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="291aa-184">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="291aa-184">CommonParameters</span></span>

<span data-ttu-id="291aa-185">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="291aa-185">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="291aa-186">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="291aa-186">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="291aa-187">輸入</span><span class="sxs-lookup"><span data-stu-id="291aa-187">INPUTS</span></span>

### <span data-ttu-id="291aa-188">System.String[]</span><span class="sxs-lookup"><span data-stu-id="291aa-188">System.String[]</span></span>

### <span data-ttu-id="291aa-189">System.String</span><span class="sxs-lookup"><span data-stu-id="291aa-189">System.String</span></span>

### <span data-ttu-id="291aa-190">System.Management.Automation.PSCredential</span><span class="sxs-lookup"><span data-stu-id="291aa-190">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="291aa-191">System.Uri</span><span class="sxs-lookup"><span data-stu-id="291aa-191">System.Uri</span></span>

## <span data-ttu-id="291aa-192">輸出</span><span class="sxs-lookup"><span data-stu-id="291aa-192">OUTPUTS</span></span>

### <span data-ttu-id="291aa-193">System.Object</span><span class="sxs-lookup"><span data-stu-id="291aa-193">System.Object</span></span>

## <span data-ttu-id="291aa-194">注意</span><span class="sxs-lookup"><span data-stu-id="291aa-194">NOTES</span></span>

<span data-ttu-id="291aa-195">針對 PowerShell 6.0 版和更新版本，預設安裝範圍一律為 **CurrentUser** 。</span><span class="sxs-lookup"><span data-stu-id="291aa-195">For PowerShell version 6.0 and above, the default installation scope is always **CurrentUser** .</span></span>
<span data-ttu-id="291aa-196">**CurrentUser** 、的模組更新 `$home\Documents\PowerShell\Modules` 不需要較高的許可權。</span><span class="sxs-lookup"><span data-stu-id="291aa-196">Module updates for **CurrentUser** , `$home\Documents\PowerShell\Modules`, don't need elevated permissions.</span></span> <span data-ttu-id="291aa-197">**AllUsers** 、的模組更新 `$env:ProgramFiles\PowerShell\Modules` 需要較高的許可權。</span><span class="sxs-lookup"><span data-stu-id="291aa-197">Module updates for **AllUsers** , `$env:ProgramFiles\PowerShell\Modules`, need elevated permissions.</span></span>

<span data-ttu-id="291aa-198">`Update-Module` 在 Windows 7 或 Windows 2008 R2 和更新版本的 Windows 上，于 powershell 3.0 或更新版本的 PowerShell 上執行。</span><span class="sxs-lookup"><span data-stu-id="291aa-198">`Update-Module` runs on PowerShell 3.0 or later releases of PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

<span data-ttu-id="291aa-199">如果未使用安裝 **名稱** 參數所指定的模組 `Install-Module` ，則會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="291aa-199">If the module that you specify with the **Name** parameter wasn't installed by using `Install-Module`, an error occurs.</span></span>

<span data-ttu-id="291aa-200">您只能藉由執行， `Update-Module` 在從線上元件庫安裝的模組上執行 `Install-Module` 。</span><span class="sxs-lookup"><span data-stu-id="291aa-200">You can only run `Update-Module` on modules that you installed from the online gallery by running `Install-Module`.</span></span>

<span data-ttu-id="291aa-201">如果 `Update-Module` 嘗試更新使用中的二進位檔，則會傳回 `Update-Module` 識別問題處理常式的錯誤。</span><span class="sxs-lookup"><span data-stu-id="291aa-201">If `Update-Module` attempts to update binaries that are in use, `Update-Module` returns an error that identifies the problem processes.</span></span> <span data-ttu-id="291aa-202">系統會在進程停止後通知使用者重試 `Update-Module` 。</span><span class="sxs-lookup"><span data-stu-id="291aa-202">The user is informed to retry `Update-Module` after the processes are stopped.</span></span>

## <span data-ttu-id="291aa-203">相關連結</span><span class="sxs-lookup"><span data-stu-id="291aa-203">RELATED LINKS</span></span>

[<span data-ttu-id="291aa-204">Find-Module</span><span class="sxs-lookup"><span data-stu-id="291aa-204">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="291aa-205">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="291aa-205">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="291aa-206">Install-Module</span><span class="sxs-lookup"><span data-stu-id="291aa-206">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="291aa-207">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="291aa-207">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="291aa-208">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="291aa-208">Uninstall-Module</span></span>](Uninstall-Module.md)
