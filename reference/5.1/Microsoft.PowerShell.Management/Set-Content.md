---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-content?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Content
ms.openlocfilehash: 897029cab790487f6834d021bfc447060fd39812
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203523"
---
# <span data-ttu-id="1e44a-103">Set-Content</span><span class="sxs-lookup"><span data-stu-id="1e44a-103">Set-Content</span></span>

## <span data-ttu-id="1e44a-104">概要</span><span class="sxs-lookup"><span data-stu-id="1e44a-104">SYNOPSIS</span></span>
<span data-ttu-id="1e44a-105">寫入新的內容，或取代檔案中的現有內容。</span><span class="sxs-lookup"><span data-stu-id="1e44a-105">Writes new content or replaces existing content in a file.</span></span>

## <span data-ttu-id="1e44a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1e44a-106">SYNTAX</span></span>

### <span data-ttu-id="1e44a-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="1e44a-107">Path (Default)</span></span>

```
Set-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [-NoNewline] [-Encoding <FileSystemCmdletProviderEncoding>]
 [-Stream <string>] [<CommonParameters>]
```

### <span data-ttu-id="1e44a-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="1e44a-108">LiteralPath</span></span>

```
Set-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [-NoNewline] [-Encoding <FileSystemCmdletProviderEncoding>]
 [-Stream <string>] [<CommonParameters>]
```

## <span data-ttu-id="1e44a-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="1e44a-109">DESCRIPTION</span></span>

<span data-ttu-id="1e44a-110">`Set-Content` 是字串處理 Cmdlet，會寫入新內容或取代檔案中的內容。</span><span class="sxs-lookup"><span data-stu-id="1e44a-110">`Set-Content` is a string-processing cmdlet that writes new content or replaces the content in a file.</span></span> <span data-ttu-id="1e44a-111">`Set-Content` 取代現有的內容，與將 `Add-Content` 內容附加至檔案的 Cmdlet 不同。</span><span class="sxs-lookup"><span data-stu-id="1e44a-111">`Set-Content` replaces the existing content and differs from the `Add-Content` cmdlet that appends content to a file.</span></span> <span data-ttu-id="1e44a-112">若要將內容傳送給 `Set-Content` 您，您可以在命令列上使用 **Value** 參數，或透過管線傳送內容。</span><span class="sxs-lookup"><span data-stu-id="1e44a-112">To send content to `Set-Content` you can use the **Value** parameter on the command line or send content through the pipeline.</span></span>

<span data-ttu-id="1e44a-113">如果您需要建立下列範例的檔案或目錄，請參閱 [新專案](New-Item.md)。</span><span class="sxs-lookup"><span data-stu-id="1e44a-113">If you need to create files or directories for the following examples, see [New-Item](New-Item.md).</span></span>

## <span data-ttu-id="1e44a-114">範例</span><span class="sxs-lookup"><span data-stu-id="1e44a-114">EXAMPLES</span></span>

### <span data-ttu-id="1e44a-115">範例1：取代目錄中多個檔案的內容</span><span class="sxs-lookup"><span data-stu-id="1e44a-115">Example 1: Replace the contents of multiple files in a directory</span></span>

<span data-ttu-id="1e44a-116">此範例會取代目前目錄中多個檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="1e44a-116">This example replaces the content for multiple files in the current directory.</span></span>

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

