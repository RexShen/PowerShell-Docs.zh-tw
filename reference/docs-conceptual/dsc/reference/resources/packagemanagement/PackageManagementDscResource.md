---
ms.date: 09/20/2019
keywords: dsc,powershell,設定,安裝
title: DSC PackageManagement 資源
ms.openlocfilehash: ba8ab1e6c2d79e98084a52e3cffec39d57d800c9
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557153"
---
# <a name="dsc-packagemanagement-resource"></a>DSC PackageManagement 資源

適用於：Windows PowerShell 4.0、Windows PowerShell 5.0、Windows PowerShell 5.1

Windows PowerShell 預期狀態設定 (DSC) 中的 **PackageManagement** 資源，提供在目標節點上安裝或解除安裝「套件管理」套件的機制。 此資源需要 **PackageManagement** 模組，可從 [https://PowerShellGallery.com](https://PowerShellGallery.com) 取得。

> [!IMPORTANT]
> **PackageManagement** 模組至少應為 1.1.7.0 版，以下才是正確的屬性資訊。

## <a name="syntax"></a>語法

```Syntax
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ AdditionalParameters = [HashTable] ]
    [ MaximumVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ ProviderName = [string] ]
    [ RequiredVersion = [string] ]
    [ Source = [string] ]
    [ SourceCredential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string]{ Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>屬性

|屬性 |描述 |
|---|---|
|名稱 |指定要安裝或解除安裝之套件的名稱。 |
|AdditionalParameters |針對將傳至 `Get-Package -AdditionalArguments` 的參數，特定提供者的雜湊表。 例如，針對 NuGet 提供者，您可以傳遞 DestinationPath 之類的其他參數。 |
|MaximumVersion |指定所要尋找套件的最高允許版本。 如果不加入此參數，資源便會尋找可用的最高版本套件。 |
|MinimumVersion |指定所要尋找套件的最低允許版本。 如果不加入此參數，資源便會尋找可用的最高版本套件，同時也會滿足 **MaximumVersion** 參數所指定的最高指定版本。 |
|ProviderName |指定套件提供者名稱，以針對它設定套件搜尋的範圍。 您可以執行 `Get-PackageProvider` 來取得套件提供者名稱。 |
|RequiredVersion |指定您要安裝之套件的確切版本。 如果未指定此參數，此 DSC 資源便會安裝套件的最新可用版本，同時也會滿足 **MaximumVersion** 參數所指定的最高版本。 |
|來源 |指定可以找到套件的套件來源名稱。 這可以是 URI，或是向 `Register-PackageSource` 或 PackageManagementSource DSC 資源註冊的來源。 |
|SourceCredential |指定有權限安裝指定套件提供者或來源之套件的使用者帳戶。 |

## <a name="additional-parameters"></a>其他參數

下表列出 AdditionalParameters 屬性的選項。

|參數 |描述 |
|---|---|
|DestinationPath |由內建 Nuget 提供者之類的提供者使用。 指定您想要安裝套件的檔案位置。 |
|InstallationPolicy |由內建 Nuget 提供者之類的提供者使用。 判斷您是否信任套件來源。 值為下列其中之一：**Untrusted**、**Trusted**。 |

## <a name="common-properties"></a>通用屬性

|屬性 |描述 |
|---|---|
|DependsOn |表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |判斷是否要安裝或解除安裝套件。 預設值為 **Present**。 |
|PsDscRunAsCredential |設定用於執行整個資源的認證。 |

> [!NOTE]
> 已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。 如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。

## <a name="example"></a>範例

此範例會使用 **PackageManagement** DSC 資源安裝 **JQuery** NuGet 套件和 **GistProvider** PowerShell 模組。 此範例會先確認必要的套件來源可以使用，然後定義 **JQuery** 和 **GistProvider** 套件 (分別是 NuGet 和 PowerShell) 的預期狀態 。

```powershell
Configuration PackageTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceLocation   = "https://www.powershellgallery.com/api/v2"
        InstallationPolicy ="Trusted"
    }

    PackageManagement NugetPackage
    {
        Ensure               = "Present"
        Name                 = "JQuery"
        AdditionalParameters = "$env:HomeDrive\nuget"
        RequiredVersion      = "2.0.1"
        DependsOn            = "[PackageManagementSource]SourceRepository"
    }

    PackageManagement PSModule
    {
        Ensure               = "Present"
        Name                 = "gistprovider"
        Source               = "PSGallery"
        DependsOn            = "[PackageManagementSource]PSGallery"
    }
}
```
