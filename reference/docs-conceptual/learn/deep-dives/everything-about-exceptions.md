---
title: 您想知道有關於例外狀況的一切 (英文)
description: 在撰寫程式碼時，錯誤處理只是生命必經的歷程。
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: cd17ae6b5ded052c93923b648155a4dda8956b34
ms.sourcegitcommit: 94c39b0d36b948d3a62707ae8a3be00efe606434
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012556"
---
# <a name="everything-you-wanted-to-know-about-exceptions"></a>您想知道有關於例外狀況的一切 (英文)

在撰寫程式碼時，錯誤處理只是生命必經的歷程。 我們通常可以檢查並驗證預期行為的條件。 當發生未預期的情況時，我們會轉換成例外狀況處理。 您可以輕鬆地處理其他人的程式碼所產生的例外狀況，或者您可以產生自己的例外狀況供其他人處理。

> [!NOTE]
> 本文的[原始版本][]出自 [@KevinMarquette][] 所撰寫的部落格。 PowerShell 小組感謝 Kevin 分享此內容。 請前往 [PowerShellExplained.com][] 瀏覽他的部落格。

## <a name="basic-terminology"></a>基本術語

我們必須先討論一些基本的詞彙，然後再跳到這一段。

### <a name="exception"></a>例外狀況

例外狀況就像是一般錯誤處理無法處理問題時所建立的事件。
嘗試將以零除某數字或記憶體不足，就是建立例外狀況的一些範例。 有時候，您所使用的程式碼作者會在發生特定問題時，建立例外狀況。

### <a name="throw-and-catch"></a>Throw 與 Catch

發生例外狀況時，我們會說系統擲回例外狀況。 若要處理擲回的例外狀況，您必須加以捕捉。 如果擲回例外狀況，但您未捕捉到任何狀況，指令碼就會停止執行。

### <a name="the-call-stack"></a>呼叫堆疊

呼叫堆疊是已呼叫彼此的函式清單。 呼叫函式時，函式會加入至堆疊或清單頂端。 當函式結束或傳回時，就會從堆疊中移除。

當系統擲回例外狀況時，會檢查該呼叫堆疊，以便讓例外狀況處理常式加以捕捉。

### <a name="terminating-and-non-terminating-errors"></a>終止和非終止錯誤

例外狀況通常是終止錯誤。 系統會捕捉擲回的例外狀況，或終止目前的執行。 根據預設，非終止錯誤是由 `Write-Error` 所產生，並且會將錯誤新增至輸出資料流程而不會擲回例外狀況。

我指出這個問題的原因是，`Write-Error` 和其他非終止錯誤都不會觸發 `catch`。

### <a name="swallowing-an-exception"></a>忍受例外狀況

當您捕捉到錯誤時，就會隱藏錯誤。 請謹慎執行此動作，因為它可能會讓疑難排解問題變得非常艱難。

## <a name="basic-command-syntax"></a>舊版命令語法

以下是 PowerShell 中用以處理基本例外狀況之語法的快速概觀。

### <a name="throw"></a>Throw

若要建立自己的例外狀況事件，我們會擲回具有 `throw` 關鍵字的例外狀況。

```powershell
function Start-Something
{
    throw "Bad thing happened"
}
```

這會建立終止錯誤的執行階段例外狀況。 它是由呼叫函式中的 `catch` 來處理，或是結束具有如下訊息的指令碼。

```powershell
PS> Start-Something

Bad thing happened
At line:1 char:1
+ throw "Bad thing happened"
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (Bad thing happened:String) [], RuntimeException
    + FullyQualifiedErrorId : Bad thing happened
```

#### <a name="write-error--erroraction-stop"></a>Write-Error -ErrorAction Stop

我說過，根據預設，`Write-Error` 不會擲回終止錯誤。 如果您指定 `-ErrorAction Stop`，`Write-Error` 會產生可使用 `catch` 處理的終止錯誤。

```powershell
Write-Error -Message "Houston, we have a problem." -ErrorAction Stop
```

感謝 Lee Dailey 以這種方式使用 `-ErrorAction Stop` 來發出提醒。

#### <a name="cmdlet--erroraction-stop"></a>Cmdlet -ErrorAction Stop

