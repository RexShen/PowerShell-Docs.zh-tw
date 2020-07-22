---
title: 如何新增附註至 Cmdlet 說明主題
ms.date: 09/12/2016
ms.openlocfilehash: d3679126ea34d7e86bcda700d0d050d8312a7aa2
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893402"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a>如何新增附註至 Cmdlet 說明主題

本節說明如何將**附注**區段新增至 PowerShell Cmdlet 說明主題。 **附注**區段是用來說明無法輕易地放入其他結構化區段的詳細資料，例如參數的更詳細說明。 此內容可能包含關於 Cmdlet 如何與特定提供者搭配使用的批註、一些獨特但重要的用法、Cmdlet，或避免可能發生錯誤狀況的方法。

您可以新增至附注區段的便箋數目沒有限制。 針對每個便箋，將一對 `<maml:alert>` 標記新增至 `<maml:alertset>` 節點。 每個便箋的內容都會加入一組標記內 `<maml:para>` 。 使用空白 `<maml:para>` 標記來進行間距。

下列 XML 顯示 `<maml:alertset>` 具有兩個附注的節點。 請注意，每個便箋都有一個選擇性 `<maml:title>` 標記（標題可以用來分組任何一組 `<maml:alert>` 標記），而且每個便箋的內容後面都會有一個空白行。

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
