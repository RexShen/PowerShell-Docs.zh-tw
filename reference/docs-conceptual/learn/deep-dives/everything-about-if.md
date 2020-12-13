---
title: If 陳述式的完整說明
description: 就像許多其他語言一樣，PowerShell 提供的陳述式也可讓您在指令碼中按條件執行程式碼。
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: b6bafb99bfb8ecd0152bae841e5c58d4c27ccd3e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "86469747"
---
# <a name="everything-you-wanted-to-know-about-the-if-statement"></a>`if` 陳述式的完整說明

就像許多其他語言一樣，PowerShell 提供的陳述式也可讓您在指令碼中按條件執行程式碼。 其中一個陳述式就是 [If][] 陳述式。 今天，我們將深入探討 PowerShell 其中一個最基本的命令。

> [!NOTE]
> [原文][]出自 [@KevinMarquette][] 所撰寫的部落格。 PowerShell 小組感謝 Kevin 分享此內容。 請前往 [PowerShellExplained.com][] 瀏覽他的部落格。

## <a name="conditional-execution"></a>條件式執行

您的指令碼經常必須做出決策，並根據這些決策執行不同的邏輯。
這就是我所謂的條件式執行。 您可以使用一個陳述式或值來進行評估，然後根據該評估結果執行不同的程式碼區段。 這就是 `if` 陳述式的功能所在。

## <a name="the-if-statement"></a>`if` 陳述式

以下是 `if` 陳述式的基本範例：

```powershell
$condition = $true
if ( $condition )
{
    Write-Output "The condition was true"
}
```

`if` 陳述式會先評估括弧中的運算式。 若評估為 `$true`，就會執行大括弧中的 `scriptblock`。 若值為 `$false`，就會略過該指令碼區塊。

在上述範例中，`if` 陳述式只評估 `$condition` 變數。 結果是 `$true`，因此會在指令碼區塊內執行 `Write-Output` 命令。

在某些語言中，您可以將任何一行程式碼置於 `if` 陳述式後方，就會執行該程式碼。 但 PowerShell 的情況並非如此。 您必須提供完整的 `scriptblock` 並加上大括弧，才能正確運作。

## <a name="comparison-operators"></a>比較運算子

`if` 陳述式最常見的用法是用來將兩個項目互相比較。 PowerShell 提供特殊運算子以用於不同的比較案例。 當您使用比較運算子時，其會比較左側的值和右側的值。

### <a name="-eq-for-equality"></a>-eq 表示相等

`-eq` 會對兩個值進行相等檢查，以確保兩者相等。

```powershell
$value = Get-MysteryValue
if ( 5 -eq $value )
{
    # do something
}
```

在這個範例中，我用已知的 `5` 值來比較我的 `$value`，以查看兩者是否相符。

其中一個可能的使用案例是先檢查值的狀態，然後再對其採取動作。 您可以取得某個服務，並確認其為執行狀態，然後呼叫 `Restart-Service`。

C# 等其他語言常會使用 `==` 來表示相等 (例如 `5 == $value`)，但 PowerShell 不適用此方法。 另一個常見的錯誤是使用專門用來指派值給變數的等號 (例如 `5 = $value`)。 此外，將已知值放在左側，這會造成更可怕的錯誤。

這個運算子 (和其他運算子) 有一些變化。

- `-eq` 等於 (不區分大小寫)
- `-ieq` 等於 (不區分大小寫)
- `-ceq` 等於 (區分大小寫)

### <a name="-ne-not-equal"></a>-ne 不等於

許多運算子都有作用相反 (檢查相反結果) 的相關運算子。 `-ne` 可確認值不相等。

```powershell
if ( 5 -ne $value )
{
    # do something
}
```

您可以使用此項目來確保只有當值不是 `5` 時才會執行動作。 良好的使用案例是在您嘗試啟動服務之前，先檢查其是否處於執行中狀態。

**變化：**

- `-ne` 不等於 (不區分大小寫)
- `-ine` 不等於 (不區分大小寫)
- `-cne` 不等於 (區分大小寫)

這些是 `-eq` 的反向變化。 當我列出其他運算子的變化時，會將這些類型整理在一起。

### <a name="-gt--ge--lt--le-for-greater-than-or-less-than"></a>-gt -ge -lt -le 表示大於或小於

這些運算子可用來檢查值是否大於或小於另一個值。
`-gt -ge -lt -le` 代表 GreaterThan、GreaterThanOrEqual、LessThan 和 LessThanOrEqual。

