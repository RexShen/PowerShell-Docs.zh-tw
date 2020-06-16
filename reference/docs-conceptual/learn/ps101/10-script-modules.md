---
title: 指令碼模組
description: 指令碼模組是將指令碼和函式封裝成可重複使用工具的簡單方法。
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 661ba725764e1f31df628f6c5f2d58d760656e37
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438279"
---
# <a name="chapter-10---script-modules"></a><span data-ttu-id="4b0de-103">第 10 章 - 指令碼模組</span><span class="sxs-lookup"><span data-stu-id="4b0de-103">Chapter 10 - Script modules</span></span>

<span data-ttu-id="4b0de-104">如果是您要經常執行的動作，將 PowerShell 中的一行程式碼和指令碼轉換成可重複使用的工具，即變得更為重要。</span><span class="sxs-lookup"><span data-stu-id="4b0de-104">Turning your one-liners and scripts in PowerShell into reusable tools becomes even more important if it's something that you're going to use frequently.</span></span> <span data-ttu-id="4b0de-105">將您的函式封裝在指令碼模組中，讓它們看起來更專業，並使其更容易共用。</span><span class="sxs-lookup"><span data-stu-id="4b0de-105">Packaging your functions in a script module makes them look and feel more professional and makes them easier to share.</span></span>

## <a name="dot-sourcing-functions"></a><span data-ttu-id="4b0de-106">點執行函式</span><span class="sxs-lookup"><span data-stu-id="4b0de-106">Dot-Sourcing Functions</span></span>

<span data-ttu-id="4b0de-107">在上一章中，我們未討論的項目是點執行函式。</span><span class="sxs-lookup"><span data-stu-id="4b0de-107">Something that we didn't talk about in the previous chapter is dot-sourcing functions.</span></span> <span data-ttu-id="4b0de-108">當指令碼中的函式不是模組的一部分時，將它載入記憶體的唯一方法就是對儲存在所在的 `.PS1` 檔案進行點執行。</span><span class="sxs-lookup"><span data-stu-id="4b0de-108">When a function in a script isn't part of a module, the only way to load it into memory is to dot-source the `.PS1` file that it's saved in.</span></span>

<span data-ttu-id="4b0de-109">下列函式已儲存為 `Get-MrPSVersion.ps1`。</span><span class="sxs-lookup"><span data-stu-id="4b0de-109">The following function has been saved as `Get-MrPSVersion.ps1`.</span></span>

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}
```

<span data-ttu-id="4b0de-110">執行指令碼時，沒有發生任何動作。</span><span class="sxs-lookup"><span data-stu-id="4b0de-110">When you run the script, nothing happens.</span></span>

```powershell
.\Get-MrPSVersion.ps1
```

<span data-ttu-id="4b0de-111">如果您嘗試呼叫函式，其會產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="4b0de-111">If you try to call the function, it generates an error message.</span></span>

```powershell
Get-MrPSVersion
```

```Output
Get-MrPSVersion : The term 'Get-MrPSVersion' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or if a path
was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-MrPSVersion
    + CategoryInfo          : ObjectNotFound: (Get-MrPSVersion:String) [], CommandNotFou
   ndException
    + FullyQualifiedErrorId : CommandNotFoundException

```

<span data-ttu-id="4b0de-112">您可以藉由檢查函式是否存在於 **Function** PSDrive，判斷是否已將函式載入記憶體。</span><span class="sxs-lookup"><span data-stu-id="4b0de-112">You can determine if functions are loaded into memory by checking to see if they exist on the **Function** PSDrive.</span></span>

```powershell
Get-ChildItem -Path Function:\Get-MrPSVersion
```

```Output
Get-ChildItem : Cannot find path 'Get-MrPSVersion' because it does not exist.
At line:1 char:1
+ Get-ChildItem -Path Function:\Get-MrPSVersion
    + CategoryInfo          : ObjectNotFound: (Get-MrPSVersion:String) [Get-ChildItem],
   ItemNotFoundException
    + FullyQualifiedErrorId : PathNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
