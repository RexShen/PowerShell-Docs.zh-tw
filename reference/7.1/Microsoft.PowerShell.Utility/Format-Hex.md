---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-hex?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Hex
ms.openlocfilehash: 587f063c425ceb7561bdd2f9f696c8b3d638a835
ms.sourcegitcommit: 9a8bb1b459b5939c95e1f6d9499fcb13d01a58c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "93206123"
---
# <span data-ttu-id="c187c-103">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="c187c-103">Format-Hex</span></span>

## <span data-ttu-id="c187c-104">概要</span><span class="sxs-lookup"><span data-stu-id="c187c-104">SYNOPSIS</span></span>

<span data-ttu-id="c187c-105">以十六進位格式顯示檔案或其他輸入。</span><span class="sxs-lookup"><span data-stu-id="c187c-105">Displays a file or other input as hexadecimal.</span></span>

## <span data-ttu-id="c187c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c187c-106">SYNTAX</span></span>

### <span data-ttu-id="c187c-107">路徑</span><span class="sxs-lookup"><span data-stu-id="c187c-107">Path</span></span>

```
Format-Hex [-Path] <String[]> [-Count <Int64>] [-Offset <Int64>] [<CommonParameters>]
```

### <span data-ttu-id="c187c-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c187c-108">LiteralPath</span></span>

```
Format-Hex -LiteralPath <String[]> [-Count <Int64>] [-Offset <Int64>] [<CommonParameters>]
```

### <span data-ttu-id="c187c-109">ByInputObject</span><span class="sxs-lookup"><span data-stu-id="c187c-109">ByInputObject</span></span>

```
Format-Hex -InputObject <PSObject> [-Encoding <Encoding>] [-Count <Int64>] [-Offset <Int64>] [-Raw]
 [<CommonParameters>]
```

## <span data-ttu-id="c187c-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="c187c-110">DESCRIPTION</span></span>

<span data-ttu-id="c187c-111">`Format-Hex`Cmdlet 會以十六進位值顯示檔案或其他輸入。</span><span class="sxs-lookup"><span data-stu-id="c187c-111">The `Format-Hex` cmdlet displays a file or other input as hexadecimal values.</span></span> <span data-ttu-id="c187c-112">若要判斷輸出中的字元位移，請將資料列最左邊的數字加到該字元的資料欄上方的數字。</span><span class="sxs-lookup"><span data-stu-id="c187c-112">To determine the offset of a character from the output, add the number at the leftmost of the row to the number at the top of the column for that character.</span></span>

<span data-ttu-id="c187c-113">此 `Format-Hex` Cmdlet 可協助您判斷損毀檔案的檔案類型，或可能沒有副檔名的檔案。</span><span class="sxs-lookup"><span data-stu-id="c187c-113">The `Format-Hex` cmdlet can help you determine the file type of a corrupted file or a file that might not have a filename extension.</span></span> <span data-ttu-id="c187c-114">您可以執行此 Cmdlet，然後讀取十六進位輸出以取得檔案資訊。</span><span class="sxs-lookup"><span data-stu-id="c187c-114">You can run this cmdlet, and then read the hexadecimal output to get file information.</span></span>

<span data-ttu-id="c187c-115">在檔案 `Format-Hex` 上使用時，此 Cmdlet 會忽略分行符號，並以保留分行符號的一個字串傳回檔案的整個內容。</span><span class="sxs-lookup"><span data-stu-id="c187c-115">When using `Format-Hex` on a file, the cmdlet ignores newline characters and returns the entire contents of a file in one string with the newline characters preserved.</span></span>

## <span data-ttu-id="c187c-116">範例</span><span class="sxs-lookup"><span data-stu-id="c187c-116">EXAMPLES</span></span>

### <span data-ttu-id="c187c-117">範例 1︰取得字串的十六進位表示法</span><span class="sxs-lookup"><span data-stu-id="c187c-117">Example 1: Get the hexadecimal representation of a string</span></span>

