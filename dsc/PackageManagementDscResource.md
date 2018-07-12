---
ms.date: 06/20/2018
keywords: dsc,powershell,設定,安裝
title: DSC PackageManagement 資源
ms.openlocfilehash: 281aee13eb005f00b23c97870eaefaa332d9c232
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892496"
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="008ec-103">DSC PackageManagement 資源</span><span class="sxs-lookup"><span data-stu-id="008ec-103">DSC PackageManagement Resource</span></span>

<span data-ttu-id="008ec-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0、Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="008ec-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="008ec-105">Windows PowerShell 預期狀態設定 (DSC) 中的 **PackageManagement** 資源，提供在目標節點上安裝或解除安裝「套件管理」套件的機制。</span><span class="sxs-lookup"><span data-stu-id="008ec-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="008ec-106">此資源需要 **PackageManagement** 模組，可從 [http://PowerShellGallery.com](http://PowerShellGallery.com) 取得。</span><span class="sxs-lookup"><span data-stu-id="008ec-106">This resource requires the **PackageManagement** module, available from [http://PowerShellGallery.com](http://PowerShellGallery.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="008ec-107">**PackageManagement** 模組至少應為 1.1.7.0 版，以下才是正確的屬性資訊。</span><span class="sxs-lookup"><span data-stu-id="008ec-107">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="008ec-108">語法</span><span class="sxs-lookup"><span data-stu-id="008ec-108">Syntax</span></span>

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [AdditionalParameters = [HashTable]]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [MaximumVersion = [string]]
    [MinimumVersion = [string]]
    [ProviderName = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [RequiredVersion = [string]]
    [Source = [string]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a><span data-ttu-id="008ec-109">Properties</span><span class="sxs-lookup"><span data-stu-id="008ec-109">Properties</span></span>

|  <span data-ttu-id="008ec-110">屬性</span><span class="sxs-lookup"><span data-stu-id="008ec-110">Property</span></span>  |  <span data-ttu-id="008ec-111">描述</span><span class="sxs-lookup"><span data-stu-id="008ec-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="008ec-112">名稱</span><span class="sxs-lookup"><span data-stu-id="008ec-112">Name</span></span>| <span data-ttu-id="008ec-113">指定要安裝或解除安裝之套件的名稱。</span><span class="sxs-lookup"><span data-stu-id="008ec-113">Specifies the name of the Package to be installed or uninstalled.</span></span>|
| <span data-ttu-id="008ec-114">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="008ec-114">AdditionalParameters</span></span>| <span data-ttu-id="008ec-115">針對將傳至 `Get-Package -AdditionalArguments` 的參數，特定提供者的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="008ec-115">Provider specific hashtable of parameters that would be passed to `Get-Package -AdditionalArguments`.</span></span> <span data-ttu-id="008ec-116">例如，針對 NuGet 提供者，您可以傳遞 DestinationPath 之類的其他參數。</span><span class="sxs-lookup"><span data-stu-id="008ec-116">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span>|
| <span data-ttu-id="008ec-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="008ec-117">Ensure</span></span>| <span data-ttu-id="008ec-118">判斷是否要安裝或解除安裝套件。</span><span class="sxs-lookup"><span data-stu-id="008ec-118">Determines whether the package is to be installed or uninstalled.</span></span>|
| <span data-ttu-id="008ec-119">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="008ec-119">MaximumVersion</span></span>|<span data-ttu-id="008ec-120">指定所要尋找套件的最高允許版本。</span><span class="sxs-lookup"><span data-stu-id="008ec-120">Specifies the maximum allowed version of the package that you want to find.</span></span> <span data-ttu-id="008ec-121">如果不加入此參數，資源便會尋找可用的最高版本套件。</span><span class="sxs-lookup"><span data-stu-id="008ec-121">If you do not add this parameter, the resource finds the highest available version of the package.</span></span>|
| <span data-ttu-id="008ec-122">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="008ec-122">MinimumVersion</span></span>|<span data-ttu-id="008ec-123">指定所要尋找套件的最低允許版本。</span><span class="sxs-lookup"><span data-stu-id="008ec-123">Specifies the minimum allowed version of the package that you want to find.</span></span> <span data-ttu-id="008ec-124">如果不加入此參數，資源便會尋找可用的最高版本套件，同時也會滿足 _MaximumVersion_ 參數所指定的最高指定版本。</span><span class="sxs-lookup"><span data-stu-id="008ec-124">If you do not add this parameter, the resource finds the highest available version of the package that also satisfies any maximum specified version specified by the _MaximumVersion_ parameter.</span></span>|
| <span data-ttu-id="008ec-125">ProviderName</span><span class="sxs-lookup"><span data-stu-id="008ec-125">ProviderName</span></span>| <span data-ttu-id="008ec-126">指定套件提供者名稱，以針對它設定套件搜尋的範圍。</span><span class="sxs-lookup"><span data-stu-id="008ec-126">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="008ec-127">您可以執行 `Get-PackageProvider` 來取得套件提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="008ec-127">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>|
| <span data-ttu-id="008ec-128">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="008ec-128">RequiredVersion</span></span>| <span data-ttu-id="008ec-129">指定您要安裝之套件的確切版本。</span><span class="sxs-lookup"><span data-stu-id="008ec-129">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="008ec-130">如果未指定此參數，此 DSC 資源便會安裝套件的最新可用版本，同時也會滿足 _MaximumVersion_ 參數所指定的最高版本。</span><span class="sxs-lookup"><span data-stu-id="008ec-130">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the _MaximumVersion_ parameter.</span></span>|
| <span data-ttu-id="008ec-131">來源</span><span class="sxs-lookup"><span data-stu-id="008ec-131">Source</span></span>| <span data-ttu-id="008ec-132">指定可以找到套件的套件來源名稱。</span><span class="sxs-lookup"><span data-stu-id="008ec-132">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="008ec-133">這可以是 URI，或是向 `Register-PackageSource` 或 PackageManagementSource DSC 資源註冊的來源。</span><span class="sxs-lookup"><span data-stu-id="008ec-133">This can either be a URI or a source registered with `Register-PackageSource` or PackageManagementSource DSC resource.</span></span>|
| <span data-ttu-id="008ec-134">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="008ec-134">SourceCredential</span></span> | <span data-ttu-id="008ec-135">指定有權限安裝指定套件提供者或來源之套件的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="008ec-135">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span>|

## <a name="additional-parameters"></a><span data-ttu-id="008ec-136">其他參數</span><span class="sxs-lookup"><span data-stu-id="008ec-136">Additional Parameters</span></span>

<span data-ttu-id="008ec-137">下表列出 AdditionalParameters 屬性的選項。</span><span class="sxs-lookup"><span data-stu-id="008ec-137">The following table lists options for the AdditionalParameters property.</span></span>
|  <span data-ttu-id="008ec-138">參數</span><span class="sxs-lookup"><span data-stu-id="008ec-138">Parameter</span></span>  | <span data-ttu-id="008ec-139">描述</span><span class="sxs-lookup"><span data-stu-id="008ec-139">Description</span></span>   |
|---|---|
| <span data-ttu-id="008ec-140">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="008ec-140">DestinationPath</span></span>| <span data-ttu-id="008ec-141">由內建 Nuget 提供者之類的提供者使用。</span><span class="sxs-lookup"><span data-stu-id="008ec-141">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="008ec-142">指定您想要安裝套件的檔案位置。</span><span class="sxs-lookup"><span data-stu-id="008ec-142">Specifies a file location where you want the package to be installed.</span></span>|
| <span data-ttu-id="008ec-143">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="008ec-143">InstallationPolicy</span></span>| <span data-ttu-id="008ec-144">由內建 Nuget 提供者之類的提供者使用。</span><span class="sxs-lookup"><span data-stu-id="008ec-144">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="008ec-145">判斷您是否信任套件來源。</span><span class="sxs-lookup"><span data-stu-id="008ec-145">Determines whether you trust the package's source.</span></span> <span data-ttu-id="008ec-146">只能是 "Untrusted" 或 "Trusted"。</span><span class="sxs-lookup"><span data-stu-id="008ec-146">One of: "Untrusted", "Trusted".</span></span>|

## <a name="example"></a><span data-ttu-id="008ec-147">範例</span><span class="sxs-lookup"><span data-stu-id="008ec-147">Example</span></span>

<span data-ttu-id="008ec-148">此範例會使用 **PackageManagement** DSC 資源安裝 **JQuery** NuGet 套件和 **GistProvider** PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="008ec-148">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="008ec-149">此範例會先確認必要的套件來源可以使用，然後定義 **JQuery** 和 **GistProvider** 套件 (分別是 NuGet 和 PowerShell) 的預期狀態 。</span><span class="sxs-lookup"><span data-stu-id="008ec-149">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

```powershell
Configuration PackageTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceLocation   = "https://www.powershellgallery.com/api/v2/"
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