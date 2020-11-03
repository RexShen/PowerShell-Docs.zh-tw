---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convert-string?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Convert-String
ms.openlocfilehash: 29ec9e21277bae02ab94ce5e862787c86a87b439
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203360"
---
# <span data-ttu-id="ceb63-103">Convert-String</span><span class="sxs-lookup"><span data-stu-id="ceb63-103">Convert-String</span></span>

## <span data-ttu-id="ceb63-104">概要</span><span class="sxs-lookup"><span data-stu-id="ceb63-104">SYNOPSIS</span></span>
<span data-ttu-id="ceb63-105">將字串格式化以符合範例。</span><span class="sxs-lookup"><span data-stu-id="ceb63-105">Formats a string to match examples.</span></span>

## <span data-ttu-id="ceb63-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ceb63-106">SYNTAX</span></span>

```
Convert-String [-Example <System.Collections.Generic.List`1[System.Management.Automation.PSObject]>]
 -InputObject <String> [<CommonParameters>]
```

## <span data-ttu-id="ceb63-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="ceb63-107">DESCRIPTION</span></span>

<span data-ttu-id="ceb63-108">**Convert 字串** Cmdlet 會將字串格式化，以符合範例的格式。</span><span class="sxs-lookup"><span data-stu-id="ceb63-108">The **Convert-String** cmdlet formats a string to match the format of examples.</span></span>

## <span data-ttu-id="ceb63-109">範例</span><span class="sxs-lookup"><span data-stu-id="ceb63-109">EXAMPLES</span></span>

### <span data-ttu-id="ceb63-110">範例1：轉換字串的格式</span><span class="sxs-lookup"><span data-stu-id="ceb63-110">Example 1: Convert format of a string</span></span>

```powershell
"Mu Han", "Jim Hance", "David Ahs", "Kim Akers" | Convert-String -Example "Ed Wilson=Wilson, E."
```

```output
Han, M.
Hance, J.
Ahs, D.
Akers, K.
```

<span data-ttu-id="ceb63-111">第一個命令會建立包含 first 和 last 名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="ceb63-111">The first command creates an array that contains first and last names.</span></span>

<span data-ttu-id="ceb63-112">第二個命令會根據範例將名稱格式化。</span><span class="sxs-lookup"><span data-stu-id="ceb63-112">The second command formats the names according to the example.</span></span>
<span data-ttu-id="ceb63-113">它會先將姓氏放在輸出中，後面接著初始。</span><span class="sxs-lookup"><span data-stu-id="ceb63-113">It puts the surname first in the output, followed by an initial.</span></span>

### <span data-ttu-id="ceb63-114">範例2：簡化字串的格式</span><span class="sxs-lookup"><span data-stu-id="ceb63-114">Example 2: Simplify format of a string</span></span>

```powershell
$composers = @("Johann Sebastian Bach", "Wolfgang Amadeus Mozart", "Frederic Francois Chopin", "Johannes Brahms")
$composers | Convert-String -Example "first middle last=last, first"
```

```output
Bach, Johann
Mozart, Wolfgang
Chopin, Frederic
Brahms, Johannes
```

<span data-ttu-id="ceb63-115">第一個命令會建立一個陣列，其中包含名字、中間名和姓氏。</span><span class="sxs-lookup"><span data-stu-id="ceb63-115">The first command creates an array that contains first, middle and last names.</span></span>
<span data-ttu-id="ceb63-116">請注意，最後一個專案沒有中間名。</span><span class="sxs-lookup"><span data-stu-id="ceb63-116">Note that the last entry has no middle name.</span></span>

<span data-ttu-id="ceb63-117">第二個命令會根據範例將名稱格式化。</span><span class="sxs-lookup"><span data-stu-id="ceb63-117">The second command formats the names according to the example.</span></span>
<span data-ttu-id="ceb63-118">它會先將姓氏放在輸出中，後面接著第一個名稱。</span><span class="sxs-lookup"><span data-stu-id="ceb63-118">It puts the last name first in the output, followed by the first name.</span></span>
<span data-ttu-id="ceb63-119">已移除所有的中間名;沒有中間名的專案會正確處理。</span><span class="sxs-lookup"><span data-stu-id="ceb63-119">All middle names removed; entry without middle name is handled correctly.</span></span>

### <span data-ttu-id="ceb63-120">範例3：當字串不符合範例時的輸出管理</span><span class="sxs-lookup"><span data-stu-id="ceb63-120">Example 3: Output management when strings don't match example</span></span>

```powershell
$composers = @("Johann Sebastian Bach", "Wolfgang Amadeus Mozart", "Frederic Francois Chopin", "Johannes Brahms")
$composers | Convert-String -Example "first middle last=middle, first"
```

```output
Sebastian, Johann
Amadeus, Wolfgang
Francois, Frederic
```

<span data-ttu-id="ceb63-121">第一個命令會建立一個陣列，其中包含名字、中間名和姓氏。</span><span class="sxs-lookup"><span data-stu-id="ceb63-121">The first command creates an array that contains first, middle and last names.</span></span>
<span data-ttu-id="ceb63-122">請注意，最後一個專案沒有中間名。</span><span class="sxs-lookup"><span data-stu-id="ceb63-122">Note that the last entry has no middle name.</span></span>

<span data-ttu-id="ceb63-123">第二個命令會根據範例將名稱格式化。</span><span class="sxs-lookup"><span data-stu-id="ceb63-123">The second command formats the names according to the example.</span></span>
<span data-ttu-id="ceb63-124">它會先將 **中間名** 放在輸出中，後面接著名字。</span><span class="sxs-lookup"><span data-stu-id="ceb63-124">It puts the **middle name** first in the output, followed by the first name.</span></span>
<span data-ttu-id="ceb63-125">**$Composers** 中的最後一個專案已略過，因為它不符合範例模式：它沒有中間名。</span><span class="sxs-lookup"><span data-stu-id="ceb63-125">The last entry in **$Composers** is skipped, because it doesn't match the sample pattern: it has no middle name.</span></span>

### <span data-ttu-id="ceb63-126">範例4：具有美加空格的警告</span><span class="sxs-lookup"><span data-stu-id="ceb63-126">Example 4: Caution with beauty spaces</span></span>

```powershell
$composers = @("Antonio Vivaldi", "Richard Wagner ", "Franz Schubert", "Johannes Brahms ")
$composers | Convert-String -Example "Patti Fuller = Fuller, P."
```

```output
 Wagner, R.
 Brahms, J.
