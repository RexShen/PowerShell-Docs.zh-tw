---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/invoke-item?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Item
ms.openlocfilehash: 6aac74b9b084996377b97997ab78972cb28b0959
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203979"
---
# Invoke-Item

## 概要
在指定項目上執行預設動作。

## SYNTAX

### 路徑 (預設值)

```
Invoke-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### LiteralPath

```
Invoke-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

## DESCRIPTION

此 `Invoke-Item` Cmdlet 會在指定的專案上執行預設動作。
例如，它會執行可執行檔或在與文件檔案類型相關聯的應用程式中開啟文件檔案。
預設動作取決於專案的類型，而且是由提供資料存取權的 PowerShell 提供者所決定。

## 範例

### 範例1：開啟檔案

此命令會在 Microsoft Office Word 中開啟 "aliasApr04.doc" 檔案。
在此情況下，在 Word 中開啟是 ".doc" 檔案的預設動作。

```powershell
Invoke-Item "C:\Test\aliasApr04.doc"
```

### 範例2：開啟特定類型的所有檔案

此命令會開啟 [C:\documents and 和 Settings\lister\my documents Documents] 資料夾中的所有 Microsoft Office Excel 試算表。
每一個試算表都會在一個新的 Excel 執行個體中開啟。
在此情況下，在 Excel 中開啟是 ".xls" 檔案的預設動作。

```powershell
Invoke-Item "C:\Documents and Settings\Lister\My Documents\*.xls"
```

## PARAMETERS

### -Credential

指定具有執行此動作權限的使用者帳戶。
預設為目前使用者。

輸入使用者名稱，例如 "User01" 或 "Domain01\User01"，或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。
若您輸入使用者名稱時，會提示您輸入密碼。

> [!WARNING]
> 與 Windows PowerShell 一起安裝的任何提供者皆不支援此參數。

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

### -Exclude

以字串陣列指定此 Cmdlet 在作業中排除的項目。
此參數的值會限定 **Path** 參數。
輸入路徑元素或模式，例如 "*.txt"。
允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Filter

以提供者的格式或語言指定篩選。
此參數的值會限定 **Path** 參數。

篩選的語法 (包括是否使用萬用字元) 取決於提供者。
篩選比其他參數更有效率，因為提供者會在 Cmdlet 取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Include

以字串陣列指定此 Cmdlet 在作業中納入的項目。
此參數的值會限定 **Path** 參數。
輸入路徑元素或模式，例如 "*.txt"。
允許使用萬用字元。

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

### -LiteralPath

指定項目的路徑。
與 **Path** 參數不同， **LiteralPath** 的值將完全依照其輸入值來使用。
沒有字元會被視為萬用字元。
如果路徑包含逸出字元，請將它括在單引號中。
單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

指定選取項目的路徑。

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -UseTransaction

將命令加入使用中交易。
只有交易為處理中狀態時，此參數才有效。
如需詳細資訊，請參閱 about_transactions。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
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

這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### System.String

您可以使用管線將包含路徑的字串傳送至此 Cmdlet。

## 輸出

### 無

命令不會產生任何輸出。
但它叫用的項目可能會產生輸出。

## 注意

此 Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。 若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。 如需詳細資訊，請參閱 about_Providers。

## 相關連結

[Clear-Item](Clear-Item.md)

[Copy-Item](Copy-Item.md)

[Get-Item](Get-Item.md)

[Move-Item](Move-Item.md)

[New-Item](New-Item.md)

[Remove-Item](Remove-Item.md)

[Rename-Item](Rename-Item.md)

[Set-Item](Set-Item.md)