```powershell
if ( $value -gt 5 )
{
    # do something
}
```

**變化：**

- `-gt` 大於
- `-igt` 大於 (不區分大小寫)
- `-cgt` 大於 (區分大小寫)
- `-ge` 大於或等於
- `-ige` 大於或等於 (不區分大小寫)
- `-cge` 大於或等於 (區分大小寫)
- `-lt` 小於
- `-ilt` 小於 (不區分大小寫)
- `-clt` 小於 (區分大小寫)
- `-le` 小於或等於
- `-ile` 小於或等於 (不區分大小寫)
- `-cle` 小於或等於 (區分大小寫)

我不知道這些運算子為何要有區分大小寫和不區分大小寫的選項。

### <a name="-like-wildcard-matches"></a>-like 萬用字元比對

PowerShell 有自己的萬用字元模式比對語法，可讓您搭配 `-like` 運算子使用。 這些萬用字元模式都很基本。

- `?` 比對任何單一字元
- `*` 比對任何字元數

```powershell
$value = 'S-ATX-SQL01'
if ( $value -like 'S-*-SQL??')
{
    # do something
}
```

請務必注意，模式會比對整個字串。 若您要比對字串中的某個項目，則必須將 `*` 放在字串的兩端。

```powershell
$value = 'S-ATX-SQL02'
if ( $value -like '*SQL*')
{
    # do something
}
```

**變化：**

- `-like` 萬用字元 (不區分大小寫)
- `-ilike` 萬用字元 (不區分大小寫)
- `-clike` 萬用字元 (區分大小寫)
- `-notlike` 萬用字元不相符 (不區分大小寫)
- `-inotlike` 萬用字元不相符 (不區分大小寫)
- `-cnotlike` 萬用字元不相符 (區分大小寫)

### <a name="-match-regular-expression"></a>-match 規則運算式

`-match` 運算子可讓您檢查字串以進行規則運算式比對。 若萬用字元模式不夠靈活時，您就可以使用這個運算子。

```powershell
$value = 'S-ATX-SQL01'
if ( $value -match 'S-\w\w\w-SQL\d\d')
{
    # do something
}
```

Regex 模式預設會比對字串中的任何位置。 因此，您可以指定要比對的子字串，如下所示：

```powershell
$value = 'S-ATX-SQL01'
if ( $value -match 'SQL')
{
    # do something
}
```

Regex 是一種複雜的語言，很值得進一步了解。 我在另一篇文章有詳細說明 `-match` 以及 [使用 RegEx 的許多方式][]。

**變化：**

- `-match` Regex (不區分大小寫)
- `-imatch` Regex (不區分大小寫)
- `-cmatch` Regex (區分大小寫)
- `-notmatch` Regex 不相符 (不區分大小寫)
- `-inotmatch` Regex 不相符 (不區分大小寫)
- `-cnotmatch` Regex 不相符 (區分大小寫)

### <a name="-is-of-type"></a>-is 類型

您可以使用 `-is` 運算子來檢查值的類型。

```powershell
if ( $value -is [string] )
{
    # do something
}
```

若您使用類別或透過管線接受各種物件，則可以使用這個運算子。 您可以輸入服務或服務名稱， 然後檢查您是否有服務；若您只有名稱，請擷取服務。

```powershell
if ( $Service -isnot [System.ServiceProcess.ServiceController] )
{
    $Service = Get-Service -Name $Service
}
```

**變化：**

- `-is` 某種類型
- `-isnot` 非某種類型

## <a name="collection-operators"></a>集合運算子

當您使用先前的運算子搭配單一值時，結果會是 `$true` 或 `$false`。 使用集合時的處理方式稍有不同。 運算子會評估集合中的每個項目，並傳回評估為 `$true` 的每一個值。

```powershell
PS> 1,2,3,4 -eq 3
3
```

這仍可在 `if` 陳述式中正常運作。 因此，運算子會傳回值，而整個陳述式為 `$true`。

```powershell
$array = 1..6
if ( $array -gt 3 )
{
    # do something
}
```

但這裡有個魔鬼藏在細節中，我必須明確指出來。以這種方式使用 `-ne` 運算子時，很容易不小心回溯檢查邏輯。 若集合中的任何項目不符合您的值，則搭配使用 `-ne` 與集合時會傳回 `$true`。

```powershell
PS> 1,2,3 -ne 4
1
2
3
```

