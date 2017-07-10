---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "資源庫,powershell,cmdlet,psget"
title: Find-Module
ms.openlocfilehash: 5c878a04d186f7f5970fba9e7f3cdb480cef21f6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
<a id="find-module" class="xliff"></a>
# Find-Module
尋找來自線上組件庫且符合所指定準則的模組。

<a id="description" class="xliff"></a>
## 描述
Find-Module 會探索已註冊存放庫中符合所指定準則的模組。
針對每個找到的模組，Find-Module 會傳回可選擇性地傳送至 Install-Module 以安裝模組的 PSRepositoryItemInfo 物件。

- Find-Module 可以使用 -Command、-DscResource、-RoleCapability 和 -Includes 參數根據模組內容進行篩選。
- Find-Module 可以使用版本參數 MinimumVersion、MaximumVersion、RequiredVersion、AllVersions 進行篩選。
  - 這些參數互斥 (MinmimumVersion 和 MaximumVersion 除外)。
  - 只有不含任何萬用字元的單一模組名稱才允許使用這些版本參數。
  - 如果未指定 RequiredVersion 參數，Find-Module 會傳回等於或大於所指定最小版本之模組的最新版本，或未指定最小版本之模組的最新版本。 
  - 如果指定 RequiredVersion 參數，Find-Module 只會傳回完全符合所指定版本之模組的版本。
- Find-Module 可以使用 -Tag 參數篩選模組中繼資料
- Find-Module 可以使用 -Filter 參數篩選存放庫特定的搜尋語言。
- Find-Module 可以篩選所有或部分已註冊存放庫中的模組。

<a id="cmdlet-syntax" class="xliff"></a>
## Cmdlet 語法
```powershell
Get-Command -Name Find-Module -Module PowerShellGet -Syntax
```

<a id="cmdlet-online-help-reference" class="xliff"></a>
## Cmdlet 線上說明參考資料

[Find-Module](http://go.microsoft.com/fwlink/?LinkID=398574)

<a id="example-commands" class="xliff"></a>
## 範例命令
```powershell
# Find a specific module
Find-Module Azure

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.3.2      Azure                               PSGallery            Microsoft Azure PowerShell - Service Management

# Find multiple modules
Find-Module Azure,AzureRM

# Find modules with wildcards in -Name
Find-Module -Name AzureRM*

# Find all versions of a module
Find-Module -Name PSReadline -AllVersions

# Find a module with -MinimumVersion. 
# With MinimumVersion we can find a module whose version is greate than or equal to the specified MinimumVersion value.
Find-Module -Name PSReadline -MinimumVersion 1.0.0.12

# Find a module with MaximumVersion
Find-Module -Name PSReadline -MaximumVersion 1.0.0.13

# Find a module with both MinimumVersion and MaximumVersion range.
Find-Module -Name PSReadline -MinimumVersion 1.0.0.12 -MaximumVersion 1.0.0.13

# Find a module with exact version
Find-Module -Name AzureRM -RequiredVersion 1.3.2

# Find a module from the specified repository
Find-Module -Name Contoso -Repository MyLocalRepo

# Find available modules from all registered repositories
Find-Module

# Find available modules from few registered repositories
Find-Module -Repository PSGallery,PrivatePSGallery

# Find a module along with its dependencies
Find-Module -Name AzureRM -IncludeDependencies

# Find all modules with Dsc resources
Find-Module -Includes DscResource

# Find modules with a specific DscResource
Find-Module -DscResource xFirewall

# Find all modules with cmdlets
Find-Module -Includes Cmdlet

# Find all modules with functions
Find-Module -Includes Function

# Find all modules with Role Capabilities
Find-Module -Includes RoleCapability

# Find all modules with the specified Role Capability name
Find-Module -RoleCapability RoleCap1
Find-Module -RoleCapability RoleCap2 -Includes RoleCapability

# Find modules with specific commands
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer -Includes Cmdlet
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer -Includes Function

# Find modules with -Filter based search. -Filter searches in description and names
Find-Module -Filter Cookbook
Find-Module -Filter RBAC
Find-Module -Filter 'App Domain' -Includes 'DscResource'

# Find all modules with tags Azure or DSC
Find-Module -Tag Azure, DSC

# Properties of Find-Module returned object
Find-Module AzureRM.Profile | Format-List * -Force

Name                       : AzureRM.profile
Version                    : 1.0.8
Type                       : Module
Description                : Microsoft Azure PowerShell - Profile credential management cmdlets for Azure Resource
                             Manager
Author                     : Microsoft Corporation
CompanyName                : {elogeel, azure-sdk}
Copyright                  : Microsoft Corporation. All rights reserved.
PublishedDate              : 5/4/2016 9:40:33 PM
InstalledDate              :
UpdatedDate                :
LicenseUri                 : https://raw.githubusercontent.com/Azure/azure-powershell/dev/LICENSE.txt
ProjectUri                 : https://github.com/Azure/azure-powershell
IconUri                    :
Tags                       : {PSModule}
Includes                   : {Function, RoleCapability, Command, DscResource...}
PowerShellGetFormatVersion :
ReleaseNotes               : https://github.com/Azure/azure-powershell/blob/dev/ChangeLog.md
Dependencies               : {}
RepositorySourceLocation   : https://www.powershellgallery.com/api/v2/
Repository                 : PSGallery
PackageManagementProvider  : NuGet
AdditionalMetadata         : {downloadCount, description, copyright, FileList...}

```

