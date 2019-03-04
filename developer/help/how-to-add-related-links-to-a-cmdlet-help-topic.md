---
title: 如何將相關的連結新增至 Cmdlet 的說明主題 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5aadb730-4eb7-4936-b8df-3b0c0ca04fd5
caps.latest.revision: 5
ms.openlocfilehash: aa46cbc5bfcfdfec9fcf9d2581ff641baa532860
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855394"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a><span data-ttu-id="5778d-102">如何新增相關連結至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="5778d-102">How to Add Related Links to a Cmdlet Help Topic</span></span>

<span data-ttu-id="5778d-103">本節說明如何將參考加入至 Windows PowerShell® cmdlet 說明主題相關的其他內容。</span><span class="sxs-lookup"><span data-stu-id="5778d-103">This section describes how to add references to other content that is related to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="5778d-104">因為這些參考會出現在命令視窗中，它們表示不要連結直接到參照的內容。</span><span class="sxs-lookup"><span data-stu-id="5778d-104">Because these references appear in a command window, they do not link directly to the referenced content.</span></span>

<span data-ttu-id="5778d-105">在隨附於 Windows PowerShell® cmdlet 說明主題，這些連結會參考其他 cmdlet、 概念性的內容 ("about_") 和其他文件和 Windows PowerShell® 不相關的說明檔。</span><span class="sxs-lookup"><span data-stu-id="5778d-105">In the cmdlet Help topics that are included in Windows PowerShell®, these links reference other cmdlets, conceptual content ("about_"), and other documents and Help files that are not related to Windows PowerShell®.</span></span>

<span data-ttu-id="5778d-106">下列 XML 示範如何加入 RelatedLinks 節點，其中包含相關主題的兩個參考。</span><span class="sxs-lookup"><span data-stu-id="5778d-106">The following XML shows how to add a RelatedLinks node that contains two references to related topics.</span></span>

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



