---
ms.date: 10/17/2017
contributor: keithb
keywords: 資源庫,powershell,cmdlet,psget
title: 指令碼的發行前版本
ms.openlocfilehash: 5b93da418b836d537491d3f1e4e29fa2e61f2f77
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188559"
---
# <a name="prerelease-versions-of-scripts"></a><span data-ttu-id="2d946-103">指令碼的發行前版本</span><span class="sxs-lookup"><span data-stu-id="2d946-103">Prerelease versions of scripts</span></span>

<span data-ttu-id="2d946-104">從 1.6.0 版開始，PowerShellGet 和 PowerShell 資源庫支援將大於 1.0.0 的版本標記為發行前版本。</span><span class="sxs-lookup"><span data-stu-id="2d946-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="2d946-105">在此功能之前，發行前版本項目僅限於以 0 開始的版本。</span><span class="sxs-lookup"><span data-stu-id="2d946-105">Prior to this feature, prerelease items were limited to having a version beginning with 0.</span></span> <span data-ttu-id="2d946-106">這些功能的目標是為 [SemVer 1.0.0 版](http://semver.org/spec/v1.0.0.html)版本設定慣例提供更好的支援，而不會中斷與 PowerShell 第 3 版及更新版本或 PowerShellGet 現有版本的回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="2d946-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="2d946-107">本主題著重在指令碼特有的功能。</span><span class="sxs-lookup"><span data-stu-id="2d946-107">This topic focuses on the script-specific features.</span></span> <span data-ttu-id="2d946-108">模組的對應功能位於[發行前模組版本](module-prerelease-support.md)主題中。</span><span class="sxs-lookup"><span data-stu-id="2d946-108">The equivalent features for modules are in the [Prerelease Module Versions](module-prerelease-support.md) topic.</span></span> <span data-ttu-id="2d946-109">使用這些功能，發行者可以將指令碼識別為 2.5.0-alpha 版，並於稍後發行已準備好投入生產環境的 2.5.0 版以取代發行前版本。</span><span class="sxs-lookup"><span data-stu-id="2d946-109">Using these features, publishers can identify a script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="2d946-110">概括而言，發行前版本的指令碼功能包括：</span><span class="sxs-lookup"><span data-stu-id="2d946-110">At a high level, the prerelease script features include:</span></span>

- <span data-ttu-id="2d946-111">將 PrereleaseString 尾碼新增至指令碼資訊清單中的版本字串。</span><span class="sxs-lookup"><span data-stu-id="2d946-111">Adding a PrereleaseString suffix to the version string in the script manifest.</span></span> <span data-ttu-id="2d946-112">當指令碼發行至 PowerShell 資源庫時，即會從資訊清單中擷取這項資料，並將其用來識別發行前版本項目。</span><span class="sxs-lookup"><span data-stu-id="2d946-112">When the scripts is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease items.</span></span>
- <span data-ttu-id="2d946-113">取得發行前版本項目需要將 -AllowPrerelease 旗標新增至 Find-Script、Install-Script、Update-Script 和 Save-Script 等 PowerShellGet 命令。</span><span class="sxs-lookup"><span data-stu-id="2d946-113">Acquiring prerelease items requires adding -AllowPrerelease flag to the PowerShellGet commands Find-Script, Install-Script, Update-Script, and Save-Script.</span></span> <span data-ttu-id="2d946-114">如果未指定此旗標，則不會顯示發行前版本項目。</span><span class="sxs-lookup"><span data-stu-id="2d946-114">If the flag is not specified, prerelease items will not be shown.</span></span>
- <span data-ttu-id="2d946-115">Find-Script、Get-InstalledScript 所顯示的指令碼以及在 PowerShell 資源庫中顯示的指令碼都將使用 PrereleaseString 顯示，如同 2.5.0-alpha。</span><span class="sxs-lookup"><span data-stu-id="2d946-115">Script versions displayed by Find-Script, Get-InstalledScript, and in the PowerShell Gallery will be displayed with the PrereleaseString, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="2d946-116">以下包含這些功能的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="2d946-116">Details for the features are included below.</span></span>

