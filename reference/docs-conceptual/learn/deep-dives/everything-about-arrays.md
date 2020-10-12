---
title: 您想知道有關於陣列的一切
description: 陣列是大部分程式設計語言的基礎語言功能。
ms.date: 10/08/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: b26aa11aadbeea1984b2754cfcad061c7fa3ff1e
ms.sourcegitcommit: 3445a343e0683124652f64abef6fe911f9eb989f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2020
ms.locfileid: "91852556"
---
# <a name="everything-you-wanted-to-know-about-arrays"></a>您想知道有關於陣列的一切

[陣列][]是大部分程式設計語言的基礎語言功能。 陣列是不容易規避的值或物件的集合。 讓我們詳細檢視陣列及其所提供的一切功能。

> [!NOTE]
> 本文的[原始版本][]出自 [@KevinMarquette][] 所撰寫的部落格。 PowerShell 小組感謝 Kevin 分享的內容。 請前往 [PowerShellExplained.com][] 瀏覽他的部落格。

## <a name="what-is-an-array"></a>什麼是陣列？

我要先從基本的技術描述開始，藉此說明陣列是什麼，以及大部分的程式設計語言如何使用這些陣列，再導入 PowerShell 使用陣列的其他方式的主題。

陣列是一種資料結構，可做為多個項目的集合。 您可以逐一查看陣列，或使用索引來存取個別的項目。 系統會以連續的記憶體區塊建立陣列，其中每個值都會儲存於彼此相鄰的位置。

隨著文章內容的敘述，我將處及相關的詳細資訊。

## <a name="basic-usage"></a>基本使用方式

因為陣列是 PowerShell 的基本功能，所以在 PowerShell 中使用陣列有一種簡單的語法。

### <a name="create-an-array"></a>建立陣列

您可以使用 `@()` 來建立空的陣列

```powershell
PS> $data = @()
PS> $data.count
0
```

我們可以建立陣列，並將值放在 `@()` 括弧中，藉此將其植入。

```powershell
PS> $data = @('Zero','One','Two','Three')
PS> $data.count
4

PS> $data
Zero
One
Two
Three
```

此陣列有 4 個項目。 當我們呼叫 `$data` 變數時，我們會看到項目的清單。 如果是字串陣列，則會為每個字串各取得一行。

我們可以在多行宣告陣列。 在此情況下，逗號是選擇性使用的，而且通常會省略。

```powershell
$data = @(
    'Zero'
    'One'
    'Two'
    'Three'
)
```

我習慣將陣列宣告為多行，就像這樣。 當您有多個項目時，這樣不僅方便閱讀，同時也可讓您在使用原始程式碼控制時更容易與舊版進行比較。

#### <a name="other-syntax"></a>其他語法

眾所周知，`@()` 是用來建立陣列的語法，不過在大多數情況下，以逗號分隔的清單就能勝任。

```powershell
$data = 'Zero','One','Two','Three'
```

#### <a name="write-output-to-create-arrays"></a>Write-Output 建立陣列

值得一提的小技巧，就是您可以使用 `Write-Output` 在主控台快速地建立字串。

```powershell
$data = Write-Output Zero One Two Three
```

這種方式很便利，因為當參數接受字串時，您不需要在字串前後加上引號。 我不會在指令碼中執行這項操作，不過這種作法在主控台中是很好下手的方式。

### <a name="accessing-items"></a>存取項目

現在您已經有一個具有項目的陣列，您可能會想要存取和更新這些項目。

#### <a name="offset"></a>Offset

若要存取個別的項目，我們將括弧 `[]` 用於從 0 開始的位移值。 這就是我們取得陣列中第一個項目的方式：

```powershell
PS> $data = 'Zero','One','Two','Three'
PS> $data[0]
Zero
```

我們在這裡使用零的原因，在於第一個項目位於清單的開頭，所以我們使用 0 個項目的位移來取得該項目。 若要取得第二個項目，我們必須藉由位移 1 來略過第一個項目。

```powershell
PS> $data[1]
One
```

這表示最後一個項目是在位移 3。

```powershell
PS> $data[3]
Three
```

#### <a name="index"></a>索引

現在您可以瞭解我在此範例中挑選那些值的原因所在。 我將此視為位移，因為這就是它真正的本質所在，但此位移較常稱為索引。 從 `0` 開始的索引。 在本文的其餘部分，我將會將該位移稱為索引。

#### <a name="special-index-tricks"></a>特殊索引訣竅

