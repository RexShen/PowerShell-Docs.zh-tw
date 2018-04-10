---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,設定
ms.openlocfilehash: 43b26426a76b6503a83e35ae0c02a0af69902ed6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="declare-base-class"></a><span data-ttu-id="26ac1-102">宣告基底類別</span><span class="sxs-lookup"><span data-stu-id="26ac1-102">Declare Base Class</span></span>
<span data-ttu-id="26ac1-103">您可以將 Windows PowerShell 類別宣告為另一個 Windows PowerShell 類別的基底類型。</span><span class="sxs-lookup"><span data-stu-id="26ac1-103">You can declare a Windows PowerShell class as a base type for another Windows PowerShell class.</span></span>

```powershell
class bar
{
   [int]foo()
       {
           return 100500
       }
}

class baz : bar {}

[baz]::new().foo() # return 100500
```

<span data-ttu-id="26ac1-104">現有的 .NET Framework 類型也可以用作為基底類別︰</span><span class="sxs-lookup"><span data-stu-id="26ac1-104">You can also use existing .NET Framework types as base classes:</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```