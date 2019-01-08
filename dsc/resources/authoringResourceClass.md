---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 使用 PowerShell 類別撰寫自訂的 DSC 資源
ms.openlocfilehash: 0759685b04688f574d72b62a15833832ad19e816
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400816"
---
# <a name="writing-a-custom-dsc-resource-with-powershell-classes"></a><span data-ttu-id="bf7af-103">使用 PowerShell 類別撰寫自訂的 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="bf7af-103">Writing a custom DSC resource with PowerShell classes</span></span>

> <span data-ttu-id="bf7af-104">適用於：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="bf7af-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="bf7af-105">您可以利用 Windows PowerShell 5.0 引入的 PowerShell 類別，藉由建立類別來定義 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="bf7af-105">With the introduction of PowerShell classes in Windows PowerShell 5.0, you can now define a DSC resource by creating a class.</span></span> <span data-ttu-id="bf7af-106">類別會定義結構描述和資源實作，所以不必建立個別的 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="bf7af-106">The class defines both the schema and the implementation of the resource, so there is no need to create a separate MOF file.</span></span> <span data-ttu-id="bf7af-107">以類別為基礎的資源資料夾結構也比較簡單，因為不需要 **DSCResources** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="bf7af-107">The folder structure for a class-based resource is also simpler, because a **DSCResources** folder is not necessary.</span></span>

<span data-ttu-id="bf7af-108">在以類別為基礎的 DSC 資源中，結構描述會定義為類別屬性，它可以使用屬性 (attribute) 修改以指定屬性 (property) 類型。</span><span class="sxs-lookup"><span data-stu-id="bf7af-108">In a class-based DSC resource, the schema is defined as properties of the class which can be modified with attributes to specify the property type..</span></span> <span data-ttu-id="bf7af-109">資源是由 **Get()**、**Set()** 和 **Test()** 方法實作，它們相當於指令碼資源的 **Get-TargetResource**、**Set-TargetResource** 和 **Test-TargetResource** 函式。</span><span class="sxs-lookup"><span data-stu-id="bf7af-109">The resource is implemented by **Get()**, **Set()**, and **Test()** methods (equivalent to the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions in a script resource.</span></span>

<span data-ttu-id="bf7af-110">本主題會建立名為 **FileResource** 的簡單資源，管理指定路徑的檔案。</span><span class="sxs-lookup"><span data-stu-id="bf7af-110">In this topic, we will create a simple resource named **FileResource** that manages a file in a specified path.</span></span>

<span data-ttu-id="bf7af-111">如需 DSC 資源的詳細資訊，請參閱[建置自訂的 Windows PowerShell 預期狀態設定資源](authoringResource.md)。</span><span class="sxs-lookup"><span data-stu-id="bf7af-111">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md)</span></span>

><span data-ttu-id="bf7af-112">**注意：** 類別型資源不支援泛型集合。</span><span class="sxs-lookup"><span data-stu-id="bf7af-112">**Note:** Generic collections are not supported in class-based resources.</span></span>

## <a name="folder-structure-for-a-class-resource"></a><span data-ttu-id="bf7af-113">類別資源的資料夾結構</span><span class="sxs-lookup"><span data-stu-id="bf7af-113">Folder structure for a class resource</span></span>

<span data-ttu-id="bf7af-114">若要使用 PowerShell 類別實作 DSC 自訂資源，請建立下列資料夾結構。</span><span class="sxs-lookup"><span data-stu-id="bf7af-114">To implement a DSC custom resource with a PowerShell class, create the following folder structure.</span></span> <span data-ttu-id="bf7af-115">此類別在 **MyDscResource.psm1** 中定義，而模組資訊清單則在 **MyDscResource.psd1** 中定義。</span><span class="sxs-lookup"><span data-stu-id="bf7af-115">The class is defined in **MyDscResource.psm1** and the module manifest is defined in **MyDscResource.psd1**.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResource (folder)
        |- MyDscResource.psm1
           MyDscResource.psd1
