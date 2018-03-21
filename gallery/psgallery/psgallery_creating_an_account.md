---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: "建立 PowerShell 資源庫帳戶"
ms.openlocfilehash: 5af38884d819cb9c600a061109233614bd33666f
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
## <a name="creating-a-powershell-gallery-account"></a><span data-ttu-id="d87ae-103">建立 PowerShell 資源庫帳戶</span><span class="sxs-lookup"><span data-stu-id="d87ae-103">Creating a PowerShell Gallery Account</span></span>

<span data-ttu-id="d87ae-104">將任何項目發行至「PowerShell 資源庫」之前，必須先建立「PowerShell 資源庫」帳戶。</span><span class="sxs-lookup"><span data-stu-id="d87ae-104">A PowerShell Gallery account must be established before publishing anything to the PowerShell Gallery.</span></span> <span data-ttu-id="d87ae-105">「PowerShell 資源庫」帳戶必須連結至已啟用電子郵件功能的 Azure Active Directory 帳戶，或是 Microsoft 電子郵件帳戶 (網域為 outlook.com、hotmail.com 等)</span><span class="sxs-lookup"><span data-stu-id="d87ae-105">The PowerShell Gallery accounts must be linked to an Azure Active Directory email-enabled account, or a Microsoft email account (with a domain of outlook.com, hotmail.com, etc.)</span></span>

<span data-ttu-id="d87ae-106">若要建立「PowerShell 資源庫」帳戶，請移至 https://PowerShellGallery.com 並按一下 [註冊]\(請參閱下圖\)。</span><span class="sxs-lookup"><span data-stu-id="d87ae-106">To create a PowerShell Gallery account, go to https://PowerShellGallery.com and click on "Register" (see the image below).</span></span> 

![註冊新帳戶](./images/CreatingAccount-Register.png)

<span data-ttu-id="d87ae-108">在下一個頁面中，若要使用 Azure Active Directory 帳戶，請選取 [公司或學校帳戶]，然後使用您的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="d87ae-108">In the next page, to use an Azure Active Directory account, select "Work or School Account", and log in with your account.</span></span> <span data-ttu-id="d87ae-109">若要使用 Microsoft 帳戶 (例如 Hotmail.com 或 Outlook.com 網域中的帳戶)，請選擇 [個人帳戶]，然後登入。</span><span class="sxs-lookup"><span data-stu-id="d87ae-109">To use a Microsoft account - such as one in a Hotmail.com or Outlook.com domain - choose "Personal Account", and log in.</span></span> 

<span data-ttu-id="d87ae-110">登入之後，系統會提示您建立用於「PowerShell 資源庫」的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="d87ae-110">Once you have logged in, you will be prompted to create a username for the PowerShell Gallery.</span></span> <span data-ttu-id="d87ae-111">請檢閱所連結的「使用規定」和「隱私權原則」、輸入使用者名稱，然後按一下 [註冊]。</span><span class="sxs-lookup"><span data-stu-id="d87ae-111">Review the Terms of Use and Privacy Policy that are linked in, enter a username, and then click Register.</span></span>

<span data-ttu-id="d87ae-112">注意：此帳戶名稱建立後即無法變更。</span><span class="sxs-lookup"><span data-stu-id="d87ae-112">Note: This account name cannot be changed once it is created.</span></span>  
<span data-ttu-id="d87ae-113">如需其他相關的詳細資料，請參閱[管理項目擁有者](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners)。</span><span class="sxs-lookup"><span data-stu-id="d87ae-113">See [Managing Item Owners](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) for additional details related to this.</span></span>

## <a name="recommended-practices-for-powershell-gallery-accounts"></a><span data-ttu-id="d87ae-114">建議的 PowerShell 資源庫帳戶做法</span><span class="sxs-lookup"><span data-stu-id="d87ae-114">Recommended Practices for PowerShell Gallery Accounts</span></span>

<span data-ttu-id="d87ae-115">主動監視與「PowerShell 資源庫」帳戶搭配使用的電子郵件帳戶相當重要。</span><span class="sxs-lookup"><span data-stu-id="d87ae-115">It is important that the email account used with your PowerShell Gallery account be actively monitored.</span></span>
<span data-ttu-id="d87ae-116">與「PowerShell 資源庫」項目擁有者進行的一切溝通，都會透過與「PowerShell 資源庫」帳戶關聯的電子郵件地址進行。</span><span class="sxs-lookup"><span data-stu-id="d87ae-116">All communiction with owners of PowerShell Gallery items is through the email using the address associated with your PowerShell Gallery account.</span></span>
<span data-ttu-id="d87ae-117">如果我們無法連絡項目擁有者，在某些情況下，作業小組可能就必須刪除項目。</span><span class="sxs-lookup"><span data-stu-id="d87ae-117">If we are unable to contact an item owner, the Operations team may be required to delete an item under some circumstances.</span></span>

<span data-ttu-id="d87ae-118">將項目發行至「PowerShell 資源庫」的組織通常會在 Outlook.com 或另一個 Microsoft 帳戶網域中針對該用途建立一個獨特的帳戶。</span><span class="sxs-lookup"><span data-stu-id="d87ae-118">Organizations that publish to the PowerShell Gallery often create a unique account for that purpose in Outlook.com, or another Microsoft account domain.</span></span>
<span data-ttu-id="d87ae-119">在許多情況下，該帳戶並不會受到定期監視。</span><span class="sxs-lookup"><span data-stu-id="d87ae-119">In many cases that account is not regularly monitored.</span></span> <span data-ttu-id="d87ae-120">針對該情況，最佳做法是使用「Outlook 轉寄設定」，將電子郵件傳送到其他將受到項目擁有者監視的帳戶 (通常是組織內的帳戶)。</span><span class="sxs-lookup"><span data-stu-id="d87ae-120">A best practice in that case is to use Outlook Forwarding to send email to another account, typically one within the organization, that will be monitored by the item owner(s).</span></span>

<span data-ttu-id="d87ae-121">如果項目有多個關聯的擁有者，系統就會將來自「PowerShell 資源庫」的所有溝通傳送給所有擁有者。</span><span class="sxs-lookup"><span data-stu-id="d87ae-121">If there are multiple owners associated with an item, all communications that come from the PowerShell Gallery will go to all owners.</span></span>
<span data-ttu-id="d87ae-122">如需有關為項目新增擁有者的其他詳細資料，請參閱[管理項目擁有者](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners)。</span><span class="sxs-lookup"><span data-stu-id="d87ae-122">See [Managing Item Owners](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) for additional details on adding owners to an item.</span></span> 

