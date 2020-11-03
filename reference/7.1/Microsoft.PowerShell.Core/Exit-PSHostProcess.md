---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pshostprocess?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSHostProcess
ms.openlocfilehash: b7e2bf7cff84e92f4c174ef01861ee5c0a822bea
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "93200954"
---
# Exit-PSHostProcess

## 概要
關閉具有本機進程的互動式會話。

## SYNTAX

```
Exit-PSHostProcess [<CommonParameters>]
```

## DESCRIPTION

**>enter-pshostprocess** 指令程式會透過執行 Enter-PSHostProcess Cmdlet，關閉您已開啟的本機進程的互動式會話。 當您完成對在進程中執行的腳本進行錯錯或疑難排解時，您可以從進程內執行 **>enter-pshostprocess 指令程式** 。

## 範例

### 範例1：結束處理常式

```
[Process:1520]: PS>  Exit-PSHostProcess
PS>
```

在此範例中，您已在使用中的進程中處理，以在進程的運行空間中對執行的腳本進行 debug 錯，如 >enter-pshostprocess 中所述。 輸入 **exit** 命令以結束偵錯工具之後，請執行 **>enter-pshostprocess** 指令程式，以關閉進程的互動式會話。
此 Cmdlet 會關閉進程中的會話，並讓您回到 PS C： \\ \> 提示字元。

## PARAMETERS

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

## 輸出

## 注意

## 相關連結

[Enter-PSHostProcess](Enter-PSHostProcess.md)