```

## <a name="create-the-class"></a><span data-ttu-id="bf7af-116">建立類別</span><span class="sxs-lookup"><span data-stu-id="bf7af-116">Create the class</span></span>

<span data-ttu-id="bf7af-117">您要使用類別關鍵字來建立 PowerShell 類別。</span><span class="sxs-lookup"><span data-stu-id="bf7af-117">You use the class keyword to create a PowerShell class.</span></span> <span data-ttu-id="bf7af-118">若要明確指出類別是 DSC 資源，請使用 **DscResource()** 屬性。</span><span class="sxs-lookup"><span data-stu-id="bf7af-118">To specify that a class is a DSC resource, use the **DscResource()** attribute.</span></span> <span data-ttu-id="bf7af-119">類別名稱是 DSC 資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="bf7af-119">The name of the class is the name of the DSC resource.</span></span>

```powershell
[DscResource()]
class FileResource {
}
```

### <a name="declare-properties"></a><span data-ttu-id="bf7af-120">宣告屬性</span><span class="sxs-lookup"><span data-stu-id="bf7af-120">Declare properties</span></span>

<span data-ttu-id="bf7af-121">DSC 資源結構描述會定義為類別的屬性。</span><span class="sxs-lookup"><span data-stu-id="bf7af-121">The DSC resource schema is defined as properties of the class.</span></span> <span data-ttu-id="bf7af-122">我們會宣告三個屬性，如下所示。</span><span class="sxs-lookup"><span data-stu-id="bf7af-122">We declare three properties as follows.</span></span>

```powershell
[DscProperty(Key)]
[string]$Path

[DscProperty(Mandatory)]
[Ensure] $Ensure

[DscProperty(Mandatory)]
[string] $SourcePath

