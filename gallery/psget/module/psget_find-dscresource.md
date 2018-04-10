---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: 資源庫,powershell,cmdlet,psget
title: Find-DscResource
ms.openlocfilehash: 522a44e25c57a7dd75a098a1f34e53e74d96f4a6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="find-dscresource"></a><span data-ttu-id="da82e-103">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="da82e-103">Find-DscResource</span></span>

<span data-ttu-id="da82e-104">尋找模組中的 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="da82e-104">Finds DSC Resources in modules.</span></span>

## <a name="description"></a><span data-ttu-id="da82e-105">描述</span><span class="sxs-lookup"><span data-stu-id="da82e-105">Description</span></span>

<span data-ttu-id="da82e-106">Find-DscResource Cmdlet 會從已註冊存放庫中尋找符合指定準則之模組中所含的[預期狀態設定 (DSC)](https://msdn.microsoft.com/PowerShell/dsc/overview) 資源。</span><span class="sxs-lookup"><span data-stu-id="da82e-106">The Find-DscResource cmdlet finds [Desired State Configuration (DSC)](https://msdn.microsoft.com/PowerShell/dsc/overview) resources contained in modules that match the specified criteria from registered repositories.</span></span>
<span data-ttu-id="da82e-107">針對這個 Cmdlet 所找到的每個群組，Find-DscResource 會傳回 PSGetDscResourceInfo 物件，而您可以將這個物件傳送至 Install-Module，來安裝包含這個 Cmdlet 所傳回之資源的模組。</span><span class="sxs-lookup"><span data-stu-id="da82e-107">For each module that this cmdlet finds, Find-DscResource returns a PSGetDscResourceInfo object that you can pipe to Install-Module to install the modules containing the resources that this cmdlet returns.</span></span>

<span data-ttu-id="da82e-108">DSC 是 Windows PowerShell 中的新管理平台，可讓您部署和管理軟體服務的設定資料及管理這些服務執行的環境。</span><span class="sxs-lookup"><span data-stu-id="da82e-108">DSC is a new management platform in Windows PowerShell that enables deploying and managing configuration data for software services and managing the environment in which these services run.</span></span>

<span data-ttu-id="da82e-109">預期狀態設定 (DSC) 資源提供 DSC 設定的建置組塊。</span><span class="sxs-lookup"><span data-stu-id="da82e-109">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="da82e-110">資源會公開可以設定的屬性 (結構描述)，而且這些屬性包含本機設定管理員 (LCM) 稱之為「make it so (讓它變成這樣)」的 PowerShell 指令碼函式。</span><span class="sxs-lookup"><span data-stu-id="da82e-110">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="da82e-111">資源可以建立某些物件的模型，像檔案一樣平常或如 IIS 伺服器設定一樣專用。</span><span class="sxs-lookup"><span data-stu-id="da82e-111">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span> <span data-ttu-id="da82e-112">類似資源的群組會併入 DSC 模組，將所有必要的檔案組織到可攜式結構中，而且包含中繼資料以識別資源的原訂用法。</span><span class="sxs-lookup"><span data-stu-id="da82e-112">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

- <span data-ttu-id="da82e-113">Find-DscResource 可以使用版本參數 MinimumVersion、RequiredVersion、AllVersions 進行篩選。</span><span class="sxs-lookup"><span data-stu-id="da82e-113">Find-DscResource can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="da82e-114">這些參數互斥。</span><span class="sxs-lookup"><span data-stu-id="da82e-114">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="da82e-115">只有不含任何萬用字元的單一模組名稱才允許使用這些版本參數。</span><span class="sxs-lookup"><span data-stu-id="da82e-115">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="da82e-116">如果未指定 RequiredVersion 參數，Find-DscResource 會傳回等於或大於所指定最小版本之模組的最新版本，或未指定最小版本之模組的最新版本。</span><span class="sxs-lookup"><span data-stu-id="da82e-116">If the RequiredVersion parameter is not specified, Find-DscResource returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="da82e-117">如果指定 RequiredVersion 參數，Find-DscResource 只會傳回完全符合所指定版本之模組的版本。</span><span class="sxs-lookup"><span data-stu-id="da82e-117">If the RequiredVersion parameter is specified, Find-DscResource only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="da82e-118">Find-DscResource 可以使用 -Tag 參數篩選模組中繼資料。</span><span class="sxs-lookup"><span data-stu-id="da82e-118">Find-DscResource can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="da82e-119">Find-DscResource 可以使用 -Filter 參數篩選存放庫特定的搜尋語言。</span><span class="sxs-lookup"><span data-stu-id="da82e-119">Find-DscResource can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="da82e-120">Find-DscResource 可以篩選所有或部分已註冊存放庫中的模組。</span><span class="sxs-lookup"><span data-stu-id="da82e-120">Find-DscResource can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="da82e-121">Cmdlet 語法</span><span class="sxs-lookup"><span data-stu-id="da82e-121">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-DscResource -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="da82e-122">Cmdlet 線上說明參考資料</span><span class="sxs-lookup"><span data-stu-id="da82e-122">Cmdlet online help reference</span></span>

[<span data-ttu-id="da82e-123">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="da82e-123">Find-DscResource</span></span>](http://go.microsoft.com/fwlink/?LinkId=517196)

## <a name="example-commands"></a><span data-ttu-id="da82e-124">範例命令</span><span class="sxs-lookup"><span data-stu-id="da82e-124">Example commands</span></span>
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