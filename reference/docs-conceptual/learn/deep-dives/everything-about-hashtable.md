---
title: 您想知道有關雜湊表的一切
description: 雜湊表在 PowerShell 中是極其重要的，因此務必加以充分了解。
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 1539cf6444cab718c1108384c640193d66c85daf
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2020
ms.locfileid: "93354417"
---
# <a name="everything-you-wanted-to-know-about-hashtables"></a>您想知道有關雜湊表的一切

我想要回頭討論[雜湊表][]。 現在我隨時都會使用雜湊表。 昨晚當使用者群組會議結束後，我正在教導某人有關雜湊表的資訊，我意識到自己和對方一樣對雜湊表感到困惑。 雜湊表在 PowerShell 中是極其重要的，因此務必加以充分了解。

> [!NOTE]
> 本文的[原始版本][]出現在 [@KevinMarquette][] 所撰寫的部落格中。 PowerShell 小組感謝 Kevin 與我們分享此內容。 請在 [PowerShellExplained.com][] 查看他的部落格。

## <a name="hashtable-as-a-collection-of-things"></a>雜湊表即事件集合

我想要您先將 **雜湊表** 看成雜湊表傳統定義中的集合。 此定義可讓您在稍後將其用於更進階的內容時，對其運作方式有基本的了解。 略過這項了解通常是造成困惑的來源。

## <a name="what-is-an-array"></a>什麼是陣列？

在跳到什麼是 **雜湊表** 之前，我必須先提到 [陣列][]。 基於此討論的目的，陣列是值或物件的清單或集合。

```powershell
$array = @(1,2,3,5,7,11)
```

一旦您將項目放入陣列後，就可以使用 `foreach` 來逐一查看清單，或使用索引來存取陣列中的個別元素。

```powershell
foreach($item in $array)
{
    Write-Output $item
}

Write-Output $array[3]
```

您也可以採用相同的方式，使用索引來更新值。

```powershell
$array[2] = 13
```

我只是稍微示範一下陣列，但是當我移到雜湊表時，應該將其放至正確的內容中。

## <a name="what-is-a-hashtable"></a>什麼是雜湊表？

我將先從基本的技術層面說明雜湊表是什麼，然後再轉移到 PowerShell 使用雜湊表的其他方法。

雜湊表是一種資料結構，與陣列非常相似，不同之處在於您會使用索引鍵來儲存每個值 (物件)。 其是基本的索引鍵/值存放區。 首先，我們會建立空的雜湊表。

```powershell
$ageList = @{}
```

請注意，大括號 (而不是括號) 是用來定義雜湊表。 然後，我們會使用如下的索引鍵來新增項目：

```powershell
$key = 'Kevin'
$value = 36
$ageList.add( $key, $value )

$ageList.add( 'Alex', 9 )
```

人員的名稱是索引鍵，而其年齡是我想要儲存的值。

## <a name="using-the-brackets-for-access"></a>使用大括號進行存取

一旦將您的值新增至雜湊表後，就可以使用該相同的索引鍵 (而不是使用數字索引鍵，如您對陣列所做的一般) 將其取回。

```powershell
$ageList['Kevin']
$ageList['Alex']
```

當我想要 Kevin 的年齡時，可以使用他的名稱來進行存取。 我們也可以使用這種方法，在雜湊表中新增或更新值。 這就像是使用上述的 `add()` 函式一樣。

```powershell
$ageList = @{}

$key = 'Kevin'
$value = 36
$ageList[$key] = $value

$ageList['Alex'] = 9
```

還有另一種語法，您可以用來存取及更新我在稍後章節中會討論到的值。 如果您是從另一種語言來到 PowerShell，這些範例應該符合您之前使用雜湊表的方式。

### <a name="creating-hashtables-with-values"></a>使用一些值建立雜湊表

到目前為止，我已經為這些範例建立了一個空的雜湊表。 在建立索引鍵和值時，您可以預先將其填入。

```powershell
$ageList = @{
    Kevin = 36
    Alex  = 9
}
```

### <a name="as-a-lookup-table"></a>做為查閱資料表

此雜湊表類型的實際值是您可以使用其做為查閱資料表的值。 以下是一個簡單範例。

```powershell
$environments = @{
    Prod = 'SrvProd05'
    QA   = 'SrvQA02'
    Dev  = 'SrvDev12'
}

$server = $environments[$env]
```

