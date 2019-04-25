---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: 8b3ebd22e03bf9bdd5f26965137a1b1ce9f47c3e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058772"
---
# <a name="declare-base-class"></a><span data-ttu-id="636ac-102">宣告基底類別</span><span class="sxs-lookup"><span data-stu-id="636ac-102">Declare Base Class</span></span>
<span data-ttu-id="636ac-103">您可以將 Windows PowerShell 類別宣告為另一個 Windows PowerShell 類別的基底類型。</span><span class="sxs-lookup"><span data-stu-id="636ac-103">You can declare a Windows PowerShell class as a base type for another Windows PowerShell class.</span></span>

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

<span data-ttu-id="636ac-104">現有的 .NET Framework 類型也可以用作為基底類別︰</span><span class="sxs-lookup"><span data-stu-id="636ac-104">You can also use existing .NET Framework types as base classes:</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```
