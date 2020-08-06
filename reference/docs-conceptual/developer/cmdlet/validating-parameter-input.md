---
title: 驗證參數輸入 |Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- parameters, validation rules
- validation, examples
- validation
ms.openlocfilehash: e12c715cfa24edfff958b12be1f3517b2f545256
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783988"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="5dddd-102">驗證參數輸入</span><span class="sxs-lookup"><span data-stu-id="5dddd-102">Validating Parameter Input</span></span>

<span data-ttu-id="5dddd-103">PowerShell 可以用數種方式驗證傳遞給 Cmdlet 參數的引數。</span><span class="sxs-lookup"><span data-stu-id="5dddd-103">PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span>
<span data-ttu-id="5dddd-104">PowerShell 可以驗證長度、範圍，以及引數字元的模式。</span><span class="sxs-lookup"><span data-stu-id="5dddd-104">PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span>
<span data-ttu-id="5dddd-105">它可以驗證 (計數) 可用的引數數目。</span><span class="sxs-lookup"><span data-stu-id="5dddd-105">It can validate the number of arguments available (the count).</span></span>
<span data-ttu-id="5dddd-106">這些驗證規則是由使用 Cmdlet 類別的公用屬性上的參數屬性所宣告的驗證屬性所定義。</span><span class="sxs-lookup"><span data-stu-id="5dddd-106">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="5dddd-107">若要驗證參數引數，PowerShell 執行時間會使用驗證屬性所提供的資訊，在執行 Cmdlet 之前確認參數的值。</span><span class="sxs-lookup"><span data-stu-id="5dddd-107">To validate a parameter argument, the PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span>
<span data-ttu-id="5dddd-108">如果參數輸入無效，使用者會收到錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="5dddd-108">If the parameter input is not valid, the user receives an error message.</span></span>
<span data-ttu-id="5dddd-109">每個驗證參數都會定義 PowerShell 強制執行的驗證規則。</span><span class="sxs-lookup"><span data-stu-id="5dddd-109">Each validation parameter defines a validation rule that is enforced by PowerShell.</span></span>

<span data-ttu-id="5dddd-110">PowerShell 會根據下列屬性來強制執行驗證規則。</span><span class="sxs-lookup"><span data-stu-id="5dddd-110">PowerShell enforces the validation rules based on the following attributes.</span></span>

### <a name="validatecount"></a><span data-ttu-id="5dddd-111">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="5dddd-111">ValidateCount</span></span>

<span data-ttu-id="5dddd-112">指定參數可以接受之引數的最小和最大數目。</span><span class="sxs-lookup"><span data-stu-id="5dddd-112">Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span>
<span data-ttu-id="5dddd-113">如需詳細資訊，請參閱[ValidateCount 屬性](./validatecount-attribute-declaration.md)宣告。</span><span class="sxs-lookup"><span data-stu-id="5dddd-113">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="5dddd-114">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="5dddd-114">ValidateLength</span></span>

<span data-ttu-id="5dddd-115">指定參數引數中的最小和最大字元數。</span><span class="sxs-lookup"><span data-stu-id="5dddd-115">Specifies the minimum and maximum number of characters in the parameter argument.</span></span>
<span data-ttu-id="5dddd-116">如需詳細資訊，請參閱[ValidateLength 屬性](./validatelength-attribute-declaration.md)宣告。</span><span class="sxs-lookup"><span data-stu-id="5dddd-116">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="5dddd-117">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="5dddd-117">ValidatePattern</span></span>

<span data-ttu-id="5dddd-118">指定驗證參數引數的正則運算式。</span><span class="sxs-lookup"><span data-stu-id="5dddd-118">Specifies a regular expression that validates the parameter argument.</span></span>
<span data-ttu-id="5dddd-119">如需詳細資訊，請參閱[ValidatePattern 屬性](./validatepattern-attribute-declaration.md)宣告。</span><span class="sxs-lookup"><span data-stu-id="5dddd-119">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="5dddd-120">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="5dddd-120">ValidateRange</span></span>

<span data-ttu-id="5dddd-121">指定參數引數的最小和最大值。</span><span class="sxs-lookup"><span data-stu-id="5dddd-121">Specifies the minimum and maximum values of the parameter argument.</span></span>
<span data-ttu-id="5dddd-122">如需詳細資訊，請參閱[ValidateRange 屬性](./validaterange-attribute-declaration.md)宣告。</span><span class="sxs-lookup"><span data-stu-id="5dddd-122">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="5dddd-123">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="5dddd-123">ValidateSet</span></span>

<span data-ttu-id="5dddd-124">指定參數引數的有效值。</span><span class="sxs-lookup"><span data-stu-id="5dddd-124">Specifies the valid values for the parameter argument.</span></span>
<span data-ttu-id="5dddd-125">如需詳細資訊，請參閱[ValidateSet 屬性](./validateset-attribute-declaration.md)宣告。</span><span class="sxs-lookup"><span data-stu-id="5dddd-125">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5dddd-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5dddd-126">See Also</span></span>

[<span data-ttu-id="5dddd-127">如何驗證參數輸入</span><span class="sxs-lookup"><span data-stu-id="5dddd-127">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

[<span data-ttu-id="5dddd-128">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5dddd-128">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