[DscProperty(NotConfigurable)]
[Nullable[datetime]] $CreationTime
```

<span data-ttu-id="bf7af-123">請注意，屬性 (attribute) 會修改屬性 (property)。</span><span class="sxs-lookup"><span data-stu-id="bf7af-123">Notice that the properties are modified by attributes.</span></span> <span data-ttu-id="bf7af-124">屬性的意義如下：</span><span class="sxs-lookup"><span data-stu-id="bf7af-124">The meaning of the attributes is as follows:</span></span>

- <span data-ttu-id="bf7af-125">**Dscproperty （key)**:屬性是必要的。</span><span class="sxs-lookup"><span data-stu-id="bf7af-125">**DscProperty(Key)**: The property is required.</span></span> <span data-ttu-id="bf7af-126">此屬性為索引鍵。</span><span class="sxs-lookup"><span data-stu-id="bf7af-126">The property is a key.</span></span> <span data-ttu-id="bf7af-127">所有標示為索引鍵的屬性值都必須結合，以在設定內唯一識別資源執行個體。</span><span class="sxs-lookup"><span data-stu-id="bf7af-127">The values of all properties marked as keys must combine to uniquely identify a resource instance within a configuration.</span></span>
- <span data-ttu-id="bf7af-128">**Dscproperty （mandatory)**:屬性是必要的。</span><span class="sxs-lookup"><span data-stu-id="bf7af-128">**DscProperty(Mandatory)**: The property is required.</span></span>
- <span data-ttu-id="bf7af-129">**Dscproperty （notconfigurable)**:屬性是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="bf7af-129">**DscProperty(NotConfigurable)**: The property is read-only.</span></span> <span data-ttu-id="bf7af-130">標示了這個屬性 (Attribute) 的屬性 (Property) 無法由設定進行設定，但出現時會由 **Get()** 方法填入。</span><span class="sxs-lookup"><span data-stu-id="bf7af-130">Properties marked with this attribute cannot be set by a configuration, but are populated by the **Get()** method when present.</span></span>
- <span data-ttu-id="bf7af-131">**Dscproperty （)**:屬性是可設定的但並非必要。</span><span class="sxs-lookup"><span data-stu-id="bf7af-131">**DscProperty()**: The property is configurable, but it is not required.</span></span>

<span data-ttu-id="bf7af-132">**$Path** 和 **$SourcePath** 屬性都是字串。</span><span class="sxs-lookup"><span data-stu-id="bf7af-132">The **$Path** and **$SourcePath** properties are both strings.</span></span> <span data-ttu-id="bf7af-133">**$CreationTime** 是 [DateTime](/dotnet/api/system.datetime) 屬性。</span><span class="sxs-lookup"><span data-stu-id="bf7af-133">The **$CreationTime** is a [DateTime](/dotnet/api/system.datetime) property.</span></span> <span data-ttu-id="bf7af-134">**$Ensure** 屬性是列舉類型，定義如下。</span><span class="sxs-lookup"><span data-stu-id="bf7af-134">The **$Ensure** property is an enumeration type, defined as follows.</span></span>

```powershell
enum Ensure
{
    Absent
    Present
}
```

### <a name="implementing-the-methods"></a><span data-ttu-id="bf7af-135">實作方法</span><span class="sxs-lookup"><span data-stu-id="bf7af-135">Implementing the methods</span></span>

<span data-ttu-id="bf7af-136">**Get()**、**Set()** 和 **Test()** 方法類似於指令碼資源中的 **Get-TargetResource**、**Set-TargetResource** 和 **Test-TargetResource** 函式。</span><span class="sxs-lookup"><span data-stu-id="bf7af-136">The **Get()**, **Set()**, and **Test()** methods are analogous to the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions in a script resource.</span></span>

<span data-ttu-id="bf7af-137">這個程式碼也包含 CopyFile() 函式，這是會將檔案從 **$SourcePath** 複製到 **$Path** 的 Helper 函式。</span><span class="sxs-lookup"><span data-stu-id="bf7af-137">This code also includes the CopyFile() function, a helper function that copies the file from **$SourcePath** to **$Path**.</span></span>

```powershell

    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)

        if ($this.ensure -eq [Ensure]::Present)
        {
            if(-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
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
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
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
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ErrorAction Ignore

        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
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
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = New-Object -TypeName System.IO.FileInfo($this.Path)

        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
```

### <a name="the-complete-file"></a><span data-ttu-id="bf7af-138">完整的檔案</span><span class="sxs-lookup"><span data-stu-id="bf7af-138">The complete file</span></span>
<span data-ttu-id="bf7af-139">完整的類別檔案如下。</span><span class="sxs-lookup"><span data-stu-id="bf7af-139">The complete class file follows.</span></span>

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
        if ($this.ensure -eq [Ensure]::Present)
        {
            if (-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
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
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
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
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ea Ignore
        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
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
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = new-object System.IO.FileInfo($this.Path)
        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                 to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
} # This module defines a class for a DSC "FileResource" provider.
```


## <a name="create-a-manifest"></a><span data-ttu-id="bf7af-140">建立資訊清單</span><span class="sxs-lookup"><span data-stu-id="bf7af-140">Create a manifest</span></span>

<span data-ttu-id="bf7af-141">若要向 DSC 引擎提供以類別為基礎的資源，指示模組匯出資源的資訊清單檔中必須包含 **DscResourcesToExport** 陳述式。</span><span class="sxs-lookup"><span data-stu-id="bf7af-141">To make a class-based resource available to the DSC engine, you must include a **DscResourcesToExport** statement in the manifest file that instructs the module to export the resource.</span></span> <span data-ttu-id="bf7af-142">我們的資訊清單看起來像這樣︰</span><span class="sxs-lookup"><span data-stu-id="bf7af-142">Our manifest looks like this:</span></span>

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

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '5.0'

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''
}
```

## <a name="test-the-resource"></a><span data-ttu-id="bf7af-143">測試資源</span><span class="sxs-lookup"><span data-stu-id="bf7af-143">Test the resource</span></span>

<span data-ttu-id="bf7af-144">如前文所述將類別和資訊清單檔儲存在資料夾結構中後，您就可以建立使用新資源的設定。</span><span class="sxs-lookup"><span data-stu-id="bf7af-144">After saving the class and manifest files in the folder structure as described earlier, you can create a configuration that uses the new resource.</span></span> <span data-ttu-id="bf7af-145">如需如何執行 DSC 設定的資訊，請參閱[施行設定](../pull-server/enactingConfigurations.md)。</span><span class="sxs-lookup"><span data-stu-id="bf7af-145">For information about how to run a DSC configuration, see [Enacting configurations](../pull-server/enactingConfigurations.md).</span></span> <span data-ttu-id="bf7af-146">下列設定會檢查 `c:\test\test.txt` 的檔案是否存在，如果不存在，會從 `c:\test.txt` 複製檔案 (您應該先建立 `c:\test.txt` 再執行設定)。</span><span class="sxs-lookup"><span data-stu-id="bf7af-146">The following configuration will check to see whether the file at `c:\test\test.txt` exists, and, if not, copies the file from `c:\test.txt` (you should create `c:\test.txt` before you run the configuration).</span></span>

```powershell
Configuration Test
{
    Import-DSCResource -module MyDscResource
    FileResource file
    {
        Path = "C:\test\test.txt"
        SourcePath = "c:\test.txt"
        Ensure = "Present"
    }
}
Test
Start-DscConfiguration -Wait -Force Test
```

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="bf7af-147">支援 PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="bf7af-147">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="bf7af-148">**注意：\*\*\*\*PsDscRunAsCredential**在 PowerShell 5.0 和更新版本支援。</span><span class="sxs-lookup"><span data-stu-id="bf7af-148">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="bf7af-149">您可以在 [DSC 設定](../configurations/configurations.md)資源區塊中使用 **PsDscRunAsCredential** 特性，以指定該資源應該在一組指定的認證下執行。</span><span class="sxs-lookup"><span data-stu-id="bf7af-149">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="bf7af-150">如需詳細資訊，請參閱[以使用者認證執行 DSC](../configurations/runAsUser.md)。</span><span class="sxs-lookup"><span data-stu-id="bf7af-150">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

### <a name="require-or-disallow-psdscrunascredential-for-your-resource"></a><span data-ttu-id="bf7af-151">針對您的資源要求使用或不允許使用 PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="bf7af-151">Require or disallow PsDscRunAsCredential for your resource</span></span>

<span data-ttu-id="bf7af-152">**DscResource()** 屬性可接受選擇性的參數 **RunAsCredential**。</span><span class="sxs-lookup"><span data-stu-id="bf7af-152">The **DscResource()** attribute takes an optional parameter **RunAsCredential**.</span></span>
<span data-ttu-id="bf7af-153">此參數可接受下列三個值其中之一：</span><span class="sxs-lookup"><span data-stu-id="bf7af-153">This parameter takes one of three values:</span></span>

- <span data-ttu-id="bf7af-154">`Optional`：對呼叫此資源的設定來說，可以選擇是否使用 **PsDscRunAsCredential**。</span><span class="sxs-lookup"><span data-stu-id="bf7af-154">`Optional` **PsDscRunAsCredential** is optional for configurations that call this resource.</span></span> <span data-ttu-id="bf7af-155">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="bf7af-155">This is the default value.</span></span>
- <span data-ttu-id="bf7af-156">`Mandatory`：對呼叫此資源的所有設定來說，必須使用 **PsDscRunAsCredential**。</span><span class="sxs-lookup"><span data-stu-id="bf7af-156">`Mandatory` **PsDscRunAsCredential** must be used for any configuration that calls this resource.</span></span>
- <span data-ttu-id="bf7af-157">`NotSupported`：呼叫此資源的設定無法使用 **PsDscRunAsCredential**。</span><span class="sxs-lookup"><span data-stu-id="bf7af-157">`NotSupported` Configurations that call this resource cannot use **PsDscRunAsCredential**.</span></span>
- <span data-ttu-id="bf7af-158">`Default`：與 `Optional` 相同。</span><span class="sxs-lookup"><span data-stu-id="bf7af-158">`Default` Same as `Optional`.</span></span>

<span data-ttu-id="bf7af-159">例如，使用下列屬性可以指定您的自訂資源不支援使用 **PsDscRunAsCredential**：</span><span class="sxs-lookup"><span data-stu-id="bf7af-159">For example, use the following attribute to specify that your custom resource does not support using **PsDscRunAsCredential**:</span></span>

```powershell
[DscResource(RunAsCredential=NotSupported)]
class FileResource {
}
```

### <a name="access-the-user-context"></a><span data-ttu-id="bf7af-160">存取使用者內容</span><span class="sxs-lookup"><span data-stu-id="bf7af-160">Access the user context</span></span>

<span data-ttu-id="bf7af-161">若要從自訂資源內存取使用者內容，您可以使用自動變數 `$global:PsDscContext`。</span><span class="sxs-lookup"><span data-stu-id="bf7af-161">To access the user context from within a custom resource, you can use the automatic variable `$global:PsDscContext`.</span></span>

<span data-ttu-id="bf7af-162">例如，下列程式碼會將資源執行位置的上層使用者內容寫入到詳細的輸出資料流：</span><span class="sxs-lookup"><span data-stu-id="bf7af-162">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $global:PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="bf7af-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf7af-163">See Also</span></span>
### <a name="concepts"></a><span data-ttu-id="bf7af-164">概念</span><span class="sxs-lookup"><span data-stu-id="bf7af-164">Concepts</span></span>
[<span data-ttu-id="bf7af-165">建置自訂的 Windows PowerShell 預期狀態設定資源</span><span class="sxs-lookup"><span data-stu-id="bf7af-165">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)