```

<span data-ttu-id="4b0de-113">呼叫包含函式之指令碼的問題是，函式會在 _Script_ 範圍中載入。</span><span class="sxs-lookup"><span data-stu-id="4b0de-113">The problem with calling the script that contains the function is that the functions are loaded in the _Script_ scope.</span></span> <span data-ttu-id="4b0de-114">當指令碼完成時，就會移除該範圍，並隨著它移除函式。</span><span class="sxs-lookup"><span data-stu-id="4b0de-114">When the script completes, that scope is removed and the function is removed with it.</span></span>

<span data-ttu-id="4b0de-115">必須將函式載入 _Global_ 範圍。</span><span class="sxs-lookup"><span data-stu-id="4b0de-115">The function needs to be loaded into the _Global_ scope.</span></span> <span data-ttu-id="4b0de-116">這可以透過對包含函式的指令碼進行點執行來完成。</span><span class="sxs-lookup"><span data-stu-id="4b0de-116">That can be accomplished by dot-sourcing the script that contains the function.</span></span> <span data-ttu-id="4b0de-117">可以使用相對路徑。</span><span class="sxs-lookup"><span data-stu-id="4b0de-117">The relative path can be used.</span></span>

```powershell
. .\Get-MrPSVersion.ps1
```

<span data-ttu-id="4b0de-118">也可以使用完整路徑。</span><span class="sxs-lookup"><span data-stu-id="4b0de-118">The fully qualified path can also be used.</span></span>

```powershell
. C:\Demo\Get-MrPSVersion.ps1
```

<span data-ttu-id="4b0de-119">如果路徑的某部分儲存在變數中，則可以與路徑的其餘部分結合。</span><span class="sxs-lookup"><span data-stu-id="4b0de-119">If a portion of the path is stored in a variable, it can be combined with the remainder of the path.</span></span>
<span data-ttu-id="4b0de-120">不需要使用字串串連，將變數與路徑的其餘部分結合在一起。</span><span class="sxs-lookup"><span data-stu-id="4b0de-120">There's no reason to use string concatenation to combine the variable together with the remainder of the path.</span></span>

```powershell
$Path = 'C:\'
. $Path\Get-MrPSVersion.ps1
```

<span data-ttu-id="4b0de-121">現在當我檢查 **Function** PSDrive 時，`Get-MrPSVersion` 函式會存在。</span><span class="sxs-lookup"><span data-stu-id="4b0de-121">Now when I check the **Function** PSDrive, the `Get-MrPSVersion` function exists.</span></span>

```powershell
Get-ChildItem -Path Function:\Get-MrPSVersion
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-MrPSVersion
```

## <a name="script-modules"></a><span data-ttu-id="4b0de-122">指令碼模組</span><span class="sxs-lookup"><span data-stu-id="4b0de-122">Script Modules</span></span>

<span data-ttu-id="4b0de-123">PowerShell 中的指令碼模組只是一個檔案，其中包含一或多個儲存為 `.PSM1` 檔案而不是 `.PS1` 檔案的函式。</span><span class="sxs-lookup"><span data-stu-id="4b0de-123">A script module in PowerShell is simply a file containing one or more functions that's saved as a `.PSM1` file instead of a `.PS1` file.</span></span>

<span data-ttu-id="4b0de-124">如何建立指令碼模組？</span><span class="sxs-lookup"><span data-stu-id="4b0de-124">How do you create a script module?</span></span> <span data-ttu-id="4b0de-125">您可能會猜測使用名為 `New-Module` 之類的命令。</span><span class="sxs-lookup"><span data-stu-id="4b0de-125">You're probably guessing with a command named something like `New-Module`.</span></span> <span data-ttu-id="4b0de-126">您的假設會是錯誤的。</span><span class="sxs-lookup"><span data-stu-id="4b0de-126">Your assumption would be wrong.</span></span> <span data-ttu-id="4b0de-127">雖然 PowerShell 中有一個名為 `New-Module` 的命令，該命令會建立動態模組，而不是指令碼模組。</span><span class="sxs-lookup"><span data-stu-id="4b0de-127">While there is a command in PowerShell named `New-Module`, that command creates a dynamic module, not a script module.</span></span> <span data-ttu-id="4b0de-128">請務必閱讀命令的說明，即使您認為已找到所需的命令也是如此。</span><span class="sxs-lookup"><span data-stu-id="4b0de-128">Always be sure to read the help for a command even when you think you've found the command you need.</span></span>

```powershell
help New-Module
```

```Output
NAME
    New-Module

SYNOPSIS
    Creates a new dynamic module that exists only in memory.

