---
title: 您想知道有關於 $null 的一切
description: PowerShell $null 常常看起來很簡單，但其實有很多細微差異。 讓我們仔細看一下 $null，您就會知道當您意外遇到 Null 值時，會發生什麼事。
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: e0553a5e17450d8044f548792649369e99903850
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149471"
---
# <a name="everything-you-wanted-to-know-about-null"></a>您想知道有關於 $null 的一切

PowerShell `$null` 常常看起來很簡單，但其實有很多細微差異。 讓我們仔細看一下 `$null`，您就會知道當您意外遇到 `$null` 值時，會發生什麼事。

> [!NOTE]
> 此文章的[原始版本][]出現在 [@KevinMarquette][] 所撰寫的部落格中。 PowerShell 小組感謝 Kevin 與我們分享此內容。 請前往 [PowerShellExplained.com][] 瀏覽他的部落格。

## <a name="what-is-null"></a>什麼是 NULL？

您可以將 NULL 想成是未知或空白的值。 在指派值或物件給變數之前，變數就會是 NULL。 這可能很重要，因為有一些命令需要值，而且如果值為 NULL，就會產生錯誤。

### <a name="powershell-null"></a>PowerShell $null

`$null` 是 PowerShell 中用來代表 NULL 的自動變數。 您可以將其指派給變數、將其用於比較，以及在集合中將其作為 NULL 的預留位置使用。

PowerShell 會將 `$null` 視為具有 NULL 值的物件。 如果您之前使用另一種語言，這可能會和您預期的不同。

## <a name="examples-of-null"></a>$null 的範例

每當您嘗試使用尚未初始化的變數時，值就會是 `$null`。 這是 `$null` 值潛入到您的程式碼中時，其中一種最常見的潛入方式。

```powershell
PS> $null -eq $undefinedVariable
True
```

如果您輸入錯誤的變數名稱，PowerShell 會將其視為不同的變數，而值會是 `$null`。

另一種尋找 `$null` 值的方式是，當它們來自不提供任何結果的其他命令時。

```powershell
PS> function Get-Nothing {}
PS> $value = Get-Nothing
PS> $null -eq $value
True
```

## <a name="impact-of-null"></a>$null 的影響

`$null` 值會依據其顯示的位置，對您的程式碼產生不同的影響。

### <a name="in-strings"></a>在字串中

如果您在字串中使用 `$null`，其就是空白值 (或空字串)。

```powershell
PS> $value = $null
PS> Write-Output "The value is $value"
The value is
```

這是我在記錄檔訊息中使用變數時，偏好用括弧括住變數的其中一個原因。 當值位於字串的結尾時，識別變數值的邊緣甚至會變得更加重要。

```powershell
PS> $value = $null
PS> Write-Output "The value is [$value]"
The value is []
```

這可讓您易於找出空字串與 `$null` 值。

### <a name="in-numeric-equation"></a>在數值方程式中

在數值方程式中使用 `$null` 值時，如果結果不會提供錯誤，那結果就會是無效的。 有時候 `$null` 會評估為 `0`，而其他時候則會讓整個結果為 `$null`。
以下是根據值的順序，給出 0 或 `$null` 的乘法範例。

```powershell
PS> $null * 5
PS> $null -eq ( $null * 5 )
True

PS> 5 * $null
0
PS> $null -eq ( 5 * $null )
False
```

### <a name="in-place-of-a-collection"></a>代替集合

集合可讓您使用索引來存取值。 如果您嘗試在實際為 `null` 的集合中編製索引，會收到此錯誤：`Cannot index into a null array`。

```powershell
PS> $value = $null
PS> $value[10]
Cannot index into a null array.
At line:1 char:1
+ $value[10]
+ ~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [], RuntimeException
    + FullyQualifiedErrorId : NullArray
```

如果您有集合，但嘗試存取不在集合中的元素時，會得到 `$null` 結果。

```powershell
$array = @( 'one','two','three' )
$null -eq $array[100]
True
```

### <a name="in-place-of-an-object"></a>代替物件

如果您嘗試存取物件的屬性或子屬性，但物件並沒有您指定的屬性，會取得 `$null` 值，就像針對未定義的變數所取得的結果一樣。 在此情況下，變數為 `$null` 或實際物件並不重要。

