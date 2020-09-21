---
ms.date: 09/10/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 管理 API 金鑰
ms.openlocfilehash: c428689d065c63716db6bc546434623e9375f8ba
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87777587"
---
# <a name="managing-api-keys"></a><span data-ttu-id="593e3-103">管理 API 金鑰</span><span class="sxs-lookup"><span data-stu-id="593e3-103">Managing API keys</span></span>

<span data-ttu-id="593e3-104">PowerShell 資源庫支援建立多個 API 金鑰，以支援各種不同的發佈需求。</span><span class="sxs-lookup"><span data-stu-id="593e3-104">The PowerShell Gallery supports creating multiple API keys to support a range of publishing requirements.</span></span> <span data-ttu-id="593e3-105">API 金鑰可以套用至一或多個套件、會授與特定權限，而且具有到期日。</span><span class="sxs-lookup"><span data-stu-id="593e3-105">An API key can apply to one or more packages, grants specific privileges, and has an expiration date.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="593e3-106">使用者若未採用限域 API 金鑰就發佈至 PowerShell 資源庫，將會有「完整存取 API 金鑰」。</span><span class="sxs-lookup"><span data-stu-id="593e3-106">Users who published to the PowerShell Gallery prior to the introduction of scoped API keys will have a "Full access API key".</span></span> <span data-ttu-id="593e3-107">完整存取金鑰沒有限域 API 金鑰內建的安全性改善。</span><span class="sxs-lookup"><span data-stu-id="593e3-107">The full access keys do not have the security improvements built into scoped API keys.</span></span> <span data-ttu-id="593e3-108">完整存取金鑰永遠有效，而且會套用至使用者擁有的所有項目。</span><span class="sxs-lookup"><span data-stu-id="593e3-108">The full access keys never expires and apply to everything owned by the user.</span></span> <span data-ttu-id="593e3-109">如果您刪除此金鑰，則無法加以重新建立。</span><span class="sxs-lookup"><span data-stu-id="593e3-109">If you delete this key, it cannot be recreated.</span></span>

<span data-ttu-id="593e3-110">下圖顯示建立限域 API 金鑰時可以使用的選項。</span><span class="sxs-lookup"><span data-stu-id="593e3-110">The following image shows the options available when creating a scoped API key.</span></span>

![建立 API 金鑰](media/creating-APIkeys/PSGallery_KeyScoped.png)

<span data-ttu-id="593e3-112">在此範例中，我們建立了名為 **AzureRMDataFactory** 的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="593e3-112">In this example, we created an API key named **AzureRMDataFactory**.</span></span> <span data-ttu-id="593e3-113">此金鑰值可用來推送名稱開頭為 'AzureRM.DataFactory' 的套件，有效期限為 365 天。</span><span class="sxs-lookup"><span data-stu-id="593e3-113">This key value can be used to push packages with names that begin with 'AzureRM.DataFactory' and is valid for 365 days.</span></span> <span data-ttu-id="593e3-114">這是同一個組織中不同小組處理不同套件時的典型案例。</span><span class="sxs-lookup"><span data-stu-id="593e3-114">This is a typical scenario when different teams within the same organization work on different packages.</span></span> <span data-ttu-id="593e3-115">小組成員所擁有的金鑰會授與他們權限來存取其所處理的特定套件。</span><span class="sxs-lookup"><span data-stu-id="593e3-115">The members of the team have a key that grants them privileges for the specific package they work on.</span></span>
<span data-ttu-id="593e3-116">到期值可防止使用過時的金鑰或忘記金鑰。</span><span class="sxs-lookup"><span data-stu-id="593e3-116">The expiration value prevents the use of stale or forgotten keys.</span></span>

## <a name="using-glob-patterns"></a><span data-ttu-id="593e3-117">使用 Glob 模式</span><span class="sxs-lookup"><span data-stu-id="593e3-117">Using glob patterns</span></span>

