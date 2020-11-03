---
description: 描述陣列，這些是設計用來儲存專案集合的資料結構。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/26/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_arrays?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Arrays
ms.openlocfilehash: 2283c36d899c3ea743f6c379dc686ec583d7a36c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206784"
---
# <a name="about-arrays"></a>關於陣列

## <a name="short-description"></a>簡短描述
描述陣列，這些是設計用來儲存專案集合的資料結構。

## <a name="long-description"></a>完整描述

陣列是設計用來儲存專案集合的資料結構。
專案可以是相同類型或不同類型。

從 Windows PowerShell 3.0 開始，零或一個物件的集合會有陣列的某些屬性。

## <a name="creating-and-initializing-an-array"></a>建立和初始化陣列

若要建立及初始化陣列，請將多個值指派給變數。 儲存在陣列中的值會以逗號分隔，並以指派運算子 () 分隔引數名稱 `=` 。

例如，若要建立名為 `$A` 的陣列，其中包含七個數值 (int) 值22、5、10、8、12、9和80，請輸入：

```powershell
$A = 22,5,10,8,12,9,80
```

您也可以將逗號放在單一專案之前，以使用逗號初始化單一專案陣列。

例如，若要建立名為的單一專案陣列 `$B` ，其中包含單一值7，請輸入：

```powershell
$B = ,7
```

您也可以使用範圍運算子 () 來建立和初始化陣列 `..` 。
下列範例會建立包含值5到8的陣列。

```powershell
$C = 5..8
```

因此， `$C` 包含四個值：5、6、7和8。

