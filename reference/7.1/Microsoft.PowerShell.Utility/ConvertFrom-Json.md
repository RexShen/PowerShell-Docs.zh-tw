---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-json?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Json
ms.openlocfilehash: 062d29d033e0a84837a1593fb96df0c3a00dc392
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94389414"
---
# ConvertFrom-Json

## 概要
將 JSON 格式的字串轉換成自訂物件或雜湊表。

## SYNTAX

```
ConvertFrom-Json [-InputObject] <String> [-AsHashtable] [-Depth <Int32>] [-NoEnumerate] [<CommonParameters>]
```

## DESCRIPTION

`ConvertFrom-Json`Cmdlet 會將 JavaScript 物件標記法 (json) 格式化的字串轉換成自訂 **PSCustomObject** 物件，該物件具有 json 字串中每個欄位的屬性。 JSON 一般由網站用於提供物件的文字表示方式。 JSON 標準不會禁止 **PSCustomObject** 禁止使用。 例如，如果 JSON 字串包含重複的索引鍵，則這個 Cmdlet 只會使用最後一個索引鍵。 請參閱下列其他範例。

若要從任何物件產生 JSON 字串，請使用 `ConvertTo-Json` Cmdlet。

此 Cmdlet 是在 PowerShell 3.0 中引進。

> [!NOTE]
> 從 PowerShell 6 開始，此 Cmdlet 支援具有批註的 JSON。 接受的批註會以兩個正斜線開始 (`//`) 。 批註不會在資料中表示，而且可以在檔案中寫入，而不會損毀資料或擲回錯誤，如同在 PowerShell 5.1 中所做的一樣。

## 範例

### 範例1：將 DateTime 物件轉換成 JSON 物件

