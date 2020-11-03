---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/get-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ScheduledJob
ms.openlocfilehash: 40224432c208ee45efc20f556312fa250e9bb7a6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203004"
---
# Get-ScheduledJob

## 概要
取得本機電腦上的排程工作。

## SYNTAX

### DefinitionId (預設值)

```
Get-ScheduledJob [[-Id] <Int32[]>] [<CommonParameters>]
```

### DefinitionName

```
Get-ScheduledJob [-Name] <String[]> [<CommonParameters>]
```

## DESCRIPTION
**Get-ScheduledJob** Cmdlet 會取得本機電腦上的排程工作。
**Get-ScheduledJob** 只會取得目前使用者使用 Register-ScheduledJob Cmdlet 所建立的排程工作。

雖然使用 **Register-ScheduledJob** Cmdlet 建立的工作會出現在 [工作排程器] 中， **Get-ScheduledJob** 只會取得排程工作。
它不會取得在 [工作排程器] 中建立的排程工作。

若未指定參數， **Get-ScheduledJob** 會取得電腦上的所有排程工作。
您可以使用 **Get-ScheduledJob** 的參數依識別碼或名稱取得排程工作，並檢查這些排程工作或使用管線將這些排程工作傳送至其他 Cmdlet。

**Get-ScheduledJob** 為 Windows PowerShell 內含之 **PSScheduledJob** 模組中的其中一個工作排程 Cmdlet 集合。

如需排程工作的詳細資訊，請參閱 PSScheduledJob 模組中的「關於」主題。
匯入 PSScheduledJob 模組，然後輸入：`Get-Help about_Scheduled*`，或參閱 about_Scheduled_Jobs。

此 Cmdlet 是在 Windows PowerShell 3.0 中引進。

## 範例

### 範例 1：取得所有排程工作

```
PS C:\> Get-ScheduledJob
```

此命令會取得本機電腦上的所有排程工作。

### 範例 2：依名稱取得排程工作

```
PS C:\> Get-ScheduledJob -Name *Backup*, *Archive*
```

此命令會取得電腦上名稱包含 Backup 或 Archive 的所有排程工作。
此命令格式可讓您搜尋特定工作。

### 範例 3：取得遠端電腦上的排程工作

```
PS C:\> Invoke-Command -ComputerName (Get-Content Servers.txt) {Get-ScheduledJob}
```

此命令會取得 Servers.txt 檔案中所列之遠端電腦上的所有排程工作。
此命令會使用 Invoke-Command Cmdlet，在每部電腦上執行 **Get-ScheduleJob** 命令。

### 範例 4：使用管線以將排程工作傳送至其他 Cmdlet

```
PS C:\> Get-ScheduledJob DailyBackup, WeeklyBackup | Get-JobTrigger
```

此命令會取得 DailyBackup 與 WeeklyBackup 排程工作的工作觸發程序。
它會使用 **Get-ScheduledJob** Cmdlet 來取得排程工作，以及使用 Get-JobTrigger Cmdlet 來取得排程工作的工作觸發程序。

## PARAMETERS

### -Id
只取得具有所指定識別碼 (ID) 的排程工作。
輸入電腦上之排程工作的一或多個識別碼。
根據預設值， **Get-ScheduledJob** 會取得電腦上的所有排程工作。

```yaml
Type: System.Int32[]
Parameter Sets: DefinitionId
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name
只取得具有所指定名稱的排程工作。
輸入電腦上之排程工作的一或多個名稱。
支援萬用字元。
根據預設值， **Get-ScheduledJob** 會取得電腦上的所有排程工作。

```yaml
Type: System.String[]
Parameter Sets: DefinitionName
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

### 無
您無法使用管線將輸入傳送至 **Get-ScheduledJob** 。

## 輸出

### Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition

## 注意

* 每個排程工作都是儲存在本機電腦之 $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs 目錄的子目錄中。 該子目錄是依排程工作名稱命名，而且包含排程工作的 XML 檔案與其執行記錄。 如需有關磁碟上之排程工作的詳細資訊，請參閱 about_Scheduled_Jobs_Advanced。
* 您在 Windows PowerShell 中建立的排程工作會出現在 [工作排程器] 的 [工作排程器程式庫\Microsoft\Windows\PowerShell\ScheduledJobs] 資料夾。 您可以使用 [工作排程器] 來檢視及編輯排程工作。
* 您可以使用 [工作排程器]、SchTasks.exe 命令列工具或「工作排程器」Cmdlet 來管理使用「排程工作」Cmdlet 建立的排程工作。 不過，您無法使用「排程工作」Cmdlet 來管理您在 [工作排程器] 中建立的工作。

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
