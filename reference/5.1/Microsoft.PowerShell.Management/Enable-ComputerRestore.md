---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/enable-computerrestore?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-ComputerRestore
ms.openlocfilehash: f9616a7f9af4dd2fa45e150bb64eef65427b4947
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204032"
---
# Enable-ComputerRestore

## 概要
在指定的檔案系統磁碟機上啟用系統還原功能。

## SYNTAX

```
Enable-ComputerRestore [-Drive] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
**Enable-ComputerRestore** Cmdlet 會開啟一或多個檔案系統磁碟機上的系統還原功能。
如此一來，您可以使用工具 (例如 Restore-Computer Cmdlet) 將電腦還原成先前的狀態。

依預設，所有適合的磁碟機上都已啟用系統還原，但是您可以停用它，像是使用 Disable-ComputerRestore Cmdlet。
如果要在任一磁碟機上啟用 (或重新啟用) 系統還原，則必須優先或同時在系統磁碟機上將它啟用。
如果要尋找每個磁碟機的系統還原狀態，請使用 Rstrui.exe。

只有用戶端作業系統 (如 Windows 7、Windows Vista 和 Windows XP) 才支援系統還原點和 ComputerRestore Cmdlet。

## 範例

### 範例 1︰啟用指定磁碟機的系統還原

```
PS C:\> Enable-ComputerRestore -Drive "C:\"
```

此命令會啟用本機電腦 Ｃ: 磁碟機上的系統還原。

### 範例 2︰啟用多個磁碟機的系統還原

```
PS C:\> Enable-ComputerRestore -Drive "C:\", "D:\"
```

此命令會啟用本機電腦 Ｃ: 與 D: 磁碟機上的系統還原。

## PARAMETERS

### -Drive
指定檔案系統磁碟機。
輸入一或多個檔系統磁碟機號，並在後面加上冒號和反斜線，並以引號括住，例如 C：\或 D:\。
這是必要參數。

您無法使用這個 Cmdlet 來啟用遠端網路磁碟機上的系統還原，即使該磁碟機對應本機電腦也一樣，也無法在不適合系統還原的磁碟機 (例如外接式磁碟機) 上啟用系統還原。

如果要在任一磁碟機上啟用系統還原，必須優先或同時在系統磁碟機上將它啟用。

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
您無法使用管線將物件傳送至此 Cmdlet。

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

[Disable-ComputerRestore](Disable-ComputerRestore.md)

[Get-ComputerRestorePoint](Get-ComputerRestorePoint.md)

[Restart-Computer](Restart-Computer.md)

[Restore-Computer](Restore-Computer.md)