<span data-ttu-id="c187c-118">此命令會傳回字串的十六進位值。</span><span class="sxs-lookup"><span data-stu-id="c187c-118">This command returns the hexadecimal values of a string.</span></span>

```powershell
'Hello World' | Format-Hex
```

```Output
   Label: String (System.String) <2944BEC3>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 48 65 6C 6C 6F 20 57 6F 72 6C 64                Hello World
```

<span data-ttu-id="c187c-119">**Hello World** 的字串會沿著管線向下傳送至 `Format-Hex` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c187c-119">The string **Hello World** is sent down the pipeline to the `Format-Hex` cmdlet.</span></span> <span data-ttu-id="c187c-120">的十六進位輸出會 `Format-Hex` 顯示字串中每個字元的值。</span><span class="sxs-lookup"><span data-stu-id="c187c-120">The hexadecimal output from `Format-Hex` shows the values of each character in the string.</span></span>

### <span data-ttu-id="c187c-121">範例2：從十六進位輸出尋找檔案類型</span><span class="sxs-lookup"><span data-stu-id="c187c-121">Example 2: Find a file type from hexadecimal output</span></span>

<span data-ttu-id="c187c-122">這個範例會使用十六進位輸出來判斷檔案類型。</span><span class="sxs-lookup"><span data-stu-id="c187c-122">This example uses the hexadecimal output to determine the file type.</span></span> <span data-ttu-id="c187c-123">此 Cmdlet 會顯示檔案的完整路徑和十六進位值。</span><span class="sxs-lookup"><span data-stu-id="c187c-123">The cmdlet displays the file's full path and the hexadecimal values.</span></span>

<span data-ttu-id="c187c-124">若要測試下列命令，請在本機電腦上複製現有的 PDF 檔案，然後將複製的檔案重新命名為 `File.t7f` 。</span><span class="sxs-lookup"><span data-stu-id="c187c-124">To test the following command, make a copy of an existing PDF file on your local computer and rename the copied file to `File.t7f`.</span></span>

```powershell
Format-Hex -Path .\File.t7f -Count 48
```

```Output
   Label: C:\Test\File.t7f

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 25 50 44 46 2D 31 2E 35 0D 0A 25 B5 B5 B5 B5 0D %PDF-1.5..%????.
0000000000000010 0A 31 20 30 20 6F 62 6A 0D 0A 3C 3C 2F 54 79 70 .1 0 obj..<</Typ
0000000000000020 65 2F 43 61 74 61 6C 6F 67 2F 50 61 67 65 73 20 e/Catalog/Pages
```

<span data-ttu-id="c187c-125">此 `Format-Hex` Cmdlet 會使用 **Path** 參數來指定當前目錄中的檔案名 `File.t7f` 。</span><span class="sxs-lookup"><span data-stu-id="c187c-125">The `Format-Hex` cmdlet uses the **Path** parameter to specify a filename in the current directory, `File.t7f`.</span></span> <span data-ttu-id="c187c-126">副檔名 `.t7f` 很罕見，但十六進位輸出 `%PDF` 顯示它是 PDF 檔案。</span><span class="sxs-lookup"><span data-stu-id="c187c-126">The file extension `.t7f` is uncommon, but the hexadecimal output `%PDF` shows that it is a PDF file.</span></span> <span data-ttu-id="c187c-127">在此範例中， **Count** 參數是用來將輸出限制為檔案的前48個位元組。</span><span class="sxs-lookup"><span data-stu-id="c187c-127">In this example, the **Count** parameter is used to limit the output to the first 48 bytes of the file.</span></span>

### <span data-ttu-id="c187c-128">範例3：將不同資料類型的陣列格式化</span><span class="sxs-lookup"><span data-stu-id="c187c-128">Example 3: Format an array of different data types</span></span>

<span data-ttu-id="c187c-129">此範例會使用不同資料類型的陣列，以醒目提示如何 `Format-Hex` 在管線中處理它們。</span><span class="sxs-lookup"><span data-stu-id="c187c-129">This example uses an array of different data types to highlight how `Format-Hex` handles them in the Pipeline.</span></span>

