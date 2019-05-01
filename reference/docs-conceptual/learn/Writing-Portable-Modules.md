---
ms.date: 12/14/2018
keywords: powershell,cmdlet
title: 撰寫可移植的模組
ms.openlocfilehash: 38a93b5b030d58784b91292e2cd060b3a2c19a00
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086403"
---
# <a name="portable-modules"></a>可移植的模組

Windows PowerShell 是針對 [.NET Framework][] 撰寫的，而 PowerShell Core 則是針對 [.NET Core][] 撰寫的。 可移植的模組是在 Windows PowerShell 和 PowerShell Core 中運作的模組。 雖然 .NET Framework 和 .NET Core 高度相容，但兩者之間提供的 API 還是有所不同。 Windows PowerShell 和 PowerShell Core 中提供的 API 也有一些差異。 同時適用於兩個環境的模組必須注意這些差異。

## <a name="porting-an-existing-module"></a>移植現有的模組

### <a name="porting-a-pssnapin"></a>移植 PSSnapIn

PowerShell Core 並不支援 PowerShell 嵌入式管理單元 (PSSnapIn)。 但是也沒有必要將 PSSnapIn 轉換成 PowerShell 模組。 一般而言，PSSnapIn 註冊程式碼是衍生自 [PSSnapIn][] 之類別的單一來源檔案。 請將此來源檔案從組建中移除，因為已經不再需要。

使用 [New-ModuleManifest][] 建立新的模組資訊清單，以取代需要 PSSnapIn 註冊程式碼的需求。 PSSnapIn 的某些值 (例如「描述」) 可在模組資訊清單內重複使用。

模組資訊清單中的 `RootModule` 屬性應設定為實作 Cmdlet 之組件 (dll) 的名稱。

### <a name="the-net-portability-analyzer-aka-apiport"></a>.NET Portability Analyzer (也稱為 APIPort)

若要移植為 Windows PowerShell 撰寫的模組以和 PowerShell Core 搭配運作，請從 [.NET Portability Analyzer][] 開始。 針對您編譯的組件執行此工具，以判斷模組中使用的 .NET API 是否與 .NET Framework、.NET Core 和其他 .NET 執行階段相容。 如果它們存在，工具會建議替代的 API。 否則，您可能需要新增[執行階段檢查][]，並限制特定執行階段中不適用的功能。

## <a name="creating-a-new-module"></a>建立新模組

如果建立新的模組，建議使用 [.NET CLI][]。

### <a name="installing-the-powershell-standard-module-template"></a>安裝 PowerShell 標準模組範本

安裝 .NET CLI 之後，請安裝範本程式庫以產生簡單的 PowerShell 模組。
模組將會與 Windows PowerShell、PowerShell Core、Windows、Linux 和 macOS 相容。

下列範例顯示如何安裝範本：

```powershell
dotnet new -i Microsoft.PowerShell.Standard.Module.Template
```

```output
  Restoring packages for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj...
  Installing Microsoft.PowerShell.Standard.Module.Template 0.1.3.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.targets.
  Restore completed in 1.66 sec for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj.

Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.
  -n, --name          The name for the output being created. If no name is specified, the name of the current directory is used.
  -o, --output        Location to place the generated output.
  -i, --install       Installs a source or a template pack.
  -u, --uninstall     Uninstalls a source or a template pack.
  --nuget-source      Specifies a NuGet source to use during install.
  --type              Filters templates based on available types. Predefined values are "project", "item" or "other".
  --force             Forces content to be generated even if it would change existing files.
  -lang, --language   Filters templates based on language and specifies the language of the template to create.


Templates                                         Short Name         Language          Tags
----------------------------------------------------------------------------------------------------------------------------
Console Application                               console            [C#], F#, VB      Common/Console
Class library                                     classlib           [C#], F#, VB      Common/Library
PowerShell Standard Module                        psmodule           [C#]              Library/PowerShell/Module
...
```

### <a name="creating-a-new-module-project"></a>建立新模組專案

安裝範本之後，就可以使用該範本建立新的 PowerShell 模組專案。 在此範例中，範例模組稱為 'myModule'。

