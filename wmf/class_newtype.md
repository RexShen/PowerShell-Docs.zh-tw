# PowerShell 5.0 的新語言功能 

PowerShell 5.0 在 Windows PowerShell 中引進了下列新的語言元素︰

## Class 關鍵字

**class** 關鍵字會定義新的類別。 這是真的 .NET Framework 類型。 
類別成員是公用的，但只在模組範圍內公用。
類型名稱不能當做字串參考 (例如，`New-Object` 不作用)，而且在這個版本中，您無法在已定義類別的指令碼/模組檔案外部使用類型常值 (例如，`[MyClass]`)。

```powershell
class MyClass
{
    ...
}
```

## Enum 關鍵字和列舉

已加入對 **enum** 關鍵字的支援，使用新行字元為分隔符號。
目前的限制︰您不能根據列舉程式本身定義列舉程式，但可以根據另一個 enum 初始化某個 enum，如下例所示。
此外，目前無法指定基底類型，它一律是 [int]。

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

列舉程式值必須是剖析時間常數，您不能將它設為叫用命令的結果。

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

## Import-DscResource

**Import-DscResource** 現在是真的動態關鍵字。
PowerShell 會剖析指定模組的根模組，搜尋包含 **DscResource** 屬性的類別。

## ImplementingAssembly

新的欄位 **ImplementingAssembly**，已加入 ModuleInfo 中。 如果指令碼定義類別，它會設定成為指令碼模組所建立的動態組件，或二進位模組的載入組件。 當 ModuleType = Manifest 時不設定。 

**ImplementingAssembly** 欄位的反映會探索模組中的資源。 這表示您可以探索以 PowerShell 或其他 Managed 語言撰寫的資源。

有初始設定式的欄位︰      

```powershell
[int] $i = 5
```

支援靜態，其運作方式類似執行類型條件約束時的屬性，因此可以用任何順序指定。

```powershell
static [int] $count = 0
```

類型是選用項目。

```powershell
$s = "hello"
```

所有成員都是公用的。 

## 建構函式和實例

Windows PowerShell 的類別可以有建構函式，名稱與其類別相同。 可以多載建構函式。 支援靜態的建構函式。 使用初始化運算式的屬性會先初始化，然後建構函式中的所有程式碼才執行。 靜態屬性會在靜態建構函式主體之前初始化，執行個體屬性則在非靜態建構函式主體之前初始化。 目前沒有任何語法可從另一個建構函式呼叫建構函式 (例如 C\# syntax ": this()")。 因應措施是定義通用的 Init 方法。 

以下是這個版本建立類別實例的方法。

使用預設的建構函式建立實例。 請注意，這個版本不支援 New-Object。

```powershell
$a = [MyClass]::new()
```

呼叫有參數的建構函式

```powershell
$b = [MyClass]::new(42)
```

將陣列傳遞至有多個參數的建構函式
```powershell
$c = [MyClass]::new(@(42,43,44), "Hello")
```

在這個版本中，New-Object 不能和 Windows PowerShell 中定義的類別一起使用。 這個版本中的類型名稱也只能以語彙方式顯示，亦即在模組或定義類別的指令碼外部不顯示類型名稱。 函式可以傳回 Windows PowerShell 中定義的類別執行個體，而這些執行個體在模組或指令碼外部運作良好。

`Get-Member -Static` 會列出建構函式，您可以像檢視任何其他方法一樣檢視多載。 這個語法的效能也比 New-Object 快得多。

名為 **new** 的 Pseudo-static 方法可搭配 .NET 類型，如下例所示。

```powershell
[hashtable]::new()
```

您現在可以看到建構函式多載了 Get-Member，或如本例所示：

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

## 方法

Windows PowerShell 類別方法會實作為只有 End 區塊的 ScriptBlock。 所有方法都是公用的。 下例說明定義名為 **DoSomething** 的方法。

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

也支援多載的方法，也就是那些與現有方法同名，但依指定值區別的方法。

## [內容] 

所有屬性都是公用的。 屬性需要新行字元或分號。 如不指定任何物件類型，屬性類型就是物件。

使用驗證屬性或引數轉換屬性 (例如 `[ValidateSet("aaa")]`) 的屬性運作一如預期。

## Hidden

已加入新的關鍵字 **Hidden**。 **Hidden** 可以套用至屬性和方法 (包括建構函式)。

Hidden 成員是公用的，但不會出現在 Get-Member 的輸出中，除非加入 -Force 參數。

當索引標籤完成或使用 Intellisense 時不會包含 Hidden 成員，除非完成是發生在定義隱藏成員的類別中。

已加入新屬性 **System.Management.Automation.HiddenAttribute**，所以 C# 程式碼在 Windows PowerShell 內有相同的語意。

## 傳回類型

傳回類型是合約，傳回值會轉換成預期的類型。 如未指定任何傳回類型，傳回類型為 void。 沒有任何物件資料流，物件無法故意或意外寫入管線。

## 屬性

已加入四個新屬性：**DscResource**、**DscResourceKey**、**DscResourceMandatory** 和 **DscResourceOut**。

## 變數的語彙範圍

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

## 端對端範例

下例會建立數個新的自訂類別以實作 HTML 動態樣式表語言 (DSL)。 
然後，範例會加入 Helper 函式來建立特定的元素類型，當做元素類別的一部分，例如標題樣式和資料表，因為類型不能用在模組範圍外。

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
# These are required because types aren’t visible outside of the module.
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
        TR (-join $Properties.Foreach{ TD ($row.$\_) } )
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
```<!--HONumber=Mar16_HO2-->
