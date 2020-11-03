---
description: 描述 Windows PowerShell 5.1 中包含的新功能。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/17/2018
online version: https://docs.microsoft.com/powershell/module/?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_PowerShell_5 1
ms.openlocfilehash: 567af048dd137c0287c6eba4ccc42a77055c0c92
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208740"
---
# <a name="about_windows_powershell_51"></a><span data-ttu-id="b6d72-104">about_Windows_PowerShell_5 1</span><span class="sxs-lookup"><span data-stu-id="b6d72-104">about_Windows_PowerShell_5.1</span></span>

## <a name="short-description"></a><span data-ttu-id="b6d72-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="b6d72-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="b6d72-106">描述 Windows PowerShell 5.1 中包含的新功能。</span><span class="sxs-lookup"><span data-stu-id="b6d72-106">Describes new features that are included in Windows PowerShell 5.1.</span></span>

## <a name="long-description"></a><span data-ttu-id="b6d72-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="b6d72-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="b6d72-108">Windows PowerShell 5.1 包含大量的新功能，可延伸其用途、改善其可用性，並可讓您更輕鬆且全面地控制及管理 Windows 環境。</span><span class="sxs-lookup"><span data-stu-id="b6d72-108">Windows PowerShell 5.1 includes significant new features that extend its use, improve its usability, and allow you to control and manage Windows-based environments more easily and comprehensively.</span></span>

<span data-ttu-id="b6d72-109">Windows PowerShell 5.1 與舊版相容。</span><span class="sxs-lookup"><span data-stu-id="b6d72-109">Windows PowerShell 5.1 is backward-compatible.</span></span> <span data-ttu-id="b6d72-110">針對 Windows PowerShell 4.0、Windows PowerShell 3.0 和 Windows PowerShell 2.0 所設計的 Cmdlet、提供者、模組、嵌入式管理單元、腳本、函式及設定檔，通常會在 Windows PowerShell 5.1 的情況下運作，而不會有任何變更。</span><span class="sxs-lookup"><span data-stu-id="b6d72-110">Cmdlets, providers, modules, snap-ins, scripts, functions, and profiles that were designed for Windows PowerShell 4.0, Windows PowerShell 3.0, and Windows PowerShell 2.0 generally work in Windows PowerShell 5.1 without changes.</span></span>

- <span data-ttu-id="b6d72-111">新的 Cmdlet︰本機使用者和群組；Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="b6d72-111">New cmdlets: local users and groups; Get-ComputerInfo</span></span>
- <span data-ttu-id="b6d72-112">PowerShellGet 改善功能包括強制執行已簽署的模組，以及安裝 JEA 模組</span><span class="sxs-lookup"><span data-stu-id="b6d72-112">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="b6d72-113">PackageManagement 新增對容器、CBS 安裝、以執行檔為基礎的安裝、封包封裝的支援</span><span class="sxs-lookup"><span data-stu-id="b6d72-113">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="b6d72-114">DSC 和 PowerShell 類別的偵錯改善</span><span class="sxs-lookup"><span data-stu-id="b6d72-114">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="b6d72-115">安全性增強功能包括強制執行來自提取伺服器的目錄簽署模組，以及在使用 PowerShellGet Cmdlet 時加以強制執行</span><span class="sxs-lookup"><span data-stu-id="b6d72-115">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="b6d72-116">回應數個使用者要求和問題</span><span class="sxs-lookup"><span data-stu-id="b6d72-116">Responses to a number of user requests and issues</span></span>

<span data-ttu-id="b6d72-117">預設會在 Windows Server 2016 和 Windows 10 上安裝 Windows PowerShell 5.1。</span><span class="sxs-lookup"><span data-stu-id="b6d72-117">Windows PowerShell 5.1 is installed by default on Windows Server 2016 and Windows 10.</span></span> <span data-ttu-id="b6d72-118">若要在 Windows Server 2012 R2、Windows 8.1 企業版或 Windows 8.1 Pro 上安裝 Windows PowerShell 5.1，請參閱 [安裝和設定 WMF 5.1](/powershell/scripting/wmf/setup/install-configure)。</span><span class="sxs-lookup"><span data-stu-id="b6d72-118">To install Windows PowerShell 5.1 on Windows Server 2012 R2, Windows 8.1 Enterprise, or Windows 8.1 Pro, see [Install and Configure WMF 5.1](/powershell/scripting/wmf/setup/install-configure).</span></span>
<span data-ttu-id="b6d72-119">安裝 Windows Management Framework 5.1 之前，請務必先閱讀下載詳細資料，並符合所有系統需求。</span><span class="sxs-lookup"><span data-stu-id="b6d72-119">Be sure to read the download details, and meet all system requirements, before you install Windows Management Framework 5.1.</span></span>

