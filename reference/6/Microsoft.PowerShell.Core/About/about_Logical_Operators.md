---
description: 描述 PowerShell 中連接語句的運算子。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logical_operators?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logical_Operators
ms.openlocfilehash: 483217e929d55097b56eade801682ea4484d2624
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208619"
---
# <a name="about_logical_operators"></a><span data-ttu-id="d5d23-104">about_Logical_Operators</span><span class="sxs-lookup"><span data-stu-id="d5d23-104">about_Logical_Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="d5d23-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="d5d23-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="d5d23-106">描述 PowerShell 中連接語句的運算子。</span><span class="sxs-lookup"><span data-stu-id="d5d23-106">Describes the operators that connect statements in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="d5d23-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="d5d23-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="d5d23-108">PowerShell 邏輯運算子會連接運算式和語句，讓您可以使用單一運算式來測試多個條件。</span><span class="sxs-lookup"><span data-stu-id="d5d23-108">The PowerShell logical operators connect expressions and statements, allowing you to use a single expression to test for multiple conditions.</span></span>

<span data-ttu-id="d5d23-109">例如，下列語句會使用 and 運算子和 or 運算子來連接三個條件陳述式。</span><span class="sxs-lookup"><span data-stu-id="d5d23-109">For example, the following statement uses the and operator and the or operator to connect three conditional statements.</span></span> <span data-ttu-id="d5d23-110">只有當 $a 的值大於 $b 的值，且 $a 或 $b 小於時，此語句才會是 true。</span><span class="sxs-lookup"><span data-stu-id="d5d23-110">The statement is true only when the value of $a is greater than the value of $b, and either $a or $b is less than</span></span>
20.

```powershell
($a -gt $b) -and (($a -lt 20) -or ($b -lt 20))
```

<span data-ttu-id="d5d23-111">PowerShell 支援下列邏輯運算子。</span><span class="sxs-lookup"><span data-stu-id="d5d23-111">PowerShell supports the following logical operators.</span></span>

|<span data-ttu-id="d5d23-112">運算子</span><span class="sxs-lookup"><span data-stu-id="d5d23-112">Operator</span></span>|<span data-ttu-id="d5d23-113">描述</span><span class="sxs-lookup"><span data-stu-id="d5d23-113">Description</span></span>                        |<span data-ttu-id="d5d23-114">範例</span><span class="sxs-lookup"><span data-stu-id="d5d23-114">Example</span></span>                   |
|--------|-----------------------------------|--------------------------|
|`-and`  |<span data-ttu-id="d5d23-115">邏輯 AND。</span><span class="sxs-lookup"><span data-stu-id="d5d23-115">Logical AND.</span></span> <span data-ttu-id="d5d23-116">當兩者都為 TRUE</span><span class="sxs-lookup"><span data-stu-id="d5d23-116">TRUE when both</span></span>        |`(1 -eq 1) -and (1 -eq 2)`|
|        |<span data-ttu-id="d5d23-117">陳述為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="d5d23-117">statements are TRUE.</span></span>               |`False`                   |
|`-or`   |<span data-ttu-id="d5d23-118">邏輯 OR。</span><span class="sxs-lookup"><span data-stu-id="d5d23-118">Logical OR.</span></span> <span data-ttu-id="d5d23-119">若為 TRUE，則為 TRUE</span><span class="sxs-lookup"><span data-stu-id="d5d23-119">TRUE when either</span></span>       |`(1 -eq 1) -or (1 -eq 2)` |
|        |<span data-ttu-id="d5d23-120">語句為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="d5d23-120">statement is TRUE.</span></span>                 |`True`                    |
|`-xor`  |<span data-ttu-id="d5d23-121">邏輯排除 OR。</span><span class="sxs-lookup"><span data-stu-id="d5d23-121">Logical EXCLUSIVE OR.</span></span> <span data-ttu-id="d5d23-122">若為 TRUE</span><span class="sxs-lookup"><span data-stu-id="d5d23-122">TRUE when</span></span>    |`(1 -eq 1) -xor (2 -eq 2)`|
|        |<span data-ttu-id="d5d23-123">只有一個語句為 TRUE</span><span class="sxs-lookup"><span data-stu-id="d5d23-123">only one statement is TRUE</span></span>         |`False`                   |
|`-not`  |<span data-ttu-id="d5d23-124">邏輯 not。</span><span class="sxs-lookup"><span data-stu-id="d5d23-124">Logical not.</span></span> <span data-ttu-id="d5d23-125">否定語句</span><span class="sxs-lookup"><span data-stu-id="d5d23-125">Negates the statement</span></span> |`-not (1 -eq 1)`          |
|        |<span data-ttu-id="d5d23-126">如下所示。</span><span class="sxs-lookup"><span data-stu-id="d5d23-126">that follows.</span></span>                      |`False`                   |
|`!`     |<span data-ttu-id="d5d23-127">與 `-not` 相同</span><span class="sxs-lookup"><span data-stu-id="d5d23-127">Same as `-not`</span></span>                     |`!(1 -eq 1)`              |
|        |                                   |`False`                   |

 <span data-ttu-id="d5d23-128">附註：</span><span class="sxs-lookup"><span data-stu-id="d5d23-128">Note:</span></span>

