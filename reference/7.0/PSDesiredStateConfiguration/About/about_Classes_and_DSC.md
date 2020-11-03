---
description: 說明如何使用類別，在 PowerShell 中使用 Desired State Configuration (DSC) 來進行開發。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 1/11/2019
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Classes_and_DSC
ms.openlocfilehash: 272d6872d096de864044ae41449caff472bb1799
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207480"
---
# <a name="about-classes-and-desired-state-configuration"></a>關於類別和 Desired State Configuration

## <a name="short-description"></a>簡短描述

說明如何使用類別，在 PowerShell 中使用 Desired State Configuration (DSC) 來進行開發。

## <a name="long-description"></a>完整描述

從 Windows PowerShell 5.0 開始，使用類似其他物件導向程式設計語言的正式語法和語義，新增了語言來定義類別和其他使用者定義類型。 目標是要讓開發人員和 IT 專業人員能夠將 PowerShell 用於更廣泛的使用案例、簡化 PowerShell 成品的開發（例如 DSC 資源），以及加快管理面的涵蓋範圍。

## <a name="supported-scenarios"></a>支援的案例

以下是支援的案例：

- 使用 PowerShell 語言定義 DSC 資源及其相關聯的類型。
- 使用熟悉的物件導向程式設計結構（例如類別、屬性、方法和繼承），在 PowerShell 中定義自訂類型。
- 使用 PowerShell 語言的偵錯工具類型。
- 使用正式的機制和適當層級來產生和處理例外狀況。

## <a name="define-dsc-resources-with-classes"></a>使用類別定義 DSC 資源

除了語法變更以外，類別定義的 DSC 資源和 Cmdlet DSC 資源提供者之間的主要差異如下：

- 不需要 (MOF) 檔的管理物件格式。
- 不需要模組資料夾中的 DSCResource 子資料夾。
- PowerShell 模組檔案可以包含多個 DSC 資源類別。

## <a name="create-a-class-defined-dsc-resource-provider"></a>建立類別定義的 DSC 資源提供者

下列範例是以模組 >mydscresource .psm1 儲存的類別定義 DSC 資源提供者。 您必須一律在類別定義的 DSC 資源提供者中包含索引鍵屬性。