這很容易讓人中招，所以我們可以使用 `-contains` 和 `-in` 運算子更有效率地處理這種情況。 而且 `-notcontains` 會如您預期般執行。

### <a name="-contains"></a>-contains

`-contains` 運算子會檢查集合中的值。 一旦找到相符的結果，就會傳回 `$true`。

```powershell
$array = 1..6
if ( $array -contains 3 )
{
    # do something
}
```

這個慣用方法可查看集合是否包含您的值。 若您使用 `Where-Object` (或 `-eq`)，則每次都會跑完整份清單，速度會明顯變慢。

**變化：**

- `-contains` 相符 (不區分大小寫)
- `-icontains` 相符 (不區分大小寫)
- `-ccontains` 相符 (區分大小寫)
- `-notcontains` 不相符 (不區分大小寫)
- `-inotcontains` 不相符 (不區分大小寫)
- `-cnotcontains` 不相符 (區分大小寫)

### <a name="-in"></a>-in

`-in` 運算子跟 `-contains` 運算子一樣，差別是其集合在右側。

```powershell
$array = 1..6
if ( 3 -in $array )
{
    # do something
}
```

**變化：**

- `-in` 相符 (不區分大小寫)
- `-iin` 相符 (不區分大小寫)
- `-cin` 相符 (區分大小寫)
- `-notin` 不相符 (不區分大小寫)
- `-inotin` 不相符 (不區分大小寫)
- `-cnotin` 不相符 (區分大小寫)

## <a name="logical-operators"></a>邏輯運算子

邏輯運算子可用來反轉或結合其他運算式。

### <a name="-not"></a>-not

`-not` 運算子會將運算式從 `$false` 翻轉為 `$true`，或從 `$true` 翻轉為 `$false`。 下列是我們想要在 `Test-Path` 為 `$false` 時執行動作的範例。

```powershell
if ( -not ( Test-Path -Path $path ) )
```

我們剛提到的大部分運算子都有變化，因此您不需要使用 `-not` 運算子， 但這個運算子仍有派上用場的時候。

### <a name="-operator"></a>! ! 運算子之後

您可以使用 `!` 作為 `-not` 的別名。

```powershell
if ( -not $value ){}
if ( !$value ){}
```

慣用 C# 等其他語言的使用者較常使用 `!`。 我偏好把整個運算子打出來，不然我在快速查看指令碼時很容易漏看。

### <a name="-and"></a>-and

您可以將運算式與 `-and` 運算子結合。 當您這麼做時，兩側都必須為 `$true`，整個運算式才能為 `$true`。

```powershell
if ( ($age -gt 13) -and ($age -lt 55) )
```

在該範例中，`$age` 左側必須大於等於 13 歲，右側則小於 55 歲。 為了讓這個範例更一目了然，我新增了額外的括弧；只要運算式很精簡，您就可以自行選擇是否使用這些括弧。 以下是不使用括弧的相同範例。

```powershell
if ( $age -gt 13 -and $age -lt 55 )
```

評估會由左至右進行。 若第一個項目評估為 `$false`，運算式就會提早結束，而無法執行正確的比較。 當您需要先確定值存在，然後再使用該值時，這會很方便。 例如，若您提供 `$null` 路徑給 `Test-Path`，就會擲回錯誤。

```powershell
if ( $null -ne $path -and (Test-Path -Path $path) )
```

### <a name="-or"></a>-or

`-or` 可讓您指定兩個運算式，並在其中一個是 `$true` 時傳回 `$true`。

```powershell
if ( $age -le 13 -or $age -ge 55 )
```

如同使用 `-and` 運算子一樣，評估會由左至右進行。 差異在於，若第一個部分為 `$true`，整個陳述式就是 `$true`；運算式的其餘部分都不會再處理。

另請注意這些運算子的語法運作方式： 您需要兩個不同的運算式。 我看過有些使用者寫出類似 `$value -eq 5 -or 6` 的運算式，而沒發現自己犯了錯。

### <a name="-xor-exclusive-or"></a>-xor 互斥 or

這個運算子比較不一樣。 `-xor` 只允許一個運算式評估為 `$true`。 因此，若這兩個項目都是 `$false`，或這兩個項目都是 `$true`，則整個運算式都是 `$false`。 換句話說，只有當運算式的結果不同時，運算式才是 `$true`。

大概沒什麼人會想用這個邏輯運算子，連我都想不出有什麼好的使用範例可以分享。

