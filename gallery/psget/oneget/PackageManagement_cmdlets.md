---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "資源庫,powershell,cmdlet,psget"
title: PackageManagement_cmdlets
ms.openlocfilehash: aca4f461ff0e51aa812f8219c74bd7d85d1e7b2d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="packagemanagement-cmdlets"></a><span data-ttu-id="c335c-103">PackageManagement Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c335c-103">PackageManagement Cmdlets</span></span>
<span data-ttu-id="c335c-104">這是支援軟體探索、安裝和清查 (SDII) 的 PackageManagement 核心。</span><span class="sxs-lookup"><span data-stu-id="c335c-104">This is the core of PackageManagement to support software discovery, installation, and inventory (SDII).</span></span> <span data-ttu-id="c335c-105">試試看這些作業的 Cmdlet︰</span><span class="sxs-lookup"><span data-stu-id="c335c-105">Try out the cmdlets for these operations:</span></span>
-   <span data-ttu-id="c335c-106">Find-Package</span><span class="sxs-lookup"><span data-stu-id="c335c-106">Find-Package</span></span>
-   <span data-ttu-id="c335c-107">Find-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="c335c-107">Find-PackageProvider</span></span>
-   <span data-ttu-id="c335c-108">Get-Package</span><span class="sxs-lookup"><span data-stu-id="c335c-108">Get-Package</span></span>
-   <span data-ttu-id="c335c-109">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="c335c-109">Get-PackageProvider</span></span>
-   <span data-ttu-id="c335c-110">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="c335c-110">Get-PackageSource</span></span>
-   <span data-ttu-id="c335c-111">Import-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="c335c-111">Import-PackageProvider</span></span>
-   <span data-ttu-id="c335c-112">Install-Package</span><span class="sxs-lookup"><span data-stu-id="c335c-112">Install-Package</span></span>
-   <span data-ttu-id="c335c-113">Install-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="c335c-113">Install-PackageProvider</span></span>
-   <span data-ttu-id="c335c-114">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="c335c-114">Register-PackageSource</span></span>
-   <span data-ttu-id="c335c-115">Save-Package</span><span class="sxs-lookup"><span data-stu-id="c335c-115">Save-Package</span></span>
-   <span data-ttu-id="c335c-116">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="c335c-116">Set-PackageSource</span></span>
-   <span data-ttu-id="c335c-117">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="c335c-117">Uninstall-Package</span></span>
-   <span data-ttu-id="c335c-118">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="c335c-118">Unregister-PackageSource</span></span>

<span data-ttu-id="c335c-119">因為 PackageManagement 是 PowerShell 模組，您可執行下列作業更新 PackageManagement：</span><span class="sxs-lookup"><span data-stu-id="c335c-119">As PackageManagement is a PowerShell module, you can do the following to update PackageManagement itself:</span></span>
```powershell
PS C:\> Install-Module PackageManagement –Force
```
<span data-ttu-id="c335c-120">在本例中，您必須重新進入 PowerShell 工作階段，以切換至新版的 PackageManagement。</span><span class="sxs-lookup"><span data-stu-id="c335c-120">In this case, you will have to re-enter PowerShell session to switch to the new version of PackageManagement.</span></span>

## <a name="find-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890709aspx"></a>[<span data-ttu-id="c335c-121">Find-Package Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c335c-121">Find-Package Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890709.aspx)
<span data-ttu-id="c335c-122">這個 Cmdlet 可讓您使用載入的封裝提供者在可用的封裝來源中探索軟體封裝。</span><span class="sxs-lookup"><span data-stu-id="c335c-122">This cmdlet allows discovery of software packages in available package sources using loaded package providers.</span></span>
```powershell
# Find all available Windows PowerShell module packages from galleries registered
# with PowerShellGet provider
Find-Package -Provider PowerShellGet -Source PSGallery

# Find a package from a provider that is not yet installed
# This will bootstrap NuGet provider and then search for jquery package using NuGet
# with <http://www.nuget.org/api/v2/> as source
Find-Package -Name jquery –Provider NuGet -Source http://www.nuget.org/api/v2/

# Find package with name and version
# Here we are assuming that the user already registered nuget.org using
# Register-PackageSource. You can specify either the provider or the source, or
# neither. For the latter, performance may be less optimal as it searches through all
# the providers and registered sources.
Find-Package -Name jquery –Provider NuGet –RequiredVersion 2.1.4 -Source nuget.org
```

