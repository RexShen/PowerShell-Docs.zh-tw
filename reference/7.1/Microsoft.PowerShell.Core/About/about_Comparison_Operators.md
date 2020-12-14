---
description: 描述在 PowerShell 中比較值的運算子。
Locale: en-US
ms.date: 12/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comparison_operators?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Comparison_Operators
ms.openlocfilehash: ea48d5928f71983f6d035f0e5e6074ce36754d80
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "97090506"
---
# <a name="about-comparison-operators"></a><span data-ttu-id="f0b4d-103">關於比較運算子</span><span class="sxs-lookup"><span data-stu-id="f0b4d-103">About Comparison Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="f0b4d-104">簡短描述</span><span class="sxs-lookup"><span data-stu-id="f0b4d-104">Short description</span></span>
<span data-ttu-id="f0b4d-105">描述在 PowerShell 中比較值的運算子。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-105">Describes the operators that compare values in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="f0b4d-106">完整描述</span><span class="sxs-lookup"><span data-stu-id="f0b4d-106">Long description</span></span>

<span data-ttu-id="f0b4d-107">比較運算子可讓您指定比較值的條件，並尋找符合指定模式的值。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-107">Comparison operators let you specify conditions for comparing values and finding values that match specified patterns.</span></span> <span data-ttu-id="f0b4d-108">若要使用比較運算子，請指定要與分隔這些值的運算子一起比較的值。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-108">To use a comparison operator, specify the values that you want to compare together with an operator that separates these values.</span></span>

<span data-ttu-id="f0b4d-109">PowerShell 包含下列比較運算子：</span><span class="sxs-lookup"><span data-stu-id="f0b4d-109">PowerShell includes the following comparison operators:</span></span>

