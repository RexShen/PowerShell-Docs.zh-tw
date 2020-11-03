---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pstrace?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSTrace
ms.openlocfilehash: 50ad2d48faee88c196942b13141d3ad57c51fdeb
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201323"
---
# Disable-PSTrace

## 概要
停用 Microsoft Windows PowerShell 事件提供者記錄檔。

## SYNTAX

```
Disable-PSTrace [-AnalyticOnly] [<CommonParameters>]
```

## DESCRIPTION

此 Cmdlet 會停用 Microsoft Windows-PowerShell 事件提供者的操作和分析事件記錄檔。

您必須從已提升許可權的 PowerShell 會話執行此 Cmdlet。

## 範例

### 範例1：停用 PowerShell 的分析事件記錄檔

下列範例只會停用 Microsoft Windows PowerShell 提供者的分析事件記錄檔。

```powershell
Disable-PSTrace -AnalyticOnly
```

## PARAMETERS

### -AnalyticOnly

使用這個參數時，此 Cmdlet 會停用 Microsoft Windows PowerShell 提供者的分析事件記錄檔。 操作事件記錄檔不會變更。

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
這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

## 輸出

### 無

## 注意

此 Cmdlet 會使用 `Get-LogProperties` 和 `Set-LogProperties` Cmdlet。

您必須從已提升許可權的 PowerShell 會話執行此 Cmdlet。

## 相關連結

[Get-LogProperties](Get-LogProperties.md)

[Set-LogProperties](Set-LogProperties.md)

[Enable-PSTrace](Enable-PSTrace.md)
