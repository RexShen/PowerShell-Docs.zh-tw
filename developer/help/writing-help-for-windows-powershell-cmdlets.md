---
title: 適用於 PowerShell Cmdlet 撰寫說明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: 8d692cf88d1d356886ef973f0989294d6b51ee6d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083156"
---
# <a name="writing-help-for-powershell-cmdlets"></a><span data-ttu-id="dc57b-102">適用於 PowerShell Cmdlet 撰寫說明</span><span class="sxs-lookup"><span data-stu-id="dc57b-102">Writing Help for PowerShell Cmdlets</span></span>

<span data-ttu-id="dc57b-103">PowerShell cmdlet 會很有用，但除非您的 [說明] 主題清楚地說明 cmdlet 的功能，以及如何使用它，此 cmdlet 可能會使用或更糟的是，它可能會讓使用者不耐煩。</span><span class="sxs-lookup"><span data-stu-id="dc57b-103">PowerShell cmdlets can be useful, but unless your Help topics clearly explain what the cmdlet does and how to use it, the cmdlet may not get used or, even worse, it might frustrate users.</span></span>
<span data-ttu-id="dc57b-104">XML 型 cmdlet 說明檔格式強化一致性，但大的幫助需要更多。</span><span class="sxs-lookup"><span data-stu-id="dc57b-104">The XML-based cmdlet Help file format enhances consistency, but great help requires much more.</span></span>

<span data-ttu-id="dc57b-105">如果您從未撰寫 cmdlet 說明，請檢閱下列指導方針。</span><span class="sxs-lookup"><span data-stu-id="dc57b-105">If you have never written cmdlet Help, review the following guidelines.</span></span>
<span data-ttu-id="dc57b-106">撰寫 cmdlet 說明主題所需的 XML 結構描述是由下列一節所述。</span><span class="sxs-lookup"><span data-stu-id="dc57b-106">The XML schema required to author the cmdlet Help topic is described in the following section.</span></span>
<span data-ttu-id="dc57b-107">開頭[建立 Cmdlet 說明檔](./how-to-create-the-cmdlet-help-file.md)。</span><span class="sxs-lookup"><span data-stu-id="dc57b-107">Start with [Creating the Cmdlet Help File](./how-to-create-the-cmdlet-help-file.md).</span></span>
<span data-ttu-id="dc57b-108">該主題都包含最上層的 XML 節點的描述。</span><span class="sxs-lookup"><span data-stu-id="dc57b-108">That topic includes a description of the top-level XML nodes.</span></span>

## <a name="writing-guidelines-for-cmdlet-help"></a><span data-ttu-id="dc57b-109">撰寫 Cmdlet 說明的指導方針</span><span class="sxs-lookup"><span data-stu-id="dc57b-109">Writing Guidelines for Cmdlet Help</span></span>

### <a name="write-well"></a><span data-ttu-id="dc57b-110">撰寫</span><span class="sxs-lookup"><span data-stu-id="dc57b-110">Write well</span></span>
<span data-ttu-id="dc57b-111">不會取代編寫完善的主題。</span><span class="sxs-lookup"><span data-stu-id="dc57b-111">Nothing replaces a well-written topic.</span></span>
<span data-ttu-id="dc57b-112">如果您不是專業的寫入器，尋找可協助您讓寫入器或編輯器。</span><span class="sxs-lookup"><span data-stu-id="dc57b-112">If you are not a professional writer, find a writer or editor to help you.</span></span>
<span data-ttu-id="dc57b-113">另一個替代方式是複製到 Microsoft Word 的說明文字，並使用文法與拼字檢查來改善您的工作。</span><span class="sxs-lookup"><span data-stu-id="dc57b-113">Another alternative is to copy your Help text into Microsoft Word and use the grammar and spelling checks to improve your work.</span></span>

