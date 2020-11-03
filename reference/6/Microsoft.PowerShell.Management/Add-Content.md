---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/add-content?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Content
ms.openlocfilehash: 291ec8f3a3958aa726fafb8032b996296272a21e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202571"
---
# <span data-ttu-id="015e7-103">Add-Content</span><span class="sxs-lookup"><span data-stu-id="015e7-103">Add-Content</span></span>

## <span data-ttu-id="015e7-104">概要</span><span class="sxs-lookup"><span data-stu-id="015e7-104">SYNOPSIS</span></span>
<span data-ttu-id="015e7-105">新增內容至指定的項目，例如將文字新增到檔案。</span><span class="sxs-lookup"><span data-stu-id="015e7-105">Adds content to the specified items, such as adding words to a file.</span></span>

## <span data-ttu-id="015e7-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="015e7-106">SYNTAX</span></span>

### <span data-ttu-id="015e7-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="015e7-107">Path (Default)</span></span>

```
Add-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

### <span data-ttu-id="015e7-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="015e7-108">LiteralPath</span></span>

```
Add-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

## <span data-ttu-id="015e7-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="015e7-109">DESCRIPTION</span></span>

<span data-ttu-id="015e7-110">Cmdlet 會將 `Add-Content` 內容附加至指定的專案或檔案。</span><span class="sxs-lookup"><span data-stu-id="015e7-110">The `Add-Content` cmdlet appends content to a specified item or file.</span></span> <span data-ttu-id="015e7-111">您可以在命令中輸入內容或透過指定包含內容的物件指定內容。</span><span class="sxs-lookup"><span data-stu-id="015e7-111">You can specify the content by typing the content in the command or by specifying an object that contains the content.</span></span>

<span data-ttu-id="015e7-112">如果您需要建立下列範例的檔案或目錄，請參閱 [新專案](New-Item.md)。</span><span class="sxs-lookup"><span data-stu-id="015e7-112">If you need to create files or directories for the following examples, see [New-Item](New-Item.md).</span></span>

## <span data-ttu-id="015e7-113">範例</span><span class="sxs-lookup"><span data-stu-id="015e7-113">EXAMPLES</span></span>

### <span data-ttu-id="015e7-114">範例1：將字串新增至所有文字檔，但有例外狀況</span><span class="sxs-lookup"><span data-stu-id="015e7-114">Example 1: Add a string to all text files with an exception</span></span>

<span data-ttu-id="015e7-115">此範例會將值附加至目前的目錄中的文字檔，但會根據檔案的檔案名來排除這些檔案。</span><span class="sxs-lookup"><span data-stu-id="015e7-115">This example appends a value to text files in the current directory but excludes files based on their file name.</span></span>

```powershell
Add-Content -Path .\*.txt -Exclude help* -Value 'End of file'
```

<span data-ttu-id="015e7-116">**Path** 參數 `.txt` 會指定目前目錄中的所有檔案，但 **Exclude** 參數會忽略符合指定模式的檔案名。</span><span class="sxs-lookup"><span data-stu-id="015e7-116">The **Path** parameter specifies all `.txt` files in the current directory, but the **Exclude** parameter ignores file names that match the specified pattern.</span></span> <span data-ttu-id="015e7-117">**Value** 參數會指定寫入檔案的文字字串。</span><span class="sxs-lookup"><span data-stu-id="015e7-117">The **Value** parameter specifies the text string that is written to the files.</span></span>

### <span data-ttu-id="015e7-118">範例2：在指定檔案的結尾加上日期</span><span class="sxs-lookup"><span data-stu-id="015e7-118">Example 2: Add a date to the end of the specified files</span></span>

<span data-ttu-id="015e7-119">此範例會將日期附加至目前目錄中的檔案，並在 PowerShell 主控台中顯示日期。</span><span class="sxs-lookup"><span data-stu-id="015e7-119">This example appends the date to files in the current directory and displays the date in the PowerShell console.</span></span>

```powershell
Add-Content -Path .\DateTimeFile1.log, .\DateTimeFile2.log -Value (Get-Date) -PassThru
Get-Content -Path .\DateTimeFile1.log
```

