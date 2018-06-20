---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: 188ede0c558210a746ad0f6c6cef6f571b280878
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219900"
---
# <a name="declare-base-class"></a><span data-ttu-id="933db-102">宣告基底類別</span><span class="sxs-lookup"><span data-stu-id="933db-102">Declare Base Class</span></span>
<span data-ttu-id="933db-103">您可以將 Windows PowerShell 類別宣告為另一個 Windows PowerShell 類別的基底類型。</span><span class="sxs-lookup"><span data-stu-id="933db-103">You can declare a Windows PowerShell class as a base type for another Windows PowerShell class.</span></span>

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

<span data-ttu-id="933db-104">現有的 .NET Framework 類型也可以用作為基底類別︰</span><span class="sxs-lookup"><span data-stu-id="933db-104">You can also use existing .NET Framework types as base classes:</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```
