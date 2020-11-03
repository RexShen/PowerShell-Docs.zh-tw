---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-uiculture?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-UICulture
ms.openlocfilehash: cd5bbcae124b1c24438d2821c4da9d71a22d38a2
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "93200921"
---
# Get-UICulture

## 概要
取得作業系統中目前的 UI 文化特性設定。

## SYNTAX

```
Get-UICulture [<CommonParameters>]
```

## DESCRIPTION

`Get-UICulture`Cmdlet 會取得 Windows 的目前使用者介面 (UI) 文化特性設定的相關資訊。
UI 文化特性會決定要將哪些文字字串用於使用者介面元素，例如功能表和訊息。

您也可以使用 `Get-Culture` Cmdlet，此 Cmdlet 會取得系統上目前的文化特性。
文化特性會決定項目 (例如數字、貨幣及日期) 的顯示格式。

## 範例

### 範例1：取得 UI 文化特性

```powershell
Get-UICulture
```

這個命令會取得目前的 UI 文化特性資訊。

### 範例2：取得 UI 文化特性並設定結果格式

```powershell
Get-UICulture | Format-List *
```

這個命令會以清單顯示目前 UI 文化特性的所有屬性值。

### 範例3：取得行事曆屬性的值

```powershell
(Get-UICulture).Calendar
```

此命令會顯示目前 UI 文化特性之 **Calendar** 屬性的目前值。
Calendar 只是 UI 文化特性的一個屬性。
若要查看所有屬性，請輸入 `Get-UICulture | Get-Member` 。

### 範例4：取得簡短日期模式

```powershell
(Get-UICulture).DateTimeFormat.ShortDatePattern
```

這個命令會顯示目前 UI 文化特性的簡短日期模式。
若要查看 UI 文化特性之 **DateTimeFormat** 屬性的所有子屬性，請輸入 `(Get-UICulture).DateTimeFormat | gm` 。

## PARAMETERS

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### 無

您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### System.string、VistaCultureInfo、

`Get-UICulture` 傳回代表目前 UI 文化特性的物件。
在 Windows PowerShell 3.0 中，它會傳回 **CultureInfo** 物件。
在 Windows PowerShell 2.0 中，它會傳回 **VistaCultureInfo** 物件。

## 注意

- 您也可以使用 `$PsCulture` 和 `$PsUICulture` 變數。 `$PsCulture`變數會儲存目前文化特性的名稱，而變數會 `$PsUICulture` 儲存目前 UI 文化特性的名稱。

## 相關連結
