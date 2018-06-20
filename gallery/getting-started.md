---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 開始使用 PowerShell Gallery
ms.openlocfilehash: 83974698152e75efac66ea725a9c220486676d6f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190157"
---
# <a name="get-started-with-the-powershell-gallery"></a><span data-ttu-id="336c5-103">開始使用 PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="336c5-103">Get Started with the PowerShell Gallery</span></span>

<span data-ttu-id="336c5-104">將項目從 PowerShell Gallery 下載至系統時，需要 [PowerShellGet](/powershell/module/powershellget) 模組。</span><span class="sxs-lookup"><span data-stu-id="336c5-104">Downloading items from the PowerShell Gallery to your system requires the [PowerShellGet](/powershell/module/powershellget) module.</span></span> <span data-ttu-id="336c5-105">您可以在下列任何一項中尋找 PowerShellGet 模組。</span><span class="sxs-lookup"><span data-stu-id="336c5-105">You can find the PowerShellGet module in any of the following.</span></span> <span data-ttu-id="336c5-106">您不需要登入，就可以從 PowerShell Gallery 下載項目。</span><span class="sxs-lookup"><span data-stu-id="336c5-106">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

## <a name="discovering-items-from-the-powershell-gallery"></a><span data-ttu-id="336c5-107">探索 PowerShell Gallery 中的項目</span><span class="sxs-lookup"><span data-stu-id="336c5-107">Discovering items from the PowerShell Gallery</span></span>

<span data-ttu-id="336c5-108">在這個網站上使用 **Search** 控制項，或瀏覽 [模組] 和 [指令碼] 頁面，即可尋找 PowerShell Gallery 中的項目。</span><span class="sxs-lookup"><span data-stu-id="336c5-108">You can find items in the PowerShell Gallery by using the **Search** control on this website, or by browsing through the Modules and Scripts pages.</span></span> <span data-ttu-id="336c5-109">您也可以執行 [Find-Module][] 與 [Find-Script][] Cmdlet (視項目類型而定) 並搭配 `-Repository PSGallery`，以尋找 PowerShell 資源庫中的項目。</span><span class="sxs-lookup"><span data-stu-id="336c5-109">You can also find items from the PowerShell Gallery by running the [Find-Module][] and [Find-Script][] cmdlets, depending on the item type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="336c5-110">若要從資源庫篩選結果，可以使用下列參數：</span><span class="sxs-lookup"><span data-stu-id="336c5-110">Filtering results from the Gallery can be done by using the following parameters:</span></span>

- <span data-ttu-id="336c5-111">名稱</span><span class="sxs-lookup"><span data-stu-id="336c5-111">Name</span></span>
- <span data-ttu-id="336c5-112">AllVersions</span><span class="sxs-lookup"><span data-stu-id="336c5-112">AllVersions</span></span>
- <span data-ttu-id="336c5-113">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="336c5-113">MinimumVersion</span></span>
- <span data-ttu-id="336c5-114">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="336c5-114">RequiredVersion</span></span>
- <span data-ttu-id="336c5-115">標籤</span><span class="sxs-lookup"><span data-stu-id="336c5-115">Tag</span></span>
- <span data-ttu-id="336c5-116">Includes</span><span class="sxs-lookup"><span data-stu-id="336c5-116">Includes</span></span>
- <span data-ttu-id="336c5-117">DscResource</span><span class="sxs-lookup"><span data-stu-id="336c5-117">DscResource</span></span>
- <span data-ttu-id="336c5-118">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="336c5-118">RoleCapability</span></span>
- <span data-ttu-id="336c5-119">命令</span><span class="sxs-lookup"><span data-stu-id="336c5-119">Command</span></span>
- <span data-ttu-id="336c5-120">篩選器</span><span class="sxs-lookup"><span data-stu-id="336c5-120">Filter</span></span>

