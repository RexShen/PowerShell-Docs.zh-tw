---
description: 說明資料區段，這些區段會將文字字串和其他唯讀資料與腳本邏輯隔離。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_data_sections?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Data_Sections
ms.openlocfilehash: a5eed0056fe572760415f62537b5a69942d819ae
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207347"
---
# <a name="about-data-sections"></a><span data-ttu-id="a6cb7-104">關於資料區段</span><span class="sxs-lookup"><span data-stu-id="a6cb7-104">About Data Sections</span></span>

## <a name="short-description"></a><span data-ttu-id="a6cb7-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="a6cb7-105">Short Description</span></span>
<span data-ttu-id="a6cb7-106">說明資料區段，這些區段會將文字字串和其他唯讀資料與腳本邏輯隔離。</span><span class="sxs-lookup"><span data-stu-id="a6cb7-106">Explains Data sections, which isolate text strings and other read-only data from script logic.</span></span>

## <a name="long-description"></a><span data-ttu-id="a6cb7-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="a6cb7-107">Long Description</span></span>

<span data-ttu-id="a6cb7-108">專為 PowerShell 設計的腳本可以有一個或多個資料區段只包含資料。</span><span class="sxs-lookup"><span data-stu-id="a6cb7-108">Scripts that are designed for PowerShell can have one or more Data sections that contain only data.</span></span> <span data-ttu-id="a6cb7-109">您可以在任何腳本、函數或 advanced 函數中包含一個或多個資料區段。</span><span class="sxs-lookup"><span data-stu-id="a6cb7-109">You can include one or more Data sections in any script, function, or advanced function.</span></span> <span data-ttu-id="a6cb7-110">Data 區段的內容限制為指定的 PowerShell 指令碼語言子集。</span><span class="sxs-lookup"><span data-stu-id="a6cb7-110">The content of the Data section is restricted to a specified subset of the PowerShell scripting language.</span></span>

<span data-ttu-id="a6cb7-111">分隔資料與程式碼邏輯可讓您更輕鬆地識別及管理邏輯和資料。</span><span class="sxs-lookup"><span data-stu-id="a6cb7-111">Separating data from code logic makes it easier to identify and manage both logic and data.</span></span> <span data-ttu-id="a6cb7-112">它可讓您針對文字使用不同的字串資源檔，例如錯誤訊息和說明字串。</span><span class="sxs-lookup"><span data-stu-id="a6cb7-112">It lets you have separate string resource files for text, such as error messages and Help strings.</span></span> <span data-ttu-id="a6cb7-113">它也會隔離程式碼邏輯，以促進安全性和驗證測試。</span><span class="sxs-lookup"><span data-stu-id="a6cb7-113">It also isolates the code logic, which facilitates security and validation tests.</span></span>

<span data-ttu-id="a6cb7-114">在 PowerShell 中，Data 區段可用來支援腳本國際化。</span><span class="sxs-lookup"><span data-stu-id="a6cb7-114">In PowerShell, the Data section is used to support script internationalization.</span></span>
<span data-ttu-id="a6cb7-115">您可以使用資料區段，讓您更輕鬆地隔離、找出及處理將轉譯成許多使用者介面 (UI) 語言的字串。</span><span class="sxs-lookup"><span data-stu-id="a6cb7-115">You can use Data sections to make it easier to isolate, locate, and process strings that will be translated into many user interface (UI) languages.</span></span>

<span data-ttu-id="a6cb7-116">Data 區段是 PowerShell 2.0 功能。</span><span class="sxs-lookup"><span data-stu-id="a6cb7-116">The Data section is a PowerShell 2.0 feature.</span></span> <span data-ttu-id="a6cb7-117">具有資料區段的腳本不會在沒有修訂的 PowerShell 1.0 中執行。</span><span class="sxs-lookup"><span data-stu-id="a6cb7-117">Scripts with Data sections will not run in PowerShell 1.0 without revision.</span></span>

