---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "限制命令時的考量"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 9f3f79a29e0fb7ec5a5111284bb7985548e17749

---

### 限制命令時的考量
此步驟還有一個值得提出的重點。
所有透過 JEA 公開的功能都必須位於系統管理員限制的區域中。
非系統管理員使用者不應該具有修改透過 JEA 端點使用之指令碼的能力。

另一個相關注意事項是，請務必不要讓 JEA 使用者可以覆寫 JEA 設定，以及將其 JEA 工作階段中的指令碼列入允許清單。
公開 `Copy-Item` 等命令時請格外小心！




<!--HONumber=Jul16_HO1-->


