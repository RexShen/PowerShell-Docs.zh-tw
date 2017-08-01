---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,設定"
ms.openlocfilehash: 6caff8c06174a1dcb990ed8e5062ccca5848dbb8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="convert-string"></a>Convert-String
**Convert-String** 公開「像變魔術一樣取代」的功能。 提供範例說明您希望轉換前後文字長什麼樣子，**Convert-String** 就會自動設定文字的格式。 以下是示範，輸入某人的名字和姓氏，然後取代為姓氏、逗號、名字首字母和一個點。 試試看使用 Regex，就會知道要花多久時間。

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```