## <a name="identifying-a-script-version-as-a-prerelease"></a><span data-ttu-id="2d946-117">將指令碼版本識別為發行前版本</span><span class="sxs-lookup"><span data-stu-id="2d946-117">Identifying a script version as a prerelease</span></span>

<span data-ttu-id="2d946-118">相較於模組，PowerShellGet 對指令碼的發行前版本支援更加簡單。</span><span class="sxs-lookup"><span data-stu-id="2d946-118">PowerShellGet support for prerelease versions is easier for scripts than modules.</span></span> <span data-ttu-id="2d946-119">因為只有 PowerShellGet 支援指令碼版本設定，所以沒有新增發行前版本字串所造成的相容性問題。</span><span class="sxs-lookup"><span data-stu-id="2d946-119">Script versioning is only supported by PowerShellGet, so there are no compatibility issues caused by adding the prerelease string.</span></span> <span data-ttu-id="2d946-120">若要將 PowerShell 資源庫中的指令碼識別為發行前版本，請將發行前版本的尾碼新增至指令碼中繼資料的正確格式版本字串中。</span><span class="sxs-lookup"><span data-stu-id="2d946-120">To identify a script in the PowerShell Gallery as a prerelease, add a prerelease suffix to a properly-formatted version string in the script metadata.</span></span>

<span data-ttu-id="2d946-121">含有發行前版本的指令碼資訊清單的範例部分如下所示：</span><span class="sxs-lookup"><span data-stu-id="2d946-121">An example section of a script manifest with a prerelease version would look like the following:</span></span>

```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>

```

<span data-ttu-id="2d946-122">若要使用發行前版本的尾碼，版本字串必須符合下列需求：</span><span class="sxs-lookup"><span data-stu-id="2d946-122">To use a prerelease suffix, the version string must meet the following requirements:</span></span>

- <span data-ttu-id="2d946-123">只有當 Major.Minor.Build 的 Version 為 3 個區段時，才能指定發行前版本的尾碼。</span><span class="sxs-lookup"><span data-stu-id="2d946-123">A prerelease suffix may only be specified when the Version is 3 segments for Major.Minor.Build.</span></span>
  <span data-ttu-id="2d946-124">這與 SemVer 1.0.0 版相符</span><span class="sxs-lookup"><span data-stu-id="2d946-124">This aligns with SemVer v1.0.0</span></span>
- <span data-ttu-id="2d946-125">發行前版本的尾碼是以連字號開頭的字串，而且可能包含 ASCII 英數字元 [0-9A-Za-z-]</span><span class="sxs-lookup"><span data-stu-id="2d946-125">The prerelease suffix is a string which begins with a hyphen, and may contain ASCII alphanumerics [0-9A-Za-z-]</span></span>
- <span data-ttu-id="2d946-126">目前只支援 SemVer 1.0.0 版的發行前版本字串，因此發行前版本的尾碼__不得__包含 SemVer 2.0 中允許使用的句號或 + [.+]</span><span class="sxs-lookup"><span data-stu-id="2d946-126">Only SemVer v1.0.0 prerelease strings are supported at this time, so the prerelease suffix __must not__ contain either period or + [.+], which are allowed in SemVer 2.0</span></span>
- <span data-ttu-id="2d946-127">支援的 PrereleaseString 字串範例包括：-alpha、-alpha1、-BETA、-update20171020</span><span class="sxs-lookup"><span data-stu-id="2d946-127">Examples of supported PrereleaseString strings are: -alpha, -alpha1, -BETA, -update20171020</span></span>

<span data-ttu-id="2d946-128">__發行前版本設定對排序順序和安裝資料夾的影響__</span><span class="sxs-lookup"><span data-stu-id="2d946-128">__Prerelease versioning impact on sort order and installation folders__</span></span>

