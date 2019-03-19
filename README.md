---
ms.openlocfilehash: 6e36e6599e36218ce2a925dceda7aa0ee6811057
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "58142205"
---
# <a name="microsoft-open-source-code-of-conduct"></a><span data-ttu-id="7be10-101">Microsoft 開放原始碼管理辦法</span><span class="sxs-lookup"><span data-stu-id="7be10-101">Microsoft Open Source Code of Conduct</span></span>

<span data-ttu-id="7be10-102">本專案已採用 [Microsoft 開放原始碼管理辦法 (英文)](https://opensource.microsoft.com/codeofconduct/)。</span><span class="sxs-lookup"><span data-stu-id="7be10-102">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span>
<span data-ttu-id="7be10-103">如需詳細資訊，請參閱[管理辦法常見問題集 (英文)](https://opensource.microsoft.com/codeofconduct/faq/)。如果有任何其他疑問或意見，請連絡 [opencode@microsoft.com](mailto:opencode@microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="7be10-103">For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>

<span data-ttu-id="7be10-104">[![組建狀態](https://ci.appveyor.com/api/projects/status/onshefxnc4g4pv87/branch/staging?svg=true)](https://ci.appveyor.com/project/PowerShell/powershell-docs/branch/staging)</span><span class="sxs-lookup"><span data-stu-id="7be10-104">[![Build status](https://ci.appveyor.com/api/projects/status/onshefxnc4g4pv87/branch/staging?svg=true)](https://ci.appveyor.com/project/PowerShell/powershell-docs/branch/staging)</span></span>

## <a name="powershell-documentation"></a><span data-ttu-id="7be10-105">PowerShell 文件</span><span class="sxs-lookup"><span data-stu-id="7be10-105">PowerShell Documentation</span></span>

<span data-ttu-id="7be10-106">歡迎使用裝載正式 PowerShell 文件的 PowerShell-Docs 存放庫。</span><span class="sxs-lookup"><span data-stu-id="7be10-106">Welcome to the PowerShell-Docs repository, housing the official PowerShell documentation.</span></span>

## <a name="repository-structure"></a><span data-ttu-id="7be10-107">存放庫結構</span><span class="sxs-lookup"><span data-stu-id="7be10-107">Repository Structure</span></span>

<span data-ttu-id="7be10-108">此存放庫中每個下列頂層資料夾都包含發行到 [Microsoft Docs](https://docs.microsoft.com/powershell) 的 DocSet。</span><span class="sxs-lookup"><span data-stu-id="7be10-108">Each of the following top-level folders in this repo contain a DocSet that is published to [Microsoft Docs](https://docs.microsoft.com/powershell).</span></span>

- <span data-ttu-id="7be10-109">[/developer/](https://docs.microsoft.com/powershell/developer/) 是 PowerShell SDK 文件的未來位置</span><span class="sxs-lookup"><span data-stu-id="7be10-109">[/developer/](https://docs.microsoft.com/powershell/developer/) is the future home of the PowerShell SDK documentation</span></span>
  - <span data-ttu-id="7be10-110">我們正在從 MSDN 移轉此內容</span><span class="sxs-lookup"><span data-stu-id="7be10-110">We are in the process of migrating this content from MSDN</span></span>
- <span data-ttu-id="7be10-111">[/dsc/](https://docs.microsoft.com/powershell/dsc/) 適用於「預期狀態設定」功能</span><span class="sxs-lookup"><span data-stu-id="7be10-111">[/dsc/](https://docs.microsoft.com/powershell/dsc/) is for the Desired State Configuration feature</span></span>
- <span data-ttu-id="7be10-112">[/gallery/](https://docs.microsoft.com/powershell/gallery) 適用於 [PowerShell 資源庫 (英文)](https://www.powershellgallery.com/)</span><span class="sxs-lookup"><span data-stu-id="7be10-112">[/gallery/](https://docs.microsoft.com/powershell/gallery) is for the [PowerShell Gallery](https://www.powershellgallery.com/)</span></span>
- <span data-ttu-id="7be10-113">[/jea/](https://docs.microsoft.com/powershell/jea/) 適用於 Just Enough Administration 功能</span><span class="sxs-lookup"><span data-stu-id="7be10-113">[/jea/](https://docs.microsoft.com/powershell/jea/) is for the Just Enough Administration feature</span></span>
- <span data-ttu-id="7be10-114">[/reference/](https://docs.microsoft.com/powershell/scripting/) 適用於 PowerShell 概念性主題與模組參考，包括 3.0、4.0、5.0、5.1 與 6.0 版</span><span class="sxs-lookup"><span data-stu-id="7be10-114">[/reference/](https://docs.microsoft.com/powershell/scripting/) is for PowerShell conceptual topics and module reference across versions 3.0, 4.0, 5.0, 5.1, and 6.0</span></span>
  - <span data-ttu-id="7be10-115">此內容也是 `Get-Help` Cmdlet 所擷取之說明內容的來源</span><span class="sxs-lookup"><span data-stu-id="7be10-115">This content is also the source of help content retrieved by the `Get-Help` cmdlet</span></span>
- <span data-ttu-id="7be10-116">[/wmf](https://docs.microsoft.com/powershell/wmf/readme) 包含 Windows Management Framework 的版本資訊，這是用來將新的 PowerShell 版本發佈至舊版 Windows 的套件。</span><span class="sxs-lookup"><span data-stu-id="7be10-116">[/wmf](https://docs.microsoft.com/powershell/wmf/readme) contains release notes for the Windows Management Framework, the package used to distribute new versions of PowerShell to previous versions of Windows.</span></span>

## <a name="contributing"></a><span data-ttu-id="7be10-117">貢獻</span><span class="sxs-lookup"><span data-stu-id="7be10-117">Contributing</span></span>

<span data-ttu-id="7be10-118">我們透過[提取要求](https://help.github.com/articles/using-pull-requests/)到「預備」分支，主動將貢獻合併到此存放庫。</span><span class="sxs-lookup"><span data-stu-id="7be10-118">We actively merge contributions into this repository via [pull request](https://help.github.com/articles/using-pull-requests/) into the *staging* branch.</span></span>
<span data-ttu-id="7be10-119">請注意，您提交提取要求之前，必須先[簽署貢獻授權合約](https://cla.microsoft.com/)，以確保社群可以自由使用您提出的內容。</span><span class="sxs-lookup"><span data-stu-id="7be10-119">Please note that before you submit a pull request you must [sign a Contribution License Agreement](https://cla.microsoft.com/) to ensure that the community is free to use your submissions.</span></span>

<span data-ttu-id="7be10-120">如需如何參與的詳細資訊，請閱讀我們的[參與者指南](CONTRIBUTING.md)。</span><span class="sxs-lookup"><span data-stu-id="7be10-120">For more information on contributing, read our [contributor's guide](CONTRIBUTING.md).</span></span>
<span data-ttu-id="7be10-121">參與者指南包含有關如何參與文件、建議工具與樣式和格式需求的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="7be10-121">The contributor's guide contains detail information about how to contribute documentation, suggested tools, and style and formatting requirements.</span></span>
<span data-ttu-id="7be10-122">請使用「問題」和「提取要求」範本，以協助維持文件在不同版本之間的一致性。</span><span class="sxs-lookup"><span data-stu-id="7be10-122">Please use the Issue and Pull Request templates to help keep documentation consistent across versions.</span></span>

## <a name="licenses"></a><span data-ttu-id="7be10-123">授權</span><span class="sxs-lookup"><span data-stu-id="7be10-123">Licenses</span></span>

<span data-ttu-id="7be10-124">此專案有兩個授權檔案。</span><span class="sxs-lookup"><span data-stu-id="7be10-124">There are two license files for this project.</span></span>
<span data-ttu-id="7be10-125">MIT 授權適用於此存放庫中包含的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7be10-125">The MIT License applies to the code contained in this repo.</span></span>
<span data-ttu-id="7be10-126">而 Creative Commons 授權則適用於文件。</span><span class="sxs-lookup"><span data-stu-id="7be10-126">The Creative Commons license applies to the documentation.</span></span>