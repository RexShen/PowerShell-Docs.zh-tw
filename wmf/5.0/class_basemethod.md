---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,設定"
ms.openlocfilehash: 7817769c3fc060a51c833b7469f7b556b9b40e87
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2017
---
# <a name="call-base-class-method"></a><span data-ttu-id="21f8d-102">呼叫基底類別方法</span><span class="sxs-lookup"><span data-stu-id="21f8d-102">Call Base Class Method</span></span>

<span data-ttu-id="21f8d-103">您可以覆寫子類別中現有的方法。</span><span class="sxs-lookup"><span data-stu-id="21f8d-103">You can override existing methods in subclasses.</span></span> <span data-ttu-id="21f8d-104">若要這樣做，請使用相同的名稱和簽章宣告方法︰</span><span class="sxs-lookup"><span data-stu-id="21f8d-104">To do this, declare methods by using the same name and signature:</span></span>

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

<span data-ttu-id="21f8d-105">若要從覆寫的實作呼叫基底類別方法，請在引動過程上轉換為基底類別 ([baseClass]$this)︰</span><span class="sxs-lookup"><span data-stu-id="21f8d-105">To call base class methods from overridden implementations, cast to the base class ([baseClass]$this) on invocation:</span></span>

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

<span data-ttu-id="21f8d-106">所有的 PowerShell 方法都是虛擬的。</span><span class="sxs-lookup"><span data-stu-id="21f8d-106">All PowerShell methods are virtual.</span></span> <span data-ttu-id="21f8d-107">您可以使用與覆寫作業相同的語法，將非虛擬的 .NET 方法隱藏在子類別中︰只宣告名稱和簽章相同的方法。</span><span class="sxs-lookup"><span data-stu-id="21f8d-107">You can hide non-virtual .NET methods in a subclass by using the same syntax as you do for an override: just declare methods with same name and signature.</span></span>

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