未指定任何資料類型時，PowerShell 會將每個陣列建立為物件陣列 ( **system.object []** ) 。 若要判斷陣列的資料類型，請使用 **GetType ( # B1** 方法。 例如，若要判斷陣列的資料類型 `$A` ，請輸入：

```powershell
$A.GetType()
```

若要建立強型別陣列，也就是只能包含特定類型之值的陣列，請將變數轉換為數組類型，例如 **string []** 、 **long []** 或 **int32 []** 。 若要轉換陣列，請在變數名稱之前加上括弧括住的陣列類型。 例如，若要建立名為的32位整數陣列 `$ia` ，其中包含四個整數 (1500、2230、3350和 4000) ，請輸入：

```powershell
[int32[]]$ia = 1500,2230,3350,4000
```

因此， `$ia` 陣列只能包含整數。

您可以建立在 Microsoft .NET Framework 中轉換成任何支援類型的陣列。 例如，用 `Get-Process` 來表示處理 **程式** 的物件是由系統的 ... 處理型別。 若要建立處理常式物件的強型別陣列，請輸入下列命令：

```powershell
[Diagnostics.Process[]]$zz = Get-Process
```

## <a name="the-array-sub-expression-operator"></a>陣列子運算式運算子

陣列子運算式運算子會從它內部的語句建立陣列。 無論運算子內的語句產生什麼，運算子都會將它放置在陣列中。 即使有零個或一個物件。

陣列運算子的語法如下所示：

```syntax
@( ... )
```

您可以使用 array 運算子來建立零或一個物件的陣列。 例如：

```powershell
$a = @("Hello World")
$a.Count
```

```Output
1
```

```powershell
$b = @()
$b.Count
```

```Output
0
```

當您取得物件時，array 運算子在腳本中很有用，但不知道您取得的物件數目。 例如：

```powershell
$p = @(Get-Process Notepad)
```

如需有關陣列子運算式運算子的詳細資訊，請參閱 [about_Operators](about_Operators.md)。

## <a name="accessing-and-using-array-elements"></a>存取和使用陣列元素

### <a name="reading-an-array"></a>讀取陣列

您可以使用變數名稱來參考陣列。 若要顯示陣列中的所有元素，請輸入陣列名稱稱。 例如，假設 `$a` 是一個陣列，其中包含0、1、2到9的整數; 輸入：

```powershell
$a
```

```Output
0
1
2
3
4
5
6
7
8
9
```

您可以使用索引（從位置0開始）來參考陣列中的元素。 以括弧括住索引編號。 例如，若要顯示陣列中的第一個元素 `$a` ，請輸入：

```powershell
$a[0]
```

```Output
0
```

若要顯示陣列中的第三個元素 `$a` ，請輸入：

```powershell
$a[2]
```

```Output
2
```

您可以使用索引的範圍運算子來取得陣列的一部分。 例如，若要取出陣列的第二到第五個元素，您可以輸入：

```powershell
$a[1..4]
```

```Output
1
2
3
4
```

從陣列結尾算算的負數。 例如，"-1" 是指陣列的最後一個元素。 若要顯示陣列的最後三個元素，請在 [索引遞增順序] 中輸入：

```powershell
$a = 0 .. 9
$a[-3..-1]
```

```Output
7
8
9
```

如果您以遞減順序輸入負索引，則輸出會變更。

```powershell
$a = 0 .. 9
$a[-1..-3]
```

```Output
9
8
7
```

不過，使用此標記法時請務必小心。 標記法從結束界限到陣列開頭的迴圈。

```powershell
$a = 0 .. 9
$a[2..-2]
```

```Output
2
1
0
9
8
```

此外，另一個常見的錯誤是假設 `$a[0..-2]` 是參考陣列的所有元素，但最後一個除外。 它會參考陣列中的第一個、最後一個和第二個元素。

您可以使用加號運算子 (`+`) ，將範圍與陣列中的元素清單結合。 例如，若要顯示索引位置0、2和4到6的元素，請輸入：

```powershell
$a = 0 .. 9
$a[0,2+4..6]
```

```Output
0
2
4
5
6
```

此外，若要列出多個範圍和個別元素，您可以使用加號運算子。 例如，將專案從零到二、四到6，以及在第八個位置型別上的元素列出：

```powershell
$a = 0..9
$a[+0..2+4..6+8]
```

```Output
0
1
2
4
5
6
8
```

### <a name="iterations-over-array-elements"></a>反覆運算陣列元素

您也可以使用迴圈結構（例如 ForEach、For 和 While 迴圈）來參考陣列中的元素。 例如，若要使用 ForEach 迴圈來顯示陣列中的元素 `$a` ，請輸入：

```powershell
$a = 0..9
foreach ($element in $a) {
  $element
}
```

```Output
0
1
2
3
4
5
6
7
8
9
```

Foreach 迴圈會逐一查看陣列，並傳回陣列中的每個值，直到到達陣列的結尾為止。

當您在檢查陣列中的元素時，當您要遞增計數器時，For 迴圈會很有用。 例如，若要使用 For 迴圈來傳回陣列中的每個其他值，請輸入：

```powershell
$a = 0..9
for ($i = 0; $i -le ($a.length - 1); $i += 2) {
  $a[$i]
}
```

```Output
0
2
4
6
8
```

您可以使用 While 迴圈來顯示陣列中的元素，直到定義的條件不再為 true 為止。 例如，若要在 `$a` 陣列索引小於4時顯示陣列中的元素，請輸入：

```powershell
$a = 0..9
$i=0
while($i -lt 4) {
  $a[$i];
  $i++
}
```

```Output
0
1
2
3
```

## <a name="properties-of-arrays"></a>陣列的屬性

### <a name="count-or-length-or-longlength"></a>Count 或 Length 或 LongLength

若要判斷陣列中有多少個專案，請使用 `Length` 屬性或其 `Count` 別名。 `Longlength` 如果陣列包含2147483647以上的元素，則會很有用。

```powershell
$a = 0..9
$a.Count
$a.Length
```

```Output
10
10
```

### <a name="rank"></a>排名

傳回陣列中的維度數目。 PowerShell 中大部分的陣列只有一個維度。 即使您想要建立多維度陣列;如下列範例所示：

```powershell
$a = @(
  @(0,1),
  @("b", "c"),
  @(Get-Process)
)

[int]$r = $a.Rank
"`$a rank: $r"
```

```Output
$a rank: 1
```

下列範例示範如何使用 .Net Framework 建立真正的多維陣列。

```powershell
[int[,]]$rank2 = [int[,]]::new(5,5)
$rank2.rank
```

```Output
2
```

## <a name="methods-of-arrays"></a>陣列的方法

### <a name="clear"></a>Clear

將所有元素值設定為數組專案類型的 _預設值_ 。
Clear ( # A1 方法不會重設陣列的大小。

在下列範例中 `$a` ，是物件的陣列。

```powershell
$a = 1, 2, 3
$a.Clear()
$a | % { $null -eq $_ }
```

```Output
True
True
True
```

在此範例中， `$intA` 明確類型為包含整數。

```powershell
[int[]] $intA = 1, 2, 3
$intA.Clear()
$intA
```

```Output
0
0
0
```

### <a name="foreach"></a>ForEach

允許逐一查看陣列中的所有元素，並針對陣列的每個元素執行指定的作業。

ForEach 方法有數個多載，可執行不同的作業。

```
ForEach(scriptblock expression)
ForEach(scriptblock expression, object[] arguments)
ForEach(type convertToType)
ForEach(string propertyName)
ForEach(string propertyName, object[] newValue)
ForEach(string methodName)
ForEach(string methodName, object[] arguments)
```

#### <a name="foreachscriptblock-expression"></a>ForEach (scriptblock 運算式) 

#### <a name="foreachscriptblock-expression-object-arguments"></a>ForEach (scriptblock 運算式，object [] 引數) 

此方法已新增至 PowerShell v4。

> [!NOTE]
> 語法需要使用腳本區塊。 如果 scriptblock 是唯一的參數，則括弧是選擇性的。 此外，方法和左括弧或大括弧之間不得有空格。

下列範例顯示如何使用 foreach 方法。 在此情況下，目的是要產生陣列中元素的平方值。

```powershell
$a = @(0 .. 3)
$a.ForEach({ $_ * $_})
```

```Output
0
1
4
9
```

如同的 `-ArgumentList` 參數 `ForEach-Object` ， `arguments` 參數允許將引數陣列傳遞至設定為接受這些引數的腳本區塊。

如需有關 **ArgumentList** 行為的詳細資訊，請參閱 [about_Splatting](about_Splatting.md#splatting-with-arrays)。

#### <a name="foreachtype-converttotype"></a>ForEach (類型 convertToType) 

`ForEach`方法可以用來將專案轉換成不同的類型; 下列範例會示範如何將字串日期清單轉換成 `[DateTime]` 型別。

```powershell
@("1/1/2017", "2/1/2017", "3/1/2017").ForEach([datetime])
```

```Output

Sunday, January 1, 2017 12:00:00 AM
Wednesday, February 1, 2017 12:00:00 AM
Wednesday, March 1, 2017 12:00:00 AM
```

#### <a name="foreachstring-propertyname"></a>ForEach (字串屬性名稱) 

#### <a name="foreachstring-propertyname-object-newvalue"></a>ForEach (string propertyName，object [] newValue) 

`ForEach`方法也可以用來快速取得或設定集合中每個專案的屬性值。

```powershell
# Set all LastAccessTime properties of files to the current date.
(dir 'C:\Temp').ForEach('LastAccessTime', (Get-Date))
# View the newly set LastAccessTime of all items, and find Unique entries.
(dir 'C:\Temp').ForEach('LastAccessTime') | Get-Unique
```

```Output
Wednesday, June 20, 2018 9:21:57 AM
```

#### <a name="foreachstring-methodname"></a>ForEach (字串方法名稱) 

#### <a name="foreachstring-methodname-object-arguments"></a>ForEach (字串方法名稱，object [] 引數) 

最後， `ForEach` 方法可以用來在集合中的每個專案上執行方法。

```powershell
("one", "two", "three").ForEach("ToUpper")
```

```Output
ONE
TWO
THREE
```

如同的 `-ArgumentList` 參數 `ForEach-Object` ， `arguments` 參數允許將引數陣列傳遞至設定為接受這些引數的腳本區塊。

> [!NOTE]
> 從 Windows PowerShell 3.0 開始，也可以使用「純量物件和集合的方法」來完成集合中每個專案的屬性和執行方法，您可以在這裡閱讀更多相關資訊 [about_methods](about_methods.md)。

### <a name="where"></a>Where

允許篩選或選取陣列的元素。 腳本必須評估為與下列專案不同的專案：零 (0) 、空字串， `$false` 或專案 `$null` 要顯示在 `Where`

方法有一個定義 `Where` 。

```
Where(scriptblock expression[, WhereOperatorSelectionMode mode
                            [, int numberToReturn]])
```

> [!NOTE]
> 語法需要使用腳本區塊。 如果 scriptblock 是唯一的參數，則括弧是選擇性的。 此外，方法和左括弧或大括弧之間不得有空格。

`Expression`是篩選所需的 scriptblock， `mode` 選擇性引數允許其他選取功能，而 `numberToReturn` 選擇性引數可讓您限制從篩選傳回的專案數目。

的可接受值為 `mode` ：

- 預設 (0) -傳回所有專案
- 第一個 (1) -傳回第一個專案
- 最後 (2) -傳回最後一個專案
- SkipUntil (3) -略過專案直到條件為 true，傳回剩餘的專案
- 直到 (4) -傳回所有專案，直到條件為 true
- 分割 (5) -傳回兩個元素的陣列
  - 第一個元素包含相符的專案
  - 第二個元素包含其餘專案

下列範例顯示如何從陣列中選取所有奇數。

```powershell
(0..9).Where{ $_ % 2 }
```

```Output
1
3
5
7
9
```

這個範例會示範如何選取非空白的字串。

```powershell
('hi', '', 'there').Where({$_.Length})
```

```Output
hi
there
```

#### <a name="default"></a>預設

此 `Default` 模式會使用 scriptblock 篩選項目 `Expression` 。

如果 `numberToReturn` 已提供，它會指定要傳回的專案數目上限。

```powershell
# Get the zip files in the current users profile, sorted by LastAccessTime.
$Zips = dir $env:userprofile -Recurse '*.zip' | Sort-Object LastAccessTime
# Get the least accessed file over 100MB
$Zips.Where({$_.Length -gt 100MB}, 'Default', 1)
```

> [!NOTE]
> `Default`模式和模式都會傳回 `First` 第一個 (`numberToReturn`) 專案，而且可以交換使用。

#### <a name="last"></a>最後一個

```powershell
$h = (Get-Date).AddHours(-1)
$logs = dir 'C:\' -Recurse '*.log' | Sort-Object CreationTime
# Find the last 5 log files created in the past hour.
$logs.Where({$_.CreationTime -gt $h}, 'Last', 5)
```

#### <a name="skipuntil"></a>SkipUntil

`SkipUntil`模式會略過集合中的所有物件，直到物件通過腳本區塊運算式篩選。 然後，它會傳回 **所有** 其餘的收集項，而不進行測試。 _只測試一個傳遞專案_ 。

這表示傳回的集合包含未經過測試的 _傳遞_ 和 _未傳遞_ 專案。

傳回的專案數可透過傳遞值給 `numberToReturn` 引數來限制。

```powershell
$computers = "Server01", "Server02", "Server03", "localhost", "Server04"
# Find the first available online server.
$computers.Where({ Test-Connection $_ }, 'SkipUntil', 1)
```

```Output
localhost
```

#### <a name="until"></a>直到

`Until`模式會反轉 `SkipUntil` 模式。  它會傳回集合中的 **所有** 專案，直到專案通過腳本區塊運算式為止。 一旦專案 _通過_ scriptblock 運算式，方法就會 `Where` 停止處理專案。

這表示您會收到來自方法的第一組 _非傳遞_ 專案 `Where` 。 一個專案通過 _後_ ，就不會測試或傳回其餘部分。

傳回的專案數可透過傳遞值給 `numberToReturn` 引數來限制。

```powershell
# Retrieve the first set of numbers less than or equal to 10.
(1..50).Where({$_ -gt 10}, 'Until')
# This would perform the same operation.
(1..50).Where({$_ -le 10})
```

```Output
1
2
3
4
5
6
7
8
9
10
```

> [!NOTE]
> `Until`和都 `SkipUntil` 是在不測試一批專案的前提下運作。
>
> `Until`_傳回_ 第一次行程 **之前** 的專案。
>
> `SkipUntil`傳回第一次 _傳遞_**之後** 的所有專案，包括第一個傳遞專案。

#### <a name="split"></a>分割

`Split`模式會分割，或將集合專案分組為兩個不同的集合。 傳遞 scriptblock 運算式的那些運算式，以及不會傳遞的運算式。

如果 `numberToReturn` 指定了，則第一個集合會包含 _傳遞_ 的專案，而不會超過指定的值。

其餘的物件（甚至是 **通過** 運算式篩選的物件）會在第二個集合中傳回。

```powershell
$running, $stopped = (Get-Service).Where({$_.Status -eq 'Running'}, 'Split')
$running
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  Appinfo            Application Information
Running  AudioEndpointBu... Windows Audio Endpoint Builder
Running  Audiosrv           Windows Audio
...
```

```powershell
$stopped
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
...
```

## <a name="get-the-members-of-an-array"></a>取得陣列的成員

若要取得陣列的屬性和方法（例如 Length 屬性和 **SetValue** 方法），請使用 Cmdlet 的 **InputObject** 參數 `Get-Member` 。

當您使用管線將陣列傳送至時 `Get-Member` ，PowerShell 會一次傳送一個專案，並傳回 `Get-Member` 陣列中每個專案的類型 (忽略重複專案) 。

當您使用 **InputObject** 參數時，會傳回 `Get-Member` 陣列的成員。

例如，下列命令會取得 `$a` 陣列變數的成員。

```powershell
Get-Member -InputObject $a
```

您也可以在傳送至 Cmdlet 的值之前輸入逗號 ( ) ，以取得陣列的成員 `Get-Member` 。 逗號會讓陣列成為陣列陣列中的第二個專案。 PowerShell 會一次將一個陣列輸送，並傳回 `Get-Member` 陣列的成員。 如同接下來的兩個範例。

```powershell
,$a | Get-Member

,(1,2,3) | Get-Member
```

## <a name="manipulating-an-array"></a>運算元組

您可以變更陣列中的元素、將專案加入至陣列，以及將兩個數組的值結合成第三個數組。

若要變更陣列中特定專案的值，請指定您要變更的陣列名稱稱和元素的索引，然後使用指派運算子 (`=`) 來指定專案的新值。 例如，若要將陣列中第二個專案的值 `$a` (索引位置 1) 變更為10，請輸入：

```powershell
$a[1] = 10
```

您也可以使用陣列的 **SetValue** 方法來變更值。 下列範例會將陣列 (索引位置 1) 的第二個值變更 `$a` 為500：

```powershell
$a.SetValue(500,1)
```

您可以使用 `+=` 運算子將元素加入至陣列。 下列範例顯示如何將元素加入至 `$a` 陣列。

```powershell
$a = @(0..4)
$a += 5
```

> [!NOTE]
> 當您使用 `+=` 運算子時，PowerShell 實際上會建立新的陣列，其中包含原始陣列的值和新增的值。 如果作業重複數次，或陣列的大小太大，這可能會導致效能問題。

從陣列中刪除元素並不容易，但您可以建立新的陣列，其中只包含現有陣列的選取專案。 例如，若要 `$t` 使用陣列中的所有元素（ `$a` 位於索引位置2的值除外）來建立陣列，請輸入：

```powershell
$t = $a[0,1 + 3..($a.length - 1)]
```

若要將兩個數組合並為單一陣列，請使用加號運算子 (`+`) 。 下列範例會建立兩個數組、將它們合併，然後顯示產生的組合陣列。

```powershell
$x = 1,3
$y = 5,9
$z = $x + $y
```

如此一來， `$z` 陣列會包含1、3、5和9。

若要刪除陣列，請將的值指派 `$null` 給陣列。 下列命令會刪除變數中的陣列 `$a` 。

`$a = $null`

您也可以使用指令 `Remove-Item` 程式，但指派的值 `$null` 更快，尤其是大型陣列。

## <a name="arrays-of-zero-or-one"></a>零或一的陣列

從 Windows PowerShell 3.0 開始，零或一個物件的集合會有 Count 和 Length 屬性。 此外，您也可以為一個物件的陣列編制索引。 這項功能可協助您避免在預期集合的命令到達兩個專案時所發生的腳本錯誤。

下列範例示範這項功能。

### <a name="zero-objects"></a>零物件

```powershell
$a = $null
$a.Count
$a.Length
```

```Output
0
0
```

### <a name="one-object"></a>一個物件

```powershell
$a = 4
$a.Count
$a.Length
$a[0]
$a[-1]
```

```Output
1
1
4
4
```

## <a name="indexing-support-for-systemtuple-objects"></a>系統元組物件的索引支援

PowerShell 6.1 新增了 **元組** 物件的索引存取支援，類似于陣列。
例如：

```powershell
PS> $tuple = [Tuple]::Create(1, 'test')
PS> $tuple[0]
1
PS> $tuple[1]
test
PS> $tuple[0..1]
1
test
PS> $tuple[-1]
test
```

與陣列和其他集合物件不同的是，當透過管線或支持對象陣列的參數傳遞元組物件時，會將 **元組** 物件視為單一物件。

如需詳細資訊，請參閱 [系統元組](/dotnet/api/system.tuple)。

## <a name="see-also"></a>另請參閱

- [about_Assignment_Operators](about_Assignment_Operators.md)
- [about_Hash_Tables](about_Hash_Tables.md)
- [about_Operators](about_Operators.md)
- [about_For](about_For.md)
- [about_Foreach](about_Foreach.md)
- [about_While](about_While.md)
