---
ms.date: 09/13/2016
ms.topic: reference
title: 安裝 PowerShell 模組
description: 安裝 PowerShell 模組
ms.openlocfilehash: 3c7a4413168934ca4de1912c9615a6ae0fc45788
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645337"
---
# <a name="installing-a-powershell-module"></a><span data-ttu-id="4a3fe-103">安裝 PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="4a3fe-103">Installing a PowerShell Module</span></span>

<span data-ttu-id="4a3fe-104">在您建立 PowerShell 模組之後，您可能想要將該模組安裝到系統上，讓您或其他人可以加以使用。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-104">After you have created your PowerShell module, you will likely want to install the module on a system, so that you or others may use it.</span></span> <span data-ttu-id="4a3fe-105">一般來說，這包含將模組檔案 (也就是 .psm1 或二進位組件、模組資訊清單，以及任何其他相關聯的檔案) 複製到該電腦上的目錄中。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-105">Generally speaking, this consists of copying the module files (ie, the .psm1, or the binary assembly, the module manifest, and any other associated files) onto a directory on that computer.</span></span> <span data-ttu-id="4a3fe-106">對於非常小的專案來說，您可能只需使用 [Windows 檔案總管] 將這些檔案複製並貼到單一遠端電腦即可；不過，對於較大型的解決方案來說，您可能需要使用更複雜的安裝程序。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-106">For a very small project, this may be as simple as copying and pasting the files with Windows Explorer onto a single remote computer; however, for larger solutions you may wish to use a more sophisticated installation process.</span></span> <span data-ttu-id="4a3fe-107">無論您是以何種方式將模組移至系統上，PowerShell 都可以使用數種技術來讓使用者尋找並使用您的模組。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-107">Regardless of how you get your module onto the system, PowerShell can use a number of techniques that will let users find and use your modules.</span></span> <span data-ttu-id="4a3fe-108">因此，安裝的主要問題在於確保 PowerShell 能夠找到您的模組。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-108">Therefore, the main issue for installation is ensuring that PowerShell will be able to find your module.</span></span> <span data-ttu-id="4a3fe-109">如需詳細資訊，請參閱[匯入 PowerShell 模組](./importing-a-powershell-module.md)。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-109">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="rules-for-installing-modules"></a><span data-ttu-id="4a3fe-110">安裝模組的規則</span><span class="sxs-lookup"><span data-stu-id="4a3fe-110">Rules for Installing Modules</span></span>

<span data-ttu-id="4a3fe-111">下列資訊適用於所有模組，包括您建立以供自己使用的模組、從其他合作對象取得的模組，以及您發佈給其他人的模組。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-111">The following information pertains to all modules, including modules that you create for your own use, modules that you get from other parties, and modules that you distribute to others.</span></span>

### <a name="install-modules-in-psmodulepath"></a><span data-ttu-id="4a3fe-112">在 PSModulePath 中安裝模組</span><span class="sxs-lookup"><span data-stu-id="4a3fe-112">Install Modules in PSModulePath</span></span>

<span data-ttu-id="4a3fe-113">請盡可能將所有模組安裝到列於 **PSModulePath** 環境變數中的路徑，或是將模組路徑新增到 **PSModulePath** 環境變數值。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-113">Whenever possible, install all modules in a path that is listed in the **PSModulePath** environment variable or add the module path to the **PSModulePath** environment variable value.</span></span>

<span data-ttu-id="4a3fe-114">**PSModulePath** 環境變數 ($Env:PSModulePath) 包含 Windows PowerShell 模組的位置。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-114">The **PSModulePath** environment variable ($Env:PSModulePath) contains the locations of Windows PowerShell modules.</span></span> <span data-ttu-id="4a3fe-115">Cmdlet 需仰賴此環境變數的值來尋找模組。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-115">Cmdlets rely on the value of this environment variable to find modules.</span></span>

