---
description: 描述 PowerShell 中的正則運算式。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_regular_expressions?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Regular_Expressions
ms.openlocfilehash: 84eefe224912cca96e6637eb6e3f239ef66b25bc
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207948"
---
# <a name="about-regular-expressions"></a><span data-ttu-id="f0557-104">關於正則運算式</span><span class="sxs-lookup"><span data-stu-id="f0557-104">About Regular Expressions</span></span>

## <a name="short-description"></a><span data-ttu-id="f0557-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="f0557-105">Short description</span></span>
<span data-ttu-id="f0557-106">描述 PowerShell 中的正則運算式。</span><span class="sxs-lookup"><span data-stu-id="f0557-106">Describes regular expressions in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="f0557-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="f0557-107">Long description</span></span>

> [!NOTE]
> <span data-ttu-id="f0557-108">本文將說明在 PowerShell 中使用正則運算式的語法和方法，而不會討論所有語法。</span><span class="sxs-lookup"><span data-stu-id="f0557-108">This article will show you the syntax and methods for using regular expressions in PowerShell, not all syntax is discussed.</span></span> <span data-ttu-id="f0557-109">如需更完整的參考，請參閱 [正則運算式語言-快速參考](/dotnet/standard/base-types/regular-expression-language-quick-reference)。</span><span class="sxs-lookup"><span data-stu-id="f0557-109">For a more complete reference, see the [Regular Expression Language - Quick Reference](/dotnet/standard/base-types/regular-expression-language-quick-reference).</span></span>

<span data-ttu-id="f0557-110">正則運算式是用來比對文字的模式。</span><span class="sxs-lookup"><span data-stu-id="f0557-110">A regular expression is a pattern used to match text.</span></span> <span data-ttu-id="f0557-111">它可以由常值字元、運算子和其他結構組成。</span><span class="sxs-lookup"><span data-stu-id="f0557-111">It can be made up of literal characters, operators, and other constructs.</span></span>

<span data-ttu-id="f0557-112">本文示範 PowerShell 中的正則運算式語法。</span><span class="sxs-lookup"><span data-stu-id="f0557-112">This article demonstrates regular expression syntax in PowerShell.</span></span> <span data-ttu-id="f0557-113">PowerShell 有數個使用正則運算式的運算子和 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f0557-113">PowerShell has several operators and cmdlets that use regular expressions.</span></span> <span data-ttu-id="f0557-114">您可以在下列連結深入瞭解其語法和用法。</span><span class="sxs-lookup"><span data-stu-id="f0557-114">You can read more about their syntax and usage at the links below.</span></span>

- [<span data-ttu-id="f0557-115">Select-String</span><span class="sxs-lookup"><span data-stu-id="f0557-115">Select-String</span></span>](xref:Microsoft.PowerShell.Utility.Select-String)
- [<span data-ttu-id="f0557-116">-match 和-replace 運算子</span><span class="sxs-lookup"><span data-stu-id="f0557-116">-match and -replace operators</span></span>](about_Comparison_Operators.md)
- [<span data-ttu-id="f0557-117">-分割</span><span class="sxs-lookup"><span data-stu-id="f0557-117">-split</span></span>](about_Split.md)
- [<span data-ttu-id="f0557-118">使用-RegEx 選項的 switch 語句</span><span class="sxs-lookup"><span data-stu-id="f0557-118">switch statement with -regex option</span></span>](about_Switch.md)

<span data-ttu-id="f0557-119">PowerShell 正則運算式預設為不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="f0557-119">PowerShell regular expressions are case-insensitive by default.</span></span> <span data-ttu-id="f0557-120">以上顯示的每個方法都有不同的方式來強制區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="f0557-120">Each method shown above has a different way to force case sensitivity.</span></span>

|       <span data-ttu-id="f0557-121">方法</span><span class="sxs-lookup"><span data-stu-id="f0557-121">Method</span></span>       |                      <span data-ttu-id="f0557-122">區分大小寫</span><span class="sxs-lookup"><span data-stu-id="f0557-122">Case Sensitivity</span></span>                      |
| ------------------ | ---------------------------------------------------------- |
| `Select-String`    | <span data-ttu-id="f0557-123">使用 `-CaseSensitive` 參數</span><span class="sxs-lookup"><span data-stu-id="f0557-123">use `-CaseSensitive` switch</span></span>                                |
| <span data-ttu-id="f0557-124">`switch` 陳述式</span><span class="sxs-lookup"><span data-stu-id="f0557-124">`switch` statement</span></span> | <span data-ttu-id="f0557-125">使用 `-casesensitive` 選項</span><span class="sxs-lookup"><span data-stu-id="f0557-125">use the `-casesensitive` option</span></span>                            |
| <span data-ttu-id="f0557-126">運算子</span><span class="sxs-lookup"><span data-stu-id="f0557-126">operators</span></span>          | <span data-ttu-id="f0557-127">前置詞為 **' c '** (`-cmatch` 、 `-csplit` 或 `-creplace`) </span><span class="sxs-lookup"><span data-stu-id="f0557-127">prefix with **'c'** (`-cmatch`, `-csplit`, or `-creplace`)</span></span> |

