---
description: 描述 PowerShell 如何剖析命令。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parsing?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parsing
ms.openlocfilehash: d7b5af8c94ad6370c69773d2bc3796bace60ef7c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207967"
---
# <a name="about-parsing"></a><span data-ttu-id="3fcba-104">關於剖析</span><span class="sxs-lookup"><span data-stu-id="3fcba-104">About Parsing</span></span>

## <a name="short-description"></a><span data-ttu-id="3fcba-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="3fcba-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="3fcba-106">描述 PowerShell 如何剖析命令。</span><span class="sxs-lookup"><span data-stu-id="3fcba-106">Describes how PowerShell parses commands.</span></span>

## <a name="long-description"></a><span data-ttu-id="3fcba-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="3fcba-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="3fcba-108">當您在命令提示字元中輸入命令時，PowerShell 會將命令文字分成一系列稱為 _權杖_ 的區段，然後決定如何解讀每個標記。</span><span class="sxs-lookup"><span data-stu-id="3fcba-108">When you enter a command at the command prompt, PowerShell breaks the command text into a series of segments called _tokens_ and then determines how to interpret each token.</span></span>

<span data-ttu-id="3fcba-109">例如，如果您輸入：</span><span class="sxs-lookup"><span data-stu-id="3fcba-109">For example, if you type:</span></span>

```powershell
Write-Host book
```

<span data-ttu-id="3fcba-110">PowerShell 會將命令分成兩個權杖，並 `Write-Host` `book` 使用兩個主要剖析模式的其中一種來個別解釋每個權杖：運算式模式和引數模式。</span><span class="sxs-lookup"><span data-stu-id="3fcba-110">PowerShell breaks the command into two tokens, `Write-Host` and `book`, and interprets each token independently using one of two major parsing modes: expression mode and argument mode.</span></span>

> [!NOTE]
> <span data-ttu-id="3fcba-111">當 PowerShell 剖析命令輸入時，它會嘗試將命令名稱解析為 Cmdlet 或原生可執行檔。</span><span class="sxs-lookup"><span data-stu-id="3fcba-111">As PowerShell parses command input it tries to resolve the command names to cmdlets or native executables.</span></span> <span data-ttu-id="3fcba-112">如果命令名稱沒有完全相符的命令名稱，PowerShell 就會在命令前面加上 `Get-` 預設的動詞命令。</span><span class="sxs-lookup"><span data-stu-id="3fcba-112">If a command name does not have an exact match, PowerShell prepends `Get-` to the command as a default verb.</span></span> <span data-ttu-id="3fcba-113">例如，PowerShell 會剖析 `Process` 為 `Get-Process` 。</span><span class="sxs-lookup"><span data-stu-id="3fcba-113">For example, PowerShell parses `Process` as `Get-Process`.</span></span> <span data-ttu-id="3fcba-114">基於下列原因，不建議使用這項功能：</span><span class="sxs-lookup"><span data-stu-id="3fcba-114">It's not recommended to use this feature for the following reasons:</span></span>
>
> - <span data-ttu-id="3fcba-115">效率不佳。</span><span class="sxs-lookup"><span data-stu-id="3fcba-115">It's inefficient.</span></span> <span data-ttu-id="3fcba-116">這會導致 PowerShell 多次搜尋。</span><span class="sxs-lookup"><span data-stu-id="3fcba-116">This causes PowerShell to search multiple times.</span></span>
> - <span data-ttu-id="3fcba-117">系統會先解決具有相同名稱的外部程式，因此您可能無法執行預定的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3fcba-117">External programs with the same name are resolved first, so you may not execute intended cmdlet.</span></span>
> - <span data-ttu-id="3fcba-118">`Get-Help` 和 `Get-Command` 不辨識動詞命令的名稱。</span><span class="sxs-lookup"><span data-stu-id="3fcba-118">`Get-Help` and `Get-Command` don't recognize verb-less names.</span></span>

