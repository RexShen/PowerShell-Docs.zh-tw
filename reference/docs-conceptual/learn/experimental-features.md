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
# <a name="using-experimental-features-in-powershell"></a>在 PowerShell 中使用實驗性功能

PowerShell 中的「實驗性功能」支援能提供一個機制，使實驗性功能可以與 PowerShell 或 PowerShell 模組中的現有穩定功能並存。

實驗性功能是設計尚未完成的功能。 該功能可供使用者測試並提供意見反應。 在實驗性功能完成之後，設計變更便會成為中斷性變更。

> [!CAUTION]
> 實驗性功能並不適用於生產環境，因為允許對其進行中斷性變更。 我們並未正式支援實驗性功能。 不過，我們非常感謝能收到任何意見反應與錯誤 (Bug) 報告。 您可以在 [GitHub 來源存放庫](https://github.com/PowerShell/PowerShell/issues/new/choose) \(英文\) 中提出問題。

如需啟用或停用這些功能的詳細資訊，請參閱 [about_Experimental_Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features)。

## <a name="available-features"></a>可用的功能

此文章描述可供使用的實驗性功能，以及該功能的使用方式。

|                            名稱                            |   6.2   |   7.0   |   7.1   |
| ---------------------------------------------------------- | :-----: | :-----: | :-----: |
| PSTempDrive (在 PS 7.0+ 中為主要功能)                        | &check; |         |         |
| PSUseAbbreviationExpansion (在 PS 7.0+ 中為主要功能)         | &check; |         |         |
| PSCommandNotFoundSuggestion                                | &check; | &check; | &check; |
| PSImplicitRemotingBatching                                 | &check; | &check; | &check; |
| Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace |         | &check; | &check; |
| PSDesiredStateConfiguration.InvokeDscResource              |         | &check; | &check; |
| PSNullConditionalOperators (PS 7.1+ 中的主流)         |         | &check; |         |
| PSUnixFileStat (僅限非 Windows)                          |         | &check; | &check; |
| PSNativePSPathResolution                                   |         |         | &check; |
| PSCultureInvariantReplaceOperator                          |         |         | &check; |
| PSNotApplyErrorActionToStderr                              |         |         | &check; |
| PSSubsystemPluginModel                                     |         |         | &check; |

## <a name="microsoftpowershellutilitypsmanagebreakpointsinrunspace"></a>Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace

在 PowerShell 7.0 中，實驗會啟用 `Debug-Runspace` 與 `Debug-Job` Cmdlet 上的 **BreakAll** 參數，以允許使用者決定是否要在其附加偵錯工具時，讓 PowerShell 在目前位置立即中斷。

在 PowerShell 7.1 中，此實驗也會將 **Runspace** 參數新增到 `*-PSBreakpoint` Cmdlet。

- `Disable-PSBreakpoint`
- `Enable-PSBreakpoint`
- `Get-PSBreakpoint`
- `Remove-PSBreakpoint`
- `Set-PSBreakpoint`

**Runspace** 參數會指定 **Runspace** 物件以與所指定 Runspace 中的中斷點互動。

```powershell
Start-Job -ScriptBlock {
    Set-PSBreakpoint -Command Start-Sleep
    Start-Sleep -Seconds 10
}

$runspace = Get-Runspace -Id 1

$breakpoint = Get-PSBreakPoint -Runspace $runspace
```

在此範例中，會啟動作業，並將中斷點設定為在執行 `Set-PSBreakPoint` 時中斷。 Runspace 會儲存在變數中，而且會使用 **Runspace** 參數傳遞至 `Get-PSBreakPoint` 命令。 您接著可以檢查 `$breakpoint` 變數中的中斷點。

## <a name="pscommandnotfoundsuggestion"></a>PSCommandNotFoundSuggestion

在 **CommandNotFoundException** 之後，根據模糊比對搜尋來建議可能的命令。

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

## <a name="pscultureinvariantreplaceoperator"></a>PSCultureInvariantReplaceOperator

當 `-replace` 運算子陳述式中的左運算元不是字串時，系統會將該運算元轉換為字串。

停用此功能時，`-replace` 運算子會進行區分文化特性的字串轉換。
例如，如果您的文化特性 (Culture) 已設定為 [法文 (fr)]，值 `1.2` 便會轉換為字串 `1,2`。

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
12
PS> [cultureinfo]::CurrentCulture = 'en'
PS> 1.2 -replace ','
1.2
```

啟用此功能時：

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
1.2
```

## <a name="psdesiredstateconfigurationinvokedscresource"></a>PSDesiredStateConfiguration.InvokeDscResource

可在非 Windows 系統上編譯至 MOF，並可在沒有 LCM 的情況下使用 `Invoke-DSCResource`。

## <a name="psimplicitremotingbatching"></a>PSImplicitRemotingBatching

此功能會檢查在殼層中輸入的命令，而且如果所有命令都是形成簡單管線的隱含遠端 Proxy 命令，則系統會對那些命令進行批次處理，並以單一遠端管線的形式叫用。

範例：

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

如上所示，在啟用批次功能的情況下，全部三個隱含遠端 Proxy 命令 (`Get-AllProcesses`、`Select-Custom`、`Group-Stuff`) 都會在遠端工作階段中執行，而且來自管線的結果是唯一會傳回至用戶端的資料。 這能減少用戶端與遠端工作階段之間來回傳送的資料量，同時也能降低物件序列化及還原序列化的量。

## <a name="psnativepspathresolution"></a>PSNativePSPathResolution

如果將使用 FileSystem 提供者的 PSDrive 路徑傳遞至原生命令，便會將解析的檔案路徑傳遞至原生命令。 這表示如 `code temp:/test.txt` 的命令現在會如預期般運作。

此外，在 Windows 上，如果路徑開頭為 `~`，便會解析為完整路徑並傳遞至原生命令。 在這兩種情況下，路徑都會標準化為相關作業系統的目錄分隔符號。

- 如果路徑不是 PSDrive 或 `~` (在 Windows 上)，便不會發生路徑標準化
- 如果路徑是以單引號括住，系統便不會加以解析，而會將其視為常值

## <a name="psnotapplyerroractiontostderr"></a>PSNotApplyErrorActionToStderr

當此實驗性功能啟用時，從原生命令重新導向的錯誤記錄 (例如使用重新導向運算子 (`2>&1`) 時) 不會寫入 `$Error` 變數，而且喜好設定變數 `$ErrorActionPreference` 不會影響重新導向的輸出。

許多原生命令都會以替代資料流的形式寫入 `stderr` ，以取得其他資訊。 當您查看錯誤時，此行為可能會造成混淆，或如果 `$ErrorActionPreference` 設定為針對輸出關閉通知的情況，則使用者可能會遺失額外的輸出資訊。

當原生命令具有非零的結束代碼時， `$?` 會設定為 `$false`。 如果結束代碼為零， `$?` 會設定為 `$true`。

## <a name="psnullconditionaloperators"></a>PSNullConditionalOperators

為 Null 條件式成員存取運算子引進新的運算子：`?.` 與 `?[]`。 可以在純量類型和陣列類型上使用 Null 成員存取運算子。 如果變數不是 Null，便會傳回已存取成員的值。 如果變數的值是 Null，便會傳回 Null。

```powershell
$x = $null
${x}?.propname
${x?}?.propname

${x}?[0]
${x?}?[0]

${x}?.MyMethod()
```

只有在 `$x` 不是 Null 的情況下，才會存取屬性 `propname` 並傳回其值。 同樣地，只有在 `$x` 不是 Null 的情況下才會使用索引子。 如果 `$x` 是 Null，便會傳回 Null。

`?.` 與 `?[]` 運算子是成員存取運算子，而且不允許在變數名稱與運算子之間使用空格。

由於 PowerShell 允許使用 `?` 作為變數名稱的一部分，使用於變數名稱與運算子之間沒有空格的運算子時，便需要加以區分。 為了加以區分，變數必須在變數名稱周圍使用 `{}`，例如：`${x?}?.propertyName` 或 `${y}?[0]`。

> [!NOTE]
> 此功能已移出實驗性階段，而且是 PowerShell 7.1 與更新版本中的主流功能。

## <a name="pstempdrive"></a>PSTempDrive

建立對應至使用者暫存目錄路徑的 `TEMP:` PSDrive。

> [!NOTE]
> 此功能已移出實驗性階段，而且是 PowerShell 7 與更新版本中的主要功能。

## <a name="psunixfilestat"></a>PSUnixFileStat

此功能可提供新的行為，以在檔案系統提供者的輸出中包含來自 Unix **stat** API 的資料，來促成更類似 Unix 的檔案清單。 其會在檔案系統提供者中新增名為 **UnixStat** 的 Note 屬性，其中包含來自底層 Unix 類型系統之 `stat(2)` API 的常見運算式。

來自 `Get-ChildItem` 的輸出應該會看起來像這樣：

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

## <a name="psuseabbreviationexpansion"></a>PSUseAbbreviationExpansion

此功能可讓您使用 Tab 鍵自動完成縮寫的 Cmdlet 與函式：

例如：

- `i-psdf<tab>` 會傳回 `Import-PowerShellDataFile`。
- `u-akvmssdr<tab>` 傳回 `Undo-AzKeyVaultManagedStorageSasDefinitionRemoval`

這僅適用於 Tab 鍵自動完成 (互動式用途)，因此 `i-psdf` 在指令碼中不是有效的 Cmdlet 名稱。

> [!NOTE]
> 此功能已移出實驗性階段，而且是 PowerShell 7 與更新版本中的主要功能。

## <a name="pssubsystempluginmodel"></a>PSSubsystemPluginModel

這項功能會在 PowerShell 中啟用子系統外掛程式模型， 並讓您將 `System.Management.Automation.dll` 的元件區分為本身組件中的個別子系統。 這種區隔可減少核心 PowerShell 引擎的磁碟使用量，並讓這些元件成為選用功能，只需安裝最低版本的 PowerShell。

目前僅支援 **CommandPredictor** 子系統。 這個子系統可搭配使用 PSReadLine 模組，以提供自訂預測外掛程式。 未來，您可以將 **Job**、**CommandCompleter**、**Remoting** 和其他元件區分為 `System.Management.Automation.dll` 以外的子系統組件。

實驗性功能包含 [Get-PSSubsystem](xref:Microsoft.PowerShell.Core.Get-PSSubsystem) 這個新的 Cmdlet。 只有在啟用此功能時，才能使用這個 Cmdlet。 這個 Cmdlet 會傳回系統上可用的子系統相關資訊。
