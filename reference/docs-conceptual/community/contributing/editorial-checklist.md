---
title: 編輯檢查清單
description: 這是編輯 PowerShell 文件之規則的摘要清單。
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 511e0c323e1a3256039e819d06f32f6e1ac42767
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/10/2020
ms.locfileid: "79060333"
---
# <a name="editors-checklist"></a><span data-ttu-id="b1b86-103">編輯的檢查清單</span><span class="sxs-lookup"><span data-stu-id="b1b86-103">Editor's checklist</span></span>

<span data-ttu-id="b1b86-104">這是在撰寫新文章或更新現有文章時應套用之規則的摘要。</span><span class="sxs-lookup"><span data-stu-id="b1b86-104">This is a summary of rules to apply when writing new or updating existing articles.</span></span> <span data-ttu-id="b1b86-105">請參閱《參與者指南》中的其他文章，以取得這些規則的詳細說明與範例。</span><span class="sxs-lookup"><span data-stu-id="b1b86-105">See other articles in the Contributor's Guide for detailed explanations and examples of these rules.</span></span>

## <a name="metadata"></a><span data-ttu-id="b1b86-106">中繼資料</span><span class="sxs-lookup"><span data-stu-id="b1b86-106">Metadata</span></span>

- <span data-ttu-id="b1b86-107">`ms.date`：格式必須為 **MM/DD/YYYY**</span><span class="sxs-lookup"><span data-stu-id="b1b86-107">`ms.date`: must be in the format **MM/DD/YYYY**</span></span>
  - <span data-ttu-id="b1b86-108">在做出重大或事實更新時，請變更日期</span><span class="sxs-lookup"><span data-stu-id="b1b86-108">Change the date when there is a significant or factual update</span></span>
    - <span data-ttu-id="b1b86-109">重新組織文章</span><span class="sxs-lookup"><span data-stu-id="b1b86-109">Reorganizing the article</span></span>
    - <span data-ttu-id="b1b86-110">修正事實錯誤</span><span class="sxs-lookup"><span data-stu-id="b1b86-110">Fixing factual errors</span></span>
    - <span data-ttu-id="b1b86-111">加入新資訊</span><span class="sxs-lookup"><span data-stu-id="b1b86-111">Adding new information</span></span>
  - <span data-ttu-id="b1b86-112">如果更新內容無足輕重，請勿變更日期</span><span class="sxs-lookup"><span data-stu-id="b1b86-112">Do not change the date if the update is insignificant</span></span>
    - <span data-ttu-id="b1b86-113">修正錯字與格式</span><span class="sxs-lookup"><span data-stu-id="b1b86-113">Fixing typos and formatting</span></span>
- <span data-ttu-id="b1b86-114">`title`：43-59 個字元的唯一字串 (包括空格)</span><span class="sxs-lookup"><span data-stu-id="b1b86-114">`title`: unique string of 43-59 chars including spaces</span></span>
  - <span data-ttu-id="b1b86-115">請勿包含網站識別碼 (會自動產生)</span><span class="sxs-lookup"><span data-stu-id="b1b86-115">Do not include site identifier (it is auto-generated)</span></span>
  - <span data-ttu-id="b1b86-116">使用句首大寫，也就是指將第一個文字及任何專有名詞以大寫字母輸入</span><span class="sxs-lookup"><span data-stu-id="b1b86-116">Use sentence case - capitalize only the first word and any proper nouns</span></span>
- <span data-ttu-id="b1b86-117">`description`:115-145 個字元 (包括空格)，此摘要會顯示於搜尋結果中</span><span class="sxs-lookup"><span data-stu-id="b1b86-117">`description`: 115-145 characters including spaces - this abstract displays in the search result</span></span>

## <a name="formatting"></a><span data-ttu-id="b1b86-118">格式化</span><span class="sxs-lookup"><span data-stu-id="b1b86-118">Formatting</span></span>

