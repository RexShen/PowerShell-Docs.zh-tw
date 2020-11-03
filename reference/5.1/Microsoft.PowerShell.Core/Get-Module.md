---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Module
ms.openlocfilehash: 4098b40c01085b266fa279107e5795b1283705cd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202300"
---
# <span data-ttu-id="288d5-103">Get-Module</span><span class="sxs-lookup"><span data-stu-id="288d5-103">Get-Module</span></span>

## <span data-ttu-id="288d5-104">概要</span><span class="sxs-lookup"><span data-stu-id="288d5-104">SYNOPSIS</span></span>
<span data-ttu-id="288d5-105">取得已匯入或可匯入目前工作階段的模組。</span><span class="sxs-lookup"><span data-stu-id="288d5-105">Gets the modules that have been imported or that can be imported into the current session.</span></span>

## <span data-ttu-id="288d5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="288d5-106">SYNTAX</span></span>

### <span data-ttu-id="288d5-107">已載入 (預設) </span><span class="sxs-lookup"><span data-stu-id="288d5-107">Loaded (Default)</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-All] [<CommonParameters>]
```

### <span data-ttu-id="288d5-108">可用</span><span class="sxs-lookup"><span data-stu-id="288d5-108">Available</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-All] [-ListAvailable]
 [-PSEdition <String>] [-Refresh] [<CommonParameters>]
```

### <span data-ttu-id="288d5-109">PsSession</span><span class="sxs-lookup"><span data-stu-id="288d5-109">PsSession</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-ListAvailable]
 [-PSEdition <String>] [-Refresh] -PSSession <PSSession> [<CommonParameters>]
```

### <span data-ttu-id="288d5-110">CimSession</span><span class="sxs-lookup"><span data-stu-id="288d5-110">CimSession</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-ListAvailable] [-Refresh]
 -CimSession <CimSession> [-CimResourceUri <Uri>] [-CimNamespace <String>] [<CommonParameters>]
```

## <span data-ttu-id="288d5-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="288d5-111">DESCRIPTION</span></span>

<span data-ttu-id="288d5-112">此 `Get-Module` Cmdlet 會取得已匯入或可匯入至 powershell 會話的 powershell 模組。</span><span class="sxs-lookup"><span data-stu-id="288d5-112">The `Get-Module` cmdlet gets the PowerShell modules that have been imported, or that can be imported, into a PowerShell session.</span></span>
<span data-ttu-id="288d5-113">傳回的模組物件 `Get-Module` 包含有關模組的重要資訊。</span><span class="sxs-lookup"><span data-stu-id="288d5-113">The module object that `Get-Module` returns contains valuable information about the module.</span></span>
<span data-ttu-id="288d5-114">您也可以透過管線將模組物件傳送至其他 Cmdlet，例如 `Import-Module` 和 `Remove-Module` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="288d5-114">You can also pipe the module objects to other cmdlets, such as the `Import-Module` and `Remove-Module` cmdlets.</span></span>

<span data-ttu-id="288d5-115">如果沒有參數，會 `Get-Module` 取得已匯入目前會話的模組。</span><span class="sxs-lookup"><span data-stu-id="288d5-115">Without parameters, `Get-Module` gets modules that have been imported into the current session.</span></span>
<span data-ttu-id="288d5-116">若要取得所有已安裝的模組，請指定 **ListAvailable** 參數。</span><span class="sxs-lookup"><span data-stu-id="288d5-116">To get all installed modules, specify the **ListAvailable** parameter.</span></span>

<span data-ttu-id="288d5-117">`Get-Module` 取得模組，但不會將它們匯入。</span><span class="sxs-lookup"><span data-stu-id="288d5-117">`Get-Module` gets modules, but it does not import them.</span></span>
<span data-ttu-id="288d5-118">從 Windows PowerShell 3.0 開始，當您使用模組中的命令時，系統會自動匯入模組，但命令不會 `Get-Module` 觸發自動匯入。</span><span class="sxs-lookup"><span data-stu-id="288d5-118">Starting in Windows PowerShell 3.0, modules are automatically imported when you use a command in the module, but a `Get-Module` command does not trigger an automatic import.</span></span>
<span data-ttu-id="288d5-119">您也可以使用 Cmdlet，將模組匯入到您的會話 `Import-Module` 。</span><span class="sxs-lookup"><span data-stu-id="288d5-119">You can also import the modules into your session by using the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="288d5-120">從 Windows PowerShell 3.0 開始，您可以從遠端會話匯入模組，然後匯入本機會話。</span><span class="sxs-lookup"><span data-stu-id="288d5-120">Starting in Windows PowerShell 3.0, you can get and then, import modules from remote sessions into the local session.</span></span>
<span data-ttu-id="288d5-121">此策略使用 PowerShell 的隱含遠端功能，相當於使用 `Import-PSSession` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="288d5-121">This strategy uses the Implicit Remoting feature of PowerShell and is equivalent to using the `Import-PSSession` cmdlet.</span></span>
<span data-ttu-id="288d5-122">當您在從另一個會話匯入的模組中使用命令時，命令會隱含地在遠端會話中執行。</span><span class="sxs-lookup"><span data-stu-id="288d5-122">When you use commands in modules imported from another session, the commands run implicitly in the remote session.</span></span> <span data-ttu-id="288d5-123">這項功能可讓您從本機會話管理遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="288d5-123">This feature lets you manage the remote computer from the local session.</span></span>

<span data-ttu-id="288d5-124">此外，從 Windows PowerShell 3.0 開始，您可以使用 `Get-Module` 和 `Import-Module` 來取得和匯入通用訊息模型 (CIM) 模組，其中的 Cmdlet 定義于 CMDLET 定義 XML (CDXML) 檔中。</span><span class="sxs-lookup"><span data-stu-id="288d5-124">Also, starting in Windows PowerShell 3.0, you can use `Get-Module` and `Import-Module` to get and import Common Information Model (CIM) modules, in which the cmdlets are defined in Cmdlet Definition XML (CDXML) files.</span></span>
<span data-ttu-id="288d5-125">這項功能可讓您使用在非受控程式碼元件中執行的 Cmdlet，例如以 c + + 撰寫的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="288d5-125">This feature lets you use cmdlets that are implemented in non-managed code assemblies, such as those written in C++.</span></span>

<span data-ttu-id="288d5-126">利用這些新功能， `Get-Module` 和 `Import-Module` Cmdlet 成為管理異類企業的主要工具，包括執行 Windows 作業系統的電腦和執行其他作業系統的電腦。</span><span class="sxs-lookup"><span data-stu-id="288d5-126">With these new features, the `Get-Module` and `Import-Module` cmdlets become primary tools for managing heterogeneous enterprises that include computers that run the Windows operating system and computers that run other operating systems.</span></span>

