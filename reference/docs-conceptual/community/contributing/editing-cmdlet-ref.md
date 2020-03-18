---
title: 編輯參考文章
description: 此文章說明編輯 PowerShell 文件中的 Cmdlet 參考與「關於」主題的特定需求。
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 3c6f1b4fc27ca8ece7ec30317daf4ed2a6bc9228
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/10/2020
ms.locfileid: "79060323"
---
# <a name="editing-reference-articles"></a><span data-ttu-id="f72df-103">編輯參考文章</span><span class="sxs-lookup"><span data-stu-id="f72df-103">Editing reference articles</span></span>

<span data-ttu-id="f72df-104">Cmdlet 參考文章具有特定的結構。</span><span class="sxs-lookup"><span data-stu-id="f72df-104">Cmdlet reference articles have a specific structure.</span></span> <span data-ttu-id="f72df-105">此結構是由 [PlatyPS][] 所定義。</span><span class="sxs-lookup"><span data-stu-id="f72df-105">This structure is defined by [PlatyPS][].</span></span>
<span data-ttu-id="f72df-106">PlatyPS 會以 Markdown 產生 PowerShell 模組的 Cmdlet 說明。</span><span class="sxs-lookup"><span data-stu-id="f72df-106">PlatyPS generates the cmdlet help for PowerShell modules in Markdown.</span></span> <span data-ttu-id="f72df-107">在編輯 Markdown 檔案之後，會使用 PlatyPS 來建立 `Get-Help` Cmdlet 所使用的 MAML 說明檔案。</span><span class="sxs-lookup"><span data-stu-id="f72df-107">After editing the Markdown files, PlatyPS is used create the MAML help files used by the `Get-Help` cmdlet.</span></span>

<span data-ttu-id="f72df-108">PlatyPS 為會寫入程式碼中，適用於 Cmdlet 參考的硬式編碼結構描述。</span><span class="sxs-lookup"><span data-stu-id="f72df-108">PlatyPS has a hard-coded schema for cmdlet reference that is written into the code.</span></span> <span data-ttu-id="f72df-109">[platyPS.schema.md][] 文件會嘗試描述此結構。</span><span class="sxs-lookup"><span data-stu-id="f72df-109">The [platyPS.schema.md][] document attempts to describe this structure.</span></span> <span data-ttu-id="f72df-110">結構描述違規會導致建置錯誤；您必須先將其修正，我們才能接受您的貢獻。</span><span class="sxs-lookup"><span data-stu-id="f72df-110">Schema violations cause build errors that must be fixed before we can accept your contribution.</span></span>

## <a name="general-guidelines"></a><span data-ttu-id="f72df-111">一般方針</span><span class="sxs-lookup"><span data-stu-id="f72df-111">General guidelines</span></span>

- <span data-ttu-id="f72df-112">勿移除任何標頭結構。</span><span class="sxs-lookup"><span data-stu-id="f72df-112">Do not remove any of the header structures.</span></span> <span data-ttu-id="f72df-113">PlatyPS 會預期特定的標頭集合。</span><span class="sxs-lookup"><span data-stu-id="f72df-113">PlatyPS expects a specific set of headers.</span></span>
- <span data-ttu-id="f72df-114">[Input type]  \(輸入類型\) 與 [Output type]  \(輸出類型\) 標頭必須具有類型。</span><span class="sxs-lookup"><span data-stu-id="f72df-114">The **Input type** and **Output type** headers must have a type.</span></span> <span data-ttu-id="f72df-115">如果 Cmdlet 不接受輸入或是傳回值，請使用 `None` 值。</span><span class="sxs-lookup"><span data-stu-id="f72df-115">If the cmdlet does not take input or return a value then use the value `None`.</span></span>
- <span data-ttu-id="f72df-116">僅於 [Examples](#structuring-examples) 小節允許使用具柵欄的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="f72df-116">Fenced code blocks are only allowed in the [Examples](#structuring-examples) section.</span></span>
- <span data-ttu-id="f72df-117">內嵌程式碼範圍可用於任何段落。</span><span class="sxs-lookup"><span data-stu-id="f72df-117">Inline code spans can be used in any paragraph.</span></span>

## <a name="formatting-about_-files"></a><span data-ttu-id="f72df-118">設定 About_ 檔案格式</span><span class="sxs-lookup"><span data-stu-id="f72df-118">Formatting About_ files</span></span>

<span data-ttu-id="f72df-119">`About_*` 檔案現已由 [Pandoc][] 處理，而非 PlatyPS。</span><span class="sxs-lookup"><span data-stu-id="f72df-119">`About_*` files are now processed by [Pandoc][], instead of PlatyPS.</span></span> <span data-ttu-id="f72df-120">`About_*` 檔案的格式設定方式，會使其能在 PowerShell 的所有版本與發行工具上取得最佳相容性。</span><span class="sxs-lookup"><span data-stu-id="f72df-120">`About_*` files are formatted for the best compatibility across all versions of PowerShell and with the publishing tools.</span></span>

<span data-ttu-id="f72df-121">基本格式設定指導方針：</span><span class="sxs-lookup"><span data-stu-id="f72df-121">Basic formatting guidelines:</span></span>

- <span data-ttu-id="f72df-122">將行限制為 80 個字元</span><span class="sxs-lookup"><span data-stu-id="f72df-122">Limit lines to 80 characters</span></span>
- <span data-ttu-id="f72df-123">程式碼區塊與表格會限制為 76 個字元，因為 Pandoc 會在轉換為純文字時，對其進行四個空格的縮排</span><span class="sxs-lookup"><span data-stu-id="f72df-123">Code blocks and tables are limited to 76 characters because Pandoc indents these by four spaces during conversion to plain text</span></span>
- <span data-ttu-id="f72df-124">表格必須能容納在 76 個字元之內</span><span class="sxs-lookup"><span data-stu-id="f72df-124">Tables need to fit within 76 characters</span></span>
  - <span data-ttu-id="f72df-125">手動將資料格的內容跨多行進行換行</span><span class="sxs-lookup"><span data-stu-id="f72df-125">Manually wrap contents of cells across multiple lines</span></span>
  - <span data-ttu-id="f72df-126">在每一行的開頭和結尾使用 `|` 字元</span><span class="sxs-lookup"><span data-stu-id="f72df-126">Use opening and closing `|` characters on each line</span></span>
  - <span data-ttu-id="f72df-127">在 [about_Comparison_Operators][about-example] 中查看實用範例</span><span class="sxs-lookup"><span data-stu-id="f72df-127">See a working example in [about_Comparison_Operators][about-example]</span></span>
- <span data-ttu-id="f72df-128">使用 Pandoc 特殊字元 `\`、`$` 與 `<`</span><span class="sxs-lookup"><span data-stu-id="f72df-128">Using Pandoc special characters `\`,`$`, and `<`</span></span>
  - <span data-ttu-id="f72df-129">在標頭內，這些字元必須透過使用前置 `\` 字元，或是以倒引號 (`` ` ``) 括住來逸出</span><span class="sxs-lookup"><span data-stu-id="f72df-129">Within a header - these characters must be escaped using a leading `\` character or enclosed in backticks (`` ` ``)</span></span>
  - <span data-ttu-id="f72df-130">在段落內，這些字元應該要置於程式碼範圍中。</span><span class="sxs-lookup"><span data-stu-id="f72df-130">Within a paragraph, these characters should be put into code spans.</span></span> <span data-ttu-id="f72df-131">例如：</span><span class="sxs-lookup"><span data-stu-id="f72df-131">For example:</span></span>

    ~~~markdown
    ### The purpose of the \$foo variable

    The `$foo` variable is used to store ...
    ~~~

