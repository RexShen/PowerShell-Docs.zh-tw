---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/show-markdown?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-Markdown
ms.openlocfilehash: f4740bca33bd70d4d8eca51ed45ba6204b5d2acb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202171"
---
# Show-Markdown

## 概要
使用 VT100 escape 序列或在瀏覽器中使用 HTML，以易記的方式顯示主控台中的 Markdown 檔案或字串。

## SYNTAX

### 路徑 (預設值)

```
Show-Markdown [-Path] <String[]> [-UseBrowser] [<CommonParameters>]
```

### InputObject

```
Show-Markdown -InputObject <PSObject> [-UseBrowser] [<CommonParameters>]
```

### LiteralPath

```
Show-Markdown -LiteralPath <String[]> [-UseBrowser] [<CommonParameters>]
```

## DESCRIPTION

此 `Show-Markdown` Cmdlet 是用來在終端機或瀏覽器中，以人類看得懂的格式來呈現 Markdown。

`Show-Markdown` 可以傳回字串，其中包含當終端機 (的 vt100 escape 序列) 時，它所呈現的 VT100 escape 序列。 這主要是用來查看終端機中的 Markdown 檔案。 您也可以藉 `ConvertFrom-Markdown` 由指定 **AsVT100EncodedString** 參數，透過來取得這個字串。

`Show-Markdown` 也可以開啟瀏覽器，並顯示轉譯過的 Markdown 版本。 它會將 Markdown 轉換成 HTML，並在您的預設瀏覽器中開啟 HTML 檔案，以轉譯。

您可以使用來變更 `Show-Markdown` Markdown 在終端機中的呈現方式 `Set-MarkdownOption` 。

此 Cmdlet 是在 PowerShell 6.1 中引進。

## 範例

### 範例1：指定路徑的簡單範例

```powershell
Show-Markdown -Path ./README.md
```

### 範例2：指定字串的簡單範例

```powershell
@"
# Show-Markdown

## Markdown

You can now interact with Markdown via PowerShell!

*stars*
__underlines__
"@ | Show-Markdown
```

### 範例2：在瀏覽器中開啟 Markdown

```powershell
Show-Markdown -Path ./README.md -UseBrowser
```

## PARAMETERS

### -InputObject

將顯示在終端機中的 Markdown 字串。 如果您未傳入支援的格式， `Show-Markdown` 將會發出錯誤。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: InputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

指定 Markdown 檔案的路徑。 與 Path 參數不同，LiteralPath 的值將完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含逸出字元，請將它括在單引號中。 單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

指定要呈現之 Markdown 檔的路徑。

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -UseBrowser

將 Markdown 輸入編譯為 HTML，並在您的預設瀏覽器中開啟。

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

### System.Management.Automation.PSObject

### System.String[]

## 輸出

### System.String

## 注意

## 相關連結

[ConvertFrom-Markdown](ConvertFrom-Markdown.md)

