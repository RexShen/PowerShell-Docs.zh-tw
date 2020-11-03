---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-clipboard?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Clipboard
ms.openlocfilehash: f3230c247296d5fd907d580e719cbbbc560183a9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203520"
---
# Set-Clipboard

## 概要
設定目前的 Windows 剪貼簿項目。

## SYNTAX

### String (預設值)

```
Set-Clipboard [-Append] [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 值

```
Set-Clipboard [-Value] <String[]> [-Append] [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 路徑

```
Set-Clipboard [-Append] -Path <String[]> [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPath

```
Set-Clipboard [-Append] -LiteralPath <String[]> [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Set-Clipboard`Cmdlet 會設定目前的 Windows 剪貼簿專案。

## 範例

### 範例 1：將文字複製到剪貼簿

```powershell
Set-Clipboard -Value "This is a test string"
```

### 範例 2︰將目錄的內容複製到剪貼簿

此命令會將指定資料夾的內容複製到剪貼簿。

```powershell
Set-Clipboard -Path "C:\Staging\"
```

## PARAMETERS

### -Append

表示此 Cmdlet 不會清除剪貼簿，會將內容附加上去。

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

### -AsHtml

指出此 Cmdlet 會將內容以 HTML 呈現至剪貼簿。

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

### -LiteralPath

指定要複製到剪貼簿的項目路徑。 與 **Path** 不同， **LiteralPath** 的值將完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含逸出字元，請將它括在單引號中。 單引號告知 Windows PowerShell 不要將任何字元視為逸出序列。

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

指定要複製到剪貼簿的項目路徑。 允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Value

以字串陣列的方式指定要複製到剪貼簿的內容。

```yaml
Type: System.String[]
Parameter Sets: Value
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Confirm

在執行 Cmdlet 前提示您確認。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

顯示執行 Cmdlet 後會發生的情況。 Cmdlet 並不會執行。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String[]

## 輸出

## 注意

在很罕見的情況下 `Set-Clipboard` ，如果快速連續地使用具有大量值（例如在迴圈中），您可能偶爾會從剪貼簿取得空白值。 您可以在迴圈中使用來修正此問題 `Start-Sleep -Milliseconds 1` 。

## 相關連結

[Get-Clipboard](Get-Clipboard.md)
