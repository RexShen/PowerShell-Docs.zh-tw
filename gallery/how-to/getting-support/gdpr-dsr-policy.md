---
ms.date: 03/27/2018
contributor: JKeithB
keywords: 資源庫,powershell,psgallery,GDPR
title: PowerShell 資源庫 GDPR 合規性
ms.openlocfilehash: fb1191d8a1cd12d5994e41238c384eb504d0c261
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002645"
---
# <a name="powershell-gallery-gdpr-compliance"></a>PowerShell 資源庫 GDPR 合規性

## <a name="overview"></a>概觀

一般資料保護規定 (GDPR) 的歐洲隱私權法於 2018 年 5 月生效。
GDPR 對公司、政府機關、非營利組織以及其他為歐盟 (EU) 居民提供產品與服務的組織，或是收集及分析與歐盟居民相關資料的組織，加諸了新的規範。
無論您身於何處均適用 GDPR。

> [!NOTE]
> 本文提供如何從 PowerShell 資源庫中刪除個人資料的步驟，且您可透過這些步驟，符合 GDPR 所規範的義務。 如果您正在尋找與 GDPR 相關的一般資訊，請參閱[服務信任入口網站的 GDPR 區段](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted)。

## <a name="personally-identifiable-data"></a>可識別個人的資料

PowerShell 資源庫會儲存下列由使用者所提供的資訊，而其中可能包含個人資訊：

- PowerShell 資源庫帳戶
- 發行至 PowerShell 資源庫的套件
- 與 PowerShell 資源庫小組來往的電子郵件

大部分的使用者不會建立 PowerShell 資源庫帳戶。
除非您將會發行套件或是使用 PowerShell 資源庫中的「連絡擁有者」功能，否則不需要帳戶。
除了由使用者所開始的往來電子郵件之外，PowerShell 資源庫對於尚未建立帳戶的使用者，不會儲存其可識別個人之資料。

建立 PowerShell 資源庫帳戶的使用者，可以對 PowerShell 資源庫發行套件。
這些套件應為 PowerShell 程式碼，但可能包含內含個人資訊的其他資訊。
下列資訊會顯示您可如何取得已發行至 PowerShell 資源庫的所有套件。

## <a name="dsr-export-of-powershell-gallery-data"></a>PowerShell 資源庫資料的 DSR 匯出

下列各節會解釋如何匯出儲存在 PowerShell 資源庫中的資訊，以及如何要求刪除此資訊，來說明 PowerShell 資源庫如何做到資料主體要求 (DSR)。

### <a name="email"></a>電子郵件

往來電子郵件可包含下列任一項：

- 若程式碼分析掃描偵測到已發行至 PowerShell 資源庫的任何套件發生問題，會傳送電子郵件給 PowerShell 資源庫套件的擁有者
- 任何人皆可使用 [與我們連絡] 頁面 [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com) 中的電子郵件地址，傳送電子郵件給 PowerShell 資源庫小組
- 使用 PowerShell 資源庫中「連絡擁有者」功能的註冊使用者，可傳送電子郵件給 PowerShell 資源庫中套件的擁有者

與 PowerShell 資源庫往來的電子郵件，保留原則為 90 天，以進行可能的安全性調查，探索在 PowerShell 資源庫上是否有惡意程式碼。
電子郵件依原則將會在 90 天後刪除。

您可申請前 90 天對您電子郵件地址以及 PowerShell 資源庫所傳送或接收之所有電子郵件的副本。
若要申請這些往來郵件，請傳送電子郵件至 [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)，標題請寫：「與此帳戶相關之電子郵件的 DSR 申請」。
在訊息內文中，請陳述您要申請的資訊 (例如：請傳送給我所有此電子郵件地址所傳送或接收之電子郵件。)您可在 7 個工作天內，收到發出申請 90 天內您電子郵件地址相關的所有電子郵件。

### <a name="powershell-gallery-account-information"></a>PowerShell 資源庫帳戶資訊

若您已建立了 PowerShell 資源庫帳戶，即可以採取下列步驟，找到儲存在 PowerShell 資源庫中的所有個人資訊：

1. 請登入 PowerShell 資源庫，然後按一下您的使用者名稱
2. 下一個顯示的頁面為 [帳戶] 頁面，其會顯示為 PowerShell 資源庫帳戶所使用的電子郵件地址

若您在 PowerShell 資源庫中建立了多個帳戶，則必須為每個帳戶重複這些步驟。

### <a name="packages-in-the-powershell-gallery"></a>PowerShell 資源庫中的套件

為便於匯出已發行至 PowerShell 資源庫的套件，我們已將指令碼 "GetPSGalleryItemsForAuthor" 發行至 PowerShell 資源庫。
此指令碼會將每個套件的每一個版本之複本，依據套件中所儲存的建立者資訊，匯出置入 PowerShell 資源庫中。

> [!NOTE]
> 當您發行您的套件時，會在套件資訊清單中儲存建立者。
> 不保證作者會與您用於 PowerShell 資源庫中之帳戶，是相同的身分識別。
> 若您在 [作者] 欄位中使用了一些其他的值，則在使用此指令碼時，必須提供該值。

您可使用下列 PowerShell 命令，下載此指令碼：

```powershell
Save-Script Get-repository psgallery
```

然後您可執行下列 PowerShell 命令，直接執行該指令碼：

```powershell
# cd <local folder location>
.\GetPSGalleryItemsForAuthor.ps1
```

系統會提示您提供建立者以及您希望儲存套件之系統上的資料夾。

## <a name="deleting-personal-data-from-the-powershell-gallery"></a>從 PowerShell 資源庫刪除個人資料

若要刪除您的 PowerShell 資源庫帳戶或任何您在 PowerShell 資源庫中所擁有的套件，請傳送電子郵件至 cgadmin@microsoft.com，標題請寫：「與此帳戶相關之電子郵件的 DSR 申請」。
在訊息內文中，請陳述您希望刪除的資訊。 例如：

- 請刪除我的套件「套件名稱」之版本 x.y.z
- 請刪除我的套件「套件名稱」之所有版本
- 請刪除我的 PowerShell 資源庫帳戶

PowerShell 資源庫系統管理員將會於 7 個工作天內回覆您。
指定的套件將於提出申請之後的 30 天內刪除。
