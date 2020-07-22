---
title: 撰寫 PowerShell Cmdlet 的說明
ms.date: 09/13/2016
ms.openlocfilehash: 4e1070e90cf3ed83c1d97a3b620e00f65d09989e
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893079"
---
# <a name="writing-help-for-powershell-cmdlets"></a><span data-ttu-id="0107b-102">撰寫 PowerShell Cmdlet 的說明</span><span class="sxs-lookup"><span data-stu-id="0107b-102">Writing Help for PowerShell Cmdlets</span></span>

<span data-ttu-id="0107b-103">PowerShell Cmdlet 可能很實用，但除非您的說明主題清楚說明了 Cmdlet 的用途和使用方式，否則 Cmdlet 可能無法使用，或甚至更糟的是，可能會讓使用者感到不快。</span><span class="sxs-lookup"><span data-stu-id="0107b-103">PowerShell cmdlets can be useful, but unless your Help topics clearly explain what the cmdlet does and how to use it, the cmdlet may not get used or, even worse, it might frustrate users.</span></span> <span data-ttu-id="0107b-104">以 XML 為基礎的 Cmdlet 說明檔案格式可增強一致性，但有很大的説明需要更多功能。</span><span class="sxs-lookup"><span data-stu-id="0107b-104">The XML-based cmdlet Help file format enhances consistency, but great help requires much more.</span></span>

<span data-ttu-id="0107b-105">如果您從未撰寫過 Cmdlet 說明，請參閱下列指導方針。</span><span class="sxs-lookup"><span data-stu-id="0107b-105">If you have never written cmdlet Help, review the following guidelines.</span></span> <span data-ttu-id="0107b-106">下一節將說明撰寫 Cmdlet 說明主題所需的 XML 架構。</span><span class="sxs-lookup"><span data-stu-id="0107b-106">The XML schema required to author the cmdlet Help topic is described in the following section.</span></span> <span data-ttu-id="0107b-107">從[建立 Cmdlet](./how-to-create-the-cmdlet-help-file.md)說明檔開始。</span><span class="sxs-lookup"><span data-stu-id="0107b-107">Start with [Creating the Cmdlet Help File](./how-to-create-the-cmdlet-help-file.md).</span></span> <span data-ttu-id="0107b-108">該主題包含最上層 XML 節點的描述。</span><span class="sxs-lookup"><span data-stu-id="0107b-108">That topic includes a description of the top-level XML nodes.</span></span>

## <a name="writing-guidelines-for-cmdlet-help"></a><span data-ttu-id="0107b-109">撰寫 Cmdlet 說明的指導方針</span><span class="sxs-lookup"><span data-stu-id="0107b-109">Writing Guidelines for Cmdlet Help</span></span>

### <a name="write-well"></a><span data-ttu-id="0107b-110">寫得好</span><span class="sxs-lookup"><span data-stu-id="0107b-110">Write well</span></span>

<span data-ttu-id="0107b-111">任何內容都不會取代撰寫完善的主題。</span><span class="sxs-lookup"><span data-stu-id="0107b-111">Nothing replaces a well-written topic.</span></span> <span data-ttu-id="0107b-112">如果您不是專業作者，請尋找可協助您的作者或編輯器。</span><span class="sxs-lookup"><span data-stu-id="0107b-112">If you are not a professional writer, find a writer or editor to help you.</span></span> <span data-ttu-id="0107b-113">另一種替代方式是將解說文字複製到 Microsoft Word，並使用文法和拼寫檢查來改善您的工作。</span><span class="sxs-lookup"><span data-stu-id="0107b-113">Another alternative is to copy your Help text into Microsoft Word and use the grammar and spelling checks to improve your work.</span></span>

### <a name="write-simply"></a><span data-ttu-id="0107b-114">簡單撰寫</span><span class="sxs-lookup"><span data-stu-id="0107b-114">Write simply</span></span>

<span data-ttu-id="0107b-115">使用簡單的字組和片語。</span><span class="sxs-lookup"><span data-stu-id="0107b-115">Use simple words and phrases.</span></span> <span data-ttu-id="0107b-116">避免術語。</span><span class="sxs-lookup"><span data-stu-id="0107b-116">Avoid jargon.</span></span> <span data-ttu-id="0107b-117">請考慮許多讀者僅配備外部語言字典和您的說明主題。</span><span class="sxs-lookup"><span data-stu-id="0107b-117">Consider that many readers are equipped only with a foreign-language dictionary and your Help topic.</span></span>

### <a name="write-consistently"></a><span data-ttu-id="0107b-118">一致寫入</span><span class="sxs-lookup"><span data-stu-id="0107b-118">Write consistently</span></span>

