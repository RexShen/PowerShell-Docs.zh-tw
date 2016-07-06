# PackageManagement Cmdlet
這是支援軟體探索、安裝和清查 (SDII) 的 PackageManagement 核心。 試試看這些作業的 Cmdlet︰
-   Find-Package
-   Find-PackageProvider
-   Get-Package
-   Get-PackageProvider
-   Get-PackageSource
-   Import-PackageProvider
-   Install-Package
-   Install-PackageProvider
-   Register-PackageSource
-   Save-Package
-   Set-PackageSource
-   Uninstall-Package
-   Unregister-PackageSource

因為 PackageManagement 是 PowerShell 模組，您可執行下列作業更新 PackageManagement：
```powershell
PS C:\> Install-Module PackageManagement –Force
```
在本例中，您必須重新進入 PowerShell 工作階段，以切換至新版的 PackageManagement。

## [Find-Package Cmdlet](https://technet.microsoft.com/en-us/library/dn890709.aspx)
這個 Cmdlet 可讓您使用載入的封裝提供者在可用的封裝來源中探索軟體封裝。
```powershell
# Find all available Windows PowerShell module packages from galleries registered
# with PowerShellGet provider
Find-Package -Provider PowerShellGet -Source PSGallery

# Find a package from a provider that is not yet installed
# This will bootstrap NuGet provider and then search for jquery package using NuGet
# with <http://www.nuget.org/api/v2/> as source
Find-Package -Name jquery –Provider NuGet -Source http://www.nuget.org/api/v2/

# Find package with name and version
# Here we are assuming that the user already registered nuget.org using
# Register-PackageSource. You can specify either the provider or the source, or
# neither. For the latter, performance may be less optimal as it searches through all
# the providers and registered sources.
Find-Package -Name jquery –Provider NuGet –RequiredVersion 2.1.4 -Source nuget.org
```

## [Find-PackageProvider Cmdlet](https://technet.microsoft.com/en-us/library/mt676544.aspx)
Find-PackageProvider Cmdlet 會在向 PowerShellGet 註冊的封裝來源中尋找相符的 PackageManagement 提供者。 這些是可使用 Install-PackageProvider Cmdlet 進行安裝的封裝提供者。 根據預設，這包括 PowerShell Gallery 提供之具有 'PackageManagement' 和 'Provider' 標記的模組。 

Find-PackageProvider 也會尋找相符的 PackageManagement 提供者，它們可在 PackageManagement Azure Blob 存放區中取得，我們在此存放區中使用 PackageManagement boostrapper 提供者尋找及安裝它們。
```powershell
#Find all available package providers in PackageManagement azure blob store as well as in PowerShellGallery.com
Find-PackageProvider

#Find all versions of a provider
Find-PackageProvider -Name "Nuget" -AllVersions

#Find a provider from a specified source
Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

## [Get-Package Cmdlet](https://technet.microsoft.com/en-us/library/dn890704.aspx)
這個 Cmdlet 會傳回所有已使用 PackageManagement 安裝的軟體封裝清單。
```powershell
# Get all the packages installed by Programs provider
Get-Package –Provider Programs

# Get all the packages installed by NuGet provider at c:\test using the dynamic
# parameter destination
Get-Package –Provider NuGet -Destination c:\test
```

## [Get-PackageProvider Cmdlet](https://technet.microsoft.com/en-us/library/dn890703.aspx)
您可以使用 Cmdlet 清查本機電腦上已載入並準備使用的封裝提供者。
```powershell
# Get all currently loaded package providers
Get-PackageProvider

# The following cmdlet will show all the package providers available on the machine (including those that are not loaded):
Get-PackageProvider -ListAvailable
```

## [Get-PackageSource Cmdlet](https://technet.microsoft.com/en-us/library/dn890705.aspx)
這個 Cmdlet 會取得封裝提供者註冊的封裝來源清單。
```powershelll
# Get all package sources
Get-PackageSource

# Get all package sources for a specific provider
Get-PackageSource –ProviderName PowerShellGet
```

## [Import-PackageProvider Cmdlet](https://technet.microsoft.com/en-us/library/mt676545.aspx)
這個 Cmdlet 會在目前的工作階段中加入封裝管理封裝提供者。
```powershell
# Import a package provider from the local machine
Import-PackageProvider –Name MyProvider

#The -Name parameter can be either the name of the provider or the full path to the provider. Currently, we support .dll, .exe and.psm1 for the full path case. If the name of the provider is used for the -Name parameter, then additional version parameters such as -RequiredVersion, -MinimumVersion and -MaximumVersion may be specified. Otherwise, the latest version of the provider will be imported.

