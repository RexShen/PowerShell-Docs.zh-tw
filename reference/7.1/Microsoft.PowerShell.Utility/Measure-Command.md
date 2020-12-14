---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/measure-command?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Measure-Command
ms.openlocfilehash: 43958b376123202e152ceb2da3223cc2f22b0687
ms.sourcegitcommit: 165d10405d9db3a68c417a239d3181378fd02b9b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2020
ms.locfileid: "96935896"
---
# Measure-Command

## 概要
測量執行指令碼區塊和 Cmdlet 所需的時間。

## SYNTAX

```
Measure-Command [-InputObject <PSObject>] [-Expression] <ScriptBlock> [<CommonParameters>]
```

## DESCRIPTION

此 `Measure-Command` Cmdlet 會在內部執行腳本區塊或 Cmdlet、執行作業的次數，並傳回執行時間。

> [!NOTE]
> 腳本區塊執行的方式是 `Measure-Command` 在目前的範圍中執行，而不是子範圍。

## 範例

### 範例1：測量命令

這個範例會測量執行命令的時間，此 `Get-EventLog` 命令會取得 Windows PowerShell 事件記錄檔中的事件。

```powershell
Measure-Command { Get-EventLog "windows powershell" }
```

### 範例2：比較 Measure-Command 的兩個輸出

第一個命令會測量處理遞迴命令所花費的時間 `Get-ChildItem` ，此命令會使用 **Path** 參數來取得 `.txt` `C:\Windows` 目錄及其子目錄中的檔案。

第二個命令會測量處理遞迴命令所需的時間 `Get-ChildItem` ，此命令使用提供者特定的 ' 參數。

這些命令會顯示在 PowerShell 命令中使用提供者特定篩選器的值。

```powershell
Measure-Command { Get-ChildItem -Path C:\Windows\*.txt -Recurse }
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 8
Milliseconds      : 618
Ticks             : 86182763
TotalDays         : 9.9748568287037E-05
TotalHours        : 0.00239396563888889
TotalMinutes      : 0.143637938333333
TotalSeconds      : 8.6182763
TotalMilliseconds : 8618.2763
```

```powershell
Measure-Command {Get-ChildItem C:\Windows -Filter "*.txt" -Recurse}
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 1
Milliseconds      : 140
Ticks             : 11409189
TotalDays         : 1.32050798611111E-05
TotalHours        : 0.000316921916666667
TotalMinutes      : 0.019015315
TotalSeconds      : 1.1409189
TotalMilliseconds : 1140.9189
```

### 範例3：將輸入輸送至 Measure-Command

`Measure-Command`傳送至 **運算式** 參數的腳本區塊可以使用輸送至的物件。 腳本區塊會針對管線上的每個物件執行一次。

```powershell
# Perform a simple operation to demonstrate the InputObject parameter
# Note that no output is displayed.
10, 20, 50 | Measure-Command -Expression { for ($i=0; $i -lt $_; $i++) {$i} }
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 12
Ticks             : 122672
TotalDays         : 1.41981481481481E-07
TotalHours        : 3.40755555555556E-06
TotalMinutes      : 0.000204453333333333
TotalSeconds      : 0.0122672
TotalMilliseconds : 12.2672
```

### 範例4：顯示已測量命令的輸出

若要在中顯示運算式的輸出， `Measure-Command` 您可以使用管道 `Out-Default` 。

```powershell
# Perform the same operation as above adding Out-Default to every execution.
# This will show that the ScriptBlock is in fact executing for every item.
10, 20, 50 | Measure-Command -Expression {for ($i=0; $i -lt $_; $i++) {$i}; "$($_)" | Out-Default }
```

```Output
10
20
50


Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 11
Ticks             : 113745
TotalDays         : 1.31649305555556E-07
TotalHours        : 3.15958333333333E-06
TotalMinutes      : 0.000189575
TotalSeconds      : 0.0113745
TotalMilliseconds : 11.3745
```

### 範例5：測量子範圍中的執行

`Measure-Command` 在目前的範圍中執行腳本區塊，因此腳本區塊可以修改目前範圍中的值。 若要避免變更目前的範圍，您必須將腳本區塊包裝在大括弧 (`{}`) ，並使用叫用運算子 (`&`) 在子範圍中執行區塊。

```powershell
$foo = 'Value 1'
$null = Measure-Command { $foo = 'Value 2' }
$foo
$null = Measure-Command { & { $foo = 'Value 3' } }
$foo
```

```Output
Value 2
Value 2
```

如需調用運算子的詳細資訊，請參閱 [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md#call-operator-)。

## PARAMETERS

### -Expression

指定正在計時的運算式。 以大括弧括住運算式 (`{}`) 。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

系結至 **InputObject** 參數的物件是傳遞至 **Expression** 參數之腳本區塊的選擇性輸入。 在腳本區塊內， `$_` 可以用來參考管線中的目前物件。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Management.Automation.PSObject

您可以使用管線將物件傳送至 `Measure-Command` 。

## 輸出

### System.TimeSpan

`Measure-Command` 傳回代表結果的時間範圍物件。

## 注意

## 相關連結

[Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)

[Trace-Command](Trace-Command.md)