在此範例中，您指定 `$env` 變數的環境，而且其會挑選正確的伺服器。 您可以將 `switch($env){...}` 用於像這樣的選擇，但雜湊表是不錯的選項。

當您以動態方式建置查閱資料表以供稍後使用時，這樣做的效果更好。 因此，當您需要交叉參考時，請考慮使用這種方法。 我認為，如果 PowerShell 在管道上使用 `Where-Object` 進行篩選並不理想，我們將看到更多這種方法。 若在效能至上的情況下，就必須考慮這種方法。

我並未說其速度更快，但其符合[若效能至上，請將其進行測試][]的規則。

#### <a name="multiselection"></a>多重選擇

一般來說，您會將雜湊表視為索引鍵/值組，其中您可以提供一個索引鍵並取得一個值。 PowerShell 可讓您提供索引鍵陣列，以取得多個值。

```powershell
$environments[@('QA','DEV')]
$environments[('QA','DEV')]
$environments['QA','DEV']
```

在此範例中，我使用上述的相同查閱雜湊表，並提供三種不同的陣列樣式來取得相符項目。 這是 PowerShell 中大部分人都不知道的隱藏功能。

## <a name="iterating-hashtables"></a>逐一查看雜湊表

因為雜湊表是索引鍵/值組的集合，所以您會以不同於陣列或一般項目清單所用的方式，逐一查看此雜湊表。

首先要注意的是，如果您透過管道處理雜湊表，則管道會將其視為一個物件。

```powershell
PS> $ageList | Measure-Object
count : 1
```

即使 `.count` 屬性會告訴您其包含多少個值，也一樣。

```powershell
PS> $ageList.count
2
```

如果您只需要值，則可以使用 `.values` 屬性來解決此問題。

```powershell
PS> $ageList.values | Measure-Object -Average
Count   : 2
Average : 22.5
```

列舉索引鍵並使用索引鍵來存取值通常更有用。

```powershell
PS> $ageList.keys | ForEach-Object{
    $message = '{0} is {1} years old!' -f $_, $ageList[$_]
    Write-Output $message
}
Kevin is 36 years old
Alex is 9 years old
```

以下是搭配 `foreach(){...}` 迴圈的相同範例。

```powershell
foreach($key in $ageList.keys)
{
    $message = '{0} is {1} years old' -f $key, $ageList[$key]
    Write-Output $message
}
```

我們正在瀏覽雜湊表中的每個索引鍵，然後使用其來存取值。 當您使用雜湊表做為集合時，這是常見的模式。

### <a name="getenumerator"></a>GetEnumerator()

這會將我們帶至 `GetEnumerator()` 以逐一查看我們的雜湊表。

```powershell
$ageList.GetEnumerator() | ForEach-Object{
    $message = '{0} is {1} years old!' -f $_.key, $_.value
    Write-Output $message
}
```

