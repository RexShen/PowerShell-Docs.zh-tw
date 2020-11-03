---
description: 描述儲存 PowerShell 狀態資訊的變數。 PowerShell 會建立和維護這些變數。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_automatic_variables?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Automatic_Variables
ms.openlocfilehash: 5ce9e61113da2c781f5774866e827663a7c7ced4
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208367"
---
# <a name="about-automatic-variables"></a>關於自動變數

## <a name="short-description"></a>簡短描述

描述儲存 PowerShell 狀態資訊的變數。 PowerShell 會建立和維護這些變數。

## <a name="long-description"></a>完整描述

在概念上，這些變數會被視為唯讀。 雖然它們 **可** 寫入至，但為了回溯相容性， **不應** 將其寫入。

以下是 PowerShell 中的自動變數清單：

### <a name=""></a>$$

包含會話收到的最後一行中的最後一個 token。

### <a name=""></a>$?

包含最後一個命令的執行狀態。 如果最後一個命令成功，則會包含 **True** ，如果失敗，則為 **False** 。

對於在管線中多個階段執行的 Cmdlet 和 advanced 函式（例如在 `process` 和區塊中 `end` ），在 `this.WriteError()` `$PSCmdlet.WriteError()` 任何時間點呼叫或分別會將設定 `$?` 為 **False** ，如同 `this.ThrowTerminatingError()` 和 `$PSCmdlet.ThrowTerminatingError()` 。

Cmdlet 會在 `Write-Error` `$?` 執行之後立即將設定為 **false** ，但在呼叫它的函式中，不會將設定 `$?` 為 **false** ：

```powershell
function Test-WriteError
{
    Write-Error "Bad"
    $? # $false
}

Test-WriteError
$? # $true
```

針對第二個用途， `$PSCmdlet.WriteError()` 應該改為使用。

若為原生命令 (可執行檔) ， `$?` 當是0時，會設定為 **True** `$LASTEXITCODE` ，當為任何其他值時，則設定為 **False** `$LASTEXITCODE` 。

> [!NOTE]
> 除非 PowerShell 7 包含括弧內的語句，否則 `(...)` 子運算式語法 `$(...)` 或陣列運算式 `@(...)` 一律會重設 `$?` 為 **true** ，因此會 `(Write-Error)` 顯示 `$?` 為 **true** 。
> 這已在 PowerShell 7 中變更，因此 `$?` 一律會反映在這些運算式中，最後一個命令執行的實際成功與否。

### <a name=""></a>$^

包含會話收到的最後一行中的第一個 token。

### <a name="_"></a>$_

與 `$PSItem` 相同。 包含管線物件中的目前物件。 您可以在命令中使用這個變數，這些命令會在管線中的每個物件或選取的物件上執行動作。

### <a name="args"></a>$args

包含未宣告參數的值陣列，這些參數會傳遞至函式、腳本或腳本區塊。 當您建立函式時，您可以使用關鍵字來宣告參數，或在函 `param` 式名稱後面的括弧中新增以逗號分隔的參數清單。

在事件動作中， `$Args` 變數包含物件，這些物件代表正在處理之事件的事件引數。 此變數只會填入 `Action` 事件註冊命令的區塊內。
您也可以在傳回的 **PSEventArgs** 物件的 **SourceArgs** 屬性中找到這個變數的值 `Get-Event` 。

### <a name="consolefilename"></a>$ConsoleFileName

包含在 `.psc1` 會話中最近使用的主控台檔案 () 的路徑。 當您使用 **PSConsoleFile** 參數啟動 PowerShell，或使用指令程式將嵌入式 `Export-Console` 管理單元名稱匯出到主控台檔案時，就會填入此變數。

當您使用 `Export-Console` 不含參數的 Cmdlet 時，它會自動更新會話中最近使用的主控台檔案。 您可以使用此自動變數來判斷將更新的檔案。

### <a name="error"></a>$Error

包含錯誤物件的陣列，這些物件表示最新的錯誤。
最新的錯誤是陣列中的第一個錯誤物件 `$Error[0]` 。

若要避免將錯誤新增至 `$Error` 陣列，請使用 **ErrorAction** 一般參數搭配 [ **略** 過] 的值。 如需詳細資訊，請參閱 [about_CommonParameters](about_CommonParameters.md)。

### <a name="event"></a>$Event

