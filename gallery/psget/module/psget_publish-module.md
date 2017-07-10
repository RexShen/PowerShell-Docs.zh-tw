---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "資源庫,powershell,cmdlet,psget"
title: Publish-Module
ms.openlocfilehash: 53fca3d6756ebf698023152ce5b58b45eb0ef757
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
<a id="publish-module" class="xliff"></a>
# Publish-Module

將指定的模組從本機電腦發行至線上資源庫。

<a id="description" class="xliff"></a>
## 描述

**Publish-Module** Cmdlet 會使用 API 金鑰將模組發行至線上 NuGet 型資源庫，而這個 API 金鑰儲存為資源庫中使用者設定檔的一部分)。 您可以指定依模組名稱，或依包含模組之資料夾的路徑來發行模組。

依名稱指定模組時，**Publish-Module** 會發行透過執行 `Get-Module -ListAvailable <Name>` 所找到的第一個模組。 如果您指定發行模組的最小版本，則 **Publish-Module** 發行版本大於或等於所指定最小版本的第一個模組。

發行模組時需要在模組之資源庫頁面上所顯示的中繼資料。 必要的中繼資料包含模組名稱、版本、描述和作者。 雖然大部分的中繼資料都是取自模組資訊清單，但是有些中繼資料必須指定於 **Publish-Module** 參數 (例如 *Tag、ReleaseNote、IconUri、ProjectUri* 和 *LicenseUri*)，因為這些參數符合 NuGet 型組件庫中的欄位。

RequiredVersion 參數可讓您指定要發行之模組的確切版本。
Path 參數也支援具有版本資料夾的模組基底路徑。
Publish-Module Cmdlet 上的 Force 切換參數會啟動載入 NuGet.exe，而不予提示。

<a id="cmdlet-syntax" class="xliff"></a>
## Cmdlet 語法
```powershell
Get-Command -Name Publish-Module -Module PowerShellGet -Syntax
```

<a id="cmdlet-online-help-reference" class="xliff"></a>
## Cmdlet 線上說明參考資料

