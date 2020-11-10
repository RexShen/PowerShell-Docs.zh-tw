---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 4/30/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-date?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Date
ms.openlocfilehash: 36e49d36ffe7e4000926cf821767dfb158efcf46
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387969"
---
# Set-Date

## 概要
將電腦的系統時間變更為您指定的時間。

## SYNTAX

### Date (預設值)

```
Set-Date [-Date] <DateTime> [-DisplayHint <DisplayHintType>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Adjust

```
Set-Date [-Adjust] <TimeSpan> [-DisplayHint <DisplayHintType>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

此 `Set-Date` Cmdlet 會將電腦上的系統日期和時間變更為您指定的日期和時間。
您可以輸入字串或將 **DateTime** 或 **TimeSpan** 物件傳遞給，以指定新的日期和/或時間 `Set-Date` 。 若要指定新的日期或時間，請使用 **date** 參數。
若要指定變更間隔，請使用 [ **調整** ] 參數。

## 範例

### 範例1：將三天新增至系統日期

此命令會將目前的系統日期增加 3 天。
它不會影響時間。
命令使用 **date** 參數指定日期。

Cmdlet 會傳回 `Get-Date` 目前的日期做為 **DateTime** 物件。 **Datetime** 物件的 **AddDays** 方法會將指定的天數 (3) 新增至目前的 **日期時間** 物件。

```powershell
Set-Date -Date (Get-Date).AddDays(3)
```

### 範例2：將系統時鐘設定回10分鐘

此範例會將目前的系統時間設定為10分鐘。

[ **調整** ] 參數可讓您指定變更間隔 (減去十分鐘，以地區設定的標準時間格式) 。

**DisplayHint** 參數會指示 PowerShell 只顯示時間，但不會影響傳回的 **DateTime** 物件 `Set-Date` 。

```powershell
Set-Date -Adjust -0:10:0 -DisplayHint Time
```

### 範例3：將日期和時間設定為變數值

這些命令會將本機電腦上的系統日期和時間變更為儲存在變數中的日期和時間 `$T` 。 第一個命令會取得日期並將其儲存在中 `$T` 。

第二個命令使用 **Date** 參數將 **DateTime** 物件傳送 `$T` 至 `Set-Date` Cmdlet。

```powershell
$T = Get-Date
Set-Date -Date $T
```

### 範例4：將90分鐘新增至系統時鐘

這些命令將本機電腦上的系統時間增加 90 分鐘。

第一個命令會使用 `New-TimeSpan` Cmdlet 來建立具有90分鐘間隔的 **TimeSpan** 物件，並將它儲存在變數中 `$90mins` 。

第二個命令使用的 **調整** 參數 `Set-Date` ，將日期調整為變數中 **TimeSpan** 物件的值 `$90mins` 。

```powershell
$90mins = New-TimeSpan -Minutes 90
Set-Date -Adjust $90mins
```

## PARAMETERS

### -Adjust

指定此 Cmdlet 會從目前的日期和時間加上或減去的值。
可以為您的地區設定輸入標準日期和時間格式的調整，或使用 [ **調整** ] 參數將 **TimeSpan** 物件從傳遞 `New-TimeSpan` 至 `Set-Date` 。

```yaml
Type: System.TimeSpan
Parameter Sets: Adjust
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Date

將日期和時間變更為指定值。
您可以簡短的日期格式輸入新日期，並以您地區設定的標準時間格式輸入時間。 或者，您可以從傳遞 **DateTime** 物件 `Get-Date` 。

如果您指定日期而非時間，則會將 `Set-Date` 時間變更為指定日期的午夜。 如果您只指定時間，則不會變更日期。

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -DisplayHint

指定要顯示日期和時間的哪些元素。此參數可接受的值包括：

- **日期** -只顯示日期。
- **時間** -只顯示時間。
- **DateTime** ：顯示日期和時間。

此參數只會影響顯示。
它不會影響抓取的 **DateTime** 物件 `Get-Date` 。

```yaml
Type: Microsoft.PowerShell.Commands.DisplayHintType
Parameter Sets: (All)
Aliases:
Accepted values: Date, Time, DateTime

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

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### System.DateTime

您可以使用管線將日期傳送至 `Set-Date` 。

## 輸出

### System.DateTime

`Set-Date` 傳回物件，表示它所設定的日期。

## 注意

- 變更電腦上的日期和時間時，請小心使用此 Cmdlet。 變更可能會導致電腦無法接收日期或時間觸發的全系統事件和更新。 使用 **WhatIf** 並 **確認** 參數，以避免發生錯誤。
- 您可以使用標準的 .NET 方法搭配搭配使用的 **DateTime** 和 **TimeSpan** 物件 `Set-Date` ，例如 **AddDays** 、 **AddMonths** 和 **FromFileTime** 。 如需詳細資訊，請參閱 [DateTime 方法](/dotnet/api/system.datetime) 和

  .NET SDK 中的[TimeSpan 方法](/dotnet/api/system.timespan)。

## 相關連結

[取得日期](Get-Date.md)

[New-TimeSpan](New-TimeSpan.md)
