---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_gettingstarted
ms.openlocfilehash: 2117712b0081db4a21f8480b458a499ed84dc512
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="get-started-with-the-powershell-gallery"></a><span data-ttu-id="c470d-103">開始使用 PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="c470d-103">Get Started with the PowerShell Gallery</span></span>

## <a name="what-is-the-powershell-gallery"></a><span data-ttu-id="c470d-104">什麼是 PowerShell Gallery？</span><span class="sxs-lookup"><span data-stu-id="c470d-104">What is the PowerShell Gallery?</span></span>

<span data-ttu-id="c470d-105">PowerShell 資源庫是 PowerShell 內容的集中存放庫。</span><span class="sxs-lookup"><span data-stu-id="c470d-105">The PowerShell Gallery is the central repository for PowerShell content.</span></span>
<span data-ttu-id="c470d-106">您可以在其中找到包含 PowerShell 命令或預期狀態設定 (DSC) 資源的有用 PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="c470d-106">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span> <span data-ttu-id="c470d-107">您也可以尋找 PowerShell 指令碼，其中有些可能會包含 PowerShell 工作流程，有些則概述一組工作並提供這些工作的序列。</span><span class="sxs-lookup"><span data-stu-id="c470d-107">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span>
<span data-ttu-id="c470d-108">這些項目有一部分是由 Microsoft 所撰寫，其他則是由 PowerShell 社群所撰寫。</span><span class="sxs-lookup"><span data-stu-id="c470d-108">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="requirements"></a><span data-ttu-id="c470d-109">需求</span><span class="sxs-lookup"><span data-stu-id="c470d-109">Requirements</span></span>