```powershell
PS> $null -eq $undefined.some.fake.property
True

PS> $date = Get-Date
PS> $null -eq $date.some.fake.property
True
```

### <a name="method-on-a-null-valued-expression"></a>Null 值運算式上的方法

呼叫 `$null` 物件上的方法會擲回 `RuntimeException`。

```powershell
PS> $value = $null
PS> $value.toString()
You cannot call a method on a null-valued expression.
At line:1 char:1
+ $value.tostring()
+ ~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [], RuntimeException
    + FullyQualifiedErrorId : InvokeMethodOnNull
```

每當我看到片語 `You cannot call a method on a null-valued expression` 時，我首先要尋找的項目就是在變數上呼叫方法，而不需要先檢查值是否為 `$null` 的地方。

## <a name="checking-for-null"></a>檢查 $null

您可能已經注意到，在我的範例中檢查 `$null` 時，我一律會將 `$null` 放在左側。 這是刻意的，而且已被視為 PowerShell 最佳做法。 在某些情況下，將其放在右側並不會提供您預期的結果。

請看看下一個範例並嘗試預測結果：

```powershell
if ( $value -eq $null )
{
    'The array is $null'
}
if ( $value -ne $null )
{
    'The array is not $null'
}
```

如果我沒有定義 `$value`，第一個就會評估為 `$true`，而且我們的訊息為 `The array is $null`。 這裡的陷阱是可以建立 `$value`，來允許它們兩個都可以是 `$false`

```powershell
$value = @( $null )
```

在此情況下，`$value` 是包含 `$null` 的陣列。 `-eq` 會檢查陣列中的每個值，並傳回符合的 `$null`。 這會評估為 `$false`。 `-ne` 會傳回不符合 `$null` 的所有項目，而且在此案例中並沒有任何結果 (這也會評估為 `$false`)。 兩個情況都不是 `$true`，即使它們其中一個看起來應該要是。

我們不僅可以建立一個會讓這兩種情況都評估為 `$false` 的值，也可以建立一個會讓兩個情況都評估為 `$true` 的值。 Mathias Jessen (@IISResetMe) 有一篇深入說明該案例的[絕佳貼文][]。

### <a name="psscriptanalyzer-and-vscode"></a>PSScriptAnalyzer 與 VSCode

[PSScriptAnalyzer][] 模組有一個會檢查是否有此問題的規則，名為 `PSPossibleIncorrectComparisonWithNull`。

```powershell
PS> Invoke-ScriptAnalyzer ./myscript.ps1

RuleName                              Message
--------                              -------
PSPossibleIncorrectComparisonWithNull $null should be on the left side of equality comparisons.
```

因為 VS Code 也會使用 PSScriptAnalyser 規則，所以其也會在您的指令碼中將此情況以反白方式顯示，或將其識別為問題。

### <a name="simple-if-check"></a>簡單的 if 檢查

人們檢查非 $null 值的一種常見方式是使用簡單的 `if()` 陳述式，而不進行比較。

```powershell
if ( $value )
{
    Do-Something
}
```

如果值是 `$null`，這會評估為 `$false`。 這很容易閱讀，但請小心，因為其會尋找您預期其尋找的項目。 我將該程式碼讀為：

> 如果 `$value` 有值。

但這並不完整。 那一行的真正意思應該是：

> 如果 `$value` 不是 `$null`、`0`、`$false` 或 `empty string`

以下是該陳述式的更完整範例。

```powershell
if ( $null -ne $value -and
        $value -ne 0 -and
        $value -ne '' -and
        $value -ne $false )
{
    Do-Something
}
```

只要您記得其他的值會視為 `$false`，而不是只會視為變數具有值，那就可以使用基本的 `if` 檢查。

我在幾天前重構一些程式碼時遇到了這個問題。 其有一個像這樣的基本屬性檢查。

```powershell
if ( $object.property )
{
    $object.property = $value
}
```

我想要指派一個值給物件屬性，如果它存在的話。 在大部分情況下，原始物件會有一個在 `if` 陳述式中評估為 `$true` 的值。 但我遇到一個偶爾未設定值的問題。 我已對程式碼進行偵錯並發現物件具有屬性，但其為空的字串值。 這會讓其無法使用先前的邏輯來更新。 所以我新增了適當的 `$null` 檢查，然後一切就能正常運作了。

