---
title: 編輯參考文章
description: 此文章說明編輯 PowerShell 文件中的 Cmdlet 參考與「關於」主題的特定需求。
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: e135f6cc81ba7537a535a08421e1ca9b2b2af573
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81624766"
---
# <a name="editing-reference-articles"></a><span data-ttu-id="d0be0-103">編輯參考文章</span><span class="sxs-lookup"><span data-stu-id="d0be0-103">Editing reference articles</span></span>

<span data-ttu-id="d0be0-104">Cmdlet 參考文章具有特定的結構。</span><span class="sxs-lookup"><span data-stu-id="d0be0-104">Cmdlet reference articles have a specific structure.</span></span> <span data-ttu-id="d0be0-105">此結構是由 [PlatyPS][] 所定義。</span><span class="sxs-lookup"><span data-stu-id="d0be0-105">This structure is defined by [PlatyPS][].</span></span>
<span data-ttu-id="d0be0-106">PlatyPS 會以 Markdown 產生 PowerShell 模組的 Cmdlet 說明。</span><span class="sxs-lookup"><span data-stu-id="d0be0-106">PlatyPS generates the cmdlet help for PowerShell modules in Markdown.</span></span> <span data-ttu-id="d0be0-107">在編輯 Markdown 檔案之後，會使用 PlatyPS 來建立 `Get-Help` Cmdlet 所使用的 MAML 說明檔案。</span><span class="sxs-lookup"><span data-stu-id="d0be0-107">After editing the Markdown files, PlatyPS is used create the MAML help files used by the `Get-Help` cmdlet.</span></span>

<span data-ttu-id="d0be0-108">PlatyPS 為會寫入程式碼中，適用於 Cmdlet 參考的硬式編碼結構描述。</span><span class="sxs-lookup"><span data-stu-id="d0be0-108">PlatyPS has a hard-coded schema for cmdlet reference that is written into the code.</span></span> <span data-ttu-id="d0be0-109">[platyPS.schema.md][] 文件會嘗試描述此結構。</span><span class="sxs-lookup"><span data-stu-id="d0be0-109">The [platyPS.schema.md][] document attempts to describe this structure.</span></span> <span data-ttu-id="d0be0-110">結構描述違規會導致建置錯誤；您必須先將其修正，我們才能接受您的貢獻。</span><span class="sxs-lookup"><span data-stu-id="d0be0-110">Schema violations cause build errors that must be fixed before we can accept your contribution.</span></span>

## <a name="general-guidelines"></a><span data-ttu-id="d0be0-111">一般方針</span><span class="sxs-lookup"><span data-stu-id="d0be0-111">General guidelines</span></span>

