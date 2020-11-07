---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-event?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Event
ms.openlocfilehash: 9a66c7ce0d892b7702aab74fc278b20e59d06a98
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94343448"
---
# Get-Event

## 概要
取得事件佇列中的事件。

## SYNTAX

### BySource (預設值)

```
Get-Event [[-SourceIdentifier] <String>] [<CommonParameters>]
```

### ById

```
Get-Event [-EventIdentifier] <Int32> [<CommonParameters>]
```

## DESCRIPTION

Cmdlet 會取得 `Get-Event` 目前會話的 PowerShell 事件佇列中的事件。 您可以取得所有事件，或使用 **EventIdentifier** 或 **SourceIdentifier** 參數來指定事件。

發生事件時，它會新增到事件佇列。 事件佇列包含您已註冊的事件、使用指令程式所建立的事件 `New-Event` ，以及在 PowerShell 結束時引發的事件。 您可以使用 `Get-Event` 或 `Wait-Event` 來取得事件。

這個 Cmdlet 不會從事件檢視器記錄檔取得事件。 若要取得這些事件，請使用 `Get-WinEvent` 或 `Get-EventLog` 。

## 範例

### 範例 1︰取得所有事件

```
PS C:\> Get-Event
```

此命令會取得事件佇列中所有的事件。

### 範例 2︰依來源識別碼取得事件

```
PS C:\> Get-Event -SourceIdentifier "PowerShell.ProcessCreated"
```

此命令會取得 SourceIdentifier 屬性值是 PowerShell.ProcessCreated 的事件。

### 範例 3︰根據事件產生時間取得事件

```
PS C:\> $Events = Get-Event
PS C:\> $Events[0] | Format-List -Property *
ComputerName     :
RunspaceId       : c2153740-256d-46c0-a57c-b805917d1b7b
EventIdentifier  : 1
Sender           : System.Management.ManagementEventWatcher
SourceEventArgs  : System.Management.EventArrivedEventArgs
SourceArgs       : {System.Management.ManagementEventWatcher, System.Management.EventArrivedEventArgs}
SourceIdentifier : ProcessStarted
TimeGenerated    : 11/13/2008 12:09:32 PM
MessageData      : PS C:\> Get-Event | Where {$_.TimeGenerated -ge "11/13/2008 12:15:00 PM"}
ComputerName     :
RunspaceId       : c2153740-256d-46c0-a57c-b8059325d1a0
EventIdentifier  : 1
Sender           : System.Management.ManagementEventWatcher
SourceEventArgs  : System.Management.EventArrivedEventArgs
SourceArgs       : {System.Management.ManagementEventWatcher, System.Management.EventArrivedEventArgs}
SourceIdentifier : ProcessStarted
TimeGenerated    : 11/13/2008 12:15:00 PM
MessageData      :
```

這個範例示範如何使用 SourceIdentifier 以外的屬性來取得事件。

第一個命令會取得事件佇列中的所有事件，並將它們儲存在 `$Events` 變數中。

第二個命令會使用陣列標記法，取得變數中陣列中的第一個 (0 索引) 事件 `$Events` 。 此命令會使用管線運算子 (`|`) 將事件傳送至 `Format-List` 命令，此命令會在清單中顯示事件的所有屬性。 這可讓您檢視事件物件的屬性。

第三個命令會顯示如何使用指令 `Where-Object` 程式，以根據產生的時間取得事件。

### 範例 4︰依識別碼取得事件

```
PS C:\> Get-Event -EventIdentifier 2
```

此命令取得事件識別碼為 2 的事件。

## PARAMETERS

### -EventIdentifier

指定此 Cmdlet 用以取得事件的事件識別碼。

```yaml
Type: System.Int32
Parameter Sets: ById
Aliases: Id

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SourceIdentifier

指定此 Cmdlet 用以取得事件的來源識別碼。 預設為事件佇列中的所有事件。 不允許使用萬用字元。

```yaml
Type: System.String
Parameter Sets: BySource
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### None

您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### System.Management.Automation.PSEventArgs

`Get-Event` 傳回每個事件的 **PSEventArgs** 物件。 如果要查看此物件的描述，請輸入 `Get-Help Get-Event -Full`，並參閱說明主題的＜附註＞一節。

## 注意

Linux 或 macOS 平臺上沒有可用的事件來源。

事件、事件訂閱與事件佇列僅存在目前工作階段中。 若關閉目前工作階段，便會捨棄事件佇列，並取消事件訂閱。

Cmdlet 會傳回 `Get-Event` **PSEventArgs** 物件， ( **PSEventArgs** ) 具有下列屬性：

- ComputerName。 發生事件之電腦的名稱。 從遠端電腦轉送事件時，才會填入這個屬性值。

- RunspaceId。 可唯一識別發生事件之工作階段的 GUID。 從遠端電腦轉送事件時，才會填入這個屬性值。

- EventIdentifier。 可唯一識別目前工作階段中之事件通知的整數 (Int32)。

- Sender。 產生事件的物件。 在 **Action** 參數的值中， `$Sender` 自動變數包含傳送者物件。

- SourceEventArgs。 衍生自 EventArgs 的第一個參數 (如果存在的話)。 例如，在計時器經過的事件中，簽章的表單物件為 **timers.elapsedeventargs** e， **SourceEventArgs** 屬性會包含 **timers.elapsedeventargs** 。 在 **Action** 參數的值中， `$EventArgs` 自動變數包含此值。

- SourceArgs。 原始事件簽章的所有參數。 若為標準事件簽章，表示傳送者 `$Args[0]` ，並 `$Args[1]` 代表 **SourceEventArgs** 。 在 **Action** 參數的值中， `$Args` 自動變數包含此值。

- SourceIdentifier。 識別事件訂閱的字串。 在 **Action** 參數的值中，自動變數的 **SourceIdentifier** 屬性會 `$Event` 包含此值。

- TimeGenerated。 代表產生該事件時間的 **DateTime** 物件。
  在 **Action** 參數的值中，自動變數的 **TimeGenerated** 屬性會 `$Event` 包含此值。

- MessageData. 與事件訂閱相關聯的資料。 使用者註冊事件時，會指定此資料。 在 **Action** 參數的值中，自動變數的 **MessageData** 屬性會 `$Event` 包含此值。

## 相關連結

[New-Event](New-Event.md)

[Register-EngineEvent](Register-EngineEvent.md)

[Register-ObjectEvent](Register-ObjectEvent.md)

[Remove-Event](Remove-Event.md)

[Unregister-Event](Unregister-Event.md)

[Wait-Event](Wait-Event.md)