如果您在任何進階函式或 Cmdlet 上指定 `-ErrorAction Stop`，結果會將所有 `Write-Error` 陳述式轉換為停止執行或可由 `catch`處理的終止錯誤。

```powershell
Start-Something -ErrorAction Stop
```

### <a name="trycatch"></a>Try/Catch

例外狀況處理在 PowerShell 中的運作方式 (以及許多其他程式設計語言) 是您先 `try` 一段程式碼，如果它擲回錯誤，您就可以 `catch` 該程式碼。 以下是一個簡短的範例。

```powershell
try
{
    Start-Something
}
catch
{
    Write-Output "Something threw an exception"
}

try
{
    Start-Something -ErrorAction Stop
}
catch
{
    Write-Output "Something threw an exception or used Write-Error"
}
```

只有在發生終止錯誤時，才會執行 `catch` 指令碼。 如果 `try` 正確執行，則會略過 `catch`。

### <a name="tryfinally"></a>Try/Finally

有時候，您不需要處理錯誤，但如果發生例外狀況，仍然需要一些程式碼才能執行。 `finally` 指令碼正是如此。

請看一下這個範例：

```powershell
$command = [System.Data.SqlClient.SqlCommand]::New(queryString, connection)
$command.Connection.Open()
$command.ExecuteNonQuery()
$command.Connection.Close()
```

每當您開啟或連線至資源時，您應該將指令碼關閉。 如果 `ExecuteNonQuery()` 擲回例外狀況，則不會關閉連線。 以下是 `try/finally` 區塊內的相同程式碼。

```powershell
$command = [System.Data.SqlClient.SqlCommand]::New(queryString, connection)
try
{
    $command.Connection.Open()
    $command.ExecuteNonQuery()
}
finally
{
    $command.Connection.Close()
}
```

在此範例中，如果發生錯誤，連線就會關閉。 即使沒有發生錯誤，連線也會關閉。 `finally` 指令碼每次都會執行。

由於您並未捕捉例外狀況，因此例外狀況仍然會傳播至呼叫堆疊。

### <a name="trycatchfinally"></a>Try/Catch/Finally

`catch` 與 `finally` 搭配使用，完全有效。 在大部分的情況下，您會使用其中一種，但您也可能會發現同時使用這兩者的情況。

## <a name="psitem"></a>$PSItem

既然已經瞭解基本概念，我們就可以更加深入地進行探討。

在 `catch` 區塊內，會有類型 `ErrorRecord` 的自動變數 (`$PSItem` 或 `$_`)，其中包含例外狀況的相關詳細資料。 以下是一些重要屬性的快速概觀。

在這些範例中，我在 `ReadAllText` 中使用了無效的路徑來產生這個例外狀況。

```powershell
[System.IO.File]::ReadAllText( '\\test\no\filefound.log')
```

### <a name="psitemtostring"></a>PSItem.ToString()

這會提供您要在記錄和一般輸出中使用的最單純的訊息。 如果 `$PSItem` 放在字串內，則會自動呼叫 `ToString()`。

```powershell
catch
{
    Write-Output "Ran into an issue: $($PSItem.ToString())"
}

catch
{
    Write-Output "Ran into an issue: $PSItem"
}
```

### <a name="psiteminvocationinfo"></a>$PSItem.InvocationInfo

此屬性包含 PowerShell 針對擲回例外狀況的函式或指令碼所收集的其他資訊。 以下是我所建立之範例例外狀況的 `InvocationInfo`。

```powershell
PS> $PSItem.InvocationInfo | Format-List *

MyCommand             : Get-Resource
BoundParameters       : {}
UnboundArguments      : {}
ScriptLineNumber      : 5
OffsetInLine          : 5
ScriptName            : C:\blog\throwerror.ps1
Line                  :     Get-Resource
PositionMessage       : At C:\blog\throwerror.ps1:5 char:5
                        +     Get-Resource
                        +     ~~~~~~~~~~~~
PSScriptRoot          : C:\blog
PSCommandPath         : C:\blog\throwerror.ps1
InvocationName        : Get-Resource
```

此處的重要詳細資料會顯示 `ScriptName`、程式碼的 `Line`，以及叫用開始的 `ScriptLineNumber`。

