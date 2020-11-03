---
description: 描述在 PowerShell 中比較值的運算子。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comparison_operators?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Comparison_Operators
ms.openlocfilehash: b6076e20ad3ecbe9f2def157bb20bdb3bee5b7ad
ms.sourcegitcommit: c9e56ec489522c706b8d6b8733f3f015d6d7e893
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208552"
---
# <a name="about-comparison-operators"></a><span data-ttu-id="0707f-104">關於比較運算子</span><span class="sxs-lookup"><span data-stu-id="0707f-104">About Comparison Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="0707f-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="0707f-105">Short description</span></span>
<span data-ttu-id="0707f-106">描述在 PowerShell 中比較值的運算子。</span><span class="sxs-lookup"><span data-stu-id="0707f-106">Describes the operators that compare values in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="0707f-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="0707f-107">Long description</span></span>

<span data-ttu-id="0707f-108">比較運算子可讓您指定比較值的條件，並尋找符合指定模式的值。</span><span class="sxs-lookup"><span data-stu-id="0707f-108">Comparison operators let you specify conditions for comparing values and finding values that match specified patterns.</span></span> <span data-ttu-id="0707f-109">若要使用比較運算子，請指定要與分隔這些值的運算子一起比較的值。</span><span class="sxs-lookup"><span data-stu-id="0707f-109">To use a comparison operator, specify the values that you want to compare together with an operator that separates these values.</span></span>

<span data-ttu-id="0707f-110">PowerShell 包含下列比較運算子：</span><span class="sxs-lookup"><span data-stu-id="0707f-110">PowerShell includes the following comparison operators:</span></span>

| <span data-ttu-id="0707f-111">類型</span><span class="sxs-lookup"><span data-stu-id="0707f-111">Type</span></span>        | <span data-ttu-id="0707f-112">運算子</span><span class="sxs-lookup"><span data-stu-id="0707f-112">Operators</span></span>    | <span data-ttu-id="0707f-113">說明</span><span class="sxs-lookup"><span data-stu-id="0707f-113">Description</span></span>                                 |
| ----------- | ------------ | --------------------------------------------|
| <span data-ttu-id="0707f-114">等式</span><span class="sxs-lookup"><span data-stu-id="0707f-114">Equality</span></span>    | <span data-ttu-id="0707f-115">-eq</span><span class="sxs-lookup"><span data-stu-id="0707f-115">-eq</span></span>          | <span data-ttu-id="0707f-116">等於</span><span class="sxs-lookup"><span data-stu-id="0707f-116">equals</span></span>                                      |
|             | <span data-ttu-id="0707f-117">-ne</span><span class="sxs-lookup"><span data-stu-id="0707f-117">-ne</span></span>          | <span data-ttu-id="0707f-118">不等於</span><span class="sxs-lookup"><span data-stu-id="0707f-118">not equals</span></span>                                  |
|             | <span data-ttu-id="0707f-119">-gt</span><span class="sxs-lookup"><span data-stu-id="0707f-119">-gt</span></span>          | <span data-ttu-id="0707f-120">大於</span><span class="sxs-lookup"><span data-stu-id="0707f-120">greater than</span></span>                                |
|             | <span data-ttu-id="0707f-121">-ge</span><span class="sxs-lookup"><span data-stu-id="0707f-121">-ge</span></span>          | <span data-ttu-id="0707f-122">大於或等於</span><span class="sxs-lookup"><span data-stu-id="0707f-122">greater than or equal</span></span>                       |
|             | <span data-ttu-id="0707f-123">-lt</span><span class="sxs-lookup"><span data-stu-id="0707f-123">-lt</span></span>          | <span data-ttu-id="0707f-124">小於</span><span class="sxs-lookup"><span data-stu-id="0707f-124">less than</span></span>                                   |
|             | <span data-ttu-id="0707f-125">-le</span><span class="sxs-lookup"><span data-stu-id="0707f-125">-le</span></span>          | <span data-ttu-id="0707f-126">小於或等於</span><span class="sxs-lookup"><span data-stu-id="0707f-126">less than or equal</span></span>                          |
|             |              |                                             |
| <span data-ttu-id="0707f-127">Matching</span><span class="sxs-lookup"><span data-stu-id="0707f-127">Matching</span></span>    | <span data-ttu-id="0707f-128">-like</span><span class="sxs-lookup"><span data-stu-id="0707f-128">-like</span></span>        | <span data-ttu-id="0707f-129">當字串符合萬用字元時傳回 true</span><span class="sxs-lookup"><span data-stu-id="0707f-129">Returns true when string matches wildcard</span></span>   |
|             |              | <span data-ttu-id="0707f-130">模式</span><span class="sxs-lookup"><span data-stu-id="0707f-130">pattern</span></span>                                     |
|             | <span data-ttu-id="0707f-131">-notlike</span><span class="sxs-lookup"><span data-stu-id="0707f-131">-notlike</span></span>     | <span data-ttu-id="0707f-132">當字串不相符時傳回 true</span><span class="sxs-lookup"><span data-stu-id="0707f-132">Returns true when string does not match</span></span>     |
|             |              | <span data-ttu-id="0707f-133">萬用字元模式</span><span class="sxs-lookup"><span data-stu-id="0707f-133">wildcard pattern</span></span>                            |
|             | <span data-ttu-id="0707f-134">-match</span><span class="sxs-lookup"><span data-stu-id="0707f-134">-match</span></span>       | <span data-ttu-id="0707f-135">當字串符合 RegEx 時傳回 true</span><span class="sxs-lookup"><span data-stu-id="0707f-135">Returns true when string matches regex</span></span>      |
|             |              | <span data-ttu-id="0707f-136">方式$matches 包含相符的字串</span><span class="sxs-lookup"><span data-stu-id="0707f-136">pattern; $matches contains matching strings</span></span> |
|             | <span data-ttu-id="0707f-137">-notmatch</span><span class="sxs-lookup"><span data-stu-id="0707f-137">-notmatch</span></span>    | <span data-ttu-id="0707f-138">當字串不相符時傳回 true</span><span class="sxs-lookup"><span data-stu-id="0707f-138">Returns true when string does not match</span></span>     |
|             |              | <span data-ttu-id="0707f-139">RegEx 模式;$matches 包含相符的</span><span class="sxs-lookup"><span data-stu-id="0707f-139">regex pattern; $matches contains matching</span></span>   |
|             |              | <span data-ttu-id="0707f-140">字串</span><span class="sxs-lookup"><span data-stu-id="0707f-140">strings</span></span>                                     |
|             |              |                                             |
| <span data-ttu-id="0707f-141">Containment</span><span class="sxs-lookup"><span data-stu-id="0707f-141">Containment</span></span> | <span data-ttu-id="0707f-142">-contains</span><span class="sxs-lookup"><span data-stu-id="0707f-142">-contains</span></span>    | <span data-ttu-id="0707f-143">當參考值包含時傳回 true</span><span class="sxs-lookup"><span data-stu-id="0707f-143">Returns true when reference value contained</span></span> |
|             |              | <span data-ttu-id="0707f-144">在集合中</span><span class="sxs-lookup"><span data-stu-id="0707f-144">in a collection</span></span>                             |
|             | <span data-ttu-id="0707f-145">-notcontains</span><span class="sxs-lookup"><span data-stu-id="0707f-145">-notcontains</span></span> | <span data-ttu-id="0707f-146">如果參考值不是，則傳回 true</span><span class="sxs-lookup"><span data-stu-id="0707f-146">Returns true when reference value not</span></span>       |
|             |              | <span data-ttu-id="0707f-147">包含在集合中</span><span class="sxs-lookup"><span data-stu-id="0707f-147">contained in a collection</span></span>                   |
|             | <span data-ttu-id="0707f-148">-in</span><span class="sxs-lookup"><span data-stu-id="0707f-148">-in</span></span>          | <span data-ttu-id="0707f-149">當包含在中的測試值時傳回 true</span><span class="sxs-lookup"><span data-stu-id="0707f-149">Returns true when test value contained in a</span></span> |
|             |              | <span data-ttu-id="0707f-150">collection</span><span class="sxs-lookup"><span data-stu-id="0707f-150">collection</span></span>                                  |
|             | <span data-ttu-id="0707f-151">-notin</span><span class="sxs-lookup"><span data-stu-id="0707f-151">-notin</span></span>       | <span data-ttu-id="0707f-152">當測試值不包含時傳回 true</span><span class="sxs-lookup"><span data-stu-id="0707f-152">Returns true when test value not contained</span></span>  |
|             |              | <span data-ttu-id="0707f-153">在集合中</span><span class="sxs-lookup"><span data-stu-id="0707f-153">in a collection</span></span>                             |
|             |              |                                             |
| <span data-ttu-id="0707f-154">取代</span><span class="sxs-lookup"><span data-stu-id="0707f-154">Replacement</span></span> | <span data-ttu-id="0707f-155">-取代</span><span class="sxs-lookup"><span data-stu-id="0707f-155">-replace</span></span>     | <span data-ttu-id="0707f-156">取代字串模式</span><span class="sxs-lookup"><span data-stu-id="0707f-156">Replaces a string pattern</span></span>                   |
|             |              |                                             |
| <span data-ttu-id="0707f-157">類型</span><span class="sxs-lookup"><span data-stu-id="0707f-157">Type</span></span>        | <span data-ttu-id="0707f-158">-是</span><span class="sxs-lookup"><span data-stu-id="0707f-158">-is</span></span>          | <span data-ttu-id="0707f-159">如果兩個物件相同，則傳回 true</span><span class="sxs-lookup"><span data-stu-id="0707f-159">Returns true if both object are the same</span></span>    |
|             |              | <span data-ttu-id="0707f-160">類型</span><span class="sxs-lookup"><span data-stu-id="0707f-160">type</span></span>                                        |
|             | <span data-ttu-id="0707f-161">-isnot</span><span class="sxs-lookup"><span data-stu-id="0707f-161">-isnot</span></span>       | <span data-ttu-id="0707f-162">如果物件相同，則傳回 true</span><span class="sxs-lookup"><span data-stu-id="0707f-162">Returns true if the objects are not the same</span></span>|
|             |              | <span data-ttu-id="0707f-163">類型</span><span class="sxs-lookup"><span data-stu-id="0707f-163">type</span></span>                                        |

