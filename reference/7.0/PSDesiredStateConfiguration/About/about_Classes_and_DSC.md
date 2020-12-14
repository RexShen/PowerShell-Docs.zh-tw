---
description: 說明如何使用類別，在 PowerShell 中使用 Desired State Configuration (DSC) 來進行開發。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 1/11/2019
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Classes_and_DSC
ms.openlocfilehash: 00a7d18bb1ccf618b22b61d2197053365ea3f21b
ms.sourcegitcommit: cc72c40315fd2981d3009b335accbfa52d57640c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/30/2020
ms.locfileid: "96349784"
---
# <a name="about-classes-and-desired-state-configuration"></a><span data-ttu-id="f33ce-104">關於類別和 Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="f33ce-104">About Classes and Desired State Configuration</span></span>

## <a name="short-description"></a><span data-ttu-id="f33ce-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="f33ce-105">Short description</span></span>

<span data-ttu-id="f33ce-106">說明如何使用類別，在 PowerShell 中使用 Desired State Configuration (DSC) 來進行開發。</span><span class="sxs-lookup"><span data-stu-id="f33ce-106">Describes how you can use classes to develop in PowerShell with Desired State Configuration (DSC).</span></span>

## <a name="long-description"></a><span data-ttu-id="f33ce-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="f33ce-107">Long description</span></span>

<span data-ttu-id="f33ce-108">從 Windows PowerShell 5.0 開始，使用類似其他物件導向程式設計語言的正式語法和語義，新增了語言來定義類別和其他使用者定義類型。</span><span class="sxs-lookup"><span data-stu-id="f33ce-108">Starting in Windows PowerShell 5.0, language was added to define classes and other user-defined types, by using formal syntax and semantics that are similar to other object-oriented programming languages.</span></span> <span data-ttu-id="f33ce-109">目標是要讓開發人員和 IT 專業人員能夠將 PowerShell 用於更廣泛的使用案例、簡化 PowerShell 成品的開發（例如 DSC 資源），以及加快管理面的涵蓋範圍。</span><span class="sxs-lookup"><span data-stu-id="f33ce-109">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts such as DSC resources, and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios"></a><span data-ttu-id="f33ce-110">支援的案例</span><span class="sxs-lookup"><span data-stu-id="f33ce-110">Supported scenarios</span></span>

<span data-ttu-id="f33ce-111">以下是支援的案例：</span><span class="sxs-lookup"><span data-stu-id="f33ce-111">The following scenarios are supported:</span></span>

- <span data-ttu-id="f33ce-112">使用 PowerShell 語言定義 DSC 資源及其相關聯的類型。</span><span class="sxs-lookup"><span data-stu-id="f33ce-112">Define DSC resources and their associated types by using the PowerShell language.</span></span>
- <span data-ttu-id="f33ce-113">使用熟悉的物件導向程式設計結構（例如類別、屬性、方法和繼承），在 PowerShell 中定義自訂類型。</span><span class="sxs-lookup"><span data-stu-id="f33ce-113">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, and inheritance.</span></span>
- <span data-ttu-id="f33ce-114">使用 PowerShell 語言的偵錯工具類型。</span><span class="sxs-lookup"><span data-stu-id="f33ce-114">Debug types by using the PowerShell language.</span></span>
- <span data-ttu-id="f33ce-115">使用正式的機制和適當層級來產生和處理例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f33ce-115">Generate and handle exceptions by using formal mechanisms, and at the right level.</span></span>

## <a name="define-dsc-resources-with-classes"></a><span data-ttu-id="f33ce-116">使用類別定義 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="f33ce-116">Define DSC resources with classes</span></span>

<span data-ttu-id="f33ce-117">除了語法變更以外，類別定義的 DSC 資源和 Cmdlet DSC 資源提供者之間的主要差異如下：</span><span class="sxs-lookup"><span data-stu-id="f33ce-117">Apart from syntax changes, the major differences between a class-defined DSC resource and a cmdlet DSC resource provider are the following items:</span></span>

- <span data-ttu-id="f33ce-118">不需要 (MOF) 檔的管理物件格式。</span><span class="sxs-lookup"><span data-stu-id="f33ce-118">A Management Object Format (MOF) file is not required.</span></span>
- <span data-ttu-id="f33ce-119">不需要模組資料夾中的 DSCResource 子資料夾。</span><span class="sxs-lookup"><span data-stu-id="f33ce-119">A DSCResource subfolder in the module folder is not required.</span></span>
- <span data-ttu-id="f33ce-120">PowerShell 模組檔案可以包含多個 DSC 資源類別。</span><span class="sxs-lookup"><span data-stu-id="f33ce-120">A PowerShell module file can contain multiple DSC resource classes.</span></span>

