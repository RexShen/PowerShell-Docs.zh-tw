---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-string?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-String
ms.openlocfilehash: 95601a4f5f42700c4de7d6ad721ee898b22bab84
ms.sourcegitcommit: 9a8bb1b459b5939c95e1f6d9499fcb13d01a58c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "93206107"
---
# <span data-ttu-id="00cfe-103">Select-String</span><span class="sxs-lookup"><span data-stu-id="00cfe-103">Select-String</span></span>

## <span data-ttu-id="00cfe-104">概要</span><span class="sxs-lookup"><span data-stu-id="00cfe-104">SYNOPSIS</span></span>
<span data-ttu-id="00cfe-105">尋找字串和檔案中的文字。</span><span class="sxs-lookup"><span data-stu-id="00cfe-105">Finds text in strings and files.</span></span>

## <span data-ttu-id="00cfe-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="00cfe-106">SYNTAX</span></span>

### <span data-ttu-id="00cfe-107">File (預設值)</span><span class="sxs-lookup"><span data-stu-id="00cfe-107">File (Default)</span></span>

```
Select-String [-Pattern] <String[]> [-Path] <String[]> [-SimpleMatch] [-CaseSensitive] [-Quiet]
 [-List] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch] [-AllMatches] [-Encoding <String>]
 [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="00cfe-108">Object</span><span class="sxs-lookup"><span data-stu-id="00cfe-108">Object</span></span>

```
Select-String -InputObject <PSObject> [-Pattern] <String[]> [-SimpleMatch] [-CaseSensitive] [-Quiet]
 [-List] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch] [-AllMatches] [-Encoding <String>]
 [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="00cfe-109">LiteralFile</span><span class="sxs-lookup"><span data-stu-id="00cfe-109">LiteralFile</span></span>

```
Select-String [-Pattern] <String[]> -LiteralPath <String[]> [-SimpleMatch] [-CaseSensitive] [-Quiet]
 [-List] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch] [-AllMatches] [-Encoding <String>]
 [-Context <Int32[]>] [<CommonParameters>]
```

## <span data-ttu-id="00cfe-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="00cfe-110">DESCRIPTION</span></span>

<span data-ttu-id="00cfe-111">此 `Select-String` Cmdlet 會搜尋輸入字串和檔案中的文字和文字模式。</span><span class="sxs-lookup"><span data-stu-id="00cfe-111">The `Select-String` cmdlet searches for text and text patterns in input strings and files.</span></span> <span data-ttu-id="00cfe-112">您可以使用 `Select-String` 類似于 UNIX 中的 **Grep** 或 Windows 中的 **findstr.exe** 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-112">You can use `Select-String` similar to **grep** in UNIX or **findstr.exe** in Windows.</span></span>

<span data-ttu-id="00cfe-113">`Select-String` 以文字行為基礎。</span><span class="sxs-lookup"><span data-stu-id="00cfe-113">`Select-String` is based on lines of text.</span></span> <span data-ttu-id="00cfe-114">依預設， `Select-String` 會在每一行中尋找第一個相符項，而且每個相符項都會顯示檔案名、行號，以及行中包含相符項的所有文字。</span><span class="sxs-lookup"><span data-stu-id="00cfe-114">By default, `Select-String` finds the first match in each line and, for each match, it displays the file name, line number, and all text in the line containing the match.</span></span> <span data-ttu-id="00cfe-115">您可以導向 `Select-String` 找出每行的多個相符專案、顯示相符專案之前和之後的文字，或是顯示 (True 或 False 的布林值) 指出是否找到相符專案。</span><span class="sxs-lookup"><span data-stu-id="00cfe-115">You can direct `Select-String` to find multiple matches per line, display text before and after the match, or display a Boolean value (True or False) that indicates whether a match is found.</span></span>

<span data-ttu-id="00cfe-116">`Select-String` 使用正則運算式比對，但它也可以執行比對，在輸入中搜尋您所指定的文字。</span><span class="sxs-lookup"><span data-stu-id="00cfe-116">`Select-String` uses regular expression matching, but it can also perform a match that searches the input for the text that you specify.</span></span>

<span data-ttu-id="00cfe-117">`Select-String` 可以顯示所有文字相符專案，或在每個輸入檔案中的第一個相符專案之後停止。</span><span class="sxs-lookup"><span data-stu-id="00cfe-117">`Select-String` can display all the text matches or stop after the first match in each input file.</span></span>
<span data-ttu-id="00cfe-118">`Select-String` 可以用來顯示所有不符合指定模式的文字。</span><span class="sxs-lookup"><span data-stu-id="00cfe-118">`Select-String` can be used to display all text that doesn't match the specified pattern.</span></span>

<span data-ttu-id="00cfe-119">您也可以指定 `Select-String` 應該預期特定字元編碼，例如當您搜尋 Unicode 文字的檔案時。</span><span class="sxs-lookup"><span data-stu-id="00cfe-119">You can also specify that `Select-String` should expect a particular character encoding, such as when you're searching files of Unicode text.</span></span> <span data-ttu-id="00cfe-120">`Select-String` 使用位元組順序標記 (BOM) 來偵測檔案的編碼格式。</span><span class="sxs-lookup"><span data-stu-id="00cfe-120">`Select-String` uses the byte-order-mark (BOM) to detect the encoding format of the file.</span></span> <span data-ttu-id="00cfe-121">如果檔案沒有 BOM，則會假設編碼為 UTF8。</span><span class="sxs-lookup"><span data-stu-id="00cfe-121">If the file has no BOM, it assumes the encoding is UTF8.</span></span>

## <span data-ttu-id="00cfe-122">範例</span><span class="sxs-lookup"><span data-stu-id="00cfe-122">EXAMPLES</span></span>

### <span data-ttu-id="00cfe-123">範例1：尋找區分大小寫的相符項</span><span class="sxs-lookup"><span data-stu-id="00cfe-123">Example 1: Find a case-sensitive match</span></span>

<span data-ttu-id="00cfe-124">此範例會對從管線傳送到 Cmdlet 的文字進行區分大小寫的比對 `Select-String` 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-124">This example does a case-sensitive match of the text that was sent down the pipeline to the `Select-String` cmdlet.</span></span>

```powershell
'Hello', 'HELLO' | Select-String -Pattern 'HELLO' -CaseSensitive -SimpleMatch
```

<span data-ttu-id="00cfe-125">文字字串 **Hello** 和 **Hello** 會向下傳送至 `Select-String` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="00cfe-125">The text strings **Hello** and **HELLO** are sent down the pipeline to the `Select-String` cmdlet.</span></span>
<span data-ttu-id="00cfe-126">`Select-String` 使用 **Pattern** 參數指定 **HELLO** 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-126">`Select-String` uses the **Pattern** parameter to specify **HELLO** .</span></span> <span data-ttu-id="00cfe-127">**CaseSensitive** 參數指定案例必須僅符合大寫模式。</span><span class="sxs-lookup"><span data-stu-id="00cfe-127">The **CaseSensitive** parameter specifies that the case must match only the upper-case pattern.</span></span> <span data-ttu-id="00cfe-128">**SimpleMatch** 是選擇性參數，可指定模式中的字串不會被視為正則運算式。</span><span class="sxs-lookup"><span data-stu-id="00cfe-128">**SimpleMatch** is an optional parameter and specifies that the string in the pattern isn't interpreted as a regular expression.</span></span>
<span data-ttu-id="00cfe-129">`Select-String` 在 PowerShell 主控台中顯示 **HELLO** 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-129">`Select-String` displays **HELLO** in the PowerShell console.</span></span>

### <span data-ttu-id="00cfe-130">範例2：在文字檔中尋找相符專案</span><span class="sxs-lookup"><span data-stu-id="00cfe-130">Example 2: Find matches in text files</span></span>

<span data-ttu-id="00cfe-131">此命令會 `.txt` 在目前目錄中搜尋副檔名為的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="00cfe-131">This command searches all files with the `.txt` file name extension in the current directory.</span></span> <span data-ttu-id="00cfe-132">輸出會顯示這些檔案中包含指定字串的行。</span><span class="sxs-lookup"><span data-stu-id="00cfe-132">The output displays the lines in those files that include the specified string.</span></span>

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

<span data-ttu-id="00cfe-133">在此範例中， `Get-Alias` 和 `Get-Command` 會與 Cmdlet 搭配使用 `Out-File` ，以在目前的目錄中建立兩個文字檔， **Alias.txt** 和 **Command.txt** 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-133">In this example, `Get-Alias` and `Get-Command` are used with the `Out-File` cmdlet to create two text files in the current directory, **Alias.txt** and **Command.txt** .</span></span>

<span data-ttu-id="00cfe-134">`Select-String` 使用 **Path** 參數搭配星號 (`*`) 萬用字元來搜尋目前目錄中副檔名為的所有檔案 `.txt` 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-134">`Select-String` uses the **Path** parameter with the asterisk (`*`) wildcard to search all files in the current directory with the file name extension `.txt`.</span></span> <span data-ttu-id="00cfe-135">**Pattern** 參數指定要與 **Get** 相符的文字。</span><span class="sxs-lookup"><span data-stu-id="00cfe-135">The **Pattern** parameter specifies the text to match **Get-** .</span></span> <span data-ttu-id="00cfe-136">`Select-String` 在 PowerShell 主控台中顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="00cfe-136">`Select-String` displays the output in the PowerShell console.</span></span> <span data-ttu-id="00cfe-137">檔案名和行號會在包含 **模式** 參數相符項的每一行內容前面。</span><span class="sxs-lookup"><span data-stu-id="00cfe-137">The file name and line number precede each line of content that contains a match for the **Pattern** parameter.</span></span>

### <span data-ttu-id="00cfe-138">範例3：尋找模式相符</span><span class="sxs-lookup"><span data-stu-id="00cfe-138">Example 3: Find a pattern match</span></span>

<span data-ttu-id="00cfe-139">在此範例中，會搜尋多個檔案，以尋找指定模式的相符專案。</span><span class="sxs-lookup"><span data-stu-id="00cfe-139">In this example, multiple files are searched to find matches for the specified pattern.</span></span> <span data-ttu-id="00cfe-140">此模式會使用正則運算式數量詞。</span><span class="sxs-lookup"><span data-stu-id="00cfe-140">The pattern uses a regular expression quantifier.</span></span> <span data-ttu-id="00cfe-141">如需詳細資訊，請參閱 [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/About_Regular_Expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="00cfe-141">For more information, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/About_Regular_Expressions.md).</span></span>

```powershell
Select-String -Path "$PSHOME\en-US\*.txt" -Pattern '\?'
```

```Output
C:\Program Files\PowerShell\6\en-US\default.help.txt:27:    beginning at https://go.microsoft.com/fwlink/?LinkID=108518.
C:\Program Files\PowerShell\6\en-US\default.help.txt:50:    or go to: https://go.microsoft.com/fwlink/?LinkID=210614
```

<span data-ttu-id="00cfe-142">此 `Select-String` Cmdlet 會使用兩個參數： **路徑** 和 **模式** 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-142">The `Select-String` cmdlet uses two parameters, **Path** and **Pattern** .</span></span> <span data-ttu-id="00cfe-143">**Path** 參數 `$PSHOME` 會使用指定 PowerShell 目錄的變數。</span><span class="sxs-lookup"><span data-stu-id="00cfe-143">The **Path** parameter uses the variable `$PSHOME` that specifies the PowerShell directory.</span></span> <span data-ttu-id="00cfe-144">路徑的其餘部分包含子目錄 **en-us** ，並指定目錄中的每個檔案 `*.txt` 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-144">The remainder of the path includes the subdirectory **en-US** and specifies each `*.txt` file in the directory.</span></span> <span data-ttu-id="00cfe-145">**Pattern** 參數指定要符合每個檔案中的問號 (`?`) 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-145">The **Pattern** parameter specifies to match a question mark (`?`) in each file.</span></span> <span data-ttu-id="00cfe-146">使用反斜線 (`\`) 作為 escape 字元，而且是必要的，因為問號 (`?`) 是正則運算式數量詞。</span><span class="sxs-lookup"><span data-stu-id="00cfe-146">A backslash (`\`) is used as an escape character and is necessary because the question mark (`?`) is a regular expression quantifier.</span></span> <span data-ttu-id="00cfe-147">`Select-String` 在 PowerShell 主控台中顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="00cfe-147">`Select-String` displays the output in the PowerShell console.</span></span> <span data-ttu-id="00cfe-148">檔案名和行號會在包含 **模式** 參數相符項的每一行內容前面。</span><span class="sxs-lookup"><span data-stu-id="00cfe-148">The file name and line number precede each line of content that contains a match for the **Pattern** parameter.</span></span>

### <span data-ttu-id="00cfe-149">範例4：在函式中使用 Select-String</span><span class="sxs-lookup"><span data-stu-id="00cfe-149">Example 4: Use Select-String in a function</span></span>

<span data-ttu-id="00cfe-150">這個範例會建立一個函式，以搜尋 PowerShell 說明檔中的模式。</span><span class="sxs-lookup"><span data-stu-id="00cfe-150">This example creates a function to search for a pattern in the PowerShell help files.</span></span> <span data-ttu-id="00cfe-151">在此範例中，此函式只存在於 PowerShell 會話中。</span><span class="sxs-lookup"><span data-stu-id="00cfe-151">For this example, the function only exists in the PowerShell session.</span></span> <span data-ttu-id="00cfe-152">當 PowerShell 會話關閉時，就會刪除該函式。</span><span class="sxs-lookup"><span data-stu-id="00cfe-152">When the PowerShell session is closed, the function is deleted.</span></span> <span data-ttu-id="00cfe-153">如需詳細資訊，請參閱 [about_Functions](../Microsoft.PowerShell.Core/About/about_Functions.md)。</span><span class="sxs-lookup"><span data-stu-id="00cfe-153">For more information, see [about_Functions](../Microsoft.PowerShell.Core/About/about_Functions.md).</span></span>

```
PS> Function Search-Help
>> {
>> $PSHelp = "$PSHOME\en-US\*.txt"
>> Select-String -Path $PSHelp -Pattern 'About_'
>> }
PS>

PS> Search-Help

C:\Windows\System32\WindowsPowerShell\v1.0\en-US\about_ActivityCommonParameters.help.txt:2:   about_ActivityCommonParameters
C:\Windows\System32\WindowsPowerShell\v1.0\en-US\about_ActivityCommonParameters.help.txt:31:  see about_WorkflowCommonParameters.
C:\Windows\System32\WindowsPowerShell\v1.0\en-US\about_ActivityCommonParameters.help.txt:33:  about_CommonParameters.
```

<span data-ttu-id="00cfe-154">函式會建立在 PowerShell 命令列上。</span><span class="sxs-lookup"><span data-stu-id="00cfe-154">The function is created on the PowerShell command line.</span></span> <span data-ttu-id="00cfe-155">此 `Function` 命令會使用名稱 **搜尋-Help** 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-155">The `Function` command uses the name **Search-Help** .</span></span> <span data-ttu-id="00cfe-156">按 **enter** 鍵，開始將語句新增至函式。</span><span class="sxs-lookup"><span data-stu-id="00cfe-156">Press **Enter** to begin adding statements to the function.</span></span> <span data-ttu-id="00cfe-157">從 `>>` 提示字元加入每個語句，然後按下 **enter** ，如範例所示。</span><span class="sxs-lookup"><span data-stu-id="00cfe-157">From the `>>` prompt, add each statement and press **Enter** as shown in the example.</span></span> <span data-ttu-id="00cfe-158">新增右括弧之後，您會回到 PowerShell 提示字元。</span><span class="sxs-lookup"><span data-stu-id="00cfe-158">After the closing bracket is added, you're returned to a PowerShell prompt.</span></span>

<span data-ttu-id="00cfe-159">函數包含兩個命令。</span><span class="sxs-lookup"><span data-stu-id="00cfe-159">The function contains two commands.</span></span> <span data-ttu-id="00cfe-160">`$PSHelp`變數會儲存 PowerShell 說明檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="00cfe-160">The `$PSHelp` variable stores the path to the PowerShell help files.</span></span> <span data-ttu-id="00cfe-161">`$PSHOME` 是具有子目錄 **en-us** 的 PowerShell 安裝目錄，指定目錄中的每個檔案 `*.txt` 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-161">`$PSHOME` is the PowerShell installation directory with the subdirectory **en-US** that specifies each `*.txt` file in the directory.</span></span>

<span data-ttu-id="00cfe-162">`Select-String`函數中的命令會使用 **路徑** 和 **模式** 參數。</span><span class="sxs-lookup"><span data-stu-id="00cfe-162">The `Select-String` command in the function uses the **Path** and **Pattern** parameters.</span></span> <span data-ttu-id="00cfe-163">**Path** 參數會使用 `$PSHelp` 變數來取得路徑。</span><span class="sxs-lookup"><span data-stu-id="00cfe-163">The **Path** parameter uses the `$PSHelp` variable to get the path.</span></span> <span data-ttu-id="00cfe-164">**Pattern** 參數會使用字串 **About_** 作為搜尋準則。</span><span class="sxs-lookup"><span data-stu-id="00cfe-164">The **Pattern** parameter uses the string **About_** as the search criteria.</span></span>

<span data-ttu-id="00cfe-165">若要執行函數，請輸入 `Search-Help` 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-165">To run the function, type `Search-Help`.</span></span> <span data-ttu-id="00cfe-166">函數的 `Select-String` 命令會在 PowerShell 主控台中顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="00cfe-166">The function's `Select-String` command displays the output in the PowerShell console.</span></span>

### <span data-ttu-id="00cfe-167">範例5：在 Windows 事件記錄檔中搜尋字串</span><span class="sxs-lookup"><span data-stu-id="00cfe-167">Example 5: Search for a string in a Windows event log</span></span>

<span data-ttu-id="00cfe-168">此範例會在 Windows 事件記錄檔中搜尋字串。</span><span class="sxs-lookup"><span data-stu-id="00cfe-168">This example searches for a string in a Windows event log.</span></span> <span data-ttu-id="00cfe-169">變數 `$_` 代表管線中的目前物件。</span><span class="sxs-lookup"><span data-stu-id="00cfe-169">The variable `$_` represents the current object in the pipeline.</span></span> <span data-ttu-id="00cfe-170">如需詳細資訊，請參閱 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="00cfe-170">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

```powershell
$Events = Get-WinEvent -LogName Application -MaxEvents 50
$Events | Select-String -InputObject {$_.message} -Pattern 'Failed'
```

<span data-ttu-id="00cfe-171">此 `Get-WinEvent` Cmdlet 會使用 **LogName** 參數來指定應用程式記錄檔。</span><span class="sxs-lookup"><span data-stu-id="00cfe-171">The `Get-WinEvent` cmdlet uses the **LogName** parameter to specify the Application log.</span></span> <span data-ttu-id="00cfe-172">**MaxEvents** 參數會從記錄檔中取得50最新的事件。</span><span class="sxs-lookup"><span data-stu-id="00cfe-172">The **MaxEvents** parameter gets the 50 most recent events from the log.</span></span> <span data-ttu-id="00cfe-173">記錄內容會儲存在名為的變數中 `$Events` 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-173">The log content is stored in the variable named `$Events`.</span></span>

<span data-ttu-id="00cfe-174">此 `$Events` 變數會向下傳送至 `Select-String` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="00cfe-174">The `$Events` variable is sent down the pipeline to the `Select-String` cmdlet.</span></span> <span data-ttu-id="00cfe-175">`Select-String` 使用 **InputObject** 參數。</span><span class="sxs-lookup"><span data-stu-id="00cfe-175">`Select-String` uses the **InputObject** parameter.</span></span> <span data-ttu-id="00cfe-176">`$_`變數代表目前的物件，而且 `message` 是事件的屬性。</span><span class="sxs-lookup"><span data-stu-id="00cfe-176">The `$_` variable represents the current object and `message` is a property of the event.</span></span> <span data-ttu-id="00cfe-177">**Pattern** 參數物種字串 **失敗** ，並在中搜尋相符專案 `$_.message` 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-177">The **Pattern** parameter species the string **Failed** and searches for matches in `$_.message`.</span></span> <span data-ttu-id="00cfe-178">`Select-String` 在 PowerShell 主控台中顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="00cfe-178">`Select-String` displays the output in the PowerShell console.</span></span>

### <span data-ttu-id="00cfe-179">範例6：在子目錄中尋找字串</span><span class="sxs-lookup"><span data-stu-id="00cfe-179">Example 6: Find a string in subdirectories</span></span>

<span data-ttu-id="00cfe-180">此範例會在目錄及其所有子目錄中搜尋特定的文字字串。</span><span class="sxs-lookup"><span data-stu-id="00cfe-180">This example searches a directory and all of its subdirectories for a specific text string.</span></span>

```powershell
Get-ChildItem -Path C:\Windows\System32\*.txt -Recurse | Select-String -Pattern 'Microsoft' -CaseSensitive
```

<span data-ttu-id="00cfe-181">`Get-ChildItem` 使用 **Path** 參數來指定 **C:\Windows\System32 \* .txt** 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-181">`Get-ChildItem` uses the **Path** parameter to specify **C:\Windows\System32\*.txt** .</span></span> <span data-ttu-id="00cfe-182">**遞迴** 參數包含子目錄。</span><span class="sxs-lookup"><span data-stu-id="00cfe-182">The **Recurse** parameter includes the subdirectories.</span></span> <span data-ttu-id="00cfe-183">物件會向下傳送到管線 `Select-String` 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-183">The objects are sent down the pipeline to `Select-String`.</span></span>

<span data-ttu-id="00cfe-184">`Select-String` 使用 **Pattern** 參數，並指定 **Microsoft** 字串。</span><span class="sxs-lookup"><span data-stu-id="00cfe-184">`Select-String` uses the **Pattern** parameter and specifies the string **Microsoft** .</span></span> <span data-ttu-id="00cfe-185">**CaseSensitive** 參數是用來符合字串的確切大小寫。</span><span class="sxs-lookup"><span data-stu-id="00cfe-185">The **CaseSensitive** parameter is used to match the exact case of the string.</span></span> <span data-ttu-id="00cfe-186">`Select-String` 在 PowerShell 主控台中顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="00cfe-186">`Select-String` displays the output in the PowerShell console.</span></span>

> [!NOTE]
> <span data-ttu-id="00cfe-187">根據您的許可權，您可能會在輸出中看到 **拒絕存取** 訊息。</span><span class="sxs-lookup"><span data-stu-id="00cfe-187">Dependent upon your permissions, you might see **Access denied** messages in the output.</span></span>

### <span data-ttu-id="00cfe-188">範例7：尋找不符合模式的字串</span><span class="sxs-lookup"><span data-stu-id="00cfe-188">Example 7: Find strings that do not match a pattern</span></span>

<span data-ttu-id="00cfe-189">此範例顯示如何排除不符合模式的資料行。</span><span class="sxs-lookup"><span data-stu-id="00cfe-189">This example shows how to exclude lines of data that don't match a pattern.</span></span>

```powershell
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\Command.txt -Pattern 'Get', 'Set'  -NotMatch
```

<span data-ttu-id="00cfe-190">`Get-Command`Cmdlet 會將物件沿著管線向下傳送至， `Out-File` 以在目前的目錄中建立 **Command.txt** 檔案。</span><span class="sxs-lookup"><span data-stu-id="00cfe-190">The `Get-Command` cmdlet sends objects down the pipeline to the `Out-File` to create the **Command.txt** file in the current directory.</span></span> <span data-ttu-id="00cfe-191">`Select-String` 使用 **Path** 參數來指定 **Command.txt** 檔。</span><span class="sxs-lookup"><span data-stu-id="00cfe-191">`Select-String` uses the **Path** parameter to specify the **Command.txt** file.</span></span> <span data-ttu-id="00cfe-192">**Pattern** 參數會指定 **Get** 和 **Set** 做為搜尋模式。</span><span class="sxs-lookup"><span data-stu-id="00cfe-192">The **Pattern** parameter specifies **Get** and **Set** as the search pattern.</span></span> <span data-ttu-id="00cfe-193">**NotMatch** 參數會將 **Get** 和 **Set** 從結果中排除。</span><span class="sxs-lookup"><span data-stu-id="00cfe-193">The **NotMatch** parameter excludes **Get** and **Set** from the results.</span></span>
<span data-ttu-id="00cfe-194">`Select-String` 在 PowerShell 主控台中顯示未包含 **Get** 或 **Set** 的輸出。</span><span class="sxs-lookup"><span data-stu-id="00cfe-194">`Select-String` displays the output in the PowerShell console that doesn't include **Get** or **Set** .</span></span>

### <span data-ttu-id="00cfe-195">範例8：在相符的前後尋找行</span><span class="sxs-lookup"><span data-stu-id="00cfe-195">Example 8: Find lines before and after a match</span></span>

<span data-ttu-id="00cfe-196">此範例示範如何取得相符模式前後的行。</span><span class="sxs-lookup"><span data-stu-id="00cfe-196">This example shows how to get the lines before and after the matched pattern.</span></span>

```powershell
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\Command.txt -Pattern 'Get-Computer' -Context 2, 3
```

```Output
  Command.txt:1186:Cmdlet          Get-CmsMessage            3.0.0.0    Microsoft.PowerShell.Security
  Command.txt:1187:Cmdlet          Get-Command               3.0.0.0    Microsoft.PowerShell.Core
> Command.txt:1188:Cmdlet          Get-ComputerInfo          3.1.0.0    Microsoft.PowerShell.Management
> Command.txt:1189:Cmdlet          Get-ComputerRestorePoint  3.1.0.0    Microsoft.PowerShell.Management
  Command.txt:1190:Cmdlet          Get-Content               3.1.0.0    Microsoft.PowerShell.Management
  Command.txt:1191:Cmdlet          Get-ControlPanelItem      3.1.0.0    Microsoft.PowerShell.Management
  Command.txt:1192:Cmdlet          Get-Counter               3.0.0.0    Microsoft.PowerShell.Diagnostics
```

<span data-ttu-id="00cfe-197">`Get-Command`Cmdlet 會將物件沿著管線向下傳送至， `Out-File` 以在目前的目錄中建立 **Command.txt** 檔案。</span><span class="sxs-lookup"><span data-stu-id="00cfe-197">The `Get-Command` cmdlet sends objects down the pipeline to the `Out-File` to create the **Command.txt** file in the current directory.</span></span> <span data-ttu-id="00cfe-198">`Select-String` 使用 **Path** 參數來指定 **Command.txt** 檔。</span><span class="sxs-lookup"><span data-stu-id="00cfe-198">`Select-String` uses the **Path** parameter to specify the **Command.txt** file.</span></span> <span data-ttu-id="00cfe-199">**Pattern** 參數會將 **Get 電腦** 指定為搜尋模式。</span><span class="sxs-lookup"><span data-stu-id="00cfe-199">The **Pattern** parameter specifies **Get-Computer** as the search pattern.</span></span> <span data-ttu-id="00cfe-200">**內容** 參數會使用兩個值，前後都有兩個值，並以角括弧 () 來標記輸出中的模式相符 `>` 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-200">The **Context** parameter uses two values, before and after, and marks pattern matches in the output with an angle bracket (`>`).</span></span> <span data-ttu-id="00cfe-201">**CoNtext** 參數會輸出第一個模式比對之前的兩行，並在最後一個模式相符之後輸出三行。</span><span class="sxs-lookup"><span data-stu-id="00cfe-201">The **Context** parameter outputs the two lines before the first pattern match and three lines after the last pattern match.</span></span>

### <span data-ttu-id="00cfe-202">範例9：尋找所有模式相符專案</span><span class="sxs-lookup"><span data-stu-id="00cfe-202">Example 9: Find all pattern matches</span></span>

<span data-ttu-id="00cfe-203">此範例示範 **AllMatches** 參數如何在文字行中尋找每個模式相符。</span><span class="sxs-lookup"><span data-stu-id="00cfe-203">This example shows how the **AllMatches** parameter finds each pattern match in a line of text.</span></span> <span data-ttu-id="00cfe-204">依預設， `Select-String` 只會在文字行中尋找第一次出現的模式。</span><span class="sxs-lookup"><span data-stu-id="00cfe-204">By default, `Select-String` only finds the first occurrence of a pattern in a line of text.</span></span> <span data-ttu-id="00cfe-205">這個範例會使用以 Cmdlet 找到的物件屬性 `Get-Member` 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-205">This example uses object properties that are found with the `Get-Member` cmdlet.</span></span>

```
PS> $A = Get-ChildItem -Path "$PSHOME\en-US\*.txt" | Select-String -Pattern 'PowerShell'

PS> $A

C:\Windows\System32\WindowsPowerShell\v1.0\en-US\about_ActivityCommonParameters.help.txt:5:    Describes the parameters that Windows PowerShell
C:\Windows\System32\WindowsPowerShell\v1.0\en-US\about_ActivityCommonParameters.help.txt:9:    Windows PowerShell Workflow adds the activity common

PS> $A.Matches

Groups   : {0}
Success  : True
Name     : 0
Captures : {0}
Index    : 4
Length   : 10
Value    : PowerShell

PS> $A.Matches.Length

2073

PS> $B = Get-ChildItem -Path "$PSHOME\en-US\*.txt" | Select-String -Pattern 'PowerShell' -AllMatches

PS> $B.Matches.Length

2200
```

<span data-ttu-id="00cfe-206">此 `Get-ChildItem` Cmdlet 會使用 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="00cfe-206">The `Get-ChildItem` cmdlet uses the **Path** parameter.</span></span> <span data-ttu-id="00cfe-207">**Path** 參數 `$PSHOME` 會使用指定 PowerShell 目錄的變數。</span><span class="sxs-lookup"><span data-stu-id="00cfe-207">The **Path** parameter uses the variable `$PSHOME` that specifies the PowerShell directory.</span></span> <span data-ttu-id="00cfe-208">路徑的其餘部分包含子目錄 **en-us** ，並指定目錄中的每個檔案 `*.txt` 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-208">The remainder of the path includes the subdirectory **en-US** and specifies each `*.txt` file in the directory.</span></span> <span data-ttu-id="00cfe-209">`Get-ChildItem`物件會儲存在變數中 `$A` 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-209">The `Get-ChildItem` objects are stored in the `$A` variable.</span></span> <span data-ttu-id="00cfe-210">此 `$A` 變數會向下傳送至 `Select-String` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="00cfe-210">The `$A` variable is sent down the pipeline to the `Select-String` cmdlet.</span></span> <span data-ttu-id="00cfe-211">`Select-String` 使用 **Pattern** 參數來搜尋字串 **PowerShell** 的每個檔案。</span><span class="sxs-lookup"><span data-stu-id="00cfe-211">`Select-String` uses the **Pattern** parameter to search each file for the string **PowerShell** .</span></span>

<span data-ttu-id="00cfe-212">從 PowerShell 命令列中， `$A` 會顯示變數內容。</span><span class="sxs-lookup"><span data-stu-id="00cfe-212">From the PowerShell command line, the `$A` variable contents are displayed.</span></span> <span data-ttu-id="00cfe-213">有一個包含兩次字串 **PowerShell** 的行。</span><span class="sxs-lookup"><span data-stu-id="00cfe-213">There's a line that contains two occurrences of the string **PowerShell** .</span></span>

<span data-ttu-id="00cfe-214">`$A.Matches`屬性會列出每一行上第一次出現的模式 **PowerShell** 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-214">The `$A.Matches` property lists the first occurrence of the pattern **PowerShell** on each line.</span></span>

<span data-ttu-id="00cfe-215">`$A.Matches.Length`屬性會計算每一行上第一次出現的模式 **PowerShell** 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-215">The `$A.Matches.Length` property counts the first occurrence of the pattern **PowerShell** on each line.</span></span>

<span data-ttu-id="00cfe-216">`$B`變數使用相同的 `Get-ChildItem` 和 `Select-String` Cmdlet，但會新增 **AllMatches** 參數。</span><span class="sxs-lookup"><span data-stu-id="00cfe-216">The `$B` variable uses the same `Get-ChildItem` and `Select-String` cmdlets, but adds the **AllMatches** parameter.</span></span> <span data-ttu-id="00cfe-217">**AllMatches** 會在每一行找出每個出現的模式 **PowerShell** 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-217">**AllMatches** finds each occurrence of the pattern **PowerShell** on each line.</span></span> <span data-ttu-id="00cfe-218">和變數中所儲存的物件 `$A` `$B` 是相同的。</span><span class="sxs-lookup"><span data-stu-id="00cfe-218">The objects stored in the `$A` and `$B` variables are identical.</span></span>

<span data-ttu-id="00cfe-219">`$B.Matches.Length`屬性會增加，因為每一行都會計算模式 **PowerShell** 的每個出現次數。</span><span class="sxs-lookup"><span data-stu-id="00cfe-219">The `$B.Matches.Length` property increases because for each line, every occurrence of the pattern **PowerShell** is counted.</span></span>

## <span data-ttu-id="00cfe-220">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="00cfe-220">PARAMETERS</span></span>

### <span data-ttu-id="00cfe-221">-AllMatches</span><span class="sxs-lookup"><span data-stu-id="00cfe-221">-AllMatches</span></span>

<span data-ttu-id="00cfe-222">指出此 Cmdlet 會在每一行文字中搜尋一個以上的相符項。</span><span class="sxs-lookup"><span data-stu-id="00cfe-222">Indicates that the cmdlet searches for more than one match in each line of text.</span></span> <span data-ttu-id="00cfe-223">如果沒有這個參數， `Select-String` 只會在每一行文字中尋找第一個相符的內容。</span><span class="sxs-lookup"><span data-stu-id="00cfe-223">Without this parameter, `Select-String` finds only the first match in each line of text.</span></span>

<span data-ttu-id="00cfe-224">當 `Select-String` 在一行文字中找到一個以上的相符專案時，它仍然只會為該行發出一個 **MatchInfo** 物件，但是 **Matches** 物件的 match 屬性會包含所有相符專案。</span><span class="sxs-lookup"><span data-stu-id="00cfe-224">When `Select-String` finds more than one match in a line of text, it still emits only one **MatchInfo** object for the line, but the **Matches** property of the object contains all the matches.</span></span>

> [!NOTE]
> <span data-ttu-id="00cfe-225">搭配 **SimpleMatch** 參數使用時，會忽略這個參數。</span><span class="sxs-lookup"><span data-stu-id="00cfe-225">This parameter is ignored when used in combination with the **SimpleMatch** parameter.</span></span> <span data-ttu-id="00cfe-226">如果您想要傳回所有相符專案，以及您要搜尋的模式包含正則運算式字元，您必須將這些字元轉義，而不是使用 **SimpleMatch** 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-226">If you wish to return all matches and the pattern that you are searching for contains regular expression characters, you must escape those characters rather than using **SimpleMatch** .</span></span> <span data-ttu-id="00cfe-227">如需有關如何轉義正則運算式的詳細資訊，請參閱 [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md) 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-227">See [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md) for more information about escaping regular expressions.</span></span>

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

### <span data-ttu-id="00cfe-228">-CaseSensitive</span><span class="sxs-lookup"><span data-stu-id="00cfe-228">-CaseSensitive</span></span>

<span data-ttu-id="00cfe-229">指出 Cmdlet 相符專案區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="00cfe-229">Indicates that the cmdlet matches are case-sensitive.</span></span> <span data-ttu-id="00cfe-230">依預設，相符專案不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="00cfe-230">By default, matches aren't case-sensitive.</span></span>

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

### <span data-ttu-id="00cfe-231">-Context</span><span class="sxs-lookup"><span data-stu-id="00cfe-231">-Context</span></span>

<span data-ttu-id="00cfe-232">在符合模式的行之前和之後捕獲指定的行數。</span><span class="sxs-lookup"><span data-stu-id="00cfe-232">Captures the specified number of lines before and after the line that matches the pattern.</span></span>

<span data-ttu-id="00cfe-233">如果您輸入一個數字做為此參數的值，該數字會決定相符項目之前與之後擷取的行數。</span><span class="sxs-lookup"><span data-stu-id="00cfe-233">If you enter one number as the value of this parameter, that number determines the number of lines captured before and after the match.</span></span> <span data-ttu-id="00cfe-234">如果您輸入兩個數字做為該值，第一個數字會決定相符項目之前的行數，而第二個數字會決定相符項目之後的行數。</span><span class="sxs-lookup"><span data-stu-id="00cfe-234">If you enter two numbers as the value, the first number determines the number of lines before the match and the second number determines the number of lines after the match.</span></span> <span data-ttu-id="00cfe-235">例如： `-Context 2,3` 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-235">For example, `-Context 2,3`.</span></span>

<span data-ttu-id="00cfe-236">在預設顯示中，具有相符的行會以右角括弧表示， (`>`) 在顯示的第一個資料行中 (ASCII 62) 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-236">In the default display, lines with a match are indicated by a right angle bracket (`>`) (ASCII 62) in the first column of the display.</span></span> <span data-ttu-id="00cfe-237">未標記的行是上下文。</span><span class="sxs-lookup"><span data-stu-id="00cfe-237">Unmarked lines are the context.</span></span>

<span data-ttu-id="00cfe-238">**CoNtext** 參數不會變更所產生的物件數目 `Select-String` 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-238">The **Context** parameter doesn't change the number of objects generated by `Select-String`.</span></span>
<span data-ttu-id="00cfe-239">`Select-String` 針對每個相符各產生一個 [MatchInfo](/dotnet/api/microsoft.powershell.commands.matchinfo) 物件。</span><span class="sxs-lookup"><span data-stu-id="00cfe-239">`Select-String` generates one [MatchInfo](/dotnet/api/microsoft.powershell.commands.matchinfo) object for each match.</span></span> <span data-ttu-id="00cfe-240">內容會以字串陣列的形式儲存在物件的 **coNtext** 屬性中。</span><span class="sxs-lookup"><span data-stu-id="00cfe-240">The context is stored as an array of strings in the **Context** property of the object.</span></span>

<span data-ttu-id="00cfe-241">當命令的輸出向 `Select-String` 下傳送到另一個 `Select-String` 命令時，接收命令只會搜尋相符行中的文字。</span><span class="sxs-lookup"><span data-stu-id="00cfe-241">When the output of a `Select-String` command is sent down the pipeline to another `Select-String` command, the receiving command searches only the text in the matched line.</span></span> <span data-ttu-id="00cfe-242">符合的行是 **MatchInfo** 物件的 **line** 屬性值，而不是內容行中的文字。</span><span class="sxs-lookup"><span data-stu-id="00cfe-242">The matched line is the value of the **Line** property of the **MatchInfo** object, not the text in the context lines.</span></span> <span data-ttu-id="00cfe-243">因此， **內容** 參數在接收命令上無效 `Select-String` 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-243">As a result, the **Context** parameter isn't valid on the receiving `Select-String` command.</span></span>

<span data-ttu-id="00cfe-244">當內容包含比對時，每個相符項的 **MatchInfo** 物件都會包含所有內容行，但是重迭行只會在顯示中出現一次。</span><span class="sxs-lookup"><span data-stu-id="00cfe-244">When the context includes a match, the **MatchInfo** object for each match includes all the context lines, but the overlapping lines appear only once in the display.</span></span>

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

### <span data-ttu-id="00cfe-245">-Encoding</span><span class="sxs-lookup"><span data-stu-id="00cfe-245">-Encoding</span></span>

<span data-ttu-id="00cfe-246">指定目標檔案的編碼類型。</span><span class="sxs-lookup"><span data-stu-id="00cfe-246">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="00cfe-247">預設值是 `default`。</span><span class="sxs-lookup"><span data-stu-id="00cfe-247">The default value is `default`.</span></span>

<span data-ttu-id="00cfe-248">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="00cfe-248">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="00cfe-249">`ascii` 使用 ASCII (7 位) 字元集。</span><span class="sxs-lookup"><span data-stu-id="00cfe-249">`ascii` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="00cfe-250">`bigendianunicode` 以位元組由大到小的順序使用 UTF-16。</span><span class="sxs-lookup"><span data-stu-id="00cfe-250">`bigendianunicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="00cfe-251">`default` 使用與系統的作用中字碼頁對應的編碼， (通常是 ANSI) 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-251">`default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="00cfe-252">`oem` 使用對應至系統目前 OEM 字碼頁的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="00cfe-252">`oem` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="00cfe-253">`unicode` 使用 UTF-16 和位元組由小到小的位元組順序。</span><span class="sxs-lookup"><span data-stu-id="00cfe-253">`unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="00cfe-254">`utf7` 使用 UTF-7。</span><span class="sxs-lookup"><span data-stu-id="00cfe-254">`utf7` Uses UTF-7.</span></span>
- <span data-ttu-id="00cfe-255">`utf8` 使用 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="00cfe-255">`utf8` Uses UTF-8.</span></span>
- <span data-ttu-id="00cfe-256">`utf32` 以位元組由小到大的位元組順序使用 UTF-32。</span><span class="sxs-lookup"><span data-stu-id="00cfe-256">`utf32` Uses UTF-32 with the little-endian byte order.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, Default, OEM, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="00cfe-257">-Exclude</span><span class="sxs-lookup"><span data-stu-id="00cfe-257">-Exclude</span></span>

<span data-ttu-id="00cfe-258">排除指定的項目。</span><span class="sxs-lookup"><span data-stu-id="00cfe-258">Exclude the specified items.</span></span> <span data-ttu-id="00cfe-259">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="00cfe-259">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="00cfe-260">輸入路徑元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="00cfe-260">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="00cfe-261">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="00cfe-261">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="00cfe-262">-Include</span><span class="sxs-lookup"><span data-stu-id="00cfe-262">-Include</span></span>

<span data-ttu-id="00cfe-263">包含指定的項目。</span><span class="sxs-lookup"><span data-stu-id="00cfe-263">Includes the specified items.</span></span> <span data-ttu-id="00cfe-264">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="00cfe-264">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="00cfe-265">輸入路徑元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="00cfe-265">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="00cfe-266">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="00cfe-266">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="00cfe-267">-InputObject</span><span class="sxs-lookup"><span data-stu-id="00cfe-267">-InputObject</span></span>

<span data-ttu-id="00cfe-268">指定要搜尋的文字。</span><span class="sxs-lookup"><span data-stu-id="00cfe-268">Specifies the text to be searched.</span></span> <span data-ttu-id="00cfe-269">輸入包含文字的變數，或輸入可取得文字的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="00cfe-269">Enter a variable that contains the text, or type a command or expression that gets the text.</span></span>

<span data-ttu-id="00cfe-270">使用 **InputObject** 參數和將字串向下傳送至時不同 `Select-String` 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-270">Using the **InputObject** parameter isn't the same as sending strings down the pipeline to `Select-String`.</span></span>

<span data-ttu-id="00cfe-271">當您將多個字串輸送至 `Select-String` Cmdlet 時，它會在每個字串中搜尋指定的文字，並傳回包含搜尋文字的每個字串。</span><span class="sxs-lookup"><span data-stu-id="00cfe-271">When you pipe more than one string to the `Select-String` cmdlet, it searches for the specified text in each string and returns each string that contains the search text.</span></span>

<span data-ttu-id="00cfe-272">當您使用 **InputObject** 參數提交字串集合時，會 `Select-String` 將集合視為單一合併字串。</span><span class="sxs-lookup"><span data-stu-id="00cfe-272">When you use the **InputObject** parameter to submit a collection of strings, `Select-String` treats the collection as a single combined string.</span></span> <span data-ttu-id="00cfe-273">`Select-String` 如果在任何字串中找到搜尋文字，則會以單位形式傳回字串。</span><span class="sxs-lookup"><span data-stu-id="00cfe-273">`Select-String` returns the strings as a unit if it finds the search text in any string.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: Object
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="00cfe-274">-List</span><span class="sxs-lookup"><span data-stu-id="00cfe-274">-List</span></span>

<span data-ttu-id="00cfe-275">每個輸入檔只會傳回相符文字的第一個實例。</span><span class="sxs-lookup"><span data-stu-id="00cfe-275">Only the first instance of matching text is returned from each input file.</span></span> <span data-ttu-id="00cfe-276">這是取得具有符合正則運算式之內容的檔案清單最有效率的方式。</span><span class="sxs-lookup"><span data-stu-id="00cfe-276">This is the most efficient way to retrieve a list of files that have contents matching the regular expression.</span></span>

<span data-ttu-id="00cfe-277">根據預設， `Select-String` 會針對找到的每個相符項傳回 **MatchInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="00cfe-277">By default, `Select-String` returns a **MatchInfo** object for each match it finds.</span></span>

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

### <span data-ttu-id="00cfe-278">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="00cfe-278">-LiteralPath</span></span>

<span data-ttu-id="00cfe-279">指定要搜尋之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="00cfe-279">Specifies the path to the files to be searched.</span></span> <span data-ttu-id="00cfe-280">**LiteralPath** 參數的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="00cfe-280">The value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="00cfe-281">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="00cfe-281">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="00cfe-282">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="00cfe-282">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="00cfe-283">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="00cfe-283">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span> <span data-ttu-id="00cfe-284">如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="00cfe-284">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralFile
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="00cfe-285">-NotMatch</span><span class="sxs-lookup"><span data-stu-id="00cfe-285">-NotMatch</span></span>

<span data-ttu-id="00cfe-286">**NotMatch** 參數會尋找不符合指定模式的文字。</span><span class="sxs-lookup"><span data-stu-id="00cfe-286">The **NotMatch** parameter finds text that doesn't match the specified pattern.</span></span>

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

### <span data-ttu-id="00cfe-287">-Path</span><span class="sxs-lookup"><span data-stu-id="00cfe-287">-Path</span></span>

<span data-ttu-id="00cfe-288">指定要搜尋之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="00cfe-288">Specifies the path to the files to search.</span></span> <span data-ttu-id="00cfe-289">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="00cfe-289">Wildcards are permitted.</span></span> <span data-ttu-id="00cfe-290">預設位置是本機目錄。</span><span class="sxs-lookup"><span data-stu-id="00cfe-290">The default location is the local directory.</span></span>

<span data-ttu-id="00cfe-291">指定目錄中的檔案，例如 `log1.txt` 、 `*.doc` 或 `*.*` 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-291">Specify files in the directory, such as `log1.txt`, `*.doc`, or `*.*`.</span></span> <span data-ttu-id="00cfe-292">如果您只指定目錄，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="00cfe-292">If you specify only a directory, the command fails.</span></span>

```yaml
Type: System.String[]
Parameter Sets: File
Aliases:

Required: True
Position: 1
Default value: Local directory
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="00cfe-293">-Pattern</span><span class="sxs-lookup"><span data-stu-id="00cfe-293">-Pattern</span></span>

<span data-ttu-id="00cfe-294">指定要在每一行上尋找的文字。</span><span class="sxs-lookup"><span data-stu-id="00cfe-294">Specifies the text to find on each line.</span></span> <span data-ttu-id="00cfe-295">模式值會被視為正則運算式。</span><span class="sxs-lookup"><span data-stu-id="00cfe-295">The pattern value is treated as a regular expression.</span></span>

<span data-ttu-id="00cfe-296">若要深入瞭解正則運算式，請參閱 [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="00cfe-296">To learn about regular expressions, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span></span>

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

### <span data-ttu-id="00cfe-297">-Quiet</span><span class="sxs-lookup"><span data-stu-id="00cfe-297">-Quiet</span></span>

<span data-ttu-id="00cfe-298">指出此 Cmdlet 會傳回布林值 (True 或 False) ，而不是 **MatchInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="00cfe-298">Indicates that the cmdlet returns a Boolean value (True or False), instead of a **MatchInfo** object.</span></span> <span data-ttu-id="00cfe-299">如果找到模式，則值為 True。否則，此值為 False。</span><span class="sxs-lookup"><span data-stu-id="00cfe-299">The value is True if the pattern is found; otherwise the value is False.</span></span>

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

### <span data-ttu-id="00cfe-300">-SimpleMatch</span><span class="sxs-lookup"><span data-stu-id="00cfe-300">-SimpleMatch</span></span>

<span data-ttu-id="00cfe-301">指出此 Cmdlet 會使用簡單比對，而不是正則運算式相符項。</span><span class="sxs-lookup"><span data-stu-id="00cfe-301">Indicates that the cmdlet uses a simple match rather than a regular expression match.</span></span> <span data-ttu-id="00cfe-302">在簡單的比對中，會在 `Select-String` 輸入中搜尋 **Pattern** 參數的文字。</span><span class="sxs-lookup"><span data-stu-id="00cfe-302">In a simple match, `Select-String` searches the input for the text in the **Pattern** parameter.</span></span> <span data-ttu-id="00cfe-303">它不會將 **Pattern** 參數的值解讀為正則運算式語句。</span><span class="sxs-lookup"><span data-stu-id="00cfe-303">It doesn't interpret the value of the **Pattern** parameter as a regular expression statement.</span></span>

<span data-ttu-id="00cfe-304">此外，當使用 **SimpleMatch** 時，所傳回之 **MatchInfo** 物件的 [ **符合** ] 屬性會是空的。</span><span class="sxs-lookup"><span data-stu-id="00cfe-304">Also, when **SimpleMatch** is used, the **Matches** property of the **MatchInfo** object returned is empty.</span></span>

> [!NOTE]
> <span data-ttu-id="00cfe-305">當此參數搭配 **AllMatches** 參數使用時，會忽略 **AllMatches** 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-305">When this parameter is used with the **AllMatches** parameter, the **AllMatches** is ignored.</span></span>

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

### <span data-ttu-id="00cfe-306">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="00cfe-306">CommonParameters</span></span>

<span data-ttu-id="00cfe-307">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="00cfe-307">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="00cfe-308">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="00cfe-308">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="00cfe-309">輸入</span><span class="sxs-lookup"><span data-stu-id="00cfe-309">INPUTS</span></span>

### <span data-ttu-id="00cfe-310">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="00cfe-310">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="00cfe-311">您可以使用管線將具有 **ToString** 方法的任何物件傳送至 `Select-String` 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-311">You can pipe any object that has a **ToString** method to `Select-String`.</span></span>

## <span data-ttu-id="00cfe-312">輸出</span><span class="sxs-lookup"><span data-stu-id="00cfe-312">OUTPUTS</span></span>

### <span data-ttu-id="00cfe-313">Microsoft.PowerShell.Commands.MatchInfo 或 System.Boolean</span><span class="sxs-lookup"><span data-stu-id="00cfe-313">Microsoft.PowerShell.Commands.MatchInfo or System.Boolean</span></span>

<span data-ttu-id="00cfe-314">根據預設，輸出是一組 **MatchInfo** 物件，每個找到的相符項都有一個物件。</span><span class="sxs-lookup"><span data-stu-id="00cfe-314">By default, the output is a set of **MatchInfo** objects with one for each match found.</span></span> <span data-ttu-id="00cfe-315">如果您使用 **Quiet** 參數，則輸出會是布林值，指出是否已找到模式。</span><span class="sxs-lookup"><span data-stu-id="00cfe-315">If you use the **Quiet** parameter, the output is a Boolean value indicating whether the pattern was found.</span></span>

## <span data-ttu-id="00cfe-316">注意</span><span class="sxs-lookup"><span data-stu-id="00cfe-316">NOTES</span></span>

<span data-ttu-id="00cfe-317">`Select-String` 類似于 UNIX 中的 **grep** 或 Windows 中的 **findstr.exe** 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-317">`Select-String` is similar to **grep** in UNIX or **findstr.exe** in Windows.</span></span>

<span data-ttu-id="00cfe-318">Cmdlet 的 **sls** 別名 `Select-String` 是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="00cfe-318">The **sls** alias for the `Select-String` cmdlet was introduced in PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="00cfe-319">根據 [PowerShell 命令的已核准動詞](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands)，Cmdlet 的官方別名前置詞 `Select-*` 為 `sc` ，而不是 `sl` 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-319">According to [Approved Verbs for PowerShell Commands](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands), the official alias prefix for `Select-*` cmdlets is `sc`, not `sl`.</span></span> <span data-ttu-id="00cfe-320">因此，適當的別名 `Select-String` 應該是 `scs` ，而不是 `sls` 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-320">Therefore, the proper alias for `Select-String` should be `scs`, not `sls`.</span></span> <span data-ttu-id="00cfe-321">這是此規則的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="00cfe-321">This is an exception to this rule.</span></span>

<span data-ttu-id="00cfe-322">若要使用 `Select-String` ，請輸入您想要尋找的文字做為 **Pattern** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="00cfe-322">To use `Select-String`, type the text that you want to find as the value of the **Pattern** parameter.</span></span> <span data-ttu-id="00cfe-323">若要指定要搜尋的文字，請使用下列準則：</span><span class="sxs-lookup"><span data-stu-id="00cfe-323">To specify the text to be searched, use the following criteria:</span></span>

- <span data-ttu-id="00cfe-324">在加上引號的字串中輸入文字，然後使用管線將它傳送至 `Select-String` 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-324">Type the text in a quoted string, and then pipe it to `Select-String`.</span></span>
- <span data-ttu-id="00cfe-325">在變數中儲存文字字串，然後將變數指定為 **InputObject** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="00cfe-325">Store a text string in a variable, and then specify the variable as the value of the **InputObject** parameter.</span></span>
- <span data-ttu-id="00cfe-326">如果文字儲存在檔案中，請使用 **path** 參數來指定檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="00cfe-326">If the text is stored in files, use the **Path** parameter to specify the path to the files.</span></span>

<span data-ttu-id="00cfe-327">依預設，會將 `Select-String` **Pattern** 參數的值解釋為正則運算式。</span><span class="sxs-lookup"><span data-stu-id="00cfe-327">By default, `Select-String` interprets the value of the **Pattern** parameter as a regular expression.</span></span> <span data-ttu-id="00cfe-328">如需詳細資訊，請參閱 [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="00cfe-328">For more information, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span></span> <span data-ttu-id="00cfe-329">您可以使用 **SimpleMatch** 參數來覆寫正則運算式比對。</span><span class="sxs-lookup"><span data-stu-id="00cfe-329">You can use the **SimpleMatch** parameter to override the regular expression matching.</span></span> <span data-ttu-id="00cfe-330">**SimpleMatch** 參數會尋找輸入中 **Pattern** 參數值的實例。</span><span class="sxs-lookup"><span data-stu-id="00cfe-330">The **SimpleMatch** parameter finds instances of the value of the **Pattern** parameter in the input.</span></span>

<span data-ttu-id="00cfe-331">的預設輸出 `Select-String` 是 **MatchInfo** 物件，其中包含相符專案的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="00cfe-331">The default output of `Select-String` is a **MatchInfo** object, which includes detailed information about the matches.</span></span> <span data-ttu-id="00cfe-332">當您搜尋檔案中的文字時，物件中的資訊會很有用，因為 **MatchInfo** 物件具有像是 **Filename** 與 **Line** 等屬性。</span><span class="sxs-lookup"><span data-stu-id="00cfe-332">The information in the object is useful when you're searching for text in files, because **MatchInfo** objects have properties such as **Filename** and **Line** .</span></span> <span data-ttu-id="00cfe-333">當輸入不是來自檔案時，這些參數的值會是 **InputStream** 。</span><span class="sxs-lookup"><span data-stu-id="00cfe-333">When the input isn't from the file, the value of these parameters is **InputStream** .</span></span>

<span data-ttu-id="00cfe-334">如果您不需要 **MatchInfo** 物件中的資訊，請使用 **Quiet** 參數。</span><span class="sxs-lookup"><span data-stu-id="00cfe-334">If you don't need the information in the **MatchInfo** object, use the **Quiet** parameter.</span></span> <span data-ttu-id="00cfe-335">**Quiet** 參數會傳回布林值 (True 或 False) 來指出它是否找到相符的，而不是 **MatchInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="00cfe-335">The **Quiet** parameter returns a Boolean value (True or False) to indicate whether it found a match, instead of a **MatchInfo** object.</span></span>

<span data-ttu-id="00cfe-336">當比對片語時， `Select-String` 會使用針對系統所設定的目前文化特性。</span><span class="sxs-lookup"><span data-stu-id="00cfe-336">When matching phrases, `Select-String` uses the current culture that is set for the system.</span></span> <span data-ttu-id="00cfe-337">若要尋找目前的文化特性，請使用 `Get-Culture` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="00cfe-337">To find the current culture, use the `Get-Culture` cmdlet.</span></span>

<span data-ttu-id="00cfe-338">若要尋找 **MatchInfo** 物件的屬性，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="00cfe-338">To find the properties of a **MatchInfo** object, type the following command:</span></span>

`Select-String -Path test.txt -Pattern 'test' | Get-Member | Format-List -Property *`

## <span data-ttu-id="00cfe-339">相關連結</span><span class="sxs-lookup"><span data-stu-id="00cfe-339">RELATED LINKS</span></span>

[<span data-ttu-id="00cfe-340">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="00cfe-340">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="00cfe-341">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="00cfe-341">about_Comparison_Operators</span></span>](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md)

[<span data-ttu-id="00cfe-342">about_Functions</span><span class="sxs-lookup"><span data-stu-id="00cfe-342">about_Functions</span></span>](../Microsoft.PowerShell.Core/About/about_Functions.md)

[<span data-ttu-id="00cfe-343">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="00cfe-343">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="00cfe-344">about_Regular_Expressions</span><span class="sxs-lookup"><span data-stu-id="00cfe-344">about_Regular_Expressions</span></span>](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)

[<span data-ttu-id="00cfe-345">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="00cfe-345">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="00cfe-346">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="00cfe-346">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[<span data-ttu-id="00cfe-347">Get-Command</span><span class="sxs-lookup"><span data-stu-id="00cfe-347">Get-Command</span></span>](../Microsoft.PowerShell.Core/Get-Command.md)

[<span data-ttu-id="00cfe-348">Get-Member</span><span class="sxs-lookup"><span data-stu-id="00cfe-348">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="00cfe-349">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="00cfe-349">Get-WinEvent</span></span>](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[<span data-ttu-id="00cfe-350">Out-File</span><span class="sxs-lookup"><span data-stu-id="00cfe-350">Out-File</span></span>](Out-File.md)
