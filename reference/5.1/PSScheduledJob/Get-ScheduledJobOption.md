---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/get-scheduledjoboption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ScheduledJobOption
ms.openlocfilehash: 5c317be9add0898137aceed6c39032f3e271bac1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203000"
---
# Get-ScheduledJobOption

## 概要
取得排程工作的工作選項。

## SYNTAX

### JobDefinition (預設值)

```
Get-ScheduledJobOption [-InputObject] <ScheduledJobDefinition> [<CommonParameters>]
```

### JobDefinitionId

```
Get-ScheduledJobOption [-Id] <Int32> [<CommonParameters>]
```

### JobDefinitionName

```
Get-ScheduledJobOption [-Name] <String> [<CommonParameters>]
```

## DESCRIPTION
**ScheduledJobOption 指令程式** 會取得排程工作的工作選項。
您可以使用此命令檢查工作選項，或者以管線傳送工作選項至其他 Cmdlet。

工作選項不會獨立儲存至磁碟；它們是排程工作的一部分。
若要取得排程工作的工作選項，請指定排程工作。

使用 **Get-ScheduledJobOption** Cmdlet 的參數來識別排程工作。
您可以依名稱或識別碼來識別排程工作，或是輸入或將 **register-scheduledjob** 物件（例如 Get-ScheduledJob Cmdlet 所傳回的物件）輸入或輸送至 **ScheduledJobOption** 。

**Get-ScheduledJobOption** 為 Windows PowerShell 內含之 PSScheduledJob 模組中的其中一個工作排程 Cmdlet 集合。

如需排程工作的詳細資訊，請參閱 PSScheduledJob 模組中的「關於」主題。
匯入 PSScheduledJob 模組，然後輸入：`Get-Help about_Scheduled*`，或參閱 about_Scheduled_Jobs。

此 Cmdlet 是在 Windows PowerShell 3.0 中引進。

## 範例

### 範例 1：取得工作選項

```
PS C:\> Get-ScheduledJobOption -Name "*Backup*"
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

MultipleInstancePolicy : Ignore

NewJobDefinition       : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

此命令會取得名稱中有備份之排程工作的工作選項。
結果顯示 **Get-ScheduledJobOption** 傳回的工作選項物件。

### 範例 2：取得所有工作選項

```
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption
```

此命令會取得本機電腦上所有排程工作的工作選項。

它會使用 Get-ScheduledJob Cmdlet，來取得本機電腦上的排程工作。
管線運算子 (|) 將排程工作傳送至 **ScheduledJobOption 指令程式** ，以取得每個排程工作的工作選項。

### 範例 3：取得選取的工作選項

```
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption | Where {$_.RunElevated -and !$_.WaketoRun}
StartIfOnBatteries     : False

StopIfGoingOnBatteries : True

WakeToRun              : True

StartIfNotIdle         : True

StopIfGoingOffIdle     : False

RestartOnIdleResume    : False

IdleDuration           : 00:10:00

IdleTimeout            : 01:00:00

ShowInTaskScheduler    : True

RunElevated            : True

RunWithoutNetwork      : True

DoNotAllowDemandStart  : False

MultipleInstancePolicy : Ignore

NewJobDefinition       : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition

The second command shows how to find to which scheduled job the job options belong. This command uses a pipeline operator (|) to send the selected job options to the ForEach-Object cmdlet, which gets the JobDefinition property of each options object. The JobDefinition property contains the originating job object. The results show that the selected options came from the DeployPkg scheduled job.
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption | Where {$_.RunElevated -and !$_.WaketoRun} | ForEach-Object {$_.JobDefinition}
Id         Name            Triggers        Command                                  Enabled

--         ----            --------        -------                                  -------

2          DeployPkg         {1, 2}        DeployPackage.ps1                        True
```

此範例顯示如何使用特定值尋找工作選項物件。

第一個命令會取得工作選項，其中 RunElevated 屬性的值為 $True，而 RunWithoutNetwork 屬性的值為 $False。
輸出會顯示已選取的 **JobOptions** 物件。

### 範例 4：使用工作選項來建立新工作

```
PS C:\> $Opts = Get-ScheduledJobOption -Name "BackupTestLogs"
PS C:\> Register-ScheduledJob -Name "Archive-Scripts" -FilePath "\\Srv01\Scripts\ArchiveScripts.ps1" -ScheduledJobOption $Opts
```

這個範例示範如何使用 Get-ScheduledJobOption 在新的排程工作中取得的工作選項。

第一個命令會使用 **ScheduledJobOption** 來取得 BackupTestLogs 排程工作的工作選項。
命令會將選項儲存於 $Opts 變數中。

第二個命令會使用 Register-ScheduledJob Cmdlet 來建立新的排程工作。
*ScheduledJobOption* 參數的值為 $Opts 變數中的選項物件。

### 範例 5：從遠端電腦取得工作選項

```
PS C:\> $O = Invoke-Command -ComputerName "Srv01" -ScriptBlock {Get-ScheduledJob -Name "DataDemon" }
```

此命令會使用 Invoke-Command Cmdlet，來取得 Srv01 電腦上 DataDemon 工作的排程工作選項。
命令會將選項儲存在 $O 變數中。

## PARAMETERS

### -Id
指定排程工作的識別碼。
**Get-ScheduledJobOption** 會取得指定排程工作的工作選項。

若要取得本機電腦或遠端電腦上排程工作的識別碼，請使用 Get-ScheduledJob Cmdlet。

```yaml
Type: System.Int32
Parameter Sets: JobDefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
指定排程工作。
輸入包含 **ScheduledJob** 物件的變數，或輸入可取得 **ScheduledJob** 物件的命令或運算式，例如 Get-ScheduledJob 命令。
您也可以使用管線傳送 **ScheduledJob** 物件至 **Get-ScheduledJobOption** 。

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
Parameter Sets: JobDefinition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name
指定排程工作的名稱。
**Get-ScheduledJobOption** 會取得指定排程工作的工作選項。
支援萬用字元。

若要取得本機電腦或遠端電腦上排程工作的名稱，請使用 Get-ScheduledJob Cmdlet。

```yaml
Type: System.String
Parameter Sets: JobDefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters
這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
您可以使用管線將排程工作從 Get-ScheduledJob 傳送至 **Get-ScheduledJobOption** 。

## 輸出

### Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions

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
