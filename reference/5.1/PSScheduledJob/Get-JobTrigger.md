---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/get-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-JobTrigger
ms.openlocfilehash: 7a75a5a7e6875ed88fd31ea0f385c19f1991f8d7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203007"
---
# Get-JobTrigger

## 概要
取得排程工作的工作觸發程序。

## SYNTAX

### JobDefinition (預設值)

```
Get-JobTrigger [[-TriggerId] <Int32[]>] [-InputObject] <ScheduledJobDefinition> [<CommonParameters>]
```

### JobDefinitionId

```
Get-JobTrigger [[-TriggerId] <Int32[]>] [-Id] <Int32> [<CommonParameters>]
```

### JobDefinitionName

```
Get-JobTrigger [[-TriggerId] <Int32[]>] [-Name] <String> [<CommonParameters>]
```

## DESCRIPTION
**Get-JobTrigger** Cmdlet 會取得排程工作的工作觸發程序。
您可以使用此命令檢查工作觸發程序，或者以管線傳送工作觸發程序至其他 Cmdlet。

工作觸發程式會定義用於啟動排程工作的週期性排程或條件。
工作觸發程序不會獨立儲存至磁碟；它們是排程工作的一部分。
若要取得工作觸發程序，請指定觸發程序啟動的排程工作。

使用 **Get-JobTrigger** Cmdlet 的參數來識別排程工作。
您可以依名稱或識別碼來識別排程工作，或是輸入或將 **register-scheduledjob** 物件（例如 Get-ScheduledJob Cmdlet 所傳回的物件）輸入或輸送至 **enable-jobtrigger** 。

**Get-JobTrigger** 為 Windows PowerShell 所包含 PSScheduledJob 模組中的其中一個工作排程 Cmdlet 集合。

如需排程工作的詳細資訊，請參閱 PSScheduledJob 模組中的「關於」主題。
匯入 PSScheduledJob 模組，然後輸入：`Get-Help about_Scheduled*`，或參閱 about_Scheduled_Jobs。

此 Cmdlet 是在 Windows PowerShell 3.0 中引進。

## 範例

### 範例 1：依排程工作名稱取得工作觸發程序

```
PS C:\> Get-JobTrigger -Name "BackupJob"
```

此命令會使用 Enable-jobtrigger 的 *Name* 參數來取得 BackupJob 排程工作的工作觸發 **程式** 。

### 範例 2：依識別碼取得工作觸發程序

```
The first command uses the Get-ScheduledJob cmdlet to display the scheduled jobs on the local computer. The display includes the IDs of the scheduled jobs.
PS C:\> Get-ScheduledJob
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          ArchiveProjects {1}             \\Server\Share\Archive-Projects.ps1      True
2          Backup          {1,2}           \\Server\Share\Run-Backup.ps1            True
3          Test-HelpFiles  {1}             \\Server\Share\Test-HelpFiles.ps1        True
4          TestJob         {}              \\Server\Share\Run-AllTests.ps1          True

The second command uses the **Get-JobTrigger** cmdlet to get the job trigger for the Test-HelpFiles job (ID = 3)
PS C:\> Get-JobTrigger -ID 3
```

此範例會使用 Enable-jobtrigger 的 *ID* 參數來取得排程工作的工作觸發 **程式** 。

### 範例 3：使用管線傳送工作來取得工作觸發程序

```
PS C:\> Get-ScheduledJob -Name *Backup*, *Archive* | Get-JobTrigger
```

此命令會取得在其名稱中有備份或封存之所有工作的工作觸發程式。

### 範例 4：取得遠端電腦上工作的工作觸發程序

```
PS C:\> Invoke-Command -ComputerName Server01 { Get-ScheduledJob Backup | Get-JobTrigger -TriggerID 2 }
```

此命令會取得遠端電腦上之排程工作的兩個工作觸發程序的其中一個。

此命令會使用 Invoke-Command Cmdlet，在 Server01 電腦上執行命令。
其會使用 Get-ScheduledJob Cmdlet 來取得 Backup 排程工作，並使用管線將它傳送至 **Get-JobTrigger** Cmdlet。
它使用 *TriggerID* 參數來只取得第二個觸發程式。

### 範例 5：取得所有工作觸發程序

