---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/remove-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-JobTrigger
ms.openlocfilehash: adcd74361b1a045a57c7db2f15996f4ea53d6d5b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202992"
---
# Remove-JobTrigger

## 概要
從排程工作刪除工作觸發程式。

## SYNTAX

### JobDefinition (預設值)

```
Remove-JobTrigger [-TriggerId <Int32[]>] [-InputObject] <ScheduledJobDefinition[]> [<CommonParameters>]
```

### JobDefinitionId

```
Remove-JobTrigger [-TriggerId <Int32[]>] [-Id] <Int32[]> [<CommonParameters>]
```

### JobDefinitionName

```
Remove-JobTrigger [-TriggerId <Int32[]>] [-Name] <String[]> [<CommonParameters>]
```

## DESCRIPTION
**Enable-jobtrigger 指令程式** 會從排程工作刪除工作觸發程式。

工作觸發程式會定義用於啟動排程工作的週期性排程或條件。
若要管理工作觸發程序，請使用 New-JobTrigger、Add-JobTrigger、Set-JobTrigger 及 Set-ScheduledJob Cmdlet。

使用 *Remove-JobTrigger* 的 *Name* 、 *ID* 或 **InputObject** 參數來識別要從中移除觸發程序的排程工作。
使用 *TriggerID* 參數來識別要刪除的工作觸發程式。
根據預設值， **Remove-JobTrigger** 會刪除排程工作的所有工作觸發程序。

**Remove-JobTrigger** 為 Windows PowerShell 所包含 PSScheduledJob 模組中的其中一個工作排程 Cmdlet 集合。

如需排程工作的詳細資訊，請參閱 PSScheduledJob 模組中的「關於」主題。
匯入 PSScheduledJob 模組，然後輸入：`Get-Help about_Scheduled*`，或參閱 about_Scheduled_Jobs。

此 Cmdlet 是在 Windows PowerShell 3.0 中引進。

## 範例

### 範例 1：刪除所有工作觸發程序

```
PS C:\> Remove-JobTrigger -Name "Test*"
```

此命令會從名稱開頭為 Test 的排程工作中刪除所有工作觸發程式。

### 範例 2：刪除選取的工作觸發程序

```
PS C:\> Remove-JobTrigger -Name "BackupArchive" -TriggerID 3
```

此命令只會刪除 BackupArchive 排程工作中的第三個觸發程序 (識別碼 = 3)。

### 範例 3：刪除所有排程工作中的 AtStartup 工作觸發程序

```
PS C:\> function Delete-AtStartup
{
    Get-ScheduledJob | Get-JobTrigger | Where-Object {$_.Frequency -eq "AtStartup"} | ForEach-Object { Remove-JobTrigger -InputObject $_.JobDefinition -TriggerID $_.ID}
}
```

此功能會刪除本機電腦上所有工作中的所有 AtStartup 工作觸發程序。
若要使用函數，請在您的會話中執行函數，然後輸入 `Delete-AtStartup` 。

Delete-AtStartup 功能包含單一命令。
此命令會使用 Get-ScheduledJob Cmdlet 來取得本機電腦上的排程工作。
管線運算子 (|) 會將排程的工作傳送至 Get-JobTrigger Cmdlet，此 Cmdlet 會取得每個排程工作的所有工作觸發程序。
管線運算子會將工作觸發程式傳送至 Where-Object Cmdlet，此 Cmdlet 會選取工作觸發程式之 Frequency 屬性值等於 AtStartup 的工作觸發程式。

**Enable-jobtrigger** 物件具有 **JobDefinition** 屬性，其中包含其所觸發的排程工作。
命令的其餘部分使用該實用功能。

管線運算子會將 AtStartup 工作觸發程序傳送至 ForEach-Object Cmdlet，它會在每個 AtStartup 觸發程序上執行 **Remove-JobTrigger** 命令。
**Remove-JobTrigger** 的 *InputObject* 參數值是工作觸發程序之 JobDefinition 屬性中的排程工作。
*TriggerID* 參數的值是工作觸發程序之 ID 屬性中的識別碼。

### 範例 4：刪除遠端排程工作的工作觸發程序

```
PS C:\> Invoke-Command -ComputerName "Server01" { Remove-JobTrigger -ID 38 -TriggerID 1 }
```

此命令會刪除 Server01 電腦上 Inventory 工作的第一個工作觸發程序。

此命令會使用 **Invoke 命令** Cmdlet 在 Server01 電腦上執行 **enable-jobtrigger** Cmdlet。
Enable-jobtrigger Cmdlet 會使用 *ID* 參數來識別清查排程工作，並使用 *TriggerID* 參數來指定第一個觸發 **程式** 。
當多個排程工作具有相同或類似的名稱時， *ID* 參數特別有用。

## PARAMETERS

### -Id
指定排程工作的識別碼。
**Remove-JobTrigger** 會將工作觸發程序從指定的排程工作刪除。

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
您也可以使用管線將 **ScheduledJob** 物件傳送至 **Remove-JobTrigger** 。

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
**Remove-JobTrigger** 會將工作觸發程序從指定的排程工作刪除。
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

### -TriggerId
只刪除指定的工作觸發程序。
根據預設值， **Remove-JobTrigger** 會刪除排程工作的所有觸發程序。
當排程工作有多個工作觸發程序時，請使用此參數。

輸入排程工作之一或多個工作觸發程序的觸發程序識別碼。
如果您指定多個排程工作，Enable-jobtrigger 會刪除所有排程工作中具有指定識別碼的工作觸發 **程式** 。

```yaml
Type: System.Int32[]
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

### Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
您可以使用管線傳送排程工作至 **Remove-JobTrigger** Cmdlet。

## 輸出

### 無
此 Cmdlet 不會產生任何輸出。

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
