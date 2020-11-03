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
# <span data-ttu-id="ad0f6-103">Start-Transaction</span><span class="sxs-lookup"><span data-stu-id="ad0f6-103">Start-Transaction</span></span>

## <span data-ttu-id="ad0f6-104">概要</span><span class="sxs-lookup"><span data-stu-id="ad0f6-104">SYNOPSIS</span></span>
<span data-ttu-id="ad0f6-105">啟動交易。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-105">Starts a transaction.</span></span>

## <span data-ttu-id="ad0f6-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ad0f6-106">SYNTAX</span></span>

```
Start-Transaction [-Timeout <Int32>] [-Independent] [-RollbackPreference <RollbackSeverity>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ad0f6-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="ad0f6-107">DESCRIPTION</span></span>
<span data-ttu-id="ad0f6-108">**啟動交易** Cmdlet 會啟動交易，這是一系列作為單位來管理的命令。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-108">The **Start-Transaction** cmdlet starts a transaction, which is a series of commands that are managed as a unit.</span></span>
<span data-ttu-id="ad0f6-109">您可以完成或認可交易。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-109">A transaction can be completed, or committed.</span></span>
<span data-ttu-id="ad0f6-110">或者，它可以完全復原或復原，讓交易所變更的任何資料都還原為其原始狀態。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-110">Alternatively, it can be completely undone, or rolled back, so that any data changed by the transaction is restored to its original state.</span></span>
<span data-ttu-id="ad0f6-111">由於交易中的命令會被視為一個單位來管理，因此，所有命令必須一起確認或一起回復。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-111">Because the commands in a transaction are managed as a unit, either all commands are committed or all commands are rolled back.</span></span>

<span data-ttu-id="ad0f6-112">根據預設，如果交易中的任何命令產生錯誤，就會自動回復交易。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-112">By default, if any command in the transaction generates an error, transactions are rolled back automatically.</span></span>
<span data-ttu-id="ad0f6-113">您可以使用 *RollbackPreference* 參數來變更此行為。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-113">You can use the *RollbackPreference* parameter to change this behavior.</span></span>

<span data-ttu-id="ad0f6-114">交易中使用的 Cmdlet 必須設計為支援交易。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-114">The cmdlets used in a transaction must be designed to support transactions.</span></span>
<span data-ttu-id="ad0f6-115">支援交易的 Cmdlet 具有 *UseTransaction* 參數。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-115">Cmdlets that support transactions have a *UseTransaction* parameter.</span></span>
<span data-ttu-id="ad0f6-116">若要在提供者中執行交易，該提供者必須支援交易。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-116">To perform transactions in a provider, the provider must support transactions.</span></span>
<span data-ttu-id="ad0f6-117">Windows Vista 和更新版本的 Windows 作業系統中的 Windows PowerShell Registry 提供者支援交易。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-117">The Windows PowerShell Registry provider in Windows Vista and later versions of the Windows operating system supports transactions.</span></span>
<span data-ttu-id="ad0f6-118">您也可以使用 **TransactedString** 類別，在任何支援 Windows PowerShell 的 Windows 系統版本上的交易中包含運算式。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-118">You can also use the **Microsoft.PowerShell.Commands.Management.TransactedString** class to include expressions in transactions on any version of the Windows system that supports Windows PowerShell.</span></span>
<span data-ttu-id="ad0f6-119">其他的 Windows PowerShell 提供者也可以支援交易。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-119">Other Windows PowerShell providers can also support transactions.</span></span>

<span data-ttu-id="ad0f6-120">一次只有一個交易可以處於使用中狀態。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-120">Only one transaction can be active at a time.</span></span>
<span data-ttu-id="ad0f6-121">如果您在交易正在進行時啟動新的獨立交易，新的交易就會變成使用中的交易，而且您必須先認可或回復新交易，然後再對原始交易進行任何變更。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-121">If you start a new, independent transaction while a transaction is in progress, the new transaction becomes the active transaction, and you must commit or roll back the new transaction before you make any changes to the original transaction.</span></span>

<span data-ttu-id="ad0f6-122">**Start-Transaction** Cmdlet 是一組支援 Windows PowerShell 中交易功能的 Cmdlet 之一。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-122">**Start-Transaction** cmdlet is one of a set of cmdlets that support the transactions feature in Windows PowerShell.</span></span>
<span data-ttu-id="ad0f6-123">如需詳細資訊，請參閱 about_Transactions。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-123">For more information, see about_Transactions.</span></span>

## <span data-ttu-id="ad0f6-124">範例</span><span class="sxs-lookup"><span data-stu-id="ad0f6-124">EXAMPLES</span></span>

### <span data-ttu-id="ad0f6-125">範例1：啟動和回復交易</span><span class="sxs-lookup"><span data-stu-id="ad0f6-125">Example 1: Start and roll back a transaction</span></span>

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany" -UseTransaction
PS HKCU:\software> New-ItemProperty "ContosoCompany" -Name "MyKey" -Value 123 -UseTransaction
PS HKCU:\software> Undo-Transaction
```

