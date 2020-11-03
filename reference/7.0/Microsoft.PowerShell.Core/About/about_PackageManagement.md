---
description: PackageManagement 是軟體套件管理員的匯總工具。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_packagemanagement?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PackageManagement
ms.openlocfilehash: 5b4b42dfce03831da5cc317276e78e0777ff73d6
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208192"
---
# <a name="about-packagemanagement"></a><span data-ttu-id="bb256-104">關於 PackageManagement</span><span class="sxs-lookup"><span data-stu-id="bb256-104">About PackageManagement</span></span>

## <a name="short-description"></a><span data-ttu-id="bb256-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="bb256-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="bb256-106">PackageManagement 是軟體套件管理員的匯總工具。</span><span class="sxs-lookup"><span data-stu-id="bb256-106">PackageManagement is an aggregator for software package managers.</span></span>

## <a name="long-description"></a><span data-ttu-id="bb256-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="bb256-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="bb256-108">PackageManagement 功能已在 Windows PowerShell 5.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="bb256-108">PackageManagement functionality was introduced in Windows PowerShell 5.0.</span></span>

<span data-ttu-id="bb256-109">PackageManagement 是軟體套件管理系統的整合介面;您可以執行 PackageManagement Cmdlet 來執行軟體探索、安裝和清查 (SDII) 工作。</span><span class="sxs-lookup"><span data-stu-id="bb256-109">PackageManagement is a unified interface for software package management systems; you can run PackageManagement cmdlets to perform software discovery, installation, and inventory (SDII) tasks.</span></span> <span data-ttu-id="bb256-110">無論基礎安裝技術為何，您都可以在 PackageManagement 模組中執行通用 Cmdlet 來搜尋、安裝或卸載套件。新增、移除和查詢套件存放庫;並在電腦上執行查詢，以判斷安裝了哪些軟體套件。</span><span class="sxs-lookup"><span data-stu-id="bb256-110">Regardless of the underlying installation technology, you can run the common cmdlets in the PackageManagement module to search for, install, or uninstall packages; add, remove, and query package repositories; and run queries on a computer to determine which software packages are installed.</span></span>

<span data-ttu-id="bb256-111">PackageManagement 支援彈性的外掛程式模型，可支援其他軟體套件管理系統。</span><span class="sxs-lookup"><span data-stu-id="bb256-111">PackageManagement supports a flexible plug-in model that enables support for other software package management systems.</span></span>

<span data-ttu-id="bb256-112">PackageManagement 模組隨附于 Windows PowerShell 5.0 和更新版本的 PowerShell，並可在封裝管理結構的三個層級上運作：套件提供者、套件來源和套件本身。</span><span class="sxs-lookup"><span data-stu-id="bb256-112">The PackageManagement module is included with Windows PowerShell 5.0 and later releases of PowerShell, and works on three levels of package management structure: package providers, package sources, and the packages themselves.</span></span> <span data-ttu-id="bb256-113">讓我們定義一些詞彙：</span><span class="sxs-lookup"><span data-stu-id="bb256-113">Let us define some terms:</span></span>

- <span data-ttu-id="bb256-114">封裝管理員：軟體套件管理系統。</span><span class="sxs-lookup"><span data-stu-id="bb256-114">Package manager: Software package management system.</span></span> <span data-ttu-id="bb256-115">在 PackageManagement 方面，這是封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="bb256-115">In PackageManagement terms, this is a package provider.</span></span>
- <span data-ttu-id="bb256-116">封裝提供者：適用于封裝管理員的 PackageManagement 詞彙。</span><span class="sxs-lookup"><span data-stu-id="bb256-116">Package provider: PackageManagement term for a package manager.</span></span> <span data-ttu-id="bb256-117">範例可以包括 Windows Installer、Chocolatey 和其他專案。</span><span class="sxs-lookup"><span data-stu-id="bb256-117">Examples can include Windows Installer, Chocolatey, and others.</span></span>
- <span data-ttu-id="bb256-118">套件來源：您設定套件提供者作為存放庫使用的 URL、本機資料夾或網路共用資料夾。</span><span class="sxs-lookup"><span data-stu-id="bb256-118">Package source: A URL, local folder, or network shared folder that you configure package providers to use as a repository.</span></span>
- <span data-ttu-id="bb256-119">封裝：套件提供者所管理的軟體，並儲存在特定套件來源中。</span><span class="sxs-lookup"><span data-stu-id="bb256-119">Package: A piece of software that a package provider manages, and that is stored in a specific package source.</span></span>

