---
ms.date: 09/20/2019
keywords: dsc,powershell,設定,安裝
title: DSC PackageManagement 資源
ms.openlocfilehash: dfc23bfabbc45041e15c56a29a77c5bdda430a30
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953235"
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="a6669-103">DSC PackageManagement 資源</span><span class="sxs-lookup"><span data-stu-id="a6669-103">DSC PackageManagement Resource</span></span>

<span data-ttu-id="a6669-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0、Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="a6669-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="a6669-105">Windows PowerShell 預期狀態設定 (DSC) 中的 **PackageManagement** 資源，提供在目標節點上安裝或解除安裝「套件管理」套件的機制。</span><span class="sxs-lookup"><span data-stu-id="a6669-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="a6669-106">此資源需要 **PackageManagement** 模組，可從 [http://PowerShellGallery.com](https://PowerShellGallery.com) 取得。</span><span class="sxs-lookup"><span data-stu-id="a6669-106">This resource requires the **PackageManagement** module, available from [http://PowerShellGallery.com](https://PowerShellGallery.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a6669-107">**PackageManagement** 模組至少應為 1.1.7.0 版，以下才是正確的屬性資訊。</span><span class="sxs-lookup"><span data-stu-id="a6669-107">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="a6669-108">語法</span><span class="sxs-lookup"><span data-stu-id="a6669-108">Syntax</span></span>

