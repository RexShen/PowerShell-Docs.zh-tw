---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-wide?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Wide
ms.openlocfilehash: f26fc996b7fd029ed5994432080e51a1d83ec20e
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2020
ms.locfileid: "93205968"
---
# Format-Wide

## 概要
將物件以每個物件只顯示一個屬性的寬型表格方式格式化。

## SYNTAX

```
Format-Wide [[-Property] <Object>] [-AutoSize] [-Column <int>] [-GroupBy <Object>] [-View <string>]
  [-ShowError] [-DisplayError] [-Force] [-Expand <string>] [-InputObject <psobject>]
  [<CommonParameters>]
```

## DESCRIPTION

`Format-Wide`Cmdlet 會將物件格式化為寬型資料表，只顯示每個物件的一個屬性。 您可以使用 **property** 參數來決定要顯示哪一個屬性。

## 範例

### 範例1：在目前的目錄中格式化檔案的名稱

這個命令會在螢幕上以三欄顯示目前目錄中檔案的名稱。

```powershell
Get-ChildItem | Format-Wide -Column 3
```

Get-ChildItem Cmdlet 會取得代表目錄中每個檔案的物件。 管線運算子 (|) 透過管線將檔案物件傳遞給，以將 `Format-Wide` 它們格式化以進行輸出。 **Column** 參數會指定資料行的數目。

### 範例2：登錄機碼的格式名稱

這個命令會顯示 HKEY_CURRENT_USER\Software\Microsoft 機碼中登錄機碼的名稱。

```powershell
Get-ChildItem HKCU:\software\microsoft | Format-Wide -Property pschildname -AutoSize
```

Get-ChildItem Cmdlet 會取得代表機碼的物件。 路徑會指定為 HKCU：、PowerShell 登錄提供者所公開的其中一個磁片磁碟機，後面接著機碼路徑。 管線運算子 (|) 透過管線將登錄機碼物件傳遞給 `Format-Wide` ，以將它們格式化以進行輸出。 **Property** 參數會指定屬性的名稱，而 **AutoSize** 參數則會調整資料行的可讀性。

### 範例3：針對格式錯誤進行疑難排解

下列範例顯示使用運算式新增 **DisplayError** 或 **ShowError** 參數的結果。

```powershell
PS /> Get-Date | Format-Wide { $_ / $null } -DisplayError


#ERR

PS /> Get-Date | Format-Wide { $_ / $null } -ShowError


Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 8:18:01 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## PARAMETERS

### -AutoSize

根據資料的寬度調整欄大小和欄數。 根據預設，欄大小和欄數是由檢視決定。 您無法在同一個命令中使用 **AutoSize** 與 **Column** 參數。

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

### -Column

指定畫面上顯示的欄數。 您無法在同一個命令中使用 **AutoSize** 與 **Column** 參數。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisplayError

在命令列中顯示錯誤。 這個參數很少使用，但是當您在命令中將運算式格式化 `Format-Wide` ，而這些運算式似乎沒有作用時，便可以使用這個參數做為偵錯工具的協助工具。

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

將集合物件以及集合中的物件格式化。 這個參數是設計來將支援 ICollection (System.Collections) 介面的物件格式化。 預設值為 **EnumOnly** 。

有效值為：

- EnumOnly：顯示集合中物件的屬性。
- CoreOnly：顯示集合物件的屬性。
- Both：顯示集合物件的屬性及集合中物件的屬性。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: EnumOnly
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

指出此 Cmdlet 會覆寫導致命令無法成功的限制，因為變更不會危及安全性。 例如， **Force** 會覆寫唯讀屬性或建立目錄來完成檔案路徑，但不會嘗試變更檔案權限。

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

根據共用屬性或值將輸出分組格式化。 輸入輸出的運算式或屬性。

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

**Property** 參數的值可以是新的計算屬性。計算的屬性可以是腳本區塊或雜湊表。 有效的索引鍵/值組為：

- 運算式 `<string>` 或 `<script block>`
- 字串 `<string>`

如需詳細資訊，請參閱 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ShowError

透過管線傳送錯誤。 這個參數很少使用，但是當您在命令中將運算式格式化 `Format-Wide` ，而這些運算式似乎沒有作用時，便可以使用這個參數做為偵錯工具的協助工具。

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

指定替代資料表格式或視圖的名稱。 您無法在相同的命令中使用 **Property** 與 **View** 參數。

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

您可以透過管線將任何物件傳送至 `Format-Wide` 。

## 輸出

### Microsoft.PowerShell.Commands.Internal.Format

`Format-Wide` 傳回代表資料表的格式物件。

## 注意

您也可以 `Format-Wide` 使用內建的別名來參考 `fw` 。 如需詳細資訊，請參閱 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。

**GroupBy** 參數假設物件已排序。 使用 `Sort-Object` 之前，請先使用 `Format-Custom` 來將物件分組。

**View** 參數可讓您指定表格的替代格式。 您可以使用 PowerShell 目錄的檔案中所定義的視圖，也 `*.format.PS1XML` 可以在新的 .ps1xml 檔案中建立自己的視圖，並使用 `Update-FormatData` Cmdlet 將它們包含在 powershell 中。

**View** 參數的替代視圖必須使用表格格式;如果沒有，則命令會失敗。 如果替代視圖是清單，請使用 `Format-List` 。 如果替代檢視既非清單也非表格，請使用 Format-Custom。

## 相關連結

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[Format-Custom](Format-Custom.md)

[Format-Hex](Format-Hex.md)

[Format-List](Format-List.md)

[Format-Table](Format-Table.md)