## <a name="bitwise-operators"></a>位元運算子

位元運算子會在值當中的位元上執行計算，並產生新的值作為結果。 這篇文章不會教大家[位元運算子][]，但以下為清單。

- `-band` 二進位 AND
- `-bor` 二進位 OR
- `-bxor` 二進位互斥 OR
- `-bnot` 二進位 NOT
- `-shl` 左移
- `-shr` 右移

## <a name="powershell-expressions"></a>PowerShell 運算式

我們可以在條件陳述式中使用一般 PowerShell。

```powershell
if ( Test-Path -Path $Path )
```

`Test-Path` 會在執行時傳回 `$true` 或 `$false`。 這也適用於會傳回其他值的命令。

```powershell
if ( Get-Process Notepad* )
```

若有傳回處理序，運算式會評估為 `$true`；若什麼都沒有，則為 `$false`。 使用管線運算式或其他 PowerShell 陳述式也完全有效，如下所示：

```powershell
if ( Get-Process | Where Name -eq Notepad )
```

這些運算式可以使用 `-and` 和 `-or` 運算子彼此結合，但您可能必須使用括弧將其分割成子運算式。

```powershell
if ( (Get-Process) -and (Get-Service) )
```

### <a name="checking-for-null"></a>檢查 $null

`if` 陳述式會將無結果或 `$null` 值評估為 `$false`。 如要特別檢查 `$null`，最佳做法是將 `$null` 放在左側。

```powershell
if ( $null -eq $value )
```

在 PowerShell 中處理 `$null` 值時，有幾個細微的差異。 若您想深入了解，可以參閱我寫的 [$null 的完整說明][]一文。

### <a name="variable-assignment"></a>變數指派

我差點忘了要納入這個項目，幸好 [Prasoon Karunan V][] 提醒我。

```powershell
if ($process=Get-Process notepad -ErrorAction ignore) {$process} else {$false}
```

一般來說，當您指派值給變數時，並不會將值傳遞給管線或主控台。 但當您在子運算式中指派變數時，變數卻會傳遞給管線。

```powershell
PS> $first = 1
PS> ($second = 2)
2
```

您知道為什麼 `$first` 指派沒有輸出，而 `$second` 指派卻有嗎？ 在 `if` 陳述式中進行指派時，其執行方式就如同上述的 `$second` 指派。 以下是簡潔的使用範例：

```powershell
if ( $process = Get-Process Notepad* )
{
    $process | Stop-Process
}
```

若將值指派給 `$process`，陳述式為 `$true`，且 `$process` 會停止。

請注意不要將這個項目與 `-eq` 混淆，因為這不是相等檢查。 這項功能比較含糊不清，因此大多數人都做不到。

## <a name="alternate-execution-path"></a>替代執行路徑

`if` 陳述式不只可讓您指定陳述式為 `$true` 時的動作，也可讓您指定陳述式為 `$false` 時的動作。 這時，`else` 陳述式就派上用場了。

### <a name="else"></a>else

使用 `else` 陳述式時，其一律是 `if` 陳述式的最後一部分。

```powershell
if ( Test-Path -Path $Path -PathType Leaf )
{
    Move-Item -Path $Path -Destination $archivePath
}
else
{
    Write-Warning "$path doesn't exist or isn't a file."
}
```

在此範例中，我們要檢查 `$path` 以確定其為一個檔案。 若找到檔案，我們就將其移動位置。 若找不到，我們就撰寫一則警告。 這種類型的分支邏輯相當普遍。

### <a name="nested-if"></a>巢狀 if

`if` 和 `else` 陳述式接受指令碼區塊，因此我們可以將任何 PowerShell 命令放在其中，包括其他 `if` 陳述式。 這可讓您使用更複雜的邏輯。

```powershell
if ( Test-Path -Path $Path -PathType Leaf )
{
    Move-Item -Path $Path -Destination $archivePath
}
else
{
    if ( Test-Path -Path $Path )
    {
        Write-Warning "A file was required but a directory was found instead."
    }
    else
    {
        Write-Warning "$path could not be found."
    }
}
```

在此範例中，我們會先測試理想路徑，然後對其採取動作。 若失敗，我們會進行其他檢查，並提供詳細資訊給使用者。

### <a name="elseif"></a>elseif

我們的作業並不限於單一條件式檢查， 因此我們可以將 `if` 和 `else` 陳述式鏈結在一起，而不使用 `elseif` 陳述式來進行巢狀。