```Output
Tuesday, May 14, 2019 8:24:27 AM
Tuesday, May 14, 2019 8:24:27 AM
5/14/2019 8:24:27 AM
```

<span data-ttu-id="015e7-120">`Add-Content`Cmdlet 會在目前的目錄中建立兩個新檔案。</span><span class="sxs-lookup"><span data-stu-id="015e7-120">The `Add-Content` cmdlet creates two new files in the current directory.</span></span> <span data-ttu-id="015e7-121">**Value** 參數包含 Cmdlet 的輸出 `Get-Date` 。</span><span class="sxs-lookup"><span data-stu-id="015e7-121">The **Value** parameter contains the output of the `Get-Date` cmdlet.</span></span> <span data-ttu-id="015e7-122">**PassThru** 參數會將新增的內容輸出到管線。</span><span class="sxs-lookup"><span data-stu-id="015e7-122">The **PassThru** parameter outputs the added contents to the pipeline.</span></span>
<span data-ttu-id="015e7-123">因為沒有任何其他 Cmdlet 可接收輸出，所以它會顯示在 PowerShell 主控台中。</span><span class="sxs-lookup"><span data-stu-id="015e7-123">Because there is no other cmdlet to receive the output, it is displayed in the PowerShell console.</span></span>
<span data-ttu-id="015e7-124">此 `Get-Content` Cmdlet 會顯示已更新的檔案 `DateTimeFile1.log` 。</span><span class="sxs-lookup"><span data-stu-id="015e7-124">The `Get-Content` cmdlet displays the updated file, `DateTimeFile1.log`.</span></span>

### <span data-ttu-id="015e7-125">範例3：將指定檔案的內容加入至另一個檔案</span><span class="sxs-lookup"><span data-stu-id="015e7-125">Example 3: Add the contents of a specified file to another file</span></span>

<span data-ttu-id="015e7-126">此範例會從檔案取得內容，並將內容儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="015e7-126">This example gets the content from a file and stores the content in a variable.</span></span> <span data-ttu-id="015e7-127">變數是用來將內容附加至另一個檔案。</span><span class="sxs-lookup"><span data-stu-id="015e7-127">The variable is used to append the content into another file.</span></span>

```powershell
$From = Get-Content -Path .\CopyFromFile.txt
Add-Content -Path .\CopyToFile.txt -Value $From
Get-Content -Path .\CopyToFile.txt
```

- <span data-ttu-id="015e7-128">`Get-Content`Cmdlet 會取得的內容 `CopyFromFile.txt` ，並將內容儲存在 `$From` 變數中。</span><span class="sxs-lookup"><span data-stu-id="015e7-128">The `Get-Content` cmdlet gets the contents of `CopyFromFile.txt` and stores the contents in the `$From` variable.</span></span>
- <span data-ttu-id="015e7-129">此 `Add-Content` Cmdlet 會 `CopyToFile.txt` 使用變數的內容來更新檔案 `$From` 。</span><span class="sxs-lookup"><span data-stu-id="015e7-129">The `Add-Content` cmdlet updates the `CopyToFile.txt` file using the contents of the `$From` variable.</span></span>
- <span data-ttu-id="015e7-130">`Get-Content`Cmdlet 會顯示 CopyToFile.txt。</span><span class="sxs-lookup"><span data-stu-id="015e7-130">The `Get-Content` cmdlet displays CopyToFile.txt.</span></span>

### <span data-ttu-id="015e7-131">範例4：使用管線將指定檔案的內容新增至另一個檔案</span><span class="sxs-lookup"><span data-stu-id="015e7-131">Example 4: Add the contents of a specified file to another file using the pipeline</span></span>

<span data-ttu-id="015e7-132">此範例會從檔案取得內容，並使用管線將它傳送至 `Add-Content` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="015e7-132">This example gets the content from a file and pipes it to the `Add-Content` cmdlet.</span></span>

```powershell
Get-Content -Path .\CopyFromFile.txt | Add-Content -Path .\CopyToFile.txt
Get-Content -Path .\CopyToFile.txt
```