<span data-ttu-id="d5d23-129">先前的範例也使用等於比較運算子 `-eq` 。</span><span class="sxs-lookup"><span data-stu-id="d5d23-129">The previous examples also use the equal to comparison operator `-eq`.</span></span> <span data-ttu-id="d5d23-130">如需詳細資訊，請參閱 [about_Comparison_Operators](about_Comparison_Operators.md)。</span><span class="sxs-lookup"><span data-stu-id="d5d23-130">For more information, see [about_Comparison_Operators](about_Comparison_Operators.md).</span></span> <span data-ttu-id="d5d23-131">這些範例也會使用整數的布林值。</span><span class="sxs-lookup"><span data-stu-id="d5d23-131">The examples also use the Boolean values of integers.</span></span> <span data-ttu-id="d5d23-132">整數0的值為 FALSE。</span><span class="sxs-lookup"><span data-stu-id="d5d23-132">The integer 0 has a value of FALSE.</span></span> <span data-ttu-id="d5d23-133">所有其他整數的值都是 TRUE。</span><span class="sxs-lookup"><span data-stu-id="d5d23-133">All other integers have a value of TRUE.</span></span>

<span data-ttu-id="d5d23-134">邏輯運算子的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="d5d23-134">The syntax of the logical operators is as follows:</span></span>

```
<statement> {-AND | -OR | -XOR} <statement>
{! | -NOT} <statement>
```

<span data-ttu-id="d5d23-135">使用邏輯運算子的語句會傳回布林值 (TRUE 或 FALSE) 值。</span><span class="sxs-lookup"><span data-stu-id="d5d23-135">Statements that use the logical operators return Boolean (TRUE or FALSE) values.</span></span>

<span data-ttu-id="d5d23-136">PowerShell 邏輯運算子只會評估判斷語句之真值所需的語句。</span><span class="sxs-lookup"><span data-stu-id="d5d23-136">The PowerShell logical operators evaluate only the statements required to determine the truth value of the statement.</span></span> <span data-ttu-id="d5d23-137">如果包含 and 運算子之語句中的左運算元為 FALSE，則不會評估右邊的運算元。</span><span class="sxs-lookup"><span data-stu-id="d5d23-137">If the left operand in a statement that contains the and operator is FALSE, the right operand is not evaluated.</span></span>
<span data-ttu-id="d5d23-138">如果包含或語句之語句中的左運算元為 TRUE，則不會評估右邊的運算元。</span><span class="sxs-lookup"><span data-stu-id="d5d23-138">If the left operand in a statement that contains the or statement is TRUE, the right operand is not evaluated.</span></span> <span data-ttu-id="d5d23-139">如此一來，您就可以使用語句的相同方式來使用這些語句 `If` 。</span><span class="sxs-lookup"><span data-stu-id="d5d23-139">As a result, you can use these statements in the same way that you would use the `If` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="d5d23-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5d23-140">SEE ALSO</span></span>

[<span data-ttu-id="d5d23-141">about_Operators</span><span class="sxs-lookup"><span data-stu-id="d5d23-141">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="d5d23-142">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="d5d23-142">Compare-Object</span></span>](xref:Microsoft.PowerShell.Utility.Compare-Object)

[<span data-ttu-id="d5d23-143">about_Comparison_operators</span><span class="sxs-lookup"><span data-stu-id="d5d23-143">about_Comparison_operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="d5d23-144">about_If</span><span class="sxs-lookup"><span data-stu-id="d5d23-144">about_If</span></span>](about_If.md)
