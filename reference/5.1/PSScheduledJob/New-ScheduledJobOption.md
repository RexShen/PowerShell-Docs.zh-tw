---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/new-scheduledjoboption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ScheduledJobOption
ms.openlocfilehash: 35ada8d5aaa6a6c1fdc74a089308aefe13598b10
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202996"
---
# New-ScheduledJobOption

## 概要
建立包含排程工作之進階選項的物件。

## SYNTAX

```
New-ScheduledJobOption [-RunElevated] [-HideInTaskScheduler] [-RestartOnIdleResume]
 [-MultipleInstancePolicy <TaskMultipleInstancePolicy>] [-DoNotAllowDemandStart] [-RequireNetwork]
 [-StopIfGoingOffIdle] [-WakeToRun] [-ContinueIfGoingOnBattery] [-StartIfOnBattery] [-IdleTimeout <TimeSpan>]
 [-IdleDuration <TimeSpan>] [-StartIfIdle] [<CommonParameters>]
```

## DESCRIPTION
**New-ScheduledJobOption** Cmdlet 會建立包含排程工作之進階選項的物件。

您可以使用由 **New-ScheduledJobOption** 所傳回的 **ScheduledJobOptions** 物件來設定新的或現有的排程工作的工作選項。
或者，您也可以使用 Get-ScheduledJobOption Cmdlet 來取得現有排程工作的工作選項，或使用雜湊表值來代表工作選項，以設定工作選項。

如果沒有參數， **ScheduledJobOption** 會產生包含所有選項之預設值的物件。
因為所有屬性 (JobDefinition 屬性除外) 都可以編輯，所以您可以使用產生的物件作為範本，然後為您的企業建立標準選項物件。

建立排程工作並設定排程工作選項時，請檢閱所有排程工作選項的預設值。
只有當符合為排程工作設定的所有執行條件時，排程工作才會執行。

**ScheduledJobOption** 是包含在 Windows PowerShell 之 PSScheduledJob 模組中的其中一個工作排程 Cmdlet 集合。

如需排程工作的詳細資訊，請參閱 PSScheduledJob 模組中的「關於」主題。
匯入 PSScheduledJob 模組，然後輸入：`Get-Help about_Scheduled*`，或參閱 about_Scheduled_Jobs。

此 Cmdlet 是在 Windows PowerShell 3.0 中引進。

## 範例

### 範例1：建立具有預設值的排程工作選項物件

```
PS C:\> New-ScheduledJobOption
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : False
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : False
RunWithoutNetwork      : True
DoNotAllowDemandStart  : False
MultipleInstancePolicy : Ignore
NewJobDefinition       :
```

此命令會建立具有所有預設值的排程工作選項物件。

### 範例2：使用自訂值建立排程工作選項物件

```
PS C:\> New-ScheduledJobOption -RequireNetwork -StartIfOnBattery
StartIfOnBatteries     : True
StopIfGoingOnBatteries : True
WakeToRun              : False
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : False
RunWithoutNetwork      : False
DoNotAllowDemandStart  : False
MultipleInstancePolicy : Ignore
NewJobDefinition       :
```

下列命令會建立一個排程工作物件，此排程工作要求必須有網路連線，且會在即使電腦未連接 AC 電源時執行。

輸出顯示 *RequireNetwork* 參數將 RunWithoutNetwork 屬性的值變更為 $False，且 *StartIfOnBattery* 參數將 StartIfOnBatteries 屬性的值變更為 $True。

### 範例3：設定新排程工作的選項

