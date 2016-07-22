---
title: "改善的提取伺服器登錄"
author: jaimeo
contributor: Indhu Sivaramakrishnan
translationtype: Human Translation
ms.sourcegitcommit: e39aa2e5cbda0c83e24e21c4459d957d8baaff25
ms.openlocfilehash: d9f7dea63e6541b673ac6be5ccad59368b301440

---

## 改善的提取伺服器登錄 ##

在舊版的 WMF 中，在使用 ESENT 資料庫時，同時登錄/報告 DSC 提取伺服器的要求，會導致 LCM 無法像案例那樣登錄及/或報告。 在這種情況下，提取伺服器的事件記錄檔就會出現「執行個體名稱已在使用中」的錯誤。
這是因為在多執行緒案例中使用不正確的模式存取 ESENT 資料庫。 WMF 5.1 已修正此問題。 WMF 5.1 中可以同時正常登錄或報告 (涉及 ESENT 資料庫)。 只有 ESENT 資料庫會發生這個問題，OLEDB 資料庫無此問題。 



<!--HONumber=Jul16_HO3-->