列舉程式會逐一為您提供每個索引鍵/值組。 其是專為此使用案例所設計的。 感謝您光臨 [Mark Kraus](https://get-PowerShellblog.blogspot.com) 提醒我這個問題。

### <a name="badenumeration"></a>BadEnumeration

其中一個重要的細節是，您無法在列舉雜湊表時對其進行修改。 如果我們從基本 `$environments` 範例開始：

```powershell
$environments = @{
    Prod = 'SrvProd05'
    QA   = 'SrvQA02'
    Dev  = 'SrvDev12'
}
```

嘗試將每個索引鍵設定為相同的伺服器值則會失敗。

```powershell
$environments.Keys | ForEach-Object {
    $environments[$_] = 'SrvDev03'
}

An error occurred while enumerating through a collection: Collection was modified; enumeration operation may not execute.
+ CategoryInfo          : InvalidOperation: tableEnumerator:HashtableEnumerator) [], RuntimeException
+ FullyQualifiedErrorId : BadEnumeration
```

即使看起來應該很好，也會失敗：

```powershell
foreach($key in $environments.keys) {
    $environments[$key] = 'SrvDev03'
}

Collection was modified; enumeration operation may not execute.
    + CategoryInfo          : OperationStopped: (:) [], InvalidOperationException
    + FullyQualifiedErrorId : System.InvalidOperationException
```

解決這種情況的訣竅是在執行列舉之前，先複製金鑰。

```powershell
$environments.Keys.Clone() | ForEach-Object {
    $environments[$_] = 'SrvDev03'
}
```

## <a name="hashtable-as-a-collection-of-properties"></a>雜湊表即屬性集合

到目前為止，我們放在雜湊表中的物件類型都是相同類型的物件。 我已在所有這些範例中使用了年齡，而索引鍵是該人員的名稱。 當您的物件集合各有一個名稱時，這是一種很好的查看方法。 在 PowerShell 中使用雜湊表的另一個常見方式是保留屬性的集合，其中索引鍵是屬性的名稱。 在下一個範例中，我將逐步解說該概念。

### <a name="property-based-access"></a>屬性型存取

使用屬性型存取可變更雜湊表的動態，以及在 PowerShell 中使用雜湊表的方式。 以下是上述的一般範例，其會將索引鍵視為屬性。

```powershell
$ageList = @{}
$ageList.Kevin = 35
$ageList.Alex = 9
```

就像上述範例，此範例會新增這些索引鍵 (如果其尚未存在於雜湊表中)。 根據您定義金鑰的方式和您的值，這可能有點奇怪或完美符合。 到目前為止，年齡清單範例一直非常有用。 我們需要新的範例，以方便您繼續進行。

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}
```

此外，我們也可以在 `$person` 上新增和存取屬性，如下所示。

```powershell
$person.city = 'Austin'
$person.state = 'TX'
```

突然間，此雜湊表就像物件一樣地感覺和運作。 雜湊表仍然是項目的集合，因此上述所有範例仍然適用。 我們只是從另一個觀點接近雜湊表。

### <a name="checking-for-keys-and-values"></a>檢查索引鍵和值

在大部分的情況下，您可以只測試值，如下所示：

```powershell
if( $person.age ){...}
```

這很簡單，但對我而言卻是許多錯誤 (bug) 的來源，因為我在邏輯中輕忽了一個重要的細節。 我開始使用測試值來測試索引鍵是否存在。 當值為 `$false` 或零時，該陳述式會意外傳回 `$false`。

```powershell
if( $person.age -ne $null ){...}
```

這解決了零值的問題，但未解決 $null 與不存在索引鍵的問題。 在大部分的時間裡，您不需要進行這項區別，但有一些功能可在這時供您執行。

```powershell
if( $person.ContainsKey('age') ){...}
```

如果您需要在不知道索引鍵或逐一查看整個集合的情況下測試值，我們也會有 `ContainsValue()` 因應此情況。

### <a name="removing-and-clearing-keys"></a>移除和清除索引鍵

您可以使用 `.Remove()` 函式來移除索引鍵。

```powershell
$person.remove('age')
```

為其指派 `$null` 值，只是讓您擁有一個具有 `$null` 值的索引鍵。

清除雜湊表的常見方式就是將其初始化為空的雜湊表。

```powershell
$person = @{}
```

儘管可以如此運作，但請嘗試改用 `clear()` 函式。

```powershell
$person.clear()
```

這是使用函式建立自我記錄程式碼的其中一個執行個體，而且其會讓程式碼的意圖非常簡潔。

## <a name="all-the-fun-stuff"></a>所有有趣的事物

### <a name="ordered-hashtables"></a>排序的雜湊表

根據預設，雜湊表不會排序 (或已排序)。 在傳統內容中，一律使用索引鍵存取值時，順序並不重要。 建議您讓屬性保持您所定義的順序。 幸好，有一種方法可以使用 `ordered` 關鍵字來執行此動作。

```powershell
$person = [ordered]@{
    name = 'Kevin'
    age  = 36
}
```

現在，當您列舉索引鍵和值時，其會保持該順序。

### <a name="inline-hashtables"></a>內嵌雜湊表

在一行上定義雜湊表時，可以用分號區隔索引鍵/值組。

```powershell
$person = @{ name = 'kevin'; age = 36; }
```

如果您是在管道上建立它們，這會非常方便。

### <a name="custom-expressions-in-common-pipeline-commands"></a>一般管道命令中的自訂運算式

有幾個 Cmdlet 可支援使用雜湊表來建立自訂或計算屬性。 您通常會看到此屬性搭配 `Select-Object` 和 `Format-Table`。 雜湊表具有特殊語法，在完全展開時看起來就像這樣。

```powershell
$property = @{
    name = 'totalSpaceGB'
    expression = { ($_.used + $_.free) / 1GB }
}
```

`name` 就是讓 Cmdlet 標示該資料行。 `expression` 是執行的指令碼區塊，其中 `$_` 是管道上物件的值。 以下是該指令碼的運作方式：

```powershell
$drives = Get-PSDrive | Where Used
$drives | Select-Object -Properties name, $property

