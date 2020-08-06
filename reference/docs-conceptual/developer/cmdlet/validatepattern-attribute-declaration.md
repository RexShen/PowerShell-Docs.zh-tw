---
title: ValidatePattern 屬性聲明 |Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- attributes, ValidatePattern
- ValidatePattern attribute, described
- ValidatePattern attribute
ms.openlocfilehash: 713fa7a46a8eeefdbfd679a5e8436285fac085f8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787796"
---
# <a name="validatepattern-attribute-declaration"></a><span data-ttu-id="d368e-102">ValidatePattern 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="d368e-102">ValidatePattern Attribute Declaration</span></span>

<span data-ttu-id="d368e-103">ValidatePattern 屬性會指定正則運算式模式，以驗證 Cmdlet 參數的引數。</span><span class="sxs-lookup"><span data-stu-id="d368e-103">The ValidatePattern attribute specifies a regular expression pattern that validates the argument of a cmdlet parameter.</span></span> <span data-ttu-id="d368e-104">Windows PowerShell 函數也可以使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="d368e-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="d368e-105">在 Cmdlet 內叫用 ValidatePattern 時，Windows PowerShell 執行時間會將 Cmdlet 參數的引數轉換成字串，然後將該字串與 ValidatePattern 屬性所提供的模式進行比較。</span><span class="sxs-lookup"><span data-stu-id="d368e-105">When ValidatePattern is invoked within a cmdlet, the Windows PowerShell runtime converts the argument of the cmdlet parameter to a string and then compares that string to the pattern supplied by the ValidatePattern attribute.</span></span> <span data-ttu-id="d368e-106">只有當引數的轉換字串表示和提供的模式相符時，才會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d368e-106">The cmdlet is run only if the converted string representation of the argument and the supplied pattern match.</span></span> <span data-ttu-id="d368e-107">如果不相符，Windows PowerShell 執行時間會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="d368e-107">If they do not match, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="d368e-108">語法</span><span class="sxs-lookup"><span data-stu-id="d368e-108">Syntax</span></span>

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="d368e-109">參數</span><span class="sxs-lookup"><span data-stu-id="d368e-109">Parameters</span></span>

<span data-ttu-id="d368e-110">`RegexString`需要 ([system.string](/dotnet/api/System.String)) 。</span><span class="sxs-lookup"><span data-stu-id="d368e-110">`RegexString` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="d368e-111">指定驗證參數引數的正則運算式。</span><span class="sxs-lookup"><span data-stu-id="d368e-111">Specifies a regular expression that validates the parameter argument.</span></span>

<span data-ttu-id="d368e-112">Options ([system.text.regularexpressions.RegEx>. system.text.regularexpressions.RegExoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) 選擇性的具名引數。</span><span class="sxs-lookup"><span data-stu-id="d368e-112">Options ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) Optional named parameter.</span></span> <span data-ttu-id="d368e-113">指定指定正則運算式選項的[System.text.regularexpressions.RegEx> system.text.regularexpressions.RegExoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)旗標的位元組合。</span><span class="sxs-lookup"><span data-stu-id="d368e-113">Specifies a bitwise combination of [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) flags that specify regular expression options.</span></span>

## <a name="remarks"></a><span data-ttu-id="d368e-114">備註</span><span class="sxs-lookup"><span data-stu-id="d368e-114">Remarks</span></span>

- <span data-ttu-id="d368e-115">每個參數只能使用此屬性一次。</span><span class="sxs-lookup"><span data-stu-id="d368e-115">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="d368e-116">您可以使用 `Option` 屬性的參數來進一步定義模式。</span><span class="sxs-lookup"><span data-stu-id="d368e-116">You can use the `Option` parameter of the attribute to further define the pattern.</span></span> <span data-ttu-id="d368e-117">例如，您可以讓模式區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="d368e-117">For example, you can make the pattern case sensitive.</span></span>

- <span data-ttu-id="d368e-118">如果將這個屬性套用至集合，則集合中的每個元素都必須符合模式。</span><span class="sxs-lookup"><span data-stu-id="d368e-118">If this attribute is applied to a collection, each element in the collection must match the pattern.</span></span>

- <span data-ttu-id="d368e-119">ValidatePattern 屬性是由[Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)類別所定義。</span><span class="sxs-lookup"><span data-stu-id="d368e-119">The ValidatePattern attribute is defined by the [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="d368e-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d368e-120">See Also</span></span>

[<span data-ttu-id="d368e-121">Validatepatternattribute。</span><span class="sxs-lookup"><span data-stu-id="d368e-121">System.Management.Automation.Validatepatternattribute</span></span>](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[<span data-ttu-id="d368e-122">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d368e-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
