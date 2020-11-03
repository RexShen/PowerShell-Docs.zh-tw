---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/set-scheduledjoboption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ScheduledJobOption
ms.openlocfilehash: 6647e9ba4e2ee49afa90dd382573d437d2deaee6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202975"
---
# Set-ScheduledJobOption

## 概要
變更排程工作的工作選項。

## SYNTAX

```
Set-ScheduledJobOption [-InputObject] <ScheduledJobOptions> [-PassThru] [-RunElevated] [-HideInTaskScheduler]
 [-RestartOnIdleResume] [-MultipleInstancePolicy <TaskMultipleInstancePolicy>] [-DoNotAllowDemandStart]
 [-RequireNetwork] [-StopIfGoingOffIdle] [-WakeToRun] [-ContinueIfGoingOnBattery] [-StartIfOnBattery]
 [-IdleTimeout <TimeSpan>] [-IdleDuration <TimeSpan>] [-StartIfIdle] [<CommonParameters>]
```

## DESCRIPTION
**Set-ScheduledJobOptions** Cmdlet 會變更排程工作的工作選項。

若要變更排程工作的選項，請先使用 Get-ScheduledJobOption Cmdlet 來取得排程工作的工作選項。
接著，使用管線傳送選項至 **Set-ScheduledJobOption** ，或將選項儲存在變數中並使用 *Set-ScheduledJobOption* Cmdlet 的 **InputObject** 參數來指定選項。
使用 **Set-ScheduledJobOption** 的其他參數來變更工作選項。

若要開啟工作選項，請使用設定該選項的參數。
若要關閉選項，請輸入參數名稱、冒號 (： ) 和 $False。
例如，若要關閉 *RunElevated* 選項，請輸入 `-RunElevated:$False` 。

每個工作選項物件都包含 JobDefinition 屬性 (其中包含排程工作)，因此當工作選項變更時，與該排程工作的關聯仍會維持。

排程工作選項決定工作由 [工作排程器] 啟動時的執行方式。
當您使用 Start-Job Cmdlet 來啟動排程工作時，這些選項不適用。

**ScheduledJobOption** 是包含在 Windows PowerShell 之 PSScheduledJob 模組中的其中一個工作排程 Cmdlet 集合。

如需排程工作的詳細資訊，請參閱 PSScheduledJob 模組中的「關於」主題。
匯入 PSScheduledJob 模組，然後輸入：`Get-Help about_Scheduled*`，或參閱 about_Scheduled_Jobs。

此 Cmdlet 是在 Windows PowerShell 3.0 中引進。

## 範例

### 範例1：變更工作選項

```
PS C:\> Get-ScheduledJobOption -Name "DeployPackage"
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
RunWithoutNetwork      : False
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNew
JobDefinition          :

The second command uses the **Set-ScheduledJobOpton** cmdlet to change the job options so the values of the WakeToRun and RunWithoutNetwork properties are $True. The command uses the *Passthru* parameter to return the trigger after the change.
PS C:\> Get-ScheduledJobOption -Name "DeployPackage" | Set-ScheduledJobOption -WakeToRun -RequireNetwork:$False -Passthru
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : True
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : False
RunWithoutNetwork      : True
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNewJobDefinition          :
```

此範例顯示如何變更本機電腦上之排程工作的選項。

第一個命令會使用 Get-ScheduledJobOption Cmdlet 來取得 DeployPackage 排程工作的工作選項。
輸出顯示 WakeToRun 和 RunElevated 屬性設定為 $False。

此命令並非必要；包含此命令僅為顯示選項變更的效果。

### 範例2：變更所有遠端排程工作的選項

```
PS C:\> Invoke-Command -Computer "Server01" -ScriptBlock {Get-ScheduledJob | Get-ScheduledJobOption | Set-ScheduledJobOption -IdleTimeout 2:00:00}
```

此命令會將 *IdleTimeout* 的值從一小時變更為 Server01 電腦上所有排程工作的 (預設值) 為兩小時。

此命令會使用 Invoke-Command Cmdlet，在 Server01 電腦上執行命令。

遠端命令的開頭是可取得電腦上所有排程工作的 Get-ScheduledJob 命令。
排程的工作會以管道傳送至 Get-ScheduledJobOption Cmdlet，以取得排程工作的工作選項。
每個工作選項物件都包含 JobDefinition 屬性 (其中包含排程工作)，因此選項物件會維持與排程工作關聯 (即使它已被變更)。

工作觸發程式會以管線傳送至 **ScheduledJobOption** Cmdlet，此 Cmdlet 會將 *IdleTimeout* 選項的值變更為兩小時， (2:00:00) 。

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

即使工作是隱藏的，使用者也可以選取工作排程器中的 [ **顯示隱藏** 的工作] 選項來顯示工作。

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

輸入 timespan 物件（例如 New-TimeSpan Cmdlet 所產生的物件），或輸入會 \<hours\> \<minutes\> \<seconds\> 自動轉換成 **timespan** 物件的值（以：：格式表示）。

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
指定工作啟動前的電腦閒置時間長度。
預設值是 10 分鐘。
若 **IdleTimeout** 值所指定的時間經過之前，電腦閒置時間未達指定的時間長度，則排程工作不會執行 (直到下次排定的時間，如果有的話)。

輸入 timespan 物件（例如 New-TimeSpan Cmdlet 所產生的物件），或輸入會 \<hours\> \<minutes\> \<seconds\> 自動轉換成 **timespan** 物件的值（以：：格式表示）。

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

### -InputObject
指定工作選項。
輸入包含 **ScheduledJobOptions** 物件的變數，或輸入可取得 **ScheduledJobOptions** 物件的命令或運算式，例如 Get-ScheduledJobOption 命令。
您也可以使用管線將 **ScheduledJobOptions** 物件傳送至 **ScheduledJobOption** 。

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -MultipleInstancePolicy
決定當排程工作的某個執行個體已在執行時，系統如何回應啟動該排程工作之另一個執行個體的要求。
此參數可接受的值為：

- IgnoreNew.
將略過新的工作執行個體。
這是預設值。
- Parallel
將立即啟動新的工作執行個體。
- 佇列。
新的工作執行個體會在目前的執行個體完成時立即啟動。
- StopExisting.
將停止目前的工作執行個體，並啟動新的執行個體。

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

### -PassThru
傳回代表您正在使用之項目的物件。
根據預設，此 Cmdlet 不會產生任何輸出。

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

**RunElevated** 參數會將排程工作的 **RunElevated** 屬性值設定為 True。

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
若電腦已閒置 **IdleDuration** 參數所指定的時間，但 *IdleTimeout* 參數所指定的時間尚未經過，則啟動排程工作。

根據預設值，系統會略過 *IdleDuration* 與 *IdleTimeout* 參數，且工作會在排定的開始時間執行 (即使電腦忙碌中)。

若指定此參數且電腦在排定的開始時間為忙碌中 (非閒置)，則工作不會執行 (直到排定的下次開始時間，如果有的話)。

*StartIfIdle* 參數會將排程工作的 **StartIfNotIdle** 屬性值設定為 False。

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
預設值是 False。

*StartIfOnBattery* 參數會將排程工作的 **StartIfOnBatteries** 屬性值設定為 $True。

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

### Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions
您可以使用管線傳送排程工作選項物件至 **Set-ScheduledJobOption** 。

## 輸出

### None 或 Register-scheduledjob. ScheduledJobOptions
當您使用 *Passthru* 參數時， **Set-ScheduledJobOption** 會傳回已變更的工作選項。
否則，此 Cmdlet 不會產生任何輸出。

## 注意

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
