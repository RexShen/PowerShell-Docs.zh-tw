---
ms.date: 06/12/2017
title: 如何從 PowerShell 資源庫刪除套件
description: 如何從 PowerShell 資源庫刪除套件
ms.openlocfilehash: e02fad61ce8ab808ba9fdf4ab16b9ae236a49e80
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662567"
---
# <a name="deleting-packages"></a>刪除套件

PowerShell 資源庫不支援永久刪除套件，因為這樣會中斷任何仰賴該套件維持可用的人員。

相反地，PowerShell 資源庫支援將套件「取消列出」，該操作可於網站上的套件管理頁面中完成。 將套件取消列出後，在 PowerShell 資源庫上瀏覽及使用 PowerShellGet 命令時，該套件都不會在搜尋及任何套件列表中顯示。
不過，該項目仍可透過指定其確切版本維持可供下載，其中確切版本可允許自動化的指令碼繼續運作。

如果您遇到例外狀況，且認為必須刪除您的其中一個套件時，PowerShell 資源庫小組可以手動處理此狀況。 例如，若發生著作權侵權問題，或是可能有害的內容，即有充分的理由可將其刪除。 在該種情況下，您應透過 [PowerShell 資源庫](https://www.PowerShellGallery.com) \(英文\) 提交支援要求。