在大部分的程式設計語言中，您只能指定單一數字做為索引，並傳回單一項目。
PowerShell 更加靈活。 您可以同時使用多個索引。 藉由提供索引清單，我們可以選取多個項目。

```powershell
PS> $data[0,2,3]
Zero
Two
Three
```

系統會根據所提供的索引順序傳回項目。 如果複製索引，則您會同時取得該項目。

```powershell
PS> $data[3,0,3]
Three
Zero
Three
```

我們可以藉由內建的 `..` 運算子來指定數字序列。

```powershell
PS> $data[1..3]
One
Two
Three
```

反向也適用。

```powershell
PS> $data[3..1]
Three
Two
One
```

您可以使用負索引值從尾端進行位移。 因此，如果需要清單中的最後一個項目，您可以使用 `-1`。

```powershell
PS> $data[-1]
Three
```

在這裡使用 `..` 運算子時，請務必小心謹慎。 序列 `0..-1` 和 `-1..0` 會針對 `0,-1` 和 `-1,0` 的值進行評估。 如果您忘記此詳細資料，很容易就能看到 `$data[0..-1]`，並聯想到它會列舉所有的項目。 `$data[0..-1]` 藉由提供陣列中的第一個和最後一個項目 (並且不含任何其他值)，為您提供與 `$data[0,-1]` 相同的值。

#### <a name="out-of-bounds"></a>超出範圍

在大部分的程式設計語言中，如果嘗試存取超出陣列結尾的項目索引，則您會收到某種類型的錯誤或例外狀況。 PowerShell 不會無訊息地傳回任何內容。

```powershell
PS> $null -eq $data[9000]
True
```

#### <a name="cannot-index-into-a-null-array"></a>無法為 null 陣列編製索引

如果您的變數是 `$null`，而您嘗試將其編製為數組之類的索引，則會收到顯示訊息 `Cannot index into a null array` 的 `System.Management.Automation.RuntimeException` 例外狀況。

```powershell
PS> $empty = $null
SP> $empty[0]
Error: Cannot index into a null array.
```

因此，在您嘗試存取其中的元素之前，請確認您的陣列並非 `$null`。

#### <a name="count"></a>Count

陣列和其他集合具有 count 屬性，可告訴您陣列中有多少個項目。

```powershell
PS> $data.count
4
```

PowerShell 3.0 已將 count 屬性新增至大部分的物件。 您可以擁有單一物件，而且物件應該會提供您 `1` 的計數。

```powershell
PS> $date = Get-Date
PS> $date.count
1
```

即使 `$null` 具有 count 屬性，它還是會傳回 `0`。

```powershell
PS> $null.count
0
```

這裡有一些陷阱，我會在本文稍後探討 `$null` 或空白陣列的檢查時，再回顧一下。

#### <a name="off-by-one-errors"></a>差一錯誤

會建立常見的程式設計錯誤的原因，在於陣列是從索引 0 開始。 有兩種方式可以導入差一錯誤。

第一種是心裡想著您想要第二個項目，並使用 `2` 的索引，然後實際上去取得第三個項目。 或者，假設您有四個項目，而您想要上一個項目，所以您可以使用此計數來取用最後一個項目。

```powershell
$data[ $data.count ]
```

PowerShell 很樂意讓您這麼做，並為您提供索引 4的確切項目： `$null`。 您應該使用 `$data.count - 1` 或我們所學習的 `-1`。

```powershell
PS> $data[ $data.count - 1 ]
Three
```

這是您可以使用 `-1` 索引來取得最後一項元素的最後機會。

```powershell
PS> $data[ -1 ]
Three
```

Lee Dailey 也會向我指出，我們可以使用 `$data.GetUpperBound(0)` 來取得最大的索引編號。

```powershell
PS> $data.GetUpperBound(0)
3
PS> $data[ $data.GetUpperBound(0) ]
Three
```

第二個最常見的方式是在反覆查看清單，而不是在合適的時間停止。 當我們談到如何使用 `for` 迴圈時，我會重新回顧此資訊。

### <a name="updating-items"></a>正在更新項目

我們可以使用相同的索引來更新陣列中的現有項目。 這可讓我們直接存取以更新個別項目。

```powershell
$data[2] = 'dos'
$data[3] = 'tres'
```

如果我們嘗試更新最後一項元素之外的項目，就會出現 `Index was outside the bounds of the array.` 錯誤。

