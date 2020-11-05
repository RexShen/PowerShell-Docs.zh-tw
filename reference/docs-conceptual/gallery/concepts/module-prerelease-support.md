---
ms.date: 09/26/2017
title: 發行前模組版本
description: PowerShellGet 模組支援使用語意化版本控制系統，將版本大於 1.0.0 的模組標記為發行前版本。
ms.openlocfilehash: f794722f0a89f98f8f445ecd45dad9d3d2d7f3cb
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661521"
---
# <a name="prerelease-module-versions"></a><span data-ttu-id="cdfdc-103">發行前模組版本</span><span class="sxs-lookup"><span data-stu-id="cdfdc-103">Prerelease Module Versions</span></span>

<span data-ttu-id="cdfdc-104">從 1.6.0 版開始，PowerShellGet 和 PowerShell 資源庫支援將大於 1.0.0 的版本標記為發行前版本。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="cdfdc-105">在此功能之前，發行前版本套件僅限於以 0 開始的版本。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-105">Prior to this feature, prerelease packages were limited to having a version beginning with 0.</span></span> <span data-ttu-id="cdfdc-106">這些功能的目標是為 [SemVer 1.0.0 版](http://semver.org/spec/v1.0.0.html)版本設定慣例提供更好的支援，而不會中斷與 PowerShell 第 3 版及更新版本或 PowerShellGet 現有版本的回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="cdfdc-107">本主題著重在模組特有的功能。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-107">This topic focuses on the module-specific features.</span></span> <span data-ttu-id="cdfdc-108">指令碼的對應功能位於[指令碼的發行前版本](script-prerelease-support.md)主題中。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-108">The equivalent features for scripts are in the [Prerelease Versions of Scripts](script-prerelease-support.md) topic.</span></span> <span data-ttu-id="cdfdc-109">使用這些功能，發行者可以將模組或指令碼識別為 2.5.0-Alpha 版，並於稍後發行已準備好投入生產環境的 2.5.0 版以取代發行前版本。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-109">Using these features, publishers can identify a module or script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="cdfdc-110">概括而言，發行前版本的模組功能包括：</span><span class="sxs-lookup"><span data-stu-id="cdfdc-110">At a high level, the prerelease module features include:</span></span>

- <span data-ttu-id="cdfdc-111">將發行前版本字串新增至模組資訊清單的 PSData 區段，可將模組識別為發行前版本。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-111">Adding a Prerelease string to the PSData section of the module manifest identifies the module as a prerelease version.</span></span> <span data-ttu-id="cdfdc-112">當模組發行至 PowerShell 資源庫時，即會從資訊清單中擷取此資料，並將其用來識別發行前版本套件。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-112">When the module is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease packages.</span></span>
- <span data-ttu-id="cdfdc-113">取得發行前版本套件需要將 `-AllowPrerelease` 旗標加入到 PowerShellGet 命令 `Find-Module`、`Install-Module`、`Update-Module` 與 `Save-Module`。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-113">Acquiring prerelease packages requires adding `-AllowPrerelease` flag to the PowerShellGet commands `Find-Module`, `Install-Module`, `Update-Module`, and `Save-Module`.</span></span> <span data-ttu-id="cdfdc-114">如果未指定此旗標，則不會顯示發行前版本套件。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-114">If the flag is not specified, prerelease packages will not be shown.</span></span>
- <span data-ttu-id="cdfdc-115">`Find-Module`、`Get-InstalledModule` 所顯示的模組版本以及 PowerShell 資源庫中顯示的模組版本，將顯示為附加了發行前版本字串的單一字串，如同 2.5.0-alpha。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-115">Module versions displayed by `Find-Module`, `Get-InstalledModule`, and in the PowerShell Gallery will be displayed as a single string with the Prerelease string appended, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="cdfdc-116">以下包含這些功能的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-116">Details for the features are included below.</span></span>

<span data-ttu-id="cdfdc-117">這些變更不會影響已內建至 PowerShell 的模組版本支援，並且與 PowerShell 3.0、4.0 和 5 相容。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-117">These changes do not affect the module version support that is built into PowerShell, and are compatible with PowerShell 3.0, 4.0, and 5.</span></span>

## <a name="identifying-a-module-version-as-a-prerelease"></a><span data-ttu-id="cdfdc-118">將模組版本識別為發行前版本</span><span class="sxs-lookup"><span data-stu-id="cdfdc-118">Identifying a module version as a prerelease</span></span>

<span data-ttu-id="cdfdc-119">PowerShellGet 對發行前版本的支援需要使用模組資訊清單內的兩個欄位：</span><span class="sxs-lookup"><span data-stu-id="cdfdc-119">PowerShellGet support for prerelease versions requires the use of two fields within the Module Manifest:</span></span>

