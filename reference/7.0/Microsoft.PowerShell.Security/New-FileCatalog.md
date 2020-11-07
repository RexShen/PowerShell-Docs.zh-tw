---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/new-filecatalog?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-FileCatalog
ms.openlocfilehash: 007b486b7b65d9b6481839643fe839eda49a1113
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94346950"
---
# New-FileCatalog

## 概要
`New-FileCatalog` 建立檔案雜湊的類別目錄檔案，可用來驗證檔案的真實性。

## SYNTAX

```
New-FileCatalog [-CatalogVersion <Int32>] [-CatalogFilePath] <String> [[-Path] <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION

`New-FileCatalog` 為一組資料夾和檔案建立 [Windows 類別目錄](/windows-hardware/drivers/install/catalog-files) 檔案。 此類別目錄檔案包含所提供路徑中所有檔案的雜湊。 然後，使用者可以使用其檔案來散發類別目錄，讓使用者可以在目錄建立時間之後，驗證是否已對資料夾進行任何變更。

支援類別目錄第 1 版和第 2 版。 第1版使用 (已淘汰的) SHA1 雜湊演算法來建立檔案雜湊，第2版使用 SHA256。 Windows Server 2008 R2 或 Windows 7 不支援第 2 版的類別目錄。 Windows 8、Windows Server 2012 和更新版本的作業系統，應該使用類別目錄第 2 版。

## 範例

### 範例1：建立的檔案類別目錄 `Microsoft.PowerShell.Utility`

```powershell
New-FileCatalog -Path $PSHOME\Modules\Microsoft.PowerShell.Utility -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -CatalogVersion 2.0
```

```Output
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         11/2/2018 11:58 AM            950 Microsoft.PowerShell.Utility.cat
```

## PARAMETERS

### -CatalogFilePath

應放置目錄檔案 ( .cat) 的檔案或資料夾路徑。 如果指定了資料夾路徑，則會使用預設的檔案名 `catalog.cat` 。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -CatalogVersion

接受 `1.0` 或 `2.0` 指定類別目錄版本的可能值。 `1.0` 應該盡可能避免使用，因為它使用不安全的 SHA-1 雜湊演算法，而使用256安全的 sha-1 雜湊演算法時， `2.0` `1.0` 是 Windows 7 和伺服器2008R2 上唯一支援的演算法。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

接受目錄檔案中應包含的檔案或資料夾路徑或路徑陣列。 如果指定資料夾，也會包含資料夾中的所有檔案。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

管線會使用做為目錄檔案名的字串。

## 輸出

### System.IO.FileInfo

## 注意

此 Cmdlet 僅適用于 Windows 平臺。

## 相關連結

[Test-FileCatalog](Test-FileCatalog.md)

[PowerShellGet](/powerShell/module/powershellget)
