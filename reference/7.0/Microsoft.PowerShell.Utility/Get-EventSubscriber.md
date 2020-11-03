---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-eventsubscriber?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-EventSubscriber
ms.openlocfilehash: 0d8808abf861390b4716e125a05cfa40b23a854a
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201687"
---
# Get-EventSubscriber

## 概要
取得目前工作階段中的事件訂閱者。

## SYNTAX

### BySource (預設值)

```
Get-EventSubscriber [[-SourceIdentifier] <String>] [-Force] [<CommonParameters>]
```

### ById

```
Get-EventSubscriber [-SubscriptionId] <Int32> [-Force] [<CommonParameters>]
```

## DESCRIPTION

**EventSubscriber** 指令 Cmdlet 會取得目前會話中的事件訂閱者。

當您使用 Register 事件 Cmdlet 訂閱事件時，會將事件訂閱者新增至您的 PowerShell 會話，而您訂閱的事件會在每次引發時新增至您的事件佇列。
若要取消事件訂閱，請使用 Unregister-Event Cmdlet 刪除事件訂閱者。

## 範例

### 範例1：取得計時器事件的事件訂閱者

```
PS C:\> $Timer = New-Object Timers.Timer
PS C:\> $Timer | Get-Member -Type Event
PS C:\> Register-ObjectEvent -InputObject $Timer -EventName Elapsed -SourceIdentifier Timer.Elapsed
PS C:\> Get-EventSubscriber
PS C:\> $Timer = New-Object Timers.Timer
PS C:\> $Timer | Get-Member -Type Event
TypeName: System.Timers.Timer
Name     MemberType Definition
----     ---------- ----------
Disposed Event      System.EventHandler Disposed(System.Object, System.EventArgs)
Elapsed  Event      System.Timers.ElapsedEventHandler Elapsed(System.Object, System.Timers.ElapsedEventArgs) PS C:\> Register-ObjectEvent -InputObject $Timer -EventName Elapsed -SourceIdentifier Timer.Elapsed
PS C:\> Get-EventSubscriber
SubscriptionId   : 4
SourceObject     : System.Timers.Timer
EventName        : Elapsed
SourceIdentifier : Timer.Elapsed
Action           :
HandlerDelegate  :
SupportEvent     : False
ForwardEvent     : False
```

此範例使用 **EventSubscriber** 命令取得計時器事件的事件訂閱者。

第一個命令使用 New-Object Cmdlet 建立一個計時器物件執行個體。
它會將新的計時器物件儲存在 $Timer 變數中。

第二個命令使用 Get-Member Cmdlet 顯示可供計時器物件使用的事件。
此命令會使用 **Get 成員** Cmdlet 的型別參數搭配事件的值。

第三個命令使用 Register-ObjectEvent Cmdlet 登錄計時器物件的 Elapsed 事件。

第四個命令使用 **EventSubscriber** 指令程式取得事件訂閱者以取得已經過的事件。

### 範例2：在事件訂閱者的 Action 屬性中使用 PSEventJob 中的動態模組

```
PS C:\> $Timer = New-Object Timers.Timer
PS C:\> $Timer.Interval = 500
PS C:\> Register-ObjectEvent -InputObject $Timer -EventName Elapsed -SourceIdentifier Timer.Random -Action { $Random = Get-Random -Min 0 -Max 100 }

Id  Name           State      HasMoreData  Location  Command
--  ----           -----      -----------  --------  -------
3   Timer.Random   NotStarted False                  $Random = Get-Random ...

PS C:\> $Timer.Enabled = $True
PS C:\> $Subscriber = Get-EventSubscriber -SourceIdentifier Timer.Random
PS C:\> ($Subscriber.action).gettype().fullname
System.Management.Automation.PSEventJob
PS C:\> $Subscriber.action | Format-List -Property *

State         : Running
Module        : __DynamicModule_6b5cbe82-d634-41d1-ae5e-ad7fe8d57fe0
StatusMessage :
HasMoreData   : True
Location      :
Command       : $random = Get-Random -Min 0 -Max 100
JobStateInfo  : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : 88944290-133d-4b44-8752-f901bd8012e2
Id            : 1
Name          : Timer.Random
ChildJobs     : {}
...

PS C:\> & $Subscriber.action.module {$Random}
96
PS C:\> & $Subscriber.action.module {$Random}
23
```

