---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-module?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Module
ms.openlocfilehash: 1f06d1e7114a84ea89097167b188ded605f81aa0
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564532"
---
# <span data-ttu-id="634b8-102">Get-Module</span><span class="sxs-lookup"><span data-stu-id="634b8-102">Get-Module</span></span>

## <span data-ttu-id="634b8-103">概要</span><span class="sxs-lookup"><span data-stu-id="634b8-103">SYNOPSIS</span></span>
<span data-ttu-id="634b8-104">列出在目前會話中匯入的模組，或可從 PSModulePath 匯入的模組。</span><span class="sxs-lookup"><span data-stu-id="634b8-104">List the modules imported in the current session or that can be imported from the PSModulePath.</span></span>

## <span data-ttu-id="634b8-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="634b8-105">SYNTAX</span></span>

### <span data-ttu-id="634b8-106">已載入 (預設) </span><span class="sxs-lookup"><span data-stu-id="634b8-106">Loaded (Default)</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-All] [<CommonParameters>]
```

### <span data-ttu-id="634b8-107">可用</span><span class="sxs-lookup"><span data-stu-id="634b8-107">Available</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-All] [-ListAvailable]
 [-PSEdition <String>] [-SkipEditionCheck] [-Refresh] [<CommonParameters>]
```

### <span data-ttu-id="634b8-108">PsSession</span><span class="sxs-lookup"><span data-stu-id="634b8-108">PsSession</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-ListAvailable]
 [-PSEdition <String>] [-SkipEditionCheck] [-Refresh] -PSSession <PSSession> [<CommonParameters>]