```

<span data-ttu-id="ceb63-127">第一個命令會建立第一個和最後一個名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="ceb63-127">The first command creates an array of first and last names.</span></span>
<span data-ttu-id="ceb63-128">請注意，第二個和第四個專案在姓氏之後有額外的尾端空格。</span><span class="sxs-lookup"><span data-stu-id="ceb63-128">Note that second and fourth items have an extra trailing space, after the last name.</span></span>

<span data-ttu-id="ceb63-129">第二個命令會轉換符合範例模式的所有字串： _單字、空格、單字和最後尾端空格_ ，全都在等號前面。</span><span class="sxs-lookup"><span data-stu-id="ceb63-129">The second command converts all strings that match the sample pattern: _word, space, word, and final trailing space_ , all of this before the equal sign.</span></span>
<span data-ttu-id="ceb63-130">此外，請記下輸出中的前置空格。</span><span class="sxs-lookup"><span data-stu-id="ceb63-130">Also, note the leading space in the output.</span></span>

### <span data-ttu-id="ceb63-131">範例5：使用多個模式來格式化處理常式資訊</span><span class="sxs-lookup"><span data-stu-id="ceb63-131">Example 5: Format process information with multiple patterns</span></span>

```powershell
$ExamplePatterns = @(
    @{before='"Hello","World"'; after='World: Hello'},
    @{before='"Hello","1"'; after='1: Hello'},
    @{before='"Hello-World","22"'; after='22: Hello-World'},
    @{before='"hello world","333"'; after='333: hello world'}
)
$Processes = Get-Process   | Select-Object -Property ProcessName, Id | ConvertTo-Csv -NoTypeInformation
$Processes | Convert-String -Example $ExamplePatterns
```

```output
Id: ProcessName
4368: AGSService
8896: Amazon Music Helper
4420: AppleMobileDeviceService
...
11140: git-bash
0: Idle
...
56: Secure System
...
13028: WmiPrvSE
2724: WUDFHost
2980: WUDFHost
3348: WUDFHost
```

<span data-ttu-id="ceb63-132">**$ExamplePatterns** 透過範例在資料中定義不同的預期模式。</span><span class="sxs-lookup"><span data-stu-id="ceb63-132">**$ExamplePatterns** defines different expected patterns in the data, through examples.</span></span>

<span data-ttu-id="ceb63-133">第一個模式是 `@{before='"Hello","World"'; after='World: Hello'}` ，如下所示：以 _雙引號括住的字串、逗號，_ 然後再以 
 _引號括住第二個字組;_ 
_字串中沒有空格。在輸出上：先放置第二個單字，_ 
 _沒有引號，然後輸入一個空格，然後是第一個單字，沒有引號。_</span><span class="sxs-lookup"><span data-stu-id="ceb63-133">The first pattern, `@{before='"Hello","World"'; after='World: Hello'}`, reads as follows: _expect strings where a word comes enclosed in double quotes, then a comma,_
_and then the second, and last, word enclosed in quotes;_
_with no spaces in the string. On the output: place second word first,_
_without quotes, then a single space, and then the first word, without quotes._</span></span>

<span data-ttu-id="ceb63-134">第二個模式是 `@{before='"Hello","1"'; after='1: Hello'}` ，如下所示：以 _雙引號括住的字串、逗號，_ 然後以 
 _引號括住的數位;_ 
_字串中沒有空格。在輸出上：先將數位放在前面，_ 
 _沒有引號，然後輸入一個空格，再加上單字，而不使用引號。_</span><span class="sxs-lookup"><span data-stu-id="ceb63-134">The second pattern, `@{before='"Hello","1"'; after='1: Hello'}`, reads as follows: _expect strings where a word comes enclosed in double quotes, then a comma,_
_and then a number enclosed in quotes;_
_with no spaces in the string. On the output: place the number first,_
_without quotes, then a single space, and then the word, without quotes._</span></span>

<span data-ttu-id="ceb63-135">第三個模式的 `@{before='"Hello-World","22"'; after='22: Hello-World'}` 讀取方式如下：會 _預期字串，其中兩個單字之間的連字號都以雙引號括住_ ，然後以逗號括住，然後以 
 _引號括住數位;_ 
_逗號和第三個雙引號之間沒有空格。_ 
_在輸出上：先放置數位，不加引號，然後輸入一個空格，_ 
然後 _再加上連字號的單字，沒有引號。_</span><span class="sxs-lookup"><span data-stu-id="ceb63-135">The third pattern, `@{before='"Hello-World","22"'; after='22: Hello-World'}`, reads as follows: _expect strings where two words with a hyphen in between come enclosed in_
_double quotes, then a comma, and then a number enclosed in quotes;_
_with no spaces between the comma and the third double quote._
_On the output: place the number first, without quotes, then a single space,_
_and then the hyphenated words, without quotes._</span></span>

<span data-ttu-id="ceb63-136">第四個和最後一個模式的讀取如下所示 `@{before='"hello world","333"'; after='333: hello world'}` ：預期的字串會以雙引號 _括住的兩個字_ 組，然後以雙引號括住，然後以 
 _引號括住數位;_ 
_逗號和第三個雙引號之間沒有空格。_ 
_在輸出上：先放置數位，不加引號，然後輸入一個空格，_ 
然後 _是空格之間有空格的單字，沒有引號。_</span><span class="sxs-lookup"><span data-stu-id="ceb63-136">The fourth, and final, pattern, `@{before='"hello world","333"'; after='333: hello world'}`, reads as follows: _expect strings where two words with a space in between come enclosed in_
_double quotes, then a comma, and then a number enclosed in quotes;_
_with no spaces between the comma and the third double quote._
_On the output: place the number first, without quotes, then a single space,_
_and then the words with the space in between, without quotes._</span></span>

<span data-ttu-id="ceb63-137">第一個命令會使用 Get-Process Cmdlet 取得所有處理常式。</span><span class="sxs-lookup"><span data-stu-id="ceb63-137">The first command gets all processes by using the Get-Process cmdlet.</span></span>
<span data-ttu-id="ceb63-138">此命令會將它們傳遞給 Select-Object Cmdlet，以選取進程名稱和處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="ceb63-138">The command passes them to the Select-Object cmdlet, which selects the process name and process ID.</span></span> <span data-ttu-id="ceb63-139">在管線的結尾，此命令會使用 ConvertTo-Csv Cmdlet，將輸出轉換成逗點分隔值，而不使用類型資訊。</span><span class="sxs-lookup"><span data-stu-id="ceb63-139">At the end of the pipeline, the command converts the output to comma separated values, without type information, by using the ConvertTo-Csv cmdlet.</span></span>
<span data-ttu-id="ceb63-140">命令會將結果儲存在 **$Processes** 變數中。</span><span class="sxs-lookup"><span data-stu-id="ceb63-140">The command stores the results in the **$Processes** variable.</span></span>
<span data-ttu-id="ceb63-141">**$Processes** 現在包含進程名稱和 PID。</span><span class="sxs-lookup"><span data-stu-id="ceb63-141">**$Processes** now contains process names and PID.</span></span>

<span data-ttu-id="ceb63-142">第二個命令會指定變更輸入專案順序的範例變數。</span><span class="sxs-lookup"><span data-stu-id="ceb63-142">The second command specifies an example variable that changes the order of the input items.</span></span>
<span data-ttu-id="ceb63-143">此命令會將 **$Processes** 中的每個字串。</span><span class="sxs-lookup"><span data-stu-id="ceb63-143">The command coverts each string in **$Processes** .</span></span>

><span data-ttu-id="ceb63-144">**注意** 第四個模式會隱含地指出以空格分隔的兩個或多個單字相符。</span><span class="sxs-lookup"><span data-stu-id="ceb63-144">**Note** The fourth pattern implicitly says that two or more words separated by spaces are matched.</span></span>
>
><span data-ttu-id="ceb63-145">如果沒有第四個模式，則只會比對以雙引號括住之字串的第一個字組。</span><span class="sxs-lookup"><span data-stu-id="ceb63-145">Without the fourth pattern, only the first word of the string enclosed in double quotes is matched.</span></span>

## <span data-ttu-id="ceb63-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ceb63-146">PARAMETERS</span></span>

### <span data-ttu-id="ceb63-147">-範例</span><span class="sxs-lookup"><span data-stu-id="ceb63-147">-Example</span></span>

<span data-ttu-id="ceb63-148">指定目標格式的範例清單。</span><span class="sxs-lookup"><span data-stu-id="ceb63-148">Specifies a list of examples of the target format.</span></span>
<span data-ttu-id="ceb63-149">指定以等於 (=) 號分隔的配對，並以左邊的來源模式和右邊的目標模式，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ceb63-149">Specify pairs separated by the equal (=) sign, with the source pattern on the left and the target pattern on the right, as in the following examples:</span></span>

* `-Example "Hello World=World, Hello"`
* `-Example "Hello World=World: Hello",'"Hello","1"=1: Hello'`

><span data-ttu-id="ceb63-150">**注意** 第二個範例會使用模式清單</span><span class="sxs-lookup"><span data-stu-id="ceb63-150">**Note** The second example uses a list of patterns</span></span>

<span data-ttu-id="ceb63-151">或者，指定包含屬性 **之前** 和 **之後** 的雜湊表清單。</span><span class="sxs-lookup"><span data-stu-id="ceb63-151">Alternatively, specify a list of hash tables that contain **Before** and **After** properties.</span></span>

* `-Example @{before='"Hello","World"'; after='World: Hello'}, @{before='"Hello","1"'; after='1: Hello'}`

><span data-ttu-id="ceb63-152">**注意** 請避免在等號前後使用空格，因為它們被視為模式的一部分。</span><span class="sxs-lookup"><span data-stu-id="ceb63-152">**Caution** Avoid using spaces around the equal sign, as they are treated as part of the pattern.</span></span>

```yaml
Type: System.Collections.Generic.List`1[System.Management.Automation.PSObject]
Parameter Sets: (All)
Aliases: E

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ceb63-153">-InputObject</span><span class="sxs-lookup"><span data-stu-id="ceb63-153">-InputObject</span></span>

<span data-ttu-id="ceb63-154">指定要格式化的字串。</span><span class="sxs-lookup"><span data-stu-id="ceb63-154">Specifies a string to format.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ceb63-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ceb63-155">CommonParameters</span></span>

<span data-ttu-id="ceb63-156">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="ceb63-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ceb63-157">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="ceb63-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ceb63-158">輸入</span><span class="sxs-lookup"><span data-stu-id="ceb63-158">INPUTS</span></span>

### <span data-ttu-id="ceb63-159">String</span><span class="sxs-lookup"><span data-stu-id="ceb63-159">String</span></span>

<span data-ttu-id="ceb63-160">您可以透過管道將字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ceb63-160">You can pipe strings to this cmdlet.</span></span>

## <span data-ttu-id="ceb63-161">輸出</span><span class="sxs-lookup"><span data-stu-id="ceb63-161">OUTPUTS</span></span>

### <span data-ttu-id="ceb63-162">String</span><span class="sxs-lookup"><span data-stu-id="ceb63-162">String</span></span>

<span data-ttu-id="ceb63-163">這個 Cmdlet 會傳回字串。</span><span class="sxs-lookup"><span data-stu-id="ceb63-163">This cmdlet returns a string.</span></span>

## <span data-ttu-id="ceb63-164">注意</span><span class="sxs-lookup"><span data-stu-id="ceb63-164">NOTES</span></span>

## <span data-ttu-id="ceb63-165">相關連結</span><span class="sxs-lookup"><span data-stu-id="ceb63-165">RELATED LINKS</span></span>

[<span data-ttu-id="ceb63-166">ConvertFrom-String</span><span class="sxs-lookup"><span data-stu-id="ceb63-166">ConvertFrom-String</span></span>](ConvertFrom-String.md)

[<span data-ttu-id="ceb63-167">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="ceb63-167">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="ceb63-168">Get-Process</span><span class="sxs-lookup"><span data-stu-id="ceb63-168">Get-Process</span></span>](../Microsoft.PowerShell.Management/Get-Process.md)

[<span data-ttu-id="ceb63-169">Out-String</span><span class="sxs-lookup"><span data-stu-id="ceb63-169">Out-String</span></span>](Out-String.md)

[<span data-ttu-id="ceb63-170">Select-Object</span><span class="sxs-lookup"><span data-stu-id="ceb63-170">Select-Object</span></span>](Select-Object.md)
