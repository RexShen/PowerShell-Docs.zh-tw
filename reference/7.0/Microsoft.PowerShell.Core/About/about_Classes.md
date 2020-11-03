---
description: 說明如何使用類別來建立您自己的自訂類型。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_classes?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Classes
ms.openlocfilehash: 27950034806caf53b2cdbe50329709a8ab177aee
ms.sourcegitcommit: 16d62a98449e3ddaf8d7c65bc1848ede1fd8a3e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "93206276"
---
# <a name="about-classes"></a><span data-ttu-id="49ea9-104">關於類別</span><span class="sxs-lookup"><span data-stu-id="49ea9-104">About Classes</span></span>

## <a name="short-description"></a><span data-ttu-id="49ea9-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="49ea9-105">Short description</span></span>
<span data-ttu-id="49ea9-106">說明如何使用類別來建立您自己的自訂類型。</span><span class="sxs-lookup"><span data-stu-id="49ea9-106">Describes how you can use classes to create your own custom types.</span></span>

## <a name="long-description"></a><span data-ttu-id="49ea9-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="49ea9-107">Long description</span></span>

<span data-ttu-id="49ea9-108">PowerShell 5.0 新增了正式的語法，以定義類別和其他使用者定義的類型。</span><span class="sxs-lookup"><span data-stu-id="49ea9-108">PowerShell 5.0 adds a formal syntax to define classes and other user-defined types.</span></span> <span data-ttu-id="49ea9-109">新增類別可讓開發人員和 IT 專業人員將 PowerShell 用於更廣泛的使用案例。</span><span class="sxs-lookup"><span data-stu-id="49ea9-109">The addition of classes enables developers and IT professionals to embrace PowerShell for a wider range of use cases.</span></span> <span data-ttu-id="49ea9-110">它可簡化 PowerShell 成品的開發，並加速管理面的涵蓋範圍。</span><span class="sxs-lookup"><span data-stu-id="49ea9-110">It simplifies development of PowerShell artifacts and accelerates coverage of management surfaces.</span></span>

<span data-ttu-id="49ea9-111">類別宣告是在執行時間用來建立物件實例的藍圖。</span><span class="sxs-lookup"><span data-stu-id="49ea9-111">A class declaration is a blueprint used to create instances of objects at run time.</span></span> <span data-ttu-id="49ea9-112">當您定義類別時，類別名稱是類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="49ea9-112">When you define a class, the class name is the name of the type.</span></span> <span data-ttu-id="49ea9-113">例如，如果您宣告名為 **device** 的類別，並將變數初始化 `$dev` 為 **裝置** 的新實例， `$dev` 就是 **裝置** 類型的物件或實例。</span><span class="sxs-lookup"><span data-stu-id="49ea9-113">For example, if you declare a class named **Device** and initialize a variable `$dev` to a new instance of **Device** , `$dev` is an object or instance of type **Device** .</span></span> <span data-ttu-id="49ea9-114">每個 **裝置** 實例在其屬性中可以有不同的值。</span><span class="sxs-lookup"><span data-stu-id="49ea9-114">Each instance of **Device** can have different values in its properties.</span></span>

## <a name="supported-scenarios"></a><span data-ttu-id="49ea9-115">支援的案例</span><span class="sxs-lookup"><span data-stu-id="49ea9-115">Supported scenarios</span></span>

- <span data-ttu-id="49ea9-116">使用熟悉的物件導向程式設計語義（例如類別、屬性、方法、繼承等），在 PowerShell 中定義自訂類型。</span><span class="sxs-lookup"><span data-stu-id="49ea9-116">Define custom types in PowerShell using familiar object-oriented programming semantics like classes, properties, methods, inheritance, etc.</span></span>
- <span data-ttu-id="49ea9-117">使用 PowerShell 語言的 Debug 類型。</span><span class="sxs-lookup"><span data-stu-id="49ea9-117">Debug types using the PowerShell language.</span></span>
- <span data-ttu-id="49ea9-118">使用正式的機制產生和處理例外狀況。</span><span class="sxs-lookup"><span data-stu-id="49ea9-118">Generate and handle exceptions using formal mechanisms.</span></span>
- <span data-ttu-id="49ea9-119">使用 PowerShell 語言定義 DSC 資源及其相關聯的類型。</span><span class="sxs-lookup"><span data-stu-id="49ea9-119">Define DSC resources and their associated types by using the PowerShell language.</span></span>

## <a name="syntax"></a><span data-ttu-id="49ea9-120">Syntax</span><span class="sxs-lookup"><span data-stu-id="49ea9-120">Syntax</span></span>

<span data-ttu-id="49ea9-121">您可以使用下列語法來宣告類別：</span><span class="sxs-lookup"><span data-stu-id="49ea9-121">Classes are declared using the following syntax:</span></span>

```syntax
class <class-name> [: [<base-class>][,<interface-list]] {
    [[<attribute>] [hidden] [static] <property-definition> ...]
    [<class-name>([<constructor-argument-list>])
      {<constructor-statement-list>} ...]
    [[<attribute>] [hidden] [static] <method-definition> ...]
}
```

<span data-ttu-id="49ea9-122">類別會使用下列其中一個語法來具現化：</span><span class="sxs-lookup"><span data-stu-id="49ea9-122">Classes are instantiated using either of the following syntaxes:</span></span>

```syntax
[$<variable-name> =] New-Object -TypeName <class-name> [
  [-ArgumentList] <constructor-argument-list>]
```

```syntax
[$<variable-name> =] [<class-name>]::new([<constructor-argument-list>])
```

