---
description: 描述在 PowerShell 中使用單引號和雙引號的規則。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/05/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_quoting_rules?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Quoting_Rules
ms.openlocfilehash: 3a858039a9128235d1b920223ca0fcc3d0b0f6c0
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207596"
---
# <a name="about-quoting-rules"></a><span data-ttu-id="12027-104">關於引號規則</span><span class="sxs-lookup"><span data-stu-id="12027-104">About Quoting Rules</span></span>

## <a name="short-description"></a><span data-ttu-id="12027-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="12027-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="12027-106">描述在 PowerShell 中使用單引號和雙引號的規則。</span><span class="sxs-lookup"><span data-stu-id="12027-106">Describes rules for using single and double quotation marks in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="12027-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="12027-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="12027-108">用引號來指定常值字串。</span><span class="sxs-lookup"><span data-stu-id="12027-108">Quotation marks are used to specify a literal string.</span></span> <span data-ttu-id="12027-109">您可以用單引號括住字串 (的 `'`) 或雙引號 (`"`) 。</span><span class="sxs-lookup"><span data-stu-id="12027-109">You can enclose a string in single quotation marks (`'`) or double quotation marks (`"`).</span></span>

<span data-ttu-id="12027-110">引號也用來建立這個字串。</span><span class="sxs-lookup"><span data-stu-id="12027-110">Quotation marks are also used to create a here-string.</span></span> <span data-ttu-id="12027-111">這裡的字串是以單引號括住的單引號或雙引號括住的字串，其中的引號會以字面方式來解讀。</span><span class="sxs-lookup"><span data-stu-id="12027-111">A here-string is a single-quoted or double-quoted string in which quotation marks are interpreted literally.</span></span> <span data-ttu-id="12027-112">在此，字串可以橫跨多行。</span><span class="sxs-lookup"><span data-stu-id="12027-112">A here-string can span multiple lines.</span></span> <span data-ttu-id="12027-113">在此字串中的所有行都會被視為字串，即使它們不是以引號括住也是一樣。</span><span class="sxs-lookup"><span data-stu-id="12027-113">All the lines in a here-string are interpreted as strings, even though they are not enclosed in quotation marks.</span></span>

<span data-ttu-id="12027-114">在 [遠端電腦的命令] 中，引號會定義在遠端電腦上執行之命令的部分。</span><span class="sxs-lookup"><span data-stu-id="12027-114">In commands to remote computers, quotation marks define the parts of the command that are run on the remote computer.</span></span> <span data-ttu-id="12027-115">在遠端會話中，引號也會決定是否要先在本機電腦或遠端電腦上解釋命令中的變數。</span><span class="sxs-lookup"><span data-stu-id="12027-115">In a remote session, quotation marks also determine whether the variables in a command are interpreted first on the local computer or on the remote computer.</span></span>

### <a name="single-and-double-quoted-strings"></a><span data-ttu-id="12027-116">單引號和雙引號括住的字串</span><span class="sxs-lookup"><span data-stu-id="12027-116">SINGLE AND DOUBLE-QUOTED STRINGS</span></span>

<span data-ttu-id="12027-117">當您以雙引號括住字串， (以雙引號括住的字串) 時，會以變數的值取代前面加上貨幣符號 () 的變數名稱， `$` 然後將字串傳遞給命令進行處理。</span><span class="sxs-lookup"><span data-stu-id="12027-117">When you enclose a string in double quotation marks (a double-quoted string), variable names that are preceded by a dollar sign (`$`) are replaced with the variable's value before the string is passed to the command for processing.</span></span>

<span data-ttu-id="12027-118">例如：</span><span class="sxs-lookup"><span data-stu-id="12027-118">For example:</span></span>

```powershell
$i = 5
"The value of $i is $i."
```

<span data-ttu-id="12027-119">此命令的輸出為：</span><span class="sxs-lookup"><span data-stu-id="12027-119">The output of this command is:</span></span>

```Output
The value of 5 is 5.
```

