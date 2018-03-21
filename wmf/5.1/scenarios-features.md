---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,設定"
title: "WMF 5.1 的新案例和功能"
ms.openlocfilehash: da3dfb2243c00e3faf637d3dbcb70016cfabb011
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="new-scenarios-and-features-in-wmf-51"></a><span data-ttu-id="51081-103">WMF 5.1 的新案例和功能</span><span class="sxs-lookup"><span data-stu-id="51081-103">New Scenarios and Features in WMF 5.1</span></span> #

> <span data-ttu-id="51081-104">注意：本資訊尚屬初始版本，後續有可能變更。</span><span class="sxs-lookup"><span data-stu-id="51081-104">Note: This information is preliminary and subject to change.</span></span>

## <a name="powershell-editions"></a><span data-ttu-id="51081-105">PowerShell 版本</span><span class="sxs-lookup"><span data-stu-id="51081-105">PowerShell Editions</span></span> ##
<span data-ttu-id="51081-106">從 5.1 版開始，PowerShell 提供代表各種功能集和平台相容性的不同版本。</span><span class="sxs-lookup"><span data-stu-id="51081-106">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="51081-107">**Desktop Edition︰**建置在 .NET Framework 上，與在完整使用量的 Windows 版本 (如 Server Core 和 Windows Desktop) 上執行之 PowerShell 版本的指令碼和模組相容。</span><span class="sxs-lookup"><span data-stu-id="51081-107">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="51081-108">**Core Edition︰**建置在 .NET Core 上，與在降低使用量的 Windows 版本 (如 Nano Server 和 Windows IoT) 上執行之 PowerShell 版本的指令碼和模組相容。</span><span class="sxs-lookup"><span data-stu-id="51081-108">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="51081-109">**深入了解使用 PowerShell 版本**</span><span class="sxs-lookup"><span data-stu-id="51081-109">**Learn more about using PowerShell Editions**</span></span>
- [<span data-ttu-id="51081-110">判斷執行的 PowerShell 版本</span><span class="sxs-lookup"><span data-stu-id="51081-110">Determine running edition of PowerShell</span></span>]()
- [<span data-ttu-id="51081-111">宣告特定 PowerShell 版本的模組相容性</span><span class="sxs-lookup"><span data-stu-id="51081-111">Declare a module's compatibility to specific PowerShell versions</span></span>]()
- [<span data-ttu-id="51081-112">依據 CompatiblePSEditions 篩選 Get-Module 結果</span><span class="sxs-lookup"><span data-stu-id="51081-112">Filter Get-Module results by CompatiblePSEditions</span></span>]()
- [<span data-ttu-id="51081-113">只有在相容的 PowerShell 版本上執行才會執行指令碼</span><span class="sxs-lookup"><span data-stu-id="51081-113">Prevent script execution unless run on a compatible edition of PowerShell</span></span>]()

## <a name="catalog-cmdlets"></a><span data-ttu-id="51081-114">類別目錄 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="51081-114">Catalog Cmdlets</span></span>  

<span data-ttu-id="51081-115">[Microsoft.PowerShell.Security](https://technet.microsoft.com/library/hh847877.aspx) 模組中新增了兩個新的 Cmdlet，它們會產生和驗證 Windows 類別目錄檔案。</span><span class="sxs-lookup"><span data-stu-id="51081-115">Two new cmdlets have been added in the [Microsoft.PowerShell.Security](https://technet.microsoft.com/library/hh847877.aspx) module; these generate and validate Windows catalog files.</span></span>  

###<a name="new-filecatalog"></a><span data-ttu-id="51081-116">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="51081-116">New-FileCatalog</span></span> 
--------------------------------

<span data-ttu-id="51081-117">New-FileCatalog 會建立 Windows 類別目錄檔案，供資料夾和檔案集合使用。</span><span class="sxs-lookup"><span data-stu-id="51081-117">New-FileCatalog creates a Windows catalog file for set of folders and files.</span></span> <span data-ttu-id="51081-118">此類別目錄檔案包含指定路徑中的所有檔案雜湊。</span><span class="sxs-lookup"><span data-stu-id="51081-118">This catalog file contains hashes for all files in specified paths.</span></span> <span data-ttu-id="51081-119">使用者可以散發資料夾集合以及代表這些資料夾的對應類別目錄檔案。</span><span class="sxs-lookup"><span data-stu-id="51081-119">Users can distribute the set of folders along with corresponding catalog file representing those folders.</span></span> <span data-ttu-id="51081-120">這項資訊對驗證資料夾在類別目錄建立後是否有任何變更，非常有用。</span><span class="sxs-lookup"><span data-stu-id="51081-120">This information is useful to validate whether any changes have been made to the folders since catalog creation time.</span></span>    

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
<span data-ttu-id="51081-121">支援類別目錄第 1 版和第 2 版。</span><span class="sxs-lookup"><span data-stu-id="51081-121">Catalog versions 1 and 2 are supported.</span></span> <span data-ttu-id="51081-122">第 1 版使用 SHA1 雜湊演算法建立檔案雜湊，第 2 版使用 SHA256。</span><span class="sxs-lookup"><span data-stu-id="51081-122">Version 1 uses the SHA1 hashing algorithm to create file hashes; version 2 uses SHA256.</span></span> <span data-ttu-id="51081-123">*Windows Server 2008 R2* 或 *Windows 7* 不支援第 2 版的類別目錄。</span><span class="sxs-lookup"><span data-stu-id="51081-123">Catalog version 2 is not supported on *Windows Server 2008 R2* or *Windows 7*.</span></span> <span data-ttu-id="51081-124">*Windows 8*、*Windows Server 2012* 和更新版本的作業系統，應該使用類別目錄第 2 版。</span><span class="sxs-lookup"><span data-stu-id="51081-124">You should use catalog version 2 on *Windows 8*, *Windows Server 2012*, and later operating systems.</span></span>  

![](../images/NewFileCatalog.jpg)

<span data-ttu-id="51081-125">這會建立類別目錄檔案。</span><span class="sxs-lookup"><span data-stu-id="51081-125">This creates the catalog file.</span></span> 

![](../images/CatalogFile1.jpg)  

![](../images/CatalogFile2.jpg) 

<span data-ttu-id="51081-126">若要驗證類別目錄檔案 (上例中為 Pester.cat) 的完整性，請使用 [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) Cmdlet 來加以簽署。</span><span class="sxs-lookup"><span data-stu-id="51081-126">To verify the integrity of catalog file (Pester.cat in above example), sign it using [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.</span></span>   


###<a name="test-filecatalog"></a><span data-ttu-id="51081-127">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="51081-127">Test-FileCatalog</span></span> 
--------------------------------

<span data-ttu-id="51081-128">Test-FileCatalog 會驗證代表資料夾集合的類別目錄。</span><span class="sxs-lookup"><span data-stu-id="51081-128">Test-FileCatalog validates the catalog representing a set of folders.</span></span> 

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

<span data-ttu-id="51081-129">此 Cmdlet 會比較所有的檔案雜湊及在 *catalog* 和 *disk* 中找到的相對路徑。</span><span class="sxs-lookup"><span data-stu-id="51081-129">This cmdlet compares all the files hashes and their relative paths found in *catalog* with ones on *disk*.</span></span> <span data-ttu-id="51081-130">如果檔案雜湊和路徑中偵測到任何不相符的項目，就會傳回 *ValidationFailed* 狀態。</span><span class="sxs-lookup"><span data-stu-id="51081-130">If it detects any mismatch between file hashes and paths it returns the status as *ValidationFailed*.</span></span> <span data-ttu-id="51081-131">使用者可以使用 *-Detailed* 參數來擷取此資訊的完整內容。</span><span class="sxs-lookup"><span data-stu-id="51081-131">Users can retrieve all this information by using the *-Detailed* parameter.</span></span> <span data-ttu-id="51081-132">它也會在 *Signature* 屬性中顯示類別目錄的簽署狀態，和呼叫 [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) Cmdlet 一模一樣。</span><span class="sxs-lookup"><span data-stu-id="51081-132">It also displays signing status of catalog in *Signature* property which is equivalent to calling [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) cmdlet on the catalog file.</span></span> <span data-ttu-id="51081-133">使用者也可以使用 *-FilesToSkip* 參數，在驗證期間略過任何檔案。</span><span class="sxs-lookup"><span data-stu-id="51081-133">Users can also skip any file during validation by using the *-FilesToSkip* parameter.</span></span> 


## <a name="module-analysis-cache"></a><span data-ttu-id="51081-134">模組分析快取</span><span class="sxs-lookup"><span data-stu-id="51081-134">Module Analysis Cache</span></span> ##
<span data-ttu-id="51081-135">從 WMF 5.1 開始，PowerShell 可以控制快取模組資料所用的檔案，例如匯出的命令。</span><span class="sxs-lookup"><span data-stu-id="51081-135">Starting with WMF 5.1, PowerShell provides control over the file that is used to cache data about a module, such as the commands it exports.</span></span>

<span data-ttu-id="51081-136">此快取預設儲存在 `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache` 檔案中。</span><span class="sxs-lookup"><span data-stu-id="51081-136">By default, this cache is stored in the file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span>
<span data-ttu-id="51081-137">快取一般在啟動同時搜尋命令時讀取，並在模組匯入一段時間後寫入背景執行緒。</span><span class="sxs-lookup"><span data-stu-id="51081-137">The cache is typically read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

<span data-ttu-id="51081-138">若要變更快取的預設位置，請先設定環境變數 `$env:PSModuleAnalysisCachePath` 再啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="51081-138">To change the default location of the cache, set the `$env:PSModuleAnalysisCachePath` environment variable before starting PowerShell.</span></span> <span data-ttu-id="51081-139">此環境變數的變更只會影響子處理程序。</span><span class="sxs-lookup"><span data-stu-id="51081-139">Changes to this environment variable will only affect children processes.</span></span> <span data-ttu-id="51081-140">該值應該命名 PowerShell 有權建立和寫入檔案的完整路徑 (包括檔名)。</span><span class="sxs-lookup"><span data-stu-id="51081-140">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span> <span data-ttu-id="51081-141">若要停用檔案快取，請將此值設定於無效的位置，例如︰</span><span class="sxs-lookup"><span data-stu-id="51081-141">To disable the file cache, set this value to an invalid location, for example:</span></span>

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

<span data-ttu-id="51081-142">這會將路徑設定到無效的裝置。</span><span class="sxs-lookup"><span data-stu-id="51081-142">This sets the path to an invalid device.</span></span> <span data-ttu-id="51081-143">如果 PowerShell 無法寫入該路徑，就不會傳回任何錯誤，但您可以藉由使用追蹤查看錯誤報告︰</span><span class="sxs-lookup"><span data-stu-id="51081-143">If PowerShell can't write to the path, no error is returned, but you can see error reporting by using a tracer:</span></span>

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

<span data-ttu-id="51081-144">寫出快取時，PowerShell 會檢查確認模組已不存在，避免不必要的大型快取。</span><span class="sxs-lookup"><span data-stu-id="51081-144">When writing out the cache, PowerShell will check for modules that no longer exist to avoid an unnecessarily large cache.</span></span>
<span data-ttu-id="51081-145">有時候不需要這些檢查，在此情況下，您可以透過設定下列項目關閉這些檢查：</span><span class="sxs-lookup"><span data-stu-id="51081-145">Sometimes these checks are not desirable, in which case you can turn them off by setting:</span></span>

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

<span data-ttu-id="51081-146">此環境變數設定會立即在目前的程序中生效。</span><span class="sxs-lookup"><span data-stu-id="51081-146">Setting this environment variable will take effect immediately in the current process.</span></span>

##<a name="specifying-module-version"></a><span data-ttu-id="51081-147">指定模組版本</span><span class="sxs-lookup"><span data-stu-id="51081-147">Specifying module version</span></span>

<span data-ttu-id="51081-148">在 WMF 5.1 中，`using module` 與 PowerShell 中其他模組相關的語法結構表現一致。</span><span class="sxs-lookup"><span data-stu-id="51081-148">In WMF 5.1, `using module` behaves the same way as other module-related constructions in PowerShell.</span></span> <span data-ttu-id="51081-149">以往，您無法指定特定的模組版本；如果有多個版本存在，這會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="51081-149">Previously, you had no way to specify a particular module version; if there were multiple versions present, this resulted in an error.</span></span>


<span data-ttu-id="51081-150">在 WMF 5.1 中：</span><span class="sxs-lookup"><span data-stu-id="51081-150">In WMF 5.1:</span></span>

* <span data-ttu-id="51081-151">您可以使用 [ModuleSpecification 建構函式 (雜湊表)](https://msdn.microsoft.com/library/jj136290)。</span><span class="sxs-lookup"><span data-stu-id="51081-151">You can use [ModuleSpecification Constructor (Hashtable)](https://msdn.microsoft.com/library/jj136290).</span></span> <span data-ttu-id="51081-152">此雜湊表與 `Get-Module -FullyQualifiedName` 的格式相同。</span><span class="sxs-lookup"><span data-stu-id="51081-152">This hash table has the same format as `Get-Module -FullyQualifiedName`.</span></span>

<span data-ttu-id="51081-153">**範例：**`using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span><span class="sxs-lookup"><span data-stu-id="51081-153">**Example:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span></span>

* <span data-ttu-id="51081-154">如果模組有多個版本，PowerShell 會使用與 `Import-Module` **相同的解析邏輯**，不傳回錯誤，和 `Import-Module` 及 `Import-DscResource` 的行為一樣。</span><span class="sxs-lookup"><span data-stu-id="51081-154">If there are multiple versions of the module, PowerShell uses the **same resolution logic** as `Import-Module` and doesn't return an error--the same behavior as `Import-Module` and `Import-DscResource`.</span></span>


##<a name="improvements-to-pester"></a><span data-ttu-id="51081-155">Pester 的改善</span><span class="sxs-lookup"><span data-stu-id="51081-155">Improvements to Pester</span></span>
<span data-ttu-id="51081-156">在 WMF 5.1 中，PowerShell 隨附的 Pester 版本已從 3.3.5 更新至 3.4.0 並附帶認可 https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e，讓 Pester 在 Nano 伺服器上有更好的表現。</span><span class="sxs-lookup"><span data-stu-id="51081-156">In WMF 5.1, the version of Pester that ships with PowerShell has been updated from 3.3.5 to 3.4.0, with the addition of commit https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, which enables better behavior for Pester on Nano Server.</span></span> 

<span data-ttu-id="51081-157">您可以調查 ChangeLog.md 檔案來檢視 3.3.5 版到 3.4.0 版之間的變更，位置在：https://github.com/pester/Pester/blob/master/CHANGELOG.md</span><span class="sxs-lookup"><span data-stu-id="51081-157">You can review the changes in versions 3.3.5 to 3.4.0 by inspecting the ChangeLog.md file at: https://github.com/pester/Pester/blob/master/CHANGELOG.md</span></span>

