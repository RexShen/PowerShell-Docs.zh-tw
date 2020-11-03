---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-psbreakpoint?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSBreakpoint
ms.openlocfilehash: ae3dbbd062171a0185308bc120c1baf31a352c92
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201672"
---
# Get-PSBreakpoint

## 概要
取得目前工作階段中設定的中斷點。

## SYNTAX

### Script (預設值)

```
Get-PSBreakpoint [-Script <String[]>] [<CommonParameters>]
```

### 變數

```
Get-PSBreakpoint [-Script <String[]>] -Variable <String[]> [<CommonParameters>]
```

### Command

```
Get-PSBreakpoint [-Script <String[]>] -Command <String[]> [<CommonParameters>]
```

### 類型

```
Get-PSBreakpoint [-Script <String[]>] [-Type] <BreakpointType[]> [<CommonParameters>]
```

### Id

```
Get-PSBreakpoint [-Id] <Int32[]> [<CommonParameters>]
```

## DESCRIPTION

**>disable-psbreakpoint 指令程式** 會取得在目前會話中設定的中斷點。
您可以使用 Cmdlet 參數以取得特定的中斷點。

中斷點是命令或指令碼中的暫時停止執行點，用來讓您檢查指示。
**>disable-psbreakpoint** 是數個設計用來對 PowerShell 腳本和命令進行偵錯工具的 Cmdlet 之一。 如需 PowerShell 偵錯工具的詳細資訊，請參閱 about_Debuggers。

## 範例

### 範例1：取得所有腳本和函式的所有中斷點

```
PS C:\> Get-PSBreakpoint
```

此命令會取得在目前工作階段中之所有指令碼和函式上設定的所有中斷點。

### 範例2：依識別碼取得中斷點

```
PS C:\> Get-PSBreakpoint -Id 2
Function   :
IncrementAction     :
Enabled    :
TrueHitCount   : 0
Id         : 2
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

此命令會取得具有中斷點識別碼 2 的中斷點。

### 範例3：使用管線將識別碼傳送至 Get-PSBreakpoint

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Command "Increment"
PS C:\> $B.Id | Get-PSBreakpoint
```

這些命令會顯示如何使用管線將中斷點識別碼傳送至 **>disable-psbreakpoint** ，以取得中斷點。

第一個命令會使用 Set-PSBreakpoint Cmdlet 在 Sample.ps1 指令碼中的 Increment 函式建立中斷點。 它會將中斷點物件儲存在 $B 變數中。

第二個命令使用點運算子 (. ) 取得 $B 變數中中斷點物件的 Id 屬性。 它使用管線運算子 (|) 將識別碼傳送至 **>disable-psbreakpoint** Cmdlet。

因此， **>disable-psbreakpoint** 會取得具有指定識別碼的中斷點。

### 範例4：在指定的指令檔中取得中斷點

```
PS C:\> Get-PSBreakpoint -Script "Sample.ps1, SupportScript.ps1"
```

此命令會取得 Sample.ps1 和 SupportScript.ps1 檔案中的所有中斷點。

此命令不會取得其他腳本或會話中的函數所設定的其他中斷點。

### 範例5：在指定的 Cmdlet 中取得中斷點

```
PS C:\> Get-PSBreakpoint -Command "Read-Host, Write-Host" -Script "Sample.ps1"
```

此命令會取得設定在 Sample.ps1 檔案之 Read-Host 或 Write-Host 命令上的所有命令中斷點。

### 範例6：在指定的檔案中取得命令中斷點

```
PS C:\> Get-PSBreakpoint -Type Command -Script "Sample.ps1"
```

此命令會取得 Sample.ps1 檔案中的所有命令中斷點。

### 範例7：依變數取得中斷點

```
PS C:\> Get-PSBreakpoint -Variable "Index, Swap"
```

此命令會取得在目前會話中的 $Index 和 $Swap 變數上設定的中斷點。

### 範例8：取得檔案中的所有行和變數中斷點

```
PS C:\> Get-PSBreakpoint -Type Line, Variable -Script "Sample.ps1"
```

此命令會取得 Sample.ps1 指令碼中的所有行和變數中斷點。

## PARAMETERS

### -Command

指定在指定的命令名稱上設定的命令中斷點陣列。
輸入命令名稱，例如 Cmdlet 或函式的名稱。

```yaml
Type: System.String[]
Parameter Sets: Command
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

指定此 Cmdlet 取得的中斷點識別碼。
以逗號分隔的清單方式輸入識別碼。
您也可以透過管線將中斷點識別碼傳送至 **>disable-psbreakpoint** 。

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Script

指定包含中斷點之腳本的陣列。
輸入 (選用) 的路徑，以及一或多個腳本檔案的名稱。
若省略路徑，則預設位置為目前目錄。

```yaml
Type: System.String[]
Parameter Sets: Script, Variable, Command, Type
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Type

指定此 Cmdlet 取得之中斷點類型的陣列。
輸入一個或多個類型。
此參數可接受的值為：

- 線條
- Command
- 變數

您也可以透過管線將中斷點類型傳送至 **>disable-psbreakpoint** 。

```yaml
Type: Microsoft.PowerShell.Commands.BreakpointType[]
Parameter Sets: Type
Aliases:
Accepted values: Line, Variable, Command

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Variable

指定在指定的變數名稱上設定的變數中斷點陣列。
輸入不含貨幣符號的變數名稱。

```yaml
Type: System.String[]
Parameter Sets: Variable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Int32、Microsoft.PowerShell.Commands.BreakpointType

您可以透過管線將中斷點識別碼和中斷點類型傳送至 **>disable-psbreakpoint** 。

## 輸出

### System.Management.Automation.Breakpoint

**>disable-psbreakpoint** 會傳回代表會話中中斷點的物件。

## 注意

* 您可以使用 **>disable-psbreakpoint** 或其別名 "gbp"。

## 相關連結

[Disable-PSBreakpoint](Disable-PSBreakpoint.md)

[Enable-PSBreakpoint](Enable-PSBreakpoint.md)

[Get-PSCallStack](Get-PSCallStack.md)

[Remove-PSBreakpoint](Remove-PSBreakpoint.md)

[Set-PSBreakpoint](Set-PSBreakpoint.md)
