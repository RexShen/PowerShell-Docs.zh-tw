---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
title: 使用 PowerShell 類別建立自訂類型
ms.openlocfilehash: c2c50fb65ce4931fcf6ae529b4146df391c831c4
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147838"
---
# <a name="creating-custom-types-using-powershell-classes"></a>使用 PowerShell 類別建立自訂類型

PowerShell 5.0 新增了功能，可使用類似其他物件導向程式設計語言的正式語法和語意，來定義類別和其他使用者定義類型。 目標是要讓開發人員和 IT 專業人員能夠掌握更多面向的 PowerShell 使用案例、簡化 PowerShell 成品的開發 (例如 DSC 資源)，並擴大管理介面的涵蓋範圍。

## <a name="supported-scenarios-in-this-release"></a>本版的支援案例

- 使用 PowerShell 語言定義 DSC 資源及其相關聯類型
- 使用熟悉的物件導向程式設計建構，例如類別、屬性、方法等等，在 PowerShell 中定義自訂的類型。
- 具有 PowerShell 類別和類別基底 DSC 資源的繼承支援
- 使用 PowerShell 語言偵錯類型
- 使用正式的機制在正確的層級產生和處理例外狀況

## <a name="declare-base-class"></a>宣告基底類別

您可以將 PowerShell 類別宣告為另一個 PowerShell 類別的基底類型。

```powershell
class bar
{
   [int]foo()
       {
           return 100500
       }
}

class baz : bar {}

[baz]::new().foo() # return 100500
```

現有的 .NET Framework 類型也可以用作為基底類別︰

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

### <a name="call-base-class-constructor"></a>呼叫基底類別建構函式

若要從子類別中呼叫基底類別建構函式，請使用關鍵字 **base**：

```powershell
class A
{
    [int]$a

    A([int]$a)
    {
        $this.a = $a
    }
}

class B : A
{
    B() : base(103) {}
}

[B]::new().a # return 103
```

如果基底類別有預設的 (無參數) 建構函式，您可以省略明確的建構函式呼叫︰

```powershell
class C : B
{
    C([int]$c) {}
}
```

### <a name="call-base-class-method"></a>呼叫基底類別方法

您可以覆寫子類別中現有的方法。 若要這樣做，請使用相同的名稱和簽章宣告方法︰

```powershell
class baseClass
{
    [int]foo() {return 100500}
}

class childClass1 : baseClass
{
    [int]foo() {return 200600}
}

[childClass1]::new().foo() # return 200600
```

若要從覆寫的實作呼叫基底類別方法，請在引動過程上轉換為基底類別 (`[baseClass]$this`)︰

```powershell
class childClass2 : baseClass
{
    [int]foo()
    {
        return 3 * ([baseClass]$this).foo()
    }
}

[childClass2]::new().foo() # return 301500
```

所有的 PowerShell 方法都是虛擬的。 您可以藉由宣告含相同名稱和簽章的方法，使用與針對覆寫所做的相同語法，在子類別中隱藏非虛擬的 .NET 方法。

```powershell
class MyIntList : system.collections.generic.list[int]
{
    # Add is final in system.collections.generic.list
    [void] Add([int]$arg)
    {
        ([system.collections.generic.list[int]]$this).Add($arg * 2)
    }
}

$list = [MyIntList]::new()
$list.Add(100)
$list[0] # return 200
```

### <a name="declare-implemented-interface"></a>宣告實作的介面

如未指定基底類型，您可以在基底類型之後或緊跟在冒號 (:) 之後宣告實作的介面。 使用逗號分隔所有類型名稱。 其類似 C# 語法。

