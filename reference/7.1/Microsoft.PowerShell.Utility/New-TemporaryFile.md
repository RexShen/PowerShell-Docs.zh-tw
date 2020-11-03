---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-temporaryfile?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-TemporaryFile
ms.openlocfilehash: 406675d8bde1b6b9a28913c09d5374393705f93b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204979"
---
# New-TemporaryFile

## 概要
建立暫存檔。

## SYNTAX

```
New-TemporaryFile [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

此 Cmdlet 會建立可在腳本中使用的暫存檔案。

此 `New-TemporaryFile` Cmdlet 會建立副檔名為的空白檔案 `.tmp` 。
此 Cmdlet 會為檔案命名 `tmp<NNNN>.tmp` ，其中 `<NNNN>` 是隨機的十六進位數位。
Cmdlet 會在您的 **暫存** 資料夾中建立檔案。

此 Cmdlet 會使用 [GetTempPath ( # B1](/dotnet/api/system.io.path.gettemppath) 方法來尋找您的 **暫存** 資料夾。 這個方法會以下列順序檢查環境變數是否存在，並使用第一個找到的路徑：

- 在 Windows 平臺上：

  1. TMP 環境變數所指定的路徑。
  1. TEMP 環境變數所指定的路徑。
  1. USERPROFILE 環境變數所指定的路徑。
  1. Windows 目錄。

- 在非 Windows 平臺上：使用 TMPDIR 環境變數所指定的路徑。

## 範例

### 範例1：建立暫存檔案

```powershell
$TempFile = New-TemporaryFile
```

此命令會 `.tmp` 在暫存資料夾中產生檔案，然後將檔案的參考儲存在 `$TempFile` 變數中。 您稍後可以在腳本中使用此檔案。

## PARAMETERS

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

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

## 輸出

### System.IO.FileInfo

此 Cmdlet 會傳回代表暫存檔案的 **FileInfo** 物件。

## 注意

## 相關連結