### <a name="syntax"></a><span data-ttu-id="a6cb7-118">Syntax</span><span class="sxs-lookup"><span data-stu-id="a6cb7-118">Syntax</span></span>

<span data-ttu-id="a6cb7-119">資料區段的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="a6cb7-119">The syntax for a Data section is as follows:</span></span>

```
DATA [<variable-name>] [-supportedCommand <cmdlet-name>] {
    <Permitted content>
}
```

<span data-ttu-id="a6cb7-120">需要資料關鍵字。</span><span class="sxs-lookup"><span data-stu-id="a6cb7-120">The Data keyword is required.</span></span> <span data-ttu-id="a6cb7-121">不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="a6cb7-121">It is not case-sensitive.</span></span> <span data-ttu-id="a6cb7-122">允許的內容限制為下列元素：</span><span class="sxs-lookup"><span data-stu-id="a6cb7-122">The permitted content is limited to the following elements:</span></span>

- <span data-ttu-id="a6cb7-123">所有 PowerShell 操作員，除了 `-match`</span><span class="sxs-lookup"><span data-stu-id="a6cb7-123">All PowerShell operators, except `-match`</span></span>
- <span data-ttu-id="a6cb7-124">`If`、 `Else` 和 `ElseIf` 語句</span><span class="sxs-lookup"><span data-stu-id="a6cb7-124">`If`, `Else`, and `ElseIf` statements</span></span>
- <span data-ttu-id="a6cb7-125">下列自動變數如下： `$PsCulture` 、 `$PsUICulture` 、 `$True` 、 `$False` 和。 `$Null`</span><span class="sxs-lookup"><span data-stu-id="a6cb7-125">The following automatic variables: `$PsCulture`, `$PsUICulture`, `$True`, `$False`, and `$Null`</span></span>
- <span data-ttu-id="a6cb7-126">註解</span><span class="sxs-lookup"><span data-stu-id="a6cb7-126">Comments</span></span>
- <span data-ttu-id="a6cb7-127">管線</span><span class="sxs-lookup"><span data-stu-id="a6cb7-127">Pipelines</span></span>
- <span data-ttu-id="a6cb7-128">以分號分隔的語句 (`;`) </span><span class="sxs-lookup"><span data-stu-id="a6cb7-128">Statements separated by semicolons (`;`)</span></span>
- <span data-ttu-id="a6cb7-129">常值，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a6cb7-129">Literals, such as the following:</span></span>

  ```powershell
  a
  1
  1,2,3
  "PowerShell 2.0"
  @( "red", "green", "blue" )
  @{ a = 0x1; b = "great"; c ="script" }
  [XML] @'
  <p> Hello, World </p>
  '@
  ```

- <span data-ttu-id="a6cb7-130">資料區段中允許的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a6cb7-130">Cmdlets that are permitted in a Data section.</span></span> <span data-ttu-id="a6cb7-131">依預設，只 `ConvertFrom-StringData` 允許 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a6cb7-131">By default, only the `ConvertFrom-StringData` cmdlet is permitted.</span></span>
- <span data-ttu-id="a6cb7-132">使用參數在資料區段中允許的 Cmdlet `-SupportedCommand` 。</span><span class="sxs-lookup"><span data-stu-id="a6cb7-132">Cmdlets that you permit in a Data section by using the `-SupportedCommand` parameter.</span></span>

<span data-ttu-id="a6cb7-133">當您 `ConvertFrom-StringData` 在資料區段中使用 Cmdlet 時，您可以用單引號或雙引號括住的字串，或是以單引號括住或以雙引號括住的字串來括住機碼值組。</span><span class="sxs-lookup"><span data-stu-id="a6cb7-133">When you use the `ConvertFrom-StringData` cmdlet in a Data section, you can enclose the key-value pairs in single-quoted or double-quoted strings or in single-quoted or double-quoted here-strings.</span></span> <span data-ttu-id="a6cb7-134">不過，包含變數和子運算式的字串必須以單引號括住的字串，或在此以單引號括住的字串括住，如此一來，就不會展開變數，且子運算式無法執行。</span><span class="sxs-lookup"><span data-stu-id="a6cb7-134">However, strings that contain variables and subexpressions must be enclosed in single-quoted strings or in single-quoted here-strings so that the variables are not expanded and the subexpressions are not executable.</span></span>