<span data-ttu-id="336c5-121">如果您只想要探索資源庫中的特定 DSC 資源，則可以執行 [Find-DscResource] Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="336c5-121">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [Find-DscResource] cmdlet.</span></span> <span data-ttu-id="336c5-122">Find-DscResource 會傳回資源庫中所含 DSC 資源的資料。</span><span class="sxs-lookup"><span data-stu-id="336c5-122">Find-DscResource returns data on DSC resources contained in the Gallery.</span></span>
<span data-ttu-id="336c5-123">因為 DSC 資源一律傳遞為模組的一部分，所以您仍然需要執行 [Install-Module][] 來安裝這些 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="336c5-123">Because DSC resources are always delivered as part of a module, you still need to run [Install-Module][] to install those DSC resources.</span></span>

## <a name="learning-about-items-in-the-powershell-gallery"></a><span data-ttu-id="336c5-124">了解 PowerShell Gallery 中的項目</span><span class="sxs-lookup"><span data-stu-id="336c5-124">Learning about items in the PowerShell Gallery</span></span>

<span data-ttu-id="336c5-125">在您識別到感興趣的項目之後，可能會想要深入了解。</span><span class="sxs-lookup"><span data-stu-id="336c5-125">Once you've identified an item you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="336c5-126">做法是檢查 Galler 上項目的特定頁面。</span><span class="sxs-lookup"><span data-stu-id="336c5-126">You can do this by examining that item's specific page on the Gallery.</span></span> <span data-ttu-id="336c5-127">在該頁面上，您可以看到所有與項目一起上傳的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="336c5-127">On that page, you'll be able to see all of the metadata uploaded with the item.</span></span> <span data-ttu-id="336c5-128">項目的這個中繼資料是由項目作者所提供，未經 Microsoft 驗證。</span><span class="sxs-lookup"><span data-stu-id="336c5-128">This metadata for an item is provided by the item's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="336c5-129">項目的 [擁有者] 與用來發行項目的 Gallery 帳戶緊密連結，而且比 [作者] 欄位更為可靠。</span><span class="sxs-lookup"><span data-stu-id="336c5-129">The Owner of the item is strongly tied to the Gallery account used to publish the item, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="336c5-130">如果您發現可能未以誠信方式發行的項目，請按一下該項目之頁面上的 [檢舉不當使用]。</span><span class="sxs-lookup"><span data-stu-id="336c5-130">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

<span data-ttu-id="336c5-131">如果您是執行 [Find-Module][] 或 [Find-Script][]，則可以在所傳回的 PSGetModuleInfo 物件中檢視這個資料。</span><span class="sxs-lookup"><span data-stu-id="336c5-131">If you're running [Find-Module][] or [Find-Script][], you can view this data in the returned PSGetModuleInfo object.</span></span> <span data-ttu-id="336c5-132">例如，執行 `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member` 可傳回資源庫中 PSReadLine 模組的資料。</span><span class="sxs-lookup"><span data-stu-id="336c5-132">For example, running `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member` returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-items-from-the-powershell-gallery"></a><span data-ttu-id="336c5-133">從 PowerShell Gallery 下載項目</span><span class="sxs-lookup"><span data-stu-id="336c5-133">Downloading items from the PowerShell Gallery</span></span>

<span data-ttu-id="336c5-134">從 PowerShell Gallery 下載項目時，建議使用下列程序︰</span><span class="sxs-lookup"><span data-stu-id="336c5-134">We encourage the following process when downloading items from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="336c5-135">檢查</span><span class="sxs-lookup"><span data-stu-id="336c5-135">Inspect</span></span>

<span data-ttu-id="336c5-136">若要下載資源庫中的項目來進行檢查，請執行 [Save-Module][] 或 [Save-Script][] Cmdlet (視項目類型而定)。</span><span class="sxs-lookup"><span data-stu-id="336c5-136">To download an item from the Gallery for inspection, run either the [Save-Module][] or [Save-Script][] cmdlet, depending on the item type.</span></span> <span data-ttu-id="336c5-137">這可讓您在本機儲存項目，而不需要安裝它，並且檢查項目內容。</span><span class="sxs-lookup"><span data-stu-id="336c5-137">This lets you save the item locally without installing it, and inspect the item contents.</span></span> <span data-ttu-id="336c5-138">請記得手動刪除儲存的項目。</span><span class="sxs-lookup"><span data-stu-id="336c5-138">Remember to delete the saved item manually.</span></span>

