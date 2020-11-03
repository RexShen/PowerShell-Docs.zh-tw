---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/resolve-path?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resolve-Path
ms.openlocfilehash: d5a4e16f06ae98532f9716deb87dcadac50f8081
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202051"
---
# Resolve-Path

## 概要
解析路徑中的萬用字元，並顯示路徑內容。

## SYNTAX

### 路徑 (預設值)

```
Resolve-Path [-Path] <String[]> [-Relative] [-Credential <PSCredential>] [<CommonParameters>]
```

### LiteralPath

```
Resolve-Path -LiteralPath <String[]> [-Relative] [-Credential <PSCredential>] [<CommonParameters>]
```

## DESCRIPTION

`Resolve-Path`Cmdlet 會在指定的位置顯示符合萬用字元模式的專案和容器。 相符可包含檔案、資料夾、登錄機碼，或可從 New-psdrive 提供者存取的任何其他物件。

## 範例

### 範例1：解析主資料夾路徑

 (~) 的波狀符號字元是目前使用者的主資料夾的縮寫標記法。 此範例顯示傳回 `Resolve-Path` 完整路徑值。

```powershell
PS C:\> Resolve-Path ~
```

```Output
Path
----
C:\Users\User01
```

### 範例2：解析 Windows 資料夾的路徑

```powershell
PS C:\> Resolve-Path -Path "windows"
```

```Output
Path
----
C:\Windows
```

從 C：磁片磁碟機的根目錄執行時，此命令會傳回 C：磁片磁碟機中 Windows 資料夾的路徑。

### 範例3：取得 Windows 資料夾中的所有路徑

```powershell
PS C:\> "C:\windows\*" | Resolve-Path
```

此命令會傳回 C：\Windows 資料夾中的所有資料夾。 命令使用管線運算子 (|) 傳送路徑字串至 `Resolve-Path` 。

### 範例4：解析 UNC 路徑

```powershell
PS C:\> Resolve-Path -Path "\\Server01\public"
```

此命令解析通用命名慣例 (UNC) 路徑，並傳回路徑中的共用。

### 範例5：取得相對路徑

```powershell
PS C:\> Resolve-Path -Path "c:\prog*" -Relative
```

```Output
.\Program Files
.\Program Files (x86)
.\programs.txt
```

此命令傳回位於 C: 磁碟機根目錄之目錄的相對路徑。

### 範例6：解析包含括弧的路徑

此範例使用 **LiteralPath** 參數來解析測試 \[ xml \] 子資料夾的路徑。
使用 **LiteralPath** 會讓括弧被視為一般字元，而不是正則運算式。

```powershell
PS C:\> Resolve-Path -LiteralPath 'test[xml]'
```

## PARAMETERS

### -Credential

指定具有執行此動作權限的使用者帳戶。
預設為目前使用者。

輸入使用者名稱（例如 User01 或 Domain01\User01），或傳遞 **PSCredential** 物件。 您可以使用 Cmdlet 來建立 **PSCredential** 物件 `Get-Credential` 。 如果您輸入使用者名稱，此 Cmdlet 會提示您輸入密碼。

使用 PowerShell 安裝的任何提供者都不支援此參數。

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

### -LiteralPath

指定要解析的路徑。
**LiteralPath** 參數的值會完全依照輸入的方式使用。
沒有字元會被視為萬用字元。
如果路徑包含逸出字元，請將它括在單引號中。
單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

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

### -Path

指定要解析的 PowerShell 路徑。
這是必要參數。
您也可以使用管線將路徑字串傳送至 `Resolve-Path` 。
允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Relative

指出此 Cmdlet 會傳回相對路徑。

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

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### System.String

您可以使用管線將包含路徑的字串傳送至此 Cmdlet

## 輸出

### System.management.automation.pathinfo，System.string. String

傳回 **system.management.automation.pathinfo** 物件。 如果您指定了 **相對** 參數，則會傳回已解析路徑的字串值。

## 注意

這些 `*-Path` Cmdlet 可與 FileSystem、登錄和憑證提供者搭配運作。

`Resolve-Path` 是設計來搭配任何提供者使用。 若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。 如需詳細資訊，請參閱 [about_providers](../microsoft.powershell.core/about/about_providers.md)。

`Resolve-Path` 只解析現有的路徑。 它無法用來解析尚未存在的位置。

## 相關連結

[Convert-Path](Convert-Path.md)

[Join-Path](Join-Path.md)

[Split-Path](Split-Path.md)

[Test-Path](Test-Path.md)

