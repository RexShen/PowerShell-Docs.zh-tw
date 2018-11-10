---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 開始使用 PowerShell Gallery
ms.openlocfilehash: 85b0a754aba25d850dc918024419318554f92b33
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225670"
---
# <a name="getting-started-with-the-powershell-gallery"></a><span data-ttu-id="a1dae-103">開始使用 PowerShell 資源庫</span><span class="sxs-lookup"><span data-stu-id="a1dae-103">Getting Started with the PowerShell Gallery</span></span>

<span data-ttu-id="a1dae-104">從 PowerShell 資源庫安裝套件的正確方式，是使用 [PowerShellGet](/powershell/module/powershellget) 模組中的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a1dae-104">The proper way to install packages from the PowerShell Gallery is to use the cmdlets in the [PowerShellGet](/powershell/module/powershellget) module.</span></span> <span data-ttu-id="a1dae-105">您不需要登入，就可以從 PowerShell Gallery 下載項目。</span><span class="sxs-lookup"><span data-stu-id="a1dae-105">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="a1dae-106">您可以從 PowerShell 資源庫直接下載套件，但這不是建議的方法。</span><span class="sxs-lookup"><span data-stu-id="a1dae-106">It is possible to download a package from the PowerShell Gallery directly, but this is not a recommended approach.</span></span>
> <span data-ttu-id="a1dae-107">如需詳細資訊，請參閱[手動下載套件](/powershell/gallery/how-to/working-with-packages/manual-download)。</span><span class="sxs-lookup"><span data-stu-id="a1dae-107">For more details, see [Manual Package Download](/powershell/gallery/how-to/working-with-packages/manual-download).</span></span>

## <a name="discovering-packages-from-the-powershell-gallery"></a><span data-ttu-id="a1dae-108">從 PowerShell 資源庫探索套件</span><span class="sxs-lookup"><span data-stu-id="a1dae-108">Discovering packages from the PowerShell Gallery</span></span>

<span data-ttu-id="a1dae-109">您可以在 PowerShell 資源庫上使用 **Search** 控制項，或瀏覽 [Modules] \(模組\) 和 [Scripts] \(指令碼\) 頁面，來尋找這個網站中的套件。</span><span class="sxs-lookup"><span data-stu-id="a1dae-109">You can find packages in the PowerShell Gallery by using the **Search** control on this website, or by browsing through the Modules and Scripts pages.</span></span> <span data-ttu-id="a1dae-110">您也可以執行 [Find-Module][] 與 [Find-Script][] Cmdlet (視項目類型而定) 並搭配 `-Repository PSGallery`，以尋找 PowerShell 資源庫中的套件。</span><span class="sxs-lookup"><span data-stu-id="a1dae-110">You can also find packages from the PowerShell Gallery by running the [Find-Module][] and [Find-Script][] cmdlets, depending on the item type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="a1dae-111">若要從資源庫篩選結果，可以使用下列參數：</span><span class="sxs-lookup"><span data-stu-id="a1dae-111">Filtering results from the Gallery can be done by using the following parameters:</span></span>

- <span data-ttu-id="a1dae-112">名稱</span><span class="sxs-lookup"><span data-stu-id="a1dae-112">Name</span></span>
- <span data-ttu-id="a1dae-113">AllVersions</span><span class="sxs-lookup"><span data-stu-id="a1dae-113">AllVersions</span></span>
- <span data-ttu-id="a1dae-114">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="a1dae-114">MinimumVersion</span></span>
- <span data-ttu-id="a1dae-115">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="a1dae-115">RequiredVersion</span></span>
- <span data-ttu-id="a1dae-116">標籤</span><span class="sxs-lookup"><span data-stu-id="a1dae-116">Tag</span></span>
- <span data-ttu-id="a1dae-117">Includes</span><span class="sxs-lookup"><span data-stu-id="a1dae-117">Includes</span></span>
- <span data-ttu-id="a1dae-118">DscResource</span><span class="sxs-lookup"><span data-stu-id="a1dae-118">DscResource</span></span>
- <span data-ttu-id="a1dae-119">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="a1dae-119">RoleCapability</span></span>
- <span data-ttu-id="a1dae-120">命令</span><span class="sxs-lookup"><span data-stu-id="a1dae-120">Command</span></span>
- <span data-ttu-id="a1dae-121">篩選器</span><span class="sxs-lookup"><span data-stu-id="a1dae-121">Filter</span></span>

