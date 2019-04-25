---
ms.date: 06/12/2017
contributor: manikb
keywords: 資源庫,powershell,cmdlet,psget
title: 安裝 PowerShellGet
ms.openlocfilehash: 23a53a9117c9f6a7ad157b635cd7ff4b3b3444c5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075268"
---
# <a name="installing-powershellget"></a><span data-ttu-id="e2a03-103">安裝 PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="e2a03-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="e2a03-104">PowerShellGet 是下列版本中的內建模組</span><span class="sxs-lookup"><span data-stu-id="e2a03-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="e2a03-105">[Windows 10](https://www.microsoft.com/windows) 或更新版本</span><span class="sxs-lookup"><span data-stu-id="e2a03-105">[Windows 10](https://www.microsoft.com/windows) or newer</span></span>
- <span data-ttu-id="e2a03-106">[Windows Server 2016](/windows-server/windows-server) 或更新版本</span><span class="sxs-lookup"><span data-stu-id="e2a03-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="e2a03-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) 或更新版本</span><span class="sxs-lookup"><span data-stu-id="e2a03-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="e2a03-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="e2a03-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a><span data-ttu-id="e2a03-109">取得適用於 PowerShell 3.0 和 4.0 版的 PowerShellGet 模組</span><span class="sxs-lookup"><span data-stu-id="e2a03-109">Get PowerShellGet module for PowerShell versions 3.0 and 4.0</span></span>

- [<span data-ttu-id="e2a03-110">PackageManagement MSI</span><span class="sxs-lookup"><span data-stu-id="e2a03-110">PackageManagement MSI</span></span>](https://www.microsoft.com/download/details.aspx?id=51451)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="e2a03-111">從 PowerShell 資源庫取的最新版本</span><span class="sxs-lookup"><span data-stu-id="e2a03-111">Get the latest version from PowerShell Gallery</span></span>

- <span data-ttu-id="e2a03-112">更新 PowerShellGet 之前，您應該一律先安裝最新的 Nuget 提供者。</span><span class="sxs-lookup"><span data-stu-id="e2a03-112">Before updating PowerShellGet, you should always install the latest Nuget provider.</span></span> <span data-ttu-id="e2a03-113">若要這樣做，請在已提升權限的 PowerShell 工作階段中執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="e2a03-113">To do that, run the following in an elevated PowerShell session.</span></span>

  ```powershell
  Install-PackageProvider Nuget –Force
  Exit
  ```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="e2a03-114">針對具有 PowerShell 5.0 (或更新版本) 的系統，您可以安裝最新的 PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="e2a03-114">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

- <span data-ttu-id="e2a03-115">若要在 Windows 10、Windows Server 2016、任何已安裝 WMF 5.0 或 5.1 的系統或任何具有 PowerShell 6 的系統上執行此操作，請從已提升權限的 PowerShell 工作階段執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="e2a03-115">To do this on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

  ```powershell
  Install-Module –Name PowerShellGet –Force
  Exit
  ```

- <span data-ttu-id="e2a03-116">使用 `Update-Module` 來取得較新版本。</span><span class="sxs-lookup"><span data-stu-id="e2a03-116">Use `Update-Module` to get newer versions.</span></span>

  ```powershell
  Update-Module -Name PowerShellGet
  Exit
  ```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpswwwmicrosoftcomdownloaddetailsaspxid51451"></a><span data-ttu-id="e2a03-117">針對執行 PowerShell 3 或 PowerShell 4 且已安裝 [PackageManagement MSI](https://www.microsoft.com/download/details.aspx?id=51451) 的系統</span><span class="sxs-lookup"><span data-stu-id="e2a03-117">For systems running PowerShell 3 or PowerShell 4, that have installed the [PackageManagement MSI](https://www.microsoft.com/download/details.aspx?id=51451)</span></span>

- <span data-ttu-id="e2a03-118">從已提升權限的 PowerShell 工作階段中使用下列 PowerShellGet Cmdlet 將模組儲存至本機目錄</span><span class="sxs-lookup"><span data-stu-id="e2a03-118">Use below PowerShellGet cmdlet from an elevated PowerShell session to save the modules to a local directory</span></span>

  ```powershell
  Save-Module PowerShellGet -Path C:\LocalFolder
  Exit
  ```

- <span data-ttu-id="e2a03-119">確定任何其他處理序都未載入 PowerShellGet 和 PackageManagment 模組。</span><span class="sxs-lookup"><span data-stu-id="e2a03-119">Ensure that PowerShellGet and PackageManagement modules are not loaded in any other processes.</span></span>
- <span data-ttu-id="e2a03-120">刪除 `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` 和 `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` 資料夾的內容。</span><span class="sxs-lookup"><span data-stu-id="e2a03-120">Delete contents of `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and  `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` folders.</span></span>
- <span data-ttu-id="e2a03-121">使用已提升的權限來重新開啟「PS 主控台」，然後執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="e2a03-121">Re-open the PS Console with elevated permissions then run the following commands.</span></span>

  ```powershell
  Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
  Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
  ```