## <a name="create-a-class-defined-dsc-resource-provider"></a><span data-ttu-id="f33ce-121">建立類別定義的 DSC 資源提供者</span><span class="sxs-lookup"><span data-stu-id="f33ce-121">Create a class-defined DSC resource provider</span></span>

<span data-ttu-id="f33ce-122">下列範例是以模組 >mydscresource .psm1 儲存的類別定義 DSC 資源提供者。</span><span class="sxs-lookup"><span data-stu-id="f33ce-122">The following example is a class-defined DSC resource provider that is saved as a module, MyDSCResource.psm1.</span></span> <span data-ttu-id="f33ce-123">您必須一律在類別定義的 DSC 資源提供者中包含索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="f33ce-123">You must always include a key property in a class-defined DSC resource provider.</span></span>

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
        if ($null -eq $item)
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
```

## <a name="create-a-module-manifest"></a><span data-ttu-id="f33ce-124">建立模組資訊清單</span><span class="sxs-lookup"><span data-stu-id="f33ce-124">Create a module manifest</span></span>

<span data-ttu-id="f33ce-125">在建立以類別為基礎的 DSC 資源提供者，並將它儲存為模組之後，為模組建立模組資訊清單。</span><span class="sxs-lookup"><span data-stu-id="f33ce-125">After creating the class-defined DSC resource provider, and saving it as a module, create a module manifest for the module.</span></span> <span data-ttu-id="f33ce-126">若要向 DSC 引擎提供以類別為基礎的資源，指示模組匯出資源的資訊清單檔中必須包含 `DscResourcesToExport` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="f33ce-126">To make a class-based resource available to the DSC engine, you must include a `DscResourcesToExport` statement in the manifest file that instructs the module to export the resource.</span></span> <span data-ttu-id="f33ce-127">在此範例中，下列的模組資訊清單會儲存為 MyDscResource.psd1。</span><span class="sxs-lookup"><span data-stu-id="f33ce-127">In this example, the following module manifest is saved as MyDscResource.psd1.</span></span>

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

## <a name="deploy-a-dsc-resource-provider"></a><span data-ttu-id="f33ce-128">部署 DSC 資源提供者</span><span class="sxs-lookup"><span data-stu-id="f33ce-128">Deploy a DSC resource provider</span></span>

<span data-ttu-id="f33ce-129">在或中建立 >mydscresource 資料夾，以部署新的 DSC 資源提供者 `$pshome\Modules` `$env:SystemDrive\ProgramFiles\WindowsPowerShell\Modules` 。</span><span class="sxs-lookup"><span data-stu-id="f33ce-129">Deploy the new DSC resource provider by creating a MyDscResource folder in `$pshome\Modules` or `$env:SystemDrive\ProgramFiles\WindowsPowerShell\Modules`.</span></span>

<span data-ttu-id="f33ce-130">您不需要建立 DSCResource 子資料夾。</span><span class="sxs-lookup"><span data-stu-id="f33ce-130">You do not need to create a DSCResource subfolder.</span></span> <span data-ttu-id="f33ce-131">將模組和模組資訊清單檔案複製 (MyDscResource.psm1 和 MyDscResource.psd1) 到 MyDscResource 資料夾。</span><span class="sxs-lookup"><span data-stu-id="f33ce-131">Copy the module and module manifest files (MyDscResource.psm1 and MyDscResource.psd1) to the MyDscResource folder.</span></span>

<span data-ttu-id="f33ce-132">從現在開始，您可以如同使用任何 DSC 資源一般的建立和執行設定指令碼。</span><span class="sxs-lookup"><span data-stu-id="f33ce-132">From this point, you create and run a configuration script as you would with any DSC resource.</span></span>

## <a name="create-a-dsc-configuration-script"></a><span data-ttu-id="f33ce-133">建立 DSC 設定指令碼</span><span class="sxs-lookup"><span data-stu-id="f33ce-133">Create a DSC configuration script</span></span>

<span data-ttu-id="f33ce-134">如前文所述將類別和資訊清單檔儲存在資料夾結構中後，您就可以建立使用新資源的設定。</span><span class="sxs-lookup"><span data-stu-id="f33ce-134">After saving the class and manifest files in the folder structure as described earlier, you can create a configuration that uses the new resource.</span></span> <span data-ttu-id="f33ce-135">下列設定會參考 >mydscresource 模組。</span><span class="sxs-lookup"><span data-stu-id="f33ce-135">The following configuration references the MyDSCResource module.</span></span> <span data-ttu-id="f33ce-136">將設定儲存為腳本，MyResource.ps1。</span><span class="sxs-lookup"><span data-stu-id="f33ce-136">Save the configuration as a script, MyResource.ps1.</span></span>

<span data-ttu-id="f33ce-137">如需有關如何執行 DSC 設定的詳細資訊，請參閱 [Windows PowerShell Desired State Configuration 總覽](/powershell/scripting/dsc/overview/dscforengineers)。</span><span class="sxs-lookup"><span data-stu-id="f33ce-137">For information about how to run a DSC configuration, see [Windows PowerShell Desired State Configuration Overview](/powershell/scripting/dsc/overview/dscforengineers).</span></span>

<span data-ttu-id="f33ce-138">執行設定之前，請先建立 `C:\test.txt` 。</span><span class="sxs-lookup"><span data-stu-id="f33ce-138">Before you run the configuration, create `C:\test.txt`.</span></span> <span data-ttu-id="f33ce-139">設定會檢查檔案是否存在於 `c:\test\test.txt` 。</span><span class="sxs-lookup"><span data-stu-id="f33ce-139">The configuration checks if the file exists at `c:\test\test.txt`.</span></span> <span data-ttu-id="f33ce-140">如果檔案不存在，則設定會從複製檔案 `C:\test.txt` 。</span><span class="sxs-lookup"><span data-stu-id="f33ce-140">If the file does not exist, the configuration copies the file from `C:\test.txt`.</span></span>

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

<span data-ttu-id="f33ce-141">如同執行任何 DSC 設定腳本一樣，執行此腳本。</span><span class="sxs-lookup"><span data-stu-id="f33ce-141">Run this script as you would any DSC configuration script.</span></span> <span data-ttu-id="f33ce-142">若要開始設定，請在提升許可權的 PowerShell 主控台中執行下列程式：</span><span class="sxs-lookup"><span data-stu-id="f33ce-142">To start the configuration, in an elevated PowerShell console, run the following:</span></span>

`PS C:\test> .\MyResource.ps1`

## <a name="inheritance-in-powershell-classes"></a><span data-ttu-id="f33ce-143">PowerShell 類別中的繼承</span><span class="sxs-lookup"><span data-stu-id="f33ce-143">Inheritance in PowerShell classes</span></span>

### <a name="declare-base-classes-for-powershell-classes"></a><span data-ttu-id="f33ce-144">宣告 PowerShell 類別的基類</span><span class="sxs-lookup"><span data-stu-id="f33ce-144">Declare base classes for PowerShell classes</span></span>

<span data-ttu-id="f33ce-145">您可以將 PowerShell 類別宣告為另一個 PowerShell 類別的基底類型，如下列範例所示，其中 **水果** 是 **apple** 的基底類型。</span><span class="sxs-lookup"><span data-stu-id="f33ce-145">You can declare a PowerShell class as a base type for another PowerShell class, as shown in the following example, in which **fruit** is a base type for **apple**.</span></span>

```powershell
class fruit
{
    [int]sold() {return 100500}
}

