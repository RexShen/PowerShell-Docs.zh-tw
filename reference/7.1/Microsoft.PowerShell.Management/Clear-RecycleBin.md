---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-recyclebin?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-RecycleBin
ms.openlocfilehash: 7e34db6eb29bf60da5ce1217653db815347d69ae
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205087"
---
# Clear-RecycleBin

## 概要
清除回收站的內容。

## SYNTAX

### 全部

```
Clear-RecycleBin [[-DriveLetter] <String[]>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Clear-RecycleBin`Cmdlet 會刪除電腦回收站的內容。 這個動作就像使用 Windows **Empty 資源回收筒** 一樣。

此 Cmdlet 是在 PowerShell 7 中 readded。

## 範例

### 1：清除所有回收站

在此範例中，會清除所有本機電腦的回收站。

```powershell
Clear-RecycleBin
```

```Output
Confirm
Are you sure you want to perform this action?
Performing the operation "Clear-RecycleBin" on target "All of the contents of the Recycle Bin".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

`Clear-RecycleBin` 提示使用者進行確認，以清除本機電腦上的所有回收站。

### 2：清除指定的回收站

此範例會清除指定磁碟機號的回收站。

```powershell
Clear-RecycleBin -DriveLetter C
```

`Clear-RecycleBin` 使用 **r** 參數來指定 **C** 磁片區上的回收站。 系統會提示使用者進行確認，以執行命令。

### 3：清除所有回收站但不確認

此範例不會提示您確認是否要清除本機電腦的回收站。

```powershell
Clear-RecycleBin -Force
```

`Clear-RecycleBin` 使用 **Force** 參數，且不會提示使用者進行確認，以清除本機電腦上的所有回收站。

替代方法是將取代 `-Force` 為 `-Confirm:$false` 。

## PARAMETERS

### -R

指定要清除單一磁碟機號或磁碟機號陣列的回收站。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Force

指定不提示使用者確認清除回收站。

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

### -Confirm

執行 Cmdlet 之前，提示使用者確認。 即使未指定 **Confirm** 參數，仍會提示使用者進行確認。

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

顯示執行時所發生 `Clear-RecycleBin` 的情況。 不會執行此 Cmdlet。

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

## 輸出

### 無

## 注意

## 相關連結