<span data-ttu-id="0707f-164">依預設，所有比較運算子都不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="0707f-164">By default, all comparison operators are case-insensitive.</span></span> <span data-ttu-id="0707f-165">若要讓比較運算子區分大小寫，請在運算子名稱之前加上 `c` 。</span><span class="sxs-lookup"><span data-stu-id="0707f-165">To make a comparison operator case-sensitive, precede the operator name with a `c`.</span></span> <span data-ttu-id="0707f-166">例如，區分大小寫的版本 `-eq` 是 `-ceq` 。</span><span class="sxs-lookup"><span data-stu-id="0707f-166">For example, the case-sensitive version of `-eq` is `-ceq`.</span></span> <span data-ttu-id="0707f-167">若要進行不區分大小寫的明確，請在運算子前面加上 `i` 。</span><span class="sxs-lookup"><span data-stu-id="0707f-167">To make the case-insensitivity explicit, precede the operator with an `i`.</span></span> <span data-ttu-id="0707f-168">例如，明確的不區分大小寫版本 `-eq` 為 `-ieq` 。</span><span class="sxs-lookup"><span data-stu-id="0707f-168">For example, the explicitly case-insensitive version of `-eq` is `-ieq`.</span></span>

<span data-ttu-id="0707f-169">當運算子的輸入是純量值時，比較運算子會傳回布林值。</span><span class="sxs-lookup"><span data-stu-id="0707f-169">When the input to an operator is a scalar value, comparison operators return a Boolean value.</span></span> <span data-ttu-id="0707f-170">當輸入是值的集合時，比較運算子會傳回任何相符的值。</span><span class="sxs-lookup"><span data-stu-id="0707f-170">When the input is a collection of values, the comparison operators return any matching values.</span></span> <span data-ttu-id="0707f-171">如果集合中沒有相符專案，比較運算子會傳回空陣列。</span><span class="sxs-lookup"><span data-stu-id="0707f-171">If there are no matches in a collection, comparison operators return an empty array.</span></span>

```powershell
PS> (1, 2 -eq 3).GetType().FullName
System.Object[]
```

