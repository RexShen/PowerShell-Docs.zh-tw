---
external help file: Microsoft.PowerShell.Utility-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/17/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-hex?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Hex
ms.openlocfilehash: 514a66ebee3827de998622a738c75d4f8e0c7279
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203300"
---
# <span data-ttu-id="65ac2-103">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="65ac2-103">Format-Hex</span></span>

## <span data-ttu-id="65ac2-104">概要</span><span class="sxs-lookup"><span data-stu-id="65ac2-104">SYNOPSIS</span></span>

<span data-ttu-id="65ac2-105">以十六進位格式顯示檔案或其他輸入。</span><span class="sxs-lookup"><span data-stu-id="65ac2-105">Displays a file or other input as hexadecimal.</span></span>

## <span data-ttu-id="65ac2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="65ac2-106">SYNTAX</span></span>

### <span data-ttu-id="65ac2-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="65ac2-107">Path (Default)</span></span>

```
Format-Hex [-Path] <string[]> [<CommonParameters>]
```

### <span data-ttu-id="65ac2-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="65ac2-108">LiteralPath</span></span>

```
Format-Hex -LiteralPath <string[]> [<CommonParameters>]
```

### <span data-ttu-id="65ac2-109">ByInputObject</span><span class="sxs-lookup"><span data-stu-id="65ac2-109">ByInputObject</span></span>

```
Format-Hex -InputObject <Object> [-Encoding <string>] [-Raw] [<CommonParameters>]
```

## <span data-ttu-id="65ac2-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="65ac2-110">DESCRIPTION</span></span>

<span data-ttu-id="65ac2-111">`Format-Hex`Cmdlet 會以十六進位值顯示檔案或其他輸入。</span><span class="sxs-lookup"><span data-stu-id="65ac2-111">The `Format-Hex` cmdlet displays a file or other input as hexadecimal values.</span></span> <span data-ttu-id="65ac2-112">若要判斷輸出中的字元位移，請將資料列最左邊的數字加到該字元的資料欄上方的數字。</span><span class="sxs-lookup"><span data-stu-id="65ac2-112">To determine the offset of a character from the output, add the number at the leftmost of the row to the number at the top of the column for that character.</span></span>

<span data-ttu-id="65ac2-113">此 `Format-Hex` Cmdlet 可協助您判斷損毀檔案的檔案類型，或可能沒有副檔名的檔案。</span><span class="sxs-lookup"><span data-stu-id="65ac2-113">The `Format-Hex` cmdlet can help you determine the file type of a corrupted file or a file that might not have a filename extension.</span></span> <span data-ttu-id="65ac2-114">您可以執行此 Cmdlet，然後讀取十六進位輸出以取得檔案資訊。</span><span class="sxs-lookup"><span data-stu-id="65ac2-114">You can run this cmdlet, and then read the hexadecimal output to get file information.</span></span>

<span data-ttu-id="65ac2-115">在檔案 `Format-Hex` 上使用時，此 Cmdlet 會忽略分行符號，並以保留分行符號的一個字串傳回檔案的整個內容。</span><span class="sxs-lookup"><span data-stu-id="65ac2-115">When using `Format-Hex` on a file, the cmdlet ignores newline characters and returns the entire contents of a file in one string with the newline characters preserved.</span></span>

## <span data-ttu-id="65ac2-116">範例</span><span class="sxs-lookup"><span data-stu-id="65ac2-116">EXAMPLES</span></span>

### <span data-ttu-id="65ac2-117">範例 1︰取得字串的十六進位表示法</span><span class="sxs-lookup"><span data-stu-id="65ac2-117">Example 1: Get the hexadecimal representation of a string</span></span>

<span data-ttu-id="65ac2-118">此命令會傳回字串的十六進位值。</span><span class="sxs-lookup"><span data-stu-id="65ac2-118">This command returns the hexadecimal values of a string.</span></span>

```powershell
'Hello World' | Format-Hex
```

```Output
           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   48 65 6C 6C 6F 20 57 6F 72 6C 64                 Hello World
```

<span data-ttu-id="65ac2-119">**Hello World** 的字串會沿著管線向下傳送至 `Format-Hex` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="65ac2-119">The string **Hello World** is sent down the pipeline to the `Format-Hex` cmdlet.</span></span> <span data-ttu-id="65ac2-120">的十六進位輸出會 `Format-Hex` 顯示字串中每個字元的值。</span><span class="sxs-lookup"><span data-stu-id="65ac2-120">The hexadecimal output from `Format-Hex` shows the values of each character in the string.</span></span>

### <span data-ttu-id="65ac2-121">範例2：從十六進位輸出尋找檔案類型</span><span class="sxs-lookup"><span data-stu-id="65ac2-121">Example 2: Find a file type from hexadecimal output</span></span>