```powershell
enum Ensure
{
    Absent
    Present
}

<#
    This resource manages the file in a specific path.
    [DscResource()] indicates the class is a DSC resource
#>

[DscResource()]
class FileResource
{
    <#
        This property is the fully qualified path to the file that is
        expected to be present or absent.

        The [DscProperty(Key)] attribute indicates the property is a
        key and its value uniquely identifies a resource instance.
        Defining this attribute also means the property is required
        and DSC will ensure a value is set before calling the resource.

        A DSC resource must define at least one key property.
    #>
    [DscProperty(Key)]
    [string]$Path

    <#
        This property indicates if the settings should be present or absent
        on the system. For present, the resource ensures the file pointed
        to by $Path exists. For absent, it ensures the file point to by
        $Path does not exist.

        The [DscProperty(Mandatory)] attribute indicates the property is
        required and DSC will guarantee it is set.

        If Mandatory is not specified or if it is defined as
        Mandatory=$false, the value is not guaranteed to be set when DSC
        calls the resource.  This is appropriate for optional properties.
    #>
    [DscProperty(Mandatory)]
    [Ensure] $Ensure

    <#
        This property defines the fully qualified path to a file that will
        be placed on the system if $Ensure = Present and $Path does not
        exist.

        NOTE: This property is required because [DscProperty(Mandatory)] is
        set.
    #>
    [DscProperty(Mandatory)]
    [string] $SourcePath

    <#
        This property reports the file's create timestamp.

        [DscProperty(NotConfigurable)] attribute indicates the property is
        not configurable in DSC configuration.  Properties marked this way
        are populated by the Get() method to report additional details
        about the resource when it is present.

    #>
    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $CreationTime

    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)
        if($this.ensure -eq [Ensure]::Present)
        {
            if(-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#

        This method is equivalent of the Test-TargetResource script
        function. It should return True or False, showing whether the
        resource is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
{
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate
        resources. This method returns an instance of this class with the
        updated key properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }
        return $this
    }

    <#
        Helper method to check if the file exists and it is correct file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ea Ignore
        if ($item -eq $null)
        {
            $present = $false
        }
        elseif( $item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }
        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if(-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo]
        $destFileInfo = new-object System.IO.FileInfo($this.Path)

        if (-not $destFileInfo.Directory.Exists)
        {
            $FullName = $destFileInfo.Directory.FullName
            $Message = "Creating directory $FullName"

            Write-Verbose -Message $Message

            #use CreateDirectory instead of New-Item to avoid code
            # to handle the non-terminating error
            [System.IO.Directory]::CreateDirectory($FullName)
        }

        if(Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $this.SourcePath to $this.Path"

        #DSC engine catches and reports any error that occurs
        Copy-Item -Path $this.SourcePath -Destination $this.Path -Force
    }
}
# This module defines a class for a DSC "FileResource" provider.

enum Ensure
{
    Absent
    Present
}

<# This resource manages the file in a specific path.
[DscResource()] indicates the class is a DSC resource
#>

[DscResource()]
class FileResource{

    <# This is a key property
        [DscResourceKey()] also means the property is required.
        It is guaranteed to be set, other properties may not
        be set if the configuration did not specify values.
    #>
    [DscResourceKey()]
    [string]$Path

    <#
        [DscResourceMandatory()] means the property is required.
        It is guaranteed to be set, other properties may not be set
        if the configuration did not specify values.
    #>
    [DscResourceMandatory()]
    [Ensure] $Ensure

    <#
        [DscResourceMandatory()] means the property is required.
    #>
    [DscResourceMandatory()]
    [string] $SourcePath

    [DscResource

    <#
        This method replaces the Set-TargetResource DSC script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = Test-Path -path $this.Path -PathType Leaf
        if($this.ensure -eq [Ensure]::Present)
        {
            if(-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if($fileExists)
            {
                Write-Verbose -Message "Deleting the file $this.Path"
                Remove-Item -LiteralPath $this.Path
            }
        }
    }

    <#

        This method replaces the Test-TargetResource function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>

    [bool] Test()
    {
        if(Test-Path -path $this.Path -PathType Container)
        {
            throw "Path '$this.Path' is a directory path."
        }

        $fileExists = Test-Path -path $this.Path -PathType Leaf

        if($this.ensure -eq [Ensure]::Present)
        {
            return $fileExists
        }

        return (-not $fileExists)
    }

    <#
        This method replaces the Get-TargetResource function.
        The implementation should use the keys to find appropriate
        resources. This method returns an instance of this class with the
        updated key properties.
    #>

    [FileResource] Get()
    {
        $file = Get-item $this.Path
        return $this
    }

    <#
        Helper method to copy file from source to path.
        Because this resource provider run under system,
        Only the Administrators and system have full
        access to the new created directory and file
    #>
    CopyFile()
    {
        if(Test-Path -path $this.SourcePath -PathType Container)
        {
            throw "SourcePath '$this.SourcePath' is a directory path"
        }

        if( -not (Test-Path -path $this.SourcePath -PathType Leaf))
        {
            throw "SourcePath '$this.SourcePath' is not found."
        }

        [System.IO.FileInfo]
        $destFileInfo = new-object System.IO.FileInfo($this.Path)

        if (-not $destFileInfo.Directory.Exists)
        {
            $FullName = $destFileInfo.Directory.FullName
            $Message = "Creating directory $FullName"

            Write-Verbose -Message $Message

            #use CreateDirectory instead of New-Item to avoid lines
            # to handle the non-terminating error
            [System.IO.Directory]::CreateDirectory($FullName)
        }

        if(Test-Path -path $this.Path -PathType Container)
        {
            throw "Path '$this.Path' is a directory path"
        }

        Write-Verbose -Message "Copying $this.SourcePath to $this.Path"

        #DSC engine catches and reports any error that occurs
        Copy-Item -Path $this.SourcePath -Destination $this.Path -Force
    }
}
```

## <a name="create-a-module-manifest"></a>建立模組資訊清單

在建立以類別為基礎的 DSC 資源提供者，並將它儲存為模組之後，為模組建立模組資訊清單。 若要向 DSC 引擎提供以類別為基礎的資源，指示模組匯出資源的資訊清單檔中必須包含 `DscResourcesToExport` 陳述式。 在此範例中，下列的模組資訊清單會儲存為 MyDscResource.psd1。

