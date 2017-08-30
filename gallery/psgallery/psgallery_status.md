---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_status
ms.openlocfilehash: d192c706bdbe9aa693f791ef1c8108aeaaae385b
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2017
---
<a name="powershell-gallery-status"></a><span data-ttu-id="5b43e-103">PowerShell 資源庫狀態</span><span class="sxs-lookup"><span data-stu-id="5b43e-103">PowerShell Gallery Status</span></span>
=========================
## <a name="06012017---deploy-to-azure-automation-currently-unavailable"></a><span data-ttu-id="5b43e-104">2017 年 6 月 1 日 - 目前無法部署至 Azure 自動化</span><span class="sxs-lookup"><span data-stu-id="5b43e-104">06/01/2017 - Deploy to Azure Automation Currently Unavailable</span></span>

<span data-ttu-id="5b43e-105">__影響摘要__：目前無法將具有相依性的項目從「PowerShell 資源庫」部署至「Azure 自動化」。</span><span class="sxs-lookup"><span data-stu-id="5b43e-105">__Summary of Impact__: Deploying items with dependencies to Azure Automation from the PowerShell Gallery is currently unavailable.</span></span>  <span data-ttu-id="5b43e-106">仍然無法從「Azure 自動化」內部自「PowerShell 資源庫」匯入項目。</span><span class="sxs-lookup"><span data-stu-id="5b43e-106">Importing items from the PowerShell Gallery from inside Azure Automation is still available.</span></span>  
 
<span data-ttu-id="5b43e-107">__根本原因__：項目如果與其他項目相依且先前已部署至「Azure 自動化」，系統就不會將其部署至「Azure 自動化」。</span><span class="sxs-lookup"><span data-stu-id="5b43e-107">__Root Cause__: Items that have dependencies on others, and have been previously deployed to Azure Automation, will not be deployed to Azure Automation.</span></span> <span data-ttu-id="5b43e-108">針對「部署至 Azure 自動化」功能，工程師已找出一個與為具有相依性的項目產生 ARM 範本有關的問題。</span><span class="sxs-lookup"><span data-stu-id="5b43e-108">Engineers have identified an issue with how ARM templates are generated for items with dependencies for the Deploy to Azure Automation functionality.</span></span>

<span data-ttu-id="5b43e-109">__解決方法__：工程師正在努力解決此問題。</span><span class="sxs-lookup"><span data-stu-id="5b43e-109">__Resolution__: Engineers are working to resolve issue.</span></span>  <span data-ttu-id="5b43e-110">使用者目前的因應措施是從「Azure 自動化」內部自「PowerShell 資源庫」匯入項目。</span><span class="sxs-lookup"><span data-stu-id="5b43e-110">The current workaround for users is to import the item from the PowerShell Gallery from inside Azure Automation.</span></span> 

<span data-ttu-id="5b43e-111">__後續步驟__：工程師將在稍後發行修正。</span><span class="sxs-lookup"><span data-stu-id="5b43e-111">__Next Steps__: Engineers will release the fix shortly.</span></span>  <span data-ttu-id="5b43e-112">在此同時，請使用建議的因應措施。</span><span class="sxs-lookup"><span data-stu-id="5b43e-112">In the meantime, please use the recommended workaround.</span></span> 


## <a name="04112017---users-unable-to-log-in-with-azure-active-directory-aad-accounts"></a><span data-ttu-id="5b43e-113">04/11/2017 - 使用者無法登入 Azure Active Directory (AAD) 帳戶</span><span class="sxs-lookup"><span data-stu-id="5b43e-113">04/11/2017 - Users unable to log in with Azure Active Directory (AAD) accounts</span></span>

<span data-ttu-id="5b43e-114">__影響摘要__：有些使用者過去無法使用 Azure AD 帳戶登入 PowerShell 資源庫。</span><span class="sxs-lookup"><span data-stu-id="5b43e-114">__Summary of Impact__: Some users were unable to log in to the PowerShell Gallery using Azure AD Accounts.</span></span> 
 
<span data-ttu-id="5b43e-115">__根本原因__︰在更新至更安全的 AAD 互動方式期間，錯過一項設定變更。</span><span class="sxs-lookup"><span data-stu-id="5b43e-115">__Root Cause__: During an update to interact more securely with AAD, a setting change was missed.</span></span> <span data-ttu-id="5b43e-116">為驗證變更而進行的測試不包括特定類型的 AAD 帳戶，所以部署會繼續進行。</span><span class="sxs-lookup"><span data-stu-id="5b43e-116">The testing done to validate the change did not include certain types of AAD accounts, so the deployment proceeded.</span></span>

