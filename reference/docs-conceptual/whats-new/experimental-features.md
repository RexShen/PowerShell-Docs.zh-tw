---
ms.date: 04/28/2020
title: 在 PowerShell 中使用實驗性功能
description: 列出目前可供使用的實驗性功能與其使用方式。
ms.openlocfilehash: 72a4309d6eeede4cd2ff7c38ce8e99ce3ace30eb
ms.sourcegitcommit: e6a9b13a4799667b74e0ba0f742dded4511d32b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/01/2020
ms.locfileid: "82630762"
---
# <a name="using-experimental-features-in-powershell"></a><span data-ttu-id="08eae-103">在 PowerShell 中使用實驗性功能</span><span class="sxs-lookup"><span data-stu-id="08eae-103">Using Experimental Features in PowerShell</span></span>

<span data-ttu-id="08eae-104">PowerShell 中的「實驗性功能」支援能提供一個機制，使實驗性功能可以與 PowerShell 或 PowerShell 模組中的現有穩定功能並存。</span><span class="sxs-lookup"><span data-stu-id="08eae-104">The Experimental Features support in PowerShell provides a mechanism for experimental features to coexist with existing stable features in PowerShell or PowerShell modules.</span></span>

<span data-ttu-id="08eae-105">實驗性功能是設計尚未完成的功能。</span><span class="sxs-lookup"><span data-stu-id="08eae-105">An experimental feature is one where the design is not finalized.</span></span> <span data-ttu-id="08eae-106">該功能可供使用者測試並提供意見反應。</span><span class="sxs-lookup"><span data-stu-id="08eae-106">The feature is available for users to test and provide feedback.</span></span> <span data-ttu-id="08eae-107">在實驗性功能完成之後，設計變更便會成為中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="08eae-107">Once an experimental feature is finalized, the design changes become breaking changes.</span></span>

> [!CAUTION]
> <span data-ttu-id="08eae-108">實驗性功能並不適用於生產環境，因為允許對其進行中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="08eae-108">Experimental features aren't intended to be used in production since the changes are allowed to be breaking.</span></span> <span data-ttu-id="08eae-109">我們並未正式支援實驗性功能。</span><span class="sxs-lookup"><span data-stu-id="08eae-109">Experimental features are not officially supported.</span></span> <span data-ttu-id="08eae-110">不過，我們非常感謝能收到任何意見反應與錯誤 (Bug) 報告。</span><span class="sxs-lookup"><span data-stu-id="08eae-110">However, we appreciate any feedback and bug reports.</span></span> <span data-ttu-id="08eae-111">您可以在 [GitHub 來源存放庫](https://github.com/PowerShell/PowerShell/issues/new/choose) \(英文\) 中提出問題。</span><span class="sxs-lookup"><span data-stu-id="08eae-111">You can file issues in the [GitHub source repository](https://github.com/PowerShell/PowerShell/issues/new/choose).</span></span>

<span data-ttu-id="08eae-112">如需啟用或停用這些功能的詳細資訊，請參閱 [about_Experimental_Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features)。</span><span class="sxs-lookup"><span data-stu-id="08eae-112">For more information about enabling or disabling these features, see [about_Experimental_Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features).</span></span>

## <a name="available-features"></a><span data-ttu-id="08eae-113">可用的功能</span><span class="sxs-lookup"><span data-stu-id="08eae-113">Available features</span></span>

<span data-ttu-id="08eae-114">此文章描述可供使用的實驗性功能，以及該功能的使用方式。</span><span class="sxs-lookup"><span data-stu-id="08eae-114">This article describes the experimental features that are available and how to use the feature.</span></span>

