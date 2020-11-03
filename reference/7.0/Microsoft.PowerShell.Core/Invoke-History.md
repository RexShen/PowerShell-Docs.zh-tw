---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-history?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-History
ms.openlocfilehash: baedf2be8bb3fca2223c65c33beb21f01ed84969
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201923"
---
# Invoke-History

## 概要
從工作階段歷程記錄執行命令。

## SYNTAX

```
Invoke-History [[-Id] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

此 `Invoke-History` Cmdlet 會從會話歷程記錄執行命令。 您可以將代表命令的物件傳遞給 Get-History `Invoke-History` ，或者您可以使用 **識別碼** 號碼來識別目前歷程記錄中的命令。 若要尋找命令的識別碼，請使用 `Get-History` Cmdlet。

會話歷程記錄是與 **PSReadLine** 模組所維護的歷程記錄分開管理。
這兩個歷程記錄都可以在載入 **PSReadLine** 的會話中使用。 此 Cmdlet 僅適用于會話歷程記錄。 如需詳細資訊，請參閱 [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)。

## 範例

### 範例1：在歷程記錄中執行最新的命令

此範例會執行會話歷程記錄中的最後一個或最新的命令。 您可以將此命令縮寫為 `r` 的別名 `Invoke-History` 。

```powershell
Invoke-History
```

### 範例2：執行具有指定識別碼的命令

此範例會在 **識別碼** 為132的會話歷程記錄中執行命令。 因為 **Id** 參數的名稱是選擇性的，所以您可以將此命令縮寫為下列內容： `Invoke-History 132` 、 `ihy 132` 或 `r 132` 。

```powershell
Invoke-History -Id 132
```

### 範例3：使用命令文字執行最新的命令

此範例會在會話歷程記錄中執行最新的 `Get-Process` 命令。 當您輸入 **Id** 參數的字元時， `Invoke-History` 會執行它所找到的第一個符合模式的命令，從最新的命令開始。

```powershell
Invoke-History -Id get-pr
```

> [!NOTE]
> 模式比對不區分大小寫，但模式符合該行的開頭。

### 範例4：從歷程記錄執行一連串的命令

此範例會執行命令16到24。 因為您只能列出一個 **識別碼** 值，所以命令會使用 `ForEach-Object` Cmdlet 來 `Invoke-History` 針對每個 **識別碼** 值執行一次命令。

```powershell
16..24 | ForEach {Invoke-History -Id $_ }
```

### 範例 5

此範例會在記錄中執行以命令 255 (249 到 255) 結尾的七個命令。 它會使用 `Get-History` Cmdlet 來取得命令。 因為您只能列出一個 **識別碼** 值，所以命令會使用 `ForEach-Object` Cmdlet `Invoke-History` 針對每個 **識別碼** 值執行一次命令。

```powershell
Get-History -Id 255 -Count 7 | ForEach {Invoke-History -Id $_.Id}
```

## PARAMETERS

### -Id

指定記錄中命令的 **識別碼** 。 您可以輸入命令的 **識別碼** 或命令的前幾個字元。

如果您輸入字元，則會 `Invoke-History` 先符合最新的命令。 如果您省略此參數，則會 `Invoke-History` 執行最後一個或最新的命令。 若要尋找命令的 **識別碼** ，請使用 `Get-History` Cmdlet。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
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

### System.String

您可以使用管線將歷程記錄 **識別碼** 傳送至此 Cmdlet。

## 輸出

### 無

此 Cmdlet 不會產生任何輸出，但輸出可能是由執行的命令所產生 `Invoke-History` 。

## 注意

工作階段歷程記錄是工作階段期間輸入的命令清單。 工作階段歷程記錄代表命令的執行順序、狀態及開始和結束時間。 當您輸入每個命令時，PowerShell 會將它新增至歷程記錄，以便您可以重複使用。 如需會話歷程記錄的詳細資訊，請參閱 [about_History](About/about_History.md)。

您也可以 `Invoke-History` 使用內建的別名和來參考 `r` `ihy` 。 如需詳細資訊，請參閱 [about_Aliases](About/about_Aliases.md)。

## 相關連結

[Add-History](Add-History.md)

[Clear-History](Clear-History.md)

[Get-History](Get-History.md)
