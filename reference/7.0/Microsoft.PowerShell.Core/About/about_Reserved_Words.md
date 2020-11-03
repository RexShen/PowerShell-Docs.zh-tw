---
description: 列出無法當做識別碼使用的保留字，因為它們在 PowerShell 中有特殊意義。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_reserved_words?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Reserved_Words
ms.openlocfilehash: c4b67a523a40319635d159791b80ab302b9aa3b4
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208152"
---
# <a name="about-reserved-words"></a><span data-ttu-id="bbeb6-104">關於保留字</span><span class="sxs-lookup"><span data-stu-id="bbeb6-104">About Reserved Words</span></span>

## <a name="short-description"></a><span data-ttu-id="bbeb6-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="bbeb6-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="bbeb6-106">列出無法當做識別碼使用的保留字，因為它們在 PowerShell 中有特殊意義。</span><span class="sxs-lookup"><span data-stu-id="bbeb6-106">Lists the reserved words that cannot be used as identifiers because they have a special meaning in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="bbeb6-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="bbeb6-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="bbeb6-108">有些單字在 PowerShell 中有特殊意義。</span><span class="sxs-lookup"><span data-stu-id="bbeb6-108">There are certain words that have special meaning in PowerShell.</span></span> <span data-ttu-id="bbeb6-109">當這些單字出現時沒有引號時，PowerShell 會嘗試套用其特殊意義，而不是將它們視為字元字串。</span><span class="sxs-lookup"><span data-stu-id="bbeb6-109">When these words appear without quotation marks, PowerShell attempts to apply their special meaning rather than treating them as character strings.</span></span> <span data-ttu-id="bbeb6-110">若要在命令或腳本中使用這些單字作為參數引數，而不叫用其特殊意義，請以引號括住保留字。</span><span class="sxs-lookup"><span data-stu-id="bbeb6-110">To use these words as parameter arguments in a command or script without invoking their special meaning, enclose the reserved words in quotation marks.</span></span>

<span data-ttu-id="bbeb6-111">以下是 PowerShell 中的保留字：</span><span class="sxs-lookup"><span data-stu-id="bbeb6-111">The following are the reserved words in PowerShell:</span></span>

```
assembly         exit            process
base             filter          public
begin            finally         return
break            for             sequence
catch            foreach         static
class            from (*)        switch
command          function        throw
configuration    hidden          trap
continue         if              try
data             in              type
define (*)       inlinescript    until
do               interface       using
dynamicparam     module          var (*)
else             namespace       while
elseif           parallel        workflow
end              param
enum             private

(*) These keywords are reserved for future use.
```

<span data-ttu-id="bbeb6-112">許多語言關鍵字（包括 `Foreach` 、 `If` 、 `For` 和 `While` ）都有自己的說明文章。</span><span class="sxs-lookup"><span data-stu-id="bbeb6-112">Several language keywords, including `Foreach`, `If`, `For`, and `While`, have their own help articles.</span></span> <span data-ttu-id="bbeb6-113">若要查看它們，請輸入 `Get-Help about_` 並加入關鍵字。</span><span class="sxs-lookup"><span data-stu-id="bbeb6-113">To view them, type `Get-Help about_` and add the keyword.</span></span> <span data-ttu-id="bbeb6-114">例如，若要取得語句的相關資訊 `Foreach` ，請輸入：</span><span class="sxs-lookup"><span data-stu-id="bbeb6-114">For example, to get information about the `Foreach` statement, type:</span></span>

```powershell
Get-Help about_ForEach
```

<span data-ttu-id="bbeb6-115">如需 `Filter` 語句或語句語法的詳細資訊 `Return` ，請輸入：</span><span class="sxs-lookup"><span data-stu-id="bbeb6-115">For information about the `Filter` statement or the `Return` statement syntax, type:</span></span>

```powershell
Get-Help about_Functions
```

<span data-ttu-id="bbeb6-116">如需其他保留字的詳細資訊，請輸入：</span><span class="sxs-lookup"><span data-stu-id="bbeb6-116">For information about other reserved words, type:</span></span>

```powershell
Get-Help <Reserved_Word>
```

> [!NOTE]
> <span data-ttu-id="bbeb6-117">並非每個保留字都有自己的說明文章。</span><span class="sxs-lookup"><span data-stu-id="bbeb6-117">Not every reserved word has its own help article.</span></span> <span data-ttu-id="bbeb6-118">如果 `Get-Help` 未傳回文章，您可以使用下列命令來搜尋與保留字相關的文章：</span><span class="sxs-lookup"><span data-stu-id="bbeb6-118">If `Get-Help` does not return an article, you can search for articles that talk about the reserved word using the following command:</span></span>
>
> ```powershell
> Get-Help <Reserved_Word> -Category:HelpFile
> ```

## <a name="see-also"></a><span data-ttu-id="bbeb6-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bbeb6-119">SEE ALSO</span></span>

- [<span data-ttu-id="bbeb6-120">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="bbeb6-120">about_Command_Syntax</span></span>](about_Command_Syntax.md)
- [<span data-ttu-id="bbeb6-121">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="bbeb6-121">about_Language_Keywords</span></span>](about_Language_Keywords.md)
- [<span data-ttu-id="bbeb6-122">about_Parsing</span><span class="sxs-lookup"><span data-stu-id="bbeb6-122">about_Parsing</span></span>](about_Parsing.md)
- [<span data-ttu-id="bbeb6-123">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="bbeb6-123">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)
- [<span data-ttu-id="bbeb6-124">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="bbeb6-124">about_Script_Blocks</span></span>](about_Script_Blocks.md)
- [<span data-ttu-id="bbeb6-125">about_Special_Characters</span><span class="sxs-lookup"><span data-stu-id="bbeb6-125">about_Special_Characters</span></span>](about_Special_Characters.md)
