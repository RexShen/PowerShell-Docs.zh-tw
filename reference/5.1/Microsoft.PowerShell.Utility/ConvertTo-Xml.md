---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-xml?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Xml
ms.openlocfilehash: e5bf7d5f0574b7e1503f229d2dee11f3bcaba43a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203331"
---
# ConvertTo-Xml

## 概要
建立物件的 XML 表示法。

## SYNTAX

```
ConvertTo-Xml [-Depth <Int32>] [-InputObject] <PSObject> [-NoTypeInformation] [-As <String>]
 [<CommonParameters>]
```

## DESCRIPTION

此 `ConvertTo-Xml` Cmdlet 會建立一或多個 .net 物件的 [XML](/dotnet/api/system.xml.xmldocument) 標記法。 若要使用此 Cmdlet，請使用管線將一或多個物件傳送至 Cmdlet，或使用 **InputObject** 參數來指定物件。

當您使用管線將多個物件傳送至 `ConvertTo-Xml` 或使用 **InputObject** 參數提交多個物件時，會傳回 `ConvertTo-Xml` 單一的記憶體中 XML 檔，其中包含所有物件的標記法。

[除了將](./Export-Clixml.md) `Export-Clixml` 產生的 XML 儲存在[通用語言基礎結構](https://www.ecma-international.org/publications/standards/Ecma-335.htm)中，此 Cmdlet 也會將產生的 XML 儲存 (CLI) XML 檔案，該檔案可以重新匯入為具有[Clixml](./Import-Clixml.md)的物件。 `ConvertTo-Xml` 傳回 XML 檔的記憶體中表示，讓您可以在 PowerShell 中繼續處理。 `ConvertTo-Xml` 沒有將物件轉換為 CLI XML 的選項。

## 範例

### 範例1：將日期轉換為 XML

```
PS C:\> Get-Date | ConvertTo-Xml
```

此命令會將 (日期 **時間** 物件) 的目前日期轉換為 XML。

### 範例2：將處理常式轉換為 XML

```
PS C:\> ConvertTo-Xml -As "Document" -InputObject (Get-Process) -Depth 3
```

這個命令會將代表電腦上所有處理程序的處理程序物件轉換為 XML 文件。 物件的深度擴充為三個層級。

## PARAMETERS

### -As

決定輸出格式。
此參數可接受的值為：

- 字串。
傳回單一字串。
- 資料流。
傳回字串陣列。
- 文件。
傳回已 **進行** 的物件。

預設值為 Document。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Stream, String, Document

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Depth

指定 XML 表示法中包含多少層的內含物件。 預設值為 1。

例如，如果物件的屬性也包含物件，為了儲存包含物件的屬性的 XML 表示法，您必須將深度指定為 2。

您可以在 Types.ps1xml 檔案中覆寫物件類型的預設值。 如需詳細資訊，請參閱 about_Types.ps1xml。

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

指定要轉換的物件。 輸入包含物件的變數，或輸入可取得物件的命令或運算式。 您也可以透過管線將物件傳送至 **CONVERTTO XML** 。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -NoTypeInformation

省略物件節點的 Type 屬性。

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

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Management.Automation.PSObject

您可以透過管線將任何物件傳送至 **CONVERTTO XML** 。

## 輸出

### System.string 或 System.Xml.Xml檔

*As* 參數的值會決定 **ConvertTo XML** 傳回的物件類型。

## 注意

## 相關連結

[ConvertTo-Csv](ConvertTo-Csv.md)

[ConvertTo-Html](ConvertTo-Html.md)

[Export-Clixml](Export-Clixml.md)

[Get-Date](Get-Date.md)

[Import-Clixml](Import-Clixml.md)