Name     totalSpaceGB
----     ------------
C    238.472652435303
```

我已將其放在變數中，但其可以輕鬆地以內嵌方式定義，而且您可以將 `name` 縮短為 `n`，以及將 `expression` 縮短為 `e` (當您位於其中時)。

```powershell
$drives | Select-Object -properties name, @{n='totalSpaceGB';e={($_.used + $_.free) / 1GB}}
```

我個人不喜歡製作長命令，而且其通常會促成一些我不想陷入的不良行為。 我更願意建立新的雜湊表或 `pscustomobject`，其中包含我想要的所有欄位和屬性，而不是在指令碼中使用這個方法。 但有很多程式碼會這麼做，因此我希望您注意此情況。 我稍後會談論如何建立 `pscustomobject`。

### <a name="custom-sort-expression"></a>自訂排序運算式

如果物件具有您想要依其排序的資料，就可以輕鬆排序集合。 您可以先將資料新增至物件，然後再排序，或針對 `Sort-Object` 建立自訂運算式。

```powershell
Get-ADUser | Sort-Object -Parameter @{ e={ Get-TotalSales $_.Name } }
```

在此範例中，我會取得使用者清單，並使用一些自訂 Cmdlet 來取得只針對排序的其他資訊。

#### <a name="sort-a-list-of-hashtables"></a>排序雜湊表清單

如果您有想要排序的雜湊表清單，則會發現 `Sort-Object` 不會將您的索引鍵視為屬性。 我們可以使用自訂排序運算式進行一回。

```powershell
$data = @(
    @{name='a'}
    @{name='c'}
    @{name='e'}
    @{name='f'}
    @{name='d'}
    @{name='b'}
)

$data | Sort-Object -Property @{e={$_.name}}
```

## <a name="splatting-hashtables-at-cmdlets"></a>在 Cmdlet 展開雜湊表

這是有關雜湊表其中一件我最愛的事，許多人早期並未發現。
其概念為不是在一行上將所有屬性提供給 Cmdlet，而是先將其封裝成雜湊表。 接著，您可以使用特殊方式將雜湊表提供給函式。
以下是以一般方式建立 DHCP 範圍的範例。

```powershell
Add-DhcpServerv4Scope -Name 'TestNetwork' -StartRange'10.0.0.2' -EndRange '10.0.0.254' -SubnetMask '255.255.255.0' -Description 'Network for testlab A' -LeaseDuration (New-TimeSpan -Days 8) -Type "Both"
```

不使用[展開][]，所有這些項目都必須定義在同一行上。 其會滾出畫面或換行，視其表現而定。 現在請將其與使用展開的命令進行比較。

```powershell
$DHCPScope = @{
    Name        = 'TestNetwork'
    StartRange  = '10.0.0.2'
    EndRange    = '10.0.0.254'
    SubnetMask  = '255.255.255.0'
    Description = 'Network for testlab A'
    LeaseDuration = (New-TimeSpan -Days 8)
    Type = "Both"
}
Add-DhcpServerv4Scope @DHCPScope
```

使用 `@` 符號，而不是 `$` 時，會叫用展開作業。

只需片刻就會理解閱讀該範例有多容易。 這是完全相同的命令，具有所有相同的值。 第二個更容易了解和繼續進行。

每當命令太長時，我就會使用展開。 我定義了太長的命令，導致我的視窗向右滾動。 如果我點擊函式的三個屬性，很可能會使用展開的雜湊表來重寫該函式。

### <a name="splatting-for-optional-parameters"></a>針對選擇性參數進行展開

我使用展開的其中一種最常見方式，就是處理來自我指令碼中其他位置的選擇性參數。 假設我有一個函式，包裝了 `Get-CIMInstance` 呼叫，其中具有選擇性 `$Credential` 引數。

```powershell
$CIMParams = @{
    ClassName = 'Win32_Bios'
    ComputerName = $ComputerName
}

if($Credential)
{
    $CIMParams.Credential = $Credential
}

Get-CIMInstance @CIMParams
```

首先使用常見的參數建立我的雜湊表。 接著新增 `$Credential`，如果存在的話。
因為我在這裡使用展開，所以我只需要在程式碼中呼叫 `Get-CIMInstance` 一次。 這種設計模式非常簡潔，而且可以輕鬆地處理許多選擇性參數。

為求公平，您可以撰寫命令，以允許參數的 `$null` 值。 只是您不一定能控制您所呼叫的其他命令。

### <a name="multiple-splats"></a>多個展開

您可以將多個雜湊表展開至相同的 Cmdlet。 如果我們回顧原始展開範例：

```powershell
$Common = @{
    SubnetMask  = '255.255.255.0'
    LeaseDuration = (New-TimeSpan -Days 8)
    Type = "Both"
}

