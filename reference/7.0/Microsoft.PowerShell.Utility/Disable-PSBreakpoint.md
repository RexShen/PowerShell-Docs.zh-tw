---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/disable-psbreakpoint?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSBreakpoint
ms.openlocfilehash: 80d0c77e4c54dbc7e501339f5550c87f5f1ddbed
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201652"
---
# Disable-PSBreakpoint

## 概要
在目前的主控台中停用中斷點。

## SYNTAX

### 中斷點 (預設值)

```
Disable-PSBreakpoint [-PassThru] [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Id

```
Disable-PSBreakpoint [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

**>disable-psbreakpoint 指令程式** 會停用中斷點，以確保在執行腳本時不會叫用中斷點。
您可以使用它來停用所有中斷點，或是藉由送出中斷點物件或中斷點識別碼來指定中斷點。

就技術上來說，這個 Cmdlet 會將中斷點物件的 Enabled 屬性值變更為 False。
如果要重新啟用中斷點，請使用 Enable-PSBreakpoint Cmdlet。
使用 Set-PSBreakpoint Cmdlet 來建立中斷點時，中斷點預設會處於已啟用狀態。

中斷點是指令碼中的暫時停止執行點，用來讓您檢查指令碼中的指示。
**>disable-psbreakpoint** 是針對將 PowerShell 腳本進行偵錯工具設計的數個 Cmdlet 之一。
如需 PowerShell 偵錯工具的詳細資訊，請參閱 about_Debuggers。

## 範例

### 範例1：設定中斷點並停用它

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Variable "name"
PS C:\> $B | Disable-PSBreakpoint
```

這些命令會停用新建的中斷點。

第一個命令會使用 Set-PSBreakpoint Cmdlet，在 Sample.ps1 腳本中的 *Name* 變數上建立中斷點。
然後，它會將中斷點物件儲存在 $B 變數中。

第二個命令使用 **>disable-psbreakpoint** Cmdlet 來停用新的中斷點。
它使用管線運算子 (|) 將 $B 中的中斷點物件傳送至 **>disable-psbreakpoint** Cmdlet。

這項命令的結果，$B 中中斷點物件的 Enabled 屬性值為 False。

### 範例2：停用中斷點

```
PS C:\> Disable-PSBreakpoint -Id 0
```

此命令停用具有中斷點識別碼 0 的中斷點。

### 範例3：建立已停用的中斷點

```
PS C:\> Disable-PSBreakpoint -Breakpoint ($B = Set-PSBreakpoint -Script "sample.ps1" -Line 5)
PS C:\> $B
```

此命令建立新的中斷點，在您啟用之前它會是停用的。

它會使用 **>disable-psbreakpoint** Cmdlet 來停用中斷點。
*中斷點* 參數的值是設定新中斷點、產生中斷點物件，並將物件儲存在 $B 變數中的 Set-PSBreakpoint 命令。

以物件為其值的 Cmdlet 參數可接受包含物件的變數，或是取得或產生物件的命令。
在此情況下，由於 **>disable-psbreakpoint** 會產生中斷點物件，因此它可以當做 *中斷點* 參數的值使用。

第二個命令會在 $B 變數的值中顯示中斷點物件。

### 範例4：停用目前主控台中的所有中斷點

```
PS C:\> Get-PSBreakpoint | Disable-PSBreakpoint
```

此命令停用目前主控台中的所有中斷點。
您可以將此命令縮寫為："gbp | dbp"。

## PARAMETERS

### -Breakpoint

指定要停用的中斷點。
請輸入包含中斷點物件的變數，或可取得中斷點物件的命令，例如 Get-PSBreakpoint 命令。
您也可以透過管線將中斷點物件傳送至 **>disable-psbreakpoint** Cmdlet。

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

停用具有指定之中斷點識別碼的中斷點。
請輸入識別碼或包含識別碼的變數。
您無法透過管線將識別碼傳送至 **停用->disable-psbreakpoint** 。

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

### -PassThru

傳回代表已啟用之中斷點的物件。
根據預設，此 Cmdlet 不會產生任何輸出。

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

您可以使用管線將中斷點物件傳送至 **停用->disable-psbreakpoint** 。

## 輸出

### 無或 System.Management.Automation.Breakpoint

當您使用 *PassThru* 參數時， **>disable-psbreakpoint** 會傳回代表已停用之中斷點的物件。
否則，此 Cmdlet 不會產生任何輸出。

## 注意

## 相關連結

[Enable-PSBreakpoint](Enable-PSBreakpoint.md)

[Get-PSBreakpoint](Get-PSBreakpoint.md)

[Get-PSCallStack](Get-PSCallStack.md)

[Remove-PSBreakpoint](Remove-PSBreakpoint.md)

[Set-PSBreakpoint](Set-PSBreakpoint.md)