## <a name="find-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarymt676544aspx"></a>[<span data-ttu-id="c335c-123">Find-PackageProvider Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c335c-123">Find-PackageProvider Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/mt676544.aspx)
<span data-ttu-id="c335c-124">Find-PackageProvider Cmdlet 會在向 PowerShellGet 註冊的封裝來源中尋找相符的 PackageManagement 提供者。</span><span class="sxs-lookup"><span data-stu-id="c335c-124">The Find-PackageProvider cmdlet finds matching PackageManagement providers that are available in package sources registered with PowerShellGet.</span></span> <span data-ttu-id="c335c-125">這些是可使用 Install-PackageProvider Cmdlet 進行安裝的封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="c335c-125">These are package providers available for installation with the Install-PackageProvider cmdlet.</span></span> <span data-ttu-id="c335c-126">根據預設，這包括 PowerShell Gallery 提供之具有 'PackageManagement' 和 'Provider' 標記的模組。</span><span class="sxs-lookup"><span data-stu-id="c335c-126">By default, this includes modules available in the PowerShell Gallery with the 'PackageManagement' and 'Provider' Tags.</span></span> 

<span data-ttu-id="c335c-127">Find-PackageProvider 也會尋找相符的 PackageManagement 提供者，它們可在 PackageManagement Azure Blob 存放區中取得，我們在此存放區中使用 PackageManagement boostrapper 提供者尋找及安裝它們。</span><span class="sxs-lookup"><span data-stu-id="c335c-127">Find-PackageProvider also finds matching PackageManagement providers that are available in the PackageManagement azure blob store where we use the PackageManagement boostrapper provider for finding and installing them.</span></span>
```powershell
#Find all available package providers in PackageManagement azure blob store as well as in PowerShellGallery.com
Find-PackageProvider

#Find all versions of a provider
Find-PackageProvider -Name "Nuget" -AllVersions

#Find a provider from a specified source
Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"

#For machines without internet, you can download the nuget provider first, put it to you file share and then use the following to install the nuget provider (TP5 or later).

Find-PackageProvider -Source  C:\sharedfolder\Providers\
Install-PackageProvider -Source C:\sharedfolder\Providers\ -Name nuget -force
    
```

## <a name="get-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890704aspx"></a>[<span data-ttu-id="c335c-128">Get-Package Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c335c-128">Get-Package Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890704.aspx)
<span data-ttu-id="c335c-129">這個 Cmdlet 會傳回所有已使用 PackageManagement 安裝的軟體封裝清單。</span><span class="sxs-lookup"><span data-stu-id="c335c-129">This cmdlet returns a list of all software packages that have been installed using PackageManagement.</span></span>
```powershell
# Get all the packages installed by Programs provider
Get-Package –Provider Programs

# Get all the packages installed by NuGet provider at c:\test using the dynamic
# parameter destination
Get-Package –Provider NuGet -Destination c:\test
```

## <a name="get-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890703aspx"></a>[<span data-ttu-id="c335c-130">Get-PackageProvider Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c335c-130">Get-PackageProvider Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890703.aspx)
<span data-ttu-id="c335c-131">您可以使用 Cmdlet 清查本機電腦上已載入並準備使用的封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="c335c-131">Package providers that are loaded and ready to be used on the local machine can be inventoried by using the cmdlet.</span></span>
```powershell
# Get all currently loaded package providers
Get-PackageProvider

# The following cmdlet will show all the package providers available on the machine (including those that are not loaded):
Get-PackageProvider -ListAvailable
```

