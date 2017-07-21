---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgalleryint_status
ms.openlocfilehash: 0b2f1ebcb365fcd24438a028a9c8181449266a8b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
<a name="powershell-gallery-status"></a><span data-ttu-id="0d393-103">PowerShell 資源庫狀態</span><span class="sxs-lookup"><span data-stu-id="0d393-103">PowerShell Gallery Status</span></span>
=========================

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a><span data-ttu-id="0d393-104">2017 年 3 月 27 日 - 已解決：無法看到個別模組和指令碼頁面</span><span class="sxs-lookup"><span data-stu-id="0d393-104">03/27/2017 - RESOLVED: Unable to see individual module and script pages</span></span>

<span data-ttu-id="0d393-105">__影響摘要__：https://www.powershellgallery.com 上個別模組和指令碼頁面的直接連結已中斷。</span><span class="sxs-lookup"><span data-stu-id="0d393-105">__Summary of Impact__: Direct links to individual module and script pages on https://www.powershellgallery.com were broken.</span></span> <span data-ttu-id="0d393-106">所有區域均回報此問題。</span><span class="sxs-lookup"><span data-stu-id="0d393-106">This was being reported across all the regions.</span></span> <span data-ttu-id="0d393-107">這並未影響任何 PowerShellGet Cmdlet，亦即 Install-Module、Install-Script、Update-Module、Update-Script、Publish-Module、Publish-Script 仍繼續運作。</span><span class="sxs-lookup"><span data-stu-id="0d393-107">This did not impact any of the PowerShellGet cmdlets ie., Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Script continued to work.</span></span>

<span data-ttu-id="0d393-108">__根本原因__：工程師確認原因出自將社交媒體按鈕 (例如 Facebook) 引入到頁面上。</span><span class="sxs-lookup"><span data-stu-id="0d393-108">__Root Cause__: Engineers identified the cause as an issue bringing up social media buttons like Facebook onto the page.</span></span>  

<span data-ttu-id="0d393-109">__解決方法__：工程師停用了 Facebook 計數資訊，以修正此問題。</span><span class="sxs-lookup"><span data-stu-id="0d393-109">__Resolution__: Engineers fixed the problem by disabling the Facebook count information.</span></span>

<span data-ttu-id="0d393-110">__後續步驟__：我們開啟了內部追蹤問題，以修正我們的 Facebook API 使用方式。</span><span class="sxs-lookup"><span data-stu-id="0d393-110">__Next Steps__: We opened an internal tracking issue to fix our usage of Facebook API.</span></span>

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a><span data-ttu-id="0d393-111">12/15/2016 - 無法透過 PowerShellGallery 網站傳送電子郵件</span><span class="sxs-lookup"><span data-stu-id="0d393-111">12/15/2016 - Unable to send emails via PowerShellGallery website</span></span>

<span data-ttu-id="0d393-112">__影響的摘要__：在 12/13/2016 和 12/15/2016 之間，PowerShell 資源庫系統管理員未收到透過「連絡擁有者」、「管理擁有者」、「連絡支援人員」或「檢舉不當使用」傳送的任何訊息。</span><span class="sxs-lookup"><span data-stu-id="0d393-112">__Summary of Impact__: Between 12/13/2016 and 12/15/2016, any messages sent via Contact Owners, Manage Owners, Contact Support, or Report Abuse were not received by the PowerShell Gallery Administrators.</span></span>  
<span data-ttu-id="0d393-113">__根本原因__︰工程師找出其肇因為 SMTP 伺服器的驗證問題。</span><span class="sxs-lookup"><span data-stu-id="0d393-113">__Root Cause__: Engineers identified the cause as an authentication issue with the SMTP server.</span></span>  
<span data-ttu-id="0d393-114">__解決方法__︰工程師能夠解決驗證問題並還原 SMTP 伺服器連線。</span><span class="sxs-lookup"><span data-stu-id="0d393-114">__Resolution__: Engineers were able to resolve the authentication issue and restore connection to the SMTP server.</span></span>  
<span data-ttu-id="0d393-115">__後續步驟__︰如果您在這段期間使用連絡「擁有者」、「管理擁有者」、「連絡支援人員」或「檢舉不當使用」連結來傳送郵件給 cgadmin@microsoft.com，而我們沒有回應，請再試一次。</span><span class="sxs-lookup"><span data-stu-id="0d393-115">__Next Steps__: If you used the Contact Owners, Manage Owners, Contact Support, or Report Abuse links to send mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="0d393-116">造成您的不便，我們深感抱歉。</span><span class="sxs-lookup"><span data-stu-id="0d393-116">We apologize for the inconvenience.</span></span>   


## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a><span data-ttu-id="0d393-117">2016/8/10 - 已解決︰無法傳送電子郵件給 cgadmin@microsoft.com</span><span class="sxs-lookup"><span data-stu-id="0d393-117">8/10/2016 - Resolved: Unable to send emails to cgadmin@microsoft.com</span></span>
<span data-ttu-id="0d393-118">__影響摘要__：2016 年 8 月5 日到 2016 年 8 月 10 日之間，客戶無法傳送電子郵件給 cgadmin@microsoft.com，也無法使用「與我們連絡」功能。</span><span class="sxs-lookup"><span data-stu-id="0d393-118">__Summary of Impact__: Between 8/5/2016 and 8/10/2016, customers were unable to send emails to cgadmin@microsoft.com, or use the Contact Us feature.</span></span>  
<span data-ttu-id="0d393-119">__根本原因__︰工程師確認原因出自電子郵件帳戶的設定變更。</span><span class="sxs-lookup"><span data-stu-id="0d393-119">__Root Cause__: Engineers identified the cause as a configuration change of the email account.</span></span>  
<span data-ttu-id="0d393-120">__解決方法__︰工程師已找出解決此設定問題的方法。</span><span class="sxs-lookup"><span data-stu-id="0d393-120">__Resolution__: Engineers worked to resolve the configuration issue.</span></span>  
<span data-ttu-id="0d393-121">__後續步驟__︰若您曾在這段期間使用 [與我們連絡] 連結，或傳送郵件給 cgadmin@microsoft.com，但我們未回應，請再試一次。</span><span class="sxs-lookup"><span data-stu-id="0d393-121">__Next Steps__: If you used the Contact Us link or sent mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="0d393-122">感謝您的耐心配合。</span><span class="sxs-lookup"><span data-stu-id="0d393-122">Thank you for your patience.</span></span>


