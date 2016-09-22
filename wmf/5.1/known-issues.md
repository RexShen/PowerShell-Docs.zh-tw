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
ms.sourcegitcommit: f413ba6470985622e55bb4bd175d7c5d4b94c7d9
ms.openlocfilehash: e545d49381a92ef3f7cc6a27316cbfc3a036a8c9

---

#WMF 5.1 (預覽) 的已知問題 #

> 注意：本資訊尚屬初始版本，後續有可能變更。

##Pester
在此版本中，當您在 Nano 伺服器使用 Pester 時有兩個問題應該要注意︰

* 因為完整 CLR 和核心 CLR 之間的差異，針對 Pester 本身執行測試時會導致某些失敗。 尤其 XmlDocument 不提供類型驗證方法。 已知有六個嘗試驗證 NUnit 輸出記錄檔結構描述的測試會失敗。 
* 有一個程式碼涵蓋範圍測試失敗起因於 Nano 伺服器沒有 *WindowsFeature* DSC 資源。 不過，這些失敗通常是無害的，可以放心地忽略。

##作業驗證 

* Microsoft.PowerShell.Operation.Validation 模組的 Update-Help 會因為無法運作的說明 URI 而失敗



<!--HONumber=Sep16_HO3-->


