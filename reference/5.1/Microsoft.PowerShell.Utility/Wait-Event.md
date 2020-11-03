---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/wait-event?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Event
ms.openlocfilehash: 55fa54521a6c2e9d37b333a27af4572c6a34913a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203095"
---
# Wait-Event

## 概要
等候引發特定事件後再繼續執行。

## SYNTAX

```
Wait-Event [[-SourceIdentifier] <String>] [-Timeout <Int32>] [<CommonParameters>]
```

## DESCRIPTION

`Wait-Event`Cmdlet 會暫停腳本或函式的執行，直到引發特定事件為止。 當偵測到事件時，就會繼續執行。 若要取消等待，請按下<kbd>CTRL</kbd> + <kbd>C</kbd>。

這個功能為事件輪詢提供一個替代方案。 它也可讓您以兩種不同的方式來判斷事件的回應：

- 使用事件訂閱的 **Action** 參數
- 等候事件返回，然後以動作回應

## 範例

### 範例1：等候下一個事件

此範例會等待下一個引發的事件。

```powershell
Wait-Event
```

### 範例2：等候具有指定來源識別碼的事件

此範例會等待下一個引發且來源識別碼為 ProcessStarted 的事件。

```powershell
Wait-Event -SourceIdentifier "ProcessStarted"
```

### 範例3：等候計時器經過的事件

這個範例會使用指令程式 `Wait-Event` 來等候設定為2000毫秒之計時器上的計時器事件。

```powershell
$Timer = New-Object Timers.Timer
$objectEventArgs = @{
    InputObject = $Timer
    EventName = 'Elapsed'
    SourceIdentifier = 'Timer.Elapsed'
}
Register-ObjectEvent @objectEventArgs
$Timer.Interval = 2000
$Timer.Autoreset = $False
$Timer.Enabled = $True
Wait-Event Timer.Elapsed
```

```Output
ComputerName     :
RunspaceId       : bb560b14-ff43-48d4-b801-5adc31bbc6fb
EventIdentifier  : 1
Sender           : System.Timers.Timer
SourceEventArgs  : System.Timers.ElapsedEventArgs
SourceArgs       : {System.Timers.Timer, System.Timers.ElapsedEventArgs}
SourceIdentifier : Timer.Elapsed
TimeGenerated    : 4/23/2020 2:30:37 PM
MessageData      :
```

### 範例4：等候指定的超時時間之後的事件

此範例會等待下一個引發且來源識別碼為 **ProcessStarted** 的事件最多90秒。 如果指定的時間過期，就會結束等待。

```powershell
Wait-Event -SourceIdentifier "ProcessStarted" -Timeout 90
```

## PARAMETERS

### -SourceIdentifier

指定此 Cmdlet 等候事件的來源識別碼。
根據預設，會 `Wait-Event` 等待任何事件。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Timeout

指定等候事件發生的最長時間（以秒為單位） `Wait-Event` 。 預設值 -1 表示會無限期等待。 當您提交命令時，便會開始計時 `Wait-Event` 。

如果超過指定的時間，即使未引發事件，也會結束等待並返回命令提示字元。 不會顯示任何錯誤訊息。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: Named
Default value: -1
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

## 輸出

### System.Management.Automation.PSEventArgs

## 注意

事件、事件訂閱與事件佇列僅存在目前工作階段中。 若關閉目前工作階段，便會捨棄事件佇列，並取消事件訂閱。

## 相關連結

[Get-Event](Get-Event.md)

[Get-EventSubscriber](Get-EventSubscriber.md)

[New-Event](New-Event.md)

[Register-EngineEvent](Register-EngineEvent.md)

[Register-ObjectEvent](Register-ObjectEvent.md)

[Remove-Event](Remove-Event.md)

[Unregister-Event](Unregister-Event.md)

[Wait-Event](Wait-Event.md)
