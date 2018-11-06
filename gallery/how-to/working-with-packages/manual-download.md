---
ms.date: 09/11/2018
contributor: JKeithB
keywords: gallery,powershell,psgallery,資源庫
title: 手動下載套件
ms.openlocfilehash: 0952aa4ec474850af5219fb2e0e9ee3e954b0f9a
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003700"
---
# <a name="manual-package-download"></a><span data-ttu-id="80ac7-103">手動下載套件</span><span class="sxs-lookup"><span data-stu-id="80ac7-103">Manual Package Download</span></span>

<span data-ttu-id="80ac7-104">Powershell 資源庫支援直接從網站下載套件，而不需要使用 PowerShellGet Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="80ac7-104">The Powershell Gallery supports downloading a package from the website directly, without using the PowerShellGet cmdlets.</span></span> <span data-ttu-id="80ac7-105">套件會下載為 NuGet 套件 (.nupkg) 檔案，之後可輕鬆複製到內部存放庫。</span><span class="sxs-lookup"><span data-stu-id="80ac7-105">The package will be downloaded as a NuGet package (.nupkg) file, which can then be easily copied to an internal repository.</span></span>

> [!NOTE]
> <span data-ttu-id="80ac7-106">手動下載套件**不會**取代 Install-Module Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="80ac7-106">Manual package download is **not** intended as a replacement for the Install-Module cmdlet.</span></span>
> <span data-ttu-id="80ac7-107">下載套件不會安裝模組或指令碼。</span><span class="sxs-lookup"><span data-stu-id="80ac7-107">Downloading the package does not install the module or script.</span></span> <span data-ttu-id="80ac7-108">下載的 NuGet 套件中不會包含相依性。</span><span class="sxs-lookup"><span data-stu-id="80ac7-108">Dependencies are not included in the NuGet package downloaded.</span></span> <span data-ttu-id="80ac7-109">下列指示僅供參考。</span><span class="sxs-lookup"><span data-stu-id="80ac7-109">The following instructions are provided for reference purposes only.</span></span>

## <a name="using-manual-download-to-acquire-a-package"></a><span data-ttu-id="80ac7-110">使用手動下載來取得套件</span><span class="sxs-lookup"><span data-stu-id="80ac7-110">Using manual download to acquire a package</span></span>

<span data-ttu-id="80ac7-111">每個頁面會有 [手動下載] 連結，如下所示：</span><span class="sxs-lookup"><span data-stu-id="80ac7-111">Each page has a link for Manual Download, as shown here:</span></span>

![手動下載](../../Images/packagedisplaypagewithpseditions.png)

<span data-ttu-id="80ac7-113">若要手動下載，請按一下 [Download the raw nupkg file] \(下載原始 nupkg 檔案\)。</span><span class="sxs-lookup"><span data-stu-id="80ac7-113">To download manually, click on **Download the raw nupkg file**.</span></span> <span data-ttu-id="80ac7-114">這會將套件複本複製到您瀏覽器中名為 `<name>.<version>.nupkg` 的下載資料夾。</span><span class="sxs-lookup"><span data-stu-id="80ac7-114">A copy of the package copied to the download folder for your browser with the name `<name>.<version>.nupkg`.</span></span>

<span data-ttu-id="80ac7-115">NuGet 套件是 ZIP 封存以及含有套件內容相關資訊的額外檔案。</span><span class="sxs-lookup"><span data-stu-id="80ac7-115">A NuGet package is a ZIP archive with extra files containing information about the contents of the package.</span></span> <span data-ttu-id="80ac7-116">某些瀏覽器 (例如 Internet Explorer) 會自動以 `.zip` 取代 `.nupkg` 副檔名。</span><span class="sxs-lookup"><span data-stu-id="80ac7-116">Some browsers, like Internet Explorer, automatically replace the `.nupkg` file extension with `.zip`.</span></span> <span data-ttu-id="80ac7-117">若要展開套件，請視需要將 `.nupkg` 檔案重新命名為 `.zip`，然後將內容解壓縮至本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="80ac7-117">To expand the package, rename the `.nupkg` file to `.zip`, if needed, then extract the contents to a local folder.</span></span>

