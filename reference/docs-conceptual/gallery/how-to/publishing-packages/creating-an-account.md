---
ms.date: 09/11/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 建立 PowerShell 資源庫帳戶
ms.openlocfilehash: f43d7e65bb8bf9a9bbdda9790cc622786377fa38
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "78278770"
---
# <a name="creating-a-powershell-gallery-account"></a>建立 PowerShell 資源庫帳戶

您必須先建立 PowerShell 資源庫帳戶，再將任何項目發佈至 PowerShell 資源庫。
PowerShell 資源庫帳戶必須連結至具備電子郵件功能的登入帳戶。 此帳戶可以是 Azure Active Directory 帳戶或 Microsoft ID (例如來自 outlook.com 或 hotmail.com 的電子郵件帳戶)。

若要建立 PowerShell 資源庫帳戶，請前往 [https://PowerShellGallery.com](https://PowerShellGallery.com)，然後按一下 [登入]  ，如下圖所示。

![註冊新帳戶](media/creating-an-account/CreateAccount-Register.png)

若要使用 Azure Active Directory 帳戶，請選取 [公司或學校帳戶]  ，然後使用您的帳戶登入。 若要使用 Microsoft ID，請選擇 [個人帳戶]  並登入。

接下來，系統會提示您建立用於 PowerShell 資源庫的使用者名稱。 請檢閱「使用規定」和「隱私權原則」、輸入使用者名稱，然後按一下 [註冊]  。

> [!NOTE]
> 帳戶名稱建立後即無法變更。 如需詳細資訊，請參閱[管理套件擁有者](managing-package-owners.md)。

## <a name="recommended-practices-for-powershell-gallery-accounts"></a>建議的 PowerShell 資源庫帳戶做法

主動監視與 PowerShell 資源庫帳戶搭配使用的電子郵件帳戶相當重要。 與 PowerShell 資源庫套件擁有者的所有通訊，都會透過此電子郵件地址進行。 如果 PowerShell 資源庫營運小組無法連絡套件擁有者，我們可能就必須刪除套件。

發佈至 PowerShell 資源庫的組織通常會針對該用途建立一個獨特的外部帳戶。 建議您使用電子郵件轉寄功能，將通知轉寄到您組織中的地址。

當多位擁有者與套件建立關聯時，所有 PowerShell 資源庫通知都會傳送給所有擁有者。 如需詳細資訊，請參閱[管理套件擁有者](managing-package-owners.md)。
