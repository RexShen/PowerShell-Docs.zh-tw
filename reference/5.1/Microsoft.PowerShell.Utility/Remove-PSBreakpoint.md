---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-psbreakpoint?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSBreakpoint
ms.openlocfilehash: b12913cd10c2c505322c1f922a05ecc98987e830
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203164"
---
# Remove-PSBreakpoint

## 概要
從目前的主控台刪除中斷點。

## SYNTAX

### 中斷點 (預設值)

```
Remove-PSBreakpoint [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Id

```
Remove-PSBreakpoint [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
**Remove-PSBreakpoint** Cmdlet 會刪除中斷點。
輸入中斷點物件或中斷點識別碼。

當您移除中斷點時，中斷點物件就無法再使用或運作。
如果您將中斷點物件儲存在變數中，參考仍然存在，但中斷點無法運作。

**Remove-PSBreakpoint** 是設計來對 Windows PowerShell 指令碼進行偵錯的數個 Cmdlet 其中之一。
如需有關 Windows PowerShell 偵錯工具的詳細資訊，請參閱 about_Debuggers。

## 範例

### 範例 1：移除所有中斷點

```
PS C:\> Get-PSBreakpoint | Remove-PSBreakpoint
```

這個命令會刪除目前主控台中的所有中斷點。

### 範例 2：移除指定的中斷點

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Variable "Name"
PS C:\> $B | Remove-PSBreakpoint
```

此命令會刪除中斷點。

第一個命令使用 Set-PSBreakpoint Cmdlet 在 Sample.ps1 指令碼中的 Name 變數上建立中斷點。
然後，它會將中斷點物件儲存在 $B 變數中。

第二個命令使用 **Remove-PSBreakpoint** Cmdlet 來刪除新的中斷點。
它使用管線運算子 (|) 將 $B 變數中的中斷點物件傳送至 **Remove-PSBreakpoint** Cmdlet。

由於此命令，如果您執行此指令碼，它會不間斷執行直到完成。
此外， **Get-PSBreakpoint** Cmdlet 不會傳回此中斷點。

### 範例 3︰依識別碼移除中斷點

```
PS C:\> Remove-PSBreakpoint -Id 2
```

此命令會刪除具有中斷點識別碼 2 的中斷點。

### 範例 4︰使用函式來移除所有中斷點

```
PS C:\> function del-psb { get-psbreakpoint | remove-psbreakpoint }
```

這個簡單函式會刪除目前主控台中的所有中斷點。
它會使用 Get-PSBreakpoint Cmdlet 取得中斷點。
然後，它會使用管線運算子 (|) 將中斷點傳送至會刪除這些中斷點的 **Remove-PSBreakpoint** Cmdlet。

如此一來，您可以輸入 `del-psb`，而不是較長的命令。

如果要儲存函式，請將它新增到您的 Windows PowerShell 設定檔。

## PARAMETERS

### -Breakpoint
指定要刪除的中斷點。
輸入包含中斷點物件的變數，或輸入可取得中斷點物件的命令，例如 **>disable-psbreakpoint** 命令。
您也可以使用管線將中斷點物件傳送至 **Remove-PSBreakpoint** 。

```yaml
Type: System.Management.Automation.Breakpoint[]
Parameter Sets: Breakpoint
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Id
指定此 Cmdlet 刪除其中斷點的中斷點識別碼。

```yaml
Type: System.Int32[]
Parameter Sets: Id
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

### System.Management.Automation.Breakpoint
您可以使用管線將中斷點物件傳送至 **Remove-PSBreakpoint** 。

## 輸出

### 無
此 Cmdlet 不會產生任何輸出。

## 注意

## 相關連結

[Disable-PSBreakpoint](Disable-PSBreakpoint.md)

[Enable-PSBreakpoint](Enable-PSBreakpoint.md)

[Get-PSBreakpoint](Get-PSBreakpoint.md)

[Get-PSCallStack](Get-PSCallStack.md)

[Set-PSBreakpoint](Set-PSBreakpoint.md)