```powershell
@{

# Script module or binary module file associated with this manifest.
RootModule = 'MyDscResource.psm1'

DscResourcesToExport = 'FileResource'

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '81624038-5e71-40f8-8905-b1a87afe22d7'

# Author of this module
Author = 'Microsoft Corporation'

# Company or vendor of this module
CompanyName = 'Microsoft Corporation'

# Copyright statement for this module
Copyright = '(c) 2014 Microsoft. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the PowerShell engine required by this module
PowerShellVersion = '5.0'

# Name of the PowerShell host required by this module
# PowerShellHostName = ''

}
```

## <a name="deploy-a-dsc-resource-provider"></a>部署 DSC 資源提供者

在或中建立 >mydscresource 資料夾，以部署新的 DSC 資源提供者 `$pshome\Modules` `$env:SystemDrive\ProgramFiles\WindowsPowerShell\Modules` 。

您不需要建立 DSCResource 子資料夾。 將模組和模組資訊清單檔案複製 (MyDscResource.psm1 和 MyDscResource.psd1) 到 MyDscResource 資料夾。

從現在開始，您可以如同使用任何 DSC 資源一般的建立和執行設定指令碼。

## <a name="create-a-dsc-configuration-script"></a>建立 DSC 設定指令碼

如前文所述將類別和資訊清單檔儲存在資料夾結構中後，您就可以建立使用新資源的設定。 下列設定會參考 >mydscresource 模組。 將設定儲存為腳本，MyResource.ps1。

如需有關如何執行 DSC 設定的詳細資訊，請參閱 [Windows PowerShell Desired State Configuration 總覽](/powershell/scripting/dsc/overview/dscforengineers)。

執行設定之前，請先建立 `C:\test.txt` 。 設定會檢查檔案是否存在於 `c:\test\test.txt` 。 如果檔案不存在，則設定會從複製檔案 `C:\test.txt` 。

```powershell
Configuration Test
{
    Import-DSCResource -module MyDscResource
    FileResource file
    {
        Path = "C:\test\test.txt"
        SourcePath = "C:\test.txt"
        Ensure = "Present"
    }
}
Test
Start-DscConfiguration -Wait -Force Test
```

如同執行任何 DSC 設定腳本一樣，執行此腳本。 若要開始設定，請在提升許可權的 PowerShell 主控台中執行下列程式：

`PS C:\test> .\MyResource.ps1`

## <a name="inheritance-in-powershell-classes"></a>PowerShell 類別中的繼承

### <a name="declare-base-classes-for-powershell-classes"></a>宣告 PowerShell 類別的基類

您可以將 PowerShell 類別宣告為另一個 PowerShell 類別的基底類型，如下列範例所示，其中 **水果** 是 **apple** 的基底類型。

```powershell
class fruit
{
    [int]sold() {return 100500}
}

class apple : fruit {}
    [apple]::new().sold() # return 100500
```

### <a name="declare-implemented-interfaces-for-powershell-classes"></a>宣告 PowerShell 類別的實作為介面

`:`如果未指定基底類型，您可以在基底類型之後，或緊接在冒號 () 之後，宣告已執行的介面。 使用逗號分隔所有類型名稱。 這類似于 c # 語法。

