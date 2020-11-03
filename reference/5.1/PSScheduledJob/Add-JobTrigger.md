---
external help file: Microsoft.PowerShell.ScheduledJob.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/add-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-JobTrigger
ms.openlocfilehash: 6066b8f91c99830fefb09a8bea13fac6ddf958e9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203035"
---
# Add-JobTrigger

## 概要
新增工作觸發程序至排程工作。

## SYNTAX

### JobDefinition (預設值)

```
Add-JobTrigger [-Trigger] <ScheduledJobTrigger[]> [-InputObject] <ScheduledJobDefinition[]>
 [<CommonParameters>]
```

### JobDefinitionId

```
Add-JobTrigger [-Trigger] <ScheduledJobTrigger[]> [-Id] <Int32[]> [<CommonParameters>]
```

### JobDefinitionName

```
Add-JobTrigger [-Trigger] <ScheduledJobTrigger[]> [-Name] <String[]> [<CommonParameters>]
```

## DESCRIPTION
**Add-JobTrigger** Cmdlet 會新增工作觸發程序至排程工作。
您可以使用它來新增多個觸發程序至多個排程工作。

工作觸發程式會以一次性或週期性排程啟動排程工作，或在事件發生時啟動排程工作。

使用 **Add-JobTrigger** 的 *Trigger* 參數來識別要新增的工作觸發程序。
使用 **Add-JobTrigger** 的 *Name* 、 *ID* 或 *InputObject* 參數來識別要新增觸發程序的排程工作。

若要針對 *Trigger* 參數的值建立工作觸發程序，請使用 New-JobTrigger Cmdlet 或使用雜湊表來指定工作觸發程序。

**Add-JobTrigger** 為 Windows PowerShell 所包含 **PSScheduledJob** 模組中的其中一個工作排程 Cmdlet 集合。

如需排程工作的詳細資訊，請參閱 PSScheduledJob 模組中的「關於」主題。
匯入 PSScheduledJob 模組，然後輸入：`Get-Help about_Scheduled*`，或參閱 about_Scheduled_Jobs。

此 Cmdlet 是在 Windows PowerShell 3.0 中引進。

## 範例

### 範例 1：新增工作觸發程序至排程工作

```
PS C:\> $Daily = New-JobTrigger -Daily -At 3AMPS
PS C:\> Add-JobTrigger -Trigger $Daily -Name "TestJob"
```

這些命令會新增 Daily 工作觸發程序至 TestJob 排程工作。

第一個命令會使用 New-JobTrigger Cmdlet 來建立工作觸發程序，此工作觸發程序會在每天上午 3 點啟動排程工作。
此命令會將工作觸發程序儲存於 $Daily 變數中。

第二個命令使用 **Add-JobTrigger** Cmdlet 將 $Startup 變數中的工作觸發程序新增至 TestJob 排程工作。

### 範例2：將工作觸發程式新增至數個排程工作

```
PS C:\> Get-ScheduledJob | Add-JobTrigger -Trigger (New-JobTrigger -AtStartup)
```

此命令會新增 AtStartup 工作觸發程序至本機電腦上的所有排程工作。
它會使用 Get-ScheduledJob 來取得電腦上的所有排程工作。
它會使用管線運算子 (|) 傳送工作至 **Add-JobTrigger** Cmdlet，此 Cmdlet 會新增工作觸發程序至每個排程工作。
*Trigger* 參數的值是 New-JobTrigger 命令，此命令會建立 AtStartup 工作觸發程序。

### 範例 3：複製工作觸發程序

```
PS C:\> $T = Get-JobTrigger -Name "BackupArchives"
PS C:\> Add-JobTrigger -Name "TestBackup,BackupLogs" -Trigger $T
```

這些命令會從 BackupArchives 排程工作複製工作觸發程序，並將它新增到 TestBackup 與 BackupLogs 排程工作。

第一個命令會使用 Get-JobTrigger Cmdlet，來取得 BackupArchives 排程工作的工作觸發程序。
命令會將觸發程序儲存於 $t 變數中。

第二個命令使用 **Add-JobTrigger** Cmdlet 將 $t 中的工作觸發程序新增到 TestBackup 與 BackupLogs 排程工作。

## PARAMETERS

### -Id
指定排程工作的識別碼。
**Add-JobTrigger** 會新增工作觸發程序至指定的排程工作。

若要取得本機電腦或遠端電腦上排程工作的識別碼，請使用 Get-ScheduledJob Cmdlet。

```yaml
Type: System.Int32[]
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
輸入包含 **register-scheduledjob** 物件的變數，或輸入可取得 **register-scheduledjob** 物件的命令或運算式，例如 Get-ScheduledJob 命令。
您也可以使用管線將 **ScheduledJob** 物件傳送至 **Add-JobTrigger** 。

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition[]
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
**Add-JobTrigger** 會新增工作觸發程序至指定的排程工作。
支援萬用字元。

若要取得本機電腦或遠端電腦上排程工作的名稱，請使用 Get-ScheduledJob Cmdlet。

```yaml
Type: System.String[]
Parameter Sets: JobDefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Trigger
指定要新增的工作觸發程序。
輸入指定工作觸發程序的雜湊表或包含 **ScheduledJobTrigger** 物件的變數，或輸入可取得 **ScheduledJobTrigger** 物件的命令或運算式，例如 Get-JobTrigger 命令。
您也可以使用管線將 **ScheduledJobTrigger** 物件傳送至 **Add-JobTrigger** 。

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters
這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger、Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
您可以使用管線傳送工作觸發程序或排程工作至 **Add-JobTrigger** 。

## 輸出

### 無
此 Cmdlet 不會傳回任何輸出。

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
