---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/19/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/test-json?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Json
ms.openlocfilehash: 618e00d8db5eadfa8658203ef435a23cfea25be3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204388"
---
# Test-Json

## 概要
測試字串是否為有效的 JSON 檔

## SYNTAX

```
Test-Json [-Json] <string> [[-Schema] <string>] [<CommonParameters>]
```

## DESCRIPTION

此 `Test-Json` Cmdlet 會測試字串是否為有效的 JavaScript 物件標記法 (JSON) 檔，並且可以選擇性地根據提供的架構來驗證 json 檔。

然後，已驗證的字串可以與 Cmdlet 搭配使用 `ConvertFrom-Json` ，將 json 格式的字串轉換成 json 物件，此物件可在 PowerShell 中輕鬆管理，或傳送到存取 JSON 輸入的其他程式或 web 服務。

許多網站都使用 JSON 而不是 XML 來將資料序列化，以便在伺服器與 Web 應用程式之間進行通訊。

此 Cmdlet 是在 PowerShell 6.1 中引進

## 範例

### 範例1：測試物件是否為有效的 JSON

此範例會測試輸入字串是否為有效的 JSON 檔。

```powershell
"{'name': 'Ashley', 'age': 25}" | Test-Json
```

```Output
True
```

### 範例2：針對提供的架構測試物件

此範例會採用包含 JSON 架構的字串，並將它與輸入字串進行比較。

```powershell
$schema = @'
{
  "definitions": {},
  "$schema": "http://json-schema.org/draft-07/schema#",
  "$id": "http://example.com/root.json",
  "type": "object",
  "title": "The Root Schema",
  "required": [
    "name",
    "age"
  ],
  "properties": {
    "name": {
      "$id": "#/properties/name",
      "type": "string",
      "title": "The Name Schema",
      "default": "",
      "examples": [
        "Ashley"
      ],
      "pattern": "^(.*)$"
    },
    "age": {
      "$id": "#/properties/age",
      "type": "integer",
      "title": "The Age Schema",
      "default": 0,
      "examples": [
        25
      ]
    }
  }
}
'@
"{'name': 'Ashley', 'age': '25'}" | Test-Json -Schema $schema
```

```Output
Test-Json : IntegerExpected: #/age
At line:1 char:37
+ "{'name': 'Ashley', 'age': '25'}" | Test-Json -Schema $schema
+                                     ~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidData: (:) [Test-Json], Exception
+ FullyQualifiedErrorId : InvalidJsonAgainstSchema,Microsoft.PowerShell.Commands.TestJsonCommand
False
```

在此範例中，我們會收到錯誤，因為架構的 **存留期** 必須是整數，但我們所測試的 JSON 輸入會改為使用字串值。

如需詳細資訊，請參閱 [JSON 架構](https://json-schema.org/)。

## PARAMETERS

### -Json

指定要測試有效性的 JSON 字串。 輸入包含字串的變數，或輸入可取得字串的命令或運算式。 您也可以使用管線將字串傳送至 `Test-Json` 。

需要 **Json** 參數。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -架構

指定要對其驗證 JSON 輸入的架構。 如果通過，則 `Test-Json` 會驗證 Json 輸入是否符合 **架構** 參數所指定的規格，而且 `$True` 只有在輸入符合提供的架構時，才會傳回。

如需詳細資訊，請參閱 [JSON 架構](https://json-schema.org/)。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

您可以使用管線將 JSON 字串傳送至 `Test-Json` 。

## 輸出

### Boolean

## 注意

此 `Test-Json` Cmdlet 會使用 [NJsonSchema 類別](https://github.com/RSuter/NJsonSchema)來執行。

## 相關連結

[JavaScript 和 .NET 中的 JavaScript 物件標記法 (JSON) 簡介](/previous-versions/dotnet/articles/bb299886(v=msdn.10))

[其他 JSON 架構詳細資料](https://json-schema.org/)

[ConvertTo-Json](ConvertTo-Json.md)

[Invoke-WebRequest](Invoke-WebRequest.md)

[Invoke-RestMethod](Invoke-RestMethod.md)