### <a name="psitemscriptstacktrace"></a>$PSItem.ScriptStackTrace

這個屬性會顯示在產生例外狀況的程式碼中，函式呼叫的順序。

```powershell
PS> $PSItem.ScriptStackTrace
at Get-Resource, C:\blog\throwerror.ps1: line 13
at Start-Something, C:\blog\throwerror.ps1: line 5
at <ScriptBlock>, C:\blog\throwerror.ps1: line 18
```

我只會呼叫相同指令碼中的函式，但如果牽涉到多個指令碼，這會追蹤呼叫。

### <a name="psitemexception"></a>$PSItem.Exception

這是所擲回的實際例外狀況。

#### <a name="psitemexceptionmessage"></a>$PSItem.Exception.Message

這是描述例外狀況的一般訊息，而且在進行疑難排解時，是很好的起點。 大部分的例外狀況都有預設訊息，但是在擲回例外狀況時，也可以設定為自訂內容。

```powershell
PS> $PSItem.Exception.Message

Exception calling "ReadAllText" with "1" argument(s): "The network path was not found."
```

這也是呼叫 `$PSItem.ToString()` 時傳回的訊息 (如果沒有在 `ErrorRecord` 進行設定的話)。

#### <a name="psitemexceptioninnerexception"></a>$PSItem.Exception.InnerException

例外狀況可以包含內部例外狀況。 當您呼叫的程式碼會捕捉到例外狀況，並擲回不同的例外狀況時，通常會發生這種情況。 原始例外狀況會放置在新的例外狀況中。

```powershell
PS> $PSItem.Exception.InnerExceptionMessage
The network path was not found.
```

稍後當我談到重新擲回例外狀況時，我將會重新回顧這種情況。

#### <a name="psitemexceptionstacktrace"></a>$PSItem.Exception.StackTrace

這是例外狀況的 `StackTrace`。 我示範了上述的 `ScriptStackTrace`，不過它的作用在於呼叫受控程式碼。

```Output
at System.IO.FileStream.Init(String path, FileMode mode, FileAccess access, Int32 rights, Boolean
 useRights, FileShare share, Int32 bufferSize, FileOptions options, SECURITY_ATTRIBUTES secAttrs,
 String msgPath, Boolean bFromProxy, Boolean useLongPath, Boolean checkHost)
at System.IO.FileStream..ctor(String path, FileMode mode, FileAccess access, FileShare share, Int32
 bufferSize, FileOptions options, String msgPath, Boolean bFromProxy, Boolean useLongPath, Boolean
 checkHost)
at System.IO.StreamReader..ctor(String path, Encoding encoding, Boolean detectEncodingFromByteOrderMarks,
 Int32 bufferSize, Boolean checkHost)
at System.IO.File.InternalReadAllText(String path, Encoding encoding, Boolean checkHost)
at CallSite.Target(Closure , CallSite , Type , String )
```

當受控程式碼擲回事件時，您只會取得此堆疊追蹤。 我直接呼叫 .NET framework 函式，這就是我們在此範例中可以看到的所有內容。 一般而言，當您在查看堆疊追蹤時，您就是在尋找程式碼的停止位置，以及系統呼叫開始的位置。

## <a name="working-with-exceptions"></a>可以運作，但出現例外狀況

除了基本語法和例外狀況屬性以外，還有更多例外狀況。

### <a name="catching-typed-exceptions"></a>捕捉類型例外狀況

您可以選擇性地使用所捕捉的例外狀況。 例外狀況各具類型，而您可以指定自己想要捕捉的例外狀況類型。

```powershell
try
{
    Start-Something -Path $path
}
catch [System.IO.FileNotFoundException]
{
    Write-Output "Could not find $path"
}
catch [System.IO.IOException]
{
        Write-Output "IO error with the file: $path"
}
```

系統會檢查每個 `catch` 區塊的例外狀況類型，直到找到符合您例外狀況的類型為止。
請務必瞭解，例外狀況可以由其他例外狀況繼承獲得。 在上述範例中，`FileNotFoundException` 便是由 `IOException` 繼承所獲得的。 因此，如果 `IOException` 是第一個，則系統會改為呼叫它。 即使有多個相符例外狀況，也只會叫用一個捕捉區塊。