```
PS C:\> Get-ScheduledJob | Get-JobTrigger | Format-Table -Property ID, Frequency, At, DaysOfWeek, Enabled, @{Label="ScheduledJob";Expression={$_.JobDefinition.Name}} -AutoSize
Id Frequency At                    DaysOfWeek Enabled ScheduledJob
-- --------- --                    ---------- ------- ------------
1    Weekly  9/28/2011 3:00:00 AM  {Monday}   True    Backup
1    Daily   9/27/2011 11:00:00 PM            True    Test-HelpFiles
```

此命令會取得本機電腦上所有排程工作的所有工作觸發程序。

此命令會使用 Get-ScheduledJob 來取得本機電腦上的排程工作，並使用管線將它們傳送至 **Get-JobTrigger** ，其會取得每個排程工作的工作觸發程序 (如果有的話)。

若要將排程工作的名稱加入至工作觸發程式顯示，此命令會使用 Format-Table Cmdlet 的計算屬性功能。
除了預設顯示的工作觸發程式屬性之外，此命令還會建立新的 Register-scheduledjob 屬性，以顯示排程工作的名稱。

### 範例 6：取得排程工作的工作觸發程序屬性

```
The command uses the Get-ScheduledJob cmdlet to get the Test-HelpFiles scheduled job. Then it uses the dot method (.) to get the JobTriggers property of the Test-HelpFiles scheduled job.
PS C:\> (Get-ScheduledJob Test-HelpFiles).JobTriggers

The second command uses the Get-ScheduledJob cmdlet to get all scheduled jobs on the local computer. It uses the ForEach-Object cmdlet to get the value of the JobTrigger property of each scheduled job.
PS C:\> Get-ScheduledJob | foreach {$_.JobTriggers}
```

排程工作的工作觸發程序是儲存在工作的 JobTriggers 屬性中。
此範例顯示使用 **enable-jobtrigger 指令程式** 來取得工作觸發程式的替代方案。
結果類似使用 **Get-JobTrigger** Cmdlet，且技巧可交換使用。

### 範例 7：比較工作觸發程序

```
The first command gets the job trigger of the ArchiveProjects scheduled job. The command pipes the job trigger to the Tee-Object cmdlet, which saves the job trigger in the $T1 variable and displays it at the command line.
PS C:\> Get-ScheduledJob -Name ArchiveProjects | Get-JobTrigger | Tee-Object -Variable T1
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
0          Daily           9/26/2011 3:00:00 AM                           True

The second command gets the job trigger of the Test-HelpFiles scheduled job. The command pipes the job trigger to the Tee-Object cmdlet, which saves the job trigger in the $T2 variable and displays it at the command line.
PS C:\> Get-ScheduledJob -Name "Test-HelpFiles" | Get-JobTrigger | Tee-Object -Variable T2
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
0          Daily           9/26/2011 3:00:00 AM                           True

The third command compares the job triggers in the $t1 and $t2 variables. It uses the Get-Member cmdlet to get the properties of the job trigger in the $t1 variable. It pipes the properties to the ForEach-Object cmdlet, which compares each property to the properties of the job trigger in the $t2 variable by name. The command then pipes the differing properties to the Format-List cmdlet, which displays them in a list.The output indicates that, although the job triggers appear to be the same, the HelpFiles job trigger includes a random delay of three (3) minutes.
PS C:\> $T1 | Get-Member -Type Property | ForEach-Object { Compare-Object $T1 $T2 -Property $_.Name}
RandomDelay                                                 SideIndicator
-----------                                                 -------------
00:00:00                                                    =>
00:03:00                                                    <=
```

此範例顯示如何比較兩個排程工作的工作觸發程序。

## PARAMETERS

### -Id
指定排程工作的識別碼。
**Get-JobTrigger** 會取得指定排程工作的工作觸發程序。

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
您也可以使用管線將 **ScheduledJob** 物件傳送至 **Get-JobTrigger** 。

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
**Get-JobTrigger** 會取得指定排程工作的工作觸發程序。
支援萬用字元。

若要取得本機電腦或遠端電腦上排程工作的名稱，請使用 Get-ScheduledJob Cmdlet。

```yaml
Type: System.String
Parameter Sets: JobDefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TriggerId
取得指定的工作觸發程序。
輸入排程工作之一或多個工作觸發程序的觸發程序識別碼。
當由 *Name* 、 *ID* 或 *InputObject* 參數指定的排程工作有多個工作觸發程序時，請使用此參數。

```yaml
Type: System.Int32[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
您可以使用管線將排程工作從 Get-ScheduledJob 傳送至 **Get-JobTrigger** 。

## 輸出

### Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger

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