class apple : fruit {}
    [apple]::new().sold() # return 100500
```

### <a name="declare-implemented-interfaces-for-powershell-classes"></a><span data-ttu-id="f33ce-146">宣告 PowerShell 類別的實作為介面</span><span class="sxs-lookup"><span data-stu-id="f33ce-146">Declare implemented interfaces for PowerShell classes</span></span>

<span data-ttu-id="f33ce-147">`:`如果未指定基底類型，您可以在基底類型之後，或緊接在冒號 () 之後，宣告已執行的介面。</span><span class="sxs-lookup"><span data-stu-id="f33ce-147">You can declare implemented interfaces after base types, or immediately after a colon (`:`) if there is no base type specified.</span></span> <span data-ttu-id="f33ce-148">使用逗號分隔所有類型名稱。</span><span class="sxs-lookup"><span data-stu-id="f33ce-148">Separate all type names by using commas.</span></span> <span data-ttu-id="f33ce-149">這類似于 c # 語法。</span><span class="sxs-lookup"><span data-stu-id="f33ce-149">This is similar to C# syntax.</span></span>

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

### <a name="call-base-class-constructors"></a><span data-ttu-id="f33ce-150">呼叫基類的函式</span><span class="sxs-lookup"><span data-stu-id="f33ce-150">Call base class constructors</span></span>

<span data-ttu-id="f33ce-151">若要從子類別呼叫基類的函式，請加入 `base` 關鍵字，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="f33ce-151">To call a base class constructor from a subclass, add the `base` keyword, as shown in the following example:</span></span>

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

<span data-ttu-id="f33ce-152">如果基類有預設的函式 (沒有任何參數) ，您可以省略明確的函式呼叫，如下所示。</span><span class="sxs-lookup"><span data-stu-id="f33ce-152">If a base class has a default constructor (no parameters), you can omit an explicit constructor call, as shown.</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```

