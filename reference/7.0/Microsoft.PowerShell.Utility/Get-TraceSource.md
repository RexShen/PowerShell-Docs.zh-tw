---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-tracesource?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TraceSource
ms.openlocfilehash: 024fa690ff9ddd4eae2d7fd6203e83f56fef6cd7
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201660"
---
# Get-TraceSource

## 概要
取得已檢測進行追蹤的 PowerShell 元件。

## SYNTAX

```
Get-TraceSource [[-Name] <String[]>] [<CommonParameters>]
```

## DESCRIPTION

**TraceSource** 指令程式會取得目前使用中之 PowerShell 元件的追蹤來源。
您可以使用資料來判斷您可以追蹤的 PowerShell 元件。
當進行追蹤時，元件會產生有關內部處理中每個步驟的詳細訊息。
開發人員使用追蹤資料來監視資料流量、程式執行和錯誤。

追蹤 Cmdlet 是專為 PowerShell 開發人員所設計，但它們可供所有使用者使用。

## 範例

### 範例 1︰依名稱取得追蹤來源

```
PS C:\> Get-TraceSource -Name "*provider*"
```

此命令會取得所有名稱包含 provider 的追蹤來源。

### 範例 2︰取得所有的追蹤來源

```
PS C:\> Get-TraceSource
```

此命令會取得所有可追蹤的 PowerShell 元件。

## PARAMETERS

### -Name

指定要取得的追蹤來源。
允許使用萬用字元。
參數名稱 *名稱* 是選擇性的。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

您可以使用管線將包含追蹤來源名稱的字串傳送至 **TraceSource** 。

## 輸出

### System.Management.Automation.PSTraceSource

**TraceSource** 會傳回代表追蹤來源的物件。

## 注意

## 相關連結

[Set-TraceSource](Set-TraceSource.md)

[Trace-Command](Trace-Command.md)