<span data-ttu-id="1e44a-117">此 `Get-ChildItem` Cmdlet 會使用 **Path** 參數來列出以目前的目錄開頭的 **.txt** 檔案。 `Test*`</span><span class="sxs-lookup"><span data-stu-id="1e44a-117">The `Get-ChildItem` cmdlet uses the **Path** parameter to list **.txt** files that begin with `Test*` in the current directory.</span></span> <span data-ttu-id="1e44a-118">此 `Set-Content` Cmdlet 會使用 **Path** 參數來指定檔案 `Test*.txt` 。</span><span class="sxs-lookup"><span data-stu-id="1e44a-118">The `Set-Content` cmdlet uses the **Path** parameter to specify the `Test*.txt` files.</span></span> <span data-ttu-id="1e44a-119">**Value** 參數提供文字字串 **Hello，World** 取代每個檔案中的現有內容。</span><span class="sxs-lookup"><span data-stu-id="1e44a-119">The **Value** parameter provides the text string **Hello, World** that replaces the existing content in each file.</span></span> <span data-ttu-id="1e44a-120">此 `Get-Content` Cmdlet 會使用 **Path** 參數來指定檔案 `Test*.txt` ，並在 PowerShell 主控台中顯示每個檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="1e44a-120">The `Get-Content` cmdlet uses the **Path** parameter to specify the `Test*.txt` files and displays each file's content in the PowerShell console.</span></span>

### <span data-ttu-id="1e44a-121">範例2：建立新檔案並寫入內容</span><span class="sxs-lookup"><span data-stu-id="1e44a-121">Example 2: Create a new file and write content</span></span>

<span data-ttu-id="1e44a-122">這個範例會建立新的檔案，並將目前的日期和時間寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="1e44a-122">This example creates a new file and writes the current date and time to the file.</span></span>

```powershell
Set-Content -Path .\DateTime.txt -Value (Get-Date)
Get-Content -Path .\DateTime.txt
```

```Output
1/30/2019 09:55:08
```

<span data-ttu-id="1e44a-123">`Set-Content` 使用 **Path** 和 **Value** 參數，在目前的目錄中建立名為 **DateTime.txt** 的新檔案。</span><span class="sxs-lookup"><span data-stu-id="1e44a-123">`Set-Content` uses the **Path** and **Value** parameters to create a new file named **DateTime.txt** in the current directory.</span></span> <span data-ttu-id="1e44a-124">**值** 參數會使用 `Get-Date` 來取得目前的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="1e44a-124">The **Value** parameter uses `Get-Date` to get the current date and time.</span></span>
<span data-ttu-id="1e44a-125">`Set-Content` 以字串的形式將 **DateTime** 物件寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="1e44a-125">`Set-Content` writes the **DateTime** object to the file as a string.</span></span> <span data-ttu-id="1e44a-126">此 `Get-Content` Cmdlet 會使用 **Path** 參數，在 PowerShell 主控台中顯示 **DateTime.txt** 的內容。</span><span class="sxs-lookup"><span data-stu-id="1e44a-126">The `Get-Content` cmdlet uses the **Path** parameter to display the content of **DateTime.txt** in the PowerShell console.</span></span>

### <span data-ttu-id="1e44a-127">範例3：取代檔案中的文字</span><span class="sxs-lookup"><span data-stu-id="1e44a-127">Example 3: Replace text in a file</span></span>

<span data-ttu-id="1e44a-128">此命令會取代現有檔案中的所有 word 實例。</span><span class="sxs-lookup"><span data-stu-id="1e44a-128">This command replaces all instances of word within an existing file.</span></span>

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

<span data-ttu-id="1e44a-129">此 `Get-Content` Cmdlet 會使用 **Path** 參數來指定目前目錄中的 **Notice.txt** 檔案。</span><span class="sxs-lookup"><span data-stu-id="1e44a-129">The `Get-Content` cmdlet uses the **Path** parameter to specify the **Notice.txt** file in the current directory.</span></span> <span data-ttu-id="1e44a-130">此 `Get-Content` 命令會以括弧括住，讓命令先完成，再向下傳送管線。</span><span class="sxs-lookup"><span data-stu-id="1e44a-130">The `Get-Content` command is wrapped with parentheses so that the command finishes before being sent down the pipeline.</span></span>

