---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 1/7/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-csv?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Csv
ms.openlocfilehash: 7d399661e4514c0a39ad00601d554c41c2897ff9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203355"
---
# ConvertTo-Csv

## 概要
將 .NET 物件轉換成一系列的逗號分隔值， (CSV) 字串。

## SYNTAX

### Delimiter (預設值)

```
ConvertTo-Csv [-InputObject] <psobject> [[-Delimiter] <char>] [-NoTypeInformation]
 [<CommonParameters>]
```

### UseCulture

```
ConvertTo-Csv [-InputObject] <psobject> [-UseCulture] [-NoTypeInformation] [<CommonParameters>]
```

## DESCRIPTION

`ConvertTo-CSV`Cmdlet 會傳回一系列以逗號分隔的值， (CSV) 字串，代表您提交的物件。 然後，您可以使用 `ConvertFrom-Csv` Cmdlet 從 CSV 字串重新建立物件。 從 CSV 轉換的物件是原始物件的字串值，這些物件包含屬性值且沒有任何方法。

您可以使用 `Export-Csv` Cmdlet，將物件轉換成 CSV 字串。 `Export-CSV` 類似于 `ConvertTo-CSV` ，不同之處在于它會將 CSV 字串儲存至檔案。

`ConvertTo-CSV`Cmdlet 有參數可指定逗號以外的分隔符號，或使用目前的文化特性做為分隔符號。

## 範例

### 範例1：將物件轉換為 CSV

這個範例會將 **處理** 程式物件轉換成 CSV 字串。

```powershell
Get-Process -Name 'PowerShell' | ConvertTo-Csv -NoTypeInformation
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Company","CPU","FileVersion", ...
"powershell","11","691","2204036739072","175943680","132665344","33312", ...
```

`Get-Process`Cmdlet 會取得 **處理** 程式物件，並使用 **Name** 參數來指定 PowerShell 處理常式。 進程物件會向下傳送至 `ConvertTo-CSV` Cmdlet。 `ConvertTo-CSV`Cmdlet 會將物件轉換成 CSV 字串。 **NoTypeInformation** 參數會從 CSV 輸出移除 **#TYPE** 資訊標頭。

### 範例2：將 DateTime 物件轉換成 CSV

這個範例會將 **DateTime** 物件轉換成 CSV 字串。

```powershell
$Date = Get-Date
ConvertTo-Csv -InputObject $Date -Delimiter ';' -NoTypeInformation
```

```Output
"DisplayHint";"DateTime";"Date";"Day";"DayOfWeek";"DayOfYear";"Hour";"Kind";"Millisecond";"Minute";"Month";"Second";"Ticks";"TimeOfDay";"Year"
"DateTime";"Friday, January 4, 2019 14:40:51";"1/4/2019 00:00:00";"4";"Friday";"4";"14";"Local";"711";"40";"1";"51";"636822096517114991";"14:40:51.7114991";"2019"
```

`Get-Date`Cmdlet 會取得 **DateTime** 物件，並將它儲存在 `$Date` 變數中。 `ConvertTo-Csv`Cmdlet 會將 **DateTime** 物件轉換成字串。 **InputObject** 參數會使用儲存在變數中的 **DateTime** 物件 `$Date` 。 **分隔符號** 參數會指定分號來分隔字串值。 **NoTypeInformation** 參數會從 CSV 輸出移除 **#TYPE** 資訊標頭。

### 範例3：將 PowerShell 事件記錄檔轉換成 CSV

此範例會將 PowerShell 的 Windows 事件記錄檔轉換成一系列 CSV 字串。

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-WinEvent -LogName 'Windows PowerShell' | ConvertTo-Csv -UseCulture -NoTypeInformation
```

```Output
,
"Message","Id","Version","Qualifiers","Level","Task","Opcode","Keywords","RecordId", ...
"Error Message = System error","403",,"0","4","4",,"36028797018963968","46891","PowerShell", ...
```

此 `Get-Culture` Cmdlet 會使用 **TextInfo** 和 **ListSeparator** 的 nested 屬性，並顯示目前文化特性的預設清單分隔符號。 `Get-WinEvent`Cmdlet 會取得事件記錄檔物件，並使用 **LogName** 參數來指定記錄檔名稱。 事件記錄檔物件會以管線傳送至 `ConvertTo-Csv` Cmdlet。 指令程式會 `ConvertTo-Csv` 將事件記錄檔物件轉換成一系列的 CSV 字串。 **UseCulture** 參數會使用目前文化特性的預設清單分隔符號做為分隔符號。 **NoTypeInformation** 參數會從 CSV 輸出移除 **#TYPE** 資訊標頭。

## PARAMETERS

### -Delimiter

指定分隔符號，以分隔 CSV 字串中的屬性值。 預設值是逗號 (`,`) 。 輸入字元，例如冒號 (`:`) 。 若要指定分號 (`;`) 將它括在單引號中。

```yaml
Type: System.Char
Parameter Sets: Delimiter
Aliases:

Required: False
Position: 1
Default value: comma (,)
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定轉換為 CSV 字串的物件。 輸入包含物件的變數，或輸入可取得物件的命令或運算式。 您也可以透過管線將物件傳送至 `ConvertTo-CSV` 。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -NoTypeInformation

從輸出中移除 **#TYPE** 資訊標頭。 此參數會成為 PowerShell 6.0 中的預設值，並包含以提供回溯相容性。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NTI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseCulture

使用目前文化特性的清單分隔字元做為專案分隔符號。 若要尋找文化特性的清單分隔符號，請使用下列命令： `(Get-Culture).TextInfo.ListSeparator` 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseCulture
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

您可以使用管線將具有擴充類型系統 (ETS) adapter 的任何物件傳送至 `ConvertTo-CSV` 。

## 輸出

### System.String

CSV 輸出會以字串集合的形式傳回。

## 注意

在 CSV 格式中，每個物件都會以其屬性值的逗號分隔清單表示。 屬性值會使用物件的 **ToString ( # B1** 方法轉換成字串。 字串會以屬性值名稱表示。 `ConvertTo-CSV` 不會匯出物件的方法。

CSV 字串的輸出如下所示：

- 依預設，第一個字串包含 **#TYPE** 資訊標頭，後面接著物件類型的完整名稱。 例如， **#TYPE 的系統診斷** 。
- 如果使用 **NoTypeInformation** ，則第一個字串會包含資料行標頭。 標頭包含第一個物件的屬性名稱，做為逗點分隔清單。
- 其餘的字串包含每個物件之屬性值的逗號分隔清單。

當您將多個物件提交至時 `ConvertTo-CSV` ，會 `ConvertTo-CSV` 根據您提交的第一個物件的屬性來排序字串。 如果其餘的物件沒有其中一個指定的屬性，則該物件的屬性值會是 Null，以兩個連續的逗號表示。 如果其餘的物件有其他屬性，則會忽略那些屬性值。

## 相關連結

[ConvertFrom-Csv](ConvertFrom-Csv.md)

[Export-Csv](Export-Csv.md)

[Import-Csv](Import-Csv.md)