<span data-ttu-id="5b43e-117">__解決方法__︰工程師找到遺失的設定，並已修正問題。</span><span class="sxs-lookup"><span data-stu-id="5b43e-117">__Resolution__: Engineers identified the missing setting and corrected the problem.</span></span> 

<span data-ttu-id="5b43e-118">__後續步驟__︰我們會修改測試以包括更廣泛的 AAD 帳戶類型。</span><span class="sxs-lookup"><span data-stu-id="5b43e-118">__Next Steps__: We will be modifying our testing to include a broader set of AAD account types.</span></span>

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a><span data-ttu-id="5b43e-119">2017 年 3 月 27 日 - 已解決：無法看到個別模組和指令碼頁面</span><span class="sxs-lookup"><span data-stu-id="5b43e-119">03/27/2017 - RESOLVED: Unable to see individual module and script pages</span></span>

<span data-ttu-id="5b43e-120">__影響摘要__：https://www.powershellgallery.com 上個別模組和指令碼頁面的直接連結已中斷。</span><span class="sxs-lookup"><span data-stu-id="5b43e-120">__Summary of Impact__: Direct links to individual module and script pages on https://www.powershellgallery.com were broken.</span></span> <span data-ttu-id="5b43e-121">所有區域均回報此問題。</span><span class="sxs-lookup"><span data-stu-id="5b43e-121">This was being reported across all the regions.</span></span> <span data-ttu-id="5b43e-122">這並未影響任何 PowerShellGet Cmdlet，Install-Module、Install-Script、Update-Module、Update-Script、Publish-Module、Publish-Script 仍繼續運作。</span><span class="sxs-lookup"><span data-stu-id="5b43e-122">This did not impact any of the PowerShellGet cmdlets ie., Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Scirpt continued to work.</span></span>

<span data-ttu-id="5b43e-123">__根本原因__：工程師確認原因出自將社交媒體按鈕 (例如 Facebook) 引入到頁面上。</span><span class="sxs-lookup"><span data-stu-id="5b43e-123">__Root Cause__: Engineers identified the cause as an issue bringing up social media buttons like Facebook onto the page.</span></span>  

<span data-ttu-id="5b43e-124">__解決方法__：工程師停用了 Facebook 計數資訊，以修正此問題。</span><span class="sxs-lookup"><span data-stu-id="5b43e-124">__Resolution__: Engineers fixed the problem by disabling the Facebook count information.</span></span>

<span data-ttu-id="5b43e-125">__後續步驟__：我們開啟了內部追蹤問題，以修正我們的 Facebook API 使用方式。</span><span class="sxs-lookup"><span data-stu-id="5b43e-125">__Next Steps__: We opened an internal tracking issue to fix our usage of Facebook API.</span></span>

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a><span data-ttu-id="5b43e-126">12/15/2016 - 無法透過 PowerShellGallery 網站傳送電子郵件</span><span class="sxs-lookup"><span data-stu-id="5b43e-126">12/15/2016 - Unable to send emails via PowerShellGallery website</span></span>

<span data-ttu-id="5b43e-127">__影響的摘要__：在 12/13/2016 和 12/15/2016 之間，PowerShell 資源庫系統管理員未收到透過「連絡擁有者」、「管理擁有者」、「連絡支援人員」或「檢舉不當使用」傳送的任何訊息。</span><span class="sxs-lookup"><span data-stu-id="5b43e-127">__Summary of Impact__: Between 12/13/2016 and 12/15/2016, any messages sent via Contact Owners, Manage Owners, Contact Support, or Report Abuse were not received by the PowerShell Gallery Administrators.</span></span>  
<span data-ttu-id="5b43e-128">__根本原因__︰工程師找出其肇因為 SMTP 伺服器的驗證問題。</span><span class="sxs-lookup"><span data-stu-id="5b43e-128">__Root Cause__: Engineers identified the cause as an authentication issue with the SMTP server.</span></span>  
<span data-ttu-id="5b43e-129">__解決方法__︰工程師能夠解決驗證問題並還原 SMTP 伺服器連線。</span><span class="sxs-lookup"><span data-stu-id="5b43e-129">__Resolution__: Engineers were able to resolve the authentication issue and restore connection to the SMTP server.</span></span>  
<span data-ttu-id="5b43e-130">__後續步驟__︰如果您在這段期間使用連絡「擁有者」、「管理擁有者」、「連絡支援人員」或「檢舉不當使用」連結來傳送郵件給 cgadmin@microsoft.com，而我們沒有回應，請再試一次。</span><span class="sxs-lookup"><span data-stu-id="5b43e-130">__Next Steps__: If you used the Contact Owners, Manage Owners, Contact Support, or Report Abuse links to send mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="5b43e-131">造成您的不便，我們深感抱歉。</span><span class="sxs-lookup"><span data-stu-id="5b43e-131">We apologize for the inconvenience.</span></span>  



## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a><span data-ttu-id="5b43e-132">2016/8/10 - 已解決︰無法傳送電子郵件給 cgadmin@microsoft.com</span><span class="sxs-lookup"><span data-stu-id="5b43e-132">8/10/2016 - Resolved: Unable to send emails to cgadmin@microsoft.com</span></span>

<span data-ttu-id="5b43e-133">__影響摘要__：2016 年 8 月5 日到 2016 年 8 月 10 日之間，客戶無法傳送電子郵件給 cgadmin@microsoft.com，也無法使用「與我們連絡」功能。</span><span class="sxs-lookup"><span data-stu-id="5b43e-133">__Summary of Impact__: Between 8/5/2016 and 8/10/2016, customers were unable to send emails to cgadmin@microsoft.com, or use the Contact Us feature.</span></span>  
<span data-ttu-id="5b43e-134">__根本原因__︰工程師確認原因出自電子郵件帳戶的設定變更。</span><span class="sxs-lookup"><span data-stu-id="5b43e-134">__Root Cause__: Engineers identified the cause as a configuration change of the email account.</span></span>  
<span data-ttu-id="5b43e-135">__解決方法__︰工程師已找出解決此設定問題的方法。</span><span class="sxs-lookup"><span data-stu-id="5b43e-135">__Resolution__: Engineers worked to resolve the configuration issue.</span></span>  
<span data-ttu-id="5b43e-136">__後續步驟__︰若您曾在這段期間使用 [與我們連絡] 連結，或傳送郵件給 cgadmin@microsoft.com，但我們未回應，請再試一次。</span><span class="sxs-lookup"><span data-stu-id="5b43e-136">__Next Steps__: If you used the Contact Us link or sent mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="5b43e-137">感謝您的耐心配合。</span><span class="sxs-lookup"><span data-stu-id="5b43e-137">Thank you for your patience.</span></span>



## <a name="7132016---download-items-failed"></a><span data-ttu-id="5b43e-138">2016/7/13 -下載項目失敗</span><span class="sxs-lookup"><span data-stu-id="5b43e-138">7/13/2016 - Download Items Failed</span></span>

<span data-ttu-id="5b43e-139">__影響摘要__：2016/7/11 到 2016/7/13 之間，有一些客戶出現無法從 PowerShell 資源庫下載項目的問題。</span><span class="sxs-lookup"><span data-stu-id="5b43e-139">__Summary of Impact__: Between 7/11/2016 and 7/13/2016, a subset of customers experienced issues downloading items from the PowerShell Gallery.</span></span> <span data-ttu-id="5b43e-140">此問題可能會顯示在 Install-Module/Install-Script 與 Save-Module/Save-Script 傳回的下列錯誤訊息中︰</span><span class="sxs-lookup"><span data-stu-id="5b43e-140">The issue likely manifested itself in the following error message returned from Install-Module/Install-Script and Save-Module/Save-Script:</span></span>

```powershell
PS C:\> Install-Module xStorage 
PackageManagement\Install-Package : Package 'xStorage' failed to be installed because: 
End of Central Directory record could not be found. At C:\Program 
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1375 char:21 + ... 
$null = PackageManagement\Install-Package @PSBoundParameters + 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + CategoryInfo : InvalidResult: 
(xStorage:String) [Install-Package], Exception + FullyQualifiedErrorId : Package '{0}' 
failed to be installed because: {1},Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage 
```

