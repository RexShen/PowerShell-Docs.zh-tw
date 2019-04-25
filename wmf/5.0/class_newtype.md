---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: a96a4a58dafa01fb43f5bdffb52ef833816148e7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058364"
---
# <a name="new-language-features-in-powershell-50"></a><span data-ttu-id="949cf-102">PowerShell 5.0 的新語言功能</span><span class="sxs-lookup"><span data-stu-id="949cf-102">New language features in PowerShell 5.0</span></span>

<span data-ttu-id="949cf-103">PowerShell 5.0 在 Windows PowerShell 中引進了下列新的語言元素︰</span><span class="sxs-lookup"><span data-stu-id="949cf-103">PowerShell 5.0 introduces the following new language elements in Windows PowerShell:</span></span>

## <a name="class-keyword"></a><span data-ttu-id="949cf-104">Class 關鍵字</span><span class="sxs-lookup"><span data-stu-id="949cf-104">Class keyword</span></span>

<span data-ttu-id="949cf-105">**class** 關鍵字會定義新的類別。</span><span class="sxs-lookup"><span data-stu-id="949cf-105">The **class** keyword defines a new class.</span></span> <span data-ttu-id="949cf-106">這是真的 .NET Framework 類型。</span><span class="sxs-lookup"><span data-stu-id="949cf-106">This is a true .NET Framework type.</span></span>
<span data-ttu-id="949cf-107">類別成員是公用的，但只在模組範圍內公用。</span><span class="sxs-lookup"><span data-stu-id="949cf-107">Class members are public, but only public within the module scope.</span></span>
<span data-ttu-id="949cf-108">類型名稱不能當做字串參考 (例如，`New-Object` 不作用)，而且在這個版本中，您無法在已定義類別的指令碼/模組檔案外部使用類型常值 (例如，`[MyClass]`)。</span><span class="sxs-lookup"><span data-stu-id="949cf-108">You can't refer to the type name as a string (for example, `New-Object` doesn't work), and in this release, you can't use a type literal (for example, `[MyClass]`) outside the script/module file in which the class is defined.</span></span>

```powershell
class MyClass
{
    ...
}
```

## <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="949cf-109">Enum 關鍵字和列舉</span><span class="sxs-lookup"><span data-stu-id="949cf-109">Enum keyword and enumerations</span></span>

<span data-ttu-id="949cf-110">已加入對 **enum** 關鍵字的支援，使用新行字元為分隔符號。</span><span class="sxs-lookup"><span data-stu-id="949cf-110">Support for the **enum** keyword has been added, which uses newline as the delimiter.</span></span>
<span data-ttu-id="949cf-111">目前的限制︰您不能根據列舉程式本身定義列舉程式，但可以根據另一個 enum 初始化某個 enum，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="949cf-111">Current limitations: you cannot define an enumerator in terms of itself, but you can initialize an enum in terms of another enum, as shown in the following example.</span></span>
<span data-ttu-id="949cf-112">此外，目前無法指定基底類型，它一律是 [int]。</span><span class="sxs-lookup"><span data-stu-id="949cf-112">Also, the base type cannot currently be specified; it is always [int].</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="949cf-113">列舉程式值必須是剖析時間常數，您不能將它設為叫用命令的結果。</span><span class="sxs-lookup"><span data-stu-id="949cf-113">An enumerator value must be a parse time constant; you cannot set it to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="949cf-114">Enum 支援算數運算，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="949cf-114">Enums support arithmetic operations, as shown in the following example.</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

## <a name="import-dscresource"></a><span data-ttu-id="949cf-115">Import-DscResource</span><span class="sxs-lookup"><span data-stu-id="949cf-115">Import-DscResource</span></span>

<span data-ttu-id="949cf-116">**Import-DscResource** 現在是真的動態關鍵字。</span><span class="sxs-lookup"><span data-stu-id="949cf-116">**Import-DscResource** is now a true dynamic keyword.</span></span>
<span data-ttu-id="949cf-117">PowerShell 會剖析指定模組的根模組，搜尋包含 **DscResource** 屬性的類別。</span><span class="sxs-lookup"><span data-stu-id="949cf-117">PowerShell parses the specified module’s root module, searching for classes that contain the **DscResource** attribute.</span></span>

## <a name="implementingassembly"></a><span data-ttu-id="949cf-118">ImplementingAssembly</span><span class="sxs-lookup"><span data-stu-id="949cf-118">ImplementingAssembly</span></span>