### <a name="call-base-class-methods"></a><span data-ttu-id="f33ce-153">呼叫基類方法</span><span class="sxs-lookup"><span data-stu-id="f33ce-153">Call base class methods</span></span>

<span data-ttu-id="f33ce-154">您可以覆寫子類別中現有的方法。</span><span class="sxs-lookup"><span data-stu-id="f33ce-154">You can override existing methods in subclasses.</span></span> <span data-ttu-id="f33ce-155">若要進行覆寫，請使用相同的名稱和簽章宣告方法。</span><span class="sxs-lookup"><span data-stu-id="f33ce-155">To do the override, declare methods by using the same name and signature.</span></span>

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

<span data-ttu-id="f33ce-156">若要從覆寫的實作為呼叫基類方法，請在叫用時轉換成基類 `([baseclass]$this)` 。</span><span class="sxs-lookup"><span data-stu-id="f33ce-156">To call base class methods from overridden implementations, cast to the base class `([baseclass]$this)` on invocation.</span></span>

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

<span data-ttu-id="f33ce-157">所有的 PowerShell 方法都是虛擬的。</span><span class="sxs-lookup"><span data-stu-id="f33ce-157">All PowerShell methods are virtual.</span></span> <span data-ttu-id="f33ce-158">您可以使用與覆寫相同的語法，在子類別中隱藏非虛擬的 .NET 方法：宣告具有相同名稱和簽章的方法。</span><span class="sxs-lookup"><span data-stu-id="f33ce-158">You can hide non-virtual .NET methods in a subclass by using the same syntax as you do for an override: declare methods with same name and signature.</span></span>

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

### <a name="current-limitations-with-class-inheritance"></a><span data-ttu-id="f33ce-159">類別繼承目前的限制</span><span class="sxs-lookup"><span data-stu-id="f33ce-159">Current limitations with class inheritance</span></span>

<span data-ttu-id="f33ce-160">類別繼承的限制是沒有任何語法可在 PowerShell 中宣告介面。</span><span class="sxs-lookup"><span data-stu-id="f33ce-160">A limitation with class inheritance is that there is no syntax to declare interfaces in PowerShell.</span></span>

## <a name="defining-custom-types-in-powershell"></a><span data-ttu-id="f33ce-161">在 PowerShell 中定義自訂類型</span><span class="sxs-lookup"><span data-stu-id="f33ce-161">Defining custom types in PowerShell</span></span>

<span data-ttu-id="f33ce-162">Windows PowerShell 5.0 引進了數種語言元素。</span><span class="sxs-lookup"><span data-stu-id="f33ce-162">Windows PowerShell 5.0 introduced several language elements.</span></span>

### <a name="class-keyword"></a><span data-ttu-id="f33ce-163">Class 關鍵字</span><span class="sxs-lookup"><span data-stu-id="f33ce-163">Class keyword</span></span>

<span data-ttu-id="f33ce-164">定義新的類別。</span><span class="sxs-lookup"><span data-stu-id="f33ce-164">Defines a new class.</span></span>
<span data-ttu-id="f33ce-165">`class`關鍵字是真正的 .NET Framework 類型。</span><span class="sxs-lookup"><span data-stu-id="f33ce-165">The `class` keyword is a true .NET Framework type.</span></span>
<span data-ttu-id="f33ce-166">類別成員是公用的。</span><span class="sxs-lookup"><span data-stu-id="f33ce-166">Class members are public.</span></span>

```powershell
class MyClass
{
}
```

### <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="f33ce-167">Enum 關鍵字和列舉</span><span class="sxs-lookup"><span data-stu-id="f33ce-167">Enum keyword and enumerations</span></span>

