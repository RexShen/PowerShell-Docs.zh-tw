---
title: 您想知道有關 PSCustomObject 的一切
description: PSCustomObject 可讓您用簡單的方法來建立結構化資料。
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: fbc8b5b6d2cfafaa75fa820f420762a1804074ac
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149491"
---
# <a name="everything-you-wanted-to-know-about-pscustomobject"></a>您想知道有關 PSCustomObject 的一切

`PSCustomObject` 是可以加入您 PowerShell 工具組中的一項優秀工具。 讓我們從基本概念開始，再循序漸進說明進階功能。 `PSCustomObject` 旨在使用簡單的方法建立結構化資料。 請見第一個範例，您便能更清楚地了解這句話的意思。

> [!NOTE]
> 本文的[原始版本][]出現在 [@KevinMarquette][] 所撰寫的部落格中。 PowerShell 小組感謝 Kevin 與我們分享此內容。 請前往 [PowerShellExplained.com][] 瀏覽 Kevin 的部落格。

## <a name="creating-a-pscustomobject"></a>建立 PSCustomObject

我非常喜歡在 PowerShell 中使用 `[PSCustomObject]`。 建立可用的物件從未如此簡單。
因此，我將跳過使用其他方法來建立物件，請注意其中大部分的範例均需使用 PowerShell v3.0 及更新版本。

```powershell
$myObject = [PSCustomObject]@{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}
```

這個方法相當適合我，因為我幾乎將雜湊表用於任何項目。 但有時候我會希望 PowerShell 能將雜湊表視為物件處理。 您會注意到的一個差異處便是當您想要使用 `Format-Table` 或 `Export-CSV` 時，卻發現雜湊表只不過是索引鍵/值組的集合。

您接著可以存取和使用值，其方式與使用一般物件相同。

```powershell
$myObject.Name
```

### <a name="converting-a-hashtable"></a>轉換雜湊表

在討論這個主題的同時，您知道可以這樣做嗎：

```powershell
$myHashtable = @{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}
$myObject = [pscustomobject]$myHashtable
```

我偏好從一開始就建立物件，但有時候您可能需要先使用雜湊表。 因為建構函式會取得物件屬性的雜湊表，所以此範例可以正常運作。 有一點相當重要，雖然此方法可以正常運作，但並非完全相等的項目。 最大差異在於屬性的順序並未獲得保留。

### <a name="legacy-approach"></a>舊版方法

您可能曾看過有人使用 `New-Object` 來建立自訂物件。

```powershell
$myHashtable = @{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}

$myObject = New-Object -TypeName PSObject -Property $myHashtable
```

這種方法的效率較低，但在舊版 PowerShell 中這可能是最好的選項了。

### <a name="saving-to-a-file"></a>儲存至檔案

我發現將雜湊表儲存至檔案的最佳方式是將其儲存為 JSON。 您可以將其匯入回 `[PSCusomObject]`

```powershell
$myObject | ConvertTo-Json -depth 1- | Set-Content -Path $Path
$myObject = Get-Content -Path $Path | ConvertFrom-Json
```

我在[讀取和寫入檔案的許多方式][]一文中談及更多將物件儲存到檔案的方式。

## <a name="working-with-properties"></a>使用屬性

### <a name="adding-properties"></a>新增屬性

您仍然可以使用 `Add-Member` 將新的屬性新增到 `PSCustomObject`。

```powershell
$myObject | Add-Member -MemberType NoteProperty -Name `ID` -Value 'KevinMarquette'

$myObject.ID
```

### <a name="remove-properties"></a>移除屬性

您也可以刪除物件的屬性。

```powershell
$myObject.psobject.properties.remove('ID')
```

`psobject` 是一種隱藏屬性，可以讓您存取基底物件的中繼資料。

### <a name="enumerating-property-names"></a>列舉屬性名稱

有時候，您需要物件上所有屬性名稱的清單。

```powershell
$myObject | Get-Member -MemberType NoteProperty | Select -ExpandProperty Name
```

我們也可以從 `psobject` 屬性取得相同的清單。

```powershell
$myobject.psobject.properties.name
```

### <a name="dynamically-accessing-properties"></a>動態存取屬性

我已經提到您可以直接存取屬性值。

```powershell
$myObject.Name
```

您可以使用字串作為屬性名稱，其仍會正常運作。

```powershell
$myObject.'Name'
```

我們可以更進一步地進行這項操作，使用變數作為屬性名稱。

```powershell
$property = 'Name'
$myObject.$property
```

我知道這看起來很奇怪，但這會正常運作。

### <a name="convert-pscustomboject-into-a-hashtable"></a>將 pscustomboject 轉換成雜湊表

若要繼續上一節的內容，您可以以動態方式逐步存取屬性，並從中建立雜湊表。

