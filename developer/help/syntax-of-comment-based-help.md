---
title: 語法的註解型說明 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: 584e5923008e8369a83c699478844f0e0c295adc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855544"
---
# <a name="syntax-of-comment-based-help"></a><span data-ttu-id="0c6f5-102">註解型說明的語法</span><span class="sxs-lookup"><span data-stu-id="0c6f5-102">Syntax of Comment-Based Help</span></span>

<span data-ttu-id="0c6f5-103">本章節描述註解型說明的語法。</span><span class="sxs-lookup"><span data-stu-id="0c6f5-103">This section describes the syntax of comment-based help.</span></span>

## <a name="syntax-diagram"></a><span data-ttu-id="0c6f5-104">語法圖</span><span class="sxs-lookup"><span data-stu-id="0c6f5-104">Syntax Diagram</span></span>

 <span data-ttu-id="0c6f5-105">註解型說明的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="0c6f5-105">The syntax for comment-based Help is as follows:</span></span>

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a><span data-ttu-id="0c6f5-106">語法描述</span><span class="sxs-lookup"><span data-stu-id="0c6f5-106">Syntax Description</span></span>

 <span data-ttu-id="0c6f5-107">以一系列的註解寫入註解型說明。</span><span class="sxs-lookup"><span data-stu-id="0c6f5-107">Comment-based Help is written as a series of comments.</span></span> <span data-ttu-id="0c6f5-108">每一行的註解之前，您可以輸入註解符號 （#），或者您可以使用 「\<#"和"#>"符號，可建立註解區塊。</span><span class="sxs-lookup"><span data-stu-id="0c6f5-108">You can type a comment symbol (#) before each line of comments, or you can use the "\<#" and "#>" symbols to create a comment block.</span></span> <span data-ttu-id="0c6f5-109">註解區塊中的所有行會都解譯成註解。</span><span class="sxs-lookup"><span data-stu-id="0c6f5-109">All the lines within the comment block are interpreted as comments.</span></span>

 <span data-ttu-id="0c6f5-110">關鍵字所定義的註解型說明每個區段和每個關鍵字加句點 （.）。</span><span class="sxs-lookup"><span data-stu-id="0c6f5-110">Each section of comment-based Help is defined by a keyword and each keyword is preceded by a dot (.).</span></span> <span data-ttu-id="0c6f5-111">關鍵字可以按照任何順序出現。</span><span class="sxs-lookup"><span data-stu-id="0c6f5-111">The keywords can appear in any order.</span></span> <span data-ttu-id="0c6f5-112">關鍵字名稱不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="0c6f5-112">The keyword names are not case-sensitive.</span></span>

 <span data-ttu-id="0c6f5-113">註解區塊必須包含至少一個的 help 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="0c6f5-113">A comment block must contain at least one help keyword.</span></span> <span data-ttu-id="0c6f5-114">某些關鍵字，例如範例中，可以多次出現相同的註解區塊中。</span><span class="sxs-lookup"><span data-stu-id="0c6f5-114">Some of the keywords, such as EXAMPLE, can appear many times in the same comment block.</span></span> <span data-ttu-id="0c6f5-115">每個關鍵字的說明內容的關鍵字後開始列上，並可以跨越多行。</span><span class="sxs-lookup"><span data-stu-id="0c6f5-115">The Help content for each keyword begins on the line after the keyword and can span multiple lines.</span></span>

 <span data-ttu-id="0c6f5-116">所有註解型說明主題中的行必須是連續的。</span><span class="sxs-lookup"><span data-stu-id="0c6f5-116">All of the lines in a comment-based Help topic must be contiguous.</span></span> <span data-ttu-id="0c6f5-117">如果註解型說明主題後面的註解不是 [說明] 主題的一部分，必須有至少一個空白行，最後一個非說明註解線條之間開頭的註解型說明。</span><span class="sxs-lookup"><span data-stu-id="0c6f5-117">If a comment-based Help topic follows a comment that is not part of the Help topic, there must be at least one blank line between the last non-Help comment line and the beginning of the comment-based Help.</span></span>

 <span data-ttu-id="0c6f5-118">例如，包含下列的註解型說明主題。說明關鍵字和其值，也就是函式或指令碼的描述。</span><span class="sxs-lookup"><span data-stu-id="0c6f5-118">For example, the following comment-based help topic contains the .Description keyword and its value, which is a description of a function or script.</span></span>

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```