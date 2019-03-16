---
title: 指令程式錯誤報告 |Microsoft Docs
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
ms.openlocfilehash: 45f5934314a2871ceb921c7a66b9dfb658d0bd99
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057938"
---
# <a name="cmdlet-error-reporting"></a><span data-ttu-id="142ee-102">Cmdlet 錯誤報告</span><span class="sxs-lookup"><span data-stu-id="142ee-102">Cmdlet Error Reporting</span></span>

<span data-ttu-id="142ee-103">以不同的方式取決於是否錯誤會終止錯誤的錯誤或非終止錯誤，就應該報告 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="142ee-103">Cmdlets should report errors differently depending on whether the errors are terminating errors or nonterminating errors.</span></span> <span data-ttu-id="142ee-104">終止的錯誤是錯誤造成管線，以立即終止或沒有理由繼續處理時，發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="142ee-104">Terminating errors are errors that cause the pipeline to be terminated immediately, or errors that occur when there is no reason to continue processing.</span></span> <span data-ttu-id="142ee-105">非終止錯誤會報告目前的錯誤狀況，這些錯誤，但此指令程式可以繼續處理輸入的物件。</span><span class="sxs-lookup"><span data-stu-id="142ee-105">Nonterminating errors are those errors that report a current error condition, but the cmdlet can continue to process input objects.</span></span> <span data-ttu-id="142ee-106">非終止錯誤，問題，通常會通知使用者，但此 cmdlet 會繼續處理下一個輸入的物件。</span><span class="sxs-lookup"><span data-stu-id="142ee-106">With nonterminating errors, the user is typically notified of the problem, but the cmdlet continues to process the next input object.</span></span>

## <a name="terminating-and-nonterminating-errors"></a><span data-ttu-id="142ee-107">終止和非終止錯誤</span><span class="sxs-lookup"><span data-stu-id="142ee-107">Terminating and Nonterminating Errors</span></span>

<span data-ttu-id="142ee-108">下列指導方針可用來判斷錯誤狀況是終止的錯誤或非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="142ee-108">The following guidelines can be used to determine if an error condition is a terminating error or a nonterminating error.</span></span>

- <span data-ttu-id="142ee-109">沒有錯誤狀況防止 cmdlet 成功處理任何進一步的輸入物件嗎？</span><span class="sxs-lookup"><span data-stu-id="142ee-109">Does the error condition prevent your cmdlet from successfully processing any further input objects?</span></span> <span data-ttu-id="142ee-110">如果是的話，這會是終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="142ee-110">If so, this is a terminating error.</span></span>

- <span data-ttu-id="142ee-111">與特定的輸入的物件或輸入的物件子集相關的錯誤狀況？</span><span class="sxs-lookup"><span data-stu-id="142ee-111">Is the error condition related to a specific input object or a subset of input objects?</span></span> <span data-ttu-id="142ee-112">如果是的話，這是一個非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="142ee-112">If so, this is a nonterminating error.</span></span>

- <span data-ttu-id="142ee-113">此 cmdlet 是否接受多個輸入的物件，例如處理可能在另一個輸入物件上成功？</span><span class="sxs-lookup"><span data-stu-id="142ee-113">Does the cmdlet accept multiple input objects, such that processing may succeed on another input object?</span></span> <span data-ttu-id="142ee-114">如果是的話，這是一個非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="142ee-114">If so, this is a nonterminating error.</span></span>

- <span data-ttu-id="142ee-115">Cmdlet 可接受多個輸入的物件應該決定什麼終止和非終止錯誤，即使是在特定情況下套用至只有單一的輸入物件。</span><span class="sxs-lookup"><span data-stu-id="142ee-115">Cmdlets that can accept multiple input objects should decide between what are terminating and nonterminating errors, even when a particular situation applies to only a single input object.</span></span>

- <span data-ttu-id="142ee-116">指令程式可以接收任何數目的輸入物件，並擲回終止的例外狀況之前傳送任何數目的成功或錯誤的物件。</span><span class="sxs-lookup"><span data-stu-id="142ee-116">Cmdlets can receive any number of input objects and send any number of success or error objects before throwing a terminating exception.</span></span> <span data-ttu-id="142ee-117">沒有任何收到的輸入物件的數目和傳送的成功和錯誤物件數目之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="142ee-117">There is no relationship between the number of input objects received and the number of success and error objects sent.</span></span>

- <span data-ttu-id="142ee-118">可以接受輸入物件只有 0-1，並產生只 0-1 的 Cmdlet 會輸出物件應該視為的終止錯誤的錯誤，並會產生終止的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="142ee-118">Cmdlets that can accept only 0-1 input objects and generate only 0-1 output objects should treat errors as terminating errors and generate terminating exceptions.</span></span>

