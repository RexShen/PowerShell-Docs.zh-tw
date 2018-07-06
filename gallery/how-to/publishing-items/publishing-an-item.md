---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 建立及發行項目
ms.openlocfilehash: 7c2a2be6986bf65c168d7c3960366fac4ee31301
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189528"
---
# <a name="creating-and-publishing-an-item"></a><span data-ttu-id="5ee5b-103">建立及發行項目</span><span class="sxs-lookup"><span data-stu-id="5ee5b-103">Creating and publishing an item</span></span>

<span data-ttu-id="5ee5b-104">「PowerShell 資源庫」是可供您發行及與更廣大的 PowerShell 使用者社群共用穩定的 PowerShell 模組、指令碼及 DSC 資源的地方。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-104">The PowerShell Gallery is the place to publish and share stable PowerShell modules, scripts, and DSC resources with the broader PowerShell user community.</span></span>

<span data-ttu-id="5ee5b-105">本文涵蓋準備指令碼或模組並將其發行至「PowerShell 資源庫」的機制和重要步驟。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-105">This article covers the mechanics and important steps for preparing a script or module, and publishing it to the PowerShell Gallery.</span></span>
<span data-ttu-id="5ee5b-106">強烈建議您檢閱[發行指導分針](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery-PublishingGuidelines) \(英文\)，以了解如何確保您發行的項目將更廣泛地獲得「PowerShell 資源庫」使用者接受。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-106">We strongly encourage that you review the [Publishing Guidelines](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery-PublishingGuidelines) to understand how to ensure that the items you publish will be more widely accepted by PowerShell Gallery users.</span></span>

<span data-ttu-id="5ee5b-107">將項目發行至「PowerShell 資源庫」的最低需求包括：</span><span class="sxs-lookup"><span data-stu-id="5ee5b-107">The minimum requirements to publish an item to the PowerShell Gallery are:</span></span>

- <span data-ttu-id="5ee5b-108">擁有「PowerShell 資源庫」帳戶及與該帳戶關聯的 API 金鑰</span><span class="sxs-lookup"><span data-stu-id="5ee5b-108">Have a PowerShell Gallery account, and the API Key associated with it</span></span>
- <span data-ttu-id="5ee5b-109">確定您的項目中有「必要的中繼資料」</span><span class="sxs-lookup"><span data-stu-id="5ee5b-109">Ensure Required Metadata is in your item</span></span>
- <span data-ttu-id="5ee5b-110">使用預先驗證工具來確保您的項目已可發行</span><span class="sxs-lookup"><span data-stu-id="5ee5b-110">Use the pre-validation tools to ensure your item is ready to publish</span></span>
- <span data-ttu-id="5ee5b-111">使用 Publish-Module 和 Publish-Script 命令將項目發行至「PowerShell 資源庫」</span><span class="sxs-lookup"><span data-stu-id="5ee5b-111">Publish the item to the PowerShell Gallery using the Publish-Module and Publish-Script commands</span></span>
- <span data-ttu-id="5ee5b-112">對您項目的相關問題與疑慮進行回應</span><span class="sxs-lookup"><span data-stu-id="5ee5b-112">Responding to questions or concerns about your item</span></span>

<span data-ttu-id="5ee5b-113">「PowerShell 資源庫」接受 PowerShell 模組和 PowerShell 指令碼。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-113">The PowerShell Gallery accepts PowerShell modules and PowerShell scripts.</span></span>
<span data-ttu-id="5ee5b-114">當我們提到指令碼時，是指本身是單一檔案而不屬於較大模組之一部分的 PowerShell 指令碼。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-114">When we refer to scripts, we mean a PowerShell script that is a single file, and not part of a larger module.</span></span>

## <a name="powershell-gallery-account-and-api-key"></a><span data-ttu-id="5ee5b-115">PowerShell 資源庫帳戶和 API 金鑰</span><span class="sxs-lookup"><span data-stu-id="5ee5b-115">PowerShell Gallery Account and API Key</span></span>

