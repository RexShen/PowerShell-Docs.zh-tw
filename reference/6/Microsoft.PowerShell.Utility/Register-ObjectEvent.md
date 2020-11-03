---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/register-objectevent?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-ObjectEvent
ms.openlocfilehash: 2d5e2c5bc47b9a0cb6a900ab7cbec624e0d1849e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204316"
---
# Register-ObjectEvent

## 概要
訂閱 Microsoft .NET Framework 物件所產生的事件。

## SYNTAX

```
Register-ObjectEvent [-InputObject] <PSObject> [-EventName] <String> [[-SourceIdentifier] <String>]
 [[-Action] <ScriptBlock>] [-MessageData <PSObject>] [-SupportEvent] [-Forward] [-MaxTriggerCount <Int32>]
 [<CommonParameters>]
```

## DESCRIPTION

此 `Register-ObjectEvent` Cmdlet 會訂閱本機電腦或遠端電腦上的 .net 物件所產生的事件。

當訂閱的事件被引發時，它會被新增到您工作階段的事件佇列中。 若要取得事件佇列中的事件，請使用 `Get-Event` Cmdlet。

您可以使用的參數 `Register-ObjectEvent` 來指定可協助您在佇列中識別事件的事件屬性值。 您也可以使用 **Action** 參數來指定當訂閱的事件引發時所要採取的動作，並使用 **Forward** 參數將遠端事件傳送到本機會話中的事件佇列。

當您訂閱某個事件時，會將事件訂閱者新增到您的工作階段中。 若要取得會話中的事件訂閱者，請使用 `Get-EventSubscriber` Cmdlet。 若要取消訂用帳戶，請使用 `Unregister-Event` Cmdlet，此 Cmdlet 會從會話刪除事件訂閱者。

## 範例

### 範例1：在新的進程開始時訂閱事件

這個範例會訂閱在新處理程序啟動時產生的事件。

此命令會使用 **ManagementEventWatcher** 物件來取得 **EventArrived** 事件。 查詢物件指定事件是 **Win32_Process** 類別的實例建立事件。

```powershell
$queryParameters = '__InstanceCreationEvent', (New-Object TimeSpan 0,0,1),
    "TargetInstance isa 'Win32_Process'"
$Query = New-Object System.Management.WqlEventQuery -ArgumentList $queryParameters
$ProcessWatcher = New-Object System.Management.ManagementEventWatcher $Query
Register-ObjectEvent -InputObject $ProcessWatcher -EventName "EventArrived"
```

### 範例2：指定回應事件的動作

指定動作時，並不會將被引發的事件新增到事件佇列。 取而代之的是，此動作會回應事件。 在此範例中，當引發實例建立事件指出新的進程啟動時，就會引發新的 **ProcessCreated** 事件。

```powershell
$queryParameters = '__InstanceCreationEvent', (New-Object TimeSpan 0,0,1),
    "TargetInstance isa 'Win32_Process'"
$Query = New-Object System.Management.WqlEventQuery -ArgumentList $queryParameters
$ProcessWatcher = New-Object System.Management.ManagementEventWatcher $query
$newEventArgs = @{
    SourceIdentifier = 'PowerShell.ProcessCreated'
    Sender = $Sender
    EventArguments = $EventArgs.NewEvent.TargetInstance
}
$Action = { New-Event @newEventArgs }
Register-ObjectEvent -InputObject $ProcessWatcher -EventName "EventArrived" -Action $Action
```

```Output
Id   Name               PSJobTypeName   State       HasMoreData   Location   Command
--   ----               -------------   -----       -----------   --------   -------
 5   3db2d67a-efff-...                 NotStarted   False                    New-Event @newEventArgs
```

動作 `$Sender` `$EventArgs` 會使用僅針對事件動作填入的和自動變數。

此 `Register-ObjectEvent` 命令會傳回代表動作（以背景工作方式執行）的工作物件。 您可以使用 Job Cmdlet （例如 `Get-Job` 和 `Receive-Job` ）來管理背景工作。 如需詳細資訊，請參閱 [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md)。

### 範例3：訂閱遠端電腦上的物件事件

這個範例示範如何訂閱遠端電腦上的物件事件。 這個範例會使用 `Enable-ProcessCreationEvent` 腳本檔中定義的函數 `ProcessCreationEvent.ps1` 。 此腳本適用于範例中的所有電腦。

```powershell
# ProcessCreationEvent.ps1
function  Enable-ProcessCreationEvent {
    $queryParameters = "__InstanceCreationEvent", (New-Object TimeSpan 0,0,1),
        "TargetInstance isa 'Win32_Process'"
    $Query = New-Object System.Management.WqlEventQuery -ArgumentList $queryParameters

    $objectEventArgs = @{
        Input = New-Object System.Management.ManagementEventWatcher $Query
        EventName = 'EventArrived'
        SourceIdentifier = 'WMI.ProcessCreated'
        MessageData = 'Test'
        Forward = $True
    }
    Register-ObjectEvent @objectEventArgs
}

$S = New-PSSession -ComputerName "Server01, Server02"
Invoke-Command -Session $S -FilePath ProcessCreationEvent.ps1
Invoke-Command -Session $S { Enable-ProcessCreationEvent }
```