<span data-ttu-id="593e3-118">如果您處理多個套件，您可以使用 Glob 模式將多個套件當作一個群組來比對。</span><span class="sxs-lookup"><span data-stu-id="593e3-118">If you work on multiple packages, you can use globbing patterns to match multiple packages as a group.</span></span> <span data-ttu-id="593e3-119">API 金鑰權限會套用至符合 Glob 模式的所有新套件。</span><span class="sxs-lookup"><span data-stu-id="593e3-119">API key permissions apply to all new packages matching the glob pattern.</span></span> <span data-ttu-id="593e3-120">例如，上一個範例使用 **Glob 模式** 值 'AzureRM.DataFactory\*'。</span><span class="sxs-lookup"><span data-stu-id="593e3-120">For example, the previous example uses a **Glob Pattern** value of 'AzureRM.DataFactory\*'.</span></span> <span data-ttu-id="593e3-121">由於套件符合 Glob 模式，因此您可以推送名為 'AzureRm.DataFactoryV2.Netcore' 的套件。</span><span class="sxs-lookup"><span data-stu-id="593e3-121">You can push a package named 'AzureRm.DataFactoryV2.Netcore' using this key since the package matches the glob pattern.</span></span>

## <a name="create-api-keys-securely"></a><span data-ttu-id="593e3-122">安全地建立 API 金鑰</span><span class="sxs-lookup"><span data-stu-id="593e3-122">Create API keys securely</span></span>

<span data-ttu-id="593e3-123">基於安全考量，新建立的金鑰值永遠不會顯示在畫面上，而且只能透過 [複製] 按鈕使用，如下所示。</span><span class="sxs-lookup"><span data-stu-id="593e3-123">For security, a newly created key value is never shown on the screen and is only available with the Copy button, as shown below.</span></span>

![取得新的 API 金鑰值](media/creating-APIkeys/PSGallery_CopyCreatedKey.png)

> [!IMPORTANT]
> <span data-ttu-id="593e3-125">您只能在建立或重新整理之後立即複製 API 金鑰值。</span><span class="sxs-lookup"><span data-stu-id="593e3-125">You can only copy the API key value immediately after creating or refreshing it.</span></span> <span data-ttu-id="593e3-126">該值不會顯示，而且在重新整理頁面之後將無法再次存取。</span><span class="sxs-lookup"><span data-stu-id="593e3-126">It will not be displayed, and will not be accessible again after the page is refreshed.</span></span> <span data-ttu-id="593e3-127">如果您遺失金鑰值，您必須使用 [重新產生]，並在重新產生金鑰之後加以複製。</span><span class="sxs-lookup"><span data-stu-id="593e3-127">If you lose the key value, you must use Regenerate, and copy the key after it is regenerated.</span></span>

## <a name="key-permissions-and-expiration"></a><span data-ttu-id="593e3-128">金鑰權限和到期日</span><span class="sxs-lookup"><span data-stu-id="593e3-128">Key permissions and expiration</span></span>

<span data-ttu-id="593e3-129">限域 API 金鑰可以指派下列任何權限：</span><span class="sxs-lookup"><span data-stu-id="593e3-129">Scoped API keys can assign any of the following permissions:</span></span>

- <span data-ttu-id="593e3-130">推送新的套件</span><span class="sxs-lookup"><span data-stu-id="593e3-130">Push new packages</span></span>
- <span data-ttu-id="593e3-131">推送新的套件或更新套件</span><span class="sxs-lookup"><span data-stu-id="593e3-131">Push new or update packages</span></span>
- <span data-ttu-id="593e3-132">取消列出套件</span><span class="sxs-lookup"><span data-stu-id="593e3-132">Unlist packages</span></span>

<span data-ttu-id="593e3-133">每個新金鑰都有到期日。</span><span class="sxs-lookup"><span data-stu-id="593e3-133">Every new key has an expiration.</span></span> <span data-ttu-id="593e3-134">到期值是以天為測量單位。</span><span class="sxs-lookup"><span data-stu-id="593e3-134">The expiration value is measured in days.</span></span> <span data-ttu-id="593e3-135">可能的到期值包括：</span><span class="sxs-lookup"><span data-stu-id="593e3-135">The possible values for expiration are:</span></span>

- <span data-ttu-id="593e3-136">1 日</span><span class="sxs-lookup"><span data-stu-id="593e3-136">1 day</span></span>
- <span data-ttu-id="593e3-137">90 天</span><span class="sxs-lookup"><span data-stu-id="593e3-137">90 days</span></span>
- <span data-ttu-id="593e3-138">180 天</span><span class="sxs-lookup"><span data-stu-id="593e3-138">180 days</span></span>
- <span data-ttu-id="593e3-139">270 天</span><span class="sxs-lookup"><span data-stu-id="593e3-139">270 days</span></span>
- <span data-ttu-id="593e3-140">365 天 (預設值)</span><span class="sxs-lookup"><span data-stu-id="593e3-140">365 days (default)</span></span>

