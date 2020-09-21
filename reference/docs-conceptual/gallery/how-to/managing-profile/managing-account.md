---
ms.date: 09/05/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: PowerShell 資源庫帳戶設定
ms.openlocfilehash: b71c7f0658c24ec2eeddb050e48b777a37c11917
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87771782"
---
# <a name="powershell-gallery-account-settings"></a><span data-ttu-id="3bf0c-103">PowerShell 資源庫帳戶設定</span><span class="sxs-lookup"><span data-stu-id="3bf0c-103">PowerShell Gallery Account Settings</span></span>

<span data-ttu-id="3bf0c-104">您的 PowerShell 資源庫帳戶是連結至身分識別的公開顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="3bf0c-104">Your PowerShell Gallery account is a publicly visible name that is linked to an identity.</span></span> <span data-ttu-id="3bf0c-105">該身分識別可以是 Microsoft ID，例如 `user@hotmail.com` 或 `user@outlook.com`，也可以是 Azure Active Directory (AAD) 帳戶。</span><span class="sxs-lookup"><span data-stu-id="3bf0c-105">That identity is either a Microsoft ID, like `user@hotmail.com` or `user@outlook.com`, or an Azure Active Directory (AAD) account.</span></span>

<span data-ttu-id="3bf0c-106">PowerShell 資源庫提供下列帳戶設定：</span><span class="sxs-lookup"><span data-stu-id="3bf0c-106">The PowerShell Gallery provides the following account settings:</span></span>

- <span data-ttu-id="3bf0c-107">與 PowerShell 資源庫帳戶建立關聯的電子郵件帳戶</span><span class="sxs-lookup"><span data-stu-id="3bf0c-107">The email account associated with your PowerShell Gallery account</span></span>
- <span data-ttu-id="3bf0c-108">從 PowerShell 資源庫傳送電子郵件通知的選項</span><span class="sxs-lookup"><span data-stu-id="3bf0c-108">Options for email notifications sent from the PowerShell Gallery</span></span>
- <span data-ttu-id="3bf0c-109">與 PowerShell 資源庫帳戶建立關聯的使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="3bf0c-109">The user account associated with your PowerShell Gallery account</span></span>
- <span data-ttu-id="3bf0c-110">與 PowerShell 資源庫帳戶建立關聯的圖片</span><span class="sxs-lookup"><span data-stu-id="3bf0c-110">The picture associated with your PowerShell Gallery account</span></span>

## <a name="email-address"></a><span data-ttu-id="3bf0c-111">電子郵件地址</span><span class="sxs-lookup"><span data-stu-id="3bf0c-111">Email address</span></span>

<span data-ttu-id="3bf0c-112">電子郵件地址是 PowerShell 資源庫通知的目的地。</span><span class="sxs-lookup"><span data-stu-id="3bf0c-112">The email address is the destination for PowerShell Gallery notifications.</span></span> <span data-ttu-id="3bf0c-113">它不一定要與登入帳戶相符。</span><span class="sxs-lookup"><span data-stu-id="3bf0c-113">It does not have to match the login account.</span></span> <span data-ttu-id="3bf0c-114">您可以使用有權存取的任何電子郵件帳戶。</span><span class="sxs-lookup"><span data-stu-id="3bf0c-114">You may use any email account you have access to.</span></span> <span data-ttu-id="3bf0c-115">PowerShell 資源庫絕不會將您的電子郵件地址提供給其他使用者。</span><span class="sxs-lookup"><span data-stu-id="3bf0c-115">Your email address is never directly provided by the PowerShell Gallery to other users.</span></span>

![變更電子郵件地址](media/managing-account/PSGallery_AcccountEmailAddress.png)

<span data-ttu-id="3bf0c-117">當您輸入新的電子郵件地址時，PowerShell 資源庫會將驗證郵件傳送至該位址。</span><span class="sxs-lookup"><span data-stu-id="3bf0c-117">When you enter a new email address, the PowerShell Gallery sends a verification mail to that address.</span></span> <span data-ttu-id="3bf0c-118">驗證郵件含有連回 PowerShell 資源庫以完成變更程序的連結。</span><span class="sxs-lookup"><span data-stu-id="3bf0c-118">The verification mail contains a link back to the PowerShell Gallery to complete the change process.</span></span> <span data-ttu-id="3bf0c-119">在您完成驗證程序之前，所有通知都會傳送至先前的地址。</span><span class="sxs-lookup"><span data-stu-id="3bf0c-119">Until you complete the verification process, all notifications are sent to the previous address.</span></span>

