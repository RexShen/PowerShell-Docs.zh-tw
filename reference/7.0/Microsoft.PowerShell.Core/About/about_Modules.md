---
description: 說明如何安裝、匯入及使用 PowerShell 模組。
Locale: en-US
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_modules?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Modules
ms.openlocfilehash: ab4e9658ed4820c3ae84ac1cd9a55b59cc8017ab
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564474"
---
# <a name="about-modules"></a><span data-ttu-id="86041-103">關於模組</span><span class="sxs-lookup"><span data-stu-id="86041-103">About Modules</span></span>

## <a name="short-description"></a><span data-ttu-id="86041-104">簡短描述</span><span class="sxs-lookup"><span data-stu-id="86041-104">Short Description</span></span>
<span data-ttu-id="86041-105">說明如何安裝、匯入及使用 PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="86041-105">Explains how to install, import, and use PowerShell modules.</span></span>

## <a name="long-description"></a><span data-ttu-id="86041-106">完整描述</span><span class="sxs-lookup"><span data-stu-id="86041-106">Long Description</span></span>

<span data-ttu-id="86041-107">模組是包含 PowerShell 成員（例如 Cmdlet、提供者、函式、工作流程、變數和別名）的套件。</span><span class="sxs-lookup"><span data-stu-id="86041-107">A module is a package that contains PowerShell members, such as cmdlets, providers, functions, workflows, variables, and aliases.</span></span>

<span data-ttu-id="86041-108">撰寫命令者可以使用模組來組織其命令，並與其他人分享。</span><span class="sxs-lookup"><span data-stu-id="86041-108">People who write commands can use modules to organize their commands and share them with others.</span></span> <span data-ttu-id="86041-109">接收模組的人員可以將模組中的命令新增至其 PowerShell 會話，並如同內建命令一般使用它們。</span><span class="sxs-lookup"><span data-stu-id="86041-109">People who receive modules can add the commands in the modules to their PowerShell sessions and use them just like the built-in commands.</span></span>

<span data-ttu-id="86041-110">本主題說明如何使用 PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="86041-110">This topic explains how to use PowerShell modules.</span></span> <span data-ttu-id="86041-111">如需如何撰寫 PowerShell 模組的詳細資訊，請參閱 [撰寫 Powershell 模組](/powershell/scripting/developer/module/writing-a-windows-powershell-module)。</span><span class="sxs-lookup"><span data-stu-id="86041-111">For information about how to write PowerShell modules, see [Writing a PowerShell Module](/powershell/scripting/developer/module/writing-a-windows-powershell-module).</span></span>

## <a name="what-is-a-module"></a><span data-ttu-id="86041-112">什麼是模組？</span><span class="sxs-lookup"><span data-stu-id="86041-112">What Is a Module?</span></span>

<span data-ttu-id="86041-113">模組是包含 PowerShell 成員（例如 Cmdlet、提供者、函式、工作流程、變數和別名）的套件。</span><span class="sxs-lookup"><span data-stu-id="86041-113">A module is a package that contains PowerShell members, such as cmdlets, providers, functions, workflows, variables, and aliases.</span></span> <span data-ttu-id="86041-114">此封裝的成員可以在 PowerShell 腳本、已編譯的 DLL 或兩者的組合中執行。</span><span class="sxs-lookup"><span data-stu-id="86041-114">The members of this package can be implemented in a PowerShell script, a compiled DLL, or a combination of both.</span></span> <span data-ttu-id="86041-115">這些檔案通常會在單一目錄中群組在一起。</span><span class="sxs-lookup"><span data-stu-id="86041-115">These files are usually grouped together in a single directory.</span></span> <span data-ttu-id="86041-116">如需詳細資訊，請參閱 SDK 檔中的 [瞭解 Windows PowerShell 模組](/powershell/scripting/developer/module/understanding-a-windows-powershell-module) 。</span><span class="sxs-lookup"><span data-stu-id="86041-116">For more information, see [Understanding a Windows PowerShell Module](/powershell/scripting/developer/module/understanding-a-windows-powershell-module) in the SDK documentation.</span></span>

## <a name="module-auto-loading"></a><span data-ttu-id="86041-117">模組自動載入</span><span class="sxs-lookup"><span data-stu-id="86041-117">Module Auto-Loading</span></span>

<span data-ttu-id="86041-118">從 PowerShell 3.0 開始，當您第一次在已安裝的模組中執行任何命令時，PowerShell 會自動匯入模組。</span><span class="sxs-lookup"><span data-stu-id="86041-118">Beginning in PowerShell 3.0, PowerShell imports modules automatically the first time that you run any command in an installed module.</span></span> <span data-ttu-id="86041-119">您現在可以使用模組中的命令，而不需要任何設定或設定檔設定，因此在電腦上安裝模組之後不需要進行管理。</span><span class="sxs-lookup"><span data-stu-id="86041-119">You can now use the commands in a module without any set-up or profile configuration, so there's no need to manage modules after you install them on your computer.</span></span>

<span data-ttu-id="86041-120">模組中的命令也比較容易找到。</span><span class="sxs-lookup"><span data-stu-id="86041-120">The commands in a module are also easier to find.</span></span> <span data-ttu-id="86041-121">`Get-Command`Cmdlet 現在會取得所有已安裝模組中的所有命令，即使它們尚未在會話中也一樣。</span><span class="sxs-lookup"><span data-stu-id="86041-121">The `Get-Command` cmdlet now gets all commands in all installed modules, even if they are not yet in the session.</span></span> <span data-ttu-id="86041-122">您可以尋找命令並使用它，而不需要先匯入模組。</span><span class="sxs-lookup"><span data-stu-id="86041-122">You can find a command and use it without importing needing to import the module first.</span></span>

<span data-ttu-id="86041-123">下列每個範例都會將包含的 CimCmdlets 模組匯 `Get-CimInstance` 入到您的會話。</span><span class="sxs-lookup"><span data-stu-id="86041-123">Each of the following examples cause the CimCmdlets module, which contains `Get-CimInstance`, to be imported into your session.</span></span>

- <span data-ttu-id="86041-124">執行命令</span><span class="sxs-lookup"><span data-stu-id="86041-124">Run the Command</span></span>

  ```powershell
  Get-CimInstance Win32_OperatingSystem
  ```

- <span data-ttu-id="86041-125">取得命令</span><span class="sxs-lookup"><span data-stu-id="86041-125">Get the Command</span></span>

  ```powershell
  Get-Command Get-CimInstance
  ```

- <span data-ttu-id="86041-126">命令的取得協助</span><span class="sxs-lookup"><span data-stu-id="86041-126">Get Help for the Command</span></span>

  ```powershell
  Get-Help Get-CimInstance
  ```

<span data-ttu-id="86041-127">`Get-Command` 包含萬用字元 () 的命令 `*` 會被視為用於探索、不使用，且不會匯入任何模組。</span><span class="sxs-lookup"><span data-stu-id="86041-127">`Get-Command` commands that include a wildcard character (`*`) are considered to be for discovery, not use, and do not import any modules.</span></span>

