---
ms.date: 2017-09-26
contributor: keithb
ms.topic: reference
keywords: "資源庫,powershell,cmdlet,psget"
title: PrereleaseModule
ms.openlocfilehash: d2c629d0e0ec0d4a4adafe5994a37d3985d13a06
ms.sourcegitcommit: 58371abe9db4b9a0e4e1eb82d39a9f9e187355f9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2017
---
# <a name="prerelease-module-versions"></a><span data-ttu-id="8924a-103">發行前模組版本</span><span class="sxs-lookup"><span data-stu-id="8924a-103">Prerelease Module Versions</span></span>
<span data-ttu-id="8924a-104">從 1.6.0 版開始，PowerShellGet 和 PowerShell 資源庫支援將大於 1.0.0 的版本標記為發行前版本。</span><span class="sxs-lookup"><span data-stu-id="8924a-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="8924a-105">在此功能之前，發行前版本項目僅限於以 0 開始的版本。</span><span class="sxs-lookup"><span data-stu-id="8924a-105">Prior to this feature, prerelease items were limited to having a version beginning with 0.</span></span> <span data-ttu-id="8924a-106">這些功能的目標是為 [SemVer 1.0.0 版](http://semver.org/spec/v1.0.0.html)版本設定慣例提供更好的支援，而不會中斷與 PowerShell 第 3 版及更新版本或 PowerShellGet 現有版本的回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="8924a-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="8924a-107">本主題著重在模組特有的功能。</span><span class="sxs-lookup"><span data-stu-id="8924a-107">This topic focuses on the module-specific features.</span></span> <span data-ttu-id="8924a-108">指令碼的對應功能位於[指令碼的發行前版本](../script/PrereleaseScript.md)主題中。</span><span class="sxs-lookup"><span data-stu-id="8924a-108">The equivalent features for scripts are in the [Prerelease Versions of Scripts](../script/PrereleaseScript.md) topic.</span></span> <span data-ttu-id="8924a-109">使用這些功能，發行者可以將模組或指令碼識別為 2.5.0-Alpha 版，並於稍後發行已準備好投入生產環境的 2.5.0 版以取代發行前版本。</span><span class="sxs-lookup"><span data-stu-id="8924a-109">Using these features, publishers can identify a module or script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span> 

<span data-ttu-id="8924a-110">概括而言，發行前版本的模組功能包括：</span><span class="sxs-lookup"><span data-stu-id="8924a-110">At a high level, the prerelease module features include:</span></span>

* <span data-ttu-id="8924a-111">將發行前版本字串新增至模組資訊清單的 PSData 區段，可將模組識別為發行前版本。</span><span class="sxs-lookup"><span data-stu-id="8924a-111">Adding a Prerelease string to the PSData section of the module manifest identifies the module as a prerelease version.</span></span> <span data-ttu-id="8924a-112">當模組發行至 PowerShell 資源庫時，即會從資訊清單中擷取這項資料，並將其用來識別發行前版本項目。</span><span class="sxs-lookup"><span data-stu-id="8924a-112">When the module is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease items.</span></span>
* <span data-ttu-id="8924a-113">取得發行前版本項目需要將 -AllowPrerelease 旗標新增至 Find-Module、Install-Module、Update-Module 和 Save-Module 等 PowerShellGet 命令。</span><span class="sxs-lookup"><span data-stu-id="8924a-113">Acquiring prerelease items requires adding -AllowPrerelease flag to the PowerShellGet commands Find-Module, Install-Module, Update-Module, and Save-Module.</span></span> <span data-ttu-id="8924a-114">如果未指定此旗標，則不會顯示發行前版本項目。</span><span class="sxs-lookup"><span data-stu-id="8924a-114">If the flag is not specified, prerelease items will not be shown.</span></span>  
* <span data-ttu-id="8924a-115">Find-Module、Get-InstalledModule 所顯示的模組版本以及 PowerShell 資源庫中顯示的模組版本，將顯示為附加了發行前版本字串的單一字串，如同 2.5.0-alpha。</span><span class="sxs-lookup"><span data-stu-id="8924a-115">Module versions displayed by Find-Module, Get-InstalledModule, and in the PowerShell Gallery will be displayed as a single string with the Prerelease string appended, as in 2.5.0-alpha.</span></span> 