<span data-ttu-id="c187c-130">它會透過管線和個別處理來傳遞每個物件。</span><span class="sxs-lookup"><span data-stu-id="c187c-130">It will pass each object through the Pipeline and process individually.</span></span> <span data-ttu-id="c187c-131">但是，如果是數值資料，且連續的物件也是數值，則會將它們分組為單一輸出區塊。</span><span class="sxs-lookup"><span data-stu-id="c187c-131">However, if it's numeric data, and the adjacent object is also numeric, it will group them into a single output block.</span></span>

```powershell
'Hello world!', 1, 1138, 'foo', 'bar', 0xdeadbeef, 1gb, 0b1101011100 , $true, $false | Format-Hex
```

```Output
   Label: String (System.String) <24F1F0A3>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 48 65 6C 6C 6F 20 77 6F 72 6C 64 21             Hello world!

   Label: Int32 (System.Int32) <2EB933C5>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 01 00 00 00 72 04 00 00                         �   r�

   Label: String (System.String) <4078B66C>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 66 6F 6F                                        foo

   Label: String (System.String) <51E4A317>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 62 61 72                                        bar

   Label: Int32 (System.Int32) <5ADF167B>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 EF BE AD DE 00 00 00 40 5C 03 00 00             ï¾-Þ   @\�

   Label: Boolean (System.Boolean) <7D8C4C1D>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 01 00 00 00 00 00 00 00                         �
```

## <span data-ttu-id="c187c-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c187c-132">PARAMETERS</span></span>

### <span data-ttu-id="c187c-133">-Encoding</span><span class="sxs-lookup"><span data-stu-id="c187c-133">-Encoding</span></span>

<span data-ttu-id="c187c-134">指定輸入字串的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="c187c-134">Specifies the encoding of the input strings.</span></span> <span data-ttu-id="c187c-135">這僅適用于 `[string]` 輸入。</span><span class="sxs-lookup"><span data-stu-id="c187c-135">This only applies to `[string]` input.</span></span> <span data-ttu-id="c187c-136">參數對數數值型別沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="c187c-136">The parameter has no effect on numeric types.</span></span> <span data-ttu-id="c187c-137">輸出值一律為 `utf8NoBOM` 。</span><span class="sxs-lookup"><span data-stu-id="c187c-137">The output value is always `utf8NoBOM`.</span></span>

<span data-ttu-id="c187c-138">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="c187c-138">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="c187c-139">`ascii`：使用 ASCII (7 位) 字元集的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="c187c-139">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="c187c-140">`bigendianunicode`：使用位元組由大到小的位元組順序，以 UTF-16 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="c187c-140">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="c187c-141">`bigendianutf32`：使用位元組由大到小的順序，以 UTF-32 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="c187c-141">`bigendianutf32`: Encodes in UTF-32 format using the big-endian byte order.</span></span>
- <span data-ttu-id="c187c-142">`oem`：針對 MS-DOS 和主控台程式使用預設編碼。</span><span class="sxs-lookup"><span data-stu-id="c187c-142">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="c187c-143">`unicode`：使用位元組由大到小的位元組順序，以 UTF-16 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="c187c-143">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="c187c-144">`utf7`：以 UTF-7 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="c187c-144">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="c187c-145">`utf8`：以 UTF-8 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="c187c-145">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="c187c-146">`utf8BOM`：使用 (BOM) 的位元組順序標記來編碼 UTF-8 格式</span><span class="sxs-lookup"><span data-stu-id="c187c-146">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="c187c-147">`utf8NoBOM`：以不含位元組順序標記的 UTF-8 格式來編碼 (BOM) </span><span class="sxs-lookup"><span data-stu-id="c187c-147">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="c187c-148">`utf32`：以 UTF-32 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="c187c-148">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="c187c-149">從 PowerShell 6.2 開始， **編碼** 參數也會允許已註冊字碼頁的數值識別碼 (例如 `-Encoding 1251`) 或已註冊字碼頁的字串名稱 (例如 `-Encoding "windows-1251"`) 。</span><span class="sxs-lookup"><span data-stu-id="c187c-149">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="c187c-150">如需詳細資訊，請參閱 .NET 檔中的 [編碼字碼頁](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)。</span><span class="sxs-lookup"><span data-stu-id="c187c-150">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

