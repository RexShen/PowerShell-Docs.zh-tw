---
title: ValidateSet 屬性聲明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateSet
- ValidateSet attribute, described
- ValidateSet attribute
ms.assetid: 4a6f97ab-45b2-4f3d-84d4-30acf8e074d0
caps.latest.revision: 12
ms.openlocfilehash: b036f39cd01ffe4b4ce7db9627cb6da0d5327190
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364277"
---
# <a name="validateset-attribute-declaration"></a><span data-ttu-id="05d99-102">ValidateSet 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="05d99-102">ValidateSet Attribute Declaration</span></span>

<span data-ttu-id="05d99-103">ValidateSetAttribute 屬性會指定 Cmdlet 參數引數的一組可能值。</span><span class="sxs-lookup"><span data-stu-id="05d99-103">The ValidateSetAttribute attribute specifies a set of possible values for a cmdlet parameter argument.</span></span> <span data-ttu-id="05d99-104">Windows PowerShell 函數也可以使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="05d99-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="05d99-105">當指定這個屬性時，Windows PowerShell 執行時間會判斷 Cmdlet 參數所提供的引數是否符合所提供元素集中的元素。</span><span class="sxs-lookup"><span data-stu-id="05d99-105">When this attribute is specified, the Windows PowerShell runtime determines whether the supplied argument for the cmdlet parameter matches an element in the supplied element set.</span></span> <span data-ttu-id="05d99-106">只有當參數引數符合集合中的元素時，才會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="05d99-106">The cmdlet is run only if the parameter argument matches an element in the set.</span></span> <span data-ttu-id="05d99-107">如果找不到相符的結果，Windows PowerShell 執行時間會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="05d99-107">If no match is found, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="05d99-108">語法</span><span class="sxs-lookup"><span data-stu-id="05d99-108">Syntax</span></span>

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="05d99-109">參數</span><span class="sxs-lookup"><span data-stu-id="05d99-109">Parameters</span></span>

<span data-ttu-id="05d99-110">需要 `ValidValues` （[system.string](/dotnet/api/System.String)）。</span><span class="sxs-lookup"><span data-stu-id="05d99-110">`ValidValues` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="05d99-111">指定有效的參數元素值。</span><span class="sxs-lookup"><span data-stu-id="05d99-111">Specifies the valid parameter element values.</span></span> <span data-ttu-id="05d99-112">下列範例示範如何指定一個或多個元素。</span><span class="sxs-lookup"><span data-stu-id="05d99-112">The following sample shows how to specify one element or multiple elements.</span></span>

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

<span data-ttu-id="05d99-113">`IgnoreCase` （[布林值](/dotnet/api/System.Boolean)）選擇性的具名引數。</span><span class="sxs-lookup"><span data-stu-id="05d99-113">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="05d99-114">`true` 的預設值表示會忽略大小寫。</span><span class="sxs-lookup"><span data-stu-id="05d99-114">The default value of `true` indicates that case is ignored.</span></span> <span data-ttu-id="05d99-115">值 `false` 會使 Cmdlet 區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="05d99-115">A value of `false` makes the cmdlet case-sensitive.</span></span>

## <a name="remarks"></a><span data-ttu-id="05d99-116">備註</span><span class="sxs-lookup"><span data-stu-id="05d99-116">Remarks</span></span>

- <span data-ttu-id="05d99-117">每個參數只能使用此屬性一次。</span><span class="sxs-lookup"><span data-stu-id="05d99-117">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="05d99-118">如果參數值為數組，則陣列的每個元素都必須符合屬性集的專案。</span><span class="sxs-lookup"><span data-stu-id="05d99-118">If the parameter value is an array, every element of the array must match an element of the attribute set.</span></span>

- <span data-ttu-id="05d99-119">ValidateSetAttribute 屬性是由[ValidateSetAttribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)類別所定義。</span><span class="sxs-lookup"><span data-stu-id="05d99-119">The ValidateSetAttribute attribute is defined by the [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="05d99-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05d99-120">See Also</span></span>

[<span data-ttu-id="05d99-121">Validatesetattribute。</span><span class="sxs-lookup"><span data-stu-id="05d99-121">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="05d99-122">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="05d99-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
