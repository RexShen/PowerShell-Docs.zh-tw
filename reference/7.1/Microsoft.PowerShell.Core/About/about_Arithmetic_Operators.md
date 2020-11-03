---
description: 描述在 PowerShell 中執行算術的運算子。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_arithmetic_operators?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Arithmetic_Operators
ms.openlocfilehash: 3ece7464198ff52fe6c22ccc54ceede84288bd7b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206763"
---
# <a name="about-arithmetic-operators"></a><span data-ttu-id="5784f-104">關於算術運算子</span><span class="sxs-lookup"><span data-stu-id="5784f-104">About Arithmetic Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="5784f-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="5784f-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="5784f-106">描述在 PowerShell 中執行算術的運算子。</span><span class="sxs-lookup"><span data-stu-id="5784f-106">Describes the operators that perform arithmetic in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="5784f-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="5784f-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="5784f-108">算術運算子會計算數位值。</span><span class="sxs-lookup"><span data-stu-id="5784f-108">Arithmetic operators calculate numeric values.</span></span> <span data-ttu-id="5784f-109">您可以使用一或多個算術運算子來加入、減去、相乘和除以值，以及計算除法運算 (模數) 的餘數。</span><span class="sxs-lookup"><span data-stu-id="5784f-109">You can use one or more arithmetic operators to add, subtract, multiply, and divide values, and to calculate the remainder (modulus) of a division operation.</span></span>

<span data-ttu-id="5784f-110">此外，加法運算子 (`+`) 和乘法運算子 (`*`) 也會在字串、陣列和雜湊表上運作。</span><span class="sxs-lookup"><span data-stu-id="5784f-110">In addition, the addition operator (`+`) and multiplication operator (`*`) also operate on strings, arrays, and hash tables.</span></span> <span data-ttu-id="5784f-111">加法運算子會串連輸入。</span><span class="sxs-lookup"><span data-stu-id="5784f-111">The addition operator concatenates the input.</span></span> <span data-ttu-id="5784f-112">乘法運算子會傳回輸入的多個複本。</span><span class="sxs-lookup"><span data-stu-id="5784f-112">The multiplication operator returns multiple copies of the input.</span></span> <span data-ttu-id="5784f-113">您甚至可以混搭算術語句中的物件類型。</span><span class="sxs-lookup"><span data-stu-id="5784f-113">You can even mix object types in an arithmetic statement.</span></span> <span data-ttu-id="5784f-114">用來評估語句的方法是由運算式中最左邊物件的型別所決定。</span><span class="sxs-lookup"><span data-stu-id="5784f-114">The method that is used to evaluate the statement is determined by the type of the leftmost object in the expression.</span></span>

<span data-ttu-id="5784f-115">從 PowerShell 2.0 開始，所有算術運算子都可在64位的數位上運作。</span><span class="sxs-lookup"><span data-stu-id="5784f-115">Beginning in PowerShell 2.0, all arithmetic operators work on 64-bit numbers.</span></span>

<span data-ttu-id="5784f-116">從 PowerShell 3.0 開始， `-shr` 會加入 (右移) 和 `-shl` (左移) ，以支援 PowerShell 中的位運算。</span><span class="sxs-lookup"><span data-stu-id="5784f-116">Beginning in PowerShell 3.0, the `-shr` (shift-right) and `-shl` (shift-left) are added to support bitwise arithmetic in PowerShell.</span></span>

<span data-ttu-id="5784f-117">PowerShell 支援下列算術運算子：</span><span class="sxs-lookup"><span data-stu-id="5784f-117">PowerShell supports the following arithmetic operators:</span></span>

|<span data-ttu-id="5784f-118">運算子</span><span class="sxs-lookup"><span data-stu-id="5784f-118">Operator</span></span>|<span data-ttu-id="5784f-119">描述</span><span class="sxs-lookup"><span data-stu-id="5784f-119">Description</span></span>                       |<span data-ttu-id="5784f-120">範例</span><span class="sxs-lookup"><span data-stu-id="5784f-120">Example</span></span>                      |
|--------|----------------------------------|-----------------------------|
| +      |<span data-ttu-id="5784f-121">新增整數;串連</span><span class="sxs-lookup"><span data-stu-id="5784f-121">Adds integers; concatenates</span></span>       |`6 + 2`                      |
|        |<span data-ttu-id="5784f-122">字串、陣列和雜湊表。</span><span class="sxs-lookup"><span data-stu-id="5784f-122">strings, arrays, and hash tables.</span></span> |`"file" + "name"`            |
|        |                                  |`@(1, "one") + @(2.0, "two")`|
|        |                                  |`@{"one" = 1} + @{"two" = 2}`|
| -      |<span data-ttu-id="5784f-123">從另一個值減去另一個值</span><span class="sxs-lookup"><span data-stu-id="5784f-123">Subtracts one value from another</span></span>  |`6 - 2`                      |
|        |<span data-ttu-id="5784f-124">value</span><span class="sxs-lookup"><span data-stu-id="5784f-124">value</span></span>                             |                             |
| -      |<span data-ttu-id="5784f-125">讓數位成為負數</span><span class="sxs-lookup"><span data-stu-id="5784f-125">Makes a number a negative number</span></span>  |`-6`                         |
|        |                                  |`(Get-Date).AddDays(-1)`     |
| *      |<span data-ttu-id="5784f-126">數位或複製字串相乘</span><span class="sxs-lookup"><span data-stu-id="5784f-126">Multiply numbers or copy strings</span></span>  |`6 * 2`                      |
|        |<span data-ttu-id="5784f-127">和陣列指定的數位</span><span class="sxs-lookup"><span data-stu-id="5784f-127">and arrays the specified number</span></span>   |`@("!") * 4`                 |
|        |<span data-ttu-id="5784f-128">的次數。</span><span class="sxs-lookup"><span data-stu-id="5784f-128">of times.</span></span>                         |`"!" * 3`                    |
| /      |<span data-ttu-id="5784f-129">兩個值相除。</span><span class="sxs-lookup"><span data-stu-id="5784f-129">Divides two values.</span></span>               |`6 / 2`                      |
| %      |<span data-ttu-id="5784f-130">模數-傳回其餘的</span><span class="sxs-lookup"><span data-stu-id="5784f-130">Modulus - returns the remainder of</span></span>|`7 % 2`                      |
|        |<span data-ttu-id="5784f-131">除法運算。</span><span class="sxs-lookup"><span data-stu-id="5784f-131">a division operation.</span></span>             |                             |
|<span data-ttu-id="5784f-132">-寬線</span><span class="sxs-lookup"><span data-stu-id="5784f-132">-band</span></span>   |<span data-ttu-id="5784f-133">位元 AND</span><span class="sxs-lookup"><span data-stu-id="5784f-133">Bitwise AND</span></span>                       |`5 -band 3`                  |
|<span data-ttu-id="5784f-134">-bnot</span><span class="sxs-lookup"><span data-stu-id="5784f-134">-bnot</span></span>   |<span data-ttu-id="5784f-135">位元 NOT</span><span class="sxs-lookup"><span data-stu-id="5784f-135">Bitwise NOT</span></span>                       |`-bnot 5`                    |
|<span data-ttu-id="5784f-136">-bor</span><span class="sxs-lookup"><span data-stu-id="5784f-136">-bor</span></span>    |<span data-ttu-id="5784f-137">位元 OR</span><span class="sxs-lookup"><span data-stu-id="5784f-137">Bitwise OR</span></span>                        |`5 -bor 0x03`                |
|<span data-ttu-id="5784f-138">-bxor</span><span class="sxs-lookup"><span data-stu-id="5784f-138">-bxor</span></span>   |<span data-ttu-id="5784f-139">位元 XOR</span><span class="sxs-lookup"><span data-stu-id="5784f-139">Bitwise XOR</span></span>                       |`5 -bxor 3`                  |
|<span data-ttu-id="5784f-140">-shl</span><span class="sxs-lookup"><span data-stu-id="5784f-140">-shl</span></span>    |<span data-ttu-id="5784f-141">將位向左移位</span><span class="sxs-lookup"><span data-stu-id="5784f-141">Shifts bits to the left</span></span>           |`102 -shl 2`                 |
|<span data-ttu-id="5784f-142">-shr</span><span class="sxs-lookup"><span data-stu-id="5784f-142">-shr</span></span>    |<span data-ttu-id="5784f-143">將位向右移位</span><span class="sxs-lookup"><span data-stu-id="5784f-143">Shifts bits to the right</span></span>          |`102 -shr 2`                 |

