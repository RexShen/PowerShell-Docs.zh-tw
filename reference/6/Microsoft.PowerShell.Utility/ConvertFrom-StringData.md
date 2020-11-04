---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/21/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-stringdata?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-StringData
ms.openlocfilehash: 8ffb7a33bb1b4b5409c48445b88a8eb58f9b93b9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204703"
---
# <span data-ttu-id="cd0bf-103">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="cd0bf-103">ConvertFrom-StringData</span></span>

## <span data-ttu-id="cd0bf-104">概要</span><span class="sxs-lookup"><span data-stu-id="cd0bf-104">SYNOPSIS</span></span>
<span data-ttu-id="cd0bf-105">將包含一或多個索引鍵與值組的字串轉換成雜湊表。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-105">Converts a string containing one or more key and value pairs to a hash table.</span></span>

## <span data-ttu-id="cd0bf-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cd0bf-106">SYNTAX</span></span>

### <span data-ttu-id="cd0bf-107">全部</span><span class="sxs-lookup"><span data-stu-id="cd0bf-107">All</span></span>

```
ConvertFrom-StringData [-StringData] <String> [<CommonParameters>]
```

## <span data-ttu-id="cd0bf-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cd0bf-108">DESCRIPTION</span></span>

<span data-ttu-id="cd0bf-109">`ConvertFrom-StringData`Cmdlet 會將包含一或多個索引鍵和值組的字串轉換成雜湊表。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-109">The `ConvertFrom-StringData` cmdlet converts a string that contains one or more key and value pairs into a hash table.</span></span> <span data-ttu-id="cd0bf-110">因為每個索引鍵/值組都必須位於不同的行上，所以此處的字串通常會用來做為輸入格式。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-110">Because each key-value pair must be on a separate line, here-strings are often used as the input format.</span></span> <span data-ttu-id="cd0bf-111">根據預設，索引 **鍵** 必須以等號 () 字元來與 **值** 分隔 `=` 。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-111">By default, the **key** must be separated from the **value** by an equals sign (`=`) character.</span></span>

<span data-ttu-id="cd0bf-112">此 `ConvertFrom-StringData` Cmdlet 會被視為安全的 Cmdlet，可以在腳本或函式的區段中使用 `DATA` 。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-112">The `ConvertFrom-StringData` cmdlet is considered to be a safe cmdlet that can be used in the `DATA` section of a script or function.</span></span> <span data-ttu-id="cd0bf-113">在區段中使用時 `DATA` ，字串的內容必須符合 DATA 區段的規則。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-113">When used in a `DATA` section, the contents of the string must conform to the rules for a DATA section.</span></span> <span data-ttu-id="cd0bf-114">如需詳細資訊，請參閱 [about_Data_Sections](../Microsoft.PowerShell.Core/About/about_Data_Sections.md)。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-114">For more information, see [about_Data_Sections](../Microsoft.PowerShell.Core/About/about_Data_Sections.md).</span></span>

