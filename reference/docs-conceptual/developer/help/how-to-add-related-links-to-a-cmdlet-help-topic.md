---
ms.date: 09/12/2016
ms.topic: reference
title: 如何新增相關連結至 Cmdlet 說明主題
description: 如何新增相關連結至 Cmdlet 說明主題
ms.openlocfilehash: 7f1baefea69310bdf835c52461f8d3f49c4d94e8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92661990"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a><span data-ttu-id="91c3e-103">如何新增相關連結至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="91c3e-103">How to Add Related Links to a Cmdlet Help Topic</span></span>

<span data-ttu-id="91c3e-104">本節說明如何將參考新增至與 PowerShell Cmdlet 說明主題相關的其他內容。</span><span class="sxs-lookup"><span data-stu-id="91c3e-104">This section describes how to add references to other content that is related to a PowerShell cmdlet Help topic.</span></span> <span data-ttu-id="91c3e-105">因為這些參考出現在命令視窗中，所以它們不會直接連結至參考的內容。</span><span class="sxs-lookup"><span data-stu-id="91c3e-105">Because these references appear in a command window, they do not link directly to the referenced content.</span></span>

<span data-ttu-id="91c3e-106">在 PowerShell 所包含的 Cmdlet 說明主題中，這些連結會參考其他 Cmdlet、概念內容 (`about_`) ，以及與 PowerShell 無關的其他檔和說明檔。</span><span class="sxs-lookup"><span data-stu-id="91c3e-106">In the cmdlet Help topics that are included in PowerShell, these links reference other cmdlets, conceptual content (`about_`), and other documents and Help files that are not related to PowerShell.</span></span>

<span data-ttu-id="91c3e-107">下列 XML 說明如何加入包含兩個相關主題參考的 **RelatedLinks** 節點。</span><span class="sxs-lookup"><span data-stu-id="91c3e-107">The following XML shows how to add a **RelatedLinks** node that contains two references to related topics.</span></span>

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