### <a name="character-literals"></a><span data-ttu-id="f0557-128">字元常值</span><span class="sxs-lookup"><span data-stu-id="f0557-128">Character literals</span></span>

<span data-ttu-id="f0557-129">正則運算式可以是常值字元或字串。</span><span class="sxs-lookup"><span data-stu-id="f0557-129">A regular expression can be a literal character or a string.</span></span> <span data-ttu-id="f0557-130">運算式會使引擎完全符合指定的文字。</span><span class="sxs-lookup"><span data-stu-id="f0557-130">The expression causes the engine to match the text specified exactly.</span></span>

```powershell
# This statement returns true because book contains the string "oo"
'book' -match 'oo'
```

### <a name="character-classes"></a><span data-ttu-id="f0557-131">字元類別</span><span class="sxs-lookup"><span data-stu-id="f0557-131">Character classes</span></span>

<span data-ttu-id="f0557-132">如果您知道確切的模式，字元常值就會運作，而字元類別可讓您更不特定。</span><span class="sxs-lookup"><span data-stu-id="f0557-132">While character literals work if you know the exact pattern, character classes allow you to be less specific.</span></span>

#### <a name="character-groups"></a><span data-ttu-id="f0557-133">字元群組</span><span class="sxs-lookup"><span data-stu-id="f0557-133">Character groups</span></span>

<span data-ttu-id="f0557-134">`[character group]` 可讓您一次比對任意數目的字元，而 `[^character group]` 只會比對不在群組中的字元。</span><span class="sxs-lookup"><span data-stu-id="f0557-134">`[character group]` allows you to match any number of characters one time, while `[^character group]` only matches characters NOT in the group.</span></span>

```powershell
# This expression returns true if the pattern matches big, bog, or bug.
'big' -match 'b[iou]g'
```

<span data-ttu-id="f0557-135">如果要比對的字元清單包含連字號字元 (`-`) ，它必須位於清單的開頭或結尾，才能與字元範圍運算式區分。</span><span class="sxs-lookup"><span data-stu-id="f0557-135">If your list of characters to match includes the hyphen character (`-`), it must be at the beginning or end of the list to distinguish it from a character range expression.</span></span>

#### <a name="character-ranges"></a><span data-ttu-id="f0557-136">字元範圍</span><span class="sxs-lookup"><span data-stu-id="f0557-136">Character ranges</span></span>

<span data-ttu-id="f0557-137">模式也可以是字元的範圍。</span><span class="sxs-lookup"><span data-stu-id="f0557-137">A pattern can also be a range of characters.</span></span> <span data-ttu-id="f0557-138">這些字元可以是字母 `[A-Z]` 、數位 `[0-9]` ，甚至是以 ASCII 為基礎 `[ -~]` (所有可列印的字元) 。</span><span class="sxs-lookup"><span data-stu-id="f0557-138">The characters can be alphabetic `[A-Z]`, numeric `[0-9]`, or even ASCII-based `[ -~]` (all printable characters).</span></span>

```powershell
# This expression returns true if the pattern matches any 2 digit number.
42 -match '[0-9][0-9]'
```

#### <a name="numbers"></a><span data-ttu-id="f0557-139">數字</span><span class="sxs-lookup"><span data-stu-id="f0557-139">Numbers</span></span>

<span data-ttu-id="f0557-140">`\d`字元類別將會比對任何十進位數。</span><span class="sxs-lookup"><span data-stu-id="f0557-140">The `\d` character class will match any decimal digit.</span></span> <span data-ttu-id="f0557-141">相反地， `\D` 將會比對任何非十進位數。</span><span class="sxs-lookup"><span data-stu-id="f0557-141">Conversely, `\D` will match any non-decimal digit.</span></span>

```powershell
# This expression returns true if it matches a server name.
# (Server-01 - Server-99).
'Server-01' -match 'Server-\d\d'
```