- <span data-ttu-id="d0be0-112">勿移除任何標頭結構。</span><span class="sxs-lookup"><span data-stu-id="d0be0-112">Do not remove any of the header structures.</span></span> <span data-ttu-id="d0be0-113">PlatyPS 會預期特定的標頭集合。</span><span class="sxs-lookup"><span data-stu-id="d0be0-113">PlatyPS expects a specific set of headers.</span></span>
- <span data-ttu-id="d0be0-114">[Input type]  \(輸入類型\) 與 [Output type]  \(輸出類型\) 標頭必須具有類型。</span><span class="sxs-lookup"><span data-stu-id="d0be0-114">The **Input type** and **Output type** headers must have a type.</span></span> <span data-ttu-id="d0be0-115">如果 Cmdlet 不接受輸入或是傳回值，請使用 `None` 值。</span><span class="sxs-lookup"><span data-stu-id="d0be0-115">If the cmdlet does not take input or return a value then use the value `None`.</span></span>
- <span data-ttu-id="d0be0-116">僅於 [Examples](#structuring-examples) 小節允許使用具柵欄的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="d0be0-116">Fenced code blocks are only allowed in the [Examples](#structuring-examples) section.</span></span>
- <span data-ttu-id="d0be0-117">內嵌程式碼範圍可用於任何段落。</span><span class="sxs-lookup"><span data-stu-id="d0be0-117">Inline code spans can be used in any paragraph.</span></span>

## <a name="formatting-about_-files"></a><span data-ttu-id="d0be0-118">設定 About_ 檔案格式</span><span class="sxs-lookup"><span data-stu-id="d0be0-118">Formatting About_ files</span></span>

<span data-ttu-id="d0be0-119">`About_*` 檔案是以 Markdown 撰寫，但以純文字檔案格式送交。</span><span class="sxs-lookup"><span data-stu-id="d0be0-119">`About_*` files are written in Markdown but are shipped as plain text files.</span></span> <span data-ttu-id="d0be0-120">我們使用 [Pandoc][] 將 Markdown 轉換為純文字。</span><span class="sxs-lookup"><span data-stu-id="d0be0-120">We use [Pandoc][] to convert the Markdown to plain text.</span></span> <span data-ttu-id="d0be0-121">`About_*` 檔案的格式設定方式，會使其能在 PowerShell 的所有版本與發行工具上取得最佳相容性。</span><span class="sxs-lookup"><span data-stu-id="d0be0-121">`About_*` files are formatted for the best compatibility across all versions of PowerShell and with the publishing tools.</span></span>

<span data-ttu-id="d0be0-122">基本格式設定指導方針：</span><span class="sxs-lookup"><span data-stu-id="d0be0-122">Basic formatting guidelines:</span></span>

- <span data-ttu-id="d0be0-123">將行限制為 80 個字元。</span><span class="sxs-lookup"><span data-stu-id="d0be0-123">Limit lines to 80 characters.</span></span> <span data-ttu-id="d0be0-124">Pandoc 會縮排某些 Markdown 區塊，因此必須調整那些區塊。</span><span class="sxs-lookup"><span data-stu-id="d0be0-124">Pandoc indents some Markdown blocks so those block must be adjusted.</span></span>
  - <span data-ttu-id="d0be0-125">程式碼區塊限制為 76 個字元</span><span class="sxs-lookup"><span data-stu-id="d0be0-125">Code blocks are limited to 76 characters</span></span>
  - <span data-ttu-id="d0be0-126">表格限制為 76 個字元</span><span class="sxs-lookup"><span data-stu-id="d0be0-126">Tables are limited 76 characters</span></span>
  - <span data-ttu-id="d0be0-127">區塊引述 (與警示) 限制為 78 個字元</span><span class="sxs-lookup"><span data-stu-id="d0be0-127">Blockquotes (and Alerts) are limited 78 characters</span></span>

- <span data-ttu-id="d0be0-128">使用 Pandoc 的特殊中繼字元 `\`、`$` 與 `<`</span><span class="sxs-lookup"><span data-stu-id="d0be0-128">Using Pandoc's special meta-characters `\`,`$`, and `<`</span></span>
  - <span data-ttu-id="d0be0-129">在標題內，這些字元必須透過使用前置 `\` 字元，或是使用倒引號 (`` ` ``) 來以程式碼範圍括住</span><span class="sxs-lookup"><span data-stu-id="d0be0-129">Within a header - these characters must be escaped using a leading `\` character or enclosed in code spans using backticks (`` ` ``)</span></span>
  - <span data-ttu-id="d0be0-130">在段落內，這些字元應該要置於程式碼範圍中。</span><span class="sxs-lookup"><span data-stu-id="d0be0-130">Within a paragraph, these characters should be put into code spans.</span></span> <span data-ttu-id="d0be0-131">例如：</span><span class="sxs-lookup"><span data-stu-id="d0be0-131">For example:</span></span>

    ~~~markdown
    ### The purpose of the \$foo variable

    The `$foo` variable is used to store ...
    ~~~

