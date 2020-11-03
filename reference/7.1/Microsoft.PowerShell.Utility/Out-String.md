---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/29/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-string?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-String
ms.openlocfilehash: 16dc25e3468eaf3126b3286cfd71bfea9627c015
ms.sourcegitcommit: c8d1ffeab215e74e87ea1b0af8cd606c1a6a80ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "93206351"
---
# Out-String

## 概要
以字串形式輸出輸入物件。

## SYNTAX

### NoNewLineFormatting (預設) 

```
Out-String [-Width <Int32>] [-NoNewline] [-InputObject <PSObject>] [<CommonParameters>]
```

### StreamFormatting

```
Out-String [-Stream] [-Width <Int32>] [-InputObject <PSObject>] [<CommonParameters>]
```

## DESCRIPTION

`Out-String`Cmdlet 會將輸入物件轉換成字串。 依預設， `Out-String` 會累積字串並將它們當作單一字串傳回，但您可以使用 **資料流程** 參數來指示 `Out-String` 一次傳回一行或建立字串陣列。 此 Cmdlet 可讓您搜尋和操作字串輸出，比在傳統殼層中的物件操作更便利。

## 範例

### 範例1：取得目前的文化特性，並將資料轉換成字串

這個範例會取得目前使用者的區域設定，並將物件資料轉換成字串。

```powershell
$C = Get-Culture | Select-Object -Property *
Out-String -InputObject $C -Width 100
```

```Output
Parent                         : en
LCID                           : 1033
KeyboardLayoutId               : 1033
Name                           : en-US
IetfLanguageTag                : en-US
DisplayName                    : English (United States)
NativeName                     : English (United States)
EnglishName                    : English (United States)
TwoLetterISOLanguageName       : en
ThreeLetterISOLanguageName     : eng
ThreeLetterWindowsLanguageName : ENU
CompareInfo                    : CompareInfo - en-US
TextInfo                       : TextInfo - en-US
IsNeutralCulture               : False
CultureTypes                   : SpecificCultures, InstalledWin32Cultures, FrameworkCultures
NumberFormat                   : System.Globalization.NumberFormatInfo
DateTimeFormat                 : System.Globalization.DateTimeFormatInfo
Calendar                       : System.Globalization.GregorianCalendar
OptionalCalendars              : {System.Globalization.GregorianCalendar,
                                 System.Globalization.GregorianCalendar}
UseUserOverride                : True
IsReadOnly                     : False
```

`$C`變數會儲存 **Selected.System。全球化 CultureInfo** 物件。 物件是將 `Get-Culture` 輸出向下傳送至的結果 `Select-Object` 。 **Property** 參數會使用星號 (`*`) 萬用字元來指定所有屬性都包含在物件中。

`Out-String` 使用 **InputObject** 參數來指定儲存在變數中的 **CultureInfo** 物件 `$C` 。 中的物件 `$C` 會轉換成字串。

> [!NOTE]
> 若要查看 `Out-String` 陣列，請將輸出儲存至變數，並使用陣列索引來查看元素。 如需陣列索引的詳細資訊，請參閱 [about_Arrays](../microsoft.powershell.core/about/about_arrays.md)。
>
> `$str = Out-String -InputObject $C -Width 100`

### 範例2：處理物件

此範例示範使用物件和使用字串之間的差異。 此命令會顯示包含文字 **gcm** （別名）的別名 `Get-Command` 。

```powershell
Get-Alias | Out-String -Stream | Select-String -Pattern "gcm"
```

```Output
Alias           gcm -> Get-Command
```

`Get-Alias` 取得 **system.management.automation.aliasinfo** 物件，每個別名各一個，並將物件沿著管線向下傳送。 `Out-String` 使用 **資料流程** 參數將每個物件轉換成字串，而不將所有物件串連成單一字串。 **System.string** 物件會向下傳送管線，並 `Select-String` 使用 **Pattern** 參數尋找文字 **gcm** 的相符專案。

> [!NOTE]
> 如果您省略 **資料流程** 參數，此命令會顯示所有別名，因為會 `Select-String` 在傳回的單一字串中尋找文字 **gcm** `Out-String` 。

### 範例3：使用 Width 參數以防止截斷。

雖然大部分的輸出 `Out-String` 都會包裝到下一行，但在某些情況下，格式化系統會在傳遞之前截斷輸出 `Out-String` 。 您可以使用 **Width** 參數避免截斷。

```powershell
PS> @{TestKey = ('x' * 200)} | Out-String
Name                           Value
----                           -----
TestKey                        xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx...

PS> @{TestKey = ('x' * 200)} | Out-String -Width 250

Name                           Value
----                           -----
TestKey                        xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## PARAMETERS

### -InputObject

指定要寫入字串的物件。 輸入包含物件的變數，或輸入可取得物件的命令或運算式。

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

### -NoNewline

從 PowerShell 格式器產生的輸出中移除所有分行符號。 包含在字串物件中的分行符號會保留下來。

此參數是在 PowerShell 6.0 中引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoNewLineFormatting
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Stream

指出此 Cmdlet 會為輸入物件的每一行傳送個別字串。 根據預設，每個物件的字串會累積，並會以單一字串形式傳送。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: StreamFormatting
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Width

指定每一行輸出的字元數目。 任何額外的字元都會包裝到下一行，或根據所使用的格式器 Cmdlet 來截斷。 **Width** 參數只適用于正在格式化的物件。 如果您省略這個參數，則寬度取決於主機程式的特性。 在終端機 (主控台) 視窗中，目前的視窗寬度會用來做為預設值。 PowerShell 主控台視窗在安裝時預設為80個字元的寬度。

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

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Management.Automation.PSObject

您可以將物件沿著管線向下傳送至 `Out-String` 。

## 輸出

### System.String

`Out-String` 傳回從輸入物件建立的字串。

## 注意

包含動詞的 Cmdlet 不會將 `Out` 物件格式化。 Cmdlet 會將 `Out` 物件傳送至指定的顯示目的地的格式器。

## 相關連結

[about_Formatting](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)

[Out-Default](../Microsoft.PowerShell.Core/Out-Default.md)

[Out-File](Out-File.md)

[Out-Host](../Microsoft.PowerShell.Core/Out-Host.md)

[Out-Null](../Microsoft.PowerShell.Core/Out-Null.md)

[Out-GridView](Out-GridView.md)

[Out-Printer](Out-Printer.md)