## <a name="get-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890705aspx"></a>[<span data-ttu-id="c335c-132">Get-PackageSource Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c335c-132">Get-PackageSource Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890705.aspx)
<span data-ttu-id="c335c-133">這個 Cmdlet 會取得封裝提供者註冊的封裝來源清單。</span><span class="sxs-lookup"><span data-stu-id="c335c-133">This cmdlet gets a list of package sources that are registered for a package provider.</span></span>
```powershelll
# Get all package sources
Get-PackageSource

# Get all package sources for a specific provider
Get-PackageSource –ProviderName PowerShellGet
```

## <a name="import-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarymt676545aspx"></a>[<span data-ttu-id="c335c-134">Import-PackageProvider Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c335c-134">Import-PackageProvider Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/mt676545.aspx)
<span data-ttu-id="c335c-135">這個 Cmdlet 會在目前的工作階段中加入封裝管理封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="c335c-135">This cmdlet adds Package Management package providers to the current session.</span></span>
```powershell
# Import a package provider from the local machine
Import-PackageProvider –Name MyProvider

#The -Name parameter can be either the name of the provider or the full path to the provider. Currently, we support .dll, .exe and.psm1 for the full path case. If the name of the provider is used for the -Name parameter, then additional version parameters such as -RequiredVersion, -MinimumVersion and -MaximumVersion may be specified. Otherwise, the latest version of the provider will be imported.

#If a package provider is not yet loaded to your system, we can discover and install on-demand. You can use explicit discovery and install cmdlets to do so:
 Find-PackageProvider
 Install-PackageProvider –Name MyProvider

#After installed, follow the Import-PackageProvider to load it to your system.

# Import a specific version of a package provider. PackageManagement supports installations of multiple versions of a package provider using PackageProvider cmdlets (not by bootstrapper provider). You can install another version of a package provider given that you already have one up running by:
Find-PackageProvider –Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force
Get-PackageProvider –ListAvailable
Import-PackageProvider –Name "Nuget" -RequiredVersion "2.8.5.201" -Verbose
Import-PackageProvider –Name MyProvider –RequiredVersion xxxx -force

As of the Windows Server Technical Preview(TP5), Install-PackageProvider does install as well as import the provider. Hence after you run find-packageprovider and install-packageprovider, the provider should be ready to use 
```

##<a name="-install-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890711aspx"></a>[<span data-ttu-id="c335c-136"> Install-Package Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c335c-136"> Install-Package Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890711.aspx)

<span data-ttu-id="c335c-137">這個 Cmdlet 可讓您使用載入的封裝提供者在可用的封裝來源中安裝軟體封裝。</span><span class="sxs-lookup"><span data-stu-id="c335c-137">This cmdlet allows installation of software packages in available package sources using loaded package providers.</span></span>
```powershell
# Install a package by name.
# NuGet provider requires us to provide the dynamic parameter destination path
# when we use this provider to install. Not all providers will require you to supply
# dynamic parameters for PackageManagement cmdlets.
Install-Package -Name jquery -Source nuget.org -Destination c:\test

# Install a package by piping.
Find-Package -Name jquery –Provider NuGet | Install-Package -Destination c:\test
```

## <a name="install-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarymt676543aspx"></a>[<span data-ttu-id="c335c-138">Install-PackageProvider Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c335c-138">Install-PackageProvider Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/mt676543.aspx)
<span data-ttu-id="c335c-139">這個 Cmdlet 會安裝一個或多個封裝管理封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="c335c-139">This cmdlet installs one or more Package Management package providers.</span></span>
```powershell
# Install a package provider from the PowerShell Gallery
Install-PackageProvider –Name "Gistprovider" -Verbose

# Install a specified version of a package provider
Find-PackageProvider –Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force

# Find a provider and install it
Find-PackageProvider –Name "Gistprovider" | Install-PackageProvider -Verbose

# Install a provider to the current user’s module folder
Install-PackageProvider –Name Gistprovider –Verbose –Scope CurrentUser
```