> [!NOTE]
> <span data-ttu-id="49ea9-123">使用語法時 `[<class-name>]::new()` ，類別名稱前後的括弧是強制性的。</span><span class="sxs-lookup"><span data-stu-id="49ea9-123">When using the `[<class-name>]::new()` syntax, brackets around the class name are mandatory.</span></span> <span data-ttu-id="49ea9-124">括弧會發出 PowerShell 的類型定義。</span><span class="sxs-lookup"><span data-stu-id="49ea9-124">The brackets signal a type definition for PowerShell.</span></span>

### <a name="example-syntax-and-usage"></a><span data-ttu-id="49ea9-125">範例語法和使用方式</span><span class="sxs-lookup"><span data-stu-id="49ea9-125">Example syntax and usage</span></span>

<span data-ttu-id="49ea9-126">此範例顯示建立可用類別所需的最低語法。</span><span class="sxs-lookup"><span data-stu-id="49ea9-126">This example shows the minimum syntax needed to create a usable class.</span></span>

```powershell
class Device {
    [string]$Brand
}

$dev = [Device]::new()
$dev.Brand = "Microsoft"
$dev
```

```Output
Brand
-----
Microsoft
```

## <a name="class-properties"></a><span data-ttu-id="49ea9-127">類別屬性</span><span class="sxs-lookup"><span data-stu-id="49ea9-127">Class properties</span></span>

<span data-ttu-id="49ea9-128">屬性是在類別範圍宣告的變數。</span><span class="sxs-lookup"><span data-stu-id="49ea9-128">Properties are variables declared at class scope.</span></span> <span data-ttu-id="49ea9-129">屬性可以是任何內建類型或另一個類別的實例。</span><span class="sxs-lookup"><span data-stu-id="49ea9-129">A property may be of any built-in type or an instance of another class.</span></span> <span data-ttu-id="49ea9-130">類別對於它們擁有的屬性數目沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="49ea9-130">Classes have no restriction in the number of properties they have.</span></span>

### <a name="example-class-with-simple-properties"></a><span data-ttu-id="49ea9-131">具有簡單屬性的範例類別</span><span class="sxs-lookup"><span data-stu-id="49ea9-131">Example class with simple properties</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku
}

$device = [Device]::new()
$device.Brand = "Microsoft"
$device.Model = "Surface Pro 4"
$device.VendorSku = "5072641000"

$device
```

```Output
Brand     Model         VendorSku
-----     -----         ---------
Microsoft Surface Pro 4 5072641000
```

### <a name="example-complex-types-in-class-properties"></a><span data-ttu-id="49ea9-132">類別屬性中的複雜類型範例</span><span class="sxs-lookup"><span data-stu-id="49ea9-132">Example complex types in class properties</span></span>

<span data-ttu-id="49ea9-133">此範例會使用 **裝置** 類別來定義空的 **機架** 類別。</span><span class="sxs-lookup"><span data-stu-id="49ea9-133">This example defines an empty **Rack** class using the **Device** class.</span></span> <span data-ttu-id="49ea9-134">接在此範例後面的範例示範如何將裝置新增至機架，以及如何從預先載入的機架開始。</span><span class="sxs-lookup"><span data-stu-id="49ea9-134">The examples, following this one, show how to add devices to the rack and how to start with a pre-loaded rack.</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku
}

class Rack {
    [string]$Brand
    [string]$Model
    [string]$VendorSku
    [string]$AssetId
    [Device[]]$Devices = [Device[]]::new(8)

}

$rack = [Rack]::new()

$rack
```

```Output

Brand     :
Model     :
VendorSku :
AssetId   :
Devices   : {$null, $null, $null, $null...}


```

## <a name="class-methods"></a><span data-ttu-id="49ea9-135">類別方法</span><span class="sxs-lookup"><span data-stu-id="49ea9-135">Class methods</span></span>

<span data-ttu-id="49ea9-136">方法會定義類別可以執行的動作。</span><span class="sxs-lookup"><span data-stu-id="49ea9-136">Methods define the actions that a class can perform.</span></span> <span data-ttu-id="49ea9-137">方法可能會採用提供輸入資料的參數。</span><span class="sxs-lookup"><span data-stu-id="49ea9-137">Methods may take parameters that provide input data.</span></span> <span data-ttu-id="49ea9-138">方法可以傳回輸出。</span><span class="sxs-lookup"><span data-stu-id="49ea9-138">Methods can return output.</span></span> <span data-ttu-id="49ea9-139">方法所傳回的資料可以是任何定義的資料類型。</span><span class="sxs-lookup"><span data-stu-id="49ea9-139">Data returned by a method can be any defined data type.</span></span>

<span data-ttu-id="49ea9-140">定義類別的方法時，您可以使用自動變數參考目前的類別物件 `$this` 。</span><span class="sxs-lookup"><span data-stu-id="49ea9-140">When defining a method for a class, you reference the current class object by using the `$this` automatic variable.</span></span> <span data-ttu-id="49ea9-141">這可讓您存取目前類別中定義的屬性和其他方法。</span><span class="sxs-lookup"><span data-stu-id="49ea9-141">This allows you to access properties and other methods defined in the current class.</span></span>

### <a name="example-simple-class-with-properties-and-methods"></a><span data-ttu-id="49ea9-142">具有屬性和方法的範例簡單類別</span><span class="sxs-lookup"><span data-stu-id="49ea9-142">Example simple class with properties and methods</span></span>

<span data-ttu-id="49ea9-143">擴充 **機架** 類別，在其中新增和移除裝置。</span><span class="sxs-lookup"><span data-stu-id="49ea9-143">Extending the **Rack** class to add and remove devices to or from it.</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku

    [string]ToString(){
        return ("{0}|{1}|{2}" -f $this.Brand, $this.Model, $this.VendorSku)
    }
}

