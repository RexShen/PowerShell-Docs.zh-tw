---
title: "DSC 類別資源改善"
author: jaimeo
contributor: amitsara
translationtype: Human Translation
ms.sourcegitcommit: e39aa2e5cbda0c83e24e21c4459d957d8baaff25
ms.openlocfilehash: b24e70c1e1aaf71487b00fbccaf6edb0f375b888

---

## DSC 類別資源改善

在此版本中，我們已修正下列已知的 WMF 5.0 問題︰
* 如果類別型 DSC 資源的 Get() 函式傳回複雜/雜湊表類型，Get-DscConfiguration 可能會傳回空值 (null) 或錯誤。
* 當 DSC 設定使用 RunAs 認證時，Get-DscConfiguration 就會傳回錯誤。
* 類別型資源無法用於複合設定中。
* 如果類別型資源有其本身類型的屬性，Start-DscConfiguration 會停止回應。
* 類別型資源不能用為獨佔資源。



<!--HONumber=Jul16_HO3-->