<span data-ttu-id="0707f-172">例外狀況是內含專案運算子、In 運算子和型別運算子，這些運算子一律會傳回 **布林** 值。</span><span class="sxs-lookup"><span data-stu-id="0707f-172">The exceptions are the containment operators, the In operators, and the type operators, which always return a **Boolean** value.</span></span>

> [!NOTE]
> <span data-ttu-id="0707f-173">如果您需要比較值與 `$null` ，應該放 `$null` 在比較的左邊。</span><span class="sxs-lookup"><span data-stu-id="0707f-173">If you need to compare a value to `$null` you should put `$null` on the left-hand side of the comparison.</span></span> <span data-ttu-id="0707f-174">當您比較 `$null` **物件 []** 時，結果為 **False** ，因為比較物件是陣列。</span><span class="sxs-lookup"><span data-stu-id="0707f-174">When you compare `$null` to an **Object[]** the result is **False** because the comparison object is an array.</span></span> <span data-ttu-id="0707f-175">當您比較陣列與時 `$null` ，比較會篩選出任何 `$null` 儲存在陣列中的值。</span><span class="sxs-lookup"><span data-stu-id="0707f-175">When you compare an array to `$null`, the comparison filters out any `$null` values stored in the array.</span></span> <span data-ttu-id="0707f-176">例如：</span><span class="sxs-lookup"><span data-stu-id="0707f-176">For example:</span></span>
>
> ```powershell
> PS> $null -ne $null, "hello"
> True
> PS> $null, "hello" -ne $null
> hello
> ```

### <a name="equality-operators"></a><span data-ttu-id="0707f-177">相等運算子</span><span class="sxs-lookup"><span data-stu-id="0707f-177">Equality Operators</span></span>

<span data-ttu-id="0707f-178">`-eq` `-ne` 當一或多個輸入值相同于指定的模式時，相等運算子 (，) 會傳回 TRUE 或相符專案的值。</span><span class="sxs-lookup"><span data-stu-id="0707f-178">The equality operators (`-eq`, `-ne`) return a value of TRUE or the matches when one or more of the input values is identical to the specified pattern.</span></span> <span data-ttu-id="0707f-179">整個模式必須符合整個值。</span><span class="sxs-lookup"><span data-stu-id="0707f-179">The entire pattern must match an entire value.</span></span>

<span data-ttu-id="0707f-180">範例：</span><span class="sxs-lookup"><span data-stu-id="0707f-180">Example:</span></span>

#### <a name="-eq"></a><span data-ttu-id="0707f-181">-eq</span><span class="sxs-lookup"><span data-stu-id="0707f-181">-eq</span></span>

<span data-ttu-id="0707f-182">描述：等於。</span><span class="sxs-lookup"><span data-stu-id="0707f-182">Description: Equal to.</span></span> <span data-ttu-id="0707f-183">包含相同的值。</span><span class="sxs-lookup"><span data-stu-id="0707f-183">Includes an identical value.</span></span>

<span data-ttu-id="0707f-184">範例：</span><span class="sxs-lookup"><span data-stu-id="0707f-184">Example:</span></span>

```powershell
PS> 2 -eq 2
True

PS> 2 -eq 3
False

PS> 1,2,3 -eq 2
2
PS> "abc" -eq "abc"
True

PS> "abc" -eq "abc", "def"
False

PS> "abc", "def" -eq "abc"
abc
```

#### <a name="-ne"></a><span data-ttu-id="0707f-185">-ne</span><span class="sxs-lookup"><span data-stu-id="0707f-185">-ne</span></span>

<span data-ttu-id="0707f-186">描述：不等於。</span><span class="sxs-lookup"><span data-stu-id="0707f-186">Description: Not equal to.</span></span> <span data-ttu-id="0707f-187">包含不同的值。</span><span class="sxs-lookup"><span data-stu-id="0707f-187">Includes a different value.</span></span>

<span data-ttu-id="0707f-188">範例：</span><span class="sxs-lookup"><span data-stu-id="0707f-188">Example:</span></span>

```powershell
PS> "abc" -ne "def"
True

PS> "abc" -ne "abc"
False

PS> "abc" -ne "abc", "def"
True

PS> "abc", "def" -ne "abc"
def
```

#### <a name="-gt"></a><span data-ttu-id="0707f-189">-gt</span><span class="sxs-lookup"><span data-stu-id="0707f-189">-gt</span></span>

<span data-ttu-id="0707f-190">描述：大於。</span><span class="sxs-lookup"><span data-stu-id="0707f-190">Description: Greater-than.</span></span>

<span data-ttu-id="0707f-191">範例：</span><span class="sxs-lookup"><span data-stu-id="0707f-191">Example:</span></span>

```powershell
PS> 8 -gt 6
True

PS> 7, 8, 9 -gt 8
9
```