<span data-ttu-id="8924a-116">以下包含這些功能的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="8924a-116">Details for the features are included below.</span></span> 

<span data-ttu-id="8924a-117">這些變更不會影響已內建至 PowerShell 的模組版本支援，並且與 PowerShell 3.0、4.0 和 5 相容。</span><span class="sxs-lookup"><span data-stu-id="8924a-117">These changes do not affect the module version support that is built into PowerShell, and are compatible with PowerShell 3.0, 4.0, and 5.</span></span> 

## <a name="identifying-a-module-version-as-a-prerelease"></a><span data-ttu-id="8924a-118">將模組版本識別為發行前版本</span><span class="sxs-lookup"><span data-stu-id="8924a-118">Identifying a module version as a prerelease</span></span> 

<span data-ttu-id="8924a-119">PowerShellGet 對發行前版本的支援需要使用模組資訊清單內的兩個欄位：</span><span class="sxs-lookup"><span data-stu-id="8924a-119">PowerShellGet support for prerelease versions requires the use of two fields within the Module Manifest:</span></span>

* <span data-ttu-id="8924a-120">如果使用發行前版本，模組資訊清單中包含的 ModuleVersion 必須是 3 段式版本，而且必須符合現有的 PowerShell 版本設定。</span><span class="sxs-lookup"><span data-stu-id="8924a-120">The ModuleVersion included in the module manifest must be a 3-part version if a prerelease version is used, and must comply with existing PowerShell versioning.</span></span> <span data-ttu-id="8924a-121">版本格式為 A.B.C，其中 A、B 和 C 皆為整數。</span><span class="sxs-lookup"><span data-stu-id="8924a-121">The version format would be A.B.C, where A, B, and C are all integers.</span></span> 
* <span data-ttu-id="8924a-122">發行前版本字串指定於模組資訊清單中 PrivateData 的 PSData 區段。</span><span class="sxs-lookup"><span data-stu-id="8924a-122">The Prerelease string is specified in the module manifest, in the PSData section of PrivateData.</span></span> <span data-ttu-id="8924a-123">發行前版本字串的詳細需求如下。</span><span class="sxs-lookup"><span data-stu-id="8924a-123">Detailed requirements on the Prerelease string are below.</span></span> 

<span data-ttu-id="8924a-124">將模組定義為發行前版本的模組資訊清單的範例部分如下所示：</span><span class="sxs-lookup"><span data-stu-id="8924a-124">An example section of a module manifest that defines a module as a prerelease would look like the following:</span></span>
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

<span data-ttu-id="8924a-125">發行前版本字串的詳細需求如下：</span><span class="sxs-lookup"><span data-stu-id="8924a-125">The detailed requirements for Prerelease string are:</span></span> 

