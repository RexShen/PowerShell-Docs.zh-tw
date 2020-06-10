---
title: 您想知道有關於 Switch 陳述式的一切
description: PowerShell 中的 Switch 陳述式提供了在其他語言中無法找到的功能。
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: ebf6191d56374273465ae6bee49ef82a02cc1580
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149421"
---
# <a name="everything-you-ever-wanted-to-know-about-the-switch-statement"></a>您想知道有關於 Switch 陳述式的一切

與其他語言相似，PowerShell 具備在您指令碼中控制執行流程的命令。 其中一個這類陳述式便是 [switch][] 陳述式，其在 PowerShell 中提供了在其他語言中無法找到的功能。 今天，我們會深入探討使用 PowerShell 的 `switch`。

> [!NOTE]
> 此[原文][]出自 [@KevinMarquette][] 所撰寫的部落格。 PowerShell 小組感謝 Kevin 分享此內容。 請前往 [PowerShellExplained.com][] 瀏覽 Kevin 的部落格。

## <a name="if-statement"></a>If 陳述式

您所學到的一個陳述式是 `if` 陳述式。 其可以讓您在陳述式為 `$true` 時執行指令碼區塊。

``` powershell
if ( Test-Path $Path )
{
    Remove-Item $Path
}
```

您可以透過使用 `elseif` 和 `else` 陳述式來擁有更複雜的邏輯。 在以下範例，我擁有一個代表星期幾的數值，並且我希望將該名稱作為字串取得。

``` powershell
$day = 3

if ( $day -eq 0 ) { $result = 'Sunday'        }
elseif ( $day -eq 1 ) { $result = 'Monday'    }
elseif ( $day -eq 2 ) { $result = 'Tuesday'   }
elseif ( $day -eq 3 ) { $result = 'Wednesday' }
elseif ( $day -eq 4 ) { $result = 'Thursday'  }
elseif ( $day -eq 5 ) { $result = 'Friday'    }
elseif ( $day -eq 6 ) { $result = 'Saturday'  }

$result
```

```Output
Wednesday
```

事實證明這是一個相當常見的模式，且有許多方式可以處理這種模式。 其中一個便是使用 `switch`。

## <a name="switch-statement"></a>Switch 陳述式

`switch` 陳述式可以讓您提供一個變數及可能值的清單。 若該值與變數相符，便會執行其 ScriptBlock。

``` powershell
$day = 3

switch ( $day )
{
    0 { $result = 'Sunday'    }
    1 { $result = 'Monday'    }
    2 { $result = 'Tuesday'   }
    3 { $result = 'Wednesday' }
    4 { $result = 'Thursday'  }
    5 { $result = 'Friday'    }
    6 { $result = 'Saturday'  }
}

$result
```

```Output
'Wednesday'
```

針對此範例，`$day` 的值與其中一個數值相符，接著便會將正確的名稱指派給 `$result`。 我們在此範例中只會執行變數指派，但在這些指令碼區塊中可以執行任何 PowerShell。

### <a name="assign-to-a-variable"></a>指派給變數

我們可以透過另外一種方式撰寫上一個範例。

``` powershell
$result = switch ( $day )
{
    0 { 'Sunday'    }
    1 { 'Monday'    }
    2 { 'Tuesday'   }
    3 { 'Wednesday' }
    4 { 'Thursday'  }
    5 { 'Friday'    }
    6 { 'Saturday'  }
}
```

我們可以將值置於 PowerShell 管線上，然後將其指派給 `$result`。 您可以使用 `if` 和 `foreach` 陳述式執行相同的操作。

### <a name="default"></a>預設

我們可以使用 `default` 關鍵字來辨別在沒有相符項目時會發生的情況。

``` powershell
$result = switch ( $day )
{
    0 { 'Sunday' }
    # ...
    6 { 'Saturday' }
    default { 'Unknown' }
}
```

在此處我們會在預設案例中傳回 `Unknown` 值。

### <a name="strings"></a>字串

