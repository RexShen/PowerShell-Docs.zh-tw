---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pswsmancombinedtrace?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSWSManCombinedTrace
ms.openlocfilehash: f6b14ea6cda7d83792f7b51b854471a2cb62bfb5
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201124"
---
# Enable-PSWSManCombinedTrace

## 概要
啟動已啟用 WSMan 和 PowerShell 提供者的記錄會話。

## SYNTAX

```
Enable-PSWSManCombinedTrace [-DoNotOverwriteExistingTrace] [<CommonParameters>]
```

## DESCRIPTION

此 Cmdlet 會啟動已啟用下列 PowerShell 提供者的記錄會話：

- Microsoft-Windows-PowerShell
- Microsoft-Windows-WinRM

會話的名稱為 ' PSTrace '。

此 Cmdlet 會使用 `Start-Trace` Cmdlet。

您必須從已提升許可權的 PowerShell 會話執行此 Cmdlet。

## 範例

### 範例1：啟動合併的記錄會話

```powershell
Enable-PSWSManCombinedTrace
```

## PARAMETERS

### -DoNotOverwriteExistingTrace

根據預設，事件會寫入 "$pshome \Traces\PSTrace.etl"。 使用此參數時，Cmdlet 會建立唯一的檔案名： "$pshome \Traces\ PSTrace_ {guid}. etl"

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

### 無

## 輸出

### 無

## 注意

## 相關連結

[事件追蹤](/windows/desktop/ETW/event-tracing-portal)

[Start-Trace](start-trace.md)

[Disable-PSWSManCombinedTrace](Disable-PSWSManCombinedTrace.md)