* <span data-ttu-id="8924a-126">只有當 Major.Minor.Build 的 ModuleVersion 為 3 個區段時，才能指定發行前版本字串。</span><span class="sxs-lookup"><span data-stu-id="8924a-126">Prerelease string may only be specified when the ModuleVersion is 3 segments for Major.Minor.Build.</span></span> <span data-ttu-id="8924a-127">這與 SemVer 1.0.0 版相符。</span><span class="sxs-lookup"><span data-stu-id="8924a-127">This aligns with SemVer v1.0.0.</span></span>
* <span data-ttu-id="8924a-128">連字號是組建編號和發行前版本字串之間的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="8924a-128">A hyphen is the delimiter between the Build number and the Prerelease string.</span></span> <span data-ttu-id="8924a-129">連字號只能作為第一個字元，包含在發行前版本字串中。</span><span class="sxs-lookup"><span data-stu-id="8924a-129">A hyphen may be included in the Prerelease string as the first character, only.</span></span>
* <span data-ttu-id="8924a-130">發行前版本字串只能包含 ASCII 英數字元 [0-9A-Za-z-]。</span><span class="sxs-lookup"><span data-stu-id="8924a-130">The Prerelease string may contain only ASCII alphanumerics [0-9A-Za-z-].</span></span> <span data-ttu-id="8924a-131">發行前版本字串最好是以英數字元開始，因為在掃描項目的清單時，可以更容易分辨這是發行前版本字串。</span><span class="sxs-lookup"><span data-stu-id="8924a-131">It is a best practice to begin the Prerelease string with an alpha character, as it will be easier to identify that this is a prerelease version when scanning a list of items.</span></span> 
* <span data-ttu-id="8924a-132">目前只支援 SemVer 1.0.0 版的發行前版本字串。</span><span class="sxs-lookup"><span data-stu-id="8924a-132">Only SemVer v1.0.0 prerelease strings are supported at this time.</span></span> <span data-ttu-id="8924a-133">發行前版本字串__不得__包含 SemVer 2.0 中允許使用的句號或 + [.+]。</span><span class="sxs-lookup"><span data-stu-id="8924a-133">Prerelease string __must not__ contain either period or + [.+], which are allowed in SemVer 2.0.</span></span> 
* <span data-ttu-id="8924a-134">支援的發行前版本字串範例包括：-alpha、-alpha1、-BETA、-update20171020</span><span class="sxs-lookup"><span data-stu-id="8924a-134">Examples of supported Prerelease string are: -alpha, -alpha1, -BETA, -update20171020</span></span>

<span data-ttu-id="8924a-135">__發行前版本設定對排序順序和安裝資料夾的影響__</span><span class="sxs-lookup"><span data-stu-id="8924a-135">__Prerelease versioning impact on sort order and installation folders__</span></span>

<span data-ttu-id="8924a-136">使用發行前版本時，排序順序會變更，這在發行至 PowerShell 資源庫以及使用 PowerShellGet 命令安裝模組時非常重要。</span><span class="sxs-lookup"><span data-stu-id="8924a-136">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing modules using PowerShellGet commands.</span></span> <span data-ttu-id="8924a-137">如果發行前版本字串是針對兩個模組指定，則排序順序是根據連字號後面的字串部分。</span><span class="sxs-lookup"><span data-stu-id="8924a-137">If the Prerelease string is specified for two modules, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="8924a-138">因此，版本 2.5.0-alpha 小於 2.5.0-beta，而 2.5.0-beta 小於 2.5.0-gamma。</span><span class="sxs-lookup"><span data-stu-id="8924a-138">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="8924a-139">如果兩個模組的 ModuleVersion 相同，而且只有一個具有發行前版本字串時，沒有發行前版本字串的模組會假設為已準備好投入生產環境的版本，並且會排序為比發行前版本 (包含發行前版本字串) 更高的版本。</span><span class="sxs-lookup"><span data-stu-id="8924a-139">If two modules have the same ModuleVersion, and only one has a Prerelease string, the module without the Prerelease string is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version (which includes the Prerelease string).</span></span> <span data-ttu-id="8924a-140">例如，比較版本 2.5.0 和 2.5.0-beta 時，2.5.0 版會視為兩個版本中的較高版本。</span><span class="sxs-lookup"><span data-stu-id="8924a-140">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span> 

<span data-ttu-id="8924a-141">發行至 PowerShell 資源庫時，根據預設，所發行的模組版本必須比 PowerShell 資源庫中任何先前已發行的版本更高。</span><span class="sxs-lookup"><span data-stu-id="8924a-141">When publishing to the PowerShell Gallery, by default the version of the module being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span> 

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a><span data-ttu-id="8924a-142">使用 PowerShellGet 命令尋找並取得發行前版本項目</span><span class="sxs-lookup"><span data-stu-id="8924a-142">Finding and acquiring prerelease items using PowerShellGet commands</span></span>

