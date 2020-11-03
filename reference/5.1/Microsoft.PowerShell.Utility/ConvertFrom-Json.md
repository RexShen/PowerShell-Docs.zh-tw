---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-json?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Json
ms.openlocfilehash: f2159a2de3432aec14fb395b93ed476f349616a8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203359"
---
# ConvertFrom-Json

## 概要
將 JSON 格式的字串轉換成自訂物件。

## SYNTAX

```
ConvertFrom-Json [-InputObject] <String> [<CommonParameters>]
```

## DESCRIPTION

`ConvertFrom-Json`Cmdlet 會將 JavaScript 物件標記法 (json) 格式化的字串轉換成自訂 **PSCustomObject** 物件，該物件具有 json 字串中每個欄位的屬性。 JSON 一般由網站用於提供物件的文字表示方式。 JSON 標準不會禁止 **PSCustomObject** 禁止使用。 例如，如果 JSON 字串包含重複的索引鍵，則這個 Cmdlet 只會使用最後一個索引鍵。 請參閱下列其他範例。

若要從任何物件產生 JSON 字串，請使用 `ConvertTo-Json` Cmdlet。

此 Cmdlet 是在 PowerShell 3.0 中引進。

> [!NOTE]
> 此 Cmdlet 不支援具有批註的 JSON。

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

## PARAMETERS

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

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

您可以使用管線將 JSON 字串傳送至 `ConvertFrom-Json` 。

## 輸出

### PSCustomObject

## 注意

此 `ConvertFrom-Json` Cmdlet 會使用 [JavaScriptSerializer 類別](/dotnet/api/system.web.script.serialization.javascriptserializer)來執行。

## 相關連結

[JavaScript 和 .NET 中的 JavaScript 物件標記法 (JSON) 簡介](/previous-versions/dotnet/articles/bb299886(v=msdn.10))

[ConvertTo-Json](ConvertTo-Json.md)

[Invoke-WebRequest](Invoke-WebRequest.md)

[Invoke-RestMethod](Invoke-RestMethod.md)
