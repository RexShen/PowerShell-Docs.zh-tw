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
ms.openlocfilehash: f7e5d4fb2f89bd6bc7036fdcff8f38e017d5d0e4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858844"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="ec371-102">驗證參數輸入</span><span class="sxs-lookup"><span data-stu-id="ec371-102">Validating Parameter Input</span></span>

<span data-ttu-id="ec371-103">Windows PowerShell 可以驗證傳遞至數種方式中的 cmdlet 參數的引數。</span><span class="sxs-lookup"><span data-stu-id="ec371-103">Windows PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span> <span data-ttu-id="ec371-104">Windows PowerShell 可以在長度、 範圍及引數的字元模式的驗證。</span><span class="sxs-lookup"><span data-stu-id="ec371-104">Windows PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span> <span data-ttu-id="ec371-105">它可以驗證引數可用 （計數） 的數目。</span><span class="sxs-lookup"><span data-stu-id="ec371-105">It can validate the number of arguments available (the count).</span></span> <span data-ttu-id="ec371-106">這些驗證規則是由宣告 cmdlet 類別的公用屬性的參數屬性使用的驗證屬性定義。</span><span class="sxs-lookup"><span data-stu-id="ec371-106">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="ec371-107">若要驗證參數的引數，Windows PowerShell 執行階段會使用驗證屬性所提供的資訊來執行此指令程式之前，請確認參數的值。</span><span class="sxs-lookup"><span data-stu-id="ec371-107">To validate a parameter argument, the Windows PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span> <span data-ttu-id="ec371-108">如果參數輸入不是有效的則使用者會收到一則錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="ec371-108">If the parameter input is not valid, the user receives an error message.</span></span> <span data-ttu-id="ec371-109">每個驗證參數定義驗證規則會強制執行 Windows powershell。</span><span class="sxs-lookup"><span data-stu-id="ec371-109">Each validation parameter defines a validation rule that is enforced by Windows PowerShell.</span></span>

<span data-ttu-id="ec371-110">Windows PowerShell 會強制執行驗證規則，根據下列屬性。</span><span class="sxs-lookup"><span data-stu-id="ec371-110">Windows PowerShell enforces the validation rules based on the following attributes.</span></span>

<span data-ttu-id="ec371-111">ValidateCount 指定最小和最大數目的參數可以接受的引數。</span><span class="sxs-lookup"><span data-stu-id="ec371-111">ValidateCount Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span> <span data-ttu-id="ec371-112">如需有關用來宣告這個屬性的語法的詳細資訊，請參閱[ValidateCount 屬性宣告](./validatecount-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="ec371-112">For more information about the syntax used to declare this attribute, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

<span data-ttu-id="ec371-113">ValidateLength 參數引數中指定最小和最大的字元數。</span><span class="sxs-lookup"><span data-stu-id="ec371-113">ValidateLength Specifies the minimum and maximum number of characters in the parameter argument.</span></span> <span data-ttu-id="ec371-114">如需有關用來宣告這個屬性的語法的詳細資訊，請參閱[ValidateLength 屬性宣告](./validatelength-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="ec371-114">For more information about the syntax used to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

<span data-ttu-id="ec371-115">ValidatePattern 會指定驗證參數的引數的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="ec371-115">ValidatePattern Specifies a regular expression that validates the parameter argument.</span></span> <span data-ttu-id="ec371-116">如需有關用來宣告這個屬性的語法的詳細資訊，請參閱[ValidatePattern 屬性宣告](./validatepattern-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="ec371-116">For more information about the syntax used to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

<span data-ttu-id="ec371-117">ValidateRange 指定參數的引數的最小和最大值。</span><span class="sxs-lookup"><span data-stu-id="ec371-117">ValidateRange Specifies the minimum and maximum values of the parameter argument.</span></span> <span data-ttu-id="ec371-118">如需有關用來宣告這個屬性的語法的詳細資訊，請參閱[ValidateRange 屬性宣告](./validaterange-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="ec371-118">For more information about the syntax used to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

<span data-ttu-id="ec371-119">ValidateSet 指定參數的引數的有效值。</span><span class="sxs-lookup"><span data-stu-id="ec371-119">ValidateSet Specifies the valid values for the parameter argument.</span></span> <span data-ttu-id="ec371-120">如需有關用來宣告這個屬性的語法的詳細資訊，請參閱[ValidateSet 屬性宣告](./validateset-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="ec371-120">For more information about the syntax used to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ec371-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec371-121">See Also</span></span>

[<span data-ttu-id="ec371-122">如何驗證參數的輸入</span><span class="sxs-lookup"><span data-stu-id="ec371-122">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

[<span data-ttu-id="ec371-123">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ec371-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