```

### <span data-ttu-id="634b8-109">CimSession</span><span class="sxs-lookup"><span data-stu-id="634b8-109">CimSession</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-ListAvailable]
 [-SkipEditionCheck] [-Refresh] -CimSession <CimSession> [-CimResourceUri <Uri>] [-CimNamespace <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="634b8-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="634b8-110">DESCRIPTION</span></span>

<span data-ttu-id="634b8-111">此 `Get-Module` Cmdlet 會列出已匯入或可匯入至 powershell 會話的 powershell 模組。</span><span class="sxs-lookup"><span data-stu-id="634b8-111">The `Get-Module` cmdlet lists the PowerShell modules that have been imported, or that can be imported, into a PowerShell session.</span></span> <span data-ttu-id="634b8-112">如果沒有參數，會 `Get-Module` 取得已匯入目前會話的模組。</span><span class="sxs-lookup"><span data-stu-id="634b8-112">Without parameters, `Get-Module` gets modules that have been imported into the current session.</span></span> <span data-ttu-id="634b8-113">**ListAvailable** 參數是用來列出可從 PSModulePath 環境變數中指定的路徑匯入的模組 (`$env:PSModulePath`) 。</span><span class="sxs-lookup"><span data-stu-id="634b8-113">The **ListAvailable** parameter is used to list the modules that are available to be imported from the paths specified in the PSModulePath environment variable (`$env:PSModulePath`).</span></span>

<span data-ttu-id="634b8-114">傳回的模組物件 `Get-Module` 包含有關模組的重要資訊。</span><span class="sxs-lookup"><span data-stu-id="634b8-114">The module object that `Get-Module` returns contains valuable information about the module.</span></span> <span data-ttu-id="634b8-115">您也可以透過管線將模組物件傳送至其他 Cmdlet，例如 `Import-Module` 和 `Remove-Module` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="634b8-115">You can also pipe the module objects to other cmdlets, such as the `Import-Module` and `Remove-Module` cmdlets.</span></span>

<span data-ttu-id="634b8-116">`Get-Module` 列出模組，但不會將它們匯入。</span><span class="sxs-lookup"><span data-stu-id="634b8-116">`Get-Module` lists modules, but it does not import them.</span></span> <span data-ttu-id="634b8-117">從 Windows PowerShell 3.0 開始，當您使用模組中的命令時，系統會自動匯入模組，但命令不會 `Get-Module` 觸發自動匯入。</span><span class="sxs-lookup"><span data-stu-id="634b8-117">Starting in Windows PowerShell 3.0, modules are automatically imported when you use a command in the module, but a `Get-Module` command does not trigger an automatic import.</span></span> <span data-ttu-id="634b8-118">您也可以使用 Cmdlet，將模組匯入到您的會話 `Import-Module` 。</span><span class="sxs-lookup"><span data-stu-id="634b8-118">You can also import the modules into your session using the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="634b8-119">從 Windows PowerShell 3.0 開始，您可以從遠端會話匯入模組，然後匯入本機會話。</span><span class="sxs-lookup"><span data-stu-id="634b8-119">Starting in Windows PowerShell 3.0, you can get and then, import modules from remote sessions into the local session.</span></span> <span data-ttu-id="634b8-120">此策略使用 PowerShell 的隱含遠端功能，相當於使用 `Import-PSSession` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="634b8-120">This strategy uses the Implicit Remoting feature of PowerShell and is equivalent to using the `Import-PSSession` cmdlet.</span></span> <span data-ttu-id="634b8-121">當您在從另一個會話匯入的模組中使用命令時，命令會隱含地在遠端會話中執行。</span><span class="sxs-lookup"><span data-stu-id="634b8-121">When you use commands in modules imported from another session, the commands run implicitly in the remote session.</span></span> <span data-ttu-id="634b8-122">這項功能可讓您從本機會話管理遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="634b8-122">This feature lets you manage the remote computer from the local session.</span></span>

<span data-ttu-id="634b8-123">此外，從 Windows PowerShell 3.0 開始，您可以使用 `Get-Module` 和 `Import-Module` 來取得通用訊息模型 (CIM) 模組並加以匯入。</span><span class="sxs-lookup"><span data-stu-id="634b8-123">Also, starting in Windows PowerShell 3.0, you can use `Get-Module` and `Import-Module` to get and import Common Information Model (CIM) modules.</span></span> <span data-ttu-id="634b8-124">CIM 模組會在 Cmdlet 定義 XML (CDXML) 檔中定義 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="634b8-124">CIM modules define cmdlets in Cmdlet Definition XML (CDXML) files.</span></span> <span data-ttu-id="634b8-125">這項功能可讓您使用在非受控程式碼元件中執行的 Cmdlet，例如以 c + + 撰寫的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="634b8-125">This feature lets you use cmdlets that are implemented in non-managed code assemblies, such as those written in C++.</span></span>

<span data-ttu-id="634b8-126">您可以使用隱含遠端來管理已啟用 PowerShell 遠端功能的遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="634b8-126">Implicit remoting can be used to manage remote computers that have PowerShell remoting enabled.</span></span>
<span data-ttu-id="634b8-127">在遠端電腦上建立 **pssession** ，然後使用的 **pssession** 參數 `Get-Module` 取得遠端會話中的 PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="634b8-127">Create a **PSSession** on the remote computer and then use the **PSSession** parameter of `Get-Module` to get the PowerShell modules in the remote session.</span></span> <span data-ttu-id="634b8-128">當您從遠端會話匯入模組時，匯入的命令會在遠端電腦的會話中執行。</span><span class="sxs-lookup"><span data-stu-id="634b8-128">When you import a module from the remote session the imported commands run in the session on the remote computer.</span></span>

<span data-ttu-id="634b8-129">您可以使用類似的策略來管理未啟用 PowerShell 遠端功能的電腦。</span><span class="sxs-lookup"><span data-stu-id="634b8-129">You can use a similar strategy to manage computers that do not have PowerShell remoting enabled.</span></span>
<span data-ttu-id="634b8-130">這些包括不是執行 Windows 作業系統的電腦，以及具有 PowerShell 但未啟用 PowerShell 遠端功能的電腦。</span><span class="sxs-lookup"><span data-stu-id="634b8-130">These include computers that are not running the Windows operating system, and computers that have PowerShell but do not have PowerShell remoting enabled.</span></span>

<span data-ttu-id="634b8-131">一開始先在遠端電腦上建立 CIM 會話。</span><span class="sxs-lookup"><span data-stu-id="634b8-131">Start by creating a CIM session on the remote computer.</span></span> <span data-ttu-id="634b8-132">CIM 會話是連接至遠端電腦上 Windows Management Instrumentation (WMI) 的連線。</span><span class="sxs-lookup"><span data-stu-id="634b8-132">A CIM session is a connection to Windows Management Instrumentation (WMI) on the remote computer.</span></span> <span data-ttu-id="634b8-133">然後使用的 **CIMSession** 參數 `Get-Module` ，從 CIM 會話取得 cim 模組。</span><span class="sxs-lookup"><span data-stu-id="634b8-133">Then use the **CIMSession** parameter of `Get-Module` to get CIM modules from the CIM session.</span></span> <span data-ttu-id="634b8-134">當您使用 Cmdlet 匯入 CIM 模組， `Import-Module` 然後執行匯入的命令時，命令會隱含地在遠端電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="634b8-134">When you import a CIM module by using the `Import-Module` cmdlet and then run the imported commands, the commands run implicitly on the remote computer.</span></span> <span data-ttu-id="634b8-135">您可以使用這個 WMI 和 CIM 策略來管理遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="634b8-135">You can use this WMI and CIM strategy to manage the remote computer.</span></span>

## <span data-ttu-id="634b8-136">範例</span><span class="sxs-lookup"><span data-stu-id="634b8-136">EXAMPLES</span></span>

### <span data-ttu-id="634b8-137">範例1：取得匯入目前會話的模組</span><span class="sxs-lookup"><span data-stu-id="634b8-137">Example 1: Get modules imported into the current session</span></span>

```powershell
Get-Module
```

<span data-ttu-id="634b8-138">此命令取得已匯入目前工作階段的模組。</span><span class="sxs-lookup"><span data-stu-id="634b8-138">This command gets modules that have been imported into the current session.</span></span>

### <span data-ttu-id="634b8-139">範例2：取得已安裝的模組和可用的模組</span><span class="sxs-lookup"><span data-stu-id="634b8-139">Example 2: Get installed modules and available modules</span></span>

```powershell
Get-Module -ListAvailable
```

<span data-ttu-id="634b8-140">此命令取得已安裝於電腦上，且可匯入目前工作階段的模組。</span><span class="sxs-lookup"><span data-stu-id="634b8-140">This command gets the modules that are installed on the computer and can be imported into the current session.</span></span>

<span data-ttu-id="634b8-141">`Get-Module` 在 **$env:P smodulepath** 環境變數所指定的路徑中尋找可用的模組。</span><span class="sxs-lookup"><span data-stu-id="634b8-141">`Get-Module` looks for available modules in the path specified by the **$env:PSModulePath** environment variable.</span></span> <span data-ttu-id="634b8-142">如需 **PSModulePath** 的詳細資訊，請參閱 [about_Modules](About/about_Modules.md) 和 [about_Environment_Variables](About/about_Environment_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="634b8-142">For more information about **PSModulePath**, see [about_Modules](About/about_Modules.md) and [about_Environment_Variables](About/about_Environment_Variables.md).</span></span>

### <span data-ttu-id="634b8-143">範例3：取得所有匯出的檔案</span><span class="sxs-lookup"><span data-stu-id="634b8-143">Example 3: Get all exported files</span></span>

```powershell
Get-Module -ListAvailable -All
```

<span data-ttu-id="634b8-144">此命令取得所有可用模組的所有匯出檔案。</span><span class="sxs-lookup"><span data-stu-id="634b8-144">This command gets all of the exported files for all available modules.</span></span>

### <span data-ttu-id="634b8-145">範例4：依完整名稱取得模組</span><span class="sxs-lookup"><span data-stu-id="634b8-145">Example 4: Get a module by its fully qualified name</span></span>

```powershell
$FullyQualifedName = @{ModuleName="Microsoft.PowerShell.Management";ModuleVersion="3.1.0.0"}
Get-Module -FullyQualifiedName $FullyQualifedName | Format-Table -Property Name,Version
```

```Output
Name                             Version
----                             -------
Microsoft.PowerShell.Management  3.1.0.0
```

<span data-ttu-id="634b8-146">此命令會使用 **FullyQualifiedName** 參數來指定模組的完整名稱，以取得 **Microsoft. 管理** 模組。</span><span class="sxs-lookup"><span data-stu-id="634b8-146">This command gets the **Microsoft.PowerShell.Management** module by specifying the fully qualified name of the module by using the **FullyQualifiedName** parameter.</span></span> <span data-ttu-id="634b8-147">命令接著會使用管線將結果傳送至 `Format-Table` Cmdlet，將結果格式化為具有 **Name** 和 **Version** 的資料表做為資料行標題。</span><span class="sxs-lookup"><span data-stu-id="634b8-147">The command then pipes the results into the `Format-Table` cmdlet to format the results as a table with **Name** and **Version** as the column headings.</span></span>

### <span data-ttu-id="634b8-148">範例5：取得模組的屬性</span><span class="sxs-lookup"><span data-stu-id="634b8-148">Example 5: Get properties of a module</span></span>

```powershell
Get-Module | Get-Member -MemberType Property | Format-Table Name
```

```Output
Name
----
AccessMode
Author
ClrVersion
CompanyName
Copyright
Definition
Description
DotNetFrameworkVersion
ExportedAliases
ExportedCmdlets
ExportedCommands
ExportedFormatFiles
ExportedFunctions
ExportedTypeFiles
ExportedVariables
ExportedWorkflows
FileList
Guid
HelpInfoUri
LogPipelineExecutionDetails
ModuleBase
ModuleList
ModuleType
Name
NestedModules
OnRemove
Path
PowerShellHostName
PowerShellHostVersion
PowerShellVersion
PrivateData
ProcessorArchitecture
RequiredAssemblies
RequiredModules
RootModule
Scripts
SessionState
Version
```

<span data-ttu-id="634b8-149">此命令會取得傳回之 **PSModuleInfo** 物件的屬性 `Get-Module` 。</span><span class="sxs-lookup"><span data-stu-id="634b8-149">This command gets the properties of the **PSModuleInfo** object that `Get-Module` returns.</span></span> <span data-ttu-id="634b8-150">每個模組檔案都有一個物件。</span><span class="sxs-lookup"><span data-stu-id="634b8-150">There is one object for each module file.</span></span>

<span data-ttu-id="634b8-151">您可以使用屬性來格式化和篩選模組物件。</span><span class="sxs-lookup"><span data-stu-id="634b8-151">You can use the properties to format and filter the module objects.</span></span> <span data-ttu-id="634b8-152">如需屬性的詳細資訊，請參閱 [PSModuleInfo 屬性](/dotnet/api/system.management.automation.psmoduleinfo)。</span><span class="sxs-lookup"><span data-stu-id="634b8-152">For more information about the properties, see [PSModuleInfo Properties](/dotnet/api/system.management.automation.psmoduleinfo).</span></span>

<span data-ttu-id="634b8-153">輸出包含在 Windows PowerShell 3.0 中引進的新屬性，例如 **Author** 和 **公司名稱**。</span><span class="sxs-lookup"><span data-stu-id="634b8-153">The output includes the new properties, such as **Author** and **CompanyName**, that were introduced in Windows PowerShell 3.0.</span></span>

### <span data-ttu-id="634b8-154">範例6：依名稱將所有模組分組</span><span class="sxs-lookup"><span data-stu-id="634b8-154">Example 6: Group all modules by name</span></span>

```powershell
Get-Module -ListAvailable -All | Format-Table -Property Name, Moduletype, Path -Groupby Name
```

```Output
Name: AppLocker

