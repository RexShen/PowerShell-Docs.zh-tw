---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/remove-psreadlinekeyhandler?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSReadLineKeyHandler
ms.openlocfilehash: 6a15e829f589fbccf0da3479a22f24cdf3fc81ae
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203736"
---
# Remove-PSReadLineKeyHandler

## 概要
移除索引鍵系結。

## SYNTAX

```
Remove-PSReadLineKeyHandler [-Chord] <String[]> [-ViMode <ViMode>] [<CommonParameters>]
```

## DESCRIPTION

`Remove-PSReadLineKeyHandler`Cmdlet 會移除指定的金鑰系結。

## 範例

### 範例1：移除系結

```powershell
Remove-PSReadLineKeyHandler -Chord Ctrl+B
```

此命令會從按鍵組合（或弦）移除系結 `Ctrl+B` 。 在 `Ctrl+B` 本文中會建立弦 `Set-PSReadLineKeyHandler` 。

## PARAMETERS

### -弦

指定要移除之索引鍵或索引鍵序列的陣列。 單一系結是使用單一字串來指定。 如果系結是索引鍵的序列，請以逗號分隔索引鍵，如下列範例所示：

`Ctrl+x,Ctrl+l`

此參數接受字串陣列。 每個字串都是個別的系結，而不是單一系結的索引鍵序列。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Key

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ViMode

指定要套用系結的 vi 模式。 可能的值為： Insert、Command。

```yaml
Type: Microsoft.PowerShell.ViMode
Parameter Sets: (All)
Aliases:
Accepted values: Insert, Command

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

您無法使用管線將物件傳送至此 Cmdlet。

## 輸出

### 無

## 注意

## 相關連結

[PSReadLineKeyHandler](Get-PSReadLineKeyHandler.md)

[PSReadLineOption](Get-PSReadLineOption.md)

[設定-PSReadLineOption](Set-PSReadLineOption.md)

[設定-PSReadLineKeyHandler](Set-PSReadLineKeyHandler.md)