包含 **PSEventArgs** 物件，表示正在處理的事件。 此變數只會填入 `Action` 事件註冊命令的區塊中，例如 `Register-ObjectEvent` 。 此變數的值與 Cmdlet 所傳回的物件相同 `Get-Event` 。 因此，您可以 `Event` `$Event.TimeGenerated` 在腳本區塊中使用變數的屬性，例如 `Action` 。

### <a name="eventargs"></a>$EventArgs

包含物件，該物件表示衍生自所處理事件之 **EventArgs** 的第一個事件引數。 此變數只會填入 `Action` 事件註冊命令的區塊內。
您也可以在傳回的 **PSEventArgs** 物件的 **SourceEventArgs** 屬性中找到這個變數的值 `Get-Event` 。

### <a name="eventsubscriber"></a>$EventSubscriber

包含 **PSEventSubscriber** 物件，這個物件表示正在處理之事件的事件訂閱者。 此變數只會填入 `Action` 事件註冊命令的區塊內。 此變數的值與 Cmdlet 所傳回的物件相同 `Get-EventSubscriber` 。

### <a name="executioncontext"></a>$ExecutionCoNtext

包含 **EngineIntrinsics** 物件，該物件代表 PowerShell 主機的執行內容。 您可以使用此變數來尋找可供 Cmdlet 使用的執行物件。

### <a name="false"></a>$false

包含 **False** 。 您可以使用此變數來表示命令和腳本中的 **False** ，而不是使用字串 "False"。 如果字串轉換成非空白字串或非零整數，則可以將該字串解釋為 **True** 。

### <a name="foreach"></a>$foreach

包含 (非 [ForEach](about_ForEach.md) 迴圈的結果值) 的列舉值。 `$ForEach`只有在迴圈執行時，變數才存在，在 `ForEach` 迴圈完成之後就會刪除。

