---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 開始使用 PowerShell Gallery
ms.openlocfilehash: bae0af144e6f520142e7eaea3dd0e1039976dae4
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81219688"
---
# <a name="getting-started-with-the-powershell-gallery"></a><span data-ttu-id="c16cb-103">開始使用 PowerShell 資源庫</span><span class="sxs-lookup"><span data-stu-id="c16cb-103">Getting Started with the PowerShell Gallery</span></span>

<span data-ttu-id="c16cb-104">PowerShell 資源庫是一個套件存放庫，其中包含您可以下載並利用的指令碼、模組和 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="c16cb-104">The PowerShell Gallery is a package repository containing scripts, modules, and DSC resources you can download and leverage.</span></span> <span data-ttu-id="c16cb-105">您可以使用 [PowerShellGet](/powershell/module/powershellget) 模組中的 Cmdlet，從 PowerShell 資源庫安裝套件。</span><span class="sxs-lookup"><span data-stu-id="c16cb-105">You use the cmdlets in the [PowerShellGet](/powershell/module/powershellget) module to install packages from the PowerShell Gallery.</span></span> <span data-ttu-id="c16cb-106">您不需要登入，就可以從 PowerShell Gallery 下載項目。</span><span class="sxs-lookup"><span data-stu-id="c16cb-106">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="c16cb-107">您可以從 PowerShell 資源庫直接下載套件，但這不是建議的方法。</span><span class="sxs-lookup"><span data-stu-id="c16cb-107">It is possible to download a package from the PowerShell Gallery directly, but this is not a recommended approach.</span></span> <span data-ttu-id="c16cb-108">如需詳細資訊，請參閱[手動下載套件](how-to/working-with-packages/manual-download.md)。</span><span class="sxs-lookup"><span data-stu-id="c16cb-108">For more details, see [Manual Package Download](how-to/working-with-packages/manual-download.md).</span></span>

## <a name="discovering-packages-from-the-powershell-gallery"></a><span data-ttu-id="c16cb-109">從 PowerShell 資源庫探索套件</span><span class="sxs-lookup"><span data-stu-id="c16cb-109">Discovering packages from the PowerShell Gallery</span></span>