<span data-ttu-id="65ac2-122">這個範例會使用十六進位輸出來判斷檔案類型。</span><span class="sxs-lookup"><span data-stu-id="65ac2-122">This example uses the hexadecimal output to determine the file type.</span></span> <span data-ttu-id="65ac2-123">此 Cmdlet 會顯示檔案的完整路徑和十六進位值。</span><span class="sxs-lookup"><span data-stu-id="65ac2-123">The cmdlet displays the file's full path and the hexadecimal values.</span></span>

<span data-ttu-id="65ac2-124">若要測試下列命令，請在您的本機電腦上複製現有的 PDF 檔案，然後將複製的檔案重新命名為 **t7f** 。</span><span class="sxs-lookup"><span data-stu-id="65ac2-124">To test the following command, make a copy of an existing PDF file on your local computer and rename the copied file to **File.t7f** .</span></span>

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

<span data-ttu-id="65ac2-125">此 `Format-Hex` Cmdlet 會使用 **Path** 參數來指定當前目錄中的檔案名 `File.t7f` 。</span><span class="sxs-lookup"><span data-stu-id="65ac2-125">The `Format-Hex` cmdlet uses the **Path** parameter to specify a filename in the current directory, `File.t7f`.</span></span> <span data-ttu-id="65ac2-126">副檔名 `.t7f` 很罕見，但十六進位輸出 `%PDF` 顯示它是 PDF 檔案。</span><span class="sxs-lookup"><span data-stu-id="65ac2-126">The file extension `.t7f` is uncommon, but the hexadecimal output `%PDF` shows that it is a PDF file.</span></span>

### <span data-ttu-id="65ac2-127">範例3：顯示原始的十六進位輸出</span><span class="sxs-lookup"><span data-stu-id="65ac2-127">Example 3: Display raw hexadecimal output</span></span>

<span data-ttu-id="65ac2-128">依預設， `Format-Hex` 會選擇數值資料類型的 compact 輸出：如果值夠小，則會使用單一位元組或雙位元組序列。</span><span class="sxs-lookup"><span data-stu-id="65ac2-128">By default `Format-Hex` opts for compact output of numeric data types: single-byte or double-byte sequences are used if the value is small enough.</span></span> <span data-ttu-id="65ac2-129">**Raw** 參數會停用此行為。</span><span class="sxs-lookup"><span data-stu-id="65ac2-129">The **Raw** parameter deactivates this behavior.</span></span>

```
PS> 1,2,3,1000 | Format-Hex

           Path:

           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   01 02 03 E8 03                                   ...è.


PS> 1,2,3,1000 | Format-Hex -Raw

           Path:

           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   01 00 00 00 02 00 00 00 03 00 00 00 E8 03 00 00  ............è...
```

<span data-ttu-id="65ac2-130">請注意輸出中的差異。</span><span class="sxs-lookup"><span data-stu-id="65ac2-130">Notice the difference in output.</span></span> <span data-ttu-id="65ac2-131">**Raw** 參數會將數字顯示為4位元組值，並顯示為其 **Int32** 類型。</span><span class="sxs-lookup"><span data-stu-id="65ac2-131">The **Raw** parameter displays the numbers as 4-byte values, true to their **Int32** types.</span></span>

## <span data-ttu-id="65ac2-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="65ac2-132">PARAMETERS</span></span>

### <span data-ttu-id="65ac2-133">-Encoding</span><span class="sxs-lookup"><span data-stu-id="65ac2-133">-Encoding</span></span>

<span data-ttu-id="65ac2-134">指定輸出的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="65ac2-134">Specifies the encoding of the output.</span></span> <span data-ttu-id="65ac2-135">這僅適用于 `[string]` 輸入。</span><span class="sxs-lookup"><span data-stu-id="65ac2-135">This only applies to `[string]` input.</span></span> <span data-ttu-id="65ac2-136">參數對數數值型別沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="65ac2-136">The parameter has no effect on numeric types.</span></span> <span data-ttu-id="65ac2-137">預設值是 `ASCII`。</span><span class="sxs-lookup"><span data-stu-id="65ac2-137">The default value is `ASCII`.</span></span>

<span data-ttu-id="65ac2-138">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="65ac2-138">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="65ac2-139">`Ascii` 使用 ASCII (7 位) 字元集。</span><span class="sxs-lookup"><span data-stu-id="65ac2-139">`Ascii` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="65ac2-140">`BigEndianUnicode` 以位元組由大到小的順序使用 UTF-16。</span><span class="sxs-lookup"><span data-stu-id="65ac2-140">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="65ac2-141">`Unicode` 使用 UTF-16 和位元組由小到小的位元組順序。</span><span class="sxs-lookup"><span data-stu-id="65ac2-141">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="65ac2-142">`UTF7` 使用 UTF-7。</span><span class="sxs-lookup"><span data-stu-id="65ac2-142">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="65ac2-143">`UTF8` 使用 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="65ac2-143">`UTF8` Uses UTF-8.</span></span>
- <span data-ttu-id="65ac2-144">`UTF32` 以位元組由小到大的位元組順序使用 UTF-32。</span><span class="sxs-lookup"><span data-stu-id="65ac2-144">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>

