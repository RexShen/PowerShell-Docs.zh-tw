---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/disable-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-ScheduledJob
ms.openlocfilehash: a7ea520d7d0365fd0de8c9d0bb767981b68467c6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203024"
---
# Disable-ScheduledJob

## 概要
停用排程工作。

## SYNTAX

### Definition (預設值)

```
Disable-ScheduledJob [-InputObject] <ScheduledJobDefinition> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### DefinitionId

```
Disable-ScheduledJob [-Id] <Int32> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### DefinitionName

```
Disable-ScheduledJob [-Name] <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
**Disable-ScheduledJob** Cmdlet 會暫時停用排程工作。
停用會保留所有工作屬性，而且不會停用工作觸發程序，但會防止排程工作在被觸發時自動啟動。
您可以使用 Start-Job Cmdlet 來啟動已停用的排程工作，或使用已停用的排程工作做為範本。

為停用排程工作， **Disable-ScheduledJob** Cmdlet 會將排程工作的 **Enabled** 屬性設定為 False ($false)。
若要重新啟用排程工作，請使用 Enable-ScheduledJob Cmdlet。

**Disable-ScheduledJob** 為 Windows PowerShell 內含之 **PSScheduledJob** 模組中的其中一個工作排程 Cmdlet 集合。

如需排程工作的詳細資訊，請參閱 PSScheduledJob 模組中的「關於」主題。
匯入 PSScheduledJob 模組，然後輸入：`Get-Help about_Scheduled*`，或參閱 about_Scheduled_Jobs。

此 Cmdlet 是在 Windows PowerShell 3.0 中引進。

## 範例

### 範例 1：停用排程工作

```
PS C:\> Disable-ScheduledJob -ID 2 -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    False
```

此命令會停用本機電腦上識別碼為 2 的排程工作。
輸出會顯示命令的效果。

### 範例 2：停用所有排程工作

```
PS C:\> Get-ScheduledJob | Disable-ScheduledJob -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          ArchiveProje... {}              C:\Scripts\Archive-DxProjects.ps1        False
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    False
4          Test-HelpFiles  {1}             .\Test-HelpFiles.ps1                     False
5          TestJob         {1, 2}          .\Run-AllTests.ps1                       False
```

此命令會停用本機電腦上的所有排程工作。
它會使用 Get-ScheduledJob Cmdlet 來取得所有排程工作，並使用 **Disable-ScheduledJob** Cmdlet 來停用它們。

您可以使用 Enable-ScheduledJob Cmdlet 來重新啟用排程工作，並使用 Start-Job Cmdlet 來執行已停用的排程工作。

**Disable-ScheduledJob** 不會產生警告或錯誤 (若您停用已經停用的排程工作)，因此您可以在不指定任何條件的情況下停用所有排程工作。

### 範例 3：停用選取的排程工作

```
PS C:\> Get-ScheduledJob | Where-Object {!$_.Credential} | Disable-ScheduledJob
```

此命令會停用不包含認證的排程工作。
不包含認證的工作是以建立工作之使用者的權限執行。

命令會使用 Get-ScheduledJob Cmdlet，來取得電腦上的所有排程工作。
管線運算子會將排程工作傳送到 Where-Object Cmdlet，此 Cmdlet 會選取沒有認證的排程工作。
此命令使用 Not (!) 運算子並參照排程工作的 Credential 屬性。
另一個管線運算子會將選取的排程工作傳送到 **Disable-ScheduledJob** Cmdlet，此 Cmdlet 會將排程工作停用。

### 範例 4：停用遠端電腦上的排程工作

```
PS C:\> Invoke-Command -ComputerName Srv01, Srv10 -ScriptBlock {Disable-ScheduledJob -Name TestJob}
```

此命令會停用兩部遠端電腦 (Srv01 與 Srv10) 上的 TestJob 排程工作。

此命令會使用 Invoke-Command Cmdlet，在 Srv01 與 Srv10 電腦上執行 **Disable-ScheduledJob** 命令。
此命令會使用 *Disable-ScheduledJob* 的 **Name** 參數來選取每部電腦上的 TestJob 排程工作。

### 範例 5：依全域識別碼停用排程工作

```
The first command demonstrates one way of finding the GlobalID of a scheduled job. The command uses the Get-ScheduledJob cmdlet to get the scheduled jobs on the computer. A pipeline operator (|) sends the scheduled jobs to the Format-Table cmdlet, which displays the Name, GlobalID, and Command properties of each job in a table.
PS C:\> Get-ScheduledJob | Format-Table -Property Name, GlobalID, Command -Autosize
Name             GlobalId                             Command
----             --------                             -------
ArchiveProjects1 a26a0b3d-b4e6-44d3-8b95-8706ef621f7c C:\Scripts\Archive-DxProjects.ps1
Inventory        3ac37e5d-84c0-4a8f-9661-7e88ebb8f914 \\Srv01\Scripts\Get-FullInventory.ps1
Backup-Scripts   4d0cc6be-c082-48d1-baec-1bd8278f3c81  Copy-Item C:\CurrentScripts\*.ps1 -Destination C:\BackupScripts
Test-HelpFiles   d77020ca-f20d-42be-86c8-fc64df97db90 .\Test-HelpFiles.ps1
Test-HelpFiles   2f1606d2-c6cf-4bef-8b1c-ae36a9cc9934 .\Test-DomainHelpFiles.ps1

The second command uses the  Get-ScheduledJob cmdlet to get the scheduled jobs on the computer. A pipeline operator (|) sends the scheduled jobs to the Where-Object cmdlet, which selects the scheduled job with the specified global ID. Another pipeline operator sends the job to the **Disable-ScheduledJob** cmdlet, which disables it.
PS C:\> Get-ScheduledJob | Where-Object {$_.GlobalID = d77020ca-f20d-42be-86c8-fc64df97db90} | Disable-ScheduledJob
```

此範例顯示如何使用全域識別碼來停用排程工作。
排程工作的 GlobalID 屬性值是唯一識別碼 (GUID)。
需要進行精確處理 (例如，當您想要停用多部電腦上的排程工作) 時，請使用 GlobalID 值。

## PARAMETERS

### -Id
停用具有所指定識別碼 (ID) 的排程工作。
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
指定要停用的排程工作。
輸入包含 **ScheduledJobDefinition** 物件的變數，或輸入可取得 **ScheduledJobDefinition** 物件的命令或運算式，例如 Get-ScheduledJob 命令。
您也可以使用管線將 **ScheduledJobDefinition** 物件傳送至 **Disable-ScheduledJob** 。

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
停用具有所指定名稱的排程工作。
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
您可以使用管線將排程工作傳送到 **Disable-ScheduledJob** 。

## 輸出

### 無或 Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
若使用 **Passthru** 參數， **Disable-ScheduledJob** 會傳回已停用的排程工作。
否則，此 Cmdlet 不會產生任何輸出。

## 注意

* 若您使用 **Disable-ScheduledJob** 來停用已經停用的排程工作，它就不會產生警告或錯誤。

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