<span data-ttu-id="86041-128">只有儲存在 PSModulePath 環境變數所指定之位置中的模組才會自動匯入。</span><span class="sxs-lookup"><span data-stu-id="86041-128">Only modules that are stored in the location specified by the PSModulePath environment variable are automatically imported.</span></span> <span data-ttu-id="86041-129">您必須執行 Cmdlet 來匯入其他位置中的模組 `Import-Module` 。</span><span class="sxs-lookup"><span data-stu-id="86041-129">Modules in other locations must be imported by running the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="86041-130">此外，使用 PowerShell 提供者的命令不會自動匯入模組。</span><span class="sxs-lookup"><span data-stu-id="86041-130">Also, commands that use PowerShell providers do not automatically import a module.</span></span> <span data-ttu-id="86041-131">例如，如果您使用需要 WSMan：磁片磁碟機的命令（例如 `Get-PSSessionConfiguration` Cmdlet），您可能需要執行指令程式 `Import-Module` 來匯入包含該磁片磁碟機的「 **Microsoft WSMan. 管理**」模組。 `WSMan:`</span><span class="sxs-lookup"><span data-stu-id="86041-131">For example, if you use a command that requires the WSMan: drive, such as the `Get-PSSessionConfiguration` cmdlet, you might need to run the `Import-Module` cmdlet to import the **Microsoft.WSMan.Management** module that includes the `WSMan:` drive.</span></span>

