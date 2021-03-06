---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 3/13/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/start-sleep?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Sleep
ms.openlocfilehash: e4add39c09b6123aaf8c9302529346a6b1dec391
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203119"
---
# Start-Sleep

## 概要
將指令碼或工作階段中的活動暫停一段指定的時間。

## SYNTAX

### 秒 (預設值)

```
Start-Sleep [-Seconds] <Int32> [<CommonParameters>]
```

### 毫秒

```
Start-Sleep -Milliseconds <Int32> [<CommonParameters>]
```

## DESCRIPTION

指令 `Start-Sleep` 程式會在指定的時間內暫停腳本或會話中的活動。
您可以將它用於許多工作，例如等待操作完成，或先暫停再重複執行一項操作。

## 範例

### 範例 1︰讓所有命令睡眠 15 秒

```powershell
Start-Sleep -s 15
```

此命令讓工作階段中的所有命令睡眠 15 秒。

### 範例 2︰讓所有命令進入睡眠狀態

```powershell
Start-Sleep -m 500
```

此命令讓工作階段中的所有命令睡眠 1/2 秒 (500 毫秒)。

## PARAMETERS

### -Milliseconds

指定資源的睡眠時間長度 (單位為毫秒)。
參數可以縮寫為 **m** 。

```yaml
Type: System.Int32
Parameter Sets: Milliseconds
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Seconds

指定資源的睡眠時間長度 (單位為秒)。
您可以省略參數名稱 ( **秒** ) ，也可以將它縮寫為 **s** 。

```yaml
Type: System.Int32
Parameter Sets: Seconds
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### System.Int32

您可以用管線將秒數傳送至 `Start-Sleep` 。

## 輸出

### 無

此 Cmdlet 不會傳回任何輸出。

## 注意

- 您也可以 `Start-Sleep` 使用內建的別名來參考 `sleep` 。 如需詳細資訊，請參閱 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。
- `Ctrl+C` 中斷 `Start-Sleep` 。
  - `Ctrl+C` 不會中斷 `[Threading.Thread]::Sleep` 。 如需詳細資訊，請參閱 [Sleep 方法](/dotnet/api/system.threading.thread.sleep)。

## 相關連結
