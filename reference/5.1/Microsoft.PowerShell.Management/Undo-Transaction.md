---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/undo-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Undo-Transaction
ms.openlocfilehash: 1acb06ea7b05a2127b04a22c4c51b92cd68056f2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203456"
---
# Undo-Transaction

## 概要
將使用中交易回復。

## SYNTAX

```
Undo-Transaction [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
**復原交易** Cmdlet 會回復使用中交易。
當您回復交易時，會捨棄交易中命令所做的變更，並將資料還原為其原始格式。

如果交易包含多個訂閱者，則 **Undo 交易** 命令會回復所有訂閱者的整個交易。

根據預設，如果交易中的任何命令產生錯誤，就會自動將交易回復。
不過，您可以使用不同的回復喜好設定來啟動交易，並且可以使用這個 Cmdlet 隨時復原使用中的交易。

**復原交易** Cmdlet 是支援 Windows PowerShell 中交易功能的其中一組 Cmdlet。
如需詳細資訊，請參閱 about_Transactions。

## 範例

### 範例1：復原目前的交易

```
PS C:\> Undo-Transaction
```

此命令會回復目前的主動式交易。

### 範例2：啟動和回復交易

```
PS C:\> cd hkcu:\software
PS HKCU:\Software> Start-Transaction
PS HKCU:\Software> New-Item -Path "ContosoCompany" -UseTransaction
PS HKCU:\Software> Undo-Transaction
```

此範例會啟動交易，然後將其回復。
因此，也就不會對登錄進行任何變更。

### 範例3：為所有訂閱者回復交易

```
PS C:\> cd hkcu:\software
PS HKCU:\Software> Start-Transaction
PS HKCU:\Software> New-Item -Path "ContosoCompany" -UseTransaction
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   -----
Error                1                 Active

PS HKCU:\Software> Start-Transaction
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   -----
Error                2                 Active

PS HKCU:\Software> Undo-Transaction
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   -----
Error                0                 RolledBack
```

這個範例示範當任何訂閱者回復交易時，都會針對所有訂閱者回復整個交易。

第一個命令將位置變更為 HKCU:\Software 登錄機碼。

第二個命令啟動交易。

第三個命令使用 New-Item Cmdlet 來建立新的登錄機碼。
此命令會使用 *UseTransaction* 參數將變更包含在交易中。

第四個命令使用 Get-Transaction Cmdlet 來取得使用中交易。
請注意，狀態是 Active，而訂閱者計數為 1。

第五個命令再次使用 Start-Transaction 命令。
一般來說，當主要交易使用的腳本包含它自己的完整交易時，當另一個交易正在進行時，就會啟動交易。
此範例會以互動方式執行，讓您可以分階段進行檢查。
當您在另一個交易正在進行時執行 **啟動交易** 命令時，這些命令會將現有的交易加入成為新的訂閱者，而訂閱者計數會遞增。

第六個命令會使用 **取得交易** Cmdlet 來取得使用中的交易。
請注意，訂閱者計數現在是 2。

第七個命令使用 **恢復交易來復原** 交易。
此命令不會傳回任何物件。

最後一個命令是取得使用中（或在此案例中為最近使用中交易）的 **取得交易** 命令。
結果會顯示交易被回復，而且訂閱者計數為 0，表示已針對所有訂閱者回復交易。

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
這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無
您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### 無
此 Cmdlet 不會傳回任何輸出。

## 注意

* 您無法回復已確認的交易。

  您無法回復使用中交易以外的任何交易。
若要回復不同的獨立交易，您必須先確認或回復使用中交易。

  回復交易會將交易結束。
若要再次使用某個交易，您必須啟動新的交易。

## 相關連結

[Complete-Transaction](Complete-Transaction.md)

[Get-Transaction](Get-Transaction.md)

[Start-Transaction](Start-Transaction.md)

[Use-Transaction](Use-Transaction.md)
