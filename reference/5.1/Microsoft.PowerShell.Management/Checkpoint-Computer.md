---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/checkpoint-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Checkpoint-Computer
ms.openlocfilehash: 61f8d626cd45cfe47f0e65a3043696a01c97ca20
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204091"
---
# Checkpoint-Computer

## 概要
在本機電腦上建立系統還原點。

## SYNTAX

```
Checkpoint-Computer [-Description] <String> [[-RestorePointType] <String>] [<CommonParameters>]
```

## DESCRIPTION

`Checkpoint-Computer`Cmdlet 會在本機電腦上建立系統還原點。

`Checkpoint-Computer`只有用戶端作業系統（例如 Windows 8、windows 7、Windows Vista 和 WINDOWS XP）才支援系統還原點和 Cmdlet。

從 Windows 8 開始， `Checkpoint-Computer` 每天不能建立一個以上的檢查點。

## 範例

### 範例 1︰建立系統還原點

```powershell
Checkpoint-Computer -Description "Install MyApp"
```

此命令建立名為 Install MyApp 的系統還原點。
它使用預設的 APPLICATION_INSTALL 還原點類型。

### 範例 2︰建立 MODIFY_SETTINGS 系統還原點

```powershell
Checkpoint-Computer -Description "ChangeNetSettings" -RestorePointType MODIFY_SETTINGS
```

此命令建立名為 "ChangeNetSettings" 的 MODIFY_SETTINGS 系統還原點。

## PARAMETERS

### -Description

指定還原點的描述性名稱。
這是必要參數。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RestorePointType

指定還原點的類型。
預設為 APPLICATION_INSTALL。

此參數可接受的值為：

- APPLICATION_INSTALL
- APPLICATION_UNINSTALL
- DEVICE_DRIVER_INSTALL
- MODIFY_SETTINGS
- CANCELLED_OPERATION

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: RPT
Accepted values: APPLICATION_INSTALL, APPLICATION_UNINSTALL, DEVICE_DRIVER_INSTALL, MODIFY_SETTINGS, CANCELLED_OPERATION

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### 無

您無法透過管道傳送物件至 `Checkpoint-Computer` 。

## 輸出

### 無

此 Cmdlet 不會產生任何輸出。

## 注意

- 此 Cmdlet 會使用 **SystemRestore** 類別的 **CreateRestorePoint** 方法搭配 **BEGIN_SYSTEM_CHANGE** 事件。
- 從 Windows 8 開始， `Checkpoint-Computer` 每天不能建立超過一個系統還原點。 如果您嘗試在 24 小時的期間內建立新的還原點，Windows PowerShell 會產生下列錯誤：

  `"A new system restore point cannot be created because one has already been created within the past 24 hours.
  Please try again later."`

## 相關連結

[Disable-ComputerRestore](Disable-ComputerRestore.md)

[Enable-ComputerRestore](Enable-ComputerRestore.md)

[Get-ComputerRestorePoint](Get-ComputerRestorePoint.md)

[Restore-Computer](Restore-Computer.md)