第一個是在兩部遠端電腦上建立 **pssession** ，並將它們儲存在 `$S` 變數中。 接著，Cmdlet 會在 `Invoke-Command` `ProcessCreationEvent.ps1` 中的每個 pssession 中執行腳本 `$S` 。 此動作會 `Enable-ProcessCreationEvent` 在遠端會話中建立函數。
最後，我們會 `Enable-ProcessCreationEvent` 在遠端會話中執行函數。

 函數包含的 `Register-ObjectEvent` 命令會透過 **ManagementEventWatcher** 物件和其 **EventArrived** 事件訂閱 **Win32_Process** 物件上的實例建立事件。

### 範例4：使用 PSEventJob 物件中的動態模組

此範例示範如何使用 **PSEventJob** 物件中的動態模組（當您在事件註冊中包含 **動作** 時所建立）。 首先我們會 createand 並啟用計時器物件，然後將計時器的間隔設定為 500 (毫秒) 。 `Register-ObjectEvent`Cmdlet 會註冊計時器 **Elapsed** 物件的已耗用事件。 **PSEventJob** 物件儲存在 `$Job` 變數中，而且也可以在事件訂閱者的 **Action** 屬性中使用。 如需詳細資訊，請參閱 [EventSubscriber](Get-EventSubscriber.md)。

每當計時器間隔超過時，就會引發事件並執行動作。 在此情況下， `Get-Random` Cmdlet 會產生0到100之間的亂數字，並將它儲存在 `$Random` 變數中。

```powershell
$Timer = New-Object Timers.Timer
$Timer.Interval = 500
$Timer.Enabled = $True
$objectEventArgs = @{
    InputObject = $Timer
    EventName = 'Elapsed'
    SourceIdentifier = 'Timer.Random'
    Action = {$Random = Get-Random -Min 0 -Max 100}
}
$Job = Register-ObjectEvent @objectEventArgs
$Job | Format-List -Property *
& $Job.module {$Random}
& $Job.module {$Random}
```

```Output
State         : Running
Module        : __DynamicModule_53113769-31f2-42dc-830b-8749325e28d6
StatusMessage :
HasMoreData   : True
Location      :
Command       : $Random = Get-Random -Min 0 -Max 100
JobStateInfo  : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : 47b5ec9f-bfe3-4605-860a-4674e5d44ca8
Id            : 7
Name          : Timer.Random
ChildJobs     : {}
PSBeginTime   : 6/27/2019 10:19:06 AM
PSEndTime     :
PSJobTypeName :
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
Information   : {}
60
47
```

**PSEventJob** 有一個 **Module** 屬性，其中包含可執行動作的動態腳本模組。 使用呼叫運算子 (`&`) ，我們會叫用模組中的命令，以顯示變數的值 `$Random` 。

如需模組的詳細資訊，請參閱 [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md)。

## PARAMETERS

### -Action

指定要處理事件的命令。 當事件被引發時，將會執行 **Action** 中的命令，而不會將事件傳送到事件佇列。 使用大括弧 ( { } ) 括住命令以建立指令碼區塊。

**Action** 參數的值可以包括 `$Event` 、、 `$EventSubscriber` `$Sender` 、 `$EventArgs` 和 `$Args` 自動變數。 這些變數會將事件的相關資訊提供給 **Action** 腳本區塊。 如需詳細資訊，請參閱 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)。

當您指定動作時，會傳回 `Register-ObjectEvent` 代表該動作的事件工作物件。 您可以使用各種 Job Cmdlet 來管理事件工作。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: 101
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EventName

指定您要訂閱的事件。

此參數的值必須是 .NET 物件所公開之事件的名稱。 例如， **ManagementEventWatcher** 類別具有名為 **EventArrived** 的事件且已 **停止** 。 若要尋找事件的事件名稱，請使用 `Get-Member` Cmdlet。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Forward

指出此 Cmdlet 會將此訂閱的事件傳送到遠端會話。 當您要訂閱遠端電腦上或遠端工作階段中的事件時，請使用此參數。

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

### -InputObject

指定產生事件的 .NET 物件。 輸入包含物件的變數，或輸入可取得物件的命令或運算式。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxTriggerCount

指定事件可以觸發的最大次數。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MessageData

指定要與這個事件訂閱建立關聯的任何其他資料。 這個參數的值會出現在與此訂閱關聯之所有事件的 MessageData 屬性中。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceIdentifier

指定您為訂閱選取的名稱。 您所選取的名稱在目前的工作階段中必須是唯一的。 預設值是 PowerShell 所指派的 GUID。

這個參數的值會出現在訂閱者物件的 **SourceIdentifier** 屬性值以及與此訂閱相關聯的所有事件物件的值中。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 100
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SupportEvent

表示此 Cmdlet 會隱藏事件訂閱。 當目前的訂閱是更複雜事件註冊機制的一部分，而且不應該獨立探索時，請使用此參數。

若要查看或取消使用 **SupportEvent** 參數建立的訂閱，請使用和 Cmdlet 的 **Force** 參數 `Get-EventSubscriber` `Unregister-Event` 。

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

您無法透過管道傳送物件至 `Register-ObjectEvent` 。

## 輸出

### 無或 System.Management.Automation.PSEventJob

當您使用 **Action** 參數時，會傳回 `Register-ObjectEvent` **PSEventJob** 物件。 否則，它不會產生任何輸出。

## 注意

事件、事件訂閱與事件佇列僅存在目前工作階段中。 若關閉目前工作階段，便會捨棄事件佇列，並取消事件訂閱。

## 相關連結

[Get-Event](Get-Event.md)

[New-Event](New-Event.md)

[Register-EngineEvent](Register-EngineEvent.md)

[Remove-Event](Remove-Event.md)

[Unregister-Event](Unregister-Event.md)

[Wait-Event](Wait-Event.md)