### <a name="-supportedcommand"></a><span data-ttu-id="a6cb7-135">-SupportedCommand</span><span class="sxs-lookup"><span data-stu-id="a6cb7-135">-SupportedCommand</span></span>

<span data-ttu-id="a6cb7-136">`-SupportedCommand`參數可讓您指出 Cmdlet 或函式只會產生資料。</span><span class="sxs-lookup"><span data-stu-id="a6cb7-136">The `-SupportedCommand` parameter allows you to indicate that a cmdlet or function generates only data.</span></span> <span data-ttu-id="a6cb7-137">它的設計目的是讓使用者在其所撰寫或測試的資料區段中包含 Cmdlet 和函數。</span><span class="sxs-lookup"><span data-stu-id="a6cb7-137">It is designed to allow users to include cmdlets and functions in a data section that they have written or tested.</span></span>

<span data-ttu-id="a6cb7-138">的值 `-SupportedCommand` 是一個或多個 Cmdlet 或函式名稱的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="a6cb7-138">The value of `-SupportedCommand` is a comma-separated list of one or more cmdlet or function names.</span></span>

<span data-ttu-id="a6cb7-139">例如，下列資料區段包含使用者撰寫的 Cmdlet，其會將 `Format-XML` XML 檔案中的資料格式化：</span><span class="sxs-lookup"><span data-stu-id="a6cb7-139">For example, the following data section includes a user-written cmdlet, `Format-XML`, that formats data in an XML file:</span></span>

```powershell
DATA -supportedCommand Format-Xml
{
    Format-Xml -Strings string1, string2, string3
}
```

### <a name="using-a-data-section"></a><span data-ttu-id="a6cb7-140">使用資料區段</span><span class="sxs-lookup"><span data-stu-id="a6cb7-140">Using a Data Section</span></span>

<span data-ttu-id="a6cb7-141">若要使用資料區段的內容，請將它指派給變數，並使用變數標記法來存取內容。</span><span class="sxs-lookup"><span data-stu-id="a6cb7-141">To use the content of a Data section, assign it to a variable and use variable notation to access the content.</span></span>

<span data-ttu-id="a6cb7-142">例如，下列資料區段包含的 `ConvertFrom-StringData` 命令會將此字串轉換成雜湊表。</span><span class="sxs-lookup"><span data-stu-id="a6cb7-142">For example, the following data section contains a `ConvertFrom-StringData` command that converts the here-string into a hash table.</span></span> <span data-ttu-id="a6cb7-143">雜湊表會指派給 `$TextMsgs` 變數。</span><span class="sxs-lookup"><span data-stu-id="a6cb7-143">The hash table is assigned to the `$TextMsgs` variable.</span></span>

<span data-ttu-id="a6cb7-144">`$TextMsgs`變數不是 data 區段的一部分。</span><span class="sxs-lookup"><span data-stu-id="a6cb7-144">The `$TextMsgs` variable is not part of the data section.</span></span>

```powershell
$TextMsgs = DATA {
    ConvertFrom-StringData -StringData @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}
```

<span data-ttu-id="a6cb7-145">若要存取雜湊表中的索引鍵和值 `$TextMsgs` ，請使用下列命令。</span><span class="sxs-lookup"><span data-stu-id="a6cb7-145">To access the keys and values in hash table in `$TextMsgs`, use the following commands.</span></span>

```powershell
$TextMsgs.Text001
$TextMsgs.Text002
```