```
The first command creates a **ScheduledJobOptions** object with the *RunElevated* parameter. It saves the object in the $RunAsAdmin variable.
PS C:\> $RunAsAdmin = New-ScheduledJobOption -RunElevated

The second command uses the Register-ScheduledJob cmdlet to create a new scheduled job. The value of the *ScheduledJobOption* parameter is the option object in the value of the $RunAsAdmin variable.
PS C:\> Register-ScheduledJob -Name Backup -FilePath D:\Scripts\Backup.ps1 -Trigger $Mondays -ScheduledJobOption $RunAsAdmin

The third command uses the Get-ScheduledJobOption cmdlet to get the job options of the Backup scheduled job.The cmdlet output shows that the RunElevated property is set to $True and the JobDefinition property of the job option object is now populated with the scheduled job object for the Backup scheduled job.
PS C:\> Get-ScheduledJobOption -Name Backup
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : False
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : True
RunWithoutNetwork      : True
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNew
JobDefinition          : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

此範例顯示如何使用由 **New-ScheduledJobOption** 所傳回的 **ScheduledJobOptions** 物件來設定新排程工作的選項。

### 範例4：排序排程工作選項物件的屬性

```
PS C:\> $Options = New-ScheduledJobOption -WakeToRun
PS C:\> $Options.PSObject.Properties | Sort-Object -Property Name | Format-Table -Property Name, Value -Autosize
Name                       Value
----                       -----
DoNotAllowDemandStart      False
IdleDuration            00:10:00
IdleTimeout             01:00:00
JobDefinition
MultipleInstancePolicy IgnoreNew
RestartOnIdleResume        False
RunElevated                False
RunWithoutNetwork           True
ShowInTaskScheduler         True
StartIfNotIdle              True
StartIfOnBatteries         False
StopIfGoingOffIdle         False
StopIfGoingOnBatteries      True
WakeToRun                   True
```

此範例顯示如何以字母順序排序 **ScheduledJobOptions** 物件的屬性以方便閱讀。

第一個命令使用 **New-ScheduledJobOption** Cmdlet 來建立 **ScheduledJobOptions** 物件。
此命令使用 *WakeToRun* 參數並將產生的結果物件儲存在 $Options 變數中。

若要取得 $Options 的屬性做為物件，第二個命令會使用所有 Windows PowerShell 物件的 **PSObject** 屬性及其 properties 屬性。
然後，此命令會使用管線將屬性物件傳送至 Sort-Object Cmdlet，此 Cmdlet 會依名稱依字母順序排序屬性，然後再傳送至 Format-Table Cmdlet，以顯示資料表中屬性的名稱和值。

此格式可讓您更輕鬆地在 $Options 中尋找 **ScheduledJobOptions** 物件的 WakeToRun 屬性，並確認其值已從 $False 變更為 $True。

## PARAMETERS

### -ContinueIfGoingOnBattery
當電腦切換到電池電源 (中斷 AC 電源)，若工作正在執行，不要停止排程工作。
根據預設值，當電腦中斷 AC 電源時，排程工作會停止。

*ContinueIfGoingOnBattery* 參數會將排程工作的 StopIfGoingOnBatteries 屬性值設定為 $True。

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

### -DoNotAllowDemandStart
只有在工作被觸發時才啟動工作。
使用者無法手動啟動工作，例如使用 [工作排程器] 中的 [執行] 功能。

此參數只會影響 [工作排程器]。
它不會防止使用者使用 Start-Job Cmdlet 來啟動工作。

*DoNotAllowDemandStart* 參數會將排程工作的 DoNotAllowDemandStart 屬性值設定為 $True。

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

### -HideInTaskScheduler
不要在 [工作排程器] 中顯示工作。
此值只會影響工作執行所在電腦。
根據預設值，排程工作會出現在 [工作排程器] 中。

即使工作是隱藏的，使用者也可以選取工作排程器中的 [顯示隱藏的工作] 選項來顯示工作。

*HideInTaskScheduler* 參數會將排程工作的 ShowInTaskScheduler 屬性值設定為 $False。

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

### -IdleDuration
指定工作啟動前的電腦閒置時間長度。
預設值是 10 分鐘。
若 *IdleTimeout* 值所指定的時間經過之前，電腦閒置時間未達指定的時間長度，則排程工作不會執行 (直到下次排定的時間，如果有的話)。

輸入 **TimeSpan** 物件（例如 New-TimeSpan Cmdlet 所產生的物件），或輸入會 \<hours\> \<minutes\> \<seconds\> 自動轉換成 **TimeSpan** 物件的值（以：：格式表示）。

若要啟用此值，請使用 *StartIfIdle* 參數。
根據預設，排程工作的 StartIfNotIdle 屬性會設定為 $True，Windows PowerShell 會忽略 *IdleDuration* 和 *IdleTimeout* 值。

```yaml
Type: System.TimeSpan
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IdleTimeout
指定排程工作等候電腦閒置的時間長度。
若電腦閒置時間未達到由 *IdleDuration* 參數所指定之時間之前，此時間就已經過，則工作不會執行 (直到排定的下次執行間，如果有的話)。
預設值是一小時。

輸入 **TimeSpan** 物件（例如 New-TimeSpan Cmdlet 所產生的物件），或輸入會 \<hours\> \<minutes\> \<seconds\> 自動轉換成 **TimeSpan** 物件的值（以：：格式表示）。

若要啟用此值，請使用 *StartIfIdle* 參數。
根據預設，排程工作的 StartIfNotIdle 屬性會設定為 $True，Windows PowerShell 會忽略 *IdleDuration* 和 *IdleTimeout* 值。