<span data-ttu-id="5784f-144">位運算子只適用于整數類型。</span><span class="sxs-lookup"><span data-stu-id="5784f-144">The bitwise operators only work on integer types.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="5784f-145">運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="5784f-145">OPERATOR PRECEDENCE</span></span>

<span data-ttu-id="5784f-146">PowerShell 會依下列連續處理算術運算子：</span><span class="sxs-lookup"><span data-stu-id="5784f-146">PowerShell processes arithmetic operators in the following order:</span></span>

|<span data-ttu-id="5784f-147">優先順序</span><span class="sxs-lookup"><span data-stu-id="5784f-147">Precedence</span></span>|<span data-ttu-id="5784f-148">運算子</span><span class="sxs-lookup"><span data-stu-id="5784f-148">Operator</span></span>          |<span data-ttu-id="5784f-149">描述</span><span class="sxs-lookup"><span data-stu-id="5784f-149">Description</span></span>                            |
|----------|------------------|---------------------------------------|
|<span data-ttu-id="5784f-150">1</span><span class="sxs-lookup"><span data-stu-id="5784f-150">1</span></span>         | `()`             |<span data-ttu-id="5784f-151">括號</span><span class="sxs-lookup"><span data-stu-id="5784f-151">Parentheses</span></span>                            |
|<span data-ttu-id="5784f-152">2</span><span class="sxs-lookup"><span data-stu-id="5784f-152">2</span></span>         | `-`              |<span data-ttu-id="5784f-153">負數值或一元運算子</span><span class="sxs-lookup"><span data-stu-id="5784f-153">For a negative number or unary operator</span></span>|
|<span data-ttu-id="5784f-154">3</span><span class="sxs-lookup"><span data-stu-id="5784f-154">3</span></span>         | <span data-ttu-id="5784f-155">`*`, `/`, `%`</span><span class="sxs-lookup"><span data-stu-id="5784f-155">`*`, `/`, `%`</span></span>    |<span data-ttu-id="5784f-156">針對乘法和除法</span><span class="sxs-lookup"><span data-stu-id="5784f-156">For multiplication and division</span></span>        |
|<span data-ttu-id="5784f-157">4</span><span class="sxs-lookup"><span data-stu-id="5784f-157">4</span></span>         | <span data-ttu-id="5784f-158">`+`, `-`</span><span class="sxs-lookup"><span data-stu-id="5784f-158">`+`, `-`</span></span>         |<span data-ttu-id="5784f-159">加法和減法</span><span class="sxs-lookup"><span data-stu-id="5784f-159">For addition and subtraction</span></span>           |
|<span data-ttu-id="5784f-160">5</span><span class="sxs-lookup"><span data-stu-id="5784f-160">5</span></span>         | <span data-ttu-id="5784f-161">`-band`, `-bnot`</span><span class="sxs-lookup"><span data-stu-id="5784f-161">`-band`, `-bnot`</span></span> |<span data-ttu-id="5784f-162">位運算的</span><span class="sxs-lookup"><span data-stu-id="5784f-162">For bitwise operations</span></span>                 |
|<span data-ttu-id="5784f-163">5</span><span class="sxs-lookup"><span data-stu-id="5784f-163">5</span></span>         | <span data-ttu-id="5784f-164">`-bor`, `-bxor`</span><span class="sxs-lookup"><span data-stu-id="5784f-164">`-bor`, `-bxor`</span></span>  |<span data-ttu-id="5784f-165">位運算的</span><span class="sxs-lookup"><span data-stu-id="5784f-165">For bitwise operations</span></span>                 |
|<span data-ttu-id="5784f-166">5</span><span class="sxs-lookup"><span data-stu-id="5784f-166">5</span></span>         | <span data-ttu-id="5784f-167">`-shr`, `-shl`</span><span class="sxs-lookup"><span data-stu-id="5784f-167">`-shr`, `-shl`</span></span>   |<span data-ttu-id="5784f-168">位運算的</span><span class="sxs-lookup"><span data-stu-id="5784f-168">For bitwise operations</span></span>                 |

<span data-ttu-id="5784f-169">PowerShell 會根據優先順序規則，從左至右處理運算式。</span><span class="sxs-lookup"><span data-stu-id="5784f-169">PowerShell processes the expressions from left to right according to the precedence rules.</span></span> <span data-ttu-id="5784f-170">下列範例顯示優先順序規則的效果：</span><span class="sxs-lookup"><span data-stu-id="5784f-170">The following examples show the effect of the precedence rules:</span></span>

|<span data-ttu-id="5784f-171">運算式</span><span class="sxs-lookup"><span data-stu-id="5784f-171">Expression</span></span> |<span data-ttu-id="5784f-172">結果</span><span class="sxs-lookup"><span data-stu-id="5784f-172">Result</span></span>|
|-----------|------|
|`3+6/3*4`  |`11`  |
|`3+6/(3*4)`|`3.5` |
|`(3+6)/3*4`|`12`  |

<span data-ttu-id="5784f-173">PowerShell 評估運算式的順序可能與您所使用的其他程式設計和指令碼語言不同。</span><span class="sxs-lookup"><span data-stu-id="5784f-173">The order in which PowerShell evaluates expressions might differ from other programming and scripting languages that you have used.</span></span> <span data-ttu-id="5784f-174">下列範例顯示覆雜的指派語句。</span><span class="sxs-lookup"><span data-stu-id="5784f-174">The following example shows a complicated assignment statement.</span></span>