<span data-ttu-id="0107b-119">相關 Cmdlet 的說明應該類似（例如，get-x 和 set-x）。</span><span class="sxs-lookup"><span data-stu-id="0107b-119">Help for related cmdlets should be similar (for example, get-x and set-x).</span></span> <span data-ttu-id="0107b-120">使用標準參數的標準描述，例如**Force**和**InputObject**。</span><span class="sxs-lookup"><span data-stu-id="0107b-120">Use the standard descriptions for standard parameters, like **Force** and **InputObject**.</span></span> <span data-ttu-id="0107b-121">（從 [說明] 複製核心 Cmdlet）。使用標準詞彙。</span><span class="sxs-lookup"><span data-stu-id="0107b-121">(Copy them from Help for the core cmdlets.) Use standard terms.</span></span> <span data-ttu-id="0107b-122">例如，使用「參數」，而不是「引數」，並使用「Cmdlet」而不是「命令」或「命令-let」。</span><span class="sxs-lookup"><span data-stu-id="0107b-122">For example, use "parameter", not "argument", and use "cmdlet" not "command" or "command-let."</span></span>

### <a name="start-the-synopsis-with-a-verb"></a><span data-ttu-id="0107b-123">使用動詞來啟動概要</span><span class="sxs-lookup"><span data-stu-id="0107b-123">Start the synopsis with a verb</span></span>

<span data-ttu-id="0107b-124">[摘要] 欄位會通知使用者 Cmdlet 的用途，而不是它的作用或其運作方式。</span><span class="sxs-lookup"><span data-stu-id="0107b-124">The synopsis field informs the user what the cmdlet does, not what it is or how it works.</span></span> <span data-ttu-id="0107b-125">動詞建立以工作為基礎的語句，通知使用者此 Cmdlet 是否符合其需求。</span><span class="sxs-lookup"><span data-stu-id="0107b-125">Verbs create a task-based statement that informs users if this cmdlet meets their requirements.</span></span> <span data-ttu-id="0107b-126">使用簡單動詞，例如「get」、「create」和「change」。</span><span class="sxs-lookup"><span data-stu-id="0107b-126">Use simple verbs like "get", "create", and "change."</span></span> <span data-ttu-id="0107b-127">請避免「設定」，這可能是不清楚的單字，例如「修改」。</span><span class="sxs-lookup"><span data-stu-id="0107b-127">Avoid "set", which can be vague and fancy words like "modify".</span></span>

### <a name="focus-on-objects"></a><span data-ttu-id="0107b-128">專注于物件</span><span class="sxs-lookup"><span data-stu-id="0107b-128">Focus on objects</span></span>

<span data-ttu-id="0107b-129">大部分的 "get" Cmdlet 會顯示某個專案，但其主要功能是取得物件。</span><span class="sxs-lookup"><span data-stu-id="0107b-129">Most "get" cmdlets display something, but their primary function is to get an object.</span></span> <span data-ttu-id="0107b-130">在您的 [說明] 中，將焦點放在物件上，讓使用者瞭解預設顯示是其中一種，而且它們可以使用您以不同方式為其取得之物件的方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="0107b-130">In your Help, focus on the object, so that users understand that the default display is one of many, and that they can use the methods and properties of the object that you retrieved for them in different ways.</span></span>

### <a name="write-detailed-descriptions"></a><span data-ttu-id="0107b-131">撰寫詳細描述</span><span class="sxs-lookup"><span data-stu-id="0107b-131">Write detailed descriptions</span></span>

<span data-ttu-id="0107b-132">簡要列出 Cmdlet 在詳細描述中可執行檔所有動作。</span><span class="sxs-lookup"><span data-stu-id="0107b-132">Briefly list everything that the cmdlet can do in the detailed description.</span></span> <span data-ttu-id="0107b-133">如果 main 函式是要變更一個屬性，但 Cmdlet 可以變更所有屬性，請在詳細的描述中列出此項。</span><span class="sxs-lookup"><span data-stu-id="0107b-133">If the main function is to change one property, but the cmdlet can change all properties, list this in the detailed description.</span></span>

### <a name="use-conventional-syntax"></a><span data-ttu-id="0107b-134">使用傳統語法</span><span class="sxs-lookup"><span data-stu-id="0107b-134">Use conventional syntax</span></span>

<span data-ttu-id="0107b-135">使用適用于 Windows 和 UNIX 命令列說明的標準巴克斯-Backus-naur 格式。</span><span class="sxs-lookup"><span data-stu-id="0107b-135">Use the standard Backus-Naur format which is common for Windows and UNIX command-line Help.</span></span>

### <a name="use-microsoft-net-types-for-parameter-values"></a><span data-ttu-id="0107b-136">使用 Microsoft .NET 類型做為參數值</span><span class="sxs-lookup"><span data-stu-id="0107b-136">Use Microsoft .NET types for parameter values</span></span>

