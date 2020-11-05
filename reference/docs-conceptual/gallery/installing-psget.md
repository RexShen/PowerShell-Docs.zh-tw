---
ms.date: 09/19/2019
title: 安裝 PowerShellGet
description: 此文章說明如何在各種 PowerShell 版本中安裝 PowerShellGet 模組。
ms.openlocfilehash: 06ec331446849784bb8464912fbce0e5a940823f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662142"
---
# <a name="installing-powershellget"></a><span data-ttu-id="c89c0-103">安裝 PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="c89c0-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="c89c0-104">PowerShellGet 是下列版本中的內建模組</span><span class="sxs-lookup"><span data-stu-id="c89c0-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="c89c0-105">[Windows 10](https://www.microsoft.com/windows) 或更新版本</span><span class="sxs-lookup"><span data-stu-id="c89c0-105">[Windows 10](https://www.microsoft.com/windows) or newer</span></span>
- <span data-ttu-id="c89c0-106">[Windows Server 2016](/windows-server/windows-server) 或更新版本</span><span class="sxs-lookup"><span data-stu-id="c89c0-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="c89c0-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) 或更新版本</span><span class="sxs-lookup"><span data-stu-id="c89c0-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="c89c0-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="c89c0-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="c89c0-109">從 PowerShell 資源庫取的最新版本</span><span class="sxs-lookup"><span data-stu-id="c89c0-109">Get the latest version from PowerShell Gallery</span></span>

<span data-ttu-id="c89c0-110">更新 **PowerShellGet** 之前，一律必須先安裝最新的 **NuGet** 提供者。</span><span class="sxs-lookup"><span data-stu-id="c89c0-110">Before updating **PowerShellGet** , you should always install the latest **NuGet** provider.</span></span> <span data-ttu-id="c89c0-111">從已提高權限的 PowerShell 工作階段執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="c89c0-111">From an elevated PowerShell session, run the following command.</span></span>

