---
ms.date: 09/12/2016
ms.topic: reference
title: 註解型說明的語法
description: 註解型說明的語法
ms.openlocfilehash: 3866f25b40fc970e8d219af6f423b7a25f5b875c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659507"
---
# <a name="syntax-of-comment-based-help"></a><span data-ttu-id="f6b7d-103">註解型說明的語法</span><span class="sxs-lookup"><span data-stu-id="f6b7d-103">Syntax of Comment-Based Help</span></span>

<span data-ttu-id="f6b7d-104">本節說明以批註為基礎的說明語法。</span><span class="sxs-lookup"><span data-stu-id="f6b7d-104">This section describes the syntax of comment-based help.</span></span>

## <a name="syntax-diagram"></a><span data-ttu-id="f6b7d-105">語法圖表</span><span class="sxs-lookup"><span data-stu-id="f6b7d-105">Syntax Diagram</span></span>

 <span data-ttu-id="f6b7d-106">以批註為基礎的說明語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="f6b7d-106">The syntax for comment-based Help is as follows:</span></span>

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a><span data-ttu-id="f6b7d-107">語法描述</span><span class="sxs-lookup"><span data-stu-id="f6b7d-107">Syntax Description</span></span>

 <span data-ttu-id="f6b7d-108">以批註為基礎的說明會以一系列的批註撰寫。</span><span class="sxs-lookup"><span data-stu-id="f6b7d-108">Comment-based Help is written as a series of comments.</span></span> <span data-ttu-id="f6b7d-109">您可以在 `#` 每一行批註之前輸入批註符號 () ，也可以使用 `<#` 和 `#>` 符號來建立批註區塊。</span><span class="sxs-lookup"><span data-stu-id="f6b7d-109">You can type a comment symbol (`#`) before each line of comments, or you can use the `<#` and `#>` symbols to create a comment block.</span></span> <span data-ttu-id="f6b7d-110">批註區塊內的所有行都會轉譯為批註。</span><span class="sxs-lookup"><span data-stu-id="f6b7d-110">All the lines within the comment block are interpreted as comments.</span></span>

 <span data-ttu-id="f6b7d-111">批註型說明的每個區段都是由關鍵字定義，而每個關鍵字的前面會加上點 (`.`) 。</span><span class="sxs-lookup"><span data-stu-id="f6b7d-111">Each section of comment-based Help is defined by a keyword and each keyword is preceded by a dot (`.`).</span></span> <span data-ttu-id="f6b7d-112">關鍵字可以依任何順序出現。</span><span class="sxs-lookup"><span data-stu-id="f6b7d-112">The keywords can appear in any order.</span></span> <span data-ttu-id="f6b7d-113">關鍵字名稱不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="f6b7d-113">The keyword names are not case-sensitive.</span></span>

 <span data-ttu-id="f6b7d-114">批註區塊必須至少包含一個 help 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="f6b7d-114">A comment block must contain at least one help keyword.</span></span> <span data-ttu-id="f6b7d-115">某些關鍵字（例如 **EXAMPLE**）可以出現在相同批註區塊中的多次。</span><span class="sxs-lookup"><span data-stu-id="f6b7d-115">Some of the keywords, such as **EXAMPLE**, can appear many times in the same comment block.</span></span> <span data-ttu-id="f6b7d-116">每個關鍵字的說明內容都是在關鍵字後面的那一行開始，而且可以橫跨多行。</span><span class="sxs-lookup"><span data-stu-id="f6b7d-116">The Help content for each keyword begins on the line after the keyword and can span multiple lines.</span></span>

 <span data-ttu-id="f6b7d-117">以批註為基礎的說明主題中的所有程式列都必須是連續的。</span><span class="sxs-lookup"><span data-stu-id="f6b7d-117">All of the lines in a comment-based Help topic must be contiguous.</span></span> <span data-ttu-id="f6b7d-118">如果以批註為基礎的說明主題遵循的批註不在說明主題中，則最後一個非說明批註行和批註式說明的開頭至少必須有一個空白行。</span><span class="sxs-lookup"><span data-stu-id="f6b7d-118">If a comment-based Help topic follows a comment that is not part of the Help topic, there must be at least one blank line between the last non-Help comment line and the beginning of the comment-based Help.</span></span>

 <span data-ttu-id="f6b7d-119">例如，下列以批註為基礎的說明主題包含。Description 關鍵字及其值，也就是函數或腳本的描述。</span><span class="sxs-lookup"><span data-stu-id="f6b7d-119">For example, the following comment-based help topic contains the .Description keyword and its value, which is a description of a function or script.</span></span>

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```
