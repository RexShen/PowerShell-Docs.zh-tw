---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/unregister-event?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-Event
ms.openlocfilehash: b132e842167bb6684519bfd196a3f4a03d078a62
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201975"
---
# Unregister-Event

## 概要
取消事件訂閱。

## SYNTAX

### BySource (預設值)

```
Unregister-Event [-SourceIdentifier] <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ById

```
Unregister-Event [-SubscriptionId] <Int32> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
**Unregister-Event** Cmdlet 會取消使用 Register-EngineEvent、Register-ObjectEvent 或 Register-WmiEvent Cmdlet 建立的事件訂閱。

取消事件訂閱時，會從工作階段刪除事件訂閱者，也不會再將訂閱的事件新增至事件佇列。
當您取消訂閱使用 New-Event Cmdlet 建立的事件時，也會從工作階段刪除新的事件。

**Unregister-Event** 不會從事件佇列刪除事件。
若要刪除事件，請使用 Remove-Event Cmdlet。

## 範例

### 範例 1︰依來源識別碼取消事件訂閱

```
PS C:\> Unregister-Event -SourceIdentifier "ProcessStarted"
```

此命令會取消來源識別碼為 ProcessStarted 的事件訂閱。

若要尋找事件的來源識別碼，請使用 Get-Event Cmdlet。
若要尋找事件訂閱的來源識別碼，請使用 **Get-EventSubscriber** Cmdlet。

### 範例 2︰依訂閱識別碼取消事件訂閱

```
PS C:\> Unregister-Event -SubscriptionId 2
```

此命令會取消訂閱識別碼為 2 的事件訂閱。

若要尋找事件訂閱的訂閱識別碼，請使用 **Get-EventSubscriber** Cmdlet。

### 範例 3︰取消所有事件訂閱

```
PS C:\> Get-EventSubscriber -Force | Unregister-Event -Force
```

此命令會取消工作階段中的所有事件訂閱。

此命令會使用 **Get-EventSubscriber** Cmdlet 取得工作階段中的所有事件訂閱者物件，包括使用事件註冊 Cmdlet 之 *SupportEvent* 參數隱藏的訂閱者。

它會使用管線運算子 (|) 將訂閱者物件傳送給 **Unregister-Event** ，這會將它們從工作階段中刪除。
若要完成工作， **Unregister-Event** 中也需有 *Force* 參數。

## PARAMETERS

### -Force
取消所有事件訂閱，包括使用 **Register-ObjectEvent** 、 **Register-WmiEvent** 及 **Register-EngineEvent** 的 *SupportEvent* 參數隱藏的訂閱。

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

### -SourceIdentifier
指定此 Cmdlet 取消事件訂閱的來源識別碼。

每個命令中必須包含 *SourceIdentifier* 或 *SubscriptionId* 參數。

```yaml
Type: System.String
Parameter Sets: BySource
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SubscriptionId
指定此 Cmdlet 取消事件訂閱的來源識別碼 ID。

每個命令中必須包含 *SourceIdentifier* 或 *SubscriptionId* 參數。

```yaml
Type: System.Int32
Parameter Sets: ById
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
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

### System.Management.Automation.PSEventSubscriber
您可以使用管線將輸出從 Get-EventSubscriber 傳送至 **Unregister-Event** 。

## 輸出

### 無
此 Cmdlet 不會傳回任何輸出。

## 注意

* 事件、事件訂閱與事件佇列僅存在目前工作階段中。 若關閉目前工作階段，便會捨棄事件佇列，並取消事件訂閱。

  **Unregister-Event** 無法刪除使用 New-Event Cmdlet 建立的事件，除非您已經使用 **Register-EngineEvent** Cmdlet 訂閱事件。
若要從工作階段刪除自訂事件，您必須以程式設計方式將它移除，或關閉工作階段。

*

## 相關連結

[Get-Event](Get-Event.md)

[Get-EventSubscriber](Get-EventSubscriber.md)

[New-Event](New-Event.md)

[Register-EngineEvent](Register-EngineEvent.md)

[Register-ObjectEvent](Register-ObjectEvent.md)

[Remove-Event](Remove-Event.md)

[Unregister-Event](Unregister-Event.md)

[Wait-Event](Wait-Event.md)