$DHCPScope = @{
    Name        = 'TestNetwork'
    StartRange  = '10.0.0.2'
    EndRange    = '10.0.0.254'
    Description = 'Network for testlab A'
}

Add-DhcpServerv4Scope @DHCPScope @Common
```

當我有一組常用的參數傳遞至許多命令時，我會使用這種方法。

### <a name="splatting-for-clean-code"></a>針對全新程式碼進行展開

如果讓您的程式碼更簡潔，展開單一參數就不會有任何問題。

```powershell
$log = @{Path = '.\logfile.log'}
Add-Content "logging this command" @log
```

### <a name="splatting-executables"></a>展開可執行檔

展開也可以在使用 `/param:value` 語法的一些可執行檔上運作。 例如，`Robocopy.exe` 具有一些如下的參數。

```powershell
$robo = @{R=1;W=1;MT=8}
robocopy source destination @robo
```

我不知道這一切是否有用，但是我發現其很有趣。

## <a name="adding-hashtables"></a>新增雜湊表

雜湊表支援新增運算子以結合兩個雜湊表。

```powershell
$person += @{Zip = '78701'}
```

這只適用於兩個雜湊表不共用索引鍵的情況。

## <a name="nested-hashtables"></a>巢狀雜湊表

我們可以使用雜湊表做為雜湊表內的值。

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}
$person.location = @{}
$person.location.city = 'Austin'
$person.location.state = 'TX'
```

我一開始使用包含兩個索引鍵的基本雜湊表。 已新增名為 `location` 的索引鍵搭配空的雜湊表。 然後，將最後兩個項目新增至該 `location` 雜湊表。 我們也可以全都以內嵌方式執行此動作。

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
    location = @{
        city  = 'Austin'
        state = 'TX'
    }
}
```

這會建立我們在上面看到的同一個雜湊表，並且可以使用相同的方式來存取屬性。

```powershell
$person.location.city
Austin
```

有許多方式可以處理您物件的結構。 這裡是查看巢狀雜湊表的第二種方式。

```powershell
$people = @{
    Kevin = @{
        age  = 36
        city = 'Austin'
    }
    Alex = @{
        age  = 9
        city = 'Austin'
    }
}
```

這會混合使用雜湊表做為物件集合和屬性集合的概念。 即使用了您偏好的任何方法使這些值形成巢狀，仍然很容易加以存取。

```powershell
PS> $people.kevin.age
36
PS> $people.kevin['city']
Austin
PS> $people['Alex'].age
9
PS> $people['Alex']['City']
Austin
```

我通常會在將其視為屬性時使用點屬性。 這些一般都是我在程式碼中以靜態方式定義的項目，而且我非常了解這些項目。 如果我需要逐步執行清單或以程式設計方式存取索引鍵，則會使用括弧來提供索引鍵名稱。

```powershell
foreach($name in $people.keys)
{
    $person = $people[$name]
    '{0}, age {1}, is in {2}' -f $name, $person.age, $person.city
}
```

能夠讓雜湊表形成巢狀，可提供您許多彈性和選項。

### <a name="looking-at-nested-hashtables"></a>查看巢狀雜湊表

一旦您開始讓雜湊表形成巢狀，就需要一個簡易的方法，從主控台進行查看。 如果我採用最後一個雜湊表，就會得到如下所示的輸出，而且其只會如此的深：

```powershell
PS> $people
Name                           Value
----                           -----
Kevin                          {age, city}
Alex                           {age, city}
```

我用於查看這些項目的移至命令是 `ConvertTo-JSON`，因為其非常簡潔，而且我經常在其他項目上使用 JSON。

```powershell
PS> $people | ConvertTo-Json
{
    "Kevin":  {
                "age":  36,
                "city":  "Austin"
            },
    "Alex":  {
                "age":  9,
                "city":  "Austin"
            }
}
```

即使您不知道 JSON，還是應該能夠看到您要尋找的內容。 這類結構化資料有一個 `Format-Custom` 命令，但我仍然更喜歡使用 JSON 檢視。

## <a name="creating-objects"></a>建立物件

有時候，您只需要擁有物件，而且使用雜湊表來保留屬性，並不只是讓工作完成而已。 最常見的情況是，您想要將索引鍵視為資料行名稱。 `pscustomobject` 讓這件事變得很簡單。

```powershell
$person = [pscustomobject]@{
    name = 'Kevin'
    age  = 36
}

