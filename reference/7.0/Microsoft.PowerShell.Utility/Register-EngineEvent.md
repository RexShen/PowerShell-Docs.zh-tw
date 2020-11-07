---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 02/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/register-engineevent?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-EngineEvent
ms.openlocfilehash: cff52e9a321428cde31977f6d91e2d1047faa2ee
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94346848"
---
# Register-EngineEvent

## 概要
訂閱由 PowerShell 引擎和 Cmdlet 所產生的事件 `New-Event` 。

## SYNTAX

```
Register-EngineEvent [-SourceIdentifier] <String> [[-Action] <ScriptBlock>] [-MessageData <PSObject>]
 [-SupportEvent] [-Forward] [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

## DESCRIPTION

`Register-EngineEvent`Cmdlet 會訂閱由 PowerShell 引擎和 Cmdlet 所產生的事件 `New-Event` 。 請使用 **SourceIdentifier** 參數指定事件。

您可以使用這個指令程式來訂閱結束 **引擎事件** 和 Cmdlet 所產生的事件 `New-Event` 。 這些事件會自動新增到您工作階段中的事件佇列但不會訂閱。 不過，訂閱可讓您轉送事件、指定回應事件的動作，以及取消訂閱。

當訂閱的事件被引發時，它會被新增到您工作階段的事件佇列中。 若要取得事件佇列中的事件，請使用 `Get-Event` Cmdlet。

當您訂閱事件時，會將事件訂閱者新增至您的會話。 若要取得會話中的事件訂閱者，請使用 `Get-EventSubscriber` Cmdlet。 若要取消訂用帳戶，請使用 `Unregister-Event` Cmdlet，此 Cmdlet 會從會話刪除事件訂閱者。

## 範例

### 範例 1︰在遠端電腦上註冊 PowerShell 引擎事件

此範例會在兩部遠端電腦上註冊 PowerShell 引擎事件。

```powershell
$S = New-PSSession -ComputerName "Server01, Server02"
Invoke-Command -Session $S { Register-EngineEvent -SourceIdentifier ([System.Management.Automation.PsEngineEvent]::Exiting) -Forward }
```

`New-PSSession` 在每一部遠端電腦上建立使用者管理的會話 (PSSession) 。此 `Invoke-Command` Cmdlet 會 `Register-EngineEvent` 在遠端會話中執行命令。
`Register-EngineEvent` 使用 **SourceIdentifier** 參數來識別事件。 **轉寄** 參數告知引擎將遠端會話中的事件轉送到本機會話。

### 範例 2︰發生 Exiting 事件時，採取指定的動作

這個範例會示範如何 `Register-EngineEvent` 在 **PowerShell** 結束事件時執行，以採取特定動作。

```powershell
Register-EngineEvent -SourceIdentifier PowerShell.Exiting -SupportEvent -Action {
    Get-History | Export-Clixml $Home\history.clixml
}
```

已新增 **SupportEvent** 參數來隱藏事件訂閱。 當 PowerShell 結束時，在此情況下，會將來自結束會話的命令歷程記錄匯出至使用者目錄中的 XML 檔案 `$Home` 。

### 範例3：建立和訂閱使用者自訂事件

此範例會從來源 **MyEventSource** 建立事件的訂用帳戶。 這是我們將用來監視作業進度的任意來源。 `Register-EngineEvent` 用來建立訂用帳戶。 **Action** 參數的腳本區塊會將事件資料記錄至文字檔。

```powershell
Register-EngineEvent -SourceIdentifier MyEventSource -Action {
    "Event: {0}" -f $event.messagedata | Out-File c:\temp\MyEvents.txt -Append
}

Start-Job -Name TestJob -ScriptBlock {
    While ($True) {
        Register-EngineEvent -SourceIdentifier MyEventSource -Forward
        Start-Sleep -seconds 2
        "Doing some work..."
        New-Event -SourceIdentifier MyEventSource -Message ("{0} -  Work done..." -f (Get-Date))
    }
}
Start-Sleep -seconds 4
Get-EventSubscriber
Get-Job
```

```Output
SubscriptionId   : 12
SourceObject     :
EventName        :
SourceIdentifier : MyEventSource
Action           : System.Management.Automation.PSEventJob
HandlerDelegate  :
SupportEvent     : False
ForwardEvent     : False

Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
18     MyEventSource                   Running       True                                 …
19     TestJob         BackgroundJob   Running       True            localhost            …
```

`Register-EngineEvent` 已建立作業識別碼18。 `Start-Job` 已建立作業 Id 19。 在範例 #4 中，我們會移除事件訂用帳戶和作業，然後檢查記錄檔。

### 範例4：取消註冊事件並清除作業

這是範例3的接續。 在此範例中，我們等候10秒，讓數個事件發生。 然後，取消註冊事件訂用帳戶。

```powershell
PS> Start-Sleep -seconds 10
PS> Get-EventSubscriber | Unregister-Event
PS> Get-Job

Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
18     MyEventSource                   Stopped       False                                …
19     TestJob         BackgroundJob   Running       True            localhost            …

