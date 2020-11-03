---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-uptime?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Uptime
ms.openlocfilehash: 999ef16ef3065c26dc1d51e49c5ba5793af7db4a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204583"
---
# Get-Uptime

## 概要
取得自上一次開機之後的 **TimeSpan** 。

## SYNTAX

### Timespan (預設) 

```
Get-Uptime [<CommonParameters>]
```

### 因為

```
Get-Uptime [-Since] [<CommonParameters>]
```

## DESCRIPTION

此 Cmdlet 會傳回自上次開機作業系統之後經過的時間。

`Get-Uptime`Cmdlet 是在 PowerShell 6.0 中引進。

## 範例

### 範例 1-顯示自上次開機後的時間

```powershell
Get-Uptime
```

```Output
Days              : 9
Hours             : 0
Minutes           : 9
Seconds           : 45
Milliseconds      : 0
Ticks             : 7781850000000
TotalDays         : 9.00677083333333
TotalHours        : 216.1625
TotalMinutes      : 12969.75
TotalSeconds      : 778185
TotalMilliseconds : 778185000
```

### 範例 2-顯示上次開機的時間

```powershell
Get-Uptime -Since
```

```Output
Tuesday, June 18, 2019 2:34:56 PM
```

## PARAMETERS

### -自

讓指令程式傳回代表作業系統上次開機時間的 **日期時間** 物件。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Since
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

### 無

## 輸出

### System.TimeSpan

如果未使用任何參數，這就是預設的傳回型別。

### System.DateTime

使用 **自** 參數時，會傳回此類型。

> [!NOTE]
> 如果啟用 [Windows 快速啟動]，Windows 不會更新儲存在 **LastBootUpTime** 中的值。 若要停用快速啟動，請執行下列命令： `Powercfg -h off` 。
>
> 如需有關 Windows 快速啟動的詳細資訊，請參閱 [從休眠喚醒開始區分快速啟動](/windows-hardware/drivers/kernel/distinguishing-fast-startup-from-wake-from-hibernation)。

## 注意

在 Windows 上，傳回的值與 WMI 中 **Win32_OperatingSystem** 類別的 **LastBootUpTime** 屬性相同。

## 相關連結

[Win32_OperatingSystem](/windows/win32/cimwin32prov/win32-operatingsystem#properties)