```powershell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableTest : test, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

### <a name="call-base-class-constructors"></a>呼叫基類的函式

若要從子類別呼叫基類的函式，請加入 `base` 關鍵字，如下列範例所示：

```powershell
class A {
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

如果基類有預設的函式 (沒有任何參數) ，您可以省略明確的函式呼叫，如下所示。

```powershell
class C : B
{
    C([int]$c) {}
}
```

### <a name="call-base-class-methods"></a>呼叫基類方法

您可以覆寫子類別中現有的方法。 若要進行覆寫，請使用相同的名稱和簽章宣告方法。

```powershell
class baseClass
{
    [int]days() {return 100500}
}
class childClass1 : baseClass
{
    [int]days () {return 200600}
}

    [childClass1]::new().days() # return 200600
```

若要從覆寫的實作為呼叫基類方法，請在叫用時轉換成基類 `([baseclass]$this)` 。

```powershell
class childClass2 : baseClass
{
    [int]days()
    {
        return 3 * ([baseClass]$this).days()
    }
}

    [childClass2]::new().days() # return 301500
```

所有的 PowerShell 方法都是虛擬的。 您可以使用與覆寫相同的語法，在子類別中隱藏非虛擬的 .NET 方法：宣告具有相同名稱和簽章的方法。

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

### <a name="current-limitations-with-class-inheritance"></a>類別繼承目前的限制

類別繼承的限制是沒有任何語法可在 PowerShell 中宣告介面。

## <a name="defining-custom-types-in-powershell"></a>在 PowerShell 中定義自訂類型

Windows PowerShell 5.0 引進了數種語言元素。

### <a name="class-keyword"></a>Class 關鍵字

定義新的類別。
`class`關鍵字是真正的 .NET Framework 類型。
類別成員是公用的。

```powershell
class MyClass
{
}
```

### <a name="enum-keyword-and-enumerations"></a>Enum 關鍵字和列舉

已 `enum` 新增關鍵字的支援，而且是重大變更。 `enum`分隔符號目前為新行。 已使用之使用者的因應措施 `enum` 是在單字之前 () 插入連字號 `&` 。 目前的限制：您無法根據其本身來定義列舉值，但您可以根據 `enum` 另一個來初始化 `enum` ，如下列範例所示：

目前無法指定基底類型。 基底類型一律為 [int]。

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

列舉程式值必須是剖析時間常數。 列舉值不能設定為叫用命令的結果。

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

`Enum` 支援算數運算，如下列範例所示：

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="hidden-keyword"></a>Hidden 關鍵字

`hidden`在 Windows PowerShell 5.0 中引進的關鍵字會從預設結果中隱藏類別成員 `Get-Member` 。 指定隱藏的屬性，如下行所示：

```powershell
hidden [type] $classmember = <value>
```

除非在定義隱藏成員的類別中發生完成，否則不會使用 tab 鍵自動完成或 IntelliSense 來顯示隱藏的成員。

已新增新的屬性 **>system.management.automation.hiddenattribute** ，因此 c # 程式碼在 PowerShell 內可以有相同的語法。

如需詳細資訊，請參閱 [about_Hidden](../../Microsoft.PowerShell.Core/About/about_hidden.md)。

### <a name="import-dscresource"></a>Import-DscResource

`Import-DscResource` 現在是真正的動態關鍵字。 PowerShell 會剖析所指定模組的根模組，其會搜尋包含 DscResource 屬性的類別。

### <a name="properties"></a>屬性

已將新欄位新增 `ImplementingAssembly` 至 `ModuleInfo` 。 如果腳本定義類別，或二進位模組的載入元件 `ImplementingAssembly` 設定為腳本模組所建立的動態元件，則為。 當 ModuleType = Manifest 時不設定。

欄位上的反映會 `ImplementingAssembly` 探索模組中的資源。 這表示您可以探索以 PowerShell 或其他 Managed 語言撰寫的資源。

具有初始化運算式的欄位。

`[int] $i = 5`

靜態是支援的，且類似于類型條件約束的屬性，因此可依任何順序指定。

`static [int] $count = 0`

類型是選用項目。

`$s = "hello"`

所有成員都是公用的。 屬性需要新行字元或分號。 如果未指定任何物件類型，則屬性類型為 **object** 。

### <a name="constructors-and-instantiation"></a>建構函式和實例

PowerShell 類別可以有與類別名稱相同的函式。 可以多載建構函式。 支援靜態的建構函式。
使用初始化運算式的屬性會先初始化，然後建構函式中的所有程式碼才執行。 靜態屬性會在靜態建構函式主體之前初始化，執行個體屬性則在非靜態建構函式主體之前初始化。 目前沒有任何語法可從另一個函式呼叫函式，例如 c # 語法： `": this()")` 。 因應措施是定義通用的 Init 方法。

以下是具現化類別的方式：

- 使用預設的建構函式建立實例。 請注意， `New-Object` 這個版本不支援。

  `$a = [MyClass]::new()`

- 使用參數呼叫函式。

  `$b = [MyClass]::new(42)`

- 將陣列傳遞至有多個參數的建構函式

