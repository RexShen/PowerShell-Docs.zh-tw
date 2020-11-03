---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-alias?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Alias
ms.openlocfilehash: f501768990c4381841fbf1402dab6cf633e7ea40
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203236"
---
# Import-Alias

## 概要
匯入來自檔案的別名清單。

## SYNTAX

### ByPath (預設值)

```
Import-Alias [-Path] <String> [-Scope <String>] [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Import-Alias -LiteralPath <String> [-Scope <String>] [-PassThru] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION

Cmdlet 會從檔案匯 `Import-Alias` 入別名清單。

從 Windows PowerShell 3.0 開始，做為安全性功能， `Import-Alias` 預設不會覆寫現有的別名。
若要覆寫現有的別名，請在確定別名檔案的內容安全之後，使用 **Force** 參數。

## 範例

### 範例 1︰從檔案匯入別名

```powershell
Import-Alias test.txt
```

此命令從名為 test.txt 的檔案匯入別名資訊。

## PARAMETERS

### -Force

允許 Cmdlet 匯入已定義或是唯讀的別名。
您可以使用下列命令來顯示與目前定義的別名相關的資訊：

`Get-Alias | Select-Object Name, Options`

如果相對應的別名是唯讀的，它將會顯示在 **Options** 屬性的值中。

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

指定包含匯出之別名資訊的檔案的路徑。
與 **Path** 參數不同， **LiteralPath** 參數的值將完全依照其輸入值來使用。
沒有字元會被視為萬用字元。
如果路徑包含逸出字元，請將它括在單引號中。
單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -PassThru

傳回代表您正在使用之項目的物件。
根據預設，此 Cmdlet 不會產生任何輸出。

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

指定包含匯出之別名資訊的檔案的路徑。
允許使用萬用字元，但它們必須解析為單一名稱。

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Scope

指定要匯入別名的範圍。
此參數可接受的值為：

- 全球
- 本機
- 指令碼
- 相對於目前範圍的數字 (0 至範圍數目，0 為目前範圍，1 為其父系)。

Local 為預設值。
如需詳細資訊，請參閱 about_Scopes。

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

您可以使用管線將包含路徑的字串傳送至 `Import-Alias` 。

## 輸出

### 無或 System.Management.Automation.AliasInfo

當您使用 **Passthru** 參數時，會傳回 `Import-Alias` 代表別名的 **system.management.automation.aliasinfo** 物件。
否則，此 Cmdlet 不會產生任何輸出。

## 注意

## 相關連結

[Export-Alias](Export-Alias.md)

[Get-Alias](Get-Alias.md)

[New-Alias](New-Alias.md)

[Set-Alias](Set-Alias.md)
