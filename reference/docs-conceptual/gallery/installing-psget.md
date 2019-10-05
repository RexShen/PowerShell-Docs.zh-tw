---
ms.date: 09/19/2019
contributor: manikb
keywords: 資源庫,powershell,cmdlet,psget
title: 安裝 PowerShellGet
ms.openlocfilehash: 69dc851c54089b47fb19e5b32990d579d26effb9
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328199"
---
# <a name="installing-powershellget"></a><span data-ttu-id="dbd7a-103">安裝 PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="dbd7a-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="dbd7a-104">PowerShellGet 是下列版本中的內建模組</span><span class="sxs-lookup"><span data-stu-id="dbd7a-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="dbd7a-105">[Windows 10](https://www.microsoft.com/windows) 或更新版本</span><span class="sxs-lookup"><span data-stu-id="dbd7a-105">[Windows 10](https://www.microsoft.com/windows) or newer</span></span>
- <span data-ttu-id="dbd7a-106">[Windows Server 2016](/windows-server/windows-server) 或更新版本</span><span class="sxs-lookup"><span data-stu-id="dbd7a-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="dbd7a-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) 或更新版本</span><span class="sxs-lookup"><span data-stu-id="dbd7a-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="dbd7a-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="dbd7a-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="dbd7a-109">從 PowerShell 資源庫取的最新版本</span><span class="sxs-lookup"><span data-stu-id="dbd7a-109">Get the latest version from PowerShell Gallery</span></span>

<span data-ttu-id="dbd7a-110">更新 **PowerShellGet** 之前，一律必須先安裝最新的 **NuGet** 提供者。</span><span class="sxs-lookup"><span data-stu-id="dbd7a-110">Before updating **PowerShellGet**, you should always install the latest **NuGet** provider.</span></span> <span data-ttu-id="dbd7a-111">從已提高權限的 PowerShell 工作階段執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="dbd7a-111">From an elevated PowerShell session, run the following command.</span></span>

```powershell
Install-PackageProvider -Name NuGet -Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="dbd7a-112">針對具有 PowerShell 5.0 (或更新版本) 的系統，您可以安裝最新的 PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="dbd7a-112">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

<span data-ttu-id="dbd7a-113">若要在 Windows 10、Windows Server 2016、任何已安裝 WMF 5.0 或 5.1 的系統或任何具有 PowerShell 6 的系統上安裝 PowerShellGet，請從已提升權限的 PowerShell 工作階段執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="dbd7a-113">To install PowerShellGet on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

```powershell
Install-Module -Name PowerShellGet -Force
Exit
```

<span data-ttu-id="dbd7a-114">使用 `Update-Module` 來取得較新版本。</span><span class="sxs-lookup"><span data-stu-id="dbd7a-114">Use `Update-Module` to get newer versions.</span></span>

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-computers-running-powershell-30-or-powershell-40"></a><span data-ttu-id="dbd7a-115">適用於執行 PowerShell 3.0 或 PowerShell 4.0 的電腦</span><span class="sxs-lookup"><span data-stu-id="dbd7a-115">For computers running PowerShell 3.0 or PowerShell 4.0</span></span>

<span data-ttu-id="dbd7a-116">這些指示適用於已安裝 **PackageManagement Preview** 的電腦，或未安裝任何版本 **PowerShellGet** 的電腦。</span><span class="sxs-lookup"><span data-stu-id="dbd7a-116">These instructions apply to computers that have the **PackageManagement Preview** installed or don't have any version of **PowerShellGet** installed.</span></span>

<span data-ttu-id="dbd7a-117">`Save-Module` Cmdlet 用於這兩組指令。</span><span class="sxs-lookup"><span data-stu-id="dbd7a-117">The `Save-Module` cmdlet is used in both sets of instructions.</span></span> <span data-ttu-id="dbd7a-118">`Save-Module` 從已註冊的存放庫下載並儲存模組和任何相依性。</span><span class="sxs-lookup"><span data-stu-id="dbd7a-118">`Save-Module` downloads and saves a module and any dependencies from a registered repository.</span></span> <span data-ttu-id="dbd7a-119">最新版本模組會儲存至本機電腦上的指定路徑，但不會安裝。</span><span class="sxs-lookup"><span data-stu-id="dbd7a-119">The module's most current version is saved to a specified path on the local computer, but isn't installed.</span></span> <span data-ttu-id="dbd7a-120">如需詳細資訊，請參閱 [Save-Module](/powershell/module/PowershellGet/Save-Module)。</span><span class="sxs-lookup"><span data-stu-id="dbd7a-120">For more information, see [Save-Module](/powershell/module/PowershellGet/Save-Module).</span></span>

#### <a name="computers-with-the-packagemanagement-preview-installed"></a><span data-ttu-id="dbd7a-121">已安裝 PackageManagement Preview 的電腦</span><span class="sxs-lookup"><span data-stu-id="dbd7a-121">Computers with the PackageManagement Preview installed</span></span>

1. <span data-ttu-id="dbd7a-122">從 PowerShell 工作階段使用 `Save-Module` 將模組儲存至本機目錄。</span><span class="sxs-lookup"><span data-stu-id="dbd7a-122">From a PowerShell session, use `Save-Module` to save the modules to a local directory.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. <span data-ttu-id="dbd7a-123">確定任何其他處理序都未載入 **PowerShellGet** 和 **PackageManagment** 模組。</span><span class="sxs-lookup"><span data-stu-id="dbd7a-123">Ensure that the **PowerShellGet** and **PackageManagement** modules aren't loaded in any other processes.</span></span>
1. <span data-ttu-id="dbd7a-124">刪除資料夾的內容：`$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` 與 `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`。</span><span class="sxs-lookup"><span data-stu-id="dbd7a-124">Delete the contents of the folders: `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span></span>
1. <span data-ttu-id="dbd7a-125">使用已提升的權限重新開啟 PowerShell 主控台，然後執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="dbd7a-125">Reopen the PowerShell console with elevated permissions and run the following commands.</span></span>

   ```powershell
   Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
   Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
   ```

