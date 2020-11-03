---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/join-path?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Join-Path
ms.openlocfilehash: 4189201cd373d29e8ea8e88441376e0df902742e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202091"
---
# Join-Path

## 概要
將路徑和子路徑結合成單一路徑。

## SYNTAX

```
Join-Path [-Path] <String[]> [-ChildPath] <String> [[-AdditionalChildPath] <String[]>] [-Resolve]
 [-Credential <PSCredential>] [<CommonParameters>]
```

## DESCRIPTION

此 `Join-Path` Cmdlet 會將路徑和子路徑結合成單一路徑。
提供者會提供路徑分隔符號。

## 範例

### 範例1：將路徑與子路徑結合

```powershell
PS C:\> Join-Path -Path "path" -ChildPath "childpath"
```

```output
path\childpath
```

此命令會使用 `Join-Path` 將路徑與 childpath 結合。

因為命令是從 `FileSystem` 提供者執行，所以它會提供 `\` 分隔符號來加入路徑。

### 範例2：合併已包含目錄分隔符號的路徑

```powershell
PS C:\> Join-Path -Path "path\" -ChildPath "\childpath"
```

```output
path\childpath
```

現有的目錄分隔符號 `\` 和處理，因此和之間只有一個分隔符號 `Path``ChildPath`

### 範例3：聯結路徑與子路徑以顯示檔案和資料夾

```powershell
Join-Path "C:\win*" "System*" -Resolve
```

此命令會顯示藉由聯結 C:\Win \* 路徑和系統子路徑所參考的檔案和資料夾 \* 。
它會顯示與相同的檔案和資料夾 `Get-ChildItem` ，但它會顯示每個專案的完整路徑。
在這個命令中， `Path` `ChildPath` 會省略和選擇性參數名稱。

### 範例4：搭配 PowerShell 登錄提供者使用 Join-Path

```powershell
PS HKLM:\> Join-Path -Path System -ChildPath *ControlSet* -Resolve
```

```output
HKLM:\System\ControlSet001
HKLM:\System\CurrentControlSet
```

此命令會顯示登錄子機碼中包含的登錄機碼 `HKLM\System` `ControlSet` 。

`Resolve`參數，會嘗試解析聯結的路徑，包括來自目前提供者路徑的萬用字元`HKLM:\`

### 範例5：結合多個路徑根目錄與子路徑

```powershell
Join-Path -Path C:, D:, E:, F: -ChildPath New
```

```output
C:\New
D:\New
E:\New
F:\New
```

此命令會使用 `Join-Path` 將多個路徑根目錄與子路徑結合。

> [!NOTE]
> 指定的磁片磁碟機 `Path` 必須存在，否則該專案的聯結將會失敗。

### 範例6：將檔案系統磁片磁碟機的根目錄與子路徑結合

```powershell
Get-PSDrive -PSProvider filesystem | ForEach-Object {$_.root} | Join-Path -ChildPath "Subdir"
```

```output
C:\Subdir
D:\Subdir
```

此命令會將主控台中每個 PowerShell 檔案系統磁片磁碟機的根目錄與 Subdir 子路徑結合。

此命令會使用 `Get-PSDrive` Cmdlet 來取得 FileSystem 提供者所支援的 PowerShell 磁片磁碟機。
`ForEach-Object`語句只會選取物件的根屬性 `PSDriveInfo` ，並將它與指定的子路徑結合。

輸出顯示電腦上的 PowerShell 磁片磁碟機包含對應至 C:\Program Files 目錄的磁片磁碟機。

### 範例7：結合不定數目的路徑

```powershell
Join-Path a b c d e f g
```

```Output
a\b\c\d\e\f\g
```

`AdditionalChildPath`參數允許聯結不限數目的路徑。

在此範例中，不會使用任何參數名稱，因此 "a" 會系結至 `Path` ，"b" 至 " `ChildPath` c-g" 至 `AdditionalChildPath`

## PARAMETERS

### -AdditionalChildPath

指定要附加至 *Path* 參數值的其他元素。 `ChildPath`參數仍然是強制性的，也必須指定。

這個參數是以屬性（property）指定，該 `ValueFromRemainingArguments` 屬性可讓您聯結不定數目的路徑。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ChildPath

指定要附加至參數值的元素 `Path` 。
允許使用萬用字元。
`ChildPath`參數是必要參數，雖然參數名稱 ( "ChildPath" ) 是選擇性的。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

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
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

指定附加子路徑的主要路徑。
允許使用萬用字元。

的值會 `Path` 決定要加入路徑的提供者，並新增路徑分隔符號。
`Path`參數是必要參數，雖然參數名稱 ( "Path" ) 是選擇性的。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSPath

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Resolve

指出此 Cmdlet 應該嘗試解析來自目前提供者的聯結路徑。

- 如果使用萬用字元，則 Cmdlet 會傳回所有符合聯結路徑的路徑。
- 如果 **未** 使用萬用字元，則如果路徑不存在，Cmdlet 將會發生錯誤。

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

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

您可以使用管線將包含路徑的字串傳送至此 Cmdlet。

## 輸出

### System.String

這個 Cmdlet 會傳回包含產生之路徑的字串。

## 注意

包含路徑名詞 (Path Cmdlet 的 Cmdlet 會) 操作路徑名稱，並傳回所有 PowerShell 提供者都能解讀的精簡格式名稱。 它們是設計用於程式與指令碼，您可以在其中以特定格式顯示所有或部分路徑名稱。 使用方式與使用 Dirname、Normpath、Realpath、Join 或其他路徑操作工具的方式相同。

您可以搭配多個提供者使用 path Cmdlet，包括 `FileSystem` 、 `Registry` 和 `Certificate` 提供者。

此 Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。
若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。
如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 相關連結

[Convert-Path](Convert-Path.md)

[Resolve-Path](Resolve-Path.md)

[Split-Path](Split-Path.md)

[Test-Path](Test-Path.md)

[Get-PSProvider](Get-PSProvider.md)

[Get-ChildItem](Get-ChildItem.md)

[Get-PSDrive](Get-PSDrive.md)