<span data-ttu-id="2d946-129">使用發行前版本時，排序順序會變更，這在發行至 PowerShell 資源庫以及使用 PowerShellGet 命令安裝指令碼時非常重要。</span><span class="sxs-lookup"><span data-stu-id="2d946-129">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing scripts using PowerShellGet commands.</span></span> <span data-ttu-id="2d946-130">如果兩個指令碼版本有該版本號碼，則排序順序是根據連字號後面的字串部分。</span><span class="sxs-lookup"><span data-stu-id="2d946-130">If two scripts versions with the version number exist, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="2d946-131">因此，版本 2.5.0-alpha 小於 2.5.0-beta，而 2.5.0-beta 小於 2.5.0-gamma。</span><span class="sxs-lookup"><span data-stu-id="2d946-131">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="2d946-132">如果兩個指令碼的版本號碼相同，而且只有一個具有 PrereleaseString 時，__沒有__發行前版本尾碼的指令碼會假設為已準備好投入生產環境的版本，並且會排序為比發行前版本更高的版本。</span><span class="sxs-lookup"><span data-stu-id="2d946-132">If two scripts have the same version number, and only one has a PrereleaseString, the script __without__ the prerelease suffix is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version.</span></span> <span data-ttu-id="2d946-133">例如，比較版本 2.5.0 和 2.5.0-beta 時，2.5.0 版會視為兩個版本中的較高版本。</span><span class="sxs-lookup"><span data-stu-id="2d946-133">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="2d946-134">發行至 PowerShell 資源庫時，根據預設，所發行的指令碼版本必須比 PowerShell 資源庫中任何先前已發行的版本更高。</span><span class="sxs-lookup"><span data-stu-id="2d946-134">When publishing to the PowerShell Gallery, by default the version of the script being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span> <span data-ttu-id="2d946-135">發行者可能會使用 2.5.0-beta 或 2.5.0 (不含發行前版本尾碼) 更新版本 2.5.0-alpha。</span><span class="sxs-lookup"><span data-stu-id="2d946-135">A publisher may update version 2.5.0-alpha with 2.5.0-beta, or with 2.5.0 (with no prerelease suffix).</span></span>

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a><span data-ttu-id="2d946-136">使用 PowerShellGet 命令尋找並取得發行前版本項目</span><span class="sxs-lookup"><span data-stu-id="2d946-136">Finding and acquiring prerelease items using PowerShellGet commands</span></span>

<span data-ttu-id="2d946-137">使用 PowerShellGet 的 Find-Script、Install-Script、Update-Script 和 Save-Script 命令處理發行前版本項目時，需要新增 -AllowPrerelease 旗標。</span><span class="sxs-lookup"><span data-stu-id="2d946-137">Dealing with prerelease items using PowerShellGet Find-Script, Install-Script, Update-Script, and Save-Script commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="2d946-138">如果已指定 -AllowPrerelease，則會包含現存的發行前版本項目。</span><span class="sxs-lookup"><span data-stu-id="2d946-138">If -AllowPrerelease is specified, prerelease items will be included if they are present.</span></span> <span data-ttu-id="2d946-139">如果未指定 -AllowPrerelease 旗標，則不會顯示發行前版本項目。</span><span class="sxs-lookup"><span data-stu-id="2d946-139">If -AllowPrerelease flag is not specified, prerelease items will not be shown.</span></span>

<span data-ttu-id="2d946-140">PowerShellGet 指令碼命令中此狀況的唯一例外是 Get-InstalledScript，以及在某些情況下的 Uninstall-Scrip。</span><span class="sxs-lookup"><span data-stu-id="2d946-140">The only exceptions to this in the PowerShellGet script commands are Get-InstalledScript, and some cases with Uninstall-Script.</span></span>

- <span data-ttu-id="2d946-141">Get-InstalledScript 一律會自動顯示版本字串中現存的發行前版本資訊。</span><span class="sxs-lookup"><span data-stu-id="2d946-141">Get-InstalledScript always will automatically show the prerelease information in the version string if it is present.</span></span>
- <span data-ttu-id="2d946-142">Uninstall-Script 在__未指定版本__時，預設將解除安裝最新的指令碼版本。</span><span class="sxs-lookup"><span data-stu-id="2d946-142">Uninstall-Script will by default uninstall the most recent version of a script, if __no version__ is specified.</span></span> <span data-ttu-id="2d946-143">該行為尚未變更。</span><span class="sxs-lookup"><span data-stu-id="2d946-143">That behavior has not changed.</span></span> <span data-ttu-id="2d946-144">但是，如果已使用 -RequiredVersion　指定了發行前版本，則需要 -AllowPrerelease。</span><span class="sxs-lookup"><span data-stu-id="2d946-144">However, if a prerelease version is specified using -RequiredVersion, -AllowPrerelease will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="2d946-145">範例</span><span class="sxs-lookup"><span data-stu-id="2d946-145">Examples</span></span>