這個範例示範如何在事件訂閱者的 Action 屬性中，使用 **PSEventJob** 物件中的動態模組。

第一個命令使用 New-Object Cmdlet 來建立計時器物件。
第二個命令將計時器的間隔設定為 500 (毫秒)。

第三個命令使用 Register-ObjectEvent Cmdlet 來登錄計時器物件的 Elapsed 事件。
此命令包含一個處理事件的動作。
每當計時器的間隔經過之後，就會引發事件，而動作中的命令也會執行。
在此情況下，Get-Random Cmdlet 會產生0到100之間的亂數字，並將它儲存在 $Random 變數中。
事件的來源識別碼是 Timer.Random。

當您在 **ObjectEvent** 命令中使用 *Action* 參數時，此命令會傳回代表該動作的 **PSEventJob** 物件。

第四個命令啟用計時器。

第五個命令使用 **EventSubscriber 指令程式** 取得 Timer 的事件訂閱者。隨機事件。
它會將事件訂閱者物件儲存在 $Subscriber 變數中。

第六個命令顯示事件訂閱者物件的 Action 屬性包含 **PSEventJob** 物件。
事實上，它包含的 **PSEventJob** 物件與 **ObjectEvent** 命令傳回的相同。

第七個命令使用 Format-List Cmdlet，在清單的 Action 屬性中顯示 **PSEventJob** 物件的所有屬性。
結果顯示 **PSEventJob** 物件有一個 Module 屬性，其中包含可執行動作的動態腳本模組。

其餘的命令會使用呼叫運算子 ( # A0) 來叫用模組中的命令，並顯示 $Random 變數的值。
您可以使用呼叫運算子來叫用模組中的任何命令，包括未匯出的命令。
在此情況下，這些命令會顯示 Elapsed 事件發生時所產生的隨機數字。

如需模組的詳細資訊，請參閱 [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md)。

## PARAMETERS

### -Force

指出此 Cmdlet 會取得所有事件訂閱者，包括使用 *SupportEvent* 參數 ObjectEvent、register >register-wmievent 和 register >register-engineevent 來隱藏事件的訂閱者。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceIdentifier

指定只取得事件訂閱者的 **SourceIdentifier** 屬性值。
根據預設， **EventSubscriber** 會取得會話中的所有事件訂閱者。
不允許使用萬用字元。
此參數區分大小寫。

```yaml
Type: System.String
Parameter Sets: BySource
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SubscriptionId

指定此 Cmdlet 取得的訂用帳戶識別碼。
根據預設， **EventSubscriber** 會取得會話中的所有事件訂閱者。

```yaml
Type: System.Int32
Parameter Sets: ById
Aliases: Id

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### System.Management.Automation.PSEventSubscriber

**EventSubscriber** 會傳回代表每個事件訂閱者的物件。

## 注意

* New-Event Cmdlet 建立自訂事件，不會產生訂閱者。 因此， **EventSubscriber 指令程式** 將找不到這些事件的訂閱者物件。 但是，如果您使用 Register-EngineEvent Cmdlet 來訂閱自訂事件 (為了轉寄事件或指定動作) ， **EventSubscriber** 會尋找 **>register-engineevent** 產生的訂閱者。

  事件、事件訂閱與事件佇列僅存在目前工作階段中。
若關閉目前工作階段，便會捨棄事件佇列，並取消事件訂閱。

*

## 相關連結

[Get-Event](Get-Event.md)

[New-Event](New-Event.md)

[Register-EngineEvent](Register-EngineEvent.md)

[Register-ObjectEvent](Register-ObjectEvent.md)

[Remove-Event](Remove-Event.md)

[Unregister-Event](Unregister-Event.md)

[Wait-Event](Wait-Event.md)