> [!NOTE]
> <span data-ttu-id="c187c-151">您不再建議使用 **utf-7** \*。</span><span class="sxs-lookup"><span data-stu-id="c187c-151">**UTF-7** \* is no longer recommended to use.</span></span> <span data-ttu-id="c187c-152">在 PowerShell 7.1 中，如果您 `utf7` 針對 **編碼** 參數指定，就會寫入警告。</span><span class="sxs-lookup"><span data-stu-id="c187c-152">In PowerShell 7.1, a warning is written if you specify `utf7` for the **Encoding** parameter.</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: ByInputObject
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c187c-153">-InputObject</span><span class="sxs-lookup"><span data-stu-id="c187c-153">-InputObject</span></span>

<span data-ttu-id="c187c-154">用於管線輸入。</span><span class="sxs-lookup"><span data-stu-id="c187c-154">Used for pipeline input.</span></span> <span data-ttu-id="c187c-155">管線輸入僅支援特定的純量類型和 `[system.io.fileinfo]` 用於輸送的實例 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="c187c-155">Pipeline input supports only certain scalar types and `[system.io.fileinfo]` instances for piping from `Get-ChildItem`.</span></span>

<span data-ttu-id="c187c-156">支援的純量類型為：</span><span class="sxs-lookup"><span data-stu-id="c187c-156">The supported scalar types are:</span></span>

- <span data-ttu-id="c187c-157">`[string]`, `[char]`</span><span class="sxs-lookup"><span data-stu-id="c187c-157">`[string]`, `[char]`</span></span>
- <span data-ttu-id="c187c-158">`[byte]`, `[sbyte]`</span><span class="sxs-lookup"><span data-stu-id="c187c-158">`[byte]`, `[sbyte]`</span></span>
- <span data-ttu-id="c187c-159">`[int16]`, `[uint16]`, `[short]`, `[ushort]`</span><span class="sxs-lookup"><span data-stu-id="c187c-159">`[int16]`, `[uint16]`, `[short]`, `[ushort]`</span></span>
- <span data-ttu-id="c187c-160">`[int]`, `[uint]`, `[int32]`, `[uint32]`,</span><span class="sxs-lookup"><span data-stu-id="c187c-160">`[int]`, `[uint]`, `[int32]`, `[uint32]`,</span></span>
- <span data-ttu-id="c187c-161">`[long]`, `[ulong]`, `[int64]`, `[uint64]`</span><span class="sxs-lookup"><span data-stu-id="c187c-161">`[long]`, `[ulong]`, `[int64]`, `[uint64]`</span></span>
- <span data-ttu-id="c187c-162">`[single]`, `[float]`, `[double]`</span><span class="sxs-lookup"><span data-stu-id="c187c-162">`[single]`, `[float]`, `[double]`</span></span>
- `[boolean]`

<span data-ttu-id="c187c-163">在 PowerShell 6.2 之前， `Format-Hex` 會將所有類似物件組成群組，以處理具有多個輸入類型的管線輸入。</span><span class="sxs-lookup"><span data-stu-id="c187c-163">Prior to PowerShell 6.2, `Format-Hex` would handle a Pipeline input with multiple input types by grouping all like objects together.</span></span> <span data-ttu-id="c187c-164">現在，它會處理通過管線的每個個別物件，而且不會將物件群組在一起，除非像是連續的物件。</span><span class="sxs-lookup"><span data-stu-id="c187c-164">Now, it handles each individual object as it passes through the Pipeline and won't group objects together unless like objects are adjacent.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c187c-165">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c187c-165">-LiteralPath</span></span>