- <span data-ttu-id="b1b86-119">以內嵌方式顯示在段落內的倒引號語法元素</span><span class="sxs-lookup"><span data-stu-id="b1b86-119">Backtick syntax elements that appear, inline, within a paragraph</span></span>
  - <span data-ttu-id="b1b86-120">Cmdlet 名稱 `Verb-Noun`</span><span class="sxs-lookup"><span data-stu-id="b1b86-120">Cmdlet names `Verb-Noun`</span></span>
  - <span data-ttu-id="b1b86-121">變數 `$counter`</span><span class="sxs-lookup"><span data-stu-id="b1b86-121">Variable `$counter`</span></span>
  - <span data-ttu-id="b1b86-122">語法範例 `Verb-Noun -Parameter`</span><span class="sxs-lookup"><span data-stu-id="b1b86-122">Syntactic examples `Verb-Noun -Parameter`</span></span>
  - <span data-ttu-id="b1b86-123">檔案路徑 `C:\Program Files\PowerShell`、`/usr/bin/pwsh`</span><span class="sxs-lookup"><span data-stu-id="b1b86-123">File paths `C:\Program Files\PowerShell`, `/usr/bin/pwsh`</span></span>
  - <span data-ttu-id="b1b86-124">文件中不應該可點選的 URL</span><span class="sxs-lookup"><span data-stu-id="b1b86-124">URLs that are not meant to be clickable in the document</span></span>
- <span data-ttu-id="b1b86-125">針對屬性名稱、參數值、參數名稱、類別名稱、模組名稱、實體名稱、物件或類型名稱使用粗體</span><span class="sxs-lookup"><span data-stu-id="b1b86-125">Use bold for property names, parameter values, parameter names, class names, module names, entity names, object or type names</span></span>
  - <span data-ttu-id="b1b86-126">粗體是用於語意標記，不是用來強調</span><span class="sxs-lookup"><span data-stu-id="b1b86-126">Bold is used for semantic markup, not emphasis</span></span>
  - <span data-ttu-id="b1b86-127">粗體：使用星號 `**`</span><span class="sxs-lookup"><span data-stu-id="b1b86-127">Bold - use asterisks `**`</span></span>
- <span data-ttu-id="b1b86-128">斜體：使用底線 `_`</span><span class="sxs-lookup"><span data-stu-id="b1b86-128">Italic - use underscore `_`</span></span>
  - <span data-ttu-id="b1b86-129">僅用來強調，不是用於語意標記</span><span class="sxs-lookup"><span data-stu-id="b1b86-129">Only used for emphasis, not for semantic markup</span></span>
- <span data-ttu-id="b1b86-130">於第 100 欄使用分行符號 (針對 **about_Topics** 則為第 80 欄)</span><span class="sxs-lookup"><span data-stu-id="b1b86-130">Line breaks at 100 columns (or at 80 for **about_Topics**)</span></span>
- <span data-ttu-id="b1b86-131">勿使用硬式 Tab，僅使用空格</span><span class="sxs-lookup"><span data-stu-id="b1b86-131">No hard tabs - use spaces only</span></span>
- <span data-ttu-id="b1b86-132">在行上勿使用尾端空格</span><span class="sxs-lookup"><span data-stu-id="b1b86-132">No trailing spaces on lines</span></span>

### <a name="headers"></a><span data-ttu-id="b1b86-133">headers</span><span class="sxs-lookup"><span data-stu-id="b1b86-133">Headers</span></span>