### <a name="write-simply"></a><span data-ttu-id="dc57b-114">只要撰寫</span><span class="sxs-lookup"><span data-stu-id="dc57b-114">Write simply</span></span>
<span data-ttu-id="dc57b-115">使用簡單的單字和片語。</span><span class="sxs-lookup"><span data-stu-id="dc57b-115">Use simple words and phrases.</span></span>
<span data-ttu-id="dc57b-116">避免術語。</span><span class="sxs-lookup"><span data-stu-id="dc57b-116">Avoid jargon.</span></span>
<span data-ttu-id="dc57b-117">請考慮許多讀者便有能力只使用外國語言字典和說明主題。</span><span class="sxs-lookup"><span data-stu-id="dc57b-117">Consider that many readers are equipped only with a foreign-language dictionary and your Help topic.</span></span>

### <a name="write-consistently"></a><span data-ttu-id="dc57b-118">以一致的方式寫入</span><span class="sxs-lookup"><span data-stu-id="dc57b-118">Write consistently</span></span>
<span data-ttu-id="dc57b-119">說明相關的 cmdlet 應該類似於 （例如 get-x 和 set-x）。</span><span class="sxs-lookup"><span data-stu-id="dc57b-119">Help for related cmdlets should be similar (for example, get-x and set-x).</span></span>
<span data-ttu-id="dc57b-120">標準的參數，使用標準的描述，例如**Force**並**InputObject**。</span><span class="sxs-lookup"><span data-stu-id="dc57b-120">Use the standard descriptions for standard parameters, like **Force** and **InputObject**.</span></span>
<span data-ttu-id="dc57b-121">（複製它們的說明對核心 cmdlet）。使用標準的詞彙。</span><span class="sxs-lookup"><span data-stu-id="dc57b-121">(Copy them from Help for the core cmdlets.) Use standard terms.</span></span>
<span data-ttu-id="dc57b-122">例如，使用 「 參數 」，不 「 引數 」，並使用 「 cmdlet 」 不 「 命令 」 或者"cmdlet。 」</span><span class="sxs-lookup"><span data-stu-id="dc57b-122">For example, use "parameter", not "argument", and use "cmdlet" not "command" or "command-let."</span></span>

### <a name="start-the-synopsis-with-a-verb"></a><span data-ttu-id="dc57b-123">使用動詞啟動概要</span><span class="sxs-lookup"><span data-stu-id="dc57b-123">Start the synopsis with a verb</span></span>
<span data-ttu-id="dc57b-124">此指令程式不會它是什麼或它的運作方式，概要欄位就會通知使用者。</span><span class="sxs-lookup"><span data-stu-id="dc57b-124">The synopsis field informs the user what the cmdlet does, not what it is or how it works.</span></span>
<span data-ttu-id="dc57b-125">動詞命令建立一個以工作為基礎的陳述式，會通知使用者，如果此 cmdlet 會符合其需求。</span><span class="sxs-lookup"><span data-stu-id="dc57b-125">Verbs create a task-based statement that informs users if this cmdlet meets their requirements.</span></span>
<span data-ttu-id="dc57b-126">使用簡單的動詞命令，例如 「 get 」、 「 建立 」 和 「 變更 」。</span><span class="sxs-lookup"><span data-stu-id="dc57b-126">Use simple verbs like "get", "create", and "change."</span></span>
<span data-ttu-id="dc57b-127">避免 「 set 」，它可以是含糊不清，和 「 修改 」 之類的複雜的單字。</span><span class="sxs-lookup"><span data-stu-id="dc57b-127">Avoid "set", which can be vague and fancy words like "modify".</span></span>

### <a name="focus-on-objects"></a><span data-ttu-id="dc57b-128">專注於物件</span><span class="sxs-lookup"><span data-stu-id="dc57b-128">Focus on objects</span></span>
<span data-ttu-id="dc57b-129">大部分 「 取得 」 cmdlet 顯示項目，但其主要功能是以取得的物件。</span><span class="sxs-lookup"><span data-stu-id="dc57b-129">Most "get" cmdlets display something, but their primary function is to get an object.</span></span>
<span data-ttu-id="dc57b-130">在您的協助，著重於物件，好讓使用者瞭解的預設顯示是任一種，以及他們可以使用的方法和您以不同的方式擷取這些物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="dc57b-130">In your Help, focus on the object, so that users understand that the default display is one of many, and that they can use the methods and properties of the object that you retrieved for them in different ways.</span></span>

