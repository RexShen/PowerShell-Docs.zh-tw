---
ms.date: 09/13/2016
ms.topic: reference
title: 驗證參數輸入
description: 驗證參數輸入
ms.openlocfilehash: a97b5c670e8c36463a85bbef1506f6311bdd5ec3
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660406"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="a8866-103">驗證參數輸入</span><span class="sxs-lookup"><span data-stu-id="a8866-103">Validating Parameter Input</span></span>

<span data-ttu-id="a8866-104">PowerShell 可以用數種方式驗證傳遞給 Cmdlet 參數的引數。</span><span class="sxs-lookup"><span data-stu-id="a8866-104">PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span>
<span data-ttu-id="a8866-105">PowerShell 可以驗證引數字元的長度、範圍和字元模式。</span><span class="sxs-lookup"><span data-stu-id="a8866-105">PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span>
<span data-ttu-id="a8866-106">它可以驗證 (計數) 可用的引數數目。</span><span class="sxs-lookup"><span data-stu-id="a8866-106">It can validate the number of arguments available (the count).</span></span>
<span data-ttu-id="a8866-107">這些驗證規則是由以 Cmdlet 類別之公用屬性上的參數屬性宣告的驗證屬性所定義。</span><span class="sxs-lookup"><span data-stu-id="a8866-107">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="a8866-108">為了驗證參數引數，PowerShell 執行時間會使用驗證屬性所提供的資訊，在執行 Cmdlet 之前確認參數的值。</span><span class="sxs-lookup"><span data-stu-id="a8866-108">To validate a parameter argument, the PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span>
<span data-ttu-id="a8866-109">如果參數輸入無效，則使用者會收到錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="a8866-109">If the parameter input is not valid, the user receives an error message.</span></span>
<span data-ttu-id="a8866-110">每個驗證參數都會定義 PowerShell 強制執行的驗證規則。</span><span class="sxs-lookup"><span data-stu-id="a8866-110">Each validation parameter defines a validation rule that is enforced by PowerShell.</span></span>

<span data-ttu-id="a8866-111">PowerShell 會根據下列屬性來強制執行驗證規則。</span><span class="sxs-lookup"><span data-stu-id="a8866-111">PowerShell enforces the validation rules based on the following attributes.</span></span>

### <a name="validatecount"></a><span data-ttu-id="a8866-112">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="a8866-112">ValidateCount</span></span>

<span data-ttu-id="a8866-113">指定參數可以接受的引數數目下限和上限。</span><span class="sxs-lookup"><span data-stu-id="a8866-113">Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span>
<span data-ttu-id="a8866-114">如需詳細資訊，請參閱 [ValidateCount 屬性聲明](./validatecount-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="a8866-114">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="a8866-115">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="a8866-115">ValidateLength</span></span>

<span data-ttu-id="a8866-116">指定參數引數中的最小和最大字元數。</span><span class="sxs-lookup"><span data-stu-id="a8866-116">Specifies the minimum and maximum number of characters in the parameter argument.</span></span>
<span data-ttu-id="a8866-117">如需詳細資訊，請參閱 [ValidateLength 屬性聲明](./validatelength-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="a8866-117">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="a8866-118">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="a8866-118">ValidatePattern</span></span>

<span data-ttu-id="a8866-119">指定驗證參數引數的正則運算式。</span><span class="sxs-lookup"><span data-stu-id="a8866-119">Specifies a regular expression that validates the parameter argument.</span></span>
<span data-ttu-id="a8866-120">如需詳細資訊，請參閱 [ValidatePattern 屬性聲明](./validatepattern-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="a8866-120">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="a8866-121">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="a8866-121">ValidateRange</span></span>

<span data-ttu-id="a8866-122">指定參數引數的最小值和最大值。</span><span class="sxs-lookup"><span data-stu-id="a8866-122">Specifies the minimum and maximum values of the parameter argument.</span></span>
<span data-ttu-id="a8866-123">如需詳細資訊，請參閱 [ValidateRange 屬性聲明](./validaterange-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="a8866-123">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="a8866-124">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="a8866-124">ValidateSet</span></span>

<span data-ttu-id="a8866-125">為參數引數指定有效的值。</span><span class="sxs-lookup"><span data-stu-id="a8866-125">Specifies the valid values for the parameter argument.</span></span>
<span data-ttu-id="a8866-126">如需詳細資訊，請參閱 [ValidateSet 屬性聲明](./validateset-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="a8866-126">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a8866-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8866-127">See Also</span></span>

[<span data-ttu-id="a8866-128">如何驗證參數輸入</span><span class="sxs-lookup"><span data-stu-id="a8866-128">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

[<span data-ttu-id="a8866-129">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a8866-129">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