| <span data-ttu-id="f0b4d-110">類型</span><span class="sxs-lookup"><span data-stu-id="f0b4d-110">Type</span></span>        | <span data-ttu-id="f0b4d-111">運算子</span><span class="sxs-lookup"><span data-stu-id="f0b4d-111">Operators</span></span>    | <span data-ttu-id="f0b4d-112">說明</span><span class="sxs-lookup"><span data-stu-id="f0b4d-112">Description</span></span>                                 |
| ----------- | ------------ | --------------------------------------------|
| <span data-ttu-id="f0b4d-113">等式</span><span class="sxs-lookup"><span data-stu-id="f0b4d-113">Equality</span></span>    | <span data-ttu-id="f0b4d-114">-eq</span><span class="sxs-lookup"><span data-stu-id="f0b4d-114">-eq</span></span>          | <span data-ttu-id="f0b4d-115">equals</span><span class="sxs-lookup"><span data-stu-id="f0b4d-115">equals</span></span>                                      |
|             | <span data-ttu-id="f0b4d-116">-ne</span><span class="sxs-lookup"><span data-stu-id="f0b4d-116">-ne</span></span>          | <span data-ttu-id="f0b4d-117">不等於</span><span class="sxs-lookup"><span data-stu-id="f0b4d-117">not equals</span></span>                                  |
|             | <span data-ttu-id="f0b4d-118">-gt</span><span class="sxs-lookup"><span data-stu-id="f0b4d-118">-gt</span></span>          | <span data-ttu-id="f0b4d-119">大於</span><span class="sxs-lookup"><span data-stu-id="f0b4d-119">greater than</span></span>                                |
|             | <span data-ttu-id="f0b4d-120">-ge</span><span class="sxs-lookup"><span data-stu-id="f0b4d-120">-ge</span></span>          | <span data-ttu-id="f0b4d-121">大於或等於</span><span class="sxs-lookup"><span data-stu-id="f0b4d-121">greater than or equal</span></span>                       |
|             | <span data-ttu-id="f0b4d-122">-lt</span><span class="sxs-lookup"><span data-stu-id="f0b4d-122">-lt</span></span>          | <span data-ttu-id="f0b4d-123">小於</span><span class="sxs-lookup"><span data-stu-id="f0b4d-123">less than</span></span>                                   |
|             | <span data-ttu-id="f0b4d-124">-le</span><span class="sxs-lookup"><span data-stu-id="f0b4d-124">-le</span></span>          | <span data-ttu-id="f0b4d-125">小於或等於</span><span class="sxs-lookup"><span data-stu-id="f0b4d-125">less than or equal</span></span>                          |
|             |              |                                             |
| <span data-ttu-id="f0b4d-126">Matching</span><span class="sxs-lookup"><span data-stu-id="f0b4d-126">Matching</span></span>    | <span data-ttu-id="f0b4d-127">-like</span><span class="sxs-lookup"><span data-stu-id="f0b4d-127">-like</span></span>        | <span data-ttu-id="f0b4d-128">當字串符合萬用字元時傳回 true</span><span class="sxs-lookup"><span data-stu-id="f0b4d-128">Returns true when string matches wildcard</span></span>   |
|             |              | <span data-ttu-id="f0b4d-129">模式</span><span class="sxs-lookup"><span data-stu-id="f0b4d-129">pattern</span></span>                                     |
|             | <span data-ttu-id="f0b4d-130">-notlike</span><span class="sxs-lookup"><span data-stu-id="f0b4d-130">-notlike</span></span>     | <span data-ttu-id="f0b4d-131">當字串不相符時傳回 true</span><span class="sxs-lookup"><span data-stu-id="f0b4d-131">Returns true when string does not match</span></span>     |
|             |              | <span data-ttu-id="f0b4d-132">萬用字元模式</span><span class="sxs-lookup"><span data-stu-id="f0b4d-132">wildcard pattern</span></span>                            |
|             | <span data-ttu-id="f0b4d-133">-match</span><span class="sxs-lookup"><span data-stu-id="f0b4d-133">-match</span></span>       | <span data-ttu-id="f0b4d-134">當字串符合 RegEx 時傳回 true</span><span class="sxs-lookup"><span data-stu-id="f0b4d-134">Returns true when string matches regex</span></span>      |
|             |              | <span data-ttu-id="f0b4d-135">方式$matches 包含相符的字串</span><span class="sxs-lookup"><span data-stu-id="f0b4d-135">pattern; $matches contains matching strings</span></span> |
|             | <span data-ttu-id="f0b4d-136">-notmatch</span><span class="sxs-lookup"><span data-stu-id="f0b4d-136">-notmatch</span></span>    | <span data-ttu-id="f0b4d-137">當字串不相符時傳回 true</span><span class="sxs-lookup"><span data-stu-id="f0b4d-137">Returns true when string does not match</span></span>     |
|             |              | <span data-ttu-id="f0b4d-138">RegEx 模式;$matches 包含相符的</span><span class="sxs-lookup"><span data-stu-id="f0b4d-138">regex pattern; $matches contains matching</span></span>   |
|             |              | <span data-ttu-id="f0b4d-139">字串</span><span class="sxs-lookup"><span data-stu-id="f0b4d-139">strings</span></span>                                     |
|             |              |                                             |
| <span data-ttu-id="f0b4d-140">Containment</span><span class="sxs-lookup"><span data-stu-id="f0b4d-140">Containment</span></span> | <span data-ttu-id="f0b4d-141">-contains</span><span class="sxs-lookup"><span data-stu-id="f0b4d-141">-contains</span></span>    | <span data-ttu-id="f0b4d-142">當參考值包含時傳回 true</span><span class="sxs-lookup"><span data-stu-id="f0b4d-142">Returns true when reference value contained</span></span> |
|             |              | <span data-ttu-id="f0b4d-143">在集合中</span><span class="sxs-lookup"><span data-stu-id="f0b4d-143">in a collection</span></span>                             |
|             | <span data-ttu-id="f0b4d-144">-notcontains</span><span class="sxs-lookup"><span data-stu-id="f0b4d-144">-notcontains</span></span> | <span data-ttu-id="f0b4d-145">如果參考值不是，則傳回 true</span><span class="sxs-lookup"><span data-stu-id="f0b4d-145">Returns true when reference value not</span></span>       |
|             |              | <span data-ttu-id="f0b4d-146">包含在集合中</span><span class="sxs-lookup"><span data-stu-id="f0b4d-146">contained in a collection</span></span>                   |
|             | <span data-ttu-id="f0b4d-147">-in</span><span class="sxs-lookup"><span data-stu-id="f0b4d-147">-in</span></span>          | <span data-ttu-id="f0b4d-148">當包含在中的測試值時傳回 true</span><span class="sxs-lookup"><span data-stu-id="f0b4d-148">Returns true when test value contained in a</span></span> |
|             |              | <span data-ttu-id="f0b4d-149">collection</span><span class="sxs-lookup"><span data-stu-id="f0b4d-149">collection</span></span>                                  |
|             | <span data-ttu-id="f0b4d-150">-notin</span><span class="sxs-lookup"><span data-stu-id="f0b4d-150">-notin</span></span>       | <span data-ttu-id="f0b4d-151">當測試值不包含時傳回 true</span><span class="sxs-lookup"><span data-stu-id="f0b4d-151">Returns true when test value not contained</span></span>  |
|             |              | <span data-ttu-id="f0b4d-152">在集合中</span><span class="sxs-lookup"><span data-stu-id="f0b4d-152">in a collection</span></span>                             |
|             |              |                                             |
| <span data-ttu-id="f0b4d-153">取代</span><span class="sxs-lookup"><span data-stu-id="f0b4d-153">Replacement</span></span> | <span data-ttu-id="f0b4d-154">-取代</span><span class="sxs-lookup"><span data-stu-id="f0b4d-154">-replace</span></span>     | <span data-ttu-id="f0b4d-155">取代字串模式</span><span class="sxs-lookup"><span data-stu-id="f0b4d-155">Replaces a string pattern</span></span>                   |
|             |              |                                             |
| <span data-ttu-id="f0b4d-156">類型</span><span class="sxs-lookup"><span data-stu-id="f0b4d-156">Type</span></span>        | <span data-ttu-id="f0b4d-157">-是</span><span class="sxs-lookup"><span data-stu-id="f0b4d-157">-is</span></span>          | <span data-ttu-id="f0b4d-158">如果兩個物件相同，則傳回 true</span><span class="sxs-lookup"><span data-stu-id="f0b4d-158">Returns true if both object are the same</span></span>    |
|             |              | <span data-ttu-id="f0b4d-159">類型</span><span class="sxs-lookup"><span data-stu-id="f0b4d-159">type</span></span>                                        |
|             | <span data-ttu-id="f0b4d-160">-isnot</span><span class="sxs-lookup"><span data-stu-id="f0b4d-160">-isnot</span></span>       | <span data-ttu-id="f0b4d-161">如果物件相同，則傳回 true</span><span class="sxs-lookup"><span data-stu-id="f0b4d-161">Returns true if the objects are not the same</span></span>|
|             |              | <span data-ttu-id="f0b4d-162">類型</span><span class="sxs-lookup"><span data-stu-id="f0b4d-162">type</span></span>                                        |