我在最後幾個範例中比對了數字，但您也可以比對字串。

``` powershell
$item = 'Role'

switch ( $item )
{
    Component
    {
        'is a component'
    }
    Role
    {
        'is a role'
    }
    Location
    {
        'is a location'
    }
}
```

```Output
is a role
```

我決定不把 `Component`、`Role` 和 `Location` 比對括在引號中，以表示這些是選擇性的。 `switch` 在大多數的案例中會將這些項目作為字串處理。

## <a name="arrays"></a>陣列

PowerShell `switch` 其中一項很酷的功能就是其處理陣列的方式。 若您將一個陣列提供給 `switch`，其便會處理該集合中的每個項目。

``` powershell
$roles = @('WEB','Database')

switch ( $roles ) {
    'Database'   { 'Configure SQL' }
    'WEB'        { 'Configure IIS' }
    'FileServer' { 'Configure Share' }
}
```

```Output
Configure IIS
Configure SQL
```

若陣列中包含重複的項目，會將其在適當的區段中多次比對。

### <a name="psitem"></a>PSItem

您可以使用 `$PSItem` 或 `$_` 來參考目前的處理項目。 當我們進行簡單的比對時，`$PSItem` 便是我們正在比對的值。 我會在下一節進行一些進階比對，並且在這些進階比對中使用此變數。

## <a name="parameters"></a>參數

PowerShell `switch` 的獨特功能便是其具備許多 [switch 參數][]，可以變更其執行的方式。

### <a name="-casesensitive"></a>-CaseSensitive

根據預設，相符的項目不區分大小寫。 若您需要區分大小寫，可以使用 `-CaseSensitive`。 其可以與其他 switch 參數一起使用。

### <a name="-wildcard"></a>-Wildcard

我們可以使用 `-wildcard` switch 來啟用萬用字元支援。 其會使用與 `-like` 運算子相同的萬用字元邏輯來進行每個比對。

``` powershell
$Message = 'Warning, out of disk space'

switch -Wildcard ( $message )
{
    'Error*'
    {
        Write-Error -Message $Message
    }
    'Warning*'
    {
        Write-Warning -Message $Message
    }
    default
    {
        Write-Information $message
    }
}
```

```Output
WARNING: Warning, out of disk space
```

我們會在此處處理訊息，然後根據訊息的內容將其輸出到不同的串流上。

### <a name="-regex"></a>-Regex

switch 陳述式支援 RegEx 比對，就跟其支援萬用字元一樣。

``` powershell
switch -Regex ( $message )
{
    '^Error'
    {
        Write-Error -Message $Message
    }
    '^Warning'
    {
        Write-Warning -Message $Message
    }
    default
    {
        Write-Information $message
    }
}
```

我在我寫的另外一篇文章中包含了更多使用 RegEx 的範例：[使用 RegEx 的許多方式][]。

### <a name="-file"></a>-File

Switch 陳述式少為人知的功能是可以透過 `-File` 參數來處理檔案。 您可以搭配檔案的路徑使用 `-file`，而非為其提供變數運算式。

``` powershell
switch -Wildcard -File $path
{
    'Error*'
    {
        Write-Error -Message $PSItem
    }
    'Warning*'
    {
        Write-Warning -Message $PSItem
    }
    default
    {
        Write-Output $PSItem
    }
}
```

其運作方式跟處理陣列類似。 在此範例中，我會將其與萬用字元比對組合，並使用 `$PSItem`。 這會處理記錄檔，並根據 RegEx 比對項目將其轉換成警告和錯誤訊息。

## <a name="advanced-details"></a>進階詳細資料

現在您已了解所記載的所有功能，我們便可以在更進階處理的內容中使用這些功能。

### <a name="expressions"></a>運算式

`switch` 可以改為在運算式上使用，而非變數。

``` powershell
switch ( ( Get-Service | Where status -eq 'running' ).name ) {...}
```

運算式所要評估的值會是用於該比對的值。