<span data-ttu-id="c470d-110">將項目從 PowerShell Gallery 下載至系統時，需要 [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 模組。</span><span class="sxs-lookup"><span data-stu-id="c470d-110">Downloading items from the PowerShell Gallery to your system requires the [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) module.</span></span> <span data-ttu-id="c470d-111">您可以在下列任何一項中尋找 PowerShellGet 模組。</span><span class="sxs-lookup"><span data-stu-id="c470d-111">You can find the PowerShellGet module in any of the following.</span></span> <span data-ttu-id="c470d-112">您不需要登入，就可以從 PowerShell Gallery 下載項目。</span><span class="sxs-lookup"><span data-stu-id="c470d-112">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

-   [<span data-ttu-id="c470d-113">Windows 10</span><span class="sxs-lookup"><span data-stu-id="c470d-113">Windows 10</span></span>](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409)
-   [<span data-ttu-id="c470d-114">Windows Management Framework 5.0</span><span class="sxs-lookup"><span data-stu-id="c470d-114">Windows Management Framework 5.0</span></span>](http://go.microsoft.com/fwlink/?LinkId=398175)
-   [<span data-ttu-id="c470d-115">MSI Installer (適用於 PowerShell 3 和 4)</span><span class="sxs-lookup"><span data-stu-id="c470d-115">MSI Installer (for PowerShell 3 and 4)</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

<span data-ttu-id="c470d-116">PowerShellGet 也需要 [NuGet 提供者](http://go.microsoft.com/fwlink/?LinkId=722208)，才能處理 PowerShell Gallery。</span><span class="sxs-lookup"><span data-stu-id="c470d-116">PowerShellGet also requires the [NuGet provider](http://go.microsoft.com/fwlink/?LinkId=722208) to work with the PowerShell Gallery.</span></span> <span data-ttu-id="c470d-117">如果 NuGet 提供者不在下列其中一個位置中，則系統會在第一次使用 PowerShellGet 時提示您安裝 NuGet 提供者：</span><span class="sxs-lookup"><span data-stu-id="c470d-117">You will be prompted to install the NuGet provider automatically upon first use of PowerShellGet if the NuGet provider is not in one of the following locations:</span></span>

- `$env:ProgramFiles\PackageManagement\ProviderAssemblies`
- `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies`

<span data-ttu-id="c470d-118">或者，您可以執行 `Install-PackageProvider -Name NuGet -Force` 來自動下載和安裝 NuGet 提供者。</span><span class="sxs-lookup"><span data-stu-id="c470d-118">Or, you can run `Install-PackageProvider -Name NuGet -Force` to automate the download and installation of the NuGet provider.</span></span>

  
<span data-ttu-id="c470d-119">如果您的版本比 NuGet 2.8.5.201 還要舊，則需要呼叫下列 PowerShell Cmdlet 來安裝並切換至最新版本的 NuGet。</span><span class="sxs-lookup"><span data-stu-id="c470d-119">If you have a version older than 2.8.5.201 of NuGet, you will need to call the following PowerShell cmdlets to install and switch to the latest version of NuGet.</span></span>

1.  `Install-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force`
2.  `Import-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force`
3.  <span data-ttu-id="c470d-120">從上述安裝的位置中，刪除舊版本的 NuGet。</span><span class="sxs-lookup"><span data-stu-id="c470d-120">Delete the older version of NuGet from the above installed location.</span></span>

<span data-ttu-id="c470d-121">如需詳細資訊，請參閱 <http://oneget.org/>。</span><span class="sxs-lookup"><span data-stu-id="c470d-121">For more information, see <http://oneget.org/> .</span></span>

  
<span data-ttu-id="c470d-122">注意︰因為封裝格式變更，所以建議您更新至最新版本的 PowerShellGet 和 PackageManagement，以安裝最近更新過的項目。</span><span class="sxs-lookup"><span data-stu-id="c470d-122">Note: Due to changes in packaging formats, we recommend you update to the latest version of PowerShellGet and PackageManagement to install items that have been updated recently.</span></span> <span data-ttu-id="c470d-123">PowerShellGet 包含可在[這裡](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409)進一步了解的 Windows 10 中。</span><span class="sxs-lookup"><span data-stu-id="c470d-123">PowerShellGet is included in Windows 10, which you can learn more about [here](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409).</span></span>
<span data-ttu-id="c470d-124">PowerShellGet 也是可在[這裡](http://go.microsoft.com/fwlink/?LinkId=398175)下載之 Windows Management Framework (WMF) 5.0 的一部分。</span><span class="sxs-lookup"><span data-stu-id="c470d-124">PowerShellGet is also part of the Windows Management Framework (WMF) 5.0, which you can download [here](http://go.microsoft.com/fwlink/?LinkId=398175).</span></span>

## <a name="discovering-items-from-the-powershell-gallery"></a><span data-ttu-id="c470d-125">探索 PowerShell Gallery 中的項目</span><span class="sxs-lookup"><span data-stu-id="c470d-125">Discovering items from the PowerShell Gallery</span></span>

<span data-ttu-id="c470d-126">在這個網站上使用 **Search** 控制項，或瀏覽 [模組] 和 [指令碼] 頁面，即可尋找 PowerShell Gallery 中的項目。</span><span class="sxs-lookup"><span data-stu-id="c470d-126">You can find items in the PowerShell Gallery by using the **Search** control on this website, or by browsing through the Modules and Scripts pages.</span></span> <span data-ttu-id="c470d-127">您也可以執行 [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) 與 [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322) Cmdlet (視項目類型而定) 並搭配 `-Repository PSGallery`，以尋找 PowerShell 資源庫中的項目。</span><span class="sxs-lookup"><span data-stu-id="c470d-127">You can also find items from the PowerShell Gallery by running the [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) and [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322) cmdlets, depending on the item type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="c470d-128">使用下列 [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) 和 [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322) 參數，即可篩選 Gallery 中的結果。</span><span class="sxs-lookup"><span data-stu-id="c470d-128">Filtering results from the Gallery can be done by using the following parameters of [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) and [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322)</span></span>

- <span data-ttu-id="c470d-129">名稱</span><span class="sxs-lookup"><span data-stu-id="c470d-129">Name</span></span>
- <span data-ttu-id="c470d-130">AllVersions</span><span class="sxs-lookup"><span data-stu-id="c470d-130">AllVersions</span></span>
- <span data-ttu-id="c470d-131">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="c470d-131">MinimumVersion</span></span>
- <span data-ttu-id="c470d-132">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="c470d-132">RequiredVersion</span></span>
- <span data-ttu-id="c470d-133">標籤</span><span class="sxs-lookup"><span data-stu-id="c470d-133">Tag</span></span>
- <span data-ttu-id="c470d-134">Includes</span><span class="sxs-lookup"><span data-stu-id="c470d-134">Includes</span></span>
- <span data-ttu-id="c470d-135">DscResource</span><span class="sxs-lookup"><span data-stu-id="c470d-135">DscResource</span></span>
- <span data-ttu-id="c470d-136">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="c470d-136">RoleCapability</span></span>
- <span data-ttu-id="c470d-137">命令</span><span class="sxs-lookup"><span data-stu-id="c470d-137">Command</span></span>
- <span data-ttu-id="c470d-138">篩選器</span><span class="sxs-lookup"><span data-stu-id="c470d-138">Filter</span></span>

<span data-ttu-id="c470d-139">如果您只想要探索資源庫中的特定 DSC 資源，則可以執行 [Find-DscResource](https://go.microsoft.com/fwlink/?LinkId=517196) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c470d-139">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [Find-DscResource](https://go.microsoft.com/fwlink/?LinkId=517196) cmdlet.</span></span>
<span data-ttu-id="c470d-140">[Find-DscResource](https://go.microsoft.com/fwlink/?LinkId=517196) 會傳回資源庫中所含 DSC 資源的資料。</span><span class="sxs-lookup"><span data-stu-id="c470d-140">[Find-DscResource](https://go.microsoft.com/fwlink/?LinkId=517196) returns data on DSC resources contained in the Gallery.</span></span> <span data-ttu-id="c470d-141">因為 DSC 資源一律傳遞為模組的一部分，所以您仍然需要執行 [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) 來安裝這些 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="c470d-141">Because DSC resources are always delivered as part of a module, you still need to run [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) to install those DSC resources.</span></span>

## <a name="learning-about-items-in-the-powershell-gallery"></a><span data-ttu-id="c470d-142">了解 PowerShell Gallery 中的項目</span><span class="sxs-lookup"><span data-stu-id="c470d-142">Learning about items in the PowerShell Gallery</span></span>

<span data-ttu-id="c470d-143">在您識別到感興趣的項目之後，可能會想要深入了解。</span><span class="sxs-lookup"><span data-stu-id="c470d-143">Once you've identified an item you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="c470d-144">做法是檢查 Galler 上項目的特定頁面。</span><span class="sxs-lookup"><span data-stu-id="c470d-144">You can do this by examining that item's specific page on the Gallery.</span></span> <span data-ttu-id="c470d-145">在該頁面上，您可以看到所有與項目一起上傳的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c470d-145">On that page, you'll be able to see all of the metadata uploaded with the item.</span></span> <span data-ttu-id="c470d-146">項目的這個中繼資料是由項目作者所提供，未經 Microsoft 驗證。</span><span class="sxs-lookup"><span data-stu-id="c470d-146">This metadata for an item is provided by the item's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="c470d-147">項目的 [擁有者] 與用來發行項目的 Gallery 帳戶緊密連結，而且比 [作者] 欄位更為可靠。</span><span class="sxs-lookup"><span data-stu-id="c470d-147">The Owner of the item is strongly tied to the Gallery account used to publish the item, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="c470d-148">如果您發現可能未以誠信方式發行的項目，請按一下該項目之頁面上的 [檢舉不當使用]。</span><span class="sxs-lookup"><span data-stu-id="c470d-148">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

<span data-ttu-id="c470d-149">如果您是執行 [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) 或 [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322)，則可以在所傳回的 PSGetModuleInfo 物件中檢視這個資料。</span><span class="sxs-lookup"><span data-stu-id="c470d-149">If you're running [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) or [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322), you can view this data in the returned PSGetModuleInfo object.</span></span>
<span data-ttu-id="c470d-150">例如，執行 `Find-Module -Name PSReadLine -Repository PSGallery | Get-Member` 可傳回資源庫中 PSReadLine 模組的資料。</span><span class="sxs-lookup"><span data-stu-id="c470d-150">For example, running `Find-Module -Name PSReadLine -Repository PSGallery | Get-Member` returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-items-from-the-powershell-gallery"></a><span data-ttu-id="c470d-151">從 PowerShell Gallery 下載項目</span><span class="sxs-lookup"><span data-stu-id="c470d-151">Downloading items from the PowerShell Gallery</span></span>

<span data-ttu-id="c470d-152">從 PowerShell Gallery 下載項目時，建議使用下列程序︰</span><span class="sxs-lookup"><span data-stu-id="c470d-152">We encourage the following process when downloading items from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="c470d-153">檢查</span><span class="sxs-lookup"><span data-stu-id="c470d-153">Inspect</span></span>

<span data-ttu-id="c470d-154">若要下載資源庫中的項目來進行檢查，請執行 [Save-Module](https://go.microsoft.com/fwlink/?LinkId=821669) 或 [Save-Script](https://go.microsoft.com/fwlink/?LinkId=822334) Cmdlet (視項目類型而定)。</span><span class="sxs-lookup"><span data-stu-id="c470d-154">To download an item from the Gallery for inspection, run either the [Save-Module](https://go.microsoft.com/fwlink/?LinkId=821669) or [Save-Script](https://go.microsoft.com/fwlink/?LinkId=822334) cmdlet, depending on the item type.</span></span> <span data-ttu-id="c470d-155">這可讓您在本機儲存項目，而不需要安裝它，並且檢查項目內容。</span><span class="sxs-lookup"><span data-stu-id="c470d-155">This lets you save the item locally without installing it, and inspect the item contents.</span></span> <span data-ttu-id="c470d-156">請記得手動刪除儲存的項目。</span><span class="sxs-lookup"><span data-stu-id="c470d-156">Remember to delete the saved item manually.</span></span>

<span data-ttu-id="c470d-157">這些項目有一部分是由 Microsoft 所撰寫，其他則是由 PowerShell 社群所撰寫。</span><span class="sxs-lookup"><span data-stu-id="c470d-157">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span> <span data-ttu-id="c470d-158">Microsoft 建議您檢閱這個組件庫上項目的內容和程式碼，再進行安裝。</span><span class="sxs-lookup"><span data-stu-id="c470d-158">Microsoft recommends that you review the contents and code of items on this gallery prior to installation.</span></span>

<span data-ttu-id="c470d-159">如果您發現可能未以誠信方式發行的項目，請按一下該項目之頁面上的 [檢舉不當使用]。</span><span class="sxs-lookup"><span data-stu-id="c470d-159">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

### <a name="install"></a><span data-ttu-id="c470d-160">安裝</span><span class="sxs-lookup"><span data-stu-id="c470d-160">Install</span></span>

<span data-ttu-id="c470d-161">若要安裝資源庫中的項目來進行使用，請執行 [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) 或 [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327) Cmdlet (視項目類型而定)。</span><span class="sxs-lookup"><span data-stu-id="c470d-161">To install an item from the Gallery for use, run either the [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) or [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327) cmdlet, depending on the item type.</span></span>

<span data-ttu-id="c470d-162">[Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) 預設會將模組安裝至 `$env:ProgramFiles\WindowsPowerShell\Modules`。</span><span class="sxs-lookup"><span data-stu-id="c470d-162">[Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span> <span data-ttu-id="c470d-163">這需要系統管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="c470d-163">This requires an administrator account.</span></span> <span data-ttu-id="c470d-164">如果您新增 `-Scope
CurrentUser` 參數，模組就會安裝至 `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`。</span><span class="sxs-lookup"><span data-stu-id="c470d-164">If you add the `-Scope
CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="c470d-165">[Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327) 預設會將指令碼安裝至 `$env:ProgramFiles\WindowsPowerShell\Scripts`。</span><span class="sxs-lookup"><span data-stu-id="c470d-165">[Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327) installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span> <span data-ttu-id="c470d-166">這需要系統管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="c470d-166">This requires an administrator account.</span></span> <span data-ttu-id="c470d-167">如果您新增 `-Scope
CurrentUser` 參數，指令碼就會安裝至 `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`。</span><span class="sxs-lookup"><span data-stu-id="c470d-167">If you add the `-Scope
CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="c470d-168">[Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) 和 [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327) 預設會安裝項目的最新版本。</span><span class="sxs-lookup"><span data-stu-id="c470d-168">By default, [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) and [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327) installs the most current version of an item.</span></span> <span data-ttu-id="c470d-169">若要安裝項目的舊版本，請新增 `-RequiredVersion` 參數。</span><span class="sxs-lookup"><span data-stu-id="c470d-169">To install an older version of the item, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="c470d-170">在客體叢集部署</span><span class="sxs-lookup"><span data-stu-id="c470d-170">Deploy</span></span>

<span data-ttu-id="c470d-171">若要將項目從 PowerShell Gallery 部署至 Azure 自動化，請按一下項目詳細資料頁面上的 [Deploy to Azure Automation] \(部署至 Azure 自動化)。</span><span class="sxs-lookup"><span data-stu-id="c470d-171">To deploy an item from the PowerShell Gallery to Azure Automation, click **Deploy to Azure Automation** on the item details page.</span></span> <span data-ttu-id="c470d-172">會將您重新導向至使用 Azure 帳戶認證所登入的 Azure 管理入口網站。</span><span class="sxs-lookup"><span data-stu-id="c470d-172">You will be redirected to the Azure Management Portal, where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="c470d-173">請注意，部署包含相依性的項目時會將所有相依性部署至 Azure 自動化。</span><span class="sxs-lookup"><span data-stu-id="c470d-173">Note that deploying items with dependencies will deploy all the dependencies to Azure Automation.</span></span> <span data-ttu-id="c470d-174">將 **AzureAutomationNotSupported** 標記新增至項目中繼資料，即可停用 [Deploy to Azure Automation] \(部署至 Azure 自動化) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c470d-174">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your item metadata.</span></span>

<span data-ttu-id="c470d-175">若要深入了解 Azure 自動化，請參閱 [Azure 自動化網站](http://azure.microsoft.com/services/automation/)。</span><span class="sxs-lookup"><span data-stu-id="c470d-175">To learn more about Azure Automation, see the [Azure Automation website](http://azure.microsoft.com/services/automation/).</span></span>

## <a name="updating-items-from-the-powershell-gallery"></a><span data-ttu-id="c470d-176">更新 PowerShell Gallery 中的項目</span><span class="sxs-lookup"><span data-stu-id="c470d-176">Updating items from the PowerShell Gallery</span></span>

<span data-ttu-id="c470d-177">若要更新從 PowerShell Gallery 安裝的項目，請執行 [Update-Module](https://go.microsoft.com/fwlink/?LinkID=398576) 或 [Update-Script](http://go.microsoft.com/fwlink/?LinkId=619787) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c470d-177">To update items installed from the PowerShell Gallery, run either the [Update-Module](https://go.microsoft.com/fwlink/?LinkID=398576) or [Update-Script](http://go.microsoft.com/fwlink/?LinkId=619787) cmdlet.</span></span> <span data-ttu-id="c470d-178">如果執行時未包含任何其他參數，則 [Update-Module](https://go.microsoft.com/fwlink/?LinkID=398576) 會嘗試更新透過執行 [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) 所安裝的每個模組。</span><span class="sxs-lookup"><span data-stu-id="c470d-178">When run without any additional parameters, [Update-Module](https://go.microsoft.com/fwlink/?LinkID=398576) attempts to update each module installed by running [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663).</span></span>
<span data-ttu-id="c470d-179">若要選擇性地更新模組，請新增 `-Name` 參數。</span><span class="sxs-lookup"><span data-stu-id="c470d-179">To selectively update modules, add the `-Name` parameter.</span></span>

<span data-ttu-id="c470d-180">同樣地，如果執行時未包含任何其他參數，則 [Update-Script](http://go.microsoft.com/fwlink/?LinkId=619787) 也會嘗試更新透過執行 [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327) 所安裝的每個指令碼。</span><span class="sxs-lookup"><span data-stu-id="c470d-180">Similarly, when run without any additional parameters, [Update-Script](http://go.microsoft.com/fwlink/?LinkId=619787) also attempts to update each script installed by running [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327).</span></span>
<span data-ttu-id="c470d-181">若要選擇性地更新指令碼，請新增 `-Name` 參數。</span><span class="sxs-lookup"><span data-stu-id="c470d-181">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="c470d-182">列出您已從 PowerShell Gallery 安裝的項目</span><span class="sxs-lookup"><span data-stu-id="c470d-182">List items that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="c470d-183">若要找出您已從 PowerShell 資源庫安裝的模組，請執行 [Get-InstalledModule](https://go.microsoft.com/fwlink/?LinkId=526863) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c470d-183">To find out which modules you have installed from the PowerShell Gallery, run the [Get-InstalledModule](https://go.microsoft.com/fwlink/?LinkId=526863) cmdlet.</span></span> <span data-ttu-id="c470d-184">這個命令會列出系統上直接從 PowerShell Gallery 安裝的所有模組。</span><span class="sxs-lookup"><span data-stu-id="c470d-184">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="c470d-185">同樣地，若要找出您已從 PowerShell 資源庫安裝的指令碼，請執行 [Get-InstalledScript](https://go.microsoft.com/fwlink/?LinkId=619790) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c470d-185">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [Get-InstalledScript](https://go.microsoft.com/fwlink/?LinkId=619790) cmdlet.</span></span> <span data-ttu-id="c470d-186">這個命令會列出系統上直接從 PowerShell Gallery 安裝的所有指令碼。</span><span class="sxs-lookup"><span data-stu-id="c470d-186">This command lists all of the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>

