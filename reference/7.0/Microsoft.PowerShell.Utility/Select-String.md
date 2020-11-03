---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-string?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-String
ms.openlocfilehash: 7c614314eb13ea484f5a0a5ade36aabdd6afdf58
ms.sourcegitcommit: 9a8bb1b459b5939c95e1f6d9499fcb13d01a58c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "93206104"
---
# <span data-ttu-id="c7694-103">Select-String</span><span class="sxs-lookup"><span data-stu-id="c7694-103">Select-String</span></span>

## <span data-ttu-id="c7694-104">概要</span><span class="sxs-lookup"><span data-stu-id="c7694-104">SYNOPSIS</span></span>
<span data-ttu-id="c7694-105">尋找字串和檔案中的文字。</span><span class="sxs-lookup"><span data-stu-id="c7694-105">Finds text in strings and files.</span></span>

## <span data-ttu-id="c7694-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c7694-106">SYNTAX</span></span>

### <span data-ttu-id="c7694-107">File (預設值)</span><span class="sxs-lookup"><span data-stu-id="c7694-107">File (Default)</span></span>

```
Select-String [-Culture <String>] [-Pattern] <String[]> [-Path] <String[]> [-SimpleMatch]
 [-CaseSensitive] [-Quiet] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>]
 [-NotMatch] [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="c7694-108">ObjectRaw</span><span class="sxs-lookup"><span data-stu-id="c7694-108">ObjectRaw</span></span>

```
Select-String [-Culture <String>] -InputObject <PSObject> [-Pattern] <String[]> -Raw [-SimpleMatch]
 [-CaseSensitive] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch]
 [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="c7694-109">Object</span><span class="sxs-lookup"><span data-stu-id="c7694-109">Object</span></span>

```
Select-String [-Culture <String>] -InputObject <PSObject> [-Pattern] <String[]> [-SimpleMatch]
 [-CaseSensitive] [-Quiet] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>]
 [-NotMatch] [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="c7694-110">FileRaw</span><span class="sxs-lookup"><span data-stu-id="c7694-110">FileRaw</span></span>

```
Select-String [-Culture <String>] [-Pattern] <String[]> [-Path] <String[]> -Raw [-SimpleMatch]
 [-CaseSensitive] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch]
 [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="c7694-111">LiteralFileRaw</span><span class="sxs-lookup"><span data-stu-id="c7694-111">LiteralFileRaw</span></span>

```
Select-String [-Culture <String>] [-Pattern] <String[]> -LiteralPath <String[]> -Raw [-SimpleMatch]
 [-CaseSensitive] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch]
 [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="c7694-112">LiteralFile</span><span class="sxs-lookup"><span data-stu-id="c7694-112">LiteralFile</span></span>

```
Select-String [-Culture <String>] [-Pattern] <String[]> -LiteralPath <String[]> [-SimpleMatch]
 [-CaseSensitive] [-Quiet] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>]
 [-NotMatch] [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

## <span data-ttu-id="c7694-113">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="c7694-113">DESCRIPTION</span></span>

<span data-ttu-id="c7694-114">此 `Select-String` Cmdlet 會搜尋輸入字串和檔案中的文字和文字模式。</span><span class="sxs-lookup"><span data-stu-id="c7694-114">The `Select-String` cmdlet searches for text and text patterns in input strings and files.</span></span> <span data-ttu-id="c7694-115">您可以使用 `Select-String` 類似于 UNIX 中的 **Grep** 或 Windows 中的 **findstr.exe** 。</span><span class="sxs-lookup"><span data-stu-id="c7694-115">You can use `Select-String` similar to **grep** in UNIX or **findstr.exe** in Windows.</span></span>

<span data-ttu-id="c7694-116">`Select-String` 以文字行為基礎。</span><span class="sxs-lookup"><span data-stu-id="c7694-116">`Select-String` is based on lines of text.</span></span> <span data-ttu-id="c7694-117">依預設， `Select-String` 會在每一行中尋找第一個相符項，而且每個相符項都會顯示檔案名、行號，以及行中包含相符項的所有文字。</span><span class="sxs-lookup"><span data-stu-id="c7694-117">By default, `Select-String` finds the first match in each line and, for each match, it displays the file name, line number, and all text in the line containing the match.</span></span> <span data-ttu-id="c7694-118">您可以導向 `Select-String` 找出每行的多個相符專案、顯示相符專案之前和之後的文字，或是顯示 (True 或 False 的布林值) 指出是否找到相符專案。</span><span class="sxs-lookup"><span data-stu-id="c7694-118">You can direct `Select-String` to find multiple matches per line, display text before and after the match, or display a Boolean value (True or False) that indicates whether a match is found.</span></span>

<span data-ttu-id="c7694-119">`Select-String` 使用正則運算式比對，但它也可以執行比對，在輸入中搜尋您所指定的文字。</span><span class="sxs-lookup"><span data-stu-id="c7694-119">`Select-String` uses regular expression matching, but it can also perform a match that searches the input for the text that you specify.</span></span>

<span data-ttu-id="c7694-120">`Select-String` 可以顯示所有文字相符專案，或在每個輸入檔案中的第一個相符專案之後停止。</span><span class="sxs-lookup"><span data-stu-id="c7694-120">`Select-String` can display all the text matches or stop after the first match in each input file.</span></span>
<span data-ttu-id="c7694-121">`Select-String` 可以用來顯示所有不符合指定模式的文字。</span><span class="sxs-lookup"><span data-stu-id="c7694-121">`Select-String` can be used to display all text that doesn't match the specified pattern.</span></span>

<span data-ttu-id="c7694-122">您也可以指定 `Select-String` 應該預期特定字元編碼，例如當您搜尋 Unicode 文字的檔案時。</span><span class="sxs-lookup"><span data-stu-id="c7694-122">You can also specify that `Select-String` should expect a particular character encoding, such as when you're searching files of Unicode text.</span></span> <span data-ttu-id="c7694-123">`Select-String` 使用位元組順序標記 (BOM) 來偵測檔案的編碼格式。</span><span class="sxs-lookup"><span data-stu-id="c7694-123">`Select-String` uses the byte-order-mark (BOM) to detect the encoding format of the file.</span></span> <span data-ttu-id="c7694-124">如果檔案沒有 BOM，則會假設編碼為 UTF8。</span><span class="sxs-lookup"><span data-stu-id="c7694-124">If the file has no BOM, it assumes the encoding is UTF8.</span></span>

## <span data-ttu-id="c7694-125">範例</span><span class="sxs-lookup"><span data-stu-id="c7694-125">EXAMPLES</span></span>

### <span data-ttu-id="c7694-126">範例1：尋找區分大小寫的相符項</span><span class="sxs-lookup"><span data-stu-id="c7694-126">Example 1: Find a case-sensitive match</span></span>

<span data-ttu-id="c7694-127">此範例會對從管線傳送到 Cmdlet 的文字進行區分大小寫的比對 `Select-String` 。</span><span class="sxs-lookup"><span data-stu-id="c7694-127">This example does a case-sensitive match of the text that was sent down the pipeline to the `Select-String` cmdlet.</span></span>

```powershell
'Hello', 'HELLO' | Select-String -Pattern 'HELLO' -CaseSensitive -SimpleMatch
```

<span data-ttu-id="c7694-128">文字字串 **Hello** 和 **Hello** 會向下傳送至 `Select-String` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c7694-128">The text strings **Hello** and **HELLO** are sent down the pipeline to the `Select-String` cmdlet.</span></span>
<span data-ttu-id="c7694-129">`Select-String` 使用 **Pattern** 參數指定 **HELLO** 。</span><span class="sxs-lookup"><span data-stu-id="c7694-129">`Select-String` uses the **Pattern** parameter to specify **HELLO** .</span></span> <span data-ttu-id="c7694-130">**CaseSensitive** 參數指定案例必須僅符合大寫模式。</span><span class="sxs-lookup"><span data-stu-id="c7694-130">The **CaseSensitive** parameter specifies that the case must match only the upper-case pattern.</span></span> <span data-ttu-id="c7694-131">**SimpleMatch** 是選擇性參數，可指定模式中的字串不會被視為正則運算式。</span><span class="sxs-lookup"><span data-stu-id="c7694-131">**SimpleMatch** is an optional parameter and specifies that the string in the pattern isn't interpreted as a regular expression.</span></span>
<span data-ttu-id="c7694-132">`Select-String` 在 PowerShell 主控台中顯示 **HELLO** 。</span><span class="sxs-lookup"><span data-stu-id="c7694-132">`Select-String` displays **HELLO** in the PowerShell console.</span></span>

### <span data-ttu-id="c7694-133">範例2：在文字檔中尋找相符專案</span><span class="sxs-lookup"><span data-stu-id="c7694-133">Example 2: Find matches in text files</span></span>

<span data-ttu-id="c7694-134">此命令會 `.txt` 在目前目錄中搜尋副檔名為的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="c7694-134">This command searches all files with the `.txt` file name extension in the current directory.</span></span> <span data-ttu-id="c7694-135">輸出會顯示這些檔案中包含指定字串的行。</span><span class="sxs-lookup"><span data-stu-id="c7694-135">The output displays the lines in those files that include the specified string.</span></span>

```powershell
Get-Alias | Out-File -FilePath .\Alias.txt
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\*.txt -Pattern 'Get-'
```

```Output
Alias.txt:8:Alias            cat -> Get-Content
Alias.txt:28:Alias           dir -> Get-ChildItem
Alias.txt:43:Alias           gal -> Get-Alias
Command.txt:966:Cmdlet       Get-Acl
Command.txt:967:Cmdlet       Get-Alias
```

<span data-ttu-id="c7694-136">在此範例中， `Get-Alias` 和 `Get-Command` 會與 Cmdlet 搭配使用 `Out-File` ，以在目前的目錄中建立兩個文字檔， **Alias.txt** 和 **Command.txt** 。</span><span class="sxs-lookup"><span data-stu-id="c7694-136">In this example, `Get-Alias` and `Get-Command` are used with the `Out-File` cmdlet to create two text files in the current directory, **Alias.txt** and **Command.txt** .</span></span>

<span data-ttu-id="c7694-137">`Select-String` 使用 **Path** 參數搭配星號 (`*`) 萬用字元來搜尋目前目錄中副檔名為的所有檔案 `.txt` 。</span><span class="sxs-lookup"><span data-stu-id="c7694-137">`Select-String` uses the **Path** parameter with the asterisk (`*`) wildcard to search all files in the current directory with the file name extension `.txt`.</span></span> <span data-ttu-id="c7694-138">**Pattern** 參數指定要與 **Get** 相符的文字。</span><span class="sxs-lookup"><span data-stu-id="c7694-138">The **Pattern** parameter specifies the text to match **Get-** .</span></span> <span data-ttu-id="c7694-139">`Select-String` 在 PowerShell 主控台中顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="c7694-139">`Select-String` displays the output in the PowerShell console.</span></span> <span data-ttu-id="c7694-140">檔案名和行號會在包含 **模式** 參數相符項的每一行內容前面。</span><span class="sxs-lookup"><span data-stu-id="c7694-140">The file name and line number precede each line of content that contains a match for the **Pattern** parameter.</span></span>

### <span data-ttu-id="c7694-141">範例3：尋找模式相符</span><span class="sxs-lookup"><span data-stu-id="c7694-141">Example 3: Find a pattern match</span></span>

<span data-ttu-id="c7694-142">在此範例中，會搜尋多個檔案，以尋找指定模式的相符專案。</span><span class="sxs-lookup"><span data-stu-id="c7694-142">In this example, multiple files are searched to find matches for the specified pattern.</span></span> <span data-ttu-id="c7694-143">此模式會使用正則運算式數量詞。</span><span class="sxs-lookup"><span data-stu-id="c7694-143">The pattern uses a regular expression quantifier.</span></span> <span data-ttu-id="c7694-144">如需詳細資訊，請參閱 [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/About_Regular_Expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="c7694-144">For more information, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/About_Regular_Expressions.md).</span></span>

```powershell
Select-String -Path "$PSHOME\en-US\*.txt" -Pattern '\?'
```

```Output
C:\Program Files\PowerShell\6\en-US\default.help.txt:27:    beginning at https://go.microsoft.com/fwlink/?LinkID=108518.
C:\Program Files\PowerShell\6\en-US\default.help.txt:50:    or go to: https://go.microsoft.com/fwlink/?LinkID=210614
```

<span data-ttu-id="c7694-145">此 `Select-String` Cmdlet 會使用兩個參數： **路徑** 和 **模式** 。</span><span class="sxs-lookup"><span data-stu-id="c7694-145">The `Select-String` cmdlet uses two parameters, **Path** and **Pattern** .</span></span> <span data-ttu-id="c7694-146">**Path** 參數 `$PSHOME` 會使用指定 PowerShell 目錄的變數。</span><span class="sxs-lookup"><span data-stu-id="c7694-146">The **Path** parameter uses the variable `$PSHOME` that specifies the PowerShell directory.</span></span> <span data-ttu-id="c7694-147">路徑的其餘部分包含子目錄 **en-us** ，並指定目錄中的每個檔案 `*.txt` 。</span><span class="sxs-lookup"><span data-stu-id="c7694-147">The remainder of the path includes the subdirectory **en-US** and specifies each `*.txt` file in the directory.</span></span> <span data-ttu-id="c7694-148">**Pattern** 參數指定要符合每個檔案中的問號 (`?`) 。</span><span class="sxs-lookup"><span data-stu-id="c7694-148">The **Pattern** parameter specifies to match a question mark (`?`) in each file.</span></span> <span data-ttu-id="c7694-149">使用反斜線 (`\`) 作為 escape 字元，而且是必要的，因為問號 (`?`) 是正則運算式數量詞。</span><span class="sxs-lookup"><span data-stu-id="c7694-149">A backslash (`\`) is used as an escape character and is necessary because the question mark (`?`) is a regular expression quantifier.</span></span> <span data-ttu-id="c7694-150">`Select-String` 在 PowerShell 主控台中顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="c7694-150">`Select-String` displays the output in the PowerShell console.</span></span> <span data-ttu-id="c7694-151">檔案名和行號會在包含 **模式** 參數相符項的每一行內容前面。</span><span class="sxs-lookup"><span data-stu-id="c7694-151">The file name and line number precede each line of content that contains a match for the **Pattern** parameter.</span></span>

### <span data-ttu-id="c7694-152">範例4：在函式中使用 Select-String</span><span class="sxs-lookup"><span data-stu-id="c7694-152">Example 4: Use Select-String in a function</span></span>

<span data-ttu-id="c7694-153">這個範例會建立一個函式，以搜尋 PowerShell 說明檔中的模式。</span><span class="sxs-lookup"><span data-stu-id="c7694-153">This example creates a function to search for a pattern in the PowerShell help files.</span></span> <span data-ttu-id="c7694-154">在此範例中，此函式只存在於 PowerShell 會話中。</span><span class="sxs-lookup"><span data-stu-id="c7694-154">For this example, the function only exists in the PowerShell session.</span></span> <span data-ttu-id="c7694-155">當 PowerShell 會話關閉時，就會刪除該函式。</span><span class="sxs-lookup"><span data-stu-id="c7694-155">When the PowerShell session is closed, the function is deleted.</span></span> <span data-ttu-id="c7694-156">如需詳細資訊，請參閱 [about_Functions](../Microsoft.PowerShell.Core/About/about_Functions.md)。</span><span class="sxs-lookup"><span data-stu-id="c7694-156">For more information, see [about_Functions](../Microsoft.PowerShell.Core/About/about_Functions.md).</span></span>

```
PS> Function Search-Help
>> {
>> $PSHelp = "$PSHOME\en-US\*.txt"
>> Select-String -Path $PSHelp -Pattern 'About_'
>> }
PS>

PS> Search-Help

C:\Program Files\PowerShell\6\en-US\default.help.txt:67:    The titles of conceptual topics begin with "About_".
C:\Program Files\PowerShell\6\en-US\default.help.txt:70:    Get-Help About_<topic-name>
C:\Program Files\PowerShell\6\en-US\default.help.txt:93:    Get-Help About_Modules : Displays help about PowerShell modules.
C:\Program Files\PowerShell\6\en-US\default.help.txt:97:    about_Updatable_Help
```

<span data-ttu-id="c7694-157">函式會建立在 PowerShell 命令列上。</span><span class="sxs-lookup"><span data-stu-id="c7694-157">The function is created on the PowerShell command line.</span></span> <span data-ttu-id="c7694-158">此 `Function` 命令會使用名稱 **搜尋-Help** 。</span><span class="sxs-lookup"><span data-stu-id="c7694-158">The `Function` command uses the name **Search-Help** .</span></span> <span data-ttu-id="c7694-159">按 **enter** 鍵，開始將語句新增至函式。</span><span class="sxs-lookup"><span data-stu-id="c7694-159">Press **Enter** to begin adding statements to the function.</span></span> <span data-ttu-id="c7694-160">從 `>>` 提示字元加入每個語句，然後按下 **enter** ，如範例所示。</span><span class="sxs-lookup"><span data-stu-id="c7694-160">From the `>>` prompt, add each statement and press **Enter** as shown in the example.</span></span> <span data-ttu-id="c7694-161">新增右括弧之後，您會回到 PowerShell 提示字元。</span><span class="sxs-lookup"><span data-stu-id="c7694-161">After the closing bracket is added, you're returned to a PowerShell prompt.</span></span>

<span data-ttu-id="c7694-162">函數包含兩個命令。</span><span class="sxs-lookup"><span data-stu-id="c7694-162">The function contains two commands.</span></span> <span data-ttu-id="c7694-163">`$PSHelp`變數會儲存 PowerShell 說明檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="c7694-163">The `$PSHelp` variable stores the path to the PowerShell help files.</span></span> <span data-ttu-id="c7694-164">`$PSHOME` 是具有子目錄 **en-us** 的 PowerShell 安裝目錄，指定目錄中的每個檔案 `*.txt` 。</span><span class="sxs-lookup"><span data-stu-id="c7694-164">`$PSHOME` is the PowerShell installation directory with the subdirectory **en-US** that specifies each `*.txt` file in the directory.</span></span>

<span data-ttu-id="c7694-165">`Select-String`函數中的命令會使用 **路徑** 和 **模式** 參數。</span><span class="sxs-lookup"><span data-stu-id="c7694-165">The `Select-String` command in the function uses the **Path** and **Pattern** parameters.</span></span> <span data-ttu-id="c7694-166">**Path** 參數會使用 `$PSHelp` 變數來取得路徑。</span><span class="sxs-lookup"><span data-stu-id="c7694-166">The **Path** parameter uses the `$PSHelp` variable to get the path.</span></span> <span data-ttu-id="c7694-167">**Pattern** 參數會使用字串 **About_** 作為搜尋準則。</span><span class="sxs-lookup"><span data-stu-id="c7694-167">The **Pattern** parameter uses the string **About_** as the search criteria.</span></span>

<span data-ttu-id="c7694-168">若要執行函數，請輸入 `Search-Help` 。</span><span class="sxs-lookup"><span data-stu-id="c7694-168">To run the function, type `Search-Help`.</span></span> <span data-ttu-id="c7694-169">函數的 `Select-String` 命令會在 PowerShell 主控台中顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="c7694-169">The function's `Select-String` command displays the output in the PowerShell console.</span></span>

### <span data-ttu-id="c7694-170">範例5：在 Windows 事件記錄檔中搜尋字串</span><span class="sxs-lookup"><span data-stu-id="c7694-170">Example 5: Search for a string in a Windows event log</span></span>

<span data-ttu-id="c7694-171">此範例會在 Windows 事件記錄檔中搜尋字串。</span><span class="sxs-lookup"><span data-stu-id="c7694-171">This example searches for a string in a Windows event log.</span></span> <span data-ttu-id="c7694-172">變數 `$_` 代表管線中的目前物件。</span><span class="sxs-lookup"><span data-stu-id="c7694-172">The variable `$_` represents the current object in the pipeline.</span></span> <span data-ttu-id="c7694-173">如需詳細資訊，請參閱 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="c7694-173">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

```powershell
$Events = Get-WinEvent -LogName Application -MaxEvents 50
$Events | Select-String -InputObject {$_.message} -Pattern 'Failed'
```

<span data-ttu-id="c7694-174">此 `Get-WinEvent` Cmdlet 會使用 **LogName** 參數來指定應用程式記錄檔。</span><span class="sxs-lookup"><span data-stu-id="c7694-174">The `Get-WinEvent` cmdlet uses the **LogName** parameter to specify the Application log.</span></span> <span data-ttu-id="c7694-175">**MaxEvents** 參數會從記錄檔中取得50最新的事件。</span><span class="sxs-lookup"><span data-stu-id="c7694-175">The **MaxEvents** parameter gets the 50 most recent events from the log.</span></span> <span data-ttu-id="c7694-176">記錄內容會儲存在名為的變數中 `$Events` 。</span><span class="sxs-lookup"><span data-stu-id="c7694-176">The log content is stored in the variable named `$Events`.</span></span>

<span data-ttu-id="c7694-177">此 `$Events` 變數會向下傳送至 `Select-String` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c7694-177">The `$Events` variable is sent down the pipeline to the `Select-String` cmdlet.</span></span> <span data-ttu-id="c7694-178">`Select-String` 使用 **InputObject** 參數。</span><span class="sxs-lookup"><span data-stu-id="c7694-178">`Select-String` uses the **InputObject** parameter.</span></span> <span data-ttu-id="c7694-179">`$_`變數代表目前的物件，而且 `message` 是事件的屬性。</span><span class="sxs-lookup"><span data-stu-id="c7694-179">The `$_` variable represents the current object and `message` is a property of the event.</span></span> <span data-ttu-id="c7694-180">**Pattern** 參數物種字串 **失敗** ，並在中搜尋相符專案 `$_.message` 。</span><span class="sxs-lookup"><span data-stu-id="c7694-180">The **Pattern** parameter species the string **Failed** and searches for matches in `$_.message`.</span></span> <span data-ttu-id="c7694-181">`Select-String` 在 PowerShell 主控台中顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="c7694-181">`Select-String` displays the output in the PowerShell console.</span></span>

### <span data-ttu-id="c7694-182">範例6：在子目錄中尋找字串</span><span class="sxs-lookup"><span data-stu-id="c7694-182">Example 6: Find a string in subdirectories</span></span>

<span data-ttu-id="c7694-183">此範例會在目錄及其所有子目錄中搜尋特定的文字字串。</span><span class="sxs-lookup"><span data-stu-id="c7694-183">This example searches a directory and all of its subdirectories for a specific text string.</span></span>

```powershell
Get-ChildItem -Path C:\Windows\System32\*.txt -Recurse | Select-String -Pattern 'Microsoft' -CaseSensitive
```

<span data-ttu-id="c7694-184">`Get-ChildItem` 使用 **Path** 參數來指定 **C:\Windows\System32 \* .txt** 。</span><span class="sxs-lookup"><span data-stu-id="c7694-184">`Get-ChildItem` uses the **Path** parameter to specify **C:\Windows\System32\*.txt** .</span></span> <span data-ttu-id="c7694-185">**遞迴** 參數包含子目錄。</span><span class="sxs-lookup"><span data-stu-id="c7694-185">The **Recurse** parameter includes the subdirectories.</span></span> <span data-ttu-id="c7694-186">物件會向下傳送到管線 `Select-String` 。</span><span class="sxs-lookup"><span data-stu-id="c7694-186">The objects are sent down the pipeline to `Select-String`.</span></span>

<span data-ttu-id="c7694-187">`Select-String` 使用 **Pattern** 參數，並指定 **Microsoft** 字串。</span><span class="sxs-lookup"><span data-stu-id="c7694-187">`Select-String` uses the **Pattern** parameter and specifies the string **Microsoft** .</span></span> <span data-ttu-id="c7694-188">**CaseSensitive** 參數是用來符合字串的確切大小寫。</span><span class="sxs-lookup"><span data-stu-id="c7694-188">The **CaseSensitive** parameter is used to match the exact case of the string.</span></span> <span data-ttu-id="c7694-189">`Select-String` 在 PowerShell 主控台中顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="c7694-189">`Select-String` displays the output in the PowerShell console.</span></span>

> [!NOTE]
> <span data-ttu-id="c7694-190">根據您的許可權，您可能會在輸出中看到 **拒絕存取** 訊息。</span><span class="sxs-lookup"><span data-stu-id="c7694-190">Dependent upon your permissions, you might see **Access denied** messages in the output.</span></span>

### <span data-ttu-id="c7694-191">範例7：尋找不符合模式的字串</span><span class="sxs-lookup"><span data-stu-id="c7694-191">Example 7: Find strings that do not match a pattern</span></span>

<span data-ttu-id="c7694-192">此範例顯示如何排除不符合模式的資料行。</span><span class="sxs-lookup"><span data-stu-id="c7694-192">This example shows how to exclude lines of data that don't match a pattern.</span></span>

```powershell
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\Command.txt -Pattern 'Get', 'Set'  -NotMatch
```

<span data-ttu-id="c7694-193">`Get-Command`Cmdlet 會將物件沿著管線向下傳送至， `Out-File` 以在目前的目錄中建立 **Command.txt** 檔案。</span><span class="sxs-lookup"><span data-stu-id="c7694-193">The `Get-Command` cmdlet sends objects down the pipeline to the `Out-File` to create the **Command.txt** file in the current directory.</span></span> <span data-ttu-id="c7694-194">`Select-String` 使用 **Path** 參數來指定 **Command.txt** 檔。</span><span class="sxs-lookup"><span data-stu-id="c7694-194">`Select-String` uses the **Path** parameter to specify the **Command.txt** file.</span></span> <span data-ttu-id="c7694-195">**Pattern** 參數會指定 **Get** 和 **Set** 做為搜尋模式。</span><span class="sxs-lookup"><span data-stu-id="c7694-195">The **Pattern** parameter specifies **Get** and **Set** as the search pattern.</span></span> <span data-ttu-id="c7694-196">**NotMatch** 參數會將 **Get** 和 **Set** 從結果中排除。</span><span class="sxs-lookup"><span data-stu-id="c7694-196">The **NotMatch** parameter excludes **Get** and **Set** from the results.</span></span>
<span data-ttu-id="c7694-197">`Select-String` 在 PowerShell 主控台中顯示未包含 **Get** 或 **Set** 的輸出。</span><span class="sxs-lookup"><span data-stu-id="c7694-197">`Select-String` displays the output in the PowerShell console that doesn't include **Get** or **Set** .</span></span>

### <span data-ttu-id="c7694-198">範例8：在相符的前後尋找行</span><span class="sxs-lookup"><span data-stu-id="c7694-198">Example 8: Find lines before and after a match</span></span>

<span data-ttu-id="c7694-199">此範例示範如何取得相符模式前後的行。</span><span class="sxs-lookup"><span data-stu-id="c7694-199">This example shows how to get the lines before and after the matched pattern.</span></span>

```powershell
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\Command.txt -Pattern 'Get-Computer' -Context 2, 3
```

```Output
  Command.txt:986:Cmdlet          Get-CmsMessage           6.1.0.0    Microsoft.PowerShell.Security
  Command.txt:987:Cmdlet          Get-Command              6.1.2.0    Microsoft.PowerShell.Core
> Command.txt:988:Cmdlet          Get-ComputerInfo         6.1.0.0    Microsoft.PowerShell.Management
  Command.txt:990:Cmdlet          Get-Content              6.1.0.0    Microsoft.PowerShell.Management
  Command.txt:991:Cmdlet          Get-ControlPanelItem     3.1.0.0    Microsoft.PowerShell.Management
  Command.txt:992:Cmdlet          Get-Credential           6.1.0.0    Microsoft.PowerShell.Security
```

<span data-ttu-id="c7694-200">`Get-Command`Cmdlet 會將物件沿著管線向下傳送至， `Out-File` 以在目前的目錄中建立 **Command.txt** 檔案。</span><span class="sxs-lookup"><span data-stu-id="c7694-200">The `Get-Command` cmdlet sends objects down the pipeline to the `Out-File` to create the **Command.txt** file in the current directory.</span></span> <span data-ttu-id="c7694-201">`Select-String` 使用 **Path** 參數來指定 **Command.txt** 檔。</span><span class="sxs-lookup"><span data-stu-id="c7694-201">`Select-String` uses the **Path** parameter to specify the **Command.txt** file.</span></span> <span data-ttu-id="c7694-202">**Pattern** 參數會將 **Get 電腦** 指定為搜尋模式。</span><span class="sxs-lookup"><span data-stu-id="c7694-202">The **Pattern** parameter specifies **Get-Computer** as the search pattern.</span></span> <span data-ttu-id="c7694-203">**內容** 參數會使用兩個值，前後都有兩個值，並以角括弧 () 來標記輸出中的模式相符 `>` 。</span><span class="sxs-lookup"><span data-stu-id="c7694-203">The **Context** parameter uses two values, before and after, and marks pattern matches in the output with an angle bracket (`>`).</span></span> <span data-ttu-id="c7694-204">**CoNtext** 參數會輸出第一個模式比對之前的兩行，並在最後一個模式相符之後輸出三行。</span><span class="sxs-lookup"><span data-stu-id="c7694-204">The **Context** parameter outputs the two lines before the first pattern match and three lines after the last pattern match.</span></span>

### <span data-ttu-id="c7694-205">範例9：尋找所有模式相符專案</span><span class="sxs-lookup"><span data-stu-id="c7694-205">Example 9: Find all pattern matches</span></span>

<span data-ttu-id="c7694-206">此範例示範 **AllMatches** 參數如何在文字行中尋找每個模式相符。</span><span class="sxs-lookup"><span data-stu-id="c7694-206">This example shows how the **AllMatches** parameter finds each pattern match in a line of text.</span></span> <span data-ttu-id="c7694-207">依預設， `Select-String` 只會在文字行中尋找第一次出現的模式。</span><span class="sxs-lookup"><span data-stu-id="c7694-207">By default, `Select-String` only finds the first occurrence of a pattern in a line of text.</span></span> <span data-ttu-id="c7694-208">這個範例會使用以 Cmdlet 找到的物件屬性 `Get-Member` 。</span><span class="sxs-lookup"><span data-stu-id="c7694-208">This example uses object properties that are found with the `Get-Member` cmdlet.</span></span>

```
PS> $A = Get-ChildItem -Path "$PSHOME\en-US\*.txt" | Select-String -Pattern 'PowerShell'

PS> $A

C:\Program Files\PowerShell\6\en-US\default.help.txt:3:    PowerShell Help System
C:\Program Files\PowerShell\6\en-US\default.help.txt:6:    Displays help about PowerShell cmdlets and concepts.
C:\Program Files\PowerShell\6\en-US\default.help.txt:9:    PowerShell Help describes PowerShell cmdlets

PS> $A.Matches

Groups   : {0}
Success  : True
Name     : 0
Captures : {0}
Index    : 4
Length   : 10
Value    : PowerShell

PS> $A.Matches.Length

8

PS> $B = Get-ChildItem -Path "$PSHOME\en-US\*.txt" | Select-String -Pattern 'PowerShell' -AllMatches

PS> $B.Matches.Length

9
```

<span data-ttu-id="c7694-209">此 `Get-ChildItem` Cmdlet 會使用 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="c7694-209">The `Get-ChildItem` cmdlet uses the **Path** parameter.</span></span> <span data-ttu-id="c7694-210">**Path** 參數 `$PSHOME` 會使用指定 PowerShell 目錄的變數。</span><span class="sxs-lookup"><span data-stu-id="c7694-210">The **Path** parameter uses the variable `$PSHOME` that specifies the PowerShell directory.</span></span> <span data-ttu-id="c7694-211">路徑的其餘部分包含子目錄 **en-us** ，並指定目錄中的每個檔案 `*.txt` 。</span><span class="sxs-lookup"><span data-stu-id="c7694-211">The remainder of the path includes the subdirectory **en-US** and specifies each `*.txt` file in the directory.</span></span> <span data-ttu-id="c7694-212">`Get-ChildItem`物件會儲存在變數中 `$A` 。</span><span class="sxs-lookup"><span data-stu-id="c7694-212">The `Get-ChildItem` objects are stored in the `$A` variable.</span></span> <span data-ttu-id="c7694-213">此 `$A` 變數會向下傳送至 `Select-String` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c7694-213">The `$A` variable is sent down the pipeline to the `Select-String` cmdlet.</span></span> <span data-ttu-id="c7694-214">`Select-String` 使用 **Pattern** 參數來搜尋字串 **PowerShell** 的每個檔案。</span><span class="sxs-lookup"><span data-stu-id="c7694-214">`Select-String` uses the **Pattern** parameter to search each file for the string **PowerShell** .</span></span>

<span data-ttu-id="c7694-215">從 PowerShell 命令列中， `$A` 會顯示變數內容。</span><span class="sxs-lookup"><span data-stu-id="c7694-215">From the PowerShell command line, the `$A` variable contents are displayed.</span></span> <span data-ttu-id="c7694-216">有一個包含兩次字串 **PowerShell** 的行。</span><span class="sxs-lookup"><span data-stu-id="c7694-216">There's a line that contains two occurrences of the string **PowerShell** .</span></span>

<span data-ttu-id="c7694-217">`$A.Matches`屬性會列出每一行上第一次出現的模式 **PowerShell** 。</span><span class="sxs-lookup"><span data-stu-id="c7694-217">The `$A.Matches` property lists the first occurrence of the pattern **PowerShell** on each line.</span></span>

<span data-ttu-id="c7694-218">`$A.Matches.Length`屬性會計算每一行上第一次出現的模式 **PowerShell** 。</span><span class="sxs-lookup"><span data-stu-id="c7694-218">The `$A.Matches.Length` property counts the first occurrence of the pattern **PowerShell** on each line.</span></span>

<span data-ttu-id="c7694-219">`$B`變數使用相同的 `Get-ChildItem` 和 `Select-String` Cmdlet，但會新增 **AllMatches** 參數。</span><span class="sxs-lookup"><span data-stu-id="c7694-219">The `$B` variable uses the same `Get-ChildItem` and `Select-String` cmdlets, but adds the **AllMatches** parameter.</span></span> <span data-ttu-id="c7694-220">**AllMatches** 會在每一行找出每個出現的模式 **PowerShell** 。</span><span class="sxs-lookup"><span data-stu-id="c7694-220">**AllMatches** finds each occurrence of the pattern **PowerShell** on each line.</span></span> <span data-ttu-id="c7694-221">和變數中所儲存的物件 `$A` `$B` 是相同的。</span><span class="sxs-lookup"><span data-stu-id="c7694-221">The objects stored in the `$A` and `$B` variables are identical.</span></span>

<span data-ttu-id="c7694-222">`$B.Matches.Length`屬性會增加，因為每一行都會計算模式 **PowerShell** 的每個出現次數。</span><span class="sxs-lookup"><span data-stu-id="c7694-222">The `$B.Matches.Length` property increases because for each line, every occurrence of the pattern **PowerShell** is counted.</span></span>

## <span data-ttu-id="c7694-223">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c7694-223">PARAMETERS</span></span>

### <span data-ttu-id="c7694-224">-AllMatches</span><span class="sxs-lookup"><span data-stu-id="c7694-224">-AllMatches</span></span>

<span data-ttu-id="c7694-225">指出此 Cmdlet 會在每一行文字中搜尋一個以上的相符項。</span><span class="sxs-lookup"><span data-stu-id="c7694-225">Indicates that the cmdlet searches for more than one match in each line of text.</span></span> <span data-ttu-id="c7694-226">如果沒有這個參數， `Select-String` 只會在每一行文字中尋找第一個相符的內容。</span><span class="sxs-lookup"><span data-stu-id="c7694-226">Without this parameter, `Select-String` finds only the first match in each line of text.</span></span>

<span data-ttu-id="c7694-227">當 `Select-String` 在一行文字中找到一個以上的相符專案時，它仍然只會為該行發出一個 **MatchInfo** 物件，但是 **Matches** 物件的 match 屬性會包含所有相符專案。</span><span class="sxs-lookup"><span data-stu-id="c7694-227">When `Select-String` finds more than one match in a line of text, it still emits only one **MatchInfo** object for the line, but the **Matches** property of the object contains all the matches.</span></span>

> [!NOTE]
> <span data-ttu-id="c7694-228">搭配 **SimpleMatch** 參數使用時，會忽略這個參數。</span><span class="sxs-lookup"><span data-stu-id="c7694-228">This parameter is ignored when used in combination with the **SimpleMatch** parameter.</span></span> <span data-ttu-id="c7694-229">如果您想要傳回所有相符專案，以及您要搜尋的模式包含正則運算式字元，您必須將這些字元轉義，而不是使用 **SimpleMatch** 。</span><span class="sxs-lookup"><span data-stu-id="c7694-229">If you wish to return all matches and the pattern that you are searching for contains regular expression characters, you must escape those characters rather than using **SimpleMatch** .</span></span> <span data-ttu-id="c7694-230">如需有關如何轉義正則運算式的詳細資訊，請參閱 [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md) 。</span><span class="sxs-lookup"><span data-stu-id="c7694-230">See [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md) for more information about escaping regular expressions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c7694-231">-CaseSensitive</span><span class="sxs-lookup"><span data-stu-id="c7694-231">-CaseSensitive</span></span>

<span data-ttu-id="c7694-232">指出 Cmdlet 相符專案區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="c7694-232">Indicates that the cmdlet matches are case-sensitive.</span></span> <span data-ttu-id="c7694-233">依預設，相符專案不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="c7694-233">By default, matches aren't case-sensitive.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c7694-234">-Context</span><span class="sxs-lookup"><span data-stu-id="c7694-234">-Context</span></span>

<span data-ttu-id="c7694-235">在符合模式的行之前和之後捕獲指定的行數。</span><span class="sxs-lookup"><span data-stu-id="c7694-235">Captures the specified number of lines before and after the line that matches the pattern.</span></span>

<span data-ttu-id="c7694-236">如果您輸入一個數字做為此參數的值，該數字會決定相符項目之前與之後擷取的行數。</span><span class="sxs-lookup"><span data-stu-id="c7694-236">If you enter one number as the value of this parameter, that number determines the number of lines captured before and after the match.</span></span> <span data-ttu-id="c7694-237">如果您輸入兩個數字做為該值，第一個數字會決定相符項目之前的行數，而第二個數字會決定相符項目之後的行數。</span><span class="sxs-lookup"><span data-stu-id="c7694-237">If you enter two numbers as the value, the first number determines the number of lines before the match and the second number determines the number of lines after the match.</span></span> <span data-ttu-id="c7694-238">例如： `-Context 2,3` 。</span><span class="sxs-lookup"><span data-stu-id="c7694-238">For example, `-Context 2,3`.</span></span>

<span data-ttu-id="c7694-239">在預設顯示中，具有相符的行會以右角括弧表示， (`>`) 在顯示的第一個資料行中 (ASCII 62) 。</span><span class="sxs-lookup"><span data-stu-id="c7694-239">In the default display, lines with a match are indicated by a right angle bracket (`>`) (ASCII 62) in the first column of the display.</span></span> <span data-ttu-id="c7694-240">未標記的行是上下文。</span><span class="sxs-lookup"><span data-stu-id="c7694-240">Unmarked lines are the context.</span></span>

<span data-ttu-id="c7694-241">**CoNtext** 參數不會變更所產生的物件數目 `Select-String` 。</span><span class="sxs-lookup"><span data-stu-id="c7694-241">The **Context** parameter doesn't change the number of objects generated by `Select-String`.</span></span>
<span data-ttu-id="c7694-242">`Select-String` 針對每個相符各產生一個 [MatchInfo](/dotnet/api/microsoft.powershell.commands.matchinfo) 物件。</span><span class="sxs-lookup"><span data-stu-id="c7694-242">`Select-String` generates one [MatchInfo](/dotnet/api/microsoft.powershell.commands.matchinfo) object for each match.</span></span> <span data-ttu-id="c7694-243">內容會以字串陣列的形式儲存在物件的 **coNtext** 屬性中。</span><span class="sxs-lookup"><span data-stu-id="c7694-243">The context is stored as an array of strings in the **Context** property of the object.</span></span>

<span data-ttu-id="c7694-244">當命令的輸出向 `Select-String` 下傳送到另一個 `Select-String` 命令時，接收命令只會搜尋相符行中的文字。</span><span class="sxs-lookup"><span data-stu-id="c7694-244">When the output of a `Select-String` command is sent down the pipeline to another `Select-String` command, the receiving command searches only the text in the matched line.</span></span> <span data-ttu-id="c7694-245">符合的行是 **MatchInfo** 物件的 **line** 屬性值，而不是內容行中的文字。</span><span class="sxs-lookup"><span data-stu-id="c7694-245">The matched line is the value of the **Line** property of the **MatchInfo** object, not the text in the context lines.</span></span> <span data-ttu-id="c7694-246">因此， **內容** 參數在接收命令上無效 `Select-String` 。</span><span class="sxs-lookup"><span data-stu-id="c7694-246">As a result, the **Context** parameter isn't valid on the receiving `Select-String` command.</span></span>

<span data-ttu-id="c7694-247">當內容包含比對時，每個相符項的 **MatchInfo** 物件都會包含所有內容行，但是重迭行只會在顯示中出現一次。</span><span class="sxs-lookup"><span data-stu-id="c7694-247">When the context includes a match, the **MatchInfo** object for each match includes all the context lines, but the overlapping lines appear only once in the display.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c7694-248">-Culture</span><span class="sxs-lookup"><span data-stu-id="c7694-248">-Culture</span></span>

<span data-ttu-id="c7694-249">指定要與指定模式相符的文化特性名稱。</span><span class="sxs-lookup"><span data-stu-id="c7694-249">Specifies a culture name to match the specified pattern.</span></span> <span data-ttu-id="c7694-250">**Culture** 參數必須搭配 **SimpleMatch** 參數使用。</span><span class="sxs-lookup"><span data-stu-id="c7694-250">The **Culture** parameter must be used with the **SimpleMatch** parameter.</span></span> <span data-ttu-id="c7694-251">預設行為會使用目前 PowerShell 運行時 (會話) 的文化特性。</span><span class="sxs-lookup"><span data-stu-id="c7694-251">The default behavior uses the culture of the current PowerShell runspace (session).</span></span>

<span data-ttu-id="c7694-252">若要取得所有支援的文化特性清單，請使用 `Get-Culture -ListAvailable` 命令。</span><span class="sxs-lookup"><span data-stu-id="c7694-252">To get a list of all supported cultures, use `Get-Culture -ListAvailable` command.</span></span>

<span data-ttu-id="c7694-253">此外，這個參數會接受下列引數：</span><span class="sxs-lookup"><span data-stu-id="c7694-253">In addition, this parameter accepts the following arguments:</span></span>

- <span data-ttu-id="c7694-254">CurrentCulture，預設值為;</span><span class="sxs-lookup"><span data-stu-id="c7694-254">CurrentCulture, that is default;</span></span>
- <span data-ttu-id="c7694-255">序數，也就是非語言二進位檔的比較;</span><span class="sxs-lookup"><span data-stu-id="c7694-255">Ordinal, that is non-linguistic binary comparison;</span></span>
- <span data-ttu-id="c7694-256">不變，這是文化特性獨立的比較。</span><span class="sxs-lookup"><span data-stu-id="c7694-256">Invariant, that is culture independent comparison.</span></span>

<span data-ttu-id="c7694-257">使用 `Select-String -Culture Ordinal -CaseSensitive -SimpleMatch` 命令可讓您取得最快速的二進位比較。</span><span class="sxs-lookup"><span data-stu-id="c7694-257">With `Select-String -Culture Ordinal -CaseSensitive -SimpleMatch` command you gets fastest binary comparison.</span></span>

<span data-ttu-id="c7694-258">**Culture** 參數會使用 tab 鍵自動完成，以在指定可用文化特性的引數清單中進行滾動。</span><span class="sxs-lookup"><span data-stu-id="c7694-258">The **Culture** parameter uses tab completion to scroll through the list of arguments that specify the available cultures.</span></span> <span data-ttu-id="c7694-259">若要列出所有可用的引數，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="c7694-259">To list all available arguments, use the following command:</span></span>

`(Get-Command Select-String).Parameters.Culture.Attributes.ValidValues`

<span data-ttu-id="c7694-260">如需 .NET CultureInfo.Name 屬性的詳細資訊，請參閱 [CultureInfo.Name](/dotnet/api//system.globalization.cultureinfo.name)。</span><span class="sxs-lookup"><span data-stu-id="c7694-260">For more information about .NET CultureInfo.Name property, see [CultureInfo.Name](/dotnet/api//system.globalization.cultureinfo.name).</span></span>

<span data-ttu-id="c7694-261">**Culture** 參數是在 PowerShell 7 中引進。</span><span class="sxs-lookup"><span data-stu-id="c7694-261">The **Culture** parameter was introduced in PowerShell 7.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Culture of the current PowerShell session
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c7694-262">-Encoding</span><span class="sxs-lookup"><span data-stu-id="c7694-262">-Encoding</span></span>

<span data-ttu-id="c7694-263">指定目標檔案的編碼類型。</span><span class="sxs-lookup"><span data-stu-id="c7694-263">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="c7694-264">預設值是 `utf8NoBOM`。</span><span class="sxs-lookup"><span data-stu-id="c7694-264">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="c7694-265">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="c7694-265">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="c7694-266">`ascii`：使用 ASCII (7 位) 字元集的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="c7694-266">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="c7694-267">`bigendianunicode`：使用位元組由大到小的位元組順序，以 UTF-16 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="c7694-267">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="c7694-268">`oem`：針對 MS-DOS 和主控台程式使用預設編碼。</span><span class="sxs-lookup"><span data-stu-id="c7694-268">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="c7694-269">`unicode`：使用位元組由大到小的位元組順序，以 UTF-16 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="c7694-269">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="c7694-270">`utf7`：以 UTF-7 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="c7694-270">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="c7694-271">`utf8`：以 UTF-8 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="c7694-271">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="c7694-272">`utf8BOM`：使用 (BOM) 的位元組順序標記來編碼 UTF-8 格式</span><span class="sxs-lookup"><span data-stu-id="c7694-272">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="c7694-273">`utf8NoBOM`：以不含位元組順序標記的 UTF-8 格式來編碼 (BOM) </span><span class="sxs-lookup"><span data-stu-id="c7694-273">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="c7694-274">`utf32`：以 UTF-32 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="c7694-274">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="c7694-275">從 PowerShell 6.2 開始， **編碼** 參數也會允許已註冊字碼頁的數值識別碼 (例如 `-Encoding 1251`) 或已註冊字碼頁的字串名稱 (例如 `-Encoding "windows-1251"`) 。</span><span class="sxs-lookup"><span data-stu-id="c7694-275">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="c7694-276">如需詳細資訊，請參閱 .NET 檔中的 [編碼字碼頁](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)。</span><span class="sxs-lookup"><span data-stu-id="c7694-276">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c7694-277">-Exclude</span><span class="sxs-lookup"><span data-stu-id="c7694-277">-Exclude</span></span>

<span data-ttu-id="c7694-278">排除指定的項目。</span><span class="sxs-lookup"><span data-stu-id="c7694-278">Exclude the specified items.</span></span> <span data-ttu-id="c7694-279">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="c7694-279">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="c7694-280">輸入路徑元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="c7694-280">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="c7694-281">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="c7694-281">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="c7694-282">-Include</span><span class="sxs-lookup"><span data-stu-id="c7694-282">-Include</span></span>

<span data-ttu-id="c7694-283">包含指定的項目。</span><span class="sxs-lookup"><span data-stu-id="c7694-283">Includes the specified items.</span></span> <span data-ttu-id="c7694-284">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="c7694-284">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="c7694-285">輸入路徑元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="c7694-285">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="c7694-286">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="c7694-286">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="c7694-287">-InputObject</span><span class="sxs-lookup"><span data-stu-id="c7694-287">-InputObject</span></span>

<span data-ttu-id="c7694-288">指定要搜尋的文字。</span><span class="sxs-lookup"><span data-stu-id="c7694-288">Specifies the text to be searched.</span></span> <span data-ttu-id="c7694-289">輸入包含文字的變數，或輸入可取得文字的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="c7694-289">Enter a variable that contains the text, or type a command or expression that gets the text.</span></span>

<span data-ttu-id="c7694-290">使用 **InputObject** 參數和將字串向下傳送至時不同 `Select-String` 。</span><span class="sxs-lookup"><span data-stu-id="c7694-290">Using the **InputObject** parameter isn't the same as sending strings down the pipeline to `Select-String`.</span></span>

<span data-ttu-id="c7694-291">當您將多個字串輸送至 `Select-String` Cmdlet 時，它會在每個字串中搜尋指定的文字，並傳回包含搜尋文字的每個字串。</span><span class="sxs-lookup"><span data-stu-id="c7694-291">When you pipe more than one string to the `Select-String` cmdlet, it searches for the specified text in each string and returns each string that contains the search text.</span></span>

<span data-ttu-id="c7694-292">當您使用 **InputObject** 參數提交字串集合時，會 `Select-String` 將集合視為單一合併字串。</span><span class="sxs-lookup"><span data-stu-id="c7694-292">When you use the **InputObject** parameter to submit a collection of strings, `Select-String` treats the collection as a single combined string.</span></span> <span data-ttu-id="c7694-293">`Select-String` 如果在任何字串中找到搜尋文字，則會以單位形式傳回字串。</span><span class="sxs-lookup"><span data-stu-id="c7694-293">`Select-String` returns the strings as a unit if it finds the search text in any string.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ObjectRaw, Object
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c7694-294">-List</span><span class="sxs-lookup"><span data-stu-id="c7694-294">-List</span></span>

<span data-ttu-id="c7694-295">每個輸入檔只會傳回相符文字的第一個實例。</span><span class="sxs-lookup"><span data-stu-id="c7694-295">Only the first instance of matching text is returned from each input file.</span></span> <span data-ttu-id="c7694-296">這是取得具有符合正則運算式之內容的檔案清單最有效率的方式。</span><span class="sxs-lookup"><span data-stu-id="c7694-296">This is the most efficient way to retrieve a list of files that have contents matching the regular expression.</span></span>

<span data-ttu-id="c7694-297">根據預設， `Select-String` 會針對找到的每個相符項傳回 **MatchInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="c7694-297">By default, `Select-String` returns a **MatchInfo** object for each match it finds.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c7694-298">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c7694-298">-LiteralPath</span></span>

<span data-ttu-id="c7694-299">指定要搜尋之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="c7694-299">Specifies the path to the files to be searched.</span></span> <span data-ttu-id="c7694-300">**LiteralPath** 參數的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="c7694-300">The value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="c7694-301">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="c7694-301">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="c7694-302">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="c7694-302">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="c7694-303">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="c7694-303">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span> <span data-ttu-id="c7694-304">如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="c7694-304">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralFileRaw, LiteralFile
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c7694-305">-NoEmphasis</span><span class="sxs-lookup"><span data-stu-id="c7694-305">-NoEmphasis</span></span>

<span data-ttu-id="c7694-306">依預設，會反白 `Select-String` 顯示符合您使用 **pattern** 參數搜尋之模式的字串。</span><span class="sxs-lookup"><span data-stu-id="c7694-306">By default, `Select-String` highlights the string that matches the pattern you searched for with the **Pattern** parameter.</span></span> <span data-ttu-id="c7694-307">**NoEmphasis** 參數會停用反白顯示。</span><span class="sxs-lookup"><span data-stu-id="c7694-307">The **NoEmphasis** parameter disables the highlighting.</span></span>

<span data-ttu-id="c7694-308">強調會根據您的 PowerShell 背景和文字色彩來使用負面色彩。</span><span class="sxs-lookup"><span data-stu-id="c7694-308">The emphasis uses negative colors based on your PowerShell background and text colors.</span></span> <span data-ttu-id="c7694-309">例如，如果您的 PowerShell 色彩是具有白色文字的黑色背景。</span><span class="sxs-lookup"><span data-stu-id="c7694-309">For example, if your PowerShell colors are a black background with white text.</span></span> <span data-ttu-id="c7694-310">強調是黑色文字的白色背景。</span><span class="sxs-lookup"><span data-stu-id="c7694-310">The emphasis is a white background with black text.</span></span>

<span data-ttu-id="c7694-311">此參數是在 PowerShell 7 中引進。</span><span class="sxs-lookup"><span data-stu-id="c7694-311">This parameter was introduced in PowerShell 7.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c7694-312">-NotMatch</span><span class="sxs-lookup"><span data-stu-id="c7694-312">-NotMatch</span></span>

<span data-ttu-id="c7694-313">**NotMatch** 參數會尋找不符合指定模式的文字。</span><span class="sxs-lookup"><span data-stu-id="c7694-313">The **NotMatch** parameter finds text that doesn't match the specified pattern.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c7694-314">-Path</span><span class="sxs-lookup"><span data-stu-id="c7694-314">-Path</span></span>

<span data-ttu-id="c7694-315">指定要搜尋之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="c7694-315">Specifies the path to the files to search.</span></span> <span data-ttu-id="c7694-316">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="c7694-316">Wildcards are permitted.</span></span> <span data-ttu-id="c7694-317">預設位置是本機目錄。</span><span class="sxs-lookup"><span data-stu-id="c7694-317">The default location is the local directory.</span></span>

<span data-ttu-id="c7694-318">指定目錄中的檔案，例如 `log1.txt` 、 `*.doc` 或 `*.*` 。</span><span class="sxs-lookup"><span data-stu-id="c7694-318">Specify files in the directory, such as `log1.txt`, `*.doc`, or `*.*`.</span></span> <span data-ttu-id="c7694-319">如果您只指定目錄，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="c7694-319">If you specify only a directory, the command fails.</span></span>

```yaml
Type: System.String[]
Parameter Sets: File, FileRaw
Aliases:

Required: True
Position: 1
Default value: Local directory
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="c7694-320">-Pattern</span><span class="sxs-lookup"><span data-stu-id="c7694-320">-Pattern</span></span>

<span data-ttu-id="c7694-321">指定要在每一行上尋找的文字。</span><span class="sxs-lookup"><span data-stu-id="c7694-321">Specifies the text to find on each line.</span></span> <span data-ttu-id="c7694-322">模式值會被視為正則運算式。</span><span class="sxs-lookup"><span data-stu-id="c7694-322">The pattern value is treated as a regular expression.</span></span>

<span data-ttu-id="c7694-323">若要深入瞭解正則運算式，請參閱 [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="c7694-323">To learn about regular expressions, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c7694-324">-Quiet</span><span class="sxs-lookup"><span data-stu-id="c7694-324">-Quiet</span></span>

<span data-ttu-id="c7694-325">指出此 Cmdlet 會傳回布林值 (True 或 False) ，而不是 **MatchInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="c7694-325">Indicates that the cmdlet returns a Boolean value (True or False), instead of a **MatchInfo** object.</span></span> <span data-ttu-id="c7694-326">如果找到模式，則值為 True。否則，此值為 False。</span><span class="sxs-lookup"><span data-stu-id="c7694-326">The value is True if the pattern is found; otherwise the value is False.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: File, Object, LiteralFile
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c7694-327">-Raw</span><span class="sxs-lookup"><span data-stu-id="c7694-327">-Raw</span></span>

<span data-ttu-id="c7694-328">使 Cmdlet 只輸出相符的字串，而不是 **MatchInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="c7694-328">Causes the cmdlet to output only the matching strings, rather than **MatchInfo** objects.</span></span> <span data-ttu-id="c7694-329">這是最類似 Unix **grep** 或 Windows **findstr.exe** 命令的行為結果。</span><span class="sxs-lookup"><span data-stu-id="c7694-329">This is the results in behavior that's the most similar to the Unix **grep** or Windows **findstr.exe** commands.</span></span>

<span data-ttu-id="c7694-330">此參數是在 PowerShell 7 中引進。</span><span class="sxs-lookup"><span data-stu-id="c7694-330">This parameter was introduced in PowerShell 7.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ObjectRaw, FileRaw, LiteralFileRaw
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c7694-331">-SimpleMatch</span><span class="sxs-lookup"><span data-stu-id="c7694-331">-SimpleMatch</span></span>

<span data-ttu-id="c7694-332">指出此 Cmdlet 會使用簡單比對，而不是正則運算式相符項。</span><span class="sxs-lookup"><span data-stu-id="c7694-332">Indicates that the cmdlet uses a simple match rather than a regular expression match.</span></span> <span data-ttu-id="c7694-333">在簡單的比對中，會在 `Select-String` 輸入中搜尋 **Pattern** 參數的文字。</span><span class="sxs-lookup"><span data-stu-id="c7694-333">In a simple match, `Select-String` searches the input for the text in the **Pattern** parameter.</span></span> <span data-ttu-id="c7694-334">它不會將 **Pattern** 參數的值解讀為正則運算式語句。</span><span class="sxs-lookup"><span data-stu-id="c7694-334">It doesn't interpret the value of the **Pattern** parameter as a regular expression statement.</span></span>

<span data-ttu-id="c7694-335">此外，當使用 **SimpleMatch** 時，所傳回之 **MatchInfo** 物件的 [ **符合** ] 屬性會是空的。</span><span class="sxs-lookup"><span data-stu-id="c7694-335">Also, when **SimpleMatch** is used, the **Matches** property of the **MatchInfo** object returned is empty.</span></span>

> [!NOTE]
> <span data-ttu-id="c7694-336">當此參數搭配 **AllMatches** 參數使用時，會忽略 **AllMatches** 。</span><span class="sxs-lookup"><span data-stu-id="c7694-336">When this parameter is used with the **AllMatches** parameter, the **AllMatches** is ignored.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c7694-337">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c7694-337">CommonParameters</span></span>

<span data-ttu-id="c7694-338">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="c7694-338">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c7694-339">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="c7694-339">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c7694-340">輸入</span><span class="sxs-lookup"><span data-stu-id="c7694-340">INPUTS</span></span>

### <span data-ttu-id="c7694-341">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="c7694-341">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="c7694-342">您可以使用管線將具有 **ToString** 方法的任何物件傳送至 `Select-String` 。</span><span class="sxs-lookup"><span data-stu-id="c7694-342">You can pipe any object that has a **ToString** method to `Select-String`.</span></span>

## <span data-ttu-id="c7694-343">輸出</span><span class="sxs-lookup"><span data-stu-id="c7694-343">OUTPUTS</span></span>

### <span data-ttu-id="c7694-344">MatchInfo，System.string，System.string.. 字串</span><span class="sxs-lookup"><span data-stu-id="c7694-344">Microsoft.PowerShell.Commands.MatchInfo, System.Boolean, System.String</span></span>

<span data-ttu-id="c7694-345">根據預設，輸出是一組 **MatchInfo** 物件，每個找到的相符項都有一個物件。</span><span class="sxs-lookup"><span data-stu-id="c7694-345">By default, the output is a set of **MatchInfo** objects with one for each match found.</span></span> <span data-ttu-id="c7694-346">如果您使用 **Quiet** 參數，則輸出會是 **布林** 值，指出是否已找到模式。</span><span class="sxs-lookup"><span data-stu-id="c7694-346">If you use the **Quiet** parameter, the output is a **Boolean** value indicating whether the pattern was found.</span></span>
<span data-ttu-id="c7694-347">如果您使用 **Raw** 參數，則輸出會是一組符合模式的 **字串** 物件。</span><span class="sxs-lookup"><span data-stu-id="c7694-347">If you use the **Raw** parameter, the output is a set of **String** objects that match the pattern.</span></span>

## <span data-ttu-id="c7694-348">注意</span><span class="sxs-lookup"><span data-stu-id="c7694-348">NOTES</span></span>

<span data-ttu-id="c7694-349">`Select-String` 類似于 UNIX 中的 **grep** 或 Windows 中的 **findstr.exe** 。</span><span class="sxs-lookup"><span data-stu-id="c7694-349">`Select-String` is similar to **grep** in UNIX or **findstr.exe** in Windows.</span></span>

<span data-ttu-id="c7694-350">Cmdlet 的 **sls** 別名 `Select-String` 是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="c7694-350">The **sls** alias for the `Select-String` cmdlet was introduced in PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="c7694-351">根據 [PowerShell 命令的已核准動詞](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands)，Cmdlet 的官方別名前置詞 `Select-*` 為 `sc` ，而不是 `sl` 。</span><span class="sxs-lookup"><span data-stu-id="c7694-351">According to [Approved Verbs for PowerShell Commands](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands), the official alias prefix for `Select-*` cmdlets is `sc`, not `sl`.</span></span> <span data-ttu-id="c7694-352">因此，適當的別名 `Select-String` 應該是 `scs` ，而不是 `sls` 。</span><span class="sxs-lookup"><span data-stu-id="c7694-352">Therefore, the proper alias for `Select-String` should be `scs`, not `sls`.</span></span> <span data-ttu-id="c7694-353">這是此規則的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c7694-353">This is an exception to this rule.</span></span>

<span data-ttu-id="c7694-354">若要使用 `Select-String` ，請輸入您想要尋找的文字做為 **Pattern** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="c7694-354">To use `Select-String`, type the text that you want to find as the value of the **Pattern** parameter.</span></span> <span data-ttu-id="c7694-355">若要指定要搜尋的文字，請使用下列準則：</span><span class="sxs-lookup"><span data-stu-id="c7694-355">To specify the text to be searched, use the following criteria:</span></span>

- <span data-ttu-id="c7694-356">在加上引號的字串中輸入文字，然後使用管線將它傳送至 `Select-String` 。</span><span class="sxs-lookup"><span data-stu-id="c7694-356">Type the text in a quoted string, and then pipe it to `Select-String`.</span></span>
- <span data-ttu-id="c7694-357">在變數中儲存文字字串，然後將變數指定為 **InputObject** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="c7694-357">Store a text string in a variable, and then specify the variable as the value of the **InputObject** parameter.</span></span>
- <span data-ttu-id="c7694-358">如果文字儲存在檔案中，請使用 **path** 參數來指定檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="c7694-358">If the text is stored in files, use the **Path** parameter to specify the path to the files.</span></span>

<span data-ttu-id="c7694-359">依預設，會將 `Select-String` **Pattern** 參數的值解釋為正則運算式。</span><span class="sxs-lookup"><span data-stu-id="c7694-359">By default, `Select-String` interprets the value of the **Pattern** parameter as a regular expression.</span></span> <span data-ttu-id="c7694-360">如需詳細資訊，請參閱 [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="c7694-360">For more information, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span></span> <span data-ttu-id="c7694-361">您可以使用 **SimpleMatch** 參數來覆寫正則運算式比對。</span><span class="sxs-lookup"><span data-stu-id="c7694-361">You can use the **SimpleMatch** parameter to override the regular expression matching.</span></span> <span data-ttu-id="c7694-362">**SimpleMatch** 參數會尋找輸入中 **Pattern** 參數值的實例。</span><span class="sxs-lookup"><span data-stu-id="c7694-362">The **SimpleMatch** parameter finds instances of the value of the **Pattern** parameter in the input.</span></span>

<span data-ttu-id="c7694-363">的預設輸出 `Select-String` 是 **MatchInfo** 物件，其中包含相符專案的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="c7694-363">The default output of `Select-String` is a **MatchInfo** object, which includes detailed information about the matches.</span></span> <span data-ttu-id="c7694-364">當您搜尋檔案中的文字時，物件中的資訊會很有用，因為 **MatchInfo** 物件具有像是 **Filename** 與 **Line** 等屬性。</span><span class="sxs-lookup"><span data-stu-id="c7694-364">The information in the object is useful when you're searching for text in files, because **MatchInfo** objects have properties such as **Filename** and **Line** .</span></span> <span data-ttu-id="c7694-365">當輸入不是來自檔案時，這些參數的值會是 **InputStream** 。</span><span class="sxs-lookup"><span data-stu-id="c7694-365">When the input isn't from the file, the value of these parameters is **InputStream** .</span></span>

<span data-ttu-id="c7694-366">如果您不需要 **MatchInfo** 物件中的資訊，請使用 **Quiet** 參數。</span><span class="sxs-lookup"><span data-stu-id="c7694-366">If you don't need the information in the **MatchInfo** object, use the **Quiet** parameter.</span></span> <span data-ttu-id="c7694-367">**Quiet** 參數會傳回布林值 (True 或 False) 來指出它是否找到相符的，而不是 **MatchInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="c7694-367">The **Quiet** parameter returns a Boolean value (True or False) to indicate whether it found a match, instead of a **MatchInfo** object.</span></span>

<span data-ttu-id="c7694-368">當比對片語時， `Select-String` 會使用針對系統所設定的目前文化特性。</span><span class="sxs-lookup"><span data-stu-id="c7694-368">When matching phrases, `Select-String` uses the current culture that is set for the system.</span></span> <span data-ttu-id="c7694-369">若要尋找目前的文化特性，請使用 `Get-Culture` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c7694-369">To find the current culture, use the `Get-Culture` cmdlet.</span></span>

<span data-ttu-id="c7694-370">若要尋找 **MatchInfo** 物件的屬性，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="c7694-370">To find the properties of a **MatchInfo** object, type the following command:</span></span>

`Select-String -Path test.txt -Pattern 'test' | Get-Member | Format-List -Property *`

## <span data-ttu-id="c7694-371">相關連結</span><span class="sxs-lookup"><span data-stu-id="c7694-371">RELATED LINKS</span></span>

[<span data-ttu-id="c7694-372">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="c7694-372">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="c7694-373">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="c7694-373">about_Comparison_Operators</span></span>](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md)

[<span data-ttu-id="c7694-374">about_Functions</span><span class="sxs-lookup"><span data-stu-id="c7694-374">about_Functions</span></span>](../Microsoft.PowerShell.Core/About/about_Functions.md)

[<span data-ttu-id="c7694-375">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="c7694-375">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="c7694-376">about_Regular_Expressions</span><span class="sxs-lookup"><span data-stu-id="c7694-376">about_Regular_Expressions</span></span>](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)

[<span data-ttu-id="c7694-377">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="c7694-377">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="c7694-378">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="c7694-378">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[<span data-ttu-id="c7694-379">Get-Command</span><span class="sxs-lookup"><span data-stu-id="c7694-379">Get-Command</span></span>](../Microsoft.PowerShell.Core/Get-Command.md)

[<span data-ttu-id="c7694-380">Get-Member</span><span class="sxs-lookup"><span data-stu-id="c7694-380">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="c7694-381">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="c7694-381">Get-WinEvent</span></span>](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[<span data-ttu-id="c7694-382">Out-File</span><span class="sxs-lookup"><span data-stu-id="c7694-382">Out-File</span></span>](Out-File.md)