### <a name="write-detailed-descriptions"></a><span data-ttu-id="dc57b-131">寫入詳細的描述</span><span class="sxs-lookup"><span data-stu-id="dc57b-131">Write detailed descriptions</span></span>
<span data-ttu-id="dc57b-132">簡短列出所有的 cmdlet 可以執行作業的詳細說明中的項目。</span><span class="sxs-lookup"><span data-stu-id="dc57b-132">Briefly list everything that the cmdlet can do in the detailed description.</span></span>
<span data-ttu-id="dc57b-133">如果 main 函式來變更一個屬性，但 cmdlet 可以變更所有屬性，請將這列入詳細的描述。</span><span class="sxs-lookup"><span data-stu-id="dc57b-133">If the main function is to change one property, but the cmdlet can change all properties, list this in the detailed description.</span></span>

### <a name="use-conventional-syntax"></a><span data-ttu-id="dc57b-134">使用傳統的語法</span><span class="sxs-lookup"><span data-stu-id="dc57b-134">Use conventional syntax</span></span>
<span data-ttu-id="dc57b-135">使用標準的巴克斯格式是很常見的 Windows 和 UNIX 命令列說明。</span><span class="sxs-lookup"><span data-stu-id="dc57b-135">Use the standard Backus-Naur format which is common for Windows and UNIX command-line Help.</span></span>

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a><span data-ttu-id="dc57b-136">使用 Microsoft.NET Framework 類型的參數值</span><span class="sxs-lookup"><span data-stu-id="dc57b-136">Use Microsoft .NET Framework types for parameter values</span></span>
<span data-ttu-id="dc57b-137">（中的語法和參數的描述） 的參數值的預留位置，顯示.NET Framework 類型的參數會接受物件。</span><span class="sxs-lookup"><span data-stu-id="dc57b-137">The placeholders for parameter values (in the syntax and parameter descriptions) show the .NET Framework types of the objects that the parameter will accept.</span></span>
<span data-ttu-id="dc57b-138">PowerShell 小組開發此慣例，可協助教導使用者有關.NET Framework。</span><span class="sxs-lookup"><span data-stu-id="dc57b-138">The PowerShell team developed this convention to help teach users about the .NET Framework.</span></span>

### <a name="write-complete-parameter-descriptions"></a><span data-ttu-id="dc57b-139">撰寫完整的參數描述</span><span class="sxs-lookup"><span data-stu-id="dc57b-139">Write complete parameter descriptions</span></span>
<span data-ttu-id="dc57b-140">參數說明必須通知使用者兩件事： 何種參數的用途 （其作用），以及他們必須輸入的參數值。</span><span class="sxs-lookup"><span data-stu-id="dc57b-140">Parameter descriptions must inform users of two things: what the parameter does (its effect) and what they must type for the parameter values.</span></span>

### <a name="write-practical-examples"></a><span data-ttu-id="dc57b-141">撰寫實用的範例</span><span class="sxs-lookup"><span data-stu-id="dc57b-141">Write practical examples</span></span>
<span data-ttu-id="dc57b-142">範例應該會顯示如何使用的所有參數，但最重要的事是要說明如何在真實世界工作中使用此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="dc57b-142">The examples should show how to use all of the parameters, but the most important thing is to show how to use the cmdlet in real-world tasks.</span></span>
<span data-ttu-id="dc57b-143">簡單範例開始，寫入日益複雜的範例。</span><span class="sxs-lookup"><span data-stu-id="dc57b-143">Start with a simple example and write increasingly complex examples.</span></span>
<span data-ttu-id="dc57b-144">在最後一個範例中，示範如何在管線中使用此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="dc57b-144">In the final example, show how to use the cmdlet in a pipeline.</span></span>