<span data-ttu-id="1e44a-131">**Notice.txt** 檔案的內容會向下傳送至 `ForEach-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1e44a-131">The contents of the **Notice.txt** file are sent down the pipeline to the `ForEach-Object` cmdlet.</span></span>
<span data-ttu-id="1e44a-132">`ForEach-Object`使用自動變數 `$_` ，並 **謹慎** 地取代每個出現的 **警告** 。</span><span class="sxs-lookup"><span data-stu-id="1e44a-132">`ForEach-Object` uses the automatic variable `$_` and replaces each occurrence of **Warning** with **Caution** .</span></span> <span data-ttu-id="1e44a-133">這些物件會向下傳送至 `Set-Content` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1e44a-133">The objects are sent down the pipeline to the `Set-Content` cmdlet.</span></span> <span data-ttu-id="1e44a-134">`Set-Content` 使用 **Path** 參數指定 **Notice.txt** 檔，並將更新的內容寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="1e44a-134">`Set-Content` uses the **Path** parameter to specify the **Notice.txt** file and writes the updated content to the file.</span></span>

<span data-ttu-id="1e44a-135">最後一個 `Get-Content` Cmdlet 會在 PowerShell 主控台中顯示已更新的檔案內容。</span><span class="sxs-lookup"><span data-stu-id="1e44a-135">The last `Get-Content` cmdlet displays the updated file content in the PowerShell console.</span></span>

### <span data-ttu-id="1e44a-136">範例4：搭配 Set-Content 使用篩選</span><span class="sxs-lookup"><span data-stu-id="1e44a-136">Example 4: Use Filters with Set-Content</span></span>

<span data-ttu-id="1e44a-137">您可以為 Cmdlet 指定篩選 `Set-Content` 。</span><span class="sxs-lookup"><span data-stu-id="1e44a-137">You can specify a filter to the `Set-Content` cmdlet.</span></span> <span data-ttu-id="1e44a-138">使用篩選準則來限定 **路徑** 參數時，您必須包含尾端星號 (`*`) 來指出路徑的內容。</span><span class="sxs-lookup"><span data-stu-id="1e44a-138">When using filters to qualify the **Path** parameter, you need to include a trailing asterisk (`*`) to indicate the contents of the path.</span></span>

<span data-ttu-id="1e44a-139">下列命令會將目錄中所有檔案的內容設定為 `*.txt` `C:\Temp` 空白 **Value** 。</span><span class="sxs-lookup"><span data-stu-id="1e44a-139">The following command set the content all `*.txt` files in the `C:\Temp` directory to the **Value** empty.</span></span>

```powershell
Set-Content -Path C:\Temp\* -Filter *.txt -Value "Empty"
```

## <span data-ttu-id="1e44a-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1e44a-140">PARAMETERS</span></span>

### <span data-ttu-id="1e44a-141">-Credential</span><span class="sxs-lookup"><span data-stu-id="1e44a-141">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="1e44a-142">使用 PowerShell 安裝的任何提供者都不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="1e44a-142">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="1e44a-143">若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="1e44a-143">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="1e44a-144">-Encoding</span><span class="sxs-lookup"><span data-stu-id="1e44a-144">-Encoding</span></span>

<span data-ttu-id="1e44a-145">指定目標檔案的編碼類型。</span><span class="sxs-lookup"><span data-stu-id="1e44a-145">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="1e44a-146">預設值是 `Default`。</span><span class="sxs-lookup"><span data-stu-id="1e44a-146">The default value is `Default`.</span></span>

<span data-ttu-id="1e44a-147">Encoding 是動態參數，FileSystem 提供者會將其加入至 `Set-Content` 。</span><span class="sxs-lookup"><span data-stu-id="1e44a-147">Encoding is a dynamic parameter that the FileSystem provider adds to `Set-Content`.</span></span> <span data-ttu-id="1e44a-148">此參數只適用於檔案系統磁碟機。</span><span class="sxs-lookup"><span data-stu-id="1e44a-148">This parameter works only in file system drives.</span></span>

<span data-ttu-id="1e44a-149">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="1e44a-149">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="1e44a-150">`Ascii` 使用 ASCII (7 位) 字元集。</span><span class="sxs-lookup"><span data-stu-id="1e44a-150">`Ascii` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="1e44a-151">`BigEndianUnicode` 以位元組由大到小的順序使用 UTF-16。</span><span class="sxs-lookup"><span data-stu-id="1e44a-151">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="1e44a-152">`BigEndianUTF32` 使用具有位元組由大到小的 32 UTF-8 順序。</span><span class="sxs-lookup"><span data-stu-id="1e44a-152">`BigEndianUTF32` Uses UTF-32 with the big-endian byte order.</span></span>
- <span data-ttu-id="1e44a-153">`Byte` 將一組字元編碼成位元組序列。</span><span class="sxs-lookup"><span data-stu-id="1e44a-153">`Byte` Encodes a set of characters into a sequence of bytes.</span></span>
- <span data-ttu-id="1e44a-154">`Default` 使用與系統的作用中字碼頁對應的編碼， (通常是 ANSI) 。</span><span class="sxs-lookup"><span data-stu-id="1e44a-154">`Default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="1e44a-155">`Oem` 使用對應至系統目前 OEM 字碼頁的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="1e44a-155">`Oem` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="1e44a-156">`String`：與 `Unicode` 相同。</span><span class="sxs-lookup"><span data-stu-id="1e44a-156">`String` Same as `Unicode`.</span></span>
- <span data-ttu-id="1e44a-157">`Unicode` 使用 UTF-16 和位元組由小到小的位元組順序。</span><span class="sxs-lookup"><span data-stu-id="1e44a-157">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="1e44a-158">`Unknown`：與 `Unicode` 相同。</span><span class="sxs-lookup"><span data-stu-id="1e44a-158">`Unknown` Same as `Unicode`.</span></span>
- <span data-ttu-id="1e44a-159">`UTF7` 使用 UTF-7。</span><span class="sxs-lookup"><span data-stu-id="1e44a-159">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="1e44a-160">`UTF8` 使用 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="1e44a-160">`UTF8` Uses UTF-8.</span></span>
- <span data-ttu-id="1e44a-161">`UTF32` 以位元組由小到大的位元組順序使用 UTF-32。</span><span class="sxs-lookup"><span data-stu-id="1e44a-161">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>