#### <a name="computers-without-powershellget"></a><span data-ttu-id="dbd7a-126">不具有 PowerShellGet 的電腦</span><span class="sxs-lookup"><span data-stu-id="dbd7a-126">Computers without PowerShellGet</span></span>

<span data-ttu-id="dbd7a-127">如果電腦沒有安裝任何版本的 **PowerShellGet**，則需要安裝具有 **PowerShellGet** 的電腦，才能下載模組。</span><span class="sxs-lookup"><span data-stu-id="dbd7a-127">For computer's without any version of **PowerShellGet** installed, a computer with **PowerShellGet** installed is needed to download the modules.</span></span>

1. <span data-ttu-id="dbd7a-128">從已安裝 **PowerShellGet** 的電腦上，使用 `Save-Module` 下載目前版本的 **PowerShellGet**。</span><span class="sxs-lookup"><span data-stu-id="dbd7a-128">From the computer that has **PowerShellGet** installed, use `Save-Module` to download the current version of **PowerShellGet**.</span></span> <span data-ttu-id="dbd7a-129">會下載兩個資料夾：**PowerShellGet** 和 **PackageManagement**。</span><span class="sxs-lookup"><span data-stu-id="dbd7a-129">Two folders are downloaded: **PowerShellGet** and **PackageManagement**.</span></span> <span data-ttu-id="dbd7a-130">每個資料夾都包含具有版本號碼的子資料夾。</span><span class="sxs-lookup"><span data-stu-id="dbd7a-130">Each folder contains a subfolder with a version number.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. <span data-ttu-id="dbd7a-131">將 **PowerShellGet** 和 **PackageManagement** 資料夾複製到未安裝 **PowerShellGet** 的電腦。</span><span class="sxs-lookup"><span data-stu-id="dbd7a-131">Copy the **PowerShellGet** and **PackageManagement** folders to the computer that doesn't have **PowerShellGet** installed.</span></span>

   <span data-ttu-id="dbd7a-132">目的地目錄為：`$env:ProgramFiles\WindowsPowerShell\Modules`</span><span class="sxs-lookup"><span data-stu-id="dbd7a-132">The destination directory is: `$env:ProgramFiles\WindowsPowerShell\Modules`</span></span>
