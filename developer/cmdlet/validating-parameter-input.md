---
title: 驗證參數輸入 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameters, validation rules
- validation, examples
- validation
ms.assetid: 3f15bf20-a068-4a7d-a170-bc43f755d1fe
caps.latest.revision: 14
ms.openlocfilehash: 171e3e974619e197a0bcc9dfc759297005e34568
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067139"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="b7130-102">驗證參數輸入</span><span class="sxs-lookup"><span data-stu-id="b7130-102">Validating Parameter Input</span></span>

<span data-ttu-id="b7130-103">PowerShell 可以驗證傳遞至數種方式中的 cmdlet 參數的引數。</span><span class="sxs-lookup"><span data-stu-id="b7130-103">PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span>
<span data-ttu-id="b7130-104">PowerShell 可以在長度、 範圍及引數的字元模式的驗證。</span><span class="sxs-lookup"><span data-stu-id="b7130-104">PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span>
<span data-ttu-id="b7130-105">它可以驗證引數可用 （計數） 的數目。</span><span class="sxs-lookup"><span data-stu-id="b7130-105">It can validate the number of arguments available (the count).</span></span>
<span data-ttu-id="b7130-106">這些驗證規則是由宣告 cmdlet 類別的公用屬性的參數屬性使用的驗證屬性定義。</span><span class="sxs-lookup"><span data-stu-id="b7130-106">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="b7130-107">若要驗證參數的引數，PowerShell 執行階段會使用驗證屬性所提供的資訊來執行此指令程式之前，請確認參數的值。</span><span class="sxs-lookup"><span data-stu-id="b7130-107">To validate a parameter argument, the PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span>
<span data-ttu-id="b7130-108">如果參數輸入不是有效的則使用者會收到一則錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="b7130-108">If the parameter input is not valid, the user receives an error message.</span></span>
<span data-ttu-id="b7130-109">每個驗證參數定義驗證規則會強制執行 powershell。</span><span class="sxs-lookup"><span data-stu-id="b7130-109">Each validation parameter defines a validation rule that is enforced by PowerShell.</span></span>

<span data-ttu-id="b7130-110">PowerShell 會強制執行驗證規則，根據下列屬性。</span><span class="sxs-lookup"><span data-stu-id="b7130-110">PowerShell enforces the validation rules based on the following attributes.</span></span>

### <a name="validatecount"></a><span data-ttu-id="b7130-111">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="b7130-111">ValidateCount</span></span>

<span data-ttu-id="b7130-112">指定最小和最大數目的參數可以接受的引數。</span><span class="sxs-lookup"><span data-stu-id="b7130-112">Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span>
<span data-ttu-id="b7130-113">如需詳細資訊，請參閱 < [ValidateCount 屬性宣告](./validatecount-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="b7130-113">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="b7130-114">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="b7130-114">ValidateLength</span></span>

<span data-ttu-id="b7130-115">參數的引數中指定最小和最大的字元數。</span><span class="sxs-lookup"><span data-stu-id="b7130-115">Specifies the minimum and maximum number of characters in the parameter argument.</span></span>
<span data-ttu-id="b7130-116">如需詳細資訊，請參閱 < [ValidateLength 屬性宣告](./validatelength-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="b7130-116">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="b7130-117">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="b7130-117">ValidatePattern</span></span>

<span data-ttu-id="b7130-118">指定驗證參數的引數的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="b7130-118">Specifies a regular expression that validates the parameter argument.</span></span>
<span data-ttu-id="b7130-119">如需詳細資訊，請參閱 < [ValidatePattern 屬性宣告](./validatepattern-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="b7130-119">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="b7130-120">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="b7130-120">ValidateRange</span></span>

<span data-ttu-id="b7130-121">指定參數的引數的最小和最大值。</span><span class="sxs-lookup"><span data-stu-id="b7130-121">Specifies the minimum and maximum values of the parameter argument.</span></span>
<span data-ttu-id="b7130-122">如需詳細資訊，請參閱 < [ValidateRange 屬性宣告](./validaterange-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="b7130-122">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="b7130-123">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="b7130-123">ValidateSet</span></span>

<span data-ttu-id="b7130-124">指定參數的引數的有效值。</span><span class="sxs-lookup"><span data-stu-id="b7130-124">Specifies the valid values for the parameter argument.</span></span>
<span data-ttu-id="b7130-125">如需詳細資訊，請參閱 < [ValidateSet 屬性宣告](./validateset-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="b7130-125">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b7130-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7130-126">See Also</span></span>

[<span data-ttu-id="b7130-127">如何驗證參數的輸入</span><span class="sxs-lookup"><span data-stu-id="b7130-127">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

[<span data-ttu-id="b7130-128">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b7130-128">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
