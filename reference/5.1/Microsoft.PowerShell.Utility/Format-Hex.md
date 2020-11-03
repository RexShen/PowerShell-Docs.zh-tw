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
# Format-Hex

## 概要

以十六進位格式顯示檔案或其他輸入。

## SYNTAX

### 路徑 (預設值)

```
Format-Hex [-Path] <string[]> [<CommonParameters>]
```

### LiteralPath

```
Format-Hex -LiteralPath <string[]> [<CommonParameters>]
```

### ByInputObject

```
Format-Hex -InputObject <Object> [-Encoding <string>] [-Raw] [<CommonParameters>]
```

## DESCRIPTION

`Format-Hex`Cmdlet 會以十六進位值顯示檔案或其他輸入。 若要判斷輸出中的字元位移，請將資料列最左邊的數字加到該字元的資料欄上方的數字。

此 `Format-Hex` Cmdlet 可協助您判斷損毀檔案的檔案類型，或可能沒有副檔名的檔案。 您可以執行此 Cmdlet，然後讀取十六進位輸出以取得檔案資訊。

在檔案 `Format-Hex` 上使用時，此 Cmdlet 會忽略分行符號，並以保留分行符號的一個字串傳回檔案的整個內容。

## 範例

### 範例 1︰取得字串的十六進位表示法

此命令會傳回字串的十六進位值。

```powershell
'Hello World' | Format-Hex
```

```Output
           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   48 65 6C 6C 6F 20 57 6F 72 6C 64                 Hello World
```

**Hello World** 的字串會沿著管線向下傳送至 `Format-Hex` Cmdlet。 的十六進位輸出會 `Format-Hex` 顯示字串中每個字元的值。

### 範例2：從十六進位輸出尋找檔案類型

這個範例會使用十六進位輸出來判斷檔案類型。 此 Cmdlet 會顯示檔案的完整路徑和十六進位值。

若要測試下列命令，請在您的本機電腦上複製現有的 PDF 檔案，然後將複製的檔案重新命名為 **t7f** 。

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

此 `Format-Hex` Cmdlet 會使用 **Path** 參數來指定當前目錄中的檔案名 `File.t7f` 。 副檔名 `.t7f` 很罕見，但十六進位輸出 `%PDF` 顯示它是 PDF 檔案。

### 範例3：顯示原始的十六進位輸出

依預設， `Format-Hex` 會選擇數值資料類型的 compact 輸出：如果值夠小，則會使用單一位元組或雙位元組序列。 **Raw** 參數會停用此行為。

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

請注意輸出中的差異。 **Raw** 參數會將數字顯示為4位元組值，並顯示為其 **Int32** 類型。

## PARAMETERS

### -Encoding

指定輸出的編碼方式。 這僅適用于 `[string]` 輸入。 參數對數數值型別沒有任何作用。 預設值是 `ASCII`。

此參數可接受的值如下：

- `Ascii` 使用 ASCII (7 位) 字元集。
- `BigEndianUnicode` 以位元組由大到小的順序使用 UTF-16。
- `Unicode` 使用 UTF-16 和位元組由小到小的位元組順序。
- `UTF7` 使用 UTF-7。
- `UTF8` 使用 UTF-8。
- `UTF32` 以位元組由小到大的位元組順序使用 UTF-32。

輸入中的非 ASCII 字元會輸出成常值 `?` 字元，而導致資訊遺失。

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

### -InputObject

用於管線輸入。 管線輸入僅支援特定的純量類型和 `[system.io.fileinfo]` 用於輸送的實例 `Get-ChildItem` 。

支援的純量類型為：

- `[string]`
- `[byte]`
- `[int]`, `[int32]`
- `[long]`, `[int64]`

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

### -LiteralPath

指定檔案的完整路徑。 **LiteralPath** 的值將完全依照其輸入值來使用。
此參數不接受萬用字元。 若要指定多個檔案路徑，請使用逗號分隔路徑。 如果 **LiteralPath** 參數包含 escape 字元，請用單引號括住路徑。 PowerShell 不會將單引號字串中的任何字元視為 escape 序列來解讀。 如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。

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

### -Path

指定檔案的路徑。 使用點 (`.`) 來指定目前的位置。 接受萬用字元 (`*`) ，而且可以用來指定位置中的所有專案。 如果 **path** 參數包含 escape 字元，請用單引號括住路徑。 若要指定多個檔案路徑，請使用逗號分隔路徑。

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

### -Raw

依預設， `Format-Hex` 會選擇數值資料類型的 compact 輸出：如果值夠小，則會使用單一位元組或雙位元組序列。 **Raw** 參數會停用此行為。

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

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

您可以使用管線傳送字串至此 Cmdlet。

## 輸出

### Microsoft.PowerShell.Commands.ByteCollection

此 Cmdlet 會傳回 **ByteCollection** 。 此物件表示位元組的集合。 它包含將位元組集合轉換成字串格式的方法，例如所傳回的每一行輸出 `Format-Hex` 。 如果您指定 **Path** 或 **LiteralPath** 參數，此物件也會包含其中含有每個位元組的檔案的路徑。

## 注意

輸出的最右邊資料行嘗試將位元組轉譯為字元：

一般而言，每個位元組都會轉譯為 Unicode 程式碼點，這表示：

- 可列印的 ASCII 字元一律會正確轉譯
- 多位元組 UTF-8 字元絕對不會正確呈現
- UTF-16 字元會在其高序位位元組發生時正確轉譯 `NUL` 。

## 相關連結

[about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[Format-Custom](Format-Custom.md)

[Format-List](Format-List.md)

[Format-Table](Format-Table.md)

[Format-Wide](Format-Wide.md)