```powershell
if ( $null -ne $object.property )
{
    $object.property = $value
}
```

這是一個和這些錯誤一樣難以找到的小錯誤 (Bug)，因此導致我積極地檢查 `$null` 值。

## <a name="nullcount"></a>$null.Count

如果您嘗試存取 `$null` 值上的屬性，該屬性也會是 `$null`。 `count` 屬性是此規則的例外。

```powershell
PS> $value = $null
PS> $value.count
0
```

當您有 `$null` 值時，`count` 就會是 `0`。 此特殊屬性是由 PowerShell 所新增的。

### <a name="pscustomobject-count"></a>[PSCustomObject] 計數

PowerShell 中幾乎所有物件都有該 count 屬性。 Windows PowerShell 5.1 中一個重要的例外是 `[PSCustomObject]` (PowerShell 6.0 中已修正此問題)。 其沒有 count 屬性，因此如果您嘗試加以使用，就會得到 `$null` 值。 我在這裡說明這件事是要讓您不要嘗試使用 `.Count`，而不執行 `$null` 檢查。

在 Windows PowerShell 5.1 與 PowerShell 6.0 上執行此範例會提供不同的結果。

```powershell
$value = [PSCustomObject]@{Name='MyObject'}
if ( $value.count -eq 1 )
{
    "We have a value"
}
```

## <a name="empty-null"></a>空白 Null

有一種特殊類型的 `$null`，其作用與其他類型不同。 我要將其命名為空白 `$null`，但它其實是 [System.Management.Automation.Internal.AutomationNull][]。 這個空的 `$null` 是函式或指令碼區塊未傳回任何內容的結果 (不正確的結果)。

```powershell
PS> function Get-Nothing {}
PS> $nothing = Get-Nothing
PS> $null -eq $nothing
True
```

如果您將其與 `$null` 比較，就會得到 `$null` 值。 在需要值的評估中使用時，值一律會是 `$null`。 但如果您將其放在陣列中，其就會被視為空陣列。

```powershell
PS> $containempty = @( @() )
PS> $containnothing = @($nothing)
PS> $containnull = @($null)

PS> $containempty.count
0
PS> $containnothing.count
0
PS> $containnull.count
1
```

您可以有一個包含一個 `$null` 值，而其 `count` 為 `1` 的陣列。 但是，如果您將空的結果放在陣列中，其就不會被視為項目。 計數為 `0`。

如果您將空 `$null` 視為集合，那其就會是空的。

### <a name="pipeline"></a>管線

您會看到差異的主要位置是在使用管線時。 您可以使用管線傳送 `$null` 值，但不能傳送空 `$null` 值。

```powershell
PS> $null | ForEach-Object{ Write-Output 'NULL Value' }
'NULL Value'
PS> $nothing | ForEach-Object{ Write-Output 'No Value' }
```

視程式碼而定，您應該在邏輯中說明 `$null`。

請先檢查 `$null`

- 在管線上篩選出 Null (`... | Where {$null -ne $_} | ...`)
- 在管線函式中加以處理

## <a name="foreach"></a>foreach

`foreach` 的功能之中，我最愛的其中之一就是其不會列舉 `$null` 集合。

```powershell
foreach ( $node in $null )
{
    #skipped
}
```

這讓我不需要先針對集合進行 `$null` 檢查，再列舉集合。 如果您有 `$null` 值的集合，`$node` 仍然可以是 `$null`。

foreach 在 PowerShell 3.0 中已開始以這種方式運作。 如果您使用的是較舊的版本，就不是這種情況。 這是為了與 2.0 版相容而向後移植程式碼時，必須注意的其中一個重要變更。

## <a name="value-types"></a>實值型別

就技術而言，只有參考型別可以是 `$null`。 但是 PowerShell 很大方，因此允許任何類型的變數。 如果您決定為實值型別進行強型別處理，那其就不能是 `$null`。
PowerShell 會將 `$null` 轉換成許多型別適用的預設值。

