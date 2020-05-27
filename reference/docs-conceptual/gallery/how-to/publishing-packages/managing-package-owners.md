---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 管理套件擁有者
ms.openlocfilehash: 72a3ff72818c5461c74d46de5689e2d6c59b19bf
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564664"
---
# <a name="managing-package-owners"></a>管理套件擁有者

PowerShell 資源庫中套件的擁有權，是由將該套件發行到資源庫的人所定義。
有時候，這個中繼資料必須在初步發行套件之後另外管理，這表示擁有者中繼資料必須能在不變動套件的情況下進行變動。

所有的套件擁有者都是對等的。
這表示任何套件擁有者均可發行新版本的套件。 這也表示任何套件擁有者都可以移除任何其他的套件擁有者。
沒有任何擁有者的權限高於其他擁有者。

## <a name="setting-a-packages-initial-owner"></a>設定套件的初始擁有者

當新的套件發行到 PowerShell 資源庫時，會依發行該套件的使用者來定義初始擁有者。 這取決於 Publish-Module cmdlet 中使用了誰的 API 金鑰。

## <a name="adding-owners"></a>新增擁有者

一旦將套件發行到 PowerShell 資源庫，就能輕易邀請其他使用者成為套件擁有者。

1. 使用套件目前擁有者的帳戶[登入](https://powershellgallery.com/users/account/LogOn) \(英文\) PowerShell 資源庫。
2. 使用 [Items] \(項目\) 索引標籤瀏覽到套件頁面，然後搜尋或按一下您的使用者名稱，並按一下 [[Manage My Packages]  ](https://www.powershellgallery.com/account/Packages) \(管理我的項目\) \(英文\)。
3. 以套件擁有者身分登入時，左側會有可按一下的 [Manage Owners] \(管理擁有者\) 連結。
4. 輸入要新增為擁有者的人員使用者名稱，然後按一下 [新增]。
5. 新的共同擁有者接著便會收到電子郵件，邀請他成為套件擁有者。
6. 使用者按一下連結後便能成為完整的共同擁有者，並對套件有完整控制權，包括能夠移除其他身為擁有者的使用者。

**注意**：在新擁有者確認擁有權之前，其將「不會」  被列為套件的擁有者。
檢視 [管理擁有者]  頁面時，您會在目前的使用者看到「等待核准」項目。
該邀請可被移除；就像其他擁有者也可被移除。
此邀請程序可防止使用者將其他使用者誤加為套件擁有者。

請注意，"Authors" 中繼資料單純為自由格式的文字，只有 "Owners" 受到控制。

## <a name="removing-owners"></a>移除擁有者

當套件有多個擁有者，而需要移除其中一個時，程序很簡單：

1. 使用套件目前擁有者的帳戶[登入](https://powershellgallery.com/users/account/LogOn) \(英文\) PowerShell 資源庫；
2. 使用 [Packages] \(套件\) 索引標籤瀏覽到套件頁面，然後搜尋或按一下您的使用者名稱，並按一下 [[Manage My Packages]  ](https://www.powershellgallery.com/account/Packages) \(管理我的項目\) \(英文\)。
3. 以套件擁有者身分登入時，左側會有可按一下的 [Manage Owners] \(管理擁有者\) 連結。
4. 在要移除的擁有者旁按一下 [移除] 連結。

## <a name="transferring-package-ownership"></a>移轉套件擁有權

我們有時候會收到想要將套件擁有權從一個使用者移轉到另一個使用者的支援要求，但使用者在大多數的情況下都可以自行完成此工作。
只要結合上述兩項功能，就能將擁有權從一位使用者移轉給另一位。

1. 目前擁有者邀請新使用者成為共同擁有者，然後心使用者接受邀請；
2. 新使用者從擁有者清單移除舊使用者。

此要求源於多種形式，但程序運作方式都一樣。

- 套件擁有權正從一個開發人員變更至另一個開發人員
- 意外使用錯誤帳戶發行套件

## <a name="orphaned-packages"></a>孤立的套件

發生了最後一個案例，但不常發生。
套件已被孤立，且無法使用唯一的套件擁有者帳戶來新增擁有者。
這裡有這個案例的一些範例：

- 擁有者帳戶與已不存在的電子郵件地址建立關聯，且使用者忘記密碼
- 註冊的擁有者已離開生產該套件的公司且已經失聯，因而無法更新套件擁有權
- 由於一個只會影響少數套件的錯誤 (bug)，使得該套件在資源庫上沒有任何擁有者

PowerShell 資源庫系統管理員可存取任何套件的 [Manage Owners] \(管理擁有者\) 連結。
如果您是套件的正當擁有者，但無法連絡到目前的擁有者以取得擁有權權限，請使用資源庫上的 [Report Abuse] \(檢舉不當使用\) 連結來連絡 PowerShell 資源庫系統管理員。
我們會進行驗證您對該套件之擁有權的程序。
如果我們判斷您是該套件的擁有者，就會使用該套件的 [Manage Owners] \(管理擁有者\) 連結，並傳送成為擁有者的邀請給您。
我們只會在驗證您應為擁有者後這樣做，而且其程序會因情況而有所不同。
通常，我們會使用套件的專案 URL 來尋找連絡專案擁有者的方法，但我們可能也會使用 Twitter、電子郵件或其他方法來連絡專案擁有者。