<span data-ttu-id="f0b4d-163">依預設，所有比較運算子都不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-163">By default, all comparison operators are case-insensitive.</span></span> <span data-ttu-id="f0b4d-164">若要讓比較運算子區分大小寫，請在運算子名稱之前加上 `c` 。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-164">To make a comparison operator case-sensitive, precede the operator name with a `c`.</span></span> <span data-ttu-id="f0b4d-165">例如，區分大小寫的版本 `-eq` 是 `-ceq` 。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-165">For example, the case-sensitive version of `-eq` is `-ceq`.</span></span> <span data-ttu-id="f0b4d-166">若要進行不區分大小寫的明確，請在運算子前面加上 `i` 。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-166">To make the case-insensitivity explicit, precede the operator with an `i`.</span></span> <span data-ttu-id="f0b4d-167">例如，明確的不區分大小寫版本 `-eq` 為 `-ieq` 。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-167">For example, the explicitly case-insensitive version of `-eq` is `-ieq`.</span></span>

<span data-ttu-id="f0b4d-168">當運算子的輸入是純量值時，比較運算子會傳回布林值。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-168">When the input to an operator is a scalar value, comparison operators return a Boolean value.</span></span> <span data-ttu-id="f0b4d-169">當輸入是值的集合時，比較運算子會傳回任何相符的值。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-169">When the input is a collection of values, the comparison operators return any matching values.</span></span> <span data-ttu-id="f0b4d-170">如果集合中沒有相符專案，比較運算子會傳回空陣列。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-170">If there are no matches in a collection, comparison operators return an empty array.</span></span>

```powershell
PS> (1, 2 -eq 3).GetType().FullName
System.Object[]
```

<span data-ttu-id="f0b4d-171">例外狀況是內含專案運算子、In 運算子和型別運算子，這些運算子一律會傳回 **布林** 值。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-171">The exceptions are the containment operators, the In operators, and the type operators, which always return a **Boolean** value.</span></span>

> [!NOTE]
> <span data-ttu-id="f0b4d-172">如果您需要比較值與 `$null` ，應該放 `$null` 在比較的左邊。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-172">If you need to compare a value to `$null` you should put `$null` on the left-hand side of the comparison.</span></span> <span data-ttu-id="f0b4d-173">當您比較 `$null` **物件 []** 時，結果為 **False** ，因為比較物件是陣列。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-173">When you compare `$null` to an **Object[]** the result is **False** because the comparison object is an array.</span></span> <span data-ttu-id="f0b4d-174">當您比較陣列與時 `$null` ，比較會篩選出任何 `$null` 儲存在陣列中的值。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-174">When you compare an array to `$null`, the comparison filters out any `$null` values stored in the array.</span></span> <span data-ttu-id="f0b4d-175">例如：</span><span class="sxs-lookup"><span data-stu-id="f0b4d-175">For example:</span></span>
>
> ```powershell
> PS> $null -ne $null, "hello"
> True
> PS> $null, "hello" -ne $null
> hello
> ```

## <a name="equality-operators"></a><span data-ttu-id="f0b4d-176">等號比較運算子</span><span class="sxs-lookup"><span data-stu-id="f0b4d-176">Equality operators</span></span>

<span data-ttu-id="f0b4d-177">`-eq` `-ne` 當一或多個輸入值相同于指定的模式時，相等運算子 (，) 會傳回 TRUE 或相符專案的值。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-177">The equality operators (`-eq`, `-ne`) return a value of TRUE or the matches when one or more of the input values is identical to the specified pattern.</span></span> <span data-ttu-id="f0b4d-178">整個模式必須符合整個值。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-178">The entire pattern must match an entire value.</span></span>

<span data-ttu-id="f0b4d-179">範例：</span><span class="sxs-lookup"><span data-stu-id="f0b4d-179">Example:</span></span>

### <a name="-eq"></a><span data-ttu-id="f0b4d-180">-eq</span><span class="sxs-lookup"><span data-stu-id="f0b4d-180">-eq</span></span>

<span data-ttu-id="f0b4d-181">描述：等於。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-181">Description: Equal to.</span></span> <span data-ttu-id="f0b4d-182">包含相同的值。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-182">Includes an identical value.</span></span>

<span data-ttu-id="f0b4d-183">範例：</span><span class="sxs-lookup"><span data-stu-id="f0b4d-183">Example:</span></span>

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

### <a name="-ne"></a><span data-ttu-id="f0b4d-184">-ne</span><span class="sxs-lookup"><span data-stu-id="f0b4d-184">-ne</span></span>

<span data-ttu-id="f0b4d-185">描述：不等於。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-185">Description: Not equal to.</span></span> <span data-ttu-id="f0b4d-186">包含不同的值。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-186">Includes a different value.</span></span>

<span data-ttu-id="f0b4d-187">範例：</span><span class="sxs-lookup"><span data-stu-id="f0b4d-187">Example:</span></span>

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

### <a name="-gt"></a><span data-ttu-id="f0b4d-188">-gt</span><span class="sxs-lookup"><span data-stu-id="f0b4d-188">-gt</span></span>

<span data-ttu-id="f0b4d-189">描述：大於。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-189">Description: Greater-than.</span></span>

<span data-ttu-id="f0b4d-190">範例：</span><span class="sxs-lookup"><span data-stu-id="f0b4d-190">Example:</span></span>

```powershell
PS> 8 -gt 6
True

PS> 7, 8, 9 -gt 8
9
```