class Rack {
    [int]$Slots = 8
    [string]$Brand
    [string]$Model
    [string]$VendorSku
    [string]$AssetId
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    [void] AddDevice([Device]$dev, [int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $dev
    }

    [void]RemoveDevice([int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $null
    }

    [int[]] GetAvailableSlots(){
        [int]$i = 0
        return @($this.Devices.foreach{ if($_ -eq $null){$i}; $i++})
    }
}

$rack = [Rack]::new()

$surface = [Device]::new()
$surface.Brand = "Microsoft"
$surface.Model = "Surface Pro 4"
$surface.VendorSku = "5072641000"

$rack.AddDevice($surface, 2)

$rack
$rack.GetAvailableSlots()
```

```Output

Slots     : 8
Brand     :
Model     :
VendorSku :
AssetId   :
Devices   : {$null, $null, Microsoft|Surface Pro 4|5072641000, $null...}

0
1
3
4
5
6
7

```

## <a name="output-in-class-methods"></a><span data-ttu-id="49ea9-144">類別方法的輸出</span><span class="sxs-lookup"><span data-stu-id="49ea9-144">Output in class methods</span></span>

<span data-ttu-id="49ea9-145">方法應定義傳回型別。</span><span class="sxs-lookup"><span data-stu-id="49ea9-145">Methods should have a return type defined.</span></span> <span data-ttu-id="49ea9-146">如果方法未傳回輸出，則輸出類型應該是 `[void]` 。</span><span class="sxs-lookup"><span data-stu-id="49ea9-146">If a method doesn't return output, then the output type should be `[void]`.</span></span>

<span data-ttu-id="49ea9-147">在類別方法中，除了語句中提及的物件以外，不會傳送任何物件至管線 `return` 。</span><span class="sxs-lookup"><span data-stu-id="49ea9-147">In class methods, no objects get sent to the pipeline except those mentioned in the `return` statement.</span></span> <span data-ttu-id="49ea9-148">程式碼不會意外輸出至管線。</span><span class="sxs-lookup"><span data-stu-id="49ea9-148">There's no accidental output to the pipeline from the code.</span></span>

> [!NOTE]
> <span data-ttu-id="49ea9-149">這基本上不同于 PowerShell 函式處理輸出的方式，其中所有專案都會移至管線。</span><span class="sxs-lookup"><span data-stu-id="49ea9-149">This is fundamentally different from how PowerShell functions handle output, where everything goes to the pipeline.</span></span>

<span data-ttu-id="49ea9-150">從類別方法內寫入至錯誤資料流程的非終止錯誤，不會經過傳遞。</span><span class="sxs-lookup"><span data-stu-id="49ea9-150">Non-terminating errors written to the error stream from inside a class method are not passed through.</span></span> <span data-ttu-id="49ea9-151">您必須使用 `throw` 來呈現終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="49ea9-151">You must use `throw` to surface a terminating error.</span></span>
<span data-ttu-id="49ea9-152">使用 `Write-*` Cmdlet，您仍然可以從類別方法內寫入 PowerShell 的輸出資料流程。</span><span class="sxs-lookup"><span data-stu-id="49ea9-152">Using the `Write-*` cmdlets, you can still write to PowerShell's output streams from within a class method.</span></span> <span data-ttu-id="49ea9-153">不過，您應該避免這種情況，讓方法只會使用語句來發出物件 `return` 。</span><span class="sxs-lookup"><span data-stu-id="49ea9-153">However, this should be avoided so that the method emits objects using only the `return` statement.</span></span>

### <a name="method-output"></a><span data-ttu-id="49ea9-154">方法輸出</span><span class="sxs-lookup"><span data-stu-id="49ea9-154">Method output</span></span>

<span data-ttu-id="49ea9-155">此範例示範不會從類別方法意外輸出至管線，但語句除外 `return` 。</span><span class="sxs-lookup"><span data-stu-id="49ea9-155">This example demonstrates no accidental output to the pipeline from class methods, except on the `return` statement.</span></span>

```powershell
class FunWithIntegers
{
    [int[]]$Integers = 0..10

    [int[]]GetOddIntegers(){
        return $this.Integers.Where({ ($_ % 2) })
    }

    [void] GetEvenIntegers(){
        # this following line doesn't go to the pipeline
        $this.Integers.Where({ ($_ % 2) -eq 0})
    }

    [string]SayHello(){
        # this following line doesn't go to the pipeline
        "Good Morning"

        # this line goes to the pipeline
        return "Hello World"
    }
}

$ints = [FunWithIntegers]::new()
$ints.GetOddIntegers()
$ints.GetEvenIntegers()
$ints.SayHello()
```

```Output
1
3
5
7
9
Hello World

```

## <a name="constructor"></a><span data-ttu-id="49ea9-156">建構函式</span><span class="sxs-lookup"><span data-stu-id="49ea9-156">Constructor</span></span>

<span data-ttu-id="49ea9-157">在建立類別的實例時，可讓您設定預設值和驗證物件邏輯。</span><span class="sxs-lookup"><span data-stu-id="49ea9-157">Constructors enable you to set default values and validate object logic at the moment of creating the instance of the class.</span></span> <span data-ttu-id="49ea9-158">函式的名稱與類別相同。</span><span class="sxs-lookup"><span data-stu-id="49ea9-158">Constructors have the same name as the class.</span></span> <span data-ttu-id="49ea9-159">您可以使用引數來初始化新物件的資料成員。</span><span class="sxs-lookup"><span data-stu-id="49ea9-159">Constructors might have arguments, to initialize the data members of the new object.</span></span>

<span data-ttu-id="49ea9-160">類別可以定義零或多個已定義的函式。</span><span class="sxs-lookup"><span data-stu-id="49ea9-160">The class can have zero or more constructors defined.</span></span> <span data-ttu-id="49ea9-161">如果未定義任何函式，則會為類別指定預設的無參數的函式。</span><span class="sxs-lookup"><span data-stu-id="49ea9-161">If no constructor is defined, the class is given a default parameterless constructor.</span></span> <span data-ttu-id="49ea9-162">這個函式會將所有成員初始化為其預設值。</span><span class="sxs-lookup"><span data-stu-id="49ea9-162">This constructor initializes all members to their default values.</span></span> <span data-ttu-id="49ea9-163">物件類型和字串會提供 null 值。</span><span class="sxs-lookup"><span data-stu-id="49ea9-163">Object types and strings are given null values.</span></span> <span data-ttu-id="49ea9-164">當您定義函式時，不會建立預設的無參數的函式。</span><span class="sxs-lookup"><span data-stu-id="49ea9-164">When you define constructor, no default parameterless constructor is created.</span></span> <span data-ttu-id="49ea9-165">如果有需要，請建立無參數的函式。</span><span class="sxs-lookup"><span data-stu-id="49ea9-165">Create a parameterless constructor if one is needed.</span></span>

### <a name="constructor-basic-syntax"></a><span data-ttu-id="49ea9-166">函數的基本語法</span><span class="sxs-lookup"><span data-stu-id="49ea9-166">Constructor basic syntax</span></span>

<span data-ttu-id="49ea9-167">在此範例中，會使用屬性和函式來定義裝置類別。</span><span class="sxs-lookup"><span data-stu-id="49ea9-167">In this example, the Device class is defined with properties and a constructor.</span></span>
<span data-ttu-id="49ea9-168">若要使用這個類別，使用者必須提供函式中所列參數的值。</span><span class="sxs-lookup"><span data-stu-id="49ea9-168">To use this class, the user is required to provide values for the parameters listed in the constructor.</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku

    Device(
        [string]$b,
        [string]$m,
        [string]$vsk
    ){
        $this.Brand = $b
        $this.Model = $m
        $this.VendorSku = $vsk
    }
}

[Device]$surface = [Device]::new("Microsoft", "Surface Pro 4", "5072641000")

$surface
```

```Output
Brand     Model         VendorSku
-----     -----         ---------
Microsoft Surface Pro 4 5072641000
```

### <a name="example-with-multiple-constructors"></a><span data-ttu-id="49ea9-169">使用多個函式的範例</span><span class="sxs-lookup"><span data-stu-id="49ea9-169">Example with multiple constructors</span></span>

<span data-ttu-id="49ea9-170">在此範例中， **裝置** 類別是以屬性、預設的函式，以及用來初始化實例的函式來定義。</span><span class="sxs-lookup"><span data-stu-id="49ea9-170">In this example, the **Device** class is defined with properties, a default constructor, and a constructor to initialize the instance.</span></span>

<span data-ttu-id="49ea9-171">預設的函式會將 **品牌** 設定為 **未定義** ，並將 **模型** 和 **廠商-sku** 保留 null 值。</span><span class="sxs-lookup"><span data-stu-id="49ea9-171">The default constructor sets the **brand** to **Undefined** , and leaves **model** and **vendor-sku** with null values.</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku

    Device(){
        $this.Brand = 'Undefined'
    }

    Device(
        [string]$b,
        [string]$m,
        [string]$vsk
    ){
        $this.Brand = $b
        $this.Model = $m
        $this.VendorSku = $vsk
    }
}

[Device]$somedevice = [Device]::new()
[Device]$surface = [Device]::new("Microsoft", "Surface Pro 4", "5072641000")

$somedevice
$surface
```

```Output
Brand       Model           VendorSku
-----       -----           ---------
Undefined
Microsoft   Surface Pro 4   5072641000
```

## <a name="hidden-attribute"></a><span data-ttu-id="49ea9-172">Hidden 屬性</span><span class="sxs-lookup"><span data-stu-id="49ea9-172">Hidden attribute</span></span>

<span data-ttu-id="49ea9-173">`hidden`屬性會隱藏屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="49ea9-173">The `hidden` attribute hides a property or method.</span></span> <span data-ttu-id="49ea9-174">屬性或方法仍可供使用者存取，而且可以在物件可用的所有範圍中使用。</span><span class="sxs-lookup"><span data-stu-id="49ea9-174">The property or method is still accessible to the user and is available in all scopes in which the object is available.</span></span> <span data-ttu-id="49ea9-175">隱藏的成員會在 Cmdlet 中隱藏 `Get-Member` ，而且無法在類別定義之外使用 tab 鍵自動完成或 IntelliSense 來顯示。</span><span class="sxs-lookup"><span data-stu-id="49ea9-175">Hidden members are hidden from the `Get-Member` cmdlet and can't be displayed using tab completion or IntelliSense outside the class definition.</span></span>

<span data-ttu-id="49ea9-176">如需詳細資訊，請參閱 [About_hidden](About_hidden.md)。</span><span class="sxs-lookup"><span data-stu-id="49ea9-176">For more information, see [About_hidden](About_hidden.md).</span></span>

### <a name="example-using-hidden-attributes"></a><span data-ttu-id="49ea9-177">使用隱藏屬性的範例</span><span class="sxs-lookup"><span data-stu-id="49ea9-177">Example using hidden attributes</span></span>

<span data-ttu-id="49ea9-178">當 **機架** 物件建立時，裝置的插槽數目是固定的值，不應該隨時變更。</span><span class="sxs-lookup"><span data-stu-id="49ea9-178">When a **Rack** object is created, the number of slots for devices is a fixed value that shouldn't be changed at any time.</span></span> <span data-ttu-id="49ea9-179">這是在建立時已知的值。</span><span class="sxs-lookup"><span data-stu-id="49ea9-179">This value is known at creation time.</span></span>

<span data-ttu-id="49ea9-180">使用 hidden 屬性可讓開發人員保持隱藏位置的數目，並防止不慎變更機架的大小。</span><span class="sxs-lookup"><span data-stu-id="49ea9-180">Using the hidden attribute allows the developer to keep the number of slots hidden and prevents unintentional changes the size of the rack.</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
}

class Rack {
    [int] hidden $Slots = 8
    [string]$Brand
    [string]$Model
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    Rack ([string]$b, [string]$m, [int]$capacity){
        ## argument validation here

        $this.Brand = $b
        $this.Model = $m
        $this.Slots = $capacity

        ## reset rack size to new capacity
        $this.Devices = [Device[]]::new($this.Slots)
    }
}

[Rack]$r1 = [Rack]::new("Microsoft", "Surface Pro 4", 16)

$r1
$r1.Devices.Length
$r1.Slots
```

```Output
Brand     Model         Devices
-----     -----         -------
Microsoft Surface Pro 4 {$null, $null, $null, $null...}
16
16
```

<span data-ttu-id="49ea9-181">[ **通知位置** ] 屬性不會顯示在 `$r1` 輸出中。</span><span class="sxs-lookup"><span data-stu-id="49ea9-181">Notice **Slots** property isn't shown in `$r1` output.</span></span> <span data-ttu-id="49ea9-182">不過，此大小已由函式變更。</span><span class="sxs-lookup"><span data-stu-id="49ea9-182">However, the size was changed by the constructor.</span></span>

## <a name="static-attribute"></a><span data-ttu-id="49ea9-183">靜態屬性</span><span class="sxs-lookup"><span data-stu-id="49ea9-183">Static attribute</span></span>

<span data-ttu-id="49ea9-184">`static`屬性會定義存在於類別中且不需要實例的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="49ea9-184">The `static` attribute defines a property or a method that exists in the class and needs no instance.</span></span>

<span data-ttu-id="49ea9-185">靜態屬性永遠可用，與類別具現化無關。</span><span class="sxs-lookup"><span data-stu-id="49ea9-185">A static property is always available, independent of class instantiation.</span></span> <span data-ttu-id="49ea9-186">靜態屬性會在類別的所有實例之間共用。</span><span class="sxs-lookup"><span data-stu-id="49ea9-186">A static property is shared across all instances of the class.</span></span> <span data-ttu-id="49ea9-187">靜態方法一律可供使用。</span><span class="sxs-lookup"><span data-stu-id="49ea9-187">A static method is available always.</span></span> <span data-ttu-id="49ea9-188">整個會話範圍的所有靜態屬性都會上線。</span><span class="sxs-lookup"><span data-stu-id="49ea9-188">All static properties live for the entire session span.</span></span>

### <a name="example-using-static-attributes-and-methods"></a><span data-ttu-id="49ea9-189">使用靜態屬性和方法的範例</span><span class="sxs-lookup"><span data-stu-id="49ea9-189">Example using static attributes and methods</span></span>

<span data-ttu-id="49ea9-190">假設在此具現化的機架存在於您的資料中心。</span><span class="sxs-lookup"><span data-stu-id="49ea9-190">Assume the racks instantiated here exist in your data center.</span></span> <span data-ttu-id="49ea9-191">因此，您會想要追蹤程式碼中的機架。</span><span class="sxs-lookup"><span data-stu-id="49ea9-191">So, you would like to keep track of the racks in your code.</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
}

