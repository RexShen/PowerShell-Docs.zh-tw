---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "資源庫,powershell,cmdlet,psget"
title: Find-Command
ms.openlocfilehash: f867f12b1c6efad30a04581c6f36c5a77a2fb2ae
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
<a id="find-command" class="xliff"></a>
# Find-Command

尋找模組中的 PowerShell 命令。

<a id="description" class="xliff"></a>
## 描述
Find-Command Cmdlet 會尋找 PowerShell 命令，例如 Cmdlet、別名、函數和工作流程。 Find-Command 會搜尋已註冊存放庫中的模組。
針對這個 Cmdlet 找到的每個命令，它會傳回 PSGetCommandInfo 物件。 您可以將 PSGetCommandInfo 物件傳遞至 Install-Module Cmdlet，以安裝包含這個命令的模組。

- Find-Command 可以使用版本參數 MinimumVersion、RequiredVersion、AllVersions 進行篩選。
  - 這些參數互斥。
  - 只有不含任何萬用字元的單一模組名稱才允許使用這些版本參數。
  - 如果未指定 RequiredVersion 參數，Find-Command 會傳回等於或大於所指定最小版本之模組的最新版本，或未指定最小版本之模組的最新版本。
  - 如果指定 RequiredVersion 參數，Find-Command 只會傳回完全符合所指定版本之模組的版本。
- Find-Command 可以使用 -Tag 參數篩選模組中繼資料
- Find-Command 可以使用 -Filter 參數篩選存放庫特定的搜尋語言。
- Find-Command 可以篩選所有或部分已註冊存放庫中的模組。

<a id="cmdlet-syntax" class="xliff"></a>
## Cmdlet 語法
```powershell
Get-Command -Name Find-Command -Module PowerShellGet -Syntax
```

<a id="cmdlet-online-help-reference" class="xliff"></a>
## Cmdlet 線上說明參考資料

[Find-Command](http://go.microsoft.com/fwlink/?LinkId=733636)

<a id="example-commands" class="xliff"></a>
## 範例命令
```powershell

# Find a specific command
Find-Command -Name Get-ScriptAnalyzerRule

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Get-ScriptAnalyzerRule              1.5.0      PSScriptAnalyzer                    PSGallery

# Find multiple commands
Find-Command -Name Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

# Find all available commands from all registered repositories
Find-Command

# Find available commands from few registered repositories
Find-Command -Repository PSGallery,PrivatePSGallery

# Find all commands in a specified repository
Find-Command -Repository PSGallery

# Find a command defined in a specific module
Find-Command -Name Get-ScriptAnalyzerRule -Module PSScriptAnalyzer

# Find commands from all versions of a module
Find-Command -ModuleName PSReadline -AllVersions

# Find commands with module name and MinimumVersion.
Find-Command -ModuleName PSReadline -MinimumVersion 1.1

# Find commands with module name and exact version
Find-Command -ModuleName AzureRM -RequiredVersion 1.4.0

# Find commands defined modules with -Filter based search. -Filter searches in description and module names
Find-Command -Filter Cookbook
Find-Command -Filter RBAC

# Find all commands with tags Azure or DSC in module metadata
Find-Command -Tag Azure, DSC

```

