---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "資源庫,powershell,cmdlet,psget"
title: Uninstall-Module
ms.openlocfilehash: 3c4d8faa63aba6b4434d42a19a219baf84122591
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
<a id="uninstall-module" class="xliff"></a>
# Uninstall-Module

解除安裝使用 PowerShellGet Cmdlet 所安裝的模組。

<a id="description" class="xliff"></a>
## 描述

Uninstall-Module Cmdlet 會從本機電腦中解除安裝指定的模組。 如果某些其他模組具有模組的相依性，則無法解除安裝模組。
Uninstall-Module Cmdlet 也會驗證是否正在使用所解除安裝的模組。 如果模組使用中，則會擲回錯誤。

<a id="cmdlet-syntax" class="xliff"></a>
## Cmdlet 語法
```powershell
Get-Command -Name Uninstall-Module -Module PowerShellGet -Syntax
```

<a id="cmdlet-online-help-reference" class="xliff"></a>
## Cmdlet 線上說明參考資料

[Uninstall-Module](http://go.microsoft.com/fwlink/?LinkId=526864)


<a id="example-commands" class="xliff"></a>
## 範例命令

<a id="run-the-uninstall-module-cmdlet-to-uninstall-a-module-that-you-installed-by-using-powershellget" class="xliff"></a>
###  執行 Uninstall-Module Cmdlet 來解除安裝您使用 PowerShellGet 安裝的模組。
如想刪除相依於此模組的任何其他模組，PowerShellGet 會擲回錯誤。
```powershell
Get-InstalledModule -Name RequiredModule1 | Uninstall-Module

PackageManagement\Uninstall-Package : The module 'RequiredModule1' of version '2.5' in module base folder 'C:\Program Files\WindowsPowerShell\Modules\RequiredModule1\2.5' cannot be uninstalled, because one or more other modules 'ModuleWithDependencies2' are dependent on this module. Uninstall the modules that depend on this module before uninstalling module 'RequiredModule1'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\PSGet.psm1:1303 char:25
+ ... $null = PackageManagement\\Uninstall-Package @PSBoundParameters
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo : InvalidOperation: (Microsoft.Power...ninstallPackage:UninstallPackage) [Uninstall-Package], Exception
+ FullyQualifiedErrorId : UnableToUninstallAsOtherModulesNeedThisModule,Uninstall-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.UninstallPackage
```

<a id="uninstalling-a-module-when-some-other-modules-have-a-dependency-on-it" class="xliff"></a>
### 在某些其他模組具有模組的相依性時解除安裝模組。

```powershell
Uninstall-Module SnippetPx

PackageManagement\Uninstall-Package : The module 'SnippetPx' of version '1.0.5.18' in module base folder 'C:\ProgramFiles\WindowsPowerShell\Modules\SnippetPx\1.0.5.18' cannot be uninstalled, because one or more other modules 'TypePx' are dependent on this module. Uninstall the modules that depend on this module before uninstalling module 'SnippetPx'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.3\PSModule.psm1:1803 char:21
+ ...        $null = PackageManagement\Uninstall-Package @PSBoundParameters
+                    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (Microsoft.Power...ninstallPackage:UninstallPackage) [Uninstall-Packag
   e], Exception
    + FullyQualifiedErrorId : UnableToUninstallAsOtherModulesNeedThisModule,Uninstall-Package,Microsoft.PowerShell.Pac
   kageManagement.Cmdlets.UninstallPackage
```

<a id="you-can-override-this-by-specify--force-option-on-uninstall-module-cmdlet" class="xliff"></a>
### 覆寫方式是在 Uninstall-Module Cmdlet 上指定 -Force 選項
**注意：**這不是建議的做法。 其他模組會因這個動作而中斷。

```powershell
Uninstall-Module SnippetPx -Force
```

<a id="uninstall-a-module-which-is-already-in-use" class="xliff"></a>
### 解除安裝已在使用中的模組

```powershell
Get-InstalledModule TypePx,SnippetPx

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to...
1.0.5.18   SnippetPx                           PSGallery            The SnippetPx module enhances the snippet experi...
```

<a id="uninstall-snippetpx-fails-due-to-the-dependent-module" class="xliff"></a>
### 因為模組相依，所以解除安裝 SnippetPx 失敗

```powershell
Uninstall-Module SnippetPx

PackageManagement\Uninstall-Package : The module 'SnippetPx' of version '1.0.5.18' in module base folder 'C:\Program
Files\WindowsPowerShell\Modules\SnippetPx\1.0.5.18' cannot be uninstalled, because one or more other modules 'TypePx'
are dependent on this module. Uninstall the modules that depend on this module before uninstalling module 'SnippetPx'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1914 char:21
+ ...        $null = PackageManagement\Uninstall-Package @PSBoundParameters
+                    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (Microsoft.Power...ninstallPackage:UninstallPackage) [Uninstall-Packag
   e], Exception
    + FullyQualifiedErrorId : UnableToUninstallAsOtherModulesNeedThisModule,Uninstall-Package,Microsoft.PowerShell.Pac
   kageManagement.Cmdlets.UninstallPackage
```

<a id="uninstall-typepx-then-uninstall-the-snippetpx" class="xliff"></a>
### 解除安裝 TypePx，然後解除安裝 SnippetPx

```powershell
Uninstall-Module TypePx
Uninstall-Module SnippetPx

WARNING: The version '1.0.5.18' of module 'SnippetPx' is currently in use. Retry the operation after closing the
applications.
PackageManagement\Uninstall-Package : Module 'SnippetPx' is in currently in use.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1914 char:21
+ ...        $null = PackageManagement\Uninstall-Package @PSBoundParameters
+                    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (Microsoft.Power...ninstallPackage:UninstallPackage) [Uninstall-Packag
   e], Exception
    + FullyQualifiedErrorId : ModuleIsInUse,Uninstall-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.Uninstall
   Package
```


<a id="for-a-module-name-which-is-not-installed-using-powershellget-cmdlets" class="xliff"></a>
### 針對不是使用 PowerShellGet Cmdlet 所安裝的模組名稱

```powershell
Uninstall-Module SnipptPx

PackageManagement\Uninstall-Package : No match was found for the specified search criteria and module names 'SnipptPx'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1914 char:21
+ ...        $null = PackageManagement\Uninstall-Package @PSBoundParameters
+                    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ninstallPackage:UninstallPackage) [Uninstall-Package]
   , Exception
    + FullyQualifiedErrorId : NoMatchFound,Microsoft.PowerShell.PackageManagement.Cmdlets.UninstallPackage
```

