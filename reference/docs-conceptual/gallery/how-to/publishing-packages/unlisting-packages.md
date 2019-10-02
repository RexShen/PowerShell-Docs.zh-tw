---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 將套件移出清單
ms.openlocfilehash: fb66fd23dae1d4640056a764c31426f61f56d910
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328269"
---
# <a name="unlisting-packages"></a>將套件移出清單

**為什麼從 PowerShell 資源庫移除套件未公開為選項？**

PowerShell 資源庫不支援使用者永久刪除套件。
這可讓其他人對您的套件採取相依性，而不需要擔心日後可能中斷。
例如，如果 Pester 模組相依於 Azure 模組，但 Azure 模組已從資源庫移除，使用者就無法再使用 Pester 模組。

與其移除套件，您可以改為將其移出清單。

**在 PowerShell 資源庫將套件移出清單會如何？**

在 PowerShell 資源庫將模組或指令碼等套件移出清單，就會將其從 [套件] 索引標籤移除。此外，使用搜尋列將無法探索到移出清單的套件。
只有指定套件的確切名稱與版本，才能下載移出清單的套件。
因為如此，將套件移出清單不會中斷相依其上的其他模組或指令碼。

若要將您的套件移出清單，請前往套件詳細資料頁面，然後選取 [刪除模組]。 取消選取 [列出] 核取方塊，然後按一下 [儲存]。

**如何移除套件？**

如果您遇到必須刪除套件的情況，請連絡 PowerShell 資源庫系統管理員。
合理的刪除案例為：
- 侵害著作權的問題。
- 套件包含可能有害的內容。
- 套件包含敏感性資料。

若要提交「刪除套件要求」給 PowerShell 資源庫系統管理員，請前往套件的詳細資料頁面，然後選取 [連絡支援服務]。