<span data-ttu-id="c187c-166">指定檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="c187c-166">Specifies the complete path to a file.</span></span> <span data-ttu-id="c187c-167">**LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="c187c-167">The value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="c187c-168">此參數不接受萬用字元。</span><span class="sxs-lookup"><span data-stu-id="c187c-168">This parameter does not accept wildcard characters.</span></span> <span data-ttu-id="c187c-169">若要指定多個檔案路徑，請使用逗號分隔路徑。</span><span class="sxs-lookup"><span data-stu-id="c187c-169">To specify multiple paths to files, separate the paths with a comma.</span></span> <span data-ttu-id="c187c-170">如果 **LiteralPath** 參數包含 escape 字元，請用單引號括住路徑。</span><span class="sxs-lookup"><span data-stu-id="c187c-170">If the **LiteralPath** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="c187c-171">PowerShell 不會將單引號字串中的任何字元視為 escape 序列來解讀。</span><span class="sxs-lookup"><span data-stu-id="c187c-171">PowerShell does not interpret any characters in a single quoted string as escape sequences.</span></span> <span data-ttu-id="c187c-172">如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="c187c-172">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c187c-173">-Path</span><span class="sxs-lookup"><span data-stu-id="c187c-173">-Path</span></span>

<span data-ttu-id="c187c-174">指定檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="c187c-174">Specifies the path to files.</span></span> <span data-ttu-id="c187c-175">使用點 (`.`) 來指定目前的位置。</span><span class="sxs-lookup"><span data-stu-id="c187c-175">Use a dot (`.`) to specify the current location.</span></span> <span data-ttu-id="c187c-176">接受萬用字元 (`*`) ，而且可以用來指定位置中的所有專案。</span><span class="sxs-lookup"><span data-stu-id="c187c-176">The wildcard character (`*`) is accepted and can be used to specify all the items in a location.</span></span> <span data-ttu-id="c187c-177">如果 **path** 參數包含 escape 字元，請用單引號括住路徑。</span><span class="sxs-lookup"><span data-stu-id="c187c-177">If the **Path** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="c187c-178">若要指定多個檔案路徑，請使用逗號分隔路徑。</span><span class="sxs-lookup"><span data-stu-id="c187c-178">To specify multiple paths to files, separate the paths with a comma.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="c187c-179">-Raw</span><span class="sxs-lookup"><span data-stu-id="c187c-179">-Raw</span></span>

<span data-ttu-id="c187c-180">此參數不會再執行任何作業。</span><span class="sxs-lookup"><span data-stu-id="c187c-180">This parameter no longer does anything.</span></span> <span data-ttu-id="c187c-181">它是為了腳本相容性而保留。</span><span class="sxs-lookup"><span data-stu-id="c187c-181">It is retained for script compatibility.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c187c-182">-位移</span><span class="sxs-lookup"><span data-stu-id="c187c-182">-Offset</span></span>

<span data-ttu-id="c187c-183">這代表要略過的位元組數目是十六進位輸出的一部分。</span><span class="sxs-lookup"><span data-stu-id="c187c-183">This represents the number of bytes to skip from being part of the hex output.</span></span>

<span data-ttu-id="c187c-184">此參數是在 PowerShell 6.2 中引進。</span><span class="sxs-lookup"><span data-stu-id="c187c-184">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c187c-185">-Count</span><span class="sxs-lookup"><span data-stu-id="c187c-185">-Count</span></span>

<span data-ttu-id="c187c-186">這代表要包含在十六進位輸出中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="c187c-186">This represents the number of bytes to include in the hex output.</span></span>

<span data-ttu-id="c187c-187">此參數是在 PowerShell 6.2 中引進。</span><span class="sxs-lookup"><span data-stu-id="c187c-187">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Int64.MaxValue
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c187c-188">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c187c-188">CommonParameters</span></span>

<span data-ttu-id="c187c-189">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="c187c-189">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c187c-190">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="c187c-190">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c187c-191">輸入</span><span class="sxs-lookup"><span data-stu-id="c187c-191">INPUTS</span></span>

### <span data-ttu-id="c187c-192">System.String</span><span class="sxs-lookup"><span data-stu-id="c187c-192">System.String</span></span>

