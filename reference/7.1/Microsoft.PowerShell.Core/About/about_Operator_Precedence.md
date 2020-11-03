---
description: 依優先順序列出 PowerShell 操作員。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_operator_precedence?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Operator_Precedence
ms.openlocfilehash: d8b0b3f339739186825b5cb041adba5e06e5d702
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207756"
---
# <a name="about-operator-precedence"></a><span data-ttu-id="2ad46-104">關於運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="2ad46-104">About Operator Precedence</span></span>

## <a name="short-description"></a><span data-ttu-id="2ad46-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="2ad46-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="2ad46-106">依優先順序列出 PowerShell 操作員。</span><span class="sxs-lookup"><span data-stu-id="2ad46-106">Lists the PowerShell operators in precedence order.</span></span>

## <a name="long-description"></a><span data-ttu-id="2ad46-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="2ad46-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="2ad46-108">PowerShell 操作員可讓您建立簡單但功能強大的運算式。</span><span class="sxs-lookup"><span data-stu-id="2ad46-108">PowerShell operators let you construct simple, but powerful expressions.</span></span> <span data-ttu-id="2ad46-109">本主題依優先順序列出操作員。</span><span class="sxs-lookup"><span data-stu-id="2ad46-109">This topic lists the operators in precedence order.</span></span> <span data-ttu-id="2ad46-110">優先順序是在相同的運算式中出現多個運算子時，PowerShell 評估運算子的順序。</span><span class="sxs-lookup"><span data-stu-id="2ad46-110">Precedence order is the order in which PowerShell evaluates the operators when multiple operators appear in the same expression.</span></span>

<span data-ttu-id="2ad46-111">當運算子的優先順序相等時，PowerShell 會在運算式中出現時，從左至右進行評估。</span><span class="sxs-lookup"><span data-stu-id="2ad46-111">When operators have equal precedence, PowerShell evaluates them from left to right as they appear within the expression.</span></span> <span data-ttu-id="2ad46-112">例外狀況是指派運算子、轉換運算子和負運算子 (`!` 、 `-not` `-bnot`) ，由右至左進行評估。</span><span class="sxs-lookup"><span data-stu-id="2ad46-112">The exceptions are the assignment operators, the cast operators, and the negation operators (`!`, `-not`, `-bnot`), which are evaluated from right to left.</span></span>

<span data-ttu-id="2ad46-113">您可以使用磁片磁碟機（例如括弧）來覆寫標準優先順序，並強制 PowerShell 在 unenclosed 部分之前評估運算式的封閉部分。</span><span class="sxs-lookup"><span data-stu-id="2ad46-113">You can use enclosures, such as parentheses, to override the standard precedence order and force PowerShell to evaluate the enclosed part of an expression before an unenclosed part.</span></span>

<span data-ttu-id="2ad46-114">在下列清單中，運算子會依照其評估的順序列出。</span><span class="sxs-lookup"><span data-stu-id="2ad46-114">In the following list, operators are listed in the order that they are evaluated.</span></span> <span data-ttu-id="2ad46-115">相同行或相同群組中的運算子具有相等的優先順序。</span><span class="sxs-lookup"><span data-stu-id="2ad46-115">Operators on the same line, or in the same group, have equal precedence.</span></span>

<span data-ttu-id="2ad46-116">[運算子] 資料行列出操作員。</span><span class="sxs-lookup"><span data-stu-id="2ad46-116">The Operator column lists the operators.</span></span> <span data-ttu-id="2ad46-117">參考資料行會列出描述運算子的 PowerShell 說明主題。</span><span class="sxs-lookup"><span data-stu-id="2ad46-117">The Reference column lists the PowerShell Help topic in which the operator is described.</span></span> <span data-ttu-id="2ad46-118">若要顯示主題，請輸入 `get-help <topic-name>` 。</span><span class="sxs-lookup"><span data-stu-id="2ad46-118">To display the topic, type `get-help <topic-name>`.</span></span>

