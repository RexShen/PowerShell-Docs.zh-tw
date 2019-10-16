---
title: 如何將相關連結新增至 Cmdlet 說明主題 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5aadb730-4eb7-4936-b8df-3b0c0ca04fd5
caps.latest.revision: 5
ms.openlocfilehash: aa46cbc5bfcfdfec9fcf9d2581ff641baa532860
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361217"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a><span data-ttu-id="7c193-102">如何新增相關連結至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="7c193-102">How to Add Related Links to a Cmdlet Help Topic</span></span>

<span data-ttu-id="7c193-103">本節說明如何新增與 Windows PowerShell® Cmdlet 說明主題相關的其他內容參考。</span><span class="sxs-lookup"><span data-stu-id="7c193-103">This section describes how to add references to other content that is related to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="7c193-104">因為這些參考會出現在命令視窗中，所以它們不會直接連結至參考的內容。</span><span class="sxs-lookup"><span data-stu-id="7c193-104">Because these references appear in a command window, they do not link directly to the referenced content.</span></span>

<span data-ttu-id="7c193-105">在 Windows PowerShell®所包含的 Cmdlet 說明主題中，這些連結會參考其他 Cmdlet、概念內容（"about_"），以及與 Windows PowerShell®無關的其他檔和說明檔案。</span><span class="sxs-lookup"><span data-stu-id="7c193-105">In the cmdlet Help topics that are included in Windows PowerShell®, these links reference other cmdlets, conceptual content ("about_"), and other documents and Help files that are not related to Windows PowerShell®.</span></span>

<span data-ttu-id="7c193-106">下列 XML 顯示如何將包含兩個參考的 RelatedLinks 節點加入至相關主題。</span><span class="sxs-lookup"><span data-stu-id="7c193-106">The following XML shows how to add a RelatedLinks node that contains two references to related topics.</span></span>

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



