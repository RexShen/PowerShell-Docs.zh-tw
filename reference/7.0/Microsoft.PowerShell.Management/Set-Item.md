---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-item?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Item
ms.openlocfilehash: 4485b1a140b1496ee80d81d1526b3d76e446fd34
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201743"
---
# Set-Item

## 概要
將項目的值變更為命令中指定的值。

## SYNTAX

### 路徑 (預設值)

```
Set-Item [-Path] <String[]> [[-Value] <Object>] [-Force] [-PassThru] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPath

```
Set-Item -LiteralPath <String[]> [[-Value] <Object>] [-Force] [-PassThru] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

Cmdlet 會將 `Set-Item` 專案（例如變數或登錄機碼）的值變更為命令中指定的值。

## 範例

### 範例1：建立別名

此命令會為「記事本」建立 np 的別名。

```powershell
Set-Item -Path alias:np -Value "c:\windows\notepad.exe"
```

### 範例2：變更環境變數的值

此命令會將 UserRole 環境變數的值變更為 Administrator。

```powershell
Set-Item -Path env:UserRole -Value "Administrator"
```

### 範例3：修改提示字元函式

此命令會變更提示字元函式，讓它顯示路徑之前的時間。

```powershell
Set-Item -Path function:prompt -Value {'PS '+ (Get-Date -Format t) + " " + (Get-Location) + '> '}
```

### 範例4：設定 prompt 函數的選項

此命令會設定 prompt 函式的 **AllScope** 和 **ReadOnly** 選項。
此命令會使用 **Options** 的動態參數選項 `Set-Item` 。
**Options** `Set-Item` 只有當您將 Options 參數與 **Alias** 或 **Function** 提供者搭配使用時，才能使用這些選項。

```powershell
Set-Item -Path function:prompt -Options "AllScope,ReadOnly"
```

## PARAMETERS

### -Credential

> [!NOTE]
> 使用 PowerShell 安裝的任何提供者都不支援此參數。
> 若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。

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

以字串陣列指定此 Cmdlet 在作業中排除的專案。 此參數的值會限定 **Path** 參數。 輸入路徑元素或模式，例如 `*.txt`。 允許使用萬用字元。 只有當命令包含專案的內容（例如）時，才會使用 **Exclude** 參數， `C:\Windows\*` 其中的萬用字元會指定目錄的內容 `C:\Windows` 。

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

指定要限定 **路徑** 參數的篩選準則。 [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供者是唯一支援使用篩選器的已安裝 PowerShell 提供者。 您可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **檔案系統** 篩選器語言的語法。
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

### -Force

強制 Cmdlet 設定無法以其他方式變更的專案，例如唯讀別名或變數。 此 Cmdlet 無法變更常數別名或變數。
實作會依提供者而異。
如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。
即使使用 *Force* 參數，Cmdlet 也無法覆寫安全性限制。

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

### -Include

以字串陣列指定此 Cmdlet 在作業中納入的項目。 此參數的值會限定 **Path** 參數。 輸入路徑元素或模式，例如 `"*.txt"`。 允許使用萬用字元。 **Include** 參數只有當命令包含專案內容時才有效，例如 `C:\Windows\*` ，其中的萬用字元會指定目錄的內容 `C:\Windows` 。

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

### -LiteralPath

指定一個或多個位置的路徑。 **LiteralPath** 的值將完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含逸出字元，請將它括在單引號中。 單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

將代表專案的物件傳遞至管線。
根據預設，此 Cmdlet 不會產生任何輸出。

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

指定專案位置的路徑。
允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Value

指定項目的新值。

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
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

這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### System.Object

您可以使用管線將代表專案新值的物件傳送至此 Cmdlet。

## 輸出

### 無或是表示新項目或變更項目的物件。

如果您指定 *PassThru* 參數，此 Cmdlet 會產生代表專案的物件。
否則，此 Cmdlet 不會產生任何輸出。

## 注意

- `Set-Item` PowerShell FileSystem 提供者不支援。 若要變更檔案系統中專案的值，請使用 `Set-Content` Cmdlet。
- 在登錄磁片磁碟機 `HKLM:` 和中 `HKCU:` ，會 `Set-Item` 變更登錄機碼 (預設) 值中的資料。
  - 若要建立和變更登錄機碼的名稱，請使用 `New-Item` 和 `Rename-Item` Cmdlet。
  - 若要變更登錄值中的名稱和資料，請使用 `New-ItemProperty` 、 `Set-ItemProperty` 和 `Rename-ItemProperty` Cmdlet。
- `Set-Item` 的設計目的是要與任何提供者公開的資料搭配使用。
  若要列出工作階段中可用的提供者，請輸入 `Get-PsProvider`。
  如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 相關連結

[Clear-Item](Clear-Item.md)

[Copy-Item](Copy-Item.md)

[Get-Item](Get-Item.md)

[Invoke-Item](Invoke-Item.md)

[Move-Item](Move-Item.md)

[New-Item](New-Item.md)

[Remove-Item](Remove-Item.md)

[Rename-Item](Rename-Item.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
