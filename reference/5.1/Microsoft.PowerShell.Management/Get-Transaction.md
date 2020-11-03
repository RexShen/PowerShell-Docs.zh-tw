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
# <span data-ttu-id="6975d-103">Get-Transaction</span><span class="sxs-lookup"><span data-stu-id="6975d-103">Get-Transaction</span></span>

## <span data-ttu-id="6975d-104">概要</span><span class="sxs-lookup"><span data-stu-id="6975d-104">SYNOPSIS</span></span>
<span data-ttu-id="6975d-105">取得目前的 (使用中) 交易。</span><span class="sxs-lookup"><span data-stu-id="6975d-105">Gets the current (active) transaction.</span></span>

## <span data-ttu-id="6975d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6975d-106">SYNTAX</span></span>

```
Get-Transaction [<CommonParameters>]
```

## <span data-ttu-id="6975d-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6975d-107">DESCRIPTION</span></span>
<span data-ttu-id="6975d-108">**取得交易** Cmdlet 會取得物件，該物件代表會話中的目前交易。</span><span class="sxs-lookup"><span data-stu-id="6975d-108">The **Get-Transaction** cmdlet gets an object that represents the current transaction in the session.</span></span>

<span data-ttu-id="6975d-109">此 Cmdlet 永遠不會傳回多個物件，因為一次只有一筆交易在作用中。</span><span class="sxs-lookup"><span data-stu-id="6975d-109">This cmdlet never returns more than one object, because only one transaction is active at a time.</span></span>
<span data-ttu-id="6975d-110">如果您使用啟動交易) 的獨立參數來啟動一或多個獨立的交易 (，最近啟動的交易就會是使用中的交易，而這就 **是交易傳回** 的交易。</span><span class="sxs-lookup"><span data-stu-id="6975d-110">If you start one or more independent transactions (by using the Independent parameter of Start-Transaction), the most recently started transaction is active, and that is the transaction that **Get-Transaction** returns.</span></span>

<span data-ttu-id="6975d-111">當所有使用中交易都已回復或認可時，此 Cmdlet 會顯示會話中最近使用中的交易。</span><span class="sxs-lookup"><span data-stu-id="6975d-111">When all active transactions have either been rolled back or committed, this cmdlet shows the transaction that was most recently active in the session.</span></span>

<span data-ttu-id="6975d-112">此 Cmdlet 是支援 Windows PowerShell 中交易功能的其中一組 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6975d-112">This cmdlet is one of a set of cmdlets that support the transactions feature in Windows PowerShell.</span></span>
<span data-ttu-id="6975d-113">如需詳細資訊，請參閱 about_Transactions。</span><span class="sxs-lookup"><span data-stu-id="6975d-113">For more information, see about_Transactions.</span></span>

## <span data-ttu-id="6975d-114">範例</span><span class="sxs-lookup"><span data-stu-id="6975d-114">EXAMPLES</span></span>

### <span data-ttu-id="6975d-115">範例1：取得目前的交易</span><span class="sxs-lookup"><span data-stu-id="6975d-115">Example 1: Get the current transaction</span></span>

```
PS C:\> Start-Transaction
PS C:\> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

<span data-ttu-id="6975d-116">此命令使用 Get-Transaction Cmdlet 取得目前交易。</span><span class="sxs-lookup"><span data-stu-id="6975d-116">This command uses the Get-Transaction cmdlet to get the current transaction.</span></span>

### <span data-ttu-id="6975d-117">範例2：顯示交易對象的屬性和方法</span><span class="sxs-lookup"><span data-stu-id="6975d-117">Example 2: Show the properties and methods of the transaction object</span></span>

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

<span data-ttu-id="6975d-118">此命令使用 Get-Member Cmdlet 顯示交易物件的屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="6975d-118">This command uses the Get-Member cmdlet to show the properties and methods of the transaction object.</span></span>

### <span data-ttu-id="6975d-119">範例3：顯示已回復交易的屬性值</span><span class="sxs-lookup"><span data-stu-id="6975d-119">Example 3: Show the property values of a rolled back transaction</span></span>

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

<span data-ttu-id="6975d-120">此命令顯示已回復的交易之交易物件的屬性值。</span><span class="sxs-lookup"><span data-stu-id="6975d-120">This command shows the property values of a transaction object for a transaction that has been rolled back.</span></span>

### <span data-ttu-id="6975d-121">範例4：顯示已認可交易的屬性值</span><span class="sxs-lookup"><span data-stu-id="6975d-121">Example 4: Show the property values of a committed transaction</span></span>

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

<span data-ttu-id="6975d-122">此命令顯示已確認的交易之交易物件的屬性值。</span><span class="sxs-lookup"><span data-stu-id="6975d-122">This command shows the property values of a transaction object for a transaction that has been committed.</span></span>

### <span data-ttu-id="6975d-123">範例5：在另一個進行中時啟動交易</span><span class="sxs-lookup"><span data-stu-id="6975d-123">Example 5: Start a transaction while another is in progress</span></span>

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

<span data-ttu-id="6975d-124">此範例顯示當有另一個交易正在進行時，啟動交易的交易物件效果。</span><span class="sxs-lookup"><span data-stu-id="6975d-124">This example shows the effect on the transaction object of starting a transaction while another transaction is in progress.</span></span>
<span data-ttu-id="6975d-125">通常這種情況會在指令碼執行的交易包含函式或呼叫包含另一個完整交易的指令碼時發生。</span><span class="sxs-lookup"><span data-stu-id="6975d-125">Typically, this happens when a script that runs a transaction includes a function or calls a script that contains another complete transaction.</span></span>

<span data-ttu-id="6975d-126">除非第二個 **啟動交易** 命令包含 *獨立* 的參數，否則 **啟動交易** 不會建立新的交易。</span><span class="sxs-lookup"><span data-stu-id="6975d-126">Unless the second **Start-Transaction** command includes the *Independent* parameter, **Start-Transaction** does not create a new transaction.</span></span>
<span data-ttu-id="6975d-127">而是將第二個訂閱者加入至原始的交易。</span><span class="sxs-lookup"><span data-stu-id="6975d-127">Instead, it adds a second subscriber to the original transaction.</span></span>

<span data-ttu-id="6975d-128">第一個 **啟動交易** 命令會啟動交易。</span><span class="sxs-lookup"><span data-stu-id="6975d-128">The first **Start-Transaction** command starts the transaction.</span></span>
<span data-ttu-id="6975d-129">具有 *UseTransaction* 參數的 New-Item 命令是交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="6975d-129">A New-Item command with the *UseTransaction* parameter is part of the transaction.</span></span>

<span data-ttu-id="6975d-130">第二個 **啟動交易** 命令會將訂閱者加入至交易。</span><span class="sxs-lookup"><span data-stu-id="6975d-130">A second **Start-Transaction** command adds a subscriber to the transaction.</span></span>
<span data-ttu-id="6975d-131">下一個 New-Item 命令也是交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="6975d-131">The next New-Item command is also part of the transaction.</span></span>

<span data-ttu-id="6975d-132">第一個 **Get transaction** 命令會顯示多訂閱者交易。</span><span class="sxs-lookup"><span data-stu-id="6975d-132">The first **Get-Transaction** command shows the multi-subscriber transaction.</span></span>
<span data-ttu-id="6975d-133">請注意，訂閱者計數是 2。</span><span class="sxs-lookup"><span data-stu-id="6975d-133">Notice that the subscriber count is 2.</span></span>

<span data-ttu-id="6975d-134">第一個 Complete-Transaction 命令不會確認交易，但它會將訂閱者計數減少至 1。</span><span class="sxs-lookup"><span data-stu-id="6975d-134">The first Complete-Transaction command does not commit the transaction, but it reduces the subscriber count to 1.</span></span>

<span data-ttu-id="6975d-135">第二個 **完整交易** 命令認可交易。</span><span class="sxs-lookup"><span data-stu-id="6975d-135">The second **Complete-Transaction** command commits the transaction.</span></span>

### <span data-ttu-id="6975d-136">範例6：當另一個交易正在進行時啟動獨立交易</span><span class="sxs-lookup"><span data-stu-id="6975d-136">Example 6: Start an independent transaction while another is in progress</span></span>

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

<span data-ttu-id="6975d-137">此範例顯示當有另一個獨立交易正在進行時，啟動交易的交易物件效果。</span><span class="sxs-lookup"><span data-stu-id="6975d-137">This example shows the effect on the transaction object of starting an independent transaction while another transaction is in progress.</span></span>

<span data-ttu-id="6975d-138">第一個 **啟動交易** 命令會啟動交易。</span><span class="sxs-lookup"><span data-stu-id="6975d-138">The first **Start-Transaction** command starts the transaction.</span></span>
<span data-ttu-id="6975d-139">具有 *UseTransaction* 參數的 **新專案** 命令是交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="6975d-139">A **New-Item** command with the *UseTransaction* parameter is part of the transaction.</span></span>

<span data-ttu-id="6975d-140">第二個 **啟動交易** 命令會將訂閱者加入至交易。</span><span class="sxs-lookup"><span data-stu-id="6975d-140">A second **Start-Transaction** command adds a subscriber to the transaction.</span></span>
<span data-ttu-id="6975d-141">下一個 **新專案** 命令也是交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="6975d-141">The next **New-Item** command is also part of the transaction.</span></span>

<span data-ttu-id="6975d-142">第一個 **Get transaction** 命令會顯示多訂閱者交易。</span><span class="sxs-lookup"><span data-stu-id="6975d-142">The first **Get-Transaction** command shows the multi-subscriber transaction.</span></span>
<span data-ttu-id="6975d-143">請注意，訂閱者計數是 2。</span><span class="sxs-lookup"><span data-stu-id="6975d-143">Note that the subscriber count is 2.</span></span>

<span data-ttu-id="6975d-144">**完整交易** 命令會將訂閱者計數減少至1，但不會認可交易。</span><span class="sxs-lookup"><span data-stu-id="6975d-144">The **Complete-Transaction** command reduces the subscriber count to 1, but it does not commit the transaction.</span></span>

<span data-ttu-id="6975d-145">第二個 **完整交易** 命令認可交易。</span><span class="sxs-lookup"><span data-stu-id="6975d-145">The second **Complete-Transaction** command commits the transaction.</span></span>

## <span data-ttu-id="6975d-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6975d-146">PARAMETERS</span></span>

### <span data-ttu-id="6975d-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6975d-147">CommonParameters</span></span>
<span data-ttu-id="6975d-148">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="6975d-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6975d-149">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="6975d-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6975d-150">輸入</span><span class="sxs-lookup"><span data-stu-id="6975d-150">INPUTS</span></span>

### <span data-ttu-id="6975d-151">無</span><span class="sxs-lookup"><span data-stu-id="6975d-151">None</span></span>
<span data-ttu-id="6975d-152">您無法使用管線將物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6975d-152">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="6975d-153">輸出</span><span class="sxs-lookup"><span data-stu-id="6975d-153">OUTPUTS</span></span>

### <span data-ttu-id="6975d-154">System.Management.Automation.PSTransaction</span><span class="sxs-lookup"><span data-stu-id="6975d-154">System.Management.Automation.PSTransaction</span></span>
<span data-ttu-id="6975d-155">這個 Cmdlet 會傳回代表目前交易的物件。</span><span class="sxs-lookup"><span data-stu-id="6975d-155">This cmdlet returns an object that represents the current transaction.</span></span>

## <span data-ttu-id="6975d-156">注意</span><span class="sxs-lookup"><span data-stu-id="6975d-156">NOTES</span></span>

## <span data-ttu-id="6975d-157">相關連結</span><span class="sxs-lookup"><span data-stu-id="6975d-157">RELATED LINKS</span></span>

[<span data-ttu-id="6975d-158">Complete-Transaction</span><span class="sxs-lookup"><span data-stu-id="6975d-158">Complete-Transaction</span></span>](Complete-Transaction.md)

[<span data-ttu-id="6975d-159">Start-Transaction</span><span class="sxs-lookup"><span data-stu-id="6975d-159">Start-Transaction</span></span>](Start-Transaction.md)

[<span data-ttu-id="6975d-160">Undo-Transaction</span><span class="sxs-lookup"><span data-stu-id="6975d-160">Undo-Transaction</span></span>](Undo-Transaction.md)

[<span data-ttu-id="6975d-161">Use-Transaction</span><span class="sxs-lookup"><span data-stu-id="6975d-161">Use-Transaction</span></span>](Use-Transaction.md)

[<span data-ttu-id="6975d-162">New-Item</span><span class="sxs-lookup"><span data-stu-id="6975d-162">New-Item</span></span>](New-Item.md)