```powershell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

## <a name="new-language-features-in-powershell-50"></a>PowerShell 5.0 的新語言功能

PowerShell 5.0 會在 PowerShell 中引進下列新的語言元素︰

### <a name="class-keyword"></a>Class 關鍵字

`class` 關鍵字會定義新類別。 這是真的 .NET Framework 類型。 類別成員是公用的，但只在模組範圍內公用。 您不能將類型名稱當作字串來參考 (例如，`New-Object` 不會運作)，而且在這個版本中，您無法在類別定義所在的指令碼或模組檔案外部使用類型常值 (例如 `[MyClass]`)。

```powershell
class MyClass
{
    ...
}
```

### <a name="enum-keyword-and-enumerations"></a>Enum 關鍵字和列舉

已新增對 `enum` 關鍵字的支援，其會使用新行字元作為分隔符號。 您目前無法根據列舉本身來定義它。 不過，您可以根據另一個列舉來將某個列舉初始化，如下列範例所示。 此外，無法指定基底類型，它一律是 `[int]`。

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

列舉程式值必須是剖析時間常數。 您無法將它設定為所叫用命令的結果。

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

Enum 支援算數運算，如下例所示。

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="import-dscresource"></a>Import-DscResource

`Import-DscResource` 現在是真正的動態關鍵字。 PowerShell 會剖析所指定模組的根模組，其會搜尋包含 **DscResource** 屬性的類別。

### <a name="implementingassembly"></a>ImplementingAssembly

已將新欄位 **ImplementingAssembly** 新增至 **ModuleInfo**。 如果指令碼定義類別，它會設定成為指令碼模組所建立的動態組件，或二進位模組的載入組件。 若 **ModuleType** 為 **Manifest**，則不會設定它。

**ImplementingAssembly** 欄位的反映會探索模組中的資源。 這表示您可以探索以 PowerShell 或其他 Managed 語言撰寫的資源。

有初始設定式的欄位︰

```powershell
[int] $i = 5
```

支援 `Static`。 其運作方式類似屬性，就像執行類型條件約束一樣。 它可以依任何順序指定。

```powershell
static [int] $count = 0
```

類型是選用項目。

```powershell
$s = "hello"
```

所有成員都是公用的。

### <a name="constructors-and-instantiation"></a>建構函式和實例

PowerShell 類別可以有建構函式。 它們的名稱與其類別相同。 可以多載建構函式。 支援靜態的建構函式。 使用初始化運算式的屬性會先初始化，然後建構函式中的所有程式碼才執行。 靜態屬性會在靜態建構函式主體之前初始化，執行個體屬性則在非靜態建構函式主體之前初始化。 目前沒有任何語法可從另一個建構函式呼叫建構函式 (例如 C\# 語法："this()")。 因應措施是定義通用的 `Init()` 方法。

#### <a name="creating-instances"></a>建立執行個體

> [!NOTE]
> 在 PowerShell 5.0 中，`New-Object` 無法與 PowerShell 中定義的類別一起運作。 此外，類型名稱只能以語彙方式顯示，這表示不會在類別定義所在的模組或指令碼外部顯示類型名稱。 函式可以傳回 PowerShell 中定義之類別的執行個體。 那些執行個體可以在模組或指令碼外部運作。

1. 使用預設的建構函式建立實例。

   ```powershell
   $a = [MyClass]::new()
   ```

1. 呼叫有參數的建構函式

   ```powershell
   $b = [MyClass]::new(42)
   ```

1. 將陣列傳遞給含有多個參數的建構函式。

   ```powershell
   $c = [MyClass]::new(@(42,43,44), "Hello")
   ```

Pseudo-static 方法 `new()` 可搭配 .NET 類型來運作，如下列範例所示。

```powershell
[hashtable]::new()
```

#### <a name="discovering-constructors"></a>探索建構函式

您現在可以使用 `Get-Member` 來查看建構函式多載，或如下列範例所示：

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

`Get-Member -Static` 會列出建構函式，您可以像檢視任何其他方法一樣檢視多載。 這個語法的效能也比 `New-Object` 快得多。

### <a name="methods"></a>Methods

PowerShell 類別方法會實作為只有 End 區塊的 **ScriptBlock**。 所有方法都是公用的。 下例說明定義名為 **DoSomething** 的方法。

```powershell
class MyClass
{
    DoSomething($x)
    {
        $this._doSomething($x) # method syntax
    }
    private _doSomething($a) {}
}
```

方法引動過程︰

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

也支援多載的方法。

### <a name="properties"></a>Properties

所有屬性都是公用的。 屬性需要新行字元或分號。 如不指定任何物件類型，屬性類型就是物件。

使用驗證或引數轉換屬性 (Attribute) (例如 `[ValidateSet("aaa")]`) 的屬性 (Property) 會如預期般運作。

### <a name="hidden"></a>Hidden

已新增關鍵字 `Hidden`。 `Hidden` 可以套用至屬性和方法 (包括建構函式)。

Hidden 成員是公用的，但除非新增 `-Force` 參數，否則不會出現在 `Get-Member` 的輸出中。 當索引標籤完成或使用 Intellisense 時不會包含 Hidden 成員，除非完成是發生在定義隱藏成員的類別中。

已新增屬性 **System.Management.Automation.HiddenAttribute**，所以 C\# 程式碼會在 PowerShell 內具有相同的語意。

### <a name="return-types"></a>傳回類型

傳回類型是一個合約。 傳回值會轉換成預期的類型。 如果未指定任何傳回類型，則傳回類型為 **void**。 沒有任何物件的串流。 無法故意或意外將物件寫入至管線。

### <a name="attributes"></a>屬性

加入了兩個新屬性：**DscResource** 及 **DscProperty**。

### <a name="lexical-scoping-of-variables"></a>變數的語彙範圍

下例說明語彙範圍在這個版本中的運作方式。

```powershell
$d = 42 # Script scope

