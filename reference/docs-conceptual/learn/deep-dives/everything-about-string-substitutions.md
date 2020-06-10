---
title: 如何在字串中替代變數
description: 在字串中使用變數來建立格式化文字的方法很多。
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 1e65e90ffa09b34f62bc49ad64b062d429483c33
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149461"
---
# <a name="everything-you-wanted-to-know-about-variable-substitution-in-strings"></a>如何在字串中替代變數

在字串中使用變數的方法很多。 這裡所謂的「替代變數」，其實是指將字串格式化以包含變數值的任何情況。 這是指令碼撰寫新手要注意的部分。

> [!NOTE]
> 此[原文][]出自 [@KevinMarquette][] 所撰寫的部落格。 PowerShell 小組感謝 Kevin 分享此內容。 請前往 [PowerShellExplained.com][] 瀏覽他的部落格。

## <a name="concatenation"></a>串連

第一種方法可以稱為「串連」。 基本上，這種方法就是把好幾個字串聯結在一起。 使用串連來建置格式化字串是一個已經行之有年的方法。

```powershell
$name = 'Kevin Marquette'
$message = 'Hello, ' + $name
```

若只有要新增幾個值，串連不會有什麼大問題。 但通常很快就會變得複雜。

```powershell
$first = 'Kevin'
$last = 'Marquette'
```

```powershell
$message = 'Hello, ' + $first + ' ' + $last + '.'
```

這個簡單的範例已經沒那麼一目了然。

## <a name="variable-substitution"></a>變數替代

PowerShell 提供另一種更輕鬆的選項。 您可以直接在字串中指定變數。

```powershell
$message = "Hello, $first $last."
```

也可以使用不同引號類型括住字串，達到不同作用。 使用雙引號括住的字串可進行替代，但用單引號的字串則否。 您可以自行選擇要使用哪一種。

## <a name="command-substitution"></a>常見替代

當您開始嘗試將屬性的值放入字串時，就會遇到一點麻煩了。 很多新手都是卡在這一關。 首先我會示範一般新手認為可以運作的內容 (而且乍看之下，這樣的值也應該沒有問題)。

```powershell
$directory = Get-Item 'c:\windows'
$message = "Time: $directory.CreationTime"
```

您以為可以得到 `$directory` 的 `CreationTime`，但卻得到 `Time: c:\windows.CreationTime` 值。 主要是因為這種類型的替代只會使用基底變數。 其會將句點視為字串的一部分，所以不會更深入地解析值。

所以當您將這個物件放入字串時，會提供字串作為預設值。
反之，有些物件會提供類型名稱，例如 `System.Collections.Hashtable`。 這都是您要小心的地方。

PowerShell 可讓您使用特殊語法在字串內執行命令。 這可讓我們取得這些物件的屬性，並執行任何其他命令來取得值。

```powershell
$message = "Time: $($directory.CreationTime)"
```

有些情況很適合這麼做，但即使只有幾個變數，也可能像串連一樣越變越複雜。

### <a name="command-execution"></a>命令執行

您可以在字串內執行命令。 不過，即使有這個選項，我也不想用。 因為內容很快就會變得雜亂無章，很難偵錯。 我會執行命令並儲存至變數，或使用格式字串。

```powershell
$message = "Date: $(Get-Date)"
```

## <a name="format-string"></a>格式字串

.NET 的格式化字串方法，我認為滿好用的。 首先，我會示範靜態方法，接著再示範如何使用 PowerShell 快捷方式來執行相同的動作。

```powershell
# .NET string format string
[string]::Format('Hello, {0} {1}.',$first,$last)

# PowerShell format string
'Hello, {0} {1}.' -f $first, $last
```

在這個範例中，系統會剖析字串以尋找 `{0}` 和 `{1}` 權杖，然後使用該數字從提供的值中挑選。 若您想要在字串中重複某位置的一個值，您可以重複使用該值數字。

字串越複雜，使用這個方法就有越顯著的優勢。

### <a name="format-values-as-arrays"></a>將值格式化為陣列

若您的格式行太長，您可以先將值放入陣列中。

```powershell
$values = @(
    "Kevin"
    "Marquette"
)
'Hello, {0} {1}.' -f $values
```

這個範例不是展開，因為我要將整個陣列傳入，但概念很類似。

## <a name="advanced-formatting"></a>進階格式

我必須強調這些功能都是來自 .NET，因為其中許多格式設定選項都已有相當完整的[記載說明][]， 也有內建的方法可以格式化各種資料類型。

```powershell
"{0:yyyyMMdd}" -f (Get-Date)
"Population {0:N0}" -f  8175133
```

我並不打算詳細說明這些方式，只是想讓您知道，這是一款非常強大的格式化引擎。

## <a name="joining-strings"></a>聯結字串

有時候您會想要將值清單串連在一起。 您可以使用 `-join` 運算子執行這個動作。 該運算子甚至可讓您指定要在字串之間聯結的字元。

```powershell
$servers = @(
    'server1'
    'server2'
    'server3'
)

$servers  -join ','
```

若要 `-join` 一些字串而不含分隔符號，您必須指定空字串 `''`。
但如果您只要做到這樣就夠了，還有更快的方法。

```powershell
[string]::Concat('server1','server2','server3')
[string]::Concat($servers)
```

順帶一提，您也可以將字串 `-split`。

## <a name="join-path"></a>Join-Path

大家很容易忽略這個建置檔案路徑的絕佳 Cmdlet。

```powershell
$folder = 'Temp'
Join-Path -Path 'c:\windows' -ChildPath $folder
```

