---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/disable-computerrestore?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-ComputerRestore
ms.openlocfilehash: 941829c3caa0f6bb2f5712dda9eb7d8c36908062
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204035"
---
# Disable-ComputerRestore

## 概要
在指定的檔案系統磁碟機上停用系統還原功能。

## SYNTAX

```
Disable-ComputerRestore [-Drive] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
**Enable-computerrestore** Cmdlet 會關閉一或多個檔案系統磁片磁碟機上的系統還原功能。
因此，嘗試還原電腦不會影響指定的磁碟機。

如果要在任一磁碟機上停用系統還原，則必須優先或同時在系統磁碟機上將它停用。

如果要重新啟用系統還原，請使用 Enable-ComputerRestore Cmdlet。
如果要尋找每個磁碟機的系統還原狀態，請使用 Rstrui.exe。

只有用戶端作業系統 (如 Windows 7、Windows Vista 和 Windows XP) 才支援系統還原點和 ComputerRestore Cmdlet。

## 範例

### 範例1：停用指定磁片磁碟機上的系統還原

```
PS C:\> Disable-ComputerRestore -Drive "C:\"
```

此命令會停用 C: 磁碟機上的系統還原 。

### 範例2：停用多個磁片磁碟機上的系統還原

```
PS C:\> Disable-ComputerRestore "C:\", "D:\"
```

此命令會停用 C: 和 D: 磁碟機上的系統還原 。
此命令會使用 *drive* 參數，但會省略磁片磁碟機參數名稱。

## PARAMETERS

### -Drive
指定檔案系統磁碟機。
輸入一或多個檔系統磁碟機號，並在後面加上冒號和反斜線，並以引號括住，例如 C：\或 D:\。
這是必要參數。

您無法使用這個 Cmdlet 來停用遠端網路磁碟機上的系統還原，即使該磁碟機對應本機電腦也一樣，也無法在不適合系統還原的磁碟機 (例如外接式磁碟機) 上停用系統還原。

如果要在任一磁碟機上停用系統還原，必須優先或同時在系統磁碟機上將它停用。

```yaml
Type: System.String[]
Parameter Sets: (All)
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

### 無
您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### 無
此 Cmdlet 不會產生任何輸出。

## 注意

* 若要在 Windows Vista 和更新版本的 Windows 上執行此 Cmdlet，請使用 [以系統管理員身分執行] 選項開啟 Windows PowerShell。

  若要尋找適合系統還原的檔案系統磁片磁碟機，請在 [系統] 的 [主控台] 中，查看 [系統保護] 索引標籤。若要在 Windows PowerShell 中開啟此索引標籤，請輸入 `SystemPropertiesProtection` 。

  此 Cmdlet 會使用 Windows Management Instrumentation (WMI) **SystemRestore** 類別。

*

## 相關連結

[Checkpoint-Computer](Checkpoint-Computer.md)

[Enable-ComputerRestore](Enable-ComputerRestore.md)

[Get-ComputerRestorePoint](Get-ComputerRestorePoint.md)

[Restart-Computer](Restart-Computer.md)

[Restore-Computer](Restore-Computer.md)
