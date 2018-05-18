---
ms.date: 03/27/2018
contributor: JKeithB
ms.topic: conceptual
keywords: 資源庫,powershell,psgallery,GDPR
title: PowerShell 資源庫 GDPR 合規性
ms.openlocfilehash: 0a9e76325a2a5cf8f509e1a6317c8ed88d133f1d
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
---
# <a name="powershell-gallery-gdpr-compliance"></a><span data-ttu-id="300ad-103">PowerShell 資源庫 GDPR 合規性</span><span class="sxs-lookup"><span data-stu-id="300ad-103">PowerShell Gallery GDPR compliance</span></span>

## <a name="overview"></a><span data-ttu-id="300ad-104">概觀</span><span class="sxs-lookup"><span data-stu-id="300ad-104">Overview</span></span>

<span data-ttu-id="300ad-105">一般資料保護規定 (GDPR) 的歐洲隱私權法於 2018 年 5 月生效。</span><span class="sxs-lookup"><span data-stu-id="300ad-105">In May 2018, a European privacy law, the General Data Protection Regulation (GDPR), takes effect.</span></span>
<span data-ttu-id="300ad-106">GDPR 對公司、政府機關、非營利組織以及其他為歐盟 (EU) 居民提供產品與服務的組織，或是收集及分析與歐盟居民相關資料的組織，加諸了新的規範。</span><span class="sxs-lookup"><span data-stu-id="300ad-106">The GDPR imposes new rules on companies, government agencies, non-profits, and other organizations that offer goods and services to people in the European Union (EU), or that collect and analyze data tied to EU residents.</span></span>
<span data-ttu-id="300ad-107">無論您身於何處均適用 GDPR。</span><span class="sxs-lookup"><span data-stu-id="300ad-107">The GDPR applies no matter where you are located.</span></span>