<span data-ttu-id="015e7-133">`Get-Content`Cmdlet 會取得的內容 `CopyFromFile.txt` 。</span><span class="sxs-lookup"><span data-stu-id="015e7-133">The `Get-Content` cmdlet gets the contents of `CopyFromFile.txt`.</span></span> <span data-ttu-id="015e7-134">結果會透過管道傳送至 `Add-Content` Cmdlet，以更新 `CopyToFile.txt` 。</span><span class="sxs-lookup"><span data-stu-id="015e7-134">The results are piped to the `Add-Content` cmdlet, which updates the `CopyToFile.txt`.</span></span>
<span data-ttu-id="015e7-135">最後一個 `Get-Content` Cmdlet 隨即顯示 `CopyToFile.txt` 。</span><span class="sxs-lookup"><span data-stu-id="015e7-135">The last `Get-Content` cmdlet displays `CopyToFile.txt`.</span></span>

### <span data-ttu-id="015e7-136">範例5：建立新的檔案並複製內容</span><span class="sxs-lookup"><span data-stu-id="015e7-136">Example 5: Create a new file and copy content</span></span>

<span data-ttu-id="015e7-137">這個範例會建立新的檔案，並將現有檔案的內容複寫到新檔案中。</span><span class="sxs-lookup"><span data-stu-id="015e7-137">This example creates a new file and copies an existing file's content into the new file.</span></span>

```powershell
Add-Content -Path .\NewFile.txt -Value (Get-Content -Path .\CopyFromFile.txt)
Get-Content -Path .\NewFile.txt
```

- <span data-ttu-id="015e7-138">此 `Add-Content` Cmdlet 會使用 **Path** 和 **Value** 參數在目前的目錄中建立新檔案。</span><span class="sxs-lookup"><span data-stu-id="015e7-138">The `Add-Content` cmdlet uses the **Path** and **Value** parameters to create a new file in the current directory.</span></span>
- <span data-ttu-id="015e7-139">`Get-Content`Cmdlet 會取得現有檔案的內容，並將 `CopyFromFile.txt` 其傳遞至 **Value** 參數。</span><span class="sxs-lookup"><span data-stu-id="015e7-139">The `Get-Content` cmdlet gets the contents of an existing file, `CopyFromFile.txt` and passes it to the **Value** parameter.</span></span> <span data-ttu-id="015e7-140">Cmdlet 周圍的括弧 `Get-Content` 可確保命令會在 `Add-Content` 命令開始之前完成。</span><span class="sxs-lookup"><span data-stu-id="015e7-140">The parentheses around the `Get-Content` cmdlet ensure that the command finishes before the `Add-Content` command begins.</span></span>
- <span data-ttu-id="015e7-141">此 `Get-Content` Cmdlet 會顯示新檔案的內容 `NewFile.txt` 。</span><span class="sxs-lookup"><span data-stu-id="015e7-141">The `Get-Content` cmdlet displays the contents of the new file, `NewFile.txt`.</span></span>

### <span data-ttu-id="015e7-142">範例6：將內容新增至唯讀檔案</span><span class="sxs-lookup"><span data-stu-id="015e7-142">Example 6: Add content to a read-only file</span></span>

<span data-ttu-id="015e7-143">此命令會將值新增至檔案，即使 **IsReadOnly** 檔案屬性設定為 True 也是 **如此** 。</span><span class="sxs-lookup"><span data-stu-id="015e7-143">This command adds a value to the file even if the **IsReadOnly** file attribute is set to **True** .</span></span>
<span data-ttu-id="015e7-144">範例中包含建立唯讀檔案的步驟。</span><span class="sxs-lookup"><span data-stu-id="015e7-144">The steps to create a read-only file are included in the example.</span></span>

```powershell
New-Item -Path .\IsReadOnlyTextFile.txt -ItemType File
Set-ItemProperty -Path .\IsReadOnlyTextFile.txt -Name IsReadOnly -Value $True
Get-ChildItem -Path .\IsReadOnlyTextFile.txt
Add-Content -Path .\IsReadOnlyTextFile.txt -Value 'Add value to read-only text file' -Force
Get-Content -Path .\IsReadOnlyTextFile.txt
```

```Output
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-ar--         1/28/2019     13:35              0 IsReadOnlyTextFile.txt
```

