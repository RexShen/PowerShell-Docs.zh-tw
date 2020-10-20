---
ms.date: 10/15/2020
title: 在 PowerShell 中使用實驗性功能
description: 列出目前可供使用的實驗性功能與其使用方式。
ms.openlocfilehash: e98b1222755f3d4ffbd432af6b01d56f63307bb2
ms.sourcegitcommit: 108686b166672cc08817c637dd93eb1ad830511d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92156570"
---
# <a name="using-experimental-features-in-powershell"></a><span data-ttu-id="eeded-103">在 PowerShell 中使用實驗性功能</span><span class="sxs-lookup"><span data-stu-id="eeded-103">Using Experimental Features in PowerShell</span></span>

<span data-ttu-id="eeded-104">PowerShell 中的「實驗性功能」支援能提供一個機制，使實驗性功能可以與 PowerShell 或 PowerShell 模組中的現有穩定功能並存。</span><span class="sxs-lookup"><span data-stu-id="eeded-104">The Experimental Features support in PowerShell provides a mechanism for experimental features to coexist with existing stable features in PowerShell or PowerShell modules.</span></span>

<span data-ttu-id="eeded-105">實驗性功能是設計尚未完成的功能。</span><span class="sxs-lookup"><span data-stu-id="eeded-105">An experimental feature is one where the design is not finalized.</span></span> <span data-ttu-id="eeded-106">該功能可供使用者測試並提供意見反應。</span><span class="sxs-lookup"><span data-stu-id="eeded-106">The feature is available for users to test and provide feedback.</span></span> <span data-ttu-id="eeded-107">在實驗性功能完成之後，設計變更便會成為中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="eeded-107">Once an experimental feature is finalized, the design changes become breaking changes.</span></span>

> [!CAUTION]
> <span data-ttu-id="eeded-108">實驗性功能並不適用於生產環境，因為允許對其進行中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="eeded-108">Experimental features aren't intended to be used in production since the changes are allowed to be breaking.</span></span> <span data-ttu-id="eeded-109">我們並未正式支援實驗性功能。</span><span class="sxs-lookup"><span data-stu-id="eeded-109">Experimental features are not officially supported.</span></span> <span data-ttu-id="eeded-110">不過，我們非常感謝能收到任何意見反應與錯誤 (Bug) 報告。</span><span class="sxs-lookup"><span data-stu-id="eeded-110">However, we appreciate any feedback and bug reports.</span></span> <span data-ttu-id="eeded-111">您可以在 [GitHub 來源存放庫](https://github.com/PowerShell/PowerShell/issues/new/choose) \(英文\) 中提出問題。</span><span class="sxs-lookup"><span data-stu-id="eeded-111">You can file issues in the [GitHub source repository](https://github.com/PowerShell/PowerShell/issues/new/choose).</span></span>

<span data-ttu-id="eeded-112">如需啟用或停用這些功能的詳細資訊，請參閱 [about_Experimental_Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features)。</span><span class="sxs-lookup"><span data-stu-id="eeded-112">For more information about enabling or disabling these features, see [about_Experimental_Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features).</span></span>

## <a name="available-features"></a><span data-ttu-id="eeded-113">可用的功能</span><span class="sxs-lookup"><span data-stu-id="eeded-113">Available features</span></span>

<span data-ttu-id="eeded-114">此文章描述可供使用的實驗性功能，以及該功能的使用方式。</span><span class="sxs-lookup"><span data-stu-id="eeded-114">This article describes the experimental features that are available and how to use the feature.</span></span>

