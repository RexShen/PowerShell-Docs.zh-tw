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
# <a name="declare-base-class"></a>宣告基底類別
您可以將 Windows PowerShell 類別宣告為另一個 Windows PowerShell 類別的基底類型。

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

現有的 .NET Framework 類型也可以用作為基底類別︰

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```
