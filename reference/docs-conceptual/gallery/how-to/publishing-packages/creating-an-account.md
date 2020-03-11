---
ms.date: 09/11/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 建立 PowerShell 資源庫帳戶
ms.openlocfilehash: f43d7e65bb8bf9a9bbdda9790cc622786377fa38
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2020
ms.locfileid: "78278770"
---
# <a name="creating-a-powershell-gallery-account"></a><span data-ttu-id="c55ad-103">建立 PowerShell 資源庫帳戶</span><span class="sxs-lookup"><span data-stu-id="c55ad-103">Creating a PowerShell Gallery account</span></span>

<span data-ttu-id="c55ad-104">您必須先建立 PowerShell 資源庫帳戶，再將任何項目發佈至 PowerShell 資源庫。</span><span class="sxs-lookup"><span data-stu-id="c55ad-104">You must create a PowerShell Gallery account before publishing anything to the PowerShell Gallery.</span></span>
<span data-ttu-id="c55ad-105">PowerShell 資源庫帳戶必須連結至具備電子郵件功能的登入帳戶。</span><span class="sxs-lookup"><span data-stu-id="c55ad-105">PowerShell Gallery accounts must be linked to an email-enabled login account.</span></span> <span data-ttu-id="c55ad-106">此帳戶可以是 Azure Active Directory 帳戶或 Microsoft ID (例如來自 outlook.com 或 hotmail.com 的電子郵件帳戶)。</span><span class="sxs-lookup"><span data-stu-id="c55ad-106">This account can be an Azure Active Directory account or a Microsoft ID, like an email account from outlook.com or hotmail.com.</span></span>

<span data-ttu-id="c55ad-107">若要建立 PowerShell 資源庫帳戶，請前往 [https://PowerShellGallery.com](https://PowerShellGallery.com)，然後按一下 [登入]  ，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="c55ad-107">To create a PowerShell Gallery account, go to [https://PowerShellGallery.com](https://PowerShellGallery.com) and click on **Sign in** as shown in the following image.</span></span>

![註冊新帳戶](media/creating-an-account/CreateAccount-Register.png)

<span data-ttu-id="c55ad-109">若要使用 Azure Active Directory 帳戶，請選取 [公司或學校帳戶]  ，然後使用您的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="c55ad-109">To use an Azure Active Directory account, select **Work or School Account**, and sign in with your account.</span></span> <span data-ttu-id="c55ad-110">若要使用 Microsoft ID，請選擇 [個人帳戶]  並登入。</span><span class="sxs-lookup"><span data-stu-id="c55ad-110">To use a Microsoft ID, choose **Personal Account** and sign in.</span></span>

<span data-ttu-id="c55ad-111">接下來，系統會提示您建立用於 PowerShell 資源庫的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="c55ad-111">Next, you are prompted to create a username for the PowerShell Gallery.</span></span> <span data-ttu-id="c55ad-112">請檢閱「使用規定」和「隱私權原則」、輸入使用者名稱，然後按一下 [註冊]  。</span><span class="sxs-lookup"><span data-stu-id="c55ad-112">Review the Terms of Use and Privacy Policy, enter a username, and then click **Register**.</span></span>

> [!NOTE]
> <span data-ttu-id="c55ad-113">帳戶名稱建立後即無法變更。</span><span class="sxs-lookup"><span data-stu-id="c55ad-113">The account name cannot be changed once it is created.</span></span> <span data-ttu-id="c55ad-114">如需詳細資訊，請參閱[管理套件擁有者](managing-package-owners.md)。</span><span class="sxs-lookup"><span data-stu-id="c55ad-114">For more information, see [Managing Package Owners](managing-package-owners.md).</span></span>

## <a name="recommended-practices-for-powershell-gallery-accounts"></a><span data-ttu-id="c55ad-115">建議的 PowerShell 資源庫帳戶做法</span><span class="sxs-lookup"><span data-stu-id="c55ad-115">Recommended practices for PowerShell Gallery accounts</span></span>

<span data-ttu-id="c55ad-116">主動監視與 PowerShell 資源庫帳戶搭配使用的電子郵件帳戶相當重要。</span><span class="sxs-lookup"><span data-stu-id="c55ad-116">It's important to actively monitor the email account used with your PowerShell Gallery account.</span></span> <span data-ttu-id="c55ad-117">與 PowerShell 資源庫套件擁有者的所有通訊，都會透過此電子郵件地址進行。</span><span class="sxs-lookup"><span data-stu-id="c55ad-117">All communication with owners of PowerShell Gallery packages is through this email address.</span></span> <span data-ttu-id="c55ad-118">如果 PowerShell 資源庫營運小組無法連絡套件擁有者，我們可能就必須刪除套件。</span><span class="sxs-lookup"><span data-stu-id="c55ad-118">If the PowerShell Gallery Operations team is unable to contact a package owner, we may be required to delete a package.</span></span>

<span data-ttu-id="c55ad-119">發佈至 PowerShell 資源庫的組織通常會針對該用途建立一個獨特的外部帳戶。</span><span class="sxs-lookup"><span data-stu-id="c55ad-119">Organizations that publish to the PowerShell Gallery often create a unique external account for that purpose.</span></span> <span data-ttu-id="c55ad-120">建議您使用電子郵件轉寄功能，將通知轉寄到您組織中的地址。</span><span class="sxs-lookup"><span data-stu-id="c55ad-120">We recommend you use email forwarding to forward notifications to an address within your organization.</span></span>

<span data-ttu-id="c55ad-121">當多位擁有者與套件建立關聯時，所有 PowerShell 資源庫通知都會傳送給所有擁有者。</span><span class="sxs-lookup"><span data-stu-id="c55ad-121">When multiple owners are associated with a package, all PowerShell Gallery notifications are sent to all owners.</span></span> <span data-ttu-id="c55ad-122">如需詳細資訊，請參閱[管理套件擁有者](managing-package-owners.md)。</span><span class="sxs-lookup"><span data-stu-id="c55ad-122">For more information, see [Managing Package Owners](managing-package-owners.md).</span></span>
