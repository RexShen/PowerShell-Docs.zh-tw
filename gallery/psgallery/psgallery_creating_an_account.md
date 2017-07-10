---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: "建立 PowerShell 資源庫帳戶"
ms.openlocfilehash: e21575320f220c1ba7ecd9bd464a814b3ebf49d9
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
<a id="creating-a-powershell-gallery-account" class="xliff"></a>
## 建立 PowerShell 資源庫帳戶

將任何項目發行至「PowerShell 資源庫」之前，必須先建立「PowerShell 資源庫」帳戶。 「PowerShell 資源庫」帳戶必須連結至已啟用電子郵件功能的 Azure Active Directory 帳戶，或是 Microsoft 電子郵件帳戶 (網域為 outlook.com、hotmail.com 等)

若要建立「PowerShell 資源庫」帳戶，請移至 https://PowerShellGallery.com 並按一下 [註冊] (請參閱下圖)。 

![註冊新帳戶](./images/CreatingAccount-Register.png)

在下一個頁面中，若要使用 Azure Active Directory 帳戶，請選取 [公司或學校帳戶]，然後使用您的帳戶登入。 若要使用 Microsoft 帳戶 (例如 Hotmail.com 或 Outlook.com 網域中的帳戶)，請選擇 [個人帳戶]，然後登入。 

登入之後，系統會提示您建立用於「PowerShell 資源庫」的使用者名稱。 請檢閱所連結的「使用規定」和「隱私權原則」、輸入使用者名稱，然後按一下 [註冊]。

注意：此帳戶名稱建立後即無法變更。  
如需其他相關的詳細資料，請參閱[管理項目擁有者](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/managing-item-owners)。

<a id="recommended-practices-for-powershell-gallery-accounts" class="xliff"></a>
## 建議的 PowerShell 資源庫帳戶做法

主動監視與「PowerShell 資源庫」帳戶搭配使用的電子郵件帳戶相當重要。
與「PowerShell 資源庫」項目擁有者進行的一切溝通，都會透過與「PowerShell 資源庫」帳戶關聯的電子郵件地址進行。
如果我們無法連絡項目擁有者，在某些情況下，作業小組可能就必須刪除項目。

將項目發行至「PowerShell 資源庫」的組織通常會在 Outlook.com 或另一個 Microsoft 帳戶網域中針對該用途建立一個獨特的帳戶。
在許多情況下，該帳戶並不會受到定期監視。 針對該情況，最佳做法是使用「Outlook 轉寄設定」，將電子郵件傳送到其他將受到項目擁有者監視的帳戶 (通常是組織內的帳戶)。

如果項目有多個關聯的擁有者，系統就會將來自「PowerShell 資源庫」的所有溝通傳送給所有擁有者。
如需有關為項目新增擁有者的其他詳細資料，請參閱[管理項目擁有者](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/managing-item-owners)。 