|                            <span data-ttu-id="eeded-115">名稱</span><span class="sxs-lookup"><span data-stu-id="eeded-115">Name</span></span>                            |   <span data-ttu-id="eeded-116">6.2</span><span class="sxs-lookup"><span data-stu-id="eeded-116">6.2</span></span>   |   <span data-ttu-id="eeded-117">7.0</span><span class="sxs-lookup"><span data-stu-id="eeded-117">7.0</span></span>   |   <span data-ttu-id="eeded-118">7.1</span><span class="sxs-lookup"><span data-stu-id="eeded-118">7.1</span></span>   |
| ---------------------------------------------------------- | :-----: | :-----: | :-----: |
| <span data-ttu-id="eeded-119">PSTempDrive (在 PS 7.0+ 中為主要功能)</span><span class="sxs-lookup"><span data-stu-id="eeded-119">PSTempDrive (mainstream in PS 7.0+)</span></span>                        | &check; |         |         |
| <span data-ttu-id="eeded-120">PSUseAbbreviationExpansion (在 PS 7.0+ 中為主要功能)</span><span class="sxs-lookup"><span data-stu-id="eeded-120">PSUseAbbreviationExpansion (mainstream in PS 7.0+)</span></span>         | &check; |         |         |
| <span data-ttu-id="eeded-121">PSCommandNotFoundSuggestion</span><span class="sxs-lookup"><span data-stu-id="eeded-121">PSCommandNotFoundSuggestion</span></span>                                | &check; | &check; | &check; |
| <span data-ttu-id="eeded-122">PSImplicitRemotingBatching</span><span class="sxs-lookup"><span data-stu-id="eeded-122">PSImplicitRemotingBatching</span></span>                                 | &check; | &check; | &check; |
| <span data-ttu-id="eeded-123">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span><span class="sxs-lookup"><span data-stu-id="eeded-123">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span></span> |         | &check; | &check; |
| <span data-ttu-id="eeded-124">PSDesiredStateConfiguration.InvokeDscResource</span><span class="sxs-lookup"><span data-stu-id="eeded-124">PSDesiredStateConfiguration.InvokeDscResource</span></span>              |         | &check; | &check; |
| <span data-ttu-id="eeded-125">PSNullConditionalOperators (PS 7.1+ 中的主流)</span><span class="sxs-lookup"><span data-stu-id="eeded-125">PSNullConditionalOperators (mainstream in PS 7.1+)</span></span>         |         | &check; |         |
| <span data-ttu-id="eeded-126">PSUnixFileStat (僅限非 Windows)</span><span class="sxs-lookup"><span data-stu-id="eeded-126">PSUnixFileStat (non-Windows only)</span></span>                          |         | &check; | &check; |
| <span data-ttu-id="eeded-127">PSNativePSPathResolution</span><span class="sxs-lookup"><span data-stu-id="eeded-127">PSNativePSPathResolution</span></span>                                   |         |         | &check; |
| <span data-ttu-id="eeded-128">PSCultureInvariantReplaceOperator</span><span class="sxs-lookup"><span data-stu-id="eeded-128">PSCultureInvariantReplaceOperator</span></span>                          |         |         | &check; |
| <span data-ttu-id="eeded-129">PSNotApplyErrorActionToStderr</span><span class="sxs-lookup"><span data-stu-id="eeded-129">PSNotApplyErrorActionToStderr</span></span>                              |         |         | &check; |
| <span data-ttu-id="eeded-130">PSSubsystemPluginModel</span><span class="sxs-lookup"><span data-stu-id="eeded-130">PSSubsystemPluginModel</span></span>                                     |         |         | &check; |

## <a name="microsoftpowershellutilitypsmanagebreakpointsinrunspace"></a><span data-ttu-id="eeded-131">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span><span class="sxs-lookup"><span data-stu-id="eeded-131">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span></span>

<span data-ttu-id="eeded-132">在 PowerShell 7.0 中，實驗會啟用 `Debug-Runspace` 與 `Debug-Job` Cmdlet 上的 **BreakAll** 參數，以允許使用者決定是否要在其附加偵錯工具時，讓 PowerShell 在目前位置立即中斷。</span><span class="sxs-lookup"><span data-stu-id="eeded-132">In PowerShell 7.0, the experiment enables the **BreakAll** parameter on the `Debug-Runspace` and `Debug-Job` cmdlets to allow users to decide if they want PowerShell to break immediately in the current location when they attach a debugger.</span></span>

