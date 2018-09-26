---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,設定
title: 類別目錄 Cmdlet
ms.openlocfilehash: ec5fc866fe27a894b23b93d3ea46ad9c0cba288e
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522883"
---
# <a name="catalog-cmdlets"></a><span data-ttu-id="5a4ed-103">類別目錄 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5a4ed-103">Catalog Cmdlets</span></span>

<span data-ttu-id="5a4ed-104">[Microsoft.Powershell.Secuity](https://technet.microsoft.com/library/hh847877.aspx) 模組中新增了兩個新的 Cmdlet，以產生和驗證 Windows 類別目錄檔案。</span><span class="sxs-lookup"><span data-stu-id="5a4ed-104">We have added two new cmdlets in [Microsoft.Powershell.Secuity](https://technet.microsoft.com/library/hh847877.aspx) module to generate and validate windows catalog files.</span></span>

## <a name="new-filecatalog"></a><span data-ttu-id="5a4ed-105">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="5a4ed-105">New-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="5a4ed-106">`New-FileCatalog` 會為一組資料夾及檔案建立 Windows 類別目錄檔案。</span><span class="sxs-lookup"><span data-stu-id="5a4ed-106">`New-FileCatalog` creates a windows catalog file for set of folders and files.</span></span> <span data-ttu-id="5a4ed-107">類別目錄檔案包含指定路徑中所有檔案的雜湊。</span><span class="sxs-lookup"><span data-stu-id="5a4ed-107">A catalog file contains hashes for all files in specified paths.</span></span> <span data-ttu-id="5a4ed-108">使用者在散發資料夾組時，可以一併散發代表這些資料夾的對應類別目錄檔案。</span><span class="sxs-lookup"><span data-stu-id="5a4ed-108">Users can distribute the set of folders along with corresponding the catalog file that represents those folders.</span></span> <span data-ttu-id="5a4ed-109">內容接收者可以利用類別目錄檔案，驗證資料夾自類別目錄建立之後有無任何變更。</span><span class="sxs-lookup"><span data-stu-id="5a4ed-109">A catalog file can be used by the recipient of content to validate whether any changes were made to the folders after the catalog was created.</span></span>

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
<span data-ttu-id="5a4ed-110">我們支援建立類別目錄第 1 版和第 2 版。</span><span class="sxs-lookup"><span data-stu-id="5a4ed-110">We support creating catalog version 1 and 2.</span></span> <span data-ttu-id="5a4ed-111">第 1 版使用 SHA1 雜湊演算法建立檔案雜湊，第 2 版使用 SHA256。</span><span class="sxs-lookup"><span data-stu-id="5a4ed-111">Version 1 uses SHA1 hashing algorithm to create file hashes and version 2 uses SHA256.</span></span> <span data-ttu-id="5a4ed-112">*Windows Server 2008 R2* 和 *Windows 7* 不支援第 2 版的類別目錄。</span><span class="sxs-lookup"><span data-stu-id="5a4ed-112">Catalog version 2 is not supported on *Windows Server 2008 R2* and *Windows 7*.</span></span> <span data-ttu-id="5a4ed-113">如果使用 *Windows 8*、*Windows Server 2012* 和更新版本的平台，建議使用第 2 版的類別目錄。</span><span class="sxs-lookup"><span data-stu-id="5a4ed-113">It is recommended to use catalog version 2 if using platforms *Windows 8*, *Windows Server 2012* and above.</span></span>

<span data-ttu-id="5a4ed-114">若要在現有的模組使用此命令，請指定 CatalogFilePath 和 Path 變數，以符合模組資訊清單的位置。</span><span class="sxs-lookup"><span data-stu-id="5a4ed-114">To use this command on an existing module, specify the CatalogFilePath and Path variables to match the location of the module manifest.</span></span> <span data-ttu-id="5a4ed-115">下列範例中，模組資訊清單位於 C:\Program Files\Windows PowerShell\Modules\Pester。</span><span class="sxs-lookup"><span data-stu-id="5a4ed-115">In the example below, the module manifest is in C:\Program Files\Windows PowerShell\Modules\Pester.</span></span>

![](../images/NewFileCatalog.jpg)

<span data-ttu-id="5a4ed-116">這會建立類別目錄檔案。</span><span class="sxs-lookup"><span data-stu-id="5a4ed-116">This creates the catalog file.</span></span>

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

<span data-ttu-id="5a4ed-117">為能確認類別目錄檔案 (在上例中為 Pester.cat) 的完整性，應使用 [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) Cmdlet 簽署該檔案。</span><span class="sxs-lookup"><span data-stu-id="5a4ed-117">To verify the integrity of a catalog file (Pester.cat in above exmaple) it should be signed using the [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.</span></span>


## <a name="test-filecatalog"></a><span data-ttu-id="5a4ed-118">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="5a4ed-118">Test-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="5a4ed-119">`Test-FileCatalog` 會驗證代表資料夾組的類別目錄。</span><span class="sxs-lookup"><span data-stu-id="5a4ed-119">`Test-FileCatalog` validates the catalog representing a set of folders.</span></span>

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

<span data-ttu-id="5a4ed-120">此 Cmdlet 會將所有檔案及在類別目錄檔案中找到和其相關之路徑的雜湊，與磁碟上儲存的雜湊進行比較。</span><span class="sxs-lookup"><span data-stu-id="5a4ed-120">This cmdlet compares the hashes of all files and their relative paths found in the catalog file with ones saved to disk.</span></span> <span data-ttu-id="5a4ed-121">若在檔案雜湊與路徑之間偵測到任何不相符，其會傳回狀態 `ValidationFailed`。</span><span class="sxs-lookup"><span data-stu-id="5a4ed-121">If it detects any mismatch between file hashes and paths it returns a status of `ValidationFailed`.</span></span>
<span data-ttu-id="5a4ed-122">使用者可以使用 `Detailed` 參數擷取所有此資訊。</span><span class="sxs-lookup"><span data-stu-id="5a4ed-122">Users can retrieve all this information using the `Detailed` switch.</span></span> <span data-ttu-id="5a4ed-123">和對類別目錄檔案類別目錄呼叫 [Get-authenticodesignature](https://technet.microsoft.com/library/hh849805.aspx) Cmdlet 一樣，類別目錄的簽署狀態也會顯示在 `Signature` 欄位中。</span><span class="sxs-lookup"><span data-stu-id="5a4ed-123">The signing status of the catalog is displayed as the `Signature` field, which is same as calling the [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) cmdlet on the catalog file.</span></span>
<span data-ttu-id="5a4ed-124">使用者也可使用 `FilesToSkip` 參數，在驗證期間跳過任何檔案。</span><span class="sxs-lookup"><span data-stu-id="5a4ed-124">Users can also skip any file during validation by using the `FilesToSkip` parameter.</span></span>
