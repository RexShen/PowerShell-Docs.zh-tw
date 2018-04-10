---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,設定
ms.openlocfilehash: 3269c8cc871f22488b64fb072dac72698983f360
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="call-base-class-constructor"></a><span data-ttu-id="686fb-102">呼叫基底類別建構函式</span><span class="sxs-lookup"><span data-stu-id="686fb-102">Call Base Class Constructor</span></span>

<span data-ttu-id="686fb-103">若要從子類別中呼叫基底類別建構函式，請使用關鍵字 **base**：</span><span class="sxs-lookup"><span data-stu-id="686fb-103">To call a base class constructor from a subclass, use the keyword **base**:</span></span>

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

<span data-ttu-id="686fb-104">如果基底類別有預設的 (無參數) 建構函式，您可以省略明確的建構函式呼叫︰</span><span class="sxs-lookup"><span data-stu-id="686fb-104">If a base class has a default (no parameter) constructor, you can omit an explicit constructor call:</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```