<span data-ttu-id="f33ce-168">已 `enum` 新增關鍵字的支援，而且是重大變更。</span><span class="sxs-lookup"><span data-stu-id="f33ce-168">Support for the `enum` keyword was added and is a breaking change.</span></span> <span data-ttu-id="f33ce-169">`enum`分隔符號目前為新行。</span><span class="sxs-lookup"><span data-stu-id="f33ce-169">The `enum` delimiter is currently a newline.</span></span> <span data-ttu-id="f33ce-170">已使用之使用者的因應措施 `enum` 是在單字之前 () 插入連字號 `&` 。</span><span class="sxs-lookup"><span data-stu-id="f33ce-170">A workaround for those who are already using `enum` is to insert an ampersand (`&`) before the word.</span></span> <span data-ttu-id="f33ce-171">目前的限制：您無法根據其本身來定義列舉值，但您可以根據 `enum` 另一個來初始化 `enum` ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="f33ce-171">Current limitations: you cannot define an enumerator in terms of itself, but you can initialize `enum` in terms of another `enum`, as shown in the following example:</span></span>

<span data-ttu-id="f33ce-172">目前無法指定基底類型。</span><span class="sxs-lookup"><span data-stu-id="f33ce-172">The base type cannot currently be specified.</span></span> <span data-ttu-id="f33ce-173">基底類型一律為 [int]。</span><span class="sxs-lookup"><span data-stu-id="f33ce-173">The base type is always [int].</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="f33ce-174">列舉程式值必須是剖析時間常數。</span><span class="sxs-lookup"><span data-stu-id="f33ce-174">An enumerator value must be a parse time constant.</span></span> <span data-ttu-id="f33ce-175">列舉值不能設定為叫用命令的結果。</span><span class="sxs-lookup"><span data-stu-id="f33ce-175">The enumerator value cannot be set to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="f33ce-176">`Enum` 支援算數運算，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="f33ce-176">`Enum` supports arithmetic operations, as shown in the following example:</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="hidden-keyword"></a><span data-ttu-id="f33ce-177">Hidden 關鍵字</span><span class="sxs-lookup"><span data-stu-id="f33ce-177">Hidden keyword</span></span>

<span data-ttu-id="f33ce-178">`hidden`在 Windows PowerShell 5.0 中引進的關鍵字會從預設結果中隱藏類別成員 `Get-Member` 。</span><span class="sxs-lookup"><span data-stu-id="f33ce-178">The `hidden` keyword, introduced in Windows PowerShell 5.0, hides class members from default `Get-Member` results.</span></span> <span data-ttu-id="f33ce-179">指定隱藏的屬性，如下行所示：</span><span class="sxs-lookup"><span data-stu-id="f33ce-179">Specify the hidden property as shown in the following line:</span></span>

```powershell
hidden [type] $classmember = <value>
```

<span data-ttu-id="f33ce-180">除非在定義隱藏成員的類別中發生完成，否則不會使用 tab 鍵自動完成或 IntelliSense 來顯示隱藏的成員。</span><span class="sxs-lookup"><span data-stu-id="f33ce-180">Hidden members are not displayed by using tab completion or IntelliSense, unless the completion occurs in the class that defines the hidden member.</span></span>

<span data-ttu-id="f33ce-181">已新增新的屬性 **>system.management.automation.hiddenattribute**，因此 c # 程式碼在 PowerShell 內可以有相同的語法。</span><span class="sxs-lookup"><span data-stu-id="f33ce-181">A new attribute, **System.Management.Automation.HiddenAttribute**, was added, so that C# code can have the same semantics within PowerShell.</span></span>

<span data-ttu-id="f33ce-182">如需詳細資訊，請參閱 [about_Hidden](../../Microsoft.PowerShell.Core/About/about_hidden.md)。</span><span class="sxs-lookup"><span data-stu-id="f33ce-182">For more information, see [about_Hidden](../../Microsoft.PowerShell.Core/About/about_hidden.md).</span></span>

### <a name="import-dscresource"></a><span data-ttu-id="f33ce-183">Import-DscResource</span><span class="sxs-lookup"><span data-stu-id="f33ce-183">Import-DscResource</span></span>

<span data-ttu-id="f33ce-184">`Import-DscResource` 現在是真正的動態關鍵字。</span><span class="sxs-lookup"><span data-stu-id="f33ce-184">`Import-DscResource` is now a true dynamic keyword.</span></span> <span data-ttu-id="f33ce-185">PowerShell 會剖析所指定模組的根模組，其會搜尋包含 DscResource 屬性的類別。</span><span class="sxs-lookup"><span data-stu-id="f33ce-185">PowerShell parses the specified module's root module, searching for classes that contain the DscResource attribute.</span></span>

### <a name="properties"></a><span data-ttu-id="f33ce-186">屬性</span><span class="sxs-lookup"><span data-stu-id="f33ce-186">Properties</span></span>

