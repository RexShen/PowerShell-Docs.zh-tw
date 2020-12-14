---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/import-module?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Module
ms.openlocfilehash: 218a4cb447c85a7362efebe9b50a917703cccc35
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564440"
---
# <span data-ttu-id="9d428-102">Import-Module</span><span class="sxs-lookup"><span data-stu-id="9d428-102">Import-Module</span></span>

## <span data-ttu-id="9d428-103">概要</span><span class="sxs-lookup"><span data-stu-id="9d428-103">SYNOPSIS</span></span>
<span data-ttu-id="9d428-104">將模組新增到目前的工作階段。</span><span class="sxs-lookup"><span data-stu-id="9d428-104">Adds modules to the current session.</span></span>

## <span data-ttu-id="9d428-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9d428-105">SYNTAX</span></span>

### <span data-ttu-id="9d428-106">Name (預設值)</span><span class="sxs-lookup"><span data-stu-id="9d428-106">Name (Default)</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>]  [<CommonParameters>]
```

### <span data-ttu-id="9d428-107">PSSession</span><span class="sxs-lookup"><span data-stu-id="9d428-107">PSSession</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -PSSession <PSSession>  [<CommonParameters>]
```

### <span data-ttu-id="9d428-108">CimSession</span><span class="sxs-lookup"><span data-stu-id="9d428-108">CimSession</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -CimSession <CimSession> [-CimResourceUri <Uri>] [-CimNamespace <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="9d428-109">UseWindowsPowerShell</span><span class="sxs-lookup"><span data-stu-id="9d428-109">UseWindowsPowerShell</span></span>

```
Import-Module [-Name] <string[]> -UseWindowsPowerShell [-Global] [-Prefix <string>]
 [-Function <string[]>] [-Cmdlet <string[]>] [-Variable <string[]>] [-Alias <string[]>]
 [-Force] [-PassThru] [-AsCustomObject] [-MinimumVersion <version>] [-MaximumVersion <string>]
 [-RequiredVersion <version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <string>] [<CommonParameters>]
```

### <span data-ttu-id="9d428-110">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="9d428-110">FullyQualifiedName</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-FullyQualifiedName] <ModuleSpecification[]>
 [-Function <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force]
 [-SkipEditionCheck] [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>]  [<CommonParameters>]
```

### <span data-ttu-id="9d428-111">FullyQualifiedNameAndPSSession</span><span class="sxs-lookup"><span data-stu-id="9d428-111">FullyQualifiedNameAndPSSession</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-FullyQualifiedName] <ModuleSpecification[]>
 [-Function <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force]
 [-SkipEditionCheck] [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>] -PSSession <PSSession>  [<CommonParameters>]
```

### <span data-ttu-id="9d428-112">FullyQualifiedNameAndUseWindowsPowerShell</span><span class="sxs-lookup"><span data-stu-id="9d428-112">FullyQualifiedNameAndUseWindowsPowerShell</span></span>

```
Import-Module [-FullyQualifiedName] <ModuleSpecification[]> -UseWindowsPowerShell [-Global]
 [-Prefix <string>] [-Function <string[]>] [-Cmdlet <string[]>] [-Variable <string[]>]
 [-Alias <string[]>] [-Force] [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>]
 [-DisableNameChecking] [-NoClobber] [-Scope <string>] [<CommonParameters>]
```

### <span data-ttu-id="9d428-113">組件</span><span class="sxs-lookup"><span data-stu-id="9d428-113">Assembly</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Assembly] <Assembly[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>]  [<CommonParameters>]
```

### <span data-ttu-id="9d428-114">ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="9d428-114">ModuleInfo</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Function <String[]>] [-Cmdlet <String[]>]
 [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck] [-PassThru]
 [-AsCustomObject] [-ModuleInfo] <PSModuleInfo[]> [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>]  [<CommonParameters>]
```

## <span data-ttu-id="9d428-115">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9d428-115">DESCRIPTION</span></span>