Name      ModuleType Path
----      ---------- ----
AppLocker   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\AppLocker\AppLocker.psd1


   Name: Appx

Name ModuleType Path
---- ---------- ----
Appx   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Appx\en-US\Appx.psd1
Appx   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Appx\Appx.psd1
Appx     Script C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Appx\Appx.psm1


   Name: BestPractices

Name          ModuleType Path
----          ---------- ----
BestPractices   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\BestPractices\BestPractices.psd1


   Name: BitsTransfer

Name         ModuleType Path
----         ---------- ----
BitsTransfer   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\BitsTransfer\BitsTransfer.psd1
```

<span data-ttu-id="634b8-155">此命令會取得所有模組檔案（已匯入和可用），然後依模組名稱將它們分組。</span><span class="sxs-lookup"><span data-stu-id="634b8-155">This command gets all module files, both imported and available, and then groups them by module name.</span></span> <span data-ttu-id="634b8-156">這可讓您查看每個指令碼正在匯出的模組檔案。</span><span class="sxs-lookup"><span data-stu-id="634b8-156">This lets you see the module files that each script is exporting.</span></span>

### <span data-ttu-id="634b8-157">範例7：顯示模組資訊清單的內容</span><span class="sxs-lookup"><span data-stu-id="634b8-157">Example 7: Display the contents of a module manifest</span></span>

<span data-ttu-id="634b8-158">這些命令會顯示 Windows PowerShell **BitsTransfer** 模組的模組資訊清單內容。</span><span class="sxs-lookup"><span data-stu-id="634b8-158">These commands display the contents of the module manifest for the Windows PowerShell **BitsTransfer** module.</span></span>

<span data-ttu-id="634b8-159">模組不需要有資訊清單檔案。</span><span class="sxs-lookup"><span data-stu-id="634b8-159">Modules are not required to have manifest files.</span></span> <span data-ttu-id="634b8-160">當他們有資訊清單檔時，資訊清單檔只需要包含版本號碼。</span><span class="sxs-lookup"><span data-stu-id="634b8-160">When they do have a manifest file, the manifest file is required only to include a version number.</span></span> <span data-ttu-id="634b8-161">不過，資訊清單檔案通常會提供模組、其需求及其內容的實用資訊。</span><span class="sxs-lookup"><span data-stu-id="634b8-161">However, manifest files often provide useful information about a module, its requirements, and its contents.</span></span>

```powershell
# First command
$m = Get-Module -list -Name BitsTransfer

# Second command
Get-Content $m.Path
```

```Output
@ {
    GUID               = "{8FA5064B-8479-4c5c-86EA-0D311FE48875}"
    Author             = "Microsoft Corporation"
    CompanyName        = "Microsoft Corporation"
    Copyright          = "Microsoft Corporation. All rights reserved."
    ModuleVersion      = "1.0.0.0"
    Description        = "Windows PowerShell File Transfer Module"
    PowerShellVersion  = "2.0"
    CLRVersion         = "2.0"
    NestedModules      = "Microsoft.BackgroundIntelligentTransfer.Management"
    FormatsToProcess   = "FileTransfer.Format.ps1xml"
    RequiredAssemblies = Join-Path $psScriptRoot "Microsoft.BackgroundIntelligentTransfer.Management.Interop.dll"
}
```

<span data-ttu-id="634b8-162">第一個命令取得代表 BitsTransfer 模組的 PSModuleInfo 物件。</span><span class="sxs-lookup"><span data-stu-id="634b8-162">The first command gets the PSModuleInfo object that represents BitsTransfer module.</span></span> <span data-ttu-id="634b8-163">它會將物件儲存在 `$m` 變數中。</span><span class="sxs-lookup"><span data-stu-id="634b8-163">It saves the object in the `$m` variable.</span></span>

<span data-ttu-id="634b8-164">第二個命令會使用 `Get-Content` Cmdlet 取得指定路徑中資訊清單檔的內容。</span><span class="sxs-lookup"><span data-stu-id="634b8-164">The second command uses the `Get-Content` cmdlet to get the content of the manifest file in the specified path.</span></span> <span data-ttu-id="634b8-165">它會使用點標記法，取得儲存在物件的 Path 屬性中的資訊清單檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="634b8-165">It uses dot notation to get the path to the manifest file, which is stored in the Path property of the object.</span></span> <span data-ttu-id="634b8-166">輸出會顯示模組資訊清單的內容。</span><span class="sxs-lookup"><span data-stu-id="634b8-166">The output shows the contents of the module manifest.</span></span>

### <span data-ttu-id="634b8-167">範例8：列出模組目錄中的檔案</span><span class="sxs-lookup"><span data-stu-id="634b8-167">Example 8: List files in module directory</span></span>

```powershell
dir (Get-Module -ListAvailable FileTransfer).ModuleBase
```

```Output
Directory: C:\Windows\system32\WindowsPowerShell\v1.0\Modules\FileTransfer
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/16/2008  12:36 PM            en-US
-a---        11/19/2008  11:30 PM      16184 FileTransfer.Format.ps1xml
-a---        11/20/2008  11:30 PM       1044 FileTransfer.psd1
-a---        12/16/2008  12:20 AM     108544 Microsoft.BackgroundIntelligentTransfer.Management.Interop.dll
```

<span data-ttu-id="634b8-168">此命令會列出模組目錄中的檔案。</span><span class="sxs-lookup"><span data-stu-id="634b8-168">This command lists the files in the directory of the module.</span></span> <span data-ttu-id="634b8-169">這是在您將模組匯入之前，可用來判斷模組中有哪些內容的另一種方式。</span><span class="sxs-lookup"><span data-stu-id="634b8-169">This is another way to determine what is in a module before you import it.</span></span> <span data-ttu-id="634b8-170">某些模組可能含有說明檔或描述模組的讀我檔案。</span><span class="sxs-lookup"><span data-stu-id="634b8-170">Some modules might have help files or ReadMe files that describe the module.</span></span>

### <span data-ttu-id="634b8-171">範例9：取得安裝在電腦上的模組</span><span class="sxs-lookup"><span data-stu-id="634b8-171">Example 9: Get modules installed on a computer</span></span>

```powershell
$s = New-PSSession -ComputerName Server01

