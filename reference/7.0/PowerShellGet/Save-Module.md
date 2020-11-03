---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 11/11/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/save-module?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Module
ms.openlocfilehash: 1a41cc743bfb2572e1ab99bf161c2f13174bd163
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201823"
---
# <span data-ttu-id="73d79-103">Save-Module</span><span class="sxs-lookup"><span data-stu-id="73d79-103">Save-Module</span></span>

## <span data-ttu-id="73d79-104">概要</span><span class="sxs-lookup"><span data-stu-id="73d79-104">SYNOPSIS</span></span>
<span data-ttu-id="73d79-105">將模組及其相依性儲存在本機電腦上，但不會安裝模組。</span><span class="sxs-lookup"><span data-stu-id="73d79-105">Saves a module and its dependencies on the local computer but doesn't install the module.</span></span>

## <span data-ttu-id="73d79-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="73d79-106">SYNTAX</span></span>

### <span data-ttu-id="73d79-107">NameAndPathParameterSet (預設) </span><span class="sxs-lookup"><span data-stu-id="73d79-107">NameAndPathParameterSet (Default)</span></span>

```
Save-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="73d79-108">NameAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="73d79-108">NameAndLiteralPathParameterSet</span></span>

```
Save-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="73d79-109">InputObjectAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="73d79-109">InputObjectAndLiteralPathParameterSet</span></span>

