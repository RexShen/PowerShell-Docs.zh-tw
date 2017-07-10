---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "資源庫,powershell,cmdlet,psget"
title: Save-Module
ms.openlocfilehash: 296c5c5ffc6f1e12da0162237e562b13b3679110
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
<a id="save-module" class="xliff"></a>
# Save-Module

在本機儲存模組，而不進行安裝。

<a id="description" class="xliff"></a>
## 描述

Save-Module Cmdlet 會在本機儲存來自所指定存放庫的模組，以進行檢查。 尚未安裝模組。

<a id="cmdlet-syntax" class="xliff"></a>
## Cmdlet 語法
```powershell
Get-Command -Name Save-Module -Module PowerShellGet -Syntax
```

<a id="cmdlet-online-help-reference" class="xliff"></a>
## Cmdlet 線上說明參考資料

[Save-Module](http://go.microsoft.com/fwlink/?LinkId=531351)

<a id="example-commands" class="xliff"></a>
## 範例命令

```powershell
Save-Module -Repository MSPSGallery -Name ModuleWithDependencies2 -Path C:\MySavedModuleLocation
dir C:\MySavedModuleLocation

Directory: C:\MySavedModuleLocation

Mode LastWriteTime Length Name
---- ------------- ------ ----
d----- 4/21/2015 5:40 PM ModuleWithDependencies2
d----- 4/21/2015 5:40 PM NestedRequiredModule1
d----- 4/21/2015 5:40 PM NestedRequiredModule2
d----- 4/21/2015 5:40 PM NestedRequiredModule3
d----- 4/21/2015 5:40 PM RequiredModule1
d----- 4/21/2015 5:40 PM RequiredModule2
d----- 4/21/2015 5:40 PM RequiredModule3


# Find a command and save its module
# This command finds the specified command, and then passes it to Save-Module to save it to the C:\temp folder.
Find-Command -Name "Get-NestedRequiredModule4" -Repository "INT" | Save-Module -Path "C:\temp\" -Verbose


# Save the role capability modules by piping the Find-RoleCapability output to Save-Module cmdlet.
Find-RoleCapability -Name Maintenance,MyJeaRole | Save-Module -Path C:\MyModulesPath

```

