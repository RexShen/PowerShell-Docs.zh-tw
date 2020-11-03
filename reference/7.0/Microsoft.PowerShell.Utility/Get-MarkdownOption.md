---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Module Name: Microsoft.PowerShell.Utility
online version: https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Get-MarkdownOption?view=powershell-7&WT.mc_id=ps-gethelp
ms.date: 01/30/2020
schema: 2.0.0
ms.openlocfilehash: f39add03a3b0250172cbb117a4233bb01958d9d3
ms.sourcegitcommit: b0488ca6557501184f20c8343b0ed5147b09e3fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "93205263"
---
# <span data-ttu-id="2d752-101">Get-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="2d752-101">Get-MarkdownOption</span></span>

## <span data-ttu-id="2d752-102">概要</span><span class="sxs-lookup"><span data-stu-id="2d752-102">SYNOPSIS</span></span>
<span data-ttu-id="2d752-103">傳回在主控台中用來呈現 Markdown 內容的目前色彩和樣式。</span><span class="sxs-lookup"><span data-stu-id="2d752-103">Returns the current colors and styles used for rendering Markdown content in the console.</span></span>

## <span data-ttu-id="2d752-104">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2d752-104">SYNTAX</span></span>

```
Get-MarkdownOption [<CommonParameters>]
```

## <span data-ttu-id="2d752-105">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="2d752-105">DESCRIPTION</span></span>

<span data-ttu-id="2d752-106">傳回在主控台中用來呈現 Markdown 內容的目前色彩和樣式。</span><span class="sxs-lookup"><span data-stu-id="2d752-106">Returns the current colors and styles used for rendering Markdown content in the console.</span></span> <span data-ttu-id="2d752-107">在此 Cmdlet 的輸出中顯示的字串包含用來變更所轉譯 Markdown 文字之色彩和樣式的 ANSI 轉義碼。</span><span class="sxs-lookup"><span data-stu-id="2d752-107">The strings displayed in the output of this cmdlet contain the ANSI escape codes used to change the color and style of the Markdown text being rendered.</span></span>

<span data-ttu-id="2d752-108">如需 Markdown 的詳細資訊，請參閱 [CommonMark](https://commonmark.org/) 網站。</span><span class="sxs-lookup"><span data-stu-id="2d752-108">For more information about Markdown, see the [CommonMark](https://commonmark.org/) website.</span></span>

## <span data-ttu-id="2d752-109">範例</span><span class="sxs-lookup"><span data-stu-id="2d752-109">EXAMPLES</span></span>

### <span data-ttu-id="2d752-110">範例 1-取得目前的色彩和樣式</span><span class="sxs-lookup"><span data-stu-id="2d752-110">Example 1 - Get the current colors and style</span></span>

```powershell
Get-MarkdownOption
```

```Output
Header1         : [7m
Header2         : [4;93m
Header3         : [4;94m
Header4         : [4;95m
Header5         : [4;96m
Header6         : [4;97m
Code            : [48;2;155;155;155;38;2;30;30;30m
Link            : [4;38;5;117m
Image           : [33m
EmphasisBold    : [1m
EmphasisItalics : [36m
```

> [!NOTE]
> <span data-ttu-id="2d752-111">輸出中所顯示的字串值為 ANSI escape 序列 () **之後的** 字元 `[char]0x1B` 。</span><span class="sxs-lookup"><span data-stu-id="2d752-111">The string values shown in the output are the characters that follow the **Escape** character (`[char]0x1B`) for the ANSI escape sequence.</span></span> <span data-ttu-id="2d752-112">如需 ANSI escape 程式碼工作的詳細資訊，請參閱 [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code)。</span><span class="sxs-lookup"><span data-stu-id="2d752-112">For more information about ANSI escape codes work, see [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span></span>

## <span data-ttu-id="2d752-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2d752-113">PARAMETERS</span></span>

### <span data-ttu-id="2d752-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2d752-114">CommonParameters</span></span>

<span data-ttu-id="2d752-115">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="2d752-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2d752-116">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="2d752-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2d752-117">輸入</span><span class="sxs-lookup"><span data-stu-id="2d752-117">INPUTS</span></span>

### <span data-ttu-id="2d752-118">無</span><span class="sxs-lookup"><span data-stu-id="2d752-118">None</span></span>

## <span data-ttu-id="2d752-119">輸出</span><span class="sxs-lookup"><span data-stu-id="2d752-119">OUTPUTS</span></span>

### <span data-ttu-id="2d752-120">MarkdownRender. PSMarkdownOptionInfo</span><span class="sxs-lookup"><span data-stu-id="2d752-120">Microsoft.PowerShell.MarkdownRender.PSMarkdownOptionInfo</span></span>

## <span data-ttu-id="2d752-121">注意</span><span class="sxs-lookup"><span data-stu-id="2d752-121">NOTES</span></span>

## <span data-ttu-id="2d752-122">相關連結</span><span class="sxs-lookup"><span data-stu-id="2d752-122">RELATED LINKS</span></span>

[<span data-ttu-id="2d752-123">Set-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="2d752-123">Set-MarkdownOption</span></span>](Set-MarkdownOption.md)

[<span data-ttu-id="2d752-124">ConvertFrom-Markdown</span><span class="sxs-lookup"><span data-stu-id="2d752-124">ConvertFrom-Markdown</span></span>](ConvertFrom-Markdown.md)

[<span data-ttu-id="2d752-125">Show-Markdown</span><span class="sxs-lookup"><span data-stu-id="2d752-125">Show-Markdown</span></span>](Show-Markdown.md)

[<span data-ttu-id="2d752-126">ANSI_escape_code</span><span class="sxs-lookup"><span data-stu-id="2d752-126">ANSI_escape_code</span></span>](https://en.wikipedia.org/wiki/ANSI_escape_code)

[<span data-ttu-id="2d752-127">CommonMark</span><span class="sxs-lookup"><span data-stu-id="2d752-127">CommonMark</span></span>](https://commonmark.org/)