此命令會使用 `ConvertTo-Json` 和 `ConvertFrom-Json` Cmdlet，將 **DateTime** 物件從 Cmdlet 轉換成 `Get-Date` JSON 物件，再轉換為 **PSCustomObject** 。

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json | ConvertFrom-Json
```

```Output
DisplayHint : 2
DateTime    : Friday, January 13, 2012 8:06:31 PM
Date        : 1/13/2012 8:00:00 AM
Day         : 13
DayOfWeek   : 5
DayOfYear   : 13
Hour        : 20
Kind        : 2
Millisecond : 400
Minute      : 6
Month       : 1
Second      : 31
Ticks       : 634620819914009002
TimeOfDay   : @{Ticks=723914009002; Days=0; Hours=20; Milliseconds=400; Minutes=6; Seconds=31; TotalDays=0.83786343634490734; TotalHours=20.108722472277776; TotalMilliseconds=72391400.900200009; TotalMinutes=1206.5233483366667;TotalSeconds=72391.4009002}
Year        : 2012
```

此範例會使用 `Select-Object` Cmdlet 來取得 **DateTime** 物件的所有屬性。 它會使用 `ConvertTo-Json` Cmdlet 將 **DateTime** 物件轉換成格式化為 json 物件的字串，並使用 `ConvertFrom-Json` Cmdlet 將 JSON 格式的字串轉換成 **PSCustomObject** 物件。

### 範例2：從 web 服務取得 JSON 字串，並將其轉換為 PowerShell 物件

此命令會使用 `Invoke-WebRequest` Cmdlet 從 web 服務取得 json 字串，然後使用 `ConvertFrom-Json` CMDLET 將 json 內容轉換成可在 PowerShell 中管理的物件。

```powershell
# Ensures that Invoke-WebRequest uses TLS 1.2
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
$j = Invoke-WebRequest 'https://api.github.com/repos/PowerShell/PowerShell/issues' | ConvertFrom-Json
```

您也可以使用 `Invoke-RestMethod` Cmdlet，它會自動將 JSON 內容轉換成物件。

### 範例3：將 JSON 字串轉換為自訂物件

此範例說明如何使用 Cmdlet 將 `ConvertFrom-Json` JSON 檔案轉換成 PowerShell 自訂物件。

```powershell
Get-Content JsonFile.JSON | ConvertFrom-Json
```

命令會使用 Get-Content Cmdlet 來取得 JSON 檔案中的字串。 然後，它會使用管線運算子將分隔的字串傳送至 `ConvertFrom-Json` Cmdlet，以將它轉換成自訂物件。

### 範例4：將 JSON 字串轉換成雜湊表

此命令會顯示一個範例，其中的 `-AsHashtable` switch 可以克服命令的限制。

```powershell
'{ "key":"value1", "Key":"value2" }' | ConvertFrom-Json -AsHashtable
```

JSON 字串包含兩個索引鍵值組，其中的索引鍵只有大小寫不同。 如果沒有參數，命令就會擲回錯誤。

### 範例5：對單一元素陣列進行來回行程

此命令會顯示一個範例，其中 `-NoEnumerate` 會使用參數來反復存取單一元素的 JSON 陣列。

```powershell
Write-Output "With -NoEnumerate: $('[1]' | ConvertFrom-Json -NoEnumerate | ConvertTo-Json -Compress)"
Write-Output "Without -NoEnumerate: $('[1]' | ConvertFrom-Json | ConvertTo-Json -Compress)"
```

```Output
With -NoEnumerate: [1]
Without -NoEnumerate: 1
```

JSON 字串包含具有單一元素的陣列。 如果沒有參數，請將 JSON 轉換成 PSObject，然後使用命令將它轉換回一個 `ConvertTo-Json` 整數。

## PARAMETERS

### -AsHashtable

將 JSON 轉換成雜湊表物件。 此參數是在 PowerShell 6.0 中引進。 在幾個案例中，它可以克服 Cmdlet 的一些限制 `ConvertFrom-Json` 。

- 如果 JSON 包含的清單中，索引鍵的大小寫不同。 如果沒有參數，則會將這些機碼視為相同的索引鍵，因此只會使用最後一個金鑰。
- 如果 JSON 包含索引鍵，則為空字串。 如果沒有參數，Cmdlet 會擲回錯誤，因為不 `PSCustomObject` 允許，但雜湊表的確有此錯誤。 可能發生這種情況的範例使用案例為檔案 `project.lock.json` 。
- 雜湊表可針對特定資料結構更快速地處理。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Depth

取得或設定 JSON 輸入允許的最大深度。 預設為1024。

此參數是在 PowerShell 6.2 中引進。

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

### -InputObject

指定 JSON 字串以轉換成 JSON 物件。 輸入包含字串的變數，或輸入可取得字串的命令或運算式。 您也可以使用管線將字串傳送至 `ConvertFrom-Json` 。

**InputObject** 是必要參數，但其值可以是空字串。 當輸入物件為空字串時，不 `ConvertFrom-Json` 會產生任何輸出。 **InputObject** 值不能是 `$null` 。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -NoEnumerate

指定不列舉輸出。

設定這個參數會讓陣列以單一物件的形式傳送，而不是個別傳送每個元素。 這可保證 JSON 可以透過進行往返 `ConvertTo-Json` 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

您可以使用管線將 JSON 字串傳送至 `ConvertFrom-Json` 。

## 輸出

### PSCustomObject

### System.Collections.Hashtable

## 注意

此 Cmdlet 會使用 [Newtonsoft Json.NET](https://www.newtonsoft.com/json)來執行。

從 PowerShell 6 開始， `ConvertTo-Json` 會嘗試將格式化為時間戳記的字串轉換成 **DateTime** 值。 轉換的值是 `[datetime]` 具有屬性設定的實例，如下 `Kind` 所示：

- `Unspecified`如果輸入字串中沒有時區資訊，則為。
- `Utc`如果時區資訊是尾端的，則為 `Z` 。
- `Local`，如果將時區資訊指定為尾端的 UTC _時差_ （例如） `+02:00` 。 位移會正確地轉換為呼叫端的設定時區。 預設的輸出格式不表示原始時區位移。

## 相關連結

[JavaScript 和 .NET 中的 JavaScript 物件標記法 (JSON) 簡介](/previous-versions/dotnet/articles/bb299886(v=msdn.10))

[ConvertTo-Json](ConvertTo-Json.md)

[Invoke-WebRequest](Invoke-WebRequest.md)

[Invoke-RestMethod](Invoke-RestMethod.md)
