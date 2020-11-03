---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/03/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-item?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-Item
ms.openlocfilehash: f05101f06e4911a797d3342b2b535780badeaefd
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201816"
---
# Rename-Item

## 概要
重新命名 PowerShell 提供者命名空間中的專案。

## SYNTAX

### ByPath (預設值)

```
Rename-Item [-Path] <String> [-NewName] <String> [-Force] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### ByLiteralPath

```
Rename-Item -LiteralPath <String> [-NewName] <String> [-Force] [-PassThru]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## DESCRIPTION

`Rename-Item`Cmdlet 會變更指定專案的名稱。 這個 Cmdlet 不會影響重新命名之項目的內容。

您無法使用 `Rename-Item` 移動專案，例如，藉由指定路徑和新名稱。 若要移動和重新命名專案，請使用 `Move-Item` Cmdlet。

## 範例

### 範例1：重新命名檔案

此命令會將檔案重新命名 `daily_file.txt` 為 `monday_file.txt` 。

```powershell
Rename-Item -Path "c:\logfiles\daily_file.txt" -NewName "monday_file.txt"
```

### 範例2：重新命名和移動專案

您無法使用 `Rename-Item` 來重新命名和移動專案。 具體而言，您無法提供 **NewName** 參數值的路徑，除非路徑與 **path** 參數中指定的路徑相同。 否則只允許新名稱。

這個範例會嘗試將目前目錄中的檔案重新命名 `project.txt` 為 `old-project.txt` 目錄中的 `D:\Archive` 。 結果是顯示在輸出中的錯誤。

```powershell
Rename-Item -Path "project.txt" -NewName "d:\archive\old-project.txt"
```

```Output
Rename-Item : can't rename because the target specified represents a path or device name.
At line:1 char:12
+ Rename-Item <<<<  -path project.txt -NewName d:\archive\old-project.txt
+ CategoryInfo          : InvalidArgument: (:) [Rename-Item], PS>  Move-Item -Path "project.txt" -De
stination "d:\archive\old-project.txt"
```

### 範例3：重新命名登錄機碼

此範例會將登錄機碼從 **廣告** 重新命名為「 **行銷** 」。 當命令完成時，會重新命名機碼，但機碼中的登錄項目則維持不變。

```powershell
Rename-Item -Path "HKLM:\Software\MyCompany\Advertising" -NewName "Marketing"
```

### 範例4：重新命名多個檔案

此範例會將目前目錄中的所有檔案重新命名 `*.txt` 為 `*.log` 。

```powershell
Get-ChildItem *.txt
```

```Output
    Directory: C:\temp\files

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        10/3/2019   7:47 AM           2918 Friday.TXT
-a----        10/3/2019   7:46 AM           2918 Monday.Txt
-a----        10/3/2019   7:47 AM           2918 Wednesday.txt
```

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.Name -replace '.txt','.log' }
Get-ChildItem *.log
```

```Output
    Directory: C:\temp\files

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        10/3/2019   7:47 AM           2918 Friday.log
-a----        10/3/2019   7:46 AM           2918 Monday.log
-a----        10/3/2019   7:47 AM           2918 Wednesday.log
```

指令 `Get-ChildItem` 程式會取得目前資料夾中具有副檔名的所有檔案， `.txt` 然後使用管線將它們傳送至 `Rename-Item` 。 **NewName** 的值是腳本區塊，會在將該值提交給 **NewName** 參數之前執行。

在腳本區塊中， `$_` 自動變數代表透過管線傳遞至命令的每個檔案物件。 腳本區塊會使用 `-replace` 運算子，將每個檔案的副檔名取代為 `.log` 。 請注意，使用 `-replace` 運算子的比對不區分大小寫。

## PARAMETERS

### -Credential

> [!NOTE]
> 使用 PowerShell 安裝的任何提供者都不支援此參數。 若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Force

強制 Cmdlet 重新命名無法以其他方式變更的專案，例如隱藏或唯讀的檔案，或是唯讀的別名或變數。 此 Cmdlet 無法變更常數別名或變數。
實作會依提供者而異。 如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

即使使用 **Force** 參數，Cmdlet 也無法覆寫安全性限制。

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

### -LiteralPath

指定一個或多個位置的路徑。 **LiteralPath** 的值將完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含逸出字元，請將它括在單引號中。 單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NewName

指定項目的新名稱。 只能輸入名稱，而非路徑和名稱。 如果您輸入的路徑與 **path** 參數中指定的路徑不同，則會 `Rename-Item` 產生錯誤。
若要重新命名和移動專案，請使用 `Move-Item` 。

您不能在 **NewName** 參數的值中使用萬用字元。 若要指定多個檔案的名稱，請在正則運算式中使用 **Replace** 運算子。 如需 Replace 運算子的詳細資訊，請參閱 [about_Comparison_Operators](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md)。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

傳回物件，該物件表示管線的專案。 根據預設，此 Cmdlet 不會產生任何輸出。

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

### -Path

指定要重新命名之項目的路徑。

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Confirm

在執行 Cmdlet 前提示您確認。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

顯示執行 Cmdlet 後會發生的情況。
Cmdlet 並不會執行。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### System.String

您可以使用管線將包含路徑的字串傳送至此 Cmdlet。

## 輸出

### None 或代表重新命名之專案的物件。

如果您指定 **PassThru** 參數，此 Cmdlet 會產生代表重新命名之專案的物件。 否則，此 Cmdlet 不會產生任何輸出。

## 注意

`Rename-Item` 的設計目的是要與任何提供者公開的資料搭配使用。 若要列出工作階段中可用的提供者，請輸入 `Get-PsProvider`。 如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 相關連結

[Clear-Item](Clear-Item.md)

[Copy-Item](Copy-Item.md)

[Get-ChildItem](Get-ChildItem.md)

[Get-Item](Get-Item.md)

[Invoke-Item](Invoke-Item.md)

[Move-Item](Move-Item.md)

[New-Item](New-Item.md)

[Remove-Item](Remove-Item.md)

[Rename-ItemProperty](Rename-ItemProperty.md)

[Set-Item](Set-Item.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
