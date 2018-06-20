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
# <a name="prerelease-versions-of-scripts"></a>指令碼的發行前版本

從 1.6.0 版開始，PowerShellGet 和 PowerShell 資源庫支援將大於 1.0.0 的版本標記為發行前版本。 在此功能之前，發行前版本項目僅限於以 0 開始的版本。 這些功能的目標是為 [SemVer 1.0.0 版](http://semver.org/spec/v1.0.0.html)版本設定慣例提供更好的支援，而不會中斷與 PowerShell 第 3 版及更新版本或 PowerShellGet 現有版本的回溯相容性。 本主題著重在指令碼特有的功能。 模組的對應功能位於[發行前模組版本](module-prerelease-support.md)主題中。 使用這些功能，發行者可以將指令碼識別為 2.5.0-alpha 版，並於稍後發行已準備好投入生產環境的 2.5.0 版以取代發行前版本。

概括而言，發行前版本的指令碼功能包括：

- 將 PrereleaseString 尾碼新增至指令碼資訊清單中的版本字串。 當指令碼發行至 PowerShell 資源庫時，即會從資訊清單中擷取這項資料，並將其用來識別發行前版本項目。
- 取得發行前版本項目需要將 -AllowPrerelease 旗標新增至 Find-Script、Install-Script、Update-Script 和 Save-Script 等 PowerShellGet 命令。 如果未指定此旗標，則不會顯示發行前版本項目。
- Find-Script、Get-InstalledScript 所顯示的指令碼以及在 PowerShell 資源庫中顯示的指令碼都將使用 PrereleaseString 顯示，如同 2.5.0-alpha。

以下包含這些功能的詳細資料。

## <a name="identifying-a-script-version-as-a-prerelease"></a>將指令碼版本識別為發行前版本

相較於模組，PowerShellGet 對指令碼的發行前版本支援更加簡單。 因為只有 PowerShellGet 支援指令碼版本設定，所以沒有新增發行前版本字串所造成的相容性問題。 若要將 PowerShell 資源庫中的指令碼識別為發行前版本，請將發行前版本的尾碼新增至指令碼中繼資料的正確格式版本字串中。

含有發行前版本的指令碼資訊清單的範例部分如下所示：

```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>

```

若要使用發行前版本的尾碼，版本字串必須符合下列需求：

- 只有當 Major.Minor.Build 的 Version 為 3 個區段時，才能指定發行前版本的尾碼。
  這與 SemVer 1.0.0 版相符
- 發行前版本的尾碼是以連字號開頭的字串，而且可能包含 ASCII 英數字元 [0-9A-Za-z-]
- 目前只支援 SemVer 1.0.0 版的發行前版本字串，因此發行前版本的尾碼__不得__包含 SemVer 2.0 中允許使用的句號或 + [.+]
- 支援的 PrereleaseString 字串範例包括：-alpha、-alpha1、-BETA、-update20171020

__發行前版本設定對排序順序和安裝資料夾的影響__

使用發行前版本時，排序順序會變更，這在發行至 PowerShell 資源庫以及使用 PowerShellGet 命令安裝指令碼時非常重要。 如果兩個指令碼版本有該版本號碼，則排序順序是根據連字號後面的字串部分。 因此，版本 2.5.0-alpha 小於 2.5.0-beta，而 2.5.0-beta 小於 2.5.0-gamma。 如果兩個指令碼的版本號碼相同，而且只有一個具有 PrereleaseString 時，__沒有__發行前版本尾碼的指令碼會假設為已準備好投入生產環境的版本，並且會排序為比發行前版本更高的版本。 例如，比較版本 2.5.0 和 2.5.0-beta 時，2.5.0 版會視為兩個版本中的較高版本。

發行至 PowerShell 資源庫時，根據預設，所發行的指令碼版本必須比 PowerShell 資源庫中任何先前已發行的版本更高。 發行者可能會使用 2.5.0-beta 或 2.5.0 (不含發行前版本尾碼) 更新版本 2.5.0-alpha。

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a>使用 PowerShellGet 命令尋找並取得發行前版本項目

使用 PowerShellGet 的 Find-Script、Install-Script、Update-Script 和 Save-Script 命令處理發行前版本項目時，需要新增 -AllowPrerelease 旗標。 如果已指定 -AllowPrerelease，則會包含現存的發行前版本項目。 如果未指定 -AllowPrerelease 旗標，則不會顯示發行前版本項目。

PowerShellGet 指令碼命令中此狀況的唯一例外是 Get-InstalledScript，以及在某些情況下的 Uninstall-Scrip。

- Get-InstalledScript 一律會自動顯示版本字串中現存的發行前版本資訊。
- Uninstall-Script 在__未指定版本__時，預設將解除安裝最新的指令碼版本。 該行為尚未變更。 但是，如果已使用 -RequiredVersion　指定了發行前版本，則需要 -AllowPrerelease。

## <a name="examples"></a>範例

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

如果未提供 -RequiredVersion，Uninstall-Script 將會移除目前的指令碼版本。
如果指定了 -RequiredVersio，而且是發行前版本，則必須將 -AllowPrerelease 新增至命令。

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

## <a name="more-details"></a>更多詳細資料

- [發行前模組版本](module-prerelease-support.md)
- [Find-Script](/powershell/module/powershellget/find-script)
- [Install-Script](/powershell/module/powershellget/install-script)
- [Save-Script](/powershell/module/powershellget/save-script)
- [Update-Script](/powershell/module/powershellget/update-script)
- [Get-InstalledScript](/powershell/module/powershellget/get-installedscript)
- [UnInstall-Script](/powershell/module/powershellget/uninstall-script)