|                            <span data-ttu-id="08eae-115">名稱</span><span class="sxs-lookup"><span data-stu-id="08eae-115">Name</span></span>                            |   <span data-ttu-id="08eae-116">6.2</span><span class="sxs-lookup"><span data-stu-id="08eae-116">6.2</span></span>   |   <span data-ttu-id="08eae-117">7.0</span><span class="sxs-lookup"><span data-stu-id="08eae-117">7.0</span></span>   | <span data-ttu-id="08eae-118">7.1 (預覽)</span><span class="sxs-lookup"><span data-stu-id="08eae-118">7.1 (preview)</span></span> |
| ---------------------------------------------------------- | :-----: | :-----: | :-----------: |
| <span data-ttu-id="08eae-119">PSTempDrive (在 PS 7.0+ 中為主要功能)</span><span class="sxs-lookup"><span data-stu-id="08eae-119">PSTempDrive (mainstream in PS 7.0+)</span></span>                        | &check; |         |               |
| <span data-ttu-id="08eae-120">PSUseAbbreviationExpansion (在 PS 7.0+ 中為主要功能)</span><span class="sxs-lookup"><span data-stu-id="08eae-120">PSUseAbbreviationExpansion (mainstream in PS 7.0+)</span></span>         | &check; |         |               |
| <span data-ttu-id="08eae-121">PSCommandNotFoundSuggestion</span><span class="sxs-lookup"><span data-stu-id="08eae-121">PSCommandNotFoundSuggestion</span></span>                                | &check; | &check; |    &check;    |
| <span data-ttu-id="08eae-122">PSImplicitRemotingBatching</span><span class="sxs-lookup"><span data-stu-id="08eae-122">PSImplicitRemotingBatching</span></span>                                 | &check; | &check; |    &check;    |
| <span data-ttu-id="08eae-123">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span><span class="sxs-lookup"><span data-stu-id="08eae-123">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span></span> |         | &check; |    &check;    |
| <span data-ttu-id="08eae-124">PSDesiredStateConfiguration.InvokeDscResource</span><span class="sxs-lookup"><span data-stu-id="08eae-124">PSDesiredStateConfiguration.InvokeDscResource</span></span>              |         | &check; |    &check;    |
| <span data-ttu-id="08eae-125">PSNullConditionalOperators</span><span class="sxs-lookup"><span data-stu-id="08eae-125">PSNullConditionalOperators</span></span>                                 |         | &check; |    &check;    |
| <span data-ttu-id="08eae-126">PSUnixFileStat (僅限非 Windows)</span><span class="sxs-lookup"><span data-stu-id="08eae-126">PSUnixFileStat (non-Windows only)</span></span>                          |         | &check; |    &check;    |
| <span data-ttu-id="08eae-127">PSNativePSPathResolution</span><span class="sxs-lookup"><span data-stu-id="08eae-127">PSNativePSPathResolution</span></span>                                   |         |         |    &check;    |
| <span data-ttu-id="08eae-128">PSCultureInvariantReplaceOperator</span><span class="sxs-lookup"><span data-stu-id="08eae-128">PSCultureInvariantReplaceOperator</span></span>                          |         |         |    &check;    |

## <a name="microsoftpowershellutilitypsmanagebreakpointsinrunspace"></a><span data-ttu-id="08eae-129">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span><span class="sxs-lookup"><span data-stu-id="08eae-129">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span></span>

<span data-ttu-id="08eae-130">在 `Debug-Runspace` 與 `Debug-Job` Cmdlet 上啟用 **BreakAll** 參數，以允許使用者決定是否要在其附加偵錯工具時，讓 PowerShell 在目前位置立即中斷。</span><span class="sxs-lookup"><span data-stu-id="08eae-130">Enables the **BreakAll** parameter on the `Debug-Runspace` and `Debug-Job` cmdlets to allow users to decide if they want PowerShell to break immediately in the current location when they attach a debugger.</span></span>

## <a name="pscommandnotfoundsuggestion"></a><span data-ttu-id="08eae-131">PSCommandNotFoundSuggestion</span><span class="sxs-lookup"><span data-stu-id="08eae-131">PSCommandNotFoundSuggestion</span></span>

<span data-ttu-id="08eae-132">在 **CommandNotFoundException** 之後，根據模糊比對搜尋來建議可能的命令。</span><span class="sxs-lookup"><span data-stu-id="08eae-132">Recommends potential commands based on fuzzy matching search after a **CommandNotFoundException**.</span></span>

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

## <a name="pscultureinvariantreplaceoperator"></a><span data-ttu-id="08eae-133">PSCultureInvariantReplaceOperator</span><span class="sxs-lookup"><span data-stu-id="08eae-133">PSCultureInvariantReplaceOperator</span></span>

<span data-ttu-id="08eae-134">當 `-replace` 運算子陳述式中的左運算元不是字串時，系統會將該運算元轉換為字串。</span><span class="sxs-lookup"><span data-stu-id="08eae-134">When the left-hand operand in a `-replace` operator statement is not a string, that operand is converted to a string.</span></span>

