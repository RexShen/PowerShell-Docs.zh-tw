---
title: "WMF 5.1 (預覽) 的已知問題"
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: krishna
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 57049ff138604b0e13c8fd949ae14da05cb03a4b
ms.openlocfilehash: 387ebc0467b9f154444292f391af0f4b77123639

---

#WMF 5.1 (預覽) 的已知問題 #

> 注意：本資訊尚屬初始版本，後續有可能變更。

##Pester 問題
在此版本中，當您在 Nano 伺服器使用 Pester 時有兩個問題應該要注意︰

* 因為完整 CLR 和核心 CLR 之間的差異，針對 Pester 本身執行測試時會導致某些失敗。 尤其 XmlDocument 不提供類型驗證方法。 已知嘗試驗證 NUnit 輸出記錄檔結構描述的六項測試會失敗。 
* 目前一項程式碼涵蓋範圍測試失敗，因為 Nano 伺服器沒有 *WindowsFeature* DSC 資源。 不過，這些失敗通常是無害的，可以放心地忽略。


<!--HONumber=Jul16_HO3-->


