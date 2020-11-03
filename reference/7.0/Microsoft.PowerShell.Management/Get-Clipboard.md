---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-clipboard?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Clipboard
ms.openlocfilehash: 9da33bcf0bc1142859d547debedfb242819041aa
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2020
ms.locfileid: "93239629"
---
# Get-Clipboard

## 概要
取得剪貼簿的內容。

## SYNTAX

```
Get-Clipboard [-Raw] [<CommonParameters>]
```

## DESCRIPTION

`Get-Clipboard`Cmdlet 會以文字形式取得剪貼簿的內容。 多行文字會以類似于的字串陣列形式傳回 `Get-Content` 。

> [!NOTE]
> 在 Linux 上，此 Cmdlet 要求 `xclip` 公用程式必須在路徑中。

## 範例

### 範例1：取得剪貼簿的內容，並將它顯示在命令列中

在此範例中，我們已將文字 "hello" 複製到剪貼簿。

```powershell
Get-Clipboard
```

```Output
hello
```

## PARAMETERS

### -Raw

取得剪貼簿的整個內容。 多行文字會以單一多行字串的形式傳回，而不是字串陣列。

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

## 輸出

### System.String

## 注意

## 相關連結

[Set-Clipboard](Set-Clipboard.md)