<span data-ttu-id="eeded-133">在 PowerShell 7.1 中，此實驗也會將 **Runspace** 參數新增到 `*-PSBreakpoint` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="eeded-133">In PowerShell 7.1, this experiment also adds the **Runspace** parameter to the `*-PSBreakpoint` cmdlets.</span></span>

- `Disable-PSBreakpoint`
- `Enable-PSBreakpoint`
- `Get-PSBreakpoint`
- `Remove-PSBreakpoint`
- `Set-PSBreakpoint`

<span data-ttu-id="eeded-134">**Runspace** 參數會指定 **Runspace** 物件以與所指定 Runspace 中的中斷點互動。</span><span class="sxs-lookup"><span data-stu-id="eeded-134">The **Runspace** parameter specifies a **Runspace** object to interact with breakpoints in the specified runspace.</span></span>

```powershell
Start-Job -ScriptBlock {
    Set-PSBreakpoint -Command Start-Sleep
    Start-Sleep -Seconds 10
}

$runspace = Get-Runspace -Id 1

$breakpoint = Get-PSBreakPoint -Runspace $runspace
```

<span data-ttu-id="eeded-135">在此範例中，會啟動作業，並將中斷點設定為在執行 `Set-PSBreakPoint` 時中斷。</span><span class="sxs-lookup"><span data-stu-id="eeded-135">In this example, a job is started and a breakpoint is set to break when the `Set-PSBreakPoint` is run.</span></span> <span data-ttu-id="eeded-136">Runspace 會儲存在變數中，而且會使用 **Runspace** 參數傳遞至 `Get-PSBreakPoint` 命令。</span><span class="sxs-lookup"><span data-stu-id="eeded-136">The runspace is stored in a variable and passed to the `Get-PSBreakPoint` command with the **Runspace** parameter.</span></span> <span data-ttu-id="eeded-137">您接著可以檢查 `$breakpoint` 變數中的中斷點。</span><span class="sxs-lookup"><span data-stu-id="eeded-137">You can then inspect the breakpoint in the `$breakpoint` variable.</span></span>

## <a name="pscommandnotfoundsuggestion"></a><span data-ttu-id="eeded-138">PSCommandNotFoundSuggestion</span><span class="sxs-lookup"><span data-stu-id="eeded-138">PSCommandNotFoundSuggestion</span></span>

<span data-ttu-id="eeded-139">在 **CommandNotFoundException** 之後，根據模糊比對搜尋來建議可能的命令。</span><span class="sxs-lookup"><span data-stu-id="eeded-139">Recommends potential commands based on fuzzy matching search after a **CommandNotFoundException**.</span></span>

```powershell
PS> get
```

```Output
get: The term 'get' is not recognized as the name of a cmdlet, function, script file, or operable
program. Check the spelling of the name, or if a path was included, verify that the path is correct
and try again.

Suggestion [4,General]: The most similar commands are: set, del, ft, gal, gbp, gc, gci, gcm, gdr,
gcs.
```

## <a name="pscultureinvariantreplaceoperator"></a><span data-ttu-id="eeded-140">PSCultureInvariantReplaceOperator</span><span class="sxs-lookup"><span data-stu-id="eeded-140">PSCultureInvariantReplaceOperator</span></span>

<span data-ttu-id="eeded-141">當 `-replace` 運算子陳述式中的左運算元不是字串時，系統會將該運算元轉換為字串。</span><span class="sxs-lookup"><span data-stu-id="eeded-141">When the left-hand operand in a `-replace` operator statement is not a string, that operand is converted to a string.</span></span>

