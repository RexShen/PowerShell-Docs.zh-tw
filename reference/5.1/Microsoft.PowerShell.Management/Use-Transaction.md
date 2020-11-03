---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/use-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Use-Transaction
ms.openlocfilehash: db8423aef6dc4b25c4ddd13f9b29b774463c6a6c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203464"
---
# Use-Transaction

## 概要
將指令碼區塊新增到使用中交易。

## SYNTAX

```
Use-Transaction [-TransactedScript] <ScriptBlock> [-UseTransaction] [<CommonParameters>]
```

## DESCRIPTION
**使用交易** Cmdlet 會將腳本區塊加入至使用中的交易。
這可讓您使用已啟用交易的 Microsoft .NET Framework 物件來執行交易式腳本處理。
此指令碼區塊只能包含支援交易的 .NET Framework 物件，例如 Microsoft.PowerShell.Commands.Management.TransactedString 類別的執行個體。

當您使用此 Cmdlet 時，需要 *UseTransaction* 參數，這對大部分的 Cmdlet 是選擇性的。

**使用-Transaction** 是支援 Windows PowerShell 中交易功能的其中一組 Cmdlet。
如需詳細資訊，請參閱 about_Transactions。

## 範例

### 範例1：使用啟用交易的物件編寫腳本

```
PS C:\> Start-Transaction
PS C:\> $transactedString = New-Object Microsoft.PowerShell.Commands.Management.TransactedString
PS C:\> $transactedString.Append("Hello")
PS C:\> Use-Transaction -TransactedScript { $transactedString.Append(", World") } -UseTransaction
PS C:\> $transactedString.ToString()
Hello
PS C:\> Use-Transaction -TransactedScript { $transactedString.ToString() } -UseTransaction
Hello, World
PS C:\> Complete-Transaction
PS C:\> $transactedString.ToString()
Hello, World
```

此範例示範如何針對已啟用交易的 .NET Framework 物件，使用 **使用-transaction** 編寫腳本。
在此情況下，物件是 **TransactedString** 物件。

第一個命令使用 Start-Transaction Cmdlet 來啟動交易。

第二個命令使用 New-Object 命令來建立 **TransactedString** 物件。
它將物件儲存在 $TransactedString 變數中。

第三個和第四個命令都使用 **TransactedString** 物件的 **Append** 方法將文字新增至 $TransactedString 的值。
其中一個命令是交易的一部分。
另一個命令則否。

第三個命令使用交易字串的 **Append** 方法，將 Hello 加入 $TransactedString 的值。
由於此命令不是交易的一部分，因此會立即套用變更。

第四個命令會使用 **使用-transaction** 將文字加入至交易中的字串。
此命令會使用 **Append** 方法將 "World" 新增至 $TransactedString 的值。
此命令會以大括弧括住 ( {} ) 使其成為腳本區塊。
此命令中必須要有 *UseTransaction* 參數。

第五個和第六個命令使用 **TransactedString** 物件的 **ToString** 方法，將 **TransactedString** 的值顯示為字串。
同樣地，其中一個命令是交易的一部分。
另一個交易則否。

第五個命令使用 **ToString** 方法來顯示 $TransactedString 變數的目前值。
由於它不是交易的一部分，因此它只會顯示字串的目前狀態。

第六個命令使用 **使用-transaction** 在交易中執行相同的命令。
因為此命令是交易的一部分，所以會在交易中顯示字串的目前值，非常類似交易變更的預覽。

第七個命令使用 Complete-Transaction Cmdlet 來確認交易。

最後一個命令會使用 **ToString** 方法將變數的產生值顯示為字串。

### 範例2：回復交易

```
PS C:\> Start-Transaction
PS C:\> $transactedString = New-Object Microsoft.PowerShell.Commands.Management.TransactedString
PS C:\> $transactedString.Append("Hello")
PS C:\> Use-Transaction -TransactedScript { $transactedString.Append(", World") } -UseTransaction
PS C:\> Undo-Transaction
PS C:\> $transactedString.ToString()
Hello
```

此範例顯示回復包含 **使用交易** 命令之交易的影響。
與交易中的所有命令相同，當交易被回復時，已交易的變更會被捨棄，而資料會保持不變。

第一個命令會使用 **啟動** 交易來啟動交易。

第二個命令使用 **New 物件** 來建立 **TransactedString** 物件。
它將物件儲存在 $TransactedString 變數中。

第三個命令（不屬於交易的一部分）使用 **Append** 方法將 "Hello" 新增至 $TransactedString 的值。

第四個命令會使用 **使用交易** 來執行另一個使用交易中 **附加** 方法的命令。
此命令會使用 **Append** 方法將 "World" 新增至 $TransactedString 的值。

第五個命令使用 Undo-Transaction Cmdlet 來回復交易。
因此，在交易中執行的所有命令都會反轉。

最後一個命令會使用 **ToString** 方法將 $TransactedString 的結果值顯示為字串。
結果顯示只有在交易外所做的變更會套用至物件。

## PARAMETERS

### -TransactedScript
指定在交易中執行的指令碼區塊。
請以大括弧 ( { } ) 括住的方式輸入任何有效的指令碼區塊。
這是必要參數。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseTransaction
將命令加入使用中交易。
只有交易為處理中狀態時，此參數才有效。
如需詳細資訊，請參閱 about_transactions。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

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

### PSObject
此 Cmdlet 會傳回交易的結果。

## 注意

* *UseTransaction* 參數包含使用中交易中的命令。 因為交易中一律會使用 **使用-transaction** Cmdlet，所以需要此參數才能讓任何 **使用交易** 命令生效。

*

## 相關連結

[Complete-Transaction](Complete-Transaction.md)

[Get-Transaction](Get-Transaction.md)

[Start-Transaction](Start-Transaction.md)

[Undo-Transaction](Undo-Transaction.md)
