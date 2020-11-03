---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/17/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-hex?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Hex
ms.openlocfilehash: 64275e72f8c21942179431b3aed4a17d328aa2e9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204648"
---
# <span data-ttu-id="e3f92-103">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="e3f92-103">Format-Hex</span></span>

## <span data-ttu-id="e3f92-104">概要</span><span class="sxs-lookup"><span data-stu-id="e3f92-104">SYNOPSIS</span></span>

<span data-ttu-id="e3f92-105">以十六進位格式顯示檔案或其他輸入。</span><span class="sxs-lookup"><span data-stu-id="e3f92-105">Displays a file or other input as hexadecimal.</span></span>

## <span data-ttu-id="e3f92-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e3f92-106">SYNTAX</span></span>

### <span data-ttu-id="e3f92-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="e3f92-107">Path (Default)</span></span>

```
Format-Hex [-Path] <string[]> [-Count <long>] [-Offset <long>] [<CommonParameters>]
```

### <span data-ttu-id="e3f92-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="e3f92-108">LiteralPath</span></span>

```
Format-Hex -LiteralPath <string[]> [-Count <long>] [-Offset <long>] [<CommonParameters>]
```

### <span data-ttu-id="e3f92-109">InputObject</span><span class="sxs-lookup"><span data-stu-id="e3f92-109">InputObject</span></span>

```
Format-Hex -InputObject <psobject> [-Encoding <Encoding>] [-Count <long>] [-Offset <long>] [-Raw] [<CommonParameters>]
```

## <span data-ttu-id="e3f92-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e3f92-110">DESCRIPTION</span></span>

<span data-ttu-id="e3f92-111">`Format-Hex`Cmdlet 會以十六進位值顯示檔案或其他輸入。</span><span class="sxs-lookup"><span data-stu-id="e3f92-111">The `Format-Hex` cmdlet displays a file or other input as hexadecimal values.</span></span> <span data-ttu-id="e3f92-112">若要判斷輸出中的字元位移，請將資料列最左邊的數字加到該字元的資料欄上方的數字。</span><span class="sxs-lookup"><span data-stu-id="e3f92-112">To determine the offset of a character from the output, add the number at the leftmost of the row to the number at the top of the column for that character.</span></span>

<span data-ttu-id="e3f92-113">此 `Format-Hex` Cmdlet 可協助您判斷損毀檔案的檔案類型，或可能沒有副檔名的檔案。</span><span class="sxs-lookup"><span data-stu-id="e3f92-113">The `Format-Hex` cmdlet can help you determine the file type of a corrupted file or a file that might not have a filename extension.</span></span> <span data-ttu-id="e3f92-114">您可以執行此 Cmdlet，然後讀取十六進位輸出以取得檔案資訊。</span><span class="sxs-lookup"><span data-stu-id="e3f92-114">You can run this cmdlet, and then read the hexadecimal output to get file information.</span></span>

<span data-ttu-id="e3f92-115">在檔案 `Format-Hex` 上使用時，此 Cmdlet 會忽略分行符號，並以保留分行符號的一個字串傳回檔案的整個內容。</span><span class="sxs-lookup"><span data-stu-id="e3f92-115">When using `Format-Hex` on a file, the cmdlet ignores newline characters and returns the entire contents of a file in one string with the newline characters preserved.</span></span>

## <span data-ttu-id="e3f92-116">範例</span><span class="sxs-lookup"><span data-stu-id="e3f92-116">EXAMPLES</span></span>

### <span data-ttu-id="e3f92-117">範例 1︰取得字串的十六進位表示法</span><span class="sxs-lookup"><span data-stu-id="e3f92-117">Example 1: Get the hexadecimal representation of a string</span></span>

<span data-ttu-id="e3f92-118">此命令會傳回字串的十六進位值。</span><span class="sxs-lookup"><span data-stu-id="e3f92-118">This command returns the hexadecimal values of a string.</span></span>

```powershell
'Hello World' | Format-Hex
```