<span data-ttu-id="1e44a-162">Encoding 是動態參數，FileSystem 提供者會將其加入至 `Set-Content` 。</span><span class="sxs-lookup"><span data-stu-id="1e44a-162">Encoding is a dynamic parameter that the FileSystem provider adds to `Set-Content`.</span></span> <span data-ttu-id="1e44a-163">此參數只適用於檔案系統磁碟機。</span><span class="sxs-lookup"><span data-stu-id="1e44a-163">This parameter works only in file system drives.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, Byte, Default, OEM, String, Unicode, Unknown, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1e44a-164">-Exclude</span><span class="sxs-lookup"><span data-stu-id="1e44a-164">-Exclude</span></span>

<span data-ttu-id="1e44a-165">以字串陣列指定此 Cmdlet 在作業中排除的專案。</span><span class="sxs-lookup"><span data-stu-id="1e44a-165">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="1e44a-166">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="1e44a-166">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="1e44a-167">輸入路徑元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="1e44a-167">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="1e44a-168">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="1e44a-168">Wildcard characters are permitted.</span></span> <span data-ttu-id="1e44a-169">只有當命令包含專案的內容（例如）時，才會使用 **Exclude** 參數， `C:\Windows\*` 其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="1e44a-169">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="1e44a-170">-Filter</span><span class="sxs-lookup"><span data-stu-id="1e44a-170">-Filter</span></span>