```powershell
PS> $data[4] = 'four'
Index was outside the bounds of the array.
At line:1 char:1
+ $data[4] = 'four'
+ ~~~~~~~~~~~~~
+ CategoryInfo          : OperationStopped: (:) [], IndexOutOfRangeException
+ FullyQualifiedErrorId : System.IndexOutOfRangeException
```

稍後當我談到如何擴大陣列時，我會重新回顧這種情況。

### <a name="iteration"></a>反覆運算

在某些時候，您可能需要針對陣列中的每個項目，逐一執行或逐一查看整個清單並執行動作。

#### <a name="pipeline"></a>管線

陣列和 PowerShell 管道皆彼此適用。 這是處理這些值最簡單的方式之一。 當您將陣列傳遞至管道時，陣列中的每個項目都會進行個別處理。

```powershell
PS> $data = 'Zero','One','Two','Three'
PS> $data | ForEach-Object {"Item: [$PSItem]"}
Item: [Zero]
Item: [One]
Item: [Two]
Item: [Three]
```

如果您之前看不到 `$PSItem`，只需要知道它與 `$_` 的內容相同即可。 您可以使用其中一種，因為兩者都代表管道中的目前物件。

#### <a name="foreach-loop"></a>ForEach 迴圈

`ForEach` 迴圈適用於集合。 使用語法： `foreach ( <variable> in <collection> )`

```powershell
foreach ( $node in $data )
{
    "Item: [$node]"
}
```

#### <a name="foreach-method"></a>ForEach 方法

我往往會忘了這項功能，但它很適合用於簡單的作業。 PowerShell 可讓您在集合上呼叫 `.ForEach()`。

```powershell
PS> $data.foreach({"Item [$PSItem]"})
Item [Zero]
Item [One]
Item [Two]
Item [Three]
```

`.foreach()` 接受屬於指令碼區塊的參數。 您可以置放括號，並僅提供指令碼區塊。

```powershell
$data.foreach{"Item [$PSItem]"}
```

這是鮮為人知的語法，但其運作方式完全相同。 此 `foreach` 方法已在 PowerShell 4.0 中新增。

#### <a name="for-loop"></a>For 迴圈

在大部分其他程式設計語言中，皆使用 `for` 迴圈，不過在 PowerShell 中並不多見。 當您看到該迴圈時，通常是在逐一執行陣列的內容中。

```powershell
for ( $index = 0; $index -lt $data.count; $index++)
{
    "Item: [{0}]" -f $data[$index]
}
```

我們首先該做的，就是將 `$index` 初始化為 `0`。 然後，我們會新增 `$index` 必須小於 `$data.count` 的條件。 最後，我們會指定每次迴圈時，我都必須藉由 `1` 來增加索引。 在此情況下，`$index++` 為 `$index = $index + 1` 縮短形。

當您使用 `for` 迴圈時，請特別注意該條件。 我在這裡使用 `$index -lt $data.count`。 您可以稍微讓條件出現錯誤，藉此在您的邏輯中取得差一錯誤。 使用 `$index -le $data.count` 或 `$index -lt ($data.count - 1)` 總是略有些許錯誤。 這會導致您的結果處理的項目過多或太少。 這是傳統的差一錯誤。

#### <a name="switch-loop"></a>Switch 迴圈

這是很容易忽略的一種。 如果您將陣列提供給 [switch 陳述式][]，則陳述式會檢查陣列中的每個項目。

```powershell
$data = 'Zero','One','Two','Three'
switch( $data )
{
    'One'
    {
        'Tock'
    }
    'Three'
    {
        'Tock'
    }
    Default
    {
        'Tick'
    }
}
```

```Output
Tick
Tock
Tick
Tock
```

我們可以使用 switch 陳述式來做很多很酷的事。 我有另一篇專文介紹這個。

- [您想知道有關於 [Switch 陳述式]的一切] (英文)

#### <a name="updating-values"></a>更新值

當陣列是字串或整數 (實值型別) 的集合時，您有時可能會在進行迴圈處理時，想要新陣列中的值。 以上大部分的迴圈會使用迴圈中的變數來保存值的複本。 如果您更新該變數，陣列中的原始值不會更新。

該陳述式的例外狀況是 `for` 迴圈。 如果您想要逐一執行陣列並更新其中的值，則 `for` 迴圈就是您要尋找的工具。

```powershell
for ( $index = 0; $index -lt $data.count; $index++ )
{
    $data[$index] = "Item: [{0}]" -f $data[$index]
}
```