<span data-ttu-id="eeded-142">停用此功能時，`-replace` 運算子會進行區分文化特性的字串轉換。</span><span class="sxs-lookup"><span data-stu-id="eeded-142">When this feature is disabled, the `-replace` operator does a culture-sensitive string conversion.</span></span>
<span data-ttu-id="eeded-143">例如，如果您的文化特性 (Culture) 已設定為 [法文 (fr)]，值 `1.2` 便會轉換為字串 `1,2`。</span><span class="sxs-lookup"><span data-stu-id="eeded-143">For example, if your culture is set to French (fr), the value `1.2` is converted to the string `1,2`.</span></span>

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
12
PS> [cultureinfo]::CurrentCulture = 'en'
PS> 1.2 -replace ','
1.2
```

<span data-ttu-id="eeded-144">啟用此功能時：</span><span class="sxs-lookup"><span data-stu-id="eeded-144">With the feature enabled:</span></span>

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
1.2
```

## <a name="psdesiredstateconfigurationinvokedscresource"></a><span data-ttu-id="eeded-145">PSDesiredStateConfiguration.InvokeDscResource</span><span class="sxs-lookup"><span data-stu-id="eeded-145">PSDesiredStateConfiguration.InvokeDscResource</span></span>

<span data-ttu-id="eeded-146">可在非 Windows 系統上編譯至 MOF，並可在沒有 LCM 的情況下使用 `Invoke-DSCResource`。</span><span class="sxs-lookup"><span data-stu-id="eeded-146">Enables compilation to MOF on non-Windows systems and enables the use of `Invoke-DSCResource` without an LCM.</span></span>

## <a name="psimplicitremotingbatching"></a><span data-ttu-id="eeded-147">PSImplicitRemotingBatching</span><span class="sxs-lookup"><span data-stu-id="eeded-147">PSImplicitRemotingBatching</span></span>

<span data-ttu-id="eeded-148">此功能會檢查在殼層中輸入的命令，而且如果所有命令都是形成簡單管線的隱含遠端 Proxy 命令，則系統會對那些命令進行批次處理，並以單一遠端管線的形式叫用。</span><span class="sxs-lookup"><span data-stu-id="eeded-148">This feature examines the command typed in the shell, and if all the commands are implicit remoting proxy commands that form a simple pipeline, then the commands are batched together and invoked as a single remote pipeline.</span></span>

<span data-ttu-id="eeded-149">範例：</span><span class="sxs-lookup"><span data-stu-id="eeded-149">Example:</span></span>

```powershell
# Create remote session and import TestIMod module
$s = nsn -host remoteMachine
icm $s { ipmo 'C:\Users\user\Documents\WindowsPowerShell\Modules\TestIMod\TestIMod.psd1' }
Import-PSSession $s -mod testimod

$maxProcs = 1000
$filter = 'pwsh','powershell*','wmi*'

# Without batching, this pipeline takes approximately 12 seconds to run
Measure-Command { Get-AllProcesses -MaxCount $maxProcs | Select-Custom $filter | Group-Stuff $filter }
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 12
Milliseconds      : 463

# But with the batching experimental feature enabled, it takes approximately 0.20 seconds
Measure-Command { Get-AllProcesses -MaxCount $maxProcs | Select-Custom $filter | Group-Stuff $filter }
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 209
```

<span data-ttu-id="eeded-150">如上所示，在啟用批次功能的情況下，全部三個隱含遠端 Proxy 命令 (`Get-AllProcesses`、`Select-Custom`、`Group-Stuff`) 都會在遠端工作階段中執行，而且來自管線的結果是唯一會傳回至用戶端的資料。</span><span class="sxs-lookup"><span data-stu-id="eeded-150">As seen above, with the batching feature enabled, all three implicit remoting proxy commands, `Get-AllProcesses`, `Select-Custom`, `Group-Stuff`, run in the remote session and the result from the pipeline is the only data returned to the client.</span></span> <span data-ttu-id="eeded-151">這能減少用戶端與遠端工作階段之間來回傳送的資料量，同時也能降低物件序列化及還原序列化的量。</span><span class="sxs-lookup"><span data-stu-id="eeded-151">This decreases the amount of data sent back and forth between client and remote session, and also reduces the amount of object serialization and de-serialization.</span></span>

