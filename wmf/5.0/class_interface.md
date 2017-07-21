---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,設定"
ms.openlocfilehash: e503f9a4462e94fce42ffcdcc0976d261c051f87
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="179f7-102">宣告實作的介面</span><span class="sxs-lookup"><span data-stu-id="179f7-102">Declare Implemented Interface</span></span>

<span data-ttu-id="179f7-103">如未指定基底類型，您可以在基底類型之後或緊跟在冒號 (:) 之後宣告實作的介面。</span><span class="sxs-lookup"><span data-stu-id="179f7-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="179f7-104">使用逗號分隔所有類型名稱。</span><span class="sxs-lookup"><span data-stu-id="179f7-104">Separate all type names by using commas.</span></span> <span data-ttu-id="179f7-105">非常類似 C# 語法。</span><span class="sxs-lookup"><span data-stu-id="179f7-105">It’s very similar to C# syntax.</span></span>

```PowerShell
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

