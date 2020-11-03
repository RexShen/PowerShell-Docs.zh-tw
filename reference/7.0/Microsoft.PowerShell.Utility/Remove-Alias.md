---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/24/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-alias?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Alias
ms.openlocfilehash: 6f98a910e43b87793ac4f2af8ffb069d3e5d47ba
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201431"
---
# Remove-Alias

## 概要
移除目前會話中的別名。

## SYNTAX

### Default (預設值)

```
Remove-Alias [-Name] <String[]> [-Scope <String>] [-Force] [<CommonParameters>]
```

## DESCRIPTION

`Remove-Alias`Cmdlet 會從目前的 PowerShell 會話中移除別名。 若要移除 **選項** 屬性設為 **ReadOnly** 的別名，請使用 **Force** 參數。

`Remove-Alias`Cmdlet 是在 PowerShell 6.0 中引進。

## 範例

### 範例 1-移除別名

此範例會移除名為 `del` 的別名，表示 `Remove-Item` Cmdlet。

```powershell
Remove-Alias -Name del
```

### 範例 2-移除所有的非常數別名

此範例會移除目前 PowerShell 會話中的所有別名，但 **選項** 屬性設為 **常數** 的別名除外。 執行命令之後，別名可在其他 PowerShell 會話或新的 PowerShell 會話中使用。

```powershell
Get-Alias | Where-Object { $_.Options -NE "Constant" } | Remove-Alias -Force
```

`Get-Alias` 取得 PowerShell 會話中的所有別名，並將物件沿著管線向下傳送。
`Where-Object` 使用腳本區塊，而自動變數 (`$_`) 和 **Options** 屬性代表目前的管線物件。 參數 **NE** (不等於) ，會選取沒有設定為 **常數** 之 **選項** 值的物件。 `Remove-Alias` 使用 **Force** 參數從 PowerShell 會話移除別名，包括唯讀別名。

## PARAMETERS

### -Force

指出此 Cmdlet 會移除別名，包括 **選項** 屬性設為 **ReadOnly** 的別名。 **Force** 參數無法移除 **選項** 屬性設為 **常數** 的別名。

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

指定要移除之別名的名稱。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Scope

只會影響指定範圍內的別名。 預設範圍為 [ **本機** ]。 如需詳細資訊，請參閱 [about_Scopes](../microsoft.powershell.core/about/about_scopes.md)。

此參數可接受的值為：

- 全球
- 本機
- 指令碼
- 相對於目前範圍的數字 (0 至範圍數目，0 為目前範圍，1 為其父系)。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String[]

您可以使用管線將別名物件傳送至 **移除別名** 。

## 輸出

### 無

此 Cmdlet 不會傳回任何輸出。

## 注意

變更只會影響目前的範圍。 若要從所有會話中移除別名，請將 **移除別名** 命令新增至您的 PowerShell 設定檔。

如需詳細資訊，請參閱 [about_Aliases](../microsoft.powershell.core/about/about_aliases.md)。

## 相關連結

[about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[Export-Alias](Export-Alias.md)

[Get-Alias](Get-Alias.md)

[Import-Alias](Import-Alias.md)

[New-Alias](New-Alias.md)

[Set-Alias](Set-Alias.md)

[Where-Object](../Microsoft.PowerShell.Core/Where-Object.md)
