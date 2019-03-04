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
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a>如何新增相關連結至 Cmdlet 說明主題

本節說明如何將參考加入至 Windows PowerShell® cmdlet 說明主題相關的其他內容。 因為這些參考會出現在命令視窗中，它們表示不要連結直接到參照的內容。

在隨附於 Windows PowerShell® cmdlet 說明主題，這些連結會參考其他 cmdlet、 概念性的內容 ("about_") 和其他文件和 Windows PowerShell® 不相關的說明檔。

下列 XML 示範如何加入 RelatedLinks 節點，其中包含相關主題的兩個參考。

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