```powershell
$hashtable = @{}
foreach( $property in $myobject.psobject.properties.name )
{
    $hashtable[$property] = $myObject.$property
}
```

### <a name="testing-for-properties"></a>測試屬性

若您需要了解一個屬性是否存在，您可以直接檢查該屬性是否具備值。

```powershell
if( $null -ne $myObject.ID )
```

但如果該值為 `$null`，您仍然需要對其進行檢查，您可以使用 `psobject.properties` 來檢查該屬性。

```powershell
if( $myobject.psobject.properties.match('ID') )
```

## <a name="adding-object-methods"></a>新增物件方法

若您需要將指令碼方法新增到物件，您可以使用 `Add-Member` 和 `ScriptBlock` 進行這項操作。 您必須使用 `this` 自動變數來參考目前的物件。 以下是將物件轉換成雜湊表的 `scriptblock`。 (與上一個範例相同的程式碼)

```powershell
$ScriptBlock = {
    $hashtable = @{}
    foreach( $property in $this.psobject.properties.name )
    {
        $hashtable[$property] = $this.$property
    }
    return $hashtable
}
```

然後，我們將其作為指令碼屬性新增到物件。

```powershell
$memberParam = @{
    MemberType = "ScriptMethod"
    InputObject = $myobject
    Name = "ToHashtable"
    Value = $scriptBlock
}
Add-Member @memberParam
```

接著呼叫函數 (如下所示)：

```powershell
$myObject.ToHashtable()
```

### <a name="objects-vs-value-types"></a>物件與實值型別

物件與實值型別處理變數指派的方式不同。 若您將實值型別互相指派，只是把值複製到新的變數。

```powershell
$first = 1
$second = $first
$second = 2
```

在此情況下，`$first` 為 1，`$second` 為 2。

物件變數會保存實際物件的參考。 當您將一個物件指派給新的變數時，其仍會參考相同的物件。

```powershell
$third = [PSCustomObject]@{Key=3}
$fourth = $third
$fourth.Key = 4
```

因為 `$third` 與 `$fourth` 會參考物件的相同執行個體，所以 `$third.key` 與 `$fourth.Key` 皆為 4。

### <a name="psobjectcopy"></a>psobject.copy()

如果您需要物件的真正複本，您可以進行複製。

```powershell
$third = [PSCustomObject]@{Key=3}
$fourth = $third.psobject.copy()
$fourth.Key = 4
```

複製會建立物件的淺層複製 (Shallow Copy)。 其現在擁有不同的執行個體，且在此範例中，`$third.key` 為 3，`$fourth.Key` 則為 4。

我將這稱為淺層複製 (Shallow Copy)，因為若您擁有巢狀物件。 (其中屬性會包含其他物件)。 只會複製最上層的值。 子物件仍會互相參考。

### <a name="pstypename-for-custom-object-types"></a>自訂物件類型的 PSTypeName

有了物件以後，我們可以對其進行幾項可能不是那麼明顯的操作。 首先需要為其提供一個 `PSTypeName`。 這是我觀察到人們普遍採用的方法：

```powershell
$myObject.PSObject.TypeNames.Insert(0,"My.Object")
```

我最近從這篇 [post by /u/markekraus][]文章中發現到另外一種進行此操作的方法。 我進行了一些研究並閱讀了更多來自 [Adam Bertram][] 和 [Mike Shepard][] 與此概念有關的文章，其中討論到這種方法可以讓您以內嵌的方式進行定義。

```powershell
$myObject = [PSCustomObject]@{
    PSTypeName = 'My.Object'
    Name       = 'Kevin'
    Language   = 'PowerShell'
    State      = 'Texas'
}
```

我非常喜歡這種方法，因為這相當適用於程式設計語言。 現在我們有了具備適當類型名稱的物件，可以進行更多操作。

## <a name="using-defaultpropertyset-the-long-way"></a>使用 DefaultPropertySet (較慢的方式)

根據預設，PowerShell 會為我們決定要顯示哪些屬性。 許多原生命令都包含了 `.ps1xml` [格式化檔案][]，可執行所有繁重的工作。 從這篇 [Boe Prox 的文章][]中，有另外一種方式可以只使用 PowerShell 在自訂物件上進行此操作。 我們可以為其提供 `MemberSet` 以供其使用。

```powershell
$defaultDisplaySet = 'Name','Language'
$defaultDisplayPropertySet = New-Object System.Management.Automation.PSPropertySet(‘DefaultDisplayPropertySet’,[string[]]$defaultDisplaySet)
$PSStandardMembers = [System.Management.Automation.PSMemberInfo[]]@($defaultDisplayPropertySet)
$MyObject | Add-Member MemberSet PSStandardMembers $PSStandardMembers
```

現在當物件進入殼層中時，根據預設只會顯示這些屬性。

### <a name="update-typedata-with-defaultpropertyset"></a>搭配 DefaultPropertySet 使用 Update-TypeData