<span data-ttu-id="949cf-119">新的欄位 **ImplementingAssembly**，已加入 ModuleInfo 中。</span><span class="sxs-lookup"><span data-stu-id="949cf-119">A new field, **ImplementingAssembly**, has been added to ModuleInfo.</span></span> <span data-ttu-id="949cf-120">如果指令碼定義類別，它會設定成為指令碼模組所建立的動態組件，或二進位模組的載入組件。</span><span class="sxs-lookup"><span data-stu-id="949cf-120">It is set to the dynamic assembly created for a script module if the script defines classes, or the loaded assembly for binary modules.</span></span> <span data-ttu-id="949cf-121">當 ModuleType = Manifest 時不設定。</span><span class="sxs-lookup"><span data-stu-id="949cf-121">It is not set when ModuleType = Manifest.</span></span>

<span data-ttu-id="949cf-122">**ImplementingAssembly** 欄位的反映會探索模組中的資源。</span><span class="sxs-lookup"><span data-stu-id="949cf-122">Reflection on the **ImplementingAssembly** field discovers resources in a module.</span></span> <span data-ttu-id="949cf-123">這表示您可以探索以 PowerShell 或其他 Managed 語言撰寫的資源。</span><span class="sxs-lookup"><span data-stu-id="949cf-123">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

<span data-ttu-id="949cf-124">有初始設定式的欄位︰</span><span class="sxs-lookup"><span data-stu-id="949cf-124">Fields with initializers:</span></span>

```powershell
[int] $i = 5
```

<span data-ttu-id="949cf-125">支援靜態，其運作方式類似執行類型條件約束時的屬性，因此可以用任何順序指定。</span><span class="sxs-lookup"><span data-stu-id="949cf-125">Static is supported; it works like an attribute, as do the type constraints, so it can be specified in any order.</span></span>

```powershell
static [int] $count = 0
```

<span data-ttu-id="949cf-126">類型是選用項目。</span><span class="sxs-lookup"><span data-stu-id="949cf-126">A type is optional.</span></span>

```powershell
$s = "hello"
```

<span data-ttu-id="949cf-127">所有成員都是公用的。</span><span class="sxs-lookup"><span data-stu-id="949cf-127">All members are public.</span></span>

## <a name="constructors-and-instantiation"></a><span data-ttu-id="949cf-128">建構函式和實例</span><span class="sxs-lookup"><span data-stu-id="949cf-128">Constructors and instantiation</span></span>

