---
description: 描述如何在 PowerShell 中管理交易的作業。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_transactions?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Transactions
ms.openlocfilehash: 522e0f727754b0b0153571039f3bf3966d0abf20
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207527"
---
# <a name="about-transactions"></a><span data-ttu-id="91e9d-104">關於交易</span><span class="sxs-lookup"><span data-stu-id="91e9d-104">About Transactions</span></span>

## <a name="short-description"></a><span data-ttu-id="91e9d-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="91e9d-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="91e9d-106">描述如何在 PowerShell 中管理交易的作業。</span><span class="sxs-lookup"><span data-stu-id="91e9d-106">Describes how to manage transacted operations in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="91e9d-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="91e9d-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="91e9d-108">從 PowerShell 2.0 開始，PowerShell 支援交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-108">Transactions are supported in PowerShell beginning in PowerShell 2.0.</span></span> <span data-ttu-id="91e9d-109">這項功能可讓您啟動交易、指出哪些命令是交易的一部分，以及認可或回復交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-109">This feature enables you to start a transaction, to indicate which commands are part of the transaction, and to commit or roll back a transaction.</span></span>

## <a name="about-transactions"></a><span data-ttu-id="91e9d-110">關於交易</span><span class="sxs-lookup"><span data-stu-id="91e9d-110">ABOUT TRANSACTIONS</span></span>

<span data-ttu-id="91e9d-111">在 PowerShell 中，交易是一組一或多個以邏輯單元形式管理的命令。</span><span class="sxs-lookup"><span data-stu-id="91e9d-111">In PowerShell, a transaction is a set of one or more commands that are managed as a logical unit.</span></span> <span data-ttu-id="91e9d-112">交易可以 ( 「已認可」 ) 來完成，這會變更受交易影響的資料。</span><span class="sxs-lookup"><span data-stu-id="91e9d-112">A transaction can be completed ("committed"), which changes data affected by the transaction.</span></span> <span data-ttu-id="91e9d-113">或者，交易可以完全復原 ( 「已復原」 ) ，讓交易不會變更受影響的資料。</span><span class="sxs-lookup"><span data-stu-id="91e9d-113">Or, a transaction can be completely undone ("rolled back") so that the affected data is not changed by the transaction.</span></span>

<span data-ttu-id="91e9d-114">由於交易中的命令是以一個單位來管理，因此會認可所有命令，否則會回復所有命令。</span><span class="sxs-lookup"><span data-stu-id="91e9d-114">Because the commands in a transaction are managed as a unit, either all commands are committed, or all commands are rolled back.</span></span>

<span data-ttu-id="91e9d-115">交易廣泛用於資料處理，最值得注意的是資料庫作業和財務交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-115">Transactions are widely used in data processing, most notably in database operations and for financial transactions.</span></span> <span data-ttu-id="91e9d-116">當一組命令的最糟案例不是它們都失敗時，最常使用交易，但有些命令會在其他命令失敗時成功，讓系統處於損毀、假或 uninterpretable 狀態，而難以修復。</span><span class="sxs-lookup"><span data-stu-id="91e9d-116">Transactions are most often used when the worst-case scenario for a set of commands is not that they all fail, but that some commands succeed while others fail, leaving the system in a damaged, false, or uninterpretable state that is difficult to repair.</span></span>

## <a name="transaction-cmdlets"></a><span data-ttu-id="91e9d-117">TRANSACTION CMDLET</span><span class="sxs-lookup"><span data-stu-id="91e9d-117">TRANSACTION CMDLETS</span></span>

<span data-ttu-id="91e9d-118">PowerShell 包含數個專為管理交易而設計的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="91e9d-118">PowerShell includes several cmdlets designed for managing transactions.</span></span>

- <span data-ttu-id="91e9d-119">Start-Transaction：啟動新的交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-119">Start-Transaction: Starts a new transaction.</span></span>
- <span data-ttu-id="91e9d-120">使用-Transaction：將命令或運算式加入至交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-120">Use-Transaction: Adds a command or expression to the transaction.</span></span> <span data-ttu-id="91e9d-121">命令必須使用已啟用交易的物件。</span><span class="sxs-lookup"><span data-stu-id="91e9d-121">The command must use transaction-enabled objects.</span></span>
- <span data-ttu-id="91e9d-122">恢復交易：回復交易，讓交易不會變更任何資料。</span><span class="sxs-lookup"><span data-stu-id="91e9d-122">Undo-Transaction: Rolls back the transaction so that no data is changed by the transaction.</span></span>
- <span data-ttu-id="91e9d-123">Complete-Transaction：認可交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-123">Complete-Transaction: Commits the transaction.</span></span> <span data-ttu-id="91e9d-124">受交易影響的資料會變更。</span><span class="sxs-lookup"><span data-stu-id="91e9d-124">The data affected by the transaction is changed.</span></span>
- <span data-ttu-id="91e9d-125">取得交易：取得使用中交易的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="91e9d-125">Get-Transaction: Gets information about the active transaction.</span></span>

<span data-ttu-id="91e9d-126">如需交易 Cmdlet 的清單，請輸入：</span><span class="sxs-lookup"><span data-stu-id="91e9d-126">For a list of transaction cmdlets, type:</span></span>

```powershell
get-command *transaction
```

<span data-ttu-id="91e9d-127">如需 Cmdlet 的詳細資訊，請輸入：</span><span class="sxs-lookup"><span data-stu-id="91e9d-127">For detailed information about the cmdlets, type:</span></span>

```powershell
get-help use-transaction -detailed
```

## <a name="transaction-enabled-elements"></a><span data-ttu-id="91e9d-128">啟用交易的元素</span><span class="sxs-lookup"><span data-stu-id="91e9d-128">TRANSACTION-ENABLED ELEMENTS</span></span>

<span data-ttu-id="91e9d-129">若要參與交易，Cmdlet 和提供者都必須支援交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-129">To participate in a transaction, both the cmdlet and the provider must support transactions.</span></span> <span data-ttu-id="91e9d-130">這項功能內建于受交易影響的物件。</span><span class="sxs-lookup"><span data-stu-id="91e9d-130">This feature is built in to the objects that are affected by the transaction.</span></span>

<span data-ttu-id="91e9d-131">PowerShell 登錄提供者支援 Windows Vista 中的交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-131">The PowerShell Registry provider supports transactions in Windows Vista.</span></span> <span data-ttu-id="91e9d-132">TransactedString 物件 (TransactedString) 可搭配任何執行 PowerShell 的作業系統使用。</span><span class="sxs-lookup"><span data-stu-id="91e9d-132">The TransactedString object (Microsoft.PowerShell.Commands.Management.TransactedString) works with any operating system that runs PowerShell.</span></span>

<span data-ttu-id="91e9d-133">其他 PowerShell 提供者可支援交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-133">Other PowerShell providers can support transactions.</span></span> <span data-ttu-id="91e9d-134">若要在您的會話中尋找支援交易的 PowerShell 提供者，請使用下列命令，在提供者的 [功能] 屬性中尋找「交易」值：</span><span class="sxs-lookup"><span data-stu-id="91e9d-134">To find the PowerShell providers in your session that support transactions, use the following command to find the "Transactions" value in the Capabilities property of providers:</span></span>

