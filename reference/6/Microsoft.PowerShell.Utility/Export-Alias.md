---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-alias?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Alias
ms.openlocfilehash: 5a732573a24da5de2a00bfd29abb3711218c64e3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204664"
---
# Export-Alias

## 概要
將目前已定義別名的相關資訊匯出至檔案。

## SYNTAX

### ByPath (預設值)

```
Export-Alias [-Path] <String> [[-Name] <String[]>] [-PassThru] [-As <ExportAliasFormat>] [-Append] [-Force]
 [-NoClobber] [-Description <String>] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Export-Alias -LiteralPath <String> [[-Name] <String[]>] [-PassThru] [-As <ExportAliasFormat>] [-Append]
 [-Force] [-NoClobber] [-Description <String>] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

Cmdlet 會將 `Export-Alias` 目前會話中的別名匯出至檔案。
如果輸出檔案不存在，此 Cmdlet 會建立它。

`Export-Alias` 可以匯出特定範圍或所有範圍中的別名，它可以產生 CSV 格式的資料，或是您可以新增至會話或 PowerShell 設定檔的一連串 Set-Alias 命令。

## 範例

### 範例1：匯出別名

```powershell
Export-Alias -Path "alias.csv"
```

此命令將目前的別名資訊匯出至目前目錄中名為 Alias.csv 的檔案。

### 範例2：匯出別名，除非匯出檔案已存在

```powershell
Export-Alias -Path "alias.csv" -NoClobber
```

此命令將目前工作階段中的別名匯出至 Alias.csv 檔案。

因為指定了 **NoClobber** 參數，所以如果目前的目錄中已經有 Alias.csv 檔案，命令將會失敗。

### 範例3：將別名附加至檔案

```powershell
Export-Alias -Path "alias.csv" -Append -Description "Appended Aliases" -Force
```

此命令將目前工作階段中的別名附加至 Alias.csv 檔案。

此命令會使用 **description** 參數將描述加入檔案頂端的批註。

此命令也會使用 **Force** 參數來覆寫任何現有的 Alias.csv 檔案，即使這些檔案具有唯讀屬性也一樣。

### 範例4：將別名匯出為腳本

```powershell
Export-Alias -Path "alias.ps1" -As Script
Add-Content -Path $Profile -Value (Get-Content alias.ps1)
$S = New-PSSession -ComputerName Server01
Invoke-Command -Session $S -FilePath .\alias.ps1
```

此範例顯示如何使用產生的腳本檔案格式 `Export-Alias` 。

第一個命令將工作階段中的別名匯出至 Alias.ps1 檔案。
它使用 **As** 參數搭配 Script 值來產生檔案，其中包含每個別名的 Set-Alias 命令。

第二個命令將 Alias.ps1 檔案中的別名加入 CurrentUser-CurrentHost 設定檔。
設定檔的路徑會儲存在變數中 `$Profile` 。
此命令會使用 `Get-Content` Cmdlet 來取得 Alias.ps1 檔案中的別名，並使用 `Add-Content` Cmdlet 將它們新增至設定檔。
如需詳細資訊，請參閱 about_Profiles。

第三個和第四個命令會將 Alias.ps1 檔案中的別名新增至 Server01 電腦上的遠端會話。
第三個命令會使用 `New-PSSession` Cmdlet 來建立會話。
第四個命令會使用 Cmdlet 的 **FilePath** 參數 `Invoke-Command` 在新的會話中執行 Alias.ps1 檔案。

## PARAMETERS

### -Append

指出此 Cmdlet 會將輸出附加至指定的檔案，而不是覆寫該檔案現有的內容。

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

### -As

指定輸出格式。
預設值為 CSV。
此參數可接受的值為：

- CSV。
以逗號分隔的值 (CSV) 格式。
- 指令碼：
`Set-Alias`針對每個匯出的別名建立命令。
如果您以 .ps1 副檔名命名輸出檔案，可以指令碼的方式執行它將別名加入任何工作階段。

```yaml
Type: Microsoft.PowerShell.Commands.ExportAliasFormat
Parameter Sets: (All)
Aliases:
Accepted values: Csv, Script

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Description

指定匯出檔案的描述。
描述會顯示在檔案頂端做為註解，後面接標頭資訊。

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

### -Force

強制執行命令而不要求使用者確認。

覆寫輸出檔案，即使檔案設定了唯讀屬性亦同。

預設 `Export-Alias` 會覆寫檔案而不發出警告，除非已設定唯讀或隱藏屬性，或在命令中使用 **NoClobber** 參數。
當命令中同時使用 **NoClobber** 參數時，它會優先于 **Force** 參數。

**Force** 參數不能強制 `Export-Alias` 以 hidden 屬性覆寫檔案。

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

指定輸出檔案的路徑。
與 **Path** 不同， **LiteralPath** 參數值將完全依照其輸入值來使用。
沒有字元會被視為萬用字元。
如果路徑包含逸出字元，請將它括在單引號中。
單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

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

### -Name

將名稱指定為要匯出之別名的陣列。
允許使用萬用字元。

根據預設，會 `Export-Alias` 匯出會話或範圍中的所有別名。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -NoClobber

指出此 Cmdlet 會防止 `Export-Alias` 覆寫任何檔案，即使在命令中使用 **Force** 參數也是如此。

如果省略 **NoClobber** 參數， `Export-Alias` 將會覆寫現有的檔案而不發出警告，除非已在檔案上設定唯讀屬性。
*NoClobber* 優先于 **Force** 參數，它允許 `Export-Alias` 以唯讀屬性覆寫檔案。

*NoClobber* 不會防止 **Append** 參數將內容加入現有的檔案。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
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

指定輸出檔案的路徑。
允許使用萬用字元，但是產生的路徑值必須解析成單一檔案名稱。

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Scope

指定要匯出別名的範圍。
此參數可接受的值為：

- 全球
- 本機
- 指令碼
- 相對於目前範圍的數位 (0 至範圍數目，0為目前範圍，1為其父系) 

預設值為 Local。
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

### 無。

您無法使用管線將物件傳送至此 Cmdlet。

## 輸出

### 無或 System.Management.Automation.AliasInfo

當您使用 **Passthru** 參數時，會傳回 `Export-Alias` 代表別名的 **system.management.automation.aliasinfo** 物件。
否則，此 Cmdlet 不會產生任何輸出。

## 注意

* 您只能匯出別名 (Export-Aliases) 至檔案。

## 相關連結

[Get-Alias](Get-Alias.md)

[Import-Alias](Import-Alias.md)

[New-Alias](New-Alias.md)

[Set-Alias](Set-Alias.md)