SYNTAX
    New-Module [-Name] <String> [-ScriptBlock] <ScriptBlock> [-ArgumentList <Object[]>]
    [-AsCustomObject] [-Cmdlet <String[]>] [-Function <String[]>] [-ReturnResult]
    [<CommonParameters>]

DESCRIPTION
    The New-Module cmdlet creates a dynamic module from a script block. The members of
    the dynamic module, such as functions and variables, are immediately available in
    the session and remain available until you close the session.

    Like static modules, by default, the cmdlets and functions in a dynamic module are
    exported and the variables and aliases are not. However, you can use the
    Export-ModuleMember cmdlet and the parameters of New-Module to override the defaults.

    You can also use the AsCustomObject parameter of New-Module to return the dynamic
    module as a custom object. The members of the modules, such as functions, are
    implemented as script methods of the custom object instead of being imported into
    the session.

    Dynamic modules exist only in memory, not on disk. Like all modules, the members of
    dynamic modules run in a private module scope that is a child of the global scope.
    Get-Module cannot get a dynamic module, but Get-Command can get the exported members.

    To make a dynamic module available to Get-Module , pipe a New-Module command to
    Import-Module, or pipe the module object that New-Module returns to Import-Module .
    This action adds the dynamic module to the Get-Module list, but it does not save the
    module to disk or make it persistent.

RELATED LINKS
    Online Version: http://go.microsoft.com/fwlink/?LinkId=821495
    Export-ModuleMember
    Get-Module
    Import-Module
    Remove-Module

REMARKS
    To see the examples, type: "get-help New-Module -examples".
    For more information, type: "get-help New-Module -detailed".
    For technical information, type: "get-help New-Module -full".
    For online help, type: "get-help New-Module -online"
```

<span data-ttu-id="4b0de-129">在上一章中，我提到函式應該使用已核准的動詞，否則會在匯入模組時產生警告訊息。</span><span class="sxs-lookup"><span data-stu-id="4b0de-129">In the previous chapter, I mentioned that functions should use approved verbs otherwise they'll generate a warning message when the module is imported.</span></span> <span data-ttu-id="4b0de-130">下列程式碼會使用 `New-Module` Cmdlet，在記憶體中建立動態模組。</span><span class="sxs-lookup"><span data-stu-id="4b0de-130">The following code uses the `New-Module` cmdlet to create a dynamic module in memory.</span></span> <span data-ttu-id="4b0de-131">此課程模組示範未核准的動詞警告。</span><span class="sxs-lookup"><span data-stu-id="4b0de-131">This module demonstrates the unapproved verb warning.</span></span>

```powershell
New-Module -Name MyModule -ScriptBlock {

    function Return-MrOsVersion {
        Get-CimInstance -ClassName Win32_OperatingSystem |
        Select-Object -Property @{label='OperatingSystem';expression={$_.Caption}}
    }

    Export-ModuleMember -Function Return-MrOsVersion

} | Import-Module
```

```Output
WARNING: The names of some imported commands from the module 'MyModule' include
unapproved verbs that might make them less discoverable. To find the commands with
unapproved verbs, run the Import-Module command again with the Verbose parameter. For a
list of approved verbs, type Get-Verb.
```

<span data-ttu-id="4b0de-132">只是要重申，雖然先前的範例中使用了 `New-Module` Cmdlet，但這並不是用來在 PowerShell 中建立指令碼模組的命令。</span><span class="sxs-lookup"><span data-stu-id="4b0de-132">Just to reiterate, although the `New-Module` cmdlet was used in the previous example, that's not the command for creating script modules in PowerShell.</span></span>

<span data-ttu-id="4b0de-133">將下列兩個函式儲存在名為 `MyScriptModule.psm1` 的檔案中。</span><span class="sxs-lookup"><span data-stu-id="4b0de-133">Save the following two functions in a file named `MyScriptModule.psm1`.</span></span>

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}

function Get-MrComputerName {
    $env:COMPUTERNAME
}
```

<span data-ttu-id="4b0de-134">嘗試呼叫其中一個函式。</span><span class="sxs-lookup"><span data-stu-id="4b0de-134">Try to call one of the functions.</span></span>

```powershell
Get-MrComputerName
```

