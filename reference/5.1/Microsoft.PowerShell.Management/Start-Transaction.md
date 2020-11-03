---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/start-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Transaction
ms.openlocfilehash: 53be131f45f15e5d2053b183040dc7b3dca4a14c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203483"
---
# Start-Transaction

## 概要
啟動交易。

## SYNTAX

```
Start-Transaction [-Timeout <Int32>] [-Independent] [-RollbackPreference <RollbackSeverity>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
**啟動交易** Cmdlet 會啟動交易，這是一系列作為單位來管理的命令。
您可以完成或認可交易。
或者，它可以完全復原或復原，讓交易所變更的任何資料都還原為其原始狀態。
由於交易中的命令會被視為一個單位來管理，因此，所有命令必須一起確認或一起回復。

根據預設，如果交易中的任何命令產生錯誤，就會自動回復交易。
您可以使用 *RollbackPreference* 參數來變更此行為。

交易中使用的 Cmdlet 必須設計為支援交易。
支援交易的 Cmdlet 具有 *UseTransaction* 參數。
若要在提供者中執行交易，該提供者必須支援交易。
Windows Vista 和更新版本的 Windows 作業系統中的 Windows PowerShell Registry 提供者支援交易。
您也可以使用 **TransactedString** 類別，在任何支援 Windows PowerShell 的 Windows 系統版本上的交易中包含運算式。
其他的 Windows PowerShell 提供者也可以支援交易。

一次只有一個交易可以處於使用中狀態。
如果您在交易正在進行時啟動新的獨立交易，新的交易就會變成使用中的交易，而且您必須先認可或回復新交易，然後再對原始交易進行任何變更。

**Start-Transaction** Cmdlet 是一組支援 Windows PowerShell 中交易功能的 Cmdlet 之一。
如需詳細資訊，請參閱 about_Transactions。

## 範例

### 範例1：啟動和回復交易

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany" -UseTransaction
PS HKCU:\software> New-ItemProperty "ContosoCompany" -Name "MyKey" -Value 123 -UseTransaction
PS HKCU:\software> Undo-Transaction
```

這些命令會啟動交易，然後回復交易。
由於交易會回復，所以不會對登錄進行任何變更。

### 範例2：啟動和完成交易

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany" -UseTransaction
PS HKCU:\software> New-ItemProperty "ContosoCompany" -Name "MyKey" -Value 123 -UseTransaction
PS HKCU:\software> Complete-Transaction
```

這些命令會啟動交易，然後完成交易。
在使用 **完整交易** 命令之前，不會對登錄進行任何變更。

### 範例3：使用不同的回復喜好設定

```
PS C:\> cd HKCU:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item -Path "NoPath" -Name "ContosoCompany" -UseTransaction
PS HKCU:\software> New-Item -Path . -Name "ContosoCompany" -UseTransaction
PS HKCU:\software> Start-Transaction -RollbackPreference never
PS HKCU:\software> New-Item -Path "NoPath" -Name "ContosoCompany" -UseTransaction
PS HKCU:\software> New-Item -Path . -Name "ContosoCompany" -UseTransaction

# Start-Transaction (-rollbackpreference error)

PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item -Path "NoPath" -Name "ContosoCompany" -UseTransaction
New-Item : The registry key at the specified path does not exist.
At line:1 char:9
+ new-item <<<<  -Path NoPath -Name ContosoCompany -UseTransaction

PS HKCU:\software> New-Item -Path . -Name "Contoso" -UseTransaction

New-Item : Cannot use transaction. The transaction has been rolled back or has timed out.
At line:1 char:9
+ new-item <<<<  -Path . -Name ContosoCompany -UseTransaction

# Start-Transaction (-rollbackpreference never)

PS HKCU:\software> Start-Transaction -RollbackPreference never
PS HKCU:\software> New-Item -Path "NoPath" -Name "ContosoCompany" -UseTransaction

New-Item : The registry key at the specified path does not exist.
At line:1 char:9
+ new-item <<<<  -Path NoPath -Name "ContosoCompany" -UseTransaction
PS HKCU:\software> New-Item -Path . -Name "ContosoCompany" -UseTransaction

