---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 管理套件擁有者
ms.openlocfilehash: 72a3ff72818c5461c74d46de5689e2d6c59b19bf
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564664"
---
# <a name="managing-package-owners"></a><span data-ttu-id="8249d-103">管理套件擁有者</span><span class="sxs-lookup"><span data-stu-id="8249d-103">Managing package owners</span></span>

<span data-ttu-id="8249d-104">PowerShell 資源庫中套件的擁有權，是由將該套件發行到資源庫的人所定義。</span><span class="sxs-lookup"><span data-stu-id="8249d-104">Ownership of a package in the PowerShell Gallery is defined by who published the package to the gallery.</span></span>
<span data-ttu-id="8249d-105">有時候，這個中繼資料必須在初步發行套件之後另外管理，這表示擁有者中繼資料必須能在不變動套件的情況下進行變動。</span><span class="sxs-lookup"><span data-stu-id="8249d-105">Sometimes this metadata needs to be managed beyond the initial package publishing, which means the owner metadata needs to be mutable while the package itself is not.</span></span>

<span data-ttu-id="8249d-106">所有的套件擁有者都是對等的。</span><span class="sxs-lookup"><span data-stu-id="8249d-106">All package owners are peers.</span></span>
<span data-ttu-id="8249d-107">這表示任何套件擁有者均可發行新版本的套件。</span><span class="sxs-lookup"><span data-stu-id="8249d-107">This means any package owner can publish a new version of an package.</span></span> <span data-ttu-id="8249d-108">這也表示任何套件擁有者都可以移除任何其他的套件擁有者。</span><span class="sxs-lookup"><span data-stu-id="8249d-108">It also means that any package owner can remove any other package owner.</span></span>
<span data-ttu-id="8249d-109">沒有任何擁有者的權限高於其他擁有者。</span><span class="sxs-lookup"><span data-stu-id="8249d-109">No owner has more authority than other owners.</span></span>

## <a name="setting-a-packages-initial-owner"></a><span data-ttu-id="8249d-110">設定套件的初始擁有者</span><span class="sxs-lookup"><span data-stu-id="8249d-110">Setting a Package's Initial Owner</span></span>

<span data-ttu-id="8249d-111">當新的套件發行到 PowerShell 資源庫時，會依發行該套件的使用者來定義初始擁有者。</span><span class="sxs-lookup"><span data-stu-id="8249d-111">When a new package is published to PowerShell Gallery, the initial owner is defined by the user that published the package.</span></span> <span data-ttu-id="8249d-112">這取決於 Publish-Module cmdlet 中使用了誰的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="8249d-112">This is determined by whose API key was used in the Publish-Module cmdlet.</span></span>

## <a name="adding-owners"></a><span data-ttu-id="8249d-113">新增擁有者</span><span class="sxs-lookup"><span data-stu-id="8249d-113">Adding Owners</span></span>

<span data-ttu-id="8249d-114">一旦將套件發行到 PowerShell 資源庫，就能輕易邀請其他使用者成為套件擁有者。</span><span class="sxs-lookup"><span data-stu-id="8249d-114">Once a package has been published to the PowerShell Gallery, it's easy to invite additional users to become owners of a package.</span></span>

