---
title: Cmdlet 錯誤報表 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error records [PowerShell], terminating
- non-terminating errors [PowerShell]
- error records [PowerShell]
- terminating errors [PowerShell]
- error records [PowerShell], non-terminating
ms.assetid: 0b014035-52ea-44cb-ab38-bbe463c5465a
caps.latest.revision: 8
ms.openlocfilehash: 5dfec318438ca139518c596011ac5e56445738ea
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365917"
---
# <a name="cmdlet-error-reporting"></a><span data-ttu-id="41ee0-102">Cmdlet 錯誤報表</span><span class="sxs-lookup"><span data-stu-id="41ee0-102">Cmdlet error reporting</span></span>

<span data-ttu-id="41ee0-103">Cmdlet 應該根據錯誤是終止錯誤還是非終止錯誤，以不同的方式報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="41ee0-103">Cmdlets should report errors differently depending on whether the errors are terminating errors or nonterminating errors.</span></span> <span data-ttu-id="41ee0-104">終止錯誤是導致管線立即終止的錯誤，或在沒有理由繼續處理時所發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="41ee0-104">Terminating errors are errors that cause the pipeline to be terminated immediately, or errors that occur when there's no reason to continue processing.</span></span> <span data-ttu-id="41ee0-105">非終止錯誤是報告目前錯誤狀況的錯誤，但 Cmdlet 可以繼續處理輸入物件。</span><span class="sxs-lookup"><span data-stu-id="41ee0-105">Nonterminating errors are those errors that report a current error condition, but the cmdlet can continue to process input objects.</span></span> <span data-ttu-id="41ee0-106">發生非終止錯誤時，使用者通常會收到問題的通知，但此 Cmdlet 會繼續處理下一個輸入物件。</span><span class="sxs-lookup"><span data-stu-id="41ee0-106">With nonterminating errors, the user is typically notified of the problem, but the cmdlet continues to process the next input object.</span></span>

## <a name="terminating-and-nonterminating-errors"></a><span data-ttu-id="41ee0-107">終止和非終止錯誤</span><span class="sxs-lookup"><span data-stu-id="41ee0-107">Terminating and nonterminating errors</span></span>

<span data-ttu-id="41ee0-108">下列指導方針可用於判斷錯誤狀況是終止錯誤或非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="41ee0-108">The following guidelines can be used to determine if an error condition is a terminating error or a nonterminating error.</span></span>

- <span data-ttu-id="41ee0-109">錯誤狀況是否會讓您的 Cmdlet 無法成功處理任何進一步的輸入物件？</span><span class="sxs-lookup"><span data-stu-id="41ee0-109">Does the error condition prevent your cmdlet from successfully processing any further input objects?</span></span> <span data-ttu-id="41ee0-110">若是如此，這就是終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="41ee0-110">If so, this is a terminating error.</span></span>

- <span data-ttu-id="41ee0-111">是否有與特定輸入物件或輸入物件子集相關的錯誤狀況？</span><span class="sxs-lookup"><span data-stu-id="41ee0-111">Is the error condition related to a specific input object or a subset of input objects?</span></span> <span data-ttu-id="41ee0-112">若是如此，這就是非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="41ee0-112">If so, this is a nonterminating error.</span></span>

- <span data-ttu-id="41ee0-113">Cmdlet 是否接受多個輸入物件，讓處理常式在另一個輸入物件上可能會成功？</span><span class="sxs-lookup"><span data-stu-id="41ee0-113">Does the cmdlet accept multiple input objects, such that processing may succeed on another input object?</span></span> <span data-ttu-id="41ee0-114">若是如此，這就是非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="41ee0-114">If so, this is a nonterminating error.</span></span>