```
PS> mkdir myModule

    Directory: C:\Users\Steve

Mode LastWriteTime Length Name
---- ------------- ------ ----
d----- 8/3/2018 2:41 PM myModule

PS> cd myModule
PS C:\Users\Steve\myModule> dotnet new psmodule

The template "PowerShell Standard Module" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\Users\Steve\myModule\myModule.csproj...
  Restoring packages for C:\Users\Steve\myModule\myModule.csproj...
  Installing PowerShellStandard.Library 5.1.0.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.targets.
  Restore completed in 1.76 sec for C:\Users\Steve\myModule\myModule.csproj.

Restore succeeded.
```

### <a name="building-the-module"></a>建置模組

使用標準 .NET CLI 命令建置專案。

```powershell
dotnet build
```

```output
PS C:\Users\Steve\myModule> dotnet build
Microsoft (R) Build Engine version 15.7.179.6572 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 76.85 ms for C:\Users\Steve\myModule\myModule.csproj.
  myModule -> C:\Users\Steve\myModule\bin\Debug\netstandard2.0\myModule.dll

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:05.40
```

### <a name="testing-the-module"></a>測試模組

建置模組之後，可以將它匯入並執行範例 Cmdlet。

```powershell
ipmo .\bin\Debug\netstandard2.0\myModule.dll
Test-SampleCmdlet -?
Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat
```

```output
PS C:\Users\Steve\myModule> ipmo .\bin\Debug\netstandard2.0\myModule.dll
PS C:\Users\Steve\myModule> Test-SampleCmdlet -?

NAME
    Test-SampleCmdlet

SYNTAX
    Test-SampleCmdlet [-FavoriteNumber] <int> [[-FavoritePet] {Cat | Dog | Horse}] [<CommonParameters>]


ALIASES
    None


REMARKS
    None


PS C:\Users\Steve\myModule> Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat

FavoriteNumber FavoritePet
-------------- -----------
             7 Cat
```

以下各節詳細說明此範本的一些使用技巧。

## <a name="net-standard-library"></a>.NET Standard 程式庫

[.NET Standard][] 是所有 .NET 實作中所提供之 .NET API 的正式規格。 以 .NET Standard 為目標的受控程式碼可和與該版 .NET Standard 相容的 .NET Framework 和 .NET Core 版本搭配使用。

> [!NOTE]
> 雖然 .NET Standard 可能已經有 API 存在，但 .NET Core 中的 API 實作可能會在執行階段擲回 `PlatformNotSupportedException`，因此為了確認與 Windows PowerShell 和 PowerShell Core 的相容性，最好的方法是在兩個環境內針對模組執行測試。
> 如果模組要跨平台使用，也請在 Linux 和 macOS 中執行測試。

以 .NET Standard 為目標有助於確保在模組發展過程中，不會突然出現不相容的 API。 因為在編譯時期就能發現不相容項目，而不是等到執行階段才發現。

但是只要使用相容的 API，就不需要將要與 Windows PowerShell 和 PowerShell Core 搭配使用的模組以 .NET Standard 為目標。 中繼語言 (IL) 在兩個執行階段之間是相容的。 您能以 .NET Framework 4.6.1 為目標，它與 .NET Standard 2.0 相容。 如果沒有使用 .NET Standard 2.0 之外的 API，您的模組不需要重新編譯，就能與 PowerShell Core 6 搭配使用。

## <a name="powershell-standard-library"></a>PowerShell Standard 程式庫

[PowerShell Standard][] 程式庫是版本大於或等於該標準版本的所有 PowerShell 版本中所提供 PowerShell API 的正式規格。

例如，[PowerShell Standard 5.1][] 與 Windows PowerShell 5.1 和 PowerShell Core 6.0 或更新版本相容。

我們建議您使用 PowerShell Standard 程式庫來編譯您的模組。 此程式庫可確保在 Windows PowerShell 和 PowerShell Core 6 中都已提供並實作 API。
PowerShell Standard 的設計旨在始終向下相容。 使用 PowerShell Standard 程式庫 5.1 建置的模組一律會與未來的 PowerShell 版本相容。

