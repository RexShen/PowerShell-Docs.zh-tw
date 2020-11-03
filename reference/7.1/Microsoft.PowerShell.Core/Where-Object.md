---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/where-object?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Where-Object
ms.openlocfilehash: b5f4a64cceffa1f4f9884bb4de3211e129871ba7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205100"
---
# Where-Object

## 概要
根據屬性值從集合中選取物件。

## SYNTAX

### EqualSet (預設) 

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-EQ]
 [<CommonParameters>]
```

### ScriptBlockSet

```
Where-Object [-InputObject <PSObject>] [-FilterScript] <ScriptBlock> [<CommonParameters>]
```

### MatchSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Match
 [<CommonParameters>]
```

### CaseSensitiveEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CEQ
 [<CommonParameters>]
```

### NotEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NE
 [<CommonParameters>]
```

### CaseSensitiveNotEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNE
 [<CommonParameters>]
```

### GreaterThanSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -GT
 [<CommonParameters>]
```

### CaseSensitiveGreaterThanSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CGT
 [<CommonParameters>]
```

### LessThanSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -LT
 [<CommonParameters>]
```

### CaseSensitiveLessThanSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CLT
 [<CommonParameters>]
```

### GreaterOrEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -GE
 [<CommonParameters>]
```

### CaseSensitiveGreaterOrEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CGE
 [<CommonParameters>]
```

### LessOrEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -LE
 [<CommonParameters>]
```

### CaseSensitiveLessOrEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CLE
 [<CommonParameters>]
```

### LikeSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Like
 [<CommonParameters>]
```

### CaseSensitiveLikeSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CLike
 [<CommonParameters>]
```

### NotLikeSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotLike
 [<CommonParameters>]
```

### CaseSensitiveNotLikeSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotLike
 [<CommonParameters>]
```

### CaseSensitiveMatchSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CMatch
 [<CommonParameters>]
```

### NotMatchSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotMatch
 [<CommonParameters>]
```

### CaseSensitiveNotMatchSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotMatch
 [<CommonParameters>]
```

### ContainsSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Contains
 [<CommonParameters>]
```

### CaseSensitiveContainsSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CContains
 [<CommonParameters>]
```

### NotContainsSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotContains
 [<CommonParameters>]
```

### CaseSensitiveNotContainsSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotContains
 [<CommonParameters>]
```

### 插圖

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -In
 [<CommonParameters>]
```

### CaseSensitiveInSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CIn
 [<CommonParameters>]
```

### NotInSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotIn
 [<CommonParameters>]
```

### CaseSensitiveNotInSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotIn
 [<CommonParameters>]
```

### IsSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Is
 [<CommonParameters>]
```

### IsNotSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -IsNot
 [<CommonParameters>]
```

### Not

```
Where-Object [-InputObject <PSObject>] [-Property] <String> -Not [<CommonParameters>]
```

## DESCRIPTION

`Where-Object`Cmdlet 會從傳遞給它的物件集合中選取具有特定屬性值的物件。 例如，您可以使用 `Where-Object` Cmdlet 來選取在特定日期之後建立的檔案、具有特定識別碼的事件，或使用特定 Windows 版本的電腦。

從 Windows PowerShell 3.0 開始，有兩種不同的方式可建立 `Where-Object` 命令。

- **腳本區塊** 。 您可以使用指令碼區塊來指定屬性名稱、比較運算子及屬性值。 `Where-Object` 傳回腳本區塊語句為 true 的所有物件。

  例如，下列命令會取得一般優先順序類別中的處理常式，也就是 **PriorityClass** 屬性的值等於 normal 的進程。

  `Get-Process | Where-Object {$_.PriorityClass -eq "Normal"}`

  所有 PowerShell 比較運算子都是有效的腳本區塊格式。 如需比較運算子的詳細資訊，請參閱 [about_Comparison_Operators](./About/about_Comparison_Operators.md)。