```powershell
$a = 0
$b = @(1,2)
$c = @(-1,-2)

$b[$a] = $c[$a++]
```

<span data-ttu-id="5784f-175">在此範例中， `$a++` 會先評估運算式 `$b[$a]` 。</span><span class="sxs-lookup"><span data-stu-id="5784f-175">In this example, the expression `$a++` is evaluated before `$b[$a]`.</span></span>
<span data-ttu-id="5784f-176">評估 `$a++` 變更在 `$a` 語句中使用之後的值 `$c[$a++]` ，但在中使用它之前 `$b[$a]` 。</span><span class="sxs-lookup"><span data-stu-id="5784f-176">Evaluating `$a++` changes the value of `$a` after it is used in the statement `$c[$a++]`; but, before it is used in `$b[$a]`.</span></span> <span data-ttu-id="5784f-177">在 equals 中的變數不是， `$a` `$b[$a]` 因此語句會將 `1` `0` 值指派給 `$b[1]` ，而不是 `$b[0]` 。</span><span class="sxs-lookup"><span data-stu-id="5784f-177">The variable `$a` in `$b[$a]` equals `1`, not `0`; so, the statement assigns a value to `$b[1]`, not `$b[0]`.</span></span>

<span data-ttu-id="5784f-178">上述程式碼相當於：</span><span class="sxs-lookup"><span data-stu-id="5784f-178">The above code is equivalent to:</span></span>

```powershell
$a = 0
$b = @(1,2)
$c = @(-1,-2)

$tmp = $c[$a]
$a = $a + 1
$b[$a] = $tmp
```

## <a name="division-and-rounding"></a><span data-ttu-id="5784f-179">除法和進位</span><span class="sxs-lookup"><span data-stu-id="5784f-179">DIVISION AND ROUNDING</span></span>

<span data-ttu-id="5784f-180">當除法運算的商為整數時，PowerShell 會將值四捨五入為最接近的整數。</span><span class="sxs-lookup"><span data-stu-id="5784f-180">When the quotient of a division operation is an integer, PowerShell rounds the value to the nearest integer.</span></span> <span data-ttu-id="5784f-181">當值為時 `.5` ，會四捨五入為最接近的偶數整數。</span><span class="sxs-lookup"><span data-stu-id="5784f-181">When the value is `.5`, it rounds to the nearest even integer.</span></span>

<span data-ttu-id="5784f-182">下列範例顯示四捨五入至最接近的偶數整數的效果。</span><span class="sxs-lookup"><span data-stu-id="5784f-182">The following example shows the effect of rounding to the nearest even integer.</span></span>

|<span data-ttu-id="5784f-183">運算式</span><span class="sxs-lookup"><span data-stu-id="5784f-183">Expression</span></span>      |<span data-ttu-id="5784f-184">結果</span><span class="sxs-lookup"><span data-stu-id="5784f-184">Result</span></span>|
|----------------|------|
|`[int]( 5 / 2 )`|`2`   |
|`[int]( 7 / 2 )`|`4`   |

<span data-ttu-id="5784f-185">請注意 **_5/2_ = 2.5** 如何舍入為 **2** 。</span><span class="sxs-lookup"><span data-stu-id="5784f-185">Notice how **_5/2_ = 2.5** gets rounded to **2** .</span></span> <span data-ttu-id="5784f-186">但是， **_7/2_ = 3.5** 會舍入為 **4** 。</span><span class="sxs-lookup"><span data-stu-id="5784f-186">But, **_7/2_ = 3.5** gets rounded to **4** .</span></span>

<span data-ttu-id="5784f-187">您可以使用 `[Math]` 類別來取得不同的舍入行為。</span><span class="sxs-lookup"><span data-stu-id="5784f-187">You can use the `[Math]` class to get different rounding behavior.</span></span>

|                          <span data-ttu-id="5784f-188">運算式</span><span class="sxs-lookup"><span data-stu-id="5784f-188">Expression</span></span>                          | <span data-ttu-id="5784f-189">結果</span><span class="sxs-lookup"><span data-stu-id="5784f-189">Result</span></span> |
| ------------------------------------------------------------ | ------ |
| `[int][Math]::Round(5 / 2,[MidpointRounding]::AwayFromZero)` | `3`    |
| `[int][Math]::Ceiling(5 / 2)`                                | `3`    |
| `[int][Math]::Floor(5 / 2)`                                  | `2`    |

<span data-ttu-id="5784f-190">如需詳細資訊，請參閱 [數學. Round](/dotnet/api/system.math.round) 方法。</span><span class="sxs-lookup"><span data-stu-id="5784f-190">For more information, see the [Math.Round](/dotnet/api/system.math.round) method.</span></span>

## <a name="adding-and-multiplying-non-numeric-types"></a><span data-ttu-id="5784f-191">加入和相乘非數數值型別</span><span class="sxs-lookup"><span data-stu-id="5784f-191">ADDING AND MULTIPLYING NON-NUMERIC TYPES</span></span>

<span data-ttu-id="5784f-192">您可以加入數位、字串、陣列和雜湊表。</span><span class="sxs-lookup"><span data-stu-id="5784f-192">You can add numbers, strings, arrays, and hash tables.</span></span> <span data-ttu-id="5784f-193">而且，您可以將數位、字串和陣列相乘。</span><span class="sxs-lookup"><span data-stu-id="5784f-193">And, you can multiply numbers, strings, and arrays.</span></span> <span data-ttu-id="5784f-194">不過，您不能將雜湊資料表相乘。</span><span class="sxs-lookup"><span data-stu-id="5784f-194">However, you cannot multiply hash tables.</span></span>

<span data-ttu-id="5784f-195">當您加入字串、陣列或雜湊表時，會串連這些元素。</span><span class="sxs-lookup"><span data-stu-id="5784f-195">When you add strings, arrays, or hash tables, the elements are concatenated.</span></span> <span data-ttu-id="5784f-196">當您串連集合（例如陣列或雜湊表）時，會建立新的物件，其中包含兩個集合中的物件。</span><span class="sxs-lookup"><span data-stu-id="5784f-196">When you concatenate collections, such as arrays or hash tables, a new object is created that contains the objects from both collections.</span></span> <span data-ttu-id="5784f-197">如果您嘗試串連具有相同索引鍵的雜湊表，作業就會失敗。</span><span class="sxs-lookup"><span data-stu-id="5784f-197">If you try to concatenate hash tables that have the same key, the operation fails.</span></span>

<span data-ttu-id="5784f-198">例如，下列命令會建立兩個數組，然後新增它們：</span><span class="sxs-lookup"><span data-stu-id="5784f-198">For example, the following commands create two arrays and then add them:</span></span>

```powershell
$a = 1,2,3
$b = "A","B","C"
$a + $b
```

```output
1
2
3
A
B
C
```

