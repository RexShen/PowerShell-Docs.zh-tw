---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 透過社交媒體或留言提供意見反應
ms.openlocfilehash: a7cdcc2ff2c18fb606d077adf0bdecf57c90703f
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003695"
---
# <a name="providing-feedback-via-social-media-or-comments"></a><span data-ttu-id="b90e9-103">透過社交媒體或留言提供意見反應</span><span class="sxs-lookup"><span data-stu-id="b90e9-103">Providing Feedback via social media or comments</span></span>

<span data-ttu-id="b90e9-104">PowerShell 資源庫支援兩種方法，可供使用者針對套件提供公開意見反應：</span><span class="sxs-lookup"><span data-stu-id="b90e9-104">The Powershell Gallery supports two approaches for users to provide public feedback on a package:</span></span>

- <span data-ttu-id="b90e9-105">使用左邊緣上的連結，以在 Facebook、LinkedIn 或 Twitter 等社交媒體網站中 [Share] \(分享\) 該套件；</span><span class="sxs-lookup"><span data-stu-id="b90e9-105">Use the links on the left edge to "share" a package in Facebook, LinkedIn, or Twitter social media sites;</span></span>
- <span data-ttu-id="b90e9-106">使用 [Comment] \(評論\) 功能來針對套件張貼評論，並允許作者監看自己所發行之套件的相關評論。</span><span class="sxs-lookup"><span data-stu-id="b90e9-106">Use the Comment feature to post comments on a package, and to allow Authors to watch for comments on packages they publish.</span></span>

## <a name="social-media-feedback"></a><span data-ttu-id="b90e9-107">社交媒體意見反應</span><span class="sxs-lookup"><span data-stu-id="b90e9-107">Social Media Feedback</span></span>

<span data-ttu-id="b90e9-108">在 PowerShell 資源庫中每個套件頁面的左側，會有 Facebook、LinkedIn 及 Twitter 的連結。</span><span class="sxs-lookup"><span data-stu-id="b90e9-108">On the left side of the page for each package in the PowerShell Gallery there are links for Facebook, LinkedIn, and Twitter.</span></span>
<span data-ttu-id="b90e9-109">按一下這些連結將會開啟社交媒體網站，並可快速分享套件的連結。</span><span class="sxs-lookup"><span data-stu-id="b90e9-109">Clicking on these links will open the social media site, and allow quickly sharing a link to the package.</span></span>

<span data-ttu-id="b90e9-110">使用者必須登入所選擇的網站，才能分享 PowerShell 資源庫套件。</span><span class="sxs-lookup"><span data-stu-id="b90e9-110">Users must log in to the site they have chosen in order to share the PowerShell Gallery package.</span></span>

<span data-ttu-id="b90e9-111">如果使用者覺得某個套件很值得推薦給其他人，我們很鼓勵他們這麼做。</span><span class="sxs-lookup"><span data-stu-id="b90e9-111">Users are encouraged to do this if they find that a package is something they would recommend to others.</span></span>
<span data-ttu-id="b90e9-112">PowerShell 資源庫將會檢查該套件在每個社交媒體網站上的「分享」次數，然後顯示該套件在每個社交媒體網站上已被分享多少次。</span><span class="sxs-lookup"><span data-stu-id="b90e9-112">The PowerShell Gallery will check each social media site for "shares" of the package, and display how many times that package has been shared in each of the social media sites.</span></span>
<span data-ttu-id="b90e9-113">由於此功能只會顯示某個東西的分享次數，因此我們會把它解讀為使用者對該套件「說讚」的次數。</span><span class="sxs-lookup"><span data-stu-id="b90e9-113">Since this shows only the count of times something has been shared, it will be intepreted other users as "liking" the package.</span></span>


## <a name="comments"></a><span data-ttu-id="b90e9-114">評價</span><span class="sxs-lookup"><span data-stu-id="b90e9-114">Comments</span></span>

