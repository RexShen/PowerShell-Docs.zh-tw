---
description: 說明如何在 PowerShell 中存取 Windows 環境變數。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_environment_variables?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Environment_Variables
ms.openlocfilehash: 3004e01e59d30005ad2fbfa92897f43471a41384
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208044"
---
# <a name="about-environment-variables"></a><span data-ttu-id="047b6-104">關於環境變數</span><span class="sxs-lookup"><span data-stu-id="047b6-104">About Environment Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="047b6-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="047b6-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="047b6-106">說明如何在 PowerShell 中存取 Windows 環境變數。</span><span class="sxs-lookup"><span data-stu-id="047b6-106">Describes how to access Windows environment variables in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="047b6-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="047b6-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="047b6-108">環境變數會儲存作業系統環境的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="047b6-108">Environment variables store information about the operating system environment.</span></span> <span data-ttu-id="047b6-109">這項資訊包含詳細資料，例如作業系統路徑、作業系統所使用的處理器數目，以及暫存資料夾的位置。</span><span class="sxs-lookup"><span data-stu-id="047b6-109">This information includes details such as the operating system path, the number of processors used by the operating system, and the location of temporary folders.</span></span>

<span data-ttu-id="047b6-110">環境變數會儲存作業系統和其他程式所使用的資料。</span><span class="sxs-lookup"><span data-stu-id="047b6-110">The environment variables store data that is used by the operating system and other programs.</span></span> <span data-ttu-id="047b6-111">例如， `WINDIR` 環境變數包含 Windows 安裝目錄的位置。</span><span class="sxs-lookup"><span data-stu-id="047b6-111">For example, the `WINDIR` environment variable contains the location of the Windows installation directory.</span></span> <span data-ttu-id="047b6-112">程式可以查詢此變數的值，以判斷 Windows 作業系統檔案的所在位置。</span><span class="sxs-lookup"><span data-stu-id="047b6-112">Programs can query the value of this variable to determine where Windows operating system files are located.</span></span>

<span data-ttu-id="047b6-113">PowerShell 可以存取和管理任何支援的作業系統平臺中的環境變數。</span><span class="sxs-lookup"><span data-stu-id="047b6-113">PowerShell can access and manage environment variables in any of the supported operating system platforms.</span></span> <span data-ttu-id="047b6-114">PowerShell 環境提供者可讓您輕鬆地查看和變更環境變數，以簡化此程式。</span><span class="sxs-lookup"><span data-stu-id="047b6-114">The PowerShell environment provider simplifies this process by making it easy to view and change environment variables.</span></span>

<span data-ttu-id="047b6-115">環境變數與 PowerShell 中其他類型的變數不同，子進程會繼承這些變數，例如本機背景工作和模組成員執行所在的會話。</span><span class="sxs-lookup"><span data-stu-id="047b6-115">Environment variables, unlike other types of variables in PowerShell, are inherited by child processes, such as local background jobs and the sessions in which module members run.</span></span> <span data-ttu-id="047b6-116">這會使環境變數非常適合用來儲存父和子進程中所需的值。</span><span class="sxs-lookup"><span data-stu-id="047b6-116">This makes environment variables well suited to storing values that are needed in both parent and child processes.</span></span>

## <a name="using-and-changing-environment-variables"></a><span data-ttu-id="047b6-117">使用和變更環境變數</span><span class="sxs-lookup"><span data-stu-id="047b6-117">Using and changing environment variables</span></span>

<span data-ttu-id="047b6-118">在 Windows 中，可以在三個範圍內定義環境變數：</span><span class="sxs-lookup"><span data-stu-id="047b6-118">On Windows, environment variables can be defined in three scopes:</span></span>

- <span data-ttu-id="047b6-119">電腦 (或系統) 範圍</span><span class="sxs-lookup"><span data-stu-id="047b6-119">Machine (or System) scope</span></span>
- <span data-ttu-id="047b6-120">使用者範圍</span><span class="sxs-lookup"><span data-stu-id="047b6-120">User scope</span></span>
- <span data-ttu-id="047b6-121">進程範圍</span><span class="sxs-lookup"><span data-stu-id="047b6-121">Process scope</span></span>

