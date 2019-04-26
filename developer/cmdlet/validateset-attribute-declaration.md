---
title: ValidateSet 屬性宣告 |Microsoft Docs
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067056"
---
# <a name="validateset-attribute-declaration"></a><span data-ttu-id="a3b04-102">ValidateSet 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="a3b04-102">ValidateSet Attribute Declaration</span></span>

<span data-ttu-id="a3b04-103">ValidateSetAttribute 屬性會指定一組 cmdlet 參數引數的可能值。</span><span class="sxs-lookup"><span data-stu-id="a3b04-103">The ValidateSetAttribute attribute specifies a set of possible values for a cmdlet parameter argument.</span></span> <span data-ttu-id="a3b04-104">這個屬性也可用 Windows PowerShell 函式。</span><span class="sxs-lookup"><span data-stu-id="a3b04-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="a3b04-105">當指定這個屬性時，Windows PowerShell 執行階段會判斷提供的引數，cmdlet 參數是否符合提供項目集合中的項目。</span><span class="sxs-lookup"><span data-stu-id="a3b04-105">When this attribute is specified, the Windows PowerShell runtime determines whether the supplied argument for the cmdlet parameter matches an element in the supplied element set.</span></span> <span data-ttu-id="a3b04-106">只有當參數引數符合集合中的項目，是執行 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a3b04-106">The cmdlet is run only if the parameter argument matches an element in the set.</span></span> <span data-ttu-id="a3b04-107">如果找到相符項目，則 Windows PowerShell 執行階段會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="a3b04-107">If no match is found, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="a3b04-108">語法</span><span class="sxs-lookup"><span data-stu-id="a3b04-108">Syntax</span></span>

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="a3b04-109">參數</span><span class="sxs-lookup"><span data-stu-id="a3b04-109">Parameters</span></span>

<span data-ttu-id="a3b04-110">`ValidValues` ([System.String](/dotnet/api/System.String)) 所需。</span><span class="sxs-lookup"><span data-stu-id="a3b04-110">`ValidValues` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="a3b04-111">指定有效的參數項目值。</span><span class="sxs-lookup"><span data-stu-id="a3b04-111">Specifies the valid parameter element values.</span></span> <span data-ttu-id="a3b04-112">下列範例示範如何指定一個項目或多個項目。</span><span class="sxs-lookup"><span data-stu-id="a3b04-112">The following sample shows how to specify one element or multiple elements.</span></span>

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

<span data-ttu-id="a3b04-113">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) 選擇性具名參數。</span><span class="sxs-lookup"><span data-stu-id="a3b04-113">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="a3b04-114">預設值`true`指出，忽略大小寫。</span><span class="sxs-lookup"><span data-stu-id="a3b04-114">The default value of `true` indicates that case is ignored.</span></span> <span data-ttu-id="a3b04-115">值為`false`會區分大小寫的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a3b04-115">A value of `false` makes the cmdlet case-sensitive.</span></span>

## <a name="remarks"></a><span data-ttu-id="a3b04-116">備註</span><span class="sxs-lookup"><span data-stu-id="a3b04-116">Remarks</span></span>

- <span data-ttu-id="a3b04-117">這個屬性可以用每個參數的一次。</span><span class="sxs-lookup"><span data-stu-id="a3b04-117">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="a3b04-118">如果參數值是陣列，陣列的每個項目必須符合屬性集合的項目。</span><span class="sxs-lookup"><span data-stu-id="a3b04-118">If the parameter value is an array, every element of the array must match an element of the attribute set.</span></span>

- <span data-ttu-id="a3b04-119">ValidateSetAttribute 屬性所定義[System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)類別。</span><span class="sxs-lookup"><span data-stu-id="a3b04-119">The ValidateSetAttribute attribute is defined by the [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="a3b04-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3b04-120">See Also</span></span>

[<span data-ttu-id="a3b04-121">System.Management.Automation.Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="a3b04-121">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="a3b04-122">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a3b04-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