> [!NOTE]
> <span data-ttu-id="300ad-108">本文提供如何從 PowerShell 資源庫中刪除個人資料的步驟，且您可透過這些步驟，符合 GDPR 所規範的義務。</span><span class="sxs-lookup"><span data-stu-id="300ad-108">This article provides steps for how to delete personal data from the PowerShell Gallery and can be used to support your obligations under the GDPR.</span></span> <span data-ttu-id="300ad-109">如果您正在尋找與 GDPR 相關的一般資訊，請參閱[服務信任入口網站的 GDPR 區段](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted)。</span><span class="sxs-lookup"><span data-stu-id="300ad-109">If you’re looking for general info about GDPR, see the [GDPR section of the Service Trust portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span></span>

## <a name="personally-identifiable-data"></a><span data-ttu-id="300ad-110">可識別個人的資料</span><span class="sxs-lookup"><span data-stu-id="300ad-110">Personally identifiable data</span></span>

<span data-ttu-id="300ad-111">PowerShell 資源庫會儲存下列由使用者所提供的資訊，而其中可能包含個人資訊：</span><span class="sxs-lookup"><span data-stu-id="300ad-111">The PowerShell Gallery stores the following information that may be provided by users, which may contain personal information:</span></span>

* <span data-ttu-id="300ad-112">PowerShell 資源庫帳戶</span><span class="sxs-lookup"><span data-stu-id="300ad-112">PowerShell Gallery account</span></span>
* <span data-ttu-id="300ad-113">發行至 PowerShell 資源庫的項目</span><span class="sxs-lookup"><span data-stu-id="300ad-113">Items published to the PowerShell Gallery</span></span>
* <span data-ttu-id="300ad-114">與 PowerShell 資源庫小組來往的電子郵件</span><span class="sxs-lookup"><span data-stu-id="300ad-114">Email correspondence with the PowerShell Gallery team</span></span>

<span data-ttu-id="300ad-115">大部分的使用者不會建立 PowerShell 資源庫帳戶。</span><span class="sxs-lookup"><span data-stu-id="300ad-115">Most users do not create a PowerShell Gallery account.</span></span>
<span data-ttu-id="300ad-116">除非您將會發行項目或是使用 PowerShell 資源庫中的「連絡擁有者」功能，否則不需要帳戶。</span><span class="sxs-lookup"><span data-stu-id="300ad-116">An account is not required unless you are going to publish an item or use the "Contact Owner" feature in the PowerShell Gallery.</span></span>
<span data-ttu-id="300ad-117">除了由使用者所開始的往來電子郵件之外，PowerShell 資源庫對於尚未建立帳戶的使用者，不會儲存其可識別個人之資料。</span><span class="sxs-lookup"><span data-stu-id="300ad-117">Other than email correspondence initiated by the user, the PowerShell Gallery does not store personally identifiable data for users who have not created an account.</span></span>

<span data-ttu-id="300ad-118">建立 PowerShell 資源庫帳戶的使用者，可以對 PowerShell 資源庫發行項目。</span><span class="sxs-lookup"><span data-stu-id="300ad-118">Users who create a PowerShell Gallery account can publish items to the PowerShell Gallery.</span></span>
<span data-ttu-id="300ad-119">這些項目應為 PowerShell 程式碼，但可能包含內含個人資訊的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="300ad-119">Those items are expected to be PowerShell code, but may contain other information including personal information.</span></span>
<span data-ttu-id="300ad-120">下列資訊會顯示您可如何取得已發行至 PowerShell 資源庫的所有項目。</span><span class="sxs-lookup"><span data-stu-id="300ad-120">The information below will show how you can get all the items you have published to the PowerShell Gallery.</span></span>

## <a name="dsr-export-of-powershell-gallery-data"></a><span data-ttu-id="300ad-121">PowerShell 資源庫資料的 DSR 匯出</span><span class="sxs-lookup"><span data-stu-id="300ad-121">DSR Export of PowerShell Gallery Data</span></span>

<span data-ttu-id="300ad-122">下列各節會解釋如何匯出儲存在 PowerShell 資源庫中的資訊，以及如何要求刪除此資訊，來說明 PowerShell 資源庫如何做到資料主體要求 (DSR)。</span><span class="sxs-lookup"><span data-stu-id="300ad-122">The following sections describe how the PowerShell Gallery supports data subject requests (DSR), by explaining how to export information stored in the PowerShell Gallery, and how to request deletion of this information.</span></span>

### <a name="email"></a><span data-ttu-id="300ad-123">電子郵件</span><span class="sxs-lookup"><span data-stu-id="300ad-123">Email</span></span>

<span data-ttu-id="300ad-124">往來電子郵件可包含下列任一項：</span><span class="sxs-lookup"><span data-stu-id="300ad-124">Email correspondence may include any of the following:</span></span>

* <span data-ttu-id="300ad-125">若程式碼分析掃描偵測到已發行至 PowerShell 資源庫的任何項目發生問題，會傳送電子郵件給 PowerShell 資源庫項目的擁有者</span><span class="sxs-lookup"><span data-stu-id="300ad-125">Email sent to the owners of PowerShell Gallery items if the code analysis scans detected an issue with any item they have published to the PowerShell Gallery</span></span>
* <span data-ttu-id="300ad-126">使用「與我們連絡」頁面 (cgadmin@microsoft.com) 中的電子郵件地址，任何人皆可傳送電子郵件給 PowerShell 資源庫小組</span><span class="sxs-lookup"><span data-stu-id="300ad-126">Email sent by anyone to the PowerShell Gallery team using the email address in the "Contact Us" page (cgadmin@microsoft.com)</span></span>
* <span data-ttu-id="300ad-127">使用 PowerShell 資源庫中「連絡擁有者」功能的註冊使用者，可傳送電子郵件給 PowerShell 資源庫中項目的擁有者</span><span class="sxs-lookup"><span data-stu-id="300ad-127">Registered users who use the "Contact Owner" feature in the PowerShell Gallery to send email to the owner of an item in the PowerShell Gallery</span></span>

<span data-ttu-id="300ad-128">與 PowerShell 資源庫往來的電子郵件，保留原則為 90 天，以進行可能的安全性調查，探索在 PowerShell 資源庫上是否有惡意程式碼。</span><span class="sxs-lookup"><span data-stu-id="300ad-128">Emails sent by or to the PowerShell Gallery have a retention policy of 90 days to support possible security investigations should malicious code be discovered on the PowerShell Gallery.</span></span>
<span data-ttu-id="300ad-129">電子郵件依原則將會在 90 天後刪除。</span><span class="sxs-lookup"><span data-stu-id="300ad-129">Emails are deleted by policy after 90 days.</span></span>

<span data-ttu-id="300ad-130">您可申請前 90 天對您電子郵件地址以及 PowerShell 資源庫所傳送或接收之所有電子郵件的副本。</span><span class="sxs-lookup"><span data-stu-id="300ad-130">You may request copies of all emails sent to or from your email address and the PowerShell Gallery within the previous 90 days.</span></span>
<span data-ttu-id="300ad-131">若要申請這些往來郵件，請傳送電子郵件至 cgadmin@microsoft.com，標題請寫：「與此帳戶相關之電子郵件的 DSR 申請」。</span><span class="sxs-lookup"><span data-stu-id="300ad-131">To request this correspondence, send an email to cgadmin@microsoft.com, with the title: "DSR Request for emails relating to this account".</span></span>
<span data-ttu-id="300ad-132">在訊息內文中，請陳述您要申請的資訊 (例如：請傳送給我所有此電子郵件地址所傳送或接收之電子郵件。)您可在 7 個工作天內，收到發出申請 90 天內您電子郵件地址相關的所有電子郵件。</span><span class="sxs-lookup"><span data-stu-id="300ad-132">In the body of the message, state what information you are requesting (for example: Please send all emails sent to or received from this email address.) All emails involving your email address within 90 days of the request will be sent within 7 business days.</span></span>

### <a name="powershell-gallery-account-information"></a><span data-ttu-id="300ad-133">PowerShell 資源庫帳戶資訊</span><span class="sxs-lookup"><span data-stu-id="300ad-133">PowerShell Gallery Account Information</span></span>

<span data-ttu-id="300ad-134">若您已建立了 PowerShell 資源庫帳戶，即可以採取下列步驟，找到儲存在 PowerShell 資源庫中的所有個人資訊：</span><span class="sxs-lookup"><span data-stu-id="300ad-134">If you have created a PowerShell Gallery account, you can find all personal information that has been stored in PowerShell Gallery by taking the following steps:</span></span>

1. <span data-ttu-id="300ad-135">請登入 PowerShell 資源庫，然後按一下您的使用者名稱</span><span class="sxs-lookup"><span data-stu-id="300ad-135">Sign in to the PowerShell Gallery, then click on your username</span></span>
2. <span data-ttu-id="300ad-136">下一個顯示的頁面為 [帳戶] 頁面，其會顯示為 PowerShell 資源庫帳戶所使用的電子郵件地址</span><span class="sxs-lookup"><span data-stu-id="300ad-136">The next page displayed is the Account page, which shows the email address used for the PowerShell Gallery account</span></span>

<span data-ttu-id="300ad-137">若您在 PowerShell 資源庫中建立了多個帳戶，則必須為每個帳戶重複這些步驟。</span><span class="sxs-lookup"><span data-stu-id="300ad-137">If you have created more than one account in the PowerShell Gallery, you will need to repeat these steps for each account.</span></span>

### <a name="items-in-the-powershell-gallery"></a><span data-ttu-id="300ad-138">PowerShell 資源庫中的項目</span><span class="sxs-lookup"><span data-stu-id="300ad-138">Items in the PowerShell Gallery</span></span>

<span data-ttu-id="300ad-139">為便於匯出已發行至 PowerShell 資源庫的項目，我們已將指令碼 "GetPSGalleryItemsForAuthor" 發行至 PowerShell 資源庫。</span><span class="sxs-lookup"><span data-stu-id="300ad-139">To facilitate exporting items published to the PowerShell Gallery, we have published the script "GetPSGalleryItemsForAuthor" to the PowerShell Gallery.</span></span>
<span data-ttu-id="300ad-140">此指令碼會將每個項目的每一個版本之副本，依據項目中所儲存的作者資訊，匯出置入 PowerShell 資源庫中。</span><span class="sxs-lookup"><span data-stu-id="300ad-140">This script exports a copy of every version of every item put into the PowerShell Gallery based on the author information stored in the item.</span></span>

> [!NOTE]
> <span data-ttu-id="300ad-141">當您發行您的項目時，會在項目的資訊清單中儲存作者。</span><span class="sxs-lookup"><span data-stu-id="300ad-141">The Author is stored in the item manifest when you publish your item.</span></span>
> <span data-ttu-id="300ad-142">不保證作者會與您用於 PowerShell 資源庫中之帳戶，是相同的身分識別。</span><span class="sxs-lookup"><span data-stu-id="300ad-142">There is no guarantee that the Author is the same identity as the account you use in the PowerShell Gallery.</span></span>
> <span data-ttu-id="300ad-143">若您在 [作者] 欄位中使用了一些其他的值，則在使用此指令碼時，必須提供該值。</span><span class="sxs-lookup"><span data-stu-id="300ad-143">If you use some other value in the Author field, you will need to supply that value when using this script.</span></span>

<span data-ttu-id="300ad-144">您可使用下列 PowerShell 命令，下載此指令碼：</span><span class="sxs-lookup"><span data-stu-id="300ad-144">You may download the script by using the following PowerShell command:</span></span>

```powershell
Save-Script GetPSGalleryItemsForAuthor -path <local folder location> -repository psgallery
```

<span data-ttu-id="300ad-145">然後您可執行下列 PowerShell 命令，直接執行該指令碼：</span><span class="sxs-lookup"><span data-stu-id="300ad-145">You can then run the script directly, by running the following PowerShell commands:</span></span>

```powershell
cd <local folder location >
.\GetPSGalleryItemsForAuthor.ps1
```

<span data-ttu-id="300ad-146">系統會提示您提供作者以及您希望儲存項目之系統上的資料夾。</span><span class="sxs-lookup"><span data-stu-id="300ad-146">You will be prompted to supply the Author and a folder on your system where you want the items to be saved.</span></span>

## <a name="deleting-personal-data-from-the-powershell-gallery"></a><span data-ttu-id="300ad-147">從 PowerShell 資源庫刪除個人資料</span><span class="sxs-lookup"><span data-stu-id="300ad-147">Deleting Personal Data From The PowerShell Gallery</span></span>

<span data-ttu-id="300ad-148">若要刪除您的 PowerShell 資源庫帳戶或任何您在 PowerShell 資源庫中所擁有的項目，請傳送電子郵件至 cgadmin@microsoft.com，標題請寫：「與此帳戶相關之電子郵件的 DSR 申請」。</span><span class="sxs-lookup"><span data-stu-id="300ad-148">To delete your PowerShell Gallery account or any item you own in the PowerShell Gallery, send email to cgadmin@microsoft.com with the title: "GDPR Request for items relating to this account".</span></span>
<span data-ttu-id="300ad-149">在訊息內文中，請陳述您希望刪除的資訊。</span><span class="sxs-lookup"><span data-stu-id="300ad-149">In the body of the message state what information you want deleted.</span></span> <span data-ttu-id="300ad-150">例如：</span><span class="sxs-lookup"><span data-stu-id="300ad-150">For example:</span></span>

* <span data-ttu-id="300ad-151">請刪除我的項目「項目名稱」之版本 x.y.z</span><span class="sxs-lookup"><span data-stu-id="300ad-151">Please delete version x.y.z of my item "item name"</span></span>
* <span data-ttu-id="300ad-152">請刪除我的項目「項目名稱」之所有版本</span><span class="sxs-lookup"><span data-stu-id="300ad-152">Please delete all versions of my item "item name"</span></span>
* <span data-ttu-id="300ad-153">請刪除我的 PowerShell 資源庫帳戶</span><span class="sxs-lookup"><span data-stu-id="300ad-153">Please delete my PowerShell Gallery account</span></span>

<span data-ttu-id="300ad-154">PowerShell 資源庫系統管理員將會於 7 個工作天內回覆您。</span><span class="sxs-lookup"><span data-stu-id="300ad-154">The PowerShell Gallery administrators will reply within 7 business days.</span></span>
<span data-ttu-id="300ad-155">指定的項目將於提出申請之後的 30 天內刪除。</span><span class="sxs-lookup"><span data-stu-id="300ad-155">The items specified will be deleted within 30 days after the request is sent.</span></span>
