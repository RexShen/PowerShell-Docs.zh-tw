---
title: "DSC 資源偵錯改善"
author: jaimeo
contributor: amitsara
translationtype: Human Translation
ms.sourcegitcommit: e39aa2e5cbda0c83e24e21c4459d957d8baaff25
ms.openlocfilehash: 33c3fcffdeb281b205ecc48f7cdd470b79e9e068

---


## DSC 資源偵錯改善

在 WMF 5.0 中，並未使用 PowerShell 偵錯工具，所以不會直接停在類別資源方法 (Get/Set/Test)。
我們已修正此問題，現在偵錯工具會停在資源類別方法，和 MOF 資源方法一樣。



<!--HONumber=Jul16_HO3-->