## <a name="psnativepspathresolution"></a><span data-ttu-id="eeded-152">PSNativePSPathResolution</span><span class="sxs-lookup"><span data-stu-id="eeded-152">PSNativePSPathResolution</span></span>

<span data-ttu-id="eeded-153">如果將使用 FileSystem 提供者的 PSDrive 路徑傳遞至原生命令，便會將解析的檔案路徑傳遞至原生命令。</span><span class="sxs-lookup"><span data-stu-id="eeded-153">If a PSDrive path that uses the FileSystem provider is passed to a native command, the resolved file path is passed to the native command.</span></span> <span data-ttu-id="eeded-154">這表示如 `code temp:/test.txt` 的命令現在會如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="eeded-154">This means a command like `code temp:/test.txt` now works as expected.</span></span>

<span data-ttu-id="eeded-155">此外，在 Windows 上，如果路徑開頭為 `~`，便會解析為完整路徑並傳遞至原生命令。</span><span class="sxs-lookup"><span data-stu-id="eeded-155">Also, on Windows, if the path starts with `~`, that is resolved to the full path and passed to the native command.</span></span> <span data-ttu-id="eeded-156">在這兩種情況下，路徑都會標準化為相關作業系統的目錄分隔符號。</span><span class="sxs-lookup"><span data-stu-id="eeded-156">In both cases, the path is normalized to the directory separators for the relevant operating system.</span></span>

- <span data-ttu-id="eeded-157">如果路徑不是 PSDrive 或 `~` (在 Windows 上)，便不會發生路徑標準化</span><span class="sxs-lookup"><span data-stu-id="eeded-157">If the path is not a PSDrive or `~` (on Windows), then path normalization doesn't occur</span></span>
- <span data-ttu-id="eeded-158">如果路徑是以單引號括住，系統便不會加以解析，而會將其視為常值</span><span class="sxs-lookup"><span data-stu-id="eeded-158">If the path is in single quotes, then it's not resolved and treated as literal</span></span>

## <a name="psnotapplyerroractiontostderr"></a><span data-ttu-id="eeded-159">PSNotApplyErrorActionToStderr</span><span class="sxs-lookup"><span data-stu-id="eeded-159">PSNotApplyErrorActionToStderr</span></span>

<span data-ttu-id="eeded-160">當此實驗性功能啟用時，從原生命令重新導向的錯誤記錄 (例如使用重新導向運算子 (`2>&1`) 時) 不會寫入 `$Error` 變數，而且喜好設定變數 `$ErrorActionPreference` 不會影響重新導向的輸出。</span><span class="sxs-lookup"><span data-stu-id="eeded-160">When this experimental feature is enabled, error records redirected from native commands, like when using redirection operators (`2>&1`), are not written to the `$Error` variable and the preference variable `$ErrorActionPreference` does not affect the redirected output.</span></span>

<span data-ttu-id="eeded-161">許多原生命令都會以替代資料流的形式寫入 `stderr` ，以取得其他資訊。</span><span class="sxs-lookup"><span data-stu-id="eeded-161">Many native commands write to `stderr` as an alternative stream for additional information.</span></span> <span data-ttu-id="eeded-162">當您查看錯誤時，此行為可能會造成混淆，或如果 `$ErrorActionPreference` 設定為針對輸出關閉通知的情況，則使用者可能會遺失額外的輸出資訊。</span><span class="sxs-lookup"><span data-stu-id="eeded-162">This behavior can cause confusion when looking through errors or the additional output information can be lost to the user if `$ErrorActionPreference` is set to a state that mutes the output.</span></span>

