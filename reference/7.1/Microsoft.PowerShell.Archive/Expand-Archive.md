---
external help file: Microsoft.PowerShell.Archive-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Archive
ms.date: 07/17/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.archive/expand-archive?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Expand-Archive
ms.openlocfilehash: 6b89512ebc786a47ae47dd2cd8f51cb532382e02
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2020
ms.locfileid: "93205323"
---
# Expand-Archive

## 概要
從指定的封存 (壓縮) 檔案中解壓縮檔案。

## SYNTAX

### 路徑 (預設值)

```
Expand-Archive [-Path] <String> [[-DestinationPath] <String>] [-Force] [-PassThru] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### LiteralPath

```
Expand-Archive -LiteralPath <String> [[-DestinationPath] <String>] [-Force] [-PassThru] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

Cmdlet 會將 `Expand-Archive` 指定之壓縮封存檔案中的檔案解壓縮到指定的目的地資料夾。 封存檔案可讓多個檔案封裝並選擇性地壓縮成單一壓縮檔案，以方便散發和儲存。

## 範例

### 範例1：將封存的內容解壓縮

此範例會將現有封存檔案的內容解壓縮到 **DestinationPath** 參數所指定的資料夾中。

```powershell
Expand-Archive -LiteralPath 'C:\Archives\Draft[v1].Zip' -DestinationPath C:\Reference
```

在此範例中，會使用 **LiteralPath** 參數，因為檔案名包含可解釋為萬用字元的字元。

### 範例2：將封存的內容解壓縮到目前的資料夾中

此範例會將目前資料夾中現有封存檔案的內容，解壓縮到 **DestinationPath** 參數所指定的資料夾中。

```powershell
Expand-Archive -Path Draftv2.Zip -DestinationPath C:\Reference
```

## PARAMETERS

### -DestinationPath

依預設， `Expand-Archive` 會在目前的位置中建立一個與 ZIP 檔案相同名稱的資料夾。 參數可讓您指定不同資料夾的路徑。 如果目的檔案夾不存在，則會加以建立。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: A folder in the current location
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

強制執行命令而不要求使用者確認。

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

### -LiteralPath

指定封存檔案的路徑。 與 **Path** 參數不同， **LiteralPath** 的值將完全依照其輸入值來使用。 不支援萬用字元。 如果路徑包含 escape 字元，請用單引號括住每個 escape 字元，以指示 PowerShell 不要將任何字元解釋為 escape 序列。

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

讓 Cmdlet 輸出從封存中展開的檔案清單。

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

### -Path

指定封存檔案的路徑。

```yaml
Type: System.String
Parameter Sets: Path
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

顯示執行 Cmdlet 後會發生的情況。 Cmdlet 並不會執行。

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

您可以使用管線將包含路徑的字串傳送至現有的保存檔案。

## 輸出

### FileSystemInfo

`-PassThru`使用參數時，此 Cmdlet 會輸出從封存擴充的檔案清單。

## 注意

[ZIP 檔案規格](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT)不會指定編碼包含非 ASCII 字元之檔案名的標準方式。 此 `Compress-Archive` Cmdlet 會使用 utf-8 編碼。 其他 ZIP 封存工具可能會使用不同的編碼配置。 使用 UTF-8 編碼方式解壓縮未儲存的檔案時，會使用在封存 `Expand-Archive` 中找到的原始值。 這可能會產生與儲存在封存中的來原始檔案名不同的檔案名。

## 相關連結

[Compress-Archive](compress-archive.md)
