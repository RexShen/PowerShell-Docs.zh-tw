---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/join-string?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Join-String
ms.openlocfilehash: bae6b8558a3e12bf161d8f0ec12037841a20cc04
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201884"
---
# Join-String

## 概要
將管線中的物件合併成單一字串。

## SYNTAX

### Default (預設值)

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-UseCulture] [-InputObject <PSObject[]>] [<CommonParameters>]
```

### SingleQuote

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-SingleQuote] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

### DoubleQuote

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-DoubleQuote] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

### 格式

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-FormatString <String>] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

## DESCRIPTION

此 `Join-String` Cmdlet 會將管線物件中的文字聯結或合併成單一字串。

如果未指定任何參數，則會將管線物件轉換成字串，並使用預設分隔符號聯結 `$OFS` 。

藉由指定屬性名稱，屬性的值會轉換成字串，並加入字串。

您可以使用腳本區塊，而不是屬性名稱。 腳本區塊的結果會在聯結之前轉換成字串，以形成結果。 它可以合併物件屬性的文字，或是轉換成字串的物件結果。

此 Cmdlet 是在 PowerShell 6.2 中引進。

## 範例

### 範例1：聯結目錄名稱

<!-- markdownlint-disable MD038 -->
此範例會聯結目錄名稱、將輸出包裝在雙引號中，並以逗號和空格分隔目錄名稱 (`, `) 。 輸出是字串物件。

```powershell
Get-ChildItem -Directory C:\ | Join-String -Property Name -DoubleQuote -Separator ', '
```

```Output
"PerfLogs", "Program Files", "Program Files (x86)", "Users", "Windows"
```

`Get-ChildItem` 使用 **Directory** 參數取得磁片磁碟機的所有目錄名稱 `C:\` 。
物件會向下傳送到管線 `Join-String` 。 **Property** 參數會指定目錄名稱。 **DoubleQuote** 參數會以雙引號括住目錄名稱。
**分隔符號** 參數指定使用逗號和空格 (`, `) 來分隔目錄名稱。

這些 `Get-ChildItem` 物件是 **DirectoryInfo** ，並 `Join-String` 將物件轉換為 **system.string** 。

### 範例2：使用屬性子字串聯結目錄名稱

這個範例會使用 substring 方法來取得前四個字母的目錄名稱、以單引號括住輸出，然後以分號分隔目錄名稱 (`;`) 。

```powershell
Get-ChildItem -Directory C:\ | Join-String -Property {$_.Name.SubString(0,4)} -SingleQuote -Separator ';'
```

```Output
'Perf';'Prog';'Prog';'User';'Wind'
```

`Get-ChildItem` 使用 **Directory** 參數取得磁片磁碟機的所有目錄名稱 `C:\` 。
物件會向下傳送到管線 `Join-String` 。

**屬性** 參數腳本區塊會使用自動變數 (`$_`) 來指定每個物件的 **名稱** 屬性子字串。 子字串會取得每個目錄名稱的前四個字母。 子字串指定字元開始和結束位置。 **SingleQuote** 參數會以單引號括住目錄名稱。 **分隔符號** 參數指定使用分號 (`;`) 來分隔目錄名稱。

如需自動變數和子字串的詳細資訊，請參閱 [about_Automatic_Variables](../microsoft.powershell.core/about/about_automatic_variables.md) 和 [Substring](/dotnet/api/system.string.substring)。

### 範例3：在個別行上顯示聯結輸出

此範例會在個別的行上將服務名稱與每個服務聯結，並以索引標籤進行縮排。

```powershell
Get-Service -Name se* | Join-String -Property Name -Separator "`r`n`t" -OutputPrefix "Services:`n`t"
```

```Output
Services:
    seclogon
    SecurityHealthService
    SEMgrSvc
    SENS
    Sense
    SensorDataService
    SensorService
    SensrSvc
    SessionEnv
```

`Get-Service` 使用 **Name** 參數搭配來指定以開頭的服務 `se*` 。 星號 (`*`) 是任何字元的萬用字元。

物件會向下傳送至 `Join-String` 使用 **Property** 參數來指定服務名稱的管線。 **分隔符號** 參數指定三個特殊字元，代表換行字元 (`` `r ``) 、新行 (`` `n ``) 和 tab (`` `t ``) 。 **OutputPrefix** 會插入標籤 **服務：** 在輸出的第一行前面加上新行和索引標籤。

如需特殊字元的詳細資訊，請參閱 [about_Special_Characters](..//microsoft.powershell.core/about/about_special_characters.md)。

### 範例4：從物件建立類別定義

此範例會使用現有的物件作為範本，以產生 PowerShell 類別定義。

這個程式碼範例會使用展開來縮減行長度，並提高可讀性。 如需詳細資訊，請參閱 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)。

```powershell
$obj = [pscustomobject] @{Name = "Joe"; Age = 42}
$parms = @{
  Property = "Name"
  FormatString = '  ${0}'
  OutputPrefix = "class {`n"
  OutputSuffix = "`n}`n"
  Separator = "`n"
}
$obj.PSObject.Properties | Join-String @parms
```

```Output
class {
  $Name
  $Age
}
```

## PARAMETERS

### -DoubleQuote

以雙引號括住每個管線物件的字串值。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DoubleQuote
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -格式格式

格式字串，指定每個專案的格式化方式。

```yaml
Type: System.String
Parameter Sets: Format
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定要加入的文字。 輸入包含文字的變數，或輸入可取得要加入字串之物件的命令或運算式。

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -OutputPrefix

在輸出字串之前插入的文字。 字串可以包含特殊字元，例如， `` `r `` 換行字元 () 、換行 (`` `n ``) 和 tab (`` `t ``) 。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: op

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputSuffix

附加至輸出字串的文字。 字串可以包含特殊字元，例如， `` `r `` 換行字元 () 、換行 (`` `n ``) 和 tab (`` `t ``) 。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: os

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Property

將管線物件投射為文字的屬性或屬性運算式的名稱。

```yaml
Type: Microsoft.PowerShell.Commands.PSPropertyExpression
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Separator

在每個管線物件的文字之間插入的文字或字元，例如逗號或分號。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SingleQuote

以單引號括住每個管線物件的字串值。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SingleQuote
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseCulture

使用目前文化特性的清單分隔字元做為專案分隔符號。 若要尋找文化特性的清單分隔符號，請使用下列命令： `(Get-Culture).TextInfo.ListSeparator` 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Management.Automation.PSObject

## 輸出

### System.String

## 注意

## 相關連結

[about_Automatic_Variables](../microsoft.powershell.core/about/about_automatic_variables.md)

[about_Special_Characters](..//microsoft.powershell.core/about/about_special_characters.md)

[子](/dotnet/api/system.string.substring)