- **比較語句** 。 您也可以撰寫較像自然語言的比較陳述式。 比較陳述式是在 Windows PowerShell 3.0 中引進。

  例如，下列命令也會取得優先順序類別為 Normal 的進程。 這些命令是相等的，可以交換使用。

  `Get-Process | Where-Object -Property PriorityClass -eq -Value "Normal"`

  `Get-Process | Where-Object PriorityClass -eq "Normal"`

  從 Windows PowerShell 3.0 開始，會在 `Where-Object` 命令中加入比較運算子做為參數 `Where-Object` 。 除非另有指定，否則所有運算子都不區分大小寫。 在 Windows PowerShell 3.0 之前，PowerShell 語言中的比較運算子只能在腳本區塊中使用。

當您提供單一 **屬性** 給時 `Where-Object` ，屬性的值會被視為布林運算式。 當 **長度** 的值不是零時，運算式會評估為 **True** 。 例如：`('hi', '', 'there') | Where-Object Length`

上述範例在功能上等同于：

- `('hi', '', 'there') | Where-Object Length -GT 0`
- `('hi', '', 'there') | Where-Object {$_.Length -gt 0}`

## 範例

### 範例1：取得已停止的服務

這些命令會取得目前已停止的所有服務清單。 `$_`自動變數代表每個傳遞給 Cmdlet 的物件 `Where-Object` 。

第一個命令使用腳本區塊格式，第二個命令使用比較語句格式。 這些命令是相等的，可以交換使用。

```powershell
Get-Service | Where-Object {$_.Status -eq "Stopped"}
Get-Service | where Status -eq "Stopped"
```

### 範例2：根據工作集取得進程

這些命令會列出工作集大於 250 mb (KB) 的處理常式。 Scriptblock 和語句語法是相等的，可以交換使用。

```powershell
Get-Process | Where-Object {$_.WorkingSet -GT 250MB}
Get-Process | Where-Object WorkingSet -GT (250MB)
```

### 範例3：根據進程名稱取得進程

這些命令會取得其 **ProcessName** 屬性值以字母開頭的處理常式 `p` 。 **Match** 運算子可讓您使用正則運算式相符專案。

Scriptblock 和語句語法是相等的，可以交換使用。

```powershell
Get-Process | Where-Object {$_.ProcessName -Match "^p.*"}
Get-Process | Where-Object ProcessName -Match "^p.*"
```

### 範例4：使用比較語句格式

此範例示範如何使用 Cmdlet 的新比較語句格式 `Where-Object` 。

第一個命令使用比較陳述式格式。
此命令中不會使用任何別名，並且所有的參數都包括參數名稱。

第二個命令是更自然的比較命令格式使用方式。 `where`別名會取代為 `Where-Object` Cmdlet 名稱，並省略所有選擇性參數名稱。

```powershell
Get-Process | Where-Object -Property Handles -GE -Value 1000
Get-Process | where Handles -GE 1000
```

### 範例5：根據屬性取得命令

此範例示範如何撰寫會傳回 True 或 False 的項目，或撰寫具有任何指定屬性值的命令。 每個範例都會顯示命令的腳本區塊和比較語句格式。

```powershell
# Use Where-Object to get commands that have any value for the OutputType property of the command.
# This omits commands that do not have an OutputType property and those that have an OutputType property, but no property value.
Get-Command | where OutputType
Get-Command | where {$_.OutputType}
```

```powershell
# Use Where-Object to get objects that are containers.
# This gets objects that have the **PSIsContainer** property with a value of $True and excludes all others.
Get-ChildItem | where PSIsContainer
Get-ChildItem | where {$_.PSIsContainer}
```

```powershell
# Finally, use the Not operator (!) to get objects that are not containers.
# This gets objects that do have the **PSIsContainer** property and those that have a value of $False for the **PSIsContainer** property.
Get-ChildItem | where {!$_.PSIsContainer}
# You cannot use the Not operator (!) in the comparison statement format of the command.
Get-ChildItem | where PSIsContainer -eq $False
```

### 範例6：使用多個條件

```powershell
Get-Module -ListAvailable | where {($_.Name -notlike "Microsoft*" -and $_.Name -notlike "PS*") -and $_.HelpInfoUri}
```

此範例說明如何建立 `Where-Object` 具有多個條件的命令。

此命令取得支援可更新之說明功能的非核心模組。 此命令會使用 Cmdlet 的 **ListAvailable** 參數 `Get-Module` 來取得電腦上的所有模組。 管線運算子 (`|`) 會將模組傳送至 `Where-Object` Cmdlet，此 Cmdlet 會取得名稱不是以 MICROSOFT 或 PS 開頭的模組，並且具有 **HelpInfoURI** 屬性的值，這會指示 PowerShell 在哪裡找到模組的已更新說明檔。 比較語句是由 **And** 邏輯運算子連接。

