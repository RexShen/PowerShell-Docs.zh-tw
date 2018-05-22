---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: 116f79a95126d0a1c579a95ec99eb5d8b75cc1e0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="3c428-102">宣告實作的介面</span><span class="sxs-lookup"><span data-stu-id="3c428-102">Declare Implemented Interface</span></span>

<span data-ttu-id="3c428-103">如未指定基底類型，您可以在基底類型之後或緊跟在冒號 (:) 之後宣告實作的介面。</span><span class="sxs-lookup"><span data-stu-id="3c428-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="3c428-104">使用逗號分隔所有類型名稱。</span><span class="sxs-lookup"><span data-stu-id="3c428-104">Separate all type names by using commas.</span></span> <span data-ttu-id="3c428-105">非常類似 C# 語法。</span><span class="sxs-lookup"><span data-stu-id="3c428-105">It’s very similar to C# syntax.</span></span>

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
