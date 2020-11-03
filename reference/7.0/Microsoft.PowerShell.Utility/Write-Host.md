---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-host?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Host
ms.openlocfilehash: d6707a9f5c54b736d0b917d453416ccdb0850baa
ms.sourcegitcommit: 758e6dbb428295698d4852b3e19f5d03deade037
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "93206259"
---
# Write-Host

## 概要

將自訂輸出寫入主機。

## SYNTAX

```
Write-Host [[-Object] <Object>] [-NoNewline] [-Separator <Object>] [-ForegroundColor <ConsoleColor>]
 [-BackgroundColor <ConsoleColor>] [<CommonParameters>]
```

## DESCRIPTION

指令程式的 `Write-Host` 主要目的是要產生 (的主機) 僅顯示輸出，例如列印彩色文字（例如，在提示使用者輸入與 [讀取主](Read-Host.md)控制項的輸入時）。
`Write-Host` 使用 [ToString ( # B1 ](/dotnet/api/system.object.tostring) 方法寫入輸出。 相反地，若要將資料輸出到管線，請使用 [寫入輸出](Write-Output.md) 或隱含輸出。

您可以使用參數來指定文字的色彩 `ForegroundColor` ，而且可以使用參數指定背景色彩 `BackgroundColor` 。 Separator 參數可讓您指定用來區隔顯示之物件的字串。 特定的結果取決於裝載 PowerShell 的程式。

> [!NOTE]
> 從 Windows PowerShell 5.0 開始，是的包裝函式，可 `Write-Host` `Write-Information` 讓您用 `Write-Host` 來發出輸出至資訊串流。 這可讓您 **捕捉** 或 **隱藏** 使用撰寫的資料， `Write-Host` 同時保留回溯相容性。
>
> `$InformationPreference`喜好設定變數和 `InformationAction` 一般參數不會影響 `Write-Host` 訊息。 這項規則的例外狀況是 `-InformationAction Ignore` 有效地隱藏 `Write-Host` 輸出。  (請參閱「範例5」 ) 

## 範例

### 範例1：寫入主控台而不新增一行

```powershell
Write-Host "no newline test " -NoNewline
Write-Host "second string"
```

```output
no newline test second string
```

此命令會以參數顯示「沒有分行符號測試」字串 `NoNewline` 。

寫入第二個字串，但它最後會在與第一個字串相同的行上，因為沒有任何分行符號分隔字串。

### 範例2：寫入主控台並包含分隔符號

```powershell
Write-Host (2,4,6,8,10,12) -Separator ", +2= "
```

```output
2, +2= 4, +2= 6, +2= 8, +2= 10, +2= 12
```

此命令會顯示從2到12的偶數數位。 **分隔符號** 參數是用來將字串新增 `, +2= ` (逗號、空格、、 `+` 、 `2` `=` 、space) 。

### 範例3：使用不同的文字和背景色彩進行寫入

```powershell
Write-Host (2,4,6,8,10,12) -Separator ", -> " -ForegroundColor DarkGreen -BackgroundColor White
```

```output
2, -> 4, -> 6, -> 8, -> 10, -> 12
```

此命令會顯示從2到12的偶數數位。 它會使用 `ForegroundColor` 參數來輸出深綠色文字，並使用 `BackgroundColor` 參數來顯示白色背景。

### 範例4：使用不同的文字和背景色彩進行寫入

```powershell
Write-Host "Red on white text." -ForegroundColor red -BackgroundColor white
```

```output
Red on white text.
```

此命令會顯示 "Red on white text" 字串。 文字是紅色，如參數所定義 `ForegroundColor` 。 背景是白色，如參數所定義 `BackgroundColor` 。

### 範例5：抑制 Write-Host 的輸出

```powershell
# The following two statements can be used to effectively suppress output from Write-Host
Write-Host "I won't print" -InformationAction Ignore
Write-Host "I won't print" 6>$null
```

```output

```

這些命令會有效地隱藏 Cmdlet 的輸出 `Write-Host` 。 第一個會使用 `InformationAction` 參數搭配 `Ignore` 值來抑制資訊資料流程的輸出。
第二個範例會將命令的資訊資料流程重新導向至變數，藉此將 `$null` 它隱藏。

## PARAMETERS

### -BackgroundColor

指定背景色彩。 沒有預設值。 此參數可接受的值為：

- 黑色
- 1：深藍色
- 2：深綠色
- 3：深青綠色
- 4：深紅色
- 5：深洋紅色
- 6：深黃色
- 灰色
- 8：深灰色
- 藍色
- 綠色
- 11：青色
- 紅色
- 桃紅色
- 黃色
- 白色

```yaml
Type: System.ConsoleColor
Parameter Sets: (All)
Aliases:
Accepted values: Black, DarkBlue, DarkGreen, DarkCyan, DarkRed, DarkMagenta, DarkYellow, Gray, DarkGray, Blue, Green, Cyan, Red, Magenta, Yellow, White

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ForegroundColor

指定文字色彩。 沒有預設值。 此參數可接受的值為：

- 黑色
- 1：深藍色
- 2：深綠色
- 3：深青綠色
- 4：深紅色
- 5：深洋紅色
- 6：深黃色
- 灰色
- 8：深灰色
- 藍色
- 綠色
- 11：青色
- 紅色
- 桃紅色
- 黃色
- 白色

```yaml
Type: System.ConsoleColor
Parameter Sets: (All)
Aliases:
Accepted values: Black, DarkBlue, DarkGreen, DarkCyan, DarkRed, DarkMagenta, DarkYellow, Gray, DarkGray, Blue, Green, Cyan, Red, Magenta, Yellow, White

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoNewline

輸入物件的字串表示會串連以形成輸出。 輸出字串之間不會插入空格或分行符號。 最後一個輸出字串之後不會加入任何新行。

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

### -Object

要顯示在主機中的物件。

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases: Msg, Message

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Separator

指定要在主機所顯示的物件之間插入的分隔字串。

```yaml
Type: System.Object
Parameter Sets: (All)
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

### System.Object

您可以使用管線來傳送要寫入主機的物件。

## 輸出

### 無

`Write-Host` 將物件傳送至主機。 它不會傳回任何物件。 但是，主機會顯示傳送 `Write-Host` 給它的物件。

## 注意

- 將集合寫入至主機時，集合的元素會列印在以單一空格分隔的同一行上。 這可以使用 **分隔符號** 參數加以覆寫。

- 非基本資料類型（例如具有屬性的物件）可能會導致非預期的結果，而不會提供有意義的輸出。 例如， `Write-Host @{a = 1; b = 2}` 會列印 `System.Collections.DictionaryEntry System.Collections.DictionaryEntry` 到主機。

## 相關連結

[Clear-Host](../Microsoft.PowerShell.Core/Clear-Host.md)

[Out-Host](../Microsoft.PowerShell.Core/Out-Host.md)

[Write-Debug](Write-Debug.md)

[Write-Error](Write-Error.md)

[Write-Output](Write-Output.md)

[Write-Progress](Write-Progress.md)

[Write-Verbose](Write-Verbose.md)

[Write-Warning](Write-Warning.md)