Get-Module -PSSession $s -ListAvailable
```

<span data-ttu-id="634b8-172">這些命令會取得 Server01 電腦上安裝的模組。</span><span class="sxs-lookup"><span data-stu-id="634b8-172">These commands get the modules that are installed on the Server01 computer.</span></span>

<span data-ttu-id="634b8-173">第一個命令會使用 `New-PSSession` Cmdlet 在 Server01 電腦上建立 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="634b8-173">The first command uses the `New-PSSession` cmdlet to create a **PSSession** on the Server01 computer.</span></span> <span data-ttu-id="634b8-174">命令會將 **PSSession** 儲存在 $s 變數中。</span><span class="sxs-lookup"><span data-stu-id="634b8-174">The command saves the **PSSession** in the $s variable.</span></span>

<span data-ttu-id="634b8-175">第二個命令使用的 **pssession** 和 **ListAvailable** 參數 `Get-Module` ，取得變數中 **pssession** 內的模組 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="634b8-175">The second command uses the **PSSession** and **ListAvailable** parameters of `Get-Module` to get the modules in the **PSSession** in the `$s` variable.</span></span>

<span data-ttu-id="634b8-176">如果您使用管線將模組從其他會話傳送至 `Import-Module` Cmdlet，則會 `Import-Module` 使用隱含的遠端功能，將模組匯入目前的會話中。</span><span class="sxs-lookup"><span data-stu-id="634b8-176">If you pipe modules from other sessions to the `Import-Module` cmdlet, `Import-Module` imports the module into the current session by using the implicit remoting feature.</span></span> <span data-ttu-id="634b8-177">這相當於使用 `Import-PSSession` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="634b8-177">This is equivalent to using the `Import-PSSession` cmdlet.</span></span> <span data-ttu-id="634b8-178">您可以使用目前工作階段中模組的 Cmdlet，但是，使用這些 Cmdlet 的命令實際上會執行遠端工作階段。</span><span class="sxs-lookup"><span data-stu-id="634b8-178">You can use the cmdlets from the module in the current session, but commands that use these cmdlets actually run the remote session.</span></span> <span data-ttu-id="634b8-179">如需詳細資訊，請參閱 [`Import-Module`](Import-Module.md) 和 [`Import-PSSession`](../Microsoft.PowerShell.Utility/Import-PSSession.md)。</span><span class="sxs-lookup"><span data-stu-id="634b8-179">For more information, see [`Import-Module`](Import-Module.md) and [`Import-PSSession`](../Microsoft.PowerShell.Utility/Import-PSSession.md).</span></span>

### <span data-ttu-id="634b8-180">範例10：管理未執行 Windows 作業系統的電腦</span><span class="sxs-lookup"><span data-stu-id="634b8-180">Example 10: Manage a computer that does not run the Windows operating system</span></span>

<span data-ttu-id="634b8-181">此範例中的命令可讓您管理不是執行 Windows 作業系統之遠端電腦的儲存系統。</span><span class="sxs-lookup"><span data-stu-id="634b8-181">The commands in this example enable you to manage the storage systems of a remote computer that is not running the Windows operating system.</span></span>
<span data-ttu-id="634b8-182">在這個範例中，因為電腦的系統管理員已安裝「模組探索」WMI 提供者，所以 CIM 命令可以使用專為提供者設計的預設值。</span><span class="sxs-lookup"><span data-stu-id="634b8-182">In this example, because the administrator of the computer has installed the Module Discovery WMI provider, the CIM commands can use the default values, which are designed for the provider.</span></span>

```powershell
$cs = New-CimSession -ComputerName RSDGF03
Get-Module -CimSession $cs -Name Storage | Import-Module
Get-Command Get-Disk
```

```Output
CommandType     Name                  ModuleName
-----------     ----                  ----------
Function        Get-Disk              Storage
```

```powershell
Get-Disk
```

```Output
Number Friendly Name              OperationalStatus          Total Size Partition Style
------ -------------              -----------------          ---------- ---------------
0      Virtual HD ATA Device      Online                          40 GB MBR
```

<span data-ttu-id="634b8-183">第一個命令會使用 `New-CimSession` Cmdlet 在 RSDGF03 遠端電腦上建立會話。</span><span class="sxs-lookup"><span data-stu-id="634b8-183">The first command uses the `New-CimSession` cmdlet to create a session on the RSDGF03 remote computer.</span></span> <span data-ttu-id="634b8-184">工作階段會連線遠端電腦上的 WMI。</span><span class="sxs-lookup"><span data-stu-id="634b8-184">The session connects to WMI on the remote computer.</span></span> <span data-ttu-id="634b8-185">此命令會將 CIM 會話儲存在 `$cs` 變數中。</span><span class="sxs-lookup"><span data-stu-id="634b8-185">The command saves the CIM session in the `$cs` variable.</span></span>

<span data-ttu-id="634b8-186">第二個命令會使用變數中的 CIM 會話 `$cs` ，在 `Get-Module` RSDGF03 電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="634b8-186">The second command uses the CIM session in the `$cs` variable to run a `Get-Module` command on the RSDGF03 computer.</span></span> <span data-ttu-id="634b8-187">命令使用 Name 參數指定 Storage 模組。</span><span class="sxs-lookup"><span data-stu-id="634b8-187">The command uses the Name parameter to specify the Storage module.</span></span> <span data-ttu-id="634b8-188">命令使用管線運算子 (|) 將儲存體模組傳送至 `Import-Module` Cmdlet，以將它匯入本機會話。</span><span class="sxs-lookup"><span data-stu-id="634b8-188">The command uses a pipeline operator (|) to send the Storage module to the `Import-Module` cmdlet, which imports it into the local session.</span></span>

<span data-ttu-id="634b8-189">第三個命令會在 `Get-Command` `Get-Disk` 儲存體模組中的命令上執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="634b8-189">The third command runs the `Get-Command` cmdlet on the `Get-Disk` command in the Storage module.</span></span>
<span data-ttu-id="634b8-190">當您將 CIM 模組匯入本機會話時，PowerShell 會將代表 CIM 模組的 CDXML 檔案轉換成 PowerShell 腳本，這會顯示為本機會話中的函式。</span><span class="sxs-lookup"><span data-stu-id="634b8-190">When you import a CIM module into the local session, PowerShell converts the CDXML files that represent the CIM module into PowerShell scripts, which appear as functions in the local session.</span></span>

<span data-ttu-id="634b8-191">第四個命令會執行 `Get-Disk` 命令。</span><span class="sxs-lookup"><span data-stu-id="634b8-191">The fourth command runs the `Get-Disk` command.</span></span> <span data-ttu-id="634b8-192">雖然命令是在本機工作階段中輸入，但是它會在匯入它的遠端電腦上隱含執行。</span><span class="sxs-lookup"><span data-stu-id="634b8-192">Although the command is typed in the local session, it runs implicitly on the remote computer from which it was imported.</span></span> <span data-ttu-id="634b8-193">命令會從遠端電腦取得物件，並將其傳回本機工作階段。</span><span class="sxs-lookup"><span data-stu-id="634b8-193">The command gets objects from the remote computer and returns them to the local session.</span></span>

## <span data-ttu-id="634b8-194">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="634b8-194">PARAMETERS</span></span>

### <span data-ttu-id="634b8-195">-All</span><span class="sxs-lookup"><span data-stu-id="634b8-195">-All</span></span>

<span data-ttu-id="634b8-196">指出此 Cmdlet 會取得每個模組資料夾中的所有模組，包括嵌套模組、資訊清單 ( .psd1) 檔案、腳本模組 (. .psm1) 檔案，以及二進位模組 ( .dll) 檔。</span><span class="sxs-lookup"><span data-stu-id="634b8-196">Indicates that this cmdlet gets all modules in each module folder, including nested modules, manifest (.psd1) files, script module (.psm1) files, and binary module (.dll) files.</span></span> <span data-ttu-id="634b8-197">如果沒有這個參數，則 `Get-Module` 只會取得每個模組資料夾中的預設模組。</span><span class="sxs-lookup"><span data-stu-id="634b8-197">Without this parameter, `Get-Module` gets only the default module in each module folder.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Loaded, Available
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="634b8-198">-CimNamespace</span><span class="sxs-lookup"><span data-stu-id="634b8-198">-CimNamespace</span></span>

<span data-ttu-id="634b8-199">指定公開 CIM 模組的替代 CIM 提供者命名空間。</span><span class="sxs-lookup"><span data-stu-id="634b8-199">Specifies the namespace of an alternate CIM provider that exposes CIM modules.</span></span> <span data-ttu-id="634b8-200">預設值為「模組探索」WMI 提供者的命名空間。</span><span class="sxs-lookup"><span data-stu-id="634b8-200">The default value is the namespace of the Module Discovery WMI provider.</span></span>

<span data-ttu-id="634b8-201">使用此參數從不是執行 Windows 作業系統的電腦和裝置取得 CIM 模組。</span><span class="sxs-lookup"><span data-stu-id="634b8-201">Use this parameter to get CIM modules from computers and devices that are not running the Windows operating system.</span></span>

<span data-ttu-id="634b8-202">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="634b8-202">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="634b8-203">-CimResourceUri</span><span class="sxs-lookup"><span data-stu-id="634b8-203">-CimResourceUri</span></span>

<span data-ttu-id="634b8-204">指定 CIM 模組的替代位置。</span><span class="sxs-lookup"><span data-stu-id="634b8-204">Specifies an alternate location for CIM modules.</span></span> <span data-ttu-id="634b8-205">預設值為遠端電腦上「模組探索」 WMI 提供者的資源 URI。</span><span class="sxs-lookup"><span data-stu-id="634b8-205">The default value is the resource URI of the Module Discovery WMI provider on the remote computer.</span></span>

<span data-ttu-id="634b8-206">使用此參數從不是執行 Windows 作業系統的電腦和裝置取得 CIM 模組。</span><span class="sxs-lookup"><span data-stu-id="634b8-206">Use this parameter to get CIM modules from computers and devices that are not running the Windows operating system.</span></span>

<span data-ttu-id="634b8-207">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="634b8-207">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Uri
Parameter Sets: CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="634b8-208">-CimSession</span><span class="sxs-lookup"><span data-stu-id="634b8-208">-CimSession</span></span>

<span data-ttu-id="634b8-209">指定遠端電腦上的 CIM 工作階段。</span><span class="sxs-lookup"><span data-stu-id="634b8-209">Specifies a CIM session on the remote computer.</span></span> <span data-ttu-id="634b8-210">輸入包含 CIM 會話的變數，或輸入可取得 CIM 會話的命令，例如 [CimSession](/powershell/module/cimcmdlets/get-cimsession) 命令。</span><span class="sxs-lookup"><span data-stu-id="634b8-210">Enter a variable that contains the CIM session or a command that gets the CIM session, such as a [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) command.</span></span>

<span data-ttu-id="634b8-211">`Get-Module` 使用 CIM 會話連接從遠端電腦取得模組。</span><span class="sxs-lookup"><span data-stu-id="634b8-211">`Get-Module` uses the CIM session connection to get modules from the remote computer.</span></span> <span data-ttu-id="634b8-212">當您使用 Cmdlet 匯入模組 `Import-Module` ，並在目前的會話中使用匯入模組的命令時，命令實際上會在遠端電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="634b8-212">When you import the module by using the `Import-Module` cmdlet and use the commands from the imported module in the current session, the commands actually run on the remote computer.</span></span>

<span data-ttu-id="634b8-213">您可以使用此參數從不是執行 Windows 作業系統的電腦和裝置，以及具有 PowerShell 但未啟用 PowerShell 遠端處理的電腦取得模組。</span><span class="sxs-lookup"><span data-stu-id="634b8-213">You can use this parameter to get modules from computers and devices that are not running the Windows operating system, and computers that have PowerShell, but do not have PowerShell remoting enabled.</span></span>

<span data-ttu-id="634b8-214">**CimSession** 參數會取得 **CIMSession** 中的所有模組。</span><span class="sxs-lookup"><span data-stu-id="634b8-214">The **CimSession** parameter gets all modules in the **CIMSession**.</span></span> <span data-ttu-id="634b8-215">不過，您可以只匯入 CIM 型和「Cmdlet 定義 XML (CDXML)」型模組。</span><span class="sxs-lookup"><span data-stu-id="634b8-215">However, you can import only CIM-based and Cmdlet Definition XML (CDXML)-based modules.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession
Parameter Sets: CimSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="634b8-216">-FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="634b8-216">-FullyQualifiedName</span></span>

<span data-ttu-id="634b8-217">指定以 **ModuleSpecification** 物件形式指定之名稱的模組。</span><span class="sxs-lookup"><span data-stu-id="634b8-217">Specifies modules with names that are specified in the form of **ModuleSpecification** objects.</span></span> <span data-ttu-id="634b8-218">請參閱 [ModuleSpecification (雜湊表) ](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_)的「備註」一節。</span><span class="sxs-lookup"><span data-stu-id="634b8-218">See the Remarks section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>

<span data-ttu-id="634b8-219">例如， **FullyQualifiedModule** 參數會接受以下列其中一種格式指定的模組名稱：</span><span class="sxs-lookup"><span data-stu-id="634b8-219">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in either of these formats:</span></span>

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

<span data-ttu-id="634b8-220">**ModuleName** 和 **ModuleVersion** 是必要參數，但 **Guid** 是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="634b8-220">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span> <span data-ttu-id="634b8-221">您無法在與 **模組** 參數相同的命令中指定 **FullyQualifiedModule** 參數。</span><span class="sxs-lookup"><span data-stu-id="634b8-221">You cannot specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span> <span data-ttu-id="634b8-222">這兩個參數是互斥的。</span><span class="sxs-lookup"><span data-stu-id="634b8-222">the two parameters are mutually exclusive.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="634b8-223">-ListAvailable</span><span class="sxs-lookup"><span data-stu-id="634b8-223">-ListAvailable</span></span>

<span data-ttu-id="634b8-224">指出此 Cmdlet 會取得所有已安裝的模組。</span><span class="sxs-lookup"><span data-stu-id="634b8-224">Indicates that this cmdlet gets all installed modules.</span></span> <span data-ttu-id="634b8-225">`Get-Module` 取得 **PSModulePath** 環境變數所列路徑中的模組。</span><span class="sxs-lookup"><span data-stu-id="634b8-225">`Get-Module` gets modules in paths listed in the **PSModulePath** environment variable.</span></span> <span data-ttu-id="634b8-226">如果沒有這個參數，則 `Get-Module` 只會取得 **PSModulePath** 環境變數中所列的模組，以及在目前的會話中載入的模組。</span><span class="sxs-lookup"><span data-stu-id="634b8-226">Without this parameter, `Get-Module` gets only the modules that are both listed in the **PSModulePath** environment variable, and that are loaded in the current session.</span></span> <span data-ttu-id="634b8-227">**ListAvailable** 不會傳回 **PSModulePath** 環境變數中找不到的模組相關資訊，即使這些模組已載入目前工作階段也一樣。</span><span class="sxs-lookup"><span data-stu-id="634b8-227">**ListAvailable** does not return information about modules that are not found in the **PSModulePath** environment variable, even if those modules are loaded in the current session.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Available, PsSession, CimSession
Aliases:

Required: True (Available), False (PsSession, CimSession)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="634b8-228">-Name</span><span class="sxs-lookup"><span data-stu-id="634b8-228">-Name</span></span>

<span data-ttu-id="634b8-229">指定此 Cmdlet 取得之模組的名稱或名稱模式。</span><span class="sxs-lookup"><span data-stu-id="634b8-229">Specifies names or name patterns of modules that this cmdlet gets.</span></span> <span data-ttu-id="634b8-230">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="634b8-230">Wildcard characters are permitted.</span></span> <span data-ttu-id="634b8-231">您也可以透過管線將名稱傳送至 `Get-Module` 。</span><span class="sxs-lookup"><span data-stu-id="634b8-231">You can also pipe the names to `Get-Module`.</span></span> <span data-ttu-id="634b8-232">您無法在與 **Name** 參數相同的命令中指定 **FullyQualifiedName** 參數。</span><span class="sxs-lookup"><span data-stu-id="634b8-232">You cannot specify the **FullyQualifiedName** parameter in the same command as a **Name** parameter.</span></span>

<span data-ttu-id="634b8-233">**名稱** 不能接受模組 GUID 做為值。</span><span class="sxs-lookup"><span data-stu-id="634b8-233">**Name** cannot accept a module GUID as a value.</span></span>
<span data-ttu-id="634b8-234">若要藉由指定 GUID 來傳回模組，請改用 **FullyQualifiedName** 。</span><span class="sxs-lookup"><span data-stu-id="634b8-234">To return modules by specifying a GUID, use **FullyQualifiedName** instead.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="634b8-235">-PSEdition</span><span class="sxs-lookup"><span data-stu-id="634b8-235">-PSEdition</span></span>

<span data-ttu-id="634b8-236">取得支援指定 PowerShell 版本的模組。</span><span class="sxs-lookup"><span data-stu-id="634b8-236">Gets the modules that support specified edition of PowerShell.</span></span>

<span data-ttu-id="634b8-237">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="634b8-237">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="634b8-238">桌上型</span><span class="sxs-lookup"><span data-stu-id="634b8-238">Desktop</span></span>
- <span data-ttu-id="634b8-239">核心</span><span class="sxs-lookup"><span data-stu-id="634b8-239">Core</span></span>

<span data-ttu-id="634b8-240">Get-Module Cmdlet 會針對指定的值檢查 **PSModuleInfo** 物件的 **CompatiblePSEditions** 屬性，並只傳回已設定的模組。</span><span class="sxs-lookup"><span data-stu-id="634b8-240">The Get-Module cmdlet checks **CompatiblePSEditions** property of **PSModuleInfo** object for the specified value and returns only those modules that have it set.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="634b8-241">**Desktop Edition：** 建置在 .NET Framework 上，與在完整使用量的 Windows 版本 (如 Server Core 和 Windows Desktop) 上執行的 PowerShell 指令碼和模組目標版本相容相容。</span><span class="sxs-lookup"><span data-stu-id="634b8-241">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
> - <span data-ttu-id="634b8-242">**Core Edition：** 建置在 .NET Core 上，與在降低使用量的 Windows 版本 (如 Nano Server 和 Windows IoT) 上執行的 PowerShell 指令碼和模組目標版本相容。</span><span class="sxs-lookup"><span data-stu-id="634b8-242">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

```yaml
Type: System.String
Parameter Sets: PsSession, Available
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="634b8-243">-PSSession</span><span class="sxs-lookup"><span data-stu-id="634b8-243">-PSSession</span></span>

