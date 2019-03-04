---
title: 安裝 PowerShell 模組 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb82827e-fdb7-4cbf-b3d4-093e72b3ff0e
caps.latest.revision: 28
ms.openlocfilehash: f7899713dd273b793017adfa0a20b3ff3352b62a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862164"
---
# <a name="installing-a-powershell-module"></a><span data-ttu-id="e574d-102">安裝 PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="e574d-102">Installing a PowerShell Module</span></span>

<span data-ttu-id="e574d-103">您已建立您的 PowerShell 模組之後，您可能會想，在系統上，安裝模組，讓您或其他人可能會使用它。</span><span class="sxs-lookup"><span data-stu-id="e574d-103">After you have created your PowerShell module, you will likely want to install the module on a system, so that you or others may use it.</span></span> <span data-ttu-id="e574d-104">一般而言，這只是包含複製的模組檔案 （亦即，.psm1，或二進位組件、 模組資訊清單和任何相關聯的檔案） 至目錄在該電腦上。</span><span class="sxs-lookup"><span data-stu-id="e574d-104">Generally speaking, this simply consists of copying the module files (ie, the .psm1, or the binary assembly, the module manifest, and any other associated files) onto a directory on that computer.</span></span> <span data-ttu-id="e574d-105">對於非常小的專案中，這可能是簡單，只要複製並貼上與 Windows 檔案總管檔案到單一遠端電腦;不過，較大的解決方案，您可能想要使用更複雜的安裝程序。</span><span class="sxs-lookup"><span data-stu-id="e574d-105">For a very small project, this may be as simple as copying and pasting the files with Windows Explorer onto a single remote computer; however, for larger solutions you may wish to use a more sophisticated installation process.</span></span> <span data-ttu-id="e574d-106">不論如何，您會取得您系統上的模組，PowerShell 可以使用一些技巧，讓使用者尋找並使用您的模組。</span><span class="sxs-lookup"><span data-stu-id="e574d-106">Regardless of how you get your module onto the system, PowerShell can use a number of techniques that will let users find and use your modules.</span></span> <span data-ttu-id="e574d-107">(如需詳細資訊，請參閱 <<c0> [ 匯入 PowerShell 模組](./importing-a-powershell-module.md)。)因此，安裝的主要問題確保 PowerShell 能夠找到您的模組。</span><span class="sxs-lookup"><span data-stu-id="e574d-107">(For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).) Therefore, the main issue for installation is ensuring that PowerShell will be able to find your module.</span></span>

<span data-ttu-id="e574d-108">本主題涵蓋下列各節：</span><span class="sxs-lookup"><span data-stu-id="e574d-108">This topic contains the following sections:</span></span>

- <span data-ttu-id="e574d-109">安裝模組的規則</span><span class="sxs-lookup"><span data-stu-id="e574d-109">Rules for Installing Modules</span></span>

- <span data-ttu-id="e574d-110">如何安裝模組</span><span class="sxs-lookup"><span data-stu-id="e574d-110">Where to Install Modules</span></span>

- <span data-ttu-id="e574d-111">安裝模組的多個版本</span><span class="sxs-lookup"><span data-stu-id="e574d-111">Installing Multiple Versions of a Module</span></span>

- <span data-ttu-id="e574d-112">處理命令名稱衝突</span><span class="sxs-lookup"><span data-stu-id="e574d-112">Handling Command Name Conflicts</span></span>

## <a name="rules-for-installing-modules"></a><span data-ttu-id="e574d-113">安裝模組的規則</span><span class="sxs-lookup"><span data-stu-id="e574d-113">Rules for Installing Modules</span></span>

<span data-ttu-id="e574d-114">下列資訊與所有模組，包括您建立您自己使用，您從其他合作對象，取得的模組和模組散發給其他人的模組。</span><span class="sxs-lookup"><span data-stu-id="e574d-114">The following information pertains to all modules, including modules that you create for your own use, modules that you get from other parties, and modules that you distribute to others.</span></span>

