---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-null?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Null
ms.openlocfilehash: a9d5c47eaf189e37f7f16b11cd48101f7b0e584d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204484"
---
# Out-Null

## 概要
隱藏輸出，而不是將它向下傳送或顯示。

## SYNTAX

```
Out-Null [-InputObject <PSObject>] [<CommonParameters>]
```

## DESCRIPTION

**Out-Null** Cmdlet 會將其輸出傳送至 Null，實際上會將其從管線中移除，並防止輸出顯示在畫面上。

## 範例

### 範例 1︰刪除輸出

```powershell
Get-ChildItem | Out-Null
```

此命令會取得目前位置/目錄中的專案，但其輸出不會透過管線傳遞，也不會在命令列中顯示。
這適用于隱藏您不需要的輸出。

## PARAMETERS

### -InputObject

指定要傳送至 Null (從管線) 移除的物件。
輸入包含物件的變數，或輸入可取得物件的命令或運算式。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Management.Automation.PSObject

您可以使用管線將任何物件傳送至此 Cmdlet。

## 輸出

### 無

此 Cmdlet 不會產生任何輸出。

## 注意

* 包含 **out** Cmdlet ( **out** Cmdlet 的 Cmdlet) 沒有名稱或檔案路徑的參數。 若要將資料傳送給 **Out** Cmdlet，請使用管線運算子 (|) 將 PowerShell 命令的輸出傳送至 Cmdlet。 您也可以將資料儲存在變數中，然後使用 *InputObject* 參數將資料傳遞給 Cmdlet。 如需詳細資訊，請參閱範例。
* **Out-Null** 不會傳回任何輸出物件。 如果您使用管線將 **Out-Null** 的輸出傳送至 Get-Member Cmdlet， **Get-Member** 即會報告尚未指定任何物件。

## 相關連結

[Out-Default](Out-Default.md)

[Out-Host](Out-Host.md)