<span data-ttu-id="634b8-244">取得指定之使用者管理的 PowerShell 會話中的模組 (**PSSession**) 。</span><span class="sxs-lookup"><span data-stu-id="634b8-244">Gets the modules in the specified user-managed PowerShell session (**PSSession**).</span></span> <span data-ttu-id="634b8-245">輸入包含會話的變數、可取得會話的命令（例如 `Get-PSSession` 命令）或建立會話的命令（例如 `New-PSSession` 命令）。</span><span class="sxs-lookup"><span data-stu-id="634b8-245">Enter a variable that contains the session, a command that gets the session, such as a `Get-PSSession` command, or a command that creates the session, such as a `New-PSSession` command.</span></span>

<span data-ttu-id="634b8-246">當會話連線到遠端電腦時，您必須指定 **ListAvailable** 參數。</span><span class="sxs-lookup"><span data-stu-id="634b8-246">When the session is connected to a remote computer, you must specify the **ListAvailable** parameter.</span></span>

<span data-ttu-id="634b8-247">`Get-Module`使用 **pssession** 參數的命令相當於使用 `Invoke-Command` Cmdlet `Get-Module -ListAvailable` 在 **PSSession** 中執行命令。</span><span class="sxs-lookup"><span data-stu-id="634b8-247">A `Get-Module` command that uses the **PSSession** parameter is equivalent to using the `Invoke-Command` cmdlet to run a `Get-Module -ListAvailable` command in a **PSSession**.</span></span>