<span data-ttu-id="08eae-135">停用此功能時，`-replace` 運算子會進行區分文化特性的字串轉換。</span><span class="sxs-lookup"><span data-stu-id="08eae-135">When this feature is disabled, the `-replace` operator does a culture-sensitive string conversion.</span></span>
<span data-ttu-id="08eae-136">例如，如果您的文化特性 (Culture) 已設定為 [法文 (fr)]，值 `1.2` 便會轉換為字串 `1,2`。</span><span class="sxs-lookup"><span data-stu-id="08eae-136">For example, if your culture is set to French (fr), the value `1.2` is converted to the string `1,2`.</span></span>

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
12
PS> [cultureinfo]::CurrentCulture = 'en'
PS> 1.2 -replace ','
1.2
```

<span data-ttu-id="08eae-137">啟用此功能時：</span><span class="sxs-lookup"><span data-stu-id="08eae-137">With the feature enabled:</span></span>

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
1.2
```

## <a name="psdesiredstateconfigurationinvokedscresource"></a><span data-ttu-id="08eae-138">PSDesiredStateConfiguration.InvokeDscResource</span><span class="sxs-lookup"><span data-stu-id="08eae-138">PSDesiredStateConfiguration.InvokeDscResource</span></span>

<span data-ttu-id="08eae-139">可在非 Windows 系統上編譯至 MOF，並可在沒有 LCM 的情況下使用 `Invoke-DSCResource`。</span><span class="sxs-lookup"><span data-stu-id="08eae-139">Enables compilation to MOF on non-Windows systems and enables the use of `Invoke-DSCResource` without an LCM.</span></span>

## <a name="psimplicitremotingbatching"></a><span data-ttu-id="08eae-140">PSImplicitRemotingBatching</span><span class="sxs-lookup"><span data-stu-id="08eae-140">PSImplicitRemotingBatching</span></span>

<span data-ttu-id="08eae-141">此功能會檢查在殼層中輸入的命令，而且如果所有命令都是形成簡單管線的隱含遠端 Proxy 命令，則系統會對那些命令進行批次處理，並以單一遠端管線的形式叫用。</span><span class="sxs-lookup"><span data-stu-id="08eae-141">This feature examines the command typed in the shell, and if all the commands are implicit remoting proxy commands that form a simple pipeline, then the commands are batched together and invoked as a single remote pipeline.</span></span>

<span data-ttu-id="08eae-142">範例：</span><span class="sxs-lookup"><span data-stu-id="08eae-142">Example:</span></span>

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

<span data-ttu-id="08eae-143">如上所示，在啟用批次功能的情況下，全部三個隱含遠端 Proxy 命令 (`Get-AllProcesses`、`Select-Custom`、`Group-Stuff`) 都會在遠端工作階段中執行，而且來自管線的結果是唯一會傳回至用戶端的資料。</span><span class="sxs-lookup"><span data-stu-id="08eae-143">As seen above, with the batching feature enabled, all three implicit remoting proxy commands, `Get-AllProcesses`, `Select-Custom`, `Group-Stuff`, run in the remote session and the result from the pipeline is the only data returned to the client.</span></span> <span data-ttu-id="08eae-144">這能減少用戶端與遠端工作階段之間來回傳送的資料量，同時也能降低物件序列化及還原序列化的量。</span><span class="sxs-lookup"><span data-stu-id="08eae-144">This decreases the amount of data sent back and forth between client and remote session, and also reduces the amount of object serialization and de-serialization.</span></span>

## <a name="psnativepspathresolution"></a><span data-ttu-id="08eae-145">PSNativePSPathResolution</span><span class="sxs-lookup"><span data-stu-id="08eae-145">PSNativePSPathResolution</span></span>

<span data-ttu-id="08eae-146">如果將使用 FileSystem 提供者的 PSDrive 路徑傳遞至原生命令，便會將解析的檔案路徑傳遞至原生命令。</span><span class="sxs-lookup"><span data-stu-id="08eae-146">If a PSDrive path that uses the FileSystem provider is passed to a native command, the resolved file path is passed to the native command.</span></span> <span data-ttu-id="08eae-147">這表示如 `code temp:/test.txt` 的命令現在會如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="08eae-147">This means a command like `code temp:/test.txt` now works as expected.</span></span>