<span data-ttu-id="eeded-163">當原生命令具有非零的結束代碼時， `$?` 會設定為 `$false`。</span><span class="sxs-lookup"><span data-stu-id="eeded-163">When a native command has a non-zero exit code, `$?` is set to `$false`.</span></span> <span data-ttu-id="eeded-164">如果結束代碼為零， `$?` 會設定為 `$true`。</span><span class="sxs-lookup"><span data-stu-id="eeded-164">If the exit code is zero, `$?` is set to `$true`.</span></span>

## <a name="psnullconditionaloperators"></a><span data-ttu-id="eeded-165">PSNullConditionalOperators</span><span class="sxs-lookup"><span data-stu-id="eeded-165">PSNullConditionalOperators</span></span>

<span data-ttu-id="eeded-166">為 Null 條件式成員存取運算子引進新的運算子：`?.` 與 `?[]`。</span><span class="sxs-lookup"><span data-stu-id="eeded-166">Introduces new operators for Null conditional member access operators - `?.` and `?[]`.</span></span> <span data-ttu-id="eeded-167">可以在純量類型和陣列類型上使用 Null 成員存取運算子。</span><span class="sxs-lookup"><span data-stu-id="eeded-167">Null member access operators can used on scalar types and array types.</span></span> <span data-ttu-id="eeded-168">如果變數不是 Null，便會傳回已存取成員的值。</span><span class="sxs-lookup"><span data-stu-id="eeded-168">Return the value of the accessed member if the variable is not null.</span></span> <span data-ttu-id="eeded-169">如果變數的值是 Null，便會傳回 Null。</span><span class="sxs-lookup"><span data-stu-id="eeded-169">If the value of the variable is null, then return null.</span></span>

```powershell
$x = $null
${x}?.propname
${x?}?.propname

${x}?[0]
${x?}?[0]

${x}?.MyMethod()
```

<span data-ttu-id="eeded-170">只有在 `$x` 不是 Null 的情況下，才會存取屬性 `propname` 並傳回其值。</span><span class="sxs-lookup"><span data-stu-id="eeded-170">The property `propname` is accessed and it's value is returned only if `$x` is not null.</span></span> <span data-ttu-id="eeded-171">同樣地，只有在 `$x` 不是 Null 的情況下才會使用索引子。</span><span class="sxs-lookup"><span data-stu-id="eeded-171">Similarly, the indexer is used only if `$x` is not null.</span></span> <span data-ttu-id="eeded-172">如果 `$x` 是 Null，便會傳回 Null。</span><span class="sxs-lookup"><span data-stu-id="eeded-172">If `$x` is null, then null is returned.</span></span>

<span data-ttu-id="eeded-173">`?.` 與 `?[]` 運算子是成員存取運算子，而且不允許在變數名稱與運算子之間使用空格。</span><span class="sxs-lookup"><span data-stu-id="eeded-173">The `?.` and `?[]` operators are member access operators and do not allow a space in between the variable name and the operator.</span></span>

<span data-ttu-id="eeded-174">由於 PowerShell 允許使用 `?` 作為變數名稱的一部分，使用於變數名稱與運算子之間沒有空格的運算子時，便需要加以區分。</span><span class="sxs-lookup"><span data-stu-id="eeded-174">Since PowerShell allows `?` as part of the variable name, disambiguation is required when the operators are used without a space between the variable name and the operator.</span></span> <span data-ttu-id="eeded-175">為了加以區分，變數必須在變數名稱周圍使用 `{}`，例如：`${x?}?.propertyName` 或 `${y}?[0]`。</span><span class="sxs-lookup"><span data-stu-id="eeded-175">To disambiguate, the variables must use `{}` around the variable name like: `${x?}?.propertyName` or `${y}?[0]`.</span></span>