class Rack {
    hidden [int] $Slots = 8
    static [Rack[]]$InstalledRacks = @()
    [string]$Brand
    [string]$Model
    [string]$AssetId
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    Rack ([string]$b, [string]$m, [string]$id, [int]$capacity){
        ## argument validation here

        $this.Brand = $b
        $this.Model = $m
        $this.AssetId = $id
        $this.Slots = $capacity

        ## reset rack size to new capacity
        $this.Devices = [Device[]]::new($this.Slots)

        ## add rack to installed racks
        [Rack]::InstalledRacks += $this
    }

    static [void]PowerOffRacks(){
        foreach ($rack in [Rack]::InstalledRacks) {
            Write-Warning ("Turning off rack: " + ($rack.AssetId))
        }
    }
}
```

### <a name="testing-static-property-and-method-exist"></a><span data-ttu-id="49ea9-192">測試靜態屬性和方法存在</span><span class="sxs-lookup"><span data-stu-id="49ea9-192">Testing static property and method exist</span></span>

```
PS> [Rack]::InstalledRacks.Length
0

PS> [Rack]::PowerOffRacks()

PS> (1..10) | ForEach-Object {
>>   [Rack]::new("Adatum Corporation", "Standard-16",
>>     $_.ToString("Std0000"), 16)
>> } > $null