### <a name="install-modules-in-psmodulepath"></a><span data-ttu-id="e574d-115">在 PSModulePath 中安裝模組</span><span class="sxs-lookup"><span data-stu-id="e574d-115">Install Modules in PSModulePath</span></span>

<span data-ttu-id="e574d-116">可能的話，則安裝所有模組中所列路徑中**PSModulePath**環境變數或新增的模組路徑**PSModulePath**環境變數的值。</span><span class="sxs-lookup"><span data-stu-id="e574d-116">Whenever possible, install all modules in a path that is listed in the **PSModulePath** environment variable or add the module path to the **PSModulePath** environment variable value.</span></span>

<span data-ttu-id="e574d-117">**PSModulePath**環境變數 ($Env: PSModulePath) 包含 Windows PowerShell 模組的位置。</span><span class="sxs-lookup"><span data-stu-id="e574d-117">The **PSModulePath** environment variable ($Env:PSModulePath) contains the locations of Windows PowerShell modules.</span></span> <span data-ttu-id="e574d-118">指令程式會依賴此環境變數的值來尋找模組。</span><span class="sxs-lookup"><span data-stu-id="e574d-118">Cmdlets rely on the value of this environment variable to find modules.</span></span>

<span data-ttu-id="e574d-119">根據預設， **PSModulePath**環境變數的值包含下列的系統和使用者的模組目錄，但您可以加入和編輯值。</span><span class="sxs-lookup"><span data-stu-id="e574d-119">By default, the **PSModulePath** environment variable value contains the following system and user module directories, but you can add to and edit the value.</span></span>

