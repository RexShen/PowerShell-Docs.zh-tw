---
title: "WMF 5.1 (預覽) 的已知問題"
ms.date: 2016-07-13
keywords: "PowerShell、DSC、WMF"
description: 
ms.topic: article
author: krishna
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 3dde62efa7ba595ed5160cc81b4e2b17a54e52a2
ms.openlocfilehash: d4c9e88ddd6cfaec611527d19d00cbd4db9f5d1d

---

#WMF 5.1 (預覽) 的已知問題 #

> 注意：本資訊尚屬初始版本，後續有可能變更。

##以系統管理員身分啟動 PowerShell 捷徑
安裝 WMF 時，如果您嘗試以系統管理員身分從捷徑啟動 PowerShell，可能會收到「未指定的錯誤」訊息。
請以非系統管理員身分重新開啟捷徑，捷徑現在將會以系統管理員身分正常運作。

##Pester
在此版本中，當您在 Nano 伺服器使用 Pester 時有兩個問題應該要注意︰

* 因為完整 CLR 和核心 CLR 之間的差異，針對 Pester 本身執行測試時會導致某些失敗。 尤其 XmlDocument 不提供類型驗證方法。 已知有六個嘗試驗證 NUnit 輸出記錄檔結構描述的測試會失敗。 
* 有一個程式碼涵蓋範圍測試失敗起因於 Nano 伺服器沒有 *WindowsFeature* DSC 資源。 不過，這些失敗通常是無害的，可以放心地忽略。

##作業驗證 

* Microsoft.PowerShell.Operation.Validation 模組的 Update-Help 會因為無法運作的說明 URI 而失敗



<!--HONumber=Sep16_HO4-->