<span data-ttu-id="5784f-199">您也可以在不同類型的物件上執行算數運算。</span><span class="sxs-lookup"><span data-stu-id="5784f-199">You can also perform arithmetic operations on objects of different types.</span></span>
<span data-ttu-id="5784f-200">PowerShell 執行的作業取決於作業中最左邊物件的 Microsoft .NET Framework 類型。</span><span class="sxs-lookup"><span data-stu-id="5784f-200">The operation that PowerShell performs is determined by the Microsoft .NET Framework type of the leftmost object in the operation.</span></span> <span data-ttu-id="5784f-201">PowerShell 會嘗試將作業中的所有物件轉換為第一個物件的 .NET Framework 類型。</span><span class="sxs-lookup"><span data-stu-id="5784f-201">PowerShell tries to convert all the objects in the operation to the .NET Framework type of the first object.</span></span> <span data-ttu-id="5784f-202">如果成功轉換物件，它會執行適合第一個物件之 .NET Framework 類型的作業。</span><span class="sxs-lookup"><span data-stu-id="5784f-202">If it succeeds in converting the objects, it performs the operation appropriate to the .NET Framework type of the first object.</span></span> <span data-ttu-id="5784f-203">如果無法轉換任何物件，則作業會失敗。</span><span class="sxs-lookup"><span data-stu-id="5784f-203">If it fails to convert any of the objects, the operation fails.</span></span>

<span data-ttu-id="5784f-204">下列範例示範加法和乘法運算子的用法;在包含不同物件類型的作業中。</span><span class="sxs-lookup"><span data-stu-id="5784f-204">The following examples demonstrate the use of the addition and multiplication operators; in operations that include different object types.</span></span> <span data-ttu-id="5784f-205">假設 `$array = 1,2,3` ：</span><span class="sxs-lookup"><span data-stu-id="5784f-205">Assume `$array = 1,2,3`:</span></span>

|<span data-ttu-id="5784f-206">運算式</span><span class="sxs-lookup"><span data-stu-id="5784f-206">Expression</span></span>       |<span data-ttu-id="5784f-207">結果</span><span class="sxs-lookup"><span data-stu-id="5784f-207">Result</span></span>                 |
|-----------------|-----------------------|
|`"file" + 16`    |`file16`               |
|`$array + 16`    |<span data-ttu-id="5784f-208">`1`,`2`,`3`,`16`</span><span class="sxs-lookup"><span data-stu-id="5784f-208">`1`,`2`,`3`,`16`</span></span>       |
|`$array + "file"`|<span data-ttu-id="5784f-209">`1`,`2`,`3`,`file`</span><span class="sxs-lookup"><span data-stu-id="5784f-209">`1`,`2`,`3`,`file`</span></span>     |
|`$array * 2`     |<span data-ttu-id="5784f-210">`1`,`2`,`3`,`1`,`2`,`3`</span><span class="sxs-lookup"><span data-stu-id="5784f-210">`1`,`2`,`3`,`1`,`2`,`3`</span></span>|
|`"file" * 3`     |`filefilefile`         |

<span data-ttu-id="5784f-211">因為用來評估語句的方法是由最左邊的物件所決定，所以 PowerShell 中的加法和乘法並未完全交換。</span><span class="sxs-lookup"><span data-stu-id="5784f-211">Because the method that is used to evaluate statements is determined by the leftmost object, addition and multiplication in PowerShell are not strictly commutative.</span></span> <span data-ttu-id="5784f-212">例如，不 `(a + b)` 一定會相等 `(b + a)` ，而且不 `(ab)` 一定會相等 `(ba)` 。</span><span class="sxs-lookup"><span data-stu-id="5784f-212">For example, `(a + b)` does not always equal `(b + a)`, and `(ab)` does not always equal `(ba)`.</span></span>

<span data-ttu-id="5784f-213">下列範例示範此原則：</span><span class="sxs-lookup"><span data-stu-id="5784f-213">The following examples demonstrate this principle:</span></span>

|<span data-ttu-id="5784f-214">運算式</span><span class="sxs-lookup"><span data-stu-id="5784f-214">Expression</span></span>   |<span data-ttu-id="5784f-215">結果</span><span class="sxs-lookup"><span data-stu-id="5784f-215">Result</span></span>                                               |
|-------------|-----------------------------------------------------|
|`"file" + 16`|`file16`                                             |
|`16 + "file"`|`Cannot convert value "file" to type "System.Int32".`|
|             |`Error: "Input string was not in a correct format."` |
|             |`At line:1 char:1`                                   |
|             |<span data-ttu-id="5784f-216">+ 16 + "file" '</span><span class="sxs-lookup"><span data-stu-id="5784f-216">+ 16 + "file"\`</span></span>                                       |

<span data-ttu-id="5784f-217">雜湊表是稍微不同的案例。</span><span class="sxs-lookup"><span data-stu-id="5784f-217">Hash tables are a slightly different case.</span></span> <span data-ttu-id="5784f-218">您可以將雜湊表加入至另一個雜湊表，只要加入的雜湊表沒有重複的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="5784f-218">You can add hash tables to another hash table, as long as, the added hash tables don't have duplicate keys.</span></span>

<span data-ttu-id="5784f-219">下列範例示範如何將雜湊表新增至其他雜湊表。</span><span class="sxs-lookup"><span data-stu-id="5784f-219">The following example show how to add hash tables to each other.</span></span>

```powershell
$hash1 = @{a=1; b=2; c=3}
$hash2 = @{c1="Server01"; c2="Server02"}
$hash1 + $hash2
```

```output
Name                           Value
----                           -----
c2                             Server02
a                              1
b                              2
c1                             Server01
c                              3
```

<span data-ttu-id="5784f-220">下列範例會擲回錯誤，因為兩個雜湊表中的其中一個索引鍵重複。</span><span class="sxs-lookup"><span data-stu-id="5784f-220">The following example throws an error because one of the keys is duplicated in both hash tables.</span></span>

```powershell
$hash1 = @{a=1; b=2; c=3}
$hash2 = @{c1="Server01"; c="Server02"}
$hash1 + $hash2
```

```output
Item has already been added. Key in dictionary: 'c'  Key being added: 'c'
At line:3 char:1
+ $hash1 + $hash2
+ ~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (:) [], ArgumentException
    + FullyQualifiedErrorId : System.ArgumentException
```

<span data-ttu-id="5784f-221">此外，您可以將雜湊表加入至陣列;而且整個雜湊資料表都會變成陣列中的專案。</span><span class="sxs-lookup"><span data-stu-id="5784f-221">Also, you can add a hash table to an array; and, the entire hash table becomes an item in the array.</span></span>

```powershell
$array1 = @(0, "Hello World", [datetime]::Now)
$hash1 = @{a=1; b=2}
$array2 = $array1 + $hash1
$array2
```

```output
0
Hello World

Monday, June 12, 2017 3:05:46 PM

Key   : a
Value : 1
Name  : a

Key   : b
Value : 2
Name  : b
```