列舉值包含屬性和方法，您可以使用這些屬性和方法來取得迴圈值並變更目前的迴圈反覆運算。 如需詳細資訊，請參閱 [使用枚舉](#using-enumerators)器。

### <a name="home"></a>$HOME

包含使用者主目錄的完整路徑。 此變數相當於 `"$env:homedrive$env:homepath"` Windows 環境變數，通常是 `C:\Users\<UserName>` 。

### <a name="host"></a>$Host

包含物件，該物件表示 PowerShell 的目前主機應用程式。 您可以使用此變數來代表命令中的目前主機，或顯示或變更主機的屬性，例如 `$Host.version` 或或 `$Host.CurrentCulture` `$host.ui.rawui.setbackgroundcolor("Red")` 。

### <a name="input"></a>$input

包含列舉傳遞給函式之所有輸入的列舉值。 `$input`變數僅適用于) 未命名函式 (的函式和腳本區塊。

- 在不含、或區塊的函式中 `Begin` `Process` ，變數會列舉函式 `End` `$input` 所有輸入的集合。

- 在 `Begin` 區塊中， `$input` 變數不包含任何資料。

- 在 `Process` 區塊中， `$input` 變數包含目前在管線中的物件。

- 在 `End` 區塊中， `$input` 變數會列舉函數的所有輸入集合。

  > [!NOTE]
  > 您無法 `$input` 在相同函式或腳本區塊中的進程區塊和 End 區塊內部使用變數。

因為 `$input` 是列舉值，所以存取它的任何屬性都會導致無法 `$input` 再使用。 您可以儲存 `$input` 在另一個變數中，以重複使用這些 `$input` 屬性。

列舉值包含屬性和方法，您可以使用這些屬性和方法來取得迴圈值並變更目前的迴圈反覆運算。 如需詳細資訊，請參閱 [使用枚舉](#using-enumerators)器。

### <a name="iscoreclr"></a>$IsCoreCLR

`$True`如果目前的會話是在 .Net Core 執行時間上執行 (CoreCLR) ，則為 [包含]。 否則會包含 `$False` 。

### <a name="islinux"></a>$IsLinux

包含 `$True` 目前的會話是否正在 Linux 作業系統上執行。
否則會包含 `$False` 。

### <a name="ismacos"></a>$IsMacOS

包含 `$True` 目前的會話是否正在 MacOS 作業系統上執行。
否則會包含 `$False` 。

### <a name="iswindows"></a>$IsWindows

包含 `$TRUE` 目前的會話是否正在 Windows 作業系統上執行。 否則會包含 `$FALSE` 。

### <a name="lastexitcode"></a>$LastExitCode

包含上次執行之 Windows 程式的結束代碼。

### <a name="matches"></a>$Matches

`Matches`變數適用于 `-match` 和 `-notmatch` 運算子。
當您將純量輸入提交給 `-match` 或 `-notmatch` 運算子，且其中一個偵測到相符項時，它們會傳回布林值，並 `$Matches` 以符合的任何字串值的雜湊表填入自動變數。 `$Matches`當您使用正則運算式搭配運算子時，雜湊表也可以填入捕捉 `-match` 。

如需有關運算子的詳細資訊 `-match` ，請參閱 [about_Comparison_Operators](about_comparison_operators.md)。 如需正則運算式的詳細資訊，請參閱 [about_Regular_Expressions](about_Regular_Expressions.md)。

### <a name="myinvocation"></a>$MyInvocation

包含目前命令的相關資訊，例如名稱、參數、參數值，以及如何啟動、呼叫或叫用命令的相關資訊，例如呼叫目前命令的腳本名稱。

`$MyInvocation` 只會填入腳本、函式和腳本區塊。 您可以使用在目前的腳本中傳回的 **InvocationInfo** 物件中的資訊 `$MyInvocation` ，例如腳本的路徑和檔案名 (`$MyInvocation.MyCommand.Path`) 或 () 的函式名稱， `$MyInvocation.MyCommand.Name` 以識別目前的命令。 這特別適合用來尋找目前腳本的名稱。

從 PowerShell 3.0 開始， `MyInvocation` 有下列新屬性。

| 屬性      | 描述                                         |
| ------------- | --------------------------------------------------- |
| **PSScriptRoot**  | 包含已叫用之腳本的完整路徑   |
|               | 目前的命令。 這個屬性的值為  |
|               | 只有在呼叫端為腳本時才會填入。         |
| **PSCommandPath** | 包含腳本的完整路徑和檔案名  |
|               | ，叫用目前的命令。 這個的值 |
|               | 只有當呼叫端為時，才會填入屬性     |
|               | 指令碼。                                             |

不同于 `$PSScriptRoot` 和 `$PSCommandPath` 自動變數，自動變數的 **PSScriptRoot** 和 **PSCommandPath** 屬性 `$MyInvocation` 會包含啟動程式或呼叫腳本的相關資訊，而不是目前的腳本。

### <a name="nestedpromptlevel"></a>$NestedPromptLevel

包含目前的提示層級。 0值表示原始提示層級。 當您輸入嵌套層級時，值會遞增，而當您結束時，該值會遞減。

例如，當您使用方法時，PowerShell 會顯示一個嵌套的命令提示字元 `$Host.EnterNestedPrompt` 。 當您進入 PowerShell 偵錯工具中的中斷點時，PowerShell 也會顯示一個嵌套的命令提示字元。

當您輸入嵌套提示字元時，PowerShell 會暫停目前的命令、儲存執行內容，並遞增變數的值 `$NestedPromptLevel` 。 若要建立額外的嵌套命令提示字元 (最多128層級) 或返回原始命令提示字元，請完成命令或輸入 `exit` 。

此 `$NestedPromptLevel` 變數可協助您追蹤提示層級。 您可以建立包含此值的替代 PowerShell 命令提示字元，讓它一律可見。

### <a name="null"></a>$null

`$null` 這是包含 **null** 或空白值的自動變數。 您可以使用此變數來代表命令和腳本中不存在或未定義的值。

PowerShell 會將 `$null` 值視為具有值的物件，也就是明確的預留位置，因此您可以使用在 `$null` 一系列的值中表示空的值。

例如，當 `$null` 集合中包含時，會計算為其中一個物件。

```powershell
$a = "one", $null, "three"
$a.count
```

```Output
3
```

如果您使用管線將 `$null` 變數傳送至 `ForEach-Object` Cmdlet，它會產生的值 `$null` ，就像是對其他物件所做的一樣。

```powershell
"one", $null, "three" | ForEach-Object { "Hello " + $_}
```

```Output
Hello one
Hello
Hello three
```

因此，您無法使用 `$null` 來表示 **沒有參數值** 。 的參數值會 `$null` 覆寫預設參數值。

不過，因為 PowerShell 會將 `$null` 變數視為預留位置，所以您可以在如下的腳本中使用它，如果被忽略，就不會有作用 `$null` 。

```powershell
$calendar = @($null, $null, "Meeting", $null, $null, "Team Lunch", $null)
$days = "Sunday","Monday","Tuesday","Wednesday","Thursday",
        "Friday","Saturday"
$currentDay = 0
foreach($day in $calendar)
{
    if($day -ne $null)
    {
        "Appointment on $($days[$currentDay]): $day"
    }

    $currentDay++
}
```

```Output
Appointment on Tuesday: Meeting
Appointment on Friday: Team lunch
```

### <a name="pid"></a>$PID

包含裝載目前 PowerShell 會話之進程 (PID) 的處理序識別碼。

### <a name="profile"></a>$PROFILE

包含目前使用者和目前主機應用程式之 PowerShell 設定檔的完整路徑。 您可以使用此變數來代表命令中的設定檔。 例如，您可以在命令中使用它來判斷是否已建立設定檔：

```powershell
Test-Path $PROFILE
```

或者，您可以在命令中使用它來建立設定檔：

```powershell
New-Item -ItemType file -Path $PROFILE -Force
```

您可以在命令中使用它，在 **notepad.exe** 中開啟設定檔：

```powershell
notepad.exe $PROFILE
```

### <a name="psboundparameters"></a>$PSBoundParameters

包含傳遞至腳本或函式之參數的字典，以及其目前的值。 此變數只有在宣告參數的範圍中具有值，例如腳本或函式。 您可以使用它來顯示或變更目前的參數值，或將參數值傳遞至另一個腳本或函式。

在此範例中， **Test2** 函式會將傳遞 `$PSBoundParameters` 至 **Test1** 函數。 `$PSBoundParameters`會以索引 **鍵** 和 **值** 的格式顯示。

```powershell
function Test1 {
   param($a, $b)

   # Display the parameters in dictionary format.
   $PSBoundParameters
}

function Test2 {
   param($a, $b)

   # Run the Test1 function with $a and $b.
   Test1 @PSBoundParameters
}
```

```powershell
Test2 -a Power -b Shell
```

```Output
Key   Value
---   -----
a     Power
b     Shell
```

### <a name="pscmdlet"></a>$PSCmdlet

包含物件，該物件表示正在執行的 Cmdlet 或 advanced 函數。

您可以在 Cmdlet 或函式程式碼中使用物件的屬性和方法，以回應使用的條件。 例如， **ParameterSetName** 屬性包含所使用之參數集的名稱，而 **ShouldProcess** 方法會動態地將 **WhatIf** 和 **Confirm** 參數新增至 Cmdlet。

如需自動變數的詳細資訊 `$PSCmdlet` ，請參閱 [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md) 和 [about_Functions_Advanced](about_Functions_Advanced.md)。

### <a name="pscommandpath"></a>$PSCommandPath

包含正在執行之腳本的完整路徑和檔案名。 此變數在所有腳本中都是有效的。

### <a name="psculture"></a>$PSCulture

從 PowerShell 7 開始，會 `$PSCulture` 反映目前 PowerShell 運行時 (會話) 的文化特性。 如果 PowerShell 執行時間中的文化特性有所變更，則 `$PSCulture` 會更新該執行時間的值。

文化特性會決定專案（例如數位、貨幣及日期）的顯示格式，並且儲存在 **system.string 物件中。** 用 `Get-Culture` 來顯示電腦的文化特性。 `$PSCulture` 包含 **Name** 屬性的值。

### <a name="psdebugcontext"></a>$PSDebugCoNtext

在進行調試時，此變數包含有關調試環境的資訊。 否則，它會包含 **null** 值。 因此，您可以使用它來指出偵錯工具是否有控制權。 填入時，它會包含具有 **中斷點** 和 **InvocationInfo** 屬性的 **PsDebugCoNtext** 物件。 **InvocationInfo** 屬性有數個有用的屬性，包括 **Location** 屬性。 **Location** 屬性指出正在進行調試的腳本路徑。

### <a name="pshome"></a>$PSHOME

包含 PowerShell 安裝目錄的完整路徑（通常是 `$env:windir\System32\PowerShell\v1.0` 在 Windows 系統中）。 您可以在 PowerShell 檔案的路徑中使用此變數。 例如，下列命令會在概念說明主題中搜尋單字 **變數** ：

```powershell
Select-String -Pattern Variable -Path $pshome\*.txt
```

### <a name="psitem"></a>$PSItem

與 `$_` 相同。 包含管線物件中的目前物件。 您可以在命令中使用這個變數，這些命令會在管線中的每個物件或選取的物件上執行動作。

### <a name="psscriptroot"></a>$PSScriptRoot

包含正在執行腳本的目錄。

在 PowerShell 2.0 中，此變數僅適用于腳本模組 (`.psm1`) 。
從 PowerShell 3.0 開始，它在所有腳本中都是有效的。

### <a name="pssenderinfo"></a>$PSSenderInfo

包含啟動 PSSession 之使用者的相關資訊，包括原始電腦的使用者身分識別和時區。 此變數僅適用于 Pssession。

`$PSSenderInfo`變數包含使用者可設定的屬性 **ApplicationArguments** ，預設只會包含 `$PSVersionTable` 來自原始會話的。 若要將資料新增至 **ApplicationArguments** 屬性，請使用 Cmdlet 的 **ApplicationArguments** 參數 `New-PSSessionOption` 。

### <a name="psuiculture"></a>$PSUICulture

包含目前正在作業系統中使用的使用者介面 (UI) 文化特性的名稱。 UI 文化特性會決定要將哪些文字字串用於使用者介面元素，例如功能表和訊息。 這是系統 **System.Globalization.CultureInfo.CurrentUICulture.Name** 屬性的值。 若要取得系統的 **system.object** 物件，請使用 `Get-UICulture` Cmdlet。

### <a name="psversiontable"></a>$PSVersionTable

包含唯讀的雜湊表，顯示目前會話中執行的 PowerShell 版本的詳細資料。 資料表包含下列專案：

| 屬性                  | 描述                                   |
| ------------------------- | --------------------------------------------- |
| **PSVersion**             | PowerShell 版本號碼                 |
| **PSEdition**             | 這個屬性的值為  |
|                           | PowerShell 4 和更低的 powershell，以及 PowerShell  |
|                           | 5.1 在功能完整的 Windows 版本上。        |
|                           | 這個屬性的值為 < Core     |
|                           | PowerShell 6 和更新版本，以及 PowerShell  |
|                           | 低使用量版本上的 PowerShell 5。1  |
|                           | 就像 Windows Nano Server 或 Windows IoT 一樣。      |
| **GitCommitId**           | 來源檔案在 GitHub 中的認可識別碼 |
| **作業系統**                    | 作業系統的描述      |
|                           | PowerShell 正在執行。                     |
| **平台**              | 作業系統正在執行的平臺 |
|                           | 開啟。 Linux 和 macOS 上的值為 **Unix** 。 |
|                           | 請參閱 `$IsMacOs` 和 `$IsLinux`。                |
| **PSCompatibleVersions**  | 相容的 PowerShell 版本    |
|                           | 使用目前的版本                      |
| **PSRemotingProtocolVersion** | PowerShell 遠端版本      |
|                           | 管理通訊協定。                          |
| **SerializationVersion**  | 序列化方法的版本       |
| **WSManStackVersion**     | WS-Management 堆疊的版本號碼 |

### <a name="pwd"></a>$PWD

包含代表目前的目錄完整路徑的路徑物件。

### <a name="sender"></a>$Sender

包含產生這個事件的物件。 此變數只會填入事件註冊命令的動作區塊內。 這個變數的值也可以在傳回之 **PSEventArgs** 物件的寄件者屬性中找到 `Get-Event` 。

### <a name="shellid"></a>$ShellId

包含目前 shell 的識別碼。

### <a name="stacktrace"></a>$StackTrace

包含最近錯誤的堆疊追蹤。

### <a name="switch"></a>$switch

包含列舉值，而不是語句的結果值 `Switch` 。 `$switch`只有當語句正在執行時，變數才存在 `Switch` ; 當語句完成執行時，就會刪除此變數 `switch` 。 如需詳細資訊，請參閱 [about_Switch](about_Switch.md)。

列舉值包含屬性和方法，您可以使用這些屬性和方法來取得迴圈值並變更目前的迴圈反覆運算。 如需詳細資訊，請參閱 [使用枚舉](#using-enumerators)器。

### <a name="this"></a>$this

在定義腳本屬性或腳本方法的腳本區塊中， `$this` 變數會參考正在擴充的物件。

在自訂類別中， `$this` 變數會參考類別物件本身，以允許存取類別中定義的屬性和方法。

### <a name="true"></a>$true

包含 **True** 。 您可以使用此變數來表示命令和腳本中的 **True** 。

## <a name="using-enumerators"></a>使用枚舉器

`$input`、 `$foreach` 和變數全都 `$switch` 是用來逐一查看其包含程式碼區塊所處理之值的枚舉器。

列舉值包含屬性和方法，您可以使用這些屬性和方法來向前或重設反復專案，或取得反復專案值。 直接操作列舉值不會被視為最佳做法。

- 在迴圈中，應偏好流量控制關鍵字 [break](about_Break.md) 和 [continue](about_Continue.md) 。
- 在接受管線輸入的函式中，最佳做法是使用參數搭配 **ValueFromPipeline** 或 **ValueFromPipelineByPropertyName** 屬性。

  如需詳細資訊，請參閱 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)。

### <a name="movenext"></a>MoveNext

[MoveNext](/dotnet/api/system.collections.ienumerator.movenext)方法會將列舉值前移至集合中的下一個元素。 如果列舉 **值** 成功地前移， **MoveNext** 會傳回 True，如果列舉值已超過集合的結尾，則 **為 False** 。

> [!NOTE]
> 傳回 my **MoveNext** 的 **布林** 值會傳送到輸出資料流程。
> 您可以 typecasting 輸出， `[void]` 或將其輸送至 [Out-Null](xref:Microsoft.PowerShell.Core.Out-Null)，以隱藏輸出。
>
> ```powershell
> $input.MoveNext() | Out-Null
> ```
>
> ```powershell
> [void]$input.MoveNext()
> ```

### <a name="reset"></a>重設

[Reset](/dotnet/api/system.collections.ienumerator.reset)方法會將列舉值設定為其初始位置，這是在集合中的第一個元素 **之前** 。

### <a name="current"></a>目前

[目前](/dotnet/api/system.collections.ienumerator.current)的屬性會取得集合中的元素，或在目前列舉值的位置中的管線。

**目前** 的屬性會繼續傳回相同的屬性，直到呼叫 **MoveNext** 為止。

## <a name="examples"></a>範例

### <a name="example-1-using-the-input-variable"></a>範例1：使用 $input 變數

在下列範例中，存取 `$input` 變數會清除變數，直到下一次進程區塊執行為止。 使用 **Reset** 方法會將變數重設 `$input` 為目前的管線值。

```powershell
function Test
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        "`tInput: $input"
        "`tAccess Again: $input"
        $input.Reset()
        "`tAfter Reset: $input"
    }
}

