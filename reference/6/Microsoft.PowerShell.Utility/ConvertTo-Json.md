---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-json?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Json
ms.openlocfilehash: 26c899b5560df566ec97eb4f81a6f7a4416932ca
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204699"
---
# ConvertTo-Json

## 概要
將物件轉換成 JSON 格式的字串。

## SYNTAX

```
ConvertTo-Json [-InputObject] <Object> [-Depth <Int32>] [-Compress]
[-EnumsAsStrings] [-AsArray] [-EscapeHandling <StringEscapeHandling>]
[<CommonParameters>]
```

## DESCRIPTION

`ConvertTo-Json`Cmdlet 會將任何 .net 物件轉換成 JavaScript 物件標記法 (JSON) 格式的字串。 屬性會轉換成欄位名稱、欄位值會轉換成屬性值，而方法會被移除。

然後，您可以使用指令 `ConvertFrom-Json` 程式，將 json 格式的字串轉換成 json 物件，在 PowerShell 中輕鬆地加以管理。

許多網站都使用 JSON 而不是 XML 來將資料序列化，以便在伺服器與 Web 應用程式之間進行通訊。

此 Cmdlet 是在 Windows PowerShell 3.0 中引進。

## 範例

### 範例 1

```powershell
(Get-UICulture).Calendar | ConvertTo-Json
```

```Output
{
  "MinSupportedDateTime": "0001-01-01T00:00:00",
  "MaxSupportedDateTime": "9999-12-31T23:59:59.9999999",
  "AlgorithmType": 1,
  "CalendarType": 1,
  "Eras": [
    1
  ],
  "TwoDigitYearMax": 2029,
  "IsReadOnly": true
}
```

此命令會使用 `ConvertTo-Json` Cmdlet 將 GregorianCalendar 物件轉換成 JSON 格式的字串。

### 範例 2

```powershell
Get-Date | ConvertTo-Json; Get-Date | ConvertTo-Json -AsArray
```

```Output
{
  "value": "2018-10-12T23:07:18.8450248-05:00",
  "DisplayHint": 2,
  "DateTime": "October 12, 2018 11:07:18 PM"
}
[
  {
    "value": "2018-10-12T23:07:18.8480668-05:00",
    "DisplayHint": 2,
    "DateTime": "October 12, 2018 11:07:18 PM"
  }
]
```

此範例會顯示 Cmdlet 的輸出， `ConvertTo-Json` 以及不含 **AsArray** 交換器參數的和。 您可以看到輸出的第二個部分是以陣列括弧括住。

### 範例 3

```powershell
@{Account="User01";Domain="Domain01";Admin="True"} | ConvertTo-Json -Compress
```

```Output
{"Domain":"Domain01","Account":"User01","Admin":"True"}
```

此命令會顯示使用 **壓縮** 參數的效果 `ConvertTo-Json` 。 壓縮只會影響字串的外觀，不會影響其有效性。

### 範例 4

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json
```

```Output
{
  "DisplayHint": 2,
  "DateTime": "October 12, 2018 10:55:32 PM",
  "Date": "2018-10-12T00:00:00-05:00",
  "Day": 12,
  "DayOfWeek": 5,
  "DayOfYear": 285,
  "Hour": 22,
  "Kind": 2,
  "Millisecond": 639,
  "Minute": 55,
  "Month": 10,
  "Second": 32,
  "Ticks": 636749817326397744,
  "TimeOfDay": {
    "Ticks": 825326397744,
    "Days": 0,
    "Hours": 22,
    "Milliseconds": 639,
    "Minutes": 55,
    "Seconds": 32,
    "TotalDays": 0.95523888627777775,
    "TotalHours": 22.925733270666665,
    "TotalMilliseconds": 82532639.774400011,
    "TotalMinutes": 1375.54399624,
    "TotalSeconds": 82532.6397744
  },
  "Year": 2018
}
```

此範例會使用 `ConvertTo-Json` Cmdlet 將 system.string 物件 **System.DateTime** 從 CMDLET 轉換成 `Get-Date` JSON 格式的字串。 此命令會使用 `Select-Object` Cmdlet 取得 `*` **DateTime** 物件的所有屬性 () 。 輸出會顯示傳回的 JSON 字串 `ConvertTo-Json` 。

### 範例 5

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json | ConvertFrom-Json
```

```Output
DisplayHint : 2
DateTime    : October 12, 2018 10:55:52 PM
Date        : 2018-10-12 12:00:00 AM
Day         : 12
DayOfWeek   : 5
DayOfYear   : 285
Hour        : 22
Kind        : 2
Millisecond : 768
Minute      : 55
Month       : 10
Second      : 52
Ticks       : 636749817527683372
TimeOfDay   : @{Ticks=825527683372; Days=0; Hours=22; Milliseconds=768; Minutes=55; Seconds=52;
              TotalDays=0.95547185575463; TotalHours=22.9313245381111; TotalMilliseconds=82552768.3372;
              TotalMinutes=1375.87947228667; TotalSeconds=82552.7683372}
Year        : 2018
```

此範例示範如何使用 `ConvertTo-Json` 和 Cmdlet， `ConvertFrom-Json` 將物件轉換成 json 字串和 json 物件。

## PARAMETERS

### -AsArray

將物件輸出在陣列括弧中，即使輸入是單一物件也一樣。

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

### -Compress

省略輸出字串中的空白字元和縮排格式。

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

### -Depth

指定 JSON 表示法中包含多少層的內含物件。 預設值為 2。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 2
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnumsAsStrings

提供將所有列舉轉換為其字串表示的替代序列化選項。

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

### -EscapeHandling

控制在產生的 JSON 輸出中如何將某些字元轉義。 根據預設，只會將控制字元 (例如換行) 。

可接受的值如下：

- 僅限預設的控制字元會進行轉義。
- EscapeNonAscii-所有非 ASCII 字元和控制字元都會進行轉義。
- EscapeHtml-HTML (`<` 、 `>` 、 `&` 、 `'` 、 `"`) 和控制字元都經過轉義。

此參數是在 PowerShell 6.2 中引進。

```yaml
Type: Newtonsoft.Json.StringEscapeHandling
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定要轉換成 JSON 格式的物件。 輸入包含物件的變數，或輸入可取得物件的命令或運算式。 您也可以使用管線將物件傳送至 `ConvertTo-Json` 。

需要 **InputObject** 參數，但其值可以是 null (`$null`) 或空字串。
當輸入物件是時 `$null` ，不 `ConvertTo-Json` 會產生任何輸出。 當輸入物件為空字串時，會傳回 `ConvertTo-Json` 空字串。

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### System.Object

您可以透過管線將任何物件傳送至 `ConvertTo-Json` 。

## 輸出

### System.String

## 注意

此 `ConvertTo-Json` Cmdlet 會使用 [Newtonsoft Json.NET](https://www.newtonsoft.com/json)來執行。

## 相關連結

[JavaScript 和 .NET 中的 JavaScript 物件標記法 (JSON) 簡介](/previous-versions/dotnet/articles/bb299886(v=msdn.10))

[ConvertFrom-Json](ConvertFrom-Json.md)

[Get-Content](../Microsoft.PowerShell.Management/Get-Content.md)

[Get-UICulture](Get-UICulture.md)

[Invoke-WebRequest](Invoke-WebRequest.md)

[Invoke-RestMethod](Invoke-RestMethod.md)

[NewtonSoft.Js開啟。StringEscapeHandling](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_StringEscapeHandling.htm)