## <a name="reporting-nonterminating-errors"></a><span data-ttu-id="142ee-119">報告非終止錯誤</span><span class="sxs-lookup"><span data-stu-id="142ee-119">Reporting Nonterminating Errors</span></span>

<span data-ttu-id="142ee-120">報告非終止錯誤應該永遠是 cmdlet 的實作內[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法， [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，或有[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法。</span><span class="sxs-lookup"><span data-stu-id="142ee-120">The reporting of a nonterminating error should always be done within the cmdlet's implementation of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, or the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="142ee-121">藉由呼叫報告這些錯誤類型[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)再傳送至錯誤資料流的錯誤記錄的方法。</span><span class="sxs-lookup"><span data-stu-id="142ee-121">These types of errors are reported by calling the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method that in turn sends an error record to the error stream.</span></span>

## <a name="reporting-terminating-errors"></a><span data-ttu-id="142ee-122">報告的終止錯誤</span><span class="sxs-lookup"><span data-stu-id="142ee-122">Reporting Terminating Errors</span></span>

<span data-ttu-id="142ee-123">終止錯誤會報告所擲回例外狀況，或藉由呼叫[System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)方法。</span><span class="sxs-lookup"><span data-stu-id="142ee-123">Terminating errors are reported by throwing exceptions or by calling the [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) method.</span></span> <span data-ttu-id="142ee-124">請注意 cmdlet 也可以攔截並重新擲回例外狀況，例如 OutOfMemory，不過，它們不需要重新擲回例外狀況，因為 Windows PowerShell 執行階段會同時攔截。</span><span class="sxs-lookup"><span data-stu-id="142ee-124">Be aware that cmdlets can also catch and re-throw exceptions such as OutOfMemory, however, they are not required to re-throw exceptions as the Windows PowerShell runtime will catch them as well.</span></span>

<span data-ttu-id="142ee-125">您也可以定義自己的例外狀況的特定問題，您的情況，或將其他資訊新增至現有的例外狀況，使用其錯誤記錄。</span><span class="sxs-lookup"><span data-stu-id="142ee-125">You can also define your own exceptions for issues specific to your situation, or add additional information to an existing exception using its error record.</span></span>

## <a name="error-records"></a><span data-ttu-id="142ee-126">錯誤記錄</span><span class="sxs-lookup"><span data-stu-id="142ee-126">Error Records</span></span>

<span data-ttu-id="142ee-127">Windows PowerShell 說明使用非終止錯誤條件[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)物件。</span><span class="sxs-lookup"><span data-stu-id="142ee-127">Windows PowerShell describes a nonterminating error condition through the use of [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objects.</span></span> <span data-ttu-id="142ee-128">每個[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)物件會提供錯誤類別目錄資訊、 選擇性目標物件和錯誤狀況的相關詳細資料。</span><span class="sxs-lookup"><span data-stu-id="142ee-128">Each [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) object provides error category information, an optional target object, and details about the error condition.</span></span>

### <a name="error-identifiers"></a><span data-ttu-id="142ee-129">錯誤識別碼</span><span class="sxs-lookup"><span data-stu-id="142ee-129">Error Identifiers</span></span>

<span data-ttu-id="142ee-130">錯誤識別碼是簡單的字串，識別在 cmdlet 中的錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="142ee-130">The error identifier is a simple string that identifies the error condition within the cmdlet.</span></span> <span data-ttu-id="142ee-131">Windows PowerShell 會結合以建立完整的錯誤識別碼時篩選回應特定的錯誤時的錯誤資料流或記錄錯誤，可以稍後使用 cmdlet 識別項，或與其他使用者特定活動，這個識別項。</span><span class="sxs-lookup"><span data-stu-id="142ee-131">Windows PowerShell combines this identifier with a cmdlet identifier to create a fully qualified error identifier that can be used later when filtering error streams or logging errors, when responding to specific errors, or with other user-specific activities.</span></span>

<span data-ttu-id="142ee-132">指定錯誤的識別碼時，應該遵循下列指導方針。</span><span class="sxs-lookup"><span data-stu-id="142ee-132">The following guidelines should be followed when specifying error identifiers.</span></span>

- <span data-ttu-id="142ee-133">不同、 非常特定，錯誤識別碼指派給不同的程式碼路徑。</span><span class="sxs-lookup"><span data-stu-id="142ee-133">Assign different, highly specific, error identifiers to different code paths.</span></span> <span data-ttu-id="142ee-134">每個呼叫的程式碼路徑[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)或是[System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)應該有自己的錯誤識別碼。</span><span class="sxs-lookup"><span data-stu-id="142ee-134">Each code path that calls [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) or [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) should have its own error identifier.</span></span>

- <span data-ttu-id="142ee-135">錯誤識別碼應該是唯一的終止和非終止錯誤的 CLR 例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="142ee-135">Error identifiers should be unique to CLR exception types for both terminating and nonterminating errors.</span></span>

- <span data-ttu-id="142ee-136">不會變更錯誤識別項 cmdlet 的 Windows PowerShell 提供者的版本之間的語意。</span><span class="sxs-lookup"><span data-stu-id="142ee-136">Do not change the semantics of an error identifier between versions of your cmdlet or Windows PowerShell provider.</span></span> <span data-ttu-id="142ee-137">建立語意錯誤識別項之後，它應該保持不變的整個生命週期的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="142ee-137">After the semantics of an error identifier is established, it should remain constant throughout the life cycle of your cmdlet.</span></span>

- <span data-ttu-id="142ee-138">終止錯誤，請針對特定的 CLR 例外狀況類型中使用唯一的錯誤識別碼。</span><span class="sxs-lookup"><span data-stu-id="142ee-138">For terminating errors, use a unique error identifier for a particular CLR exception type.</span></span> <span data-ttu-id="142ee-139">如果例外狀況類型變更，請使用新的錯誤識別碼。</span><span class="sxs-lookup"><span data-stu-id="142ee-139">If the exception type changes, use a new error identifier.</span></span>

- <span data-ttu-id="142ee-140">對於非終止錯誤，請針對特定的輸入物件中使用特定的錯誤識別碼。</span><span class="sxs-lookup"><span data-stu-id="142ee-140">For nonterminating errors, use a specific error identifier for a specific input object.</span></span>

- <span data-ttu-id="142ee-141">選擇識別碼 tersely 對應到所回報的錯誤文字。</span><span class="sxs-lookup"><span data-stu-id="142ee-141">Choose text for the identifier that tersely corresponds to the error being reported.</span></span> <span data-ttu-id="142ee-142">請勿使用空格或標點符號。</span><span class="sxs-lookup"><span data-stu-id="142ee-142">Do not use white space or punctuation.</span></span>

- <span data-ttu-id="142ee-143">不會產生不是可重現的錯誤識別碼。</span><span class="sxs-lookup"><span data-stu-id="142ee-143">Do not generate error identifiers that are not reproducible.</span></span> <span data-ttu-id="142ee-144">比方說，不會產生包含處理序識別項的識別項。</span><span class="sxs-lookup"><span data-stu-id="142ee-144">For example, do not generate identifiers that include a process identifier.</span></span> <span data-ttu-id="142ee-145">錯誤識別碼在它們發生相同問題的其他使用者所見的識別項對應時，才很有用。</span><span class="sxs-lookup"><span data-stu-id="142ee-145">Error identifiers are useful only when they correspond to identifiers that are seen by other users who are experiencing the same problem.</span></span>

### <a name="error-categories"></a><span data-ttu-id="142ee-146">錯誤類別目錄</span><span class="sxs-lookup"><span data-stu-id="142ee-146">Error Categories</span></span>

<span data-ttu-id="142ee-147">錯誤類別目錄用來群組使用者的錯誤。</span><span class="sxs-lookup"><span data-stu-id="142ee-147">Error categories are used to group errors for the end-user.</span></span> <span data-ttu-id="142ee-148">這些類別會定義 Windows PowerShell 和 cmdlet 與 Windows PowerShell 提供者必須產生的錯誤記錄時之間做出選擇。</span><span class="sxs-lookup"><span data-stu-id="142ee-148">Windows PowerShell defines these categories and cmdlets and Windows PowerShell providers must choose between them when generating the error record.</span></span>

<span data-ttu-id="142ee-149">如需錯誤類別目錄所提供的說明，請參閱 < [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="142ee-149">For a description of the error categories that are available, see the [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) enumeration.</span></span> <span data-ttu-id="142ee-150">一般情況下，您應該避免使用 NoError、 UndefinedError 和 GenericError 盡可能。</span><span class="sxs-lookup"><span data-stu-id="142ee-150">In general, you should avoid using NoError, UndefinedError, and GenericError whenever possible.</span></span>

<span data-ttu-id="142ee-151">使用者可以檢視這些設定時，根據分類的錯誤 」`$ErrorView`"到"CategoryView 」。</span><span class="sxs-lookup"><span data-stu-id="142ee-151">Users can view errors based on category when they set "`$ErrorView`" to "CategoryView".</span></span>

## <a name="see-also"></a><span data-ttu-id="142ee-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="142ee-152">See Also</span></span>

[<span data-ttu-id="142ee-153">Windows PowerShell Cmdlets</span><span class="sxs-lookup"><span data-stu-id="142ee-153">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)

[<span data-ttu-id="142ee-154">Cmdlet Output</span><span class="sxs-lookup"><span data-stu-id="142ee-154">Cmdlet Output</span></span>](./types-of-cmdlet-output.md)

[<span data-ttu-id="142ee-155">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="142ee-155">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
