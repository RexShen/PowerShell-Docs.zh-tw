---
title: ValidatePattern 屬性宣告 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidatePattern
- ValidatePattern attribute, described
- ValidatePattern attribute
ms.assetid: 87b811be-6d93-4e7d-b9d0-c567a19bb0ef
caps.latest.revision: 13
ms.openlocfilehash: 5edcb65a6fbe1cb2fe2d0efe3f763fb84628b049
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858874"
---
# <a name="validatepattern-attribute-declaration"></a><span data-ttu-id="07faa-102">ValidatePattern 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="07faa-102">ValidatePattern Attribute Declaration</span></span>

<span data-ttu-id="07faa-103">ValidatePattern 屬性會指定驗證的 cmdlet 參數的引數的規則運算式模式。</span><span class="sxs-lookup"><span data-stu-id="07faa-103">The ValidatePattern attribute specifies a regular expression pattern that validates the argument of a cmdlet parameter.</span></span> <span data-ttu-id="07faa-104">這個屬性也可用 Windows PowerShell 函式。</span><span class="sxs-lookup"><span data-stu-id="07faa-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="07faa-105">ValidatePattern cmdlet 內叫用時，Windows PowerShell 執行階段將 cmdlet 參數的引數轉換為字串，然後比較該 ValidatePattern 屬性提供之模式的字串。</span><span class="sxs-lookup"><span data-stu-id="07faa-105">When ValidatePattern is invoked within a cmdlet, the Windows PowerShell runtime converts the argument of the cmdlet parameter to a string and then compares that string to the pattern supplied by the ValidatePattern attribute.</span></span> <span data-ttu-id="07faa-106">已轉換的字串表示的引數，而提供的模式比對時，才會執行 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="07faa-106">The cmdlet is run only if the converted string representation of the argument and the supplied pattern match.</span></span> <span data-ttu-id="07faa-107">如果不符，Windows PowerShell 執行階段會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="07faa-107">If they do not match, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="07faa-108">語法</span><span class="sxs-lookup"><span data-stu-id="07faa-108">Syntax</span></span>

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="07faa-109">參數</span><span class="sxs-lookup"><span data-stu-id="07faa-109">Parameters</span></span>

<span data-ttu-id="07faa-110">`RegexString` ([System.String](/dotnet/api/System.String)) 所需。</span><span class="sxs-lookup"><span data-stu-id="07faa-110">`RegexString` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="07faa-111">指定驗證參數的引數的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="07faa-111">Specifies a regular expression that validates the parameter argument.</span></span>

<span data-ttu-id="07faa-112">選項 ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) 選擇性具名參數。</span><span class="sxs-lookup"><span data-stu-id="07faa-112">Options ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) Optional named parameter.</span></span> <span data-ttu-id="07faa-113">指定的位元組合[System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)旗標，指定規則運算式選項。</span><span class="sxs-lookup"><span data-stu-id="07faa-113">Specifies a bitwise combination of [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) flags that specify regular expression options.</span></span>

## <a name="remarks"></a><span data-ttu-id="07faa-114">備註</span><span class="sxs-lookup"><span data-stu-id="07faa-114">Remarks</span></span>

- <span data-ttu-id="07faa-115">這個屬性可以用每個參數的一次。</span><span class="sxs-lookup"><span data-stu-id="07faa-115">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="07faa-116">您可以使用`Option`進一步定義模式之屬性的參數。</span><span class="sxs-lookup"><span data-stu-id="07faa-116">You can use the `Option` parameter of the attribute to further define the pattern.</span></span> <span data-ttu-id="07faa-117">例如，您可以進行的模式區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="07faa-117">For example, you can make the pattern case sensitive.</span></span>

- <span data-ttu-id="07faa-118">如果這個屬性會套用至集合，集合中的每個項目必須符合的模式。</span><span class="sxs-lookup"><span data-stu-id="07faa-118">If this attribute is applied to a collection, each element in the collection must match the pattern.</span></span>

- <span data-ttu-id="07faa-119">藉由定義 ValidatePattern 屬性[System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)類別。</span><span class="sxs-lookup"><span data-stu-id="07faa-119">The ValidatePattern attribute is defined by the [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="07faa-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07faa-120">See Also</span></span>

[<span data-ttu-id="07faa-121">System.Management.Automation.Validatepatternattribute</span><span class="sxs-lookup"><span data-stu-id="07faa-121">System.Management.Automation.Validatepatternattribute</span></span>](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[<span data-ttu-id="07faa-122">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="07faa-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