<span data-ttu-id="5784f-222">不過，您無法將任何其他類型加入至雜湊表。</span><span class="sxs-lookup"><span data-stu-id="5784f-222">However, you cannot add any other type to a hash table.</span></span>

```powershell
$hash1 + 2
```

```output
A hash table can only be added to another hash table.
At line:3 char:1
+ $hash1 + 2
```

<span data-ttu-id="5784f-223">雖然加法運算子非常有用，但請使用指派運算子將專案加入至雜湊資料表和陣列。</span><span class="sxs-lookup"><span data-stu-id="5784f-223">Although the addition operators are very useful, use the assignment operators to add elements to hash tables and arrays.</span></span> <span data-ttu-id="5784f-224">如需詳細資訊，請參閱 [about_assignment_operators](about_Assignment_Operators.md)。</span><span class="sxs-lookup"><span data-stu-id="5784f-224">For more information see [about_assignment_operators](about_Assignment_Operators.md).</span></span> <span data-ttu-id="5784f-225">下列範例會使用 `+=` 指派運算子將專案加入至陣列：</span><span class="sxs-lookup"><span data-stu-id="5784f-225">The following examples use the `+=` assignment operator to add items to an array:</span></span>

```powershell
$array = @()
(0..9).foreach{ $array += $_ }
$array
```

```output
0
1
2
```

## <a name="type-conversion-to-accommodate-result"></a><span data-ttu-id="5784f-226">輸入轉換以容納結果</span><span class="sxs-lookup"><span data-stu-id="5784f-226">TYPE CONVERSION TO ACCOMMODATE RESULT</span></span>

<span data-ttu-id="5784f-227">PowerShell 會自動選取最能表達結果的 .NET Framework 數數值型別，而不會失去精確度。</span><span class="sxs-lookup"><span data-stu-id="5784f-227">PowerShell automatically selects the .NET Framework numeric type that best expresses the result without losing precision.</span></span> <span data-ttu-id="5784f-228">例如：</span><span class="sxs-lookup"><span data-stu-id="5784f-228">For example:</span></span>

```powershell
2 + 3.1

(2). GetType().FullName
(2 + 3.1).GetType().FullName
```

```output
5.1
System.Int32
System.Double
```

<span data-ttu-id="5784f-229">如果作業的結果對該類型而言太大，結果的類型會加寬以容納結果，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="5784f-229">If the result of an operation is too large for the type, the type of the result is widened to accommodate the result, as in the following example:</span></span>

```powershell
(512MB).GetType().FullName
(512MB * 512MB).GetType().FullName
```

```output
System.Int32
System.Double
```

<span data-ttu-id="5784f-230">結果的型別不一定會與其中一個運算元相同。</span><span class="sxs-lookup"><span data-stu-id="5784f-230">The type of the result will not necessarily be the same as one of the operands.</span></span> <span data-ttu-id="5784f-231">在下列範例中，負值無法轉換成不帶正負號的整數，而且不帶正負號的整數太大而無法轉換成 `Int32` ：</span><span class="sxs-lookup"><span data-stu-id="5784f-231">In the following example, the negative value cannot be cast to an unsigned integer, and the unsigned integer is too large to be cast to `Int32`:</span></span>

```powershell
([int32]::minvalue + [uint32]::maxvalue).gettype().fullname
```

```output
System.Int64
```

<span data-ttu-id="5784f-232">在此範例中， `Int64` 可以容納這兩種類型。</span><span class="sxs-lookup"><span data-stu-id="5784f-232">In this example, `Int64` can accommodate both types.</span></span>

<span data-ttu-id="5784f-233">此 `System.Decimal` 類型為例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5784f-233">The `System.Decimal` type is an exception.</span></span> <span data-ttu-id="5784f-234">如果任一個運算元具有 Decimal 類型，則結果會是 Decimal 類型。</span><span class="sxs-lookup"><span data-stu-id="5784f-234">If either operand has the Decimal type, the result will be of the Decimal type.</span></span> <span data-ttu-id="5784f-235">如果結果對 Decimal 類型而言太大，則不會轉換成 Double。</span><span class="sxs-lookup"><span data-stu-id="5784f-235">If the result is too large for the Decimal type, it will not be cast to Double.</span></span> <span data-ttu-id="5784f-236">相反地，會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="5784f-236">Instead, an error results.</span></span>

|<span data-ttu-id="5784f-237">運算式</span><span class="sxs-lookup"><span data-stu-id="5784f-237">Expression</span></span>               |<span data-ttu-id="5784f-238">結果</span><span class="sxs-lookup"><span data-stu-id="5784f-238">Result</span></span>                                         |
|-------------------------|-----------------------------------------------|
|`[Decimal]::maxvalue`    |`79228162514264337593543950335`                |
|`[Decimal]::maxvalue + 1`|`Value was either too large or too small for a`|
|                         |`Decimal.`                                     |

## <a name="arithmetic-operators-and-variables"></a><span data-ttu-id="5784f-239">算術運算子和變數</span><span class="sxs-lookup"><span data-stu-id="5784f-239">ARITHMETIC OPERATORS AND VARIABLES</span></span>

<span data-ttu-id="5784f-240">您也可以搭配變數來使用算術運算子。</span><span class="sxs-lookup"><span data-stu-id="5784f-240">You can also use arithmetic operators with variables.</span></span> <span data-ttu-id="5784f-241">運算子會對變數的值採取動作。</span><span class="sxs-lookup"><span data-stu-id="5784f-241">The operators act on the values of the variables.</span></span> <span data-ttu-id="5784f-242">下列範例示範如何使用算術運算子搭配變數：</span><span class="sxs-lookup"><span data-stu-id="5784f-242">The following examples demonstrate the use of arithmetic operators with variables:</span></span>

| <span data-ttu-id="5784f-243">運算式</span><span class="sxs-lookup"><span data-stu-id="5784f-243">Expression</span></span>                                    |<span data-ttu-id="5784f-244">結果</span><span class="sxs-lookup"><span data-stu-id="5784f-244">Result</span></span>      |
|-----------------------------------------------|------------|
|`$intA = 6`<br/>`$intB = 4`<br/>`$intA + $intB`|`10`        |
|`$a = "Power"`<br/>`$b = "Shell"`<br/>`$a + $b`|`PowerShell`|

## <a name="arithmetic-operators-and-commands"></a><span data-ttu-id="5784f-245">算術運算子和命令</span><span class="sxs-lookup"><span data-stu-id="5784f-245">ARITHMETIC OPERATORS AND COMMANDS</span></span>

<span data-ttu-id="5784f-246">一般而言，您會在具有數位、字串和陣列的運算式中使用算術運算子。</span><span class="sxs-lookup"><span data-stu-id="5784f-246">Typically, you use the arithmetic operators in expressions with numbers, strings, and arrays.</span></span> <span data-ttu-id="5784f-247">不過，您也可以搭配命令傳回的物件和這些物件的屬性來使用算術運算子。</span><span class="sxs-lookup"><span data-stu-id="5784f-247">However, you can also use arithmetic operators with the objects that commands return and with the properties of those objects.</span></span>

