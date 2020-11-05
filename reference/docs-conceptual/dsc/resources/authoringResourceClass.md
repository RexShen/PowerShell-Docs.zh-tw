---
ms.date: 07/08/2020
keywords: dsc,powershell,設定,安裝
title: 使用 PowerShell 類別撰寫自訂的 DSC 資源
description: 此文章說明如何建立能管理位於指定路徑之檔案的簡單資源。
ms.openlocfilehash: 72a828795c29e10ff66f164b8871b0fea7a1e0a8
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667312"
---
# <a name="writing-a-custom-dsc-resource-with-powershell-classes"></a>使用 PowerShell 類別撰寫自訂的 DSC 資源

> 適用於：Windows PowerShell 5.0

您可以利用 Windows PowerShell 5.0 引入的 PowerShell 類別，藉由建立類別來定義 DSC 資源。 類別會定義結構描述和資源實作，所以不必建立個別的 MOF 檔案。 以類別為基礎的資源資料夾結構也比較簡單，因為不需要 **DSCResources** 資料夾。

在以類別為基礎的 DSC 資源中，結構描述會定義為類別屬性，它可以使用屬性 (attribute) 修改以指定屬性 (property) 類型。 資源是由 `Get()` 、`Set()` 和 `Test()` 方法實作，它們相當於指令碼資源的 `Get-TargetResource`、`Set-TargetResource` 和 `Test-TargetResource` 函式。

在此文章中，我們會建立名為 **FileResource** 的簡單資源，以管理位於指定路徑的檔案。

如需 DSC 資源的詳細資訊，請參閱[建置自訂的 Windows PowerShell 預期狀態設定資源](authoringResource.md)。

> [!Note]
> 以類別為基礎的資源不支援泛型集合。

## <a name="folder-structure-for-a-class-resource"></a>類別資源的資料夾結構

若要使用 PowerShell 類別實作 DSC 自訂資源，請建立下列資料夾結構。
此類別在 `MyDscResource.psm1` 中定義，而模組資訊清單則在 `MyDscResource.psd1` 中定義。

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResource (folder)
        MyDscResource.psm1
        MyDscResource.psd1
```

## <a name="create-the-class"></a>建立類別

您要使用類別關鍵字來建立 PowerShell 類別。 若要明確指出類別是 DSC 資源，請使用 `DscResource()` 屬性。 類別名稱是 DSC 資源的名稱。

```powershell
[DscResource()]
class FileResource {
}
```

### <a name="declare-properties"></a>宣告屬性

DSC 資源結構描述會定義為類別的屬性。 我們會宣告三個屬性，如下所示。

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

請注意，屬性 (attribute) 會修改屬性 (property)。 屬性的意義如下：

- **DscProperty(Key)** ：此為必要屬性。 此屬性為索引鍵。 所有標示為索引鍵的屬性值都必須結合，以在設定內唯一識別資源執行個體。
- **DscProperty(Mandatory)** ：此為必要屬性。
- **DscProperty(NotConfigurable)** ：此為唯讀屬性。 標示了這個屬性 (Attribute) 的屬性 (Property) 無法由設定進行設定，但出現時會由 `Get()` 方法填入。
- **DscProperty()** ：此為可設定但非必要的屬性。

`$Path` 和 `$SourcePath` 屬性都是字串。 `$CreationTime` 是 [DateTime](/dotnet/api/system.datetime) 屬性。 `$Ensure` 屬性是列舉類型，定義如下。

```powershell
enum Ensure
{
    Absent
    Present
}
```

### <a name="implementing-the-methods"></a>實作方法

`Get()` 、`Set()` 和 `Test()` 方法類似於指令碼資源中的 `Get-TargetResource`、`Set-TargetResource` 和 `Test-TargetResource` 函式。

這段程式碼也包含 `CopyFile()` 函式，這是能將檔案從 `$SourcePath` 複製到 `$Path` 的 Helper 函式。

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

### <a name="the-complete-file"></a>完整的檔案

完整的類別檔案如下。

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

## <a name="create-a-manifest"></a>建立資訊清單

若要向 DSC 引擎提供以類別為基礎的資源，指示模組匯出資源的資訊清單檔中必須包含 `DscResourcesToExport` 陳述式。 我們的資訊清單看起來像這樣︰

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

## <a name="test-the-resource"></a>測試資源

如前文所述將類別和資訊清單檔儲存在資料夾結構中後，您就可以建立使用新資源的設定。 如需如何執行 DSC 設定的資訊，請參閱[施行設定](../pull-server/enactingConfigurations.md)。 下列設定會檢查 `c:\test\test.txt` 的檔案是否存在，如果不存在，會從 `c:\test.txt` 複製檔案 (您應該先建立 `c:\test.txt` 再執行設定)。

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

## <a name="supporting-psdscrunascredential"></a>支援 PsDscRunAsCredential

> [注意] PowerShell 5.0 及更新版本支援 **PsDscRunAsCredential** 。

您可以在 [DSC 設定](../configurations/configurations.md)資源區塊中使用 **PsDscRunAsCredential** 特性，以指定該資源應該在一組指定的認證下執行。 如需詳細資訊，請參閱[以使用者認證執行 DSC](../configurations/runAsUser.md)。

### <a name="require-or-disallow-psdscrunascredential-for-your-resource"></a>針對您的資源要求使用或不允許使用 PsDscRunAsCredential

`DscResource()` 屬性可接受選擇性的參數 **RunAsCredential** 。 此參數可接受下列三個值其中之一：

- 對呼叫此資源的設定來說，可以選擇是否使用 `Optional` **PsDscRunAsCredential** 。 這是預設值。
- 對呼叫此資源的所有設定來說，必須使用 `Mandatory` **PsDscRunAsCredential** 。
- `NotSupported`：呼叫此資源的設定無法使用 **PsDscRunAsCredential** 。
- `Default`：與 `Optional` 相同。

例如，使用下列屬性可以指定您的自訂資源不支援使用 **PsDscRunAsCredential** ：

```powershell
[DscResource(RunAsCredential=NotSupported)]
class FileResource {
}
```

### <a name="declaring-multiple-class-resources-in-a-module"></a>在模組中宣告多個類別資源

一個模組可定義以多個類別為基礎的 DSC 資源。 您可以透過下列方式建立資料夾結構：

1. 在 `<ModuleName>.psm1` 檔案中定義第一個資源，然後在 **DSCResources** 資料夾下方定義後續資源。

   ```
   $env:ProgramFiles\WindowsPowerShell\Modules (folder)
        |- MyDscResource (folder)
           |- MyDscResource.psm1
              MyDscResource.psd1
        |- DSCResources
           |- SecondResource.psm1
   ```

1. 在 **DSCResources** 資料夾下方定義所有資源。

   ```
   $env:ProgramFiles\WindowsPowerShell\Modules (folder)
        |- MyDscResource (folder)
           |- MyDscResource.psm1
              MyDscResource.psd1
        |- DSCResources
           |- FirstResource.psm1
              SecondResource.psm1
   ```

> [!NOTE]
> 在上述範例中，將 **DSCResources** 下方的所有 PSM1 檔案新增至您 PSD1 檔案中的 **NestedModules** 索引碼。

### <a name="access-the-user-context"></a>存取使用者內容

若要從自訂資源內存取使用者內容，您可以使用自動變數 `$global:PsDscContext`。

例如，下列程式碼會將資源執行位置的上層使用者內容寫入到詳細的輸出資料流：

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $global:PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a>另請參閱

[建置自訂的 Windows PowerShell 預期狀態設定資源](authoringResource.md)