<span data-ttu-id="08eae-148">此外，在 Windows 上，如果路徑開頭為 `~`，便會解析為完整路徑並傳遞至原生命令。</span><span class="sxs-lookup"><span data-stu-id="08eae-148">Also, on Windows, if the path starts with `~`, that is resolved to the full path and passed to the native command.</span></span> <span data-ttu-id="08eae-149">在這兩種情況下，路徑都會標準化為相關作業系統的目錄分隔符號。</span><span class="sxs-lookup"><span data-stu-id="08eae-149">In both cases, the path is normalized to the directory separators for the relevant operating system.</span></span>

- <span data-ttu-id="08eae-150">如果路徑不是 PSDrive 或 `~` (在 Windows 上)，便不會發生路徑標準化</span><span class="sxs-lookup"><span data-stu-id="08eae-150">If the path is not a PSDrive or `~` (on Windows), then path normalization doesn't occur</span></span>
- <span data-ttu-id="08eae-151">如果路徑是以單引號括住，系統便不會加以解析，而會將其視為常值</span><span class="sxs-lookup"><span data-stu-id="08eae-151">If the path is in single quotes, then it's not resolved and treated as literal</span></span>

## <a name="psnullconditionaloperators"></a><span data-ttu-id="08eae-152">PSNullConditionalOperators</span><span class="sxs-lookup"><span data-stu-id="08eae-152">PSNullConditionalOperators</span></span>

<span data-ttu-id="08eae-153">為 Null 條件式成員存取運算子引進新的運算子：`?.` 與 `?[]`。</span><span class="sxs-lookup"><span data-stu-id="08eae-153">Introduces new operators for Null conditional member access operators - `?.` and `?[]`.</span></span> <span data-ttu-id="08eae-154">可以在純量類型和陣列類型上使用 Null 成員存取運算子。</span><span class="sxs-lookup"><span data-stu-id="08eae-154">Null member access operators can used on scalar types and array types.</span></span> <span data-ttu-id="08eae-155">如果變數不是 Null，便會傳回已存取成員的值。</span><span class="sxs-lookup"><span data-stu-id="08eae-155">Return the value of the accessed member if the variable is not null.</span></span> <span data-ttu-id="08eae-156">如果變數的值是 Null，便會傳回 Null。</span><span class="sxs-lookup"><span data-stu-id="08eae-156">If the value of the variable is null, then return null.</span></span>

```powershell
$x = $null
${x}?.propname
${x?}?.propname

${x}?[0]
${x?}?[0]

${x}?.MyMethod()
```

<span data-ttu-id="08eae-157">只有在 `$x` 不是 Null 的情況下，才會存取屬性 `propname` 並傳回其值。</span><span class="sxs-lookup"><span data-stu-id="08eae-157">The property `propname` is accessed and it's value is returned only if `$x` is not null.</span></span> <span data-ttu-id="08eae-158">同樣地，只有在 `$x` 不是 Null 的情況下才會使用索引子。</span><span class="sxs-lookup"><span data-stu-id="08eae-158">Similarly, the indexer is used only if `$x` is not null.</span></span> <span data-ttu-id="08eae-159">如果 `$x` 是 Null，便會傳回 Null。</span><span class="sxs-lookup"><span data-stu-id="08eae-159">If `$x` is null, then null is returned.</span></span>

<span data-ttu-id="08eae-160">`?.` 與 `?[]` 運算子是成員存取運算子，而且不允許在變數名稱與運算子之間使用空格。</span><span class="sxs-lookup"><span data-stu-id="08eae-160">The `?.` and `?[]` operators are member access operators and do not allow a space in between the variable name and the operator.</span></span>

<span data-ttu-id="08eae-161">由於 PowerShell 允許使用 `?` 作為變數名稱的一部分，使用於變數名稱與運算子之間沒有空格的運算子時，便需要加以區分。</span><span class="sxs-lookup"><span data-stu-id="08eae-161">Since PowerShell allows `?` as part of the variable name, disambiguation is required when the operators are used without a space between the variable name and the operator.</span></span> <span data-ttu-id="08eae-162">為了加以區分，變數必須在變數名稱周圍使用 `{}`，例如：`${x?}?.propertyName` 或 `${y}?[0]`。</span><span class="sxs-lookup"><span data-stu-id="08eae-162">To disambiguate, the variables must use `{}` around the variable name like: `${x?}?.propertyName` or `${y}?[0]`.</span></span>

## <a name="pstempdrive"></a><span data-ttu-id="08eae-163">PSTempDrive</span><span class="sxs-lookup"><span data-stu-id="08eae-163">PSTempDrive</span></span>