<span data-ttu-id="5784f-248">下列範例示範如何使用運算式中的算術運算子搭配 PowerShell 命令：</span><span class="sxs-lookup"><span data-stu-id="5784f-248">The following examples show how to use the arithmetic operators in expressions with PowerShell commands:</span></span>

```powershell
(get-date) + (new-timespan -day 1)
```

<span data-ttu-id="5784f-249">括弧運算子會依序強制評估 `get-date` Cmdlet 和 `new-timespan -day 1` Cmdlet 運算式的評估。</span><span class="sxs-lookup"><span data-stu-id="5784f-249">The parenthesis operator forces the evaluation of the `get-date` cmdlet and the evaluation of the `new-timespan -day 1` cmdlet expression, in that order.</span></span> <span data-ttu-id="5784f-250">這兩個結果接著會使用 `+` 運算子來新增。</span><span class="sxs-lookup"><span data-stu-id="5784f-250">Both results are then added using the `+` operator.</span></span>

```powershell
Get-Process | Where-Object { ($_.ws * 2) -gt 50mb }
```

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1896      39    50968      30620   264 1,572.55   1104 explorer
  12802      78   188468      81032   753 3,676.39   5676 OUTLOOK
    660       9    36168      26956   143    12.20    988 PowerShell
    561      14     6592      28144   110 1,010.09    496 services
   3476      80    34664      26092   234 ...45.69    876 svchost
    967      30    58804      59496   416   930.97   2508 WINWORD
