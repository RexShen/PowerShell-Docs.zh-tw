---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-alias?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Alias
ms.openlocfilehash: cf936b63063b3381c4aac54e246ec921b61c3b22
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203299"
---
# Get-Alias

## 概要

取得目前工作階段的別名。

## SYNTAX

### Default (預設值)

```
Get-Alias [[-Name] <String[]>] [-Exclude <String[]>] [-Scope <String>]
 [<CommonParameters>]
```

### 定義

```
Get-Alias [-Exclude <String[]>] [-Scope <String>] [-Definition <String[]>]
 [<CommonParameters>]
```

## DESCRIPTION

**取得別名** Cmdlet 會取得目前會話中的別名。
這包括內建的別名、您已設定或匯入的別名，以及您已新增至 PowerShell 設定檔的別名。

根據預設， **Get 別名** 會使用別名並傳回命令名稱。
當您使用 *定義* 參數時， **Get 別名** 會接受命令名稱並傳回它的別名。

從 Windows PowerShell 3.0 開始， **Get 別名** 會以格式顯示非連字號的別名名稱， `<alias> -> <definition>` 讓您更容易找到所需的資訊。

## 範例

### 範例1：取得目前會話中的所有別名

```
PS C:\> Get-Alias

CommandType     Name
-----------     ----
Alias           % -> ForEach-Object
Alias           ? -> Where-Object
Alias           ac -> Add-Content
Alias           asnp -> Add-PSSnapin
Alias           cat -> Get-Content
Alias           cd -> Set-Location
Alias           chdir -> Set-Location
Alias           clc -> Clear-Content
Alias           clear -> Clear-Host
Alias           clhy -> Clear-History
...
```

此命令取得目前工作階段中的所有別名。

輸出 `<alias> -> <definition>` 會顯示 Windows PowerShell 3.0 中引進的格式。
此格式只用於不含連字號的別名，因為含連字號的別名通常是 Cmdlet 和函式的慣用名稱，而非暱稱。

### 範例2：依名稱取得別名

```powershell
Get-Alias -Name gp*, sp* -Exclude *ps
```

此命令會取得以 gp 或 sp 開頭的所有別名，但以 ps 結尾的別名除外。

### 範例3：取得 Cmdlet 的別名

```powershell
Get-Alias -Definition Get-ChildItem
```

此命令取得 Get-ChildItem Cmdlet 的別名。

依預設，當您知道別名時， **取得別名** Cmdlet 會取得專案名稱。
當您知道專案名稱時， *定義* 參數會取得別名。

### 範例4：依屬性取得別名

```powershell
Get-Alias | Where-Object {$_.Options -Match "ReadOnly"}
```

此命令會取得 Options 屬性值為 ReadOnly 的所有別名。
此命令可讓您快速找出 PowerShell 內建的別名，因為它們具有 ReadOnly 選項。

選項只是 System.management.automation.aliasinfo 物件的一個屬性，可 **取得別名** 。
若要尋找 System.management.automation.aliasinfo 物件的所有屬性和方法，請輸入 `Get-Alias | get-member` 。

### 範例5：依名稱取得別名並依開頭字母篩選

```powershell
Get-Alias -Definition "*-PSSession" -Exclude e* -Scope Global
```

此範例取得名稱結尾為 "-PSSession" 且開頭不是 "e" 之命令的別名。

命令使用 *Scope* 參數將命令套用至全域範圍。
當您想要取得工作階段中的別名時，這在指令碼中相當有用。

## PARAMETERS

### -Definition

取得指定項目的別名。
請輸入 Cmdlet、函式、指令碼、檔案或可執行檔的名稱。

此參數稱為 *定義* ，因為它會在別名物件的定義屬性中搜尋專案名稱。

```yaml
Type: System.String[]
Parameter Sets: Definition
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Exclude

省略指定的項目。
此參數的值會限定 Name 和 Definition 參數。
輸入名稱、定義或模式，例如 "s*"。
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

### -Name

指定此 Cmdlet 取得的別名。
允許使用萬用字元。
依預設，會抓取 `Get-Alias` 為目前會話定義的所有別名。
參數名稱 **名稱** 是選擇性的。
您也可以透過管線將別名名稱傳送至 `Get-Alias` 。

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: False
Position: 0
Default value: All aliases
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Scope

指定此 Cmdlet 取得別名的範圍。
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
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

您可以透過管線將別名名稱傳送至 **取得別名** 。

## 輸出

### System.Management.Automation.AliasInfo

**取得別名** 會傳回代表每個別名的物件。
**取得別名** 會針對每個別名傳回相同的物件，但 PowerShell 會使用以箭號為基礎的格式來顯示非連字號別名的名稱。

## 注意

- 若要建立新的別名，請使用 Set-Alias 或 New-Alias。 若要刪除別名，請使用 Remove-Item。
- 箭號型別名名稱格式不會用於含連字號的別名。 這些可能是 Cmdlet 和函式的慣用替代名稱，而不是典型的縮寫或暱稱。

## 相關連結

[Export-Alias](Export-Alias.md)

[Import-Alias](Import-Alias.md)

[New-Alias](New-Alias.md)

[Set-Alias](Set-Alias.md)

[別名提供者](../Microsoft.PowerShell.Core/About/about_Alias_Provider.md)

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)