<span data-ttu-id="0107b-137">參數值的預留位置（在語法和參數描述中）會顯示參數將接受之物件的 .NET Framework 類型。</span><span class="sxs-lookup"><span data-stu-id="0107b-137">The placeholders for parameter values (in the syntax and parameter descriptions) show the .NET Framework types of the objects that the parameter will accept.</span></span> <span data-ttu-id="0107b-138">PowerShell 小組會開發此慣例，協助使用者瞭解 .NET Framework 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="0107b-138">The PowerShell team developed this convention to help teach users about the .NET Framework.</span></span>

### <a name="write-complete-parameter-descriptions"></a><span data-ttu-id="0107b-139">撰寫完整的參數描述</span><span class="sxs-lookup"><span data-stu-id="0107b-139">Write complete parameter descriptions</span></span>

<span data-ttu-id="0107b-140">參數描述必須通知使用者兩個事項：參數的作用（其效果），以及它們必須為參數值輸入的內容。</span><span class="sxs-lookup"><span data-stu-id="0107b-140">Parameter descriptions must inform users of two things: what the parameter does (its effect) and what they must type for the parameter values.</span></span>

### <a name="write-practical-examples"></a><span data-ttu-id="0107b-141">撰寫實用的範例</span><span class="sxs-lookup"><span data-stu-id="0107b-141">Write practical examples</span></span>

<span data-ttu-id="0107b-142">範例應該會顯示如何使用所有參數，但最重要的是示範如何在真實世界的工作中使用此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0107b-142">The examples should show how to use all of the parameters, but the most important thing is to show how to use the cmdlet in real-world tasks.</span></span> <span data-ttu-id="0107b-143">從簡單的範例開始，並撰寫日益複雜的範例。</span><span class="sxs-lookup"><span data-stu-id="0107b-143">Start with a simple example and write increasingly complex examples.</span></span> <span data-ttu-id="0107b-144">在最後一個範例中，示範如何在管線中使用 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0107b-144">In the final example, show how to use the cmdlet in a pipeline.</span></span>

### <a name="use-the-notes-field"></a><span data-ttu-id="0107b-145">使用 [附注] 欄位</span><span class="sxs-lookup"><span data-stu-id="0107b-145">Use the Notes field</span></span>

<span data-ttu-id="0107b-146">使用 [附注] 欄位來說明使用者必須瞭解 Cmdlet 的概念。</span><span class="sxs-lookup"><span data-stu-id="0107b-146">Use the Notes field to explain concepts that users need to understand the cmdlet.</span></span> <span data-ttu-id="0107b-147">您也可以使用記事來協助使用者避免常見的錯誤。</span><span class="sxs-lookup"><span data-stu-id="0107b-147">You can also use notes to help users avoid common errors.</span></span> <span data-ttu-id="0107b-148">避免 Url 變更。</span><span class="sxs-lookup"><span data-stu-id="0107b-148">Avoid URLs as they change.</span></span> <span data-ttu-id="0107b-149">相反地，請提供要搜尋的使用者字詞。</span><span class="sxs-lookup"><span data-stu-id="0107b-149">Instead, provide users terms to search for.</span></span>

### <a name="test-your-help"></a><span data-ttu-id="0107b-150">測試您的協助</span><span class="sxs-lookup"><span data-stu-id="0107b-150">Test your Help</span></span>

<span data-ttu-id="0107b-151">測試此協助，就像測試程式碼一樣。</span><span class="sxs-lookup"><span data-stu-id="0107b-151">Test the Help just like you test your code.</span></span> <span data-ttu-id="0107b-152">讓朋友和同事閱讀您的說明內容並提供意見反應。</span><span class="sxs-lookup"><span data-stu-id="0107b-152">Have friends and colleagues read your Help content and provide feedback.</span></span> <span data-ttu-id="0107b-153">您也可以從新聞群組要求意見反應。</span><span class="sxs-lookup"><span data-stu-id="0107b-153">You can also solicit feedback from newsgroups.</span></span>

## <a name="see-also"></a><span data-ttu-id="0107b-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0107b-154">See Also</span></span>

 [<span data-ttu-id="0107b-155">如何建立 Cmdlet 說明檔案</span><span class="sxs-lookup"><span data-stu-id="0107b-155">How to Create the Cmdlet Help File</span></span>](./how-to-create-the-cmdlet-help-file.md)

 [<span data-ttu-id="0107b-156">如何新增 Cmdlet 名稱和概要至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="0107b-156">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="0107b-157">如何將詳細描述新增至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="0107b-157">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="0107b-158">如何新增語法至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="0107b-158">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="0107b-159">如何將參數新增至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="0107b-159">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="0107b-160">如何將輸入類型新增至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="0107b-160">How to add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="0107b-161">如何新增傳回值至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="0107b-161">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="0107b-162">如何新增附註至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="0107b-162">How to Add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="0107b-163">如何新增範例至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="0107b-163">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="0107b-164">如何新增相關連結至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="0107b-164">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="0107b-165">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="0107b-165">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