function bar
{
    $d = 0 # Function scope
    [MyClass]::DoSomething()
}

class MyClass
{
    static [object] DoSomething()
    {
        return $d # error, not found dynamically
        return $script:d # no error
        $d = $script:d
        return $d # no error, found lexically
    }
}

$v = bar
$v -eq $d # true
```

## <a name="end-to-end-example"></a>端對端範例

下列範例會建立一些自訂類別，以實作 HTML 動態樣式表語言 (DSL)。 然後，範例會加入 Helper 函式來建立特定的元素類型，當做元素類別的一部分，例如標題樣式和資料表，因為類型不能用在模組範圍外。

```powershell
# Classes that define the structure of the document
#
class Html
{
    [string] $docType
    [HtmlHead] $Head
    [Element[]] $Body

    [string] Render()
    {
        $text = "<html>`n<head>`n"
        $text += $this.Head
        $text += "`n</head>`n<body>`n"
        $text += $this.Body -join "`n" # Render all of the body elements
        $text += "</body>`n</html>"
        return $text
    }
    [string] ToString() { return $this.Render() }
}

class HtmlHead
{
    $Title
    $Base
    $Link
    $Style
    $Meta
    $Script
    [string] Render() { return "<title>$($this.Title)</title>" }
    [string] ToString() { return $this.Render() }
}

class Element
{
    [string] $Tag
    [string] $Text
    [hashtable] $Attributes
    [string] Render() {
        $attributesText= ""
        if ($this.Attributes)
        {
            foreach ($attr in $this.Attributes.Keys)
            {
                #BUGBUG - need to validate keys against attribute
                $attributesText += " $attr=`"$($this.Attributes[$attr])\`""
            }
        }
        return "<$($this.tag)${attributesText}>$($this.text)</$($this.tag)>`n"
    }
[string] ToString() { return $this.Render() }
}

#
# Helper functions for creating specific element types on top of the classes.
# These are required because types aren't visible outside of the module.
#

function H1 { [Element] @{ Tag = "H1" ; Text = $args.foreach{$_} -join " " }}
function H2 { [Element] @{ Tag = "H2" ; Text = $args.foreach{$_} -join " " }}
function H3 { [Element] @{ Tag = "H3" ; Text = $args.foreach{$_} -join " " }}
function P { [Element] @{ Tag = "P" ; Text = $args.foreach{$_} -join " " }}
function B { [Element] @{ Tag = "B" ; Text = $args.foreach{$_} -join " " }}
function I { [Element] @{ Tag = "I" ; Text = $args.foreach{$_} -join " " }}
function HREF
{
    param (
        $Name,
        $Link
    )
    return [Element] @{
        Tag = "A"
        Attributes = @{ HREF = $link }
        Text = $name
    }
}
function Table
{
    param (
    [Parameter(Mandatory)]
    [object[]]
        $Data,
    [Parameter()]
    [string[]]
        $Properties = "*",
    [Parameter()]
    [hashtable]
        $Attributes = @{ border=2; cellpadding=2; cellspacing=2 }
    )
$bodyText = ""
# Add the header tags
$bodyText += $Properties.foreach{TH $_}
# Add the rows
$bodyText += foreach ($row in $Data)
    {
        TR (-join $Properties.Foreach{ TD ($row.$_) } )
    }

    $table = [Element] @{
        Tag = "Table"
        Attributes = $Attributes
        Text = $bodyText
    }
$table
}
function TH { ([Element] @{ Tag = "TH" ; Text = $args.foreach{$_} -join " " }) }
function TR { ([Element] @{ Tag = "TR" ; Text = $args.foreach{$_} -join " " }) }
function TD { ([Element] @{ Tag = "TD" ; Text = $args.foreach{$_} -join " " }) }
function Style

{
    return [Element] @{
        Tag = "style"
        Text = "$args"
    }
}

# Takes a hash table, casts it to and HTML document
# and then returns the resulting type.
#
function Html ([HTML] $doc) { return $doc }
```
