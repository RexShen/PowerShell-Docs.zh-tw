---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,設定"
ms.openlocfilehash: 403a79e17b832b5c58fd21a138fcebb8adb76d40
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
<a id="call-base-class-constructor" class="xliff"></a>
# 呼叫基底類別建構函式

若要從子類別中呼叫基底類別建構函式，請使用關鍵字 **base**：

```PowerShell
class A 
{
    [int]$a

    A([int]$a)
    {
        $this.a = $a
    }
}

class B : A
{
    B() : base(103) {}
}

[B]::new().a # return 103
```

如果基底類別有預設的 (無參數) 建構函式，您可以省略明確的建構函式呼叫︰

```PowerShell
class C : B
{
    C([int]$c) {}
}
```

