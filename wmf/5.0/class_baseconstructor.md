---
ms.date: 2017-06-12T00:00:00.000Z
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,設定"
ms.openlocfilehash: 1fd6d80d6b7effb4bd98c1594d64e531c4e5c9b5
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2017
---
# <a name="call-base-class-constructor"></a>呼叫基底類別建構函式

若要從子類別中呼叫基底類別建構函式，請使用關鍵字 **base**：

```powershell
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

```powershell
class C : B
{
    C([int]$c) {}
}
```

