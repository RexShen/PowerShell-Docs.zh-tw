---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_unlist_items
ms.openlocfilehash: 8fa09c77e144f14bf0fd3493dff7650897100715
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
<a id="unlisting-items" class="xliff"></a>
# 將項目從清單移除

**為什麼從 PowerShell 資源庫移除項目未公開為選項？**

PowerShell 資源庫不支援使用者永久刪除項目。 這可讓其他人對您的項目採取相依性，而不需要擔心日後可能中斷。 例如，如果 Pester 模組相依於 Azure 模組，但 Azure 模組已從資源庫移除，使用者就無法再使用 Pester 模組。

與其移除項目，您可以改為將其移出清單。

**在 PowerShell 資源庫將項目移出清單會如何？**

在 PowerShell 資源庫將模組或指令碼等項目移出清單，就會將其從 [項目] 索引標籤移除。
此外，使用搜尋列將無法探索到移出清單的項目。
只有指定項目的確切名稱與版本，才能下載移出清單的項目。
因為如此，將項目移除清單不會中斷相依其上的其他模組或指令碼。

若要將您的項目移出清單，請前往項目詳細資料頁面，然後選取 [刪除項目]。 取消選取 [列出] 核取方塊，然後按一下 [儲存]。

**如何移除項目？**

如果您遇到必須刪除項目的情況，請連絡 PowerShell 資源庫系統管理員。
合理的刪除案例為：
- 侵害著作權的問題。
- 項目包含可能有害的內容。
- 項目包含敏感性資料。

若要提交「刪除項目要求」給 PowerShell 資源庫系統管理員，請前往項目的詳細資料頁面，然後選取 [連絡支援服務]。  