$person

name  age
----  ---
Kevin  36
```

即使您一開始並未將其建立為 `pscustomobject`，稍後也可以視需要將其轉換。

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}

[pscustomobject]$person

name  age
----  ---
Kevin  36
```

我已經為了 [pscustomobject][] 撰寫詳細的文章，您應該在此之後閱讀。 其係根據這裡所學到的許多東西建置的。

## <a name="reading-and-writing-hashtables-to-file"></a>讀取和寫入雜湊表至檔案

### <a name="saving-to-csv"></a>儲存至 CSV

努力將雜湊表儲存至 CSV，是我在上面提到的其中一個困難之處。 將您的雜湊表轉換成 `pscustomobject`，然後其就會正確地儲存至 CSV。 如果您從 `pscustomobject` 開始，很有幫助，因為資料行順序會保留下來。 但您可以視需要將其轉換成 `pscustomobject` 內嵌。

```powershell
$person | ForEach-Object{ [pscustomobject]$_ } | Export-CSV -Path $path
```

可以再次參閱我針對如何使用 [pscustomobject][] 撰寫的文章。

### <a name="saving-a-nested-hashtable-to-file"></a>將巢狀雜湊表儲存至檔案

如果我需要將巢狀雜湊表儲存至檔案，然後再次將其讀回，則會使用 JSON Cmdlet 來執行此動作。

```powershell
$people | ConvertTo-JSON | Set-Content -Path $path
$people = Get-Content -Path $path -Raw | ConvertFrom-JSON
```

這個方法有兩個重點。 第一個重點是 JSON 會寫出多行，因此我需要使用 `-Raw` 選項，將其讀回成單一字串。 第二個重點是匯入的物件不再是 `[hashtable]`。 現在是 `[pscustomobject]`，而且如果不是您所預期的，可能會造成問題。

注意深層巢狀雜湊表。 當您將其轉換為 JSON 時，可能不會得到您預期的結果。

```powershell
@{ a = @{ b = @{ c = @{ d = "e" }}}} | ConvertTo-Json

{
  "a": {
    "b": {
      "c": "System.Collections.Hashtable"
    }
  }
}
```

使用 **Depth** 參數以確保您已展開所有的巢狀雜湊表。

```powershell
@{ a = @{ b = @{ c = @{ d = "e" }}}} | ConvertTo-Json -Depth 3

{
  "a": {
    "b": {
      "c": {
        "d": "e"
      }
    }
  }
}
```

如果您需要其在匯入時成為 `[hashtable]`，則必須使用 `Export-CliXml` 和 `Import-CliXml` 命令。

### <a name="converting-json-to-hashtable"></a>將 JSON 轉換成雜湊表

如果您需要將 JSON 轉換成 `[hashtable]`，我知道有一種方法，可以利用 .NET 中的 [JavaScriptSerializer][] 來執行此動作。

```powershell
[Reflection.Assembly]::LoadWithPartialName("System.Web.Script.Serialization")
$JSSerializer = [System.Web.Script.Serialization.JavaScriptSerializer]::new()
$JSSerializer.Deserialize($json,'Hashtable')
```

從 PowerShell v6 開始，JSON 支援會使用 NewtonSoft JSON.NET 並加入雜湊表支援。

```powershell
'{ "a": "b" }' | ConvertFrom-Json -AsHashtable

Name      Value
----      -----
a         b
```

PowerShell 6.2 已將 **Depth** 參數新增至 `ConvertFrom-Json`。 預設 **Depth** 為1024。

### <a name="reading-directly-from-a-file"></a>直接從檔案讀取

如果您有一個檔案包含一個使用 PowerShell 語法的雜湊表，則有一種可以直接將其匯入的方式。

```powershell
$content = Get-Content -Path $Path -Raw -ErrorAction Stop
$scriptBlock = [scriptblock]::Create( $content )
$scriptBlock.CheckRestrictedLanguage( $allowedCommands, $allowedVariables, $true )
$hashtable = ( & $scriptBlock )
```

其會將檔案的內容匯入至 `scriptblock`，然後在執行其之前，檢查以確定其中沒有任何其他 PowerShell 命令。

關於這一點，您知道模組資訊清單 (.psd1 檔案) 只是雜湊表嗎？