<span data-ttu-id="5ee5b-116">如需了解如何設定您的「PowerShell 資源庫」帳戶，請參閱[建立 PowerShell 資源庫帳戶](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery_creating_an_account) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-116">See [Creating a PowerShell Gallery Account](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery_creating_an_account) for how to set up your PowerShell Gallery account.</span></span>

<span data-ttu-id="5ee5b-117">建立帳戶之後，您可以取得發行項目所需的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-117">Once you have created an account, you can get the API Key needed to publish an item.</span></span>
<span data-ttu-id="5ee5b-118">使用帳戶進行登入之後，您的使用者名稱將會顯示在「PowerShell 資源庫」頁面的頂端，而不會顯示 [註冊]。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-118">After you sign in with the account, your username will be displayed at the top of the PowerShell Gallery pages instead of Register.</span></span>
<span data-ttu-id="5ee5b-119">按一下您的帳戶名稱就會前往 [我的帳戶] 頁面，您將可以在該頁面找到 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-119">Clicking on your username will take you to the My Account page, where you will find the API Key.</span></span>

<span data-ttu-id="5ee5b-120">注意：必須小心保管 API 金鑰，就像對待您的登錄和密碼一樣。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-120">Note: The API Key must be treated as securely as your login and password.</span></span>
<span data-ttu-id="5ee5b-121">您或任何其他使用者只要有了這個金鑰，便可更新「PowerShell 資源庫」中您擁有的所有項目。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-121">With this key you, or anyone else, can update any item you own in the PowerShell Gallery.</span></span>
<span data-ttu-id="5ee5b-122">建議您定期更新此金鑰，只要使用 [我的帳戶] 頁面上的 [重設金鑰]，即可完成此操作。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-122">We recommend updating the key regularly, which can be done using Reset Key on your My Account page.</span></span>

## <a name="required-metadata-for-items-published-to-the-powershell-gallery"></a><span data-ttu-id="5ee5b-123">發行至 PowerShell 資源庫之項目的必要中繼資料</span><span class="sxs-lookup"><span data-stu-id="5ee5b-123">Required Metadata for Items Published to the PowerShell Gallery</span></span>

<span data-ttu-id="5ee5b-124">「PowerShell 資源庫」會將從指令碼或模組資訊清單所包含之中繼資料欄位取得的資訊，提供給資源庫使用者。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-124">The PowerShell Gallery provides information to gallery users drawn from metadata fields that are included in the script or module manifest.</span></span>
<span data-ttu-id="5ee5b-125">建立或修改要發行至「PowerShell 資源庫」的項目時，針對在項目資訊清單中提供的資訊有一些要求。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-125">Creating or modifying items for publication to the PowerShell Gallery has a small set of requirements for information supplied in the item manifest.</span></span>
<span data-ttu-id="5ee5b-126">強烈建議您檢閱[發行指導方針](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery-PublishingGuidelines) \(英文\) 的 ＜項目中繼資料＞ (Item Metadata) 一節，以了解如何為您項目的使用者提供最佳資訊。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-126">We strongly encourage that you review the Item Metadata section of the [Publishing Guidelines](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery-PublishingGuidelines) to learn how to provide the best information to users with your items.</span></span>