<span data-ttu-id="634b8-248">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="634b8-248">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: PsSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="634b8-249">-Refresh</span><span class="sxs-lookup"><span data-stu-id="634b8-249">-Refresh</span></span>

<span data-ttu-id="634b8-250">指出此 Cmdlet 會重新整理已安裝命令的快取。</span><span class="sxs-lookup"><span data-stu-id="634b8-250">Indicates that this cmdlet refreshes the cache of installed commands.</span></span> <span data-ttu-id="634b8-251">當工作階段啟動時，即會建立命令快取。</span><span class="sxs-lookup"><span data-stu-id="634b8-251">The command cache is created when the session starts.</span></span> <span data-ttu-id="634b8-252">它可讓 `Get-Command` Cmdlet 從未匯入會話的模組中取得命令。</span><span class="sxs-lookup"><span data-stu-id="634b8-252">It enables the `Get-Command` cmdlet to get commands from modules that are not imported into the session.</span></span>

<span data-ttu-id="634b8-253">這個參數是專為開發和測試案例所設計，在這類案例中，模組的內容會在工作階段開始後變更。</span><span class="sxs-lookup"><span data-stu-id="634b8-253">This parameter is designed for development and testing scenarios in which the contents of modules have changed since the session started.</span></span>

<span data-ttu-id="634b8-254">當您在命令中指定 **Refresh** 參數時，必須指定 **ListAvailable**。</span><span class="sxs-lookup"><span data-stu-id="634b8-254">When you specify the **Refresh** parameter in a command, you must specify **ListAvailable**.</span></span>

