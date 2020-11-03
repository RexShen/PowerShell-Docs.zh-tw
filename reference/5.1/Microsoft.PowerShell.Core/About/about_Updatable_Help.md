---
description: 描述 PowerShell 中可更新的說明系統。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_updatable_help?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Updatable_Help
ms.openlocfilehash: 03425aef93f3d4bbb06aee87d30f4a441c0b2d86
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207904"
---
# <a name="about-updatable-help"></a><span data-ttu-id="84fa3-104">關於可更新的說明</span><span class="sxs-lookup"><span data-stu-id="84fa3-104">About Updatable Help</span></span>

## <a name="short-description"></a><span data-ttu-id="84fa3-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="84fa3-105">Short description</span></span>
<span data-ttu-id="84fa3-106">描述 PowerShell 中可更新的說明系統。</span><span class="sxs-lookup"><span data-stu-id="84fa3-106">Describes the updatable help system in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="84fa3-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="84fa3-107">Long description</span></span>

<span data-ttu-id="84fa3-108">PowerShell 提供數種不同的方法來存取 PowerShell Cmdlet 和概念的最新說明主題。</span><span class="sxs-lookup"><span data-stu-id="84fa3-108">PowerShell provides several different ways to access the most up-to-date help topics for PowerShell cmdlets and concepts.</span></span>

<span data-ttu-id="84fa3-109">PowerShell 3.0 中引進的可更新說明系統是設計來確保您在本機電腦上一律擁有最新的說明主題，讓您可以在命令列中讀取它們。</span><span class="sxs-lookup"><span data-stu-id="84fa3-109">The Updatable Help system, introduced in PowerShell 3.0, is designed to assure that you always have the newest help topics on your local computer so that you can read them at the command line.</span></span> <span data-ttu-id="84fa3-110">它可讓您輕鬆地下載和安裝說明檔，並在有較新的說明檔可用時加以更新。</span><span class="sxs-lookup"><span data-stu-id="84fa3-110">It makes it easy to download and install help files and to update them whenever newer help files become available.</span></span>

<span data-ttu-id="84fa3-111">若要為企業中的多部電腦和無法存取網際網路的電腦提供更新的說明，可更新的說明可讓您將說明檔案下載到檔案系統目錄或檔案共用，然後從檔案共用安裝說明檔。</span><span class="sxs-lookup"><span data-stu-id="84fa3-111">To provide updated help for multiple computers in an enterprise and for computers that do not have access to the internet, Updatable Help lets you download help files to a filesystem directory or file share, and then install the help files from the file share.</span></span>