此範例使用指令碼區塊命令格式。 邏輯運算子（例如 **and** 和 **Or** ）僅適用于腳本區塊。 您無法在命令的比較語句格式中使用它們 `Where-Object` 。

- 如需 PowerShell 邏輯運算子的詳細資訊，請參閱 [about_Logical_Operators](./About/about_logical_operators.md)。
- 如需可更新之說明功能的詳細資訊，請參閱 [about_Updatable_Help](./About/about_Updatable_Help.md)。

## PARAMETERS

### -包含

指出如果物件的屬性值與指定的值完全相符，此 Cmdlet 會從集合取得物件。 這項操作會區分大小寫。

例如：`Get-Process | where ProcessName -CContains "svchost"`

**包含** 是指值的集合，如果集合包含的專案與指定的值完全相符，則為 true。 如果輸入是單一物件，則 PowerShell 會將它轉換成一個物件的集合。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveContainsSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CEQ

指出此 Cmdlet 會在屬性值與指定的值相同時取得物件。
這項操作會區分大小寫。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CGE

指出此 Cmdlet 會在屬性值大於或等於指定的值時取得物件。 這項操作會區分大小寫。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveGreaterOrEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CGT

指出此 Cmdlet 會在屬性值大於指定的值時取得物件。
這項操作會區分大小寫。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveGreaterThanSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CIn

指出此 Cmdlet 會在屬性值包含指定的值時取得物件。 這項操作會區分大小寫。

例如：`Get-Process | where -Value "svchost" -CIn ProcessName`

**CIn** 類似 **包含** ，不同之處在于屬性和值的位置是相反的。 例如，下列陳述式都是 True。

`"abc", "def" -CContains "abc"`

`"abc" -CIn "abc", "def"`

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveInSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CLE

指出此 Cmdlet 會在屬性值小於或等於指定的值時取得物件。 這項操作會區分大小寫。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveLessOrEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CLike

指出此 Cmdlet 會在屬性值與包含萬用字元的值相符時取得物件。 這項操作會區分大小寫。

例如：`Get-Process | where ProcessName -CLike "*host"`

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveLikeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CLT

指出此 Cmdlet 會在屬性值小於指定的值時取得物件。 這項操作會區分大小寫。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveLessThanSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CMatch

指出此 Cmdlet 會在屬性值與指定的正則運算式相符時取得物件。 這項操作會區分大小寫。 當輸入是純量時，相符的值會儲存在 `$Matches` 自動變數中。

例如：`Get-Process | where ProcessName -CMatch "Shell"`

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveMatchSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CNE

指出此 Cmdlet 會在屬性值與指定的值不同時取得物件。
這項操作會區分大小寫。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Cnotcontains 是指

指出此 Cmdlet 會在物件的屬性值與指定的值不完全相符時取得物件。 這項操作會區分大小寫。

例如：`Get-Process | where ProcessName -CNotContains "svchost"`

**NotContains** 和 **cnotcontains 是指** 指的是值的集合，而且當集合未包含任何與指定的值完全相符的專案時為 true。 如果輸入是單一物件，則 PowerShell 會將它轉換成一個物件的集合。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotContainsSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CNotIn

指出此 Cmdlet 會在屬性值與指定的值不完全相符時取得物件。 這項操作會區分大小寫。

例如：`Get-Process | where -Value "svchost" -CNotIn -Property ProcessName`

**NotIn** 和 **CNotIn** 運算子類似 **NotContains** 和 **cnotcontains 是指** ，不同之處在于屬性和值的位置是相反的。 例如，下列陳述式為 True。

`"abc", "def" -CNotContains "Abc"`

`"abc" -CNotIn "Abc", "def"`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotInSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CNotLike

指出此 Cmdlet 會在屬性值與包含萬用字元的值不相符時取得物件。 這項操作會區分大小寫。

例如：`Get-Process | where ProcessName -CNotLike "*host"`

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotLikeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CNotMatch

