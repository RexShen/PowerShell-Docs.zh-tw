---
ms.date: 09/13/2016
ms.topic: reference
title: 撰寫註解型說明主題
description: 撰寫註解型說明主題
ms.openlocfilehash: 11bbadfde27a74bde29d336b91516939e7265b3b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658797"
---
# <a name="writing-comment-based-help-topics"></a><span data-ttu-id="c29e1-103">撰寫註解型說明主題</span><span class="sxs-lookup"><span data-stu-id="c29e1-103">Writing Comment-Based Help Topics</span></span>

<span data-ttu-id="c29e1-104">您可以使用特殊的說明批註關鍵字來撰寫函數和腳本的批註式說明主題。</span><span class="sxs-lookup"><span data-stu-id="c29e1-104">You can write comment-based Help topics for functions and scripts by using special Help comment keywords.</span></span>

 <span data-ttu-id="c29e1-105">此 `Get-Help` Cmdlet 會顯示以批註為基礎的說明，其格式會顯示從 XML 檔案產生的 Cmdlet 說明主題。</span><span class="sxs-lookup"><span data-stu-id="c29e1-105">The `Get-Help` cmdlet displays comment-based Help in the same format in which it displays the cmdlet Help topics that are generated from XML files.</span></span> <span data-ttu-id="c29e1-106">使用者可以使用的所有參數（ `Get-Help` 如詳細、完整、範例和線上）來顯示函數和腳本說明。</span><span class="sxs-lookup"><span data-stu-id="c29e1-106">Users can use all of the parameters of `Get-Help`, such as Detailed, Full, Example, and Online, to display function and script Help.</span></span>

 <span data-ttu-id="c29e1-107">您也可以撰寫腳本和函式的 XML 型說明主題，並使用說明批註關鍵字將使用者重新導向至以 XML 為基礎的主題或其他主題。</span><span class="sxs-lookup"><span data-stu-id="c29e1-107">You can also write XML-based Help topics for scripts and functions and use the Help comment keywords to redirect users to the XML-based topics or other topics.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="c29e1-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="c29e1-108">In This Section</span></span>

 <span data-ttu-id="c29e1-109">[Comment-Based 說明的語法](./syntax-of-comment-based-help.md) 描述以批註為基礎的說明語法。</span><span class="sxs-lookup"><span data-stu-id="c29e1-109">[Syntax of Comment-Based Help](./syntax-of-comment-based-help.md) Describes the syntax of comment-based help.</span></span>

 <span data-ttu-id="c29e1-110">以[批註為基礎的說明關鍵字](./comment-based-help-keywords.md)列出以批註為基礎的說明中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c29e1-110">[Comment-Based Help Keywords](./comment-based-help-keywords.md) Lists the keywords in comment-based help.</span></span>

 <span data-ttu-id="c29e1-111">[在函數中放置 Comment-Based](./placing-comment-based-help-in-functions.md) 說明顯示在何處放置函式以批註為基礎的說明。</span><span class="sxs-lookup"><span data-stu-id="c29e1-111">[Placing Comment-Based Help in Functions](./placing-comment-based-help-in-functions.md) Shows where to place comment-based help for a function.</span></span>

 <span data-ttu-id="c29e1-112">[在腳本中放入 Comment-Based 協助](./placing-comment-based-help-in-scripts.md) 顯示腳本的批註式說明放置位置。</span><span class="sxs-lookup"><span data-stu-id="c29e1-112">[Placing Comment-Based Help in Scripts](./placing-comment-based-help-in-scripts.md) Shows where to place comment-based help for a script.</span></span>
