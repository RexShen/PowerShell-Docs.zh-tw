# 以類別為基礎的 DSC 資源

## 以類別定義 DSC 資源

根據意見反應，我們讓撰寫以類別為基礎的 DSC 資源更簡單且更容易了解。 
以類別為基礎的 DSC 資源和 Cmdlet DSC 資源提供者之間的主要差異如下︰

* 不需要結構描述的 MOF 檔案。
* 不需要模組資料夾中的 **DSCResource** 子資料夾。
* PowerShell 模組檔案可以包含多個 DSC 資源類別。

以下是以類別為基礎的 DSC 資源範例，該範例的內容延伸至相同檔案中的其他類別 DSC 資源。 這會儲存為模組 **MyDSCResource.psm1**。. 
請注意，您必須一律包含至少一個關鍵屬性，以及以類別為基礎的 DSC 資源或其基底類別中的 Get、Set、Test 方法。

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
class BaseFileResource
{
<#
This property is the fully qualified path to the file that is expected to be present or absent.

The [DscProperty(Key)] attribute indicates the property is a key and its value uniquely identifies a resource instance. Defining this attribute also means the property is required and DSC will ensure a value is set before calling the resource.

A DSC resource must define at least one key property.
#>

[DscProperty(Key)]
[string]$Path

<#
This property indicates if the settings should be present or absent on the system.

For present, the resource ensures the file pointed to by $Path exists. For absent, it ensures the file that $Path points to does not exist.

The [DscProperty(Mandatory)] attribute indicates the property is required and DSC will guarantee it is set.

If Mandatory is not specified or if it is defined as Mandatory=$false, the value is not guaranteed to be set when DSC calls the resource. This is appropriate for optional properties.
#>

[DscProperty(Mandatory)]
[Ensure] $Ensure

<#
This property defines the fully qualified path to a file that will be placed on the system if $Ensure = Present and $Path does not exist.
NOTE: This property is required because [DscProperty(Mandatory)] is set.
#>

[DscProperty(Mandatory)]
[string] $SourcePath

<#
This property reports the file creation timestamp.

[DscProperty(NotConfigurable)] attribute indicates the property is not configurable in a DSC configuration. Properties marked this way are populated by the Get() method to report additional details about the resource when it is present.
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
This method is equivalent of the Test-TargetResource script function.
It should return True or False, showing whether the resource is in a desired state.
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
This method is equal to the Get-TargetResource script function.
The implementation should use the keys to find appropriate resources.
This method returns an instance of this class with the updated key properties.
#>

[BaseFileResource] Get()
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
Helper method to check if the file exists and it is the right file
#>

[bool] TestFilePath([string] $location)
{
    $present = $true
    $item = Get-ChildItem -LiteralPath $location -ea Ignore
    
    if ($item -eq $null)
    {
        $present = $false
    }
    elseif($item.PSProvider.Name -ne "FileSystem")
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
Helper method to copy the file from source to path
#>

[void] CopyFile()
{
    if(-not $this.TestFilePath($this.SourcePath))
    {
        throw "SourcePath $($this.SourcePath) is not found."
    }

    [System.IO.FileInfo] $destFileInfo = new-object System.IO.FileInfo($this.Path)
    if (-not $destFileInfo.Directory.Exists)
    {
        Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"
    
        # use CreateDirectory instead of New-Item to avoid code
        # to handle the non-terminating error
        [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
    }

    if(Test-Path -LiteralPath $this.Path -PathType Container)
    {
        throw "Path $($this.Path) is a directory path"
    }

    Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"
    # DSC engine catches and reports any error that occurs
    Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
}
}

<#
This resource inherits from the [BaseFileResource]
It reports additional information in Get method
#>

[DscResource()]
class FileResource : BaseFileResource
{
    <#
    This property reports if it is a readonly file
    #>
    [DscProperty(NotConfigurable)]
    [bool] $IsReadOnly

    <#
    This property reports the file LastAccessTime timestamp.
    #>
    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $LastAccessTime

    <#
    This property reports the file LastWriteTime timestamp.
    #>
    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $LastWriteTime

    <#
    This method overrides the Get method in the base class.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)
        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.IsReadOnly = $file.IsReadOnly
            $this.LastAccessTime = $file.LastAccessTime
            $this.LastWriteTime = $file.LastWriteTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.LastAccessTime = $null
            $this.LastWriteTime = $null
            $this.Ensure = [Ensure]::Absent
        }

    return $this
}

}
```

在建立以類別為基礎的 DSC 資源提供者，並將它儲存為模組之後，為模組建立模組資訊清單。 此範例會將下列模組資訊清單儲存為 **MyDscResource.psd1**。.

```powershell
@{
# Script module or binary module file associated with this manifest.
RootModule = 'MyDscResource.psm1'

# Version number of this module.
ModuleVersion = '1.0'

# ID used to identify this module uniquely
GUID = '81624038-5e71-40f8-8905-b1a87afe22d7'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) 2015 User01. All rights reserved.'

# Description of the functionality provided by this module
Description = 'DSC resource provider for FileResource.'

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '5.0'

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''

# Required for DSC to detect PS class-based resources.
DscResourcesToExport = @('BaseFileResource','FileResource')
}
```

只要在其下建立 **MyDscResource** 資料夾，就能部署新的 DSC 資源提供者。 `$env:SystemDrive\Program Files\WindowsPowerShell\Modules`.
您不需要建立 DSCResource 子資料夾。
將模組和模組資訊清單檔案複製 (**MyDscResource.psm1** 和 **MyDscResource.psd1**) 到 **MyDscResource** 資料夾。

從現在開始，您可以如同使用任何 DSC 資源一般的建立和執行設定指令碼。 
以下為參考 MyDSCResource 模組的設定。 
將此檔案儲存為指令碼 **MyResource.ps1**。.

```powershell
Configuration MyConfig
{
    Import-Dscresource -ModuleName MyDscResource
    BaseFileResource file
    {
        Path = "C:\test\baseFile.txt"
        SourcePath = "c:\test.txt"
        Ensure = "Present"
    }

    FileResource file
    {
        Path = "C:\test\File.txt"
        SourcePath = "c:\test.txt"
        Ensure = "Present"
    }
}

MyConfig
```

如同執行任何 DSC 設定指令碼一般的執行此指令碼。 若要開始設定，請在提升權限的 Windows PowerShell 主控台中執行下列 Cmdlet。 
您會看到 FileResource 中 Get-DscConfiguration 的輸出包含比 BaseFileResource 還要多的資訊。

```powershell
.\MyResource.ps1
Start-DscConfiguration c:\test\MyConfig –Wait –Verbose
Get-DscConfiguration
```

## 已知問題

在此版本中，下列項目是以類別為基礎 DSC 資源的已知問題︰

* 如果以類別為基礎 DSC 資源的 Get() 函式傳回複雜類型的話，Get-DscConfiguration 可能會傳回空值 (null) 或錯誤。
* 複合資源作為以類別為基礎的資源時無法寫入。


<!--HONumber=Apr16_HO5-->


