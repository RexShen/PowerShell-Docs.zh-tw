---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-experimentalfeature?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-ExperimentalFeature
ms.openlocfilehash: 9b85e429df0de4c740345a7e1afc42b7614a4a96
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203820"
---
# Disable-ExperimentalFeature

## 概要
在啟動新的 PowerShell 實例時停用實驗性功能。

## SYNTAX

```
Disable-ExperimentalFeature [-Name] <String[]> [-Scope <ConfigScope>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

此 `Disable-ExperimentalFeature` Cmdlet 會從 `powershell.config.json` PowerShell 啟動時讀取的設定檔案中移除已命名的實驗性功能，以停用實驗性功能。

此 Cmdlet 是在 PowerShell 6.2 中引進。

> [!NOTE]
> 實驗性功能狀態的任何變更只會在重新開機 PowerShell 時生效

## 範例

### 範例1：停用實驗性功能

在此範例中，如果先前已啟用此實驗性功能，則 `powershell.config.json` 會更新檔案，讓使用者在 PowerShell 重新開機後不啟用該功能。
成功時，不會對管線輸出任何內容，而且只會顯示警告訊息。

```powershell
PS C:\> Disable-ExperimentalFeature PSImplicitRemotingBatching
```

```Output
WARNING: Enabling and disabling experimental features do not take effect until next start of PowerShell.
```

## PARAMETERS

### -Confirm

在執行 Cmdlet 前提示您確認。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

要停用之實驗性功能的名稱或名稱。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Scope

決定 `powershell.config.json` 是否要更新其是否會影響所有使用者，或只影響目前的使用者。

```yaml
Type: System.Management.Automation.Configuration.ConfigScope
Parameter Sets: (All)
Aliases:
Accepted values: AllUsers, CurrentUser

Required: False
Position: Named
Default value: CurrentUser
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
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### ExperimentalFeature

將 ExperimentalFeature 的管道實例從 `Get-ExperimentalFeature` Cmdlet 傳送至停用。

## 輸出

### 無

此 Cmdlet 不會傳回任何輸出。

## 注意

實驗性功能的狀態變更只會在重新開機 PowerShell 時生效。

## 相關連結

[Enable-ExperimentalFeature](Enable-ExperimentalFeature.md)

[Get-ExperimentalFeature](Get-ExperimentalFeature.md)