```
Save-Module [-InputObject] <PSObject[]> -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="73d79-110">InputObjectAndPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="73d79-110">InputObjectAndPathParameterSet</span></span>

```
Save-Module [-InputObject] <PSObject[]> [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="73d79-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="73d79-111">DESCRIPTION</span></span>

<span data-ttu-id="73d79-112">此 `Save-Module` Cmdlet 會從已註冊的存放庫下載模組和任何相依性。</span><span class="sxs-lookup"><span data-stu-id="73d79-112">The `Save-Module` cmdlet downloads a module and any dependencies from a registered repository.</span></span>
<span data-ttu-id="73d79-113">`Save-Module` 下載並儲存模組的最新版本。</span><span class="sxs-lookup"><span data-stu-id="73d79-113">`Save-Module` downloads and saves the most current version of a module.</span></span> <span data-ttu-id="73d79-114">檔案會儲存至本機電腦上的指定路徑。</span><span class="sxs-lookup"><span data-stu-id="73d79-114">The files are saved to a specified path on the local computer.</span></span> <span data-ttu-id="73d79-115">未安裝此模組，但內容可供系統管理員進行檢查。</span><span class="sxs-lookup"><span data-stu-id="73d79-115">The module isn't installed, but the contents are available for inspection by an administrator.</span></span> <span data-ttu-id="73d79-116">然後可以將儲存的模組複製到 `$env:PSModulePath` 離線電腦的適當位置。</span><span class="sxs-lookup"><span data-stu-id="73d79-116">The saved module can then be copied into the appropriate `$env:PSModulePath` location of the offline machine.</span></span>

<span data-ttu-id="73d79-117">`Get-PSRepository` 顯示本機電腦的已註冊存放庫。</span><span class="sxs-lookup"><span data-stu-id="73d79-117">`Get-PSRepository` displays the local computer's registered repositories.</span></span> <span data-ttu-id="73d79-118">您可以使用 `Find-Module` Cmdlet 來搜尋已註冊的存放庫。</span><span class="sxs-lookup"><span data-stu-id="73d79-118">You can use the `Find-Module` cmdlet to search registered repositories.</span></span>

## <span data-ttu-id="73d79-119">範例</span><span class="sxs-lookup"><span data-stu-id="73d79-119">EXAMPLES</span></span>

### <span data-ttu-id="73d79-120">範例1：儲存模組</span><span class="sxs-lookup"><span data-stu-id="73d79-120">Example 1: Save a module</span></span>

<span data-ttu-id="73d79-121">在此範例中，模組和其相依性會儲存至本機電腦。</span><span class="sxs-lookup"><span data-stu-id="73d79-121">In this example, a module and its dependencies are saved to the local computer.</span></span>

```powershell
Save-Module -Name PowerShellGet -Path C:\Test\Modules -Repository PSGallery
Get-ChildItem -Path C:\Test\Modules
```

```Output
    Directory: C:\Test\Modules

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/1/2019     13:31                PackageManagement
d-----         7/1/2019     13:31                PowerShellGet
```

<span data-ttu-id="73d79-122">`Save-Module` 使用 **Name** 參數來指定模組（ **PowerShellGet** ）。</span><span class="sxs-lookup"><span data-stu-id="73d79-122">`Save-Module` uses the **Name** parameter to specify the module, **PowerShellGet** .</span></span> <span data-ttu-id="73d79-123">**Path** 參數指定要儲存已下載模組的位置。</span><span class="sxs-lookup"><span data-stu-id="73d79-123">The **Path** parameter specifies where to store the downloaded module.</span></span> <span data-ttu-id="73d79-124">存放 **庫** 參數會指定已註冊的存放庫 **PSGallery** 。</span><span class="sxs-lookup"><span data-stu-id="73d79-124">The **Repository** parameter specifies a registered repository, **PSGallery** .</span></span> <span data-ttu-id="73d79-125">下載完成之後，會 `Get-ChildItem` 顯示儲存檔案的 **路徑** 內容。</span><span class="sxs-lookup"><span data-stu-id="73d79-125">After the download is finished, `Get-ChildItem` displays the contents of **Path** where the files are stored.</span></span>

### <span data-ttu-id="73d79-126">範例2：儲存特定版本的模組</span><span class="sxs-lookup"><span data-stu-id="73d79-126">Example 2: Save a specific version of a module</span></span>

<span data-ttu-id="73d79-127">此範例示範如何使用參數（例如 **MaximumVersion** 或 **RequiredVersion** ）來指定模組版本。</span><span class="sxs-lookup"><span data-stu-id="73d79-127">This example shows how to use a parameter such as **MaximumVersion** , or **RequiredVersion** to specify a module version.</span></span>

```powershell
Save-Module -Name PowerShellGet -Path C:\Test\Modules -Repository PSGallery -MaximumVersion 2.1.0
Get-ChildItem -Path C:\Test\Modules\PowerShellGet\
```

```Output
    Directory: C:\Test\Modules\PowerShellGet

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/1/2019     13:40                2.1.0
```

<span data-ttu-id="73d79-128">`Save-Module` 使用 **Name** 參數來指定模組（ **PowerShellGet** ）。</span><span class="sxs-lookup"><span data-stu-id="73d79-128">`Save-Module` uses the **Name** parameter to specify the module, **PowerShellGet** .</span></span> <span data-ttu-id="73d79-129">**Path** 參數指定要儲存已下載模組的位置。</span><span class="sxs-lookup"><span data-stu-id="73d79-129">The **Path** parameter specifies where to store the downloaded module.</span></span> <span data-ttu-id="73d79-130">存放 **庫** 參數會指定已註冊的存放庫 **PSGallery** 。</span><span class="sxs-lookup"><span data-stu-id="73d79-130">The **Repository** parameter specifies a registered repository, **PSGallery** .</span></span> <span data-ttu-id="73d79-131">**MaximumVersion** 指定下載並儲存版本 **2.1.0** 。</span><span class="sxs-lookup"><span data-stu-id="73d79-131">**MaximumVersion** specifies that version **2.1.0** is downloaded and saved.</span></span> <span data-ttu-id="73d79-132">下載完成之後，會 `Get-ChildItem` 顯示儲存檔案的 **路徑** 內容。</span><span class="sxs-lookup"><span data-stu-id="73d79-132">After the download is finished, `Get-ChildItem` displays the contents of **Path** where the files are stored.</span></span>

### <span data-ttu-id="73d79-133">範例3：尋找並儲存特定版本的模組</span><span class="sxs-lookup"><span data-stu-id="73d79-133">Example 3: Find and save a specific version of a module</span></span>

<span data-ttu-id="73d79-134">在此範例中，在存放庫中找到必要的模組版本，並儲存到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="73d79-134">In this example, a required module version is found in the repository and saved to the local computer.</span></span>

```powershell
Find-Module -Name PowerShellGet -Repository PSGallery -RequiredVersion 1.6.5 |
  Save-Module -Path C:\Test\Modules
Get-ChildItem -Path C:\Test\Modules\PowerShellGet
```

```Output
    Directory: C:\Test\Modules\PowerShellGet

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/1/2019     14:04                1.6.5
```

<span data-ttu-id="73d79-135">`Find-Module` 使用 **Name** 參數來指定模組（ **PowerShellGet** ）。</span><span class="sxs-lookup"><span data-stu-id="73d79-135">`Find-Module` uses the **Name** parameter to specify the module, **PowerShellGet** .</span></span> <span data-ttu-id="73d79-136">存放 **庫** 參數會指定已註冊的存放庫 **PSGallery** 。</span><span class="sxs-lookup"><span data-stu-id="73d79-136">The **Repository** parameter specifies a registered repository, **PSGallery** .</span></span> <span data-ttu-id="73d79-137">**RequiredVersion** 指定版本 **1.6.5** 。</span><span class="sxs-lookup"><span data-stu-id="73d79-137">**RequiredVersion** specifies version **1.6.5** .</span></span>

<span data-ttu-id="73d79-138">物件會向下傳送到管線 `Save-Module` 。</span><span class="sxs-lookup"><span data-stu-id="73d79-138">The object is sent down the pipeline to `Save-Module`.</span></span> <span data-ttu-id="73d79-139">**Path** 參數指定要儲存已下載模組的位置。</span><span class="sxs-lookup"><span data-stu-id="73d79-139">The **Path** parameter specifies where to store the downloaded module.</span></span> <span data-ttu-id="73d79-140">下載完成之後，會 `Get-ChildItem` 顯示儲存檔案的 **路徑** 內容。</span><span class="sxs-lookup"><span data-stu-id="73d79-140">After the download is finished, `Get-ChildItem` displays the contents of **Path** where the files are stored.</span></span>

## <span data-ttu-id="73d79-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="73d79-141">PARAMETERS</span></span>

### <span data-ttu-id="73d79-142">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="73d79-142">-AcceptLicense</span></span>

<span data-ttu-id="73d79-143">如果套件需要，則自動接受授權合約。</span><span class="sxs-lookup"><span data-stu-id="73d79-143">Automatically accept the license agreement if the package requires it.</span></span>

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

### <span data-ttu-id="73d79-144">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="73d79-144">-AllowPrerelease</span></span>

<span data-ttu-id="73d79-145">可讓您儲存標記為發行前版本的模組。</span><span class="sxs-lookup"><span data-stu-id="73d79-145">Allows you to save a module marked as a prerelease.</span></span>

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

### <span data-ttu-id="73d79-146">-Confirm</span><span class="sxs-lookup"><span data-stu-id="73d79-146">-Confirm</span></span>

<span data-ttu-id="73d79-147">在執行之前提示您確認 `Save-Module` 。</span><span class="sxs-lookup"><span data-stu-id="73d79-147">Prompts you for confirmation before running the `Save-Module`.</span></span>

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

### <span data-ttu-id="73d79-148">-Credential</span><span class="sxs-lookup"><span data-stu-id="73d79-148">-Credential</span></span>

<span data-ttu-id="73d79-149">指定有權儲存模組的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="73d79-149">Specifies a user account that has rights to save a module.</span></span>

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

### <span data-ttu-id="73d79-150">-Force</span><span class="sxs-lookup"><span data-stu-id="73d79-150">-Force</span></span>

<span data-ttu-id="73d79-151">強制 `Save-Module` 執行而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="73d79-151">Forces `Save-Module` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="73d79-152">-InputObject</span><span class="sxs-lookup"><span data-stu-id="73d79-152">-InputObject</span></span>

<span data-ttu-id="73d79-153">接受 **PSRepositoryItemInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="73d79-153">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="73d79-154">例如，輸出 `Find-Module` 到變數，並使用該變數作為 **InputObject** 引數。</span><span class="sxs-lookup"><span data-stu-id="73d79-154">For example, output `Find-Module` to a variable and use that variable as the **InputObject** argument.</span></span>

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

### <span data-ttu-id="73d79-155">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="73d79-155">-LiteralPath</span></span>

<span data-ttu-id="73d79-156">指定一個或多個位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="73d79-156">Specifies a path to one or more locations.</span></span> <span data-ttu-id="73d79-157">**LiteralPath** 參數的值會完全依照輸入的方式使用。</span><span class="sxs-lookup"><span data-stu-id="73d79-157">The value of the **LiteralPath** parameter is used exactly as entered.</span></span> <span data-ttu-id="73d79-158">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="73d79-158">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="73d79-159">如果路徑包含 escape 字元，請用單引號括住。</span><span class="sxs-lookup"><span data-stu-id="73d79-159">If the path includes escape characters, enclose them in single quotation marks.</span></span> <span data-ttu-id="73d79-160">PowerShell 不會將以單引號括住的任何字元視為 escape 序列來解讀。</span><span class="sxs-lookup"><span data-stu-id="73d79-160">PowerShell does not interpret any characters enclosed in single quotation marks as escape sequences.</span></span>

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

### <span data-ttu-id="73d79-161">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="73d79-161">-MaximumVersion</span></span>

<span data-ttu-id="73d79-162">指定要儲存之模組的最大或最新版本。</span><span class="sxs-lookup"><span data-stu-id="73d79-162">Specifies the maximum, or newest, version of the module to save.</span></span> <span data-ttu-id="73d79-163">在相同的命令中不能使用 **MaximumVersion** 和 **RequiredVersion** 參數。</span><span class="sxs-lookup"><span data-stu-id="73d79-163">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="73d79-164">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="73d79-164">-MinimumVersion</span></span>

<span data-ttu-id="73d79-165">指定要儲存之單一模組的最小版本。</span><span class="sxs-lookup"><span data-stu-id="73d79-165">Specifies the minimum version of a single module to save.</span></span> <span data-ttu-id="73d79-166">如果您嘗試安裝多個模組，就無法新增此參數。</span><span class="sxs-lookup"><span data-stu-id="73d79-166">You cannot add this parameter if you are attempting to install multiple modules.</span></span> <span data-ttu-id="73d79-167">**MinimumVersion** 和 **RequiredVersion** 參數無法在相同的命令中使用。</span><span class="sxs-lookup"><span data-stu-id="73d79-167">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="73d79-168">-Name</span><span class="sxs-lookup"><span data-stu-id="73d79-168">-Name</span></span>

<span data-ttu-id="73d79-169">指定要儲存的模組名稱陣列。</span><span class="sxs-lookup"><span data-stu-id="73d79-169">Specifies an array of names of modules to save.</span></span>

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

### <span data-ttu-id="73d79-170">-Path</span><span class="sxs-lookup"><span data-stu-id="73d79-170">-Path</span></span>

<span data-ttu-id="73d79-171">指定本機電腦上儲存已儲存模組的位置。</span><span class="sxs-lookup"><span data-stu-id="73d79-171">Specifies the location on the local computer to store a saved module.</span></span> <span data-ttu-id="73d79-172">接受萬用字元。</span><span class="sxs-lookup"><span data-stu-id="73d79-172">Accepts wildcard characters.</span></span>

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

### <span data-ttu-id="73d79-173">-Proxy</span><span class="sxs-lookup"><span data-stu-id="73d79-173">-Proxy</span></span>

<span data-ttu-id="73d79-174">指定要求的 proxy 伺服器，而不是直接連接到網際網路資源。</span><span class="sxs-lookup"><span data-stu-id="73d79-174">Specifies a proxy server for the request, rather than connecting directly to the internet resource.</span></span>

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

### <span data-ttu-id="73d79-175">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="73d79-175">-ProxyCredential</span></span>

<span data-ttu-id="73d79-176">指定具有使用 **Proxy** 參數所指定 Proxy 伺服器之權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="73d79-176">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="73d79-177">-Repository</span><span class="sxs-lookup"><span data-stu-id="73d79-177">-Repository</span></span>

<span data-ttu-id="73d79-178">指定由執行註冊之存放庫的易記名稱 `Register-PSRepository` 。</span><span class="sxs-lookup"><span data-stu-id="73d79-178">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span> <span data-ttu-id="73d79-179">用 `Get-PSRepository` 來顯示已註冊的存放庫。</span><span class="sxs-lookup"><span data-stu-id="73d79-179">Use `Get-PSRepository` to display registered repositories.</span></span>

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

### <span data-ttu-id="73d79-180">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="73d79-180">-RequiredVersion</span></span>

<span data-ttu-id="73d79-181">指定要儲存之模組的確切版本號碼。</span><span class="sxs-lookup"><span data-stu-id="73d79-181">Specifies the exact version number of the module to save.</span></span>

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

### <span data-ttu-id="73d79-182">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="73d79-182">-WhatIf</span></span>

<span data-ttu-id="73d79-183">顯示執行時所發生的情況 `Save-Module` 。</span><span class="sxs-lookup"><span data-stu-id="73d79-183">Shows what would happen if the `Save-Module` runs.</span></span> <span data-ttu-id="73d79-184">不會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="73d79-184">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="73d79-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="73d79-185">CommonParameters</span></span>

<span data-ttu-id="73d79-186">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="73d79-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="73d79-187">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="73d79-187">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="73d79-188">輸入</span><span class="sxs-lookup"><span data-stu-id="73d79-188">INPUTS</span></span>

### <span data-ttu-id="73d79-189">System.String[]</span><span class="sxs-lookup"><span data-stu-id="73d79-189">System.String[]</span></span>

### <span data-ttu-id="73d79-190">管理. PSObject []</span><span class="sxs-lookup"><span data-stu-id="73d79-190">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="73d79-191">System.String</span><span class="sxs-lookup"><span data-stu-id="73d79-191">System.String</span></span>

### <span data-ttu-id="73d79-192">System.Uri</span><span class="sxs-lookup"><span data-stu-id="73d79-192">System.Uri</span></span>

### <span data-ttu-id="73d79-193">System.Management.Automation.PSCredential</span><span class="sxs-lookup"><span data-stu-id="73d79-193">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="73d79-194">輸出</span><span class="sxs-lookup"><span data-stu-id="73d79-194">OUTPUTS</span></span>

### <span data-ttu-id="73d79-195">System.Object</span><span class="sxs-lookup"><span data-stu-id="73d79-195">System.Object</span></span>

## <span data-ttu-id="73d79-196">注意</span><span class="sxs-lookup"><span data-stu-id="73d79-196">NOTES</span></span>

## <span data-ttu-id="73d79-197">相關連結</span><span class="sxs-lookup"><span data-stu-id="73d79-197">RELATED LINKS</span></span>
