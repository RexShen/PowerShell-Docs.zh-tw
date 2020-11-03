---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 5/1/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-timespan?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-TimeSpan
ms.openlocfilehash: 135b4441490bbee7d8c8e0088080f97a7128af53
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204976"
---
# New-TimeSpan

## 概要
建立 TimeSpan 物件。

## SYNTAX

### Date (預設值)

```
New-TimeSpan [[-Start] <DateTime>] [[-End] <DateTime>] [<CommonParameters>]
```

### 時間

```
New-TimeSpan [-Days <Int32>] [-Hours <Int32>] [-Minutes <Int32>] [-Seconds <Int32>] [<CommonParameters>]
```

## DESCRIPTION

此 `New-TimeSpan` Cmdlet 會建立代表時間間隔的 **TimeSpan** 物件。
您可以使用 **TimeSpan** 物件加上或減去 **DateTime** 物件的時間。

如果沒有參數， `New-TimeSpan` 命令會傳回代表時間間隔為零的 **TimeSpan** 物件。

## 範例

### 範例 1︰建立指定持續期間的 TimeSpan 物件

此命令會建立持續時間為1小時和25分鐘的 **TimeSpan** 物件，並將它儲存在名為的變數中 `$TimeSpan` 。 它會顯示 **TimeSpan** 物件的表示法。

```powershell
$TimeSpan = New-TimeSpan -Hours 1 -Minutes 25
$TimeSpan
```

```Output
Days              : 0
Hours             : 1
Minutes           : 25
Seconds           : 0
Milliseconds      : 0
Ticks             : 51000000000
TotalDays         : 0.0590277777777778
TotalHours        : 1.41666666666667
TotalMinutes      : 85
TotalSeconds      : 5100
TotalMilliseconds : 5100000
```

### 範例 2︰建立某時間間隔的 TimeSpan 物件

此範例建立一個新的 **TimeSpan** 物件，代表命令執行時間和 2010 年 1 月 1 日之間的間隔。

此命令不需要 **Start** 參數，因為 **Start** 參數的預設值是目前的日期和時間。

```powershell
New-TimeSpan -End (Get-Date -Year 2010 -Month 1 -Day 1)
```

### 範例 3︰取得距離目前日期 90 天的日期

```powershell
$90days = New-TimeSpan -Days 90
(Get-Date) + $90days
```

這些命令傳回目前日期後 90 天的日期。

### 範例 4︰探索自檔案更新後的 TimeSpan

此命令會告訴您，自從上一次更新 [about_remote](../Microsoft.PowerShell.Core/About/about_Remote.md) 說明檔以來有多長時間。
您可以在任何檔案或具有 **LastWriteTime** 屬性的任何其他物件上使用此命令格式。

此命令的運作方式是因為的 **啟動** 參數 `New-TimeSpan` 具有 **LastWriteTime** 的別名。 當您使用管線將具有 **LastWriteTime** 屬性的物件傳送至時 `New-TimeSpan` ，PowerShell 會使用 **LastWriteTime** 屬性的值作為 **Start** 參數的值。

```powershell
Get-ChildItem $PSHOME\en-us\about_remote.help.txt | New-TimeSpan
```

```Output
Days              : 321
Hours             : 21
Minutes           : 59
Seconds           : 22
Milliseconds      : 312
Ticks             : 278135623127728
TotalDays         : 321.916230471907
TotalHours        : 7725.98953132578
TotalMinutes      : 463559.371879547
TotalSeconds      : 27813562.3127728
TotalMilliseconds : 27813562312.7728
```

## PARAMETERS

### -Days

指定時間範圍中的天數。
預設值為 0。

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -End

指定時間範圍的結束。
預設值為目前日期和時間。

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases:

Required: False
Position: 1
Default value: Current date and time
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Hours

指定時間範圍中的小時數。
預設值為零。

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Minutes

指定時間範圍中的分鐘數。
預設值為 0。

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Seconds

指定時間範圍的長度 (以秒為單位)。
預設值為 0。

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Start

指定時間範圍的開始。
輸入代表日期和時間的字串，例如 "3/15/09" 或 **DateTime** 物件，例如來自命令的日期和時間 `Get-Date` 。 預設值為目前日期和時間。

您可以使用 **Start** 或其別名 **LastWriteTime** 。
**LastWriteTime** 別名可讓您使用管線將具有 **LastWriteTime** 屬性的物件（例如檔案系統中的檔案 `[System.Io.FileIO]` ）傳送至 **的 Start** 參數 `New-TimeSpan` 。

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases: LastWriteTime

Required: False
Position: 0
Default value: Current date and time
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### System.DateTime

您可以使用管線將代表該開始時間的 **DateTime** 物件傳送至 `New-TimeSpan` 。

## 輸出

### System.TimeSpan

`New-TimeSpan` 傳回代表時間範圍的物件。

## 注意

## 相關連結

[Get-Date](Get-Date.md)

[Set-Date](Set-Date.md)