PS> [Rack]::InstalledRacks.Length
10

PS> [Rack]::InstalledRacks[3]
Brand              Model       AssetId Devices
-----              -----       ------- -------
Adatum Corporation Standard-16 Std0004 {$null, $null, $null, $null...}

PS> [Rack]::PowerOffRacks()
WARNING: Turning off rack: Std0001
WARNING: Turning off rack: Std0002
WARNING: Turning off rack: Std0003
WARNING: Turning off rack: Std0004
WARNING: Turning off rack: Std0005
WARNING: Turning off rack: Std0006
WARNING: Turning off rack: Std0007
WARNING: Turning off rack: Std0008
WARNING: Turning off rack: Std0009
WARNING: Turning off rack: Std0010
```

<span data-ttu-id="49ea9-193">請注意，每次執行此範例時，機架數目都會增加。</span><span class="sxs-lookup"><span data-stu-id="49ea9-193">Notice that the number of racks increases each time you run this example.</span></span>

## <a name="property-validation-attributes"></a><span data-ttu-id="49ea9-194">屬性驗證屬性</span><span class="sxs-lookup"><span data-stu-id="49ea9-194">Property validation attributes</span></span>

<span data-ttu-id="49ea9-195">驗證屬性可讓您測試指定給屬性的值是否符合已定義的需求。</span><span class="sxs-lookup"><span data-stu-id="49ea9-195">Validation attributes allow you to test that values given to properties meet defined requirements.</span></span> <span data-ttu-id="49ea9-196">當指派值時，就會觸發驗證。</span><span class="sxs-lookup"><span data-stu-id="49ea9-196">Validation is triggered the moment that the value is assigned.</span></span> <span data-ttu-id="49ea9-197">請參閱 [about_functions_advanced_parameters](about_functions_advanced_parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="49ea9-197">See [about_functions_advanced_parameters](about_functions_advanced_parameters.md).</span></span>

### <a name="example-using-validation-attributes"></a><span data-ttu-id="49ea9-198">使用驗證屬性的範例</span><span class="sxs-lookup"><span data-stu-id="49ea9-198">Example using validation attributes</span></span>

```powershell
class Device {
    [ValidateNotNullOrEmpty()][string]$Brand
    [ValidateNotNullOrEmpty()][string]$Model
}

