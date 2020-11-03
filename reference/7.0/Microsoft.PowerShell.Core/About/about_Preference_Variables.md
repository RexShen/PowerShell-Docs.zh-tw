---
description: 自訂 PowerShell 行為的變數。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_preference_variables?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Preference_Variables
ms.openlocfilehash: 2f290020a66b2db15c41cc9581ae3582dda8c96d
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206628"
---
# <a name="about-preference-variables"></a>關於喜好設定變數

## <a name="short-description"></a>簡短描述

自訂 PowerShell 行為的變數。

## <a name="long-description"></a>完整描述

PowerShell 包含一組可讓您自訂其行為的變數。 這些喜好設定變數的運作方式就像 GUI 系統中的選項。

喜好設定變數會影響 PowerShell 操作環境和環境中執行的所有命令。 在許多情況下，Cmdlet 都有參數，可讓您用來覆寫特定命令的喜好設定行為。

下表列出喜好設定變數及其預設值。

|             變數             |       預設值       |
| -------------------------------- | ------------------------- |
| `$ConfirmPreference`             | 高                      |
| `$DebugPreference`               | SilentlyContinue          |
| `$ErrorActionPreference`         | Continue                  |
| `$ErrorView`                     | ConciseView               |
| `$FormatEnumerationLimit`        | 4                         |
| `$InformationPreference`         | SilentlyContinue          |
| `$LogCommandHealthEvent`         | False (未記錄)         |
| `$LogCommandLifecycleEvent`      | False (未記錄)         |
| `$LogEngineHealthEvent`          | True (記錄)              |
| `$LogEngineLifecycleEvent`       | True (記錄)              |
| `$LogProviderLifecycleEvent`     | True (記錄)              |
| `$LogProviderHealthEvent`        | True (記錄)              |
| `$MaximumHistoryCount`           | 4096                      |
| `$OFS`                           |  (空白字元 (`" "`) # A3 |
| `$OutputEncoding`                | UTF8Encoding 物件       |
| `$ProgressPreference`            | 繼續                  |
| `$PSDefaultParameterValues`      |  (無-空白雜湊表)  |
| `$PSEmailServer`                 | (無)                    |
| `$PSModuleAutoLoadingPreference` | 全部                       |
| `$PSSessionApplicationName`      | wsman                     |
| `$PSSessionConfigurationName`    | `http://schemas.microsoft.com/powershell/Microsoft.PowerShell` |
| `$PSSessionOption`               | 請參閱 [$PSSessionOption](#pssessionoption) |
| `$Transcript`                    | (無)                    |
| `$VerbosePreference`             | SilentlyContinue          |
| `$WarningPreference`             | Continue                  |
| `$WhatIfPreference`              | False                     |

PowerShell 包含下列儲存使用者喜好設定的環境變數。 如需這些環境變數的詳細資訊，請參閱 [about_Environment_Variables](about_Environment_Variables.md)。

- `env:PSExecutionPolicyPreference`
- `$env:PSModulePath`

> [!NOTE]
> 喜好設定變數的變更只會在腳本和函式中生效（如果這些腳本或函式定義所在的範圍與使用喜好設定的範圍相同）。 如需詳細資訊，請參閱 [about_Scopes](about_Scopes.md)。

## <a name="working-with-preference-variables"></a>使用喜好設定變數

本檔說明每個喜好設定變數。

若要顯示特定喜好設定變數的目前值，請輸入變數的名稱。 例如，下列命令會顯示 `$ConfirmPreference` 變數的值。

```powershell
 $ConfirmPreference
```

```Output
High
```

若要變更變數的值，請使用指派語句。 例如，下列語句會將 `$ConfirmPreference` 參數的值變更為 **Medium** 。

```powershell
$ConfirmPreference = "Medium"
```

您所設定的值是目前 PowerShell 會話的特定值。 若要讓變數在所有 PowerShell 會話中都有效，請將它們新增至您的 PowerShell 設定檔。 如需詳細資訊，請參閱 [about_Profiles](about_Profiles.md)。

## <a name="working-remotely"></a>從遠端工作

當您在遠端電腦上執行命令時，遠端命令僅受限於遠端電腦的 PowerShell 用戶端中設定的喜好設定。 例如，當您執行遠端命令時，遠端電腦的變數值會 `$DebugPreference` 決定 PowerShell 如何回應偵錯工具訊息。

如需遠端命令的詳細資訊，請參閱 [about_Remote](about_Remote.md)。

### <a name="confirmpreference"></a>\$ConfirmPreference

判斷 PowerShell 是否會在執行 Cmdlet 或函式之前，自動提示您進行確認。

`$ConfirmPreference`變數的有效值為 [ **高** ]、[ **中** ] 或 [ **低** ]。 Cmdlet 和函式會被指派 **高** 、 **中** 或 **低** 的風險。 當變數的值 `$ConfirmPreference` 小於或等於指派給 Cmdlet 或函式的風險時，PowerShell 會在執行 Cmdlet 或函式之前，自動提示您進行確認。

如果變數的值 `$ConfirmPreference` 為 **None** ，則 PowerShell 永遠不會在執行 Cmdlet 或函式之前自動提示您。

若要變更會話中所有 Cmdlet 和函式的確認行為，請變更 `$ConfirmPreference` 變數的值。

若要覆寫 `$ConfirmPreference` 單一命令的，請使用 Cmdlet 或函式的 **Confirm** 參數。 若要要求確認，請使用 `-Confirm` 。 若要隱藏確認，請使用 `-Confirm:$false` 。

有效的值 `$ConfirmPreference` ：

- **無** ： PowerShell 不會自動提示。 若要要求確認特定的命令，請使用 Cmdlet 或函式的 **Confirm** 參數。
- **低** ： PowerShell 在執行具有低、中或高風險的 Cmdlet 或函式之前，會先提示確認。
- **媒體** ： PowerShell 在執行具有中或高風險的 Cmdlet 或函式之前，會先提示確認。
- **高** ： PowerShell 在執行具有高風險的 Cmdlet 或函式之前，會先提示確認。

#### <a name="detailed-explanation"></a>詳細說明

PowerShell 會在執行動作之前自動提示您進行確認。 例如，當 Cmdlet 或函式大幅影響系統來刪除資料或使用大量系統資源時。

```powershell
Remove-Item -Path C:\file.txt
```

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target "C:\file.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [?] Help (default is "Y"):
```

風險預估是 Cmdlet 或函式的屬性，稱為其 **ConfirmImpact** 。 使用者無法變更它。

可能會對系統造成風險的 Cmdlet 和函式有一個 **Confirm** 參數，可讓您用來要求或隱藏單一命令的確認。

因為大部分的 Cmdlet 和函式使用預設的風險值 **ConfirmImpact** ，而預設值為 High **，** 所以 `$ConfirmPreference` 很 **High** 少會發生自動確認。 不過，您可以藉由將的值變更為 [ `$ConfirmPreference` **中** ] 或 [ **低** ]，來啟用自動確認。

#### <a name="examples"></a>範例

此範例顯示 `$ConfirmPreference` 變數的預設值（ **High** ）效果。 最 **高** 值只會確認高風險的 Cmdlet 和函式。 因為大部分的 Cmdlet 和函式都是中度風險，所以不會自動確認並 `Remove-Item` 刪除該檔案。 新增 `-Confirm` 至命令會提示使用者進行確認。

```powershell
$ConfirmPreference
```

```Output
High
```

```powershell
Remove-Item -Path C:\temp1.txt
```

用 `-Confirm` 來要求確認。

```powershell
Remove-Item -Path C:\temp2.txt -Confirm
```

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target "C:\temp2.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All
[?] Help (default is "Y"):
```

下列範例顯示將值變更 `$ConfirmPreference` 為 **Medium** 的效果。 因為大部分的 Cmdlet 和函式都是中度風險，所以會自動確認。 若要隱藏單一命令的確認提示，請使用的 **Confirm** 參數值為 `$false` 。

```powershell
$ConfirmPreference = "Medium"
Remove-Item -Path C:\temp2.txt
```

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target "C:\temp2.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All
[?] Help (default is "Y"):
```

```powershell
Remove-Item -Path C:\temp3.txt -Confirm:$false
```

### <a name="debugpreference"></a>\$DebugPreference

決定 PowerShell 如何回應腳本、Cmdlet 或提供者所產生的訊息，或命令列中的 `Write-Debug` 命令。

某些 Cmdlet 會顯示偵錯工具，通常是專為程式設計人員和技術支援專業人員設計的技術訊息。 根據預設，不會顯示偵錯工具訊息，但是您可以藉由變更的值來顯示偵錯工具訊息 `$DebugPreference` 。

您可以使用 Cmdlet 的 **Debug** 一般參數來顯示或隱藏特定命令的偵錯工具訊息。 如需詳細資訊，請參閱 [about_CommonParameters](about_CommonParameters.md)。

有效值如下：

- **停止** ：顯示 debug 訊息並停止執行。 將錯誤寫入主控台。
- **Inquire** ：顯示 debug 訊息，並詢問您是否要繼續。 將 **Debug** 一般參數加入至命令，當命令設定為產生偵錯工具訊息時，會將變數的值變更 `$DebugPreference` 為 **Inquire** 。
- **繼續** ：顯示 debug 訊息，並繼續執行。
- **SilentlyContinue** ： (預設) 沒有任何作用。 調試訊息不會顯示，而且會繼續執行而不會中斷。

#### <a name="examples"></a>範例

下列範例顯示在 `$DebugPreference` `Write-Debug` 命令列輸入命令時，變更值的效果。
這項變更會影響所有的偵錯工具訊息，包括 Cmdlet 和腳本所產生的訊息。 這些範例會顯示 **Debug** 參數，該參數會顯示或隱藏與單一命令相關的調試訊息。

此範例顯示 `$DebugPreference` 變數預設值 **SilentlyContinue** 的效果。 依預設， `Write-Debug` 不會顯示 Cmdlet 的偵錯工具訊息，而且會繼續處理。 使用 **Debug** 參數時，它會覆寫單一命令的喜好設定。 隨即顯示偵錯工具訊息。

```powershell
$DebugPreference
```

```Output
SilentlyContinue
```

```powershell
Write-Debug -Message "Hello, World"
```

```powershell
Write-Debug -Message "Hello, World" -Debug
```

```Output
DEBUG: Hello, World
```

此範例顯示 `$DebugPreference` 使用 **Continue** 值的效果。 隨即會顯示偵錯工具訊息，並繼續處理命令。

```powershell
$DebugPreference = "Continue"
Write-Debug -Message "Hello, World"
```

```Output
DEBUG: Hello, World
```

此範例使用 **Debug** 參數搭配的值 `$false` 來抑制單一命令的訊息。 不會顯示調試訊息。

```powershell
Write-Debug -Message "Hello, World" -Debug:$false
```

此範例顯示 `$DebugPreference` 設定為 **Stop** 值的效果。 隨即會顯示偵錯工具訊息並停止命令。

```powershell
$DebugPreference = "Stop"
Write-Debug -Message "Hello, World"
```

```Output
DEBUG: Hello, World
Write-Debug : The running command stopped because the preference variable
 "DebugPreference" or common parameter is set to Stop: Hello, World
At line:1 char:1
+ Write-Debug -Message "Hello, World"
```

此範例使用 **Debug** 參數搭配的值 `$false` 來抑制單一命令的訊息。 不會顯示 debug 訊息，也不會停止處理。

```powershell
Write-Debug -Message "Hello, World" -Debug:$false
```

此範例顯示 `$DebugPreference` 設定為 **Inquire** 值的效果。 隨即會顯示偵錯工具訊息，並提示使用者進行確認。

```powershell
$DebugPreference = "Inquire"
Write-Debug -Message "Hello, World"
```

```Output
DEBUG: Hello, World

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

此範例使用 **Debug** 參數搭配的值 `$false` 來抑制單一命令的訊息。 調試訊息不會顯示，而且會繼續處理。

```powershell
Write-Debug -Message "Hello, World" -Debug:$false
```

### <a name="erroractionpreference"></a>\$ErrorActionPreference

判斷 PowerShell 如何回應非終止錯誤，這是不會停止 Cmdlet 處理的錯誤。 例如，在命令列或腳本、Cmdlet 或提供者中，例如 Cmdlet 所產生的錯誤 `Write-Error` 。

您可以使用 Cmdlet 的 **ErrorAction** 一般參數覆寫特定命令的喜好設定。

有效值如下：

- **中斷** -進入發生錯誤時或引發例外狀況時的偵錯工具。
- **繼續** ： (預設) 顯示錯誤訊息，並繼續執行。
- **Ignore** ：抑制錯誤訊息，並繼續執行命令。 **Ignore** 值適用于每個命令使用，不是用來做為儲存的喜好設定。 **Ignore** 對變數而言不是有效的值 `$ErrorActionPreference` 。
- **查詢** ：顯示錯誤訊息，並詢問您是否要繼續。
- **SilentlyContinue** ：無效果。 不會顯示錯誤訊息，且會繼續執行而不會中斷。
- **停止** ：顯示錯誤訊息並停止執行。 除了產生的錯誤之外， **Stop** 值也會產生 ActionPreferenceStopException 物件至錯誤資料流程。
  資料流
- **暫** 止：自動暫停工作流程工作以允許進一步調查。 經過調查之後，即可繼續工作流程。 「 **暫停** 」值適用于每個命令使用，不是用來做為儲存的喜好設定。 **暫** 止不是有效的 `$ErrorActionPreference` 變數值。

`$ErrorActionPreference` 而 **ErrorAction** 參數不會影響 PowerShell 如何回應停止 Cmdlet 處理的終止錯誤。 如需 **ErrorAction** 一般參數的詳細資訊，請參閱 [about_CommonParameters](about_CommonParameters.md)。

#### <a name="examples"></a>範例

這些範例顯示變數不同值的效果 `$ErrorActionPreference` 。 **ErrorAction** 參數是用來覆寫 `$ErrorActionPreference` 值。

此範例會顯示 `$ErrorActionPreference` 預設值 [ **繼續** ]。 產生非終止錯誤。 訊息隨即顯示，並且繼續處理。

```powershell
# Change the ErrorActionPreference to 'Continue'
$ErrorActionPreference = 'Continue'
# Generate a non-terminating error and continue processing the script.
Write-Error -Message  'Test Error' ; Write-Host 'Hello World'
```

```Output
Write-Error: Test Error
Hello World
```

此範例顯示 `$ErrorActionPreference` 預設值： **Inquire** 。 系統會產生錯誤，並顯示提示動作。

```powershell
# Change the ErrorActionPreference to 'Inquire'
$ErrorActionPreference = 'Inquire'
Write-Error -Message 'Test Error' ; Write-Host 'Hello World'
```

```Output
Confirm
Test Error
[Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"):
```

這個範例會示範 `$ErrorActionPreference` 要 **SilentlyContinue** 的設定。
會隱藏錯誤訊息。

```powershell
# Change the ErrorActionPreference to 'SilentlyContinue'
$ErrorActionPreference = 'SilentlyContinue'
# Generate an error message
Write-Error -Message 'Test Error' ; Write-Host 'Hello World'
# Error message is suppressed and script continues processing
```

```Output
Hello World
```

這個範例會顯示 `$ErrorActionPreference` 要 **停止** 的設定。 它也會顯示為變數產生的額外物件 `$Error` 。

```powershell
# Change the ErrorActionPreference to 'Stop'
$ErrorActionPreference = 'Stop'
# Error message is is generated and script stops processing
Write-Error -Message 'Test Error' ; Write-Host 'Hello World'

# Show the ActionPreferenceStopException and the error generated
$Error[0]
$Error[1]
```

```Output
Write-Error: Test Error

ErrorRecord                 : Test Error
WasThrownFromThrowStatement : False
TargetSite                  : System.Collections.ObjectModel.Collection`1[System.Management.Automation.PSObject]
                              Invoke(System.Collections.IEnumerable)
StackTrace                  :    at System.Management.Automation.Runspaces.PipelineBase.Invoke(IEnumerable input)
                                 at Microsoft.PowerShell.Executor.ExecuteCommandHelper(Pipeline tempPipeline,
                              Exception& exceptionThrown, ExecutionOptions options)
Message                     : The running command stopped because the preference variable "ErrorActionPreference" or
                              common parameter is set to Stop: Test Error
Data                        : {System.Management.Automation.Interpreter.InterpretedFrameInfo}
InnerException              :
HelpLink                    :
Source                      : System.Management.Automation
HResult                     : -2146233087

Write-Error: Test Error
```

### <a name="errorview"></a>\$ErrorView

決定 PowerShell 中錯誤訊息的顯示格式。

有效值如下：

- **ConciseView** ： (預設) 提供簡潔的錯誤訊息，以及 advanced 模組產生器的重構視圖。 如果錯誤來自命令列，則為單一行錯誤訊息。 否則，您會收到包含錯誤的多行錯誤訊息，以及顯示該錯誤在該行中發生之錯誤的指標。 如果終端機支援虛擬終端機，則會使用 ANSI 色彩代碼來提供色彩強調。 您可以在中變更輔色 `$Host.PrivateData.ErrorAccentColor` 。 使用指令程式可完整 `Get-Error` 查看完整的錯誤，包括內部例外狀況。

  **ConciseView** 已在 PowerShell 7 中新增。

- **NormalView** ：為大部分的使用者設計的詳細觀點。 包含錯誤的描述，以及包含在錯誤中的物件名稱。

- **CategoryView** ：專為生產環境所設計的簡潔結構化視圖。 其格式如下所示：

  {Category}： ( {TargetName}： {TargetType} ) ： [{Activity}]，{Reason}

如需 **CategoryView** 中欄位的詳細資訊，請參閱 [ErrorCategoryInfo](/dotnet/api/system.management.automation.errorcategoryinfo) 類別。

#### <a name="examples"></a>範例

這個範例示範當的值 `$ErrorView` 是預設的 **ConciseView** 時，如何顯示錯誤。 `Get-ChildItem` 用來尋找不存在的目錄。

```powershell
Get-ChildItem -path 'C:\NoRealDirectory'
```

```Output
Get-ChildItem: Cannot find path 'C:\NoRealDirectory' because it does not exist.
```

這個範例示範當的值 `$ErrorView` 是預設的 **ConciseView** 時，如何顯示錯誤。 `Script.ps1` 會執行，並從語句擲回錯誤 `Get-Item` 。

```powershell
./Script.ps1
```

```Output
Get-Item: C:\Script.ps1
Line |
  11 | Get-Item -Path .\stuff
     | ^ Cannot find path 'C:\demo\stuff' because it does not exist.
```

這個範例會顯示當的值 `$ErrorView` 變更為 **NormalView** 時，如何顯示錯誤。 `Get-ChildItem` 用來尋找不存在的檔案。

```powershell
Get-ChildItem -Path C:\nofile.txt
```

```Output
Get-ChildItem : Cannot find path 'C:\nofile.txt' because it does not exist.
At line:1 char:1
+ Get-ChildItem -Path C:\nofile.txt
```

這個範例示範當的值 `$ErrorView` 變更為 **CategoryView** 時，會如何顯示相同的錯誤。

```powershell
$ErrorView = "CategoryView"
Get-ChildItem -Path C:\nofile.txt
```

```Output
ObjectNotFound: (C:\nofile.txt:String) [Get-ChildItem], ItemNotFoundException
```

這個範例示範的值 `$ErrorView` 只會影響錯誤顯示。 它不會變更儲存在自動變數中之錯誤物件的結構 `$Error` 。 如需自動變數的相關資訊 `$Error` ，請參閱 [about_automatic_variables](about_Automatic_Variables.md)。

下列命令會使用與錯誤陣列（專案 **0** ）中最新錯誤相關聯的 **ErrorRecord** 物件，並將所有錯誤物件的屬性格式化為清單中的所有錯誤物件。

```powershell
$Error[0] | Format-List -Property * -Force
```

```Output
PSMessageDetails      :
Exception             : System.Management.Automation.ItemNotFoundException:
                          Cannot find path 'C:\nofile.txt' because it does
                          not exist.
                        at System.Management.Automation.SessionStateInternal.
                          GetChildItems(String path, Boolean recurse, UInt32
                          depth, CmdletProviderContext context)
                        at System.Management.Automation.ChildItemCmdlet
                          ProviderIntrinsics.Get(String path, Boolean
                          recurse, UInt32 depth, CmdletProviderContext context)
                        at Microsoft.PowerShell.Commands.GetChildItemCommand.
                          ProcessRecord()
TargetObject          : C:\nofile.txt
CategoryInfo          : ObjectNotFound: (C:\nofile.txt:String) [Get-ChildItem],
                          ItemNotFoundException
FullyQualifiedErrorId : PathNotFound,
                          Microsoft.PowerShell.Commands.GetChildItemCommand
ErrorDetails          :
InvocationInfo        : System.Management.Automation.InvocationInfo
ScriptStackTrace      : at <ScriptBlock>, <No file>: line 1
PipelineIterationInfo : {0, 1}
```

### <a name="formatenumerationlimit"></a>\$FormatEnumerationLimit

決定顯示中包含多少列舉專案。 此變數不會影響基礎物件，只會影響顯示。 當的值 `$FormatEnumerationLimit` 少於列舉的專案數目時，PowerShell 會新增省略號 (`...`) 來指出未顯示的專案。

**有效的值** ：整數 (`Int32`) 

**預設值** ：4

#### <a name="examples"></a>範例

此範例顯示如何使用 `$FormatEnumerationLimit` 變數來改善列舉專案的顯示。

此範例中的命令會產生一份資料表，其中列出在電腦上執行的所有服務，其中有兩個群組：一個用來 **執行服務，另一個用於****已停止** 的服務。 它會使用 `Get-Service` 命令來取得所有服務，然後透過管線將結果傳送至 `Group-Object` Cmdlet，此 Cmdlet 會依服務狀態將結果分組。

結果是在 [ **名稱** ] 資料行中列出狀態的資料表，以及 [ **群組** ] 資料行中的處理常式。 若要變更資料行標籤，請使用雜湊表，請參閱 [about_Hash_Tables](about_Hash_Tables.md)。 如需詳細資訊，請參閱 [格式資料表](xref:Microsoft.PowerShell.Utility.Format-Table)中的範例。

找出目前的值 `$FormatEnumerationLimit` 。

```powershell
$FormatEnumerationLimit
```

```Output
4
```

列出依 **狀態** 分組的所有服務。 每個狀態的 [ **群組** ] 資料行中最多會列出四項服務，因為的 `$FormatEnumerationLimit` 值為 **4** 。

```powershell
Get-Service | Group-Object -Property Status
```

```Output
Count  Name       Group
-----  ----       -----
60     Running    {AdtAgent, ALG, Ati HotKey Poller, AudioSrv...}
41     Stopped    {Alerter, AppMgmt, aspnet_state, ATI Smart...}
```

若要增加列出的專案數目，請將的值增加 `$FormatEnumerationLimit` 到 **1000** 。 使用 `Get-Service` 和 `Group-Object` 來顯示服務。

```powershell
$FormatEnumerationLimit = 1000
Get-Service | Group-Object -Property Status
```

```Output
Count  Name       Group
-----  ----       -----
60     Running    {AdtAgent, ALG, Ati HotKey Poller, AudioSrv, BITS, CcmExec...
41     Stopped    {Alerter, AppMgmt, aspnet_state, ATI Smart, Browser, CiSvc...
```

使用 `Format-Table` **Wrap** 參數來顯示服務清單。

```powershell
Get-Service | Group-Object -Property Status | Format-Table -Wrap
```

```Output
Count  Name       Group
-----  ----       -----
60     Running    {AdtAgent, ALG, Ati HotKey Poller, AudioSrv, BITS, CcmExec,
                  Client for NFS, CryptSvc, DcomLaunch, Dhcp, dmserver,
                  Dnscache, ERSvc, Eventlog, EventSystem, FwcAgent, helpsvc,
                  HidServ, IISADMIN, InoRPC, InoRT, InoTask, lanmanserver,
                  lanmanworkstation, LmHosts, MDM, Netlogon, Netman, Nla,
                  NtLmSsp, PlugPlay, PolicyAgent, ProtectedStorage, RasMan,
                  RemoteRegistry, RpcSs, SamSs, Schedule, seclogon, SENS,
                  SharedAccess, ShellHWDetection, SMT PSVC, Spooler,
                  srservice, SSDPSRV, stisvc, TapiSrv, TermService, Themes,
                  TrkWks, UMWdf, W32Time, W3SVC, WebClient, winmgmt, wscsvc,
                  wuauserv, WZCSVC, zzInterix}

41     Stopped    {Alerter, AppMgmt, aspnet_state, ATI Smart, Browser, CiSvc,
                  ClipSrv, clr_optimization_v2.0.50727_32, COMSysApp,
                  CronService, dmadmin, FastUserSwitchingCompatibility,
                  HTTPFilter, ImapiService, Mapsvc, Messenger, mnmsrvc,
                  MSDTC, MSIServer, msvsmon80, NetDDE, NetDDEdsdm, NtmsSvc,
                  NVSvc, ose, RasAuto, RDSessMgr, RemoteAccess, RpcLocator,
                  SCardSvr, SwPrv, SysmonLog, TlntSvr, upnphost, UPS, VSS,
                  WmdmPmSN, Wmi, WmiApSrv, xmlprov}
```

### <a name="informationpreference"></a>\$InformationPreference

`$InformationPreference`變數可讓您設定要顯示給使用者的資訊串流喜好設定。 具體來說，您可以藉由新增 [寫入資訊](xref:Microsoft.PowerShell.Utility.Write-Information) Cmdlet 來新增至命令或腳本的參考訊息。 如果使用 **InformationAction** 參數，它的值會覆寫變數的值 `$InformationPreference` 。 `Write-Information` 已在 PowerShell 5.0 中引進。

有效值如下：

- **停止** ：在命令出現時停止命令或腳本 `Write-Information` 。
- **Inquire** ：顯示您在命令中指定的參考用訊息 `Write-Information` ，然後詢問您是否要繼續。
- **繼續** ：顯示資訊訊息，並繼續執行。
- **暫** 止只適用于 PowerShell 6 和以上版本中不支援的工作流程。
- **SilentlyContinue** ： (預設) 沒有任何作用。 不會顯示資訊訊息，腳本會繼續執行而不會中斷。

### <a name="logevent"></a>\$記錄 * 事件

**Log * 事件** 喜好設定變數會決定哪些類型的事件會寫入事件檢視器中的 PowerShell 事件記錄檔。 依預設，只會記錄引擎和提供者事件。 但是，您可以使用 **log * 事件** 喜好設定變數來自訂您的記錄檔，例如記錄有關命令的事件。

**Log * 事件** 喜好設定變數如下所示：

- `$LogCommandHealthEvent`：記錄命令初始化和處理中的錯誤和例外狀況。 預設值為 `$false` (不會) 記錄。
- `$LogCommandLifecycleEvent`：在命令探索中記錄命令的啟動和停止，以及命令管線和安全性例外狀況。 預設值為 `$false` (不會) 記錄。
- `$LogEngineHealthEvent`：記錄會話的錯誤和失敗。 預設值是 `$true` (記錄) 。
- `$LogEngineLifecycleEvent`：記錄會話的開啟和關閉。 預設值是 `$true` (記錄) 。
- `$LogProviderHealthEvent`：記錄提供者錯誤，例如讀取和寫入錯誤、查閱錯誤和調用錯誤。 預設值是 `$true` (記錄) 。
- `$LogProviderLifecycleEvent`：記錄 PowerShell 提供者的新增和移除。 預設值是 `$true` (記錄) 。 如需 PowerShell 提供者的詳細資訊，請參閱 [about_Providers](about_Providers.md)。

若要啟用 **記錄 * 事件** ，請輸入具有值的變數 `$true` ，例如：

```powershell
$LogCommandLifeCycleEvent = $true
```

若要停用事件種類，請輸入值為的變數 `$false` ，例如：

```powershell
$LogCommandLifeCycleEvent = $false
```

您啟用的事件只會對目前的 PowerShell 主控台有效。 若要將設定套用至所有主控台，請將變數設定儲存在您的 PowerShell 設定檔中。 如需詳細資訊，請參閱 [about_Profiles](about_Profiles.md)。

### <a name="maximumhistorycount"></a>\$MaximumHistoryCount

決定目前會話的命令歷程記錄中所儲存的命令數目。

**有效的值** ： 1-32768 (`Int32`) 

**預設值** ：4096

若要判斷命令歷程記錄中目前儲存的命令數目，請輸入：

```powershell
(Get-History).Count
```

若要查看儲存在會話歷程記錄中的命令，請使用 `Get-History` Cmdlet。 如需詳細資訊，請參閱 [about_History](about_History.md)。

### <a name="ofs"></a>\$.OFS

輸出欄位分隔符號 (.OFS) 指定字元來分隔轉換成字串的陣列元素。

**有效的值** ：任何字串。

**預設值** ：空間

根據預設，此 `$OFS` 變數不存在，而且輸出檔分隔符號是一個空格，但是您可以加入這個變數，並將它設定為任何字串。 您可以藉 `$OFS` 由輸入來變更會話中的值 `$OFS="<value>"` 。

> [!NOTE]
> 如果您需要在 `" "` 腳本、模組或設定輸出中 () 空間的預設值，請小心在 `$OFS` 程式碼中的其他位置未變更預設值。

#### <a name="examples"></a>範例

這個範例顯示當陣列轉換成字串時，會使用空格來分隔值。 在此情況下，會將整數陣列儲存在變數中，然後將變數轉換成字串。

```powershell
$array = 1,2,3,4
[string]$array
```

```Output
1 2 3 4
```

若要變更分隔符號，請將 `$OFS` 值指派給該變數。
變數必須命名為 `$OFS` 。

```powershell
$OFS = "+"
[string]$array
```

```Output
1+2+3+4
```

若要還原預設行為，您可以 () 指派空間給 `" "` 值， `$OFS` 或刪除變數。 下列命令會刪除變數，然後確認分隔符號是空格。

```powershell
Remove-Variable OFS
[string]$array
```

```Output
1 2 3 4
```

### <a name="outputencoding"></a>\$OutputEncoding

決定 PowerShell 在將文字傳送至其他應用程式時所使用的字元編碼方法。

例如，如果應用程式將 Unicode 字串傳回到 PowerShell，您可能需要將值變更為 **>unicodeencoding** ，才能正確地傳送字元。

有效的值如下：衍生自編碼類別的物件，例如 **ASCIIEncoding** 、 **SBCSCodePageEncoding** 、 **UTF7Encoding** 、 **UTF8Encoding** 、 **>utf32encoding** 和 **>unicodeencoding** 。

**預設值** ： UTF8Encoding 物件 (UTF8Encoding) 

#### <a name="examples"></a>範例

此範例示範如何在已針對使用 Unicode 字元的語言（例如中文）當地語系化的電腦上，讓 Windows **findstr.exe** 命令在 PowerShell 中運作。

第一個命令會尋找的值 `$OutputEncoding` 。 因為值是編碼物件，所以只會顯示其 **encoding.encodingname** 屬性。

```powershell
$OutputEncoding.EncodingName
```

在此範例中， **findstr.exe** 命令是用來搜尋檔案中有兩個中文字元 `Test.txt` 。 在 Windows 命令提示字元中執行此 **findstr.exe** 命令 ( **cmd.exe** ) ， **findstr.exe** 會尋找文字檔中的字元。 不過，當您在 PowerShell 中執行相同的 **findstr.exe** 命令時，找不到字元，因為 PowerShell 會將它們傳送至 ASCII 文字中的 **findstr.exe** ，而不是 Unicode 文字。

```powershell
findstr <Unicode-characters>
```

若要在 PowerShell 中執行命令，請將的值設定 `$OutputEncoding` 為主控台的 [ **OutputEncoding** ] 屬性值（以針對 Windows 選取的地區設定為基礎）。 由於 **OutputEncoding** 是主控台的靜態屬性，因此請在命令中使用雙冒號 (`::`) 。

```powershell
$OutputEncoding = [console]::OutputEncoding
$OutputEncoding.EncodingName
```

```Output
OEM United States
```

編碼變更之後， **findstr.exe** 命令會尋找 Unicode 字元。

```powershell
findstr <Unicode-characters>
```

```Output
test.txt:         <Unicode-characters>
```

### <a name="progresspreference"></a>\$ProgressPreference

決定 PowerShell 如何回應腳本、Cmdlet 或提供者所產生的進度更新，例如 [寫入進度](xref:Microsoft.PowerShell.Utility.Write-Progress) Cmdlet 所產生的進度列。
此 `Write-Progress` Cmdlet 會建立顯示命令狀態的進度列。

有效值如下：

- **停止** ：不顯示進度列。 相反地，它會顯示錯誤訊息並停止執行。
- **Inquire** ：不顯示進度列。 提示您提供繼續的許可權。 如果您使用 `Y` 或回復 `A` ，則會顯示進度列。
- **繼續** ： (預設) 顯示進度列，並繼續執行。
- **SilentlyContinue** ：執行命令，但不會顯示進度列。

### <a name="psemailserver"></a>\$PSEmailServer

指定用來傳送電子郵件訊息的預設電子郵件伺服器。 傳送電子郵件的 Cmdlet 會使用這個喜好設定變數，例如 [傳送 send-mailmessage](xref:Microsoft.PowerShell.Utility.Send-MailMessage) 指令程式。

### <a name="psdefaultparametervalues"></a>\$PSDefaultParameterValues

指定 Cmdlet 和 advanced 函式之參數的預設值。
的值 `$PSDefaultParameterValues` 是雜湊表，其中索引鍵是由 Cmdlet 名稱和參數名稱所組成，並以冒號分隔 (`:`) 。 值是您指定的自訂預設值。

`$PSDefaultParameterValues` 已在 PowerShell 3.0 中引進。

如需此喜好設定變數的詳細資訊，請參閱 [about_Parameters_Default_Values](about_Parameters_Default_Values.md)。

### <a name="psmoduleautoloadingpreference"></a>\$PSModuleAutoloadingPreference

啟用和停用自動匯入會話中的模組。 **All** 是預設值。 不論變數的值為何，您都可以使用 [import-module](xref:Microsoft.PowerShell.Core.Import-Module) 匯入模組。

有效值為：

- **全部** ：模組會在第一次使用時自動匯入。 若要匯入模組，請取得或使用模組中的任何命令。 例如，使用 `Get-Command`。
- **ModuleQualified** ：只有在使用者使用模組中命令的模組限定名稱時，才會自動匯入模組。 例如，如果使用者輸入，則 `MyModule\MyCommand` PowerShell 會匯入 **MyModule** 模組。
- **無** ：在會話中停用自動匯入模組。 若要匯入模組，請使用 `Import-Module` Cmdlet。

如需自動匯入模組的詳細資訊，請參閱 [about_Modules](about_Modules.md)。

### <a name="pssessionapplicationname"></a>\$PSSessionApplicationName

指定遠端命令的預設應用程式名稱，此命令會使用 Web 服務來管理 (WS-MANAGEMENT) 技術。 如需詳細資訊，請參閱 [關於 Windows 遠端管理](/windows/win32/winrm/about-windows-remote-management)。

系統預設的應用程式名稱是 `WSMAN` ，但您可以使用這個喜好設定變數來變更預設值。

應用程式名稱是連接 URI 中的最後一個節點。 例如，下列範例 URI 中的應用程式名稱為 `WSMAN` 。

`http://Server01:8080/WSMAN`

當遠端命令未指定連接 URI 或應用程式名稱時，就會使用預設的應用程式名稱。

**WinRM** 服務會使用應用程式名稱來選取接聽程式，以服務連線要求。 參數的值應該符合遠端電腦上接聽程式之 **URLPrefix** 屬性的值。

若要覆寫系統預設值和這個變數的值，並為特定會話選取不同的應用程式名稱，請使用 [新的-pssession](xref:Microsoft.PowerShell.Core.New-PSSession)、 [輸入-Pssession](xref:Microsoft.PowerShell.Core.Enter-PSSession)或 [Invoke 命令](xref:Microsoft.PowerShell.Core.Invoke-Command)Cmdlet 的 **ConnectionURI** 或 **ApplicationName** 參數。

`$PSSessionApplicationName`喜好設定變數是在本機電腦上設定的，但它會指定遠端電腦上的接聽程式。 如果您指定的應用程式名稱不存在於遠端電腦上，用來建立會話的命令會失敗。

### <a name="pssessionconfigurationname"></a>\$PSSessionConfigurationName

指定用於在目前會話中建立之 **pssession** 的預設會話設定。

此喜好設定變數是在本機電腦上設定的，但它會指定位於遠端電腦上的會話設定。

變數的值 `$PSSessionConfigurationName` 是完整的資源 URI。

預設值 `http://schemas.microsoft.com/PowerShell/microsoft.PowerShell` 表示遠端電腦上的 **Microsoft PowerShell** 會話設定。

如果您只指定設定名稱，則會在前面加上下列架構 URI：

`http://schemas.microsoft.com/PowerShell/`

您可以使用 **ConfigurationName** `New-PSSession` 、 `Enter-PSSession` 或 Cmdlet 的 ConfigurationName 參數來覆寫預設值，並為特定會話選取不同的會話設定 `Invoke-Command` 。

您可以隨時變更此變數的值。 當您這樣做時，請記住，您選取的會話設定必須存在於遠端電腦上。 如果不是，用來建立使用會話設定之會話的命令會失敗。

當遠端使用者建立連接到這部電腦的會話時，這個喜好設定變數不會決定要使用的本機會話設定。
不過，您可以使用本機會話設定的許可權來判斷哪些使用者可能會使用這些設定。

### <a name="pssessionoption"></a>\$PSSessionOption

在遠端會話中建立 advanced user 選項的預設值。
這些選項喜好設定會覆寫會話選項的系統預設值。

`$PSSessionOption`變數包含 **PSSessionOption** 物件。 如需詳細資訊，請參閱 [PSSessionOption](/dotnet/api/system.management.automation.remoting.pssessionoption)。
物件的每個屬性都代表一個會話選項。 例如， **NoCompression** 屬性會在會話期間開啟資料壓縮。

根據預設， `$PSSessionOption` 變數包含 **PSSessionOption** 物件，其中包含所有選項的預設值，如下所示。

```Output
MaximumConnectionRedirectionCount : 5
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : None
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
IncludePortInSPN                  : False
OutputBufferingMode               : None
Culture                           :
UICulture                         :
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         : 209715200
ApplicationArguments              :
OpenTimeout                       : 00:03:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : -00:00:00.0010000
```

如需這些選項的說明和詳細資訊，請參閱 [PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)。 如需遠端命令和會話的詳細資訊，請參閱 [about_Remote](about_Remote.md) 和 [about_PSSessions](about_PSSessions.md)。

若要變更喜好設定變數的值 `$PSSessionOption` ，請使用 `New-PSSessionOption` Cmdlet 以您偏好的選項值來建立 **PSSessionOption** 物件。 將輸出儲存在名為的變數中 `$PSSessionOption` 。

```powershell
$PSSessionOption = New-PSSessionOption -NoCompression
```

若要 `$PSSessionOption` 在每個 powershell 會話中使用喜好設定變數，請將 `New-PSSessionOption` 建立變數的命令新增 `$PSSessionOption` 至您的 powershell 設定檔。 如需詳細資訊，請參閱 [about_Profiles](about_Profiles.md)。

您可以為特定的遠端會話設定自訂選項。 您所設定的選項會優先于系統預設值和喜好設定變數的值 `$PSSessionOption` 。

若要設定自訂會話選項，請使用 `New-PSSessionOption` Cmdlet 來建立 **PSSessionOption** 物件。 然後，在建立會話的 Cmdlet 中使用 **PSSessionOption** 物件做為 **SessionOption** 參數的值，例如 `New-PSSession` 、 `Enter-PSSession` 和 `Invoke-Command` 。

### <a name="transcript"></a>$Transcript

用 `Start-Transcript` 來指定文字記錄檔的名稱和位置。 如果您未指定 **path** 參數的值，會 `Start-Transcript` 使用全域變數值中的路徑 `$Transcript` 。 如果您尚未建立此變數，請將文字記錄以檔案的 `Start-Transcript` 形式儲存在 `$Home\My Documents` 目錄中 `\PowerShell_transcript.<time-stamp>.txt` 。

### <a name="verbosepreference"></a>\$VerbosePreference

決定 PowerShell 如何回應腳本、Cmdlet 或提供者所產生的詳細資訊訊息，例如 [寫入詳細](xref:Microsoft.PowerShell.Utility.Write-Verbose) 資訊 Cmdlet 所產生的訊息。
詳細資訊訊息說明執行命令所執行的動作。

依預設不會顯示詳細訊息，但您可以藉由變更的值來變更此行為 `$VerbosePreference` 。

您可以使用 Cmdlet 的 **verbose** 一般參數來顯示或隱藏特定命令的詳細資訊訊息。 如需詳細資訊，請參閱 [about_CommonParameters](about_CommonParameters.md)。

有效值如下：

- **停止** ：顯示詳細資訊訊息和錯誤訊息，然後停止執行。
- **Inquire** ：顯示詳細資訊訊息，然後顯示詢問您是否要繼續的提示。
- **繼續** ：顯示詳細資訊訊息，然後繼續執行。
- **SilentlyContinue** ： (預設) 不會顯示詳細資訊訊息。 繼續執行。

#### <a name="examples"></a>範例

這些範例會顯示不同值的效果 `$VerbosePreference` ，以及 **詳細** 資訊參數以覆寫喜好設定值。

此範例顯示 **SilentlyContinue** 值的效果，這是預設值。 此命令會使用 **message** 參數，但不會將訊息寫入 PowerShell 主控台。

```powershell
Write-Verbose -Message "Verbose message test."
```

使用 **Verbose** 參數時，會寫入訊息。

```powershell
Write-Verbose -Message "Verbose message test." -Verbose
```

```Output
VERBOSE: Verbose message test.
```

此範例顯示 **Continue** 值的效果。 `$VerbosePreference`變數設定為 **Continue** ，並顯示訊息。

```powershell
$VerbosePreference = "Continue"
Write-Verbose -Message "Verbose message test."
```

```Output
VERBOSE: Verbose message test.
```

這個範例會使用 **Verbose** 參數，其值 `$false` 會覆寫 **Continue** 值。 不會顯示訊息。

```powershell
Write-Verbose -Message "Verbose message test." -Verbose:$false
```

此範例顯示 **Stop** 值的效果。 `$VerbosePreference`變數已設定為 [ **停止** ]，並顯示訊息。 此命令已停止。

```powershell
$VerbosePreference = "Stop"
Write-Verbose -Message "Verbose message test."
```

```Output
VERBOSE: Verbose message test.
Write-Verbose : The running command stopped because the preference variable
  "VerbosePreference" or common parameter is set to Stop: Verbose message test.
At line:1 char:1
+ Write-Verbose -Message "Verbose message test."
```

這個範例會使用 **Verbose** 參數，其值 `$false` 會覆寫 **停止** 值。 不會顯示訊息。

```powershell
Write-Verbose -Message "Verbose message test." -Verbose:$false
```

此範例顯示 **Inquire** 值的效果。 `$VerbosePreference`變數設定為 **Inquire** 。 訊息隨即顯示，並提示使用者進行確認。

```powershell
$VerbosePreference = "Inquire"
Write-Verbose -Message "Verbose message test."
```

```Output
VERBOSE: Verbose message test.

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

這個範例會使用 **Verbose** 參數，其值 `$false` 會覆寫 **查詢** 值。 系統不會提示使用者，也不會顯示訊息。

```powershell
Write-Verbose -Message "Verbose message test." -Verbose:$false
```

### <a name="warningpreference"></a>\$WarningPreference

決定 PowerShell 如何回應腳本、Cmdlet 或提供者所產生的警告訊息，例如由 [Write-warning](xref:Microsoft.PowerShell.Utility.Write-Warning) Cmdlet 所產生的訊息。

根據預設，會顯示警告訊息並繼續執行，但您可以藉由變更的值來變更此行為 `$WarningPreference` 。

您可以使用 Cmdlet 的 **WarningAction** 一般參數，來判斷 PowerShell 如何回應特定命令的警告。 如需詳細資訊，請參閱 [about_CommonParameters](about_CommonParameters.md)。

有效值如下：

- **停止** ：顯示警告訊息和錯誤訊息，然後停止執行。
- **查詢** ：顯示警告訊息，然後提示您取得繼續的許可權。
- **繼續** ： (預設值) 顯示警告訊息，然後繼續執行。
- **SilentlyContinue** ：不顯示警告訊息。 繼續執行。

#### <a name="examples"></a>範例

這些範例會顯示不同值的效果 `$WarningPreference` 。
**WarningAction** 參數會覆寫喜好設定值。

此範例顯示預設值的效果 [ **Continue** ]。

```powershell
$m = "This action can delete data."
Write-Warning -Message $m
```

```Output
WARNING: This action can delete data.
```

此範例使用 **WarningAction** 參數搭配值 **SilentlyContinue** 來抑制警告。 不會顯示訊息。

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction SilentlyContinue
```

此範例會將 `$WarningPreference` 變數變更為 **SilentlyContinue** 值。 不會顯示訊息。

```powershell
$WarningPreference = "SilentlyContinue"
$m = "This action can delete data."
Write-Warning -Message $m
```

此範例會在產生警告時使用 **WarningAction** 參數來停止。

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction Stop
```

```Output
WARNING: This action can delete data.
Write-Warning : The running command stopped because the preference variable
  "WarningPreference" or common parameter is set to Stop:
    This action can delete data.
At line:1 char:1
+ Write-Warning -Message $m -WarningAction Stop
```

此範例會將 `$WarningPreference` 變數變更為 **查詢** 值。 系統會提示使用者進行確認。

```powershell
$WarningPreference = "Inquire"
$m = "This action can delete data."
Write-Warning -Message $m
```

```Output
WARNING: This action can delete data.

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

此範例使用 **WarningAction** 參數搭配值 **SilentlyContinue** 。 此命令會繼續執行，且不會顯示任何訊息。

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction SilentlyContinue
```

此範例會將 `$WarningPreference` 值變更為 [ **停止** ]。

```powershell
$WarningPreference = "Stop"
$m = "This action can delete data."
Write-Warning -Message $m
```

```Output
WARNING: This action can delete data.
Write-Warning : The running command stopped because the preference variable
  "WarningPreference" or common parameter is set to Stop:
    This action can delete data.
At line:1 char:1
+ Write-Warning -Message $m
```

此範例會使用 **WarningAction** 搭配 **查詢** 值。 出現警告時，系統會提示使用者。

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction Inquire
```

```Output
WARNING: This action can delete data.

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

### <a name="whatifpreference"></a>\$WhatIfPreference

決定是否針對支援的每個命令自動啟用 **WhatIf** 。 當 **WhatIf** 啟用時，此 Cmdlet 會報告命令的預期效果，但不會執行命令。

有效值如下：

- **False** ( **0** ，未啟用) ： (預設) **WhatIf** 不會自動啟用。 若要手動啟用，請使用 Cmdlet 的 **WhatIf** 參數。
- **True** ( **1** ，enabled) ： **WhatIf** 會在任何支援的命令上自動啟用。 使用者可以將 **WhatIf** 參數的值設為 **False** ，以手動方式停用它，例如 `-WhatIf:$false` 。

#### <a name="examples"></a>範例

這些範例會顯示不同值的效果 `$WhatIfPreference` 。
它們會示範如何使用 **WhatIf** 參數來覆寫特定命令的喜好設定值。

此範例顯示 `$WhatIfPreference` 變數設定為預設值 **False** 的效果。 使用 `Get-ChildItem` 確認檔案是否存在。
`Remove-Item` 刪除檔案。 刪除檔案之後，您可以使用確認刪除 `Get-ChildItem` 。

```powershell
Get-ChildItem -Path .\test.txt
Remove-Item -Path ./test.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           9/13/2019    10:53             10 test.txt
```

```powershell
Get-ChildItem -Path .\test.txt
```

```Output
Get-ChildItem : Cannot find path 'C:\Test\test.txt' because it does not exist.
At line:1 char:1
+ Get-ChildItem -File test.txt
```

此範例顯示當的值為 False 時，使用 **WhatIf** 參數的 `$WhatIfPreference` 效果 **False** 。

請確認檔案存在。

```powershell
Get-ChildItem -Path .\test2.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/28/2019    17:06             12 test2.txt
```

使用 **WhatIf** 參數來判斷嘗試刪除檔案的結果。

```powershell
Remove-Item -Path .\test2.txt -WhatIf
```

```Output
What if: Performing the operation "Remove File" on target "C:\Test\test2.txt".
``````

確認未刪除該檔案。

```powershell
Get-ChildItem -Path .\test2.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/28/2019    17:06             12 test2.txt
```

此範例顯示 `$WhatIfPreference` 變數設定為 **True** 的效果。 當您使用刪除檔案時， `Remove-Item` 會顯示檔案的路徑，但不會刪除檔案。

嘗試刪除檔案。 當執行時，會顯示一則訊息 `Remove-Item` ，但不會刪除該檔案。

```powershell
$WhatIfPreference = "True"
Remove-Item -Path .\test2.txt
```

```Output
What if: Performing the operation "Remove File" on target "C:\Test\test2.txt".
```

使用 `Get-ChildItem` 確認未刪除檔案。

```powershell
Get-ChildItem -Path .\test2.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/28/2019    17:06             12 test2.txt
```

這個範例示範當的值為 True 時，如何刪除 `$WhatIfPreference` 檔案 **True** 。 它會使用具有值的 **WhatIf** 參數 `$false` 。 使用 `Get-ChildItem` 確認檔案已刪除。

```powershell
Remove-Item -Path .\test2.txt -WhatIf:$false
Get-ChildItem -Path .\test2.txt
```

```Output
Get-ChildItem : Cannot find path 'C:\Test\test2.txt' because it does not exist.
At line:1 char:1
+ Get-ChildItem -Path .\test2.txt
```

以下是不 `Get-Process` 支援 **whatif** 且 `Stop-Process` 支援 **whatif** 的 Cmdlet 範例。 `$WhatIfPreference`變數的值為 **True** 。

`Get-Process` 不支援 **WhatIf** 。 當命令執行時，它會顯示 **Winword** 處理常式。

```powershell
Get-Process -Name Winword
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    130   119.84     173.38       8.39   15024   4 WINWORD
```

`Stop-Process` 支援 **WhatIf** 。 **Winword** 進程不會停止。

```powershell
Stop-Process -Name Winword
```

```Output
What if: Performing the operation "Stop-Process" on target "WINWORD (15024)".
```

您可以使用 Whatif 參數搭配的值來覆寫 `Stop-Process` **whatif** 行為 **WhatIf** `$false` 。 **Winword** 進程已停止。

```powershell
Stop-Process -Name Winword -WhatIf:$false
```

若要確認 **Winword** 進程已停止，請使用 `Get-Process` 。

```powershell
Get-Process -Name Winword
```

```Output
Get-Process : Cannot find a process with the name "Winword".
  Verify the process name and call the cmdlet again.
At line:1 char:1
+ Get-Process -Name Winword
```

## <a name="see-also"></a>另請參閱

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_CommonParameters](about_CommonParameters.md)

[about_Environment_Variables](about_Environment_Variables.md)

[about_Profiles](about_Profiles.md)

[about_Remote](about_Remote.md)

[about_Scopes](about_Scopes.md)

[about_Variables](about_Variables.md)
