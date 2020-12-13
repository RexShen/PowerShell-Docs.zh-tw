---
ms.date: 09/13/2016
ms.topic: reference
title: 撰寫 PowerShell Cmdlet 的說明
description: 撰寫 PowerShell Cmdlet 的說明
ms.openlocfilehash: b1deaa5998dbc54add93764db785d57afcc0a779
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658111"
---
# <a name="writing-help-for-powershell-cmdlets"></a><span data-ttu-id="e566d-103">撰寫 PowerShell Cmdlet 的說明</span><span class="sxs-lookup"><span data-stu-id="e566d-103">Writing Help for PowerShell Cmdlets</span></span>

<span data-ttu-id="e566d-104">PowerShell Cmdlet 可能很有用，但除非您的說明主題清楚地說明了 Cmdlet 的用途和使用方式，否則 Cmdlet 可能無法使用，或甚至更糟的是，它可能會讓使用者感到不快。</span><span class="sxs-lookup"><span data-stu-id="e566d-104">PowerShell cmdlets can be useful, but unless your Help topics clearly explain what the cmdlet does and how to use it, the cmdlet may not get used or, even worse, it might frustrate users.</span></span> <span data-ttu-id="e566d-105">以 XML 為基礎的 Cmdlet 說明檔案格式可增強一致性，但有很大的説明需要更多。</span><span class="sxs-lookup"><span data-stu-id="e566d-105">The XML-based cmdlet Help file format enhances consistency, but great help requires much more.</span></span>

<span data-ttu-id="e566d-106">如果您從未撰寫過 Cmdlet 說明，請參閱下列指導方針。</span><span class="sxs-lookup"><span data-stu-id="e566d-106">If you have never written cmdlet Help, review the following guidelines.</span></span> <span data-ttu-id="e566d-107">下一節將說明撰寫 Cmdlet 說明主題所需的 XML 架構。</span><span class="sxs-lookup"><span data-stu-id="e566d-107">The XML schema required to author the cmdlet Help topic is described in the following section.</span></span> <span data-ttu-id="e566d-108">從 [建立 Cmdlet](./how-to-create-the-cmdlet-help-file.md)說明檔開始。</span><span class="sxs-lookup"><span data-stu-id="e566d-108">Start with [Creating the Cmdlet Help File](./how-to-create-the-cmdlet-help-file.md).</span></span> <span data-ttu-id="e566d-109">該主題包含最上層 XML 節點的描述。</span><span class="sxs-lookup"><span data-stu-id="e566d-109">That topic includes a description of the top-level XML nodes.</span></span>

## <a name="writing-guidelines-for-cmdlet-help"></a><span data-ttu-id="e566d-110">Cmdlet 說明的撰寫指導方針</span><span class="sxs-lookup"><span data-stu-id="e566d-110">Writing Guidelines for Cmdlet Help</span></span>

### <a name="write-well"></a><span data-ttu-id="e566d-111">寫得很好</span><span class="sxs-lookup"><span data-stu-id="e566d-111">Write well</span></span>

<span data-ttu-id="e566d-112">任何東西都不會取代妥善撰寫的主題。</span><span class="sxs-lookup"><span data-stu-id="e566d-112">Nothing replaces a well-written topic.</span></span> <span data-ttu-id="e566d-113">如果您不是專業作者，請尋找可協助您的寫入器或編輯器。</span><span class="sxs-lookup"><span data-stu-id="e566d-113">If you are not a professional writer, find a writer or editor to help you.</span></span> <span data-ttu-id="e566d-114">另一個替代方法是將您的解說文字複製到 Microsoft Word 中，並使用文法和拼寫檢查來改善您的工作。</span><span class="sxs-lookup"><span data-stu-id="e566d-114">Another alternative is to copy your Help text into Microsoft Word and use the grammar and spelling checks to improve your work.</span></span>

### <a name="write-simply"></a><span data-ttu-id="e566d-115">單純撰寫</span><span class="sxs-lookup"><span data-stu-id="e566d-115">Write simply</span></span>

<span data-ttu-id="e566d-116">使用簡單的單字和片語。</span><span class="sxs-lookup"><span data-stu-id="e566d-116">Use simple words and phrases.</span></span> <span data-ttu-id="e566d-117">避免術語。</span><span class="sxs-lookup"><span data-stu-id="e566d-117">Avoid jargon.</span></span> <span data-ttu-id="e566d-118">請考慮許多讀者僅配備外部語言字典和您的說明主題。</span><span class="sxs-lookup"><span data-stu-id="e566d-118">Consider that many readers are equipped only with a foreign-language dictionary and your Help topic.</span></span>

### <a name="write-consistently"></a><span data-ttu-id="e566d-119">一致寫入</span><span class="sxs-lookup"><span data-stu-id="e566d-119">Write consistently</span></span>

