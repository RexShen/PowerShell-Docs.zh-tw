---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: 0e79127faf3f9bf6fe7d525db5bb946daf3b93e1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058619"
---
# <a name="call-base-class-method"></a>呼叫基底類別方法

您可以覆寫子類別中現有的方法。 若要這樣做，請使用相同的名稱和簽章宣告方法︰

```powershell
class baseClass
{
    [int]foo() {return 100500}
}

class childClass1 : baseClass
{
    [int]foo() {return 200600}
}

[childClass1]::new().foo() # return 200600
```

若要從覆寫的實作呼叫基底類別方法，請在引動過程上轉換為基底類別 ([baseClass]$this)︰

```powershell
class childClass2 : baseClass
{
    [int]foo()
    {
        return 3 * ([baseClass]$this).foo()
    }
}

[childClass2]::new().foo() # return 301500
```

所有的 PowerShell 方法都是虛擬的。 您可以使用與覆寫作業相同的語法，將非虛擬的 .NET 方法隱藏在子類別中︰只宣告名稱和簽章相同的方法。

```powershell
class MyIntList : system.collections.generic.list[int]
{
    # Add is final in system.collections.generic.list
    [void] Add([int]$arg)
    {
        ([system.collections.generic.list[int]]$this).Add($arg * 2)
    }
}

$list = [MyIntList]::new()
$list.Add(100)
$list[0] # return 200
```
