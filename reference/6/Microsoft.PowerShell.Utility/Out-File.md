---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-file?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-File
ms.openlocfilehash: f3cd58bffde8bcb6dab488a9e40e69d7435133e4
ms.sourcegitcommit: d757d64ea8c8af4d92596e8fbe15f2f40d48d3ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "93206319"
---
# <span data-ttu-id="99f13-103">Out-File</span><span class="sxs-lookup"><span data-stu-id="99f13-103">Out-File</span></span>

## <span data-ttu-id="99f13-104">概要</span><span class="sxs-lookup"><span data-stu-id="99f13-104">SYNOPSIS</span></span>
<span data-ttu-id="99f13-105">將輸出傳送到檔案。</span><span class="sxs-lookup"><span data-stu-id="99f13-105">Sends output to a file.</span></span>

## <span data-ttu-id="99f13-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="99f13-106">SYNTAX</span></span>

### <span data-ttu-id="99f13-107">ByPath (預設值)</span><span class="sxs-lookup"><span data-stu-id="99f13-107">ByPath (Default)</span></span>

```
Out-File [-FilePath] <string> [[-Encoding] <Encoding>] [-Append] [-Force] [-NoClobber]
 [-Width <int>] [-NoNewline] [-InputObject <psobject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="99f13-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="99f13-108">ByLiteralPath</span></span>

```
Out-File [[-Encoding] <Encoding>] -LiteralPath <string> [-Append] [-Force] [-NoClobber]
 [-Width <int>] [-NoNewline] [-InputObject <psobject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="99f13-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="99f13-109">DESCRIPTION</span></span>

<span data-ttu-id="99f13-110">`Out-File`Cmdlet 會將輸出傳送至檔案。</span><span class="sxs-lookup"><span data-stu-id="99f13-110">The `Out-File` cmdlet sends output to a file.</span></span> <span data-ttu-id="99f13-111">它會隱含地使用 PowerShell 的格式化系統寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="99f13-111">It implicitly uses PowerShell's formatting system to write to the file.</span></span> <span data-ttu-id="99f13-112">檔案會接收與終端機相同的顯示表示。</span><span class="sxs-lookup"><span data-stu-id="99f13-112">The file receives the same display representation as the terminal.</span></span> <span data-ttu-id="99f13-113">這表示，除非所有輸入物件都是字串，否則輸出可能不適合以程式設計方式處理。</span><span class="sxs-lookup"><span data-stu-id="99f13-113">This means that the output may not be ideal for programmatic processing unless all input objects are strings.</span></span>
<span data-ttu-id="99f13-114">當您需要指定輸出參數時，請使用 `Out-File` 而不是重新導向運算子 (`>`) 。</span><span class="sxs-lookup"><span data-stu-id="99f13-114">When you need to specify parameters for the output, use `Out-File` rather than the redirection operator (`>`).</span></span> <span data-ttu-id="99f13-115">如需重新導向的詳細資訊，請參閱 [about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)。</span><span class="sxs-lookup"><span data-stu-id="99f13-115">For more information about redirection, see [about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md).</span></span>

## <span data-ttu-id="99f13-116">範例</span><span class="sxs-lookup"><span data-stu-id="99f13-116">EXAMPLES</span></span>

### <span data-ttu-id="99f13-117">範例1：傳送輸出並建立檔案</span><span class="sxs-lookup"><span data-stu-id="99f13-117">Example 1: Send output and create a file</span></span>

<span data-ttu-id="99f13-118">此範例示範如何將本機電腦的進程清單傳送至檔案。</span><span class="sxs-lookup"><span data-stu-id="99f13-118">This example shows how to send a list of the local computer's processes to a file.</span></span> <span data-ttu-id="99f13-119">如果檔案不存在，則會 `Out-File` 在指定的路徑中建立檔案。</span><span class="sxs-lookup"><span data-stu-id="99f13-119">If the file does not exist, `Out-File` creates the file in the specified path.</span></span>

```powershell
Get-Process | Out-File -FilePath .\Process.txt
Get-Content -Path .\Process.txt
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     29    22.39      35.40      10.98   42764   9 Application
     53    99.04     113.96       0.00   32664   0 CcmExec
     27    96.62     112.43     113.00   17720   9 Code
```

<span data-ttu-id="99f13-120">此 `Get-Process` Cmdlet 會取得在本機電腦上執行的進程清單。</span><span class="sxs-lookup"><span data-stu-id="99f13-120">The `Get-Process` cmdlet gets the list of processes running on the local computer.</span></span> <span data-ttu-id="99f13-121">**處理** 程式物件會向下傳送至 `Out-File` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="99f13-121">The **Process** objects are sent down the pipeline to the `Out-File` cmdlet.</span></span> <span data-ttu-id="99f13-122">`Out-File` 使用 **FilePath** 參數，並在目前目錄中建立名為 **Process.txt** 的檔案。</span><span class="sxs-lookup"><span data-stu-id="99f13-122">`Out-File` uses the **FilePath** parameter and creates a file in the current directory named **Process.txt** .</span></span> <span data-ttu-id="99f13-123">此 `Get-Content` 命令會從檔案取得內容，並將其顯示在 PowerShell 主控台中。</span><span class="sxs-lookup"><span data-stu-id="99f13-123">The `Get-Content` command gets content from the file and displays it in the PowerShell console.</span></span>

### <span data-ttu-id="99f13-124">範例2：防止覆寫現有的檔案</span><span class="sxs-lookup"><span data-stu-id="99f13-124">Example 2: Prevent an existing file from being overwritten</span></span>

<span data-ttu-id="99f13-125">此範例會防止覆寫現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="99f13-125">This example prevents an existing file from being overwritten.</span></span> <span data-ttu-id="99f13-126">根據預設，會 `Out-File` 覆寫現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="99f13-126">By default, `Out-File` overwrites existing files.</span></span>

```powershell
Get-Process | Out-File -FilePath .\Process.txt -NoClobber
```

```Output
Out-File : The file 'C:\Test\Process.txt' already exists.
At line:1 char:15
+ Get-Process | Out-File -FilePath .\Process.txt -NoClobber
+               ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
```

<span data-ttu-id="99f13-127">此 `Get-Process` Cmdlet 會取得在本機電腦上執行的進程清單。</span><span class="sxs-lookup"><span data-stu-id="99f13-127">The `Get-Process` cmdlet gets the list of processes running on the local computer.</span></span> <span data-ttu-id="99f13-128">**處理** 程式物件會向下傳送至 `Out-File` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="99f13-128">The **Process** objects are sent down the pipeline to the `Out-File` cmdlet.</span></span> <span data-ttu-id="99f13-129">`Out-File` 使用 **FilePath** 參數，並嘗試寫入至目前目錄中名為 **Process.txt** 的檔案。</span><span class="sxs-lookup"><span data-stu-id="99f13-129">`Out-File` uses the **FilePath** parameter and attempts to write to a file in the current directory named **Process.txt** .</span></span> <span data-ttu-id="99f13-130">**NoClobber** 參數會防止檔案遭到覆寫，並顯示該檔案已經存在的訊息。</span><span class="sxs-lookup"><span data-stu-id="99f13-130">The **NoClobber** parameter prevents the file from being overwritten and displays a message that the file already exists.</span></span>

### <span data-ttu-id="99f13-131">範例3：以 ASCII 格式將輸出傳送至檔案</span><span class="sxs-lookup"><span data-stu-id="99f13-131">Example 3: Send output to a file in ASCII format</span></span>

<span data-ttu-id="99f13-132">此範例示範如何使用特定編碼類型來編碼輸出。</span><span class="sxs-lookup"><span data-stu-id="99f13-132">This example shows how to encode output with a specific encoding type.</span></span>

```powershell
$Procs = Get-Process
Out-File -FilePath .\Process.txt -InputObject $Procs -Encoding ASCII -Width 50
```

<span data-ttu-id="99f13-133">此 `Get-Process` Cmdlet 會取得在本機電腦上執行的進程清單。</span><span class="sxs-lookup"><span data-stu-id="99f13-133">The `Get-Process` cmdlet gets the list of processes running on the local computer.</span></span> <span data-ttu-id="99f13-134">**處理** 程式物件會儲存在變數中 `$Procs` 。</span><span class="sxs-lookup"><span data-stu-id="99f13-134">The **Process** objects are stored in the variable, `$Procs`.</span></span> <span data-ttu-id="99f13-135">`Out-File` 使用 **FilePath** 參數，並在目前目錄中建立名為 **Process.txt** 的檔案。</span><span class="sxs-lookup"><span data-stu-id="99f13-135">`Out-File` uses the **FilePath** parameter and creates a file in the current directory named **Process.txt** .</span></span> <span data-ttu-id="99f13-136">**InputObject** 參數會將中的處理常式物件傳遞 `$Procs` 至檔案 **Process.txt** 。</span><span class="sxs-lookup"><span data-stu-id="99f13-136">The **InputObject** parameter passes the process objects in `$Procs` to the file **Process.txt** .</span></span> <span data-ttu-id="99f13-137">**Encoding** 參數會將輸出轉換為 **ASCII** 格式。</span><span class="sxs-lookup"><span data-stu-id="99f13-137">The **Encoding** parameter converts the output to **ASCII** format.</span></span> <span data-ttu-id="99f13-138">**寬度** 參數會將檔案中的每一行限制為50個字元，因此某些資料可能會被截斷。</span><span class="sxs-lookup"><span data-stu-id="99f13-138">The **Width** parameter limits each line in the file to 50 characters so some data might be truncated.</span></span>

### <span data-ttu-id="99f13-139">範例4：使用提供者並將輸出傳送至檔案</span><span class="sxs-lookup"><span data-stu-id="99f13-139">Example 4: Use a provider and send output to a file</span></span>

<span data-ttu-id="99f13-140">此範例顯示 `Out-File` 當您不在 **FileSystem** 提供者磁片磁碟機時，如何使用此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="99f13-140">This example shows how to use the `Out-File` cmdlet when you are not in a **FileSystem** provider drive.</span></span> <span data-ttu-id="99f13-141">使用 `Get-PSProvider` Cmdlet 來查看您本機電腦上的提供者。</span><span class="sxs-lookup"><span data-stu-id="99f13-141">Use the `Get-PSProvider` cmdlet to view the providers on your local computer.</span></span> <span data-ttu-id="99f13-142">如需詳細資訊，請參閱 [about_Providers](../Microsoft.Powershell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="99f13-142">For more information, see [about_Providers](../Microsoft.Powershell.Core/About/about_Providers.md).</span></span>

```
PS> Set-Location -Path Alias:

PS> Get-Location

Path
----
Alias:\

PS> Get-ChildItem | Out-File -FilePath C:\TestDir\AliasNames.txt

PS> Get-Content -Path C:\TestDir\AliasNames.txt

CommandType     Name
-----------     ----
Alias           % -> ForEach-Object
Alias           ? -> Where-Object
Alias           ac -> Add-Content
Alias           cat -> Get-Content
```

<span data-ttu-id="99f13-143">`Set-Location`命令使用 **Path** 參數將目前位置設定為登錄提供者 `Alias:` 。</span><span class="sxs-lookup"><span data-stu-id="99f13-143">The `Set-Location` command uses the **Path** parameter to set the current location to the registry provider `Alias:`.</span></span> <span data-ttu-id="99f13-144">`Get-Location`Cmdlet 會顯示的完整路徑 `Alias:` 。</span><span class="sxs-lookup"><span data-stu-id="99f13-144">The `Get-Location` cmdlet displays the complete path for `Alias:`.</span></span>
<span data-ttu-id="99f13-145">`Get-ChildItem` 將物件沿著管線向下傳送至 `Out-File` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="99f13-145">`Get-ChildItem` sends objects down the pipeline to the `Out-File` cmdlet.</span></span> <span data-ttu-id="99f13-146">`Out-File` 使用 **FilePath** 參數來指定輸出的完整路徑和檔案名， **C:\TestDir\AliasNames.txt** 。</span><span class="sxs-lookup"><span data-stu-id="99f13-146">`Out-File` uses the **FilePath** parameter to specify the complete path and filename for the output, **C:\TestDir\AliasNames.txt** .</span></span> <span data-ttu-id="99f13-147">此 `Get-Content` Cmdlet 會使用 **Path** 參數，並在 PowerShell 主控台中顯示檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="99f13-147">The `Get-Content` cmdlet uses the **Path** parameter and displays the file's content in the PowerShell console.</span></span>

## <span data-ttu-id="99f13-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="99f13-148">PARAMETERS</span></span>

### <span data-ttu-id="99f13-149">-Append</span><span class="sxs-lookup"><span data-stu-id="99f13-149">-Append</span></span>

<span data-ttu-id="99f13-150">將輸出新增到現有檔案的結尾。</span><span class="sxs-lookup"><span data-stu-id="99f13-150">Adds the output to the end of an existing file.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="99f13-151">-Encoding</span><span class="sxs-lookup"><span data-stu-id="99f13-151">-Encoding</span></span>

<span data-ttu-id="99f13-152">指定目標檔案的編碼類型。</span><span class="sxs-lookup"><span data-stu-id="99f13-152">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="99f13-153">預設值是 `utf8NoBOM`。</span><span class="sxs-lookup"><span data-stu-id="99f13-153">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="99f13-154">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="99f13-154">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="99f13-155">`ascii`：使用 ASCII (7 位) 字元集的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="99f13-155">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="99f13-156">`bigendianunicode`：使用位元組由大到小的位元組順序，以 UTF-16 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="99f13-156">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="99f13-157">`oem`：針對 MS-DOS 和主控台程式使用預設編碼。</span><span class="sxs-lookup"><span data-stu-id="99f13-157">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="99f13-158">`unicode`：使用位元組由大到小的位元組順序，以 UTF-16 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="99f13-158">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="99f13-159">`utf7`：以 UTF-7 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="99f13-159">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="99f13-160">`utf8`：以 UTF-8 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="99f13-160">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="99f13-161">`utf8BOM`：使用 (BOM) 的位元組順序標記來編碼 UTF-8 格式</span><span class="sxs-lookup"><span data-stu-id="99f13-161">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="99f13-162">`utf8NoBOM`：以不含位元組順序標記的 UTF-8 格式來編碼 (BOM) </span><span class="sxs-lookup"><span data-stu-id="99f13-162">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="99f13-163">`utf32`：以 UTF-32 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="99f13-163">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="99f13-164">從 PowerShell 6.2 開始， **編碼** 參數也會允許已註冊字碼頁的數值識別碼 (例如 `-Encoding 1251`) 或已註冊字碼頁的字串名稱 (例如 `-Encoding "windows-1251"`) 。</span><span class="sxs-lookup"><span data-stu-id="99f13-164">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="99f13-165">如需詳細資訊，請參閱 .NET 檔中的 [編碼字碼頁](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)。</span><span class="sxs-lookup"><span data-stu-id="99f13-165">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: 1
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="99f13-166">-FilePath</span><span class="sxs-lookup"><span data-stu-id="99f13-166">-FilePath</span></span>

<span data-ttu-id="99f13-167">指定輸出檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="99f13-167">Specifies the path to the output file.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases: Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="99f13-168">-Force</span><span class="sxs-lookup"><span data-stu-id="99f13-168">-Force</span></span>

<span data-ttu-id="99f13-169">覆寫唯讀屬性，並覆寫現有的唯讀檔案。</span><span class="sxs-lookup"><span data-stu-id="99f13-169">Overrides the read-only attribute and overwrites an existing read-only file.</span></span> <span data-ttu-id="99f13-170">**Force** 參數不會覆寫安全性限制。</span><span class="sxs-lookup"><span data-stu-id="99f13-170">The **Force** parameter does not override security restrictions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="99f13-171">-InputObject</span><span class="sxs-lookup"><span data-stu-id="99f13-171">-InputObject</span></span>

<span data-ttu-id="99f13-172">指定要寫入檔案的物件。</span><span class="sxs-lookup"><span data-stu-id="99f13-172">Specifies the objects to be written to the file.</span></span> <span data-ttu-id="99f13-173">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="99f13-173">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="99f13-174">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="99f13-174">-LiteralPath</span></span>

<span data-ttu-id="99f13-175">指定輸出檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="99f13-175">Specifies the path to the output file.</span></span> <span data-ttu-id="99f13-176">**LiteralPath** 參數的使用方式與輸入的完全相同。</span><span class="sxs-lookup"><span data-stu-id="99f13-176">The **LiteralPath** parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="99f13-177">不接受萬用字元。</span><span class="sxs-lookup"><span data-stu-id="99f13-177">Wildcard characters are not accepted.</span></span> <span data-ttu-id="99f13-178">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="99f13-178">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="99f13-179">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="99f13-179">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span> <span data-ttu-id="99f13-180">如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="99f13-180">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="99f13-181">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="99f13-181">-NoClobber</span></span>

<span data-ttu-id="99f13-182">**NoClobber** 可防止覆寫現有的檔案，並顯示該檔案已經存在的訊息。</span><span class="sxs-lookup"><span data-stu-id="99f13-182">**NoClobber** prevents an existing file from being overwritten and displays a message that the file already exists.</span></span> <span data-ttu-id="99f13-183">根據預設，如果檔案存在指定的路徑中， `Out-File` 會覆寫檔案而不發出警告。</span><span class="sxs-lookup"><span data-stu-id="99f13-183">By default, if a file exists in the specified path, `Out-File` overwrites the file without warning.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="99f13-184">-NoNewline</span><span class="sxs-lookup"><span data-stu-id="99f13-184">-NoNewline</span></span>

<span data-ttu-id="99f13-185">指定寫入檔案的內容不會以分行符號結尾。</span><span class="sxs-lookup"><span data-stu-id="99f13-185">Specifies that the content written to the file does not end with a newline character.</span></span> <span data-ttu-id="99f13-186">輸入物件的字串表示會串連以形成輸出。</span><span class="sxs-lookup"><span data-stu-id="99f13-186">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="99f13-187">輸出字串之間不會插入空格或分行符號。</span><span class="sxs-lookup"><span data-stu-id="99f13-187">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="99f13-188">最後一個輸出字串之後不會加入任何新行。</span><span class="sxs-lookup"><span data-stu-id="99f13-188">No newline is added after the last output string.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="99f13-189">-Width</span><span class="sxs-lookup"><span data-stu-id="99f13-189">-Width</span></span>

<span data-ttu-id="99f13-190">指定每一行輸出的字元數目。</span><span class="sxs-lookup"><span data-stu-id="99f13-190">Specifies the number of characters in each line of output.</span></span> <span data-ttu-id="99f13-191">任何額外的字元都會被截斷，而不會換行顯示。</span><span class="sxs-lookup"><span data-stu-id="99f13-191">Any additional characters are truncated, not wrapped.</span></span> <span data-ttu-id="99f13-192">如果未使用此參數，則寬度取決於主控制項的特性。</span><span class="sxs-lookup"><span data-stu-id="99f13-192">If this parameter is not used, the width is determined by the characteristics of the host.</span></span> <span data-ttu-id="99f13-193">PowerShell 主控台的預設值為80個字元。</span><span class="sxs-lookup"><span data-stu-id="99f13-193">The default for the PowerShell console is 80 characters.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="99f13-194">-Confirm</span><span class="sxs-lookup"><span data-stu-id="99f13-194">-Confirm</span></span>

<span data-ttu-id="99f13-195">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="99f13-195">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="99f13-196">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="99f13-196">-WhatIf</span></span>

<span data-ttu-id="99f13-197">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="99f13-197">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="99f13-198">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="99f13-198">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="99f13-199">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="99f13-199">CommonParameters</span></span>

<span data-ttu-id="99f13-200">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="99f13-200">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="99f13-201">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="99f13-201">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="99f13-202">輸入</span><span class="sxs-lookup"><span data-stu-id="99f13-202">INPUTS</span></span>

### <span data-ttu-id="99f13-203">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="99f13-203">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="99f13-204">您可以透過管線將任何物件傳送至 `Out-File` 。</span><span class="sxs-lookup"><span data-stu-id="99f13-204">You can pipe any object to `Out-File`.</span></span>

## <span data-ttu-id="99f13-205">輸出</span><span class="sxs-lookup"><span data-stu-id="99f13-205">OUTPUTS</span></span>

### <span data-ttu-id="99f13-206">無</span><span class="sxs-lookup"><span data-stu-id="99f13-206">None</span></span>

<span data-ttu-id="99f13-207">`Out-File` 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="99f13-207">`Out-File` does not generate any output.</span></span>

## <span data-ttu-id="99f13-208">注意</span><span class="sxs-lookup"><span data-stu-id="99f13-208">NOTES</span></span>

<span data-ttu-id="99f13-209">輸入物件會自動格式化，因為它們會在終端機中，但是您可以使用 `Format-*` Cmdlet 來明確控制檔案輸出的格式。</span><span class="sxs-lookup"><span data-stu-id="99f13-209">Input objects are automatically formatted as they would be in the terminal, but you can use a `Format-*` cmdlet to explicitly control the formatting of the output to the file.</span></span> <span data-ttu-id="99f13-210">例如， `Get-Date | Format-List | Out-File out.txt`</span><span class="sxs-lookup"><span data-stu-id="99f13-210">For example, `Get-Date | Format-List | Out-File out.txt`</span></span>

<span data-ttu-id="99f13-211">若要將 PowerShell 命令的輸出傳送至 `Out-File` Cmdlet，請使用管線。</span><span class="sxs-lookup"><span data-stu-id="99f13-211">To send a PowerShell command's output to the `Out-File` cmdlet, use the pipeline.</span></span> <span data-ttu-id="99f13-212">或者，您可以將資料儲存在變數中，然後使用 **InputObject** 參數將資料傳遞給 `Out-File` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="99f13-212">Alternatively, you can store data in a variable and use the **InputObject** parameter to pass data to the `Out-File` cmdlet.</span></span>

<span data-ttu-id="99f13-213">`Out-File` 將資料儲存至檔案，但不會對管線產生任何輸出物件。</span><span class="sxs-lookup"><span data-stu-id="99f13-213">`Out-File` saves data to a file but it does not produce any output objects to the pipeline.</span></span>

## <span data-ttu-id="99f13-214">相關連結</span><span class="sxs-lookup"><span data-stu-id="99f13-214">RELATED LINKS</span></span>

[<span data-ttu-id="99f13-215">about_Providers</span><span class="sxs-lookup"><span data-stu-id="99f13-215">about_Providers</span></span>](../Microsoft.Powershell.Core/About/about_Providers.md)

[<span data-ttu-id="99f13-216">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="99f13-216">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="99f13-217">Out-Default</span><span class="sxs-lookup"><span data-stu-id="99f13-217">Out-Default</span></span>](../Microsoft.PowerShell.Core/Out-Default.md)

[<span data-ttu-id="99f13-218">Out-Host</span><span class="sxs-lookup"><span data-stu-id="99f13-218">Out-Host</span></span>](../Microsoft.PowerShell.Core/Out-Host.md)

[<span data-ttu-id="99f13-219">Out-Null</span><span class="sxs-lookup"><span data-stu-id="99f13-219">Out-Null</span></span>](../Microsoft.PowerShell.Core/Out-Null.md)

[<span data-ttu-id="99f13-220">Out-String</span><span class="sxs-lookup"><span data-stu-id="99f13-220">Out-String</span></span>](Out-String.md)

[<span data-ttu-id="99f13-221">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="99f13-221">Tee-Object</span></span>](Tee-Object.md)
