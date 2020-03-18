---
title: PowerShell-Docs 樣式指南
description: 此文章提供撰寫 PowerShell 文件的樣式規則。
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 964536c5195c3bb8abd98b5996a96fc7b9362489
ms.sourcegitcommit: c97dcf1e00ef540e7464c36c88f841474060044c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79402575"
---
# <a name="powershell-docs-style-guide"></a><span data-ttu-id="6035d-103">PowerShell-Docs 樣式指南</span><span class="sxs-lookup"><span data-stu-id="6035d-103">PowerShell-Docs style guide</span></span>

<span data-ttu-id="6035d-104">此文章提供 PowerShell-Docs 內容專屬的樣式指導方針。</span><span class="sxs-lookup"><span data-stu-id="6035d-104">This article provides style guidance specific to the PowerShell-Docs content.</span></span> <span data-ttu-id="6035d-105">這是根據[概觀](overview.md#get-started-writing-docs)中所述的資訊來建置的。</span><span class="sxs-lookup"><span data-stu-id="6035d-105">This builds on the information outlined in the [Overview](overview.md#get-started-writing-docs).</span></span>

## <a name="product-terminology"></a><span data-ttu-id="6035d-106">產品術語</span><span class="sxs-lookup"><span data-stu-id="6035d-106">Product Terminology</span></span>

<span data-ttu-id="6035d-107">PowerShell 有好幾種變體。</span><span class="sxs-lookup"><span data-stu-id="6035d-107">There are several variants of PowerShell.</span></span>
<span data-ttu-id="6035d-108">下表定義一些用來討論 PowerShell 的不同詞彙。</span><span class="sxs-lookup"><span data-stu-id="6035d-108">This table defines some of the different terms used to discuss PowerShell.</span></span>

- <span data-ttu-id="6035d-109">**PowerShell** - 這是預設值。</span><span class="sxs-lookup"><span data-stu-id="6035d-109">**PowerShell** - This is the default.</span></span> <span data-ttu-id="6035d-110">我們認為 PowerShell 7 及往後版本將是真正的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="6035d-110">We consider PowerShell 7 and beyond to be the one, true PowerShell going forward.</span></span>

- <span data-ttu-id="6035d-111">**PowerShell Core** - 以 .NET Core 為基礎建置的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="6035d-111">**PowerShell Core** - PowerShell built on .NET Core.</span></span> <span data-ttu-id="6035d-112">使用 **Core** 一詞應該僅限於需要與 Windows PowerShell 區別的情況。</span><span class="sxs-lookup"><span data-stu-id="6035d-112">Usage of the term **Core** should be limited to cases where it is necessary to differentiate it from Windows PowerShell.</span></span>

- <span data-ttu-id="6035d-113">**Windows PowerShell** - 以 .NET Framework 為基礎建置的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="6035d-113">**Windows PowerShell** - PowerShell built on .NET Framework.</span></span> <span data-ttu-id="6035d-114">Windows PowerShell 只隨附於 Windows，而且需要完整的 Framework。</span><span class="sxs-lookup"><span data-stu-id="6035d-114">Windows PowerShell ships only on Windows and requires the complete Framework.</span></span>

<span data-ttu-id="6035d-115">一般而言，文件中提及 "Windows PowerShell" 時可以代換為 "PowerShell"。</span><span class="sxs-lookup"><span data-stu-id="6035d-115">In general, references to "Windows PowerShell" in documentation can be changed to "PowerShell".</span></span>
<span data-ttu-id="6035d-116">當討論 Windows 特定技術時，應該**不會**變更 "Windows PowerShell"。</span><span class="sxs-lookup"><span data-stu-id="6035d-116">"Windows PowerShell" should **not** be changed when Windows-specific technology is being discussed.</span></span>

## <a name="markdown-specifics"></a><span data-ttu-id="6035d-117">Markdown 細節</span><span class="sxs-lookup"><span data-stu-id="6035d-117">Markdown specifics</span></span>

<span data-ttu-id="6035d-118">建置文件的 Microsoft Open Publishing System (OPS) 會使用 [markdig][] 來處理 Markdown 文件。</span><span class="sxs-lookup"><span data-stu-id="6035d-118">The Microsoft Open Publishing System (OPS) that builds our documentation uses [markdig][] to process the Markdown documents.</span></span> <span data-ttu-id="6035d-119">Markdig 會根據最新的 [CommonMark][] 規格的規則來剖析文件。</span><span class="sxs-lookup"><span data-stu-id="6035d-119">Markdig parses the documents based on the rules of the latest [CommonMark][] specification.</span></span>

<span data-ttu-id="6035d-120">新的 CommonMark 規格對某些 Markdown 元素的建構要嚴格得多。</span><span class="sxs-lookup"><span data-stu-id="6035d-120">The new CommonMark spec is much stricter about the construction of some Markdown elements.</span></span> <span data-ttu-id="6035d-121">請密切注意此文件中提供的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="6035d-121">Pay close attention to the details provided in this document.</span></span>

### <a name="blank-lines-spaces-and-tabs"></a><span data-ttu-id="6035d-122">空白行、空格與定位字元</span><span class="sxs-lookup"><span data-stu-id="6035d-122">Blank lines, spaces, and tabs</span></span>

<span data-ttu-id="6035d-123">移除重複的空白行。</span><span class="sxs-lookup"><span data-stu-id="6035d-123">Remove duplicate blank lines.</span></span> <span data-ttu-id="6035d-124">多個空白行會轉譯為 HTML 中的單一空白行，因此不會有多個空白行的用途。</span><span class="sxs-lookup"><span data-stu-id="6035d-124">Multiple blank lines render as a single blank line in HTML so there is not purpose for multiple blank lines.</span></span>

<span data-ttu-id="6035d-125">空白行也表示 Markdown 中區塊的結尾。</span><span class="sxs-lookup"><span data-stu-id="6035d-125">Blank lines also signal the end of a block in Markdown.</span></span> <span data-ttu-id="6035d-126">不同類型的 Markdown 區塊之間應該有一個空白 (例如，段落與清單或標題之間)。</span><span class="sxs-lookup"><span data-stu-id="6035d-126">There should be a single blank between Markdown blocks of different types (for example, between a paragraph and a list or header).</span></span>

> [!NOTE]
> <span data-ttu-id="6035d-127">間距在 Markdown 中很重要。</span><span class="sxs-lookup"><span data-stu-id="6035d-127">Spacing is significant in Markdown.</span></span> <span data-ttu-id="6035d-128">一律使用空格，而不是固定定位字元。</span><span class="sxs-lookup"><span data-stu-id="6035d-128">Always uses spaces instead of hard tabs.</span></span> <span data-ttu-id="6035d-129">移除行結尾多餘的空格。</span><span class="sxs-lookup"><span data-stu-id="6035d-129">Remove extra spaces at the end of lines.</span></span>

### <a name="titles-and-headings"></a><span data-ttu-id="6035d-130">標題 (Title) 與標題 (Heading)</span><span class="sxs-lookup"><span data-stu-id="6035d-130">Titles and headings</span></span>

<span data-ttu-id="6035d-131">僅使用 [ATX 標題][atx] (# 樣式，而非 `=` 或 `-` 樣式標頭)。</span><span class="sxs-lookup"><span data-stu-id="6035d-131">Only use [ATX headings][atx] (# style, as opposed to `=` or `-` style headers).</span></span>

- <span data-ttu-id="6035d-132">使用句子大小寫 - 僅專有名詞與標題或標頭的第一個字母應為大寫</span><span class="sxs-lookup"><span data-stu-id="6035d-132">Use sentence case - only proper nouns and the first letter of a title or header should be capitalized</span></span>
- <span data-ttu-id="6035d-133">`#` 與標題的第一個字母之間必須有一個空格</span><span class="sxs-lookup"><span data-stu-id="6035d-133">There must be a single space between the `#` and the first letter of the heading</span></span>
- <span data-ttu-id="6035d-134">標題應該以一條空白行括住</span><span class="sxs-lookup"><span data-stu-id="6035d-134">Headings should be surrounded by a single blank line</span></span>
- <span data-ttu-id="6035d-135">每個文件只能有一個 H1</span><span class="sxs-lookup"><span data-stu-id="6035d-135">Only one H1 per document</span></span>
- <span data-ttu-id="6035d-136">標頭層級應該以 1 遞增。</span><span class="sxs-lookup"><span data-stu-id="6035d-136">Header levels should increment by one.</span></span> <span data-ttu-id="6035d-137">請勿跳級</span><span class="sxs-lookup"><span data-stu-id="6035d-137">Do not skip levels</span></span>
- <span data-ttu-id="6035d-138">請勿在標頭中使用粗體或其他標記</span><span class="sxs-lookup"><span data-stu-id="6035d-138">Do not use bold or other markup in headers</span></span>

### <a name="limit-line-length-to-100-characters"></a><span data-ttu-id="6035d-139">將行長度限制為 100 個字元</span><span class="sxs-lookup"><span data-stu-id="6035d-139">Limit line length to 100 characters</span></span>

<span data-ttu-id="6035d-140">這適用於概念性文章與 Cmdlet 參考。</span><span class="sxs-lookup"><span data-stu-id="6035d-140">This applies to conceptual articles and cmdlet reference.</span></span> <span data-ttu-id="6035d-141">About_topics 限制為 80 個字元。</span><span class="sxs-lookup"><span data-stu-id="6035d-141">About_topics are limited to 80 characters.</span></span>
<span data-ttu-id="6035d-142">限制行長度可改善 git 差異與歷程記錄的可讀性。</span><span class="sxs-lookup"><span data-stu-id="6035d-142">Limiting the line length improves the readability git diffs and history.</span></span> <span data-ttu-id="6035d-143">這也可以讓其他作者更輕鬆地做出貢獻。</span><span class="sxs-lookup"><span data-stu-id="6035d-143">It also makes it easier for other writers to make contributions.</span></span>

<span data-ttu-id="6035d-144">使用 Visual Studio Code 中的 [Reflow Markdown][reflow] 延伸模組，輕鬆地重排段落以符合指定的行長度。</span><span class="sxs-lookup"><span data-stu-id="6035d-144">Use the [Reflow Markdown][reflow] extension in Visual Studio Code to easily reflow paragraphs to fit the prescribed line length.</span></span>

### <a name="lists"></a><span data-ttu-id="6035d-145">清單</span><span class="sxs-lookup"><span data-stu-id="6035d-145">Lists</span></span>

<span data-ttu-id="6035d-146">如果您的清單包含多個句子或段落，請考慮使用子層級標頭，而不是清單。</span><span class="sxs-lookup"><span data-stu-id="6035d-146">If your list contains multiple sentences or paragraphs, consider using a sub-level header rather than a list.</span></span>

<span data-ttu-id="6035d-147">清單應以單一空白行括住。</span><span class="sxs-lookup"><span data-stu-id="6035d-147">List should be surrounded by a single blank line.</span></span>

#### <a name="unordered-lists"></a><span data-ttu-id="6035d-148">未排序清單</span><span class="sxs-lookup"><span data-stu-id="6035d-148">Unordered lists</span></span>

<span data-ttu-id="6035d-149">請勿在清單項目的結尾使用句號 (除非它們包含多個句子)。</span><span class="sxs-lookup"><span data-stu-id="6035d-149">Do not end list items with a period unless they contain multiple sentences.</span></span> <span data-ttu-id="6035d-150">針對清單項目的項目符號使用連字號字元 (`-`)。</span><span class="sxs-lookup"><span data-stu-id="6035d-150">Use the hyphen character (`-`) for list item bullets.</span></span> <span data-ttu-id="6035d-151">這樣可以避免與使用星號 [`*`] 的粗體或斜體標記混淆。</span><span class="sxs-lookup"><span data-stu-id="6035d-151">This avoids confusion with bold or italic markup that uses the asterisk [`*`].</span></span> <span data-ttu-id="6035d-152">若要在項目符號項目下包含段落或其他元素，請插入分行符號，並與項目符號後面的第一個字元縮排對齊。</span><span class="sxs-lookup"><span data-stu-id="6035d-152">To include a paragraph or other elements under a bullet item, insert a line break and align indentation with the first character after the bullet.</span></span>

<span data-ttu-id="6035d-153">例如：</span><span class="sxs-lookup"><span data-stu-id="6035d-153">For example:</span></span>

```markdown
This is a list that contain sub-elements under a bullet item.

- First bullet item

  Sentence explaining the first bullet.

  - Sub-bullet item

    Sentence explaining the sub-bullet.

- Second bullet item
- Third bullet item
```

<span data-ttu-id="6035d-154">這是一個清單，其中包含項目符號項目下的子元素。</span><span class="sxs-lookup"><span data-stu-id="6035d-154">This is a list that contains sub-elements under a bullet item.</span></span>

- <span data-ttu-id="6035d-155">第一個項目符號項目</span><span class="sxs-lookup"><span data-stu-id="6035d-155">First bullet item</span></span>

  <span data-ttu-id="6035d-156">說明第一個項目符號的句子。</span><span class="sxs-lookup"><span data-stu-id="6035d-156">Sentence explaining the first bullet.</span></span>

  - <span data-ttu-id="6035d-157">子項目符號項目</span><span class="sxs-lookup"><span data-stu-id="6035d-157">Sub-bullet item</span></span>

    <span data-ttu-id="6035d-158">說明子項目符號的句子。</span><span class="sxs-lookup"><span data-stu-id="6035d-158">Sentence explaining the sub-bullet.</span></span>

- <span data-ttu-id="6035d-159">第二個項目符號項目</span><span class="sxs-lookup"><span data-stu-id="6035d-159">Second bullet item</span></span>
- <span data-ttu-id="6035d-160">第三個項目符號項目</span><span class="sxs-lookup"><span data-stu-id="6035d-160">Third bullet item</span></span>

#### <a name="ordered-lists"></a><span data-ttu-id="6035d-161">已排序清單</span><span class="sxs-lookup"><span data-stu-id="6035d-161">Ordered lists</span></span>

<span data-ttu-id="6035d-162">若要在編號項目底下包含段落或其他元素，請與項目編號後的第一個字元縮排對齊。</span><span class="sxs-lookup"><span data-stu-id="6035d-162">To include a paragraph or other elements under a numbered item, align indentation with the first character after the item number.</span></span> <span data-ttu-id="6035d-163">列出的所有編號項目都應該使用數字 `1.`，而不是遞增每個項目。</span><span class="sxs-lookup"><span data-stu-id="6035d-163">All items in a numbered listed should use the number `1.` rather than incrementing each item.</span></span> <span data-ttu-id="6035d-164">Markdown 轉譯會自動增加值。</span><span class="sxs-lookup"><span data-stu-id="6035d-164">Markdown rendering increments the value automatically.</span></span> <span data-ttu-id="6035d-165">這會讓重新排列項目變得更容易，並標準化附屬內容的縮排。</span><span class="sxs-lookup"><span data-stu-id="6035d-165">This makes reordering items easier and standardizes the indentation of subordinate content.</span></span>

<span data-ttu-id="6035d-166">例如：</span><span class="sxs-lookup"><span data-stu-id="6035d-166">For example:</span></span>

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

<span data-ttu-id="6035d-167">產生的 Markdown 會轉譯如下：</span><span class="sxs-lookup"><span data-stu-id="6035d-167">The resulting Markdown is rendered as follows:</span></span>

1. <span data-ttu-id="6035d-168">針對第一個元素，在 1 之後插入單一空格。</span><span class="sxs-lookup"><span data-stu-id="6035d-168">For the first element, insert a single space after the 1.</span></span> <span data-ttu-id="6035d-169">長句子應該換行到下一行，而且必須與編號清單標記後面的第一個字元對齊。</span><span class="sxs-lookup"><span data-stu-id="6035d-169">Long sentences should be wrapped to the next line and must line up with the first character after the numbered list marker.</span></span>

   <span data-ttu-id="6035d-170">若要包含第二個元素 (例如這個)，在第一個之後插入分行符號並對齊縮排。</span><span class="sxs-lookup"><span data-stu-id="6035d-170">To include a second element (like this one), insert a line break after the first and align indentations.</span></span> <span data-ttu-id="6035d-171">第二個元素的縮排必須與編號清單標記後面的第一個字元對齊。</span><span class="sxs-lookup"><span data-stu-id="6035d-171">The indentation of the second element must line up with the first character after the numbered list marker.</span></span> <span data-ttu-id="6035d-172">針對單位數項目 (例如此處)，您必須縮排到第 4 欄。</span><span class="sxs-lookup"><span data-stu-id="6035d-172">For single digit items, like this one, you indent to column 4.</span></span> <span data-ttu-id="6035d-173">若為雙位數項目 (例如項目編號 10)，則必須縮排到第 5 欄。</span><span class="sxs-lookup"><span data-stu-id="6035d-173">For double digits items, for example item number 10, you indent to column 5.</span></span>

1. <span data-ttu-id="6035d-174">下一個編號項目會從這裡開始。</span><span class="sxs-lookup"><span data-stu-id="6035d-174">The next numbered item starts here.</span></span>

### <a name="formatting-command-syntax-elements"></a><span data-ttu-id="6035d-175">設定命令語法元素格式</span><span class="sxs-lookup"><span data-stu-id="6035d-175">Formatting command syntax elements</span></span>

- <span data-ttu-id="6035d-176">請一律使用 Cmdlet 與參數的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="6035d-176">Always use the full name for cmdlets and parameters.</span></span> <span data-ttu-id="6035d-177">除非您特別示範別名，否則請避免使用別名。</span><span class="sxs-lookup"><span data-stu-id="6035d-177">Avoid using aliases unless you are specifically demonstrating the alias.</span></span>

- <span data-ttu-id="6035d-178">在段落內，語言關鍵字、Cmdlet 名稱、變數與檔案路徑應以倒引號 (`` ` ``) 字元括起來。</span><span class="sxs-lookup"><span data-stu-id="6035d-178">Within a paragraph, language keywords, cmdlet names, variables, and file paths should be wrapped in backtick (`` ` ``) characters.</span></span> <span data-ttu-id="6035d-179">屬性、參數與類別名稱應為**粗體**。</span><span class="sxs-lookup"><span data-stu-id="6035d-179">Property, parameter, and class names should be **bold**.</span></span>

  <span data-ttu-id="6035d-180">例如：</span><span class="sxs-lookup"><span data-stu-id="6035d-180">For example:</span></span>

  ~~~markdown
  The following code uses `Get-ChildItem` to list the contents of `C:\Windows` and assigns
  the output to the `$files` variable.

  ```powershell
  $files = Get-ChildItem C:\Windows
  ```
  ~~~

- <span data-ttu-id="6035d-181">依名稱參考參數時，名稱應為**粗體**。</span><span class="sxs-lookup"><span data-stu-id="6035d-181">When referring to a parameter by name, the name should be **bold**.</span></span> <span data-ttu-id="6035d-182">在說明使用連字號前置詞的參數時，應將參數包裝在倒引號中。</span><span class="sxs-lookup"><span data-stu-id="6035d-182">When illustrating the use of a parameter with the hyphen prefix, the parameter should be wrapped in backticks.</span></span> <span data-ttu-id="6035d-183">例如：</span><span class="sxs-lookup"><span data-stu-id="6035d-183">For example:</span></span>

  ```markdown
  The parameter's name is **Name**, but it is typed as `-Name` when used on the command
  line as a parameter.
  ```

- <span data-ttu-id="6035d-184">參考外部命令 (EXE、指令碼等) 時，命令名稱應為粗體、全部小寫 (如果在句子開頭則第一個字母大寫)，並包含適當的副檔名。</span><span class="sxs-lookup"><span data-stu-id="6035d-184">When referring to external commands (EXEs, scripts, etc.), the command name should be bold, all lowercase (or capitalized if at the beginning of a sentence), and include the appropriate file extension.</span></span> <span data-ttu-id="6035d-185">例如：</span><span class="sxs-lookup"><span data-stu-id="6035d-185">For example:</span></span>

  ```markdown
  For example, on Windows systems, you can use the `net start` and `net stop` commands
  to start and stop a service. **Sc.exe** is another service control tool for Windows.
  That name does not fit into the naming pattern for the **net.exe** service commands.
  ```

- <span data-ttu-id="6035d-186">顯示外部命令的範例使用方式時，應將該範例包裝在倒引號中。</span><span class="sxs-lookup"><span data-stu-id="6035d-186">When showing example usage of an external command, the example should be wrapped in backticks.</span></span>
  <span data-ttu-id="6035d-187">如果名稱與別名衝突，則必須在命令範例中包括副檔名。</span><span class="sxs-lookup"><span data-stu-id="6035d-187">When there is a name collisions with an alias you must include the file extension in the command example.</span></span> <span data-ttu-id="6035d-188">例如：</span><span class="sxs-lookup"><span data-stu-id="6035d-188">For example:</span></span>

  ```markdown
  To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.
  ```

- <span data-ttu-id="6035d-189">撰寫概念性文章 (而非撰寫參考內容) 時，第一個 Cmdlet 名稱執行個體必須能以超連結方式連到該 Cmdlet 文件。</span><span class="sxs-lookup"><span data-stu-id="6035d-189">When writing a conceptual article (as opposed to reference content), the first instance of a cmdlet name should be hyperlinked to the cmdlet documentation.</span></span> <span data-ttu-id="6035d-190">請勿在超連結的括弧內使用倒引號、粗體或其他標記。</span><span class="sxs-lookup"><span data-stu-id="6035d-190">Do not use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>

  <span data-ttu-id="6035d-191">例如：</span><span class="sxs-lookup"><span data-stu-id="6035d-191">For example:</span></span>

  ```markdown
  This [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet
  uses the **Object** parameter to ...
  ```

  <span data-ttu-id="6035d-192">如需詳細資訊，請參閱此文章的[超連結](#hyperlinks)一節。</span><span class="sxs-lookup"><span data-stu-id="6035d-192">For more information, see [Hyperlinks](#hyperlinks) section of this article.</span></span>

### <a name="images"></a><span data-ttu-id="6035d-193">影像</span><span class="sxs-lookup"><span data-stu-id="6035d-193">Images</span></span>

<span data-ttu-id="6035d-194">包含影像的語法為：</span><span class="sxs-lookup"><span data-stu-id="6035d-194">The syntax to include an image is:</span></span>

```markdown
![[alt text]](<folderPath>)

Example:
![Introduction](./media/overview/Introduction.png)
```

<span data-ttu-id="6035d-195">其中 `alt text` 是影像的簡短描述，而 `<folder path>` 是影像的相對路徑。</span><span class="sxs-lookup"><span data-stu-id="6035d-195">Where `alt text` is a brief description of the image and `<folder path>` is a relative path to the image.</span></span> <span data-ttu-id="6035d-196">視障人士的螢幕助讀程式需要替代文字。</span><span class="sxs-lookup"><span data-stu-id="6035d-196">Alternate text is required for screen readers for the visually impaired.</span></span> <span data-ttu-id="6035d-197">如果存在無法轉譯影像的網站錯誤 (Bug)，這也很有用。</span><span class="sxs-lookup"><span data-stu-id="6035d-197">It is also useful in case there is a site bug where the image cannot be rendered.</span></span>

<span data-ttu-id="6035d-198">影像應儲存在包含文章之資料夾內的 `media/<article-name>` 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="6035d-198">Images should be stored in a `media/<article-name>` folder within the folder containing the article.</span></span>
<span data-ttu-id="6035d-199">不應在文章之間共用影像。</span><span class="sxs-lookup"><span data-stu-id="6035d-199">Images should not be shared between articles.</span></span> <span data-ttu-id="6035d-200">在 `media` 資料夾底下，建立符合您文章檔案名稱的資料夾。</span><span class="sxs-lookup"><span data-stu-id="6035d-200">Create a folder that matches the filename of your article under the `media` folder.</span></span> <span data-ttu-id="6035d-201">將該文章的影像複製到該新資料夾。</span><span class="sxs-lookup"><span data-stu-id="6035d-201">Copy the images for that article to that new folder.</span></span> <span data-ttu-id="6035d-202">如果某個影像由多個文章使用，每個影像資料夾都必須有該影像檔案的複本。</span><span class="sxs-lookup"><span data-stu-id="6035d-202">If an image is used by multiple articles, each image folder must have a copy of that image file.</span></span> <span data-ttu-id="6035d-203">這種做法可防止變更一篇文章中的影像而影響另一篇文章。</span><span class="sxs-lookup"><span data-stu-id="6035d-203">This practice prevents a change to an image in one article affecting another article.</span></span>

<span data-ttu-id="6035d-204">支援下列影像檔案類型：`*.png`、`*.gif`、`*.jpeg`、`*.jpg`、`*.svg`</span><span class="sxs-lookup"><span data-stu-id="6035d-204">The following image file types are supported: `*.png`, `*.gif`, `*.jpeg`, `*.jpg`, `*.svg`</span></span>

### <a name="markdown-extensions-supported-by-open-publishing"></a><span data-ttu-id="6035d-205">Open Publishing 支援的 Markdown 延伸模組</span><span class="sxs-lookup"><span data-stu-id="6035d-205">Markdown extensions supported by Open Publishing</span></span>

<span data-ttu-id="6035d-206">[Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) 包含支援我們發佈系統特有功能的工具。</span><span class="sxs-lookup"><span data-stu-id="6035d-206">The [Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) contains tools that support features unique to our publishing system.</span></span> <span data-ttu-id="6035d-207">警示是 Markdown 延伸模組，用來建立在 docs.microsoft.com 上轉譯的區塊引號，並以色彩與圖示指出內容的重要性。</span><span class="sxs-lookup"><span data-stu-id="6035d-207">Alerts are a Markdown extension to create block quotes that render on docs.microsoft.com with colors and icons that indicate the significance of the content.</span></span> <span data-ttu-id="6035d-208">支援下列警示類型：</span><span class="sxs-lookup"><span data-stu-id="6035d-208">The following alert types are supported:</span></span>

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

<span data-ttu-id="6035d-209">這些警示在 docs.microsoft.com 上看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="6035d-209">These alerts look like this on docs.microsoft.com:</span></span>

> [!NOTE]
> <span data-ttu-id="6035d-210">即使略讀，使用者也應該注意的資訊。</span><span class="sxs-lookup"><span data-stu-id="6035d-210">Information the user should notice even if skimming.</span></span>

> [!TIP]
> <span data-ttu-id="6035d-211">可協助使用者更成功的選擇性資訊。</span><span class="sxs-lookup"><span data-stu-id="6035d-211">Optional information to help a user be more successful.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6035d-212">使用者成功所需的基本資訊。</span><span class="sxs-lookup"><span data-stu-id="6035d-212">Essential information required for user success.</span></span>

> [!CAUTION]
> <span data-ttu-id="6035d-213">動作的潛在負面後果。</span><span class="sxs-lookup"><span data-stu-id="6035d-213">Negative potential consequences of an action.</span></span>

> [!WARNING]
> <span data-ttu-id="6035d-214">動作的危險特定結果。</span><span class="sxs-lookup"><span data-stu-id="6035d-214">Dangerous certain consequences of an action.</span></span>

## <a name="hyperlinks"></a><span data-ttu-id="6035d-215">超連結</span><span class="sxs-lookup"><span data-stu-id="6035d-215">Hyperlinks</span></span>

- <span data-ttu-id="6035d-216">避免使用單純網址 (Bare URL)。</span><span class="sxs-lookup"><span data-stu-id="6035d-216">Avoid using bare URLs.</span></span> <span data-ttu-id="6035d-217">連結應該使用 Markdown 語法 `[friendlyname](url-or-path)`</span><span class="sxs-lookup"><span data-stu-id="6035d-217">Links should use Markdown syntax `[friendlyname](url-or-path)`</span></span>
- <span data-ttu-id="6035d-218">必要時，可以使用單純網址，但應包含在倒引號中。</span><span class="sxs-lookup"><span data-stu-id="6035d-218">Bare URLs may be used when necessary, but should be enclosed in backticks.</span></span> <span data-ttu-id="6035d-219">例如：</span><span class="sxs-lookup"><span data-stu-id="6035d-219">For example:</span></span>

  ```markdown
  By default, if you do not specify this parameter, the DMTF standard resource URI
  `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.
  ```

- <span data-ttu-id="6035d-220">URL 連結應該是 HTTPS (可能的話)。</span><span class="sxs-lookup"><span data-stu-id="6035d-220">URL links should be HTTPS when possible.</span></span>
- <span data-ttu-id="6035d-221">連結必須具有易記名稱，通常是連結主題的標題</span><span class="sxs-lookup"><span data-stu-id="6035d-221">Links must have a friendly name, usually the title of the linked topic</span></span>
- <span data-ttu-id="6035d-222">位於底部＜相關連結＞一節中的所有項目，都應該是超連結。</span><span class="sxs-lookup"><span data-stu-id="6035d-222">All items in the "related links" section at the bottom should be hyperlinked.</span></span>
- <span data-ttu-id="6035d-223">請勿在超連結的括弧內使用倒引號、粗體或其他標記。</span><span class="sxs-lookup"><span data-stu-id="6035d-223">Do not use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>

### <a name="linking-to-other-content"></a><span data-ttu-id="6035d-224">連結至其他內容</span><span class="sxs-lookup"><span data-stu-id="6035d-224">Linking to other content</span></span>

<span data-ttu-id="6035d-225">發佈系統支援兩種類型的超連結：URL 與檔案連結。</span><span class="sxs-lookup"><span data-stu-id="6035d-225">There are two types of hyperlinks supported by the publishing system: URLs and file links.</span></span>

<span data-ttu-id="6035d-226">URL 連結可以是相對於 docs.microsoft.com 根目錄的 URL 路徑。</span><span class="sxs-lookup"><span data-stu-id="6035d-226">A URL link can be a URL path that is relative to the root of docs.microsoft.com.</span></span> <span data-ttu-id="6035d-227">或包含完整 URL 語法的絕對 URL。</span><span class="sxs-lookup"><span data-stu-id="6035d-227">Or an absolute URL that include the full URL syntax.</span></span> <span data-ttu-id="6035d-228">(例如：`https:/github.com/MicrosoftDocs/PowerShell-Docs`)</span><span class="sxs-lookup"><span data-stu-id="6035d-228">(For example: `https:/github.com/MicrosoftDocs/PowerShell-Docs`)</span></span>

- <span data-ttu-id="6035d-229">連結至 PowerShell-Docs 以外的內容，或在 Cmdlet 參考與 PowerShell-docs 中的概念性文章之間連結時，請使用 URL 連結。</span><span class="sxs-lookup"><span data-stu-id="6035d-229">Use URL links when linking to content outside of PowerShell-Docs or between cmdlet reference and conceptual articles within PowerShell-docs.</span></span>
- <span data-ttu-id="6035d-230">建立相對連結最簡單的方式是從瀏覽器複製 URL，然後從您貼到 Markdown 的值中移除 `https://docs.microsoft.com/en-us`。</span><span class="sxs-lookup"><span data-stu-id="6035d-230">The simplest way to link create a relative link is to copy the URL from your browser then remove `https://docs.microsoft.com/en-us` from the value you paste into markdown.</span></span>
   - <span data-ttu-id="6035d-231">請勿在 Microsoft 內容的 URL 中包含地區設定 (例如，</span><span class="sxs-lookup"><span data-stu-id="6035d-231">Do not include locales in URLs on Microsoft properties (eg.</span></span> <span data-ttu-id="6035d-232">從 URL 移除 "/en-us")。</span><span class="sxs-lookup"><span data-stu-id="6035d-232">remove "/en-us" from URL).</span></span>
- <span data-ttu-id="6035d-233">針對外部網站的所有 URL 都應該使用 HTTPS，除非目標網站不適用。</span><span class="sxs-lookup"><span data-stu-id="6035d-233">All URLs to external websites should use HTTPS unless that is not valid for the target site.</span></span>

<span data-ttu-id="6035d-234">檔案連結是用來從一篇參考文章連結至另一篇，或從某篇概念性文章連結至另一篇。</span><span class="sxs-lookup"><span data-stu-id="6035d-234">A file link is used to link from one reference article to another, or from one conceptual article to another.</span></span> <span data-ttu-id="6035d-235">如果您需要連結至特定 PowerShell 版本的參考文章，則必須使用 URL 連結。</span><span class="sxs-lookup"><span data-stu-id="6035d-235">If you need to link to a reference article for a specific version of PowerShell, then you need to use a URL link.</span></span>

- <span data-ttu-id="6035d-236">檔案連結包含相對檔案路徑 (例如：`../folder/file.md`)</span><span class="sxs-lookup"><span data-stu-id="6035d-236">File links contain a relative file path (for example: `../folder/file.md`)</span></span>
- <span data-ttu-id="6035d-237">所有檔案路徑都使用正斜線 (`/`) 字元</span><span class="sxs-lookup"><span data-stu-id="6035d-237">All file paths use forward-slash (`/`) characters</span></span>

## <a name="formatting-code-samples"></a><span data-ttu-id="6035d-238">格式化程式碼範例</span><span class="sxs-lookup"><span data-stu-id="6035d-238">Formatting code samples</span></span>

<span data-ttu-id="6035d-239">Markdown 支援兩種不同的程式碼樣式：</span><span class="sxs-lookup"><span data-stu-id="6035d-239">Markdown supports two different code styles:</span></span>

- <span data-ttu-id="6035d-240">程式碼延伸 (內嵌) - 以單一倒引號 (`` ` ``) 字元標記。</span><span class="sxs-lookup"><span data-stu-id="6035d-240">Code spans (inline) - marked by a single backtick (`` ` ``) character.</span></span> <span data-ttu-id="6035d-241">用於段落內，而不是作為獨立區塊。</span><span class="sxs-lookup"><span data-stu-id="6035d-241">Used within a paragraph rather than as a standalone block.</span></span>
- <span data-ttu-id="6035d-242">程式碼區塊 - 以三倒引號 (`` ``` ``) 字串括住的多行區塊。</span><span class="sxs-lookup"><span data-stu-id="6035d-242">Code blocks - a multi-line block surrounded by triple-backtick (`` ``` ``) strings.</span></span> <span data-ttu-id="6035d-243">程式碼區塊在倒引號之後可能也會有語言標籤。</span><span class="sxs-lookup"><span data-stu-id="6035d-243">Code blocks may also have a language label following the backticks.</span></span> <span data-ttu-id="6035d-244">語言標籤會針對程式碼區塊的內容啟用語法醒目提示。</span><span class="sxs-lookup"><span data-stu-id="6035d-244">The language label enables syntax highlighting for the contents of the code block.</span></span>

### <a name="using-code-blocks"></a><span data-ttu-id="6035d-245">使用程式碼區塊</span><span class="sxs-lookup"><span data-stu-id="6035d-245">Using code blocks</span></span>

<span data-ttu-id="6035d-246">Markdown 允許縮排表示程式碼區塊，但是這種模式可能會出現問題，應予以避免。</span><span class="sxs-lookup"><span data-stu-id="6035d-246">Markdown allows for indentation to signify a code block, but this pattern can be problematic and should be avoided.</span></span> <span data-ttu-id="6035d-247">所有程式碼區塊都應該包含在程式碼柵欄中。</span><span class="sxs-lookup"><span data-stu-id="6035d-247">All code blocks should be contained in a code fence.</span></span> <span data-ttu-id="6035d-248">程式碼柵欄是以三倒引號 (`` ``` ``) 字串括住的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="6035d-248">A code fence is a block of code surrounded by triple-backtick (`` ``` ``) strings.</span></span> <span data-ttu-id="6035d-249">程式碼柵欄標記本身必須位於程式碼範例前後的一行中。</span><span class="sxs-lookup"><span data-stu-id="6035d-249">The code fence markers must be on their own line before and after the code sample.</span></span> <span data-ttu-id="6035d-250">程式碼區塊開頭的標記可能會有選擇性的語言標籤。</span><span class="sxs-lookup"><span data-stu-id="6035d-250">The marker at the start of the code block may have an optional language label.</span></span> <span data-ttu-id="6035d-251">Microsoft 的 Open Publishing System (OPS) 使用語言標籤來支援語法醒目提示功能。</span><span class="sxs-lookup"><span data-stu-id="6035d-251">Microsoft's Open Publishing System (OPS) uses the language label to support the syntax highlighting feature.</span></span>

<span data-ttu-id="6035d-252">OPS 也新增了 [複製]  按鈕，可將程式碼區塊的內容複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="6035d-252">OPS also adds a **Copy** button that copies the contents of the code block to the clipboard.</span></span> <span data-ttu-id="6035d-253">這可讓您快速地將程式碼貼到指令碼中，以測試程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="6035d-253">This allows you to quickly paste the code into a script for testing the code example.</span></span> <span data-ttu-id="6035d-254">不過，並非文件中的所有範例都是可執行的。</span><span class="sxs-lookup"><span data-stu-id="6035d-254">However, not all examples in our documentation are intended to be run.</span></span> <span data-ttu-id="6035d-255">某些程式碼區塊是 PowerShell 概念的簡單圖解。</span><span class="sxs-lookup"><span data-stu-id="6035d-255">Some code blocks are simple illustrations of a PowerShell concept.</span></span>

<span data-ttu-id="6035d-256">我們的文件中使用了兩種類型的程式碼區塊：</span><span class="sxs-lookup"><span data-stu-id="6035d-256">There are two types code blocks used in our documentation:</span></span>

1. <span data-ttu-id="6035d-257">說明範例</span><span class="sxs-lookup"><span data-stu-id="6035d-257">Illustrative examples</span></span>
2. <span data-ttu-id="6035d-258">可執行檔範例</span><span class="sxs-lookup"><span data-stu-id="6035d-258">Executable examples</span></span>

### <a name="syntax-code-blocks"></a><span data-ttu-id="6035d-259">語法程式碼區塊</span><span class="sxs-lookup"><span data-stu-id="6035d-259">Syntax code blocks</span></span>

<span data-ttu-id="6035d-260">此範例說明 `Get-Command` Cmdlet 的所有可能參數。</span><span class="sxs-lookup"><span data-stu-id="6035d-260">This example illustrates all the possible parameters of the `Get-Command` cmdlet.</span></span>

~~~markdown
```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
  [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax] [-ShowCommandInfo]
  [[-ArgumentList] <Object[]>] [-All] [-ListImported] [-ParameterName <String[]>]
  [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```
~~~

<span data-ttu-id="6035d-261">此範例以一般字詞描述 `for` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="6035d-261">This example describes the `for` statement in generalized terms:</span></span>

~~~markdown
```
for (<init>; <condition>; <repeat>)
{<statement list>}
```
~~~

### <a name="illustrative-examples"></a><span data-ttu-id="6035d-262">說明範例</span><span class="sxs-lookup"><span data-stu-id="6035d-262">Illustrative examples</span></span>

<span data-ttu-id="6035d-263">說明範例是用來說明 PowerShell 概念。</span><span class="sxs-lookup"><span data-stu-id="6035d-263">Illustrative examples are used to explain a PowerShell concept.</span></span> <span data-ttu-id="6035d-264">它們不應該複製到剪貼簿來執行。</span><span class="sxs-lookup"><span data-stu-id="6035d-264">They are not meant to be copied to the clipboard for execution.</span></span> <span data-ttu-id="6035d-265">這些最常用於容易輸入的簡單範例。</span><span class="sxs-lookup"><span data-stu-id="6035d-265">These are most commonly used for simple examples that are easy to type.</span></span>
<span data-ttu-id="6035d-266">其也會用於語法範例，其中您會說明命令的語法。</span><span class="sxs-lookup"><span data-stu-id="6035d-266">They are also used for syntax examples where you are illustrating the syntax of a command.</span></span> <span data-ttu-id="6035d-267">程式碼區塊可能包含所說明之命令的範例輸出。</span><span class="sxs-lookup"><span data-stu-id="6035d-267">The code block may contain example output from the command being illustrated.</span></span>

<span data-ttu-id="6035d-268">以下是說明 PowerShell 比較運算子的簡單範例：</span><span class="sxs-lookup"><span data-stu-id="6035d-268">Here is a simple example illustrating a PowerShell comparison operators:</span></span>

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

<span data-ttu-id="6035d-269">請注意，此範例具有簡化的 PowerShell 提示，並會顯示產生的輸出。</span><span class="sxs-lookup"><span data-stu-id="6035d-269">Note that this example has the simplified PowerShell prompt and shows the resulting output.</span></span> <span data-ttu-id="6035d-270">在此案例中，我們不希望讀者複製並執行此範例。</span><span class="sxs-lookup"><span data-stu-id="6035d-270">In this case, we don't intend the reader to copy and run this example.</span></span>

### <a name="executable-examples"></a><span data-ttu-id="6035d-271">可執行的範例</span><span class="sxs-lookup"><span data-stu-id="6035d-271">Executable examples</span></span>

<span data-ttu-id="6035d-272">更複雜的範例或對複製及執行有用的範例，應使用下列區塊樣式標記：</span><span class="sxs-lookup"><span data-stu-id="6035d-272">More complex examples or examples that are intended to be useful to copy and execute should use the following block-style markup:</span></span>

~~~markdown
```powershell
<PowerShell code goes here>
```
~~~

<span data-ttu-id="6035d-273">PowerShell 命令所顯示的輸出應該包含在 **Output** 程式碼區塊中，以避免語法醒目提示。</span><span class="sxs-lookup"><span data-stu-id="6035d-273">The output displayed by PowerShell commands should be enclosed in an **Output** code block to prevent syntax highlighting.</span></span> <span data-ttu-id="6035d-274">例如：</span><span class="sxs-lookup"><span data-stu-id="6035d-274">For example:</span></span>

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

<span data-ttu-id="6035d-275">**Output** 程式碼標籤不是語法醒目提示系統所支援的官方「語言」。</span><span class="sxs-lookup"><span data-stu-id="6035d-275">The **Output** code label is not an official "language" supported by the syntax highlighting system.</span></span>
<span data-ttu-id="6035d-276">不過，此標籤很有用，因為 OPS 會將 "Output" 標籤新增至網頁上的程式碼方塊框架。</span><span class="sxs-lookup"><span data-stu-id="6035d-276">However, this label is useful because OPS adds the "Output" label to the code box frame on the web page.</span></span> <span data-ttu-id="6035d-277">"Output" 程式碼方塊沒有語法醒目提示。</span><span class="sxs-lookup"><span data-stu-id="6035d-277">The "Output" code box has no syntax highlighting.</span></span>

## <a name="coding-style-rules"></a><span data-ttu-id="6035d-278">程式碼撰寫樣式規則</span><span class="sxs-lookup"><span data-stu-id="6035d-278">Coding style rules</span></span>

### <a name="avoid-line-continuation-in-code-samples"></a><span data-ttu-id="6035d-279">避免程式碼範例中的行接續</span><span class="sxs-lookup"><span data-stu-id="6035d-279">Avoid line continuation in code samples</span></span>

<span data-ttu-id="6035d-280">避免在 PowerShell 程式碼範例中使用行接續字元 (`` ` ``)。</span><span class="sxs-lookup"><span data-stu-id="6035d-280">Avoid using line continuation characters (`` ` ``) in PowerShell code examples.</span></span> <span data-ttu-id="6035d-281">這些字元很難看到，如果行尾有多餘的空格，可能會造成問題。</span><span class="sxs-lookup"><span data-stu-id="6035d-281">These are hard to see and can cause problems if there are extra spaces at the end of the line.</span></span>

- <span data-ttu-id="6035d-282">使用 PowerShell 展開來減少具有大量參數之 Cmdlet 的行長度。</span><span class="sxs-lookup"><span data-stu-id="6035d-282">Use PowerShell splatting to reduce line length for cmdlets that have a lot of parameters.</span></span>
- <span data-ttu-id="6035d-283">利用 PowerShell 的自然換行機會，像是管道 (`|`) 字元、左括弧、括弧和方括弧之後。</span><span class="sxs-lookup"><span data-stu-id="6035d-283">Take advantage of PowerShell's natural line break opportunities, like after pipe (`|`) characters, opening braces, parentheses, and brackets.</span></span>

### <a name="avoid-using-powershell-prompts-in-examples"></a><span data-ttu-id="6035d-284">避免在範例中使用 PowerShell 提示字元</span><span class="sxs-lookup"><span data-stu-id="6035d-284">Avoid using PowerShell prompts in examples</span></span>

<span data-ttu-id="6035d-285">不建議使用提示字元字串，而且應該僅限於用來說明命令列使用方式的情節。</span><span class="sxs-lookup"><span data-stu-id="6035d-285">Use of the prompt string is discouraged and should be limited to scenarios that are meant to illustrate command line usage.</span></span> <span data-ttu-id="6035d-286">對於大多數這些範例，提示字元字串應該為 `PS>`。</span><span class="sxs-lookup"><span data-stu-id="6035d-286">For most of these examples, the prompt string should be `PS>`.</span></span> <span data-ttu-id="6035d-287">這個提示字元與 OS 特有的指標無關。</span><span class="sxs-lookup"><span data-stu-id="6035d-287">This prompt is independent of OS-specific indicators.</span></span>

<span data-ttu-id="6035d-288">如需說明會改變提示字元的命令，或顯示的路徑對所示案例很重要的範例，則需要提示字元。</span><span class="sxs-lookup"><span data-stu-id="6035d-288">Prompts are required for examples that illustrate commands that alter the prompt or when the path displayed is significant to the scenario being illustrated.</span></span> <span data-ttu-id="6035d-289">下列範例說明當使用登錄提供者時，提示字元的變更方式。</span><span class="sxs-lookup"><span data-stu-id="6035d-289">The following example illustrates how the prompt changes when using the Registry provider.</span></span>

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

### <a name="do-not-use-aliases-in-examples"></a><span data-ttu-id="6035d-290">請勿在範例中使用別名</span><span class="sxs-lookup"><span data-stu-id="6035d-290">Do not use aliases in examples</span></span>

<span data-ttu-id="6035d-291">除非您特別討論別名，否則請一律使用所有 Cmdlet 與參數的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="6035d-291">You should always use the full name of all cmdlets and parameters unless you are specifically talking about the alias.</span></span> <span data-ttu-id="6035d-292">Cmdlet 與參數名稱必須使用程式碼中所定義的正確拼寫。</span><span class="sxs-lookup"><span data-stu-id="6035d-292">Cmdlet and parameter names must use the proper spelling defined in the code.</span></span>

### <a name="using-parameters-in-examples"></a><span data-ttu-id="6035d-293">在範例中使用參數</span><span class="sxs-lookup"><span data-stu-id="6035d-293">Using parameters in examples</span></span>

<span data-ttu-id="6035d-294">避免使用位置參數。</span><span class="sxs-lookup"><span data-stu-id="6035d-294">Avoid using positional parameters.</span></span> <span data-ttu-id="6035d-295">一般來說，即使是位置參數，您也應該在範例中使用 [一律包含參數名稱]。</span><span class="sxs-lookup"><span data-stu-id="6035d-295">In general, you should use always include the parameter name in an example, even if the parameter positional.</span></span> <span data-ttu-id="6035d-296">這可減少您的範例中產生混淆的機會。</span><span class="sxs-lookup"><span data-stu-id="6035d-296">This reduces the chance of confusion in your examples.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6035d-297">後續步驟</span><span class="sxs-lookup"><span data-stu-id="6035d-297">Next steps</span></span>

[<span data-ttu-id="6035d-298">編輯 Cmdlet 參考</span><span class="sxs-lookup"><span data-stu-id="6035d-298">Editing cmdlet reference</span></span>](editing-cmdlet-ref.md)

<!-- External URLs -->
[platyPS]: https://github.com/PowerShell/platyPS
[markdig]: https://github.com/lunet-io/markdig \(英文\)
[CommonMark]: https://spec.commonmark.org/ \(英文\)
[atx]: https://github.github.com/gfm/#atx-headings
[pascal-case]: https://en.wikipedia.org/wiki/PascalCase
[reflow]: https://marketplace.visualstudio.com/items?itemName=marvhen.reflow-markdown