- <span data-ttu-id="015e7-145">此 `New-Item` Cmdlet 會使用 **Path** 和 **ItemType** 參數， `IsReadOnlyTextFile.txt` 在目前的目錄中建立檔案。</span><span class="sxs-lookup"><span data-stu-id="015e7-145">The `New-Item` cmdlet uses the **Path** and **ItemType** parameters to create the file `IsReadOnlyTextFile.txt` in the current directory.</span></span>
- <span data-ttu-id="015e7-146">此 `Set-ItemProperty` Cmdlet 會使用 **Name** 和 **Value** 參數將檔案的 **IsReadOnly** 屬性變更為 True。</span><span class="sxs-lookup"><span data-stu-id="015e7-146">The `Set-ItemProperty` cmdlet uses the **Name** and **Value** parameters to change the file's **IsReadOnly** property to True.</span></span>
- <span data-ttu-id="015e7-147">此 `Get-ChildItem` Cmdlet 會顯示 (0) 的檔案是空的，且 () 的唯讀屬性 `r` 。</span><span class="sxs-lookup"><span data-stu-id="015e7-147">The `Get-ChildItem` cmdlet shows the file is empty (0) and has the read-only attribute (`r`).</span></span>
- <span data-ttu-id="015e7-148">此 `Add-Content` Cmdlet 會使用 **Path** 參數來指定檔案。</span><span class="sxs-lookup"><span data-stu-id="015e7-148">The `Add-Content` cmdlet uses the **Path** parameter to specify the file.</span></span> <span data-ttu-id="015e7-149">**Value** 參數包含要附加至檔案的文字字串。</span><span class="sxs-lookup"><span data-stu-id="015e7-149">The **Value** parameter includes the text string to append to the file.</span></span> <span data-ttu-id="015e7-150">**Force** 參數會將文字寫入至唯讀檔案。</span><span class="sxs-lookup"><span data-stu-id="015e7-150">The **Force** parameter writes the text to the read-only file.</span></span>
- <span data-ttu-id="015e7-151">此 `Get-Content` Cmdlet 會使用 **Path** 參數來顯示檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="015e7-151">The `Get-Content` cmdlet uses the **Path** parameter to display the file's contents.</span></span>

<span data-ttu-id="015e7-152">若要移除唯讀屬性，請使用命令， `Set-ItemProperty` 並將 **Value** 參數設定為 `False` 。</span><span class="sxs-lookup"><span data-stu-id="015e7-152">To remove the read-only attribute, use the `Set-ItemProperty` command with the **Value** parameter set to `False`.</span></span>

### <span data-ttu-id="015e7-153">範例7：搭配 Add-Content 使用篩選</span><span class="sxs-lookup"><span data-stu-id="015e7-153">Example 7: Use Filters with Add-Content</span></span>

<span data-ttu-id="015e7-154">您可以為 Cmdlet 指定篩選 `Add-Content` 。</span><span class="sxs-lookup"><span data-stu-id="015e7-154">You can specify a filter to the `Add-Content` cmdlet.</span></span> <span data-ttu-id="015e7-155">使用篩選準則來限定 **路徑** 參數時，您必須包含尾端星號 (`*`) 來指出路徑的內容。</span><span class="sxs-lookup"><span data-stu-id="015e7-155">When using filters to qualify the **Path** parameter, you need to include a trailing asterisk (`*`) to indicate the contents of the path.</span></span>

<span data-ttu-id="015e7-156">下列命令會將目錄中所有檔案的內容「完成」一字 `*.txt` `C:\Temp` 。</span><span class="sxs-lookup"><span data-stu-id="015e7-156">The following command adds the word "Done" the content of all `*.txt` files in the `C:\Temp` directory.</span></span>

```powershell
Add-Content -Path C:\Temp\* -Filter *.txt -Value "Done"
```

## <span data-ttu-id="015e7-157">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="015e7-157">PARAMETERS</span></span>

### <span data-ttu-id="015e7-158">-AsByteStream</span><span class="sxs-lookup"><span data-stu-id="015e7-158">-AsByteStream</span></span>

<span data-ttu-id="015e7-159">指定應將內容讀取為位元組資料流程。</span><span class="sxs-lookup"><span data-stu-id="015e7-159">Specifies that the content should be read as a stream of bytes.</span></span> <span data-ttu-id="015e7-160">此參數是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="015e7-160">This parameter was introduced in PowerShell 6.0.</span></span>