- <span data-ttu-id="41ee0-115">可以接受多個輸入物件的 Cmdlet 應該決定什麼是終止和非終止錯誤，即使特定情況僅適用于單一輸入物件也是如此。</span><span class="sxs-lookup"><span data-stu-id="41ee0-115">Cmdlets that can accept multiple input objects should decide between what are terminating and nonterminating errors, even when a particular situation applies to only a single input object.</span></span>

- <span data-ttu-id="41ee0-116">Cmdlet 可以在擲回終止例外狀況之前，接收任意數目的輸入物件，並傳送任何數目的成功或錯誤物件。</span><span class="sxs-lookup"><span data-stu-id="41ee0-116">Cmdlets can receive any number of input objects and send any number of success or error objects before throwing a terminating exception.</span></span> <span data-ttu-id="41ee0-117">接收的輸入物件數目與傳送的成功和錯誤物件之間沒有任何關聯性。</span><span class="sxs-lookup"><span data-stu-id="41ee0-117">There's no relationship between the number of input objects received and the number of success and error objects sent.</span></span>

- <span data-ttu-id="41ee0-118">只能接受0-1 輸入物件和只產生0-1 輸出物件的 Cmdlet 應該將錯誤視為終止錯誤，並產生終止例外狀況。</span><span class="sxs-lookup"><span data-stu-id="41ee0-118">Cmdlets that can accept only 0-1 input objects and generate only 0-1 output objects should treat errors as terminating errors and generate terminating exceptions.</span></span>

## <a name="reporting-nonterminating-errors"></a><span data-ttu-id="41ee0-119">報告非終止錯誤</span><span class="sxs-lookup"><span data-stu-id="41ee0-119">Reporting nonterminating errors</span></span>