### <a name="multiple-matches"></a>多個比對項目

您可能已經使用過這項功能，但 `switch` 可以比對多個條件。 這在使用 `-wildcard` 或 `-regex` 進行比對時更是如此。 您可以多次新增相同的條件，這些條件都會觸發。

``` powershell
switch ( 'Word' )
{
    'word' { 'lower case word match' }
    'Word' { 'mixed case word match' }
    'WORD' { 'upper case word match' }
}
```

```Output
lower case word match
mixed case word match
upper case word match
```

這三個陳述式全部都會觸發。 這代表每個條件都會進行檢查 (按照順序)。 這在處理陣列時也是如此，陣列中的每個項目會檢查每個條件。

### <a name="continue"></a>Continue

一般而言，我會在此處介紹 `break` 陳述式，但先了解如何使用 `continue` 會更好。 就像 `foreach` 迴圈一樣，`continue` 會繼續執行集合中的下一個項目，或是在沒有其他項目時結束 `switch`。 我們可以使用 continue 陳述式重新撰寫上一個範例，使其只執行一個陳述式。

``` powershell
switch ( 'Word' )
{
    'word'
    {
        'lower case word match'
        continue
    }
    'Word'
    {
        'mixed case word match'
        continue
    }
    'WORD'
    {
        'upper case word match'
        continue
    }
}
```

```Output
lower case word match
```

switch 會比對第一個項目，然後便會繼續執行下一個值，而非比對全部的三個項目。 因為沒有任何要處理的值，所以 switch 會結束。 下一個範例顯示了萬用字元比對多個項目的方式。

``` powershell
switch -Wildcard -File $path
{
    '*Error*'
    {
        Write-Error -Message $PSItem
        continue
    }
    '*Warning*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    default
    {
        Write-Output $PSItem
    }
}
```

因為輸入檔中的行可能會同時包含 `Error` 和 `Warning` 字詞，我們只希望執行第一個字詞，然後繼續處理檔案。

### <a name="break"></a>中斷

`break` 陳述式會結束 switch。 這與 `continue` 針對單一值所呈現的行為相同。 其差異會在處理陣列時顯示。 `break` 會停止 switch 中的所有處理，`continue` 則會移動到下一個項目。

``` powershell
$Messages = @(
    'Downloading update'
    'Ran into errors downloading file'
    'Error: out of disk space'
    'Sending email'
    '...'
)

switch -Wildcard ($Messages)
{
    'Error*'
    {
        Write-Error -Message $PSItem
        break
    }
    '*Error*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    '*Warning*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    default
    {
        Write-Output $PSItem
    }
}
```

```Output
Downloading update
WARNING: Ran into errors downloading file
write-error -message $PSItem : Error: out of disk space
+ CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
+ FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException
```

在此案例中，若我們遇到任何開頭為 `Error` 的行，便會出現錯誤，然後 switch 會停止。
這就是 `break` 陳述式為我們執行的操作。 若我們在字串中發現 `Error`，而非只在開頭，便會將其作為警告寫入。 我們會對 `Warning` 執行相同的操作。 一行可能會同時包含 `Error` 和 `Warning` 字詞，但我們只需要其中一個就可執行。 這便是 `continue` 為我們執行的操作。

### <a name="break-labels"></a>中斷標籤

`switch` 陳述式支援 `break/continue` 標籤，如同 `foreach` 陳述式。

``` powershell
:filelist foreach($path in $logs)
{
    :logFile switch -Wildcard -File $path
    {
        'Error*'
        {
            Write-Error -Message $PSItem
            break filelist
        }
        'Warning*'
        {
            Write-Error -Message $PSItem
            break logFile
        }
        default
        {
            Write-Output $PSItem
        }
    }
}
```

我個人不喜歡使用中斷標籤，但我還是想要提及，因為若您先前從未看過這些標籤，可能會覺得相當困惑。 當您有多個呈現巢狀的 `switch` 或 `foreach` 陳述式時，建議您中斷最內部以外的項目。 您可以將標籤置於 `switch` 上，其可以作為 `break` 的目標。