此範例會依索引採用值，進行一些變更，然後使用該相同的索引將其指派回去。

## <a name="arrays-of-objects"></a>物件陣列

到目前為止，我們放入陣列中的唯一東西就是實值型別，不過陣列也可以包含物件。

```powershell
$data = @(
    [pscustomobject]@{FirstName='Kevin';LastName='Marquette'}
    [pscustomobject]@{FirstName='John'; LastName='Doe'}
)
```

當您將物件的集合指派給變數時，許多 Cmdlet 都會以陣列的形式將其傳回。

```powershell
$processList = Get-Process
```

我們已討論過的所有基本功能，仍適用於物件陣列，其中有一些值得加以說明的細節。

### <a name="accessing-properties"></a>存取屬性

我們可以使用索引來存取集合中的個別項目，就像使用實值型別一樣。

```powershell
PS> $data[0]

FirstName LastName
-----     ----
Kevin     Marquette
```

我們可以直接存取和更新屬性。

```powershell
PS> $data[0].FirstName

Kevin

PS> $data[0].FirstName = 'Jay'
PS> $data[0]

FirstName LastName
-----     ----
Jay       Marquette
```

#### <a name="array-properties"></a>陣列屬性

通常您必須列舉這類的完整清單，才能存取所有屬性：

```powershell
PS> $data | ForEach-Object {$_.LastName}

Marquette
Doe
```

或藉由使用 `Select-Object -ExpandProperty` Cmdlet 達到目的。

```powershell
PS> $data | Select-Object -ExpandProperty LastName

Marquette
Doe
```

不過，PowerShell 讓我們能夠直接要求 `LastName`。 PowerShell 會為我們列舉所有清單，並傳回一份清除清單。

```powershell
PS> $data.LastName

Marquette
Doe
```

列舉仍然會發生，但我們無法瞭解其背後的複雜性。

### <a name="where-object-filtering"></a>Where-Object 篩選

這就是 `Where-Object` 的進入位置，因此我們可以根據物件的屬性，篩選並選取我們想要的陣列內容。

```powershell
PS> $data | Where-Object {$_.FirstName -eq 'Kevin'}

FirstName LastName
-----     ----
Kevin     Marquette
```

我們可以撰寫相同的查詢，以取得我們所要尋找的 `FirstName`。

```powershell
$data | Where FirstName -eq Kevin
```

#### <a name="where"></a>Where()

陣列具有 `Where()` 的方法，可讓您指定篩選條件的 `scriptblock`。

```powershell
$data.Where({$_.FirstName -eq 'Kevin'})
```

此功能已在 PowerShell 4.0 中新增。

### <a name="updating-objects-in-loops"></a>更新迴圈中的物件

採用實值型別時，更新陣列的唯一方式是使用 for 迴圈，因為我們需要知道索引以取代值。 我們有更多選項可使用物件，因為它們是參考型別。 以下是一個簡短的範例：

```powershell
foreach($person in $data)
{
    $person.FirstName = 'Kevin'
}
```

這個迴圈會逐一執行 `$data` 陣列中的每個物件。 由於物件屬於參考型別，因此 `$person` 變數會參考陣列中完全相同的物件。 因此，更新其屬性會更新原始物件。

您仍然無法以這種方式來取代整個物件。 如果您嘗試將新物件指派給 `$person` 變數，則會將變數參考更新為不會再指向陣列中原始物件的其他物件。 這種運作方式與您的預期不同：

```powershell
foreach($person in $data)
{
    $person = [pscustomobject]@{
        FirstName='Kevin'
        LastName='Marquette'
    }
}
```

## <a name="operators"></a>操作員

PowerShell 中的運算子也適用陣列。 其中一些工作的執行方式稍有不同。

### <a name="-join"></a>-join

`-join` 運算子最明顯，因此讓我們先瞭解一下。 我喜歡 `-join` 運算子並經常使用。 它會將陣列中的所有元素與您指定的字元或字串聯結在一起。

```powershell
PS> $data = @(1,2,3,4)
PS> $data -join '-'
1-2-3-4
PS> $data -join ','
1,2,3,4
```

我喜歡 `-join` 運算子的其中一項功能，就是它會處理單一項目。

```powershell
PS> 1 -join '-'
1
```

我在記錄和詳細資訊訊息中使用此功能。

```powershell
PS> $data = @(1,2,3,4)
PS> "Data is $($data -join ',')."
Data is 1,2,3,4.
```