這很不錯，但是我最近在觀看 [PowerShell unplugged 2016 with Jeffrey Snover & Don Jones][psunplugged] (Jeffrey Snover 和 Don Jones 的 PowerShell 不插電 2016) 時，發現還有更好的方式。 Jeffrey 使用 [Update-TypeData][] 來指定預設屬性。

```powershell
$TypeData = @{
    TypeName = 'My.Object'
    DefaultDisplayPropertySet = 'Name','Language'
}
Update-TypeData @TypeData
```

這相當簡單，甚至如果我沒有這篇文章作為快速參考，我幾乎仍然可以記得。 現在我可以輕鬆地建立包含許多屬性的物件，並讓其在殼層中以相當簡潔的方式提供檢視。 若我需要存取或查看其他屬性，這些屬性仍會在其位置。

```powershell
$myObject | Format-List *
```

### <a name="update-typedata-with-scriptproperty"></a>搭配 ScriptProperty 使用 Update-TypeData

我從該影片得知的另外一件事是為物件建立指令碼屬性。 這也是指出這項操作適用於現有物件的良好時機。

```powershell
$TypeData = @{
    TypeName = 'My.Object'
    MemberType = 'ScriptProperty'
    MemberName = 'UpperCaseName'
    Value = {$this.Name.toUpper()}
}
Update-TypeData @TypeData
```

您可以在建立物件前，或是建立物件之後進行這項操作，而其仍然會正常運作。 這正是與前述搭配指令碼屬性使用 `Add-Member` 的不同之處。 當您按照我先前參考的方式使用 `Add-Member`，其只會存在於物件的特定執行個體。 但這項操作適用於所有使用此 `TypeName` 的物件。

## <a name="function-parameters"></a>函數參數

您現在可以在函數和指令碼中使用這些參數的自訂類型。 您可以讓其中一個函數建立這些自訂物件，然後將這些物件傳遞至其他函數。

```powershell
param( [PSTypeName('My.Object')]$Data )
```

PowerShell 會要求物件必須是您所指定的類型。 當類型無法自動比對時，便會擲回驗證錯誤，為您省下在程式碼中對其進行測試的步驟。 讓 PowerShell 達到最佳效果的絕佳範例。

### <a name="function-outputtype"></a>函數 OutputType

您也可以為進階函數定義 `OutputType`。

```powershell
function Get-MyObject
{
    [OutputType('My.Object')]
    [CmdletBinding()]
        param
        (
            ...
```

**OutputType** 屬性值只是文件備註。 其並非衍生自函數程式碼或與實際的函數輸出比較。

使用輸出類型旨在讓函數的中繼資訊反映您的意圖。 像是 `Get-Command` 和 `Get-Help` 等可供您開發環境利用的項目。 如需詳細資訊，請查看其說明：[about_Functions_OutputTypeAttribute][]。

換句話說，若您使用 Pester 對函數進行單元測試，確保輸出物件與您的 **OutputType** 相符便是個不錯的做法。 這可以擷取不應進入管道卻進入管道的變數。

## <a name="closing-thoughts"></a>結論

本文的內容主要與 `[PSCustomObject]` 有關，但其中許多資訊都適用於一般的物件。

我以前曾經看過這些大部分的功能，但從未見過將這些資訊集中以展示 `PSCustomObject` 的功能。 就在上一週我偶然發現另外一種做法，而我相當驚訝先前從未見過這種做法。 我想要將這些概念集中在一起，讓您有機會以更宏觀的方式來檢視，並在您有機會使用這些功能時知道這些功能存在。 我希望您可以了解到一些資訊，並找到將這些資訊融入您指令碼的方式。

<!-- link references -->
[原始版本]: https://powershellexplained.com/2016-10-28-powershell-everything-you-wanted-to-know-about-pscustomobject/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Boe Prox 的文章]: https://learn-PowerShell.net/2013/08/03/quick-hits-set-the-default-property-display-in-PowerShell-on-custom-objects/
[格式化檔案]: https://mcpmag.com/articles/2014/05/13/PowerShell-properties-part-3.aspx
[about_Functions_OutputTypeAttribute]: /powershell/module/microsoft.powershell.core/about/about_functions_outputtypeattribute
[讀取和寫入檔案的許多方式]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files
[post by /u/markekraus]: https://www.reddit.com/r/PowerShell/comments/590awc/is_it_possible_to_initialize_a_pscustoobject_with/
[Adam Bertram]: http://www.adamtheautomator.com/building-custom-object-types-PowerShell-pstypename/
[Mike Shepard]: https://powershellstation.com/2016/05/22/custom-objects-and-pstypename/
[psunplugged]: https://www.youtube.com/watch?v=Ab46gHXNm8Q
[Update-TypeData]: /powershell/module/microsoft.powershell.utility/update-typedata
