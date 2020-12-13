---
ms.date: 09/13/2016
ms.topic: reference
title: ValidateSet 屬性宣告
description: ValidateSet 屬性宣告
ms.openlocfilehash: 7894d00561366ada492911e8147acbd8d3454a55
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660475"
---
# <a name="validateset-attribute-declaration"></a><span data-ttu-id="bfe3e-103">ValidateSet 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="bfe3e-103">ValidateSet Attribute Declaration</span></span>

<span data-ttu-id="bfe3e-104">ValidateSetAttribute 屬性會指定 Cmdlet 參數引數的一組可能值。</span><span class="sxs-lookup"><span data-stu-id="bfe3e-104">The ValidateSetAttribute attribute specifies a set of possible values for a cmdlet parameter argument.</span></span> <span data-ttu-id="bfe3e-105">Windows PowerShell 函數也可以使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="bfe3e-105">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="bfe3e-106">當指定這個屬性時，Windows PowerShell 執行時間會判斷提供的 Cmdlet 參數所提供的引數是否符合提供之元素集內的專案。</span><span class="sxs-lookup"><span data-stu-id="bfe3e-106">When this attribute is specified, the Windows PowerShell runtime determines whether the supplied argument for the cmdlet parameter matches an element in the supplied element set.</span></span> <span data-ttu-id="bfe3e-107">只有當參數引數符合集合中的元素時，才會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bfe3e-107">The cmdlet is run only if the parameter argument matches an element in the set.</span></span> <span data-ttu-id="bfe3e-108">如果找不到相符項，Windows PowerShell 執行時間會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="bfe3e-108">If no match is found, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="bfe3e-109">語法</span><span class="sxs-lookup"><span data-stu-id="bfe3e-109">Syntax</span></span>

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="bfe3e-110">參數</span><span class="sxs-lookup"><span data-stu-id="bfe3e-110">Parameters</span></span>

<span data-ttu-id="bfe3e-111">`ValidValues` 需要 ([system.string](/dotnet/api/System.String)) 。</span><span class="sxs-lookup"><span data-stu-id="bfe3e-111">`ValidValues` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="bfe3e-112">指定有效的參數元素值。</span><span class="sxs-lookup"><span data-stu-id="bfe3e-112">Specifies the valid parameter element values.</span></span> <span data-ttu-id="bfe3e-113">下列範例示範如何指定一個專案或多個元素。</span><span class="sxs-lookup"><span data-stu-id="bfe3e-113">The following sample shows how to specify one element or multiple elements.</span></span>

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

<span data-ttu-id="bfe3e-114">`IgnoreCase` ([system.string) 選擇性的命名](/dotnet/api/System.Boolean) 參數。</span><span class="sxs-lookup"><span data-stu-id="bfe3e-114">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="bfe3e-115">的預設值 `true` 表示忽略大小寫。</span><span class="sxs-lookup"><span data-stu-id="bfe3e-115">The default value of `true` indicates that case is ignored.</span></span> <span data-ttu-id="bfe3e-116">的值 `false` 可讓 Cmdlet 區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="bfe3e-116">A value of `false` makes the cmdlet case-sensitive.</span></span>

## <a name="remarks"></a><span data-ttu-id="bfe3e-117">備註</span><span class="sxs-lookup"><span data-stu-id="bfe3e-117">Remarks</span></span>

- <span data-ttu-id="bfe3e-118">此屬性每個參數只能使用一次。</span><span class="sxs-lookup"><span data-stu-id="bfe3e-118">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="bfe3e-119">如果參數值是陣列，則陣列的每個元素都必須符合屬性集的元素。</span><span class="sxs-lookup"><span data-stu-id="bfe3e-119">If the parameter value is an array, every element of the array must match an element of the attribute set.</span></span>

- <span data-ttu-id="bfe3e-120">ValidateSetAttribute 屬性是由 [ValidateSetAttribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) 類別所定義。</span><span class="sxs-lookup"><span data-stu-id="bfe3e-120">The ValidateSetAttribute attribute is defined by the [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="bfe3e-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bfe3e-121">See Also</span></span>

[<span data-ttu-id="bfe3e-122">Validatesetattribute。</span><span class="sxs-lookup"><span data-stu-id="bfe3e-122">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="bfe3e-123">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="bfe3e-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