<span data-ttu-id="12027-120">此外，在以雙引號括住的字串中，會評估運算式，並在字串中插入結果。</span><span class="sxs-lookup"><span data-stu-id="12027-120">Also, in a double-quoted string, expressions are evaluated, and the result is inserted in the string.</span></span> <span data-ttu-id="12027-121">例如：</span><span class="sxs-lookup"><span data-stu-id="12027-121">For example:</span></span>

```powershell
"The value of $(2+3) is 5."
```

<span data-ttu-id="12027-122">此命令的輸出為：</span><span class="sxs-lookup"><span data-stu-id="12027-122">The output of this command is:</span></span>

```Output
The value of 5 is 5.
```

<span data-ttu-id="12027-123">當您以單引號括住字串 (單引號字串) 時，字串就會與您輸入時完全一樣地傳遞至命令。</span><span class="sxs-lookup"><span data-stu-id="12027-123">When you enclose a string in single-quotation marks (a single-quoted string), the string is passed to the command exactly as you type it.</span></span> <span data-ttu-id="12027-124">不會執行任何替代。</span><span class="sxs-lookup"><span data-stu-id="12027-124">No substitution is performed.</span></span> <span data-ttu-id="12027-125">例如：</span><span class="sxs-lookup"><span data-stu-id="12027-125">For example:</span></span>

```powershell
$i = 5
'The value of $i is $i.'
```

<span data-ttu-id="12027-126">此命令的輸出為：</span><span class="sxs-lookup"><span data-stu-id="12027-126">The output of this command is:</span></span>

```Output
The value $i is $i.
```

<span data-ttu-id="12027-127">同樣地，不會評估以單引號括住的字串中的運算式。</span><span class="sxs-lookup"><span data-stu-id="12027-127">Similarly, expressions in single-quoted strings are not evaluated.</span></span> <span data-ttu-id="12027-128">它們會被視為常值。</span><span class="sxs-lookup"><span data-stu-id="12027-128">They are interpreted as literals.</span></span> <span data-ttu-id="12027-129">例如：</span><span class="sxs-lookup"><span data-stu-id="12027-129">For example:</span></span>

```powershell
'The value of $(2+3) is 5.'
```

<span data-ttu-id="12027-130">此命令的輸出為：</span><span class="sxs-lookup"><span data-stu-id="12027-130">The output of this command is:</span></span>

```Output
The value of $(2+3) is 5.
```

<span data-ttu-id="12027-131">若要避免在以雙引號括住的字串中替換變數值，請使用倒引號字元 (`` ` ``) # B2 ASCII 96) ，也就是 PowerShell escape 字元。</span><span class="sxs-lookup"><span data-stu-id="12027-131">To prevent the substitution of a variable value in a double-quoted string, use the backtick character (`` ` ``)(ASCII 96), which is the PowerShell escape character.</span></span>

<span data-ttu-id="12027-132">在下列範例中，第一個 $i 變數之前的倒引號字元會防止 PowerShell 以其值取代變數名稱。</span><span class="sxs-lookup"><span data-stu-id="12027-132">In the following example, the backtick character that precedes the first $i variable prevents PowerShell from replacing the variable name with its value.</span></span>
<span data-ttu-id="12027-133">例如：</span><span class="sxs-lookup"><span data-stu-id="12027-133">For example:</span></span>

