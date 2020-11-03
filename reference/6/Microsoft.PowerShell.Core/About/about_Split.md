---
description: 說明如何使用 Split 運算子將一或多個字串分割成子字串。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/20/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_split?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Split
ms.openlocfilehash: 520aac1fd1aae4f1f0f4a12a10bc4f5c7f258731
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206851"
---
# <a name="about-split"></a><span data-ttu-id="2406e-104">關於分割</span><span class="sxs-lookup"><span data-stu-id="2406e-104">About Split</span></span>

## <a name="short-description"></a><span data-ttu-id="2406e-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="2406e-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="2406e-106">說明如何使用 Split 運算子將一或多個字串分割成子字串。</span><span class="sxs-lookup"><span data-stu-id="2406e-106">Explains how to use the Split operator to split one or more strings into substrings.</span></span>

## <a name="long-description"></a><span data-ttu-id="2406e-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="2406e-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="2406e-108">Split 運算子會將一個或多個字串分割成子字串。</span><span class="sxs-lookup"><span data-stu-id="2406e-108">The Split operator splits one or more strings into substrings.</span></span> <span data-ttu-id="2406e-109">您可以變更分割作業的下列元素：</span><span class="sxs-lookup"><span data-stu-id="2406e-109">You can change the following elements of the Split operation:</span></span>

- <span data-ttu-id="2406e-110">分隔符號。</span><span class="sxs-lookup"><span data-stu-id="2406e-110">Delimiter.</span></span> <span data-ttu-id="2406e-111">預設值為空白，但您可以指定字元、字串、模式或指定分隔符號的腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="2406e-111">The default is whitespace, but you can specify characters, strings, patterns, or script blocks that specify the delimiter.</span></span> <span data-ttu-id="2406e-112">PowerShell 中的 Split 運算子會在分隔符號中使用正則運算式，而不是使用簡單字元。</span><span class="sxs-lookup"><span data-stu-id="2406e-112">The Split operator in PowerShell uses a regular expression in the delimiter, rather than a simple character.</span></span>
- <span data-ttu-id="2406e-113">子字串的最大數目。</span><span class="sxs-lookup"><span data-stu-id="2406e-113">Maximum number of substrings.</span></span> <span data-ttu-id="2406e-114">預設值是傳回所有子字串。</span><span class="sxs-lookup"><span data-stu-id="2406e-114">The default is to return all substrings.</span></span> <span data-ttu-id="2406e-115">如果您指定的數位小於子字串的數目，則會在最後一個子字串串連其餘的子字串。</span><span class="sxs-lookup"><span data-stu-id="2406e-115">If you specify a number less than the number of substrings, the remaining substrings are concatenated in the last substring.</span></span>
- <span data-ttu-id="2406e-116">選項，可指定符合分隔符號的條件，例如 SimpleMatch 和多行。</span><span class="sxs-lookup"><span data-stu-id="2406e-116">Options that specify the conditions under which the delimiter is matched, such as SimpleMatch and Multiline.</span></span>

## <a name="syntax"></a><span data-ttu-id="2406e-117">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2406e-117">SYNTAX</span></span>

<span data-ttu-id="2406e-118">下圖顯示-split 運算子的語法。</span><span class="sxs-lookup"><span data-stu-id="2406e-118">The following diagram shows the syntax for the -split operator.</span></span>

<span data-ttu-id="2406e-119">參數名稱不會出現在命令中。</span><span class="sxs-lookup"><span data-stu-id="2406e-119">The parameter names do not appear in the command.</span></span> <span data-ttu-id="2406e-120">只包含參數值。</span><span class="sxs-lookup"><span data-stu-id="2406e-120">Include only the parameter values.</span></span> <span data-ttu-id="2406e-121">這些值必須以語法圖表中指定的順序顯示。</span><span class="sxs-lookup"><span data-stu-id="2406e-121">The values must appear in the order specified in the syntax diagram.</span></span>