1. <span data-ttu-id="8249d-115">使用套件目前擁有者的帳戶[登入](https://powershellgallery.com/users/account/LogOn) \(英文\) PowerShell 資源庫。</span><span class="sxs-lookup"><span data-stu-id="8249d-115">[Log on](https://powershellgallery.com/users/account/LogOn) to the PowerShell Gallery with the account that is the current owner of a package.</span></span>
2. <span data-ttu-id="8249d-116">使用 [Items] \(項目\) 索引標籤瀏覽到套件頁面，然後搜尋或按一下您的使用者名稱，並按一下 [[Manage My Packages]  ](https://www.powershellgallery.com/account/Packages) \(管理我的項目\) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="8249d-116">Navigate to a package page using the 'Items' tab, searching, or clicking your username and then [**Manage My Packages**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="8249d-117">以套件擁有者身分登入時，左側會有可按一下的 [Manage Owners] \(管理擁有者\) 連結。</span><span class="sxs-lookup"><span data-stu-id="8249d-117">When logged on as an package's owner, there is a 'Manage Owners' link on the left side to click.</span></span>
4. <span data-ttu-id="8249d-118">輸入要新增為擁有者的人員使用者名稱，然後按一下 [新增]。</span><span class="sxs-lookup"><span data-stu-id="8249d-118">Enter the username of the person to add as an owner and click 'Add'.</span></span>
5. <span data-ttu-id="8249d-119">新的共同擁有者接著便會收到電子郵件，邀請他成為套件擁有者。</span><span class="sxs-lookup"><span data-stu-id="8249d-119">An email is then sent to the new co-owner, as an invitation to become an owner of a package.</span></span>
6. <span data-ttu-id="8249d-120">使用者按一下連結後便能成為完整的共同擁有者，並對套件有完整控制權，包括能夠移除其他身為擁有者的使用者。</span><span class="sxs-lookup"><span data-stu-id="8249d-120">Once that user clicks the link, they are a full co-owner with full control over a package, including the ability to remove other users as owners.</span></span>

<span data-ttu-id="8249d-121">**注意**：在新擁有者確認擁有權之前，其將「不會」  被列為套件的擁有者。</span><span class="sxs-lookup"><span data-stu-id="8249d-121">**NOTE**: Until the new owner confirms ownership, they *will not* be listed as an owner of a package.</span></span>
<span data-ttu-id="8249d-122">檢視 [管理擁有者]  頁面時，您會在目前的使用者看到「等待核准」項目。</span><span class="sxs-lookup"><span data-stu-id="8249d-122">When viewing the **Manage Owners** page, you will see a "pending approval" entry in the current owners.</span></span>
<span data-ttu-id="8249d-123">該邀請可被移除；就像其他擁有者也可被移除。</span><span class="sxs-lookup"><span data-stu-id="8249d-123">That invitation can be removed; just as other owners can be removed.</span></span>
<span data-ttu-id="8249d-124">此邀請程序可防止使用者將其他使用者誤加為套件擁有者。</span><span class="sxs-lookup"><span data-stu-id="8249d-124">This process of invitations prevents users from falsely adding other users as owners of their packages.</span></span>

<span data-ttu-id="8249d-125">請注意，"Authors" 中繼資料單純為自由格式的文字，只有 "Owners" 受到控制。</span><span class="sxs-lookup"><span data-stu-id="8249d-125">Note that the "Authors" metadata is purely freeform text; only "Owners" are controlled.</span></span>

## <a name="removing-owners"></a><span data-ttu-id="8249d-126">移除擁有者</span><span class="sxs-lookup"><span data-stu-id="8249d-126">Removing Owners</span></span>

<span data-ttu-id="8249d-127">當套件有多個擁有者，而需要移除其中一個時，程序很簡單：</span><span class="sxs-lookup"><span data-stu-id="8249d-127">When a package has multiple owners and one needs to be removed, the process is simple:</span></span>

1. <span data-ttu-id="8249d-128">使用套件目前擁有者的帳戶[登入](https://powershellgallery.com/users/account/LogOn) \(英文\) PowerShell 資源庫；</span><span class="sxs-lookup"><span data-stu-id="8249d-128">[Log on](https://powershellgallery.com/users/account/LogOn) to PowerShell Gallery with the account that is the current owner of a package;</span></span>
2. <span data-ttu-id="8249d-129">使用 [Packages] \(套件\) 索引標籤瀏覽到套件頁面，然後搜尋或按一下您的使用者名稱，並按一下 [[Manage My Packages]  ](https://www.powershellgallery.com/account/Packages) \(管理我的項目\) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="8249d-129">Navigate to a package page using the Packages tab, searching, or clicking your username and then [**Manage My Packages**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="8249d-130">以套件擁有者身分登入時，左側會有可按一下的 [Manage Owners] \(管理擁有者\) 連結。</span><span class="sxs-lookup"><span data-stu-id="8249d-130">When logged on as a package's owner, there is a 'Manage Owners' link on the left side to click;</span></span>
4. <span data-ttu-id="8249d-131">在要移除的擁有者旁按一下 [移除] 連結。</span><span class="sxs-lookup"><span data-stu-id="8249d-131">Click the 'remove' link next to the owner to be removed.</span></span>

## <a name="transferring-package-ownership"></a><span data-ttu-id="8249d-132">移轉套件擁有權</span><span class="sxs-lookup"><span data-stu-id="8249d-132">Transferring Package Ownership</span></span>

<span data-ttu-id="8249d-133">我們有時候會收到想要將套件擁有權從一個使用者移轉到另一個使用者的支援要求，但使用者在大多數的情況下都可以自行完成此工作。</span><span class="sxs-lookup"><span data-stu-id="8249d-133">We sometimes get support requests to transfer package ownership from one user to another, but you can almost always accomplish this yourself.</span></span>
<span data-ttu-id="8249d-134">只要結合上述兩項功能，就能將擁有權從一位使用者移轉給另一位。</span><span class="sxs-lookup"><span data-stu-id="8249d-134">Transferring ownership from one user to another is simply a combination of the two features above.</span></span>

1. <span data-ttu-id="8249d-135">目前擁有者邀請新使用者成為共同擁有者，然後心使用者接受邀請；</span><span class="sxs-lookup"><span data-stu-id="8249d-135">The current owner invites the new user to become a co-owner and the new user accepts the invite;</span></span>
2. <span data-ttu-id="8249d-136">新使用者從擁有者清單移除舊使用者。</span><span class="sxs-lookup"><span data-stu-id="8249d-136">The new user removes the old user from the list of owners.</span></span>

<span data-ttu-id="8249d-137">此要求源於多種形式，但程序運作方式都一樣。</span><span class="sxs-lookup"><span data-stu-id="8249d-137">This request has come in under a couple forms but the process works the same.</span></span>

- <span data-ttu-id="8249d-138">套件擁有權正從一個開發人員變更至另一個開發人員</span><span class="sxs-lookup"><span data-stu-id="8249d-138">The package ownership is changing from one developer to another</span></span>
- <span data-ttu-id="8249d-139">意外使用錯誤帳戶發行套件</span><span class="sxs-lookup"><span data-stu-id="8249d-139">The package was accidentally published using the wrong account</span></span>

## <a name="orphaned-packages"></a><span data-ttu-id="8249d-140">孤立的套件</span><span class="sxs-lookup"><span data-stu-id="8249d-140">Orphaned Packages</span></span>

<span data-ttu-id="8249d-141">發生了最後一個案例，但不常發生。</span><span class="sxs-lookup"><span data-stu-id="8249d-141">One last scenario has occurred, but not many times.</span></span>
<span data-ttu-id="8249d-142">套件已被孤立，且無法使用唯一的套件擁有者帳戶來新增擁有者。</span><span class="sxs-lookup"><span data-stu-id="8249d-142">Packages have become orphans and the only package owner account cannot be used to add new owners.</span></span>
<span data-ttu-id="8249d-143">這裡有這個案例的一些範例：</span><span class="sxs-lookup"><span data-stu-id="8249d-143">Here are some examples of this scenario:</span></span>

- <span data-ttu-id="8249d-144">擁有者帳戶與已不存在的電子郵件地址建立關聯，且使用者忘記密碼</span><span class="sxs-lookup"><span data-stu-id="8249d-144">The owner's account is associated with an email address that no longer exists and the user has forgotten their password</span></span>
- <span data-ttu-id="8249d-145">註冊的擁有者已離開生產該套件的公司且已經失聯，因而無法更新套件擁有權</span><span class="sxs-lookup"><span data-stu-id="8249d-145">The registered owner has left the company that produces the package and cannot be reached to update the package ownership</span></span>
- <span data-ttu-id="8249d-146">由於一個只會影響少數套件的錯誤 (bug)，使得該套件在資源庫上沒有任何擁有者</span><span class="sxs-lookup"><span data-stu-id="8249d-146">Due to a bug that has only affected a handful of packages, the package is somehow ownerless on the gallery</span></span>

<span data-ttu-id="8249d-147">PowerShell 資源庫系統管理員可存取任何套件的 [Manage Owners] \(管理擁有者\) 連結。</span><span class="sxs-lookup"><span data-stu-id="8249d-147">The PowerShell Gallery Administrators can access the 'Manage Owners' link for any package.</span></span>
<span data-ttu-id="8249d-148">如果您是套件的正當擁有者，但無法連絡到目前的擁有者以取得擁有權權限，請使用資源庫上的 [Report Abuse] \(檢舉不當使用\) 連結來連絡 PowerShell 資源庫系統管理員。</span><span class="sxs-lookup"><span data-stu-id="8249d-148">If you are the rightful owner of a package and cannot reach the current owner to gain ownership permissions, then use the 'Report Abuse' link on the gallery to reach the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="8249d-149">我們會進行驗證您對該套件之擁有權的程序。</span><span class="sxs-lookup"><span data-stu-id="8249d-149">We will then follow a process to verify your ownership of the package.</span></span>
<span data-ttu-id="8249d-150">如果我們判斷您是該套件的擁有者，就會使用該套件的 [Manage Owners] \(管理擁有者\) 連結，並傳送成為擁有者的邀請給您。</span><span class="sxs-lookup"><span data-stu-id="8249d-150">If we determine you should be an owner of the package, we will use the 'Manage Owners' link for the package ourselves and send you the invite to become an owner.</span></span>
<span data-ttu-id="8249d-151">我們只會在驗證您應為擁有者後這樣做，而且其程序會因情況而有所不同。</span><span class="sxs-lookup"><span data-stu-id="8249d-151">We will only do this after verifying that you should be an owner and the process for this varies by circumstances.</span></span>
<span data-ttu-id="8249d-152">通常，我們會使用套件的專案 URL 來尋找連絡專案擁有者的方法，但我們可能也會使用 Twitter、電子郵件或其他方法來連絡專案擁有者。</span><span class="sxs-lookup"><span data-stu-id="8249d-152">Often times, we will use the package's Project URL to find a way to contact the project owner, but we may also use Twitter, Email, or other means for contacting the project owner.</span></span>
