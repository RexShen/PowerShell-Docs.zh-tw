---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,設定
title: WMF 5.x 版本資訊
ms.openlocfilehash: 8bdc423234cf0b104b72b1bee1de35e50783d8a4
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855763"
---
# <a name="windows-management-framework-wmf-5x-release-notes"></a><span data-ttu-id="1ec7c-103">Windows Management Framework (WMF) 5.x 版本資訊</span><span class="sxs-lookup"><span data-stu-id="1ec7c-103">Windows Management Framework (WMF) 5.x Release Notes</span></span>

## <a name="wmf-50-changes"></a><span data-ttu-id="1ec7c-104">WMF 5.0 變更</span><span class="sxs-lookup"><span data-stu-id="1ec7c-104">WMF 5.0 Changes</span></span>

- <span data-ttu-id="1ec7c-105">PowerShell 5.0 會新增新的結構化**資訊**串流</span><span class="sxs-lookup"><span data-stu-id="1ec7c-105">PowerShell 5.0 adds a new structured **Information** stream</span></span>
- <span data-ttu-id="1ec7c-106">對 DSC 的改進包括四個新 DSC 資源：</span><span class="sxs-lookup"><span data-stu-id="1ec7c-106">Improvements to DSC including four new DSC resources:</span></span>
  - <span data-ttu-id="1ec7c-107">WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="1ec7c-107">WindowsFeatureSet</span></span>
  - <span data-ttu-id="1ec7c-108">WindowsOptionalFeatureSet</span><span class="sxs-lookup"><span data-stu-id="1ec7c-108">WindowsOptionalFeatureSet</span></span>
  - <span data-ttu-id="1ec7c-109">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="1ec7c-109">ServiceSet</span></span>
  - <span data-ttu-id="1ec7c-110">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="1ec7c-110">ProcessSet</span></span>
- <span data-ttu-id="1ec7c-111">已新增 Just Enough Administration，可透過 PowerShell 遠端來啟用以角色為基礎的系統管理</span><span class="sxs-lookup"><span data-stu-id="1ec7c-111">Added Just Enough Administration to enable role-based administration through PowerShell remoting</span></span>
- <span data-ttu-id="1ec7c-112">PowerShell 5.0 會擴充語言以包含使用者定義的類別和列舉</span><span class="sxs-lookup"><span data-stu-id="1ec7c-112">PowerShell 5.0 extends the language to include user-defined classes and enumerations</span></span>
- <span data-ttu-id="1ec7c-113">已改進 PowerShell ISE 中的偵錯功能，並新增了遠端偵錯</span><span class="sxs-lookup"><span data-stu-id="1ec7c-113">Improved debugging features in PowerShell ISE and added remote debugging</span></span>
- <span data-ttu-id="1ec7c-114">已新增 PowerShellGet 和 PackageManagement 模組</span><span class="sxs-lookup"><span data-stu-id="1ec7c-114">Added the PowerShellGet and PackageManagement modules</span></span>
- <span data-ttu-id="1ec7c-115">已增強 PowerShell 指令碼記錄和文字記錄</span><span class="sxs-lookup"><span data-stu-id="1ec7c-115">Enhanced PowerShell script logging and transcripts</span></span>
- <span data-ttu-id="1ec7c-116">新增密碼編譯訊息語法 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1ec7c-116">Add Cryptographic Message Syntax cmdlets</span></span>
- <span data-ttu-id="1ec7c-117">WMF 5.0 包含適用於 Windows 的 NetworkSwitchManager 模組</span><span class="sxs-lookup"><span data-stu-id="1ec7c-117">WMF 5.0 includes the NetworkSwitchManager module for Windows</span></span>
- <span data-ttu-id="1ec7c-118">已新增 Microsoft.PowerShell.ODataUtils 模組</span><span class="sxs-lookup"><span data-stu-id="1ec7c-118">Added the Microsoft.PowerShell.ODataUtils module</span></span>
- <span data-ttu-id="1ec7c-119">已新增支援軟體清查記錄 (SIL)</span><span class="sxs-lookup"><span data-stu-id="1ec7c-119">Added support for Software Inventory Logging (SIL)</span></span>
- <span data-ttu-id="1ec7c-120">提供新的或更新的 Cmdlet 來回應使用者要求和問題</span><span class="sxs-lookup"><span data-stu-id="1ec7c-120">Sever new or update cmdlets in response to user requests and issues</span></span>