<span data-ttu-id="b6d72-120">您也可以在 [Windows PowerShell 的新功能](/powershell/scripting/windows-powershell/whats-new/what-s-new-in-windows-powershell-50)中，閱讀 Windows PowerShell 5.1 的變更。</span><span class="sxs-lookup"><span data-stu-id="b6d72-120">You can also read about changes to Windows PowerShell 5.1 in [What's New in Windows PowerShell](/powershell/scripting/windows-powershell/whats-new/what-s-new-in-windows-powershell-50).</span></span>

## <a name="new-scenarios-and-features-in-wmf-51"></a><span data-ttu-id="b6d72-121">WMF 5.1 的新案例和功能</span><span class="sxs-lookup"><span data-stu-id="b6d72-121">New Scenarios and Features in WMF 5.1</span></span>

> <span data-ttu-id="b6d72-122">注意：本資訊尚屬初始版本，後續有可能變更。</span><span class="sxs-lookup"><span data-stu-id="b6d72-122">Note: This information is preliminary and subject to change.</span></span>

### <a name="powershell-editions"></a><span data-ttu-id="b6d72-123">PowerShell 版本</span><span class="sxs-lookup"><span data-stu-id="b6d72-123">PowerShell Editions</span></span>
<span data-ttu-id="b6d72-124">從 5.1 版開始，PowerShell 提供代表各種功能集和平台相容性的不同版本。</span><span class="sxs-lookup"><span data-stu-id="b6d72-124">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="b6d72-125">**Desktop Edition：** 建置在 .NET Framework 上，並與目標為完整版 Windows (Server Core 和 Windows Desktop 等) 上執行之 PowerShell 版本的指令碼和模組相容。</span><span class="sxs-lookup"><span data-stu-id="b6d72-125">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="b6d72-126">**Core Edition：** 建置在 .NET Core 上，並與目標為縮減版 Windows (Nano Server 和 Windows IoT 等) 上執行之 PowerShell 版本的指令碼和模組相容。</span><span class="sxs-lookup"><span data-stu-id="b6d72-126">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="b6d72-127">**深入了解使用 PowerShell 版本**</span><span class="sxs-lookup"><span data-stu-id="b6d72-127">**Learn more about using PowerShell Editions**</span></span>

- [<span data-ttu-id="b6d72-128">使用 PSVersionTable 來判斷執行的 PowerShell 版本</span><span class="sxs-lookup"><span data-stu-id="b6d72-128">Determine running edition of PowerShell using $PSVersionTable</span></span>](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [<span data-ttu-id="b6d72-129">使用 PSEdition 參數並依據 CompatiblePSEditions 篩選 Get-Module 結果</span><span class="sxs-lookup"><span data-stu-id="b6d72-129">Filter Get-Module results by CompatiblePSEditions using PSEdition parameter</span></span>](/powershell/module/microsoft.powershell.core/get-module)
- [<span data-ttu-id="b6d72-130">只有在相容的 PowerShell 版本上執行才會執行指令碼</span><span class="sxs-lookup"><span data-stu-id="b6d72-130">Prevent script execution unless run on a compatible edition of PowerShell</span></span>](/powershell/scripting/gallery/concepts/script-psedition-support)
- [<span data-ttu-id="b6d72-131">宣告特定 PowerShell 版本的模組相容性</span><span class="sxs-lookup"><span data-stu-id="b6d72-131">Declare a module's compatibility to specific PowerShell versions</span></span>](/powershell/scripting/gallery/concepts/module-psedition-support)

### <a name="catalog-cmdlets"></a><span data-ttu-id="b6d72-132">類別目錄 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b6d72-132">Catalog Cmdlets</span></span>

<span data-ttu-id="b6d72-133">[Microsoft.PowerShell.Security](/previous-versions/windows/powershell-scripting/hh847877(v=wps.640)) 模組中新增了兩個新的 Cmdlet，它們會產生和驗證 Windows 類別目錄檔案。</span><span class="sxs-lookup"><span data-stu-id="b6d72-133">Two new cmdlets have been added in the [Microsoft.PowerShell.Security](/previous-versions/windows/powershell-scripting/hh847877(v=wps.640)) module; these generate and validate Windows catalog files.</span></span>

#### <a name="new-filecatalog"></a><span data-ttu-id="b6d72-134">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="b6d72-134">New-FileCatalog</span></span>

<span data-ttu-id="b6d72-135">New-FileCatalog 會建立 Windows 類別目錄檔案，供資料夾和檔案集合使用。</span><span class="sxs-lookup"><span data-stu-id="b6d72-135">New-FileCatalog creates a Windows catalog file for set of folders and files.</span></span>
<span data-ttu-id="b6d72-136">此類別目錄檔案包含指定路徑中的所有檔案雜湊。</span><span class="sxs-lookup"><span data-stu-id="b6d72-136">This catalog file contains hashes for all files in specified paths.</span></span> <span data-ttu-id="b6d72-137">使用者可以散發資料夾集合以及代表這些資料夾的對應類別目錄檔案。</span><span class="sxs-lookup"><span data-stu-id="b6d72-137">Users can distribute the set of folders along with corresponding catalog file representing those folders.</span></span> <span data-ttu-id="b6d72-138">這項資訊對驗證資料夾在類別目錄建立後是否有任何變更，非常有用。</span><span class="sxs-lookup"><span data-stu-id="b6d72-138">This information is useful to validate whether any changes have been made to the folders since catalog creation time.</span></span>

```
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>]
 [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

<span data-ttu-id="b6d72-139">支援類別目錄第 1 版和第 2 版。</span><span class="sxs-lookup"><span data-stu-id="b6d72-139">Catalog versions 1 and 2 are supported.</span></span> <span data-ttu-id="b6d72-140">第 1 版使用 SHA1 雜湊演算法建立檔案雜湊，第 2 版使用 SHA256。</span><span class="sxs-lookup"><span data-stu-id="b6d72-140">Version 1 uses the SHA1 hashing algorithm to create file hashes; version 2 uses SHA256.</span></span> <span data-ttu-id="b6d72-141">*Windows Server 2008 R2* 或 *Windows 7* 不支援第 2 版的類別目錄。</span><span class="sxs-lookup"><span data-stu-id="b6d72-141">Catalog version 2 is not supported on *Windows Server 2008 R2* or *Windows 7* .</span></span> <span data-ttu-id="b6d72-142">*Windows 8* 、 *Windows Server 2012* 和更新版本的作業系統，應該使用類別目錄第 2 版。</span><span class="sxs-lookup"><span data-stu-id="b6d72-142">You should use catalog version 2 on *Windows 8* , *Windows Server 2012* , and later operating systems.</span></span>

<span data-ttu-id="b6d72-143">若要驗證類別目錄檔案 (上例中為 Pester.cat) 的完整性，請使用 [Set-AuthenticodeSignature](/powershell/module/microsoft.powershell.security/set-authenticodesignature) Cmdlet 來加以簽署。</span><span class="sxs-lookup"><span data-stu-id="b6d72-143">To verify the integrity of catalog file (Pester.cat in above example), sign it using [Set-AuthenticodeSignature](/powershell/module/microsoft.powershell.security/set-authenticodesignature) cmdlet.</span></span>

#### <a name="test-filecatalog"></a><span data-ttu-id="b6d72-144">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="b6d72-144">Test-FileCatalog</span></span>

<span data-ttu-id="b6d72-145">Test-FileCatalog 會驗證代表資料夾集合的類別目錄。</span><span class="sxs-lookup"><span data-stu-id="b6d72-145">Test-FileCatalog validates the catalog representing a set of folders.</span></span>

```
Test-FileCatalog [-Detailed] [-FilesToSkip <String[]>]
 [-CatalogFilePath] <String> [[-Path] <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

<span data-ttu-id="b6d72-146">此 Cmdlet 會比較所有的檔案雜湊及在 *catalog* 和 *disk* 中找到的相對路徑。</span><span class="sxs-lookup"><span data-stu-id="b6d72-146">This cmdlet compares all the files hashes and their relative paths found in *catalog* with ones on *disk* .</span></span> <span data-ttu-id="b6d72-147">如果檔案雜湊和路徑中偵測到任何不相符的項目，就會傳回 *ValidationFailed* 狀態。</span><span class="sxs-lookup"><span data-stu-id="b6d72-147">If it detects any mismatch between file hashes and paths it returns the status as *ValidationFailed* .</span></span> <span data-ttu-id="b6d72-148">使用者可以使用 *-Detailed* 參數來擷取此資訊的完整內容。</span><span class="sxs-lookup"><span data-stu-id="b6d72-148">Users can retrieve all this information by using the *-Detailed* parameter.</span></span> <span data-ttu-id="b6d72-149">它也會在 *Signature* 屬性中顯示類別目錄的簽署狀態，和呼叫 [Get-AuthenticodeSignature](/powershell/module/microsoft.powershell.security/get-authenticodesignature) Cmdlet 一模一樣。</span><span class="sxs-lookup"><span data-stu-id="b6d72-149">It also displays signing status of catalog in *Signature* property which is equivalent to calling [Get-AuthenticodeSignature](/powershell/module/microsoft.powershell.security/get-authenticodesignature) cmdlet on the catalog file.</span></span> <span data-ttu-id="b6d72-150">使用者也可以使用 *-FilesToSkip* 參數，在驗證期間略過任何檔案。</span><span class="sxs-lookup"><span data-stu-id="b6d72-150">Users can also skip any file during validation by using the *-FilesToSkip* parameter.</span></span>

### <a name="module-analysis-cache"></a><span data-ttu-id="b6d72-151">模組分析快取</span><span class="sxs-lookup"><span data-stu-id="b6d72-151">Module Analysis Cache</span></span>

<span data-ttu-id="b6d72-152">從 WMF 5.1 開始，PowerShell 可以控制快取模組資料所用的檔案，例如匯出的命令。</span><span class="sxs-lookup"><span data-stu-id="b6d72-152">Starting with WMF 5.1, PowerShell provides control over the file that is used to cache data about a module, such as the commands it exports.</span></span>

<span data-ttu-id="b6d72-153">此快取預設儲存在 `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache` 檔案中。</span><span class="sxs-lookup"><span data-stu-id="b6d72-153">By default, this cache is stored in the file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span> <span data-ttu-id="b6d72-154">快取一般在啟動同時搜尋命令時讀取，並在模組匯入一段時間後寫入背景執行緒。</span><span class="sxs-lookup"><span data-stu-id="b6d72-154">The cache is typically read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

<span data-ttu-id="b6d72-155">若要變更快取的預設位置，請先設定環境變數 `$env:PSModuleAnalysisCachePath` 再啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="b6d72-155">To change the default location of the cache, set the `$env:PSModuleAnalysisCachePath` environment variable before starting PowerShell.</span></span> <span data-ttu-id="b6d72-156">此環境變數的變更只會影響子處理程序。</span><span class="sxs-lookup"><span data-stu-id="b6d72-156">Changes to this environment variable will only affect children processes.</span></span> <span data-ttu-id="b6d72-157">該值應該命名 PowerShell 有權建立和寫入檔案的完整路徑 (包括檔名)。</span><span class="sxs-lookup"><span data-stu-id="b6d72-157">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span> <span data-ttu-id="b6d72-158">若要停用檔案快取，請將此值設定於無效的位置，例如︰</span><span class="sxs-lookup"><span data-stu-id="b6d72-158">To disable the file cache, set this value to an invalid location, for example:</span></span>

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

<span data-ttu-id="b6d72-159">這會將路徑設定到無效的裝置。</span><span class="sxs-lookup"><span data-stu-id="b6d72-159">This sets the path to an invalid device.</span></span> <span data-ttu-id="b6d72-160">如果 PowerShell 無法寫入該路徑，就不會傳回任何錯誤，但您可以藉由使用追蹤查看錯誤報告︰</span><span class="sxs-lookup"><span data-stu-id="b6d72-160">If PowerShell can't write to the path, no error is returned, but you can see error reporting by using a tracer:</span></span>

```powershell
Trace-Command -PSHost -Name Modules -Expression {
  Import-Module Microsoft.PowerShell.Management -Force
}
```

<span data-ttu-id="b6d72-161">寫出快取時，PowerShell 會檢查確認模組已不存在，避免不必要的大型快取。</span><span class="sxs-lookup"><span data-stu-id="b6d72-161">When writing out the cache, PowerShell will check for modules that no longer exist to avoid an unnecessarily large cache.</span></span> <span data-ttu-id="b6d72-162">有時候不需要這些檢查，在此情況下，您可以透過設定下列項目關閉這些檢查：</span><span class="sxs-lookup"><span data-stu-id="b6d72-162">Sometimes these checks are not desirable, in which case you can turn them off by setting:</span></span>

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

<span data-ttu-id="b6d72-163">此環境變數設定會立即在目前的程序中生效。</span><span class="sxs-lookup"><span data-stu-id="b6d72-163">Setting this environment variable will take effect immediately in the current process.</span></span>

### <a name="specifying-module-version"></a><span data-ttu-id="b6d72-164">指定模組版本</span><span class="sxs-lookup"><span data-stu-id="b6d72-164">Specifying module version</span></span>

<span data-ttu-id="b6d72-165">在 WMF 5.1 中，`using module` 與 PowerShell 中其他模組相關的語法結構表現一致。</span><span class="sxs-lookup"><span data-stu-id="b6d72-165">In WMF 5.1, `using module` behaves the same way as other module-related constructions in PowerShell.</span></span> <span data-ttu-id="b6d72-166">以往，您無法指定特定的模組版本；如果有多個版本存在，這會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="b6d72-166">Previously, you had no way to specify a particular module version; if there were multiple versions present, this resulted in an error.</span></span>

<span data-ttu-id="b6d72-167">在 WMF 5.1 中：</span><span class="sxs-lookup"><span data-stu-id="b6d72-167">In WMF 5.1:</span></span>

* <span data-ttu-id="b6d72-168">您可以使用 [ModuleSpecification 建構函式 (雜湊表)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor)。</span><span class="sxs-lookup"><span data-stu-id="b6d72-168">You can use [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor).</span></span>
  <span data-ttu-id="b6d72-169">此雜湊表與 `Get-Module -FullyQualifiedName` 的格式相同。</span><span class="sxs-lookup"><span data-stu-id="b6d72-169">This hash table has the same format as `Get-Module -FullyQualifiedName`.</span></span>

  <span data-ttu-id="b6d72-170">**範例：** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span><span class="sxs-lookup"><span data-stu-id="b6d72-170">**Example:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span></span>

* <span data-ttu-id="b6d72-171">如果模組有多個版本，PowerShell 會使用與 `Import-Module`**相同的解析邏輯** ，不傳回錯誤，和 `Import-Module` 及 `Import-DscResource` 的行為一樣。</span><span class="sxs-lookup"><span data-stu-id="b6d72-171">If there are multiple versions of the module, PowerShell uses the **same resolution logic** as `Import-Module` and doesn't return an error--the same behavior as `Import-Module` and `Import-DscResource`.</span></span>

### <a name="improvements-to-pester"></a><span data-ttu-id="b6d72-172">Pester 的改善</span><span class="sxs-lookup"><span data-stu-id="b6d72-172">Improvements to Pester</span></span>

<span data-ttu-id="b6d72-173">在 WMF 5.1 中，隨附于 PowerShell 的 Pester 版本已從3.3.5 更新為3.4.0，並新增了 GitHub [PR # 484](https://github.com/pester/Pester/pull/484)，可針對 Nano Server 上的 Pester 提供更佳的行為。</span><span class="sxs-lookup"><span data-stu-id="b6d72-173">In WMF 5.1, the version of Pester that ships with PowerShell has been updated from 3.3.5 to 3.4.0, with the addition of GitHub [PR# 484](https://github.com/pester/Pester/pull/484), which enables better behavior for Pester on Nano Server.</span></span>

<span data-ttu-id="b6d72-174">您可以調查 ChangeLog.md 檔案來檢視 3.3.5 版到 3.4.0 版之間的變更，位置在：https://github.com/pester/Pester/blob/master/CHANGELOG.md</span><span class="sxs-lookup"><span data-stu-id="b6d72-174">You can review the changes in versions 3.3.5 to 3.4.0 by inspecting the ChangeLog.md file at: https://github.com/pester/Pester/blob/master/CHANGELOG.md</span></span>

## <a name="keywords"></a><span data-ttu-id="b6d72-175">關鍵 字</span><span class="sxs-lookup"><span data-stu-id="b6d72-175">KEYWORDS</span></span>

<span data-ttu-id="b6d72-176">Windows PowerShell 5.1 的新功能</span><span class="sxs-lookup"><span data-stu-id="b6d72-176">What's New in Windows PowerShell 5.1</span></span>
