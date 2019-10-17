---
ms.date: 09/25/2019
keywords: powershell,cmdlet
title: 如何使用 PowerShell 文件
ms.openlocfilehash: 9e3d5828d6bdb4ef14701994f146354a041efaea
ms.sourcegitcommit: a80bb79b85deab8ae3c21de56d1ee432fdd92628
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/11/2019
ms.locfileid: "72281644"
---
# <a name="how-to-use-the-powershell-documentation"></a><span data-ttu-id="0d34c-103">如何使用 PowerShell 文件</span><span class="sxs-lookup"><span data-stu-id="0d34c-103">How to use the PowerShell documentation</span></span>

<span data-ttu-id="0d34c-104">歡迎使用 PowerShell 線上文件。</span><span class="sxs-lookup"><span data-stu-id="0d34c-104">Welcome to the PowerShell online documentation.</span></span> <span data-ttu-id="0d34c-105">此網站包含適用於下列 PowerShell 版本的 Cmdlet 參考：</span><span class="sxs-lookup"><span data-stu-id="0d34c-105">This site contains cmdlet reference for the following versions of PowerShell:</span></span>

- <span data-ttu-id="0d34c-106">PowerShell 7 (預覽)</span><span class="sxs-lookup"><span data-stu-id="0d34c-106">PowerShell 7 (preview)</span></span>
- <span data-ttu-id="0d34c-107">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="0d34c-107">PowerShell 6</span></span>
- <span data-ttu-id="0d34c-108">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="0d34c-108">PowerShell 5.1</span></span>
- <span data-ttu-id="0d34c-109">PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0d34c-109">PowerShell 5.0</span></span>
- <span data-ttu-id="0d34c-110">PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="0d34c-110">PowerShell 4.0</span></span>
- <span data-ttu-id="0d34c-111">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="0d34c-111">PowerShell 3.0</span></span>

## <a name="selecting-your-version"></a><span data-ttu-id="0d34c-112">選取您的版本</span><span class="sxs-lookup"><span data-stu-id="0d34c-112">Selecting your version</span></span>

<span data-ttu-id="0d34c-113">根據預設，此網站會顯示最新發行版本的 PowerShell 文件。</span><span class="sxs-lookup"><span data-stu-id="0d34c-113">By default, this site displays documentation for the latest released version of PowerShell.</span></span> <span data-ttu-id="0d34c-114">某些 Cmdlet 在各種 PowerShell 版本中的運作方式不同。</span><span class="sxs-lookup"><span data-stu-id="0d34c-114">Some cmdlets work differently in various versions of PowerShell.</span></span> <span data-ttu-id="0d34c-115">請確定您檢視您所使用 PowerShell 版本的文件。</span><span class="sxs-lookup"><span data-stu-id="0d34c-115">Be sure you are viewing the documentation for the version of PowerShell you are using.</span></span>

<span data-ttu-id="0d34c-116">使用頁面頂端的版本選擇器，選取您想要的 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="0d34c-116">Use the version picker at the top of the page to select the version of PowerShell you want.</span></span>

![版本選擇器](images/how-to-use-docs/picker-vall.gif)

<span data-ttu-id="0d34c-118">您可以透過檢查 `$PSversionTable.PSVersion` 值來檢查您使用的 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="0d34c-118">You can verify the version of PowerShell you are using by inspecting the `$PSversionTable.PSVersion` value.</span></span> <span data-ttu-id="0d34c-119">下列範例顯示 Windows PowerShell v5.1 的輸出。</span><span class="sxs-lookup"><span data-stu-id="0d34c-119">The following example shows the output for Windows PowerShell v5.1.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```

## <a name="searching-for-articles"></a><span data-ttu-id="0d34c-120">搜尋文章</span><span class="sxs-lookup"><span data-stu-id="0d34c-120">Searching for articles</span></span>

<span data-ttu-id="0d34c-121">有兩種方式可搜尋文件中的內容。最簡單方式是使用版本選擇器下方的 [篩選] 方塊。</span><span class="sxs-lookup"><span data-stu-id="0d34c-121">There are two ways to search for content in Docs. The simplest way is to use the filter box under the version selector.</span></span> <span data-ttu-id="0d34c-122">只要輸入出現在文章標題中的字組即可。</span><span class="sxs-lookup"><span data-stu-id="0d34c-122">Just enter a word that appears in the title of an article.</span></span> <span data-ttu-id="0d34c-123">此頁面會顯示相符的文章清單。</span><span class="sxs-lookup"><span data-stu-id="0d34c-123">The page displays a list of matching articles.</span></span> <span data-ttu-id="0d34c-124">您也可以選取從該清單中搜尋整個網站的選項。</span><span class="sxs-lookup"><span data-stu-id="0d34c-124">You can also select the option to search the entire site from that list.</span></span>

![篩選方塊](images/how-to-use-docs/filter-search.gif)