<span data-ttu-id="a6cb7-146">或者，您可以將變數名稱放在 Data 區段的定義中。</span><span class="sxs-lookup"><span data-stu-id="a6cb7-146">Alternately, you can put the variable name in the definition of the Data section.</span></span> <span data-ttu-id="a6cb7-147">例如：</span><span class="sxs-lookup"><span data-stu-id="a6cb7-147">For example:</span></span>

```powershell
DATA TextMsgs {
    ConvertFrom-StringData -StringData @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}

$TextMsgs
```

<span data-ttu-id="a6cb7-148">結果與上一個範例相同。</span><span class="sxs-lookup"><span data-stu-id="a6cb7-148">The result is the same as the previous example.</span></span>

```Output
Name                           Value
----                           -----
Text001                        Windows 7
Text002                        Windows Server 2008 R2
```

### <a name="examples"></a><span data-ttu-id="a6cb7-149">範例</span><span class="sxs-lookup"><span data-stu-id="a6cb7-149">Examples</span></span>

<span data-ttu-id="a6cb7-150">簡單的資料字串。</span><span class="sxs-lookup"><span data-stu-id="a6cb7-150">Simple data strings.</span></span>

```powershell
DATA {
    "Thank you for using my PowerShell Organize.pst script."
    "It is provided free of charge to the community."
    "I appreciate your comments and feedback."
}
```

<span data-ttu-id="a6cb7-151">包含允許變數的字串。</span><span class="sxs-lookup"><span data-stu-id="a6cb7-151">Strings that include permitted variables.</span></span>

```powershell
DATA {
    if ($null) {
        "To get help for this cmdlet, type get-help new-dictionary."
    }
}
```

<span data-ttu-id="a6cb7-152">以單引號括住的字串，使用 `ConvertFrom-StringData` Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="a6cb7-152">A single-quoted here-string that uses the `ConvertFrom-StringData` cmdlet:</span></span>

```powershell
DATA {
    ConvertFrom-StringData -stringdata @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}
```

<span data-ttu-id="a6cb7-153">以雙引號括住的字串，使用 `ConvertFrom-StringData` Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="a6cb7-153">A double-quoted here-string that uses the `ConvertFrom-StringData` cmdlet:</span></span>

```powershell
DATA  {
    ConvertFrom-StringData -stringdata @"
Msg1 = To start, press any key.
Msg2 = To exit, type "quit".
"@
}
```

<span data-ttu-id="a6cb7-154">資料區段，包含可產生資料的使用者撰寫 Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="a6cb7-154">A data section that includes a user-written cmdlet that generates data:</span></span>

```powershell
DATA -supportedCommand Format-XML {
    Format-Xml -strings string1, string2, string3
}
```

## <a name="see-also"></a><span data-ttu-id="a6cb7-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6cb7-155">See Also</span></span>

[<span data-ttu-id="a6cb7-156">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="a6cb7-156">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="a6cb7-157">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="a6cb7-157">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="a6cb7-158">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="a6cb7-158">about_Hash_Tables</span></span>](about_Hash_Tables.md)

[<span data-ttu-id="a6cb7-159">about_If</span><span class="sxs-lookup"><span data-stu-id="a6cb7-159">about_If</span></span>](about_If.md)

[<span data-ttu-id="a6cb7-160">about_Operators</span><span class="sxs-lookup"><span data-stu-id="a6cb7-160">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="a6cb7-161">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="a6cb7-161">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)

[<span data-ttu-id="a6cb7-162">about_Script_Internationalization</span><span class="sxs-lookup"><span data-stu-id="a6cb7-162">about_Script_Internationalization</span></span>](about_Script_Internationalization.md)

[<span data-ttu-id="a6cb7-163">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="a6cb7-163">ConvertFrom-StringData</span></span>](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)

[<span data-ttu-id="a6cb7-164">Import-LocalizedData</span><span class="sxs-lookup"><span data-stu-id="a6cb7-164">Import-LocalizedData</span></span>](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)