<span data-ttu-id="5ee5b-127">[New-ModuleManifest](https://msdn.microsoft.com/en-us/powershell/gallery/psget/module/ModuleManifest-Reference) 和 [New-ScriptFileInfo](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_new-scriptfileinfo) Cmdlet 將會為您建立資訊清單範本，其中會包含所有資訊清單元素的預留位置。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-127">The [New-ModuleManifest](https://msdn.microsoft.com/en-us/powershell/gallery/psget/module/ModuleManifest-Reference) and [New-ScriptFileInfo](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_new-scriptfileinfo) cmdlets will create the manifest template for you, with placeholders for all the manifest elements.</span></span>

<span data-ttu-id="5ee5b-128">兩個資訊清單都有兩個對發行而言相當重要的區段，即「主索引鍵資料」和 PrivateData 的 PSData 區域。PowerShell 模組資訊清單中的主索引鍵資料係指 PrivateData 區段外的所有資料。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-128">Both manifests have two sections that are important for publishing, the Primary Key Data and PSData area of PrivateData The primary key data in a PowerShell module manifest is everything outside of the PrivateData section.</span></span>
<span data-ttu-id="5ee5b-129">主索引鍵組會繫結至使用中的 PowerShell 版本，且不支援設為未定義。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-129">The set of primary keys is tied to the version of PowerShell in use, and undefined are not supported.</span></span>
<span data-ttu-id="5ee5b-130">PrivateData 支援新增金鑰，因此「PowerShell 資源庫」特定的元素會在 PSData 中。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-130">PrivateData supports adding new keys, so the elements specific to the PowerShell Gallery are in PSData.</span></span>


<span data-ttu-id="5ee5b-131">對您要發行至「PowerShell 資源庫」的項目來說，要填入的最重要資訊清單元素包括：</span><span class="sxs-lookup"><span data-stu-id="5ee5b-131">Manifest elements that are most important to fill in for item you publish to the PowerShell Gallery are:</span></span>

- <span data-ttu-id="5ee5b-132">指令碼或模組名稱 - 這些名稱會取自 .PS1 (適用於指令碼) 或 .PSD1 (適用於模組)。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-132">Script or Module Name - Those are drawn from the names of the .PS1 for a script, or the .PSD1 for a module.</span></span>
- <span data-ttu-id="5ee5b-133">版本 - 這是必要的主索引鍵，格式應該依循 SemVer 指導方針 (如需詳細資料，請參閱＜最佳做法＞)</span><span class="sxs-lookup"><span data-stu-id="5ee5b-133">Version - this is a required primary key, format should follow SemVer guidelines (see Best Practices for details)</span></span>
- <span data-ttu-id="5ee5b-134">作者 - 這是必要的主索引鍵，並且包含要與項目建立關聯的名稱 (請參閱下面的「作者」和「擁有者」)</span><span class="sxs-lookup"><span data-stu-id="5ee5b-134">Author - this is a required primary key, and contains the name to be associated with the item (see Authors and Owners, below)</span></span>
- <span data-ttu-id="5ee5b-135">描述 - 這是必要的主索引鍵，用來簡要說明此項目的功能及使用它時的任何需求</span><span class="sxs-lookup"><span data-stu-id="5ee5b-135">Description - this is a required primary key, used to briefly explain what this item does and any requirements for using it</span></span>
- <span data-ttu-id="5ee5b-136">ProjectURI - 這是強烈建議使用的 PSData 中 URI 欄位，可提供 Github 儲存機制或可供您進行項目相關開發之類似位置的連結</span><span class="sxs-lookup"><span data-stu-id="5ee5b-136">ProjectURI - this is a strongly recommended URI field in PSData that provides a link to a Github repo or similar location where you do development on the item</span></span>

<span data-ttu-id="5ee5b-137">「PowerShell 資源庫」項目的「作者」和「擁有者」是相關的概念，但未必一定相符。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-137">Authors and Owners of PowerShell Gallery items are related concepts, but do not always match.</span></span>
<span data-ttu-id="5ee5b-138">項目「擁有者」是「PowerShell 資源庫」帳戶具有項目維護權限的使用者。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-138">Item Owners are users with PowerShell Gallery accounts that have permission to maintain the item.</span></span> <span data-ttu-id="5ee5b-139">可能會有許多個能夠更新任何項目的「擁有者」。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-139">There may be many Owners who can update any item.</span></span>
<span data-ttu-id="5ee5b-140">「擁有者」只有從「PowerShell 資源庫」中才有提供，且如果將項目從一個系統複製到另一個系統，就會遺失擁有者。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-140">The Owner is only available from the PowerShell Gallery, and is lost if the item is copied from one system to another.</span></span>
<span data-ttu-id="5ee5b-141">「作者」是建置在資訊清單資料中的字串，因此它一律是項目的一部分。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-141">Author is a string that is built into the manifest data, so it is always part of the item.</span></span>
<span data-ttu-id="5ee5b-142">針對來自 Microsoft 產品的項目，建議事項包括：</span><span class="sxs-lookup"><span data-stu-id="5ee5b-142">The recommendations for items from Microsoft products are:</span></span>

- <span data-ttu-id="5ee5b-143">設定多個擁有者，且至少要有一個是產生項目之小組的名稱；</span><span class="sxs-lookup"><span data-stu-id="5ee5b-143">Have multiple owners, with at least one being the name of the team that produces the item;</span></span>
- <span data-ttu-id="5ee5b-144">將「作者」設為已知的小組名稱 (例如 Azure SDK 小組) 或 Microsoft Corporation。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-144">Have the Author be a well-known team name (such as Azure SDK Team), or Microsoft Corporation.</span></span>


## <a name="pre-validate-your-item"></a><span data-ttu-id="5ee5b-145">預先驗證您的項目</span><span class="sxs-lookup"><span data-stu-id="5ee5b-145">Pre-Validate Your Item</span></span>

<span data-ttu-id="5ee5b-146">將項目發行至「PowerShell 資源庫」之前，有一些您必須針對程式碼執行的工具：</span><span class="sxs-lookup"><span data-stu-id="5ee5b-146">There are a few tools you need to run against your code before publishing your item to the PowerShell Gallery:</span></span>

- <span data-ttu-id="5ee5b-147">[PowerShell 指令碼分析程式](https://www.powershellgallery.com/packages/PSScriptAnalyzer/)：此工具位於「PowerShell 資源庫」中</span><span class="sxs-lookup"><span data-stu-id="5ee5b-147">[PowerShell Script Analyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer/), which is in the PowerShell Gallery</span></span>
- <span data-ttu-id="5ee5b-148">針對模組，請執行 Test-ModuleManifest，這包含在 PowerShell 中</span><span class="sxs-lookup"><span data-stu-id="5ee5b-148">For modules, Test-ModuleManifest which is part of PowerShell</span></span>
- <span data-ttu-id="5ee5b-149">針對指令碼，請執行 Test-ScriptFileInfo，這隨附於 PowerShell Get</span><span class="sxs-lookup"><span data-stu-id="5ee5b-149">For scripts, Test-ScriptFileInfo which comes with PowerShell Get</span></span>

<span data-ttu-id="5ee5b-150">[PowerShell 指令碼分析程式](https://www.powershellgallery.com/packages/PSScriptAnalyzer/) 是一個靜態的程式碼分析工具，會掃描您的程式碼以確保它符合基本的 PowerShell 程式碼編寫指導方針。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-150">[PowerShell Script Analyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer/) is a static code analysis tool that will scan your code to ensure it meets basic PowerShell coding guidelines.</span></span> <span data-ttu-id="5ee5b-151">此工具會識別您程式碼中的一般和重大問題，在開發期間應該定期執行，以協助您備妥項目以供發行。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-151">This tool will identify common and critical issues in your code, and should be run regularly during development to help you get your item ready to publish.</span></span>
<span data-ttu-id="5ee5b-152">「PowerShell 指令碼分析工具」會提供識別為「錯誤」、「警告」及「資訊」的問題清單。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-152">PowerShell Script Analyzer will provide list of issues identified as Errors, Warning, and Information.</span></span>
<span data-ttu-id="5ee5b-153">您必須解決所有錯誤，才能將項目發行至「PowerShell 資源庫」。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-153">All errors must be addressed before you publish to the PowerShell Gallery.</span></span> <span data-ttu-id="5ee5b-154">警告需要經過檢閱，且大多數都應該加以解決。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-154">Warnings need to be reviewed, and most should be addressed.</span></span>
<span data-ttu-id="5ee5b-155">每次在「PowerShell 資源庫」中發行或更新項目時，都會執行「PowerShell 指令碼分析工具」。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-155">PowerShell Script Analyzer is run every time an item is published or updated in the PowerShell Gallery.</span></span>
<span data-ttu-id="5ee5b-156">「資源庫作業」小組將會連絡項目擁有者來解決所發現的問題。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-156">The Gallery Operations team will contact item owners to address errors that are found.</span></span>

<span data-ttu-id="5ee5b-157">如果「PowerShell 資源庫」基礎結構無法讀取您項目中的資訊清單資訊，您將無法發行該項目。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-157">If the manifest information in your item cannot be read by the PowerShell Gallery infrastructure, you will not be able to publish.</span></span>
<span data-ttu-id="5ee5b-158">[Test-ModuleManifest](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-modulemanifest) 會捕捉將造成模組在安裝後無法使用的常見問題。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-158">[Test-ModuleManifest](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-modulemanifest) will catch common problems that would cause the module to not be usable when it is installed.</span></span> <span data-ttu-id="5ee5b-159">您必須先針對每個模組執行此 Cmdlet，才能將模組發行至「PowerShell 資源庫」。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-159">It must be run for every module prior to publishing it to the PowerShell Gallery.</span></span>

<span data-ttu-id="5ee5b-160">同樣地，[Test-ScriptFileInfo](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_test-scriptfileinfo) 會驗證指令碼中的資訊清單，且必須先在每個指令碼 (與模組個別發行) 上執行，才能將指令碼發行至「PowerShell 資源庫」。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-160">Likewise, [Test-ScriptFileInfo](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_test-scriptfileinfo) validates the metadata in a script, and must be run on every script (published separate from a module) prior to publishing it to the Powershell Gallery.</span></span>


## <a name="publishing-items"></a><span data-ttu-id="5ee5b-161">發行項目</span><span class="sxs-lookup"><span data-stu-id="5ee5b-161">Publishing Items</span></span>

<span data-ttu-id="5ee5b-162">您必須使用 [Publish-Script](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_publish-script) 或 [Publish-Module](https://msdn.microsoft.com/en-us/powershell/gallery/psget/module/psget_publish-module) 將項目發行至「PowerShell 資源庫」。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-162">You must use the [Publish-Script](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_publish-script) or [Publish-Module](https://msdn.microsoft.com/en-us/powershell/gallery/psget/module/psget_publish-module) to publish items to the PowerShell Gallery.</span></span>
<span data-ttu-id="5ee5b-163">這些命令都需要</span><span class="sxs-lookup"><span data-stu-id="5ee5b-163">These commands both require</span></span>

- <span data-ttu-id="5ee5b-164">您將發行之項目的路徑。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-164">The path to the item you will publish.</span></span> <span data-ttu-id="5ee5b-165">針對模組，請使用針對您模組命名的資料夾。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-165">For a module, use the folder named for your module.</span></span> <span data-ttu-id="5ee5b-166">如果您指定的資料夾包含同一個模組的多個版本，您就必須指定 RequiredVersion。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-166">If you specify a folder that contains multiple versions of the same module, you must specify RequiredVersion.</span></span>
- <span data-ttu-id="5ee5b-167">Nuget API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-167">A Nuget API key.</span></span> <span data-ttu-id="5ee5b-168">這是在「PowerShell 資源庫」上 [我的帳戶] 頁面中找到的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-168">This is the API key found in the My Account page on the PowerShell Gallery.</span></span>

<span data-ttu-id="5ee5b-169">命令列中大多數其他選項應該都在您要發行之項目的資訊清單資料中，因此您應該不需要在命令中指定它們。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-169">Most of the other options in the command line should be in the manifest data for the item you are publishing, so you should not need to specify them in the command.</span></span>

<span data-ttu-id="5ee5b-170">為了避免錯誤，強烈建議您在發行之前，先使用 -Whatif -Verbose 來嘗試執行命令。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-170">To avoid errors, it is strongly recommended that you try the commands using -Whatif -Verbose, before publishing.</span></span>
<span data-ttu-id="5ee5b-171">這將可大幅節省時間，因為每次您發行至「PowerShell 資源庫」時，都必須更新項目資訊清單區段中的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-171">This will save considerable time, since every time you publish to the PowerShell Gallery, you must update the version number in the manifest section of the item.</span></span>

<span data-ttu-id="5ee5b-172">範例：'Publish-Module -Path ".\MyModule" -RequiredVersion "0.0.1" -NugetAPIKey "GUID" -Whatif -Verbose' 'Publish-Script -Path ".\MyScriptFile.PS1" -NugetAPIKey "GUID" -Whatif -Verbose'</span><span class="sxs-lookup"><span data-stu-id="5ee5b-172">Examples would be: 'Publish-Module -Path ".\MyModule" -RequiredVersion "0.0.1" -NugetAPIKey "GUID" -Whatif -Verbose' 'Publish-Script -Path ".\MyScriptFile.PS1" -NugetAPIKey "GUID" -Whatif -Verbose'</span></span>

<span data-ttu-id="5ee5b-173">請小心檢閱輸出，如果沒看見任何錯誤或警告，請在不使用 -Whatif 的情況下重複執行該命令。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-173">Review the output carefully, and if you see no errors or warnings, repeat the command without -Whatif.</span></span>

<span data-ttu-id="5ee5b-174">系統會對所有發行至「PowerShell 資源庫」的項目進行病毒掃描，並使用「PowerShell 指令碼分析工具」進行分析。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-174">All items that are published to the PowerShell Gallery will be scanned for viruses, and will be analyzed using the PowerShell Script Analyzer.</span></span>
<span data-ttu-id="5ee5b-175">在該時間出現的所有問題都會傳回給發行者來進行解析。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-175">Any issues that arise at that time will be sent back to the publisher for resolution.</span></span>

<span data-ttu-id="5ee5b-176">將項目發行至「PowerShell 資源庫」之後，您將必須監看有關項目的意見反應。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-176">Once you have published an item to the PowerShell Gallery, you will need to watch for feedback on your item.</span></span>

- <span data-ttu-id="5ee5b-177">請務必監看與用來發行之帳戶相關的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-177">Ensure you monitor the email address associated with the account used to publish.</span></span>
<span data-ttu-id="5ee5b-178">使用者及「PowerShell 資源庫作業」小組將會透過提供該帳戶提供意見反應，包括來自 PSSA 或防毒軟體掃描的問題。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-178">Users, and the PowerShell Gallery Operations team will provide feedback via that account, including issues from the PSSA or antivirus scans.</span></span>
<span data-ttu-id="5ee5b-179">如果該電子郵件帳戶無效，或將嚴重問題回報給該帳戶而長時間未獲得解決，系統就可能將項目視為已遭捨棄，而將會如[使用規定](https://www.powershellgallery.com/policies/Terms)所述，從「PowerShell 資源庫」中移除。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-179">If the email account is invalid, or if serious issues are reported to the account and left unresolved for a long time, items can be considered abandoned and will be removed from the PowerShell Gallery as described in our [Terms of Use](https://www.powershellgallery.com/policies/Terms).</span></span>
- <span data-ttu-id="5ee5b-180">建議您訂閱您所發行之每個「PowerShell 資源庫」項目的「評論」。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-180">We recommend you subscribe to Comments for each PowerShell Gallery item you publish.</span></span>
<span data-ttu-id="5ee5b-181">如此一來，當任何使用者對您在「PowerShell 資源庫」中的項目提出評論時，您便會收到通知。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-181">This allows you to be notified if anyone comments on your items in the PowerShell Gallery.</span></span>
<span data-ttu-id="5ee5b-182">這是選擇性選項，因為這需要使用 LiveFyre 來建立帳戶。</span><span class="sxs-lookup"><span data-stu-id="5ee5b-182">This is optional, as it requires creating an account with LiveFyre.</span></span>