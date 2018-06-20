---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: 9486fdbaeca66c83551564c76ce47482f77c36b9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225601"
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