如果有 `System.IO.PathTooLongException`，`IOException` 會相符，但如果有 `InsufficientMemoryException`，則不會有任何項目捕捉它，而且會向上傳播堆疊。

### <a name="catch-multiple-types-at-once"></a>一次捕捉多個類型

您可以使用相同的 `catch` 陳述式來捕捉多個例外狀況類型。

```powershell
try
{
    Start-Something -Path $path -ErrorAction Stop
}
catch [System.IO.DirectoryNotFoundException],[System.IO.FileNotFoundException]
{
    Write-Output "The path or file was not found: [$path]"
}
catch [System.IO.IOException]
{
    Write-Output "IO error with the file: [$path]"
}
```

感謝您 `/u/Sheppard_Ra` 提出這項新增建議。

### <a name="throwing-typed-exceptions"></a>擲回類型例外狀況

您可以在 PowerShell 中擲回類型例外狀況。 而不是使用字串來呼叫 `throw`：

```powershell
throw "Could not find: $path"
```

使用例外狀況加速器，如下所示：

```powershell
throw [System.IO.FileNotFoundException] "Could not find: $path"
```

但是當您這樣做時，就必須指定訊息。

您也可以建立要擲回之例外狀況的新執行個體。 當您這麼做時，訊息是選擇性的，因為系統具有所有內建例外狀況的預設訊息。

```powershell
throw [System.IO.FileNotFoundException]::new()
throw [System.IO.FileNotFoundException]::new("Could not find path: $path")
```

如果您不是使用 PowerShell 5.0 或更新版本，則必須使用舊版的 `New-Object` 方法。

```powershell
throw (New-Object -TypeName System.IO.FileNotFoundException )
throw (New-Object -TypeName System.IO.FileNotFoundException -ArgumentList "Could not find path: $path")
```

藉由使用類型例外狀況，您 (或其他人) 可以依照上一節所述的類型來捕捉例外狀況。

#### <a name="write-error--exception"></a>Write-Error -Exception

我們可以將這些類型例外狀況新增至 `Write-Error`，而且仍然可以按照例外狀況類型 `catch` 錯誤。 按照列範例所示的方式使用 `Write-Error`：

```powershell
# with normal message
Write-Error -Message "Could not find path: $path" -Exception ([System.IO.FileNotFoundException]::new()) -ErrorAction Stop

# With message inside new exception
Write-Error -Exception ([System.IO.FileNotFoundException]::new("Could not find path: $path")) -ErrorAction Stop

# Pre PS 5.0
Write-Error -Exception ([System.IO.FileNotFoundException]"Could not find path: $path") -ErrorAction Stop

Write-Error -Message "Could not find path: $path" -Exception ( New-Object -TypeName System.IO.FileNotFoundException ) -ErrorAction Stop
```

然後，我們可加以捕捉，如下所示：

```powershell
catch [System.IO.FileNotFoundException]
{
    Write-Log $PSItem.ToString()
}
```

#### <a name="the-big-list-of-net-exceptions"></a>.NET 例外狀況的大型清單

我已藉由 [Reddit/r/PowerShell community][]的協助來編譯主要清單，其中包含數以百計的 .NET 例外狀況，藉此充實這篇文章的內容。

- [.NET 例外狀況的大型清單][]

我一開始先搜尋該清單，找出充分適用於我的情況的例外狀況。 您應該嘗試使用基礎 `System` 命名空間中的例外狀況。

### <a name="exceptions-are-objects"></a>例外狀況皆為物件

如果您開始使用許多類型例外狀況，請記住它們都是物件。 不同的例外狀況有不同的建構函式和屬性。 如果我們查看 `System.IO.FileNotFoundException` 的 [FileNotFoundException][] 檔，我們會看到我們可以傳入的訊息和檔案路徑。

```powershell
[System.IO.FileNotFoundException]::new("Could not find file", $path)
```

而且它具有公開該檔案路徑的 `FileName` 屬性。

```powershell
catch [System.IO.FileNotFoundException]
{
    Write-Output $PSItem.Exception.FileName
}
```

如需其他建構函式和物件屬性，請參閱 [.NET 文件][]。

