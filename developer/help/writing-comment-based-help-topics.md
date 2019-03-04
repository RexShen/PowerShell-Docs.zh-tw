---
title: 撰寫註解式說明主題 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e619ab16-90ad-46e9-9bde-d6dce492ba56
caps.latest.revision: 4
ms.openlocfilehash: e3d32f36b597088abc41e229bb0955c1b25504e6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857574"
---
# <a name="writing-comment-based-help-topics"></a><span data-ttu-id="5205e-102">撰寫註解型說明主題</span><span class="sxs-lookup"><span data-stu-id="5205e-102">Writing Comment-Based Help Topics</span></span>

<span data-ttu-id="5205e-103">您可以使用特殊的說明註解關鍵字來撰寫函式和指令碼的註解式說明主題。</span><span class="sxs-lookup"><span data-stu-id="5205e-103">You can write comment-based Help topics for functions and scripts by using special Help comment keywords.</span></span>

 <span data-ttu-id="5205e-104">`Get-Help` Cmdlet 會顯示在相同的格式，它會顯示從 XML 檔案所產生的 cmdlet 說明主題中的註解型說明。</span><span class="sxs-lookup"><span data-stu-id="5205e-104">The `Get-Help` cmdlet displays comment-based Help in the same format in which it displays the cmdlet Help topics that are generated from XML files.</span></span> <span data-ttu-id="5205e-105">使用者可以使用所有的參數`Get-Help`，例如 Detailed、 全文，範例中，與 Online 之外，若要顯示函式和指令碼說明。</span><span class="sxs-lookup"><span data-stu-id="5205e-105">Users can use all of the parameters of `Get-Help`, such as Detailed, Full, Example, and Online, to display function and script Help.</span></span>

 <span data-ttu-id="5205e-106">您也可以撰寫以 XML 為基礎的指令碼和函式的說明主題，並使用 Help 註解關鍵字使用者重新導向至的 XML 架構的主題或其他主題。</span><span class="sxs-lookup"><span data-stu-id="5205e-106">You can also write XML-based Help topics for scripts and functions and use the Help comment keywords to redirect users to the XML-based topics or other topics.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="5205e-107">在本節中</span><span class="sxs-lookup"><span data-stu-id="5205e-107">In This Section</span></span>

 <span data-ttu-id="5205e-108">[語法的註解型說明](./syntax-of-comment-based-help.md)描述的註解型說明語法。</span><span class="sxs-lookup"><span data-stu-id="5205e-108">[Syntax of Comment-Based Help](./syntax-of-comment-based-help.md) Describes the syntax of comment-based help.</span></span>

 <span data-ttu-id="5205e-109">[註解型說明關鍵字](./comment-based-help-keywords.md)列出註解型說明中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="5205e-109">[Comment-Based Help Keywords](./comment-based-help-keywords.md) Lists the keywords in comment-based help.</span></span>

 <span data-ttu-id="5205e-110">[函式中放置註解型說明](./placing-comment-based-help-in-functions.md)顯示函式的註解型說明的位置。</span><span class="sxs-lookup"><span data-stu-id="5205e-110">[Placing Comment-Based Help in Functions](./placing-comment-based-help-in-functions.md) Shows where to place comment-based help for a function.</span></span>

 <span data-ttu-id="5205e-111">[在 指令碼中放置註解型說明](./placing-comment-based-help-in-scripts.md)顯示註解型說明的指令碼的位置。</span><span class="sxs-lookup"><span data-stu-id="5205e-111">[Placing Comment-Based Help in Scripts](./placing-comment-based-help-in-scripts.md) Shows where to place comment-based help for a script.</span></span>