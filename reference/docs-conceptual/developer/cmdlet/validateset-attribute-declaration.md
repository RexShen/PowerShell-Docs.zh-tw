---
title: ValidateSet 屬性聲明 |Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- attributes, ValidateSet
- ValidateSet attribute, described
- ValidateSet attribute
ms.openlocfilehash: 0b6833efb0ce8e9474e9d91049fd201fc845cbea
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787762"
---
# <a name="validateset-attribute-declaration"></a><span data-ttu-id="b6a77-102">ValidateSet 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="b6a77-102">ValidateSet Attribute Declaration</span></span>

<span data-ttu-id="b6a77-103">ValidateSetAttribute 屬性會指定 Cmdlet 參數引數的一組可能值。</span><span class="sxs-lookup"><span data-stu-id="b6a77-103">The ValidateSetAttribute attribute specifies a set of possible values for a cmdlet parameter argument.</span></span> <span data-ttu-id="b6a77-104">Windows PowerShell 函數也可以使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="b6a77-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="b6a77-105">當指定這個屬性時，Windows PowerShell 執行時間會判斷 Cmdlet 參數所提供的引數是否符合所提供元素集中的元素。</span><span class="sxs-lookup"><span data-stu-id="b6a77-105">When this attribute is specified, the Windows PowerShell runtime determines whether the supplied argument for the cmdlet parameter matches an element in the supplied element set.</span></span> <span data-ttu-id="b6a77-106">只有當參數引數符合集合中的元素時，才會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b6a77-106">The cmdlet is run only if the parameter argument matches an element in the set.</span></span> <span data-ttu-id="b6a77-107">如果找不到相符的結果，Windows PowerShell 執行時間會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="b6a77-107">If no match is found, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="b6a77-108">語法</span><span class="sxs-lookup"><span data-stu-id="b6a77-108">Syntax</span></span>

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="b6a77-109">參數</span><span class="sxs-lookup"><span data-stu-id="b6a77-109">Parameters</span></span>

<span data-ttu-id="b6a77-110">`ValidValues`需要 ([system.string](/dotnet/api/System.String)) 。</span><span class="sxs-lookup"><span data-stu-id="b6a77-110">`ValidValues` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="b6a77-111">指定有效的參數元素值。</span><span class="sxs-lookup"><span data-stu-id="b6a77-111">Specifies the valid parameter element values.</span></span> <span data-ttu-id="b6a77-112">下列範例示範如何指定一個或多個元素。</span><span class="sxs-lookup"><span data-stu-id="b6a77-112">The following sample shows how to specify one element or multiple elements.</span></span>

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

<span data-ttu-id="b6a77-113">`IgnoreCase` ([的布林值](/dotnet/api/System.Boolean)) 選擇性的具名引數。</span><span class="sxs-lookup"><span data-stu-id="b6a77-113">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="b6a77-114">的預設值 `true` 表示忽略大小寫。</span><span class="sxs-lookup"><span data-stu-id="b6a77-114">The default value of `true` indicates that case is ignored.</span></span> <span data-ttu-id="b6a77-115">的值 `false` 會讓 Cmdlet 區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="b6a77-115">A value of `false` makes the cmdlet case-sensitive.</span></span>

## <a name="remarks"></a><span data-ttu-id="b6a77-116">備註</span><span class="sxs-lookup"><span data-stu-id="b6a77-116">Remarks</span></span>

- <span data-ttu-id="b6a77-117">每個參數只能使用此屬性一次。</span><span class="sxs-lookup"><span data-stu-id="b6a77-117">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="b6a77-118">如果參數值為數組，則陣列的每個元素都必須符合屬性集的專案。</span><span class="sxs-lookup"><span data-stu-id="b6a77-118">If the parameter value is an array, every element of the array must match an element of the attribute set.</span></span>

- <span data-ttu-id="b6a77-119">ValidateSetAttribute 屬性是由[ValidateSetAttribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)類別所定義。</span><span class="sxs-lookup"><span data-stu-id="b6a77-119">The ValidateSetAttribute attribute is defined by the [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="b6a77-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6a77-120">See Also</span></span>

[<span data-ttu-id="b6a77-121">Validatesetattribute。</span><span class="sxs-lookup"><span data-stu-id="b6a77-121">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="b6a77-122">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b6a77-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