```Output
           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   48 65 6C 6C 6F 20 57 6F 72 6C 64                 Hello World
```

<span data-ttu-id="e3f92-119">**Hello World** 的字串會沿著管線向下傳送至 `Format-Hex` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e3f92-119">The string **Hello World** is sent down the pipeline to the `Format-Hex` cmdlet.</span></span> <span data-ttu-id="e3f92-120">的十六進位輸出會 `Format-Hex` 顯示字串中每個字元的值。</span><span class="sxs-lookup"><span data-stu-id="e3f92-120">The hexadecimal output from `Format-Hex` shows the values of each character in the string.</span></span>

### <span data-ttu-id="e3f92-121">範例2：從十六進位輸出尋找檔案類型</span><span class="sxs-lookup"><span data-stu-id="e3f92-121">Example 2: Find a file type from hexadecimal output</span></span>

<span data-ttu-id="e3f92-122">這個範例會使用十六進位輸出來判斷檔案類型。</span><span class="sxs-lookup"><span data-stu-id="e3f92-122">This example uses the hexadecimal output to determine the file type.</span></span> <span data-ttu-id="e3f92-123">此 Cmdlet 會顯示檔案的完整路徑和十六進位值。</span><span class="sxs-lookup"><span data-stu-id="e3f92-123">The cmdlet displays the file's full path and the hexadecimal values.</span></span>

<span data-ttu-id="e3f92-124">若要測試下列命令，請在本機電腦上複製現有的 PDF 檔案，然後將複製的檔案重新命名為 `File.t7f` 。</span><span class="sxs-lookup"><span data-stu-id="e3f92-124">To test the following command, make a copy of an existing PDF file on your local computer and rename the copied file to `File.t7f`.</span></span>

```powershell
Format-Hex -Path .\File.t7f
```

```Output
           Path: C:\Test\File.t7f

           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   25 50 44 46 2D 31 2E 35 0D 0A 25 B5 B5 B5 B5 0D  %PDF-1.5..%????.
00000010   0A 31 20 30 20 6F 62 6A 0D 0A 3C 3C 2F 54 79 70  .1 0 obj..<</Typ
00000020   65 2F 43 61 74 61 6C 6F 67 2F 50 61 67 65 73 20  e/Catalog/Pages
```

<span data-ttu-id="e3f92-125">此 `Format-Hex` Cmdlet 會使用 **Path** 參數來指定當前目錄中的檔案名 **t7f** 。</span><span class="sxs-lookup"><span data-stu-id="e3f92-125">The `Format-Hex` cmdlet uses the **Path** parameter to specify a filename in the current directory, **File.t7f** .</span></span> <span data-ttu-id="e3f92-126">**T7f** 並不常見，但十六進位輸出 **% pdf** 顯示其為 PDF 檔案。</span><span class="sxs-lookup"><span data-stu-id="e3f92-126">The file extension **.t7f** is uncommon, but the hexadecimal output **%PDF** shows that it is a PDF file.</span></span>

## <span data-ttu-id="e3f92-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e3f92-127">PARAMETERS</span></span>

### <span data-ttu-id="e3f92-128">-Encoding</span><span class="sxs-lookup"><span data-stu-id="e3f92-128">-Encoding</span></span>