<span data-ttu-id="5b43e-141">__初步的根本原因__︰工程師確認這是 Azure 內容傳遞網路 (CDN) 的問題。Azure CDN 於 2016/7/11 部署到 PowerShell 資源庫。</span><span class="sxs-lookup"><span data-stu-id="5b43e-141">__Preliminary root cause__: Engineers identified an issue with Azure Content Deliver Network (CDN), which was deployed to the PowerShell Gallery on 7/11/2016.</span></span>  
<span data-ttu-id="5b43e-142">__緩和方法__：工程師停用了 PowerShell 資源庫中的 Azure CDN。</span><span class="sxs-lookup"><span data-stu-id="5b43e-142">__Mitigation__: Engineers disabled Azure CDN in the PowerShell Gallery.</span></span>  
<span data-ttu-id="5b43e-143">__後續步驟__︰調查最根本的原因，並制定解決方法，以避免日後再次發生。</span><span class="sxs-lookup"><span data-stu-id="5b43e-143">__Next Steps__: Investigate the underlying root cause and developing a solution to prevent future occurrences.</span></span>


## <a name="5192016---download-items-failed"></a><span data-ttu-id="5b43e-144">2016/5/19 - 下載項目失敗</span><span class="sxs-lookup"><span data-stu-id="5b43e-144">5/19/2016 - Download Items Failed</span></span>
<span data-ttu-id="5b43e-145">__影響摘要__：2016/5/17 到 2016/5/19 之間，有一些客戶出現無法從 PowerShell 資源庫下載項目的問題。</span><span class="sxs-lookup"><span data-stu-id="5b43e-145">__Summary of Impact__: Between 5/17/2016 and 5/19/2016, a subset of customers experienced issues downloading items from the PowerShell Gallery.</span></span> <span data-ttu-id="5b43e-146">此問題可能會顯示在 Install-Module/Install-Script 與 Save-Module/Save-Script 傳回的下列錯誤訊息中︰</span><span class="sxs-lookup"><span data-stu-id="5b43e-146">The issue likely manifested itself in the following error message returned from Install-Module/Install-Script and Save-Module/Save-Script:</span></span>

```powershell
VERBOSE: Hash for package 'AzureRM.OperationalInsights' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='AzureRM.OperationalInsights', version='1.0.8',
destination='C:\Users\jbritt\AppData\Local\Temp\2\1741355729'
WARNING: Package 'AzureRM.OperationalInsights' failed to be installed because: 
End of Central Directory record could not be found. 
WARNING: Dependent Package 'AzureRM.OperationalInsights' failed to install. 
WARNING: Package 'AzureRM' failed to install. 
VERBOSE: Module 'AzureRM.Network' was saved successfully. 
VERBOSE: Saving the dependency module 'AzureRM.NotificationHubs' with version '1.0.8' for the 
module 'AzureRM'. 
VERBOSE: Module 'AzureRM.NotificationHubs' was saved successfully. 
PackageManagement\Save-Package : Unable to save the module 'AzureRM'. At C:\Program 
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1187 char:21 + 
$null = PackageManagement\Save-Package @PSBoundParameters + 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + 
CategoryInfo : InvalidOperation: (Microsoft.Power...ets.SavePackage:SavePackage) 
[Save-Package], Exception + FullyQualifiedErrorId : ProviderFailToDownloadFile,
Microsoft.PowerShell.PackageManagement.Cmdlets.SavePackage 
```

<span data-ttu-id="5b43e-147">__初步的根本原因__︰工程師確認是 Azure 內容傳遞網路 (CDN)基礎提供者中斷所致。Azure CDN 於 2016/5/17 部署到 PowerShell 資源庫。</span><span class="sxs-lookup"><span data-stu-id="5b43e-147">__Preliminary root cause__: Engineers identified an outage in the underlying provider of Azure Content Deliver Network (CDN), which was deployed to the PowerShell Gallery on 5/17/2016.</span></span>  
<span data-ttu-id="5b43e-148">__緩和方法__：工程師停用了 PowerShell 資源庫中的 Azure CDN。</span><span class="sxs-lookup"><span data-stu-id="5b43e-148">__Mitigation__: Engineers disabled Azure CDN in the PowerShell Gallery.</span></span>  
<span data-ttu-id="5b43e-149">__後續步驟__︰調查最根本的原因，並制定解決方法，以避免日後再次發生。</span><span class="sxs-lookup"><span data-stu-id="5b43e-149">__Next Steps__: Investigate the underlying root cause and developing a solution to prevent future occurrences.</span></span>