#### <a name="word-characters"></a><span data-ttu-id="f0557-142">單字字元</span><span class="sxs-lookup"><span data-stu-id="f0557-142">Word characters</span></span>

<span data-ttu-id="f0557-143">`\w`字元類別將會比對任何文字字元 `[a-zA-Z_0-9]` 。</span><span class="sxs-lookup"><span data-stu-id="f0557-143">The `\w` character class will match any word character `[a-zA-Z_0-9]`.</span></span> <span data-ttu-id="f0557-144">若要比對任何非文字字元，請使用 `\W` 。</span><span class="sxs-lookup"><span data-stu-id="f0557-144">To match any non-word character, use `\W`.</span></span>

```powershell
# This expression returns true.
# The pattern matches the first word character 'B'.
'Book' -match '\w'
```

#### <a name="wildcards"></a><span data-ttu-id="f0557-145">萬用字元</span><span class="sxs-lookup"><span data-stu-id="f0557-145">Wildcards</span></span>

<span data-ttu-id="f0557-146">期間 (`.`) 是正則運算式中的萬用字元。</span><span class="sxs-lookup"><span data-stu-id="f0557-146">The period (`.`) is a wildcard character in regular expressions.</span></span> <span data-ttu-id="f0557-147">它會比對任何字元，但不包括分行符號 (`\n`) 。</span><span class="sxs-lookup"><span data-stu-id="f0557-147">It will match any character except a newline (`\n`).</span></span>

```powershell
# This expression returns true.
# The pattern matches any 4 characters except the newline.
'a1\ ' -match '....'
```

#### <a name="whitespace"></a><span data-ttu-id="f0557-148">空白</span><span class="sxs-lookup"><span data-stu-id="f0557-148">Whitespace</span></span>

<span data-ttu-id="f0557-149">空白字元會使用字元類別進行比對 `\s` 。</span><span class="sxs-lookup"><span data-stu-id="f0557-149">Whitespace is matched using the `\s` character class.</span></span> <span data-ttu-id="f0557-150">任何非空白字元都會使用進行比對 `\S` 。</span><span class="sxs-lookup"><span data-stu-id="f0557-150">Any non-whitespace character is matched using `\S`.</span></span> <span data-ttu-id="f0557-151">也可以使用常值空白字元 `' '` 。</span><span class="sxs-lookup"><span data-stu-id="f0557-151">Literal space characters `' '` can also be used.</span></span>

```powershell
# This expression returns true.
# The pattern uses both methods to match the space.
' - ' -match '\s- '
```

### <a name="quantifiers"></a><span data-ttu-id="f0557-152">數量詞</span><span class="sxs-lookup"><span data-stu-id="f0557-152">Quantifiers</span></span>

<span data-ttu-id="f0557-153">數量詞會控制每個專案的實例應該出現在輸入字串中的數目。</span><span class="sxs-lookup"><span data-stu-id="f0557-153">Quantifiers control how many instances of each element should be present in the input string.</span></span>

<span data-ttu-id="f0557-154">以下是 PowerShell 中可用的一些數量詞：</span><span class="sxs-lookup"><span data-stu-id="f0557-154">The following are a few of the quantifiers available in PowerShell:</span></span>

| <span data-ttu-id="f0557-155">數量詞</span><span class="sxs-lookup"><span data-stu-id="f0557-155">Quantifier</span></span> |                <span data-ttu-id="f0557-156">Description</span><span class="sxs-lookup"><span data-stu-id="f0557-156">Description</span></span>                |
| ---------- | ----------------------------------------- |
| `*`        | <span data-ttu-id="f0557-157">零次或多次。</span><span class="sxs-lookup"><span data-stu-id="f0557-157">Zero or more times.</span></span>                       |
| `+`        | <span data-ttu-id="f0557-158">一或多次。</span><span class="sxs-lookup"><span data-stu-id="f0557-158">One or more times.</span></span>                        |
| `?`        | <span data-ttu-id="f0557-159">零次或一次。</span><span class="sxs-lookup"><span data-stu-id="f0557-159">Zero or one time.</span></span>                         |
| `{n,m}`    | <span data-ttu-id="f0557-160">至少 `n` ，但不能超過一 `m` 次。</span><span class="sxs-lookup"><span data-stu-id="f0557-160">At least `n`, but no more than `m` times.</span></span> |

<span data-ttu-id="f0557-161">星號 (`*`) 比對前一個元素零次或多次。</span><span class="sxs-lookup"><span data-stu-id="f0557-161">The asterisk (`*`) matches the previous element zero or more times.</span></span> <span data-ttu-id="f0557-162">結果是，即使輸入字串沒有元素，也會是相符專案。</span><span class="sxs-lookup"><span data-stu-id="f0557-162">The result is that even an input string without the element would be a match.</span></span>