- <span data-ttu-id="cdfdc-120">如果使用發行前版本，模組資訊清單中包含的 ModuleVersion 必須是 3 段式版本，而且必須符合現有的 PowerShell 版本設定。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-120">The ModuleVersion included in the module manifest must be a 3-part version if a prerelease version is used, and must comply with existing PowerShell versioning.</span></span> <span data-ttu-id="cdfdc-121">版本格式為 A.B.C，其中 A、B 和 C 皆為整數。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-121">The version format would be A.B.C, where A, B, and C are all integers.</span></span>
- <span data-ttu-id="cdfdc-122">發行前版本字串指定於模組資訊清單中 PrivateData 的 PSData 區段。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-122">The Prerelease string is specified in the module manifest, in the PSData section of PrivateData.</span></span>

<span data-ttu-id="cdfdc-123">發行前版本字串的詳細需求如下。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-123">Detailed requirements on the Prerelease string are below.</span></span>

<span data-ttu-id="cdfdc-124">將模組定義為發行前版本的模組資訊清單的範例部分如下所示：</span><span class="sxs-lookup"><span data-stu-id="cdfdc-124">An example section of a module manifest that defines a module as a prerelease would look like the following:</span></span>

```powershell
@{
    ModuleVersion = '2.5.0'
    #---
    PrivateData = @{
        PSData = @{
            Prerelease = 'alpha'
        }
    }
}
```

<span data-ttu-id="cdfdc-125">發行前版本字串的詳細需求如下：</span><span class="sxs-lookup"><span data-stu-id="cdfdc-125">The detailed requirements for Prerelease string are:</span></span>

- <span data-ttu-id="cdfdc-126">只有當 Major.Minor.Build 的 ModuleVersion 為 3 個區段時，才能指定發行前版本字串。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-126">Prerelease string may only be specified when the ModuleVersion is 3 segments for Major.Minor.Build.</span></span> <span data-ttu-id="cdfdc-127">這與 SemVer 1.0.0 版相符。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-127">This aligns with SemVer v1.0.0.</span></span>
- <span data-ttu-id="cdfdc-128">連字號是組建編號和發行前版本字串之間的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-128">A hyphen is the delimiter between the Build number and the Prerelease string.</span></span> <span data-ttu-id="cdfdc-129">連字號只能作為第一個字元，包含在發行前版本字串中。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-129">A hyphen may be included in the Prerelease string as the first character, only.</span></span>
- <span data-ttu-id="cdfdc-130">發行前版本字串只能包含 ASCII 英數字元 [0-9A-Za-z-]。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-130">The Prerelease string may contain only ASCII alphanumerics [0-9A-Za-z-].</span></span> <span data-ttu-id="cdfdc-131">發行前版本字串最好是以英數字元開始，因為在掃描套件的清單時，可以更容易分辨這是發行前版本字串。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-131">It is a best practice to begin the Prerelease string with an alpha character, as it will be easier to identify that this is a prerelease version when scanning a list of packages.</span></span>
- <span data-ttu-id="cdfdc-132">目前只支援 SemVer 1.0.0 版的發行前版本字串。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-132">Only SemVer v1.0.0 prerelease strings are supported at this time.</span></span> <span data-ttu-id="cdfdc-133">發行前版本字串 **不得** 包含 SemVer 2.0 中允許使用的句號或 + [.+]。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-133">Prerelease string **must not** contain either period or + [.+], which are allowed in SemVer 2.0.</span></span>
- <span data-ttu-id="cdfdc-134">支援的發行前版本字串範例包括：-alpha、-alpha1、-BETA、-update20171020</span><span class="sxs-lookup"><span data-stu-id="cdfdc-134">Examples of supported Prerelease string are: -alpha, -alpha1, -BETA, -update20171020</span></span>

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a><span data-ttu-id="cdfdc-135">發行前版本設定對排序次序和安裝資料夾的影響</span><span class="sxs-lookup"><span data-stu-id="cdfdc-135">Prerelease versioning impact on sort order and installation folders</span></span>

