---
ms.openlocfilehash: f46b14e44c32ce31b4da1a14580fe03564bf9946
ms.sourcegitcommit: 0e18be0a2869beaa711ba3eca7a8a15514e5e962
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2020
ms.locfileid: "91899263"
---
# <a name="microsoft-open-source-code-of-conduct"></a><span data-ttu-id="a0ddb-101">Microsoft 開放原始碼管理辦法</span><span class="sxs-lookup"><span data-stu-id="a0ddb-101">Microsoft Open Source Code of Conduct</span></span>

<span data-ttu-id="a0ddb-102">此專案採用了 [Microsoft 開放原始碼管理辦法](https://opensource.microsoft.com/codeofconduct/)。</span><span class="sxs-lookup"><span data-stu-id="a0ddb-102">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span> <span data-ttu-id="a0ddb-103">如需詳細資訊，請參閱[管理辦法常見問題集 (英文)](https://opensource.microsoft.com/codeofconduct/faq/)。如果有任何其他疑問或意見，請連絡 [opencode@microsoft.com](mailto:opencode@microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="a0ddb-103">For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>

[即時徽章]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=live
[live-badge]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=live
[預備徽章]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=staging
[staging-badge]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=staging

## <a name="build-status"></a><span data-ttu-id="a0ddb-106">組建狀態</span><span class="sxs-lookup"><span data-stu-id="a0ddb-106">Build Status</span></span>

|          <span data-ttu-id="a0ddb-107">即時分支</span><span class="sxs-lookup"><span data-stu-id="a0ddb-107">Live Branch</span></span>          |           <span data-ttu-id="a0ddb-108">預備分支</span><span class="sxs-lookup"><span data-stu-id="a0ddb-108">Staging Branch</span></span>            |
| :---------------------------- | :---------------------------------- |
| <span data-ttu-id="a0ddb-109">[![即時徽章][]][即時徽章]</span><span class="sxs-lookup"><span data-stu-id="a0ddb-109">[![live-badge][]][live-badge]</span></span> | <span data-ttu-id="a0ddb-110">[![預備徽章][]][預備徽章]</span><span class="sxs-lookup"><span data-stu-id="a0ddb-110">[![staging-badge][]][staging-badge]</span></span> |

## <a name="powershell-documentation"></a><span data-ttu-id="a0ddb-111">PowerShell 文件</span><span class="sxs-lookup"><span data-stu-id="a0ddb-111">PowerShell Documentation</span></span>

<span data-ttu-id="a0ddb-112">歡迎使用 PowerShell-Docs 存放庫，此處為正式 PowerShell 文件的首頁。</span><span class="sxs-lookup"><span data-stu-id="a0ddb-112">Welcome to the PowerShell-Docs repository, the home of the official PowerShell documentation.</span></span>

## <a name="repository-structure"></a><span data-ttu-id="a0ddb-113">存放庫結構</span><span class="sxs-lookup"><span data-stu-id="a0ddb-113">Repository Structure</span></span>

<span data-ttu-id="a0ddb-114">下列清單描述此存放庫中的主要資料夾。</span><span class="sxs-lookup"><span data-stu-id="a0ddb-114">The following list describes the main folders in this repository.</span></span>

- <span data-ttu-id="a0ddb-115">`.github` - 包含 GitHub 在此存放庫所使用的組態</span><span class="sxs-lookup"><span data-stu-id="a0ddb-115">`.github` - contains configuration settings used by GitHub for this repository</span></span>
- <span data-ttu-id="a0ddb-116">`.vscode` - 包含 Visual Studio Code (VS Code) 的組態設定與建議延伸模組</span><span class="sxs-lookup"><span data-stu-id="a0ddb-116">`.vscode` - contains configuration settings and recommended extensions for Visual Studio Code (VS Code)</span></span>
- <span data-ttu-id="a0ddb-117">`assets` - 包含本文件中連結的可下載檔案</span><span class="sxs-lookup"><span data-stu-id="a0ddb-117">`assets` - contains downloadable files linked in the documentation</span></span>
- <span data-ttu-id="a0ddb-118">`reference` - 包含發佈至 [docs.microsoft.com]([https://docs.microsoft.com/powershell/scripting/) 的文件。</span><span class="sxs-lookup"><span data-stu-id="a0ddb-118">`reference` - contains the documentation published to [docs.microsoft.com]([https://docs.microsoft.com/powershell/scripting/).</span></span> <span data-ttu-id="a0ddb-119">包含參考與概念內容。</span><span class="sxs-lookup"><span data-stu-id="a0ddb-119">This includes both reference and conceptual content.</span></span>
  - <span data-ttu-id="a0ddb-120">`5.1` - 包含 Cmdlet 參考與 PowerShell 5.1 的相關主題</span><span class="sxs-lookup"><span data-stu-id="a0ddb-120">`5.1` - contains the cmdlet reference and about topics for PowerShell 5.1</span></span>
  - <span data-ttu-id="a0ddb-121">`6` - 包含 Cmdlet 參考與 PowerShell 6 的相關主題</span><span class="sxs-lookup"><span data-stu-id="a0ddb-121">`6` - contains the cmdlet reference and about topics for PowerShell 6</span></span>
  - <span data-ttu-id="a0ddb-122">`7.0` - 包含 Cmdlet 參考與 PowerShell 7.0 的相關主題</span><span class="sxs-lookup"><span data-stu-id="a0ddb-122">`7.0` - contains the cmdlet reference and about topics for PowerShell 7.0</span></span>
  - <span data-ttu-id="a0ddb-123">`7.1` - 包含 Cmdlet 參考與 PowerShell 7.1 的相關主題</span><span class="sxs-lookup"><span data-stu-id="a0ddb-123">`7.1` - contains the cmdlet reference and about topics for PowerShell 7.1</span></span>
  - <span data-ttu-id="a0ddb-124">`bread` - 包含用於軌跡瀏覽的目錄</span><span class="sxs-lookup"><span data-stu-id="a0ddb-124">`bread` - contains the TOC used for breadcrumb navigation</span></span>
  - <span data-ttu-id="a0ddb-125">`docs-conceptual` - 包含發佈至 Docs 網站的概念文章。</span><span class="sxs-lookup"><span data-stu-id="a0ddb-125">`docs-conceptual` - contains the conceptual articles that are published to the Docs site.</span></span> <span data-ttu-id="a0ddb-126">一般而言，資料夾結構會建立鏡像目錄 (TOC)。</span><span class="sxs-lookup"><span data-stu-id="a0ddb-126">In general, the folder structure mirrors the Table of Contents (TOC).</span></span>
  - <span data-ttu-id="a0ddb-127">`mapping` - 包含建置系統所使用的版本對應組態</span><span class="sxs-lookup"><span data-stu-id="a0ddb-127">`mapping` - contains the version mapping configuration used by the build system</span></span>
  - <span data-ttu-id="a0ddb-128">`media` - 包含文件中所使用的影像檔案。</span><span class="sxs-lookup"><span data-stu-id="a0ddb-128">`media` - contains image files used in documentation.</span></span> <span data-ttu-id="a0ddb-129">`docs-conceptual` 內容中包含媒體資料夾。</span><span class="sxs-lookup"><span data-stu-id="a0ddb-129">There are media folders throughout the `docs-conceptual` content.</span></span> <span data-ttu-id="a0ddb-130">如需在文件中使用影像的詳細資訊，請參閱參與者指南。</span><span class="sxs-lookup"><span data-stu-id="a0ddb-130">See the Contributor Guide for information on using images in documentation.</span></span>
  - <span data-ttu-id="a0ddb-131">`module` - 包含 [模組瀏覽器] 頁面的 Markdown 來源</span><span class="sxs-lookup"><span data-stu-id="a0ddb-131">`module` - contains the markdown source for the Module Browser page</span></span>
- <span data-ttu-id="a0ddb-132">`tests` - 包含建置系統所使用的 Pester 測試</span><span class="sxs-lookup"><span data-stu-id="a0ddb-132">`tests` - contains the Pester tests used by the build system</span></span>
- <span data-ttu-id="a0ddb-133">`tools` - 包含建置系統所使用的其他工具</span><span class="sxs-lookup"><span data-stu-id="a0ddb-133">`tools` - contains other tools used by the build system</span></span>

> <span data-ttu-id="a0ddb-134">注意：(在編號資料夾中的) 參考內容是用來在 Docs 網站上建立網頁，以及 PowerShell 所使用的可更新說明。</span><span class="sxs-lookup"><span data-stu-id="a0ddb-134">NOTE: The reference content (in the numbered folders) is used to create the webpages on the Docs site as well as the updateable help used by PowerShell.</span></span>
> <span data-ttu-id="a0ddb-135">`docs-conceptual` 資料夾中的文章只會發佈到 Docs 網站。</span><span class="sxs-lookup"><span data-stu-id="a0ddb-135">The articles in the `docs-conceptual` folder are only published to the Docs website.</span></span>

## <a name="contributing"></a><span data-ttu-id="a0ddb-136">參與</span><span class="sxs-lookup"><span data-stu-id="a0ddb-136">Contributing</span></span>

<span data-ttu-id="a0ddb-137">我們歡迎透過[提取要求](https://help.github.com/articles/using-pull-requests/)，投稿至存放庫的「暫存」分支中。</span><span class="sxs-lookup"><span data-stu-id="a0ddb-137">We welcome public contributions into this repository via [pull requests](https://help.github.com/articles/using-pull-requests/) into the _staging_ branch.</span></span>
<span data-ttu-id="a0ddb-138">請注意，您必須先同意[貢獻授權合約](https://cla.microsoft.com/)，我們才會接受您的提取要求。</span><span class="sxs-lookup"><span data-stu-id="a0ddb-138">Please note that before we can accept your pull request you must sign our [Contribution License Agreement](https://cla.microsoft.com/).</span></span> <span data-ttu-id="a0ddb-139">這只需要執行一次。</span><span class="sxs-lookup"><span data-stu-id="a0ddb-139">This is a one-time requirement.</span></span>

<span data-ttu-id="a0ddb-140">如需如何參與的詳細資訊，請閱讀我們的[參與者指南](https://aka.ms/PSDocsContributor)。</span><span class="sxs-lookup"><span data-stu-id="a0ddb-140">For more information on contributing, read our [contributor's guide](https://aka.ms/PSDocsContributor).</span></span> <span data-ttu-id="a0ddb-141">參與者指南包含有關如何參與文件、建議工具與樣式和格式需求的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="a0ddb-141">The contributor's guide contains detail information about how to contribute documentation, suggested tools, and style and formatting requirements.</span></span> <span data-ttu-id="a0ddb-142">請使用「問題」和「提取要求」範本，以協助維持文件在不同版本之間的一致性。</span><span class="sxs-lookup"><span data-stu-id="a0ddb-142">Please use the Issue and Pull Request templates to help keep documentation consistent across versions.</span></span>

## <a name="licenses"></a><span data-ttu-id="a0ddb-143">授權</span><span class="sxs-lookup"><span data-stu-id="a0ddb-143">Licenses</span></span>

<span data-ttu-id="a0ddb-144">此專案有兩個授權檔案。</span><span class="sxs-lookup"><span data-stu-id="a0ddb-144">There are two license files for this project.</span></span> <span data-ttu-id="a0ddb-145">MIT 授權適用於此存放庫中包含的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a0ddb-145">The MIT License applies to the code contained in this repo.</span></span> <span data-ttu-id="a0ddb-146">而 Creative Commons 授權則適用於文件。</span><span class="sxs-lookup"><span data-stu-id="a0ddb-146">The Creative Commons license applies to the documentation.</span></span>