- <span data-ttu-id="d0be0-132">表格必須能容納在 76 個字元之內</span><span class="sxs-lookup"><span data-stu-id="d0be0-132">Tables need to fit within 76 characters</span></span>
  - <span data-ttu-id="d0be0-133">手動將資料格的內容跨多行進行換行</span><span class="sxs-lookup"><span data-stu-id="d0be0-133">Manually wrap contents of cells across multiple lines</span></span>
  - <span data-ttu-id="d0be0-134">在每一行的開頭和結尾使用 `|` 字元</span><span class="sxs-lookup"><span data-stu-id="d0be0-134">Use opening and closing `|` characters on each line</span></span>
  - <span data-ttu-id="d0be0-135">下列範例說明如何正確地建立一個表格，其中包含包裝在資料格內多行的資訊。</span><span class="sxs-lookup"><span data-stu-id="d0be0-135">The following example illustrates how to properly construct a table that contains information that wraps on multiple lines within a cell.</span></span>

    ~~~markdown
    ```
    |Operator|Description                |Example                          |
    |--------|---------------------------|---------------------------------|
    |`-is`   |Returns TRUE when the input|`(get-date) -is [DateTime]`      |
    |        |is an instance of the      |`True`                           |
    |        |specified .NET type.       |                                 |
    |`-isNot`|Returns TRUE when the input|`(get-date) -isNot [DateTime]`   |
    |        |not an instance of the     |`False`                          |
    |        |specified.NET type.        |                                 |
    |`-as`   |Converts the input to the  |`"5/7/07" -as [DateTime]`        |
    |        |specified .NET type.       |`Monday, May 7, 2007 12:00:00 AM`|
    ```
    ~~~

    > [!NOTE]
    > <span data-ttu-id="d0be0-136">76 欄限制僅適用於 `About_*` 主題。</span><span class="sxs-lookup"><span data-stu-id="d0be0-136">The 76-column limitation applies only to `About_*` topics.</span></span> <span data-ttu-id="d0be0-137">您可以在概念或 Cmdlet 參考文章中使用寬欄。</span><span class="sxs-lookup"><span data-stu-id="d0be0-137">You can use wide columns in conceptual or cmdlet reference articles.</span></span>

## <a name="structuring-examples"></a><span data-ttu-id="d0be0-138">結構範例</span><span class="sxs-lookup"><span data-stu-id="d0be0-138">Structuring examples</span></span>

<span data-ttu-id="d0be0-139">在 PlatyPS 結構描述中，**EXAMPLES** 標頭為 H2 標頭，且每個範例都是 H3 標頭。</span><span class="sxs-lookup"><span data-stu-id="d0be0-139">In the PlatyPS schema, the **EXAMPLES** header is an H2 header and each example is an H3 header.</span></span>

<span data-ttu-id="d0be0-140">在範例內，結構描述不允許使用段落來區分程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="d0be0-140">Within an example, the schema does not allow code blocks to be separated by paragraphs.</span></span> <span data-ttu-id="d0be0-141">支援的結構描述為：</span><span class="sxs-lookup"><span data-stu-id="d0be0-141">The supported schema is:</span></span>

```
### Example #X title

0 or more paragraphs
1 or more code blocks
0 or more paragraphs.
```

<span data-ttu-id="d0be0-142">為每個範例加上編號，然後加入簡短的標題。</span><span class="sxs-lookup"><span data-stu-id="d0be0-142">Number each example and add a brief title.</span></span>

<span data-ttu-id="d0be0-143">例如：</span><span class="sxs-lookup"><span data-stu-id="d0be0-143">For example:</span></span>

### <a name="example-1-get-cmdlets-functions-and-aliases"></a><span data-ttu-id="d0be0-144">範例 1：取得 Cmdlet、函式與別名</span><span class="sxs-lookup"><span data-stu-id="d0be0-144">Example 1: Get cmdlets, functions, and aliases</span></span>

<span data-ttu-id="d0be0-145">此命令會取得電腦上安裝的 PowerShell Cmdlet、函式與別名。</span><span class="sxs-lookup"><span data-stu-id="d0be0-145">This command gets the PowerShell cmdlets, functions, and aliases that are installed on the computer.</span></span>

```powershell
Get-Command
```

### <a name="example-2-get-commands-in-the-current-session"></a><span data-ttu-id="d0be0-146">範例 2：取得目前工作階段中的命令</span><span class="sxs-lookup"><span data-stu-id="d0be0-146">Example 2: Get commands in the current session</span></span>

```powershell
Get-Command -ListImported
```

## <a name="next-steps"></a><span data-ttu-id="d0be0-147">後續步驟</span><span class="sxs-lookup"><span data-stu-id="d0be0-147">Next steps</span></span>

[<span data-ttu-id="d0be0-148">編輯檢查清單</span><span class="sxs-lookup"><span data-stu-id="d0be0-148">Editorial checklist</span></span>](editorial-checklist.md)

<!-- link references -->
[PlatyPS]: https://github.com/powershell/platyps
[platyPS.schema.md]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[issue1806]: https://github.com/MicrosoftDocs/PowerShell-Docs/issues/1806
[about-example]: /PowerShell/module/Microsoft.PowerShell.Core/About/about_Comparison_Operators
[Pandoc]: https://pandoc.org
