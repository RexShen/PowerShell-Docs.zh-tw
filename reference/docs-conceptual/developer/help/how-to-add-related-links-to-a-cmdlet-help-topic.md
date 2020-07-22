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
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a>如何新增相關連結至 Cmdlet 說明主題

本節說明如何新增與 PowerShell Cmdlet 說明主題相關的其他內容參考。 因為這些參考會出現在命令視窗中，所以它們不會直接連結至參考的內容。

在 PowerShell 所包含的 Cmdlet 說明主題中，這些連結會參考其他 Cmdlet、概念內容（ `about_` ），以及與 powershell 不相關的其他檔和說明檔。

下列 XML 顯示如何將包含兩個參考的**RelatedLinks**節點加入至相關主題。

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
