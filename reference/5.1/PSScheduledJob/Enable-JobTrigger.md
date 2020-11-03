---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/enable-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-JobTrigger
ms.openlocfilehash: d08b55f4ba78af69608ac74c097fc6851164093b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203008"
---
# Enable-JobTrigger

## 概要
啟用排程工作的工作觸發程序。

## SYNTAX

```
Enable-JobTrigger [-InputObject] <ScheduledJobTrigger[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
**Enable-JobTrigger** Cmdlet 會重新啟用排程工作的工作觸發程序，例如使用 Disable-JobTrigger Cmdlet 停用的工作觸發程序。
已啟用與已重新啟用的工作觸發程序可立即啟動排程工作；您不需要重新啟動 Windows 或 Windows PowerShell。

若要使用此 Cmdlet，請使用 Get-JobTrigger Cmdlet 來取得工作觸發程序。
接著，使用管線將工作觸發程序傳送至 **Enable-JobTrigger** 或使用其 *InputObject* 參數。

為啟用工作觸發程序， **Enable-JobTrigger** Cmdlet 會將工作觸發程序的 Enabled 屬性設為 $True。

**Enable-ScheduledJob** 為 Windows PowerShell 內含之 **PSScheduledJob** 模組中的其中一個工作排程 Cmdlet 集合。

如需排程工作的詳細資訊，請參閱 PSScheduledJob 模組中的「關於」主題。
匯入 PSScheduledJob 模組，然後輸入：`Get-Help about_Scheduled*`，或參閱 about_Scheduled_Jobs。

此 Cmdlet 是在 Windows PowerShell 3.0 中引進。

## 範例

### 範例 1︰啟用工作觸發程序

```
PS C:\> Get-JobTrigger -Name Backup-Archives -TriggerID 1 | Enable-JobTrigger
```

此命令會啟用本機電腦上 Backup-Archives 排程工作的第一個觸發程序 (識別碼=1)。

此命令會使用 Get-JobTrigger Cmdlet 來取得工作觸發程序。
管線運算子會傳送工作觸發程序至 **Enable-JobTrigger** Cmdlet，此 Cmdlet 會將它啟用。

### 範例 2︰啟用所有工作觸發程序

```
PS C:\> Get-ScheduledJob | Get-JobTrigger | Enable-JobTrigger
```

此命令會使用 Get-ScheduledJob Cmdlet 來取得本機電腦上排程的工作。
管線運算子 (|) 會將排程工作傳送至 Get-JobTrigger Cmdlet，此 Cmdlet 會取得排程工作的所有工作觸發程序。
另一個管線運算子會傳送工作觸發程序至 **Enable-JobTrigger** Cmdlet，此 Cmdlet 會將它們啟用。

### 範例 3：啟用遠端電腦上排程工作的工作觸發程序

```
PS C:\> Invoke-Command -ComputerName Server01 {Get-JobTrigger -Name DeployPackage | Where-Object {$_.Frequency -eq "AtLogon"} | Enable-JobTrigger}
```

此命令會重新啟用 Server01 遠端電腦上 DeployPackage 排程工作的 AtLogon 工作觸發程序。

此命令會使用 Invoke-Command Cmdlet，在 Server01 電腦上執行命令。
遠端命令會使用 Get-JobTrigger Cmdlet 來取得 DeployPackage 排程工作的工作觸發程序。
管線運算子會將工作觸發程序傳送至 Where-Object Cmdlet，這個 Cmdlet 只會傳回 AtLogon 工作觸發程序。
管線運算子會將 AtLogon 工作觸發程序傳送至 **Enable-JobTrigger** Cmdlet，此 Cmdlet 會啟用它們。

### 範例 4︰顯示已停用的工作觸發程序

```
PS C:\> Get-ScheduledJob | Get-JobTrigger | where {!$_.Enabled} | Format-Table Id, Frequency, At, DaysOfWeek, Enabled, @{Label="JobName";Expression={$_.JobDefinition.Name}}
Id Frequency At                     DaysOfWeek Enabled JobName
-- --------- --                     ---------- ------- -------
 1    Weekly 9/28/2011 3:00:00 AM   {Monday}   False   Backup-Archive
 2    Daily  9/29/2011 1:00:00 AM              False   Backup-Archive
 1    Weekly 10/20/2011 11:00:00 PM {Friday}   False   Inventory
 1    Weekly 11/2/2011 2:00:00 PM   {Monday}   False   Inventory
```

此命令會以表格方式顯示所有排程工作的所有已停用工作觸發程序。
您可以使用像這樣的命令來探索可能需要重新啟用的工作觸發程序。

此命令會使用 Get-ScheduledJob Cmdlet 來取得本機電腦上的排程工作。
管線運算子 (|) 會將排程工作傳送至 Get-JobTrigger Cmdlet，此 Cmdlet 會取得排程工作的所有工作觸發程序。
另一個管線運算子會將工作觸發程序傳送至 Where-Object Cmdlet，此 Cmdlet 只會傳回已停用的工作觸發程序，也就是，工作觸發程序的 Enabled 屬性值不是 (!) true。

另一個管線運算子會將已停用的工作觸發程序傳送至 Format-Table Cmdlet，這個 Cmdlet 會顯示資料表中選取的工作觸發程序屬性。
這些屬性包含新的 JobName 屬性，此屬性會顯示工作觸發程序 JobDefinition 屬性中排程工作的名稱。

## PARAMETERS

### -InputObject
指定要啟用的工作觸發程序。
輸入包含 **>scheduledjobtrigger** 物件的變數，或輸入可取得 **>scheduledjobtrigger** 物件的命令或運算式，例如 Get-JobTrigger 命令。
您也可以使用管線將 **ScheduledJobTrigger** 物件傳遞給 **Enable-JobTrigger** 。

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
您可以使用管線將工作觸發程序傳送至 **Enable-JobTrigger** 。

## 輸出

### 無
此 Cmdlet 不會產生任何輸出。

## 注意

* 若您啟用已經啟用的工作觸發程序， **Enable-JobTrigger** 就不會產生錯誤或警告。

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