<span data-ttu-id="80ac7-118">NuGet 套件檔案包含不屬於原始封裝程式碼的下列 NuGet 特定項目：</span><span class="sxs-lookup"><span data-stu-id="80ac7-118">A NuGet package file includes the following NuGet-specific elements that aren't part of the original packaged code:</span></span>

- <span data-ttu-id="80ac7-119">名為 `_rels` 的資料夾 - 包含列出相依性的 `.rels` 檔案</span><span class="sxs-lookup"><span data-stu-id="80ac7-119">A folder named `_rels` - contains a `.rels` file that lists the dependencies</span></span>
- <span data-ttu-id="80ac7-120">名為 `package` 的資料夾 - 包含 NuGet 特定資料</span><span class="sxs-lookup"><span data-stu-id="80ac7-120">A folder named `package` - contains the NuGet-specific data</span></span>
- <span data-ttu-id="80ac7-121">名為 `[Content_Types].xml` 的檔案 - 描述 PowerShellGet 等延伸模組如何與 NuGet 搭配運作</span><span class="sxs-lookup"><span data-stu-id="80ac7-121">A file named `[Content_Types].xml` - describes how extensions like PowerShellGet work with NuGet</span></span>
- <span data-ttu-id="80ac7-122">名為 `<name>.nuspec` 的檔案 - 包含大量中繼資料</span><span class="sxs-lookup"><span data-stu-id="80ac7-122">A file named `<name>.nuspec` - contains the bulk of the metadata</span></span>

## <a name="installing-powershell-modules-from-a-nuget-package"></a><span data-ttu-id="80ac7-123">從 NuGet 套件安裝 PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="80ac7-123">Installing PowerShell Modules from a NuGet package</span></span>

> [!NOTE]
> <span data-ttu-id="80ac7-124">這些指示**不會**提供與執行 `Install-Module` 相同的結果。</span><span class="sxs-lookup"><span data-stu-id="80ac7-124">These instructions **DO NOT** give the same result as running `Install-Module`.</span></span> <span data-ttu-id="80ac7-125">這些指示符合最低需求。</span><span class="sxs-lookup"><span data-stu-id="80ac7-125">These instructions fulfill the minimum requirements.</span></span> <span data-ttu-id="80ac7-126">它們不會取代 `Install-Module`。</span><span class="sxs-lookup"><span data-stu-id="80ac7-126">They are not intended to be a replacement for `Install-Module`.</span></span> <span data-ttu-id="80ac7-127">`Install-Module` 執行的一些步驟並未包含在內。</span><span class="sxs-lookup"><span data-stu-id="80ac7-127">Some steps performed by `Install-Module` are not included.</span></span>

<span data-ttu-id="80ac7-128">最簡單的方法是從資料夾中移除 NuGet 特定項目。</span><span class="sxs-lookup"><span data-stu-id="80ac7-128">The easiest approach is to remove the NuGet-specific elements from the folder.</span></span> <span data-ttu-id="80ac7-129">這會留下套件作者所建立的 PowerShell 程式碼。</span><span class="sxs-lookup"><span data-stu-id="80ac7-129">This leaves the PowerShell code created by the package author.</span></span> <span data-ttu-id="80ac7-130">步驟如下：</span><span class="sxs-lookup"><span data-stu-id="80ac7-130">The steps are:</span></span>