<span data-ttu-id="b90e9-115">PowerShell 資源庫會使用 LiveFyre 服務來允許使用者對套件提出評論。</span><span class="sxs-lookup"><span data-stu-id="b90e9-115">The PowerShell Gallery uses the LiveFyre service to allow users to comment on packages.</span></span>
<span data-ttu-id="b90e9-116">使用者如果有建議或意見反應，便可使用此功能來提供意見反應；該意見反應將會對瀏覽該套件頁面的所有人公開。</span><span class="sxs-lookup"><span data-stu-id="b90e9-116">Users who have recommendations or feedback can use this feature to provide feedback that is visible to anyone who visits the package page.</span></span>
<span data-ttu-id="b90e9-117">套件擁有者可以關注此意見反應，並在有人張貼評論時收到通知。</span><span class="sxs-lookup"><span data-stu-id="b90e9-117">Package owners can Follow this feedback, and be notified when someone posts a comment.</span></span>

<span data-ttu-id="b90e9-118">「評論」系統是以 LiveFyre 為基礎，這是一個不受 Microsoft 管理的個別服務，必須另行登入才能使用。</span><span class="sxs-lookup"><span data-stu-id="b90e9-118">The Comment system is based on LiveFyre, which is a separate service that is not managed by Microsoft, and requires unique login to use.</span></span>
<span data-ttu-id="b90e9-119">第一次提出評論或關注您其中一個套件的相關評論時，系統會提示您建立一個 LiveFyre 帳戶。</span><span class="sxs-lookup"><span data-stu-id="b90e9-119">The first time you choose to leave a comment or follow comments on one of your packages, you will be prompted to create a LiveFyre account.</span></span>

<span data-ttu-id="b90e9-120">如果您已經建立 LiveFyre 帳戶並登入，便可針對套件撰寫相關意見反應的評論，然後按一下 [Post comment] \(張貼評論\)該評論將不會立即顯示。</span><span class="sxs-lookup"><span data-stu-id="b90e9-120">If you have created a LiveFyre account and logged in, you can craft a comment that provides feedback on the package, then click on "Post comment..." The comment will not be visible immediately.</span></span>
<span data-ttu-id="b90e9-121">對資源庫套件的評論是由 PowerShell 資源庫系統管理員進行仲裁，且所有貼文都會先由仲裁者進行檢閱，然後才會發行並對其他使用者公開。</span><span class="sxs-lookup"><span data-stu-id="b90e9-121">Comments for gallery packages are moderated by the PowerShell Gallery administrators, and all posts are reviewed by the moderators before being published and visible to others.</span></span>
<span data-ttu-id="b90e9-122">仲裁評論的目的是要確保這些評論遵守符合「PowerShell 資源庫」[使用規定](https://www.powershellgallery.com/policies/Terms)的公共行為。</span><span class="sxs-lookup"><span data-stu-id="b90e9-122">Our purpose in moderating the comments is to ensure that they align with public behavior consistent with the PowerShell Gallery [Terms of Use](https://www.powershellgallery.com/policies/Terms).</span></span>

<span data-ttu-id="b90e9-123">我們建議套件擁有者關注張貼至 LiveFyre 的評論。</span><span class="sxs-lookup"><span data-stu-id="b90e9-123">Package owners are encouraged to Follow comments that are posted to LiveFyre.</span></span>
<span data-ttu-id="b90e9-124">您需要一個 LiveFyre 帳戶，且建議您在 LiveFyre 中使用與發行套件相同的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="b90e9-124">A LiveFyre account is required, and it is recommended to use the same email address you use for publishing your package in LiveFyre.</span></span>
<span data-ttu-id="b90e9-125">若要關注評論，請登入 LiveFyre，然後瀏覽至您被列為「擁有者」的任何套件。</span><span class="sxs-lookup"><span data-stu-id="b90e9-125">To Follow comments, log into LiveFyre, and navigate to any package where you are listed as an Owner.</span></span>
<span data-ttu-id="b90e9-126">在每個套件底部的 [Comment] \(評論\) 方塊下，您會看到 [+Follow] \(+關注\)。</span><span class="sxs-lookup"><span data-stu-id="b90e9-126">Below the Comment box at the bottom of each package you will see "+Follow".</span></span>
<span data-ttu-id="b90e9-127">按一下它之後，每當該套件有新的評論時，LiveFyre 就會傳送電子郵件至註冊的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="b90e9-127">Once you click on this, LiveFyre will send an email to the registered email address any time new comments made on the package.</span></span>