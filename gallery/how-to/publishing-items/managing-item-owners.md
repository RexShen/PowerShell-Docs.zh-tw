---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: 管理項目擁有者
ms.openlocfilehash: 20380972ffe365ec9a479073fdf7e7f0eb1ee34e
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
---
# <a name="managing-item-owners"></a><span data-ttu-id="3e2c2-103">管理項目擁有者</span><span class="sxs-lookup"><span data-stu-id="3e2c2-103">Managing item owners</span></span>

<span data-ttu-id="3e2c2-104">PowerShell 資源庫中的項目擁有權由將該項目發行到資源庫的人定義。</span><span class="sxs-lookup"><span data-stu-id="3e2c2-104">Ownership of an item in the PowerShell Gallery is defined by who published the item to the gallery.</span></span>
<span data-ttu-id="3e2c2-105">有時候，這個中繼資料必須在初步發行項目時另外受到管理，這表示擁有者中繼資料必須可變動，項目本身則不可變動。</span><span class="sxs-lookup"><span data-stu-id="3e2c2-105">Sometimes this metadata needs to be managed beyond the initial item publishing, which means the owner metadata needs to be mutable while the item itself is not.</span></span>

<span data-ttu-id="3e2c2-106">所有項目擁有者均為同儕。</span><span class="sxs-lookup"><span data-stu-id="3e2c2-106">All item owners are peers.</span></span>
<span data-ttu-id="3e2c2-107">這表示任何項目擁有者均可發行新版本的項目。</span><span class="sxs-lookup"><span data-stu-id="3e2c2-107">This means any item owner can publish a new version of an item.</span></span> <span data-ttu-id="3e2c2-108">而且任何項目擁有者也都可以移除其他任何項目擁有者。</span><span class="sxs-lookup"><span data-stu-id="3e2c2-108">It also means that any item owner can remove any other item owner.</span></span>
<span data-ttu-id="3e2c2-109">沒有任何擁有者的權限高於其他擁有者。</span><span class="sxs-lookup"><span data-stu-id="3e2c2-109">No owner has more authority than other owners.</span></span>

## <a name="setting-an-items-initial-owner"></a><span data-ttu-id="3e2c2-110">設定項目的初始擁有者</span><span class="sxs-lookup"><span data-stu-id="3e2c2-110">Setting an Item's Initial Owner</span></span>

<span data-ttu-id="3e2c2-111">當新的項目發行到 PowerShell 資源庫時，會由發行該項目的使用者定義初始擁有者。</span><span class="sxs-lookup"><span data-stu-id="3e2c2-111">When a new item is published to PowerShell Gallery, the initial owner is defined by the user that published the item.</span></span> <span data-ttu-id="3e2c2-112">這取決於 Publish-Module cmdlet 中使用了誰的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="3e2c2-112">This is determined by whose API key was used in the Publish-Module cmdlet.</span></span>

## <a name="adding-owners"></a><span data-ttu-id="3e2c2-113">新增擁有者</span><span class="sxs-lookup"><span data-stu-id="3e2c2-113">Adding Owners</span></span>

<span data-ttu-id="3e2c2-114">一旦將項目發行到 PowerShell 資源庫，就能輕易邀請其他使用者成為項目擁有者。</span><span class="sxs-lookup"><span data-stu-id="3e2c2-114">Once an item has been published to the PowerShell Gallery, it's easy to invite additional users to become owners of an item.</span></span>