<span data-ttu-id="288d5-127">若要管理執行 Windows 作業系統且已啟用 PowerShell 和 PowerShell 遠端功能的遠端電腦，請在遠端電腦上建立 **pssession** ，然後使用的 **Pssession** 參數 `Get-Module` 取得 **pssession** 中的 PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="288d5-127">To manage remote computers that run the Windows operating system that have PowerShell and PowerShell remoting enabled, create a **PSSession** on the remote computer and then use the **PSSession** parameter of `Get-Module` to get the PowerShell modules in the **PSSession** .</span></span>
<span data-ttu-id="288d5-128">當您匯入模組，然後在目前的會話中使用匯入的命令時，命令會隱含地在遠端電腦上的 **PSSession** 中執行。</span><span class="sxs-lookup"><span data-stu-id="288d5-128">When you import the modules, and then use the imported commands in the current session, the commands run implicitly in the **PSSession** on the remote computer.</span></span>
<span data-ttu-id="288d5-129">您可以使用這個策略來管理遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="288d5-129">You can use this strategy to manage the remote computer.</span></span>

<span data-ttu-id="288d5-130">您可以使用類似的策略來管理未啟用 PowerShell 遠端功能的電腦。</span><span class="sxs-lookup"><span data-stu-id="288d5-130">You can use a similar strategy to manage computers that do not have PowerShell remoting enabled.</span></span>
<span data-ttu-id="288d5-131">這些包括不是執行 Windows 作業系統的電腦，以及具有 PowerShell 但未啟用 PowerShell 遠端功能的電腦。</span><span class="sxs-lookup"><span data-stu-id="288d5-131">These include computers that are not running the Windows operating system, and computers that have PowerShell but do not have PowerShell remoting enabled.</span></span>

<span data-ttu-id="288d5-132">一開始先在遠端電腦上建立 CIM 會話。</span><span class="sxs-lookup"><span data-stu-id="288d5-132">Start by creating a CIM session on the remote computer.</span></span>
<span data-ttu-id="288d5-133">CIM 會話是連接至遠端電腦上 Windows Management Instrumentation (WMI) 的連線。</span><span class="sxs-lookup"><span data-stu-id="288d5-133">A CIM session is a connection to Windows Management Instrumentation (WMI) on the remote computer.</span></span>
<span data-ttu-id="288d5-134">然後使用的 **CIMSession** 參數 `Get-Module` ，從 CIM 會話取得 cim 模組。</span><span class="sxs-lookup"><span data-stu-id="288d5-134">Then use the **CIMSession** parameter of `Get-Module` to get CIM modules from the CIM session.</span></span>
<span data-ttu-id="288d5-135">當您使用 Cmdlet 匯入 CIM 模組， `Import-Module` 然後執行匯入的命令時，命令會隱含地在遠端電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="288d5-135">When you import a CIM module by using the `Import-Module` cmdlet and then run the imported commands, the commands run implicitly on the remote computer.</span></span>
<span data-ttu-id="288d5-136">您可以使用這個 WMI 和 CIM 策略來管理遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="288d5-136">You can use this WMI and CIM strategy to manage the remote computer.</span></span>

## <span data-ttu-id="288d5-137">範例</span><span class="sxs-lookup"><span data-stu-id="288d5-137">EXAMPLES</span></span>

### <span data-ttu-id="288d5-138">範例1：取得匯入目前會話的模組</span><span class="sxs-lookup"><span data-stu-id="288d5-138">Example 1: Get modules imported into the current session</span></span>

```powershell
Get-Module
```

<span data-ttu-id="288d5-139">此命令取得已匯入目前工作階段的模組。</span><span class="sxs-lookup"><span data-stu-id="288d5-139">This command gets modules that have been imported into the current session.</span></span>

### <span data-ttu-id="288d5-140">範例2：取得已安裝的模組和可用的模組</span><span class="sxs-lookup"><span data-stu-id="288d5-140">Example 2: Get installed modules and available modules</span></span>

```powershell
Get-Module -ListAvailable
```

<span data-ttu-id="288d5-141">此命令取得已安裝於電腦上，且可匯入目前工作階段的模組。</span><span class="sxs-lookup"><span data-stu-id="288d5-141">This command gets the modules that are installed on the computer and can be imported into the current session.</span></span>