<span data-ttu-id="015e7-161">當您使用 **AsByteStream** 參數搭配 **編碼** 參數時，就會發生警告。</span><span class="sxs-lookup"><span data-stu-id="015e7-161">A warning occurs when you use the **AsByteStream** parameter with the **Encoding** parameter.</span></span> <span data-ttu-id="015e7-162">**AsByteStream** 參數會忽略任何編碼，並以位元組資料流程的形式傳回輸出。</span><span class="sxs-lookup"><span data-stu-id="015e7-162">The **AsByteStream** parameter ignores any encoding and the output is returned as a stream of bytes.</span></span>

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

### <span data-ttu-id="015e7-163">-Credential</span><span class="sxs-lookup"><span data-stu-id="015e7-163">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="015e7-164">使用 PowerShell 安裝的任何提供者都不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="015e7-164">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="015e7-165">若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="015e7-165">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="015e7-166">-Encoding</span><span class="sxs-lookup"><span data-stu-id="015e7-166">-Encoding</span></span>

<span data-ttu-id="015e7-167">指定目標檔案的編碼類型。</span><span class="sxs-lookup"><span data-stu-id="015e7-167">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="015e7-168">預設值是 `utf8NoBOM`。</span><span class="sxs-lookup"><span data-stu-id="015e7-168">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="015e7-169">Encoding 是動態參數，FileSystem 提供者會將它新增至 `Add-Content` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="015e7-169">Encoding is a dynamic parameter that the FileSystem provider adds to the `Add-Content` cmdlet.</span></span> <span data-ttu-id="015e7-170">此參數只適用於檔案系統磁碟機。</span><span class="sxs-lookup"><span data-stu-id="015e7-170">This parameter works only in file system drives.</span></span>

<span data-ttu-id="015e7-171">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="015e7-171">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="015e7-172">`ascii`：使用 ASCII (7 位) 字元集的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="015e7-172">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="015e7-173">`bigendianunicode`：使用位元組由大到小的位元組順序，以 UTF-16 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="015e7-173">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="015e7-174">`oem`：針對 MS-DOS 和主控台程式使用預設編碼。</span><span class="sxs-lookup"><span data-stu-id="015e7-174">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="015e7-175">`unicode`：使用位元組由大到小的位元組順序，以 UTF-16 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="015e7-175">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="015e7-176">`utf7`：以 UTF-7 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="015e7-176">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="015e7-177">`utf8`：以 UTF-8 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="015e7-177">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="015e7-178">`utf8BOM`：使用 (BOM) 的位元組順序標記來編碼 UTF-8 格式</span><span class="sxs-lookup"><span data-stu-id="015e7-178">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="015e7-179">`utf8NoBOM`：以不含位元組順序標記的 UTF-8 格式來編碼 (BOM) </span><span class="sxs-lookup"><span data-stu-id="015e7-179">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="015e7-180">`utf32`：以 UTF-32 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="015e7-180">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="015e7-181">從 PowerShell 6.2 開始， **編碼** 參數也會允許已註冊字碼頁的數值識別碼 (例如 `-Encoding 1251`) 或已註冊字碼頁的字串名稱 (例如 `-Encoding "windows-1251"`) 。</span><span class="sxs-lookup"><span data-stu-id="015e7-181">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="015e7-182">如需詳細資訊，請參閱 .NET 檔中的 [編碼字碼頁](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)。</span><span class="sxs-lookup"><span data-stu-id="015e7-182">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

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

### <span data-ttu-id="015e7-183">-Exclude</span><span class="sxs-lookup"><span data-stu-id="015e7-183">-Exclude</span></span>

<span data-ttu-id="015e7-184">以字串陣列指定此 Cmdlet 在作業中排除的專案。</span><span class="sxs-lookup"><span data-stu-id="015e7-184">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="015e7-185">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="015e7-185">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="015e7-186">輸入路徑元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="015e7-186">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="015e7-187">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="015e7-187">Wildcard characters are permitted.</span></span> <span data-ttu-id="015e7-188">只有當命令包含專案的內容（例如）時，才會使用 **Exclude** 參數， `C:\Windows\*` 其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="015e7-188">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="015e7-189">-Filter</span><span class="sxs-lookup"><span data-stu-id="015e7-189">-Filter</span></span>