> [!NOTE]
> <span data-ttu-id="0707f-192">這應該不會與 `>` 其他許多程式設計語言中的大於運算子混淆。</span><span class="sxs-lookup"><span data-stu-id="0707f-192">This should not to be confused with `>`, the greater-than operator in many other programming languages.</span></span> <span data-ttu-id="0707f-193">在 PowerShell 中， `>` 是用來重新導向。</span><span class="sxs-lookup"><span data-stu-id="0707f-193">In PowerShell, `>` is used for redirection.</span></span> <span data-ttu-id="0707f-194">如需詳細資訊，請參閱 [About_redirection](about_Redirection.md#potential-confusion-with-comparison-operators)。</span><span class="sxs-lookup"><span data-stu-id="0707f-194">For more information, see [About_redirection](about_Redirection.md#potential-confusion-with-comparison-operators).</span></span>

#### <a name="-ge"></a><span data-ttu-id="0707f-195">-ge</span><span class="sxs-lookup"><span data-stu-id="0707f-195">-ge</span></span>

<span data-ttu-id="0707f-196">描述：大於或等於。</span><span class="sxs-lookup"><span data-stu-id="0707f-196">Description: Greater-than or equal to.</span></span>

<span data-ttu-id="0707f-197">範例：</span><span class="sxs-lookup"><span data-stu-id="0707f-197">Example:</span></span>

```powershell
PS> 8 -ge 8
True

PS> 7, 8, 9 -ge 8
8
9
```

#### <a name="-lt"></a><span data-ttu-id="0707f-198">-lt</span><span class="sxs-lookup"><span data-stu-id="0707f-198">-lt</span></span>

<span data-ttu-id="0707f-199">描述：小於。</span><span class="sxs-lookup"><span data-stu-id="0707f-199">Description: Less-than.</span></span>

<span data-ttu-id="0707f-200">範例：</span><span class="sxs-lookup"><span data-stu-id="0707f-200">Example:</span></span>

```powershell

PS> 8 -lt 6
False

PS> 7, 8, 9 -lt 8
7
```

#### <a name="-le"></a><span data-ttu-id="0707f-201">-le</span><span class="sxs-lookup"><span data-stu-id="0707f-201">-le</span></span>

<span data-ttu-id="0707f-202">描述：小於或等於。</span><span class="sxs-lookup"><span data-stu-id="0707f-202">Description: Less-than or equal to.</span></span>

<span data-ttu-id="0707f-203">範例：</span><span class="sxs-lookup"><span data-stu-id="0707f-203">Example:</span></span>

```powershell
PS> 6 -le 8
True

PS> 7, 8, 9 -le 8
7
8
```

### <a name="matching-operators"></a><span data-ttu-id="0707f-204">相符運算子</span><span class="sxs-lookup"><span data-stu-id="0707f-204">Matching Operators</span></span>

<span data-ttu-id="0707f-205">Like 運算子 (`-like` 和 `-notlike`) 使用萬用字元運算式來尋找符合或不符合指定模式的元素。</span><span class="sxs-lookup"><span data-stu-id="0707f-205">The like operators (`-like` and `-notlike`) find elements that match or do not match a specified pattern using wildcard expressions.</span></span>

<span data-ttu-id="0707f-206">語法為：</span><span class="sxs-lookup"><span data-stu-id="0707f-206">The syntax is:</span></span>

```powershell
<string[]> -like <wildcard-expression>
<string[]> -notlike <wildcard-expression>
```

<span data-ttu-id="0707f-207">符合運算子 (`-match` 和 `-notmatch`) 使用正則運算式來尋找符合或不符合指定模式的元素。</span><span class="sxs-lookup"><span data-stu-id="0707f-207">The match operators (`-match` and `-notmatch`) find elements that match or do not match a specified pattern using regular expressions.</span></span>

<span data-ttu-id="0707f-208">`$Matches`當運算子的左邊引數)  (的輸入是單一純量物件時，比對運算子會填入自動變數。</span><span class="sxs-lookup"><span data-stu-id="0707f-208">The match operators populate the `$Matches` automatic variable when the input (the left-side argument) to the operator is a single scalar object.</span></span> <span data-ttu-id="0707f-209">當輸入是純量時， `-match` 和 `-notmatch` 運算子會傳回布林值，並將自動變數的值設定 `$Matches` 為引數的相符元件。</span><span class="sxs-lookup"><span data-stu-id="0707f-209">When the input is scalar, the `-match` and `-notmatch` operators return a Boolean value and set the value of the `$Matches` automatic variable to the matched components of the argument.</span></span>

<span data-ttu-id="0707f-210">語法為：</span><span class="sxs-lookup"><span data-stu-id="0707f-210">The syntax is:</span></span>

```powershell
<string[]> -match <regular-expression>
<string[]> -notmatch <regular-expression>
```

#### <a name="-like"></a><span data-ttu-id="0707f-211">-like</span><span class="sxs-lookup"><span data-stu-id="0707f-211">-like</span></span>

<span data-ttu-id="0707f-212">描述：使用萬用字元 () 比對 \* 。</span><span class="sxs-lookup"><span data-stu-id="0707f-212">Description: Match using the wildcard character (\*).</span></span>

<span data-ttu-id="0707f-213">範例：</span><span class="sxs-lookup"><span data-stu-id="0707f-213">Example:</span></span>

```powershell
PS> "PowerShell" -like "*shell"
True

PS> "PowerShell", "Server" -like "*shell"
PowerShell
```

#### <a name="-notlike"></a><span data-ttu-id="0707f-214">-notlike</span><span class="sxs-lookup"><span data-stu-id="0707f-214">-notlike</span></span>

<span data-ttu-id="0707f-215">描述：不符合使用萬用字元 (\*) 。</span><span class="sxs-lookup"><span data-stu-id="0707f-215">Description: Does not match using the wildcard character (\*).</span></span>

<span data-ttu-id="0707f-216">範例：</span><span class="sxs-lookup"><span data-stu-id="0707f-216">Example:</span></span>

```powershell
PS> "PowerShell" -notlike "*shell"
False

PS> "PowerShell", "Server" -notlike "*shell"
Server
```

### <a name="-match"></a><span data-ttu-id="0707f-217">-match</span><span class="sxs-lookup"><span data-stu-id="0707f-217">-match</span></span>

<span data-ttu-id="0707f-218">描述：使用正則運算式比對字串。</span><span class="sxs-lookup"><span data-stu-id="0707f-218">Description: Matches a string using regular expressions.</span></span> <span data-ttu-id="0707f-219">當輸入是純量時，會填入 `$Matches` 自動變數。</span><span class="sxs-lookup"><span data-stu-id="0707f-219">When the input is scalar, it populates the `$Matches` automatic variable.</span></span>

<span data-ttu-id="0707f-220">如果輸入是集合， `-match` 和運算子會傳回 `-notmatch` 該集合的相符成員，但是運算子不會填入 `$Matches` 變數。</span><span class="sxs-lookup"><span data-stu-id="0707f-220">If the input is a collection, the `-match` and `-notmatch` operators return the matching members of that collection, but the operator does not populate the `$Matches` variable.</span></span>

<span data-ttu-id="0707f-221">例如，下列命令會將字串的集合提交給 `-match` 運算子。</span><span class="sxs-lookup"><span data-stu-id="0707f-221">For example, the following command submits a collection of strings to the `-match` operator.</span></span> <span data-ttu-id="0707f-222">`-match`運算子會傳回集合中符合的專案。</span><span class="sxs-lookup"><span data-stu-id="0707f-222">The `-match` operator returns the items in the collection that match.</span></span> <span data-ttu-id="0707f-223">它不會填入 `$Matches` 自動變數。</span><span class="sxs-lookup"><span data-stu-id="0707f-223">It does not populate the `$Matches` automatic variable.</span></span>

```powershell
PS> "Sunday", "Monday", "Tuesday" -match "sun"
Sunday

PS> $Matches
PS>
```

<span data-ttu-id="0707f-224">相反地，下列命令會將單一字串提交給 `-match` 運算子。</span><span class="sxs-lookup"><span data-stu-id="0707f-224">In contrast, the following command submits a single string to the `-match` operator.</span></span> <span data-ttu-id="0707f-225">運算子會傳回 `-match` 布林值，並填入 `$Matches` 自動變數。</span><span class="sxs-lookup"><span data-stu-id="0707f-225">The `-match` operator returns a Boolean value and populates the `$Matches` automatic variable.</span></span> <span data-ttu-id="0707f-226">`$Matches`自動變數是 **雜湊表** 。</span><span class="sxs-lookup"><span data-stu-id="0707f-226">The `$Matches` automatic variable is a **Hashtable** .</span></span> <span data-ttu-id="0707f-227">如果未使用群組或捕捉，則只會填入一個金鑰。</span><span class="sxs-lookup"><span data-stu-id="0707f-227">If no grouping or capturing is used, only one key is populated.</span></span>
<span data-ttu-id="0707f-228">機 `0` 碼代表所有相符的文字。</span><span class="sxs-lookup"><span data-stu-id="0707f-228">The `0` key represents all text that was matched.</span></span> <span data-ttu-id="0707f-229">如需使用正則運算式進行群組和捕捉的詳細資訊，請參閱 [about_Regular_Expressions](about_Regular_Expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="0707f-229">For more information about grouping and capturing using regular expressions, see [about_Regular_Expressions](about_Regular_Expressions.md).</span></span>

```powershell
PS> "Sunday" -match "sun"
True

PS> $Matches

Name                           Value
----                           -----
0                              Sun
```

<span data-ttu-id="0707f-230">請務必注意， `$Matches` 雜湊表只會包含第一次出現的任何相符模式。</span><span class="sxs-lookup"><span data-stu-id="0707f-230">It is important to note that the `$Matches` hashtable will only contain the first occurrence of any matching pattern.</span></span>

```powershell
PS> "Banana" -match "na"
True

PS> $Matches

Name                           Value
----                           -----
0                              na
```

> [!IMPORTANT]
> <span data-ttu-id="0707f-231">索引 `0` 鍵是 **整數** 。</span><span class="sxs-lookup"><span data-stu-id="0707f-231">The `0` key is an **Integer** .</span></span> <span data-ttu-id="0707f-232">您可以使用任何 **Hashtable** 方法來存取儲存的值。</span><span class="sxs-lookup"><span data-stu-id="0707f-232">You can use any **Hashtable** method to access the value stored.</span></span>
>
> ```powershell
> PS> "Good Dog" -match "Dog"
> True
>
> PS> $Matches[0]
> Dog
>
> PS> $Matches.Item(0)
> Dog
>
> PS> $Matches.0
> Dog
> ```

<span data-ttu-id="0707f-233">`-notmatch`當輸入是純量時，運算子會填入 `$Matches` 自動變數，而當它偵測到相符時，結果會是 False。</span><span class="sxs-lookup"><span data-stu-id="0707f-233">The `-notmatch` operator populates the `$Matches` automatic variable when the input is scalar and the result is False, that it, when it detects a match.</span></span>

```powershell
PS> "Sunday" -notmatch "rain"
True

PS> $matches
PS>

PS> "Sunday" -notmatch "day"
False

PS> $matches

Name                           Value
----                           -----
0                              day
```

#### <a name="-notmatch"></a><span data-ttu-id="0707f-234">-notmatch</span><span class="sxs-lookup"><span data-stu-id="0707f-234">-notmatch</span></span>

<span data-ttu-id="0707f-235">描述：不符合字串。</span><span class="sxs-lookup"><span data-stu-id="0707f-235">Description: Does not match a string.</span></span> <span data-ttu-id="0707f-236">使用正則運算式。</span><span class="sxs-lookup"><span data-stu-id="0707f-236">Uses regular expressions.</span></span> <span data-ttu-id="0707f-237">當輸入是純量時，會填入 `$Matches` 自動變數。</span><span class="sxs-lookup"><span data-stu-id="0707f-237">When the input is scalar, it populates the `$Matches` automatic variable.</span></span>

<span data-ttu-id="0707f-238">範例：</span><span class="sxs-lookup"><span data-stu-id="0707f-238">Example:</span></span>

```powershell
PS> "Sunday" -notmatch "sun"
False

PS> $matches
Name Value
---- -----
0    sun

PS> "Sunday", "Monday" -notmatch "sun"
Monday
```

### <a name="containment-operators"></a><span data-ttu-id="0707f-239">內含專案運算子</span><span class="sxs-lookup"><span data-stu-id="0707f-239">Containment Operators</span></span>

<span data-ttu-id="0707f-240">內含專案運算子 (`-contains` 和 `-notcontains`) 類似于等號比較運算子。</span><span class="sxs-lookup"><span data-stu-id="0707f-240">The containment operators (`-contains` and `-notcontains`) are similar to the equality operators.</span></span> <span data-ttu-id="0707f-241">不過，內含專案運算子一律會傳回布林值，即使輸入是集合也一樣。</span><span class="sxs-lookup"><span data-stu-id="0707f-241">However, the containment operators always return a Boolean value, even when the input is a collection.</span></span>

<span data-ttu-id="0707f-242">此外，和等號比較運算子不同的是，內含專案運算子會在偵測到第一個相符專案時，立即傳回值。</span><span class="sxs-lookup"><span data-stu-id="0707f-242">Also, unlike the equality operators, the containment operators return a value as soon as they detect the first match.</span></span> <span data-ttu-id="0707f-243">等號比較運算子會評估所有輸入，然後傳回集合中的所有相符專案。</span><span class="sxs-lookup"><span data-stu-id="0707f-243">The equality operators evaluate all input and then return all the matches in the collection.</span></span>

#### <a name="-contains"></a><span data-ttu-id="0707f-244">-contains</span><span class="sxs-lookup"><span data-stu-id="0707f-244">-contains</span></span>

<span data-ttu-id="0707f-245">描述：內含專案運算子。</span><span class="sxs-lookup"><span data-stu-id="0707f-245">Description: Containment operator.</span></span> <span data-ttu-id="0707f-246">指出參考值的集合是否包含單一測試值。</span><span class="sxs-lookup"><span data-stu-id="0707f-246">Tells whether a collection of reference values includes a single test value.</span></span> <span data-ttu-id="0707f-247">一律傳回布林值。</span><span class="sxs-lookup"><span data-stu-id="0707f-247">Always returns a Boolean value.</span></span> <span data-ttu-id="0707f-248">只有當測試值完全符合至少一個參考值時，才會傳回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="0707f-248">Returns TRUE only when the test value exactly matches at least one of the reference values.</span></span>

<span data-ttu-id="0707f-249">當測試值為集合時，Contains 運算子會使用參考相等。</span><span class="sxs-lookup"><span data-stu-id="0707f-249">When the test value is a collection, the Contains operator uses reference equality.</span></span> <span data-ttu-id="0707f-250">只有當其中一個參考值是測試值物件的相同實例時，才會傳回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="0707f-250">It returns TRUE only when one of the reference values is the same instance of the test value object.</span></span>

<span data-ttu-id="0707f-251">在非常大的集合中， `-contains` 運算子會傳回比等於運算子更快的結果。</span><span class="sxs-lookup"><span data-stu-id="0707f-251">In a very large collection, the `-contains` operator returns results quicker than the equal to operator.</span></span>

<span data-ttu-id="0707f-252">語法：</span><span class="sxs-lookup"><span data-stu-id="0707f-252">Syntax:</span></span>

`<Reference-values> -contains <Test-value>`

<span data-ttu-id="0707f-253">範例：</span><span class="sxs-lookup"><span data-stu-id="0707f-253">Examples:</span></span>

```powershell
PS> "abc", "def" -contains "def"
True

PS> "Windows", "PowerShell" -contains "Shell"
False  #Not an exact match

# Does the list of computers in $DomainServers include $ThisComputer?
PS> $DomainServers -contains $thisComputer
True

PS> "abc", "def", "ghi" -contains "abc", "def"
False

PS> $a = "abc", "def"
PS> "abc", "def", "ghi" -contains $a
False
PS> $a, "ghi" -contains $a
True
```

#### <a name="-notcontains"></a><span data-ttu-id="0707f-254">-notcontains</span><span class="sxs-lookup"><span data-stu-id="0707f-254">-notcontains</span></span>

<span data-ttu-id="0707f-255">描述：內含專案運算子。</span><span class="sxs-lookup"><span data-stu-id="0707f-255">Description: Containment operator.</span></span> <span data-ttu-id="0707f-256">指出參考值的集合是否包含單一測試值。</span><span class="sxs-lookup"><span data-stu-id="0707f-256">Tells whether a collection of reference values includes a single test value.</span></span> <span data-ttu-id="0707f-257">一律傳回布林值。</span><span class="sxs-lookup"><span data-stu-id="0707f-257">Always returns a Boolean value.</span></span> <span data-ttu-id="0707f-258">當測試值與至少一個參考值的完全相符時，就會傳回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="0707f-258">Returns TRUE when the test value is not an exact matches for at least one of the reference values.</span></span>

<span data-ttu-id="0707f-259">當測試值為集合時，NotContains 運算子會使用參考相等。</span><span class="sxs-lookup"><span data-stu-id="0707f-259">When the test value is a collection, the NotContains operator uses reference equality.</span></span>

<span data-ttu-id="0707f-260">語法：</span><span class="sxs-lookup"><span data-stu-id="0707f-260">Syntax:</span></span>

`<Reference-values> -notcontains <Test-value>`

<span data-ttu-id="0707f-261">範例：</span><span class="sxs-lookup"><span data-stu-id="0707f-261">Examples:</span></span>

```powershell
PS> "Windows", "PowerShell" -notcontains "Shell"
True  #Not an exact match

# Get cmdlet parameters, but exclude common parameters
function get-parms ($cmdlet)
{
    $Common = "Verbose", "Debug", "WarningAction", "WarningVariable",
      "ErrorAction", "ErrorVariable", "OutVariable", "OutBuffer"

    $allparms = (Get-Command $Cmdlet).parametersets |
      foreach {$_.Parameters} |
        foreach {$_.Name} | Sort-Object | Get-Unique

    $allparms | where {$Common -notcontains $_ }
}

# Find unapproved verbs in the functions in my module
PS> $ApprovedVerbs = Get-Verb | foreach {$_.verb}
PS> $myVerbs = Get-Command -Module MyModule | foreach {$_.verb}
PS> $myVerbs | where {$ApprovedVerbs -notcontains $_}
ForEach
Sort
Tee
Where
```

#### <a name="-in"></a><span data-ttu-id="0707f-262">-in</span><span class="sxs-lookup"><span data-stu-id="0707f-262">-in</span></span>

<span data-ttu-id="0707f-263">描述： In 運算子。</span><span class="sxs-lookup"><span data-stu-id="0707f-263">Description: In operator.</span></span> <span data-ttu-id="0707f-264">告知測試值是否出現在參考值的集合中。</span><span class="sxs-lookup"><span data-stu-id="0707f-264">Tells whether a test value appears in a collection of reference values.</span></span> <span data-ttu-id="0707f-265">一律傳回為布林值。</span><span class="sxs-lookup"><span data-stu-id="0707f-265">Always return as Boolean value.</span></span> <span data-ttu-id="0707f-266">只有當測試值完全符合至少一個參考值時，才會傳回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="0707f-266">Returns TRUE only when the test value exactly matches at least one of the reference values.</span></span>

<span data-ttu-id="0707f-267">當測試值為集合時，In 運算子會使用參考相等。</span><span class="sxs-lookup"><span data-stu-id="0707f-267">When the test value is a collection, the In operator uses reference equality.</span></span>
<span data-ttu-id="0707f-268">只有當其中一個參考值是測試值物件的相同實例時，才會傳回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="0707f-268">It returns TRUE only when one of the reference values is the same instance of the test value object.</span></span>

<span data-ttu-id="0707f-269">`-in`操作員是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="0707f-269">The `-in` operator was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="0707f-270">語法：</span><span class="sxs-lookup"><span data-stu-id="0707f-270">Syntax:</span></span>

`<Test-value> -in <Reference-values>`

<span data-ttu-id="0707f-271">範例：</span><span class="sxs-lookup"><span data-stu-id="0707f-271">Examples:</span></span>

```powershell
PS> "def" -in "abc", "def"
True

PS> "Shell" -in "Windows", "PowerShell"
False  #Not an exact match

PS> "Windows" -in "Windows", "PowerShell"
True  #An exact match

PS> "Windows", "PowerShell" -in "Windows", "PowerShell", "ServerManager"
False  #Using reference equality

PS> $a = "Windows", "PowerShell"
PS> $a -in $a, "ServerManager"
True  #Using reference equality

# Does the list of computers in $DomainServers include $ThisComputer?
PS> $thisComputer -in  $domainServers
True
```

#### <a name="-notin"></a><span data-ttu-id="0707f-272">-notin</span><span class="sxs-lookup"><span data-stu-id="0707f-272">-notin</span></span>

<span data-ttu-id="0707f-273">描述：告知測試值是否出現在參考值的集合中。</span><span class="sxs-lookup"><span data-stu-id="0707f-273">Description: Tells whether a test value appears in a collection of reference values.</span></span> <span data-ttu-id="0707f-274">一律傳回布林值。</span><span class="sxs-lookup"><span data-stu-id="0707f-274">Always returns a Boolean value.</span></span> <span data-ttu-id="0707f-275">當測試值與至少一個參考值完全相符時，就會傳回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="0707f-275">Returns TRUE when the test value is not an exact match for at least one of the reference values.</span></span>

<span data-ttu-id="0707f-276">當測試值為集合時，In 運算子會使用參考相等。</span><span class="sxs-lookup"><span data-stu-id="0707f-276">When the test value is a collection, the In operator uses reference equality.</span></span>
<span data-ttu-id="0707f-277">只有當其中一個參考值是測試值物件的相同實例時，才會傳回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="0707f-277">It returns TRUE only when one of the reference values is the same instance of the test value object.</span></span>

<span data-ttu-id="0707f-278">`-notin`操作員是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="0707f-278">The `-notin` operator was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="0707f-279">語法：</span><span class="sxs-lookup"><span data-stu-id="0707f-279">Syntax:</span></span>

`<Test-value> -notin <Reference-values>`

<span data-ttu-id="0707f-280">範例：</span><span class="sxs-lookup"><span data-stu-id="0707f-280">Examples:</span></span>

```powershell
PS> "def" -notin "abc", "def"
False

PS> "ghi" -notin "abc", "def"
True

PS> "Shell" -notin "Windows", "PowerShell"
True  #Not an exact match

PS> "Windows" -notin "Windows", "PowerShell"
False  #An exact match

# Find unapproved verbs in the functions in my module
PS> $ApprovedVerbs = Get-Verb | foreach {$_.verb}
PS> $MyVerbs = Get-Command -Module MyModule | foreach {$_.verb}

PS> $MyVerbs | where {$_ -notin $ApprovedVerbs}
ForEach
Sort
Tee
Where
```

### <a name="replacement-operator"></a><span data-ttu-id="0707f-281">取代運算子</span><span class="sxs-lookup"><span data-stu-id="0707f-281">Replacement Operator</span></span>

<span data-ttu-id="0707f-282">`-replace`運算子會使用正則運算式來取代具有指定值的所有或部分值。</span><span class="sxs-lookup"><span data-stu-id="0707f-282">The `-replace` operator replaces all or part of a value with the specified value using regular expressions.</span></span> <span data-ttu-id="0707f-283">您可以使用 `-replace` 運算子進行許多系統管理工作，例如重新命名檔案。</span><span class="sxs-lookup"><span data-stu-id="0707f-283">You can use the `-replace` operator for many administrative tasks, such as renaming files.</span></span> <span data-ttu-id="0707f-284">例如，下列命令會將所有 .txt 檔案的副檔名變更為 .log：</span><span class="sxs-lookup"><span data-stu-id="0707f-284">For example, the following command changes the file name extensions of all .txt files to .log:</span></span>

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.name -replace '\.txt$','.log' }
```

<span data-ttu-id="0707f-285">運算子的語法 `-replace` 如下所示，其中 `<original>` 預留位置代表要取代的字元，而 `<substitute>` 預留位置代表將取代這些字元的字元：</span><span class="sxs-lookup"><span data-stu-id="0707f-285">The syntax of the `-replace` operator is as follows, where the `<original>` placeholder represents the characters to be replaced, and the `<substitute>` placeholder represents the characters that will replace them:</span></span>

`<input> <operator> <original>, <substitute>`

<span data-ttu-id="0707f-286">依預設， `-replace` 運算子不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="0707f-286">By default, the `-replace` operator is case-insensitive.</span></span> <span data-ttu-id="0707f-287">若要區分大小寫，請使用 `-creplace` 。</span><span class="sxs-lookup"><span data-stu-id="0707f-287">To make it case sensitive, use `-creplace`.</span></span> <span data-ttu-id="0707f-288">若要讓它明確不區分大小寫，請使用 `-ireplace` 。</span><span class="sxs-lookup"><span data-stu-id="0707f-288">To make it explicitly case-insensitive, use `-ireplace`.</span></span>

<span data-ttu-id="0707f-289">請考慮以下範例：</span><span class="sxs-lookup"><span data-stu-id="0707f-289">Consider the following examples:</span></span>

```powershell
PS> "book" -replace "B", "C"
```

```Output
Cook
```

```powershell
"book" -ireplace "B", "C"
```

```Output
Cook
```

```powershell
"book" -creplace "B", "C"
```

```Output
book
```

<span data-ttu-id="0707f-290">您也可以使用正則運算式，以動態方式使用捕捉群組和替代來取代文字。</span><span class="sxs-lookup"><span data-stu-id="0707f-290">It is also possible to use regular expressions to dynamically replace text using capturing groups, and substitutions.</span></span> <span data-ttu-id="0707f-291">如需詳細資訊，請參閱 [about_Regular_Expressions](about_Regular_Expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="0707f-291">For more information, see [about_Regular_Expressions](about_Regular_Expressions.md).</span></span>

#### <a name="substitutions-in-regular-expressions"></a><span data-ttu-id="0707f-292">在規則運算式中執行替代</span><span class="sxs-lookup"><span data-stu-id="0707f-292">Substitutions in Regular Expressions</span></span>

<span data-ttu-id="0707f-293">此外，也可以在字串中參考捕捉群組 \<substitute\> 。</span><span class="sxs-lookup"><span data-stu-id="0707f-293">Additionally, capturing groups can be referenced in the \<substitute\> string.</span></span>
<span data-ttu-id="0707f-294">這是藉由使用 `$` 群組識別碼之前的字元來完成。</span><span class="sxs-lookup"><span data-stu-id="0707f-294">This is done by using the `$` character before the group identifier.</span></span>

<span data-ttu-id="0707f-295">參考「捕獲群組」的兩個方式是依 **編號** 和 **名稱**</span><span class="sxs-lookup"><span data-stu-id="0707f-295">Two of the ways to reference capturing groups is by **Number** and by **Name**</span></span>

- <span data-ttu-id="0707f-296">依 **編號** 的 -
   捕獲群組會由左至右編號。</span><span class="sxs-lookup"><span data-stu-id="0707f-296">By **Number** -
Capturing Groups are numbered from left to right.</span></span>

  ```powershell
  "John D. Smith" -replace "(\w+) (\w+)\. (\w+)", '$1.$2.$3@contoso.com'
  ```

  ```Output
  John.D.Smith@contoso.com
  ```

- <span data-ttu-id="0707f-297">依 **Name** 名稱， -
   也可以依名稱參考名稱的捕獲群組。</span><span class="sxs-lookup"><span data-stu-id="0707f-297">By **Name** -
Capturing Groups can also be referenced by name.</span></span>

  ```powershell
  "CONTOSO\Administrator" -replace '\w+\\(?<user>\w+)', 'FABRIKAM\${user}'
  ```

  ```Output
  FABRIKOM\Administrator
  ```

> [!WARNING]
> <span data-ttu-id="0707f-298">由於 `$` 字元是在字串展開中使用，因此您必須使用常值字串搭配替代，或將字元換用 `$` 。</span><span class="sxs-lookup"><span data-stu-id="0707f-298">Since the `$` character is used in string expansion, you will need to use literal strings with substitution, or escape the `$` character.</span></span>
>
> ```powershell
> 'Hello World' -replace '(\w+) \w+', "`$1 Universe"
> ```
>
> ```Output
> Hello Universe
> ```
>
> <span data-ttu-id="0707f-299">此外，因為在 `$` 替代中使用字元，所以您必須將字串中的任何實例都換用。</span><span class="sxs-lookup"><span data-stu-id="0707f-299">Additionally, since the `$` character is used in substitution, you will need to escape any instances in your string.</span></span>
>
> ```powershell
> '5.72' -replace '(.+)', '$$$1'
> ```
>
> ```Output
> $5.72
> ```

<span data-ttu-id="0707f-300">若要深入瞭解，請參閱[正則運算式中的](/dotnet/standard/base-types/substitutions-in-regular-expressions) [about_Regular_Expressions](about_Regular_Expressions.md)和替代</span><span class="sxs-lookup"><span data-stu-id="0707f-300">To learn more see [about_Regular_Expressions](about_Regular_Expressions.md) and [Substitutions in Regular Expressions](/dotnet/standard/base-types/substitutions-in-regular-expressions)</span></span>

### <a name="type-comparison"></a><span data-ttu-id="0707f-301">類型比較</span><span class="sxs-lookup"><span data-stu-id="0707f-301">Type comparison</span></span>

<span data-ttu-id="0707f-302">類型比較運算子 (`-is` 和 `-isnot`) 用來判斷物件是否為特定類型。</span><span class="sxs-lookup"><span data-stu-id="0707f-302">The type comparison operators (`-is` and `-isnot`) are used to determine if an object is a specific type.</span></span>

#### <a name="-is"></a><span data-ttu-id="0707f-303">-是</span><span class="sxs-lookup"><span data-stu-id="0707f-303">-is</span></span>

<span data-ttu-id="0707f-304">語法：</span><span class="sxs-lookup"><span data-stu-id="0707f-304">Syntax:</span></span>

`<object> -is <type reference>`

<span data-ttu-id="0707f-305">範例：</span><span class="sxs-lookup"><span data-stu-id="0707f-305">Example:</span></span>

```powershell
PS> $a = 1
PS> $b = "1"
PS> $a -is [int]
True
PS> $a -is $b.GetType()
False
```

#### <a name="-isnot"></a><span data-ttu-id="0707f-306">-isnot</span><span class="sxs-lookup"><span data-stu-id="0707f-306">-isnot</span></span>

<span data-ttu-id="0707f-307">語法：</span><span class="sxs-lookup"><span data-stu-id="0707f-307">Syntax:</span></span>

`<object> -isnot <type reference>`

<span data-ttu-id="0707f-308">範例：</span><span class="sxs-lookup"><span data-stu-id="0707f-308">Example:</span></span>

```powershell
PS> $a = 1
PS> $b = "1"
PS> $a -isnot $b.GetType()
True
PS> $b -isnot [int]
True
```

## <a name="see-also"></a><span data-ttu-id="0707f-309">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0707f-309">SEE ALSO</span></span>

- [<span data-ttu-id="0707f-310">about_Operators</span><span class="sxs-lookup"><span data-stu-id="0707f-310">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="0707f-311">about_Regular_Expressions</span><span class="sxs-lookup"><span data-stu-id="0707f-311">about_Regular_Expressions</span></span>](about_Regular_Expressions.md)
- [<span data-ttu-id="0707f-312">about_Wildcards</span><span class="sxs-lookup"><span data-stu-id="0707f-312">about_Wildcards</span></span>](about_Wildcards.md)
- [<span data-ttu-id="0707f-313">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="0707f-313">Compare-Object</span></span>](xref:Microsoft.PowerShell.Utility.Compare-Object)
- [<span data-ttu-id="0707f-314">Foreach-Object</span><span class="sxs-lookup"><span data-stu-id="0707f-314">Foreach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)
- [<span data-ttu-id="0707f-315">Where-Object</span><span class="sxs-lookup"><span data-stu-id="0707f-315">Where-Object</span></span>](xref:Microsoft.PowerShell.Core.Where-Object)