這個 Cmdlet 的最大優點是可以正確處理多個值當中的反斜線。 若您要從使用者或設定檔取得值，這就特別重要。

這也適用於 `Split-Path` 和 `Test-Path`。 我在[讀取和儲存至檔案][]文章中也會說明這些內容。

## <a name="strings-are-arrays"></a>字串為陣列

在繼續之前，我必須先說明一下何謂新增字串。 其實字串就是一個字元陣列。 當您新增多個字串時，每次都會建立新的陣列。

請看一下這個範例：

```powershell
$message = "Numbers: "
foreach($number in 1..10000)
{
    $message += " $number"
}
```

這看似很基本，但您不知道的是，每將一個字串新增到 `$message` 時，就會建立一整個新的字串。 系統會配置記憶體、複製資料，並將舊的字串捨棄。
若只要重複幾次倒沒什麼問題，但這樣的迴圈仍可能爆出問題。

### <a name="stringbuilder"></a>StringBuilder

當您要從許多較小的字串建立大型字串時，StringBuilder 也是非常熱門的選擇。 因為 StringBuilder 只會收集您新增至其中的所有字串，並在您最後要擷取值時，才會將字串全部串連起來。

```powershell
$stringBuilder = New-Object -TypeName "System.Text.StringBuilder"

[void]$stringBuilder.Append("Numbers: ")
foreach($number in 1..10000)
{
    [void]$stringBuilder.Append(" $number")
}
$message = $stringBuilder.ToString()
```

同樣地，這也是我特別推薦的 .NET 功能。 雖然我並不常用，但知道有這個功能也挺不錯的。

## <a name="delineation-with-braces"></a>以大括弧區隔

這種做法主要用於字串內的尾碼串連。 因為變數的字邊界有時候不太明確。

```powershell
$test = "Bet"
$tester = "Better"
Write-Host "$test $tester ${test}ter"
```

感謝 [/u/real_parbold][] 提供範例。

以下是這種方法的替代方式：

```powershell
Write-Host "$test $tester $($test)ter"
Write-Host "{0} {1} {0}ter" -f $test, $tester
```

我個人會使用格式字串來進行這項工作，但多了解一種做法對您也很有幫助。

## <a name="find-and-replace-tokens"></a>尋找和取代權杖

雖然這裡提的大部分功能都可讓您盡量不用翻遍解決方案，但有時候您的範本檔案可能很大，而您想要取代其中的字串。

假設您已從含大量文字的檔案中提取範本。

```powershell
$letter = Get-Content -Path TemplateLetter.txt -RAW
$letter = $letter -replace '#FULL_NAME#', 'Kevin Marquette'
```

您可能必須取代一大堆權杖。 訣竅是使用非常明顯且易於尋找和取代的權杖。 我通常會在兩端使用特殊字元以利辨別。

不過，我最近發現了一種新的方法。 我就順便在這裡說明一下，因為這是常用的模式。

### <a name="replace-multiple-tokens"></a>取代多個權杖

當手邊有需要取代的權杖清單時，我會採用一般的方法。 我會將這些權杖放在雜湊表中，然後逐一查看以進行取代。

```powershell
$tokenList = @{
    Full_Name = 'Kevin Marquette'
    Location = 'Orange County'
    State = 'CA'
}

$letter = Get-Content -Path TemplateLetter.txt -RAW
foreach( $token in $tokenList.GetEnumerator() )
{
    $pattern = '#{0}#' -f $token.key
    $letter = $letter -replace $pattern, $token.Value
}
```

您可以視需要從 JSON 或 CSV 載入這些權杖。

### <a name="executioncontext-expandstring"></a>ExecutionCoNtext ExpandString

有個妙計是使用單引號來定義替代字串，稍後再展開變數。 請看一下這個範例：

```powershell
$message = 'Hello, $Name!'
$name = 'Kevin Marquette'
$string = $ExecutionContext.InvokeCommand.ExpandString($message)
```

當您對目前的執行內容呼叫 `.InvokeCommand.ExpandString` 時，系統會使用目前範圍中的變數來進行替代。 值得注意的是，您甚至可以在變數存在之前就先定義 `$message`。

若再延伸一下，我們可以使用不同的值不斷執行這種替代。

```powershell
$message = 'Hello, $Name!'
$nameList = 'Mark Kraus','Kevin Marquette','Lee Dailey'
foreach($name in $nameList){
    $ExecutionContext.InvokeCommand.ExpandString($message)
}
```

若要進一步延伸這個概念，您可以從文字檔匯入大型電子郵件範本來執行此動作。 感謝 [Mark Kraus][] 提供這個[建議][]。

## <a name="whatever-works-the-best-for-you"></a>適合的方法最好

我個人是格式字串方法的粉絲。 遇到更複雜的字串或多個變數時，我一定會採用這個方法。 不過若要處理的內容很簡短，我就會採用本文提到的任何一種方法。

## <a name="anything-else"></a>還想知道什麼嗎？

針對這個主題，我快速把重點都講完了。 希望您有學到一點新東西。

<!-- link references -->
[原文]: https://powershellexplained.com/2017-01-13-powershell-variable-substitution-in-strings/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Mark Kraus]: https://get-powershellblog.blogspot.com/
[建議]: https://www.reddit.com/r/PowerShell/comments/5npf8h/kevmar_everything_you_wanted_to_know_about/dcdfia5/
[/u/real_parbold]: https://www.reddit.com/r/PowerShell/comments/5npf8h/kevmar_everything_you_wanted_to_know_about/dcdfm6p/
[讀取和儲存至檔案]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files/
[記載說明]: /dotnet/api/system.string.format#overloads
