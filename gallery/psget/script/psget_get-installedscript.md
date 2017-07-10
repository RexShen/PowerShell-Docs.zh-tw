---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "資源庫,powershell,cmdlet,psget"
title: Get-InstalledScript
ms.openlocfilehash: f35e57cdadd1448bd9032ab007d692003c4cf4a2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
<a id="get-installedscript" class="xliff"></a>
# Get-InstalledScript

取得電腦上的已安裝指令碼。

<a id="description" class="xliff"></a>
## 描述

Get-InstalledScript Cmdlet 會取得電腦上的已安裝 PowerShell 指令碼。

針對每個已安裝的指令碼，Get-InstalledScript 會傳回可選擇性地傳送至 Uninstall-Script 的 PSRepositoryItemInfo 物件，以解除安裝已安裝的指令碼。

- Get-InstalledScript 可以根據名稱和版本參數來篩選已安裝的指令碼。
- Get-InstalledScript 可以使用版本參數 MinimumVersion、MaximumVersion、RequiredVersion、AllVersions 進行篩選。
  - 這些參數互斥 (MinmimumVersion 和 MaximumVersion 除外)。
  - 只有不含任何萬用字元的單一指令碼名稱才允許使用這些版本參數。
  - 如果未指定 RequiredVersion 參數，Get-InstalledScript 會傳回等於或大於所指定最小版本之已安裝指令碼的最新版本，或未指定最小版本之指令碼的最新版本。 
  - 如果指定 RequiredVersion 參數，Get-InstalledScript 只會傳回完全符合所指定版本之已安裝指令碼的版本。

<a id="cmdlet-syntax" class="xliff"></a>
## Cmdlet 語法

```powershell
Get-Command -Name Get-InstalledScript -Module PowerShellGet -Syntax
```

<a id="cmdlet-online-help-reference" class="xliff"></a>
## Cmdlet 線上說明參考資料

[Get-InstalledScript](http://go.microsoft.com/fwlink/?LinkId=619790)

<a id="example-commands" class="xliff"></a>
## 範例命令

```powershell

# Get all scripts installed using PowerShellGet cmdlets
Get-InstalledScript

# Get a specific installed script
Get-InstalledScript Show-Tree

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0.0      Show-Tree                           PSGallery            Script to show the layout of PowerShell namespaces (Tr...

# Get installed script with wildcards
Get-InstalledScript -Name *Azure*

# Get all versions of an installed script
Get-InstalledScript -Name Connect-O365 -AllVersions

# Get installed script with MinimumVersion
Get-InstalledScript -Name Connect-O365 -MinimumVersion 1.1

# Get installed script with MaximumVersion
Get-InstalledScript -Name Connect-O365 -MaximumVersion 1.6.3

# Get installed script with version range
Get-InstalledScript -Name Connect-O365 -MinimumVersion 1.1 -MaximumVersion 1.6.3

# Get installed script with RequiredVersion
Get-InstalledScript -Name Connect-O365 -RequiredVersion 1.4

# Properties of Get-InstalledScript returned object
Get-InstalledScript Show-Tree | Format-List * -Force

Name                       : Show-Tree
Version                    : 1.0.0
Type                       : Script
Description                : Script to show the layout of PowerShell namespaces (Trees) using ASCII
Author                     : Jeffrey Snover
CompanyName                : jsnover
Copyright                  : (C) Microsoft Corporation. All rights reserved.
PublishedDate              : 2/15/2016 10:15:35 PM
InstalledDate              : 5/4/2016 11:44:13 PM
UpdatedDate                :
LicenseUri                 :
ProjectUri                 :
IconUri                    :
Tags                       : {Nano, PSScript}
Includes                   : {Function, RoleCapability, Command, DscResource...}
PowerShellGetFormatVersion :
ReleaseNotes               :
Dependencies               : {}
RepositorySourceLocation   : https://www.powershellgallery.com/api/v2/
Repository                 : PSGallery
PackageManagementProvider  : NuGet
AdditionalMetadata         : {description, installeddate, tags, PackageManagementProvider...}
InstalledLocation          : C:\Program Files\WindowsPowerShell\Scripts


```

