---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/19/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-list?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-List
ms.openlocfilehash: a025432e8aed93f6668c676161c21377d0ba225c
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2020
ms.locfileid: "93206023"
---
# Format-List

## 概要
將輸出格式化為屬性清單，其中每個屬性會顯示在新的一行上。

## SYNTAX

```
Format-List [[-Property] <Object[]>] [-GroupBy <Object>] [-View <string>] [-ShowError]
[-DisplayError] [-Force] [-Expand <string>] [-InputObject <psobject>] [<CommonParameters>]
```

## DESCRIPTION

`Format-List`Cmdlet 會將命令的輸出格式化為屬性清單，其中每個屬性都會顯示在個別的行上。 您可以使用 `Format-List` ，將物件的所有或選取屬性格式化並顯示為清單 (格式清單 * ) 。

由於清單中的每個專案都有更多可用空間，而不是在資料表中，因此 PowerShell 會在清單中顯示更多物件屬性，且屬性值較不可能被截斷。

## 範例

### 範例1：格式化電腦服務

```powershell
Get-Service | Format-List
```

此命令將電腦上關於服務的資訊格式化為清單。 根據預設，服務會格式化為表格。 `Get-Service`Cmdlet 會取得代表電腦上之服務的物件。 管線運算子 (|) 透過管線將結果傳遞給 `Format-List` 。
然後，此 `Format-List` 命令會格式化清單中的服務資訊，並將其傳送至預設的輸出 Cmdlet 以供顯示。

### 範例2：格式化 .PS1XML 檔案

這些命令會以清單形式顯示 PowerShell 目錄中 .PS1XML 檔案的相關資訊。

```powershell
$A = Get-ChildItem $pshome\*.ps1xml
Format-List -InputObject $A
```

第一個命令會取得代表檔案的物件，並將它們儲存在 `$A` 變數中。

第二個命令會使用 `Format-List` 來格式化中所儲存之物件的相關資訊 `$A` 。 此命令會使用 **InputObject** 參數將變數傳遞給 `Format-List` ，然後將格式化的輸出傳送至預設的 output Cmdlet 以供顯示。

### 範例3：依名稱格式化進程屬性

此命令顯示電腦上每個處理程序的名稱、基本優先順序和優先順序類別。

```powershell
Get-Process | Format-List -Property name, basepriority, priorityclass
```

它會使用 `Get-Process` Cmdlet 來取得代表每個處理常式的物件。 管線運算子 (|) 透過管線將處理常式物件傳遞至 `Format-List` 。 `Format-List` 將處理常式格式化為指定屬性的清單。 *屬性* 參數名稱為選擇性，因此您可以省略它。

### 範例4：格式化進程的所有屬性

此命令顯示 Winlogon 處理程序的所有屬性。

```powershell
Get-Process winlogon | Format-List -Property *
```

它使用 Get-Process Cmdlet 取得代表 Winlogon 處理程序的物件。 管線運算子 (|) 透過管線將 Winlogon 處理常式物件傳遞至 `Format-List` 。 命令使用 *Property* 參數指定屬性，並使用 \* 來指出所有屬性。
因為 *Property* 參數的名稱是選擇性的，所以您可以省略它，並將命令輸入為 `Format-List *` 。 `Format-List` 自動將結果傳送至預設的輸出 Cmdlet 以供顯示。

### 範例5：針對格式錯誤進行疑難排解

下列範例顯示使用運算式新增 **DisplayError** 或 **ShowError** 參數的結果。