```powershell
get-psprovider | where {$_.Capabilities -like "*transactions*"}
```

<span data-ttu-id="91e9d-135">如需提供者的詳細資訊，請參閱提供者的說明。</span><span class="sxs-lookup"><span data-stu-id="91e9d-135">For more information about a provider, see the Help for the provider.</span></span> <span data-ttu-id="91e9d-136">若要取得提供者說明，請輸入：</span><span class="sxs-lookup"><span data-stu-id="91e9d-136">To get provider Help, type:</span></span>

```
get-help <provider-name>
```

<span data-ttu-id="91e9d-137">例如，若要取得登錄提供者的說明，請輸入：</span><span class="sxs-lookup"><span data-stu-id="91e9d-137">For example, to get Help for the Registry provider, type:</span></span>

```powershell
get-help registry
```

## <a name="the-usetransaction-parameter"></a><span data-ttu-id="91e9d-138">USETRANSACTION 參數</span><span class="sxs-lookup"><span data-stu-id="91e9d-138">THE USETRANSACTION PARAMETER</span></span>

<span data-ttu-id="91e9d-139">可支援交易的 Cmdlet 具有 UseTransaction 參數。</span><span class="sxs-lookup"><span data-stu-id="91e9d-139">Cmdlets that can support transactions have a UseTransaction parameter.</span></span> <span data-ttu-id="91e9d-140">此參數包含使用中交易中的命令。</span><span class="sxs-lookup"><span data-stu-id="91e9d-140">This parameter includes the command in the active transaction.</span></span> <span data-ttu-id="91e9d-141">您可以使用完整的參數名稱或其別名 "usetx"。</span><span class="sxs-lookup"><span data-stu-id="91e9d-141">You can use the full parameter name or its alias, "usetx".</span></span>

<span data-ttu-id="91e9d-142">只有當會話包含使用中的交易時，才能使用此參數。</span><span class="sxs-lookup"><span data-stu-id="91e9d-142">The parameter can be used only when the session contains an active transaction.</span></span> <span data-ttu-id="91e9d-143">如果您在沒有使用中交易時輸入具有 UseTransaction 參數的命令，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="91e9d-143">If you enter a command with the UseTransaction parameter when there is no active transaction, the command fails.</span></span>

<span data-ttu-id="91e9d-144">若要使用 UseTransaction 參數尋找 Cmdlet，請輸入：</span><span class="sxs-lookup"><span data-stu-id="91e9d-144">To find cmdlets with the UseTransaction parameter, type:</span></span>

```powershell
get-help * -parameter UseTransaction
```

<span data-ttu-id="91e9d-145">在 PowerShell core 中，設計來搭配 PowerShell 提供者使用的所有 Cmdlet 都支援交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-145">In PowerShell core, all of the cmdlets designed to work with PowerShell providers support transactions.</span></span> <span data-ttu-id="91e9d-146">因此，您可以使用提供者 Cmdlet 來管理交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-146">As a result, you can use the provider cmdlets to manage transactions.</span></span>