  `$c = [MyClass]::new(@(42,43,44), "Hello")`

在這個版本中，型別名稱只會以詞法的方式顯示，這表示它不會顯示在定義類別的模組或腳本外部。 函式可以傳回 PowerShell 中定義之類別的實例，而實例可在模組或腳本之外正常運作。

`Get-Member`**靜態** 參數會列出函式，因此您可以像任何其他方法一樣查看多載。 這個語法的效能也比 `New-Object` 快得多。

名為 **new** 的 Pseudo-static 方法可搭配 .NET 類型，如下例所示。 `[hashtable]::new()`

您現在可以使用 `Get-Member` 來查看建構函式多載，或如下列範例所示：

```powershell
[hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

### <a name="methods"></a>方法

PowerShell 類別方法會實作為只有 End 區塊的 **ScriptBlock** 。 所有方法都是公用的。 下例說明定義名為 **DoSomething** 的方法。

```powershell
class MyClass
{
    DoSomething($x)
    {
        $this._doSomething($x)       # method syntax
    }
    private _doSomething($a) {}
}
```

### <a name="method-invocation"></a>方法引動過程

支援多載的方法。 多載方法的命名方式與現有的方法相同，但以其指定的值來區分。

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

### <a name="invocation"></a>引動過程

請參閱 [方法調用](#method-invocation)。

### <a name="attributes"></a>屬性

已新增三個新屬性： `DscResource` 、 `DscResourceKey` 和 `DscResourceMandatory` 。

### <a name="return-types"></a>傳回類型

傳回類型是一個合約。 傳回值會轉換成預期的類型。
如未指定任何傳回類型，傳回類型為 void。 沒有物件和物件的資料流程可以刻意或意外寫入管線。

### <a name="lexical-scoping-of-variables"></a>變數的語彙範圍

下例說明語彙範圍在這個版本中的運作方式。

```powershell
$d = 42  # Script scope

function bar
{
    $d = 0  # Function scope
    [MyClass]::DoSomething()
}

class MyClass
{
    static [object] DoSomething()
    {
        return $d  # error, not found dynamically
        return $script:d # no error

        $d = $script:d
        return $d # no error, found lexically
    }
}

$v = bar
$v -eq $d # true
```

## <a name="example-create-custom-classes"></a>範例：建立自訂類別

下列範例會建立數個新的自訂類別，以執行 (DSL) 的 HTML 動態樣式表單語言。 此範例會加入 helper 函式來建立特定的元素類型，當做元素類別的一部分，例如標題樣式和資料表，因為類型不能用在模組的範圍之外。

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
        $text += $Head
        $text += "`n</head>`n<body>`n"
        $text += $Body -join "`n" # Render all of the body elements
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
    [string] Render() { return "<title>$Title</title>" }
    [string] ToString() { return $this.Render() }
}

class Element
{
    [string] $Tag
    [string] $Text
    [hashtable] $Attributes
    [string] Render() {
        $attributesText= ""
        if ($Attributes)
        {
            foreach ($attr in $Attributes.Keys)
            {
                $attributesText = " $attr=`"$($Attributes[$attr])`""
            }
        }

        return "<${tag}${attributesText}>$text</$tag>`n"
    }
    [string] ToString() { return $this.Render() }
}

#
# Helper functions for creating specific element types on top of the classes.
# These are required because types aren't visible outside of the module.
#
function H1 {[Element] @{Tag = "H1"; Text = $args.foreach{$_} -join " "}}
function H2 {[Element] @{Tag = "H2"; Text = $args.foreach{$_} -join " "}}
function H3 {[Element] @{Tag = "H3"; Text = $args.foreach{$_} -join " "}}
function P  {[Element] @{Tag = "P" ; Text = $args.foreach{$_} -join " "}}
function B  {[Element] @{Tag = "B" ; Text = $args.foreach{$_} -join " "}}
function I  {[Element] @{Tag = "I" ; Text = $args.foreach{$_} -join " "}}
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
    $bodyText +=  $Properties.foreach{TH $_}
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
function TH  {([Element] @{Tag="TH"; Text=$args.foreach{$_} -join " "})}
function TR  {([Element] @{Tag="TR"; Text=$args.foreach{$_} -join " "})}
function TD  {([Element] @{Tag="TD"; Text=$args.foreach{$_} -join " "})}

function Style
{
    return  [Element]  @{
        Tag = "style"
        Text = "$args"
    }
}

# Takes a hash table, casts it to and HTML document
# and then returns the resulting type.
#
function Html ([HTML] $doc) { return $doc }
```

## <a name="see-also"></a>另請參閱

[about_Enum](../../Microsoft.PowerShell.Core/About/about_Enum.md)

[about_Hidden](../../Microsoft.PowerShell.Core/About/about_hidden.md)

[about_Language_Keywords](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[about_Methods](../../Microsoft.PowerShell.Core/About/about_Methods.md)

[建立自訂的 PowerShell Desired State Configuration 資源](/powershell/scripting/dsc/resources/authoringResource)
