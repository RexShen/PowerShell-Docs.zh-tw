---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/measure-object?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Measure-Object
ms.openlocfilehash: 88b18a929a1debc85eb7ce65dbdf2d14fc4b89cd
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2020
ms.locfileid: "93205923"
---
# Measure-Object

## 概要
計算物件的數值屬性，以及字串物件 (例如文字檔案) 中的字元數、文字數和行數。

## SYNTAX

### GenericMeasure (預設值)

```
Measure-Object [[-Property] <PSPropertyExpression[]>] [-InputObject <PSObject>] [-StandardDeviation]
 [-Sum] [-AllStats] [-Average] [-Maximum] [-Minimum] [<CommonParameters>]
```

### TextMeasure

```
Measure-Object [[-Property] <PSPropertyExpression[]>] [-InputObject <PSObject>] [-Line] [-Word]
 [-Character] [-IgnoreWhiteSpace] [<CommonParameters>]
```

## DESCRIPTION

`Measure-Object`Cmdlet 會計算特定物件類型的屬性值。
`Measure-Object` 根據命令中的參數，執行三種類型的度量。

此 `Measure-Object` Cmdlet 會在物件的屬性值上執行計算。 您可以使用 `Measure-Object` 來計算物件或計算具有指定 **屬性** 的物件。 您也可以使用 `Measure-Object` 來計算數值的 **最小** 值、 **最大** 值、 **總和** 、 **list.standarddeviation** 和 **平均值** 。 針對 **字串** 物件，您也可以使用 `Measure-Object` 來計算行數、字組和字元數。

## 範例

### 範例 1︰計算目錄中的檔案和資料夾數目

此命令計算目前目錄中的檔案數目和資料夾數目。

```powershell
Get-ChildItem | Measure-Object
```

### 範例 2︰測量目錄中的檔案

此命令會顯示目前目錄中所有檔案大小的 **最小值** 、 **最大值** 和 **總和** ，以及目錄中檔案的平均大小。

```powershell
Get-ChildItem | Measure-Object -Property length -Minimum -Maximum -Average
```

### 範例 3︰測量文字檔中的文字

此命令顯示 Text.txt 檔案中的字元數、文字數和行數。
如果沒有 **Raw** 參數，請將檔案 `Get-Content` 輸出為行的陣列。

第一個命令會使用將 `Set-Content` 一些預設文字新增至檔案。

```powershell
"One", "Two", "Three", "Four" | Set-Content -Path C:\Temp\tmp.txt
Get-Content C:\Temp\tmp.txt | Measure-Object -Character -Line -Word
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    4     4         15
```

### 範例4：量值物件包含指定的屬性

此範例會計算具有 **DisplayName** 屬性的物件數目。 前兩個命令會取得本機電腦上的所有服務和進程。 第三個命令會計算服務和進程的組合數目。 最後一個命令會結合兩個集合，並將結果輸送至 `Measure-Object` 。

System.servicemodel **物件沒有** **DisplayName** 屬性，而且會保留在最後一個計數中。

```powershell
$services = Get-Service
$processes = Get-Process
$services + $processes | Measure-Object
$services + $processes | Measure-Object -Property DisplayName
```

```Output
Count    : 682
Average  :
Sum      :
Maximum  :
Minimum  :
Property :

Count    : 290
Average  :
Sum      :
Maximum  :
Minimum  :
Property : DisplayName
```

### 範例 5︰測量 CSV 檔案的內容

此命令計算公司員工的平均服務年資。

檔案 `ServiceYrs.csv` 是一個 CSV 檔案，其中包含每個員工的員工人數和年度服務。 資料表中的第一個資料列是 **具有 empno** ， **年** 的標頭資料列。

當您使用匯入檔案時 `Import-Csv` ，結果會是 **PSCustomObject** ，其中包含 **具有 empno** 和 **年** 的附注屬性。
您可以使用 `Measure-Object` 來計算這些屬性的值，就像物件的任何其他屬性一樣。

```powershell
Import-Csv d:\test\serviceyrs.csv | Measure-Object -Property years -Minimum -Maximum -Average
```

### 範例 6︰測量布林值