<span data-ttu-id="634b8-255">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="634b8-255">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Available, PsSession, CimSession
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="634b8-256">-SkipEditionCheck</span><span class="sxs-lookup"><span data-stu-id="634b8-256">-SkipEditionCheck</span></span>

<span data-ttu-id="634b8-257">略過欄位的檢查 `CompatiblePSEditions` 。</span><span class="sxs-lookup"><span data-stu-id="634b8-257">Skips the check of the `CompatiblePSEditions` field.</span></span>

<span data-ttu-id="634b8-258">根據預設，Get-Module 會省略 `%windir%\System32\WindowsPowerShell\v1.0\Modules` 未在欄位中指定之目錄中的模組 `Core` `CompatiblePSEditions` 。</span><span class="sxs-lookup"><span data-stu-id="634b8-258">By default, Get-Module will omit modules in the `%windir%\System32\WindowsPowerShell\v1.0\Modules` directory that do not specify `Core` in the `CompatiblePSEditions` field.</span></span> <span data-ttu-id="634b8-259">當設定此參數時，不會 `Core` 包含模組，因此將會傳回不相容 PowerShell Core Windows PowerShell 模組路徑下的模組。</span><span class="sxs-lookup"><span data-stu-id="634b8-259">When this switch is set, modules without `Core` will be included, so that modules under the Windows PowerShell module path that are incompatible with PowerShell Core will be returned.</span></span>

<span data-ttu-id="634b8-260">在 macOS 和 Linux 上，此參數不會執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="634b8-260">On macOS and Linux, this parameter does nothing.</span></span>

<span data-ttu-id="634b8-261">如需詳細資訊，請參閱 [about_PowerShell_Editions](About/about_PowerShell_Editions.md) 。</span><span class="sxs-lookup"><span data-stu-id="634b8-261">See [about_PowerShell_Editions](About/about_PowerShell_Editions.md) for more information.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Available, PsSession, CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="634b8-262">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="634b8-262">CommonParameters</span></span>

<span data-ttu-id="634b8-263">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="634b8-263">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="634b8-264">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="634b8-264">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="634b8-265">輸入</span><span class="sxs-lookup"><span data-stu-id="634b8-265">INPUTS</span></span>

### <span data-ttu-id="634b8-266">System.String</span><span class="sxs-lookup"><span data-stu-id="634b8-266">System.String</span></span>

<span data-ttu-id="634b8-267">您可以透過管線將模組名稱傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="634b8-267">You can pipe module names to this cmdlet.</span></span>

## <span data-ttu-id="634b8-268">輸出</span><span class="sxs-lookup"><span data-stu-id="634b8-268">OUTPUTS</span></span>

### <span data-ttu-id="634b8-269">System.Management.Automation.PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="634b8-269">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="634b8-270">此 Cmdlet 會傳回代表模組的物件。</span><span class="sxs-lookup"><span data-stu-id="634b8-270">This cmdlet returns objects that represent modules.</span></span>
<span data-ttu-id="634b8-271">當您指定 **ListAvailable** 參數時， `Get-Module` 會傳回 **ModuleInfoGrouping** 物件，這是具有相同屬性和方法的 **PSModuleInfo** 物件類型。</span><span class="sxs-lookup"><span data-stu-id="634b8-271">When you specify the **ListAvailable** parameter, `Get-Module` returns a **ModuleInfoGrouping** object, which is a type of **PSModuleInfo** object that has the same properties and methods.</span></span>

## <span data-ttu-id="634b8-272">注意</span><span class="sxs-lookup"><span data-stu-id="634b8-272">NOTES</span></span>

