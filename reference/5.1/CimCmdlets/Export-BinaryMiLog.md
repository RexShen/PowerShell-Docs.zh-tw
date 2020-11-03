---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/20/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/export-binarymilog?WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-BinaryMiLog
ms.openlocfilehash: cf03ad884121c6cf8cf65cdb791cbdc4e587c3b9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202515"
---
# Export-BinaryMiLog

## 概要
建立物件或物件的二進位編碼標記法，並將它儲存在檔案中。

## SYNTAX

```
Export-BinaryMiLog [-InputObject <CimInstance>] [-Path] <String> [<CommonParameters>]
```

## DESCRIPTION

`Export-BinaryMILog`Cmdlet 會建立物件或物件的二進位標記法，並將它儲存在檔案中。 然後，您可以使用 `Import-BinaryMiLog` Cmdlet，根據該檔案的內容重新建立儲存的物件。

這個 Cmdlet 類似于 `Import-Clixml` ，但會將 `Export-BinaryMILog` 產生的物件儲存在二進位編碼的檔案中。

## 範例

### 範例 1-建立 CimInstances 的二進位標記法

```powershell
Get-CimInstance Win32_Process | Export-BinaryMiLog -Path "Processes.bmil"
```

此命令會將 **CimInstances** 匯出至 Path 參數所指定的二進位 MI 記錄檔。 請參閱 Import-BinaryMiLog 的範例，以瞭解如何藉由匯入這個檔案來重新建立 **CimInstances** 。

## PARAMETERS

### -InputObject

指定此 Cmdlet 的輸入。 您可以使用這個參數，或者您可以透過管線將輸入傳送到此 Cmdlet。

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Path

指定要在其中儲存物件之二進位表示的檔案路徑。 **Path** 參數支援萬用字元和相對路徑。 如果路徑解析為一個以上的檔案，則此 Cmdlet 會產生錯誤。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### Microsoft.Management.Infrastructure.CimInstance

## 輸出

### System.Object

## 注意

## 相關連結

[Get-CimInstance](get-ciminstance.md)

[Import-BinaryMiLog](import-binarymilog.md)

[Import-Clixml](../microsoft.powershell.utility/import-clixml.md)
