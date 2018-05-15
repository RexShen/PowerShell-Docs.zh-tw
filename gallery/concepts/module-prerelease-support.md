---
ms.date: 09/26/2017
contributor: keithb
ms.topic: reference
keywords: 資源庫,powershell,cmdlet,psget
title: 發行前模組版本
ms.openlocfilehash: e663a42092556ef1c43a7cf236616bf420171af6
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
---
# <a name="prerelease-module-versions"></a>發行前模組版本

從 1.6.0 版開始，PowerShellGet 和 PowerShell 資源庫支援將大於 1.0.0 的版本標記為發行前版本。 在此功能之前，發行前版本項目僅限於以 0 開始的版本。 這些功能的目標是為 [SemVer 1.0.0 版](http://semver.org/spec/v1.0.0.html)版本設定慣例提供更好的支援，而不會中斷與 PowerShell 第 3 版及更新版本或 PowerShellGet 現有版本的回溯相容性。 本主題著重在模組特有的功能。 指令碼的對應功能位於[指令碼的發行前版本](script-prerelease-support.md)主題中。 使用這些功能，發行者可以將模組或指令碼識別為 2.5.0-Alpha 版，並於稍後發行已準備好投入生產環境的 2.5.0 版以取代發行前版本。

概括而言，發行前版本的模組功能包括：

- 將發行前版本字串新增至模組資訊清單的 PSData 區段，可將模組識別為發行前版本。 當模組發行至 PowerShell 資源庫時，即會從資訊清單中擷取這項資料，並將其用來識別發行前版本項目。
- 取得發行前版本項目需要將 -AllowPrerelease 旗標新增至 Find-Module、Install-Module、Update-Module 和 Save-Module 等 PowerShellGet 命令。 如果未指定此旗標，則不會顯示發行前版本項目。
- Find-Module、Get-InstalledModule 所顯示的模組版本以及 PowerShell 資源庫中顯示的模組版本，將顯示為附加了發行前版本字串的單一字串，如同 2.5.0-alpha。

以下包含這些功能的詳細資料。

這些變更不會影響已內建至 PowerShell 的模組版本支援，並且與 PowerShell 3.0、4.0 和 5 相容。

## <a name="identifying-a-module-version-as-a-prerelease"></a>將模組版本識別為發行前版本

PowerShellGet 對發行前版本的支援需要使用模組資訊清單內的兩個欄位：

- 如果使用發行前版本，模組資訊清單中包含的 ModuleVersion 必須是 3 段式版本，而且必須符合現有的 PowerShell 版本設定。 版本格式為 A.B.C，其中 A、B 和 C 皆為整數。
- 發行前版本字串指定於模組資訊清單中 PrivateData 的 PSData 區段。

發行前版本字串的詳細需求如下。

將模組定義為發行前版本的模組資訊清單的範例部分如下所示：

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

發行前版本字串的詳細需求如下：

- 只有當 Major.Minor.Build 的 ModuleVersion 為 3 個區段時，才能指定發行前版本字串。 這與 SemVer 1.0.0 版相符。
- 連字號是組建編號和發行前版本字串之間的分隔符號。 連字號只能作為第一個字元，包含在發行前版本字串中。
- 發行前版本字串只能包含 ASCII 英數字元 [0-9A-Za-z-]。 發行前版本字串最好是以英數字元開始，因為在掃描項目的清單時，可以更容易分辨這是發行前版本字串。
- 目前只支援 SemVer 1.0.0 版的發行前版本字串。 發行前版本字串__不得__包含 SemVer 2.0 中允許使用的句號或 + [.+]。
- 支援的發行前版本字串範例包括：-alpha、-alpha1、-BETA、-update20171020

__發行前版本設定對排序順序和安裝資料夾的影響__

使用發行前版本時，排序順序會變更，這在發行至 PowerShell 資源庫以及使用 PowerShellGet 命令安裝模組時非常重要。 如果發行前版本字串是針對兩個模組指定，則排序順序是根據連字號後面的字串部分。 因此，版本 2.5.0-alpha 小於 2.5.0-beta，而 2.5.0-beta 小於 2.5.0-gamma。 如果兩個模組的 ModuleVersion 相同，而且只有一個具有發行前版本字串時，沒有發行前版本字串的模組會假設為已準備好投入生產環境的版本，並且會排序為比發行前版本 (包含發行前版本字串) 更高的版本。 例如，比較版本 2.5.0 和 2.5.0-beta 時，2.5.0 版會視為兩個版本中的較高版本。

發行至 PowerShell 資源庫時，根據預設，所發行的模組版本必須比 PowerShell 資源庫中任何先前已發行的版本更高。

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a>使用 PowerShellGet 命令尋找並取得發行前版本項目

使用 PowerShellGet 的 Find-Module、Install-Module、Update-Module 和 Save-Module 命令處理發行前版本項目時，需要新增 -AllowPrerelease 旗標。 如果已指定 -AllowPrerelease，則會包含現存的發行前版本項目。 如果未指定 -AllowPrerelease 旗標，則不會顯示發行前版本項目。

PowerShellGet 模組命令中此狀況的唯一例外是 Get-InstalledModule，以及在某些情況下的 Uninstall-Module。

- Get-InstalledModule 一律會自動顯示模組版本字串中的發行前版本資訊。
- Uninstall-Module 在__未指定版本__時，預設將解除安裝最新的模組版本。 該行為尚未變更。 但是，如果已使用 -RequiredVersion　指定了發行前版本，則需要 -AllowPrerelease。

## <a name="examples"></a>範例

```powershell
# Assume the PowerShell Gallery has TestPackage module versions 1.8.0 and 1.9.0-alpha.
# If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
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

如果模組的版本僅僅因為指定的發行前版本而有所不同，則不支援並行安裝模組的各版本。 使用 PowerShellGet 安裝模組時，透過使用 ModuleVersion 建立資料夾名稱，可並行安裝相同模組的不同版本。 不含發行前版本字串的 ModuleVersion 可作為資料夾名稱使用。 如果使用者安裝 MyModule 2.5.0-alpha 版，它將安裝至 MyModule\2.5.0 資料夾。 如果使用者接著安裝 2.5.0-beta，則 2.5.0-beta 版將__覆寫__ MyModule\2.5.0 資料夾的內容。 這種方法的其中一個優點是，安裝已準備好投入生產環境的版本之後，不需要解除安裝發行前版本。 下列範例示範預期的結果：

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

如果未提供 -RequiredVersion，Uninstall-Module 將會移除最新的模組版本。
如果指定了 -RequiredVersio，而且是發行前版本，則必須將 -AllowPrerelease 新增至命令。

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

## <a name="more-details"></a>更多詳細資料

- [發行前指令碼版本](script-prerelease-support.md)
- [Find-Module](/powershell/module/powershellget/find-module)
- [Install-Module](/powershell/module/powershellget/install-module)
- [Save-Module](/powershell/module/powershellget/save-module)
- [Update-Module](/powershell/module/powershellget/Update-Module)
- [Get-InstalledModule](/powershell/module/powershellget/get-installedmodule)
- [UnInstall-Module](/powershell/gallery/psget/module/psget_uninstall-module)