---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/enable-psbreakpoint?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSBreakpoint
ms.openlocfilehash: 9530e3bc15360245de334a6f45ff35883181a41e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203327"
---
# Enable-PSBreakpoint

## 概要
在目前的主控台中啟用中斷點。

## SYNTAX

### Id (預設值)

```
Enable-PSBreakpoint [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 中斷點

```
Enable-PSBreakpoint [-PassThru] [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION

此 `Enable-PSBreakpoint` Cmdlet 會重新啟用已停用的中斷點。 您可以使用它來啟用所有中斷點，或是藉由提供中斷點物件或識別碼來啟用特定中斷點。

中斷點是腳本中的某個點，會暫時停止執行，讓您可以檢查腳本的狀態。 新建立的中斷點會自動啟用，但可使用來停用 `Disable-PSBreakpoint` 。

技術上來說，這個 Cmdlet 會將中斷點物件的 **Enabled** 屬性值變更為 **True** 。

`Enable-PSBreakpoint` 是數個設計用來偵測 PowerShell 腳本的 Cmdlet 之一。 如需 PowerShell 偵錯工具的詳細資訊，請參閱 [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md)。

## 範例

### 範例 1：啟用所有中斷點

此範例會啟用目前會話中的所有中斷點。

```powershell
Get-PSBreakpoint | Enable-PSBreakpoint
```

使用別名時，此範例可以縮寫為 `gbp | ebp` 。

### 範例 2：透過識別碼啟用中斷點

此範例會使用中斷點識別碼來啟用多個中斷點。

```powershell
Enable-PSBreakpoint -Id 0, 1, 5
```

### 範例 3：啟用停用的中斷點

此範例會重新啟用已停用的中斷點。

```powershell
$B = Set-PSBreakpoint -Script "sample.ps1" -Variable Name -PassThru
$B | Enable-PSBreakpoint -PassThru
```

```Output
AccessMode : Write
Variable   : Name
Action     :
Enabled    : False
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1

AccessMode : Write
Variable   : Name
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

`Set-PSBreakpoint`在腳本中，將 **Name** `Sample.ps1` 中斷點物件儲存在變數中的 Name 變數上建立中斷點 `$B` 。 **PassThru** 參數會顯示中斷點的 **Enabled** 屬性值為 **False** 。

`Enable-PSBreakpoint` 重新啟用中斷點。 同樣地，使用 **PassThru** 參數時，會看到 **Enabled** 屬性的值為 **True** 。

### 範例 4：使用變數啟用中斷點

這個範例會使用中斷點物件來啟用一組中斷點。

```powershell
$B = Get-PSBreakpoint -Id 3, 5
Enable-PSBreakpoint -Breakpoint $B
```

`Get-PSBreakpoint` 取得中斷點，並將它們儲存在 `$B` 變數中。 使用 **中斷點** 參數 `Enable-PSBreakpoint` 可啟用中斷點。

這個範例相當於正在執行 `Enable-PSBreakpoint -Id 3, 5` 。

## PARAMETERS

### -Breakpoint

指定要啟用的中斷點。 提供包含中斷點的變數，或提供可取得中斷點物件的命令（例如） `Get-PSBreakpoint` 。 您也可以透過管線將中斷點物件傳送至 `Enable-PSBreakpoint` 。

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

指定要啟用之中斷點的 **識別碼** 。 預設值為所有中斷點。
依數位或在變數中提供 **識別碼** 。 您無法以管道傳送 **識別碼** 至 `Enable-PSBreakpoint` 。 若要尋找中斷點的 **識別碼** ，請使用 `Get-PSBreakpoint` Cmdlet。

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

傳回物件，表示要啟用的中斷點。 根據預設，此 Cmdlet 不會產生任何輸出。

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

顯示執行 Cmdlet 後會發生的情況。 不會執行此 Cmdlet。

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

您可以使用管線將中斷點物件傳送至 `Enable-PSBreakpoint` 。

## 輸出

### 無或 System.Management.Automation.Breakpoint

當您使用 **PassThru** 參數時，會傳回 `Enable-PSBreakpoint` 代表已啟用之中斷點的中斷點物件。 否則，此 Cmdlet 不會產生任何輸出。

## 注意

- `Enable-PSBreakpoint`如果您嘗試啟用已啟用的中斷點，此 Cmdlet 並不會產生錯誤。 因此，即使只有少數中斷點已停用，您也可以啟用所有中斷點而不會發生錯誤。

- 當您使用 Cmdlet 來建立中斷點時，中斷點就會啟用 `Set-PSBreakpoint` 。 您不需要啟用新建立的中斷點。

## 相關連結

[Disable-PSBreakpoint](Disable-PSBreakpoint.md)

[Get-PSBreakpoint](Get-PSBreakpoint.md)

[Get-PSCallStack](Get-PSCallStack.md)

[Remove-PSBreakpoint](Remove-PSBreakpoint.md)

[Set-PSBreakpoint](Set-PSBreakpoint.md)