<span data-ttu-id="1e44a-171">指定要限定 **路徑** 參數的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="1e44a-171">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="1e44a-172">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供者是唯一支援使用篩選器的已安裝 PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="1e44a-172">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="1e44a-173">您可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **檔案系統** 篩選器語言的語法。</span><span class="sxs-lookup"><span data-stu-id="1e44a-173">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="1e44a-174">篩選比其他參數更有效率，因為提供者會在 Cmdlet 取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。</span><span class="sxs-lookup"><span data-stu-id="1e44a-174">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="1e44a-175">-Force</span><span class="sxs-lookup"><span data-stu-id="1e44a-175">-Force</span></span>

<span data-ttu-id="1e44a-176">強制 Cmdlet 設定檔案的內容，即使檔案是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="1e44a-176">Forces the cmdlet to set the contents of a file, even if the file is read-only.</span></span> <span data-ttu-id="1e44a-177">實作會依提供者而異。</span><span class="sxs-lookup"><span data-stu-id="1e44a-177">Implementation varies from provider to provider.</span></span> <span data-ttu-id="1e44a-178">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="1e44a-178">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
<span data-ttu-id="1e44a-179">**Force** 參數不會覆寫安全性限制。</span><span class="sxs-lookup"><span data-stu-id="1e44a-179">The **Force** parameter does not override security restrictions.</span></span>

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

### <span data-ttu-id="1e44a-180">-Include</span><span class="sxs-lookup"><span data-stu-id="1e44a-180">-Include</span></span>

<span data-ttu-id="1e44a-181">以字串陣列指定此 Cmdlet 在作業中納入的項目。</span><span class="sxs-lookup"><span data-stu-id="1e44a-181">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="1e44a-182">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="1e44a-182">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="1e44a-183">輸入路徑元素或模式，例如 `"*.txt"`。</span><span class="sxs-lookup"><span data-stu-id="1e44a-183">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="1e44a-184">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="1e44a-184">Wildcard characters are permitted.</span></span> <span data-ttu-id="1e44a-185">**Include** 參數只有當命令包含專案內容時才有效，例如 `C:\Windows\*` ，其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="1e44a-185">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="1e44a-186">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="1e44a-186">-LiteralPath</span></span>

<span data-ttu-id="1e44a-187">指定一個或多個位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="1e44a-187">Specifies a path to one or more locations.</span></span> <span data-ttu-id="1e44a-188">**LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="1e44a-188">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="1e44a-189">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="1e44a-189">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="1e44a-190">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="1e44a-190">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="1e44a-191">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="1e44a-191">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="1e44a-192">如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="1e44a-192">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1e44a-193">-NoNewline</span><span class="sxs-lookup"><span data-stu-id="1e44a-193">-NoNewline</span></span>

<span data-ttu-id="1e44a-194">輸入物件的字串表示會串連以形成輸出。</span><span class="sxs-lookup"><span data-stu-id="1e44a-194">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="1e44a-195">輸出字串之間不會插入空格或分行符號。</span><span class="sxs-lookup"><span data-stu-id="1e44a-195">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="1e44a-196">最後一個輸出字串之後不會加入任何新行。</span><span class="sxs-lookup"><span data-stu-id="1e44a-196">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="1e44a-197">-PassThru</span><span class="sxs-lookup"><span data-stu-id="1e44a-197">-PassThru</span></span>

<span data-ttu-id="1e44a-198">傳回代表內容的物件。</span><span class="sxs-lookup"><span data-stu-id="1e44a-198">Returns an object that represents the content.</span></span> <span data-ttu-id="1e44a-199">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="1e44a-199">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="1e44a-200">-Path</span><span class="sxs-lookup"><span data-stu-id="1e44a-200">-Path</span></span>

<span data-ttu-id="1e44a-201">指定接收內容之專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="1e44a-201">Specifies the path of the item that receives the content.</span></span>
<span data-ttu-id="1e44a-202">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="1e44a-202">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="1e44a-203">-Stream</span><span class="sxs-lookup"><span data-stu-id="1e44a-203">-Stream</span></span>