<span data-ttu-id="cdfdc-136">使用發行前版本時，排序順序會變更，這在發行至 PowerShell 資源庫以及使用 PowerShellGet 命令安裝模組時非常重要。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-136">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing modules using PowerShellGet commands.</span></span> <span data-ttu-id="cdfdc-137">如果發行前版本字串是針對兩個模組指定，則排序順序是根據連字號後面的字串部分。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-137">If the Prerelease string is specified for two modules, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="cdfdc-138">因此，版本 2.5.0-alpha 小於 2.5.0-beta，而 2.5.0-beta 小於 2.5.0-gamma。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-138">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="cdfdc-139">如果兩個模組的 ModuleVersion 相同，而且只有一個具有發行前版本字串時，沒有發行前版本字串的模組會假設為已準備好投入生產環境的版本，並且會排序為比發行前版本 (包含發行前版本字串) 更高的版本。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-139">If two modules have the same ModuleVersion, and only one has a Prerelease string, the module without the Prerelease string is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version (which includes the Prerelease string).</span></span> <span data-ttu-id="cdfdc-140">例如，比較版本 2.5.0 和 2.5.0-beta 時，2.5.0 版會視為兩個版本中的較高版本。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-140">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="cdfdc-141">發行至 PowerShell 資源庫時，根據預設，所發行的模組版本必須比 PowerShell 資源庫中任何先前已發行的版本更高。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-141">When publishing to the PowerShell Gallery, by default the version of the module being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span>

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a><span data-ttu-id="cdfdc-142">使用 PowerShellGet 命令尋找並取得發行前版本套件</span><span class="sxs-lookup"><span data-stu-id="cdfdc-142">Finding and acquiring prerelease packages using PowerShellGet commands</span></span>

<span data-ttu-id="cdfdc-143">使用 PowerShellGet 的 Find-Module、Install-Module、Update-Module 和 Save-Module 命令處理發行前版本套件時，需要新增 -AllowPrerelease 旗標。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-143">Dealing with prerelease packages using PowerShellGet Find-Module, Install-Module, Update-Module, and Save-Module commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="cdfdc-144">如果已指定 -AllowPrerelease，則會包含現存的發行前版本套件。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-144">If -AllowPrerelease is specified, prerelease packages will be included if they are present.</span></span> <span data-ttu-id="cdfdc-145">如果未指定 -AllowPrerelease 旗標，則不會顯示發行前版本套件。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-145">If -AllowPrerelease flag is not specified, prerelease packages will not be shown.</span></span>

<span data-ttu-id="cdfdc-146">PowerShellGet 模組命令中此狀況的唯一例外是 Get-InstalledModule，以及在某些情況下的 Uninstall-Module。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-146">The only exceptions to this in the PowerShellGet module commands are Get-InstalledModule, and some cases with Uninstall-Module.</span></span>

- <span data-ttu-id="cdfdc-147">Get-InstalledModule 一律會自動顯示模組版本字串中的發行前版本資訊。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-147">Get-InstalledModule always will automatically show the prerelease information in the version string for modules.</span></span>
- <span data-ttu-id="cdfdc-148">Uninstall-Module 在 __未指定版本__ 時，預設將解除安裝最新的模組版本。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-148">Uninstall-Module will by default uninstall the most recent version of a module, if __no version__ is specified.</span></span> <span data-ttu-id="cdfdc-149">該行為尚未變更。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-149">That behavior has not changed.</span></span> <span data-ttu-id="cdfdc-150">但是，如果已使用 -RequiredVersion　指定了發行前版本，則需要 -AllowPrerelease。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-150">However, if a prerelease version is specified using -RequiredVersion, -AllowPrerelease will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="cdfdc-151">範例</span><span class="sxs-lookup"><span data-stu-id="cdfdc-151">Examples</span></span>

<span data-ttu-id="cdfdc-152">假設 PowerShell 資源庫有 TestPackage 模組的 1.8.0 版和 1.9.0-alpha 版。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-152">Assume the PowerShell Gallery has TestPackage module versions 1.8.0 and 1.9.0-alpha.</span></span> <span data-ttu-id="cdfdc-153">如果未指定 `-AllowPrerelease`，則只會傳回 1.8.0 版。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-153">If `-AllowPrerelease` is not specified, only version 1.8.0 will be returned.</span></span>

```powershell
find-module TestPackage
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.8.0          TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

```powershell
find-module TestPackage -AllowPrerelease
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.9.0-alpha    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

<span data-ttu-id="cdfdc-154">若要安裝發行前版本，請一律指定 -AllowPrerelease。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-154">To install a prerelease, always specify -AllowPrerelease.</span></span> <span data-ttu-id="cdfdc-155">只有指定發行前版本字串是不夠的。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-155">Specifying a prerelease version string is not sufficient.</span></span>

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha
```

```output
PackageManagement\Find-Package : No match was found for the specified search criteria and module name 'TestPackage'.
Try Get-PSRepository to see all available registered module repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exception
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage
```

<span data-ttu-id="cdfdc-156">前一個命令會失敗，是因為沒有指定 -AllowPrerelease。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-156">The previous command failed because -AllowPrerelease was not specified.</span></span> <span data-ttu-id="cdfdc-157">加入 `-AllowPrerelease` 就會成功。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-157">Adding `-AllowPrerelease` will result in success.</span></span>

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
Get-InstalledModule TestPackage
```

