---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "DSC PackageManagement 資源"
ms.openlocfilehash: 4cd7625af7ed0bb3fe971c826ac2075841cdfdc5
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="9eeaa-103">DSC PackageManagement 資源</span><span class="sxs-lookup"><span data-stu-id="9eeaa-103">DSC PackageManagement Resource</span></span>

> <span data-ttu-id="9eeaa-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9eeaa-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="9eeaa-105">Windows PowerShell 預期狀態設定 (DSC) 中的 **PackageManagement** 資源，提供在目標節點上安裝或解除安裝「套件管理」套件的機制。</span><span class="sxs-lookup"><span data-stu-id="9eeaa-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="9eeaa-106">此資源需要 **PackageManagement** 模組，可從 http://PowerShellGallery.com 取得。</span><span class="sxs-lookup"><span data-stu-id="9eeaa-106">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

## <a name="syntax"></a><span data-ttu-id="9eeaa-107">語法</span><span class="sxs-lookup"><span data-stu-id="9eeaa-107">Syntax</span></span>

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ Source = [string] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ RequiredVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ MaximumVersion = [string] ]
    [ SourceCredential = [PSCredential] ]
    [ ProviderName = [string] ]
    [ AdditionalParameters = [Microsoft.Management.Infrastructure.CimInstance[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="9eeaa-108">Properties</span><span class="sxs-lookup"><span data-stu-id="9eeaa-108">Properties</span></span>
|  <span data-ttu-id="9eeaa-109">屬性</span><span class="sxs-lookup"><span data-stu-id="9eeaa-109">Property</span></span>  |  <span data-ttu-id="9eeaa-110">描述</span><span class="sxs-lookup"><span data-stu-id="9eeaa-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="9eeaa-111">名稱</span><span class="sxs-lookup"><span data-stu-id="9eeaa-111">Name</span></span>| <span data-ttu-id="9eeaa-112">指定要安裝或解除安裝之套件的名稱。</span><span class="sxs-lookup"><span data-stu-id="9eeaa-112">Specifies the name of the Package to be installed or uninstalled.</span></span>| 
| <span data-ttu-id="9eeaa-113">來源</span><span class="sxs-lookup"><span data-stu-id="9eeaa-113">Source</span></span>| <span data-ttu-id="9eeaa-114">指定可以找到套件的套件來源名稱。</span><span class="sxs-lookup"><span data-stu-id="9eeaa-114">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="9eeaa-115">這可以是 URI，或是向 Register-PackageSource 或 PackageManagementSource DSC 資源註冊的來源。</span><span class="sxs-lookup"><span data-stu-id="9eeaa-115">This can either be a URI or a source registered with Register-PackageSource or PackageManagementSource DSC resource.</span></span> <span data-ttu-id="9eeaa-116">DSC 資源 MSFT_PackageManagementSource 也可以註冊套件來源。</span><span class="sxs-lookup"><span data-stu-id="9eeaa-116">The DSC resource MSFT_PackageManagementSource can also register a package source.</span></span>| 
| <span data-ttu-id="9eeaa-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="9eeaa-117">Ensure</span></span>| <span data-ttu-id="9eeaa-118">判斷是否要安裝或解除安裝套件。</span><span class="sxs-lookup"><span data-stu-id="9eeaa-118">Determines whether the package is to be installed or uninstalled.</span></span>| 
| <span data-ttu-id="9eeaa-119">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="9eeaa-119">RequiredVersion</span></span>| <span data-ttu-id="9eeaa-120">指定您要安裝之套件的確切版本。</span><span class="sxs-lookup"><span data-stu-id="9eeaa-120">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="9eeaa-121">如果未指定此參數，此 DSC 資源會安裝套件的最新可用版本，同時也會滿足 MaximumVersion 參數所指定的最高允許版本。</span><span class="sxs-lookup"><span data-stu-id="9eeaa-121">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the MaximumVersion parameter.</span></span>| 
| <span data-ttu-id="9eeaa-122">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="9eeaa-122">MinimumVersion</span></span>| <span data-ttu-id="9eeaa-123">指定您要安裝之套件的最低允許版本。</span><span class="sxs-lookup"><span data-stu-id="9eeaa-123">Specifies the minimum allowed version of the package that you want to install.</span></span> <span data-ttu-id="9eeaa-124">如果您沒有加入此參數，此 DSC 資源會安裝套件的最高可用版本，同時也會滿足 MaximumVersion 參數所指定的最高允許版本。</span><span class="sxs-lookup"><span data-stu-id="9eeaa-124">If you do not add this parameter, this DSC resource intalls the highest available version of the package that also satisfies any maximum specified version specified by the MaximumVersion parameter.</span></span>| 
| <span data-ttu-id="9eeaa-125">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="9eeaa-125">MaximumVersion</span></span>| <span data-ttu-id="9eeaa-126">指定您要安裝之套件的最高允許版本。</span><span class="sxs-lookup"><span data-stu-id="9eeaa-126">Specifies the maximum allowed version of the package that you want to install.</span></span> <span data-ttu-id="9eeaa-127">如果未指定此參數，此 DSC 資源會安裝套件的最高編號可用版本。</span><span class="sxs-lookup"><span data-stu-id="9eeaa-127">If you do not specify this parameter, this DSC resource installs the highest-numbered available version of the package.</span></span>| 
| <span data-ttu-id="9eeaa-128">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="9eeaa-128">SourceCredential</span></span> | <span data-ttu-id="9eeaa-129">指定有權限安裝指定套件提供者或來源之套件的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="9eeaa-129">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span>| 
| <span data-ttu-id="9eeaa-130">ProviderName</span><span class="sxs-lookup"><span data-stu-id="9eeaa-130">ProviderName</span></span>| <span data-ttu-id="9eeaa-131">指定套件提供者名稱，以針對它設定套件搜尋的範圍。</span><span class="sxs-lookup"><span data-stu-id="9eeaa-131">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="9eeaa-132">您可以執行 Get-PackageProvider Cmdlet 來取得套件提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="9eeaa-132">You can get package provider names by running the Get-PackageProvider cmdlet.</span></span>| 
| <span data-ttu-id="9eeaa-133">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="9eeaa-133">AdditionalParameters</span></span>| <span data-ttu-id="9eeaa-134">以雜湊表傳遞的提供者特定參數。</span><span class="sxs-lookup"><span data-stu-id="9eeaa-134">Provider specific parameters that are passed as an Hashtable.</span></span> <span data-ttu-id="9eeaa-135">例如，針對 NuGet 提供者，您可以傳遞 DestinationPath 之類的其他參數。</span><span class="sxs-lookup"><span data-stu-id="9eeaa-135">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span>| 

## <a name="additional-parameters"></a><span data-ttu-id="9eeaa-136">其他參數</span><span class="sxs-lookup"><span data-stu-id="9eeaa-136">Additional Parameters</span></span>
<span data-ttu-id="9eeaa-137">下表列出 AdditionalParameters 屬性的選項。</span><span class="sxs-lookup"><span data-stu-id="9eeaa-137">The following table lists options for the AdditionalParameters property.</span></span>
|  <span data-ttu-id="9eeaa-138">參數</span><span class="sxs-lookup"><span data-stu-id="9eeaa-138">Parameter</span></span>  | <span data-ttu-id="9eeaa-139">描述</span><span class="sxs-lookup"><span data-stu-id="9eeaa-139">Description</span></span>   | 
|---|---|
| <span data-ttu-id="9eeaa-140">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="9eeaa-140">DestinationPath</span></span>| <span data-ttu-id="9eeaa-141">由內建 Nuget 提供者之類的提供者使用。</span><span class="sxs-lookup"><span data-stu-id="9eeaa-141">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="9eeaa-142">指定您想要安裝套件的檔案位置。</span><span class="sxs-lookup"><span data-stu-id="9eeaa-142">Specifies a file location where you want the package to be installed.</span></span>|
| <span data-ttu-id="9eeaa-143">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="9eeaa-143">InstallationPolicy</span></span>| <span data-ttu-id="9eeaa-144">由內建 Nuget 提供者之類的提供者使用。</span><span class="sxs-lookup"><span data-stu-id="9eeaa-144">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="9eeaa-145">判斷您是否信任套件來源。</span><span class="sxs-lookup"><span data-stu-id="9eeaa-145">Determines whether you trust the package's source.</span></span> <span data-ttu-id="9eeaa-146">只能是 "Untrusted" 或 "Trusted"。</span><span class="sxs-lookup"><span data-stu-id="9eeaa-146">One of: "Untrusted", "Trusted".</span></span>|

## <a name="example"></a><span data-ttu-id="9eeaa-147">範例</span><span class="sxs-lookup"><span data-stu-id="9eeaa-147">Example</span></span>

<span data-ttu-id="9eeaa-148">此範例會使用 **PackageManagement** DSC 資源安裝 **JQuery** NuGet 套件和 **GistProvider** PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="9eeaa-148">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="9eeaa-149">此範例會先確認必要的套件來源可以使用，然後定義 **JQuery** 和 **GistProvider** 套件 (分別是 NuGet 和 PowerShell) 的預期狀態 。</span><span class="sxs-lookup"><span data-stu-id="9eeaa-149">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

```powershell
Configuration PackageTest
{    
    PackageManagementSource SourceRepository 
    { 
        Ensure      = "Present" 
        Name        = "MyNuget" 
        ProviderName= "Nuget" 
        SourceUri   = "http://nuget.org/api/v2/"   
        InstallationPolicy ="Trusted" 
    }    
    
    PackageManagementSource PSGallery 
    { 
        Ensure      = "Present" 
        Name        = "psgallery" 
        ProviderName= "PowerShellGet" 
        SourceUri   = "https://www.powershellgallery.com/api/v2/"   
        InstallationPolicy ="Trusted" 
    } 
          
    PackageManagement NugetPackage 
    { 
        Ensure               = "Present"  
        Name                 = "JQuery"
        AdditionalParameters = "$env:HomeDrive\nuget"
        RequiredVersion      = "2.0.1" 
        DependsOn            = "[PackageManagementSource]SourceRepository" 
    }
    
    PackageManagement PSModule 
    { 
        Ensure               = "Present"  
        Name                 = "gistprovider"
        Source               = "PSGallery"
        DependsOn            = "[PackageManagementSource]PSGallery" 
    }
}
```