<span data-ttu-id="593e3-141">一旦建立金鑰，就無法變更這些設定。</span><span class="sxs-lookup"><span data-stu-id="593e3-141">These settings cannot be changed once the key is created.</span></span> <span data-ttu-id="593e3-142">您無法建立永遠有效的新金鑰。</span><span class="sxs-lookup"><span data-stu-id="593e3-142">You cannot create a new key that never expires.</span></span>

## <a name="editing-and-deleting-existing-api-keys"></a><span data-ttu-id="593e3-143">編輯和刪除現有的 API 金鑰</span><span class="sxs-lookup"><span data-stu-id="593e3-143">Editing and deleting existing API keys</span></span>

<span data-ttu-id="593e3-144">您可以變更現有金鑰的某些設定。</span><span class="sxs-lookup"><span data-stu-id="593e3-144">You can change some settings of an existing key.</span></span> <span data-ttu-id="593e3-145">如前所述，您無法修改現有 API 金鑰的安全性範圍，或變更到期日。</span><span class="sxs-lookup"><span data-stu-id="593e3-145">As previously noted, you cannot modify the security scope for an existing API key or change the expiration.</span></span> <span data-ttu-id="593e3-146">下列螢幕擷取畫面顯示可變更的選項：</span><span class="sxs-lookup"><span data-stu-id="593e3-146">The changeable options are shown in the following screenshot:</span></span>

![編輯 API 金鑰值](media/creating-APIkeys/PSGallery_EditAPIKey.png)

<span data-ttu-id="593e3-148">若要變更受金鑰控制的套件，您可以從清單中選擇個別套件，或變更 Glob 模式。</span><span class="sxs-lookup"><span data-stu-id="593e3-148">To change the packages controlled by a key, you can choose individual packages from the list or change the glob pattern.</span></span>

<span data-ttu-id="593e3-149">按一下 [重新產生]  會建立新的金鑰值。</span><span class="sxs-lookup"><span data-stu-id="593e3-149">Clicking **Regenerate** creates a new key value.</span></span> <span data-ttu-id="593e3-150">如同初始建立金鑰，您必須在更新金鑰之後**複製**其值。</span><span class="sxs-lookup"><span data-stu-id="593e3-150">Just like when you initially created the key, you must **Copy** the key value immediately after updating it.</span></span> <span data-ttu-id="593e3-151">一旦離開此頁面，就無法使用 [複製]  選項。</span><span class="sxs-lookup"><span data-stu-id="593e3-151">The **Copy** option is not available once you leave this page.</span></span>

<span data-ttu-id="593e3-152">按一下 [刪除]  會顯示確認訊息。</span><span class="sxs-lookup"><span data-stu-id="593e3-152">Clicking **Delete** displays a confirmation message.</span></span> <span data-ttu-id="593e3-153">金鑰一旦刪除，就無法使用。</span><span class="sxs-lookup"><span data-stu-id="593e3-153">Once a key is deleted, it will be unusable.</span></span>

## <a name="key-expiration"></a><span data-ttu-id="593e3-154">金鑰到期日</span><span class="sxs-lookup"><span data-stu-id="593e3-154">Key expiration</span></span>

<span data-ttu-id="593e3-155">在到期十天前，PowerShell 資源庫會傳送警告電子郵件給 API 金鑰的帳戶持有人。</span><span class="sxs-lookup"><span data-stu-id="593e3-155">Ten days before the expiration, the PowerShell Gallery sends a warning email the account holder of the API key.</span></span> <span data-ttu-id="593e3-156">到期後，金鑰將無法使用。</span><span class="sxs-lookup"><span data-stu-id="593e3-156">After expiration, the key is unusable.</span></span> <span data-ttu-id="593e3-157">API 金鑰管理頁面頂端會出現一則警告訊息，顯示哪些金鑰不再有效。</span><span class="sxs-lookup"><span data-stu-id="593e3-157">A warning message is displayed at the top of the API key management page showing which keys are no longer valid.</span></span> <span data-ttu-id="593e3-158">您可以產生新的金鑰值。</span><span class="sxs-lookup"><span data-stu-id="593e3-158">You can generate a new key value.</span></span>
