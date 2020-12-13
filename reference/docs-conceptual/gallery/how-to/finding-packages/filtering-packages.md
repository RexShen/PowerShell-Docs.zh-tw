---
ms.date: 06/12/2017
title: 篩選搜尋結果
description: 此文章描述用來篩選 PowerShell 資源庫內容的使用者介面。
ms.openlocfilehash: a769daae903e614b96be1056e3ff14eca41970bd
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94389822"
---
# <a name="filtering-search-results"></a><span data-ttu-id="feeb3-103">篩選搜尋結果</span><span class="sxs-lookup"><span data-stu-id="feeb3-103">Filtering search results</span></span>

<span data-ttu-id="feeb3-104">[套件索引標籤](https://www.powershellgallery.com/packages) \(英文\) 會顯示 PowerShell 資源庫中的所有可用套件。</span><span class="sxs-lookup"><span data-stu-id="feeb3-104">The [Packages tab](https://www.powershellgallery.com/packages) displays all available packages in the PowerShell Gallery.</span></span>

<span data-ttu-id="feeb3-105">有數種方式可篩選、排序和搜尋套件。</span><span class="sxs-lookup"><span data-stu-id="feeb3-105">There are several ways to filter, sort, and search the packages.</span></span> <span data-ttu-id="feeb3-106">若要查看特定套件的更多詳細資料，請按一下 [套件]。</span><span class="sxs-lookup"><span data-stu-id="feeb3-106">To see more details about a particular package, click the package.</span></span>

## <a name="filter-by"></a><span data-ttu-id="feeb3-107">篩選依據</span><span class="sxs-lookup"><span data-stu-id="feeb3-107">Filter By</span></span>

<span data-ttu-id="feeb3-108">[Filter By] \(篩選依據\) 之下的下拉式清單可讓使用者依據下列條件來篩選結果：</span><span class="sxs-lookup"><span data-stu-id="feeb3-108">The drop-down under "Filter By" allows users to filter the results by:</span></span>

- <span data-ttu-id="feeb3-109">Include Prerelease (包括發行前版本)</span><span class="sxs-lookup"><span data-stu-id="feeb3-109">Include Prerelease</span></span>
- <span data-ttu-id="feeb3-110">Stable Only (僅限穩定)</span><span class="sxs-lookup"><span data-stu-id="feeb3-110">Stable Only</span></span>

<span data-ttu-id="feeb3-111">如需「發行前版本」與「穩定版本」的相關資訊，請參閱 PowerShell 小組部落格中的 [PowerShellGet 與 PowerShell 資源庫新增了發行前版本的版本設定](https://devblogs.microsoft.com/powershell/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="feeb3-111">For information about "Prerelease" and "Stable", see [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://devblogs.microsoft.com/powershell/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) in the PowerShell Team Blog.</span></span>

<span data-ttu-id="feeb3-112">下拉式清單之下的核取方塊可讓使用者依據下列條件來篩選結果：</span><span class="sxs-lookup"><span data-stu-id="feeb3-112">The checkboxes under the drop-down allow users to filter the results by:</span></span>

- <span data-ttu-id="feeb3-113">套件類型</span><span class="sxs-lookup"><span data-stu-id="feeb3-113">Package Types</span></span>
  - <span data-ttu-id="feeb3-114">模組</span><span class="sxs-lookup"><span data-stu-id="feeb3-114">Module</span></span>
  - <span data-ttu-id="feeb3-115">指令碼</span><span class="sxs-lookup"><span data-stu-id="feeb3-115">Script</span></span>
- <span data-ttu-id="feeb3-116">類別</span><span class="sxs-lookup"><span data-stu-id="feeb3-116">Categories</span></span>
  - <span data-ttu-id="feeb3-117">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="feeb3-117">Cmdlet</span></span>
  - <span data-ttu-id="feeb3-118">DSC 資源</span><span class="sxs-lookup"><span data-stu-id="feeb3-118">DSC Resource</span></span>
  - <span data-ttu-id="feeb3-119">函式</span><span class="sxs-lookup"><span data-stu-id="feeb3-119">Function</span></span>
  - <span data-ttu-id="feeb3-120">角色功能</span><span class="sxs-lookup"><span data-stu-id="feeb3-120">Role Capability</span></span>
  - <span data-ttu-id="feeb3-121">工作流程</span><span class="sxs-lookup"><span data-stu-id="feeb3-121">Workflow</span></span>

<span data-ttu-id="feeb3-122">若只要查看 PowerShell 資源庫中的模組，請選取 [套件類型] 中的 [模組]。</span><span class="sxs-lookup"><span data-stu-id="feeb3-122">To see only modules in the PowerShell Gallery, check Module in the Package Types.</span></span> <span data-ttu-id="feeb3-123">同樣地，若只要查看 PowerShell 資源庫中的指令碼，請選取 [套件類型] 中的 [指令碼]。</span><span class="sxs-lookup"><span data-stu-id="feeb3-123">Similarly, to see only scripts in the PowerShell Gallery, check Script in the Package Types.</span></span>

> [!NOTE]
> <span data-ttu-id="feeb3-124">篩選條件是內含的。</span><span class="sxs-lookup"><span data-stu-id="feeb3-124">Filters are inclusive.</span></span> <span data-ttu-id="feeb3-125">範例：若已核取 [Cmdlet] 或 [函式] (或兩者)，將會顯示同時包含 Cmdlet 和函式的套件。</span><span class="sxs-lookup"><span data-stu-id="feeb3-125">Example: A package containing both cmdlets and functions will appear if either Cmdlet or Function (or both) are checked.</span></span> <span data-ttu-id="feeb3-126">如果未選取兩者，則不會顯示套件。</span><span class="sxs-lookup"><span data-stu-id="feeb3-126">If neither are selected, the package will not appear.</span></span> <span data-ttu-id="feeb3-127">同樣地，如果選取所有類別，則只會顯示包含其中一種類別的套件。</span><span class="sxs-lookup"><span data-stu-id="feeb3-127">Similarly, if all categories are selected, only packages containing one of those categories will appear.</span></span> <span data-ttu-id="feeb3-128">**不屬於所有這些類別的套件都不會出現。**</span><span class="sxs-lookup"><span data-stu-id="feeb3-128">**Packages that do not belong to any of those categories will not appear.**</span></span>

## <a name="sort-by"></a><span data-ttu-id="feeb3-129">排序依據</span><span class="sxs-lookup"><span data-stu-id="feeb3-129">Sort By</span></span>

<span data-ttu-id="feeb3-130">[Sort By] \(排序依據\) 下拉式清單可讓使用者依據下列條件來排序結果︰</span><span class="sxs-lookup"><span data-stu-id="feeb3-130">The Sort By drop-down allows users to sort the results by:</span></span>

- <span data-ttu-id="feeb3-131">[Popularity] \(熱門程度\)：熱門程度取決於下載計數</span><span class="sxs-lookup"><span data-stu-id="feeb3-131">Popularity - Popularity is determined by Download Count</span></span>
- <span data-ttu-id="feeb3-132">A-Z：依字母順序排序套件名稱</span><span class="sxs-lookup"><span data-stu-id="feeb3-132">A-Z - Alphabetically by package name</span></span>
- <span data-ttu-id="feeb3-133">最近：依發行日期順序顯示套件</span><span class="sxs-lookup"><span data-stu-id="feeb3-133">Recent - Packages appear in order of publish date</span></span>

## <a name="search-box"></a><span data-ttu-id="feeb3-134">搜尋方塊</span><span class="sxs-lookup"><span data-stu-id="feeb3-134">Search Box</span></span>

<span data-ttu-id="feeb3-135">[搜尋] 方塊可讓使用者根據關鍵字來搜尋套件。</span><span class="sxs-lookup"><span data-stu-id="feeb3-135">The Search Box allows users to search the packages on keywords.</span></span>
<span data-ttu-id="feeb3-136">如需詳細資訊，請參閱[資源庫搜尋語法](search-syntax.md)。</span><span class="sxs-lookup"><span data-stu-id="feeb3-136">For more information, see [Gallery Search Syntax](search-syntax.md).</span></span>