<span data-ttu-id="1e44a-204">指定內容的替代資料流程。</span><span class="sxs-lookup"><span data-stu-id="1e44a-204">Specifies an alternative data stream for content.</span></span> <span data-ttu-id="1e44a-205">如果資料流程不存在，此 Cmdlet 會建立該資料流程。</span><span class="sxs-lookup"><span data-stu-id="1e44a-205">If the stream does not exist, this cmdlet creates it.</span></span> <span data-ttu-id="1e44a-206">不支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="1e44a-206">Wildcard characters are not supported.</span></span>

<span data-ttu-id="1e44a-207">**Stream** 是動態參數， **FileSystem** 提供者會將其加入至 `Set-Content` 。</span><span class="sxs-lookup"><span data-stu-id="1e44a-207">**Stream** is a dynamic parameter that the **FileSystem** provider adds to `Set-Content`.</span></span> <span data-ttu-id="1e44a-208">此參數只適用於檔案系統磁碟機。</span><span class="sxs-lookup"><span data-stu-id="1e44a-208">This parameter works only in file system drives.</span></span>

<span data-ttu-id="1e44a-209">您可以使用 `Set-Content` Cmdlet 來變更區域的內容 **。識別碼** 替代資料流程。</span><span class="sxs-lookup"><span data-stu-id="1e44a-209">You can use the `Set-Content` cmdlet to change the content of the **Zone.Identifier** alternate data stream.</span></span> <span data-ttu-id="1e44a-210">不過，我們不建議您這樣做，以排除封鎖從網際網路下載之檔案的安全性檢查。</span><span class="sxs-lookup"><span data-stu-id="1e44a-210">However, we do not recommend this as a way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="1e44a-211">如果您確認下載的檔案是安全的，請使用 `Unblock-File` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1e44a-211">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="1e44a-212">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="1e44a-212">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="1e44a-213">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="1e44a-213">-UseTransaction</span></span>

<span data-ttu-id="1e44a-214">將命令加入使用中交易。</span><span class="sxs-lookup"><span data-stu-id="1e44a-214">Includes the command in the active transaction.</span></span> <span data-ttu-id="1e44a-215">只有交易為處理中狀態時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="1e44a-215">This parameter is valid only when a transaction is in progress.</span></span> <span data-ttu-id="1e44a-216">如需詳細資訊，請參閱 [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)。</span><span class="sxs-lookup"><span data-stu-id="1e44a-216">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1e44a-217">-Value</span><span class="sxs-lookup"><span data-stu-id="1e44a-217">-Value</span></span>

<span data-ttu-id="1e44a-218">指定項目的新內容。</span><span class="sxs-lookup"><span data-stu-id="1e44a-218">Specifies the new content for the item.</span></span>

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

### <span data-ttu-id="1e44a-219">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1e44a-219">-Confirm</span></span>

<span data-ttu-id="1e44a-220">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="1e44a-220">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="1e44a-221">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1e44a-221">-WhatIf</span></span>

<span data-ttu-id="1e44a-222">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="1e44a-222">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="1e44a-223">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="1e44a-223">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="1e44a-224">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1e44a-224">CommonParameters</span></span>

<span data-ttu-id="1e44a-225">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="1e44a-225">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span>
<span data-ttu-id="1e44a-226">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="1e44a-226">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="1e44a-227">輸入</span><span class="sxs-lookup"><span data-stu-id="1e44a-227">INPUTS</span></span>

### <span data-ttu-id="1e44a-228">System.Object</span><span class="sxs-lookup"><span data-stu-id="1e44a-228">System.Object</span></span>

<span data-ttu-id="1e44a-229">您可以使用管線將包含專案新值的物件傳送至 `Set-Content` 。</span><span class="sxs-lookup"><span data-stu-id="1e44a-229">You can pipe an object that contains the new value for the item to `Set-Content`.</span></span>