```powershell
# This returns true for all account name strings even if the name is absent.
'ACCOUNT NAME:    Administrator' -match 'ACCOUNT NAME:\s*\w*'
```

<span data-ttu-id="f0557-163">加號 (`+`) 比對前一個元素一或多次。</span><span class="sxs-lookup"><span data-stu-id="f0557-163">The plus sign (`+`) matches the previous element one or more times.</span></span>

```powershell
# This returns true if it matches any server name.
'DC-01' -match '[A-Z]+-\d\d'
```

<span data-ttu-id="f0557-164">問號會 `?` 比對前一個元素零或一次。</span><span class="sxs-lookup"><span data-stu-id="f0557-164">The question mark `?` matches the previous element zero or one time.</span></span> <span data-ttu-id="f0557-165">就像星號一樣 `*` ，它甚至會比對不存在元素的字串。</span><span class="sxs-lookup"><span data-stu-id="f0557-165">Like asterisk `*`, it will even match strings where the element is absent.</span></span>

```powershell
# This returns true for any server name, even server names without dashes.
'SERVER01' -match '[A-Z]+-?\d\d'
```

<span data-ttu-id="f0557-166">`{n, m}`數量詞可以使用數種不同的方式來允許對數量詞進行細微的控制。</span><span class="sxs-lookup"><span data-stu-id="f0557-166">The `{n, m}` quantifier can be used several different ways to allow granular control over the quantifier.</span></span> <span data-ttu-id="f0557-167">第二個元素 `m` 和逗號 `,` 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="f0557-167">The second element `m` and the comma `,` are optional.</span></span>

| <span data-ttu-id="f0557-168">數量詞</span><span class="sxs-lookup"><span data-stu-id="f0557-168">Quantifier</span></span> |                <span data-ttu-id="f0557-169">Description</span><span class="sxs-lookup"><span data-stu-id="f0557-169">Description</span></span>                 |
| ---------- | ------------------------------------------ |
| `{n}`      | <span data-ttu-id="f0557-170">精確比 `n` 對的次數。</span><span class="sxs-lookup"><span data-stu-id="f0557-170">Match EXACTLY `n` number of times.</span></span>         |
| `{n,}`     | <span data-ttu-id="f0557-171">至少比 `n` 對次數。</span><span class="sxs-lookup"><span data-stu-id="f0557-171">Match at LEAST `n` number of times.</span></span>        |
| `{n,m}`    | <span data-ttu-id="f0557-172">比 `n` 對和 `m` 次數。</span><span class="sxs-lookup"><span data-stu-id="f0557-172">Match between `n` and `m` number of times.</span></span> |

```powershell
# This returns true if it matches any phone number.
'111-222-3333' -match '\d{3}-\d{3}-\d{4}'
```

### <a name="anchors"></a><span data-ttu-id="f0557-173">錨點</span><span class="sxs-lookup"><span data-stu-id="f0557-173">Anchors</span></span>

<span data-ttu-id="f0557-174">錨點可讓您根據輸入字串內的相符位置，使相符專案成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="f0557-174">Anchors allow you to cause a match to succeed or fail based on the matches position within the input string.</span></span>

<span data-ttu-id="f0557-175">這兩個常用錨點為 `^` 和 `$` 。</span><span class="sxs-lookup"><span data-stu-id="f0557-175">The two commonly used anchors are `^` and `$`.</span></span> <span data-ttu-id="f0557-176">插入點會比對字串的 `^` 開頭和 `$` ，後者會符合字串的結尾。</span><span class="sxs-lookup"><span data-stu-id="f0557-176">The caret `^` matches the start of a string, and `$`, which matches the end of a string.</span></span> <span data-ttu-id="f0557-177">錨點可讓您在特定位置比對文字，同時也會捨棄不需要的字元。</span><span class="sxs-lookup"><span data-stu-id="f0557-177">The anchors allow you to match your text at a specific position while also discarding unwanted characters.</span></span>

```powershell
# The pattern expects the string 'fish' to be the only thing on the line.
# This returns FALSE.
'fishing' -match '^fish$'
```

> [!NOTE]
> <span data-ttu-id="f0557-178">定義包含錨點的 RegEx 時 `$` ，請務必使用單引號來括住 RegEx (`'`) 而不是雙引號 (`"`) 或 PowerShell 會將運算式擴充為變數。</span><span class="sxs-lookup"><span data-stu-id="f0557-178">When defining a regex containing an `$` anchor, be sure to enclose the regex using single quotes (`'`) instead of double quotes (`"`) or PowerShell will expand the expression as a variable.</span></span>

