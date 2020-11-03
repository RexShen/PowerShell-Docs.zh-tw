---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 2/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-alias?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Alias
ms.openlocfilehash: 86eff41bc9784627db82689108d01cbd71840e77
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201248"
---
# Set-Alias

## 概要
在目前的 PowerShell 會話中，建立或變更 Cmdlet 或其他命令的別名。

## SYNTAX

### Default (預設值)

```
Set-Alias [-Name] <string> [-Value] <string> [-Description <string>] [-Option <ScopedItemOptions>]
 [-PassThru] [-Scope <string>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

此 `Set-Alias` Cmdlet 會建立或變更 Cmdlet 或命令的別名，例如函式、腳本、檔案或其他可執行檔。 別名是參考 Cmdlet 或命令的替代名稱。
例如， `sal` 是 Cmdlet 的別名 `Set-Alias` 。 如需詳細資訊，請參閱 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。

Cmdlet 可以有多個別名，但別名只能與一個 Cmdlet 相關聯。 您可以使用 `Set-Alias` 將現有的別名重新指派給另一個 Cmdlet，或變更別名的屬性，例如描述。

所建立或變更的別名 `Set-Alias` 不是永久性的，而且只能在目前的 PowerShell 會話期間使用。 當 PowerShell 會話關閉時，就會移除別名。

## 範例

### 範例 1︰建立 Cmdlet 的別名

此命令會在目前的 PowerShell 會話中建立 Cmdlet 的別名。

```
PS> Set-Alias -Name list -Value Get-ChildItem

PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-ChildItem
```

`Set-Alias`Cmdlet 會在目前的 PowerShell 會話中建立別名。 **Name** 參數會指定別名的名稱 `list` 。 **Value** 參數會指定別名執行的 Cmdlet。

若要執行別名，請 `list` 在 PowerShell 命令列上輸入。

### 範例2：將現有的別名重新指派給不同的 Cmdlet

此命令會重新指派現有的別名，以執行不同的 Cmdlet。

```
PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-ChildItem

PS> Set-Alias -Name list -Value Get-Location

PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-Location
```

此 `Get-Alias` Cmdlet 會使用 **Name** 參數來顯示 `list` 別名。 `list`別名與 Cmdlet 相關聯 `Get-ChildItem` 。 當 `list` 別名執行時，會顯示目前目錄中的專案。

此 `Set-Alias` Cmdlet 會使用 **Name** 參數來指定 `list` 別名。 **Value** 參數會將別名與 Cmdlet 產生關聯 `Get-Location` 。

此 `Get-Alias` Cmdlet 會使用 **Name** 參數來顯示 `list` 別名。 `list`別名與 Cmdlet 相關聯 `Get-Location` 。 當 `list` 別名執行時，會顯示目前的目錄的位置。

### 範例3：建立和變更唯讀別名

此命令會建立唯讀別名。 唯讀選項可防止非預期的別名變更。 若要變更或刪除唯讀別名，請使用 **Force** 參數。

```
PS> Set-Alias -Name loc -Value Get-Location -Option ReadOnly -PassThru | Format-List -Property *

DisplayName         : loc -> Get-Location
Definition          : Get-Location
Options             : ReadOnly
Description         :
Name                : loc
CommandType         : Alias

PS> Set-Alias -Name loc -Value Get-Location -Option ReadOnly -Description 'Displays the current directory' -Force -PassThru | Format-List -Property *

DisplayName         : loc -> Get-Location
Definition          : Get-Location
Options             : ReadOnly
Description         : Displays the current directory
Name                : loc
CommandType         : Alias
```

`Set-Alias`Cmdlet 會在目前的 PowerShell 會話中建立別名。 **Name** 參數會指定別名的名稱 `loc` 。 **Value** 參數 `Get-Location` 會指定別名執行的 Cmdlet。 **Option** 參數會指定 **ReadOnly** 值。 **PassThru** 參數代表別名物件，並將物件沿著管線向下傳送至 `Format-List` Cmdlet。 `Format-List` 使用 **Property** 參數搭配星號 (`*`) ，以便顯示所有屬性。 範例輸出會顯示這些屬性的部分清單。

`loc`別名的變更會加上兩個參數。 **描述** 會新增文字來說明別名的用途。 需要 **Force** 參數，因為 `loc` 別名為唯讀。 如果未使用 **Force** 參數，變更就會失敗。

### 範例4：建立可執行檔的別名

這個範例會建立本機電腦上可執行檔的別名。

```
PS> Set-Alias -Name np -Value C:\Windows\notepad.exe

PS> Get-Alias -Name np