<span data-ttu-id="f33ce-187">已將新欄位新增 `ImplementingAssembly` 至 `ModuleInfo` 。</span><span class="sxs-lookup"><span data-stu-id="f33ce-187">A new field, `ImplementingAssembly`, was added to `ModuleInfo`.</span></span> <span data-ttu-id="f33ce-188">如果腳本定義類別，或二進位模組的載入元件 `ImplementingAssembly` 設定為腳本模組所建立的動態元件，則為。</span><span class="sxs-lookup"><span data-stu-id="f33ce-188">If the script defines classes, or the loaded assembly for binary modules `ImplementingAssembly` is set to the dynamic assembly created for a script module.</span></span> <span data-ttu-id="f33ce-189">當 ModuleType = Manifest 時不設定。</span><span class="sxs-lookup"><span data-stu-id="f33ce-189">It is not set when ModuleType = Manifest.</span></span>

<span data-ttu-id="f33ce-190">欄位上的反映會 `ImplementingAssembly` 探索模組中的資源。</span><span class="sxs-lookup"><span data-stu-id="f33ce-190">Reflection on the `ImplementingAssembly` field discovers resources in a module.</span></span> <span data-ttu-id="f33ce-191">這表示您可以探索以 PowerShell 或其他 Managed 語言撰寫的資源。</span><span class="sxs-lookup"><span data-stu-id="f33ce-191">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

<span data-ttu-id="f33ce-192">具有初始化運算式的欄位。</span><span class="sxs-lookup"><span data-stu-id="f33ce-192">Fields with initializers.</span></span>

`[int] $i = 5`

<span data-ttu-id="f33ce-193">靜態是支援的，且類似于類型條件約束的屬性，因此可依任何順序指定。</span><span class="sxs-lookup"><span data-stu-id="f33ce-193">Static is supported and works like an attribute, similar to the type constraints, so it can be specified in any order.</span></span>

`static [int] $count = 0`

<span data-ttu-id="f33ce-194">類型是選用項目。</span><span class="sxs-lookup"><span data-stu-id="f33ce-194">A type is optional.</span></span>

`$s = "hello"`

<span data-ttu-id="f33ce-195">所有成員都是公用的。</span><span class="sxs-lookup"><span data-stu-id="f33ce-195">All members are public.</span></span> <span data-ttu-id="f33ce-196">屬性需要新行字元或分號。</span><span class="sxs-lookup"><span data-stu-id="f33ce-196">Properties require either a newline or semicolon.</span></span> <span data-ttu-id="f33ce-197">如果未指定任何物件類型，則屬性類型為 **object**。</span><span class="sxs-lookup"><span data-stu-id="f33ce-197">If no object type is specified, the property type is **Object**.</span></span>

### <a name="constructors-and-instantiation"></a><span data-ttu-id="f33ce-198">建構函式和實例</span><span class="sxs-lookup"><span data-stu-id="f33ce-198">Constructors and instantiation</span></span>

<span data-ttu-id="f33ce-199">PowerShell 類別可以有與類別名稱相同的函式。</span><span class="sxs-lookup"><span data-stu-id="f33ce-199">PowerShell classes can have constructors that have the same name as their class.</span></span> <span data-ttu-id="f33ce-200">可以多載建構函式。</span><span class="sxs-lookup"><span data-stu-id="f33ce-200">Constructors can be overloaded.</span></span> <span data-ttu-id="f33ce-201">支援靜態的建構函式。</span><span class="sxs-lookup"><span data-stu-id="f33ce-201">Static constructors are supported.</span></span>
<span data-ttu-id="f33ce-202">使用初始化運算式的屬性會先初始化，然後建構函式中的所有程式碼才執行。</span><span class="sxs-lookup"><span data-stu-id="f33ce-202">Properties with initialization expressions are initialized before running any code in a constructor.</span></span> <span data-ttu-id="f33ce-203">靜態屬性會在靜態建構函式主體之前初始化，執行個體屬性則在非靜態建構函式主體之前初始化。</span><span class="sxs-lookup"><span data-stu-id="f33ce-203">Static properties are initialized before the body of a static constructor, and instance properties are initialized before the body of the non-static constructor.</span></span> <span data-ttu-id="f33ce-204">目前沒有任何語法可從另一個函式呼叫函式，例如 c # 語法： `": this()")` 。</span><span class="sxs-lookup"><span data-stu-id="f33ce-204">Currently, there is no syntax for calling a constructor from another constructor such as the C# syntax: `": this()")`.</span></span> <span data-ttu-id="f33ce-205">因應措施是定義通用的 Init 方法。</span><span class="sxs-lookup"><span data-stu-id="f33ce-205">The workaround is to define a common Init method.</span></span>

