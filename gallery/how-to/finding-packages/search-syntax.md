---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 組件庫搜尋語法
ms.openlocfilehash: aabcaa1f1b5b641ab5033c9ba2e358477c84a23b
ms.sourcegitcommit: e24525046dd37166b9d83eeecdc534726316f429
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2018
ms.locfileid: "52742851"
---
# <a name="gallery-search-syntax"></a><span data-ttu-id="ec327-103">組件庫搜尋語法</span><span class="sxs-lookup"><span data-stu-id="ec327-103">Gallery Search Syntax</span></span>

<span data-ttu-id="ec327-104">您可以使用 PowerShell 資源庫搜尋[PowerShell 資源庫的網站](https://www.powershellgallery.com/)。</span><span class="sxs-lookup"><span data-stu-id="ec327-104">You can search the PowerShell Gallery using the [PowerShell Gallery's web site](https://www.powershellgallery.com/).</span></span>
<span data-ttu-id="ec327-105">PowerShell 資源庫的網站提供文字搜尋方塊，您可以使用單字、 片語和關鍵字運算式來縮小搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="ec327-105">PowerShell Gallery web site offers a text searchbox where you can use words, phrases and keyword expressions to narrow down search results.</span></span>

## <a name="search-by-keywords"></a><span data-ttu-id="ec327-106">依關鍵字搜尋</span><span class="sxs-lookup"><span data-stu-id="ec327-106">Search by Keywords</span></span>

    dsc azure sql

<span data-ttu-id="ec327-107">搜尋會嘗試尋找相關的文件包含所有 3 個關鍵字，並傳回相符文件。</span><span class="sxs-lookup"><span data-stu-id="ec327-107">Search attempts to find relevant documents containing all 3 keywords, and return matching documents.</span></span>

## <a name="search-using-phrases-and-keywords"></a><span data-ttu-id="ec327-108">使用片語和關鍵字搜尋</span><span class="sxs-lookup"><span data-stu-id="ec327-108">Search using Phrases and keywords</span></span>

    "azure sql" deployment

<span data-ttu-id="ec327-109">輸入加上引號 ("") 的片語，會變更搜尋以尋找特定片語，而非個別關鍵字。</span><span class="sxs-lookup"><span data-stu-id="ec327-109">Entering a phrase between quotation marks ("") change the search to look for the particular phrase instead of separate keywords.</span></span>
<span data-ttu-id="ec327-110">相符文件通常應該會包含精確片語 "azure sql" (包含大寫變化，例如"Azure SQL")，通常也會包含 'deployment' 這個字。</span><span class="sxs-lookup"><span data-stu-id="ec327-110">Matching documents should usually contain the exact phrase "azure sql", including variations on capitalization e.g. "Azure SQL", and also usually contain the word 'deployment'.</span></span>

## <a name="filtering-on-fields"></a><span data-ttu-id="ec327-111">根據欄位進行篩選</span><span class="sxs-lookup"><span data-stu-id="ec327-111">Filtering on fields</span></span>

<span data-ttu-id="ec327-112">您可以搜尋特定套件識別碼 (或者 'Id' 或 'id')，或在搜尋詞彙前面加上欄位名稱來搜尋特定其他欄位。</span><span class="sxs-lookup"><span data-stu-id="ec327-112">You can search for a specific package ID (or 'Id' or 'id'), or certain other fields by prefixing search terms with the field name.</span></span>

<span data-ttu-id="ec327-113">可搜尋的欄位目前是 'Id'、'Version'、'Tags'、'Author'、'Owner'、'Functions'、'Cmdlets'、'DscResources' 和 'PowerShellVersion'。</span><span class="sxs-lookup"><span data-stu-id="ec327-113">Currently the searchable fields are 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' and 'PowerShellVersion'.</span></span>

<span data-ttu-id="ec327-114">[識別碼與標題的差異為何？</span><span class="sxs-lookup"><span data-stu-id="ec327-114">[What's the difference between ID and Title?</span></span> <span data-ttu-id="ec327-115">識別碼是您在主控台中使用的名稱。</span><span class="sxs-lookup"><span data-stu-id="ec327-115">ID is the name you use in the console.</span></span> <span data-ttu-id="ec327-116">標題是搜尋結果中套件頁面頂端所顯示的內容。]</span><span class="sxs-lookup"><span data-stu-id="ec327-116">Title is what is shown at the top of the package page in search results.]</span></span>

## <a name="examples"></a><span data-ttu-id="ec327-117">範例</span><span class="sxs-lookup"><span data-stu-id="ec327-117">Examples</span></span>

    ID:PSReadline
    
<span data-ttu-id="ec327-118">尋找包含"PSReadline"識別碼的封裝。</span><span class="sxs-lookup"><span data-stu-id="ec327-118">finds packages with an ID containing "PSReadline".</span></span>

    Id:"AzureRM.Profile"

<span data-ttu-id="ec327-119">是尋找 [識別碼] 欄位中有 "AzureRM.Profile" 之套件的另一種方式。</span><span class="sxs-lookup"><span data-stu-id="ec327-119">is another way to find packages with "AzureRM.Profile" in their ID field.</span></span>

<span data-ttu-id="ec327-120">'Id' 篩選是子字串比對，因此，如果您搜尋下列項目︰</span><span class="sxs-lookup"><span data-stu-id="ec327-120">The 'Id' filter is a substring match, so if you search for the following:</span></span>

    Id:"azure"

<span data-ttu-id="ec327-121">這提供結果，其中包含 AzureRM.Profile' 和 'Azure.Storage'。</span><span class="sxs-lookup"><span data-stu-id="ec327-121">This provides results that include AzureRM.Profile' and 'Azure.Storage'.</span></span>

<span data-ttu-id="ec327-122">您也可以在單一欄位中搜尋多個關鍵字。</span><span class="sxs-lookup"><span data-stu-id="ec327-122">You can also search for multiple keywords in a single field.</span></span> 

    id:azure tags:intellisense

<span data-ttu-id="ec327-123">此外，您可以執行使用雙引號括住片語搜尋：</span><span class="sxs-lookup"><span data-stu-id="ec327-123">And you can perform phrase searches using double quotes:</span></span>

    id:"azure.storage"

<span data-ttu-id="ec327-124">使用 DSC 標記搜尋所有套件。</span><span class="sxs-lookup"><span data-stu-id="ec327-124">To search all packages with DSC tag.</span></span>

    Tags:DSC

<span data-ttu-id="ec327-125">使用指定的函數搜尋所有套件。</span><span class="sxs-lookup"><span data-stu-id="ec327-125">To search all packages with the specified function.</span></span>

    Functions:Get-TreeSize

<span data-ttu-id="ec327-126">使用指定的 Cmdlet 搜尋所有套件。</span><span class="sxs-lookup"><span data-stu-id="ec327-126">To search all packages with the specified cmdlet.</span></span>

    Cmdlets:Get-AzureRmEnvironment

<span data-ttu-id="ec327-127">使用指定的「DSC 資源」名稱搜尋所有套件。</span><span class="sxs-lookup"><span data-stu-id="ec327-127">To search all packages with the specified DSC Resource name.</span></span>

    DscResources:xArchive

<span data-ttu-id="ec327-128">使用指定的 PowerShellVersion 搜尋所有套件</span><span class="sxs-lookup"><span data-stu-id="ec327-128">To search all packages with the specified PowerShellVersion</span></span>

    PowerShellVersion:2.0

<span data-ttu-id="ec327-129">最後，如果您使用不支援的欄位 (例如 'commands')，則只會略過它，並搜尋所有欄位。</span><span class="sxs-lookup"><span data-stu-id="ec327-129">Finally, if you use a field we don't support, such as 'commands', we'll just ignore it and search all the fields.</span></span> <span data-ttu-id="ec327-130">因此，下列查詢</span><span class="sxs-lookup"><span data-stu-id="ec327-130">So the following query</span></span>

    commands:blobs storage

<span data-ttu-id="ec327-131">會解譯成與這個查詢完全相同︰</span><span class="sxs-lookup"><span data-stu-id="ec327-131">Is interpreted exactly the same as this query:</span></span>

    blobs storage