"one","two" | Test
```

```Output
Iteration: 0
    Input: one
    Access Again:
    After Reset: one
Iteration: 1
    Input: two
    Access Again:
    After Reset: two
```

即使您未存取，進程區塊也會自動將變數往前移 `$input` 。

```powershell
$skip = $true
function Skip
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        if ($skip)
        {
            "`tSkipping"
            $skip = $false
        }
        else
        {
            "`tInput: $input"
        }
    }
}

"one","two" | Skip
```

```Output
Iteration: 0
    Skipping
Iteration: 1
    Input: two
```

### <a name="example-2-using-input-outside-the-process-block"></a>範例2：在進程區塊之外使用 $input

在進程區塊外部， `$input` 變數代表所有輸送至函式的值。

- 存取 `$input` 變數會清除所有值。
- **Reset** 方法會重設整個集合。
- 永遠不會填入 **目前** 的屬性。
- **MoveNext** 方法會傳回 false，因為集合無法是先進的。
  - 呼叫 **MoveNext** 會清除 `$input` 變數。

```powershell
Function All
{
    "All Values: $input"
    "Access Again: $input"
    $input.Reset()
    "After Reset: $input"
    $input.MoveNext() | Out-Null
    "After MoveNext: $input"
}

"one","two","three" | All
```

```Output
All Values: one two three
Access Again:
After Reset: one two three
After MoveNext:
```

### <a name="example-3-using-the-inputcurrent-property"></a>範例3：使用 $input。Current 屬性

藉由使用 **current** 屬性，可以在不使用 **Reset** 方法的情況下多次存取目前的管線值。 進程區塊不會自動呼叫 **MoveNext** 方法。

除非您明確呼叫 **MoveNext** ，否則永遠不會填入 **目前** 的屬性。 您可以在進程區塊內多次存取 **目前** 的屬性，而不需要清除其值。

```powershell
function Current
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        "`tBefore MoveNext: $($input.Current)"
        $input.MoveNext() | Out-Null
        "`tAfter MoveNext: $($input.Current)"
        "`tAccess Again: $($input.Current)"
    }
}