<span data-ttu-id="91e9d-147">如需 PowerShell 提供者的詳細資訊，請參閱 [about_Providers](about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="91e9d-147">For more information about PowerShell providers, see [about_Providers](about_Providers.md).</span></span>

## <a name="the-transaction-object"></a><span data-ttu-id="91e9d-148">TRANSACTION 物件</span><span class="sxs-lookup"><span data-stu-id="91e9d-148">THE TRANSACTION OBJECT</span></span>

<span data-ttu-id="91e9d-149">交易會以 PowerShell 以交易對象（即 transaction）表示。</span><span class="sxs-lookup"><span data-stu-id="91e9d-149">Transactions are represented in PowerShell by a transaction object, System.Management.Automation.Transaction.</span></span>

<span data-ttu-id="91e9d-150">此物件具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="91e9d-150">The object has the following properties:</span></span>

- <span data-ttu-id="91e9d-151">RollbackPreference：包含目前交易的復原喜好設定集。</span><span class="sxs-lookup"><span data-stu-id="91e9d-151">RollbackPreference: Contains the rollback preference set for the current transaction.</span></span> <span data-ttu-id="91e9d-152">當您使用 Start-Transaction 啟動交易時，可以設定復原喜好設定。</span><span class="sxs-lookup"><span data-stu-id="91e9d-152">You can set the rollback preference when you use Start-Transaction to start the transaction.</span></span>

  <span data-ttu-id="91e9d-153">復原喜好設定會決定自動回復交易的條件。</span><span class="sxs-lookup"><span data-stu-id="91e9d-153">The rollback preference determines the conditions under which the transaction is rolled back automatically.</span></span> <span data-ttu-id="91e9d-154">有效值為 Error、TerminatingError 和 Never。</span><span class="sxs-lookup"><span data-stu-id="91e9d-154">Valid values are Error, TerminatingError, and Never.</span></span> <span data-ttu-id="91e9d-155">預設值為 Error。</span><span class="sxs-lookup"><span data-stu-id="91e9d-155">The default value is Error.</span></span>

- <span data-ttu-id="91e9d-156">狀態：包含交易的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="91e9d-156">Status: Contains the current status of the transaction.</span></span> <span data-ttu-id="91e9d-157">有效的值為作用中、已認可和 RolledBack。</span><span class="sxs-lookup"><span data-stu-id="91e9d-157">Valid values are Active, Committed, and RolledBack.</span></span>

- <span data-ttu-id="91e9d-158">SubscriberCount：包含交易的訂閱者數目。</span><span class="sxs-lookup"><span data-stu-id="91e9d-158">SubscriberCount: Contains the number of subscribers to the transaction.</span></span> <span data-ttu-id="91e9d-159">當您在另一個交易正在進行時，當您啟動交易時，便會將「訂閱者」新增至交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-159">A subscriber is added to a transaction when you start a transaction while another transaction is in progress.</span></span> <span data-ttu-id="91e9d-160">訂閱者認可交易時，訂閱者計數會遞減。</span><span class="sxs-lookup"><span data-stu-id="91e9d-160">The subscriber count is decremented when a subscriber commits the transaction.</span></span>

## <a name="active-transactions"></a><span data-ttu-id="91e9d-161">使用中交易</span><span class="sxs-lookup"><span data-stu-id="91e9d-161">ACTIVE TRANSACTIONS</span></span>

<span data-ttu-id="91e9d-162">在 PowerShell 中，一次只能有一個作用中的交易，而且您只能管理使用中的交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-162">In PowerShell, only one transaction is active at a time, and you can manage only the active transaction.</span></span> <span data-ttu-id="91e9d-163">相同會話中的多個交易可以同時進行，但只有最新啟動的交易處於作用中狀態。</span><span class="sxs-lookup"><span data-stu-id="91e9d-163">Multiple transactions can be in progress in the same session at the same time, but only the most-recently started transaction is active.</span></span>

<span data-ttu-id="91e9d-164">因此，當您使用 transaction Cmdlet 時，無法指定特定的交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-164">As a result, you cannot specify a particular transaction when using the transaction cmdlets.</span></span> <span data-ttu-id="91e9d-165">命令一律適用于使用中的交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-165">Commands always apply to the active transaction.</span></span>

<span data-ttu-id="91e9d-166">這在 Get-Transaction Cmdlet 的行為中最明顯。</span><span class="sxs-lookup"><span data-stu-id="91e9d-166">This is most evident in the behavior of the Get-Transaction cmdlet.</span></span> <span data-ttu-id="91e9d-167">當您輸入 Get-Transaction 命令時，Get-Transaction 一律只會取得一個交易對象。</span><span class="sxs-lookup"><span data-stu-id="91e9d-167">When you enter a Get-Transaction command, Get-Transaction always gets only one transaction object.</span></span> <span data-ttu-id="91e9d-168">此物件是代表使用中交易的物件。</span><span class="sxs-lookup"><span data-stu-id="91e9d-168">This object is the object that represents the active transaction.</span></span>

<span data-ttu-id="91e9d-169">若要管理不同的交易，您必須先認可或回復使用中的交易，才能完成該交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-169">To manage a different transaction, you must first finish the active transaction, either by committing it or rolling it back.</span></span> <span data-ttu-id="91e9d-170">當您這樣做時，先前的交易就會自動變成使用中狀態。</span><span class="sxs-lookup"><span data-stu-id="91e9d-170">When you do this, the previous transaction becomes active automatically.</span></span> <span data-ttu-id="91e9d-171">交易會以啟動的順序反轉，使最近啟動的交易一律為使用中狀態。</span><span class="sxs-lookup"><span data-stu-id="91e9d-171">Transactions become active in the reverse of order of which they are started, so that the most recently started transaction is always active.</span></span>

## <a name="subscribers-and-independent-transactions"></a><span data-ttu-id="91e9d-172">訂閱者與獨立交易</span><span class="sxs-lookup"><span data-stu-id="91e9d-172">SUBSCRIBERS AND INDEPENDENT TRANSACTIONS</span></span>

<span data-ttu-id="91e9d-173">如果您在另一個交易正在進行時啟動交易，則 PowerShell 預設不會啟動新的交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-173">If you start a transaction while another transaction is in progress, by default, PowerShell does not start a new transaction.</span></span> <span data-ttu-id="91e9d-174">相反地，它會將「訂閱者」新增至目前的交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-174">Instead, it adds a "subscriber" to the current transaction.</span></span>

<span data-ttu-id="91e9d-175">當交易有多個訂閱者時，在任何時間點的單一 Undo-Transaction 命令都會針對所有訂閱者回復整個交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-175">When a transaction has multiple subscribers, a single Undo-Transaction command at any point rolls back the entire transaction for all subscribers.</span></span> <span data-ttu-id="91e9d-176">不過，若要認可交易，您必須為每個訂閱者輸入 Complete-Transaction 命令。</span><span class="sxs-lookup"><span data-stu-id="91e9d-176">However, to commit the transaction, you must enter a Complete-Transaction command for every subscriber.</span></span>

<span data-ttu-id="91e9d-177">若要尋找交易的訂閱者數目，請檢查交易對象的 SubscriberCount 屬性。</span><span class="sxs-lookup"><span data-stu-id="91e9d-177">To find the number of subscribers to a transaction, check the SubscriberCount property of the transaction object.</span></span> <span data-ttu-id="91e9d-178">例如，下列命令會使用 Get-Transaction Cmdlet 來取得使用中交易的 SubscriberCount 屬性值：</span><span class="sxs-lookup"><span data-stu-id="91e9d-178">For example, the following command uses the Get-Transaction cmdlet to get the value of the SubscriberCount property of the active transaction:</span></span>

```powershell
(Get-Transaction).SubscriberCount
```

<span data-ttu-id="91e9d-179">加入訂閱者是預設行為，因為另一個交易正在進行時所啟動的大部分交易都與原始交易相關。</span><span class="sxs-lookup"><span data-stu-id="91e9d-179">Adding a subscriber is the default behavior because most transactions that are started while another transaction is in progress are related to the original transaction.</span></span> <span data-ttu-id="91e9d-180">在一般模型中，包含交易的腳本會呼叫包含其本身交易的 helper 腳本。</span><span class="sxs-lookup"><span data-stu-id="91e9d-180">In the typical model, a script that contains a transaction calls a helper script that contains its own transaction.</span></span> <span data-ttu-id="91e9d-181">因為交易是相關的，所以應該將它們回復或作為一個單位來認可。</span><span class="sxs-lookup"><span data-stu-id="91e9d-181">Because the transactions are related, they should be rolled back or committed as a unit.</span></span>

<span data-ttu-id="91e9d-182">不過，您可以使用 Start-Transaction Cmdlet 的獨立參數，來啟動與目前交易無關的交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-182">However, you can start a transaction that is independent of the current transaction by using the Independent parameter of the Start-Transaction cmdlet.</span></span>

<span data-ttu-id="91e9d-183">當您啟動獨立的交易時，Start-Transaction 會建立新的交易對象，而新的交易就會變成使用中的交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-183">When you start an independent transaction, Start-Transaction creates a new transaction object, and the new transaction becomes the active transaction.</span></span>
<span data-ttu-id="91e9d-184">您可以認可或回復獨立交易，而不會影響原始交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-184">The independent transaction can be committed or rolled back without affecting the original transaction.</span></span>

<span data-ttu-id="91e9d-185">當獨立交易完成 (認可或復原) 時，原始交易會再次成為使用中交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-185">When the independent transaction is finished (committed or rolled back), the original transaction becomes the active transaction again.</span></span>

## <a name="changing-data"></a><span data-ttu-id="91e9d-186">變更資料</span><span class="sxs-lookup"><span data-stu-id="91e9d-186">CHANGING DATA</span></span>

<span data-ttu-id="91e9d-187">當您使用交易來變更資料時，在認可交易之前，將不會變更受交易影響的資料。</span><span class="sxs-lookup"><span data-stu-id="91e9d-187">When you use transactions to change data, the data that is affected by the transaction is not changed until you commit the transaction.</span></span> <span data-ttu-id="91e9d-188">不過，相同的資料也可以由不屬於交易一部分的命令變更。</span><span class="sxs-lookup"><span data-stu-id="91e9d-188">However, the same data can be changed by commands that are not part of the transaction.</span></span>

<span data-ttu-id="91e9d-189">當您使用交易來管理共用資料時，請記住這一點。</span><span class="sxs-lookup"><span data-stu-id="91e9d-189">Keep this in mind when you are using transactions to manage shared data.</span></span>
<span data-ttu-id="91e9d-190">一般而言，資料庫具有在您處理資料時鎖定資料的機制，可防止其他使用者和其他命令、腳本和函式進行變更。</span><span class="sxs-lookup"><span data-stu-id="91e9d-190">Typically, databases have mechanisms that lock the data while you are working on it, preventing other users, and other commands, scripts, and functions, from changing it.</span></span>

<span data-ttu-id="91e9d-191">但是，鎖定是資料庫的一項功能。</span><span class="sxs-lookup"><span data-stu-id="91e9d-191">However, the lock is a feature of the database.</span></span> <span data-ttu-id="91e9d-192">它與交易無關。</span><span class="sxs-lookup"><span data-stu-id="91e9d-192">It is not related to transactions.</span></span> <span data-ttu-id="91e9d-193">如果您是在已啟用交易的檔案系統或其他資料存放區中工作，則可以在交易進行時變更資料。</span><span class="sxs-lookup"><span data-stu-id="91e9d-193">If you are working in a transaction-enabled file system or other data store, the data can be changed while the transaction is in progress.</span></span>

## <a name="examples"></a><span data-ttu-id="91e9d-194">範例</span><span class="sxs-lookup"><span data-stu-id="91e9d-194">EXAMPLES</span></span>

<span data-ttu-id="91e9d-195">本節中的範例會使用 PowerShell 登錄提供者，並假設您已熟悉它。</span><span class="sxs-lookup"><span data-stu-id="91e9d-195">The examples in this section use the PowerShell Registry provider and assume that you are familiar with it.</span></span> <span data-ttu-id="91e9d-196">如需登錄提供者的相關資訊，請輸入 "get-help Registry"。</span><span class="sxs-lookup"><span data-stu-id="91e9d-196">For information about the Registry provider, type "get-help registry".</span></span>

### <a name="example-1-committing-a-transaction"></a><span data-ttu-id="91e9d-197">範例1：認可交易</span><span class="sxs-lookup"><span data-stu-id="91e9d-197">EXAMPLE 1: COMMITTING A TRANSACTION</span></span>

<span data-ttu-id="91e9d-198">若要建立交易，請使用 Start-Transaction Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="91e9d-198">To create a transaction, use the Start-Transaction cmdlet.</span></span> <span data-ttu-id="91e9d-199">下列命令會以預設設定啟動交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-199">The following command starts a transaction with the default settings.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="91e9d-200">若要在交易中包含命令，請使用 Cmdlet 的 UseTransaction 參數。</span><span class="sxs-lookup"><span data-stu-id="91e9d-200">To include commands in the transaction, use the UseTransaction parameter of the cmdlet.</span></span> <span data-ttu-id="91e9d-201">根據預設，命令不會包含在交易中，</span><span class="sxs-lookup"><span data-stu-id="91e9d-201">By default, commands are not included in the transaction,</span></span>

<span data-ttu-id="91e9d-202">例如，下列命令會將 HKCU：磁片磁碟機的軟體金鑰中的目前位置設定為不包含在交易中。</span><span class="sxs-lookup"><span data-stu-id="91e9d-202">For example, the following command, which sets the current location in the Software key of the HKCU: drive, is not included in the transaction.</span></span>

```powershell
cd hkcu:\Software
```

<span data-ttu-id="91e9d-203">下列命令會建立 MyCompany 索引鍵，並使用 New-Item Cmdlet 的 UseTransaction 參數，將命令包含在使用中的交易中。</span><span class="sxs-lookup"><span data-stu-id="91e9d-203">The following command, which creates the MyCompany key, uses the UseTransaction parameter of the New-Item cmdlet to include the command in the active transaction.</span></span>

```powershell
new-item MyCompany -UseTransaction
```

<span data-ttu-id="91e9d-204">此命令會傳回代表新索引鍵的物件，但是因為此命令是交易的一部分，所以登錄尚未變更。</span><span class="sxs-lookup"><span data-stu-id="91e9d-204">The command returns an object that represents the new key, but because the command is part of the transaction, the registry is not yet changed.</span></span>

```
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 MyCompany                      {}
```

<span data-ttu-id="91e9d-205">若要認可交易，請使用 Complete-Transaction Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="91e9d-205">To commit the transaction, use the Complete-Transaction cmdlet.</span></span> <span data-ttu-id="91e9d-206">因為它一律會影響使用中的交易，所以您無法指定交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-206">Because it always affects the active transaction, you cannot specify the transaction.</span></span>

```powershell
complete-transaction
```

<span data-ttu-id="91e9d-207">如此一來，就會將 MyCompany 金鑰新增至登錄中。</span><span class="sxs-lookup"><span data-stu-id="91e9d-207">As a result, the MyCompany key is added to the registry.</span></span>

```powershell
dir m*
```

```output
Hive: HKEY_CURRENT_USER\software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   0 MyCompany                      {}
```

### <a name="example-2-rolling-back-a-transaction"></a><span data-ttu-id="91e9d-208">範例2：回復交易</span><span class="sxs-lookup"><span data-stu-id="91e9d-208">EXAMPLE 2: ROLLING BACK A TRANSACTION</span></span>

<span data-ttu-id="91e9d-209">若要建立交易，請使用 Start-Transaction Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="91e9d-209">To create a transaction, use the Start-Transaction cmdlet.</span></span> <span data-ttu-id="91e9d-210">下列命令會以預設設定啟動交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-210">The following command starts a transaction with the default settings.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="91e9d-211">下列命令會建立 MyOtherCompany 索引鍵，並使用 New-Item Cmdlet 的 UseTransaction 參數，將命令包含在使用中的交易中。</span><span class="sxs-lookup"><span data-stu-id="91e9d-211">The following command, which creates the MyOtherCompany key, uses the UseTransaction parameter of the New-Item cmdlet to include the command in the active transaction.</span></span>

```powershell
new-item MyOtherCompany -UseTransaction
```

<span data-ttu-id="91e9d-212">此命令會傳回代表新索引鍵的物件，但是因為此命令是交易的一部分，所以登錄尚未變更。</span><span class="sxs-lookup"><span data-stu-id="91e9d-212">The command returns an object that represents the new key, but because the command is part of the transaction, the registry is not yet changed.</span></span>

```
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 MyOtherCompany                 {}
```

<span data-ttu-id="91e9d-213">若要回復交易，請使用 Undo-Transaction Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="91e9d-213">To roll back the transaction, use the Undo-Transaction cmdlet.</span></span> <span data-ttu-id="91e9d-214">因為它一律會影響使用中的交易，所以您未指定交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-214">Because it always affects the active transaction, you do not specify the transaction.</span></span>

```powershell
Undo-transaction
```

<span data-ttu-id="91e9d-215">結果是 MyOtherCompany 機碼不會新增至登錄。</span><span class="sxs-lookup"><span data-stu-id="91e9d-215">The result is that the MyOtherCompany key is not added to the registry.</span></span>

```powershell
dir m*
```

```output
Hive: HKEY_CURRENT_USER\software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   0 MyCompany                      {}
```

### <a name="example-3-previewing-a-transaction"></a><span data-ttu-id="91e9d-216">範例3：預覽交易</span><span class="sxs-lookup"><span data-stu-id="91e9d-216">EXAMPLE 3: PREVIEWING A TRANSACTION</span></span>

<span data-ttu-id="91e9d-217">通常，交易中使用的命令會變更資料。</span><span class="sxs-lookup"><span data-stu-id="91e9d-217">Typically, the commands used in a transaction change data.</span></span> <span data-ttu-id="91e9d-218">不過，取得資料的命令也可用於交易中，因為它們會取得交易內的資料。</span><span class="sxs-lookup"><span data-stu-id="91e9d-218">However, the commands that get data are useful in a transaction, too, because they get data inside of the transaction.</span></span> <span data-ttu-id="91e9d-219">這會提供認可交易之變更的預覽。</span><span class="sxs-lookup"><span data-stu-id="91e9d-219">This provides a preview of the changes that committing the transaction would cause.</span></span>

<span data-ttu-id="91e9d-220">下列範例示範如何使用 Get-ChildItem 命令 (別名是 "dir" ) 來預覽交易中的變更。</span><span class="sxs-lookup"><span data-stu-id="91e9d-220">The following example shows how to use the Get-ChildItem command (the alias is "dir") to preview the changes in a transaction.</span></span>

<span data-ttu-id="91e9d-221">下列命令會啟動交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-221">The following command starts a transaction.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="91e9d-222">下列命令使用 New-ItemProperty Cmdlet 將 MyKey 登錄專案新增至 MyCompany 機碼。</span><span class="sxs-lookup"><span data-stu-id="91e9d-222">The following command uses the New-ItemProperty cmdlet to add the MyKey registry entry to the MyCompany key.</span></span> <span data-ttu-id="91e9d-223">此命令會使用 UseTransaction 參數將命令包含在交易中。</span><span class="sxs-lookup"><span data-stu-id="91e9d-223">The command uses the UseTransaction parameter to include the command in the transaction.</span></span>

```powershell
new-itemproperty -path MyCompany -Name MyKey -value 123 -UseTransaction
```

<span data-ttu-id="91e9d-224">此命令會傳回代表新登錄專案的物件，但不會變更登錄專案。</span><span class="sxs-lookup"><span data-stu-id="91e9d-224">The command returns an object representing the new registry entry, but the registry entry is not changed.</span></span>

```
MyKey
-----
123
```

<span data-ttu-id="91e9d-225">若要取得目前在登錄中的專案，請在不使用 UseTransaction 參數的情況下，使用 Get-ChildItem 命令 ( "dir" ) 。</span><span class="sxs-lookup"><span data-stu-id="91e9d-225">To get the items that are currently in the registry, use a Get-ChildItem command ("dir") without the UseTransaction parameter.</span></span> <span data-ttu-id="91e9d-226">下列命令會取得以 "M" 為開頭的專案。</span><span class="sxs-lookup"><span data-stu-id="91e9d-226">The following command gets items that begin with "M."</span></span>

```powershell
dir m*
```

<span data-ttu-id="91e9d-227">結果顯示尚未將任何專案加入至 MyCompany 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="91e9d-227">The result shows that no entries have yet been added to the MyCompany key.</span></span>

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   0 MyCompany                      {}
```

<span data-ttu-id="91e9d-228">若要預覽認可交易的效果，請使用 UseTransaction 參數輸入 Get-ChildItem ( "dir" ) 命令。</span><span class="sxs-lookup"><span data-stu-id="91e9d-228">To preview the effect of committing the transaction, enter a Get-ChildItem ("dir") command with the UseTransaction parameter.</span></span> <span data-ttu-id="91e9d-229">此命令會查看交易內的資料。</span><span class="sxs-lookup"><span data-stu-id="91e9d-229">This command has a view of the data from within the transaction.</span></span>

```powershell
dir m* -useTransaction
```

<span data-ttu-id="91e9d-230">結果顯示，如果認可交易，則 MyKey 專案會新增至 MyCompany 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="91e9d-230">The result shows that, if the transaction is committed, the MyKey entry will be added to the MyCompany key.</span></span>

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   1 MyCompany                      {MyKey}
```

### <a name="example-4-combining-transacted-and-non-transacted-commands"></a><span data-ttu-id="91e9d-231">範例4：合併交易與非交易命令</span><span class="sxs-lookup"><span data-stu-id="91e9d-231">EXAMPLE 4: COMBINING TRANSACTED AND NON-TRANSACTED COMMANDS</span></span>

<span data-ttu-id="91e9d-232">您可以在交易期間輸入非交易命令。</span><span class="sxs-lookup"><span data-stu-id="91e9d-232">You can enter non-transacted commands during a transaction.</span></span> <span data-ttu-id="91e9d-233">非交易命令會立即影響資料，但不會影響交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-233">The non-transacted commands affect the data immediately, but they do not affect the transaction.</span></span>
<span data-ttu-id="91e9d-234">下列命令會在 HKCU： \ Software 登錄機碼中啟動交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-234">The following command starts a transaction in the HKCU:\Software registry key.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="91e9d-235">接下來的三個命令會使用 New-Item Cmdlet，將金鑰新增至登錄。</span><span class="sxs-lookup"><span data-stu-id="91e9d-235">The next three commands use the New-Item cmdlet to add keys to the registry.</span></span>
<span data-ttu-id="91e9d-236">第一個和第三個命令使用 UseTransaction 參數將命令包含在交易中。</span><span class="sxs-lookup"><span data-stu-id="91e9d-236">The first and third commands use the UseTransaction parameter to include the commands in the transaction.</span></span> <span data-ttu-id="91e9d-237">第二個命令會省略參數。</span><span class="sxs-lookup"><span data-stu-id="91e9d-237">The second command omits the parameter.</span></span> <span data-ttu-id="91e9d-238">因為第二個命令未包含在交易中，所以它會立即生效。</span><span class="sxs-lookup"><span data-stu-id="91e9d-238">Because the second command is not included in the transaction, it is effective immediately.</span></span>

```powershell
new-item MyCompany1 -UseTransaction
new-item MyCompany2
new-item MyCompany3 -UseTransaction
```

<span data-ttu-id="91e9d-239">若要查看登錄的目前狀態，請使用 Get-ChildItem ( "dir" ) 命令，而不使用 UseTransaction 參數。</span><span class="sxs-lookup"><span data-stu-id="91e9d-239">To view the current state of the registry, use a Get-ChildItem ("dir") command without the UseTransaction parameter.</span></span> <span data-ttu-id="91e9d-240">此命令會取得以 "M" 為開頭的專案。</span><span class="sxs-lookup"><span data-stu-id="91e9d-240">This command gets items that begin with "M."</span></span>

```powershell
dir m*
```

<span data-ttu-id="91e9d-241">結果會顯示 MyCompany2 索引鍵已新增至登錄，但不會新增 MyCompany1 和 MyCompany3 索引鍵（屬於交易的一部分）。</span><span class="sxs-lookup"><span data-stu-id="91e9d-241">The result shows that the MyCompany2 key is added to the registry, but the MyCompany1 and MyCompany3 keys, which are part of the transaction, are not added.</span></span>

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0    0 MyCompany2                     {}
```

<span data-ttu-id="91e9d-242">下列命令會認可交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-242">The following command commits the transaction.</span></span>

```powershell
complete-transaction
```

<span data-ttu-id="91e9d-243">現在，新增為交易一部分的金鑰會出現在登錄中。</span><span class="sxs-lookup"><span data-stu-id="91e9d-243">Now, the keys that were added as part of the transaction appear in the registry.</span></span>

```powershell
dir m*
```

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
83   1 Microsoft                      {(default)}
0    0 MyCompany1                     {}
0    0 MyCompany2                     {}
0    0 MyCompany3                     {}
```

### <a name="example-5-using-automatic-rollback"></a><span data-ttu-id="91e9d-244">範例5：使用自動回復</span><span class="sxs-lookup"><span data-stu-id="91e9d-244">EXAMPLE 5: USING AUTOMATIC ROLLBACK</span></span>

<span data-ttu-id="91e9d-245">當交易中的命令產生任何種類的錯誤時，就會自動回復交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-245">When a command in a transaction generates an error of any kind, the transaction is automatically rolled back.</span></span>

<span data-ttu-id="91e9d-246">此預設行為是針對執行交易的腳本所設計。</span><span class="sxs-lookup"><span data-stu-id="91e9d-246">This default behavior is designed for scripts that run transactions.</span></span> <span data-ttu-id="91e9d-247">腳本通常經過妥善測試，並包含錯誤處理邏輯，因此不會發生錯誤，而且應該終止交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-247">Scripts are typically well tested and include error-handling logic, so errors are not expected and should terminate the transaction.</span></span>

<span data-ttu-id="91e9d-248">第一個命令會在 HKCU： \ Software 登錄機碼中啟動交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-248">The first command starts a transaction in the HKCU:\Software registry key.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="91e9d-249">下列命令使用 New-Item Cmdlet 將 MyCompany 機碼新增至登錄。</span><span class="sxs-lookup"><span data-stu-id="91e9d-249">The following command uses the New-Item cmdlet to add the MyCompany key to the registry.</span></span> <span data-ttu-id="91e9d-250">此命令會使用 UseTransaction 參數 (別名是 "usetx" ) 將命令包含在交易中。</span><span class="sxs-lookup"><span data-stu-id="91e9d-250">The command uses the UseTransaction parameter (the alias is "usetx") to include the command in the transaction.</span></span>

```powershell
New-Item MyCompany -UseTX
```

<span data-ttu-id="91e9d-251">因為 MyCompany 索引鍵已經存在於登錄中，所以命令會失敗，並回復交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-251">Because the MyCompany key already exists in the registry, the command fails, and the transaction is rolled back.</span></span>

```output
New-Item : A key at this path already exists
At line:1 char:9
+ new-item <<<<  MyCompany -usetx
```

<span data-ttu-id="91e9d-252">Get-Transaction 命令會確認交易已回復，且 SubscriberCount 為0。</span><span class="sxs-lookup"><span data-stu-id="91e9d-252">A Get-Transaction command confirms that the transaction has been rolled back and that the SubscriberCount is 0.</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                0                 RolledBack
```

### <a name="example-6-changing-the-rollback-preference"></a><span data-ttu-id="91e9d-253">範例6：變更復原喜好設定</span><span class="sxs-lookup"><span data-stu-id="91e9d-253">EXAMPLE 6: CHANGING THE ROLLBACK PREFERENCE</span></span>

<span data-ttu-id="91e9d-254">如果您希望交易更有容錯能力，可以使用 Start-Transaction 的 RollbackPreference 參數來變更喜好設定。</span><span class="sxs-lookup"><span data-stu-id="91e9d-254">If you want the transaction to be more error tolerant, you can use the RollbackPreference parameter of Start-Transaction to change the preference.</span></span>

<span data-ttu-id="91e9d-255">下列命令會啟動復原喜好設定為 "Never" 的交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-255">The following command starts a transaction with a rollback preference of "Never".</span></span>

```powershell
start-transaction -rollbackpreference Never
```

<span data-ttu-id="91e9d-256">在此情況下，當命令失敗時，不會自動回復交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-256">In this case, when the command fails, the transaction is not automatically rolled back.</span></span>

```powershell
New-Item MyCompany -UseTX
```

```output
New-Item : A key at this path already exists
At line:1 char:9
+ new-item <<<<  MyCompany -usetx
```

<span data-ttu-id="91e9d-257">因為交易仍在使用中，所以您可以將命令重新提交為交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="91e9d-257">Because the transaction is still active, you can resubmit the command as part of the transaction.</span></span>

```powershell
New-Item MyOtherCompany -UseTX
```

### <a name="example-7-using-the-use-transaction-cmdlet"></a><span data-ttu-id="91e9d-258">範例7：使用使用-TRANSACTION CMDLET</span><span class="sxs-lookup"><span data-stu-id="91e9d-258">EXAMPLE 7: USING THE USE-TRANSACTION CMDLET</span></span>

<span data-ttu-id="91e9d-259">Use-Transaction Cmdlet 可讓您針對已啟用交易的 Microsoft .NET Framework 物件執行直接腳本處理。</span><span class="sxs-lookup"><span data-stu-id="91e9d-259">The Use-Transaction cmdlet enables you to do direct scripting against transaction-enabled Microsoft .NET Framework objects.</span></span> <span data-ttu-id="91e9d-260">Use-Transaction 會採用只能包含命令的腳本區塊，以及使用啟用交易 .NET Framework 物件的運算式，例如 TransactedString 類別的實例。</span><span class="sxs-lookup"><span data-stu-id="91e9d-260">Use-Transaction takes a script block that can only contain commands and expressions that use transaction-enabled .NET Framework objects, such as instances of the Microsoft.PowerShell.Commands.Management.TransactedString class.</span></span>

<span data-ttu-id="91e9d-261">下列命令會啟動交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-261">The following command starts a transaction.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="91e9d-262">下列 New-Object 命令會建立 TransactedString 類別的實例，並將它儲存在 $t 變數中。</span><span class="sxs-lookup"><span data-stu-id="91e9d-262">The following New-Object command creates an instance of the TransactedString class and saves it in the $t variable.</span></span>

```powershell
$t = New-Object Microsoft.PowerShell.Commands.Management.TransactedString
```

<span data-ttu-id="91e9d-263">下列命令會使用 TransactedString 物件的 Append 方法將文字新增至字串。</span><span class="sxs-lookup"><span data-stu-id="91e9d-263">The following command uses the Append method of the TransactedString object to add text to the string.</span></span> <span data-ttu-id="91e9d-264">因為此命令不是交易的一部分，所以變更會立即生效。</span><span class="sxs-lookup"><span data-stu-id="91e9d-264">Because the command is not part of the transaction, the change is effective immediately.</span></span>

```powershell
$t.append("Windows")
```

<span data-ttu-id="91e9d-265">下列命令使用相同的 Append 方法來加入文字，但它會將文字新增為交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="91e9d-265">The following command uses the same Append method to add text, but it adds the text as part of the transaction.</span></span> <span data-ttu-id="91e9d-266">此命令會以大括弧括住，並設定為使用-Transaction 的 ScriptBlock 參數值。</span><span class="sxs-lookup"><span data-stu-id="91e9d-266">The command is enclosed in braces, and it is set as the value of the ScriptBlock parameter of Use-Transaction.</span></span> <span data-ttu-id="91e9d-267">需要 (UseTx) 的 UseTransaction 參數。</span><span class="sxs-lookup"><span data-stu-id="91e9d-267">The UseTransaction parameter (UseTx) is required.</span></span>

```powershell
use-transaction {$t.append(" PowerShell")} -usetx
```

<span data-ttu-id="91e9d-268">若要查看 $t 中交易字串的目前內容，請使用 TransactedString 物件的 ToString 方法。</span><span class="sxs-lookup"><span data-stu-id="91e9d-268">To see the current content of the transacted string in $t, use the ToString method of the TransactedString object.</span></span>

```powershell
$t.tostring()
```

<span data-ttu-id="91e9d-269">輸出顯示只有非交易的變更會生效。</span><span class="sxs-lookup"><span data-stu-id="91e9d-269">The output shows that only the non-transacted changes are effective.</span></span>

```output
Windows
```

<span data-ttu-id="91e9d-270">若要從交易內查看 $t 中交易字串的目前內容，請在 Use-Transaction 命令中內嵌運算式。</span><span class="sxs-lookup"><span data-stu-id="91e9d-270">To see the current content of the transacted string in $t from within the transaction, embed the expression in a Use-Transaction command.</span></span>

```powershell
use-transaction {$s.tostring()} -usetx
```

<span data-ttu-id="91e9d-271">輸出會顯示交易視圖。</span><span class="sxs-lookup"><span data-stu-id="91e9d-271">The output shows the transaction view.</span></span>

```output
PowerShell
```

<span data-ttu-id="91e9d-272">下列命令會認可交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-272">The following command commits the transaction.</span></span>

```powershell
complete-transaction
```

<span data-ttu-id="91e9d-273">若要查看最終字串：</span><span class="sxs-lookup"><span data-stu-id="91e9d-273">To see the final string:</span></span>

```
$t.tostring()
PowerShell
```

### <a name="example-8-managing-multi-subscriber-transactions"></a><span data-ttu-id="91e9d-274">範例8：管理多訂閱者交易</span><span class="sxs-lookup"><span data-stu-id="91e9d-274">EXAMPLE 8: MANAGING MULTI-SUBSCRIBER TRANSACTIONS</span></span>

<span data-ttu-id="91e9d-275">當您在另一個交易正在進行時啟動交易時，PowerShell 預設不會建立第二筆交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-275">When you start a transaction while another transaction is in progress, PowerShell does not create a second transaction by default.</span></span> <span data-ttu-id="91e9d-276">相反地，它會將訂閱者加入目前的交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-276">Instead, it adds a subscriber to the current transaction.</span></span>

<span data-ttu-id="91e9d-277">此範例顯示如何查看和管理多訂閱者交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-277">This example shows how to view and manage a multi-subscriber transaction.</span></span>

<span data-ttu-id="91e9d-278">從在 HKCU： \ Software 金鑰中啟動交易開始。</span><span class="sxs-lookup"><span data-stu-id="91e9d-278">Begin by starting a transaction in the HKCU:\Software key.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="91e9d-279">下列命令使用 Get-Transaction 命令來取得使用中的交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-279">The following command uses the Get-Transaction command to get the active transaction.</span></span>

```powershell
get-transaction
```

<span data-ttu-id="91e9d-280">結果會顯示代表使用中交易的物件。</span><span class="sxs-lookup"><span data-stu-id="91e9d-280">The result shows the object that represents the active transaction.</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

<span data-ttu-id="91e9d-281">下列命令會將 MyCompany 機碼新增至登錄。</span><span class="sxs-lookup"><span data-stu-id="91e9d-281">The following command adds the MyCompany key to the registry.</span></span> <span data-ttu-id="91e9d-282">此命令會使用 UseTransaction 參數將命令包含在交易中。</span><span class="sxs-lookup"><span data-stu-id="91e9d-282">The command uses the UseTransaction parameter to include the command in the transaction.</span></span>

```powershell
new-item MyCompany -UseTransaction
```

<span data-ttu-id="91e9d-283">下列命令使用 Start-Transaction 命令來啟動交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-283">The following command uses the Start-Transaction command to start a transaction.</span></span> <span data-ttu-id="91e9d-284">雖然此命令是在命令提示字元中輸入的，但當您執行包含交易的腳本時，可能會發生此情況。</span><span class="sxs-lookup"><span data-stu-id="91e9d-284">Although this command is typed at the command prompt, this scenario is more likely to happen when you run a script that contains a transaction.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="91e9d-285">Get-Transaction 命令顯示交易對象上的訂閱者計數會遞增。</span><span class="sxs-lookup"><span data-stu-id="91e9d-285">A Get-Transaction command shows that the subscriber count on the transaction object is incremented.</span></span> <span data-ttu-id="91e9d-286">值現在是2。</span><span class="sxs-lookup"><span data-stu-id="91e9d-286">The value is now 2.</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                2                 Active
```

<span data-ttu-id="91e9d-287">下一個命令會使用 New-ItemProperty Cmdlet 將 MyKey 登錄專案新增至 MyCompany 機碼。</span><span class="sxs-lookup"><span data-stu-id="91e9d-287">The next command uses the New-ItemProperty cmdlet to add the MyKey registry entry to the MyCompany key.</span></span> <span data-ttu-id="91e9d-288">它會使用 UseTransaction 參數將命令包含在交易中。</span><span class="sxs-lookup"><span data-stu-id="91e9d-288">It uses the UseTransaction parameter to include the command in the transaction.</span></span>

```powershell
new-itemproperty -path MyCompany -name MyKey -UseTransaction
```

<span data-ttu-id="91e9d-289">MyCompany 索引鍵不存在於登錄中，但此命令會成功，因為這兩個命令是相同交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="91e9d-289">The MyCompany key does not exist in the registry, but this command succeeds because the two commands are part of the same transaction.</span></span>

<span data-ttu-id="91e9d-290">下列命令會認可交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-290">The following command commits the transaction.</span></span> <span data-ttu-id="91e9d-291">如果回復交易，則會針對所有訂閱者回復交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-291">If it rolled back the transaction, the transaction would be rolled back for all the subscribers.</span></span>

```powershell
complete-transaction
```

<span data-ttu-id="91e9d-292">Get-Transaction 命令顯示交易對象上的訂閱者計數為1，但狀態的值仍處於作用中， (未認可) 。</span><span class="sxs-lookup"><span data-stu-id="91e9d-292">A Get-Transaction command shows that the subscriber count on the transaction object is 1, but the value of Status is still Active (not Committed).</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

<span data-ttu-id="91e9d-293">若要完成認可交易，請輸入第二個完整交易命令。</span><span class="sxs-lookup"><span data-stu-id="91e9d-293">To finish committing the transaction, enter a second Complete- Transaction command.</span></span> <span data-ttu-id="91e9d-294">若要認可多訂閱者交易，您必須為每個 Start-Transaction 命令輸入一個 Complete-Transaction 命令。</span><span class="sxs-lookup"><span data-stu-id="91e9d-294">To commit a multi-subscriber transaction, you must enter one Complete-Transaction command for each Start-Transaction command.</span></span>

```powershell
complete-transaction
```

<span data-ttu-id="91e9d-295">另一個 Get-Transaction 命令顯示交易已認可。</span><span class="sxs-lookup"><span data-stu-id="91e9d-295">Another Get-Transaction command shows that the transaction has been committed.</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                0                 Committed
```

### <a name="example-9-managing-independent-transactions"></a><span data-ttu-id="91e9d-296">範例9：管理獨立交易</span><span class="sxs-lookup"><span data-stu-id="91e9d-296">EXAMPLE 9: MANAGING INDEPENDENT TRANSACTIONS</span></span>

<span data-ttu-id="91e9d-297">當您在另一個交易正在進行時啟動交易時，您可以使用 Start-Transaction 的獨立參數，讓新交易與原始交易無關。</span><span class="sxs-lookup"><span data-stu-id="91e9d-297">When you start a transaction while another transaction is in progress, you can use the Independent parameter of Start-Transaction to make the new transaction independent of the original transaction.</span></span>

<span data-ttu-id="91e9d-298">當您這樣做時，Start-Transaction 會建立新的交易對象，並讓新交易成為使用中的交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-298">When you do, Start-Transaction creates a new transaction object and makes the new transaction the active transaction.</span></span>

<span data-ttu-id="91e9d-299">從在 HKCU： Software 金鑰中啟動交易開始 \\ 。</span><span class="sxs-lookup"><span data-stu-id="91e9d-299">Begin by starting a transaction in the HKCU:\\Software key.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="91e9d-300">下列命令使用 Get-Transaction 命令來取得使用中的交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-300">The following command uses the Get-Transaction command to get the active transaction.</span></span>

```powershell
get-transaction
```

<span data-ttu-id="91e9d-301">結果會顯示代表使用中交易的物件。</span><span class="sxs-lookup"><span data-stu-id="91e9d-301">The result shows the object that represents the active transaction.</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

<span data-ttu-id="91e9d-302">下列命令會將 MyCompany 登錄機碼新增為交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="91e9d-302">The following command adds the MyCompany registry key as part of the transaction.</span></span> <span data-ttu-id="91e9d-303">它會使用 UseTransaction 參數 (UseTx) 將命令包含在使用中的交易中。</span><span class="sxs-lookup"><span data-stu-id="91e9d-303">It uses the UseTransaction parameter (UseTx) to include the command in the active transaction.</span></span>

```powershell
new-item MyCompany -use
```

<span data-ttu-id="91e9d-304">下列命令會啟動新的交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-304">The following command starts a new transaction.</span></span> <span data-ttu-id="91e9d-305">此命令會使用獨立參數，表示此交易不是使用中交易的訂閱者。</span><span class="sxs-lookup"><span data-stu-id="91e9d-305">The command uses the Independent parameter to indicate that this transaction is not a subscriber to the active transaction.</span></span>

```powershell
start-transaction -independent
```

<span data-ttu-id="91e9d-306">當您建立獨立的交易時，最近建立的新 () 交易會成為使用中的交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-306">When you create an independent transaction, the new (most-recently created) transaction becomes the active transaction.</span></span> <span data-ttu-id="91e9d-307">您可以使用 Get-Transaction 命令來取得使用中的交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-307">You can use a Get-Transaction command to get the active transaction.</span></span>

```powershell
get-transaction
```

<span data-ttu-id="91e9d-308">請注意，交易的 SubscriberCount 是1，表示沒有其他訂閱者，而且交易是新的。</span><span class="sxs-lookup"><span data-stu-id="91e9d-308">Note that the SubscriberCount of the transaction is 1, indicating that there are no other subscribers and that the transaction is new.</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

<span data-ttu-id="91e9d-309">必須先完成新交易 (認可或復原) ，才能管理原始交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-309">The new transaction must be finished (either committed or rolled back) before you can manage the original transaction.</span></span>

<span data-ttu-id="91e9d-310">下列命令會將 MyOtherCompany 機碼新增至登錄。</span><span class="sxs-lookup"><span data-stu-id="91e9d-310">The following command adds the MyOtherCompany key to the registry.</span></span> <span data-ttu-id="91e9d-311">它會使用 UseTransaction 參數 (UseTx) 將命令包含在使用中的交易中。</span><span class="sxs-lookup"><span data-stu-id="91e9d-311">It uses the UseTransaction parameter (UseTx) to include the command in the active transaction.</span></span>

```powershell
new-item MyOtherCompany -usetx
```

<span data-ttu-id="91e9d-312">現在，回復交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-312">Now, roll back the transaction.</span></span> <span data-ttu-id="91e9d-313">如果有兩個訂閱者的單一交易，回復交易會針對所有訂閱者回復整個交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-313">If there were a single transaction with two subscribers, rolling back the transaction would roll back the entire transaction for all the subscribers.</span></span>

<span data-ttu-id="91e9d-314">不過，因為這些交易是獨立的，所以回復最新的交易會取消登錄的變更，並讓原始交易成為使用中的交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-314">However, because these transactions are independent, rolling back the newest transaction cancels the registry changes and makes the original transaction the active transaction.</span></span>

```powershell
undo-transaction
```

<span data-ttu-id="91e9d-315">Get-Transaction 命令會確認原始交易在會話中仍為使用中狀態。</span><span class="sxs-lookup"><span data-stu-id="91e9d-315">A Get-Transaction command confirms that the original transaction is still active in the session.</span></span>

```powershell
get-transaction
```

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

<span data-ttu-id="91e9d-316">下列命令會認可使用中交易。</span><span class="sxs-lookup"><span data-stu-id="91e9d-316">The following command commits the active transaction.</span></span>

```powershell
complete-transaction
```

<span data-ttu-id="91e9d-317">Get-ChildItem 命令顯示登錄已經變更。</span><span class="sxs-lookup"><span data-stu-id="91e9d-317">A Get-ChildItem command shows that the registry has been changed.</span></span>

```powershell
dir m*
```

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   0 MyCompany                      {}
```

## <a name="see-also"></a><span data-ttu-id="91e9d-318">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91e9d-318">SEE ALSO</span></span>

[<span data-ttu-id="91e9d-319">Start-Transaction</span><span class="sxs-lookup"><span data-stu-id="91e9d-319">Start-Transaction</span></span>](xref:Microsoft.PowerShell.Management.Start-Transaction)

[<span data-ttu-id="91e9d-320">Get-Transaction</span><span class="sxs-lookup"><span data-stu-id="91e9d-320">Get-Transaction</span></span>](xref:Microsoft.PowerShell.Management.Get-Transaction)

[<span data-ttu-id="91e9d-321">Complete-Transaction</span><span class="sxs-lookup"><span data-stu-id="91e9d-321">Complete-Transaction</span></span>](xref:Microsoft.PowerShell.Management.Complete-Transaction)

[<span data-ttu-id="91e9d-322">Undo-Transaction</span><span class="sxs-lookup"><span data-stu-id="91e9d-322">Undo-Transaction</span></span>](xref:Microsoft.PowerShell.Management.Undo-Transaction)

[<span data-ttu-id="91e9d-323">Use-Transaction</span><span class="sxs-lookup"><span data-stu-id="91e9d-323">Use-Transaction</span></span>](xref:Microsoft.PowerShell.Management.Use-Transaction)

[<span data-ttu-id="91e9d-324">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="91e9d-324">Get-PSProvider</span></span>](xref:Microsoft.PowerShell.Management.Get-PSProvider)

[<span data-ttu-id="91e9d-325">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="91e9d-325">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

[<span data-ttu-id="91e9d-326">about_Providers</span><span class="sxs-lookup"><span data-stu-id="91e9d-326">about_Providers</span></span>](about_Providers.md)