### <a name="enum"></a>例舉

PowerShell 5.0 提供了列舉，讓我們可在 switch 中使用。

``` powershell
enum Context {
    Component
    Role
    Location
}

$item = [Context]::Role

switch ( $item )
{
    Component
    {
        'is a component'
    }
    Role
    {
        'is a role'
    }
    Location
    {
        'is a location'
    }
}
```

```Output
is a role
```

若您希望保持所有項目為強型別列舉，可以將這些項目放在括弧中。

``` powershell
switch ($item )
{
    ([Context]::Component)
    {
        'is a component'
    }
    ([Context]::Role)
    {
        'is a role'
    }
    ([Context]::Location)
    {
        'is a location'
    }
}
```

此處需要括弧，以避免 switch 將 `[Context]::Location` 值視為常值字串處理。

### <a name="scriptblock"></a>ScriptBlock

我們可以視需要使用 ScriptBlock 為比對執行評估。

``` powershell
$age = 37

switch ( $age )
{
    {$PSItem -le 18}
    {
        'child'
    }
    {$PSItem -gt 18}
    {
        'adult'
    }
}
```

```Output
'adult'
```

這會增加複雜度，並且可能會讓您的 `switch` 難以閱讀。 在大多數您想要使用這類項目的案例中，建議使用 `if` 和 `elseif` 陳述式。 若我已經擁有大型的 switch，且需要兩個項目叫用相同的評估區塊，便會考慮使用此項目。

有一個我認為可以提升易讀性的方法，便是將 ScriptBlock 放在括弧中。

``` powershell
switch ( $age )
{
    ({$PSItem -le 18})
    {
        'child'
    }
    ({$PSItem -gt 18})
    {
        'adult'
    }
}
```

其仍會以相同的方式執行，並且可以在快速查看時有更好的視覺體驗。

### <a name="regex-matches"></a>RegEx $matches

我們必須回到 RegEx 接觸一些不會讓人立即察覺的項目。 使用 RegEx 會填入 `$matches` 變數。 當我談到[使用 RegEx 的許多方式][]時，我更常談的是如何使用 `$matches`。 以下是示範其搭配具名比對項目運作方式的快速範例。

``` powershell
$message = 'my ssn is 123-23-3456 and credit card: 1234-5678-1234-5678'

switch -regex ($message)
{
    '(?<SSN>\d\d\d-\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a SSN: $($matches.SSN)"
    }
    '(?<CC>\d\d\d\d-\d\d\d\d-\d\d\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a credit card number: $($matches.CC)"
    }
    '(?<Phone>\d\d\d-\d\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a phone number: $($matches.Phone)"
    }
}
```

```Output
WARNING: message may contain a SSN: 123-23-3456
WARNING: message may contain a credit card number: 1234-5678-1234-5678
```

### <a name="null"></a>$null

您可以比對不一定要是預設的 `$null` 值。

``` powershell
$value = $null

switch ( $value )
{
    $null
    {
        'Value is null'
    }
    default
    {
        'value is not null'
    }
}

```Output
Value is null
```

這也適用於空字串。

``` powershell
switch ( '' )
{
    ''
    {
        'Value is empty'
    }
    default
    {
        'value is a empty string'
    }
}

```Output
Value is empty
```

### <a name="constant-expression"></a>常數運算式

Lee Dailey 指出我們可以使用常數 `$true` 運算式來評估 `[bool]` 項目。
假設我們有幾個需要進行的布林值檢查。

``` powershell
$isVisible = $false
$isEnabled = $true
$isSecure = $true

switch ( $true )
{
    $isEnabled
    {
        'Do-Action'
    }
    $isVisible
    {
        'Show-Animation'
    }
    $isSecure
    {
        'Enable-AdminMenu'
    }
}
```

```Output
Do-Action
Enabled-AdminMenu
```