```
-Split <String>
-Split (<String[]>)
<String> -Split <Delimiter>[,<Max-substrings>[,"<Options>"]]
<String> -Split {<ScriptBlock>} [,<Max-substrings>]
```

<span data-ttu-id="2406e-122">您可以 `-iSplit` `-cSplit` `-split` 在任何二元分割語句中替代或， (包含分隔符號或腳本區塊) 的 split 語句。</span><span class="sxs-lookup"><span data-stu-id="2406e-122">You can substitute `-iSplit` or `-cSplit` for `-split` in any binary Split statement (a Split statement that includes a delimiter or script block).</span></span> <span data-ttu-id="2406e-123">`-iSplit`和 `-split` 運算子不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="2406e-123">The `-iSplit` and `-split` operators are case-insensitive.</span></span> <span data-ttu-id="2406e-124">`-cSplit`運算子會區分大小寫，這表示套用分隔符號規則時，會考慮大小寫。</span><span class="sxs-lookup"><span data-stu-id="2406e-124">The `-cSplit` operator is case-sensitive, meaning that case is considered when the delimiter rules are applied.</span></span>

## <a name="parameters"></a><span data-ttu-id="2406e-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2406e-125">PARAMETERS</span></span>

### <a name="string-or-string"></a><span data-ttu-id="2406e-126">\<String\> 或 \<String[]\></span><span class="sxs-lookup"><span data-stu-id="2406e-126">\<String\> or \<String[]\></span></span>

<span data-ttu-id="2406e-127">指定要分割的一或多個字串。</span><span class="sxs-lookup"><span data-stu-id="2406e-127">Specifies one or more strings to be split.</span></span> <span data-ttu-id="2406e-128">如果您提交多個字串，則會使用相同的分隔符號規則來分割所有字串。</span><span class="sxs-lookup"><span data-stu-id="2406e-128">If you submit multiple strings, all the strings are split using the same delimiter rules.</span></span>

<span data-ttu-id="2406e-129">範例：</span><span class="sxs-lookup"><span data-stu-id="2406e-129">Example:</span></span>

```
-split "red yellow blue green"
red
yellow
blue
green
```

### \<Delimiter\>

