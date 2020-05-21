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
ms.openlocfilehash: 0a6403e2dea16d73e2fdcb8cf5df39b2aa5b5dae
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560265"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a>如何新增相關連結至 Cmdlet 說明主題

本節說明如何新增與 Windows PowerShell® Cmdlet 說明主題相關的其他內容參考。 因為這些參考會出現在命令視窗中，所以它們不會直接連結至參考的內容。

在 Windows PowerShell®所包含的 Cmdlet 說明主題中，這些連結會參考其他 Cmdlet、概念內容（"about_"），以及與 Windows PowerShell®無關的其他檔和說明檔案。

下列 XML 顯示如何將包含兩個參考的 RelatedLinks 節點加入至相關主題。

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