<span data-ttu-id="e566d-120">相關 Cmdlet 的說明應該類似 (例如，1.x 和 x-y) 。</span><span class="sxs-lookup"><span data-stu-id="e566d-120">Help for related cmdlets should be similar (for example, get-x and set-x).</span></span> <span data-ttu-id="e566d-121">使用標準參數的標準描述，例如 **Force** 和 **InputObject**。</span><span class="sxs-lookup"><span data-stu-id="e566d-121">Use the standard descriptions for standard parameters, like **Force** and **InputObject**.</span></span> <span data-ttu-id="e566d-122"> (從核心 Cmdlet 的說明複製這些專案。 ) 使用標準術語。</span><span class="sxs-lookup"><span data-stu-id="e566d-122">(Copy them from Help for the core cmdlets.) Use standard terms.</span></span> <span data-ttu-id="e566d-123">例如，使用「參數」，而不是「引數」，並使用「Cmdlet」而非「命令」或「命令-let」。</span><span class="sxs-lookup"><span data-stu-id="e566d-123">For example, use "parameter", not "argument", and use "cmdlet" not "command" or "command-let."</span></span>

### <a name="start-the-synopsis-with-a-verb"></a><span data-ttu-id="e566d-124">使用動詞開始摘要</span><span class="sxs-lookup"><span data-stu-id="e566d-124">Start the synopsis with a verb</span></span>

<span data-ttu-id="e566d-125">摘要欄位會通知使用者 Cmdlet 的功能，而不是它的作用或運作方式。</span><span class="sxs-lookup"><span data-stu-id="e566d-125">The synopsis field informs the user what the cmdlet does, not what it is or how it works.</span></span> <span data-ttu-id="e566d-126">動詞命令會建立以工作為基礎的語句，以在此 Cmdlet 符合其需求時通知使用者。</span><span class="sxs-lookup"><span data-stu-id="e566d-126">Verbs create a task-based statement that informs users if this cmdlet meets their requirements.</span></span> <span data-ttu-id="e566d-127">使用簡單的動詞命令，例如「get」、「create」和「change」。</span><span class="sxs-lookup"><span data-stu-id="e566d-127">Use simple verbs like "get", "create", and "change."</span></span> <span data-ttu-id="e566d-128">避免「設定」，這可以是不清楚的單字，例如「修改」。</span><span class="sxs-lookup"><span data-stu-id="e566d-128">Avoid "set", which can be vague and fancy words like "modify".</span></span>

### <a name="focus-on-objects"></a><span data-ttu-id="e566d-129">專注于物件</span><span class="sxs-lookup"><span data-stu-id="e566d-129">Focus on objects</span></span>

<span data-ttu-id="e566d-130">大部分的 "get" Cmdlet 會顯示一些內容，但其主要功能是取得物件。</span><span class="sxs-lookup"><span data-stu-id="e566d-130">Most "get" cmdlets display something, but their primary function is to get an object.</span></span> <span data-ttu-id="e566d-131">在您的 [說明] 中，將焦點放在物件上，讓使用者瞭解預設顯示是其中一種，而且可以使用您針對它們所抓取之物件的方法和屬性（以不同方式）。</span><span class="sxs-lookup"><span data-stu-id="e566d-131">In your Help, focus on the object, so that users understand that the default display is one of many, and that they can use the methods and properties of the object that you retrieved for them in different ways.</span></span>

### <a name="write-detailed-descriptions"></a><span data-ttu-id="e566d-132">寫入詳細描述</span><span class="sxs-lookup"><span data-stu-id="e566d-132">Write detailed descriptions</span></span>

<span data-ttu-id="e566d-133">簡短列出 Cmdlet 可在詳細描述中進行的所有動作。</span><span class="sxs-lookup"><span data-stu-id="e566d-133">Briefly list everything that the cmdlet can do in the detailed description.</span></span> <span data-ttu-id="e566d-134">如果主要函式是變更某個屬性，但 Cmdlet 可以變更所有屬性，請在詳細的描述中列出這項功能。</span><span class="sxs-lookup"><span data-stu-id="e566d-134">If the main function is to change one property, but the cmdlet can change all properties, list this in the detailed description.</span></span>

### <a name="use-conventional-syntax"></a><span data-ttu-id="e566d-135">使用傳統語法</span><span class="sxs-lookup"><span data-stu-id="e566d-135">Use conventional syntax</span></span>

<span data-ttu-id="e566d-136">使用 Windows 和 UNIX 命令列說明常用的標準 Backus-Naur 格式。</span><span class="sxs-lookup"><span data-stu-id="e566d-136">Use the standard Backus-Naur format which is common for Windows and UNIX command-line Help.</span></span>

### <a name="use-microsoft-net-types-for-parameter-values"></a><span data-ttu-id="e566d-137">使用 Microsoft .NET 類型作為參數值</span><span class="sxs-lookup"><span data-stu-id="e566d-137">Use Microsoft .NET types for parameter values</span></span>

