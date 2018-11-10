---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 刪除套件
ms.openlocfilehash: ca5e68fcad52e4c7561d2c2b3858228652f22e0b
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003744"
---
# <a name="deleting-packages"></a>刪除套件

PowerShell 資源庫不支援永久刪除套件，因為這樣會中斷任何仰賴該套件維持可用的人員。

相反地，PowerShell 資源庫支援將套件「取消列出」，該操作可於網站上的套件管理頁面中完成。
將套件取消列出後，在 PowerShell 資源庫上瀏覽及使用 PowerShellGet 命令時，該套件都不會在搜尋及任何套件列表中顯示。
不過，該項目仍可透過指定其確切版本維持可供下載，其中確切版本可允許自動化的指令碼繼續運作。

如果您遇到例外狀況，且認為必須刪除您的其中一個套件時，PowerShell 資源庫小組可以手動處理此狀況。
例如，若發生著作權侵權問題，或是可能有害的內容，即有充分的理由可將其刪除。
在該種情況下，您應透過 [PowerShell 資源庫](http://www.PowerShellGallery.com) \(英文\) 提交支援要求。
