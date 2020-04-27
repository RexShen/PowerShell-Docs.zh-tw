---
title: PowerShell-Docs 樣式指南
description: 此文章提供撰寫 PowerShell 文件的樣式規則。
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 90dc93d608440ce7388614b552c0cd873a385cd9
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81624783"
---
# <a name="powershell-docs-style-guide"></a><span data-ttu-id="498ab-103">PowerShell-Docs 樣式指南</span><span class="sxs-lookup"><span data-stu-id="498ab-103">PowerShell-Docs style guide</span></span>

<span data-ttu-id="498ab-104">此文章提供 PowerShell-Docs 內容專屬的樣式指導方針。</span><span class="sxs-lookup"><span data-stu-id="498ab-104">This article provides style guidance specific to the PowerShell-Docs content.</span></span> <span data-ttu-id="498ab-105">這是根據[概觀](overview.md#get-started-writing-docs)中所述的資訊來建置的。</span><span class="sxs-lookup"><span data-stu-id="498ab-105">This builds on the information outlined in the [Overview](overview.md#get-started-writing-docs).</span></span>

## <a name="product-terminology"></a><span data-ttu-id="498ab-106">產品術語</span><span class="sxs-lookup"><span data-stu-id="498ab-106">Product Terminology</span></span>

<span data-ttu-id="498ab-107">PowerShell 有好幾種變體。</span><span class="sxs-lookup"><span data-stu-id="498ab-107">There are several variants of PowerShell.</span></span>

- <span data-ttu-id="498ab-108">**PowerShell** - 這是預設值。</span><span class="sxs-lookup"><span data-stu-id="498ab-108">**PowerShell** - This is the default.</span></span> <span data-ttu-id="498ab-109">我們認為 PowerShell 7 及往後版本將是真正的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="498ab-109">We consider PowerShell 7 and beyond to be the one, true PowerShell going forward.</span></span>
- <span data-ttu-id="498ab-110">**PowerShell Core** - 以 .NET Core 為基礎建置的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="498ab-110">**PowerShell Core** - PowerShell built on .NET Core.</span></span> <span data-ttu-id="498ab-111">使用 **Core** 一詞應該僅限於需要與 Windows PowerShell 區別的情況。</span><span class="sxs-lookup"><span data-stu-id="498ab-111">Usage of the term **Core** should be limited to cases where it is necessary to differentiate it from Windows PowerShell.</span></span>
- <span data-ttu-id="498ab-112">**Windows PowerShell** - 以 .NET Framework 為基礎建置的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="498ab-112">**Windows PowerShell** - PowerShell built on .NET Framework.</span></span> <span data-ttu-id="498ab-113">Windows PowerShell 只隨附於 Windows，而且需要完整的 Framework。</span><span class="sxs-lookup"><span data-stu-id="498ab-113">Windows PowerShell ships only on Windows and requires the complete Framework.</span></span>

  <span data-ttu-id="498ab-114">一般而言，文件中提及 "Windows PowerShell" 時可以代換為 "PowerShell"。</span><span class="sxs-lookup"><span data-stu-id="498ab-114">In general, references to "Windows PowerShell" in documentation can be changed to "PowerShell".</span></span>
  <span data-ttu-id="498ab-115">當討論特定於 "Windows PowerShell" 的行為時，應該使用 "Windows PowerShell"。</span><span class="sxs-lookup"><span data-stu-id="498ab-115">"Windows PowerShell" should be used when "Windows PowerShell"-specific behavior is being discussed.</span></span>

<span data-ttu-id="498ab-116">相關產品</span><span class="sxs-lookup"><span data-stu-id="498ab-116">Related products</span></span>

- <span data-ttu-id="498ab-117">**Visual Studio Code (VS Code)** - 這是 Microsoft 的免費開放原始碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="498ab-117">**Visual Studio Code (VS Code)** - This is Microsoft's free, open source editor.</span></span> <span data-ttu-id="498ab-118">第一次提及時，應使用完整名稱。</span><span class="sxs-lookup"><span data-stu-id="498ab-118">At first mention, the full name should be used.</span></span> <span data-ttu-id="498ab-119">之後，您可以使用 **VS Code**。</span><span class="sxs-lookup"><span data-stu-id="498ab-119">After that you may use **VS Code**.</span></span> <span data-ttu-id="498ab-120">請勿使用 "VSCode"。</span><span class="sxs-lookup"><span data-stu-id="498ab-120">Do not use "VSCode".</span></span>
- <span data-ttu-id="498ab-121">**適用於 Visual Studio Code 的 PowerShell 擴充功能** - 擴充功能會將 VS Code 轉換為適合 PowerShell 的 IDE。</span><span class="sxs-lookup"><span data-stu-id="498ab-121">**PowerShell Extension for Visual Studio Code** - The extension turns VS Code into the preferred IDE for PowerShell.</span></span> <span data-ttu-id="498ab-122">第一次提及時，應使用完整名稱。</span><span class="sxs-lookup"><span data-stu-id="498ab-122">At first mention, the full name should be used.</span></span> <span data-ttu-id="498ab-123">之後，您可以使用 **PowerShell 擴充功能**。</span><span class="sxs-lookup"><span data-stu-id="498ab-123">After that you may use **PowerShell extension**.</span></span>
- <span data-ttu-id="498ab-124">**Azure PowerShell** - 這是用來管理 Azure 服務的 PowerShell 模組集合。</span><span class="sxs-lookup"><span data-stu-id="498ab-124">**Azure PowerShell** - This is the collection of PowerShell modules used to manage Azure services.</span></span>
- <span data-ttu-id="498ab-125">**Azure Stack PowerShell** - 這是用來管理 Microsoft 混合式雲端解決方案的 PowerShell 模組集合。</span><span class="sxs-lookup"><span data-stu-id="498ab-125">**Azure Stack PowerShell** - This is the collection of PowerShell modules used to manage Microsoft's hybrid cloud solution.</span></span>

## <a name="markdown-specifics"></a><span data-ttu-id="498ab-126">Markdown 細節</span><span class="sxs-lookup"><span data-stu-id="498ab-126">Markdown specifics</span></span>

<span data-ttu-id="498ab-127">建置文件的 Microsoft Open Publishing System (OPS) 會使用 [markdig][] 來處理 Markdown 文件。</span><span class="sxs-lookup"><span data-stu-id="498ab-127">The Microsoft Open Publishing System (OPS) that builds our documentation uses [markdig][] to process the Markdown documents.</span></span> <span data-ttu-id="498ab-128">Markdig 會根據最新的 [CommonMark][] 規格的規則來剖析文件。</span><span class="sxs-lookup"><span data-stu-id="498ab-128">Markdig parses the documents based on the rules of the latest [CommonMark][] specification.</span></span>

<span data-ttu-id="498ab-129">新的 CommonMark 規格對某些 Markdown 元素的建構要嚴格得多。</span><span class="sxs-lookup"><span data-stu-id="498ab-129">The new CommonMark spec is much stricter about the construction of some Markdown elements.</span></span> <span data-ttu-id="498ab-130">請密切注意此文件中提供的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="498ab-130">Pay close attention to the details provided in this document.</span></span>

### <a name="blank-lines-spaces-and-tabs"></a><span data-ttu-id="498ab-131">空白行、空格與定位字元</span><span class="sxs-lookup"><span data-stu-id="498ab-131">Blank lines, spaces, and tabs</span></span>

<span data-ttu-id="498ab-132">空白行也表示 Markdown 中區塊的結尾。</span><span class="sxs-lookup"><span data-stu-id="498ab-132">Blank lines also signal the end of a block in Markdown.</span></span> <span data-ttu-id="498ab-133">不同類型的 Markdown 區塊之間應該有一個空白 (例如，段落與清單或標題之間)。</span><span class="sxs-lookup"><span data-stu-id="498ab-133">There should be a single blank between Markdown blocks of different types (for example, between a paragraph and a list or header).</span></span>

<span data-ttu-id="498ab-134">移除重複的空白行。</span><span class="sxs-lookup"><span data-stu-id="498ab-134">Remove duplicate blank lines.</span></span> <span data-ttu-id="498ab-135">多個空白行會轉譯為 HTML 中的單一空白行，因此多個空白行沒有用途。</span><span class="sxs-lookup"><span data-stu-id="498ab-135">Multiple blank lines render as a single blank line in HTML so there is no purpose for multiple blank lines.</span></span> <span data-ttu-id="498ab-136">程式碼區塊內的多個空白行會中斷程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="498ab-136">Multiple blank lines within a code block break the code block.</span></span>

<span data-ttu-id="498ab-137">移除行結尾多餘的空格。</span><span class="sxs-lookup"><span data-stu-id="498ab-137">Remove extra spaces at the end of lines.</span></span>

> [!NOTE]
> <span data-ttu-id="498ab-138">間距在 Markdown 中很重要。</span><span class="sxs-lookup"><span data-stu-id="498ab-138">Spacing is significant in Markdown.</span></span> <span data-ttu-id="498ab-139">一律使用空格，而不是固定定位字元。</span><span class="sxs-lookup"><span data-stu-id="498ab-139">Always uses spaces instead of hard tabs.</span></span> <span data-ttu-id="498ab-140">尾端空白可以變更 Markdown 轉譯的方式。</span><span class="sxs-lookup"><span data-stu-id="498ab-140">Trailing spaces can change how Markdown renders.</span></span>

### <a name="titles-and-headings"></a><span data-ttu-id="498ab-141">標題 (Title) 與標題 (Heading)</span><span class="sxs-lookup"><span data-stu-id="498ab-141">Titles and headings</span></span>

<span data-ttu-id="498ab-142">僅使用 [ATX 標題][atx] (# 樣式，而非 `=` 或 `-` 樣式標頭)。</span><span class="sxs-lookup"><span data-stu-id="498ab-142">Only use [ATX headings][atx] (# style, as opposed to `=` or `-` style headers).</span></span>

- <span data-ttu-id="498ab-143">使用句子大小寫 - 僅專有名詞與標題或標頭的第一個字母應為大寫</span><span class="sxs-lookup"><span data-stu-id="498ab-143">Use sentence case - only proper nouns and the first letter of a title or header should be capitalized</span></span>
- <span data-ttu-id="498ab-144">`#` 與標題的第一個字母之間必須有一個空格</span><span class="sxs-lookup"><span data-stu-id="498ab-144">There must be a single space between the `#` and the first letter of the heading</span></span>
- <span data-ttu-id="498ab-145">標題應該以一條空白行括住</span><span class="sxs-lookup"><span data-stu-id="498ab-145">Headings should be surrounded by a single blank line</span></span>
- <span data-ttu-id="498ab-146">每個文件只能有一個 H1</span><span class="sxs-lookup"><span data-stu-id="498ab-146">Only one H1 per document</span></span>
- <span data-ttu-id="498ab-147">標頭層級應該以 1 遞增。</span><span class="sxs-lookup"><span data-stu-id="498ab-147">Header levels should increment by one.</span></span> <span data-ttu-id="498ab-148">請勿跳級</span><span class="sxs-lookup"><span data-stu-id="498ab-148">Do not skip levels</span></span>
- <span data-ttu-id="498ab-149">請勿在標頭中使用粗體或其他標記</span><span class="sxs-lookup"><span data-stu-id="498ab-149">Do not use bold or other markup in headers</span></span>

### <a name="limit-line-length-to-100-characters"></a><span data-ttu-id="498ab-150">將行長度限制為 100 個字元</span><span class="sxs-lookup"><span data-stu-id="498ab-150">Limit line length to 100 characters</span></span>

<span data-ttu-id="498ab-151">這適用於概念性文章與 Cmdlet 參考。</span><span class="sxs-lookup"><span data-stu-id="498ab-151">This applies to conceptual articles and cmdlet reference.</span></span> <span data-ttu-id="498ab-152">限制行長度可改善 git 差異與歷程記錄的可讀性。</span><span class="sxs-lookup"><span data-stu-id="498ab-152">Limiting the line length improves the readability of git diffs and history.</span></span> <span data-ttu-id="498ab-153">這也可以讓其他作者更輕鬆地做出貢獻。</span><span class="sxs-lookup"><span data-stu-id="498ab-153">It also makes it easier for other writers to make contributions.</span></span>

<span data-ttu-id="498ab-154">使用 Visual Studio Code 中的 [Reflow Markdown][reflow] 延伸模組，輕鬆地重排段落以符合指定的行長度。</span><span class="sxs-lookup"><span data-stu-id="498ab-154">Use the [Reflow Markdown][reflow] extension in Visual Studio Code to easily reflow paragraphs to fit the prescribed line length.</span></span>

<span data-ttu-id="498ab-155">About_topics 限制為 80 個字元。</span><span class="sxs-lookup"><span data-stu-id="498ab-155">About_topics are limited to 80 characters.</span></span> <span data-ttu-id="498ab-156">如需更具體的資訊，請參閱[編輯參考文章](./editing-cmdlet-ref.md#formatting-about_-files)。</span><span class="sxs-lookup"><span data-stu-id="498ab-156">For more specific information, see [Editing reference articles](./editing-cmdlet-ref.md#formatting-about_-files).</span></span>

### <a name="lists"></a><span data-ttu-id="498ab-157">清單</span><span class="sxs-lookup"><span data-stu-id="498ab-157">Lists</span></span>

<span data-ttu-id="498ab-158">如果您的清單包含多個句子或段落，請考慮使用子層級標頭，而不是清單。</span><span class="sxs-lookup"><span data-stu-id="498ab-158">If your list contains multiple sentences or paragraphs, consider using a sub-level header rather than a list.</span></span>

<span data-ttu-id="498ab-159">清單應以單一空白行括住。</span><span class="sxs-lookup"><span data-stu-id="498ab-159">List should be surrounded by a single blank line.</span></span>

#### <a name="unordered-lists"></a><span data-ttu-id="498ab-160">未排序清單</span><span class="sxs-lookup"><span data-stu-id="498ab-160">Unordered lists</span></span>

<span data-ttu-id="498ab-161">請勿在清單項目的結尾使用句號 (除非它們包含多個句子)。</span><span class="sxs-lookup"><span data-stu-id="498ab-161">Do not end list items with a period unless they contain multiple sentences.</span></span> <span data-ttu-id="498ab-162">針對清單項目的項目符號使用連字號字元 (`-`)。</span><span class="sxs-lookup"><span data-stu-id="498ab-162">Use the hyphen character (`-`) for list item bullets.</span></span> <span data-ttu-id="498ab-163">這樣可以避免與使用星號 [`*`] 的粗體或斜體標記混淆。</span><span class="sxs-lookup"><span data-stu-id="498ab-163">This avoids confusion with bold or italic markup that uses the asterisk [`*`].</span></span> <span data-ttu-id="498ab-164">若要在項目符號項目下包含段落或其他元素，請插入分行符號，並與項目符號後面的第一個字元縮排對齊。</span><span class="sxs-lookup"><span data-stu-id="498ab-164">To include a paragraph or other elements under a bullet item, insert a line break and align indentation with the first character after the bullet.</span></span>

<span data-ttu-id="498ab-165">例如：</span><span class="sxs-lookup"><span data-stu-id="498ab-165">For example:</span></span>

```markdown
This is a list that contain sub-elements under a bullet item.

- First bullet item

  Sentence explaining the first bullet.

  - Sub-bullet item

    Sentence explaining the sub-bullet.

- Second bullet item
- Third bullet item
```

<span data-ttu-id="498ab-166">這是一個清單，其中包含項目符號項目下的子元素。</span><span class="sxs-lookup"><span data-stu-id="498ab-166">This is a list that contains sub-elements under a bullet item.</span></span>

- <span data-ttu-id="498ab-167">第一個項目符號項目</span><span class="sxs-lookup"><span data-stu-id="498ab-167">First bullet item</span></span>

  <span data-ttu-id="498ab-168">說明第一個項目符號的句子。</span><span class="sxs-lookup"><span data-stu-id="498ab-168">Sentence explaining the first bullet.</span></span>

  - <span data-ttu-id="498ab-169">子項目符號項目</span><span class="sxs-lookup"><span data-stu-id="498ab-169">Sub-bullet item</span></span>

    <span data-ttu-id="498ab-170">說明子項目符號的句子。</span><span class="sxs-lookup"><span data-stu-id="498ab-170">Sentence explaining the sub-bullet.</span></span>

- <span data-ttu-id="498ab-171">第二個項目符號項目</span><span class="sxs-lookup"><span data-stu-id="498ab-171">Second bullet item</span></span>
- <span data-ttu-id="498ab-172">第三個項目符號項目</span><span class="sxs-lookup"><span data-stu-id="498ab-172">Third bullet item</span></span>

#### <a name="ordered-lists"></a><span data-ttu-id="498ab-173">已排序清單</span><span class="sxs-lookup"><span data-stu-id="498ab-173">Ordered lists</span></span>

<span data-ttu-id="498ab-174">若要在編號項目底下包含段落或其他元素，請與項目編號後的第一個字元縮排對齊。</span><span class="sxs-lookup"><span data-stu-id="498ab-174">To include a paragraph or other elements under a numbered item, align indentation with the first character after the item number.</span></span> <span data-ttu-id="498ab-175">列出的所有編號項目都應該使用數字 `1.`，而不是遞增每個項目。</span><span class="sxs-lookup"><span data-stu-id="498ab-175">All items in a numbered listed should use the number `1.` rather than incrementing each item.</span></span> <span data-ttu-id="498ab-176">Markdown 轉譯會自動增加值。</span><span class="sxs-lookup"><span data-stu-id="498ab-176">Markdown rendering increments the value automatically.</span></span> <span data-ttu-id="498ab-177">這會讓重新排列項目變得更容易，並標準化附屬內容的縮排。</span><span class="sxs-lookup"><span data-stu-id="498ab-177">This makes reordering items easier and standardizes the indentation of subordinate content.</span></span>

<span data-ttu-id="498ab-178">例如：</span><span class="sxs-lookup"><span data-stu-id="498ab-178">For example:</span></span>

```markdown
1. For the first element, insert a single space after the 1. Long sentences should be
   wrapped to the next line and must line up with the first character after the numbered
   list marker.

   To include a second element (like this one), insert a line break after the first
   and align indentations. The indentation of the second element must line up with
   the first character after the numbered list marker. For single digit items, like
   this one, you indent to column 4. For double digits items, for example item number
   10, you indent to column 5.

1. The next numbered item starts here.
```

<span data-ttu-id="498ab-179">產生的 Markdown 會轉譯如下：</span><span class="sxs-lookup"><span data-stu-id="498ab-179">The resulting Markdown is rendered as follows:</span></span>

1. <span data-ttu-id="498ab-180">針對第一個元素，在 1 之後插入單一空格。</span><span class="sxs-lookup"><span data-stu-id="498ab-180">For the first element, insert a single space after the 1.</span></span> <span data-ttu-id="498ab-181">長句子應該換行到下一行，而且必須與編號清單標記後面的第一個字元對齊。</span><span class="sxs-lookup"><span data-stu-id="498ab-181">Long sentences should be wrapped to the next line and must line up with the first character after the numbered list marker.</span></span>

   <span data-ttu-id="498ab-182">若要包含第二個元素 (例如這個)，在第一個之後插入分行符號並對齊縮排。</span><span class="sxs-lookup"><span data-stu-id="498ab-182">To include a second element (like this one), insert a line break after the first and align indentations.</span></span> <span data-ttu-id="498ab-183">第二個元素的縮排必須與編號清單標記後面的第一個字元對齊。</span><span class="sxs-lookup"><span data-stu-id="498ab-183">The indentation of the second element must line up with the first character after the numbered list marker.</span></span> <span data-ttu-id="498ab-184">針對單位數項目 (例如此處)，您必須縮排到第 4 欄。</span><span class="sxs-lookup"><span data-stu-id="498ab-184">For single digit items, like this one, you indent to column 4.</span></span> <span data-ttu-id="498ab-185">若為雙位數項目 (例如項目編號 10)，則必須縮排到第 5 欄。</span><span class="sxs-lookup"><span data-stu-id="498ab-185">For double digits items, for example item number 10, you indent to column 5.</span></span>

1. <span data-ttu-id="498ab-186">下一個編號項目會從這裡開始。</span><span class="sxs-lookup"><span data-stu-id="498ab-186">The next numbered item starts here.</span></span>

### <a name="images"></a><span data-ttu-id="498ab-187">影像</span><span class="sxs-lookup"><span data-stu-id="498ab-187">Images</span></span>

<span data-ttu-id="498ab-188">包含影像的語法為：</span><span class="sxs-lookup"><span data-stu-id="498ab-188">The syntax to include an image is:</span></span>

```markdown
![[alt text]](<folderPath>)

Example:
![Introduction](./media/overview/Introduction.png)
```

<span data-ttu-id="498ab-189">其中 `alt text` 是影像的簡短描述，而 `<folder path>` 是影像的相對路徑。</span><span class="sxs-lookup"><span data-stu-id="498ab-189">Where `alt text` is a brief description of the image and `<folder path>` is a relative path to the image.</span></span> <span data-ttu-id="498ab-190">視障人士的螢幕助讀程式需要替代文字。</span><span class="sxs-lookup"><span data-stu-id="498ab-190">Alternate text is required for screen readers for the visually impaired.</span></span> <span data-ttu-id="498ab-191">如果存在無法轉譯影像的網站錯誤 (Bug)，這也很有用。</span><span class="sxs-lookup"><span data-stu-id="498ab-191">It is also useful in case there is a site bug where the image cannot be rendered.</span></span>

<span data-ttu-id="498ab-192">影像應儲存在包含文章之資料夾內的 `media/<article-name>` 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="498ab-192">Images should be stored in a `media/<article-name>` folder within the folder containing the article.</span></span>
<span data-ttu-id="498ab-193">不應在文章之間共用影像。</span><span class="sxs-lookup"><span data-stu-id="498ab-193">Images should not be shared between articles.</span></span> <span data-ttu-id="498ab-194">在 `media` 資料夾底下，建立符合您文章檔案名稱的資料夾。</span><span class="sxs-lookup"><span data-stu-id="498ab-194">Create a folder that matches the filename of your article under the `media` folder.</span></span> <span data-ttu-id="498ab-195">將該文章的影像複製到該新資料夾。</span><span class="sxs-lookup"><span data-stu-id="498ab-195">Copy the images for that article to that new folder.</span></span> <span data-ttu-id="498ab-196">如果某個影像由多個文章使用，每個影像資料夾都必須有該影像檔案的複本。</span><span class="sxs-lookup"><span data-stu-id="498ab-196">If an image is used by multiple articles, each image folder must have a copy of that image file.</span></span> <span data-ttu-id="498ab-197">這種做法可防止變更一篇文章中的影像而影響另一篇文章。</span><span class="sxs-lookup"><span data-stu-id="498ab-197">This practice prevents a change to an image in one article affecting another article.</span></span>

<span data-ttu-id="498ab-198">支援下列影像檔案類型：`*.png`、`*.gif`、`*.jpeg`、`*.jpg`、`*.svg`</span><span class="sxs-lookup"><span data-stu-id="498ab-198">The following image file types are supported: `*.png`, `*.gif`, `*.jpeg`, `*.jpg`, `*.svg`</span></span>

### <a name="markdown-extensions-supported-by-open-publishing"></a><span data-ttu-id="498ab-199">Open Publishing 支援的 Markdown 延伸模組</span><span class="sxs-lookup"><span data-stu-id="498ab-199">Markdown extensions supported by Open Publishing</span></span>

<span data-ttu-id="498ab-200">[Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) 包含支援我們發佈系統特有功能的工具。</span><span class="sxs-lookup"><span data-stu-id="498ab-200">The [Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) contains tools that support features unique to our publishing system.</span></span> <span data-ttu-id="498ab-201">警示是 Markdown 擴充功能，用來建立在 docs.microsoft.com 上轉譯的區塊引述，並以色彩與圖示醒目提示內容的重要性。</span><span class="sxs-lookup"><span data-stu-id="498ab-201">Alerts are a Markdown extension to create blockquotes that render on docs.microsoft.com with colors and icons that highlight the significance of the content.</span></span> <span data-ttu-id="498ab-202">支援下列警示類型：</span><span class="sxs-lookup"><span data-stu-id="498ab-202">The following alert types are supported:</span></span>

```markdown
> [!NOTE]
> Information the user should notice even if skimming.

> [!TIP]
> Optional information to help a user be more successful.

> [!IMPORTANT]
> Essential information required for user success.

> [!CAUTION]
> Negative potential consequences of an action.

> [!WARNING]
> Dangerous certain consequences of an action.
```

<span data-ttu-id="498ab-203">這些警示在 docs.microsoft.com 上看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="498ab-203">These alerts look like this on docs.microsoft.com:</span></span>

<span data-ttu-id="498ab-204">附註區塊</span><span class="sxs-lookup"><span data-stu-id="498ab-204">Note block</span></span>

> [!NOTE]
> <span data-ttu-id="498ab-205">即使略讀，使用者也應該注意的資訊。</span><span class="sxs-lookup"><span data-stu-id="498ab-205">Information the user should notice even if skimming.</span></span>

<span data-ttu-id="498ab-206">提示區塊</span><span class="sxs-lookup"><span data-stu-id="498ab-206">Tip block</span></span>

> [!TIP]
> <span data-ttu-id="498ab-207">可協助使用者更成功的選擇性資訊。</span><span class="sxs-lookup"><span data-stu-id="498ab-207">Optional information to help a user be more successful.</span></span>

<span data-ttu-id="498ab-208">重要區塊</span><span class="sxs-lookup"><span data-stu-id="498ab-208">Important block</span></span>

> [!IMPORTANT]
> <span data-ttu-id="498ab-209">使用者成功所需的基本資訊。</span><span class="sxs-lookup"><span data-stu-id="498ab-209">Essential information required for user success.</span></span>

<span data-ttu-id="498ab-210">注意區塊</span><span class="sxs-lookup"><span data-stu-id="498ab-210">Caution block</span></span>

> [!CAUTION]
> <span data-ttu-id="498ab-211">動作的潛在負面後果。</span><span class="sxs-lookup"><span data-stu-id="498ab-211">Negative potential consequences of an action.</span></span>

<span data-ttu-id="498ab-212">警告區塊</span><span class="sxs-lookup"><span data-stu-id="498ab-212">Warning block</span></span>

> [!WARNING]
> <span data-ttu-id="498ab-213">動作的危險特定結果。</span><span class="sxs-lookup"><span data-stu-id="498ab-213">Dangerous certain consequences of an action.</span></span>

### <a name="hyperlinks"></a><span data-ttu-id="498ab-214">超連結</span><span class="sxs-lookup"><span data-stu-id="498ab-214">Hyperlinks</span></span>

- <span data-ttu-id="498ab-215">超連結必須使用 Markdown 語法 `[friendlyname](url-or-path)`</span><span class="sxs-lookup"><span data-stu-id="498ab-215">Hyperlinks must use Markdown syntax `[friendlyname](url-or-path)`</span></span>
- <span data-ttu-id="498ab-216">連結應盡可能使用 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="498ab-216">Links should be HTTPS when possible.</span></span>
- <span data-ttu-id="498ab-217">連結必須具有易記名稱，通常是連結主題的標題</span><span class="sxs-lookup"><span data-stu-id="498ab-217">Links must have a friendly name, usually the title of the linked topic</span></span>
- <span data-ttu-id="498ab-218">位於底部＜相關連結＞一節中的所有項目，都應該是超連結</span><span class="sxs-lookup"><span data-stu-id="498ab-218">All items in the "related links" section at the bottom should be hyperlinked</span></span>
- <span data-ttu-id="498ab-219">請勿在超連結的括弧內使用倒引號、粗體或其他標記。</span><span class="sxs-lookup"><span data-stu-id="498ab-219">Do not use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>
- <span data-ttu-id="498ab-220">當您在談論特定的 URI 時，可能會使用裸 URL。</span><span class="sxs-lookup"><span data-stu-id="498ab-220">Bare URLs may be used when you are talking about a specific URI.</span></span> <span data-ttu-id="498ab-221">URI 必須括在倒引號中。</span><span class="sxs-lookup"><span data-stu-id="498ab-221">The URI must be enclosed in backticks.</span></span> <span data-ttu-id="498ab-222">例如：</span><span class="sxs-lookup"><span data-stu-id="498ab-222">For example:</span></span>

  ```markdown
  By default, if you do not specify this parameter, the DMTF standard resource URI
  `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.
  ```

#### <a name="linking-to-other-content"></a><span data-ttu-id="498ab-223">連結至其他內容</span><span class="sxs-lookup"><span data-stu-id="498ab-223">Linking to other content</span></span>

<span data-ttu-id="498ab-224">發佈系統支援兩種類型的超連結：</span><span class="sxs-lookup"><span data-stu-id="498ab-224">There are two types of hyperlinks supported by the publishing system:</span></span>

<span data-ttu-id="498ab-225">**URL 連結**可以是相對於 docs.microsoft.com 根目錄的 URL 路徑。</span><span class="sxs-lookup"><span data-stu-id="498ab-225">A **URL link** can be a URL path that is relative to the root of docs.microsoft.com.</span></span> <span data-ttu-id="498ab-226">或包含完整 URL 語法的絕對 URL。</span><span class="sxs-lookup"><span data-stu-id="498ab-226">Or an absolute URL that include the full URL syntax.</span></span> <span data-ttu-id="498ab-227">例如： `https:/github.com/MicrosoftDocs/PowerShell-Docs`</span><span class="sxs-lookup"><span data-stu-id="498ab-227">For example: `https:/github.com/MicrosoftDocs/PowerShell-Docs`</span></span>

- <span data-ttu-id="498ab-228">連結至 PowerShell-Docs 以外的內容，或在 Cmdlet 參考與 PowerShell-docs 中的概念性文章之間連結時，請使用 URL 連結。建立相對連結最簡單的方式是從瀏覽器複製 URL，然後從您貼到 Markdown 的值中移除 `https://docs.microsoft.com/en-us`。</span><span class="sxs-lookup"><span data-stu-id="498ab-228">Use URL links when linking to content outside of PowerShell-Docs or between cmdlet reference and conceptual articles within PowerShell-docs. The simplest way to create a relative link is to copy the URL from your browser then remove `https://docs.microsoft.com/en-us` from the value you paste into markdown.</span></span>
- <span data-ttu-id="498ab-229">請勿在 Microsoft 內容的 URL 中包含地區設定 (例如，</span><span class="sxs-lookup"><span data-stu-id="498ab-229">Do not include locales in URLs on Microsoft properties (eg.</span></span> <span data-ttu-id="498ab-230">從 URL 中移除 `/en-us`)。</span><span class="sxs-lookup"><span data-stu-id="498ab-230">remove `/en-us` from URL).</span></span>
- <span data-ttu-id="498ab-231">除非您需要連結至文章的特定版本，否則請從 URL 移除任何非必要的查詢參數。</span><span class="sxs-lookup"><span data-stu-id="498ab-231">Remove any unnecessary query parameters from the URL unless you need to link to a specific version of an article.</span></span> <span data-ttu-id="498ab-232">範例：</span><span class="sxs-lookup"><span data-stu-id="498ab-232">Examples:</span></span>
  - <span data-ttu-id="498ab-233">`?view=powershell-5.1` - 這是用來連結至 PowerShell 的特定版本</span><span class="sxs-lookup"><span data-stu-id="498ab-233">`?view=powershell-5.1` - this is used to link to a specific version of PowerShell</span></span>
  - <span data-ttu-id="498ab-234">`?redirectedfrom=MSDN` - 當您從舊文章重新導向至其新位置時，會將此參數新增至 URL</span><span class="sxs-lookup"><span data-stu-id="498ab-234">`?redirectedfrom=MSDN` - this is added to the URL when you get redirected from an old article to its new location</span></span>
- <span data-ttu-id="498ab-235">針對外部網站的所有 URL 都應該使用 HTTPS，除非目標網站不適用。</span><span class="sxs-lookup"><span data-stu-id="498ab-235">All URLs to external websites should use HTTPS unless that is not valid for the target site.</span></span>

<span data-ttu-id="498ab-236">**檔案連結**是用來從一篇參考文章連結至另一篇，或從某篇概念性文章連結至另一篇。</span><span class="sxs-lookup"><span data-stu-id="498ab-236">A **file link** is used to link from one reference article to another, or from one conceptual article to another.</span></span> <span data-ttu-id="498ab-237">如果您需要連結至 PowerShell 特定版本的參考文章，則必須使用 URL 連結。</span><span class="sxs-lookup"><span data-stu-id="498ab-237">If you need to link to a reference article for a specific version of PowerShell, then you must use a URL link.</span></span>

- <span data-ttu-id="498ab-238">檔案連結包含相對檔案路徑 (例如：`../folder/file.md`)</span><span class="sxs-lookup"><span data-stu-id="498ab-238">File links contain a relative file path (for example: `../folder/file.md`)</span></span>
- <span data-ttu-id="498ab-239">所有檔案路徑都使用正斜線 (`/`) 字元</span><span class="sxs-lookup"><span data-stu-id="498ab-239">All file paths use forward-slash (`/`) characters</span></span>

<span data-ttu-id="498ab-240">URL 和檔案連結上都允許深層連結。</span><span class="sxs-lookup"><span data-stu-id="498ab-240">Deep linking is allowed on both URL and file links.</span></span> <span data-ttu-id="498ab-241">將錨點新增至目標路徑的結尾。</span><span class="sxs-lookup"><span data-stu-id="498ab-241">Add the anchor to the end of the target path.</span></span>
<span data-ttu-id="498ab-242">例如：</span><span class="sxs-lookup"><span data-stu-id="498ab-242">For example:</span></span>

- `[about_Splatting](about_Splatting.md#splatting-with-arrays)`
- `[custom key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)`

<span data-ttu-id="498ab-243">如需詳細資訊，請參閱[在文件中使用連結](https://docs.microsoft.com/contribute/how-to-write-links)。</span><span class="sxs-lookup"><span data-stu-id="498ab-243">For more information, see [Use links in documentation](https://docs.microsoft.com/contribute/how-to-write-links).</span></span>

## <a name="formatting-command-syntax-elements"></a><span data-ttu-id="498ab-244">設定命令語法元素格式</span><span class="sxs-lookup"><span data-stu-id="498ab-244">Formatting command syntax elements</span></span>

- <span data-ttu-id="498ab-245">請一律使用 Cmdlet 與參數的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="498ab-245">Always use the full name for cmdlets and parameters.</span></span> <span data-ttu-id="498ab-246">除非您特別示範別名，否則請避免使用別名。</span><span class="sxs-lookup"><span data-stu-id="498ab-246">Avoid using aliases unless you are specifically demonstrating the alias.</span></span>

- <span data-ttu-id="498ab-247">屬性、參數、物件、類型名稱、類別名稱、類別方法應為**粗體**。</span><span class="sxs-lookup"><span data-stu-id="498ab-247">Property, parameter, object, type names, class names, class methods should be **bold**.</span></span>
  - <span data-ttu-id="498ab-248">屬性與參數值應括在倒引號 (`` ` ``) 中。</span><span class="sxs-lookup"><span data-stu-id="498ab-248">Property and parameter values should be wrapped in backticks (`` ` ``).</span></span>
  - <span data-ttu-id="498ab-249">使用括弧樣式提及類型時，請使用倒引號。</span><span class="sxs-lookup"><span data-stu-id="498ab-249">When referring to types using the bracketed style, use backticks.</span></span> <span data-ttu-id="498ab-250">例如： `[System.Io.FileInfo]`</span><span class="sxs-lookup"><span data-stu-id="498ab-250">For example: `[System.Io.FileInfo]`</span></span>

- <span data-ttu-id="498ab-251">語言關鍵字、Cmdlet 名稱、函式、變數、原生 EXE、檔案路徑與內嵌語法範例都應該以倒引號 (`` ` ``) 字元括住。</span><span class="sxs-lookup"><span data-stu-id="498ab-251">Language keywords, cmdlet names, functions, variables, native EXEs, file paths, and inline syntax examples should be wrapped in backtick (`` ` ``) characters.</span></span>

  <span data-ttu-id="498ab-252">例如：</span><span class="sxs-lookup"><span data-stu-id="498ab-252">For example:</span></span>

  ~~~markdown
  The following code uses `Get-ChildItem` to list the contents of `C:\Windows` and assigns
  the output to the `$files` variable.

  ```powershell
  $files = Get-ChildItem C:\Windows
  ```
  ~~~

  - <span data-ttu-id="498ab-253">依名稱參考參數時，名稱應為**粗體**。</span><span class="sxs-lookup"><span data-stu-id="498ab-253">When referring to a parameter by name, the name should be **bold**.</span></span> <span data-ttu-id="498ab-254">在說明使用連字號前置詞的參數時，應將參數包裝在倒引號中。</span><span class="sxs-lookup"><span data-stu-id="498ab-254">When illustrating the use of a parameter with the hyphen prefix, the parameter should be wrapped in backticks.</span></span> <span data-ttu-id="498ab-255">例如：</span><span class="sxs-lookup"><span data-stu-id="498ab-255">For example:</span></span>

    ```markdown
    The parameter's name is **Name**, but it is typed as `-Name` when used on the command
    line as a parameter.
    ```

  - <span data-ttu-id="498ab-256">顯示外部命令的範例使用方式時，應將該範例包裝在倒引號中。</span><span class="sxs-lookup"><span data-stu-id="498ab-256">When showing example usage of an external command, the example should be wrapped in backticks.</span></span>
    <span data-ttu-id="498ab-257">一律在原生命令中包含副檔名。</span><span class="sxs-lookup"><span data-stu-id="498ab-257">Always include the file extension in the native command.</span></span> <span data-ttu-id="498ab-258">例如：</span><span class="sxs-lookup"><span data-stu-id="498ab-258">For example:</span></span>

    ```markdown
    To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.
    ```

    <span data-ttu-id="498ab-259">包含副檔名可確保系統會根據 PowerShell 的命令優先順序執行正確命令。</span><span class="sxs-lookup"><span data-stu-id="498ab-259">Including the file extension ensures that the correct command is executed according PowerShell's command precedence.</span></span>

- <span data-ttu-id="498ab-260">撰寫概念性文章 (而非撰寫參考內容) 時，第一個 Cmdlet 名稱執行個體必須能以超連結方式連到該 Cmdlet 文件。</span><span class="sxs-lookup"><span data-stu-id="498ab-260">When writing a conceptual article (as opposed to reference content), the first instance of a cmdlet name should be hyperlinked to the cmdlet documentation.</span></span> <span data-ttu-id="498ab-261">請勿在超連結的括弧內使用倒引號、粗體或其他標記。</span><span class="sxs-lookup"><span data-stu-id="498ab-261">Do not use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>

  <span data-ttu-id="498ab-262">例如：</span><span class="sxs-lookup"><span data-stu-id="498ab-262">For example:</span></span>

  ```markdown
  This [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet
  uses the **Object** parameter to ...
  ```

  <span data-ttu-id="498ab-263">如需詳細資訊，請參閱此文章的[超連結](#hyperlinks)一節。</span><span class="sxs-lookup"><span data-stu-id="498ab-263">For more information, see [Hyperlinks](#hyperlinks) section of this article.</span></span>

## <a name="markdown-for-code-samples"></a><span data-ttu-id="498ab-264">程式碼範例的 Markdown</span><span class="sxs-lookup"><span data-stu-id="498ab-264">Markdown for code samples</span></span>

<span data-ttu-id="498ab-265">Markdown 支援兩種不同的程式碼樣式：</span><span class="sxs-lookup"><span data-stu-id="498ab-265">Markdown supports two different code styles:</span></span>

- <span data-ttu-id="498ab-266">**程式碼範圍 (內嵌)** - 以單一倒引號 (`` ` ``) 字元標記。</span><span class="sxs-lookup"><span data-stu-id="498ab-266">**Code spans (inline)** - marked by a single backtick (`` ` ``) character.</span></span> <span data-ttu-id="498ab-267">用於段落內，而不是作為獨立區塊。</span><span class="sxs-lookup"><span data-stu-id="498ab-267">Used within a paragraph rather than as a standalone block.</span></span>
- <span data-ttu-id="498ab-268">**程式碼區塊** - 以三倒引號 (`` ``` ``) 字串括住的多行區塊。</span><span class="sxs-lookup"><span data-stu-id="498ab-268">**Code blocks** - a multi-line block surrounded by triple-backtick (`` ``` ``) strings.</span></span> <span data-ttu-id="498ab-269">程式碼區塊在倒引號之後可能也會有語言標籤。</span><span class="sxs-lookup"><span data-stu-id="498ab-269">Code blocks may also have a language label following the backticks.</span></span> <span data-ttu-id="498ab-270">語言標籤會針對程式碼區塊的內容啟用語法醒目提示。</span><span class="sxs-lookup"><span data-stu-id="498ab-270">The language label enables syntax highlighting for the contents of the code block.</span></span>

<span data-ttu-id="498ab-271">所有程式碼區塊都應該包含在程式碼柵欄中。</span><span class="sxs-lookup"><span data-stu-id="498ab-271">All code blocks should be contained in a code fence.</span></span> <span data-ttu-id="498ab-272">針對程式碼區塊一律不使用縮排。</span><span class="sxs-lookup"><span data-stu-id="498ab-272">Never use indentation for code blocks.</span></span> <span data-ttu-id="498ab-273">Markdown 允許此模式，但可能會有問題，應予以避免。</span><span class="sxs-lookup"><span data-stu-id="498ab-273">Markdown allows this pattern but it can be problematic and should be avoided.</span></span>

<span data-ttu-id="498ab-274">程式碼區塊是以三倒引號 (`` ``` ``) 程式碼柵欄括住的一或多行程式碼。</span><span class="sxs-lookup"><span data-stu-id="498ab-274">A code block is one or more lines of code surrounded by a triple-backtick (`` ``` ``) code fence.</span></span>
<span data-ttu-id="498ab-275">程式碼柵欄標記本身必須位於程式碼範例前後的一行中。</span><span class="sxs-lookup"><span data-stu-id="498ab-275">The code fence markers must be on their own line before and after the code sample.</span></span> <span data-ttu-id="498ab-276">程式碼區塊開頭的標記可能會有選擇性的語言標籤。</span><span class="sxs-lookup"><span data-stu-id="498ab-276">The marker at the start of the code block may have an optional language label.</span></span> <span data-ttu-id="498ab-277">Microsoft 的 Open Publishing System (OPS) 使用語言標籤來支援語法醒目提示功能。</span><span class="sxs-lookup"><span data-stu-id="498ab-277">Microsoft's Open Publishing System (OPS) uses the language label to support the syntax highlighting feature.</span></span>

<span data-ttu-id="498ab-278">如需所支援語言標記的完整清單，請參閱集中式參與者指南中的[加上柵欄的程式碼區塊](/contribute/code-in-docs#fenced-code-blocks)。</span><span class="sxs-lookup"><span data-stu-id="498ab-278">For a full list of supported language tags, see [Fenced code blocks](/contribute/code-in-docs#fenced-code-blocks) in the centralized contributor guide.</span></span>

<span data-ttu-id="498ab-279">OPS 也新增了 [複製]  按鈕，可將程式碼區塊的內容複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="498ab-279">OPS also adds a **Copy** button that copies the contents of the code block to the clipboard.</span></span> <span data-ttu-id="498ab-280">這可讓您快速地將程式碼貼到指令碼中，以測試程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="498ab-280">This allows you to quickly paste the code into a script to test the code sample.</span></span> <span data-ttu-id="498ab-281">不過，並非文件中的所有範例都是可依原樣執行的。</span><span class="sxs-lookup"><span data-stu-id="498ab-281">However, not all examples in our documentation are intended to be run as-is.</span></span> <span data-ttu-id="498ab-282">某些程式碼區塊是 PowerShell 概念的簡單圖解。</span><span class="sxs-lookup"><span data-stu-id="498ab-282">Some code blocks are simple illustrations of a PowerShell concept.</span></span>

<span data-ttu-id="498ab-283">我們的文件中使用了三種類型的程式碼區塊：</span><span class="sxs-lookup"><span data-stu-id="498ab-283">There are three types code blocks used in our documentation:</span></span>

1. <span data-ttu-id="498ab-284">語法區塊</span><span class="sxs-lookup"><span data-stu-id="498ab-284">Syntax blocks</span></span>
1. <span data-ttu-id="498ab-285">說明範例</span><span class="sxs-lookup"><span data-stu-id="498ab-285">Illustrative examples</span></span>
1. <span data-ttu-id="498ab-286">可執行檔範例</span><span class="sxs-lookup"><span data-stu-id="498ab-286">Executable examples</span></span>

### <a name="syntax-code-blocks"></a><span data-ttu-id="498ab-287">語法程式碼區塊</span><span class="sxs-lookup"><span data-stu-id="498ab-287">Syntax code blocks</span></span>

<span data-ttu-id="498ab-288">語法程式碼區塊是用來描述命令的語法結構。</span><span class="sxs-lookup"><span data-stu-id="498ab-288">Syntax code blocks are used to describe the syntactic structure of a command.</span></span> <span data-ttu-id="498ab-289">請勿在程式碼柵欄使用語言標籤。</span><span class="sxs-lookup"><span data-stu-id="498ab-289">Do not use a language tag on the code fence.</span></span> <span data-ttu-id="498ab-290">此範例說明 `Get-Command` Cmdlet 的所有可能參數。</span><span class="sxs-lookup"><span data-stu-id="498ab-290">This example illustrates all the possible parameters of the `Get-Command` cmdlet.</span></span>

~~~markdown
```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
  [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax]
  [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
  [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```
~~~

<span data-ttu-id="498ab-291">此範例以一般字詞描述 `for` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="498ab-291">This example describes the `for` statement in generalized terms:</span></span>

~~~markdown
```
for (<init>; <condition>; <repeat>)
{<statement list>}
```
~~~

### <a name="illustrative-examples"></a><span data-ttu-id="498ab-292">說明範例</span><span class="sxs-lookup"><span data-stu-id="498ab-292">Illustrative examples</span></span>

<span data-ttu-id="498ab-293">說明範例是用來說明 PowerShell 概念。</span><span class="sxs-lookup"><span data-stu-id="498ab-293">Illustrative examples are used to explain a PowerShell concept.</span></span> <span data-ttu-id="498ab-294">它們不應該複製到剪貼簿來執行。</span><span class="sxs-lookup"><span data-stu-id="498ab-294">They are not meant to be copied to the clipboard for execution.</span></span> <span data-ttu-id="498ab-295">這些最常用於容易輸入且容易了解的簡單範例。</span><span class="sxs-lookup"><span data-stu-id="498ab-295">These are most commonly used for simple examples that are easy to type and easy to understand.</span></span> <span data-ttu-id="498ab-296">程式碼區塊可以包含 PowerShell 提示字元與範例輸出。</span><span class="sxs-lookup"><span data-stu-id="498ab-296">The code block can include the PowerShell prompt and example output.</span></span>

<span data-ttu-id="498ab-297">以下是說明 PowerShell 比較運算子的簡單範例。</span><span class="sxs-lookup"><span data-stu-id="498ab-297">Here is a simple example illustrating the PowerShell comparison operators.</span></span> <span data-ttu-id="498ab-298">在此案例中，我們不希望讀者複製並執行此範例。</span><span class="sxs-lookup"><span data-stu-id="498ab-298">In this case, we don't intend the reader to copy and run this example.</span></span>

~~~markdown
```powershell
PS> 2 -eq 2
True

PS> 2 -eq 3
False

PS>  1,2,3 -eq 2
2

PS> "abc" -eq "abc"
True

PS> "abc" -eq "abc", "def"
False

PS> "abc", "def" -eq "abc"
abc
```
~~~

### <a name="executable-examples"></a><span data-ttu-id="498ab-299">可執行的範例</span><span class="sxs-lookup"><span data-stu-id="498ab-299">Executable examples</span></span>

<span data-ttu-id="498ab-300">複雜範例或目的是用來複製並執行的範例，應使用下列區塊樣式標記：</span><span class="sxs-lookup"><span data-stu-id="498ab-300">Complex examples, or examples that are intended to be copied and executed, should use the following block-style markup:</span></span>

~~~markdown
```powershell
<Your PowerShell code goes here>
```
~~~

<span data-ttu-id="498ab-301">PowerShell 命令所顯示的輸出應該包含在 **Output** 程式碼區塊中，以避免語法醒目提示。</span><span class="sxs-lookup"><span data-stu-id="498ab-301">The output displayed by PowerShell commands should be enclosed in an **Output** code block to prevent syntax highlighting.</span></span> <span data-ttu-id="498ab-302">例如：</span><span class="sxs-lookup"><span data-stu-id="498ab-302">For example:</span></span>

~~~markdown
```powershell
Get-Command -Module Microsoft.PowerShell.Security
```

```Output
CommandType  Name                        Version    Source
-----------  ----                        -------    ------
Cmdlet       ConvertFrom-SecureString    3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       ConvertTo-SecureString      3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-Acl                     3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-AuthenticodeSignature   3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-CmsMessage              3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-Credential              3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-ExecutionPolicy         3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-PfxCertificate          3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       New-FileCatalog             3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Protect-CmsMessage          3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-Acl                     3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-AuthenticodeSignature   3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-ExecutionPolicy         3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Test-FileCatalog            3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Unprotect-CmsMessage        3.0.0.0    Microsoft.PowerShell.Security
```
~~~

<span data-ttu-id="498ab-303">**Output** 程式碼標籤不是語法醒目提示系統所支援的官方「語言」。</span><span class="sxs-lookup"><span data-stu-id="498ab-303">The **Output** code label is not an official "language" supported by the syntax highlighting system.</span></span>
<span data-ttu-id="498ab-304">不過，此標籤很有用，因為 OPS 會將 "Output" 標籤新增至網頁上的程式碼方塊框架。</span><span class="sxs-lookup"><span data-stu-id="498ab-304">However, this label is useful because OPS adds the "Output" label to the code box frame on the web page.</span></span> <span data-ttu-id="498ab-305">"Output" 程式碼方塊沒有語法醒目提示。</span><span class="sxs-lookup"><span data-stu-id="498ab-305">The "Output" code box has no syntax highlighting.</span></span>

## <a name="coding-style-rules"></a><span data-ttu-id="498ab-306">程式碼撰寫樣式規則</span><span class="sxs-lookup"><span data-stu-id="498ab-306">Coding style rules</span></span>

### <a name="avoid-line-continuation-in-code-samples"></a><span data-ttu-id="498ab-307">避免程式碼範例中的行接續</span><span class="sxs-lookup"><span data-stu-id="498ab-307">Avoid line continuation in code samples</span></span>

<span data-ttu-id="498ab-308">避免在 PowerShell 程式碼範例中使用行接續字元 (`` ` ``)。</span><span class="sxs-lookup"><span data-stu-id="498ab-308">Avoid using line continuation characters (`` ` ``) in PowerShell code examples.</span></span> <span data-ttu-id="498ab-309">這些字元很難看到，如果行尾有多餘的空格，可能會造成問題。</span><span class="sxs-lookup"><span data-stu-id="498ab-309">These are hard to see and can cause problems if there are extra spaces at the end of the line.</span></span>

- <span data-ttu-id="498ab-310">使用 PowerShell 展開來減少具有大量參數之 Cmdlet 的行長度。</span><span class="sxs-lookup"><span data-stu-id="498ab-310">Use PowerShell splatting to reduce line length for cmdlets that have a lot of parameters.</span></span>
- <span data-ttu-id="498ab-311">利用 PowerShell 的自然換行機會，像是管道 (`|`) 字元、左括弧、括弧和方括弧之後。</span><span class="sxs-lookup"><span data-stu-id="498ab-311">Take advantage of PowerShell's natural line break opportunities, like after pipe (`|`) characters, opening braces, parentheses, and brackets.</span></span>

### <a name="avoid-using-powershell-prompts-in-examples"></a><span data-ttu-id="498ab-312">避免在範例中使用 PowerShell 提示字元</span><span class="sxs-lookup"><span data-stu-id="498ab-312">Avoid using PowerShell prompts in examples</span></span>

<span data-ttu-id="498ab-313">不建議使用提示字元字串，而且應該僅限於用來說明命令列使用方式的情節。</span><span class="sxs-lookup"><span data-stu-id="498ab-313">Use of the prompt string is discouraged and should be limited to scenarios that are meant to illustrate command line usage.</span></span> <span data-ttu-id="498ab-314">對於大多數這些範例，提示字元字串應該為 `PS>`。</span><span class="sxs-lookup"><span data-stu-id="498ab-314">For most of these examples, the prompt string should be `PS>`.</span></span> <span data-ttu-id="498ab-315">這個提示字元與 OS 特有的指標無關。</span><span class="sxs-lookup"><span data-stu-id="498ab-315">This prompt is independent of OS-specific indicators.</span></span>

<span data-ttu-id="498ab-316">如需說明會改變提示字元的命令，或顯示的路徑對所示案例很重要的範例，則需要提示字元。</span><span class="sxs-lookup"><span data-stu-id="498ab-316">Prompts are required for examples that illustrate commands that alter the prompt or when the path displayed is significant to the scenario being illustrated.</span></span> <span data-ttu-id="498ab-317">下列範例說明當使用登錄提供者時，提示字元的變更方式。</span><span class="sxs-lookup"><span data-stu-id="498ab-317">The following example illustrates how the prompt changes when using the Registry provider.</span></span>

```powershell
PS C:\> cd HKCU:\System\
PS HKCU:\System\> dir

    Hive: HKEY_CURRENT_USER\System

Name                   Property
----                   --------
CurrentControlSet
GameConfigStore        GameDVR_Enabled                       : 1
                       GameDVR_FSEBehaviorMode               : 2
                       Win32_AutoGameModeDefaultProfile      : {2, 0, 1, 0...}
                       Win32_GameModeRelatedProcesses        : {1, 0, 1, 0...}
                       GameDVR_HonorUserFSEBehaviorMode      : 0
                       GameDVR_DXGIHonorFSEWindowsCompatible : 0
```

### <a name="do-not-use-aliases-in-examples"></a><span data-ttu-id="498ab-318">請勿在範例中使用別名</span><span class="sxs-lookup"><span data-stu-id="498ab-318">Do not use aliases in examples</span></span>

<span data-ttu-id="498ab-319">除非您特別討論別名，否則請一律使用所有 Cmdlet 與參數的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="498ab-319">You should always use the full name of all cmdlets and parameters unless you are specifically talking about the alias.</span></span> <span data-ttu-id="498ab-320">Cmdlet 與參數名稱必須使用正確的 Pascal 大小寫格式名稱。</span><span class="sxs-lookup"><span data-stu-id="498ab-320">Cmdlet and parameter names must use the proper Pascal-cased names.</span></span>

### <a name="using-parameters-in-examples"></a><span data-ttu-id="498ab-321">在範例中使用參數</span><span class="sxs-lookup"><span data-stu-id="498ab-321">Using parameters in examples</span></span>

<span data-ttu-id="498ab-322">避免使用位置參數。</span><span class="sxs-lookup"><span data-stu-id="498ab-322">Avoid using positional parameters.</span></span> <span data-ttu-id="498ab-323">一般來說，即使是位置參數，您也應該一律在範例中包含參數名稱。</span><span class="sxs-lookup"><span data-stu-id="498ab-323">In general, you should always include the parameter name in an example, even if the parameter is positional.</span></span> <span data-ttu-id="498ab-324">這可減少您的範例中產生混淆的機會。</span><span class="sxs-lookup"><span data-stu-id="498ab-324">This reduces the chance of confusion in your examples.</span></span>

## <a name="next-steps"></a><span data-ttu-id="498ab-325">後續步驟</span><span class="sxs-lookup"><span data-stu-id="498ab-325">Next steps</span></span>

[<span data-ttu-id="498ab-326">編輯 Cmdlet 參考</span><span class="sxs-lookup"><span data-stu-id="498ab-326">Editing cmdlet reference</span></span>](editing-cmdlet-ref.md)

<!-- External URLs -->
[platyPS]: https://github.com/PowerShell/platyPS
[markdig]: https://github.com/lunet-io/markdig
[CommonMark]: https://spec.commonmark.org/
[atx]: https://github.github.com/gfm/#atx-headings
[pascal-case]: https://en.wikipedia.org/wiki/PascalCase
[reflow]: https://marketplace.visualstudio.com/items?itemName=marvhen.reflow-markdown
