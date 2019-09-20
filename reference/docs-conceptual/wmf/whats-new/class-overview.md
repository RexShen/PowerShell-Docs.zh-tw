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
# <a name="creating-custom-types-using-powershell-classes"></a><span data-ttu-id="5caa3-103">使用 PowerShell 類別建立自訂類型</span><span class="sxs-lookup"><span data-stu-id="5caa3-103">Creating Custom Types using PowerShell Classes</span></span>

<span data-ttu-id="5caa3-104">PowerShell 5.0 新增了功能，可使用類似其他物件導向程式設計語言的正式語法和語意，來定義類別和其他使用者定義類型。</span><span class="sxs-lookup"><span data-stu-id="5caa3-104">PowerShell 5.0 added the ability to define classes and other user-defined types using formal syntax and semantics like other object-oriented programming languages.</span></span> <span data-ttu-id="5caa3-105">目標是要讓開發人員和 IT 專業人員能夠掌握更多面向的 PowerShell 使用案例、簡化 PowerShell 成品的開發 (例如 DSC 資源)，並擴大管理介面的涵蓋範圍。</span><span class="sxs-lookup"><span data-stu-id="5caa3-105">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios-in-this-release"></a><span data-ttu-id="5caa3-106">本版的支援案例</span><span class="sxs-lookup"><span data-stu-id="5caa3-106">Supported scenarios in this release</span></span>

- <span data-ttu-id="5caa3-107">使用 PowerShell 語言定義 DSC 資源及其相關聯類型</span><span class="sxs-lookup"><span data-stu-id="5caa3-107">Define DSC resources and their associated types by using the PowerShell language</span></span>
- <span data-ttu-id="5caa3-108">使用熟悉的物件導向程式設計建構，例如類別、屬性、方法等等，在 PowerShell 中定義自訂的類型。</span><span class="sxs-lookup"><span data-stu-id="5caa3-108">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, etc.</span></span>
- <span data-ttu-id="5caa3-109">具有 PowerShell 類別和類別基底 DSC 資源的繼承支援</span><span class="sxs-lookup"><span data-stu-id="5caa3-109">Inheritance support with class in PowerShell and class base DSC resource</span></span>
- <span data-ttu-id="5caa3-110">使用 PowerShell 語言偵錯類型</span><span class="sxs-lookup"><span data-stu-id="5caa3-110">Debug types by using the PowerShell language</span></span>
- <span data-ttu-id="5caa3-111">使用正式的機制在正確的層級產生和處理例外狀況</span><span class="sxs-lookup"><span data-stu-id="5caa3-111">Generate and handle exceptions by using formal mechanisms, and at the right level</span></span>

## <a name="declare-base-class"></a><span data-ttu-id="5caa3-112">宣告基底類別</span><span class="sxs-lookup"><span data-stu-id="5caa3-112">Declare Base Class</span></span>

<span data-ttu-id="5caa3-113">您可以將 PowerShell 類別宣告為另一個 PowerShell 類別的基底類型。</span><span class="sxs-lookup"><span data-stu-id="5caa3-113">You can declare a PowerShell class as a base type for another PowerShell class.</span></span>

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

<span data-ttu-id="5caa3-114">現有的 .NET Framework 類型也可以用作為基底類別︰</span><span class="sxs-lookup"><span data-stu-id="5caa3-114">You can also use existing .NET Framework types as base classes:</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

### <a name="call-base-class-constructor"></a><span data-ttu-id="5caa3-115">呼叫基底類別建構函式</span><span class="sxs-lookup"><span data-stu-id="5caa3-115">Call Base Class Constructor</span></span>

<span data-ttu-id="5caa3-116">若要從子類別中呼叫基底類別建構函式，請使用關鍵字 **base**：</span><span class="sxs-lookup"><span data-stu-id="5caa3-116">To call a base class constructor from a subclass, use the keyword **base**:</span></span>

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

