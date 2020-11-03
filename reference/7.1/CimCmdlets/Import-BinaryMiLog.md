---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/20/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/import-binarymilog?WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-BinaryMiLog
ms.openlocfilehash: ce5dd31170bc47edaa04ca3c31deab62dc4ec354
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208808"
---
# Import-BinaryMiLog

## 概要
用來根據匯出檔案的內容重新建立儲存的物件。

## SYNTAX

```
Import-BinaryMiLog [-Path] <String> [<CommonParameters>]
```

## DESCRIPTION

使用這個指令程式可根據所建立的匯出檔案內容，重新建立儲存的物件 `Export-BinaryMILog` 。 這個 Cmdlet 類似于 `Import-Clixml` ，但會將 `Export-BinaryMILog` 產生的物件儲存在二進位編碼的檔案中。

## 範例

### 範例 1-將匯出的物件還原至檔案

```powershell
Import-BinaryMiLog -Path "Processes.bmil"
```

## PARAMETERS

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

### 無

## 輸出

### System.Object

## 注意

## 相關連結