<span data-ttu-id="f0557-179">在 PowerShell 中使用錨點時，您應該瞭解 **單行** 和 **多行** 正則運算式選項之間的差異。</span><span class="sxs-lookup"><span data-stu-id="f0557-179">When using anchors in PowerShell, you should understand the difference between **Singleline** and **Multiline** regular expression options.</span></span>

- <span data-ttu-id="f0557-180">**多** 行：多行模式會強制 `^` 並 `$` 比對每一行的開頭，而不是輸入字串的開頭和結尾。</span><span class="sxs-lookup"><span data-stu-id="f0557-180">**Multiline** : Multiline mode forces `^` and `$` to match the beginning end of every LINE instead of the beginning and end of the input string.</span></span>
- <span data-ttu-id="f0557-181">**單行** ：單行模式會將輸入字串視為 **單行** 。</span><span class="sxs-lookup"><span data-stu-id="f0557-181">**Singleline** : Singleline mode treats the input string as a **SingleLine** .</span></span>
  <span data-ttu-id="f0557-182">它會強制 `.` 字元符合每個字元 (包括分行符號) ，而不是比對分行符號以外的每個字元 `\n` 。</span><span class="sxs-lookup"><span data-stu-id="f0557-182">It forces the `.` character to match every character (including newlines), instead of matching every character EXCEPT the newline `\n`.</span></span>

<span data-ttu-id="f0557-183">若要深入瞭解這些選項以及如何使用這些選項，請造訪 [正則運算式語言-快速參考](/dotnet/standard/base-types/regular-expression-language-quick-reference)。</span><span class="sxs-lookup"><span data-stu-id="f0557-183">To read more about these options and how to use them, visit the [Regular Expression Language - Quick Reference](/dotnet/standard/base-types/regular-expression-language-quick-reference).</span></span>

### <a name="escaping-characters"></a><span data-ttu-id="f0557-184">逸出字元</span><span class="sxs-lookup"><span data-stu-id="f0557-184">Escaping characters</span></span>