### <a name="use-the-notes-field"></a><span data-ttu-id="dc57b-145">使用附註 欄位</span><span class="sxs-lookup"><span data-stu-id="dc57b-145">Use the Notes field</span></span>
<span data-ttu-id="dc57b-146">使用附註 欄位來解釋使用者需要了解此 cmdlet 的概念。</span><span class="sxs-lookup"><span data-stu-id="dc57b-146">Use the Notes field to explain concepts that users need to understand the cmdlet.</span></span>
<span data-ttu-id="dc57b-147">您也可以使用資訊以協助使用者避免常見的錯誤。</span><span class="sxs-lookup"><span data-stu-id="dc57b-147">You can also use notes to help users avoid common errors.</span></span>
<span data-ttu-id="dc57b-148">變更時，請避免 Url。</span><span class="sxs-lookup"><span data-stu-id="dc57b-148">Avoid URLs as they change.</span></span>
<span data-ttu-id="dc57b-149">相反地，提供要搜尋的使用者條款。</span><span class="sxs-lookup"><span data-stu-id="dc57b-149">Instead, provide users terms to search for.</span></span>

### <a name="test-your-help"></a><span data-ttu-id="dc57b-150">測試您的協助</span><span class="sxs-lookup"><span data-stu-id="dc57b-150">Test your Help</span></span>
<span data-ttu-id="dc57b-151">就像您測試您的程式碼，請測試說明。</span><span class="sxs-lookup"><span data-stu-id="dc57b-151">Test the Help just like you test your code.</span></span>
<span data-ttu-id="dc57b-152">朋友和同事讀取您的說明內容，並提供意見反應。</span><span class="sxs-lookup"><span data-stu-id="dc57b-152">Have friends and colleagues read your Help content and provide feedback.</span></span>
<span data-ttu-id="dc57b-153">您也可以請求意見反應的新聞群組。</span><span class="sxs-lookup"><span data-stu-id="dc57b-153">You can also solicit feedback from newsgroups.</span></span>

## <a name="see-also"></a><span data-ttu-id="dc57b-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc57b-154">See Also</span></span>

 [<span data-ttu-id="dc57b-155">如何建立 Cmdlet 說明檔</span><span class="sxs-lookup"><span data-stu-id="dc57b-155">How to Create the Cmdlet Help File</span></span>](./how-to-create-the-cmdlet-help-file.md)

 [<span data-ttu-id="dc57b-156">如何將 Cmdlet 說明主題的概要與 Cmdlet 名稱</span><span class="sxs-lookup"><span data-stu-id="dc57b-156">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="dc57b-157">如何將詳細的說明新增至 Cmdlet 的說明主題</span><span class="sxs-lookup"><span data-stu-id="dc57b-157">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="dc57b-158">如何將 Cmdlet 說明主題中的語法</span><span class="sxs-lookup"><span data-stu-id="dc57b-158">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="dc57b-159">如何將參數新增至 Cmdlet 的說明主題</span><span class="sxs-lookup"><span data-stu-id="dc57b-159">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="dc57b-160">如何將輸入類型新增至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="dc57b-160">How to add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="dc57b-161">如何將傳回的值新增至 Cmdlet 的說明主題</span><span class="sxs-lookup"><span data-stu-id="dc57b-161">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="dc57b-162">如何新增備忘稿 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="dc57b-162">How to Add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="dc57b-163">如何新增 Cmdlet 說明主題的範例</span><span class="sxs-lookup"><span data-stu-id="dc57b-163">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="dc57b-164">如何將相關的連結新增至 Cmdlet 的說明主題</span><span class="sxs-lookup"><span data-stu-id="dc57b-164">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="dc57b-165">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="dc57b-165">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)