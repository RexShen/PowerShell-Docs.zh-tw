---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: 9486fdbaeca66c83551564c76ce47482f77c36b9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="call-base-class-constructor"></a><span data-ttu-id="1f106-102">呼叫基底類別建構函式</span><span class="sxs-lookup"><span data-stu-id="1f106-102">Call Base Class Constructor</span></span>

<span data-ttu-id="1f106-103">若要從子類別中呼叫基底類別建構函式，請使用關鍵字 **base**：</span><span class="sxs-lookup"><span data-stu-id="1f106-103">To call a base class constructor from a subclass, use the keyword **base**:</span></span>

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

<span data-ttu-id="1f106-104">如果基底類別有預設的 (無參數) 建構函式，您可以省略明確的建構函式呼叫︰</span><span class="sxs-lookup"><span data-stu-id="1f106-104">If a base class has a default (no parameter) constructor, you can omit an explicit constructor call:</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```
