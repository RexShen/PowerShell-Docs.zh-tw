---
external help file: System.Management.Automation.dll-Help.xml
Module Name: Microsoft.PowerShell.Core
ms.date: 03/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-experimentalfeature?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ExperimentalFeature
ms.openlocfilehash: 993cc47f9c95fc39d717bb3b76b3de01f16ad47e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204903"
---
# Get-ExperimentalFeature

## 概要
取得實驗性功能。

## SYNTAX

```
Get-ExperimentalFeature [[-Name] <String[]>] [<CommonParameters>]
```

## DESCRIPTION

Cmdlet 會傳回 `Get-ExperimentalFeature` PowerShell 探索到的所有實驗性功能。
實驗性功能可以來自模組或 PowerShell 引擎。 實驗性功能可讓使用者安全地測試新功能，並提供意見反應 (通常會在設計被視為完成之前透過 GitHub) ，而且任何變更都可能會變成重大變更。

## 範例

### 範例 1

取得目前註冊的實驗性功能及其目前狀態的清單。

```powershell
Get-ExperimentalFeature
```

```Output
Name                         Enabled Source      Description
----                         ------- ------      -----------
PSImplicitRemotingBatching   False PSEngine      Batch implicit remoting proxy commands to improve performance
```

## PARAMETERS

### -Name

要傳回之特定實驗性功能的名稱或名稱。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String[]

要傳回的實驗性功能名稱或名稱。

## 輸出

### ExperimentalFeature

如果未指定名稱，則傳回符合所要求名稱或所有實驗性功能的實例。

## 注意

## 相關連結

[Disable-ExperimentalFeature](Disable-ExperimentalFeature.md)

[Enable-ExperimentalFeature](Enable-ExperimentalFeature.md)