> [!NOTE]
> <span data-ttu-id="eeded-176">此功能已移出實驗性階段，而且是 PowerShell 7.1 與更新版本中的主流功能。</span><span class="sxs-lookup"><span data-stu-id="eeded-176">This feature has moved out of the experimental phase and is a mainstream feature in PowerShell 7.1 and higher.</span></span>

## <a name="pstempdrive"></a><span data-ttu-id="eeded-177">PSTempDrive</span><span class="sxs-lookup"><span data-stu-id="eeded-177">PSTempDrive</span></span>

<span data-ttu-id="eeded-178">建立對應至使用者暫存目錄路徑的 `TEMP:` PSDrive。</span><span class="sxs-lookup"><span data-stu-id="eeded-178">Creates the `TEMP:` PSDrive mapped to user's temporary directory path.</span></span>

> [!NOTE]
> <span data-ttu-id="eeded-179">此功能已移出實驗性階段，而且是 PowerShell 7 與更新版本中的主要功能。</span><span class="sxs-lookup"><span data-stu-id="eeded-179">This feature has moved out of the experimental phase and is a mainstream feature in PowerShell 7 and higher.</span></span>

## <a name="psunixfilestat"></a><span data-ttu-id="eeded-180">PSUnixFileStat</span><span class="sxs-lookup"><span data-stu-id="eeded-180">PSUnixFileStat</span></span>

<span data-ttu-id="eeded-181">此功能可提供新的行為，以在檔案系統提供者的輸出中包含來自 Unix **stat** API 的資料，來促成更類似 Unix 的檔案清單。</span><span class="sxs-lookup"><span data-stu-id="eeded-181">This feature provides new behavior to include data from the Unix **stat** API in the output of the file system provider to facilitate a more Unix-like file listing.</span></span> <span data-ttu-id="eeded-182">其會在檔案系統提供者中新增名為 **UnixStat** 的 Note 屬性，其中包含來自底層 Unix 類型系統之 `stat(2)` API 的常見運算式。</span><span class="sxs-lookup"><span data-stu-id="eeded-182">It adds a new note property in the filesystem provider named **UnixStat** that includes a common expression of the `stat(2)` API from the underlying Unix type system.</span></span>

<span data-ttu-id="eeded-183">來自 `Get-ChildItem` 的輸出應該會看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="eeded-183">The output from `Get-ChildItem` should look something like this:</span></span>

```powershell
dir | select -first 4 -skip 5


    Directory: /Users/jimtru/src/github/forks/JamesWTruher/PowerShell-1

UnixMode   User      Group           LastWriteTime        Size Name
--------   ----      -----           -------------        ---- ----
drwxr-xr-x jimtru    staff        10/23/2019 13:16         416 test
drwxr-xr-x jimtru    staff         11/8/2019 10:37         896 tools
-rw-r--r-- jimtru    staff         11/8/2019 10:37      112858 build.psm1
-rw-r--r-- jimtru    staff         11/8/2019 10:37      201297 CHANGELOG.md
```

## <a name="psuseabbreviationexpansion"></a><span data-ttu-id="eeded-184">PSUseAbbreviationExpansion</span><span class="sxs-lookup"><span data-stu-id="eeded-184">PSUseAbbreviationExpansion</span></span>

<span data-ttu-id="eeded-185">此功能可讓您使用 Tab 鍵自動完成縮寫的 Cmdlet 與函式：</span><span class="sxs-lookup"><span data-stu-id="eeded-185">This feature enables tab-completion of abbreviated cmdlets and functions:</span></span>

<span data-ttu-id="eeded-186">例如：</span><span class="sxs-lookup"><span data-stu-id="eeded-186">For example:</span></span>

- <span data-ttu-id="eeded-187">`i-psdf<tab>` 會傳回 `Import-PowerShellDataFile`。</span><span class="sxs-lookup"><span data-stu-id="eeded-187">`i-psdf<tab>` returns `Import-PowerShellDataFile`.</span></span>
- <span data-ttu-id="eeded-188">`u-akvmssdr<tab>` 傳回 `Undo-AzKeyVaultManagedStorageSasDefinitionRemoval`</span><span class="sxs-lookup"><span data-stu-id="eeded-188">`u-akvmssdr<tab>` returns `Undo-AzKeyVaultManagedStorageSasDefinitionRemoval`</span></span>