#### <a name="-join-array"></a>-join $array

Lee Dailey 在這裡向我傳授一個聰明的技巧。 如果您想要加入任何不含分隔符號的內容，您可以改用以下方式：

```powershell
PS> $data = @(1,2,3,4)
PS> $data -join $null
1234
```

您可以使用 `-join` 搭配陣列做為參數，而不使用前置詞。 請檢視此範例，瞭解我所說的內容。

```powershell
PS> $data = @(1,2,3,4)
PS> -join $data
1234
```

### <a name="-replace-and--split"></a>-replace 與 -split

`-replace` 和 `-split` 等其他運算子會在陣列中的每個項目上執行。 我不能說我曾用過這種方式，但這裡有一個範例。

```powershell
PS> $data = @('ATX-SQL-01','ATX-SQL-02','ATX-SQL-03')
PS> $data -replace 'ATX','LAX'
LAX-SQL-01
LAX-SQL-02
LAX-SQL-03
```

### <a name="-contains"></a>-contains

`-contains` 運算子可讓您檢查值的陣列，以查看其是否包含指定的值。

```powershell
PS> $data = @('red','green','blue')
PS> $data -contains 'green'
True
```

### <a name="-in"></a>-in

當您有想要驗證的單一值符合數個值的其中之一時，您可以使用 `-in` 運算子。 這個值會在左邊，而陣列位於運算子右側。

```powershell
PS> $data = @('red','green','blue')
PS> 'green' -in $data
True
```

如果清單很大，這可能會產生昂貴的費用。 如果我檢查的值不是少數幾個，我通常會使用 RegEx 模式。

```powershell
PS> $data = @('red','green','blue')
PS> $pattern = "^({0})$" -f ($data -join '|')
PS> $pattern
^(red|green|blue)$

PS> 'green' -match $pattern
True
```

### <a name="-eq-and--ne"></a>-eq 和-ne

等式和陣列可能會變得複雜。 當陣列位於左側時，會比較每個項目。 這樣並不會傳回 `True`，而是會傳回符合的物件。

```powershell
PS> $data = @('red','green','blue')
PS> $data -eq 'green'
green
```

當您使用 `-ne` 運算子時，我們會取得所有與我們值不相等的值。

```powershell
PS> $data = @('red','green','blue')
PS> $data -ne 'green'
red
blue
```

當您在 `if()` 陳述式中使用這種方式時，傳回的值就是 `True` 值。 如果未傳回任何值，則為 `False` 值。 這兩個後續陳述式都會評估為 `True`。

```powershell
$data = @('red','green','blue')
if ( $data -eq 'green' )
{
    'Green was found'
}
if ( $data -ne 'green' )
{
    'And green was not found'
}
```

我稍後會回顧一下我們談到的 `$null` 的測試。

### <a name="-match"></a>-match

`-match` 運算子會嘗試比對集合中的每個項目。

```powershell
PS> $servers = @(
    'LAX-SQL-01'
    'LAX-API-01'
    'ATX-SQL-01'
    'ATX-API-01'
)
PS> $servers -match 'SQL'
LAX-SQL-01
ATX-SQL-01
```

當您使用具有單一值的 `-match` 時，會以符合的資訊填入一個特殊的變數 `$Matches`。 若以這種方式處理陣列，就不會出現這種情況。

我們可以採用與 `Select-String` 相同的方法。

```powershell
$servers | Select-String SQL
```

我會進一步檢視 `Select-String`、`-match` 和另一篇文章 ([使用 RegEx 的許多方式][] (英文)) 中的 `$matches` 變數。

### <a name="null-or-empty"></a>$null 或 empty

測試 `$null` 或空陣列可能會很棘手。 以下是陣列的常見陷阱。

乍看之下，這個陳述式看起來應該可以運作。

```powershell
if ( $array -eq $null)
{
    'Array is $null'
}
```

但是我只是在 `-eq` 檢查陣列中的每個項目。 因此，我們可以擁有數個項目的陣列，其中包含單一 $null 值，而且該值會評估為 `$true`

```powershell
$array = @('one',$null,'three')
if ( $array -eq $null)
{
    'I think Array is $null, but I would be wrong'
}
```

這就是將 `$null` 放在運算子左邊是最佳做法的理由所在。 這會讓此情況成為不會發生的問題。

```powershell
if ( $null -eq $array )
{
    'Array actually is $null'
}
```