### <a name="expression-mode"></a><span data-ttu-id="3fcba-119">運算式模式</span><span class="sxs-lookup"><span data-stu-id="3fcba-119">Expression mode</span></span>

<span data-ttu-id="3fcba-120">運算式模式適用于結合運算式，這是在指令碼語言中進行值操作的必要項。</span><span class="sxs-lookup"><span data-stu-id="3fcba-120">Expression mode is intended for combining expressions, required for value manipulation in a scripting language.</span></span> <span data-ttu-id="3fcba-121">運算式是 PowerShell 語法中值的標記法，而且可以是簡單或複合的，例如：</span><span class="sxs-lookup"><span data-stu-id="3fcba-121">Expressions are representations of values in PowerShell syntax, and can be simple or composite, for example:</span></span>

<span data-ttu-id="3fcba-122">常值運算式是其值的直接標記法：</span><span class="sxs-lookup"><span data-stu-id="3fcba-122">Literal expressions are direct representations of their values:</span></span>

```powershell
'hello', 32
```

<span data-ttu-id="3fcba-123">變數運算式會包含它們所參考的變數值：</span><span class="sxs-lookup"><span data-stu-id="3fcba-123">Variable expressions carry the value of the variable they reference:</span></span>

```powershell
$x, $script:path
```

<span data-ttu-id="3fcba-124">運算子會合並其他運算式以進行評估：</span><span class="sxs-lookup"><span data-stu-id="3fcba-124">Operators combine other expressions for evaluation:</span></span>

```powershell
- 12, -not $Quiet, 3 + 7, $input.Length -gt 1
```