<span data-ttu-id="336c5-139">這些項目有一部分是由 Microsoft 所撰寫，其他則是由 PowerShell 社群所撰寫。</span><span class="sxs-lookup"><span data-stu-id="336c5-139">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>
<span data-ttu-id="336c5-140">Microsoft 建議您檢閱這個組件庫上項目的內容和程式碼，再進行安裝。</span><span class="sxs-lookup"><span data-stu-id="336c5-140">Microsoft recommends that you review the contents and code of items on this gallery prior to installation.</span></span>

<span data-ttu-id="336c5-141">如果您發現可能未以誠信方式發行的項目，請按一下該項目之頁面上的 [檢舉不當使用]。</span><span class="sxs-lookup"><span data-stu-id="336c5-141">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

### <a name="install"></a><span data-ttu-id="336c5-142">安裝</span><span class="sxs-lookup"><span data-stu-id="336c5-142">Install</span></span>

<span data-ttu-id="336c5-143">若要安裝資源庫中的項目來進行使用，請執行 [Install-Module][] 或 [Install-Script][] Cmdlet (視項目類型而定)。</span><span class="sxs-lookup"><span data-stu-id="336c5-143">To install an item from the Gallery for use, run either the [Install-Module][] or [Install-Script][] cmdlet, depending on the item type.</span></span>

<span data-ttu-id="336c5-144">[Install-Module][] 預設會將模組安裝至 `$env:ProgramFiles\WindowsPowerShell\Modules`。</span><span class="sxs-lookup"><span data-stu-id="336c5-144">[Install-Module][] installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span>
<span data-ttu-id="336c5-145">這需要系統管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="336c5-145">This requires an administrator account.</span></span> <span data-ttu-id="336c5-146">如果您新增 `-Scope CurrentUser` 參數，模組就會安裝至 `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`。</span><span class="sxs-lookup"><span data-stu-id="336c5-146">If you add the `-Scope CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="336c5-147">[Install-Script][] 預設會將指令碼安裝至 `$env:ProgramFiles\WindowsPowerShell\Scripts`。</span><span class="sxs-lookup"><span data-stu-id="336c5-147">[Install-Script][] installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span>
<span data-ttu-id="336c5-148">這需要系統管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="336c5-148">This requires an administrator account.</span></span> <span data-ttu-id="336c5-149">如果您新增 `-Scope CurrentUser` 參數，指令碼就會安裝至 `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`。</span><span class="sxs-lookup"><span data-stu-id="336c5-149">If you add the `-Scope CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="336c5-150">[Install-Module][] 和 [Install-Script][] 預設會安裝項目的最新版本。</span><span class="sxs-lookup"><span data-stu-id="336c5-150">By default, [Install-Module][] and [Install-Script][] installs the most current version of an item.</span></span>
<span data-ttu-id="336c5-151">若要安裝項目的舊版本，請新增 `-RequiredVersion` 參數。</span><span class="sxs-lookup"><span data-stu-id="336c5-151">To install an older version of the item, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="336c5-152">在客體叢集部署</span><span class="sxs-lookup"><span data-stu-id="336c5-152">Deploy</span></span>

<span data-ttu-id="336c5-153">若要將項目從 PowerShell Gallery 部署至 Azure 自動化，請按一下項目詳細資料頁面上的 [Deploy to Azure Automation] \(部署至 Azure 自動化)。</span><span class="sxs-lookup"><span data-stu-id="336c5-153">To deploy an item from the PowerShell Gallery to Azure Automation, click **Deploy to Azure Automation** on the item details page.</span></span> <span data-ttu-id="336c5-154">會將您重新導向至使用 Azure 帳戶認證所登入的 Azure 管理入口網站。</span><span class="sxs-lookup"><span data-stu-id="336c5-154">You will be redirected to the Azure Management Portal, where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="336c5-155">請注意，部署包含相依性的項目時會將所有相依性部署至 Azure 自動化。</span><span class="sxs-lookup"><span data-stu-id="336c5-155">Note that deploying items with dependencies will deploy all the dependencies to Azure Automation.</span></span> <span data-ttu-id="336c5-156">將 **AzureAutomationNotSupported** 標記新增至項目中繼資料，即可停用 [Deploy to Azure Automation] \(部署至 Azure 自動化) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="336c5-156">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your item metadata.</span></span>