<span data-ttu-id="949cf-129">Windows PowerShell 的類別可以有建構函式，名稱與其類別相同。</span><span class="sxs-lookup"><span data-stu-id="949cf-129">Windows PowerShell classes can have constructors; they have the same name as their class.</span></span> <span data-ttu-id="949cf-130">可以多載建構函式。</span><span class="sxs-lookup"><span data-stu-id="949cf-130">Constructors can be overloaded.</span></span> <span data-ttu-id="949cf-131">支援靜態的建構函式。</span><span class="sxs-lookup"><span data-stu-id="949cf-131">Static constructors are supported.</span></span> <span data-ttu-id="949cf-132">使用初始化運算式的屬性會先初始化，然後建構函式中的所有程式碼才執行。</span><span class="sxs-lookup"><span data-stu-id="949cf-132">Properties with initialization expressions are initialized before running any code in a constructor.</span></span> <span data-ttu-id="949cf-133">靜態屬性會在靜態建構函式主體之前初始化，執行個體屬性則在非靜態建構函式主體之前初始化。</span><span class="sxs-lookup"><span data-stu-id="949cf-133">Static properties are initialized before the body of a static constructor, and instance properties are initialized before the body of the non-static constructor.</span></span> <span data-ttu-id="949cf-134">目前沒有任何語法可從另一個建構函式呼叫建構函式 (例如 C\# 語法："this()")。</span><span class="sxs-lookup"><span data-stu-id="949cf-134">Currently, there is no syntax for calling a constructor from another constructor (like the C\# syntax ": this()").</span></span> <span data-ttu-id="949cf-135">因應措施是定義通用的 Init 方法。</span><span class="sxs-lookup"><span data-stu-id="949cf-135">The workaround is to define a common Init method.</span></span>

<span data-ttu-id="949cf-136">以下是這個版本建立類別實例的方法。</span><span class="sxs-lookup"><span data-stu-id="949cf-136">The following are ways of instantiating classes in this release.</span></span>

<span data-ttu-id="949cf-137">使用預設的建構函式建立實例。</span><span class="sxs-lookup"><span data-stu-id="949cf-137">Instantiating by using the default constructor.</span></span> <span data-ttu-id="949cf-138">請注意，這個版本不支援 New-Object。</span><span class="sxs-lookup"><span data-stu-id="949cf-138">Note that New-Object is not supported in this release.</span></span>

```powershell
$a = [MyClass]::new()
```

<span data-ttu-id="949cf-139">呼叫有參數的建構函式</span><span class="sxs-lookup"><span data-stu-id="949cf-139">Calling a constructor with a parameter</span></span>

```powershell
$b = [MyClass]::new(42)
```

<span data-ttu-id="949cf-140">將陣列傳遞至有多個參數的建構函式</span><span class="sxs-lookup"><span data-stu-id="949cf-140">Passing an array to a constructor with multiple parameters</span></span>
```powershell
$c = [MyClass]::new(@(42,43,44), "Hello")
```

<span data-ttu-id="949cf-141">在這個版本中，New-Object 不能和 Windows PowerShell 中定義的類別一起使用。</span><span class="sxs-lookup"><span data-stu-id="949cf-141">In this release, New-Object does not work with classes defined in Windows PowerShell.</span></span> <span data-ttu-id="949cf-142">這個版本中的類型名稱也只能以語彙方式顯示，亦即在模組或定義類別的指令碼外部不顯示類型名稱。</span><span class="sxs-lookup"><span data-stu-id="949cf-142">Also for this release, the type name is only visible lexically, meaning it is not visible outside of the module or script that defines the class.</span></span> <span data-ttu-id="949cf-143">函式可以傳回 Windows PowerShell 中定義的類別執行個體，而這些執行個體在模組或指令碼外部運作良好。</span><span class="sxs-lookup"><span data-stu-id="949cf-143">Functions can return instances of a class defined in Windows PowerShell, and instances work well outside of the module or script.</span></span>

<span data-ttu-id="949cf-144">`Get-Member -Static` 會列出建構函式，您可以像檢視任何其他方法一樣檢視多載。</span><span class="sxs-lookup"><span data-stu-id="949cf-144">`Get-Member -Static` lists constructors, so you can view overloads like any other method.</span></span> <span data-ttu-id="949cf-145">這個語法的效能也比 New-Object 快得多。</span><span class="sxs-lookup"><span data-stu-id="949cf-145">The performance of this syntax is also considerably faster than New-Object.</span></span>

<span data-ttu-id="949cf-146">名為 **new** 的 Pseudo-static 方法可搭配 .NET 類型，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="949cf-146">The pseudo-static method named **new** works with .NET types, as shown in the following example.</span></span>

```powershell
[hashtable]::new()
```

<span data-ttu-id="949cf-147">您現在可以看到建構函式多載了 Get-Member，或如本例所示：</span><span class="sxs-lookup"><span data-stu-id="949cf-147">You can now see constructor overloads with Get-Member, or as shown in this example:</span></span>

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

## <a name="methods"></a><span data-ttu-id="949cf-148">Methods</span><span class="sxs-lookup"><span data-stu-id="949cf-148">Methods</span></span>

<span data-ttu-id="949cf-149">Windows PowerShell 類別方法會實作為只有 End 區塊的 ScriptBlock。</span><span class="sxs-lookup"><span data-stu-id="949cf-149">A Windows PowerShell class method is implemented as a ScriptBlock that has only an end block.</span></span> <span data-ttu-id="949cf-150">所有方法都是公用的。</span><span class="sxs-lookup"><span data-stu-id="949cf-150">All methods are public.</span></span> <span data-ttu-id="949cf-151">下例說明定義名為 **DoSomething** 的方法。</span><span class="sxs-lookup"><span data-stu-id="949cf-151">The following shows an example of defining a method named **DoSomething**.</span></span>

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

<span data-ttu-id="949cf-152">方法引動過程︰</span><span class="sxs-lookup"><span data-stu-id="949cf-152">Method invocation:</span></span>

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

<span data-ttu-id="949cf-153">也支援多載的方法，也就是那些與現有方法同名，但依指定值區別的方法。</span><span class="sxs-lookup"><span data-stu-id="949cf-153">Overloaded methods--that is, those that are named the same as an existing method, but differentiated by their specified values--are also supported.</span></span>

## <a name="properties"></a><span data-ttu-id="949cf-154">Properties</span><span class="sxs-lookup"><span data-stu-id="949cf-154">Properties</span></span>

<span data-ttu-id="949cf-155">所有屬性都是公用的。</span><span class="sxs-lookup"><span data-stu-id="949cf-155">All properties are public.</span></span> <span data-ttu-id="949cf-156">屬性需要新行字元或分號。</span><span class="sxs-lookup"><span data-stu-id="949cf-156">Properties require either a newline or semicolon.</span></span> <span data-ttu-id="949cf-157">如不指定任何物件類型，屬性類型就是物件。</span><span class="sxs-lookup"><span data-stu-id="949cf-157">If no object type is specified, the property type is object.</span></span>

<span data-ttu-id="949cf-158">使用驗證屬性或引數轉換屬性 (例如 `[ValidateSet("aaa")]`) 的屬性運作一如預期。</span><span class="sxs-lookup"><span data-stu-id="949cf-158">Properties that use validation attributes or argument transformation attributes (e.g. `[ValidateSet("aaa")]`) work as expected.</span></span>

## <a name="hidden"></a><span data-ttu-id="949cf-159">Hidden</span><span class="sxs-lookup"><span data-stu-id="949cf-159">Hidden</span></span>

<span data-ttu-id="949cf-160">已加入新的關鍵字 **Hidden**。</span><span class="sxs-lookup"><span data-stu-id="949cf-160">A new keyword, **Hidden**, has been added.</span></span> <span data-ttu-id="949cf-161">**Hidden** 可以套用至屬性和方法 (包括建構函式)。</span><span class="sxs-lookup"><span data-stu-id="949cf-161">**Hidden** can be applied to properties and methods (including constructors).</span></span>

<span data-ttu-id="949cf-162">Hidden 成員是公用的，但不會出現在 Get-Member 的輸出中，除非加入 -Force 參數。</span><span class="sxs-lookup"><span data-stu-id="949cf-162">Hidden members are public, but do not appear in the output of Get-Member unless the -Force parameter is added.</span></span>

<span data-ttu-id="949cf-163">當索引標籤完成或使用 Intellisense 時不會包含 Hidden 成員，除非完成是發生在定義隱藏成員的類別中。</span><span class="sxs-lookup"><span data-stu-id="949cf-163">Hidden members are not included when tab completing or using Intellisense unless the completion occurs in the class defining the hidden member.</span></span>

<span data-ttu-id="949cf-164">已加入新屬性 **System.Management.Automation.HiddenAttribute**，所以 C# 程式碼在 Windows PowerShell 內有相同的語意。</span><span class="sxs-lookup"><span data-stu-id="949cf-164">A new attribute, **System.Management.Automation.HiddenAttribute** has been added so that C# code can have the same semantics within Windows PowerShell.</span></span>

## <a name="return-types"></a><span data-ttu-id="949cf-165">傳回類型</span><span class="sxs-lookup"><span data-stu-id="949cf-165">Return types</span></span>

<span data-ttu-id="949cf-166">傳回類型是合約，傳回值會轉換成預期的類型。</span><span class="sxs-lookup"><span data-stu-id="949cf-166">Return type is a contract; the return value is converted to the expected type.</span></span> <span data-ttu-id="949cf-167">如未指定任何傳回類型，傳回類型為 void。</span><span class="sxs-lookup"><span data-stu-id="949cf-167">If no return type is specified, the return type is void.</span></span> <span data-ttu-id="949cf-168">沒有任何物件資料流，物件無法故意或意外寫入管線。</span><span class="sxs-lookup"><span data-stu-id="949cf-168">There is no streaming of objects; objects cannot be written to the pipeline either intentionally or by accident.</span></span>

## <a name="attributes"></a><span data-ttu-id="949cf-169">屬性</span><span class="sxs-lookup"><span data-stu-id="949cf-169">Attributes</span></span>

<span data-ttu-id="949cf-170">加入了兩個新屬性：**DscResource** 及 **DscProperty**。</span><span class="sxs-lookup"><span data-stu-id="949cf-170">Two new attributes, **DscResource** and **DscProperty** have been added.</span></span>

## <a name="lexical-scoping-of-variables"></a><span data-ttu-id="949cf-171">變數的語彙範圍</span><span class="sxs-lookup"><span data-stu-id="949cf-171">Lexical scoping of variables</span></span>

<span data-ttu-id="949cf-172">下例說明語彙範圍在這個版本中的運作方式。</span><span class="sxs-lookup"><span data-stu-id="949cf-172">The following shows an example of how lexical scoping works in this release.</span></span>

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

## <a name="end-to-end-example"></a><span data-ttu-id="949cf-173">端對端範例</span><span class="sxs-lookup"><span data-stu-id="949cf-173">End-to-End Example</span></span>

<span data-ttu-id="949cf-174">下例會建立數個新的自訂類別以實作 HTML 動態樣式表語言 (DSL)。</span><span class="sxs-lookup"><span data-stu-id="949cf-174">The following example creates several new, custom classes to implement an HTML dynamic style sheet language (DSL).</span></span>
<span data-ttu-id="949cf-175">然後，範例會加入 Helper 函式來建立特定的元素類型，當做元素類別的一部分，例如標題樣式和資料表，因為類型不能用在模組範圍外。</span><span class="sxs-lookup"><span data-stu-id="949cf-175">Then, the example adds helper functions to create specific element types as part of the element class, such as heading styles and tables, because types cannot be used outside the scope of a module.</span></span>

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