```output
Version         Name          Repository  Description
-------         ----          ----------  -----------
1.9.0-alpha     TestPackage   PSGallery   Package used to validate changes to the PowerShe...
```

<span data-ttu-id="cdfdc-158">如果模組的版本僅僅因為指定的發行前版本而有所不同，則不支援並行安裝模組的各版本。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-158">Side-by-side installation of versions of a module that differ only due to the prerelease specified is not supported.</span></span> <span data-ttu-id="cdfdc-159">使用 PowerShellGet 安裝模組時，透過使用 ModuleVersion 建立資料夾名稱，可並行安裝相同模組的不同版本。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-159">When installing a module using PowerShellGet, different versions of the same module are installed side-by-side by creating a folder name using the ModuleVersion.</span></span> <span data-ttu-id="cdfdc-160">不含發行前版本字串的 ModuleVersion 可作為資料夾名稱使用。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-160">The ModuleVersion, without the prerelease string, is used for the folder name.</span></span> <span data-ttu-id="cdfdc-161">如果使用者安裝 MyModule 2.5.0-alpha 版，它將安裝至 `MyModule\2.5.0` 資料夾。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-161">If a user installs MyModule version 2.5.0-alpha, it will be installed to the `MyModule\2.5.0` folder.</span></span> <span data-ttu-id="cdfdc-162">如果使用者接著安裝 2.5.0-beta，則 2.5.0-beta 版將 **覆寫**`MyModule\2.5.0` 資料夾的內容。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-162">If the user then installs 2.5.0-beta, the 2.5.0-beta version will **overwrite** the contents of the folder `MyModule\2.5.0`.</span></span> <span data-ttu-id="cdfdc-163">這種方法的其中一個優點是，安裝已準備好投入生產環境的版本之後，不需要解除安裝發行前版本。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-163">One advantage to this approach is that there is no need to un-install the prerelease version after installing the production-ready version.</span></span> <span data-ttu-id="cdfdc-164">下列範例示範預期的結果：</span><span class="sxs-lookup"><span data-stu-id="cdfdc-164">The example below shows what to expect:</span></span>

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-alpha     TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name            Repository  Description
-------        ----            ----------  -----------
1.9.0-beta     TestPackage     PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Update-Module TestPackage -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

```

<span data-ttu-id="cdfdc-165">如果未提供 -RequiredVersion，Uninstall-Module 將會移除最新的模組版本。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-165">Uninstall-Module will remove the latest version of a module when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="cdfdc-166">如果指定了 -RequiredVersio，而且是發行前版本，則必須將 -AllowPrerelease 新增至命令。</span><span class="sxs-lookup"><span data-stu-id="cdfdc-166">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
2.0.0-alpha1    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta

Uninstall-Module : The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Module], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninstall-Module

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
2.0.0-alpha1    TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...
```

## <a name="more-details"></a><span data-ttu-id="cdfdc-167">其他詳細資訊</span><span class="sxs-lookup"><span data-stu-id="cdfdc-167">More details</span></span>

- [<span data-ttu-id="cdfdc-168">發行前指令碼版本</span><span class="sxs-lookup"><span data-stu-id="cdfdc-168">Prerelease Script Versions</span></span>](script-prerelease-support.md)
- [<span data-ttu-id="cdfdc-169">Find-Module</span><span class="sxs-lookup"><span data-stu-id="cdfdc-169">Find-Module</span></span>](/powershell/module/powershellget/find-module)
- [<span data-ttu-id="cdfdc-170">Install-Module</span><span class="sxs-lookup"><span data-stu-id="cdfdc-170">Install-Module</span></span>](/powershell/module/powershellget/install-module)
- [<span data-ttu-id="cdfdc-171">Save-Module</span><span class="sxs-lookup"><span data-stu-id="cdfdc-171">Save-Module</span></span>](/powershell/module/powershellget/save-module)
- [<span data-ttu-id="cdfdc-172">Update-Module</span><span class="sxs-lookup"><span data-stu-id="cdfdc-172">Update-Module</span></span>](/powershell/module/powershellget/Update-Module)
- [<span data-ttu-id="cdfdc-173">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="cdfdc-173">Get-InstalledModule</span></span>](/powershell/module/powershellget/get-installedmodule)
- [<span data-ttu-id="cdfdc-174">UnInstall-Module</span><span class="sxs-lookup"><span data-stu-id="cdfdc-174">UnInstall-Module</span></span>](/powershell/module/powershellget/uninstall-module)