## <a name="structuring-examples"></a><span data-ttu-id="f72df-132">結構範例</span><span class="sxs-lookup"><span data-stu-id="f72df-132">Structuring examples</span></span>

<span data-ttu-id="f72df-133">在 PlatyPS 結構描述中，**EXAMPLES** 標頭為 H2 標頭，且每個範例都是 H3 標頭。</span><span class="sxs-lookup"><span data-stu-id="f72df-133">In the PlatyPS schema, the **EXAMPLES** header is an H2 header and each example is an H3 header.</span></span>

<span data-ttu-id="f72df-134">在範例內，結構描述不允許使用段落來區分程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="f72df-134">Within an example, the schema does not allow code blocks to be separated by paragraphs.</span></span> <span data-ttu-id="f72df-135">支援的結構描述為：</span><span class="sxs-lookup"><span data-stu-id="f72df-135">The supported schema is:</span></span>

```
### Example #X title

0 or more paragraphs
1 or more code blocks
0 or more paragraphs.
```

<span data-ttu-id="f72df-136">為每個範例加上編號，然後加入簡短的標題。</span><span class="sxs-lookup"><span data-stu-id="f72df-136">Number each example and add a brief title.</span></span>

<span data-ttu-id="f72df-137">例如：</span><span class="sxs-lookup"><span data-stu-id="f72df-137">For example:</span></span>

### <a name="example-1-get-cmdlets-functions-and-aliases"></a><span data-ttu-id="f72df-138">範例 1：取得 Cmdlet、函式與別名</span><span class="sxs-lookup"><span data-stu-id="f72df-138">Example 1: Get cmdlets, functions, and aliases</span></span>

<span data-ttu-id="f72df-139">此命令會取得電腦上安裝的 PowerShell Cmdlet、函式與別名。</span><span class="sxs-lookup"><span data-stu-id="f72df-139">This command gets the PowerShell cmdlets, functions, and aliases that are installed on the computer.</span></span>

```powershell
Get-Command
```

### <a name="example-2-get-commands-in-the-current-session"></a><span data-ttu-id="f72df-140">範例 2：取得目前工作階段中的命令</span><span class="sxs-lookup"><span data-stu-id="f72df-140">Example 2: Get commands in the current session</span></span>

```powershell
Get-Command -ListImported
```

## <a name="next-steps"></a><span data-ttu-id="f72df-141">後續步驟</span><span class="sxs-lookup"><span data-stu-id="f72df-141">Next steps</span></span>

[<span data-ttu-id="f72df-142">編輯檢查清單</span><span class="sxs-lookup"><span data-stu-id="f72df-142">Editorial checklist</span></span>](editorial-checklist.md)

<!-- link references -->
[PlatyPS]: https://github.com/powershell/platyps \(英文\)
[platyPS.schema.md]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md \(英文\)
[issue1806]: https://github.com/MicrosoftDocs/PowerShell-Docs/issues/1806
[about-example]: https://github.com/MicrosoftDocs/PowerShell-Docs/reference/5.1/Microsoft.PowerShell.Core/About/about_Comparison_Operators.md
[Pandoc]: https://pandoc.org \(英文\)