1. <span data-ttu-id="80ac7-131">將 NuGet 套件內容解壓縮至本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="80ac7-131">Extract the contents of the NuGet package to a local folder.</span></span>
2. <span data-ttu-id="80ac7-132">從資料夾中刪除 NuGet 特定項目。</span><span class="sxs-lookup"><span data-stu-id="80ac7-132">Delete the NuGet-specific elements from the folder.</span></span>
3. <span data-ttu-id="80ac7-133">重新命名資料夾。</span><span class="sxs-lookup"><span data-stu-id="80ac7-133">Rename the folder.</span></span> <span data-ttu-id="80ac7-134">預設資料夾名稱通常是 `<name>.<version>`。</span><span class="sxs-lookup"><span data-stu-id="80ac7-134">The default folder name is usually `<name>.<version>`.</span></span> <span data-ttu-id="80ac7-135">如果模組標記為發行前版本，則版本可以包含 "-prerelease"。</span><span class="sxs-lookup"><span data-stu-id="80ac7-135">The version can include "-prerelease" if the module is tagged as a prerelease version.</span></span> <span data-ttu-id="80ac7-136">請將資料夾重新命名為只有模組名稱。</span><span class="sxs-lookup"><span data-stu-id="80ac7-136">Rename the folder to just the module name.</span></span> <span data-ttu-id="80ac7-137">例如，"azurerm.storage.5.0.4-preview" 會變成 "azurerm.storage"。</span><span class="sxs-lookup"><span data-stu-id="80ac7-137">For example, "azurerm.storage.5.0.4-preview" becomes "azurerm.storage".</span></span>
4. <span data-ttu-id="80ac7-138">將資料夾複製到您的 PSModulePath。</span><span class="sxs-lookup"><span data-stu-id="80ac7-138">Copy the folder to your PSModulePath.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="80ac7-139">手動下載不會包含模組所需的任何相依性。</span><span class="sxs-lookup"><span data-stu-id="80ac7-139">The manual download does not include any dependencies required by the module.</span></span> <span data-ttu-id="80ac7-140">如果套件具有相依性，則必須在系統上加以安裝，此模組才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="80ac7-140">If the package has dependencies, they must be installed on the system for this module to work correctly.</span></span> <span data-ttu-id="80ac7-141">PowerShell 資源庫會顯示套件所需的所有相依性。</span><span class="sxs-lookup"><span data-stu-id="80ac7-141">The PowerShell Gallery shows all dependencies required by the package.</span></span>

## <a name="installing-powershell-scripts-from-a-nuget-package"></a><span data-ttu-id="80ac7-142">從 NuGet 套件安裝 PowerShell 指令碼</span><span class="sxs-lookup"><span data-stu-id="80ac7-142">Installing PowerShell Scripts from a NuGet package</span></span>

> [!NOTE]
> <span data-ttu-id="80ac7-143">這些指示**不會**提供與執行 `Install-Script` 相同的結果。</span><span class="sxs-lookup"><span data-stu-id="80ac7-143">These instructions **DO NOT** give the same result as running `Install-Script`.</span></span> <span data-ttu-id="80ac7-144">這些指示符合最低需求。</span><span class="sxs-lookup"><span data-stu-id="80ac7-144">These instructions fulfill the minimum requirements.</span></span> <span data-ttu-id="80ac7-145">它們不會取代 `Install-Script`。</span><span class="sxs-lookup"><span data-stu-id="80ac7-145">They are not intended to be a replacement for `Install-Script`.</span></span>

<span data-ttu-id="80ac7-146">最簡單的方法是解壓縮 NuGet 套件，然後直接使用指令碼。</span><span class="sxs-lookup"><span data-stu-id="80ac7-146">The easiest approach is to extract the NuGet package, then use the script directly.</span></span> <span data-ttu-id="80ac7-147">步驟如下：</span><span class="sxs-lookup"><span data-stu-id="80ac7-147">The steps are:</span></span>

1. <span data-ttu-id="80ac7-148">解壓縮 NuGet 套件內容。</span><span class="sxs-lookup"><span data-stu-id="80ac7-148">Extract the contents of the NuGet package.</span></span>
2. <span data-ttu-id="80ac7-149">資料夾中的 `.PS1` 檔案可直接從此位置使用。</span><span class="sxs-lookup"><span data-stu-id="80ac7-149">The `.PS1` file in the folder can be used directly from this location.</span></span>
3. <span data-ttu-id="80ac7-150">您可以刪除此資料夾中的 NuGet 特定項目。</span><span class="sxs-lookup"><span data-stu-id="80ac7-150">You may delete the NuGet-specific elements in the folder.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="80ac7-151">手動下載不會包含模組所需的任何相依性。</span><span class="sxs-lookup"><span data-stu-id="80ac7-151">The manual download does not include any dependencies required by the module.</span></span> <span data-ttu-id="80ac7-152">如果套件具有相依性，則必須在系統上加以安裝，此模組才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="80ac7-152">If the package has dependencies, they must be installed on the system for this module to work correctly.</span></span> <span data-ttu-id="80ac7-153">PowerShell 資源庫會顯示套件所需的所有相依性。</span><span class="sxs-lookup"><span data-stu-id="80ac7-153">The PowerShell Gallery shows all dependencies required by the package.</span></span>
