---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-alias?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Alias
ms.openlocfilehash: 00ef887dc79e35a6dff299a37bfafa57aebc77db
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203199"
---
# New-Alias

## 概要
建立新的別名。

## SYNTAX

```
New-Alias [-Name] <String> [-Value] <String> [-Description <String>] [-Option <ScopedItemOptions>] [-PassThru]
 [-Scope <String>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
**New-Alias** Cmdlet 會在目前的 Windows PowerShell 工作階段中建立新的別名。
在您結束工作階段或是關閉 Windows PowerShell 之後，不會儲存使用 **New-Alias** 建立的別名。
您可以使用 Export-Alias Cmdlet 將別名資訊儲存到檔案。
您之後可以使用 **Import-Alias** 來抓取儲存的別名資訊。

## 範例

### 範例 1︰建立 Cmdlet 的別名

```
PS C:\> New-Alias -Name "List" Get-ChildItem
```

此命令會建立名為 List 的別名，以代表 Get-ChildItem Cmdlet。

### 範例 2︰建立 Cmdlet 的唯讀別名

```
PS C:\> New-Alias -Name "W" -Value Get-WmiObject -Description "quick wmi alias" -Option ReadOnly
PS C:\> Get-Alias -Name "W" | Format-List *
```

此命令會建立名為 W 的別名，以代表 Get-WmiObject Cmdlet。
它會為別名建立描述 quick wmi alias，並使其變成唯讀。
命令的最後一行使用 Get-Alias 取得新的別名，並使用管線將它傳送至 Format-List 以顯示其所有的相關資訊。

## PARAMETERS

### -Description
指定別名的描述。
您可以輸入任何字串。
如果描述包含空格，請將它括在引號中。

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
指出如果所命名的別名已經存在，此 Cmdlet 的運作方式就和 Set-Alias 一樣。

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

### -Name
指定新的別名。
您可以在別名中使用任何英數字元，但是第一個字元不能是數字。

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
指定別名的 **Options** 屬性值。
有效值為：

- 無：別名沒有 (預設值的條件約束) 
- ReadOnly：可以刪除別名，但除非使用 **Force** 參數，否則無法變更
- 常數：無法刪除或變更別名
- 私用：別名只能在目前的範圍中使用
- AllScope：別名會複製到所建立的任何新範圍
- 未指定：未指定選項

若要查看會話中所有別名的 **Options** 屬性，請輸入 `Get-Alias | Format-Table -Property Name, Options -AutoSize` 。

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, ReadOnly, Constant, Private, AllScope, Unspecified

Required: False
Position: Named
Default value: [System.Management.Automation.ScopedItemOptions]::None
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

### -Scope
指定新別名的範圍。
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

### -Value
指定 Cmdlet 名稱或已有別名的命令元素。

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

### 無
您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### 無或 System.Management.Automation.AliasInfo
使用 *Passthru* 參數時， **New-Alias** 會產生代表新別名的 **System.Management.Automation.AliasInfo** 物件。
否則，此 Cmdlet 不會產生任何輸出。

## 注意

* 若要建立新的別名，請使用 Set-Alias 或 New-Alias。 若要變更別名，請使用 **Set-Alias** 。 若要刪除別名，請使用 Remove-Item。

*

## 相關連結

[Export-Alias](Export-Alias.md)

[Get-Alias](Get-Alias.md)

[Import-Alias](Import-Alias.md)

[Set-Alias](Set-Alias.md)