<span data-ttu-id="047b6-122">_進程_ 範圍包含目前進程或 PowerShell 會話中可用的環境變數。</span><span class="sxs-lookup"><span data-stu-id="047b6-122">The _Process_ scope contains the environment variables available in the current process, or PowerShell session.</span></span> <span data-ttu-id="047b6-123">這份變數清單繼承自父進程，而且是由 _電腦_ 和 _使用者_ 範圍中的變數所構成。</span><span class="sxs-lookup"><span data-stu-id="047b6-123">This list of variables is inherited from the parent process and is constructed from the variables in the _Machine_ and _User_ scopes.</span></span>

<span data-ttu-id="047b6-124">您可以使用變數語法搭配環境提供者來顯示和變更環境變數的值，而不使用 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="047b6-124">You can display and change the values of environment variables without using a cmdlet by using a variable syntax with the environment provider.</span></span> <span data-ttu-id="047b6-125">若要顯示環境變數的值，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="047b6-125">To display the value of an environment variable, use the following syntax:</span></span>

```
$Env:<variable-name>
```

<span data-ttu-id="047b6-126">例如，若要顯示環境變數的值 `WINDIR` ，請在 PowerShell 命令提示字元中輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="047b6-126">For example, to display the value of the `WINDIR` environment variable, type the following command at the PowerShell command prompt:</span></span>

```powershell
$Env:windir
```

<span data-ttu-id="047b6-127">在此語法中，貨幣符號 (`$`) 表示變數，而磁片磁碟機名稱 (`Env:`) 表示環境變數，後面接著變數名稱 (`windir`) 。</span><span class="sxs-lookup"><span data-stu-id="047b6-127">In this syntax, the dollar sign (`$`) indicates a variable, and the drive name (`Env:`) indicates an environment variable followed by the variable name (`windir`).</span></span>

<span data-ttu-id="047b6-128">當您在 PowerShell 中變更環境變數時，變更只會影響目前的會話。</span><span class="sxs-lookup"><span data-stu-id="047b6-128">When you change environment variables in PowerShell, the change affects only the current session.</span></span> <span data-ttu-id="047b6-129">此行為類似于 `Set` Windows 命令 Shell 中命令的行為，以及 `Setenv` UNIX 環境中的命令。</span><span class="sxs-lookup"><span data-stu-id="047b6-129">This behavior resembles the behavior of the `Set` command in the Windows Command Shell and the `Setenv` command in UNIX-based environments.</span></span> <span data-ttu-id="047b6-130">若要變更電腦或使用者範圍中的值，您必須使用 **System. 環境** 類別的方法。</span><span class="sxs-lookup"><span data-stu-id="047b6-130">To change values in the Machine or User scopes, you must use the methods of the **System.Environment** class.</span></span>

<span data-ttu-id="047b6-131">若要變更電腦範圍變數，也必須具有許可權。</span><span class="sxs-lookup"><span data-stu-id="047b6-131">To make changes to Machine-scoped variables, must also have permission.</span></span> <span data-ttu-id="047b6-132">如果您嘗試在沒有足夠許可權的情況下變更值，此命令將會失敗，且 PowerShell 會顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="047b6-132">If you try to change a value without sufficient permission, the command fails and PowerShell displays an error.</span></span>

<span data-ttu-id="047b6-133">您可以使用下列語法來變更變數的值，而不使用 Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="047b6-133">You can change the values of variables without using a cmdlet using the following syntax:</span></span>

```powershell
$Env:<variable-name> = "<new-value>"
```

<span data-ttu-id="047b6-134">例如，若要附加 `;c:\temp` 至環境變數的值 `Path` ，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="047b6-134">For example, to append `;c:\temp` to the value of the `Path` environment variable, use the following syntax:</span></span>

```powershell
$Env:Path += ";c:\temp"
```