- <span data-ttu-id="b1b86-134">H1 為第一；每篇文章僅能有一個 H1</span><span class="sxs-lookup"><span data-stu-id="b1b86-134">H1 is first - only one H1 per article</span></span>
- <span data-ttu-id="b1b86-135">僅使用 [ATX 標頭](https://github.github.com/gfm/#atx-headings) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="b1b86-135">Use [ATX Headers](https://github.github.com/gfm/#atx-headings) only</span></span>
- <span data-ttu-id="b1b86-136">針對所有標頭使用句首大寫</span><span class="sxs-lookup"><span data-stu-id="b1b86-136">Use sentence case for all headers</span></span>
- <span data-ttu-id="b1b86-137">勿略過層級 (在沒有 H2 的情況下便不能有 H3)</span><span class="sxs-lookup"><span data-stu-id="b1b86-137">Do not skip levels - no H3 without an H2</span></span>
- <span data-ttu-id="b1b86-138">最大深度為 H3 或 H4</span><span class="sxs-lookup"><span data-stu-id="b1b86-138">Max depth of H3 or H4</span></span>
- <span data-ttu-id="b1b86-139">在前後都使用空白行</span><span class="sxs-lookup"><span data-stu-id="b1b86-139">Blank line before and after</span></span>
- <span data-ttu-id="b1b86-140">PlatyPS 會在其結構描述中強制使用特定標頭，請不要加入或移除標頭</span><span class="sxs-lookup"><span data-stu-id="b1b86-140">PlatyPS enforces specific headers in its schema - do not add or remove headers</span></span>

### <a name="code-blocks"></a><span data-ttu-id="b1b86-141">程式碼區塊</span><span class="sxs-lookup"><span data-stu-id="b1b86-141">Code blocks</span></span>

- <span data-ttu-id="b1b86-142">在前後都使用空白行</span><span class="sxs-lookup"><span data-stu-id="b1b86-142">Blank line before and after</span></span>
- <span data-ttu-id="b1b86-143">使用已標記的程式碼柵欄：**powershell**、**Output** 或其他適當的語言識別碼</span><span class="sxs-lookup"><span data-stu-id="b1b86-143">Use tagged code fences - **powershell**, **Output**, or other appropriate language ID</span></span>
- <span data-ttu-id="b1b86-144">未標記的柵欄：語法區塊或其他殼層</span><span class="sxs-lookup"><span data-stu-id="b1b86-144">Untagged fence - syntax blocks or other shells</span></span>
- <span data-ttu-id="b1b86-145">除了您不想讓讀者使用 [Copy]  \(複製\) 按鈕的簡單範例以外，請將 [Output]  \(輸出\) 置於個別的程式碼區塊</span><span class="sxs-lookup"><span data-stu-id="b1b86-145">Put **Output** in separate code block except for simple examples where you don't intend the for the reader to use the **Copy** button</span></span>
- <span data-ttu-id="b1b86-146">請參閱[支援的語言](/contribute/code-in-docs#supported-languages)清單</span><span class="sxs-lookup"><span data-stu-id="b1b86-146">See list of [supported languages](/contribute/code-in-docs#supported-languages)</span></span>

### <a name="lists"></a><span data-ttu-id="b1b86-147">清單</span><span class="sxs-lookup"><span data-stu-id="b1b86-147">Lists</span></span>

- <span data-ttu-id="b1b86-148">已適當縮排</span><span class="sxs-lookup"><span data-stu-id="b1b86-148">Indented properly</span></span>
- <span data-ttu-id="b1b86-149">在第一個項目之前與最後一個項目之後使用空白行</span><span class="sxs-lookup"><span data-stu-id="b1b86-149">Blank line before first item and after last item</span></span>
- <span data-ttu-id="b1b86-150">項目符號：請使用連字號 (`-`) 而非星號 (`*`)，因為星號太容易與強調混淆</span><span class="sxs-lookup"><span data-stu-id="b1b86-150">Bullet - use hyphen (`-`) not asterisk (`*`) - too easy to confuse with emphasis</span></span>
- <span data-ttu-id="b1b86-151">針對編號清單，所有數字都是 "1."</span><span class="sxs-lookup"><span data-stu-id="b1b86-151">For numbered lists, all numbers are "1."</span></span>

## <a name="terminology"></a><span data-ttu-id="b1b86-152">詞彙</span><span class="sxs-lookup"><span data-stu-id="b1b86-152">Terminology</span></span>

- <span data-ttu-id="b1b86-153">PowerShell 與Windows PowerShell 與PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="b1b86-153">PowerShell vs. Windows PowerShell vs. PowerShell Core</span></span>
- <span data-ttu-id="b1b86-154">請參閱[產品術語](powershell-style-guide.md#product-terminology)</span><span class="sxs-lookup"><span data-stu-id="b1b86-154">See [Product Terminology](powershell-style-guide.md#product-terminology)</span></span>

## <a name="cmdlet-reference-examples"></a><span data-ttu-id="b1b86-155">Cmdlet 參考範例</span><span class="sxs-lookup"><span data-stu-id="b1b86-155">Cmdlet reference examples</span></span>

- <span data-ttu-id="b1b86-156">至少必須有一個 Cmdlet 參考的範例</span><span class="sxs-lookup"><span data-stu-id="b1b86-156">Must have at least one example in cmdlet reference</span></span>
- <span data-ttu-id="b1b86-157">範例應該包含剛好足以示範使用方式的程式碼</span><span class="sxs-lookup"><span data-stu-id="b1b86-157">Examples should be just enough code to demonstrate the usage</span></span>
- <span data-ttu-id="b1b86-158">PowerShell 語法</span><span class="sxs-lookup"><span data-stu-id="b1b86-158">PowerShell syntax</span></span>
  - <span data-ttu-id="b1b86-159">使用 Cmdlet 與參數的全名，請勿使用別名</span><span class="sxs-lookup"><span data-stu-id="b1b86-159">Use full names of cmdlets and parameters - no aliases</span></span>
  - <span data-ttu-id="b1b86-160">當命令列太長時，請針對參數使用展開</span><span class="sxs-lookup"><span data-stu-id="b1b86-160">Use splatting for parameters when the command line gets too long</span></span>
  - <span data-ttu-id="b1b86-161">避免使用行接續符號倒引號，僅在必要時使用</span><span class="sxs-lookup"><span data-stu-id="b1b86-161">Avoid using line continuation backticks - only use when necessary</span></span>
- <span data-ttu-id="b1b86-162">移除或簡化 PowerShell 提示字元 (`PS>`)，除非是範例所需</span><span class="sxs-lookup"><span data-stu-id="b1b86-162">Remove or simplify the PowerShell prompt (`PS>`) except where required for the example</span></span>
- <span data-ttu-id="b1b86-163">Cmdlet 參考範例必須遵循下列 PlatyPS 結構描述</span><span class="sxs-lookup"><span data-stu-id="b1b86-163">Cmdlet reference example must follow the following PlatyPS schema</span></span>

  ~~~Markdown
  ### Example 1 - Descriptive title

  Zero or more short descriptive paragraphs explaining the context of the example followed by one or
  more code blocks. Recommend at least one and no more than two.

  ```powershell
  ... one or more PowerShell code statements ...
  ```

  ```Output
  Example output of the code above.
  ```

  Zero or more optional follow up paragraphs that explain the details of the code and output.
  ~~~

- <span data-ttu-id="b1b86-164">勿將段落置於程式碼區塊之間。</span><span class="sxs-lookup"><span data-stu-id="b1b86-164">Do not put paragraphs between the code blocks.</span></span> <span data-ttu-id="b1b86-165">所有描述性內容都必須位於程式碼區塊之前或之後。</span><span class="sxs-lookup"><span data-stu-id="b1b86-165">All descriptive content must come before or after the code blocks.</span></span>

## <a name="linking-to-other-documents"></a><span data-ttu-id="b1b86-166">連結到其他文件</span><span class="sxs-lookup"><span data-stu-id="b1b86-166">Linking to other documents</span></span>

- <span data-ttu-id="b1b86-167">連結到 DocSet 之外，或是在 Cmdlet 參考與概念之間連結</span><span class="sxs-lookup"><span data-stu-id="b1b86-167">Linking outside the docset or between cmdlet reference and conceptual</span></span>
  - <span data-ttu-id="b1b86-168">在連結到 docs.microsoft.com 時，請使用相對 URL (移除 `https://docs.microsoft.com/en-us`)</span><span class="sxs-lookup"><span data-stu-id="b1b86-168">Use relative URLs when linking to docs.microsoft.com (remove `https://docs.microsoft.com/en-us`)</span></span>
  - <span data-ttu-id="b1b86-169">勿在 Microsoft 內容的 URL 中包含地區設定 (例如，</span><span class="sxs-lookup"><span data-stu-id="b1b86-169">Do not include locales in URLs on Microsoft properties (eg.</span></span> <span data-ttu-id="b1b86-170">從 URL 中移除 `/en-us`)</span><span class="sxs-lookup"><span data-stu-id="b1b86-170">remove `/en-us` from URL)</span></span>
  - <span data-ttu-id="b1b86-171">針對外部網站的所有 URL 都應該使用 HTTPS，除非目標網站不適用</span><span class="sxs-lookup"><span data-stu-id="b1b86-171">All URLs to external websites should use HTTPS unless that is not valid for the target site</span></span>
- <span data-ttu-id="b1b86-172">在 DocSet 之內</span><span class="sxs-lookup"><span data-stu-id="b1b86-172">Within docset</span></span>
  - <span data-ttu-id="b1b86-173">連結到檔案路徑 (例如 `../folder/file.md`)</span><span class="sxs-lookup"><span data-stu-id="b1b86-173">Link to file path (e.g. `../folder/file.md`)</span></span>
  - <span data-ttu-id="b1b86-174">所有檔案路徑都使用正斜線 (`/`) 字元</span><span class="sxs-lookup"><span data-stu-id="b1b86-174">All file paths use forward-slash (`/`) characters</span></span>
- <span data-ttu-id="b1b86-175">影像連結應該要有不重複的替代文字</span><span class="sxs-lookup"><span data-stu-id="b1b86-175">Image links should have unique alt text</span></span>
