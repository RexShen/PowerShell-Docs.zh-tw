---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Guid
ms.openlocfilehash: 0356b0f9a0792cd75828bf735e7806b5cca0daa3
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "93196674"
---
# New-Guid

## 概要
建立 GUID。

## SYNTAX

```
New-Guid [<CommonParameters>]
```

## DESCRIPTION

**New-Guid** Cmdlet 會建立一個隨機全域唯一識別碼 (GUID)。
如果您在指令碼中需要唯一識別碼，您可以視需要建立 GUID。

## 範例

### 範例 1︰建立 GUID

```
PS C:\> New-Guid
Guid
----
0352cf0f-2e7a-4aee-801d-7f27f8344c77
```

此命令會建立隨機的 GUID。
或者，您可以將此 Cmdlet 的輸出儲存於變數中，以在指令碼中的其他位置使用。

## PARAMETERS

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

## 輸出

### System.Guid

這個 Cmdlet 會傳回 GUID。

## 注意

## 相關連結
