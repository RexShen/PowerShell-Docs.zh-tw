---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,設定"
ms.openlocfilehash: 6caff8c06174a1dcb990ed8e5062ccca5848dbb8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="convert-string"></a><span data-ttu-id="3ca6a-102">Convert-String</span><span class="sxs-lookup"><span data-stu-id="3ca6a-102">Convert-String</span></span>
<span data-ttu-id="3ca6a-103">**Convert-String** 公開「像變魔術一樣取代」的功能。</span><span class="sxs-lookup"><span data-stu-id="3ca6a-103">**Convert-String** exposes "replace by magic" functionality.</span></span> <span data-ttu-id="3ca6a-104">提供範例說明您希望轉換前後文字長什麼樣子，**Convert-String** 就會自動設定文字的格式。</span><span class="sxs-lookup"><span data-stu-id="3ca6a-104">Provide before and after examples of how you want text to look, and **Convert-String** formats your text automatically.</span></span> <span data-ttu-id="3ca6a-105">以下是示範，輸入某人的名字和姓氏，然後取代為姓氏、逗號、名字首字母和一個點。</span><span class="sxs-lookup"><span data-stu-id="3ca6a-105">Here's a demo - taking somebody's first and last name, and replacing it with their last name, a comma, the first initial of their last name, and a dot.</span></span> <span data-ttu-id="3ca6a-106">試試看使用 Regex，就會知道要花多久時間。</span><span class="sxs-lookup"><span data-stu-id="3ca6a-106">Try it with a regex, and see how long it takes you.</span></span>

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```