#If a package provider is not yet loaded to your system, we can discover and install on-demand. You can use explicit discovery and install cmdlets to do so:
 Find-PackageProvider
 Install-PackageProvider –Name MyProvider

#After installed, follow the Import-PackageProvider to load it to your system.

# Import a specific version of a package provider. PackageManagement supports installations of multiple versions of a package provider using PackageProvider cmdlets (not by bootstrapper provider). You can install another version of a package provider given that you already have one up running by:
Find-PackageProvider –Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force
Get-PackageProvider –ListAvailable
Import-PackageProvider –Name "Nuget" -RequiredVersion "2.8.5.201" -Verbose
Import-PackageProvider –Name MyProvider –RequiredVersion xxxx -force
```

##[ Install-Package Cmdlet](https://technet.microsoft.com/en-us/library/dn890711.aspx)

這個 Cmdlet 可讓您使用載入的封裝提供者在可用的封裝來源中安裝軟體封裝。
```powershell
# Install a package by name.
# NuGet provider requires us to provide the dynamic parameter destination path
# when we use this provider to install. Not all providers will require you to supply
# dynamic parameters for PackageManagement cmdlets.
Install-Package -Name jquery -Source nuget.org -Destination c:\test

# Install a package by piping.
Find-Package -Name jquery –Provider NuGet | Install-Package -Destination c:\test
```

## [Install-PackageProvider Cmdlet](https://technet.microsoft.com/en-us/library/mt676543.aspx)
這個 Cmdlet 會安裝一個或多個封裝管理封裝提供者。
```powershell
# Install a package provider from the PowerShell Gallery
Install-PackageProvider –Name "Gistprovider" -Verbose

# Install a specified version of a package provider
Find-PackageProvider –Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force

# Find a provider and install it
Find-PackageProvider –Name "Gistprovider" | Install-PackageProvider -Verbose

# Install a provider to the current user’s module folder
Install-PackageProvider –Name Gistprovider –Verbose –Scope CurrentUser
```

## [Register-PackageSource Cmdlet](https://technet.microsoft.com/en-us/library/dn890701.aspx)
這個 Cmdlet 會加入指定封裝提供者的封裝來源。
每個 PackageManagement 提供者都可能會有一個或多個軟體來源或是存放庫。 PackageManagement 提供 PowerShell Cmdlet 來新增/移除/查詢來源。 例如，您可以註冊 NuGet 提供者的封裝來源：
```powershell
Register-PackageSource -Name "NugetSource" -Location "http://www.nuget.org/api/v2" –ProviderName nuget
```

## [Save-Package Cmdlet](https://technet.microsoft.com/en-us/library/dn890708.aspx)
這個 Cmdlet 會將封裝儲存到本機電腦，而不加以安裝。
```powershell
# Saves jquery package to c:\test using NuGetProvider
# Notes that the -Path parameter must point to an existing location
Save-Package -Name jquery –Provider NuGet -Path c:\test

# Save a package by piping.
Find-Package -Name jquery -Source http://www.nuget.org/api/v2/ | Save-Package -Path c:\test
Find-Package -source c:\test
```

## [Set-PackageSource Cmdlet](https://technet.microsoft.com/en-us/library/dn890710.aspx)
這個 Cmdlet 會變更現有封裝來源的相關資訊。 
```powershell
#Set-PackageSource changes the values for a source that has already been registered by running the Register-PackageSource cmdlet. By #running Set-PackageSource, you can change the source name and location.
Set-PackageSource  -Name nuget.org -Location  http://www.nuget.org/api/v2 -NewName nuget2 -NewLocation https://www.nuget.org/api/v2 
```

## [Uninstall-Package Cmdlet](https://technet.microsoft.com/en-us/library/dn890702.aspx)
這個 Cmdlet 會解除安裝本機電腦上安裝的封裝。
```powershell
# Uninstall jquery using nuget
Uninstall-Package -Name jquery –Provider NuGet -Destination c:\test

# Uninstall a package with by piping with Get-Package
Get-Package -Name jquery –Provider NuGet -Destination c:\test | Uninstall-Package
```

## [Unregister-PackageSource Cmdlet](https://technet.microsoft.com/en-us/library/dn890707.aspx)
```powershell
# Unregister a package source for the NuGet provider. You can use command Unregister-PackageSource, to disconnect with a repository, and Get-PackageSource, to discover what the repositories are associated with that provider.
Unregister-PackageSource  -Name "NugetSource"
```


<!--HONumber=Jun16_HO4-->