## <a name="keys-can-be-any-object"></a>索引鍵可以是任何物件

在大部分的時候，索引鍵只是字串。 因此，我們可以在任何項目前後加上引號，使其成為索引鍵。

```powershell
$person = @{
    'full name' = 'Kevin Marquette'
    '#' = 3978
}
$person['full name']
```

您可以做到一些可能沒有意識到可以做到的事情。

```powershell
$person.'full name'

$key = 'full name'
$person.$key
```

這是因為您可以做到一些事情，這並不表示您應該這麼做。 最後一個看起來就像是等待發生的錯誤 (bug)，這讓讀取您程式碼的任何人很容易產生誤解。

從技術上來說，您的索引鍵不一定是字串，但如果您只使用字串，就比較容易思考。 不過，索引編製並不適用於複雜索引鍵。

```powershell
$ht = @{ @(1,2,3) = "a" }
$ht

Name                           Value
----                           -----
{1, 2, 3}                      a
```

依索引鍵存取雜湊表中的值不一定會有作用。 例如：

```powershell
$key = $ht.keys[0]
$ht.$($key)
a
$ht[$key]
a
```

當索引鍵是陣列時，即必須將 `$key` 變數包裝在子運算式中，使其可與成員存取 (`.`) 標記法搭配使用。 或者，您也可使用陣列索引 (`[]`) 標記法。

## <a name="use-in-automatic-variables"></a>用於自動變數

### <a name="psboundparameters"></a>$PSBoundParameters

[$PSBoundParameters][] 是只存在於函式內容中的自動變數。
其包含呼叫函數時搭配的所有參數。 這不是真正的雜湊表，但是足以讓您將其等同視之。

其中包括移除索引鍵，並將其展開至其他函式。 如果您發現自己撰寫的是 Proxy 函式，請仔細查看一下。

如需其他詳細資料，請參閱 [about_Automatic_Variables][]。

### <a name="psboundparameters-gotcha"></a>PSBoundParameters 陷阱

要記住的一個重點是，這只包含當做參數傳入的值。 如果您也有具有預設值的參數，但呼叫者未將其傳入，則 `$PSBoundParameters` 不會包含這些值。 這通常會被輕忽掉。

### <a name="psdefaultparametervalues"></a>$PSDefaultParameterValues

這個自動變數可讓您將預設值指派給任何 Cmdlet，而無需變更 Cmdlet。
請看一下這個範例。

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "UTF8"
```

這會新增一個項目至 `$PSDefaultParameterValues` 雜湊表，將 `UTF8` 設定為 `Out-File -Encoding` 參數的預設值。 這是工作階段特有的，因此應該將其置於您的 `$profile` 中。

我經常使用這個來預先指派我經常輸入的值。

```powershell
$PSDefaultParameterValues[ "Connect-VIServer:Server" ] = 'VCENTER01.contoso.local'
```

這也會接受萬用字元，讓您可以大量設定這些值。 以下是一些您可以使用的方法：

```powershell
$PSDefaultParameterValues[ "Get-*:Verbose" ] = $true
$PSDefaultParameterValues[ "*:Credential" ] = Get-Credential
```

如需更深入的明細，請參閱由 [Michael Sorens][] 撰寫的[自動預設值][]，這是一篇絕佳的文章。

## <a name="regex-matches"></a>Regex $Matches

使用 `-match` 運算子時，會使用比對的結果來建立稱為 `$matches` 的自動變數。 如果您的規則運算式中有任何子運算式，也會列出那些子比對。

```powershell
$message = 'My SSN is 123-45-6789.'

$message -match 'My SSN is (.+)\.'
$Matches[0]
$Matches[1]
```

### <a name="named-matches"></a>具名比對

這是我最愛的其中一項功能，大部分人都不知道。 如果您使用具名規則運算式比對，則可以依據比對上的名稱來存取該比對。

```powershell
$message = 'My Name is Kevin and my SSN is 123-45-6789.'

