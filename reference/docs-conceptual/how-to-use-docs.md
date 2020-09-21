---
ms.date: 07/29/2020
keywords: powershell,cmdlet
title: 如何使用 PowerShell 文件
ms.openlocfilehash: 1cfeb9eea564e7618062e1b8ada4948bd9e22969
ms.sourcegitcommit: 9f9eb95bc859e9e0fed48101327a602b2ced351d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87821524"
---
# <a name="how-to-use-the-powershell-documentation"></a><span data-ttu-id="0aa19-103">如何使用 PowerShell 文件</span><span class="sxs-lookup"><span data-stu-id="0aa19-103">How to use the PowerShell documentation</span></span>

<span data-ttu-id="0aa19-104">歡迎使用 PowerShell 線上文件。</span><span class="sxs-lookup"><span data-stu-id="0aa19-104">Welcome to the PowerShell online documentation.</span></span> <span data-ttu-id="0aa19-105">此網站包含適用於下列 PowerShell 版本的 Cmdlet 參考：</span><span class="sxs-lookup"><span data-stu-id="0aa19-105">This site contains cmdlet reference for the following versions of PowerShell:</span></span>

- <span data-ttu-id="0aa19-106">PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="0aa19-106">PowerShell 7</span></span>
- <span data-ttu-id="0aa19-107">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="0aa19-107">PowerShell 6</span></span>
- <span data-ttu-id="0aa19-108">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="0aa19-108">PowerShell 5.1</span></span>

## <a name="finding-articles-and-selecting-a-version"></a><span data-ttu-id="0aa19-109">尋找文章並選取版本</span><span class="sxs-lookup"><span data-stu-id="0aa19-109">Finding articles and selecting a version</span></span>

<span data-ttu-id="0aa19-110">有兩種方式可搜尋文件中的內容。最簡單方式是使用版本選擇器下方的 [篩選] 方塊。</span><span class="sxs-lookup"><span data-stu-id="0aa19-110">There are two ways to search for content in Docs. The simplest way is to use the filter box under the version selector.</span></span> <span data-ttu-id="0aa19-111">只要輸入出現在文章標題中的字組即可。</span><span class="sxs-lookup"><span data-stu-id="0aa19-111">Just enter a word that appears in the title of an article.</span></span> <span data-ttu-id="0aa19-112">此頁面會顯示相符的文章清單。</span><span class="sxs-lookup"><span data-stu-id="0aa19-112">The page displays a list of matching articles.</span></span> <span data-ttu-id="0aa19-113">您也可以選取從該清單中搜尋整個網站的選項。</span><span class="sxs-lookup"><span data-stu-id="0aa19-113">You can also select the option to search the entire site from that list.</span></span>

<span data-ttu-id="0aa19-114">根據預設，此網站會顯示最新發行版本的 PowerShell 文件。</span><span class="sxs-lookup"><span data-stu-id="0aa19-114">By default, this site displays documentation for the latest released version of PowerShell.</span></span> <span data-ttu-id="0aa19-115">某些 Cmdlet 在各種 PowerShell 版本中的運作方式不同。</span><span class="sxs-lookup"><span data-stu-id="0aa19-115">Some cmdlets work differently in various versions of PowerShell.</span></span> <span data-ttu-id="0aa19-116">請確定您檢視您所使用 PowerShell 版本的文件。</span><span class="sxs-lookup"><span data-stu-id="0aa19-116">Be sure you are viewing the documentation for the version of PowerShell you are using.</span></span>

<span data-ttu-id="0aa19-117">使用頁面頂端的版本選擇器，選取您想要的 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="0aa19-117">Use the version picker at the top of the page to select the version of PowerShell you want.</span></span>

![使用版本選擇器](media/how-to-use-docs/version-search.gif)

<span data-ttu-id="0aa19-119">您可以透過檢查 `$PSversionTable.PSVersion` 值來檢查您使用的 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="0aa19-119">You can verify the version of PowerShell you are using by inspecting the `$PSversionTable.PSVersion` value.</span></span> <span data-ttu-id="0aa19-120">下例顯示 Windows PowerShell 5.1 的輸出。</span><span class="sxs-lookup"><span data-stu-id="0aa19-120">The following example shows the output for Windows PowerShell 5.1.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      19041  1
```

<span data-ttu-id="0aa19-121">如果不熟悉 PowerShell，且需要了解命令語法的說明，請參閱 [about_Command_Syntax](/powershell/module/microsoft.powershell.core/about/about_command_syntax)。</span><span class="sxs-lookup"><span data-stu-id="0aa19-121">If you are new to PowerShell and need help understanding the command syntax, see [about_Command_Syntax](/powershell/module/microsoft.powershell.core/about/about_command_syntax).</span></span>

## <a name="finding-articles-for-previous-versions"></a><span data-ttu-id="0aa19-122">尋找舊版文章</span><span class="sxs-lookup"><span data-stu-id="0aa19-122">Finding articles for previous versions</span></span>

<span data-ttu-id="0aa19-123">舊版 PowerShell 的文件已封存在我們的[舊版](https://aka.ms/PSLegacyDocs)網站中。</span><span class="sxs-lookup"><span data-stu-id="0aa19-123">Documentation for older versions of PowerShell has been archived in our [Previous Versions](https://aka.ms/PSLegacyDocs) site.</span></span>

<span data-ttu-id="0aa19-124">此網站包含下列主題的文件：</span><span class="sxs-lookup"><span data-stu-id="0aa19-124">This site contains documentation for the following topics:</span></span>

- <span data-ttu-id="0aa19-125">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="0aa19-125">PowerShell 3.0</span></span>
- <span data-ttu-id="0aa19-126">PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="0aa19-126">PowerShell 4.0</span></span>
- <span data-ttu-id="0aa19-127">PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0aa19-127">PowerShell 5.0</span></span>
- <span data-ttu-id="0aa19-128">PowerShell 工作流程</span><span class="sxs-lookup"><span data-stu-id="0aa19-128">PowerShell Workflows</span></span>
- <span data-ttu-id="0aa19-129">PowerShell Web 存取</span><span class="sxs-lookup"><span data-stu-id="0aa19-129">PowerShell Web Access</span></span>
