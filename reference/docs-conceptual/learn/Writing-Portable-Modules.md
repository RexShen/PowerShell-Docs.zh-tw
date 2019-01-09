---
ms.date: 12/14/2018
keywords: powershell,cmdlet
title: 撰寫可移植的模組
ms.openlocfilehash: 38a93b5b030d58784b91292e2cd060b3a2c19a00
ms.sourcegitcommit: d396d0e4cfe3d279f399c17e7337380a31d373ac
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2018
ms.locfileid: "53747716"
---
# <a name="portable-modules"></a>可移植的模組

Windows PowerShell 針對撰寫[.NET Framework][]雖然 PowerShell Core 針對撰寫[.NET Core][]。 可移植的模組是在 Windows PowerShell 和 PowerShell Core 中運作的模組。 雖然.NET Framework 及.NET Core 為高度相容，有可用的 api 兩者之間的差異。 另外還有 Api 中的差異可在 Windows PowerShell 和 PowerShell Core 中。 適用於兩個環境中的模組必須要注意這些差異。

## <a name="porting-an-existing-module"></a>移植現有的模組

### <a name="porting-a-pssnapin"></a>移植 PSSnapIn

PowerShell Core 並不支援 PowerShell 嵌入式管理單元 (PSSnapIn)。 不過，它是 trivial 將 PSSnapIn 轉換成 PowerShell 模組。 一般而言，PSSnapIn 註冊程式碼是單一原始程式檔中的類別衍生自[PSSnapIn][]。 從組建; 移除這個原始程式檔不再需要。

使用[New-modulemanifest][]來建立新的模組資訊清單，以取代需要 PSSnapIn 註冊程式碼。 可重複使用的某些值 （例如描述） PSSnapIn 從模組資訊清單內。

`RootModule`模組資訊清單中的屬性應設為 實作指令程式的組件 (dll) 的名稱。

### <a name="the-net-portability-analyzer-aka-apiport"></a>.NET Portability Analyzer (也稱為 APIPort)

若要撰寫適用於 Windows PowerShell 使用 PowerShell Core 時，開始使用的連接埠模組[.NET Portability Analyzer][]。 針對您編譯的組件，以判斷是否相容於.NET Framework、.NET Core 及其他.NET 執行階段模組中使用的.NET Api 中執行這項工具。 如果有的話，則工具會提供建議替代的 Api。 否則，您可能必須加入[執行階段檢查][]並限制不適用於特定的執行階段的功能。

## <a name="creating-a-new-module"></a>建立新的模組

如果建立新的模組，是使用建議[.NET CLI][]。

### <a name="installing-the-powershell-standard-module-template"></a>安裝 PowerShell 標準模組範本

.NET CLI 安裝之後，安裝的範本程式庫，以產生簡單的 PowerShell 模組。
此模組會與 Windows PowerShell、 PowerShell Core、 Windows、 Linux 和 macOS 相容。

下列範例示範如何安裝的範本：

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

### <a name="creating-a-new-module-project"></a>建立新的模組專案

安裝範本之後，您可以建立新的 PowerShell 模組專案，使用該範本。 在此範例中，範例模組稱為 'myModule'。

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

使用標準的.NET CLI 命令來建置專案。

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

在建置模組之後, 您可以將它匯入，並執行範例 cmdlet。

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

下列各節詳細說明一些使用此範本的技術。

## <a name="net-standard-library"></a>.NET 標準程式庫

[.NET standard][]是可用於所有.NET 實作的.NET api 正式規格。 Managed 程式碼以.NET Standard 搭配與該版.NET Standard 相容的.NET Framework 和.NET Core 版本為目標。

> [!NOTE]
> 雖然 API 可能存在於.NET Standard，.NET Core 中的 API 實作可能會擲回`PlatformNotSupportedException`在執行階段，因此若要確認使用 Windows PowerShell 和 PowerShell Core 的相容性最佳做法是對您的模組，這兩種環境中執行測試。
> 如果您的模組是跨平台，也執行 Linux 和 macOS 上測試。

目標.NET Standard，可協助確保，隨著模組的發展，不相容的 Api 不意外取得導入的模組。 在編譯時期，而不是執行階段探索到不相容。

不過，它不需要.NET 標準為目標的模組來使用 Windows PowerShell 和 PowerShell Core，只要您使用相容的 Api。 Intermediate Language (IL) 是兩個執行階段之間相容。 您可以針對.NET Framework 4.6.1 中，這是與.NET Standard 2.0 相容。 如果您不使用外部.NET Standard 2.0 的 Api，然後您的模組搭配 PowerShell Core 6 而不必重新編譯。

## <a name="powershell-standard-library"></a>PowerShell 的標準程式庫

[PowerShell 標準][]程式庫是所有的 PowerShell 版本大於或等於該標準的版本中提供的 PowerShell Api 正式規格。

例如， [PowerShell 標準 5.1][]相容於 Windows PowerShell 5.1 和 PowerShell Core 6.0 或更新版本。

我們建議您編譯您使用 PowerShell 的標準程式庫的模組。 程式庫可確保 Api 可供使用且在 Windows PowerShell 和 PowerShell Core 6 實作。
PowerShell 標準被要總是轉送相容。 使用標準程式庫 5.1 PowerShell 所建置的模組一律會與未來的 PowerShell 版本相容。

## <a name="module-manifest"></a>模組資訊清單

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a>表示使用 Windows PowerShell 和 PowerShell Core 的相容性

驗證之後，與 Windows PowerShell 和 PowerShell Core 搭配使用您的模組，模組資訊清單應該明確表示相容性使用[CompatiblePSEditions][]屬性。 值為`Desktop`表示模組會使用 Windows PowerShell 時的值相容`Core`表示模組與 PowerShell Core 相容。 包括`Desktop`和`Core`表示模組是與 Windows PowerShell 和 PowerShell Core 相容。

> [!NOTE]
> `Core` 不自動表示模組適用於 Windows、 Linux 和 macOS。
> **CompatiblePSEditions** PowerShell v5 中引進了屬性。 模組資訊清單使用**CompatiblePSEditions**屬性無法載入 PowerShell v5 之前的版本中。

### <a name="indicating-os-compatibility"></a>指出作業系統相容性

首先，請驗證您的模組，適用於 Linux 和 macOS 上。 接下來，指出與這些模組資訊清單中的作業系統相容性。 這可讓使用者更輕鬆地找到您的模組時發行至其作業系統[PowerShell 資源庫][]。

在模組資訊清單中，`PrivateData`屬性具有`PSData`子屬性。 選擇性`Tags`屬性`PSData`接受 PowerShell 資源庫中顯示的值陣列。 「 PowerShell 資源庫支援下列相容性值：

| 標籤               | 描述                                |
|-------------------|--------------------------------------------|
| PSEdition_Core    | 與 PowerShell Core 6 相容          |
| PSEdition_Desktop | 使用 Windows PowerShell 相容         |
| Windows           | 與 Windows 相容性                    |
| Linux             | 與 Linux （沒有特定的散發版本） 相容 |
| macOS             | MacOS 與相容性                      |

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
[PowerShell 標準]: https://github.com/PowerShell/PowerShellStandard
[PowerShell 標準 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell 資源庫]: https://www.powershellgallery.com
[.NET portability Analyzer]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/gallery/concepts/module-psedition-support