```powershell
if ( Test-Path -Path $Path -PathType Leaf )
{
    Move-Item -Path $Path -Destination $archivePath
}
elseif ( Test-Path -Path $Path )
{
    Write-Warning "A file was required but a directory was found instead."
}
else
{
    Write-Warning "$path could not be found."
}
```

執行順序是由上到下。 因此會評估最上面的 `if` 陳述式。 若是 `$false`，則會向下移動到清單的下一個 `elseif` 或 `else`。 若沒有其他陳述式傳回 `$true`，最後一個 `else` 就是會採取的預設動作。

### <a name="switch"></a>參數

現在，我要來說明 `switch` 陳述式。 此陳述式提供的替代語法可多次比較某個值。 使用 `switch` 時，您可以指定運算式，而結果會與數個不同的值進行比較。 若其中一個值相符，則會執行相符的程式碼區塊。 請看一下這個範例：

```powershell
$itemType = 'Role'
switch ( $itemType )
{
    'Component'
    {
        'is a component'
    }
    'Role'
    {
        'is a role'
    }
    'Location'
    {
        'is a location'
    }
}
```

有三個可能的值符合 `$itemType`。 在此情況下，其會與 `Role` 進行比對。 這只是一個簡單的範例，讓您看一下 `switch` 運算子的用法。 我在另一篇 [Switch 陳述式的完整說明][]文章中會專門介紹。

## <a name="pipeline"></a>管線

管線是 PowerShell 的獨特重要功能。 未隱藏或未指派給變數的任何值都會放在管線中。 `if` 提供的方法，可讓我們透過較隱密的方式利用管線。

```powershell
$discount = if ( $age -ge 55 )
{
    Get-SeniorDiscount
}
elseif ( $age -le 13 )
{
    Get-ChildDiscount
}
else
{
    0.00
}
```

每個指令碼區塊都會將結果、命令或值放入管線中， 然後再將 `if` 陳述式的結果指派給 `$discount` 變數。 此範例可以輕鬆地將這些值直接指派給每個指令碼區塊中的 `$discount` 變數。 說實話，我不常這樣搭配使用 `if` 陳述式，但我最近確實有這麼一個使用範例。

### <a name="array-inline"></a>陣列內嵌

假設我有個名為 [Invoke-SnowSql][] 的函式，其會使用數個命令列引數來啟動可執行檔。 以下是該函式的片段，其中我會建置引數陣列。

```powershell
$snowSqlParam = @(
    '--accountname', $Endpoint
    '--username', $Credential.UserName
    '--option', 'exit_on_error=true'
    '--option', 'output_format=csv'
    '--option', 'friendly=false'
    '--option', 'timing=false'
    if ($Debug)
    {
        '--option', 'log_level=DEBUG'
    }
    if ($Path)
    {
        '--filename', $Path
    }
    else
    {
        '--query', $singleLineQuery
    }
)
```

`$Debug` 和 `$Path` 變數是終端使用者提供的函式參數。
在陣列的初始化中，我以內嵌方式評估這些項目。 若 `$Debug` 為 true，則這些值會落在正確位置的 `$snowSqlParam` 中。 `$Path` 變數也是如此。

## <a name="simplify-complex-operations"></a>簡化複雜的作業

有時候，當要檢查的比較項目太多時，`If` 陳述式會從畫面右側一路跑到底。

```powershell
$user = Get-ADUser -Identity $UserName
if ( $null -ne $user -and $user.Department -eq 'Finance' -and $user.Title -match 'Senior' -and $user.HomeDrive -notlike '\\server\*' )
{
    # Do Something
}
```

這會導致難以閱讀，您也更容易犯錯。 我們可以用幾個方法來改善情況。

### <a name="line-continuation"></a>行接續

PowerShell 中有一些運算子可讓您將命令換行。 若您想要將運算式分成多行，就非常適合使用 `-and` 和 `-or` 邏輯運算子。

```powershell
if ($null -ne $user -and
    $user.Department -eq 'Finance' -and
    $user.Title -match 'Senior' -and
    $user.HomeDrive -notlike '\\server\*'
)
{
    # Do Something
}
```

雖然要看的東西還是很多，但將每個項目分開獨立一行，視覺感完全不一樣。
一般來說，當我進行兩個以上的項目比較時，或必須向右捲動才能讀取任何邏輯時，我都會使用這個方法。

