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
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a>如何新增相關連結至 Cmdlet 說明主題

本節說明如何將參考新增至與 PowerShell Cmdlet 說明主題相關的其他內容。 因為這些參考出現在命令視窗中，所以它們不會直接連結至參考的內容。

在 PowerShell 所包含的 Cmdlet 說明主題中，這些連結會參考其他 Cmdlet、概念內容 (`about_`) ，以及與 PowerShell 無關的其他檔和說明檔。

下列 XML 說明如何加入包含兩個相關主題參考的 **RelatedLinks** 節點。

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
