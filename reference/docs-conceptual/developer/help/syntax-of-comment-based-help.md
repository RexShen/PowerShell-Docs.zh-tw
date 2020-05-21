---
title: 以批註為基礎之說明的語法 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: da74c674c704794d8648dcdf9ba0a1617decba9b
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560605"
---
# <a name="syntax-of-comment-based-help"></a><span data-ttu-id="2f0d5-102">註解型說明的語法</span><span class="sxs-lookup"><span data-stu-id="2f0d5-102">Syntax of Comment-Based Help</span></span>

<span data-ttu-id="2f0d5-103">本節說明以批註為基礎之說明的語法。</span><span class="sxs-lookup"><span data-stu-id="2f0d5-103">This section describes the syntax of comment-based help.</span></span>

## <a name="syntax-diagram"></a><span data-ttu-id="2f0d5-104">語法圖表</span><span class="sxs-lookup"><span data-stu-id="2f0d5-104">Syntax Diagram</span></span>

 <span data-ttu-id="2f0d5-105">以批註為基礎的說明語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="2f0d5-105">The syntax for comment-based Help is as follows:</span></span>

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a><span data-ttu-id="2f0d5-106">語法描述</span><span class="sxs-lookup"><span data-stu-id="2f0d5-106">Syntax Description</span></span>

 <span data-ttu-id="2f0d5-107">以批註為基礎的說明會以一系列的批註來撰寫。</span><span class="sxs-lookup"><span data-stu-id="2f0d5-107">Comment-based Help is written as a series of comments.</span></span> <span data-ttu-id="2f0d5-108">您可以在每一行批註之前輸入批註符號（#），也可以使用 " \< #" 和 "# >" 符號來建立批註區塊。</span><span class="sxs-lookup"><span data-stu-id="2f0d5-108">You can type a comment symbol (#) before each line of comments, or you can use the "\<#" and "#>" symbols to create a comment block.</span></span> <span data-ttu-id="2f0d5-109">批註區塊中的所有行都會轉譯為批註。</span><span class="sxs-lookup"><span data-stu-id="2f0d5-109">All the lines within the comment block are interpreted as comments.</span></span>

 <span data-ttu-id="2f0d5-110">以批註為基礎的說明的每個區段都是由關鍵字所定義，而且每個關鍵字前面會加上點（.）。</span><span class="sxs-lookup"><span data-stu-id="2f0d5-110">Each section of comment-based Help is defined by a keyword and each keyword is preceded by a dot (.).</span></span> <span data-ttu-id="2f0d5-111">關鍵字可以依任何順序出現。</span><span class="sxs-lookup"><span data-stu-id="2f0d5-111">The keywords can appear in any order.</span></span> <span data-ttu-id="2f0d5-112">關鍵字名稱不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="2f0d5-112">The keyword names are not case-sensitive.</span></span>

 <span data-ttu-id="2f0d5-113">批註區塊必須包含至少一個 help 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="2f0d5-113">A comment block must contain at least one help keyword.</span></span> <span data-ttu-id="2f0d5-114">某些關鍵字（例如）可能會在相同的批註區塊中出現多次。</span><span class="sxs-lookup"><span data-stu-id="2f0d5-114">Some of the keywords, such as EXAMPLE, can appear many times in the same comment block.</span></span> <span data-ttu-id="2f0d5-115">每個關鍵字的說明內容都是在關鍵字後面的一行開始，而且可以跨越多行。</span><span class="sxs-lookup"><span data-stu-id="2f0d5-115">The Help content for each keyword begins on the line after the keyword and can span multiple lines.</span></span>

 <span data-ttu-id="2f0d5-116">以批註為基礎的說明主題中的所有行都必須是連續的。</span><span class="sxs-lookup"><span data-stu-id="2f0d5-116">All of the lines in a comment-based Help topic must be contiguous.</span></span> <span data-ttu-id="2f0d5-117">如果以批註為基礎的說明主題遵循不屬於說明主題的批註，則最後一個非說明批註行和批註式說明開頭必須至少有一個空白行。</span><span class="sxs-lookup"><span data-stu-id="2f0d5-117">If a comment-based Help topic follows a comment that is not part of the Help topic, there must be at least one blank line between the last non-Help comment line and the beginning of the comment-based Help.</span></span>

 <span data-ttu-id="2f0d5-118">例如，下列以批註為基礎的說明主題包含。Description 關鍵字及其值，這是函數或腳本的描述。</span><span class="sxs-lookup"><span data-stu-id="2f0d5-118">For example, the following comment-based help topic contains the .Description keyword and its value, which is a description of a function or script.</span></span>

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```