這個範例會示範如何 `Measure-Object` 測量布林值。
在此情況下，它會使用 **PSIsContainer** **布林** 值屬性來測量目前目錄中) 資料夾 (與檔案的發生情形。

```powershell
Get-ChildItem | Measure-Object -Property psiscontainer -Maximum -Sum -Minimum -Average
```

```Output
Count             : 126
Average           : 0.0634920634920635
Sum               : 8
Maximum           : 1
Minimum           : 0
StandardDeviation :
Property          : PSIsContainer
```

### 範例7：量值字串

下列範例會測量行數、第一個字串，然後在數個字串之間進行測量。 換行字元會將 <code>`n</code> 字串分隔成多行。

```powershell
# The newline character `n separates the string into separate lines, as shown in the output.
"One`nTwo`nThree"
"One`nTwo`nThree" | Measure-Object -Line
```

```Output
One
Two
Three


Lines Words Characters Property
----- ----- ---------- --------
    3
```

```powershell
# The first string counts as a single line.
# The second string is separated into two lines by the newline character.
"One", "Two`nThree" | Measure-Object -Line
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    3
```

```powershell
# The Word switch counts the number of words in each InputObject
# Each InputObject is treated as a single line.
"One, Two", "Three", "Four Five" | Measure-Object -Word -Line
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    3     5
```

### 範例8：測量所有值

從 PowerShell 6 開始，的 **AllStats** 參數可 `Measure-Object` 讓您同時測量所有統計資料。

```powershell
1..5 | Measure-Object -AllStats
```

```output
Count             : 5
Average           : 3
Sum               : 15
Maximum           : 5
Minimum           : 1
StandardDeviation : 1.58113883008419
Property          :
```

### 範例9：使用 scriptblock 屬性測量

從 PowerShell 6 開始， `Measure-Object` 支援 **ScriptBlock** 屬性。 下列範例示範如何使用 **ScriptBlock** 屬性來判斷目錄中所有檔案的大小（以 Mb 為單位）。

```powershell
Get-ChildItem | Measure-Object -Sum {$_.Length/1MB}
```

### 範例10：量值雜湊表

從 PowerShell 6 開始，可 `Measure-Object` 支援量 **表** 輸入的測量。 下列範例會決定 `num` 3 個 **雜湊表** 物件之索引鍵的最大值。

```powershell
@{num=3}, @{num=4}, @{num=5} | Measure-Object -Maximum Num
```

```output
Count             : 3
Average           :
Sum               :
Maximum           : 5
Minimum           :
StandardDeviation :
Property          : num
```

### 範例11：測量標準差

從 PowerShell 6 開始， `Measure-Object` 支援 `-StandardDeviation` 參數。 下列範例會決定所有進程所使用之 CPU 的 *標準差* 。 有很大的偏差表示耗用最多 CPU 的進程數目很少。

```powershell
Get-Process | Measure-Object -Average -StandardDeviation CPU
```

```output
Count             : 303
Average           : 163.032384488449
Sum               :
Maximum           :
Minimum           :
StandardDeviation : 859.444048419069
Property          : CPU
```

### 範例12：使用萬用字元測量

從 PowerShell 6 開始，可 `Measure-Object` 支援在屬性名稱中使用萬用字元來測量物件。 下列範例會決定一組處理常式之間任何分頁記憶體使用量類型的最大值。

```powershell
Get-Process | Measure-Object -Maximum *paged*memory*size
```

```output
Count             : 303
Average           :
Sum               :
Maximum           : 735784
Minimum           :
StandardDeviation :
Property          : NonpagedSystemMemorySize

Count             : 303
Average           :
Sum               :
Maximum           : 352104448
Minimum           :
StandardDeviation :
Property          : PagedMemorySize

Count             : 303
Average           :
Sum               :
Maximum           : 2201968
Minimum           :
StandardDeviation :
Property          : PagedSystemMemorySize

Count             : 303
Average           :
Sum               :
Maximum           : 719032320
Minimum           :
StandardDeviation :
Property          : PeakPagedMemorySize
```

## PARAMETERS

### -Average

指出此 Cmdlet 會顯示指定屬性的平均值。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Character

指出此 Cmdlet 會計算輸入物件中的字元數。

> [!NOTE]
> **單字** 、 **Char** 和 **Line** 參數會在每個輸入物件 *內* ，以及輸入物件 *之間* 進行計數。 請參閱範例7。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IgnoreWhiteSpace

指出此 Cmdlet 會忽略字元計數中的空白字元。
根據預設，不會忽略空白字元。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定要測量的物件。
輸入包含物件的變數，或輸入可取得物件的命令或運算式。

當您搭配使用 **inputobject** 參數與時 `Measure-Object` ，不會將命令結果傳送至，而是 `Measure-Object` 會將 **inputobject** 值視為單一物件。

`Measure-Object`如果您想要根據物件是否在已定義屬性中具有特定值來測量物件集合，建議您在管線中使用。

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

### -Line

指出此 Cmdlet 會計算輸入物件中的行數。

> [!NOTE]
> **單字** 、 **Char** 和 **Line** 參數會在每個輸入物件 *內* ，以及輸入物件 *之間* 進行計數。 請參閱範例7。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Maximum

指出此 Cmdlet 會顯示指定屬性的最大值。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Minimum

指出此 Cmdlet 會顯示指定屬性的最小值。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Property

指定要測量的一或多個屬性。 如果您未指定任何其他量值，則 `Measure-Object` 會計算具有您指定之屬性的物件。

**Property** 參數的值可以是新的計算屬性。 計算屬性必須是腳本區塊。 如需詳細資訊，請參閱 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。

```yaml
Type: Microsoft.PowerShell.Commands.PSPropertyExpression[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -List.standarddeviation

指出此 Cmdlet 會顯示指定屬性值的標準差。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Sum

指出此 Cmdlet 會顯示指定屬性的總和。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllStats

指出此 Cmdlet 會顯示指定屬性的所有統計資料。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Word

指出此 Cmdlet 會計算輸入物件中的文字數目。

> [!NOTE]
> **單字** 、 **Char** 和 **Line** 參數會在每個輸入物件 *內* ，以及輸入物件 *之間* 進行計數。 請參閱範例7。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Management.Automation.PSObject

您可以透過管線將物件傳送至 `Measure-Object` 。

## 輸出

### GenericMeasureInfo。

### TextMeasureInfo。

如果您使用 **Word** 參數，則會傳回 `Measure-Object` **TextMeasureInfo** 物件。
否則，它會傳回 **GenericMeasureInfo** 物件。

## 注意

## 相關連結

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[Compare-Object](Compare-Object.md)

[ForEach-Object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Group-Object](Group-Object.md)

[New-Object](New-Object.md)

[Select-Object](Select-Object.md)

[Sort-Object](Sort-Object.md)

[Tee-Object](Tee-Object.md)

[Where-Object](../Microsoft.PowerShell.Core/Where-Object.md)