Hive: HKEY_CURRENT_USER\Software
SKC  VC Name                           Property
---  -- ----                           --------
0   0 ContosoCompany                 {}
PS HKCU:\Software> Complete-Transaction

# Succeeds
```

此範例示範變更 *RollbackPreference* 參數值的效果。

在第一組命令中， **Start-Transaction** 不會使用 *RollbackPreference* 。
因此，會使用預設值 (錯誤) 。
當交易命令中發生錯誤時，也就是指定的路徑不存在，就會自動回復交易。

在第二組命令中， **Start Transaction** 會使用 *RollbackPreference* ，其值為「永不」。
因此，當交易命令中發生錯誤時，交易仍為使用中狀態且可順利完成。

因為大部分的交易必須在沒有錯誤的情況下執行，所以通常偏好 *RollbackPreference* 的預設值。

### 範例4：交易正在進行時使用這個 Cmdlet

```
PS C:\> cd HKCU:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany" -UseTransaction
PS HKCU:\software> Start-Transaction
PS HKCU:\software> Get-Transaction
PS HKCU:\software> New-Item "ContosoCompany2" -UseTransaction
PS HKCU:\software> Complete-Transaction
PS HKCU:\software> Complete-Transaction
PS HKCU:\Software> Get-Transaction
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                2                 Active
```

此範例顯示交易進行中時使用 **啟動交易** 的效果。
這個效果類似加入進行中交易。

雖然這是簡化的命令，但這種情況通常是在交易涉及執行包含完整交易的腳本時發生。

第一個 **啟動交易** 命令會啟動交易。
第一個 **新專案** 命令是交易的一部分。

第二個 **啟動交易** 命令會將新的訂閱者新增至交易。
**取得交易** 命令現在會傳回訂閱者計數為2的交易。
第二個 **新專案** 命令是相同交易的一部分。

在整個交易完成之前，不會對登錄進行任何變更。
若要完成交易，您必須輸入兩個 **完整交易** 命令，每個訂閱者一個。
如果您在任何時間點回復交易，則會針對這兩個訂閱者復原所有交易。

### 範例5：當獨立交易正在進行時啟動

```
PS C:\> cd HKCU:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany" -UseTransaction
PS HKCU:\software> Start-Transaction -Independent
PS HKCU:\software> Get-Transaction
PS HKCU:\software> Undo-Transaction
PS HKCU:\software> New-ItemProperty -Path "ContosoCompany" -Name "MyKey" -Value 123 -UseTransaction
PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir contoso*
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
PS HKCU:\software> Undo-Transaction
PS HKCU:\software> New-ItemProperty -Path "ContosoCompany" -Name "MyKey" -Value 123 -UseTransaction
MyKey
-----
123
PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir contoso*
Hive: HKEY_CURRENT_USER\Software
SKC  VC Name                           Property
---  -- ----                           --------
0   1 MyCompany                      {MyKey}
```

此範例顯示在另一個交易正在進行時，使用 **啟動交易** 的 *獨立* 參數啟動交易的效果。
在這個案例中，會回復新交易，但不會對原始交易產生任何影響。

雖然交易在邏輯上是獨立的，但由於一次只能有一個交易可處於使用中狀態，因此，您必須先回復或確認最新交易，才能繼續執行原始交易上的工作。

第一組命令會啟動交易。
[ **新增專案** ] 命令是第一個交易的一部分。

在第二組命令中， **Start Transaction** 命令會使用 *獨立* 的參數。
接下來的「 **取得交易** 」命令會顯示使用中交易的交易對象，這是最新的交易。
訂閱者計數等於1，顯示交易無關。

使用 **Undo 交易** 命令復原使用中的交易時，原始交易會再次變成作用中狀態。

**ItemProperty** 命令（原始交易的一部分）會在沒有錯誤的情況下完成，而且可以使用 **完整交易** 命令來完成原始交易。
因此，會變更登錄。

### 範例6：執行不屬於交易一部分的命令

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany1" -UseTransaction
PS HKCU:\software> New-Item "ContosoCompany2"
PS HKCU:\software> New-Item "ContosoCompany3" -UseTransaction
PS HKCU:\software> dir contoso*
PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir contoso*
PS HKCU:\Software> dir contoso*

Hive: HKEY_CURRENT_USER\Software
SKC  VC Name                           Property
---  -- ----                           --------
0   0 ContosoCompany2                {}

PS HKCU:\Software> Complete-Transaction
PS HKCU:\Software> dir contoso*

Hive: HKEY_CURRENT_USER\Software
SKC  VC Name                           Property
---  -- ----                           --------
0   0 ContosoCompany1                     {}
0   0 ContosoCompany2                     {}
0   0 ContosoCompany3                     {}
```

