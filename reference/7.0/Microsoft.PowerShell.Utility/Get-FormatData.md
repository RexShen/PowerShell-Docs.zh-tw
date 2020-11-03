---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-formatdata?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-FormatData
ms.openlocfilehash: 22cdfce0ca9e591dfc97a6ac7ef2c1e0f0ed37ab
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201683"
---
# Get-FormatData

## 概要
取得目前工作階段中的格式化資料。

## SYNTAX

```
Get-FormatData [[-TypeName] <String[]>] [-PowerShellVersion <Version>] [<CommonParameters>]
```

## DESCRIPTION

`Get-FormatData`Cmdlet 會取得目前會話中的格式化資料。

會話中的格式化資料包括格式化檔案的格式設定 `Format.ps1xml` ，例如目錄中的檔案 `$PSHOME` 、格式化您匯入會話中之模組的資料，以及使用指令程式將您匯入到會話的命令格式化資料 `Import-PSSession` 。

您可以使用這個 Cmdlet 來檢查格式化資料。 然後，您可以使用 `Export-FormatData` Cmdlet 序列化物件、將它們轉換成 XML，然後將它們儲存在檔案中 `Format.ps1xml` 。

如需有關在 PowerShell 中格式化檔案的詳細資訊，請參閱 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)。

## 範例

### 範例1：取得所有格式化資料

此範例會取得會話中的所有格式化資料。

```powershell
Get-FormatData -PowerShellVersion 5.1
```

> [!IMPORTANT]
> 為確保傳回完整的類型格式資訊，您應該一律在使用的本機叫用時，將 **PowerShellVersion** 參數包含值 `5.1` `Get-FormatData` 。 如果省略參數和值，您可能無法取得所有正確的類型資訊。

### 範例2：依類型名稱取得格式化資料

這個範例會取得名稱開頭為的格式化資料項目 `System.Management.Automation.Cmd` 。

```powershell
Get-FormatData -TypeName 'System.Management.Automation.Cmd*' -PowerShellVersion 5.1
```

### 範例3：檢查格式化資料物件

這個範例示範如何取得格式化資料物件，並檢查其屬性。

```powershell
$F = Get-FormatData -TypeName 'System.Management.Automation.Cmd*' -PowerShellVersion 5.1
$F
```

```Output
TypeName        FormatViewDefinition
--------        --------------------
HelpInfoShort   {help , TableControl}
```

```powershell
$F.FormatViewDefinition[0].control
```

```Output
Headers          : {System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader}
Rows             : {System.Management.Automation.TableControlRow}
AutoSize         : False
HideTableHeaders : False
GroupBy          :
OutOfBand        : False
```

```powershell
$F.FormatViewDefinition[0].control.Headers
```

```Output
Label       Alignment Width
-----       --------- -----
CommandType Undefined    15
Name        Undefined    50
Version     Undefined    10
Source      Undefined     0
```

### 範例4：取得格式化資料並匯出

這個範例示範如何使用 `Get-FormatData` 和 `Export-FormatData` 來匯出模組所新增的格式化資料。

```powershell
$A = Get-FormatData -PowerShellVersion 5.1
Import-Module bitstransfer
$B = Get-FormatData -PowerShellVersion 5.1
Compare-Object $A $B
```

```Output
InputObject                                                SideIndicator
-----------                                                -------------
Microsoft.BackgroundIntelligentTransfer.Management.BitsJob =>
```

```powershell
Get-FormatData *bits* | Export-FormatData -FilePath c:\test\bits.format.ps1xml
Get-Content c:\test\bits.format.ps1xml
```

```Output
<?xml version="1.0" encoding="utf-8"?><Configuration><ViewDefinitions>
<View><Name>Microsoft.BackgroundIntelligentTransfer.Management.BitsJob</Name>
...
```

前四個命令會使用 `Get-FormatData` 、 `Import-Module` 和 `Compare-Object` Cmdlet 來識別 **BitsTransfer** 模組新增至會話的格式類型。

第五個命令會使用 `Get-FormatData` Cmdlet 來取得 **BitsTransfer** 模組所新增的格式類型。 它使用管線運算子 (`|`) 將格式類型物件傳送至 `Export-FormatData` Cmdlet，以將它轉換回 XML，並將它儲存在指定的檔案中 `format.ps1xml` 。

最後一個命令會顯示檔案內容的摘要 `format.ps1xml` 。

### 範例5：根據指定的 PowerShell 版本取得格式化資料

此範例示範如何使用 `Get-FormatData` 來取得指定之 **TypeName** 和 PowerShell 版本的格式資料。

```powershell
Get-FormatData -TypeName 'Microsoft.Powershell.Utility.FileHash' -PowerShellVersion $PSVersionTable.PSVersion

TypeNames                               FormatViewDefinition
---------                               --------------------
{Microsoft.Powershell.Utility.FileHash} {Microsoft.Powershell.Utility.FileHash}
```

## PARAMETERS

### -PowerShellVersion

指定此 Cmdlet 取得格式化資料的 PowerShell 版本。 輸入以句號分隔的兩位數數位。

此參數是在 PowerShell 5.1 中新增的，可改善執行舊版 PowerShell 的遠端電腦的相容性。

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeName

指定此 Cmdlet 為格式化資料取得的類型名稱。
輸入類型名稱。
允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### System.Management.Automation.ExtendedTypeDefinition

## 注意

## 相關連結

[Export-FormatData](Export-FormatData.md)

[Update-FormatData](Update-FormatData.md)