指出此 Cmdlet 會在屬性值與指定的正則運算式不相符時取得物件。 這項操作會區分大小寫。 當輸入是純量時，相符的值會儲存在 `$Matches` 自動變數中。

例如：`Get-Process | where ProcessName -CNotMatch "Shell"`

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotMatchSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Contains

指出此 Cmdlet 會在物件的屬性值中有任何專案與指定的值完全相符時取得物件。

例如：`Get-Process | where ProcessName -Contains "Svchost"`

如果屬性值包含單一物件，則 PowerShell 會將它轉換成一個物件的集合。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainsSet
Aliases: IContains

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EQ

指出此 Cmdlet 會在屬性值與指定的值相同時取得物件。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: EqualSet
Aliases: IEQ

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilterScript

指定用來篩選物件的指令碼區塊。 以大括弧括住腳本區塊 (`{}`) 。

參數名稱 **FilterScript** 是選擇性的。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -GE

指出此 Cmdlet 會在屬性值大於或等於指定的值時取得物件。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GreaterOrEqualSet
Aliases: IGE

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -GT

指出此 Cmdlet 會在屬性值大於指定的值時取得物件。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GreaterThanSet
Aliases: IGT

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -In

指出此 Cmdlet 會在屬性值符合任何指定的值時取得物件。
例如：

`Get-Process | where -Property ProcessName -in -Value "Svchost", "TaskHost", "WsmProvHost"`

如果 **value** 參數的值為單一物件，則 PowerShell 會將它轉換成一個物件的集合。

如果物件的屬性值是陣列，則 PowerShell 會使用參考相等來判斷是否相符。 `Where-Object` 只有當 **Property** 參數的值和 **值** 的任何值都是物件的相同實例時，才會傳回物件。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: InSet
Aliases: IIn

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定要篩選的物件。 您也可以透過管道將物件傳送至 `Where-Object` 。

當您搭配使用 **inputobject** 參數與時 `Where-Object` ，不會將命令結果傳送至，而是 `Where-Object` 會將 **inputobject** 值視為單一物件。 即使值是命令結果的集合（例如），也是如此 `-InputObject (Get-Process)` 。 因為 **InputObject** 無法從物件陣列或集合傳回個別屬性，所以如果您使用來篩選物件的集合，而 `Where-Object` 這些物件具有已定義屬性中的特定值，您可以 `Where-Object` 在管線中使用，如本主題中的範例所示。

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

### -是

指出此 Cmdlet 會在屬性值為指定之 .NET 型別的實例時取得物件。 使用方括號括住型別名稱。

例如， `Get-Process | where StartTime -Is [DateTime]`

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IsNot

指出此 Cmdlet 會在屬性值不是指定之 .NET 型別的實例時取得物件。

例如， `Get-Process | where StartTime -IsNot [DateTime]`

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsNotSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LE

指出此 Cmdlet 會在屬性值小於或等於指定的值時取得物件。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LessOrEqualSet
Aliases: ILE

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Like

指出此 Cmdlet 會在屬性值與包含萬用字元的值相符時取得物件。

例如：`Get-Process | where ProcessName -Like "*host"`

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LikeSet
Aliases: ILike

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LT

指出此 Cmdlet 會在屬性值小於指定的值時取得物件。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LessThanSet
Aliases: ILT

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Match

指出此 Cmdlet 會在屬性值與指定的正則運算式相符時取得物件。 當輸入是純量時，相符的值會儲存在 `$Matches` 自動變數中。

例如：`Get-Process | where ProcessName -Match "shell"`

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: MatchSet
Aliases: IMatch

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NE

指出此 Cmdlet 會在屬性值與指定的值不同時取得物件。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotEqualSet
Aliases: INE

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Not

指出此 Cmdlet 會在屬性不存在或值為 null 或 false 時取得物件。

例如：`Get-Service | where -Not "DependentServices"`

此參數是在 Windows PowerShell 6.1 中引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Not
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotContains

指出此 Cmdlet 會在屬性值中沒有任何專案與指定的值完全相符時取得物件。

例如：`Get-Process | where ProcessName -NotContains "Svchost"`

**NotContains** 是指值的集合，如果集合未包含任何與指定的值完全相符的專案，則為 true。 如果輸入是單一物件，則 PowerShell 會將它轉換成一個物件的集合。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotContainsSet
Aliases: INotContains

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotIn

