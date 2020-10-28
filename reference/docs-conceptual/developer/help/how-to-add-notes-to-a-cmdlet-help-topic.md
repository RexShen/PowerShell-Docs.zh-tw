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
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a><span data-ttu-id="74c9e-103">如何新增附註至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="74c9e-103">How to Add Notes to a Cmdlet Help Topic</span></span>

<span data-ttu-id="74c9e-104">此節描述如何將 [附註] 小節新增到 PowerShell Cmdlet 說明主題。</span><span class="sxs-lookup"><span data-stu-id="74c9e-104">This section describes how to add a **NOTES** section to a PowerShell cmdlet Help topic.</span></span> <span data-ttu-id="74c9e-105">[附註] 小節是用來解釋無法輕鬆放入其他結構化小節的詳細資料，例如更詳細的參數說明。</span><span class="sxs-lookup"><span data-stu-id="74c9e-105">The **NOTES** section is used to explain details that do not fit easily into the other structured sections, such as a more detailed explanation of a parameter.</span></span> <span data-ttu-id="74c9e-106">此內容可能包括關於 Cmdlet 如何與特定提供者搭配使用的註解、一些獨特但重要的 Cmdlet 用法，或有助於避免可能發生錯誤狀況的方法。</span><span class="sxs-lookup"><span data-stu-id="74c9e-106">This content could include comments on how the cmdlet works with a specific provider, some unique, yet important, uses of the cmdlet, or ways to avoid possible error conditions.</span></span>

<span data-ttu-id="74c9e-107">[附註] 小節是使用單一 `<maml:alertset>` 節點來定義的。</span><span class="sxs-lookup"><span data-stu-id="74c9e-107">The **NOTES** section is defined using a single `<maml:alertset>` node.</span></span> <span data-ttu-id="74c9e-108">您可以新增到 [附註] 小節的附註數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="74c9e-108">There are no limits to the number of notes that you can add to a Notes section.</span></span> <span data-ttu-id="74c9e-109">針對每個附註，將一對 `<maml:alert>` 標記新增至 `<maml:alertset>` 節點。</span><span class="sxs-lookup"><span data-stu-id="74c9e-109">For each note, add a pair of `<maml:alert>` tags to the `<maml:alertset>` node.</span></span> <span data-ttu-id="74c9e-110">每個附註的內容都會新增到一組 `<maml:para>` 標記內。</span><span class="sxs-lookup"><span data-stu-id="74c9e-110">The content of each note is added within a set of `<maml:para>` tags.</span></span> <span data-ttu-id="74c9e-111">使用空白 `<maml:para>` 標記來加上間距。</span><span class="sxs-lookup"><span data-stu-id="74c9e-111">Use blank `<maml:para>` tags for spacing.</span></span>

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