<span data-ttu-id="015e7-190">指定要限定 **路徑** 參數的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="015e7-190">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="015e7-191">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供者是唯一支援使用篩選器的已安裝 PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="015e7-191">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="015e7-192">您可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **檔案系統** 篩選器語言的語法。</span><span class="sxs-lookup"><span data-stu-id="015e7-192">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="015e7-193">篩選比其他參數更有效率，因為提供者會在 Cmdlet 取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。</span><span class="sxs-lookup"><span data-stu-id="015e7-193">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="015e7-194">-Force</span><span class="sxs-lookup"><span data-stu-id="015e7-194">-Force</span></span>

<span data-ttu-id="015e7-195">覆寫唯讀屬性，可讓您新增內容至唯讀檔案。</span><span class="sxs-lookup"><span data-stu-id="015e7-195">Overrides the read-only attribute, allowing you to add content to a read-only file.</span></span> <span data-ttu-id="015e7-196">例如， **Force** 會覆寫唯讀屬性或建立目錄來完成檔案路徑，但不會嘗試變更檔案權限。</span><span class="sxs-lookup"><span data-stu-id="015e7-196">For example, **Force** will override the read-only attribute or create directories to complete a file path, but it will not attempt to change file permissions.</span></span>

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

### <span data-ttu-id="015e7-197">-Include</span><span class="sxs-lookup"><span data-stu-id="015e7-197">-Include</span></span>

<span data-ttu-id="015e7-198">以字串陣列指定此 Cmdlet 在作業中納入的項目。</span><span class="sxs-lookup"><span data-stu-id="015e7-198">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="015e7-199">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="015e7-199">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="015e7-200">輸入路徑元素或模式，例如 `"*.txt"`。</span><span class="sxs-lookup"><span data-stu-id="015e7-200">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="015e7-201">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="015e7-201">Wildcard characters are permitted.</span></span> <span data-ttu-id="015e7-202">**Include** 參數只有當命令包含專案內容時才有效，例如 `C:\Windows\*` ，其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="015e7-202">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="015e7-203">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="015e7-203">-LiteralPath</span></span>

<span data-ttu-id="015e7-204">指定一個或多個位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="015e7-204">Specifies a path to one or more locations.</span></span> <span data-ttu-id="015e7-205">**LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="015e7-205">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="015e7-206">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="015e7-206">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="015e7-207">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="015e7-207">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="015e7-208">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="015e7-208">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="015e7-209">如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="015e7-209">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="015e7-210">-NoNewline</span><span class="sxs-lookup"><span data-stu-id="015e7-210">-NoNewline</span></span>

<span data-ttu-id="015e7-211">指出此 Cmdlet 不會將新的一行或換行內容新增至內容。</span><span class="sxs-lookup"><span data-stu-id="015e7-211">Indicates that this cmdlet does not add a new line or carriage return to the content.</span></span>

<span data-ttu-id="015e7-212">輸入物件的字串表示會串連以形成輸出。</span><span class="sxs-lookup"><span data-stu-id="015e7-212">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="015e7-213">輸出字串之間不會插入空格或分行符號。</span><span class="sxs-lookup"><span data-stu-id="015e7-213">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="015e7-214">最後一個輸出字串之後不會加入任何新行。</span><span class="sxs-lookup"><span data-stu-id="015e7-214">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="015e7-215">-PassThru</span><span class="sxs-lookup"><span data-stu-id="015e7-215">-PassThru</span></span>

<span data-ttu-id="015e7-216">傳回代表新增內容的物件。</span><span class="sxs-lookup"><span data-stu-id="015e7-216">Returns an object representing the added content.</span></span> <span data-ttu-id="015e7-217">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="015e7-217">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="015e7-218">-Path</span><span class="sxs-lookup"><span data-stu-id="015e7-218">-Path</span></span>