## <a name="register-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890701aspx"></a>[<span data-ttu-id="c335c-140">Register-PackageSource Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c335c-140">Register-PackageSource Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890701.aspx)
<span data-ttu-id="c335c-141">這個 Cmdlet 會加入指定封裝提供者的封裝來源。</span><span class="sxs-lookup"><span data-stu-id="c335c-141">This cmdlet adds a package source for a specified package provider.</span></span>
<span data-ttu-id="c335c-142">每個 PackageManagement 提供者都可能會有一個或多個軟體來源或是存放庫。</span><span class="sxs-lookup"><span data-stu-id="c335c-142">Each PackageManagement provider may have one or multiple software sources, or repositories.</span></span> <span data-ttu-id="c335c-143">PackageManagement 提供 PowerShell Cmdlet 來新增/移除/查詢來源。</span><span class="sxs-lookup"><span data-stu-id="c335c-143">PackageManagement provides PowerShell cmdlets to add/remove/query the source.</span></span> <span data-ttu-id="c335c-144">例如，您可以註冊 NuGet 提供者的封裝來源：</span><span class="sxs-lookup"><span data-stu-id="c335c-144">For example, you can register a package source for the NuGet provider:</span></span>
```powershell
Register-PackageSource -Name "NugetSource" -Location "http://www.nuget.org/api/v2" –ProviderName nuget
```

## <a name="save-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890708aspx"></a>[<span data-ttu-id="c335c-145">Save-Package Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c335c-145">Save-Package Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890708.aspx)
<span data-ttu-id="c335c-146">這個 Cmdlet 會將封裝儲存到本機電腦，而不加以安裝。</span><span class="sxs-lookup"><span data-stu-id="c335c-146">This cmdlet saves packages to the local computer without installing them.</span></span>
```powershell
# Saves jquery package to c:\test using NuGetProvider
# Notes that the -Path parameter must point to an existing location
Save-Package -Name jquery –Provider NuGet -Path c:\test

# Save a package by piping.
Find-Package -Name jquery -Source http://www.nuget.org/api/v2/ | Save-Package -Path c:\test
Find-Package -source c:\test
```

## <a name="set-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890710aspx"></a>[<span data-ttu-id="c335c-147">Set-PackageSource Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c335c-147">Set-PackageSource Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890710.aspx)
<span data-ttu-id="c335c-148">這個 Cmdlet 會變更現有封裝來源的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c335c-148">This cmdlet changes information about an existing package source.</span></span> 
```powershell
#Set-PackageSource changes the values for a source that has already been registered by running the Register-PackageSource cmdlet. By #running Set-PackageSource, you can change the source name and location.
Set-PackageSource  -Name nuget.org -Location  http://www.nuget.org/api/v2 -NewName nuget2 -NewLocation https://www.nuget.org/api/v2 
```

## <a name="uninstall-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890702aspx"></a>[<span data-ttu-id="c335c-149">Uninstall-Package Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c335c-149">Uninstall-Package Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890702.aspx)
<span data-ttu-id="c335c-150">這個 Cmdlet 會解除安裝本機電腦上安裝的封裝。</span><span class="sxs-lookup"><span data-stu-id="c335c-150">This cmdlet uninstalls packages installed on the local computer.</span></span>
```powershell
# Uninstall jquery using nuget
Uninstall-Package -Name jquery –Provider NuGet -Destination c:\test

# Uninstall a package with by piping with Get-Package
Get-Package -Name jquery –Provider NuGet -Destination c:\test | Uninstall-Package
```

## <a name="unregister-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890707aspx"></a>[<span data-ttu-id="c335c-151">Unregister-PackageSource Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c335c-151">Unregister-PackageSource Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890707.aspx)
```powershell
# Unregister a package source for the NuGet provider. You can use command Unregister-PackageSource, to disconnect with a repository, and Get-PackageSource, to discover what the repositories are associated with that provider.
Unregister-PackageSource  -Name "NugetSource"
```