```Syntax
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ AdditionalParameters = [HashTable] ]
    [ MaximumVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ ProviderName = [string] ]
    [ RequiredVersion = [string] ]
    [ Source = [string] ]
    [ SourceCredential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string]{ Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="a6669-109">Properties</span><span class="sxs-lookup"><span data-stu-id="a6669-109">Properties</span></span>

|<span data-ttu-id="a6669-110">屬性</span><span class="sxs-lookup"><span data-stu-id="a6669-110">Property</span></span> |<span data-ttu-id="a6669-111">描述</span><span class="sxs-lookup"><span data-stu-id="a6669-111">Description</span></span> |
|---|---|
|<span data-ttu-id="a6669-112">名稱</span><span class="sxs-lookup"><span data-stu-id="a6669-112">Name</span></span> |<span data-ttu-id="a6669-113">指定要安裝或解除安裝之套件的名稱。</span><span class="sxs-lookup"><span data-stu-id="a6669-113">Specifies the name of the Package to be installed or uninstalled.</span></span> |
|<span data-ttu-id="a6669-114">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="a6669-114">AdditionalParameters</span></span> |<span data-ttu-id="a6669-115">針對將傳至 `Get-Package -AdditionalArguments` 的參數，特定提供者的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="a6669-115">Provider specific hashtable of parameters that would be passed to `Get-Package -AdditionalArguments`.</span></span> <span data-ttu-id="a6669-116">例如，針對 NuGet 提供者，您可以傳遞 DestinationPath 之類的其他參數。</span><span class="sxs-lookup"><span data-stu-id="a6669-116">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span> |
|<span data-ttu-id="a6669-117">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="a6669-117">MaximumVersion</span></span> |<span data-ttu-id="a6669-118">指定所要尋找套件的最高允許版本。</span><span class="sxs-lookup"><span data-stu-id="a6669-118">Specifies the maximum allowed version of the package that you want to find.</span></span> <span data-ttu-id="a6669-119">如果不加入此參數，資源便會尋找可用的最高版本套件。</span><span class="sxs-lookup"><span data-stu-id="a6669-119">If you do not add this parameter, the resource finds the highest available version of the package.</span></span> |
|<span data-ttu-id="a6669-120">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="a6669-120">MinimumVersion</span></span> |<span data-ttu-id="a6669-121">指定所要尋找套件的最低允許版本。</span><span class="sxs-lookup"><span data-stu-id="a6669-121">Specifies the minimum allowed version of the package that you want to find.</span></span> <span data-ttu-id="a6669-122">如果不加入此參數，資源便會尋找可用的最高版本套件，同時也會滿足 **MaximumVersion** 參數所指定的最高指定版本。</span><span class="sxs-lookup"><span data-stu-id="a6669-122">If you do not add this parameter, the resource finds the highest available version of the package that also satisfies any maximum specified version specified by the **MaximumVersion** parameter.</span></span> |
|<span data-ttu-id="a6669-123">ProviderName</span><span class="sxs-lookup"><span data-stu-id="a6669-123">ProviderName</span></span> |<span data-ttu-id="a6669-124">指定套件提供者名稱，以針對它設定套件搜尋的範圍。</span><span class="sxs-lookup"><span data-stu-id="a6669-124">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="a6669-125">您可以執行 `Get-PackageProvider` 來取得套件提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="a6669-125">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span> |
|<span data-ttu-id="a6669-126">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="a6669-126">RequiredVersion</span></span> |<span data-ttu-id="a6669-127">指定您要安裝之套件的確切版本。</span><span class="sxs-lookup"><span data-stu-id="a6669-127">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="a6669-128">如果未指定此參數，此 DSC 資源便會安裝套件的最新可用版本，同時也會滿足 **MaximumVersion** 參數所指定的最高版本。</span><span class="sxs-lookup"><span data-stu-id="a6669-128">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the **MaximumVersion** parameter.</span></span> |
|<span data-ttu-id="a6669-129">來源</span><span class="sxs-lookup"><span data-stu-id="a6669-129">Source</span></span> |<span data-ttu-id="a6669-130">指定可以找到套件的套件來源名稱。</span><span class="sxs-lookup"><span data-stu-id="a6669-130">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="a6669-131">這可以是 URI，或是向 `Register-PackageSource` 或 PackageManagementSource DSC 資源註冊的來源。</span><span class="sxs-lookup"><span data-stu-id="a6669-131">This can either be a URI or a source registered with `Register-PackageSource` or PackageManagementSource DSC resource.</span></span> |
|<span data-ttu-id="a6669-132">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="a6669-132">SourceCredential</span></span> |<span data-ttu-id="a6669-133">指定有權限安裝指定套件提供者或來源之套件的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="a6669-133">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span> |

## <a name="additional-parameters"></a><span data-ttu-id="a6669-134">其他參數</span><span class="sxs-lookup"><span data-stu-id="a6669-134">Additional Parameters</span></span>

<span data-ttu-id="a6669-135">下表列出 AdditionalParameters 屬性的選項。</span><span class="sxs-lookup"><span data-stu-id="a6669-135">The following table lists options for the AdditionalParameters property.</span></span>

|<span data-ttu-id="a6669-136">參數</span><span class="sxs-lookup"><span data-stu-id="a6669-136">Parameter</span></span> |<span data-ttu-id="a6669-137">描述</span><span class="sxs-lookup"><span data-stu-id="a6669-137">Description</span></span> |
|---|---|
|<span data-ttu-id="a6669-138">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="a6669-138">DestinationPath</span></span> |<span data-ttu-id="a6669-139">由內建 Nuget 提供者之類的提供者使用。</span><span class="sxs-lookup"><span data-stu-id="a6669-139">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="a6669-140">指定您想要安裝套件的檔案位置。</span><span class="sxs-lookup"><span data-stu-id="a6669-140">Specifies a file location where you want the package to be installed.</span></span> |
|<span data-ttu-id="a6669-141">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="a6669-141">InstallationPolicy</span></span> |<span data-ttu-id="a6669-142">由內建 Nuget 提供者之類的提供者使用。</span><span class="sxs-lookup"><span data-stu-id="a6669-142">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="a6669-143">判斷您是否信任套件來源。</span><span class="sxs-lookup"><span data-stu-id="a6669-143">Determines whether you trust the package's source.</span></span> <span data-ttu-id="a6669-144">值為下列其中之一：**Untrusted**、**Trusted**。</span><span class="sxs-lookup"><span data-stu-id="a6669-144">One of: **Untrusted** or **Trusted**.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="a6669-145">通用屬性</span><span class="sxs-lookup"><span data-stu-id="a6669-145">Common properties</span></span>

|<span data-ttu-id="a6669-146">屬性</span><span class="sxs-lookup"><span data-stu-id="a6669-146">Property</span></span> |<span data-ttu-id="a6669-147">描述</span><span class="sxs-lookup"><span data-stu-id="a6669-147">Description</span></span> |
|---|---|
|<span data-ttu-id="a6669-148">DependsOn</span><span class="sxs-lookup"><span data-stu-id="a6669-148">DependsOn</span></span> |<span data-ttu-id="a6669-149">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="a6669-149">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a6669-150">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="a6669-150">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="a6669-151">Ensure</span><span class="sxs-lookup"><span data-stu-id="a6669-151">Ensure</span></span> |<span data-ttu-id="a6669-152">判斷是否要安裝或解除安裝套件。</span><span class="sxs-lookup"><span data-stu-id="a6669-152">Determines whether the package is to be installed or uninstalled.</span></span> <span data-ttu-id="a6669-153">預設值為 **Present**。</span><span class="sxs-lookup"><span data-stu-id="a6669-153">The default value is **Present**.</span></span> |
|<span data-ttu-id="a6669-154">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="a6669-154">PsDscRunAsCredential</span></span> |<span data-ttu-id="a6669-155">設定用於執行整個資源的認證。</span><span class="sxs-lookup"><span data-stu-id="a6669-155">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="a6669-156">已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="a6669-156">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="a6669-157">如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="a6669-157">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="a6669-158">範例</span><span class="sxs-lookup"><span data-stu-id="a6669-158">Example</span></span>

<span data-ttu-id="a6669-159">此範例會使用 **PackageManagement** DSC 資源安裝 **JQuery** NuGet 套件和 **GistProvider** PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="a6669-159">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="a6669-160">此範例會先確認必要的套件來源可以使用，然後定義 **JQuery** 和 **GistProvider** 套件 (分別是 NuGet 和 PowerShell) 的預期狀態 。</span><span class="sxs-lookup"><span data-stu-id="a6669-160">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

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
        SourceLocation   = "https://www.powershellgallery.com/api/v2"
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