<span data-ttu-id="8924a-143">使用 PowerShellGet 的 Find-Module、Install-Module、Update-Module 和 Save-Module 命令處理發行前版本項目時，需要新增 -AllowPrerelease 旗標。</span><span class="sxs-lookup"><span data-stu-id="8924a-143">Dealing with prerelease items using PowerShellGet Find-Module, Install-Module, Update-Module, and Save-Module commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="8924a-144">如果已指定 -AllowPrerelease，則會包含現存的發行前版本項目。</span><span class="sxs-lookup"><span data-stu-id="8924a-144">If -AllowPrerelease is specified, prerelease items will be included if they are present.</span></span>
<span data-ttu-id="8924a-145">如果未指定 -AllowPrerelease 旗標，則不會顯示發行前版本項目。</span><span class="sxs-lookup"><span data-stu-id="8924a-145">If -AllowPrerelease flag is not specified, prerelease items will not be shown.</span></span> 

<span data-ttu-id="8924a-146">PowerShellGet 模組命令中此狀況的唯一例外是 Get-InstalledModule，以及在某些情況下的 Uninstall-Module。</span><span class="sxs-lookup"><span data-stu-id="8924a-146">The only exceptions to this in the PowerShellGet module commands are Get-InstalledModule, and some cases with Uninstall-Module.</span></span> 

* <span data-ttu-id="8924a-147">Get-InstalledModule 一律會自動顯示模組版本字串中的發行前版本資訊。</span><span class="sxs-lookup"><span data-stu-id="8924a-147">Get-InstalledModule always will automatically show the prerelease information in the version string for modules.</span></span> 
* <span data-ttu-id="8924a-148">Uninstall-Module 在__未指定版本__時，預設將解除安裝最新的模組版本。</span><span class="sxs-lookup"><span data-stu-id="8924a-148">Uninstall-Module will by default uninstall the most recent version of a module, if __no version__ is specified.</span></span> <span data-ttu-id="8924a-149">該行為尚未變更。</span><span class="sxs-lookup"><span data-stu-id="8924a-149">That behavior has not changed.</span></span> <span data-ttu-id="8924a-150">但是，如果已使用 -RequiredVersion　指定了發行前版本，則需要 -AllowPrerelease。</span><span class="sxs-lookup"><span data-stu-id="8924a-150">However, if a prerelease version is specified using -RequiredVersion, -AllowPrerelease will be required.</span></span> 

## <a name="examples"></a><span data-ttu-id="8924a-151">範例</span><span class="sxs-lookup"><span data-stu-id="8924a-151">Examples</span></span>
```powershell
# Assume the PowerShell Gallery has TestPackage module versions 1.8.0 and 1.9.0-alpha. If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
C:\windows\system32> find-module TestPackage 

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.8.0          TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-alpha    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

# To install a prerelease, always specify -AllowPrerelease. Specifying a prerelease version string is not sufficient. 

C:\windows\system32> Install-module TestPackage -RequiredVersion 1.9.0-alpha
PackageManagement\Find-Package : No match was found for the specified search criteria and module name 'TestPackage'.
Try Get-PSRepository to see all available registered module repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exceptio
   n
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage

# The previous command failed because -AllowPrerelease was not specified.
# Adding -AllowPrerelease will result in success.

C:\windows\system32> Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

```

