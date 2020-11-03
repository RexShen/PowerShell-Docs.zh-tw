---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 08/03/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/install-module?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Module
ms.openlocfilehash: 0e6dfd00da246b5632474c45d3794d796715240c
ms.sourcegitcommit: 4fc8cf397cb725ae973751d1d5d542f34f0db2d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2020
ms.locfileid: "93205820"
---
# <span data-ttu-id="fbf5f-103">Install-Module</span><span class="sxs-lookup"><span data-stu-id="fbf5f-103">Install-Module</span></span>

## <span data-ttu-id="fbf5f-104">概要</span><span class="sxs-lookup"><span data-stu-id="fbf5f-104">SYNOPSIS</span></span>
<span data-ttu-id="fbf5f-105">從存放庫下載一或多個模組，並將它們安裝在本機電腦上。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-105">Downloads one or more modules from a repository, and installs them on the local computer.</span></span>

## <span data-ttu-id="fbf5f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fbf5f-106">SYNTAX</span></span>

### <span data-ttu-id="fbf5f-107">NameParameterSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="fbf5f-107">NameParameterSet (Default)</span></span>

```
Install-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Credential <PSCredential>] [-Scope <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllowClobber] [-SkipPublisherCheck] [-Force]
 [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="fbf5f-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="fbf5f-108">InputObject</span></span>

```
Install-Module [-InputObject] <PSObject[]> [-Credential <PSCredential>] [-Scope <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllowClobber] [-SkipPublisherCheck] [-Force]
 [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="fbf5f-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="fbf5f-109">DESCRIPTION</span></span>

<span data-ttu-id="fbf5f-110">此 `Install-Module` Cmdlet 會從線上存放庫中取得一或多個符合指定準則的模組。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-110">The `Install-Module` cmdlet gets one or more modules that meet specified criteria from an online repository.</span></span> <span data-ttu-id="fbf5f-111">此 Cmdlet 會確認搜尋結果是有效的模組，並將模組資料夾複製到安裝位置。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-111">The cmdlet verifies that search results are valid modules and copies the module folders to the installation location.</span></span> <span data-ttu-id="fbf5f-112">安裝後不會自動匯入已安裝的模組。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-112">Installed modules are not automatically imported after installation.</span></span>
<span data-ttu-id="fbf5f-113">您可以根據指定模組的最小值、最大值和確切版本，篩選要安裝的模組。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-113">You can filter which module is installed based on the minimum, maximum, and exact versions of specified modules.</span></span>

<span data-ttu-id="fbf5f-114">如果要安裝的模組具有相同的名稱或版本，或包含現有模組中的命令，則會顯示警告訊息。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-114">If the module being installed has the same name or version, or contains commands in an existing module, warning messages are displayed.</span></span> <span data-ttu-id="fbf5f-115">在您確認要安裝模組並覆寫警告之後，請使用 `-Force` 和 `-AllowClobber` 參數。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-115">After you confirm that you want to install the module and override the warnings, use the `-Force` and `-AllowClobber` parameters.</span></span> <span data-ttu-id="fbf5f-116">根據您的存放庫設定，您可能需要回答提示，讓模組安裝繼續進行。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-116">Dependent upon your repository settings, you might need to answer a prompt for the module installation to continue.</span></span>

<span data-ttu-id="fbf5f-117">這些範例會使用 [PowerShell 資源庫](https://www.powershellgallery.com/) 作為唯一的已註冊存放庫。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-117">These examples use the [PowerShell Gallery](https://www.powershellgallery.com/) as the only registered repository.</span></span> <span data-ttu-id="fbf5f-118">`Get-PSRepository` 顯示已註冊的存放庫。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-118">`Get-PSRepository` displays the registered repositories.</span></span> <span data-ttu-id="fbf5f-119">如果您有多個已註冊的存放庫，請使用 `-Repository` 參數來指定存放庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-119">If you have multiple registered repositories, use the `-Repository` parameter to specify the repository's name.</span></span>

## <span data-ttu-id="fbf5f-120">範例</span><span class="sxs-lookup"><span data-stu-id="fbf5f-120">EXAMPLES</span></span>

### <span data-ttu-id="fbf5f-121">範例1：尋找並安裝模組</span><span class="sxs-lookup"><span data-stu-id="fbf5f-121">Example 1: Find and install a module</span></span>

<span data-ttu-id="fbf5f-122">此範例會尋找存放庫中的模組，並安裝該模組。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-122">This example finds a module in the repository and installs the module.</span></span>

```powershell
Find-Module -Name PowerShellGet | Install-Module
```

<span data-ttu-id="fbf5f-123">會 `Find-Module` 使用 **Name** 參數來指定 **PowerShellGet** 模組。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-123">The `Find-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="fbf5f-124">根據預設，會從存放庫下載最新版本的模組。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-124">By default, the newest version of the module is downloaded from the repository.</span></span> <span data-ttu-id="fbf5f-125">物件會向下傳送至 `Install-Module` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-125">The object is sent down the pipeline to the `Install-Module` cmdlet.</span></span> <span data-ttu-id="fbf5f-126">`Install-Module` 為中的所有使用者安裝模組 `$env:ProgramFiles\PowerShell\Modules` 。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-126">`Install-Module` installs the module for all users in `$env:ProgramFiles\PowerShell\Modules`.</span></span>

### <span data-ttu-id="fbf5f-127">範例2：依名稱安裝模組</span><span class="sxs-lookup"><span data-stu-id="fbf5f-127">Example 2: Install a module by name</span></span>

<span data-ttu-id="fbf5f-128">在此範例中，會安裝最新版本的 **PowerShellGet** 模組。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-128">In this example, the newest version of the **PowerShellGet** module is installed.</span></span>

```powershell
Install-Module -Name PowerShellGet
```

<span data-ttu-id="fbf5f-129">會 `Install-Module` 使用 **Name** 參數來指定 **PowerShellGet** 模組。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-129">The `Install-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="fbf5f-130">根據預設，會從存放庫下載最新版本的模組並安裝。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-130">By default, the newest version of the module is downloaded from the repository and installed.</span></span>

### <span data-ttu-id="fbf5f-131">範例3：使用最小版本來安裝模組</span><span class="sxs-lookup"><span data-stu-id="fbf5f-131">Example 3: Install a module using its minimum version</span></span>

<span data-ttu-id="fbf5f-132">在此範例中，會安裝 **PowerShellGet** 模組的最小版本。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-132">In this example, the minimum version of the **PowerShellGet** module is installed.</span></span> <span data-ttu-id="fbf5f-133">**MinimumVersion** 參數指定應安裝的模組最低版本。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-133">The **MinimumVersion** parameter specifies the lowest version of the module that should be installed.</span></span> <span data-ttu-id="fbf5f-134">如果有較新版本的模組可供使用，則會為所有使用者下載並安裝該版本。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-134">If a newer version of the module is available, that version is downloaded and installed for all users.</span></span>

```powershell
Install-Module -Name PowerShellGet -MinimumVersion 2.0.1
```

<span data-ttu-id="fbf5f-135">會 `Install-Module` 使用 **Name** 參數來指定 **PowerShellGet** 模組。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-135">The `Install-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="fbf5f-136">**MinimumVersion** 參數指定從存放庫下載 **2.0.1** 版，並安裝該版本。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-136">The **MinimumVersion** parameter specifies that version **2.0.1** is downloaded from the repository and installed.</span></span> <span data-ttu-id="fbf5f-137">因為版本 **2.0.4 版** 可用，所以會為所有使用者下載並安裝該版本。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-137">Because version **2.0.4** is available, that version is downloaded and installed for all users.</span></span>

### <span data-ttu-id="fbf5f-138">範例4：安裝特定版本的模組</span><span class="sxs-lookup"><span data-stu-id="fbf5f-138">Example 4: Install a specific version of a module</span></span>

<span data-ttu-id="fbf5f-139">在此範例中，會安裝特定版本的 **PowerShellGet** 模組。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-139">In this example, a specific version of the **PowerShellGet** module is installed.</span></span>

```powershell
Install-Module -Name PowerShellGet -RequiredVersion 2.0.0
```

<span data-ttu-id="fbf5f-140">會 `Install-Module` 使用 **Name** 參數來指定 **PowerShellGet** 模組。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-140">The `Install-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="fbf5f-141">**RequiredVersion** 參數指定為所有使用者下載並安裝版本 **2.0.0** 。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-141">The **RequiredVersion** parameter specifies that version **2.0.0** is downloaded and installed for all users.</span></span>

### <span data-ttu-id="fbf5f-142">範例5：僅針對目前的使用者安裝模組</span><span class="sxs-lookup"><span data-stu-id="fbf5f-142">Example 5: Install a module only for the current user</span></span>

<span data-ttu-id="fbf5f-143">此範例會下載並安裝最新版本的模組，僅適用于目前的使用者。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-143">This example downloads and installs the newest version of a module, only for the current user.</span></span>

```powershell
Install-Module -Name PowerShellGet -Scope CurrentUser
```

<span data-ttu-id="fbf5f-144">會 `Install-Module` 使用 **Name** 參數來指定 **PowerShellGet** 模組。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-144">The `Install-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span>
<span data-ttu-id="fbf5f-145">`Install-Module` 將最新版本的 **PowerShellGet** 下載並安裝到目前使用者的目錄中 `$home\Documents\PowerShell\Modules` 。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-145">`Install-Module` downloads and installs the newest version of **PowerShellGet** into the current user's directory, `$home\Documents\PowerShell\Modules`.</span></span>

## <span data-ttu-id="fbf5f-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fbf5f-146">PARAMETERS</span></span>

### <span data-ttu-id="fbf5f-147">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="fbf5f-147">-AcceptLicense</span></span>

<span data-ttu-id="fbf5f-148">針對需要授權的模組， **AcceptLicense** 會在安裝期間自動接受授權合約。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-148">For modules that require a license, **AcceptLicense** automatically accepts the license agreement during installation.</span></span> <span data-ttu-id="fbf5f-149">如需詳細資訊，請參閱 [要求接受授權的模組](/powershell/scripting/gallery/concepts/module-license-acceptance)。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-149">For more information, see [Modules Requiring License Acceptance](/powershell/scripting/gallery/concepts/module-license-acceptance).</span></span>

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

### <span data-ttu-id="fbf5f-150">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="fbf5f-150">-AllowClobber</span></span>

<span data-ttu-id="fbf5f-151">覆寫有關電腦上現有命令之安裝衝突的警告訊息。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-151">Overrides warning messages about installation conflicts about existing commands on a computer.</span></span>
<span data-ttu-id="fbf5f-152">覆寫現有的命令，其名稱與模組所安裝的命令相同。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-152">Overwrites existing commands that have the same name as commands being installed by a module.</span></span>
<span data-ttu-id="fbf5f-153">**AllowClobber** 和 **Force** 可以在命令中一起使用 `Install-Module` 。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-153">**AllowClobber** and **Force** can be used together in an `Install-Module` command.</span></span>

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

### <span data-ttu-id="fbf5f-154">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="fbf5f-154">-AllowPrerelease</span></span>

<span data-ttu-id="fbf5f-155">可讓您安裝標示為發行前版本的模組。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-155">Allows you to install a module marked as a pre-release.</span></span>

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

### <span data-ttu-id="fbf5f-156">-Confirm</span><span class="sxs-lookup"><span data-stu-id="fbf5f-156">-Confirm</span></span>

<span data-ttu-id="fbf5f-157">在執行 Cmdlet 前提示您確認 `Install-Module` 。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-157">Prompts you for confirmation before running the `Install-Module` cmdlet.</span></span>

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

### <span data-ttu-id="fbf5f-158">-Credential</span><span class="sxs-lookup"><span data-stu-id="fbf5f-158">-Credential</span></span>

<span data-ttu-id="fbf5f-159">指定擁有為指定的套件提供者或來源安裝模組之許可權的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-159">Specifies a user account that has rights to install a module for a specified package provider or source.</span></span>

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

### <span data-ttu-id="fbf5f-160">-Force</span><span class="sxs-lookup"><span data-stu-id="fbf5f-160">-Force</span></span>

<span data-ttu-id="fbf5f-161">安裝模組並覆寫有關模組安裝衝突的警告訊息。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-161">Installs a module and overrides warning messages about module installation conflicts.</span></span> <span data-ttu-id="fbf5f-162">如果電腦上已有相同名稱的模組，則 **強制** 允許安裝多個版本。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-162">If a module with the same name already exists on the computer, **Force** allows for multiple versions to be installed.</span></span> <span data-ttu-id="fbf5f-163">如果有現有的模組具有相同的名稱和版本，請 **強制** 覆寫該版本。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-163">If there is an existing module with the same name and version, **Force** overwrites that version.</span></span> <span data-ttu-id="fbf5f-164">**Force** 和 **AllowClobber** 可以在命令中一起使用 `Install-Module` 。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-164">**Force** and **AllowClobber** can be used together in an `Install-Module` command.</span></span>

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

### <span data-ttu-id="fbf5f-165">-InputObject</span><span class="sxs-lookup"><span data-stu-id="fbf5f-165">-InputObject</span></span>

<span data-ttu-id="fbf5f-166">用於管線輸入。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-166">Used for pipeline input.</span></span>

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

### <span data-ttu-id="fbf5f-167">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="fbf5f-167">-MaximumVersion</span></span>

<span data-ttu-id="fbf5f-168">指定要安裝之單一模組的最大版本。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-168">Specifies the maximum version of a single module to install.</span></span> <span data-ttu-id="fbf5f-169">安裝的版本必須小於或等於 **MaximumVersion** 。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-169">The version installed must be less than or equal to **MaximumVersion** .</span></span> <span data-ttu-id="fbf5f-170">如果您想要安裝多個模組，則不能使用 **MaximumVersion** 。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-170">If you want to install multiple modules, you cannot use **MaximumVersion** .</span></span> <span data-ttu-id="fbf5f-171">無法在同一個命令中使用 **MaximumVersion** 和 **RequiredVersion** `Install-Module` 。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-171">**MaximumVersion** and **RequiredVersion** cannot be used in the same `Install-Module` command.</span></span>

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

### <span data-ttu-id="fbf5f-172">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="fbf5f-172">-MinimumVersion</span></span>

<span data-ttu-id="fbf5f-173">指定要安裝之單一模組的最小版本。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-173">Specifies the minimum version of a single module to install.</span></span> <span data-ttu-id="fbf5f-174">安裝的版本必須大於或等於 **MinimumVersion** 。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-174">The version installed must be greater than or equal to **MinimumVersion** .</span></span> <span data-ttu-id="fbf5f-175">如果有較新版本的模組可供使用，則會安裝較新的版本。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-175">If there is a newer version of the module available, the newer version is installed.</span></span> <span data-ttu-id="fbf5f-176">如果您想要安裝多個模組，則無法使用 **MinimumVersion** 。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-176">If you want to install multiple modules, you cannot use **MinimumVersion** .</span></span>
<span data-ttu-id="fbf5f-177">**MinimumVersion** 和 **RequiredVersion** 無法在相同的命令中使用 `Install-Module` 。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-177">**MinimumVersion** and **RequiredVersion** cannot be used in the same `Install-Module` command.</span></span>

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

### <span data-ttu-id="fbf5f-178">-Name</span><span class="sxs-lookup"><span data-stu-id="fbf5f-178">-Name</span></span>

<span data-ttu-id="fbf5f-179">指定要從線上元件庫安裝的確切模組名稱。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-179">Specifies the exact names of modules to install from the online gallery.</span></span> <span data-ttu-id="fbf5f-180">接受以逗號分隔的模組名稱清單。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-180">A comma-separated list of module names is accepted.</span></span> <span data-ttu-id="fbf5f-181">模組名稱必須符合存放庫中的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-181">The module name must match the module name in the repository.</span></span> <span data-ttu-id="fbf5f-182">用 `Find-Module` 來取得模組名稱的清單。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-182">Use `Find-Module` to get a list of module names.</span></span>

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

### <span data-ttu-id="fbf5f-183">-PassThru</span><span class="sxs-lookup"><span data-stu-id="fbf5f-183">-PassThru</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fbf5f-184">-Proxy</span><span class="sxs-lookup"><span data-stu-id="fbf5f-184">-Proxy</span></span>

<span data-ttu-id="fbf5f-185">指定要求的 proxy 伺服器，而不是直接連接到網際網路資源。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-185">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="fbf5f-186">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="fbf5f-186">-ProxyCredential</span></span>

<span data-ttu-id="fbf5f-187">指定具有使用 **Proxy** 參數所指定 Proxy 伺服器之權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-187">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="fbf5f-188">-Repository</span><span class="sxs-lookup"><span data-stu-id="fbf5f-188">-Repository</span></span>

<span data-ttu-id="fbf5f-189">使用存放 **庫** 參數來指定要用來下載及安裝模組的存放庫。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-189">Use the **Repository** parameter to specify which repository is used to download and install a module.</span></span> <span data-ttu-id="fbf5f-190">在註冊多個存放庫時使用。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-190">Used when multiple repositories are registered.</span></span> <span data-ttu-id="fbf5f-191">在命令中指定已註冊存放庫的名稱 `Install-Module` 。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-191">Specifies the name of a registered repository in the `Install-Module` command.</span></span> <span data-ttu-id="fbf5f-192">若要註冊存放庫，請使用 `Register-PSRepository` 。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-192">To register a repository, use `Register-PSRepository`.</span></span>
<span data-ttu-id="fbf5f-193">若要顯示已註冊的存放庫，請使用 `Get-PSRepository` 。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-193">To display registered repositories, use `Get-PSRepository`.</span></span>

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

### <span data-ttu-id="fbf5f-194">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="fbf5f-194">-RequiredVersion</span></span>

<span data-ttu-id="fbf5f-195">指定要安裝之單一模組的確切版本。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-195">Specifies the exact version of a single module to install.</span></span> <span data-ttu-id="fbf5f-196">如果指定版本的存放庫中沒有相符的，則會顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-196">If there is no match in the repository for the specified version, an error is displayed.</span></span> <span data-ttu-id="fbf5f-197">如果您想要安裝多個模組，則無法使用 **RequiredVersion** 。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-197">If you want to install multiple modules, you cannot use **RequiredVersion** .</span></span> <span data-ttu-id="fbf5f-198">**RequiredVersion** 無法在與 `Install-Module` **MinimumVersion** 或 **MaximumVersion** 相同的命令中使用。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-198">**RequiredVersion** cannot be used in the same `Install-Module` command as **MinimumVersion** or **MaximumVersion** .</span></span>

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

### <span data-ttu-id="fbf5f-199">-Scope</span><span class="sxs-lookup"><span data-stu-id="fbf5f-199">-Scope</span></span>

<span data-ttu-id="fbf5f-200">指定模組的安裝範圍。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-200">Specifies the installation scope of the module.</span></span> <span data-ttu-id="fbf5f-201">此參數可接受的值為 **AllUsers** 和 **CurrentUser** 。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-201">The acceptable values for this parameter are **AllUsers** and **CurrentUser** .</span></span>

<span data-ttu-id="fbf5f-202">**AllUsers** 範圍會在可供電腦的所有使用者存取的位置中安裝模組：</span><span class="sxs-lookup"><span data-stu-id="fbf5f-202">The **AllUsers** scope installs modules in a location that is accessible to all users of the computer:</span></span>

`$env:ProgramFiles\PowerShell\Modules`

<span data-ttu-id="fbf5f-203">**CurrentUser** 會將模組安裝在只能供電腦目前使用者存取的位置。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-203">The **CurrentUser** installs modules in a location that is accessible only to the current user of the computer.</span></span> <span data-ttu-id="fbf5f-204">例如：</span><span class="sxs-lookup"><span data-stu-id="fbf5f-204">For example:</span></span>

`$home\Documents\PowerShell\Modules`

<span data-ttu-id="fbf5f-205">未定義 **範圍** 時，會根據 PowerShellGet 版本設定預設值。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-205">When no **Scope** is defined, the default is set based on the PowerShellGet version.</span></span>

- <span data-ttu-id="fbf5f-206">在 PowerShellGet 版本2.0.0 和更新版本中，預設值為 **CurrentUser** ，不需要提高安裝的許可權。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-206">In PowerShellGet versions 2.0.0 and above, the default is **CurrentUser** , which does not require elevation for install.</span></span>
- <span data-ttu-id="fbf5f-207">在 PowerShellGet 1.x 版中，預設值為 **AllUsers** ，這需要提高安裝的許可權。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-207">In PowerShellGet 1.x versions, the default is **AllUsers** , which requires elevation for install.</span></span>

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

### <span data-ttu-id="fbf5f-208">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="fbf5f-208">-SkipPublisherCheck</span></span>

<span data-ttu-id="fbf5f-209">可讓您安裝已存在於電腦上的較新版本模組。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-209">Allows you to install a newer version of a module that already exists on your computer.</span></span> <span data-ttu-id="fbf5f-210">例如，當現有的模組由受信任的發行者以數位方式簽署，但新版本未由受信任的發行者進行數位簽署。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-210">For example, when an existing module is digitally signed by a trusted publisher but the new version is not digitally signed by a trusted publisher.</span></span>

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

### <span data-ttu-id="fbf5f-211">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="fbf5f-211">-WhatIf</span></span>

<span data-ttu-id="fbf5f-212">顯示命令執行時所發生的情況 `Install-Module` 。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-212">Shows what would happen if an `Install-Module` command was run.</span></span> <span data-ttu-id="fbf5f-213">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-213">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="fbf5f-214">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fbf5f-214">CommonParameters</span></span>

<span data-ttu-id="fbf5f-215">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-215">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fbf5f-216">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-216">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fbf5f-217">輸入</span><span class="sxs-lookup"><span data-stu-id="fbf5f-217">INPUTS</span></span>

### <span data-ttu-id="fbf5f-218">PSRepositoryItemInfo</span><span class="sxs-lookup"><span data-stu-id="fbf5f-218">PSRepositoryItemInfo</span></span>

<span data-ttu-id="fbf5f-219">`Find-Module` 建立可以向下傳送到管線的 **PSRepositoryItemInfo** 物件 `Install-Module` 。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-219">`Find-Module` creates **PSRepositoryItemInfo** objects that can be sent down the pipeline to `Install-Module`.</span></span>

### <span data-ttu-id="fbf5f-220">System.String[]</span><span class="sxs-lookup"><span data-stu-id="fbf5f-220">System.String[]</span></span>

### <span data-ttu-id="fbf5f-221">管理. PSObject []</span><span class="sxs-lookup"><span data-stu-id="fbf5f-221">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="fbf5f-222">System.String</span><span class="sxs-lookup"><span data-stu-id="fbf5f-222">System.String</span></span>

### <span data-ttu-id="fbf5f-223">System.Management.Automation.PSCredential</span><span class="sxs-lookup"><span data-stu-id="fbf5f-223">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="fbf5f-224">System.Uri</span><span class="sxs-lookup"><span data-stu-id="fbf5f-224">System.Uri</span></span>

## <span data-ttu-id="fbf5f-225">輸出</span><span class="sxs-lookup"><span data-stu-id="fbf5f-225">OUTPUTS</span></span>

### <span data-ttu-id="fbf5f-226">PSRepositoryItemInfo。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-226">Microsoft.PowerShell.Commands.PSRepositoryItemInfo</span></span>

<span data-ttu-id="fbf5f-227">使用 **PassThru** 參數時，會 `Install-Module` 輸出模組的 **PSRepositoryItemInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-227">When using the **PassThru** parameter, `Install-Module` outputs a **PSRepositoryItemInfo** object for the module.</span></span> <span data-ttu-id="fbf5f-228">這是您從 Cmdlet 取得的相同資訊 `Find-Module` 。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-228">This is the same information that you get from the `Find-Module` cmdlet.</span></span>

## <span data-ttu-id="fbf5f-229">注意</span><span class="sxs-lookup"><span data-stu-id="fbf5f-229">NOTES</span></span>

<span data-ttu-id="fbf5f-230">`Install-Module` 在 Windows 7 或 Windows 2008 R2 和更新版本的 Windows 上，于 PowerShell 5.0 或更新版本上執行。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-230">`Install-Module` runs on PowerShell 5.0 or later releases, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

<span data-ttu-id="fbf5f-231">安全性最佳作法是在第一次執行任何 Cmdlet 或函式之前，先評估模組的程式碼。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-231">As a security best practice, evaluate a module's code before running any cmdlets or functions for the first time.</span></span> <span data-ttu-id="fbf5f-232">為了避免執行包含惡意程式碼的模組，安裝之後不會自動匯入已安裝的模組。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-232">To prevent running modules that contain malicious code, installed modules are not automatically imported after installation.</span></span>

<span data-ttu-id="fbf5f-233">如果存放庫中沒有 **名稱** 參數所指定的模組名稱，則會傳回 `Install-Module` 錯誤。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-233">If the module name specified by the **Name** parameter does not exist in the repository, `Install-Module` returns an error.</span></span>

<span data-ttu-id="fbf5f-234">若要安裝多個模組，請使用 **Name** 參數，並指定以逗號分隔的模組名稱陣列。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-234">To install multiple modules, use the **Name** parameter and specify a comma-separated array of module names.</span></span> <span data-ttu-id="fbf5f-235">如果您指定多個模組名稱，則無法使用 **MinimumVersion** 、 **MaximumVersion** 或 **RequiredVersion** 。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-235">If you specify multiple module names, you cannot use **MinimumVersion** , **MaximumVersion** , or **RequiredVersion** .</span></span> <span data-ttu-id="fbf5f-236">`Find-Module` 建立可以向下傳送到管線的 **PSRepositoryItemInfo** 物件 `Install-Module` 。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-236">`Find-Module` creates **PSRepositoryItemInfo** objects that can be sent down the pipeline to `Install-Module`.</span></span> <span data-ttu-id="fbf5f-237">管線是另一種方式，可指定要在單一命令中安裝的多個模組。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-237">The pipeline is another way to specify multiple modules to install in a single command.</span></span>

<span data-ttu-id="fbf5f-238">根據預設，會將 **AllUsers** 範圍的模組安裝在中 `$env:ProgramFiles\PowerShell\Modules` 。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-238">By default, modules for the scope of **AllUsers** are installed in `$env:ProgramFiles\PowerShell\Modules`.</span></span> <span data-ttu-id="fbf5f-239">當您安裝 PowerShell Desired State Configuration (DSC) 資源時，預設值會造成混淆。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-239">The default prevents confusion when you install PowerShell Desired State Configuration (DSC) resources.</span></span>

<span data-ttu-id="fbf5f-240">模組安裝失敗，而且如果 `.psm1` `.psd1` 資料夾內沒有相同名稱的、或，則無法匯入 `.dll` 。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-240">A module installation fails and cannot be imported if it does not have a `.psm1`, `.psd1`, or `.dll` of the same name within the folder.</span></span> <span data-ttu-id="fbf5f-241">使用 **Force** 參數來安裝模組。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-241">Use the **Force** parameter to install the module.</span></span>

<span data-ttu-id="fbf5f-242">如果現有模組的版本符合 **name** 參數所指定的名稱，且未使用 **MinimumVersion** 或 **RequiredVersion** 參數，則會以 `Install-Module` 無訊息模式繼續，但不會安裝模組。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-242">If an existing module's version matches the name specified by the **Name** parameter, and the **MinimumVersion** or **RequiredVersion** parameter are not used, `Install-Module` silently continues but does not install the module.</span></span>

<span data-ttu-id="fbf5f-243">如果現有模組的版本大於 **MinimumVersion** 參數的值，或等於 **RequiredVersion** 參數的值，則會以 `Install-Module` 無訊息模式繼續，但不會安裝模組。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-243">If an existing module's version is greater than the value of the **MinimumVersion** parameter, or equal to the value of the **RequiredVersion** parameter, `Install-Module` silently continues but does not install the module.</span></span>

<span data-ttu-id="fbf5f-244">如果現有的模組與 **MinimumVersion** 或 **RequiredVersion** 參數所指定的值不相符，則命令中會發生錯誤 `Install-Module` 。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-244">If the existing module does not match the values specified by the **MinimumVersion** or **RequiredVersion** parameters, an error occurs in the `Install-Module` command.</span></span> <span data-ttu-id="fbf5f-245">例如，如果現有已安裝模組的版本低於 **MinimumVersion** 值，或不等於 **RequiredVersion** 值。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-245">For example, if the version of the existing installed module is lower than the **MinimumVersion** value or not equal to the **RequiredVersion** value.</span></span>

<span data-ttu-id="fbf5f-246">模組安裝也會安裝模組發行者所需的任何相依模組。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-246">A module installation will also install any dependent modules specified as required by the module publisher.</span></span>
<span data-ttu-id="fbf5f-247">發行者會在模組資訊清單中指定所需的模組及其版本。</span><span class="sxs-lookup"><span data-stu-id="fbf5f-247">The publisher will specify the required modules and their versions in the module manifest.</span></span>

## <span data-ttu-id="fbf5f-248">相關連結</span><span class="sxs-lookup"><span data-stu-id="fbf5f-248">RELATED LINKS</span></span>

[<span data-ttu-id="fbf5f-249">Find-Module</span><span class="sxs-lookup"><span data-stu-id="fbf5f-249">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="fbf5f-250">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="fbf5f-250">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="fbf5f-251">Import-Module</span><span class="sxs-lookup"><span data-stu-id="fbf5f-251">Import-Module</span></span>](../Microsoft.PowerShell.Core/Import-Module.md)

[<span data-ttu-id="fbf5f-252">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="fbf5f-252">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="fbf5f-253">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="fbf5f-253">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="fbf5f-254">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="fbf5f-254">Uninstall-Module</span></span>](Uninstall-Module.md)

[<span data-ttu-id="fbf5f-255">Update-Module</span><span class="sxs-lookup"><span data-stu-id="fbf5f-255">Update-Module</span></span>](Update-Module.md)

[<span data-ttu-id="fbf5f-256">about_Module</span><span class="sxs-lookup"><span data-stu-id="fbf5f-256">about_Module</span></span>](../Microsoft.PowerShell.Core/About/about_Modules.md)