<span data-ttu-id="f33ce-206">以下是具現化類別的方式：</span><span class="sxs-lookup"><span data-stu-id="f33ce-206">The following are ways of instantiating classes:</span></span>

- <span data-ttu-id="f33ce-207">使用預設的建構函式建立實例。</span><span class="sxs-lookup"><span data-stu-id="f33ce-207">Instantiating by using the default constructor.</span></span> <span data-ttu-id="f33ce-208">請注意， `New-Object` 這個版本不支援。</span><span class="sxs-lookup"><span data-stu-id="f33ce-208">Note that `New-Object` is not supported in this release.</span></span>

  `$a = [MyClass]::new()`

- <span data-ttu-id="f33ce-209">使用參數呼叫函式。</span><span class="sxs-lookup"><span data-stu-id="f33ce-209">Calling a constructor with a parameter.</span></span>

  `$b = [MyClass]::new(42)`

- <span data-ttu-id="f33ce-210">將陣列傳遞至有多個參數的建構函式</span><span class="sxs-lookup"><span data-stu-id="f33ce-210">Passing an array to a constructor with multiple parameters</span></span>

  `$c = [MyClass]::new(@(42,43,44), "Hello")`

<span data-ttu-id="f33ce-211">在這個版本中，型別名稱只會以詞法的方式顯示，這表示它不會顯示在定義類別的模組或腳本外部。</span><span class="sxs-lookup"><span data-stu-id="f33ce-211">For this release, the type name is only visible lexically, meaning it is not visible outside of the module or script that defines the class.</span></span> <span data-ttu-id="f33ce-212">函式可以傳回 PowerShell 中定義之類別的實例，而實例可在模組或腳本之外正常運作。</span><span class="sxs-lookup"><span data-stu-id="f33ce-212">Functions can return instances of a class defined in PowerShell, and instances work well outside of the module or script.</span></span>

<span data-ttu-id="f33ce-213">`Get-Member`**靜態** 參數會列出函式，因此您可以像任何其他方法一樣查看多載。</span><span class="sxs-lookup"><span data-stu-id="f33ce-213">The `Get-Member` **Static** parameter lists constructors, so you can view overloads like any other method.</span></span> <span data-ttu-id="f33ce-214">這個語法的效能也比 `New-Object` 快得多。</span><span class="sxs-lookup"><span data-stu-id="f33ce-214">The performance of this syntax is also considerably faster than `New-Object`.</span></span>

<span data-ttu-id="f33ce-215">名為 **new** 的 Pseudo-static 方法可搭配 .NET 類型，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="f33ce-215">The pseudo-static method named **new** works with .NET types, as shown in the following example.</span></span> `[hashtable]::new()`

<span data-ttu-id="f33ce-216">您現在可以使用 `Get-Member` 來查看建構函式多載，或如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="f33ce-216">You can now see constructor overloads with `Get-Member`, or as shown in this example:</span></span>