<span data-ttu-id="f0557-185">反斜線 (`\`) 用來 escape 字元，因此正則運算式引擎不會剖析它們。</span><span class="sxs-lookup"><span data-stu-id="f0557-185">The backslash (`\`) is used to escape characters so they aren't parsed by the regular expression engine.</span></span>

<span data-ttu-id="f0557-186">保留下列字元： `[]().\^$|?*+{}` 。</span><span class="sxs-lookup"><span data-stu-id="f0557-186">The following characters are reserved: `[]().\^$|?*+{}`.</span></span>

<span data-ttu-id="f0557-187">您必須在模式中將這些字元換成符合輸入字串中的字元。</span><span class="sxs-lookup"><span data-stu-id="f0557-187">You'll need to escape these characters in your patterns to match them in your input strings.</span></span>

```powershell
# This returns true and matches numbers with at least 2 digits of precision.
# The decimal point is escaped using the backslash.
'3.141' -match '3\.\d{2,}'
```

<span data-ttu-id="f0557-188">Regex 類別的靜態方法可為您 escape 文字。</span><span class="sxs-lookup"><span data-stu-id="f0557-188">There\`s a static method of the regex class that can escape text for you.</span></span>

```powershell
[regex]::escape('3.\d{2,}')
```

```Output
3\.\\d\{2,}
```

> [!NOTE]
> <span data-ttu-id="f0557-189">這會將所有保留的正則運算式字元（包括字元類別中使用的現有反斜線）全部轉義。</span><span class="sxs-lookup"><span data-stu-id="f0557-189">This escapes all reserved regular expression characters, including existing backslashes used in character classes.</span></span> <span data-ttu-id="f0557-190">請務必只在您需要 escape 的模式部分使用它。</span><span class="sxs-lookup"><span data-stu-id="f0557-190">Be sure to only use it on the portion of your pattern that you need to escape.</span></span>

#### <a name="other-character-escapes"></a><span data-ttu-id="f0557-191">其他字元轉義</span><span class="sxs-lookup"><span data-stu-id="f0557-191">Other character escapes</span></span>

<span data-ttu-id="f0557-192">您也可以使用保留的字元 esc 來比對特殊的字元類型。</span><span class="sxs-lookup"><span data-stu-id="f0557-192">There are also reserved character escapes that you can use to match special character types.</span></span>

<span data-ttu-id="f0557-193">以下是一些常用的字元數轉義：</span><span class="sxs-lookup"><span data-stu-id="f0557-193">The following are a few commonly used character escapes:</span></span>

|<span data-ttu-id="f0557-194">字元 Escape</span><span class="sxs-lookup"><span data-stu-id="f0557-194">Character Escape</span></span>  |<span data-ttu-id="f0557-195">Description</span><span class="sxs-lookup"><span data-stu-id="f0557-195">Description</span></span>  |
|---------|---------|
|`\t`|<span data-ttu-id="f0557-196">符合索引標籤</span><span class="sxs-lookup"><span data-stu-id="f0557-196">Matches a tab</span></span>|
|`\n`|<span data-ttu-id="f0557-197">符合新行</span><span class="sxs-lookup"><span data-stu-id="f0557-197">Matches a newline</span></span>|
|`\r`|<span data-ttu-id="f0557-198">符合回車</span><span class="sxs-lookup"><span data-stu-id="f0557-198">Matches a carriage return</span></span>|

### <a name="groups-captures-and-substitutions"></a><span data-ttu-id="f0557-199">群組、捕捉和替代</span><span class="sxs-lookup"><span data-stu-id="f0557-199">Groups, Captures, and Substitutions</span></span>

<span data-ttu-id="f0557-200">群組結構會將輸入字串分隔成可加以捕獲或忽略的子字串。</span><span class="sxs-lookup"><span data-stu-id="f0557-200">Grouping constructs separate an input string into substrings that can be captured or ignored.</span></span> <span data-ttu-id="f0557-201">群組的子字串稱為子運算式。</span><span class="sxs-lookup"><span data-stu-id="f0557-201">Grouped substrings are called subexpressions.</span></span> <span data-ttu-id="f0557-202">依預設，子運算式是在編號群組中捕捉，不過您也可以指派名稱給它們。</span><span class="sxs-lookup"><span data-stu-id="f0557-202">By default subexpressions are captured in numbered groups, though you can assign names to them as well.</span></span>

<span data-ttu-id="f0557-203">群組結構是以括弧括住的正則運算式。</span><span class="sxs-lookup"><span data-stu-id="f0557-203">A grouping construct is a regular expression surrounded by parentheses.</span></span> <span data-ttu-id="f0557-204">會捕捉任何由包含的正則運算式相符的文字。</span><span class="sxs-lookup"><span data-stu-id="f0557-204">Any text matched by the enclosed regular expression is captured.</span></span> <span data-ttu-id="f0557-205">下列範例會將輸入文字分成兩個捕獲群組。</span><span class="sxs-lookup"><span data-stu-id="f0557-205">The following example will break the input text into two capturing groups.</span></span>

```powershell
'The last logged on user was CONTOSO\jsmith' -match '(.+was )(.+)'
```

```Output
True
```

<span data-ttu-id="f0557-206">使用 `$Matches` **Hashtable** 自動變數來取出捕捉的文字。</span><span class="sxs-lookup"><span data-stu-id="f0557-206">Use the `$Matches` **Hashtable** automatic variable to retrieve captured text.</span></span>
<span data-ttu-id="f0557-207">代表整個相符的文字會儲存在索引鍵 `0` 。</span><span class="sxs-lookup"><span data-stu-id="f0557-207">The text representing the entire match is stored at key `0`.</span></span>

```powershell
$Matches.0
```

```Output
The last logged on user was CONTOSO\jsmith
```

<span data-ttu-id="f0557-208">捕捉會儲存在由左至右增加的數值 **整數** 索引鍵中。</span><span class="sxs-lookup"><span data-stu-id="f0557-208">Captures are stored in numeric **Integer** keys that increase from left to right.</span></span> <span data-ttu-id="f0557-209">Capture `1` 包含所有文字，直到使用者名稱，capture `2` 只包含使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="f0557-209">Capture `1` contains all the text until the username, capture `2` contains just the username.</span></span>

```powershell
$Matches
```

```Output
Name                           Value
----                           -----
2                              CONTOSO\jsmith
1                              The last logged on user was
0                              The last logged on user was CONTOSO\jsmith
```

> [!IMPORTANT]
> <span data-ttu-id="f0557-210">索引 `0` 鍵是 **整數** 。</span><span class="sxs-lookup"><span data-stu-id="f0557-210">The `0` key is an **Integer** .</span></span> <span data-ttu-id="f0557-211">您可以使用任何 **Hashtable** 方法來存取儲存的值。</span><span class="sxs-lookup"><span data-stu-id="f0557-211">You can use any **Hashtable** method to access the value stored.</span></span>
>
> ```
> PS> 'Good Dog' -match 'Dog'
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

#### <a name="named-captures"></a><span data-ttu-id="f0557-212">已命名的捕獲</span><span class="sxs-lookup"><span data-stu-id="f0557-212">Named Captures</span></span>

<span data-ttu-id="f0557-213">依預設，會以遞增的數值順序（從左至右）儲存捕獲。</span><span class="sxs-lookup"><span data-stu-id="f0557-213">By default, captures are stored in ascending numeric order, from left to right.</span></span>
<span data-ttu-id="f0557-214">您也可以將 **名稱** 指派給捕捉群組。</span><span class="sxs-lookup"><span data-stu-id="f0557-214">You can also assign a **name** to a capturing group.</span></span> <span data-ttu-id="f0557-215">這個 **名稱** 會成為 `$Matches` **Hashtable** 自動變數的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="f0557-215">This **name** becomes a key on the `$Matches` **Hashtable** automatic variable.</span></span>

<span data-ttu-id="f0557-216">在「捕獲群組」內，使用 `?<keyname>` 將已捕捉的資料儲存在名為的金鑰下。</span><span class="sxs-lookup"><span data-stu-id="f0557-216">Inside a capturing group, use `?<keyname>` to store captured data under a named key.</span></span>

```
PS> $string = 'The last logged on user was CONTOSO\jsmith'
PS> $string -match 'was (?<domain>.+)\\(?<user>.+)'
True

PS> $Matches

Name                           Value
----                           -----
domain                         CONTOSO
user                           jsmith
0                              was CONTOSO\jsmith

PS> $Matches.domain
CONTOSO

PS> $Matches.user
jsmith
```

<span data-ttu-id="f0557-217">下列範例會儲存 Windows 安全性記錄檔中的最新 **SuccessAudit** 。</span><span class="sxs-lookup"><span data-stu-id="f0557-217">The following example stores the latest **SuccessAudit** from the Windows Security Log.</span></span> <span data-ttu-id="f0557-218">提供的正則運算式會從訊息中解壓縮使用者名稱和網域，並將其儲存在索引鍵的索引鍵上： **N** 代表網域的名稱和 **D** 。</span><span class="sxs-lookup"><span data-stu-id="f0557-218">The provided regular expression extracts the username and domain from the message and stores them under the keys: **N** for name and **D** for domain.</span></span>

```powershell
$log = (Get-EventLog -LogName Security -Newest 1 -InstanceId 4689).message
$r = '(?s).*Account Name:\s*(?<N>.*).*Account Domain:\s*(?<D>[A-Z,0-9]*)'
$log -match $r
```

```Output
True
```

```powershell
$Matches
```

```Output
Name                           Value
----                           -----
D                              CONTOSO
N                              jsmith
0                              A process has exited....
```

<span data-ttu-id="f0557-219">如需詳細資訊，請參閱 [正則運算式中的群組結構](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions)。</span><span class="sxs-lookup"><span data-stu-id="f0557-219">For more information, see [Grouping Constructs in Regular Expressions](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions).</span></span>

#### <a name="substitutions-in-regular-expressions"></a><span data-ttu-id="f0557-220">在規則運算式中執行替代</span><span class="sxs-lookup"><span data-stu-id="f0557-220">Substitutions in Regular Expressions</span></span>

<span data-ttu-id="f0557-221">使用正則運算式搭配 `-replace` 運算子，可讓您使用已捕捉的文字動態取代文字。</span><span class="sxs-lookup"><span data-stu-id="f0557-221">Using the regular expressions with the `-replace` operator allows you to dynamically replace text using captured text.</span></span>

`<input> -replace <original>, <substitute>`

- <span data-ttu-id="f0557-222">`<input>`：要搜尋的字串</span><span class="sxs-lookup"><span data-stu-id="f0557-222">`<input>`: The string to be searched</span></span>
- <span data-ttu-id="f0557-223">`<original>`：用來搜尋輸入字串的正則運算式</span><span class="sxs-lookup"><span data-stu-id="f0557-223">`<original>`: A regular expression used to search the input string</span></span>
- <span data-ttu-id="f0557-224">`<substitute>`：用來取代在輸入字串中找到之相符專案的正則運算式替代運算式。</span><span class="sxs-lookup"><span data-stu-id="f0557-224">`<substitute>`: A regular expression substitution expression to replace matches found in the input string.</span></span>

> [!NOTE]
> <span data-ttu-id="f0557-225">`<original>`和 `<substitute>` 運算元受限於正則運算式引擎的規則，例如字元轉義。</span><span class="sxs-lookup"><span data-stu-id="f0557-225">The `<original>` and `<substitute>` operands are subject to rules of the regular expression engine such as character escaping.</span></span>

<span data-ttu-id="f0557-226">您可以在字串中參考捕捉群組 `<substitute>` 。</span><span class="sxs-lookup"><span data-stu-id="f0557-226">Capturing groups can be referenced in the `<substitute>` string.</span></span> <span data-ttu-id="f0557-227">您可以使用 `$` 群組識別碼之前的字元來完成替代。</span><span class="sxs-lookup"><span data-stu-id="f0557-227">The substitution is done by using the `$` character before the group identifier.</span></span>

<span data-ttu-id="f0557-228">有兩種方式可以參考捕捉群組，也就是依 **編號** 和 **名稱** 。</span><span class="sxs-lookup"><span data-stu-id="f0557-228">Two ways to reference capturing groups are by **Number** and by **Name** .</span></span>

- <span data-ttu-id="f0557-229">依 **編號** -捕獲群組是由左至右編號。</span><span class="sxs-lookup"><span data-stu-id="f0557-229">By **Number** - Capturing Groups are numbered from left to right.</span></span>

  ```powershell
  'John D. Smith' -replace '(\w+) (\w+)\. (\w+)', '$1.$2.$3@contoso.com'
  ```

  ```Output
  John.D.Smith@contoso.com
  ```

- <span data-ttu-id="f0557-230">依 **名稱-捕獲** 群組也可以依名稱參考。</span><span class="sxs-lookup"><span data-stu-id="f0557-230">By **Name** - Capturing Groups can also be referenced by name.</span></span>

  ```powershell
  'CONTOSO\Administrator' -replace '\w+\\(?<user>\w+)', 'FABRIKAM\${user}'
  ```

  ```Output
  FABRIKAM\Administrator
  ```

<span data-ttu-id="f0557-231">`$&`運算式代表所有符合的文字。</span><span class="sxs-lookup"><span data-stu-id="f0557-231">The `$&` expression represents all the text matched.</span></span>

```powershell
'Gobble' -replace 'Gobble', '$& $&'
```

```Output
Gobble Gobble
```

> [!WARNING]
> <span data-ttu-id="f0557-232">由於 `$` 字元是在字串展開中使用，因此您必須使用常值字串搭配替代，或 `$` 在使用雙引號時將字元換用。</span><span class="sxs-lookup"><span data-stu-id="f0557-232">Since the `$` character is used in string expansion, you'll need to use literal strings with substitution, or escape the `$` character when using double quotes.</span></span>
>
> ```powershell
> 'Hello World' -replace '(\w+) \w+', '$1 Universe'
> "Hello World" -replace "(\w+) \w+", "`$1 Universe"
> ```
>
> ```Output
> Hello Universe
> Hello Universe
> ```
>
> <span data-ttu-id="f0557-233">此外，如果您想要將做 `$` 為常值字元，請使用 `$$` 而不是一般的 escape 字元。</span><span class="sxs-lookup"><span data-stu-id="f0557-233">Additionally, if you want to have the `$` as a literal character, use `$$` instead of the normal escape characters.</span></span> <span data-ttu-id="f0557-234">使用雙引號時，仍會將的所有實例都換用， `$` 以避免不正確的替代。</span><span class="sxs-lookup"><span data-stu-id="f0557-234">When using double quotes, still escape all instances of `$` to avoid incorrect substitution.</span></span>
>
> ```powershell
> '5.72' -replace '(.+)', '$$$1'
> "5.72" -replace "(.+)", "`$`$`$1"
> ```
>
> ```Output
> $5.72
> $5.72
> ```

<span data-ttu-id="f0557-235">如需詳細資訊，請參閱 [正則運算式中的替代](/dotnet/standard/base-types/substitutions-in-regular-expressions)。</span><span class="sxs-lookup"><span data-stu-id="f0557-235">For more information, see [Substitutions in Regular Expressions](/dotnet/standard/base-types/substitutions-in-regular-expressions).</span></span>

## <a name="see-also"></a><span data-ttu-id="f0557-236">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0557-236">See also</span></span>

[<span data-ttu-id="f0557-237">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="f0557-237">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="f0557-238">about_Operators</span><span class="sxs-lookup"><span data-stu-id="f0557-238">about_Operators</span></span>](about_Operators.md)
