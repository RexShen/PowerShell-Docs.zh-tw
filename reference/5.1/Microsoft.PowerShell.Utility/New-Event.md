---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-event?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Event
ms.openlocfilehash: c822711b7fda94dd6a2a391560100758ee41d233
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344638"
---
# New-Event

## 概要
建立新的事件。

## SYNTAX

```
New-Event [-SourceIdentifier] <String> [[-Sender] <PSObject>] [[-EventArguments] <PSObject[]>]
 [[-MessageData] <PSObject>] [<CommonParameters>]
```

## DESCRIPTION

`New-Event`Cmdlet 會建立新的自訂事件。

您可以使用自訂事件來通知使用者關於程式的狀態變更，以及您的程式可偵測到的任何變更，包括硬體或系統狀況、應用程式狀態、磁碟狀態、網路狀態或背景工作完成。

自訂事件每次引發時會自動新增至您工作階段的事件佇列，不需要訂閱它們。 但是，如果您想要將事件轉送到本機會話，或指定回應事件的動作，請使用 `Register-EngineEvent` Cmdlet 來訂閱自訂事件。

當您訂閱自訂事件時，會將事件訂閱者新增到您的工作階段中。 如果您使用 Cmdlet 取消事件訂閱 `Unregister-Event` ，則會從會話刪除事件訂閱者和自訂事件。 如果您沒有訂閱自訂事件，必須變更程式條件或關閉 PowerShell 會話，才能刪除事件。

## 範例

### 範例1：在事件佇列中建立新事件

```
PS C:\> New-Event -SourceIdentifier Timer -Sender windows.timer -MessageData "Test"
```

此命令會在 PowerShell 事件佇列中建立新的事件。 它會使用 **Windows Timer** 物件來傳送事件。

### 範例2：引發事件以回應另一個事件

```
PS C:\> function Enable-ProcessCreationEvent
{
   $Query = New-Object System.Management.WqlEventQuery "__InstanceCreationEvent", (New-Object TimeSpan 0,0,1), "TargetInstance isa 'Win32_Process'"
   $ProcessWatcher = New-Object System.Management.ManagementEventWatcher $Query
   $Identifier = "WMI.ProcessCreated"
   Register-ObjectEvent $ProcessWatcher "EventArrived" -SupportEvent $Identifier -Action
   {
      [void] (New-Event -SourceID "PowerShell.ProcessCreated" -Sender $Args[0] -EventArguments $Args[1].SourceEventArgs.NewEvent.TargetInstance)
   }
}
```

這個範例函式會使用 `New-Event` Cmdlet 來引發事件以回應另一個事件。 此命令會使用 `Register-ObjectEvent` Cmdlet 來訂閱在新的進程建立時所引發的 Windows Management Instrumentation (WMI) 事件。 此命令會使用 Cmdlet 的 **Action** 參數來呼叫 `New-Event` Cmdlet，以建立新的事件。

由於引發的事件會 `New-Event` 自動新增至 PowerShell 事件佇列，因此不需要註冊該事件。

## PARAMETERS

### -EventArguments

指定包含事件選項的物件。

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MessageData

指定與事件關聯的其他資料。 此參數的值會顯示在事件物件的 **MessageData** 屬性。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -寄件者

指定引發事件的物件。 預設值為 PowerShell 引擎。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceIdentifier

指定新事件的名稱。 此為必要參數，它在工作階段中必須是唯一的。

此參數的值會出現在事件的 **SourceIdentifier** 屬性中。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### None

您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### System.Management.Automation.PSEventArgs

## 注意

新的自訂事件、事件訂閱與事件佇列只會存在目前的工作階段。
若關閉目前工作階段，便會捨棄事件佇列，並取消事件訂閱。

## 相關連結

[Get-Event](Get-Event.md)

[Register-EngineEvent](Register-EngineEvent.md)

[Register-ObjectEvent](Register-ObjectEvent.md)

[Remove-Event](Remove-Event.md)

[Unregister-Event](Unregister-Event.md)

[Wait-Event](Wait-Event.md)