<span data-ttu-id="e3f92-129">指定輸出的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="e3f92-129">Specifies the encoding of the output.</span></span> <span data-ttu-id="e3f92-130">這僅適用于 `[string]` 輸入。</span><span class="sxs-lookup"><span data-stu-id="e3f92-130">This only applies to `[string]` input.</span></span> <span data-ttu-id="e3f92-131">參數對數數值型別沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="e3f92-131">The parameter has no effect on numeric types.</span></span> <span data-ttu-id="e3f92-132">預設值是 `utf8NoBOM`。</span><span class="sxs-lookup"><span data-stu-id="e3f92-132">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="e3f92-133">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="e3f92-133">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="e3f92-134">`ascii`：使用 ASCII (7 位) 字元集的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="e3f92-134">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="e3f92-135">`bigendianunicode`：使用位元組由大到小的位元組順序，以 UTF-16 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="e3f92-135">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="e3f92-136">`oem`：針對 MS-DOS 和主控台程式使用預設編碼。</span><span class="sxs-lookup"><span data-stu-id="e3f92-136">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="e3f92-137">`unicode`：使用位元組由大到小的位元組順序，以 UTF-16 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="e3f92-137">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="e3f92-138">`utf7`：以 UTF-7 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="e3f92-138">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="e3f92-139">`utf8`：以 UTF-8 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="e3f92-139">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="e3f92-140">`utf8BOM`：使用 (BOM) 的位元組順序標記來編碼 UTF-8 格式</span><span class="sxs-lookup"><span data-stu-id="e3f92-140">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="e3f92-141">`utf8NoBOM`：以不含位元組順序標記的 UTF-8 格式來編碼 (BOM) </span><span class="sxs-lookup"><span data-stu-id="e3f92-141">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="e3f92-142">`utf32`：以 UTF-32 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="e3f92-142">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="e3f92-143">從 PowerShell 6.2 開始， **編碼** 參數也會允許已註冊字碼頁的數值識別碼 (例如 `-Encoding 1251`) 或已註冊字碼頁的字串名稱 (例如 `-Encoding "windows-1251"`) 。</span><span class="sxs-lookup"><span data-stu-id="e3f92-143">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="e3f92-144">如需詳細資訊，請參閱 .NET 檔中的 [編碼字碼頁](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)。</span><span class="sxs-lookup"><span data-stu-id="e3f92-144">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

