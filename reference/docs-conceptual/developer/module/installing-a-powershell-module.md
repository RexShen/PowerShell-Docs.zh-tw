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
ms.openlocfilehash: 60ac4bf9089232a9fa879e835e32da53422489fd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367067"
---
# <a name="installing-a-powershell-module"></a><span data-ttu-id="8ed43-102">安裝 PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="8ed43-102">Installing a PowerShell Module</span></span>

<span data-ttu-id="8ed43-103">建立 PowerShell 模組之後，您可能會想要在系統上安裝模組，讓您或其他人可以使用它。</span><span class="sxs-lookup"><span data-stu-id="8ed43-103">After you have created your PowerShell module, you will likely want to install the module on a system, so that you or others may use it.</span></span> <span data-ttu-id="8ed43-104">一般來說，這是由將模組檔案（即 .psm1 或二進位元件、模組資訊清單，以及任何其他相關聯的檔案）複製到該電腦上的目錄。</span><span class="sxs-lookup"><span data-stu-id="8ed43-104">Generally speaking, this consists of copying the module files (ie, the .psm1, or the binary assembly, the module manifest, and any other associated files) onto a directory on that computer.</span></span> <span data-ttu-id="8ed43-105">對於非常小型的專案，這可能就像是將檔案以 Windows Explorer 複製並貼到單一遠端電腦一樣簡單;不過，對於較大型的解決方案，您可能會想要使用更複雜的安裝程式。</span><span class="sxs-lookup"><span data-stu-id="8ed43-105">For a very small project, this may be as simple as copying and pasting the files with Windows Explorer onto a single remote computer; however, for larger solutions you may wish to use a more sophisticated installation process.</span></span> <span data-ttu-id="8ed43-106">無論您如何將模組放入系統，PowerShell 都可以使用一些技術，讓使用者尋找和使用您的模組。</span><span class="sxs-lookup"><span data-stu-id="8ed43-106">Regardless of how you get your module onto the system, PowerShell can use a number of techniques that will let users find and use your modules.</span></span> <span data-ttu-id="8ed43-107">因此，安裝的主要問題是確保 PowerShell 能夠找到您的模組。</span><span class="sxs-lookup"><span data-stu-id="8ed43-107">Therefore, the main issue for installation is ensuring that PowerShell will be able to find your module.</span></span> <span data-ttu-id="8ed43-108">如需詳細資訊，請參閱匯[入 PowerShell 模組](./importing-a-powershell-module.md)。</span><span class="sxs-lookup"><span data-stu-id="8ed43-108">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="rules-for-installing-modules"></a><span data-ttu-id="8ed43-109">安裝模組的規則</span><span class="sxs-lookup"><span data-stu-id="8ed43-109">Rules for Installing Modules</span></span>

<span data-ttu-id="8ed43-110">下列資訊適用于所有模組，包括您為自己的用途所建立的模組、從其他方取得的模組，以及您散發給其他人的模組。</span><span class="sxs-lookup"><span data-stu-id="8ed43-110">The following information pertains to all modules, including modules that you create for your own use, modules that you get from other parties, and modules that you distribute to others.</span></span>

### <a name="install-modules-in-psmodulepath"></a><span data-ttu-id="8ed43-111">在 PSModulePath 中安裝模組</span><span class="sxs-lookup"><span data-stu-id="8ed43-111">Install Modules in PSModulePath</span></span>

<span data-ttu-id="8ed43-112">盡可能將所有模組安裝在**PSModulePath**環境變數中所列的路徑，或將模組路徑新增至**PSModulePath**環境變數值。</span><span class="sxs-lookup"><span data-stu-id="8ed43-112">Whenever possible, install all modules in a path that is listed in the **PSModulePath** environment variable or add the module path to the **PSModulePath** environment variable value.</span></span>

