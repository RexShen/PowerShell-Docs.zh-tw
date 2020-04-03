---
title: 從 Windows PowerShell 5.1 移轉至 PowerShell 7
description: 針對您的 Windows 平台，從 PowerShell 5.1 更新為 PowerShell 7。
ms.date: 03/25/2020
ms.openlocfilehash: e3881b1758f50119444969ad39541aec694cebe5
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500493"
---
# <a name="migrating-from-windows-powershell-51-to-powershell-7"></a><span data-ttu-id="cf105-103">從 Windows PowerShell 5.1 移轉至 PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="cf105-103">Migrating from Windows PowerShell 5.1 to PowerShell 7</span></span>

<span data-ttu-id="cf105-104">PowerShell 7 是針對雲端、內部部署和混合式環境所設計，具有增強功能和[新功能](What-s-New-in-PowerShell-70.md)。</span><span class="sxs-lookup"><span data-stu-id="cf105-104">Designed for cloud, on-premises, and hybrid environments, PowerShell 7 is packed with enhancements and [new features](What-s-New-in-PowerShell-70.md).</span></span>

- <span data-ttu-id="cf105-105">與 Windows PowerShell 並存安裝和執行</span><span class="sxs-lookup"><span data-stu-id="cf105-105">Installs and runs side-by-side with Windows PowerShell</span></span>
- <span data-ttu-id="cf105-106">改善與現有 Windows PowerShell 模組的相容性</span><span class="sxs-lookup"><span data-stu-id="cf105-106">Improved compatibility with existing Windows PowerShell modules</span></span>
- <span data-ttu-id="cf105-107">新的語言功能，例如三元運算子和 `ForEach-Object -Parallel`</span><span class="sxs-lookup"><span data-stu-id="cf105-107">New language features, like ternary operators and `ForEach-Object -Parallel`</span></span>
- <span data-ttu-id="cf105-108">提升效能</span><span class="sxs-lookup"><span data-stu-id="cf105-108">Improved performance</span></span>
- <span data-ttu-id="cf105-109">以 SSH 為基礎的遠端功能</span><span class="sxs-lookup"><span data-stu-id="cf105-109">SSH-based remoting</span></span>
- <span data-ttu-id="cf105-110">跨平台互通性</span><span class="sxs-lookup"><span data-stu-id="cf105-110">Cross-platform interoperability</span></span>
- <span data-ttu-id="cf105-111">支援 Docker 容器</span><span class="sxs-lookup"><span data-stu-id="cf105-111">Support for Docker containers</span></span>

<span data-ttu-id="cf105-112">PowerShell 7 與 Windows PowerShell 並存運作，可讓您在部署之前，輕鬆地在版本之間進行測試和比較。</span><span class="sxs-lookup"><span data-stu-id="cf105-112">PowerShell 7 works side-by-side with Windows PowerShell letting you easily test and compare between editions before deployment.</span></span> <span data-ttu-id="cf105-113">移轉既簡單又快速，而且很安全。</span><span class="sxs-lookup"><span data-stu-id="cf105-113">Migration is simple, quick, and safe.</span></span> <span data-ttu-id="cf105-114">失敗。</span><span class="sxs-lookup"><span data-stu-id="cf105-114">failure.</span></span>

<span data-ttu-id="cf105-115">下列 Windows 作業系統支援 PowerShell 7：</span><span class="sxs-lookup"><span data-stu-id="cf105-115">PowerShell 7 is supported on the following Windows operating systems:</span></span>

- <span data-ttu-id="cf105-116">Windows 8.1 和 10</span><span class="sxs-lookup"><span data-stu-id="cf105-116">Windows 8.1 and 10</span></span>
- <span data-ttu-id="cf105-117">Windows Server 2012、2012 R2、2016 及 2019</span><span class="sxs-lookup"><span data-stu-id="cf105-117">Windows Server 2012, 2012 R2, 2016, and 2019</span></span>

<span data-ttu-id="cf105-118">PowerShell 7 也可以在 macOS 和數個 Linux 散發套件上執行。</span><span class="sxs-lookup"><span data-stu-id="cf105-118">PowerShell 7 also runs on macOS and several Linux distributions.</span></span> <span data-ttu-id="cf105-119">如需支援的作業系統清單和支援生命週期的詳細資訊，請參閱 [PowerShell 支援生命週期](/powershell/scripting/powershell-support-lifecycle)。</span><span class="sxs-lookup"><span data-stu-id="cf105-119">For a list of supported operating systems and information about the support lifecycle, see the [PowerShell Support Lifecycle](/powershell/scripting/powershell-support-lifecycle).</span></span>

## <a name="installing-powershell-7"></a><span data-ttu-id="cf105-120">安裝 PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="cf105-120">Installing PowerShell 7</span></span>

<span data-ttu-id="cf105-121">為了提供彈性並支援 IT、DevOps 工程師和開發人員的需求，有數個選項可用來安裝 PowerShell 7。</span><span class="sxs-lookup"><span data-stu-id="cf105-121">For flexibility and to support the needs of IT, DevOps engineers, and developers, there are several options available to install PowerShell 7.</span></span> <span data-ttu-id="cf105-122">在大部分情況下，安裝選項可以縮減為下列方法：</span><span class="sxs-lookup"><span data-stu-id="cf105-122">In most cases, the installation options can be reduced to the following methods:</span></span>