## <a name="module-manifest"></a>模組資訊清單

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a>指示與 Windows PowerShell 和 PowerShell Core 的相容性

驗證模組可與 Windows PowerShell 和 PowerShell Core 搭配使用之後，模組資訊清單應該使用 [CompatiblePSEditions][] 屬性明確指示相容性。 值為 `Desktop` 表示模組與 Windows PowerShell 相容，值為 `Core` 表示模組與 PowerShell Core 相容。 同時包含 `Desktop` 與 `Core` 表示模組與 Windows PowerShell 和 PowerShell Core 相容。

> [!NOTE]
> `Core` 不會自動表示模組與 Windows、Linux 和 macOS 相容。
> PowerShell v5 中已經引進 **CompatiblePSEditions** 屬性。 使用 **CompatiblePSEditions** 屬性的模組資訊清單無法載入至 PowerShell v5 之前的版本中。

### <a name="indicating-os-compatibility"></a>指示作業系統相容性

首先，請驗證您的模組可在 Linux 和 macOS 上運作。 接下來，在模組資訊清單中指示與那些作業系統相容。 這可在將模組發佈至 [PowerShell 資源庫][]時，讓使用者更容易地為他們的作業系統找到您的模組。

在模組資訊清單內，`PrivateData` 屬性具有 `PSData` 子屬性。 `PSData` 的選擇性 `Tags` 屬性接受 PowerShell 資源庫中顯示的值陣列。 PowerShell 資源庫支援下列相容性值：

| 標籤               | 描述                                |
|-------------------|--------------------------------------------|
| PSEdition_Core    | 與 PowerShell Core 6 相容          |
| PSEdition_Desktop | 與 Windows PowerShell 相容         |
| Windows           | 與 Windows 相容                    |
| Linux             | 與 Linux (不限特定散發版本) 相容 |
| macOS             | 與 macOS 相容                      |

範例：

```powershell
@{
    GUID = "4ae9fd46-338a-459c-8186-07f910774cb8"
    Author = "Microsoft Corporation"
    CompanyName = "Microsoft Corporation"
    Copyright = "(C) Microsoft Corporation. All rights reserved."
    HelpInfoUri = "https://go.microsoft.com/fwlink/?linkid=855962"
    ModuleVersion = "1.2.4"
    PowerShellVersion = "3.0"
    ClrVersion = "4.0"
    RootModule = "PackageManagement.psm1"
    Description = 'PackageManagement (a.k.a. OneGet) is a new way to discover and install software packages from around the web.
 It is a manager or multiplexer of existing package managers (also called package providers) that unifies Windows package management with a single Windows PowerShell interface. With PackageManagement, you can do the following.
  - Manage a list of software repositories in which packages can be searched, acquired and installed
  - Discover software packages
  - Seamlessly install, uninstall, and inventory packages from one or more software repositories'

    CmdletsToExport = @(
        'Find-Package',
        'Get-Package',
        'Get-PackageProvider',
        'Get-PackageSource',
        'Install-Package',
        'Import-PackageProvider'
        'Find-PackageProvider'
        'Install-PackageProvider'
        'Register-PackageSource',
        'Set-PackageSource',
        'Unregister-PackageSource',
        'Uninstall-Package'
        'Save-Package'
    )

    FormatsToProcess  = @('PackageManagement.format.ps1xml')

    PrivateData = @{
        PSData = @{
            Tags = @('PackageManagement', 'PSEdition_Core', 'PSEdition_Desktop', 'Windows', 'Linux', 'macOS')
            ProjectUri = 'https://oneget.org'
        }
    }
}
```

<!-- reference links -->
[.NET Framework]: /dotnet/framework/
[.NET Core]: /dotnet/core/
[PSSnapIn]: /dotnet/api/system.management.automation.pssnapin
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[執行階段檢查]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[.NET CLI]: /dotnet/core/tools/?tabs=netcore2x
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell Standard]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell 資源庫]: https://www.powershellgallery.com
[.NET Portability Analyzer]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/gallery/concepts/module-psedition-support