- <span data-ttu-id="3fcba-125">_字元字串常_ 值必須包含在引號中。</span><span class="sxs-lookup"><span data-stu-id="3fcba-125">_Character string literals_ must be contained in quotation marks.</span></span>
- <span data-ttu-id="3fcba-126">_數位_ 會被視為數值，而不是一系列的字元 (除非是) 的轉義。</span><span class="sxs-lookup"><span data-stu-id="3fcba-126">_Numbers_ are treated as numerical values rather than as a series of characters (unless escaped).</span></span>
- <span data-ttu-id="3fcba-127">_運算子_ （包括和和等 `-` 二元運算子） `-not` `+` `-gt` 會被視為運算子，並將其引數的各自作業套用至) 的 (運算元。</span><span class="sxs-lookup"><span data-stu-id="3fcba-127">_Operators_ , including unary operators like `-` and `-not` and binary operators like `+` and `-gt`, are interpreted as operators and apply their respective operations on their arguments (operands).</span></span>
- <span data-ttu-id="3fcba-128">_屬性和轉換運算式_ 會剖析為運算式，並套用至從屬運算式（例如） `[int] '7'` 。</span><span class="sxs-lookup"><span data-stu-id="3fcba-128">_Attribute and conversion expressions_ are parsed as expressions and applied to subordinate expressions, e.g. `[int] '7'`.</span></span>
- <span data-ttu-id="3fcba-129">_變數參考_ 會評估為它們的值，但 _展開_ (亦即，將預先填入的參數集貼入) 是禁止的，並導致剖析器錯誤。</span><span class="sxs-lookup"><span data-stu-id="3fcba-129">_Variable references_ are evaluated to their values but _splatting_ (i.e. pasting prefilled parameter sets) is forbidden and causes a parser error.</span></span>
- <span data-ttu-id="3fcba-130">任何其他將會被視為要叫用的命令。</span><span class="sxs-lookup"><span data-stu-id="3fcba-130">Anything else will be treated as a command to be invoked.</span></span>

### <a name="argument-mode"></a><span data-ttu-id="3fcba-131">引數模式</span><span class="sxs-lookup"><span data-stu-id="3fcba-131">Argument mode</span></span>

<span data-ttu-id="3fcba-132">剖析時，PowerShell 會先將輸入解讀為運算式。</span><span class="sxs-lookup"><span data-stu-id="3fcba-132">When parsing, PowerShell first looks to interpret input as an expression.</span></span> <span data-ttu-id="3fcba-133">但是，當遇到命令調用時，剖析作業會繼續處於引數模式。</span><span class="sxs-lookup"><span data-stu-id="3fcba-133">But when a command invocation is encountered, parsing continues in argument mode.</span></span>

<span data-ttu-id="3fcba-134">引數模式的設計是為了剖析 shell 環境中命令的引數和參數。</span><span class="sxs-lookup"><span data-stu-id="3fcba-134">Argument mode is designed for parsing arguments and parameters for commands in a shell environment.</span></span> <span data-ttu-id="3fcba-135">所有輸入都會被視為可擴充的字串，除非它使用下列其中一個語法：</span><span class="sxs-lookup"><span data-stu-id="3fcba-135">All input is treated as an expandable string unless it uses one of the following syntaxes:</span></span>

- <span data-ttu-id="3fcba-136">貨幣符號 (`$`) 只會在後面加上有效的變數名稱時才開始變數參考 (，否則會被視為可展開字串) 的一部分。</span><span class="sxs-lookup"><span data-stu-id="3fcba-136">Dollar sign (`$`) begins a variable reference (only if it is followed by a valid variable name, otherwise it is interpreted as part of the expandable string).</span></span>
- <span data-ttu-id="3fcba-137">引號 (`'` 和 `"`) 開始字串值</span><span class="sxs-lookup"><span data-stu-id="3fcba-137">Quotation marks (`'` and `"`) begin string values</span></span>
- <span data-ttu-id="3fcba-138">括弧 (`(` 和 `)`) 界限新的運算式。</span><span class="sxs-lookup"><span data-stu-id="3fcba-138">Parentheses (`(` and `)`) demarcate new expressions.</span></span>
- <span data-ttu-id="3fcba-139">子運算式運算子 (`$(` ... `)`) 標示內嵌運算式。</span><span class="sxs-lookup"><span data-stu-id="3fcba-139">Subexpression operator (`$(`…`)`) demarcates embedded expressions.</span></span>
- <span data-ttu-id="3fcba-140">括弧 (`{` ，並 `}`) 界限新的腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="3fcba-140">Braces (`{` and `}`) demarcate new script blocks.</span></span>
- <span data-ttu-id="3fcba-141">初始 at sign (`@`) 開始運算式語法，例如展開 (`@args`) 、陣列 (`@(1,2,3)`) ，以及雜湊表 () `@{a=1;b=2}` 。</span><span class="sxs-lookup"><span data-stu-id="3fcba-141">Initial at sign (`@`) begins expression syntaxes such as splatting (`@args`), arrays (`@(1,2,3)`) and hash tables (`@{a=1;b=2}`).</span></span>
- <span data-ttu-id="3fcba-142">`,`除非要呼叫的命令是原生應用程式，但在此情況下，會將它們視為可展開字串的一部分，所以逗號 () 引進以陣列形式傳遞的清單。</span><span class="sxs-lookup"><span data-stu-id="3fcba-142">Commas (`,`) introduce lists passed as arrays, except when the command to be called is a native application, in which case they are interpreted as part of the expandable string.</span></span> <span data-ttu-id="3fcba-143">不支援初始、連續或結尾的逗號。</span><span class="sxs-lookup"><span data-stu-id="3fcba-143">Initial, consecutive or trailing commas are not supported.</span></span>

<span data-ttu-id="3fcba-144">內嵌運算式的值會轉換成字串。</span><span class="sxs-lookup"><span data-stu-id="3fcba-144">Values of embedded expressions are converted to strings.</span></span>

<span data-ttu-id="3fcba-145">下表提供數個在運算式模式和引數模式中處理的值範例，以及這些值的評估。</span><span class="sxs-lookup"><span data-stu-id="3fcba-145">The following table provides several examples of values processed in expression mode and argument mode and the evaluation of those values.</span></span> <span data-ttu-id="3fcba-146">我們假設變數的值 `a` 是 `4` 。</span><span class="sxs-lookup"><span data-stu-id="3fcba-146">We assume that the value of the variable `a` is `4`.</span></span>

|       <span data-ttu-id="3fcba-147">範例</span><span class="sxs-lookup"><span data-stu-id="3fcba-147">Example</span></span>        |    <span data-ttu-id="3fcba-148">模式</span><span class="sxs-lookup"><span data-stu-id="3fcba-148">Mode</span></span>    |      <span data-ttu-id="3fcba-149">結果</span><span class="sxs-lookup"><span data-stu-id="3fcba-149">Result</span></span>       |
| -------------------- | ---------- | ----------------- |
| `2`                  | <span data-ttu-id="3fcba-150">運算是</span><span class="sxs-lookup"><span data-stu-id="3fcba-150">Expression</span></span> | <span data-ttu-id="3fcba-151">2 (整數) </span><span class="sxs-lookup"><span data-stu-id="3fcba-151">2 (integer)</span></span>       |
| `` `2``              | <span data-ttu-id="3fcba-152">運算式</span><span class="sxs-lookup"><span data-stu-id="3fcba-152">Expression</span></span> | <span data-ttu-id="3fcba-153">"2" (命令) </span><span class="sxs-lookup"><span data-stu-id="3fcba-153">"2" (command)</span></span>     |
| `echo 2`             | <span data-ttu-id="3fcba-154">運算式</span><span class="sxs-lookup"><span data-stu-id="3fcba-154">Expression</span></span> | <span data-ttu-id="3fcba-155">2 (整數) </span><span class="sxs-lookup"><span data-stu-id="3fcba-155">2 (integer)</span></span>       |
| `2+2`                | <span data-ttu-id="3fcba-156">運算式</span><span class="sxs-lookup"><span data-stu-id="3fcba-156">Expression</span></span> | <span data-ttu-id="3fcba-157">4 (整數) </span><span class="sxs-lookup"><span data-stu-id="3fcba-157">4 (integer)</span></span>       |
| `echo 2+2`           | <span data-ttu-id="3fcba-158">引數</span><span class="sxs-lookup"><span data-stu-id="3fcba-158">Argument</span></span>   | <span data-ttu-id="3fcba-159">"2 + 2" (字串) </span><span class="sxs-lookup"><span data-stu-id="3fcba-159">"2+2" (string)</span></span>    |
| `echo(2+2)`          | <span data-ttu-id="3fcba-160">運算式</span><span class="sxs-lookup"><span data-stu-id="3fcba-160">Expression</span></span> | <span data-ttu-id="3fcba-161">4 (整數) </span><span class="sxs-lookup"><span data-stu-id="3fcba-161">4 (integer)</span></span>       |
| `$a`                 | <span data-ttu-id="3fcba-162">運算式</span><span class="sxs-lookup"><span data-stu-id="3fcba-162">Expression</span></span> | <span data-ttu-id="3fcba-163">4 (整數) </span><span class="sxs-lookup"><span data-stu-id="3fcba-163">4 (integer)</span></span>       |
| `echo $a`            | <span data-ttu-id="3fcba-164">運算式</span><span class="sxs-lookup"><span data-stu-id="3fcba-164">Expression</span></span> | <span data-ttu-id="3fcba-165">4 (整數) </span><span class="sxs-lookup"><span data-stu-id="3fcba-165">4 (integer)</span></span>       |
| `$a+2`               | <span data-ttu-id="3fcba-166">運算式</span><span class="sxs-lookup"><span data-stu-id="3fcba-166">Expression</span></span> | <span data-ttu-id="3fcba-167">6 (整數) </span><span class="sxs-lookup"><span data-stu-id="3fcba-167">6 (integer)</span></span>       |
| `echo $a+2`          | <span data-ttu-id="3fcba-168">引數</span><span class="sxs-lookup"><span data-stu-id="3fcba-168">Argument</span></span>   | <span data-ttu-id="3fcba-169">4 + 2 (字串) </span><span class="sxs-lookup"><span data-stu-id="3fcba-169">4+2 (string)</span></span>      |
| `$-`                 | <span data-ttu-id="3fcba-170">引數</span><span class="sxs-lookup"><span data-stu-id="3fcba-170">Argument</span></span>   | <span data-ttu-id="3fcba-171">"$-" (命令) </span><span class="sxs-lookup"><span data-stu-id="3fcba-171">"$-" (command)</span></span>    |
| `echo $-`            | <span data-ttu-id="3fcba-172">引數</span><span class="sxs-lookup"><span data-stu-id="3fcba-172">Argument</span></span>   | <span data-ttu-id="3fcba-173">"$-" (字串) </span><span class="sxs-lookup"><span data-stu-id="3fcba-173">"$-" (string)</span></span>     |
| `a$a`                | <span data-ttu-id="3fcba-174">運算式</span><span class="sxs-lookup"><span data-stu-id="3fcba-174">Expression</span></span> | <span data-ttu-id="3fcba-175">"a $ a" (命令) </span><span class="sxs-lookup"><span data-stu-id="3fcba-175">"a$a" (command)</span></span>   |
| `echo a$a`           | <span data-ttu-id="3fcba-176">引數</span><span class="sxs-lookup"><span data-stu-id="3fcba-176">Argument</span></span>   | <span data-ttu-id="3fcba-177">"a4" (字串) </span><span class="sxs-lookup"><span data-stu-id="3fcba-177">"a4" (string)</span></span>     |
| `a'$a'`              | <span data-ttu-id="3fcba-178">運算式</span><span class="sxs-lookup"><span data-stu-id="3fcba-178">Expression</span></span> | <span data-ttu-id="3fcba-179">"a $ a" (命令) </span><span class="sxs-lookup"><span data-stu-id="3fcba-179">"a$a" (command)</span></span>   |
| `echo a'$a'`         | <span data-ttu-id="3fcba-180">引數</span><span class="sxs-lookup"><span data-stu-id="3fcba-180">Argument</span></span>   | <span data-ttu-id="3fcba-181">"a $ a" (字串) </span><span class="sxs-lookup"><span data-stu-id="3fcba-181">"a$a" (string)</span></span>    |
| `a"$a"`              | <span data-ttu-id="3fcba-182">運算式</span><span class="sxs-lookup"><span data-stu-id="3fcba-182">Expression</span></span> | <span data-ttu-id="3fcba-183">"a $ a" (命令) </span><span class="sxs-lookup"><span data-stu-id="3fcba-183">"a$a" (command)</span></span>   |
| `echo a"$a"`         | <span data-ttu-id="3fcba-184">引數</span><span class="sxs-lookup"><span data-stu-id="3fcba-184">Argument</span></span>   | <span data-ttu-id="3fcba-185">"a4" (字串) </span><span class="sxs-lookup"><span data-stu-id="3fcba-185">"a4" (string)</span></span>     |
| `a$(2)`              | <span data-ttu-id="3fcba-186">運算式</span><span class="sxs-lookup"><span data-stu-id="3fcba-186">Expression</span></span> | <span data-ttu-id="3fcba-187">"a $ (2) " (命令) </span><span class="sxs-lookup"><span data-stu-id="3fcba-187">"a$(2)" (command)</span></span> |
| `echo a$(2)`         | <span data-ttu-id="3fcba-188">引數</span><span class="sxs-lookup"><span data-stu-id="3fcba-188">Argument</span></span>   | <span data-ttu-id="3fcba-189">"a2" (字串) </span><span class="sxs-lookup"><span data-stu-id="3fcba-189">"a2" (string)</span></span>     |

<span data-ttu-id="3fcba-190">每個標記都可以解讀為某種類型的物件類型，例如布林值或字串。</span><span class="sxs-lookup"><span data-stu-id="3fcba-190">Every token can be interpreted as some kind of object type, such as Boolean or string.</span></span> <span data-ttu-id="3fcba-191">PowerShell 會嘗試從運算式判斷物件類型。</span><span class="sxs-lookup"><span data-stu-id="3fcba-191">PowerShell attempts to determine the object type from the expression.</span></span>
<span data-ttu-id="3fcba-192">物件類型取決於命令所預期的參數類型，以及 PowerShell 是否知道如何將引數轉換成正確的型別。</span><span class="sxs-lookup"><span data-stu-id="3fcba-192">The object type depends on the type of parameter a command expects and on whether PowerShell knows how to convert the argument to the correct type.</span></span> <span data-ttu-id="3fcba-193">下表顯示數個指派給運算式所傳回值的類型範例。</span><span class="sxs-lookup"><span data-stu-id="3fcba-193">The following table shows several examples of the types assigned to values returned by the expressions.</span></span>

|       <span data-ttu-id="3fcba-194">範例</span><span class="sxs-lookup"><span data-stu-id="3fcba-194">Example</span></span>          |    <span data-ttu-id="3fcba-195">模式</span><span class="sxs-lookup"><span data-stu-id="3fcba-195">Mode</span></span>    |     <span data-ttu-id="3fcba-196">結果</span><span class="sxs-lookup"><span data-stu-id="3fcba-196">Result</span></span>      |
| ---------------------- | ---------- | --------------- |
| `Write-Output !1`      | <span data-ttu-id="3fcba-197">引數</span><span class="sxs-lookup"><span data-stu-id="3fcba-197">argument</span></span>   | <span data-ttu-id="3fcba-198">"！ 1" (字串) </span><span class="sxs-lookup"><span data-stu-id="3fcba-198">"!1" (string)</span></span>   |
| `Write-Output (!1)`    | <span data-ttu-id="3fcba-199">運算式</span><span class="sxs-lookup"><span data-stu-id="3fcba-199">expression</span></span> | <span data-ttu-id="3fcba-200">False (布林值) </span><span class="sxs-lookup"><span data-stu-id="3fcba-200">False (Boolean)</span></span> |
| `Write-Output (2)`     | <span data-ttu-id="3fcba-201">運算式</span><span class="sxs-lookup"><span data-stu-id="3fcba-201">expression</span></span> | <span data-ttu-id="3fcba-202">2 (整數) </span><span class="sxs-lookup"><span data-stu-id="3fcba-202">2 (integer)</span></span>     |
| `Set-Variable AB A,B`  | <span data-ttu-id="3fcba-203">引數</span><span class="sxs-lookup"><span data-stu-id="3fcba-203">argument</span></span>   | <span data-ttu-id="3fcba-204">' A '、' B ' (陣列) </span><span class="sxs-lookup"><span data-stu-id="3fcba-204">'A','B' (array)</span></span> |
| `CMD /CECHO A,B`       | <span data-ttu-id="3fcba-205">引數</span><span class="sxs-lookup"><span data-stu-id="3fcba-205">argument</span></span>   | <span data-ttu-id="3fcba-206">' A，B ' (字串) </span><span class="sxs-lookup"><span data-stu-id="3fcba-206">'A,B' (string)</span></span>  |
| `CMD /CECHO $AB`       | <span data-ttu-id="3fcba-207">運算式</span><span class="sxs-lookup"><span data-stu-id="3fcba-207">expression</span></span> | <span data-ttu-id="3fcba-208">' A '、' B ' (陣列) </span><span class="sxs-lookup"><span data-stu-id="3fcba-208">'A','B' (array)</span></span> |
| `CMD /CECHO :$AB`      | <span data-ttu-id="3fcba-209">引數</span><span class="sxs-lookup"><span data-stu-id="3fcba-209">argument</span></span>   | <span data-ttu-id="3fcba-210">'： B ' (字串) </span><span class="sxs-lookup"><span data-stu-id="3fcba-210">':A B' (string)</span></span> |

<span data-ttu-id="3fcba-211">在 PowerShell 3.0 中引進的停止剖析符號 () ，會 `--%` 指示 powershell 避免將輸入解釋為 powershell 命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="3fcba-211">The stop-parsing symbol (`--%`), introduced in PowerShell 3.0, directs PowerShell to refrain from interpreting input as PowerShell commands or expressions.</span></span>

<span data-ttu-id="3fcba-212">在 PowerShell 中呼叫可執行程式時，請在程式引數之前放置停止剖析符號。</span><span class="sxs-lookup"><span data-stu-id="3fcba-212">When calling an executable program in PowerShell, place the stop-parsing symbol before the program arguments.</span></span> <span data-ttu-id="3fcba-213">這項技術比使用 escape 字元來防止解釋的程式更容易。</span><span class="sxs-lookup"><span data-stu-id="3fcba-213">This technique is much easier than using escape characters to prevent misinterpretation.</span></span>

<span data-ttu-id="3fcba-214">當它遇到停止剖析符號時，PowerShell 會將該行中的其餘字元視為常值。</span><span class="sxs-lookup"><span data-stu-id="3fcba-214">When it encounters a stop-parsing symbol, PowerShell treats the remaining characters in the line as a literal.</span></span> <span data-ttu-id="3fcba-215">唯一會執行的轉譯是替代使用標準 Windows 標記法的環境變數值，例如 `%USERPROFILE%` 。</span><span class="sxs-lookup"><span data-stu-id="3fcba-215">The only interpretation it performs is to substitute values for environment variables that use standard Windows notation, such as `%USERPROFILE%`.</span></span>

<span data-ttu-id="3fcba-216">停止剖析符號只有在下一個新行或管線字元之後才有效。</span><span class="sxs-lookup"><span data-stu-id="3fcba-216">The stop-parsing symbol is effective only until the next newline or pipeline character.</span></span> <span data-ttu-id="3fcba-217">您無法使用接續字元 (`` ` ``) 來延伸其效果，或使用命令分隔符號 (`;`) 終止其效果。</span><span class="sxs-lookup"><span data-stu-id="3fcba-217">You cannot use a continuation character (`` ` ``) to extend its effect or use a command delimiter (`;`) to terminate its effect.</span></span>

<span data-ttu-id="3fcba-218">例如，下列命令會呼叫 **Icacls** 程式。</span><span class="sxs-lookup"><span data-stu-id="3fcba-218">For example, the following command calls the **Icacls** program.</span></span>

```powershell
icacls X:\VMS /grant Dom\HVAdmin:(CI)(OI)F
```

<span data-ttu-id="3fcba-219">若要在 PowerShell 2.0 中執行此命令，您必須使用 escape 字元，以防止 PowerShell 錯誤解譯括弧。</span><span class="sxs-lookup"><span data-stu-id="3fcba-219">To run this command in PowerShell 2.0, you must use escape characters to prevent PowerShell from misinterpreting the parentheses.</span></span>

```powershell
icacls X:\VMS /grant Dom\HVAdmin:`(CI`)`(OI`)F
```

<span data-ttu-id="3fcba-220">從 PowerShell 3.0 開始，您可以使用停止剖析符號。</span><span class="sxs-lookup"><span data-stu-id="3fcba-220">Beginning in PowerShell 3.0, you can use the stop-parsing symbol.</span></span>

```powershell
icacls X:\VMS --% /grant Dom\HVAdmin:(CI)(OI)F
```

<span data-ttu-id="3fcba-221">PowerShell 會將下列命令字串傳送至 **Icacls** 程式：</span><span class="sxs-lookup"><span data-stu-id="3fcba-221">PowerShell sends the following command string to the **Icacls** program:</span></span>

`X:\VMS /grant Dom\HVAdmin:(CI)(OI)F`

## <a name="see-also"></a><span data-ttu-id="3fcba-222">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3fcba-222">SEE ALSO</span></span>

[<span data-ttu-id="3fcba-223">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="3fcba-223">about_Command_Syntax</span></span>](about_Command_Syntax.md)