指出此 Cmdlet 會在屬性值與任何指定的值不完全相符時取得物件。

例如：`Get-Process | where -Value "svchost" -NotIn -Property ProcessName`

如果 **value** 值是單一物件，則 PowerShell 會將它轉換成一個物件的集合。

如果物件的屬性值是陣列，則 PowerShell 會使用參考相等來判斷是否相符。 `Where-Object` 只有當 **屬性** 的值和 **值** 的任何值都不是物件的相同實例時，才會傳回物件。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotInSet
Aliases: INotIn

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotLike

指出此 Cmdlet 會在屬性值與包含萬用字元的值不相符時取得物件。

例如：`Get-Process | where ProcessName -NotLike "*host"`

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotLikeSet
Aliases: INotLike

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotMatch

指出當屬性值與指定的正則運算式不相符時，此 Cmdlet 會取得物件。 當輸入是純量時，相符的值會儲存在 `$Matches` 自動變數中。

例如：`Get-Process | where ProcessName -NotMatch "PowerShell"`

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotMatchSet
Aliases: INotMatch

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Property

指定物件屬性的名稱。 參數名稱（ **Property** ）是選擇性的。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.String
Parameter Sets: EqualSet, LessOrEqualSet, CaseSensitiveEqualSet, NotEqualSet, CaseSensitiveNotEqualSet, GreaterThanSet, CaseSensitiveGreaterThanSet, LessThanSet, CaseSensitiveLessThanSet, GreaterOrEqualSet, CaseSensitiveGreaterOrEqualSet, CaseSensitiveLessOrEqualSet, LikeSet, CaseSensitiveLikeSet, NotLikeSet, CaseSensitiveNotLikeSet, MatchSet, CaseSensitiveMatchSet, NotMatchSet, CaseSensitiveNotMatchSet, ContainsSet, CaseSensitiveContainsSet, NotContainsSet, CaseSensitiveNotContainsSet, InSet, CaseSensitiveInSet, NotInSet, CaseSensitiveNotInSet, IsSet, IsNotSet, Not
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Value

指定屬性值。 參數名稱， **值** 是選擇性的。 此參數與下列比較參數搭配使用時，可接受萬用字元：

- **CLike**
- **CNotLike**
- **喜歡**
- **NotLike**

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Object
Parameter Sets: EqualSet, LessOrEqualSet, CaseSensitiveEqualSet, NotEqualSet, CaseSensitiveNotEqualSet, GreaterThanSet, CaseSensitiveGreaterThanSet, LessThanSet, CaseSensitiveLessThanSet, GreaterOrEqualSet, CaseSensitiveGreaterOrEqualSet, CaseSensitiveLessOrEqualSet, LikeSet, CaseSensitiveLikeSet, NotLikeSet, CaseSensitiveNotLikeSet, MatchSet, CaseSensitiveMatchSet, NotMatchSet, CaseSensitiveNotMatchSet, ContainsSet, CaseSensitiveContainsSet, NotContainsSet, CaseSensitiveNotContainsSet, InSet, CaseSensitiveInSet, NotInSet, CaseSensitiveNotInSet, IsSet, IsNotSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Management.Automation.PSObject

您可以透過管道將物件傳送至此 Cmdlet。

## 輸出

### Object

此 Cmdlet 會從輸入物件集傳回選取的專案。

## 注意

從 Windows PowerShell 4.0 開始， `Where` 且已 `ForEach` 新增方法來與集合搭配使用。

您可以在這裡閱讀更多有關這些新方法的資訊 [about_arrays](./About/about_Arrays.md)

## 相關連結

[Compare-Object](../Microsoft.PowerShell.Utility/Compare-Object.md)

[ForEach-Object](ForEach-Object.md)

[Group-Object](../Microsoft.PowerShell.Utility/Group-Object.md)

[Measure-Object](../Microsoft.PowerShell.Utility/Measure-Object.md)

[New-Object](../Microsoft.PowerShell.Utility/New-Object.md)

[Select-Object](../Microsoft.PowerShell.Utility/Select-Object.md)

[Sort-Object](../Microsoft.PowerShell.Utility/Sort-Object.md)

[Tee-Object](../Microsoft.PowerShell.Utility/Tee-Object.md)

