---
title: 如何新增相關連結至 Cmdlet 說明主題
ms.date: 09/12/2016
ms.openlocfilehash: 7557b3856d8470434070dd286cd7e30c9ba015c5
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893368"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a><span data-ttu-id="3fff7-102">如何新增相關連結至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="3fff7-102">How to Add Related Links to a Cmdlet Help Topic</span></span>

<span data-ttu-id="3fff7-103">本節說明如何新增與 PowerShell Cmdlet 說明主題相關的其他內容參考。</span><span class="sxs-lookup"><span data-stu-id="3fff7-103">This section describes how to add references to other content that is related to a PowerShell cmdlet Help topic.</span></span> <span data-ttu-id="3fff7-104">因為這些參考會出現在命令視窗中，所以它們不會直接連結至參考的內容。</span><span class="sxs-lookup"><span data-stu-id="3fff7-104">Because these references appear in a command window, they do not link directly to the referenced content.</span></span>

<span data-ttu-id="3fff7-105">在 PowerShell 所包含的 Cmdlet 說明主題中，這些連結會參考其他 Cmdlet、概念內容（ `about_` ），以及與 powershell 不相關的其他檔和說明檔。</span><span class="sxs-lookup"><span data-stu-id="3fff7-105">In the cmdlet Help topics that are included in PowerShell, these links reference other cmdlets, conceptual content (`about_`), and other documents and Help files that are not related to PowerShell.</span></span>

<span data-ttu-id="3fff7-106">下列 XML 顯示如何將包含兩個參考的**RelatedLinks**節點加入至相關主題。</span><span class="sxs-lookup"><span data-stu-id="3fff7-106">The following XML shows how to add a **RelatedLinks** node that contains two references to related topics.</span></span>

```xml
<maml:relatedLinks>
  <maml:navigationLink>
    <maml:linkText>Topic-name</maml:linkText>
  </maml:navigationLink>
  <maml:navigationLink>
    <maml:linkText>Topic-name</maml:linkText>
  </maml:navigationLink>
</ maml:relatedLinks >
```