<span data-ttu-id="8ed43-113">**PSModulePath**環境變數（$Env:P smodulepath）包含 Windows PowerShell 模組的位置。</span><span class="sxs-lookup"><span data-stu-id="8ed43-113">The **PSModulePath** environment variable ($Env:PSModulePath) contains the locations of Windows PowerShell modules.</span></span> <span data-ttu-id="8ed43-114">Cmdlet 會依賴此環境變數的值來尋找模組。</span><span class="sxs-lookup"><span data-stu-id="8ed43-114">Cmdlets rely on the value of this environment variable to find modules.</span></span>

<span data-ttu-id="8ed43-115">根據預設， **PSModulePath**環境變數值包含下列系統和使用者模組目錄，但是您可以加入並編輯值。</span><span class="sxs-lookup"><span data-stu-id="8ed43-115">By default, the **PSModulePath** environment variable value contains the following system and user module directories, but you can add to and edit the value.</span></span>

- <span data-ttu-id="8ed43-116">`$PSHome\Modules` （%Windir%\System32\WindowsPowerShell\v1.0\Modules）</span><span class="sxs-lookup"><span data-stu-id="8ed43-116">`$PSHome\Modules` (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span></span>

  > [!WARNING]
  > <span data-ttu-id="8ed43-117">這個位置會保留給 Windows 隨附的模組。</span><span class="sxs-lookup"><span data-stu-id="8ed43-117">This location is reserved for modules that ship with Windows.</span></span> <span data-ttu-id="8ed43-118">請勿將模組安裝到這個位置。</span><span class="sxs-lookup"><span data-stu-id="8ed43-118">Do not install modules to this location.</span></span>

- <span data-ttu-id="8ed43-119">`$Home\Documents\WindowsPowerShell\Modules` （%UserProfile%\Documents\WindowsPowerShell\Modules）</span><span class="sxs-lookup"><span data-stu-id="8ed43-119">`$Home\Documents\WindowsPowerShell\Modules` (%UserProfile%\Documents\WindowsPowerShell\Modules)</span></span>

- <span data-ttu-id="8ed43-120">`$Env:ProgramFiles\WindowsPowerShell\Modules` （%ProgramFiles%\WindowsPowerShell\Modules）</span><span class="sxs-lookup"><span data-stu-id="8ed43-120">`$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\WindowsPowerShell\Modules)</span></span>

  <span data-ttu-id="8ed43-121">若要取得**PSModulePath**環境變數的值，請使用下列其中一個命令。</span><span class="sxs-lookup"><span data-stu-id="8ed43-121">To get the value of the **PSModulePath** environment variable, use either of the following commands.</span></span>

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  <span data-ttu-id="8ed43-122">若要將模組路徑新增至**PSModulePath**環境變數值的值，請使用下列命令格式。</span><span class="sxs-lookup"><span data-stu-id="8ed43-122">To add a module path to value of the **PSModulePath** environment variable value, use the following command format.</span></span> <span data-ttu-id="8ed43-123">此格式會使用**system.object**類別的**SetEnvironmentVariable**方法，對**PSModulePath**環境變數進行與會話無關的變更。</span><span class="sxs-lookup"><span data-stu-id="8ed43-123">This format uses the **SetEnvironmentVariable** method of the **System.Environment** class to make a session-independent change to the **PSModulePath** environment variable.</span></span>

  ```powershell
  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > <span data-ttu-id="8ed43-124">將路徑新增至**PSModulePath**之後，您應該廣播有關此變更的環境訊息。</span><span class="sxs-lookup"><span data-stu-id="8ed43-124">Once you have added the path to **PSModulePath**, you should broadcast an environment message about the change.</span></span> <span data-ttu-id="8ed43-125">廣播變更可讓其他應用程式（例如 shell）收取變更。</span><span class="sxs-lookup"><span data-stu-id="8ed43-125">Broadcasting the change allows other applications, such as the shell, to pick up the change.</span></span> <span data-ttu-id="8ed43-126">若要廣播變更，請讓您的產品安裝程式碼傳送**WM_SETTINGCHANGE**訊息，其中 `lParam` 設定為「環境」字串。</span><span class="sxs-lookup"><span data-stu-id="8ed43-126">To broadcast the change, have your product installation code send a **WM_SETTINGCHANGE** message with `lParam` set to the string "Environment".</span></span> <span data-ttu-id="8ed43-127">在您的模組安裝程式碼更新**PSModulePath**之後，請務必傳送該訊息。</span><span class="sxs-lookup"><span data-stu-id="8ed43-127">Be sure to send the message after your module installation code has updated **PSModulePath**.</span></span>

### <a name="use-the-correct-module-directory-name"></a><span data-ttu-id="8ed43-128">使用正確的模組目錄名稱</span><span class="sxs-lookup"><span data-stu-id="8ed43-128">Use the Correct Module Directory Name</span></span>

<span data-ttu-id="8ed43-129">格式正確的模組是儲存在目錄中的模組，其名稱與模組目錄中至少一個檔案的基底名稱相同。</span><span class="sxs-lookup"><span data-stu-id="8ed43-129">A well-formed module is a module that is stored in a directory that has the same name as the base name of at least one file in the module directory.</span></span> <span data-ttu-id="8ed43-130">如果模組的格式不正確，Windows PowerShell 就無法將它辨識為模組。</span><span class="sxs-lookup"><span data-stu-id="8ed43-130">If a module is not well-formed, Windows PowerShell does not recognize it as a module.</span></span>

<span data-ttu-id="8ed43-131">檔案的「基底名稱」是沒有副檔名的名稱。</span><span class="sxs-lookup"><span data-stu-id="8ed43-131">The "base name" of a file is the name without the file name extension.</span></span> <span data-ttu-id="8ed43-132">在格式正確的模組中，包含模組檔案的目錄名稱必須符合模組中至少一個檔案的基底名稱。</span><span class="sxs-lookup"><span data-stu-id="8ed43-132">In a well-formed module, the name of the directory that contains the module files must match the base name of at least one file in the module.</span></span>

<span data-ttu-id="8ed43-133">例如，在範例 Fabrikam 模組中，包含模組檔案的目錄會命名為 "Fabrikam"，而且至少有一個檔案包含 "Fabrikam" 基底名稱。</span><span class="sxs-lookup"><span data-stu-id="8ed43-133">For example, in the sample Fabrikam module, the directory that contains the module files is named "Fabrikam" and at least one file has the "Fabrikam" base name.</span></span> <span data-ttu-id="8ed43-134">在此情況下，.psd1 和 Fabrikam 都會有 "Fabrikam" 基底名稱。</span><span class="sxs-lookup"><span data-stu-id="8ed43-134">In this case, both Fabrikam.psd1 and Fabrikam.dll have the "Fabrikam" base name.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a><span data-ttu-id="8ed43-135">安裝不正確的效果</span><span class="sxs-lookup"><span data-stu-id="8ed43-135">Effect of Incorrect Installation</span></span>

<span data-ttu-id="8ed43-136">如果模組的格式不正確，且其位置並未包含在**PSModulePath**環境變數的值中，則 Windows PowerShell 的基本探索功能（如下列）將無法運作。</span><span class="sxs-lookup"><span data-stu-id="8ed43-136">If the module is not well-formed and its location is not included in the value of the **PSModulePath** environment variable, basic discovery features of Windows PowerShell, such as the following, do not work.</span></span>

- <span data-ttu-id="8ed43-137">模組自動載入功能無法自動匯入模組。</span><span class="sxs-lookup"><span data-stu-id="8ed43-137">The Module Auto-Loading feature cannot import the module automatically.</span></span>

- <span data-ttu-id="8ed43-138">[取得模組](/powershell/module/Microsoft.PowerShell.Core/Get-Module)Cmdlet 的 `ListAvailable` 參數找不到模組。</span><span class="sxs-lookup"><span data-stu-id="8ed43-138">The `ListAvailable` parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet cannot find the module.</span></span>

- <span data-ttu-id="8ed43-139">[Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet 找不到模組。</span><span class="sxs-lookup"><span data-stu-id="8ed43-139">The [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet cannot find the module.</span></span> <span data-ttu-id="8ed43-140">若要匯入模組，您必須提供根模組檔案或模組資訊清單檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="8ed43-140">To import the module, you must provide the full path to the root module file or module manifest file.</span></span>

  <span data-ttu-id="8ed43-141">除非將模組匯入會話，否則其他功能（例如下列）無法正常執行。</span><span class="sxs-lookup"><span data-stu-id="8ed43-141">Additional features, such as the following, do not work unless the module is imported into the session.</span></span> <span data-ttu-id="8ed43-142">在**PSModulePath**環境變數中格式正確的模組中，即使模組未匯入會話，這些功能仍可運作。</span><span class="sxs-lookup"><span data-stu-id="8ed43-142">In well-formed modules in the **PSModulePath** environment variable, these features work even when the module is not imported into the session.</span></span>

- <span data-ttu-id="8ed43-143">[Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) Cmdlet 在模組中找不到命令。</span><span class="sxs-lookup"><span data-stu-id="8ed43-143">The [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet cannot find commands in the module.</span></span>

- <span data-ttu-id="8ed43-144">[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)和[Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) Cmdlet 無法更新或儲存模組的說明。</span><span class="sxs-lookup"><span data-stu-id="8ed43-144">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets cannot update or save help for the module.</span></span>

- <span data-ttu-id="8ed43-145">[顯示命令](/powershell/module/Microsoft.PowerShell.Utility/Show-Command)Cmdlet 找不到並顯示模組中的命令。</span><span class="sxs-lookup"><span data-stu-id="8ed43-145">The [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet cannot find and display the commands in the module.</span></span>

  <span data-ttu-id="8ed43-146">Windows PowerShell 整合式腳本環境（ISE）中的 `Show-Command` 視窗遺失模組中的命令。</span><span class="sxs-lookup"><span data-stu-id="8ed43-146">The commands in the module are missing from the `Show-Command` window in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="where-to-install-modules"></a><span data-ttu-id="8ed43-147">模組的安裝位置</span><span class="sxs-lookup"><span data-stu-id="8ed43-147">Where to Install Modules</span></span>

<span data-ttu-id="8ed43-148">本節說明檔案系統中安裝 Windows PowerShell 模組的位置。</span><span class="sxs-lookup"><span data-stu-id="8ed43-148">This section explains where in the file system to install Windows PowerShell modules.</span></span> <span data-ttu-id="8ed43-149">位置取決於模組的使用方式。</span><span class="sxs-lookup"><span data-stu-id="8ed43-149">The location depends on how the module is used.</span></span>

### <a name="installing-modules-for-a-specific-user"></a><span data-ttu-id="8ed43-150">為特定使用者安裝模組</span><span class="sxs-lookup"><span data-stu-id="8ed43-150">Installing Modules for a Specific User</span></span>

<span data-ttu-id="8ed43-151">如果您建立自己的模組，或從另一方取得模組，例如 Windows PowerShell 社區網站，而且您想要讓模組僅供您的使用者帳戶使用，請在您的使用者特定模組目錄中安裝模組。</span><span class="sxs-lookup"><span data-stu-id="8ed43-151">If you create your own module or get a module from another party, such as a Windows PowerShell community website, and you want the module to be available for your user account only, install the module in your user-specific Modules directory.</span></span>

`$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

<span data-ttu-id="8ed43-152">根據預設，會將使用者特定的模組目錄新增至**PSModulePath**環境變數的值。</span><span class="sxs-lookup"><span data-stu-id="8ed43-152">The user-specific Modules directory is added to the value of the **PSModulePath** environment variable by default.</span></span>

### <a name="installing-modules-for-all-users-in-program-files"></a><span data-ttu-id="8ed43-153">針對 Program Files 中的所有使用者安裝模組</span><span class="sxs-lookup"><span data-stu-id="8ed43-153">Installing Modules for all Users in Program Files</span></span>

<span data-ttu-id="8ed43-154">如果您想要將模組提供給電腦上的所有使用者帳戶，請將模組安裝在 Program Files 位置。</span><span class="sxs-lookup"><span data-stu-id="8ed43-154">If you want a module to be available to all user accounts on the computer, install the module in the Program Files location.</span></span>

`$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

> [!NOTE]
> <span data-ttu-id="8ed43-155">在 Windows PowerShell 4.0 和更新版本中，預設會將 Program Files 位置新增至 PSModulePath 環境變數的值。</span><span class="sxs-lookup"><span data-stu-id="8ed43-155">The Program Files location is added to the value of the PSModulePath environment variable by default in Windows PowerShell 4.0 and later.</span></span> <span data-ttu-id="8ed43-156">對於舊版的 Windows PowerShell，您可以手動建立程式檔案位置（（%ProgramFiles%\WindowsPowerShell\Modules），並將此路徑新增至您的 PSModulePath 環境變數，如上所述。</span><span class="sxs-lookup"><span data-stu-id="8ed43-156">For earlier versions of Windows PowerShell, you can manually create the Program Files location ((%ProgramFiles%\WindowsPowerShell\Modules) and add this path to your PSModulePath environment variable as described above.</span></span>

### <a name="installing-modules-in-a-product-directory"></a><span data-ttu-id="8ed43-157">在產品目錄中安裝模組</span><span class="sxs-lookup"><span data-stu-id="8ed43-157">Installing Modules in a Product Directory</span></span>

<span data-ttu-id="8ed43-158">如果您要將課程模組散發給其他人，請使用上述的預設程式檔案位置，或建立您自己的公司專屬或產品特定的% ProgramFiles% 目錄子目錄。</span><span class="sxs-lookup"><span data-stu-id="8ed43-158">If you are distributing the module to other parties, use the default Program Files location described above, or create your own company-specific or product-specific subdirectory of the %ProgramFiles% directory.</span></span>

<span data-ttu-id="8ed43-159">例如，Fabrikam 技術是一家虛構的公司，它會為其 Fabrikam Manager 產品運送 Windows PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="8ed43-159">For example, Fabrikam Technologies, a fictitious company, is shipping a Windows PowerShell module for their Fabrikam Manager product.</span></span> <span data-ttu-id="8ed43-160">其模組安裝程式會在 Fabrikam Manager 產品子目錄中建立模組子目錄。</span><span class="sxs-lookup"><span data-stu-id="8ed43-160">Their module installer creates a Modules subdirectory in the Fabrikam Manager product subdirectory.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

<span data-ttu-id="8ed43-161">若要啟用 Windows PowerShell 模組探索功能以尋找 Fabrikam 模組，Fabrikam 模組安裝程式會將模組位置新增至**PSModulePath**環境變數的值。</span><span class="sxs-lookup"><span data-stu-id="8ed43-161">To enable the Windows PowerShell module discovery features to find the Fabrikam module, the Fabrikam module installer adds the module location to the value of the **PSModulePath** environment variable.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a><span data-ttu-id="8ed43-162">在通用檔案目錄中安裝模組</span><span class="sxs-lookup"><span data-stu-id="8ed43-162">Installing Modules in the Common Files Directory</span></span>

<span data-ttu-id="8ed43-163">如果產品的多個元件或產品的多個版本使用模組，請在%ProgramFiles%\Common Files\Modules 子目錄的模組特定子目錄中安裝模組。</span><span class="sxs-lookup"><span data-stu-id="8ed43-163">If a module is used by multiple components of a product or by multiple versions of a product, install the module in a module-specific subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span>

<span data-ttu-id="8ed43-164">在下列範例中，Fabrikam 模組會安裝在 `%ProgramFiles%\Common Files\Modules` 子目錄的 Fabrikam 子目錄中。</span><span class="sxs-lookup"><span data-stu-id="8ed43-164">In the following example, the Fabrikam module is installed in a Fabrikam subdirectory of the `%ProgramFiles%\Common Files\Modules` subdirectory.</span></span> <span data-ttu-id="8ed43-165">請注意，每個模組都位於模組子目錄中自己的子目錄中。</span><span class="sxs-lookup"><span data-stu-id="8ed43-165">Note that each module resides in its own subdirectory in the Modules subdirectory.</span></span>

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)
```

<span data-ttu-id="8ed43-166">然後，安裝程式會確保**PSModulePath**環境變數的值包含 common files 模組子目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="8ed43-166">Then, the installer assures the value of the **PSModulePath** environment variable includes the path of the common files modules subdirectory.</span></span>

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

## <a name="installing-multiple-versions-of-a-module"></a><span data-ttu-id="8ed43-167">安裝多個版本的模組</span><span class="sxs-lookup"><span data-stu-id="8ed43-167">Installing Multiple Versions of a Module</span></span>

<span data-ttu-id="8ed43-168">若要安裝相同模組的多個版本，請使用下列程式。</span><span class="sxs-lookup"><span data-stu-id="8ed43-168">To install multiple versions of the same module, use the following procedure.</span></span>

1. <span data-ttu-id="8ed43-169">為每個模組版本建立一個目錄。</span><span class="sxs-lookup"><span data-stu-id="8ed43-169">Create a directory for each version of the module.</span></span> <span data-ttu-id="8ed43-170">在目錄名稱中包含版本號碼。</span><span class="sxs-lookup"><span data-stu-id="8ed43-170">Include the version number in the directory name.</span></span>
2. <span data-ttu-id="8ed43-171">為模組的每個版本建立模組資訊清單。</span><span class="sxs-lookup"><span data-stu-id="8ed43-171">Create a module manifest for each version of the module.</span></span> <span data-ttu-id="8ed43-172">在資訊清單中**ModuleVersion**索引鍵的值，輸入模組版本號碼。</span><span class="sxs-lookup"><span data-stu-id="8ed43-172">In the value of the **ModuleVersion** key in the manifest, enter the module version number.</span></span> <span data-ttu-id="8ed43-173">將資訊清單檔案（. .psd1）儲存在模組的版本特定目錄中。</span><span class="sxs-lookup"><span data-stu-id="8ed43-173">Save the manifest file (.psd1) in the version-specific directory for the module.</span></span>
3. <span data-ttu-id="8ed43-174">將模組根資料夾路徑新增至**PSModulePath**環境變數的值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="8ed43-174">Add the module root folder path to the value of the **PSModulePath** environment variable, as shown in the following examples.</span></span>

<span data-ttu-id="8ed43-175">若要匯入特定版本的模組，終端使用者可以使用[import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet 的 `MinimumVersion` 或 `RequiredVersion` 參數。</span><span class="sxs-lookup"><span data-stu-id="8ed43-175">To import a particular version of the module, the end-user can use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="8ed43-176">例如，如果在8.0 和9.0 版中提供 Fabrikam 模組，Fabrikam 模組目錄結構可能如下所示。</span><span class="sxs-lookup"><span data-stu-id="8ed43-176">For example, if the Fabrikam module is available in versions 8.0 and 9.0, the Fabrikam module directory structure might resemble the following.</span></span>

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

<span data-ttu-id="8ed43-177">安裝程式會將這兩個模組路徑新增至**PSModulePath**環境變數值。</span><span class="sxs-lookup"><span data-stu-id="8ed43-177">The installer adds both of the module paths to the **PSModulePath** environment variable value.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

<span data-ttu-id="8ed43-178">當這些步驟完成時， [get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Module) Cmdlet 的**ListAvailable**參數會取得這兩個 Fabrikam 模組。</span><span class="sxs-lookup"><span data-stu-id="8ed43-178">When these steps are complete, the **ListAvailable** parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet gets both of the Fabrikam modules.</span></span> <span data-ttu-id="8ed43-179">若要匯入特定模組，請使用[import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet 的 `MinimumVersion` 或 `RequiredVersion` 參數。</span><span class="sxs-lookup"><span data-stu-id="8ed43-179">To import a particular module, use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="8ed43-180">如果這兩個模組都匯入相同的會話中，而且模組包含具有相同名稱的 Cmdlet，則最後匯入的 Cmdlet 就會在會話中生效。</span><span class="sxs-lookup"><span data-stu-id="8ed43-180">If both modules are imported into the same session, and the modules contain cmdlets with the same names, the cmdlets that are imported last are effective in the session.</span></span>

## <a name="handling-command-name-conflicts"></a><span data-ttu-id="8ed43-181">處理命令名稱衝突</span><span class="sxs-lookup"><span data-stu-id="8ed43-181">Handling Command Name Conflicts</span></span>

<span data-ttu-id="8ed43-182">當模組匯出的命令與使用者會話中的命令同名時，可能會發生命令名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="8ed43-182">Command name conflicts can occur when the commands that a module exports have the same name as commands in the user's session.</span></span>

<span data-ttu-id="8ed43-183">當會話包含兩個具有相同名稱的命令時，Windows PowerShell 會執行優先的命令類型。</span><span class="sxs-lookup"><span data-stu-id="8ed43-183">When a session contains two commands that have the same name, Windows PowerShell runs the command type that takes precedence.</span></span> <span data-ttu-id="8ed43-184">當會話包含兩個具有相同名稱和相同類型的命令時，Windows PowerShell 會執行最近新增至會話的命令。</span><span class="sxs-lookup"><span data-stu-id="8ed43-184">When a session contains two commands that have the same name and the same type, Windows PowerShell runs the command that was added to the session most recently.</span></span> <span data-ttu-id="8ed43-185">若要執行預設不會執行的命令，使用者可以使用模組名稱來限定命令名稱。</span><span class="sxs-lookup"><span data-stu-id="8ed43-185">To run a command that is not run by default, users can qualify the command name with the module name.</span></span>

<span data-ttu-id="8ed43-186">例如，如果會話包含 `Get-Date` 函式和 `Get-Date` Cmdlet，Windows PowerShell 預設會執行此功能。</span><span class="sxs-lookup"><span data-stu-id="8ed43-186">For example, if the session contains a `Get-Date` function and the `Get-Date` cmdlet, Windows PowerShell runs the function by default.</span></span> <span data-ttu-id="8ed43-187">若要執行此 Cmdlet，請在命令前面加上模組名稱，例如：</span><span class="sxs-lookup"><span data-stu-id="8ed43-187">To run the cmdlet, preface the command with the module name, such as:</span></span>

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

<span data-ttu-id="8ed43-188">為避免名稱衝突，模組作者可以使用模組資訊清單中的**DefaultCommandPrefix**索引鍵，為從模組匯出的所有命令指定名詞前置詞。</span><span class="sxs-lookup"><span data-stu-id="8ed43-188">To prevent name conflicts, module authors can use the **DefaultCommandPrefix** key in the module manifest to specify a noun prefix for all commands exported from the module.</span></span>

<span data-ttu-id="8ed43-189">使用者可以使用 `Import-Module` Cmdlet 的**prefix**參數，以使用替代的前置詞。</span><span class="sxs-lookup"><span data-stu-id="8ed43-189">Users can use the **Prefix** parameter of the `Import-Module` cmdlet to use an alternate prefix.</span></span> <span data-ttu-id="8ed43-190">**Prefix**參數的值會優先于**DefaultCommandPrefix**索引鍵的值。</span><span class="sxs-lookup"><span data-stu-id="8ed43-190">The value of the **Prefix** parameter takes precedence over the value of the **DefaultCommandPrefix** key.</span></span>

## <a name="see-also"></a><span data-ttu-id="8ed43-191">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ed43-191">See Also</span></span>

[<span data-ttu-id="8ed43-192">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="8ed43-192">about_Command_Precedence</span></span>](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[<span data-ttu-id="8ed43-193">撰寫 Windows PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="8ed43-193">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