<span data-ttu-id="a1dae-122">如果您只想要探索資源庫中的特定 DSC 資源，則可以執行 [Find-DscResource] Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a1dae-122">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [Find-DscResource] cmdlet.</span></span> <span data-ttu-id="a1dae-123">Find-DscResource 會傳回資源庫中所含 DSC 資源的資料。</span><span class="sxs-lookup"><span data-stu-id="a1dae-123">Find-DscResource returns data on DSC resources contained in the Gallery.</span></span>
<span data-ttu-id="a1dae-124">因為 DSC 資源一律傳遞為模組的一部分，所以您仍然需要執行 [Install-Module][] 來安裝這些 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="a1dae-124">Because DSC resources are always delivered as part of a module, you still need to run [Install-Module][] to install those DSC resources.</span></span>

## <a name="learning-about-packages-in-the-powershell-gallery"></a><span data-ttu-id="a1dae-125">在 PowerShell 資源庫中了解套件</span><span class="sxs-lookup"><span data-stu-id="a1dae-125">Learning about packages in the PowerShell Gallery</span></span>

<span data-ttu-id="a1dae-126">在您找出自己感興趣的套件之後，可能會想要深入了解它。</span><span class="sxs-lookup"><span data-stu-id="a1dae-126">Once you've identified a package that you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="a1dae-127">您可以透過檢查該套件在資源庫上的特定頁面來這麼做。</span><span class="sxs-lookup"><span data-stu-id="a1dae-127">You can do this by examining that package's specific page on the Gallery.</span></span> <span data-ttu-id="a1dae-128">在該頁面上，您將可以看到所有與該套件一起上傳的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a1dae-128">On that page, you'll be able to see all of the metadata uploaded with the package.</span></span> <span data-ttu-id="a1dae-129">此中繼資料是由套件的作者所提供，且未經 Microsoft 驗證。</span><span class="sxs-lookup"><span data-stu-id="a1dae-129">This metadata is provided by the package's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="a1dae-130">套件的擁有者與用來發行該套件的資源庫帳戶具有緊密的關聯性，因此會比 [Author] \(作者\) 欄位中的資訊更為可靠。</span><span class="sxs-lookup"><span data-stu-id="a1dae-130">The Owner of the package is strongly tied to the Gallery account used to publish the package, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="a1dae-131">如果您發現可能未以誠信心態發行的套件，請按一下該套件頁面上的 [Report Abuse] \(檢舉不當使用\)。</span><span class="sxs-lookup"><span data-stu-id="a1dae-131">If you discover a package that you feel is not published in good faith, click **Report Abuse** on that package's page.</span></span>

<span data-ttu-id="a1dae-132">如果您是執行 [Find-Module][] 或 [Find-Script][]，則可以在所傳回的 PSGetModuleInfo 物件中檢視這個資料。</span><span class="sxs-lookup"><span data-stu-id="a1dae-132">If you're running [Find-Module][] or [Find-Script][], you can view this data in the returned PSGetModuleInfo object.</span></span> <span data-ttu-id="a1dae-133">例如，執行 `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span><span class="sxs-lookup"><span data-stu-id="a1dae-133">For example, running `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span></span>
<span data-ttu-id="a1dae-134">會傳回資源庫中 PSReadLine 模組的相關資料。</span><span class="sxs-lookup"><span data-stu-id="a1dae-134">returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-packages-from-the-powershell-gallery"></a><span data-ttu-id="a1dae-135">從 PowerShell 資源庫下載套件</span><span class="sxs-lookup"><span data-stu-id="a1dae-135">Downloading packages from the PowerShell Gallery</span></span>

<span data-ttu-id="a1dae-136">從 PowerShell 資源庫下載套件時，建議使用下列程序︰</span><span class="sxs-lookup"><span data-stu-id="a1dae-136">We encourage the following process when downloading packages from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="a1dae-137">檢查</span><span class="sxs-lookup"><span data-stu-id="a1dae-137">Inspect</span></span>