<span data-ttu-id="65ac2-145">輸入中的非 ASCII 字元會輸出成常值 `?` 字元，而導致資訊遺失。</span><span class="sxs-lookup"><span data-stu-id="65ac2-145">Non-ASCII characters in the input are output as literal `?` characters resulting in a loss of information.</span></span>

```yaml
Type: System.String
Parameter Sets: ByInputObject
Aliases:
Accepted values: ASCII, BigEndianUnicode, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: ASCII
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="65ac2-146">-InputObject</span><span class="sxs-lookup"><span data-stu-id="65ac2-146">-InputObject</span></span>

<span data-ttu-id="65ac2-147">用於管線輸入。</span><span class="sxs-lookup"><span data-stu-id="65ac2-147">Used for pipeline input.</span></span> <span data-ttu-id="65ac2-148">管線輸入僅支援特定的純量類型和 `[system.io.fileinfo]` 用於輸送的實例 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="65ac2-148">Pipeline input supports only certain scalar types and `[system.io.fileinfo]` instances for piping from `Get-ChildItem`.</span></span>

<span data-ttu-id="65ac2-149">支援的純量類型為：</span><span class="sxs-lookup"><span data-stu-id="65ac2-149">The supported scalar types are:</span></span>

- `[string]`
- `[byte]`
- <span data-ttu-id="65ac2-150">`[int]`, `[int32]`</span><span class="sxs-lookup"><span data-stu-id="65ac2-150">`[int]`, `[int32]`</span></span>
- <span data-ttu-id="65ac2-151">`[long]`, `[int64]`</span><span class="sxs-lookup"><span data-stu-id="65ac2-151">`[long]`, `[int64]`</span></span>

```yaml
Type: System.Object
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="65ac2-152">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="65ac2-152">-LiteralPath</span></span>

<span data-ttu-id="65ac2-153">指定檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="65ac2-153">Specifies the complete path to a file.</span></span> <span data-ttu-id="65ac2-154">**LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="65ac2-154">The value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="65ac2-155">此參數不接受萬用字元。</span><span class="sxs-lookup"><span data-stu-id="65ac2-155">This parameter does not accept wildcard characters.</span></span> <span data-ttu-id="65ac2-156">若要指定多個檔案路徑，請使用逗號分隔路徑。</span><span class="sxs-lookup"><span data-stu-id="65ac2-156">To specify multiple paths to files, separate the paths with a comma.</span></span> <span data-ttu-id="65ac2-157">如果 **LiteralPath** 參數包含 escape 字元，請用單引號括住路徑。</span><span class="sxs-lookup"><span data-stu-id="65ac2-157">If the **LiteralPath** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="65ac2-158">PowerShell 不會將單引號字串中的任何字元視為 escape 序列來解讀。</span><span class="sxs-lookup"><span data-stu-id="65ac2-158">PowerShell does not interpret any characters in a single quoted string as escape sequences.</span></span> <span data-ttu-id="65ac2-159">如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="65ac2-159">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="65ac2-160">-Path</span><span class="sxs-lookup"><span data-stu-id="65ac2-160">-Path</span></span>

<span data-ttu-id="65ac2-161">指定檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="65ac2-161">Specifies the path to files.</span></span> <span data-ttu-id="65ac2-162">使用點 (`.`) 來指定目前的位置。</span><span class="sxs-lookup"><span data-stu-id="65ac2-162">Use a dot (`.`) to specify the current location.</span></span> <span data-ttu-id="65ac2-163">接受萬用字元 (`*`) ，而且可以用來指定位置中的所有專案。</span><span class="sxs-lookup"><span data-stu-id="65ac2-163">The wildcard character (`*`) is accepted and can be used to specify all the items in a location.</span></span> <span data-ttu-id="65ac2-164">如果 **path** 參數包含 escape 字元，請用單引號括住路徑。</span><span class="sxs-lookup"><span data-stu-id="65ac2-164">If the **Path** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="65ac2-165">若要指定多個檔案路徑，請使用逗號分隔路徑。</span><span class="sxs-lookup"><span data-stu-id="65ac2-165">To specify multiple paths to files, separate the paths with a comma.</span></span>

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

### <span data-ttu-id="65ac2-166">-Raw</span><span class="sxs-lookup"><span data-stu-id="65ac2-166">-Raw</span></span>

