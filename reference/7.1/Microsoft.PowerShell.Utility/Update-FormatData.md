---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-formatdata?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-FormatData
ms.openlocfilehash: 8e4f9e82674baa90b8c7242921e4838f7470a85a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205064"
---
# Update-FormatData

## 概要
更新目前工作階段中的格式化資料。

## SYNTAX

```
Update-FormatData [[-AppendPath] <String[]>] [-PrependPath <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION

此 Cmdlet 會將格式化檔案 `Update-FormatData` 中的格式化資料重載至目前的會話。 此 Cmdlet 可讓您更新格式化資料，而不需要重新開機 PowerShell。

如果沒有參數，會 `Update-FormatData` 重載它先前載入的格式化檔案。
您可以使用的參數， `Update-FormatData` 將新的格式化檔案新增到會話。

格式化檔案是具有副檔名的 XML 格式文字檔 `format.ps1xml` 。 檔案中的格式化資料會定義工作階段中 Microsoft .NET Framework 物件的顯示方式。

PowerShell 啟動時，會從 PowerShell 原始程式碼載入格式資料。 不過，您可以建立自訂的 format.ps1xml 檔案，以更新目前會話中的格式。 您可以使用 `Update-FormatData` 將格式化資料重載目前的會話，而不需要重新開機 PowerShell。 當您已新增或變更格式化檔案，但不想中斷工作階段時，這非常有用。

如需有關在 PowerShell 中格式化檔案的詳細資訊，請參閱 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)。

## 範例

### 範例 1︰重新載入先前載入的格式化檔案

```powershell
Update-FormatData
```

這個命令會重新載入它先前載入的格式化檔案。

### 範例 2︰重新載入格式化檔案以及追蹤和記錄格式化檔案

```powershell
Update-FormatData -AppendPath "trace.format.ps1xml, log.format.ps1xml"
```

這個命令會將格式化檔案重新載入工作階段，包括 Trace.format.ps1xml 和 Log.format.ps1xml 這兩個新檔案。

由於此命令使用 **AppendPath** 參數，因此，新檔案中的格式化資料會在來自內建檔案的格式化資料之後載入。

因為新檔案包含內建檔案中未參考物件的格式化資料，所以會使用 **AppendPath** 參數。

### 範例 3︰編輯格式化檔案，並重新載入

```powershell
Update-FormatData -PrependPath "c:\test\NewFiles.format.ps1xml"

# Edit the NewFiles.format.ps1 file.

Update-FormatData
```

這個範例示範如何在編輯格式化檔案之後重新載入它。

第一個命令將 NewFiles.format.ps1xml 檔案新增至工作階段。 它會使用 **PrependPath** 參數，因為檔案包含內建檔案中所參考物件的格式化資料。

新增 NewFiles.format.ps1xml 檔案並在這些工作階段中測試該檔案之後，作者編輯了該檔案。

第二個命令會使用 `Update-FormatData` Cmdlet 來重載格式化檔案。 因為先前已載入 NewFiles.format.ps1xml 檔案，所以 `Update-FormatData` 會自動重載，而不使用參數。

## PARAMETERS

### -AppendPath

指定此 Cmdlet 要新增至工作階段的格式化檔案。 這些檔案會在 PowerShell 載入內建的格式化檔案之後載入。

將 .NET 物件格式化時，PowerShell 會使用它針對每個 .NET 類型所找到的第一個格式化定義。 如果您使用 **AppendPath** 參數，則 PowerShell 會在遇到您要新增的格式化資料之前，先從內建檔案搜尋資料。

使用這個參數來新增格式化 .NET 物件的檔案，而內建的格式化檔案未參考該物件。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSPath, Path

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -PrependPath

指定此 Cmdlet 要新增至工作階段的格式化檔案。 這些檔案會在 PowerShell 載入內建的格式化檔案之前載入。

將 .NET 物件格式化時，PowerShell 會使用它針對每個 .NET 類型所找到的第一個格式化定義。 如果您使用 **PrependPath** 參數，則 PowerShell 會在遇到來自內建檔案的格式化資料之前，從您要新增的檔案中搜尋資料。

使用這個參數來新增格式化 .NET 物件的檔案，而內建的格式化檔案亦參考該物件。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
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

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

您可以使用管線將包含附加路徑的字串傳送至 `Update-FormatData` 。

## 輸出

### 無

此 Cmdlet 不會傳回任何輸出。

## 注意

- `Update-FormatData` 也會在會話中，針對從模組匯入的命令更新格式化資料。 如果模組的格式化檔案變更，您可以執行 `Update-FormatData` 命令來更新匯入命令的格式化資料。 您不需要再次匯入模組。

## 相關連結

[Get-FormatData](Get-FormatData.md)

[Export-FormatData](Export-FormatData.md)