```yaml
Type: Encoding
Parameter Sets: ByInputObject
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e3f92-145">-InputObject</span><span class="sxs-lookup"><span data-stu-id="e3f92-145">-InputObject</span></span>

<span data-ttu-id="e3f92-146">用於管線輸入。</span><span class="sxs-lookup"><span data-stu-id="e3f92-146">Used for pipeline input.</span></span> <span data-ttu-id="e3f92-147">管線輸入僅支援特定的純量類型和 `[system.io.fileinfo]` 用於輸送的實例 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="e3f92-147">Pipeline input supports only certain scalar types and `[system.io.fileinfo]` instances for piping from `Get-ChildItem`.</span></span>

<span data-ttu-id="e3f92-148">支援的純量類型為：</span><span class="sxs-lookup"><span data-stu-id="e3f92-148">The supported scalar types are:</span></span>

- <span data-ttu-id="e3f92-149">`[string]`, `[char]`</span><span class="sxs-lookup"><span data-stu-id="e3f92-149">`[string]`, `[char]`</span></span>
- <span data-ttu-id="e3f92-150">`[byte]`, `[sbyte]`</span><span class="sxs-lookup"><span data-stu-id="e3f92-150">`[byte]`, `[sbyte]`</span></span>
- <span data-ttu-id="e3f92-151">`[int16]`, `[uint16]`, `[short]`, `[ushort]`</span><span class="sxs-lookup"><span data-stu-id="e3f92-151">`[int16]`, `[uint16]`, `[short]`, `[ushort]`</span></span>
- <span data-ttu-id="e3f92-152">`[int]`, `[uint]`, `[int32]`, `[uint32]`,</span><span class="sxs-lookup"><span data-stu-id="e3f92-152">`[int]`, `[uint]`, `[int32]`, `[uint32]`,</span></span>
- <span data-ttu-id="e3f92-153">`[long]`, `[ulong]`, `[int64]`, `[uint64]`</span><span class="sxs-lookup"><span data-stu-id="e3f92-153">`[long]`, `[ulong]`, `[int64]`, `[uint64]`</span></span>
- <span data-ttu-id="e3f92-154">`[single]`, `[float]`, `[double]`</span><span class="sxs-lookup"><span data-stu-id="e3f92-154">`[single]`, `[float]`, `[double]`</span></span>

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

### <span data-ttu-id="e3f92-155">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="e3f92-155">-LiteralPath</span></span>

<span data-ttu-id="e3f92-156">指定檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="e3f92-156">Specifies the complete path to a file.</span></span> <span data-ttu-id="e3f92-157">**LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="e3f92-157">The value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="e3f92-158">此參數不接受萬用字元。</span><span class="sxs-lookup"><span data-stu-id="e3f92-158">This parameter does not accept wildcard characters.</span></span> <span data-ttu-id="e3f92-159">若要指定多個檔案路徑，請使用逗號分隔路徑。</span><span class="sxs-lookup"><span data-stu-id="e3f92-159">To specify multiple paths to files, separate the paths with a comma.</span></span> <span data-ttu-id="e3f92-160">如果 **LiteralPath** 參數包含 escape 字元，請用單引號括住路徑。</span><span class="sxs-lookup"><span data-stu-id="e3f92-160">If the **LiteralPath** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="e3f92-161">PowerShell 不會將單引號字串中的任何字元視為 escape 序列來解讀。</span><span class="sxs-lookup"><span data-stu-id="e3f92-161">PowerShell does not interpret any characters in a single quoted string as escape sequences.</span></span> <span data-ttu-id="e3f92-162">如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="e3f92-162">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="e3f92-163">-Path</span><span class="sxs-lookup"><span data-stu-id="e3f92-163">-Path</span></span>

<span data-ttu-id="e3f92-164">指定檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="e3f92-164">Specifies the path to files.</span></span> <span data-ttu-id="e3f92-165">使用點 (`.`) 來指定目前的位置。</span><span class="sxs-lookup"><span data-stu-id="e3f92-165">Use a dot (`.`) to specify the current location.</span></span> <span data-ttu-id="e3f92-166">接受萬用字元 (`*`) ，而且可以用來指定位置中的所有專案。</span><span class="sxs-lookup"><span data-stu-id="e3f92-166">The wildcard character (`*`) is accepted and can be used to specify all the items in a location.</span></span> <span data-ttu-id="e3f92-167">如果 **path** 參數包含 escape 字元，請用單引號括住路徑。</span><span class="sxs-lookup"><span data-stu-id="e3f92-167">If the **Path** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="e3f92-168">若要指定多個檔案路徑，請使用逗號分隔路徑。</span><span class="sxs-lookup"><span data-stu-id="e3f92-168">To specify multiple paths to files, separate the paths with a comma.</span></span>

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

### <span data-ttu-id="e3f92-169">-Raw</span><span class="sxs-lookup"><span data-stu-id="e3f92-169">-Raw</span></span>

<span data-ttu-id="e3f92-170">此參數不會再執行任何作業。</span><span class="sxs-lookup"><span data-stu-id="e3f92-170">This parameter no longer does anything.</span></span> <span data-ttu-id="e3f92-171">它是為了腳本相容性而保留。</span><span class="sxs-lookup"><span data-stu-id="e3f92-171">It is retained for script compatibility.</span></span>

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

### <span data-ttu-id="e3f92-172">-位移</span><span class="sxs-lookup"><span data-stu-id="e3f92-172">-Offset</span></span>

<span data-ttu-id="e3f92-173">這代表要略過的位元組數目是十六進位輸出的一部分。</span><span class="sxs-lookup"><span data-stu-id="e3f92-173">This represents the number of bytes to skip from being part of the hex output.</span></span>

<span data-ttu-id="e3f92-174">此參數是在 PowerShell 6.2 中引進。</span><span class="sxs-lookup"><span data-stu-id="e3f92-174">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="e3f92-175">-Count</span><span class="sxs-lookup"><span data-stu-id="e3f92-175">-Count</span></span>

<span data-ttu-id="e3f92-176">這代表要包含在十六進位輸出中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="e3f92-176">This represents the number of bytes to include in the hex output.</span></span>

<span data-ttu-id="e3f92-177">此參數是在 PowerShell 6.2 中引進。</span><span class="sxs-lookup"><span data-stu-id="e3f92-177">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="e3f92-178">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e3f92-178">CommonParameters</span></span>

<span data-ttu-id="e3f92-179">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="e3f92-179">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e3f92-180">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="e3f92-180">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e3f92-181">輸入</span><span class="sxs-lookup"><span data-stu-id="e3f92-181">INPUTS</span></span>

### <span data-ttu-id="e3f92-182">System.String</span><span class="sxs-lookup"><span data-stu-id="e3f92-182">System.String</span></span>

<span data-ttu-id="e3f92-183">您可以使用管線傳送字串至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e3f92-183">You can pipe a string to this cmdlet.</span></span>

## <span data-ttu-id="e3f92-184">輸出</span><span class="sxs-lookup"><span data-stu-id="e3f92-184">OUTPUTS</span></span>

### <span data-ttu-id="e3f92-185">Microsoft.PowerShell.Commands.ByteCollection</span><span class="sxs-lookup"><span data-stu-id="e3f92-185">Microsoft.PowerShell.Commands.ByteCollection</span></span>

<span data-ttu-id="e3f92-186">此 Cmdlet 會傳回 **ByteCollection** 。</span><span class="sxs-lookup"><span data-stu-id="e3f92-186">This cmdlet returns a **ByteCollection** .</span></span> <span data-ttu-id="e3f92-187">此物件表示位元組的集合。</span><span class="sxs-lookup"><span data-stu-id="e3f92-187">This object represents a collection of bytes.</span></span> <span data-ttu-id="e3f92-188">它包含將位元組集合轉換成字串格式的方法，例如所傳回的每一行輸出 `Format-Hex` 。</span><span class="sxs-lookup"><span data-stu-id="e3f92-188">It includes methods that convert the collection of bytes to a string formatted like each line of output returned by `Format-Hex`.</span></span> <span data-ttu-id="e3f92-189">如果您指定 **Path** 或 **LiteralPath** 參數，此物件也會包含其中含有每個位元組的檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="e3f92-189">If you specify the **Path** or **LiteralPath** parameter, the object also contains the path of the file that contains each byte.</span></span>

## <span data-ttu-id="e3f92-190">注意</span><span class="sxs-lookup"><span data-stu-id="e3f92-190">NOTES</span></span>

<span data-ttu-id="e3f92-191">最右邊的輸出資料行嘗試將位元組轉譯為 ASCII 字元：</span><span class="sxs-lookup"><span data-stu-id="e3f92-191">The right-most column of output tries to render the bytes as ASCII characters:</span></span>

<span data-ttu-id="e3f92-192">一般而言，每個位元組都會轉譯為 Unicode 程式碼點，這表示：</span><span class="sxs-lookup"><span data-stu-id="e3f92-192">Generally, each byte is interpreted as a Unicode code point, which means that:</span></span>

- <span data-ttu-id="e3f92-193">可列印的 ASCII 字元一律會正確轉譯</span><span class="sxs-lookup"><span data-stu-id="e3f92-193">Printable ASCII characters are always rendered correctly</span></span>
- <span data-ttu-id="e3f92-194">多位元組 UTF-8 字元絕對不會正確呈現</span><span class="sxs-lookup"><span data-stu-id="e3f92-194">Multi-byte UTF-8 characters never render correctly</span></span>
- <span data-ttu-id="e3f92-195">UTF-16 字元會在其高序位位元組發生時正確轉譯 `NUL` 。</span><span class="sxs-lookup"><span data-stu-id="e3f92-195">UTF-16 characters render correctly only if their high-order byte happens be `NUL`.</span></span>

## <span data-ttu-id="e3f92-196">相關連結</span><span class="sxs-lookup"><span data-stu-id="e3f92-196">RELATED LINKS</span></span>

[<span data-ttu-id="e3f92-197">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="e3f92-197">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="e3f92-198">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="e3f92-198">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="e3f92-199">Format-List</span><span class="sxs-lookup"><span data-stu-id="e3f92-199">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="e3f92-200">Format-Table</span><span class="sxs-lookup"><span data-stu-id="e3f92-200">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="e3f92-201">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="e3f92-201">Format-Wide</span></span>](Format-Wide.md)
