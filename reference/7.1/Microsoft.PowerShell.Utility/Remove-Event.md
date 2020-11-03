---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-event?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Event
ms.openlocfilehash: 2ef1125320141d0a16a2a0120560efbe65017b4a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202748"
---
# Remove-Event

## 概要
從事件佇列中刪除事件。

## SYNTAX

### BySource (預設值)

```
Remove-Event [-SourceIdentifier] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByIdentifier

```
Remove-Event [-EventIdentifier] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
**Remove 事件** Cmdlet 會從目前會話中的事件佇列刪除事件。

這個 Cmdlet 只會刪除目前在佇列中的事件。
若要取消事件登錄或取消訂閱，請使用 Unregister-Event Cmdlet。

## 範例

### 範例 1︰依來源識別碼移除事件

```
PS C:\> Remove-Event -SourceIdentifier "ProcessStarted"
```

這個命令會從事件佇列中刪除來源識別碼為 Process Started 的事件。

### 範例 2︰依事件識別碼移除事件

```
PS C:\> Remove-Event -EventIdentifier 30
```

這個命令會從事件佇列中刪除事件識別碼為 30 的事件。

### 範例 3：移除所有事件

```
PS C:\> Get-Event | Remove-Event
```

這個命令會從事件佇列中刪除所有事件。

## PARAMETERS

### -EventIdentifier
指定 Cmdlet 要刪除之事件的事件識別碼。
每個命令中都需要 *EventIdentifier* 或 *SourceIdentifier* 參數。

```yaml
Type: System.Int32
Parameter Sets: ByIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SourceIdentifier
指定此 Cmdlet 從中刪除事件之來源的來源識別碼。
不允許使用萬用字元。
每個命令中都需要 *EventIdentifier* 或 *SourceIdentifier* 參數。

```yaml
Type: System.String
Parameter Sets: BySource
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

### System.Management.Automation.PSEventArgs
您可以透過管線將事件從 Get-Event 傳送至 **移除事件** 。

## 輸出

### 無
此 Cmdlet 不會產生任何輸出。

## 注意

* 事件、事件訂閱與事件佇列僅存在目前工作階段中。 若關閉目前工作階段，便會捨棄事件佇列，並取消事件訂閱。

*

## 相關連結

[Get-Event](Get-Event.md)

[New-Event](New-Event.md)

[Register-EngineEvent](Register-EngineEvent.md)

[Register-ObjectEvent](Register-ObjectEvent.md)

[Remove-Event](Remove-Event.md)

[Unregister-Event](Unregister-Event.md)

[Wait-Event](Wait-Event.md)