[Device]$dev = [Device]::new()

Write-Output "Testing dev"
$dev

$dev.Brand = ""
```

```Output
Testing dev

Brand Model
----- -----

Exception setting "Brand": "The argument is null or empty. Provide an
argument that is not null or empty, and then try the command again."
At C:\tmp\Untitled-5.ps1:11 char:1
+ $dev.Brand = ""
+ ~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [], SetValueInvocationException
    + FullyQualifiedErrorId : ExceptionWhenSetting
```

## <a name="inheritance-in-powershell-classes"></a><span data-ttu-id="49ea9-199">PowerShell 類別中的繼承</span><span class="sxs-lookup"><span data-stu-id="49ea9-199">Inheritance in PowerShell classes</span></span>

<span data-ttu-id="49ea9-200">您可以藉由建立衍生自現有類別的新類別來擴充類別。</span><span class="sxs-lookup"><span data-stu-id="49ea9-200">You can extend a class by creating a new class that derives from an existing class.</span></span> <span data-ttu-id="49ea9-201">衍生的類別會繼承基類的屬性。</span><span class="sxs-lookup"><span data-stu-id="49ea9-201">The derived class inherits the properties of the base class.</span></span> <span data-ttu-id="49ea9-202">您可以視需要新增或覆寫方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="49ea9-202">You can add or override methods and properties as required.</span></span>

<span data-ttu-id="49ea9-203">PowerShell 不支援多重繼承。</span><span class="sxs-lookup"><span data-stu-id="49ea9-203">PowerShell does not support multiple inheritance.</span></span> <span data-ttu-id="49ea9-204">類別不能繼承自一個以上的類別。</span><span class="sxs-lookup"><span data-stu-id="49ea9-204">Classes cannot inherit from more than one class.</span></span> <span data-ttu-id="49ea9-205">不過，您可以針對該目的使用介面。</span><span class="sxs-lookup"><span data-stu-id="49ea9-205">However, you can use interfaces for that purpose.</span></span>

<span data-ttu-id="49ea9-206">繼承執行是由運算子所定義 `:` ; 這表示擴充此類別或執行這些介面。</span><span class="sxs-lookup"><span data-stu-id="49ea9-206">Inheritance implementation is defined by the `:` operator; which means to extend this class or implements these interfaces.</span></span> <span data-ttu-id="49ea9-207">衍生類別在類別宣告中應一律為最左邊。</span><span class="sxs-lookup"><span data-stu-id="49ea9-207">The derived class should always be leftmost in the class declaration.</span></span>

### <a name="example-using-simple-inheritance-syntax"></a><span data-ttu-id="49ea9-208">使用簡單繼承語法的範例</span><span class="sxs-lookup"><span data-stu-id="49ea9-208">Example using simple inheritance syntax</span></span>

<span data-ttu-id="49ea9-209">此範例顯示簡單的 PowerShell 類別繼承語法。</span><span class="sxs-lookup"><span data-stu-id="49ea9-209">This example shows the simple PowerShell class inheritance syntax.</span></span>

```powershell
Class Derived : Base {...}
```

<span data-ttu-id="49ea9-210">這個範例會顯示繼承在基類後面的介面宣告。</span><span class="sxs-lookup"><span data-stu-id="49ea9-210">This example shows inheritance with an interface declaration coming after the base class.</span></span>

```powershell
Class Derived : Base, Interface {...}
```

### <a name="example-of-simple-inheritance-in-powershell-classes"></a><span data-ttu-id="49ea9-211">PowerShell 類別中簡單繼承的範例</span><span class="sxs-lookup"><span data-stu-id="49ea9-211">Example of simple inheritance in PowerShell classes</span></span>

<span data-ttu-id="49ea9-212">在此範例中，前一個範例中使用的 **機架** 和 **裝置** 類別較妥善定義如下：避免屬性重複、更妥善地對齊通用屬性，以及重複使用常見的商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="49ea9-212">In this example the **Rack** and **Device** classes used in the previous examples are better defined to: avoid property repetitions, better align common properties, and reuse common business logic.</span></span>

<span data-ttu-id="49ea9-213">資料中心內的大部分物件都是公司資產，因此將其視為資產來開始追蹤是合理的。</span><span class="sxs-lookup"><span data-stu-id="49ea9-213">Most objects in the data center are company assets, which makes sense to start tracking them as assets.</span></span> <span data-ttu-id="49ea9-214">裝置類型是由列舉所定義，如需 `DeviceType` 列舉的詳細資訊，請參閱 [about_Enum](about_Enum.md) 。</span><span class="sxs-lookup"><span data-stu-id="49ea9-214">Device types are defined by the `DeviceType` enumeration, see [about_Enum](about_Enum.md) for details on enumerations.</span></span>

<span data-ttu-id="49ea9-215">在我們的範例中，我們只會定義 `Rack` 和， `ComputeServer` 這兩個類別的副檔名都是 `Device` 。</span><span class="sxs-lookup"><span data-stu-id="49ea9-215">In our example, we're only defining `Rack` and `ComputeServer`; both extensions to the `Device` class.</span></span>

```powershell
enum DeviceType {
    Undefined = 0
    Compute = 1
    Storage = 2
    Networking = 4
    Communications = 8
    Power = 16
    Rack = 32
}