```powershell
# Assume the PowerShell Gallery has TestPackage versions 1.8.0 and 1.9.0-alpha.
# If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
C:\windows\system32> Find-Script TestPackage

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.8.0          TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Find-Script TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-alpha    TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# To install a prerelease, you must specify -AllowPrerelease. Specifying a prerelease version string is not sufficient.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha
PackageManagement\Find-Package : No match was found for the specified search criteria and script name 'TestPackage'.
Try Get-PSRepository to see all available registered script repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exceptio
   n
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage

# The previous command failed because -AllowPrerelease was not specified.
# Adding -AllowPrerelease will result in success.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# Note that Get-InstalledScript shows the prerelease version.
# If -RequiredVersion is not specified, all installed scripts will be displayed by Get-InstalledScript
```

<span data-ttu-id="2d946-146">如果未提供 -RequiredVersion，Uninstall-Script 將會移除目前的指令碼版本。</span><span class="sxs-lookup"><span data-stu-id="2d946-146">Uninstall-Script will remove the current version of a script when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="2d946-147">如果指定了 -RequiredVersio，而且是發行前版本，則必須將 -AllowPrerelease 新增至命令。</span><span class="sxs-lookup"><span data-stu-id="2d946-147">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

``` powershell
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha
Uninstall-Script: The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Unnstall-Script TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Script], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninnstall-script


C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
# Since script versions are not installed side-by-side, the above could be simply "Uninstall-Script TestPackage"

C:\windows\system32> Get-Installedscript TestPackage
PackageManagement\Get-Package : No match was found for the specified search criteria and script names 'testpackage'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.5.0.0\PSModule.psm1:4088 char:9
+         PackageManagement\Get-Package @PSBoundParameters | Microsoft. ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...lets.GetPackage:GetPackage) [Get-Package], Exception
    + FullyQualifiedErrorId : NoMatchFound,Microsoft.PowerShell.PackageManagement.Cmdlets.GetPackage
```

## <a name="more-details"></a><span data-ttu-id="2d946-148">更多詳細資料</span><span class="sxs-lookup"><span data-stu-id="2d946-148">More details</span></span>

- [<span data-ttu-id="2d946-149">發行前模組版本</span><span class="sxs-lookup"><span data-stu-id="2d946-149">Prerelease Module Versions</span></span>](module-prerelease-support.md)
- [<span data-ttu-id="2d946-150">Find-Script</span><span class="sxs-lookup"><span data-stu-id="2d946-150">Find-script</span></span>](/powershell/module/powershellget/find-script)
- [<span data-ttu-id="2d946-151">Install-Script</span><span class="sxs-lookup"><span data-stu-id="2d946-151">Install-script</span></span>](/powershell/module/powershellget/install-script)
- [<span data-ttu-id="2d946-152">Save-Script</span><span class="sxs-lookup"><span data-stu-id="2d946-152">Save-script</span></span>](/powershell/module/powershellget/save-script)
- [<span data-ttu-id="2d946-153">Update-Script</span><span class="sxs-lookup"><span data-stu-id="2d946-153">Update-script</span></span>](/powershell/module/powershellget/update-script)
- [<span data-ttu-id="2d946-154">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="2d946-154">Get-Installedscript</span></span>](/powershell/module/powershellget/get-installedscript)
- [<span data-ttu-id="2d946-155">UnInstall-Script</span><span class="sxs-lookup"><span data-stu-id="2d946-155">UnInstall-script</span></span>](/powershell/module/powershellget/uninstall-script)