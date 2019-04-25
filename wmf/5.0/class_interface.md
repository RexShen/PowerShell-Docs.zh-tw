---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: 4b593e9a1eca43ee7ad85fc921ae3c1d62722db9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085848"
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="c4a5e-102">宣告實作的介面</span><span class="sxs-lookup"><span data-stu-id="c4a5e-102">Declare Implemented Interface</span></span>

<span data-ttu-id="c4a5e-103">如未指定基底類型，您可以在基底類型之後或緊跟在冒號 (:) 之後宣告實作的介面。</span><span class="sxs-lookup"><span data-stu-id="c4a5e-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="c4a5e-104">使用逗號分隔所有類型名稱。</span><span class="sxs-lookup"><span data-stu-id="c4a5e-104">Separate all type names by using commas.</span></span> <span data-ttu-id="c4a5e-105">非常類似 C# 語法。</span><span class="sxs-lookup"><span data-stu-id="c4a5e-105">It’s very similar to C# syntax.</span></span>

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