<span data-ttu-id="84fa3-112">在 PowerShell 4.0 中， **HelpInfoUri** 屬性會保留在 Windows PowerShell 遠端處理，讓您可以 `Save-Help` 使用安裝在遠端電腦上的模組，但不一定會安裝在本機電腦上。</span><span class="sxs-lookup"><span data-stu-id="84fa3-112">In PowerShell 4.0, the **HelpInfoUri** property is preserved over Windows PowerShell remoting, which allows `Save-Help` to work for modules that are installed on a remote computer, but are not necessarily installed on the local computer.</span></span> <span data-ttu-id="84fa3-113">您可以將 **PSModuleInfo** 物件儲存至磁片或卸載式媒體 (例如 USB 磁片磁碟機) ，方法是 `Export-Clixml` 在無法存取網際網路的電腦上執行、在可存取網際網路的電腦上匯入 **PSModuleInfo** 物件，然後 `Save-Help` 在 **PSModuleInfo** 物件上執行。</span><span class="sxs-lookup"><span data-stu-id="84fa3-113">You can save a **PSModuleInfo** object to disk or removable media (such as a USB drive) by running `Export-Clixml` on a computer that does not have internet access, importing the **PSModuleInfo** object on a computer that does have internet access, and then running `Save-Help` on the **PSModuleInfo** object.</span></span> <span data-ttu-id="84fa3-114">您可以使用卸載式媒體將儲存的說明複製到遠端的已中斷連線的電腦，然後再執行安裝 `Update-Help` 。</span><span class="sxs-lookup"><span data-stu-id="84fa3-114">The saved help can be copied to the remote, disconnected computer by using removable media, and then installed by running `Update-Help`.</span></span> <span data-ttu-id="84fa3-115">這些功能的增強 `Save-Help` 功能可讓您在沒有任何網路存取的電腦上安裝說明。</span><span class="sxs-lookup"><span data-stu-id="84fa3-115">These improvements in `Save-Help` functionality let you install help on computers that are without any kind of network access.</span></span> <span data-ttu-id="84fa3-116">如需如何使用新功能的範例 `Save-Help` ，請參閱本主題中的 [如何更新檔案共用的說明](#how-to-update-help-from-a-file-share) 。</span><span class="sxs-lookup"><span data-stu-id="84fa3-116">For an example of how to use the new `Save-Help` functionality, see [How to update help from a file share](#how-to-update-help-from-a-file-share) in this topic.</span></span>

<span data-ttu-id="84fa3-117">「可更新的說明」也支援線上存取最新的說明主題和 Cmdlet 的基本說明，即使電腦上沒有說明檔也一樣。</span><span class="sxs-lookup"><span data-stu-id="84fa3-117">Updatable Help also supports online access to the newest help topics and basic help for cmdlets, even when there are no help files on the computer.</span></span>

<span data-ttu-id="84fa3-118">PowerShell 3.0 並未隨附說明檔。</span><span class="sxs-lookup"><span data-stu-id="84fa3-118">PowerShell 3.0 does not come with Help files.</span></span> <span data-ttu-id="84fa3-119">您可以使用「可更新的說明」功能，針對 PowerShell 和所有 Windows 模組中預設包含的所有命令安裝說明檔。</span><span class="sxs-lookup"><span data-stu-id="84fa3-119">You can use the Updatable Help feature to install the help files for all of the commands that are included by default in PowerShell and for all Windows modules.</span></span>

## <a name="updatable-help-cmdlets"></a><span data-ttu-id="84fa3-120">可更新的說明 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="84fa3-120">Updatable help cmdlets</span></span>

- <span data-ttu-id="84fa3-121">`Update-Help`：從網際網路或檔案共用下載最新的說明檔，並將它們安裝在本機電腦上。</span><span class="sxs-lookup"><span data-stu-id="84fa3-121">`Update-Help`: Downloads the newest help files from the internet or a file share, and installs them on the local computer.</span></span>

- <span data-ttu-id="84fa3-122">`Save-Help`：從網際網路下載最新的說明檔，並將它們儲存在檔案系統目錄或檔案共用中。</span><span class="sxs-lookup"><span data-stu-id="84fa3-122">`Save-Help`: Downloads the newest help files from the internet and saves them in a filesystem directory or file share.</span></span> <span data-ttu-id="84fa3-123">若要在電腦上安裝說明檔，請使用 `Update-Help` 。</span><span class="sxs-lookup"><span data-stu-id="84fa3-123">To install the help files on computers, use `Update-Help`.</span></span>

- <span data-ttu-id="84fa3-124">`Get-Help`：在命令列中顯示說明主題。</span><span class="sxs-lookup"><span data-stu-id="84fa3-124">`Get-Help`: Displays help topics at the command line.</span></span> <span data-ttu-id="84fa3-125">從電腦上的說明檔中取得協助。</span><span class="sxs-lookup"><span data-stu-id="84fa3-125">Gets help from the help files on the computer.</span></span> <span data-ttu-id="84fa3-126">針對沒有說明檔的 Cmdlet 和函式，顯示自動產生的說明。</span><span class="sxs-lookup"><span data-stu-id="84fa3-126">Displays auto-generated help for cmdlets and functions that do not have help files.</span></span> <span data-ttu-id="84fa3-127">在您的預設網際網路瀏覽器中，開啟 Cmdlet、函式、腳本和工作流程的線上說明主題。</span><span class="sxs-lookup"><span data-stu-id="84fa3-127">Opens online help topics for cmdlets, functions, scripts, and workflows in your default internet browser.</span></span>

## <a name="update-help-in-the-powershell-ise"></a><span data-ttu-id="84fa3-128">更新 PowerShell ISE 中的說明</span><span class="sxs-lookup"><span data-stu-id="84fa3-128">Update help in the PowerShell ISE</span></span>

<span data-ttu-id="84fa3-129">您也可以在 PowerShell 整合式腳本環境 (ISE) 的 [說明] 功能表中，使用 [ **更新 powershell** 說明] 專案來更新說明。</span><span class="sxs-lookup"><span data-stu-id="84fa3-129">You can also update help by using the **Update PowerShell Help** item in the Help menu in PowerShell Integrated Scripting Environment (ISE).</span></span>

<span data-ttu-id="84fa3-130">**Update PowerShell** 說明專案 `Update-Help` 會執行不含參數的命令。</span><span class="sxs-lookup"><span data-stu-id="84fa3-130">The **Update PowerShell Help** item runs an `Update-Help` command without parameters.</span></span>

## <a name="auto-generated-help-help-without-help-files"></a><span data-ttu-id="84fa3-131">自動產生的說明：沒有說明檔的說明</span><span class="sxs-lookup"><span data-stu-id="84fa3-131">Auto-generated help: help without help files</span></span>

<span data-ttu-id="84fa3-132">如果您的電腦上沒有 Cmdlet、函式或工作流程的說明檔，此 `Get-Help` Cmdlet 會顯示自動產生的說明，並提示您下載說明檔或在線上閱讀。</span><span class="sxs-lookup"><span data-stu-id="84fa3-132">If you do not have the help file for a cmdlet, function, or workflow on the computer, the `Get-Help` cmdlet displays auto-generated help and prompts you to download the help files or read them online.</span></span>

<span data-ttu-id="84fa3-133">自動產生的說明包括語法和別名，以及說明如何使用可更新的說明 Cmdlet 及存取線上說明主題的備註。</span><span class="sxs-lookup"><span data-stu-id="84fa3-133">Auto-generated help includes syntax and aliases, and remarks that explain how to use the Updatable Help cmdlets and to access the online help topics.</span></span>

<span data-ttu-id="84fa3-134">例如，下列命令會取得 Cmdlet 的基本說明 `Get-Culture` 。</span><span class="sxs-lookup"><span data-stu-id="84fa3-134">For example, the following command gets basic help for the `Get-Culture` cmdlet.</span></span> <span data-ttu-id="84fa3-135">當電腦上沒有說明檔時，輸出 `Get-Help` 會顯示顯示。</span><span class="sxs-lookup"><span data-stu-id="84fa3-135">The output shows the `Get-Help` display when there are no help files on the computer.</span></span>

```powershell
Get-Help Get-Culture
```

```output
NAME
    Get-Culture

SYNTAX
    Get-Culture [<CommonParameters>]

ALIASES
    None

REMARKS
    To get the latest Help content including descriptions and examples
    type: Update-Help.
```

## <a name="help-files-for-modules"></a><span data-ttu-id="84fa3-136">模組的說明檔</span><span class="sxs-lookup"><span data-stu-id="84fa3-136">Help files for modules</span></span>

<span data-ttu-id="84fa3-137">可更新說明的最小單位是模組的說明。</span><span class="sxs-lookup"><span data-stu-id="84fa3-137">The smallest unit of Updatable Help is help for a module.</span></span> <span data-ttu-id="84fa3-138">模組說明包含模組中所有 Cmdlet、函數、工作流程、提供者、腳本和概念的說明。</span><span class="sxs-lookup"><span data-stu-id="84fa3-138">Module help includes help for all of the cmdlets, functions, workflows, providers, scripts, and concepts in a module.</span></span> <span data-ttu-id="84fa3-139">您可以更新安裝在電腦上的所有模組的說明，即使它們未匯入目前的會話中也一樣。</span><span class="sxs-lookup"><span data-stu-id="84fa3-139">You can update help for all modules that are installed on the computer, even if they are not imported into the current session.</span></span>

<span data-ttu-id="84fa3-140">您可以更新整個模組的說明，但無法更新個別 Cmdlet 的說明。</span><span class="sxs-lookup"><span data-stu-id="84fa3-140">You can update help for the entire module, but you cannot update help for individual cmdlets.</span></span>

<span data-ttu-id="84fa3-141">若要尋找包含特定 Cmdlet 的模組，請使用下列命令格式：</span><span class="sxs-lookup"><span data-stu-id="84fa3-141">To find the module that contains a particular cmdlet, use the following command format:</span></span>

```powershell
(Get-Command <cmdlet-name>).ModuleName
```

<span data-ttu-id="84fa3-142">例如，若要尋找包含 Cmdlet 的模組 `Set-ExecutionPolicy` ，請輸入：</span><span class="sxs-lookup"><span data-stu-id="84fa3-142">For example, to find the module that contains the `Set-ExecutionPolicy` cmdlet, type:</span></span>

```powershell
(Get-Command Set-ExecutionPolicy).ModuleName
```

<span data-ttu-id="84fa3-143">若要更新特定模組的說明，請輸入：</span><span class="sxs-lookup"><span data-stu-id="84fa3-143">To update help for a particular module, type:</span></span>

```powershell
Update-Help -Module <ModuleName>
```

<span data-ttu-id="84fa3-144">例如，若要更新包含 Set-ExecutionPolicy Cmdlet 之模組的說明，請輸入：</span><span class="sxs-lookup"><span data-stu-id="84fa3-144">For example, to update help for the module that contains the Set-ExecutionPolicy cmdlet, type:</span></span>

```powershell
Update-Help -Module Microsoft.PowerShell.Security
```

## <a name="permissions-for-updatable-help"></a><span data-ttu-id="84fa3-145">可更新說明的許可權</span><span class="sxs-lookup"><span data-stu-id="84fa3-145">Permissions for updatable help</span></span>

<span data-ttu-id="84fa3-146">若要更新目錄中模組的說明 `$pshome/Modules` ，您必須是電腦上 Administrators 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="84fa3-146">To update help for the modules in the directory `$pshome/Modules`, you must be member of the Administrators group on the computer.</span></span>

<span data-ttu-id="84fa3-147">如果您不是 Administrators 群組的成員，您就無法更新這些模組的說明。但是，如果您可以存取網際網路，就可以在線上觀看說明。</span><span class="sxs-lookup"><span data-stu-id="84fa3-147">If you are not a member of the Administrators group, you cannot update help for these modules; but if you have internet access, you can view help online.</span></span>

<span data-ttu-id="84fa3-148">針對目錄中的模組 `$home/Documents/PowerShell/Modules` 或目錄其他子目錄中的模組更新說明不 `$home` 需要特殊許可權。</span><span class="sxs-lookup"><span data-stu-id="84fa3-148">Updating help for modules in the directory `$home/Documents/PowerShell/Modules` or modules in other subdirectories of the `$home` directory does not require special permissions.</span></span>

<span data-ttu-id="84fa3-149">`Update-Help`和 `Save-Help` Cmdlet 具有 **UseDefaultCredentials** 參數，可提供目前使用者的明確認證。</span><span class="sxs-lookup"><span data-stu-id="84fa3-149">The `Update-Help` and `Save-Help` cmdlets have a **UseDefaultCredentials** parameter that provides the explicit credentials of the current user.</span></span> <span data-ttu-id="84fa3-150">此參數是針對存取安全的網際網路位置所設計。</span><span class="sxs-lookup"><span data-stu-id="84fa3-150">This parameter is designed for accessing secure internet locations.</span></span>

<span data-ttu-id="84fa3-151">`Update-Help`和 `Save-Help` Cmdlet 也有一個 **Credential** 參數，可讓您在遠端電腦上執行命令，並存取第三部電腦上的檔案共用。</span><span class="sxs-lookup"><span data-stu-id="84fa3-151">The `Update-Help` and `Save-Help` cmdlets also have a **Credential** parameter that allows you to run the command on a remote computer and access a file share on a third computer.</span></span> <span data-ttu-id="84fa3-152">只有 **Credential** 當您使用的 SourcePath 或 **LiteralPath** 參數 `Update-Help` 以及的 **DestinationPath** 或 **LiteralPath** 參數時，Credential 參數才有效 `Save-Help` 。</span><span class="sxs-lookup"><span data-stu-id="84fa3-152">The **Credential** parameter is valid only when you use the SourcePath or **LiteralPath** parameters of `Update-Help` and the **DestinationPath** or **LiteralPath** parameters of `Save-Help`.</span></span>

## <a name="how-to-install-and-update-help-files"></a><span data-ttu-id="84fa3-153">如何安裝和更新說明檔</span><span class="sxs-lookup"><span data-stu-id="84fa3-153">How to install and update help files</span></span>

<span data-ttu-id="84fa3-154">若要第一次下載和安裝說明檔，或更新您電腦上的說明檔，請使用 `Update-Help` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="84fa3-154">To download and install help files for the first time, or to update the help files on your computer, use the `Update-Help` cmdlet.</span></span>

<span data-ttu-id="84fa3-155">此 `Update-Help` Cmdlet 會為您執行所有的困難工作，包括下列工作。</span><span class="sxs-lookup"><span data-stu-id="84fa3-155">The `Update-Help` cmdlet does all of the hard work for you, including the following tasks.</span></span>

- <span data-ttu-id="84fa3-156">判斷哪些模組支援可更新的說明。</span><span class="sxs-lookup"><span data-stu-id="84fa3-156">Determines which modules support Updatable Help.</span></span>
- <span data-ttu-id="84fa3-157">尋找每個模組儲存其可更新說明檔的網際網路位置。</span><span class="sxs-lookup"><span data-stu-id="84fa3-157">Finds the internet location where each module stores its Updatable Help files.</span></span>
- <span data-ttu-id="84fa3-158">將您電腦上每個模組的說明檔，與每個模組可用的最新說明檔案進行比較。</span><span class="sxs-lookup"><span data-stu-id="84fa3-158">Compares the help files for each module on your computer to the newest help files that are available for each module.</span></span>
- <span data-ttu-id="84fa3-159">從網際網路下載新的檔案。</span><span class="sxs-lookup"><span data-stu-id="84fa3-159">Downloads the new files from the internet.</span></span>
- <span data-ttu-id="84fa3-160">解除包裝說明檔套件。</span><span class="sxs-lookup"><span data-stu-id="84fa3-160">Unwraps the help file package.</span></span>
- <span data-ttu-id="84fa3-161">確認檔案是有效的說明檔。</span><span class="sxs-lookup"><span data-stu-id="84fa3-161">Verifies that the files are valid help files.</span></span>
- <span data-ttu-id="84fa3-162">在模組目錄的特定語言子目錄中安裝說明檔。</span><span class="sxs-lookup"><span data-stu-id="84fa3-162">Installs the help files in the language-specific subdirectory of the module directory.</span></span>

<span data-ttu-id="84fa3-163">若要存取新的說明主題，請使用 `Get-Help` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="84fa3-163">To access the new help topics, use the `Get-Help` cmdlet.</span></span> <span data-ttu-id="84fa3-164">您不需要重新開機 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="84fa3-164">You do not need to restart PowerShell.</span></span>

<span data-ttu-id="84fa3-165">若要在支援可更新說明的電腦上安裝或更新所有模組的說明，請輸入：</span><span class="sxs-lookup"><span data-stu-id="84fa3-165">To install or update help for all modules on the computer that supports Updatable Help, type:</span></span>

```powershell
Update-Help
```

<span data-ttu-id="84fa3-166">若要更新特定模組的說明，請新增的 **模組** 參數 `Update-Help` 。</span><span class="sxs-lookup"><span data-stu-id="84fa3-166">To update help for particular modules, add the **Module** parameter of `Update-Help`.</span></span> <span data-ttu-id="84fa3-167">模組名稱中允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="84fa3-167">Wildcard characters are permitted in the module name.</span></span>

<span data-ttu-id="84fa3-168">例如，若要更新 ServerManager 模組的說明，請輸入：</span><span class="sxs-lookup"><span data-stu-id="84fa3-168">For example, to update help for the ServerManager module, type:</span></span>

```powershell
Update-Help -Module ServerManager
```

<span data-ttu-id="84fa3-169">如果沒有參數， `Update-Help` 則會針對會話中的所有模組以及所有支援可更新說明的已安裝模組更新說明。</span><span class="sxs-lookup"><span data-stu-id="84fa3-169">Without parameters, `Update-Help` updates help for all modules in the session and for all installed modules that support Updatable Help.</span></span> <span data-ttu-id="84fa3-170">您必須將模組安裝在 PSModulePath 環境變數的值所列的目錄中，才能包含這些模組。</span><span class="sxs-lookup"><span data-stu-id="84fa3-170">To be included, modules must be installed in directories that are listed in the value of the PSModulePath environment variable.</span></span> <span data-ttu-id="84fa3-171">這些也是由 "Get-help-ListAvailable" 命令所傳回的模組。</span><span class="sxs-lookup"><span data-stu-id="84fa3-171">These are also modules that are returned by a "Get-Help -ListAvailable" command.</span></span>

<span data-ttu-id="84fa3-172">如果 **Module** 參數的值是 `*` (所有) ，則 `Update-Help` 會嘗試更新所有已安裝模組的說明，包括不支援「可更新的說明」的模組。</span><span class="sxs-lookup"><span data-stu-id="84fa3-172">If the value of the **Module** parameter is `*` (all), `Update-Help` attempts to update help for all installed modules, including modules that do not support Updatable Help.</span></span> <span data-ttu-id="84fa3-173">此命令通常會在 Cmdlet 遇到不支援「可更新的說明」的模組時產生許多錯誤。</span><span class="sxs-lookup"><span data-stu-id="84fa3-173">This command typically generates many errors as the cmdlet encounters modules that do not support Updatable Help.</span></span>

## <a name="how-to-update-help-from-a-file-share"></a><span data-ttu-id="84fa3-174">如何從檔案共用更新說明</span><span class="sxs-lookup"><span data-stu-id="84fa3-174">How to update help from a file share</span></span>

<span data-ttu-id="84fa3-175">若要支援未連線至網際網路的電腦，或是要控制或簡化在企業中更新的協助，請使用 `Save-Help` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="84fa3-175">To support computers that are not connected to the internet, or to control or streamline help updating in an enterprise, use the `Save-Help` cmdlet.</span></span> <span data-ttu-id="84fa3-176">`Save-Help`Cmdlet 會從網際網路下載說明檔，並將其儲存在您指定的 filesystem 目錄中。</span><span class="sxs-lookup"><span data-stu-id="84fa3-176">The `Save-Help` cmdlet downloads help files from the internet and saves them in a filesystem directory that you specify.</span></span>

<span data-ttu-id="84fa3-177">`Save-Help` 比較指定目錄中的說明檔與每個模組可用的最新說明檔案。</span><span class="sxs-lookup"><span data-stu-id="84fa3-177">`Save-Help` compares the help files in the specified directory to the newest help files that are available for each module.</span></span> <span data-ttu-id="84fa3-178">如果目錄沒有說明檔或較新的說明檔可供模組使用，則 `Save-Help` Cmdlet 會從網際網路下載新的檔案。</span><span class="sxs-lookup"><span data-stu-id="84fa3-178">If the directory has no help files or newer help files are available for the module, the `Save-Help` cmdlet downloads the new files from the internet.</span></span> <span data-ttu-id="84fa3-179">但是，它不會解除包裝或安裝說明檔。</span><span class="sxs-lookup"><span data-stu-id="84fa3-179">However, it does not unwrap or install the help files.</span></span>

<span data-ttu-id="84fa3-180">若要從儲存至檔案系統目錄的說明檔安裝或更新電腦上的說明檔，請使用 Cmdlet 的 **SourcePath** 參數 `Update-Help` 。</span><span class="sxs-lookup"><span data-stu-id="84fa3-180">To install or update the help files on a computer from help files that were saved to a filesystem directory, use the **SourcePath** parameter of the `Update-Help` cmdlet.</span></span> <span data-ttu-id="84fa3-181">此 `Update-Help` Cmdlet 會識別最新的說明檔案、解除包裝並驗證它們，然後將它們安裝在模組目錄的特定語言子目錄中。</span><span class="sxs-lookup"><span data-stu-id="84fa3-181">The `Update-Help` cmdlet identifies the newest help files, unwraps and validates them, and installs them in the language-specific subdirectories of the module directories.</span></span>

<span data-ttu-id="84fa3-182">例如，若要將所有已安裝模組的說明儲存至 `\\Server\Share` 目錄，請輸入：</span><span class="sxs-lookup"><span data-stu-id="84fa3-182">For example, to save help for all installed modules to the `\\Server\Share` directory, type:</span></span>

```powershell
Save-Help -DestinationPath \\Server\Share
```

<span data-ttu-id="84fa3-183">然後，若要更新目錄中的說明 `\\Server\Share` ，請輸入：</span><span class="sxs-lookup"><span data-stu-id="84fa3-183">Then, to update help from the `\\Server\Share` directory, type:</span></span>

```powershell
Update-Help -SourcePath \\Server\Share
```

<span data-ttu-id="84fa3-184">下列範例示範 `Save-Help` 如何使用來儲存未安裝在本機電腦上之模組的說明。</span><span class="sxs-lookup"><span data-stu-id="84fa3-184">The following examples show the use of `Save-Help` to save help for modules that are not installed on the local computer.</span></span> <span data-ttu-id="84fa3-185">在此範例中，系統管理員 `Save-Help` 會執行，以從連線到網際網路的用戶端電腦儲存 DhcpServer 模組的說明，而不需要在本機電腦上安裝 DhcpServer 模組或 DHCP 伺服器角色。</span><span class="sxs-lookup"><span data-stu-id="84fa3-185">In this example, the administrator runs `Save-Help` to save the help for the DhcpServer module from an internet-connected client computer, without installing the DhcpServer module or DHCP Server role on the local computer.</span></span>

<span data-ttu-id="84fa3-186">選項1：執行 `Invoke-Command` 以取得遠端模組的 **PSModuleInfo** 物件，將它儲存在變數中， `$m` 然後在 `Save-Help` **PSModuleInfo** 物件上執行，方法是將變數指定 `$m` 為模組名稱。</span><span class="sxs-lookup"><span data-stu-id="84fa3-186">Option 1: Run `Invoke-Command` to get the **PSModuleInfo** object for the remote module, save it in a variable, `$m`, and then run `Save-Help` on the **PSModuleInfo** object by specifying the variable `$m` as the module name.</span></span>

```powershell
$m = Invoke-Command -ComputerName RemoteServer -ScriptBlock
{ Get-Module -Name DhcpServer -ListAvailable }
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

<span data-ttu-id="84fa3-187">選項2：開啟以執行 DHCP 伺服器模組的電腦為目標的 PSSession、取得模組的 **PSModuleInfo** 物件、將它儲存在變數中， `$m` 然後 `Save-Help` 在儲存在變數中的物件上執行 `$m` 。</span><span class="sxs-lookup"><span data-stu-id="84fa3-187">Option 2: Open a PSSession targeted at the computer that is running the DHCP Server module, to get the **PSModuleInfo** object for the module, save it in a variable `$m`, and then run `Save-Help` on the object that is saved in the `$m` variable.</span></span>

```powershell
$s = New-PSSession -ComputerName RemoteServer
$m = Get-Module -PSSession $s -Name DhcpServer -ListAvailable
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

<span data-ttu-id="84fa3-188">選項3：開啟以執行 DHCP 伺服器模組的電腦為目標的 CIM 會話，若要取得模組的 **PSModuleInfo** 物件，請將它儲存在變數中， `$m` 然後 `Save-Help` 在儲存在變數中的物件上執行 `$m` 。</span><span class="sxs-lookup"><span data-stu-id="84fa3-188">Option 3: Open a CIM session, targeted at the computer that is running the DHCP Server module, to get the **PSModuleInfo** object for the module, save it in a variable `$m`, and then run `Save-Help` on the object that is saved in the `$m` variable.</span></span>

```powershell
$c = New-CimSession -ComputerName RemoteServer
$m = Get-Module -CimSession $c -Name DhcpServer -ListAvailable
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

<span data-ttu-id="84fa3-189">在下列範例中，系統管理員會在沒有網路存取的電腦上，安裝 DHCP 伺服器模組的說明。</span><span class="sxs-lookup"><span data-stu-id="84fa3-189">In the following example, the administrator installs help for the DHCP Server module on a computer that does not have network access.</span></span>

<span data-ttu-id="84fa3-190">首先，執行 `Export-Clixml` 以將 **PSModuleInfo** 物件匯出到共用資料夾或卸載式媒體。</span><span class="sxs-lookup"><span data-stu-id="84fa3-190">First, run `Export-Clixml` to export the **PSModuleInfo** object to a shared folder or to removable media.</span></span>

```powershell
$m = Get-Module -Name DhcpServer -ListAvailable
Export-Clixml -Path E:\UsbFlashDrive\DhcpModule.xml -InputObject $m
```

<span data-ttu-id="84fa3-191">接下來，將卸載式媒體傳輸到可存取網際網路的電腦，然後使用匯入 **PSModuleInfo** 物件 `Import-Clixml` 。</span><span class="sxs-lookup"><span data-stu-id="84fa3-191">Next, transport the removable media to a computer that has internet access, and then import the **PSModuleInfo** object with `Import-Clixml`.</span></span> <span data-ttu-id="84fa3-192">執行 `Save-Help` 以儲存已匯入 DhcpServer 模組 **PSModuleInfo** 物件的說明。</span><span class="sxs-lookup"><span data-stu-id="84fa3-192">Run `Save-Help` to save the Help for the imported DhcpServer module **PSModuleInfo** object.</span></span>

```powershell
$deserialized_m = Import-Clixml E:\UsbFlashDrive\DhcpModule.xml
Save-Help -Module $deserialized_m -DestinationPath E:\UsbFlashDrive\SavedHelp
```

<span data-ttu-id="84fa3-193">最後，將卸載式媒體傳輸回沒有網路存取的電腦，然後執行以安裝說明 `Update-Help` 。</span><span class="sxs-lookup"><span data-stu-id="84fa3-193">Finally, transport the removable media back to the computer that does not have network access, and then install the help by running `Update-Help`.</span></span>

```powershell
Update-Help -Module DhcpServer -SourcePath E:\UsbFlashDrive\SavedHelp
```

<span data-ttu-id="84fa3-194">如果沒有參數， `Save-Help` 則會為會話中的所有模組以及所有支援可更新說明的已安裝模組下載說明。</span><span class="sxs-lookup"><span data-stu-id="84fa3-194">Without parameters, `Save-Help` downloads help for all modules in the session and for all installed modules that support Updatable Help.</span></span> <span data-ttu-id="84fa3-195">您必須將模組安裝在 `$env:PSModulePath` 本機電腦或遠端電腦上（您要儲存說明的環境變數值）中所列的目錄中，才能加入模組。</span><span class="sxs-lookup"><span data-stu-id="84fa3-195">To be included, modules must be installed in directories that are listed in the value of the `$env:PSModulePath` environment variable, on either the local computer or on a remote computer for which you want to save help.</span></span> <span data-ttu-id="84fa3-196">這些也是藉由執行命令所傳回的模組 `Get-Help -ListAvailable` 。</span><span class="sxs-lookup"><span data-stu-id="84fa3-196">These are also modules that are returned by running a `Get-Help -ListAvailable` command.</span></span>

## <a name="how-to-update-help-files-in-different-languages"></a><span data-ttu-id="84fa3-197">如何以不同的語言更新說明檔</span><span class="sxs-lookup"><span data-stu-id="84fa3-197">How to update help files in different languages</span></span>

<span data-ttu-id="84fa3-198">根據預設， `Update-Help` 和 `Save-Help` Cmdlet 會以 UI 文化特性和在本機電腦上為 Windows 設定的語言下載說明。</span><span class="sxs-lookup"><span data-stu-id="84fa3-198">By default, the `Update-Help` and `Save-Help` cmdlets download help in the UI culture and language that is set for Windows on the local computer.</span></span> <span data-ttu-id="84fa3-199">如果在本機 UI 文化特性中無法使用指定模組的說明檔， `Update-Help` 並 `Save-Help` 使用 Windows 語言回復規則來尋找最受支援的語言。</span><span class="sxs-lookup"><span data-stu-id="84fa3-199">If help files for the specified modules are not available in the local UI culture, `Update-Help` and `Save-Help` use the Windows language fallback rules to find the best supported language.</span></span>

<span data-ttu-id="84fa3-200">不過，您可以使用和 Cmdlet 的 **UICulture** 參數 `Update-Help` ， `Save-Help` 以在任何可用的 UI 文化特性中下載並安裝說明檔。</span><span class="sxs-lookup"><span data-stu-id="84fa3-200">However, you can use the **UICulture** parameters of the `Update-Help` and `Save-Help` cmdlets to download and install help files in any UI cultures in which they are available.</span></span>

<span data-ttu-id="84fa3-201">例如，若要以日文儲存會話上所有模組的最新說明檔 (Ja-jp) 和法文 (fr-fr) ，請輸入：</span><span class="sxs-lookup"><span data-stu-id="84fa3-201">For example, to save the newest help files for all modules on the session in Japanese (Ja-jp) and French (fr-FR), type:</span></span>

```powershell
Save-Help -Path \Server\Share -UICulture ja-jp, fr-fr
```

<span data-ttu-id="84fa3-202">如果您指定的語言中無法使用模組的說明檔，和 Cmdlet 會傳回 `Update-Help` `Save-Help` 一則錯誤訊息，其中列出每個模組的說明可用的語言，讓您可以選擇最符合您需求的替代方案。</span><span class="sxs-lookup"><span data-stu-id="84fa3-202">If help files for the modules are not available in the languages that you specified, the `Update-Help` and `Save-Help` cmdlets return an error message that lists the languages in which help for each module is available so you can choose the alternative that best meets your needs.</span></span>

> [!NOTE]
> <span data-ttu-id="84fa3-203">目前，可更新的說明內容只會以英文 (en-us) 來發佈。</span><span class="sxs-lookup"><span data-stu-id="84fa3-203">Currently, Updateable Help content is only published in English (en-US).</span></span>

## <a name="how-to-use-online-help"></a><span data-ttu-id="84fa3-204">如何使用線上說明</span><span class="sxs-lookup"><span data-stu-id="84fa3-204">How to use online help</span></span>

<span data-ttu-id="84fa3-205">如果您無法或選擇不更新本機電腦上的說明檔，您仍然可以在線上取得最新的說明檔。</span><span class="sxs-lookup"><span data-stu-id="84fa3-205">If you cannot or choose not to update the help files on your local computer, you can still get the newest help files online.</span></span>

<span data-ttu-id="84fa3-206">若要開啟任何 Cmdlet 或函式的線上說明主題，請使用 Cmdlet 的 **online** 參數 `Get-Help` 。</span><span class="sxs-lookup"><span data-stu-id="84fa3-206">To open the online help topic for any cmdlet or function, use the **Online** parameter of the `Get-Help` cmdlet.</span></span>

<span data-ttu-id="84fa3-207">例如，下列命令會 `Get-Job` 在您的預設網際網路瀏覽器中開啟 Cmdlet 的線上說明主題：</span><span class="sxs-lookup"><span data-stu-id="84fa3-207">For example, the following command opens the online help topic for the `Get-Job` cmdlet in your default internet browser:</span></span>

```powershell
Get-Help Get-Job -Online
```

<span data-ttu-id="84fa3-208">若要取得腳本的線上說明，請使用 **online** 參數和腳本的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="84fa3-208">To get online help for a script, use the **Online** parameter and the full path to the script.</span></span>

<span data-ttu-id="84fa3-209">**Online** 參數不適用於「關於」主題。</span><span class="sxs-lookup"><span data-stu-id="84fa3-209">The **Online** parameter does not work with About topics.</span></span> <span data-ttu-id="84fa3-210">若要查看 PowerShell 的「關於」主題，包括 PowerShell 語言的相關說明主題，請參閱 [Powershell 關於主題](about.md)。</span><span class="sxs-lookup"><span data-stu-id="84fa3-210">To see the about topics for PowerShell, including help topics about the PowerShell language, see [PowerShell About Topics](about.md).</span></span>

## <a name="how-to-minimize-or-prevent-internet-downloads"></a><span data-ttu-id="84fa3-211">如何最小化或防止網際網路下載</span><span class="sxs-lookup"><span data-stu-id="84fa3-211">How to minimize or prevent internet downloads</span></span>

<span data-ttu-id="84fa3-212">若要將網際網路下載降至最低，並為未連線至網際網路的使用者提供可更新的說明，請使用 `Save-Help` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="84fa3-212">To minimize internet downloads and provide Updatable Help to users who are not connected to the internet, use the `Save-Help` cmdlet.</span></span> <span data-ttu-id="84fa3-213">從網際網路下載說明，並將其儲存到網路共用。</span><span class="sxs-lookup"><span data-stu-id="84fa3-213">Download help from the internet and save it to a network share.</span></span> <span data-ttu-id="84fa3-214">然後，建立 `Update-Help` 在所有電腦上執行命令的群組原則設定或排程工作。</span><span class="sxs-lookup"><span data-stu-id="84fa3-214">Then, create a Group Policy setting or scheduled job that runs an `Update-Help` command on all computers.</span></span> <span data-ttu-id="84fa3-215">將 Cmdlet 的 **SourcePath** 參數值設定 `Update-Help` 為網路共用。</span><span class="sxs-lookup"><span data-stu-id="84fa3-215">Set the value of the **SourcePath** parameter of the `Update-Help` cmdlet to the network share.</span></span>

<span data-ttu-id="84fa3-216">若要防止可存取網際網路的使用者從網際網路下載可更新的說明，請使用 **設定 update-help 群組原則設定的預設來源路徑** 。</span><span class="sxs-lookup"><span data-stu-id="84fa3-216">To prevent users who have internet access from downloading Updatable Help from the internet, use the **Set the default source path for Update-Help** Group Policy setting.</span></span>

<span data-ttu-id="84fa3-217">此群組原則設定會以隱含方式將 **SourcePath** 參數（具有您指定的檔案系統位置）新增至 `Update-Help` 每個受影響電腦上的每個命令。</span><span class="sxs-lookup"><span data-stu-id="84fa3-217">This Group Policy setting implicitly adds the **SourcePath** parameter, with the filesystem location that you specify, to every `Update-Help` command on every affected computer.</span></span> <span data-ttu-id="84fa3-218">使用者可以明確地使用 **SourcePath** 參數來指定不同的檔案系統位置，但是無法排除 **sourcepath** 參數並從網際網路下載說明。</span><span class="sxs-lookup"><span data-stu-id="84fa3-218">Users can use the **SourcePath** parameter explicitly to specify a different filesystem location, but they cannot exclude the **SourcePath** parameter and download help from the internet.</span></span>

> [!NOTE]
> <span data-ttu-id="84fa3-219">[ **設定 update-help 群組原則的預設來源路徑] 設定** 會出現在 [ **電腦** 設定和 **使用者** 設定] 下。</span><span class="sxs-lookup"><span data-stu-id="84fa3-219">The **Set the default source path for Update-Help** group policy setting appears under **Computer Configuration** and **User Configuration** .</span></span> <span data-ttu-id="84fa3-220">不過，只有 [ **電腦** 設定] 下的原則設定才會生效。</span><span class="sxs-lookup"><span data-stu-id="84fa3-220">However, only the policy setting under **Computer Configuration** is effective.</span></span> <span data-ttu-id="84fa3-221">[ **使用者** 設定] 下的原則設定會被忽略。</span><span class="sxs-lookup"><span data-stu-id="84fa3-221">The policy setting under **User Configuration** is ignored.</span></span>

<span data-ttu-id="84fa3-222">如需詳細資訊，請參閱 [about_Group_Policy_Settings](about_Group_Policy_Settings.md)。</span><span class="sxs-lookup"><span data-stu-id="84fa3-222">For more information, see [about_Group_Policy_Settings](about_Group_Policy_Settings.md).</span></span>

## <a name="how-to-update-help-for-non-standard-modules"></a><span data-ttu-id="84fa3-223">如何更新非標準模組的說明</span><span class="sxs-lookup"><span data-stu-id="84fa3-223">How to update help for non-standard modules</span></span>

<span data-ttu-id="84fa3-224">若要更新或儲存指令程式的 **ListAvailable** 參數未傳回的模組說明 `Get-Module` ，請將模組匯入到目前的會話，然後再執行 `Update-Help` 或 `Save-Help` 命令。</span><span class="sxs-lookup"><span data-stu-id="84fa3-224">To update or save help for a module that is not returned by the **ListAvailable** parameter of the `Get-Module` cmdlet, import the module into the current session before running an `Update-Help` or `Save-Help` command.</span></span> <span data-ttu-id="84fa3-225">在遠端電腦上執行 `Save-Help` 命令之前，請將模組匯入目前的會話，或 `Invoke-Command` 連接到遠端電腦的腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="84fa3-225">On a remote computer, before running the `Save-Help` command, import the module into the current Session, or `Invoke-Command` script block, that is connected to the remote computer.</span></span>

<span data-ttu-id="84fa3-226">當模組在目前的會話中時，請執行 `Update-Help` 或 `Save-Help` 不含參數的 Cmdlet，或使用 **module** 參數指定模組名稱。</span><span class="sxs-lookup"><span data-stu-id="84fa3-226">When the module is in the current session, run the `Update-Help` or `Save-Help` cmdlets without parameters, or use the **Module** parameter to specify the module name.</span></span>

<span data-ttu-id="84fa3-227">和 Cmdlet 的 **模組** 參數 `Update-Help` `Save-Help` 只接受模組名稱。</span><span class="sxs-lookup"><span data-stu-id="84fa3-227">The **Module** parameters of the `Update-Help` and `Save-Help` cmdlets accept only a module name.</span></span> <span data-ttu-id="84fa3-228">它們不接受模組檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="84fa3-228">They do not accept the path to a module file.</span></span>

<span data-ttu-id="84fa3-229">使用這項技術來更新或儲存任何不是由 Cmdlet 的 **ListAvailable** 參數所傳回之模組的說明 `Get-Module` ，例如安裝在環境變數未列出之位置中的模組 `$env:PSModulePath` ，或不是格式正確的模組 (模組目錄不包含至少一個檔案，其 basename 與目錄名稱相同) 。</span><span class="sxs-lookup"><span data-stu-id="84fa3-229">Use this technique to update or save help for any module that is not returned by the **ListAvailable** parameter of the `Get-Module` cmdlet, such as a module that is installed in a location that is not listed in the `$env:PSModulePath` environment variable, or a module that is not well-formed (the module directory does not contain at least one file whose basename is the same as the directory name).</span></span>

## <a name="how-to-support-updatable-help"></a><span data-ttu-id="84fa3-230">如何支援可更新的說明</span><span class="sxs-lookup"><span data-stu-id="84fa3-230">How to support updatable help</span></span>

<span data-ttu-id="84fa3-231">如果您撰寫模組，您可以支援模組的線上說明和可更新說明。</span><span class="sxs-lookup"><span data-stu-id="84fa3-231">If you author a module, you can support online help and Updatable Help for your modules.</span></span> <span data-ttu-id="84fa3-232">如需詳細資訊，請參閱 Microsoft Docs 中的 [支援可更新](/powershell/scripting/developer/help/supporting-updatable-help) 的說明和 [支援線上說明](/powershell/scripting/developer/module/supporting-online-help) 。</span><span class="sxs-lookup"><span data-stu-id="84fa3-232">For more information, see [Supporting Updatable Help](/powershell/scripting/developer/help/supporting-updatable-help) and [Supporting Online Help](/powershell/scripting/developer/module/supporting-online-help) in the Microsoft Docs.</span></span>

<span data-ttu-id="84fa3-233">PowerShell 嵌入式管理單元或以批註為基礎的說明無法使用可更新的說明。</span><span class="sxs-lookup"><span data-stu-id="84fa3-233">Updatable help not available for PowerShell snap-ins or comment-based help.</span></span>

## <a name="remarks"></a><span data-ttu-id="84fa3-234">備註</span><span class="sxs-lookup"><span data-stu-id="84fa3-234">Remarks</span></span>

<span data-ttu-id="84fa3-235">`Update-Help` `Save-Help` Windows 預先安裝環境 (Windows PE) 不支援和 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="84fa3-235">The `Update-Help` and `Save-Help` cmdlets are not supported on Windows Preinstallation Environment (Windows PE).</span></span>

## <a name="see-also"></a><span data-ttu-id="84fa3-236">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84fa3-236">See also</span></span>

[<span data-ttu-id="84fa3-237">Get-Help</span><span class="sxs-lookup"><span data-stu-id="84fa3-237">Get-Help</span></span>](xref:Microsoft.PowerShell.Core.Get-Help)

[<span data-ttu-id="84fa3-238">Save-Help</span><span class="sxs-lookup"><span data-stu-id="84fa3-238">Save-Help</span></span>](xref:Microsoft.PowerShell.Core.Save-Help)

[<span data-ttu-id="84fa3-239">Update-Help</span><span class="sxs-lookup"><span data-stu-id="84fa3-239">Update-Help</span></span>](xref:Microsoft.PowerShell.Core.Update-Help)
