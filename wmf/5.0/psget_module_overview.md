---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,設定"
ms.openlocfilehash: 2c7e718bc518b332cb4303ef73b1bf5c924ca471
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="powershell-module-discovery-install-and-inventory-with-powershellget"></a><span data-ttu-id="ca506-102">使用 PowerShellGet 探索、安裝及清查 PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="ca506-102">PowerShell Module Discovery, Install and Inventory with PowerShellGet</span></span>
 
<span data-ttu-id="ca506-103">PowerShellGet 隨附於這一版的 WMF：</span><span class="sxs-lookup"><span data-stu-id="ca506-103">PowerShellGet is included in this release of WMF:</span></span>
-   <span data-ttu-id="ca506-104">Find-Module 可以使用 -Tag 參數篩選模組中繼資料</span><span class="sxs-lookup"><span data-stu-id="ca506-104">Find-Module can filter on module metadata with the -Tag parameter</span></span>
-   <span data-ttu-id="ca506-105">Find-Module 可以使用 -Filter 參數篩選存放庫特定的搜尋語言</span><span class="sxs-lookup"><span data-stu-id="ca506-105">Find-Module can filter on repository-specific search language with the -Filter parameter</span></span>
-   <span data-ttu-id="ca506-106">Find-Module 可以使用 -Command、-DscResource 和 -Includes 參數根據模組內容進行篩選</span><span class="sxs-lookup"><span data-stu-id="ca506-106">Find-Module can filter based on module contents with the -Command, -DscResource, and -Includes parameters</span></span>
-   <span data-ttu-id="ca506-107">Find-DscResource 可以在存放庫中探索個別的 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="ca506-107">Find-DscResource allows discovery of individual DSC resources in repositories</span></span>
-   <span data-ttu-id="ca506-108">支援使用 NuGet 從檔案共用安裝和發佈至檔案共用</span><span class="sxs-lookup"><span data-stu-id="ca506-108">Support for installing from and publishing to file shares with NuGet</span></span>

## <a name="example-commands"></a><span data-ttu-id="ca506-109">範例命令</span><span class="sxs-lookup"><span data-stu-id="ca506-109">Example commands</span></span>
```powershell
\# Find all modules with tags Azure or DSC
Find-Module -Tag Azure, DSC

\# Find modules with a specific DscResource
Find-Module -DscResource xFirewall

\#Find modules with specific commands
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

\# Find all modules with Dsc resources
Find-Module -Includes DscResource

\# Find all modules with cmdlets
Find-Module -Includes Cmdlet

\# Find all modules with functions
Find-Module -Includes Function

\# Find all DSC resources
Find-DscResource

\# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking

\# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

\# Find modules using -Filter parameter
\# Specified filter value is searched in Name and Description properties
Find-Module -Filter Cookbook -Repository PSGallery
Find-Module -Filter RBAC -Repository PSGallery
```

## <a name="new-features-in-powershellget"></a><span data-ttu-id="ca506-110">PowerShellGet 的新功能</span><span class="sxs-lookup"><span data-stu-id="ca506-110">New features in PowerShellGet</span></span>
-   <span data-ttu-id="ca506-111">Windows PowerShell 5.0 或更新版本的並存版本支援</span><span class="sxs-lookup"><span data-stu-id="ca506-111">Side-by-side version support on Windows PowerShell 5.0 or newer</span></span>
-   <span data-ttu-id="ca506-112">模組相依性安裝支援</span><span class="sxs-lookup"><span data-stu-id="ca506-112">Module dependency installation support</span></span>
-   <span data-ttu-id="ca506-113">三個新的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ca506-113">Three new cmdlets</span></span>
    -   <span data-ttu-id="ca506-114">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="ca506-114">Get-InstalledModule</span></span>
    -   <span data-ttu-id="ca506-115">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="ca506-115">Uninstall-Module</span></span>
    -   <span data-ttu-id="ca506-116">Save-Module</span><span class="sxs-lookup"><span data-stu-id="ca506-116">Save-Module</span></span>
    