<span data-ttu-id="047b6-135">您也可以使用 Item Cmdlet （例如 `Set-Item` 、和） `Remove-Item` `Copy-Item` 來變更環境變數的值。</span><span class="sxs-lookup"><span data-stu-id="047b6-135">You can also use the Item cmdlets, such as `Set-Item`, `Remove-Item`, and `Copy-Item` to change the values of environment variables.</span></span> <span data-ttu-id="047b6-136">例如，若要使用 `Set-Item` Cmdlet 附加 `;c:\temp` 至 `Path` 環境變數的值，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="047b6-136">For example, to use the `Set-Item` cmdlet to append `;c:\temp` to the value of the `Path` environment variable, use the following syntax:</span></span>

```powershell
Set-Item -Path Env:Path -Value ($Env:Path + ";C:\Temp")
```

<span data-ttu-id="047b6-137">在此命令中，值會以括弧括住，以將其解釋為一個單位。</span><span class="sxs-lookup"><span data-stu-id="047b6-137">In this command, the value is enclosed in parentheses so that it is interpreted as a unit.</span></span>

## <a name="environment-variables-that-store-preferences"></a><span data-ttu-id="047b6-138">儲存喜好設定的環境變數</span><span class="sxs-lookup"><span data-stu-id="047b6-138">Environment variables that store preferences</span></span>

