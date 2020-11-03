---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restore-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restore-Computer
ms.openlocfilehash: 824e9a24693c7a7de01358a048a0df55be333263
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203524"
---
# Restore-Computer

## 概要
在本機電腦上啟動系統還原。

## SYNTAX

```
Restore-Computer [-RestorePoint] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
**Restore-Computer** Cmdlet 會將本機電腦還原到指定的系統還原點。

**Restore-Computer** 會重新啟動電腦。
還原會在重新啟動操作期間完成。

只有用戶端作業系統 (如 Windows 7、Windows Vista 和 Windows XP) 才支援系統還原點和 **Restore-Computer** 。

## 範例

### 範例 1︰還原本機電腦

```
PS C:\> Restore-Computer -RestorePoint 253
```

此命令將本機電腦還原到序號為 253 的還原點。

### 範例 2︰透過確認還原本機電腦

```
PS C:\> Restore-Computer -RestorePoint 255 -Confirm
Confirm
Are you sure you want to perform this action?
Performing operation "Restore-Computer" .
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

此命令將本機電腦還原到序號為 255 的還原點。
它使用 *Confirm* 參數以在實際執行操作之前先提示使用者。

### 範例 3︰ 還原電腦並檢查狀態

```
PS C:\> Get-ComputerRestorePoint
PS C:\> Restore-Computer -RestorePoint 255
PS C:\> Get-ComputerRestorePoint -LastStatus
```

這些命令執行系統還原，然後檢查其狀態。

第一個命令使用 **Get-ComputerRestorePoint** 取得本機電腦上的還原點。

第二個命令將電腦還原到序號為 255 的還原點。

第三個命令使用 *Get-ComputerRestorePoint* Cmdlet 的 *LastStatus* 參數檢查還原操作的狀態。
由於 **Restore-Computer** 會強制重新啟動，因此在電腦重新啟動後會輸入這個命令。

## PARAMETERS

### -RestorePoint
指定還原點的序號。
若要尋找序號，請使用 Get-ComputerRestorePoint Cmdlet。
這是必要參數。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: SequenceNumber, SN, RP

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

### 無
您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### 無
此 Cmdlet 不會產生任何輸出。

## 注意

* 若要在 Windows Vista 和更新版本的 Windows 作業系統上執行 Restore-Computer 命令，請使用 [以系統管理員身分執行] 選項開啟 Windows PowerShell。
* 此 Cmdlet 會使用 Windows Management Instrumentation (WMI) **SystemRestore** 類別。

## 相關連結

[Checkpoint-Computer](Checkpoint-Computer.md)

[Disable-ComputerRestore](Disable-ComputerRestore.md)

[Enable-ComputerRestore](Enable-ComputerRestore.md)

[Get-ComputerRestorePoint](Get-ComputerRestorePoint.md)

[Restart-Computer](Restart-Computer.md)
