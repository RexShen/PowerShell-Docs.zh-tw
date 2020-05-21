---
title: 如何將附注新增至 Cmdlet 說明主題 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bea35e5-b680-4f86-b928-176890aac99d
caps.latest.revision: 5
ms.openlocfilehash: 1a365a167c245006bb882a542aedb5c43cfc4c96
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557102"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a>如何新增附註至 Cmdlet 說明主題

本節說明如何將附注區段新增至 Windows PowerShell® Cmdlet 說明主題。 附注區段是用來說明無法輕易地放入其他結構化區段的詳細資料，例如參數的更詳細說明。 此內容可能包含關於 Cmdlet 如何與特定提供者搭配使用的批註、一些獨特但重要的用法、Cmdlet，或避免可能發生錯誤狀況的方法。

您可以新增至附注區段的便箋數目沒有限制。 針對每個便箋，將一對 \< maml： alert> 標記新增至 \< maml： alertset> 節點。 每個便箋的內容都會加入一組 \< maml：段落> 標記中。 使用空白 \< 的 maml：段落> 標籤的間距。

下列 XML 顯示 \< 具有兩個附注的 maml： alertset> 節點。 請注意，每個便箋都有一個選擇性的 \< maml： title> 標記（標題可用來將任何 \< maml 集合分組：警示> 標記），而且每個便箋的內容後面都有一個空白行。

```xml
<maml:alertSet>
  <maml:title>title for Note 1</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
  <maml:title>title for Note 2</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
</maml:alertSet>
```