<span data-ttu-id="65ac2-167">依預設， `Format-Hex` 會選擇數值資料類型的 compact 輸出：如果值夠小，則會使用單一位元組或雙位元組序列。</span><span class="sxs-lookup"><span data-stu-id="65ac2-167">By default `Format-Hex` opts for compact output of numeric data types: single-byte or double-byte sequences are used if the value is small enough.</span></span> <span data-ttu-id="65ac2-168">**Raw** 參數會停用此行為。</span><span class="sxs-lookup"><span data-stu-id="65ac2-168">The **Raw** parameter deactivates this behavior.</span></span>

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

### <span data-ttu-id="65ac2-169">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="65ac2-169">CommonParameters</span></span>

<span data-ttu-id="65ac2-170">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="65ac2-170">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="65ac2-171">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="65ac2-171">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="65ac2-172">輸入</span><span class="sxs-lookup"><span data-stu-id="65ac2-172">INPUTS</span></span>

### <span data-ttu-id="65ac2-173">System.String</span><span class="sxs-lookup"><span data-stu-id="65ac2-173">System.String</span></span>

<span data-ttu-id="65ac2-174">您可以使用管線傳送字串至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="65ac2-174">You can pipe a string to this cmdlet.</span></span>

## <span data-ttu-id="65ac2-175">輸出</span><span class="sxs-lookup"><span data-stu-id="65ac2-175">OUTPUTS</span></span>

### <span data-ttu-id="65ac2-176">Microsoft.PowerShell.Commands.ByteCollection</span><span class="sxs-lookup"><span data-stu-id="65ac2-176">Microsoft.PowerShell.Commands.ByteCollection</span></span>

<span data-ttu-id="65ac2-177">此 Cmdlet 會傳回 **ByteCollection** 。</span><span class="sxs-lookup"><span data-stu-id="65ac2-177">This cmdlet returns a **ByteCollection** .</span></span> <span data-ttu-id="65ac2-178">此物件表示位元組的集合。</span><span class="sxs-lookup"><span data-stu-id="65ac2-178">This object represents a collection of bytes.</span></span> <span data-ttu-id="65ac2-179">它包含將位元組集合轉換成字串格式的方法，例如所傳回的每一行輸出 `Format-Hex` 。</span><span class="sxs-lookup"><span data-stu-id="65ac2-179">It includes methods that convert the collection of bytes to a string formatted like each line of output returned by `Format-Hex`.</span></span> <span data-ttu-id="65ac2-180">如果您指定 **Path** 或 **LiteralPath** 參數，此物件也會包含其中含有每個位元組的檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="65ac2-180">If you specify the **Path** or **LiteralPath** parameter, the object also contains the path of the file that contains each byte.</span></span>

## <span data-ttu-id="65ac2-181">注意</span><span class="sxs-lookup"><span data-stu-id="65ac2-181">NOTES</span></span>

<span data-ttu-id="65ac2-182">輸出的最右邊資料行嘗試將位元組轉譯為字元：</span><span class="sxs-lookup"><span data-stu-id="65ac2-182">The right-most column of output tries to render the bytes as characters:</span></span>

<span data-ttu-id="65ac2-183">一般而言，每個位元組都會轉譯為 Unicode 程式碼點，這表示：</span><span class="sxs-lookup"><span data-stu-id="65ac2-183">Generally, each byte is interpreted as a Unicode code point, which means that:</span></span>

- <span data-ttu-id="65ac2-184">可列印的 ASCII 字元一律會正確轉譯</span><span class="sxs-lookup"><span data-stu-id="65ac2-184">Printable ASCII characters are always rendered correctly</span></span>
- <span data-ttu-id="65ac2-185">多位元組 UTF-8 字元絕對不會正確呈現</span><span class="sxs-lookup"><span data-stu-id="65ac2-185">Multi-byte UTF-8 characters never render correctly</span></span>
- <span data-ttu-id="65ac2-186">UTF-16 字元會在其高序位位元組發生時正確轉譯 `NUL` 。</span><span class="sxs-lookup"><span data-stu-id="65ac2-186">UTF-16 characters render correctly only if their high-order byte happens be `NUL`.</span></span>

## <span data-ttu-id="65ac2-187">相關連結</span><span class="sxs-lookup"><span data-stu-id="65ac2-187">RELATED LINKS</span></span>

[<span data-ttu-id="65ac2-188">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="65ac2-188">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="65ac2-189">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="65ac2-189">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="65ac2-190">Format-List</span><span class="sxs-lookup"><span data-stu-id="65ac2-190">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="65ac2-191">Format-Table</span><span class="sxs-lookup"><span data-stu-id="65ac2-191">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="65ac2-192">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="65ac2-192">Format-Wide</span></span>](Format-Wide.md)
