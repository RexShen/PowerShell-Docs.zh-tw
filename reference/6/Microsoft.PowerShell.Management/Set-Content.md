---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-content?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Content
ms.openlocfilehash: 33ed166b4e467d5c1054c936414a6628370f69d8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202432"
---
# <span data-ttu-id="51d85-103">Set-Content</span><span class="sxs-lookup"><span data-stu-id="51d85-103">Set-Content</span></span>

## <span data-ttu-id="51d85-104">概要</span><span class="sxs-lookup"><span data-stu-id="51d85-104">SYNOPSIS</span></span>
<span data-ttu-id="51d85-105">寫入新的內容，或取代檔案中的現有內容。</span><span class="sxs-lookup"><span data-stu-id="51d85-105">Writes new content or replaces existing content in a file.</span></span>

## <span data-ttu-id="51d85-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="51d85-106">SYNTAX</span></span>

### <span data-ttu-id="51d85-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="51d85-107">Path (Default)</span></span>

```
Set-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>]
 [-WhatIf] [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

### <span data-ttu-id="51d85-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="51d85-108">LiteralPath</span></span>

```
Set-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>]
 [-WhatIf] [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

## <span data-ttu-id="51d85-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="51d85-109">DESCRIPTION</span></span>

<span data-ttu-id="51d85-110">`Set-Content` 是字串處理 Cmdlet，會寫入新內容或取代檔案中的內容。</span><span class="sxs-lookup"><span data-stu-id="51d85-110">`Set-Content` is a string-processing cmdlet that writes new content or replaces the content in a file.</span></span> <span data-ttu-id="51d85-111">`Set-Content` 取代現有的內容，與將 `Add-Content` 內容附加至檔案的 Cmdlet 不同。</span><span class="sxs-lookup"><span data-stu-id="51d85-111">`Set-Content` replaces the existing content and differs from the `Add-Content` cmdlet that appends content to a file.</span></span> <span data-ttu-id="51d85-112">若要將內容傳送給 `Set-Content` 您，您可以在命令列上使用 **Value** 參數，或透過管線傳送內容。</span><span class="sxs-lookup"><span data-stu-id="51d85-112">To send content to `Set-Content` you can use the **Value** parameter on the command line or send content through the pipeline.</span></span>

<span data-ttu-id="51d85-113">如果您需要建立下列範例的檔案或目錄，請參閱 [新專案](New-Item.md)。</span><span class="sxs-lookup"><span data-stu-id="51d85-113">If you need to create files or directories for the following examples, see [New-Item](New-Item.md).</span></span>

## <span data-ttu-id="51d85-114">範例</span><span class="sxs-lookup"><span data-stu-id="51d85-114">EXAMPLES</span></span>

### <span data-ttu-id="51d85-115">範例1：取代目錄中多個檔案的內容</span><span class="sxs-lookup"><span data-stu-id="51d85-115">Example 1: Replace the contents of multiple files in a directory</span></span>

<span data-ttu-id="51d85-116">此範例會取代目前目錄中多個檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="51d85-116">This example replaces the content for multiple files in the current directory.</span></span>

```powershell
Get-ChildItem -Path .\Test*.txt
```

```Output
Test1.txt
Test2.txt
Test3.txt
```

```powershell
Set-Content -Path .\Test*.txt -Value 'Hello, World'
Get-Content -Path .\Test*.txt
```

```Output
Hello, World
Hello, World
Hello, World
```

<span data-ttu-id="51d85-117">此 `Get-ChildItem` Cmdlet 會使用 **Path** 參數來列出以目前的目錄開頭的 **.txt** 檔案。 `Test*`</span><span class="sxs-lookup"><span data-stu-id="51d85-117">The `Get-ChildItem` cmdlet uses the **Path** parameter to list **.txt** files that begin with `Test*` in the current directory.</span></span> <span data-ttu-id="51d85-118">此 `Set-Content` Cmdlet 會使用 **Path** 參數來指定檔案 `Test*.txt` 。</span><span class="sxs-lookup"><span data-stu-id="51d85-118">The `Set-Content` cmdlet uses the **Path** parameter to specify the `Test*.txt` files.</span></span> <span data-ttu-id="51d85-119">**Value** 參數提供文字字串 **Hello，World** 取代每個檔案中的現有內容。</span><span class="sxs-lookup"><span data-stu-id="51d85-119">The **Value** parameter provides the text string **Hello, World** that replaces the existing content in each file.</span></span> <span data-ttu-id="51d85-120">此 `Get-Content` Cmdlet 會使用 **Path** 參數來指定檔案 `Test*.txt` ，並在 PowerShell 主控台中顯示每個檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="51d85-120">The `Get-Content` cmdlet uses the **Path** parameter to specify the `Test*.txt` files and displays each file's content in the PowerShell console.</span></span>

### <span data-ttu-id="51d85-121">範例2：建立新檔案並寫入內容</span><span class="sxs-lookup"><span data-stu-id="51d85-121">Example 2: Create a new file and write content</span></span>

<span data-ttu-id="51d85-122">這個範例會建立新的檔案，並將目前的日期和時間寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="51d85-122">This example creates a new file and writes the current date and time to the file.</span></span>

```powershell
Set-Content -Path .\DateTime.txt -Value (Get-Date)
Get-Content -Path .\DateTime.txt
```

```Output
1/30/2019 09:55:08
```

<span data-ttu-id="51d85-123">`Set-Content` 使用 **Path** 和 **Value** 參數，在目前的目錄中建立名為 **DateTime.txt** 的新檔案。</span><span class="sxs-lookup"><span data-stu-id="51d85-123">`Set-Content` uses the **Path** and **Value** parameters to create a new file named **DateTime.txt** in the current directory.</span></span> <span data-ttu-id="51d85-124">**值** 參數會使用 `Get-Date` 來取得目前的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="51d85-124">The **Value** parameter uses `Get-Date` to get the current date and time.</span></span>
<span data-ttu-id="51d85-125">`Set-Content` 以字串的形式將 **DateTime** 物件寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="51d85-125">`Set-Content` writes the **DateTime** object to the file as a string.</span></span> <span data-ttu-id="51d85-126">此 `Get-Content` Cmdlet 會使用 **Path** 參數，在 PowerShell 主控台中顯示 **DateTime.txt** 的內容。</span><span class="sxs-lookup"><span data-stu-id="51d85-126">The `Get-Content` cmdlet uses the **Path** parameter to display the content of **DateTime.txt** in the PowerShell console.</span></span>

### <span data-ttu-id="51d85-127">範例3：取代檔案中的文字</span><span class="sxs-lookup"><span data-stu-id="51d85-127">Example 3: Replace text in a file</span></span>

<span data-ttu-id="51d85-128">此命令會取代現有檔案中的所有 word 實例。</span><span class="sxs-lookup"><span data-stu-id="51d85-128">This command replaces all instances of word within an existing file.</span></span>

```powershell
Get-Content -Path .\Notice.txt
```

```Output
Warning
Replace Warning with a new word.
The word Warning was replaced.
```

```powershell
(Get-Content -Path .\Notice.txt) |
    ForEach-Object {$_ -Replace 'Warning', 'Caution'} |
        Set-Content -Path .\Notice.txt
Get-Content -Path .\Notice.txt
```

```Output
Caution
Replace Caution with a new word.
The word Caution was replaced.
```

<span data-ttu-id="51d85-129">此 `Get-Content` Cmdlet 會使用 **Path** 參數來指定目前目錄中的 **Notice.txt** 檔案。</span><span class="sxs-lookup"><span data-stu-id="51d85-129">The `Get-Content` cmdlet uses the **Path** parameter to specify the **Notice.txt** file in the current directory.</span></span> <span data-ttu-id="51d85-130">此 `Get-Content` 命令會以括弧括住，讓命令先完成，再向下傳送管線。</span><span class="sxs-lookup"><span data-stu-id="51d85-130">The `Get-Content` command is wrapped with parentheses so that the command finishes before being sent down the pipeline.</span></span>

<span data-ttu-id="51d85-131">**Notice.txt** 檔案的內容會向下傳送至 `ForEach-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="51d85-131">The contents of the **Notice.txt** file are sent down the pipeline to the `ForEach-Object` cmdlet.</span></span>
<span data-ttu-id="51d85-132">`ForEach-Object`使用自動變數 `$_` ，並 **謹慎** 地取代每個出現的 **警告** 。</span><span class="sxs-lookup"><span data-stu-id="51d85-132">`ForEach-Object` uses the automatic variable `$_` and replaces each occurrence of **Warning** with **Caution** .</span></span> <span data-ttu-id="51d85-133">這些物件會向下傳送至 `Set-Content` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="51d85-133">The objects are sent down the pipeline to the `Set-Content` cmdlet.</span></span> <span data-ttu-id="51d85-134">`Set-Content` 使用 **Path** 參數指定 **Notice.txt** 檔，並將更新的內容寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="51d85-134">`Set-Content` uses the **Path** parameter to specify the **Notice.txt** file and writes the updated content to the file.</span></span>

<span data-ttu-id="51d85-135">最後一個 `Get-Content` Cmdlet 會在 PowerShell 主控台中顯示已更新的檔案內容。</span><span class="sxs-lookup"><span data-stu-id="51d85-135">The last `Get-Content` cmdlet displays the updated file content in the PowerShell console.</span></span>

### <span data-ttu-id="51d85-136">範例4：搭配 Set-Content 使用篩選</span><span class="sxs-lookup"><span data-stu-id="51d85-136">Example 4: Use Filters with Set-Content</span></span>

<span data-ttu-id="51d85-137">您可以為 Cmdlet 指定篩選 `Set-Content` 。</span><span class="sxs-lookup"><span data-stu-id="51d85-137">You can specify a filter to the `Set-Content` cmdlet.</span></span> <span data-ttu-id="51d85-138">使用篩選準則來限定 **路徑** 參數時，您必須包含尾端星號 (`*`) 來指出路徑的內容。</span><span class="sxs-lookup"><span data-stu-id="51d85-138">When using filters to qualify the **Path** parameter, you need to include a trailing asterisk (`*`) to indicate the contents of the path.</span></span>

<span data-ttu-id="51d85-139">下列命令會將目錄中所有檔案的內容設定為 `*.txt` `C:\Temp` 空白 **Value** 。</span><span class="sxs-lookup"><span data-stu-id="51d85-139">The following command set the content all `*.txt` files in the `C:\Temp` directory to the **Value** empty.</span></span>

```powershell
Set-Content -Path C:\Temp\* -Filter *.txt -Value "Empty"
```

## <span data-ttu-id="51d85-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="51d85-140">PARAMETERS</span></span>

### <span data-ttu-id="51d85-141">-AsByteStream</span><span class="sxs-lookup"><span data-stu-id="51d85-141">-AsByteStream</span></span>

<span data-ttu-id="51d85-142">指定應將內容讀取為位元組資料流程。</span><span class="sxs-lookup"><span data-stu-id="51d85-142">Specifies that the content should be read as a stream of bytes.</span></span> <span data-ttu-id="51d85-143">此參數是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="51d85-143">This parameter was introduced in PowerShell 6.0.</span></span>

<span data-ttu-id="51d85-144">當您使用 **AsByteStream** 參數搭配 **編碼** 參數時，就會發生警告。</span><span class="sxs-lookup"><span data-stu-id="51d85-144">A warning occurs when you use the **AsByteStream** parameter with the **Encoding** parameter.</span></span> <span data-ttu-id="51d85-145">**AsByteStream** 參數會忽略任何編碼，並以位元組資料流程的形式傳回輸出。</span><span class="sxs-lookup"><span data-stu-id="51d85-145">The **AsByteStream** parameter ignores any encoding and the output is returned as a stream of bytes.</span></span>

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

### <span data-ttu-id="51d85-146">-Credential</span><span class="sxs-lookup"><span data-stu-id="51d85-146">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="51d85-147">使用 PowerShell 安裝的任何提供者都不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="51d85-147">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="51d85-148">若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="51d85-148">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="51d85-149">-Encoding</span><span class="sxs-lookup"><span data-stu-id="51d85-149">-Encoding</span></span>

<span data-ttu-id="51d85-150">指定目標檔案的編碼類型。</span><span class="sxs-lookup"><span data-stu-id="51d85-150">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="51d85-151">預設值是 `utf8NoBOM`。</span><span class="sxs-lookup"><span data-stu-id="51d85-151">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="51d85-152">Encoding 是動態參數，FileSystem 提供者會將其加入至 `Set-Content` 。</span><span class="sxs-lookup"><span data-stu-id="51d85-152">Encoding is a dynamic parameter that the FileSystem provider adds to `Set-Content`.</span></span> <span data-ttu-id="51d85-153">此參數只適用於檔案系統磁碟機。</span><span class="sxs-lookup"><span data-stu-id="51d85-153">This parameter works only in file system drives.</span></span>

<span data-ttu-id="51d85-154">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="51d85-154">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="51d85-155">`ascii`：使用 ASCII (7 位) 字元集的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="51d85-155">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="51d85-156">`bigendianunicode`：使用位元組由大到小的位元組順序，以 UTF-16 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="51d85-156">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="51d85-157">`oem`：針對 MS-DOS 和主控台程式使用預設編碼。</span><span class="sxs-lookup"><span data-stu-id="51d85-157">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="51d85-158">`unicode`：使用位元組由大到小的位元組順序，以 UTF-16 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="51d85-158">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="51d85-159">`utf7`：以 UTF-7 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="51d85-159">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="51d85-160">`utf8`：以 UTF-8 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="51d85-160">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="51d85-161">`utf8BOM`：使用 (BOM) 的位元組順序標記來編碼 UTF-8 格式</span><span class="sxs-lookup"><span data-stu-id="51d85-161">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="51d85-162">`utf8NoBOM`：以不含位元組順序標記的 UTF-8 格式來編碼 (BOM) </span><span class="sxs-lookup"><span data-stu-id="51d85-162">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="51d85-163">`utf32`：以 UTF-32 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="51d85-163">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="51d85-164">從 PowerShell 6.2 開始， **編碼** 參數也會允許已註冊字碼頁的數值識別碼 (例如 `-Encoding 1251`) 或已註冊字碼頁的字串名稱 (例如 `-Encoding "windows-1251"`) 。</span><span class="sxs-lookup"><span data-stu-id="51d85-164">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="51d85-165">如需詳細資訊，請參閱 .NET 檔中的 [編碼字碼頁](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)。</span><span class="sxs-lookup"><span data-stu-id="51d85-165">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

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

### <span data-ttu-id="51d85-166">-Exclude</span><span class="sxs-lookup"><span data-stu-id="51d85-166">-Exclude</span></span>

<span data-ttu-id="51d85-167">以字串陣列指定此 Cmdlet 在作業中排除的專案。</span><span class="sxs-lookup"><span data-stu-id="51d85-167">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="51d85-168">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="51d85-168">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="51d85-169">輸入路徑元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="51d85-169">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="51d85-170">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="51d85-170">Wildcard characters are permitted.</span></span> <span data-ttu-id="51d85-171">只有當命令包含專案的內容（例如）時，才會使用 **Exclude** 參數， `C:\Windows\*` 其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="51d85-171">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="51d85-172">-Filter</span><span class="sxs-lookup"><span data-stu-id="51d85-172">-Filter</span></span>

<span data-ttu-id="51d85-173">指定要限定 **路徑** 參數的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="51d85-173">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="51d85-174">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供者是唯一支援使用篩選器的已安裝 PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="51d85-174">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="51d85-175">您可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **檔案系統** 篩選器語言的語法。</span><span class="sxs-lookup"><span data-stu-id="51d85-175">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="51d85-176">篩選比其他參數更有效率，因為提供者會在 Cmdlet 取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。</span><span class="sxs-lookup"><span data-stu-id="51d85-176">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="51d85-177">-Force</span><span class="sxs-lookup"><span data-stu-id="51d85-177">-Force</span></span>

<span data-ttu-id="51d85-178">強制 Cmdlet 設定檔案的內容，即使檔案是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="51d85-178">Forces the cmdlet to set the contents of a file, even if the file is read-only.</span></span> <span data-ttu-id="51d85-179">實作會依提供者而異。</span><span class="sxs-lookup"><span data-stu-id="51d85-179">Implementation varies from provider to provider.</span></span> <span data-ttu-id="51d85-180">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="51d85-180">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
<span data-ttu-id="51d85-181">**Force** 參數不會覆寫安全性限制。</span><span class="sxs-lookup"><span data-stu-id="51d85-181">The **Force** parameter does not override security restrictions.</span></span>

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

### <span data-ttu-id="51d85-182">-Include</span><span class="sxs-lookup"><span data-stu-id="51d85-182">-Include</span></span>

<span data-ttu-id="51d85-183">以字串陣列指定此 Cmdlet 在作業中納入的項目。</span><span class="sxs-lookup"><span data-stu-id="51d85-183">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="51d85-184">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="51d85-184">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="51d85-185">輸入路徑元素或模式，例如 `"*.txt"`。</span><span class="sxs-lookup"><span data-stu-id="51d85-185">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="51d85-186">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="51d85-186">Wildcard characters are permitted.</span></span> <span data-ttu-id="51d85-187">**Include** 參數只有當命令包含專案內容時才有效，例如 `C:\Windows\*` ，其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="51d85-187">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="51d85-188">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="51d85-188">-LiteralPath</span></span>

<span data-ttu-id="51d85-189">指定一個或多個位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="51d85-189">Specifies a path to one or more locations.</span></span> <span data-ttu-id="51d85-190">**LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="51d85-190">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="51d85-191">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="51d85-191">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="51d85-192">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="51d85-192">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="51d85-193">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="51d85-193">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="51d85-194">如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="51d85-194">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="51d85-195">-NoNewline</span><span class="sxs-lookup"><span data-stu-id="51d85-195">-NoNewline</span></span>

<span data-ttu-id="51d85-196">輸入物件的字串表示會串連以形成輸出。</span><span class="sxs-lookup"><span data-stu-id="51d85-196">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="51d85-197">輸出字串之間不會插入空格或分行符號。</span><span class="sxs-lookup"><span data-stu-id="51d85-197">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="51d85-198">最後一個輸出字串之後不會加入任何新行。</span><span class="sxs-lookup"><span data-stu-id="51d85-198">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="51d85-199">-PassThru</span><span class="sxs-lookup"><span data-stu-id="51d85-199">-PassThru</span></span>

<span data-ttu-id="51d85-200">傳回代表內容的物件。</span><span class="sxs-lookup"><span data-stu-id="51d85-200">Returns an object that represents the content.</span></span> <span data-ttu-id="51d85-201">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="51d85-201">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="51d85-202">-Path</span><span class="sxs-lookup"><span data-stu-id="51d85-202">-Path</span></span>

<span data-ttu-id="51d85-203">指定接收內容之專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="51d85-203">Specifies the path of the item that receives the content.</span></span>
<span data-ttu-id="51d85-204">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="51d85-204">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="51d85-205">-Stream</span><span class="sxs-lookup"><span data-stu-id="51d85-205">-Stream</span></span>

<span data-ttu-id="51d85-206">指定內容的替代資料流程。</span><span class="sxs-lookup"><span data-stu-id="51d85-206">Specifies an alternative data stream for content.</span></span> <span data-ttu-id="51d85-207">如果資料流程不存在，此 Cmdlet 會建立該資料流程。</span><span class="sxs-lookup"><span data-stu-id="51d85-207">If the stream does not exist, this cmdlet creates it.</span></span> <span data-ttu-id="51d85-208">不支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="51d85-208">Wildcard characters are not supported.</span></span>

<span data-ttu-id="51d85-209">**Stream** 是動態參數， **FileSystem** 提供者會將其加入至 `Set-Content` 。</span><span class="sxs-lookup"><span data-stu-id="51d85-209">**Stream** is a dynamic parameter that the **FileSystem** provider adds to `Set-Content`.</span></span> <span data-ttu-id="51d85-210">此參數只適用於檔案系統磁碟機。</span><span class="sxs-lookup"><span data-stu-id="51d85-210">This parameter works only in file system drives.</span></span>

<span data-ttu-id="51d85-211">您可以使用 `Set-Content` Cmdlet 來變更區域的內容 **。識別碼** 替代資料流程。</span><span class="sxs-lookup"><span data-stu-id="51d85-211">You can use the `Set-Content` cmdlet to change the content of the **Zone.Identifier** alternate data stream.</span></span> <span data-ttu-id="51d85-212">不過，我們不建議您這樣做，以排除封鎖從網際網路下載之檔案的安全性檢查。</span><span class="sxs-lookup"><span data-stu-id="51d85-212">However, we do not recommend this as a way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="51d85-213">如果您確認下載的檔案是安全的，請使用 `Unblock-File` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="51d85-213">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="51d85-214">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="51d85-214">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="51d85-215">-Value</span><span class="sxs-lookup"><span data-stu-id="51d85-215">-Value</span></span>

<span data-ttu-id="51d85-216">指定項目的新內容。</span><span class="sxs-lookup"><span data-stu-id="51d85-216">Specifies the new content for the item.</span></span>

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

### <span data-ttu-id="51d85-217">-Confirm</span><span class="sxs-lookup"><span data-stu-id="51d85-217">-Confirm</span></span>

<span data-ttu-id="51d85-218">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="51d85-218">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="51d85-219">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="51d85-219">-WhatIf</span></span>

<span data-ttu-id="51d85-220">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="51d85-220">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="51d85-221">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="51d85-221">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="51d85-222">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="51d85-222">CommonParameters</span></span>

<span data-ttu-id="51d85-223">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="51d85-223">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span>
<span data-ttu-id="51d85-224">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="51d85-224">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="51d85-225">輸入</span><span class="sxs-lookup"><span data-stu-id="51d85-225">INPUTS</span></span>

### <span data-ttu-id="51d85-226">System.Object</span><span class="sxs-lookup"><span data-stu-id="51d85-226">System.Object</span></span>

<span data-ttu-id="51d85-227">您可以使用管線將包含專案新值的物件傳送至 `Set-Content` 。</span><span class="sxs-lookup"><span data-stu-id="51d85-227">You can pipe an object that contains the new value for the item to `Set-Content`.</span></span>

## <span data-ttu-id="51d85-228">輸出</span><span class="sxs-lookup"><span data-stu-id="51d85-228">OUTPUTS</span></span>

### <span data-ttu-id="51d85-229">無或 System.String</span><span class="sxs-lookup"><span data-stu-id="51d85-229">None or System.String</span></span>

<span data-ttu-id="51d85-230">當您使用 **PassThru** 參數時，會 `Set-Content` 產生代表內容的 **system.string** 物件。</span><span class="sxs-lookup"><span data-stu-id="51d85-230">When you use the **PassThru** parameter, `Set-Content` generates a **System.String** object that represents the content.</span></span> <span data-ttu-id="51d85-231">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="51d85-231">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="51d85-232">注意</span><span class="sxs-lookup"><span data-stu-id="51d85-232">NOTES</span></span>

- <span data-ttu-id="51d85-233">您也可以 `Set-Content` 使用內建的別名來參考 `sc` 。</span><span class="sxs-lookup"><span data-stu-id="51d85-233">You can also refer to `Set-Content` by its built-in alias, `sc`.</span></span>
  <span data-ttu-id="51d85-234">如需詳細資訊，請參閱 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="51d85-234">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="51d85-235">`Set-Content` 是針對字串處理所設計。</span><span class="sxs-lookup"><span data-stu-id="51d85-235">`Set-Content` is designed for string processing.</span></span> <span data-ttu-id="51d85-236">如果您使用管線將非字串物件傳送至 `Set-Content` ，它會先將物件轉換成字串，再進行寫入。</span><span class="sxs-lookup"><span data-stu-id="51d85-236">If you pipe non-string objects to `Set-Content`, it converts the object to a string before writing it.</span></span> <span data-ttu-id="51d85-237">若要將物件寫入檔案，請使用 `Out-File` 。</span><span class="sxs-lookup"><span data-stu-id="51d85-237">To write objects to files, use `Out-File`.</span></span>
- <span data-ttu-id="51d85-238">此 `Set-Content` Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。</span><span class="sxs-lookup"><span data-stu-id="51d85-238">The `Set-Content` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="51d85-239">若要列出工作階段中可用的提供者，請輸入 `Get-PsProvider`。</span><span class="sxs-lookup"><span data-stu-id="51d85-239">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="51d85-240">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="51d85-240">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="51d85-241">相關連結</span><span class="sxs-lookup"><span data-stu-id="51d85-241">RELATED LINKS</span></span>

[<span data-ttu-id="51d85-242">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="51d85-242">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="51d85-243">about_Automatic_Variables md</span><span class="sxs-lookup"><span data-stu-id="51d85-243">about_Automatic_Variables.md</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="51d85-244">about_Providers</span><span class="sxs-lookup"><span data-stu-id="51d85-244">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="51d85-245">Add-Content</span><span class="sxs-lookup"><span data-stu-id="51d85-245">Add-Content</span></span>](Add-Content.md)

[<span data-ttu-id="51d85-246">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="51d85-246">Clear-Content</span></span>](Clear-Content.md)

[<span data-ttu-id="51d85-247">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="51d85-247">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="51d85-248">Get-Content</span><span class="sxs-lookup"><span data-stu-id="51d85-248">Get-Content</span></span>](Get-Content.md)

[<span data-ttu-id="51d85-249">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="51d85-249">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="51d85-250">New-Item</span><span class="sxs-lookup"><span data-stu-id="51d85-250">New-Item</span></span>](New-Item.md)
