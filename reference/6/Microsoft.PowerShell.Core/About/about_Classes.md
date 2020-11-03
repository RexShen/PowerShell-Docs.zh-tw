---
description: 說明如何使用類別來建立您自己的自訂類型。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_classes?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Classes
ms.openlocfilehash: e4e3379c18b8e63e5c494b71485d6dab5c7689f2
ms.sourcegitcommit: 16d62a98449e3ddaf8d7c65bc1848ede1fd8a3e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "93206272"
---
# <a name="about-classes"></a>關於類別

## <a name="short-description"></a>簡短描述
說明如何使用類別來建立您自己的自訂類型。

## <a name="long-description"></a>完整描述

PowerShell 5.0 新增了正式的語法，以定義類別和其他使用者定義的類型。 新增類別可讓開發人員和 IT 專業人員將 PowerShell 用於更廣泛的使用案例。 它可簡化 PowerShell 成品的開發，並加速管理面的涵蓋範圍。

類別宣告是在執行時間用來建立物件實例的藍圖。 當您定義類別時，類別名稱是類型的名稱。 例如，如果您宣告名為 **device** 的類別，並將變數初始化 `$dev` 為 **裝置** 的新實例， `$dev` 就是 **裝置** 類型的物件或實例。 每個 **裝置** 實例在其屬性中可以有不同的值。

## <a name="supported-scenarios"></a>支援的案例

- 使用熟悉的物件導向程式設計語義（例如類別、屬性、方法、繼承等），在 PowerShell 中定義自訂類型。
- 使用 PowerShell 語言的 Debug 類型。
- 使用正式的機制產生和處理例外狀況。
- 使用 PowerShell 語言定義 DSC 資源及其相關聯的類型。

## <a name="syntax"></a>Syntax

您可以使用下列語法來宣告類別：

```syntax
class <class-name> [: [<base-class>][,<interface-list]] {
    [[<attribute>] [hidden] [static] <property-definition> ...]
    [<class-name>([<constructor-argument-list>])
      {<constructor-statement-list>} ...]
    [[<attribute>] [hidden] [static] <method-definition> ...]
}
```

類別會使用下列其中一個語法來具現化：

```syntax
[$<variable-name> =] New-Object -TypeName <class-name> [
  [-ArgumentList] <constructor-argument-list>]
```

```syntax
[$<variable-name> =] [<class-name>]::new([<constructor-argument-list>])
```

> [!NOTE]
> 使用語法時 `[<class-name>]::new()` ，類別名稱前後的括弧是強制性的。 括弧會發出 PowerShell 的類型定義。

### <a name="example-syntax-and-usage"></a>範例語法和使用方式

此範例顯示建立可用類別所需的最低語法。

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

## <a name="class-properties"></a>類別屬性

屬性是在類別範圍宣告的變數。 屬性可以是任何內建類型或另一個類別的實例。 類別對於它們擁有的屬性數目沒有任何限制。

### <a name="example-class-with-simple-properties"></a>具有簡單屬性的範例類別

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

### <a name="example-complex-types-in-class-properties"></a>類別屬性中的複雜類型範例

此範例會使用 **裝置** 類別來定義空的 **機架** 類別。 接在此範例後面的範例示範如何將裝置新增至機架，以及如何從預先載入的機架開始。

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

## <a name="class-methods"></a>類別方法

方法會定義類別可以執行的動作。 方法可能會採用提供輸入資料的參數。 方法可以傳回輸出。 方法所傳回的資料可以是任何定義的資料類型。

定義類別的方法時，您可以使用自動變數參考目前的類別物件 `$this` 。 這可讓您存取目前類別中定義的屬性和其他方法。

### <a name="example-simple-class-with-properties-and-methods"></a>具有屬性和方法的範例簡單類別

擴充 **機架** 類別，在其中新增和移除裝置。

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

## <a name="output-in-class-methods"></a>類別方法的輸出

方法應定義傳回型別。 如果方法未傳回輸出，則輸出類型應該是 `[void]` 。

在類別方法中，除了語句中提及的物件以外，不會傳送任何物件至管線 `return` 。 程式碼不會意外輸出至管線。

> [!NOTE]
> 這基本上不同于 PowerShell 函式處理輸出的方式，其中所有專案都會移至管線。

從類別方法內寫入至錯誤資料流程的非終止錯誤，不會經過傳遞。 您必須使用 `throw` 來呈現終止錯誤。
使用 `Write-*` Cmdlet，您仍然可以從類別方法內寫入 PowerShell 的輸出資料流程。 不過，您應該避免這種情況，讓方法只會使用語句來發出物件 `return` 。

### <a name="method-output"></a>方法輸出

此範例示範不會從類別方法意外輸出至管線，但語句除外 `return` 。

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

## <a name="constructor"></a>建構函式

在建立類別的實例時，可讓您設定預設值和驗證物件邏輯。 函式的名稱與類別相同。 您可以使用引數來初始化新物件的資料成員。

類別可以定義零或多個已定義的函式。 如果未定義任何函式，則會為類別指定預設的無參數的函式。 這個函式會將所有成員初始化為其預設值。 物件類型和字串會提供 null 值。 當您定義函式時，不會建立預設的無參數的函式。 如果有需要，請建立無參數的函式。

### <a name="constructor-basic-syntax"></a>函數的基本語法

在此範例中，會使用屬性和函式來定義裝置類別。
若要使用這個類別，使用者必須提供函式中所列參數的值。

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

### <a name="example-with-multiple-constructors"></a>使用多個函式的範例

在此範例中， **裝置** 類別是以屬性、預設的函式，以及用來初始化實例的函式來定義。

預設的函式會將 **品牌** 設定為 **未定義** ，並將 **模型** 和 **廠商-sku** 保留 null 值。

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