這是進行評估及針對數個布林值欄位狀態採取動作的最簡潔方式。 最棒的是，您可以讓其中一個比對項目翻轉尚未評估的值的狀態。

``` powershell
$isVisible = $false
$isEnabled = $true
$isAdmin = $false

switch ( $true )
{
    $isEnabled
    {
        'Do-Action'
        $isVisible = $true
    }
    $isVisible
    {
        'Show-Animation'
    }
    $isAdmin
    {
        'Enable-AdminMenu'
    }
}
```

```Output
Do-Action
Show-Animation
```

在此範例中將 `$isEnabled` 設為 `$true` 可以確保 `$isVisible` 也會設為 `$true`。 然後，當評估 `$isVisible` 時，便會呼叫其 ScriptBlock。 這雖然有點不直覺，但是卻是使用該機制的聰明方式。

### <a name="switch-automatic-variable"></a>$switch 自動變數

當 `switch` 處理其值時，其會建立列舉程式並呼叫其為 `$switch`。 這是由 PowerShell 所建立的自動變數，其可以讓您直接操作。

這是由 [/u/frmadsen](https://www.reddit.com/user/frmadsen) 向我指出的

<div class="reddit-embed" data-embed-media="www.redditmedia.com" data-embed-parent="false" data-embed-live="false" data-embed-uuid="8f6edbf1-abc6-4513-971e-ccd1d202889d" data-embed-created="2018-12-25T22:05:33.986Z">來自<a href="https://www.reddit.com/r/PowerShell/comments/a90rx2/what_should_i_it_student_learn_to_master/">我 (IT 學生) 該如何熟悉運用 PowerShell？</a>(英文) 討論的<a href="https://www.reddit.com/r/PowerShell/comments/a90rx2/what_should_i_it_student_learn_to_master/ecj2kji/">留言</a>。</div><script async src="https://www.redditstatic.com/comment-embed.js"></script>

這可以為您提供以下結果：

```Output
2
4
```

藉由將列舉程式向前移動，下一個項目將不會由 `switch` 進行處理，但是您可以直接存取該值。 我認為這種做法相當瘋狂。

## <a name="other-patterns"></a>其他模式

### <a name="hashtables"></a>雜湊表

我其中一個最熱門的貼文是針對[雜湊表][]的貼文。 其中一個 `hashtable` 的使用案例是作為查閱資料表。 這是除了 `switch` 陳述式所經常處理的常見模式之外，可用的替代方法。

``` powershell
$day = 3

$lookup = @{
    0 = 'Sunday'
    1 = 'Monday'
    2 = 'Tuesday'
    3 = 'Wednesday'
    4 = 'Thursday'
    5 = 'Friday'
    6 = 'Saturday'
}

$lookup[$day]
```

```Output
Wednesday
```

若我只將 `switch` 作為查閱使用，我經常會改為使用 `hashtable`。

### <a name="enum"></a>例舉

PowerShell 5.0 引進了 `Enum`，而這也是此案例中的選項之一。

``` powershell
$day = 3

enum DayOfTheWeek {
    Sunday
    Monday
    Tuesday
    Wednesday
    Thursday
    Friday
    Saturday
}

[DayOfTheWeek]$day
```

```Output
Wednesday
```

我們可以花上一整天的時間來查看解決此問題的不同方式。 但我只想確定您知道您可有所選擇。

## <a name="final-words"></a>結論

switch 陳述式表面上相當簡單，但其提供了一些不為人知的進階功能。 將這些功能連結在一起可以讓其提供強大的功能。 我希望您有了解到一些先前並不了解的知識。

<!-- link references -->
[原文]: https://powershellexplained.com/2018-01-12-Powershell-switch-statement/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[switch]: /powershell/module/microsoft.powershell.core/about/about_switch
[switch 參數]: https://www.powershellmagazine.com/2013/12/20/using-powershell-switch-vs-boolean-parameters-in-sma-runbooks/
[使用 RegEx 的許多方式]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression
[雜湊表]: everything-about-hashtable.md
