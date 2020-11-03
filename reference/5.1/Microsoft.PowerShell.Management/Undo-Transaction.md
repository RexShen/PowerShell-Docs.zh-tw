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
# <span data-ttu-id="0c21b-103">Undo-Transaction</span><span class="sxs-lookup"><span data-stu-id="0c21b-103">Undo-Transaction</span></span>

## <span data-ttu-id="0c21b-104">概要</span><span class="sxs-lookup"><span data-stu-id="0c21b-104">SYNOPSIS</span></span>
<span data-ttu-id="0c21b-105">將使用中交易回復。</span><span class="sxs-lookup"><span data-stu-id="0c21b-105">Rolls back the active transaction.</span></span>

## <span data-ttu-id="0c21b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0c21b-106">SYNTAX</span></span>

```
Undo-Transaction [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="0c21b-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0c21b-107">DESCRIPTION</span></span>
<span data-ttu-id="0c21b-108">**復原交易** Cmdlet 會回復使用中交易。</span><span class="sxs-lookup"><span data-stu-id="0c21b-108">The **Undo-Transaction** cmdlet rolls back the active transaction.</span></span>
<span data-ttu-id="0c21b-109">當您回復交易時，會捨棄交易中命令所做的變更，並將資料還原為其原始格式。</span><span class="sxs-lookup"><span data-stu-id="0c21b-109">When you roll back a transaction, the changes that were made by the commands in the transaction are discarded and the data is restored to its original form.</span></span>

<span data-ttu-id="0c21b-110">如果交易包含多個訂閱者，則 **Undo 交易** 命令會回復所有訂閱者的整個交易。</span><span class="sxs-lookup"><span data-stu-id="0c21b-110">If the transaction includes multiple subscribers, an **Undo-Transaction** command rolls back the whole transaction for all subscribers.</span></span>

<span data-ttu-id="0c21b-111">根據預設，如果交易中的任何命令產生錯誤，就會自動將交易回復。</span><span class="sxs-lookup"><span data-stu-id="0c21b-111">By default, transactions are rolled back automatically if any command in the transaction generates an error.</span></span>
<span data-ttu-id="0c21b-112">不過，您可以使用不同的回復喜好設定來啟動交易，並且可以使用這個 Cmdlet 隨時復原使用中的交易。</span><span class="sxs-lookup"><span data-stu-id="0c21b-112">However, transactions can be started by using a different rollback preference and you can use this cmdlet to roll back the active transaction at any time.</span></span>

<span data-ttu-id="0c21b-113">**復原交易** Cmdlet 是支援 Windows PowerShell 中交易功能的其中一組 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0c21b-113">The **Undo-Transaction** cmdlet is one of a set of cmdlets that support the transactions feature in Windows PowerShell.</span></span>
<span data-ttu-id="0c21b-114">如需詳細資訊，請參閱 about_Transactions。</span><span class="sxs-lookup"><span data-stu-id="0c21b-114">For more information, see about_Transactions.</span></span>

## <span data-ttu-id="0c21b-115">範例</span><span class="sxs-lookup"><span data-stu-id="0c21b-115">EXAMPLES</span></span>

### <span data-ttu-id="0c21b-116">範例1：復原目前的交易</span><span class="sxs-lookup"><span data-stu-id="0c21b-116">Example 1: Roll back the current transaction</span></span>

```
PS C:\> Undo-Transaction
```

<span data-ttu-id="0c21b-117">此命令會回復目前的主動式交易。</span><span class="sxs-lookup"><span data-stu-id="0c21b-117">This command rolls back the current, active, transaction.</span></span>

### <span data-ttu-id="0c21b-118">範例2：啟動和回復交易</span><span class="sxs-lookup"><span data-stu-id="0c21b-118">Example 2: Start and roll back a transaction</span></span>

```
PS C:\> cd hkcu:\software
PS HKCU:\Software> Start-Transaction
PS HKCU:\Software> New-Item -Path "ContosoCompany" -UseTransaction
PS HKCU:\Software> Undo-Transaction
```

<span data-ttu-id="0c21b-119">此範例會啟動交易，然後將其回復。</span><span class="sxs-lookup"><span data-stu-id="0c21b-119">This example starts a transaction and then rolls it back.</span></span>
<span data-ttu-id="0c21b-120">因此，也就不會對登錄進行任何變更。</span><span class="sxs-lookup"><span data-stu-id="0c21b-120">As a result, no changes are made to the registry.</span></span>

### <span data-ttu-id="0c21b-121">範例3：為所有訂閱者回復交易</span><span class="sxs-lookup"><span data-stu-id="0c21b-121">Example 3: Roll back a transaction for all subscribers</span></span>

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

<span data-ttu-id="0c21b-122">這個範例示範當任何訂閱者回復交易時，都會針對所有訂閱者回復整個交易。</span><span class="sxs-lookup"><span data-stu-id="0c21b-122">This example demonstrates that when any subscriber rolls back a transaction, the whole transaction is rolled back for all subscribers.</span></span>

<span data-ttu-id="0c21b-123">第一個命令將位置變更為 HKCU:\Software 登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="0c21b-123">The first command changes the location to the HKCU:\Software registry key.</span></span>

<span data-ttu-id="0c21b-124">第二個命令啟動交易。</span><span class="sxs-lookup"><span data-stu-id="0c21b-124">The second command starts a transaction.</span></span>

<span data-ttu-id="0c21b-125">第三個命令使用 New-Item Cmdlet 來建立新的登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="0c21b-125">The third command uses the New-Item cmdlet to create a new registry key.</span></span>
<span data-ttu-id="0c21b-126">此命令會使用 *UseTransaction* 參數將變更包含在交易中。</span><span class="sxs-lookup"><span data-stu-id="0c21b-126">The command uses the *UseTransaction* parameter to include the change in the transaction.</span></span>

<span data-ttu-id="0c21b-127">第四個命令使用 Get-Transaction Cmdlet 來取得使用中交易。</span><span class="sxs-lookup"><span data-stu-id="0c21b-127">The fourth command uses the Get-Transaction cmdlet to get the active transaction.</span></span>
<span data-ttu-id="0c21b-128">請注意，狀態是 Active，而訂閱者計數為 1。</span><span class="sxs-lookup"><span data-stu-id="0c21b-128">Notice that the status is Active and the subscriber count is 1.</span></span>

<span data-ttu-id="0c21b-129">第五個命令再次使用 Start-Transaction 命令。</span><span class="sxs-lookup"><span data-stu-id="0c21b-129">The fifth command uses the Start-Transaction command again.</span></span>
<span data-ttu-id="0c21b-130">一般來說，當主要交易使用的腳本包含它自己的完整交易時，當另一個交易正在進行時，就會啟動交易。</span><span class="sxs-lookup"><span data-stu-id="0c21b-130">Typically, starting a transaction while another transaction is in progress occurs when a script that is used by the main transaction includes its own complete transaction.</span></span>
<span data-ttu-id="0c21b-131">此範例會以互動方式執行，讓您可以分階段進行檢查。</span><span class="sxs-lookup"><span data-stu-id="0c21b-131">This example is performed interactively so that you can examine it in stages.</span></span>
<span data-ttu-id="0c21b-132">當您在另一個交易正在進行時執行 **啟動交易** 命令時，這些命令會將現有的交易加入成為新的訂閱者，而訂閱者計數會遞增。</span><span class="sxs-lookup"><span data-stu-id="0c21b-132">When you run a **Start-Transaction** command while another transaction is in progress, the commands join the existing transaction as a new subscriber and the subscriber count is incremented.</span></span>

<span data-ttu-id="0c21b-133">第六個命令會使用 **取得交易** Cmdlet 來取得使用中的交易。</span><span class="sxs-lookup"><span data-stu-id="0c21b-133">The sixth command uses the **Get-Transaction** cmdlet to get the active transaction.</span></span>
<span data-ttu-id="0c21b-134">請注意，訂閱者計數現在是 2。</span><span class="sxs-lookup"><span data-stu-id="0c21b-134">Notice that the subscriber count is now 2.</span></span>

<span data-ttu-id="0c21b-135">第七個命令使用 **恢復交易來復原** 交易。</span><span class="sxs-lookup"><span data-stu-id="0c21b-135">The seventh command uses **Undo-Transaction** to roll back the transaction.</span></span>
<span data-ttu-id="0c21b-136">此命令不會傳回任何物件。</span><span class="sxs-lookup"><span data-stu-id="0c21b-136">This command does not return any objects.</span></span>

<span data-ttu-id="0c21b-137">最後一個命令是取得使用中（或在此案例中為最近使用中交易）的 **取得交易** 命令。</span><span class="sxs-lookup"><span data-stu-id="0c21b-137">The final command is a **Get-Transaction** command that gets the active, or in this case, the most recently active, transaction.</span></span>
<span data-ttu-id="0c21b-138">結果會顯示交易被回復，而且訂閱者計數為 0，表示已針對所有訂閱者回復交易。</span><span class="sxs-lookup"><span data-stu-id="0c21b-138">The results show that the transaction is rolled back, and that the subscriber count is 0, showing that the transaction was rolled back for all subscribers.</span></span>

## <span data-ttu-id="0c21b-139">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0c21b-139">PARAMETERS</span></span>

### <span data-ttu-id="0c21b-140">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0c21b-140">-Confirm</span></span>
<span data-ttu-id="0c21b-141">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="0c21b-141">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="0c21b-142">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0c21b-142">-WhatIf</span></span>
<span data-ttu-id="0c21b-143">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="0c21b-143">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="0c21b-144">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="0c21b-144">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="0c21b-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0c21b-145">CommonParameters</span></span>
<span data-ttu-id="0c21b-146">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="0c21b-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0c21b-147">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="0c21b-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0c21b-148">輸入</span><span class="sxs-lookup"><span data-stu-id="0c21b-148">INPUTS</span></span>

### <span data-ttu-id="0c21b-149">無</span><span class="sxs-lookup"><span data-stu-id="0c21b-149">None</span></span>
<span data-ttu-id="0c21b-150">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0c21b-150">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="0c21b-151">輸出</span><span class="sxs-lookup"><span data-stu-id="0c21b-151">OUTPUTS</span></span>

### <span data-ttu-id="0c21b-152">無</span><span class="sxs-lookup"><span data-stu-id="0c21b-152">None</span></span>
<span data-ttu-id="0c21b-153">此 Cmdlet 不會傳回任何輸出。</span><span class="sxs-lookup"><span data-stu-id="0c21b-153">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="0c21b-154">注意</span><span class="sxs-lookup"><span data-stu-id="0c21b-154">NOTES</span></span>

* <span data-ttu-id="0c21b-155">您無法回復已確認的交易。</span><span class="sxs-lookup"><span data-stu-id="0c21b-155">You cannot roll back a transaction that has been committed.</span></span>

  <span data-ttu-id="0c21b-156">您無法回復使用中交易以外的任何交易。</span><span class="sxs-lookup"><span data-stu-id="0c21b-156">You cannot roll back any transaction other than the active transaction.</span></span>
<span data-ttu-id="0c21b-157">若要回復不同的獨立交易，您必須先確認或回復使用中交易。</span><span class="sxs-lookup"><span data-stu-id="0c21b-157">To roll back a different, independent transaction, you must first commit or roll back the active transaction.</span></span>

  <span data-ttu-id="0c21b-158">回復交易會將交易結束。</span><span class="sxs-lookup"><span data-stu-id="0c21b-158">Rolling back the transaction ends the transaction.</span></span>
<span data-ttu-id="0c21b-159">若要再次使用某個交易，您必須啟動新的交易。</span><span class="sxs-lookup"><span data-stu-id="0c21b-159">To use a transaction again, you must start a new transaction.</span></span>

## <span data-ttu-id="0c21b-160">相關連結</span><span class="sxs-lookup"><span data-stu-id="0c21b-160">RELATED LINKS</span></span>

[<span data-ttu-id="0c21b-161">Complete-Transaction</span><span class="sxs-lookup"><span data-stu-id="0c21b-161">Complete-Transaction</span></span>](Complete-Transaction.md)

[<span data-ttu-id="0c21b-162">Get-Transaction</span><span class="sxs-lookup"><span data-stu-id="0c21b-162">Get-Transaction</span></span>](Get-Transaction.md)

[<span data-ttu-id="0c21b-163">Start-Transaction</span><span class="sxs-lookup"><span data-stu-id="0c21b-163">Start-Transaction</span></span>](Start-Transaction.md)

[<span data-ttu-id="0c21b-164">Use-Transaction</span><span class="sxs-lookup"><span data-stu-id="0c21b-164">Use-Transaction</span></span>](Use-Transaction.md)