<span data-ttu-id="336c5-157">若要深入了解 Azure 自動化，請參閱 [Azure 自動化](/azure/automation)文件。</span><span class="sxs-lookup"><span data-stu-id="336c5-157">To learn more about Azure Automation, see the [Azure Automation](/azure/automation) documentation.</span></span>

## <a name="updating-items-from-the-powershell-gallery"></a><span data-ttu-id="336c5-158">更新 PowerShell Gallery 中的項目</span><span class="sxs-lookup"><span data-stu-id="336c5-158">Updating items from the PowerShell Gallery</span></span>

<span data-ttu-id="336c5-159">若要更新從「PowerShell 資源庫」安裝的項目，請執行 [Update-Module][] 或 [Update-Script][] Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="336c5-159">To update items installed from the PowerShell Gallery, run either the [Update-Module][] or [Update-Script][] cmdlet.</span></span> <span data-ttu-id="336c5-160">如果執行時未指定任何其他參數，[Update-Module][] 就會嘗試更新透過執行 [Install-Module][] 所安裝的每個模組。</span><span class="sxs-lookup"><span data-stu-id="336c5-160">When run without any additional parameters, [Update-Module][] attempts to update each module installed by running [Install-Module][].</span></span> <span data-ttu-id="336c5-161">若要選擇性地更新模組，請新增 `-Name` 參數。</span><span class="sxs-lookup"><span data-stu-id="336c5-161">To selectively update modules, add the `-Name` parameter.</span></span>

<span data-ttu-id="336c5-162">同樣地，如果執行時未指定任何其他參數，[Update-Script][] 也會嘗試更新透過執行 [Install-Script][] 所安裝的每個指令碼。</span><span class="sxs-lookup"><span data-stu-id="336c5-162">Similarly, when run without any additional parameters, [Update-Script][] also attempts to update each script installed by running [Install-Script][].</span></span> <span data-ttu-id="336c5-163">若要選擇性地更新指令碼，請新增 `-Name` 參數。</span><span class="sxs-lookup"><span data-stu-id="336c5-163">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="336c5-164">列出您已從 PowerShell Gallery 安裝的項目</span><span class="sxs-lookup"><span data-stu-id="336c5-164">List items that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="336c5-165">若要找出您已從 PowerShell 資源庫安裝的模組，請執行 [Get-InstalledModule][] Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="336c5-165">To find out which modules you have installed from the PowerShell Gallery, run the [Get-InstalledModule][] cmdlet.</span></span> <span data-ttu-id="336c5-166">這個命令會列出系統上直接從 PowerShell Gallery 安裝的所有模組。</span><span class="sxs-lookup"><span data-stu-id="336c5-166">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="336c5-167">同樣地，若要找出您已從 PowerShell 資源庫安裝的指令碼，請執行 [Get-InstalledScript][] Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="336c5-167">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [Get-InstalledScript][] cmdlet.</span></span> <span data-ttu-id="336c5-168">這個命令會列出系統上直接從 PowerShell Gallery 安裝的所有指令碼。</span><span class="sxs-lookup"><span data-stu-id="336c5-168">This command lists all of the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>

[Find-DscResource]: /powershell/module/powershellget/Find-DscResource
[Find-Module]: /powershell/module/powershellget/Find-Module
[Find-Script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[Install-Module]: /powershell/module/powershellget/Install-Module
[Install-Script]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[Save-Module]: /powershell/module/powershellget/Save-Module
[Save-Script]: /powershell/module/powershellget/Save-Script