```Output
Get-MrComputerName : The term 'Get-MrComputerName' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-MrComputerName
    + CategoryInfo          : ObjectNotFound: (Get-MrComputerName:String) [], CommandNot
   FoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

<span data-ttu-id="4b0de-135">系統會產生錯誤訊息，指出找不到函式。</span><span class="sxs-lookup"><span data-stu-id="4b0de-135">An error message is generated saying the function can't be found.</span></span> <span data-ttu-id="4b0de-136">您也可以像之前一樣檢查 **Function** PSDrive，而您也會發現也它不存在於其中。</span><span class="sxs-lookup"><span data-stu-id="4b0de-136">You could also check the **Function** PSDrive just like before and you'll find that it doesn't exist there either.</span></span>

<span data-ttu-id="4b0de-137">您可以使用 `Import-Module` Cmdlet 手動匯入檔案。</span><span class="sxs-lookup"><span data-stu-id="4b0de-137">You could manually import the file with the `Import-Module` cmdlet.</span></span>

```powershell
Import-Module C:\MyScriptModule.psm1
```

<span data-ttu-id="4b0de-138">模組自動載入功能是在 PowerShell 版本 3 中推出。</span><span class="sxs-lookup"><span data-stu-id="4b0de-138">The module autoloading feature was introduced in PowerShell version 3.</span></span> <span data-ttu-id="4b0de-139">若要利用模組自動載入，必須將指令碼模組儲存在與 `.PSM1` 檔案具有相同基礎名稱的資料夾，以及在 `$env:PSModulePath` 中指定的位置。</span><span class="sxs-lookup"><span data-stu-id="4b0de-139">To take advantage of module autoloading, a script module needs to be saved in a folder with the same base name as the `.PSM1` file and in a location specified in `$env:PSModulePath`.</span></span>

```powershell
$env:PSModulePath
```

```Output
C:\Users\mike-ladm\Documents\WindowsPowerShell\Modules;C:\Program Files\WindowsPowerShell\
Modules;C:\Windows\system32\WindowsPowerShell\v1.0\Modules;C:\Program Files (x86)\Microsof
t SQL Server\130\Tools\PowerShell\Modules\
```

<span data-ttu-id="4b0de-140">結果難以閱讀。</span><span class="sxs-lookup"><span data-stu-id="4b0de-140">The results are difficult to read.</span></span> <span data-ttu-id="4b0de-141">由於路徑是以分號分隔，因此您可以分割結果，以在個別行上傳回每個路徑。</span><span class="sxs-lookup"><span data-stu-id="4b0de-141">Since the paths are separated by a semicolon, you can split the results to return each path on a separate line.</span></span> <span data-ttu-id="4b0de-142">這會讓它們更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="4b0de-142">This makes them easier to read.</span></span>

```powershell
$env:PSModulePath -split ';'
```

```Output
C:\Users\mike-ladm\Documents\WindowsPowerShell\Modules
C:\Program Files\WindowsPowerShell\Modules
C:\Windows\system32\WindowsPowerShell\v1.0\Modules
C:\Program Files (x86)\Microsoft SQL Server\130\Tools\PowerShell\Modules\
```

<span data-ttu-id="4b0de-143">清單中的前三個路徑是預設值。</span><span class="sxs-lookup"><span data-stu-id="4b0de-143">The first three paths in the list are the default.</span></span> <span data-ttu-id="4b0de-144">安裝 SQL Server Management Studio 時，會新增最後一個路徑。</span><span class="sxs-lookup"><span data-stu-id="4b0de-144">When SQL Server Management Studio was installed, it added the last path.</span></span> <span data-ttu-id="4b0de-145">若要讓模組自動載入正常執行，`MyScriptModule.psm1` 檔案必須位於其中一個路徑內名為 `MyScriptModule` 的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="4b0de-145">For module autoloading to work, the `MyScriptModule.psm1` file needs to be located in a folder named `MyScriptModule` directly inside one of those paths.</span></span>

<span data-ttu-id="4b0de-146">慢著。</span><span class="sxs-lookup"><span data-stu-id="4b0de-146">Not so fast.</span></span> <span data-ttu-id="4b0de-147">就我的情況，我目前的使用者路徑不是清單中的第一個。</span><span class="sxs-lookup"><span data-stu-id="4b0de-147">For me, my current user path isn't the first one in the list.</span></span> <span data-ttu-id="4b0de-148">我幾乎從不會使用該路徑，因為我用來登入 Windows 的使用者與用來執行 PowerShell 的使用者不同。</span><span class="sxs-lookup"><span data-stu-id="4b0de-148">I almost never use that path since I log into Windows with a different user than the one I use to run PowerShell.</span></span> <span data-ttu-id="4b0de-149">這表示它不在一般的 [我的文件] 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="4b0de-149">That means it's not located in my normal Documents folder.</span></span>

<span data-ttu-id="4b0de-150">第二個路徑是 **AllUsers** 路徑。</span><span class="sxs-lookup"><span data-stu-id="4b0de-150">The second path is the **AllUsers** path.</span></span> <span data-ttu-id="4b0de-151">這是我用來儲存所有模組的位置。</span><span class="sxs-lookup"><span data-stu-id="4b0de-151">This is the location where I store all of my modules.</span></span>

<span data-ttu-id="4b0de-152">第三個路徑在 `C:\Windows\System32` 之下。</span><span class="sxs-lookup"><span data-stu-id="4b0de-152">The third path is underneath `C:\Windows\System32`.</span></span> <span data-ttu-id="4b0de-153">只有 Microsoft 應該將模組儲存在該位置，因為它位於作業系統資料夾內。</span><span class="sxs-lookup"><span data-stu-id="4b0de-153">Only Microsoft should be storing modules in that location since it resides within the operating systems folder.</span></span>

<span data-ttu-id="4b0de-154">一旦 `.PSM1` 檔案位於正確的路徑中，則在呼叫其中一個命令時，模組就會自動載入。</span><span class="sxs-lookup"><span data-stu-id="4b0de-154">Once the `.PSM1` file is located in the correct path, the module will load automatically when one of its commands is called.</span></span>

## <a name="module-manifests"></a><span data-ttu-id="4b0de-155">模組資訊清單</span><span class="sxs-lookup"><span data-stu-id="4b0de-155">Module Manifests</span></span>

<span data-ttu-id="4b0de-156">所有模組都應該有模組資訊清單。</span><span class="sxs-lookup"><span data-stu-id="4b0de-156">All modules should have a module manifest.</span></span> <span data-ttu-id="4b0de-157">模組資訊清單包含關於模組的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="4b0de-157">A module manifest contains metadata about your module.</span></span>
<span data-ttu-id="4b0de-158">模組資訊清單檔案的副檔名為 `.PSD1`。</span><span class="sxs-lookup"><span data-stu-id="4b0de-158">The file extension for a module manifest file is `.PSD1`.</span></span> <span data-ttu-id="4b0de-159">並非具有 `.PSD1` 副檔名的所有檔案都是模組資訊清單。</span><span class="sxs-lookup"><span data-stu-id="4b0de-159">Not all files with a `.PSD1` extension are module manifests.</span></span> <span data-ttu-id="4b0de-160">它們也可以用於儲存 DSC 設定的環境部分等項目。</span><span class="sxs-lookup"><span data-stu-id="4b0de-160">They can also be used for things such as storing the environmental portion of a DSC configuration.</span></span> <span data-ttu-id="4b0de-161">`New-ModuleManifest` 用來建立模組資訊清單。</span><span class="sxs-lookup"><span data-stu-id="4b0de-161">`New-ModuleManifest` is used to create a module manifest.</span></span> <span data-ttu-id="4b0de-162">**Path** 是唯一需要的值。</span><span class="sxs-lookup"><span data-stu-id="4b0de-162">**Path** is the only value that's required.</span></span> <span data-ttu-id="4b0de-163">不過，如果未指定 **RootModule**，模組將無法正常執行。</span><span class="sxs-lookup"><span data-stu-id="4b0de-163">However, the module won't work if **RootModule** isn't specified.</span></span> <span data-ttu-id="4b0de-164">如果您決定使用 PowerShellGet 將模組上傳至 NuGet 存放庫，則最好指定 **Author** 和 **Description**，因為在該案例中，這些值是必要的。</span><span class="sxs-lookup"><span data-stu-id="4b0de-164">It's a good idea to specify **Author** and **Description** in case you decide to upload your module to a NuGet repository with PowerShellGet since those values are required in that scenario.</span></span>

<span data-ttu-id="4b0de-165">沒有資訊清單的模組版本為 0.0。</span><span class="sxs-lookup"><span data-stu-id="4b0de-165">The version of a module without a manifest is 0.0.</span></span> <span data-ttu-id="4b0de-166">模組沒有資訊清單這點實在很明顯。</span><span class="sxs-lookup"><span data-stu-id="4b0de-166">This is a dead giveaway that the module doesn't have a manifest.</span></span>

```powershell
Get-Module -Name MyScriptModule
```

```Output
ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Script     0.0        myscriptmodule                      {Get-MrComputerName, Get-MrP...
```

<span data-ttu-id="4b0de-167">您可以使用所有建議的資訊來建立模組資訊清單。</span><span class="sxs-lookup"><span data-stu-id="4b0de-167">The module manifest can be created with all of the recommended information.</span></span>

```powershell
New-ModuleManifest -Path $env:ProgramFiles\WindowsPowerShell\Modules\MyScriptModule\MyScriptModule.psd1 -RootModule MyScriptModule -Author 'Mike F Robbins' -Description 'MyScriptModule' -CompanyName 'mikefrobbins.com'
```

<span data-ttu-id="4b0de-168">如果在模組資訊清單初始建立期間遺漏了任何這項資訊，則可以稍後使用 `Update-ModuleManifest` 來新增或更新。</span><span class="sxs-lookup"><span data-stu-id="4b0de-168">If any of this information is missed during the initial creation of the module manifest, it can be added or updated later using `Update-ModuleManifest`.</span></span> <span data-ttu-id="4b0de-169">資訊清單建立之後，請勿使用 `New-ModuleManifest` 重新建立資訊清單，因為 GUID 會變更。</span><span class="sxs-lookup"><span data-stu-id="4b0de-169">Don't recreate the manifest using `New-ModuleManifest` once it's already created because the GUID will change.</span></span>

## <a name="defining-public-and-private-functions"></a><span data-ttu-id="4b0de-170">定義公用和私人函式</span><span class="sxs-lookup"><span data-stu-id="4b0de-170">Defining Public and Private Functions</span></span>

<span data-ttu-id="4b0de-171">您可能會有想要設為私人的協助程式函式，而且只能由模組內的其他函式存取。</span><span class="sxs-lookup"><span data-stu-id="4b0de-171">You may have helper functions that you may want to be private and only accessible by other functions within the module.</span></span> <span data-ttu-id="4b0de-172">它們無法供您模組的使用者存取。</span><span class="sxs-lookup"><span data-stu-id="4b0de-172">They are not intended to be accessible to users of your module.</span></span> <span data-ttu-id="4b0de-173">有幾個不同方式可以完成此操作。</span><span class="sxs-lookup"><span data-stu-id="4b0de-173">There are a couple of different ways to accomplish this.</span></span>

<span data-ttu-id="4b0de-174">如果您未遵循最佳做法，而且只有一個 `.PSM1` 檔案，則您唯一的選項是使用 `Export-ModuleMember` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4b0de-174">If you're not following the best practices and only have a `.PSM1` file, then your only option is to use the `Export-ModuleMember` cmdlet.</span></span>

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}

function Get-MrComputerName {
    $env:COMPUTERNAME
}

Export-ModuleMember -Function Get-MrPSVersion
```

<span data-ttu-id="4b0de-175">在上述範例中，只有 `Get-MrPSVersion` 函式可供您模組的使用者使用，但 `Get-MrComputerName` 函式可供模組本身內的其他函式使用。</span><span class="sxs-lookup"><span data-stu-id="4b0de-175">In the previous example, only the `Get-MrPSVersion` function is available to the users of your module, but the `Get-MrComputerName` function is available to other functions within the module itself.</span></span>

```powershell
Get-Command -Module MyScriptModule

CommandType     Name                        Version    Source
-----------     ----                        -------    ------
Function        Get-MrPSVersion             1.0        MyScript...
```

<span data-ttu-id="4b0de-176">如果您已將模組資訊清單新增至模組 (而且您應該這麼做)，則建議您在模組資訊清單的 **FunctionsToExport** 區段中，指定您想要匯出的個別函式。</span><span class="sxs-lookup"><span data-stu-id="4b0de-176">If you've added a module manifest to your module (and you should), then I recommend specifying the individual functions you want to export in the **FunctionsToExport** section of the module manifest.</span></span>

```powershell
FunctionsToExport = 'Get-MrPSVersion'
```

<span data-ttu-id="4b0de-177">不需要在 `.PSM1` 檔案和模組資訊清單的 **FunctionsToExport** 區段中同時使用 `Export-ModuleMember`。</span><span class="sxs-lookup"><span data-stu-id="4b0de-177">It's not necessary to use both `Export-ModuleMember` in the `.PSM1` file and the **FunctionsToExport** section of the module manifest.</span></span> <span data-ttu-id="4b0de-178">在其中一個中使用已足夠。</span><span class="sxs-lookup"><span data-stu-id="4b0de-178">One or the other is sufficient.</span></span>

## <a name="summary"></a><span data-ttu-id="4b0de-179">摘要</span><span class="sxs-lookup"><span data-stu-id="4b0de-179">Summary</span></span>

<span data-ttu-id="4b0de-180">在本章中，您已了解如何在 PowerShell 中將您的函式轉換成指令碼模組。</span><span class="sxs-lookup"><span data-stu-id="4b0de-180">In this chapter you've learned how to turn your functions into a script module in PowerShell.</span></span> <span data-ttu-id="4b0de-181">您也已了解一些建立指令碼模組的最佳做法，例如，建立指令碼模組的模組資訊清單。</span><span class="sxs-lookup"><span data-stu-id="4b0de-181">You've also leaned some of the best practices for creating script modules such as creating a module manifest for your script module.</span></span>

## <a name="review"></a><span data-ttu-id="4b0de-182">檢閱</span><span class="sxs-lookup"><span data-stu-id="4b0de-182">Review</span></span>

1. <span data-ttu-id="4b0de-183">如何在 PowerShell 中建立指令碼模組？</span><span class="sxs-lookup"><span data-stu-id="4b0de-183">How do you create a script module in PowerShell?</span></span>
1. <span data-ttu-id="4b0de-184">為何您的函式務必需要使用已核准的動詞？</span><span class="sxs-lookup"><span data-stu-id="4b0de-184">Why is it important for your functions to use an approved verb?</span></span>
1. <span data-ttu-id="4b0de-185">如何在 PowerShell 中建立模組資訊清單？</span><span class="sxs-lookup"><span data-stu-id="4b0de-185">How do you create a module manifest in PowerShell?</span></span>
1. <span data-ttu-id="4b0de-186">用於從您的模組匯出僅特定函式的兩個選項為何？</span><span class="sxs-lookup"><span data-stu-id="4b0de-186">What are the two options for exporting only certain functions from your module?</span></span>
1. <span data-ttu-id="4b0de-187">呼叫命令時，模組需要哪些項目才能自動載入？</span><span class="sxs-lookup"><span data-stu-id="4b0de-187">What is required for your modules to load automatically when a command is called?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="4b0de-188">建議閱讀資料</span><span class="sxs-lookup"><span data-stu-id="4b0de-188">Recommended Reading</span></span>

- <span data-ttu-id="4b0de-189">[如何建立 PowerShell 指令碼模組和模組資訊清單][]</span><span class="sxs-lookup"><span data-stu-id="4b0de-189">[How to Create PowerShell Script Modules and Module Manifests][]</span></span>
- <span data-ttu-id="4b0de-190">[about_Modules][]</span><span class="sxs-lookup"><span data-stu-id="4b0de-190">[about_Modules][]</span></span>
- <span data-ttu-id="4b0de-191">[New-ModuleManifest][]</span><span class="sxs-lookup"><span data-stu-id="4b0de-191">[New-ModuleManifest][]</span></span>
- <span data-ttu-id="4b0de-192">[Export-ModuleMember][]</span><span class="sxs-lookup"><span data-stu-id="4b0de-192">[Export-ModuleMember][]</span></span>

<!-- link references -->
[如何建立 PowerShell 指令碼模組和模組資訊清單]: https://mikefrobbins.com/2013/07/04/how-to-create-powershell-script-modules-and-module-manifests/
[How to Create PowerShell Script Modules and Module Manifests]: https://mikefrobbins.com/2013/07/04/how-to-create-powershell-script-modules-and-module-manifests/
[about_Modules]: /powershell/module/microsoft.powershell.core/about/about_modules
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[Export-ModuleMember]: /powershell/module/microsoft.powershell.core/export-modulemember
