---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_items_tab
ms.openlocfilehash: 8704091542de5c19817ab0b4f77fd98987084b5d
ms.sourcegitcommit: 1a0a0928c1e3cae4e8df8d79b0737bd7ed6b4e47
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="items-tab"></a><span data-ttu-id="4f12c-103">項目索引標籤</span><span class="sxs-lookup"><span data-stu-id="4f12c-103">Items Tab</span></span>

<span data-ttu-id="4f12c-104">[Items (項目) 索引標籤](https://www.powershellgallery.com/items) \(英文\) 會顯示 PowerShell 資源庫中的所有可用項目。</span><span class="sxs-lookup"><span data-stu-id="4f12c-104">The [Items tab](https://www.powershellgallery.com/items) displays all available items in the PowerShell Gallery.</span></span>

<span data-ttu-id="4f12c-105">有數種方式可篩選、排序和搜尋項目。</span><span class="sxs-lookup"><span data-stu-id="4f12c-105">There are several ways to filter, sort, and search the items.</span></span>
<span data-ttu-id="4f12c-106">若要查看特定項目的更多詳細資料，請按一下項目。</span><span class="sxs-lookup"><span data-stu-id="4f12c-106">To see more details about a particular item, click the item.</span></span>

## <a name="filter-by"></a><span data-ttu-id="4f12c-107">篩選依據</span><span class="sxs-lookup"><span data-stu-id="4f12c-107">Filter By</span></span>

<span data-ttu-id="4f12c-108">[Filter By] \(篩選依據\) 之下的下拉式清單可讓使用者依據下列條件來篩選結果：</span><span class="sxs-lookup"><span data-stu-id="4f12c-108">The drop-down under "Filter By" allows users to filter the results by:</span></span>
* <span data-ttu-id="4f12c-109">Include Prerelease (包括發行前版本)</span><span class="sxs-lookup"><span data-stu-id="4f12c-109">Include Prerelease</span></span>
* <span data-ttu-id="4f12c-110">Stable Only (僅限穩定)</span><span class="sxs-lookup"><span data-stu-id="4f12c-110">Stable Only</span></span>

<span data-ttu-id="4f12c-111">如需「發行前版本」與「穩定版本」的相關資訊，請參閱 PowerShell 小組部落格中的 [PowerShellGet 與 PowerShell 資源庫新增了發行前版本的版本設定](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="4f12c-111">For information about "Prerelease" and "Stable", see [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) in the PowerShell Team Blog.</span></span>

<span data-ttu-id="4f12c-112">下拉式清單之下的核取方塊可讓使用者依據下列條件來篩選結果：</span><span class="sxs-lookup"><span data-stu-id="4f12c-112">The checkboxes under the drop-down allow users to filter the results by:</span></span>
* <span data-ttu-id="4f12c-113">項目類型</span><span class="sxs-lookup"><span data-stu-id="4f12c-113">Item Types</span></span>
  - <span data-ttu-id="4f12c-114">模組</span><span class="sxs-lookup"><span data-stu-id="4f12c-114">Module</span></span>
  - <span data-ttu-id="4f12c-115">指令碼</span><span class="sxs-lookup"><span data-stu-id="4f12c-115">Script</span></span>
* <span data-ttu-id="4f12c-116">類別</span><span class="sxs-lookup"><span data-stu-id="4f12c-116">Categories</span></span>
  - <span data-ttu-id="4f12c-117">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4f12c-117">Cmdlet</span></span>
  - <span data-ttu-id="4f12c-118">DSC 資源</span><span class="sxs-lookup"><span data-stu-id="4f12c-118">DSC Resource</span></span>
  - <span data-ttu-id="4f12c-119">函式</span><span class="sxs-lookup"><span data-stu-id="4f12c-119">Function</span></span>
  - <span data-ttu-id="4f12c-120">角色功能</span><span class="sxs-lookup"><span data-stu-id="4f12c-120">Role Capability</span></span>
  - <span data-ttu-id="4f12c-121">工作流程</span><span class="sxs-lookup"><span data-stu-id="4f12c-121">Workflow</span></span>

<span data-ttu-id="4f12c-122">若只要查看 PowerShell 資源庫中的模組，請選取 [Item Types] \(項目類型\) 中的 [Module] \(模組\)。</span><span class="sxs-lookup"><span data-stu-id="4f12c-122">To see only modules in the PowerShell Gallery, check Module in the Item Types.</span></span>
<span data-ttu-id="4f12c-123">同樣地，若只要查看 PowerShell 資源庫中的指令碼，請選取 [Item Types] \(項目類型\) 中的 [Script] \(指令碼\)。</span><span class="sxs-lookup"><span data-stu-id="4f12c-123">Similarly, to see only scripts in the PowerShell Gallery, check Script in the Item Types.</span></span>

> [!NOTE]
> <span data-ttu-id="4f12c-124">篩選條件是內含的。</span><span class="sxs-lookup"><span data-stu-id="4f12c-124">Filters are inclusive.</span></span>
> <span data-ttu-id="4f12c-125">範例︰如果選取了 [Cmdlet] 或 [Function] \(函數\) 之一或兩者皆選取，將會出現同時包含 Cmdlet 和函數的項目。</span><span class="sxs-lookup"><span data-stu-id="4f12c-125">Example: An item containing both cmdlets and functions will appear if either Cmdlet or Function (or both) are checked.</span></span>
> <span data-ttu-id="4f12c-126">如果未選取兩者，則不會顯示項目。</span><span class="sxs-lookup"><span data-stu-id="4f12c-126">If neither are selected, the item will not appear.</span></span>
> <span data-ttu-id="4f12c-127">同樣地，如果選取所有類別，則只會顯示包含其中一種類別的項目。</span><span class="sxs-lookup"><span data-stu-id="4f12c-127">Similarly, if all categories are selected, only items containing one of those categories will appear.</span></span>
> <span data-ttu-id="4f12c-128">**不屬於所有這些類別的項目都不會出現。**</span><span class="sxs-lookup"><span data-stu-id="4f12c-128">**Items that do not belong to any of those categories will not appear.**</span></span>

## <a name="sort-by"></a><span data-ttu-id="4f12c-129">排序依據</span><span class="sxs-lookup"><span data-stu-id="4f12c-129">Sort By</span></span>

<span data-ttu-id="4f12c-130">[Sort By] \(排序依據\) 下拉式清單可讓使用者依據下列條件來排序結果︰</span><span class="sxs-lookup"><span data-stu-id="4f12c-130">The Sort By drop-down allows users to sort the results by:</span></span>
* <span data-ttu-id="4f12c-131">[Popularity] \(熱門程度\)：熱門程度取決於下載計數</span><span class="sxs-lookup"><span data-stu-id="4f12c-131">Popularity - Popularity is determined by Download Count</span></span>
* <span data-ttu-id="4f12c-132">[A-Z]：依字母順序排序項目名稱</span><span class="sxs-lookup"><span data-stu-id="4f12c-132">A-Z - Alphabetically by item name</span></span>
* <span data-ttu-id="4f12c-133">[Recent] \(最近\)：依發行日期順序顯示項目</span><span class="sxs-lookup"><span data-stu-id="4f12c-133">Recent - Items appear in order of publish date</span></span>

## <a name="search-box"></a><span data-ttu-id="4f12c-134">搜尋方塊</span><span class="sxs-lookup"><span data-stu-id="4f12c-134">Search Box</span></span>

<span data-ttu-id="4f12c-135">[搜尋] 方塊可讓使用者根據關鍵字來搜尋項目。</span><span class="sxs-lookup"><span data-stu-id="4f12c-135">The Search Box allows users to search the items on keywords.</span></span>
<span data-ttu-id="4f12c-136">如需詳細資訊，請參閱[資源庫搜尋語法](psgallery_search_syntax.md)。</span><span class="sxs-lookup"><span data-stu-id="4f12c-136">For more information, see [Gallery Search Syntax](psgallery_search_syntax.md).</span></span>