<span data-ttu-id="bb256-120">PackageManagement 模組包含下列 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bb256-120">The PackageManagement module includes the following cmdlets.</span></span> <span data-ttu-id="bb256-121">如需詳細資訊，請參閱 [PackageManagement](/powershell/module/packagemanagement) 說明。</span><span class="sxs-lookup"><span data-stu-id="bb256-121">For more information, see the [PackageManagement](/powershell/module/packagemanagement) help.</span></span>

- <span data-ttu-id="bb256-122">`Get-PackageProvider`：傳回連接至 PackageManagement 的封裝提供者清單。</span><span class="sxs-lookup"><span data-stu-id="bb256-122">`Get-PackageProvider`: Returns a list of package providers that are  connected to PackageManagement.</span></span>
- <span data-ttu-id="bb256-123">`Get-PackageSource`：取得為封裝提供者註冊的封裝來源清單。</span><span class="sxs-lookup"><span data-stu-id="bb256-123">`Get-PackageSource`: Gets a list of package sources that are registered for a package provider.</span></span>
- <span data-ttu-id="bb256-124">`Register-PackageSource`：加入指定封裝提供者的封裝來源。</span><span class="sxs-lookup"><span data-stu-id="bb256-124">`Register-PackageSource`: Adds a package source for a specified package provider.</span></span>
- <span data-ttu-id="bb256-125">`Set-PackageSource`：設定現有封裝來源的屬性。</span><span class="sxs-lookup"><span data-stu-id="bb256-125">`Set-PackageSource`: Sets properties on an existing package source.</span></span>
- <span data-ttu-id="bb256-126">`Unregister-PackageSource`：移除已註冊的套件來源。</span><span class="sxs-lookup"><span data-stu-id="bb256-126">`Unregister-PackageSource`: Removes a registered package source.</span></span>
- <span data-ttu-id="bb256-127">`Get-Package`：傳回已安裝之軟體套件的清單。</span><span class="sxs-lookup"><span data-stu-id="bb256-127">`Get-Package`: Returns a list of installed software packages.</span></span>
- <span data-ttu-id="bb256-128">`Find-Package`：尋找可用套件來源中的軟體套件。</span><span class="sxs-lookup"><span data-stu-id="bb256-128">`Find-Package`: Finds software packages in available package sources.</span></span>
- <span data-ttu-id="bb256-129">`Install-Package`：安裝一或多個軟體套件。</span><span class="sxs-lookup"><span data-stu-id="bb256-129">`Install-Package`: Installs one or more software packages.</span></span>
- <span data-ttu-id="bb256-130">`Save-Package`：將封裝儲存至本機電腦，而不進行安裝。</span><span class="sxs-lookup"><span data-stu-id="bb256-130">`Save-Package`: Saves packages to the local computer without installing them.</span></span>
- <span data-ttu-id="bb256-131">`Uninstall-Package`：卸載一或多個軟體套件。</span><span class="sxs-lookup"><span data-stu-id="bb256-131">`Uninstall-Package`: Uninstalls one or more software packages.</span></span>

### <a name="package-provider-bootstrapping-and-dynamic-cmdlet-parameters"></a><span data-ttu-id="bb256-132">套件提供者啟動載入和動態 Cmdlet 參數</span><span class="sxs-lookup"><span data-stu-id="bb256-132">Package Provider Bootstrapping and Dynamic Cmdlet Parameters</span></span>

<span data-ttu-id="bb256-133">根據預設，PackageManagement 會隨附核心啟動提供者。</span><span class="sxs-lookup"><span data-stu-id="bb256-133">By default, PackageManagement ships with a core bootstrap provider.</span></span> <span data-ttu-id="bb256-134">您可以藉由啟動提供者，以依需要安裝其他套件提供者;也就是，回應從 web 服務自動安裝提供者的提示。</span><span class="sxs-lookup"><span data-stu-id="bb256-134">You can install additional package providers as you need them by bootstrapping the providers; that is, responding to a prompt to install the provider automatically, from a web service.</span></span> <span data-ttu-id="bb256-135">您可以使用任何 PackageManagement Cmdlet 指定封裝提供者;如果指定的提供者無法使用，PackageManagement 會提示您啟動 (，或自動安裝) 提供者。</span><span class="sxs-lookup"><span data-stu-id="bb256-135">You can specify a package provider with any PackageManagement cmdlet; if the specified provider is not available, PackageManagement prompts you to bootstrap (or automatically install) the provider.</span></span> <span data-ttu-id="bb256-136">在下列範例中，如果尚未安裝 Chocolatey 提供者，PackageManagement 啟動程式會安裝提供者。</span><span class="sxs-lookup"><span data-stu-id="bb256-136">In the following examples, if the Chocolatey provider is not already installed, PackageManagement bootstrapping installs the provider.</span></span>

