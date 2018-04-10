---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,設定
ms.openlocfilehash: 2c007321789ae22b4a2e048d2d64162b065f9a75
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="d6b69-102">宣告實作的介面</span><span class="sxs-lookup"><span data-stu-id="d6b69-102">Declare Implemented Interface</span></span>

<span data-ttu-id="d6b69-103">如未指定基底類型，您可以在基底類型之後或緊跟在冒號 (:) 之後宣告實作的介面。</span><span class="sxs-lookup"><span data-stu-id="d6b69-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="d6b69-104">使用逗號分隔所有類型名稱。</span><span class="sxs-lookup"><span data-stu-id="d6b69-104">Separate all type names by using commas.</span></span> <span data-ttu-id="d6b69-105">非常類似 C# 語法。</span><span class="sxs-lookup"><span data-stu-id="d6b69-105">It’s very similar to C# syntax.</span></span>

```powershell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```