### <a name="re-throwing-an-exception"></a>重新擲回例外狀況

如果您要在 `catch` 區塊中 `throw` 相同的例外狀況，請不要加以 `catch`。 您應該僅 `catch` 您打算處理的例外狀況，或在例外狀況發生時執行某些動作。

有時候您會想要對例外狀況執行動作，但是系統會重新擲回例外狀況，讓下游可加以處理。 我們可以探索訊息或記錄的所在地附近寫入訊息或記錄問題，卻將問題交給更高層的堆疊處理。

```powershell
catch
{
    Write-Log $PSItem.ToString()
    throw $PSItem
}
```

有趣的是，我們可以從 `catch` 內呼叫 `throw`，然後重新擲回目前的例外狀況。

```powershell
catch
{
    Write-Log $PSItem.ToString()
    throw
}
```

我們想要重新擲回例外狀況，以保留原始的執行資訊 (例如來來源指令碼與行號)。 如果在此時擲回新的例外狀況，它會隱藏例外狀況開始的位置。

#### <a name="re-throwing-a-new-exception"></a>重新擲回例外狀況

若您捕捉某個例外狀況，卻想要擲回不同的例外狀況，則應該將原始例外狀況嵌套在新的例外狀況中。 這可讓其他人在堆疊下進行存取，做為 `$PSItem.Exception.InnerException`。

```powershell
catch
{
    throw [System.MissingFieldException]::new('Could not access field',$PSItem.Exception)
}
```

#### <a name="pscmdletthrowterminatingerror"></a>$PSCmdlet.ThrowTerminatingError()

我不喜歡使用 `throw` 來處理原始例外狀況的問題，就是錯誤訊息會指向 `throw` 的陳述式，並指出該行是問題所在。

```Output
Unable to find the specified file.
At line:31 char:9
+         throw [System.IO.FileNotFoundException]::new()
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (:) [], FileNotFoundException
    + FullyQualifiedErrorId : Unable to find the specified file.
```

出現錯誤訊息指出我的指令碼已中斷，是因為我在第 31 行呼叫 `throw` 是您的指令碼使用者無法看見的錯誤訊息。 該錯誤訊息無法提供任何實用資訊。

Dexter Dhami 指出，我可以使用 `ThrowTerminatingError()` 來加以更正。

```powershell
$PSCmdlet.ThrowTerminatingError(
    [System.Management.Automation.ErrorRecord]::new(
        ([System.IO.FileNotFoundException]"Could not find $Path"),
        'My.ID',
        [System.Management.Automation.ErrorCategory]::OpenError,
        $MyObject
    )
)
```

假設在稱為 `Get-Resource` 的函式內呼叫了 `ThrowTerminatingError()`，這就是我們會看到的錯誤。

```Output
Get-Resource : Could not find C:\Program Files (x86)\Reference
Assemblies\Microsoft\Framework\.NETPortable\v4.6\System.IO.xml
At line:6 char:5
+     Get-Resource -Path $Path
+     ~~~~~~~~~~~~
    + CategoryInfo          : OpenError: (:) [Get-Resource], FileNotFoundException
    + FullyQualifiedErrorId : My.ID,Get-Resource
```

您是否看到它如何指出 `Get-Resource` 函式為問題的來源？ 這會提供使用者實用的資訊。

因為 `$PSItem` 是 `ErrorRecord`，所以我們也可以使用 `ThrowTerminatingError` 以這種方式重新擲回。

```powershell
catch
{
    $PSCmdlet.ThrowTerminatingError($PSItem)
}
```

這會將錯誤的來源變更為 Cmdlet，並將您的函式的內部內容對 Cmdlet 的使用者隱藏。

## <a name="try-can-create-terminating-errors"></a>Try 可以建立終止錯誤

Kirk Munro 指出，在 `try/catch` 區塊中，某些例外狀況僅僅是終止錯誤。 以下是他提供給我的範例，該範例會產生除以零的執行階段例外狀況。

```powershell
function Start-Something { 1/(1-1) }
```

然後叫用例外狀況，如下所示，便會產生錯誤並仍然輸出訊息。

```powershell
&{ Start-Something; Write-Output "We did it. Send Email" }
```

