---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/convert-path?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Convert-Path
ms.openlocfilehash: a442d8ff9f021e1ec05671d9190d35ef97ff4d72
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204059"
---
# Convert-Path

## 概要
將路徑從 PowerShell 路徑轉換為 PowerShell 提供者路徑。

## SYNTAX

### 路徑 (預設值)

```
Convert-Path [-Path] <String[]> [-UseTransaction] [<CommonParameters>]
```

### LiteralPath

```
Convert-Path -LiteralPath <String[]> [-UseTransaction] [<CommonParameters>]
```

## DESCRIPTION

`Convert-Path`Cmdlet 會將路徑從 powershell 路徑轉換成 powershell 提供者路徑。

## 範例

### 範例 1︰將工作目錄轉換成標準檔案系統路徑

這個範例會將目前的工作目錄（以點 (`.`) 表示）轉換成標準檔案系統路徑。

```
PS C:\> Convert-Path .
C:\
```

### 範例 2︰將提供者路徑轉換成標準登錄路徑

此範例會將 PowerShell 提供者路徑轉換成標準登錄路徑。

```powershell
PS C:\> Convert-Path HKLM:\Software\Microsoft
HKEY_LOCAL_MACHINE\Software\Microsoft
```

### 範例 3︰將路徑轉換成字串

這個範例會將目前提供者（FileSystem 提供者）的主目錄路徑轉換成字串。

```powershell
PS C:\> Convert-Path ~
C:\Users\User01
```

## PARAMETERS

### -LiteralPath

以字串陣列指定要轉換的路徑。 **LiteralPath** 參數的值將完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含逸出字元，請將它括在單引號中。 單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

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

指定要轉換的 PowerShell 路徑。

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

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

您可以使用管線將路徑 (而非常值路徑) 傳送至此 Cmdlet。

## 輸出

### System.String

此 Cmdlet 會傳回包含已轉換路徑的字串。

## 注意

包含路徑名詞的 Cmdlet 會操作路徑名稱，並傳回所有 PowerShell 提供者都可解讀的精簡格式名稱。 它們是設計用於程式與指令碼，您可以在其中以特定格式顯示所有或部分路徑名稱。 使用它們，就像您使用 **Dirname** 、 **Normpath** 、 **Realpath** 、 **Join** 或其他路徑操作工具一樣。

您可以使用 Path Cmdlet 於數種提供者，包括 FileSystem、Registry 與 Certificate 提供者。

此 Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。 若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。 如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

`Convert-Path` 只會轉換現有的路徑。 它無法用來轉換尚未存在的位置。

## 相關連結

[Join-Path](Join-Path.md)

[Resolve-Path](Resolve-Path.md)

[Split-Path](Split-Path.md)

[Test-Path](Test-Path.md)

[Get-PSProvider](Get-PSProvider.md)