## <a name="email-notifications"></a><span data-ttu-id="3bf0c-120">電子郵件通知</span><span class="sxs-lookup"><span data-stu-id="3bf0c-120">Email notifications</span></span>

<span data-ttu-id="3bf0c-121">PowerShell 資源庫提供下列通知選項：</span><span class="sxs-lookup"><span data-stu-id="3bf0c-121">PowerShell Gallery provides the following notification options:</span></span>

- <span data-ttu-id="3bf0c-122">使用者可以透過 PowerShell 資源庫與我連絡</span><span class="sxs-lookup"><span data-stu-id="3bf0c-122">Users can contact me through the PowerShell Gallery</span></span>
- <span data-ttu-id="3bf0c-123">當使用我的帳戶將套件推送至 PowerShell 資源庫時通知我</span><span class="sxs-lookup"><span data-stu-id="3bf0c-123">Notify me when an package is pushed to the PowerShell Gallery using my account</span></span>

![選取電子郵件地址各選項](media/managing-account/PSGallery_AccountEmailOptions.png)

<span data-ttu-id="3bf0c-125">如頁面所示，無法停用來自 PowerShell 資源庫的重大通知。</span><span class="sxs-lookup"><span data-stu-id="3bf0c-125">As noted on the page, critical notifications from the PowerShell Gallery can't be disabled.</span></span>
<span data-ttu-id="3bf0c-126">其中包括：</span><span class="sxs-lookup"><span data-stu-id="3bf0c-126">These include:</span></span>

- <span data-ttu-id="3bf0c-127">安全性通知</span><span class="sxs-lookup"><span data-stu-id="3bf0c-127">Security notifications</span></span>
- <span data-ttu-id="3bf0c-128">來自 PowerShell 資源庫管理員的帳戶管理通知</span><span class="sxs-lookup"><span data-stu-id="3bf0c-128">Account management notifications from PowerShell Gallery administrators</span></span>
- <span data-ttu-id="3bf0c-129">PowerShell 資源庫針對提交所執行的測試相關通知</span><span class="sxs-lookup"><span data-stu-id="3bf0c-129">Notifications about the tests run by the PowerShell Gallery for submissions you have made</span></span>

## <a name="change-your-login-account"></a><span data-ttu-id="3bf0c-130">變更您的登入帳戶</span><span class="sxs-lookup"><span data-stu-id="3bf0c-130">Change your login account</span></span>

<span data-ttu-id="3bf0c-131">若要變更登入帳戶，您必須使用目前的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="3bf0c-131">To change the login account, you must be signed in with the current account.</span></span> <span data-ttu-id="3bf0c-132">請使用下列步驟以完成變更。</span><span class="sxs-lookup"><span data-stu-id="3bf0c-132">Use the following steps to complete the change.</span></span>

![變更登入帳戶設定](media/managing-account/PSGallery_LoginAccountSettings.png)

1. <span data-ttu-id="3bf0c-134">按一下 [變更帳戶]  。</span><span class="sxs-lookup"><span data-stu-id="3bf0c-134">Click on **Change Account**.</span></span> <span data-ttu-id="3bf0c-135">快顯視窗說明變更登入帳戶會套用至在 PowerShell 資源庫中使用該帳戶的所有情況。</span><span class="sxs-lookup"><span data-stu-id="3bf0c-135">A pop-up window explains that changing the login account applies to all uses of that account in the PowerShell Gallery.</span></span> <span data-ttu-id="3bf0c-136">檢閱資訊，然後按一下 [確定]  繼續。</span><span class="sxs-lookup"><span data-stu-id="3bf0c-136">Review the information, then click **OK** to continue.</span></span>

   ![確認變更 - [確定]/[取消]](media/managing-account/PSGallery_LoginAccountChange-1.png)

2. <span data-ttu-id="3bf0c-138">接著系統會提示您使用「新帳戶」  登入。</span><span class="sxs-lookup"><span data-stu-id="3bf0c-138">You are then prompted to sign in using the _new account_.</span></span>

   ![使用新的帳戶登入](media/managing-account/PSGallery_LoginAccountChange-2.png)

3. <span data-ttu-id="3bf0c-140">當您按一下 [下一步]  時，您會看到一則訊息，指出您使用目前的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="3bf0c-140">When you click **Next**, you see a message that you are signed in using the current account.</span></span>
   <span data-ttu-id="3bf0c-141">按一下 [登出並以不同帳戶登入]  。</span><span class="sxs-lookup"><span data-stu-id="3bf0c-141">Click **Sign out and sign in with a different account**.</span></span>

   ![登出並使用其他帳戶登入](media/managing-account/PSGallery_LoginAccountChange-3.png)

