---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: 資源庫,powershell,cmdlet,psget
title: Find-RoleCapability
ms.openlocfilehash: 89aacd604d54f6a5e9752790be65cc3bcc77c8e1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="find-rolecapability"></a>Find-RoleCapability

尋找模組中的角色功能。

## <a name="description"></a>描述
Find-RoleCapability Cmdlet 會尋找模組中的 PowerShell 角色功能。 Find-RoleCapability 會搜尋已註冊存放庫中的模組。
針對這個 Cmdlet 找到的每個角色功能，它會傳回 PSGetRoleCapabilityInfo 物件。 您可以將 PSGetRoleCapabilityInfo 物件傳遞至 Install-Module Cmdlet，以安裝包含這個角色功能的模組。
PowerShell 角色功能會定義使用者可在 Just Enough Administration (JEA) 端點使用的命令、應用程式等。 角色功能是由副檔名為 .psrc 的檔案所定義。

- Find-RoleCapability 可以使用版本參數 MinimumVersion、RequiredVersion、AllVersions 進行篩選。
  - 這些參數互斥。
  - 只有不含任何萬用字元的單一模組名稱才允許使用這些版本參數。
  - 如果未指定 RequiredVersion 參數，Find-RoleCapability 會傳回等於或大於所指定最小版本之模組的最新版本，或未指定最小版本之模組的最新版本。
  - 如果指定 RequiredVersion 參數，Find-RoleCapability 只會傳回完全符合所指定版本之模組的版本。
- Find-RoleCapability 可以使用 -Tag 參數篩選模組中繼資料。
- Find-RoleCapability 可以使用 -Filter 參數篩選存放庫特定的搜尋語言。
- Find-RoleCapability 可以篩選所有或部分已註冊存放庫中的模組。

## <a name="cmdlet-syntax"></a>Cmdlet 語法
```powershell
Get-Command -Name Find-RoleCapability -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Cmdlet 線上說明參考資料

[Find-RoleCapability](http://go.microsoft.com/fwlink/?LinkId=718029)

## <a name="example-commands"></a>範例命令
```powershell

# Find a specific role capability
Find-RoleCapability -Name Maintenance

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Maintenance                         1.5.0      RoleCapModule                       PrivatePSGallery

# Find multiple role capabilities
Find-RoleCapability -Name MyJeaRole, Maintenance

# Find all available role capabilities from all registered repositories
Find-RoleCapability

# Find available role capabilities from few registered repositories
Find-RoleCapability -Repository PSGallery,PrivatePSGallery

# Find all role capabilities in a specified repository
Find-RoleCapability -Repository PSGallery

# Find a role capability defined in a specific module
Find-RoleCapability -Name Maintenance -ModuleName RoleCapModule

# Find role capabilities from all versions of a module
Find-RoleCapability -ModuleName RoleCapModule -AllVersions

# Find role capabilities with module name and MinimumVersion.
Find-RoleCapability -ModuleName RoleCapModule -MinimumVersion 1.1

# Find role capabilities with module name and exact version
Find-RoleCapability -ModuleName RoleCapModule -RequiredVersion 1.4.0

# Find role capabilities defined modules with -Filter based search. -Filter searches in description and module names
Find-RoleCapability -Filter Cookbook
Find-RoleCapability -Filter RBAC

# Find all role capabilities with tags Azure or DSC in module metadata
Find-RoleCapability -Tag Azure, DSC

```