<span data-ttu-id="cd0bf-115">`ConvertFrom-StringData` 支援傳統機器翻譯工具所允許的 escape 字元序列。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-115">`ConvertFrom-StringData` supports escape character sequences that are allowed by conventional machine translation tools.</span></span> <span data-ttu-id="cd0bf-116">也就是說，此 Cmdlet 可以 `\` 使用 [Unescape 方法](/dotnet/api/system.text.regularexpressions.regex.unescape)將反斜線 () 為字串資料中的 escape 字元，而不是 \` 通常會在腳本中發出行結尾的 PowerShell 倒引號字元 () 。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-116">That is, the cmdlet can interpret backslashes (`\`) as escape characters in the string data by using the [Regex.Unescape Method](/dotnet/api/system.text.regularexpressions.regex.unescape), instead of the PowerShell backtick character (\`) that would normally signal the end of a line in a script.</span></span> <span data-ttu-id="cd0bf-117">在 here-string 內部，倒單引號字元沒有作用。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-117">Inside the here-string, the backtick character does not work.</span></span> <span data-ttu-id="cd0bf-118">您也可以使用前面的反斜線（如下所示）將常值反斜線保留在結果中 `\\` 。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-118">You can also preserve a literal backslash in your results by escaping it with a preceding backslash, like this: `\\`.</span></span> <span data-ttu-id="cd0bf-119">未逸出的反斜線字元 (例如通常在檔案路徑中使用的反斜線)，可能會在您的結果中轉譯為無效的逸出序列。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-119">Unescaped backslash characters, such as those that are commonly used in file paths, can render as illegal escape sequences in your results.</span></span>

## <span data-ttu-id="cd0bf-120">範例</span><span class="sxs-lookup"><span data-stu-id="cd0bf-120">EXAMPLES</span></span>

### <span data-ttu-id="cd0bf-121">範例1：將以單引號括住的字串轉換成雜湊表</span><span class="sxs-lookup"><span data-stu-id="cd0bf-121">Example 1: Convert a single-quoted here-string to a hash table</span></span>

<span data-ttu-id="cd0bf-122">此範例會將以單引號括住的使用者訊息字串轉換成雜湊表。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-122">This example converts a single-quoted here-string of user messages into a hash table.</span></span> <span data-ttu-id="cd0bf-123">在單引號字串中，值不會被變數取代，而且不會評估運算式。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-123">In a single-quoted string, values are not substituted for variables and expressions are not evaluated.</span></span>
<span data-ttu-id="cd0bf-124">`ConvertFrom-StringData`Cmdlet 會將變數中的值轉換 `$Here` 成雜湊表。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-124">The `ConvertFrom-StringData` cmdlet converts the value in the `$Here` variable to a hash table.</span></span>

```powershell
$Here = @'
Msg1 = The string parameter is required.
Msg2 = Credentials are required for this command.
Msg3 = The specified variable does not exist.
'@
ConvertFrom-StringData -StringData $Here
```

```Output
Name                           Value
----                           -----
Msg3                           The specified variable does not exist.
Msg2                           Credentials are required for this command.
Msg1                           The string parameter is required.
```

### <span data-ttu-id="cd0bf-125">範例2：在此轉換包含批註的字串</span><span class="sxs-lookup"><span data-stu-id="cd0bf-125">Example 2: Convert a here-string containing a comment</span></span>

<span data-ttu-id="cd0bf-126">此範例會將包含批註和多個索引鍵/值組的字串轉換成雜湊表。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-126">This example converts a here-string that contains a comment and multiple key-value pairs into a hash table.</span></span>

```powershell
ConvertFrom-StringData -StringData @'
Name = Disks.ps1

# Category is optional.

Category = Storage
Cost = Free
'@
```

```Output
Name                           Value
----                           -----
Cost                           Free
Category                       Storage
Name                           Disks.ps1
```

<span data-ttu-id="cd0bf-127">**至 convertfrom-stringdata** 參數的值是此處的字串，而不是包含此處字串的變數。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-127">The value of the **StringData** parameter is a here-string, instead of a variable that contains a here-string.</span></span> <span data-ttu-id="cd0bf-128">任一格式都有效。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-128">Either format is valid.</span></span> <span data-ttu-id="cd0bf-129">here-string 包括一個與其中一個字串有關的註解。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-129">The here-string includes a comment about one of the strings.</span></span>
<span data-ttu-id="cd0bf-130">`ConvertFrom-StringData` 忽略單行批註，但 `#` 字元必須是該行的第一個非空白字元。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-130">`ConvertFrom-StringData` ignores single-line comments, but the `#` character must be the first non-whitespace character on the line.</span></span> <span data-ttu-id="cd0bf-131">中的行上的所有字元 `#` 都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-131">All characters on the line after the `#` are ignored.</span></span>

### <span data-ttu-id="cd0bf-132">範例3：將字串轉換成雜湊表</span><span class="sxs-lookup"><span data-stu-id="cd0bf-132">Example 3: Convert a string to a hash table</span></span>

<span data-ttu-id="cd0bf-133">此範例會將正則雙引號的字串 (不是此處的字串) 轉換成雜湊表，並將它儲存在 `$A` 變數中。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-133">This example converts a regular double-quoted string (not a here-string) into a hash table and saves it in the `$A` variable.</span></span>

```powershell
$A = ConvertFrom-StringData -StringData "Top = Red `n Bottom = Blue"
$A
```

```Output
Name             Value
----             -----
Bottom           Blue
Top              Red
```

<span data-ttu-id="cd0bf-134">為了滿足每個索引鍵/值組都必須位於不同行的條件，此字串會使用 PowerShell 分行符號 (\` n) 來分隔配對。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-134">To satisfy the condition that each key-value pair must be on a separate line, the string uses the PowerShell newline character (\`n) to separate the pairs.</span></span>

### <span data-ttu-id="cd0bf-135">範例4：在腳本的 DATA 區段中使用 ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="cd0bf-135">Example 4: Use ConvertFrom-StringData in the DATA section of a script</span></span>

<span data-ttu-id="cd0bf-136">此範例顯示 `ConvertFrom-StringData` 在腳本的 DATA 區段中使用的命令。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-136">This example shows a `ConvertFrom-StringData` command used in the DATA section of a script.</span></span>
<span data-ttu-id="cd0bf-137">DATA 區段下方的陳述式會向使用者顯示文字。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-137">The statements below the DATA section display the text to the user.</span></span>

```powershell
$TextMsgs = DATA {
ConvertFrom-StringData @'
Text001 = The $Notebook variable contains the name of the user's system notebook.
Text002 = The $MyNotebook variable contains the name of the user's private notebook.
'@
}
$TextMsgs
```

```Output
Name             Value
----             -----
Text001          The $Notebook variable contains the name of the user's system notebook.
Text002          The $MyNotebook variable contains the name of the user's private notebook.
```

<span data-ttu-id="cd0bf-138">因為文字包括變數名稱，必須在單引號字串中將它括住，才能將變數解譯為常值且不會展開。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-138">Because the text includes variable names, it must be enclosed in a single-quoted string so that the variables are interpreted literally and not expanded.</span></span> <span data-ttu-id="cd0bf-139">**DATA** 區段中不允許使用變數。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-139">Variables are not permitted in the **DATA** section.</span></span>

### <span data-ttu-id="cd0bf-140">範例5：使用管線運算子來傳遞字串</span><span class="sxs-lookup"><span data-stu-id="cd0bf-140">Example 5: Use the pipeline operator to pass a string</span></span>

<span data-ttu-id="cd0bf-141">此範例顯示您可以使用管線運算子 () 將 `|` 字串傳送至 `ConvertFrom-StringData` 。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-141">This example shows that you can use a pipeline operator (`|`) to send a string to `ConvertFrom-StringData`.</span></span> <span data-ttu-id="cd0bf-142">變數的值 `$Here` 會以管道傳送至 `ConvertFrom-StringData` 變數中的結果，並產生結果 `$Hash` 。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-142">The the value of the `$Here` variable is piped to `ConvertFrom-StringData` and the result in the `$Hash` variable.</span></span>

```powershell
$Here = @'
Msg1 = The string parameter is required.
Msg2 = Credentials are required for this command.
Msg3 = The specified variable does not exist.
'@
$Hash = $Here | ConvertFrom-StringData
$Hash
```

```Output
Name     Value
----     -----
Msg3     The specified variable does not exist.
Msg2     Credentials are required for this command.
Msg1     The string parameter is required.
```

### <span data-ttu-id="cd0bf-143">範例6：使用 escape 字元加入新行和傳回字元</span><span class="sxs-lookup"><span data-stu-id="cd0bf-143">Example 6: Use escape characters to add new lines and return characters</span></span>

<span data-ttu-id="cd0bf-144">此範例示範如何使用 escape 字元來建立新的行，並傳回來源資料中的字元。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-144">This example shows the use of escape characters to create new lines and return characters in source data.</span></span> <span data-ttu-id="cd0bf-145">Escape 序列 `\n` 是用來在與產生的雜湊表中的名稱或專案相關聯的文字區塊內建立新的行。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-145">The escape sequence `\n` is used to create new lines within a block of text that is associated with a name or item in the resulting hash table.</span></span>

```powershell
ConvertFrom-StringData @"
Vincentio = Heaven doth with us as we with torches do,\nNot light them for themselves; for if our virtues\nDid not go forth of us, 'twere all alike\nAs if we had them not.
Angelo = Let there be some more test made of my metal,\nBefore so noble and so great a figure\nBe stamp'd upon it.
"@ | Format-List
```

```Output
Name  : Angelo
Value : Let there be some more test made of my metal,
        Before so noble and so great a figure
        Be stamp'd upon it.

Name  : Vincentio
Value : Heaven doth with us as we with torches do,
        Not light them for themselves; for if our virtues
        Did not go forth of us, 'twere all alike
        As if we had them not.
```

### <span data-ttu-id="cd0bf-146">範例7：使用反斜線 escape 字元正確轉譯檔案路徑</span><span class="sxs-lookup"><span data-stu-id="cd0bf-146">Example 7: Use backslash escape character to correctly render a file path</span></span>

<span data-ttu-id="cd0bf-147">此範例示範如何在字串資料中使用反斜線 escape 字元，以允許在產生的雜湊表中正確轉譯檔案路徑 `ConvertFrom-StringData` 。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-147">This example shows how to use of the backslash escape character in the string data to allow a file path to render correctly in the resulting `ConvertFrom-StringData` hash table.</span></span> <span data-ttu-id="cd0bf-148">雙反斜線可確保能夠在雜湊表輸出中正確轉譯常值反斜線字元。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-148">The double backslash ensures that the literal backslash characters render correctly in the hash table output.</span></span>

```powershell
ConvertFrom-StringData "Message=Look in c:\\Windows\\System32"
```

```Output
Name                           Value
----                           -----
Message                        Look in c:\Windows\System32
```

## <span data-ttu-id="cd0bf-149">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cd0bf-149">PARAMETERS</span></span>

### <span data-ttu-id="cd0bf-150">-StringData</span><span class="sxs-lookup"><span data-stu-id="cd0bf-150">-StringData</span></span>

<span data-ttu-id="cd0bf-151">指定要轉換的字串。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-151">Specifies the string to be converted.</span></span> <span data-ttu-id="cd0bf-152">您可以使用這個參數或使用管線將字串傳送至 `ConvertFrom-StringData` 。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-152">You can use this parameter or pipe a string to `ConvertFrom-StringData`.</span></span> <span data-ttu-id="cd0bf-153">參數名稱為選擇性。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-153">The parameter name is optional.</span></span>

<span data-ttu-id="cd0bf-154">此參數的值必須是包含一或多個索引鍵/值組的字串。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-154">The value of this parameter must be a string that contains one or more key-value pairs.</span></span> <span data-ttu-id="cd0bf-155">每個索引鍵/值組都必須位於不同的行上，否則每個配對必須以分行符號分隔 (\` n) 。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-155">Each key-value pair must be on a separate line, or each pair must be separated by newline characters (\`n).</span></span>

<span data-ttu-id="cd0bf-156">您可以在字串中包括批註，但是批註不能和索引鍵/值組位於同一行。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-156">You can include comments in the string, but the comments cannot be on the same line as a key-value pair.</span></span> <span data-ttu-id="cd0bf-157">`ConvertFrom-StringData` 忽略單行批註。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-157">`ConvertFrom-StringData` ignores single-line comments.</span></span> <span data-ttu-id="cd0bf-158">`#`字元必須是該行的第一個非空白字元。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-158">The `#` character must be the first non-whitespace character on the line.</span></span> <span data-ttu-id="cd0bf-159">中的行上的所有字元 `#` 都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-159">All characters on the line after the `#` are ignored.</span></span> <span data-ttu-id="cd0bf-160">註解不會包括在雜湊表中。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-160">The comments are not included in the hash table.</span></span>

<span data-ttu-id="cd0bf-161">這裡的字串是由一或多行組成的字串。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-161">A here-string is a string consisting of one or more lines.</span></span> <span data-ttu-id="cd0bf-162">在此字串內的引號會當做字串資料的一部分來解讀。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-162">Quotation marks within the here-string are interpreted literally as part of the string data.</span></span> <span data-ttu-id="cd0bf-163">如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-163">For more information, see [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="cd0bf-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cd0bf-164">CommonParameters</span></span>

<span data-ttu-id="cd0bf-165">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-165">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cd0bf-166">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-166">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="cd0bf-167">輸入</span><span class="sxs-lookup"><span data-stu-id="cd0bf-167">INPUTS</span></span>

### <span data-ttu-id="cd0bf-168">System.String</span><span class="sxs-lookup"><span data-stu-id="cd0bf-168">System.String</span></span>

<span data-ttu-id="cd0bf-169">您可以使用管線將包含機碼值組的字串傳送至 `ConvertFrom-StringData` 。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-169">You can pipe a string containing a key-value pair to `ConvertFrom-StringData`.</span></span>

## <span data-ttu-id="cd0bf-170">輸出</span><span class="sxs-lookup"><span data-stu-id="cd0bf-170">OUTPUTS</span></span>

### <span data-ttu-id="cd0bf-171">System.Collections.Hashtable</span><span class="sxs-lookup"><span data-stu-id="cd0bf-171">System.Collections.Hashtable</span></span>

<span data-ttu-id="cd0bf-172">這個 Cmdlet 會傳回雜湊表，它會從索引鍵/值組建立。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-172">This cmdlet returns a hash table that it creates from the key-value pairs.</span></span>

## <span data-ttu-id="cd0bf-173">注意</span><span class="sxs-lookup"><span data-stu-id="cd0bf-173">NOTES</span></span>

<span data-ttu-id="cd0bf-174">here-string 是由一或多行組成的字串，其中的引號會解譯為常值。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-174">A here-string is a string consisting of one or more lines within which quotation marks are interpreted literally.</span></span>

<span data-ttu-id="cd0bf-175">在以多種語言顯示使用者訊息的腳本中，此 Cmdlet 會很有用。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-175">This cmdlet can be useful in scripts that display user messages in multiple spoken languages.</span></span> <span data-ttu-id="cd0bf-176">您可以使用字典樣式雜湊表來隔離文字字串與程式碼 (例如在資源檔案中)，以及將文字字串格式化以在翻譯工具中使用。</span><span class="sxs-lookup"><span data-stu-id="cd0bf-176">You can use the dictionary-style hash tables to isolate text strings from code, such as in resource files, and to format the text strings for use in translation tools.</span></span>

## <span data-ttu-id="cd0bf-177">相關連結</span><span class="sxs-lookup"><span data-stu-id="cd0bf-177">RELATED LINKS</span></span>