---
external help file: Microsoft.PowerShell.ConsoleHost.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Host
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.host/stop-transcript?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Transcript
ms.openlocfilehash: 5f02f59e778c55b2292bb4533cf2f8aaab2dbb7d
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "93196676"
---
# Stop-Transcript

## 概要
停止文字記錄。

## SYNTAX

```
Stop-Transcript [<CommonParameters>]
```

## DESCRIPTION

此 `Stop-Transcript` Cmdlet 會停止 Cmdlet 所啟動的文字記錄 `Start-Transcript` 。
或者，您可以結束工作階段以停止文字記錄。

## 範例

### 範例 1︰停止所有文字記錄

```powershell
Stop-Transcript
```

此命令會停止所有文字記錄。

## PARAMETERS

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### System.String

此 Cmdlet 會傳回包含狀態訊息和輸出檔路徑的字串。

## 注意

* 如果文字記錄尚未啟動，此命令便會失敗。

*

## 相關連結

[Start-Transcript](Start-Transcript.md)