```powershell
PC /> Get-Date | Format-List DayOfWeek,{ $_ / $null } -DisplayError

DayOfWeek    : Friday
 $_ / $null  : #ERR

PC /> Get-Date | Format-List DayOfWeek,{ $_ / $null } -ShowError

DayOfWeek    : Friday
 $_ / $null  :

Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 7:59:23 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## PARAMETERS

### -DisplayError

指出此 Cmdlet 會在命令列顯示錯誤。 這個參數很少使用，但是當您在命令中將運算式格式化 `Format-List` ，而這些運算式似乎沒有作用時，便可以使用這個參數做為偵錯工具的協助工具。

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

### -Expand

指定格式化的集合物件，以及集合中的物件。 這個參數是設計來將支援 ICollection (System.Collections) 介面的物件格式化。 預設值為 EnumOnly。 此參數可接受的值為：

- EnumOnly. 顯示集合中物件的屬性。
- CoreOnly. 顯示集合物件的屬性。
- 兩者。 顯示集合物件的屬性及集合中物件的屬性。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

指出此 Cmdlet 會顯示所有錯誤資訊。 搭配 **DisplayError** 或 **ShowError** 參數使用。 根據預設，將錯誤物件寫入錯誤或顯示串流時，只會顯示某些錯誤資訊。

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

### -GroupBy

根據共用屬性或值，指定群組中的輸出。 輸入輸出的運算式或屬性。

**GroupBy** 參數的值可以是新的計算屬性。 計算的屬性可以是腳本區塊或雜湊表。 有效的索引鍵/值組為：

- 名稱 (或標籤) - `<string>`
- 運算式 `<string>` 或 `<script block>`
- 字串 `<string>`

如需詳細資訊，請參閱 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定要格式化的物件。 輸入包含物件的變數，或輸入可取得物件的命令或運算式。

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

### -Property

指定顯示中出現的物件屬性及其出現順序。
允許使用萬用字元。

如果省略這個參數，則出現在顯示中的屬性將取決於所顯示的物件。 參數名稱 "Property" 是選擇性的。 您無法在相同的命令中使用 **Property** 與 **View** 參數。

**Property** 參數的值可以是新的計算屬性。 計算的屬性可以是腳本區塊或雜湊表。 有效的索引鍵/值組為：

- 名稱 (或標籤) - `<string>`
- 運算式 `<string>` 或 `<script block>`
- 字串 `<string>`

如需詳細資訊，請參閱 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ShowError

指出此 Cmdlet 會透過管線傳送錯誤。 這個參數很少使用，但是當您在命令中將運算式格式化 `Format-List` ，而這些運算式似乎沒有作用時，便可以使用這個參數做為偵錯工具的協助工具。

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

### -View

指定替代清單格式或視圖的名稱。 您無法在相同的命令中使用 **Property** 與 **View** 參數。

```yaml
Type: System.String
Parameter Sets: (All)
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

您可以透過管線將任何物件傳送至 `Format-List` 。

## 輸出

### Microsoft.PowerShell.Commands.Internal.Format

`Format-List` 傳回代表清單的格式物件。

## 注意

您也可以使用內建的別名（FL）來參考 Format-List。 如需詳細資訊，請參閱 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。

格式 Cmdlet （例如 `Format-List` ）會排列要顯示的資料，但不會顯示它。
PowerShell 的輸出功能和包含 Out 動詞 (Out Cmdlet 的 Cmdlet 會顯示資料) ，例如 `Out-Host` 或 `Out-File` 。

如果您未使用 format Cmdlet，則 PowerShell 會針對它所顯示的每個物件套用該預設格式。

**GroupBy** 參數假設物件已排序。 使用 Sort-Object 之前，請先使用 `Format-List` 來將物件分組。

**View** 參數可讓您指定表格的替代格式。 您可以使用 PowerShell 目錄的檔案中所定義的視圖 `*.format.PS1XML` ，也可以在新的 .ps1xml 檔案中建立自己的視圖，並使用 Update-FormatData Cmdlet 將它們包含在 powershell 中。

**View** 參數的替代視圖必須使用清單格式，否則命令會失敗。 如果替代視圖為數據表，請使用 `Format-Table` 。 如果替代視圖不是清單或資料表，請使用 `Format-Custom` 。

## 相關連結

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[Format-Custom](Format-Custom.md)

[Format-Hex](Format-Hex.md)

[Format-Table](Format-Table.md)

[Format-Wide](Format-Wide.md)