if($message -match 'My Name is (?<Name>.+) and my SSN is (?<SSN>.+)\.')
{
    $Matches.Name
    $Matches.SSN
}
```

在上述範例中，`(?<Name>.*)` 是具名子運算式。 此值接著會放置在 `$Matches.Name` 屬性中。

## <a name="group-object--ashashtable"></a>Group-Object -AsHashtable

少有人知的 `Group-Object` 功能，其可以為您將某些資料集變成雜湊表。

```powershell
Import-CSV $Path | Group-Object -AsHashtable -Property email
```

這會將每個資料列加入雜湊表中，並使用指定的屬性做為存取其的索引鍵。

## <a name="copying-hashtables"></a>複製雜湊表

要知道的一個重點是，雜湊表是物件。 此外，每個變數只是物件的參考。 這表示需要更多工作，才能建立雜湊表的有效複本。

### <a name="assigning-reference-types"></a>指派參考型別

當您有一個雜湊表並將其指派給第二個變數時，這兩個變數都會指向相同的雜湊表。

```powershell
PS> $orig = @{name='orig'}
PS> $copy = $orig
PS> $copy.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.name
PS> 'Orig: [{0}]' -f $orig.name

Copy: [copy]
Orig: [copy]
```

這強調這些雜湊表是相同的，因為變更其中一個變數的值時，也會變更另一個變數中的值。 這也適用於將雜湊表傳遞至其他函式時。 如果這些函式對該雜湊表進行變更，您的原始雜湊表也會變更。

### <a name="shallow-copies-single-level"></a>淺層複製，單層

如果我們有像上述範例的簡單雜湊表，則可以使用 `.Clone()` 來進行淺層複製。

```powershell
PS> $orig = @{name='orig'}
PS> $copy = $orig.Clone()
PS> $copy.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.name
PS> 'Orig: [{0}]' -f $orig.name

Copy: [copy]
Orig: [orig]
```

這可讓我們對某個雜湊表進行一些不會影響另一個雜湊表的基本變更。

### <a name="shallow-copies-nested"></a>淺層複製，巢狀

為何稱為淺層複製的原因是其只會複製基層屬性。 如果其中一個屬性是參考型別 (例如另一個雜湊表)，則這些巢狀物件仍會指向彼此。

```powershell
PS> $orig = @{
        person=@{
            name='orig'
        }
    }
PS> $copy = $orig.Clone()
PS> $copy.person.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.person.name
PS> 'Orig: [{0}]' -f $orig.person.name

Copy: [copy]
Orig: [copy]
```

因此，您可以看到，即使我複製了雜湊表，也不會複製 `person` 的參考。 我們需要進行深層複製，才能真正具有未連結到第一個雜湊表的第二個雜湊表。

### <a name="deep-copies"></a>深層複製

在撰寫本文時，我並不知道只要深層複製雜湊表 (並將其保留為雜湊表)，是一種聰明的方式。 這只是某人需要撰寫的其中一件事。
以下是執行此動作的快速方法。

```powershell
function Get-DeepClone
{
    [CmdletBinding()]
    param(
        $InputObject
    )
    process
    {
        if($InputObject -is [hashtable]) {
            $clone = @{}
            foreach($key in $InputObject.keys)
            {
                $clone[$key] = Get-DeepClone $InputObject[$key]
            }
            return $clone
        } else {
            return $InputObject
        }
    }
}
```

其不會處理任何其他參考型別或陣列，但這是很好的起點。

## <a name="anything-else"></a>任何其他項目？

我很快涵蓋了許多基礎的東西。 我希望您可以走出去學習新的事物，或在每次閱讀時有更深的領悟。 因為我涵蓋了這項功能的完整範疇，所以目前可能會有一些層面不適用於您。 這完全沒問題，而且是預期的情況，視您使用 PowerShell 的程度而定。

<!-- link references -->
[原始版本]: https://powershellexplained.com/2016-11-06-powershell-hashtable-everything-you-wanted-to-know-about/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[雜湊表]: /powershell/module/microsoft.powershell.core/about/about_hash_tables
[陣列]: /powershell/module/microsoft.powershell.core/about/about_arrays
[若效能至上，請將其進行測試]: https://github.com/PoshCode/PowerShellPracticeAndStyle/blob/master/Best-Practices/Performance.md
[展開]: /powershell/module/microsoft.powershell.core/about/about_splatting
[pscustomobject]: everything-about-pscustomobject.md
[JavaScriptSerializer]: /dotnet/api/system.web.script.serialization.javascriptserializer?view=netframework-4.8&preserve-view=true
[PSBoundParameters]: https://tommymaynard.com/the-psboundparameters-automatic-variable-2016/
[about_Automatic_Variables]: /powershell/module/microsoft.powershell.core/about/about_automatic_variables
[自動預設值]: https://www.simple-talk.com/sysadmin/PowerShell/PowerShell-time-saver-automatic-defaults/
[Michael Sorens]: http://cleancode.sourceforge.net/wwwdoc/about.html
