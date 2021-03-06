---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/enable-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-ScheduledJob
ms.openlocfilehash: 757402a348a6b694d2f2aee53053a1b7615dbb53
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203011"
---
# Enable-ScheduledJob

## 概要
啟用排程工作。

## SYNTAX

### Definition (預設值)

```
Enable-ScheduledJob [-InputObject] <ScheduledJobDefinition> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### DefinitionId

```
Enable-ScheduledJob [-Id] <Int32> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### DefinitionName

```
Enable-ScheduledJob [-Name] <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
**Enable-ScheduledJob** Cmdlet 會重新啟用已停用的排程工作 (例如使 用Disable-ScheduledJob Cmdlet 停用的排程工作)。
已啟用的工作會在被觸發時自動執行。

若要啟用排程工作， **register-scheduledjob 指令程式** 會將排程工作的 Enabled 屬性設定為 $True。

**Enabled-ScheduledJob** 為 Windows PowerShell 內含之 **PSScheduledJob** 模組中其中一個工作排程 Cmdlet 的集合。

如需排程工作的詳細資訊，請參閱 PSScheduledJob 模組中的「關於」主題。
匯入 PSScheduledJob 模組，然後輸入：`Get-Help about_Scheduled*`，或參閱 about_Scheduled_Jobs。

此 Cmdlet 是在 Windows PowerShell 3.0 中引進。

## 範例

### 範例 1：啟用排程工作

```
PS C:\> Enable-ScheduledJob -ID 2 -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    True
```

此命令會啟用本機電腦上識別碼為 2 的排程工作。
輸出會顯示命令的效果。

### 範例2：啟用所有排程工作

```
PS C:\> Get-ScheduledJob | Enable-ScheduledJob -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          ArchiveProje... {}              C:\Scripts\Archive-DxProjects.ps1        True
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    True
4          Test-HelpFiles  {1}             .\Test-HelpFiles.ps1                     True
5          TestJob         {1, 2}          .\Run-AllTests.ps1                       True
```

此命令會啟用本機電腦上的所有排程工作。
它會使用 Get-ScheduledJob Cmdlet 來取得所有排程工作，並使用 **Enable-ScheduledJob** Cmdlet 來將它們啟用。

**Enable-ScheduledJob** 不會產生警告或錯誤 (若您啟用已啟用的排程工作)，因此您可以在不指定任何條件的情況下啟用所有排程工作。

### 範例 3：啟用選取的排程工作

```
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption | Where-Object {$_.RunWithoutNetwork} | ForEach-Object {Enable-ScheduledJob -InputObject $_.JobDefinition}
```

此命令會啟用不需要網路連線的排程工作。

命令會使用 Get-ScheduledJob Cmdlet，來取得電腦上的所有排程工作。
管線運算子會傳送排程工作至 Get-ScheduledJobOption Cmdlet，此 Cmdlet 會取得每個排程工作的工作選項。
每個工作選項物件都具有 JobDefinition 屬性，該屬性包含關聯的排程工作。
JobDefinition 屬性會被用來完成命令。

命令使用管線運算子 (|) 將工作選項傳送至 Where-Object Cmdlet，它會選取排程工作選項物件，其中 **RunWithoutNetwork** 屬性的值為 True ($true) 。
另一個管線運算子會將選取的排程工作選項物件傳送至 ForEach-Object Cmdlet，它會使用每個工作選項物件的 JobDefinition 屬性值，在排程工作上執行 **Enable-ScheduledJob** 命令。

### 範例 4：啟用遠端電腦上的排程工作

```
PS C:\> Invoke-Command -ComputerName "Srv01,Srv10" -ScriptBlock {Enable-ScheduledJob -Name "Inventory"}
```

此命令會啟用兩部遠端電腦 (Srv01 與 Srv10) 上名稱中包含 "test" 的排程工作。

此命令會使用 Invoke-Command Cmdlet 在 Srv01 與 Srv10 電腦上執行 **Enable-ScheduledJob** 命令。
此命令使用 *Enable-ScheduledJob* 的 **Name** 參數來啟用每部電腦上的 Inventory 排程工作。

## PARAMETERS

### -Id
啟用具有所指定識別碼 (ID) 的排程工作。
輸入排程工作的識別碼。

```yaml
Type: System.Int32
Parameter Sets: DefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
指定要啟用的排程工作。
輸入包含 **>scheduledjobdefinition** 物件的變數，或輸入可取得 **>scheduledjobdefinition** 物件的命令或運算式，例如 Get-ScheduledJob 命令。
您也可以使用管線將 **ScheduledJobDefinition** 物件傳送至 **Enable-ScheduledJob** 。

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
Parameter Sets: Definition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name
啟用具有所指定名稱的排程工作。
輸入排程工作的名稱。
支援萬用字元。

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: True
Position: 0
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
您可以使用管線將排程工作傳送到 **Enable-ScheduledJob** 。

## 輸出

### 無或 Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
若使用 **Passthru** 參數， **Enable-ScheduledJob** 會傳回已啟用的排程工作。
否則，此 Cmdlet 不會產生任何輸出。

## 注意

* **Enable-ScheduledJob** 不會產生警告或錯誤 (若使用它來啟用已啟用的排程工作)。

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