"one","two" | Current
```

```Output
Iteration: 0
    Before MoveNext:
    After MoveNext: one
    Access Again: one
Iteration: 1
    Before MoveNext:
    After MoveNext: two
    Access Again: two
```

### <a name="example-4-using-the-foreach-variable"></a>範例4：使用 $foreach 變數

與變數不同的 `$input` 是， `$foreach` 當直接存取時，變數一律會代表集合中的所有專案。 使用 **current** 屬性來存取目前的 collection 元素，以及使用 **Reset** 和 **MoveNext** 方法來變更其值。

> [!NOTE]
> 迴圈的每個反復專案 `foreach` 都會自動呼叫 **MoveNext** 方法。

下列迴圈只會執行兩次。 在第二個反復專案中，集合會在反覆運算完成之前移至第三個元素。 在第二個反復專案之後，現在沒有可逐一查看的值，而且迴圈會結束。

**MoveNext** 屬性不會影響已選擇逐一查看集合 () 的變數 `$Num` 。

```powershell
$i = 0
foreach ($num in ("one","two","three"))
{
    "Iteration: $i"
    $i++
    "`tNum: $num"
    "`tCurrent: $($foreach.Current)"

    if ($foreach.Current -eq "two")
    {
        "Before MoveNext (Current): $($foreach.Current)"
        $foreach.MoveNext() | Out-Null
        "After MoveNext (Current): $($foreach.Current)"
        "Num has not changed: $num"
    }
}
```

```Output
Iteration: 0
        Num: one
        Current: one