4. <span data-ttu-id="3bf0c-143">輸入新帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="3bf0c-143">Enter the password of the new account.</span></span> <span data-ttu-id="3bf0c-144">輸入密碼之後，您會回到 [帳戶設定] 頁面，其中顯示登入帳戶已更新。</span><span class="sxs-lookup"><span data-stu-id="3bf0c-144">After entering the password, you are returned to the Account Settings page showing you that the login account has been updated.</span></span>

## <a name="enable-two-factor-authentication-2fa"></a><span data-ttu-id="3bf0c-145">啟用雙因素驗證 (2FA)</span><span class="sxs-lookup"><span data-stu-id="3bf0c-145">Enable Two-Factor Authentication (2FA)</span></span>

<span data-ttu-id="3bf0c-146">建議對手動發佈至 PowerShell 資源庫的所有使用者進行雙因素驗證。</span><span class="sxs-lookup"><span data-stu-id="3bf0c-146">Two-factor authentication is recommended for all users who publish manually to the PowerShell Gallery.</span></span> <span data-ttu-id="3bf0c-147">若要啟用雙因素驗證，登入帳戶必須註冊至少兩個驗證格式。</span><span class="sxs-lookup"><span data-stu-id="3bf0c-147">To enable two-factor authentication, the login account must have at least two forms of authentication registered.</span></span> <span data-ttu-id="3bf0c-148">一個是密碼，其他格式可以是：</span><span class="sxs-lookup"><span data-stu-id="3bf0c-148">One is a password and the other forms can be:</span></span>

- <span data-ttu-id="3bf0c-149">可接收簡訊的電話號碼</span><span class="sxs-lookup"><span data-stu-id="3bf0c-149">A phone number that can receive text messages</span></span>
- <span data-ttu-id="3bf0c-150">已註冊的驗證器應用程式，例如適用於您行動電話的 Microsoft Authenticator</span><span class="sxs-lookup"><span data-stu-id="3bf0c-150">A registered authenticator application, such as Microsoft Authenticator for your mobile phone</span></span>

<span data-ttu-id="3bf0c-151">您必須在 AAD 帳戶資訊或 Microsoft ID 帳戶安全性設定中設定這些驗證格式。</span><span class="sxs-lookup"><span data-stu-id="3bf0c-151">These forms of authentication must be configured in your AAD account information or in your Microsoft ID Account Security settings.</span></span>

<span data-ttu-id="3bf0c-152">一旦啟用 2FA，每次登入 PowerShell 資源庫，都必須使用所設定的驗證格式進行驗證。</span><span class="sxs-lookup"><span data-stu-id="3bf0c-152">Once 2FA is enabled, you are required to authenticate using the configured forms of authentication every time you sign in to the PowerShell Gallery.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3bf0c-153">針對 PowerShell 資源庫網站啟用雙因素驗證不需要您在每次使用登入帳戶時啟用 2FA。</span><span class="sxs-lookup"><span data-stu-id="3bf0c-153">Enabling two-factor authentication for the PowerShell Gallery site does not require you to enable 2FA for all uses of your login account.</span></span> <span data-ttu-id="3bf0c-154">如需詳細資訊，請參閱[關於雙步驟驗證](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification)。</span><span class="sxs-lookup"><span data-stu-id="3bf0c-154">For more information, see [About two-step verification](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification).</span></span>

## <a name="change-your-profile-picture"></a><span data-ttu-id="3bf0c-155">變更您的個人資料圖片</span><span class="sxs-lookup"><span data-stu-id="3bf0c-155">Change your profile picture</span></span>

<span data-ttu-id="3bf0c-156">PowerShell 資源庫依賴 Gravatar 儲存及顯示與您個人資料建立關聯的圖片。</span><span class="sxs-lookup"><span data-stu-id="3bf0c-156">The PowerShell Gallery relies on Gravatar to store and display the picture associated with your profile.</span></span> <span data-ttu-id="3bf0c-157">若要更新您的個人資料影像，請前往 [Gravatar.com](http://www.gravatar.com/)。</span><span class="sxs-lookup"><span data-stu-id="3bf0c-157">To update your profile image, visit [Gravatar.com](http://www.gravatar.com/).</span></span>
