---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pssession?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSSession
ms.openlocfilehash: f6123bca498d753de1fe284d48f29407c3f8a465
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "93200951"
---
# Exit-PSSession

## 概要
結束遠端電腦的互動式工作階段。

## SYNTAX

```
Exit-PSSession [<CommonParameters>]
```

## DESCRIPTION

**Exit-PSSession** Cmdlet 結束您使用 Enter-PSSession Cmdlet 啟動的互動式工作階段。

您也可以使用 **Exit** 關鍵字結束互動式會話。
效果與使用 **Exit-PSSession** 相同。

## 範例

### 範例 1︰啟動和停止互動式工作階段

```
PS> Enter-PSSession -computername Server01
Server01\PS> Exit-PSSession
PS>
```

這些命令會啟動，然後再停止與 Server01 遠端電腦的互動式工作階段。

### 範例 2︰使用 PSSession 物件啟動和停止互動式工作階段

```
PS> $s = New-PSSession -ComputerName Server01
PS> Enter-PSSession -Session $s
Server01\PS> Exit-PSSession
PS> $s
Id Name            ComputerName    State    ConfigurationName
-- ----            ------------    -----    -----------------
1  Session1        Server01        Opened   Microsoft.PowerShell
```

這些命令會啟動和停止 Server01 電腦的互動式會話，而該電腦使用 ( **PSSession** ) 的 PowerShell 會話。

因為互動式會話是使用 PowerShell 會話來啟動，所以當互動式會話結束時， **PSSession** 仍然可以使用。
如果您使用 *ComputerName* 參數，則 **輸入-PSSession** 會建立在互動式會話結束時關閉的暫時會話。

第一個命令使用 New-PSSession Cmdlet 在 Server01 電腦上建立 **PSSession** 。
命令會將 **PSSession** 儲存在 $s 變數中。

第二個命令使用 **Enter-PSSession** 使用 $s 中的 **PSSession** 啟動互動式工作階段。

第三個命令使用 **Exit-PSSession** 停止互動式工作階段。

最後一個命令會在 $s 變數中顯示 **PSSession** 。
**State** 屬性顯示 **PSSession** 仍然開啟且可供使用。

### 範例 3︰使用 Exit 關鍵字停止工作階段

```
PS> Enter-PSSession -computername Server01
Server01\PS> exit
PS>
```

此範例使用 **Exit** 關鍵字停止使用 **Enter-PSSession** 啟動的互動式工作階段。
**Exit** 關鍵字與使用 **exit-PSSession** 具有相同的效果。

## PARAMETERS

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

您無法使用管線將物件傳送至此 Cmdlet。

## 輸出

### 無

此 Cmdlet 不會傳回任何輸出。

## 注意

* 此 Cmdlet 只採用一般的參數。

*

## 相關連結

[Connect-PSSession](Connect-PSSession.md)

[Disconnect-PSSession](Disconnect-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-Command](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[Receive-PSSession](Receive-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)

