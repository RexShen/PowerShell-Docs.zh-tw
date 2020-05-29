---
ms.openlocfilehash: 0d91230aa063e58106b35a4ada1d577f316f8f27
ms.sourcegitcommit: c752ae8d0fa47eaaf3c5eae2a5a770f06c63921c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/26/2020
ms.locfileid: "83840989"
---
# <a name="microsoft-open-source-code-of-conduct"></a><span data-ttu-id="70b33-101">Microsoft 開放原始碼管理辦法</span><span class="sxs-lookup"><span data-stu-id="70b33-101">Microsoft Open Source Code of Conduct</span></span>

<span data-ttu-id="70b33-102">此專案採用了 [Microsoft 開放原始碼管理辦法](https://opensource.microsoft.com/codeofconduct/)。</span><span class="sxs-lookup"><span data-stu-id="70b33-102">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span> <span data-ttu-id="70b33-103">如需詳細資訊，請參閱[管理辦法常見問題集 (英文)](https://opensource.microsoft.com/codeofconduct/faq/)。如果有任何其他疑問或意見，請連絡 [opencode@microsoft.com](mailto:opencode@microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="70b33-103">For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>

[即時徽章]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=live
[live-badge]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=live
[預備徽章]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=staging
[staging-badge]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=staging

## <a name="build-status"></a><span data-ttu-id="70b33-106">組建狀態</span><span class="sxs-lookup"><span data-stu-id="70b33-106">Build Status</span></span>

|          <span data-ttu-id="70b33-107">即時分支</span><span class="sxs-lookup"><span data-stu-id="70b33-107">Live Branch</span></span>          |           <span data-ttu-id="70b33-108">預備分支</span><span class="sxs-lookup"><span data-stu-id="70b33-108">Staging Branch</span></span>            |
| :---------------------------- | :---------------------------------- |
| <span data-ttu-id="70b33-109">[![即時徽章][]][即時徽章]</span><span class="sxs-lookup"><span data-stu-id="70b33-109">[![live-badge][]][live-badge]</span></span> | <span data-ttu-id="70b33-110">[![預備徽章][]][預備徽章]</span><span class="sxs-lookup"><span data-stu-id="70b33-110">[![staging-badge][]][staging-badge]</span></span> |

## <a name="powershell-documentation"></a><span data-ttu-id="70b33-111">PowerShell 文件</span><span class="sxs-lookup"><span data-stu-id="70b33-111">PowerShell Documentation</span></span>

<span data-ttu-id="70b33-112">歡迎使用裝載正式 PowerShell 文件的 PowerShell-Docs 存放庫。</span><span class="sxs-lookup"><span data-stu-id="70b33-112">Welcome to the PowerShell-Docs repository, housing the official PowerShell documentation.</span></span>

## <a name="repository-structure"></a><span data-ttu-id="70b33-113">存放庫結構</span><span class="sxs-lookup"><span data-stu-id="70b33-113">Repository Structure</span></span>

<span data-ttu-id="70b33-114">此存放庫中每個下列頂層資料夾都包含發行到 [Microsoft Docs](https://docs.microsoft.com/powershell) 的 DocSet。</span><span class="sxs-lookup"><span data-stu-id="70b33-114">Each of the following top-level folders in this repo contain a DocSet that is published to [Microsoft Docs](https://docs.microsoft.com/powershell).</span></span>

- <span data-ttu-id="70b33-115">[/reference/](https://docs.microsoft.com/powershell/scripting/) 適用於 5.1、6.0 與 7.0 版的 PowerShell 概念性主題與模組參考。</span><span class="sxs-lookup"><span data-stu-id="70b33-115">[/reference/](https://docs.microsoft.com/powershell/scripting/) is for PowerShell conceptual topics and module reference across versions 5.1, 6.0, and 7.0.</span></span> <span data-ttu-id="70b33-116">此內容也是 `Get-Help` Cmdlet 擷取說明內容的來源。</span><span class="sxs-lookup"><span data-stu-id="70b33-116">This content is also the source of help content retrieved by the `Get-Help` cmdlet.</span></span>
  - <span data-ttu-id="70b33-117">[docs-conceptual/](https://docs.microsoft.com/powershell) - 此資料夾包含概念性文件及下列文件集：</span><span class="sxs-lookup"><span data-stu-id="70b33-117">[docs-conceptual/](https://docs.microsoft.com/powershell) - this folder contains the conceptual documentation and the following docsets:</span></span>
    - <span data-ttu-id="70b33-118">[developer/](https://docs.microsoft.com/powershell/scripting/developer/) 是 PowerShell SDK 文件 (從 MSDN 移轉而來)</span><span class="sxs-lookup"><span data-stu-id="70b33-118">[developer/](https://docs.microsoft.com/powershell/scripting/developer/) is the PowerShell SDK documentation (migrated from MSDN)</span></span>
    - <span data-ttu-id="70b33-119">[dsc/](https://docs.microsoft.com/powershell/scripting/dsc/) 適用於 Desired State Configuration 功能</span><span class="sxs-lookup"><span data-stu-id="70b33-119">[dsc/](https://docs.microsoft.com/powershell/scripting/dsc/) is for the Desired State Configuration feature</span></span>
    - <span data-ttu-id="70b33-120">[gallery/](https://docs.microsoft.com/powershell/scripting/gallery) 適用於 [PowerShell 資源庫](https://www.powershellgallery.com/)</span><span class="sxs-lookup"><span data-stu-id="70b33-120">[gallery/](https://docs.microsoft.com/powershell/scripting/gallery) is for the [PowerShell Gallery](https://www.powershellgallery.com/)</span></span>
    - <span data-ttu-id="70b33-121">[jea/](https://docs.microsoft.com/powershell/scripting/learn/remoting/jea/overview) 適用於 Just Enough Administration 功能</span><span class="sxs-lookup"><span data-stu-id="70b33-121">[jea/](https://docs.microsoft.com/powershell/scripting/learn/remoting/jea/overview) is for the Just Enough Administration feature</span></span>
    - <span data-ttu-id="70b33-122">[wmf/](https://docs.microsoft.com/powershell/scripting/windows-powershell/wmf/overview) 包含 Windows Management Framework 的版本資訊。Windows Management Framework 的功能在將新版的 PowerShell 散發至舊版 Windows 的套件。</span><span class="sxs-lookup"><span data-stu-id="70b33-122">[wmf/](https://docs.microsoft.com/powershell/scripting/windows-powershell/wmf/overview) contains release notes for the Windows Management Framework, the package used to distribute new versions of PowerShell to previous versions of Windows.</span></span>

## <a name="contributing"></a><span data-ttu-id="70b33-123">參與</span><span class="sxs-lookup"><span data-stu-id="70b33-123">Contributing</span></span>

<span data-ttu-id="70b33-124">我們會透過[提取要求](https://help.github.com/articles/using-pull-requests/)，主動將對此存放庫的貢獻，合併到_臨時_分支中。</span><span class="sxs-lookup"><span data-stu-id="70b33-124">We actively merge contributions into this repository via [pull requests](https://help.github.com/articles/using-pull-requests/) into the _staging_ branch.</span></span>
<span data-ttu-id="70b33-125">請注意，提交提取要求之前，請先簽署[貢獻授權合約](https://cla.microsoft.com/)，以確保社群可以自由使用您提交的內容。</span><span class="sxs-lookup"><span data-stu-id="70b33-125">Please note that before you submit a pull request you must sign a [Contribution License Agreement](https://cla.microsoft.com/) to ensure that the community is free to use your submissions.</span></span>

<span data-ttu-id="70b33-126">如需如何參與的詳細資訊，請閱讀我們的[參與者指南](https://docs.microsoft.com/powershell/scripting/community/contributing/overview)。</span><span class="sxs-lookup"><span data-stu-id="70b33-126">For more information on contributing, read our [contributor's guide](https://docs.microsoft.com/powershell/scripting/community/contributing/overview).</span></span>
<span data-ttu-id="70b33-127">參與者指南包含有關如何參與文件、建議工具與樣式和格式需求的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="70b33-127">The contributor's guide contains detail information about how to contribute documentation, suggested tools, and style and formatting requirements.</span></span> <span data-ttu-id="70b33-128">請使用「問題」和「提取要求」範本，以協助維持文件在不同版本之間的一致性。</span><span class="sxs-lookup"><span data-stu-id="70b33-128">Please use the Issue and Pull Request templates to help keep documentation consistent across versions.</span></span>

## <a name="licenses"></a><span data-ttu-id="70b33-129">授權</span><span class="sxs-lookup"><span data-stu-id="70b33-129">Licenses</span></span>

<span data-ttu-id="70b33-130">此專案有兩個授權檔案。</span><span class="sxs-lookup"><span data-stu-id="70b33-130">There are two license files for this project.</span></span> <span data-ttu-id="70b33-131">MIT 授權適用於此存放庫中包含的程式碼。</span><span class="sxs-lookup"><span data-stu-id="70b33-131">The MIT License applies to the code contained in this repo.</span></span> <span data-ttu-id="70b33-132">而 Creative Commons 授權則適用於文件。</span><span class="sxs-lookup"><span data-stu-id="70b33-132">The Creative Commons license applies to the documentation.</span></span>