<span data-ttu-id="5caa3-117">如果基底類別有預設的 (無參數) 建構函式，您可以省略明確的建構函式呼叫︰</span><span class="sxs-lookup"><span data-stu-id="5caa3-117">If a base class has a default (no parameter) constructor, you can omit an explicit constructor call:</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```

### <a name="call-base-class-method"></a><span data-ttu-id="5caa3-118">呼叫基底類別方法</span><span class="sxs-lookup"><span data-stu-id="5caa3-118">Call Base Class Method</span></span>

<span data-ttu-id="5caa3-119">您可以覆寫子類別中現有的方法。</span><span class="sxs-lookup"><span data-stu-id="5caa3-119">You can override existing methods in subclasses.</span></span> <span data-ttu-id="5caa3-120">若要這樣做，請使用相同的名稱和簽章宣告方法︰</span><span class="sxs-lookup"><span data-stu-id="5caa3-120">To do this, declare methods by using the same name and signature:</span></span>

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

<span data-ttu-id="5caa3-121">若要從覆寫的實作呼叫基底類別方法，請在引動過程上轉換為基底類別 (`[baseClass]$this`)︰</span><span class="sxs-lookup"><span data-stu-id="5caa3-121">To call base class methods from overridden implementations, cast to the base class (`[baseClass]$this`) on invocation:</span></span>

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

<span data-ttu-id="5caa3-122">所有的 PowerShell 方法都是虛擬的。</span><span class="sxs-lookup"><span data-stu-id="5caa3-122">All PowerShell methods are virtual.</span></span> <span data-ttu-id="5caa3-123">您可以藉由宣告含相同名稱和簽章的方法，使用與針對覆寫所做的相同語法，在子類別中隱藏非虛擬的 .NET 方法。</span><span class="sxs-lookup"><span data-stu-id="5caa3-123">You can hide non-virtual .NET methods in a subclass by using the same syntax as you do for an override, by declaring methods with same name and signature.</span></span>

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

### <a name="declare-implemented-interface"></a><span data-ttu-id="5caa3-124">宣告實作的介面</span><span class="sxs-lookup"><span data-stu-id="5caa3-124">Declare Implemented Interface</span></span>

<span data-ttu-id="5caa3-125">如未指定基底類型，您可以在基底類型之後或緊跟在冒號 (:) 之後宣告實作的介面。</span><span class="sxs-lookup"><span data-stu-id="5caa3-125">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="5caa3-126">使用逗號分隔所有類型名稱。</span><span class="sxs-lookup"><span data-stu-id="5caa3-126">Separate all type names by using commas.</span></span> <span data-ttu-id="5caa3-127">其類似 C# 語法。</span><span class="sxs-lookup"><span data-stu-id="5caa3-127">It's similar to C# syntax.</span></span>

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

## <a name="new-language-features-in-powershell-50"></a><span data-ttu-id="5caa3-128">PowerShell 5.0 的新語言功能</span><span class="sxs-lookup"><span data-stu-id="5caa3-128">New language features in PowerShell 5.0</span></span>

<span data-ttu-id="5caa3-129">PowerShell 5.0 會在 PowerShell 中引進下列新的語言元素︰</span><span class="sxs-lookup"><span data-stu-id="5caa3-129">PowerShell 5.0 introduces the following new language elements in PowerShell:</span></span>

### <a name="class-keyword"></a><span data-ttu-id="5caa3-130">Class 關鍵字</span><span class="sxs-lookup"><span data-stu-id="5caa3-130">Class keyword</span></span>

<span data-ttu-id="5caa3-131">`class` 關鍵字會定義新類別。</span><span class="sxs-lookup"><span data-stu-id="5caa3-131">The `class` keyword defines a new class.</span></span> <span data-ttu-id="5caa3-132">這是真的 .NET Framework 類型。</span><span class="sxs-lookup"><span data-stu-id="5caa3-132">This is a true .NET Framework type.</span></span> <span data-ttu-id="5caa3-133">類別成員是公用的，但只在模組範圍內公用。</span><span class="sxs-lookup"><span data-stu-id="5caa3-133">Class members are public, but only public within the module scope.</span></span> <span data-ttu-id="5caa3-134">您不能將類型名稱當作字串來參考 (例如，`New-Object` 不會運作)，而且在這個版本中，您無法在類別定義所在的指令碼或模組檔案外部使用類型常值 (例如 `[MyClass]`)。</span><span class="sxs-lookup"><span data-stu-id="5caa3-134">You can't refer to the type name as a string (for example, `New-Object` doesn't work), and in this release, you can't use a type literal (for example, `[MyClass]`) outside the script or module file in which the class is defined.</span></span>

```powershell
class MyClass
{
    ...
}
```

### <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="5caa3-135">Enum 關鍵字和列舉</span><span class="sxs-lookup"><span data-stu-id="5caa3-135">Enum keyword and enumerations</span></span>

<span data-ttu-id="5caa3-136">已新增對 `enum` 關鍵字的支援，其會使用新行字元作為分隔符號。</span><span class="sxs-lookup"><span data-stu-id="5caa3-136">Support for the `enum` keyword has been added, which uses newline as the delimiter.</span></span> <span data-ttu-id="5caa3-137">您目前無法根據列舉本身來定義它。</span><span class="sxs-lookup"><span data-stu-id="5caa3-137">Currently, you cannot define an enumerator in terms of itself.</span></span> <span data-ttu-id="5caa3-138">不過，您可以根據另一個列舉來將某個列舉初始化，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="5caa3-138">However, you can initialize an enum in terms of another enum, as shown in the following example.</span></span> <span data-ttu-id="5caa3-139">此外，無法指定基底類型，它一律是 `[int]`。</span><span class="sxs-lookup"><span data-stu-id="5caa3-139">Also, the base type cannot be specified; it is always `[int]`.</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="5caa3-140">列舉程式值必須是剖析時間常數。</span><span class="sxs-lookup"><span data-stu-id="5caa3-140">An enumerator value must be a parse time constant.</span></span> <span data-ttu-id="5caa3-141">您無法將它設定為所叫用命令的結果。</span><span class="sxs-lookup"><span data-stu-id="5caa3-141">You cannot set it to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="5caa3-142">Enum 支援算數運算，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="5caa3-142">Enums support arithmetic operations, as shown in the following example.</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="import-dscresource"></a><span data-ttu-id="5caa3-143">Import-DscResource</span><span class="sxs-lookup"><span data-stu-id="5caa3-143">Import-DscResource</span></span>

<span data-ttu-id="5caa3-144">`Import-DscResource` 現在是真正的動態關鍵字。</span><span class="sxs-lookup"><span data-stu-id="5caa3-144">`Import-DscResource` is now a true dynamic keyword.</span></span> <span data-ttu-id="5caa3-145">PowerShell 會剖析所指定模組的根模組，其會搜尋包含 **DscResource** 屬性的類別。</span><span class="sxs-lookup"><span data-stu-id="5caa3-145">PowerShell parses the specified module's root module, searching for classes that contain the **DscResource** attribute.</span></span>

### <a name="implementingassembly"></a><span data-ttu-id="5caa3-146">ImplementingAssembly</span><span class="sxs-lookup"><span data-stu-id="5caa3-146">ImplementingAssembly</span></span>

<span data-ttu-id="5caa3-147">已將新欄位 **ImplementingAssembly** 新增至 **ModuleInfo**。</span><span class="sxs-lookup"><span data-stu-id="5caa3-147">A new field, **ImplementingAssembly**, has been added to **ModuleInfo**.</span></span> <span data-ttu-id="5caa3-148">如果指令碼定義類別，它會設定成為指令碼模組所建立的動態組件，或二進位模組的載入組件。</span><span class="sxs-lookup"><span data-stu-id="5caa3-148">It is set to the dynamic assembly created for a script module if the script defines classes, or the loaded assembly for binary modules.</span></span> <span data-ttu-id="5caa3-149">若 **ModuleType** 為 **Manifest**，則不會設定它。</span><span class="sxs-lookup"><span data-stu-id="5caa3-149">It is not set when **ModuleType** is **Manifest**.</span></span>

<span data-ttu-id="5caa3-150">**ImplementingAssembly** 欄位的反映會探索模組中的資源。</span><span class="sxs-lookup"><span data-stu-id="5caa3-150">Reflection on the **ImplementingAssembly** field discovers resources in a module.</span></span> <span data-ttu-id="5caa3-151">這表示您可以探索以 PowerShell 或其他 Managed 語言撰寫的資源。</span><span class="sxs-lookup"><span data-stu-id="5caa3-151">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

<span data-ttu-id="5caa3-152">有初始設定式的欄位︰</span><span class="sxs-lookup"><span data-stu-id="5caa3-152">Fields with initializers:</span></span>

```powershell
[int] $i = 5
```

<span data-ttu-id="5caa3-153">支援 `Static`。</span><span class="sxs-lookup"><span data-stu-id="5caa3-153">`Static` is supported.</span></span> <span data-ttu-id="5caa3-154">其運作方式類似屬性，就像執行類型條件約束一樣。</span><span class="sxs-lookup"><span data-stu-id="5caa3-154">It works like an attribute, as do the type constraints.</span></span> <span data-ttu-id="5caa3-155">它可以依任何順序指定。</span><span class="sxs-lookup"><span data-stu-id="5caa3-155">It can be specified in any order.</span></span>

```powershell
static [int] $count = 0
```

<span data-ttu-id="5caa3-156">類型是選用項目。</span><span class="sxs-lookup"><span data-stu-id="5caa3-156">A type is optional.</span></span>

```powershell
$s = "hello"
```

<span data-ttu-id="5caa3-157">所有成員都是公用的。</span><span class="sxs-lookup"><span data-stu-id="5caa3-157">All members are public.</span></span>

### <a name="constructors-and-instantiation"></a><span data-ttu-id="5caa3-158">建構函式和實例</span><span class="sxs-lookup"><span data-stu-id="5caa3-158">Constructors and instantiation</span></span>

<span data-ttu-id="5caa3-159">PowerShell 類別可以有建構函式。</span><span class="sxs-lookup"><span data-stu-id="5caa3-159">PowerShell classes can have constructors.</span></span> <span data-ttu-id="5caa3-160">它們的名稱與其類別相同。</span><span class="sxs-lookup"><span data-stu-id="5caa3-160">They have the same name as their class.</span></span> <span data-ttu-id="5caa3-161">可以多載建構函式。</span><span class="sxs-lookup"><span data-stu-id="5caa3-161">Constructors can be overloaded.</span></span> <span data-ttu-id="5caa3-162">支援靜態的建構函式。</span><span class="sxs-lookup"><span data-stu-id="5caa3-162">Static constructors are supported.</span></span> <span data-ttu-id="5caa3-163">使用初始化運算式的屬性會先初始化，然後建構函式中的所有程式碼才執行。</span><span class="sxs-lookup"><span data-stu-id="5caa3-163">Properties with initialization expressions are initialized before running any code in a constructor.</span></span> <span data-ttu-id="5caa3-164">靜態屬性會在靜態建構函式主體之前初始化，執行個體屬性則在非靜態建構函式主體之前初始化。</span><span class="sxs-lookup"><span data-stu-id="5caa3-164">Static properties are initialized before the body of a static constructor, and instance properties are initialized before the body of the non-static constructor.</span></span> <span data-ttu-id="5caa3-165">目前沒有任何語法可從另一個建構函式呼叫建構函式 (例如 C\# 語法："this()")。</span><span class="sxs-lookup"><span data-stu-id="5caa3-165">Currently, there is no syntax for calling a constructor from another constructor (like the C\# syntax ": this()").</span></span> <span data-ttu-id="5caa3-166">因應措施是定義通用的 `Init()` 方法。</span><span class="sxs-lookup"><span data-stu-id="5caa3-166">The workaround is to define a common `Init()` method.</span></span>

#### <a name="creating-instances"></a><span data-ttu-id="5caa3-167">建立執行個體</span><span class="sxs-lookup"><span data-stu-id="5caa3-167">Creating instances</span></span>

> [!NOTE]
> <span data-ttu-id="5caa3-168">在 PowerShell 5.0 中，`New-Object` 無法與 PowerShell 中定義的類別一起運作。</span><span class="sxs-lookup"><span data-stu-id="5caa3-168">In PowerShell 5.0, `New-Object` does not work with classes defined in PowerShell.</span></span> <span data-ttu-id="5caa3-169">此外，類型名稱只能以語彙方式顯示，這表示不會在類別定義所在的模組或指令碼外部顯示類型名稱。</span><span class="sxs-lookup"><span data-stu-id="5caa3-169">Also, the type name is only visible lexically, meaning it is not visible outside of the module or script that defines the class.</span></span> <span data-ttu-id="5caa3-170">函式可以傳回 PowerShell 中定義之類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="5caa3-170">Functions can return instances of a class defined in PowerShell.</span></span> <span data-ttu-id="5caa3-171">那些執行個體可以在模組或指令碼外部運作。</span><span class="sxs-lookup"><span data-stu-id="5caa3-171">Those instances work outside of the module or script.</span></span>

1. <span data-ttu-id="5caa3-172">使用預設的建構函式建立實例。</span><span class="sxs-lookup"><span data-stu-id="5caa3-172">Instantiating by using the default constructor.</span></span>

   ```powershell
   $a = [MyClass]::new()
   ```

1. <span data-ttu-id="5caa3-173">呼叫有參數的建構函式</span><span class="sxs-lookup"><span data-stu-id="5caa3-173">Calling a constructor with a parameter</span></span>

   ```powershell
   $b = [MyClass]::new(42)
   ```

1. <span data-ttu-id="5caa3-174">將陣列傳遞給含有多個參數的建構函式。</span><span class="sxs-lookup"><span data-stu-id="5caa3-174">Passing an array to a constructor with multiple parameters.</span></span>

   ```powershell
   $c = [MyClass]::new(@(42,43,44), "Hello")
   ```

<span data-ttu-id="5caa3-175">Pseudo-static 方法 `new()` 可搭配 .NET 類型來運作，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="5caa3-175">The pseudo-static method `new()` works with .NET types, as shown in the following example.</span></span>

```powershell
[hashtable]::new()
```

#### <a name="discovering-constructors"></a><span data-ttu-id="5caa3-176">探索建構函式</span><span class="sxs-lookup"><span data-stu-id="5caa3-176">Discovering constructors</span></span>

<span data-ttu-id="5caa3-177">您現在可以使用 `Get-Member` 來查看建構函式多載，或如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="5caa3-177">You can now see constructor overloads with `Get-Member`, or as shown in this example:</span></span>

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

<span data-ttu-id="5caa3-178">`Get-Member -Static` 會列出建構函式，您可以像檢視任何其他方法一樣檢視多載。</span><span class="sxs-lookup"><span data-stu-id="5caa3-178">`Get-Member -Static` lists constructors, so you can view overloads like any other method.</span></span> <span data-ttu-id="5caa3-179">這個語法的效能也比 `New-Object` 快得多。</span><span class="sxs-lookup"><span data-stu-id="5caa3-179">The performance of this syntax is also considerably faster than `New-Object`.</span></span>

### <a name="methods"></a><span data-ttu-id="5caa3-180">Methods</span><span class="sxs-lookup"><span data-stu-id="5caa3-180">Methods</span></span>

<span data-ttu-id="5caa3-181">PowerShell 類別方法會實作為只有 End 區塊的 **ScriptBlock**。</span><span class="sxs-lookup"><span data-stu-id="5caa3-181">A PowerShell class method is implemented as a **ScriptBlock** that has only an end block.</span></span> <span data-ttu-id="5caa3-182">所有方法都是公用的。</span><span class="sxs-lookup"><span data-stu-id="5caa3-182">All methods are public.</span></span> <span data-ttu-id="5caa3-183">下例說明定義名為 **DoSomething** 的方法。</span><span class="sxs-lookup"><span data-stu-id="5caa3-183">The following shows an example of defining a method named **DoSomething**.</span></span>

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

<span data-ttu-id="5caa3-184">方法引動過程︰</span><span class="sxs-lookup"><span data-stu-id="5caa3-184">Method invocation:</span></span>

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

<span data-ttu-id="5caa3-185">也支援多載的方法。</span><span class="sxs-lookup"><span data-stu-id="5caa3-185">Overloaded methods are also supported.</span></span>

### <a name="properties"></a><span data-ttu-id="5caa3-186">Properties</span><span class="sxs-lookup"><span data-stu-id="5caa3-186">Properties</span></span>

<span data-ttu-id="5caa3-187">所有屬性都是公用的。</span><span class="sxs-lookup"><span data-stu-id="5caa3-187">All properties are public.</span></span> <span data-ttu-id="5caa3-188">屬性需要新行字元或分號。</span><span class="sxs-lookup"><span data-stu-id="5caa3-188">Properties require either a newline or semicolon.</span></span> <span data-ttu-id="5caa3-189">如不指定任何物件類型，屬性類型就是物件。</span><span class="sxs-lookup"><span data-stu-id="5caa3-189">If no object type is specified, the property type is object.</span></span>

<span data-ttu-id="5caa3-190">使用驗證或引數轉換屬性 (Attribute) (例如 `[ValidateSet("aaa")]`) 的屬性 (Property) 會如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="5caa3-190">Properties that use validation or argument transformation attributes (like `[ValidateSet("aaa")]`) work as expected.</span></span>

### <a name="hidden"></a><span data-ttu-id="5caa3-191">Hidden</span><span class="sxs-lookup"><span data-stu-id="5caa3-191">Hidden</span></span>

<span data-ttu-id="5caa3-192">已新增關鍵字 `Hidden`。</span><span class="sxs-lookup"><span data-stu-id="5caa3-192">A new keyword, `Hidden`, has been added.</span></span> <span data-ttu-id="5caa3-193">`Hidden` 可以套用至屬性和方法 (包括建構函式)。</span><span class="sxs-lookup"><span data-stu-id="5caa3-193">`Hidden` can be applied to properties and methods (including constructors).</span></span>

<span data-ttu-id="5caa3-194">Hidden 成員是公用的，但除非新增 `-Force` 參數，否則不會出現在 `Get-Member` 的輸出中。</span><span class="sxs-lookup"><span data-stu-id="5caa3-194">Hidden members are public, but do not appear in the output of `Get-Member` unless the `-Force` parameter is added.</span></span> <span data-ttu-id="5caa3-195">當索引標籤完成或使用 Intellisense 時不會包含 Hidden 成員，除非完成是發生在定義隱藏成員的類別中。</span><span class="sxs-lookup"><span data-stu-id="5caa3-195">Hidden members are not included when tab completing or using Intellisense unless the completion occurs in the class defining the hidden member.</span></span>

<span data-ttu-id="5caa3-196">已新增屬性 **System.Management.Automation.HiddenAttribute**，所以 C\# 程式碼會在 PowerShell 內具有相同的語意。</span><span class="sxs-lookup"><span data-stu-id="5caa3-196">A new attribute, **System.Management.Automation.HiddenAttribute** has been added so that C\# code can have the same semantics within PowerShell.</span></span>

### <a name="return-types"></a><span data-ttu-id="5caa3-197">傳回類型</span><span class="sxs-lookup"><span data-stu-id="5caa3-197">Return types</span></span>

<span data-ttu-id="5caa3-198">傳回類型是一個合約。</span><span class="sxs-lookup"><span data-stu-id="5caa3-198">Return type is a contract.</span></span> <span data-ttu-id="5caa3-199">傳回值會轉換成預期的類型。</span><span class="sxs-lookup"><span data-stu-id="5caa3-199">The return value is converted to the expected type.</span></span> <span data-ttu-id="5caa3-200">如果未指定任何傳回類型，則傳回類型為 **void**。</span><span class="sxs-lookup"><span data-stu-id="5caa3-200">If no return type is specified, the return type is **void**.</span></span> <span data-ttu-id="5caa3-201">沒有任何物件的串流。</span><span class="sxs-lookup"><span data-stu-id="5caa3-201">There is no streaming of objects.</span></span> <span data-ttu-id="5caa3-202">無法故意或意外將物件寫入至管線。</span><span class="sxs-lookup"><span data-stu-id="5caa3-202">Objects cannot be written to the pipeline either intentionally or by accident.</span></span>

### <a name="attributes"></a><span data-ttu-id="5caa3-203">屬性</span><span class="sxs-lookup"><span data-stu-id="5caa3-203">Attributes</span></span>

<span data-ttu-id="5caa3-204">加入了兩個新屬性：**DscResource** 及 **DscProperty**。</span><span class="sxs-lookup"><span data-stu-id="5caa3-204">Two new attributes, **DscResource** and **DscProperty** have been added.</span></span>

### <a name="lexical-scoping-of-variables"></a><span data-ttu-id="5caa3-205">變數的語彙範圍</span><span class="sxs-lookup"><span data-stu-id="5caa3-205">Lexical scoping of variables</span></span>

<span data-ttu-id="5caa3-206">下例說明語彙範圍在這個版本中的運作方式。</span><span class="sxs-lookup"><span data-stu-id="5caa3-206">The following shows an example of how lexical scoping works in this release.</span></span>

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

## <a name="end-to-end-example"></a><span data-ttu-id="5caa3-207">端對端範例</span><span class="sxs-lookup"><span data-stu-id="5caa3-207">End-to-End Example</span></span>

<span data-ttu-id="5caa3-208">下列範例會建立一些自訂類別，以實作 HTML 動態樣式表語言 (DSL)。</span><span class="sxs-lookup"><span data-stu-id="5caa3-208">The following example creates some custom classes to implement an HTML dynamic style sheet language (DSL).</span></span> <span data-ttu-id="5caa3-209">然後，範例會加入 Helper 函式來建立特定的元素類型，當做元素類別的一部分，例如標題樣式和資料表，因為類型不能用在模組範圍外。</span><span class="sxs-lookup"><span data-stu-id="5caa3-209">Then, the example adds helper functions to create specific element types as part of the element class, such as heading styles and tables, because types cannot be used outside the scope of a module.</span></span>

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