[Publish-Module](http://go.microsoft.com/fwlink/?LinkID=398575)

<a id="example-commands" class="xliff"></a>
## 範例命令

```powershell
ContosoServer module with different versions to be published.
PS C:\\windows\\system32> Get-Module -Name ContosoServer -ListAvailable
Directory: C:\\Program Files\\WindowsPowerShell\\Modules
ModuleType Version Name ExportedCommands
---------- ------- ---- ----------------
Manifest 2.8 ContosoServer Get-ContosoServer
Manifest 2.0 ContosoServer Get-ContosoServer
Manifest 1.5 ContosoServer Get-ContosoServer
Manifest 1.0 ContosoServer Get-ContosoServer
PS C:\\windows\\system32> Publish-Module -Name ContosoServer -RequiredVersion 1.0 -Repository LocalRepo -NuGetApiKey Local-Repo-NuGet-ApiKey
PS C:\\windows\\system32> Find-Module -Name ContosoServer -Repository LocalRepo
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer LocalRepo ContosoServer module
PS C:\\windows\\system32> Publish-Module -Name ContosoServer -RequiredVersion 1.5 -Repository LocalRepo -NuGetApiKey Local-Repo-NuGet-ApiKey
PS C:\\windows\\system32> Find-Module -Name ContosoServer -Repository LocalRepo
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer LocalRepo ContosoServer module
1.5 ContosoServer LocalRepo ContosoServer module
PS C:\\windows\\system32> Publish-Module -Path "C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.0" -Repository LocalRepo -NuGetApiKey Local-Repo-NuGet-ApiKey
PS C:\\windows\\system32> Find-Module -Name ContosoServer -Repository LocalRepo
Version Name Repository Description
_------ ---- ---------- -----------
1.0 ContosoServer LocalRepo ContosoServer module
1.5 ContosoServer LocalRepo ContosoServer module
2.0 ContosoServer LocalRepo ContosoServer module
```

<a id="publishing-a-module-with-dependencies" class="xliff"></a>
## 發行具有相依性的模組

<a id="create-a-module-with-dependencies-and-version-range-specified-in-requiredmodules-property-of-its-module-manifest" class="xliff"></a>
### 建立具有相依性和版本範圍的模組，這些相依性和版本範圍是在其模組資訊清單的 RequiredModules 屬性中所指定。

**注意：**
  - \*只在 MaximumVersion 中予以支援，同時應該位於版本字串尾端。 
  - \* 取代為版本物件中的 999999999。

```powershell
PS C:\windows\system32> $requiredModules = @( @{ModuleName = 'RequiredModule1'; ModuleVersion = '0.1'; MaximumVersion = '1.9'; }, @{ModuleName = 'RequiredModule2'; MaximumVersion = '1.*'; })

PS C:\windows\system32> cd C:\MyModules\ModuleWithDependencies

PS C:\MyModules\ModuleWithDependencies> New-ModuleManifest -Path .\ModuleWithDependencies.psd1 -ModuleVersion 1.0 -RequiredModules $requiredModules -Description 'ModuleWithDependencies demo module'
```

<a id="publish-modulewithdependencies-module-with-dependencies-to-the-repository" class="xliff"></a>
### 將具有相依性的 ModuleWithDependencies 模組發行至存放庫。

```powershell
PS C:\MyModules\ModuleWithDependencies> Publish-Module -Path C:\MyModules\ModuleWithDependencies -Repository LocalRepo
```

<a id="find-modulewithdependencies-module-with-its-dependencies-by-specifying--includedependencies" class="xliff"></a>
### 指定 -IncludeDependencies 來尋找具有其相依性的 ModuleWithDependencies 模組

```powershell
PS C:\MyModules\ModuleWithDependencies> Find-Module -Name ModuleWithDependencies -Repository LocalRepo -IncludeDependencies

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        ModuleWithDependencies              Module     localrepo            ModuleWithDependencies demo module
1.5        RequiredModule1                     Module     localrepo            RequiredModule1 module
1.5        RequiredModule2                     Module     localrepo            RequiredModule2 module
```

<a id="install-the-modulewithdependencies-module-with-dependencies" class="xliff"></a>
### 安裝具有相依性的 ModuleWithDependencies 模組。
請注意，在相依性安裝期間會使用版本範圍。

```powershell
PS C:\windows\system32> Get-InstalledModule
PS C:\windows\system32>
PS C:\windows\system32> Install-Module -Name ModuleWithDependencies -Repository LocalRepo
PS C:\windows\system32>
PS C:\windows\system32> Get-InstalledModule

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        ModuleWithDependencies              Module     localrepo            ModuleWithDependencies demo module
1.5        RequiredModule1                     Module     localrepo            RequiredModule1 module
1.5        RequiredModule2                     Module     localrepo            RequiredModule2 module
```

<a id="contents-of-modulewithdependencies2-module-manifest-file" class="xliff"></a>
### ModuleWithDependencies2 模組資訊清單檔案的內容

```powershell
@{
# Version number of this module.
ModuleVersion = '2.0'
# ID used to uniquely identify this module
GUID = '0eae34da-99dd-4608-8d28-c614fe7b0841'
# Author of this module
Author = 'manikb'
# Company or vendor of this module
CompanyName = 'Unknown'
# Copyright statement for this module
Copyright = '(c) 2015 manikb. All rights reserved.'
# Description of the functionality provided by this module
Description = 'ModuleWithDependencies2 module'
# Modules that must be imported into the global environment prior to importing this module
RequiredModules = @('RequiredModule1',
@{ModuleName = 'RequiredModule2'; ModuleVersion = '2.0'; },
@{ModuleName = 'RequiredModule3'; RequiredVersion = '2.5'; },
@{ModuleName = 'RequiredModule4'; ModuleVersion = '1.1'; MaximumVersion = '2.0'; },
@{ModuleName = 'RequiredModule5'; MaximumVersion = '1.5'; })
# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = @('NestedRequiredModule1',
@{ModuleName = 'NestedRequiredModule2'; ModuleVersion = '2.0'; },
@{ModuleName = 'NestedRequiredModule3'; RequiredVersion = '2.5'; },
@{ModuleName = 'NestedRequiredModule4'; ModuleVersion = '0.7'; MaximumVersion = '2.4'; },
@{ModuleName = 'NestedRequiredModule5'; MaximumVersion = '1.6'; },'ModuleWithDependencies2.psm1')
# Functions to export from this module
FunctionsToExport = '\*'
# Cmdlets to export from this module
CmdletsToExport = '\*'
# Variables to export from this module
VariablesToExport = '\*'
# Aliases to export from this module
AliasesToExport = '\*'
# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{
    PSData = @{
      # Tags applied to this module. These help with module discovery in online galleries.
      Tags = 'Tag1', 'Tag2', 'Tag-ModuleWithDependencies2-2.0'
      # A URL to the license for this module.
      LicenseUri = 'http://modulewithdependencies2.com/license'
      # A URL to the main website for this project.
      ProjectUri = 'http://modulewithdependencies2.com/'
      # A URL to an icon representing this module.
      IconUri = 'http://modulewithdependencies2.com/icon'
      # ReleaseNotes of this module
      ReleaseNotes = 'ModuleWithDependencies2 release notes'
    } # End of PSData hashtable
} # End of PrivateData hashtable
}
```


<a id="external-dependencies" class="xliff"></a>
### 外部相依性
有些模組相依性可以在外部進行管理，在該情況下，應該將它們新增至模組資訊清單的 PSData 區段中的 ExternalModuleDependencies 項目。

如果存放庫上沒有 'SnippetPx'，則會擲回下列錯誤。
```powershell
Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
```

