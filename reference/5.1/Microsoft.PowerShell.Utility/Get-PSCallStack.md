---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-pscallstack?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSCallStack
ms.openlocfilehash: 45c2ea5bc166e2d21153ae8b19c1c0afe4ca0640
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "93196684"
---
# Get-PSCallStack

## 概要
顯示目前的呼叫堆疊。

## SYNTAX

```
Get-PSCallStack [<CommonParameters>]
```

## DESCRIPTION
**Get-pscallstack** 指令 Cmdlet 會顯示目前的呼叫堆疊。

雖然它是設計來搭配 Windows PowerShell 偵錯工具使用，您可以在偵錯工具之外，使用這個 Cmdlet 顯示指令碼或函式中的呼叫堆疊。

若要在偵錯工具中執行 **get-pscallstack** 命令，請輸入 `k` 或 `Get-PSCallStack` 。

## 範例

### 範例1：取得函式的呼叫堆疊

```
PS C:\> function my-alias {
$p = $args[0]
Get-Alias | where {$_.definition -like "*$p"} | format-table definition, name -auto
}
PS C:\ps-test> Set-PSBreakpoint -Command my-alias
Command    : my-alias
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : prompt PS C:\> my-alias Get-Content

Entering debug mode. Use h or ? for help.
Hit Command breakpoint on 'prompt:my-alias'
my-alias get-content
[DBG]: PS C:\ps-test> s
$p = $args[0]
DEBUG: Stepped to ':    $p = $args[0]    '
[DBG]: PS C:\ps-test> s
get-alias | Where {$_.Definition -like "*$p*"} | format-table Definition,
[DBG]: PS C:\ps-test>get-pscallstack

Name        CommandLineParameters         UnboundArguments              Location
----        ---------------------         ----------------              --------
prompt      {}                            {}                            prompt
my-alias    {}                            {get-content}                 prompt
prompt      {}                            {}                            prompt PS C:\> [DBG]: PS C:\ps-test> o
Definition  Name
----------  ----
Get-Content gc
Get-Content cat
Get-Content type
```

此命令會使用 **get-pscallstack** 指令程式來顯示我別名的呼叫堆疊，這個簡單的函式會取得 Cmdlet 名稱的別名。

第一個命令在 Windows PowerShell 命令提示字元中輸入函式。
第二個命令使用 Set-PSBreakpoint Cmdlet 在 My-Alias 函式上設定中斷點。
第三個命令使用 My-Alias 函式取得目前工作階段中 Get-Content Cmdlet 的所有別名。

偵錯工具會在函式呼叫時中斷。
兩個連續「逐步執行」命令 (s) 開始逐行執行函式。
然後，會使用 **get-pscallstack** 命令來取得呼叫堆疊。

最後一個命令是「跳離」命令 (o)，它會結束偵錯工具，並繼續執行指令碼直到完成。

## PARAMETERS

### CommonParameters
這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無
您無法使用管線將物件傳送至此 Cmdlet。

## 輸出

### CallStackFrame。
**Get-pscallstack** 會傳回代表呼叫堆疊中專案的物件。

## 注意

## 相關連結

[Disable-PSBreakpoint](Disable-PSBreakpoint.md)

[Enable-PSBreakpoint](Enable-PSBreakpoint.md)

[Format-Table](Format-Table.md)

[Get-PSBreakpoint](Get-PSBreakpoint.md)

[Remove-PSBreakpoint](Remove-PSBreakpoint.md)

[Set-PSBreakpoint](Set-PSBreakpoint.md)
