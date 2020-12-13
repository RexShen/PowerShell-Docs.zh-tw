---
ms.date: 09/13/2016
ms.topic: reference
title: ValidatePattern 屬性宣告
description: ValidatePattern 屬性宣告
ms.openlocfilehash: 364f63d2c52563eaefe64bcbb2bbae511bccb074
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646162"
---
# <a name="validatepattern-attribute-declaration"></a><span data-ttu-id="e349d-103">ValidatePattern 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="e349d-103">ValidatePattern Attribute Declaration</span></span>

<span data-ttu-id="e349d-104">ValidatePattern 屬性會指定正則運算式模式，以驗證 Cmdlet 參數的引數。</span><span class="sxs-lookup"><span data-stu-id="e349d-104">The ValidatePattern attribute specifies a regular expression pattern that validates the argument of a cmdlet parameter.</span></span> <span data-ttu-id="e349d-105">Windows PowerShell 函數也可以使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="e349d-105">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="e349d-106">在 Cmdlet 中叫用 ValidatePattern 時，Windows PowerShell 執行時間會將 Cmdlet 參數的引數轉換成字串，然後將該字串與 ValidatePattern 屬性所提供的模式進行比較。</span><span class="sxs-lookup"><span data-stu-id="e349d-106">When ValidatePattern is invoked within a cmdlet, the Windows PowerShell runtime converts the argument of the cmdlet parameter to a string and then compares that string to the pattern supplied by the ValidatePattern attribute.</span></span> <span data-ttu-id="e349d-107">只有在引數的已轉換字串標記法和提供的模式相符時，才會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e349d-107">The cmdlet is run only if the converted string representation of the argument and the supplied pattern match.</span></span> <span data-ttu-id="e349d-108">如果兩者不相符，Windows PowerShell 執行時間會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="e349d-108">If they do not match, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="e349d-109">語法</span><span class="sxs-lookup"><span data-stu-id="e349d-109">Syntax</span></span>

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="e349d-110">參數</span><span class="sxs-lookup"><span data-stu-id="e349d-110">Parameters</span></span>

<span data-ttu-id="e349d-111">`RegexString` 需要 ([system.string](/dotnet/api/System.String)) 。</span><span class="sxs-lookup"><span data-stu-id="e349d-111">`RegexString` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="e349d-112">指定驗證參數引數的正則運算式。</span><span class="sxs-lookup"><span data-stu-id="e349d-112">Specifies a regular expression that validates the parameter argument.</span></span>

<span data-ttu-id="e349d-113">選項 ([>system.text.regularexpressions. Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) 選擇性的具名引數。</span><span class="sxs-lookup"><span data-stu-id="e349d-113">Options ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) Optional named parameter.</span></span> <span data-ttu-id="e349d-114">指定 [>system.text.regularexpressions. Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) 旗標的位元組合，這些旗標會指定正則運算式選項。</span><span class="sxs-lookup"><span data-stu-id="e349d-114">Specifies a bitwise combination of [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) flags that specify regular expression options.</span></span>

## <a name="remarks"></a><span data-ttu-id="e349d-115">備註</span><span class="sxs-lookup"><span data-stu-id="e349d-115">Remarks</span></span>

- <span data-ttu-id="e349d-116">此屬性每個參數只能使用一次。</span><span class="sxs-lookup"><span data-stu-id="e349d-116">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="e349d-117">您可以使用 `Option` 屬性的參數來進一步定義模式。</span><span class="sxs-lookup"><span data-stu-id="e349d-117">You can use the `Option` parameter of the attribute to further define the pattern.</span></span> <span data-ttu-id="e349d-118">例如，您可以讓模式區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="e349d-118">For example, you can make the pattern case sensitive.</span></span>

- <span data-ttu-id="e349d-119">如果將這個屬性套用至集合，則集合中的每個元素都必須符合模式。</span><span class="sxs-lookup"><span data-stu-id="e349d-119">If this attribute is applied to a collection, each element in the collection must match the pattern.</span></span>

- <span data-ttu-id="e349d-120">ValidatePattern 屬性是由 [Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) 類別所定義。</span><span class="sxs-lookup"><span data-stu-id="e349d-120">The ValidatePattern attribute is defined by the [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="e349d-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e349d-121">See Also</span></span>

[<span data-ttu-id="e349d-122">Validatepatternattribute。</span><span class="sxs-lookup"><span data-stu-id="e349d-122">System.Management.Automation.Validatepatternattribute</span></span>](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[<span data-ttu-id="e349d-123">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e349d-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