- <span data-ttu-id="cf105-123">使用 [MSI 套件](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-msi-package)來部署 PowerShell</span><span class="sxs-lookup"><span data-stu-id="cf105-123">Deploy PowerShell using the [MSI package](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-msi-package)</span></span>
- <span data-ttu-id="cf105-124">使用 [ZIP 套件](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-zip-package)來部署 PowerShell</span><span class="sxs-lookup"><span data-stu-id="cf105-124">Deploy PowerShell using the [ZIP package](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-zip-package)</span></span>

> [!NOTE]
> <span data-ttu-id="cf105-125">您可以使用 [System Center Configuration Manager (SCCM)](/configmgr/apps/) 之類的管理產品來部署及更新 MSI 套件。</span><span class="sxs-lookup"><span data-stu-id="cf105-125">The MSI package can be deployed and updated with management products such as [System Center Configuration Manager (SCCM)](/configmgr/apps/).</span></span> <span data-ttu-id="cf105-126">從 [GitHub 版本頁面](https://github.com/PowerShell/PowerShell/releases)下載套件。</span><span class="sxs-lookup"><span data-stu-id="cf105-126">Download the packages from [GitHub Release page](https://github.com/PowerShell/PowerShell/releases).</span></span>

<span data-ttu-id="cf105-127">部署 MSI 套件需要系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="cf105-127">Deploying the MSI package requires Administrator permission.</span></span> <span data-ttu-id="cf105-128">任何使用者都可以部署 ZIP 套件。</span><span class="sxs-lookup"><span data-stu-id="cf105-128">The ZIP package can be deployed by any user.</span></span> <span data-ttu-id="cf105-129">在認可完整安裝之前，ZIP 套件是安裝 PowerShell 7 以進行測試最簡單的方式。</span><span class="sxs-lookup"><span data-stu-id="cf105-129">The ZIP package is the easiest way to install PowerShell 7 for testing, before committing to a full installation.</span></span>

## <a name="using-powershell-7-side-by-side-with-windows-powershell-51"></a><span data-ttu-id="cf105-130">與 Windows PowerShell 5.1 並存使用 PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="cf105-130">Using PowerShell 7 side-by-side with Windows PowerShell 5.1</span></span>

<span data-ttu-id="cf105-131">PowerShell 7 的設計是與 Windows PowerShell 5.1 並存。</span><span class="sxs-lookup"><span data-stu-id="cf105-131">PowerShell 7 is designed to coexist with Windows PowerShell 5.1.</span></span> <span data-ttu-id="cf105-132">下列功能可確保您在 PowerShell 中的投資受到保護，且您移轉至 PowerShell 7 很簡單。</span><span class="sxs-lookup"><span data-stu-id="cf105-132">The following features ensure that your investment in PowerShell is protected and your migration to PowerShell 7 is simple.</span></span>

- <span data-ttu-id="cf105-133">個別安裝路徑和可執行檔名稱</span><span class="sxs-lookup"><span data-stu-id="cf105-133">Separate installation path and executable name</span></span>
- <span data-ttu-id="cf105-134">個別 PSModulePath</span><span class="sxs-lookup"><span data-stu-id="cf105-134">Separate PSModulePath</span></span>
- <span data-ttu-id="cf105-135">每個版本都有個別設定檔</span><span class="sxs-lookup"><span data-stu-id="cf105-135">Separate profiles for each version</span></span>
- <span data-ttu-id="cf105-136">改良的模組相容性</span><span class="sxs-lookup"><span data-stu-id="cf105-136">Improved module compatibility</span></span>
- <span data-ttu-id="cf105-137">新的遠端端點</span><span class="sxs-lookup"><span data-stu-id="cf105-137">New remoting endpoints</span></span>
- <span data-ttu-id="cf105-138">群組原則支援</span><span class="sxs-lookup"><span data-stu-id="cf105-138">Group policy support</span></span>
- <span data-ttu-id="cf105-139">個別事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="cf105-139">Separate Event logs</span></span>

### <a name="separate-installation-path-and-executable-name"></a><span data-ttu-id="cf105-140">個別安裝路徑和可執行檔名稱</span><span class="sxs-lookup"><span data-stu-id="cf105-140">Separate installation path and executable name</span></span>

<span data-ttu-id="cf105-141">PowerShell 7 會安裝到新目錄，並與 Windows PowerShell 5.1 並存執行。</span><span class="sxs-lookup"><span data-stu-id="cf105-141">PowerShell 7 installs to a new directory, enabling side-by-side execution with Windows PowerShell 5.1.</span></span>

<span data-ttu-id="cf105-142">依版本的安裝位置：</span><span class="sxs-lookup"><span data-stu-id="cf105-142">Install locations by version:</span></span>

- <span data-ttu-id="cf105-143">Windows PowerShell 5.1：`$env:WINDIR\System32\WindowsPowerShell\v1.0`</span><span class="sxs-lookup"><span data-stu-id="cf105-143">Windows PowerShell 5.1: `$env:WINDIR\System32\WindowsPowerShell\v1.0`</span></span>
- <span data-ttu-id="cf105-144">PowerShell Core 6.x：`$env:ProgramFiles\PowerShell\6`</span><span class="sxs-lookup"><span data-stu-id="cf105-144">PowerShell Core 6.x: `$env:ProgramFiles\PowerShell\6`</span></span>
- <span data-ttu-id="cf105-145">PowerShell 7：`$env:ProgramFiles\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="cf105-145">PowerShell 7: `$env:ProgramFiles\PowerShell\7`</span></span>

<span data-ttu-id="cf105-146">新的位置會新增至您的 PATH，讓您能夠同時執行 Windows PowerShell 5.1 和 PowerShell 7。</span><span class="sxs-lookup"><span data-stu-id="cf105-146">The new location is added to your PATH allowing you to run both Windows PowerShell 5.1 and PowerShell 7.</span></span> <span data-ttu-id="cf105-147">如果您要從 PowerShell Core 6.x 遷移至 PowerShell 7，則會移除 PowerShell 6 並取代 PATH。</span><span class="sxs-lookup"><span data-stu-id="cf105-147">If you're migrating from PowerShell Core 6.x to PowerShell 7, PowerShell 6 is removed and the PATH replaced.</span></span>

<span data-ttu-id="cf105-148">在 Windows PowerShell 中，PowerShell 可執行檔的名稱為 `powershell.exe`。</span><span class="sxs-lookup"><span data-stu-id="cf105-148">In Windows PowerShell, the PowerShell executable is named `powershell.exe`.</span></span> <span data-ttu-id="cf105-149">在第 6 版和更新版本中，可執行檔的名稱為 `pwsh.exe`。</span><span class="sxs-lookup"><span data-stu-id="cf105-149">In version 6 and above, the executable is named `pwsh.exe`.</span></span> <span data-ttu-id="cf105-150">新的名稱可讓您輕鬆地支援這兩個版本的並存執行。</span><span class="sxs-lookup"><span data-stu-id="cf105-150">The new name makes it easy to support side-by-side execution of both versions.</span></span>

### <a name="separate-psmodulepath"></a><span data-ttu-id="cf105-151">個別 PSModulePath</span><span class="sxs-lookup"><span data-stu-id="cf105-151">Separate PSModulePath</span></span>

<span data-ttu-id="cf105-152">根據預設，Windows PowerShell 和 PowerShell 7 會在不同的位置儲存模組。</span><span class="sxs-lookup"><span data-stu-id="cf105-152">By default, Windows PowerShell and PowerShell 7 store modules in different locations.</span></span> <span data-ttu-id="cf105-153">PowerShell 7 會將這些位置合併到 `$Env:PSModulePath` 環境變數中。</span><span class="sxs-lookup"><span data-stu-id="cf105-153">PowerShell 7 combines those locations in the `$Env:PSModulePath` environment variable.</span></span> <span data-ttu-id="cf105-154">依名稱匯入模組時，PowerShell 會檢查 `$Env:PSModulePath` 所指定的位置。</span><span class="sxs-lookup"><span data-stu-id="cf105-154">When importing a module by name, PowerShell checks the location specified by `$Env:PSModulePath`.</span></span> <span data-ttu-id="cf105-155">這可讓 PowerShell 7 同時載入核心和桌面模組。</span><span class="sxs-lookup"><span data-stu-id="cf105-155">This allows PowerShell 7 to load both Core and Desktop modules.</span></span>

|            <span data-ttu-id="cf105-156">安裝範圍</span><span class="sxs-lookup"><span data-stu-id="cf105-156">Install Scope</span></span>            |                <span data-ttu-id="cf105-157">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="cf105-157">Windows PowerShell 5.1</span></span>                 |             <span data-ttu-id="cf105-158">PowerShell 7.0</span><span class="sxs-lookup"><span data-stu-id="cf105-158">PowerShell 7.0</span></span>             |
| ----------------------------------- | ----------------------------------------------------- | -------------------------------------- |
| <span data-ttu-id="cf105-159">PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="cf105-159">PowerShell modules</span></span>                  | `$env:WINDIR\system32\WindowsPowerShell\v1.0\Modules` | `$PSHOME\Modules`                      |
| <span data-ttu-id="cf105-160">使用者已安裝</span><span class="sxs-lookup"><span data-stu-id="cf105-160">User installed</span></span><br><span data-ttu-id="cf105-161">AllUsers 範圍</span><span class="sxs-lookup"><span data-stu-id="cf105-161">AllUsers scope</span></span>    | `$env:ProgramFiles\WindowsPowerShell\Modules`         | `$env:ProgramFiles\PowerShell\Modules` |
| <span data-ttu-id="cf105-162">使用者已安裝</span><span class="sxs-lookup"><span data-stu-id="cf105-162">User installed</span></span><br><span data-ttu-id="cf105-163">CurrentUser 範圍</span><span class="sxs-lookup"><span data-stu-id="cf105-163">CurrentUser scope</span></span> | `$HOME\Documents\WindowsPowerShell\Modules`           | `$HOME\Documents\PowerShell\Modules`   |

<span data-ttu-id="cf105-164">下列範例會顯示每個版本的 `$Env:PSModulePath` 預設值。</span><span class="sxs-lookup"><span data-stu-id="cf105-164">The following examples show the default values of `$Env:PSModulePath` for each version.</span></span>

- <span data-ttu-id="cf105-165">若是 Windows PowerShell 5.1：</span><span class="sxs-lookup"><span data-stu-id="cf105-165">For Windows PowerShell 5.1:</span></span>

  ```powershell
  $Env:PSModulePath -split (';')
  ```

  ```Output
  C:\Users\<user>\Documents\WindowsPowerShell\Modules
  C:\Program Files\WindowsPowerShell\Modules
  C:\WINDOWS\System32\WindowsPowerShell\v1.0\Modules
  ```

- <span data-ttu-id="cf105-166">若是 PowerShell 7：</span><span class="sxs-lookup"><span data-stu-id="cf105-166">For PowerShell 7:</span></span>

  ```powershell
  $Env:PSModulePath -split (';')
  ```

  ```Output
  C:\Users\<user>\Documents\PowerShell\Modules
  C:\Program Files\PowerShell\Modules
  C:\Program Files\PowerShell\7\Modules
  C:\Program Files\WindowsPowerShell\Modules
  C:\WINDOWS\System32\WindowsPowerShell\v1.0\Modules
  ```

<span data-ttu-id="cf105-167">請注意，PowerShell 7 包含 Windows PowerShell 路徑和 PowerShell 7 路徑，以提供模組的自動載入。</span><span class="sxs-lookup"><span data-stu-id="cf105-167">Notice that PowerShell 7 includes the Windows PowerShell paths and the PowerShell 7 paths to provide autoloading of modules.</span></span>

> [!NOTE]
> <span data-ttu-id="cf105-168">如果您已變更 PSModulePath 環境變數或已安裝自訂模組或應用程式，則可能會有其他路徑。</span><span class="sxs-lookup"><span data-stu-id="cf105-168">Additional paths may exist if you have changed the PSModulePath environment variable or installed custom modules or applications.</span></span>

<span data-ttu-id="cf105-169">如需詳細資訊，請參閱 [about_Environment_Variables](/powershell/module/microsoft.powershell.core/about/about_environment_variables#environment-variables-that-store-preferences) 中的 `PSModulePath`。</span><span class="sxs-lookup"><span data-stu-id="cf105-169">For more information, see `PSModulePath` in [about_Environment_Variables](/powershell/module/microsoft.powershell.core/about/about_environment_variables#environment-variables-that-store-preferences).</span></span>

<span data-ttu-id="cf105-170">如需有關模組的詳細資訊，請參閱 [about_Modules](/powershell/module/Microsoft.PowerShell.Core/About/about_Modules)。</span><span class="sxs-lookup"><span data-stu-id="cf105-170">For more information about Modules, see [about_Modules](/powershell/module/Microsoft.PowerShell.Core/About/about_Modules).</span></span>

### <a name="separate-profiles"></a><span data-ttu-id="cf105-171">個別設定檔</span><span class="sxs-lookup"><span data-stu-id="cf105-171">Separate profiles</span></span>

<span data-ttu-id="cf105-172">PowerShell 設定檔是在 PowerShell 啟動時執行的指令碼。</span><span class="sxs-lookup"><span data-stu-id="cf105-172">A PowerShell profile is a script that executes when PowerShell starts.</span></span> <span data-ttu-id="cf105-173">此指令碼會藉由新增命令、別名、函式、變數、模組和 PowerShell 磁碟機，以自訂您的環境。</span><span class="sxs-lookup"><span data-stu-id="cf105-173">This script customizes your environment by adding commands, aliases, functions, variables, modules, and PowerShell drives.</span></span> <span data-ttu-id="cf105-174">設定檔指令碼可讓您在每個工作階段中使用這些自訂項目，而不必手動重新建立。</span><span class="sxs-lookup"><span data-stu-id="cf105-174">The profile script makes these customizations available in every session without having to manually recreate them.</span></span>

<span data-ttu-id="cf105-175">在 PowerShell 7 中，設定檔位置的路徑已變更。</span><span class="sxs-lookup"><span data-stu-id="cf105-175">The path to the location of the profile has changed in PowerShell 7.</span></span>

- <span data-ttu-id="cf105-176">在 Windows PowerShell 5.1 中，設定檔的位置是 `$HOME\Documents\WindowsPowerShell`。</span><span class="sxs-lookup"><span data-stu-id="cf105-176">In Windows PowerShell 5.1, the location of the profile is `$HOME\Documents\WindowsPowerShell`.</span></span>
- <span data-ttu-id="cf105-177">在 PowerShell 7 中，設定檔的位置是 `$HOME\Documents\PowerShell`。</span><span class="sxs-lookup"><span data-stu-id="cf105-177">In PowerShell 7, the location of the profile is `$HOME\Documents\PowerShell`.</span></span>

<span data-ttu-id="cf105-178">設定檔檔名也已變更：</span><span class="sxs-lookup"><span data-stu-id="cf105-178">The profile filenames have also changed:</span></span>

   ```powershell
   PS> $PROFILE | Select-Object *Host* | Format-List

   AllUsersAllHosts       : C:\Program Files\PowerShell\7\profile.ps1
   AllUsersCurrentHost    : C:\Program Files\PowerShell\7\Microsoft.PowerShell_profile.ps1
   CurrentUserAllHosts    : C:\Users\<user>\Documents\PowerShell\profile.ps1
   CurrentUserCurrentHost : C:\Users\<user>\Documents\PowerShell\Microsoft.PowerShell_profile.ps1
   ```

<span data-ttu-id="cf105-179">如需詳細資訊，請參閱 [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)。</span><span class="sxs-lookup"><span data-stu-id="cf105-179">For more information [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span></span>

### <a name="powershell-7-compatibility-with-windows-powershell-51-modules"></a><span data-ttu-id="cf105-180">PowerShell 7 與 Windows PowerShell 5.1 模組的相容性</span><span class="sxs-lookup"><span data-stu-id="cf105-180">PowerShell 7 compatibility with Windows PowerShell 5.1 modules</span></span>

<span data-ttu-id="cf105-181">您在 Windows PowerShell 5.1 中使用的大部分模組都已經與 PowerShell 7 搭配使用，包括 Azure PowerShell 和 Active Directory。</span><span class="sxs-lookup"><span data-stu-id="cf105-181">Most of the modules you use in Windows PowerShell 5.1 already work with PowerShell 7, including Azure PowerShell and Active Directory.</span></span> <span data-ttu-id="cf105-182">我們會繼續與其他小組合作，以新增更多模組的原生 PowerShell 7 支援，包括 Microsoft Graph、Office 365 和其他模組。</span><span class="sxs-lookup"><span data-stu-id="cf105-182">We're continuing to work with other teams to add native PowerShell 7 support for more modules including Microsoft Graph, Office 365, and others.</span></span> <span data-ttu-id="cf105-183">如需目前支援模組的清單，請參閱 [PowerShell 7 模組相容性](/powershell/scripting/whats-new/module-compatibility)。</span><span class="sxs-lookup"><span data-stu-id="cf105-183">For the current list of supported modules, see [PowerShell 7 module compatibility](/powershell/scripting/whats-new/module-compatibility).</span></span>

> [!NOTE]
> <span data-ttu-id="cf105-184">在 Windows 上，我們也將 **UseWindowsPowerShell** 參數新增至 `Import-Module`，讓使用不相容模組的程式能夠更容易轉換至 PowerShell 7。</span><span class="sxs-lookup"><span data-stu-id="cf105-184">On Windows, we've also added a **UseWindowsPowerShell** switch to `Import-Module` to ease the transition to PowerShell 7 for those using incompatible modules.</span></span> <span data-ttu-id="cf105-185">如需此功能的詳細資訊，請參閱 [about_Windows_PowerShell_Compatibility](/powershell/module/Microsoft.PowerShell.Core/About/about_windows_powershell_compatibility)。</span><span class="sxs-lookup"><span data-stu-id="cf105-185">For more information on this functionality, see [about_Windows_PowerShell_Compatibility](/powershell/module/Microsoft.PowerShell.Core/About/about_windows_powershell_compatibility).</span></span>

### <a name="powershell-remoting"></a><span data-ttu-id="cf105-186">PowerShell 遠端功能</span><span class="sxs-lookup"><span data-stu-id="cf105-186">PowerShell Remoting</span></span>

<span data-ttu-id="cf105-187">PowerShell 遠端功能可讓您在一或多部遠端電腦上執行任何 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="cf105-187">PowerShell remoting lets you run any PowerShell command on one or more remote computers.</span></span> <span data-ttu-id="cf105-188">您可以建立持續連線、啟動互動式工作階段，以及在遠端電腦上執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="cf105-188">You can establish persistent connections, start interactive sessions, and run scripts on remote computers.</span></span>

#### <a name="ws-management-remoting"></a><span data-ttu-id="cf105-189">WS-MANAGEMENT 遠端功能</span><span class="sxs-lookup"><span data-stu-id="cf105-189">WS-Management remoting</span></span>

<span data-ttu-id="cf105-190">Windows PowerShell 5.1 和較舊版本使用 WS-Management (WSMAN) 通訊協定進行連線協商和資料傳輸。</span><span class="sxs-lookup"><span data-stu-id="cf105-190">Windows PowerShell 5.1 and below use the WS-Management (WSMAN) protocol for connection negotiation and data transport.</span></span> <span data-ttu-id="cf105-191">Windows 遠端管理 (WinRM) 使用 WSMAN 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="cf105-191">Windows Remote Management (WinRM) uses the WSMAN protocol.</span></span> <span data-ttu-id="cf105-192">如果已啟用 WinRM，PowerShell 7 會使用名為 `Microsoft.PowerShell` 的現有 Windows PowerShell 5.1 端點來進行遠端連線。</span><span class="sxs-lookup"><span data-stu-id="cf105-192">If WinRM has been enabled, PowerShell 7 uses the existing Windows PowerShell 5.1 endpoint named `Microsoft.PowerShell` for remoting connections.</span></span> <span data-ttu-id="cf105-193">若要更新 PowerShell 7 以包含其自己的端點，請執行 `Enable-PSRemoting` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cf105-193">To update PowerShell 7 to include its own endpoint, run the `Enable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="cf105-194">如需連線至特定端點的詳細資訊，請參閱 [PowerShell Core 中的 WS-Management 遠端功能](/powershell/scripting/learn/remoting/wsman-remoting-in-powershell-core)</span><span class="sxs-lookup"><span data-stu-id="cf105-194">For information about connecting to specific endpoints, see [WS-Management Remoting in PowerShell Core](/powershell/scripting/learn/remoting/wsman-remoting-in-powershell-core)</span></span>

<span data-ttu-id="cf105-195">若要使用 Windows PowerShell 遠端執行功能，必須針對遠端管理設定遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="cf105-195">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span>
<span data-ttu-id="cf105-196">如需包括指示的詳細資訊，請參閱[關於遠端需求](/powershell/module/microsoft.powershell.core/about/about_remote_requirements)。</span><span class="sxs-lookup"><span data-stu-id="cf105-196">For more information, including instructions, see [About Remote Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span></span>

<span data-ttu-id="cf105-197">如需有關使用遠端功能的詳細資訊，請參閱[關於遠端](/powershell/module/microsoft.powershell.core/about/about_remote)</span><span class="sxs-lookup"><span data-stu-id="cf105-197">For more information about working with remoting, see [About Remote](/powershell/module/microsoft.powershell.core/about/about_remote)</span></span>

#### <a name="ssh-based-remoting"></a><span data-ttu-id="cf105-198">以 SSH 為基礎的遠端功能</span><span class="sxs-lookup"><span data-stu-id="cf105-198">SSH-based remoting</span></span>

<span data-ttu-id="cf105-199">PowerShell Core 6.x 中已新增以 SSH 為基礎的遠端功能，以支援無法使用 Windows 原生元件 (例如 **WinRM**) 的其他作業系統。</span><span class="sxs-lookup"><span data-stu-id="cf105-199">SSH-based remoting was added in PowerShell Core 6.x to support other operating systems that can't use Windows native components like **WinRM**.</span></span> <span data-ttu-id="cf105-200">SSH 遠端功能會在目標電腦上建立 PowerShell 裝載處理序作為 SSH 子系統。</span><span class="sxs-lookup"><span data-stu-id="cf105-200">SSH remoting creates a PowerShell host process on the target computer as an SSH subsystem.</span></span> <span data-ttu-id="cf105-201">如需在 Windows 或 Linux 上設定以 SSH 為基礎的遠端功能的詳細資訊和範例，請參閱：[透過 SSH 的 PowerShell 遠端功能](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)</span><span class="sxs-lookup"><span data-stu-id="cf105-201">For details and examples on setting up SSH-based remoting on Windows or Linux, see: [PowerShell remoting over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

> [!NOTE]
> <span data-ttu-id="cf105-202">PowerShell 資源庫 (PSGallery) 包含可自動設定以 SSH 為基礎的遠端功能的模組和 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cf105-202">The PowerShell Gallery (PSGallery) contains a module and cmdlet that automatically configures SSH-based remoting.</span></span> <span data-ttu-id="cf105-203">從 [PSGallery](https://www.powershellgallery.com/packages/Microsoft.PowerShell.RemotingTools/0.1.0) 安裝 `Microsoft.PowerShell.RemotingTools` 模組，然後執行 `Enable-SSH` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cf105-203">Install the `Microsoft.PowerShell.RemotingTools` module from the [PSGallery](https://www.powershellgallery.com/packages/Microsoft.PowerShell.RemotingTools/0.1.0) and run the `Enable-SSH` cmdlet.</span></span>

<span data-ttu-id="cf105-204">`New-PSSession`、`Enter-PSSession` 和 `Invoke-Command` Cmdlet 都有新的參數集，可支援 SSH 連線。</span><span class="sxs-lookup"><span data-stu-id="cf105-204">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets have new parameter sets to support SSH connections.</span></span>

```powershell
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="cf105-205">若要建立遠端工作階段，請使用 **HostName** 參數來指定目標電腦，並使用 **UserName** 來提供使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="cf105-205">To create a remote session, specify the target computer with the **HostName** parameter and provide the user name with **UserName**.</span></span> <span data-ttu-id="cf105-206">以互動方式執行 Cmdlet 時，系統會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="cf105-206">When running the cmdlets interactively, you're prompted for a password.</span></span>

```powershell
Enter-PSSession -HostName <Computer> -UserName <Username>
```

<span data-ttu-id="cf105-207">或者，使用 **HostName** 參數時，請提供使用者名稱資訊，後面加上 @ 符號 ('@')，後面接著電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="cf105-207">Alternatively, when using the **HostName** parameter, provide the username information followed by the at sign ('@'), followed by the computer name.</span></span>

```powershell
Enter-PSSession -HostName <Username>@<Computer>
```

<span data-ttu-id="cf105-208">您可以搭配 **KeyFilePath** 參數使用私密金鑰檔案，來設定 SSH 金鑰驗證。</span><span class="sxs-lookup"><span data-stu-id="cf105-208">You may set up SSH key authentication using a private key file with the **KeyFilePath** parameter.</span></span>
<span data-ttu-id="cf105-209">如需詳細資訊，請參閱 [OpenSSH 金鑰管理](/windows-server/administration/openssh/openssh_keymanagement)。</span><span class="sxs-lookup"><span data-stu-id="cf105-209">For more information, see [OpenSSH Key Management](/windows-server/administration/openssh/openssh_keymanagement).</span></span>

### <a name="group-policy-supported"></a><span data-ttu-id="cf105-210">支援的群組原則</span><span class="sxs-lookup"><span data-stu-id="cf105-210">Group Policy supported</span></span>

<span data-ttu-id="cf105-211">PowerShell 包含群組原則設定，可協助您為企業環境中的伺服器定義一致的選項值。</span><span class="sxs-lookup"><span data-stu-id="cf105-211">PowerShell includes Group Policy settings to help you define consistent option values for servers in an enterprise environment.</span></span> <span data-ttu-id="cf105-212">這些設定包括：</span><span class="sxs-lookup"><span data-stu-id="cf105-212">These settings include:</span></span>

- <span data-ttu-id="cf105-213">主控台工作階段設定：設定 PowerShell 執行所在的設定端點。</span><span class="sxs-lookup"><span data-stu-id="cf105-213">Console session configuration: Sets a configuration endpoint in which PowerShell is run.</span></span>
- <span data-ttu-id="cf105-214">開啟模組記錄：設定模組的 LogPipelineExecutionDetails 屬性。</span><span class="sxs-lookup"><span data-stu-id="cf105-214">Turn on Module Logging: Sets the LogPipelineExecutionDetails property of modules.</span></span>
- <span data-ttu-id="cf105-215">開啟 PowerShell 指令碼區塊記錄：啟用所有 PowerShell 指令碼的詳細記錄。</span><span class="sxs-lookup"><span data-stu-id="cf105-215">Turn on PowerShell Script Block Logging: Enables detailed logging of all PowerShell scripts.</span></span>
- <span data-ttu-id="cf105-216">開啟指令碼執行：設定 PowerShell 執行原則。</span><span class="sxs-lookup"><span data-stu-id="cf105-216">Turn on Script Execution: Sets the PowerShell execution policy.</span></span>
- <span data-ttu-id="cf105-217">開啟 PowerShell 轉譯：將 PowerShell 命令的輸入和輸出，擷取到以文字為基礎的文字記錄。</span><span class="sxs-lookup"><span data-stu-id="cf105-217">Turn on PowerShell Transcription: enables capturing of input and output of PowerShell commands into text-based transcripts.</span></span>
- <span data-ttu-id="cf105-218">設定 Update-Help 的預設來源路徑：將「可更新的說明」來源設定為目錄，而不是網際網路。</span><span class="sxs-lookup"><span data-stu-id="cf105-218">Set the default source path for Update-Help: Sets the source for Updatable Help to a directory, not the Internet.</span></span>

<span data-ttu-id="cf105-219">如需詳細資訊，請參閱 [about_Group_Policy_Settings](/powershell/module/microsoft.powershell.core/about/about_group_policy_settings)。</span><span class="sxs-lookup"><span data-stu-id="cf105-219">For more information, see [about_Group_Policy_Settings](/powershell/module/microsoft.powershell.core/about/about_group_policy_settings).</span></span>

<span data-ttu-id="cf105-220">PowerShell 7 包含群組原則範本，以及 `$PSHOME` 中的安裝指令碼。</span><span class="sxs-lookup"><span data-stu-id="cf105-220">PowerShell 7 includes Group Policy templates and an installation script in `$PSHOME`.</span></span>

<span data-ttu-id="cf105-221">群組原則工具會使用系統管理範本檔案 (`.admx`、`.adml`)，在使用者介面中填入原則設定。</span><span class="sxs-lookup"><span data-stu-id="cf105-221">Group Policy tools use administrative template files (`.admx`, `.adml`) to populate policy settings in the user interface.</span></span> <span data-ttu-id="cf105-222">這樣可讓系統管理員管理以登錄為基礎的原則設定。</span><span class="sxs-lookup"><span data-stu-id="cf105-222">This allows administrators to manage registry-based policy settings.</span></span> <span data-ttu-id="cf105-223">`InstallPSCorePolicyDefinitions.ps1` 指令碼會在本機電腦上安裝 PowerShell Core 系統管理範本。</span><span class="sxs-lookup"><span data-stu-id="cf105-223">The `InstallPSCorePolicyDefinitions.ps1` script installs PowerShell Core Administrative Templates on the local machine.</span></span>

```powershell
Get-ChildItem -Path $PSHOME -Filter *Core*Policy*
```

```Output
    Directory: C:\Program Files\PowerShell\7

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/27/2020 12:38 AM          15861 InstallPSCorePolicyDefinitions.ps1
-a---           2/27/2020 12:28 AM           9675 PowerShellCoreExecutionPolicy.adml
-a---           2/27/2020 12:28 AM           6201 PowerShellCoreExecutionPolicy.admx
```

### <a name="separate-event-logs"></a><span data-ttu-id="cf105-224">個別事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="cf105-224">Separate Event Logs</span></span>

<span data-ttu-id="cf105-225">Windows PowerShell 和 PowerShell 7 將事件記錄到個別事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="cf105-225">Windows PowerShell and PowerShell 7 log events to separate event logs.</span></span> <span data-ttu-id="cf105-226">使用下列命令來取得 PowerShell 記錄的清單。</span><span class="sxs-lookup"><span data-stu-id="cf105-226">Use the following command to get a list of the PowerShell logs.</span></span>

```powershell
Get-WinEvent -ListLog *PowerShell*
```

<span data-ttu-id="cf105-227">如需詳細資訊，請參閱 [about_Logging_Windows](/powershell/module/microsoft.powershell.core/about/about_logging_windows)。</span><span class="sxs-lookup"><span data-stu-id="cf105-227">For more information, see [about_Logging_Windows](/powershell/module/microsoft.powershell.core/about/about_logging_windows).</span></span>

## <a name="improved-editing-experience-with-visual-studio-code"></a><span data-ttu-id="cf105-228">改善 Visual Studio Code 的編輯體驗</span><span class="sxs-lookup"><span data-stu-id="cf105-228">Improved editing experience with Visual Studio Code</span></span>

<span data-ttu-id="cf105-229">[Visual Studio Code (VSCode)](https://code.visualstudio.com/) 與 [PowerShell 延伸模組](https://code.visualstudio.com/docs/languages/powershell)是 PowerShell 7 的支援指令碼環境。</span><span class="sxs-lookup"><span data-stu-id="cf105-229">[Visual Studio Code (VSCode)](https://code.visualstudio.com/) with the [PowerShell Extension](https://code.visualstudio.com/docs/languages/powershell) is the supported scripting environment for PowerShell 7.</span></span> <span data-ttu-id="cf105-230">Windows PowerShell 整合式指令碼環境 (ISE) 僅支援 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="cf105-230">The Windows PowerShell Integrated Scripting Environment (ISE) only supports Windows PowerShell.</span></span>

<span data-ttu-id="cf105-231">更新的 PowerShell 延伸模組包括：</span><span class="sxs-lookup"><span data-stu-id="cf105-231">The updated PowerShell extension includes:</span></span>

- <span data-ttu-id="cf105-232">新的 ISE 相容性模式</span><span class="sxs-lookup"><span data-stu-id="cf105-232">New ISE compatibility mode</span></span>
- <span data-ttu-id="cf105-233">整合式主控台中的 PSReadLine，包括語法醒目提示、多行編輯和上一頁搜尋</span><span class="sxs-lookup"><span data-stu-id="cf105-233">PSReadLine in the Integrated Console, including syntax highlighting, multi-line editing, and back search</span></span>
- <span data-ttu-id="cf105-234">穩定性與效能提升</span><span class="sxs-lookup"><span data-stu-id="cf105-234">Stability and performance improvements</span></span>
- <span data-ttu-id="cf105-235">新的 CodeLens 整合</span><span class="sxs-lookup"><span data-stu-id="cf105-235">New CodeLens integration</span></span>
- <span data-ttu-id="cf105-236">已改善路徑自動完成</span><span class="sxs-lookup"><span data-stu-id="cf105-236">Improved path auto-completion</span></span>

<span data-ttu-id="cf105-237">若要更輕鬆地轉換為 Visual Studio Code，請使用 [命令選擇區]  中提供的 **Enable ISE Mode** 函式。</span><span class="sxs-lookup"><span data-stu-id="cf105-237">To make the transition to Visual Studio Code easier, use the **Enable ISE Mode** function available in the **Command Palette**.</span></span> <span data-ttu-id="cf105-238">此函式會將 VSCode 切換為 ISE 樣式配置。</span><span class="sxs-lookup"><span data-stu-id="cf105-238">This function switches VSCode into an ISE-style layout.</span></span> <span data-ttu-id="cf105-239">ISE 樣式配置以熟悉的使用者體驗，為您提供 PowerShell 的所有新特性和功能。</span><span class="sxs-lookup"><span data-stu-id="cf105-239">The ISE-style layout gives you all the new features and capabilities of PowerShell in a familiar user experience.</span></span>

<span data-ttu-id="cf105-240">若要切換至新的 ISE 配置，請按 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> 以開啟 [命令選擇區]  ，輸入 `PowerShell` 並選取 [**PowerShell：啟用 ISE 模式**]。</span><span class="sxs-lookup"><span data-stu-id="cf105-240">To switch to the new ISE layout, press <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> to open the **Command Palette**, type `PowerShell` and select **PowerShell: Enable ISE Mode**.</span></span>

<span data-ttu-id="cf105-241">若要將配置設定為原始配置，請開啟 [命令選擇區]  ，然後選取 [**PowerShell：停用 ISE 模式 (還原為預設值)** ]。</span><span class="sxs-lookup"><span data-stu-id="cf105-241">To set the layout to the original layout, open the **Command Palette**, select **PowerShell: Disable ISE Mode (restore to defaults)**.</span></span>

<span data-ttu-id="cf105-242">如需有關自訂 VSCode 配置至 ISE 的詳細資訊，請參閱[如何在 Visual Studio Code 中複寫 ISE 體驗](/powershell/scripting/components/vscode/how-to-replicate-the-ise-experience-in-vscode)</span><span class="sxs-lookup"><span data-stu-id="cf105-242">For details about customizing the VSCode layout to ISE, see [How to Replicate the ISE Experience in Visual Studio Code](/powershell/scripting/components/vscode/how-to-replicate-the-ise-experience-in-vscode)</span></span>

> [!NOTE]
> <span data-ttu-id="cf105-243">沒有計劃要以新功能更新 ISE。</span><span class="sxs-lookup"><span data-stu-id="cf105-243">There no plans to update the ISE with new features.</span></span> <span data-ttu-id="cf105-244">ISE 現在是最新版本 Windows 10 和 Windows Server 中的使用者可解除安裝功能。</span><span class="sxs-lookup"><span data-stu-id="cf105-244">The ISE is now a user-uninstallable feature in the latest versions of Windows 10 and Windows Server.</span></span> <span data-ttu-id="cf105-245">沒有計劃要永久移除 ISE。</span><span class="sxs-lookup"><span data-stu-id="cf105-245">There are no plans to permanently remove the ISE.</span></span> <span data-ttu-id="cf105-246">PowerShell 小組及其合作夥伴著重於改善適用於 Visual Studio Code 的 PowerShell 延伸模組指令碼體驗。</span><span class="sxs-lookup"><span data-stu-id="cf105-246">The PowerShell Team and its partners are focused on improving the scripting experience in the PowerShell extension for Visual Studio Code.</span></span>

## <a name="next-steps"></a><span data-ttu-id="cf105-247">後續步驟</span><span class="sxs-lookup"><span data-stu-id="cf105-247">Next Steps</span></span>

<span data-ttu-id="cf105-248">有了有效遷移的知識，立即[安裝 PowerShell 7](/powershell/scripting/install/installing-powershell-core-on-windows)！</span><span class="sxs-lookup"><span data-stu-id="cf105-248">Armed with the knowledge to effectively migrate, [install PowerShell 7](/powershell/scripting/install/installing-powershell-core-on-windows) now!</span></span>
