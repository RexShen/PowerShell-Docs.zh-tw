---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pshostprocess?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSHostProcess
ms.openlocfilehash: 1734758d34e89020f579fffa217cef58eb222736
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344043"
---
# Exit-PSHostProcess

## 概要
關閉具有本機進程的互動式會話。

## SYNTAX

```
Exit-PSHostProcess [<CommonParameters>]
```

## DESCRIPTION

此 `Exit-PSHostProcess` Cmdlet 會關閉具有本機進程的互動式會話，您可以執行此 Cmdlet 來開啟 `Enter-PSHostProcess` 。 `Exit-PSHostProcess`當您完成對在進程中執行的腳本進行偵錯工具或針對其進行疑難排解時，您可以從進程內執行 Cmdlet。 從 PowerShell 6.2 開始，非 Windows 平臺支援此 Cmdlet。

## 範例

### 範例1：結束處理常式

```
[Process:1520]: PS>  Exit-PSHostProcess
PS>
```

在此範例中，您已在使用中的進程中處理，以依照中的說明，在進程的運行空間中對執行的腳本進行 debug 錯 `Enter-PSHostProcess` 。 鍵入 `exit` 命令以結束偵錯工具之後，請執行 Cmdlet， `Exit-PSHostProcess` 以關閉進程的互動式會話。
此 Cmdlet 會關閉進程中的會話，並將您返回 `PS C:\>` 提示字元。

## PARAMETERS

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

## 輸出

## 注意

## 相關連結

[Enter-PSHostProcess](Enter-PSHostProcess.md)
