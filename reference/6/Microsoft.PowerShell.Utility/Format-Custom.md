---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-custom?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Custom
ms.openlocfilehash: 28914b86c86d5c16f09c81a5dc70ed1e05123b3e
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2020
ms.locfileid: "93205912"
---
# Format-Custom

## 概要
使用自訂檢視來格式化輸出。

## SYNTAX

```
Format-Custom [[-Property] <Object[]>] [-Depth <Int32>] [-GroupBy <Object>] [-View <String>]
 [-ShowError] [-DisplayError] [-Force] [-Expand <String>] [-InputObject <PSObject>]
 [<CommonParameters>]
```

## DESCRIPTION

`Format-Custom`Cmdlet 會格式化命令的輸出，如替代視圖中所定義。
`Format-Custom` 的設計目的是要顯示不只是資料表或只是清單的視圖。 您可以使用 PowerShell 中定義的視圖，也可以在新的檔案中建立自己的視圖， `format.ps1xml` 並使用 `Update-FormatData` Cmdlet 將它們新增至 PowerShell。

## 範例

### 範例1：使用自訂視圖格式化輸出

```powershell
Get-Command Start-Transcript | Format-Custom -View MyView
```

此命令會 `Start-Transcript` 以 MyView view （由使用者建立的自訂視圖）所定義的格式來格式化 Cmdlet 的相關資訊。 若要成功執行此命令，您必須先建立新的 .PS1XML 檔案、定義 **MyView** 視圖，然後使用 `Update-FormatData` 命令將 .ps1xml 檔案新增至 PowerShell。

### 範例2：使用預設 view 格式化輸出

```powershell
Get-Process Winlogon | Format-Custom
```

此命令會在替代自訂視圖中格式化 **Winlogon** 處理常式的相關資訊。
因為命令不使用 **View** 參數，所以會 `Format-Custom` 使用預設的自訂視圖來格式化資料。

### 範例3：針對格式錯誤進行疑難排解

下列範例顯示使用運算式新增 **DisplayError** 或 **ShowError** 參數的結果。

```powershell
PC /> Get-Date | Format-Custom DayOfWeek,{ $_ / $null } -DisplayError

class DateTime
{
  DayOfWeek = Friday
   $_ / $null  = #ERR
}


PC /> Get-Date | Format-Custom DayOfWeek,{ $_ / $null } -ShowError

class DateTime
{
  DayOfWeek = Friday
   $_ / $null  =
}

Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 8:01:04 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## PARAMETERS

### -Depth

指定畫面上顯示的欄數。

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

在命令列中顯示錯誤。 這個參數很少使用，但是當您在命令中將運算式格式化 `Format-Custom` ，而這些運算式似乎沒有作用時，便可以使用這個參數做為偵錯工具的協助工具。

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

將集合物件以及集合中的物件格式化。 這個參數是設計來格式化支援 **system.object** 介面的物件。 預設值為 **EnumOnly** 。

有效值為：

- EnumOnly：顯示集合中物件的屬性。
- CoreOnly：顯示集合物件的屬性。
- Both：顯示集合物件的屬性和集合中的物件。

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

指示 Cmdlet 顯示所有錯誤資訊。 搭配 **DisplayError** 或 **ShowError** 參數使用。 根據預設，將錯誤物件寫入錯誤或顯示串流時，只會顯示某些錯誤資訊。

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

如果省略這個參數，則出現在顯示中的屬性將取決於所顯示的物件。 [參數名稱] **屬性** 是選擇性的。 您無法在相同的命令中使用 **Property** 與 **View** 參數。

**Property** 參數的值可以是新的計算屬性。 計算的屬性可以是腳本區塊或雜湊表。 有效的索引鍵/值組為：

- 運算式 `<string>` 或 `<script block>`
- 解析度 `<int32>`

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

透過管線傳送錯誤。 這個參數很少使用，但是當您在命令中將運算式格式化 `Format-Custom` ，而這些運算式似乎沒有作用時，便可以使用這個參數做為偵錯工具的協助工具。

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

指定替代格式或視圖的名稱。 如果您省略此參數，則會 `Format-Custom` 使用預設的自訂視圖。 您無法在相同的命令中使用 **Property** 與 **View** 參數。

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

您可以透過管線將任何物件傳送至 `Format-Custom` 。

## 輸出

### Microsoft.PowerShell.Commands.Internal.Format

`Format-Custom` 傳回代表顯示的格式物件。

## 注意

`Format-Custom` 的設計目的是要顯示不只是資料表或只是清單的視圖。 若要顯示替代資料表視圖，請使用 `Format-Table` 。 若要顯示替代清單視圖，請使用 `Format-List` 。

您也可以 `Format-Custom` 使用內建的別名來參考 `fc` 。 如需詳細資訊，請參閱 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。

**GroupBy** 參數假設物件已排序。 使用 `Format-Custom` 來群組物件之前，請使用 `Sort-Object` 來排序物件。

## 相關連結

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[Format-Hex](Format-Hex.md)

[Format-List](Format-List.md)

[Format-Table](Format-Table.md)

[Format-Wide](Format-Wide.md)

[Get-Process](../Microsoft.PowerShell.Management/Get-Process.md)
