---
ms.date: 10/20/2019
keywords: powershell,cmdlet
title: 如何使用 PowerShell 文件
ms.openlocfilehash: 80f72bb89b3bb82ee7c4d16b8969395f02d7d4ca
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72676172"
---
# <a name="how-to-use-the-powershell-documentation"></a><span data-ttu-id="32e09-103">如何使用 PowerShell 文件</span><span class="sxs-lookup"><span data-stu-id="32e09-103">How to use the PowerShell documentation</span></span>

<span data-ttu-id="32e09-104">歡迎使用 PowerShell 線上文件。</span><span class="sxs-lookup"><span data-stu-id="32e09-104">Welcome to the PowerShell online documentation.</span></span> <span data-ttu-id="32e09-105">此網站包含適用於下列 PowerShell 版本的 Cmdlet 參考：</span><span class="sxs-lookup"><span data-stu-id="32e09-105">This site contains cmdlet reference for the following versions of PowerShell:</span></span>

- <span data-ttu-id="32e09-106">PowerShell 7 (預覽)</span><span class="sxs-lookup"><span data-stu-id="32e09-106">PowerShell 7 (preview)</span></span>
- <span data-ttu-id="32e09-107">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="32e09-107">PowerShell 6</span></span>
- <span data-ttu-id="32e09-108">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="32e09-108">PowerShell 5.1</span></span>

## <a name="finding-articles-and-selecting-a-version"></a><span data-ttu-id="32e09-109">尋找文章並選取版本</span><span class="sxs-lookup"><span data-stu-id="32e09-109">Finding articles and selecting a version</span></span>

<span data-ttu-id="32e09-110">有兩種方式可搜尋文件中的內容。最簡單方式是使用版本選擇器下方的 [篩選] 方塊。</span><span class="sxs-lookup"><span data-stu-id="32e09-110">There are two ways to search for content in Docs. The simplest way is to use the filter box under the version selector.</span></span> <span data-ttu-id="32e09-111">只要輸入出現在文章標題中的字組即可。</span><span class="sxs-lookup"><span data-stu-id="32e09-111">Just enter a word that appears in the title of an article.</span></span> <span data-ttu-id="32e09-112">此頁面會顯示相符的文章清單。</span><span class="sxs-lookup"><span data-stu-id="32e09-112">The page displays a list of matching articles.</span></span> <span data-ttu-id="32e09-113">您也可以選取從該清單中搜尋整個網站的選項。</span><span class="sxs-lookup"><span data-stu-id="32e09-113">You can also select the option to search the entire site from that list.</span></span>

<span data-ttu-id="32e09-114">根據預設，此網站會顯示最新發行版本的 PowerShell 文件。</span><span class="sxs-lookup"><span data-stu-id="32e09-114">By default, this site displays documentation for the latest released version of PowerShell.</span></span> <span data-ttu-id="32e09-115">某些 Cmdlet 在各種 PowerShell 版本中的運作方式不同。</span><span class="sxs-lookup"><span data-stu-id="32e09-115">Some cmdlets work differently in various versions of PowerShell.</span></span> <span data-ttu-id="32e09-116">請確定您檢視您所使用 PowerShell 版本的文件。</span><span class="sxs-lookup"><span data-stu-id="32e09-116">Be sure you are viewing the documentation for the version of PowerShell you are using.</span></span>

<span data-ttu-id="32e09-117">使用頁面頂端的版本選擇器，選取您想要的 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="32e09-117">Use the version picker at the top of the page to select the version of PowerShell you want.</span></span>

![版本選擇器](images/how-to-use-docs/version-search.gif)

<span data-ttu-id="32e09-119">您可以透過檢查 `$PSversionTable.PSVersion` 值來檢查您使用的 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="32e09-119">You can verify the version of PowerShell you are using by inspecting the `$PSversionTable.PSVersion` value.</span></span> <span data-ttu-id="32e09-120">下列範例顯示 Windows PowerShell v5.1 的輸出。</span><span class="sxs-lookup"><span data-stu-id="32e09-120">The following example shows the output for Windows PowerShell v5.1.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```