`$null` 陣列與空陣列屬於不同的陣列。 若您知道自己有陣列，請檢查其中的物件計數。 如果陣列為 `$null`，則計數為 `0`。

```powershell
if ( $array.count -gt 0 )
{
    "Array isn't empty"
}
```

這裡還有另一個要注意的陷阱。 即使您有單一物件，您仍然可以使用 `count`，除非該物件是 `PSCustomObject`。 這是 PowerShell 6.1 中所修正的錯誤。
這是好消息，但有很多人仍在使用 5.1，而且需要留意。

```powershell
PS> $object = [PSCustomObject]@{Name='TestObject'}
PS> $object.count
$null
```

如果您仍在使用 PowerShell 5.1，您可以先將物件包裝在陣列中，再檢查計數以取得精確的計數。

```powershell
if ( @($array).count -gt 0 )
{
    "Array isn't empty"
}
```

為了充分確保安全起見，請檢查 `$null`，然後檢查計數。

```powershell
if ( $null -ne $array -and @($array).count -gt 0 )
{
    "Array isn't empty"
}
```

### <a name="all--eq"></a>全部 -eq

我最近看到有人詢問 [如何驗證陣列中的每個值是否符合指定的值][]。
Reddit 使用者 **/u/bis** 享有這項聰明的 [解決方案][]，可檢查是否有任何不正確的值，然後將結果翻轉。

```powershell
$results = Test-Something
if ( -not ( $results -ne 'Passed') )
{
    'All results a Passed'
}
```

## <a name="adding-to-arrays"></a>新增至陣列

此時，您會開始對如何將項目新增至陣列感到懷疑。 簡單明瞭的答案就是您無法將項目新增至陣列。 陣列在記憶體中的大小是固定的。 如果您需要擴充陣列或在其中加入單一項目，則需要建立新的陣列，並將所有的值複製到舊陣列。 就跟很多工作一樣，這聽起來十分費工；不過，PowerShell 會隱藏建立新陣列的複雜性。 PowerShell 會為陣列實作新增運算子 (`+`)。

