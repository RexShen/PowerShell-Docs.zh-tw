---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: 資源庫,powershell,cmdlet,psget
title: Find-Command
ms.openlocfilehash: 26ddf4824816db245131a0fc95b7d2a88bef8f4c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="find-command"></a><span data-ttu-id="434cf-103">Find-Command</span><span class="sxs-lookup"><span data-stu-id="434cf-103">Find-Command</span></span>

<span data-ttu-id="434cf-104">尋找模組中的 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="434cf-104">Finds PowerShell commands in modules.</span></span>

## <a name="description"></a><span data-ttu-id="434cf-105">描述</span><span class="sxs-lookup"><span data-stu-id="434cf-105">Description</span></span>
<span data-ttu-id="434cf-106">Find-Command Cmdlet 會尋找 PowerShell 命令，例如 Cmdlet、別名、函數和工作流程。</span><span class="sxs-lookup"><span data-stu-id="434cf-106">The Find-Command cmdlet finds PowerShell commands such as cmdlets, aliases, functions, and workflows.</span></span> <span data-ttu-id="434cf-107">Find-Command 會搜尋已註冊存放庫中的模組。</span><span class="sxs-lookup"><span data-stu-id="434cf-107">Find-Command searches modules in registered repositories.</span></span>
<span data-ttu-id="434cf-108">針對這個 Cmdlet 找到的每個命令，它會傳回 PSGetCommandInfo 物件。</span><span class="sxs-lookup"><span data-stu-id="434cf-108">For each command that this cmdlet finds, it returns a PSGetCommandInfo object.</span></span> <span data-ttu-id="434cf-109">您可以將 PSGetCommandInfo 物件傳遞至 Install-Module Cmdlet，以安裝包含這個命令的模組。</span><span class="sxs-lookup"><span data-stu-id="434cf-109">You can pass a PSGetCommandInfo object to the Install-Module cmdlet to install the module that contains the command.</span></span>

- <span data-ttu-id="434cf-110">Find-Command 可以使用版本參數 MinimumVersion、RequiredVersion、AllVersions 進行篩選。</span><span class="sxs-lookup"><span data-stu-id="434cf-110">Find-Command can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="434cf-111">這些參數互斥。</span><span class="sxs-lookup"><span data-stu-id="434cf-111">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="434cf-112">只有不含任何萬用字元的單一模組名稱才允許使用這些版本參數。</span><span class="sxs-lookup"><span data-stu-id="434cf-112">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="434cf-113">如果未指定 RequiredVersion 參數，Find-Command 會傳回等於或大於所指定最小版本之模組的最新版本，或未指定最小版本之模組的最新版本。</span><span class="sxs-lookup"><span data-stu-id="434cf-113">If the RequiredVersion parameter is not specified, Find-Command returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="434cf-114">如果指定 RequiredVersion 參數，Find-Command 只會傳回完全符合所指定版本之模組的版本。</span><span class="sxs-lookup"><span data-stu-id="434cf-114">If the RequiredVersion parameter is specified, Find-Command only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="434cf-115">Find-Command 可以使用 -Tag 參數篩選模組中繼資料</span><span class="sxs-lookup"><span data-stu-id="434cf-115">Find-Command can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="434cf-116">Find-Command 可以使用 -Filter 參數篩選存放庫特定的搜尋語言。</span><span class="sxs-lookup"><span data-stu-id="434cf-116">Find-Command can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="434cf-117">Find-Command 可以篩選所有或部分已註冊存放庫中的模組。</span><span class="sxs-lookup"><span data-stu-id="434cf-117">Find-Command can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="434cf-118">Cmdlet 語法</span><span class="sxs-lookup"><span data-stu-id="434cf-118">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-Command -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="434cf-119">Cmdlet 線上說明參考資料</span><span class="sxs-lookup"><span data-stu-id="434cf-119">Cmdlet online help reference</span></span>

[<span data-ttu-id="434cf-120">Find-Command</span><span class="sxs-lookup"><span data-stu-id="434cf-120">Find-Command</span></span>](http://go.microsoft.com/fwlink/?LinkId=733636)

## <a name="example-commands"></a><span data-ttu-id="434cf-121">範例命令</span><span class="sxs-lookup"><span data-stu-id="434cf-121">Example commands</span></span>
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