## <a name="wmf-51-changes"></a><span data-ttu-id="1ec7c-121">WMF 5.1 變更</span><span class="sxs-lookup"><span data-stu-id="1ec7c-121">WMF 5.1 Changes</span></span>

<span data-ttu-id="1ec7c-122">WMF 5.1 包含已搭配 Windows Server 2016 發行的 PowerShell、WMI、WinRM，以及軟體清查記錄 (SIL) 元件。</span><span class="sxs-lookup"><span data-stu-id="1ec7c-122">WMF 5.1 includes the PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span> <span data-ttu-id="1ec7c-123">WMF 5.1 可以安裝於 Windows 7、Windows 8.1、Windows Server 2008 R2、2012 及 2012 R2 上，並提供數個對 WMF 5.0 的改進，包括：</span><span class="sxs-lookup"><span data-stu-id="1ec7c-123">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides several improvements over WMF 5.0 including:</span></span>

- <span data-ttu-id="1ec7c-124">新的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1ec7c-124">New cmdlets</span></span>
- <span data-ttu-id="1ec7c-125">PowerShellGet 改善功能包括強制執行已簽署的模組，以及安裝 JEA 模組</span><span class="sxs-lookup"><span data-stu-id="1ec7c-125">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="1ec7c-126">PackageManagement 新增對容器、CBS 安裝、以執行檔為基礎的安裝、封包封裝的支援</span><span class="sxs-lookup"><span data-stu-id="1ec7c-126">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="1ec7c-127">DSC 和 PowerShell 類別的偵錯改善</span><span class="sxs-lookup"><span data-stu-id="1ec7c-127">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="1ec7c-128">安全性增強功能包括強制執行來自提取伺服器的目錄簽署模組，以及在使用 PowerShellGet Cmdlet 時加以強制執行</span><span class="sxs-lookup"><span data-stu-id="1ec7c-128">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="1ec7c-129">回應數個使用者要求和問題</span><span class="sxs-lookup"><span data-stu-id="1ec7c-129">Responses to a number of user requests and issues</span></span>

## <a name="powershell-editions"></a><span data-ttu-id="1ec7c-130">PowerShell 版本</span><span class="sxs-lookup"><span data-stu-id="1ec7c-130">PowerShell Editions</span></span>

<span data-ttu-id="1ec7c-131">從 5.1 版開始，PowerShell 適用於代表各種功能集及平台相容性的不同版本。</span><span class="sxs-lookup"><span data-stu-id="1ec7c-131">Starting with version 5.1, PowerShell is available in different editions that denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="1ec7c-132">**Desktop Edition：** 建置在 .NET Framework 上，與在完整使用量的 Windows 版本 (如 Server Core 和 Windows Desktop) 上執行的 PowerShell 指令碼和模組目標版本相容相容。</span><span class="sxs-lookup"><span data-stu-id="1ec7c-132">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="1ec7c-133">**Core Edition：** 建置在 .NET Core 上，與在降低使用量的 Windows 版本 (如 Nano Server 和 Windows IoT) 上執行的 PowerShell 指令碼和模組目標版本相容。</span><span class="sxs-lookup"><span data-stu-id="1ec7c-133">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

### <a name="learn-more-about-using-powershell-editions"></a><span data-ttu-id="1ec7c-134">深入了解使用 PowerShell 版本</span><span class="sxs-lookup"><span data-stu-id="1ec7c-134">Learn more about using PowerShell Editions</span></span>