## <a name="hidden-attribute"></a>Hidden 屬性

`hidden`屬性會隱藏屬性或方法。 屬性或方法仍可供使用者存取，而且可以在物件可用的所有範圍中使用。 隱藏的成員會在 Cmdlet 中隱藏 `Get-Member` ，而且無法在類別定義之外使用 tab 鍵自動完成或 IntelliSense 來顯示。

如需詳細資訊，請參閱 [About_hidden](About_hidden.md)。

### <a name="example-using-hidden-attributes"></a>使用隱藏屬性的範例

當 **機架** 物件建立時，裝置的插槽數目是固定的值，不應該隨時變更。 這是在建立時已知的值。

使用 hidden 屬性可讓開發人員保持隱藏位置的數目，並防止不慎變更機架的大小。

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

[ **通知位置** ] 屬性不會顯示在 `$r1` 輸出中。 不過，此大小已由函式變更。

## <a name="static-attribute"></a>靜態屬性

`static`屬性會定義存在於類別中且不需要實例的屬性或方法。

靜態屬性永遠可用，與類別具現化無關。 靜態屬性會在類別的所有實例之間共用。 靜態方法一律可供使用。 整個會話範圍的所有靜態屬性都會上線。

### <a name="example-using-static-attributes-and-methods"></a>使用靜態屬性和方法的範例

假設在此具現化的機架存在於您的資料中心。 因此，您會想要追蹤程式碼中的機架。

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

### <a name="testing-static-property-and-method-exist"></a>測試靜態屬性和方法存在

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

請注意，每次執行此範例時，機架數目都會增加。

## <a name="property-validation-attributes"></a>屬性驗證屬性

驗證屬性可讓您測試指定給屬性的值是否符合已定義的需求。 當指派值時，就會觸發驗證。 請參閱 [about_functions_advanced_parameters](about_functions_advanced_parameters.md)。

### <a name="example-using-validation-attributes"></a>使用驗證屬性的範例

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

## <a name="inheritance-in-powershell-classes"></a>PowerShell 類別中的繼承

您可以藉由建立衍生自現有類別的新類別來擴充類別。 衍生的類別會繼承基類的屬性。 您可以視需要新增或覆寫方法和屬性。

PowerShell 不支援多重繼承。 類別不能繼承自一個以上的類別。 不過，您可以針對該目的使用介面。

繼承執行是由運算子所定義 `:` ; 這表示擴充此類別或執行這些介面。 衍生類別在類別宣告中應一律為最左邊。

### <a name="example-using-simple-inheritance-syntax"></a>使用簡單繼承語法的範例

此範例顯示簡單的 PowerShell 類別繼承語法。

```powershell
Class Derived : Base {...}
```

這個範例會顯示繼承在基類後面的介面宣告。

```powershell
Class Derived : Base, Interface {...}
```

### <a name="example-of-simple-inheritance-in-powershell-classes"></a>PowerShell 類別中簡單繼承的範例

在此範例中，前一個範例中使用的 **機架** 和 **裝置** 類別較妥善定義如下：避免屬性重複、更妥善地對齊通用屬性，以及重複使用常見的商務邏輯。

資料中心內的大部分物件都是公司資產，因此將其視為資產來開始追蹤是合理的。 裝置類型是由列舉所定義，如需 `DeviceType` 列舉的詳細資訊，請參閱 [about_Enum](about_Enum.md) 。

在我們的範例中，我們只會定義 `Rack` 和， `ComputeServer` 這兩個類別的副檔名都是 `Device` 。

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

### <a name="calling-base-class-constructors"></a>呼叫基類的函式

若要從子類別叫用基類的函式，請新增 `base` 關鍵字。

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

### <a name="invoke-base-class-methods"></a>叫用基類方法

若要覆寫子類別中現有的方法，請使用相同的名稱和簽章宣告方法。

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

若要從覆寫的 baseclass 呼叫基類方法，請在叫用時轉換成基類 ( [] $this) 。

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

### <a name="inheriting-from-interfaces"></a>從介面繼承

PowerShell 類別可以使用用來擴充基類的相同繼承語法來執行介面。 因為介面允許多重繼承，所以執行介面的 PowerShell 類別可以繼承自多個類型，方法是在冒號 () 之後分隔類型名稱， `:` (`,`) 。 執行介面的 PowerShell 類別必須執行該介面的所有成員。 省略實作此實作介面成員會導致腳本中發生剖析時期錯誤。

> [!NOTE]
> PowerShell 目前不支援在 PowerShell 腳本中宣告新的介面。

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

## <a name="importing-classes-from-a-powershell-module"></a>從 PowerShell 模組匯入類別

`Import-Module` 和語句只會匯入模組函式 `#requires` 、別名和變數，如模組所定義。 未匯入類別。 語句會匯 `using module` 入模組中定義的類別。 如果模組未在目前的會話中載入，則 `using` 語句會失敗。 如需有關語句的詳細資訊 `using` ，請參閱 [about_Using](about_Using.md)。

## <a name="the-psreference-type-is-not-supported-with-class-members"></a>類別成員不支援 PSReference 類型

使用 `[ref]` 具有類別成員的類型轉換時，會以無訊息模式失敗。 使用參數的 Api `[ref]` 無法與類別成員一起使用。 **PSReference** 是設計來支援 COM 物件。 COM 物件有您需要以傳址方式傳遞值的情況。

如需類型的詳細資訊 `[ref]` ，請參閱 [PSReference 類別](/dotnet/api/system.management.automation.psreference)。

## <a name="see-also"></a>另請參閱

- [About_hidden](About_hidden.md)
- [about_Enum](about_Enum.md)
- [about_Language_Keywords](about_language_keywords.md)
- [about_Methods](about_methods.md)
- [about_Using](about_using.md)
