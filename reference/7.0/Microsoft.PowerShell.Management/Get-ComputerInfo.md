---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-computerinfo?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ComputerInfo
ms.openlocfilehash: e9170a8023977f485a99e5e7fc59fb2280a8081e
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347579"
---
# Get-ComputerInfo

## 概要
取得系統和作業系統屬性的合併物件。

## SYNTAX

```
Get-ComputerInfo [[-Property] <String[]>] [<CommonParameters>]
```

## DESCRIPTION

`Get-ComputerInfo`Cmdlet 會取得系統和作業系統屬性的合併物件。
此 Cmdlet 是在 Windows PowerShell 5.1 中引進。

## 範例

### 範例1：取得所有電腦屬性

```powershell
Get-ComputerInfo
```

此命令會從電腦取得所有系統和作業系統屬性。

### 範例2：取得所有電腦作業系統屬性

```powershell
Get-ComputerInfo -Property "os*"
```

此命令會從電腦取得所有的作業系統屬性。

## PARAMETERS

### -Property

以字串陣列指定此 Cmdlet 所顯示的電腦屬性。

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

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### System.String[]

## 輸出

### Get-computerinfo。

## 注意

此 Cmdlet 僅適用于 Windows 平臺。

## 相關連結