<span data-ttu-id="41ee0-120">非終止錯誤的報告應一律在 Cmdlet 的[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法、 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法或 system.servicemodel 方法的執行中完成。（可能為 system. 管理元件），或[系統管理](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)元件（EndProcessing）方法。</span><span class="sxs-lookup"><span data-stu-id="41ee0-120">The reporting of a nonterminating error should always be done within the cmdlet's implementation of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, or the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="41ee0-121">這些類型的錯誤會藉由呼叫[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法來回報，然後再將錯誤記錄傳送至錯誤資料流程。</span><span class="sxs-lookup"><span data-stu-id="41ee0-121">These types of errors are reported by calling the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method that in turn sends an error record to the error stream.</span></span>

## <a name="reporting-terminating-errors"></a><span data-ttu-id="41ee0-122">報告終止錯誤</span><span class="sxs-lookup"><span data-stu-id="41ee0-122">Reporting terminating errors</span></span>

<span data-ttu-id="41ee0-123">終止錯誤會藉由擲回例外狀況或藉由呼叫[ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)方法來回報。</span><span class="sxs-lookup"><span data-stu-id="41ee0-123">Terminating errors are reported by throwing exceptions or by calling the [System.Management.Automation.Cmdlet.ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) method.</span></span> <span data-ttu-id="41ee0-124">請注意，Cmdlet 也可以攔截並重新擲回例外狀況（例如**OutOfMemory**），不過，它們不需要重新擲回例外狀況，因為 PowerShell 執行時間也會加以攔截。</span><span class="sxs-lookup"><span data-stu-id="41ee0-124">Be aware that cmdlets can also catch and rethrow exceptions such as **OutOfMemory**, however, they aren't required to rethrow exceptions as the PowerShell runtime will catch them as well.</span></span>

<span data-ttu-id="41ee0-125">您也可以針對您的情況特定的問題定義自己的例外狀況，或使用其錯誤記錄將其他資訊新增至現有的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="41ee0-125">You can also define your own exceptions for issues specific to your situation, or add additional information to an existing exception using its error record.</span></span>

## <a name="error-records"></a><span data-ttu-id="41ee0-126">錯誤記錄</span><span class="sxs-lookup"><span data-stu-id="41ee0-126">Error records</span></span>

<span data-ttu-id="41ee0-127">PowerShell 描述[ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)物件的非終止錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="41ee0-127">PowerShell describes a nonterminating error condition with [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objects.</span></span> <span data-ttu-id="41ee0-128">每個物件都會提供錯誤類別目錄資訊、選擇性的目標物件，以及有關錯誤狀況的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="41ee0-128">Each object provides error category information, an optional target object, and details about the error condition.</span></span>

### <a name="error-identifiers"></a><span data-ttu-id="41ee0-129">錯誤識別碼</span><span class="sxs-lookup"><span data-stu-id="41ee0-129">Error identifiers</span></span>

<span data-ttu-id="41ee0-130">錯誤識別碼是一個簡單字串，可識別 Cmdlet 內的錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="41ee0-130">The error identifier is a simple string that identifies the error condition within the cmdlet.</span></span>
<span data-ttu-id="41ee0-131">PowerShell 會將此識別碼與 Cmdlet 識別碼結合，以建立可在稍後篩選錯誤資料流程或記錄錯誤時、回應特定錯誤時，或其他使用者特定活動時使用的完整錯誤識別碼。</span><span class="sxs-lookup"><span data-stu-id="41ee0-131">PowerShell combines this identifier with a cmdlet identifier to create a fully qualified error identifier that can be used later when filtering error streams or logging errors, when responding to specific errors, or with other user-specific activities.</span></span>

<span data-ttu-id="41ee0-132">指定錯誤識別碼時，應遵循下列指導方針：</span><span class="sxs-lookup"><span data-stu-id="41ee0-132">The following guidelines should be followed when specifying error identifiers:</span></span>

- <span data-ttu-id="41ee0-133">將不同、高度特定的錯誤識別碼指派給不同的程式碼路徑。</span><span class="sxs-lookup"><span data-stu-id="41ee0-133">Assign different, highly specific, error identifiers to different code paths.</span></span> <span data-ttu-id="41ee0-134">每個呼叫[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)或[ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)的程式碼路徑，都應該有自己的錯誤識別碼。（可能為）。</span><span class="sxs-lookup"><span data-stu-id="41ee0-134">Each code path that calls [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) or [System.Management.Automation.Cmdlet.ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) should have its own error identifier.</span></span>

- <span data-ttu-id="41ee0-135">對於終止和非終止錯誤而言，錯誤識別碼應該是 Common Language Runtime （CLR）例外狀況類型的唯一。</span><span class="sxs-lookup"><span data-stu-id="41ee0-135">Error identifiers should be unique to Common Language Runtime (CLR) exception types for both terminating and nonterminating errors.</span></span>

- <span data-ttu-id="41ee0-136">請勿變更 Cmdlet 或 PowerShell 提供者版本之間的錯誤識別碼的語法。</span><span class="sxs-lookup"><span data-stu-id="41ee0-136">Don't change the semantics of an error identifier between versions of your cmdlet or PowerShell provider.</span></span> <span data-ttu-id="41ee0-137">建立錯誤識別碼的語義之後，它應該會在 Cmdlet 的整個生命週期中保持不變。</span><span class="sxs-lookup"><span data-stu-id="41ee0-137">After the semantics of an error identifier is established, it should remain constant throughout the lifecycle of your cmdlet.</span></span>

- <span data-ttu-id="41ee0-138">針對終止錯誤，請針對特定 CLR 例外狀況類型使用唯一的錯誤識別碼。</span><span class="sxs-lookup"><span data-stu-id="41ee0-138">For terminating errors, use a unique error identifier for a particular CLR exception type.</span></span> <span data-ttu-id="41ee0-139">如果例外狀況類型變更，請使用新的錯誤識別碼。</span><span class="sxs-lookup"><span data-stu-id="41ee0-139">If the exception type changes, use a new error identifier.</span></span>

- <span data-ttu-id="41ee0-140">針對非終止錯誤，請針對特定的輸入物件使用特定的錯誤識別碼。</span><span class="sxs-lookup"><span data-stu-id="41ee0-140">For nonterminating errors, use a specific error identifier for a specific input object.</span></span>

- <span data-ttu-id="41ee0-141">針對 tersely 對應至所回報錯誤的識別碼，選擇 [文字]。</span><span class="sxs-lookup"><span data-stu-id="41ee0-141">Choose text for the identifier that tersely corresponds to the error being reported.</span></span> <span data-ttu-id="41ee0-142">請勿使用空白字元或標點符號。</span><span class="sxs-lookup"><span data-stu-id="41ee0-142">Don't use white space or punctuation.</span></span>

- <span data-ttu-id="41ee0-143">不要產生無法重現的錯誤識別碼。</span><span class="sxs-lookup"><span data-stu-id="41ee0-143">Don't generate error identifiers that aren't reproducible.</span></span> <span data-ttu-id="41ee0-144">例如，請勿產生包含進程識別碼的識別碼。</span><span class="sxs-lookup"><span data-stu-id="41ee0-144">For example, don't generate identifiers that include a process identifier.</span></span> <span data-ttu-id="41ee0-145">只有當錯誤識別碼對應至其他遇到相同問題的使用者所看到的識別碼時，才有用。</span><span class="sxs-lookup"><span data-stu-id="41ee0-145">Error identifiers are useful only when they correspond to identifiers that are seen by other users who are experiencing the same problem.</span></span>

### <a name="error-categories"></a><span data-ttu-id="41ee0-146">錯誤類別</span><span class="sxs-lookup"><span data-stu-id="41ee0-146">Error categories</span></span>

<span data-ttu-id="41ee0-147">錯誤類別是用來將使用者的錯誤分組。</span><span class="sxs-lookup"><span data-stu-id="41ee0-147">Error categories are used to group errors for the user.</span></span> <span data-ttu-id="41ee0-148">PowerShell 會定義這些類別和 Cmdlet，而且在產生錯誤記錄時，PowerShell 提供者必須在兩者之間進行選擇。</span><span class="sxs-lookup"><span data-stu-id="41ee0-148">PowerShell defines these categories and cmdlets and PowerShell providers must choose between them when generating the error record.</span></span>

<span data-ttu-id="41ee0-149">如需可用錯誤類別的描述，請參閱[ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory)列舉。</span><span class="sxs-lookup"><span data-stu-id="41ee0-149">For a description of the error categories that are available, see the [System.Management.Automation.ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) enumeration.</span></span> <span data-ttu-id="41ee0-150">一般來說，您應該盡可能避免使用**aad-userreadusingalternativesecurityid-noerror**、 **UndefinedError**和**GenericError** 。</span><span class="sxs-lookup"><span data-stu-id="41ee0-150">In general, you should avoid using **NoError**, **UndefinedError**, and **GenericError** whenever possible.</span></span>

<span data-ttu-id="41ee0-151">當使用者將 `$ErrorView` 設定為**CategoryView**時，可以根據分類來查看錯誤。</span><span class="sxs-lookup"><span data-stu-id="41ee0-151">Users can view errors based on category when they set `$ErrorView` to **CategoryView**.</span></span>

## <a name="see-also"></a><span data-ttu-id="41ee0-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41ee0-152">See also</span></span>

[<span data-ttu-id="41ee0-153">Cmdlet 總覽</span><span class="sxs-lookup"><span data-stu-id="41ee0-153">Cmdlet Overview</span></span>](./cmdlet-overview.md)

[<span data-ttu-id="41ee0-154">Cmdlet 輸出的類型</span><span class="sxs-lookup"><span data-stu-id="41ee0-154">Types of Cmdlet Output</span></span>](./types-of-cmdlet-output.md)

[<span data-ttu-id="41ee0-155">Windows PowerShell 參考</span><span class="sxs-lookup"><span data-stu-id="41ee0-155">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)
