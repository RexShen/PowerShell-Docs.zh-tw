---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/complete-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Complete-Transaction
ms.openlocfilehash: 20fbdd86aab07dda065492eff2da4f358fb2ffca
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204064"
---
# Complete-Transaction

## 概要
認可使用中交易。

## SYNTAX

```
Complete-Transaction [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
**完整交易** Cmdlet 會認可使用中交易。
當您確認交易時，交易中的命令會完成，且受命令影響的資料會變更。

如果交易包括多個訂閱者，若要認可交易，您必須針對每個 Start-Transaction 命令輸入一個 **完整交易** 命令。

**完整交易** Cmdlet 是支援 Windows PowerShell 中交易功能的其中一組 Cmdlet。
如需詳細資訊，請參閱 about_Transactions。

## 範例

### 範例1：認可交易

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item MyCompany -UseTransaction
PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}

PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}
0   0 MyCompany                      {}
```

此範例顯示當您使用 **完整交易** Cmdlet 來認可交易時，會發生什麼事。

**啟動交易** 命令會啟動交易。
New-Item 命令使用 *UseTransaction* 參數將命令包含在交易中。

第一個 dir (Get-childitem) 命令顯示新的專案尚未新增至登錄。

**完整交易** 命令會認可交易，讓登錄變更生效。
因此，第二個 dir 命令會顯示登錄已經變更。

### 範例2：認可具有一個以上訂閱者的交易

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item MyCompany -UseTransaction
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
0   0 MyCompany                      {}

PS HKCU:\software> Start-Transaction
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount  Status
------------------   ---------------  ------
Error                2                Active

PS HKCU:\software> New-ItemProperty -Path MyCompany -Name MyKey -Value -UseTransaction

MyKey
-----
123

PS HKCU:\software> Complete-Transaction
PS HKCU:\software> Get-Transaction

RollbackPreference   SubscriberCount  Status
------------------   ---------------  ------
Error                1                Active

PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}

PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}
0   1 MyCompany                      {MyKey}
```

這個範例會示範如何使用 **完整交易** 來認可具有多個訂閱者的交易。

若要認可多訂閱者交易，您必須針對每個 **啟動交易** 命令輸入一個 **完整交易** 命令。
只有在提交最後一個 **完整交易** 命令時，才會變更資料。

針對示範用途，此範例會顯示在命令列輸入的一系列命令。
實際上，交易很可能是以指令碼方式執行，次級交易則由主指令碼所呼叫的函式或協助程式指令碼執行。

在此範例中， **啟動交易** 命令會啟動交易。
具有 *UseTransaction* 參數的 **新專案** 命令會將 MyCompany 機碼新增至軟體金鑰。
雖然 **新專案** Cmdlet 會傳回金鑰組象，但是登錄中的資料尚未變更。

第二個 **啟動交易** 命令會將第二個訂閱者加入至現有的交易。
**取得交易** Cmdlet 會確認訂閱者計數為2。
具有 *UseTransaction* 參數的 New-ItemProperty 命令會將登錄專案新增至新的 MyCompany 機碼。
同樣地，命令會傳回值，但是登錄還不會變更。

第一個 **完整交易** 命令會將訂閱者計數減少1。
這是由 **取得交易** 命令確認。
但是，不會變更任何資料，如 dir m * ( **get-childitem** ) 命令所證明。

第二個 **完整交易** 命令會認可整個交易，並變更登錄中的資料。
這是由第二個 dir * 命令確認，它會顯示變更。

### 範例3：執行不會變更任何資料的交易

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item MyCompany -UseTransaction
PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}

PS HKCU:\software> dir m* -UseTransaction
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}
0   0 MyCompany                      {}

PS HKCU:\software> Complete-Transaction
```

此範例會顯示交易中使用 Get-\* 命令的值，以及其他不會變更資料的命令。
在交易中使用 Get-\* 命令時，它會取得屬於交易之一部分的物件。
這可以讓您在確認變更前先預覽交易中的變更。

在此範例中，交易已經啟動。
具有 *UseTransaction* 參數的 New-Item 命令會將新的金鑰新增至登錄，以作為交易的一部分。

由於新的登錄機碼不會新增至登錄，直到執行 **完整交易** 命令的情況下，簡單的 Dir ( **get-childitem** ) 命令會顯示不含新機碼的登錄。

但是，當您將 *UseTransaction* 參數新增至 dir 命令時，此命令會成為交易的一部分，而且即使尚未新增至資料，它也會取得交易中的專案。

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
您無法使用管線將物件傳送至此 Cmdlet。

## 輸出

### 無
此 Cmdlet 不會產生任何輸出。

## 注意

* 您無法回復已經確認的交易，或確認已經回復的交易。

  您無法回復使用中交易以外的任何交易。
若要回復其他交易，您必須先確認或回復使用中交易。

  依照預設，如果交易的任一部分無法確認 (例如當交易中的命令產生錯誤時)，就會回復整個交易。

*

## 相關連結

[Get-Transaction](Get-Transaction.md)

[Start-Transaction](Start-Transaction.md)

[Undo-Transaction](Undo-Transaction.md)

[Use-Transaction](Use-Transaction.md)

[Get-ChildItem](Get-ChildItem.md)

[New-Item](New-Item.md)

[New-ItemProperty](New-ItemProperty.md)