<span data-ttu-id="eeded-189">這僅適用於 Tab 鍵自動完成 (互動式用途)，因此 `i-psdf` 在指令碼中不是有效的 Cmdlet 名稱。</span><span class="sxs-lookup"><span data-stu-id="eeded-189">This only works for tab completion (interactive use), so `i-psdf` is not a valid cmdlet name in a script.</span></span>

> [!NOTE]
> <span data-ttu-id="eeded-190">此功能已移出實驗性階段，而且是 PowerShell 7 與更新版本中的主要功能。</span><span class="sxs-lookup"><span data-stu-id="eeded-190">This feature has moved out of the experimental phase and is a mainstream feature in PowerShell 7 and higher.</span></span>

## <a name="pssubsystempluginmodel"></a><span data-ttu-id="eeded-191">PSSubsystemPluginModel</span><span class="sxs-lookup"><span data-stu-id="eeded-191">PSSubsystemPluginModel</span></span>

<span data-ttu-id="eeded-192">這項功能會在 PowerShell 中啟用子系統外掛程式模型，</span><span class="sxs-lookup"><span data-stu-id="eeded-192">This feature enables the subsystem plugin model in PowerShell.</span></span> <span data-ttu-id="eeded-193">並讓您將 `System.Management.Automation.dll` 的元件區分為本身組件中的個別子系統。</span><span class="sxs-lookup"><span data-stu-id="eeded-193">The feature makes it possible to separate components of `System.Management.Automation.dll` into individual subsystems that reside in their own assembly.</span></span> <span data-ttu-id="eeded-194">這種區隔可減少核心 PowerShell 引擎的磁碟使用量，並讓這些元件成為選用功能，只需安裝最低版本的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="eeded-194">This separation reduces the disk footprint of the core PowerShell engine and allows these components to become optional features for a minimal PowerShell installation.</span></span>

<span data-ttu-id="eeded-195">目前僅支援 **CommandPredictor** 子系統。</span><span class="sxs-lookup"><span data-stu-id="eeded-195">Currently, only the **CommandPredictor** subsystem is supported.</span></span> <span data-ttu-id="eeded-196">這個子系統可搭配使用 PSReadLine 模組，以提供自訂預測外掛程式。</span><span class="sxs-lookup"><span data-stu-id="eeded-196">This subsystem is used along with the PSReadLine module to provide custom prediction plugins.</span></span> <span data-ttu-id="eeded-197">未來，您可以將 **Job**、**CommandCompleter**、**Remoting** 和其他元件區分為 `System.Management.Automation.dll` 以外的子系統組件。</span><span class="sxs-lookup"><span data-stu-id="eeded-197">In future, **Job**, **CommandCompleter**, **Remoting** and other components could be separated into subsystem assemblies outside of `System.Management.Automation.dll`.</span></span>

<span data-ttu-id="eeded-198">實驗性功能包含 [Get-PSSubsystem](xref:Microsoft.PowerShell.Core.Get-PSSubsystem) 這個新的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="eeded-198">The experimental feature includes a new cmdlet, [Get-PSSubsystem](xref:Microsoft.PowerShell.Core.Get-PSSubsystem).</span></span> <span data-ttu-id="eeded-199">只有在啟用此功能時，才能使用這個 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="eeded-199">This cmdlet is only available when the feature is enabled.</span></span> <span data-ttu-id="eeded-200">這個 Cmdlet 會傳回系統上可用的子系統相關資訊。</span><span class="sxs-lookup"><span data-stu-id="eeded-200">This cmdlet returns information about the subsystems that are available on the system.</span></span>
