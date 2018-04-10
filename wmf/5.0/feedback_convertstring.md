---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,設定
ms.openlocfilehash: 302a347b0f4c9c322f7701e8d6a721f9ffba9b59
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="convert-string"></a><span data-ttu-id="8b91a-102">Convert-String</span><span class="sxs-lookup"><span data-stu-id="8b91a-102">Convert-String</span></span>
<span data-ttu-id="8b91a-103">**Convert-String** 公開「像變魔術一樣取代」的功能。</span><span class="sxs-lookup"><span data-stu-id="8b91a-103">**Convert-String** exposes "replace by magic" functionality.</span></span> <span data-ttu-id="8b91a-104">提供範例說明您希望轉換前後文字長什麼樣子，**Convert-String** 就會自動設定文字的格式。</span><span class="sxs-lookup"><span data-stu-id="8b91a-104">Provide before and after examples of how you want text to look, and **Convert-String** formats your text automatically.</span></span> <span data-ttu-id="8b91a-105">以下是示範，輸入某人的名字和姓氏，然後取代為姓氏、逗號、名字首字母和一個點。</span><span class="sxs-lookup"><span data-stu-id="8b91a-105">Here's a demo - taking somebody's first and last name, and replacing it with their last name, a comma, the first initial of their last name, and a dot.</span></span> <span data-ttu-id="8b91a-106">試試看使用 Regex，就會知道要花多久時間。</span><span class="sxs-lookup"><span data-stu-id="8b91a-106">Try it with a regex, and see how long it takes you.</span></span>

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```