CommandType     Name
-----------     ----
Alias           np -> notepad.exe
```

`Set-Alias`Cmdlet 會在目前的 PowerShell 會話中建立別名。 **Name** 參數會指定別名的名稱 `np` 。 **Value** 參數會指定 **C:\Windows\notepad.exe** 的路徑和應用程式名稱。 此 `Get-Alias` Cmdlet 會使用 **Name** 參數來顯示 `np` 別名與 **notepad.exe** 相關聯。

若要執行別名，請 `np` 在 PowerShell 命令列上輸入，以開啟 **notepad.exe** 。

### 範例5：使用參數建立命令的別名

此範例示範如何使用參數將別名指派給命令。

您可以為 Cmdlet 建立別名，例如 `Set-Location` 。 您無法為具有參數和值的命令建立別名，例如 `Set-Location -Path C:\Windows\System32` 。 若要為命令建立別名，請建立一個包含該命令的函式，然後建立該函式的別名。 如需詳細資訊，請參閱 [about_Functions](../Microsoft.PowerShell.Core/about/about_Functions.md)。

```
PS> Function CD32 {Set-Location -Path C:\Windows\System32}

PS> Set-Alias -Name Go -Value CD32
```

即會建立名為的函式 `CD32` 。 此函式會使用 `Set-Location` Cmdlet 搭配 **Path** 參數來指定目錄 **C:\Windows\System32** 。

`Set-Alias`Cmdlet 會在目前的 PowerShell 會話中建立函式的別名。 **Name** 參數會指定別名的名稱 `Go` 。 **Value** 參數會指定函數的名稱 `CD32` 。

若要執行別名，請 `Go` 在 PowerShell 命令列上輸入。 `CD32`函數會執行並變更目錄 **C:\Windows\System32** 。

## PARAMETERS

### -Description

指定別名的描述。 您可以輸入任何字串。 如果描述包含空格，請將它括在單引號中。

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

使用 **Force** 參數來變更或刪除將 **Option** 參數設定為 **ReadOnly** 的別名。

**Force** 參數無法變更或刪除將 **Option** 參數設為 **常數** 的別名。

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

### -Name

指定新別名的名稱。 別名名稱可包含英數位元和連字號。 別名名稱不可以是數值，例如123。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Option

設定別名的 **Option** 屬性值。 **ReadOnly** 和 **常數** 等值會保護別名免于非預期的變更。 若要查看會話中所有別名的 **Option** 屬性，請輸入 `Get-Alias | Format-Table -Property Name, Options -Autosize` 。

此參數可接受的值如下：

- **AllScope** 別名會複製到所建立的任何新範圍。
- **常數** 無法變更或刪除。
- **無** 不設定任何選項，而且是預設值。
- **私** 用別名只能在目前的範圍中使用。
- **ReadOnly** 除非使用 **Force** 參數，否則無法變更或刪除。
- **未指定**

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: AllScope, Constant, None, Private, ReadOnly, Unspecified

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

傳回代表別名的物件。 使用格式 Cmdlet （例如） `Format-List` 來顯示物件。 依預設，不 `Set-Alias` 會產生任何輸出。

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

### -Scope

指定別名的有效範圍。 預設值為 [ **本機** ]。 如需詳細資訊，請參閱 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)。

可接受的值如下：

- 全球
- 本機
- 私人
- 編號的範圍
- 指令碼

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Global, Local, Private, Numbered scopes, Script

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### -Value

指定別名所執行 Cmdlet 或命令的名稱。 **值** 參數是別名的 **定義** 屬性。

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

### 無

`Set-Alias` 不接受來自管線的輸入。

## 輸出

### 無或 System.Management.Automation.AliasInfo

當您使用 **PassThru** 參數時，會 `Set-Alias` 產生代表別名的 **system.management.automation.aliasinfo** 物件。 否則，不 `Set-Alias` 會產生任何輸出。

## 注意

PowerShell 包含可在每個 PowerShell 會話中使用的內建別名。 此 `Get-Alias` Cmdlet 會顯示 PowerShell 會話中可用的別名。

若要建立別名，請使用 Cmdlet `Set-Alias` 或 `New-Alias` 。 在 PowerShell 6 中，若要刪除別名，請使用 `Remove-Alias` Cmdlet。 `Remove-Item` 是針對回溯相容性所接受，例如，針對使用舊版 PowerShell 所建立的腳本。 使用像這樣的命令 `Remove-Item -Path Alias:aliasname` 。

若要建立可在每個 PowerShell 會話中使用的別名，請將它新增至您的 PowerShell 設定檔。
如需詳細資訊，請參閱 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)。

您可以執行匯出和匯入，將別名儲存並重複使用於另一個 PowerShell 會話。 若要將別名儲存至檔案，請使用 `Export-Alias` 。 若要將儲存的別名新增至新的 PowerShell 會話，請使用 `Import-Alias` 。

## 相關連結

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[about_Functions](../Microsoft.PowerShell.Core/about/about_Functions.md)

[about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)

[about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)

[Export-Alias](Export-Alias.md)

[Get-Alias](Get-Alias.md)

[Import-Alias](Import-Alias.md)

[New-Alias](New-Alias.md)

[Remove-Alias](Remove-Alias.md)

[Remove-Item](../Microsoft.PowerShell.Management/Remove-Item.md)
