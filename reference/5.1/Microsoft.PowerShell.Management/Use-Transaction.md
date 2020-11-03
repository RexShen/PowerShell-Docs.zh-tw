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
# <span data-ttu-id="e627e-103">Use-Transaction</span><span class="sxs-lookup"><span data-stu-id="e627e-103">Use-Transaction</span></span>

## <span data-ttu-id="e627e-104">概要</span><span class="sxs-lookup"><span data-stu-id="e627e-104">SYNOPSIS</span></span>
<span data-ttu-id="e627e-105">將指令碼區塊新增到使用中交易。</span><span class="sxs-lookup"><span data-stu-id="e627e-105">Adds the script block to the active transaction.</span></span>

## <span data-ttu-id="e627e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e627e-106">SYNTAX</span></span>

```
Use-Transaction [-TransactedScript] <ScriptBlock> [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="e627e-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e627e-107">DESCRIPTION</span></span>
<span data-ttu-id="e627e-108">**使用交易** Cmdlet 會將腳本區塊加入至使用中的交易。</span><span class="sxs-lookup"><span data-stu-id="e627e-108">The **Use-Transaction** cmdlet adds a script block to an active transaction.</span></span>
<span data-ttu-id="e627e-109">這可讓您使用已啟用交易的 Microsoft .NET Framework 物件來執行交易式腳本處理。</span><span class="sxs-lookup"><span data-stu-id="e627e-109">This enables you to do transacted scripting by using transaction-enabled Microsoft .NET Framework objects.</span></span>
<span data-ttu-id="e627e-110">此指令碼區塊只能包含支援交易的 .NET Framework 物件，例如 Microsoft.PowerShell.Commands.Management.TransactedString 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e627e-110">The script block can contain only transaction-enabled .NET Framework objects, such as instances of the Microsoft.PowerShell.Commands.Management.TransactedString class.</span></span>

<span data-ttu-id="e627e-111">當您使用此 Cmdlet 時，需要 *UseTransaction* 參數，這對大部分的 Cmdlet 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="e627e-111">The *UseTransaction* parameter, which is optional for most cmdlets, is required when you use this cmdlet.</span></span>

<span data-ttu-id="e627e-112">**使用-Transaction** 是支援 Windows PowerShell 中交易功能的其中一組 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e627e-112">**Use-Transaction** is one of a set of cmdlets that support the transactions feature in Windows PowerShell.</span></span>
<span data-ttu-id="e627e-113">如需詳細資訊，請參閱 about_Transactions。</span><span class="sxs-lookup"><span data-stu-id="e627e-113">For more information, see about_Transactions.</span></span>

## <span data-ttu-id="e627e-114">範例</span><span class="sxs-lookup"><span data-stu-id="e627e-114">EXAMPLES</span></span>

### <span data-ttu-id="e627e-115">範例1：使用啟用交易的物件編寫腳本</span><span class="sxs-lookup"><span data-stu-id="e627e-115">Example 1: Script by using a transaction-enabled object</span></span>

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

<span data-ttu-id="e627e-116">此範例示範如何針對已啟用交易的 .NET Framework 物件，使用 **使用-transaction** 編寫腳本。</span><span class="sxs-lookup"><span data-stu-id="e627e-116">This example shows how to use **Use-Transaction** to script against a transaction-enabled .NET Framework object.</span></span>
<span data-ttu-id="e627e-117">在此情況下，物件是 **TransactedString** 物件。</span><span class="sxs-lookup"><span data-stu-id="e627e-117">In this case, the object is a **TransactedString** object.</span></span>

<span data-ttu-id="e627e-118">第一個命令使用 Start-Transaction Cmdlet 來啟動交易。</span><span class="sxs-lookup"><span data-stu-id="e627e-118">The first command uses the Start-Transaction cmdlet to start a transaction.</span></span>

<span data-ttu-id="e627e-119">第二個命令使用 New-Object 命令來建立 **TransactedString** 物件。</span><span class="sxs-lookup"><span data-stu-id="e627e-119">The second command uses the New-Object command to create a **TransactedString** object.</span></span>
<span data-ttu-id="e627e-120">它將物件儲存在 $TransactedString 變數中。</span><span class="sxs-lookup"><span data-stu-id="e627e-120">It stores the object in the $TransactedString variable.</span></span>

<span data-ttu-id="e627e-121">第三個和第四個命令都使用 **TransactedString** 物件的 **Append** 方法將文字新增至 $TransactedString 的值。</span><span class="sxs-lookup"><span data-stu-id="e627e-121">The third and fourth commands both use the **Append** method of the **TransactedString** object to add text to the value of $TransactedString.</span></span>
<span data-ttu-id="e627e-122">其中一個命令是交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="e627e-122">One command is part of the transaction.</span></span>
<span data-ttu-id="e627e-123">另一個命令則否。</span><span class="sxs-lookup"><span data-stu-id="e627e-123">The other command is not.</span></span>

<span data-ttu-id="e627e-124">第三個命令使用交易字串的 **Append** 方法，將 Hello 加入 $TransactedString 的值。</span><span class="sxs-lookup"><span data-stu-id="e627e-124">The third command uses the **Append** method of the transacted string to add Hello to the value of $TransactedString.</span></span>
<span data-ttu-id="e627e-125">由於此命令不是交易的一部分，因此會立即套用變更。</span><span class="sxs-lookup"><span data-stu-id="e627e-125">Because the command is not part of the transaction, the change is applied immediately.</span></span>

<span data-ttu-id="e627e-126">第四個命令會使用 **使用-transaction** 將文字加入至交易中的字串。</span><span class="sxs-lookup"><span data-stu-id="e627e-126">The fourth command uses **Use-Transaction** to add text to the string in the transaction.</span></span>
<span data-ttu-id="e627e-127">此命令會使用 **Append** 方法將 "World" 新增至 $TransactedString 的值。</span><span class="sxs-lookup"><span data-stu-id="e627e-127">The command uses the **Append** method to add ", World" to the value of $TransactedString.</span></span>
<span data-ttu-id="e627e-128">此命令會以大括弧括住 ( {} ) 使其成為腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="e627e-128">The command is enclosed in braces ( {} ) to make it a script block.</span></span>
<span data-ttu-id="e627e-129">此命令中必須要有 *UseTransaction* 參數。</span><span class="sxs-lookup"><span data-stu-id="e627e-129">The *UseTransaction* parameter is required in this command.</span></span>

<span data-ttu-id="e627e-130">第五個和第六個命令使用 **TransactedString** 物件的 **ToString** 方法，將 **TransactedString** 的值顯示為字串。</span><span class="sxs-lookup"><span data-stu-id="e627e-130">The fifth and sixth commands use the **ToString** method of the **TransactedString** object to display the value of the **TransactedString** as a string.</span></span>
<span data-ttu-id="e627e-131">同樣地，其中一個命令是交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="e627e-131">Again, one command is part of the transaction.</span></span>
<span data-ttu-id="e627e-132">另一個交易則否。</span><span class="sxs-lookup"><span data-stu-id="e627e-132">The other transaction is not.</span></span>

<span data-ttu-id="e627e-133">第五個命令使用 **ToString** 方法來顯示 $TransactedString 變數的目前值。</span><span class="sxs-lookup"><span data-stu-id="e627e-133">The fifth command uses the **ToString** method to display the current value of the $TransactedString variable.</span></span>
<span data-ttu-id="e627e-134">由於它不是交易的一部分，因此它只會顯示字串的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="e627e-134">Because it is not part of the transaction, it displays only the current state of the string.</span></span>

<span data-ttu-id="e627e-135">第六個命令使用 **使用-transaction** 在交易中執行相同的命令。</span><span class="sxs-lookup"><span data-stu-id="e627e-135">The sixth command uses **Use-Transaction** to run the same command in the transaction.</span></span>
<span data-ttu-id="e627e-136">因為此命令是交易的一部分，所以會在交易中顯示字串的目前值，非常類似交易變更的預覽。</span><span class="sxs-lookup"><span data-stu-id="e627e-136">Because the command is part of the transaction, it displays the current value of the string in the transaction, much like a preview of the transaction changes.</span></span>

<span data-ttu-id="e627e-137">第七個命令使用 Complete-Transaction Cmdlet 來確認交易。</span><span class="sxs-lookup"><span data-stu-id="e627e-137">The seventh command uses the Complete-Transaction cmdlet to commit the transaction.</span></span>

<span data-ttu-id="e627e-138">最後一個命令會使用 **ToString** 方法將變數的產生值顯示為字串。</span><span class="sxs-lookup"><span data-stu-id="e627e-138">The final command uses the **ToString** method to display the resulting value of the variable as a string.</span></span>

### <span data-ttu-id="e627e-139">範例2：回復交易</span><span class="sxs-lookup"><span data-stu-id="e627e-139">Example 2: Roll back a transaction</span></span>

```
PS C:\> Start-Transaction
PS C:\> $transactedString = New-Object Microsoft.PowerShell.Commands.Management.TransactedString
PS C:\> $transactedString.Append("Hello")
PS C:\> Use-Transaction -TransactedScript { $transactedString.Append(", World") } -UseTransaction
PS C:\> Undo-Transaction
PS C:\> $transactedString.ToString()
Hello
```

<span data-ttu-id="e627e-140">此範例顯示回復包含 **使用交易** 命令之交易的影響。</span><span class="sxs-lookup"><span data-stu-id="e627e-140">This example shows the effect of rolling back a transaction that includes **Use-Transaction** commands.</span></span>
<span data-ttu-id="e627e-141">與交易中的所有命令相同，當交易被回復時，已交易的變更會被捨棄，而資料會保持不變。</span><span class="sxs-lookup"><span data-stu-id="e627e-141">Like all commands in a transaction, when the transaction is rolled back, the transacted changes are discarded and the data is unchanged.</span></span>

<span data-ttu-id="e627e-142">第一個命令會使用 **啟動** 交易來啟動交易。</span><span class="sxs-lookup"><span data-stu-id="e627e-142">The first command uses **Start-Transaction** to start a transaction.</span></span>

<span data-ttu-id="e627e-143">第二個命令使用 **New 物件** 來建立 **TransactedString** 物件。</span><span class="sxs-lookup"><span data-stu-id="e627e-143">The second command uses **New-Object** to create a **TransactedString** object.</span></span>
<span data-ttu-id="e627e-144">它將物件儲存在 $TransactedString 變數中。</span><span class="sxs-lookup"><span data-stu-id="e627e-144">It stores the object in the $TransactedString variable.</span></span>

<span data-ttu-id="e627e-145">第三個命令（不屬於交易的一部分）使用 **Append** 方法將 "Hello" 新增至 $TransactedString 的值。</span><span class="sxs-lookup"><span data-stu-id="e627e-145">The third command, which is not part of the transaction, uses the **Append** method to add "Hello" to the value of $TransactedString.</span></span>

<span data-ttu-id="e627e-146">第四個命令會使用 **使用交易** 來執行另一個使用交易中 **附加** 方法的命令。</span><span class="sxs-lookup"><span data-stu-id="e627e-146">The fourth command uses **Use-Transaction** to run another command that uses the **Append** method in the transaction.</span></span>
<span data-ttu-id="e627e-147">此命令會使用 **Append** 方法將 "World" 新增至 $TransactedString 的值。</span><span class="sxs-lookup"><span data-stu-id="e627e-147">The command uses the **Append** method to add ", World" to the value of $TransactedString.</span></span>

<span data-ttu-id="e627e-148">第五個命令使用 Undo-Transaction Cmdlet 來回復交易。</span><span class="sxs-lookup"><span data-stu-id="e627e-148">The fifth command uses the Undo-Transaction cmdlet to roll back the transaction.</span></span>
<span data-ttu-id="e627e-149">因此，在交易中執行的所有命令都會反轉。</span><span class="sxs-lookup"><span data-stu-id="e627e-149">As a result, all commands performed in the transaction are reversed.</span></span>

<span data-ttu-id="e627e-150">最後一個命令會使用 **ToString** 方法將 $TransactedString 的結果值顯示為字串。</span><span class="sxs-lookup"><span data-stu-id="e627e-150">The final command uses the **ToString** method to display the resulting value of $TransactedString as a string.</span></span>
<span data-ttu-id="e627e-151">結果顯示只有在交易外所做的變更會套用至物件。</span><span class="sxs-lookup"><span data-stu-id="e627e-151">The results show that only the changes that were made outside the transaction were applied to the object.</span></span>

## <span data-ttu-id="e627e-152">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e627e-152">PARAMETERS</span></span>

### <span data-ttu-id="e627e-153">-TransactedScript</span><span class="sxs-lookup"><span data-stu-id="e627e-153">-TransactedScript</span></span>
<span data-ttu-id="e627e-154">指定在交易中執行的指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="e627e-154">Specifies the script block that is run in the transaction.</span></span>
<span data-ttu-id="e627e-155">請以大括弧 ( { } ) 括住的方式輸入任何有效的指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="e627e-155">Enter any valid script block enclosed in braces ( { } ).</span></span>
<span data-ttu-id="e627e-156">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="e627e-156">This parameter is required.</span></span>

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

### <span data-ttu-id="e627e-157">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="e627e-157">-UseTransaction</span></span>
<span data-ttu-id="e627e-158">將命令加入使用中交易。</span><span class="sxs-lookup"><span data-stu-id="e627e-158">Includes the command in the active transaction.</span></span>
<span data-ttu-id="e627e-159">只有交易為處理中狀態時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="e627e-159">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="e627e-160">如需詳細資訊，請參閱 about_transactions。</span><span class="sxs-lookup"><span data-stu-id="e627e-160">For more information, see about_transactions.</span></span>

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

### <span data-ttu-id="e627e-161">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e627e-161">CommonParameters</span></span>
<span data-ttu-id="e627e-162">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="e627e-162">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e627e-163">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="e627e-163">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e627e-164">輸入</span><span class="sxs-lookup"><span data-stu-id="e627e-164">INPUTS</span></span>

### <span data-ttu-id="e627e-165">無</span><span class="sxs-lookup"><span data-stu-id="e627e-165">None</span></span>
<span data-ttu-id="e627e-166">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e627e-166">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="e627e-167">輸出</span><span class="sxs-lookup"><span data-stu-id="e627e-167">OUTPUTS</span></span>

### <span data-ttu-id="e627e-168">PSObject</span><span class="sxs-lookup"><span data-stu-id="e627e-168">PSObject</span></span>
<span data-ttu-id="e627e-169">此 Cmdlet 會傳回交易的結果。</span><span class="sxs-lookup"><span data-stu-id="e627e-169">This cmdlet returns the result of the transaction.</span></span>

## <span data-ttu-id="e627e-170">注意</span><span class="sxs-lookup"><span data-stu-id="e627e-170">NOTES</span></span>

* <span data-ttu-id="e627e-171">*UseTransaction* 參數包含使用中交易中的命令。</span><span class="sxs-lookup"><span data-stu-id="e627e-171">The *UseTransaction* parameter includes the command in the active transaction.</span></span> <span data-ttu-id="e627e-172">因為交易中一律會使用 **使用-transaction** Cmdlet，所以需要此參數才能讓任何 **使用交易** 命令生效。</span><span class="sxs-lookup"><span data-stu-id="e627e-172">Because the **Use-Transaction** cmdlet is always used in transactions, this parameter is required to make any **Use-Transaction** command effective.</span></span>

*

## <span data-ttu-id="e627e-173">相關連結</span><span class="sxs-lookup"><span data-stu-id="e627e-173">RELATED LINKS</span></span>

[<span data-ttu-id="e627e-174">Complete-Transaction</span><span class="sxs-lookup"><span data-stu-id="e627e-174">Complete-Transaction</span></span>](Complete-Transaction.md)

[<span data-ttu-id="e627e-175">Get-Transaction</span><span class="sxs-lookup"><span data-stu-id="e627e-175">Get-Transaction</span></span>](Get-Transaction.md)

[<span data-ttu-id="e627e-176">Start-Transaction</span><span class="sxs-lookup"><span data-stu-id="e627e-176">Start-Transaction</span></span>](Start-Transaction.md)

[<span data-ttu-id="e627e-177">Undo-Transaction</span><span class="sxs-lookup"><span data-stu-id="e627e-177">Undo-Transaction</span></span>](Undo-Transaction.md)