<span data-ttu-id="86041-132">您仍然可以執行 `Import-Module` 命令以匯入模組，並使用 `$PSModuleAutoloadingPreference` 變數來啟用、停用及設定自動匯入模組。</span><span class="sxs-lookup"><span data-stu-id="86041-132">You can still run the `Import-Module` command to import a module and use the `$PSModuleAutoloadingPreference` variable to enable, disable and configure automatic importing of modules.</span></span> <span data-ttu-id="86041-133">如需詳細資訊，請參閱 [about_Preference_Variables](about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="86041-133">For more information, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

## <a name="how-to-use-a-module"></a><span data-ttu-id="86041-134">如何使用模組</span><span class="sxs-lookup"><span data-stu-id="86041-134">How to Use a Module</span></span>

<span data-ttu-id="86041-135">若要使用模組，請執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="86041-135">To use a module, perform the following tasks:</span></span>

1. <span data-ttu-id="86041-136">安裝模組</span><span class="sxs-lookup"><span data-stu-id="86041-136">Install the module.</span></span> <span data-ttu-id="86041-137">(這通常會為您完成)。</span><span class="sxs-lookup"><span data-stu-id="86041-137">(This is often done for you.)</span></span>
1. <span data-ttu-id="86041-138">尋找模組所新增的命令。</span><span class="sxs-lookup"><span data-stu-id="86041-138">Find the commands that the module added.</span></span>
1. <span data-ttu-id="86041-139">使用模組所新增的命令。</span><span class="sxs-lookup"><span data-stu-id="86041-139">Use the commands that the module added.</span></span>

<span data-ttu-id="86041-140">此主題說明如何執行這些工作。</span><span class="sxs-lookup"><span data-stu-id="86041-140">This topic explains how to perform these tasks.</span></span> <span data-ttu-id="86041-141">它也包含管理模組的其他實用資訊。</span><span class="sxs-lookup"><span data-stu-id="86041-141">It also includes other useful information about managing modules.</span></span>

## <a name="how-to-install-a-module"></a><span data-ttu-id="86041-142">如何安裝模組</span><span class="sxs-lookup"><span data-stu-id="86041-142">How to Install a Module</span></span>

<span data-ttu-id="86041-143">如果您以資料夾的形式接收模組，則必須先將它安裝在您的電腦上，才能在 PowerShell 中使用。</span><span class="sxs-lookup"><span data-stu-id="86041-143">If you receive a module as a folder with files in it, you need to install it on your computer before you can use it in PowerShell.</span></span>

<span data-ttu-id="86041-144">大部分的模組會為您安裝。</span><span class="sxs-lookup"><span data-stu-id="86041-144">Most modules are installed for you.</span></span> <span data-ttu-id="86041-145">PowerShell 隨附數個預先安裝的模組，有時稱為 _核心_ 模組。</span><span class="sxs-lookup"><span data-stu-id="86041-145">PowerShell comes with several preinstalled modules, sometimes called the _core_ modules.</span></span> <span data-ttu-id="86041-146">在以 Windows 為基礎的電腦上，如果作業系統隨附的功能具有管理它們的 Cmdlet，則會預先安裝這些模組。</span><span class="sxs-lookup"><span data-stu-id="86041-146">On Windows-based computers, if features that are included with the operating system have cmdlets to manage them, those modules are preinstalled.</span></span> <span data-ttu-id="86041-147">當您使用安裝 Windows 功能時，您可以使用伺服器管理員中的 [新增角色及功能]，或主控台中的 [開啟或關閉 Windows 功能] 對話方塊，安裝任何屬於功能的 PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="86041-147">When you install a Windows feature, by using, for example, the Add Roles and Features Wizard in Server Manager, or the Turn Windows features on or off dialog box in Control Panel, any PowerShell modules that are part of the feature are installed.</span></span> <span data-ttu-id="86041-148">其他許多模組則包含在安裝模組的安裝程式或 Setup 程式中。</span><span class="sxs-lookup"><span data-stu-id="86041-148">Many other modules come in an installer or Setup program that installs the module.</span></span>

<span data-ttu-id="86041-149">使用下列命令來建立目前使用者的 **模組** 目錄：</span><span class="sxs-lookup"><span data-stu-id="86041-149">Use the following command to create a **Modules** directory for the current user:</span></span>

```powershell
New-Item -Type Directory -Path $HOME\Documents\PowerShell\Modules
```

<span data-ttu-id="86041-150">將整個模組資料夾複製到 Modules 目錄中。</span><span class="sxs-lookup"><span data-stu-id="86041-150">Copy the entire module folder into the Modules directory.</span></span> <span data-ttu-id="86041-151">您可以使用任何方法複製資料夾，包括 Windows 檔案總管和 Cmd.exe，以及 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="86041-151">You can use any method to copy the folder, including Windows Explorer and Cmd.exe, as well as PowerShell.</span></span> <span data-ttu-id="86041-152">在 PowerShell 中，請使用 `Copy-Item` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="86041-152">In PowerShell use the `Copy-Item` cmdlet.</span></span> <span data-ttu-id="86041-153">例如，若要將 MyModule 資料夾從複製 `C:\ps-test\MyModule` 到模組目錄，請輸入：</span><span class="sxs-lookup"><span data-stu-id="86041-153">For example, to copy the MyModule folder from `C:\ps-test\MyModule` to the Modules directory, type:</span></span>

```powershell
Copy-Item -Path C:\ps-test\MyModule -Destination `
    $HOME\Documents\PowerShell\Modules
```

<span data-ttu-id="86041-154">您可以在任何位置安裝模組，但在預設模組位置安裝模組可讓您更輕鬆地管理模組。</span><span class="sxs-lookup"><span data-stu-id="86041-154">You can install a module in any location, but installing your modules in a default module location makes them easier to manage.</span></span> <span data-ttu-id="86041-155">如需預設模組位置的詳細資訊，請參閱 [模組和 DSC 資源位置，以及 PSModulePath](#module-and-dsc-resource-locations-and-psmodulepath) 一節。</span><span class="sxs-lookup"><span data-stu-id="86041-155">For more information about the default module locations, see the [Module and DSC Resource Locations, and PSModulePath](#module-and-dsc-resource-locations-and-psmodulepath) section.</span></span>

## <a name="how-to-find-installed-modules"></a><span data-ttu-id="86041-156">如何尋找已安裝的模組</span><span class="sxs-lookup"><span data-stu-id="86041-156">How to Find Installed Modules</span></span>

<span data-ttu-id="86041-157">若要尋找已安裝在預設模組位置，但尚未匯入到您工作階段的模組，請輸入：</span><span class="sxs-lookup"><span data-stu-id="86041-157">To find modules that are installed in a default module location, but not yet imported into your session, type:</span></span>

```powershell
Get-Module -ListAvailable
```

<span data-ttu-id="86041-158">若要尋找已匯入至會話的模組，請在 PowerShell 提示字元中輸入：</span><span class="sxs-lookup"><span data-stu-id="86041-158">To find the modules that have already been imported into your session, at the PowerShell prompt, type:</span></span>

```powershell
Get-Module
```

<span data-ttu-id="86041-159">如需有關 Cmdlet 的詳細資訊 `Get-Module` ，請參閱 [get-help](xref:Microsoft.PowerShell.Core.Get-Module)。</span><span class="sxs-lookup"><span data-stu-id="86041-159">For more information about the `Get-Module` cmdlet, see [Get-Module](xref:Microsoft.PowerShell.Core.Get-Module).</span></span>

## <a name="how-to-find-the-commands-in-a-module"></a><span data-ttu-id="86041-160">如何尋找模組中的命令</span><span class="sxs-lookup"><span data-stu-id="86041-160">How to Find the Commands in a Module</span></span>

<span data-ttu-id="86041-161">使用 `Get-Command` Cmdlet 來尋找所有可用的命令。</span><span class="sxs-lookup"><span data-stu-id="86041-161">Use the `Get-Command` cmdlet to find all available commands.</span></span> <span data-ttu-id="86041-162">您可以使用 Cmdlet 的參數 `Get-Command` 來篩選命令，例如依模組、名稱和名詞。</span><span class="sxs-lookup"><span data-stu-id="86041-162">You can use the parameters of the `Get-Command` cmdlet to filter commands such as by module, name, and noun.</span></span>

<span data-ttu-id="86041-163">若要尋找模組中的所有命令，請輸入：</span><span class="sxs-lookup"><span data-stu-id="86041-163">To find all commands in a module, type:</span></span>

```powershell
Get-Command -Module <module-name>
```

<span data-ttu-id="86041-164">例如，若要尋找 BitsTransfer 模組中的命令，請輸入：</span><span class="sxs-lookup"><span data-stu-id="86041-164">For example, to find the commands in the BitsTransfer module, type:</span></span>

```powershell
Get-Command -Module BitsTransfer
```

<span data-ttu-id="86041-165">如需有關 Cmdlet 的詳細資訊 `Get-Command` ，請參閱 [Get 命令](xref:Microsoft.PowerShell.Core.Get-Command)。</span><span class="sxs-lookup"><span data-stu-id="86041-165">For more information about the `Get-Command` cmdlet, see [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command).</span></span>

## <a name="how-to-get-help-for-the-commands-in-a-module"></a><span data-ttu-id="86041-166">如何針對模組中的命令取得協助</span><span class="sxs-lookup"><span data-stu-id="86041-166">How to Get Help for the Commands in a Module</span></span>

<span data-ttu-id="86041-167">如果模組包含所匯出命令的說明檔，則 `Get-Help` Cmdlet 會顯示說明主題。</span><span class="sxs-lookup"><span data-stu-id="86041-167">If the module contains Help files for the commands that it exports, the `Get-Help` cmdlet will display the Help topics.</span></span> <span data-ttu-id="86041-168">使用您在 `Get-Help` PowerShell 中用來取得任何命令之說明的相同命令格式。</span><span class="sxs-lookup"><span data-stu-id="86041-168">Use the same `Get-Help` command format that you would use to get help for any command in PowerShell.</span></span>

<span data-ttu-id="86041-169">從 PowerShell 3.0 開始，您可以下載模組的說明檔，並下載說明檔的更新，讓它們永遠不會過時。</span><span class="sxs-lookup"><span data-stu-id="86041-169">Beginning in PowerShell 3.0, you can download Help files for a module and download updates to the Help files so they are never obsolete.</span></span>

<span data-ttu-id="86041-170">若要取得模組中之命令的說明，請輸入：</span><span class="sxs-lookup"><span data-stu-id="86041-170">To get help for a commands in a module, type:</span></span>

```powershell
Get-Help <command-name>
```

<span data-ttu-id="86041-171">若要取得模組中命令的線上說明，請輸入：</span><span class="sxs-lookup"><span data-stu-id="86041-171">To get help online for command in a module, type:</span></span>

```powershell
Get-Help <command-name> -Online
```

<span data-ttu-id="86041-172">若要下載並安裝模組中命令的說明檔，請輸入：</span><span class="sxs-lookup"><span data-stu-id="86041-172">To download and install the help files for the commands in a module, type:</span></span>

```powershell
Update-Help -Module <module-name>
```

<span data-ttu-id="86041-173">如需詳細資訊，請參閱 [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 和 [update-help](xref:Microsoft.PowerShell.Core.Update-Help)。</span><span class="sxs-lookup"><span data-stu-id="86041-173">For more information, see [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) and [Update-Help](xref:Microsoft.PowerShell.Core.Update-Help).</span></span>

## <a name="how-to-import-a-module"></a><span data-ttu-id="86041-174">如何匯入模組</span><span class="sxs-lookup"><span data-stu-id="86041-174">How to Import a Module</span></span>

<span data-ttu-id="86041-175">您可能必須匯入模組或匯入模組檔案。</span><span class="sxs-lookup"><span data-stu-id="86041-175">You might have to import a module or import a module file.</span></span> <span data-ttu-id="86041-176">當模組不是安裝在 **PSModulePath** 環境變數所指定的位置， `$env:PSModulePath` 或模組是由檔案（例如 .dll 或 .psm1 檔案）所組成，而非以資料夾形式傳遞的一般模組時，就需要匯入。</span><span class="sxs-lookup"><span data-stu-id="86041-176">Importing is required when a module is not installed in the locations specified by the **PSModulePath** environment variable, `$env:PSModulePath`, or the module consists of file, such as a .dll or .psm1 file, instead of typical module that is delivered as a folder.</span></span>

<span data-ttu-id="86041-177">您也可以選擇匯入模組，讓您可以使用命令的參數 `Import-Module` ，例如 Prefix 參數，將特殊的前置詞加入至所有匯入命令的名詞名稱，或 **NoClobber** 參數，以防止模組加入將隱藏或取代會話中現有命令的命令。</span><span class="sxs-lookup"><span data-stu-id="86041-177">You might also choose to import a module so that you can use the parameters of the `Import-Module` command, such as the Prefix parameter, which adds a distinctive prefix to the noun names of all imported commands, or the **NoClobber** parameter, which prevents the module from adding commands that would hide or replace existing commands in the session.</span></span>

<span data-ttu-id="86041-178">若要匯入模組，請使用 `Import-Module` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="86041-178">To import modules, use the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="86041-179">若要將 PSModulePath 位置中的模組匯入到目前的工作階段，請使用下列命令格式。</span><span class="sxs-lookup"><span data-stu-id="86041-179">To import modules in a PSModulePath location into the current session, use the following command format.</span></span>

```powershell
Import-Module <module-name>
```

<span data-ttu-id="86041-180">例如，下列命令會將 BitsTransfer 模組匯入到目前的會話。</span><span class="sxs-lookup"><span data-stu-id="86041-180">For example, the following command imports the BitsTransfer module into the current session.</span></span>

```powershell
Import-Module BitsTransfer
```

<span data-ttu-id="86041-181">若要匯入不在預設模組位置中的模組，請在命令中使用模組資料夾的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="86041-181">To import a module that is not in a default module location, use the fully qualified path to the module folder in the command.</span></span>

<span data-ttu-id="86041-182">例如，若要將目錄中的 TestCmdlets 模組新增 `C:\ps-test` 至您的會話，請輸入：</span><span class="sxs-lookup"><span data-stu-id="86041-182">For example, to add the TestCmdlets module in the `C:\ps-test` directory to your session, type:</span></span>

```powershell
Import-Module C:\ps-test\TestCmdlets
```

<span data-ttu-id="86041-183">若要匯入未包含在模組資料夾中的模組檔案，請在命令中使用模組檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="86041-183">To import a module file that is not contained in a module folder, use the fully qualified path to the module file in the command.</span></span>

<span data-ttu-id="86041-184">例如，若要將目錄中的 TestCmdlets.dll 模組新增 `C:\ps-test` 至您的會話，請輸入：</span><span class="sxs-lookup"><span data-stu-id="86041-184">For example, to add the TestCmdlets.dll module in the `C:\ps-test` directory to your session, type:</span></span>

```powershell
Import-Module C:\ps-test\TestCmdlets.dll
```

<span data-ttu-id="86041-185">如需有關將模組加入至會話的詳細資訊，請參閱 [import-module](xref:Microsoft.PowerShell.Core.Import-Module)。</span><span class="sxs-lookup"><span data-stu-id="86041-185">For more information about adding modules to your session, see [Import-Module](xref:Microsoft.PowerShell.Core.Import-Module).</span></span>

## <a name="how-to-import-a-module-into-every-session"></a><span data-ttu-id="86041-186">如何將模組匯入到每個會話</span><span class="sxs-lookup"><span data-stu-id="86041-186">How to Import a Module into Every Session</span></span>

<span data-ttu-id="86041-187">此 `Import-Module` 命令會將模組匯入到您目前的 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="86041-187">The `Import-Module` command imports modules into your current PowerShell session.</span></span> <span data-ttu-id="86041-188">若要將模組匯入到您啟動的每個 PowerShell 會話，請將 `Import-Module` 命令新增至您的 powershell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="86041-188">To import a module into every PowerShell session that you start, add the `Import-Module` command to your PowerShell profile.</span></span>

<span data-ttu-id="86041-189">如需設定檔的詳細資訊，請參閱 [about_Profiles](about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="86041-189">For more information about profiles, see [about_Profiles](about_Profiles.md).</span></span>

## <a name="how-to-remove-a-module"></a><span data-ttu-id="86041-190">如何移除模組</span><span class="sxs-lookup"><span data-stu-id="86041-190">How to Remove a Module</span></span>

<span data-ttu-id="86041-191">當您移除模組時，會從工作階段刪除模組所加入的命令。</span><span class="sxs-lookup"><span data-stu-id="86041-191">When you remove a module, the commands that the module added are deleted from the session.</span></span>

<span data-ttu-id="86041-192">若要從您的會話移除模組，請使用下列命令格式。</span><span class="sxs-lookup"><span data-stu-id="86041-192">To remove a module from your session, use the following command format.</span></span>

```powershell
Remove-Module <module-name>
```

<span data-ttu-id="86041-193">例如，下列命令會從目前的會話移除 BitsTransfer 模組。</span><span class="sxs-lookup"><span data-stu-id="86041-193">For example, the following command removes the BitsTransfer module from the current session.</span></span>

```powershell
Remove-Module BitsTransfer
```

<span data-ttu-id="86041-194">移除模組會反轉匯入模組的作業。</span><span class="sxs-lookup"><span data-stu-id="86041-194">Removing a module reverses the operation of importing a module.</span></span> <span data-ttu-id="86041-195">移除模組並不會解除安裝模組。</span><span class="sxs-lookup"><span data-stu-id="86041-195">Removing a module does not uninstall the module.</span></span> <span data-ttu-id="86041-196">如需詳細資訊，請參閱 [移除模組](xref:Microsoft.PowerShell.Core.Remove-Module)。</span><span class="sxs-lookup"><span data-stu-id="86041-196">For more information, see [Remove-Module](xref:Microsoft.PowerShell.Core.Remove-Module).</span></span>

## <a name="module-and-dsc-resource-locations-and-psmodulepath"></a><span data-ttu-id="86041-197">模組和 DSC 資源位置，以及 PSModulePath</span><span class="sxs-lookup"><span data-stu-id="86041-197">Module and DSC Resource Locations, and PSModulePath</span></span>

<span data-ttu-id="86041-198">`$env:PSModulePath`環境變數包含要搜尋以尋找模組和資源的資料夾位置清單。</span><span class="sxs-lookup"><span data-stu-id="86041-198">The `$env:PSModulePath` environment variable contains a list of folder locations that are searched to find modules and resources.</span></span>

<span data-ttu-id="86041-199">依預設，指派給的有效位置 `$env:PSModulePath` 為：</span><span class="sxs-lookup"><span data-stu-id="86041-199">By default, the effective locations assigned to `$env:PSModulePath` are:</span></span>

- <span data-ttu-id="86041-200">全系統位置： `$PSHOME\Modules`</span><span class="sxs-lookup"><span data-stu-id="86041-200">System-wide locations: `$PSHOME\Modules`</span></span>

  <span data-ttu-id="86041-201">這些資料夾包含隨附于 Windows 和 PowerShell 的模組。</span><span class="sxs-lookup"><span data-stu-id="86041-201">These folders contain modules that ship with Windows and PowerShell.</span></span>

  <span data-ttu-id="86041-202">PowerShell 隨附的 DSC 資源會儲存在 `$PSHOME\Modules\PSDesiredStateConfiguration\DSCResources` 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="86041-202">DSC resources that are included with PowerShell are stored in the `$PSHOME\Modules\PSDesiredStateConfiguration\DSCResources` folder.</span></span>

- <span data-ttu-id="86041-203">使用者專屬的模組：這些是使用者在使用者範圍內所安裝的模組。</span><span class="sxs-lookup"><span data-stu-id="86041-203">User-specific modules: These are modules installed by the user in the user's scope.</span></span> <span data-ttu-id="86041-204">`Install-Module` 具有 **範圍** 參數，可讓您指定是否為目前的使用者或所有使用者安裝模組。</span><span class="sxs-lookup"><span data-stu-id="86041-204">`Install-Module` has a **Scope** parameter that allows you to specify whether the module is installed for the current user or for all users.</span></span> <span data-ttu-id="86041-205">如需詳細資訊，請參閱 [Install 模組](xref:PowerShellGet.Install-Module)。</span><span class="sxs-lookup"><span data-stu-id="86041-205">For more information, see [Install-Module](xref:PowerShellGet.Install-Module).</span></span>

  <span data-ttu-id="86041-206">Windows 上使用者專屬的 **CurrentUser** 位置是 `PowerShell\Modules` 位於使用者設定檔中檔位置的資料夾。</span><span class="sxs-lookup"><span data-stu-id="86041-206">The user-specific **CurrentUser** location on Windows is the `PowerShell\Modules` folder located in the **Documents** location in your user profile.</span></span> <span data-ttu-id="86041-207">該位置的特定路徑會因 Windows 版本而異，以及您是否正在使用資料夾重新導向。</span><span class="sxs-lookup"><span data-stu-id="86041-207">The specific path of that location varies by version of Windows and whether or not you are using folder redirection.</span></span> <span data-ttu-id="86041-208">Microsoft OneDrive 也可以變更您的 [ **檔** ] 資料夾的位置。</span><span class="sxs-lookup"><span data-stu-id="86041-208">Microsoft OneDrive can also change the location of your **Documents** folder.</span></span>

  <span data-ttu-id="86041-209">根據預設，在 Windows 10 上，該位置為 `$HOME\Documents\PowerShell\Modules` 。</span><span class="sxs-lookup"><span data-stu-id="86041-209">By default, on Windows 10, that location is `$HOME\Documents\PowerShell\Modules`.</span></span> <span data-ttu-id="86041-210">在 Linux 或 Mac 上， **CurrentUser** 位置為 `$HOME/.local/share/powershell/Modules` 。</span><span class="sxs-lookup"><span data-stu-id="86041-210">On Linux or Mac, the **CurrentUser** location is `$HOME/.local/share/powershell/Modules`.</span></span>

  > [!NOTE]
  > <span data-ttu-id="86041-211">您可以使用下列命令來確認 [ **檔** ] 資料夾的位置： `[Environment]::GetFolderPath('MyDocuments')` 。</span><span class="sxs-lookup"><span data-stu-id="86041-211">You can verify the location of your **Documents** folder using the following command: `[Environment]::GetFolderPath('MyDocuments')`.</span></span>

- <span data-ttu-id="86041-212">**AllUsers** 位置是 `$env:PROGRAMFILES\PowerShell\Modules` 在 Windows 上。</span><span class="sxs-lookup"><span data-stu-id="86041-212">The **AllUsers** location is `$env:PROGRAMFILES\PowerShell\Modules` on Windows.</span></span> <span data-ttu-id="86041-213">在 Linux 或 Mac 上，模組會儲存在中 `/usr/local/share/powershell/Modules` 。</span><span class="sxs-lookup"><span data-stu-id="86041-213">On Linux or Mac the modules are stored at `/usr/local/share/powershell/Modules`.</span></span>

> [!NOTE]
> <span data-ttu-id="86041-214">若要在目錄中新增或變更檔案 `$env:Windir\System32` ，請使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="86041-214">To add or change files in the `$env:Windir\System32` directory, start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="86041-215">您可以藉由變更 **PSModulePath** 環境變數的值，變更系統上的預設模組位置 `$Env:PSModulePath` 。</span><span class="sxs-lookup"><span data-stu-id="86041-215">You can change the default module locations on your system by changing the value of the **PSModulePath** environment variable, `$Env:PSModulePath`.</span></span> <span data-ttu-id="86041-216">**PSModulePath** 環境變數是以 Path 環境變數為模型，而且具有相同的格式。</span><span class="sxs-lookup"><span data-stu-id="86041-216">The **PSModulePath** environment variable is modeled on the Path environment variable and has the same format.</span></span>

<span data-ttu-id="86041-217">若要檢視預設模組位置，請輸入：</span><span class="sxs-lookup"><span data-stu-id="86041-217">To view the default module locations, type:</span></span>

```powershell
$Env:PSModulePath
```

<span data-ttu-id="86041-218">若要新增預設模組位置，請使用下列命令格式。</span><span class="sxs-lookup"><span data-stu-id="86041-218">To add a default module location, use the following command format.</span></span>

```powershell
$Env:PSModulePath = $Env:PSModulePath + ";<path>"
```

<span data-ttu-id="86041-219">命令中的分號 (`;`) 會將新路徑與清單中該路徑前面的路徑隔開。</span><span class="sxs-lookup"><span data-stu-id="86041-219">The semi-colon (`;`) in the command separates the new path from the path that precedes it in the list.</span></span>

<span data-ttu-id="86041-220">例如，若要新增 `C:\ps-test\Modules` 目錄，請輸入：</span><span class="sxs-lookup"><span data-stu-id="86041-220">For example, to add the `C:\ps-test\Modules` directory, type:</span></span>

```powershell
$Env:PSModulePath + ";C:\ps-test\Modules"
```

<span data-ttu-id="86041-221">若要在 Linux 或 MacOS 上新增預設模組位置，請使用下列命令格式：</span><span class="sxs-lookup"><span data-stu-id="86041-221">To add a default module location on Linux or MacOS, use the following command format:</span></span>

```powershell
$Env:PSModulePath += ":<path>"
```

<span data-ttu-id="86041-222">例如，若要將 `/usr/local/Fabrikam/Modules` 目錄新增至 **PSModulePath** 環境變數的值，請輸入：</span><span class="sxs-lookup"><span data-stu-id="86041-222">For example, to add the `/usr/local/Fabrikam/Modules` directory to the value of the **PSModulePath** environment variable, type:</span></span>

```powershell
$Env:PSModulePath += ":/usr/local/Fabrikam/Modules"
```

<span data-ttu-id="86041-223">在 Linux 或 MacOS 上，命令中的冒號 (`:`) 會將新路徑與清單中該路徑前面的路徑隔開。</span><span class="sxs-lookup"><span data-stu-id="86041-223">On Linux or MacOS, the colon (`:`) in the command separates the new path from the path that precedes it in the list.</span></span>

<span data-ttu-id="86041-224">當您新增 **PSModulePath** 的路徑時， `Get-Module` `Import-Module` 命令會包含該路徑中的模組。</span><span class="sxs-lookup"><span data-stu-id="86041-224">When you add a path to **PSModulePath**, `Get-Module` and `Import-Module` commands include modules in that path.</span></span>

<span data-ttu-id="86041-225">您所設定的值只會影響目前的工作階段。</span><span class="sxs-lookup"><span data-stu-id="86041-225">The value that you set affects only the current session.</span></span> <span data-ttu-id="86041-226">若要讓變更持續發生，請將命令新增至 PowerShell 設定檔，或使用主控台中的系統來變更登錄中 **PSModulePath** 環境變數的值。</span><span class="sxs-lookup"><span data-stu-id="86041-226">To make the change persistent, add the command to your PowerShell profile or use System in Control Panel to change the value of the **PSModulePath** environment variable in the registry.</span></span>

<span data-ttu-id="86041-227">此外，若要讓變更持續進行，您也可以使用 **System. 環境** 類別的 **SetEnvironmentVariable** 方法，將路徑加入至 **PSModulePath** 環境變數。</span><span class="sxs-lookup"><span data-stu-id="86041-227">Also, to make the change persistent, you can also use the **SetEnvironmentVariable** method of the **System.Environment** class to add a Path to the **PSModulePath** environment variable.</span></span>

<span data-ttu-id="86041-228">如需有關 **PSModulePath** 變數的詳細資訊，請參閱 [about_Environment_Variables](about_Environment_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="86041-228">For more information about the **PSModulePath** variable, see [about_Environment_Variables](about_Environment_Variables.md).</span></span>

## <a name="modules-and-name-conflicts"></a><span data-ttu-id="86041-229">模組和名稱衝突</span><span class="sxs-lookup"><span data-stu-id="86041-229">Modules and Name Conflicts</span></span>

<span data-ttu-id="86041-230">工作階段中的多個命令擁有相同名稱時，會發生名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="86041-230">Name conflicts occur when more than one command in the session has the same name.</span></span> <span data-ttu-id="86041-231">當模組中的命令與工作階段中的命令或項目擁有相同的名稱時，匯入模組會造成名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="86041-231">Importing a module causes a name conflict when commands in the module have the same names as commands or items in the session.</span></span>

<span data-ttu-id="86041-232">名稱衝突可能會導致隱藏或取代命令。</span><span class="sxs-lookup"><span data-stu-id="86041-232">Name conflicts can result in commands being hidden or replaced.</span></span>

### <a name="hidden"></a><span data-ttu-id="86041-233">Hidden</span><span class="sxs-lookup"><span data-stu-id="86041-233">Hidden</span></span>

<span data-ttu-id="86041-234">當某個命令不是您輸入命令名稱時執行的命令，但是您可以使用其他方法 (例如，使用起源自該命令之模組或嵌入式管理單元的名稱限定命令名稱) 執行它時，就會隱藏該命令。</span><span class="sxs-lookup"><span data-stu-id="86041-234">A command is hidden when it is not the command that runs when you type the command name, but you can run it by using another method, such as by qualifying the command name with the name of the module or snap-in in which it originated.</span></span>

### <a name="replaced"></a><span data-ttu-id="86041-235">已取代</span><span class="sxs-lookup"><span data-stu-id="86041-235">Replaced</span></span>

<span data-ttu-id="86041-236">當您因為具有相同名稱的命令覆寫某個命令而無法執行時，會取代該命令。</span><span class="sxs-lookup"><span data-stu-id="86041-236">A command is replaced when you cannot run it because it has been overwritten by a command with the same name.</span></span> <span data-ttu-id="86041-237">即使您移除造成衝突的模組，除非您重新啟動工作階段，否則還是無法執行遭到取代的命令。</span><span class="sxs-lookup"><span data-stu-id="86041-237">Even when you remove the module that caused the conflict, you cannot run a replaced command unless you restart the session.</span></span>

<span data-ttu-id="86041-238">`Import-Module` 可能會加入隱藏和取代目前會話中命令的命令。</span><span class="sxs-lookup"><span data-stu-id="86041-238">`Import-Module` might add commands that hide and replace commands in the current session.</span></span> <span data-ttu-id="86041-239">此外，您工作階段中的命令可以隱藏模組所加入的命令。</span><span class="sxs-lookup"><span data-stu-id="86041-239">Also, commands in your session can hide commands that the module added.</span></span>

<span data-ttu-id="86041-240">若要偵測名稱衝突，請使用 Cmdlet 的 **All** 參數 `Get-Command` 。</span><span class="sxs-lookup"><span data-stu-id="86041-240">To detect name conflicts, use the **All** parameter of the `Get-Command` cmdlet.</span></span> <span data-ttu-id="86041-241">從 PowerShell 3.0 開始， `Get-Command` 只會取得您輸入命令名稱時所執行的命令。</span><span class="sxs-lookup"><span data-stu-id="86041-241">Beginning in PowerShell 3.0, `Get-Command` gets only that commands that run when you type the command name.</span></span> <span data-ttu-id="86041-242">**All** 參數會取得會話中具有特定名稱的所有命令。</span><span class="sxs-lookup"><span data-stu-id="86041-242">The **All** parameter gets all commands with the specific name in the session.</span></span>

<span data-ttu-id="86041-243">若要避免名稱衝突，請使用 Cmdlet 的 **NoClobber** 或 **Prefix** 參數 `Import-Module` 。</span><span class="sxs-lookup"><span data-stu-id="86041-243">To prevent name conflicts, use the **NoClobber** or **Prefix** parameters of the `Import-Module` cmdlet.</span></span> <span data-ttu-id="86041-244">**Prefix** 參數會將前置詞加入至已匯入命令的名稱，使其在會話中是唯一的。</span><span class="sxs-lookup"><span data-stu-id="86041-244">The **Prefix** parameter adds a prefix to the names of imported commands so that they are unique in the session.</span></span> <span data-ttu-id="86041-245">**NoClobber** 參數不會匯入任何會隱藏或取代會話中現有命令的命令。</span><span class="sxs-lookup"><span data-stu-id="86041-245">The **NoClobber** parameter does not import any commands that would hide or replace existing commands in the session.</span></span>

<span data-ttu-id="86041-246">您也可以使用的 **Alias**、 **Cmdlet**、 **Function** 和 **Variable** 參數， `Import-Module` 只選取您要匯入的命令，而且您可以排除在您的會話中造成名稱衝突的命令。</span><span class="sxs-lookup"><span data-stu-id="86041-246">You can also use the **Alias**, **Cmdlet**, **Function**, and **Variable** parameters of `Import-Module` to select only the commands that you want to import, and you can exclude commands that cause name conflicts in your session.</span></span>

<span data-ttu-id="86041-247">模組作者可以使用模組資訊清單的 **DefaultCommandPrefix** 屬性，將預設前置詞加入至所有命令名稱，藉以防止名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="86041-247">Module authors can prevent name conflicts by using the **DefaultCommandPrefix** property of the module manifest to add a default prefix to all command names.</span></span>
<span data-ttu-id="86041-248">**Prefix** 參數的值會優先于 **DefaultCommandPrefix** 的值。</span><span class="sxs-lookup"><span data-stu-id="86041-248">The value of the **Prefix** parameter takes precedence over the value of **DefaultCommandPrefix**.</span></span>

<span data-ttu-id="86041-249">即使隱藏某個命令，您還是可以透過使用起源自該命令之模組或嵌入式管理單元的名稱限定命令名稱來執行。</span><span class="sxs-lookup"><span data-stu-id="86041-249">Even if a command is hidden, you can run it by qualifying the command name with the name of the module or snap-in in which it originated.</span></span>

<span data-ttu-id="86041-250">PowerShell 命令優先順序規則可決定會話包含具有相同名稱的命令時，所執行的命令。</span><span class="sxs-lookup"><span data-stu-id="86041-250">The PowerShell command precedence rules determine which command runs when the session includes commands with the same name.</span></span>

<span data-ttu-id="86041-251">例如，當會話包含具有相同名稱的函式和 Cmdlet 時，PowerShell 預設會執行函式。</span><span class="sxs-lookup"><span data-stu-id="86041-251">For example, when a session includes a function and a cmdlet with the same name, PowerShell runs the function by default.</span></span> <span data-ttu-id="86041-252">當工作階段預設包含具有相同名稱之相同類型的命令 (例如，具有相同名稱的兩個 Cmdlet) 時，它會執行最近加入的命令。</span><span class="sxs-lookup"><span data-stu-id="86041-252">When the session includes commands of the same type with the same name, such as two cmdlets with the same name, by default, it runs the most recently added command.</span></span>

<span data-ttu-id="86041-253">如需詳細資訊，包括優先順序規則的說明和執行隱藏命令的指示，請參閱 [about_Command_Precedence](about_Command_Precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="86041-253">For more information, including an explanation of the precedence rules and instructions for running hidden commands, see [about_Command_Precedence](about_Command_Precedence.md).</span></span>

## <a name="modules-and-snap-ins"></a><span data-ttu-id="86041-254">模組與嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="86041-254">Modules and Snap-ins</span></span>

<span data-ttu-id="86041-255">您可以從模組和嵌入式管理單元將命令新增至您的會話。模組可以加入所有類型的命令，包括 Cmdlet、提供者和函式，以及專案，例如變數、別名和 PowerShell 磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="86041-255">You can add commands to your session from modules and snap-ins. Modules can add all types of commands, including cmdlets, providers, and functions, and items, such as variables, aliases, and PowerShell drives.</span></span> <span data-ttu-id="86041-256">嵌入式管理單元只能加入 Cmdlet 和提供者。</span><span class="sxs-lookup"><span data-stu-id="86041-256">Snap-ins can add only cmdlets and providers.</span></span>

<span data-ttu-id="86041-257">從您的工作階段移除模組或嵌入式管理單元之前，請使用下列命令判斷將會移除哪些命令。</span><span class="sxs-lookup"><span data-stu-id="86041-257">Before removing a module or snap-in from your session, use the following commands to determine which commands will be removed.</span></span>

<span data-ttu-id="86041-258">若要在您的會話中尋找 Cmdlet 的來源，請使用下列命令格式：</span><span class="sxs-lookup"><span data-stu-id="86041-258">To find the source of a cmdlet in your session, use the following command format:</span></span>

```powershell
Get-Command <cmdlet-name> | Format-List -Property verb,noun,pssnapin,module
```

<span data-ttu-id="86041-259">例如，若要尋找 Cmdlet 的來源 `Get-Date` ，請輸入：</span><span class="sxs-lookup"><span data-stu-id="86041-259">For example, to find the source of the `Get-Date` cmdlet, type:</span></span>

```powershell
Get-Command Get-Date | Format-List -Property verb,noun,module
```

## <a name="module-related-warnings-and-errors"></a><span data-ttu-id="86041-260">模組相關警告和錯誤</span><span class="sxs-lookup"><span data-stu-id="86041-260">Module-related Warnings and Errors</span></span>

<span data-ttu-id="86041-261">模組所匯出的命令應遵循 PowerShell 命令命名規則。</span><span class="sxs-lookup"><span data-stu-id="86041-261">The commands that a module exports should follow the PowerShell command naming rules.</span></span> <span data-ttu-id="86041-262">如果您匯入的模組會匯出其名稱中具有未核准之動詞的 Cmdlet 或函式，則此 `Import-Module` Cmdlet 會顯示下列警告訊息。</span><span class="sxs-lookup"><span data-stu-id="86041-262">If the module that you import exports cmdlets or functions that have unapproved verbs in their names, the `Import-Module` cmdlet displays the following warning message.</span></span>

> <span data-ttu-id="86041-263">警告：某些匯入的命令名稱包含未核准的動詞命令，可能會讓它們更不容易探索。</span><span class="sxs-lookup"><span data-stu-id="86041-263">WARNING: Some imported command names include unapproved verbs which might make them less discoverable.</span></span> <span data-ttu-id="86041-264">請使用 Verbose 參數取得詳細資訊，或輸入 Get-Verb 查看核准的動詞清單。</span><span class="sxs-lookup"><span data-stu-id="86041-264">Use the Verbose parameter for more detail or type Get-Verb to see the list of approved verbs.</span></span>

<span data-ttu-id="86041-265">這則訊息只是一個警告。</span><span class="sxs-lookup"><span data-stu-id="86041-265">This message is only a warning.</span></span> <span data-ttu-id="86041-266">模組仍然完整匯入，包括不合格的命令。</span><span class="sxs-lookup"><span data-stu-id="86041-266">The complete module is still imported, including the non-conforming commands.</span></span> <span data-ttu-id="86041-267">雖然訊息是顯示給模組的使用者，但命名的問題應該由模組作者修正。</span><span class="sxs-lookup"><span data-stu-id="86041-267">Although the message is displayed to module users, the naming problem should be fixed by the module author.</span></span>

<span data-ttu-id="86041-268">若要隱藏警告訊息，請使用 Cmdlet 的 **DisableNameChecking** 參數 `Import-Module` 。</span><span class="sxs-lookup"><span data-stu-id="86041-268">To suppress the warning message, use the **DisableNameChecking** parameter of the `Import-Module` cmdlet.</span></span>

## <a name="built-in-modules-and-snap-ins"></a><span data-ttu-id="86041-269">內建模組和嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="86041-269">Built-in Modules and Snap-ins</span></span>

<span data-ttu-id="86041-270">在 powershell 2.0 和 PowerShell 3.0 和更新版本中舊版的主機程式中，隨 PowerShell 安裝的核心命令會封裝在自動加入至每個 PowerShell 會話的嵌入式管理單元中。</span><span class="sxs-lookup"><span data-stu-id="86041-270">In PowerShell 2.0 and in older-style host programs in PowerShell 3.0 and later, the core commands that are installed with PowerShell are packaged in snap-ins that are added automatically to every PowerShell session.</span></span>

<span data-ttu-id="86041-271">從 PowerShell 3.0 開始，針對執行 `InitialSessionState.CreateDefault2` 初始會話狀態 API 的主機程式，預設會將 Microsoft. 核心嵌入式管理單元加入至每個會話。</span><span class="sxs-lookup"><span data-stu-id="86041-271">Beginning in PowerShell 3.0, for host programs that implement the `InitialSessionState.CreateDefault2` initial session state API the Microsoft.PowerShell.Core snap-in is added to every session by default.</span></span> <span data-ttu-id="86041-272">第一次使用時，會自動載入模組。</span><span class="sxs-lookup"><span data-stu-id="86041-272">Modules are loaded automatically on first-use.</span></span>

> [!NOTE]
> <span data-ttu-id="86041-273">遠端會話（包括使用 Cmdlet 啟動的會話 `New-PSSession` ）是較舊的會話，其中內建命令會封裝在嵌入式管理單元中。</span><span class="sxs-lookup"><span data-stu-id="86041-273">Remote sessions, including sessions that are started by using the `New-PSSession` cmdlet, are older-style sessions in which the built-in commands are packaged in snap-ins.</span></span>

<span data-ttu-id="86041-274">下列模組 (或嵌入式管理單元) 與 PowerShell 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="86041-274">The following modules (or snap-ins) are installed with PowerShell.</span></span>

- <span data-ttu-id="86041-275">CimCmdlets</span><span class="sxs-lookup"><span data-stu-id="86041-275">CimCmdlets</span></span>
- <span data-ttu-id="86041-276">Microsoft.PowerShell.Archive</span><span class="sxs-lookup"><span data-stu-id="86041-276">Microsoft.PowerShell.Archive</span></span>
- <span data-ttu-id="86041-277">Microsoft.PowerShell.Core</span><span class="sxs-lookup"><span data-stu-id="86041-277">Microsoft.PowerShell.Core</span></span>
- <span data-ttu-id="86041-278">Microsoft.PowerShell.Diagnostics</span><span class="sxs-lookup"><span data-stu-id="86041-278">Microsoft.PowerShell.Diagnostics</span></span>
- <span data-ttu-id="86041-279">Microsoft.PowerShell.Host</span><span class="sxs-lookup"><span data-stu-id="86041-279">Microsoft.PowerShell.Host</span></span>
- <span data-ttu-id="86041-280">Microsoft.PowerShell.Management</span><span class="sxs-lookup"><span data-stu-id="86041-280">Microsoft.PowerShell.Management</span></span>
- <span data-ttu-id="86041-281">Microsoft.PowerShell.Security</span><span class="sxs-lookup"><span data-stu-id="86041-281">Microsoft.PowerShell.Security</span></span>
- <span data-ttu-id="86041-282">Microsoft.PowerShell.Utility</span><span class="sxs-lookup"><span data-stu-id="86041-282">Microsoft.PowerShell.Utility</span></span>
- <span data-ttu-id="86041-283">Microsoft.WSMan.Management</span><span class="sxs-lookup"><span data-stu-id="86041-283">Microsoft.WSMan.Management</span></span>
- <span data-ttu-id="86041-284">PackageManagement</span><span class="sxs-lookup"><span data-stu-id="86041-284">PackageManagement</span></span>
- <span data-ttu-id="86041-285">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="86041-285">PowerShellGet</span></span>
- <span data-ttu-id="86041-286">PSDesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="86041-286">PSDesiredStateConfiguration</span></span>
- <span data-ttu-id="86041-287">PSDiagnostics</span><span class="sxs-lookup"><span data-stu-id="86041-287">PSDiagnostics</span></span>
- <span data-ttu-id="86041-288">PSReadline</span><span class="sxs-lookup"><span data-stu-id="86041-288">PSReadline</span></span>

## <a name="logging-module-events"></a><span data-ttu-id="86041-289">記錄模組事件</span><span class="sxs-lookup"><span data-stu-id="86041-289">Logging Module Events</span></span>

<span data-ttu-id="86041-290">從 PowerShell 3.0 開始，您可以藉由將模組和嵌入式管理單元的 **LogPipelineExecutionDetails** 屬性設定為，來記錄 powershell 模組和嵌入式管理單元中的 Cmdlet 和函式的執行事件 `$True` 。</span><span class="sxs-lookup"><span data-stu-id="86041-290">Beginning in PowerShell 3.0, you can record execution events for the cmdlets and functions in PowerShell modules and snap-ins by setting the **LogPipelineExecutionDetails** property of modules and snap-ins to `$True`.</span></span>
<span data-ttu-id="86041-291">您也可以使用群組原則設定，開啟模組記錄，以在所有 PowerShell 會話中啟用模組記錄。</span><span class="sxs-lookup"><span data-stu-id="86041-291">You can also use a Group Policy setting, Turn on Module Logging, to enable module logging in all PowerShell sessions.</span></span> <span data-ttu-id="86041-292">如需詳細資訊，請參閱記錄和群組原則文章。</span><span class="sxs-lookup"><span data-stu-id="86041-292">For more information, see the logging and group policy articles.</span></span>

## <a name="see-also"></a><span data-ttu-id="86041-293">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86041-293">See Also</span></span>

[<span data-ttu-id="86041-294">about_Logging_Windows</span><span class="sxs-lookup"><span data-stu-id="86041-294">about_Logging_Windows</span></span>](about_Logging_Windows.md)

[<span data-ttu-id="86041-295">about_Logging_Non-Windows</span><span class="sxs-lookup"><span data-stu-id="86041-295">about_Logging_Non-Windows</span></span>](about_Logging_Non-Windows.md)

[<span data-ttu-id="86041-296">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="86041-296">about_Group_Policy_Settings</span></span>](about_Group_Policy_Settings.md)

[<span data-ttu-id="86041-297">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="86041-297">about_Command_Precedence</span></span>](about_Command_Precedence.md)

[<span data-ttu-id="86041-298">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="86041-298">about_Group_Policy_Settings</span></span>](about_Group_Policy_Settings.md)

[<span data-ttu-id="86041-299">Get-Command</span><span class="sxs-lookup"><span data-stu-id="86041-299">Get-Command</span></span>](xref:Microsoft.PowerShell.Core.Get-Command)

[<span data-ttu-id="86041-300">Get-Help</span><span class="sxs-lookup"><span data-stu-id="86041-300">Get-Help</span></span>](xref:Microsoft.PowerShell.Core.Get-Help)

[<span data-ttu-id="86041-301">Get-Module</span><span class="sxs-lookup"><span data-stu-id="86041-301">Get-Module</span></span>](xref:Microsoft.PowerShell.Core.Get-Module)

[<span data-ttu-id="86041-302">Import-Module</span><span class="sxs-lookup"><span data-stu-id="86041-302">Import-Module</span></span>](xref:Microsoft.PowerShell.Core.Import-Module)

[<span data-ttu-id="86041-303">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="86041-303">Remove-Module</span></span>](xref:Microsoft.PowerShell.Core.Remove-Module)