1. <span data-ttu-id="3e2c2-115">使用項目目前擁有者的帳戶[登入](https://powershellgallery.com/users/account/LogOn) PowerShell 資源庫。</span><span class="sxs-lookup"><span data-stu-id="3e2c2-115">[Log on](https://powershellgallery.com/users/account/LogOn) to the PowerShell Gallery with the account that is the current owner of an item.</span></span>
2. <span data-ttu-id="3e2c2-116">使用 [項目] 索引標籤瀏覽到項目頁面，進行搜尋或依序按一下您的使用者名稱及 [**[管理我的項目]**](https://www.powershellgallery.com/account/Packages)。</span><span class="sxs-lookup"><span data-stu-id="3e2c2-116">Navigate to an item page using the 'Items' tab, searching, or clicking your username and then [**Manage My Items**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="3e2c2-117">以項目擁有者身分登入時，左側會有 [管理擁有者] 連結可點選。</span><span class="sxs-lookup"><span data-stu-id="3e2c2-117">When logged on as an item's owner, there is a 'Manage Owners' link on the left side to click.</span></span>
4. <span data-ttu-id="3e2c2-118">輸入要新增為擁有者的人員使用者名稱，然後按一下 [新增]。</span><span class="sxs-lookup"><span data-stu-id="3e2c2-118">Enter the username of the person to add as an owner and click 'Add'.</span></span>
5. <span data-ttu-id="3e2c2-119">新的共同擁有者接著便會收到電子郵件，即成為項目擁有者的邀請。</span><span class="sxs-lookup"><span data-stu-id="3e2c2-119">An email is then sent to the new co-owner, as an invitation to become an owner of an item.</span></span>
6. <span data-ttu-id="3e2c2-120">使用者按一下連結後即成為正式共同擁有者，對項目有完整控制權，包括能夠移除其他身為擁有者的使用者。</span><span class="sxs-lookup"><span data-stu-id="3e2c2-120">Once that user clicks the link, they are a full co-owner with full control over an item, including the ability to remove other users as owners.</span></span>

<span data-ttu-id="3e2c2-121">**注意**：在新擁有者確認擁有權之前，他們「不會」列為項目的擁有者。</span><span class="sxs-lookup"><span data-stu-id="3e2c2-121">**NOTE**: Until the new owner confirms ownership, they *will not* be listed as an owner of an item.</span></span>
<span data-ttu-id="3e2c2-122">檢視 [管理擁有者] 頁面時，您會在目前的使用者看到「等待核准」項目。</span><span class="sxs-lookup"><span data-stu-id="3e2c2-122">When viewing the **Manage Owners** page, you will see a "pending approval" entry in the current owners.</span></span>
<span data-ttu-id="3e2c2-123">該邀請可被移除；就像其他擁有者也可被移除。</span><span class="sxs-lookup"><span data-stu-id="3e2c2-123">That invitation can be removed; just as other owners can be removed.</span></span>
<span data-ttu-id="3e2c2-124">此邀請程序可防止使用者將其他使用者誤加為項目擁有者。</span><span class="sxs-lookup"><span data-stu-id="3e2c2-124">This process of invitations prevents users from falsely adding other users as owners of their items.</span></span>

<span data-ttu-id="3e2c2-125">請注意，"Authors" 中繼資料單純為自由格式的文字，只有 "Owners" 受到控制。</span><span class="sxs-lookup"><span data-stu-id="3e2c2-125">Note that the "Authors" metadata is purely freeform text; only "Owners" are controlled.</span></span>


## <a name="removing-owners"></a><span data-ttu-id="3e2c2-126">移除擁有者</span><span class="sxs-lookup"><span data-stu-id="3e2c2-126">Removing Owners</span></span>

<span data-ttu-id="3e2c2-127">當項目有多個擁有者，而需要移除其中一個時，程序很簡單：</span><span class="sxs-lookup"><span data-stu-id="3e2c2-127">When an item has multiple owners and one needs to be removed, the process is simple:</span></span>

1. <span data-ttu-id="3e2c2-128">使用項目目前擁有者的帳戶[登入](https://powershellgallery.com/users/account/LogOn) PowerShell 資源庫；</span><span class="sxs-lookup"><span data-stu-id="3e2c2-128">[Log on](https://powershellgallery.com/users/account/LogOn) to PowerShell Gallery with the account that is the current owner of an item;</span></span>
2. <span data-ttu-id="3e2c2-129">使用 [項目] 索引標籤瀏覽到項目頁面，進行搜尋或依序按一下您的使用者名稱及 [**[管理我的項目]**](https://www.powershellgallery.com/account/Packages)。</span><span class="sxs-lookup"><span data-stu-id="3e2c2-129">Navigate to an item page using the Items tab, searching, or clicking your username and then [**Manage My Items**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="3e2c2-130">以項目擁有者身分登入時，左側會有 [管理擁有者] 連結可點選；</span><span class="sxs-lookup"><span data-stu-id="3e2c2-130">When logged on as an item's owner, there is a 'Manage Owners' link on the left side to click;</span></span>
4. <span data-ttu-id="3e2c2-131">在要移除的擁有者旁按一下 [移除] 連結。</span><span class="sxs-lookup"><span data-stu-id="3e2c2-131">Click the 'remove' link next to the owner to be removed.</span></span>



## <a name="transferring-item-ownership"></a><span data-ttu-id="3e2c2-132">移轉項目擁有權</span><span class="sxs-lookup"><span data-stu-id="3e2c2-132">Transferring Item Ownership</span></span>

<span data-ttu-id="3e2c2-133">我們有時候會收到將項目擁有權從一名使用者移轉到另一名的支援要求，但您幾乎可以隨時自行完成。</span><span class="sxs-lookup"><span data-stu-id="3e2c2-133">We sometimes get support requests to transfer item ownership from one user to another, but you can almost always accomplish this yourself.</span></span>
<span data-ttu-id="3e2c2-134">只要結合上述兩項功能，就能將擁有權從一位使用者移轉給另一位。</span><span class="sxs-lookup"><span data-stu-id="3e2c2-134">Transferring ownership from one user to another is simply a combination of the two features above.</span></span>

1. <span data-ttu-id="3e2c2-135">目前擁有者邀請新使用者成為共同擁有者，然後心使用者接受邀請；</span><span class="sxs-lookup"><span data-stu-id="3e2c2-135">The current owner invites the new user to become a co-owner and the new user accepts the invite;</span></span>
2. <span data-ttu-id="3e2c2-136">新使用者從擁有者清單移除舊使用者。</span><span class="sxs-lookup"><span data-stu-id="3e2c2-136">The new user removes the old user from the list of owners.</span></span>

<span data-ttu-id="3e2c2-137">此要求源於多種形式，但程序運作方式都一樣。</span><span class="sxs-lookup"><span data-stu-id="3e2c2-137">This request has come in under a couple forms but the process works the same.</span></span>

- <span data-ttu-id="3e2c2-138">項目擁有權正從一名開發人員變更為另一名</span><span class="sxs-lookup"><span data-stu-id="3e2c2-138">The item ownership is changing from one developer to another</span></span>
- <span data-ttu-id="3e2c2-139">意外使用錯誤帳戶發行了項目</span><span class="sxs-lookup"><span data-stu-id="3e2c2-139">The item was accidentally published using the wrong account</span></span>


## <a name="orphaned-items"></a><span data-ttu-id="3e2c2-140">孤立的項目</span><span class="sxs-lookup"><span data-stu-id="3e2c2-140">Orphaned Items</span></span>

<span data-ttu-id="3e2c2-141">發生了最後一個案例，但不常發生。</span><span class="sxs-lookup"><span data-stu-id="3e2c2-141">One last scenario has occurred, but not many times.</span></span>
<span data-ttu-id="3e2c2-142">項目已被孤立，而無法使用唯一的項目擁有者帳戶新增使用者。</span><span class="sxs-lookup"><span data-stu-id="3e2c2-142">Items have become orphans and the only item owner account cannot be used to add new owners.</span></span>
<span data-ttu-id="3e2c2-143">這裡有這個案例的一些範例：</span><span class="sxs-lookup"><span data-stu-id="3e2c2-143">Here are some examples of this scenario:</span></span>

- <span data-ttu-id="3e2c2-144">擁有者帳戶與已不存在的電子郵件地址建立關聯，且使用者忘記密碼</span><span class="sxs-lookup"><span data-stu-id="3e2c2-144">The owner's account is associated with an email address that no longer exists and the user has forgotten their password</span></span>
- <span data-ttu-id="3e2c2-145">註冊的擁有者已離開產生項目的公司，而無法更新項目擁有權</span><span class="sxs-lookup"><span data-stu-id="3e2c2-145">The registered owner has left the company that produces the item and cannot be reached to update the item ownership</span></span>
- <span data-ttu-id="3e2c2-146">由於一個只影響了少數項目的錯誤，項目在資源庫沒有擁有權</span><span class="sxs-lookup"><span data-stu-id="3e2c2-146">Due to a bug that has only affected a handful of items, the item is somehow ownerless on the gallery</span></span>

<span data-ttu-id="3e2c2-147">PowerShell 資源庫系統管理員可存取任何項目的 [管理擁有者] 連結。</span><span class="sxs-lookup"><span data-stu-id="3e2c2-147">The PowerShell Gallery Administrators can access the 'Manage Owners' link for any item.</span></span>
<span data-ttu-id="3e2c2-148">如果您是項目的正當擁有者，但無法連絡到目前擁有者以取得擁有權權限，就使用資源庫的 [檢舉不當使用] 連結連絡 PowerShell 資源庫系統管理員。</span><span class="sxs-lookup"><span data-stu-id="3e2c2-148">If you are the rightful owner of a item and cannot reach the current owner to gain ownership permissions, then use the 'Report Abuse' link on the gallery to reach the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="3e2c2-149">我們會遵循一套程序驗證您的項目擁有權。</span><span class="sxs-lookup"><span data-stu-id="3e2c2-149">We will then follow a process to verify your ownership of the item.</span></span>
<span data-ttu-id="3e2c2-150">如果我們判斷您應為項目擁有者，就會自行使用項目的 [管理擁有者] 連結，並傳送成為擁有者的邀請給您。</span><span class="sxs-lookup"><span data-stu-id="3e2c2-150">If we determine you should be an owner of the item, we will use the 'Manage Owners' link for the item ourselves and send you the invite to become an owner.</span></span>
<span data-ttu-id="3e2c2-151">我們只會在驗證您應為擁有者後這樣做，而且其程序會因情況而有所不同。</span><span class="sxs-lookup"><span data-stu-id="3e2c2-151">We will only do this after verifying that you should be an owner and the process for this varies by circumstances.</span></span>
<span data-ttu-id="3e2c2-152">通常，我們會使用項目的專案 URL 找到連絡專案擁有者的方法，但我們可能也會使用 Twitter、電子郵件或其他方式連絡專案擁有者。</span><span class="sxs-lookup"><span data-stu-id="3e2c2-152">Often times, we will use the item's Project URL to find a way to contact the project owner, but we may also use Twitter, Email, or other means for contacting the project owner.</span></span>