```powershell
PS> [int]$number = $null
PS> $number
0

PS> [bool]$boolean = $null
PS> $boolean
False

PS> [string]$string = $null
PS> $string -eq ''
True
```

有些型別並沒有從 `$null` 轉換而來的有效轉換。 這些型別會產生 `Cannot convert null to type` 錯誤。

```powershell
PS> [datetime]$date = $null
Cannot convert null to type "System.DateTime".
At line:1 char:1
+ [datetime]$date = $null
+ ~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : MetadataError: (:) [], ArgumentTransformationMetadataException
    + FullyQualifiedErrorId : RuntimeException
```

### <a name="function-parameters"></a>函數參數

在函式參數中使用強型別值是很常見的。 我們通常會學習定義參數的型別，即使我們習慣不在指令碼中定義其他變數的型別也一樣。 您的函式中可能已經有一些強型別變數，但您甚至沒有意識到。

```powershell
function Do-Something
{
    param(
        [String] $Value
    )
}
```

一旦您將參數的型別設定為 `string`，值就永遠不會是 `$null`。 我們經常會檢查某個值是否是 `$null`，以查看使用者是否已提供值。

```powershell
if ( $null -ne $Value ){...}
```

如果沒有提供任何值，`$Value` 就會是一個空字串 `''`。 請改為使用自動變數 `$PSBoundParameters.Value`。

```powershell
if ( $null -ne $PSBoundParameters.Value ){...}
```

`$PSBoundParameters` 只會包含呼叫函式時所指定的參數。
您也可以使用 `ContainsKey` 方法來檢查屬性。

```powershell
if ( $PSBoundParameters.ContainsKey('Value') ){...}
```

### <a name="isnotnullorempty"></a>IsNotNullOrEmpty

如果值是字串，您可以使用靜態字串函式來同時檢查值是否為 `$null` 或空字串。

```powershell
if ( -not [string]::IsNullOrEmpty( $value ) ){...}
```

當我知道實值型別應該是字串時，才發現我經常會用到。

## <a name="when-i-null-check"></a>當我進行 $null 檢查時

我是一個防禦性高的指令碼作者。 每當我呼叫函式並將其指派給變數時，都會檢查其是否是 `$null`。

```powershell
$userList = Get-ADUser kevmar
if ($null -ne $userList){...}
```

相較於 `try/catch`，我更喜歡使用 `if` 或 `foreach`。 別誤會我的意思，我還是很常使用 `try/catch` 的。 但是，如果我可以測試錯誤條件或空的結果集，我可以讓例外狀況處理作業成為處理真正例外狀況的作業。

我也習慣先檢查是否有 `$null`，然後才在物件為值編製索引或呼叫方法。 這兩個動作會因為 `$null` 物件而失敗，所以我發現先驗證它們是很重要的。 我先前已經在這篇文章中討論過那些案例。

### <a name="no-results-scenario"></a>無結果案例

請務必了解一點，那就是不同的函式與命令會以不同的方式處理無結果案例。 許多 PowerShell 命令都會在錯誤資料流中傳回空的 `$null` 與錯誤。 但其他則會擲回例外狀況，或提供狀態物件。 您仍然需要知道自己使用的命令會如何處理無結果與錯誤狀況。

## <a name="initializing-to-null"></a>初始化為 $null

我養成了一個習慣，那就是先將所有的變數初始化，然後再使用。 您必須以其他語言執行此動作。 在我的函式的最前面，或當我輸入 foreach 迴圈時，我會定義我使用的所有值。

以下是我想要讓您仔細看看的狀況。 這是我之前必須追查的一個錯誤 (Bug) 的範例。

```powershell
function Do-Something
{
    foreach ( $node in 1..6 )
    {
        try
        {
            $result = Get-Something -ID $node
        }
        catch
        {
            Write-Verbose "[$result] not valid"
        }

        if ( $null -ne $result )
        {
            Update-Something $result
        }
    }
}
```

這裡預期的是 `Get-Something` 會傳回結果或空 `$null`。 如果發生錯誤，我們會將其記錄下來。 然後，我們會先檢查以確定我們已經取得有效結果，然後再加以處理。

