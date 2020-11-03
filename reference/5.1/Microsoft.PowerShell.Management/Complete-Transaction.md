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
# <span data-ttu-id="9bbe2-103">Complete-Transaction</span><span class="sxs-lookup"><span data-stu-id="9bbe2-103">Complete-Transaction</span></span>

## <span data-ttu-id="9bbe2-104">概要</span><span class="sxs-lookup"><span data-stu-id="9bbe2-104">SYNOPSIS</span></span>
<span data-ttu-id="9bbe2-105">認可使用中交易。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-105">Commits the active transaction.</span></span>

## <span data-ttu-id="9bbe2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9bbe2-106">SYNTAX</span></span>

```
Complete-Transaction [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="9bbe2-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9bbe2-107">DESCRIPTION</span></span>
<span data-ttu-id="9bbe2-108">**完整交易** Cmdlet 會認可使用中交易。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-108">The **Complete-Transaction** cmdlet commits an active transaction.</span></span>
<span data-ttu-id="9bbe2-109">當您確認交易時，交易中的命令會完成，且受命令影響的資料會變更。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-109">When you commit a transaction, the commands in the transaction are finalized and the data affected by the commands is changed.</span></span>

<span data-ttu-id="9bbe2-110">如果交易包括多個訂閱者，若要認可交易，您必須針對每個 Start-Transaction 命令輸入一個 **完整交易** 命令。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-110">If the transaction includes multiple subscribers, to commit the transaction, you must enter one **Complete-Transaction** command for every Start-Transaction command.</span></span>

<span data-ttu-id="9bbe2-111">**完整交易** Cmdlet 是支援 Windows PowerShell 中交易功能的其中一組 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-111">The **Complete-Transaction** cmdlet is one of a set of cmdlets that support the transactions feature in Windows PowerShell.</span></span>
<span data-ttu-id="9bbe2-112">如需詳細資訊，請參閱 about_Transactions。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-112">For more information, see about_Transactions.</span></span>

## <span data-ttu-id="9bbe2-113">範例</span><span class="sxs-lookup"><span data-stu-id="9bbe2-113">EXAMPLES</span></span>

### <span data-ttu-id="9bbe2-114">範例1：認可交易</span><span class="sxs-lookup"><span data-stu-id="9bbe2-114">Example 1: Commit a transaction</span></span>

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

<span data-ttu-id="9bbe2-115">此範例顯示當您使用 **完整交易** Cmdlet 來認可交易時，會發生什麼事。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-115">This example shows what happens when you use the **Complete-Transaction** cmdlet to commit a transaction.</span></span>

<span data-ttu-id="9bbe2-116">**啟動交易** 命令會啟動交易。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-116">The **Start-Transaction** command starts the transaction.</span></span>
<span data-ttu-id="9bbe2-117">New-Item 命令使用 *UseTransaction* 參數將命令包含在交易中。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-117">The New-Item command uses the *UseTransaction* parameter to include the command in the transaction.</span></span>

<span data-ttu-id="9bbe2-118">第一個 dir (Get-childitem) 命令顯示新的專案尚未新增至登錄。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-118">The first dir (Get-ChildItem) command shows that the new item has not yet been added to the registry.</span></span>

<span data-ttu-id="9bbe2-119">**完整交易** 命令會認可交易，讓登錄變更生效。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-119">The **Complete-Transaction** command commits the transaction, which makes the registry change effective.</span></span>
<span data-ttu-id="9bbe2-120">因此，第二個 dir 命令會顯示登錄已經變更。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-120">As a result, the second dir command shows that the registry is changed.</span></span>

### <span data-ttu-id="9bbe2-121">範例2：認可具有一個以上訂閱者的交易</span><span class="sxs-lookup"><span data-stu-id="9bbe2-121">Example 2: Commit a transaction that has more than one subscriber</span></span>

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

<span data-ttu-id="9bbe2-122">這個範例會示範如何使用 **完整交易** 來認可具有多個訂閱者的交易。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-122">This example shows how to use **Complete-Transaction** to commit a transaction that has more than one subscriber.</span></span>

<span data-ttu-id="9bbe2-123">若要認可多訂閱者交易，您必須針對每個 **啟動交易** 命令輸入一個 **完整交易** 命令。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-123">To commit a multi-subscriber transaction, you must enter one **Complete-Transaction** command for every **Start-Transaction** command.</span></span>
<span data-ttu-id="9bbe2-124">只有在提交最後一個 **完整交易** 命令時，才會變更資料。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-124">The data is changed only when the final **Complete-Transaction** command is submitted.</span></span>

<span data-ttu-id="9bbe2-125">針對示範用途，此範例會顯示在命令列輸入的一系列命令。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-125">For demonstration purposes, this example shows a series of commands entered at the command line.</span></span>
<span data-ttu-id="9bbe2-126">實際上，交易很可能是以指令碼方式執行，次級交易則由主指令碼所呼叫的函式或協助程式指令碼執行。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-126">In practice, transactions are likely to be run in scripts, with the secondary transaction being run by a function or helper script that is called by the main script.</span></span>

<span data-ttu-id="9bbe2-127">在此範例中， **啟動交易** 命令會啟動交易。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-127">In this example, a **Start-Transaction** command starts the transaction.</span></span>
<span data-ttu-id="9bbe2-128">具有 *UseTransaction* 參數的 **新專案** 命令會將 MyCompany 機碼新增至軟體金鑰。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-128">A **New-Item** command with the *UseTransaction* parameter adds the MyCompany key to the Software key.</span></span>
<span data-ttu-id="9bbe2-129">雖然 **新專案** Cmdlet 會傳回金鑰組象，但是登錄中的資料尚未變更。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-129">Although the **New-Item** cmdlet returns a key object, the data in the registry is not yet changed.</span></span>

<span data-ttu-id="9bbe2-130">第二個 **啟動交易** 命令會將第二個訂閱者加入至現有的交易。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-130">A second **Start-Transaction** command adds a second subscriber to the existing transaction.</span></span>
<span data-ttu-id="9bbe2-131">**取得交易** Cmdlet 會確認訂閱者計數為2。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-131">The **Get-Transaction** cmdlet confirms that the subscriber count is 2.</span></span>
<span data-ttu-id="9bbe2-132">具有 *UseTransaction* 參數的 New-ItemProperty 命令會將登錄專案新增至新的 MyCompany 機碼。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-132">A New-ItemProperty command with the *UseTransaction* parameter adds a registry entry to the new MyCompany key.</span></span>
<span data-ttu-id="9bbe2-133">同樣地，命令會傳回值，但是登錄還不會變更。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-133">Again, the command returns a value, but the registry is not changed.</span></span>

<span data-ttu-id="9bbe2-134">第一個 **完整交易** 命令會將訂閱者計數減少1。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-134">The first **Complete-Transaction** command reduces the subscriber count by 1.</span></span>
<span data-ttu-id="9bbe2-135">這是由 **取得交易** 命令確認。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-135">This is confirmed by a **Get-Transaction** command.</span></span>
<span data-ttu-id="9bbe2-136">但是，不會變更任何資料，如 dir m \* ( **get-childitem** ) 命令所證明。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-136">However, no data is changed, as evidenced by a dir m\* ( **Get-ChildItem** ) command.</span></span>

<span data-ttu-id="9bbe2-137">第二個 **完整交易** 命令會認可整個交易，並變更登錄中的資料。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-137">The second **Complete-Transaction** command commits the entire transaction and changes the data in the registry.</span></span>
<span data-ttu-id="9bbe2-138">這是由第二個 dir \* 命令確認，它會顯示變更。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-138">This is confirmed by a second dir m\* command, which shows the changes.</span></span>

### <span data-ttu-id="9bbe2-139">範例3：執行不會變更任何資料的交易</span><span class="sxs-lookup"><span data-stu-id="9bbe2-139">Example 3: Perform a transaction that does not change any data</span></span>

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

<span data-ttu-id="9bbe2-140">此範例會顯示交易中使用 Get-\* 命令的值，以及其他不會變更資料的命令。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-140">This example shows the value of using Get-\* commands, and other commands that do not change data, in a transaction.</span></span>
<span data-ttu-id="9bbe2-141">在交易中使用 Get-\* 命令時，它會取得屬於交易之一部分的物件。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-141">When a Get-\* command is used in a transaction, it gets the objects that are part of the transaction.</span></span>
<span data-ttu-id="9bbe2-142">這可以讓您在確認變更前先預覽交易中的變更。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-142">This allows you to preview the changes in the transaction before the changes are committed.</span></span>

<span data-ttu-id="9bbe2-143">在此範例中，交易已經啟動。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-143">In this example, a transaction is started.</span></span>
<span data-ttu-id="9bbe2-144">具有 *UseTransaction* 參數的 New-Item 命令會將新的金鑰新增至登錄，以作為交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-144">A New-Item command with the *UseTransaction* parameter adds a new key to the registry as part of the transaction.</span></span>

<span data-ttu-id="9bbe2-145">由於新的登錄機碼不會新增至登錄，直到執行 **完整交易** 命令的情況下，簡單的 Dir ( **get-childitem** ) 命令會顯示不含新機碼的登錄。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-145">Because the new registry key is not added to the registry until the **Complete-Transaction** command is run, a simple dir ( **Get-ChildItem** ) command shows the registry without the new key.</span></span>

<span data-ttu-id="9bbe2-146">但是，當您將 *UseTransaction* 參數新增至 dir 命令時，此命令會成為交易的一部分，而且即使尚未新增至資料，它也會取得交易中的專案。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-146">However, when you add the *UseTransaction* parameter to the dir command, the command becomes part of the transaction, and it gets the items in the transaction even if they are not yet added to the data.</span></span>

## <span data-ttu-id="9bbe2-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9bbe2-147">PARAMETERS</span></span>

### <span data-ttu-id="9bbe2-148">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9bbe2-148">-Confirm</span></span>
<span data-ttu-id="9bbe2-149">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-149">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="9bbe2-150">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9bbe2-150">-WhatIf</span></span>
<span data-ttu-id="9bbe2-151">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-151">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="9bbe2-152">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-152">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="9bbe2-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9bbe2-153">CommonParameters</span></span>
<span data-ttu-id="9bbe2-154">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9bbe2-155">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9bbe2-156">輸入</span><span class="sxs-lookup"><span data-stu-id="9bbe2-156">INPUTS</span></span>

### <span data-ttu-id="9bbe2-157">無</span><span class="sxs-lookup"><span data-stu-id="9bbe2-157">None</span></span>
<span data-ttu-id="9bbe2-158">您無法使用管線將物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-158">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="9bbe2-159">輸出</span><span class="sxs-lookup"><span data-stu-id="9bbe2-159">OUTPUTS</span></span>

### <span data-ttu-id="9bbe2-160">無</span><span class="sxs-lookup"><span data-stu-id="9bbe2-160">None</span></span>
<span data-ttu-id="9bbe2-161">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-161">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="9bbe2-162">注意</span><span class="sxs-lookup"><span data-stu-id="9bbe2-162">NOTES</span></span>

* <span data-ttu-id="9bbe2-163">您無法回復已經確認的交易，或確認已經回復的交易。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-163">You cannot roll back a transaction that has been committed, or commit a transaction that has been rolled back.</span></span>

  <span data-ttu-id="9bbe2-164">您無法回復使用中交易以外的任何交易。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-164">You cannot roll back any transaction other than the active transaction.</span></span>
<span data-ttu-id="9bbe2-165">若要回復其他交易，您必須先確認或回復使用中交易。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-165">To roll back a different transaction, you must first commit or roll back the active transaction.</span></span>

  <span data-ttu-id="9bbe2-166">依照預設，如果交易的任一部分無法確認 (例如當交易中的命令產生錯誤時)，就會回復整個交易。</span><span class="sxs-lookup"><span data-stu-id="9bbe2-166">By default, if any part of a transaction cannot be committed, such as when a command in the transaction results in an error, the entire transaction is rolled back.</span></span>

*

## <span data-ttu-id="9bbe2-167">相關連結</span><span class="sxs-lookup"><span data-stu-id="9bbe2-167">RELATED LINKS</span></span>

[<span data-ttu-id="9bbe2-168">Get-Transaction</span><span class="sxs-lookup"><span data-stu-id="9bbe2-168">Get-Transaction</span></span>](Get-Transaction.md)

[<span data-ttu-id="9bbe2-169">Start-Transaction</span><span class="sxs-lookup"><span data-stu-id="9bbe2-169">Start-Transaction</span></span>](Start-Transaction.md)

[<span data-ttu-id="9bbe2-170">Undo-Transaction</span><span class="sxs-lookup"><span data-stu-id="9bbe2-170">Undo-Transaction</span></span>](Undo-Transaction.md)

[<span data-ttu-id="9bbe2-171">Use-Transaction</span><span class="sxs-lookup"><span data-stu-id="9bbe2-171">Use-Transaction</span></span>](Use-Transaction.md)

[<span data-ttu-id="9bbe2-172">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="9bbe2-172">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="9bbe2-173">New-Item</span><span class="sxs-lookup"><span data-stu-id="9bbe2-173">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="9bbe2-174">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9bbe2-174">New-ItemProperty</span></span>](New-ItemProperty.md)