但藉由將相同的程式碼放在 `try/catch` 中，我們會看到出現其他狀況。

```powershell
try
{
    &{ Start-Something; Write-Output "We did it. Send Email" }
}
catch
{
    Write-Output "Notify Admin to fix error and send email"
}
```

我們會看到錯誤變成終止錯誤，而且不會輸出第一個訊息。 我不喜歡這種方式，就是您可以在函式中使用此程式碼，若是有人使用 `try/catch`，則其運作方式便會有所不同。

我還未遇到這個問題，但它是一種需要留意的極端狀況。

### <a name="pscmdletthrowterminatingerror-inside-trycatch"></a>$PSCmdlet.ThrowTerminatingError() inside try/catch

`$PSCmdlet.ThrowTerminatingError()` 的其中一項差異是，它會在您的 Cmdlet 內建立終止錯誤，但是在離開 Cmdlet 之後，它會轉換為非終止錯誤。 這會將負擔留給函式的呼叫者，以決定如何處理錯誤。 他們可以使用 `-ErrorAction Stop` 或從 `try{...}catch{...}`內呼叫它，將其轉換回終止錯誤。

### <a name="public-function-templates"></a>公用函式範本

我對 Kirk Munro 的對話的最後一項要點就是，他在所有的進階函式中都在每個 `begin`、`process` 和 `end` 區塊附近放置 `try{...}catch{...}`。 在這些一般 catch 區塊中，他會使用一行 `$PSCmdlet.ThrowTerminatingError($PSItem)` 來處理所有離開函式的例外狀況。

```powershell
function Start-Something
{
    [CmdletBinding()]
    param()

    process
    {
        try
        {
            ...
        }
        catch
        {
            $PSCmdlet.ThrowTerminatingError($PSItem)
        }
    }
}
```

由於所有內容都是位於其函式內的 `try` 陳述式中，因此所有動作都會以一致的方式運作。 這也會為終端使用者提供清除錯誤，並對產生的錯誤隱藏內部程式碼。

## <a name="trap"></a>陷阱

我將重點放在例外狀況的 `try/catch` 層面。 但是在總結之前，我必須先提一下一個舊版功能。

`trap` 會放在指令碼或函式中，以捕捉出現在該範圍內的所有例外狀況。 發生例外狀況時，會執行 `trap` 中的程式碼，然後再繼續執行正常的程式碼。 如果發生多個例外狀況，則會一再呼叫陷阱。

```powershell
trap
{
    Write-Log $PSItem.ToString()
}

throw [System.Exception]::new('first')
throw [System.Exception]::new('second')
throw [System.Exception]::new('third')
```

我個人從未採用過這種方法，但是我可以在系統管理員或控制器指令碼中看到記錄任何和所有例外狀況的值，然後仍繼續執行。

## <a name="closing-remarks"></a>關閉備註

將適當的例外狀況處理新增至您的指令碼不僅會使其更穩定，還可讓您針對這些例外狀況進行疑難排解時更輕鬆。

我花了很多時間來談論 `throw`，因為這是在討論例外狀況處理時的核心概念。 PowerShell 也提供我們 `Write-Error`，可因應您使用 `throw` 時的所有情況。 因此，請不要認為在閱讀此之後，您必須使用 `throw`。

既然我已經花時間撰寫有關例外狀況處理的詳細資訊，現在我要將重點切換到使用 `Write-Error -Stop` 在我的程式碼中產生錯誤。 我也會採納 Kirk 的建議，並針對每個函數使 `ThrowTerminatingError` 成為我的 goto 例外處理常式。

<!-- link references -->
[powershellexplained.com]: https://powershellexplained.com/
[原始版本]: https://powershellexplained.com/2017-04-10-Powershell-exceptions-everything-you-ever-wanted-to-know/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Reddit/r/PowerShell community]: https://www.reddit.com/r/PowerShell/comments/64866o/kevmar_all_net_46_exceptions_list_for_use_with/
[.NET 例外狀況的大型清單]: https://powershellexplained.com/2017-04-07-all-dotnet-exception-list
[FileNotFoundException]: /dotnet/api/System.IO.FileNotFoundException
[.NET 文件]: /dotnet/api
