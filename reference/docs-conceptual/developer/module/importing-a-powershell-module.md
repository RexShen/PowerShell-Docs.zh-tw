---
title: 匯入 PowerShell 模組 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 697791b3-2135-4a39-b9d7-8566ed67acf2
caps.latest.revision: 13
ms.openlocfilehash: bb5d036e5658c365a4fafa2cac05c0bba9f87019
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360697"
---
# <a name="importing-a-powershell-module"></a><span data-ttu-id="1be77-102">匯入 PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="1be77-102">Importing a PowerShell Module</span></span>

<span data-ttu-id="1be77-103">在系統上安裝模組之後，您可能會想要匯入模組。</span><span class="sxs-lookup"><span data-stu-id="1be77-103">Once your have installed a module on a system, you will likely want to import the module.</span></span> <span data-ttu-id="1be77-104">匯入是將模組載入使用中記憶體的程式，讓使用者可以在其 PowerShell 會話中存取該模組。</span><span class="sxs-lookup"><span data-stu-id="1be77-104">Importing is the process that loads the module into active memory, so that a user can access that module in their PowerShell session.</span></span> <span data-ttu-id="1be77-105">在 PowerShell 2.0 中，您可以使用[import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet 的呼叫匯入新安裝的 PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="1be77-105">In PowerShell 2.0, you can import a newly-installed PowerShell module with a call to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span> <span data-ttu-id="1be77-106">在 PowerShell 3.0 中，當使用者呼叫模組中的其中一個函式或 Cmdlet 時，PowerShell 可以隱含地匯入模組。</span><span class="sxs-lookup"><span data-stu-id="1be77-106">In PowerShell 3.0, PowerShell is able to implicitly import a module when one of the functions or cmdlets in the module is called by a user.</span></span> <span data-ttu-id="1be77-107">請注意，這兩個版本都假設您將模組安裝在 PowerShell 能夠找到它的位置;如需詳細資訊，請參閱[安裝 PowerShell 模組](./installing-a-powershell-module.md)。</span><span class="sxs-lookup"><span data-stu-id="1be77-107">Note that both versions assume that you install your module in a location where PowerShell is able to find it; for more information, see [Installing a PowerShell Module](./installing-a-powershell-module.md).</span></span> <span data-ttu-id="1be77-108">您可以使用模組資訊清單來限制要匯出模組的哪些部分，而且您可以使用 `Import-Module` 呼叫的參數來限制要匯入的元件。</span><span class="sxs-lookup"><span data-stu-id="1be77-108">You can use a module manifest to restrict what parts of your module are exported, and you can use parameters of the `Import-Module` call to restrict what parts are imported.</span></span>

## <a name="importing-a-snap-in-powershell-10"></a><span data-ttu-id="1be77-109">匯入嵌入式管理單元（PowerShell 1.0）</span><span class="sxs-lookup"><span data-stu-id="1be77-109">Importing a Snap-In (PowerShell 1.0)</span></span>

<span data-ttu-id="1be77-110">模組不存在於 PowerShell 1.0 中：相反地，您必須註冊並使用嵌入式管理單元。不過，我們不建議您在此時使用這項技術，因為模組通常較容易安裝和匯入。</span><span class="sxs-lookup"><span data-stu-id="1be77-110">Modules did not exist in PowerShell 1.0: instead, you had to register and use snap-ins. However, it is not recommended that you use this technology at this point, as modules are generally easier to install and import.</span></span> <span data-ttu-id="1be77-111">如需詳細資訊，請參閱[如何建立 Windows PowerShell 嵌入式管理單元](../cmdlet/how-to-create-a-windows-powershell-snap-in.md)。</span><span class="sxs-lookup"><span data-stu-id="1be77-111">For more information, see [How to Create a Windows PowerShell Snap-in](../cmdlet/how-to-create-a-windows-powershell-snap-in.md).</span></span>

## <a name="importing-a-module-with-import-module-powershell-20"></a><span data-ttu-id="1be77-112">使用 Import-module 匯入模組（PowerShell 2.0）</span><span class="sxs-lookup"><span data-stu-id="1be77-112">Importing a Module with Import-Module (PowerShell 2.0)</span></span>

<span data-ttu-id="1be77-113">PowerShell 2.0 使用適當命名的[import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet 來匯入模組。</span><span class="sxs-lookup"><span data-stu-id="1be77-113">PowerShell 2.0 uses the appropriately-named [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet to import modules.</span></span> <span data-ttu-id="1be77-114">執行此 Cmdlet 時，Windows PowerShell 會在 `PSModulePath` 變數中所指定的目錄內搜尋指定的模組。</span><span class="sxs-lookup"><span data-stu-id="1be77-114">When this cmdlet is run, Windows PowerShell searches for the specified module within the directories specified in the `PSModulePath` variable.</span></span> <span data-ttu-id="1be77-115">找到指定的目錄時，Windows PowerShell 會依下列順序搜尋檔案：模組資訊清單檔案（. .psd1）、腳本模組檔案（. .psm1）、二進位模組檔案（.dll）。</span><span class="sxs-lookup"><span data-stu-id="1be77-115">When the specified directory is found, Windows PowerShell searches for files in the following order: module manifest files (.psd1), script module files (.psm1), binary module files (.dll).</span></span> <span data-ttu-id="1be77-116">如需將目錄新增至搜尋的詳細資訊，請參閱[修改 PSModulePath 安裝路徑](./modifying-the-psmodulepath-installation-path.md)。</span><span class="sxs-lookup"><span data-stu-id="1be77-116">For more information about adding directories to the search, see [Modifying the PSModulePath Installation Path](./modifying-the-psmodulepath-installation-path.md).</span></span> <span data-ttu-id="1be77-117">下列程式碼說明如何匯入模組：</span><span class="sxs-lookup"><span data-stu-id="1be77-117">The following code describes how to import a module:</span></span>

```powershell
Import-Module myModule
```

<span data-ttu-id="1be77-118">假設 myModule 位於 `PSModulePath`，則 PowerShell 會將 myModule 載入至使用中的記憶體。</span><span class="sxs-lookup"><span data-stu-id="1be77-118">Assuming that myModule was located in the `PSModulePath`, PowerShell would load myModule into active memory.</span></span> <span data-ttu-id="1be77-119">如果 myModule 不在 `PSModulePath` 路徑上，您仍然可以明確告知 PowerShell 哪裡可以找到它：</span><span class="sxs-lookup"><span data-stu-id="1be77-119">If myModule was not located on a `PSModulePath` path, you could still explicitly tell PowerShell where to find it:</span></span>

```powershell
Import-Module -Name C:\myRandomDirectory\myModule -Verbose
```

<span data-ttu-id="1be77-120">您也可以使用-verbose 參數來識別要從模組匯出的內容，以及匯入到使用中記憶體的內容。</span><span class="sxs-lookup"><span data-stu-id="1be77-120">You can also use the -verbose parameter to identify what is being exported out of the module, and what is being imported into active memory.</span></span> <span data-ttu-id="1be77-121">匯出和匯入都會限制對使用者公開的內容：其差異在於控制可見度的物件。</span><span class="sxs-lookup"><span data-stu-id="1be77-121">Both exports and imports restrict what is exposed to the user: the difference is who is controlling the visibility.</span></span> <span data-ttu-id="1be77-122">基本上，匯出是由模組內的程式碼所控制。</span><span class="sxs-lookup"><span data-stu-id="1be77-122">Essentially, exports are controlled by code within the module.</span></span> <span data-ttu-id="1be77-123">相反地，匯入是由 `Import-Module` 呼叫所控制。</span><span class="sxs-lookup"><span data-stu-id="1be77-123">In contrast, imports are controlled by the `Import-Module` call.</span></span> <span data-ttu-id="1be77-124">如需詳細資訊，請參閱下方的**限制匯入的成員**。</span><span class="sxs-lookup"><span data-stu-id="1be77-124">For more information, see **Restricting Members That Are Imported**, below.</span></span>

## <a name="implicitly-importing-a-module-powershell-30"></a><span data-ttu-id="1be77-125">隱含匯入模組（PowerShell 3.0）</span><span class="sxs-lookup"><span data-stu-id="1be77-125">Implicitly Importing a Module (PowerShell 3.0)</span></span>

<span data-ttu-id="1be77-126">從 Windows PowerShell 3.0 開始，在命令中使用模組中的任何 Cmdlet 或函式時，就會自動匯入模組。</span><span class="sxs-lookup"><span data-stu-id="1be77-126">Beginning in Windows PowerShell 3.0, modules are imported automatically when any cmdlet or function in the module is used in a command.</span></span> <span data-ttu-id="1be77-127">這項功能適用于目錄中的任何模組，其包含在**PSModulePath**環境變數的值中。</span><span class="sxs-lookup"><span data-stu-id="1be77-127">This feature works on any module in a directory that this included in the value of the **PSModulePath** environment variable.</span></span> <span data-ttu-id="1be77-128">不過，如果您未將模組儲存在有效的路徑上，您仍然可以使用上述的明確匯[入模組](/powershell/module/Microsoft.PowerShell.Core/Import-Module)選項來載入它們。</span><span class="sxs-lookup"><span data-stu-id="1be77-128">If you do not save your module on a valid path however, you can still load them using the explicit [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) option, described above.</span></span>

<span data-ttu-id="1be77-129">下列動作會觸發自動匯入模組（也稱為「模組自動載入」）。</span><span class="sxs-lookup"><span data-stu-id="1be77-129">The following actions trigger automatic importing of a module, also known as "module auto-loading."</span></span>

- <span data-ttu-id="1be77-130">在命令中使用 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1be77-130">Using a cmdlet in a command.</span></span> <span data-ttu-id="1be77-131">例如，輸入 `Get-ExecutionPolicy` 會匯入包含 `Get-ExecutionPolicy` Cmdlet 的 Microsoft. PowerShell. Security 模組。</span><span class="sxs-lookup"><span data-stu-id="1be77-131">For example, typing `Get-ExecutionPolicy` imports the Microsoft.PowerShell.Security module that contains the `Get-ExecutionPolicy` cmdlet.</span></span>

- <span data-ttu-id="1be77-132">使用[get-command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) Cmdlet 來取得命令。</span><span class="sxs-lookup"><span data-stu-id="1be77-132">Using the [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet to get the command.</span></span>  <span data-ttu-id="1be77-133">例如，輸入 `Get-Command Get-JobTrigger` 會匯入包含 `Get-JobTrigger` Cmdlet 的**PSScheduledJob**模組。</span><span class="sxs-lookup"><span data-stu-id="1be77-133">For example, typing `Get-Command Get-JobTrigger` imports the **PSScheduledJob** module that contains the `Get-JobTrigger` cmdlet.</span></span> <span data-ttu-id="1be77-134">包含萬用字元的 `Get-Command` 命令會被視為探索，而且不會觸發模組的匯入。</span><span class="sxs-lookup"><span data-stu-id="1be77-134">A `Get-Command` command that includes wildcard characters is considered to be discovery and does not trigger importing of a module.</span></span>

- <span data-ttu-id="1be77-135">使用[get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) Cmdlet 取得 Cmdlet 的說明。</span><span class="sxs-lookup"><span data-stu-id="1be77-135">Using the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet to get help for a cmdlet.</span></span> <span data-ttu-id="1be77-136">例如，輸入 `Get-Help Get-WinEvent` 會匯入包含 `Get-WinEvent` Cmdlet 的 Microsoft. PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="1be77-136">For example, typing `Get-Help Get-WinEvent` imports the Microsoft.PowerShell.Diagnostics module that contains the `Get-WinEvent` cmdlet.</span></span>

<span data-ttu-id="1be77-137">為了支援自動匯入模組，`Get-Command` Cmdlet 會取得所有已安裝模組中的所有 Cmdlet 和函式，即使模組未匯入會話中也一樣。</span><span class="sxs-lookup"><span data-stu-id="1be77-137">To support automatic importing of modules, the `Get-Command` cmdlet gets all cmdlets and functions in all installed modules, even if the module is not imported into the session.</span></span> <span data-ttu-id="1be77-138">如需詳細資訊，請參閱[Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) Cmdlet 的說明主題。</span><span class="sxs-lookup"><span data-stu-id="1be77-138">For more information, see the help topic for the [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet.</span></span>

## <a name="the-importing-process"></a><span data-ttu-id="1be77-139">匯入程式</span><span class="sxs-lookup"><span data-stu-id="1be77-139">The Importing Process</span></span>

<span data-ttu-id="1be77-140">匯入模組時，系統會為模組建立新的會話狀態，並在記憶體中建立[PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo)物件。</span><span class="sxs-lookup"><span data-stu-id="1be77-140">When a module is imported, a new session state is created for the module, and a [System.Management.Automation.PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) object is created in memory.</span></span> <span data-ttu-id="1be77-141">已匯入的每個模組都會建立會話狀態（這包括根模組和任何嵌套模組）。</span><span class="sxs-lookup"><span data-stu-id="1be77-141">A session-state is created for each module that is imported (this includes the root module and any nested modules).</span></span> <span data-ttu-id="1be77-142">從根模組匯出的成員（包括任何由任何嵌套模組匯出到根模組的成員），接著會匯入至呼叫者的會話狀態。</span><span class="sxs-lookup"><span data-stu-id="1be77-142">The members that are exported from the root module, including any members that were exported to the root module by any nested modules, are then imported into the caller's session state.</span></span>

<span data-ttu-id="1be77-143">從模組匯出之成員的中繼資料具有 ModuleName 屬性。</span><span class="sxs-lookup"><span data-stu-id="1be77-143">The metadata of members that are exported from a module have a ModuleName property.</span></span> <span data-ttu-id="1be77-144">這個屬性會以匯出它們的模組名稱填入。</span><span class="sxs-lookup"><span data-stu-id="1be77-144">This property is populated with the name of the module that exported them.</span></span>

> [!WARNING]
> <span data-ttu-id="1be77-145">如果匯出成員的名稱使用未核准的動詞命令，或如果成員的名稱使用限制的字元，則會在執行[import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet 時顯示警告。</span><span class="sxs-lookup"><span data-stu-id="1be77-145">If the name of an exported member uses an unapproved verb or if the name of the member uses restricted characters, a warning is displayed when the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet is run.</span></span>

<span data-ttu-id="1be77-146">根據預設， [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet 不會將任何物件傳回至管線。</span><span class="sxs-lookup"><span data-stu-id="1be77-146">By default, the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet does not return any objects to the pipeline.</span></span> <span data-ttu-id="1be77-147">不過，此 Cmdlet 支援 `PassThru` 參數，可以用來針對每個匯入的模組傳回[PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo)物件。</span><span class="sxs-lookup"><span data-stu-id="1be77-147">However, the cmdlet supports a `PassThru` parameter that can be used to return a [System.Management.Automation.PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) object for each module that is imported.</span></span> <span data-ttu-id="1be77-148">若要將輸出傳送至主機，使用者應該執行「[寫入主機](/powershell/module/Microsoft.PowerShell.Utility/Write-Host)」 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1be77-148">To send output to the host, users should run the [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet.</span></span>

## <a name="restricting--the-members-that-are-imported"></a><span data-ttu-id="1be77-149">限制已匯入的成員</span><span class="sxs-lookup"><span data-stu-id="1be77-149">Restricting  the Members That Are Imported</span></span>

<span data-ttu-id="1be77-150">使用[import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet 匯入模組時，預設會將所有匯出的模組成員匯入到會話中，包括由嵌套模組匯出至模組的任何命令。</span><span class="sxs-lookup"><span data-stu-id="1be77-150">When a module is imported by using the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet, by default, all exported module members are imported into the session, including any commands exported to the module by a nested module.</span></span> <span data-ttu-id="1be77-151">預設不會匯出變數和別名。</span><span class="sxs-lookup"><span data-stu-id="1be77-151">By default, variables and aliases are not exported.</span></span> <span data-ttu-id="1be77-152">若要限制匯出的成員，請使用[模組資訊清單](./how-to-write-a-powershell-module-manifest.md)。</span><span class="sxs-lookup"><span data-stu-id="1be77-152">To restrict the members that are exported, use a [module manifest](./how-to-write-a-powershell-module-manifest.md).</span></span> <span data-ttu-id="1be77-153">若要限制匯入的成員，請使用 `Import-Module` Cmdlet 的下列參數。</span><span class="sxs-lookup"><span data-stu-id="1be77-153">To restrict the members that are imported, use the following parameters of the `Import-Module` cmdlet.</span></span>

- <span data-ttu-id="1be77-154">`Function`：此參數會限制匯出的函式。</span><span class="sxs-lookup"><span data-stu-id="1be77-154">`Function`: This parameter restricts the functions that are exported.</span></span> <span data-ttu-id="1be77-155">（如果您使用模組資訊清單，請參閱 FunctionsToExport 鍵）。</span><span class="sxs-lookup"><span data-stu-id="1be77-155">(If you are using a module manifest, see the FunctionsToExport key.)</span></span>

- <span data-ttu-id="1be77-156">`Cmdlet`：此參數會限制匯出的 Cmdlet （如果您使用模組資訊清單，請參閱 CmdletsToExport 鍵）。</span><span class="sxs-lookup"><span data-stu-id="1be77-156">`Cmdlet`: This parameter restricts the cmdlets that are exported (If you are using a module manifest, see the CmdletsToExport key.)</span></span>

- <span data-ttu-id="1be77-157">`Variable`：此參數會限制匯出的變數（如果您使用模組資訊清單，請參閱 VariablesToExport 鍵）。</span><span class="sxs-lookup"><span data-stu-id="1be77-157">`Variable`: This parameter restricts the variables that are exported (If you are using a module manifest, see the VariablesToExport key.)</span></span>

- <span data-ttu-id="1be77-158">`Alias`：此參數會限制匯出的別名（如果您使用模組資訊清單，請參閱 AliasesToExport 鍵）。</span><span class="sxs-lookup"><span data-stu-id="1be77-158">`Alias`: This parameter restricts the aliases that are exported (If you are using a module manifest, see the AliasesToExport key.)</span></span>

## <a name="see-also"></a><span data-ttu-id="1be77-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1be77-159">See Also</span></span>

[<span data-ttu-id="1be77-160">撰寫 Windows PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="1be77-160">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)