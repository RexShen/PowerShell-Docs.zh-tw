---
ms.openlocfilehash: 61a70db9ae7a38d6731f1cefb011072c12d1e39a
ms.sourcegitcommit: 077488408c820c860131382324bdd576d0edf52a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95514913"
---
# <a name="microsoft-open-source-code-of-conduct"></a><span data-ttu-id="520af-101">Microsoft 開放原始碼管理辦法</span><span class="sxs-lookup"><span data-stu-id="520af-101">Microsoft Open Source Code of Conduct</span></span>

> <span data-ttu-id="520af-102">更新日期：2020/11/02</span><span class="sxs-lookup"><span data-stu-id="520af-102">Updated: 11/02/2020</span></span>

<span data-ttu-id="520af-103">此專案採用了 [Microsoft 開放原始碼管理辦法](https://opensource.microsoft.com/codeofconduct/)。</span><span class="sxs-lookup"><span data-stu-id="520af-103">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span> <span data-ttu-id="520af-104">如需詳細資訊，請參閱[管理辦法常見問題集 (英文)](https://opensource.microsoft.com/codeofconduct/faq/)。如果有任何其他疑問或意見，請連絡 [opencode@microsoft.com](mailto:opencode@microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="520af-104">For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>

[即時徽章]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=live
[live-badge]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=live
[預備徽章]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=staging
[staging-badge]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=staging

## <a name="build-status"></a><span data-ttu-id="520af-107">組建狀態</span><span class="sxs-lookup"><span data-stu-id="520af-107">Build Status</span></span>

|          <span data-ttu-id="520af-108">即時分支</span><span class="sxs-lookup"><span data-stu-id="520af-108">Live Branch</span></span>          |           <span data-ttu-id="520af-109">預備分支</span><span class="sxs-lookup"><span data-stu-id="520af-109">Staging Branch</span></span>            |
| :---------------------------- | :---------------------------------- |
| <span data-ttu-id="520af-110">[![即時徽章][]][即時徽章]</span><span class="sxs-lookup"><span data-stu-id="520af-110">[![live-badge][]][live-badge]</span></span> | <span data-ttu-id="520af-111">[![預備徽章][]][預備徽章]</span><span class="sxs-lookup"><span data-stu-id="520af-111">[![staging-badge][]][staging-badge]</span></span> |

## <a name="powershell-documentation"></a><span data-ttu-id="520af-112">PowerShell 文件</span><span class="sxs-lookup"><span data-stu-id="520af-112">PowerShell Documentation</span></span>

<span data-ttu-id="520af-113">歡迎使用 PowerShell-Docs 存放庫，此處為正式 PowerShell 文件的首頁。</span><span class="sxs-lookup"><span data-stu-id="520af-113">Welcome to the PowerShell-Docs repository, the home of the official PowerShell documentation.</span></span>

## <a name="repository-structure"></a><span data-ttu-id="520af-114">存放庫結構</span><span class="sxs-lookup"><span data-stu-id="520af-114">Repository Structure</span></span>

<span data-ttu-id="520af-115">下列清單描述此存放庫中的主要資料夾。</span><span class="sxs-lookup"><span data-stu-id="520af-115">The following list describes the main folders in this repository.</span></span>

- <span data-ttu-id="520af-116">`.github` - 包含 GitHub 在此存放庫所使用的組態</span><span class="sxs-lookup"><span data-stu-id="520af-116">`.github` - contains configuration settings used by GitHub for this repository</span></span>
- <span data-ttu-id="520af-117">`.vscode` - 包含 Visual Studio Code (VS Code) 的組態設定與建議延伸模組</span><span class="sxs-lookup"><span data-stu-id="520af-117">`.vscode` - contains configuration settings and recommended extensions for Visual Studio Code (VS Code)</span></span>
- <span data-ttu-id="520af-118">`assets` - 包含本文件中連結的可下載檔案</span><span class="sxs-lookup"><span data-stu-id="520af-118">`assets` - contains downloadable files linked in the documentation</span></span>
- <span data-ttu-id="520af-119">`reference` - 包含發佈至 [docs.microsoft.com]([https://docs.microsoft.com/powershell/scripting/) 的文件。</span><span class="sxs-lookup"><span data-stu-id="520af-119">`reference` - contains the documentation published to [docs.microsoft.com]([https://docs.microsoft.com/powershell/scripting/).</span></span> <span data-ttu-id="520af-120">包含參考與概念內容。</span><span class="sxs-lookup"><span data-stu-id="520af-120">This includes both reference and conceptual content.</span></span>
  - <span data-ttu-id="520af-121">`5.1` - 包含 Cmdlet 參考與 PowerShell 5.1 的相關主題</span><span class="sxs-lookup"><span data-stu-id="520af-121">`5.1` - contains the cmdlet reference and about topics for PowerShell 5.1</span></span>
  - <span data-ttu-id="520af-122">`7.0` - 包含 Cmdlet 參考與 PowerShell 7.0 的相關主題</span><span class="sxs-lookup"><span data-stu-id="520af-122">`7.0` - contains the cmdlet reference and about topics for PowerShell 7.0</span></span>
  - <span data-ttu-id="520af-123">`7.1` - 包含 Cmdlet 參考與 PowerShell 7.1 的相關主題</span><span class="sxs-lookup"><span data-stu-id="520af-123">`7.1` - contains the cmdlet reference and about topics for PowerShell 7.1</span></span>
  - <span data-ttu-id="520af-124">`7.2` - 包含適用於 PowerShell 7.2 (預覽) 的 Cmdlet 參考與關於主題</span><span class="sxs-lookup"><span data-stu-id="520af-124">`7.2` - contains the cmdlet reference and about topics for PowerShell 7.2 (preview)</span></span>
  - <span data-ttu-id="520af-125">`bread` - 包含用於軌跡瀏覽的目錄</span><span class="sxs-lookup"><span data-stu-id="520af-125">`bread` - contains the TOC used for breadcrumb navigation</span></span>
  - <span data-ttu-id="520af-126">`docs-conceptual` - 包含發佈至 Docs 網站的概念文章。</span><span class="sxs-lookup"><span data-stu-id="520af-126">`docs-conceptual` - contains the conceptual articles that are published to the Docs site.</span></span> <span data-ttu-id="520af-127">一般而言，資料夾結構會建立鏡像目錄 (TOC)。</span><span class="sxs-lookup"><span data-stu-id="520af-127">In general, the folder structure mirrors the Table of Contents (TOC).</span></span>
  - <span data-ttu-id="520af-128">`mapping` - 包含建置系統所使用的版本對應組態</span><span class="sxs-lookup"><span data-stu-id="520af-128">`mapping` - contains the version mapping configuration used by the build system</span></span>
  - <span data-ttu-id="520af-129">`media` - 包含文件中所使用的影像檔案。</span><span class="sxs-lookup"><span data-stu-id="520af-129">`media` - contains image files used in documentation.</span></span> <span data-ttu-id="520af-130">`docs-conceptual` 內容中包含媒體資料夾。</span><span class="sxs-lookup"><span data-stu-id="520af-130">There are media folders throughout the `docs-conceptual` content.</span></span> <span data-ttu-id="520af-131">如需在文件中使用影像的詳細資訊，請參閱參與者指南。</span><span class="sxs-lookup"><span data-stu-id="520af-131">See the Contributor Guide for information on using images in documentation.</span></span>
  - <span data-ttu-id="520af-132">`module` - 包含 [模組瀏覽器] 頁面的 Markdown 來源</span><span class="sxs-lookup"><span data-stu-id="520af-132">`module` - contains the markdown source for the Module Browser page</span></span>
- <span data-ttu-id="520af-133">`tests` - 包含建置系統所使用的 Pester 測試</span><span class="sxs-lookup"><span data-stu-id="520af-133">`tests` - contains the Pester tests used by the build system</span></span>
- <span data-ttu-id="520af-134">`tools` - 包含建置系統所使用的其他工具</span><span class="sxs-lookup"><span data-stu-id="520af-134">`tools` - contains other tools used by the build system</span></span>

> <span data-ttu-id="520af-135">注意：(在編號資料夾中的) 參考內容是用來在 Docs 網站上建立網頁，以及 PowerShell 所使用的可更新說明。</span><span class="sxs-lookup"><span data-stu-id="520af-135">NOTE: The reference content (in the numbered folders) is used to create the webpages on the Docs site as well as the updateable help used by PowerShell.</span></span>
> <span data-ttu-id="520af-136">`docs-conceptual` 資料夾中的文章只會發佈到 Docs 網站。</span><span class="sxs-lookup"><span data-stu-id="520af-136">The articles in the `docs-conceptual` folder are only published to the Docs website.</span></span>

## <a name="contributing"></a><span data-ttu-id="520af-137">參與</span><span class="sxs-lookup"><span data-stu-id="520af-137">Contributing</span></span>

<span data-ttu-id="520af-138">我們歡迎透過[提取要求](https://help.github.com/articles/using-pull-requests/)，投稿至存放庫的「暫存」分支中。</span><span class="sxs-lookup"><span data-stu-id="520af-138">We welcome public contributions into this repository via [pull requests](https://help.github.com/articles/using-pull-requests/) into the _staging_ branch.</span></span>
<span data-ttu-id="520af-139">請注意，您必須先同意[貢獻授權合約](https://cla.microsoft.com/)，我們才會接受您的提取要求。</span><span class="sxs-lookup"><span data-stu-id="520af-139">Please note that before we can accept your pull request you must sign our [Contribution License Agreement](https://cla.microsoft.com/).</span></span> <span data-ttu-id="520af-140">這只需要執行一次。</span><span class="sxs-lookup"><span data-stu-id="520af-140">This is a one-time requirement.</span></span>

<span data-ttu-id="520af-141">如需如何參與的詳細資訊，請閱讀我們的[參與者指南](https://aka.ms/PSDocsContributor)。</span><span class="sxs-lookup"><span data-stu-id="520af-141">For more information on contributing, read our [contributor's guide](https://aka.ms/PSDocsContributor).</span></span> <span data-ttu-id="520af-142">參與者指南包含有關如何參與文件、建議工具與樣式和格式需求的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="520af-142">The contributor's guide contains detail information about how to contribute documentation, suggested tools, and style and formatting requirements.</span></span> <span data-ttu-id="520af-143">請使用「問題」和「提取要求」範本，以協助維持文件在不同版本之間的一致性。</span><span class="sxs-lookup"><span data-stu-id="520af-143">Please use the Issue and Pull Request templates to help keep documentation consistent across versions.</span></span>

## <a name="licenses"></a><span data-ttu-id="520af-144">授權</span><span class="sxs-lookup"><span data-stu-id="520af-144">Licenses</span></span>

<span data-ttu-id="520af-145">此專案有兩個授權檔案。</span><span class="sxs-lookup"><span data-stu-id="520af-145">There are two license files for this project.</span></span> <span data-ttu-id="520af-146">MIT 授權適用於此存放庫中包含的程式碼。</span><span class="sxs-lookup"><span data-stu-id="520af-146">The MIT License applies to the code contained in this repo.</span></span> <span data-ttu-id="520af-147">而 Creative Commons 授權則適用於文件。</span><span class="sxs-lookup"><span data-stu-id="520af-147">The Creative Commons license applies to the documentation.</span></span>
