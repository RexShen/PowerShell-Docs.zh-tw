---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Transaction
ms.openlocfilehash: bb8e9e1f204c67207f31613181f856d3bcaf8dc3
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "93196686"
---
# Get-Transaction

## 概要
取得目前的 (使用中) 交易。

## SYNTAX

```
Get-Transaction [<CommonParameters>]
```

## DESCRIPTION
**取得交易** Cmdlet 會取得物件，該物件代表會話中的目前交易。

此 Cmdlet 永遠不會傳回多個物件，因為一次只有一筆交易在作用中。
如果您使用啟動交易) 的獨立參數來啟動一或多個獨立的交易 (，最近啟動的交易就會是使用中的交易，而這就 **是交易傳回** 的交易。

當所有使用中交易都已回復或認可時，此 Cmdlet 會顯示會話中最近使用中的交易。

此 Cmdlet 是支援 Windows PowerShell 中交易功能的其中一組 Cmdlet。
如需詳細資訊，請參閱 about_Transactions。

## 範例

### 範例1：取得目前的交易

```
PS C:\> Start-Transaction
PS C:\> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

此命令使用 Get-Transaction Cmdlet 取得目前交易。

### 範例2：顯示交易對象的屬性和方法

```
PS C:\> Get-Transaction | Get-Member

Name               MemberType Definition
----               ---------- ----------
Dispose            Method     System.Void Dispose(), System.Void Dispose(Boolean disposing)
Equals             Method     System.Boolean Equals(Object obj)
GetHashCode        Method     System.Int32 GetHashCode()
GetType            Method     System.Type GetType()
ToString           Method     System.String ToString()
IsCommitted        Property   System.Boolean IsCommitted {get;}
IsRolledBack       Property   System.Boolean IsRolledBack {get;}
RollbackPreference Property   System.Management.Automation.RollbackSeverity RollbackPreference {get;}
SubscriberCount    Property   System.Int32 SubscriberCount {get;set;}
```

此命令使用 Get-Member Cmdlet 顯示交易物件的屬性和方法。

### 範例3：顯示已回復交易的屬性值

```
PS C:\> cd hklm:\software
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> New-Item MyCompany -UseTransaction
HKLM:\SOFTWARE> Undo-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ----------
Error                0                 RolledBack
```

此命令顯示已回復的交易之交易物件的屬性值。

### 範例4：顯示已認可交易的屬性值

```
PS C:\> cd hklm:\software
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> New-Item MyCompany -UseTransaction
HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ---------
Error                1                 Committed
```

此命令顯示已確認的交易之交易物件的屬性值。

### 範例5：在另一個進行中時啟動交易

```
PS C:\> cd hklm:\software
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> New-Item MyCompany -UseTransaction
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> New-Item MyCompany2 -UseTransaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                2                 Active

HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active

HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ---------
Error                1                 Committed
```

此範例顯示當有另一個交易正在進行時，啟動交易的交易物件效果。
通常這種情況會在指令碼執行的交易包含函式或呼叫包含另一個完整交易的指令碼時發生。

除非第二個 **啟動交易** 命令包含 *獨立* 的參數，否則 **啟動交易** 不會建立新的交易。
而是將第二個訂閱者加入至原始的交易。

第一個 **啟動交易** 命令會啟動交易。
具有 *UseTransaction* 參數的 New-Item 命令是交易的一部分。

第二個 **啟動交易** 命令會將訂閱者加入至交易。
下一個 New-Item 命令也是交易的一部分。

第一個 **Get transaction** 命令會顯示多訂閱者交易。
請注意，訂閱者計數是 2。

第一個 Complete-Transaction 命令不會確認交易，但它會將訂閱者計數減少至 1。

第二個 **完整交易** 命令認可交易。

### 範例6：當另一個交易正在進行時啟動獨立交易

```
PS C:\>
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   IsRolledBack   IsCommitted
------------------   ---------------   ------------   -----------
Error                1                 False          False

HKLM:\SOFTWARE> Start-Transaction -Independent
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   IsRolledBack   IsCommitted
------------------   ---------------   ------------   -----------
Error                1                 False          False

HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction
HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction
```

此範例顯示當有另一個獨立交易正在進行時，啟動交易的交易物件效果。

第一個 **啟動交易** 命令會啟動交易。
具有 *UseTransaction* 參數的 **新專案** 命令是交易的一部分。

第二個 **啟動交易** 命令會將訂閱者加入至交易。
下一個 **新專案** 命令也是交易的一部分。

第一個 **Get transaction** 命令會顯示多訂閱者交易。
請注意，訂閱者計數是 2。

**完整交易** 命令會將訂閱者計數減少至1，但不會認可交易。

第二個 **完整交易** 命令認可交易。

## PARAMETERS

### CommonParameters
這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無
您無法使用管線將物件傳送至此 Cmdlet。

## 輸出

### System.Management.Automation.PSTransaction
這個 Cmdlet 會傳回代表目前交易的物件。

## 注意

## 相關連結

[Complete-Transaction](Complete-Transaction.md)

[Start-Transaction](Start-Transaction.md)

[Undo-Transaction](Undo-Transaction.md)

[Use-Transaction](Use-Transaction.md)

[New-Item](New-Item.md)