<span data-ttu-id="e566d-138">參數值的預留位置 (在語法和參數描述中) 顯示參數將接受之物件的 .NET Framework 類型。</span><span class="sxs-lookup"><span data-stu-id="e566d-138">The placeholders for parameter values (in the syntax and parameter descriptions) show the .NET Framework types of the objects that the parameter will accept.</span></span> <span data-ttu-id="e566d-139">PowerShell 小組開發了此慣例，以協助使用者瞭解 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="e566d-139">The PowerShell team developed this convention to help teach users about the .NET Framework.</span></span>

### <a name="write-complete-parameter-descriptions"></a><span data-ttu-id="e566d-140">撰寫完整的參數描述</span><span class="sxs-lookup"><span data-stu-id="e566d-140">Write complete parameter descriptions</span></span>

<span data-ttu-id="e566d-141">參數描述必須通知使用者兩件事：參數 (其效果) ，以及必須為參數值輸入的內容。</span><span class="sxs-lookup"><span data-stu-id="e566d-141">Parameter descriptions must inform users of two things: what the parameter does (its effect) and what they must type for the parameter values.</span></span>

### <a name="write-practical-examples"></a><span data-ttu-id="e566d-142">撰寫實用範例</span><span class="sxs-lookup"><span data-stu-id="e566d-142">Write practical examples</span></span>

<span data-ttu-id="e566d-143">這些範例應該會示範如何使用所有參數，但最重要的是示範如何在真實世界的工作中使用此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e566d-143">The examples should show how to use all of the parameters, but the most important thing is to show how to use the cmdlet in real-world tasks.</span></span> <span data-ttu-id="e566d-144">從簡單的範例開始，並撰寫逐漸複雜的範例。</span><span class="sxs-lookup"><span data-stu-id="e566d-144">Start with a simple example and write increasingly complex examples.</span></span> <span data-ttu-id="e566d-145">在最後一個範例中，示範如何在管線中使用 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e566d-145">In the final example, show how to use the cmdlet in a pipeline.</span></span>

### <a name="use-the-notes-field"></a><span data-ttu-id="e566d-146">使用附注欄位</span><span class="sxs-lookup"><span data-stu-id="e566d-146">Use the Notes field</span></span>

<span data-ttu-id="e566d-147">使用 [附注] 欄位來說明使用者瞭解 Cmdlet 所需的概念。</span><span class="sxs-lookup"><span data-stu-id="e566d-147">Use the Notes field to explain concepts that users need to understand the cmdlet.</span></span> <span data-ttu-id="e566d-148">您也可以使用附注來協助使用者避免常見的錯誤。</span><span class="sxs-lookup"><span data-stu-id="e566d-148">You can also use notes to help users avoid common errors.</span></span> <span data-ttu-id="e566d-149">避免 Url 變更。</span><span class="sxs-lookup"><span data-stu-id="e566d-149">Avoid URLs as they change.</span></span> <span data-ttu-id="e566d-150">相反地，請提供使用者字詞來搜尋。</span><span class="sxs-lookup"><span data-stu-id="e566d-150">Instead, provide users terms to search for.</span></span>

### <a name="test-your-help"></a><span data-ttu-id="e566d-151">測試您的協助</span><span class="sxs-lookup"><span data-stu-id="e566d-151">Test your Help</span></span>

<span data-ttu-id="e566d-152">測試您的程式碼，就像測試程式碼一樣。</span><span class="sxs-lookup"><span data-stu-id="e566d-152">Test the Help just like you test your code.</span></span> <span data-ttu-id="e566d-153">讓朋友和同事閱讀您的說明內容，並提供意見反應。</span><span class="sxs-lookup"><span data-stu-id="e566d-153">Have friends and colleagues read your Help content and provide feedback.</span></span> <span data-ttu-id="e566d-154">您也可以從新聞群組請求意見反應。</span><span class="sxs-lookup"><span data-stu-id="e566d-154">You can also solicit feedback from newsgroups.</span></span>

## <a name="see-also"></a><span data-ttu-id="e566d-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e566d-155">See Also</span></span>

 [<span data-ttu-id="e566d-156">如何建立 Cmdlet 說明檔案</span><span class="sxs-lookup"><span data-stu-id="e566d-156">How to Create the Cmdlet Help File</span></span>](./how-to-create-the-cmdlet-help-file.md)

 [<span data-ttu-id="e566d-157">如何新增 Cmdlet 名稱和概要至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="e566d-157">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e566d-158">如何將詳細描述新增至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="e566d-158">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="e566d-159">如何新增語法至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="e566d-159">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e566d-160">如何將參數新增至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="e566d-160">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="e566d-161">如何將輸入類型新增至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="e566d-161">How to add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e566d-162">如何新增傳回值至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="e566d-162">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e566d-163">如何新增附註至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="e566d-163">How to Add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e566d-164">如何新增範例至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="e566d-164">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e566d-165">如何新增相關連結至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="e566d-165">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e566d-166">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e566d-166">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