|         <span data-ttu-id="2ad46-119">OPERATOR</span><span class="sxs-lookup"><span data-stu-id="2ad46-119">OPERATOR</span></span>         |           <span data-ttu-id="2ad46-120">參考</span><span class="sxs-lookup"><span data-stu-id="2ad46-120">REFERENCE</span></span>            |
| ------------------------ | ------------------------------ |
| `$() @() ()`             | <span data-ttu-id="2ad46-121">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-121">[about_Operators][]</span></span>            |
| <span data-ttu-id="2ad46-122">`. ?.` (成員存取) </span><span class="sxs-lookup"><span data-stu-id="2ad46-122">`. ?.` (member access)</span></span>   | <span data-ttu-id="2ad46-123">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-123">[about_Operators][]</span></span>            |
| <span data-ttu-id="2ad46-124">`::` (靜態) </span><span class="sxs-lookup"><span data-stu-id="2ad46-124">`::` (static)</span></span>            | <span data-ttu-id="2ad46-125">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-125">[about_Operators][]</span></span>            |
| <span data-ttu-id="2ad46-126">`[0] ?[0]` (索引運算子) </span><span class="sxs-lookup"><span data-stu-id="2ad46-126">`[0] ?[0]` (index operator)</span></span> | <span data-ttu-id="2ad46-127">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-127">[about_Operators][]</span></span>         |
| <span data-ttu-id="2ad46-128">`[int]` (轉換運算子) </span><span class="sxs-lookup"><span data-stu-id="2ad46-128">`[int]` (cast operators)</span></span> | <span data-ttu-id="2ad46-129">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-129">[about_Operators][]</span></span>            |
| <span data-ttu-id="2ad46-130">`-split` (一元) </span><span class="sxs-lookup"><span data-stu-id="2ad46-130">`-split` (unary)</span></span>         | <span data-ttu-id="2ad46-131">[about_Split][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-131">[about_Split][]</span></span>                |
| <span data-ttu-id="2ad46-132">`-join` (一元) </span><span class="sxs-lookup"><span data-stu-id="2ad46-132">`-join` (unary)</span></span>          | <span data-ttu-id="2ad46-133">[about_Join][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-133">[about_Join][]</span></span>                 |
| <span data-ttu-id="2ad46-134">`,` (逗號運算子) </span><span class="sxs-lookup"><span data-stu-id="2ad46-134">`,` (comma operator)</span></span>     | <span data-ttu-id="2ad46-135">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-135">[about_Operators][]</span></span>            |
| `++ --`                  | <span data-ttu-id="2ad46-136">[about_Assignment_Operators][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-136">[about_Assignment_Operators][]</span></span> |
| `! -not`                 | <span data-ttu-id="2ad46-137">[about_Logical_Operators][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-137">[about_Logical_Operators][]</span></span>    |
| <span data-ttu-id="2ad46-138">`..` (範圍運算子) </span><span class="sxs-lookup"><span data-stu-id="2ad46-138">`..` (range operator)</span></span>    | <span data-ttu-id="2ad46-139">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-139">[about_Operators][]</span></span>            |
| <span data-ttu-id="2ad46-140">`-f` (格式運算子) </span><span class="sxs-lookup"><span data-stu-id="2ad46-140">`-f` (format operator)</span></span>   | <span data-ttu-id="2ad46-141">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-141">[about_Operators][]</span></span>            |
| <span data-ttu-id="2ad46-142">`-` (一元/負) </span><span class="sxs-lookup"><span data-stu-id="2ad46-142">`-` (unary/negative)</span></span>     | <span data-ttu-id="2ad46-143">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-143">[about_Arithmetic_Operators][]</span></span> |
| `* / %`                  | <span data-ttu-id="2ad46-144">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-144">[about_Arithmetic_Operators][]</span></span> |
| `+ -`                    | <span data-ttu-id="2ad46-145">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-145">[about_Arithmetic_Operators][]</span></span> |

<span data-ttu-id="2ad46-146">下列運算子群組具有相同的優先順序。</span><span class="sxs-lookup"><span data-stu-id="2ad46-146">The following group of operators have equal precedence.</span></span> <span data-ttu-id="2ad46-147">其區分大小寫且明確區分大小寫的變數具有相同的優先順序。</span><span class="sxs-lookup"><span data-stu-id="2ad46-147">Their case-sensitive and explicitly case-insensitive variants have the same precedence.</span></span>

|         <span data-ttu-id="2ad46-148">OPERATOR</span><span class="sxs-lookup"><span data-stu-id="2ad46-148">OPERATOR</span></span>          |           <span data-ttu-id="2ad46-149">參考</span><span class="sxs-lookup"><span data-stu-id="2ad46-149">REFERENCE</span></span>            |
| ------------------------- | ------------------------------ |
| <span data-ttu-id="2ad46-150">`-split` (二進位) </span><span class="sxs-lookup"><span data-stu-id="2ad46-150">`-split` (binary)</span></span>         | <span data-ttu-id="2ad46-151">[about_Split][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-151">[about_Split][]</span></span>                |
| <span data-ttu-id="2ad46-152">`-join` (二進位) </span><span class="sxs-lookup"><span data-stu-id="2ad46-152">`-join` (binary)</span></span>          | <span data-ttu-id="2ad46-153">[about_Join][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-153">[about_Join][]</span></span>                 |
| `-is -isnot -as`          | <span data-ttu-id="2ad46-154">[about_Type_Operators][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-154">[about_Type_Operators][]</span></span>       |
| `-eq -ne -gt -gt -lt -le` | <span data-ttu-id="2ad46-155">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-155">[about_Comparison_Operators][]</span></span> |
| `-like -notlike`          | <span data-ttu-id="2ad46-156">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-156">[about_Comparison_Operators][]</span></span> |
| `-match -notmatch`        | <span data-ttu-id="2ad46-157">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-157">[about_Comparison_Operators][]</span></span> |
| `-in -notIn`              | <span data-ttu-id="2ad46-158">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-158">[about_Comparison_Operators][]</span></span> |
| `-contains -notContains`  | <span data-ttu-id="2ad46-159">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-159">[about_Comparison_Operators][]</span></span> |
| `-replace`                | <span data-ttu-id="2ad46-160">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-160">[about_Comparison_Operators][]</span></span> |

<span data-ttu-id="2ad46-161">清單會依下列順序在這裡繼續：</span><span class="sxs-lookup"><span data-stu-id="2ad46-161">The list resumes here with the following operators in precedence order:</span></span>

|                <span data-ttu-id="2ad46-162">OPERATOR</span><span class="sxs-lookup"><span data-stu-id="2ad46-162">OPERATOR</span></span>                 |           <span data-ttu-id="2ad46-163">參考</span><span class="sxs-lookup"><span data-stu-id="2ad46-163">REFERENCE</span></span>            |
| --------------------------------------- | ------------------------------ |
| `-band -bnot -bor -bxor -shr -shl`      | <span data-ttu-id="2ad46-164">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-164">[about_Arithmetic_Operators][]</span></span> |
| `-and -or -xor`                         | <span data-ttu-id="2ad46-165">[about_Logical_Operators][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-165">[about_Logical_Operators][]</span></span>    |

<span data-ttu-id="2ad46-166">下列專案不是 true 運算子。</span><span class="sxs-lookup"><span data-stu-id="2ad46-166">The following items are not true operators.</span></span> <span data-ttu-id="2ad46-167">它們是 PowerShell 命令語法的一部分，而不是運算式語法的一部分。</span><span class="sxs-lookup"><span data-stu-id="2ad46-167">They are part of PowerShell's command syntax, not expression syntax.</span></span> <span data-ttu-id="2ad46-168">指派一律會是最後一個執行的動作。</span><span class="sxs-lookup"><span data-stu-id="2ad46-168">Assignment is always the last action that happens.</span></span>

|                <span data-ttu-id="2ad46-169">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2ad46-169">SYNTAX</span></span>                   |           <span data-ttu-id="2ad46-170">參考</span><span class="sxs-lookup"><span data-stu-id="2ad46-170">REFERENCE</span></span>            |
| --------------------------------------- | ------------------------------ |
| <span data-ttu-id="2ad46-171">`.` (點-來源) </span><span class="sxs-lookup"><span data-stu-id="2ad46-171">`.` (dot-source)</span></span>                        | <span data-ttu-id="2ad46-172">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-172">[about_Operators][]</span></span>            |
| <span data-ttu-id="2ad46-173">`&` (呼叫) </span><span class="sxs-lookup"><span data-stu-id="2ad46-173">`&` (call)</span></span>                              | <span data-ttu-id="2ad46-174">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-174">[about_Operators][]</span></span>            |
| <span data-ttu-id="2ad46-175">`? <if-true> : <if-false>` (三元運算子) </span><span class="sxs-lookup"><span data-stu-id="2ad46-175">`? <if-true> : <if-false>` (Ternary operator)</span></span> | <span data-ttu-id="2ad46-176">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-176">[about_Operators][]</span></span>      |
| <span data-ttu-id="2ad46-177">`??` (null coalese 運算子) </span><span class="sxs-lookup"><span data-stu-id="2ad46-177">`??` (null-coalese operator)</span></span>            | <span data-ttu-id="2ad46-178">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-178">[about_Operators][]</span></span>            |
| <span data-ttu-id="2ad46-179"><code>&#124;</code> (管線運算子) </span><span class="sxs-lookup"><span data-stu-id="2ad46-179"><code>&#124;</code> (pipeline operator)</span></span> | <span data-ttu-id="2ad46-180">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-180">[about_Operators][]</span></span>            |
| `> >> 2> 2>> 2>&1`                      | <span data-ttu-id="2ad46-181">[about_Redirection][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-181">[about_Redirection][]</span></span>          |
| <span data-ttu-id="2ad46-182"><code>&& &#124;&#124;</code> (管線鏈運算子) </span><span class="sxs-lookup"><span data-stu-id="2ad46-182"><code>&& &#124;&#124;</code> (pipeline chain operators)</span></span> | <span data-ttu-id="2ad46-183">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-183">[about_Operators][]</span></span> |
| `= += -= *= /= %= ??=`                  | <span data-ttu-id="2ad46-184">[about_Assignment_Operators][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-184">[about_Assignment_Operators][]</span></span> |

## <a name="examples"></a><span data-ttu-id="2ad46-185">範例</span><span class="sxs-lookup"><span data-stu-id="2ad46-185">EXAMPLES</span></span>

<span data-ttu-id="2ad46-186">下列兩個命令顯示算術運算子，以及使用括弧強制 PowerShell 先評估運算式的封閉部分的效果。</span><span class="sxs-lookup"><span data-stu-id="2ad46-186">The following two commands show the arithmetic operators and the effect of using parentheses to force PowerShell to evaluate the enclosed part of the expression first.</span></span>

```powershell
PS> 2 + 3 * 4
14

PS> (2 + 3) * 4
20
```

<span data-ttu-id="2ad46-187">下列範例會從本機目錄取得唯讀文字檔，並將它們儲存在 `$read_only` 變數中。</span><span class="sxs-lookup"><span data-stu-id="2ad46-187">The following example gets the read-only text files from the local directory and saves them in the `$read_only` variable.</span></span>

```powershell
$read_only = Get-ChildItem *.txt | Where-Object {$_.isReadOnly}
```

<span data-ttu-id="2ad46-188">它相當於下列範例。</span><span class="sxs-lookup"><span data-stu-id="2ad46-188">It is equivalent to the following example.</span></span>

```powershell
$read_only = ( Get-ChildItem *.txt | Where-Object {$_.isReadOnly} )
```

<span data-ttu-id="2ad46-189">因為管線運算子 (`|`) 的優先順序高於指派運算子 (`=`) ，所以 Cmdlet 取得的檔案會在指派給 `Get-ChildItem` 變數之前，傳送至 `Where-Object` Cmdlet 進行篩選 `$read_only` 。</span><span class="sxs-lookup"><span data-stu-id="2ad46-189">Because the pipeline operator (`|`) has a higher precedence than the assignment operator (`=`), the files that the `Get-ChildItem` cmdlet gets are sent to the `Where-Object` cmdlet for filtering before they are assigned to the `$read_only` variable.</span></span>

<span data-ttu-id="2ad46-190">下列範例示範索引運算子的優先順序高於轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="2ad46-190">The following example demonstrates that the index operator takes precedence over the cast operator.</span></span>

<span data-ttu-id="2ad46-191">此運算式會建立三個字串的陣列。</span><span class="sxs-lookup"><span data-stu-id="2ad46-191">This expression creates an array of three strings.</span></span> <span data-ttu-id="2ad46-192">然後，它會使用具有0值的索引運算子來選取陣列中的第一個物件，也就是第一個字串。</span><span class="sxs-lookup"><span data-stu-id="2ad46-192">Then, it uses the index operator with a value of 0 to select the first object in the array, which is the first string.</span></span> <span data-ttu-id="2ad46-193">最後，它會將選取的物件轉換為字串。</span><span class="sxs-lookup"><span data-stu-id="2ad46-193">Finally, it casts the selected object as a string.</span></span> <span data-ttu-id="2ad46-194">在此情況下，轉換不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="2ad46-194">In this case, the cast has no effect.</span></span>

```powershell
PS> [string]@('Windows','PowerShell','2.0')[0]
Windows
```

<span data-ttu-id="2ad46-195">這個運算式會使用括弧來強制在索引選取之前進行轉換作業。</span><span class="sxs-lookup"><span data-stu-id="2ad46-195">This expression uses parentheses to force the cast operation to occur before the index selection.</span></span> <span data-ttu-id="2ad46-196">因此，整個陣列會轉換成 (單一) 字串。</span><span class="sxs-lookup"><span data-stu-id="2ad46-196">As a result, the entire array is cast as a (single) string.</span></span> <span data-ttu-id="2ad46-197">然後，索引運算子會選取字串陣列中的第一個專案，也就是第一個字元。</span><span class="sxs-lookup"><span data-stu-id="2ad46-197">Then, the index operator selects the first item in the string array, which is the first character.</span></span>

```powershell
PS> ([string]@('Windows','PowerShell','2.0'))[0]
W
```

<span data-ttu-id="2ad46-198">在下列範例中，因為 `-gt` (大於) 運算子的優先順序高於 `-and` (邏輯 AND) 運算子，所以運算式的結果為 FALSE。</span><span class="sxs-lookup"><span data-stu-id="2ad46-198">In the following example, because the `-gt` (greater-than) operator has a higher precedence than the `-and` (logical AND) operator, the result of the expression is FALSE.</span></span>

```powershell
PS> 2 -gt 4 -and 1
False
```

<span data-ttu-id="2ad46-199">它相當於下列運算式。</span><span class="sxs-lookup"><span data-stu-id="2ad46-199">It is equivalent to the following expression.</span></span>

```powershell
PS> (2 -gt 4) -and 1
False
```

<span data-ttu-id="2ad46-200">如果-and 運算子的優先順序較高，則答案會是 TRUE。</span><span class="sxs-lookup"><span data-stu-id="2ad46-200">If the -and operator had higher precedence, the answer would be TRUE.</span></span>

```powershell
PS> 2 -gt (4 -and 1)
True
```

<span data-ttu-id="2ad46-201">不過，此範例示範管理運算子優先順序的重要原則。</span><span class="sxs-lookup"><span data-stu-id="2ad46-201">However, this example demonstrates an important principle of managing operator precedence.</span></span> <span data-ttu-id="2ad46-202">當某個運算式不容易解讀時，請使用括弧來強制執行評估順序，即使它強制預設運算子優先順序亦同。</span><span class="sxs-lookup"><span data-stu-id="2ad46-202">When an expression is difficult for people to interpret, use parentheses to force the evaluation order, even when it forces the default operator precedence.</span></span> <span data-ttu-id="2ad46-203">括弧讓讀取和維護腳本的人員清楚明瞭。</span><span class="sxs-lookup"><span data-stu-id="2ad46-203">The parentheses make your intentions clear to people who are reading and maintaining your scripts.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ad46-204">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ad46-204">SEE ALSO</span></span>

<span data-ttu-id="2ad46-205">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-205">[about_Operators][]</span></span>

<span data-ttu-id="2ad46-206">[about_Assignment_Operators][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-206">[about_Assignment_Operators][]</span></span>

<span data-ttu-id="2ad46-207">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-207">[about_Comparison_Operators][]</span></span>

<span data-ttu-id="2ad46-208">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-208">[about_Arithmetic_Operators][]</span></span>

<span data-ttu-id="2ad46-209">[about_Join][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-209">[about_Join][]</span></span>

<span data-ttu-id="2ad46-210">[about_Redirection][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-210">[about_Redirection][]</span></span>

<span data-ttu-id="2ad46-211">[about_Scopes][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-211">[about_Scopes][]</span></span>

<span data-ttu-id="2ad46-212">[about_Split][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-212">[about_Split][]</span></span>

<span data-ttu-id="2ad46-213">[about_Type_Operators][]</span><span class="sxs-lookup"><span data-stu-id="2ad46-213">[about_Type_Operators][]</span></span>

<!-- reference links -->
[about_Arithmetic_Operators]: about_Arithmetic_Operators.md
[about_Assignment_Operators]: about_Assignment_Operators.md
[about_Comparison_Operators]: about_Comparison_Operators.md
[about_Join]: about_Join.md
[about_Logical_Operators]: about_logical_operators.md
[about_Operators]: about_Operators.md
[about_Redirection]: about_Redirection.md
[about_Scopes]: about_Scopes.md
[about_Split]: about_Split.md
[about_Type_Operators]: about_Type_Operators.md