```powershell
$i = 5
"The value of `$i is $i."
```

<span data-ttu-id="12027-134">此命令的輸出為：</span><span class="sxs-lookup"><span data-stu-id="12027-134">The output of this command is:</span></span>

```Output
The value $i is 5.
```

<span data-ttu-id="12027-135">若要讓雙引號出現在字串中，請使用單引號括住整個字串。</span><span class="sxs-lookup"><span data-stu-id="12027-135">To make double-quotation marks appear in a string, enclose the entire string in single quotation marks.</span></span> <span data-ttu-id="12027-136">例如：</span><span class="sxs-lookup"><span data-stu-id="12027-136">For example:</span></span>

```powershell
'As they say, "live and learn."'
```

<span data-ttu-id="12027-137">此命令的輸出為：</span><span class="sxs-lookup"><span data-stu-id="12027-137">The output of this command is:</span></span>

```Output
As they say, "live and learn."
```

<span data-ttu-id="12027-138">您也可以用雙引號括住的字串括住單引號字串。</span><span class="sxs-lookup"><span data-stu-id="12027-138">You can also enclose a single-quoted string in a double-quoted string.</span></span> <span data-ttu-id="12027-139">例如：</span><span class="sxs-lookup"><span data-stu-id="12027-139">For example:</span></span>

```powershell
"As they say, 'live and learn.'"
```

<span data-ttu-id="12027-140">此命令的輸出為：</span><span class="sxs-lookup"><span data-stu-id="12027-140">The output of this command is:</span></span>

```Output
As they say, 'live and learn.'
```

<span data-ttu-id="12027-141">或者，以雙引號括住雙引號的雙引號。</span><span class="sxs-lookup"><span data-stu-id="12027-141">Or, double the quotation marks around a double-quoted phrase.</span></span> <span data-ttu-id="12027-142">例如：</span><span class="sxs-lookup"><span data-stu-id="12027-142">For example:</span></span>

```powershell
"As they say, ""live and learn."""
```

<span data-ttu-id="12027-143">此命令的輸出為：</span><span class="sxs-lookup"><span data-stu-id="12027-143">The output of this command is:</span></span>

```Output
As they say, "live and learn."
```

<span data-ttu-id="12027-144">若要在單引號字串中加入單引號，請使用第二個連續單引號。</span><span class="sxs-lookup"><span data-stu-id="12027-144">To include a single quotation mark in a single-quoted string, use a second consecutive single quote.</span></span> <span data-ttu-id="12027-145">例如：</span><span class="sxs-lookup"><span data-stu-id="12027-145">For example:</span></span>

```powershell
'don''t'
```

<span data-ttu-id="12027-146">此命令的輸出為：</span><span class="sxs-lookup"><span data-stu-id="12027-146">The output of this command is:</span></span>

```Output
don't
```

<span data-ttu-id="12027-147">若要強制 PowerShell 逐字解讀雙引號，請使用倒引號字元。</span><span class="sxs-lookup"><span data-stu-id="12027-147">To force PowerShell to interpret a double quotation mark literally, use a backtick character.</span></span> <span data-ttu-id="12027-148">這可防止 PowerShell 將引號解讀為字串分隔符號。</span><span class="sxs-lookup"><span data-stu-id="12027-148">This prevents PowerShell from interpreting the quotation mark as a string delimiter.</span></span> <span data-ttu-id="12027-149">例如：</span><span class="sxs-lookup"><span data-stu-id="12027-149">For example:</span></span>

```powershell
PS> "Use a quotation mark (`") to begin a string."
Use a quotation mark (") to begin a string.
PS> 'Use a quotation mark (`") to begin a string.'
Use a quotation mark (`") to begin a string.
```

<span data-ttu-id="12027-150">因為單引號字串的內容是以字面方式解讀，所以您會將倒引號字元視為常值字元，並顯示在輸出中。</span><span class="sxs-lookup"><span data-stu-id="12027-150">Because the contents of single-quoted strings are interpreted literally, you the backtick character is treated as a literal character and displayed in the output.</span></span>

### <a name="here-strings"></a><span data-ttu-id="12027-151">這裡-字串</span><span class="sxs-lookup"><span data-stu-id="12027-151">HERE-STRINGS</span></span>

<span data-ttu-id="12027-152">這裡的引號規則-字串略有不同。</span><span class="sxs-lookup"><span data-stu-id="12027-152">The quotation rules for here-strings are slightly different.</span></span>

<span data-ttu-id="12027-153">這裡的字串是以單引號括住的單引號或雙引號括住的字串，其中的引號會以字面方式來解讀。</span><span class="sxs-lookup"><span data-stu-id="12027-153">A here-string is a single-quoted or double-quoted string in which quotation marks are interpreted literally.</span></span> <span data-ttu-id="12027-154">在此，字串可以橫跨多行。</span><span class="sxs-lookup"><span data-stu-id="12027-154">A here-string can span multiple lines.</span></span> <span data-ttu-id="12027-155">在此字串中的所有行都會被視為字串，即使它們不是以引號括住。</span><span class="sxs-lookup"><span data-stu-id="12027-155">All the lines in a here-string are interpreted as strings even though they are not enclosed in quotation marks.</span></span>

<span data-ttu-id="12027-156">如同一般字串，變數會以雙引號括住的值取代。</span><span class="sxs-lookup"><span data-stu-id="12027-156">Like regular strings, variables are replaced by their values in double-quoted here-strings.</span></span> <span data-ttu-id="12027-157">在這裡以單引號括住的字串中，不會以變數的值取代變數。</span><span class="sxs-lookup"><span data-stu-id="12027-157">In single-quoted here-strings, variables are not replaced by their values.</span></span>

<span data-ttu-id="12027-158">您可以在這裡使用任何文字的字串，但它們對下列種類的文字特別有用：</span><span class="sxs-lookup"><span data-stu-id="12027-158">You can use here-strings for any text, but they are particularly useful for the following kinds of text:</span></span>

- <span data-ttu-id="12027-159">包含常值引號的文字</span><span class="sxs-lookup"><span data-stu-id="12027-159">Text that contains literal quotation marks</span></span>
- <span data-ttu-id="12027-160">多行文字，例如 HTML 或 XML 中的文字</span><span class="sxs-lookup"><span data-stu-id="12027-160">Multiple lines of text, such as the text in an HTML or XML</span></span>
- <span data-ttu-id="12027-161">腳本或函數檔的解說文字</span><span class="sxs-lookup"><span data-stu-id="12027-161">The Help text for a script or function document</span></span>

<span data-ttu-id="12027-162">這裡的字串可以是下列其中一種格式，其中 `<Enter>` 代表當您按下 <kbd>enter</kbd> 鍵時加入的換行字元或分行符號。</span><span class="sxs-lookup"><span data-stu-id="12027-162">A here-string can have either of the following formats, where `<Enter>` represents the linefeed or newline hidden character that is added when you press the <kbd>ENTER</kbd> key.</span></span>

<span data-ttu-id="12027-163">雙引號：</span><span class="sxs-lookup"><span data-stu-id="12027-163">Double-quotes:</span></span>

```
@"<Enter>
<string> [string] ...<Enter>
"@
```

<span data-ttu-id="12027-164">單引號：</span><span class="sxs-lookup"><span data-stu-id="12027-164">Single-quotes:</span></span>

```
@'<Enter>
<string> [string] ...<Enter>
'@
```

<span data-ttu-id="12027-165">無論是哪一種格式，右引號都必須是該行中的第一個字元。</span><span class="sxs-lookup"><span data-stu-id="12027-165">In either format, the closing quotation mark must be the first character in the line.</span></span>

<span data-ttu-id="12027-166">這裡的字串包含兩個隱藏字元之間的所有文字。</span><span class="sxs-lookup"><span data-stu-id="12027-166">A here-string contains all the text between the two hidden characters.</span></span> <span data-ttu-id="12027-167">在此字串中，所有引號都會以字面方式來解讀。</span><span class="sxs-lookup"><span data-stu-id="12027-167">In the here-string, all quotation marks are interpreted literally.</span></span> <span data-ttu-id="12027-168">例如：</span><span class="sxs-lookup"><span data-stu-id="12027-168">For example:</span></span>

```powershell
@"
For help, type "get-help"
"@
```

<span data-ttu-id="12027-169">此命令的輸出為：</span><span class="sxs-lookup"><span data-stu-id="12027-169">The output of this command is:</span></span>

```Output
For help, type "get-help"
```

<span data-ttu-id="12027-170">使用這裡的字串可以簡化在命令中使用字串的方式。</span><span class="sxs-lookup"><span data-stu-id="12027-170">Using a here-string can simplify using a string in a command.</span></span> <span data-ttu-id="12027-171">例如：</span><span class="sxs-lookup"><span data-stu-id="12027-171">For example:</span></span>

```powershell
@"
Use a quotation mark (') to begin a string.
"@
```

<span data-ttu-id="12027-172">此命令的輸出為：</span><span class="sxs-lookup"><span data-stu-id="12027-172">The output of this command is:</span></span>

```Output
Use a quotation mark (') to begin a string.
```

<span data-ttu-id="12027-173">在這裡以單引號括住的字串中，變數會完全解讀和重現。</span><span class="sxs-lookup"><span data-stu-id="12027-173">In single-quoted here-strings, variables are interpreted literally and reproduced exactly.</span></span> <span data-ttu-id="12027-174">例如：</span><span class="sxs-lookup"><span data-stu-id="12027-174">For example:</span></span>

```powershell
@'
The $profile variable contains the path
of your PowerShell profile.
'@
```

<span data-ttu-id="12027-175">此命令的輸出為：</span><span class="sxs-lookup"><span data-stu-id="12027-175">The output of this command is:</span></span>

```Output
The $profile variable contains the path
of your PowerShell profile.
```

<span data-ttu-id="12027-176">以雙引號括住的字串，變數會以其值取代。</span><span class="sxs-lookup"><span data-stu-id="12027-176">In double-quoted here-strings, variables are replaced by their values.</span></span> <span data-ttu-id="12027-177">例如：</span><span class="sxs-lookup"><span data-stu-id="12027-177">For example:</span></span>

```powershell
@"
Even if you have not created a profile,
the path of the profile file is:
$profile.
"@
```

<span data-ttu-id="12027-178">此命令的輸出為：</span><span class="sxs-lookup"><span data-stu-id="12027-178">The output of this command is:</span></span>

```Output
Even if you have not created a profile,
the path of the profile file is:
C:\Users\User1\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1.
```

<span data-ttu-id="12027-179">這裡-字串通常用來將多行指派給變數。</span><span class="sxs-lookup"><span data-stu-id="12027-179">Here-strings are typically used to assign multiple lines to a variable.</span></span> <span data-ttu-id="12027-180">例如，下列字串會將 XML 頁面指派給 $page 變數。</span><span class="sxs-lookup"><span data-stu-id="12027-180">For example, the following here-string assigns a page of XML to the $page variable.</span></span>

```powershell
$page = [XML] @"
<command:command xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
<command:details>
        <command:name>
               Format-Table
        </command:name>
        <maml:description>
            <maml:para>Formats the output as a table.</maml:para>
        </maml:description>
        <command:verb>format</command:verb>
        <command:noun>table</command:noun>
        <dev:version></dev:version>
</command:details>
...
</command:command>
"@
```

<span data-ttu-id="12027-181">在此，字串也是對 Cmdlet 輸入的便利格式 `ConvertFrom-StringData` ，會將這裡的字串轉換成雜湊表。</span><span class="sxs-lookup"><span data-stu-id="12027-181">Here-strings are also a convenient format for input to the `ConvertFrom-StringData` cmdlet, which converts here-strings to hash tables.</span></span>
<span data-ttu-id="12027-182">如需詳細資訊，請參閱`ConvertFrom-StringData`。</span><span class="sxs-lookup"><span data-stu-id="12027-182">For more information, see `ConvertFrom-StringData`.</span></span>

## <a name="see-also"></a><span data-ttu-id="12027-183">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12027-183">SEE ALSO</span></span>

[<span data-ttu-id="12027-184">about_Special_Characters</span><span class="sxs-lookup"><span data-stu-id="12027-184">about_Special_Characters</span></span>](about_Special_Characters.md)

[<span data-ttu-id="12027-185">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="12027-185">ConvertFrom-StringData</span></span>](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)