```powershell
Find-Package -Provider Chocolatey <PackageName>
```

<span data-ttu-id="bb256-137">如果尚未安裝 Chocolatey 提供者，當您執行上述命令時，系統會提示您安裝它。</span><span class="sxs-lookup"><span data-stu-id="bb256-137">If the Chocolatey provider is not already installed, when you run the preceding command, you are prompted to install it.</span></span>

```powershell
Install-Package <Chocolatey package Name> -ForceBootstrap
```

<span data-ttu-id="bb256-138">如果尚未安裝 Chocolatey 提供者，則當您執行上述命令時，會安裝提供者;但因為 ForceBootstrap 參數已新增至命令，所以系統不會提示您安裝它。提供者和套件都會自動安裝。</span><span class="sxs-lookup"><span data-stu-id="bb256-138">If the Chocolatey provider is not already installed, when you run the preceding command, the provider is installed; but because the ForceBootstrap parameter has been added to the command, you are not prompted to install it; both the provider and the package are installed automatically.</span></span>

<span data-ttu-id="bb256-139">當您嘗試安裝套件時，如果尚未安裝支援提供者，而且您沒有將 ForceBootstrap 參數新增至命令，PackageManagement 會提示您安裝該提供者。</span><span class="sxs-lookup"><span data-stu-id="bb256-139">When you try to install a package, if you do not already have the supporting provider installed, and you do not add the ForceBootstrap parameter to your command, PackageManagement prompts you to install the provider.</span></span>

<span data-ttu-id="bb256-140">在 PackageManagement 命令中指定封裝提供者可以讓特定的動態參數提供給該封裝提供者使用。</span><span class="sxs-lookup"><span data-stu-id="bb256-140">Specifying a package provider in your PackageManagement command can make dynamic parameters available that are specific to that package provider.</span></span> <span data-ttu-id="bb256-141">當您針對特定 PackageManagement Cmdlet 執行 Get-Help 時，會傳回參數集清單，並將可用封裝提供者的動態參數群組在不同的參數集中。</span><span class="sxs-lookup"><span data-stu-id="bb256-141">When you run Get-Help for a specific PackageManagement cmdlet, a list of parameter sets are returned, grouping dynamic parameters for available package providers in separate parameter sets.</span></span>

<span data-ttu-id="bb256-142">PackageManagement 專案的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="bb256-142">More Information About the PackageManagement Project</span></span>

<span data-ttu-id="bb256-143">如需 PackageManagement open 開發專案的詳細資訊，包括如何建立 PackageManagement 套件提供者，請參閱 GitHub 上的 PackageManagement 專案 https://oneget.org 。</span><span class="sxs-lookup"><span data-stu-id="bb256-143">For more information about the PackageManagement open development project, including how to create a PackageManagement package provider, see the PackageManagement project on GitHub at https://oneget.org.</span></span>

## <a name="see-also"></a><span data-ttu-id="bb256-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb256-144">SEE ALSO</span></span>

[<span data-ttu-id="bb256-145">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="bb256-145">Get-PackageProvider</span></span>](xref:PackageManagement.Get-PackageProvider)

[<span data-ttu-id="bb256-146">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="bb256-146">Get-PackageSource</span></span>](xref:PackageManagement.Get-PackageSource)

[<span data-ttu-id="bb256-147">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="bb256-147">Register-PackageSource</span></span>](xref:PackageManagement.Register-PackageSource)

[<span data-ttu-id="bb256-148">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="bb256-148">Set-PackageSource</span></span>](xref:PackageManagement.Set-PackageSource)

[<span data-ttu-id="bb256-149">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="bb256-149">Unregister-PackageSource</span></span>](xref:PackageManagement.Unregister-PackageSource)

[<span data-ttu-id="bb256-150">Get-Package</span><span class="sxs-lookup"><span data-stu-id="bb256-150">Get-Package</span></span>](xref:PackageManagement.Get-Package)

[<span data-ttu-id="bb256-151">Find-Package</span><span class="sxs-lookup"><span data-stu-id="bb256-151">Find-Package</span></span>](xref:PackageManagement.Find-Package)

[<span data-ttu-id="bb256-152">Install-Package</span><span class="sxs-lookup"><span data-stu-id="bb256-152">Install-Package</span></span>](xref:PackageManagement.Install-Package)

[<span data-ttu-id="bb256-153">Save-Package</span><span class="sxs-lookup"><span data-stu-id="bb256-153">Save-Package</span></span>](xref:PackageManagement.Save-Package)

[<span data-ttu-id="bb256-154">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="bb256-154">Uninstall-Package</span></span>](xref:PackageManagement.Uninstall-Package)