<span data-ttu-id="9d428-116">`Import-Module`Cmdlet 會將一或多個模組新增到目前的會話。</span><span class="sxs-lookup"><span data-stu-id="9d428-116">The `Import-Module` cmdlet adds one or more modules to the current session.</span></span> <span data-ttu-id="9d428-117">從 PowerShell 3.0 開始，當您使用模組中的任何命令或提供者時，已安裝的模組會自動匯入至會話。</span><span class="sxs-lookup"><span data-stu-id="9d428-117">Starting in PowerShell 3.0, installed modules are automatically imported to the session when you use any commands or providers in the module.</span></span> <span data-ttu-id="9d428-118">不過，您仍然可以使用 `Import-Module` 命令匯入模組。</span><span class="sxs-lookup"><span data-stu-id="9d428-118">However, you can still use the `Import-Module` command to import a module.</span></span>
<span data-ttu-id="9d428-119">您可以使用喜好設定變數停用自動匯入模組 `$PSModuleAutoloadingPreference` 。</span><span class="sxs-lookup"><span data-stu-id="9d428-119">You can disable automatic module importing using the `$PSModuleAutoloadingPreference` preference variable.</span></span> <span data-ttu-id="9d428-120">如需變數的詳細資訊 `$PSModuleAutoloadingPreference` ，請參閱 [about_Preference_Variables](About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="9d428-120">For more information about the `$PSModuleAutoloadingPreference` variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="9d428-121">模組是一個套件，其中包含可在 PowerShell 中使用的成員。</span><span class="sxs-lookup"><span data-stu-id="9d428-121">A module is a package that contains members that can be used in PowerShell.</span></span> <span data-ttu-id="9d428-122">成員包括 Cmdlet、提供者、腳本、函式、變數和其他工具和檔案。</span><span class="sxs-lookup"><span data-stu-id="9d428-122">Members include cmdlets, providers, scripts, functions, variables, and other tools and files.</span></span> <span data-ttu-id="9d428-123">在匯入模組之後，您可以在工作階段中使用模組成員。</span><span class="sxs-lookup"><span data-stu-id="9d428-123">After a module is imported, you can use the module members in your session.</span></span> <span data-ttu-id="9d428-124">如需模組的詳細資訊，請參閱 [about_Modules](About/about_Modules.md)。</span><span class="sxs-lookup"><span data-stu-id="9d428-124">For more information about modules, see [about_Modules](About/about_Modules.md).</span></span>

<span data-ttu-id="9d428-125">根據預設， `Import-Module` 會匯入模組匯出的所有成員，但您可以使用 **別名**、 函式、 **Cmdlet** 和 **變數** 參數來限制要匯入的成員。</span><span class="sxs-lookup"><span data-stu-id="9d428-125">By default, `Import-Module` imports all members that the module exports, but you can use the **Alias**, **Function**, **Cmdlet**, and **Variable** parameters to restrict which members are imported.</span></span> <span data-ttu-id="9d428-126">**NoClobber** 參數會防止匯 `Import-Module` 入與目前會話中的成員具有相同名稱的成員。</span><span class="sxs-lookup"><span data-stu-id="9d428-126">The **NoClobber** parameter prevents `Import-Module` from importing members that have the same names as members in the current session.</span></span>

<span data-ttu-id="9d428-127">`Import-Module` 只將模組匯入到目前的會話。</span><span class="sxs-lookup"><span data-stu-id="9d428-127">`Import-Module` imports a module only into the current session.</span></span> <span data-ttu-id="9d428-128">若要將模組匯入到每個新的會話，請將 `Import-Module` 命令新增至您的 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="9d428-128">To import the module into every new session, add an `Import-Module` command to your PowerShell profile.</span></span> <span data-ttu-id="9d428-129">如需設定檔的詳細資訊，請參閱 [about_Profiles](About/about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="9d428-129">For more information about profiles, see [about_Profiles](About/about_Profiles.md).</span></span>

<span data-ttu-id="9d428-130">您可以在遠端電腦上建立 **PSSession** ，以管理已啟用 PowerShell 遠端功能的遠端 Windows 電腦。</span><span class="sxs-lookup"><span data-stu-id="9d428-130">You can manage remote Windows computers that have PowerShell remoting enabled by creating a **PSSession** on the remote computer.</span></span> <span data-ttu-id="9d428-131">然後使用的 **PSSession** 參數 `Import-Module` ，匯入在遠端電腦上安裝的模組。</span><span class="sxs-lookup"><span data-stu-id="9d428-131">Then use the **PSSession** parameter of `Import-Module` to import the modules that are installed on the remote computer.</span></span> <span data-ttu-id="9d428-132">當您在目前的會話中使用匯入的命令時，命令會隱含地在遠端電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="9d428-132">When you use the imported commands in the current session the commands implicitly run on the remote computer.</span></span>

<span data-ttu-id="9d428-133">從 Windows PowerShell 3.0 開始，您可以使用匯 `Import-Module` 入通用訊息模型 (CIM) 模組。</span><span class="sxs-lookup"><span data-stu-id="9d428-133">Starting in Windows PowerShell 3.0, you can use `Import-Module` to import Common Information Model (CIM) modules.</span></span> <span data-ttu-id="9d428-134">CIM 模組會在 Cmdlet 定義 XML (CDXML) 檔中定義 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9d428-134">CIM modules define cmdlets in Cmdlet Definition XML (CDXML) files.</span></span> <span data-ttu-id="9d428-135">這項功能可讓您使用在非受控程式碼元件中執行的 Cmdlet，例如以 c + + 撰寫的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9d428-135">This feature lets you use cmdlets that are implemented in non-managed code assemblies, such as those written in C++.</span></span>

<span data-ttu-id="9d428-136">針對未啟用 PowerShell 遠端處理的遠端電腦，包括不是執行 Windows 作業系統的電腦，您可以使用的 **CIMSession** 參數， `Import-Module` 從遠端電腦匯入 CIM 模組。</span><span class="sxs-lookup"><span data-stu-id="9d428-136">For remote computers that don't have PowerShell remoting enabled, including computers that aren't running the Windows operating system, you can use the **CIMSession** parameter of `Import-Module` to import CIM modules from the remote computer.</span></span> <span data-ttu-id="9d428-137">匯入的命令會隱含地在遠端電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="9d428-137">The imported commands run implicitly on the remote computer.</span></span> <span data-ttu-id="9d428-138">**CIMSession** 是連線到遠端電腦上的 WINDOWS MANAGEMENT INSTRUMENTATION (WMI) 的連接。</span><span class="sxs-lookup"><span data-stu-id="9d428-138">A **CIMSession** is a connection to Windows Management Instrumentation (WMI) on the remote computer.</span></span>

## <span data-ttu-id="9d428-139">範例</span><span class="sxs-lookup"><span data-stu-id="9d428-139">EXAMPLES</span></span>

### <span data-ttu-id="9d428-140">範例1：將模組的成員匯入到目前的會話</span><span class="sxs-lookup"><span data-stu-id="9d428-140">Example 1: Import the members of a module into the current session</span></span>

<span data-ttu-id="9d428-141">此範例會將 **PSDiagnostics** 模組的成員匯入到目前的會話。</span><span class="sxs-lookup"><span data-stu-id="9d428-141">This example imports the members of the **PSDiagnostics** module into the current session.</span></span>

```powershell
Import-Module -Name PSDiagnostics
```

### <span data-ttu-id="9d428-142">範例2：匯入模組路徑所指定的所有模組</span><span class="sxs-lookup"><span data-stu-id="9d428-142">Example 2: Import all modules specified by the module path</span></span>

<span data-ttu-id="9d428-143">此範例會將環境變數所指定路徑中的所有可用模組匯入 `$env:PSModulePath` 到目前的會話。</span><span class="sxs-lookup"><span data-stu-id="9d428-143">This example imports all available modules in the path specified by the `$env:PSModulePath` environment variable into the current session.</span></span>

```powershell
Get-Module -ListAvailable | Import-Module
```

### <span data-ttu-id="9d428-144">範例3：將數個模組的成員匯入到目前的會話</span><span class="sxs-lookup"><span data-stu-id="9d428-144">Example 3: Import the members of several modules into the current session</span></span>

<span data-ttu-id="9d428-145">此範例會將 **PSDiagnostics** 和 **Dism** 模組的成員匯入到目前的會話。</span><span class="sxs-lookup"><span data-stu-id="9d428-145">This example imports the members of the **PSDiagnostics** and **Dism** modules into the current session.</span></span>

```powershell
$m = Get-Module -ListAvailable PSDiagnostics, Dism
Import-Module -ModuleInfo $m
```

<span data-ttu-id="9d428-146">`Get-Module`Cmdlet 會取得 **PSDiagnostics** 和 **Dism** 模組，並將物件儲存在變數中 `$m` 。</span><span class="sxs-lookup"><span data-stu-id="9d428-146">The `Get-Module` cmdlet gets the **PSDiagnostics** and **Dism** modules and saves the objects in the `$m` variable.</span></span> <span data-ttu-id="9d428-147">當您取得尚未匯入至會話的模組時，必須要有 **ListAvailable** 參數。</span><span class="sxs-lookup"><span data-stu-id="9d428-147">The **ListAvailable** parameter is required when you're getting modules that aren't yet imported into the session.</span></span>

<span data-ttu-id="9d428-148">的 **ModuleInfo** 參數 `Import-Module` 是用來將模組匯入到目前的會話。</span><span class="sxs-lookup"><span data-stu-id="9d428-148">The **ModuleInfo** parameter of `Import-Module` is used to import the modules into the current session.</span></span>

### <span data-ttu-id="9d428-149">範例4：匯入路徑指定的所有模組</span><span class="sxs-lookup"><span data-stu-id="9d428-149">Example 4: Import all modules specified by a path</span></span>

<span data-ttu-id="9d428-150">此範例會使用明確的路徑來識別要匯入的模組。</span><span class="sxs-lookup"><span data-stu-id="9d428-150">This example uses an explicit path to identify the module to import.</span></span>

```powershell
Import-Module -Name c:\ps-test\modules\test -Verbose
```

```Output
VERBOSE: Loading module from path 'C:\ps-test\modules\Test\Test.psm1'.
VERBOSE: Exporting function 'my-parm'.
VERBOSE: Exporting function 'Get-Parameter'.
VERBOSE: Exporting function 'Get-Specification'.
VERBOSE: Exporting function 'Get-SpecDetails'.
```

<span data-ttu-id="9d428-151">使用 **Verbose** 參數會導致在 `Import-Module` 載入模組時報告進度。</span><span class="sxs-lookup"><span data-stu-id="9d428-151">Using the **Verbose** parameter causes `Import-Module` to report progress as it loads the module.</span></span>
<span data-ttu-id="9d428-152">如果沒有 **Verbose**、 **PassThru** 或 **AsCustomObject** 參數， `Import-Module` 則在匯入模組時不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="9d428-152">Without the **Verbose**, **PassThru**, or **AsCustomObject** parameter, `Import-Module` does not generate any output when it imports a module.</span></span>

### <span data-ttu-id="9d428-153">範例5：限制匯入到會話的模組成員</span><span class="sxs-lookup"><span data-stu-id="9d428-153">Example 5: Restrict module members imported into a session</span></span>

<span data-ttu-id="9d428-154">此範例顯示如何限制將哪些模組成員匯入會話，以及此命令在會話上的效果。</span><span class="sxs-lookup"><span data-stu-id="9d428-154">This example shows how to restrict which module members are imported into the session and the effect of this command on the session.</span></span> <span data-ttu-id="9d428-155">**函數** 參數會限制從模組匯入的成員。</span><span class="sxs-lookup"><span data-stu-id="9d428-155">The **Function** parameter limits the members that are imported from the module.</span></span> <span data-ttu-id="9d428-156">您也可以使用 **別名**、 **變數** 和 **Cmdlet** 參數來限制模組所匯入的其他成員。</span><span class="sxs-lookup"><span data-stu-id="9d428-156">You can also use the **Alias**, **Variable**, and **Cmdlet** parameters to restrict other members that a module imports.</span></span>

<span data-ttu-id="9d428-157">`Get-Module`Cmdlet 會取得代表 **PSDiagnostics** 模組的物件。</span><span class="sxs-lookup"><span data-stu-id="9d428-157">The `Get-Module` cmdlet gets the object that represents the **PSDiagnostics** module.</span></span> <span data-ttu-id="9d428-158">**ExportedCmdlets** 屬性會列出模組匯出的所有 Cmdlet，即使它們並未全部匯入也一樣。</span><span class="sxs-lookup"><span data-stu-id="9d428-158">The **ExportedCmdlets** property lists all the cmdlets that the module exports, even though they were not all imported.</span></span>

```powershell
Import-Module PSDiagnostics -Function Disable-PSTrace, Enable-PSTrace
(Get-Module PSDiagnostics).ExportedCommands
```

```Output
Key                          Value
---                          -----
Disable-PSTrace              Disable-PSTrace
Disable-PSWSManCombinedTrace Disable-PSWSManCombinedTrace
Disable-WSManTrace           Disable-WSManTrace
Enable-PSTrace               Enable-PSTrace
Enable-PSWSManCombinedTrace  Enable-PSWSManCombinedTrace
Enable-WSManTrace            Enable-WSManTrace
Get-LogProperties            Get-LogProperties
Set-LogProperties            Set-LogProperties
Start-Trace                  Start-Trace
Stop-Trace                   Stop-Trace
```

```powershell
Get-Command -Module PSDiagnostics
```

```Output
CommandType     Name                 Version    Source
-----------     ----                 -------    ------
Function        Disable-PSTrace      6.1.0.0    PSDiagnostics
Function        Enable-PSTrace       6.1.0.0    PSDiagnostics
```

<span data-ttu-id="9d428-159">使用 Cmdlet 的 **Module** 參數， `Get-Command` 會顯示從 **PSDiagnostics** 模組匯入的命令。</span><span class="sxs-lookup"><span data-stu-id="9d428-159">Using the **Module** parameter of the `Get-Command` cmdlet shows the commands that were imported from the **PSDiagnostics** module.</span></span> <span data-ttu-id="9d428-160">結果會確認只匯 `Disable-PSTrace` 入和 `Enable-PSTrace` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9d428-160">The results confirm that only the `Disable-PSTrace` and `Enable-PSTrace` cmdlets were imported.</span></span>

### <span data-ttu-id="9d428-161">範例6：匯入模組的成員並新增前置詞</span><span class="sxs-lookup"><span data-stu-id="9d428-161">Example 6: Import the members of a module and add a prefix</span></span>

<span data-ttu-id="9d428-162">此範例會將 **PSDiagnostics** 模組匯入到目前的會話、將前置詞新增至成員名稱，然後顯示前置詞的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="9d428-162">This example imports the **PSDiagnostics** module into the current session, adds a prefix to the member names, and then displays the prefixed member names.</span></span> <span data-ttu-id="9d428-163">的 **prefix** 參數 `Import-Module` 會將 **x** 前置詞加入至從模組匯入的所有成員。</span><span class="sxs-lookup"><span data-stu-id="9d428-163">The **Prefix** parameter of `Import-Module` adds the **x** prefix to all members that are imported from the module.</span></span> <span data-ttu-id="9d428-164">前置詞只適用于目前會話中的成員。</span><span class="sxs-lookup"><span data-stu-id="9d428-164">The prefix applies only to the members in the current session.</span></span> <span data-ttu-id="9d428-165">它不會變更模組。</span><span class="sxs-lookup"><span data-stu-id="9d428-165">It does not change the module.</span></span> <span data-ttu-id="9d428-166">**PassThru** 參數會傳回代表匯入模組的模組物件。</span><span class="sxs-lookup"><span data-stu-id="9d428-166">The **PassThru** parameter returns a module object that represents the imported module.</span></span>

```powershell
Import-Module PSDiagnostics -Prefix x -PassThru
```

```Output
ModuleType Version    Name               ExportedCommands
---------- -------    ----               ----------------
Script     6.1.0.0    PSDiagnostics      {Disable-xPSTrace, Disable-xPSWSManCombinedTrace, Disable-xW...
```

```powershell
Get-Command -Module PSDiagnostics
```

```Output
CommandType     Name                                   Version    Source
-----------     ----                                   -------    ------
Function        Disable-xPSTrace                       6.1.0.0    PSDiagnostics
Function        Disable-xPSWSManCombinedTrace          6.1.0.0    PSDiagnostics
Function        Disable-xWSManTrace                    6.1.0.0    PSDiagnostics
Function        Enable-xPSTrace                        6.1.0.0    PSDiagnostics
Function        Enable-xPSWSManCombinedTrace           6.1.0.0    PSDiagnostics
Function        Enable-xWSManTrace                     6.1.0.0    PSDiagnostics
Function        Get-xLogProperties                     6.1.0.0    PSDiagnostics
Function        Set-xLogProperties                     6.1.0.0    PSDiagnostics
Function        Start-xTrace                           6.1.0.0    PSDiagnostics
Function        Stop-xTrace                            6.1.0.0    PSDiagnostics
```

<span data-ttu-id="9d428-167">`Get-Command` 取得已從模組匯入的成員。</span><span class="sxs-lookup"><span data-stu-id="9d428-167">`Get-Command` gets the members that have been imported from the module.</span></span> <span data-ttu-id="9d428-168">輸出會顯示已正確為模組成員加上前置詞。</span><span class="sxs-lookup"><span data-stu-id="9d428-168">The output shows that the module members were correctly prefixed.</span></span>

### <span data-ttu-id="9d428-169">範例7：取得和使用自訂物件</span><span class="sxs-lookup"><span data-stu-id="9d428-169">Example 7: Get and use a custom object</span></span>

<span data-ttu-id="9d428-170">這個範例示範如何取得和使用所傳回的自訂物件 `Import-Module` 。</span><span class="sxs-lookup"><span data-stu-id="9d428-170">This example demonstrates how to get and use the custom object returned by `Import-Module`.</span></span>

<span data-ttu-id="9d428-171">自訂物件包括代表每個匯入之模組成員的綜合成員。</span><span class="sxs-lookup"><span data-stu-id="9d428-171">Custom objects include synthetic members that represent each of the imported module members.</span></span> <span data-ttu-id="9d428-172">例如，模組中的 Cmdlet 和函式會轉換成自訂物件的指令碼方法。</span><span class="sxs-lookup"><span data-stu-id="9d428-172">For example, the cmdlets and functions in a module are converted to script methods of the custom object.</span></span>

<span data-ttu-id="9d428-173">自訂物件在撰寫腳本時非常有用。</span><span class="sxs-lookup"><span data-stu-id="9d428-173">Custom objects are useful in scripting.</span></span> <span data-ttu-id="9d428-174">它們在有數個匯入的物件有相同名稱時也非常有用。</span><span class="sxs-lookup"><span data-stu-id="9d428-174">They are also useful when several imported objects have the same names.</span></span> <span data-ttu-id="9d428-175">使用物件的指令碼方法相當於指定匯入成員的完整名稱，包括其模組名稱。</span><span class="sxs-lookup"><span data-stu-id="9d428-175">Using the script method of an object is equivalent to specifying the fully qualified name of an imported member, including its module name.</span></span>

<span data-ttu-id="9d428-176">只有在匯入腳本模組時，才能使用 **AsCustomObject** 參數。</span><span class="sxs-lookup"><span data-stu-id="9d428-176">The **AsCustomObject** parameter can be used only when importing a script module.</span></span> <span data-ttu-id="9d428-177">用 `Get-Module` 來判斷哪些可用的模組是腳本模組。</span><span class="sxs-lookup"><span data-stu-id="9d428-177">Use `Get-Module` to determine which of the available modules is a script module.</span></span>

```powershell
Get-Module -List | Format-Table -Property Name, ModuleType -AutoSize
```

```Output
Name          ModuleType
----          ----------
Show-Calendar     Script
BitsTransfer    Manifest
PSDiagnostics   Manifest
TestCmdlets       Script
...
```

```powershell
$a = Import-Module -Name Show-Calendar -AsCustomObject -Passthru
$a | Get-Member
```

```Output
    TypeName: System.Management.Automation.PSCustomObject
Name          MemberType   Definition
----          ----------   ----------
Equals        Method       bool Equals(System.Object obj)
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
ToString      Method       string ToString()
Show-Calendar ScriptMethod System.Object Show-Calendar();
```

```powershell
$a."Show-Calendar"()
```

<span data-ttu-id="9d428-178">`Show-Calendar`使用 **AsCustomObject** 參數匯入腳本模組，以要求自訂物件，並使用 **PassThru** 參數來傳回物件。</span><span class="sxs-lookup"><span data-stu-id="9d428-178">The `Show-Calendar` script module is imported using the **AsCustomObject** parameter to request a custom object and the **PassThru** parameter to return the object.</span></span> <span data-ttu-id="9d428-179">產生的自訂物件會儲存在 `$a` 變數中。</span><span class="sxs-lookup"><span data-stu-id="9d428-179">The resulting custom object is saved in the `$a` variable.</span></span>

<span data-ttu-id="9d428-180">此 `$a` 變數會透過管道傳送至 `Get-Member` Cmdlet，以顯示已儲存物件的屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="9d428-180">The `$a` variable is piped to the `Get-Member` cmdlet to show the properties and methods of the saved object.</span></span> <span data-ttu-id="9d428-181">輸出會顯示 `Show-Calendar` 腳本方法。</span><span class="sxs-lookup"><span data-stu-id="9d428-181">The output shows a `Show-Calendar` script method.</span></span>

<span data-ttu-id="9d428-182">若要呼叫 `Show-Calendar` 腳本方法，方法名稱必須以引號括住，因為名稱包含連字號。</span><span class="sxs-lookup"><span data-stu-id="9d428-182">To call the `Show-Calendar` script method, the method name must be enclosed in quotation marks because the name includes a hyphen.</span></span>

### <span data-ttu-id="9d428-183">範例8：將模組重新匯入到相同的會話</span><span class="sxs-lookup"><span data-stu-id="9d428-183">Example 8: Reimport a module into the same session</span></span>

<span data-ttu-id="9d428-184">這個範例示範 `Import-Module` 當您在相同的會話中重新匯入模組時，如何使用的 Force 參數。</span><span class="sxs-lookup"><span data-stu-id="9d428-184">This example shows how to use the **Force** parameter of `Import-Module` when you're reimporting a module into the same session.</span></span> <span data-ttu-id="9d428-185">**Force** 參數會移除載入的模組，然後重新匯入。</span><span class="sxs-lookup"><span data-stu-id="9d428-185">The **Force** parameter removes the loaded module and then imports it again.</span></span>

```powershell
Import-Module PSDiagnostics
Import-Module PSDiagnostics -Force -Prefix PS
```

<span data-ttu-id="9d428-186">第一個命令會匯入 **PSDiagnostics** 模組。</span><span class="sxs-lookup"><span data-stu-id="9d428-186">The first command imports the **PSDiagnostics** module.</span></span> <span data-ttu-id="9d428-187">第二個命令再次匯入該模組，這次是使用 **Prefix** 參數。</span><span class="sxs-lookup"><span data-stu-id="9d428-187">The second command imports the module again, this time using the **Prefix** parameter.</span></span>

<span data-ttu-id="9d428-188">如果沒有 **Force** 參數，會話會包含每個 **PSDiagnostics** Cmdlet 的兩個複本，一個具有標準名稱，另一個具有首碼名稱。</span><span class="sxs-lookup"><span data-stu-id="9d428-188">Without the **Force** parameter, the session would include two copies of each **PSDiagnostics** cmdlet, one with the standard name and one with the prefixed name.</span></span>

### <span data-ttu-id="9d428-189">範例9：執行已匯入命令隱藏的命令</span><span class="sxs-lookup"><span data-stu-id="9d428-189">Example 9: Run commands that have been hidden by imported commands</span></span>

<span data-ttu-id="9d428-190">此範例顯示如何執行由匯入命令所隱藏的命令。</span><span class="sxs-lookup"><span data-stu-id="9d428-190">This example shows how to run commands that have been hidden by imported commands.</span></span> <span data-ttu-id="9d428-191">**TestModule** 模組包含名為的函式，該函式會傳回年的 `Get-Date` 年份和日。</span><span class="sxs-lookup"><span data-stu-id="9d428-191">The **TestModule** module includes a function named `Get-Date` that returns the year and day of the year.</span></span>

```powershell
Get-Date
```

```Output
Thursday, August 15, 2019 2:26:12 PM
```

```powershell
Import-Module TestModule
Get-Date
```

```Output
19227
```

```powershell
Get-Command Get-Date -All | Format-Table -Property CommandType, Name, ModuleName -AutoSize
```

```Output
CommandType     Name         ModuleName
-----------     ----         ----------
Function        Get-Date     TestModule
Cmdlet          Get-Date     Microsoft.PowerShell.Utility
```

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

```Output
Thursday, August 15, 2019 2:28:31 PM
```

<span data-ttu-id="9d428-192">第一個 `Get-Date` Cmdlet 會傳回包含目前日期的 **DateTime** 物件。</span><span class="sxs-lookup"><span data-stu-id="9d428-192">The first `Get-Date` cmdlet returns a **DateTime** object with the current date.</span></span> <span data-ttu-id="9d428-193">匯入 **TestModule** 模組之後，會傳回一 `Get-Date` 年的年份和日。</span><span class="sxs-lookup"><span data-stu-id="9d428-193">After importing the **TestModule** module, `Get-Date` returns the year and day of the year.</span></span>

<span data-ttu-id="9d428-194">使用的 **all** 參數會 `Get-Command` 顯示 `Get-Date` 會話中的所有命令。</span><span class="sxs-lookup"><span data-stu-id="9d428-194">Using the **All** parameter of `Get-Command` show all the `Get-Date` commands in the session.</span></span> <span data-ttu-id="9d428-195">結果顯示會話中有兩個 `Get-Date` 命令、 **TestModule** 模組中的函式，以及來自于 **Microsoft PowerShell** 模組的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9d428-195">The results show that there are two `Get-Date` commands in the session, a function from the **TestModule** module and a cmdlet from the **Microsoft.PowerShell.Utility** module.</span></span>

<span data-ttu-id="9d428-196">因為函式優先于 Cmdlet，所以 `Get-Date` **TestModule** 模組中的函式會執行，而不是 `Get-Date` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9d428-196">Because functions take precedence over cmdlets, the `Get-Date` function from the **TestModule** module runs, instead of the `Get-Date` cmdlet.</span></span> <span data-ttu-id="9d428-197">若要執行的原始版本 `Get-Date` ，您必須使用模組名稱來限定命令名稱。</span><span class="sxs-lookup"><span data-stu-id="9d428-197">To run the original version of `Get-Date`, you must qualify the command name with the module name.</span></span>

<span data-ttu-id="9d428-198">如需 PowerShell 中之命令優先順序的詳細資訊，請參閱 [about_Command_Precedence](about/about_Command_Precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="9d428-198">For more information about command precedence in PowerShell, see [about_Command_Precedence](about/about_Command_Precedence.md).</span></span>

### <span data-ttu-id="9d428-199">範例10：匯入模組的最小版本</span><span class="sxs-lookup"><span data-stu-id="9d428-199">Example 10: Import a minimum version of a module</span></span>

<span data-ttu-id="9d428-200">此範例會匯入 **PowerShellGet** 模組。</span><span class="sxs-lookup"><span data-stu-id="9d428-200">This example imports the **PowerShellGet** module.</span></span> <span data-ttu-id="9d428-201">它使用的 **MinimumVersion** 參數 `Import-Module` ，只匯入2.0.0 或更高版本的模組。</span><span class="sxs-lookup"><span data-stu-id="9d428-201">It uses the **MinimumVersion** parameter of `Import-Module` to import only version 2.0.0 or greater of the module.</span></span>

```powershell
Import-Module -Name PowerShellGet -MinimumVersion 2.0.0
```

<span data-ttu-id="9d428-202">您也可以使用 **RequiredVersion** 參數匯入特定版本的模組，或使用關鍵字的 **模組** 和 **版本** 參數 `#Requires` 來要求腳本中特定版本的模組。</span><span class="sxs-lookup"><span data-stu-id="9d428-202">You can also use the **RequiredVersion** parameter to import a particular version of a module, or use the **Module** and **Version** parameters of the `#Requires` keyword to require a particular version of a module in a script.</span></span>

### <span data-ttu-id="9d428-203">範例11：使用完整名稱匯入</span><span class="sxs-lookup"><span data-stu-id="9d428-203">Example 11: Import using a fully qualified name</span></span>

<span data-ttu-id="9d428-204">此範例會使用 FullyQualifiedName 來匯入特定版本的模組。</span><span class="sxs-lookup"><span data-stu-id="9d428-204">This example imports a specific version of a module using the FullyQualifiedName.</span></span>

```powershell
PS> Get-Module -ListAvailable PowerShellGet | Select-Object Name, Version

Name          Version
----          -------
PowerShellGet 2.2.1
PowerShellGet 2.1.3
PowerShellGet 2.1.2
PowerShellGet 1.0.0.1

PS> Import-Module -FullyQualifiedName @{ModuleName = 'PowerShellGet'; ModuleVersion = '2.1.3' }
```

### <span data-ttu-id="9d428-205">範例12：使用完整路徑匯入</span><span class="sxs-lookup"><span data-stu-id="9d428-205">Example 12: Import using a fully qualified path</span></span>

<span data-ttu-id="9d428-206">此範例會使用完整路徑來匯入特定版本的模組。</span><span class="sxs-lookup"><span data-stu-id="9d428-206">This example imports a specific version of a module using the fully qualified path.</span></span>

```powershell
PS> Get-Module -ListAvailable PowerShellGet | Select-Object Path

Path
----
C:\Program Files\PowerShell\Modules\PowerShellGet\2.2.1\PowerShellGet.psd1
C:\program files\powershell\6\Modules\PowerShellGet\PowerShellGet.psd1
C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\2.1.2\PowerShellGet.psd1
C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PowerShellGet.psd1

PS> Import-Module -Name 'C:\Program Files\PowerShell\Modules\PowerShellGet\2.2.1\PowerShellGet.psd1'
```

### <span data-ttu-id="9d428-207">範例13：從遠端電腦匯入模組</span><span class="sxs-lookup"><span data-stu-id="9d428-207">Example 13: Import a module from a remote computer</span></span>

<span data-ttu-id="9d428-208">此範例示範如何使用 `Import-Module` Cmdlet 從遠端電腦匯入模組。</span><span class="sxs-lookup"><span data-stu-id="9d428-208">This example shows how to use the `Import-Module` cmdlet to import a module from a remote computer.</span></span>
<span data-ttu-id="9d428-209">此命令會使用 PowerShell 的隱含遠端功能。</span><span class="sxs-lookup"><span data-stu-id="9d428-209">This command uses the Implicit Remoting feature of PowerShell.</span></span>

<span data-ttu-id="9d428-210">當您從另一個工作階段匯入模組時，您可以在目前的工作階段中使用 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9d428-210">When you import modules from another session, you can use the cmdlets in the current session.</span></span>
<span data-ttu-id="9d428-211">不過，使用 Cmdlet 的命令會在遠端會話中執行。</span><span class="sxs-lookup"><span data-stu-id="9d428-211">However, commands that use the cmdlets run in the remote session.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01
Get-Module -PSSession $s -ListAvailable -Name NetSecurity
```

```Output
ModuleType Name             ExportedCommands
---------- ----             ----------------
Manifest   NetSecurity      {New-NetIPsecAuthProposal, New-NetIPsecMainModeCryptoProposal, New-Ne...
```

```powershell
Import-Module -PSSession $s -Name NetSecurity
Get-Command -Module NetSecurity -Name Get-*Firewall*
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Function        Get-NetFirewallAddressFilter                       NetSecurity
Function        Get-NetFirewallApplicationFilter                   NetSecurity
Function        Get-NetFirewallInterfaceFilter                     NetSecurity
Function        Get-NetFirewallInterfaceTypeFilter                 NetSecurity
Function        Get-NetFirewallPortFilter                          NetSecurity
Function        Get-NetFirewallProfile                             NetSecurity
Function        Get-NetFirewallRule                                NetSecurity
Function        Get-NetFirewallSecurityFilter                      NetSecurity
Function        Get-NetFirewallServiceFilter                       NetSecurity
Function        Get-NetFirewallSetting                             NetSecurity
```

```powershell
Get-NetFirewallRule -DisplayName "Windows Remote Management*" |
  Format-Table -Property DisplayName, Name -AutoSize
```

```Output
DisplayName                                              Name
-----------                                              ----
Windows Remote Management (HTTP-In)                      WINRM-HTTP-In-TCP
Windows Remote Management (HTTP-In)                      WINRM-HTTP-In-TCP-PUBLIC
Windows Remote Management - Compatibility Mode (HTTP-In) WINRM-HTTP-Compat-In-TCP
```

<span data-ttu-id="9d428-212">`New-PSSession` 建立 (**PSSession**) 至 Server01 電腦的遠端會話。</span><span class="sxs-lookup"><span data-stu-id="9d428-212">`New-PSSession` creates a remote session (**PSSession**) to the Server01 computer.</span></span> <span data-ttu-id="9d428-213">**PSSession** 會儲存在變數中 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="9d428-213">The **PSSession** is saved in the `$s` variable.</span></span>

<span data-ttu-id="9d428-214">`Get-Module`以 **PSSession** 參數執行時，會顯示已在遠端電腦上安裝並使用 **NetSecurity** 模組。</span><span class="sxs-lookup"><span data-stu-id="9d428-214">Running `Get-Module` with the **PSSession** parameter shows that the **NetSecurity** module is installed and available on the remote computer.</span></span> <span data-ttu-id="9d428-215">此命令相當於使用 `Invoke-Command` Cmdlet `Get-Module` 在遠端會話中執行命令。</span><span class="sxs-lookup"><span data-stu-id="9d428-215">This command is equivalent to using the `Invoke-Command` cmdlet to run `Get-Module` command in the remote session.</span></span> <span data-ttu-id="9d428-216">例如： (`Invoke-Command $s {Get-Module -ListAvailable -Name NetSecurity`</span><span class="sxs-lookup"><span data-stu-id="9d428-216">For example: (`Invoke-Command $s {Get-Module -ListAvailable -Name NetSecurity`</span></span>

<span data-ttu-id="9d428-217">`Import-Module`以 **PSSession** 參數執行時，會將 **NetSecurity** 模組從遠端電腦匯入到目前的會話。</span><span class="sxs-lookup"><span data-stu-id="9d428-217">Running `Import-Module` with the **PSSession** parameter imports the **NetSecurity** module from the remote computer into the current session.</span></span> <span data-ttu-id="9d428-218">此 `Get-Command` Cmdlet 是用來取得以 **get** 開頭的命令，並從 **NetSecurity** 模組包含 **防火牆**。</span><span class="sxs-lookup"><span data-stu-id="9d428-218">The `Get-Command` cmdlet is used to get commands that begin with **Get** and include **Firewall** from the **NetSecurity** module.</span></span> <span data-ttu-id="9d428-219">輸出會確認模組及其 Cmdlet 已匯入至目前的會話。</span><span class="sxs-lookup"><span data-stu-id="9d428-219">The output confirms that the module and its cmdlets were imported into the current session.</span></span>

<span data-ttu-id="9d428-220">接著， `Get-NetFirewallRule` Cmdlet 會取得 Server01 電腦上 Windows 遠端管理的防火牆規則。</span><span class="sxs-lookup"><span data-stu-id="9d428-220">Next, the `Get-NetFirewallRule` cmdlet gets Windows Remote Management firewall rules on the Server01 computer.</span></span> <span data-ttu-id="9d428-221">這相當於使用 `Invoke-Command` Cmdlet `Get-NetFirewallRule` 在遠端會話上執行。</span><span class="sxs-lookup"><span data-stu-id="9d428-221">This is equivalent to using the `Invoke-Command` cmdlet to run `Get-NetFirewallRule` on the remote session.</span></span>

### <span data-ttu-id="9d428-222">範例14：不使用 Windows 作業系統來管理遠端電腦上的存放裝置</span><span class="sxs-lookup"><span data-stu-id="9d428-222">Example 14: Manage storage on a remote computer without the Windows operating system</span></span>

<span data-ttu-id="9d428-223">在此範例中，電腦的系統管理員已安裝「模組探索」 WMI 提供者，可讓您使用專為提供者設計的 CIM 命令。</span><span class="sxs-lookup"><span data-stu-id="9d428-223">In this example, the administrator of the computer has installed the Module Discovery WMI provider, which allows you to use CIM commands that are designed for the provider.</span></span>

<span data-ttu-id="9d428-224">此 `New-CimSession` Cmdlet 會在名為 RSDGF03 的遠端電腦上建立會話。</span><span class="sxs-lookup"><span data-stu-id="9d428-224">The `New-CimSession` cmdlet creates a session on the remote computer named RSDGF03.</span></span> <span data-ttu-id="9d428-225">會話會連接到遠端電腦上的 WMI 服務。</span><span class="sxs-lookup"><span data-stu-id="9d428-225">The session connects to the WMI service on the remote computer.</span></span> <span data-ttu-id="9d428-226">CIM 會話會儲存在變數中 `$cs` 。</span><span class="sxs-lookup"><span data-stu-id="9d428-226">The CIM session is saved in the `$cs` variable.</span></span>
<span data-ttu-id="9d428-227">`Import-Module`使用中的 CimSession `$cs` ，從 RSDGF03 電腦匯入 **儲存體** CIM 模組。</span><span class="sxs-lookup"><span data-stu-id="9d428-227">`Import-Module` uses the **CimSession** in `$cs` to import the **Storage** CIM module from the RSDGF03 computer.</span></span>

<span data-ttu-id="9d428-228">此 `Get-Command` Cmdlet 會 `Get-Disk` 在 **儲存體** 模組中顯示命令。</span><span class="sxs-lookup"><span data-stu-id="9d428-228">The `Get-Command` cmdlet shows the `Get-Disk` command in the **Storage** module.</span></span> <span data-ttu-id="9d428-229">當您將 CIM 模組匯入本機會話時，PowerShell 會將每個命令的 CDXML 檔案轉換成 PowerShell 腳本，這會在本機會話中以函式的形式出現。</span><span class="sxs-lookup"><span data-stu-id="9d428-229">When you import a CIM module into the local session, PowerShell converts the CDXML files for each command into PowerShell scripts, which appear as functions in the local session.</span></span>

<span data-ttu-id="9d428-230">雖然 `Get-Disk` 是在本機會話中輸入的，但此 Cmdlet 會隱含地在其匯入的遠端電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="9d428-230">Although `Get-Disk` is typed in the local session, the cmdlet implicitly runs on the remote computer from which it was imported.</span></span> <span data-ttu-id="9d428-231">此命令會將物件從遠端電腦傳回至本機會話。</span><span class="sxs-lookup"><span data-stu-id="9d428-231">The command returns objects from the remote computer to the local session.</span></span>

```powershell
$cs = New-CimSession -ComputerName RSDGF03
Import-Module -CimSession $cs -Name Storage
# Importing a CIM module, converts the CDXML files for each command into PowerShell scripts.
# These appear as functions in the local session.
Get-Command Get-Disk
```

```Output
CommandType     Name                  ModuleName
-----------     ----                  ----------
Function        Get-Disk              Storage
```

```powershell
# Use implicit remoting to query disks on the remote computer from which the module was imported.
Get-Disk
```

```Output
Number Friendly Name           OperationalStatus  Total Size Partition Style
------ -------------           -----------------  ---------- ---------------
0      Virtual HD ATA Device   Online                  40 GB MBR
```

## <span data-ttu-id="9d428-232">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9d428-232">PARAMETERS</span></span>

### <span data-ttu-id="9d428-233">-Alias</span><span class="sxs-lookup"><span data-stu-id="9d428-233">-Alias</span></span>

<span data-ttu-id="9d428-234">指定此 Cmdlet 從模組匯入至目前會話的別名。</span><span class="sxs-lookup"><span data-stu-id="9d428-234">Specifies the aliases that this cmdlet imports from the module into the current session.</span></span> <span data-ttu-id="9d428-235">輸入以逗號分隔的別名清單。</span><span class="sxs-lookup"><span data-stu-id="9d428-235">Enter a comma-separated list of aliases.</span></span> <span data-ttu-id="9d428-236">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="9d428-236">Wildcard characters are permitted.</span></span>

<span data-ttu-id="9d428-237">當您匯入模組時，某些模組會自動將選取的別名匯出至您的工作階段。</span><span class="sxs-lookup"><span data-stu-id="9d428-237">Some modules automatically export selected aliases into your session when you import the module.</span></span>
<span data-ttu-id="9d428-238">此參數可讓您從匯出的別名中選取。</span><span class="sxs-lookup"><span data-stu-id="9d428-238">This parameter lets you select from among the exported aliases.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="9d428-239">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="9d428-239">-ArgumentList</span></span>

<span data-ttu-id="9d428-240">指定在命令期間傳遞至腳本模組的引數或參數值陣列 `Import-Module` 。</span><span class="sxs-lookup"><span data-stu-id="9d428-240">Specifies an array of arguments, or parameter values, that are passed to a script module during the `Import-Module` command.</span></span> <span data-ttu-id="9d428-241">只有在匯入腳本模組時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="9d428-241">This parameter is valid only when you're importing a script module.</span></span>

<span data-ttu-id="9d428-242">您也可以使用其別名（ **args**）來參考 **ArgumentList** 參數。</span><span class="sxs-lookup"><span data-stu-id="9d428-242">You can also refer to the **ArgumentList** parameter by its alias, **args**.</span></span> <span data-ttu-id="9d428-243">如需有關 **ArgumentList** 行為的詳細資訊，請參閱 [about_Splatting](about/about_Splatting.md#splatting-with-arrays)。</span><span class="sxs-lookup"><span data-stu-id="9d428-243">For more information about the behavior of **ArgumentList**, see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9d428-244">-AsCustomObject</span><span class="sxs-lookup"><span data-stu-id="9d428-244">-AsCustomObject</span></span>

<span data-ttu-id="9d428-245">指出此 Cmdlet 會傳回自訂物件，其成員代表已匯入的模組成員。</span><span class="sxs-lookup"><span data-stu-id="9d428-245">Indicates that this cmdlet returns a custom object with members that represent the imported module members.</span></span> <span data-ttu-id="9d428-246">此參數只適用於指令碼模組。</span><span class="sxs-lookup"><span data-stu-id="9d428-246">This parameter is valid only for script modules.</span></span>

<span data-ttu-id="9d428-247">當您使用 **AsCustomObject** 參數時，會將 `Import-Module` 模組成員匯入到會話中，然後傳回 **PSCustomObject** 物件，而非 **PSModuleInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="9d428-247">When you use the **AsCustomObject** parameter, `Import-Module` imports the module members into the session and then returns a **PSCustomObject** object instead of a **PSModuleInfo** object.</span></span> <span data-ttu-id="9d428-248">您可以將自訂物件儲存在變數中，並使用點標記法來叫用成員。</span><span class="sxs-lookup"><span data-stu-id="9d428-248">You can save the custom object in a variable and use dot notation to invoke the members.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9d428-249">-Assembly</span><span class="sxs-lookup"><span data-stu-id="9d428-249">-Assembly</span></span>

<span data-ttu-id="9d428-250">指定元件物件的陣列。</span><span class="sxs-lookup"><span data-stu-id="9d428-250">Specifies an array of assembly objects.</span></span> <span data-ttu-id="9d428-251">此 Cmdlet 會匯入在指定元件物件中執行的 Cmdlet 和提供者。</span><span class="sxs-lookup"><span data-stu-id="9d428-251">This cmdlet imports the cmdlets and providers implemented in the specified assembly objects.</span></span> <span data-ttu-id="9d428-252">輸入包含組件物件的變數，或輸入可建立組件物件的命令。</span><span class="sxs-lookup"><span data-stu-id="9d428-252">Enter a variable that contains assembly objects or a command that creates assembly objects.</span></span> <span data-ttu-id="9d428-253">您也可以使用管線將元件物件傳送至 `Import-Module` 。</span><span class="sxs-lookup"><span data-stu-id="9d428-253">You can also pipe an assembly object to `Import-Module`.</span></span>

<span data-ttu-id="9d428-254">當您使用此參數時，只會匯入指定組件所實作的 Cmdlet 與提供者。</span><span class="sxs-lookup"><span data-stu-id="9d428-254">When you use this parameter, only the cmdlets and providers implemented by the specified assemblies are imported.</span></span> <span data-ttu-id="9d428-255">如果模組包含其他檔案，則不會匯入它們，而且您可能會遺失模組的重要成員。</span><span class="sxs-lookup"><span data-stu-id="9d428-255">If the module contains other files, they aren't imported, and you might be missing important members of the module.</span></span> <span data-ttu-id="9d428-256">您可以使用此參數來偵測和測試模組，或在您指示模組作者使用它時使用此參數。</span><span class="sxs-lookup"><span data-stu-id="9d428-256">Use this parameter for debugging and testing the module, or when you're instructed to use it by the module author.</span></span>

```yaml
Type: System.Reflection.Assembly[]
Parameter Sets: Assembly
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9d428-257">-CimNamespace</span><span class="sxs-lookup"><span data-stu-id="9d428-257">-CimNamespace</span></span>

<span data-ttu-id="9d428-258">指定公開 CIM 模組的替代 CIM 提供者命名空間。</span><span class="sxs-lookup"><span data-stu-id="9d428-258">Specifies the namespace of an alternate CIM provider that exposes CIM modules.</span></span> <span data-ttu-id="9d428-259">預設值為「模組探索」WMI 提供者的命名空間。</span><span class="sxs-lookup"><span data-stu-id="9d428-259">The default value is the namespace of the Module Discovery WMI provider.</span></span>

<span data-ttu-id="9d428-260">使用此參數從不是執行 Windows 作業系統的電腦和裝置匯入 CIM 模組。</span><span class="sxs-lookup"><span data-stu-id="9d428-260">Use this parameter to import CIM modules from computers and devices that aren't running a Windows operating system.</span></span>

<span data-ttu-id="9d428-261">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="9d428-261">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="9d428-262">-CimResourceUri</span><span class="sxs-lookup"><span data-stu-id="9d428-262">-CimResourceUri</span></span>

<span data-ttu-id="9d428-263">指定 CIM 模組的替代位置。</span><span class="sxs-lookup"><span data-stu-id="9d428-263">Specifies an alternate location for CIM modules.</span></span> <span data-ttu-id="9d428-264">預設值為遠端電腦上「模組探索」 WMI 提供者的資源 URI。</span><span class="sxs-lookup"><span data-stu-id="9d428-264">The default value is the resource URI of the Module Discovery WMI provider on the remote computer.</span></span>

<span data-ttu-id="9d428-265">使用此參數從不是執行 Windows 作業系統的電腦和裝置匯入 CIM 模組。</span><span class="sxs-lookup"><span data-stu-id="9d428-265">Use this parameter to import CIM modules from computers and devices that aren't running a Windows operating system.</span></span>

<span data-ttu-id="9d428-266">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="9d428-266">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="9d428-267">-CimSession</span><span class="sxs-lookup"><span data-stu-id="9d428-267">-CimSession</span></span>

<span data-ttu-id="9d428-268">指定遠端電腦上的 CIM 工作階段。</span><span class="sxs-lookup"><span data-stu-id="9d428-268">Specifies a CIM session on the remote computer.</span></span> <span data-ttu-id="9d428-269">輸入包含 CIM 會話的變數，或輸入可取得 CIM 會話的命令，例如 [CimSession](../CimCmdlets/Get-CimSession.md) 命令。</span><span class="sxs-lookup"><span data-stu-id="9d428-269">Enter a variable that contains the CIM session or a command that gets the CIM session, such as a [Get-CimSession](../CimCmdlets/Get-CimSession.md) command.</span></span>

<span data-ttu-id="9d428-270">`Import-Module` 使用 CIM 會話連線，從遠端電腦將模組匯入到目前的會話。</span><span class="sxs-lookup"><span data-stu-id="9d428-270">`Import-Module` uses the CIM session connection to import modules from the remote computer into the current session.</span></span> <span data-ttu-id="9d428-271">當您在目前會話中使用匯入模組的命令時，命令會在遠端電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="9d428-271">When you use the commands from the imported module in the current session, the commands run on the remote computer.</span></span>

<span data-ttu-id="9d428-272">您可以使用此參數從不是執行 Windows 作業系統的電腦和裝置，以及具有 PowerShell 但未啟用 PowerShell 遠端功能的 Windows 電腦匯入模組。</span><span class="sxs-lookup"><span data-stu-id="9d428-272">You can use this parameter to import modules from computers and devices that aren't running the Windows operating system, and Windows computers that have PowerShell, but don't have PowerShell remoting enabled.</span></span>

<span data-ttu-id="9d428-273">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="9d428-273">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="9d428-274">-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9d428-274">-Cmdlet</span></span>

<span data-ttu-id="9d428-275">指定此 Cmdlet 從模組匯入至目前會話的 Cmdlet 陣列。</span><span class="sxs-lookup"><span data-stu-id="9d428-275">Specifies an array of cmdlets that this cmdlet imports from the module into the current session.</span></span>
<span data-ttu-id="9d428-276">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="9d428-276">Wildcard characters are permitted.</span></span>

<span data-ttu-id="9d428-277">當您匯入模組時，某些模組會自動將選取的 Cmdlet 匯出至您的工作階段。</span><span class="sxs-lookup"><span data-stu-id="9d428-277">Some modules automatically export selected cmdlets into your session when you import the module.</span></span>
<span data-ttu-id="9d428-278">此參數可讓您從匯出的 Cmdlet 中選取。</span><span class="sxs-lookup"><span data-stu-id="9d428-278">This parameter lets you select from among the exported cmdlets.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="9d428-279">-DisableNameChecking</span><span class="sxs-lookup"><span data-stu-id="9d428-279">-DisableNameChecking</span></span>

<span data-ttu-id="9d428-280">指出當您匯入的 Cmdlet 或函式的名稱包含未核准的動詞或禁止的字元時，此 Cmdlet 會隱藏警告您的訊息。</span><span class="sxs-lookup"><span data-stu-id="9d428-280">Indicates that this cmdlet suppresses the message that warns you when you import a cmdlet or function whose name includes an unapproved verb or a prohibited character.</span></span>

<span data-ttu-id="9d428-281">依預設，當您匯入的模組會匯出其名稱中具有未核准動詞的 Cmdlet 或函式時，PowerShell 會顯示下列警告訊息：</span><span class="sxs-lookup"><span data-stu-id="9d428-281">By default, when a module that you import exports cmdlets or functions that have unapproved verbs in their names, PowerShell displays the following warning message:</span></span>

> <span data-ttu-id="9d428-282">警告：某些匯入的命令名稱包含未核准的動詞命令，可能會讓它們更不容易探索。</span><span class="sxs-lookup"><span data-stu-id="9d428-282">WARNING: Some imported command names include unapproved verbs which might make them less discoverable.</span></span> <span data-ttu-id="9d428-283">請使用 Verbose 參數取得詳細資訊，或輸入 Get-Verb 查看核准的動詞清單。</span><span class="sxs-lookup"><span data-stu-id="9d428-283">Use the Verbose parameter for more detail or type Get-Verb to see the list of approved verbs.</span></span>

<span data-ttu-id="9d428-284">這則訊息只是一個警告。</span><span class="sxs-lookup"><span data-stu-id="9d428-284">This message is only a warning.</span></span> <span data-ttu-id="9d428-285">模組仍然完整匯入，包括不合格的命令。</span><span class="sxs-lookup"><span data-stu-id="9d428-285">The complete module is still imported, including the non-conforming commands.</span></span> <span data-ttu-id="9d428-286">雖然訊息是顯示給模組的使用者，但命名的問題應該由模組作者修正。</span><span class="sxs-lookup"><span data-stu-id="9d428-286">Although the message is displayed to module users, the naming problem should be fixed by the module author.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9d428-287">-Force</span><span class="sxs-lookup"><span data-stu-id="9d428-287">-Force</span></span>

<span data-ttu-id="9d428-288">此參數會在目前的模組上載入或重載模組。</span><span class="sxs-lookup"><span data-stu-id="9d428-288">This parameter causes a module to be loaded, or reloaded, over top of the current one.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9d428-289">-FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="9d428-289">-FullyQualifiedName</span></span>

<span data-ttu-id="9d428-290">將模組的完整名稱指定為雜湊表。</span><span class="sxs-lookup"><span data-stu-id="9d428-290">Specifies the fully qualified name of the module as a hash table.</span></span> <span data-ttu-id="9d428-291">此值可以是字串和雜湊表的組合。</span><span class="sxs-lookup"><span data-stu-id="9d428-291">The value can be a combination of strings and hash tables.</span></span> <span data-ttu-id="9d428-292">雜湊表具有下列索引鍵。</span><span class="sxs-lookup"><span data-stu-id="9d428-292">The hash table has the following keys.</span></span>

- <span data-ttu-id="9d428-293">`ModuleName` - **必要** 指定模組名稱。</span><span class="sxs-lookup"><span data-stu-id="9d428-293">`ModuleName` - **Required** Specifies the module name.</span></span>
- <span data-ttu-id="9d428-294">`GUID` - **選擇性** 指定模組的 GUID。</span><span class="sxs-lookup"><span data-stu-id="9d428-294">`GUID` - **Optional** Specifies the GUID of the module.</span></span>
- <span data-ttu-id="9d428-295">您也 **必須** 指定下列三個索引鍵中的其中一個。</span><span class="sxs-lookup"><span data-stu-id="9d428-295">It's also **Required** to specify one of the three below keys.</span></span> <span data-ttu-id="9d428-296">這些金鑰無法一起使用。</span><span class="sxs-lookup"><span data-stu-id="9d428-296">These keys can't be used together.</span></span>
  - <span data-ttu-id="9d428-297">`ModuleVersion` -指定模組可接受的最小版本。</span><span class="sxs-lookup"><span data-stu-id="9d428-297">`ModuleVersion` - Specifies a minimum acceptable version of the module.</span></span>
  - <span data-ttu-id="9d428-298">`RequiredVersion` -指定完全必要的模組版本。</span><span class="sxs-lookup"><span data-stu-id="9d428-298">`RequiredVersion` - Specifies an exact, required version of the module.</span></span>
  - <span data-ttu-id="9d428-299">`MaximumVersion` -指定模組可接受的最大版本。</span><span class="sxs-lookup"><span data-stu-id="9d428-299">`MaximumVersion` - Specifies the maximum acceptable version of the module.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: FullyQualifiedNameAndPSSession, FullyQualifiedName, FullyQualifiedNameAndWinCompat
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9d428-300">-Function</span><span class="sxs-lookup"><span data-stu-id="9d428-300">-Function</span></span>

<span data-ttu-id="9d428-301">指定此 Cmdlet 從模組匯入至目前會話的函式陣列。</span><span class="sxs-lookup"><span data-stu-id="9d428-301">Specifies an array of functions that this cmdlet imports from the module into the current session.</span></span>
<span data-ttu-id="9d428-302">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="9d428-302">Wildcard characters are permitted.</span></span> <span data-ttu-id="9d428-303">當您匯入模組時，某些模組會自動將選取的函式匯出至您的工作階段。</span><span class="sxs-lookup"><span data-stu-id="9d428-303">Some modules automatically export selected functions into your session when you import the module.</span></span> <span data-ttu-id="9d428-304">此參數可讓您從匯出的函式中選取。</span><span class="sxs-lookup"><span data-stu-id="9d428-304">This parameter lets you select from among the exported functions.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="9d428-305">-Global</span><span class="sxs-lookup"><span data-stu-id="9d428-305">-Global</span></span>

<span data-ttu-id="9d428-306">指出此 Cmdlet 會將模組匯入到全域會話狀態，使其可供會話中的所有命令使用。</span><span class="sxs-lookup"><span data-stu-id="9d428-306">Indicates that this cmdlet imports modules into the global session state so they are available to all commands in the session.</span></span>

<span data-ttu-id="9d428-307">根據預設，當 `Import-Module` 從命令提示字元、腳本檔或 scriptblock 呼叫 Cmdlet 時，會將所有命令匯入到全域會話狀態。</span><span class="sxs-lookup"><span data-stu-id="9d428-307">By default, when `Import-Module` cmdlet is called from the command prompt, script file, or scriptblock, all the commands are imported into the global session state.</span></span>

<span data-ttu-id="9d428-308">從其他模組叫用時，Cmdlet 會將 `Import-Module` 模組中的命令（包括從嵌套模組載入的命令）匯入至呼叫模組的會話狀態。</span><span class="sxs-lookup"><span data-stu-id="9d428-308">When invoked from another module, `Import-Module` cmdlet imports the commands in a module, including commands from nested modules, into the calling module's session state.</span></span>

> [!TIP]
> <span data-ttu-id="9d428-309">您應該避免 `Import-Module` 從模組內呼叫。</span><span class="sxs-lookup"><span data-stu-id="9d428-309">You should avoid calling `Import-Module` from within a module.</span></span> <span data-ttu-id="9d428-310">相反地，請在父模組的資訊清單中，將目的模組宣告為嵌套模組。</span><span class="sxs-lookup"><span data-stu-id="9d428-310">Instead, declare the target module as a nested module in the parent module's manifest.</span></span> <span data-ttu-id="9d428-311">宣告嵌套模組可改善相依性的可探索性。</span><span class="sxs-lookup"><span data-stu-id="9d428-311">Declaring nested modules improves the discoverability of dependencies.</span></span>

<span data-ttu-id="9d428-312">**Global** 參數等同於值為 **Global** 的 **Scope** 參數。</span><span class="sxs-lookup"><span data-stu-id="9d428-312">The **Global** parameter is equivalent to the **Scope** parameter with a value of **Global**.</span></span>

<span data-ttu-id="9d428-313">若要限制模組所匯出的命令，請使用 `Export-ModuleMember` 腳本模組中的命令。</span><span class="sxs-lookup"><span data-stu-id="9d428-313">To restrict the commands that a module exports, use an `Export-ModuleMember` command in the script module.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9d428-314">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="9d428-314">-MaximumVersion</span></span>

<span data-ttu-id="9d428-315">指定最大版本。</span><span class="sxs-lookup"><span data-stu-id="9d428-315">Specifies a maximum version.</span></span> <span data-ttu-id="9d428-316">此 Cmdlet 只會匯入小於或等於指定值的模組版本。</span><span class="sxs-lookup"><span data-stu-id="9d428-316">This cmdlet imports only a version of the module that is less than or equal to the specified value.</span></span> <span data-ttu-id="9d428-317">如果沒有任何版本符合資格，就會傳回 `Import-Module` 錯誤。</span><span class="sxs-lookup"><span data-stu-id="9d428-317">If no version qualifies, `Import-Module` returns an error.</span></span>

```yaml
Type: System.String
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9d428-318">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="9d428-318">-MinimumVersion</span></span>

<span data-ttu-id="9d428-319">指定最小版本。</span><span class="sxs-lookup"><span data-stu-id="9d428-319">Specifies a minimum version.</span></span> <span data-ttu-id="9d428-320">此 Cmdlet 只會匯入大於或等於指定值的模組版本。</span><span class="sxs-lookup"><span data-stu-id="9d428-320">This cmdlet imports only a version of the module that is greater than or equal to the specified value.</span></span> <span data-ttu-id="9d428-321">使用 **MinimumVersion** 參數名稱或它的別名，**Version**。</span><span class="sxs-lookup"><span data-stu-id="9d428-321">Use the **MinimumVersion** parameter name or its alias, **Version**.</span></span> <span data-ttu-id="9d428-322">如果沒有任何版本符合資格，就會 `Import-Module` 產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="9d428-322">If no version qualifies, `Import-Module` generates an error.</span></span>

<span data-ttu-id="9d428-323">若要指定確切的版本，請使用 **RequiredVersion** 參數。</span><span class="sxs-lookup"><span data-stu-id="9d428-323">To specify an exact version, use the **RequiredVersion** parameter.</span></span> <span data-ttu-id="9d428-324">您也可以使用 **#Requires** 關鍵字的 **module** 和 **Version** 參數，要求在腳本中使用特定版本的模組。</span><span class="sxs-lookup"><span data-stu-id="9d428-324">You can also use the **Module** and **Version** parameters of the **#Requires** keyword to require a specific version of a module in a script.</span></span>

<span data-ttu-id="9d428-325">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="9d428-325">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Version
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases: Version

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9d428-326">-ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="9d428-326">-ModuleInfo</span></span>

<span data-ttu-id="9d428-327">指定要匯入之模組物件的陣列。</span><span class="sxs-lookup"><span data-stu-id="9d428-327">Specifies an array of module objects to import.</span></span> <span data-ttu-id="9d428-328">輸入包含模組物件的變數，或輸入可取得模組物件的命令，例如下列命令： `Get-Module -ListAvailable` 。</span><span class="sxs-lookup"><span data-stu-id="9d428-328">Enter a variable that contains the module objects, or a command that gets the module objects, such as the following command: `Get-Module -ListAvailable`.</span></span> <span data-ttu-id="9d428-329">您也可以透過管線將模組物件傳送至 `Import-Module` 。</span><span class="sxs-lookup"><span data-stu-id="9d428-329">You can also pipe module objects to `Import-Module`.</span></span>

```yaml
Type: System.Management.Automation.PSModuleInfo[]
Parameter Sets: ModuleInfo
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9d428-330">-Name</span><span class="sxs-lookup"><span data-stu-id="9d428-330">-Name</span></span>

<span data-ttu-id="9d428-331">指定要匯入之模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="9d428-331">Specifies the names of the modules to import.</span></span> <span data-ttu-id="9d428-332">輸入模組的名稱或模組中的檔案名，例如 `.psd1` 、、 `.psm1` 或檔案 `.dll` `.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="9d428-332">Enter the name of the module or the name of a file in the module, such as a `.psd1`, `.psm1`, `.dll`, or `.ps1` file.</span></span> <span data-ttu-id="9d428-333">檔案路徑為選擇性。</span><span class="sxs-lookup"><span data-stu-id="9d428-333">File paths are optional.</span></span> <span data-ttu-id="9d428-334">不允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="9d428-334">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="9d428-335">您也可以透過管線將模組名稱與檔案名傳送至 `Import-Module` 。</span><span class="sxs-lookup"><span data-stu-id="9d428-335">You can also pipe module names and filenames to `Import-Module`.</span></span>

<span data-ttu-id="9d428-336">如果您省略路徑，會 `Import-Module` 在環境變數中所儲存的路徑中尋找模組 `$env:PSModulePath` 。</span><span class="sxs-lookup"><span data-stu-id="9d428-336">If you omit a path, `Import-Module` looks for the module in the paths saved in the `$env:PSModulePath` environment variable.</span></span>

<span data-ttu-id="9d428-337">盡可能只指定模組名稱。</span><span class="sxs-lookup"><span data-stu-id="9d428-337">Specify only the module name whenever possible.</span></span> <span data-ttu-id="9d428-338">當您指定檔案名稱時，只會匯入該檔案中實作的成員。</span><span class="sxs-lookup"><span data-stu-id="9d428-338">When you specify a file name, only the members that are implemented in that file are imported.</span></span> <span data-ttu-id="9d428-339">如果模組包含其他檔案，則不會匯入它們，而且您可能會遺失模組的重要成員。</span><span class="sxs-lookup"><span data-stu-id="9d428-339">If the module contains other files, they aren't imported, and you might be missing important members of the module.</span></span>

> [!NOTE]
> <span data-ttu-id="9d428-340">雖然可以將腳本 () 檔匯入 `.ps1` 為模組，但腳本檔案通常不像腳本模組檔案 () 檔一樣 `.psm1` 。</span><span class="sxs-lookup"><span data-stu-id="9d428-340">While it is possible to import a script (`.ps1`) file as a module, script files are usually not structured like script modules file (`.psm1`) file.</span></span> <span data-ttu-id="9d428-341">匯入腳本檔案並不保證可作為模組使用。</span><span class="sxs-lookup"><span data-stu-id="9d428-341">Importing a script file does not guarantee that it is usable as a module.</span></span> <span data-ttu-id="9d428-342">如需詳細資訊，請參閱 [about_Modules](about/about_Modules.md)。</span><span class="sxs-lookup"><span data-stu-id="9d428-342">For more information, see [about_Modules](about/about_Modules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="9d428-343">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="9d428-343">-NoClobber</span></span>

<span data-ttu-id="9d428-344">防止匯入與目前會話中現有命令具有相同名稱的命令。</span><span class="sxs-lookup"><span data-stu-id="9d428-344">Prevents importing commands that have the same names as existing commands in the current session.</span></span> <span data-ttu-id="9d428-345">預設會匯 `Import-Module` 入所有匯出的模組命令。</span><span class="sxs-lookup"><span data-stu-id="9d428-345">By default, `Import-Module` imports all exported module commands.</span></span>

<span data-ttu-id="9d428-346">具有相同名稱的命令可以隱藏或取代會話中的命令。</span><span class="sxs-lookup"><span data-stu-id="9d428-346">Commands that have the same names can hide or replace commands in the session.</span></span> <span data-ttu-id="9d428-347">為避免工作階段中發生命令名稱衝突，請使用 **Prefix** 或 **NoClobber** 參數。</span><span class="sxs-lookup"><span data-stu-id="9d428-347">To avoid command name conflicts in a session, use the **Prefix** or **NoClobber** parameters.</span></span> <span data-ttu-id="9d428-348">如需名稱衝突和命令優先順序的詳細資訊，請參閱 [about_Modules](about/about_Modules.md) 中的「模組和名稱衝突」和 [about_Command_Precedence](about/about_Command_Precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="9d428-348">For more information about name conflicts and command precedence, see "Modules and Name Conflicts" in [about_Modules](about/about_Modules.md) and [about_Command_Precedence](about/about_Command_Precedence.md).</span></span>

<span data-ttu-id="9d428-349">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="9d428-349">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9d428-350">-PassThru</span><span class="sxs-lookup"><span data-stu-id="9d428-350">-PassThru</span></span>

<span data-ttu-id="9d428-351">傳回代表您正在使用之專案的物件。</span><span class="sxs-lookup"><span data-stu-id="9d428-351">Returns an object representing the item with which you're working.</span></span> <span data-ttu-id="9d428-352">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="9d428-352">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9d428-353">-前置詞</span><span class="sxs-lookup"><span data-stu-id="9d428-353">-Prefix</span></span>

<span data-ttu-id="9d428-354">指定此 Cmdlet 在匯入的模組成員名稱中新增至名詞的前置詞。</span><span class="sxs-lookup"><span data-stu-id="9d428-354">Specifies a prefix that this cmdlet adds to the nouns in the names of imported module members.</span></span>

<span data-ttu-id="9d428-355">使用此參數來避免工作階段中不同成員具有相同名稱時可能會發生的名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="9d428-355">Use this parameter to avoid name conflicts that might occur when different members in the session have the same name.</span></span> <span data-ttu-id="9d428-356">此參數不會變更模組，而且不會影響模組匯入以供自己使用的檔案。</span><span class="sxs-lookup"><span data-stu-id="9d428-356">This parameter does not change the module, and it does not affect files that the module imports for its own use.</span></span> <span data-ttu-id="9d428-357">這些稱為「嵌套模組」。</span><span class="sxs-lookup"><span data-stu-id="9d428-357">These are known as nested modules.</span></span> <span data-ttu-id="9d428-358">此 Cmdlet 只會影響目前會話中的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="9d428-358">This cmdlet affects only the names of members in the current session.</span></span>

<span data-ttu-id="9d428-359">例如，如果您指定首碼 UTC，然後匯入 `Get-Date` Cmdlet，則此 Cmdlet 在會話中會是已知的 `Get-UTCDate` ，且不會與原始的 Cmdlet 混淆 `Get-Date` 。</span><span class="sxs-lookup"><span data-stu-id="9d428-359">For example, if you specify the prefix UTC and then import a `Get-Date` cmdlet, the cmdlet is known in the session as `Get-UTCDate`, and it is not confused with the original `Get-Date` cmdlet.</span></span>

<span data-ttu-id="9d428-360">此參數的值優先順序高於模組中指定預設前置詞的 **DefaultCommandPrefix** 屬性。</span><span class="sxs-lookup"><span data-stu-id="9d428-360">The value of this parameter takes precedence over the **DefaultCommandPrefix** property of the module, which specifies the default prefix.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9d428-361">-PSSession</span><span class="sxs-lookup"><span data-stu-id="9d428-361">-PSSession</span></span>

<span data-ttu-id="9d428-362">指定 PowerShell 使用者管理的會話 (**PSSession**) ，此 Cmdlet 會將模組匯入目前的會話中。</span><span class="sxs-lookup"><span data-stu-id="9d428-362">Specifies a PowerShell user-managed session (**PSSession**) from which this cmdlet imports modules into the current session.</span></span> <span data-ttu-id="9d428-363">輸入包含 **pssession** 的變數，或輸入可取得 **pssession** 的命令，例如 `Get-PSSession` 命令。</span><span class="sxs-lookup"><span data-stu-id="9d428-363">Enter a variable that contains a **PSSession** or a command that gets a **PSSession**, such as a `Get-PSSession` command.</span></span>

<span data-ttu-id="9d428-364">當您將不同工作階段的模組匯入到目前工作階段時，您可以使用目前的工作階段之模組的 Cmdlet，就如同您使用本機模組的 Cmdlet 一樣。</span><span class="sxs-lookup"><span data-stu-id="9d428-364">When you import a module from a different session into the current session, you can use the cmdlets from the module in the current session, just as you would use cmdlets from a local module.</span></span> <span data-ttu-id="9d428-365">使用遠端 Cmdlet 的命令會在遠端會話中執行，但遠端處理詳細資料是由 PowerShell 在背景中管理。</span><span class="sxs-lookup"><span data-stu-id="9d428-365">Commands that use the remote cmdlets run in the remote session, but the remoting details are managed in the background by PowerShell.</span></span>

<span data-ttu-id="9d428-366">此參數會使用 PowerShell 的隱含遠端功能。</span><span class="sxs-lookup"><span data-stu-id="9d428-366">This parameter uses the Implicit Remoting feature of PowerShell.</span></span> <span data-ttu-id="9d428-367">它相當於使用指令程式 `Import-PSSession` 從會話匯入特定模組。</span><span class="sxs-lookup"><span data-stu-id="9d428-367">It is equivalent to using the `Import-PSSession` cmdlet to import particular modules from a session.</span></span>

<span data-ttu-id="9d428-368">`Import-Module` 無法從另一個會話匯入 PowerShell Core 模組。</span><span class="sxs-lookup"><span data-stu-id="9d428-368">`Import-Module` cannot import PowerShell Core modules from another session.</span></span> <span data-ttu-id="9d428-369">PowerShell Core 的模組都有以 Microsoft. PowerShell 開頭的名稱。</span><span class="sxs-lookup"><span data-stu-id="9d428-369">The PowerShell Core modules have names that begin with Microsoft.PowerShell.</span></span>

<span data-ttu-id="9d428-370">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="9d428-370">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: PSSession, FullyQualifiedNameAndPSSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9d428-371">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="9d428-371">-RequiredVersion</span></span>

<span data-ttu-id="9d428-372">指定此 Cmdlet 匯入之模組的版本。</span><span class="sxs-lookup"><span data-stu-id="9d428-372">Specifies a version of the module that this cmdlet imports.</span></span> <span data-ttu-id="9d428-373">如果未安裝該版本，則會 `Import-Module` 產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="9d428-373">If the version is not installed, `Import-Module` generates an error.</span></span>

<span data-ttu-id="9d428-374">根據預設，匯 `Import-Module` 入模組時不會檢查版本號碼。</span><span class="sxs-lookup"><span data-stu-id="9d428-374">By default, `Import-Module` imports the module without checking the version number.</span></span>

<span data-ttu-id="9d428-375">若要指定最小版本，請使用 **MinimumVersion** 參數。</span><span class="sxs-lookup"><span data-stu-id="9d428-375">To specify a minimum version, use the **MinimumVersion** parameter.</span></span> <span data-ttu-id="9d428-376">您也可以使用 **#Requires** 關鍵字的 **module** 和 **Version** 參數，要求在腳本中使用特定版本的模組。</span><span class="sxs-lookup"><span data-stu-id="9d428-376">You can also use the **Module** and **Version** parameters of the **#Requires** keyword to require a specific version of a module in a script.</span></span>

<span data-ttu-id="9d428-377">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="9d428-377">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="9d428-378">使用 **RequiredVersion** 匯入隨附于現有 windows 作業系統版本之模組的腳本，不會在未來的 windows 作業系統版本中自動執行。</span><span class="sxs-lookup"><span data-stu-id="9d428-378">Scripts that use **RequiredVersion** to import modules that are included with existing releases of the Windows operating system don't automatically run in future releases of the Windows operating system.</span></span> <span data-ttu-id="9d428-379">這是因為在未來的 Windows 作業系統版本中，PowerShell 模組版本號碼高於現有 Windows 作業系統版本中的模組版本號碼。</span><span class="sxs-lookup"><span data-stu-id="9d428-379">This is because PowerShell module version numbers in future releases of the Windows operating system are higher than module version numbers in existing releases of the Windows operating system.</span></span>

```yaml
Type: System.Version
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9d428-380">-Scope</span><span class="sxs-lookup"><span data-stu-id="9d428-380">-Scope</span></span>

<span data-ttu-id="9d428-381">指定此 Cmdlet 匯入模組的範圍。</span><span class="sxs-lookup"><span data-stu-id="9d428-381">Specifies a scope into which this cmdlet imports the module.</span></span>

<span data-ttu-id="9d428-382">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="9d428-382">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="9d428-383">**Global**。</span><span class="sxs-lookup"><span data-stu-id="9d428-383">**Global**.</span></span> <span data-ttu-id="9d428-384">適用於工作階段中的所有命令。</span><span class="sxs-lookup"><span data-stu-id="9d428-384">Available to all commands in the session.</span></span> <span data-ttu-id="9d428-385">等同於 **Global** 參數。</span><span class="sxs-lookup"><span data-stu-id="9d428-385">Equivalent to the **Global** parameter.</span></span>
- <span data-ttu-id="9d428-386">**本機**。</span><span class="sxs-lookup"><span data-stu-id="9d428-386">**Local**.</span></span> <span data-ttu-id="9d428-387">只適用於目前的範圍。</span><span class="sxs-lookup"><span data-stu-id="9d428-387">Available only in the current scope.</span></span>

<span data-ttu-id="9d428-388">根據預設，當 `Import-Module` 從命令提示字元、腳本檔或 scriptblock 呼叫 Cmdlet 時，會將所有命令匯入到全域會話狀態。</span><span class="sxs-lookup"><span data-stu-id="9d428-388">By default, when `Import-Module` cmdlet is called from the command prompt, script file, or scriptblock, all the commands are imported into the global session state.</span></span> <span data-ttu-id="9d428-389">您可以使用 `-Scope Local` 參數將模組內容匯入至腳本或 scriptblock 範圍中。</span><span class="sxs-lookup"><span data-stu-id="9d428-389">You can use the `-Scope Local` parameter to import module content into the script or scriptblock scope.</span></span>

<span data-ttu-id="9d428-390">從其他模組叫用時，Cmdlet 會將 `Import-Module` 模組中的命令（包括從嵌套模組載入的命令）匯入至呼叫端的會話狀態。</span><span class="sxs-lookup"><span data-stu-id="9d428-390">When invoked from another module, `Import-Module` cmdlet imports the commands in a module, including commands from nested modules, into the caller's session state.</span></span> <span data-ttu-id="9d428-391">指定 `-Scope Global` 或 `-Global` 表示此 Cmdlet 會將模組匯入到全域會話狀態，使其可供會話中的所有命令使用。</span><span class="sxs-lookup"><span data-stu-id="9d428-391">Specifying `-Scope Global` or `-Global` indicates that this cmdlet imports modules into the global session state so they are available to all commands in the session.</span></span>

<span data-ttu-id="9d428-392">**Global** 參數等同於值為 **Global** 的 **Scope** 參數。</span><span class="sxs-lookup"><span data-stu-id="9d428-392">The **Global** parameter is equivalent to the **Scope** parameter with a value of **Global**.</span></span>

<span data-ttu-id="9d428-393">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="9d428-393">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Local, Global

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9d428-394">-Variable</span><span class="sxs-lookup"><span data-stu-id="9d428-394">-Variable</span></span>

<span data-ttu-id="9d428-395">指定此 Cmdlet 從模組匯入至目前會話的變數陣列。</span><span class="sxs-lookup"><span data-stu-id="9d428-395">Specifies an array of variables that this cmdlet imports from the module into the current session.</span></span>
<span data-ttu-id="9d428-396">輸入變數的清單。</span><span class="sxs-lookup"><span data-stu-id="9d428-396">Enter a list of variables.</span></span> <span data-ttu-id="9d428-397">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="9d428-397">Wildcard characters are permitted.</span></span>

<span data-ttu-id="9d428-398">當您匯入模組時，某些模組會自動將選取的變數匯出至您的工作階段。</span><span class="sxs-lookup"><span data-stu-id="9d428-398">Some modules automatically export selected variables into your session when you import the module.</span></span>
<span data-ttu-id="9d428-399">此參數可讓您從匯出的變數中選取。</span><span class="sxs-lookup"><span data-stu-id="9d428-399">This parameter lets you select from among the exported variables.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="9d428-400">-SkipEditionCheck</span><span class="sxs-lookup"><span data-stu-id="9d428-400">-SkipEditionCheck</span></span>

<span data-ttu-id="9d428-401">略過欄位的檢查 `CompatiblePSEditions` 。</span><span class="sxs-lookup"><span data-stu-id="9d428-401">Skips the check on the `CompatiblePSEditions` field.</span></span>

<span data-ttu-id="9d428-402">`"$($env:windir)\System32\WindowsPowerShell\v1.0\Modules"`當模組未 `Core` 在資訊清單欄位中指定時，允許從模組目錄將模組載入至 PowerShell Core `CompatiblePSEditions` 。</span><span class="sxs-lookup"><span data-stu-id="9d428-402">Allows loading a module from the `"$($env:windir)\System32\WindowsPowerShell\v1.0\Modules"` module directory into PowerShell Core when that module does not specify `Core` in the `CompatiblePSEditions` manifest field.</span></span>

<span data-ttu-id="9d428-403">從另一個路徑匯入模組時，此參數不會執行任何動作，因為不會執行檢查。</span><span class="sxs-lookup"><span data-stu-id="9d428-403">When importing a module from another path, this switch does nothing, since the check is not performed.</span></span> <span data-ttu-id="9d428-404">在 Linux 和 macOS 上，此參數不會執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="9d428-404">On Linux and macOS, this switch does nothing.</span></span>

<span data-ttu-id="9d428-405">如需詳細資訊，請參閱 [about_PowerShell_Editions](About/about_PowerShell_Editions.md)。</span><span class="sxs-lookup"><span data-stu-id="9d428-405">For more information, see [about_PowerShell_Editions](About/about_PowerShell_Editions.md).</span></span>

> [!WARNING]
> <span data-ttu-id="9d428-406">`Import-Module -SkipEditionCheck` 仍可能無法匯入模組。</span><span class="sxs-lookup"><span data-stu-id="9d428-406">`Import-Module -SkipEditionCheck` is still likely to fail to import a module.</span></span> <span data-ttu-id="9d428-407">即使成功，叫用模組中的命令稍後可能會在嘗試使用不相容的 API 時失敗。</span><span class="sxs-lookup"><span data-stu-id="9d428-407">Even if it does succeed, invoking a command from the module may later fail when it tries to use an incompatible API.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Name, PSSession, CimSession, FullyQualifiedNameAndPSSession, FullyQualifiedName, Assembly, ModuleInfo
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9d428-408">-UseWindowsPowerShell</span><span class="sxs-lookup"><span data-stu-id="9d428-408">-UseWindowsPowerShell</span></span>

<span data-ttu-id="9d428-409">使用 Windows PowerShell 相容性功能載入模組。</span><span class="sxs-lookup"><span data-stu-id="9d428-409">Loads module using Windows PowerShell Compatibility functionality.</span></span> <span data-ttu-id="9d428-410">如需詳細資訊，請參閱 [about_Windows_PowerShell_Compatibility](About/about_Windows_PowerShell_Compatibility.md) 。</span><span class="sxs-lookup"><span data-stu-id="9d428-410">See [about_Windows_PowerShell_Compatibility](About/about_Windows_PowerShell_Compatibility.md) for more information.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WinCompat, FullyQualifiedNameAndWinCompat
Aliases: UseWinPS

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9d428-411">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9d428-411">CommonParameters</span></span>

<span data-ttu-id="9d428-412">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="9d428-412">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9d428-413">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="9d428-413">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9d428-414">輸入</span><span class="sxs-lookup"><span data-stu-id="9d428-414">INPUTS</span></span>

### <span data-ttu-id="9d428-415">System.string，PSModuleInfo，System.string. Assembly （系統）</span><span class="sxs-lookup"><span data-stu-id="9d428-415">System.String, System.Management.Automation.PSModuleInfo, System.Reflection.Assembly</span></span>

<span data-ttu-id="9d428-416">您可以使用管線將模組名稱、模組物件或元件物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9d428-416">You can pipe a module name, module object, or assembly object to this cmdlet.</span></span>

## <span data-ttu-id="9d428-417">輸出</span><span class="sxs-lookup"><span data-stu-id="9d428-417">OUTPUTS</span></span>

### <span data-ttu-id="9d428-418">None、PSModuleInfo 或 PSCustomObject，或 Automation。</span><span class="sxs-lookup"><span data-stu-id="9d428-418">None, System.Management.Automation.PSModuleInfo, or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="9d428-419">依預設，不 `Import-Module` 會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="9d428-419">By default, `Import-Module` does not generate any output.</span></span> <span data-ttu-id="9d428-420">如果您指定 **PassThru** 參數，此 Cmdlet 會產生代表模組的 **PSModuleInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="9d428-420">If you specify the **PassThru** parameter, the cmdlet generates a **System.Management.Automation.PSModuleInfo** object that represents the module.</span></span> <span data-ttu-id="9d428-421">如果您指定 **AsCustomObject** 參數，它會產生 **PSCustomObject** 物件。</span><span class="sxs-lookup"><span data-stu-id="9d428-421">If you specify the **AsCustomObject** parameter, it generates a **PSCustomObject** object.</span></span>

## <span data-ttu-id="9d428-422">注意</span><span class="sxs-lookup"><span data-stu-id="9d428-422">NOTES</span></span>

- <span data-ttu-id="9d428-423">您必須先將模組安裝在本機電腦上，才能匯入模組。</span><span class="sxs-lookup"><span data-stu-id="9d428-423">Before you can import a module, the module must be installed on the local computer.</span></span> <span data-ttu-id="9d428-424">也就是說，必須將模組目錄複寫到本機電腦可以存取的目錄中。</span><span class="sxs-lookup"><span data-stu-id="9d428-424">That is, the module directory must be copied to a directory that is accessible to your local computer.</span></span> <span data-ttu-id="9d428-425">如需詳細資訊，請參閱 [about_Modules](About/about_Modules.md)。</span><span class="sxs-lookup"><span data-stu-id="9d428-425">For more information, see [about_Modules](About/about_Modules.md).</span></span>

  <span data-ttu-id="9d428-426">您也可以使用 **PSSession** 和 **CIMSession** 參數，匯入在遠端電腦安裝的模組。</span><span class="sxs-lookup"><span data-stu-id="9d428-426">You can also use the **PSSession** and **CIMSession** parameters to import modules that are installed on remote computers.</span></span> <span data-ttu-id="9d428-427">不過，在這些模組中使用 Cmdlet 的命令會在遠端電腦上的遠端會話中執行。</span><span class="sxs-lookup"><span data-stu-id="9d428-427">However, commands that use the cmdlets in these modules run in the remote session on the remote computer.</span></span>

- <span data-ttu-id="9d428-428">如果您將具有相同名稱和相同類型的成員匯入到您的會話中，則 PowerShell 預設會使用最後匯入的成員。</span><span class="sxs-lookup"><span data-stu-id="9d428-428">If you import members with the same name and the same type into your session, PowerShell uses the member imported last by default.</span></span> <span data-ttu-id="9d428-429">變數和別名會被取代，而且無法存取原始變數和別名。</span><span class="sxs-lookup"><span data-stu-id="9d428-429">Variables and aliases are replaced, and the originals aren't accessible.</span></span> <span data-ttu-id="9d428-430">函式、Cmdlet 和提供者只會由新成員遮蔽。</span><span class="sxs-lookup"><span data-stu-id="9d428-430">Functions, cmdlets, and providers are merely shadowed by the new members.</span></span> <span data-ttu-id="9d428-431">您可以使用嵌入式管理單元、模組或函式路徑的名稱來限定命令名稱來存取它們。</span><span class="sxs-lookup"><span data-stu-id="9d428-431">They can be accessed by qualifying the command name with the name of its snap-in, module, or function path.</span></span>

- <span data-ttu-id="9d428-432">若要更新已從模組匯入之命令的格式設定資料，請使用 `Update-FormatData` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9d428-432">To update the formatting data for commands that have been imported from a module, use the `Update-FormatData` cmdlet.</span></span> <span data-ttu-id="9d428-433">`Update-FormatData` 也會在會話中，針對從模組匯入的命令更新格式化資料。</span><span class="sxs-lookup"><span data-stu-id="9d428-433">`Update-FormatData` also updates the formatting data for commands in the session that were imported from modules.</span></span> <span data-ttu-id="9d428-434">如果模組的格式化檔案變更，您可以執行 `Update-FormatData` 命令來更新匯入命令的格式化資料。</span><span class="sxs-lookup"><span data-stu-id="9d428-434">If the formatting file for a module changes, you can run an `Update-FormatData` command to update the formatting data for imported commands.</span></span> <span data-ttu-id="9d428-435">您不需要再次匯入模組。</span><span class="sxs-lookup"><span data-stu-id="9d428-435">You don't need to import the module again.</span></span>

- <span data-ttu-id="9d428-436">從 Windows PowerShell 3.0 開始，隨 PowerShell 安裝的核心命令會封裝在模組中。</span><span class="sxs-lookup"><span data-stu-id="9d428-436">Starting in Windows PowerShell 3.0, the core commands that are installed with PowerShell are packaged in modules.</span></span> <span data-ttu-id="9d428-437">在 Windows PowerShell 2.0，以及在較新版本的 PowerShell 中建立舊版會話的主機程式中，會將核心命令封裝在嵌入式管理單元中， (**PSSnapins**) 。</span><span class="sxs-lookup"><span data-stu-id="9d428-437">In Windows PowerShell 2.0, and in host programs that create older-style sessions in later versions of PowerShell, the core commands are packaged in snap-ins (**PSSnapins**).</span></span> <span data-ttu-id="9d428-438">**Microsoft.PowerShell.Core** 是一個例外，它一律是一個嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="9d428-438">The exception is **Microsoft.PowerShell.Core**, which is always a snap-in.</span></span> <span data-ttu-id="9d428-439">此外，遠端會話（例如由 Cmdlet 啟動的會話） `New-PSSession` 都是包含核心嵌入式管理單元的較舊樣式會話。</span><span class="sxs-lookup"><span data-stu-id="9d428-439">Also, remote sessions, such as those started by the `New-PSSession` cmdlet, are older-style sessions that include core snap-ins.</span></span>

  <span data-ttu-id="9d428-440">如需使用核心模組建立較新樣式會話之 **CreateDefault2** 方法的詳細資訊，請參閱 [CreateDefault2 方法](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2)。</span><span class="sxs-lookup"><span data-stu-id="9d428-440">For information about the **CreateDefault2** method that creates newer-style sessions with core modules, see the [CreateDefault2 Method](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2).</span></span>

- <span data-ttu-id="9d428-441">在 Windows PowerShell 2.0 中，模組物件的某些屬性值（例如 **ExportedCmdlets** 和 **NestedModules** 屬性值），在匯入模組之前都不會填入。</span><span class="sxs-lookup"><span data-stu-id="9d428-441">In Windows PowerShell 2.0, some of the property values of the module object, such as the **ExportedCmdlets** and **NestedModules** property values, were not populated until the module was imported.</span></span>

- <span data-ttu-id="9d428-442">如果您嘗試匯入包含與 Windows PowerShell 3.0 + 不相容之混合模式元件的模組，則會傳回 `Import-Module` 類似下列的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="9d428-442">If you attempt to import a module that contains mixed-mode assemblies that aren't compatible with Windows PowerShell 3.0+, `Import-Module` returns an error message like the following one.</span></span>

  > <span data-ttu-id="9d428-443">Import-Module：混合模式元件是針對執行時間的版本 ' v 2.0.50727 ' 所建立，而且無法在4.0 執行時間中載入，而不需要額外的設定資訊。</span><span class="sxs-lookup"><span data-stu-id="9d428-443">Import-Module : Mixed mode assembly is built against version 'v2.0.50727' of the runtime and cannot be loaded in the 4.0 runtime without additional configuration information.</span></span>

  <span data-ttu-id="9d428-444">針對 Windows PowerShell 2.0 設計的模組至少包含一個混合模組元件時，就會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="9d428-444">This error occurs when a module that is designed for Windows PowerShell 2.0 contains at least one mixed-module assembly.</span></span> <span data-ttu-id="9d428-445">混合模組元件，其中包括 managed 和非 managed 程式碼，例如 c + + 和 c #。</span><span class="sxs-lookup"><span data-stu-id="9d428-445">A mixed-module assembly that includes both managed and non-managed code, such as C++ and C#.</span></span>

  <span data-ttu-id="9d428-446">若要匯入包含混合模式元件的模組，請使用下列命令啟動 Windows PowerShell 2.0，然後 `Import-Module` 再次嘗試命令。</span><span class="sxs-lookup"><span data-stu-id="9d428-446">To import a module that contains mixed-mode assemblies, start Windows PowerShell 2.0 by using the following command, and then try the `Import-Module` command again.</span></span>

  `PowerShell.exe -Version 2.0`

- <span data-ttu-id="9d428-447">若要使用 CIM 工作階段功能，遠端電腦必須具備 WS-Management 遠端功能和 Windows Management Instrumentation (WMI)，這是 Microsoft 實作的「通用訊息模型 (CIM)」標準。</span><span class="sxs-lookup"><span data-stu-id="9d428-447">To use the CIM session feature, the remote computer must have WS-Management remoting and Windows Management Instrumentation (WMI), which is the Microsoft implementation of the Common Information Model (CIM) standard.</span></span> <span data-ttu-id="9d428-448">電腦也必須擁有具有相同基本功能的「模組探索」WMI 提供者或替代 CIM 提供者。</span><span class="sxs-lookup"><span data-stu-id="9d428-448">The computer must also have the Module Discovery WMI provider or an alternate CIM provider that has the same basic features.</span></span>

  <span data-ttu-id="9d428-449">您可以在不是執行 Windows 作業系統的電腦上，以及在具有 PowerShell 但未啟用 PowerShell 遠端功能的 Windows 電腦上，使用 CIM 會話功能。</span><span class="sxs-lookup"><span data-stu-id="9d428-449">You can use the CIM session feature on computers that aren't running a Windows operating system and on Windows computers that have PowerShell, but don't have PowerShell remoting enabled.</span></span>

  <span data-ttu-id="9d428-450">您也可以使用 CIM 參數，從已啟用 PowerShell 遠端功能的電腦（包括本機電腦）取得 CIM 模組。</span><span class="sxs-lookup"><span data-stu-id="9d428-450">You can also use the CIM parameters to get CIM modules from computers that have PowerShell remoting enabled, including the local computer.</span></span> <span data-ttu-id="9d428-451">當您在本機電腦上建立 CIM 會話時，PowerShell 會使用 DCOM （而不是 WMI）來建立會話。</span><span class="sxs-lookup"><span data-stu-id="9d428-451">When you create a CIM session on the local computer, PowerShell uses DCOM, instead of WMI, to create the session.</span></span>

- <span data-ttu-id="9d428-452">根據預設，會 `Import-Module` 在全域範圍內匯入模組，即使是從子系範圍呼叫也一樣。</span><span class="sxs-lookup"><span data-stu-id="9d428-452">By default, `Import-Module` imports modules in the global scope even when called from a descendant scope.</span></span> <span data-ttu-id="9d428-453">最上層範圍和所有子代範圍都可以存取模組的匯出元素。</span><span class="sxs-lookup"><span data-stu-id="9d428-453">The top-level scope and all descendant scopes have access to the module's exported elements.</span></span>

  <span data-ttu-id="9d428-454">在子代範圍中， `-Scope Local` 將匯入限制在該範圍及其所有子系範圍內。</span><span class="sxs-lookup"><span data-stu-id="9d428-454">In a descendant scope, `-Scope Local` limits the import to that scope and all its descendant scopes.</span></span> <span data-ttu-id="9d428-455">父範圍接著看不到匯入的成員。</span><span class="sxs-lookup"><span data-stu-id="9d428-455">Parent scopes then do not see the imported members.</span></span>

  > [!NOTE]
  > <span data-ttu-id="9d428-456">`Get-Module` 顯示目前會話中載入的所有模組。</span><span class="sxs-lookup"><span data-stu-id="9d428-456">`Get-Module` shows all modules loaded in the current session.</span></span> <span data-ttu-id="9d428-457">這包括在子系範圍中本機載入的模組。</span><span class="sxs-lookup"><span data-stu-id="9d428-457">This includes modules loaded locally in a descendant scope.</span></span> <span data-ttu-id="9d428-458">使用 `Get-Command -Module modulename` 以查看哪些成員會在目前的範圍中載入。</span><span class="sxs-lookup"><span data-stu-id="9d428-458">Use `Get-Command -Module modulename` to see which members are loaded in the current scope.</span></span>

  <span data-ttu-id="9d428-459">`Import-Module` 未在模組中載入類別和列舉定義。</span><span class="sxs-lookup"><span data-stu-id="9d428-459">`Import-Module` does not load class and enum definitions in the module.</span></span> <span data-ttu-id="9d428-460">使用 `using module` 腳本開頭的語句。</span><span class="sxs-lookup"><span data-stu-id="9d428-460">Use the `using module` statement at the beginning of your script.</span></span> <span data-ttu-id="9d428-461">這會匯入模組，包括類別和列舉定義。</span><span class="sxs-lookup"><span data-stu-id="9d428-461">This imports the module, including the class and enum definitions.</span></span> <span data-ttu-id="9d428-462">如需詳細資訊，請參閱 [about_Using](About/about_Using.md)。</span><span class="sxs-lookup"><span data-stu-id="9d428-462">For more information, see [about_Using](About/about_Using.md).</span></span>

## <span data-ttu-id="9d428-463">相關連結</span><span class="sxs-lookup"><span data-stu-id="9d428-463">RELATED LINKS</span></span>

[<span data-ttu-id="9d428-464">about_Modules</span><span class="sxs-lookup"><span data-stu-id="9d428-464">about_Modules</span></span>](about/about_Modules.md)

[<span data-ttu-id="9d428-465">Export-ModuleMember</span><span class="sxs-lookup"><span data-stu-id="9d428-465">Export-ModuleMember</span></span>](Export-ModuleMember.md)

[<span data-ttu-id="9d428-466">Get-Module</span><span class="sxs-lookup"><span data-stu-id="9d428-466">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="9d428-467">New-Module</span><span class="sxs-lookup"><span data-stu-id="9d428-467">New-Module</span></span>](New-Module.md)

[<span data-ttu-id="9d428-468">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="9d428-468">Remove-Module</span></span>](Remove-Module.md)

[<span data-ttu-id="9d428-469">about_PowerShell_Editions</span><span class="sxs-lookup"><span data-stu-id="9d428-469">about_PowerShell_Editions</span></span>](About/about_PowerShell_Editions.md)