<span data-ttu-id="c16cb-110">您可以使用 PowerShell 資源庫[首頁](https://www.powershellgallery.com) \(英文\) 上的**搜尋**控制項，或從[套件頁面](https://www.powershellgallery.com/packages) \(英文\) 完整瀏覽模組和指令碼，藉以在 PowerShell 資源庫中尋找套件。</span><span class="sxs-lookup"><span data-stu-id="c16cb-110">You can find packages in the PowerShell Gallery by using the **Search** control on the PowerShell Gallery's [home page](https://www.powershellgallery.com), or by browsing through the Modules and Scripts from the [Packages page](https://www.powershellgallery.com/packages).</span></span> <span data-ttu-id="c16cb-111">您也可以搭配 `-Repository PSGallery` 執行 [Find-Module][]、[Find-DscResource] 及 [Find-Script][] Cmdlet (視套件類型而定)，來尋找 PowerShell 資源庫中的套件。</span><span class="sxs-lookup"><span data-stu-id="c16cb-111">You can also find packages from the PowerShell Gallery by running the [Find-Module][], [Find-DscResource], and [Find-Script][] cmdlets, depending on the package type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="c16cb-112">您可以使用下列參數，從資源庫中篩選結果：</span><span class="sxs-lookup"><span data-stu-id="c16cb-112">You can filter results from the Gallery by using the following parameters:</span></span>

- <span data-ttu-id="c16cb-113">名稱</span><span class="sxs-lookup"><span data-stu-id="c16cb-113">Name</span></span>
- <span data-ttu-id="c16cb-114">AllVersions</span><span class="sxs-lookup"><span data-stu-id="c16cb-114">AllVersions</span></span>
- <span data-ttu-id="c16cb-115">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="c16cb-115">MinimumVersion</span></span>
- <span data-ttu-id="c16cb-116">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="c16cb-116">RequiredVersion</span></span>
- <span data-ttu-id="c16cb-117">Tag</span><span class="sxs-lookup"><span data-stu-id="c16cb-117">Tag</span></span>
- <span data-ttu-id="c16cb-118">Includes</span><span class="sxs-lookup"><span data-stu-id="c16cb-118">Includes</span></span>
- <span data-ttu-id="c16cb-119">DscResource</span><span class="sxs-lookup"><span data-stu-id="c16cb-119">DscResource</span></span>
- <span data-ttu-id="c16cb-120">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="c16cb-120">RoleCapability</span></span>
- <span data-ttu-id="c16cb-121">Command</span><span class="sxs-lookup"><span data-stu-id="c16cb-121">Command</span></span>
- <span data-ttu-id="c16cb-122">Filter</span><span class="sxs-lookup"><span data-stu-id="c16cb-122">Filter</span></span>

<span data-ttu-id="c16cb-123">如果您只想要探索資源庫中的特定 DSC 資源，則可以執行 [Find-DscResource][] Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c16cb-123">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [Find-DscResource][] cmdlet.</span></span> <span data-ttu-id="c16cb-124">Find-DscResource 會傳回資源庫中所含 DSC 資源的資料。</span><span class="sxs-lookup"><span data-stu-id="c16cb-124">Find-DscResource returns data on DSC resources contained in the Gallery.</span></span> <span data-ttu-id="c16cb-125">因為 DSC 資源一律傳遞為模組的一部分，所以您仍然需要執行 [Install-Module][] 來安裝這些 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="c16cb-125">Because DSC resources are always delivered as part of a module, you still need to run [Install-Module][] to install those DSC resources.</span></span>

## <a name="learning-about-packages-in-the-powershell-gallery"></a><span data-ttu-id="c16cb-126">在 PowerShell 資源庫中了解套件</span><span class="sxs-lookup"><span data-stu-id="c16cb-126">Learning about packages in the PowerShell Gallery</span></span>

<span data-ttu-id="c16cb-127">在您找出自己感興趣的套件之後，可能會想要深入了解它。</span><span class="sxs-lookup"><span data-stu-id="c16cb-127">Once you've identified a package that you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="c16cb-128">您可以透過檢查該套件在資源庫上的特定頁面來這麼做。</span><span class="sxs-lookup"><span data-stu-id="c16cb-128">You can do this by examining that package's specific page on the Gallery.</span></span> <span data-ttu-id="c16cb-129">在該頁面上，您將可以看到所有與該套件一起上傳的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c16cb-129">On that page, you'll be able to see all of the metadata uploaded with the package.</span></span> <span data-ttu-id="c16cb-130">此中繼資料是由套件的作者所提供，且未經 Microsoft 驗證。</span><span class="sxs-lookup"><span data-stu-id="c16cb-130">This metadata is provided by the package's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="c16cb-131">套件的擁有者與用來發行該套件的資源庫帳戶具有緊密的關聯性，因此會比 [Author] \(作者\) 欄位中的資訊更為可靠。</span><span class="sxs-lookup"><span data-stu-id="c16cb-131">The Owner of the package is strongly tied to the Gallery account used to publish the package, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="c16cb-132">如果您發現可能未以誠信心態發行的套件，請按一下該套件頁面上的 [Report Abuse]  \(檢舉不當使用\)。</span><span class="sxs-lookup"><span data-stu-id="c16cb-132">If you discover a package that you feel is not published in good faith, click **Report Abuse** on that package's page.</span></span>

<span data-ttu-id="c16cb-133">如果您是執行 [Find-Module][] 或 [Find-Script][]，則可以在所傳回的 PSGetModuleInfo 物件中檢視這個資料。</span><span class="sxs-lookup"><span data-stu-id="c16cb-133">If you're running [Find-Module][] or [Find-Script][], you can view this data in the returned PSGetModuleInfo object.</span></span> <span data-ttu-id="c16cb-134">例如，執行 `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member` 可傳回資源庫中 PSReadLine 模組的資料。</span><span class="sxs-lookup"><span data-stu-id="c16cb-134">For example, running `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member` returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-packages-from-the-powershell-gallery"></a><span data-ttu-id="c16cb-135">從 PowerShell 資源庫下載套件</span><span class="sxs-lookup"><span data-stu-id="c16cb-135">Downloading packages from the PowerShell Gallery</span></span>

<span data-ttu-id="c16cb-136">從 PowerShell 資源庫下載套件時，建議使用下列程序︰</span><span class="sxs-lookup"><span data-stu-id="c16cb-136">We encourage the following process when downloading packages from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="c16cb-137">檢查</span><span class="sxs-lookup"><span data-stu-id="c16cb-137">Inspect</span></span>

<span data-ttu-id="c16cb-138">若要下載資源庫中的套件以進行檢查，請執行 [Save-Module][] 或 [Save-Script][] Cmdlet (視套件類型而定)。</span><span class="sxs-lookup"><span data-stu-id="c16cb-138">To download a package from the Gallery for inspection, run either the [Save-Module][] or [Save-Script][] cmdlet, depending on the package type.</span></span> <span data-ttu-id="c16cb-139">這可讓您在不安裝該套件的情況下於本機儲存它，並檢查套件內容。</span><span class="sxs-lookup"><span data-stu-id="c16cb-139">This lets you save the package locally without installing it, and inspect the package contents.</span></span> <span data-ttu-id="c16cb-140">請記得手動刪除已儲存的套件。</span><span class="sxs-lookup"><span data-stu-id="c16cb-140">Remember to delete the saved package manually.</span></span>

<span data-ttu-id="c16cb-141">這些套件有一部分是由 Microsoft 所撰寫，其他則是由 PowerShell 社群所撰寫。</span><span class="sxs-lookup"><span data-stu-id="c16cb-141">Some of these packages are authored by Microsoft, and others are authored by the PowerShell community.</span></span> <span data-ttu-id="c16cb-142">Microsoft 建議您先檢閱此資源庫上的套件內容和程式碼，然後再進行安裝。</span><span class="sxs-lookup"><span data-stu-id="c16cb-142">Microsoft recommends that you review the contents and code of packages on this gallery prior to installation.</span></span>

<span data-ttu-id="c16cb-143">如果您發現可能未以誠信心態發行的套件，請按一下該套件頁面上的 [Report Abuse]  \(檢舉不當使用\)。</span><span class="sxs-lookup"><span data-stu-id="c16cb-143">If you discover a package that you feel is not published in good faith, click **Report Abuse** on that package's page.</span></span>

### <a name="install"></a><span data-ttu-id="c16cb-144">安裝</span><span class="sxs-lookup"><span data-stu-id="c16cb-144">Install</span></span>

<span data-ttu-id="c16cb-145">若要安裝資源庫中的套件以來進行使用，請執行 [Install-Module][] 或 [Install-Script][] Cmdlet (視套件類型而定)。</span><span class="sxs-lookup"><span data-stu-id="c16cb-145">To install a package from the Gallery for use, run either the [Install-Module][] or [Install-Script][] cmdlet, depending on the package type.</span></span>

<span data-ttu-id="c16cb-146">[Install-Module][] 預設會將模組安裝至 `$env:ProgramFiles\WindowsPowerShell\Modules`。</span><span class="sxs-lookup"><span data-stu-id="c16cb-146">[Install-Module][] installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span>
<span data-ttu-id="c16cb-147">這需要系統管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="c16cb-147">This requires an administrator account.</span></span> <span data-ttu-id="c16cb-148">如果您新增 `-Scope CurrentUser` 參數，模組就會安裝至 `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`。</span><span class="sxs-lookup"><span data-stu-id="c16cb-148">If you add the `-Scope CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="c16cb-149">[Install-Script][] 預設會將指令碼安裝至 `$env:ProgramFiles\WindowsPowerShell\Scripts`。</span><span class="sxs-lookup"><span data-stu-id="c16cb-149">[Install-Script][] installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span>
<span data-ttu-id="c16cb-150">這需要系統管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="c16cb-150">This requires an administrator account.</span></span> <span data-ttu-id="c16cb-151">如果您新增 `-Scope CurrentUser` 參數，指令碼就會安裝至 `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`。</span><span class="sxs-lookup"><span data-stu-id="c16cb-151">If you add the `-Scope CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="c16cb-152">根據預設，[Install-Module][] 和 [Install-Script][] 會安裝套件的最新版本。</span><span class="sxs-lookup"><span data-stu-id="c16cb-152">By default, [Install-Module][] and [Install-Script][] installs the most current version of a package.</span></span> <span data-ttu-id="c16cb-153">若要安裝較舊的套件版本，請新增 `-RequiredVersion` 參數。</span><span class="sxs-lookup"><span data-stu-id="c16cb-153">To install an older version of the package, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="c16cb-154">部署</span><span class="sxs-lookup"><span data-stu-id="c16cb-154">Deploy</span></span>

<span data-ttu-id="c16cb-155">若要將套件從 PowerShell 資源庫部署至 Azure 自動化，按一下 [Azure 自動化]  ，然後按一下套件詳細資料頁面上的 [部署至 Azure 自動化]  。</span><span class="sxs-lookup"><span data-stu-id="c16cb-155">To deploy a package from the PowerShell Gallery to Azure Automation, click **Azure Automation**, then click **Deploy to Azure Automation** on the package details page.</span></span> <span data-ttu-id="c16cb-156">系統會將您重新導向至 Azure 管理入口網站，而您必須使用 Azure 帳戶認證來登入。</span><span class="sxs-lookup"><span data-stu-id="c16cb-156">You are redirected to the Azure Management Portal where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="c16cb-157">請注意，部署含相依性的套件會將所有相依性部署至 Azure 自動化。</span><span class="sxs-lookup"><span data-stu-id="c16cb-157">Note that deploying packages with dependencies deploys all the dependencies to Azure Automation.</span></span> <span data-ttu-id="c16cb-158">若要停用 [Deploy to Azure Automation] \(部署至 Azure 自動化) 按鈕，請將 **AzureAutomationNotSupported** 標記新增至套件中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c16cb-158">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your package metadata.</span></span>

<span data-ttu-id="c16cb-159">若要深入了解 Azure 自動化，請參閱 [Azure 自動化](/azure/automation)文件。</span><span class="sxs-lookup"><span data-stu-id="c16cb-159">To learn more about Azure Automation, see the [Azure Automation](/azure/automation) documentation.</span></span>

## <a name="updating-packages-from-the-powershell-gallery"></a><span data-ttu-id="c16cb-160">從 PowerShell 資源庫更新套件</span><span class="sxs-lookup"><span data-stu-id="c16cb-160">Updating packages from the PowerShell Gallery</span></span>

<span data-ttu-id="c16cb-161">若要更新從 PowerShell 資源庫安裝的套件，請執行 [Update-Module][] 或 [Update-Script][] Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c16cb-161">To update packages installed from the PowerShell Gallery, run either the [Update-Module][] or [Update-Script][] cmdlet.</span></span> <span data-ttu-id="c16cb-162">如果執行時未指定任何其他參數，[Update-Module][] 就會嘗試更新透過執行 [Install-Module][] 安裝的所有模組。</span><span class="sxs-lookup"><span data-stu-id="c16cb-162">When run without any additional parameters, [Update-Module][] attempts to update all modules installed by running [Install-Module][].</span></span> <span data-ttu-id="c16cb-163">若要選擇性地更新模組，請新增 `-Name` 參數。</span><span class="sxs-lookup"><span data-stu-id="c16cb-163">To selectively update modules, add the `-Name` parameter.</span></span>

<span data-ttu-id="c16cb-164">同樣地，如果執行時未指定任何其他參數，[Update-Script][] 也會嘗試更新透過執行 [Install-Script][] 安裝的所有指令碼。</span><span class="sxs-lookup"><span data-stu-id="c16cb-164">Similarly, when run without any additional parameters, [Update-Script][] also attempts to update all scripts installed by running [Install-Script][].</span></span> <span data-ttu-id="c16cb-165">若要選擇性地更新指令碼，請新增 `-Name` 參數。</span><span class="sxs-lookup"><span data-stu-id="c16cb-165">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-packages-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="c16cb-166">列出已從 PowerShell 資源庫安裝的套件</span><span class="sxs-lookup"><span data-stu-id="c16cb-166">List packages that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="c16cb-167">若要找出您已從 PowerShell 資源庫安裝的模組，請執行 [Get-InstalledModule][] Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c16cb-167">To find out which modules you have installed from the PowerShell Gallery, run the [Get-InstalledModule][] cmdlet.</span></span> <span data-ttu-id="c16cb-168">這個命令會列出系統上直接從 PowerShell Gallery 安裝的所有模組。</span><span class="sxs-lookup"><span data-stu-id="c16cb-168">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="c16cb-169">同樣地，若要找出您已從 PowerShell 資源庫安裝的指令碼，請執行 [Get-InstalledScript][] Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c16cb-169">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [Get-InstalledScript][] cmdlet.</span></span> <span data-ttu-id="c16cb-170">這個命令會列出系統上直接從 PowerShell Gallery 安裝的所有指令碼。</span><span class="sxs-lookup"><span data-stu-id="c16cb-170">This command lists all the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>

## <a name="network-access-to-the-powershell-gallery"></a><span data-ttu-id="c16cb-171">PowerShell 資源庫的網路存取權</span><span class="sxs-lookup"><span data-stu-id="c16cb-171">Network access to the PowerShell Gallery</span></span>

<span data-ttu-id="c16cb-172">PowerShell 資源庫使用下列主機名稱。</span><span class="sxs-lookup"><span data-stu-id="c16cb-172">The PowerShell Gallery uses the following hostnames.</span></span>

- <span data-ttu-id="c16cb-173">`psg-prod-eastus.azureedge.net` - CDN 主機名稱</span><span class="sxs-lookup"><span data-stu-id="c16cb-173">`psg-prod-eastus.azureedge.net` - the CDN hostname</span></span>
- <span data-ttu-id="c16cb-174">`devopsgallerystorage.blob.core.windows.net` - 儲存體帳戶主機名稱</span><span class="sxs-lookup"><span data-stu-id="c16cb-174">`devopsgallerystorage.blob.core.windows.net` - the storage account hostname</span></span>
- <span data-ttu-id="c16cb-175">`*.powershellgallery.com` - 網站</span><span class="sxs-lookup"><span data-stu-id="c16cb-175">`*.powershellgallery.com` - the website</span></span>

<span data-ttu-id="c16cb-176">這些主機名稱應新增至控制您的網路存取的允許清單。</span><span class="sxs-lookup"><span data-stu-id="c16cb-176">These hostnames should be added to the allow lists that control access from your network.</span></span>

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
[Update-Module]: /powershell/module/powershellget/Update-Module
[Update-Script]: /powershell/module/powershellget/Update-Script