<span data-ttu-id="015e7-219">指定要接收其他內容的項目路徑。</span><span class="sxs-lookup"><span data-stu-id="015e7-219">Specifies the path to the items that receive the additional content.</span></span>
<span data-ttu-id="015e7-220">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="015e7-220">Wildcard characters are permitted.</span></span>
<span data-ttu-id="015e7-221">路徑需為項目的路徑，而非容器的路徑。</span><span class="sxs-lookup"><span data-stu-id="015e7-221">The paths must be paths to items, not to containers.</span></span>
<span data-ttu-id="015e7-222">例如，您必須指定一或多個檔案的路徑，而非目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="015e7-222">For example, you must specify a path to one or more files, not a path to a directory.</span></span>
<span data-ttu-id="015e7-223">如果您指定多個路徑，請使用逗號來分隔路徑。</span><span class="sxs-lookup"><span data-stu-id="015e7-223">If you specify multiple paths, use commas to separate the paths.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="015e7-224">-Stream</span><span class="sxs-lookup"><span data-stu-id="015e7-224">-Stream</span></span>

<span data-ttu-id="015e7-225">指定內容的替代資料流程。</span><span class="sxs-lookup"><span data-stu-id="015e7-225">Specifies an alternative data stream for content.</span></span> <span data-ttu-id="015e7-226">如果資料流程不存在，此 Cmdlet 會建立該資料流程。</span><span class="sxs-lookup"><span data-stu-id="015e7-226">If the stream does not exist, this cmdlet creates it.</span></span> <span data-ttu-id="015e7-227">不支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="015e7-227">Wildcard characters are not supported.</span></span>

<span data-ttu-id="015e7-228">**Stream** 是動態參數，FileSystem 提供者會將其加入至 `Add-Content` 。</span><span class="sxs-lookup"><span data-stu-id="015e7-228">**Stream** is a dynamic parameter that the FileSystem provider adds to `Add-Content`.</span></span> <span data-ttu-id="015e7-229">此參數只適用於檔案系統磁碟機。</span><span class="sxs-lookup"><span data-stu-id="015e7-229">This parameter works only in file system drives.</span></span>

<span data-ttu-id="015e7-230">您可以使用 `Add-Content` Cmdlet 來變更區域的內容 **。識別碼** 替代資料流程。</span><span class="sxs-lookup"><span data-stu-id="015e7-230">You can use the `Add-Content` cmdlet to change the content of the **Zone.Identifier** alternate data stream.</span></span> <span data-ttu-id="015e7-231">不過，我們不建議您這樣做，以排除封鎖從網際網路下載之檔案的安全性檢查。</span><span class="sxs-lookup"><span data-stu-id="015e7-231">However, we do not recommend this as a way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="015e7-232">如果您確認下載的檔案是安全的，請使用 `Unblock-File` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="015e7-232">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="015e7-233">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="015e7-233">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="015e7-234">-Value</span><span class="sxs-lookup"><span data-stu-id="015e7-234">-Value</span></span>

<span data-ttu-id="015e7-235">指定要新增的內容。</span><span class="sxs-lookup"><span data-stu-id="015e7-235">Specifies the content to be added.</span></span> <span data-ttu-id="015e7-236">輸入加上引號的字串，例如 **此資料僅供內部使用** ，或指定包含內容的物件，例如產生的 **DateTime** 物件 `Get-Date` 。</span><span class="sxs-lookup"><span data-stu-id="015e7-236">Type a quoted string, such as **This data is for internal use only** , or specify an object that contains content, such as the **DateTime** object that `Get-Date` generates.</span></span>

<span data-ttu-id="015e7-237">您無法藉由輸入檔案的路徑來指定檔案的內容，因為路徑只是一個字串。</span><span class="sxs-lookup"><span data-stu-id="015e7-237">You cannot specify the contents of a file by typing its path, because the path is just a string.</span></span>
<span data-ttu-id="015e7-238">您可以使用 `Get-Content` 命令取得內容，並將其傳遞至 **Value** 參數。</span><span class="sxs-lookup"><span data-stu-id="015e7-238">You can use a `Get-Content` command to get the content and pass it to the **Value** parameter.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="015e7-239">-Confirm</span><span class="sxs-lookup"><span data-stu-id="015e7-239">-Confirm</span></span>

