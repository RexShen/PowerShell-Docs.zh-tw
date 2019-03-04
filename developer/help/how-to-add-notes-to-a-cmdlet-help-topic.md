---
title: 如何將資訊新增至 Cmdlet 的說明主題 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bea35e5-b680-4f86-b928-176890aac99d
caps.latest.revision: 5
ms.openlocfilehash: 4e9ca9a3bbcbc900d079b9275bc47d21de9e2996
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862264"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a><span data-ttu-id="fc08a-102">如何新增附註至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="fc08a-102">How to Add Notes to a Cmdlet Help Topic</span></span>

<span data-ttu-id="fc08a-103">本節說明如何將附註區段新增至 Windows PowerShell® cmdlet 說明主題。</span><span class="sxs-lookup"><span data-stu-id="fc08a-103">This section describes how to add a Notes section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="fc08a-104">附註區段用來說明不適合輕鬆地在其他結構化的區段，例如參數的詳細說明的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="fc08a-104">The Notes section is used to explain details that do not fit easily into the other structured sections, such as a more detailed explanation of a parameter.</span></span> <span data-ttu-id="fc08a-105">此內容可能包含與特定的提供者 cmdlet 的運作方式，一些唯一的但重要的是，會使用的 cmdlet 或如何避免可能的錯誤狀況的註解。</span><span class="sxs-lookup"><span data-stu-id="fc08a-105">This content could include comments on how the cmdlet works with a specific provider, some unique, yet important, uses of the cmdlet, or ways to avoid possible error conditions.</span></span>

<span data-ttu-id="fc08a-106">沒有任何限制，您可以加入提示 > 一節的附註的數目。</span><span class="sxs-lookup"><span data-stu-id="fc08a-106">There are no limits to the number of notes that you can add to a Notes section.</span></span> <span data-ttu-id="fc08a-107">針對每個提示中，加入一組\<maml:alert > 標記\<maml:alertset > 節點。</span><span class="sxs-lookup"><span data-stu-id="fc08a-107">For each note, add a pair of \<maml:alert> tags to the \<maml:alertset> node.</span></span> <span data-ttu-id="fc08a-108">每個提示的內容就會在一組\<: para><maml: > 標記。</span><span class="sxs-lookup"><span data-stu-id="fc08a-108">The content of each note is added within a set of \<maml:para> tags.</span></span> <span data-ttu-id="fc08a-109">使用空白\<: para><maml: > 標記間距。</span><span class="sxs-lookup"><span data-stu-id="fc08a-109">Use blank \<maml:para> tags for spacing.</span></span>

<span data-ttu-id="fc08a-110">下列 XML 會說明\<maml:alertset > 使用兩個節點的節點。</span><span class="sxs-lookup"><span data-stu-id="fc08a-110">The following XML shows an \<maml:alertset> node with two notes.</span></span> <span data-ttu-id="fc08a-111">請注意，每個提示有選擇性\<title> > 標記 (項目可用來群組一組\<maml:alert > 標記)，而且每個提示有空白行遵循間距的內容。</span><span class="sxs-lookup"><span data-stu-id="fc08a-111">Notice that each note has an optional \<maml:title> tag (titles can be used to group any set of \<maml:alert> tags), and that each note has a blank line following the content for spacing.</span></span>

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



