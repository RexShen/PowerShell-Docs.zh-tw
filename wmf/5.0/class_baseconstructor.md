---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: 424e0b7a4d62fc35e5040a7e425950e887021d7e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085876"
---
# <a name="call-base-class-constructor"></a><span data-ttu-id="a0779-102">呼叫基底類別建構函式</span><span class="sxs-lookup"><span data-stu-id="a0779-102">Call Base Class Constructor</span></span>

<span data-ttu-id="a0779-103">若要從子類別中呼叫基底類別建構函式，請使用關鍵字 **base**：</span><span class="sxs-lookup"><span data-stu-id="a0779-103">To call a base class constructor from a subclass, use the keyword **base**:</span></span>

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

<span data-ttu-id="a0779-104">如果基底類別有預設的 (無參數) 建構函式，您可以省略明確的建構函式呼叫︰</span><span class="sxs-lookup"><span data-stu-id="a0779-104">If a base class has a default (no parameter) constructor, you can omit an explicit constructor call:</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```