> [!NOTE]
> <span data-ttu-id="f0b4d-191">這應該不會與 `>` 其他許多程式設計語言中的大於運算子混淆。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-191">This should not to be confused with `>`, the greater-than operator in many other programming languages.</span></span> <span data-ttu-id="f0b4d-192">在 PowerShell 中， `>` 是用來重新導向。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-192">In PowerShell, `>` is used for redirection.</span></span> <span data-ttu-id="f0b4d-193">如需詳細資訊，請參閱 [About_redirection](about_Redirection.md#potential-confusion-with-comparison-operators)。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-193">For more information, see [About_redirection](about_Redirection.md#potential-confusion-with-comparison-operators).</span></span>

### <a name="-ge"></a><span data-ttu-id="f0b4d-194">-ge</span><span class="sxs-lookup"><span data-stu-id="f0b4d-194">-ge</span></span>

<span data-ttu-id="f0b4d-195">描述：大於或等於。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-195">Description: Greater-than or equal to.</span></span>

<span data-ttu-id="f0b4d-196">範例：</span><span class="sxs-lookup"><span data-stu-id="f0b4d-196">Example:</span></span>

```powershell
PS> 8 -ge 8
True

PS> 7, 8, 9 -ge 8
8
9
```

### <a name="-lt"></a><span data-ttu-id="f0b4d-197">-lt</span><span class="sxs-lookup"><span data-stu-id="f0b4d-197">-lt</span></span>

<span data-ttu-id="f0b4d-198">描述：小於。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-198">Description: Less-than.</span></span>

<span data-ttu-id="f0b4d-199">範例：</span><span class="sxs-lookup"><span data-stu-id="f0b4d-199">Example:</span></span>

```powershell

PS> 8 -lt 6
False

PS> 7, 8, 9 -lt 8
7
```

### <a name="-le"></a><span data-ttu-id="f0b4d-200">-le</span><span class="sxs-lookup"><span data-stu-id="f0b4d-200">-le</span></span>

<span data-ttu-id="f0b4d-201">描述：小於或等於。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-201">Description: Less-than or equal to.</span></span>

<span data-ttu-id="f0b4d-202">範例：</span><span class="sxs-lookup"><span data-stu-id="f0b4d-202">Example:</span></span>

```powershell
PS> 6 -le 8
True

PS> 7, 8, 9 -le 8
7
8
```

## <a name="matching-operators"></a><span data-ttu-id="f0b4d-203">相符運算子</span><span class="sxs-lookup"><span data-stu-id="f0b4d-203">Matching operators</span></span>

<span data-ttu-id="f0b4d-204">Like 運算子 (`-like` 和 `-notlike`) 使用萬用字元運算式來尋找符合或不符合指定模式的元素。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-204">The like operators (`-like` and `-notlike`) find elements that match or do not match a specified pattern using wildcard expressions.</span></span>

<span data-ttu-id="f0b4d-205">語法為：</span><span class="sxs-lookup"><span data-stu-id="f0b4d-205">The syntax is:</span></span>

```powershell
<string[]> -like <wildcard-expression>
<string[]> -notlike <wildcard-expression>
```

<span data-ttu-id="f0b4d-206">符合運算子 (`-match` 和 `-notmatch`) 使用正則運算式來尋找符合或不符合指定模式的元素。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-206">The match operators (`-match` and `-notmatch`) find elements that match or do not match a specified pattern using regular expressions.</span></span>

<span data-ttu-id="f0b4d-207">`$Matches`當運算子的左邊引數)  (的輸入是單一純量物件時，比對運算子會填入自動變數。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-207">The match operators populate the `$Matches` automatic variable when the input (the left-side argument) to the operator is a single scalar object.</span></span> <span data-ttu-id="f0b4d-208">當輸入是純量時， `-match` 和 `-notmatch` 運算子會傳回布林值，並將自動變數的值設定 `$Matches` 為引數的相符元件。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-208">When the input is scalar, the `-match` and `-notmatch` operators return a Boolean value and set the value of the `$Matches` automatic variable to the matched components of the argument.</span></span>

<span data-ttu-id="f0b4d-209">語法為：</span><span class="sxs-lookup"><span data-stu-id="f0b4d-209">The syntax is:</span></span>

```powershell
<string[]> -match <regular-expression>
<string[]> -notmatch <regular-expression>
```

### <a name="-like"></a><span data-ttu-id="f0b4d-210">-like</span><span class="sxs-lookup"><span data-stu-id="f0b4d-210">-like</span></span>

<span data-ttu-id="f0b4d-211">描述：使用萬用字元 () 比對 \* 。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-211">Description: Match using the wildcard character (\*).</span></span>

<span data-ttu-id="f0b4d-212">範例：</span><span class="sxs-lookup"><span data-stu-id="f0b4d-212">Example:</span></span>

```powershell
PS> "PowerShell" -like "*shell"
True

PS> "PowerShell", "Server" -like "*shell"
PowerShell
```

### <a name="-notlike"></a><span data-ttu-id="f0b4d-213">-notlike</span><span class="sxs-lookup"><span data-stu-id="f0b4d-213">-notlike</span></span>

<span data-ttu-id="f0b4d-214">描述：不符合使用萬用字元 (\*) 。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-214">Description: Does not match using the wildcard character (\*).</span></span>

<span data-ttu-id="f0b4d-215">範例：</span><span class="sxs-lookup"><span data-stu-id="f0b4d-215">Example:</span></span>

```powershell
PS> "PowerShell" -notlike "*shell"
False

PS> "PowerShell", "Server" -notlike "*shell"
Server
```

### <a name="-match"></a><span data-ttu-id="f0b4d-216">-match</span><span class="sxs-lookup"><span data-stu-id="f0b4d-216">-match</span></span>

<span data-ttu-id="f0b4d-217">描述：使用正則運算式比對字串。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-217">Description: Matches a string using regular expressions.</span></span> <span data-ttu-id="f0b4d-218">當輸入是純量時，會填入 `$Matches` 自動變數。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-218">When the input is scalar, it populates the `$Matches` automatic variable.</span></span>

<span data-ttu-id="f0b4d-219">如果輸入是集合， `-match` 和運算子會傳回 `-notmatch` 該集合的相符成員，但是運算子不會填入 `$Matches` 變數。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-219">If the input is a collection, the `-match` and `-notmatch` operators return the matching members of that collection, but the operator does not populate the `$Matches` variable.</span></span>

<span data-ttu-id="f0b4d-220">例如，下列命令會將字串的集合提交給 `-match` 運算子。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-220">For example, the following command submits a collection of strings to the `-match` operator.</span></span> <span data-ttu-id="f0b4d-221">`-match`運算子會傳回集合中符合的專案。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-221">The `-match` operator returns the items in the collection that match.</span></span> <span data-ttu-id="f0b4d-222">它不會填入 `$Matches` 自動變數。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-222">It does not populate the `$Matches` automatic variable.</span></span>

```powershell
PS> "Sunday", "Monday", "Tuesday" -match "sun"
Sunday

PS> $Matches
PS>
```

<span data-ttu-id="f0b4d-223">相反地，下列命令會將單一字串提交給 `-match` 運算子。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-223">In contrast, the following command submits a single string to the `-match` operator.</span></span> <span data-ttu-id="f0b4d-224">運算子會傳回 `-match` 布林值，並填入 `$Matches` 自動變數。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-224">The `-match` operator returns a Boolean value and populates the `$Matches` automatic variable.</span></span> <span data-ttu-id="f0b4d-225">`$Matches`自動變數是 **雜湊表**。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-225">The `$Matches` automatic variable is a **Hashtable**.</span></span> <span data-ttu-id="f0b4d-226">如果未使用群組或捕捉，則只會填入一個金鑰。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-226">If no grouping or capturing is used, only one key is populated.</span></span>
<span data-ttu-id="f0b4d-227">機 `0` 碼代表所有相符的文字。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-227">The `0` key represents all text that was matched.</span></span> <span data-ttu-id="f0b4d-228">如需使用正則運算式進行群組和捕捉的詳細資訊，請參閱 [about_Regular_Expressions](about_Regular_Expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-228">For more information about grouping and capturing using regular expressions, see [about_Regular_Expressions](about_Regular_Expressions.md).</span></span>

```powershell
PS> "Sunday" -match "sun"
True

PS> $Matches

Name                           Value
----                           -----
0                              Sun
```

<span data-ttu-id="f0b4d-229">請務必注意， `$Matches` 雜湊表只會包含第一次出現的任何相符模式。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-229">It is important to note that the `$Matches` hashtable will only contain the first occurrence of any matching pattern.</span></span>

```powershell
PS> "Banana" -match "na"
True

PS> $Matches

Name                           Value
----                           -----
0                              na
```

> [!IMPORTANT]
> <span data-ttu-id="f0b4d-230">索引 `0` 鍵是 **整數**。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-230">The `0` key is an **Integer**.</span></span> <span data-ttu-id="f0b4d-231">您可以使用任何 **Hashtable** 方法來存取儲存的值。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-231">You can use any **Hashtable** method to access the value stored.</span></span>
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

<span data-ttu-id="f0b4d-232">`-notmatch`當輸入是純量時，運算子會填入 `$Matches` 自動變數，而當它偵測到相符時，結果會是 False。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-232">The `-notmatch` operator populates the `$Matches` automatic variable when the input is scalar and the result is False, that it, when it detects a match.</span></span>

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

### <a name="-notmatch"></a><span data-ttu-id="f0b4d-233">-notmatch</span><span class="sxs-lookup"><span data-stu-id="f0b4d-233">-notmatch</span></span>

<span data-ttu-id="f0b4d-234">描述：不符合字串。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-234">Description: Does not match a string.</span></span> <span data-ttu-id="f0b4d-235">使用正則運算式。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-235">Uses regular expressions.</span></span> <span data-ttu-id="f0b4d-236">當輸入是純量時，會填入 `$Matches` 自動變數。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-236">When the input is scalar, it populates the `$Matches` automatic variable.</span></span>

<span data-ttu-id="f0b4d-237">範例：</span><span class="sxs-lookup"><span data-stu-id="f0b4d-237">Example:</span></span>

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

## <a name="containment-operators"></a><span data-ttu-id="f0b4d-238">內含專案運算子</span><span class="sxs-lookup"><span data-stu-id="f0b4d-238">Containment operators</span></span>

<span data-ttu-id="f0b4d-239">內含專案運算子 (`-contains` 和 `-notcontains`) 類似于等號比較運算子。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-239">The containment operators (`-contains` and `-notcontains`) are similar to the equality operators.</span></span> <span data-ttu-id="f0b4d-240">不過，內含專案運算子一律會傳回布林值，即使輸入是集合也一樣。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-240">However, the containment operators always return a Boolean value, even when the input is a collection.</span></span>

<span data-ttu-id="f0b4d-241">此外，和等號比較運算子不同的是，內含專案運算子會在偵測到第一個相符專案時，立即傳回值。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-241">Also, unlike the equality operators, the containment operators return a value as soon as they detect the first match.</span></span> <span data-ttu-id="f0b4d-242">等號比較運算子會評估所有輸入，然後傳回集合中的所有相符專案。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-242">The equality operators evaluate all input and then return all the matches in the collection.</span></span>

### <a name="-contains"></a><span data-ttu-id="f0b4d-243">-contains</span><span class="sxs-lookup"><span data-stu-id="f0b4d-243">-contains</span></span>

<span data-ttu-id="f0b4d-244">描述：內含專案運算子。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-244">Description: Containment operator.</span></span> <span data-ttu-id="f0b4d-245">指出參考值的集合是否包含單一測試值。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-245">Tells whether a collection of reference values includes a single test value.</span></span> <span data-ttu-id="f0b4d-246">一律傳回布林值。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-246">Always returns a Boolean value.</span></span> <span data-ttu-id="f0b4d-247">只有當測試值完全符合至少一個參考值時，才會傳回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-247">Returns TRUE only when the test value exactly matches at least one of the reference values.</span></span>

<span data-ttu-id="f0b4d-248">當測試值為集合時，Contains 運算子會使用參考相等。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-248">When the test value is a collection, the Contains operator uses reference equality.</span></span> <span data-ttu-id="f0b4d-249">只有當其中一個參考值是測試值物件的相同實例時，才會傳回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-249">It returns TRUE only when one of the reference values is the same instance of the test value object.</span></span>

<span data-ttu-id="f0b4d-250">在非常大的集合中， `-contains` 運算子會傳回比等於運算子更快的結果。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-250">In a very large collection, the `-contains` operator returns results quicker than the equal to operator.</span></span>

<span data-ttu-id="f0b4d-251">語法：</span><span class="sxs-lookup"><span data-stu-id="f0b4d-251">Syntax:</span></span>

`<Reference-values> -contains <Test-value>`

<span data-ttu-id="f0b4d-252">範例：</span><span class="sxs-lookup"><span data-stu-id="f0b4d-252">Examples:</span></span>

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

### <a name="-notcontains"></a><span data-ttu-id="f0b4d-253">-notcontains</span><span class="sxs-lookup"><span data-stu-id="f0b4d-253">-notcontains</span></span>

<span data-ttu-id="f0b4d-254">描述：內含專案運算子。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-254">Description: Containment operator.</span></span> <span data-ttu-id="f0b4d-255">指出參考值的集合是否包含單一測試值。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-255">Tells whether a collection of reference values includes a single test value.</span></span> <span data-ttu-id="f0b4d-256">一律傳回布林值。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-256">Always returns a Boolean value.</span></span> <span data-ttu-id="f0b4d-257">當測試值與至少一個參考值的完全相符時，就會傳回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-257">Returns TRUE when the test value is not an exact matches for at least one of the reference values.</span></span>

<span data-ttu-id="f0b4d-258">當測試值為集合時，NotContains 運算子會使用參考相等。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-258">When the test value is a collection, the NotContains operator uses reference equality.</span></span>

<span data-ttu-id="f0b4d-259">語法：</span><span class="sxs-lookup"><span data-stu-id="f0b4d-259">Syntax:</span></span>

`<Reference-values> -notcontains <Test-value>`

<span data-ttu-id="f0b4d-260">範例：</span><span class="sxs-lookup"><span data-stu-id="f0b4d-260">Examples:</span></span>

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

### <a name="-in"></a><span data-ttu-id="f0b4d-261">-in</span><span class="sxs-lookup"><span data-stu-id="f0b4d-261">-in</span></span>

<span data-ttu-id="f0b4d-262">描述： In 運算子。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-262">Description: In operator.</span></span> <span data-ttu-id="f0b4d-263">告知測試值是否出現在參考值的集合中。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-263">Tells whether a test value appears in a collection of reference values.</span></span> <span data-ttu-id="f0b4d-264">一律傳回為布林值。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-264">Always return as Boolean value.</span></span> <span data-ttu-id="f0b4d-265">只有當測試值完全符合至少一個參考值時，才會傳回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-265">Returns TRUE only when the test value exactly matches at least one of the reference values.</span></span>

<span data-ttu-id="f0b4d-266">當測試值為集合時，In 運算子會使用參考相等。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-266">When the test value is a collection, the In operator uses reference equality.</span></span>
<span data-ttu-id="f0b4d-267">只有當其中一個參考值是測試值物件的相同實例時，才會傳回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-267">It returns TRUE only when one of the reference values is the same instance of the test value object.</span></span>

<span data-ttu-id="f0b4d-268">`-in`操作員是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-268">The `-in` operator was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="f0b4d-269">語法：</span><span class="sxs-lookup"><span data-stu-id="f0b4d-269">Syntax:</span></span>

`<Test-value> -in <Reference-values>`

<span data-ttu-id="f0b4d-270">範例：</span><span class="sxs-lookup"><span data-stu-id="f0b4d-270">Examples:</span></span>

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

### <a name="-notin"></a><span data-ttu-id="f0b4d-271">-notin</span><span class="sxs-lookup"><span data-stu-id="f0b4d-271">-notin</span></span>

<span data-ttu-id="f0b4d-272">描述：告知測試值是否出現在參考值的集合中。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-272">Description: Tells whether a test value appears in a collection of reference values.</span></span> <span data-ttu-id="f0b4d-273">一律傳回布林值。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-273">Always returns a Boolean value.</span></span> <span data-ttu-id="f0b4d-274">當測試值與至少一個參考值完全相符時，就會傳回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-274">Returns TRUE when the test value is not an exact match for at least one of the reference values.</span></span>

<span data-ttu-id="f0b4d-275">當測試值為集合時，In 運算子會使用參考相等。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-275">When the test value is a collection, the In operator uses reference equality.</span></span>
<span data-ttu-id="f0b4d-276">只有當其中一個參考值是測試值物件的相同實例時，才會傳回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-276">It returns TRUE only when one of the reference values is the same instance of the test value object.</span></span>

<span data-ttu-id="f0b4d-277">`-notin`操作員是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-277">The `-notin` operator was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="f0b4d-278">語法：</span><span class="sxs-lookup"><span data-stu-id="f0b4d-278">Syntax:</span></span>

`<Test-value> -notin <Reference-values>`

<span data-ttu-id="f0b4d-279">範例：</span><span class="sxs-lookup"><span data-stu-id="f0b4d-279">Examples:</span></span>

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

## <a name="replacement-operator"></a><span data-ttu-id="f0b4d-280">取代運算子</span><span class="sxs-lookup"><span data-stu-id="f0b4d-280">Replacement Operator</span></span>

<span data-ttu-id="f0b4d-281">`-replace`運算子具有下列語法：</span><span class="sxs-lookup"><span data-stu-id="f0b4d-281">The `-replace` operator has the following syntax:</span></span>

`<input> -replace <original>, <substitute>`

<span data-ttu-id="f0b4d-282">`<original>`預留位置是符合要取代之字元的正則運算式。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-282">The `<original>` placeholder is a regular expression matching the characters to be replaced.</span></span> <span data-ttu-id="f0b4d-283">`<substitute>`預留位置是取代它們的常值字串。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-283">The `<substitute>` placeholder is a literal string that replaces them.</span></span>

<span data-ttu-id="f0b4d-284">運算子會使用正則運算式來取代具有指定值的所有或部分值。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-284">The operator replaces all or part of a value with the specified value using regular expressions.</span></span> <span data-ttu-id="f0b4d-285">您可以使用運算子進行許多系統管理工作，例如重新命名檔案。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-285">You can use the operator for many administrative tasks, such as renaming files.</span></span> <span data-ttu-id="f0b4d-286">例如，下列命令會將所有檔案的副檔名變更 `.txt` 為 `.log` ：</span><span class="sxs-lookup"><span data-stu-id="f0b4d-286">For example, the following command changes the file name extensions of all `.txt` files to `.log`:</span></span>

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.name -replace '\.txt$','.log' }
```

### <a name="case-sensitive-matches"></a><span data-ttu-id="f0b4d-287">區分大小寫的相符專案</span><span class="sxs-lookup"><span data-stu-id="f0b4d-287">Case-sensitive matches</span></span>

<span data-ttu-id="f0b4d-288">依預設， `-replace` 運算子不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-288">By default, the `-replace` operator is case-insensitive.</span></span> <span data-ttu-id="f0b4d-289">若要區分大小寫，請使用 `-creplace` 。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-289">To make it case sensitive, use `-creplace`.</span></span> <span data-ttu-id="f0b4d-290">若要讓它明確不區分大小寫，請使用 `-ireplace` 。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-290">To make it explicitly case-insensitive, use `-ireplace`.</span></span>

<span data-ttu-id="f0b4d-291">請參考下列範例：</span><span class="sxs-lookup"><span data-stu-id="f0b4d-291">Consider the following examples:</span></span>

```powershell
PS> "book" -replace "B", "C"
Cook
```

```powershell
PS> "book" -ireplace "B", "C"
Cook
```

```powershell
PS> "book" -creplace "B", "C"
book
```

### <a name="substitutions-in-regular-expressions"></a><span data-ttu-id="f0b4d-292">規則運算式中的替代項目</span><span class="sxs-lookup"><span data-stu-id="f0b4d-292">Substitutions in regular expressions</span></span>

<span data-ttu-id="f0b4d-293">您也可以使用正則運算式，以動態方式使用捕捉群組和替代來取代文字。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-293">It is also possible to use regular expressions to dynamically replace text using capturing groups, and substitutions.</span></span> <span data-ttu-id="f0b4d-294">您可以 `<substitute>` 使用群組識別碼之前的貨幣符號 () 字元，在字串中參考 Capture 群組 `$` 。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-294">Capture groups can be referenced in the `<substitute>` string using the dollar sign (`$`) character before the group identifier.</span></span>

<span data-ttu-id="f0b4d-295">您可以依 **編號** 或 **名稱** 參考 Capture 群組</span><span class="sxs-lookup"><span data-stu-id="f0b4d-295">Capture groups can be referenced by **Number** or **Name**</span></span>

- <span data-ttu-id="f0b4d-296">依 **編號** -捕獲群組是由左至右編號。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-296">By **Number** - Capturing Groups are numbered from left to right.</span></span>

  ```powershell
  PS> "John D. Smith" -replace "(\w+) (\w+)\. (\w+)", '$1.$2.$3@contoso.com'
  John.D.Smith@contoso.com
  ```

- <span data-ttu-id="f0b4d-297">依 **名稱-捕獲** 群組也可以依名稱參考。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-297">By **Name** - Capturing Groups can also be referenced by name.</span></span>

  ```powershell
  PS> "CONTOSO\Administrator" -replace '\w+\\(?<user>\w+)', 'FABRIKAM\${user}'
  FABRIKAM\Administrator
  ```

> [!WARNING]
> <span data-ttu-id="f0b4d-298">由於 `$` 字元是在字串展開中使用，因此您必須使用常值字串或將 `$` 字元換用。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-298">Since the `$` character is used in string expansion, you will must use literal strings or escape the `$` character.</span></span>
>
> ```powershell
> PS> 'Hello World' -replace '(\w+) \w+', "`$1 Universe"
> Hello Universe
> ```
>
> <span data-ttu-id="f0b4d-299">此外，因為在 `$` 替代中使用字元，所以您必須將字串中的任何實例都換用。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-299">Additionally, since the `$` character is used in substitution, you must escape any instances in your string.</span></span>
>
> ```powershell
> PS> '5.72' -replace '(.+)', '$$$1'
> $5.72
> ```

<span data-ttu-id="f0b4d-300">若要深入瞭解，請參閱[正則運算式中的](/dotnet/standard/base-types/substitutions-in-regular-expressions) [about_Regular_Expressions](about_Regular_Expressions.md)和替代</span><span class="sxs-lookup"><span data-stu-id="f0b4d-300">To learn more see [about_Regular_Expressions](about_Regular_Expressions.md) and [Substitutions in Regular Expressions](/dotnet/standard/base-types/substitutions-in-regular-expressions)</span></span>

### <a name="substituting-in-a-collection"></a><span data-ttu-id="f0b4d-301">以集合取代</span><span class="sxs-lookup"><span data-stu-id="f0b4d-301">Substituting in a collection</span></span>

<span data-ttu-id="f0b4d-302">當 `<input>` `-replace` 運算子為集合時，PowerShell 會將取代套用至集合中的每個值。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-302">When the `<input>` to the `-replace` operator is a collection, PowerShell applies the replacement to every value in the collection.</span></span> <span data-ttu-id="f0b4d-303">例如：</span><span class="sxs-lookup"><span data-stu-id="f0b4d-303">For example:</span></span>

```powershell
"B1","B2","B3","B4","B5" -replace "B", 'a'
a1
a2
a3
a4
a5
```

### <a name="scriptblock-substitutions"></a><span data-ttu-id="f0b4d-304">ScriptBlock 替代</span><span class="sxs-lookup"><span data-stu-id="f0b4d-304">ScriptBlock substitutions</span></span>

<span data-ttu-id="f0b4d-305">從 PowerShell 6 開始，您可以使用 **ScriptBlock** 引數做為 _替代_ 文字。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-305">Beginning in PowerShell 6, you can use a **ScriptBlock** argument for the _Substitution_ text.</span></span> <span data-ttu-id="f0b4d-306">在 _輸入_ 字串中找到的每個相符項都會執行 **ScriptBlock** 。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-306">The **ScriptBlock** will execute for each match found in the _input_ string.</span></span>

<span data-ttu-id="f0b4d-307">在 **ScriptBlock** 內，使用 `$_` 自動變數來參考目前的 **>system.text.regularexpressions 相符** 物件。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-307">Within the **ScriptBlock**, use the `$_` automatic variable to refer to the current **System.Text.RegularExpressions.Match** object.</span></span> <span data-ttu-id="f0b4d-308">**Match** 物件可讓您存取目前所要取代的輸入文字，以及其他有用的資訊。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-308">The **Match** object gives you access to the current input text being replaced, as well as other useful information.</span></span>

<span data-ttu-id="f0b4d-309">此範例會以對等字元取代三個小數點的每個序列。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-309">This example replaces each sequence of three decimals with the character equivalent.</span></span> <span data-ttu-id="f0b4d-310">每一組需要取代的三個小數位數都會執行 **ScriptBlock** 。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-310">The **ScriptBlock** is run for each set of three decimals that needs to be replaced.</span></span>

```powershell
PS> "072101108108111" -replace "\d{3}", {[char][int]$_.Value}
Hello
```

## <a name="type-comparison"></a><span data-ttu-id="f0b4d-311">類型比較</span><span class="sxs-lookup"><span data-stu-id="f0b4d-311">Type comparison</span></span>

<span data-ttu-id="f0b4d-312">類型比較運算子 (`-is` 和 `-isnot`) 用來判斷物件是否為特定類型。</span><span class="sxs-lookup"><span data-stu-id="f0b4d-312">The type comparison operators (`-is` and `-isnot`) are used to determine if an object is a specific type.</span></span>

### <a name="-is"></a><span data-ttu-id="f0b4d-313">-是</span><span class="sxs-lookup"><span data-stu-id="f0b4d-313">-is</span></span>

<span data-ttu-id="f0b4d-314">語法：</span><span class="sxs-lookup"><span data-stu-id="f0b4d-314">Syntax:</span></span>

`<object> -is <type reference>`

<span data-ttu-id="f0b4d-315">範例：</span><span class="sxs-lookup"><span data-stu-id="f0b4d-315">Example:</span></span>

```powershell
PS> $a = 1
PS> $b = "1"
PS> $a -is [int]
True
PS> $a -is $b.GetType()
False
```

### <a name="-isnot"></a><span data-ttu-id="f0b4d-316">-isnot</span><span class="sxs-lookup"><span data-stu-id="f0b4d-316">-isnot</span></span>

<span data-ttu-id="f0b4d-317">語法：</span><span class="sxs-lookup"><span data-stu-id="f0b4d-317">Syntax:</span></span>

`<object> -isnot <type reference>`

<span data-ttu-id="f0b4d-318">範例：</span><span class="sxs-lookup"><span data-stu-id="f0b4d-318">Example:</span></span>

```powershell
PS> $a = 1
PS> $b = "1"
PS> $a -isnot $b.GetType()
True
PS> $b -isnot [int]
True
```

## <a name="see-also"></a><span data-ttu-id="f0b4d-319">請參閱</span><span class="sxs-lookup"><span data-stu-id="f0b4d-319">See also</span></span>

- [<span data-ttu-id="f0b4d-320">about_Operators</span><span class="sxs-lookup"><span data-stu-id="f0b4d-320">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="f0b4d-321">about_Regular_Expressions</span><span class="sxs-lookup"><span data-stu-id="f0b4d-321">about_Regular_Expressions</span></span>](about_Regular_Expressions.md)
- [<span data-ttu-id="f0b4d-322">about_Wildcards</span><span class="sxs-lookup"><span data-stu-id="f0b4d-322">about_Wildcards</span></span>](about_Wildcards.md)
- [<span data-ttu-id="f0b4d-323">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="f0b4d-323">Compare-Object</span></span>](xref:Microsoft.PowerShell.Utility.Compare-Object)
- [<span data-ttu-id="f0b4d-324">Foreach-Object</span><span class="sxs-lookup"><span data-stu-id="f0b4d-324">Foreach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)
- [<span data-ttu-id="f0b4d-325">Where-Object</span><span class="sxs-lookup"><span data-stu-id="f0b4d-325">Where-Object</span></span>](xref:Microsoft.PowerShell.Core.Where-Object)