<span data-ttu-id="015e7-240">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="015e7-240">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="015e7-241">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="015e7-241">-WhatIf</span></span>

<span data-ttu-id="015e7-242">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="015e7-242">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="015e7-243">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="015e7-243">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="015e7-244">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="015e7-244">CommonParameters</span></span>

<span data-ttu-id="015e7-245">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="015e7-245">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="015e7-246">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="015e7-246">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="015e7-247">輸入</span><span class="sxs-lookup"><span data-stu-id="015e7-247">INPUTS</span></span>

### <span data-ttu-id="015e7-248">System.string、System.object、system.string</span><span class="sxs-lookup"><span data-stu-id="015e7-248">System.Object, System.Management.Automation.PSCredential</span></span>

<span data-ttu-id="015e7-249">您可以透過管道將值、路徑或認證傳送至 `Set-Content` 。</span><span class="sxs-lookup"><span data-stu-id="015e7-249">You can pipe values, paths, or credentials to `Set-Content`.</span></span>

## <span data-ttu-id="015e7-250">輸出</span><span class="sxs-lookup"><span data-stu-id="015e7-250">OUTPUTS</span></span>

### <span data-ttu-id="015e7-251">無或 System.String</span><span class="sxs-lookup"><span data-stu-id="015e7-251">None or System.String</span></span>

<span data-ttu-id="015e7-252">當您使用 **PassThru** 參數時，會 `Add-Content` 產生代表內容的 **system.string** 物件。</span><span class="sxs-lookup"><span data-stu-id="015e7-252">When you use the **PassThru** parameter, `Add-Content` generates a **System.String** object that represents the content.</span></span> <span data-ttu-id="015e7-253">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="015e7-253">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="015e7-254">注意</span><span class="sxs-lookup"><span data-stu-id="015e7-254">NOTES</span></span>

- <span data-ttu-id="015e7-255">當您使用管線將物件傳送至時 `Add-Content` ，會先將物件轉換成字串，然後再將它加入至專案。</span><span class="sxs-lookup"><span data-stu-id="015e7-255">When you pipe an object to `Add-Content`, the object is converted to a string before it is added to the item.</span></span> <span data-ttu-id="015e7-256">物件類型決定字串格式，但是格式可能會不同於物件的預設顯示。</span><span class="sxs-lookup"><span data-stu-id="015e7-256">The object type determines the string format, but the format might be different than the default display of the object.</span></span> <span data-ttu-id="015e7-257">若要控制字串格式，請使用傳送 Cmdlet 的格式化參數。</span><span class="sxs-lookup"><span data-stu-id="015e7-257">To control the string format, use the formatting parameters of the sending cmdlet.</span></span>
- <span data-ttu-id="015e7-258">您也可以 `Add-Content` 使用內建的別名來參考 `ac` 。</span><span class="sxs-lookup"><span data-stu-id="015e7-258">You can also refer to `Add-Content` by its built-in alias, `ac`.</span></span> <span data-ttu-id="015e7-259">如需詳細資訊，請參閱 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="015e7-259">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="015e7-260">此 `Add-Content` Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。</span><span class="sxs-lookup"><span data-stu-id="015e7-260">The `Add-Content` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="015e7-261">若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="015e7-261">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="015e7-262">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="015e7-262">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="015e7-263">相關連結</span><span class="sxs-lookup"><span data-stu-id="015e7-263">RELATED LINKS</span></span>

[<span data-ttu-id="015e7-264">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="015e7-264">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="015e7-265">about_Providers</span><span class="sxs-lookup"><span data-stu-id="015e7-265">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="015e7-266">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="015e7-266">Clear-Content</span></span>](Clear-Content.md)

[<span data-ttu-id="015e7-267">Get-Content</span><span class="sxs-lookup"><span data-stu-id="015e7-267">Get-Content</span></span>](Get-Content.md)

[<span data-ttu-id="015e7-268">Get-Item</span><span class="sxs-lookup"><span data-stu-id="015e7-268">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="015e7-269">New-Item</span><span class="sxs-lookup"><span data-stu-id="015e7-269">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="015e7-270">Set-Content</span><span class="sxs-lookup"><span data-stu-id="015e7-270">Set-Content</span></span>](Set-Content.md)