```powershell
Install-PackageProvider -Name NuGet -Force
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="c89c0-112">針對具有 PowerShell 5.0 (或更新版本) 的系統，您可以安裝最新的 PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="c89c0-112">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

<span data-ttu-id="c89c0-113">若要在 Windows 10、Windows Server 2016、任何已安裝 WMF 5.0 或 5.1 的系統或任何具有 PowerShell 6 的系統上安裝 PowerShellGet，請從已提升權限的 PowerShell 工作階段執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="c89c0-113">To install PowerShellGet on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

```powershell
Install-Module -Name PowerShellGet -Force
```

<span data-ttu-id="c89c0-114">使用 `Update-Module` 來取得較新版本。</span><span class="sxs-lookup"><span data-stu-id="c89c0-114">Use `Update-Module` to get newer versions.</span></span>

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-computers-running-powershell-30-or-powershell-40"></a><span data-ttu-id="c89c0-115">適用於執行 PowerShell 3.0 或 PowerShell 4.0 的電腦</span><span class="sxs-lookup"><span data-stu-id="c89c0-115">For computers running PowerShell 3.0 or PowerShell 4.0</span></span>

<span data-ttu-id="c89c0-116">這些指示適用於已安裝 **PackageManagement Preview** 的電腦，或未安裝任何版本 **PowerShellGet** 的電腦。</span><span class="sxs-lookup"><span data-stu-id="c89c0-116">These instructions apply to computers that have the **PackageManagement Preview** installed or don't have any version of **PowerShellGet** installed.</span></span>

<span data-ttu-id="c89c0-117">`Save-Module` Cmdlet 用於這兩組指令。</span><span class="sxs-lookup"><span data-stu-id="c89c0-117">The `Save-Module` cmdlet is used in both sets of instructions.</span></span> <span data-ttu-id="c89c0-118">`Save-Module` 從已註冊的存放庫下載並儲存模組和任何相依性。</span><span class="sxs-lookup"><span data-stu-id="c89c0-118">`Save-Module` downloads and saves a module and any dependencies from a registered repository.</span></span> <span data-ttu-id="c89c0-119">最新版本模組會儲存至本機電腦上的指定路徑，但不會安裝。</span><span class="sxs-lookup"><span data-stu-id="c89c0-119">The module's most current version is saved to a specified path on the local computer, but isn't installed.</span></span> <span data-ttu-id="c89c0-120">若要將模組安裝在 PowerShell 3.0 或 4.0 中，請將該模組的預存資料夾複製到 `$env:ProgramFiles\WindowsPowerShell\Modules`。</span><span class="sxs-lookup"><span data-stu-id="c89c0-120">To install the modules in PowerShell 3.0 or 4.0, copy the module saved folders to `$env:ProgramFiles\WindowsPowerShell\Modules`.</span></span>

<span data-ttu-id="c89c0-121">如需詳細資訊，請參閱 [Save-Module](/powershell/module/PowershellGet/Save-Module)。</span><span class="sxs-lookup"><span data-stu-id="c89c0-121">For more information, see [Save-Module](/powershell/module/PowershellGet/Save-Module).</span></span>

> [!NOTE]
> <span data-ttu-id="c89c0-122">PowerShell 3.0 與 PowerShell 4.0 僅支援一個模組版本。</span><span class="sxs-lookup"><span data-stu-id="c89c0-122">PowerShell 3.0 and PowerShell 4.0 only supported one version of a module.</span></span> <span data-ttu-id="c89c0-123">自 PowerShell 5.0 起，模組會安裝在 `<modulename>\<version>` 中。</span><span class="sxs-lookup"><span data-stu-id="c89c0-123">Starting in PowerShell 5.0, modules are installed in `<modulename>\<version>`.</span></span> <span data-ttu-id="c89c0-124">這會允許並存安裝多個版本。</span><span class="sxs-lookup"><span data-stu-id="c89c0-124">This allows you to install multiple versions side-by-side.</span></span> <span data-ttu-id="c89c0-125">在使用 `Save-Module` 下載模組後，您必須從 `<modulename>\<version>` 將檔案複製到目標電腦上的 `<modulename>` 資料夾，如下列說明所示。</span><span class="sxs-lookup"><span data-stu-id="c89c0-125">After downloading the module using `Save-Module` you must copy the files from the `<modulename>\<version>` to the `<modulename>` folder on the destination machine, as shown in the instructions below.</span></span>

#### <a name="preparatory-step-on-computers-running-powershell-30"></a><span data-ttu-id="c89c0-126">執行 PowerShell 3.0 的電腦上準備步驟</span><span class="sxs-lookup"><span data-stu-id="c89c0-126">Preparatory Step on computers running PowerShell 3.0</span></span>

<span data-ttu-id="c89c0-127">下列各節中的說明會在 `$env:ProgramFiles\WindowsPowerShell\Modules` 目錄中安裝模組。</span><span class="sxs-lookup"><span data-stu-id="c89c0-127">The instructions in the sections below install the modules in directory `$env:ProgramFiles\WindowsPowerShell\Modules`.</span></span>
<span data-ttu-id="c89c0-128">在 PowerShell 3.0 中，根據預設此目錄不會列在 `$env:PSModulePath` 中，因此需要新增此目錄，才能自動載入模組。</span><span class="sxs-lookup"><span data-stu-id="c89c0-128">In PowerShell 3.0, this directory isn't listed in `$env:PSModulePath` by default, so you'll need to add it in order for the modules to be auto-loaded.</span></span>

<span data-ttu-id="c89c0-129">開啟提升權限的 PowerShell 工作階段，並執行下列命令 (這會在未來的工作階段中生效)：</span><span class="sxs-lookup"><span data-stu-id="c89c0-129">Open an elevated PowerShell session and run the following command (which will take effect in future sessions):</span></span>

```powershell
[Environment]::SetEnvironmentVariable(
  'PSModulePath',
  ((([Environment]::GetEnvironmentVariable('PSModulePath', 'Machine') -split ';') + "$env:ProgramFiles\WindowsPowerShell\Modules") -join ';'),
  'Machine'
)
```

#### <a name="computers-with-the-packagemanagement-preview-installed"></a><span data-ttu-id="c89c0-130">已安裝 PackageManagement Preview 的電腦</span><span class="sxs-lookup"><span data-stu-id="c89c0-130">Computers with the PackageManagement Preview installed</span></span>

> [!NOTE]
> <span data-ttu-id="c89c0-131">PackageManagement Preview 是一個可下載的元件，其可供在 PowerShell 版本 3 和 4 中使用 PowerShellGet，但其已不再提供使用。</span><span class="sxs-lookup"><span data-stu-id="c89c0-131">PackageManagement Preview was a downloadable component that made PowerShellGet available to PowerShell versions 3 and 4, but it is no longer available.</span></span>
> <span data-ttu-id="c89c0-132">若要測試是否已在指定電腦上安裝該項目，請執行 `Get-Module -ListAvailable PowerShellGet`。</span><span class="sxs-lookup"><span data-stu-id="c89c0-132">To test if it was installed on a given computer, run `Get-Module -ListAvailable PowerShellGet`.</span></span>

1. <span data-ttu-id="c89c0-133">在 PowerShell 工作階段中，使用 `Save-Module` 來下載 **PowerShellGet** 的目前版本。</span><span class="sxs-lookup"><span data-stu-id="c89c0-133">From a PowerShell session, use `Save-Module` to download the current version of **PowerShellGet**.</span></span> <span data-ttu-id="c89c0-134">會下載兩個資料夾： **PowerShellGet** 和 **PackageManagement** 。</span><span class="sxs-lookup"><span data-stu-id="c89c0-134">Two folders are downloaded: **PowerShellGet** and **PackageManagement**.</span></span> <span data-ttu-id="c89c0-135">每個資料夾都包含具有版本號碼的子資料夾。</span><span class="sxs-lookup"><span data-stu-id="c89c0-135">Each folder contains a subfolder with a version number.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. <span data-ttu-id="c89c0-136">確定任何其他處理序都未載入 **PowerShellGet** 和 **PackageManagment** 模組。</span><span class="sxs-lookup"><span data-stu-id="c89c0-136">Ensure that the **PowerShellGet** and **PackageManagement** modules aren't loaded in any other processes.</span></span>

1. <span data-ttu-id="c89c0-137">使用已提升的權限重新開啟 PowerShell 主控台，並執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="c89c0-137">Reopen the PowerShell console with elevated permissions and run the following command.</span></span>

   ```powershell
   'PowerShellGet', 'PackageManagement' | % {
     $targetDir = "$env:ProgramFiles\WindowsPowerShell\Modules\$_"
     Remove-Item $targetDir\* -Recurse -Force
     Copy-Item C:\LocalFolder\$_\*\* $targetDir\ -Recurse -Force
   }
   ```

#### <a name="computers-without-powershellget"></a><span data-ttu-id="c89c0-138">不具有 PowerShellGet 的電腦</span><span class="sxs-lookup"><span data-stu-id="c89c0-138">Computers without PowerShellGet</span></span>

<span data-ttu-id="c89c0-139">針對沒有安裝任何 **PowerShellGet** 版本的電腦 (使用 `Get-Module -ListAvailable PowerShellGet` 測試)，將需要已安裝 **PowerShellGet** 的電腦來下載模組。</span><span class="sxs-lookup"><span data-stu-id="c89c0-139">For computers without any version of **PowerShellGet** installed (test with `Get-Module -ListAvailable PowerShellGet`), a computer with **PowerShellGet** installed is needed to download the modules.</span></span>

1. <span data-ttu-id="c89c0-140">從已安裝 **PowerShellGet** 的電腦上，使用 `Save-Module` 下載目前版本的 **PowerShellGet** 。</span><span class="sxs-lookup"><span data-stu-id="c89c0-140">From the computer that has **PowerShellGet** installed, use `Save-Module` to download the current version of **PowerShellGet**.</span></span> <span data-ttu-id="c89c0-141">會下載兩個資料夾： **PowerShellGet** 和 **PackageManagement** 。</span><span class="sxs-lookup"><span data-stu-id="c89c0-141">Two folders are downloaded: **PowerShellGet** and **PackageManagement**.</span></span> <span data-ttu-id="c89c0-142">每個資料夾都包含具有版本號碼的子資料夾。</span><span class="sxs-lookup"><span data-stu-id="c89c0-142">Each folder contains a subfolder with a version number.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. <span data-ttu-id="c89c0-143">將 **PowerShellGet** 和 **PackageManagement** 資料夾中的個別 `<version>` 子資料夾分別複製到沒有安裝 **PowerShellGet** 電腦中的 `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` 和 `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` 資料夾，這項操作需要提升權限的工作階段。</span><span class="sxs-lookup"><span data-stu-id="c89c0-143">Copy the respective `<version>` subfolder in the **PowerShellGet** and **PackageManagement** folders to the computer that doesn't have **PowerShellGet** installed, into folders `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` respectively, which requires an elevated session.</span></span>

1. <span data-ttu-id="c89c0-144">例如，若可存取其他電腦 (例如 `ws1`) 上的下載資料夾，請透過 UNC 路徑 (例如 `\\ws1\C$\LocalFolder`) 在目標電腦上開啟提升權限的 PowerShell 主控台，並執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="c89c0-144">For instance, if you can access the download folder on the other computer, say `ws1`, from the target computer via a UNC path, say `\\ws1\C$\LocalFolder`, open a PowerShell console with elevated permissions and run the following command:</span></span>

   ```powershell
   'PowerShellGet', 'PackageManagement' | % {
     $targetDir = "$env:ProgramFiles\WindowsPowerShell\Modules\$_"
     $null = New-Item -Type Directory -Force $targetDir
     $fromComputer = 'ws1'  # Specify the name of the other computer here.
     Copy-Item \\$fromComputer\C$\LocalFolder\$_\*\* $targetDir -Recurse -Force
     if (-not (Get-ChildItem $targetDir)) { Throw "Copying failed." }
   }
   ```
