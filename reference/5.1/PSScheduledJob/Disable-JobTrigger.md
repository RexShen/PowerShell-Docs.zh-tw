---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/disable-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-JobTrigger
ms.openlocfilehash: 236e6b7e6e450bd1f3f868f889a19cf796890127
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203032"
---
# Disable-JobTrigger

## 概要
停用排程工作的工作觸發程序。

## SYNTAX

```
Disable-JobTrigger [-InputObject] <ScheduledJobTrigger[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
**Disable-JobTrigger** Cmdlet 會暫時停用排程工作的工作觸發程序。
停用會保留所有工作觸發程序屬性，但不會防止工作觸發程序啟動排程工作。

若要使用此 Cmdlet，請使用 Get-JobTrigger Cmdlet 來取得工作觸發程式。
接著，使用管線傳送工作觸發程序至 **Disable-JobTrigger** 或使用其 *InputObject* 參數。

若要停用工作觸發 **程式，enable-jobtrigger** Cmdlet 會將工作觸發程式的 Enabled 屬性設定為 $False。
若要重新啟用工作觸發程式，請使用 Enable-JobTrigger Cmdlet，此 Cmdlet 會將工作觸發程式的 **Enabled** 屬性設定為 $True。
停用工作觸發程序不會停用排程的工作 (例如 Disable-ScheduledJob Cmdlet 的作用)，但若您停用所有工作觸發程序，則效果等同於停用排程的工作。

若停用排程工作或停用排程工作的所有工作觸發程序，您仍然可以使用 Start-Job Cmdlet 或使用停用的排程工作做為範本來啟動工作。

**Disable-ScheduledJob** 為 Windows PowerShell 內含之 **PSScheduledJob** 模組中的其中一個工作排程 Cmdlet 集合。

如需排程工作的詳細資訊，請參閱 PSScheduledJob 模組中的「關於」主題。
匯入 PSScheduledJob 模組，然後輸入：`Get-Help about_Scheduled*`，或參閱 about_Scheduled_Jobs。

此 Cmdlet 是在 Windows PowerShell 3.0 中引進。

## 範例

### 範例 1：停用工作觸發程序

```
PS C:\> Get-JobTrigger -Name "Backup-Archives" -TriggerID 1 | Disable-JobTrigger
```

此命令會停用本機電腦上 Backup-Archives 排程工作的第一個觸發程序 (識別碼=1)。

此命令會使用 Get-JobTrigger Cmdlet 來取得工作觸發程序。
管線運算子會傳送工作觸發程序至 **Disable-JobTrigger** Cmdlet，此 Cmdlet 會將它停用。

### 範例 2：停用所有工作觸發程序

```
The first command uses the Get-ScheduledJob cmdlet to get the Backup-Archives and Inventory scheduled jobs. A pipeline operator (|) sends the scheduled jobs to the Get-JobTrigger cmdlet, which gets all job triggers of the scheduled jobs. Another pipeline operator sends the job triggers to the **Disable-JobTrigger** cmdlet, which disables them.The first command uses the **Get-ScheduledJob** cmdlet to get the jobs, because its *Name* parameter takes multiple names.
PS C:\> Get-ScheduledJob -Name "Backup-Archives,Inventory" | Get-JobTrigger | Disable-JobTrigger

The second command displays the results. The command repeats the **Get-ScheduledJob** and **Get-JobTrigger** command. A pipeline operator sends the job triggers to the Format-Table cmdlet, which displays the job triggers in a table. The **Format-Table** command adds a JobName property that displays the value of the Name property of the scheduled job in the JobDefinition property of the job trigger object.
PS C:\> Get-ScheduledJob -Name "Backup-Archives,Inventory" | Get-JobTrigger | Format-Table -Property ID, Frequency, At, DaysOfWeek, Enabled, @{Label="JobName";Expression={$_.JobDefinition.Name}} -AutoSize
Id Frequency At                     DaysOfWeek Enabled JobName
-- --------- --                     ---------- ------- -------
1  Weekly    9/28/2011 3:00:00 AM   {Monday}   False   Backup-Archive
2  Daily     9/29/2011 1:00:00 AM              False   Backup-Archive
1  Weekly    10/20/2011 11:00:00 PM {Friday}   False   Inventory
1  Weekly    11/2/2011 2:00:00 PM   {Monday}   False   Inventory
```

這些命令會停用兩個排程工作上的所有工作觸發程序，並顯示結果。

### 範例3：停用遠端電腦上排程工作的工作觸發程式

```
PS C:\> Invoke-Command -ComputerName Server01 {Get-JobTrigger -Name DeployPackage | Where-Object {$_.Frequency -eq "Daily"} | Disable-JobTrigger}
```

此命令會停用 Server01 遠端電腦上 DeployPackage 排程工作的每日工作觸發程序。

此命令會使用 Invoke-Command Cmdlet，在 Server01 電腦上執行命令。
遠端命令會使用 Get-JobTrigger Cmdlet 來取得 DeployPackage 排程工作的工作觸發程序。
管線運算子會將工作觸發程式傳送至 Where-Object Cmdlet，此 Cmdlet 只會傳回每日工作觸發程式。
管線運算子會將每日工作觸發程式傳送至 **enable-jobtrigger** Cmdlet，以停用它們。

## PARAMETERS

### -InputObject
指定要停用的工作觸發程序。
輸入變數，其中包含 **ScheduledJobTrigger** 物件，或輸入命令或運算式取得 **ScheduledJobTrigger** 物件，例如 Get-JobTrigger 命令。
您也可以使用管線將 **ScheduledJobTrigger** 物件傳遞給 **Disable-JobTrigger** 。

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
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

### -Confirm
在執行 Cmdlet 前提示您確認。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
顯示執行 Cmdlet 後會發生的情況。
Cmdlet 並不會執行。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger
您可以使用管線傳送工作觸發程序至 **Disable-JobTrigger** 。

## 輸出

### 無
此 Cmdlet 不會產生任何輸出。

## 注意

* **Disable-JobTrigger** 不會產生錯誤或警告 (若您停用已停用的工作觸發程序)。

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