PS> Stop-Job -Id 19
PS> Get-Job | Remove-Job
PS> Get-Content C:\temp\MyEvents.txt
Event: 2/18/2020 2:36:19 PM -  Work done...
Event: 2/18/2020 2:36:21 PM -  Work done...
Event: 2/18/2020 2:36:23 PM -  Work done...
Event: 2/18/2020 2:36:25 PM -  Work done...
Event: 2/18/2020 2:36:27 PM -  Work done...
Event: 2/18/2020 2:36:29 PM -  Work done...
Event: 2/18/2020 2:36:31 PM -  Work done...
```

此 `Unregister-Event` Cmdlet 會停止與事件訂閱相關聯的工作， (作業識別碼 18) 。 作業識別碼19仍在執行中，並正在建立新的事件。 我們使用 **job** Cmdlet 來停止工作，並移除不必要的工作物件。 `Get-Content` 顯示記錄檔的內容。

## PARAMETERS

### -Action

指定要處理事件的命令。 當事件被引發時，將會執行 **Action** 中的命令，而不會將事件傳送到事件佇列。 使用大括弧 ( { } ) 括住命令以建立指令碼區塊。

**Action** 參數的值可以包括 `$Event` 、 `$EventSubscriber` 、 `$Sender` 、 `$EventArgs` 和 `$Args` 自動變數，這些變數會將事件的相關資訊提供給 **Action** 腳本區塊。 如需詳細資訊，請參閱 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)。

當您指定動作時，會傳回 `Register-EngineEvent` 代表該動作的事件工作物件。 您可以使用各種 Job Cmdlet 來管理事件工作。

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

### -Forward

指定此 Cmdlet 會將此訂閱的事件傳送到本機電腦上的工作階段。
當您要訂閱遠端電腦上或遠端工作階段中的事件時，請使用此參數。

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

### -MaxTriggerCount

指定事件訂用帳戶將執行動作的最大次數。

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

指定與事件關聯的其他資料。 此參數的值會顯示在事件物件的 **MessageData** 屬性。

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

指定您要訂閱的事件的來源識別碼。 來源識別碼在目前的工作階段中必須是唯一的。 這是必要參數。

這個參數的值會出現在訂閱者物件以及與此訂閱相關聯之所有事件物件的 **SourceIdentifier** 屬性值中。

此值為事件來源的特定值。 這可以是您所建立的任意值，以搭配 `New-Event` Cmdlet 使用。 PowerShell 引擎支援 **>register-engineevent** 值 **powershell。** 正在結束和 **powershell。**

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 100
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SupportEvent

表示此 Cmdlet 會隱藏事件訂閱。 當目前的訂閱是更複雜事件註冊機制的一部分，而不該單獨探索時，請新增此參數。

若要查看或取消使用 **SupportEvent** 參數建立的訂閱，請將 **Force** 參數加入至 `Get-EventSubscriber` 或 `Unregister-Event` Cmdlet。

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

### None

您無法透過管道傳送輸入 `Register-EngineEvent` 。

## 輸出

### 無或 System.Management.Automation.PSEventJob

如果您使用 **Action** 參數，會傳回 `Register-EngineEvent` **PSEventJob** 物件。 否則，它不會產生任何輸出。

## 注意

Linux 或 macOS 平臺上沒有可用的事件來源。

事件、事件訂閱與事件佇列僅存在目前工作階段中。 若關閉目前工作階段，便會捨棄事件佇列，並取消事件訂閱。

## 相關連結

[Get-Event](Get-Event.md)

[New-Event](New-Event.md)

[Register-ObjectEvent](Register-ObjectEvent.md)

[Remove-Event](Remove-Event.md)

[Unregister-Event](Unregister-Event.md)

[Wait-Event](Wait-Event.md)