> [!NOTE]
> PowerShell 不會實作減法運算。 如果您想要有彈性的陣列替代方案，則必須使用[泛型`List`](#generic-list)物件。

### <a name="array-addition"></a>新增陣列

我們可以搭配使用新增運算子與陣列來建立新的陣列。 因此，假設有這兩個陣列：

```powershell
$first = @(
    'Zero'
    'One'
)
$second = @(
    'Two'
    'Three'
)
```

我們可以將其合併以取得新的陣列。

```powershell
PS> $first + $second

Zero
One
Two
Three
```

### <a name="plus-equals-"></a>Plus equals +=

我們可以就地建立新的陣列，並在其中新增項目，如下所示：

```powershell
$data = @(
    'Zero'
    'One'
    'Two'
    'Three'
)
$data += 'four'
```

請記住，您每次使用 `+=` 時，都會複製並建立新的陣列。 這不是小型資料集的問題，而是以極不理想的方式進行規模調整。

### <a name="pipeline-assignment"></a>管道指派

您可以將任何管道的結果指派至變數中。 如果其中包含多個項目，則為陣列。

```powershell
$array = 1..5 | ForEach-Object {
    "ATX-SQL-$PSItem"
}
```

通常當我們想要使用管道時，我們會考慮使用一般的 PowerShell 一行程式碼。 我們可以利用管道搭配 `foreach()` 陳述式和其他迴圈。 因此，我們不會將項目新增至迴圈中的陣列，而是可以將項目放置在管道上。

```powershell
$array = foreach ( $node in (1..5))
{
    "ATX-SQL-$node"
}
```

## <a name="array-types"></a>陣列類型

根據預設，系統建立 PowerShell 中的陣列做為 `[PSObject[]]` 類型。 如此可使其包含任何類型的物件或值。 這種方式有效，是因為所有項目都是從 `PSObject` 類型繼承而來。

### <a name="strongly-typed-arrays"></a>強類型陣列

您可以使用類似的語法來建立任何類型的陣列。 當您建立強類型陣列時，它只能包含指定類型的值或物件。

```powershell
PS> [int[]] $numbers = 1,2,3
PS> [int[]] $numbers2 = 'one','two','three'
ERROR: Cannot convert value "one" to type "System.Int32". Input string was not in a correct format."

PS> [string[]] $strings = 'one','two','three'
```

### <a name="arraylist"></a>ArrayList

將項目新增至陣列是其最大的限制之一，但還有一些其他集合可供我們使用，從而解決這個問題。

當我們需要更快速使用的陣列時，`ArrayList` 通常是我們想到的第一個辦法。 它的作用就像是物件陣列，我們在任何場合都需要它，但它會快速地處理新增項目。

以下是我們建立 `ArrayList` 並在其中新增項目的方式。

```powershell
$myarray = [System.Collections.ArrayList]::new()
[void]$myArray.Add('Value')
```

我們會呼叫 .NET 來取得這種類型。 在此情況下，我們會使用預設的建構函式來建立它。 然後，我們會呼叫 `Add` 方法，並將項目新增至其中。

我在行首使用 `[void]` 的原因，是要隱藏傳回程式碼。 有些 .NET 呼叫會執行此動作，而且可能會產生非預期的輸出。

如果您在陣列中的唯一資料是字串，則也請瞭解 [StringBuilder][] 的使用方式。 這幾乎是相同的東西，但有一些僅供處理字串的方法。 `StringBuilder` 是專為效能而特別設計的。

人們從陣列移至 `ArrayList` 的情況很常見。 但這種情況發生在 C# 並未提供泛型支援的時代。 `ArrayList` 在泛型的 `List[]` 支援中已淘汰

### <a name="generic-list"></a>泛型清單

泛型型別是中的特殊類型 C# ，可定義一般化類別，而使用者會指定它在建立時所使用的資料類型。 因此，如果您需要數字或字串的清單，您可以定義想要 `int` 或 `string` 類型的清單。

以下是建立字串清單的方式。

```powershell
$mylist = [System.Collections.Generic.List[string]]::new()
```

或者您也可以數字的清單。

```powershell
$mylist = [System.Collections.Generic.List[int]]::new()
```

我們可以將現有的陣列轉換成類似如下的清單，而且不需要先建立物件：

```powershell
$mylist = [System.Collections.Generic.List[int]]@(1,2,3)
```

我們可以使用 PowerShell 5 和更新版本中的 `using namespace` 陳述式來縮短語法。 `using` 陳述式必須是指令碼的第一行。 藉由宣告命名空間，PowerShell 可讓您在參考資料類型時，將其剔除。

```powershell
using namespace System.Collections.Generic
$myList = [List[int]]@(1,2,3)
```

這可讓 `List` 變得更容易使用。

您可以使用類似 `Add` 的方法。 有別於 ArrayList，`Add` 方法沒有傳回值，因此我們不需要 `void` 它。

```powershell
$myList.Add(10)
```

我們仍然可以存取其他陣列之類的元素。

```powershell
PS> $myList[-1]
10
```

#### <a name="listpsobject"></a>List[PSObject]

您可擁有任何類型的清單，但在不知道物件類型時，可使用 `[List[PSObject]]` 加以包含。

```powershell
$list = [List[PSObject]]::new()
```

#### <a name="remove"></a>Remove()

`ArrayList` 和泛型 `List[]` 都支援從集合中移除項目。

```powershell
using namespace System.Collections.Generic
$myList = [List[string]]@('Zero','One','Two','Three')
[void]$myList.Remove("Two")
Zero
One
Three
```

使用實值型別時，它會從清單中移除第一個項目。 您可以再次呼叫它，以便繼續移除該值。 如果您有參考型別，則您必須提供要移除的物件。

```powershell
[list[System.Management.Automation.PSDriveInfo]]$drives = Get-PSDrive
$drives.remove($drives[2])
```

```powershell
$delete = $drives[2]
$drives.remove($delete)
```

如果可以從集合中尋找並移除項目，則 remove 方法會傳回 `true`。

### <a name="more-collections"></a>更多集合

還有許多其他可以使用的集合，但是有良好的泛型陣列替代品。
如果您想要深入瞭解更多選項，請查看此 [Gist](https://gist.github.com/kevinblumenfeld/4a698dbc90272a336ed9367b11d91f1c)，那是由 [Mark Kraus](https://get-powershellblog.blogspot.com/2016/11/about-mark-kraus.html) 合併在一起的。

## <a name="other-nuances"></a>其他細微差異

現在我已經討論過所有的主要功能，接下來我要提到幾件事，再進行總結。

### <a name="pre-sized-arrays"></a>預先調整大小的陣列

我說過，一旦建立陣列之後，您就無法變更它的大小。 我們可以使用 `new($size)` 建構函式來呼叫它，以建立預先決定大小的陣列。

```powershell
$data = [Object[]]::new(4)
$data.count
4
```

### <a name="multiplying-arrays"></a>相乘陣列

有趣的小技巧是，您可以將陣列乘以一個整數。

```powershell
PS> $data = @('red','green','blue')
PS> $data * 3
red
green
blue
red
green
blue
red
green
blue
```

### <a name="initialize-with-0"></a>以 0 初始化

常見的情況是您想要建立全部為零的陣列。 如果您只會有整數，則強型別的整數陣列會預設為全部為零。

```powershell
PS> [int[]]::new(4)
0
0
0
0
```

我們也可以使用相乘的技巧來執行此動作。

```powershell
PS> $data = @(0) * 4
PS> $data
0
0
0
0
```

「相乘」技巧的好處是您可以使用任何值。 因此，如果您想要以 `255` 做為預設值，這會是很好的方式。

```powershell
PS> $data = @(255) * 4
PS> $data
255
255
255
255
```

### <a name="nested-arrays"></a>嵌套陣列

陣列中的陣列稱為「嵌套陣列」。 我不會在 PowerShell 中使用這些功能，但我在其他程式設計語言中使用了這些功能。 當您的資料符合資料格 (如模式) 時，請考慮在各陣列中使用一個陣列。

這裡提供兩種方式可以建立二維陣列。

```powershell
$data = @(@(1,2,3),@(4,5,6),@(7,8,9))

$data2 = @(
    @(1,2,3),
    @(4,5,6),
    @(7,8,9)
)
```

在這些範例中，逗點非常重要。 我先前針對多行提供了一個一般陣列的範例，其中逗號是選擇性使用的。 多維陣列則不會發生這種情況。

我們使用索引標記法的方式現在有了些許變更，因為我們已經有了嵌套陣列。 使用上述 `$data`，這就是我們存取值 3 的方式。

```powershell
PS> $outside = 0
PS> $inside = 2
PS> $data[$outside][$inside]
3
```

為每個陣列嵌套層級新增一組括弧。 第一組括弧是針對最外部的陣列，然後以您的方式從該處開始作業。

### <a name="write-output--noenumerate"></a>Write-Output -NoEnumerate

PowerShell 習慣取消換行或列舉陣列。 這是 PowerShell 使用管道的核心層面，但有時您不希望出現這種情況。

我通常會將物件輸送至 `Get-Member` 以便進行深入瞭解。 當我使用管道將陣列輸送給它時，它會取消換行，而 Get-Member 會看到陣列的成員，而不是實際的陣列。

```powershell
PS> $data = @('red','green','blue')
PS> $data | Get-Member
TypeName: System.String
...
```

若要避免陣列取消換行，您可以使用 `Write-Object -NoEnumerate`。

```powershell
PS> Write-Output -NoEnumerate $data | Get-Member
TypeName: System.Object[]
...
```

我還有第二種方式，也就是駭客入侵的手法 (而且我試著避免這類的駭客入侵守法)。 您可以將逗號放在陣列前方，然後再使用管道輸送。

```powershell
PS> ,$data | Get-Member
TypeName: System.Object[]
...
```

### <a name="return-an-array"></a>傳回陣列

當您從函式輸出或傳回值時，也會發生此陣列取消換行的情況。 如果您將輸出指派給變數，但這通常不是問題，您仍然可以取得陣列。

Catch 是您有新的陣列。 如果這樣造成困擾，您可以使用 `Write-Output -NoEnumerate $array` 或 `return ,$array` 來解決問題。

## <a name="anything-else"></a>還想知道什麼嗎？

我知道這裡有很多內容需要吸收消化。 我希望您每次閱讀本文時，都學到一些東西，而且本文將會是您未來漫長歲月中的絕佳參考資料。 若您認為本文內容實用，請與您認為可能會從中獲得價值的其他人分享。

從這裡開始，我會建議您查看我所寫的關於[雜湊表][]的類似文章。

<!-- link references -->
[原始版本]: https://powershellexplained.com/2018-10-15-Powershell-arrays-Everything-you-wanted-to-know/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[陣列]: /powershell/module/microsoft.powershell.core/about/about_arrays
[switch 陳述式]: everything-about-switch.md
[雜湊表]: everything-about-hashtable.md
[使用 RegEx 的許多方式]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/
[如何驗證陣列中的每個值是否符合指定的值]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition
[解決方案]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition/e7iizca
[StringBuilder]: https://powershellexplained.com/2017-11-20-Powershell-StringBuilder/
