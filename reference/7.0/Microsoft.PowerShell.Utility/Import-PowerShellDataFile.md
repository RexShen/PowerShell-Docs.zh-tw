---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-powershelldatafile?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PowerShellDataFile
ms.openlocfilehash: f25191d27013469023b9fcfb03650a8693c6ddb4
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201152"
---
# Import-PowerShellDataFile

## 概要
匯入檔案中的值 `.PSD1` ，而不叫用其內容。

## SYNTAX

### ByPath (預設值)

```
Import-PowerShellDataFile [-Path] <String[]> [<CommonParameters>]
```

### ByLiteralPath

```
Import-PowerShellDataFile [-LiteralPath] <String[]> [<CommonParameters>]
```

## DESCRIPTION

此 `Import-PowerShellDataFile` Cmdlet 會從檔案中定義的雜湊表安全地匯入機碼值組 `.PSD1` 。 您可以使用檔案內容來匯入這些值 `Invoke-Expression` 。
但是，會 `Invoke-Expression` 執行檔案中包含的任何程式碼。 這可能會產生不必要的結果，或執行不安全的程式碼。 `Import-PowerShellDataFile` 匯入資料，而不叫用程式碼。

## 範例

### 範例1：從 .PSD1 取出值

這個範例會抓取儲存在檔案中的雜湊表中的機碼值組 `Configuration.psd1` 。 `Get-Content` 用來顯示檔案的內容 `Configuration.psd1` 。

```powershell
Get-Content .\Configuration.psd1
$config = Import-PowerShellDataFile .\Configuration.psd1
$config.AllNodes
```

```Output
@{
    AllNodes = @(
        @{
            NodeName = 'DSC-01'
        }
        @{
            NodeName = 'DSC-02'
        }
    )
}

Name                           Value
----                           -----
NodeName                       DSC-01
NodeName                       DSC-02
```

## PARAMETERS

### -LiteralPath

要匯入之檔案的路徑。 路徑中的所有字元都會被視為常值。
不會處理萬用字元。

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

要匯入之檔案的路徑。 允許使用萬用字元，但只會匯入第一個相符的檔案。

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

## 輸出

### System.Collections.Hashtable

## 注意

## 相關連結

[Invoke-Expression](Invoke-Expression.md)

[Import-LocalizedData](Import-LocalizedData.md)
