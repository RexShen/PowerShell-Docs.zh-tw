---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell、Cmdlet、markdown
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-markdown?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Markdown
ms.openlocfilehash: efa5e65566e3b80f12f3de5ebd1277bf68c03ff0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204704"
---
# ConvertFrom-Markdown

## 概要
將字串或檔案的內容轉換為 **MarkdownInfo** 物件。

## SYNTAX

### PathParamSet (預設) 

```
ConvertFrom-Markdown [-Path] <String[]> [-AsVT100EncodedString] [<CommonParameters>]
```

### LiteralParamSet

```
ConvertFrom-Markdown -LiteralPath <String[]> [-AsVT100EncodedString] [<CommonParameters>]
```

### InputObjParamSet

```
ConvertFrom-Markdown -InputObject <PSObject> [-AsVT100EncodedString] [<CommonParameters>]
```

## DESCRIPTION

此 Cmdlet 會將指定的內容轉換為 **MarkdownInfo** 。 針對 **path** 參數指定檔案路徑時，會轉換檔案的內容。 輸出物件有三個屬性：

- **Token** 屬性具有已轉換物件 (AST) 的抽象語法樹狀結構
- **Html** 屬性具有指定輸入的 html 轉換
- 如果指定 **AsVT100EncodedString** 參數，則 **VT100ENCODEDSTRING** 屬性具有 ANSI (VT100) escape 序列的已轉換字串

此 Cmdlet 是在 PowerShell 6.1 中引進。

## 範例

### 範例1：將包含 Markdown 內容的檔案轉換成 HTML

```powershell
ConvertFrom-Markdown -Path .\README.md
```

傳回 **MarkdownInfo** 物件。 Token **屬性具有** 已轉換之檔案內容的 AST `README.md` 。 **Html** 屬性具有 html 轉換的檔案內容 `README.md` 。

### 範例2：將包含 Markdown 內容的檔案轉換成 VT100 編碼的字串

```powershell
ConvertFrom-Markdown -Path .\README.md -AsVT100EncodedString
```

傳回 **MarkdownInfo** 物件。 Token **屬性具有** 已轉換之檔案內容的 AST `README.md` 。 **VT100EncodedString** 屬性具有已轉換之檔案內容的 VT100 編碼字串 `README.md` 。

### 範例3：將包含 Markdown 內容的輸入物件轉換成 VT100 編碼的字串

```powershell
Get-Item .\README.md | ConvertFrom-Markdown -AsVT100EncodedString
```

傳回 **MarkdownInfo** 物件。 的 **FileInfo** 物件 `Get-Item` 會轉換成 VT100 編碼的字串。 Token **屬性具有** 已轉換之檔案內容的 AST `README.md` 。 **VT100EncodedString** 屬性具有已轉換之檔案內容的 VT100 編碼字串 `README.md` 。

### 範例4：將包含 Markdown 內容的字串轉換成 VT100 編碼的字串

```powershell
"**Bold text**" | ConvertFrom-Markdown -AsVT100EncodedString
```

傳回 **MarkdownInfo** 物件。 指定的字串 `**Bold text**` 會轉換為 VT100 編碼的字串，並可在 **VT100EncodedString** 屬性中使用。

## PARAMETERS

### -AsVT100EncodedString

指定是否應將輸出編碼為具有 VT100 escape 代碼的字串。

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

### -InputObject

指定要轉換的物件。 指定 system.string 類型的物件時 **，會轉換** 字串。 指定 **FileInfo** 類型的物件時，會轉換物件所指定之檔案的內容。 任何其他類型的物件都會產生錯誤。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: InputObjParamSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

指定要轉換之檔案的路徑。

```yaml
Type: System.String[]
Parameter Sets: LiteralParamSet
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

指定要轉換之檔案的路徑。

```yaml
Type: System.String[]
Parameter Sets: PathParamSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Management.Automation.PSObject

## 輸出

### MarkdownRender. MarkdownInfo

## 注意

## 相關連結

[Markdown 剖析器](https://github.com/lunet-io/markdig)

[ANSI 轉義碼](https://wikipedia.org/wiki/ANSI_escape_code)