<span data-ttu-id="288d5-142">`Get-Module` 在 **$env:P smodulepath** 環境變數所指定的路徑中尋找可用的模組。</span><span class="sxs-lookup"><span data-stu-id="288d5-142">`Get-Module` looks for available modules in the path specified by the **$env:PSModulePath** environment variable.</span></span>
<span data-ttu-id="288d5-143">如需 **PSModulePath** 的詳細資訊，請參閱 [about_Modules](About/about_Modules.md) 和 [about_Environment_Variables](About/about_Environment_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="288d5-143">For more information about **PSModulePath** , see [about_Modules](About/about_Modules.md) and [about_Environment_Variables](About/about_Environment_Variables.md).</span></span>

### <span data-ttu-id="288d5-144">範例3：取得所有匯出的檔案</span><span class="sxs-lookup"><span data-stu-id="288d5-144">Example 3: Get all exported files</span></span>

```powershell
Get-Module -ListAvailable -All
```

<span data-ttu-id="288d5-145">此命令取得所有可用模組的所有匯出檔案。</span><span class="sxs-lookup"><span data-stu-id="288d5-145">This command gets all of the exported files for all available modules.</span></span>

### <span data-ttu-id="288d5-146">範例4：依完整名稱取得模組</span><span class="sxs-lookup"><span data-stu-id="288d5-146">Example 4: Get a module by its fully qualified name</span></span>

```powershell
$FullyQualifedName = @{ModuleName="Microsoft.PowerShell.Management";ModuleVersion="3.1.0.0"}
Get-Module -FullyQualifiedName $FullyQualifedName | Format-Table -Property Name,Version
```

```Output
Name                             Version
----                             -------
Microsoft.PowerShell.Management  3.1.0.0
```

<span data-ttu-id="288d5-147">此命令會使用 **FullyQualifiedName** 參數來指定模組的完整名稱，以取得 **Microsoft. 管理** 模組。</span><span class="sxs-lookup"><span data-stu-id="288d5-147">This command gets the **Microsoft.PowerShell.Management** module by specifying the fully qualified name of the module by using the **FullyQualifiedName** parameter.</span></span>
<span data-ttu-id="288d5-148">命令接著會使用管線將結果傳送至 `Format-Table` Cmdlet，將結果格式化為具有 **Name** 和 **Version** 的資料表做為資料行標題。</span><span class="sxs-lookup"><span data-stu-id="288d5-148">The command then pipes the results into the `Format-Table` cmdlet to format the results as a table with **Name** and **Version** as the column headings.</span></span>

### <span data-ttu-id="288d5-149">範例5：取得模組的屬性</span><span class="sxs-lookup"><span data-stu-id="288d5-149">Example 5: Get properties of a module</span></span>

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

<span data-ttu-id="288d5-150">此命令會取得傳回之 **PSModuleInfo** 物件的屬性 `Get-Module` 。</span><span class="sxs-lookup"><span data-stu-id="288d5-150">This command gets the properties of the **PSModuleInfo** object that `Get-Module` returns.</span></span>
<span data-ttu-id="288d5-151">每個模組檔案都有一個物件。</span><span class="sxs-lookup"><span data-stu-id="288d5-151">There is one object for each module file.</span></span>

<span data-ttu-id="288d5-152">您可以使用屬性來格式化和篩選模組物件。</span><span class="sxs-lookup"><span data-stu-id="288d5-152">You can use the properties to format and filter the module objects.</span></span>
<span data-ttu-id="288d5-153">如需屬性的詳細資訊，請參閱 [PSModuleInfo 屬性](/dotnet/api/system.management.automation.psmoduleinfo)。</span><span class="sxs-lookup"><span data-stu-id="288d5-153">For more information about the properties, see [PSModuleInfo Properties](/dotnet/api/system.management.automation.psmoduleinfo).</span></span>

<span data-ttu-id="288d5-154">輸出包含在 Windows PowerShell 3.0 中引進的新屬性，例如 **Author** 和 **公司名稱** 。</span><span class="sxs-lookup"><span data-stu-id="288d5-154">The output includes the new properties, such as **Author** and **CompanyName** , that were introduced in Windows PowerShell 3.0.</span></span>

### <span data-ttu-id="288d5-155">範例6：依名稱將所有模組分組</span><span class="sxs-lookup"><span data-stu-id="288d5-155">Example 6: Group all modules by name</span></span>

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

<span data-ttu-id="288d5-156">此命令會取得所有模組檔案（已匯入和可用），然後依模組名稱將它們分組。</span><span class="sxs-lookup"><span data-stu-id="288d5-156">This command gets all module files, both imported and available, and then groups them by module name.</span></span> <span data-ttu-id="288d5-157">這可讓您查看每個指令碼正在匯出的模組檔案。</span><span class="sxs-lookup"><span data-stu-id="288d5-157">This lets you see the module files that each script is exporting.</span></span>

### <span data-ttu-id="288d5-158">範例7：顯示模組資訊清單的內容</span><span class="sxs-lookup"><span data-stu-id="288d5-158">Example 7: Display the contents of a module manifest</span></span>

<span data-ttu-id="288d5-159">這些命令會顯示 Windows PowerShell **BitsTransfer** 模組的模組資訊清單內容。</span><span class="sxs-lookup"><span data-stu-id="288d5-159">These commands display the contents of the module manifest for the Windows PowerShell **BitsTransfer** module.</span></span>

<span data-ttu-id="288d5-160">模組不需要有資訊清單檔案。</span><span class="sxs-lookup"><span data-stu-id="288d5-160">Modules are not required to have manifest files.</span></span>
<span data-ttu-id="288d5-161">當他們有資訊清單檔時，資訊清單檔只需要包含版本號碼。</span><span class="sxs-lookup"><span data-stu-id="288d5-161">When they do have a manifest file, the manifest file is required only to include a version number.</span></span>
<span data-ttu-id="288d5-162">不過，資訊清單檔案通常會提供模組、其需求及其內容的實用資訊。</span><span class="sxs-lookup"><span data-stu-id="288d5-162">However, manifest files often provide useful information about a module, its requirements, and its contents.</span></span>

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

<span data-ttu-id="288d5-163">第一個命令取得代表 BitsTransfer 模組的 PSModuleInfo 物件。</span><span class="sxs-lookup"><span data-stu-id="288d5-163">The first command gets the PSModuleInfo object that represents BitsTransfer module.</span></span> <span data-ttu-id="288d5-164">它會將物件儲存在 `$m` 變數中。</span><span class="sxs-lookup"><span data-stu-id="288d5-164">It saves the object in the `$m` variable.</span></span>

<span data-ttu-id="288d5-165">第二個命令會使用 `Get-Content` Cmdlet 取得指定路徑中資訊清單檔的內容。</span><span class="sxs-lookup"><span data-stu-id="288d5-165">The second command uses the `Get-Content` cmdlet to get the content of the manifest file in the specified path.</span></span> <span data-ttu-id="288d5-166">它會使用點標記法，取得儲存在物件的 Path 屬性中的資訊清單檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="288d5-166">It uses dot notation to get the path to the manifest file, which is stored in the Path property of the object.</span></span> <span data-ttu-id="288d5-167">輸出會顯示模組資訊清單的內容。</span><span class="sxs-lookup"><span data-stu-id="288d5-167">The output shows the contents of the module manifest.</span></span>

### <span data-ttu-id="288d5-168">範例8：列出模組目錄中的檔案</span><span class="sxs-lookup"><span data-stu-id="288d5-168">Example 8: List files in module directory</span></span>

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

<span data-ttu-id="288d5-169">此命令會列出模組目錄中的檔案。</span><span class="sxs-lookup"><span data-stu-id="288d5-169">This command lists the files in the directory of the module.</span></span>
<span data-ttu-id="288d5-170">這是在您將模組匯入之前，可用來判斷模組中有哪些內容的另一種方式。</span><span class="sxs-lookup"><span data-stu-id="288d5-170">This is another way to determine what is in a module before you import it.</span></span>
<span data-ttu-id="288d5-171">某些模組可能含有說明檔或描述模組的讀我檔案。</span><span class="sxs-lookup"><span data-stu-id="288d5-171">Some modules might have help files or ReadMe files that describe the module.</span></span>

### <span data-ttu-id="288d5-172">範例9：取得安裝在電腦上的模組</span><span class="sxs-lookup"><span data-stu-id="288d5-172">Example 9: Get modules installed on a computer</span></span>

```powershell
$s = New-PSSession -ComputerName Server01

Get-Module -PSSession $s -ListAvailable
```

<span data-ttu-id="288d5-173">這些命令會取得 Server01 電腦上安裝的模組。</span><span class="sxs-lookup"><span data-stu-id="288d5-173">These commands get the modules that are installed on the Server01 computer.</span></span>

<span data-ttu-id="288d5-174">第一個命令會使用 `New-PSSession` Cmdlet 在 Server01 電腦上建立 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="288d5-174">The first command uses the `New-PSSession` cmdlet to create a **PSSession** on the Server01 computer.</span></span> <span data-ttu-id="288d5-175">命令會將 **PSSession** 儲存在 $s 變數中。</span><span class="sxs-lookup"><span data-stu-id="288d5-175">The command saves the **PSSession** in the $s variable.</span></span>

<span data-ttu-id="288d5-176">第二個命令使用的 **pssession** 和 **ListAvailable** 參數 `Get-Module` ，取得 $s 變數中 **pssession** 內的模組。</span><span class="sxs-lookup"><span data-stu-id="288d5-176">The second command uses the **PSSession** and **ListAvailable** parameters of `Get-Module` to get the modules in the **PSSession** in the $s variable.</span></span>

<span data-ttu-id="288d5-177">如果您使用管線將模組從其他會話傳送至 `Import-Module` Cmdlet，則會 `Import-Module` 使用隱含的遠端功能，將模組匯入目前的會話中。</span><span class="sxs-lookup"><span data-stu-id="288d5-177">If you pipe modules from other sessions to the `Import-Module` cmdlet, `Import-Module` imports the module into the current session by using the implicit remoting feature.</span></span>
<span data-ttu-id="288d5-178">這相當於使用 `Import-PSSession` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="288d5-178">This is equivalent to using the `Import-PSSession` cmdlet.</span></span>
<span data-ttu-id="288d5-179">您可以使用目前工作階段中模組的 Cmdlet，但是，使用這些 Cmdlet 的命令實際上會執行遠端工作階段。</span><span class="sxs-lookup"><span data-stu-id="288d5-179">You can use the cmdlets from the module in the current session, but commands that use these cmdlets actually run the remote session.</span></span>
<span data-ttu-id="288d5-180">如需詳細資訊，請參閱 [`Import-Module`](Import-Module.md) 和 [`Import-PSSession`](../Microsoft.PowerShell.Utility/Import-PSSession.md)。</span><span class="sxs-lookup"><span data-stu-id="288d5-180">For more information, see [`Import-Module`](Import-Module.md) and [`Import-PSSession`](../Microsoft.PowerShell.Utility/Import-PSSession.md).</span></span>

### <span data-ttu-id="288d5-181">範例10：管理未執行 Windows 作業系統的電腦</span><span class="sxs-lookup"><span data-stu-id="288d5-181">Example 10: Manage a computer that does not run the Windows operating system</span></span>

<span data-ttu-id="288d5-182">此範例中的命令可讓您管理不是執行 Windows 作業系統之遠端電腦的儲存系統。</span><span class="sxs-lookup"><span data-stu-id="288d5-182">The commands in this example enable you to manage the storage systems of a remote computer that is not running the Windows operating system.</span></span>
<span data-ttu-id="288d5-183">在這個範例中，因為電腦的系統管理員已安裝「模組探索」WMI 提供者，所以 CIM 命令可以使用專為提供者設計的預設值。</span><span class="sxs-lookup"><span data-stu-id="288d5-183">In this example, because the administrator of the computer has installed the Module Discovery WMI provider, the CIM commands can use the default values, which are designed for the provider.</span></span>

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

<span data-ttu-id="288d5-184">第一個命令會使用 `New-CimSession` Cmdlet 在 RSDGF03 遠端電腦上建立會話。</span><span class="sxs-lookup"><span data-stu-id="288d5-184">The first command uses the `New-CimSession` cmdlet to create a session on the RSDGF03 remote computer.</span></span> <span data-ttu-id="288d5-185">工作階段會連線遠端電腦上的 WMI。</span><span class="sxs-lookup"><span data-stu-id="288d5-185">The session connects to WMI on the remote computer.</span></span> <span data-ttu-id="288d5-186">此命令會將 CIM 會話儲存在 `$cs` 變數中。</span><span class="sxs-lookup"><span data-stu-id="288d5-186">The command saves the CIM session in the `$cs` variable.</span></span>

<span data-ttu-id="288d5-187">第二個命令會使用變數中的 CIM 會話 `$cs` ，在 `Get-Module` RSDGF03 電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="288d5-187">The second command uses the CIM session in the `$cs` variable to run a `Get-Module` command on the RSDGF03 computer.</span></span> <span data-ttu-id="288d5-188">命令使用 Name 參數指定 Storage 模組。</span><span class="sxs-lookup"><span data-stu-id="288d5-188">The command uses the Name parameter to specify the Storage module.</span></span> <span data-ttu-id="288d5-189">命令使用管線運算子 (|) 將儲存體模組傳送至 `Import-Module` Cmdlet，以將它匯入本機會話。</span><span class="sxs-lookup"><span data-stu-id="288d5-189">The command uses a pipeline operator (|) to send the Storage module to the `Import-Module` cmdlet, which imports it into the local session.</span></span>

<span data-ttu-id="288d5-190">第三個命令會在 `Get-Command` `Get-Disk` 儲存體模組中的命令上執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="288d5-190">The third command runs the `Get-Command` cmdlet on the `Get-Disk` command in the Storage module.</span></span>
<span data-ttu-id="288d5-191">當您將 CIM 模組匯入本機會話時，PowerShell 會將代表 CIM 模組的 CDXML 檔案轉換成 PowerShell 腳本，這會顯示為本機會話中的函式。</span><span class="sxs-lookup"><span data-stu-id="288d5-191">When you import a CIM module into the local session, PowerShell converts the CDXML files that represent the CIM module into PowerShell scripts, which appear as functions in the local session.</span></span>

<span data-ttu-id="288d5-192">第四個命令會執行 `Get-Disk` 命令。</span><span class="sxs-lookup"><span data-stu-id="288d5-192">The fourth command runs the `Get-Disk` command.</span></span> <span data-ttu-id="288d5-193">雖然命令是在本機工作階段中輸入，但是它會在匯入它的遠端電腦上隱含執行。</span><span class="sxs-lookup"><span data-stu-id="288d5-193">Although the command is typed in the local session, it runs implicitly on the remote computer from which it was imported.</span></span> <span data-ttu-id="288d5-194">命令會從遠端電腦取得物件，並將其傳回本機工作階段。</span><span class="sxs-lookup"><span data-stu-id="288d5-194">The command gets objects from the remote computer and returns them to the local session.</span></span>

## <span data-ttu-id="288d5-195">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="288d5-195">PARAMETERS</span></span>

### <span data-ttu-id="288d5-196">-All</span><span class="sxs-lookup"><span data-stu-id="288d5-196">-All</span></span>

<span data-ttu-id="288d5-197">指出此 Cmdlet 會取得每個模組資料夾中的所有模組，包括嵌套模組、資訊清單 ( .psd1) 檔案、腳本模組 (. .psm1) 檔案，以及二進位模組 ( .dll) 檔。</span><span class="sxs-lookup"><span data-stu-id="288d5-197">Indicates that this cmdlet gets all modules in each module folder, including nested modules, manifest (.psd1) files, script module (.psm1) files, and binary module (.dll) files.</span></span>
<span data-ttu-id="288d5-198">如果沒有這個參數，則 `Get-Module` 只會取得每個模組資料夾中的預設模組。</span><span class="sxs-lookup"><span data-stu-id="288d5-198">Without this parameter, `Get-Module` gets only the default module in each module folder.</span></span>

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

### <span data-ttu-id="288d5-199">-CimNamespace</span><span class="sxs-lookup"><span data-stu-id="288d5-199">-CimNamespace</span></span>

<span data-ttu-id="288d5-200">指定公開 CIM 模組的替代 CIM 提供者命名空間。</span><span class="sxs-lookup"><span data-stu-id="288d5-200">Specifies the namespace of an alternate CIM provider that exposes CIM modules.</span></span>
<span data-ttu-id="288d5-201">預設值為「模組探索」WMI 提供者的命名空間。</span><span class="sxs-lookup"><span data-stu-id="288d5-201">The default value is the namespace of the Module Discovery WMI provider.</span></span>

<span data-ttu-id="288d5-202">使用此參數從不是執行 Windows 作業系統的電腦和裝置取得 CIM 模組。</span><span class="sxs-lookup"><span data-stu-id="288d5-202">Use this parameter to get CIM modules from computers and devices that are not running the Windows operating system.</span></span>

<span data-ttu-id="288d5-203">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="288d5-203">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="288d5-204">-CimResourceUri</span><span class="sxs-lookup"><span data-stu-id="288d5-204">-CimResourceUri</span></span>

<span data-ttu-id="288d5-205">指定 CIM 模組的替代位置。</span><span class="sxs-lookup"><span data-stu-id="288d5-205">Specifies an alternate location for CIM modules.</span></span>
<span data-ttu-id="288d5-206">預設值為遠端電腦上「模組探索」 WMI 提供者的資源 URI。</span><span class="sxs-lookup"><span data-stu-id="288d5-206">The default value is the resource URI of the Module Discovery WMI provider on the remote computer.</span></span>

<span data-ttu-id="288d5-207">使用此參數從不是執行 Windows 作業系統的電腦和裝置取得 CIM 模組。</span><span class="sxs-lookup"><span data-stu-id="288d5-207">Use this parameter to get CIM modules from computers and devices that are not running the Windows operating system.</span></span>

<span data-ttu-id="288d5-208">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="288d5-208">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="288d5-209">-CimSession</span><span class="sxs-lookup"><span data-stu-id="288d5-209">-CimSession</span></span>

<span data-ttu-id="288d5-210">指定遠端電腦上的 CIM 工作階段。</span><span class="sxs-lookup"><span data-stu-id="288d5-210">Specifies a CIM session on the remote computer.</span></span>
<span data-ttu-id="288d5-211">輸入包含 CIM 會話的變數，或輸入可取得 CIM 會話的命令，例如 [CimSession](/powershell/module/cimcmdlets/get-cimsession) 命令。</span><span class="sxs-lookup"><span data-stu-id="288d5-211">Enter a variable that contains the CIM session or a command that gets the CIM session, such as a [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) command.</span></span>

<span data-ttu-id="288d5-212">`Get-Module` 使用 CIM 會話連接從遠端電腦取得模組。</span><span class="sxs-lookup"><span data-stu-id="288d5-212">`Get-Module` uses the CIM session connection to get modules from the remote computer.</span></span>
<span data-ttu-id="288d5-213">當您使用 Cmdlet 匯入模組 `Import-Module` ，並在目前的會話中使用匯入模組的命令時，命令實際上會在遠端電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="288d5-213">When you import the module by using the `Import-Module` cmdlet and use the commands from the imported module in the current session, the commands actually run on the remote computer.</span></span>

<span data-ttu-id="288d5-214">您可以使用此參數從不是執行 Windows 作業系統的電腦和裝置，以及具有 PowerShell 但未啟用 PowerShell 遠端處理的電腦取得模組。</span><span class="sxs-lookup"><span data-stu-id="288d5-214">You can use this parameter to get modules from computers and devices that are not running the Windows operating system, and computers that have PowerShell, but do not have PowerShell remoting enabled.</span></span>

<span data-ttu-id="288d5-215">**CimSession** 參數會取得 **CIMSession** 中的所有模組。</span><span class="sxs-lookup"><span data-stu-id="288d5-215">The **CimSession** parameter gets all modules in the **CIMSession** .</span></span>
<span data-ttu-id="288d5-216">不過，您可以只匯入 CIM 型和「Cmdlet 定義 XML (CDXML)」型模組。</span><span class="sxs-lookup"><span data-stu-id="288d5-216">However, you can import only CIM-based and Cmdlet Definition XML (CDXML)-based modules.</span></span>

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

### <span data-ttu-id="288d5-217">-FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="288d5-217">-FullyQualifiedName</span></span>

<span data-ttu-id="288d5-218">以 **ModuleSpecification** 物件的形式指定模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="288d5-218">Specifies names of modules in the form of **ModuleSpecification** objects.</span></span>
<span data-ttu-id="288d5-219">這些物件會在 MSDN library 中 [ModuleSpecification (表的「雜湊表) ](https://msdn.microsoft.com/library/jj136290) 的「備註」一節中描述。</span><span class="sxs-lookup"><span data-stu-id="288d5-219">These objects are described in the Remarks section of [ModuleSpecification Constructor (Hashtable)](https://msdn.microsoft.com/library/jj136290) in the MSDN library.</span></span>
<span data-ttu-id="288d5-220">例如， **FullyQualifiedName** 參數會接受以下列格式指定的模組名稱：</span><span class="sxs-lookup"><span data-stu-id="288d5-220">For example, the **FullyQualifiedName** parameter accepts a module name that is specified in the following formats:</span></span>

- <span data-ttu-id="288d5-221">@ {ModuleName = "modulename";ModuleVersion = "version_number"}</span><span class="sxs-lookup"><span data-stu-id="288d5-221">@{ModuleName = "modulename"; ModuleVersion = "version_number"}</span></span>
- <span data-ttu-id="288d5-222">@ {ModuleName = "modulename";ModuleVersion = "version_number";Guid = "GUID"}</span><span class="sxs-lookup"><span data-stu-id="288d5-222">@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}</span></span>

<span data-ttu-id="288d5-223">**ModuleName** 和 **ModuleVersion** 是必要參數，但 **Guid** 是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="288d5-223">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="288d5-224">您無法在與 **Name** 參數相同的命令中指定 **FullyQualifiedName** 參數。</span><span class="sxs-lookup"><span data-stu-id="288d5-224">You cannot specify the **FullyQualifiedName** parameter in the same command as a **Name** parameter.</span></span>

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

### <span data-ttu-id="288d5-225">-ListAvailable</span><span class="sxs-lookup"><span data-stu-id="288d5-225">-ListAvailable</span></span>

<span data-ttu-id="288d5-226">指出此 Cmdlet 會取得所有已安裝的模組。</span><span class="sxs-lookup"><span data-stu-id="288d5-226">Indicates that this cmdlet gets all installed modules.</span></span>
<span data-ttu-id="288d5-227">`Get-Module` 取得 **PSModulePath** 環境變數所列路徑中的模組。</span><span class="sxs-lookup"><span data-stu-id="288d5-227">`Get-Module` gets modules in paths listed in the **PSModulePath** environment variable.</span></span>
<span data-ttu-id="288d5-228">如果沒有這個參數，則 `Get-Module` 只會取得 **PSModulePath** 環境變數中所列的模組，以及在目前的會話中載入的模組。</span><span class="sxs-lookup"><span data-stu-id="288d5-228">Without this parameter, `Get-Module` gets only the modules that are both listed in the **PSModulePath** environment variable, and that are loaded in the current session.</span></span>
<span data-ttu-id="288d5-229">**ListAvailable** 不會傳回 **PSModulePath** 環境變數中找不到的模組相關資訊，即使這些模組已載入目前工作階段也一樣。</span><span class="sxs-lookup"><span data-stu-id="288d5-229">**ListAvailable** does not return information about modules that are not found in the **PSModulePath** environment variable, even if those modules are loaded in the current session.</span></span>

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

### <span data-ttu-id="288d5-230">-Name</span><span class="sxs-lookup"><span data-stu-id="288d5-230">-Name</span></span>

<span data-ttu-id="288d5-231">指定此 Cmdlet 取得之模組的名稱或名稱模式。</span><span class="sxs-lookup"><span data-stu-id="288d5-231">Specifies names or name patterns of modules that this cmdlet gets.</span></span>
<span data-ttu-id="288d5-232">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="288d5-232">Wildcard characters are permitted.</span></span>
<span data-ttu-id="288d5-233">您也可以透過管線將名稱傳送至 `Get-Module` 。</span><span class="sxs-lookup"><span data-stu-id="288d5-233">You can also pipe the names to `Get-Module`.</span></span>
<span data-ttu-id="288d5-234">您無法在與 **Name** 參數相同的命令中指定 **FullyQualifiedName** 參數。</span><span class="sxs-lookup"><span data-stu-id="288d5-234">You cannot specify the **FullyQualifiedName** parameter in the same command as a **Name** parameter.</span></span>

<span data-ttu-id="288d5-235">**名稱** 不能接受模組 GUID 做為值。</span><span class="sxs-lookup"><span data-stu-id="288d5-235">**Name** cannot accept a module GUID as a value.</span></span>
<span data-ttu-id="288d5-236">若要藉由指定 GUID 來傳回模組，請改用 **FullyQualifiedName** 。</span><span class="sxs-lookup"><span data-stu-id="288d5-236">To return modules by specifying a GUID, use **FullyQualifiedName** instead.</span></span>

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

### <span data-ttu-id="288d5-237">-PSEdition</span><span class="sxs-lookup"><span data-stu-id="288d5-237">-PSEdition</span></span>

<span data-ttu-id="288d5-238">取得支援指定 PowerShell 版本的模組。</span><span class="sxs-lookup"><span data-stu-id="288d5-238">Gets the modules that support specified edition of PowerShell.</span></span>

<span data-ttu-id="288d5-239">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="288d5-239">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="288d5-240">桌面</span><span class="sxs-lookup"><span data-stu-id="288d5-240">Desktop</span></span>
- <span data-ttu-id="288d5-241">核心</span><span class="sxs-lookup"><span data-stu-id="288d5-241">Core</span></span>

<span data-ttu-id="288d5-242">Get-Module Cmdlet 會針對指定的值檢查 **PSModuleInfo** 物件的 **CompatiblePSEditions** 屬性，並只傳回已設定的模組。</span><span class="sxs-lookup"><span data-stu-id="288d5-242">The Get-Module cmdlet checks **CompatiblePSEditions** property of **PSModuleInfo** object for the specified value and returns only those modules that have it set.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="288d5-243">**Desktop Edition：** 建置在 .NET Framework 上，並與目標為完整版 Windows (Server Core 和 Windows Desktop 等) 上執行之 PowerShell 版本的指令碼和模組相容。</span><span class="sxs-lookup"><span data-stu-id="288d5-243">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
> - <span data-ttu-id="288d5-244">**Core Edition：** 建置在 .NET Core 上，並與目標為縮減版 Windows (Nano Server 和 Windows IoT 等) 上執行之 PowerShell 版本的指令碼和模組相容。</span><span class="sxs-lookup"><span data-stu-id="288d5-244">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

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

### <span data-ttu-id="288d5-245">-PSSession</span><span class="sxs-lookup"><span data-stu-id="288d5-245">-PSSession</span></span>

<span data-ttu-id="288d5-246">取得指定之使用者管理的 PowerShell 會話中的模組 ( **PSSession** ) 。</span><span class="sxs-lookup"><span data-stu-id="288d5-246">Gets the modules in the specified user-managed PowerShell session ( **PSSession** ).</span></span>
<span data-ttu-id="288d5-247">輸入包含會話的變數、可取得會話的命令（例如 `Get-PSSession` 命令）或建立會話的命令（例如 `New-PSSession` 命令）。</span><span class="sxs-lookup"><span data-stu-id="288d5-247">Enter a variable that contains the session, a command that gets the session, such as a `Get-PSSession` command, or a command that creates the session, such as a `New-PSSession` command.</span></span>

<span data-ttu-id="288d5-248">當會話連線到遠端電腦時，您必須指定 **ListAvailable** 參數。</span><span class="sxs-lookup"><span data-stu-id="288d5-248">When the session is connected to a remote computer, you must specify the **ListAvailable** parameter.</span></span>

<span data-ttu-id="288d5-249">`Get-Module`使用 **pssession** 參數的命令相當於使用 `Invoke-Command` Cmdlet `Get-Module -ListAvailable` 在 **PSSession** 中執行命令。</span><span class="sxs-lookup"><span data-stu-id="288d5-249">A `Get-Module` command that uses the **PSSession** parameter is equivalent to using the `Invoke-Command` cmdlet to run a `Get-Module -ListAvailable` command in a **PSSession** .</span></span>

<span data-ttu-id="288d5-250">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="288d5-250">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="288d5-251">-Refresh</span><span class="sxs-lookup"><span data-stu-id="288d5-251">-Refresh</span></span>

<span data-ttu-id="288d5-252">指出此 Cmdlet 會重新整理已安裝命令的快取。</span><span class="sxs-lookup"><span data-stu-id="288d5-252">Indicates that this cmdlet refreshes the cache of installed commands.</span></span>
<span data-ttu-id="288d5-253">當工作階段啟動時，即會建立命令快取。</span><span class="sxs-lookup"><span data-stu-id="288d5-253">The command cache is created when the session starts.</span></span>
<span data-ttu-id="288d5-254">它可讓 `Get-Command` Cmdlet 從未匯入會話的模組中取得命令。</span><span class="sxs-lookup"><span data-stu-id="288d5-254">It enables the `Get-Command` cmdlet to get commands from modules that are not imported into the session.</span></span>

<span data-ttu-id="288d5-255">這個參數是專為開發和測試案例所設計，在這類案例中，模組的內容會在工作階段開始後變更。</span><span class="sxs-lookup"><span data-stu-id="288d5-255">This parameter is designed for development and testing scenarios in which the contents of modules have changed since the session started.</span></span>

<span data-ttu-id="288d5-256">當您在命令中指定 **Refresh** 參數時，必須指定 **ListAvailable** 。</span><span class="sxs-lookup"><span data-stu-id="288d5-256">When you specify the **Refresh** parameter in a command, you must specify **ListAvailable** .</span></span>

<span data-ttu-id="288d5-257">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="288d5-257">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PsSession, Available, CimSession
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="288d5-258">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="288d5-258">CommonParameters</span></span>

<span data-ttu-id="288d5-259">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="288d5-259">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="288d5-260">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="288d5-260">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="288d5-261">輸入</span><span class="sxs-lookup"><span data-stu-id="288d5-261">INPUTS</span></span>

### <span data-ttu-id="288d5-262">System.String</span><span class="sxs-lookup"><span data-stu-id="288d5-262">System.String</span></span>

<span data-ttu-id="288d5-263">您可以透過管線將模組名稱傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="288d5-263">You can pipe module names to this cmdlet.</span></span>

## <span data-ttu-id="288d5-264">輸出</span><span class="sxs-lookup"><span data-stu-id="288d5-264">OUTPUTS</span></span>

### <span data-ttu-id="288d5-265">System.Management.Automation.PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="288d5-265">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="288d5-266">此 Cmdlet 會傳回代表模組的物件。</span><span class="sxs-lookup"><span data-stu-id="288d5-266">This cmdlet returns objects that represent modules.</span></span>
<span data-ttu-id="288d5-267">當您指定 **ListAvailable** 參數時， `Get-Module` 會傳回 **ModuleInfoGrouping** 物件，這是具有相同屬性和方法的 **PSModuleInfo** 物件類型。</span><span class="sxs-lookup"><span data-stu-id="288d5-267">When you specify the **ListAvailable** parameter, `Get-Module` returns a **ModuleInfoGrouping** object, which is a type of **PSModuleInfo** object that has the same properties and methods.</span></span>

## <span data-ttu-id="288d5-268">注意</span><span class="sxs-lookup"><span data-stu-id="288d5-268">NOTES</span></span>

- <span data-ttu-id="288d5-269">從 Windows PowerShell 3.0 開始，PowerShell 隨附的核心命令會封裝在模組中。</span><span class="sxs-lookup"><span data-stu-id="288d5-269">Beginning in Windows PowerShell 3.0, the core commands that are included in PowerShell are packaged in modules.</span></span> <span data-ttu-id="288d5-270">例外狀況是 **PSSnapin** ) 的嵌入式管理單元 **(。**</span><span class="sxs-lookup"><span data-stu-id="288d5-270">The exception is **Microsoft.PowerShell.Core** , which is a snap-in ( **PSSnapin** ).</span></span> <span data-ttu-id="288d5-271">依照預設，只會新增 **Microsoft.PowerShell.Core** 嵌入式管理單元至工作階段。</span><span class="sxs-lookup"><span data-stu-id="288d5-271">By default, only the **Microsoft.PowerShell.Core** snap-in is added to the session.</span></span>
<span data-ttu-id="288d5-272">模組會在第一次使用時自動匯入，而您可以使用 `Import-Module` Cmdlet 將它們匯入。</span><span class="sxs-lookup"><span data-stu-id="288d5-272">Modules are imported automatically on first use and you can use the `Import-Module` cmdlet to import them.</span></span>
- <span data-ttu-id="288d5-273">從 Windows PowerShell 3.0 開始，隨 PowerShell 安裝的核心命令會封裝在模組中。</span><span class="sxs-lookup"><span data-stu-id="288d5-273">Starting in Windows PowerShell 3.0, the core commands that are installed with PowerShell are packaged in modules.</span></span> <span data-ttu-id="288d5-274">在 Windows PowerShell 2.0，以及在較新版本的 PowerShell 中建立舊版會話的主機程式中，會將核心命令封裝在嵌入式管理單元中， ( **PSSnapins** ) 。</span><span class="sxs-lookup"><span data-stu-id="288d5-274">In Windows PowerShell 2.0, and in host programs that create older-style sessions in later versions of PowerShell, the core commands are packaged in snap-ins ( **PSSnapins** ).</span></span> <span data-ttu-id="288d5-275">**Microsoft.PowerShell.Core** 是一個例外，它一律是一個嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="288d5-275">The exception is **Microsoft.PowerShell.Core** , which is always a snap-in.</span></span> <span data-ttu-id="288d5-276">此外，遠端會話（例如由 Cmdlet 啟動的會話） `New-PSSession` 都是包含核心嵌入式管理單元的較舊樣式會話。</span><span class="sxs-lookup"><span data-stu-id="288d5-276">Also, remote sessions, such as those started by the `New-PSSession` cmdlet, are older-style sessions that include core snap-ins.</span></span>

  <span data-ttu-id="288d5-277">如需有關使用核心模組建立較新樣式會話的 **CreateDefault2** 方法的詳細資訊，請參閱 MSDN library 中的 [CreateDefault2 方法](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2) 。</span><span class="sxs-lookup"><span data-stu-id="288d5-277">For information about the **CreateDefault2** method that creates newer-style sessions with core modules, see [CreateDefault2 Method](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2) in the MSDN library.</span></span>

- <span data-ttu-id="288d5-278">`Get-Module` 只會取得位置中的模組，這些位置會儲存在 **PSModulePath** 環境變數的值 ($Env:P smodulepath) 中。</span><span class="sxs-lookup"><span data-stu-id="288d5-278">`Get-Module` only gets modules in locations that are stored in the value of the **PSModulePath** environment variable ($env:PSModulePath).</span></span> <span data-ttu-id="288d5-279">您可以使用 Cmdlet 的 **Path** 參數 `Import-Module` ，在其他位置匯入模組，但您無法使用 `Get-Module` Cmdlet 來取得它們。</span><span class="sxs-lookup"><span data-stu-id="288d5-279">You can use the **Path** parameter of the `Import-Module` cmdlet to import modules in other locations, but you cannot use the `Get-Module` cmdlet to get them.</span></span>
- <span data-ttu-id="288d5-280">此外，從 PowerShell 3.0 開始，已在傳回的物件中加入新的屬性，讓您可以在匯 `Get-Module` 入模組之前，更輕鬆地瞭解它們。</span><span class="sxs-lookup"><span data-stu-id="288d5-280">Also, starting in PowerShell 3.0, new properties have been added to the object that `Get-Module` returns that make it easier to learn about modules even before they are imported.</span></span> <span data-ttu-id="288d5-281">所有屬性都會在匯入之前填入。</span><span class="sxs-lookup"><span data-stu-id="288d5-281">All properties are populated before importing.</span></span> <span data-ttu-id="288d5-282">其中包括 **ExportedCommands** 、 **ExportedCmdlets** 和 **ExportedFunctions** 屬性，這些屬性會列出模組匯出的命令。</span><span class="sxs-lookup"><span data-stu-id="288d5-282">These include the **ExportedCommands** , **ExportedCmdlets** and **ExportedFunctions** properties that list the commands that the module exports.</span></span>
- <span data-ttu-id="288d5-283">**ListAvailable** 參數只會取得格式正確的模組，也就是至少包含一個檔案的資料夾，其基底名稱與模組資料夾的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="288d5-283">The **ListAvailable** parameter gets only well-formed modules, that is, folders that contain at least one file whose base name is the same as the name of the module folder.</span></span> <span data-ttu-id="288d5-284">基底名稱是不含副檔名的名稱。</span><span class="sxs-lookup"><span data-stu-id="288d5-284">The base name is the name without the file name extension.</span></span> <span data-ttu-id="288d5-285">包含具有不同名稱之檔案的資料夾會被視為容器，而非模組。</span><span class="sxs-lookup"><span data-stu-id="288d5-285">Folders that contain files that have different names are considered to be containers, but not modules.</span></span>

  <span data-ttu-id="288d5-286">若要取得實作為 .dll 檔案，但未包含在模組資料夾中的模組，請同時指定 **ListAvailable** 和 **All** 參數。</span><span class="sxs-lookup"><span data-stu-id="288d5-286">To get modules that are implemented as .dll files, but are not enclosed in a module folder, specify both the **ListAvailable** and **All** parameters.</span></span>

- <span data-ttu-id="288d5-287">若要使用 CIM 工作階段功能，遠端電腦必須具備 WS-Management 遠端功能和 Windows Management Instrumentation (WMI)，這是 Microsoft 實作的「通用訊息模型 (CIM)」標準。</span><span class="sxs-lookup"><span data-stu-id="288d5-287">To use the CIM session feature, the remote computer must have WS-Management remoting and Windows Management Instrumentation (WMI), which is the Microsoft implementation of the Common Information Model (CIM) standard.</span></span> <span data-ttu-id="288d5-288">電腦也必須擁有具有相同基本功能的「模組探索」WMI 提供者或替代 WMI 提供者。</span><span class="sxs-lookup"><span data-stu-id="288d5-288">The computer must also have the Module Discovery WMI provider or an alternate WMI provider that has the same basic features.</span></span>

  <span data-ttu-id="288d5-289">您可以在未執行 Windows 作業系統的電腦上，以及在具有 PowerShell 但未啟用 PowerShell 遠端功能的 Windows 電腦上，使用 CIM 會話功能。</span><span class="sxs-lookup"><span data-stu-id="288d5-289">You can use the CIM session feature on computers that are not running the Windows operating system and on Windows computers that have PowerShell, but do not have PowerShell remoting enabled.</span></span>

  <span data-ttu-id="288d5-290">您也可以使用 CIM 參數，從已啟用 PowerShell 遠端功能的電腦取得 CIM 模組。</span><span class="sxs-lookup"><span data-stu-id="288d5-290">You can also use the CIM parameters to get CIM modules from computers that have PowerShell remoting enabled.</span></span> <span data-ttu-id="288d5-291">這包括本機電腦。</span><span class="sxs-lookup"><span data-stu-id="288d5-291">This includes the local computer.</span></span>
<span data-ttu-id="288d5-292">當您在本機電腦上建立 CIM 會話時，PowerShell 會使用 DCOM （而不是 WMI）來建立會話。</span><span class="sxs-lookup"><span data-stu-id="288d5-292">When you create a CIM session on the local computer, PowerShell uses DCOM, instead of WMI, to create the session.</span></span>

## <span data-ttu-id="288d5-293">相關連結</span><span class="sxs-lookup"><span data-stu-id="288d5-293">RELATED LINKS</span></span>

[<span data-ttu-id="288d5-294">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="288d5-294">Get-CimSession</span></span>](../CimCmdlets/Get-CimSession.md)

[<span data-ttu-id="288d5-295">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="288d5-295">New-CimSession</span></span>](../CimCmdlets/New-CimSession.md)

[<span data-ttu-id="288d5-296">about_Modules</span><span class="sxs-lookup"><span data-stu-id="288d5-296">about_Modules</span></span>](About/about_Modules.md)

[<span data-ttu-id="288d5-297">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="288d5-297">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="288d5-298">Import-Module</span><span class="sxs-lookup"><span data-stu-id="288d5-298">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="288d5-299">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="288d5-299">Import-PSSession</span></span>](../Microsoft.PowerShell.Utility/Import-PSSession.md)

[<span data-ttu-id="288d5-300">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="288d5-300">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="288d5-301">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="288d5-301">Remove-Module</span></span>](Remove-Module.md)