```powershell
[hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

### <a name="methods"></a><span data-ttu-id="f33ce-217">方法</span><span class="sxs-lookup"><span data-stu-id="f33ce-217">Methods</span></span>

<span data-ttu-id="f33ce-218">PowerShell 類別方法會實作為只有 End 區塊的 **ScriptBlock**。</span><span class="sxs-lookup"><span data-stu-id="f33ce-218">A PowerShell class method is implemented as a **ScriptBlock** that has only an end block.</span></span> <span data-ttu-id="f33ce-219">所有方法都是公用的。</span><span class="sxs-lookup"><span data-stu-id="f33ce-219">All methods are public.</span></span> <span data-ttu-id="f33ce-220">下例說明定義名為 **DoSomething** 的方法。</span><span class="sxs-lookup"><span data-stu-id="f33ce-220">The following shows an example of defining a method named **DoSomething**.</span></span>

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

### <a name="method-invocation"></a><span data-ttu-id="f33ce-221">方法引動過程</span><span class="sxs-lookup"><span data-stu-id="f33ce-221">Method invocation</span></span>

<span data-ttu-id="f33ce-222">支援多載的方法。</span><span class="sxs-lookup"><span data-stu-id="f33ce-222">Overloaded methods are supported.</span></span> <span data-ttu-id="f33ce-223">多載方法的命名方式與現有的方法相同，但以其指定的值來區分。</span><span class="sxs-lookup"><span data-stu-id="f33ce-223">Overloaded methods are named the same as an existing method but differentiated by their specified values.</span></span>

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

### <a name="invocation"></a><span data-ttu-id="f33ce-224">引動過程</span><span class="sxs-lookup"><span data-stu-id="f33ce-224">Invocation</span></span>

<span data-ttu-id="f33ce-225">請參閱 [方法調用](#method-invocation)。</span><span class="sxs-lookup"><span data-stu-id="f33ce-225">See [Method invocation](#method-invocation).</span></span>

### <a name="attributes"></a><span data-ttu-id="f33ce-226">屬性</span><span class="sxs-lookup"><span data-stu-id="f33ce-226">Attributes</span></span>

<span data-ttu-id="f33ce-227">已新增三個新屬性： `DscResource` 、 `DscResourceKey` 和 `DscResourceMandatory` 。</span><span class="sxs-lookup"><span data-stu-id="f33ce-227">Three new attributes were added: `DscResource`, `DscResourceKey`, and `DscResourceMandatory`.</span></span>

### <a name="return-types"></a><span data-ttu-id="f33ce-228">傳回類型</span><span class="sxs-lookup"><span data-stu-id="f33ce-228">Return types</span></span>

<span data-ttu-id="f33ce-229">傳回類型是一個合約。</span><span class="sxs-lookup"><span data-stu-id="f33ce-229">Return type is a contract.</span></span> <span data-ttu-id="f33ce-230">傳回值會轉換成預期的類型。</span><span class="sxs-lookup"><span data-stu-id="f33ce-230">The return value is converted to the expected type.</span></span>
<span data-ttu-id="f33ce-231">如未指定任何傳回類型，傳回類型為 void。</span><span class="sxs-lookup"><span data-stu-id="f33ce-231">If no return type is specified, the return type is void.</span></span> <span data-ttu-id="f33ce-232">沒有物件和物件的資料流程可以刻意或意外寫入管線。</span><span class="sxs-lookup"><span data-stu-id="f33ce-232">There is no streaming of objects and objects cannot be written to the pipeline either intentionally or by accident.</span></span>

### <a name="lexical-scoping-of-variables"></a><span data-ttu-id="f33ce-233">變數的語彙範圍</span><span class="sxs-lookup"><span data-stu-id="f33ce-233">Lexical scoping of variables</span></span>

<span data-ttu-id="f33ce-234">下例說明語彙範圍在這個版本中的運作方式。</span><span class="sxs-lookup"><span data-stu-id="f33ce-234">The following shows an example of how lexical scoping works in this release.</span></span>

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

## <a name="example-create-custom-classes"></a><span data-ttu-id="f33ce-235">範例：建立自訂類別</span><span class="sxs-lookup"><span data-stu-id="f33ce-235">Example: Create custom classes</span></span>

<span data-ttu-id="f33ce-236">下列範例會建立數個新的自訂類別，以執行 (DSL) 的 HTML 動態樣式表單語言。</span><span class="sxs-lookup"><span data-stu-id="f33ce-236">The following example creates several new, custom classes to implement an HTML Dynamic Stylesheet Language (DSL).</span></span> <span data-ttu-id="f33ce-237">此範例會加入 helper 函式來建立特定的元素類型，當做元素類別的一部分，例如標題樣式和資料表，因為類型不能用在模組的範圍之外。</span><span class="sxs-lookup"><span data-stu-id="f33ce-237">The example adds helper functions to create specific element types as part of the element class, such as heading styles and tables, because types cannot be used outside the scope of a module.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f33ce-238">請參閱</span><span class="sxs-lookup"><span data-stu-id="f33ce-238">See also</span></span>

[<span data-ttu-id="f33ce-239">about_Enum</span><span class="sxs-lookup"><span data-stu-id="f33ce-239">about_Enum</span></span>](../../Microsoft.PowerShell.Core/About/about_Enum.md)

[<span data-ttu-id="f33ce-240">about_Hidden</span><span class="sxs-lookup"><span data-stu-id="f33ce-240">about_Hidden</span></span>](../../Microsoft.PowerShell.Core/About/about_hidden.md)

[<span data-ttu-id="f33ce-241">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="f33ce-241">about_Language_Keywords</span></span>](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[<span data-ttu-id="f33ce-242">about_Methods</span><span class="sxs-lookup"><span data-stu-id="f33ce-242">about_Methods</span></span>](../../Microsoft.PowerShell.Core/About/about_Methods.md)

[<span data-ttu-id="f33ce-243">建立自訂的 PowerShell Desired State Configuration 資源</span><span class="sxs-lookup"><span data-stu-id="f33ce-243">Build Custom PowerShell Desired State Configuration Resources</span></span>](/powershell/scripting/dsc/resources/authoringResource)
