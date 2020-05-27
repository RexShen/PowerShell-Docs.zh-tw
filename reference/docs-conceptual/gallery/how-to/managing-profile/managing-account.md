---
ms.date: 09/05/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: PowerShell 資源庫帳戶設定
ms.openlocfilehash: 7f67311b42123f247a00a9c7a5bf775685b64d48
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560452"
---
# <a name="powershell-gallery-account-settings"></a>PowerShell 資源庫帳戶設定

您的 PowerShell 資源庫帳戶是連結至身分識別的公開顯示名稱。 該身分識別可以是 Microsoft ID，例如 `user@hotmail.com` 或 `user@outlook.com`，也可以是 Azure Active Directory (AAD) 帳戶。

PowerShell 資源庫提供下列帳戶設定：

- 與 PowerShell 資源庫帳戶建立關聯的電子郵件帳戶
- 從 PowerShell 資源庫傳送電子郵件通知的選項
- 與 PowerShell 資源庫帳戶建立關聯的使用者帳戶
- 與 PowerShell 資源庫帳戶建立關聯的圖片

## <a name="email-address"></a>電子郵件地址

電子郵件地址是 PowerShell 資源庫通知的目的地。 它不一定要與登入帳戶相符。 您可以使用有權存取的任何電子郵件帳戶。 PowerShell 資源庫絕不會將您的電子郵件地址提供給其他使用者。

![變更電子郵件地址](media/managing-account/PSGallery_AcccountEmailAddress.png)

當您輸入新的電子郵件地址時，PowerShell 資源庫會將驗證郵件傳送至該位址。 驗證郵件含有連回 PowerShell 資源庫以完成變更程序的連結。 在您完成驗證程序之前，所有通知都會傳送至先前的地址。

## <a name="email-notifications"></a>電子郵件通知

PowerShell 資源庫提供下列通知選項：

- 使用者可以透過 PowerShell 資源庫與我連絡
- 當使用我的帳戶將套件推送至 PowerShell 資源庫時通知我

![變更電子郵件地址](media/managing-account/PSGallery_AccountEmailOptions.png)

如頁面所示，無法停用來自 PowerShell 資源庫的重大通知。
其中包括：

- 安全性通知
- 來自 PowerShell 資源庫管理員的帳戶管理通知
- PowerShell 資源庫針對提交所執行的測試相關通知

## <a name="change-your-login-account"></a>變更您的登入帳戶

若要變更登入帳戶，您必須使用目前的帳戶登入。 請使用下列步驟以完成變更。

![[登入帳戶] 設定](media/managing-account/PSGallery_LoginAccountSettings.png)

1. 按一下 [變更帳戶]  。 快顯視窗說明變更登入帳戶會套用至在 PowerShell 資源庫中使用該帳戶的所有情況。 檢閱資訊，然後按一下 [確定]  繼續。

   ![[登入帳戶] 設定](media/managing-account/PSGallery_LoginAccountChange-1.png)

2. 接著系統會提示您使用「新帳戶」  登入。

   ![[登入帳戶] 設定](media/managing-account/PSGallery_LoginAccountChange-2.png)

3. 當您按一下 [下一步]  時，您會看到一則訊息，指出您使用目前的帳戶登入。
   按一下 [登出並以不同帳戶登入]  。

   ![[登入帳戶] 設定](media/managing-account/PSGallery_LoginAccountChange-3.png)

4. 輸入新帳戶的密碼。 輸入密碼之後，您會回到 [帳戶設定] 頁面，其中顯示登入帳戶已更新。

## <a name="enable-two-factor-authentication-2fa"></a>啟用雙因素驗證 (2FA)

建議對手動發佈至 PowerShell 資源庫的所有使用者進行雙因素驗證。 若要啟用雙因素驗證，登入帳戶必須註冊至少兩個驗證格式。 一個是密碼，其他格式可以是：

- 可接收簡訊的電話號碼
- 已註冊的驗證器應用程式，例如適用於您行動電話的 Microsoft Authenticator

您必須在 AAD 帳戶資訊或 Microsoft ID 帳戶安全性設定中設定這些驗證格式。

一旦啟用 2FA，每次登入 PowerShell 資源庫，都必須使用所設定的驗證格式進行驗證。

> [!IMPORTANT]
> 針對 PowerShell 資源庫網站啟用雙因素驗證不需要您在每次使用登入帳戶時啟用 2FA。 如需詳細資訊，請參閱[關於雙步驟驗證](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification)。

## <a name="change-your-profile-picture"></a>變更您的個人資料圖片

PowerShell 資源庫依賴 Gravatar 儲存及顯示與您個人資料建立關聯的圖片。 若要更新您的個人資料影像，請前往 [Gravatar.com](http://www.gravatar.com/)。