```yaml
Type: System.TimeSpan
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MultipleInstancePolicy
決定當排程工作的某個執行個體已在執行時，系統如何回應啟動該排程工作之另一個執行個體的要求。
預設值為 IgnoreNew。
此參數可接受的值為：

- IgnoreNew.
將略過新的工作執行個體。
- Parallel
將立即啟動新的工作執行個體。
- 佇列。
新的工作執行個體會在目前的執行個體完成時立即啟動。
- StopExisting.
目前的作業實例會停止，並啟動新的實例。

必須符合工作排程的所有條件，工作才會執行。
例如，如果不符合 *RequireNetwork* 、 *IdleDuration* 和 *IdleTimeout* 參數所設定的條件，則不論此參數的值為何，工作實例都不會啟動。

```yaml
Type: Microsoft.PowerShell.ScheduledJob.TaskMultipleInstancePolicy
Parameter Sets: (All)
Aliases:
Accepted values: None, IgnoreNew, Parallel, Queue, StopExisting

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequireNetwork
只有在網路連線可以使用時才執行排程工作。

若指定此參數且網路連線在排定的啟動時間無法使用，該工作不會執行 (直到排定的下次啟動時間，如果有的話)。

*RequireNetwork* 參數會將排程工作的 RunWithoutNetwork 屬性值設定為 $False。

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

### -RestartOnIdleResume
當電腦成為閒置時重新啟動排程工作。
此參數搭配 *StopIfGoingOffIdle* 參數使用，它可以在電腦成為作用中 (離開閒置狀態) 時暫停執行中的排程工作。

*RestartOnIdleResume* 參數會將排程工作的 RestartOnIdleResume 屬性值設定為 $True。

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

### -RunElevated
使用工作執行所在電腦上 Administrators 群組成員的權限執行排程工作。

若要讓排程工作以系統管理員許可權執行，請使用 Register-ScheduledJob 的 *credential* 參數來提供作業的明確認證。

*RunElevated* 參數會將排程工作的 RunElevated 屬性值設定為 $True。

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

### -StartIfIdle
若電腦已閒置 *IdleDuration* 參數所指定的時間，但 *IdleTimeout* 參數所指定的時間尚未經過，則啟動排程工作。

根據預設值，系統會略過 *IdleDuration* 與 *IdleTimeout* 參數，且工作會在排定的開始時間執行 (即使電腦忙碌中)。

若指定此參數且電腦在排定的開始時間為忙碌中 (非閒置)，則工作不會執行 (直到排定的下次開始時間，如果有的話)。

*StartIfIdle* 參數會將排程工作的 StartIfNotIdle 屬性值設定為 $False。

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

### -StartIfOnBattery
即使電腦在排定的開始時間是使用電池電力執行，也啟動排程工作。
預設值為 $False。

*StartIfOnBattery* 參數會將排程工作的 StartIfOnBatteries 屬性值設定為 $True。

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

### -StopIfGoingOffIdle
若電腦在工作正在執行時成為作用中 (非閒置)，則暫停執行中的排程工作。

根據預設值，當電腦再度進入閒置狀態時，當初在電腦成為作用中時暫停的排程工作會繼續執行。
若要變更此預設行為，請使用 *RestartOnIdleResume* 參數。

*StopIfGoingOffIdle* 參數會將排程工作的 StopIfGoingOffIdle 屬性值設定為 $True。

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

### -WakeToRun
在到了排定的開始時間時將電腦從休眠或睡眠狀態喚醒以執行工作。
根據預設值，在到了排定的開始時間時，若電腦處於休眠或睡眠狀態，則工作不會執行。

*WakeToRun* 參數會將排程工作的 WakeToRun 屬性值設定為 $True。

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
您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions

## 注意

* 您可以使用 **ScheduledJobOption** 所建立的 **ScheduledJobOptions** 物件，做為 Register-ScheduledJob Cmdlet 的 *ScheduledJobOption* 參數值。 不過， *ScheduledJobOption* 參數也可以採用雜湊表值來指定 **ScheduledJobOptions** 物件的屬性及其值，例如：

  `@{ShowInTaskScheduler=$False; RunElevated=$True; IdleDuration="00:05"}`

## 相關連結

[Add-JobTrigger](Add-JobTrigger.md)

[Disable-JobTrigger](Disable-JobTrigger.md)

[Disable-ScheduledJob](Disable-ScheduledJob.md)

[Enable-JobTrigger](Enable-JobTrigger.md)

[Enable-ScheduledJob](Enable-ScheduledJob.md)

[Get-JobTrigger](Get-JobTrigger.md)

[Get-ScheduledJob](Get-ScheduledJob.md)

[Get-ScheduledJobOption](Get-ScheduledJobOption.md)

[New-JobTrigger](New-JobTrigger.md)

[New-ScheduledJobOption](New-ScheduledJobOption.md)

[Register-ScheduledJob](Register-ScheduledJob.md)

[Remove-JobTrigger](Remove-JobTrigger.md)

[Set-JobTrigger](Set-JobTrigger.md)

[Set-ScheduledJob](Set-ScheduledJob.md)

[Set-ScheduledJobOption](Set-ScheduledJobOption.md)

[Unregister-ScheduledJob](Unregister-ScheduledJob.md)