<span data-ttu-id="4a3fe-116">根據預設， **PSModulePath** 環境變數值包含下列系統與使用者模組目錄，但您可以對該值進行新增及編輯。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-116">By default, the **PSModulePath** environment variable value contains the following system and user module directories, but you can add to and edit the value.</span></span>

- <span data-ttu-id="4a3fe-117">`$PSHome\Modules` (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span><span class="sxs-lookup"><span data-stu-id="4a3fe-117">`$PSHome\Modules` (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span></span>

  > [!WARNING]
  > <span data-ttu-id="4a3fe-118">此位置是保留給 Windows 隨附的模組。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-118">This location is reserved for modules that ship with Windows.</span></span> <span data-ttu-id="4a3fe-119">請勿將模組安裝到此位置。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-119">Do not install modules to this location.</span></span>

- <span data-ttu-id="4a3fe-120">`$Home\Documents\WindowsPowerShell\Modules` (%UserProfile%\Documents\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="4a3fe-120">`$Home\Documents\WindowsPowerShell\Modules` (%UserProfile%\Documents\WindowsPowerShell\Modules)</span></span>

- <span data-ttu-id="4a3fe-121">`$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="4a3fe-121">`$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\WindowsPowerShell\Modules)</span></span>

  <span data-ttu-id="4a3fe-122">若要取得 **PSModulePath** 環境變數的值，請使用下列其中一個命令。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-122">To get the value of the **PSModulePath** environment variable, use either of the following commands.</span></span>

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  <span data-ttu-id="4a3fe-123">若要將模組路徑新增到 **PSModulePath** 環境變數值的值，請使用下列命令格式。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-123">To add a module path to value of the **PSModulePath** environment variable value, use the following command format.</span></span> <span data-ttu-id="4a3fe-124">此格式使用 **System.Environment** 類別的 **SetEnvironmentVariable** 方法，來對 **PSModulePath** 環境變數進行與工作階段無關的變更。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-124">This format uses the **SetEnvironmentVariable** method of the **System.Environment** class to make a session-independent change to the **PSModulePath** environment variable.</span></span>

  ```powershell
  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > <span data-ttu-id="4a3fe-125">在您將路徑新增到 **PSModulePath** 之後，便應該廣播關於該變更的環境訊息。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-125">Once you have added the path to **PSModulePath** , you should broadcast an environment message about the change.</span></span> <span data-ttu-id="4a3fe-126">廣播變更可讓其他應用程式 (例如殼層) 取得該變更。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-126">Broadcasting the change allows other applications, such as the shell, to pick up the change.</span></span> <span data-ttu-id="4a3fe-127">若要廣播變更，請讓您的產品安裝程式碼傳送將 `lParam` 設定為 "Environment" 字串的 **WM_SETTINGCHANGE** 訊息。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-127">To broadcast the change, have your product installation code send a **WM_SETTINGCHANGE** message with `lParam` set to the string "Environment".</span></span> <span data-ttu-id="4a3fe-128">請務必在模組安裝程式碼具有更新的 **PSModulePath** 之後傳送該訊息。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-128">Be sure to send the message after your module installation code has updated **PSModulePath** .</span></span>

### <a name="use-the-correct-module-directory-name"></a><span data-ttu-id="4a3fe-129">使用正確的模組目錄名稱</span><span class="sxs-lookup"><span data-stu-id="4a3fe-129">Use the Correct Module Directory Name</span></span>

<span data-ttu-id="4a3fe-130">一個格式正確的模組，應該要儲存在與模組目錄中至少一個檔案的基底名稱具有相同名稱的目錄中。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-130">A well-formed module is a module that is stored in a directory that has the same name as the base name of at least one file in the module directory.</span></span> <span data-ttu-id="4a3fe-131">如果模組的格式不正確，Windows PowerShell 便無法將其辨識為模組。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-131">If a module is not well-formed, Windows PowerShell does not recognize it as a module.</span></span>

<span data-ttu-id="4a3fe-132">檔案的「基底名稱」是不含副檔名的名稱。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-132">The "base name" of a file is the name without the file name extension.</span></span> <span data-ttu-id="4a3fe-133">在格式正確的模組中，包含模組檔案之目錄的名稱必須符合模組中至少一個檔案的基底名稱。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-133">In a well-formed module, the name of the directory that contains the module files must match the base name of at least one file in the module.</span></span>

<span data-ttu-id="4a3fe-134">例如，在範例 Fabrikam 模組中，包含模組檔案的目錄名為 "Fabrikam"，且至少有一個檔案具有 "Fabrikam" 基底名稱。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-134">For example, in the sample Fabrikam module, the directory that contains the module files is named "Fabrikam" and at least one file has the "Fabrikam" base name.</span></span> <span data-ttu-id="4a3fe-135">在此情況下，Fabrikam.psd1 與 Fabrikam.dll 都具有 "Fabrikam" 基底名稱。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-135">In this case, both Fabrikam.psd1 and Fabrikam.dll have the "Fabrikam" base name.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a><span data-ttu-id="4a3fe-136">不正確安裝的影響</span><span class="sxs-lookup"><span data-stu-id="4a3fe-136">Effect of Incorrect Installation</span></span>

<span data-ttu-id="4a3fe-137">如果模組格式不正確，且其位置未包含在 **PSModulePath** 環境變數的值中，則 Windows PowerShell 的基本探索功能 (例如下列功能) 將無法運作。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-137">If the module is not well-formed and its location is not included in the value of the **PSModulePath** environment variable, basic discovery features of Windows PowerShell, such as the following, do not work.</span></span>

- <span data-ttu-id="4a3fe-138">模組自動載入功能無法自動匯入模組。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-138">The Module Auto-Loading feature cannot import the module automatically.</span></span>

- <span data-ttu-id="4a3fe-139">[Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) Cmdlet 的 `ListAvailable` 參數找不到模組。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-139">The `ListAvailable` parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet cannot find the module.</span></span>

- <span data-ttu-id="4a3fe-140">[Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet 找不到模組。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-140">The [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet cannot find the module.</span></span> <span data-ttu-id="4a3fe-141">若要匯入模組，您必須提供根模組檔案或模組資訊清單檔的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-141">To import the module, you must provide the full path to the root module file or module manifest file.</span></span>

  <span data-ttu-id="4a3fe-142">除非將模組匯入工作階段，否則其他功能 (例如下列功能) 將無法運作。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-142">Additional features, such as the following, do not work unless the module is imported into the session.</span></span> <span data-ttu-id="4a3fe-143">對於位於 **PSModulePath** 環境變數中且格式正確的模組來說，即使模組未匯入工作階段，這些功能也仍然可以運作。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-143">In well-formed modules in the **PSModulePath** environment variable, these features work even when the module is not imported into the session.</span></span>

- <span data-ttu-id="4a3fe-144">[Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) Cmdlet 無法在模組中找到命令。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-144">The [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet cannot find commands in the module.</span></span>

- <span data-ttu-id="4a3fe-145">[Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) 與 [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) Cmdlet 無法更新或儲存模組的說明。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-145">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets cannot update or save help for the module.</span></span>

- <span data-ttu-id="4a3fe-146">[Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) Cmdlet 無法在模組中找到並顯示命令。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-146">The [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet cannot find and display the commands in the module.</span></span>

  <span data-ttu-id="4a3fe-147">Windows PowerShell 整合式指令碼環境 (ISE) 中的 `Show-Command` 視窗遺失模組中的命令。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-147">The commands in the module are missing from the `Show-Command` window in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="where-to-install-modules"></a><span data-ttu-id="4a3fe-148">安裝模組的位置</span><span class="sxs-lookup"><span data-stu-id="4a3fe-148">Where to Install Modules</span></span>

<span data-ttu-id="4a3fe-149">此節說明在檔案系統中安裝 Windows PowerShell 模組的位置。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-149">This section explains where in the file system to install Windows PowerShell modules.</span></span> <span data-ttu-id="4a3fe-150">該位置會取決於模組的使用方式。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-150">The location depends on how the module is used.</span></span>

### <a name="installing-modules-for-a-specific-user"></a><span data-ttu-id="4a3fe-151">為特定使用者安裝模組</span><span class="sxs-lookup"><span data-stu-id="4a3fe-151">Installing Modules for a Specific User</span></span>

<span data-ttu-id="4a3fe-152">如果您是自行建立模組，或是從另一個合作對象 (例如 Windows PowerShell 社群網站) 取得模組，且您只想要讓該模組供您的使用者帳戶使用，請將模組安裝到您的使用者特定 [Modules] 目錄中。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-152">If you create your own module or get a module from another party, such as a Windows PowerShell community website, and you want the module to be available for your user account only, install the module in your user-specific Modules directory.</span></span>

`$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

<span data-ttu-id="4a3fe-153">使用者特定 [Modules] 目錄預設已新增至 **PSModulePath** 環境變數的值中。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-153">The user-specific Modules directory is added to the value of the **PSModulePath** environment variable by default.</span></span>

### <a name="installing-modules-for-all-users-in-program-files"></a><span data-ttu-id="4a3fe-154">為所有使用者在 [Program Files] 中安裝模組</span><span class="sxs-lookup"><span data-stu-id="4a3fe-154">Installing Modules for all Users in Program Files</span></span>

<span data-ttu-id="4a3fe-155">如果您想要讓模組供電腦上所有使用者帳戶使用，請將模組安裝到 [Program Files] 位置中。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-155">If you want a module to be available to all user accounts on the computer, install the module in the Program Files location.</span></span>

`$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

> [!NOTE]
> <span data-ttu-id="4a3fe-156">在 Windows PowerShell 4.0 與更新版本中，[Program Files] 位置預設已新增至 PSModulePath 環境變數的值中。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-156">The Program Files location is added to the value of the PSModulePath environment variable by default in Windows PowerShell 4.0 and later.</span></span> <span data-ttu-id="4a3fe-157">針對舊版的 Windows PowerShell，您可以手動建立 [Program Files] 位置 (%ProgramFiles%\WindowsPowerShell\Modules)，並以上述方式將此路徑新增至您的 PSModulePath 環境變數。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-157">For earlier versions of Windows PowerShell, you can manually create the Program Files location (%ProgramFiles%\WindowsPowerShell\Modules) and add this path to your PSModulePath environment variable as described above.</span></span>

### <a name="installing-modules-in-a-product-directory"></a><span data-ttu-id="4a3fe-158">在產品目錄中安裝模組</span><span class="sxs-lookup"><span data-stu-id="4a3fe-158">Installing Modules in a Product Directory</span></span>

<span data-ttu-id="4a3fe-159">如果您是要將模組發佈至其他合作對象，請使用上述的預設 [Program Files] 位置，或是在 %ProgramFiles% 目錄中自行建立公司特定或產品特定的子目錄。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-159">If you are distributing the module to other parties, use the default Program Files location described above, or create your own company-specific or product-specific subdirectory of the %ProgramFiles% directory.</span></span>

<span data-ttu-id="4a3fe-160">例如，假設 Fabrikam Technologies 這家虛構公司正在為他們的 Fabrikam Manager 產品推出 Windows PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-160">For example, Fabrikam Technologies, a fictitious company, is shipping a Windows PowerShell module for their Fabrikam Manager product.</span></span> <span data-ttu-id="4a3fe-161">他們的模組安裝程式會在 Fabrikam Manager 產品子目錄中建立 [Modules] 子目錄。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-161">Their module installer creates a Modules subdirectory in the Fabrikam Manager product subdirectory.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

<span data-ttu-id="4a3fe-162">為了讓 Windows PowerShell 模組探索功能找到 Fabrikam 模組，Fabrikam 模組安裝程式會將該模組位置新增到 **PSModulePath** 環境變數的值中。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-162">To enable the Windows PowerShell module discovery features to find the Fabrikam module, the Fabrikam module installer adds the module location to the value of the **PSModulePath** environment variable.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a><span data-ttu-id="4a3fe-163">在 [Common Files] 目錄中安裝模組</span><span class="sxs-lookup"><span data-stu-id="4a3fe-163">Installing Modules in the Common Files Directory</span></span>

<span data-ttu-id="4a3fe-164">如果模組會用於某個產品的多個元件或多個版本，請將該模組安裝到 %ProgramFiles%\Common Files\Modules 的模組特定子目錄中。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-164">If a module is used by multiple components of a product or by multiple versions of a product, install the module in a module-specific subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span>

<span data-ttu-id="4a3fe-165">在下列範例中，Fabrikam 模組會安裝到 `%ProgramFiles%\Common Files\Modules` 子目錄的 [Fabrikam] 子目錄中。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-165">In the following example, the Fabrikam module is installed in a Fabrikam subdirectory of the `%ProgramFiles%\Common Files\Modules` subdirectory.</span></span> <span data-ttu-id="4a3fe-166">請注意，在 [Modules] 子目錄中，每個模組都位於其自己的子目錄中。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-166">Note that each module resides in its own subdirectory in the Modules subdirectory.</span></span>

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)
```

<span data-ttu-id="4a3fe-167">然後，安裝程式會確保 **PSModulePath** 環境變數的值會包含 Common Files\Modules 子目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-167">Then, the installer assures the value of the **PSModulePath** environment variable includes the path of the common files modules subdirectory.</span></span>

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

## <a name="installing-multiple-versions-of-a-module"></a><span data-ttu-id="4a3fe-168">安裝模組的多個版本</span><span class="sxs-lookup"><span data-stu-id="4a3fe-168">Installing Multiple Versions of a Module</span></span>

<span data-ttu-id="4a3fe-169">若要安裝相同模組的多個版本，請使用下列程序。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-169">To install multiple versions of the same module, use the following procedure.</span></span>

1. <span data-ttu-id="4a3fe-170">為模組的每個版本建立目錄。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-170">Create a directory for each version of the module.</span></span> <span data-ttu-id="4a3fe-171">在目錄名稱中包含版本號碼。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-171">Include the version number in the directory name.</span></span>
2. <span data-ttu-id="4a3fe-172">為模組的每個版本建立模組資訊清單。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-172">Create a module manifest for each version of the module.</span></span> <span data-ttu-id="4a3fe-173">在資訊清單 **ModuleVersion** 機碼的值中，輸入模組版本號碼。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-173">In the value of the **ModuleVersion** key in the manifest, enter the module version number.</span></span> <span data-ttu-id="4a3fe-174">將資訊清單檔 (.psd1) 儲存到該模組的版本特定目錄中。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-174">Save the manifest file (.psd1) in the version-specific directory for the module.</span></span>
3. <span data-ttu-id="4a3fe-175">將模組根資料夾路徑新增到 **PSModulePath** 環境變數的值中，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-175">Add the module root folder path to the value of the **PSModulePath** environment variable, as shown in the following examples.</span></span>

<span data-ttu-id="4a3fe-176">若要匯入模組的特定版本，終端使用者可以使用 [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet 的 `MinimumVersion` 或 `RequiredVersion` 參數。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-176">To import a particular version of the module, the end-user can use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="4a3fe-177">例如，如果 Fabrikam 模組提供 8.0 與 9.0 版，Fabrikam 模組目錄結構可能如下所示。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-177">For example, if the Fabrikam module is available in versions 8.0 and 9.0, the Fabrikam module directory structure might resemble the following.</span></span>

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

<span data-ttu-id="4a3fe-178">安裝程式會將這兩個模組路徑新增到 **PSModulePath** 環境變數值。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-178">The installer adds both of the module paths to the **PSModulePath** environment variable value.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

<span data-ttu-id="4a3fe-179">完成這些步驟時， [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) Cmdlet 的 **ListAvailable** 參數便會取得這兩個 Fabrikam 模組。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-179">When these steps are complete, the **ListAvailable** parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet gets both of the Fabrikam modules.</span></span> <span data-ttu-id="4a3fe-180">若要匯入特定模組，請使用 [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet 的 `MinimumVersion` 或 `RequiredVersion` 參數。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-180">To import a particular module, use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="4a3fe-181">如果這兩個模組都匯入相同的工作階段，且兩個模組都包含具有相同名稱的 Cmdlet，則最後匯入的 Cmdlet 便會在工作階段中生效。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-181">If both modules are imported into the same session, and the modules contain cmdlets with the same names, the cmdlets that are imported last are effective in the session.</span></span>

## <a name="handling-command-name-conflicts"></a><span data-ttu-id="4a3fe-182">處理命令名稱衝突</span><span class="sxs-lookup"><span data-stu-id="4a3fe-182">Handling Command Name Conflicts</span></span>

<span data-ttu-id="4a3fe-183">命令名稱衝突可能會在模組匯出的命令與使用者工作階段中的命令具有相同名稱時發生。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-183">Command name conflicts can occur when the commands that a module exports have the same name as commands in the user's session.</span></span>

<span data-ttu-id="4a3fe-184">當工作階段包含兩個具有相同名稱的命令時，Windows PowerShell 會執行具優先順序的命令類型。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-184">When a session contains two commands that have the same name, Windows PowerShell runs the command type that takes precedence.</span></span> <span data-ttu-id="4a3fe-185">當工作階段包含兩個具有相同名稱與相同類型的命令時，Windows PowerShell 會執行最近新增到工作階段的命令。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-185">When a session contains two commands that have the same name and the same type, Windows PowerShell runs the command that was added to the session most recently.</span></span> <span data-ttu-id="4a3fe-186">若要執行預設不會執行的命令，使用者可以使用模組名稱來限定命令名稱。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-186">To run a command that is not run by default, users can qualify the command name with the module name.</span></span>

<span data-ttu-id="4a3fe-187">例如，若某個工作階段包含 `Get-Date` 函式與 `Get-Date` Cmdlet，Windows PowerShell 預設會執行函式。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-187">For example, if the session contains a `Get-Date` function and the `Get-Date` cmdlet, Windows PowerShell runs the function by default.</span></span> <span data-ttu-id="4a3fe-188">若要執行 Cmdlet，請在命令前面加上模組名稱，例如：</span><span class="sxs-lookup"><span data-stu-id="4a3fe-188">To run the cmdlet, preface the command with the module name, such as:</span></span>

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

<span data-ttu-id="4a3fe-189">若要避免名稱衝突，模組作者可以在模組資訊清單中使用 **DefaultCommandPrefix** 機碼，來針對從模組匯出的所有命令指定名詞前置詞。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-189">To prevent name conflicts, module authors can use the **DefaultCommandPrefix** key in the module manifest to specify a noun prefix for all commands exported from the module.</span></span>

<span data-ttu-id="4a3fe-190">使用者可以使用 `Import-Module` Cmdlet 的 **Prefix** 參數來使用替代的前置詞。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-190">Users can use the **Prefix** parameter of the `Import-Module` cmdlet to use an alternate prefix.</span></span> <span data-ttu-id="4a3fe-191">**Prefix** 參數的值會優先於 **DefaultCommandPrefix** 機碼的值。</span><span class="sxs-lookup"><span data-stu-id="4a3fe-191">The value of the **Prefix** parameter takes precedence over the value of the **DefaultCommandPrefix** key.</span></span>

## <a name="see-also"></a><span data-ttu-id="4a3fe-192">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a3fe-192">See Also</span></span>

[<span data-ttu-id="4a3fe-193">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="4a3fe-193">about_Command_Precedence</span></span>](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[<span data-ttu-id="4a3fe-194">撰寫 Windows PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="4a3fe-194">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
