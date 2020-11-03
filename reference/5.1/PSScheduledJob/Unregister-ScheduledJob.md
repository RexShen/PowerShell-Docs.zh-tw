---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/unregister-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-ScheduledJob
ms.openlocfilehash: 0c0b55513bcfdcebdcd5d8a6f17968a4a45e2839
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202972"
---
# Unregister-ScheduledJob

## 概要
刪除本機電腦上的排程工作。

## SYNTAX

### Definition (預設值)

```
Unregister-ScheduledJob [-InputObject] <ScheduledJobDefinition[]> [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### DefinitionId

```
Unregister-ScheduledJob [-Id] <Int32[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### DefinitionName

```
Unregister-ScheduledJob [-Name] <String[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
**Unregister-ScheduledJob** Cmdlet 會刪除本機電腦上的排程工作。

當它刪除或取消註冊排程工作時， **取消註冊-register-scheduledjob** 會刪除 $home \appdata\local\microsoft\windows\powershell\scheduledjobs directory) 中 (排程工作的目錄，其中包含定義排程工作的 XML 檔案、工作執行歷程記錄，以及所有工作結果。
此動作也會將工作從 [工作排程器] 刪除。

**Unregister-ScheduledJob** 只會刪除使用 Register-ScheduledJob Cmdlet 所建立的排程工作。
它不會刪除在 [工作排程器] 中建立的排程工作。

您可以使用 **register-scheduledjob** 的參數，依識別碼或名稱刪除排程工作，或使用管線將排程工作從 Get-ScheduledJob 傳送至 **取消註冊-register-scheduledjob** 。

**Unregister-ScheduledJob** 為 Windows PowerShell 內含之 PSScheduledJob 模組中其中一個工作排程 Cmdlet 的集合。

如需排程工作的詳細資訊，請參閱 PSScheduledJob 模組中的「關於」主題。
匯入 PSScheduledJob 模組，然後輸入：`Get-Help about_Scheduled*`，或參閱 about_Scheduled_Jobs。

此 Cmdlet 是在 Windows PowerShell 3.0 中引進。

## 範例

### 範例 1：刪除排程工作

```
PS C:\> Unregister-ScheduledJob TestJob
```

此命令會刪除本機電腦上的 TestJob 排程工作。

### 範例 2：刪除所有排程工作

```
PS C:\> Get-ScheduledJob | Unregister-ScheduledJob -Force
PS C:\> Unregister-ScheduledJob -Name "*" -Force
```

此範例顯示兩個不同的命令，這些命令會刪除本機電腦上的所有排程工作。

第一個命令會使用 Get-ScheduledJob Cmdlet 來取得電腦上的所有排程工作。
管線運算子 (|) 會傳送排程工作至 **Unregister-ScheduleJob** ，此 Cmdlet 會將它們刪除。

第二個命令使用 *Unregister-ScheduledJob* 的 **Name** 參數搭配全部 (*) 的值來刪除所有排程工作。

這兩個命令都使用 *Force* 參數，此參數會刪除排程工作，即使工作的執行個體在執行中。

### 範例 3：刪除遠端電腦上的排程工作

```
PS C:\> Invoke-Command -ComputerName "Server01" { Unregister-ScheduledJob -Name "Test*"}
```

此命令會刪除 Server01 遠端電腦上名稱開頭為 Test 的排程工作。
此命令會使用 Invoke-Command Cmdlet，在 Server02 電腦上執行 **Unregister-ScheduledJob** 命令。

## PARAMETERS

### -Force
刪除排程工作，即使工作的執行個體正在執行。
根據預設值， **Unregister-ScheduledJob** 不會中斷執行中的工作。

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

### -Id
刪除具有所指定識別碼 (ID) 的排程工作。
輸入電腦上之排程工作的識別碼。

```yaml
Type: System.Int32[]
Parameter Sets: DefinitionId
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
您也可以使用管線將 **ScheduledJob** 物件傳送至 **Unregister-JobTrigger** 。

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition[]
Parameter Sets: Definition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name
刪除具有所指定名稱的排程工作。
輸入電腦上一或多個排程工作的名稱。
支援萬用字元。

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

### Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
您可以使用管線傳送排程工作至 Unregister-ScheduledJob

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