<span data-ttu-id="c187c-193">您可以使用管線傳送字串至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c187c-193">You can pipe a string to this cmdlet.</span></span>

## <span data-ttu-id="c187c-194">輸出</span><span class="sxs-lookup"><span data-stu-id="c187c-194">OUTPUTS</span></span>

### <span data-ttu-id="c187c-195">Microsoft.PowerShell.Commands.ByteCollection</span><span class="sxs-lookup"><span data-stu-id="c187c-195">Microsoft.PowerShell.Commands.ByteCollection</span></span>

<span data-ttu-id="c187c-196">此 Cmdlet 會傳回 **ByteCollection** 。</span><span class="sxs-lookup"><span data-stu-id="c187c-196">This cmdlet returns a **ByteCollection** .</span></span> <span data-ttu-id="c187c-197">此物件表示位元組的集合。</span><span class="sxs-lookup"><span data-stu-id="c187c-197">This object represents a collection of bytes.</span></span> <span data-ttu-id="c187c-198">它包含將位元組集合轉換成字串格式的方法，例如所傳回的每一行輸出 `Format-Hex` 。</span><span class="sxs-lookup"><span data-stu-id="c187c-198">It includes methods that convert the collection of bytes to a string formatted like each line of output returned by `Format-Hex`.</span></span> <span data-ttu-id="c187c-199">輸出也會指出要處理的位元組類型。</span><span class="sxs-lookup"><span data-stu-id="c187c-199">The output also states they type of bytes being processed.</span></span> <span data-ttu-id="c187c-200">如果您指定 **path** 或 **LiteralPath** 參數，物件就會包含包含每個位元組之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="c187c-200">If you specify the **Path** or **LiteralPath** parameter, the object contains the path of the file that contains each byte.</span></span> <span data-ttu-id="c187c-201">如果您傳遞字串、布林值、整數等，則會適當地標示。</span><span class="sxs-lookup"><span data-stu-id="c187c-201">If you pass a string, boolean, integer, etc, it will be labeled appropriately.</span></span>

## <span data-ttu-id="c187c-202">注意</span><span class="sxs-lookup"><span data-stu-id="c187c-202">NOTES</span></span>

<span data-ttu-id="c187c-203">最右邊的輸出資料行嘗試將位元組轉譯為 ASCII 字元：</span><span class="sxs-lookup"><span data-stu-id="c187c-203">The right-most column of output tries to render the bytes as ASCII characters:</span></span>

<span data-ttu-id="c187c-204">一般而言，每個位元組都會轉譯為 Unicode 程式碼點，這表示：</span><span class="sxs-lookup"><span data-stu-id="c187c-204">Generally, each byte is interpreted as a Unicode code point, which means that:</span></span>

- <span data-ttu-id="c187c-205">可列印的 ASCII 字元一律會正確轉譯</span><span class="sxs-lookup"><span data-stu-id="c187c-205">Printable ASCII characters are always rendered correctly</span></span>
- <span data-ttu-id="c187c-206">多位元組 UTF-8 字元絕對不會正確呈現</span><span class="sxs-lookup"><span data-stu-id="c187c-206">Multi-byte UTF-8 characters never render correctly</span></span>
- <span data-ttu-id="c187c-207">UTF-16 字元會在其高序位位元組發生時正確轉譯 `NUL` 。</span><span class="sxs-lookup"><span data-stu-id="c187c-207">UTF-16 characters render correctly only if their high-order byte happens be `NUL`.</span></span>

## <span data-ttu-id="c187c-208">相關連結</span><span class="sxs-lookup"><span data-stu-id="c187c-208">RELATED LINKS</span></span>

[<span data-ttu-id="c187c-209">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="c187c-209">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="c187c-210">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="c187c-210">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="c187c-211">Format-List</span><span class="sxs-lookup"><span data-stu-id="c187c-211">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="c187c-212">Format-Table</span><span class="sxs-lookup"><span data-stu-id="c187c-212">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="c187c-213">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="c187c-213">Format-Wide</span></span>](Format-Wide.md)