<span data-ttu-id="047b6-139">PowerShell 功能可以使用環境變數來儲存使用者喜好設定。</span><span class="sxs-lookup"><span data-stu-id="047b6-139">PowerShell features can use environment variables to store user preferences.</span></span>
<span data-ttu-id="047b6-140">這些變數的運作方式類似喜好設定變數，但它們是由其建立所在之會話的子會話所繼承。</span><span class="sxs-lookup"><span data-stu-id="047b6-140">These variables work like preference variables, but they are inherited by child sessions of the sessions in which they are created.</span></span> <span data-ttu-id="047b6-141">如需喜好設定變數的詳細資訊，請參閱 [about_preference_variables](about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="047b6-141">For more information about preference variables, see [about_preference_variables](about_Preference_Variables.md).</span></span>

<span data-ttu-id="047b6-142">儲存喜好設定的環境變數包括：</span><span class="sxs-lookup"><span data-stu-id="047b6-142">The environment variables that store preferences include:</span></span>

- <span data-ttu-id="047b6-143">PSExecutionPolicyPreference</span><span class="sxs-lookup"><span data-stu-id="047b6-143">PSExecutionPolicyPreference</span></span>

  <span data-ttu-id="047b6-144">儲存目前會話的執行原則集。</span><span class="sxs-lookup"><span data-stu-id="047b6-144">Stores the execution policy set for the current session.</span></span> <span data-ttu-id="047b6-145">只有當您為單一會話設定執行原則時，才會有這個環境變數。</span><span class="sxs-lookup"><span data-stu-id="047b6-145">This environment variable exists only when you set an execution policy for a single session.</span></span>
  <span data-ttu-id="047b6-146">您可以透過兩種不同的方式來完成這項作業。</span><span class="sxs-lookup"><span data-stu-id="047b6-146">You can do this in two different ways.</span></span>

  - <span data-ttu-id="047b6-147">從命令列使用 **ExecutionPolicy** 參數來設定會話的執行原則，以啟動會話。</span><span class="sxs-lookup"><span data-stu-id="047b6-147">Start a session from the command line using the **ExecutionPolicy** parameter to set the execution policy for the session.</span></span>

  - <span data-ttu-id="047b6-148">使用 `Set-ExecutionPolicy` 指令程式。</span><span class="sxs-lookup"><span data-stu-id="047b6-148">Use the `Set-ExecutionPolicy` cmdlet.</span></span> <span data-ttu-id="047b6-149">使用具有 "Process" 值的 Scope 參數。</span><span class="sxs-lookup"><span data-stu-id="047b6-149">Use the Scope parameter with a value of "Process".</span></span>

    <span data-ttu-id="047b6-150">如需詳細資訊，請參閱 [about_Execution_Policies](about_Execution_Policies.md)。</span><span class="sxs-lookup"><span data-stu-id="047b6-150">For more information, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

- <span data-ttu-id="047b6-151">PSModuleAnalysisCachePath</span><span class="sxs-lookup"><span data-stu-id="047b6-151">PSModuleAnalysisCachePath</span></span>

  <span data-ttu-id="047b6-152">PowerShell 可讓您控制用來快取模組及其 Cmdlet 相關資料的檔案。</span><span class="sxs-lookup"><span data-stu-id="047b6-152">PowerShell provides control over the file that is used to cache data about modules and their cmdlets.</span></span> <span data-ttu-id="047b6-153">當您搜尋命令時，會在啟動時讀取快取，而且在匯入模組之後，會在背景執行緒上寫入快取。</span><span class="sxs-lookup"><span data-stu-id="047b6-153">The cache is read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

  <span data-ttu-id="047b6-154">快取的預設位置為：</span><span class="sxs-lookup"><span data-stu-id="047b6-154">Default location of the cache is:</span></span>

  - `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell`

  <span data-ttu-id="047b6-155">快取的預設檔案名為 `ModuleAnalysisCache` 。</span><span class="sxs-lookup"><span data-stu-id="047b6-155">The default filename for the cache is `ModuleAnalysisCache`.</span></span> <span data-ttu-id="047b6-156">若要變更快取的預設位置，請在啟動 PowerShell 之前設定環境變數。</span><span class="sxs-lookup"><span data-stu-id="047b6-156">To change the default location of the cache, set the environment variable before starting PowerShell.</span></span> <span data-ttu-id="047b6-157">對此環境變數所做的變更只會影響子進程。</span><span class="sxs-lookup"><span data-stu-id="047b6-157">Changes to this environment variable only affect child processes.</span></span>
  <span data-ttu-id="047b6-158">該值應該命名 PowerShell 有權建立和寫入檔案的完整路徑 (包括檔名)。</span><span class="sxs-lookup"><span data-stu-id="047b6-158">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span>

  > [!NOTE]
  > <span data-ttu-id="047b6-159">如果命令探索無法正常運作，例如 Intellisense 會顯示不存在的命令，您可以刪除快取檔案。</span><span class="sxs-lookup"><span data-stu-id="047b6-159">If command discovery isn't working correctly, for example Intellisense shows commands that don't exist, you can delete the cache file.</span></span> <span data-ttu-id="047b6-160">下次您啟動 PowerShell 時，即會重新建立快取。</span><span class="sxs-lookup"><span data-stu-id="047b6-160">The cache is recreated the next time you start PowerShell.</span></span>

  <span data-ttu-id="047b6-161">若要停用檔案快取，請將此值設定於無效的位置，例如︰</span><span class="sxs-lookup"><span data-stu-id="047b6-161">To disable the file cache, set this value to an invalid location, for example:</span></span>

  ```powershell
  # `NUL` here is a special device on Windows that cannot be written to
  $env:PSModuleAnalysisCachePath = 'NUL'
  ```

  <span data-ttu-id="047b6-162">這會設定 **NUL** 裝置的路徑。</span><span class="sxs-lookup"><span data-stu-id="047b6-162">This sets the path to the **NUL** device.</span></span> <span data-ttu-id="047b6-163">PowerShell 無法寫入路徑，但不會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="047b6-163">PowerShell can't write to the path but no error is returned.</span></span> <span data-ttu-id="047b6-164">您可以使用追蹤來查看報告的錯誤：</span><span class="sxs-lookup"><span data-stu-id="047b6-164">You can see the errors reported using a tracer:</span></span>

  ```powershell
  Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
  ```

- <span data-ttu-id="047b6-165">PSDisableModuleAnalysisCacheCleanup</span><span class="sxs-lookup"><span data-stu-id="047b6-165">PSDisableModuleAnalysisCacheCleanup</span></span>

  <span data-ttu-id="047b6-166">寫出模組分析快取時，PowerShell 會檢查不再存在的模組，以避免不必要的大型快取。</span><span class="sxs-lookup"><span data-stu-id="047b6-166">When writing out the module analysis cache, PowerShell checks for modules that no longer exist to avoid an unnecessarily large cache.</span></span> <span data-ttu-id="047b6-167">有時不需要這些檢查，在此情況下，您可以藉由將此環境變數值設定為來關閉這些檢查 `1` 。</span><span class="sxs-lookup"><span data-stu-id="047b6-167">Sometimes these checks are not desirable, in which case you can turn them off by setting this environment variable value to `1`.</span></span>

  <span data-ttu-id="047b6-168">設定此環境變數會立即在目前的進程中生效。</span><span class="sxs-lookup"><span data-stu-id="047b6-168">Setting this environment variable takes effect immediately in the current process.</span></span>

- <span data-ttu-id="047b6-169">PSModulePath</span><span class="sxs-lookup"><span data-stu-id="047b6-169">PSModulePath</span></span>

  <span data-ttu-id="047b6-170">`$env:PSModulePath`環境變數包含要搜尋以尋找模組和資源的資料夾位置清單。</span><span class="sxs-lookup"><span data-stu-id="047b6-170">The `$env:PSModulePath` environment variable contains a list of folder locations that are searched to find modules and resources.</span></span>

  <span data-ttu-id="047b6-171">依預設，指派給的有效位置 `$env:PSModulePath` 為：</span><span class="sxs-lookup"><span data-stu-id="047b6-171">By default, the effective locations assigned to `$env:PSModulePath` are:</span></span>

  - <span data-ttu-id="047b6-172">全系統位置：這些資料夾包含 PowerShell 隨附的模組。</span><span class="sxs-lookup"><span data-stu-id="047b6-172">System-wide locations: These folders contain modules that ship with PowerShell.</span></span> <span data-ttu-id="047b6-173">這些模組會儲存在 `$PSHOME\Modules` 位置中。</span><span class="sxs-lookup"><span data-stu-id="047b6-173">The modules are store in the `$PSHOME\Modules` location.</span></span> <span data-ttu-id="047b6-174">此外，這是安裝 Windows 管理模組的位置。</span><span class="sxs-lookup"><span data-stu-id="047b6-174">Also, This is the location where the Windows management modules are installed.</span></span>

  - <span data-ttu-id="047b6-175">使用者安裝的模組：這些是使用者所安裝的模組。</span><span class="sxs-lookup"><span data-stu-id="047b6-175">User-installed modules: These are modules installed by the user.</span></span>
    <span data-ttu-id="047b6-176">`Install-Module` 具有 **範圍** 參數，可讓您指定是否為目前的使用者或所有使用者安裝模組。</span><span class="sxs-lookup"><span data-stu-id="047b6-176">`Install-Module` has a **Scope** parameter that allows you to specify whether the module is installed for the current user or for all users.</span></span> <span data-ttu-id="047b6-177">如需詳細資訊，請參閱 [Install 模組](xref:PowerShellGet.Install-Module)。</span><span class="sxs-lookup"><span data-stu-id="047b6-177">For more information, see [Install-Module](xref:PowerShellGet.Install-Module).</span></span>

    - <span data-ttu-id="047b6-178">在 Windows 中，使用者專屬 **CurrentUser** 範圍的位置是 `$HOME\Documents\PowerShell\Modules` 資料夾。</span><span class="sxs-lookup"><span data-stu-id="047b6-178">On Windows, the location of the user-specific **CurrentUser** scope is the `$HOME\Documents\PowerShell\Modules` folder.</span></span> <span data-ttu-id="047b6-179">**AllUsers** 範圍的位置是 `$env:ProgramFiles\PowerShell\Modules` 。</span><span class="sxs-lookup"><span data-stu-id="047b6-179">The location of the **AllUsers** scope is `$env:ProgramFiles\PowerShell\Modules`.</span></span>

  <span data-ttu-id="047b6-180">此外，在其他目錄中安裝模組的安裝程式（例如 [Program Files] 目錄）可以將其位置附加至的值 `$env:PSModulePath` 。</span><span class="sxs-lookup"><span data-stu-id="047b6-180">In addition, setup programs that install modules in other directories, such as the Program Files directory, can append their locations to the value of `$env:PSModulePath`.</span></span>

  <span data-ttu-id="047b6-181">如需詳細資訊，請參閱 [about_PSModulePath](about_PSModulePath.md)。</span><span class="sxs-lookup"><span data-stu-id="047b6-181">For more information, see [about_PSModulePath](about_PSModulePath.md).</span></span>

## <a name="managing-environment-variables"></a><span data-ttu-id="047b6-182">管理環境變數</span><span class="sxs-lookup"><span data-stu-id="047b6-182">Managing environment variables</span></span>

<span data-ttu-id="047b6-183">PowerShell 提供數種不同的方法來管理環境變數。</span><span class="sxs-lookup"><span data-stu-id="047b6-183">PowerShell provides several different methods for managing environment variables.</span></span>

- <span data-ttu-id="047b6-184">環境提供者磁片磁碟機</span><span class="sxs-lookup"><span data-stu-id="047b6-184">The Environment provider drive</span></span>
- <span data-ttu-id="047b6-185">Item Cmdlet</span><span class="sxs-lookup"><span data-stu-id="047b6-185">The Item cmdlets</span></span>
- <span data-ttu-id="047b6-186">.NET **System. 環境** 類別</span><span class="sxs-lookup"><span data-stu-id="047b6-186">The .NET **System.Environment** class</span></span>
- <span data-ttu-id="047b6-187">在 Windows 中，系統主控台</span><span class="sxs-lookup"><span data-stu-id="047b6-187">On Windows, the System Control Panel</span></span>

### <a name="using-the-environment-provider"></a><span data-ttu-id="047b6-188">使用環境提供者</span><span class="sxs-lookup"><span data-stu-id="047b6-188">Using the Environment provider</span></span>

<span data-ttu-id="047b6-189">每個環境變數都會以 **DictionaryEntry** 類別的實例來表示。</span><span class="sxs-lookup"><span data-stu-id="047b6-189">Each environment variable is represented by an instance of the **System.Collections.DictionaryEntry** class.</span></span> <span data-ttu-id="047b6-190">在每個 **DictionaryEntry** 物件中，環境變數的名稱是字典索引鍵。</span><span class="sxs-lookup"><span data-stu-id="047b6-190">In each **DictionaryEntry** object, the name of the environment variable is the dictionary key.</span></span> <span data-ttu-id="047b6-191">變數的值是字典值。</span><span class="sxs-lookup"><span data-stu-id="047b6-191">The value of the variable is the dictionary value.</span></span>

<span data-ttu-id="047b6-192">若要在 PowerShell 中顯示代表環境變數之物件的屬性和方法，請使用 `Get-Member` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="047b6-192">To display the properties and methods of the object that represents an environment variable in PowerShell, use the `Get-Member` cmdlet.</span></span> <span data-ttu-id="047b6-193">例如，若要顯示磁片磁碟機中所有物件的方法和屬性 `Env:` ，請輸入：</span><span class="sxs-lookup"><span data-stu-id="047b6-193">For example, to display the methods and properties of all the objects in the `Env:` drive, type:</span></span>

```powershell
Get-Item -Path Env:* | Get-Member
```

<span data-ttu-id="047b6-194">PowerShell 環境提供者可讓您存取 PowerShell 磁片磁碟機中的環境變數 (`Env:` 磁片磁碟機) 。</span><span class="sxs-lookup"><span data-stu-id="047b6-194">The PowerShell Environment provider lets you access environment variables in a PowerShell drive (the `Env:` drive).</span></span> <span data-ttu-id="047b6-195">此磁片磁碟機看起來很像檔案系統磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="047b6-195">This drive looks much like a file system drive.</span></span> <span data-ttu-id="047b6-196">若要移至 `Env:` 磁片磁碟機，請輸入：</span><span class="sxs-lookup"><span data-stu-id="047b6-196">To go to the `Env:` drive, type:</span></span>

```powershell
Set-Location Env:
```

<span data-ttu-id="047b6-197">使用 Content Cmdlet 來取得或設定環境變數的值。</span><span class="sxs-lookup"><span data-stu-id="047b6-197">Use the Content cmdlets to get or set the values of an environment variable.</span></span>

```powershell
PS Env:\> Set-Content -Path Test -Value 'Test value'
PS Env:\> Get-Content -Path Test
Test value
```

<span data-ttu-id="047b6-198">您可以 `Env:` 從任何其他 PowerShell 磁片磁碟機查看磁片磁碟機中的環境變數，也可以移至 `Env:` 磁片磁碟機來查看和變更環境變數。</span><span class="sxs-lookup"><span data-stu-id="047b6-198">You can view the environment variables in the `Env:` drive from any other PowerShell drive, and you can go into the `Env:` drive to view and change the environment variables.</span></span>

### <a name="using-item-cmdlets"></a><span data-ttu-id="047b6-199">使用 Item Cmdlet</span><span class="sxs-lookup"><span data-stu-id="047b6-199">Using Item cmdlets</span></span>

<span data-ttu-id="047b6-200">當您參考環境變數時，請輸入 `Env:` 磁片磁碟機名稱，後面接著變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="047b6-200">When you refer to an environment variable, type the `Env:` drive name followed by the name of the variable.</span></span> <span data-ttu-id="047b6-201">例如，若要顯示環境變數的值 `COMPUTERNAME` ，請輸入：</span><span class="sxs-lookup"><span data-stu-id="047b6-201">For example, to display the value of the `COMPUTERNAME` environment variable, type:</span></span>

```powershell
Get-ChildItem Env:Computername
```

<span data-ttu-id="047b6-202">若要顯示所有環境變數的值，請輸入：</span><span class="sxs-lookup"><span data-stu-id="047b6-202">To display the values of all the environment variables, type:</span></span>

```powershell
Get-ChildItem Env:
```

<span data-ttu-id="047b6-203">由於環境變數沒有子專案，因此的輸出也 `Get-Item` `Get-ChildItem` 相同。</span><span class="sxs-lookup"><span data-stu-id="047b6-203">Because environment variables do not have child items, the output of `Get-Item` and `Get-ChildItem` is the same.</span></span>

<span data-ttu-id="047b6-204">根據預設，PowerShell 會依照其抓取環境變數的順序來顯示。</span><span class="sxs-lookup"><span data-stu-id="047b6-204">By default, PowerShell displays the environment variables in the order in which it retrieves them.</span></span> <span data-ttu-id="047b6-205">若要依變數名稱排序環境變數的清單，請使用管線將命令的輸出傳送 `Get-ChildItem` 至 `Sort-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="047b6-205">To sort the list of environment variables by variable name, pipe the output of a `Get-ChildItem` command to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="047b6-206">例如，從任何 PowerShell 磁片磁碟機，輸入：</span><span class="sxs-lookup"><span data-stu-id="047b6-206">For example, from any PowerShell drive, type:</span></span>

```powershell
Get-ChildItem Env: | Sort Name
```

<span data-ttu-id="047b6-207">您也可以 `Env:` 使用 Cmdlet 移至磁片磁碟機 `Set-Location` ：</span><span class="sxs-lookup"><span data-stu-id="047b6-207">You can also go into the `Env:` drive by using the `Set-Location` cmdlet:</span></span>

```powershell
Set-Location Env:
```

<span data-ttu-id="047b6-208">當您位於 `Env:` 磁片磁碟機時，您可以省略路徑中的 `Env:` 磁片磁碟機名稱。</span><span class="sxs-lookup"><span data-stu-id="047b6-208">When you are in the `Env:` drive, you can omit the `Env:` drive name from the path.</span></span> <span data-ttu-id="047b6-209">例如，若要顯示所有環境變數，請輸入：</span><span class="sxs-lookup"><span data-stu-id="047b6-209">For example, to display all the environment variables, type:</span></span>

```powershell
PS Env:\> Get-ChildItem
```

<span data-ttu-id="047b6-210">若要顯示 `COMPUTERNAME` 磁片磁碟機中的變數值 `Env:` ，請輸入：</span><span class="sxs-lookup"><span data-stu-id="047b6-210">To display the value of the `COMPUTERNAME` variable from within the `Env:` drive, type:</span></span>

```powershell
PS Env:\> Get-ChildItem ComputerName
```

### <a name="saving-changes-to-environment-variables"></a><span data-ttu-id="047b6-211">將變更儲存至環境變數</span><span class="sxs-lookup"><span data-stu-id="047b6-211">Saving changes to environment variables</span></span>

<span data-ttu-id="047b6-212">若要對 Windows 上的環境變數進行持續變更，請使用系統主控台。</span><span class="sxs-lookup"><span data-stu-id="047b6-212">To make a persistent change to an environment variable on Windows, use the System Control Panel.</span></span> <span data-ttu-id="047b6-213">選取 [ **Advanced System Settings** ]。</span><span class="sxs-lookup"><span data-stu-id="047b6-213">Select **Advanced System Settings** .</span></span> <span data-ttu-id="047b6-214">在 [ **Advanced （Advanced** ）] 索引標籤上，按一下 [ **環境變數 ...** ]。您可以在 **使用者** 和 **系統** (機) 範圍中新增或編輯現有的環境變數。</span><span class="sxs-lookup"><span data-stu-id="047b6-214">On the **Advanced** tab, click **Environment Variable...** . You can add or edit existing environment variables in the **User** and **System** (Machine) scopes.</span></span> <span data-ttu-id="047b6-215">Windows 會將這些值寫入登錄，以便在會話和系統重新開機期間保存這些值。</span><span class="sxs-lookup"><span data-stu-id="047b6-215">Windows writes these values to the Registry so that they persist across sessions and system restarts.</span></span>

<span data-ttu-id="047b6-216">或者，您也可以在 PowerShell 設定檔中新增或變更環境變數。</span><span class="sxs-lookup"><span data-stu-id="047b6-216">Alternately, you can add or change environment variables in your PowerShell profile.</span></span> <span data-ttu-id="047b6-217">此方法適用于任何支援平臺上的任何 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="047b6-217">This method works for any version of PowerShell on any supported platform.</span></span>

### <a name="using-systemenvironment-methods"></a><span data-ttu-id="047b6-218">使用 System. 環境方法</span><span class="sxs-lookup"><span data-stu-id="047b6-218">Using System.Environment methods</span></span>

<span data-ttu-id="047b6-219">**System. 環境** 類別提供 **GetEnvironmentVariable** 和 **SetEnvironmentVariable** 方法，可讓您指定變數的範圍。</span><span class="sxs-lookup"><span data-stu-id="047b6-219">The **System.Environment** class provides **GetEnvironmentVariable** and **SetEnvironmentVariable** methods that allow you to specify the scope of the variable.</span></span>

<span data-ttu-id="047b6-220">下列範例會使用 **GetEnvironmentVariable** 方法來取得的電腦設定 `PSModulePath` ，並使用 **SetEnvironmentVariable** 方法來新增值的 `C:\Program Files\Fabrikam\Modules` 路徑。</span><span class="sxs-lookup"><span data-stu-id="047b6-220">The following example uses the **GetEnvironmentVariable** method to get the machine setting of `PSModulePath` and the **SetEnvironmentVariable** method to add the `C:\Program Files\Fabrikam\Modules` path to the value.</span></span>

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'Machine')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable("PSModulePath", $newpath, 'Machine')
```

<span data-ttu-id="047b6-221">如需 **System. 環境** 類別方法的詳細資訊，請參閱 [環境方法](/dotnet/api/system.environment)。</span><span class="sxs-lookup"><span data-stu-id="047b6-221">For more information about the methods of the **System.Environment** class, see [Environment Methods](/dotnet/api/system.environment).</span></span>

## <a name="see-also"></a><span data-ttu-id="047b6-222">另請參閱</span><span class="sxs-lookup"><span data-stu-id="047b6-222">SEE ALSO</span></span>

- [<span data-ttu-id="047b6-223">環境 (提供者) </span><span class="sxs-lookup"><span data-stu-id="047b6-223">Environment (provider)</span></span>](../About/about_Environment_Provider.md)
- [<span data-ttu-id="047b6-224">about_Modules</span><span class="sxs-lookup"><span data-stu-id="047b6-224">about_Modules</span></span>](about_Modules.md)
