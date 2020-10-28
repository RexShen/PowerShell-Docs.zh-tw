---
ms.date: 10/20/2020
ms.topic: reference
title: 如何新增附註至 Cmdlet 說明主題
description: 如何新增附註至 Cmdlet 說明主題
ms.openlocfilehash: 61363c26ab0172277d1332ed1e9de080d8da200c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92659563"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a>如何新增附註至 Cmdlet 說明主題

此節描述如何將 [附註] 小節新增到 PowerShell Cmdlet 說明主題。 [附註] 小節是用來解釋無法輕鬆放入其他結構化小節的詳細資料，例如更詳細的參數說明。 此內容可能包括關於 Cmdlet 如何與特定提供者搭配使用的註解、一些獨特但重要的 Cmdlet 用法，或有助於避免可能發生錯誤狀況的方法。

[附註] 小節是使用單一 `<maml:alertset>` 節點來定義的。 您可以新增到 [附註] 小節的附註數目沒有限制。 針對每個附註，將一對 `<maml:alert>` 標記新增至 `<maml:alertset>` 節點。 每個附註的內容都會新增到一組 `<maml:para>` 標記內。 使用空白 `<maml:para>` 標記來加上間距。

```xml
<maml:alertSet>
  <maml:title>Optional title for Note</maml:title>
  <maml:alert>
    <maml:para>Note 1</maml:para>
    <maml:para>Note a</maml:para>
  </maml:alert>
  <maml:alert>
    <maml:para>Note 2</maml:para>
  </maml:alert>
</maml:alertSet>
```