<span data-ttu-id="2406e-130">識別子字串結尾的字元。</span><span class="sxs-lookup"><span data-stu-id="2406e-130">The characters that identify the end of a substring.</span></span> <span data-ttu-id="2406e-131">預設分隔符號是空白字元，包括空格和不可列印的字元，例如分行符號 (\` n) 和 tab (\` t) 。</span><span class="sxs-lookup"><span data-stu-id="2406e-131">The default delimiter is whitespace, including spaces and non-printable characters, such as newline (\`n) and tab (\`t).</span></span> <span data-ttu-id="2406e-132">分割字串時，會省略所有子字串中的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="2406e-132">When the strings are split, the delimiter is omitted from all the substrings.</span></span> <span data-ttu-id="2406e-133">範例：</span><span class="sxs-lookup"><span data-stu-id="2406e-133">Example:</span></span>

```
"Lastname:FirstName:Address" -split ":"
Lastname
FirstName
Address
```

<span data-ttu-id="2406e-134">根據預設，會從結果中省略分隔符號。</span><span class="sxs-lookup"><span data-stu-id="2406e-134">By default, the delimiter is omitted from the results.</span></span> <span data-ttu-id="2406e-135">若要保留全部或部分的分隔符號，請以括弧括住您想要保留的部分。</span><span class="sxs-lookup"><span data-stu-id="2406e-135">To preserve all or part of the delimiter, enclose in parentheses the part that you want to preserve.</span></span>
<span data-ttu-id="2406e-136">如果已 \<Max-substrings\> 加入參數，則當您的命令分割集合時，會優先使用此參數。</span><span class="sxs-lookup"><span data-stu-id="2406e-136">If the \<Max-substrings\> parameter is added, this takes precedence when your command splits up the collection.</span></span> <span data-ttu-id="2406e-137">如果您選擇包含分隔符號作為輸出的一部分，此命令會傳回分隔符號作為輸出的一部分;但是，將字串分割以傳回分隔符號作為輸出的一部分，並不會被視為分割。</span><span class="sxs-lookup"><span data-stu-id="2406e-137">If you opt to include a delimiter as part of the output, the command returns the delimiter as part of the output; however, splitting the string to return the delimiter as part of output does not count as a split.</span></span>

<span data-ttu-id="2406e-138">範例：</span><span class="sxs-lookup"><span data-stu-id="2406e-138">Examples:</span></span>

```
"Lastname:FirstName:Address" -split "(:)"
Lastname
:
FirstName
:
Address

"Lastname/:/FirstName/:/Address" -split "/(:)/"
Lastname
:
FirstName
:
Address
```

<span data-ttu-id="2406e-139">在下列範例中， \<Max-substrings\> 會設為3。</span><span class="sxs-lookup"><span data-stu-id="2406e-139">In the following example, \<Max-substrings\> is set to 3.</span></span> <span data-ttu-id="2406e-140">這會產生三個字串值的分割，但產生的輸出中總共有五個字串：分隔符號會包含在分割之後，直到達到三個子字串的最大值為止。</span><span class="sxs-lookup"><span data-stu-id="2406e-140">This results in three splits of the string values, but a total of five strings in the resulting output; the delimiter is included after the splits, until the maximum of three substrings is reached.</span></span> <span data-ttu-id="2406e-141">最後一個子字串中的其他分隔符號會成為子字串的一部分。</span><span class="sxs-lookup"><span data-stu-id="2406e-141">Additional delimiters in the final substring become part of the substring.</span></span>

```powershell
'Chocolate-Vanilla-Strawberry-Blueberry' -split '(-)', 3
```

```output
Chocolate
-
Vanilla
-
Strawberry-Blueberry
```

### \<Max-substrings\>

<span data-ttu-id="2406e-142">指定分割字串的最大次數。</span><span class="sxs-lookup"><span data-stu-id="2406e-142">Specifies the maximum number of times that a string is split.</span></span> <span data-ttu-id="2406e-143">預設值是依分隔符號分割的所有子字串。</span><span class="sxs-lookup"><span data-stu-id="2406e-143">The default is all the substrings split by the delimiter.</span></span> <span data-ttu-id="2406e-144">如果有更多的子字串，它們會串連到最後一個子字串。</span><span class="sxs-lookup"><span data-stu-id="2406e-144">If there are more substrings, they are concatenated to the final substring.</span></span> <span data-ttu-id="2406e-145">如果有較少的子字串，則會傳回所有子字串。</span><span class="sxs-lookup"><span data-stu-id="2406e-145">If there are fewer substrings, all the substrings are returned.</span></span> <span data-ttu-id="2406e-146">0和負值值會傳回所有子字串。</span><span class="sxs-lookup"><span data-stu-id="2406e-146">A value of 0 and negative values return all the substrings.</span></span>

<span data-ttu-id="2406e-147">Max-子字串不會指定傳回的最大物件數目;其值等於分割字串的最大次數。</span><span class="sxs-lookup"><span data-stu-id="2406e-147">Max-substrings does not specify the maximum number of objects that are returned; its value equals the maximum number of times that a string is split.</span></span>
<span data-ttu-id="2406e-148">如果您送出多個字串 (字串陣列) 至分割運算子，則最大的子字串限制會分別套用至每個字串。</span><span class="sxs-lookup"><span data-stu-id="2406e-148">If you submit more than one string (an array of strings) to the Split operator , the Max-substrings limit is applied to each string separately.</span></span>

<span data-ttu-id="2406e-149">範例：</span><span class="sxs-lookup"><span data-stu-id="2406e-149">Example:</span></span>

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split ",", 5
```

```output
Mercury
Venus
Earth
Mars
Jupiter,Saturn,Uranus,Neptune
```

### \<ScriptBlock\>

<span data-ttu-id="2406e-150">運算式，指定套用分隔符號的規則。</span><span class="sxs-lookup"><span data-stu-id="2406e-150">An expression that specifies rules for applying the delimiter.</span></span> <span data-ttu-id="2406e-151">運算式必須評估為 $true 或 $false。</span><span class="sxs-lookup"><span data-stu-id="2406e-151">The expression must evaluate to $true or $false.</span></span> <span data-ttu-id="2406e-152">以大括弧括住腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="2406e-152">Enclose the script block in braces.</span></span>

<span data-ttu-id="2406e-153">範例：</span><span class="sxs-lookup"><span data-stu-id="2406e-153">Example:</span></span>

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split {$_ -eq "e" -or $_ -eq "p"}
```

```output
M
rcury,V
nus,
arth,Mars,Ju
it
r,Saturn,Uranus,N

tun
```

### \<Options\>

<span data-ttu-id="2406e-154">將選項名稱括在引號中。</span><span class="sxs-lookup"><span data-stu-id="2406e-154">Enclose the option name in quotation marks.</span></span> <span data-ttu-id="2406e-155">只有在 \<Max-substrings\> 語句中使用參數時，選項才有效。</span><span class="sxs-lookup"><span data-stu-id="2406e-155">Options are valid only when the \<Max-substrings\> parameter is used in the statement.</span></span>

<span data-ttu-id="2406e-156">Options 參數的語法為：</span><span class="sxs-lookup"><span data-stu-id="2406e-156">The syntax for the Options parameter is:</span></span>

```
"SimpleMatch [,IgnoreCase]"

"[RegexMatch] [,IgnoreCase] [,CultureInvariant]
[,IgnorePatternWhitespace] [,ExplicitCapture]
[,Singleline | ,Multiline]"
```

<span data-ttu-id="2406e-157">SimpleMatch 選項如下：</span><span class="sxs-lookup"><span data-stu-id="2406e-157">The SimpleMatch options are:</span></span>

- <span data-ttu-id="2406e-158">**SimpleMatch** ：評估分隔符號時，請使用簡單的字串比較。</span><span class="sxs-lookup"><span data-stu-id="2406e-158">**SimpleMatch** : Use simple string comparison when evaluating the delimiter.</span></span> <span data-ttu-id="2406e-159">無法與 RegexMatch 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="2406e-159">Cannot be used with RegexMatch.</span></span>
- <span data-ttu-id="2406e-160">**IgnoreCase** ：強制比對不區分大小寫，即使已指定-cSplit 運算子也是如此。</span><span class="sxs-lookup"><span data-stu-id="2406e-160">**IgnoreCase** : Forces case-insensitive matching, even if the -cSplit operator is specified.</span></span>

<span data-ttu-id="2406e-161">RegexMatch 選項如下：</span><span class="sxs-lookup"><span data-stu-id="2406e-161">The RegexMatch options are:</span></span>

- <span data-ttu-id="2406e-162">**RegexMatch** ：使用正則運算式比對來評估分隔符號。</span><span class="sxs-lookup"><span data-stu-id="2406e-162">**RegexMatch** : Use regular expression matching to evaluate the delimiter.</span></span> <span data-ttu-id="2406e-163">此為預設行為。</span><span class="sxs-lookup"><span data-stu-id="2406e-163">This is the default behavior.</span></span> <span data-ttu-id="2406e-164">無法與 SimpleMatch 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="2406e-164">Cannot be used with SimpleMatch.</span></span>
- <span data-ttu-id="2406e-165">**IgnoreCase** ：強制比對不區分大小寫，即使已指定-cSplit 運算子也是如此。</span><span class="sxs-lookup"><span data-stu-id="2406e-165">**IgnoreCase** : Forces case-insensitive matching, even if the -cSplit operator is specified.</span></span>
- <span data-ttu-id="2406e-166">**>RegExoptions.cultureinvariant** ：評估分隔符號時，會忽略語言的文化差異。</span><span class="sxs-lookup"><span data-stu-id="2406e-166">**CultureInvariant** : Ignores cultural differences in language when evaluting the delimiter.</span></span> <span data-ttu-id="2406e-167">僅適用于 RegexMatch。</span><span class="sxs-lookup"><span data-stu-id="2406e-167">Valid only with RegexMatch.</span></span>
- <span data-ttu-id="2406e-168">**Regexoptions.ignorepatternwhitespace** ：忽略以數位正負號 ( # ) 標記的非轉義空白字元和批註。</span><span class="sxs-lookup"><span data-stu-id="2406e-168">**IgnorePatternWhitespace** : Ignores unescaped whitespace and comments marked with the number sign (#).</span></span> <span data-ttu-id="2406e-169">僅適用于 RegexMatch。</span><span class="sxs-lookup"><span data-stu-id="2406e-169">Valid only with RegexMatch.</span></span>
- <span data-ttu-id="2406e-170">**多** 行：多行模式會強制 `^` 並 `$` 比對每一行的開頭，而不是輸入字串的開頭和結尾。</span><span class="sxs-lookup"><span data-stu-id="2406e-170">**Multiline** : Multiline mode forces `^` and `$` to match the beginning end of every line instead of the beginning and end of the input string.</span></span>
- <span data-ttu-id="2406e-171">**單行** ：單行模式會將輸入字串視為 *單行* 。</span><span class="sxs-lookup"><span data-stu-id="2406e-171">**Singleline** : Singleline mode treats the input string as a *SingleLine* .</span></span>
  <span data-ttu-id="2406e-172">它會強制 `.` 字元符合每個字元 (包括分行符號) ，而不是比對分行符號以外的每個字元 `\n` 。</span><span class="sxs-lookup"><span data-stu-id="2406e-172">It forces the `.` character to match every character (including newlines), instead of matching every character EXCEPT the newline `\n`.</span></span>
- <span data-ttu-id="2406e-173">**>RegExoptions.explicitcapture** ：忽略非命名的比對群組，以便只傳回結果清單中的明確 capture 群組。</span><span class="sxs-lookup"><span data-stu-id="2406e-173">**ExplicitCapture** : Ignores non-named match groups so that only explicit capture groups are returned in the result list.</span></span> <span data-ttu-id="2406e-174">僅適用于 RegexMatch。</span><span class="sxs-lookup"><span data-stu-id="2406e-174">Valid only with RegexMatch.</span></span>

## <a name="unary-and-binary-split-operators"></a><span data-ttu-id="2406e-175">一元和二元分割運算子</span><span class="sxs-lookup"><span data-stu-id="2406e-175">UNARY and BINARY SPLIT OPERATORS</span></span>

<span data-ttu-id="2406e-176">一元分割運算子 (`-split <string>`) 的優先順序高於逗號。</span><span class="sxs-lookup"><span data-stu-id="2406e-176">The unary split operator (`-split <string>`) has higher precedence than a comma.</span></span> <span data-ttu-id="2406e-177">如此一來，如果您將以逗號分隔的字串清單提交給一元分割運算子，則只有第一個字串在第一個逗號) 之前 (會被分割。</span><span class="sxs-lookup"><span data-stu-id="2406e-177">As a result, if you submit a comma-separated list of strings to the unary split operator, only the first string (before the first comma) is split.</span></span>

<span data-ttu-id="2406e-178">您可以使用下列其中一種模式來分割一個以上的字串：</span><span class="sxs-lookup"><span data-stu-id="2406e-178">Use one of the following patterns to split more than one string:</span></span>

- <span data-ttu-id="2406e-179">使用二元分割運算子 (\<string[]\> 分割 \<delimiter\>) </span><span class="sxs-lookup"><span data-stu-id="2406e-179">Use the binary split operator (\<string[]\> -split \<delimiter\>)</span></span>
- <span data-ttu-id="2406e-180">將所有字串括在括弧中</span><span class="sxs-lookup"><span data-stu-id="2406e-180">Enclose all the strings in parentheses</span></span>
- <span data-ttu-id="2406e-181">將字串儲存在變數中，然後將變數提交給分割運算子</span><span class="sxs-lookup"><span data-stu-id="2406e-181">Store the strings in a variable then submit the variable to the split operator</span></span>

<span data-ttu-id="2406e-182">請考慮下列範例：</span><span class="sxs-lookup"><span data-stu-id="2406e-182">Consider the following example:</span></span>

```
PS> -split "1 2", "a b"
1
2
a b
```

```
PS> "1 2", "a b" -split " "
1
2
a
b
```

```
PS> -split ("1 2", "a b")
1
2
a
b
```

```
PS> $a = "1 2", "a b"
PS> -split $a
1
2
a
b
```

## <a name="examples"></a><span data-ttu-id="2406e-183">範例</span><span class="sxs-lookup"><span data-stu-id="2406e-183">EXAMPLES</span></span>

<span data-ttu-id="2406e-184">下列語句會將字串分割為空格。</span><span class="sxs-lookup"><span data-stu-id="2406e-184">The following statement splits the string at whitespace.</span></span>

```powershell
-split "Windows PowerShell 2.0`nWindows PowerShell with remoting"
```

```output

Windows
PowerShell
2.0
Windows
PowerShell
with
remoting
```

<span data-ttu-id="2406e-185">下列語句會以任何逗號分隔字串。</span><span class="sxs-lookup"><span data-stu-id="2406e-185">The following statement splits the string at any comma.</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split ','
```

```output
Mercury
Venus
Earth
Mars
Jupiter
Saturn
Uranus
Neptune
```

<span data-ttu-id="2406e-186">下列語句會將字串分割為 "er" 模式。</span><span class="sxs-lookup"><span data-stu-id="2406e-186">The following statement splits the string at the pattern "er".</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split 'er'
```

```output
M
cury,Venus,Earth,Mars,Jupit
,Saturn,Uranus,Neptune
```

<span data-ttu-id="2406e-187">下列語句會以字母 "N" 執行區分大小寫的分割。</span><span class="sxs-lookup"><span data-stu-id="2406e-187">The following statement performs a case-sensitive split at the letter "N".</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -cSplit 'N'
```

```output
Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,
eptune
```

<span data-ttu-id="2406e-188">下列語句會將字串分割為 "e" 和 "t"。</span><span class="sxs-lookup"><span data-stu-id="2406e-188">The following statement splits the string at "e" and "t".</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split '[et]'
```

```output
M
rcury,V
nus,
ar
h,Mars,Jupi

r,Sa
urn,Uranus,N
p
un
```

<span data-ttu-id="2406e-189">下列語句會在 "e" 和 "r" 分割字串，但會將產生的子字串限制為六個子字串。</span><span class="sxs-lookup"><span data-stu-id="2406e-189">The following statement splits the string at "e" and "r", but limits the resulting substrings to six substrings.</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split '[er]', 6
```

```output
M

cu
y,V
nus,
arth,Mars,Jupiter,Saturn,Uranus,Neptune
```

<span data-ttu-id="2406e-190">下列語句會將字串分割成三個子字串。</span><span class="sxs-lookup"><span data-stu-id="2406e-190">The following statement splits a string into three substrings.</span></span>

```powershell
"a,b,c,d,e,f,g,h" -split ",", 3
```

```output
a
b
c,d,e,f,g,h
```

<span data-ttu-id="2406e-191">下列語句會將兩個字串分割成三個子字串。</span><span class="sxs-lookup"><span data-stu-id="2406e-191">The following statement splits two strings into three substrings.</span></span>
<span data-ttu-id="2406e-192"> (限制會個別套用至每個字串。 ) </span><span class="sxs-lookup"><span data-stu-id="2406e-192">(The limit is applied to each string independently.)</span></span>

```powershell
"a,b,c,d", "e,f,g,h" -split ",", 3
```

```output
a
b
c,d
e
f
g,h
```

<span data-ttu-id="2406e-193">下列語句會在第一個數位分割此處的每一行。</span><span class="sxs-lookup"><span data-stu-id="2406e-193">The following statement splits each line in the here-string at the first digit.</span></span> <span data-ttu-id="2406e-194">它會使用多行選項來辨識每一行和字串的開頭。</span><span class="sxs-lookup"><span data-stu-id="2406e-194">It uses the Multiline option to recognize the beginning of each line and string.</span></span>

<span data-ttu-id="2406e-195">0代表最大子字串參數的 "return all" 值。</span><span class="sxs-lookup"><span data-stu-id="2406e-195">The 0 represents the "return all" value of the Max-substrings parameter.</span></span> <span data-ttu-id="2406e-196">只有在指定最大的子字串值時，您才能使用選項，例如多行。</span><span class="sxs-lookup"><span data-stu-id="2406e-196">You can use options, such as Multiline, only when the Max-substrings value is specified.</span></span>

```powershell
$a = @'
1The first line.
2The second line.
3The third of three lines.
'@
$a -split "^\d", 0, "multiline"
```

```output

The first line.

The second line.

The third of three lines.
```

<span data-ttu-id="2406e-197">下列語句會使用反斜線字元來將點 ( ) 分隔符號。</span><span class="sxs-lookup"><span data-stu-id="2406e-197">The following statement uses the backslash character to escape the dot (.) delimiter.</span></span>

<span data-ttu-id="2406e-198">使用預設值 RegexMatch 時，以引號括住的點 ( ".") 會被解讀來比對分行符號以外的任何字元。</span><span class="sxs-lookup"><span data-stu-id="2406e-198">With the default, RegexMatch, the dot enclosed in quotation marks (".") is interpreted to match any character except for a newline character.</span></span> <span data-ttu-id="2406e-199">因此，Split 語句會針對分行符號以外的每個字元傳回空白行。</span><span class="sxs-lookup"><span data-stu-id="2406e-199">As a result, the Split statement returns a blank line for every character except newline.</span></span>

```powershell
"This.is.a.test" -split "\."
```

```output
This
is
a
test
```

<span data-ttu-id="2406e-200">下列語句會使用 SimpleMatch 選項來指示-split 運算子，將點 (。 ) 分隔符號。</span><span class="sxs-lookup"><span data-stu-id="2406e-200">The following statement uses the SimpleMatch option to direct the -split operator to interpret the dot (.) delimiter literally.</span></span>

<span data-ttu-id="2406e-201">0代表最大子字串參數的 "return all" 值。</span><span class="sxs-lookup"><span data-stu-id="2406e-201">The 0 represents the "return all" value of the Max-substrings parameter.</span></span> <span data-ttu-id="2406e-202">只有在指定最大的子字串值時，您才能使用選項（例如 SimpleMatch）。</span><span class="sxs-lookup"><span data-stu-id="2406e-202">You can use options, such as SimpleMatch, only when the Max-substrings value is specified.</span></span>

```powershell
"This.is.a.test" -split ".", 0, "simplematch"
```

```output
This
is
a
test
```

<span data-ttu-id="2406e-203">下列語句會根據變數的值，將字串分割成兩個分隔符號的其中一個。</span><span class="sxs-lookup"><span data-stu-id="2406e-203">The following statement splits the string at one of two delimiters, depending on the value of a variable.</span></span>

```powershell
$i = 1
$c = "LastName, FirstName; Address, City, State, Zip"
$c -split $(if ($i -lt 1) {","} else {";"})
```

```output
LastName, FirstName
 Address, City, State, Zip
```

## <a name="see-also"></a><span data-ttu-id="2406e-204">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2406e-204">SEE ALSO</span></span>

[<span data-ttu-id="2406e-205">Split-Path</span><span class="sxs-lookup"><span data-stu-id="2406e-205">Split-Path</span></span>](xref:Microsoft.PowerShell.Management.Split-Path)

[<span data-ttu-id="2406e-206">about_Operators</span><span class="sxs-lookup"><span data-stu-id="2406e-206">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="2406e-207">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="2406e-207">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="2406e-208">about_Join</span><span class="sxs-lookup"><span data-stu-id="2406e-208">about_Join</span></span>](about_Join.md)
