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
# <a name="find-rolecapability"></a><span data-ttu-id="9a5e3-103">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="9a5e3-103">Find-RoleCapability</span></span>

<span data-ttu-id="9a5e3-104">尋找模組中的角色功能。</span><span class="sxs-lookup"><span data-stu-id="9a5e3-104">Finds role capabilities in modules.</span></span>

## <a name="description"></a><span data-ttu-id="9a5e3-105">描述</span><span class="sxs-lookup"><span data-stu-id="9a5e3-105">Description</span></span>
<span data-ttu-id="9a5e3-106">Find-RoleCapability Cmdlet 會尋找模組中的 PowerShell 角色功能。</span><span class="sxs-lookup"><span data-stu-id="9a5e3-106">The Find-RoleCapability cmdlet finds PowerShell role capabilities in modules.</span></span> <span data-ttu-id="9a5e3-107">Find-RoleCapability 會搜尋已註冊存放庫中的模組。</span><span class="sxs-lookup"><span data-stu-id="9a5e3-107">Find-RoleCapability searches modules in registered repositories.</span></span>
<span data-ttu-id="9a5e3-108">針對這個 Cmdlet 找到的每個角色功能，它會傳回 PSGetRoleCapabilityInfo 物件。</span><span class="sxs-lookup"><span data-stu-id="9a5e3-108">For each role capability that this cmdlet finds, it returns a PSGetRoleCapabilityInfo object.</span></span> <span data-ttu-id="9a5e3-109">您可以將 PSGetRoleCapabilityInfo 物件傳遞至 Install-Module Cmdlet，以安裝包含這個角色功能的模組。</span><span class="sxs-lookup"><span data-stu-id="9a5e3-109">You can pass a PSGetRoleCapabilityInfo object to the Install-Module cmdlet to install the module that contains the role capability.</span></span>
<span data-ttu-id="9a5e3-110">PowerShell 角色功能會定義使用者可在 Just Enough Administration (JEA) 端點使用的命令、應用程式等。</span><span class="sxs-lookup"><span data-stu-id="9a5e3-110">PowerShell role capabilities define which commands, applications, and so on are available to a user at a Just Enough Administration (JEA) endpoint.</span></span> <span data-ttu-id="9a5e3-111">角色功能是由副檔名為 .psrc 的檔案所定義。</span><span class="sxs-lookup"><span data-stu-id="9a5e3-111">Role capabilities are defined by files with a .psrc extension.</span></span>

- <span data-ttu-id="9a5e3-112">Find-RoleCapability 可以使用版本參數 MinimumVersion、RequiredVersion、AllVersions 進行篩選。</span><span class="sxs-lookup"><span data-stu-id="9a5e3-112">Find-RoleCapability can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="9a5e3-113">這些參數互斥。</span><span class="sxs-lookup"><span data-stu-id="9a5e3-113">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="9a5e3-114">只有不含任何萬用字元的單一模組名稱才允許使用這些版本參數。</span><span class="sxs-lookup"><span data-stu-id="9a5e3-114">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="9a5e3-115">如果未指定 RequiredVersion 參數，Find-RoleCapability 會傳回等於或大於所指定最小版本之模組的最新版本，或未指定最小版本之模組的最新版本。</span><span class="sxs-lookup"><span data-stu-id="9a5e3-115">If the RequiredVersion parameter is not specified, Find-RoleCapability returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="9a5e3-116">如果指定 RequiredVersion 參數，Find-RoleCapability 只會傳回完全符合所指定版本之模組的版本。</span><span class="sxs-lookup"><span data-stu-id="9a5e3-116">If the RequiredVersion parameter is specified, Find-RoleCapability only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="9a5e3-117">Find-RoleCapability 可以使用 -Tag 參數篩選模組中繼資料。</span><span class="sxs-lookup"><span data-stu-id="9a5e3-117">Find-RoleCapability can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="9a5e3-118">Find-RoleCapability 可以使用 -Filter 參數篩選存放庫特定的搜尋語言。</span><span class="sxs-lookup"><span data-stu-id="9a5e3-118">Find-RoleCapability can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="9a5e3-119">Find-RoleCapability 可以篩選所有或部分已註冊存放庫中的模組。</span><span class="sxs-lookup"><span data-stu-id="9a5e3-119">Find-RoleCapability can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="9a5e3-120">Cmdlet 語法</span><span class="sxs-lookup"><span data-stu-id="9a5e3-120">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-RoleCapability -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="9a5e3-121">Cmdlet 線上說明參考資料</span><span class="sxs-lookup"><span data-stu-id="9a5e3-121">Cmdlet online help reference</span></span>

[<span data-ttu-id="9a5e3-122">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="9a5e3-122">Find-RoleCapability</span></span>](http://go.microsoft.com/fwlink/?LinkId=718029)

## <a name="example-commands"></a><span data-ttu-id="9a5e3-123">範例命令</span><span class="sxs-lookup"><span data-stu-id="9a5e3-123">Example commands</span></span>
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