此程式碼中隱藏的錯誤 (Bug) 是 `Get-Something` 擲回例外狀況，而且未指派值給 `$result`。 其會在指派之前失敗，因此甚至不會將 `$null` 指派給 `$result` 變數。 `$result` 仍然包含先前來自其他反覆項目的有效 `$result`。
在此範例中，會 `Update-Something` 以在同一物件上執行多次。

我先直接在 foreach 迴圈內部把 `$result` 設定為 `$null`，然後再加以使用來緩解這個問題。

```powershell
foreach ( $node in 1..6 )
{
    $result = $null
    try
    {
        ...
```

### <a name="scope-issues"></a>範圍問題

這也有助於緩解範圍設定問題。 在該範例中，我們會在迴圈中不斷重複指派值給 `$result`。 但是，由於 PowerShell 允許來自函式外部的變數值進入目前函式的範圍，因此在函式內將它們初始化可以緩解可能透過該方式引入的錯誤 (Bug)。

如果函式中未初始化的變數設定為父代範圍中個某個值，該變數就不會是 `$null`。
父代範圍可能是另一個函式，其會呼叫您的函式並使用相同的變數名稱。

如果我採用相同的 `Do-something` 範例，並移除迴圈，最後會得到看起來像此範例的結果：

```powershell
function Invoke-Something
{
    $result = 'ParentScope'
    Do-Something
}

function Do-Something
{
    try
    {
        $result = Get-Something -ID $node
    }
    catch
    {
        Write-Verbose "[$result] not valid"
    }

    if ( $null -ne $result )
    {
        Update-Something $result
    }
}
```

如果對 `Get-Something` 的呼叫擲回例外狀況，我執行的 `$null` 檢查就會從 `Invoke-Something` 尋找 `$result`。 將函式內部的值初始化可緩解這個問題。

為變數命名並不容易，而且通常都會在多個函式中使用相同的變數名稱。 我知道我總是使用 `$node`、`$result` 與 `$data`。 因此，這會使來自其他範圍的變數非常容易出現在不應該出現的位置。

## <a name="redirect-output-to-null"></a>將輸出重新導向至 $null

我已經在這整篇文章中討論過很多次 `$null` 值，但如果不說一下將輸出重新導向至 `$null`，那這個主題就不算完整。 有時候，有些命令會輸出您想要隱藏的資訊或物件。 將輸出重新導向至 `$null` 就可以達到您想要的隱藏效果。

### <a name="out-null"></a>Out-Null

Out-Null 命令是內建的方法，可將管線資料重新導向到 `$null`。

```powershell
New-Item -Type Directory -Path $path | Out-Null
```

### <a name="assign-to-null"></a>指派給 $null

您可以將命令的結果指派給 `$null`，以獲得與使用 `Out-Null` 相同的效果。

```powershell
$null = New-Item -Type Directory -Path $path
```

因為 `$null` 是個常數值，所以您一律不能加以覆寫。 我不喜歡其在我的程式碼中的樣子，但其執行速度通常比 `Out-Null` 快。

### <a name="redirect-to-null"></a>重新導向至 $null

您也可以使用重新導向運算子將輸出傳送至 `$null`。

```powershell
New-Item -Type Directory -Path $path > $null
```

如果您處理的是會在不同的資料流上輸出的命令列可執行檔。 您可以將所有輸出資料流重新導向至 `$null`，就像這樣：

```powershell
git status *> $null
```

## <a name="summary"></a>摘要

我已經討論過很多與此項目有關的基礎，而且我知道這篇文章的內容比我大多數的深入探討文章更分散。 這是因為 `$null` 值可能會在 PowerShell 中的許多不同位置出現，而且所有細微差異都會是在找到它的位置特定的。 我希望您能夠進一步了解 `$null`，並知道您可能會遇到更晦澀的狀況，進而擺脫掉這個問題。

<!-- link references -->
[原始版本]: https://powershellexplained.com/2018-12-23-Powershell-null-everything-you-wanted-to-know/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[絕佳貼文]: https://blog.iisreset.me/schrodingers-argumentlist
[PSScriptAnalyzer]: https://www.powershellgallery.com/packages/PSScriptAnalyzer
[System.Management.Automation.Internal.AutomationNull]: /dotnet/api/system.management.automation.internal.automationnull