## <span data-ttu-id="1e44a-230">輸出</span><span class="sxs-lookup"><span data-stu-id="1e44a-230">OUTPUTS</span></span>

### <span data-ttu-id="1e44a-231">無或 System.String</span><span class="sxs-lookup"><span data-stu-id="1e44a-231">None or System.String</span></span>

<span data-ttu-id="1e44a-232">當您使用 **PassThru** 參數時，會 `Set-Content` 產生代表內容的 **system.string** 物件。</span><span class="sxs-lookup"><span data-stu-id="1e44a-232">When you use the **PassThru** parameter, `Set-Content` generates a **System.String** object that represents the content.</span></span> <span data-ttu-id="1e44a-233">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="1e44a-233">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="1e44a-234">注意</span><span class="sxs-lookup"><span data-stu-id="1e44a-234">NOTES</span></span>

- <span data-ttu-id="1e44a-235">您也可以 `Set-Content` 使用內建的別名來參考 `sc` 。</span><span class="sxs-lookup"><span data-stu-id="1e44a-235">You can also refer to `Set-Content` by its built-in alias, `sc`.</span></span>
  <span data-ttu-id="1e44a-236">如需詳細資訊，請參閱 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="1e44a-236">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="1e44a-237">`Set-Content` 是針對字串處理所設計。</span><span class="sxs-lookup"><span data-stu-id="1e44a-237">`Set-Content` is designed for string processing.</span></span> <span data-ttu-id="1e44a-238">如果您使用管線將非字串物件傳送至 `Set-Content` ，它會先將物件轉換成字串，再進行寫入。</span><span class="sxs-lookup"><span data-stu-id="1e44a-238">If you pipe non-string objects to `Set-Content`, it converts the object to a string before writing it.</span></span> <span data-ttu-id="1e44a-239">若要將物件寫入檔案，請使用 `Out-File` 。</span><span class="sxs-lookup"><span data-stu-id="1e44a-239">To write objects to files, use `Out-File`.</span></span>
- <span data-ttu-id="1e44a-240">此 `Set-Content` Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。</span><span class="sxs-lookup"><span data-stu-id="1e44a-240">The `Set-Content` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="1e44a-241">若要列出工作階段中可用的提供者，請輸入 `Get-PsProvider`。</span><span class="sxs-lookup"><span data-stu-id="1e44a-241">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="1e44a-242">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="1e44a-242">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="1e44a-243">相關連結</span><span class="sxs-lookup"><span data-stu-id="1e44a-243">RELATED LINKS</span></span>

[<span data-ttu-id="1e44a-244">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="1e44a-244">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="1e44a-245">about_Automatic_Variables md</span><span class="sxs-lookup"><span data-stu-id="1e44a-245">about_Automatic_Variables.md</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="1e44a-246">about_Providers</span><span class="sxs-lookup"><span data-stu-id="1e44a-246">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="1e44a-247">about_Transactions</span><span class="sxs-lookup"><span data-stu-id="1e44a-247">about_Transactions</span></span>](../Microsoft.PowerShell.Core/About/about_Transactions.md)

[<span data-ttu-id="1e44a-248">Add-Content</span><span class="sxs-lookup"><span data-stu-id="1e44a-248">Add-Content</span></span>](Add-Content.md)

[<span data-ttu-id="1e44a-249">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="1e44a-249">Clear-Content</span></span>](Clear-Content.md)

[<span data-ttu-id="1e44a-250">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="1e44a-250">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="1e44a-251">Get-Content</span><span class="sxs-lookup"><span data-stu-id="1e44a-251">Get-Content</span></span>](Get-Content.md)

[<span data-ttu-id="1e44a-252">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="1e44a-252">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="1e44a-253">New-Item</span><span class="sxs-lookup"><span data-stu-id="1e44a-253">New-Item</span></span>](New-Item.md)
