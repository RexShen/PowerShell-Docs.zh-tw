---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "資源庫,powershell,cmdlet,psget"
title: Find-DscResource
ms.openlocfilehash: 37ba7925d6f73c453126f25e0818b3f8839d3b3b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
<a id="find-dscresource" class="xliff"></a>
# Find-DscResource

尋找模組中的 DSC 資源。

<a id="description" class="xliff"></a>
## 描述

Find-DscResource Cmdlet 會從已註冊存放庫中尋找符合指定準則之模組中所含的[預期狀態設定 (DSC)](https://msdn.microsoft.com/en-us/PowerShell/dsc/overview) 資源。
針對這個 Cmdlet 所找到的每個群組，Find-DscResource 會傳回 PSGetDscResourceInfo 物件，而您可以將這個物件傳送至 Install-Module，來安裝包含這個 Cmdlet 所傳回之資源的模組。

DSC 是 Windows PowerShell 中的新管理平台，可讓您部署和管理軟體服務的設定資料及管理這些服務執行的環境。

預期狀態設定 (DSC) 資源提供 DSC 設定的建置組塊。 資源會公開可以設定的屬性 (結構描述)，而且這些屬性包含本機設定管理員 (LCM) 稱之為「make it so (讓它變成這樣)」的 PowerShell 指令碼函式。

資源可以建立某些物件的模型，像檔案一樣平常或如 IIS 伺服器設定一樣專用。 類似資源的群組會併入 DSC 模組，將所有必要的檔案組織到可攜式結構中，而且包含中繼資料以識別資源的原訂用法。

- Find-DscResource 可以使用版本參數 MinimumVersion、RequiredVersion、AllVersions 進行篩選。
  - 這些參數互斥。
  - 只有不含任何萬用字元的單一模組名稱才允許使用這些版本參數。
  - 如果未指定 RequiredVersion 參數，Find-DscResource 會傳回等於或大於所指定最小版本之模組的最新版本，或未指定最小版本之模組的最新版本。
  - 如果指定 RequiredVersion 參數，Find-DscResource 只會傳回完全符合所指定版本之模組的版本。
- Find-DscResource 可以使用 -Tag 參數篩選模組中繼資料。
- Find-DscResource 可以使用 -Filter 參數篩選存放庫特定的搜尋語言。
- Find-DscResource 可以篩選所有或部分已註冊存放庫中的模組。

<a id="cmdlet-syntax" class="xliff"></a>
## Cmdlet 語法
```powershell
Get-Command -Name Find-DscResource -Module PowerShellGet -Syntax
```

<a id="cmdlet-online-help-reference" class="xliff"></a>
## Cmdlet 線上說明參考資料

[Find-DscResource](http://go.microsoft.com/fwlink/?LinkId=517196)

<a id="example-commands" class="xliff"></a>
## 範例命令
```powershell

# Find a specific DSC Resource
Find-DscResource -Name xIisFeatureDelegation

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
xIisFeatureDelegation               1.10.0.0   xWebAdministration                  PSGallery

# Find all available DSC Resources from all registered repositories
Find-DscResource

# Find a DSC resource by name
Find-DscResource -Name xWebsite

# Find multiple DSC Resources
Find-DscResource -Name xIisHandler, xFirewall

# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking
Find-DscResource -ModuleName xWebAdministration

# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

# Find available DSC Resources from few registered repositories
Find-DscResource -Repository PSGallery,PrivatePSGallery

# Find all DSC Resources in a specified repository
Find-DscResource -Repository PSGallery

# Find DSC Resources from all versions of a module
Find-DscResource -ModuleName xNetworking -AllVersions

# Find DSC Resources with module name and MinimumVersion.
Find-DscResource -ModuleName xNetworking -MinimumVersion 1.1

# Find DSC Resources with module name and exact version
Find-DscResource -ModuleName xNetworking -RequiredVersion 2.1.1

# Find DSC Resources defined modules with -Filter based search. -Filter searches in description and module names
Find-DscResource -Filter Domain

# Find all DSC Resources with tags Azure or DSC in module metadata
Find-DscResource -Tag Azure, DSC

```