- [<span data-ttu-id="1ec7c-135">使用 PSVersionTable 來判斷執行的 PowerShell 版本</span><span class="sxs-lookup"><span data-stu-id="1ec7c-135">Determine running edition of PowerShell using $PSVersionTable</span></span>](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [<span data-ttu-id="1ec7c-136">使用 PSEdition 參數並依據 CompatiblePSEditions 篩選 Get-Module 結果</span><span class="sxs-lookup"><span data-stu-id="1ec7c-136">Filter Get-Module results by CompatiblePSEditions using PSEdition parameter</span></span>](/powershell/module/microsoft.powershell.core/get-module)
- [<span data-ttu-id="1ec7c-137">只有在相容的 PowerShell 版本上執行才會執行指令碼</span><span class="sxs-lookup"><span data-stu-id="1ec7c-137">Prevent script execution unless run on a compatible edition of PowerShell</span></span>](/powershell/gallery/concepts/script-psedition-support)
- [<span data-ttu-id="1ec7c-138">宣告特定 PowerShell 版本的模組相容性</span><span class="sxs-lookup"><span data-stu-id="1ec7c-138">Declare a module's compatibility to specific PowerShell versions</span></span>](/powershell/gallery/concepts/module-psedition-support)

## <a name="module-analysis-cache"></a><span data-ttu-id="1ec7c-139">模組分析快取</span><span class="sxs-lookup"><span data-stu-id="1ec7c-139">Module Analysis Cache</span></span>

<span data-ttu-id="1ec7c-140">從 WMF 5.1 開始，PowerShell 可以控制快取模組資料所用的檔案，例如匯出的命令。</span><span class="sxs-lookup"><span data-stu-id="1ec7c-140">Starting with WMF 5.1, PowerShell provides control over the file that is used to cache data about a module, such as the commands it exports.</span></span>

<span data-ttu-id="1ec7c-141">此快取預設儲存在 `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache` 檔案中。</span><span class="sxs-lookup"><span data-stu-id="1ec7c-141">By default, this cache is stored in the file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span> <span data-ttu-id="1ec7c-142">快取一般在啟動同時搜尋命令時讀取，並在模組匯入一段時間後寫入背景執行緒。</span><span class="sxs-lookup"><span data-stu-id="1ec7c-142">The cache is typically read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

<span data-ttu-id="1ec7c-143">若要變更快取的預設位置，請先設定環境變數 `$env:PSModuleAnalysisCachePath` 再啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="1ec7c-143">To change the default location of the cache, set the `$env:PSModuleAnalysisCachePath` environment variable before starting PowerShell.</span></span> <span data-ttu-id="1ec7c-144">此環境變數的變更只會影響子處理程序。</span><span class="sxs-lookup"><span data-stu-id="1ec7c-144">Changes to this environment variable will only affect children processes.</span></span> <span data-ttu-id="1ec7c-145">該值應該命名 PowerShell 有權建立和寫入檔案的完整路徑 (包括檔名)。</span><span class="sxs-lookup"><span data-stu-id="1ec7c-145">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span> <span data-ttu-id="1ec7c-146">若要停用檔案快取，請將此值設定於無效的位置，例如︰</span><span class="sxs-lookup"><span data-stu-id="1ec7c-146">To disable the file cache, set this value to an invalid location, for example:</span></span>

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

<span data-ttu-id="1ec7c-147">這會將路徑設定到無效的裝置。</span><span class="sxs-lookup"><span data-stu-id="1ec7c-147">This sets the path to an invalid device.</span></span> <span data-ttu-id="1ec7c-148">如果 PowerShell 無法寫入該路徑，就不會傳回任何錯誤，但您可以藉由使用追蹤查看錯誤報告︰</span><span class="sxs-lookup"><span data-stu-id="1ec7c-148">If PowerShell can't write to the path, no error is returned, but you can see error reporting by using a tracer:</span></span>

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

<span data-ttu-id="1ec7c-149">寫出快取時，PowerShell 會檢查確認模組已不存在，避免不必要的大型快取。</span><span class="sxs-lookup"><span data-stu-id="1ec7c-149">When writing out the cache, PowerShell will check for modules that no longer exist to avoid an unnecessarily large cache.</span></span> <span data-ttu-id="1ec7c-150">有時候不需要這些檢查，在此情況下，您可以透過設定下列項目關閉這些檢查：</span><span class="sxs-lookup"><span data-stu-id="1ec7c-150">Sometimes these checks are not desirable, in which case you can turn them off by setting:</span></span>

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

<span data-ttu-id="1ec7c-151">此環境變數設定會立即在目前的程序中生效。</span><span class="sxs-lookup"><span data-stu-id="1ec7c-151">Setting this environment variable will take effect immediately in the current process.</span></span>

## <a name="specifying-module-version"></a><span data-ttu-id="1ec7c-152">指定模組版本</span><span class="sxs-lookup"><span data-stu-id="1ec7c-152">Specifying module version</span></span>

<span data-ttu-id="1ec7c-153">在 WMF 5.1 中，`using module` 與 PowerShell 中其他模組相關的語法結構表現一致。</span><span class="sxs-lookup"><span data-stu-id="1ec7c-153">In WMF 5.1, `using module` behaves the same way as other module-related constructions in PowerShell.</span></span>
<span data-ttu-id="1ec7c-154">以往，您無法指定特定的模組版本；如果有多個版本存在，這會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="1ec7c-154">Previously, you had no way to specify a particular module version; if there were multiple versions present, this resulted in an error.</span></span>

<span data-ttu-id="1ec7c-155">在 WMF 5.1 中：</span><span class="sxs-lookup"><span data-stu-id="1ec7c-155">In WMF 5.1:</span></span>

- <span data-ttu-id="1ec7c-156">您可以使用 [ModuleSpecification 建構函式 (雜湊表)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_)。</span><span class="sxs-lookup"><span data-stu-id="1ec7c-156">You can use [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>
  <span data-ttu-id="1ec7c-157">此雜湊表與 `Get-Module -FullyQualifiedName` 的格式相同。</span><span class="sxs-lookup"><span data-stu-id="1ec7c-157">This hash table has the same format as `Get-Module -FullyQualifiedName`.</span></span>

  <span data-ttu-id="1ec7c-158">**範例：**`using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span><span class="sxs-lookup"><span data-stu-id="1ec7c-158">**Example:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span></span>

- <span data-ttu-id="1ec7c-159">如果模組有多個版本，PowerShell 會使用與 `Import-Module` **相同的解析邏輯**，不傳回錯誤，和 `Import-Module` 及 `Import-DscResource` 的行為一樣。</span><span class="sxs-lookup"><span data-stu-id="1ec7c-159">If there are multiple versions of the module, PowerShell uses the **same resolution logic** as `Import-Module` and doesn't return an error--the same behavior as `Import-Module` and `Import-DscResource`.</span></span>

## <a name="improvements-to-pester"></a><span data-ttu-id="1ec7c-160">Pester 的改善</span><span class="sxs-lookup"><span data-stu-id="1ec7c-160">Improvements to Pester</span></span>

<span data-ttu-id="1ec7c-161">在 WMF 5.1 中，PowerShell 隨附的 Pester 版本已從 3.3.5 更新為 3.4.0。</span><span class="sxs-lookup"><span data-stu-id="1ec7c-161">In WMF 5.1, the version of Pester that ships with PowerShell has been updated from 3.3.5 to 3.4.0.</span></span>
<span data-ttu-id="1ec7c-162">此更新讓 Pester 在 Nano 伺服器上有更好的表現。</span><span class="sxs-lookup"><span data-stu-id="1ec7c-162">This update enables better behavior for Pester on Nano Server.</span></span>

<span data-ttu-id="1ec7c-163">您可以藉由檢查 GitHub 存放庫中的 [ChangeLog.md](https://github.com/pester/Pester/blob/master/CHANGELOG.md) 檔案，來檢閱 Pester 中的變更。</span><span class="sxs-lookup"><span data-stu-id="1ec7c-163">You can review the changes in Pest by inspecting the [ChangeLog](https://github.com/pester/Pester/blob/master/CHANGELOG.md) in the GitHub repository.</span></span>
