---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 組件庫搜尋語法
ms.openlocfilehash: 9eaabc22090655076dabe177f04130738e081179
ms.sourcegitcommit: d757d64ea8c8af4d92596e8fbe15f2f40d48d3ac
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90846995"
---
# <a name="gallery-search-syntax"></a><span data-ttu-id="25a10-103">組件庫搜尋語法</span><span class="sxs-lookup"><span data-stu-id="25a10-103">Gallery Search Syntax</span></span>

<span data-ttu-id="25a10-104">您可以使用 [PowerShell 資源庫的網站](https://www.powershellgallery.com/) \(英文\) 來搜尋 PowerShell 資源庫。</span><span class="sxs-lookup"><span data-stu-id="25a10-104">You can search the PowerShell Gallery using the [PowerShell Gallery's web site](https://www.powershellgallery.com/).</span></span> <span data-ttu-id="25a10-105">PowerShell 資源庫網站提供文字搜尋方塊，讓您可以使用字組、片語和關鍵字運算式來縮小搜尋結果範圍。</span><span class="sxs-lookup"><span data-stu-id="25a10-105">PowerShell Gallery web site offers a text searchbox where you can use words, phrases and keyword expressions to narrow down search results.</span></span>

## <a name="search-by-keywords"></a><span data-ttu-id="25a10-106">依關鍵字搜尋</span><span class="sxs-lookup"><span data-stu-id="25a10-106">Search by Keywords</span></span>

```Syntax
dsc azure sql
```

<span data-ttu-id="25a10-107">搜尋會嘗試尋找包含所有 3 個關鍵字的相關文件，並傳回相符文件。</span><span class="sxs-lookup"><span data-stu-id="25a10-107">Search attempts to find relevant documents containing all 3 keywords, and return matching documents.</span></span>

## <a name="search-using-phrases-and-keywords"></a><span data-ttu-id="25a10-108">使用片語和關鍵字搜尋</span><span class="sxs-lookup"><span data-stu-id="25a10-108">Search using Phrases and keywords</span></span>

```Syntax
"azure sql" deployment
```

<span data-ttu-id="25a10-109">輸入加上引號 ("") 的片語，會變更搜尋以尋找特定片語，而非個別關鍵字。</span><span class="sxs-lookup"><span data-stu-id="25a10-109">Entering a phrase between quotation marks ("") change the search to look for the particular phrase instead of separate keywords.</span></span> <span data-ttu-id="25a10-110">相符文件通常應該會包含精確片語 "azure sql" (包含大寫變化，例如"Azure SQL")，通常也會包含 'deployment' 這個字。</span><span class="sxs-lookup"><span data-stu-id="25a10-110">Matching documents should usually contain the exact phrase "azure sql", including variations on capitalization e.g. "Azure SQL", and also usually contain the word 'deployment'.</span></span>

## <a name="filtering-on-fields"></a><span data-ttu-id="25a10-111">根據欄位進行篩選</span><span class="sxs-lookup"><span data-stu-id="25a10-111">Filtering on fields</span></span>

<span data-ttu-id="25a10-112">您可以搜尋特定套件識別碼 (或者 'Id' 或 'id')，或在搜尋詞彙前面加上欄位名稱來搜尋特定其他欄位。</span><span class="sxs-lookup"><span data-stu-id="25a10-112">You can search for a specific package ID (or 'Id' or 'id'), or certain other fields by prefixing search terms with the field name.</span></span>

<span data-ttu-id="25a10-113">可搜尋的欄位目前是 'Id'、'Version'、'Tags'、'Author'、'Owner'、'Functions'、'Cmdlets'、'DscResources' 和 'PowerShellVersion'。</span><span class="sxs-lookup"><span data-stu-id="25a10-113">Currently the searchable fields are 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' and 'PowerShellVersion'.</span></span>

- <span data-ttu-id="25a10-114">識別碼是您在主控台中使用的名稱。</span><span class="sxs-lookup"><span data-stu-id="25a10-114">ID is the name you use in the console.</span></span>
- <span data-ttu-id="25a10-115">標題是搜尋結果中套件頁面頂端所顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="25a10-115">Title is what is shown at the top of the package page in search results.</span></span>

## <a name="examples"></a><span data-ttu-id="25a10-116">範例</span><span class="sxs-lookup"><span data-stu-id="25a10-116">Examples</span></span>

```Syntax
ID:PSReadline
```

<span data-ttu-id="25a10-117">尋找識別碼包含 "PSReadline" 的套件。</span><span class="sxs-lookup"><span data-stu-id="25a10-117">finds packages with an ID containing "PSReadline".</span></span>

```Syntax
Id:"AzureRM.Profile"
```

<span data-ttu-id="25a10-118">是尋找 [識別碼] 欄位中有 "AzureRM.Profile" 之套件的另一種方式。</span><span class="sxs-lookup"><span data-stu-id="25a10-118">is another way to find packages with "AzureRM.Profile" in their ID field.</span></span>

<span data-ttu-id="25a10-119">'Id' 篩選是子字串比對，因此，如果您搜尋下列項目︰</span><span class="sxs-lookup"><span data-stu-id="25a10-119">The 'Id' filter is a substring match, so if you search for the following:</span></span>

```Syntax
Id:"azure"
```

<span data-ttu-id="25a10-120">這會提供包含 'AzureRM.Profile' 和 'Azure.Storage' 的結果。</span><span class="sxs-lookup"><span data-stu-id="25a10-120">This provides results that include AzureRM.Profile' and 'Azure.Storage'.</span></span>

<span data-ttu-id="25a10-121">您也可以在單一欄位中搜尋多個關鍵字。</span><span class="sxs-lookup"><span data-stu-id="25a10-121">You can also search for multiple keywords in a single field.</span></span>

```Syntax
id:azure tags:intellisense
```

<span data-ttu-id="25a10-122">而且，您可以使用雙引號來執行片語搜尋：</span><span class="sxs-lookup"><span data-stu-id="25a10-122">And you can perform phrase searches using double quotes:</span></span>

```Syntax
id:"azure.storage"
```

<span data-ttu-id="25a10-123">使用 DSC 標記搜尋所有套件。</span><span class="sxs-lookup"><span data-stu-id="25a10-123">To search all packages with DSC tag.</span></span>

```Syntax
Tags:DSC
```

<span data-ttu-id="25a10-124">使用指定的函數搜尋所有套件。</span><span class="sxs-lookup"><span data-stu-id="25a10-124">To search all packages with the specified function.</span></span>

```Syntax
Functions:Get-TreeSize
```

<span data-ttu-id="25a10-125">使用指定的 Cmdlet 搜尋所有套件。</span><span class="sxs-lookup"><span data-stu-id="25a10-125">To search all packages with the specified cmdlet.</span></span>

```Syntax
Cmdlets:Get-AzureRmEnvironment
```

<span data-ttu-id="25a10-126">使用指定的「DSC 資源」名稱搜尋所有套件。</span><span class="sxs-lookup"><span data-stu-id="25a10-126">To search all packages with the specified DSC Resource name.</span></span>

```Syntax
DscResources:xArchive
```

<span data-ttu-id="25a10-127">使用指定的 PowerShellVersion 搜尋所有套件</span><span class="sxs-lookup"><span data-stu-id="25a10-127">To search all packages with the specified PowerShellVersion</span></span>

```Syntax
PowerShellVersion:2.0
```

<span data-ttu-id="25a10-128">最後，如果您使用不支援的欄位 (例如 'commands')，則只會略過它，並搜尋所有欄位。</span><span class="sxs-lookup"><span data-stu-id="25a10-128">Finally, if you use a field we don't support, such as 'commands', we'll just ignore it and search all the fields.</span></span> <span data-ttu-id="25a10-129">因此，下列查詢</span><span class="sxs-lookup"><span data-stu-id="25a10-129">So the following query</span></span>

```Syntax
commands:blobs storage
```

<span data-ttu-id="25a10-130">會解譯成與這個查詢完全相同︰</span><span class="sxs-lookup"><span data-stu-id="25a10-130">Is interpreted exactly the same as this query:</span></span>

```Syntax
blobs storage
```