<span data-ttu-id="08eae-164">建立對應至使用者暫存目錄路徑的 `TEMP:` PSDrive。</span><span class="sxs-lookup"><span data-stu-id="08eae-164">Creates the `TEMP:` PSDrive mapped to user's temporary directory path.</span></span>

> [!NOTE]
> <span data-ttu-id="08eae-165">此功能已移出實驗性階段，而且是 PowerShell 7 與更新版本中的主要功能。</span><span class="sxs-lookup"><span data-stu-id="08eae-165">This feature has moved out of the experimental phase and is a mainstream feature in PowerShell 7 and higher.</span></span>

## <a name="psunixfilestat"></a><span data-ttu-id="08eae-166">PSUnixFileStat</span><span class="sxs-lookup"><span data-stu-id="08eae-166">PSUnixFileStat</span></span>

<span data-ttu-id="08eae-167">此功能可提供新的行為，以在檔案系統提供者的輸出中包含來自 Unix **stat** API 的資料，來促成更類似 Unix 的檔案清單。</span><span class="sxs-lookup"><span data-stu-id="08eae-167">This feature provides new behavior to include data from the Unix **stat** API in the output of the file system provider to facilitate a more Unix-like file listing.</span></span> <span data-ttu-id="08eae-168">其會在檔案系統提供者中新增名為 **UnixStat** 的 Note 屬性，其中包含來自底層 Unix 類型系統之 `stat(2)` API 的常見運算式。</span><span class="sxs-lookup"><span data-stu-id="08eae-168">It adds a new note property in the filesystem provider named **UnixStat** that includes a common expression of the `stat(2)` API from the underlying Unix type system.</span></span>

<span data-ttu-id="08eae-169">來自 `Get-ChildItem` 的輸出應該會看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="08eae-169">The output from `Get-ChildItem` should look something like this:</span></span>

```powershell
PS> dir | select -first 4 -skip 5


    Directory: /Users/jimtru/src/github/forks/JamesWTruher/PowerShell-1

UnixMode   User      Group           LastWriteTime        Size Name
--------   ----      -----           -------------        ---- ----
drwxr-xr-x jimtru    staff        10/23/2019 13:16         416 test
drwxr-xr-x jimtru    staff         11/8/2019 10:37         896 tools
-rw-r--r-- jimtru    staff         11/8/2019 10:37      112858 build.psm1
-rw-r--r-- jimtru    staff         11/8/2019 10:37      201297 CHANGELOG.md
```

## <a name="psuseabbreviationexpansion"></a><span data-ttu-id="08eae-170">PSUseAbbreviationExpansion</span><span class="sxs-lookup"><span data-stu-id="08eae-170">PSUseAbbreviationExpansion</span></span>

<span data-ttu-id="08eae-171">此功能可讓您使用 Tab 鍵自動完成縮寫的 Cmdlet 與函式：</span><span class="sxs-lookup"><span data-stu-id="08eae-171">This feature enables tab-completion of abbreviated cmdlets and functions:</span></span>

<span data-ttu-id="08eae-172">例如：</span><span class="sxs-lookup"><span data-stu-id="08eae-172">For example:</span></span>

- <span data-ttu-id="08eae-173">`i-psdf<tab>` 會傳回 `Import-PowerShellDataFile`。</span><span class="sxs-lookup"><span data-stu-id="08eae-173">`i-psdf<tab>` returns `Import-PowerShellDataFile`.</span></span>
- <span data-ttu-id="08eae-174">`u-akvmssdr<tab>` 傳回 `Undo-AzKeyVaultManagedStorageSasDefinitionRemoval`</span><span class="sxs-lookup"><span data-stu-id="08eae-174">`u-akvmssdr<tab>` returns `Undo-AzKeyVaultManagedStorageSasDefinitionRemoval`</span></span>

<span data-ttu-id="08eae-175">這僅適用於 Tab 鍵自動完成 (互動式用途)，因此 `i-psdf` 在指令碼中不是有效的 Cmdlet 名稱。</span><span class="sxs-lookup"><span data-stu-id="08eae-175">This only works for tab completion (interactive use), so `i-psdf` is not a valid cmdlet name in a script.</span></span>

> [!NOTE]
> <span data-ttu-id="08eae-176">此功能已移出實驗性階段，而且是 PowerShell 7 與更新版本中的主要功能。</span><span class="sxs-lookup"><span data-stu-id="08eae-176">This feature has moved out of the experimental phase and is a mainstream feature in PowerShell 7 and higher.</span></span>