class Asset {
    [string]$Brand
    [string]$Model
}

class Device : Asset {
    hidden [DeviceType]$devtype = [DeviceType]::Undefined
    [string]$Status

    [DeviceType] GetDeviceType(){
        return $this.devtype
    }
}

class ComputeServer : Device {
    hidden [DeviceType]$devtype = [DeviceType]::Compute
    [string]$ProcessorIdentifier
    [string]$Hostname
}

class Rack : Device {
    hidden [DeviceType]$devtype = [DeviceType]::Rack
    hidden [int]$Slots = 8

    [string]$Datacenter
    [string]$Location
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    Rack (){
        ## Just create the default rack with 8 slots
    }

    Rack ([int]$s){
        ## Add argument validation logic here
        $this.Devices = [Device[]]::new($s)
    }

    [void] AddDevice([Device]$dev, [int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $dev
    }

    [void] RemoveDevice([int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $null
    }
}

$FirstRack = [Rack]::new(16)
$FirstRack.Status = "Operational"
$FirstRack.Datacenter = "PNW"
$FirstRack.Location = "F03R02.J10"

(0..15).ForEach({
    $ComputeServer = [ComputeServer]::new()
    $ComputeServer.Brand = "Fabrikam, Inc."       ## Inherited from Asset
    $ComputeServer.Model = "Fbk5040"              ## Inherited from Asset
    $ComputeServer.Status = "Installed"           ## Inherited from Device
    $ComputeServer.ProcessorIdentifier = "x64"    ## ComputeServer
    $ComputeServer.Hostname = ("r1s" + $_.ToString("000")) ## ComputeServer
    $FirstRack.AddDevice($ComputeServer, $_)
  })

$FirstRack
$FirstRack.Devices
```

```Output
Datacenter : PNW
Location   : F03R02.J10
Devices    : {r1s000, r1s001, r1s002, r1s003...}
Status     : Operational
Brand      :
Model      :

ProcessorIdentifier : x64
Hostname            : r1s000
Status              : Installed
Brand               : Fabrikam, Inc.
Model               : Fbk5040

ProcessorIdentifier : x64
Hostname            : r1s001
Status              : Installed
Brand               : Fabrikam, Inc.
Model               : Fbk5040

<... content truncated here for brevity ...>

ProcessorIdentifier : x64
Hostname            : r1s015
Status              : Installed
Brand               : Fabrikam, Inc.
Model               : Fbk5040
```

### <a name="calling-base-class-constructors"></a><span data-ttu-id="49ea9-216">呼叫基類的函式</span><span class="sxs-lookup"><span data-stu-id="49ea9-216">Calling base class constructors</span></span>

<span data-ttu-id="49ea9-217">若要從子類別叫用基類的函式，請新增 `base` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="49ea9-217">To invoke a base class constructor from a subclass, add the `base` keyword.</span></span>

```powershell
class Person {
    [int]$Age

    Person([int]$a)
    {
        $this.Age = $a
    }
}

class Child : Person
{
    [string]$School

    Child([int]$a, [string]$s ) : base($a) {
        $this.School = $s
    }
}

[Child]$littleone = [Child]::new(10, "Silver Fir Elementary School")

$littleone.Age
```

```Output

10
```

### <a name="invoke-base-class-methods"></a><span data-ttu-id="49ea9-218">叫用基類方法</span><span class="sxs-lookup"><span data-stu-id="49ea9-218">Invoke base class methods</span></span>

<span data-ttu-id="49ea9-219">若要覆寫子類別中現有的方法，請使用相同的名稱和簽章宣告方法。</span><span class="sxs-lookup"><span data-stu-id="49ea9-219">To override existing methods in subclasses, declare methods using the same name and signature.</span></span>

```powershell
class BaseClass
{
    [int]days() {return 1}
}
class ChildClass1 : BaseClass
{
    [int]days () {return 2}
}

[ChildClass1]::new().days()
```

```Output

2
```

<span data-ttu-id="49ea9-220">若要從覆寫的 baseclass 呼叫基類方法，請在叫用時轉換成基類 ( [] $this) 。</span><span class="sxs-lookup"><span data-stu-id="49ea9-220">To call base class methods from overridden implementations, cast to the base class ([baseclass]$this) on invocation.</span></span>

```powershell
class BaseClass
{
    [int]days() {return 1}
}
class ChildClass1 : BaseClass
{
    [int]days () {return 2}
    [int]basedays() {return ([BaseClass]$this).days()}
}

[ChildClass1]::new().days()
[ChildClass1]::new().basedays()
```

```Output

2
1
```

### <a name="inheriting-from-interfaces"></a><span data-ttu-id="49ea9-221">從介面繼承</span><span class="sxs-lookup"><span data-stu-id="49ea9-221">Inheriting from interfaces</span></span>

<span data-ttu-id="49ea9-222">PowerShell 類別可以使用用來擴充基類的相同繼承語法來執行介面。</span><span class="sxs-lookup"><span data-stu-id="49ea9-222">PowerShell classes can implement an interface using the same inheritance syntax used to extend base classes.</span></span> <span data-ttu-id="49ea9-223">因為介面允許多重繼承，所以執行介面的 PowerShell 類別可以繼承自多個類型，方法是在冒號 () 之後分隔類型名稱， `:` (`,`) 。</span><span class="sxs-lookup"><span data-stu-id="49ea9-223">Because interfaces allow multiple inheritance, a PowerShell class implementing an interface may inherit from multiple types, by separating the type names after the colon (`:`) with commas (`,`).</span></span> <span data-ttu-id="49ea9-224">執行介面的 PowerShell 類別必須執行該介面的所有成員。</span><span class="sxs-lookup"><span data-stu-id="49ea9-224">A PowerShell class that implements an interface must implement all the members of that interface.</span></span> <span data-ttu-id="49ea9-225">省略實作此實作介面成員會導致腳本中發生剖析時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="49ea9-225">Omitting the implemention interface members causes a parse-time error in the script.</span></span>

> [!NOTE]
> <span data-ttu-id="49ea9-226">PowerShell 目前不支援在 PowerShell 腳本中宣告新的介面。</span><span class="sxs-lookup"><span data-stu-id="49ea9-226">PowerShell does not currently support declaring new interfaces in PowerShell script.</span></span>

```powershell
class MyComparable : System.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, System.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

## <a name="importing-classes-from-a-powershell-module"></a><span data-ttu-id="49ea9-227">從 PowerShell 模組匯入類別</span><span class="sxs-lookup"><span data-stu-id="49ea9-227">Importing classes from a PowerShell module</span></span>

<span data-ttu-id="49ea9-228">`Import-Module` 和語句只會匯入模組函式 `#requires` 、別名和變數，如模組所定義。</span><span class="sxs-lookup"><span data-stu-id="49ea9-228">`Import-Module` and the `#requires` statement only import the module functions, aliases, and variables, as defined by the module.</span></span> <span data-ttu-id="49ea9-229">未匯入類別。</span><span class="sxs-lookup"><span data-stu-id="49ea9-229">Classes are not imported.</span></span> <span data-ttu-id="49ea9-230">語句會匯 `using module` 入模組中定義的類別。</span><span class="sxs-lookup"><span data-stu-id="49ea9-230">The `using module` statement imports the classes defined in the module.</span></span> <span data-ttu-id="49ea9-231">如果模組未在目前的會話中載入，則 `using` 語句會失敗。</span><span class="sxs-lookup"><span data-stu-id="49ea9-231">If the module isn't loaded in the current session, the `using` statement fails.</span></span> <span data-ttu-id="49ea9-232">如需有關語句的詳細資訊 `using` ，請參閱 [about_Using](about_Using.md)。</span><span class="sxs-lookup"><span data-stu-id="49ea9-232">For more information about the `using` statement, see [about_Using](about_Using.md).</span></span>

## <a name="the-psreference-type-is-not-supported-with-class-members"></a><span data-ttu-id="49ea9-233">類別成員不支援 PSReference 類型</span><span class="sxs-lookup"><span data-stu-id="49ea9-233">The PSReference type is not supported with class members</span></span>

<span data-ttu-id="49ea9-234">使用 `[ref]` 具有類別成員的類型轉換時，會以無訊息模式失敗。</span><span class="sxs-lookup"><span data-stu-id="49ea9-234">Using the `[ref]` type-cast with a class member silently fails.</span></span> <span data-ttu-id="49ea9-235">使用參數的 Api `[ref]` 無法與類別成員一起使用。</span><span class="sxs-lookup"><span data-stu-id="49ea9-235">APIs that use `[ref]` parameters cannot be used with class members.</span></span> <span data-ttu-id="49ea9-236">**PSReference** 是設計來支援 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="49ea9-236">The **PSReference** was designed to support COM objects.</span></span> <span data-ttu-id="49ea9-237">COM 物件有您需要以傳址方式傳遞值的情況。</span><span class="sxs-lookup"><span data-stu-id="49ea9-237">COM objects have cases where you need to pass a value in by reference.</span></span>

<span data-ttu-id="49ea9-238">如需類型的詳細資訊 `[ref]` ，請參閱 [PSReference 類別](/dotnet/api/system.management.automation.psreference)。</span><span class="sxs-lookup"><span data-stu-id="49ea9-238">For more information about the `[ref]` type, see [PSReference Class](/dotnet/api/system.management.automation.psreference).</span></span>

## <a name="see-also"></a><span data-ttu-id="49ea9-239">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49ea9-239">See also</span></span>

- [<span data-ttu-id="49ea9-240">About_hidden</span><span class="sxs-lookup"><span data-stu-id="49ea9-240">About_hidden</span></span>](About_hidden.md)
- [<span data-ttu-id="49ea9-241">about_Enum</span><span class="sxs-lookup"><span data-stu-id="49ea9-241">about_Enum</span></span>](about_Enum.md)
- [<span data-ttu-id="49ea9-242">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="49ea9-242">about_Language_Keywords</span></span>](about_language_keywords.md)
- [<span data-ttu-id="49ea9-243">about_Methods</span><span class="sxs-lookup"><span data-stu-id="49ea9-243">about_Methods</span></span>](about_methods.md)
- [<span data-ttu-id="49ea9-244">about_Using</span><span class="sxs-lookup"><span data-stu-id="49ea9-244">about_Using</span></span>](about_using.md)