這個範例示範交易正在進行時提交的命令，可以包含或不包含在交易中。
只有使用 *UseTransaction* 參數的命令是交易的一部分。

第一個和第三個 **新專案** 命令使用 *UseTransaction* 參數。
這些命令是交易的一部分。
因為第二個 **新專案** 命令未使用 *UseTransaction* 參數，所以它不是交易的一部分。

第一個 dir 命令會顯示效果。
第二個 **新專案** 命令會立即完成，但在認可交易之前，第一個和第三個 **新專案** 命令都沒有作用。

**完整交易** 命令認可交易。
如此一來，第二個 dir 命令會顯示所有新專案都會新增至登錄中。

### 範例7：回復未在指定時間內完成的交易

```
PS C:\> Start-Transaction -Timeout 2

# Wait two minutes...

PS C:\> Get-Transaction
PS C:\> New-Item HKCU:\Software\ContosoCompany -UseTransaction
PS C:\> Start-Transaction -Timeout 2

# Wait two minutes...

PS C:\> > Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   -----------
Error                1                 RolledBack

PS C:\> New-Item HKCU:\Software\ContosoCompany -UseTransaction

New-Item : Cannot use transaction. The transaction has been rolled back or has timed out.
At line:1 char:9
+ new-item <<<<  MyCompany -UseTransaction
```

此命令會使用 **start-Transaction** 的 *Timeout* 參數啟動必須在兩分鐘內完成的交易。
如果在超時時間過期時交易未完成，則會自動回復。

過期時，系統不會通知您，但 transaction 物件的 **Status** 屬性會設定為 RolledBack，而使用 *UseTransaction* 參數的命令則會失敗。

## PARAMETERS

### -獨立
指出此 Cmdlet 會啟動與任何進行中交易無關的交易。
依預設，如果您在另一個交易正在進行時使用 **啟動交易** ，則會將新的訂閱者新增到進行中的交易。
只有當工作階段中已經有進行中交易，這個參數才有作用。

依預設，如果您在交易正在進行時使用 **啟動交易** ，則會重複使用現有的交易對象，而且訂閱者計數會遞增。
這個效果類似加入原始交易。
Undo-Transaction 命令會回復整個交易。
若要完成交易，您必須針對每個訂閱者輸入 Complete-Transaction 命令。
因為大部分同時處於進行中狀態的交易都是相關的，所以預設值就足以應付大部分的使用。

如果您指定 *獨立* 參數，這個 Cmdlet 會建立可以完成或復原的新交易，而不會影響原始交易。
不過，由於一次只能有一個交易可以處於使用中狀態，因此，您必須先完成或回復新交易，然後才能繼續執行原始交易上的工作。

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

### -RollbackPreference
指定自動回復交易的條件。
此參數可接受的值為：

- 錯誤。
如果發生終止或非終止錯誤，即會自動回復交易。
- TerminatingError.
如果發生終止錯誤，即會自動回復交易。
- 永不。
永遠不會自動回復交易。

預設值為 Error。

```yaml
Type: System.Management.Automation.RollbackSeverity
Parameter Sets: (All)
Aliases:
Accepted values: Error, TerminatingError, Never

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Timeout
指定交易處於使用中狀態的最長時間 (以分鐘為單位)。
當逾時過期時，即會自動回復交易。

根據預設，在命令列啟動的交易不會逾時。
如果交易是透過指令碼啟動，則預設的逾時值是 30 分鐘。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutMins

Required: False
Position: Named
Default value: None
Accept pipeline input: False
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
此 Cmdlet 不會產生任何輸出。

## 注意

## 相關連結

[Complete-Transaction](Complete-Transaction.md)

[Get-Transaction](Get-Transaction.md)

[Undo-Transaction](Undo-Transaction.md)

[Use-Transaction](Use-Transaction.md)