### <a name="pre-calculating-results"></a>預先計算結果

我們可將上面的陳述式從 `if` 陳述式中獨立出來，並只檢查結果。

```powershell
$needsSecureHomeDrive = $null -ne $user -and
    $user.Department -eq 'Finance' -and
    $user.Title -match 'Senior' -and
    $user.HomeDrive -notlike '\\server\*'

if ( $needsSecureHomeDrive )
{
    # Do Something
}
```

這種方式比上一個範例更加一目了然。 您也可以使用變數名稱來明確說明要檢查的內容。 這也是一個用來儲存非必要註解的自編程式碼範例。

### <a name="multiple-if-statements"></a>多個 if 陳述式

我們可以範例分成多個陳述式，並逐一檢查。 在這個案例中，我們會使用旗標或追蹤變數來合併結果。

```powershell

$skipUser = $false

if( $null -eq $user )
{
    $skipUser = $true
}

if( $user.Department -ne 'Finance' )
{
    Write-Verbose "isn't in Finance department"
    $skipUser = $true
}

if( $user.Title -match 'Senior' )
{
    Write-Verbose "Doesn't have Senior title"
    $skipUser = $true
}

if( $user.HomeDrive -like '\\server\*' )
{
    Write-Verbose "Home drive already configured"
    $skipUser = $true
}

if ( -not $skipUser )
{
    # do something
}
```

我必須反轉邏輯，讓旗標邏輯能夠正確運作。 每項評估都是個別的 `if` 陳述式。 這麼做的優點是您可以在偵錯時明確看出邏輯的運作方式。 我也可以同時提升詳細程度。

這種做法有個明顯的缺點，就是要寫的程式碼太多了。 若您把程式碼用逐行邏輯呈現，並分解成 25 行或更多行，看起來就比較複雜。

### <a name="using-functions"></a>使用函式

我們也可以將所有驗證邏輯移至函式中。 這樣看起來就清爽多了。

```powershell
if ( Test-SecureDriveConfiguration -ADUser $user )
{
    # do something
}
```

雖然您仍必須建立函式來進行驗證，但這麼做讓這段程式碼更易於使用， 您也可以更輕鬆測試這段程式碼。 在測試中，您可以模擬對 `Test-ADDriveConfiguration` 的呼叫，並只需要對此函式進行兩項測試。 其中一個會傳回 `$true`，另一個則傳回 `$false`。 另一個函式很小，因此更容易測試。

該函式的主體仍可以是我們一開始使用的一行程式碼，或是我們在上一節中使用的分解邏輯。 兩種案例都適用於這種做法，並可讓您稍後更輕鬆地變更該實作。

## <a name="error-handling"></a>錯誤處理

`if` 陳述式的其中一個重要用法是在發生錯誤之前，先檢查是否有錯誤條件。 舉例來說，我們可以在嘗試建立資料夾之前，先檢查資料夾是否已經存在。

```powershell
if ( -not (Test-Path -Path $folder) )
{
    New-Item -Type Directory -Path $folder
}
```

我必須提醒一點，如果例外狀況是您能預期得到的，就不是真正的例外狀況。 因此，請檢查您的值，並盡量驗證條件。

若您想要深入了解實際的例外狀況處理方式，可以參閱我寫的[例外狀況的完整說明][]一文。

## <a name="final-words"></a>結論

`if` 陳述式是非常簡單的陳述式，但卻是 PowerShell 的基礎。 幾乎在您撰寫的每個指令碼中，都會多次使用這個陳述式。 希望您對相關內容有更清楚的了解。

<!-- link references -->
[原文]: https://powershellexplained.com/2019-08-11-Powershell-if-then-else-equals-operator/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[if]: /powershell/module/microsoft.powershell.core/about/about_if
[位元運算子]: /powershell/module/microsoft.powershell.core/about/about_arithmetic_operators#bitwise-operators
[使用 RegEx 的許多方式]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/
[例外狀況的完整說明]: everything-about-exceptions.md
[$null 的完整說明]: everything-about-null.md
[Prasoon Karunan V]: https://twitter.com/prasoonkarunan
[Switch 陳述式的完整說明]: everything-about-switch.md
[Invoke-SnowSql]: https://github.com/loanDepot/SnowSQL/blob/a3731b52e4ab4ecb503fb81e2d8cb131e8f90410/SnowSQL/public/Invoke-SnowSql.ps1#L90