<span data-ttu-id="8924a-152">如果模組的版本僅僅因為指定的發行前版本而有所不同，則不支援並行安裝模組的各版本。</span><span class="sxs-lookup"><span data-stu-id="8924a-152">Side-by-side installation of versions of a module that differ only due to the prerelease specified is not supported.</span></span> <span data-ttu-id="8924a-153">使用 PowerShellGet 安裝模組時，透過使用 ModuleVersion 建立資料夾名稱，可並行安裝相同模組的不同版本。</span><span class="sxs-lookup"><span data-stu-id="8924a-153">When installing a module using PowerShellGet, different versions of the same module are installed side-by-side by creating a folder name using the ModuleVersion.</span></span> <span data-ttu-id="8924a-154">不含發行前版本字串的 ModuleVersion 可作為資料夾名稱使用。</span><span class="sxs-lookup"><span data-stu-id="8924a-154">The ModuleVersion, without the prerelease string, is used for the folder name.</span></span> <span data-ttu-id="8924a-155">如果使用者安裝 MyModule 2.5.0-alpha 版，它將安裝至 MyModule\2.5.0 資料夾。</span><span class="sxs-lookup"><span data-stu-id="8924a-155">If a user installs MyModule version 2.5.0-alpha, it will be installed to the MyModule\2.5.0 folder.</span></span> <span data-ttu-id="8924a-156">如果使用者接著安裝 2.5.0-beta，則 2.5.0-beta 版將__覆寫__ MyModule\2.5.0 資料夾的內容。</span><span class="sxs-lookup"><span data-stu-id="8924a-156">If the user then installs 2.5.0-beta, the 2.5.0-beta version will __over-write__ the contents of the folder MyModule\2.5.0.</span></span> <span data-ttu-id="8924a-157">這種方法的其中一個優點是，安裝已準備好投入生產環境的版本之後，不需要解除安裝發行前版本。</span><span class="sxs-lookup"><span data-stu-id="8924a-157">One advantage to this approach is that there is no need to un-install the prerelease version after installing the production-ready version.</span></span> <span data-ttu-id="8924a-158">下列範例示範預期的結果：</span><span class="sxs-lookup"><span data-stu-id="8924a-158">The example below shows what to expect:</span></span>


``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-beta     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Update-Module TestPackage -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-beta      TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

```

<span data-ttu-id="8924a-159">如果未提供 -RequiredVersion，Uninstall-Module 將會移除最新的模組版本。</span><span class="sxs-lookup"><span data-stu-id="8924a-159">Uninstall-Module will remove the latest version of a module when -RequiredVersion is not supplied.</span></span> <span data-ttu-id="8924a-160">如果指定了 -RequiredVersio，而且是發行前版本，則必須將 -AllowPrerelease 新增至命令。</span><span class="sxs-lookup"><span data-stu-id="8924a-160">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span> 

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
2.0.0-alpha1    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.9.0-beta      TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta
Uninstall-Module : The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Unnstall-Module TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Module], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninnstall-Module



C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
2.0.0-alpha1    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...


```



## <a name="more-details"></a><span data-ttu-id="8924a-161">更多詳細資料</span><span class="sxs-lookup"><span data-stu-id="8924a-161">More details</span></span>
### <a name="prerelease-script-versionsscriptprereleasescriptmd"></a>[<span data-ttu-id="8924a-162">發行前指令碼版本</span><span class="sxs-lookup"><span data-stu-id="8924a-162">Prerelease Script Versions</span></span>](../script/PrereleaseScript.md)
### <a name="find-modulepsgetfind-modulemd"></a>[<span data-ttu-id="8924a-163">Find-Module</span><span class="sxs-lookup"><span data-stu-id="8924a-163">Find-Module</span></span>](./psget_find-module.md)
### <a name="install-modulepsgetinstall-modulemd"></a>[<span data-ttu-id="8924a-164">Install-Module</span><span class="sxs-lookup"><span data-stu-id="8924a-164">Install-Module</span></span>](./psget_install-module.md)
### <a name="save-modulepsgetsave-modulemd"></a>[<span data-ttu-id="8924a-165">Save-Module</span><span class="sxs-lookup"><span data-stu-id="8924a-165">Save-Module</span></span>](./psget_save-module.md)
### <a name="update-modulepsgetupdate-modulemd"></a>[<span data-ttu-id="8924a-166">Update-Module</span><span class="sxs-lookup"><span data-stu-id="8924a-166">Update-Module</span></span>](./psget_update-module.md)
### <a name="get-installedmodulepsgetget-installedmodulemd"></a>[<span data-ttu-id="8924a-167">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="8924a-167">Get-InstalledModule</span></span>](./psget_get-installedmodule.md)
### <a name="uninstall-modulepsgetuninstall-modulemd"></a>[<span data-ttu-id="8924a-168">UnInstall-Module</span><span class="sxs-lookup"><span data-stu-id="8924a-168">UnInstall-Module</span></span>](./psget_uninstall-module.md)
