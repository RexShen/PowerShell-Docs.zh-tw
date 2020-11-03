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
# Format-Hex

## 概要

以十六進位格式顯示檔案或其他輸入。

## SYNTAX

### 路徑 (預設值)

```
Format-Hex [-Path] <string[]> [-Count <long>] [-Offset <long>] [<CommonParameters>]
```

### LiteralPath

```
Format-Hex -LiteralPath <string[]> [-Count <long>] [-Offset <long>] [<CommonParameters>]
```

### InputObject

```
Format-Hex -InputObject <psobject> [-Encoding <Encoding>] [-Count <long>] [-Offset <long>] [-Raw] [<CommonParameters>]
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

若要測試下列命令，請在本機電腦上複製現有的 PDF 檔案，然後將複製的檔案重新命名為 `File.t7f` 。

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

此 `Format-Hex` Cmdlet 會使用 **Path** 參數來指定當前目錄中的檔案名 **t7f** 。 **T7f** 並不常見，但十六進位輸出 **% pdf** 顯示其為 PDF 檔案。

## PARAMETERS

### -Encoding

指定輸出的編碼方式。 這僅適用于 `[string]` 輸入。 參數對數數值型別沒有任何作用。 預設值是 `utf8NoBOM`。

此參數可接受的值如下：

- `ascii`：使用 ASCII (7 位) 字元集的編碼方式。
- `bigendianunicode`：使用位元組由大到小的位元組順序，以 UTF-16 格式編碼。
- `oem`：針對 MS-DOS 和主控台程式使用預設編碼。
- `unicode`：使用位元組由大到小的位元組順序，以 UTF-16 格式編碼。
- `utf7`：以 UTF-7 格式編碼。
- `utf8`：以 UTF-8 格式編碼。
- `utf8BOM`：使用 (BOM) 的位元組順序標記來編碼 UTF-8 格式
- `utf8NoBOM`：以不含位元組順序標記的 UTF-8 格式來編碼 (BOM) 
- `utf32`：以 UTF-32 格式編碼。

從 PowerShell 6.2 開始， **編碼** 參數也會允許已註冊字碼頁的數值識別碼 (例如 `-Encoding 1251`) 或已註冊字碼頁的字串名稱 (例如 `-Encoding "windows-1251"`) 。 如需詳細資訊，請參閱 .NET 檔中的 [編碼字碼頁](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)。

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

### -InputObject

用於管線輸入。 管線輸入僅支援特定的純量類型和 `[system.io.fileinfo]` 用於輸送的實例 `Get-ChildItem` 。

支援的純量類型為：

- `[string]`, `[char]`
- `[byte]`, `[sbyte]`
- `[int16]`, `[uint16]`, `[short]`, `[ushort]`
- `[int]`, `[uint]`, `[int32]`, `[uint32]`,
- `[long]`, `[ulong]`, `[int64]`, `[uint64]`
- `[single]`, `[float]`, `[double]`

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

### -LiteralPath

指定檔案的完整路徑。 **LiteralPath** 的值將完全依照其輸入值來使用。
此參數不接受萬用字元。 若要指定多個檔案路徑，請使用逗號分隔路徑。 如果 **LiteralPath** 參數包含 escape 字元，請用單引號括住路徑。 PowerShell 不會將單引號字串中的任何字元視為 escape 序列來解讀。 如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。

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

此參數不會再執行任何作業。 它是為了腳本相容性而保留。

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

### -位移

這代表要略過的位元組數目是十六進位輸出的一部分。

此參數是在 PowerShell 6.2 中引進。

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

### -Count

這代表要包含在十六進位輸出中的位元組數目。

此參數是在 PowerShell 6.2 中引進。

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

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

您可以使用管線傳送字串至此 Cmdlet。

## 輸出

### Microsoft.PowerShell.Commands.ByteCollection

此 Cmdlet 會傳回 **ByteCollection** 。 此物件表示位元組的集合。 它包含將位元組集合轉換成字串格式的方法，例如所傳回的每一行輸出 `Format-Hex` 。 如果您指定 **Path** 或 **LiteralPath** 參數，此物件也會包含其中含有每個位元組的檔案的路徑。

## 注意

最右邊的輸出資料行嘗試將位元組轉譯為 ASCII 字元：

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