- <span data-ttu-id="e574d-120">$PSHome\Modules (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span><span class="sxs-lookup"><span data-stu-id="e574d-120">$PSHome\Modules (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span></span>

  > [!WARNING]
  > <span data-ttu-id="e574d-121">此位置會保留給 Windows 隨附的模組。</span><span class="sxs-lookup"><span data-stu-id="e574d-121">This location is reserved for modules that ship with Windows.</span></span> <span data-ttu-id="e574d-122">請勿將模組安裝到這個位置。</span><span class="sxs-lookup"><span data-stu-id="e574d-122">Do not install modules to this location.</span></span>

- <span data-ttu-id="e574d-123">$ Home\Documents\WindowsPowerShell\Modules (%userprofile%\documents\windowspowershell\modules)</span><span class="sxs-lookup"><span data-stu-id="e574d-123">$Home\Documents\WindowsPowerShell\Modules (%UserProfile%\Documents\WindowsPowerShell\Modules)</span></span>

- <span data-ttu-id="e574d-124">$Env: ProgramFiles\WindowsPowerShell\Modules (%programfiles%\windowspowershell\modules)</span><span class="sxs-lookup"><span data-stu-id="e574d-124">$Env:ProgramFiles\WindowsPowerShell\Modules (%ProgramFiles%\WindowsPowerShell\Modules)</span></span>

  <span data-ttu-id="e574d-125">若要取得的值**PSModulePath**環境變數，使用下列命令。</span><span class="sxs-lookup"><span data-stu-id="e574d-125">To get the value of the **PSModulePath** environment variable, use either of the following commands.</span></span>

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  <span data-ttu-id="e574d-126">若要加入的值中的模組路徑**PSModulePath**環境變數值，請使用下列命令格式。</span><span class="sxs-lookup"><span data-stu-id="e574d-126">To add a module path to value of the **PSModulePath** environment variable value, use the following command format.</span></span> <span data-ttu-id="e574d-127">此格式會使用**SetEnvironmentVariable**方法**System.Environment**類別，以獨立於工作階段的變更**PSModulePath**環境變數。</span><span class="sxs-lookup"><span data-stu-id="e574d-127">This format uses the **SetEnvironmentVariable** method of the **System.Environment** class to make a session-independent change to the **PSModulePath** environment variable.</span></span>

  ```powershell

  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > <span data-ttu-id="e574d-128">一旦您加入的路徑**PSModulePath**，您應該廣播與變更相關的環境訊息。</span><span class="sxs-lookup"><span data-stu-id="e574d-128">Once you have added the path to **PSModulePath**, you should broadcast an environment message about the change.</span></span> <span data-ttu-id="e574d-129">廣播變更可讓其他應用程式，例如殼層，來取得變更。</span><span class="sxs-lookup"><span data-stu-id="e574d-129">Broadcasting the change allows other applications, such as the shell, to pick up the change.</span></span> <span data-ttu-id="e574d-130">若要廣播變更，已傳送您產品的安裝程式碼**WM_SETTINGCHANGE**訊息，其`lParam`設為 「 環境 」 的字串。</span><span class="sxs-lookup"><span data-stu-id="e574d-130">To broadcast the change, have your product installation code send a **WM_SETTINGCHANGE** message with `lParam` set to the string "Environment".</span></span> <span data-ttu-id="e574d-131">傳送訊息之後已更新您的模組安裝程式碼，請務必**PSModulePath**。</span><span class="sxs-lookup"><span data-stu-id="e574d-131">Be sure to send the message after your module installation code has updated **PSModulePath**.</span></span>

### <a name="use-the-correct-module-directory-name"></a><span data-ttu-id="e574d-132">使用正確的模組目錄名稱</span><span class="sxs-lookup"><span data-stu-id="e574d-132">Use the Correct Module Directory Name</span></span>

<span data-ttu-id="e574d-133">「 語式正確的 「 模組是儲存在模組目錄中的至少一個檔案的基底名稱與同名的目錄中的模組。</span><span class="sxs-lookup"><span data-stu-id="e574d-133">A "well-formed" module is a module that is stored in a directory that has the same name as the base name of at least one file in the module directory.</span></span> <span data-ttu-id="e574d-134">如果模組不是語式正確的 Windows PowerShell 無法辨識其為模組。</span><span class="sxs-lookup"><span data-stu-id="e574d-134">If a module is not well-formed, Windows PowerShell does not recognize it as a module.</span></span>

<span data-ttu-id="e574d-135">檔案的 「 基底名稱 」 是不含副檔名的名稱。</span><span class="sxs-lookup"><span data-stu-id="e574d-135">The "base name" of a file is the name without the file name extension.</span></span> <span data-ttu-id="e574d-136">語式正確的模組中包含的模組檔案的目錄名稱必須符合模組中至少一個檔案的基底名稱。</span><span class="sxs-lookup"><span data-stu-id="e574d-136">In a well-formed module, the name of the directory that contains the module files must match the base name of at least one file in the module.</span></span>

<span data-ttu-id="e574d-137">比方說，在 Fabrikam 模組範例包含的模組檔案的目錄名為"Fabrikam"，至少一個檔案的"Fabrikam"基底名稱。</span><span class="sxs-lookup"><span data-stu-id="e574d-137">For example, in the sample Fabrikam module, the directory that contains the module files is named "Fabrikam" and at least one file has the "Fabrikam" base name.</span></span> <span data-ttu-id="e574d-138">在此情況下，Fabrikam.psd1 和 Fabrikam.dll 有"Fabrikam"基底名稱。</span><span class="sxs-lookup"><span data-stu-id="e574d-138">In this case, both Fabrikam.psd1 and Fabrikam.dll have the "Fabrikam" base name.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a><span data-ttu-id="e574d-139">安裝錯誤的影響</span><span class="sxs-lookup"><span data-stu-id="e574d-139">Effect of Incorrect Installation</span></span>

<span data-ttu-id="e574d-140">如果模組不是語式正確，而且它的位置不會納入的值**PSModulePath**環境變數，如下所示，Windows PowerShell 中，基本的探索功能無法運作。</span><span class="sxs-lookup"><span data-stu-id="e574d-140">If the module is not well-formed and its location is not included in the value of the **PSModulePath** environment variable, basic discovery features of Windows PowerShell, such as the following, do not work.</span></span>

- <span data-ttu-id="e574d-141">模組自動載入功能無法自動匯入模組。</span><span class="sxs-lookup"><span data-stu-id="e574d-141">The Module Auto-Loading feature cannot import the module automatically.</span></span>

- <span data-ttu-id="e574d-142">`ListAvailable`的參數[Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet 找不到模組。</span><span class="sxs-lookup"><span data-stu-id="e574d-142">The `ListAvailable` parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet cannot find the module.</span></span>

- <span data-ttu-id="e574d-143">[Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet 找不到模組。</span><span class="sxs-lookup"><span data-stu-id="e574d-143">The [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet cannot find the module.</span></span> <span data-ttu-id="e574d-144">若要匯入模組，您必須提供根模組檔案或模組資訊清單檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="e574d-144">To import the module, you must provide the full path to the root module file or module manifest file.</span></span>

  <span data-ttu-id="e574d-145">其他功能，例如下列程式碼，將無法運作除非模組匯入工作階段。</span><span class="sxs-lookup"><span data-stu-id="e574d-145">Additional features, such as the following, do not work unless the module is imported into the session.</span></span> <span data-ttu-id="e574d-146">語式正確的模組中**PSModulePath**環境變數，這些功能運作，即使模組不會匯入工作階段。</span><span class="sxs-lookup"><span data-stu-id="e574d-146">In well-formed modules in the **PSModulePath** environment variable, these features work even when the module is not imported into the session.</span></span>

- <span data-ttu-id="e574d-147">[Get-command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet 模組中找不到命令。</span><span class="sxs-lookup"><span data-stu-id="e574d-147">The [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet cannot find commands in the module.</span></span>

- <span data-ttu-id="e574d-148">[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)並[Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet 無法更新或儲存模組的說明。</span><span class="sxs-lookup"><span data-stu-id="e574d-148">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets cannot update or save help for the module.</span></span>

- <span data-ttu-id="e574d-149">[Show-command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet 無法尋找並顯示在模組中的命令。</span><span class="sxs-lookup"><span data-stu-id="e574d-149">The [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet cannot find and display the commands in the module.</span></span>

  <span data-ttu-id="e574d-150">模組中的命令中遺漏的`Show-Command`視窗在 Windows PowerShell 整合式指令碼環境 (ISE)。</span><span class="sxs-lookup"><span data-stu-id="e574d-150">The commands in the module are missing from the `Show-Command` window in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="where-to-install-modules"></a><span data-ttu-id="e574d-151">如何安裝模組</span><span class="sxs-lookup"><span data-stu-id="e574d-151">Where to Install Modules</span></span>

<span data-ttu-id="e574d-152">本節說明在何處安裝 Windows PowerShell 模組的檔案系統中。</span><span class="sxs-lookup"><span data-stu-id="e574d-152">This section explains where in the file system to install Windows PowerShell modules.</span></span> <span data-ttu-id="e574d-153">位置取決於如何使用模組。</span><span class="sxs-lookup"><span data-stu-id="e574d-153">The location depends on how the module is used.</span></span>

### <a name="installing-modules-for-a-specific-user"></a><span data-ttu-id="e574d-154">適用於特定使用者安裝的模組</span><span class="sxs-lookup"><span data-stu-id="e574d-154">Installing Modules for a Specific User</span></span>

<span data-ttu-id="e574d-155">如果您建立您自己的模組，或從另一個合作對象，例如 Windows PowerShell 社群網站，取得模組，您想要的模組，可供您的使用者帳戶只能安裝模組，在使用者專屬的 Modules 目錄中。</span><span class="sxs-lookup"><span data-stu-id="e574d-155">If you create your own module or get a module from another party, such as a Windows PowerShell community website, and you want the module to be available for your user account only, install the module in your user-specific Modules directory.</span></span>

```
$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

<span data-ttu-id="e574d-156">使用者專屬 Modules 目錄加入至值**PSModulePath**預設的環境變數。</span><span class="sxs-lookup"><span data-stu-id="e574d-156">The user-specific Modules directory is added to the value of the **PSModulePath** environment variable by default.</span></span>

### <a name="installing-modules-for-all-users-in-program-files"></a><span data-ttu-id="e574d-157">安裝程式檔案中的所有使用者的模組</span><span class="sxs-lookup"><span data-stu-id="e574d-157">Installing Modules for all Users in Program Files</span></span>

<span data-ttu-id="e574d-158">如果您想要可供電腦上的所有使用者帳戶的模組，請在程式檔案的位置安裝模組。</span><span class="sxs-lookup"><span data-stu-id="e574d-158">If you want a module to be available to all user accounts on the computer, install the module in the Program Files location.</span></span>

```
$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

> [!NOTE]
> <span data-ttu-id="e574d-159">程式檔案的位置加入 PSModulePath 環境變數的值，根據預設，在 Windows PowerShell 4.0 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="e574d-159">The Program Files location is added to the value of the PSModulePath environment variable by default in Windows PowerShell 4.0 and later.</span></span> <span data-ttu-id="e574d-160">對於舊版的 Windows PowerShell 中，可以手動建立的程式檔案位置 ((%ProgramFiles%\WindowsPowerShell\Modules) 並將此路徑新增至 PSModulePath 環境變數，如上面所述。</span><span class="sxs-lookup"><span data-stu-id="e574d-160">For earlier versions of Windows PowerShell, you can manually create the Program Files location ((%ProgramFiles%\WindowsPowerShell\Modules) and add this path to your PSModulePath environment variable as described above.</span></span>

### <a name="installing-modules-in-a-product-directory"></a><span data-ttu-id="e574d-161">產品目錄中安裝模組</span><span class="sxs-lookup"><span data-stu-id="e574d-161">Installing Modules in a Product Directory</span></span>

<span data-ttu-id="e574d-162">在散發給其他對象的模組時，如果使用上面所述的預設程式檔案位置，或建立您自己公司專屬或產品特定子目錄的 %programfiles%目錄。</span><span class="sxs-lookup"><span data-stu-id="e574d-162">If you are distributing the module to other parties, use the default Program Files location described above, or create your own company-specific or product-specific subdirectory of the %ProgramFiles% directory.</span></span>

<span data-ttu-id="e574d-163">例如，Fabrikam 技術，這家虛構公司的會出貨 Fabrikam Manager 產品的 Windows PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="e574d-163">For example, Fabrikam Technologies, a fictitious company, is shipping a Windows PowerShell module for their Fabrikam Manager product.</span></span> <span data-ttu-id="e574d-164">其模組安裝程式會建立模組子目錄，Fabrikam Manager 產品子目錄中。</span><span class="sxs-lookup"><span data-stu-id="e574d-164">Their module installer creates a Modules subdirectory in the Fabrikam Manager product subdirectory.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

<span data-ttu-id="e574d-165">若要啟用 Windows PowerShell 模組探索功能，若要尋找 Fabrikam 模組，Fabrikam 模組安裝程式會將模組位置的值**PSModulePath**環境變數。</span><span class="sxs-lookup"><span data-stu-id="e574d-165">To enable the Windows PowerShell module discovery features to find the Fabrikam module, the Fabrikam module installer adds the module location to the value of the **PSModulePath** environment variable.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += "C:\Program Files\Fabrikam Technolgies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a><span data-ttu-id="e574d-166">在 [Common Files] 目錄中安裝模組</span><span class="sxs-lookup"><span data-stu-id="e574d-166">Installing Modules in the Common Files Directory</span></span>

<span data-ttu-id="e574d-167">如果模組使用由多個元件的產品或產品的多個版本，請 %ProgramFiles%\Common Files\Modules 子目錄的特定模組的子目錄中安裝模組。</span><span class="sxs-lookup"><span data-stu-id="e574d-167">If a module is used by multiple components of a product or by multiple versions of a product, install the module in a module-specific subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span>

<span data-ttu-id="e574d-168">在下列範例中，Fabrikam 模組會安裝在 Fabrikam %ProgramFiles%\Common Files\Modules 子目錄的子目錄。</span><span class="sxs-lookup"><span data-stu-id="e574d-168">In the following example, the Fabrikam module is installed in a Fabrikam subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span> <span data-ttu-id="e574d-169">請注意每個模組都位於自己的模組子目錄中的子目錄。</span><span class="sxs-lookup"><span data-stu-id="e574d-169">Note that each module resides in its own subdirectory in the Modules subdirectory.</span></span>

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)

```

<span data-ttu-id="e574d-170">然後，安裝程式可確保 windows 7 **PSModulePath**環境變數包含一般的檔案模組子目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="e574d-170">Then, the installer assures the value of the **PSModulePath** environment variable includes the path of the common files modules subdirectory.</span></span>

```powershell
$m = $env:ProgramFiles + '\Common Files\Modules'
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$q = $p -split ';'
if ($q -notContains $m) {
    $q += ";$m"
}
$p = $q -join ';'
[Environment]::SetEnvironmentVariable("PSModulePath", $p)
```

## <a name="installing-multiple-versions-of-a-module"></a><span data-ttu-id="e574d-171">安裝模組的多個版本</span><span class="sxs-lookup"><span data-stu-id="e574d-171">Installing Multiple Versions of a Module</span></span>

<span data-ttu-id="e574d-172">若要安裝之相同模組的多個版本，請使用下列程序。</span><span class="sxs-lookup"><span data-stu-id="e574d-172">To install multiple versions of the same module, use the following procedure.</span></span>

1. <span data-ttu-id="e574d-173">建立每個版本的模組目錄。</span><span class="sxs-lookup"><span data-stu-id="e574d-173">Create a directory for each version of the module.</span></span> <span data-ttu-id="e574d-174">目錄名稱中包含的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="e574d-174">Include the version number in the directory name.</span></span>

2. <span data-ttu-id="e574d-175">建立模組的每個版本的模組資訊清單。</span><span class="sxs-lookup"><span data-stu-id="e574d-175">Create a module manifest for each version of the module.</span></span> <span data-ttu-id="e574d-176">中的值**ModuleVersion**金鑰資訊清單中，請輸入模組的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="e574d-176">In the value of the **ModuleVersion** key in the manifest, enter the module version number.</span></span> <span data-ttu-id="e574d-177">模組的版本特定目錄中儲存資訊清單檔案 (.psd1)。</span><span class="sxs-lookup"><span data-stu-id="e574d-177">Save the manifest file (.psd1) in the version-specific directory for the module.</span></span>

3. <span data-ttu-id="e574d-178">將模組的根資料夾路徑新增至 windows 7 **PSModulePath**環境變數，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e574d-178">Add the module root folder path to the value of the **PSModulePath** environment variable, as shown in the following examples.</span></span>

<span data-ttu-id="e574d-179">若要匯入特定版本的模組，使用者可以使用`MinimumVersion`或是`RequiredVersion`的參數[Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e574d-179">To import a particular version of the module, the end-user can use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="e574d-180">例如，Fabrikam 模組是否可在 8.0 及 9.0 版本中，Fabrikam 的模組目錄結構可能會如下所示。</span><span class="sxs-lookup"><span data-stu-id="e574d-180">For example, if the Fabrikam module is available in versions 8.0 and 9.0, the Fabrikam module directory structure might resemble the following.</span></span>

 ```
C:\Program Files
Fabrikam Manager
  Fabrikam8
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "8.0")
      Fabrikam.dll (module assembly)
  Fabrikam9
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "9.0")
      Fabrikam.dll (module assembly)
```

<span data-ttu-id="e574d-181">安裝程式將這兩個模組路徑**PSModulePath**環境變數的值。</span><span class="sxs-lookup"><span data-stu-id="e574d-181">The installer adds both of the module paths to the **PSModulePath** environment variable value.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

<span data-ttu-id="e574d-182">完成這些步驟時**ListAvailable**的參數[Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet 會取得這兩個 Fabrikam 模組。</span><span class="sxs-lookup"><span data-stu-id="e574d-182">When these steps are complete, the **ListAvailable** parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet gets both of the Fabrikam modules.</span></span> <span data-ttu-id="e574d-183">若要匯入特定模組，請使用`MiminumVersion`或是`RequiredVersion`的參數[Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e574d-183">To import a particular module, use the `MiminumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="e574d-184">如果這兩個模組匯入相同的工作階段中，模組會包含具有相同名稱的 cmdlet，最後匯入的 cmdlet 會在工作階段中有效。</span><span class="sxs-lookup"><span data-stu-id="e574d-184">If both modules are imported into the same session, and the modules contain cmdlets with the same names, the cmdlets that are imported last are effective in the session.</span></span>

## <a name="handling-command-name-conflicts"></a><span data-ttu-id="e574d-185">處理命令名稱衝突</span><span class="sxs-lookup"><span data-stu-id="e574d-185">Handling Command Name Conflicts</span></span>

<span data-ttu-id="e574d-186">模組匯出的命令會在使用者工作階段中的命令相同的名稱，就會發生命令名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="e574d-186">Command name conflicts can occur when the commands that a module exports have the same name as commands in the user's session.</span></span>

<span data-ttu-id="e574d-187">當工作階段包含兩個具有相同名稱的命令時，Windows PowerShell 會執行會優先使用的命令類型。</span><span class="sxs-lookup"><span data-stu-id="e574d-187">When a session contains two commands that have the same name, Windows PowerShell runs the command type that takes precedence.</span></span> <span data-ttu-id="e574d-188">當工作階段包含兩個具有相同名稱和相同類型的命令時，Windows PowerShell 就會執行已加入至最近的工作階段的命令。</span><span class="sxs-lookup"><span data-stu-id="e574d-188">When a session contains two commands that have the same name and the same type, Windows PowerShell runs the command that was added to the session most recently.</span></span> <span data-ttu-id="e574d-189">若要執行的命令，預設不會執行，使用者可以限定命令名稱的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="e574d-189">To run a command that is not run by default, users can qualify the command name with the module name.</span></span>

<span data-ttu-id="e574d-190">例如，如果工作階段包含`Get-Date`函式和`Get-Date`cmdlet，Windows PowerShell 預設會執行函式。</span><span class="sxs-lookup"><span data-stu-id="e574d-190">For example, if the session contains a `Get-Date` function and the `Get-Date` cmdlet, Windows PowerShell runs the function by default.</span></span> <span data-ttu-id="e574d-191">若要執行此 cmdlet，命令前面加上模組名稱，例如：</span><span class="sxs-lookup"><span data-stu-id="e574d-191">To run the cmdlet, preface the command with the module name, such as:</span></span>

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

<span data-ttu-id="e574d-192">若要避免名稱衝突，可以使用模組作者**DefaultCommandPrefix**從模組匯出的模組資訊清單來指定所有命令的名詞前置詞中的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="e574d-192">To prevent name conflicts, module authors can use the **DefaultCommandPrefix** key in the module manifest to specify a noun prefix for all commands exported from the module.</span></span>

<span data-ttu-id="e574d-193">使用者可以使用**前置詞**參數`Import-Module`cmdlet 以使用替代的前置詞。</span><span class="sxs-lookup"><span data-stu-id="e574d-193">Users can use the **Prefix** parameter of the `Import-Module` cmdlet to use an alternate prefix.</span></span> <span data-ttu-id="e574d-194">值**前置詞**參數的值會優先**DefaultCommandPrefix**索引鍵。</span><span class="sxs-lookup"><span data-stu-id="e574d-194">The value of the **Prefix** parameter takes precedence over the value of the **DefaultCommandPrefix** key.</span></span>

## <a name="see-also"></a><span data-ttu-id="e574d-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e574d-195">See Also</span></span>

[<span data-ttu-id="e574d-196">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="e574d-196">about_Command_Precedence</span></span>](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[<span data-ttu-id="e574d-197">撰寫 Windows PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="e574d-197">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