<span data-ttu-id="ad0f6-126">這些命令會啟動交易，然後回復交易。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-126">These commands start and then roll back a transaction.</span></span>
<span data-ttu-id="ad0f6-127">由於交易會回復，所以不會對登錄進行任何變更。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-127">Because the transaction is rolled back, no changes are made to the registry.</span></span>

### <span data-ttu-id="ad0f6-128">範例2：啟動和完成交易</span><span class="sxs-lookup"><span data-stu-id="ad0f6-128">Example 2: Start and complete a transaction</span></span>

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany" -UseTransaction
PS HKCU:\software> New-ItemProperty "ContosoCompany" -Name "MyKey" -Value 123 -UseTransaction
PS HKCU:\software> Complete-Transaction
```

<span data-ttu-id="ad0f6-129">這些命令會啟動交易，然後完成交易。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-129">These commands start and then complete a transaction.</span></span>
<span data-ttu-id="ad0f6-130">在使用 **完整交易** 命令之前，不會對登錄進行任何變更。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-130">No changes are made to the registry until the **Complete-Transaction** command is used.</span></span>

### <span data-ttu-id="ad0f6-131">範例3：使用不同的回復喜好設定</span><span class="sxs-lookup"><span data-stu-id="ad0f6-131">Example 3: Use different rollback preferences</span></span>

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

<span data-ttu-id="ad0f6-132">此範例示範變更 *RollbackPreference* 參數值的效果。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-132">This example demonstrates the effect of changing the *RollbackPreference* parameter value.</span></span>

<span data-ttu-id="ad0f6-133">在第一組命令中， **Start-Transaction** 不會使用 *RollbackPreference* 。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-133">In the first set of commands, **Start-Transaction** does not use *RollbackPreference* .</span></span>
<span data-ttu-id="ad0f6-134">因此，會使用預設值 (錯誤) 。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-134">As a result, the default value (Error) is used.</span></span>
<span data-ttu-id="ad0f6-135">當交易命令中發生錯誤時，也就是指定的路徑不存在，就會自動回復交易。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-135">When an error occurs in a transaction command, that is, the specified path does not exist, the transaction is automatically rolled back.</span></span>

<span data-ttu-id="ad0f6-136">在第二組命令中， **Start Transaction** 會使用 *RollbackPreference* ，其值為「永不」。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-136">In the second set of commands, **Start-Transaction** uses *RollbackPreference* with a value of Never.</span></span>
<span data-ttu-id="ad0f6-137">因此，當交易命令中發生錯誤時，交易仍為使用中狀態且可順利完成。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-137">As a result, when an error occurs in a transaction command, the transaction is still active and can be completed successfully.</span></span>

<span data-ttu-id="ad0f6-138">因為大部分的交易必須在沒有錯誤的情況下執行，所以通常偏好 *RollbackPreference* 的預設值。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-138">Because most transactions must be performed without error, the default value of *RollbackPreference* is typically preferred.</span></span>

### <span data-ttu-id="ad0f6-139">範例4：交易正在進行時使用這個 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ad0f6-139">Example 4: Use this cmdlet while a transaction is in progress</span></span>

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

<span data-ttu-id="ad0f6-140">此範例顯示交易進行中時使用 **啟動交易** 的效果。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-140">This example shows the effect of using **Start-Transaction** while a transaction is in progress.</span></span>
<span data-ttu-id="ad0f6-141">這個效果類似加入進行中交易。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-141">The effect is much like joining the transaction in progress.</span></span>

<span data-ttu-id="ad0f6-142">雖然這是簡化的命令，但這種情況通常是在交易涉及執行包含完整交易的腳本時發生。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-142">Although this is a simplified command, this scenario frequently occurs when the transaction involves running a script that includes a complete transaction.</span></span>

<span data-ttu-id="ad0f6-143">第一個 **啟動交易** 命令會啟動交易。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-143">The first **Start-Transaction** command starts the transaction.</span></span>
<span data-ttu-id="ad0f6-144">第一個 **新專案** 命令是交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-144">The first **New-Item** command is part of the transaction.</span></span>

<span data-ttu-id="ad0f6-145">第二個 **啟動交易** 命令會將新的訂閱者新增至交易。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-145">The second **Start-Transaction** command adds a new subscriber to the transaction.</span></span>
<span data-ttu-id="ad0f6-146">**取得交易** 命令現在會傳回訂閱者計數為2的交易。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-146">The **Get-Transaction** command now returns a transaction with a subscriber count of 2.</span></span>
<span data-ttu-id="ad0f6-147">第二個 **新專案** 命令是相同交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-147">The second **New-Item** command is part of the same transaction.</span></span>

<span data-ttu-id="ad0f6-148">在整個交易完成之前，不會對登錄進行任何變更。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-148">No changes are made to the registry until the whole transaction is completed.</span></span>
<span data-ttu-id="ad0f6-149">若要完成交易，您必須輸入兩個 **完整交易** 命令，每個訂閱者一個。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-149">To complete the transaction, you must enter two **Complete-Transaction** commands, one for each subscriber.</span></span>
<span data-ttu-id="ad0f6-150">如果您在任何時間點回復交易，則會針對這兩個訂閱者復原所有交易。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-150">If you were to roll back the transaction at any point, all the transaction would be rolled back for both subscribers.</span></span>

### <span data-ttu-id="ad0f6-151">範例5：當獨立交易正在進行時啟動</span><span class="sxs-lookup"><span data-stu-id="ad0f6-151">Example 5: Start an independent transaction while one is in progress</span></span>

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

<span data-ttu-id="ad0f6-152">此範例顯示在另一個交易正在進行時，使用 **啟動交易** 的 *獨立* 參數啟動交易的效果。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-152">This example shows the effect of using the *Independent* parameter of **Start-Transaction** to start a transaction while another transaction is in progress.</span></span>
<span data-ttu-id="ad0f6-153">在這個案例中，會回復新交易，但不會對原始交易產生任何影響。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-153">In this case, the new transaction is rolled back without affecting the original transaction.</span></span>

<span data-ttu-id="ad0f6-154">雖然交易在邏輯上是獨立的，但由於一次只能有一個交易可處於使用中狀態，因此，您必須先回復或確認最新交易，才能繼續執行原始交易上的工作。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-154">Although the transactions are logically independent, because only one transaction can be active at a time, you must roll back or commit the newest transaction before resuming work on the original transaction.</span></span>

<span data-ttu-id="ad0f6-155">第一組命令會啟動交易。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-155">The first set of commands starts a transaction.</span></span>
<span data-ttu-id="ad0f6-156">[ **新增專案** ] 命令是第一個交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-156">The **New-Item** command is part of the first transaction.</span></span>

<span data-ttu-id="ad0f6-157">在第二組命令中， **Start Transaction** 命令會使用 *獨立* 的參數。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-157">In the second set of commands, the **Start-Transaction** command uses the *Independent* parameter.</span></span>
<span data-ttu-id="ad0f6-158">接下來的「 **取得交易** 」命令會顯示使用中交易的交易對象，這是最新的交易。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-158">The **Get-Transaction** command that follows shows the transaction object for the active transaction, which is the newest one.</span></span>
<span data-ttu-id="ad0f6-159">訂閱者計數等於1，顯示交易無關。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-159">The subscriber count is equal to 1, that shows that the transactions are unrelated.</span></span>

<span data-ttu-id="ad0f6-160">使用 **Undo 交易** 命令復原使用中的交易時，原始交易會再次變成作用中狀態。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-160">When the active transaction is rolled back by using an **Undo-Transaction** command, the original transaction becomes active again.</span></span>

<span data-ttu-id="ad0f6-161">**ItemProperty** 命令（原始交易的一部分）會在沒有錯誤的情況下完成，而且可以使用 **完整交易** 命令來完成原始交易。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-161">The **New-ItemProperty** command, which is part of the original transaction, finishes without error, and the original transaction can be completed by using the **Complete-Transaction** command.</span></span>
<span data-ttu-id="ad0f6-162">因此，會變更登錄。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-162">As a result, the registry is changed.</span></span>

### <span data-ttu-id="ad0f6-163">範例6：執行不屬於交易一部分的命令</span><span class="sxs-lookup"><span data-stu-id="ad0f6-163">Example 6: Run commands that are not part of a transaction</span></span>

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

<span data-ttu-id="ad0f6-164">這個範例示範交易正在進行時提交的命令，可以包含或不包含在交易中。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-164">This example demonstrates that commands that are submitted while a transaction is in progress can be included in the transaction or not included.</span></span>
<span data-ttu-id="ad0f6-165">只有使用 *UseTransaction* 參數的命令是交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-165">Only commands that use the *UseTransaction* parameter are part of the transaction.</span></span>

<span data-ttu-id="ad0f6-166">第一個和第三個 **新專案** 命令使用 *UseTransaction* 參數。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-166">The first and third **New-Item** commands use the *UseTransaction* parameter.</span></span>
<span data-ttu-id="ad0f6-167">這些命令是交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-167">These commands are part of the transaction.</span></span>
<span data-ttu-id="ad0f6-168">因為第二個 **新專案** 命令未使用 *UseTransaction* 參數，所以它不是交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-168">Because the second **New-Item** command does not use the *UseTransaction* parameter, it is not part of the transaction.</span></span>

<span data-ttu-id="ad0f6-169">第一個 dir 命令會顯示效果。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-169">The first dir command shows the effect.</span></span>
<span data-ttu-id="ad0f6-170">第二個 **新專案** 命令會立即完成，但在認可交易之前，第一個和第三個 **新專案** 命令都沒有作用。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-170">The second **New-Item** command is completed immediately, but the first and third **New-Item** commands are not effective until the transaction is committed.</span></span>

<span data-ttu-id="ad0f6-171">**完整交易** 命令認可交易。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-171">The **Complete-Transaction** command commits the transaction.</span></span>
<span data-ttu-id="ad0f6-172">如此一來，第二個 dir 命令會顯示所有新專案都會新增至登錄中。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-172">As a result, the second dir command shows that all of the new items are added to the registry.</span></span>

### <span data-ttu-id="ad0f6-173">範例7：回復未在指定時間內完成的交易</span><span class="sxs-lookup"><span data-stu-id="ad0f6-173">Example 7: Roll back a transaction that does not finish in a specified time</span></span>

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

<span data-ttu-id="ad0f6-174">此命令會使用 **start-Transaction** 的 *Timeout* 參數啟動必須在兩分鐘內完成的交易。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-174">This command uses the *Timeout* parameter of **Start-Transaction** to start a transaction that must be completed within two minutes.</span></span>
<span data-ttu-id="ad0f6-175">如果在超時時間過期時交易未完成，則會自動回復。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-175">If the transaction is not finished when the time-out expires, it is rolled back automatically.</span></span>

<span data-ttu-id="ad0f6-176">過期時，系統不會通知您，但 transaction 物件的 **Status** 屬性會設定為 RolledBack，而使用 *UseTransaction* 參數的命令則會失敗。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-176">When the time-out expires, you are not notified, but the **Status** property of the transaction object is set to RolledBack and commands that use the *UseTransaction* parameter fail.</span></span>

## <span data-ttu-id="ad0f6-177">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ad0f6-177">PARAMETERS</span></span>

### <span data-ttu-id="ad0f6-178">-獨立</span><span class="sxs-lookup"><span data-stu-id="ad0f6-178">-Independent</span></span>
<span data-ttu-id="ad0f6-179">指出此 Cmdlet 會啟動與任何進行中交易無關的交易。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-179">Indicates that this cmdlet starts a transaction that is independent of any transactions in progress.</span></span>
<span data-ttu-id="ad0f6-180">依預設，如果您在另一個交易正在進行時使用 **啟動交易** ，則會將新的訂閱者新增到進行中的交易。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-180">By default, if you use **Start-Transaction** while another transaction is in progress, a new subscriber is added to the transaction in progress.</span></span>
<span data-ttu-id="ad0f6-181">只有當工作階段中已經有進行中交易，這個參數才有作用。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-181">This parameter has an effect only when a transaction is already in progress in the session.</span></span>

<span data-ttu-id="ad0f6-182">依預設，如果您在交易正在進行時使用 **啟動交易** ，則會重複使用現有的交易對象，而且訂閱者計數會遞增。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-182">By default, if you use **Start-Transaction** while a transaction is in progress, the existing transaction object is reused and the subscriber count is incremented.</span></span>
<span data-ttu-id="ad0f6-183">這個效果類似加入原始交易。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-183">The effect is much like joining the original transaction.</span></span>
<span data-ttu-id="ad0f6-184">Undo-Transaction 命令會回復整個交易。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-184">An Undo-Transaction command rolls back the whole the transaction.</span></span>
<span data-ttu-id="ad0f6-185">若要完成交易，您必須針對每個訂閱者輸入 Complete-Transaction 命令。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-185">To complete the transaction, you must enter a Complete-Transaction command for each subscriber.</span></span>
<span data-ttu-id="ad0f6-186">因為大部分同時處於進行中狀態的交易都是相關的，所以預設值就足以應付大部分的使用。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-186">Because most transactions that are in progress at the same time are related, the default is sufficient for most uses.</span></span>

<span data-ttu-id="ad0f6-187">如果您指定 *獨立* 參數，這個 Cmdlet 會建立可以完成或復原的新交易，而不會影響原始交易。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-187">If you specify the *Independent* parameter, this cmdlet creates a new transaction that can be completed or undone without affecting the original transaction.</span></span>
<span data-ttu-id="ad0f6-188">不過，由於一次只能有一個交易可以處於使用中狀態，因此，您必須先完成或回復新交易，然後才能繼續執行原始交易上的工作。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-188">However, because only one transaction can be active at a time, you must complete or roll back the new transaction before resuming work on the original transaction.</span></span>

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

### <span data-ttu-id="ad0f6-189">-RollbackPreference</span><span class="sxs-lookup"><span data-stu-id="ad0f6-189">-RollbackPreference</span></span>
<span data-ttu-id="ad0f6-190">指定自動回復交易的條件。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-190">Specifies the conditions under which a transaction is automatically rolled back.</span></span>
<span data-ttu-id="ad0f6-191">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="ad0f6-191">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="ad0f6-192">錯誤。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-192">Error.</span></span>
<span data-ttu-id="ad0f6-193">如果發生終止或非終止錯誤，即會自動回復交易。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-193">The transaction is rolled back automatically if a terminating or non-terminating error occurs.</span></span>
- <span data-ttu-id="ad0f6-194">TerminatingError.</span><span class="sxs-lookup"><span data-stu-id="ad0f6-194">TerminatingError.</span></span>
<span data-ttu-id="ad0f6-195">如果發生終止錯誤，即會自動回復交易。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-195">The transaction is rolled back automatically if a terminating error occurs.</span></span>
- <span data-ttu-id="ad0f6-196">永不。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-196">Never.</span></span>
<span data-ttu-id="ad0f6-197">永遠不會自動回復交易。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-197">The transaction is never rolled back automatically.</span></span>

<span data-ttu-id="ad0f6-198">預設值為 Error。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-198">The default value is Error.</span></span>

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

### <span data-ttu-id="ad0f6-199">-Timeout</span><span class="sxs-lookup"><span data-stu-id="ad0f6-199">-Timeout</span></span>
<span data-ttu-id="ad0f6-200">指定交易處於使用中狀態的最長時間 (以分鐘為單位)。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-200">Specifies the maximum time, in minutes, that the transaction is active.</span></span>
<span data-ttu-id="ad0f6-201">當逾時過期時，即會自動回復交易。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-201">When the time-out expires, the transaction is automatically rolled back.</span></span>

<span data-ttu-id="ad0f6-202">根據預設，在命令列啟動的交易不會逾時。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-202">By default, there is no time-out for transactions that are started at the command line.</span></span>
<span data-ttu-id="ad0f6-203">如果交易是透過指令碼啟動，則預設的逾時值是 30 分鐘。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-203">When transactions are started by a script, the default time-out is 30 minutes.</span></span>

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

### <span data-ttu-id="ad0f6-204">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ad0f6-204">-Confirm</span></span>
<span data-ttu-id="ad0f6-205">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-205">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ad0f6-206">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ad0f6-206">-WhatIf</span></span>
<span data-ttu-id="ad0f6-207">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-207">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="ad0f6-208">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-208">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ad0f6-209">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ad0f6-209">CommonParameters</span></span>
<span data-ttu-id="ad0f6-210">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-210">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ad0f6-211">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-211">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ad0f6-212">輸入</span><span class="sxs-lookup"><span data-stu-id="ad0f6-212">INPUTS</span></span>

### <span data-ttu-id="ad0f6-213">無</span><span class="sxs-lookup"><span data-stu-id="ad0f6-213">None</span></span>
<span data-ttu-id="ad0f6-214">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-214">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="ad0f6-215">輸出</span><span class="sxs-lookup"><span data-stu-id="ad0f6-215">OUTPUTS</span></span>

### <span data-ttu-id="ad0f6-216">無</span><span class="sxs-lookup"><span data-stu-id="ad0f6-216">None</span></span>
<span data-ttu-id="ad0f6-217">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="ad0f6-217">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="ad0f6-218">注意</span><span class="sxs-lookup"><span data-stu-id="ad0f6-218">NOTES</span></span>

## <span data-ttu-id="ad0f6-219">相關連結</span><span class="sxs-lookup"><span data-stu-id="ad0f6-219">RELATED LINKS</span></span>

[<span data-ttu-id="ad0f6-220">Complete-Transaction</span><span class="sxs-lookup"><span data-stu-id="ad0f6-220">Complete-Transaction</span></span>](Complete-Transaction.md)

[<span data-ttu-id="ad0f6-221">Get-Transaction</span><span class="sxs-lookup"><span data-stu-id="ad0f6-221">Get-Transaction</span></span>](Get-Transaction.md)

[<span data-ttu-id="ad0f6-222">Undo-Transaction</span><span class="sxs-lookup"><span data-stu-id="ad0f6-222">Undo-Transaction</span></span>](Undo-Transaction.md)

[<span data-ttu-id="ad0f6-223">Use-Transaction</span><span class="sxs-lookup"><span data-stu-id="ad0f6-223">Use-Transaction</span></span>](Use-Transaction.md)