<span data-ttu-id="a1dae-138">若要下載資源庫中的套件以進行檢查，請執行 [Save-Module][] 或 [Save-Script][] Cmdlet (視套件類型而定)。</span><span class="sxs-lookup"><span data-stu-id="a1dae-138">To download a package from the Gallery for inspection, run either the [Save-Module][] or [Save-Script][] cmdlet, depending on the package type.</span></span> <span data-ttu-id="a1dae-139">這可讓您在不安裝該套件的情況下於本機儲存它，並檢查套件內容。</span><span class="sxs-lookup"><span data-stu-id="a1dae-139">This lets you save the package locally without installing it, and inspect the package contents.</span></span> <span data-ttu-id="a1dae-140">請記得手動刪除已儲存的套件。</span><span class="sxs-lookup"><span data-stu-id="a1dae-140">Remember to delete the saved package manually.</span></span>

<span data-ttu-id="a1dae-141">這些套件有一部分是由 Microsoft 所撰寫，其他則是由 PowerShell 社群所撰寫。</span><span class="sxs-lookup"><span data-stu-id="a1dae-141">Some of these packages are authored by Microsoft, and others are authored by the PowerShell community.</span></span>
<span data-ttu-id="a1dae-142">Microsoft 建議您先檢閱此資源庫上的套件內容和程式碼，然後再進行安裝。</span><span class="sxs-lookup"><span data-stu-id="a1dae-142">Microsoft recommends that you review the contents and code of packages on this gallery prior to installation.</span></span>

<span data-ttu-id="a1dae-143">如果您發現可能未以誠信心態發行的套件，請按一下該套件頁面上的 [Report Abuse] \(檢舉不當使用\)。</span><span class="sxs-lookup"><span data-stu-id="a1dae-143">If you discover a package that you feel is not published in good faith, click **Report Abuse** on that package's page.</span></span>

### <a name="install"></a><span data-ttu-id="a1dae-144">安裝</span><span class="sxs-lookup"><span data-stu-id="a1dae-144">Install</span></span>

<span data-ttu-id="a1dae-145">若要安裝資源庫中的套件以來進行使用，請執行 [Install-Module][] 或 [Install-Script][] Cmdlet (視套件類型而定)。</span><span class="sxs-lookup"><span data-stu-id="a1dae-145">To install a package from the Gallery for use, run either the [Install-Module][] or [Install-Script][] cmdlet, depending on the package type.</span></span>

<span data-ttu-id="a1dae-146">[Install-Module][] 預設會將模組安裝至 `$env:ProgramFiles\WindowsPowerShell\Modules`。</span><span class="sxs-lookup"><span data-stu-id="a1dae-146">[Install-Module][] installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span>
<span data-ttu-id="a1dae-147">這需要系統管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="a1dae-147">This requires an administrator account.</span></span> <span data-ttu-id="a1dae-148">如果您新增 `-Scope CurrentUser` 參數，模組就會安裝至 `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`。</span><span class="sxs-lookup"><span data-stu-id="a1dae-148">If you add the `-Scope CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="a1dae-149">[Install-Script][] 預設會將指令碼安裝至 `$env:ProgramFiles\WindowsPowerShell\Scripts`。</span><span class="sxs-lookup"><span data-stu-id="a1dae-149">[Install-Script][] installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span>
<span data-ttu-id="a1dae-150">這需要系統管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="a1dae-150">This requires an administrator account.</span></span> <span data-ttu-id="a1dae-151">如果您新增 `-Scope CurrentUser` 參數，指令碼就會安裝至 `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`。</span><span class="sxs-lookup"><span data-stu-id="a1dae-151">If you add the `-Scope CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="a1dae-152">根據預設，[Install-Module][] 和 [Install-Script][] 會安裝套件的最新版本。</span><span class="sxs-lookup"><span data-stu-id="a1dae-152">By default, [Install-Module][] and [Install-Script][] installs the most current version of a package.</span></span>
<span data-ttu-id="a1dae-153">若要安裝較舊的套件版本，請新增 `-RequiredVersion` 參數。</span><span class="sxs-lookup"><span data-stu-id="a1dae-153">To install an older version of the package, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="a1dae-154">在客體叢集部署</span><span class="sxs-lookup"><span data-stu-id="a1dae-154">Deploy</span></span>