Iteration: 1
        Num: two
        Current: two
Before MoveNext (Current): two
After MoveNext (Current): three
Num has not changed: two
```

使用 **Reset** 方法會重設集合中目前的元素。 下列範例會迴圈執行前兩個元素 **兩次** ，因為會呼叫 **Reset** 方法。 在前兩個迴圈之後， `if` 語句會失敗，而且迴圈會正常地逐一查看所有三個元素。

> [!IMPORTANT]
> 這可能會導致無限迴圈。

```powershell
$stopLoop = 0
foreach ($num in ("one","two", "three"))
{
    ("`t" * $stopLoop) + "Current: $($foreach.Current)"

    if ($num -eq "two" -and $stopLoop -lt 2)
    {
        $foreach.Reset() | Out-Null
        ("`t" * $stopLoop) + "Reset Loop: $stopLoop"
        $stopLoop++
    }
}
```

```Output
Current: one
Current: two
Reset Loop: 0
        Current: one
        Current: two
        Reset Loop: 1
                Current: one
                Current: two
                Current: three
```

### <a name="example-5-using-the-switch-variable"></a>範例5：使用 $switch 變數

`$switch`變數與變數具有完全相同的規則 `$foreach` 。
下列範例示範所有列舉值概念。

> [!NOTE]
> 請注意， **NotEvaluated** 即使 `break` **MoveNext** 方法之後沒有語句，NotEvaluated 案例也不會執行。

```powershell
$values = "Start", "MoveNext", "NotEvaluated", "Reset", "End"
$stopInfinite = $false
switch ($values)
{
    "MoveNext" {
        "`tMoveNext"
        $switch.MoveNext() | Out-Null
        "`tAfter MoveNext: $($switch.Current)"
    }
    # This case is never evaluated.
    "NotEvaluated" {
        "`tAfterMoveNext: $($switch.Current)"
    }

    "Reset" {
        if (!$stopInfinite)
        {
            "`tReset"
            $switch.Reset()
            $stopInfinite = $true
        }
    }

    default {
        "Default (Current): $($switch.Current)"
    }
}
```

```Output
Default (Current): Start
    MoveNext
    After MoveNext: NotEvaluated
    Reset
Default (Current): Start
    MoveNext
    After MoveNext: NotEvaluated
Default (Current): End
```

## <a name="see-also"></a>另請參閱

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Hash_Tables](about_Hash_Tables.md)

[about_Preference_Variables](about_Preference_Variables.md)

[about_Splatting](about_Splatting.md)

[about_Variables](about_Variables.md)

