---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-file?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-File
ms.openlocfilehash: 71602cb0621c835257f556a0a9db15bd754a3aee
ms.sourcegitcommit: d757d64ea8c8af4d92596e8fbe15f2f40d48d3ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "93206327"
---
# <span data-ttu-id="851f5-103">Out-File</span><span class="sxs-lookup"><span data-stu-id="851f5-103">Out-File</span></span>

## <span data-ttu-id="851f5-104">概要</span><span class="sxs-lookup"><span data-stu-id="851f5-104">SYNOPSIS</span></span>
<span data-ttu-id="851f5-105">將輸出傳送到檔案。</span><span class="sxs-lookup"><span data-stu-id="851f5-105">Sends output to a file.</span></span>

## <span data-ttu-id="851f5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="851f5-106">SYNTAX</span></span>

### <span data-ttu-id="851f5-107">ByPath (預設值)</span><span class="sxs-lookup"><span data-stu-id="851f5-107">ByPath (Default)</span></span>

```
Out-File [-FilePath] <string> [[-Encoding] <string>] [-Append] [-Force] [-NoClobber] [-Width <int>]
 [-NoNewline] [-InputObject <psobject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="851f5-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="851f5-108">ByLiteralPath</span></span>

```
Out-File [[-Encoding] <string>] -LiteralPath <string> [-Append] [-Force] [-NoClobber] [-Width <int>]
 [-NoNewline] [-InputObject <psobject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="851f5-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="851f5-109">DESCRIPTION</span></span>

<span data-ttu-id="851f5-110">`Out-File`Cmdlet 會將輸出傳送至檔案。</span><span class="sxs-lookup"><span data-stu-id="851f5-110">The `Out-File` cmdlet sends output to a file.</span></span> <span data-ttu-id="851f5-111">它會隱含地使用 PowerShell 的格式化系統寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="851f5-111">It implicitly uses PowerShell's formatting system to write to the file.</span></span> <span data-ttu-id="851f5-112">檔案會接收與終端機相同的顯示表示。</span><span class="sxs-lookup"><span data-stu-id="851f5-112">The file receives the same display representation as the terminal.</span></span> <span data-ttu-id="851f5-113">這表示，除非所有輸入物件都是字串，否則輸出可能不適合以程式設計方式處理。</span><span class="sxs-lookup"><span data-stu-id="851f5-113">This means that the output may not be ideal for programmatic processing unless all input objects are strings.</span></span>
<span data-ttu-id="851f5-114">當您需要指定輸出參數時，請使用 `Out-File` 而不是重新導向運算子 (`>`) 。</span><span class="sxs-lookup"><span data-stu-id="851f5-114">When you need to specify parameters for the output, use `Out-File` rather than the redirection operator (`>`).</span></span> <span data-ttu-id="851f5-115">如需重新導向的詳細資訊，請參閱 [about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)。</span><span class="sxs-lookup"><span data-stu-id="851f5-115">For more information about redirection, see [about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md).</span></span>

## <span data-ttu-id="851f5-116">範例</span><span class="sxs-lookup"><span data-stu-id="851f5-116">EXAMPLES</span></span>

### <span data-ttu-id="851f5-117">範例1：傳送輸出並建立檔案</span><span class="sxs-lookup"><span data-stu-id="851f5-117">Example 1: Send output and create a file</span></span>

<span data-ttu-id="851f5-118">此範例示範如何將本機電腦的進程清單傳送至檔案。</span><span class="sxs-lookup"><span data-stu-id="851f5-118">This example shows how to send a list of the local computer's processes to a file.</span></span> <span data-ttu-id="851f5-119">如果檔案不存在，則會 `Out-File` 在指定的路徑中建立檔案。</span><span class="sxs-lookup"><span data-stu-id="851f5-119">If the file does not exist, `Out-File` creates the file in the specified path.</span></span>

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

<span data-ttu-id="851f5-120">此 `Get-Process` Cmdlet 會取得在本機電腦上執行的進程清單。</span><span class="sxs-lookup"><span data-stu-id="851f5-120">The `Get-Process` cmdlet gets the list of processes running on the local computer.</span></span> <span data-ttu-id="851f5-121">**處理** 程式物件會向下傳送至 `Out-File` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="851f5-121">The **Process** objects are sent down the pipeline to the `Out-File` cmdlet.</span></span> <span data-ttu-id="851f5-122">`Out-File` 使用 **FilePath** 參數，並在目前目錄中建立名為 **Process.txt** 的檔案。</span><span class="sxs-lookup"><span data-stu-id="851f5-122">`Out-File` uses the **FilePath** parameter and creates a file in the current directory named **Process.txt** .</span></span> <span data-ttu-id="851f5-123">此 `Get-Content` 命令會從檔案取得內容，並將其顯示在 PowerShell 主控台中。</span><span class="sxs-lookup"><span data-stu-id="851f5-123">The `Get-Content` command gets content from the file and displays it in the PowerShell console.</span></span>

### <span data-ttu-id="851f5-124">範例2：防止覆寫現有的檔案</span><span class="sxs-lookup"><span data-stu-id="851f5-124">Example 2: Prevent an existing file from being overwritten</span></span>

<span data-ttu-id="851f5-125">此範例會防止覆寫現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="851f5-125">This example prevents an existing file from being overwritten.</span></span> <span data-ttu-id="851f5-126">根據預設，會 `Out-File` 覆寫現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="851f5-126">By default, `Out-File` overwrites existing files.</span></span>

```powershell
Get-Process | Out-File -FilePath .\Process.txt -NoClobber
```

```Output
Out-File : The file 'C:\Test\Process.txt' already exists.
At line:1 char:15
+ Get-Process | Out-File -FilePath .\Process.txt -NoClobber
+               ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
```

<span data-ttu-id="851f5-127">此 `Get-Process` Cmdlet 會取得在本機電腦上執行的進程清單。</span><span class="sxs-lookup"><span data-stu-id="851f5-127">The `Get-Process` cmdlet gets the list of processes running on the local computer.</span></span> <span data-ttu-id="851f5-128">**處理** 程式物件會向下傳送至 `Out-File` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="851f5-128">The **Process** objects are sent down the pipeline to the `Out-File` cmdlet.</span></span> <span data-ttu-id="851f5-129">`Out-File` 使用 **FilePath** 參數，並嘗試寫入至目前目錄中名為 **Process.txt** 的檔案。</span><span class="sxs-lookup"><span data-stu-id="851f5-129">`Out-File` uses the **FilePath** parameter and attempts to write to a file in the current directory named **Process.txt** .</span></span> <span data-ttu-id="851f5-130">**NoClobber** 參數會防止檔案遭到覆寫，並顯示該檔案已經存在的訊息。</span><span class="sxs-lookup"><span data-stu-id="851f5-130">The **NoClobber** parameter prevents the file from being overwritten and displays a message that the file already exists.</span></span>

### <span data-ttu-id="851f5-131">範例3：以 ASCII 格式將輸出傳送至檔案</span><span class="sxs-lookup"><span data-stu-id="851f5-131">Example 3: Send output to a file in ASCII format</span></span>

<span data-ttu-id="851f5-132">此範例示範如何使用特定編碼類型來編碼輸出。</span><span class="sxs-lookup"><span data-stu-id="851f5-132">This example shows how to encode output with a specific encoding type.</span></span>

```powershell
$Procs = Get-Process
Out-File -FilePath .\Process.txt -InputObject $Procs -Encoding ASCII -Width 50
```

<span data-ttu-id="851f5-133">此 `Get-Process` Cmdlet 會取得在本機電腦上執行的進程清單。</span><span class="sxs-lookup"><span data-stu-id="851f5-133">The `Get-Process` cmdlet gets the list of processes running on the local computer.</span></span> <span data-ttu-id="851f5-134">**處理** 程式物件會儲存在變數中 `$Procs` 。</span><span class="sxs-lookup"><span data-stu-id="851f5-134">The **Process** objects are stored in the variable, `$Procs`.</span></span> <span data-ttu-id="851f5-135">`Out-File` 使用 **FilePath** 參數，並在目前目錄中建立名為 **Process.txt** 的檔案。</span><span class="sxs-lookup"><span data-stu-id="851f5-135">`Out-File` uses the **FilePath** parameter and creates a file in the current directory named **Process.txt** .</span></span> <span data-ttu-id="851f5-136">**InputObject** 參數會將中的處理常式物件傳遞 `$Procs` 至檔案 **Process.txt** 。</span><span class="sxs-lookup"><span data-stu-id="851f5-136">The **InputObject** parameter passes the process objects in `$Procs` to the file **Process.txt** .</span></span> <span data-ttu-id="851f5-137">**Encoding** 參數會將輸出轉換為 **ASCII** 格式。</span><span class="sxs-lookup"><span data-stu-id="851f5-137">The **Encoding** parameter converts the output to **ASCII** format.</span></span> <span data-ttu-id="851f5-138">**寬度** 參數會將檔案中的每一行限制為50個字元，因此某些資料可能會被截斷。</span><span class="sxs-lookup"><span data-stu-id="851f5-138">The **Width** parameter limits each line in the file to 50 characters so some data might be truncated.</span></span>

### <span data-ttu-id="851f5-139">範例4：使用提供者並將輸出傳送至檔案</span><span class="sxs-lookup"><span data-stu-id="851f5-139">Example 4: Use a provider and send output to a file</span></span>

<span data-ttu-id="851f5-140">此範例顯示 `Out-File` 當您不在 **FileSystem** 提供者磁片磁碟機時，如何使用此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="851f5-140">This example shows how to use the `Out-File` cmdlet when you are not in a **FileSystem** provider drive.</span></span> <span data-ttu-id="851f5-141">使用 `Get-PSProvider` Cmdlet 來查看您本機電腦上的提供者。</span><span class="sxs-lookup"><span data-stu-id="851f5-141">Use the `Get-PSProvider` cmdlet to view the providers on your local computer.</span></span> <span data-ttu-id="851f5-142">如需詳細資訊，請參閱 [about_Providers](../Microsoft.Powershell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="851f5-142">For more information, see [about_Providers](../Microsoft.Powershell.Core/About/about_Providers.md).</span></span>

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

<span data-ttu-id="851f5-143">`Set-Location`命令使用 **Path** 參數將目前位置設定為登錄提供者 `Alias:` 。</span><span class="sxs-lookup"><span data-stu-id="851f5-143">The `Set-Location` command uses the **Path** parameter to set the current location to the registry provider `Alias:`.</span></span> <span data-ttu-id="851f5-144">`Get-Location`Cmdlet 會顯示的完整路徑 `Alias:` 。</span><span class="sxs-lookup"><span data-stu-id="851f5-144">The `Get-Location` cmdlet displays the complete path for `Alias:`.</span></span>
<span data-ttu-id="851f5-145">`Get-ChildItem` 將物件沿著管線向下傳送至 `Out-File` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="851f5-145">`Get-ChildItem` sends objects down the pipeline to the `Out-File` cmdlet.</span></span> <span data-ttu-id="851f5-146">`Out-File` 使用 **FilePath** 參數來指定輸出的完整路徑和檔案名， **C:\TestDir\AliasNames.txt** 。</span><span class="sxs-lookup"><span data-stu-id="851f5-146">`Out-File` uses the **FilePath** parameter to specify the complete path and filename for the output, **C:\TestDir\AliasNames.txt** .</span></span> <span data-ttu-id="851f5-147">此 `Get-Content` Cmdlet 會使用 **Path** 參數，並在 PowerShell 主控台中顯示檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="851f5-147">The `Get-Content` cmdlet uses the **Path** parameter and displays the file's content in the PowerShell console.</span></span>

## <span data-ttu-id="851f5-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="851f5-148">PARAMETERS</span></span>

### <span data-ttu-id="851f5-149">-Append</span><span class="sxs-lookup"><span data-stu-id="851f5-149">-Append</span></span>

<span data-ttu-id="851f5-150">將輸出新增到現有檔案的結尾。</span><span class="sxs-lookup"><span data-stu-id="851f5-150">Adds the output to the end of an existing file.</span></span> <span data-ttu-id="851f5-151">如果未指定 **編碼方式** ，Cmdlet 會使用預設的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="851f5-151">If no **Encoding** is specified, the cmdlet uses the default encoding.</span></span> <span data-ttu-id="851f5-152">該編碼可能不符合目標檔案的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="851f5-152">That encoding may not match the encoding of the target file.</span></span> <span data-ttu-id="851f5-153">這與重新導向操作員 () 的行為相同 `>>` 。</span><span class="sxs-lookup"><span data-stu-id="851f5-153">This is the same behavior as the redirection operator (`>>`).</span></span>

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

### <span data-ttu-id="851f5-154">-Encoding</span><span class="sxs-lookup"><span data-stu-id="851f5-154">-Encoding</span></span>

<span data-ttu-id="851f5-155">指定目標檔案的編碼類型。</span><span class="sxs-lookup"><span data-stu-id="851f5-155">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="851f5-156">預設值是 `unicode`。</span><span class="sxs-lookup"><span data-stu-id="851f5-156">The default value is `unicode`.</span></span>

<span data-ttu-id="851f5-157">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="851f5-157">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="851f5-158">`ascii` 使用 ASCII (7 位) 字元集。</span><span class="sxs-lookup"><span data-stu-id="851f5-158">`ascii` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="851f5-159">`bigendianunicode` 以位元組由大到小的順序使用 UTF-16。</span><span class="sxs-lookup"><span data-stu-id="851f5-159">`bigendianunicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="851f5-160">`default` 使用與系統的作用中字碼頁對應的編碼， (通常是 ANSI) 。</span><span class="sxs-lookup"><span data-stu-id="851f5-160">`default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="851f5-161">`oem` 使用對應至系統目前 OEM 字碼頁的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="851f5-161">`oem` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="851f5-162">`string`：與 `unicode` 相同。</span><span class="sxs-lookup"><span data-stu-id="851f5-162">`string` Same as `unicode`.</span></span>
- <span data-ttu-id="851f5-163">`unicode` 使用 UTF-16 和位元組由小到小的位元組順序。</span><span class="sxs-lookup"><span data-stu-id="851f5-163">`unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="851f5-164">`unknown`：與 `unicode` 相同。</span><span class="sxs-lookup"><span data-stu-id="851f5-164">`unknown` Same as `unicode`.</span></span>
- <span data-ttu-id="851f5-165">`utf7` 使用 UTF-7。</span><span class="sxs-lookup"><span data-stu-id="851f5-165">`utf7` Uses UTF-7.</span></span>
- <span data-ttu-id="851f5-166">`utf8` 使用 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="851f5-166">`utf8` Uses UTF-8.</span></span>
- <span data-ttu-id="851f5-167">`utf32` 以位元組由小到大的位元組順序使用 UTF-32。</span><span class="sxs-lookup"><span data-stu-id="851f5-167">`utf32` Uses UTF-32 with the little-endian byte order.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, Default, OEM, String, Unicode, Unknown, UTF7, UTF8, UTF32

Required: False
Position: 1
Default value: Unicode
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="851f5-168">-FilePath</span><span class="sxs-lookup"><span data-stu-id="851f5-168">-FilePath</span></span>

<span data-ttu-id="851f5-169">指定輸出檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="851f5-169">Specifies the path to the output file.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="851f5-170">-Force</span><span class="sxs-lookup"><span data-stu-id="851f5-170">-Force</span></span>

<span data-ttu-id="851f5-171">覆寫唯讀屬性，並覆寫現有的唯讀檔案。</span><span class="sxs-lookup"><span data-stu-id="851f5-171">Overrides the read-only attribute and overwrites an existing read-only file.</span></span> <span data-ttu-id="851f5-172">**Force** 參數不會覆寫安全性限制。</span><span class="sxs-lookup"><span data-stu-id="851f5-172">The **Force** parameter does not override security restrictions.</span></span>

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

### <span data-ttu-id="851f5-173">-InputObject</span><span class="sxs-lookup"><span data-stu-id="851f5-173">-InputObject</span></span>

<span data-ttu-id="851f5-174">指定要寫入檔案的物件。</span><span class="sxs-lookup"><span data-stu-id="851f5-174">Specifies the objects to be written to the file.</span></span> <span data-ttu-id="851f5-175">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="851f5-175">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="851f5-176">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="851f5-176">-LiteralPath</span></span>

<span data-ttu-id="851f5-177">指定輸出檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="851f5-177">Specifies the path to the output file.</span></span> <span data-ttu-id="851f5-178">**LiteralPath** 參數的使用方式與輸入的完全相同。</span><span class="sxs-lookup"><span data-stu-id="851f5-178">The **LiteralPath** parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="851f5-179">不接受萬用字元。</span><span class="sxs-lookup"><span data-stu-id="851f5-179">Wildcard characters are not accepted.</span></span> <span data-ttu-id="851f5-180">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="851f5-180">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="851f5-181">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="851f5-181">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span> <span data-ttu-id="851f5-182">如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="851f5-182">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="851f5-183">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="851f5-183">-NoClobber</span></span>

<span data-ttu-id="851f5-184">**NoClobber** 可防止覆寫現有的檔案，並顯示該檔案已經存在的訊息。</span><span class="sxs-lookup"><span data-stu-id="851f5-184">**NoClobber** prevents an existing file from being overwritten and displays a message that the file already exists.</span></span> <span data-ttu-id="851f5-185">根據預設，如果檔案存在指定的路徑中， `Out-File` 會覆寫檔案而不發出警告。</span><span class="sxs-lookup"><span data-stu-id="851f5-185">By default, if a file exists in the specified path, `Out-File` overwrites the file without warning.</span></span>

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

### <span data-ttu-id="851f5-186">-NoNewline</span><span class="sxs-lookup"><span data-stu-id="851f5-186">-NoNewline</span></span>

<span data-ttu-id="851f5-187">指定寫入檔案的內容不會以分行符號結尾。</span><span class="sxs-lookup"><span data-stu-id="851f5-187">Specifies that the content written to the file does not end with a newline character.</span></span> <span data-ttu-id="851f5-188">輸入物件的字串表示會串連以形成輸出。</span><span class="sxs-lookup"><span data-stu-id="851f5-188">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="851f5-189">輸出字串之間不會插入空格或分行符號。</span><span class="sxs-lookup"><span data-stu-id="851f5-189">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="851f5-190">最後一個輸出字串之後不會加入任何新行。</span><span class="sxs-lookup"><span data-stu-id="851f5-190">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="851f5-191">-Width</span><span class="sxs-lookup"><span data-stu-id="851f5-191">-Width</span></span>

<span data-ttu-id="851f5-192">指定每一行輸出的字元數目。</span><span class="sxs-lookup"><span data-stu-id="851f5-192">Specifies the number of characters in each line of output.</span></span> <span data-ttu-id="851f5-193">任何額外的字元都會被截斷，而不會換行顯示。</span><span class="sxs-lookup"><span data-stu-id="851f5-193">Any additional characters are truncated, not wrapped.</span></span> <span data-ttu-id="851f5-194">如果未使用此參數，則寬度取決於主控制項的特性。</span><span class="sxs-lookup"><span data-stu-id="851f5-194">If this parameter is not used, the width is determined by the characteristics of the host.</span></span> <span data-ttu-id="851f5-195">PowerShell 主控台的預設值為80個字元。</span><span class="sxs-lookup"><span data-stu-id="851f5-195">The default for the PowerShell console is 80 characters.</span></span>

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

### <span data-ttu-id="851f5-196">-Confirm</span><span class="sxs-lookup"><span data-stu-id="851f5-196">-Confirm</span></span>

<span data-ttu-id="851f5-197">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="851f5-197">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="851f5-198">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="851f5-198">-WhatIf</span></span>

<span data-ttu-id="851f5-199">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="851f5-199">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="851f5-200">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="851f5-200">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="851f5-201">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="851f5-201">CommonParameters</span></span>

<span data-ttu-id="851f5-202">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="851f5-202">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="851f5-203">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="851f5-203">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="851f5-204">輸入</span><span class="sxs-lookup"><span data-stu-id="851f5-204">INPUTS</span></span>

### <span data-ttu-id="851f5-205">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="851f5-205">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="851f5-206">您可以透過管線將任何物件傳送至 `Out-File` 。</span><span class="sxs-lookup"><span data-stu-id="851f5-206">You can pipe any object to `Out-File`.</span></span>

## <span data-ttu-id="851f5-207">輸出</span><span class="sxs-lookup"><span data-stu-id="851f5-207">OUTPUTS</span></span>

### <span data-ttu-id="851f5-208">無</span><span class="sxs-lookup"><span data-stu-id="851f5-208">None</span></span>

<span data-ttu-id="851f5-209">`Out-File` 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="851f5-209">`Out-File` does not generate any output.</span></span>

## <span data-ttu-id="851f5-210">注意</span><span class="sxs-lookup"><span data-stu-id="851f5-210">NOTES</span></span>

<span data-ttu-id="851f5-211">輸入物件會自動格式化，因為它們會在終端機中，但是您可以使用 `Format-*` Cmdlet 來明確控制檔案輸出的格式。</span><span class="sxs-lookup"><span data-stu-id="851f5-211">Input objects are automatically formatted as they would be in the terminal, but you can use a `Format-*` cmdlet to explicitly control the formatting of the output to the file.</span></span> <span data-ttu-id="851f5-212">例如， `Get-Date | Format-List | Out-File out.txt`</span><span class="sxs-lookup"><span data-stu-id="851f5-212">For example, `Get-Date | Format-List | Out-File out.txt`</span></span>

<span data-ttu-id="851f5-213">若要將 PowerShell 命令的輸出傳送至 `Out-File` Cmdlet，請使用管線。</span><span class="sxs-lookup"><span data-stu-id="851f5-213">To send a PowerShell command's output to the `Out-File` cmdlet, use the pipeline.</span></span> <span data-ttu-id="851f5-214">或者，您可以將資料儲存在變數中，然後使用 **InputObject** 參數將資料傳遞給 `Out-File` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="851f5-214">Alternatively, you can store data in a variable and use the **InputObject** parameter to pass data to the `Out-File` cmdlet.</span></span>

<span data-ttu-id="851f5-215">`Out-File` 將資料儲存至檔案，但不會對管線產生任何輸出物件。</span><span class="sxs-lookup"><span data-stu-id="851f5-215">`Out-File` saves data to a file but it does not produce any output objects to the pipeline.</span></span>

## <span data-ttu-id="851f5-216">相關連結</span><span class="sxs-lookup"><span data-stu-id="851f5-216">RELATED LINKS</span></span>

[<span data-ttu-id="851f5-217">about_Providers</span><span class="sxs-lookup"><span data-stu-id="851f5-217">about_Providers</span></span>](../Microsoft.Powershell.Core/About/about_Providers.md)

[<span data-ttu-id="851f5-218">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="851f5-218">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="851f5-219">Out-Default</span><span class="sxs-lookup"><span data-stu-id="851f5-219">Out-Default</span></span>](../Microsoft.PowerShell.Core/Out-Default.md)

[<span data-ttu-id="851f5-220">Out-GridView</span><span class="sxs-lookup"><span data-stu-id="851f5-220">Out-GridView</span></span>](Out-GridView.md)

[<span data-ttu-id="851f5-221">Out-Host</span><span class="sxs-lookup"><span data-stu-id="851f5-221">Out-Host</span></span>](../Microsoft.PowerShell.Core/Out-Host.md)

[<span data-ttu-id="851f5-222">Out-Null</span><span class="sxs-lookup"><span data-stu-id="851f5-222">Out-Null</span></span>](../Microsoft.PowerShell.Core/Out-Null.md)

[<span data-ttu-id="851f5-223">Out-Printer</span><span class="sxs-lookup"><span data-stu-id="851f5-223">Out-Printer</span></span>](Out-Printer.md)

[<span data-ttu-id="851f5-224">Out-String</span><span class="sxs-lookup"><span data-stu-id="851f5-224">Out-String</span></span>](Out-String.md)

[<span data-ttu-id="851f5-225">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="851f5-225">Tee-Object</span></span>](Tee-Object.md)