<span data-ttu-id="a1dae-155">若要將套件從 PowerShell 資源庫部署至 Azure 自動化，請按一下套件詳細資料頁面上的 [Deploy to Azure Automation] \(部署至 Azure 自動化)。</span><span class="sxs-lookup"><span data-stu-id="a1dae-155">To deploy a package from the PowerShell Gallery to Azure Automation, click **Deploy to Azure Automation** on the package details page.</span></span> <span data-ttu-id="a1dae-156">系統會將您重新導向至 Azure 管理入口網站，而您必須使用 Azure 帳戶認證來登入。</span><span class="sxs-lookup"><span data-stu-id="a1dae-156">You will be redirected to the Azure Management Portal where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="a1dae-157">請注意，部署包含相依性的套件會將所有相依性部署至 Azure 自動化。</span><span class="sxs-lookup"><span data-stu-id="a1dae-157">Note that deploying packages with dependencies will deploy all the dependencies to Azure Automation.</span></span> <span data-ttu-id="a1dae-158">若要停用 [Deploy to Azure Automation] \(部署至 Azure 自動化) 按鈕，請將 **AzureAutomationNotSupported** 標記新增至套件中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a1dae-158">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your package metadata.</span></span>

<span data-ttu-id="a1dae-159">若要深入了解 Azure 自動化，請參閱 [Azure 自動化](/azure/automation)文件。</span><span class="sxs-lookup"><span data-stu-id="a1dae-159">To learn more about Azure Automation, see the [Azure Automation](/azure/automation) documentation.</span></span>

## <a name="updating-packages-from-the-powershell-gallery"></a><span data-ttu-id="a1dae-160">從 PowerShell 資源庫更新套件</span><span class="sxs-lookup"><span data-stu-id="a1dae-160">Updating packages from the PowerShell Gallery</span></span>

<span data-ttu-id="a1dae-161">若要更新從 PowerShell 資源庫安裝的套件，請執行 [Update-Module][] 或 [Update-Script][] Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a1dae-161">To update packages installed from the PowerShell Gallery, run either the [Update-Module][] or [Update-Script][] cmdlet.</span></span> <span data-ttu-id="a1dae-162">如果執行時未指定任何其他參數，[Update-Module][] 就會嘗試更新透過執行 [Install-Module][] 所安裝的每個模組。</span><span class="sxs-lookup"><span data-stu-id="a1dae-162">When run without any additional parameters, [Update-Module][] attempts to update each module installed by running [Install-Module][].</span></span> <span data-ttu-id="a1dae-163">若要選擇性地更新模組，請新增 `-Name` 參數。</span><span class="sxs-lookup"><span data-stu-id="a1dae-163">To selectively update modules, add the `-Name` parameter.</span></span>

<span data-ttu-id="a1dae-164">同樣地，如果執行時未指定任何其他參數，[Update-Script][] 也會嘗試更新透過執行 [Install-Script][] 所安裝的每個指令碼。</span><span class="sxs-lookup"><span data-stu-id="a1dae-164">Similarly, when run without any additional parameters, [Update-Script][] also attempts to update each script installed by running [Install-Script][].</span></span> <span data-ttu-id="a1dae-165">若要選擇性地更新指令碼，請新增 `-Name` 參數。</span><span class="sxs-lookup"><span data-stu-id="a1dae-165">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-packages-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="a1dae-166">列出已從 PowerShell 資源庫安裝的套件</span><span class="sxs-lookup"><span data-stu-id="a1dae-166">List packages that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="a1dae-167">若要找出您已從 PowerShell 資源庫安裝的模組，請執行 [Get-InstalledModule][] Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a1dae-167">To find out which modules you have installed from the PowerShell Gallery, run the [Get-InstalledModule][] cmdlet.</span></span> <span data-ttu-id="a1dae-168">這個命令會列出系統上直接從 PowerShell Gallery 安裝的所有模組。</span><span class="sxs-lookup"><span data-stu-id="a1dae-168">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="a1dae-169">同樣地，若要找出您已從 PowerShell 資源庫安裝的指令碼，請執行 [Get-InstalledScript][] Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a1dae-169">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [Get-InstalledScript][] cmdlet.</span></span> <span data-ttu-id="a1dae-170">這個命令會列出系統上直接從 PowerShell Gallery 安裝的所有指令碼。</span><span class="sxs-lookup"><span data-stu-id="a1dae-170">This command lists all of the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>

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