```

<span data-ttu-id="5784f-251">在上述運算式中，每個處理常式工作空間 (`$_.ws`) 會乘以， `2` 而結果會與比較， `50mb` 以查看它是否大於該值。</span><span class="sxs-lookup"><span data-stu-id="5784f-251">In the above expression, each process working space (`$_.ws`) is multiplied by `2`; and, the result, compared against `50mb` to see if it is greater than that.</span></span>

## <a name="bitwise-operators"></a><span data-ttu-id="5784f-252">位元運算子</span><span class="sxs-lookup"><span data-stu-id="5784f-252">Bitwise Operators</span></span>

<span data-ttu-id="5784f-253">PowerShell 支援標準的位運算子，包括位 and (`-bAnd`) 、包含和排除的位 or 運算子 (`-bOr` 和 `-bXor`) ，以及位 NOT (`-bNot`) 。</span><span class="sxs-lookup"><span data-stu-id="5784f-253">PowerShell supports the standard bitwise operators, including bitwise-AND (`-bAnd`), the inclusive and exclusive bitwise-OR operators (`-bOr` and `-bXor`), and bitwise-NOT (`-bNot`).</span></span>

<span data-ttu-id="5784f-254">從 PowerShell 2.0 開始，所有位運算子都會使用64位整數。</span><span class="sxs-lookup"><span data-stu-id="5784f-254">Beginning in PowerShell 2.0, all bitwise operators work with 64-bit integers.</span></span>

<span data-ttu-id="5784f-255">從 PowerShell 3.0 開始， `-shr` 引進了 (右移) 和 `-shl` (shift 左) ，以支援 PowerShell 中的位運算。</span><span class="sxs-lookup"><span data-stu-id="5784f-255">Beginning in PowerShell 3.0, the `-shr` (shift-right) and `-shl` (shift-left) are introduced to support bitwise arithmetic in PowerShell.</span></span>

<span data-ttu-id="5784f-256">PowerShell 支援下列位運算子。</span><span class="sxs-lookup"><span data-stu-id="5784f-256">PowerShell supports the following bitwise operators.</span></span>

| <span data-ttu-id="5784f-257">運算子</span><span class="sxs-lookup"><span data-stu-id="5784f-257">Operator</span></span> | <span data-ttu-id="5784f-258">描述</span><span class="sxs-lookup"><span data-stu-id="5784f-258">Description</span></span>            | <span data-ttu-id="5784f-259">運算是</span><span class="sxs-lookup"><span data-stu-id="5784f-259">Expression</span></span>   | <span data-ttu-id="5784f-260">結果</span><span class="sxs-lookup"><span data-stu-id="5784f-260">Result</span></span> |
| -------- | ---------------------- | ------------ | ------ |
| `-band`  | <span data-ttu-id="5784f-261">位元 AND</span><span class="sxs-lookup"><span data-stu-id="5784f-261">Bitwise AND</span></span>            | `10 -band 3` | <span data-ttu-id="5784f-262">2</span><span class="sxs-lookup"><span data-stu-id="5784f-262">2</span></span>      |
| `-bor`   | <span data-ttu-id="5784f-263">位 OR (內含) </span><span class="sxs-lookup"><span data-stu-id="5784f-263">Bitwise OR (inclusive)</span></span> | `10 -bor 3`  | <span data-ttu-id="5784f-264">11</span><span class="sxs-lookup"><span data-stu-id="5784f-264">11</span></span>     |
| `-bxor`  | <span data-ttu-id="5784f-265">位或 (獨佔) </span><span class="sxs-lookup"><span data-stu-id="5784f-265">Bitwise OR (exclusive)</span></span> | `10 -bxor 3` | <span data-ttu-id="5784f-266">9</span><span class="sxs-lookup"><span data-stu-id="5784f-266">9</span></span>      |
| `-bnot`  | <span data-ttu-id="5784f-267">位元 NOT</span><span class="sxs-lookup"><span data-stu-id="5784f-267">Bitwise NOT</span></span>            | `-bNot 10`   | <span data-ttu-id="5784f-268">-11</span><span class="sxs-lookup"><span data-stu-id="5784f-268">-11</span></span>    |
| `-shl`   | <span data-ttu-id="5784f-269">左移</span><span class="sxs-lookup"><span data-stu-id="5784f-269">Shift-left</span></span>             | `102 -shl 2` | <span data-ttu-id="5784f-270">408</span><span class="sxs-lookup"><span data-stu-id="5784f-270">408</span></span>    |
| `-shr`   | <span data-ttu-id="5784f-271">向右移位</span><span class="sxs-lookup"><span data-stu-id="5784f-271">Shift-right</span></span>            | `102 -shr 1` | <span data-ttu-id="5784f-272">51</span><span class="sxs-lookup"><span data-stu-id="5784f-272">51</span></span>     |

<span data-ttu-id="5784f-273">位運算子會對值的二進位格式執行動作。</span><span class="sxs-lookup"><span data-stu-id="5784f-273">Bitwise operators act on the binary format of a value.</span></span> <span data-ttu-id="5784f-274">例如，數位10的位結構是 00001010 (根據1個位元組) ，而數位3的位結構是00000011。</span><span class="sxs-lookup"><span data-stu-id="5784f-274">For example, the bit structure for the number 10 is 00001010 (based on 1 byte), and the bit structure for the number 3 is 00000011.</span></span> <span data-ttu-id="5784f-275">當您使用位運算子比較10到3時，會比較每個位元組中的個別位。</span><span class="sxs-lookup"><span data-stu-id="5784f-275">When you use a bitwise operator to compare 10 to 3, the individual bits in each byte are compared.</span></span>

<span data-ttu-id="5784f-276">在位 AND 運算中，只有當兩個輸入位都是1時，才會將產生的位設定為1。</span><span class="sxs-lookup"><span data-stu-id="5784f-276">In a bitwise AND operation, the resulting bit is set to 1 only when both input bits are 1.</span></span>

```
1010      (10)
0011      ( 3)
--------------  bAND
0010      ( 2)
```

<span data-ttu-id="5784f-277">在位 OR (內含) 運算中，如果其中一個或兩個輸入位為1，則產生的位會設定為1。</span><span class="sxs-lookup"><span data-stu-id="5784f-277">In a bitwise OR (inclusive) operation, the resulting bit is set to 1 when either or both input bits are 1.</span></span> <span data-ttu-id="5784f-278">只有當兩個輸入位都設定為0時，才會將產生的位設定為0。</span><span class="sxs-lookup"><span data-stu-id="5784f-278">The resulting bit is set to 0 only when both input bits are set to 0.</span></span>

```
1010      (10)
0011      ( 3)
--------------  bOR (inclusive)
1011      (11)
```

<span data-ttu-id="5784f-279">在位或 (專有) 運算中，只有當一個輸入位為1時，才會將產生的位設定為1。</span><span class="sxs-lookup"><span data-stu-id="5784f-279">In a bitwise OR (exclusive) operation, the resulting bit is set to 1 only when one input bit is 1.</span></span>

```
1010      (10)
0011      ( 3)
--------------  bXOR (exclusive)
1001      ( 9)
```

<span data-ttu-id="5784f-280">位 NOT 運算子是一元運算子，會產生值的二進位補數。</span><span class="sxs-lookup"><span data-stu-id="5784f-280">The bitwise NOT operator is a unary operator that produces the binary complement of the value.</span></span> <span data-ttu-id="5784f-281">1位設定為0，而位0設定為1。</span><span class="sxs-lookup"><span data-stu-id="5784f-281">A bit of 1 is set to 0 and a bit of 0 is set to 1.</span></span>

<span data-ttu-id="5784f-282">例如，0的二進位補數為-1、最大不帶正負號整數 (0xffffffff) ，而-1 的二進位補數為0。</span><span class="sxs-lookup"><span data-stu-id="5784f-282">For example, the binary complement of 0 is -1, the maximum unsigned integer (0xffffffff), and the binary complement of -1 is 0.</span></span>

```powershell
-bNot 10
```

```Output
-11
```

```
0000 0000 0000 1010  (10)
------------------------- bNOT
1111 1111 1111 0101  (-11, xfffffff5)
```

<span data-ttu-id="5784f-283">在位左移位運算中，所有位都會移至左邊的 "n" 位置，其中 "n" 是右運算元的值。</span><span class="sxs-lookup"><span data-stu-id="5784f-283">In a bitwise shift-left operation, all bits are moved "n" places to the left, where "n" is the value of the right operand.</span></span> <span data-ttu-id="5784f-284">在一個位置插入零。</span><span class="sxs-lookup"><span data-stu-id="5784f-284">A zero is inserted in the ones place.</span></span>

<span data-ttu-id="5784f-285">當左運算元是整數 (32 位) 值時，右邊運算元的較低5個位會決定要移位的左運算元位數。</span><span class="sxs-lookup"><span data-stu-id="5784f-285">When the left operand is an Integer (32-bit) value, the lower 5 bits of the right operand determine how many bits of the left operand are shifted.</span></span>

<span data-ttu-id="5784f-286">當左運算元是 Long (64 位) 值時，右邊運算元的較低6位會決定要移位的左運算元位數。</span><span class="sxs-lookup"><span data-stu-id="5784f-286">When the left operand is a Long (64-bit) value, the lower 6 bits of the right operand determine how many bits of the left operand are shifted.</span></span>

|<span data-ttu-id="5784f-287">運算式</span><span class="sxs-lookup"><span data-stu-id="5784f-287">Expression</span></span> |<span data-ttu-id="5784f-288">結果</span><span class="sxs-lookup"><span data-stu-id="5784f-288">Result</span></span>|<span data-ttu-id="5784f-289">二進位結果</span><span class="sxs-lookup"><span data-stu-id="5784f-289">Binary Result</span></span>|
|-----------|------|-------------|
|`21 -shl 0`|<span data-ttu-id="5784f-290">21</span><span class="sxs-lookup"><span data-stu-id="5784f-290">21</span></span>    |<span data-ttu-id="5784f-291">0001 0101</span><span class="sxs-lookup"><span data-stu-id="5784f-291">0001 0101</span></span>    |
|`21 -shl 1`|<span data-ttu-id="5784f-292">42</span><span class="sxs-lookup"><span data-stu-id="5784f-292">42</span></span>    |<span data-ttu-id="5784f-293">0010 1010</span><span class="sxs-lookup"><span data-stu-id="5784f-293">0010 1010</span></span>    |
|`21 -shl 2`|<span data-ttu-id="5784f-294">84</span><span class="sxs-lookup"><span data-stu-id="5784f-294">84</span></span>    |<span data-ttu-id="5784f-295">0101 0100</span><span class="sxs-lookup"><span data-stu-id="5784f-295">0101 0100</span></span>    |

<span data-ttu-id="5784f-296">在位右移作業中，所有位都會移至右邊的 "n" 位置，其中 "n" 是由右運算元所指定。</span><span class="sxs-lookup"><span data-stu-id="5784f-296">In a bitwise shift-right operation, all bits are moved "n" places to the right, where "n" is specified by the right operand.</span></span> <span data-ttu-id="5784f-297">右移運算子 (-shr) 將正值或不帶正負號的值向右移動時，在最左邊的位置插入零。</span><span class="sxs-lookup"><span data-stu-id="5784f-297">The shift-right operator (-shr) inserts a zero in the left-most place when shifting a positive or unsigned value to the right.</span></span>

<span data-ttu-id="5784f-298">當左運算元是整數 (32 位) 值時，右邊運算元的較低5個位會決定要移位的左運算元位數。</span><span class="sxs-lookup"><span data-stu-id="5784f-298">When the left operand is an Integer (32-bit) value, the lower 5 bits of the right operand determine how many bits of the left operand are shifted.</span></span>

<span data-ttu-id="5784f-299">當左運算元是 Long (64 位) 值時，右邊運算元的較低6位會決定要移位的左運算元位數。</span><span class="sxs-lookup"><span data-stu-id="5784f-299">When the left operand is a Long (64-bit) value, the lower 6 bits of the right operand determine how many bits of the left operand are shifted.</span></span>

|<span data-ttu-id="5784f-300">運算式</span><span class="sxs-lookup"><span data-stu-id="5784f-300">Expression</span></span>              |<span data-ttu-id="5784f-301">結果</span><span class="sxs-lookup"><span data-stu-id="5784f-301">Result</span></span>      |<span data-ttu-id="5784f-302">Binary</span><span class="sxs-lookup"><span data-stu-id="5784f-302">Binary</span></span>     |<span data-ttu-id="5784f-303">Hex</span><span class="sxs-lookup"><span data-stu-id="5784f-303">Hex</span></span>         |
|------------------------|------------|-----------|------------|
|`21 -shr 0`             | <span data-ttu-id="5784f-304">21</span><span class="sxs-lookup"><span data-stu-id="5784f-304">21</span></span>         | <span data-ttu-id="5784f-305">0001 0101</span><span class="sxs-lookup"><span data-stu-id="5784f-305">0001 0101</span></span> | <span data-ttu-id="5784f-306">0x15</span><span class="sxs-lookup"><span data-stu-id="5784f-306">0x15</span></span>       |
|`21 -shr 1`             | <span data-ttu-id="5784f-307">10</span><span class="sxs-lookup"><span data-stu-id="5784f-307">10</span></span>         | <span data-ttu-id="5784f-308">0000 1010</span><span class="sxs-lookup"><span data-stu-id="5784f-308">0000 1010</span></span> | <span data-ttu-id="5784f-309">0x0A</span><span class="sxs-lookup"><span data-stu-id="5784f-309">0x0A</span></span>       |
|`21 -shr 2`             | <span data-ttu-id="5784f-310">5</span><span class="sxs-lookup"><span data-stu-id="5784f-310">5</span></span>          | <span data-ttu-id="5784f-311">0000 0101</span><span class="sxs-lookup"><span data-stu-id="5784f-311">0000 0101</span></span> | <span data-ttu-id="5784f-312">0x05</span><span class="sxs-lookup"><span data-stu-id="5784f-312">0x05</span></span>       |
|`21 -shr 31`            | <span data-ttu-id="5784f-313">0</span><span class="sxs-lookup"><span data-stu-id="5784f-313">0</span></span>          | <span data-ttu-id="5784f-314">0000 0000</span><span class="sxs-lookup"><span data-stu-id="5784f-314">0000 0000</span></span> | <span data-ttu-id="5784f-315">0x00</span><span class="sxs-lookup"><span data-stu-id="5784f-315">0x00</span></span>       |
|`21 -shr 32`            | <span data-ttu-id="5784f-316">21</span><span class="sxs-lookup"><span data-stu-id="5784f-316">21</span></span>         | <span data-ttu-id="5784f-317">0001 0101</span><span class="sxs-lookup"><span data-stu-id="5784f-317">0001 0101</span></span> | <span data-ttu-id="5784f-318">0x15</span><span class="sxs-lookup"><span data-stu-id="5784f-318">0x15</span></span>       |
|`21 -shr 64`            | <span data-ttu-id="5784f-319">21</span><span class="sxs-lookup"><span data-stu-id="5784f-319">21</span></span>         | <span data-ttu-id="5784f-320">0001 0101</span><span class="sxs-lookup"><span data-stu-id="5784f-320">0001 0101</span></span> | <span data-ttu-id="5784f-321">0x15</span><span class="sxs-lookup"><span data-stu-id="5784f-321">0x15</span></span>       |
|`21 -shr 65`            | <span data-ttu-id="5784f-322">10</span><span class="sxs-lookup"><span data-stu-id="5784f-322">10</span></span>         | <span data-ttu-id="5784f-323">0000 1010</span><span class="sxs-lookup"><span data-stu-id="5784f-323">0000 1010</span></span> | <span data-ttu-id="5784f-324">0x0A</span><span class="sxs-lookup"><span data-stu-id="5784f-324">0x0A</span></span>       |
|`21 -shr 66`            | <span data-ttu-id="5784f-325">5</span><span class="sxs-lookup"><span data-stu-id="5784f-325">5</span></span>          | <span data-ttu-id="5784f-326">0000 0101</span><span class="sxs-lookup"><span data-stu-id="5784f-326">0000 0101</span></span> | <span data-ttu-id="5784f-327">0x05</span><span class="sxs-lookup"><span data-stu-id="5784f-327">0x05</span></span>       |
|`[int]::MaxValue -shr 1`| <span data-ttu-id="5784f-328">1073741823</span><span class="sxs-lookup"><span data-stu-id="5784f-328">1073741823</span></span> |           | <span data-ttu-id="5784f-329">0x3FFFFFFF</span><span class="sxs-lookup"><span data-stu-id="5784f-329">0x3FFFFFFF</span></span> |
|`[int]::MinValue -shr 1`| <span data-ttu-id="5784f-330">-1073741824</span><span class="sxs-lookup"><span data-stu-id="5784f-330">-1073741824</span></span>|           | <span data-ttu-id="5784f-331">0xC0000000</span><span class="sxs-lookup"><span data-stu-id="5784f-331">0xC0000000</span></span> |
|`-1 -shr 1`             | <span data-ttu-id="5784f-332">-1</span><span class="sxs-lookup"><span data-stu-id="5784f-332">-1</span></span>         |           | <span data-ttu-id="5784f-333">0xFFFFFFFF</span><span class="sxs-lookup"><span data-stu-id="5784f-333">0xFFFFFFFF</span></span> |

## <a name="see-also"></a><span data-ttu-id="5784f-334">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5784f-334">SEE ALSO</span></span>

- [<span data-ttu-id="5784f-335">about_arrays</span><span class="sxs-lookup"><span data-stu-id="5784f-335">about_arrays</span></span>](about_Arrays.md)
- [<span data-ttu-id="5784f-336">about_assignment_operators</span><span class="sxs-lookup"><span data-stu-id="5784f-336">about_assignment_operators</span></span>](about_Assignment_Operators.md)
- [<span data-ttu-id="5784f-337">about_comparison_operators</span><span class="sxs-lookup"><span data-stu-id="5784f-337">about_comparison_operators</span></span>](about_Comparison_Operators.md)
- [<span data-ttu-id="5784f-338">about_hash_tables</span><span class="sxs-lookup"><span data-stu-id="5784f-338">about_hash_tables</span></span>](about_Hash_Tables.md)
- [<span data-ttu-id="5784f-339">about_operators</span><span class="sxs-lookup"><span data-stu-id="5784f-339">about_operators</span></span>](about_Operators.md)
- [<span data-ttu-id="5784f-340">about_variables</span><span class="sxs-lookup"><span data-stu-id="5784f-340">about_variables</span></span>](about_Variables.md)
- [<span data-ttu-id="5784f-341">Get-Date</span><span class="sxs-lookup"><span data-stu-id="5784f-341">Get-Date</span></span>](xref:Microsoft.PowerShell.Utility.Get-Date)
- [<span data-ttu-id="5784f-342">New-TimeSpan</span><span class="sxs-lookup"><span data-stu-id="5784f-342">New-TimeSpan</span></span>](xref:Microsoft.PowerShell.Utility.New-TimeSpan)