- <span data-ttu-id="634b8-273">從 Windows PowerShell 3.0 開始，PowerShell 隨附的核心命令會封裝在模組中。</span><span class="sxs-lookup"><span data-stu-id="634b8-273">Beginning in Windows PowerShell 3.0, the core commands that are included in PowerShell are packaged in modules.</span></span> <span data-ttu-id="634b8-274">例外狀況是 **PSSnapin**) 的嵌入式管理單元 **(。**</span><span class="sxs-lookup"><span data-stu-id="634b8-274">The exception is **Microsoft.PowerShell.Core**, which is a snap-in (**PSSnapin**).</span></span> <span data-ttu-id="634b8-275">依照預設，只會新增 **Microsoft.PowerShell.Core** 嵌入式管理單元至工作階段。</span><span class="sxs-lookup"><span data-stu-id="634b8-275">By default, only the **Microsoft.PowerShell.Core** snap-in is added to the session.</span></span> <span data-ttu-id="634b8-276">模組會在第一次使用時自動匯入，而您可以使用 `Import-Module` Cmdlet 將它們匯入。</span><span class="sxs-lookup"><span data-stu-id="634b8-276">Modules are imported automatically on first use and you can use the `Import-Module` cmdlet to import them.</span></span>

- <span data-ttu-id="634b8-277">在 Windows PowerShell 2.0，以及在較新版本的 PowerShell 中建立舊版會話的主機程式中，會將核心命令封裝在嵌入式管理單元中， (**PSSnapins**) 。</span><span class="sxs-lookup"><span data-stu-id="634b8-277">In Windows PowerShell 2.0, and in host programs that create older-style sessions in later versions of PowerShell, the core commands are packaged in snap-ins (**PSSnapins**).</span></span> <span data-ttu-id="634b8-278">**Microsoft.PowerShell.Core** 是一個例外，它一律是一個嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="634b8-278">The exception is **Microsoft.PowerShell.Core**, which is always a snap-in.</span></span> <span data-ttu-id="634b8-279">此外，遠端會話（例如由 Cmdlet 啟動的會話） `New-PSSession` 都是包含核心嵌入式管理單元的較舊樣式會話。</span><span class="sxs-lookup"><span data-stu-id="634b8-279">Also, remote sessions, such as those started by the `New-PSSession` cmdlet, are older-style sessions that include core snap-ins.</span></span>

  <span data-ttu-id="634b8-280">如需使用核心模組建立較新樣式會話之 **CreateDefault2** 方法的詳細資訊，請參閱 [CreateDefault2 方法](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2)。</span><span class="sxs-lookup"><span data-stu-id="634b8-280">For information about the **CreateDefault2** method that creates newer-style sessions with core modules, see [CreateDefault2 Method](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2).</span></span>

- <span data-ttu-id="634b8-281">`Get-Module` 只會取得位置中的模組，這些位置會儲存在 **PSModulePath** 環境變數的值 ($Env:P smodulepath) 中。</span><span class="sxs-lookup"><span data-stu-id="634b8-281">`Get-Module` only gets modules in locations that are stored in the value of the **PSModulePath** environment variable ($env:PSModulePath).</span></span> <span data-ttu-id="634b8-282">`Import-Module`Cmdlet 可以在其他位置匯入模組，但您無法使用 `Get-Module` Cmdlet 來取得它們。</span><span class="sxs-lookup"><span data-stu-id="634b8-282">The `Import-Module` cmdlet can import modules in other locations, but you cannot use the `Get-Module` cmdlet to get them.</span></span>

- <span data-ttu-id="634b8-283">此外，從 PowerShell 3.0 開始，已在傳回的物件中加入新的屬性，讓您可以在匯 `Get-Module` 入模組之前，更輕鬆地瞭解它們。</span><span class="sxs-lookup"><span data-stu-id="634b8-283">Also, starting in PowerShell 3.0, new properties have been added to the object that `Get-Module` returns that make it easier to learn about modules even before they are imported.</span></span> <span data-ttu-id="634b8-284">所有屬性都會在匯入之前填入。</span><span class="sxs-lookup"><span data-stu-id="634b8-284">All properties are populated before importing.</span></span> <span data-ttu-id="634b8-285">其中包括 **ExportedCommands**、 **ExportedCmdlets** 和 **ExportedFunctions** 屬性，這些屬性會列出模組匯出的命令。</span><span class="sxs-lookup"><span data-stu-id="634b8-285">These include the **ExportedCommands**, **ExportedCmdlets** and **ExportedFunctions** properties that list the commands that the module exports.</span></span>

- <span data-ttu-id="634b8-286">**ListAvailable** 參數只會取得格式正確的模組，也就是至少包含一個檔案的資料夾，其基底名稱與模組資料夾的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="634b8-286">The **ListAvailable** parameter gets only well-formed modules, that is, folders that contain at least one file whose base name is the same as the name of the module folder.</span></span> <span data-ttu-id="634b8-287">基底名稱是不含副檔名的名稱。</span><span class="sxs-lookup"><span data-stu-id="634b8-287">The base name is the name without the file name extension.</span></span> <span data-ttu-id="634b8-288">包含具有不同名稱之檔案的資料夾會被視為容器，而非模組。</span><span class="sxs-lookup"><span data-stu-id="634b8-288">Folders that contain files that have different names are considered to be containers, but not modules.</span></span>

  <span data-ttu-id="634b8-289">若要取得實作為 DLL 檔案，但未包含在模組資料夾中的模組，請同時指定 **ListAvailable** 和 **All** 參數。</span><span class="sxs-lookup"><span data-stu-id="634b8-289">To get modules that are implemented as DLL files, but are not enclosed in a module folder, specify both the **ListAvailable** and **All** parameters.</span></span>

- <span data-ttu-id="634b8-290">若要使用 CIM 工作階段功能，遠端電腦必須具備 WS-Management 遠端功能和 Windows Management Instrumentation (WMI)，這是 Microsoft 實作的「通用訊息模型 (CIM)」標準。</span><span class="sxs-lookup"><span data-stu-id="634b8-290">To use the CIM session feature, the remote computer must have WS-Management remoting and Windows Management Instrumentation (WMI), which is the Microsoft implementation of the Common Information Model (CIM) standard.</span></span> <span data-ttu-id="634b8-291">電腦也必須擁有具有相同基本功能的「模組探索」WMI 提供者或替代 WMI 提供者。</span><span class="sxs-lookup"><span data-stu-id="634b8-291">The computer must also have the Module Discovery WMI provider or an alternate WMI provider that has the same basic features.</span></span>

  <span data-ttu-id="634b8-292">您可以在未執行 Windows 作業系統的電腦上，以及在具有 PowerShell 但未啟用 PowerShell 遠端功能的 Windows 電腦上，使用 CIM 會話功能。</span><span class="sxs-lookup"><span data-stu-id="634b8-292">You can use the CIM session feature on computers that are not running the Windows operating system and on Windows computers that have PowerShell, but do not have PowerShell remoting enabled.</span></span>

  <span data-ttu-id="634b8-293">您也可以使用 CIM 參數，從已啟用 PowerShell 遠端功能的電腦取得 CIM 模組。</span><span class="sxs-lookup"><span data-stu-id="634b8-293">You can also use the CIM parameters to get CIM modules from computers that have PowerShell remoting enabled.</span></span> <span data-ttu-id="634b8-294">這包括本機電腦。</span><span class="sxs-lookup"><span data-stu-id="634b8-294">This includes the local computer.</span></span> <span data-ttu-id="634b8-295">當您在本機電腦上建立 CIM 會話時，PowerShell 會使用 DCOM （而不是 WMI）來建立會話。</span><span class="sxs-lookup"><span data-stu-id="634b8-295">When you create a CIM session on the local computer, PowerShell uses DCOM, instead of WMI, to create the session.</span></span>

## <span data-ttu-id="634b8-296">相關連結</span><span class="sxs-lookup"><span data-stu-id="634b8-296">RELATED LINKS</span></span>

[<span data-ttu-id="634b8-297">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="634b8-297">Get-CimSession</span></span>](../CimCmdlets/Get-CimSession.md)

[<span data-ttu-id="634b8-298">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="634b8-298">New-CimSession</span></span>](../CimCmdlets/New-CimSession.md)

[<span data-ttu-id="634b8-299">about_Modules</span><span class="sxs-lookup"><span data-stu-id="634b8-299">about_Modules</span></span>](About/about_Modules.md)

[<span data-ttu-id="634b8-300">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="634b8-300">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="634b8-301">Import-Module</span><span class="sxs-lookup"><span data-stu-id="634b8-301">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="634b8-302">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="634b8-302">Import-PSSession</span></span>](../Microsoft.PowerShell.Utility/Import-PSSession.md)

[<span data-ttu-id="634b8-303">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="634b8-303">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="634b8-304">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="634b8-304">Remove-Module</span></span>](Remove-Module.md)

[<span data-ttu-id="634b8-305">about_PowerShell_Editions</span><span class="sxs-lookup"><span data-stu-id="634b8-305">about_PowerShell_Editions</span></span>](About/about_PowerShell_Editions.md)
